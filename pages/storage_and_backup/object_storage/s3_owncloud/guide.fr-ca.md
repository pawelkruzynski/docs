---
title: Object Storage - Utiliser S3 Object Storage avec Owncloud
excerpt: Découvrez comment configurer le stockage dans Owncloud pour utiliser un bucket S3 Object Storage
updated: 2024-05-20
---

## Objectif

Owncloud est une suite de logiciels client-serveur pour créer et utiliser des services d'hébergement de fichiers.

**Ce guide explique comment configurer le stockage dans Owncloud pour utiliser un bucket S3 Object Storage.**

> [!warning]
>
> OVHcloud met à votre disposition des services dont la configuration, la gestion et la responsabilité vous incombent. Il vous revient de ce fait d'en assurer le bon fonctionnement.
>
> Nous mettons à votre disposition ce guide afin de vous accompagner au mieux sur des tâches courantes. Néanmoins, nous vous recommandons de faire appel à un [prestataire spécialisé](https://partner.ovhcloud.com/fr-ca/directory/) et/ou de contacter l'éditeur du logiciel si vous éprouvez des difficultés. En effet, nous ne serons pas en mesure de vous fournir une assistance. Plus d'informations dans la section « Aller plus loin » de ce guide.
>

## Prérequis

- Avoir créé un bucket
- Avoir créé un utilisateur et avoir défini les droits d'accès requis sur le bucket
- Connaître vos informations d'identification S3 (access_key et secret_access_key).

Consultez notre guide « [Débuter avec S3 Object Storage](/pages/storage_and_backup/object_storage/s3_getting_started_with_object_storage) » pour plus de détails.

> [!primary]
>
> Afin d'identifier votre Endpoint correspondant à votre classe de stockage, veuillez vous référer à ce guide : [Object Storage - Endpoints et géo-disponibilité de l’Object Storage](/pages/storage_and_backup/object_storage/s3_location)
>

## En pratique

Si besoin, installez le plugin `External Storage: S3` depuis le `Market`{.action}.

![Owncloud open Market](images/HighPerf-Owncloud-20211209131331778.png){.thumbnail}

Recherchez le plugin `External Storage: S3`.

![Owncloud plugin External Storage S3](images/HighPerf-Owncloud-20211209131556714.png){.thumbnail}

Puis installez le plugin.

![Owncloud install plugin](images/HighPerf-Owncloud-20211209131648711.png){.thumbnail}

Rendez-vous dans les `Paramètres`{.action}.

![Owncloud open Settings](images/HighPerf-Owncloud-20211209131942821.png){.thumbnail}

Puis :

1. dans `Storage`{.action}
2. activez `Enable external storage `{.action}
3. nommez votre dossier
4. ajoutez un stockage de type `Amazon S3 compatible (SDK v3)`{.action}

![Owncloud create AWS S3 storage](images/HighPerf-Owncloud-20211209143008822.png){.thumbnail}

Renseignez les informations suivantes :

1. Indiquez le nom de votre bucket
2. Définissez l'hôte comme tel : `s3.<region_in_lowercase>.io.cloud.ovh.net`
3. Définissez le port : 443
4. Indiquez la région
5. Activez SSL
6. Renseignez votre clé d'accès
7. Renseignez votre clé secrète

![Owncloud complete AWS S3 storage](images/HighPerf-Owncloud-20211209133630272.png){.thumbnail}

Allez dans `Files`{.action}.

![Owncloud open Files](images/HighPerf-Owncloud-20211209133730832.png){.thumbnail}

Puis dans `External storage`{.action}.

![Owncloud Files External Storage](images/HighPerf-Owncloud-2021120913382299.png){.thumbnail}

Voici le résultat que vous devez obtenir :

![Owncloud Bucket listing](images/HighPerf-Owncloud-20211209140757288.png){.thumbnail}

## Aller plus loin

Si vous avez besoin d'une formation ou d'une assistance technique pour la mise en oeuvre de nos solutions, contactez votre commercial ou cliquez sur [ce lien](/links/professional-services) pour obtenir un devis et demander une analyse personnalisée de votre projet à nos experts de l’équipe Professional Services.

Échangez avec notre [communauté d'utilisateurs](/links/community).
