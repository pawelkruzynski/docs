---
title: ZMotion
excerpt: Comprendre le mécanisme de Zmotion
updated: 2020-07-13
---

## Objectif

ZMotion est une technologie OVHcloud qui transfère les données à travers un réseau privé client entre 2 baies de stockage physiques.

## En pratique 

### Description

Nos banques de données (datastores) exécutent NFS sur ZFS dans une baie de stockage maison appelée "Leclerc". Afin d'obtenir une meilleure flexibilité dans la gestion de notre matériel, nous avons développé un moyen de déplacer à chaud le stock de données ZFS d'un périphérique matériel à un autre.

Cette technologie est appelée "ZMotion", pour "ZFS Motion".

Le but de ZMotion est de libérer une banque de données (datastore) sans aucune action de vCenter (pas de vMotion, pas de clonage...) et sans aucune action de notre client.

![VMotion](images/zmotionPrez.png){.thumbnail}

### Etapes

- Un datastore gratuit, sur un autre *Leclerc*, est réservé dans notre datacenter pour pousser toutes les données.
- Nos propriétés réseau sont définies sur le datastore de destination
- Le transfert de données commence dans un réseau privé dédié au client
- Lorsque toutes les données sont transférées, le service NFS passe d'un tableau à un autre.

Du point de vue de VMware, il n'y a pas de temps d'arrêt.

## Aller plus loin

Échangez avec notre [communauté d'utilisateurs](/links/community).
