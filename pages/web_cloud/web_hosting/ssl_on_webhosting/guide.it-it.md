---
title: "Hosting Web - Gestire un certificato SSL"
excerpt: "Questa quiga ti mostra come attivare e utilizzare un certificato SSL sugli hosting Web OVHcloud"
updated: 2024-10-31
---

## Obiettivo

I certificati Secure Socket Layer (SSL) permettono di cifrare gli scambi effettuati da o verso il sito Web. In questo modo si evita che un utente o un robot malevolo "ascolti" chiaramente le richieste inviate dal sito Web.

OVHcloud propone diversi tipi di certificati SSL sulle nostre soluzioni di [hosting condiviso OVHcloud](/links/web/hosting). Per maggiori informazioni, consulta questa guida. I certificati SSL sono indispensabili per la sicurezza del sito Web.

Esistono tre tipi di certificati SSL:

- Domain Validation (DV)
- Organization validation (OV)
- Extended Validation (EV)

I livelli di crittografia SSL sono identici tra questi tre tipi di certificati.

La principale differenza risiede nel livello di controlli che saranno effettuati dall'Autorità di Certificazione (CA) che rilascia il certificato SSL e ne attesta l'autenticità.

Per utilizzare il protocollo HTTPS è indispensabile disporre di un certificato SSL.

**Questa quiga ti mostra come gestire un certificato SSL su un hosting Web OVHcloud.**

## Prerequisiti

- Disporre di un piano di [hosting Web OVHcloud](/links/web/hosting) attivo.
- Aver registrato almeno un [dominio](/links/web/domains).
- Avere accesso allo [Spazio Cliente OVHcloud](/links/manager).

## Procedura

> [!warning]
>
> **Prima di proseguire**, verifica che **i domini e/o sottodomini interessati dal tuo futuro certificato SSL:
>
> - punta(nt) verso l’indirizzo IP del tuo hosting Web;
> - è (sono) dichiarato/i come multisito sul tuo hosting Web.
>
> Per maggiori informazioni, consulta le nostre guide:
>
> - [Ospitare più siti su uno stesso hosting](/pages/web_cloud/web_hosting/multisites_configure_multisite);
> - [Lista degli indirizzi IP di cluster e hosting Web](/pages/web_cloud/web_hosting/clusters_and_shared_hosting_IP);
> - [Modificare una zona DNS di OVHcloud](/pages/web_cloud/domains/dns_zone_edit).

### Attivare un certificato SSL sul proprio hosting Web <a name="ssl-enable"></a>

OVHcloud propone 4 soluzioni per attivare/installare un certificato SSL su un hosting Web. Per ognuna di queste soluzioni viene fornita una documentazione dettagliata.

Trovi qui sotto i 4 link verso le nostre guide dedicate a queste 4 soluzioni:

- [Attivare il certificato SSL gratuito Let's Encrypt (DV)](/pages/web_cloud/web_hosting/ssl_letsencrypt): certificato che può includere fino a **99** domini/sottodomini dichiarati su un hosting Web.
- [Attivare il certificato SSL a pagamento Sectigo (DV)](/pages/web_cloud/web_hosting/ssl_dv): certificato valido per un solo dominio + il relativo sottodominio in "www" (esempio: `domain.tld` e `www.domain.tld`) o **solo** un sottodominio (esempio: `sub.domain.tld`).
- [Attivare il certificato SSL a pagamento Sectigo (EV)](/pages/web_cloud/web_hosting/ssl_ev): certificato valido per un solo dominio + suo sottodominio in "www" (esempio: `domain.tld` e `www.domain.tld`) o **solo** un sottodominio (esempio: `sub.domain.tld`).
- [Installare un certificato SSL personalizzato](/pages/web_cloud/web_hosting/ssl_custom): se disponi di un tuo certificato SSL o se nessuna delle 3 soluzioni precedenti risponde alle tue necessità.

> [!primary]
>
> È possibile installare un solo certificato SSL per ogni hosting Web (tra le 4 soluzioni citate in precedenza).
>
> Se hai bisogno di attivare un certificato SSL per più domini/sottodomini dichiarati sul tuo hosting Web, prediligi l’installazione di un [certificato SSL gratuito Let’s Encrypt](/links/web/hosting-options-ssl) o installa il tuo [certificato SSL personalizzato](/pages/web_cloud/web_hosting/ssl_custom).

### Eliminare un certificato SSL da un hosting Web <a name="delete-ssl"></a>

> [!warning]
>
> Per rimuovere un certificato SSL da un hosting Web e **prima di continuare, assicurati che la rimozione del certificato non abbia impatto sulla raggiungibilità dei tuoi siti Web. In questo caso, gli utenti visualizzeranno un errore di sicurezza quando tenteranno di accedere al sito Web in "HTTPS".

Queste operazioni sono relative ai parametri dei tuoi siti Web, per cui OVH non fornisce assistenza. In caso di difficoltà o dubbi, ti consigliamo di contattare un esperto del settore. OVH non sarà in grado di fornirti assistenza.

Per rimuovere il certificato SSL installato sull’hosting Web, esegui queste operazioni:

1. Accedi allo [Spazio Cliente OVHcloud](/links/manager).
2. Nella riga superiore dello Spazio Cliente, clicca sulla scheda `Web Cloud`{.action}.
3. Nella colonna di sinistra, clicca sul menu a tendina `Hosting`{.action}.
4. Seleziona il tuo hosting Web.
5. Nella nuova pagina, rimani nella scheda `Informazioni generali`{.action}.
6. Posizionati nel riquadro intitolato `Configurazione`.
7. A destra della voce `Certificato SSL`, clicca sul pulsante `...`{.action} e poi su `Elimina SSL`{.action}.
8. Nella nuova finestra, clicca su `Conferma`{.action} per confermare l’eliminazione del certificato SSL.

![Delete SSL](/pages/assets/screens/control_panel/product-selection/web-cloud/web-hosting/general-information/delete-ssl.png){.thumbnail}

L’operazione diventerà effettiva entro poche ore.

> [!warning]
>
> L'eliminazione di un certificato SSL a pagamento **Sectigo** (DV o EV) è definitiva, anche se il certificato non era ancora scaduto. Non verrà effettuato alcun rimborso proporzionale al tempo restante. Per reinstallare un certificato SSL **Sectigo** (DV o EV), è necessario effettuare un nuovo ordine e pagare per l'intero importo del nuovo certificato SSL sottoscritto.
>

### Correggi i frequenti errori dei certificati SSL degli hosting Web

#### "You already have an SSL certificate on your account. It will be migrated on new SSL offers in the next week."

Questo messaggio indica che sei già proprietario di un certificato SSL. Non è quindi necessario attivare un nuovo certificato SSL su un hosting Web.

- 1: Se il certificato SSL installato sul tuo hosting Web è un certificato SSL gratuito Let's Encrypt, consulta la nostra guida sul certificato SSL [Let's Encrypt (DV)](/pages/web_cloud/web_hosting/ssl_letsencrypt) per proseguire nelle tue operazioni.

- 2: Se il certificato SSL installato sull’hosting Web non è quello che vuoi utilizzare, puoi [eliminare il tuo certificato SSL](#delete-ssl) attuale e poi [attivare un nuovo certificato SSL](#ssl-enable) sul tuo hosting Web.

#### ""No attached domain with ssl enabled or no attached domain that redirect on hosting IPs, please use hosting IP in your domain zone."

La notifica può essere motivata in tre casi.

- 1: il dominio associato al sito Web punta verso l'indirizzo IP della CDN del tuo hosting Web, con nessuna opzione CDN attiva sul tuo hosting Web:

Per risolvere il problema, assegna l’indirizzo IP dell’hosting Web senza CDN al dominio nella zona DNS attiva.
Per recuperare l’indirizzo IP dell’hosting Web, consulta la nostra guida "[Lista degli indirizzi IP di cluster e hosting Web](/pages/web_cloud/web_hosting/clusters_and_shared_hosting_IP)".
Per modificare la zona DNS attiva del dominio, consulta la nostra guida "[Modificare una zona DNS di OVHcloud](/pages/web_cloud/domains/dns_zone_edit)".

- 2: Il dominio associato al sito Web non punta verso l'indirizzo IP dell’hosting Web:

Per risolvere il problema, assegna l’indirizzo IP dell’hosting Web al dominio nella zona DNS attiva.
Se sul tuo hosting Web hai attivato un'opzione CDN, puoi utilizzare anche l'indirizzo IP dell'hosting Web con CDN.
Per recuperare l’indirizzo IP dell’hosting Web, consulta la nostra guida "[Lista degli indirizzi IP di cluster e hosting Web](/pages/web_cloud/web_hosting/clusters_and_shared_hosting_IP)".
Per modificare la zona DNS attiva del dominio, consulta la nostra guida "[Modificare una zona DNS di OVHcloud](/pages/web_cloud/domains/dns_zone_edit)".

- 3: Nessuno dei domini presenti nella scheda "Multisito" dispone di un'opzione SSL "attiva":

Per risolvere il problema, attiva il certificato SSL per il o i domini. Se necessario, consulta la sezione "[Attivare un certificato SSL](#ssl-enable)" di questa guida per proseguire con le tue azioni.

#### Hai ordinato un SSL Sectigo EV contemporaneamente al tuo hosting Web, ma il certificato non è ancora attivo e l'hosting Web non funziona correttamente

Questa situazione è dovuta agli step da eseguire per attivare il certificato SSL EV sul tuo hosting Web.

Per risolvere il problema, consulta la nostra guida "[Hosting Web - Attiva un certificato SSL Sectigo EV](/pages/web_cloud/web_hosting/ssl_ev)".

> [!primary]
>
> Se il certificato SSL EV non è totalmente attivo, l'ordine non verrà mai chiuso e non genererà mai fatture. Di conseguenza, il servizio di hosting Web non funzionerà correttamente.
>

#### Dopo la scadenza del Certificato SSL Sectigo (DV o EV), comparirà l'errore "No attached domain with ssl enabled or no attached domain that redirect on hosting IPs, please use hosting IP in your domain zone"

Questo errore si verifica ogni volta che il Certificato SSL Sectigo (attivato direttamente dall'hosting Web) scade e l'indirizzo IP dell'hosting Web cambia. In questo caso è necessario far puntare il dominio verso l’indirizzo IP corretto (record di tipo A), direttamente dalla zona DNS attiva del dominio.

Per recuperare l’indirizzo IP dell’hosting Web, consulta la nostra guida "[Lista degli indirizzi IP di cluster e hosting Web](/pages/web_cloud/web_hosting/clusters_and_shared_hosting_IP)".
Per modificare la zona DNS attiva del dominio, consulta la nostra guida "[Modificare una zona DNS di OVHcloud](/pages/web_cloud/domains/dns_zone_edit)".

#### Il certificato SSL è attivo sul tuo hosting Web, ma sul tuo sito viene visualizzato il messaggio "Your connection is not private"

Questo messaggio viene visualizzato nei seguenti casi:

- 1: La regola di reindirizzamento verso il tuo URL in "HTTPS" non è configurata correttamente o non esiste nel file ".htaccess":

Per risolvere il problema, consulta la nostra guida "[riscrivi l'URL di accesso al mio sito grazie al mod_rewrite tramite il file.htaccess](/pages/web_cloud/web_hosting/htaccess_url_rewriting_using_mod_rewrite)" o rivolgiti a un [provider specializzato](/links/partner) in caso di difficoltà.

- 2: Alcuni elementi della pagina Web non sono correttamente reindirizzati verso elementi cifrati in "HTTPS":

Per risolvere il problema, è necessario crittografare l’intero sito Web con il protocollo "HTTPS".
In caso di difficoltà o dubbi, consulta la guida "[Hosting Web - Passare il proprio sito Web in HTTPS](/pages/web_cloud/web_hosting/ssl-activate-https-website)" o rivolgiti a un [provider specializzato](/links/partner).

> [!success]
>
> Gli elementi interessati sulla pagina Web possono essere visualizzati direttamente dalle informazioni SSL del browser Internet, consultando i *dettagli del certificato*.
>

## Per saperne di più

[Hosting Web - Passare il proprio sito Web in HTTPS](/pages/web_cloud/web_hosting/ssl-activate-https-website).

[Errori comuni associati alla protezione del sito Web con il certificato SSL](/pages/web_cloud/web_hosting/ssl_avoid_common_pitfalls_of_making_website_secure).
 
Per prestazioni specializzate (referenziamento, sviluppo, ecc...), contatta i [partner OVHcloud](/links/partner).
 
Per usufruire di un supporto per l'utilizzo e la configurazione delle soluzioni OVHcloud, è possibile consultare le nostre soluzioni [offerte di supporto](/links/support).
 
Contatta la nostra [Community di utenti](/links/community).