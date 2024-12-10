---
title: Enterprise File Storage - Gérer vos volumes
excerpt: Découvrez comment créer et gérer vos volumes OVHcloud Enterprise File Storage en utilisant les API OVHcloud
updated: 2021-10-27
---

## Objectif

Dans ce guide, découvrez comment gérer les volumes pour l'offre OVHcloud Enterprise File Storage.

**Vous apprendrez comment récupérer les volumes existants ainsi que leur point de montage, créer un nouveau volume ou encore supprimer un volume existant depuis les API OVHcloud.**

## Prérequis

- Disposer d'une offre OVHcloud Enterprise File Storage
- Être connecté sur la page des [API OVHcloud](https://api.ovh.com/)

## L'essentiel

Un volume est un système de fichiers partagé persistant, accessible en lecture et/ou écriture.

Il peut également avoir un nom et une description (facultatif).

> [!warning]
>
> Par défaut, tout accès à un volume nouvellement créé est restreint. Une ACL doit être créée pour permettre l’accès.
>

## Instructions

Toutes les routes API utilisées pour ce guide sont disponibles dans la section */storage* : <https://api.ovh.com/console/#/storage>.

> [!primary]
>
> Lors de l'utilisation des API, tous les champs marqués d'un astérisque (\*) sont obligatoires.
>

### Lister les volumes

Pour lister les volumes d'un service, utilisez la route API suivante :

> [!faq]
>
> API :
>
>> > [!api]
>> >
>> > @api {v1} /storage GET /storage/netapp/{serviceName}/share
>> >
>>
>
> Paramètres :
>
>> > **serviceName** *
>> >
>> >> ID du service
>> >
>

Remplacez `serviceName` par l'ID de votre service.

### Récupérer les informations d'un volume

Pour récupérer les informations d'un volume, utilisez la route API suivante :

> [!faq]
>
> API :
>
>> > [!api]
>> >
>> > @api {v1} /storage GET /storage/netapp/{serviceName}/share/{shareId}
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

Remplacez `serviceName` par l'ID de votre service et `shareId` par l'ID du volume.

### Créer un volume

Pour créer un nouveau volume, utilisez la route API suivante :

> [!faq]
>
> API :
>
>> > [!api]
>> >
>> > @api {v1} /storage POST /storage/netapp{serviceNme}/share
>> >
>>
>
> Paramètres :
>
>> > **serviceName** *
>> >
>> >> ID du service
>> >
>

Remplacez `serviceName` par l'ID de votre service.

Choisissez le protocol `NFS` pour votre nouveau volume (propriété `protocol`) ainsi que la taille de celui-ci (propriété `size`).
Vous pouvez également spécifier un nom et une description avec les propriétés `name` et `description`.

### Afficher les points de montage d'un volume

Pour connaître le chemin de montage d'un volume, utilisez la route API suivante :

> [!faq]
>
> API :
>
>> > [!api]
>> >
>> > @api {v1} /storage GET /storage/netapp{serviceName}/share/{shareId}/accessPath
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

Remplacez `serviceName` par l'ID de votre service et `shareId` par l'ID du volume.

Les chemins de montage retournés peuvent être utilisés pour monter le volume.

La commande de montage sera différente, suivant le protocole choisi pour le volume.  

> [!primary]
>
> Pour NFS, vous trouverez les instructions de montage dans le guide [Monter votre NAS via un partage NFS](/pages/storage_and_backup/file_storage/ha_nas/nas_nfs).
> À noter que le chemin de montage récupéré remplace IP_NAS/NFS_PATH dans cette documentation.
>  

### Supprimer un volume

Pour supprimer un volume, utilisez la route API suivante :  

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

Remplacez `serviceName` par l'ID de votre service et `shareId` par l'ID du volume à supprimer.

## Aller plus loin

[Premiers pas avec les API OVHcloud](/pages/manage_and_operate/api/first-steps)

Si vous avez besoin d'une formation ou d'une assistance technique pour la mise en oeuvre de nos solutions, contactez votre commercial ou cliquez sur [ce lien](https://www.ovhcloud.com/fr/professional-services/) pour obtenir un devis et demander une analyse personnalisée de votre projet à nos experts de l’équipe Professional Services.

Échangez avec notre [communauté d'utilisateurs](/links/community).
