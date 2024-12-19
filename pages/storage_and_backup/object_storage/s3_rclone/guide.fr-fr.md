---
title: Object Storage - Utiliser Object Storage avec Rclone
excerpt: Découvrez comment configurer Rclone afin de synchroniser vos fichiers vers et depuis Object Storage
updated: 2024-05-20
---

## Objectif

[Rclone](https://rclone.org/){.external} est un outil de sauvegarde qui peut se synchroniser vers et depuis divers backends de stockage, et peut être utilisé sur Windows, macOS et Linux. Une documentation détaillée est également disponible sur le site officiel de Rclone : [Documentation officielle Rclone](https://rclone.org/docs/){.external}.

**Ce guide explique comment configurer Rclone afin de synchroniser vos fichiers vers et depuis Object Storage.**

> [!warning]
>
> OVHcloud met à votre disposition des services dont la configuration, la gestion et la responsabilité vous incombent. Il vous revient de ce fait d'en assurer le bon fonctionnement.
>
> Nous mettons à votre disposition ce guide afin de vous accompagner au mieux sur des tâches courantes. Néanmoins, nous vous recommandons de faire appel à un [prestataire spécialisé](/links/partner) et/ou de contacter l'éditeur du logiciel si vous éprouvez des difficultés. En effet, nous ne serons pas en mesure de vous fournir une assistance. Plus d'informations dans la section « Aller plus loin » de ce guide.
>

## Prérequis

- Avoir créé un bucket
- Avoir créé un utilisateur et avoir défini les droits d'accès requis sur le bucket
- Connaître vos informations d'identification Object Storage (access_key et secret_access_key).

Consultez notre guide « [Débuter avec Object Storage](/pages/storage_and_backup/object_storage/s3_getting_started_with_object_storage) » pour plus de détails.

> [!primary]
>
> Afin d'identifier votre Endpoint correspondant à votre classe de stockage, veuillez vous référer à ce guide : [Object Storage - Endpoints et géo-disponibilité de l’Object Storage](/pages/storage_and_backup/object_storage/s3_location)
>

## En pratique

Pour configurer Rclone, éditez ou créez le fichier `~/.config/rclone/rclone.conf` et ajoutez-y ceci :

```bash
[<profile_name>]
type = s3
provider = Other
env_auth = false
access_key_id = <access_key>
secret_access_key = <secret_key>
endpoint = https://s3.<region_in_lowercase>.io.cloud.ovh.net
acl = private
region = <region_in_lowercase>
location_constraint = <region_in_lowercase>
```

RClone est maintenant prêt à être utilisé.

**Exemples de commande**

Lister tous les buckets :

```bash
$ rclone lsd <profile_name>:
```

Créer un nouveau bucket :

```bash
$ rclone mkdir <profile_name>:mybucket
```

Lister le contenu d'un bucket :

```bash
$ rclone ls <profile_name>:mybucket
```

Synchroniser `/home/user/documents` vers un bucket :

```bash
$ rclone sync /home/user/documents <profile_name>:mybucket
```

Copier un fichier `/home/user/file.txt` dans un bucket :

```bash
$ rclone copy /home/user/file.txt <profile_name>:mybucket
```

Télécharger un fichier `file.txt` depuis un bucket :

```bash
$ rclone copy <profile_name>:mybucket/file.txt fichier.txt
```

Vous trouverez sur le site officiel de Rclone une documentation précise des actions possibles: [Documentation officielle Rclone](https://rclone.org/docs/){.external}.

## Aller plus loin

Si vous avez besoin d'une formation ou d'une assistance technique pour la mise en oeuvre de nos solutions, contactez votre commercial ou cliquez sur [ce lien](/links/professional-services) pour obtenir un devis et demander une analyse personnalisée de votre projet à nos experts de l’équipe Professional Services.

Échangez avec notre [communauté d'utilisateurs](/links/community).
