---
title: Using Codefresh with OVHcloud Managed Kubernetes cluster
excerpt: 'Find out how to use Codefresh CI/CD with an OVHcloud Managed Kubernetes cluster'
updated: 2019-07-01
---

In this tutorial we will see how you can connect [Codefresh](https://codefresh.io){.external}, a CI/CD platform for Kubernetes, to an OVHcloud Managed Kubernetes cluster.

## Before you begin

The first thing you need to follow this tutorial is a Codefresh account, you can get it directly at [Codefresh](https://codefresh.io){.external} site.

![Codefresh](images/using-codefresh-01.jpg){.thumbnail}

This tutorial also presupposes that you already have a working OVHcloud Managed Kubernetes cluster, and some basic knowledge of how to operate it. If you want to know more on those topics, please look at the [OVHcloud Managed Kubernetes Service Quickstart](/pages/public_cloud/containers_orchestration/managed_kubernetes/deploying-hello-world).

## Connect an OVH Kubernetes cluster to Codefresh dashboard

You can use the Codefresh GUI to connect your OVHcloud Managed Kubernetes cluster to Codefresh. In Codefresh GUI, start by going into your *Account Configuration*, by clicking on *Account Settings* on the left sidebar. On the first section called *Integrations* click the *Configure* button next to Kubernetes.

![Connect an OVH Kubernetes cluster to Codefresh dashboard](images/using-codefresh-02.jpg){.thumbnail}

![Connect an OVH Kubernetes cluster to Codefresh dashboard](images/using-codefresh-03.jpg){.thumbnail}

As the current time, Codefresh doesn't propose a direct integration with OVHcloud Managed Kubernetes Service, so you will have to add your cluster manually. To do it, click on the *Add provider* button and select *Custom providers*.

![Connect an OVH Kubernetes cluster to Codefresh dashboard](images/using-codefresh-03.jpg){.thumbnail}

![Connect an OVH Kubernetes cluster to Codefresh dashboard](images/using-codefresh-04.jpg){.thumbnail}

![Connect an OVH Kubernetes cluster to Codefresh dashboard](images/using-codefresh-05.jpg){.thumbnail}

The integration between Codefresh and your Kubernetes cluster is API based and relies on a Kubernetes service account of your choosing that will be used to manage the integration.

The configurations you’ll be required to add are:

1. Name - Any name of your choosing, that will represent your cluster context in Codefresh.
1. Host - The full URL of the Kubernetes API endpoints including protocol and port
1. Certificate - The Kubernetes service account certificate used for the integration with Codefresh (base64 encoded)
1. Token - The Kubernetes service account token used for the integration with Codefresh (base64 encoded)

Let's see how you can obtain these parameters, using `kubectl`.

### Set the permissions

In order to allow Codefresh to connect to your cluster, you need to set up a `Role`, a `ServiceAccount` and a `RoleBinding`. Create a `codefresh-role-sa-bind.yml` YAML file:

```yaml
kind: ClusterRole
apiVersion: rbac.authorization.k8s.io/v1
metadata:
  name: codefresh-role
rules:
  - apiGroups: [""]
    resources: ["*"]
    verbs: ["list", "watch", "get"]
---
apiVersion: v1
kind: ServiceAccount
metadata:
  name: codefresh-user
  namespace: kube-system
---
apiVersion: rbac.authorization.k8s.io/v1beta1
kind: ClusterRoleBinding
metadata:
  name: codefresh-user
roleRef:
  apiGroup: rbac.authorization.k8s.io
  kind: ClusterRole
  name: codefresh-role
subjects:
- kind: ServiceAccount
  name: codefresh-user
  namespace: kube-system
```

And apply it using `kubectl`:

```bash
kubectl apply -f codefresh-role-sa-bind.yml
```

The `Role`, the `ServiceAccount` and the `RoleBinding` are created:

```console
$ kubectl apply -f codefresh-role-sa-bind.yml
clusterrole.rbac.authorization.k8s.io/codefresh-role created
serviceaccount/codefresh-user created
clusterrolebinding.rbac.authorization.k8s.io/codefresh-user created
```

### Getting the *Host*

Use `kubectl` to get the full URL of the OVHcloud Managed Kubernetes API endpoints:

```bash
kubectl cluster-info
```

The *Host* parameter is the URL of the Kubernetes master.

```console
$ kubectl cluster-info
Kubernetes master is running at https://xxxxxxxx.c1.gra.k8s.ovh.net
KubeDNS is running at https://xxxxxxxx.c1.gra.k8s.ovh.net/api/v1/namespaces/kube-system/services/kube-dns:dns/proxy

To further debug and diagnose cluster problems, use 'kubectl cluster-info dump'.
```

In my example cluster, the *Host* is `https://xxxxxxxx.c1.gra.k8s.ovh.net`.

### Getting the *Certificate*

Use `kubectl` to generate a certificate:

```bash
echo $(kubectl get secret --namespace kube-system  -o go-template='{{index .data "ca.crt" }}' $(kubectl get sa codefresh-user --namespace kube-system -o go-template="{{range .secrets}}{{.name}}{{end}}"))

```

Copy the generated certificate into the *Certificate* field on Codefresh.

```console
$ echo $(kubectl get secret --namespace kube-system -o go-template='{{index .data "ca.crt" }}' $(kubectl get sa codefresh-user --namespace kube-system -o go-template="{{range .secrets}}{{.name}}{{end}}"))
LS0tLS1CRUdJTiBDRVJUSUZJQ0FURS0tLS0tCk1JSUZtVENDQTRHZ0F3SUJBZ0lCS2pBTkJna3Foa2lHOXcwQkFRc0ZBREF2TVMwd0t3WURWUVFERENReVlqRmsKWVdabFlTMWxNR1l6TFRRNU5UVXRPV1JqWkMxaFpqbGhNemd4TWpobFl6Z3dIaGNOTVRneE1EQTVNVGMxTVRVMQpXaGNOTWpNeE1EQTRNVGMxTVRVMVdqQXZNUzB3S3LS0tLS1CRUdJTiBDRVJUSUZJQ0FURS0tLS0tCk1JSUZtVENDQTRHZ0F3SUJBZ0lCS2pBTkJna3Foa2lHOXcwQkFRc0ZBREF2TVMwd0t3WURWUVFERENReVlqRmsKWVdabFlTMWxNR1l6TFRRNU5UVXRPV1JqWkMxaFpqbGhNemd4TWpobFl6Z3dIaGNOTVRneE1EQTVNVGMxTVRVMQpXaGNOTWpNeE1EQTRNVGMxTVRVMVdqQXZNUzB3S3LS0tLS1CRUdJTiBDRVJUSUZJQ0FURS0tLS0tCk1JSUZtVENDQTRHZ0F3SUJBZ0lCS2pBTkJna3Foa2lHOXcwQkFRc0ZBREF2TVMwd0t3WURWUVFERENReVlqRmsKWVdabFlTMWxNR1l6TFRRNU5UVXRPV1JqWkMxaFpqbGhNemd4TWpobFl6Z3dIaGNOTVRneE1EQTVNVGMxTVRVMQpXaGNOTWpNeE1EQTRNVGMxTVRVMVdqQXZNUzB3S3LS0tLS1CRUdJTiBDRVJUSUZJQ0FURS0tLS0tCk1JSUZtVENDQTRHZ0F3SUJBZ0lCS2pBTkJna3Foa2lHOXcwQkFRc0ZBREF2TVMwd0t3WURWUVFERENReVlqRmsKWVdabFlTMWxNR1l6TFRRNU5UVXRPV1JqWkMxaFpqbGhNemd4TWpobFl6Z3dIaGNOTVRneE1EQTVNVGMxTVRVMQpXaGNOTWpNeE1EQTRNVGMxTVRVMVdqQXZNUzB3S3LS0tLS1CRUdJTiBDRVJUSUZJQ0FURS0tLS0tCk1JSUZtVENDQTRHZ0F3SUJBZ0lCS2pBTkJna3Foa2lHOXcwQkFRc0ZBREF2TVMwd0t3WURWUVFERENReVlqRmsKWVdabFlTMWxNR1l6TFRRNU5UVXRPV1JqWkMxaFpqbGhNemd4TWpobFl6Z3dIaGNOTVRneE1EQTVNVGMxTVRVMQpXaGNOTWpNeE1EQTRNVGMxTVRVMVdqQXZNUzB3S3LS0tLS1CRUdJTiBDRVJUSUZJQ0FURS0tLS0tCk1JSUZtVENDQTRHZ0F3SUJBZ0lCS2pBTkJna3Foa2lHOXcwQkFRc0ZBREF2TVMwd0t3WURWUVFERENReVlqRmsKWVdabFlTMWxNR1l6TFRRNU5UVXRPV1JqWkMxaFpqbGhNemd4TWpobFl6Z3dIaGNOTVRneE1EQTVNVGMxTVRVMQpXaGNOTWpNeE1EQTRNVGMxTVRVMVdqQXZNUzB3S3LS0tLS1CRUdJTiBDRVJUSUZJQ0FURS0tLS0tCk1JSUZtVENDQTRHZ0F3SUJBZ0lCS2pBTkJna3Foa2lHOXcwQkFRc0ZBREF2TVMwd0t3WURWUVFERENReVlqRmsKWVdabFlTMWxNR1l6TFRRNU5UVXRPV1JqWkMxaFpqbGhNemd4TWpobFl6Z3dIaGNOTVRneE1EQTVNVGMxTVRVMQpXaGNOTWpNeE1EQTRNVGMxTVRVMVdqQXZNUzB3S3LS0tLS1CRUdJTiBDRVJUSUZJQ0FURS0tLS0tCk1JSUZtVENDQTRHZ0F3SUJBZ0lCS2pBTkJna3Foa2lHOXcwQkFRc0ZBREF2TVMwd0t3WURWUVFERENReVlqRmsKWVdabFlTMWxNR1l6TFRRNU5UVXRPV1JqWkMxaFpqbGhNemd4TWpobFl6Z3dIaGNOTVRneE1EQTVNVGMxTVRVMQpXaGNOTWpNeE1EQTRNVGMxTVRVMVdqQXZNUzB3S3LS0tLS1CRUdJTiBDRVJUSUZJQ0FURS0tLS0tCk1JSUZtVENDQTRHZ0F3SUJBZ0lCS2pBTkJna3Foa2lHOXcwQkFRc0ZBREF2TVMwd0t3WURWUVFERENReVlqRmsKWVdabFlTMWxNR1l6TFRRNU5UVXRPV1JqWkMxaFpqbGhNemd4TWpobFl6Z3dIaGNOTVRneE1EQTVNVGMxTVRVMQpXaGNOTWpNeE1EQTRNVGMxTVRVMVdqQXZNUzB3S3LS0tLS1CRUdJTiBDRVJUSUZJQ0FURS0tLS0tCk1JSUZtVENDQTRHZ0F3SUJBZ0lCS2pBTkJna3Foa2lHOXcwQkFRc0ZBREF2TVMwd0t3WURWUVFERENReVlqRmsKWVdabFlTMWxNR1l6TFRRNU5UVXRPV1JqWkMxaFpqbGhNemd4TWpobFl6Z3dIaGNOTVRneE1EQTVNVGMxTVRVMQpXaGNOTWpNeE1EQTRNVGMxTVRVMVdqQXZNUzB3S31NBQnUKLS0tLS1FTkQgQ0VSVElGSUNBVEUtLS0tLQo=
```

### Getting the *Token*

Use `kubectl` to generate a token:

```bash
echo $(kubectl get secret --namespace kube-system -o go-template='{{index .data "token" }}' $(kubectl get sa codefresh-user --namespace kube-system -o go-template="{{range .secrets}}{{.name}}{{end}}"))
```

Copy the generated token into the *Token* field on Codefresh.

```console
$ echo $(kubectl get secret -o go-template='{{index .data "token" }}' $(kubectl get sa default -o go-template="{{range .secrets}}{{.name}}{{end}}"))
ZXlKaGJHY2lPaUpTVXpJMU5pSXNJbXRwWkNJNklpSjkuZXlKcGMzTWlPaUpyZFdKbGNtNWxkR1Z6TDNObGNuWnBZMlZoWTJOdmRXNTBJaXdpYTNWaVpYSnVaWFJsY3k1cGJ5OXpaWEoyYVdObFlXTmpiM1Z1ZEM5dVlXMWxjM0JoWTJVaU9pSmtaV1poZFd4MElpd2lhM1ZpWlhKdVpYUmxjeTVwYnk5elpYSjJhV05sWVdOamIzVnVkQzZXlKaGJHY2lPaUpTVXpJMU5pSXNJbXRwWkNJNklpSjkuZXlKcGMzTWlPaUpyZFdKbGNtNWxkR1Z6TDNObGNuWnBZMlZoWTJOdmRXNTBJaXdpYTNWaVpYSnVaWFJsY3k1cGJ5OXpaWEoyYVdObFlXTmpiM1Z1ZEM5dVlXMWxjM0JoWTJVaU9pSmtaV1poZFd4MElpd2lhM1ZpWlhKdVpYUmxjeTVwYnk5elpYSjJhV05sWVdOamIzVnVkQzZXlKaGJHY2lPaUpTVXpJMU5pSXNJbXRwWkNJNklpSjkuZXlKcGMzTWlPaUpyZFdKbGNtNWxkR1Z6TDNObGNuWnBZMlZoWTJOdmRXNTBJaXdpYTNWaVpYSnVaWFJsY3k1cGJ5OXpaWEoyYVdObFlXTmpiM1Z1ZEM5dVlXMWxjM0JoWTJVaU9pSmtaV1poZFd4MElpd2lhM1ZpWlhKdVpYUmxjeTVwYnk5elpYSjJhV05sWVdOamIzVnVkQzZXlKaGJHY2lPaUpTVXpJMU5pSXNJbXRwWkNJNklpSjkuZXlKcGMzTWlPaUpyZFdKbGNtNWxkR1Z6TDNObGNuWnBZMlZoWTJOdmRXNTBJaXdpYTNWaVpYSnVaWFJsY3k1cGJ5OXpaWEoyYVdObFlXTmpiM1Z1ZEM5dVlXMWxjM0JoWTJVaU9pSmtaV1poZFd4MElpd2lhM1ZpWlhKdVpYUmxjeTVwYnk5elpYSjJhV05sWVdOamIzVnVkQzZXlKaGJHY2lPaUpTVXpJMU5pSXNJbXRwWkNJNklpSjkuZXlKcGMzTWlPaUpyZFdKbGNtNWxkR1Z6TDNObGNuWnBZMlZoWTJOdmRXNTBJaXdpYTNWaVpYSnVaWFJsY3k1cGJ5OXpaWEoyYVdObFlXTmpiM1Z1ZEM5dVlXMWxjM0JoWTJVaU9pSmtaV1poZFd4MElpd2lhM1ZpWlhKdVpYUmxjeTVwYnk5elpYSjJhV05sWVdOamIzVnVkQzSmtGQ3lxU01Rb3RqejFhNFc3R3VFQk03MlJjMUhZSUwtOHhSNy1aVzRBQU9jeGdxMVhyZ2F2LVZhRQ==
```

### Test and save the connection

Click on the *Test connection* button to test the configuration. You should get a message telling you that your OVHcloud Managed Kubernetes cluster connects successfully with Codefresh:

![Connect an OVH Kubernetes cluster to Codefresh dashboard](images/using-codefresh-07.jpg){.thumbnail}

Then click on *Save* to save your cluster on your Codefresh Dashboard.

### And now?

Now you can follow [Codefresh official tutorial](https://codefresh.io/docs/docs/getting-started/deployment-to-kubernetes-quick-start-guide/){.external} to deploy a Docker image to a Kubernetes cluster and also how to setup an automated pipeline to automatically redeploy it when the source code changes.

![Connect an OVH Kubernetes cluster to Codefresh dashboard](images/using-codefresh-08.jpg){.thumbnail}

## Go further

- If you need training or technical assistance to implement our solutions, contact your sales representative or click on [this link](https://www.ovhcloud.com/fr/professional-services/) to get a quote and ask our Professional Services experts for assisting you on your specific use case of your project.

- Join our [community of users](/links/community).
