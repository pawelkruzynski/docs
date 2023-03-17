---
title: Getting started with database kubernetes opdrator
excerpt: Find out how to install and use the kubernetes database operator 
slug: database-operator
section: General guides
order: 120
updated: 2023-03-16
---

**Last updated March 16<sup>th</sup>, 2023**

## Objective

The kubernetes database operator allow you to automaticaly authorize your Kubernetes cluster IP on your OVHcloud cloud databases service.

**This guide explains how to install and use the database operator in order to authorize the Kubernetes IP on your service**

## Requirements

- Access to the [OVHcloud API](https://api.ovh.com/) (create your credentials by consulting [this guide](https://docs.ovh.com/de/api/first-steps-with-ovh-api/))
- A [Public Cloud project](https://www.ovhcloud.com/de/public-cloud/) in your OVHcloud account

## Installation

Use the kubernetes package manager [helm](https://helm.sh) to install the operator.

```bash
helm repo add clouddatabases-operator https://artifacthub.io/clouddb/public-cloud-databases-operator
helm update
```

### OVH Credentials

The operator needs a secret that contains the credentials to call Ovhcloud api. Go to https://api.ovh.com/createToken/ to generate the credentials namely:
- application key
- application secret
- consumer key

### Values

Create a values.yaml to be injected in the helm chart 
that will be created afterwards. Region is either: ovh-eu, ovh-ca or ovh-us.
```yaml
ovhCredentials:
  applicationKey: XXXX
  applicationSecret: XXXX
  consumerKey: XXXX
  region: XXXX # ovh-eu, ovh-ca or ovh-us

namespace: XXXX # Your Kubernetes namespace
```
Use the values file you created to create the helm chart

```bash
helm install -f values.yaml clouddatabases-operator public-cloud-databases-operator
```
That will create the operator, crd and secrets.
 ```bash
kubectl get deploy
NAME                                       READY   UP-TO-DATE   AVAILABLE   AGE
operator-public-cloud-databases-operator   0/1     1            0           11h

kubectl get crd services.clouddatabases.ovhcloud.net
NAME                                   CREATED AT
services.clouddatabases.ovhcloud.net   2023-03-07T19:32:37Z

kubectl get secret ovh-credentials
NAME              TYPE                      DATA   AGE
ovh-credentials   kubernetes.io/storageos   4      9h
```

## Create Custom Resource

Create a custom resource object using this example file.
```yaml
 {
        "apiVersion": "clouddatabases.ovhcloud.net/v1alpha1",
        "kind": "services",
        "metadata": {
          "name": "XXXX",
          "namespace": "XXXX"
        },
        "spec": {
          "projectId": "XXXX",
          "serviceId": "XXXX",
          "labelSelector": # No label selector means apply on all nodes
            "matchLabels":
              "LABELNAME": "LABELVALUE"
        },
      }
```

The field serviceId is optional. If not set, the operator will be run against all the services of your project.

```bash
kubectl apply -f cr.yaml
```

## Nodes Labels
You can use kubernetes labeling in order to select specific nodes that you want the operator to be run against. 
The created CR and the node must have the same label and value.

```bash
kubectl label nodes NODENAME1 NODENAME2 ... LABELNAME=LABELVALUE
```

# Related links
 
[Github repository](https://github.com/ovh/public-cloud-databases-operator)
