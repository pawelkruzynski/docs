---
title: Object Storage - Optimise the sending of your files to Object Storage
excerpt: Learn how to optimise the sending of your files to your bucket
updated: 2021-12-08
---

## Objective

Learn how to optimise the sending of your files to your bucket.

## Requirements

- [awscli](/pages/storage_and_backup/object_storage/s3_getting_started_with_object_storage) installed

## Instructions

The aws s3 transfer commands are multithreaded. At any time, several requests are in progress.

For example, if you download a directory via `aws s3 cp localdir s3://bucket/ --recursive`, the AWS CLI might download localdir/file1, localdir/file2 and localdir/file3 in parallel. The `max_concurrent_requests` value specifies the maximum number of transfer commands allowed at any single time.

You may need to change this value for several reasons:

- **Decrease this value**

On some environments, the default value of 10 concurrent requests can overwhelm a system. This can cause connection interruptions or slow down system responsiveness. By lowering this value, Object Storage transfer commands will be less resource-intensive. The downside is that Object Storage transfers may take longer to complete. It may be necessary to reduce this value if you are using a tool such as trickle to limit bandwidth.

- **Increasing this value**

In some scenarios, you may want Object Storage transfers to complete as quickly as possible, using as much bandwidth as necessary. In this scenario, the default number of concurrent requests may not be sufficient to use all available network bandwidth. Increasing this value can improve the time required to complete an Object Storage transfer.

This value should be set under the top-level s3 key in the AWS configuration file, whose default location is `~/.aws/config`.

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

You can also set this value using the `aws configure set` command.

```bash
aws configure set default.s3.max_concurrent_requests 20
```

## Go further

If you need training or technical assistance to implement our solutions, contact your sales representative or click on [this link](/links/professional-services) to get a quote and ask our Professional Services experts for assisting you on your specific use case of your project.

Join our [community of users](/links/community).

