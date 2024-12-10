---
title: 'Tester la vitesse des disques'
excerpt: "Vérifiez le nombre d'opérations d'entrée-sortie par seconde (IOPS) que vos disques sont en mesure d'effectuer"
updated: 2024-11-18
---

## Objectif

Lors de vos tests, vous serez probablement amené à vérifier la vitesse de vos disques. Que ce soit pour comparer leurs performances ou, simplement, pour vérifier qu'ils répondent à vos attentes.

**Apprenez à tester le nombre d'opérations d'entrée-sortie par seconde (IOPS) que vos disques sont en mesure d'effectuer, pour vos instances ou disques supplémentaires.**

## Prérequis

- Posséder une [instance Public Cloud](https://www.ovhcloud.com/fr-ca/public-cloud/).
- Avoir un accès administratif (sudo) à votre instance via SSH (Linux) ou RDP (Windows).

## En pratique

### Installer la commande de test

La commande dont vous avez besoin pour vérifier la vitesse de votre disque s'appelle `fio`. Elle n'est pas présente par défaut sur votre serveur.

Pour installer `fio`, établissez une connexion SSH à votre instance puis exécutez la commande suivante :

```bash
apt install fio
```

### Tester la vitesse de votre disque

Pour tester la vitesse de votre disque, exécutez la commande suivante :

```bash
fio --name=rand-write --ioengine=libaio --iodepth=32 --rw=randwrite --invalidate=1 --bsrange=4k:4k,4k:4k --size=512m --runtime=120 --time_based --do_verify=1 --direct=1 --group_reporting --numjobs=1
```

> [!primary]
>
> Notez que vous devrez modifier l'argument `--numjobs` pour refléter le nombre de CPU de votre instance.
>
> Vous pouvez récupérer une liste d'arguments et leurs fonctions directement à partir du [guide](https://github.com/axboe/fio/blob/master/HOWTO.rst) de fio.
>

### Analyser les données

```console
fio-3.33
Starting 1 process
Jobs: 1 (f=1): [w(1)][100.0%][w=156MiB/s][w=40.0k IOPS][eta 00m:00s]
rand-write: (groupid=0, jobs=1): err= 0: pid=2974: Sat Nov 16 03:21:07 2024
  write: IOPS=40.0k, BW=156MiB/s (164MB/s)(18.3GiB/120001msec); 0 zone resets
    slat (usec): min=2, max=812, avg= 4.65, stdev= 1.89
    clat (usec): min=53, max=12487, avg=794.13, stdev=75.55
     lat (usec): min=58, max=12492, avg=798.78, stdev=75.53
    clat percentiles (usec):
     |  1.00th=[  742],  5.00th=[  775], 10.00th=[  783], 20.00th=[  783],
     | 30.00th=[  791], 40.00th=[  791], 50.00th=[  799], 60.00th=[  799],
     | 70.00th=[  799], 80.00th=[  807], 90.00th=[  807], 95.00th=[  816],
     | 99.00th=[  840], 99.50th=[  857], 99.90th=[ 1037], 99.95th=[ 1434],
     | 99.99th=[ 4883]
   bw (  KiB/s): min=159904, max=191976, per=100.00%, avg=160265.41, stdev=2060.10, samples=239
   iops        : min=39976, max=47994, avg=40066.36, stdev=515.02, samples=239
  lat (usec)   : 100=0.01%, 250=0.07%, 500=0.30%, 750=0.94%, 1000=98.56%
  lat (msec)   : 2=0.10%, 4=0.01%, 10=0.01%, 20=0.01%
  cpu          : usr=7.37%, sys=20.48%, ctx=4614084, majf=0, minf=10
  IO depths    : 1=0.1%, 2=0.1%, 4=0.1%, 8=0.1%, 16=0.1%, 32=100.0%, >=64=0.0%
     submit    : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, 64=0.0%, >=64=0.0%
     complete  : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.1%, 64=0.0%, >=64=0.0%
     issued rwts: total=0,4803938,0,0 short=0,0,0,0 dropped=0,0,0,0
     latency   : target=0, window=0, percentile=100.00%, depth=32

Run status group 0 (all jobs):
  WRITE: bw=156MiB/s (164MB/s), 156MiB/s-156MiB/s (164MB/s-164MB/s), io=18.3GiB (19.7GB), run=120001-120001msec

Disk stats (read/write):
  sda: ios=0/4799786, merge=0/29, ticks=0/3797382, in_queue=3797385, util=74.39% 
```

La ligne qui nous intéresse est la cinquième, qui contient le nombre d'opérations d'entrée-sortie par seconde (IOPS) :

```console
write: IOPS=40.0k, BW=156MiB/s (164MB/s)(18.3GiB/120001msec); 0 zone resets
```

Nous pouvons voir que la performance du disque principal est d'environ 40.0k IOPS.

### Disque supplémentaire

Pour tester la vitesse d'un disque supplémentaire, vous devez monter celui-ci à l'aide de la commande suivante : 

```bash
root@serveur:~$ cd /mnt/disk
```
### Analyser les données

La valeur IOPS dépend du type de disque supplémentaire utilisé. Dans l'exemple ci-dessous, nous avons effectué le test sur un volume high-speed :

```console
fio-3.33
Starting 1 process
Jobs: 1 (f=1): [w(1)][100.0%][w=11.9MiB/s][w=3054 IOPS][eta 00m:00s]
rand-write: (groupid=0, jobs=1): err= 0: pid=2946: Sat Nov 16 03:13:20 2024
  write: IOPS=3052, BW=11.9MiB/s (12.5MB/s)(1431MiB/120011msec); 0 zone resets
    slat (usec): min=2, max=8119, avg= 6.14, stdev=53.35
    clat (usec): min=114, max=20721, avg=10477.33, stdev=587.51
     lat (usec): min=117, max=20724, avg=10483.47, stdev=584.33
    clat percentiles (usec):
     |  1.00th=[ 9634],  5.00th=[10028], 10.00th=[10028], 20.00th=[10159],
     | 30.00th=[10159], 40.00th=[10290], 50.00th=[10290], 60.00th=[10421],
     | 70.00th=[10552], 80.00th=[11076], 90.00th=[11207], 95.00th=[11338],
     | 99.00th=[11469], 99.50th=[11469], 99.90th=[12780], 99.95th=[14877],
     | 99.99th=[17433]
   bw (  KiB/s): min=12160, max=14648, per=100.00%, avg=12217.46, stdev=158.45, samples=239
   iops        : min= 3040, max= 3662, avg=3054.36, stdev=39.61, samples=239
  lat (usec)   : 250=0.01%, 500=0.04%, 750=0.03%, 1000=0.01%
  lat (msec)   : 2=0.01%, 4=0.01%, 10=5.06%, 20=94.84%, 50=0.01%
  cpu          : usr=0.70%, sys=1.82%, ctx=143740, majf=0, minf=10
  IO depths    : 1=0.1%, 2=0.1%, 4=0.1%, 8=0.1%, 16=0.1%, 32=100.0%, >=64=0.0%
     submit    : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, 64=0.0%, >=64=0.0%
     complete  : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.1%, 64=0.0%, >=64=0.0%
     issued rwts: total=0,366290,0,0 short=0,0,0,0 dropped=0,0,0,0
     latency   : target=0, window=0, percentile=100.00%, depth=32

Run status group 0 (all jobs):
  WRITE: bw=11.9MiB/s (12.5MB/s), 11.9MiB/s-11.9MiB/s (12.5MB/s-12.5MB/s), io=1431MiB (1500MB), run=120011-120011msec

Disk stats (read/write):
  sdb: ios=0/365996, merge=0/23, ticks=0/3826413, in_queue=3826472, util=96.45%  
```

```console
write: IOPS=3052, BW=11.9MiB/s (12.5MB/s)(1431MiB/120011msec); 0 zone resets
```

Nous pouvons voir que la performance du disque supplémentaire est d'environ 3052 IOPS.

### Sur Windows

### Installer la commande de test

La commande dont vous avez besoin pour vérifier la vitesse de votre disque s'appelle `fio`. Elle n'est pas présente par défaut sur votre serveur.

Pour installer `fio`, connectez-vous à votre instance via RDP et téléchargez ce binaire : [Microsoft Windows binaries for fio](https://bsdio.com/fio/).

### Tester la vitesse de votre disque

Pour tester la vitesse de votre disque, exécutez la commande suivante :

```powershell
fio --name=rand-write --ioengine=windowsaio --iodepth=32 --rw=randwrite --invalidate=1 --bsrange=4k:4k,4k:4k --size=512m --runtime=120 --time_based --do_verify=1 --direct=1 --group_reporting --numjobs=1
```

> [!primary]
>
> Notez que vous devrez modifier l'argument `--numjobs` pour refléter le nombre de CPU de votre instance.
>
> Vous pouvez récupérer une liste d'arguments et leurs fonctions directement à partir du [guide de fio](https://github.com/axboe/fio/blob/master/HOWTO.rst).
>

### Analyser les données

Une fois le test terminé, vous obtenez un résultat semblable à ce qui suit :

```powershell
fio-3.38
Starting 1 thread
rand-write: Laying out IO file (1 file / 512MiB)
Jobs: 1 (f=1): [w(1)][100.0%][w=156MiB/s][w=40.0k IOPS][eta 00m:00s]
rand-write: (groupid=0, jobs=1): err= 0: pid=6880: Thu Nov 14 08:57:53 2024
write: IOPS=39.4k, BW=154MiB/s (161MB/s)(18.0GiB/120001msec); 0 zone resets
slat (usec): min=5, max=542348, avg=15.35, stdev=251.51
clat (nsec): min=900, max=184132k, avg=663865.64, stdev=581569.23
lat (usec): min=65, max=544389, avg=679.22, stdev=632.99
clat percentiles (usec):
|  1.00th=[  182],  5.00th=[  273], 10.00th=[  330], 20.00th=[  437],
| 30.00th=[  537], 40.00th=[  619], 50.00th=[  676], 60.00th=[  725],
| 70.00th=[  766], 80.00th=[  807], 90.00th=[  881], 95.00th=[  979],
| 99.00th=[ 1418], 99.50th=[ 1975], 99.90th=[ 6259], 99.95th=[ 8094],
| 99.99th=[13435]
bw (  KiB/s): min=111952, max=183453, per=100.00%, avg=157817.69, stdev=10924.21, samples=201
iops        : min=27988, max=45863, avg=39454.11, stdev=2731.09, samples=201
lat (nsec)   : 1000=0.01%
lat (usec)   : 2=0.01%, 4=0.01%, 10=0.01%, 20=0.01%, 50=0.01%
lat (usec)   : 100=0.06%, 250=3.54%, 500=22.77%, 750=40.01%, 1000=29.12%
lat (msec)   : 2=3.98%, 4=0.29%, 10=0.17%, 20=0.02%, 50=0.01%
lat (msec)   : 250=0.01%
cpu          : usr=7.50%, sys=36.67%, ctx=0, majf=0, minf=0
IO depths    : 1=0.2%, 2=0.5%, 4=1.8%, 8=9.5%, 16=71.1%, 32=17.0%, >=64=0.0%
submit    : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, 64=0.0%, >=64=0.0% complete  : 0=0.0%, 4=94.7%, 8=2.1%, 16=1.6%, 32=1.6%, 64=0.0%, >=64=0.0%
issued rwts: total=0,4726001,0,0 short=0,0,0,0 dropped=0,0,0,0
latency   : target=0, window=0, percentile=100.00%, depth=32

Run status group 0 (all jobs):
WRITE: bw=154MiB/s (161MB/s), 154MiB/s-154MiB/s (161MB/s-161MB/s), io=18.0GiB (19.4GB), run=120001-120001msec
```

La ligne qui nous intéresse est la cinquième, qui contient le nombre d'opérations d'entrée-sortie par seconde (IOPS) :

```console
write: IOPS=39.4k, BW=154MiB/s (161MB/s)(18.0GiB/120001msec); 0 zone resets
```

Nous pouvons voir que la performance du disque principal est d'environ 39.4k IOPS.

### Disque supplémentaire

Pour tester la vitesse d'un disque supplémentaire, vous devez le monter. Pour plus d'informations, consultez ce [guide](/pages/public_cloud/compute/create_and_configure_an_additional_disk_on_an_instance#sous-windows).

Accédez ensuite au disque supplémentaire via powershell et exécutez la même commande `fio` (voir ci-dessus).


## Aller plus loin

[Créer et configurer un disque supplémentaire sur une instance](/pages/public_cloud/compute/create_and_configure_an_additional_disk_on_an_instance){.external}.

Échangez avec notre [communauté d'utilisateurs](/links/community).