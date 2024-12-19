---
title: Object Storage - Optimisez l'envoi de vos fichiers vers Object Storage
excerpt: Découvrez comment optimiser l'envoi de vos fichiers vers votre bucket
updated: 2021-12-08
---

## Objectif

Découvrez comment optimiser l'envoi de vos fichiers vers votre bucket.

## Prérequis

- [Avoir installé awscli](/pages/storage_and_backup/object_storage/s3_getting_started_with_object_storage)

## En pratique

Les commandes de transfert aws s3 sont multithreadées. À tout moment, plusieurs requêtes sont en cours.

Par exemple, si vous téléchargez un répertoire via `aws s3 cp localdir s3://bucket/ --recursive`, l'AWS CLI pourrait télécharger en parallèle les fichiers locaux localdir/file1, localdir/file2 et localdir/file3. La valeur `max_concurrent_requests` spécifie le nombre maximum de commandes de transfert autorisées à un moment donné.

Vous pouvez avoir besoin de modifier cette valeur pour plusieurs raisons :

- **Diminuer cette valeur**

Sur certains environnements, la valeur par défaut de 10 demandes simultanées peut submerger un système. Cela peut provoquer des interruptions de connexion ou ralentir la réactivité du système. En diminuant cette valeur, les commandes de transfert Object Storage seront moins gourmandes en ressources. La contrepartie est que les transferts Object Storage peuvent prendre plus de temps à se terminer. Il peut être nécessaire de réduire cette valeur si vous utilisez un outil tel que trickle pour limiter la bande passante.

- **Augmentation de cette valeur**

Dans certains scénarios, vous pouvez souhaiter que les transferts Object Storage se terminent aussi rapidement que possible, en utilisant autant de bande passante que nécessaire. Dans ce scénario, le nombre de requêtes simultanées par défaut peut ne pas être suffisant pour utiliser toute la bande passante du réseau disponible. L'augmentation de cette valeur peut améliorer le temps nécessaire à la réalisation d'un transfert Object Storage.

Cette valeur doit être définie sous la clé s3 de premier niveau dans le fichier de configuration AWS, dont l'emplacement par défaut est `~/.aws/config`.

```bash
user@host:~$ cat ~/.aws/config

[profile default]
region = <region_in_lowercase>
s3 =
  endpoint_url = https://s3.<region_in_lowercase>.perf.cloud.ovh.net
  max_concurrent_requests = 20
  signature_version = s3v4
s3api =
  endpoint_url = https://s3.<region_in_lowercase>.perf.cloud.ovh.net
```

Vous pouvez également définir cette valeur à l'aide de la commande `aws configure set`.

```bash
aws configure set default.s3.max_concurrent_requests 20
```

## Aller plus loin

Si vous avez besoin d'une formation ou d'une assistance technique pour la mise en oeuvre de nos solutions, contactez votre commercial ou cliquez sur [ce lien](/links/professional-services) pour obtenir un devis et demander une analyse personnalisée de votre projet à nos experts de l’équipe Professional Services.

Échangez avec notre [communauté d'utilisateurs](/links/community).
