---
title: "Object Storage Swift - Iniziare a utilizzare l'API Swift S3"
excerpt: "Come utilizzare l'API Swift S3"
updated: 2024-06-21
---

## Obiettivo

Il middleware Swift s3api, che assicura la compatibilità dell'API S3, è stato attivato su tutte le Region del Public Cloud.

**Questa guida ti mostra come accedere agli oggetti Swift utilizzando un software progettato per interagire con punti terminali compatibili con S3.**

## Prerequisiti

- [Preparare l’ambiente per utilizzare l’API OpenStack](/pages/public_cloud/compute/prepare_the_environment_for_using_the_openstack_api)
- [Parametri di accesso e sicurezza in Horizon](/pages/public_cloud/compute/access_and_security_in_horizon)

## Procedura

### Definisci le variabili d'ambiente OpenStack

```bash
user@host:~$ source <user_name>-openrc.sh
Please enter your OpenStack Password for project <project_name> as user <user_name>:

user@host:~$
```

### Installare il client OpenStack se necessario

```bash
user@host:~$ pip install python-openstackclient

user@host:~$
```

Visualizza il referenza degli ordini del client Openstack [qui](https://docs.openstack.org/python-openstackclient/latest/).

### Crea informazioni di identificazione EC2

I token S3 sono diversi: per generare un token S3 sono necessari 2 parametri (**accesso** e **segreto**).
Queste informazioni di identificazione saranno salvate in tutta sicurezza in Keystone. Per generare:

#### Genera il token S3 con il client python-openstack

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

#### Genera il token S3 con curl

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

### Configura il client AWS

Installa il client AWS e configuralo come segue:

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

L'accesso di tipo `hostato virtuale` e l'accesso di tipo `percorso di accesso` sono supportati in tutte le Region, ma ti consigliamo di utilizzare lo stile `hosting virtuale` perché l'accesso di tipo `percorso di accesso` sarà svalutato dopo il 30 settembre 2020.

### Utilizza il client AWS

Per visualizzare la lista dei Buckets (container) utilizza questo comando:

```bash
user@host:~$ aws --profile default s3 ls
```

Per creare un nuovo bucket utilizza questo comando:

```bash
user@host:~$ aws --profile default s3 mb s3://bucket
```

> [!primary]
>
> I cuscinetti S3 possono essere creati solo sulla strategia PCS (Storage di oggetti).
>

> [!primary]
>
> Il nome del container deve rispettare queste regole:
>  
> - Il nome del container può contenere da 3 a 63 caratteri e può contenere solo lettere minuscole, cifre, punti e trattini.  
> - Il nome del container deve iniziare con una lettera minuscola o una cifra.  
> - Il nome del container non può contenere tratti di sottolineatura, terminare con un trattino, avere punti consecutivi o utilizzare trattini adiacenti a punti.  
> - Il nome del container non può essere formattato come un indirizzo IP (198.51.100.24).  
>

Utilizza questo comando per trasferire un file locale su Swift:

```bash
user@host:~$ aws --profile default s3 cp file.txt s3://bucket/file.txt
```

Per scaricare un oggetto da Swift utilizza questo comando:

```bash
user@host:~$ aws --profile default s3 cp s3://bucket/file.txt file.txt
```

Per eliminare un oggetto Swift, utilizza questo comando:

```bash
user@host:~$ aws --profile default s3 rm s3://bucket/file.txt
```

Per eliminare un bucket utilizza questo comando:

```bash
user@host:~$ aws --profile default s3 rb s3://bucket
```

## Per saperne di più

Se avete bisogno di formazione o di assistenza tecnica per implementare le nostre soluzioni, contattate il vostro rappresentante o cliccate su [questo link](/links/professional-services) per ottenere un preventivo e richiedere un'analisi personalizzata del vostro progetto da parte dei nostri esperti del team Professional Services.

Contatta la nostra Community di utenti all’indirizzo <https://community.ovh.com/en/>.

**\***: S3 is a trademark of Amazon Technologies, Inc. OVHcloud’s service is not sponsored by, endorsed by, or otherwise affiliated with Amazon Technologies, Inc.