---
title: Trasferire un dominio.uk in OVHcloud
excerpt: Questa guida ti mostra come trasferire un dominio.uk o equiparato a OVHcloud.
updated: 2024-06-28
---

## Obiettivo

Il trasferimento di un dominio.uk (o assimilato) richiede una procedura specifica.

> [!warning]
>
> OVHcloud mette a tua disposizione servizi di cui tu sei responsabile per la configurazione e la gestione. Garantirne quotidianamente il corretto funzionamento è quindi responsabilità dell’utente.
>
> Questa guida ti aiuta a eseguire le operazioni necessarie alla configurazione del tuo account. Tuttavia, in caso di difficoltà o dubbi, ti consigliamo di contattare un fornitore specializzato o l’amministratore del servizio. OVHcloud non potrà fornirti alcuna assistenza. Per maggiori informazioni consulta la sezione [Per saperne di più](#go-further) su questa guida.
>

**Come trasferire un dominio.uk (o equivalente) in OVHcloud**

> [!warning]
>
> Se il dominio in corso di modifica è registrato in OVHcloud, il trasferimento in entrata del dominio non è la procedura appropriata. Questa procedura si applica esclusivamente alla modifica del dominio registrato (OVHcloud).
>
> Per trasferire la gestione del tuo dominio verso un altro account cliente OVHcloud, la modalità corretta è una *modifica dei contatti*. La procedura è descritta in [guida](/pages/account_and_service_management/account_information/managing_contacts).
>
> Se è necessario modificare il **proprietario** del dominio, è necessario farlo **prima** di modificare i contatti del dominio. Segui le istruzioni descritte nella nostra guida sul [cambiamento di proprietario dei domini](/pages/web_cloud/domains/trade_domain).
>
> Se, oltre al trasferimento del dominio, vuoi anche migrare i servizi associati (sito Web, email, ecc...), prima di proseguire consulta la nostra guida "[Migrare il sito Web e i servizi associati in OVHcloud](/pages/web_cloud/web_hosting/hosting_migrating_to_ovh)".
> Questa guida ti mostra come migrare tutti i tuoi servizi senza interruzioni di servizio.
>
> Se trasferisci il tuo dominio senza trasferire gli altri servizi, assicurati di recuperare i server DNS attivi per il tuo dominio presso il tuo **Registrar** attuale e di inserirli direttamente nello step 3 della guida "[Trasferisci il tuo dominio in OVHcloud](/pages/web_cloud/domains/transfer_incoming_generic_domain)"
> In questo modo eviterai di interrompere l'associazione tra il tuo dominio e i tuoi servizi esterni associati.
>

## Prerequisiti

- Il tuo dominio non deve essere in fase di **redemption** o di eliminazione.
- Il dominio non deve essere bloccato presso il tuo registrar. 
- Le coordinate del proprietario devono essere ben aggiornate nel [Whois](https://www.nominet.uk/whois/){.external} del dominio.
- Riceverai il codice di autorizzazione che verrà inviato all'indirizzo email del proprietario.

> [!primary]
>
> Il periodo di **redemption** è di massimo 90 giorni a partire dalla data di scadenza del dominio. In caso di trasferimento, questo periodo permette di ripristinare il dominio e sbloccare la possibilità di trasferirlo.

## Estensioni interessate

- .uk
- .co.uk
- .ac.uk
- .gov.uk
- .me.uk
- .net.uk
- .org.uk
- .plc.uk
- .sch.uk

## Procedura

### Procedura di trasferimento

#### Step 1: Modifica del TAG del tuo dominio

Per trasferire il tuo dominio in OVHcloud, è necessario indicare preventivamente il TAG OVHcloud presso il tuo attuale registrar. Il TAG OVHcloud è "OVH-FR". La lista dei TAGS dei vari registrar è disponibile sul sito ufficiale del registro [Nominet](https://registrars.nominet.uk/uk-namespace/registrar-agreement/list-of-registrars/){.external}.

> [!primary]
>
> Se non riesci a effettuare la modifica del Tag del tuo dominio tramite
> il tuo attuale Registrar, puoi inoltrare una richiesta al Registrar
> Nominet per richiedere la modifica.
> Accedi alla pagina del Registry: "Manage your domain - Change registrar".
> Attenzione, questa operazione è fatturata per Nominet.
>

#### Step 2: Ottenimento del codice di autorizzazione al trasferimento

Una volta modificato il TAG, il proprietario del dominio riceverà dopo qualche minuto un codice di autorizzazione ("authcode") via email. Il servizio, valido per 5 giorni, permetterà di avviare l'ordine (gratuito) del dominio presso OVHcloud.

#### Step 3: Ordine di trasferimento gratuito

Una volta recuperato il codice di autorizzazione, è possibile ricercare ed avviare l'ordine di trasferimento del dominio sul sito OVHcloud. L'ordine è simile a quello di qualsiasi altro dominio generico.

Il dominio sarà disponibile nello [Spazio Cliente OVHcloud](/links/manager) entro poche ore.

### Informazioni utili

#### Costo del trasferimento di un dominio con estensione .uk (o assimilato)

Il trasferimento è gratuito.

#### Validità del codice di autorizzazione

Il codice di autorizzazione è generato automaticamente a seguito della modifica del TAG. Se l'ordine non viene eseguito entro 5 giorni, il trasferimento sarà annullato presso il registro.

#### Rinnovo del dominio a seguito di un trasferimento

Poiché il trasferimento è gratuito, la data di scadenza del dominio dopo il trasferimento sarà la stessa che prima del trasferimento. Per rinnovarlo in seguito al trasferimento, accedi al [sito OVHcloud](https://www.ovh.co.uk/cgi-bin/order/renew.cgi).

## Per saperne di più <a name="go-further"></a>

[Trasferire un dominio in OVHcloud](/pages/web_cloud/domains/transfer_incoming_generic_domain)

Contatta la nostra [Community di utenti](/links/community).