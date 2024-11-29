---
title: "Tutorial - riscrivi l'URL di accesso al mio sito grazie al mod_rewrite tramite il file.htaccess"
excerpt: "Questa tutorial ti mostra come riscrivere l'URL di accesso al tuo sito grazie al mod_rewrite tramite il file.htaccess"
updated: 2022-12-22
---

## Obiettivo

Il "**mod_rewrite**" è uno dei moduli disponibili sul server Web HTTP **Apache**. **Apache** è installato su tutta la nostra infrastruttura di hosting condiviso. Questi server Web permettono di gestire tutte le richieste HTTP inviate al tuo hosting Web.

Ad esempio, è Apache che recupera le richieste HTTP generate dai browser Internet dei visitatori del tuo sito e restituisce loro il contenuto richiesto dalle stesse richieste. I browser mostreranno poi il contenuto del tuo sito Web ai visitatori.

Il "**mod_rewrite**" permette ad esempio di riscrivere e reindirizzare:

- un visitatore che inserisce il tuo URL in "HTTP" direttamente verso l'URL del tuo sito Web in "HTTPS"
- l'insieme degli URL utilizzati per il tuo sito Web verso una cartella o un file specifico;
- un visitatore che inserisce il tuo URL senza "www" direttamente verso l'URL del tuo sito web con le "www".

Il "**mod_rewrite**" offre un'infinità di possibilità. Di seguito vi mostreremo alcuni esempi di utilizzo tra i più comuni.

> [!success]
>
> Per approfondire le tue conoscenze sull'utilizzo del "**mod_rewrite**" di Apache o se l'esempio che cerchi non è presente nel tutorial successivo, consulta la [documentazione ufficiale di Apache](https://httpd.apache.org/docs/2.4/fr/mod/mod_rewrite.html).
>

**Questa tutorial ti mostra come riscrivere l'URL di accesso al tuo sito grazie al mod_rewrite tramite il file.htaccess**
  
## Prerequisiti

- Disporre di un [hosting condiviso OVHcloud](/links/web/hosting)
  
## Procedura

> [!warning]
>
> OVHcloud mette a tua disposizione servizi di cui tu sei responsabile per la configurazione e la gestione. Assicurarne il corretto funzionamento è quindi responsabilità dell'utente.
> 
> Questa guida ti aiuta a eseguire le operazioni necessarie. Tuttavia, in caso di difficoltà o dubbi, ti consigliamo di rivolgerti a uno [specialista del settore](/links/partner). OVHcloud non potrà fornirti alcuna assistenza. Per maggiori informazioni consulta la sezione [Per saperne di più](#go-further) di questa guida.
>
>
> Gli esempi che seguiranno dovranno essere inseriti in un file ".htaccess". Attenzione, le regole definite in questo file hanno conseguenze dirette sul tuo sito Web. Prima di applicarle al tuo sito, verifica sistematicamente le regole che aggiungi.
>

Il file ".htaccess" nel quale configura il "**mod_rewrite**" di Apache può essere inserito in diverse cartelle. Dovrai rispettare solo la regola di un **solo** file ".htaccess" per cartella o sottocartella.

I parametri definiti in un file ".htaccess" si applicano alla directory in cui è presente e a tutte le sue sottodirectory.

Per modificare o creare directory, accedi allo spazio FTP del tuo hosting. Se necessario, consulta la guida "[Accedi al tuo spazio di storage](/pages/web_cloud/web_hosting/ftp_connection)".

Di seguito trovi alcuni esempi tra i più comuni di utilizzo del "**mod_rewrite**" di Apache. Alcuni di loro possono anche favorire l'SEO del tuo sito Web.

### Reindirizza tutte le richieste HTTP verso un unico file del tuo sito

Modifica il file ".htaccess" presente alla root della directory contenente il tuo sito web. Inserisci questo codice (sostituendo nel nostro esempio **test.php** con il nome del tuo file):

```bash
RewriteEngine On
RewriteRule .* test.php
```

Nel nostro esempio, tutte le richieste effettuate verso il tuo sito Web sono reindirizzate verso il file **test.php**.

### Reindirizzare una parte delle richieste HTTP verso un unico file del tuo sito Web

Modifica il file ".htaccess" presente alla root della directory contenente il tuo sito web. Inserisci all'interno il seguente codice (sostituendo nel nostro esempio i valori **thetest** e **/test_wslash/test.php** con i nomi dei tuoi file):

```bash
RewriteEngine On
RewriteRule thetest /test_wslash/test.php
```

Nel nostro esempio, tutte le richieste HTTP che contengono **/thetest** sono reindirizzate al file **/test_wslash/test.php**.

### Reindirizza il tuo dominio verso il sottodominio in "www"

Questa regola di riscrittura costringe l'indirizzo/URL del tuo sito ad essere riscritto con il sottodominio in "www".

Modifica il file ".htaccess" presente alla root della directory contenente il tuo sito web. Inserisci questo codice (sostituendo nel nostro esempio **domain.tld** con il tuo dominio):

```bash
RewriteEngine on
RewriteCond %{HTTP_HOST} ^domain.tld$
RewriteRule ^(.*) http://www.domain.tld/$1 [QSA,L,R=301]
```

Questa riscrittura dell'URL può favorire l'indicizzazione SEO del tuo sito Web.

### Reindirizzare le richieste verso una cartella specifica senza visualizzare la pratica in questione

Quando utilizzi un hosting condiviso OVHcloud, il tuo dominio (ad esempio **domain.tld**) è dichiarato in `Multisito` per visualizzare il contenuto di una cartella di destinazione conosciuta anche `Cartella di root`. È possibile personalizzare il nome di `Cartella di root`

Per maggiori informazioni sull'argomento, consulta la nostra guida sulla [configurazione di un multisito su un hosting condiviso](/pages/web_cloud/web_hosting/multisites_configure_multisite).

Alcuni utenti non caricano il loro sito direttamente alla base della `Cartella di root` e creano una sottocartella (ad esempio: **MyWebsite**) nella loro `Cartella di root` per creare il tuo sito Web.

In questo caso, l'URL per accedere al sito avrà la forma seguente: **http://domain.tld/MyWebsite**

Se il tuo sito Web non è presente direttamente nella `Cartella di root` dichiarata in multisito per il tuo dominio e se non vuoi visualizzare il nome della cartella nell'URL del tuo sito, modifica il file ".htaccess" presente nella cartella che contiene il tuo sito Web. 

Inserisci il seguente codice all'interno (sostituendo nel nostro esempio i valori **domain.tld** con il tuo dominio e **MyWebsite*** con il nome della tua cartella):

```bash
RewriteEngine on
RewriteCond %{HTTP_HOST} ^domain.tld
RewriteCond %{REQUEST_URI} !^/MyWebsite
RewriteRule ^(.*)$ /MyWebsite/
```

Nel nostro esempio, questo costringe l'indirizzo del tuo sito ad essere di tipo **http://domain.tld**, mentre in realtà la pagina è **http://domain.tld/MyWebsite**.

### Reindirizzare automaticamente un visitatore verso il tuo sito Web in HTTPS quando lo consulta con un URL in HTTP

I certificati SSL consentono di cifrare gli scambi effettuati in HTTP con il tuo sito Web. Ciò impedisce a persone o robot malevoli di raccogliere i dati scambiati tra il sito e il visitatore, come ad esempio le coordinate bancarie.

Se non disponi di un certificato SSL, consulta la nostra guida sulla [gestione di un certificato SSL su un hosting condiviso OVHcloud](/pages/web_cloud/web_hosting/ssl_on_webhosting).

Alcuni visitatori possono dimenticare di inserire l'URL di accesso al tuo sito in **https://** : questo rappresenta un rischio non trascurabile per i dati scambiati tra il tuo sito Web e i loro browser.

Per impedirlo, modifica il file ".htaccess" presente alla root della directory contenente il tuo sito Web. Inserisci questo codice (sostituendo nel nostro esempio **domain.tld** con il tuo dominio):

```bash
RewriteEngine On
RewriteCond %{SERVER_PORT} 80
RewriteRule ^(.*)$ https://www.domain.tld/$1 [R,L]
```

Nel nostro esempio, tutte le richieste effettuate con un URL in "**http://**" saranno automaticamente riscritte in "**https://**". I visitatori saranno così reindirizzati verso il tuo sito in "**https://**".
  
## Per saperne di più <a name="go-further"></a>

[Bloccare l'accesso al mio sito web per alcuni indirizzi IP tramite un file.htaccess](/pages/web_cloud/web_hosting/htaccess_how_to_block_a_specific_ip_address_from_accessing_your_website)

[Proteggere l'interfaccia di gestione del tuo sito con un file.htaccess](/pages/web_cloud/web_hosting/htaccess_protect_directory_by_password)

Per prestazioni specializzate (referenziamento, sviluppo, ecc...), contatta i [partner OVHcloud](/links/partner).

Per usufruire di un supporto per l'utilizzo e la configurazione delle soluzioni OVHcloud, è possibile consultare le nostre soluzioni [offerte di supporto](/links/support).

Contatta la nostra [Community di utenti](/links/community).