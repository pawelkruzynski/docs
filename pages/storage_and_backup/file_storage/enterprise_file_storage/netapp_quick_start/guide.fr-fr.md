---
title: Enterprise File Storage - Premiers pas avec les API
excerpt: Débuter sur votre offre Enterprise File Storage à l’aide des API OVHcloud
updated: 2021-10-27
---

## Objectif

Dans ce guide de démarrage rapide, découvrez comment débuter sur votre offre Enterprise File Storage.

**Vous apprendrez comment récupérer les informations de votre offre et créer votre premier volume à l'aide des API OVHcloud.**

## Prérequis

- Disposer d'une offre OVHcloud Enterprise File Storage
- Être connecté sur la page des [API OVHcloud](https://api.ovh.com/)
- Savoir [monter un partage NFS](/pages/storage_and_backup/file_storage/ha_nas/nas_nfs)

## L'essentiel

L'offre OVHcloud Enterprise File Storage vous permet de créer des volumes et de gérer ainsi des partages de fichiers accessibles sur un réseau.

Vous avez la possibilité de choisir la taille de vos volumes, gérer les accès via des ACL ou encore créer des snapshots (copie instantanée du volume).

## En pratique

Toutes les API utilisées pour ce guide sont disponibles dans la section */storage* : <https://api.ovh.com/console/#/storage>.

> [!primary]
>
> Lors de l'utilisation des API, tous les champs marqués d'un astérisque (\*) sont obligatoires.
>

### Récupérer les informations de votre service

Tous vos services actifs peuvent être récupérés en utilisant la route API suivante :

> [!api]
>
> @api {v1} /storage GET /storage/netapp
>

### Créer un nouveau volume

Un volume est une unité de stockage avec une taille et un protocole.

Pour créer un volume, utilisez la route API suivante :

> [!faq]
>
> API :
>
>> > [!api]
>> >
>> > @api {v1} /storage POST /storage/netapp/{serviceName}/share
>> >
>>
>
> Paramètres :
>
>> > **serviceName** *
>> >
>> >> ID du service
>> >
>> > **NetAppShare** *
>> >
>> >> **description**
>> >>
>> >> > Description du volume
>> >>
>> >> **name**
>> >>
>> >> > Nom du volume
>> >>
>> >> **protocole** *
>> >>
>> >> > Protocole utilisé par le volume
>> >>
>> >> **size**
>> >>
>> >> > Taille en gigaoctets du volume
>

Sélectionnez le protocole `NFS` et une taille de `10` gigaoctets par exemple.

### Ajouter une ACL au volume

Les ACLs permettent d'autoriser ou de refuser l'accès à un volume.

> [!warning]
>
> Le comportement par défaut consiste à refuser tout accès à un nouveau volume.
>

Après avoir créé un volume, vous devez créer une nouvelle ACL afin d'accéder à celui-ci.

Pour créer une nouvelle ACL qui vous permettra de vous connecter à votre volume, utilisez la route API suivante :

> [!faq]
>
> API :
>
>> > [!api]
>> >
>> > @api {v1} /storage POST /storage/netapp/{serviceName}/share/{shareId}/acl
>> >
>>
>
> Paramètres :
>
>> > **serviceName** *
>> >
>> >> ID du service
>> >
>> > **shareId** *
>> >
>> >> ID du volume
>> >
>> > **NetAppShareACLRule** *
>> >
>> >> **accessLevel** *
>> >>
>> >> > Niveau d'accès ACL. Peut être **rw** (lecture et écriture) ou **ro** (lecture seule).
>> >>
>> >> **accessTo** *
>> >>
>> >> > Adresse IP ou plage d'adresses IP en notation CIDR.
>

> [!primary]
>
> En utilisant la notation CIDR, vous pouvez autoriser l'accès au volume depuis la plage d'adresses IP X.X.X.X/X.
> Par exemple: 192.0.2.0/24
>

### Monter le volume

Vérifiez le statut de création de l'ACL à l'aide de la route API suivante :

> [!faq]
>
> API :
>
>> > [!api]
>> >
>> > @api {v1} /storage GET /storage/netapp/{serviceName}/share/{shareId}/acl/{aclRuleId}
>> >
>>
>
> Paramètres :
>
>> > **serviceName** *
>> >
>> >> ID du service
>> >
>> > **shareId** *
>> >
>> >> ID du volume
>> >
>> > **aclRuleId** *
>> >
>> >> ID de l'ACL
>

Remplacez `aclRuleId` par l'ID de l'ACL créée pour votre volume.

> [!primary]
>
> Le statut ACL doit être `active`.
>

Une fois que l'ACL est active, récupérez les chemins d'accès du volume à l'aide de l'API suivante :

> [!faq]
>
> API :
>
>> > [!api]
>> >
>> > @api {v1} /storage GET /storage/netapp/{serviceName}/share/{shareId}/accessPath
>> >
>>
>
> Paramètres :
>
>> > **serviceName** *
>> >
>> >> ID du service
>> >
>> > **shareId** *
>> >
>> >> ID du volume
>

Un ou plusieurs chemins d'accès vous seront présentés pour votre volume.

Vous pouvez maintenant monter le volume avec la commande suivante :

```sh
mount -t nfs accessPath
```

> [!primary]
>
> Si vous utilisez Linux, le paquet `nfs-utils` doit être installé.
>

Une fois monté, votre volume est alors utilisable pour stocker vos fichiers.

### Suppression du volume

Vous pouvez supprimer votre volume à l'aide de la route API suivante :

> [!faq]
>
> API :
>
>> > [!api]
>> >
>> > @api {v1} /storage DELETE /storage/netapp/{serviceName}/share/{shareId}
>> >
>>
>
> Paramètres :
>
>> > **serviceName** *
>> >
>> >> ID du service
>> >
>> > **shareId** *
>> >
>> >> ID du volume
>

## Aller plus loin

Si vous avez besoin d'une formation ou d'une assistance technique pour la mise en oeuvre de nos solutions, contactez votre commercial ou cliquez sur [ce lien](https://www.ovhcloud.com/fr/professional-services/) pour obtenir un devis et demander une analyse personnalisée de votre projet à nos experts de l’équipe Professional Services.

Échangez avec notre [communauté d'utilisateurs](/links/community).
