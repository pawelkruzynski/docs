---
title: Object Storage Swift - Getting started with the Swift S3 API
excerpt: 'Getting started with the Swift S3 API'
updated: 2024-06-21
---

## Objective

The Swift s3api middleware providing S3 API compatibility has been enabled on all Public Cloud regions.

**This guide will help you access objects in Swift using a software designed to interact with S3-compatible endpoints.**

## Requirements

- [Prepare the environment to use the OpenStack API](/pages/public_cloud/compute/prepare_the_environment_for_using_the_openstack_api)
- [Get the Openstack RC File v3 from Horizon](/pages/public_cloud/compute/access_and_security_in_horizon)

## Instructions

### Set the OpenStack environment variables

```bash
user@host:~$ source <user_name>-openrc.sh
Please enter your OpenStack Password for project <project_name> as user <user_name>:

user@host:~$
```

### Install OpenStack client if needed

```bash
user@host:~$ pip install python-openstackclient

user@host:~$
```

OpenStack client command reference [here](https://docs.openstack.org/python-openstackclient/latest/).

### Create EC2 credentials

S3 tokens are different, you need 2 parameters (**access** and **secret**) to generate a S3 token.
These credentials will be safely stored in Keystone. To generate it:

With python-openstack client:

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

With curl:

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

### Configure AWS client

Install the AWS client and configure it as follows:

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

Virtual hosted-style and path-style access are supported in all regions, but we recommend to use virtual hosted-style since path-style access will be deprecated after September 30, 2020.

### Use AWS client

List buckets (containers):

```bash
user@host:~$ aws --profile default s3 ls
```

Create a new bucket:

```bash
user@host:~$ aws --profile default s3 mb s3://bucket
```

> [!primary]
>
> S3 Buckets can only be created on PCS policy (Object Storage).
>

> [!primary]
>
> The container name must respect the following rules.
>
> - The bucket name can be between 3 and 63 characters long, and can contain only lower-case characters, numbers, periods, and dashes.  
> - Each bucket name must start with a lowercase letter or number.  
> - The bucket name cannot contain underscores, end with a dash, have consecutive periods, or use dashes adjacent to periods.  
> - The bucket name cannot be formatted as an IP address (198.51.100.24).  
>

Upload a local file to Swift:

```bash
user@host:~$ aws --profile default s3 cp file.txt s3://bucket/file.txt
```

Download an object from Swift:

```bash
user@host:~$ aws --profile default s3 cp file.txt s3://bucket/file.txt
```

Delete a Swift object:

```bash
user@host:~$ aws --profile default s3 rm s3://bucket/file.txt
```

Delete a bucket:

```bash
user@host:~$ aws --profile default s3 rb s3://bucket
```

## Go further

- OpenStack client command reference [here](https://docs.openstack.org/python-openstackclient/latest/)
- S3 client command reference [here](https://docs.aws.amazon.com/cli/latest/reference/s3/index.html)

If you need training or technical assistance to implement our solutions, contact your sales representative or click on [this link]((/links/professional-services) to get a quote and ask our Professional Services experts for assisting you on your specific use case of your project.

Join our [community of users](/links/community).

**\***: S3 is a trademark of Amazon Technologies, Inc. OVHcloud’s service is not sponsored by, endorsed by, or otherwise affiliated with Amazon Technologies, Inc.
