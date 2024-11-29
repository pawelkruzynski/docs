---
title: VMware Storage vMotion
excerpt: Déplacer votre machine virtuelle sur un hôte différent à chaud
updated: 2020-07-10
---

## Objectif

Le **Storage vMotion** permet de modifier l'emplacement de stockage des fichiers de la machine virtuelle et cela en conservant la machine virtuelle sous tension. Il est possible de déplacer la machine virtuelle complètement ou disque par disque.

**Ce guide montre comment réaliser cette opération.**

## En pratique

### Déplacer le disque d'une machine virtuelle

Pour déplacer les fichiers d'une machine virtuelle vers un autre datastore, il vous suffit de faire un clic droit sur la machine virtuelle allumée puis de sélectionner le menu `Migrer...`.

![déplacer disque](images/VmotionStorage1.png){.thumbnail}

### Choix du type de vMotion

Le menu propose plusieurs options de **vMotion**. Dans notre exemple, nous désirons uniquement migrer la machine virtuelle sur une autre banque de données. Il faut donc sélectionner « Modifier uniquement le stockage ».

L'option « Modifier uniquement la ressource de calcul » permet de migrer la machine virtuelle sur un autre hôte.  

Cette opération appelé **vMotion** est décrit dans [ce guide](/pages/hosted_private_cloud/hosted_private_cloud_powered_by_vmware/vmware_vmotion_new).

![choix de vMotion](images/VmotionStorage2.png){.thumbnail}

### Choix du datastore

Choisissez vers quel stockage migrer les données.

Il est également possible de modifier la politique de stockage lors de cette opération.

Ainsi, vous pouvez appliquer les politiques de stockage créées si vous disposez d'un [stockage vSAN](/pages/hosted_private_cloud/hosted_private_cloud_powered_by_vmware/vmware_vsan) ou de l'option [VMencryption](/pages/hosted_private_cloud/hosted_private_cloud_powered_by_vmware/vm_encrypt).

![choix datastore](images/VmotionStorage3.png){.thumbnail}

Dans le cas ou vous avez plusieurs disques virtuels sur la même machine, il est possible de ne migrer qu'un seul disque de la VM en utilisant le bouton `Advanced`{.action}.

Vous retrouverez cette vue :

![datastore vMotion](images/VmotionStorage6.png){.thumbnail}

### Finaliser le vMotion

Cliquez sur `Terminer`{.action} pour lancer la procédure de migration.

![finaliser le vMotion](images/VmotionStorage4.png){.thumbnail}

### Suivi du vMotion

Dans les tâches récentes, vous pourrez suivre l'état de la migration. Celle-ci prend plus ou moins de temps selon la taille de la VM, les accès IO et la bande passante utilisée.

![suivi de vMotion](images/VmotionStorage5.png){.thumbnail}

## Aller plus loin

Échangez avec notre [communauté d'utilisateurs](/links/community).
