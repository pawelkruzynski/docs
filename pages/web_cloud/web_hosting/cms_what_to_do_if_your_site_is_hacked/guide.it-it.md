---
title: "Casi d'uso - Consigli in seguito alla pirateria del tuo sito Web"
excerpt: "Scopri i nostri consigli per riparare il tuo sito Web pirata"
updated: 2022-11-15
---

## Obiettivo

Questa guida ti mostra come il tuo sito Web è stato piratato. Di seguito **i 4 step da effettuare nell'ordine** per correggere la situazione.

La pirateria può manifestarsi in diversi modi (elenco non esaustivo):

- il tuo sito Web non appare più correttamente o per nulla, senza alcuna modifica (FTP, SQL o DNS) da parte tua
- il tuo sito Web è reindirizzato verso un altro sito
- il tuo sito genera "annunci" intempestivi (Pop-up, finestre di errori, ecc...)
- il database del tuo sito Web è subito compilato
- dall'hosting vengono generati SPAM generati da script infetti.

**Scopri i nostri consigli per riparare il tuo sito Web pirata.**

> [!warning]
>
> OVHcloud mette a tua disposizione servizi di cui tu sei responsabile per la configurazione e la gestione. Assicurarne il corretto funzionamento è quindi responsabilità dell'utente.
> 
> Mettiamo a tua disposizione questo tutorial per supportarti nelle operazioni più frequenti. Tuttavia, in caso di difficoltà o dubbi, ti consigliamo di rivolgerti a uno [specialista del settore](/links/partner). OVHcloud non potrà fornirti alcuna assistenza. Per maggiori informazioni consulta la sezione ["Per saperne di più"](#go-further) di questa guida.
>

## Prerequisiti

- Disporre di una [offerta di hosting Web Cloud](/links/web/hosting) con il tuo sito Web ospitato su
- Avere accesso allo [Spazio Cliente OVHcloud](/links/manager)

## Procedura

La pirateria di un sito Web è sistematicamente legata a **almeno**:

- mancanza di aggiornamenti del sito Web;
- software spia presente su uno dei dispositivi che utilizzi per amministrare il tuo sito Web;
- l'utilizzo di un plugin o di un tema "non ufficiale", in particolare se utilizzi un Content Managment System (CMS) come WordPress, Joomla!, PrestaShop o Drupal
- password (FTP, SQL, "back office" per i CMS, ecc.) troppo corte o troppo facili da trovare, soprattutto se non cambiate;
- uno script del tuo sito che apre deliberatamente porte a livello del tuo hosting Web **senza** verificare quello che riceve da queste porte;
- diritti di accesso FTP "CHMOD" un po' troppo permissivi.

**La pirateria di un sito Web non deriva da un difetto di sicurezza dell'hosting Web.** Solo gli script/file ospitati sono in grado di dare ordini all'hosting. Gli enti creditizi possono chiedere o meno di aprire alcuni porti di accesso chiusi di default o di eseguire o meno alcune azioni.<br>
Gli script ordinano, l'hosting esegue.

### Step 1 - scannerizza tutti i tuoi dispositivi

Esegui un'analisi anti-virus e anti-spyware di tutti i dispositivi (PC, Mac, smartphone/Iphone, tablet,...) da cui gestisci l'amministrazione o la gestione del tuo sito Web.

> [!warning]
>
> Se utilizzi dispositivi che funzionano con *Linux*, *Mac OS* o altri sistemi operativi per i quali è comunemente indicato che non esiste il rischio di avere un virus o un software "spia", **effettua comunque questa analisi**.
>
> **Nessun sistema operativo è immune da malware/malware.**
>

> [!success]
>
> Ti consigliamo di utilizzare diversi anti-virus/anti-spyware (gratuiti o a pagamento) per ogni tuo dispositivo.
> Effettivamente, alcuni virus o spyware possono persistere a seconda del software antivirus utilizzato.
> Esistono versioni di anti-virus/anti-spyware che puoi installare "in locale" sul tuo dispositivo o utilizzare direttamente "online" su Internet.
>

Se viene individuato un virus o un software spia, eliminalo utilizzando il tuo software anti-virus/anti-spyware **anteriormente** allo step successivo.

### Step 2 - modifica la password <a name="step2"></a>

Se un sito Web è stato hacker e precauzionale, modifica tutte le password associate.

Per OVHcloud, consulta la nostra guida:

- [Modifica la password di accesso al tuo identificativo cliente OVHcloud](/pages/account_and_service_management/account_information/manage-ovh-password).
- [Rendere sicuro l'accesso allo Spazio Cliente OVHcloud con doppia autenticazione](/pages/account_and_service_management/account_information/secure-ovhcloud-account-with-2fa).
- [Modificare la password di accesso allo spazio di storage FTP del tuo hosting Web](/pages/web_cloud/web_hosting/ftp_change_password).
- [Modifica la password di accesso al tuo database](/pages/web_cloud/web_hosting/sql_change_password).

Consigliamo inoltre di utilizzare un [gestore di password](/pages/account_and_service_management/account_information/manage-ovh-password#utilizza-un-software-per-la-gestione-di-password).

> [!warning]
> 
> Modificando la password del tuo database, ricordati di aggiornare la password anche nel file di configurazione del tuo sito Web. In caso contrario, il collegamento tra il database e i file presenti nello spazio di storage FTP del tuo hosting Web sarà interrotto e il tuo sito visualizzerà un "errore durante la connessione al tuo database".
>

> [!primary]
>
> Se utilizzi un CMS come WordPress, Joomla!, PrestaShop o Drupal, consulta la documentazione ufficiale del tuo CMS per modificare la password di accesso allo spazio di amministrazione del tuo CMS ("Back-office").
>

### Step 3 - ricercare i file malevoli e le falle di sicurezza

> [!warning]
>
> In caso di difficoltà nell'esecuzione delle azioni descritte di seguito, rivolgiti a un [fornitore specializzato](/links/partner) in sicurezza informatica.
>

Utilizza la nostra guida su [le statistiche e i log del tuo hosting Web](/pages/web_cloud/web_hosting/logs_and_statistics) per ricercare gli elementi malevoli iniettati nel tuo sito Web. Trovi le informazioni nei log "web". 

Cerca a partire dalla data in cui hai rilevato la pirateria e torna allo storico dei tuoi log.

Identifica le richieste "POST" che escono dall'ordinario. Generalmente i file malevoli hanno nomi alfanumerici senza alcun significato particolare (**esempio***: az78e4jFn.txt, oij8bh4.html, udh73hd45.php, mlkjc23d.js, ...).

Recupera l'indirizzo IP che ha effettuato la richiesta malevola. Effettua una ricerca di questo indirizzo nei tuoi log per visualizzare tutte le azioni richieste sul tuo sito da questo IP.

> [!primary]
>
> In genere, più indirizzi IP malevoli chiamano, durante lo stesso periodo, gli script malevoli presenti in seguito alla pirateria.
> Ti ringraziamo per aver analizzato tutti i log del tuo hosting.
>

Raggiungi le falle di sicurezza presenti nel tuo sito, elencando i file malevoli che incontri.

> [!success]
>
> Alcuni siti (non gestiti da OVHcloud) possono permetterti di ottenere informazioni sugli IP malevoli. Puoi utilizzare uno di questi per recuperare informazioni come il provider dell'IP, la sua geolocalizzazione, il gestore, ecc...
>
> Se sei assolutamente sicuro che si tratti di un IP malevolo, puoi bloccarlo all'accesso al tuo hosting seguendo la nostra guida sulle [restrizioni di accesso tramite il file ".htaccess"](/pages/web_cloud/web_hosting/htaccess_how_to_block_a_specific_ip_address_from_accessing_your_website).
> 

### Step 4 - Eliminare gli elementi malevoli e correggere le falle di sicurezza

In questa fase sono possibili tre casi: 

> [!alert]
>
> **Importante**: In ogni caso, se elimini i codici malevoli senza correggere le falle di sicurezza, l'hacker potrebbe di nuovo utilizzarli per depositare nuovamente il codice malevolo sul tuo hosting. Avrebbe anche la possibilità di creare una nuova porta d'accesso.
>
> Il ripristino a una data anteriore alla pirateria richiederà un aggiornamento **immediato** e l'indispensabile realizzazione di un **audit di sicurezza**, al fine di identificare tutte le falle di sicurezza.
>

#### Caso n°1 - OVHcloud dispone di un backup del tuo sito Internet (spazio di storage FTP e database)

In base alla data di hacking del tuo sito (meno di 14 giorni), OVHcloud può fornirti un backup (non contrattuale).

Per farlo, consulta le nostre 3 guide sull'argomento:

- [Ripristinare lo spazio di storage FTP del tuo hosting Web](/pages/web_cloud/web_hosting/ftp_save_and_backup)
- [Recupera il backup SQL del tuo database](/pages/web_cloud/web_hosting/sql_database_export)
- [Importare il backup SQL nel tuo database](/pages/web_cloud/web_hosting/sql_importing_mysql_database)

Fai coincidere il più possibile le date di ripristino del tuo spazio di storage FTP e del tuo database SQL.

>[!warning]
>
> OVHcloud dispone di robot di sicurezza in grado di rilevare azioni malevoli eseguite dal tuo hosting. che disattivano il tuo hosting e ti avvisano via email che il tuo hosting è stato disattivato.
> In aggiunta a questa email, in genere compare una pagina "403 Forbidden" quando cerchi di accedere al tuo sito.
>
> Se il tuo hosting è "disattivato", i robot di ripristino automatico disponibili nello [Spazio Cliente OVHcloud](/links/manager) saranno disattivati.
> È necessario effettuare un ripristino "manuale" del sito, eliminare gli elementi malevoli residui e correggere eventuali falle di sicurezza presenti nel backup. Questa operazione **prima** di riattivare il tuo hosting.
>
> Per riattivare l'hosting Web, segui le istruzioni riportate nello Step 4 di questa [guida](/pages/web_cloud/web_hosting/diagnostic_403_forbidden).
>

Se le operazioni sono state eseguite correttamente, il sito dovrebbe essere riabilitato.

#### Caso n°2 - Disponi del tuo backup precedente la pirateria

Per farlo, consulta le nostre 2 guide sull'argomento:

- [Ripristinare lo spazio di storage FTP del tuo hosting Web](/pages/web_cloud/web_hosting/ftp_save_and_backup)
- [Importare il backup SQL nel tuo database](/pages/web_cloud/web_hosting/sql_importing_mysql_database)

>[!warning]
>
> OVHcloud dispone di robot di sicurezza in grado di rilevare azioni malevoli eseguite dal tuo hosting. che disattivano il tuo hosting e ti avvisano via email che il tuo hosting è stato disattivato.
> In aggiunta a questa email, in genere compare una pagina "403 Forbidden" quando cerchi di accedere al tuo sito.
>
> Se il tuo hosting è "disattivato", effettua un ripristino "manuale" del sito, rimuovi gli elementi malevoli residui e correggi tutte le falle di sicurezza presenti nel backup. Questa operazione **prima** di riattivare il tuo hosting.
>
> Per riattivare l'hosting Web, segui le istruzioni riportate nello Step 4 di questa [guida](/pages/web_cloud/web_hosting/diagnostic_403_forbidden).
>

Se le operazioni sono state eseguite correttamente, il sito dovrebbe essere riabilitato.

#### Caso n. 3 - nessun backup è disponibile per il tuo sito Web

Elimina manualmente i file e i codici malevoli precedentemente rilevati durante lo [step 2](#step2) di questa guida e correggi le falle di sicurezza del tuo sito.

Per accedere allo spazio di storage del tuo hosting, consulta la nostra guida (/pages/web_cloud/web_hosting/ftp_connection) sull'argomento.

> [!warning]
>
> OVHcloud dispone di robot di sicurezza in grado di rilevare azioni malevoli eseguite dal tuo hosting. che disattivano il tuo hosting e ti avvisano via email che il tuo hosting è stato disattivato.
> In aggiunta a questa email, in genere compare una pagina "403 Forbidden" quando cerchi di accedere al tuo sito.
>
> Se il tuo hosting è "disattivato", rimuovi gli elementi malevoli residui e correggi tutte le falle di sicurezza presenti nel backup **prima** di riattivare il tuo hosting.
>
> Per riattivare l'hosting Web, segui le istruzioni riportate nello Step 4 di questa [guida](/pages/web_cloud/web_hosting/diagnostic_403_forbidden).
>

Se le operazioni sono state eseguite correttamente, il sito dovrebbe essere riabilitato.

### Step 5 - Aggiorna il tuo sito

Aggiorna il tuo sito Web al suo codice sorgente, ai parametri di sicurezza di cui dispone, alle versioni di linguaggio che utilizza (in particolare PHP).

Verifica i diritti di accesso FTP "CHMOD" per ogni cartelle e file ospitati nel tuo spazio di archiviazione.
Di default, consigliamo di utilizzare al massimo i diritti "CHMOD" **705** per i fascicoli e **604** per i file.
Per maggiori informazioni sui permessi "CHMOD", consulta la sezione "Informazioni utili" del nostro [tutorial sull'utilizzo del client FTP Filezilla](/pages/web_cloud/web_hosting/ftp_filezilla_user_guide#useful-information).

Se utilizzi un CMS (Wordpress, Joomla!, PrestaShop, Drupal...), aggiorna i tuoi plugin, il tuo tema e il CMS in sé.
Utilizza plugin/temi "ufficiali" e aggiorna il tuo sito Web il più regolarmente possibile ed esaustivamente.

Proteggi i tuoi form di contatto con l'ausilio di un sistema di tipo "Captcha" per evitare che i robot malevoli emettano SPAM attraverso questo mezzo. Se la funzione "mail()" di PHP è stata bloccata sul tuo hosting, consulta [la nostra guida](/pages/web_cloud/web_hosting/mail_function_script_records) su questo argomento per risolvere il blocco.

Consulta anche la nostra guida su [come proteggere il tuo sito Web](/pages/web_cloud/web_hosting/secure_your_website), per ridurre al minimo il rischio di un'altra pirateria.

## Per saperne di più <a name="go-further"></a>

[Accedere allo spazio di storage del tuo hosting Web](/pages/web_cloud/web_hosting/ftp_connection)

[Modifica la configurazione di un hosting Web](/pages/web_cloud/web_hosting/configure_your_web_hosting)

[Attiva il firewall applicativo](/pages/web_cloud/web_hosting/multisites_activating_application_firewall)

[Ottimizza le performance del tuo sito](/pages/web_cloud/web_hosting/optimise_your_website_performance)

Per prestazioni specializzate (referenziamento, sviluppo, ecc...), contatta i [partner OVHcloud](/links/partner).

Per usufruire di un supporto per l'utilizzo e la configurazione delle soluzioni OVHcloud, è possibile consultare le nostre soluzioni [offerte di supporto](/links/support).

Contatta la nostra [Community di utenti](/links/community).