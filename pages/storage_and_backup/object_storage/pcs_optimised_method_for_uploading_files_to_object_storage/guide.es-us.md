---
title: Object Storage Swift - Optimizar los envíos hacia el Object Storage
updated: 2021-10-27
---

## Objetivo

Para enviar archivos muy pesados al Object Storage (como vídeos o imágenes de disco, por ejemplo), es posible utilizar el cliente OpenStack Swift, que optimiza las transferencias segmentando los archivos.

Esta guía explica cómo mejorar la velocidad de los envíos hacia el Object Storage utilizando esta funcionalidad.

## Requisitos

- [Preparar el entorno para utilizar la API de OpenStack](/pages/public_cloud/compute/prepare_the_environment_for_using_the_openstack_api) con el cliente python-swiftclient
- [Cargar las variables de entorno necesarias para OpenStack](/pages/public_cloud/compute/loading_openstack_environment_variables)

## Procedimiento

OpenStack Swift permite almacenar archivos sin límite de tamaño dividiéndolos en varios segmentos.

Cuando se utiliza un cliente Swift para enviar un archivo, el proxy Swift determina el nodo de almacenamiento utilizando un hash del nombre del objeto. Por lo tanto, hay una alta probabilidad de que los segmentos sean almacenados en distintos nodos de almacenamiento, lo que permitirá escribir los datos a mayor velocidad.

De este modo, podemos enviar un archivo de 10 GB en 100 segmentos de 100 MB como se indica a continuación:

```bash
root@server:~$ swift upload --segment-size 104857600 --segment-threads 100
container_name 10Gio.dat
```

--segment-size: Tamaño de los segmentos (en bytes)
--segment-threads: Número de segmentos
Es posible medir la velocidad de envío utilizando programas como iftop.

## Más información
  
If you need training or technical assistance to implement our solutions, contact your sales representative or click on [this link](/links/professional-services) to get a quote and ask our Professional Services experts for assisting you on your specific use case of your project.

Interactúe con nuestra comunidad de usuarios en <https://community.ovh.com/en/>.
