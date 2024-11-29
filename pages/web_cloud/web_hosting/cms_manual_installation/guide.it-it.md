---
title: "Tutorial - Installare manualmente un CMS sul tuo hosting"
excerpt: "Questa guida ti mostra come installare manualmente un CMS sul tuo hosting"
updated: 2024-03-28
---

## Obiettivo

Questa guida ti mostra come installare manualmente un CMS (Content Management System) come WordPress, Joomla!, Drupal, PrestaShop, Pico, Grav, Typo3 o SPIP.

> [!warning]
>
> OVHcloud mette a tua disposizione servizi di cui tu sei responsabile per la configurazione e la gestione. Assicurarne il corretto funzionamento è quindi responsabilità dell'utente.
> 
> Mettiamo a tua disposizione questo tutorial per supportarti nelle operazioni più frequenti. Tuttavia, in caso di difficoltà o dubbi, ti consigliamo di rivolgerti a uno [specialista del settore](/links/partner) o all'amministratore del CMS che hai scelto di installare. OVHcloud non potrà fornirti alcuna assistenza. Per maggiori informazioni consulta la sezione ["Per saperne di più"](#go-further) di questo tutorial.
>
> Per contattare gli editori dei CMS di cui sopra, clicca qui di seguito sui link alle rispettive pagine ufficiali:
>
> - [WordPress](https://wordpress.com/support/){.external}
> - [Joomla!](https://www.joomla.org/){.external}
> - [Drupal](https://www.drupal.org/){.external}
> - [PrestaShop](https://www.prestashop.com/en/support){.external}
> - [Pico](https://picocms.org/){.external}
> - [Grav](https://getgrav.org/){.external}
> - [Typo3](https://typo3.com/){.external}
> - [SPIP](https://www.spip.net/en_rubrique25.html){.external}
>

> [!success]
>
> Per installare il tuo CMS **automaticamente** dal tuo [Spazio Cliente OVHcloud](/links/manager), consulta la nostra guida sull'[installazione di un modulo "in un click"](/pages/web_cloud/web_hosting/cms_install_1_click_modules).
>

**Questa guida ti mostra come configurare un sito Web installando manualmente un CMS.**

## Prerequisiti

- Disporre di un'offerta di [hosting web](/links/web/hosting) che contiene almeno un database.
- Disporre di un [dominio](/links/web/domains)
- Avere accesso allo [Spazio Cliente OVHcloud](/links/manager){.external}

## Procedura

### Presentazione CMS

Per aiutarti a scegliere il tuo CMS, scopri di seguito una breve descrizione per ciascuno dei CMS citati precedentemente.

##### WordPress

**WordPress** è generalmente utilizzato per creare un sito Web o un blog. È basato sulla tecnologia PHP e comporta una gamma di strumenti come un correttore ortografico e plugin per l'e-commerce, la SEO e la sicurezza del tuo sito Web.

Per maggiori informazioni, consulta la nostra pagina relativa al [modulo WordPress](/links/web/hosting-wordpress)

- Sito ufficiale di [WordPress](https://wordpress.com/){.external}

#### Joomla!

**Joomla!** è un CMS che permette di creare siti e applicazioni Web performanti.

La Community **Joomla!** è molto grande e può fornire assistenza e servizi in tutti i settori del CMS (assistenza, documentazione, assistenza tecnica, temi, ecc...)

Per maggiori informazioni, consulta la nostra pagina relativa a [modulo Joomla!](/links/web/hosting-joomla)

- Sito ufficiale di [Joomla!](https://www.joomla.org/){.external}

#### Drupal

**Drupal** è una piattaforma open source gratuita con PHP creata nel 2000. **Drupal** permette di creare rapidamente siti Web dinamici.

Per maggiori informazioni, consulta la pagina relativa al [modulo Drupal](/links/web/hosting-drupal)

- Sito ufficiale di [Drupal](https://www.drupal.org/){.external}

#### PrestaShop

CMS creato nel 2005 e dedicato alla realizzazione di siti web e-commerce. Oltre alle funzionalità comuni degli e-commerce, questo software può anche essere personalizzato con moduli, temi e modelli. 

Per maggiori informazioni, consulta la nostra pagina relativa al [modulo PrestaShop](/links/web/hosting-prestashop)

- Sito ufficiale di [PrestaShop](https://www.prestashop.com/){.external}

#### Pico

**Pico** è un CMS leggero basato su PHP, ideale per creare siti Web o blog. Privo di database, utilizza file Markdown per gestire il contenuto. che supporta estensioni per personalizzare il sito Web.

- Sito ufficiale di [Pico](https://picocms.org/){.external}

#### Grav

**Grav** è un CMS moderno e flessibile basato su PHP. È progettato senza database e utilizza file Markdown per lo storage e la gestione dei contenuti. Grav si distingue per il suo sistema di gestione dei pacchetti che facilita l'installazione e l'aggiornamento dei plugin e dei temi per il vostro sito web.

- Sito ufficiale di [Grav](https://getgrav.org/){.external}

#### Typo3

**Typo3** è un CMS basato su PHP, progettato per lo sviluppo di siti Web di tutte le dimensioni, dalle piccole alle grandi imprese. Utilizza un database per salvare il contenuto. Offre una vasta gamma di estensioni per estendere le sue funzionalità e personalizzare il tuo sito Web.

- Sito ufficiale di [Typo3](https://typo3.com/){.external}

#### SPIP

**SPIP** è un CMS concepito principalmente per la pubblicazione e la gestione di siti Web editoriali come giornali o riviste online. Basato su PHP e basato su un database SQL, facilita la creazione di siti Web arricchiti di contenuti testuali, grafici e/o multimediali.

- Sito ufficiale di [SPIP](https://www.spip.net/en_rubrique25.html){.external}

> [!warning]
>
> Indipendentemente dal CMS scelto, ti ricordiamo che OVHcloud non fornisce alcuna assistenza sull'utilizzo di questi CMS. In caso di difficoltà o dubbi, contatta direttamente il produttore del CMS scelto utilizzando i link indicati in questa guida.
>

### Step 1 - preparare l'installazione <a name="step1"></a>

Per installare un CMS sulla tua offerta di [hosting Web](/links/web/hosting), sono necessari alcuni preparativi.

#### 1.1 - Verifica la dichiarazione della "cartella di root"

La "cartella di root" corrisponde alla directory in cui verrà installato il tuo futuro CMS sul tuo hosting. Ti consigliamo di scegliere una directory vuota per evitare conflitti con altri potenziali multisiti.

Consulta la nostra documentazione che descrive [come aggiungere un multisito su un hosting Web](/pages/web_cloud/web_hosting/multisites_configure_multisite) per definire la cartella di root da utilizzare con il tuo CMS.

> [!primary]
>
> Se definisci un nome di "cartella di root" che non esiste sul tuo hosting Web, verrà creato automaticamente nello spazio di storage FTP del tuo hosting Web.
>

#### 1.2 - Verifica il "puntamento" del dominio

- Assicurati che il dominio che utilizzerai per accedere al tuo CMS e il sottodominio in "www" puntino verso l'indirizzo IP della tua offerta di [hosting web](/links/web/hosting).

Accedi allo [Spazio Cliente OVHcloud](/links/manager) nella sezione `Web Cloud`{.action} e seleziona la tua soluzione di hosting Web nella sezione `Hosting`{.action}.<br>
Nel riquadro `Informazioni generali`{.action} sulla tua destra, clicca su `IPv4`{.action} e seleziona l'indirizzo IP del tuo hosting Web.

Se la zona DNS attiva del tuo dominio è gestita dallo [Spazio Cliente OVHcloud](/links/manager), compara l'indirizzo IP del tuo hosting con quello presente nella zona DNS del tuo dominio, consultando la nostra documentazione sulle [zone DNS OVHcloud](/pages/web_cloud/domains/dns_zone_edit).

> [!warning]
>
> Se hai attivato le opzioni `CDN`{.action} o `IP del paese`{.action} con il tuo dominio, utilizza l'indirizzo IP adattato seguendo la procedura descritta nella guida che contiene [tutti gli indirizzi IP dei nostri hosting condivisi](/pages/web_cloud/web_hosting/clusters_and_shared_hosting_IP).
>

Se non riesci a effettuare queste verifiche, contatta il provider della tua zona DNS attiva per aggiornare il puntamento del tuo dominio.

> [!warning]
>
> Le modifiche effettuate nella tua zona DNS comportano un tempo di propagazione da 4 a 24 ore.
>

- Recupera [le informazioni necessarie per accedere allo spazio FTP del tuo hosting web](/pages/web_cloud/web_hosting/ftp_connection#step-1-recupera-i-dati-necessari-a-effettuare-laccesso).
- Recupera gli accessi al database della tua offerta di hosting Web se esiste già, o creane una utilizzando la nostra [guida](/pages/web_cloud/web_hosting/sql_create_database).

#### 1.3 - Installare il client FTP gratuito "FileZilla"

Se non utilizzi già un client FTP, puoi utilizzare Filezilla. Per maggiori informazioni, consulta la guida scaricare gratuitamente il link di download e una guida all'utilizzo nella nostra guida su [utilizzare FileZilla con la tua soluzione di hosting OVHcloud](/pages/web_cloud/web_hosting/ftp_filezilla_user_guide).

> [!primary]
>
> Ci sono altri client FTP che puoi utilizzare come, ad esempio, Cyberduck. Per maggiori informazioni, consulta la nostra documentazione relativa all'[utilizzo di Cyberduck con la tua soluzione di hosting OVHcloud](/pages/web_cloud/web_hosting/ftp_cyberduck_user_guide_on_mac).
>

#### 1.4 - Preparare un database <a name="step1-4"></a>

> [!warning]
>
> Alcuni CMS funzionano senza database. Se questo è il caso del CMS che vuoi installare, salta questo step.
>

Per funzionare correttamente, la maggior parte dei CMS ha bisogno di un database. Le nostre offerte di [hosting web](/links/web/hosting) ne contengono, ad eccezione di [Hosting gratuito 100M](/links/web/domains-free-hosting).

Utilizza la nostra documentazione per [creare un database dalla tua offerta di hosting web](/pages/web_cloud/web_hosting/sql_create_database).

Se disponi di un'offerta Web Cloud Databases in MySQL o MariaDB e desideri utilizzarla per installare manualmente il tuo CMS, consulta la nostra guida sulla [creazione di un database su un servizio Web Cloud Databases](/pages/web_cloud/web_cloud_databases/create-db-and-user-on-db-server#crea-un-database).

Una volta creato il database, recupera i parametri di connessione (server, nome del database, nome utente e password) e conservali per [step 3](#step3) di questa guida.

> [!primary]
>
> Per installare il tuo CMS con un database già esistente, recupera le impostazioni di connessione al tuo database direttamente nei file del sito ad esso associati.
>
> Se il CMS è identico a quello da installare, puoi utilizzare [questa guida](/pages/web_cloud/web_hosting/sql_change_password#step-3-modifica-la-password-del-database-del-tuo-sito-nel-file-di-configurazione) per identificare i file di configurazione nel tuo [spazio di storage FTP](/pages/web_cloud/web_hosting/ftp_connection).
>
> Accedi al tuo database per censire i "prefissi" delle tabelle già presenti all'interno. per non scegliere un "prefisso" da tavolo già utilizzato da un altro sito.
>
> - Per connetterti al tuo database associato alla tua offerta di hosting Web, consulta [questa guida](/pages/web_cloud/web_hosting/sql_create_database#accedi-allinterfaccia-phpmyadmin).
> - Per connetterti a un database presente su un Web Cloud Databases, consulta [questa guida](https://help.ovhcloud.com/csm/it-web-cloud-db-connecting-database-server?id=kb_article_view&sysparm_article=KB0051461).
>

### Step 2 - Avvia l'installazione manuale

#### 2.1 - Recuperare i file sorgente del tuo CMS

Accedi al sito ufficiale del CMS che hai scelto per scaricare i file sorgente.

Di seguito trovi i link alle pagine di download dei CMS citati in questo tutorial:

- [WordPress](https://wordpress.org/download/#download-install){.external}
- [Joomla!](https://downloads.joomla.org/){.external}
- [Drupal](https://www.drupal.org/download){.external}
- [Prestashop](https://www.prestashop.com/en/download){.external}
- [Pico](https://picocms.org/download/){.external}
- [Grav](https://getgrav.org/downloads){.external}
- [Typo3](https://get.typo3.org/#download){.external}
- [SPIP](https://www.spip.net/en_download){.external}

> [!primary]
>
> Recupera la versione PHP e, se il tuo CMS utilizza un database, identifica la versione MySQL o MariaDB necessaria per far funzionare il tuo CMS.
>
> Per farlo, consulta il link alla pagina ufficiale del CMS che vuoi installare:
>
> - [WordPress](https://wordpress.org/about/requirements/){.external}
> - [Joomla!](https://downloads.joomla.org/technical-requirements){.external}
> - [Drupal](https://www.drupal.org/docs/getting-started/system-requirements/php-requirements){.external}
> - [Prestashop](https://www.prestashop.com/en/system-requirements){.external}
> - [Pico](https://picocms.org/download/){.external}
> - [Grav](https://learn.getgrav.org/17/basics/requirements){.external}
> - [Typo3](https://docs.typo3.org/m/typo3/tutorial-getting-started/main/en-us/SystemRequirements/Index.html){.external}
> - [SPIP](https://www.spip.net/en_article6659.html){.external}
>
> Configura la versione di PHP sul tuo hosting Web consultando la nostra guida su [modifica della versione PHP di un hosting Web](/pages/web_cloud/web_hosting/configure_your_web_hosting).
>
> Se utilizzi già una versione di PHP superiore o uguale a quella richiesta, non è necessario apportare modifiche.
>

Segui le istruzioni fornite dal tuo CMS fino a che i file sorgente non saranno caricati sul tuo computer e prosegui nella lettura di questo tutorial.

> [!warning]
>
> Se hai altri siti ospitati sulla tua offerta di hosting Web, verifica che siano compatibili con la versione di PHP scelta per il tuo nuovo CMS.
>

#### 2.2 - Decomprimere i file sorgente scaricati in una nuova cartella

>[!primary]
>
> Per maggiore semplicità, sostituisci in questo step il nome della cartella "**CMS**" con il nome del CMS che hai scelto. (**WordPress**, **Joomla!**, **Drupal**, **PrestaShop**, ecc...)
>

Il file caricato è in formato **compresso** (zippato). Crea una cartella intitolata "**CMS**" sul tuo computer e **decomprimine** il contenuto del file scaricato all'interno della cartella "**CMS**".

Per farlo, apri la cartella in cui hai scaricato il file compresso, clicca con il tasto destro sul file in questione e seleziona "Estrarre tutto... ".

Indica la cartella "**CMS**" per estrarre i tuoi file da questa cartella.

### 2.3 - Sposta i file sorgente della cartella "CMS" sulla cartella root del tuo hosting Web

Una volta che i file decomprimono la cartella "**CMS**", [collegati in FTP al tuo spazio di archiviazione](/pages/web_cloud/web_hosting/ftp_connection) con l'aiuto del [client FTP FileZilla](/pages/web_cloud/web_hosting/ftp_filezilla_user_guide) e copia i file contenuti nella cartella "**CMS**" nella "cartella root" definita sul tuo hosting durante lo [step 1](#step1) di questa guida.

Di seguito, un esempio con il CMS *WordPress*:

![hosting](/pages/assets/screens/other/web-tools/filezilla/ftp-upload-wordpress.png){.thumbnail}

> [!warning]
>
> Ti consigliamo vivamente di utilizzare una "cartella radice" vuota per evitare qualsiasi conflitto con un altro dei tuoi siti Web. Verifica che la cartella di destinazione non contenga elementi prima di spostare i file.
>

> [!primary]
>
> Se la cartella root definita non è stata creata automaticamente durante le azioni descritte nello [step 1](#step1), puoi crearla via FileZilla.
>
> Il deposito dei file sul tuo hosting può richiedere qualche minuto.
>
> Una volta completata l'operazione, verifica che tutti gli elementi presenti nella cartella locale "**CMS**" siano stati correttamente trasferiti nella "cartella di root" presente sul tuo hosting Web.
>

**Caso Particolare**: Se disponi di una connessione Internet limitata e/o di un'offerta di hosting **Pro** o superiore, puoi utilizzare la connessione in **SSH** per inserire i file sorgente del tuo CMS nello spazio di archiviazione del tuo hosting Web. 

Per connetterti in SSH al tuo hosting, consulta la nostra guida sulla [connessione in SSH da un hosting condiviso OVHcloud](/pages/web_cloud/web_hosting/ssh_on_webhosting).

Una volta connesso in **SSH**, esegui questi comandi:

- Accedi alla "cartella di root", nella quale vuoi installare il tuo CMS sul tuo hosting Web:

```bash
cd NameOfYourTargetFolder
```

- Recupera i file sorgente del tuo CMS direttamente dalla tua "cartella di root" utilizzando il comando corrispondente al CMS che hai scelto:

> [!tabs]
> **WordPress**
>> 
>> ```bash
>> wget http://wordpress.org/latest.tar.gz
>> ```
>>
>> **latest** permette di installare automaticamente l'ultima versione del CMS.
>>
> **Joomla!**
>> 
>> ```bash
>> wget https://downloads.joomla.org/cms/joomla4/4-2-8/Joomla_4-2-8-Stable-Full_Package.tar.gz
>> ```
>> 
>> **Joomla4** e **4-2-8** corrispondono, alla data, all'ultima versione di Joomla! disponibile
>> Sostituisci questi valori con quelli che vuoi installare.
>> 
> **Drupal**
>> 
>> ```bash
>> wget https://ftp.drupal.org/files/projects/admin_toolbar-8.x-2.4.tar.gz
>> ```
>> 
>> **8.x-2.4** corrisponde, alla data, all'ultima versione di Drupal disponibile.
>> Sostituisci questo valore con quello che vuoi installare.
>> 
> **PrestaShop**
>> 
>> ```bash
>> wget https://github.com/PrestaShop/PrestaShop/archive/1.7.8.8.tar.gz
>> ```
>> 
>> **1.7.8.8** corrisponde, alla data, all'ultima versione di PrestaShop disponibile. Sostituisci questo valore con quello che vuoi installare.
>> 

- Elimina i file sorgente dal tuo CMS nella cartella root utilizzando il comando corrispondente al CMS che hai scelto:

> [!tabs]
> **WordPress**
>> 
>> ```bash
>> tar xvf latest.tar.gz
>> ```
>> 
> **Joomla!**
>> 
>> ```bash
>> tar xvf Joomla_4-2-8-Stable-Full_Package.tar.gz
>> ```
>> 
> **Drupal**
>> 
>> ```bash
>> tar xvf admin_toolbar-8.x-2.4.tar.gz
>> ```
>> 
> **PrestaShop**
>> 
>> ```bash
>> tar xvf 1.7.8.8.tar.gz
>> ```
>> 

- La cartella "root" crea una cartella "**CMS**". Sposta il contenuto alla base della tua "cartella di root":

```bash
mv CMS/* ./
```

- Elimina la cartella "**CMS**", ormai vuota:

```bash
rmdir ./CMS/
```

- Elimina il file compresso corrispondente al CMS scelto:

> [!tabs]
> **WordPress**
>> ```bash
>> rm -f latest.tar.gz
>> ```
>> 
> **Joomla!**
>> ```bash
>> rm -f Joomla_4-2-8-Stable-Full_Package.tar.gz
>> ```
>> 
> **Drupal**
>> ```bash
>> rm -f admin_toolbar-8.x-2.4.tar.gz
>> ```
>> 
> **PrestaShop**
>> ```bash
>> rm -f 1.7.8.8.tar.gz
>> ```
>> 

### Step 3 - Completare l'installazione manuale <a name="step3"></a>

> [!success]
>
> Prima di continuare l'installazione, svuota la cache del tuo browser per evitare errori.
>

A partire da questo step, la procedura varia in base al CMS scelto precedentemente.

Per proseguire con l'installazione, segui uno di questi link cliccando sulla guida corrispondente al tuo CMS:

- [Completare l'installazione di Wordpress](/pages/web_cloud/web_hosting/cms_manual_installation_wordpress)
- [Completare l'installazione di Joomla!](/pages/web_cloud/web_hosting/cms_manual_installation_joomla)
- [Completare l'installazione di Drupal](/pages/web_cloud/web_hosting/cms_manual_installation_drupal)
- [Completare l'installazione di PrestaShop](/pages/web_cloud/web_hosting/cms_manual_installation_prestashop)
- [Completare l'installazione di Pico](/pages/web_cloud/web_hosting/cms_manual_installation_pico)
- [Completare l'installazione di Grav](/pages/web_cloud/web_hosting/cms_manual_installation_grav)
- [Completare l'installazione di Typo3](/pages/web_cloud/web_hosting/cms_manual_installation_typo3)
- [Completare l'installazione di SPIP](/pages/web_cloud/web_hosting/cms_manual_installation_spip)

## Per saperne di più <a name="go-further"></a>

[Migrazione del tuo sito Web e delle tue email verso OVHcloud](/pages/web_cloud/web_hosting/hosting_migrating_to_ovh)

[Pubblicare un sito Internet su un hosting Web](/pages/web_cloud/web_hosting/hosting_how_to_get_my_website_online)

[Ospitare più siti su uno stesso hosting](/pages/web_cloud/web_hosting/multisites_configure_multisite)

Per prestazioni specializzate (referenziamento, sviluppo, ecc...), contatta i [partner OVHcloud](/links/partner).

Per usufruire di un supporto per l'utilizzo e la configurazione delle soluzioni OVHcloud, è possibile consultare le nostre soluzioni [offerte di supporto](/links/support).

Contatta la nostra [Community di utenti](/links/community).