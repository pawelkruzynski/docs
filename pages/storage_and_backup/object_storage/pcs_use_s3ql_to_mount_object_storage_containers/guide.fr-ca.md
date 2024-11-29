---
title: Object Storage Swift - Utiliser S3QL pour monter un conteneur Object Storage
updated: 2021-10-27
---

## Objectif

S3QL est un système de fichiers distant qui peut être configuré localement pour stocker des données à l'aide de solutions de stockage en nuage comme OVHcloud Object Storage.
Il présente plusieurs caractéristiques, telles que la compression des données, le cryptage et les instantanés des conteneurs, ce qui rend cette solution particulièrement adaptée à la création de sauvegardes.

Vous pouvez trouver plus d'informations directement sur leur [Site Web](http://www.rath.org/s3ql-docs/).

**Ce guide vous montre comment configurer un conteneur d'objets comme système de fichiers.**

## Prérequis

- [Configurer l'utilisateur](/pages/public_cloud/compute/loading_openstack_environment_variables)
- [Ajouter de l'espace de stockage](/pages/storage_and_backup/object_storage/pcs_create_container)

> [!primary]
>
> L'utilisation d'un conteneur d'objets comme système de fichiers peut avoir un impact sur la performance de vos opérations.
> La version S3ql 3.3 ou supérieure est requise.
>

## En pratique

### Créez votre système de fichiers

- Créer un fichier contenant les informations de connexion:

```bash
admin@serveur1:~$ sudo vim s3qlcredentials.txt

[swift]
backend-login: OS_PROJECT_ID:OS_USERNAME
backend-password: OS_PASSWORD
storage-url: swiftks://auth.cloud.ovh.net/REGION_NAME:CT_NAME
fs-passphrase: PASSPHRASE
```

Les paramètres OS_PROJECT_ID, OS_USERNAME et OS_PASSWORD peuvent être trouvés dans votre fichier OpenRC.

Les arguments REGION_NAME et CT_NAME peuvent être adaptés en fonction du nom et de l'emplacement de votre conteneur d'objets.

- Modifier les autorisations d'accès au fichier d'authentification:

```bash
admin@serveur1:~$ sudo chmod 600 s3qlcredentials.txt
```

- Formatage des conteneurs d'objets:

```bash
admin@serveur1:~$ sudo mkfs.s3ql --backend-options domain=default --authfile s3qlcredentials.txt swiftks://auth.cloud.ovh.net/REGION_NAME:CT_NAME
```

Vous devez ensuite ajouter la passphrase à votre fichier d'authentification.
Si vous ne voulez pas le configurer, vous devez supprimer la ligne "fs-passphrase : PASSPHRASE" de votre fichier de configuration.

### Configurez votre système de fichiers

- Créer le point de montage

```bash
admin@serveur1:~$ sudo mkdir /mnt/container
```

- Monter le conteneur

```bash
admin@serveur1:~$ sudo mount.s3ql --backend-options domain=default --authfile s3qlcredentials.txt swiftks://auth.cloud.ovh.net/REGION_NAME:CT_NAME /mnt/container/
```

- Vérifier le montage:

```bash
admin@serveur1:~$ sudo df -h

Filesystem Size Used Avail Use% Mounted on
/dev/vda1 9.8G 927M 8.5G 10% /
udev 10M 0 10M 0% /dev
tmpfs 393M 5.2M 388M 2% /run
tmpfs 982M 0 982M 0% /dev/shm
tmpfs 5.0M 0 5.0M 0% /run/lock
tmpfs 982M 0 982M 0% /sys/fs/cgroup
swiftks://auth.cloud.ovh.net/REGION_NAME:CT_NAME 1.0T 0 1.0T 0% /mnt/container
```

> [!warning]
>
> Vous ne pouvez pas utiliser S3QL en mode hors ligne. Vous ne devez pas configurer la persistance via le fichier /etc/fstab mais en utilisant un script qui sera exécuté au démarrage de votre serveur.
>

## Aller plus loin

Si vous avez besoin d'une formation ou d'une assistance technique pour la mise en oeuvre de nos solutions, contactez votre commercial ou cliquez sur [ce lien](https://www.ovhcloud.com/fr-ca/professional-services/) pour obtenir un devis et demander une analyse personnalisée de votre projet à nos experts de l’équipe Professional Services.

Échangez avec notre [communauté d'utilisateurs](/links/community).
