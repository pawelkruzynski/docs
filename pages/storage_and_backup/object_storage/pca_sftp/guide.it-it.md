---
title: Cloud Archive Swift - Gestisci i tuoi archivi con un client SFTP/SCP
excerpt: Come gestire il tuo servizio Public Cloud Archive
updated: 2022-05-13
---

## Introduzione
Public Cloud Archive (PCA) è una soluzione di archiviazione gestibile tramite l'API di OpenStack. Se non hai familiarità nell'amministrazione dello spazio di storage da riga di comando, abbiamo sviluppato un gateway che ti permette di accedere a PCA tramite un client SFTP.

### Prerequisiti
- Client SFTP: [WinSCP](https://winscp.net/eng/download.php){.external}
- Login e Password OpenStack
- TenantName del progetto

## Client SFTP
Nel nostro esempio, il client SFTP utilizzato è WinSCP. Ne esistono molti altri, con una configurazione simile a quella presentata in questa guida.

## Identificativo OpenStack
Per generare il tuo login e password OpenStack, consulta questa [guida](/pages/public_cloud/compute/create_and_delete_a_user).

## TenantName
Il TenantName corrisponde al nome del tuo progetto su Horizon. Per recuperarlo, accedi all’interfaccia Web OpenStack utilizzando le credenziali generate precedentemente: [https://horizon.cloud.ovh.net/](https://horizon.cloud.ovh.net/){.external}. Una volta effettuato il login, il TenantName è visibile in alto nella pagina.

![horizon](images/image1.png){.thumbnail}

## Connessione
- Host name: gateways.storage.<region>.cloud.ovh.net
- User name: pca
- Password: <TenantName>.<Username_Openstack>.<Password_Openstack>

![connexion](images/image2.png){.thumbnail}

## Esempio
Hai creato un container PCA nel datacenter SBG:

- Host name: gateways.storage.sbg.cloud.ovh.net
- User name: pca
- Password: 971891XXXX1214.f6nBXXXXXAmcv.SfPeASYfuWeqBZgXXXXX2XhF3DY12RkD

![connexion](images/image3.png){.thumbnail}

## Impostazioni WinSCP
In questa sezione disattiveremo due opzioni di WinSCP:

**Transfer Resume/Transfer to Temporary Filename:** questa opzione deve essere disattivata perché con PCA non è possibile ripristinare i dati e WinSCP può quindi restituire un errore.

- Nella sezione "Endurance", seleziona "Disable".

![connexion](images/conf1.png){.thumbnail}

**Preserve Timestamp:** il TimeStamp corrisponde alla data di modifica del file. Questa opzione deve essere disattivata perché su PCA questa informazione viene sostituita con la data di caricamento del file.

- Nella categoria "Transfer", clicca su "Edit...".

![connexion](images/conf2.png){.thumbnail}

- Deseleziona "Preserve timestamp".

![connexion](images/conf3.png){.thumbnail}

## Recupero dei dati
Per recuperare i dati, per prima cosa è necessario sbloccare l’oggetto effettuando una richiesta di tipo GET. Se questo comando non viene eseguito, il client SFTP restituisce un messaggio di errore durante il tentativo di download del file. Per maggiori informazioni sulla procedura da seguire per sbloccare il tuo oggetto, consulta questa [guida](/pages/storage_and_backup/object_storage/pca_unlock).

## Per saperne di più

Se avete bisogno di formazione o di assistenza tecnica per implementare le nostre soluzioni, contattate il vostro rappresentante o cliccate su [questo link](/links/professional-services) per ottenere un preventivo e richiedere un'analisi personalizzata del vostro progetto da parte dei nostri esperti del team Professional Services.

Contatta la nostra Community di utenti all’indirizzo <https://community.ovh.com/en/>.