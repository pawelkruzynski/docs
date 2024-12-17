---
title: Cloud Archive Swift - Capabilities and limitations (EN)
excerpt: Find here the main capacities and limitations for the management of your containers
updated: 2021-09-23
---

## Objective

The purpose of this guide is to outline the main capacities and limitations for managing your containers.

## Instructions

> [!primary]
>
> You can view some of this information directly from a browser by going to: `https://storage.<region>.cloud.ovh.net/info`, or, if you are using python-swiftclient, via the command: `swift capabilities`.
>

### container_listing_limit = 10000

The default (and maximum) number of items returned for a container list request.

Show all items with python-swiftclient:

```bash
swift list <container>

container_listing_limit/00001
container_listing_limit/00002
container_listing_limit/00003
container_listing_limit/00004
container_listing_limit/00005
container_listing_limit/00006
container_listing_limit/00007
[...]
container_listing_limit/10038
```

Show only the first 10000 objects:

```bash
curl -i "https://storage.gra.cloud.ovh.net/v1/AUTH_702xxxxxxxxxxxxxxxxxxxxxxxxxxdaf/<container>" -X GET -H `X-Auth-Token: xxx`
```

```
Content-Length: 300000
X-Container-Object-Count: 10038
X-Timestamp: 1627567737.86773
Accept-Ranges: bytes
X-Storage-Policy: PCA
Last-Modified: Mon, 02 Aug 2021 07:20:42 GMT
X-Container-Bytes-Used: 973749
Content-Type: text/plain; charset=utf-8
Vary: Accept
X-Trans-Id: tx03e7a5725123423d9962c-0061080b90
X-Openstack-Request-Id: tx03e7a5725123423d9962c-0061080b90
Date: Mon, 02 Aug 2021 15:13:20 GMT
X-IPLB-Request-ID: 6DBEFE1E:A1BE_3626E64B:01BB_61080B90_3F0404F:1454
X-IPLB-Instance: 38342

container_listing_limit/00001
container_listing_limit/00002
container_listing_limit/00003
container_listing_limit/00004
container_listing_limit/00005
container_listing_limit/00006
container_listing_limit/00007
[...]
container_listing_limit/10000
```

You can use the `marker`, `limit`, and `end_marker` parameters to control how many items are returned in a list and where the list starts or ends.

| Setting | Type | Description |
|:----------|:-----|:------------|
| marker | string | To get the following names, you must make another request with the marker parameter. Set the marker parameter to the last item returned in the previous list. |
| limit | integer | Use the limit parameter to return fewer than 10,000 names. |
| end_marker | string | Restricts the result set to names that are less than the end_marker value. |

Show more via `marker`:

```bash
curl -i "https://storage.gra.cloud.ovh.net/v1/AUTH_702xxxxxxxxxxxxxxxxxxxxxxxxxxdaf/<conteneur>?marker=container_listing_limit/10000" -X GET -H "X-Auth-Token: xxx"
```

```output
Content-Length: 10038
X-Container-Object-Count: 10038
X-Timestamp: 1627567737.86773
Accept-Ranges: bytes
X-Storage-Policy: PCA
Last-Modified: Mon, 02 Aug 2021 07:20:42 GMT
X-Container-Bytes-Used: 973749
Content-Type: text/plain; charset=utf-8
Vary: Accept
X-Trans-Id: tx03e7a5725123423d9962c-0061080b90
X-Openstack-Request-Id: tx03e7a5725123423d9962c-0061080b90
Date: Mon, 02 Aug 2021 15:13:20 GMT
X-IPLB-Request-ID: 6DBEFE1E:A1BE_3626E64B:01BB_61080B90_3F0404F:1454
X-IPLB-Instance: 38342

container_listing_limit/10001
container_listing_limit/10002
container_listing_limit/10003
container_listing_limit/10004
container_listing_limit/10005
container_listing_limit/10006
container_listing_limit/10007
[...]
container_listing_limit/10038
```

### max_container_name_length = 256

The maximum number of bytes in utf8 encoding of a container name.

```bash
max_container_name_length="max_container_name_length_$(cat /dev/urandom | tr -dc "a-zA-Z0-9" | fold -w 300 | head -n1)"
swift post $max_container_name_length
```

```
Container PUT failed: https://storage.gra.cloud.ovh.net/v1/AUTH_702xxxxxxxxxxxxxxxxxxxxxxxxxxdaf/max_container_name_length_MoZOkNO4bnbrTR6iQz2kXMstW3D5STEF6Ojw48oOEat3pTMWL47gHomhl5FRx7biOz2ELDIlSaVI4757vSP6lgqKIQlDS36lMLSitWSLoD7CDnQ6mWW5GpnwNxrtKsxT6jLYOCbrknEmpXTSOqfoFmaqSwc7g3ZLbxP1zUJ1EKp1xJVI7ZoQg4VqRX6iQtZreVlbhe0mc9n1Chia1zE4JHduGV9HkeMJyRIpAe7yTN83L7rCz0EdXwFMTSfJzYs4l01Ph0LKvogenhQzTMFtLIS57hMgOPYMVnfhCzHBNiZY 400 Bad Request   b'Container name length of 326 longer than 256'
Failed Transaction ID: txd3664103d22a445687c5a-00610a32e3
```

### max_file_size = 5368709122 (5Gb)

The largest normal object that can be saved in the cluster. This is also the limit on the size of each segment of a large object when using the large object manifest media. This value is set in bytes. If it is less than 1MiB, some tests will fail. It is STRONGLY recommended to leave this value as the default (`5 * 2**30 + 2`).

```bash
swift upload <container> <largeobject>
```

```
Object PUT failed: https://storage.gra.cloud.ovh.net/v1/AUTH_702xxxxxxxxxxxxxxxxxxxxxxxxxxdaf/<conteneur>/<largeobject> 413 Request Entity Too Large   b'Your request is too large.'
Consider using the --segment-size option to chunk the object
```

```bash
swift upload --use-slo --segment-size 1G <container> <largeobject>
```

```
<largeobject> segment 5
<largeobject> segment 4
<largeobject> segment 0
<largeobject> segment 1
<largeobject> segment 2
<largeobject> segment 3
<largeobject>
```

```bash
swift list <container_segments>
```

```
<largeobject>/slo/1627934910.652204/6442450944/1073741824/00000000
<largeobject>/slo/1627934910.652204/6442450944/1073741824/00000001
<largeobject>/slo/1627934910.652204/6442450944/1073741824/00000002
<largeobject>/slo/1627934910.652204/6442450944/1073741824/00000003
<largeobject>/slo/1627934910.652204/6442450944/1073741824/00000004
<largeobject>/slo/1627934910.652204/6442450944/1073741824/00000005
```

### max_meta_count = 90

The maximum number of metadata keys that can be stored on a single account, container, or object.

```bash
for i in $(seq 1 100)
do
swift post -m "max_meta_count_$i:value" <container>
done
```

```output
Container POST failed: https://storage.gra.cloud.ovh.net/v1/AUTH_702xxxxxxxxxxxxxxxxxxxxxxxxxxdaf/<container> 400 Bad Request  b'Too many metadata items; max 90'
Failed Transaction ID: txef5aa187467c4c949c0d4-00610a35f0
```

```bash
swift stat <container>
```

```output
Container HEAD failed: https://storage.gra.cloud.ovh.net/v1/AUTH_702xxxxxxxxxxxxxxxxxxxxxxxxxxdaf/<container> 502 Bad Gateway
```

### max_meta_name_length = 128

The maximum number of bytes in utf8 encoding of the name portion of a metadata header.

```bash
swift post -m 'max_meta_name_length_oROpb2gFutM1NrZI9Q5aOuJDi0eiO0hFvJIJo9Hrd7mhPeAOoRwoCk00CJPX0yFvmbcatIuqXY8avxTLhhQBRwVhBJ0Ht2DeUKFTEZDeKfF2xBou4aC9krFMjVoF8wEsdb:value' <container>
```

```
Container POST failed: https://storage.gra.cloud.ovh.net/v1/AUTH_702xxxxxxxxxxxxxxxxxxxxxxxxxxdaf/<conteneur> 400 Bad Request  [first 60 chars of response] b'Metadata name too long: x-container-meta-Max-Meta-Name-Lengt'
Failed Transaction ID: tx6ced883b311a4c1eb5e75-00610a30eb
```

### max_meta_overall_size = 4096

The maximum number of bytes in the utf8 encoding of metadata (keys + values).

```bash
for i in $(seq 1 1 50)
do
swift post -m "max_meta_overall_size_$i:oROpb2gFutM1NrZI9Q5aOuJDi0eiO0hFvJIJo9Hrd7mhPeAOoRwoCk00CJPX0yFvmbcatIuqXY8avxTLhhQBRwVhBJ0Ht2DeUKFTEZDeKfF2xBou4aC9krFMjVoF8wEsdb" <container>
done
```

```
Container POST failed: https://storage.gra.cloud.ovh.net/v1/AUTH_702xxxxxxxxxxxxxxxxxxxxxxxxxxdaf/<container> 400 Bad Request   b'Total metadata too large; max 4096'
Failed Transaction ID: tx062504c366c3454c958c9-00610a34c0
```

### max_object_name_length = 1024

The maximum number of bytes in utf8 encoding of an object name.  
The name of an object includes its prefix.

```bash
cd /tmp/
d=$(cat /dev/urandom | tr -dc "a-zA-Z0-9" | fold -w 100 | head -n1)
mkdir -p "$d/$d/$d/$d/$d/$d/$d/$d/$d/$d/$d/" && cd $_
touch max_object_name_length.txt
file="$(pwd)/max_object_name_length.txt"
swift upload <container> $file
```

```
Object PUT failed: https://storage.gra.cloud.ovh.net/v1/AUTH_702de32b692c4842b0bb751dc5085daf/<conteneur>/tmp/dyL8Vb4KVkMnusLEWgDRsHWFIqGRJvxepapekbHHcQ08GFLPDEctdtRCpkpdZAOITkN4P0km0O717djG5qHd9EPA82zqyIrmEB4T/dyL8Vb4KVkMnusLEWgDRsHWFIqGRJvxepapekbHHcQ08GFLPDEctdtRCpkpdZAOITkN4P0km0O717djG5qHd9EPA82zqyIrmEB4T/dyL8Vb4KVkMnusLEWgDRsHWFIqGRJvxepapekbHHcQ08GFLPDEctdtRCpkpdZAOITkN4P0km0O717djG5qHd9EPA82zqyIrmEB4T/dyL8Vb4KVkMnusLEWgDRsHWFIqGRJvxepapekbHHcQ08GFLPDEctdtRCpkpdZAOITkN4P0km0O717djG5qHd9EPA82zqyIrmEB4T/dyL8Vb4KVkMnusLEWgDRsHWFIqGRJvxepapekbHHcQ08GFLPDEctdtRCpkpdZAOITkN4P0km0O717djG5qHd9EPA82zqyIrmEB4T/dyL8Vb4KVkMnusLEWgDRsHWFIqGRJvxepapekbHHcQ08GFLPDEctdtRCpkpdZAOITkN4P0km0O717djG5qHd9EPA82zqyIrmEB4T/dyL8Vb4KVkMnusLEWgDRsHWFIqGRJvxepapekbHHcQ08GFLPDEctdtRCpkpdZAOITkN4P0km0O717djG5qHd9EPA82zqyIrmEB4T/dyL8Vb4KVkMnusLEWgDRsHWFIqGRJvxepapekbHHcQ08GFLPDEctdtRCpkpdZAOITkN4P0km0O717djG5qHd9EPA82zqyIrmEB4T/dyL8Vb4KVkMnusLEWgDRsHWFIqGRJvxepapekbHHcQ08GFLPDEctdtRCpkpdZAOITkN4P0km0O717djG5qHd9EPA82zqyIrmEB4T/dyL8Vb4KVkMnusLEWgDRsHWFIqGRJvxepapekbHHcQ08GFLPDEctdtRCpkpdZAOITkN4P0km0O717djG5qHd9EPA82zqyIrmEB4T/dyL8Vb4KVkMnusLEWgDRsHWFIqGRJvxepapekbHHcQ08GFLPDEctdtRCpkpdZAOITkN4P0km0O717djG5qHd9EPA82zqyIrmEB4T/max_object_name_length.txt 400 Bad Request   b'Object name length of 1141 longer than 1024'

```

### Validity period of a token

A token is valid for 24 hours.

> [!warning]
>
> Too many token requests will return a 429 Too Many Requests error.
>

### Creating a container via Horizon

Horizon does not list storage policies. As a result, it is not possible to create a PCA container via Horizon, with PCS being the default storage policy.

### Number of containers in storage

There is no limit to the number of containers in a storage.

### Number of user accounts per project

1,000

### Creating a Public Cloud Archive container on SBG

It is no longer possible to create a PCA container on SBG. No return date has been announced for the moment.

### Keystone API version

The current version of Keystone is version 3, v2 being obsolete for several years: <https://public-cloud.status-ovhcloud.com/incidents/gwqhdkprm136>

## Go further

If you need training or technical assistance to implement our solutions, contact your sales representative or click on [this link](/links/professional-services) to get a quote and ask our Professional Services experts for assisting you on your specific use case of your project.

Join our [community of users](/links/community).
