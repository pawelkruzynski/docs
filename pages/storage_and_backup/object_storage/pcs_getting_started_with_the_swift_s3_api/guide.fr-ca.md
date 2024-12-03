---
title: "Object Storage Swift - Premiers pas avec l'API Swift S3"
excerpt: "Découvrez comment utiliser l'API Swift S3"
updated: 2024-06-21
---

## Objectif

Le middleware Swift s3api qui assure la compatibilité de l'API S3 a été activé sur toutes les régions du Public Cloud.

**Ce guide vous aidera à accéder aux objets de Swift à l'aide d'un logiciel conçu pour interagir avec des points de terminaison compatibles S3.**

## Prérequis

- [Préparer l’environnement pour utiliser l’API OpenStack](/pages/public_cloud/compute/prepare_the_environment_for_using_the_openstack_api)
- [Obtenir le fichier Openstack RC v3 d'Horizon](/pages/public_cloud/compute/access_and_security_in_horizon)

## En pratique

### Définir les variables d'environnement OpenStack

```bash
user@host:~$ source <user_name>-openrc.sh
Please enter your OpenStack Password for project <project_name> as user <user_name>:

user@host:~$
```

### Installer le client OpenStack si nécessaire

```bash
user@host:~$ pip install python-openstackclient

user@host:~$
```

Retrouvez la référence des commandes Openstack client [ici](https://docs.openstack.org/python-openstackclient/latest/).

### Créer des informations d'identification EC2

Les jetons S3 sont différents, vous avez besoin de 2 paramètres (**access** et **secret**) pour générer un jeton S3.
Ces informations d'identification seront stockées en toute sécurité dans Keystone. Pour la générer :

#### Générer le jeton S3 avec le client python-openstack

```bash
user@host:~$ openstack ec2 credentials create
+------------+----------------------------------------------------------------------------------------------------------------------------+
| Field      | Value                                                                                                                      |
+------------+----------------------------------------------------------------------------------------------------------------------------+
| access     | 5a4d8b8d88104123a862c527ede5a3d3                                                                                           |
| links      | {u'self': u'https://auth.cloud.ovh.net/v3/users/d74d05ff121b44bea9216495e7f0df61/credentials/OS-                     |
|            | EC2/5a4d8b8d88104123a862c527ede5a3d3'}                                                                                     |
| project_id | 20e124b71be141299e111ec26b1892fa                                                                                           |
| secret     | 925d5fcfcd9f436d8ffcb20548cc53a2                                                                                           |
| trust_id   | None                                                                                                                       |
| user_id    | d74d05ff121b44bea9216495e7f0df61                                                                                           |
+------------+----------------------------------------------------------------------------------------------------------------------------+
```

#### Générer le jeton S3 avec curl

```bash
. openrc.sh
TMP_FILE=$(mktemp)
OS_USER_ID=$(curl -s -D $TMP_FILE -X POST "${OS_AUTH_URL}auth/tokens" -H "Content-Type: application/json" -d '{"auth":{"identity":{"methods":["password"],"password":{"user":{"name":"'$OS_USERNAME'","domain":{"id":"default"},"password":"'$OS_PASSWORD'"}}},"scope":{"project":{ "id":"'$OS_TENANT_ID'","domain":{"id":"default"}}}}}' | jq -r '.["token"]["user"]["id"]')
OS_TOKEN=$(awk 'BEGIN{IGNORECASE=1} /^X-Subject-Token/ {print $2}' $TMP_FILE |  tr -d "\r")
curl -s -X POST -H "Content-Type: application/json" -H "X-Auth-Token: $OS_TOKEN" -d '{"tenant_id": "'$OS_TENANT_ID'"}' "${OS_AUTH_URL}users/${OS_USER_ID}/credentials/OS-EC2" | jq .
{
  "credential": {
    "user_id": "d74d05ff121b44bea9216495e7f0df61",
    "links": {
      "self": "https://auth.cloud.ovh.net/v3/users/d74d05ff121b44bea9216495e7f0df61/credentials/OS-EC2/660c89cfc4764271ba169941c7b2f310"
    },
    "tenant_id": "20e124b71be141299e111ec26b1892fa",
    "access": "660c89cfc4764271ba169941c7b2f310",
    "secret": "fc9e8eb545724accadcfabbd99207df1",
    "trust_id": null
  }
}
```

### Configurer le client AWS

Installez le client AWS et configurez-le comme suit :

```bash
user@host:~$ pip install awscli
[...]
user@host:~$ cat ~/.aws/credentials

[default]
aws_access_key_id = <access_key>
aws_secret_access_key = <secret_key>

user@host:~$ cat ~/.aws/config

[plugins]
endpoint = awscli_plugin_endpoint

[profile default]
region = <region>
s3 =
  endpoint_url = https://s3.<region>.cloud.ovh.net
  signature_version = s3v4
s3api =
  endpoint_url = https://s3.<region>.cloud.ovh.net
```

L'accès de type `hébergé virtuel` et l'accès de type `chemin d'accès` sont pris en charge dans toutes les régions, mais nous vous recommandons d'utiliser le style `hébergé virtuel` car l'accès de type `chemin d'accès` sera déprécié après le 30 septembre 2020.

### Utiliser le client AWS

Utilisez la commande suivante pour obtenir la liste des Buckets (conteneurs) :

```bash
user@host:~$ aws --profile default s3 ls
```

Utilisez la commande suivante pour créer un nouveau bucket :

```bash
user@host:~$ aws --profile default s3 mb s3://bucket
```

S3 ne prend plus en charge la création de noms de bukcet contenant des lettres majuscules ou des traits de soulignement.
Les buckets S3 ne peuvent être créés que sur la stratégie PCS (Stockage d'objets).

Utilisez la commande suivante pour téléverser un fichier local sur Swift :

```bash
user@host:~$ aws --profile default s3 cp file.txt s3://bucket/file.txt
```

Utilisez la commande suivante pour télécharger un objet à partir de Swift :

```bash
user@host:~$ aws --profile default s3 cp s3://bucket/file.txt file.txt
```

Utilisez la commande suivante pour supprimer un objet Swift :

```bash
user@host:~$ aws --profile default s3 rm s3://bucket/file.txt
```

Utilisez la commande suivante pour supprimer un bucket:

```bash
user@host:~$ aws --profile default s3 rb s3://bucket
```

## Aller plus loin

Échangez avec notre [communauté d'utilisateurs](/links/community).
