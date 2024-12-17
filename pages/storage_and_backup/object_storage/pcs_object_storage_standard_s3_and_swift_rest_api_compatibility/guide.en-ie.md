---
title: Object Storage Swift - S3/Swift REST API compatibility
updated: 2022-03-23
---

## Objective

This guide lists the main features of Amazon S3 that are supported.

### S3/Swift REST API Comparison Matrix

| S3 REST API method | Swift S3 API |
| --- | :---: |
| GET Object | **Yes** |
| HEAD Object | **Yes** |
| PUT Object | **Yes** |
| PUT Object Copy | **Yes** |
| DELETE Object | **Yes** |
| Initiate Multipart Upload | **Yes** |
| Upload Part | **Yes** |
| Upload Part Copy | **Yes** |
| Complete Multipart Upload | **Yes** |
| Abort Multipart Upload | **Yes** |
| List Parts | **Yes** |
| GET Object ACL | **Yes** |
| PUT Object ACL | No |
| PUT Bucket | **Yes** |
| GET Bucket List Objects | **Yes** |
| HEAD Bucket | **Yes** |
| DELETE Bucket | **Yes** |
| List Multipart Uploads | **Yes** |
| GET Bucket acl | **Yes** |
| PUT Bucket acl | **Yes** |
| Versioning | **Yes** |
| Bucket notification | No |
| Bucket Lifecycle | No |
| Bucket policy | No |
| Public website | No |
| GET Bucket location | **Yes** |
| Delete Multiple Objects | **Yes** |
| Object tagging | No |
| GET Object torrent | No |
| Bucket inventory | No |
| GET Bucket service | No |
| Bucket accelerate | No |

## Go further

If you need training or technical assistance to implement our solutions, contact your sales representative or click on [this link](/links/professional-services) to get a quote and ask our Professional Services experts for assisting you on your specific use case of your project.

Join our [community of users](/links/community).

**\***: S3 is a trademark of Amazon Technologies, Inc. OVHcloud’s service is not sponsored by, endorsed by, or otherwise affiliated with Amazon Technologies, Inc.