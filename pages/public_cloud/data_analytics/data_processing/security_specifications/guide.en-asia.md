---
title: Security specifications for Data Processing
excerpt: Data Processing security overview
updated: 2024-03-01
---

## Objective

This security fact sheets aims at describing security features and functions associated to the service. It describes also best practices that customers can adopt to secure their Data Processing service that can be activated on a Public Cloud project.

## 1. Certifications

- ISO/IEC 27001
- ISO/IEC 27701
- ISO/IEC 27017
- ISO/IEC 27018
- HDS
- SOC 1 type 1
- SOC 2 type 1
- CSA type 1
- C5 type 1

## 2. Best pratices to be deployed on the service

### 2.1 Recommandations once the service is delivered

You must filter connections to tier processes and apply [IP restriction](/pages/public_cloud/data_analytics/data_processing/01_CONCEPTS_Capabilities) in order to access your data.

Once you have subscribed to the OVHcloud Object storage service, use best practices to secure your access to your Object storage service such as [collecting credentials](/pages/storage_and_backup/object_storage/s3_getting_started_with_object_storage) or [managing accesses](/pages/storage_and_backup/object_storage/s3_identity_and_access_management).

### 2.2 Vulnerability scans

You are authorized to perform vulnerability scans on the service you have subscribed to. OVHcloud doesn't have to be previously informed.<br>
Security measures deployed by OVHcloud (especially network protection) aren't disabled, because such an audit's purpose is to demonstrate a clear vision of the security level of the customer's infrastructure.<br>
You are not authorized to use your service to scan other infrastructures.<br>
Tests could be made on the service API and the web page for spark dashboard (stateless).

## 3. SLA

In the event of a Job failing as part of the Service, the Client may receive a credit which equals to 100% of the amount paid by the Client for the portion of the Service affected during the month in question, with a limit of up to five (5) hours per Job.

In case of a subscription to the Object storage service, SLA of this service applies too. More details are available in particular conditions of the service.

## 4. Backups and retention

You are autonomous for defining data input and output for your storage purpose.

The object storage service is used for two objectives : job code (as an input) and job logs (as an output).

You must use High Performance Object Storage for temporary storage or store checkpoints for Spark Streaming

To lock your data stored in the Object Storage service, manage versioning and preventing from unwanted modification or deletion, you can follow this guide for [data immutability on Object storage service](/pages/storage_and_backup/object_storage/s3_managing_object_lock).

## 5. Logs

| **Source** | **Content** | **Documentation** |
| --- | --- | --- |
| Control Panel | Logs of interactions made by admin, technical or billing contacts in the Control Panel and services they have access to, using API calls. | - <https://ca.api.ovh.com/console/#/me> (see `/me/api/logs`)<br> - [List of API calls done with your account](https://ca.api.ovh.com/console/#/me/api/logs/self~GET)<br> - [List of API calls done on services you have access to](https://ca.api.ovh.com/console/#/me/api/logs/services~GET)<br> -[Get your audit logs](https://ca.api.ovh.com/console/#/me/logs/audit~GET) |
| Service | Logs generated by your job environment creation and execution following your configurations. | Logs are available in the Control Panel in real time (see sheet 'logs') and can be also downloaded from the Object Storage service with CLI or via API, following [these indications](/pages/public_cloud/data_analytics/data_processing/21_GETTINGSTARTED_check-job-logs). |

## 6. API

| **Name** | **Capacity** | **Link** |
| --- | --- | --- |
| Control Panel and service | Manage customer accounts and services on which each account has access rights. | [Documentation on how to use API](/pages/public_cloud/data_analytics/data_processing/38_HOWTO_use-with-ovh-api) <br> [API link](https://ca.api.ovh.com/console/#/cloud) |

## 7. Users accounts

### 7.1 Control plane

Using your customer account on the OVHcloud Control Panel, you are able to manage your service using [three different contacts](/pages/account_and_service_management/account_information/managing_contacts).<br>
OVHcloud uses another account with an internal NIC to refer a customer having subscribed to several services.

To enforce security access to your account on the Control Panel, we recommend activating a [two-factor authentication mechanism](/pages/account_and_service_management/account_information/secure-ovhcloud-account-with-2fa) or [SSO(Single Sign-On) authentication](/pages/account_and_service_management/account_information/ovhcloud-account-connect-saml-adfs).

### 7.2 Data plane

Once you have activated the service and retrieved your API v6 token, you can create your jobs.

## 8. Features and options available at service delivery

### 8.1 Segregation, monitoring and vulnerability management

OVHcloud teams ensure segregation between customer's clusters as for each Spark job submitted. A user's Spark cluster is created in an isolated and unique Kubernetes namespace dedicated to that job and it is limited, isolated and secured using Kubernetes Network Policies and Pod Security Policies.<br>

OVHcloud teams monitor all components in support of the service as well as CVE handling and correction.

### 8.2 Data encryption

Once you use the OVHcloud Object Storage service, you can manage data encryption on server-side by following [this guide](/pages/storage_and_backup/object_storage/s3_encrypt_your_objects_with_sse_c).

### 8.3 HDS option

The HDS option can be activated on the service.<br>
The subscription to the Business support level is mandatory, at least to maintain necessary requirements.

## 9. Reversibility

OVHcloud provides this service based on Apache Spark technology without any specific customization (Vanilla). You are able to use to use all modules and codes supported by the technology following your business needs.<br>

Data storage technology is based on S3 **\*** compatible Object Storage or SWIFT Object Storage technology and you are able to import and export your data at anytime using API calls.

### 9.1 Erasure of customer data

Once the job is executed, no data are retained on OVHcloud infrastructure and all allocated resources are destroyed.

To destroy stored data and logs , you have to use API calls to destroy your Object Storage.

## Feedback

Please send us your questions, feedback and suggestions to improve the service:

- On the OVHcloud [Discord server](https://discord.com/invite/vXVurFfwe9)

**\***: S3 is a trademark of Amazon Technologies, Inc. OVHcloud’s service is not sponsored by, endorsed by, or otherwise affiliated with Amazon Technologies, Inc.