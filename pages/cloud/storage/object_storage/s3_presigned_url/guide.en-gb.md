# Introduction

By default, all objects are private ie only the object owner has permission to access them. However, objects can be shared temporarily with others by using a presigned URL to grant time-limited permission to download the objects without having the need to re-configure permissions.

Please note that anyone who has access to the presigned url can download your object, so we recommand that you protect it carefully.



# In practice

## Prerequisites

Make sure you have the necessary permissions by using the credentials of the object owner (by default, the owner of the bucket).

## Using the cli

To generate a presigned URL to share an object using the AWS CLI, you can use the *presign* command :

```bash
$ aws s3 presign s3://<bucket>/<key>
```

Example:

```bash
$ aws s3 presign s3://gribs/grib-file
https://s3.gra.perf.cloud.ovh.net/gribs/grib-file?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Credential=5ba255c12baf43be9d00289070faf936%2F20230221%2Fgra%2Fs3%2Faws4_request&X-Amz-Date=20230221T142726Z&X-Amz-Expires=3600&X-Amz-SignedHeaders=host&X-Amz-Signature=a43dc63c483d469f6f747ef041a434145b3661541e95e4334eee3a96e059e15e

```
