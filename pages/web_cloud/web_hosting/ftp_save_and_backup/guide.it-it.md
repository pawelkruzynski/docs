---
title: "Ripristinare i dati dello spazio di storage di un hosting Web"
excerpt: "Questa guida ti mostra come recuperare un file o l’intero contenuto dello spazio di storage di un hosting Web OVHcloud"
updated: 2023-12-04
---

## Obiettivo

Le soluzioni di hosting Web OVHcloud includono uno spazio di storage in cui è possibile ospitare i tuoi siti Internet. Per diversi motivi potrebbe essere necessario ripristinare tutti i dati in esso contenuti o un file specifico, ad esempio nel caso in cui il tuo sito risulti irraggiungibile in seguito alla rimozione o alla modifica errata di un file.

> [!primary]
> 
> I backup proposti da OVHcloud per gli hosting condivisi sono non contrattuali. In aggiunta ai tuoi servizi, ti offriamo le nostre soluzioni per aiutarti in caso di emergenze. Ti consigliamo di effettuare regolarmente i backup di sicurezza necessari per far fronte alle eventuali perdite di dati.
> 
> Quando effettui un backup di sicurezza per il tuo sito e utilizzi un database, fai anche un backup del tuo database. Consulta la guida per [recuperare il backup del database di un hosting Web](/pages/web_cloud/web_hosting/sql_database_export).
> 

**Questa guida ti mostra come ripristinare un file o l’intero contenuto dello storage del tuo hosting Web OVHcloud.**

## Prerequisiti

- Disporre di un piano di [hosting Web OVHcloud](/links/web/hosting){.external} (escluso il servizio [Cloud Web](/links/web/hosting-cloud-web-offer))
- In base al metodo utilizzato, disporre dell’accesso alla gestione della soluzione di hosting Web dallo [Spazio Cliente OVHcloud](/links/manager){.external} o della password FTP per accedere allo spazio di storage 

## Procedura

Prima di iniziare, assicurati che le date di ripristino disponibili ti consentano di recuperare i dati del tuo hosting allo stato desiderato:

- giorno corrente, alle 00:01
- giorno precedente, alle 00:01
- due giorni prima, alle 00:01
- domenica precedente, alle 01:00 del mattino
- domenica di due settimane prima, alle 01:00 del mattino

OVHcloud non sarà in grado di fornirti backup antecedenti: in caso di necessità, dovrai utilizzare un backup eseguito personalmente. 

Inoltre, dovrai indicare il metodo di ripristino che intendi adottare:

|Metodo di ripristino|Descrizione|
|---|---|
|Ripristino dallo Spazio Cliente OVHcloud|Ripristina tutti i dati dello spazio di storage. L’intero contenuto corrente sarà sostituito con quello del backup selezionato.|
|Ripristino da un software o un’interfaccia Web|Permette di accedere in sola lettura a un backup dello spazio di storage. Questo metodo, più tecnico, consente di recuperare uno o più file di una data anteriore senza sovrascrivere completamente il contenuto dello spazio di storage.|

> [!warning]
>
> Per maggiori informazioni sul metodo di **ripristino dallo Spazio Cliente OVHcloud**, verifica che almeno **la metà dello spazio di storage FTP totale** incluso con la tua offerta di hosting sia ancora disponibile.
> Ad esempio, se disponi di un'offerta di hosting **Performance**, 250 GB devono ancora essere disponibili sui 500 GB messi a disposizione.
>
> I nostri sistemi installano il backup sul tuo hosting prima di eliminare il contenuto FTP che verrà sostituito dal ripristino.
>
> Per verificare la quota utilizzata sull'hosting, accedi allo [Spazio Cliente OVHcloud](/links/manager). Accedi alla sezione `Web Cloud`{.action} e clicca su `Hosting`{.action}. Seleziona il nome dell'hosting interessato. 
>
> La quota utilizzata compare sulla pagina che appare:
>
>![ftp quota](/pages/assets/screens/control_panel/product-selection/web-cloud/web-hosting/general-information/find-disk-space.png){.thumbnail}
>
> Se lo spazio di storage FTP utilizzato è superiore alla metà dello spazio di storage FTP totale della tua offerta di hosting, recupera in locale alcuni elementi voluminosi del tuo sito Web (per farlo, puoi utilizzare [Filezilla](/pages/web_cloud/web_hosting/ftp_filezilla_user_guide)). Eliminali dallo spazio di storage FTP. Questa operazione diminuirà la dimensione dello spazio di storage FTP utilizzato e potrai avviare il ripristino dallo Spazio Cliente OVHcloud.
>

Una volta scelto il metodo di ripristino più adatto alle tue esigenze, prosegui nella lettura di questa guida nel paragrafo corrispondente:

- [Ripristina i dati dello storage dallo Spazio Cliente OVHcloud](#viacontrolpanel)
- [Ripristina un file da un software o un’interfaccia Web](#viainterface)

### Ripristina i dati dello storage dallo Spazio Cliente OVHcloud <a name="viacontrolpanel"></a>

> [!warning]
>
> Questo metodo di ripristino non è disponibile se il tuo hosting è stato impostato in modalità manutenzione dai nostri amministratori o se non dispone dei diritti di accesso FTP (diritti `chmod`) in seguito ad un'azione da parte tua.
>
> Perché questo metodo funzioni è necessario che i diritti `chmod` alla radice del tuo hosting siano obbligatoriamente nel `705`.
>

> [!primary]
> **Sito in modalità manutenzione**
> 
> Per verificare se il tuo sito è stato impostato in modalità manutenzione, consulta la nostra guida [Cosa fare in caso di pagina “403 forbidden”?](/pages/web_cloud/web_hosting/diagnostic_403_forbidden). 
> 
> In questo caso:
>
> - I nostri team inviano un'email al [contatto amministratore](/pages/account_and_service_management/account_information/managing_contacts#accedi-alla-pagina-di-gestione-dei-contatti) dell'hosting. 
> - Lo stato di "manutenzione" compare nello [Spazio Cliente OVHcloud](/links/manager){.external}. Nella sezione `Web Cloud`{.action}, clicca sul tuo servizio nella sezione `Hosting`{.action} e poi sulla scheda `Informazioni generali`{.action}.
> - Il(i) sito(i) ospita(i) mostra(no) una pagina "403 Forbidden".
>

Accedi allo [Spazio Cliente OVHcloud](/links/manager){.external}, seleziona il tuo servizio nella sezione `Hosting`{.action} e, nella scheda `FTP - SSH`{.action}, clicca sul pulsante `Ripristina un backup`{.action}.

![backupftp](/pages/assets/screens/control_panel/product-selection/web-cloud/web-hosting/ftp-ssh/restore-backup.png){.thumbnail}

Nella nuova finestra è possibile selezionare la data di ripristino dal menu a tendina:

|Data|Momento del backup|
|---|---|
|g-1|Il giorno stesso alle 00:01|
|g-2|Il giorno precedente alle 00:01|
|g-3|Due giorni prima alle 00:01|
|1 settimana|La domenica precedente alle 01:00|
|2 settimane|La domenica di due settimane prima alle 01:00|

Una volta selezionata la data, clicca su `Seguente`{.action}. 

![backupftp](/pages/assets/screens/control_panel/product-selection/web-cloud/web-hosting/ftp-ssh/restore-backup-step-1.png){.thumbnail}

Assicurati che questa azione non comporti la perdita di dati, ad esempio di un file archiviato sullo spazio di storage dopo la data di ripristino selezionata. Come già precisato, il backup sovrascriverà i dati presenti nello storage.

Clicca su `Conferma`{.action} per avviare l’operazione.

> [!primary]
>
> Il ripristino automatico può richiedere da qualche minuto a qualche ora. Se dura **più di 24 ore**, contatta [il supporto OVHcloud](/links/support).
>

### Ripristina un file da un software o un’interfaccia Web <a name="viainterface"></a>

Questa operazione prevede diversi step. Assicurati di avere a disposizione la password dell’utente FTP per poter accedere allo spazio di storage. 

> [!warning]
>
> Questa soluzione richiede conoscenze del software o dell’interfaccia utilizzati. In questa guida puoi trovare informazioni utili per effettuare l’operazione ma, in caso di necessità, ti consigliamo di rivolgerti a uno specialista del settore. 
>

#### 1. Scegliere il software o l’interfaccia Web da utilizzare

Per prima cosa, definisci quale software o interfaccia utilizzerai per accedere al backup del tuo spazio di storage. Se hai già preso la tua decisione, passa direttamente allo step 2. In caso contrario, ecco alcune soluzioni consigliate:

- **FileZilla**: il download di questo client è disponibile dal sito ufficiale. Per maggiori informazioni consulta la nostra[ guida all’utilizzo di FileZilla](/pages/web_cloud/web_hosting/ftp_filezilla_user_guide){.external}, tenendo però presente che non si sostituisce alla documentazione ufficiale del software.

- **Cyberduck**: il download di questo client è disponibile dal sito ufficiale. Per maggiori informazioni consulta la nostra [guida all’utilizzo di Cyberduck (MAC)](/pages/web_cloud/web_hosting/ftp_cyberduck_user_guide_on_mac){.external}, tenendo però presente che non si sostituisce alla documentazione ufficiale del software.

- **FTP Explorer**: questa interfaccia è disponibile nello [Spazio Cliente OVHcloud](/links/manager){.external}: seleziona il tuo servizio nella sezione `Hosting`{.action}, clicca sulla scheda `FTP - SSH`{.action} e poi sul pulsante `FTP Explorer`{.action}.

A questo punto, prosegui con lo step successivo.

![backupftp](/pages/assets/screens/control_panel/product-selection/web-cloud/web-hosting/ftp-ssh/ftp-explorer.png){.thumbnail}

#### 2. Accedere al backup

Dall’interfaccia o dal software selezionato, dovrai connetterti al tuo spazio di storage per accedere ai dati del backup da recuperare. Per effettuare questa operazione è necessario disporre di nome utente FTP, password e hostname del server FTP.

Queste informazioni sono disponibili nella scheda `FTP - SSH`{.action} del tuo hosting. Se non possiedi più la password, segui le indicazioni descritte nella guida [Modificare la password di un utente FTP](/pages/web_cloud/web_hosting/ftp_change_password){.external}.

![backupftp](/pages/assets/screens/control_panel/product-selection/web-cloud/web-hosting/ftp-ssh/login-infos.png){.thumbnail}

Una volta effettuato il login, dovrai aggiungere al tuo nome utente FTP il suffisso corrispondente al backup che utilizzerai, come indicato qui sotto:

|Data del backup|Suffisso da aggiungere|Esempio di nome utente completo|
|---|---|---|
|Il giorno stesso alle 00:01|-snap0|utenteftp**-snap0**|
|Il giorno precedente alle 00:01|-snap1|utenteftp**-snap1**|
|Due giorni prima alle 00:01|-snap2|utenteftp**-snap2**|
|La domenica precedente alle 01:00|-snap3|utenteftp**-snap3**|
|La domenica di due settimane prima alle 01:00|-snap4|utenteftp**-snap4**|

Sostituisci l’informazione generica “utenteftp” con il tuo nome utente FTP principale, conservando il suffisso che indica la data del backup che intendi ripristinare.

Il metodo di accesso allo spazio di storage differisce in base all’interfaccia o al software utilizzato. L’immagine qui sotto, ad esempio, ti mostra l’interfaccia di connessione di FTP Explorer.

![backupftp](/pages/assets/screens/other/web-tools/net2ftp/login-interface-snap0.png){.thumbnail}

#### 3. Recuperare i file

A questo punto recupera i file da ripristinare esplorando il contenuto del tuo spazio di storage. L’operazione differisce a seconda del software o dell’interfaccia utilizzati.

Prima di passare allo step successivo, assicurati di aver recuperato tutti i file necessari e poi esci dallo spazio di storage.

> [!success]
>
> Se utilizzi l'interfaccia di **FTP Explorer**, consulta la [pagina della Guida](https://net2ftp.cluster020.hosting.ovh.net/help.html){.external} per effettuare correttamente il recupero dei tuoi file. Per accedere a questa pagina, clicca sul pulsante `Help Guide`{.action} nella parte inferiore dell’interfaccia di connessione al **FTP Explorer**.
>
> Se utilizzi un altro software per accedere allo spazio di storage FTP, ti consigliamo di consultare la documentazione ufficiale del tuo client per effettuare correttamente le operazioni.
>

#### 4. Ripristinare i file

Dopo aver recuperato i file, accedi di nuovo allo storage senza aggiungere suffissi al nome utente FTP: ti connetterai al contenuto corrente del tuo storage e non a un backup precedente.

A questo punto non ti resta che ripristinare i file: recuperali esplorando il contenuto del tuo spazio di storage e scaricali sostituendoli ai file precedenti.

> [!success]
>
> Se utilizzi l’interfaccia di **FTP Explorer**, consulta la [pagina della Guida](https://net2ftp.cluster020.hosting.ovh.net/help.html){.external} per effettuare correttamente il ripristino dei tuoi file. Per accedere a questa pagina, clicca sul pulsante `Help Guide`{.action} nella parte inferiore dell’interfaccia di connessione al **FTP Explorer**.
>
> Se utilizzi un altro software per accedere allo spazio di storage FTP, ti consigliamo di consultare la documentazione ufficiale del tuo client per effettuare correttamente le operazioni.
>

## Per saperne di più

[Hosting condiviso: guida all’utilizzo di FileZilla](/pages/web_cloud/web_hosting/ftp_filezilla_user_guide){.external}

[Hosting condiviso: guida all’utilizzo di Cyberduck (MAC)](/pages/web_cloud/web_hosting/ftp_cyberduck_user_guide_on_mac){.external}

[Modificare la password di un utente FTP](/pages/web_cloud/web_hosting/ftp_change_password){.external}

[Recuperare il backup del database di un hosting Web](/pages/web_cloud/web_hosting/sql_database_export)

Per prestazioni specializzate (referenziamento, sviluppo, ecc...), contatta i [partner OVHcloud](/links/partner).

Per usufruire di un supporto per l'utilizzo e la configurazione delle soluzioni OVHcloud, è possibile consultare le nostre soluzioni [offerte di supporto](/links/support).

Contatta la nostra [Community di utenti](/links/community).