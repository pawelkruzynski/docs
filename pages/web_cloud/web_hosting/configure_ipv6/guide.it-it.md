---
title: "Configura un indirizzo IPv6 per il tuo sito Web"
excerpt: "Questa guida ti mostra come rendere il tuo sito Web compatibile con un indirizzo IPv6"
updated: 2024-03-12
---

## Obiettivo

La rete Internet funziona dall'inizio degli anni '90 seguendo lo standard IPv4. Questa norma permette di fornire un indirizzo IP X.X.X.X (o le "X" sono numeri compresi tra 0 e 255) a ciascuna delle macchine collegate alla rete Internet (server, computer, smartphone, tablet, ecc.). Tuttavia, tale norma limita a circa 4 miliardi il numero di dispositivi connessi alla rete Internet, che nel 2022 rappresentava meno di un apparecchio connesso per due persone sulla Terra.

In seguito, il protocollo **IPv6** è stato introdotto per permettere di connettere alla rete Internet fino a 340 sextitillions di apparecchi. La sua implementazione richiede tempo perché l'intera rete Internet deve integrare questa nuova norma. 

Dato che gli indirizzi IPv4 sono meno disponibili, è più difficile aggiungere nuove macchine sulla rete con lo standard IPv4. Tuttavia, le connessioni con un indirizzo IPv6 sono utili solo se, ad esempio, il tuo sito Web è anche disponibile con lo stesso protocollo. In questo modo, più siti web accessibili in IPv6, più i diversi attori presenti sulla rete Internet trasferiranno i loro dispositivi/macchine su questo nuovo protocollo.

Per maggiori informazioni, consulta l'articolo di [Wikipedia](https://it.wikipedia.org/wiki/IPv6){.external} sul protocollo IPv6.

I nostri hosting Web sono compatibili con IPv6 dal 2011. L'attivazione di questo protocollo è rimasta fino a poco tempo fa un'opzione facoltativa alla configurazione. 

**Questa guida ti mostra come verificare la compatibilità del tuo sito con il protocollo IPv6 e come configurarlo con un indirizzo IPv6.**

## Prerequisiti

- Avere un [dominio](/links/web/domains){.external} nello Spazio Cliente OVHcloud
- Disporre di una [offerta di hosting Web](/links/web/hosting){.external}
- Avere accesso allo [Spazio Cliente OVHcloud](/links/manager){.external}

## Procedura

> [!warning]
>
> OVHcloud mette a tua disposizione servizi di cui tu sei responsabile per la configurazione e la gestione. Assicurarne il corretto funzionamento è quindi responsabilità dell'utente.
> 
> Questa guida ti aiuta a eseguire le operazioni necessarie. Tuttavia, in caso di difficoltà o dubbi, ti consigliamo di rivolgerti a uno [specialista del settore](/links/partner) o di contattare l'amministratore del servizio. OVHcloud non potrà fornirti alcuna assistenza. Per maggiori informazioni consulta la sezione ["Per saperne di più"](#go-further) di questo tutorial.
> 

Se il tuo sito non è configurato per funzionare con un indirizzo IPv6, puoi aggiungere [l'indirizzo IPv6 del tuo hosting condiviso OVHcloud](/pages/web_cloud/web_hosting/clusters_and_shared_hosting_IP) nella zona DNS attiva del tuo dominio. L'obiettivo è permettere ai browser di trovare un indirizzo IPv6 associato al tuo sito Web tramite il tuo dominio.

### Verifica la compatibilità IPv6 del tuo sito Web

Per verificare se il tuo sito Web utilizza già un indirizzo IPv6, utilizza il sito [ipv6-test.com](https://ipv6-test.com/validate.php){.external}. Ti dirà se il tuo sito Web risponde a questo nuovo protocollo IP. In caso contrario, prosegui nella lettura della guida.

### Step 1: recuperare l'indirizzo IPv6 del tuo hosting Web

Accedi al tuo [Spazio Cliente OVHcloud](/links/manager){.external}. Nella sezione `Web Cloud`{.action}, clicca su `Hosting`{.action}, seleziona il nome dell'hosting e clicca sulla scheda `Informazioni generali`{.action}.

Nel riquadro **IPv6**, copia l'record e passa allo step successivo.

![IPv6](/pages/assets/screens/control_panel/product-selection/web-cloud/web-hosting/general-information/find-ipv6.png){.thumbnail}

### Step 2: configurare la zona DNS attiva del dominio

> [!warning]
>
> Le nostre opzioni CDN sono attualmente incompatibili con gli indirizzi IPv6. Se configuri un indirizzo IPv6 per il tuo sito Web, i tuoi visitatori non usufruiranno della CDN.
>
> Inoltre, l'aggiunta, la modifica o l'eliminazione di un record DNS nella zona DNS attiva di un dominio comporta un tempo di propagazione da **4 a 24 ore** per essere pienamente efficace.
>

Per consentire al browser di trovare l'indirizzo IPv6 con il tuo dominio, modifica la zona DNS attiva del tuo dominio. Per creare un record DNS di tipo **AAAA**, consulta la guida "[Modificare una zona DNS OVHcloud](/pages/web_cloud/domains/dns_zone_edit)".

Nella sezione `Web Cloud`{.action}, clicca su `Domini`{.action}. Seleziona il tuo dominio e clicca sulla scheda `Zona DNS`{.action}. Clicca su `Aggiungi un record`{.action} a destra della tabella. 

Inserisci l'indirizzo IPv6 precedentemente copiato utilizzando il tipo di record **AAAA**.

![IPv6](/pages/assets/screens/control_panel/product-selection/web-cloud/domain-dns/dns-zone/add-dns-zone-entry-aaaa.png){.thumbnail}

## Per saperne di più <a name="go-further"></a>

[Modifica una zona DNS OVHcloud](/pages/web_cloud/domains/dns_zone_edit)

Per prestazioni specializzate (referenziamento, sviluppo, ecc...), contatta i [partner OVHcloud](/links/partner).

Per usufruire di un supporto per l'utilizzo e la configurazione delle soluzioni OVHcloud, è possibile consultare le nostre soluzioni [offerte di supporto](/links/support).

Contatta la nostra [Community di utenti](/links/community).