---
title: Backing up and restoring your Persistent Volume with Volume Snapshots on OVHcloud Managed Kubernetes
excerpt: Find out how to back up and restore your Persistent Volume with Volume Snapshots on OVHcloud Managed Kubernetes
updated: 2023-01-11
---

In this tutorial, we are using [Kubernetes Volume Snapshots](https://kubernetes.io/docs/concepts/storage/volume-snapshots/) to back up and restore persistent volumes on an OVHcloud Managed Kubernetes cluster.

Volume Snapshots are a Kubernetes feature released in General Availability (GA) on **Kubernetes 1.20**.

They provide the ability to create a “snapshot” of a persistent volume. A snapshot represents a point-in-time copy of a volume. A snapshot can be used either to rehydrate a new volume (pre-populated with the snapshot data) or to restore an existing volume to a previous state (represented by the snapshot).

## Before you begin

This tutorial presupposes that you already have a working OVHcloud Managed Kubernetes cluster, and some basic knowledge of how to operate it. If you want to know more on those topics, please look at the [OVHcloud Managed Kubernetes Service Quickstart](/pages/public_cloud/containers_orchestration/managed_kubernetes/deploying-hello-world).

The tutorial also supposes that you're familiar with [Kubernetes Persistent Volumes](https://kubernetes.io/docs/concepts/storage/persistent-volumes/). You also need to know how PVs are handled on the OVHcloud Managed Kubernetes service. Please refer to the [Persistent Volumes on OVHcloud Managed Kubernetes](/pages/public_cloud/containers_orchestration/managed_kubernetes/persistent-volumes-on-ovh-managed-kubernetes) guide.

## Instructions

### Setup

In this guide we are going to use a simple example: a small Nginx web server with a `PersistentVolume`.

Create a file named `nginx-example-with-pv.yml` with the following content:

```yaml
---
apiVersion: v1
kind: Namespace
metadata:
  name: nginx-example
  labels:
    app: nginx
---
kind: PersistentVolumeClaim
apiVersion: v1
metadata:
  name: nginx-logs
  namespace: nginx-example
  labels:
    app: nginx
spec:
  storageClassName: csi-cinder-high-speed
  accessModes:
    - ReadWriteOnce
  resources:
    requests:
      storage: 1Gi
---
apiVersion: apps/v1
kind: Deployment
metadata:
  name: nginx-deployment
  namespace: nginx-example
spec:
  strategy:
    type: Recreate
  replicas: 1
  selector:
    matchLabels:
      app: nginx
  template:
    metadata:
      labels:
        app: nginx
    spec:
      volumes:
        - name: nginx-logs
          persistentVolumeClaim:
            claimName: nginx-logs
      containers:
        - image: nginx:1.7.9
          name: nginx
          ports:
            - containerPort: 80
          volumeMounts:
            - mountPath: "/var/log/nginx"
              name: nginx-logs
              readOnly: false
---
apiVersion: v1
kind: Service
metadata:
  labels:
    app: nginx
  name: nginx-service
  namespace: nginx-example
spec:
  ports:
    - port: 80
      targetPort: 80
  selector:
    app: nginx
  type: LoadBalancer
```

And apply it to the cluster:

```bash
kubectl apply -f nginx-example-with-pv.yml
```

> [!primary]
>
> If you look attentively to the `deployment` part of this manifest, you will see that we have defined a `.spec.strategy.type`. It specifies the strategy used to replace old pods by new ones, and we have set it to `Recreate`, so all existing pods are killed before new ones are created.
>
> We do so as the Storage Class we are using, `csi-cinder-high-speed`, only supports a `ReadWriteOnce`, so we can only have one pod writing on the Persistent Volume at any given time.

Wait until you get an external IP:

```bash
kubectl -n nginx-example get svc nginx-service -w
```

When you have a Load Balancer external IP, save it:

```bash
export LB_IP=$(kubectl -n nginx-example get svc nginx-service -o jsonpath='{.status.loadBalancer.ingress[0].ip}')
```

And do some calls to the URL to generate some access logs:

```bash
curl -I $LB_IP
```

Now we need to connect to the pod to read the log file and verify that our logs are written.

First, get the name of the Nginx running pod:

```bash
export POD_NAME=$(kubectl get po -n nginx-example -o name)
```

And then connect to it and view your access logs:

```bash
kubectl -n nginx-example exec $POD_NAME -c nginx -- cat /var/log/nginx/access.log
```

You should have a result like this:

```console
$ kubectl apply -f nginx-example-with-pv.yml
namespace/nginx-example created
persistentvolumeclaim/nginx-logs created
deployment.apps/nginx-deployment created
service/nginx-service created

$ kubectl -n nginx-example get svc nginx-service -w

NAME            TYPE           CLUSTER-IP   EXTERNAL-IP   PORT(S)        AGE
nginx-service   LoadBalancer   10.3.28.41   <pending>     80:32675/TCP   4s
nginx-service   LoadBalancer   10.3.28.41   <pending>     80:32675/TCP   91s
nginx-service   LoadBalancer   10.3.28.41   135.125.XX.XXX   80:32675/TCP   91s
nginx-service   LoadBalancer   10.3.28.41   135.125.XX.XXX   80:32675/TCP   95s

$ export LB_IP=$(kubectl -n nginx-example get svc nginx-service -o jsonpath='{.status.loadBalancer.ingress[0].ip}')

$ echo $LB_IP
135.125.XX.XXX

$ curl -I $LB_IP
HTTP/1.1 200 OK
Server: nginx/1.7.9
Date: Mon, 26 Sep 2022 06:56:32 GMT
Content-Type: text/html
Content-Length: 612
Last-Modified: Tue, 23 Dec 2014 16:25:09 GMT
Connection: keep-alive
ETag: "54999765-264"
Accept-Ranges: bytes

$ curl -I $LB_IP
HTTP/1.1 200 OK
Server: nginx/1.7.9
Date: Mon, 26 Sep 2022 06:56:33 GMT
Content-Type: text/html
Content-Length: 612
Last-Modified: Tue, 23 Dec 2014 16:25:09 GMT
Connection: keep-alive
ETag: "54999765-264"
Accept-Ranges: bytes

$ export POD_NAME=$(kubectl get po -n nginx-example -o name)

$ echo $POD_NAME
pod/nginx-deployment-5bfc8c9f6f-zplsl

$ kubectl -n nginx-example exec $POD_NAME -c nginx -- cat /var/log/nginx/access.log

10.2.0.0 - - [26/Sep/2022:06:56:32 +0000] "HEAD / HTTP/1.1" 200 0 "-" "curl/7.64.1" "-"
141.94.164.46 - - [26/Sep/2022:06:56:33 +0000] "HEAD / HTTP/1.1" 200 0 "-" "curl/7.64.1" "-"
```

### Creating a Snapshot

Create a `VolumeSnapshot` in a `nginx-example-snapshot.yml` file with the following content:

```yaml
apiVersion: snapshot.storage.k8s.io/v1
kind: VolumeSnapshot
metadata:
  name: nginx-snapshot
  namespace: nginx-example
spec:
  volumeSnapshotClassName: csi-cinder-snapclass-in-use-v1
  source:
    persistentVolumeClaimName: nginx-logs 
```

And apply it:

```bash
kubectl apply -f nginx-example-snapshot.yml
```

You should have a result like this:

```console
$ kubectl apply -f nginx-example-snapshot.yml

volumesnapshot.snapshot.storage.k8s.io/nginx-snapshot created

$ kubectl -n nginx-example get VolumeSnapshot
NAME             READYTOUSE   SOURCEPVC    SOURCESNAPSHOTCONTENT   RESTORESIZE   SNAPSHOTCLASS                    SNAPSHOTCONTENT                                    CREATIONTIME   AGE
nginx-snapshot   true         nginx-logs                           1Gi           csi-cinder-snapclass-in-use-v1   snapcontent-131c751e-5cdb-4575-b0c0-538273c67d36   5m20s          5m20s
```

### Simulate a disaster

Let’s simulate a disaster scenario, deleting the log files from the `PVC`:

```bash
kubectl -n nginx-example exec $POD_NAME -c nginx -- rm /var/log/nginx/access.log
kubectl -n nginx-example exec $POD_NAME -c nginx -- ls -al /var/log/nginx/
```

You shoud have a result like this:

```console
$ kubectl -n nginx-example exec $POD_NAME -c nginx -- rm /var/log/nginx/access.log
kubectl -n nginx-example exec $POD_NAME -c nginx -- ls -al /var/log/nginx/

total 24
drwxr-xr-x 3 root root  4096 Sep 26 07:10 .
drwxr-xr-x 1 root root  4096 Jan 27  2015 ..
-rw-r--r-- 1 root root     0 Sep 26 06:54 error.log
drwx------ 2 root root 16384 Sep 26 06:54 lost+found
```

### Restoring the Volume

To restore from a given snapshot, you need to delete the original `PVC` and then recreate it from the snapshot.

Downscale the deployment to 0 replicas and delete the original `PVC`:

```bash
kubectl -n nginx-example scale deployment/nginx-deployment --replicas=0 
kubectl -n nginx-example delete pvc nginx-logs
```

Then create a `nginx-example-restore.yml` file with the following content:

```yaml
apiVersion: v1
kind: PersistentVolumeClaim
metadata:
  name: nginx-logs
  namespace: nginx-example
  labels:
    app: nginx
spec:
  dataSource:
    name: nginx-snapshot
    kind: VolumeSnapshot
    apiGroup: snapshot.storage.k8s.io
  accessModes:
    - ReadWriteOnce
  resources:
    requests:
      storage: 1Gi
```

And apply it:

```bash
kubectl apply -f nginx-example-restore.yml
```

Verify that the PVC is restored:

```bash
kubectl -n nginx-example get pvc
```

The volume should have a status equal to `Bound`. Now you can restore the deployment to its replica value of 1, and wait until the pod is again `Running`:

```bash
kubectl -n nginx-example scale deployment/nginx-deployment --replicas=1 
kubectl -n nginx-example get pods -w
```

Now you can verify that the `access.log` file is back and its content is still there:

```bash
export POD_NAME=$(kubectl get po -n nginx-example -o name)
echo $POD_NAME

kubectl -n nginx-example exec $POD_NAME -c nginx -- ls -al /var/log/nginx/
kubectl -n nginx-example exec $POD_NAME -c nginx -- cat /var/log/nginx/access.log
```

You should have a result like this:

```console
$ kubectl -n nginx-example scale deployment/nginx-deployment --replicas=0
kubectl -n nginx-example delete pvc nginx-logs
deployment.apps/nginx-deployment scaled
persistentvolumeclaim "nginx-logs" deleted

$ vi nginx-example-restore.yml

$ kubectl apply -f nginx-example-restore.yml

persistentvolumeclaim/nginx-logs created

$ kubectl -n nginx-example get pvc

NAME         STATUS   VOLUME                                                                   CAPACITY   ACCESS MODES   STORAGECLASS            AGE
nginx-logs   Bound    ovh-managed-kubernetes-dmhe43-pvc-d5c65ae2-e9fd-48a9-8c29-d69cdd464f59   1Gi        RWO            csi-cinder-high-speed   7s

$ kubectl -n nginx-example scale deployment/nginx-deployment --replicas=1
kubectl -n nginx-example get pods -w
deployment.apps/nginx-deployment scaled
NAME                                READY   STATUS              RESTARTS   AGE
nginx-deployment-5bfc8c9f6f-m627t   0/1     ContainerCreating   0          0s
nginx-deployment-5bfc8c9f6f-m627t   0/1     ContainerCreating   0          7s
nginx-deployment-5bfc8c9f6f-m627t   1/1     Running             0          10s

$ export POD_NAME=$(kubectl get po -n nginx-example -o name)
$ echo $POD_NAME
pod/nginx-deployment-5bfc8c9f6f-m627t

$ kubectl -n nginx-example exec $POD_NAME -c nginx -- ls -al /var/log/nginx/

total 28
drwxr-xr-x 3 root root  4096 Sep 26 06:54 .
drwxr-xr-x 1 root root  4096 Jan 27  2015 ..
-rw-r--r-- 1 root root   181 Sep 26 06:56 access.log
-rw-r--r-- 1 root root     0 Sep 26 06:54 error.log
drwx------ 2 root root 16384 Sep 26 06:54 lost+found

$ kubectl -n nginx-example exec $POD_NAME -c nginx -- cat /var/log/nginx/access.log

10.2.0.0 - - [26/Sep/2022:06:56:32 +0000] "HEAD / HTTP/1.1" 200 0 "-" "curl/7.64.1" "-"
141.94.164.46 - - [26/Sep/2022:06:56:33 +0000] "HEAD / HTTP/1.1" 200 0 "-" "curl/7.64.1" "-"
```

## Clean-up

At the end you can proceed to clean up by deleting everything. Delete the `nginx-example` namespace:

```bash
kubectl delete namespace nginx-example
```

## Go further

- If you need training or technical assistance to implement our solutions, contact your sales representative or click on [this link](https://www.ovhcloud.com/fr-ca/professional-services/) to get a quote and ask our Professional Services experts for assisting you on your specific use case of your project.

- Join our [community of users](/links/community).
