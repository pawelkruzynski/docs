---
title: "Object Storage Swift - Utilizzare l'Object Storage con Rclone"
updated: 2021-10-27
---

## Obiettivo

L’Object Storage OVH può essere sincronizzato tramite Rclone.

**Questa guida ti mostra la procedura da eseguire per configurare il tool dallo Spazio Cliente OVH.**

Rclone è un software di sincronizzazione esterno: per maggiori dettagli sul suo utilizzo, consulta la [documentazione ufficiale](https://Rclone.org/){.external}.

## Prerequisiti

- Aver creato un container *Object Storage* (dallo Spazio Cliente OVH o dall’interfaccia [Horizon](/pages/storage_and_backup/object_storage/pcs_create_container){.external})
- Aver creato un [utente OpenStack](/pages/public_cloud/compute/create_and_delete_a_user){.external}

## Procedura

​Una volta creato il container e l'utente OpenStack, restano due cose da fare:

- recuperare il file di configurazione per Rclone

Dopo aver creato il tuo utente OpenStack, è possibile recuperare nello Spazio Cliente OVH il file di configurazione necessario per Rclone: seleziona il tuo progetto nel menu a sinistra e accedi alla pagina degli utenti OpenStack. Clicca sull’icona con i tre puntini in corrispondenza del nome dell’utente e poi su `Scarica un file di configurazione rClone`{.external}.

![Scarica un file di configurazione rClone](images/download_file.png){.thumbnail}

- configurare Rclone

Una volta scaricato il file, esegui questo comando per aggiungere il nuovo spazio di storage:

```sh
Rclone config
```

Ti verrà chiesto di inserire i dati di configurazione presenti nel tuo file.

> [!primary]
>
> Puoi anche copiare e incollare il contenuto del tuo file nella cartella dedicata alle configurazioni di Rclone (*.config/Rclone/Rclone.conf*).
>

Una volta completata l’operazione, è possibile verificarne la correttezza, ad esempio, eseguendo il comando che restituisce la lista dei tuoi container:

```sh
Rclone lsd BackupStorage
```

*BackupStorage* corrisponde al nome assegnato al tuo spazio di storage.

Per sincronizzare il tuo Object Storage con Rclone, consulta la documentazione dettagliata disponibile sul [sito ufficiale](https://Rclone.org/swift/){.external}.

## Per saperne di più

Se avete bisogno di formazione o di assistenza tecnica per implementare le nostre soluzioni, contattate il vostro rappresentante o cliccate su [questo link](/links/professional-services) per ottenere un preventivo e richiedere un'analisi personalizzata del vostro progetto da parte dei nostri esperti del team Professional Services.

Contatta la nostra Community di utenti all’indirizzo <https://community.ovh.com/en/>.
