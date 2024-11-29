---
title: "Lista degli indirizzi IP di cluster e hosting Web"
excerpt: "Questa guida ti mostra comme tutti gli indirizzi IP disponibili con i nostri hosting Web"
updated: 2024-02-28
---

## Obiettivo

In questa guida sono elencati tutti gli indirizzi IP degli hosting Web OVHcloud. In questo modo è possibile individuare l’indirizzo IP da inserire nella tua zona DNS, in base a:

- cluster
- opzioni (CDN, SSL a pagamento, SSL gratuito, ecc.)
- Paese

**Questa guida ti mostra comme tutti gli indirizzi IP disponibili con i nostri hosting Web.**

> [!primary]
>
> Gli indirizzi IP dell’opzione CDN sono “Anycast”,
> ovvero non hanno bisogno di geolocalizzazione ([Maggiori informazioni qui](/links/web/hosting-options-cdn)).
> 

## Prerequisiti

- Disporre di un piano di [hosting Web](/links/web/hosting){.external} attivo
- Avere accesso allo [Spazio Cliente OVHcloud](/links/manager){.external}

## Procedura

Per conoscere il cluster di hosting Web su cui si trova il tuo servizio, accedi allo [Spazio Cliente OVHcloud](/links/manager) e seleziona `Web Cloud`{.action}. Seleziona il tuo servizio nella sezione `Hosting`{.action}. In seguito accedi alla scheda `FTP - SSH`{.action}.
Per verificare il numero di cluster dell'hosting Web, accedi alla pagina con il **Server FTP**.

### Cluster 002

Qui di seguito trovi gli indirizzi IP del **cluster** per ciascun Paese (per la geolocalizzazione):

|Paese|Codice Paese|IPv4|IPv6|
|---|---|----|---|
|Francia|FR|213.186.33.2|2001:41d0:1:1b00:213:186:33:2|
|Irlanda|IE|188.165.7.2|2001:41d0:1:1b00:188:165:7:2|
|Portogallo|PT|94.23.79.2|2001:41d0:1:1b00:94:23:79:2|
|Regno Unito|UK|87.98.255.2|2001:41d0:1:1b00:87:98:255:2|
|Italia|IT|94.23.64.2|2001:41d0:1:1b00:94:23:64:2|
|Spagna|ES|87.98.231.2|2001:41d0:1:1b00:87:98:231:2|
|Polonia|PL|87.98.239.2|2001:41d0:1:1b00:87:98:239:2|
|Repubblica Ceca|CZ|94.23.175.2|2001:41d0:1:1b00:94:23:175:2|
|Paesi Bassi|NL|94.23.151.2|2001:41d0:1:1b00:94:23:151:2|
|Finlandia|FI|188.165.143.2|2001:41d0:1:1b00:188:165:143:2|
|Lituania|LT|188.165.31.2|2001:41d0:1:1b00:188:165:31:2|
|Germania|DE|87.98.247.2|2001:41d0:1:1b00:87:98:247:2|

Se il **Shared CDN** è attivo sul tuo hosting, devi utilizzare questo indirizzo IP:

```bash
46.105.204.2
```

Se hai bisogno dell’indirizzo IP del **gateway di uscita** del tuo hosting, è necessario utilizzare questo indirizzo IP:

```bash
51.68.11.191
```

### Cluster 003

Qui di seguito trovi gli indirizzi IP del **cluster** per ciascun Paese (per la geolocalizzazione):

|Paese|Codice Paese|IPv4|IPv6|
|---|---|----|---|
|Francia|FR|213.186.33.4|2001:41d0:1:1b00:213:186:33:4|
|Irlanda|IE|188.165.7.4|2001:41d0:1:1b00:188:165:7:4|
|Portogallo|PT|94.23.79.4|2001:41d0:1:1b00:94:23:79:4|
|Regno Unito|UK|87.98.255.4|2001:41d0:1:1b00:87:98:255:4|
|Italia|IT|94.23.64.4|2001:41d0:1:1b00:94:23:64:4|
|Spagna|ES|87.98.231.4|2001:41d0:1:1b00:87:98:231:4|
|Polonia|PL|87.98.239.4|2001:41d0:1:1b00:87:98:239:4|
|Repubblica Ceca|CZ|94.23.175.4|2001:41d0:1:1b00:94:23:175:4|
|Paesi Bassi|NL|94.23.151.4|2001:41d0:1:1b00:94:23:151:4|
|Finlandia|FI|188.165.143.4|2001:41d0:1:1b00:188:165:143:4|
|Lituania|LT|188.165.31.4|2001:41d0:1:1b00:188:165:31:4|
|Germania|DE|87.98.247.4|2001:41d0:1:1b00:87:98:247:4|

Se il **Shared CDN** è attivo sul tuo hosting, devi utilizzare questo indirizzo IP:

```bash
46.105.204.3
```

Se hai bisogno dell’indirizzo IP del **gateway di uscita** del tuo hosting, è necessario utilizzare questo indirizzo IP:

```bash
51.68.11.195
```

### Cluster 005

Qui di seguito trovi gli indirizzi IP del **cluster** per ciascun Paese (per la geolocalizzazione):

|Paese|Codice Paese|IPv4|IPv6|
|---|---|----|---|
|Francia|FR|213.186.33.16|2001:41d0:1:1b00:213:186:33:16|
|Irlanda|IE|188.165.7.16|2001:41d0:1:1b00:188:165:7:16|
|Portogallo|PT|94.23.79.16|2001:41d0:1:1b00:94:23:79:16|
|Regno Unito|UK|87.98.255.16|2001:41d0:1:1b00:87:98:255:16|
|Italia|IT|94.23.64.16|2001:41d0:1:1b00:94:23:64:16|
|Spagna|ES|87.98.231.16|2001:41d0:1:1b00:87:98:231:16|
|Polonia|PL|87.98.239.16|2001:41d0:1:1b00:87:98:239:16|
|Repubblica Ceca|CZ|94.23.175.16|2001:41d0:1:1b00:94:23:175:16|
|Paesi Bassi|NL|94.23.151.16|2001:41d0:1:1b00:94:23:151:16|
|Finlandia|FI|188.165.143.16|2001:41d0:1:1b00:188:165:143:16|
|Lituania|LT|188.165.31.16|2001:41d0:1:1b00:188.165.31.16|
|Germania|DE|87.98.247.16|2001:41d0:1:1b00:87:98:247:16|

Se il **Shared CDN** è attivo sul tuo hosting, devi utilizzare questo indirizzo IP:

```bash
46.105.204.5
```

Se hai bisogno dell’indirizzo IP del **gateway di uscita** del tuo hosting, è necessario utilizzare questo indirizzo IP:

```bash
51.68.11.199
```

### Cluster 006

Qui di seguito trovi gli indirizzi IP del **cluster** per ciascun Paese (per la geolocalizzazione):

|Paese|Codice Paese|IPv4|IPv6|
|---|---|----|---|
|Francia|FR|213.186.33.17|2001:41d0:1:1b00:213:186:33:17|
|Irlanda|IE|188.165.7.17|2001:41d0:1:1b00:188:165:7:17|
|Portogallo|PT|94.23.79.17|2001:41d0:1:1b00:94:23:79:17|
|Regno Unito|UK|87.98.255.17|2001:41d0:1:1b00:87:98:255:17|
|Italia|IT|94.23.64.17|2001:41d0:1:1b00:94:23:64:17|
|Spagna|ES|87.98.231.17|2001:41d0:1:1b00:87:98:231:17|
|Polonia|PL|87.98.239.17|2001:41d0:1:1b00:87:98:239:17|
|Repubblica Ceca|CZ|94.23.175.17|2001:41d0:1:1b00:94:23:175:17|
|Paesi Bassi|NL|94.23.151.17|2001:41d0:1:1b00:94:23:151:17|
|Finlandia|FI|188.165.143.17|2001:41d0:1:1b00:188:165:143:17|
|Lituania|LT|188.165.31.17|2001:41d0:1:1b00:188:165:31:17|
|Germania|DE|87.98.247.17|2001:41d0:1:1b00:87:98:247:17|

Se il **Shared CDN** è attivo sul tuo hosting, devi utilizzare questo indirizzo IP:

```bash
46.105.204.6
```

Se hai bisogno dell’indirizzo IP del **gateway di uscita** del tuo hosting, è necessario utilizzare questo indirizzo IP:

```bash
51.68.11.203
```

### Cluster 007

Qui di seguito trovi gli indirizzi IP del **cluster** per ciascun Paese (per la geolocalizzazione):

|Paese|Codice Paese|IPv4|IPv6|
|---|---|----|---|
|Francia|FR|213.186.33.18|2001:41d0:1:1b00:213:186:33:18|
|Irlanda|IE|188.165.7.18|2001:41d0:1:1b00:188:165:7:18|
|Portogallo|PT|94.23.79.18|2001:41d0:1:1b00:94:23:79:18|
|Regno Unito|UK|87.98.255.18|2001:41d0:1:1b00:87:98:255:18|
|Italia|IT|94.23.64.18|2001:41d0:1:1b00:94:23:64:18|
|Spagna|ES|87.98.231.18|2001:41d0:1:1b00:87:98:231:18|
|Polonia|PL|87.98.239.18|2001:41d0:1:1b00:87:98:239:18|
|Repubblica Ceca|CZ|94.23.175.18|2001:41d0:1:1b00:94:23:175:18|
|Paesi Bassi|NL|94.23.151.18|2001:41d0:1:1b00:94:23:151:18|
|Finlandia|FI|188.165.143.18|2001:41d0:1:1b00:188:165:143:18|
|Lituania|LT|188.165.31.18|2001:41d0:1:1b00:188:165:31:18|
|Germania|DE|87.98.247.18|2001:41d0:1:1b00:87:98:247:18|

Se il **Shared CDN** è attivo sul tuo hosting, devi utilizzare questo indirizzo IP:

```bash
46.105.204.7
```

Se hai bisogno dell’indirizzo IP del **gateway di uscita** del tuo hosting, è necessario utilizzare questo indirizzo IP:

```bash
51.68.11.207
```

### Cluster 010

Qui di seguito trovi gli indirizzi IP del **cluster** per ciascun Paese (per la geolocalizzazione):

|Paese|Codice Paese|IPv4|IPv6|
|---|---|----|---|
|Francia|FR|213.186.33.19|2001:41d0:1:1b00:213:186:33:19|
|Irlanda|IE|188.165.7.19|2001:41d0:1:1b00:188:165:7:19|
|Portogallo|PT|94.23.79.19|2001:41d0:1:1b00:94:23:79:19|
|Regno Unito|UK|87.98.255.19|2001:41d0:1:1b00:87:98:255:19|
|Italia|IT|94.23.64.19|2001:41d0:1:1b00:94:23:64:19|
|Spagna|ES|87.98.231.19|2001:41d0:1:1b00:87:98:231:19|
|Polonia|PL|87.98.239.19|2001:41d0:1:1b00:87:98:239:19|
|Repubblica Ceca|CZ|94.23.175.19|2001:41d0:1:1b00:94:23:175:19|
|Paesi Bassi|NL|94.23.151.19|2001:41d0:1:1b00:94:23:151:19|
|Finlandia|FI|188.165.143.19|2001:41d0:1:1b00:188:165:143:19|
|Lituania|LT|188.165.31.19|2001:41d0:1:1b00:188:165:31:19|
|Germania|DE|87.98.247.19|2001:41d0:1:1b00:87:98:247:19|

Se il **Shared CDN** è attivo sul tuo hosting, devi utilizzare questo indirizzo IP:

```bash
46.105.204.10
```

Se hai bisogno dell’indirizzo IP del **gateway di uscita** del tuo hosting, è necessario utilizzare questo indirizzo IP:

```bash
51.68.11.211
```

### Cluster 011

Qui di seguito trovi gli indirizzi IP del **cluster** per ciascun Paese (per la geolocalizzazione):

|Paese|Codice Paese|IPv4|IPv6|
|---|---|----|---|
|Francia|FR|213.186.33.40|2001:41d0:1:1b00:213:186:33:40|
|Irlanda|IE|188.165.7.40|2001:41d0:1:1b00:188:165:7:40|
|Portogallo|PT|94.23.79.40|2001:41d0:1:1b00:94:23:79:40|
|Regno Unito|UK|87.98.255.40|2001:41d0:1:1b00:87:98:255:40|
|Italia|IT|94.23.64.40|2001:41d0:1:1b00:94:23:64:40|
|Spagna|ES|87.98.231.40|2001:41d0:1:1b00:87:98:231:40|
|Polonia|PL|87.98.239.40|2001:41d0:1:1b00:87:98:239:40|
|Repubblica Ceca|CZ|94.23.175.40|2001:41d0:1:1b00:94:23:175:40|
|Paesi Bassi|NL|94.23.151.40|2001:41d0:1:1b00:94:23:151:40|
|Finlandia|FI|188.165.143.40|2001:41d0:1:1b00:188:165:143:40|
|Lituania|LT|188.165.31.40|2001:41d0:1:1b00:188:165:31:40|
|Germania|DE|87.98.247.40|2001:41d0:1:1b00:87:98:247:40|

Se il **Shared CDN** è attivo sul tuo hosting, devi utilizzare questo indirizzo IP:

```bash
46.105.204.11
```

Se hai bisogno dell’indirizzo IP del **gateway di uscita** del tuo hosting, è necessario utilizzare questo indirizzo IP:

```bash
51.68.11.215
```

### Cluster 012

Qui di seguito trovi gli indirizzi IP del **cluster** per ciascun Paese (per la geolocalizzazione):

|Paese|Codice Paese|IPv4|IPv6|
|---|---|----|---|
|Francia|FR|213.186.33.48|2001:41d0:1:1b00:213:186:33:48|
|Irlanda|IE|188.165.7.48|2001:41d0:1:1b00:188:165:7:48|
|Portogallo|PT|94.23.79.48|2001:41d0:1:1b00:94:23:79:48|
|Regno Unito|UK|87.98.255.48|2001:41d0:1:1b00:87:98:255:48|
|Italia|IT|94.23.64.48|2001:41d0:1:1b00:94:23:64:48|
|Spagna|ES|87.98.231.48|2001:41d0:1:1b00:87:98:231:48|
|Polonia|PL|87.98.239.48|2001:41d0:1:1b00:87:98:239:48|
|Repubblica Ceca|CZ|94.23.175.48|2001:41d0:1:1b00:94:23:175:48|
|Paesi Bassi|NL|94.23.151.48|2001:41d0:1:1b00:94:23:151:48|
|Finlandia|FI|188.165.143.48|2001:41d0:1:1b00:188:165:143:48|
|Lituania|LT|188.165.31.48|2001:41d0:1:1b00:188:165:31:48|
|Germania|DE|87.98.247.48|2001:41d0:1:1b00:87:98:247:48|

Se il **Shared CDN** è attivo sul tuo hosting, devi utilizzare questo indirizzo IP:

```bash
46.105.204.12
```

Se hai bisogno dell’indirizzo IP del **gateway di uscita** del tuo hosting, è necessario utilizzare questo indirizzo IP:

```bash
51.68.11.219
```

### Cluster 013

Qui di seguito trovi gli indirizzi IP del **cluster** per ciascun Paese (per la geolocalizzazione):

|Paese|Codice Paese|IPv4|IPv6|
|---|---|----|---|
|Francia|FR|213.186.33.24|2001:41d0:1:1b00:213:186:33:24|
|Irlanda|IE|188.165.7.24|2001:41d0:1:1b00:188:165:7:24|
|Portogallo|PT|94.23.79.24|2001:41d0:1:1b00:94:23:79:24|
|Regno Unito|UK|87.98.255.24|2001:41d0:1:1b00:87:98:255:24|
|Italia|IT|94.23.64.24|2001:41d0:1:1b00:94:23:64:24|
|Spagna|ES|87.98.231.24|2001:41d0:1:1b00:87:98:231:24|
|Polonia|PL|87.98.239.24|2001:41d0:1:1b00:87:98:239:24|
|Repubblica Ceca|CZ|94.23.175.24|2001:41d0:1:1b00:94:23:175:24|
|Paesi Bassi|NL|94.23.151.24|2001:41d0:1:1b00:94:23:151:24|
|Finlandia|FI|188.165.143.24|2001:41d0:1:1b00:188:165:143:24|
|Lituania|LT|188.165.31.24|2001:41d0:1:1b00:188:165:31:24|
|Germania|DE|87.98.247.24|2001:41d0:1:1b00:87:98:247:24|

Se il **Shared CDN** è attivo sul tuo hosting, devi utilizzare questo indirizzo IP:

```bash
46.105.204.13
```

Se hai bisogno dell’indirizzo IP del **gateway di uscita** del tuo hosting, è necessario utilizzare questo indirizzo IP:

```bash
51.68.11.223
```

### Cluster 014

Qui di seguito trovi gli indirizzi IP del **cluster** per ciascun Paese (per la geolocalizzazione):

|Paese|Codice Paese|IPv4|IPv6|
|---|---|----|---|
|Francia|FR|213.186.33.87|2001:41d0:1:1b00:213:186:33:87|
|Irlanda|IE|188.165.7.87|2001:41d0:1:1b00:188:165:7:87|
|Portogallo|PT|94.23.79.87|2001:41d0:1:1b00:94:23:79:87|
|Regno Unito|UK|87.98.255.87|2001:41d0:1:1b00:87:98:255:87|
|Italia|IT|94.23.64.87|2001:41d0:1:1b00:94:23:64:87|
|Spagna|ES|87.98.231.87|2001:41d0:1:1b00:87:98:231:87|
|Polonia|PL|87.98.239.87|2001:41d0:1:1b00:87:98:239:87|
|Repubblica Ceca|CZ|94.23.175.87|2001:41d0:1:1b00:94:23:175:87|
|Paesi Bassi|NL|94.23.151.87|2001:41d0:1:1b00:94:23:151:87|
|Finlandia|FI|188.165.143.87|2001:41d0:1:1b00:188:165:143:87|
|Lituania|LT|188.165.31.87|2001:41d0:1:1b00:188:165:31:87|
|Germania|DE|87.98.247.87|2001:41d0:1:1b00:87:98:247:87|

Se il **Shared CDN** è attivo sul tuo hosting, devi utilizzare questo indirizzo IP:

```bash
46.105.204.14
```

Se hai bisogno dell’indirizzo IP del **gateway di uscita** del tuo hosting, è necessario utilizzare questo indirizzo IP:

```bash
51.68.11.227
```

### Cluster 015

Qui di seguito trovi gli indirizzi IP del **cluster** per ciascun Paese (per la geolocalizzazione):

|Paese|Codice Paese|IPv4|IPv6|
|---|---|----|---|
|Francia|FR|213.186.33.3|2001:41d0:1:1b00:213:186:33:3|
|Irlanda|IE|188.165.7.3|2001:41d0:1:1b00:188:165:7:3|
|Portogallo|PT|94.23.79.3|2001:41d0:1:1b00:94:23:79:3|
|Regno Unito|UK|87.98.255.3|2001:41d0:1:1b00:87:98:255:3|
|Italia|IT|94.23.64.3|2001:41d0:1:1b00:94:23:64:3|
|Spagna|ES|87.98.231.3|2001:41d0:1:1b00:87:98:231:3|
|Polonia|PL|87.98.239.3|2001:41d0:1:1b00:87:98:239:3|
|Repubblica Ceca|CZ|94.23.175.3|2001:41d0:1:1b00:94:23:175:3|
|Paesi Bassi|NL|94.23.151.3|2001:41d0:1:1b00:94:23:151:3|
|Finlandia|FI|188.165.143.3|2001:41d0:1:1b00:188:165:143:3|
|Lituania|LT|188.165.31.3|2001:41d0:1:1b00:188:165:31:3|
|Germania|DE|87.98.247.3|2001:41d0:1:1b00:87:98:247:3|

Se il **Shared CDN** è attivo sul tuo hosting, devi utilizzare questo indirizzo IP:

```bash
46.105.204.15
```

Se hai bisogno dell’indirizzo IP del **gateway di uscita** del tuo hosting, è necessario utilizzare questo indirizzo IP:

```bash
51.68.11.231
```

### Cluster 017

Qui di seguito trovi gli indirizzi IP del **cluster** per ciascun Paese (per la geolocalizzazione):

|Paese|Codice Paese|IPv4|IPv6|
|---|---|----|---|
|Francia|FR|213.186.33.50|2001:41d0:1:1b00:213:186:33:50|
|Irlanda|IE|188.165.7.50|2001:41d0:1:1b00:188:165:7:50|
|Portogallo|PT|94.23.79.50|2001:41d0:1:1b00:94:23:79:50|
|Regno Unito|UK|87.98.255.50|2001:41d0:1:1b00:87:98:255:50|
|Italia|IT|94.23.64.50|2001:41d0:1:1b00:94:23:64:50|
|Spagna|ES|87.98.231.50|2001:41d0:1:1b00:87:98:231:50|
|Polonia|PL|87.98.239.50|2001:41d0:1:1b00:87:98:239:50|
|Repubblica Ceca|CZ|94.23.175.50|2001:41d0:1:1b00:94:23:175:50|
|Paesi Bassi|NL|94.23.151.50|2001:41d0:1:1b00:94:23:151:50|
|Finlandia|FI|188.165.143.50|2001:41d0:1:1b00:188:165:143:50|
|Lituania|LT|188.165.31.50|2001:41d0:1:1b00:188:165:31:50|
|Germania|DE|87.98.247.50|2001:41d0:1:1b00:87:98:247:50|

Se il **Shared CDN** è attivo sul tuo hosting, devi utilizzare questo indirizzo IP:

```bash
46.105.204.17
```

Se hai bisogno dell’indirizzo IP del **gateway di uscita** del tuo hosting, è necessario utilizzare questo indirizzo IP:

```bash
51.68.11.239
```

### Cluster 020

Qui di seguito trovi gli indirizzi IP del **cluster** per ciascun Paese (per la geolocalizzazione):

|Paese|Codice Paese|IPv4|IPv6|
|---|---|----|---|
|Francia|FR|46.105.57.169|2001:41d0:301::20|
|Irlanda|IE|51.254.78.227|2001:41d0:301:3::20|
|Portogallo|PT|5.135.59.60|2001:41d0:301:2::20|
|Regno Unito|UK|51.254.94.183|2001:41d0:301:12::20|
|Italia|IT|37.59.236.156|2001:41d0:301:11::20|
|Spagna|ES|37.59.203.111|2001:41d0:301:4::20|
|Polonia|PL|178.32.149.185|2001:41d0:301:5::20|
|Repubblica Ceca|CZ|51.254.181.43|2001:41d0:301:6::20|
|Paesi Bassi|NL|37.59.164.205|2001:41d0:301:7::20|
|Finlandia|FI|5.196.208.117|2001:41d0:301:8::20|
|Lituania|LT|5.196.129.52|2001:41d0:301:9::20|
|Germania|DE|5.135.108.219|2001:41d0:301:1::20|
|Belgio|BE|5.196.203.200|2001:41d0:301:10::20|

Se il **Shared CDN** è attivo sul tuo hosting, devi utilizzare questo indirizzo IP:

```bash
46.105.204.20
```

Se hai bisogno dell’indirizzo IP del **gateway di uscita** del tuo hosting, è necessario utilizzare questo indirizzo IP:

```bash
91.134.248.253
```

### Cluster 021

Qui di seguito trovi gli indirizzi IP del **cluster** per ciascun Paese (per la geolocalizzazione):

|Paese|Codice Paese|IPv4|IPv6|
|---|---|----|---|
|Francia|FR|188.165.53.185|2001:41d0:301::21|
|Irlanda|IE|188.165.6.20|2001:41d0:301:6::21|
|Portogallo|PT|94.23.75.235|2001:41d0:301:2::21|
|Regno Unito|UK|94.23.152.220|2001:41d0:301:12::21|
|Italia|IT|94.23.69.227|2001:41d0:301:11::21|
|Spagna|ES|87.98.230.241|2001:41d0:301:4::21|
|Polonia|PL|188.165.23.19|2001:41d0:301:5::21|
|Repubblica Ceca|CZ|94.23.173.184|2001:41d0:301:6::21|
|Paesi Bassi|NL|94.23.144.60|2001:41d0:301:7::21|
|Finlandia|FI|188.165.139.219|2001:41d0:301:8::21|
|Lituania|LT|188.165.30.41|2001:41d0:301:9::21|
|Germania|DE|94.23.162.9|2001:41d0:301:1::21|
|Belgio|BE|178.32.40.72|2001:41d0:301:10::21|

Se il **Shared CDN** è attivo sul tuo hosting, devi utilizzare questo indirizzo IP:

```bash
46.105.204.21
```

Se hai bisogno dell’indirizzo IP del **gateway di uscita** del tuo hosting, è necessario utilizzare questo indirizzo IP:

```bash
91.134.248.245
```

### Cluster 023

Qui di seguito trovi gli indirizzi IP del **cluster** per ciascun Paese (per la geolocalizzazione):

|Paese|Codice Paese|IPv4|IPv6|
|---|---|----|---|
|Francia|FR|164.132.235.17|2001:41d0:301::23|
|Irlanda|IE|79.137.112.24|2001:41d0:301:3::23|
|Portogallo|PT|5.135.68.66|2001:41d0:301:2::23|
|Regno Unito|UK|178.32.59.150|2001:41d0:301:12::23|
|Italia|IT|178.32.140.171|2001:41d0:301:11::23|
|Spagna|ES|51.254.16.36|2001:41d0:301:4::23|
|Polonia|PL|87.98.235.184|2001:41d0:301:5::23|
|Repubblica Ceca|CZ|94.23.169.83|2001:41d0:301:6::23|
|Paesi Bassi|NL|94.23.148.187|2001:41d0:301:7::23|
|Finlandia|FI|178.32.17.246|2001:41d0:301:8::23|
|Lituania|LT|37.59.69.122|2001:41d0:301:9::23|
|Germania|DE|87.98.242.65|2001:41d0:301:1::23|
|Belgio|BE|137.74.229.68|2001:41d0:301:10::23|

Se il **Shared CDN** è attivo sul tuo hosting, devi utilizzare questo indirizzo IP:

```bash
46.105.204.23
```

Se hai bisogno dell’indirizzo IP del **gateway di uscita** del tuo hosting, è necessario utilizzare questo indirizzo IP:

```bash
91.134.248.235
```

### Cluster 024

Qui di seguito trovi gli indirizzi IP del **cluster** per ciascun Paese (per la geolocalizzazione):

|Paese|Codice Paese|IPv4|IPv6|
|---|---|----|---|
|Francia|FR|188.165.61.82|2001:41d0:301::24|
|Irlanda|IE|188.165.6.81|2001:41d0:301:3::24|
|Portogallo|PT|5.135.68.67|2001:41d0:301:2::24|
|Regno Unito|UK|178.32.59.194|2001:41d0:301:12::24|
|Italia|IT|178.32.140.172|2001:41d0:301:11::24|
|Spagna|ES|51.255.132.41|2001:41d0:301:4::24|
|Polonia|PL|94.23.88.105|2001:41d0:301:5::24|
|Repubblica Ceca|CZ|94.23.169.75|2001:41d0:301:6::24|
|Paesi Bassi|NL|94.23.149.14|2001:41d0:301:7::24|
|Finlandia|FI|188.165.138.2|2001:41d0:301:8::24|
|Lituania|LT|164.132.150.73|2001:41d0:301:9::24|
|Germania|DE|178.33.38.88|2001:41d0:301:1::24|
|Belgio|BE|213.32.81.103|2001:41d0:301:10::24|

Se il **Shared CDN** è attivo sul tuo hosting, devi utilizzare questo indirizzo IP:

```bash
46.105.204.24
```

Se hai bisogno dell’indirizzo IP del **gateway di uscita** del tuo hosting, è necessario utilizzare questo indirizzo IP:

```bash
91.134.248.230
```

### Cluster 026

Qui di seguito trovi gli indirizzi IP del **cluster** per ciascun Paese (per la geolocalizzazione):

|Paese|Codice Paese|IPv4|IPv6|
|---|---|----|---|
|Francia|FR|87.98.154.146|2001:41d0:301::26|
|Irlanda|IE|188.165.4.35|2001:41d0:301:3::26|
|Portogallo|PT|51.254.64.107|2001:41d0:301:2::26|
|Regno Unito|UK|91.134.201.112|2001:41d0:301:12::26|
|Italia|IT|94.23.66.212|2001:41d0:301:11::26|
|Spagna|ES|188.165.129.145|2001:41d0:301:4::26|
|Polonia|PL|178.32.205.96|2001:41d0:301:5::26|
|Repubblica Ceca|CZ|137.74.234.211|2001:41d0:301:6::26|
|Paesi Bassi|NL|137.74.180.117|2001:41d0:301:7::26|
|Finlandia|FI|137.74.48.119|2001:41d0:301:8::26|
|Lituania|LT|188.165.29.126|2001:41d0:301:9::26|
|Germania|DE|94.23.160.29|2001:41d0:301:1::26|
|Belgio|BE|178.32.43.46|2001:41d0:301:10::26|

Se il **Shared CDN** è attivo sul tuo hosting, devi utilizzare questo indirizzo IP:

```bash
46.105.204.26
```

Se hai bisogno dell’indirizzo IP del **gateway di uscita** del tuo hosting, è necessario utilizzare questo indirizzo IP:

```bash
91.134.248.211
```

### Cluster 027

Qui di seguito trovi gli indirizzi IP del **cluster** per ciascun Paese (per la geolocalizzazione):

|Paese|Codice Paese|IPv4|IPv6|
|---|---|----|---|
|Francia|FR|54.36.91.62|2001:41d0:301::27|
|Irlanda|IE|54.36.31.145|2001:41d0:301:3::27|
|Portogallo|PT|193.70.24.82|2001:41d0:301:2::27|
|Regno Unito|UK|54.36.203.165|2001:41d0:301:12::27|
|Italia|IT|178.32.138.212|2001:41d0:301:11::27|
|Spagna|ES|213.32.37.233|2001:41d0:301:4::27|
|Polonia|PL|178.32.203.125|2001:41d0:301:5::27|
|Repubblica Ceca|CZ|54.37.182.230|2001:41d0:301:6::27|
|Paesi Bassi|NL|54.36.41.83|2001:41d0:301:7::27|
|Finlandia|FI|188.165.140.194|2001:41d0:301:8::27|
|Lituania|LT|51.255.97.18|2001:41d0:301:9::27|
|Germania|DE|91.134.179.251|2001:41d0:301:1::27|
|Belgio|BE|193.70.58.226|2001:41d0:301:10::27|

Se il **Shared CDN** è attivo sul tuo hosting, devi utilizzare questo indirizzo IP:

```bash
46.105.204.27
```

Se hai bisogno dell’indirizzo IP del **gateway di uscita** del tuo hosting, è necessario utilizzare questo indirizzo IP:

```bash
54.37.121.239
```

### Cluster 028

Qui di seguito trovi gli indirizzi IP del **cluster** per ciascun Paese (per la geolocalizzazione):

|Paese|Codice Paese|IPv4|IPv6|
|---|---|----|---|
|Francia|FR|51.91.236.193|2001:41d0:301::28|
|Irlanda|IE|92.222.139.190|2001:41d0:301:3::28|
|Portogallo|PT|217.182.39.251|2001:41d0:301:2::28|
|Regno Unito|UK|193.70.71.149|2001:41d0:301:12::28|
|Italia|IT|51.255.117.202|2001:41d0:301:11::28|
|Spagna|ES|54.36.145.173|2001:41d0:301:4::28|
|Polonia|PL|213.32.10.111|2001:41d0:301:5::28|
|Repubblica Ceca|CZ|54.38.116.114|2001:41d0:301:6::28|
|Paesi Bassi|NL|176.31.23.191|2001:41d0:301:7::28|
|Finlandia|FI|51.255.135.35|2001:41d0:301:8::28|
|Lituania|LT|51.83.29.135|2001:41d0:301:9::28|
|Germania|DE|54.37.173.127|2001:41d0:301:1::28|
|Belgio|BE|193.70.70.144|2001:41d0:301:10::28|

Se il **Shared CDN** è attivo sul tuo hosting, devi utilizzare questo indirizzo IP:

```bash
46.105.204.28
```

Se hai bisogno dell’indirizzo IP del **gateway di uscita** del tuo hosting, è necessario utilizzare questo indirizzo IP:

```bash
91.134.248.249
```

### Cluster 029

Qui di seguito trovi gli indirizzi IP del **cluster** per ciascun Paese (per la geolocalizzazione):

|Paese|Codice Paese|IPv4|IPv6|
|---|---|----|---|
|Francia|FR|51.91.236.255|2001:41d0:301::29|
|Irlanda|IE|92.222.139.156|2001:41d0:301:3::29|
|Portogallo|PT|46.105.159.220|2001:41d0:301:2::29|
|Regno Unito|UK|178.32.48.109|2001:41d0:301:12::29|
|Italia|IT|178.32.137.139|2001:41d0:301:11::29|
|Spagna|ES|188.165.132.144|2001:41d0:301:4::29|
|Polonia|PL|213.32.10.205|2001:41d0:301:5::29|
|Repubblica Ceca|CZ|5.196.248.55|2001:41d0:301:6::29|
|Paesi Bassi|NL|51.83.124.4|2001:41d0:301:7::29|
|Finlandia|FI|79.137.116.129|2001:41d0:301:8::29|
|Lituania|LT|164.132.14.117|2001:41d0:301:9::29|
|Germania|DE|145.239.222.45|2001:41d0:301:1::29|
|Belgio|BE|178.32.44.140|2001:41d0:301:10::29|

Se il **Shared CDN** è attivo sul tuo hosting, devi utilizzare questo indirizzo IP:

```bash
46.105.204.29
```

Se hai bisogno dell’indirizzo IP del **gateway di uscita** del tuo hosting, è necessario utilizzare questo indirizzo IP:

```bash
91.134.248.192
```

### Cluster 030

Qui di seguito trovi gli indirizzi IP del **cluster** per ciascun Paese (per la geolocalizzazione):

|Paese|Codice Paese|IPv4|IPv6|
|---|---|----|---|
|Francia|FR|145.239.37.162|2001:41d0:301::30|
|Irlanda|IE|178.32.77.113|2001:41d0:301:3::30|
|Portogallo|PT|5.135.68.91|2001:41d0:301:2::30|
|Regno Unito|UK|91.134.177.228|2001:41d0:301:12::30|
|Italia|IT|94.23.73.16|2001:41d0:301:11::30|
|Spagna|ES|149.202.105.228|2001:41d0:301:4::30|
|Polonia|PL|188.165.21.8|2001:41d0:301:5::30|
|Repubblica Ceca|CZ|94.23.168.143|2001:41d0:301:6::30|
|Paesi Bassi|NL|149.202.25.75|2001:41d0:301:7::30|
|Finlandia|FI|188.165.140.151|2001:41d0:301:8::30|
|Lituania|LT|188.165.24.146|2001:41d0:301:9::30|
|Germania|DE|51.255.232.79|2001:41d0:301:1::30|
|Belgio|BE|213.32.107.241|2001:41d0:301:10::30|

Se il **Shared CDN** è attivo sul tuo hosting, devi utilizzare questo indirizzo IP:

```bash
46.105.204.30
```

Se hai bisogno dell’indirizzo IP del **gateway di uscita** del tuo hosting, è necessario utilizzare questo indirizzo IP:

```bash
51.178.146.199
```

### Cluster 031

Qui di seguito trovi gli indirizzi IP del **cluster** per ciascun Paese (per la geolocalizzazione):

|Paese|Codice Paese|IPv4|IPv6|
|---|---|----|---|
|Francia|FR|146.59.209.152|2001:41d0:301::31|
|Irlanda|IE|188.165.5.107|2001:41d0:301:3::31|
|Portogallo|PT|51.178.229.47|2001:41d0:301:2::31|
|Regno Unito|UK|178.32.52.177|2001:41d0:301:12::31|
|Italia|IT|94.23.66.84|2001:41d0:301:11::31|
|Spagna|ES|51.255.26.63|2001:41d0:301:4::31|
|Polonia|PL|87.98.236.253|2001:41d0:301:5::31|
|Repubblica Ceca|CZ|217.182.52.81|2001:41d0:301:6::31|
|Paesi Bassi|NL|213.32.108.83|2001:41d0:301:7::31|
|Finlandia|FI|178.32.10.72|2001:41d0:301:8::31|
|Lituania|LT|188.165.30.182|2001:41d0:301:9::31|
|Germania|DE|151.80.4.219|2001:41d0:301:1::31|
|Belgio|BE|217.182.187.17|2001:41d0:301:10::31|

Se il **Shared CDN** è attivo sul tuo hosting, devi utilizzare questo indirizzo IP:

```bash
46.105.204.31
```

Se hai bisogno dell’indirizzo IP del **gateway di uscita** del tuo hosting, è necessario utilizzare questo indirizzo IP:

```bash
141.94.87.67
```

### Cluster 051

Qui di seguito trovi gli indirizzi IP del **cluster** per ciascun Paese (per la geolocalizzazione):

|Paese|Codice Paese|IPv4|IPv6|
|---|---|----|---|
|Canada|CA|51.161.122.78|2607:5300:202:0:0::51|

Se il **Shared CDN** è attivo sul tuo hosting, devi utilizzare questo indirizzo IP:

```bash
46.105.204.51
```

Se hai bisogno dell’indirizzo IP del **gateway di uscita** del tuo hosting, è necessario utilizzare questo indirizzo IP:

```bash
51.161.94.36
```

### Cluster 100

Qui di seguito trovi gli indirizzi IP del **cluster** per ciascun Paese (per la geolocalizzazione):

|Paese|Codice Paese|IPv4|IPv6|
|---|---|----|---|
|Francia|FR|5.135.23.164|2001:41d0:301::100|
|Irlanda|IE|188.165.0.143|2001:41d0:301:3::100|
|Portogallo|PT|94.23.76.76|2001:41d0:301:2::100|
|Regno Unito|UK|87.98.254.187|2001:41d0:301:12::100|
|Italia|IT|178.32.143.165|2001:41d0:301:11::100|
|Spagna|ES|178.33.119.211|2001:41d0:301:4::100|
|Polonia|PL|94.23.89.116|2001:41d0:301:5::100|
|Repubblica Ceca|CZ|94.23.172.226|2001:41d0:301:6::100|
|Paesi Bassi|NL|94.23.146.244|2001:41d0:301:7::100|
|Finlandia|FI|188.165.137.37|2001:41d0:301:8::100|
|Lituania|LT|188.165.26.152|2001:41d0:301:9::100|
|Germania|DE|87.98.243.177|2001:41d0:301:1::100|
|Belgio|BE|91.121.217.51|2001:41d0:301:10::100|

Se il **Shared CDN** è attivo sul tuo hosting, devi utilizzare questo indirizzo IP:

```bash
46.105.204.100
```

Se hai bisogno dell’indirizzo IP del **gateway di uscita** del tuo hosting, è necessario utilizzare questo indirizzo IP:

```bash
54.36.142.130
```

## Per saperne di più

[Installare un multisito sul tuo hosting Web](/pages/web_cloud/web_hosting/multisites_configure_multisite) 

[Attiva l'HTTPS con il tuo certificato SSL sul tuo hosting Web](/pages/web_cloud/web_hosting/ssl-activate-https-website)

[Ottimizza le performance del tuo sito Web](/pages/web_cloud/web_hosting/optimise_your_website_performance)

Per prestazioni specializzate (referenziamento, sviluppo, ecc...), contatta i [partner OVHcloud](/links/partner).
 
Per usufruire di un supporto per l'utilizzo e la configurazione delle soluzioni OVHcloud, è possibile consultare le nostre soluzioni [offerte di supporto](/links/support).
 
Contatta la nostra [Community di utenti](/links/community).