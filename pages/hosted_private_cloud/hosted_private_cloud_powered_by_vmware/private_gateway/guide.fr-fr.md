---
title: Activer la Private Gateway
excerpt: Découvrez comment activer la Private Gateway sur une infrastructure Hosted Private Cloud
hidden: true
updated: 2023-01-06
---

## Objectif

L'interface vSphere est accessible par défaut via Internet. Pour les infrastructures qui peuvent être gérées via le réseau privé vRack, il est possible de basculer l'accès vSphere sur le vRack au moyen de la private gateway.

**Ce guide vous explique comment activer la private gateway sur votre infrastructure Hosted Private Cloud via l'API OVHCloud.**

> [!warning]
> N'activez pas l'option Private Gateway si vous utilisez la solution de plan de reprise d'activité [Zerto](https://www.ovhcloud.com/fr/enterprise/products/hosted-private-cloud/zerto/) car cela provoquerait un dysfonctionnement de Zerto.
>

> [!warning]
>
> L'activation de la private gateway coupe l'accès depuis Internet, il est donc important de s'assurer de pouvoir accéder au vRack.
>

## Prérequis

* Posséder une offre [Hosted Private Cloud](https://www.ovh.com/fr/private-cloud/){.external}.
* Accéder à l’interface de gestion vSphere.
* Être connecté aux [API OVHCloud](https://api.ovh.com/){.external}.
* Avoir [créé ses identifiants pour l'API OVHCloud](/pages/manage_and_operate/api/first-steps){.external}.

## En pratique

### Architecture

* La private gateway est une machine virtuelle (VM) qui sera déployée sur l'infrastructure et connectée au vRack.
* La private gateway n'a pas de route, donc seul l'utilisateur du même sous-réseau peut atteindre la passerelle. La connexion à partir d'un autre réseau doit être source-natté.

> [!warning]
>
> Le certificat TLS reste le même (pcc-X-X-X-X-X.ovh.com).
>

### Prérequis

* Avoir créé un Portgroup sur le vRack pour connecter la private gateway. Il doit etre sous le datacenter prévu.
* Avoir ajouté le réseau de la private gateway dans [les autorisations par IP source](/pages/hosted_private_cloud/hosted_private_cloud_powered_by_vmware/manager_ovh_private_cloud).
* Avoir ajouté une entrée dans le fichier /etc/hosts ou C:\Windows\system32\drivers\etc\hosts pour faire correspondre l'adresse pcc-X-X-X-X.ovh.com avec l'adresse IP privée (outre éviter des messages d'erreurs de certificat, cela est nécessaire pour un bon fonctionnement des différentes consoles VMRC ou autre).

<a name="enablegw"></a>

### Activer la private gateway

Avant de commencer, rassemblez les informations nécessaires suivantes :

- **serviceName** : le nom du Hosted Private Cloud (syntaxe pcc-X-X-X-X)
- **datacenterId** : le datacenter ID
- **ip** & **netmask** : le réseau IP pour la private gateway
- **portgroup** : le nom du PortGroup pour la connexion au vRack

Ces informations seront à utiliser dans les différents appels d'API qui suivent.

Lancez l'activation avec :

> [!api]
>
> @api {v1} /dedicatedCloud POST /dedicatedCloud/{serviceName}/datacenter/{datacenterId}/privateGateway/enable
>

L'appel entraîne la création d'une tâche qui va déployer la machine virtuelle et fait la configuration réseau.

Vous recevrez peut-être une notification de livraison de ressource (un nouveau datastore). Celui-ci ne sera pas facturé et sera placé dans le dossier **Admin Storages** de la vue **Storage**. Il est ajouté pour pouvoir héberger la machine virtuelle sans affecter vos espaces de stockage.

<a name="disablegw"></a>

### Désactiver la private gateway

Avant de commencer, rassemblez les informations nécessaires suivantes :

- **serviceName** : le nom du Hosted Private Cloud (syntaxe pcc-X-X-X-X)
- **datacenterId** : le datacenter ID

> [!warning]
>
> La désactivation de la private gateway rétablit l'accès depuis Internet, il est donc important de s'assurer d'avoir mis en place le filtrage IP voulu.
>

Lancez la désactivation avec :

> [!api]
>
> @api {v1} /dedicatedCloud POST /dedicatedCloud/{serviceName}/datacenter/{datacenterId}/privateGateway/disable
>

## Aller plus loin

Échangez avec notre [communauté d'utilisateurs](/links/community).
