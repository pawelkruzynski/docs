---
title: Object Storage Swift - Ottimizza il trasferimento dei tuoi file verso l’Object Storage
updated: 2021-10-27
---

## Obiettivo

Per inviare file di grandi dimensioni (ad esempio, video o immagini disco) verso l'Object Storage, è possibile utilizzare il client OpenStack Swift per segmentare questi file e ottimizzarne il trasferimento.

**Questa guida ti mostra come ottimizzare il trasferimento dei tuoi file verso l'Object Storage utilizzando questa funzionalità.**

## Prerequisiti

- [Preparare l’ambiente per utilizzare l’API OpenStack](/pages/public_cloud/compute/prepare_the_environment_for_using_the_openstack_api) con il client python-swiftclient
- [Impostare le variabili d’ambiente OpenStack](/pages/public_cloud/compute/loading_openstack_environment_variables)

## Procedura

OpenStack Swift ti permette di archiviare i tuoi file senza limiti di dimensione, dividendoli in più segmenti.

Quando utilizzi un client Swift per l'invio di file, il nodo di storage è determinato dal proxy Swift tramite un hashing del nome dell'oggetto.
Per questo motivo, è molto probabile che i segmenti vengano salvati in diversi nodi dello storage consentendo la scrittura dei tuoi dati a una velocità superiore.

Ad esempio, è possibile inviare un file da 10 GB in 100 segmenti da 100 MB:

```bash
root@server:~$ swift upload --segment-size 104857600 --segment-threads 100
container_name 10Gio.dat
```

|Argomento|Descrizione|
|---|---|
|--segment-size|Dimensione dei segmenti (byte)|
|--segment-threads|Numero di segmenti|

Per verificare la velocità di invio, utilizza programmi come iftop.

## Per saperne di più
  
Se avete bisogno di formazione o di assistenza tecnica per implementare le nostre soluzioni, contattate il vostro rappresentante o cliccate su [questo link](/links/professional-services) per ottenere un preventivo e richiedere un'analisi personalizzata del vostro progetto da parte dei nostri esperti del team Professional Services.

Contatta la nostra Community di utenti all’indirizzo <https://community.ovh.com/en/>.
