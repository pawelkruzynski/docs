---
title: "Tutorial - Utilizza il file htaccess con WordPress"
excerpt: "Come proteggere un blog WordPress con uno o più file htaccess"
updated: 2024-05-28
---

## Obiettivo

Questa guida ti mostra come configurare alcune funzionalità del tuo hosting Web con uno o più file **.htaccess**, in particolare per modificare i parametri di una parte o dell'insieme del tuo sito Web (reindirizzamenti, divieti di accesso, autorizzazioni limitate, controllo della cache, ecc...).

> [!warning]
>
> OVHcloud mette a tua disposizione servizi di cui tu sei responsabile per la configurazione e la gestione. Assicurarne il corretto funzionamento è quindi responsabilità dell'utente.
> 
> Mettiamo a tua disposizione questo tutorial per supportarti nelle operazioni più frequenti. Tuttavia, in caso di difficoltà o dubbi, ti consigliamo di rivolgerti a uno [specialista del settore](/links/partner) o [l'amministratore del CMS WordPress](https://wordpress.com/it/support/){.external}. OVHcloud non potrà fornirti alcuna assistenza. Per maggiori informazioni consulta la sezione ["Per saperne di più"](#go-further) di questo tutorial.
>

**Questa guida ti mostra come proteggere il tuo WordPress con uno o più file htaccess.**

## Prerequisiti

- Disporre di un [hosting Web](/links/web/hosting) e aver installato WordPress
- Essere in grado di utilizzare un client FTP come [FileZilla](https://filezilla-project.org/) Consulta la guida "[Utilizzare FileZilla](/pages/web_cloud/web_hosting/ftp_filezilla_user_guide)".

I file **.htaccess** possono essere creati e modificati con editor di testo come:

- [Blocco note](https://support.microsoft.com/it-it/windows/assistenza-per-blocco-note-4d68c388-2ff2-0e7f-b706-35fb2ab88a8c){.external} di Windows;
- [TextEdit](https://support.apple.com/it-it/guide/textedit/welcome/mac){.external} su macOS;
- [Notepad++](https://notepad-plus-plus.org/){.external}.

> [!primary]
>
> Le soluzioni di sicurezza proposte qui sotto non sono esaustive.
>
> Ad esempio, se utilizzi un altro **C**ontent **M**anagement **S**ystem (**CMS**) che WordPress, esistono altre soluzioni di sicurezza.
>
> Se non utilizzi un CMS, OVHcloud mette a tua disposizione un tutorial sulla [protezione di una directory o dell'interfaccia di gestione del tuo sito Web tramite file .htaccess](/pages/web_cloud/web_hosting/htaccess_protect_directory_by_password).
>
> Per qualsiasi domanda relativa alla creazione, all'utilizzo o alla programmazione del tuo sito Web, contatta la nostra [community di utenti](/links/community) o i nostri [partner OVHcloud](/links/partner). I team del supporto OVHcloud non saranno in grado di fornirti assistenza su questi argomenti.
>

## FAQ

### Cos'è un file **.htaccess**?

Un file **.htaccess** permette di configurare un server Web. Nel caso di un hosting web condiviso, si tratta del server web open source "**Apache**". La sintassi di questo file è definita dall'organismo che modifica e mantiene **Apache**. A differenza della maggior parte dei file di configurazione di un server, i file **.htaccess** sono situati nelle directory dei siti Web, nello spazio di storage FTP del tuo hosting Web. Un file **.htaccess** avrà effetti sulla directory in cui è presente e su tutte le sottocartelle presenti all'interno.

Le nostre offerte di hosting condivisi non autorizzano i file di configurazione server. Tuttavia, i file **.htaccess** danno la possibilità di modificare alcune caratteristiche e comportamenti. Inoltre, non è necessario riavviare il server **Apache** affinché le indicazioni e le modifiche scritte nel file **.htaccess** siano prese in carico. Tutte le nostre offerte di [hosting web condiviso OVHcloud](/links/web/hosting) permettono di configurare file **.htaccess*.

Il punto davanti al nome del file **.htaccess** (senza estensione) designa un file nascosto. Questi file non sono accessibili da utenti esterni che accedono al tuo sito Web.

### Cos'è un server web?

Un server Web è un software che consente lo scambio di informazioni su una rete utilizzando il protocollo *HTTP*.<br>
Ce ne sono molti, tra cui *Apache*, *Nginx*, *Tomcat* o il modulo http incluso nella *NodeJS*.

### Quali sono le precauzioni da prendere?

Una configurazione errata del tuo file **.htaccess** può generare errori sul tuo server (come un errore 500: *Internal Server Error*) o rendere totalmente indisponibile il tuo servizio, anche per te. È normale eseguire backup sistematici delle versioni dei tuoi file funzionali, in modo da poter tornare a uno stato precedente in caso di guasti a seguito di una modifica.

Allo stesso modo, se non hai l'abitudine di manipolare questo tipo di file, fai un test su ogni elemento che modifichi. In questo modo eviti di perdere tempo per ritrovare la linea o le linee che hanno causato il malfunzionamento del tuo server Web. Un errore di configurazione o un semplice errore di battitura possono compromettere la configurazione del tuo server Web e quindi il suo funzionamento.

### Quali strumenti utilizzare?

- client FTP per recuperare i tuoi file (FileZilla, Cyberduck)
- un editor di testo.

### Dove sono localizzati i file .htaccess in WordPress?

Come precisato nell'introduzione, è possibile avere più file**.htaccess** su uno stesso hosting Web. Ciascuno di questi file definisce le regole per la directory in cui si trova, nonché le sottocartelle che contiene.

La maggior parte delle modifiche avverrà a livello di **radice del sito web**. Installato di default, il file **.htaccess** nella root del sito contiene queste righe:

```bash
# BEGIN WordPress
# Le linee guida tra "BEGIN WordPress" e "END WordPress" sono generate
# dinamicamente e devono essere modificati solo tramite i filtri WordPress.
# Ogni modifica delle direttive tra questi marcatori sarà sovraccaricata.

<IfModule mod_rewrite.c>
RewriteEngine On
RewriteRule .* - [E=HTTP_AUTHORIZATION:%{HTTP:Authorization}]
RewriteBase /
RewriteRule ^index\.php$ - [L]
RewriteCond %{REQUEST_FILENAME} !-f
RewriteCond %{REQUEST_FILENAME} !-d
RewriteRule . /index.php [L]
</IfModule>

# END WordPress
```

**Spiegazioni del codice di cui sopra**:

- **#** : carattere utilizzato per mettere una riga di commento.
- **RewriteEngine On**: attiva il modulo Apache `mod_rewrite`, che permette la riscrittura dell'URL al volo (consente anche di reindirizzare un URL verso un altro URL).
- **RewriteRule**: questa sintassi si scrive in base alla figura `RewriteRule Modello Sostitution`. La scrittura può essere presente più volte nel file **.htaccess** (è il caso nel file predefinito che trovi alla radice dell'installazione del tuo WordPress). L'ordine di scrittura nel file è fondamentale, assicurati di essere vigili sull'ordine in cui scrivi le tue regole.
- **RewriteBase**: indica che la radice del sito è `/`.
- **RewriteCond**: si tratta di condizioni preliminari per la regola che segue direttamente. Nel nostro caso, la prima condizione esclude gli URL che contengono un percorso verso un file reale, mentre la seconda esclude, invece, le sottodirectory.

### Cosa posso aggiungere in un file **.htaccess** con WordPress?

Esistono diversi modi per definire e modificare i parametri che cambieranno il comportamento del server (alcune limitazioni esistono tuttavia in funzione dell'hosting):

- modificare i file di configurazione del tuo server
- aggiungere o modificare direttive nel file di configurazione **wp-config.php** alla radice del tuo sito Web
- modificare o aggiungere direttive nel file **.htaccess** alla radice.

## Procedura

> [!warning]
>
> Prima di seguire gli step qui sotto, è necessario reindirizzare il protocollo HTTP verso HTTPS. Per effettuare questa operazione, segui le istruzioni contenute nella guida [Attivare il protocollo HTTPS su un sito Internet tramite SSL](/pages/web_cloud/web_hosting/ssl-activate-https-website#step-1-attiva-il-certificato-ssl-sullhosting).

### Impedire la visualizzazione delle directory e delle sottodirectory

Per evitare di permettere a tutti i visitatori del tuo sito di visualizzare il contenuto delle sotto-directory (e accidentalmente dare informazioni ai pirati sui temi o sulle estensioni utilizzate), blocca la visualizzazione del contenuto aggiungendo questa riga nel tuo file **.htaccess**:

```bash
Options All -Indexes
```

### Proteggi il tuo file di configurazione

Il tuo file **wp-config.php**, presente alla radice del tuo sito Web, contiene informazioni di configurazione sensibili. Impedisci l'accesso a questo file aggiungendo queste righe nel tuo file **.htaccess**:

```bash
<Files wp-config.php>
    order allow,deny
    deny from all
    satisfy all
</Files>
```

### Blocca un indirizzo IP

Se hai identificato un indirizzo IP malevolo, inserisci la riga nel tuo file **.htaccess*:

> [!tabs]
> **IPv4**
>>
>>```bash
>> <Limit GET POST>
>>   order allow,deny 
>>   deny from 203.0.113.0
>>   allow from all
>> </Limit>
>>```
>>
>> In questo esempio `203.0.113.0` indica l'indirizzo IPv4 da bloccare.
>>
> **IPv6**
>>
>>```bash
>> <Limit GET POST>
>>   order allow,deny 
>>   deny from 2001:db8:1:1b00:203:0:113:0
>>   allow from all
>> </Limit>
>>```
>>
>> In questo esempio `2001:db8:1:1b00:203:0:113:0` indica l'indirizzo IPv6 da bloccare.
>>

Per maggiori informazioni su questo argomento, consulta la nostra guida sulla ["restrizione di accesso via IP tramite il file.htaccess"](/pages/web_cloud/web_hosting/htaccess_how_to_block_a_specific_ip_address_from_accessing_your_website).

#### Blocca un indirizzo IP dalla directory wp-admin (o nelle altre directory)

La directory **wp-admin** permette di accedere alla tua interfaccia di amministrazione (il metodo funziona anche con le altre directory, ma corrispondono a URL che non portano a un'interfaccia specifica). Per proteggere questa directory, autorizzi in modo specifico l'accesso a uno o più indirizzi IP utilizzando il seguente codice da inserire nel tuo **.htaccess**:

> [!tabs]
> **IPv4**
>>
>>```bash
>> <Limit GET POST PUT>
>>   order deny,allow 
>>   deny from all
>>   allow from 203.0.113.0
>>   allow from 203.0.113.1
>> </Limit>
>>```
>>
>> In questo esempio, solo gli indirizzi IPv4 `203.0.113.0` e `203.0.113.1` sono autorizzati ad accedere alla directory in cui si trova il file .htaccess.
>>
> **IPv6**
>>
>>```bash
>> <Limit GET POST PUT>
>>   order deny,allow 
>>   deny from all
>>   allow from 2001:db8:1:1b00:203:0:113:0
>>   allow from 2001:db8:1:1b00:203:0:113:1
>> </Limit>
>>```
>>
>> In questo esempio, solo gli indirizzi IPv6 `2001:db8:1:1b00:203:0:113:0` e `2001:db8:1:1b00:203:0:113:1` sono autorizzati ad accedere alla directory in cui si trova il file .htaccess.

### Informazioni importanti da ricordare

- Salva una versione funzionale del tuo file **.htaccess** prima di effettuare qualsiasi operazione.
- Se le modifiche apportate provocano un errore, sostituisci (tramite il tuo client FTP) il file **.htaccess** online con la versione precedente.
- Puoi gestire alcuni parametri nel tuo file **wp-config.php**
- I file **.htaccess** sono particolarmente efficaci per la gestione di URL, reindirizzamenti e la sicurezza del tuo sito Web.

## Per saperne di più <a name="go-further"></a>

Consulta il [tutorial disponibile sul sito della Fondazione Apache](https://httpd.apache.org/docs/2.4/en/howto/htaccess.html).

Per prestazioni specializzate (referenziamento, sviluppo, ecc...), contatta i [partner OVHcloud](/links/partner).

Per usufruire di un supporto per l'utilizzo e la configurazione delle soluzioni OVHcloud, è possibile consultare le nostre soluzioni [offerte di supporto](/links/support).

Contatta la nostra [Community di utenti](/links/community).