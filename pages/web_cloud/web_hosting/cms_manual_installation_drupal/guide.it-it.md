---
title: "Tutorial - Installare manualmente Drupal"
excerpt: "Questa guida ti mostra come installare manualmente il tuo CMS Drupal"
updated: 2024-05-16
---
  
## Obiettivo

Qui trovi tutti gli elementi per installare manualmente il CMS (Content Management System) Drupal in pochi step.

> [!warning]
>
> OVHcloud mette a tua disposizione servizi di cui tu sei responsabile per la configurazione e la gestione. Assicurarne il corretto funzionamento è quindi responsabilità dell'utente.
> 
> Mettiamo a tua disposizione questo tutorial per supportarti nelle operazioni più frequenti. Tuttavia, in caso di difficoltà o dubbi, ti consigliamo di rivolgerti a uno [specialista del settore](/links/partner) o [amministratore del CMS Drupal](https://www.drupal.org/support){.external}. OVHcloud non potrà fornirti alcuna assistenza. Per maggiori informazioni, consulta la sezione ["Per saperne di più"](#go-further) di questo tutorial.
>
> Per aggiornare un CMS Drupal esistente o avere domande sull'utilizzo del CMS Drupal, contatta direttamente [l'editor del CMS Drupal](https://www.drupal.org/support){.external}.
>

> [!success]
>
> Per installare Drupal **automaticamente** dal tuo [Spazio Cliente OVHcloud](/links/manager), consulta la nostra guida sull'[installazione di un modulo "in un click"](/pages/web_cloud/web_hosting/cms_install_1_click_modules).
>
> Per installare **manualmente un altro CMS** (WordPress, Joomla!, PrestaShop), consulta la nostra guida sull'[installazione manuale di un CMS](/pages/web_cloud/web_hosting/cms_manual_installation).
>

**Questa guida ti mostra come installare manualmente il tuo CMS Drupal**
  
## Prerequisiti

- Disporre di un'offerta di [hosting web](/links/web/hosting) che contiene almeno un database.
- Disporre di un [dominio](/links/web/domains)
- Avere accesso allo [Spazio Cliente OVHcloud](/links/manager){.external}
  
## Procedura

### Step 1 - preparare l'installazione <a name="step1"></a>

Per installare il CMS **Drupal** sulla tua offerta di [hosting web](/links/web/hosting), sono necessari alcuni preparativi.

Segui **gli step** descritti nel nostro tutorial sull'[installazione manuale di un CMS](/pages/web_cloud/web_hosting/cms_manual_installation) prima di proseguire allo Step 2.

### Step 2 - finalizzare l'installazione manuale <a name="step2"></a>

> [!success]
>
> Prima di continuare l'installazione, svuota la cache del tuo browser per evitare errori.
>

#### 2.1 - Accedi al tuo sito Drupal attraverso il tuo browser

Inserisci il dominio nella barra di ricerca del browser

Se i file sorgente di Drupal sono stati inseriti correttamente nella cartella root, la pagina di selezione della lingua per Drupal appare:

![Drupal Installstep 1](/pages/assets/screens/other/cms/drupal/install-language-1.png){.thumbnail}

Seleziona la lingua del sito e clicca su `Save and Continue`{.action}.

#### 2.2 - Scegli il tipo di installazione

Drupal propone diversi livelli di installazione:

- una versione standard (consigliata), 
- una versione minima
- una versione di presentazione 

![Drupal Installstep 2](/pages/assets/screens/other/cms/drupal/install-profil-2.png){.thumbnail}

Ti consigliamo di installare questi strumenti **Standard**. Clicca su `Save and Continue`{.action}.

#### 2.3 - Associa il tuo Drupal al tuo database

Inserisci le informazioni richieste relative al database:

![Drupal Installstep 3](/pages/assets/screens/other/cms/drupal/install-db-config-3.png){.thumbnail}

Recupera le credenziali del tuo database (se necessario, consulta **lo Step 1.4** della guida sull'[installazione manuale di un CMS](/pages/web_cloud/web_hosting/cms_manual_installation)).

- *Database type*: scegli tra le opzioni proposte il tipo del tuo database.

- *Database name*: questo nome è stato definito durante la creazione del database nello [Spazio Cliente OVHcloud](/links/manager).

- *Database username*: è identico al nome del database se utilizzi un database incluso con il tuo hosting Web. Per i database creati su un servizio Web Cloud Databases, consulta le informazioni indicate nello **Step 1.4** del tutorial sull'[installazione manuale di un CMS](/pages/web_cloud/web_hosting/cms_manual_installation).

- *Database password*: l'hai definito tu stesso durante la creazione del tuo database. È possibile che tu l'abbia modificato nel frattempo.

Clicca su `Advanced Options`{.action} per scoprire il resto del menu.

- *Host*: inserisci il nome del server del database presente nell'email di installazione o nello Spazio Cliente OVHcloud. 

> [!primary]
> 
> - Il nome del server di un database incluso con la tua offerta di hosting Web ha questa forma: `NameOfYourDatabase.mysql.db` 
>
> - Il nome del server di un database Web Cloud Database inizia con il tuo identificativo cliente OVHcloud e viene mostrato come segue: `aa00000-XXX.eu.clouddb.ovh.net`, **"aa0000"** corrisponde al tuo identificativo OVHcloud senza il **"-ovh"** e i **"X"** sono sostituiti dal resto del riferimento del tuo servizio Web Cloud Databases.
>

- *Port number*: se utilizzi un database incluso con il tuo hosting OVHcloud, lascia per default **3306**. Se utilizzi un servizio Web Cloud Databases, fai riferimento allo **step 1.4** del tutorial sull'[installazione manuale di un CMS](/pages/web_cloud/web_hosting/cms_manual_installation) per recuperare il numero di porta corretto.

- *Table name prefix*: se l'installazione avviene con un nuovo database, inserisci il "prefisso" che preferisci. Se utilizzi un database già utilizzato da un altro sito, fai riferimento allo **step 1.4** del tutorial sull'[installazione manuale di un CMS](/pages/web_cloud/web_hosting/cms_manual_installation) per non inserire un "prefisso" di tavolo già utilizzato nel tuo database.

Clicca su `Save and Continue`{.action}.

Se tutto è stato realizzato correttamente, l'installazione di Drupal si avvia:

![Drupal Installstep 4](/pages/assets/screens/other/cms/drupal/install-4.png){.thumbnail}

#### 2.4 - Configura le informazioni del sito e l'accesso "Amministratore"

Una volta completato lo step precedente, visualizzi la pagina seguente:

![Drupal Installstep 5-1](/pages/assets/screens/other/cms/drupal/install-configure-site-5-1.png){.thumbnail}

Inserisci gli elementi richiesti:

- *Site name*: inserisci il nome del tuo futuro sito Drupal.

- *Site email address*: inserisci un indirizzo email valido che verrà utilizzato dal tuo sito Drupal.

- *Username*: inserisci un nome utente per accedere al tuo spazio di amministrazione Drupal (Back Office).

- *Password* e *Confirm password*: definisci la password associata al tuo nome utente per accedere al tuo *Back Office* Drupal.

Prosegui nella lettura di questa guida in basso:

![Drupal Installstep 5-1](/pages/assets/screens/other/cms/drupal/install-configure-site-5-2.png){.thumbnail}

- *Email address*: inserisci il tuo indirizzo email. Idealmente inserisci lo stesso indirizzo indicato sopra nel form *Indirizzo email del sito*.

- *Default country*: scegli il paese in cui il tuo sito sarà più visitato.

- *Default time zone*: seleziona il fuso orario di default per il tuo sito Web.

Clicca su `Save and Continue`{.action}.

Se tutto è andato a buon fine, visualizzi la pagina seguente:

![Drupal Installstep 6](/pages/assets/screens/other/cms/drupal/install-ending-6.png){.thumbnail}

> [!success]
>
> L'installazione di Drupal è terminata, puoi avviare la creazione del contenuto del tuo sito Drupal!
>
  
## Per saperne di più <a name="go-further"></a>

[Sito ufficiale Drupal](https://www.drupal.org/){.external}
 
Per prestazioni specializzate (referenziamento, sviluppo, ecc...), contatta i [partner OVHcloud](/links/partner).
 
Per usufruire di un supporto per l'utilizzo e la configurazione delle soluzioni OVHcloud, è possibile consultare le nostre soluzioni [offerte di supporto](/links/support).
 
Contatta la nostra [Community di utenti](/links/community).