---
title: Exposed APIs, Kubernetes configuration and Feature gates
excerpt: ''
updated: 2022-05-30
---

ou can find here some details on the APIs: the one we expose on OVHcloud and the configuration of Kubernetes APIs on OVHcloud Managed Kubernetes clusters.

## OVHcloud API

We have added a [Kubernetes section](https://ca.api.ovh.com/console/#/cloud/project/{serviceName}/kube) to the [OVHcloud API](https://ca.api.ovh.com/).  
Using it allows you to add and remove nodes, update and reset your clusters or get `kubectl` configuration.

> [!primary]
> If you have never used the OVHcloud API, you can learn the basics in [First steps with the OVHcloud API](/pages/manage_and_operate/api/first-steps).

## Kubernetes configuration

### API

Admission plugins (defaults are not listed here):

* `AlwaysPullImages`: Forces every new pod to pull the required images each time. In a multi-tenant cluster users can be assured that their private images can only be used by those who have the credentials to pull them.
* `NodeRestriction`: Ensure that the kubelet is restricted to the Node and Pod objects that it could modify as defined. Such kubelets will only be allowed to modify their own NodeAPI object and PodAPI objects that are bound to their node.

Authorization modes:

* [Node](https://kubernetes.io/docs/reference/access-authn-authz/node/){.external}: Authorise API requests made by Kubelets.
* [RBAC](https://kubernetes.io/docs/reference/access-authn-authz/rbac/){.external}: Role-based access control is a method of regulating access to computer or network resources based on the roles of individual users within an organisation.

Feature gates:

* `TTLAfterFinished`: Allow a TTL controller to clean up resources after they finish execution.

### Kubelet

* `protect-kernel-defaults`: Protect tuned kernel parameters from overriding kubelet default kernel parameter values.

## Go further

- If you need training or technical assistance to implement our solutions, contact your sales representative or click on [this link](https://www.ovhcloud.com/fr/professional-services/) to get a quote and ask our Professional Services experts for assisting you on your specific use case of your project.

- Join our [community of users](/links/community).