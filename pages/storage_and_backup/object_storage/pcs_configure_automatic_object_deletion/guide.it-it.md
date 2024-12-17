---
title: Object Storage Swift - Configura la cancellazione automatica dei tuoi oggetti
excerpt: Configura la cancellazione automatica dei tuoi oggetti
updated: 2021-10-27
---

## Obiettivo

Per gestire più facilmente il tuo Object Storage, potrebbe essere necessario definire la durata di vita di alcuni dei tuoi file. Questo ti permette, ad esempio, di conservare alcuni backup solo per un determinato periodo.

Questa guida ti mostra come impostare la cancellazione automatica dei tuoi file, dopo un periodo stabilito o in una data specifica.

## Requisiti necessari

- [Prepara il tuo ambiente di sviluppo per utilizzare l'API OpenStack](/pages/public_cloud/compute/prepare_the_environment_for_using_the_openstack_api)
- [Imposta le variabili d'ambiente OpenStack](/pages/public_cloud/compute/loading_openstack_environment_variables)

## Procedura

Puoi eliminare i tuoi file:

- dopo un certo numero di secondi
- in una data specifica

### Dopo un certo numero di secondi

Per eseguire questa operazione, configura l'header `X-Delete-After` della tua richiesta:

```bash
root@server:~$ swift copy --header "X-Delete-After: 3600" container test.txt
```

Nel nostro esempio, il file test.txt sarà eliminato dopo 1 ora.

### In una data specifica

Innanzitutto, è necessario conoscere la data di eliminazione in formato epoch.
Per trovare più facilmente il valore da inserire, utilizza un [convertitore](http://www.epochconverter.com/){.external}.

Una volta eseguita questa operazione, inserisci la data nell'header `X-Delete-At`:

```bash
root@server:~$ swift copy --header "X-Delete-At: 1668877261000" container test.txt
```

Nel nostro esempio, il file test.txt sarà eliminato il 19/11/2021.

## Per saperne di più

Se avete bisogno di formazione o di assistenza tecnica per implementare le nostre soluzioni, contattate il vostro rappresentante o cliccate su [questo link](/links/professional-services) per ottenere un preventivo e richiedere un'analisi personalizzata del vostro progetto da parte dei nostri esperti del team Professional Services.
  
Contatta la nostra Community di utenti all’indirizzo <https://community.ovh.com/en/>.
