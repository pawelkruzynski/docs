---
title: Object Storage Swift - Erste Schritte mit der Swift S3 API
excerpt: "So verwenden Sie die Swift S3 API"
updated: 2024-06-21
---

## Ziel

Die Swift s3api Middleware, die die Kompatibilität der S3 API sicherstellt, wurde in allen Regionen der Public Cloud aktiviert.

**Diese Anleitung erklärt den Zugriff auf Swift-Objekte über S3-kompatible Endpunkte mithilfe kompatibler Software.**

## Voraussetzungen

- [Umgebung für die Verwendung der OpenStack-API vorbereiten](/pages/public_cloud/compute/prepare_the_environment_for_using_the_openstack_api)
- [Die OpenStack RC von Horizon beziehen](/pages/public_cloud/compute/access_and_security_in_horizon)

## In der praktischen Anwendung

### OpenStack-Umgebungsvariablen festlegen

```bash
user@host:~$ source <user_name>-openrc.sh
Please enter your OpenStack Password for project <project_name> as user <user_name>:

user@host:~$
```

### Installieren Sie den OpenStack-Client

```bash
user@host:~$ pip install python-openstackclient

user@host:~$
```

Hier finden Sie die Referenz zur [OpenStack-Kommandozeilensteuerung](https://docs.openstack.org/python-openstackclient/latest/).

### EC2-Authentifizierung erstellen

Un S3 Token zu generieren, benötigen Sie zwei Parameter ("**access**" und "**secret**").
Diese Login-Daten werden sicher in Keystone gespeichert. Sie können auf zwei Arten erstellt werden:

#### S3 Token mit dem Python-Openstack-Client erstellen

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

#### S3 Token mit curl erstellen

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

### AWS Client konfigurieren

Installieren Sie den AWS Client und konfigurieren Sie ihn wie folgt:

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

Zugänge der Typen `virtual hosted-style` und `path-style` werden in allen Regionen unterstützt. Wir empfehlen Ihnen jedoch, `virtual hosted-style` zu verwenden, da `path-style` nach dem 30. September 2020 nicht mehr aktualisiert wird.

### AWS Client verwenden

Verwenden Sie folgenden Befehl, um die Liste der Buckets (Container) zu erhalten:

```bash
user@host:~$ aws --profile default s3 ls
```

Verwenden Sie folgenden Befehl, um einen neuen Bucket zu erstellen:

```bash
user@host:~$ aws --profile default s3 mb s3://bucket
```

> [!primary]
>
> S3 Buckets können nur aufgrund der PCS Policy (Object Storage) erstellt werden.
>

> [!primary]
>
> Der Name des Containers muss folgenden Regeln entsprechen:
>  
> - Der Name des Containers darf zwischen 3 und 63 Zeichen lang sein und darf nur Kleinbuchstaben, Ziffern, Punkte und Minuszeichen enthalten.  
> - Der Name des Containers muss mit einem Kleinbuchstaben oder einer Ziffer beginnen.  
> - Der Name des Containers darf keine Unterstriche enthalten, mit einem Minus enden, aufeinander folgende Punkte haben oder Minuszeichen neben Punkten verwenden.  
> - Der Name des Containers kann nicht als IP-Adresse (198.51.100.24) formatiert werden.  
>

Eine lokale Datei zu Swift hochladen:

```bash
user@host:~$ aws --profile default s3 cp file.txt s3://bucket/file.txt
```

Ein Objekt von Swift herunterladen:

```bash
user@host:~$ aws --profile default s3 cp s3://bucket/file.txt file.txt
```

Ein Swift-Objekt löschen:

```bash
user@host:~$ aws --profile default s3 rm s3://bucket/file.txt
```

Einen Bucket löschen:

```bash
user@host:~$ aws --profile default s3 rb s3://bucket
```

## Weiterführende Informationen

Wenn Sie Schulungen oder technische Unterstützung bei der Implementierung unserer Lösungen benötigen, wenden Sie sich an Ihren Vertriebsmitarbeiter oder klicken Sie auf [diesen Link](/links/professional-services), um einen Kostenvoranschlag zu erhalten und eine persönliche Analyse Ihres Projekts durch unsere Experten des Professional Services Teams anzufordern.

Für den Austausch mit unserer User Community gehen Sie auf <https://community.ovh.com/en/>.
