---
title: Object Storage - Managing object immutability with Object Lock (WORM)
excerpt: Object Lock is a feature that allows you to store objects using a Write Once, Read Many (WORM) model
updated: 2023-08-09
---

## Objective

Object Lock is a feature that allows you to store objects using a **W**rite **O**nce, **R**ead **M**any (WORM) model and can be used for scenarios where it is imperative that data is not changed or deleted after it has been written.

**This guide explains how to manage Object Lock**

## Concept

Object Lock provides two ways to manage object retention. The first is *retention periods* and the second is *Legal hold*.

### How does Object Lock work ?

To understand how Object Lock lock works, we must first understand how deletion of objects and versioning work together. When a delete object operation is performed on an object in a versioning-enabled bucket, it does not delete the object permanently but it creates a delete marker on the object. This delete marker becomes the latest and current version of the object with a new version id.

A delete marker has the following properties:

- A key and version ID like any other object.
- It does not have data associated with it, thus it does not retrieve anything from a GET request (you get a 404 error).
- By default, it is not displayed in the Control Panel UI anymore.
- The only operation you can use on a delete marker is DELETE, and only the bucket owner can issue such a request.

To permanently delete an object, you have to specify the version-id in your delete object request:

```bash
aws s3api delete-object --bucket my-bucket --key an-object --version-id 123456huijw0
```

The Object Lock feature prevents objects, for a fixed amount of time (retention mode) or indefinitely (legal hold), from being:

- deleted even if you specify the version id (you get an Access Denied error) ;
- overwritten by using versioning.

> [!primary]
>
> To use Object Lock, versioning must be activated.
>

### Retention periods

A retention period specifies a fixed period of time during which an object remains locked. During this period, your object is protected and can’t be overwritten or deleted. You apply a retention period either in number of days or number of years with the minimum being 1-day and no maximum limit.

When setting a retention period for your objects or buckets, you can choose the retention mode you wish to apply to your objects. You can choose either the *Governance mode* or the *Compliance mode* for your objects.

#### Governance mode

You should use the Governance mode if you want to protect objects from being deleted by most users during a pre-defined retention period, while authorising some users with special permissions to have the flexibility to alter the retention settings or delete the objects. Users with the `s3:BypassGovernanceRetention` permission can override or remove governance-mode retention settings.

#### Compliance mode

You should use the Compliance mode if you have a requirement to store compliant data.
When this mode is set, an object version cannot be overwritten or deleted by any user. If this mode is configured for an object, then its retention mode cannot be changed, and its retention period can’t be shortened.

> [!warning]
>
> You should only use the Compliance mode if you never want any user, including the administrator user, to be able to delete the objects during a pre-defined retention period.
>

### Legal hold

Designed for any situation where you are not sure for how long you want your objects to stay immutable, Legal hold is an ON/OFF switch that can be applied to every object in a locked bucket, independently from the lock configuration, the object retention or the object age. It can be applied to objects which are locked.

Legal hold provides the same protection as a retention period, but it has no expiration date. Instead, a Legal hold remains in place until you explicitly remove it.

## Requirements

- Your S3 credentials (access_key and secret_access_key)
- Aws cli installed and configured

See our [Getting started with S3 Object Storage](/pages/storage_and_backup/object_storage/s3_getting_started_with_object_storage) guide for more information.

## Instructions

> [!primary]
>
> All the following examples will use aws cli.
>
> To learn more about aws cli, please read this [guide](/pages/storage_and_backup/object_storage/s3_getting_started_with_object_storage).
>

### Permissions

| Name | Description |
|:--|:--|
| `s3:GetObjectRetention` | Allows users to view an object retention mode and retention period |
| `s3:PutObjectRetention` | Allows users to place an object retention configuration on an object |
| `s3:GetObjectLegalHold` | Allows users to view an object Legal hold status |
| `s3:PutObjectLegalHold` | Allows users to place a Legal hold on an object |
| `s3:GetBucketObjectLockConfiguration` | Allows users to view a bucket's default retention configuration |
| `s3:PutBucketObjectLockConfiguration` | Allows users to place an Object Lock configuration on the specified bucket  |
| `s3:BypassGovernanceRetention` | Allows users to bypass the Governance mode |

*Read this [guide](/pages/storage_and_backup/object_storage/s3_identity_and_access_management) to learn more about IAM.*

### Object Lock configuration

To use Object Lock, you have to create a bucket that supports the feature with the `--object-lock-enabled-for-bucket` flag. If a bucket is created without `--object-lock-enabled-for-bucket`, the flag cannot be added later.

> [!primary]
>
> The following command does not apply Object Lock to the bucket’s objects, it only activates the feature.
>

```bash
aws s3api create-bucket \
  --bucket object-lock-bucket \
  --object-lock-enabled-for-bucket
```

> [!primary]
>
> This action also enables versioning of the bucket.
>

### How to configure Object Lock on bucket

The lock configuration enables you to set a lock configuration on a specified bucket. Once set, the rule specified in the Object Lock configuration is applied by default to every new object placed in the specified bucket.

```bash
aws s3api put-object-lock-configuration \
    --bucket object-lock-bucket \
    --object-lock-configuration '{ "ObjectLockEnabled": "Enabled", "Rule": { "DefaultRetention": { "Mode": "GOVERNANCE", "Days": 60 }}}'
```

To view the Object Lock configuration of a bucket, run:

```bash
aws s3api get-object-lock-configuration \
   --bucket object-lock-bucket
```

The result should look like this:

```json
{
  "ObjectLockConfiguration": {
    "ObjectLockEnabled": "Enabled",
    "Rule": {
      "DefaultRetention": {
        "Mode": "GOVERNANCE",
        "Days": 60
      }
    }
  }
}
```

### How to configure an Object Lock retention period on an object

To set an object retention configuration on an object:

```bash
aws s3api put-object-retention \
       --bucket object-lock-bucket \
       --key test.txt \
       --retention '{ "Mode": "COMPLIANCE", "RetainUntilDate":
"2023-01-01T12:00:00.00Z" }'
```

> [!primary]
>
> The date format is standard iso8601: `Y-m-dTH:M:S.%3fZ`
>

To view the Object Lock retention configuration of an object, run:

```bash
aws s3api get-object-retention \
   --bucket object-lock-bucket \
   --key test.txt
```

The result should look like this:

```json
{
  "Retention": {
  "Mode": "COMPLIANCE",
  "RetainUntilDate": "2023-01-01T12:00:00Z"
  }
}
```

#### Bypassing Governance mode

> [!primary]
>
> If you have the `s3:BypassGovernanceRetention` permission, you can perform operations on object versions that are locked in governance mode as if they were unprotected.
>

To bypass governance mode, you must explicitly indicate in your request that you want to bypass this mode. To do this, include the `--bypass-governance-retention` header with your request:

```bash
aws s3api delete-object \
  --bucket object-lock-bucket \
  --key test.txt \
  --bypass-governance-retention
```

### How to configure an Object Lock Legal hold on an object

To set a Legal hold configuration to the specified object:

```bash
aws s3api put-object-legal-hold \
  --bucket object-lock-bucket \
  --key test.txt \
  --legal-hold Status=ON
```

To view the Object Lock Legal hold configuration of an object, run:

```bash
aws s3api get-object-legal-hold \
  --bucket object-lock-bucket \
  --key test.txt
```

The result should look like this:

```json
{
  "LegalHold": {
    "Status": "ON"
  }
}
```

## Go further

If you need training or technical assistance to implement our solutions, contact your sales representative or click on [this link]((/links/professional-services) to get a quote and ask our Professional Services experts for assisting you on your specific use case of your project.

Join our [community of users](/links/community).

**\***: S3 is a trademark of Amazon Technologies, Inc. OVHcloud’s service is not sponsored by, endorsed by, or otherwise affiliated with Amazon Technologies, Inc.
