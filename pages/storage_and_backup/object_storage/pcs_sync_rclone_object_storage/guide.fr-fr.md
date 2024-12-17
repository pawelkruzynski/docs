---
title: Object Storage Swift - Utiliser l'Object Storage avec rClone
updated: 2021-10-27
---

## Objectif

L'Object Storage d'OVH peut être synchronisé via rClone.

**Ce guide a pour objectif de vous rappeler les étapes pour effectuer cette synchronisation sur votre espace client OVH.**

rClone étant un logiciel de synchronisation externe, les détails d'utilisation de celui-ci sont à découvrir directement sur sa [documentation officielle](https://Rclone.org/).

## Prérequis

- Avoir créé son container *Object Storage* (depuis l'espace client ou depuis [Horizon](/pages/storage_and_backup/object_storage/pcs_create_container){.external}).
- Avoir créé un [utilisateur OpenStack](/pages/public_cloud/compute/create_and_delete_a_user){.external}.

## En pratique

Une fois votre container et votre utilisateur OpenStack créés, il vous reste deux choses à faire :

- Récupérer le fichier de configuration pour rClone :

Une fois votre [utilisateur OpenStack](/pages/public_cloud/compute/create_and_delete_a_user){.external} créé vous pourrez choisir, dans votre espace client, de récupérer le fichier de configuration nécessaire pour rClone.

Pour cela, quand vous êtes sur la page des utilisateurs OpenStack dans votre espace client, cliquez sur `...`{.action} à droite de l'utilisateur puis sur `Télécharger un fichier de configuration Rclone`{.action}.

![Télécharger un fichier de configuration Rclone](images/pcs_sync_rclone_pcs-20211008090532581.png)

- Configurer rClone :

Une fois le fichier téléchargé, vous pouvez lancer la commande suivante afin d’ajouter votre nouvel espace de stockage :

```sh
rclone config
```

Vous serez invité à insérer les données de configuration présentes dans votre fichier.

> [!primary]
>
> Vous pouvez également copier-coller le contenu de votre fichier dans l'espace dédié aux configurations de Rclone (*.config/Rclone/Rclone.conf*).
>

Une fois votre configuration effectuée, vous pouvez la tester en listant par exemple vos containers :

```sh
rclone lsd BackupStorage
```

*BackupStorage* correspond au nom donné à votre espace de stockage.

Vous trouverez sur le site officiel de rClone une documentation précise des actions à effectuer pour synchroniser votre Object Storage et rClone : [Documentation officielle rClone](https://Rclone.org/swift/){.external}.

## Aller plus loin

Si vous avez besoin d'une formation ou d'une assistance technique pour la mise en oeuvre de nos solutions, contactez votre commercial ou cliquez sur [ce lien](/links/professional-services) pour obtenir un devis et demander une analyse personnalisée de votre projet à nos experts de l’équipe Professional Services.

Échangez avec notre [communauté d'utilisateurs](/links/community).
