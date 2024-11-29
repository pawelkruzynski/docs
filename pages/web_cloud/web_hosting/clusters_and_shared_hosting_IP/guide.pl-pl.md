---
title: "Lista adresów IP klastrów i hostingów WWW"
excerpt: "Poznaj wszystkie dostępne adresy IP dostępne na naszych hostingach"
updated: 2024-02-28
---

## Wprowadzenie 

W tym przewodniku znajdziesz wszystkie adresy IP hostingów WWW OVHcloud. Dzięki temu dowiesz się na przykład, jaki adres IP wpisać w strefach DNS w zależności od elementów takich jak:

- klaster,
- opcje (CDN, płatny certyfikat SSL, darmowy certyfikat SSL itp.),
- szukany kraj.

**Poznaj wszystkie dostępne adresy IP dostępne na naszych hostingach.**

> [!primary]
>
> Adresy IP opcji CDN są typu „Anycast”.
> Oznacza to, że nie potrzebują geolokalizacji ([więcej informacji znajdziesz tutaj](/links/web/hosting-options-cdn)).
> 

## Wymagania początkowe

- Zakupienie [hostingu OVHcloud](/links/web/hosting){.external}.
- Dostęp do [Panelu klienta OVHcloud](/links/manager){.external}.

## W praktyce

Aby poznać klaster hostingu, w którym hostowana jest Twoja usługa, zaloguj się do [Panelu klienta OVHcloud](/links/manager) wybierz `Web Cloud`{.action}. Kliknij `Hosting`{.action} po czym wybierz odpowiedni hosting. Następnie przejdź do zakładki `FTP - SSH`{.action}.
Na tej stronie możesz sprawdzić numer klastra hostingu WWW, używając **Serwer FTP**.

### Klaster 002

Tutaj znajdziesz adresy IP **klastra** według kraju (w przypadku geolokalizacji):

|Kraj|Kod kraju|IPv4|IPv6|
|---|---|----|---|
|Francja|FR|213.186.33.2|2001:41d0:1:1b00:213:186:33:2|
|Irlandia|IE|188.165.7.2|2001:41d0:1:1b00:188:165:7:2|
|Portugalia|PT|94.23.79.2|2001:41d0:1:1b00:94:23:79:2|
|Wielka Brytania|UK|87.98.255.2|2001:41d0:1:1b00:87:98:255:2|
|Włochy|IT|94.23.64.2|2001:41d0:1:1b00:94:23:64:2|
|Hiszpania|ES|87.98.231.2|2001:41d0:1:1b00:87:98:231:2|
|Polska|PL|87.98.239.2|2001:41d0:1:1b00:87:98:239:2|
|Czechy|CZ|94.23.175.2|2001:41d0:1:1b00:94:23:175:2|
|Niderlandy|NL|94.23.151.2|2001:41d0:1:1b00:94:23:151:2|
|Finlandia|FI|188.165.143.2|2001:41d0:1:1b00:188:165:143:2|
|Litwa|LT|188.165.31.2|2001:41d0:1:1b00:188:165:31:2|
|Niemcy|DE|87.98.247.2|2001:41d0:1:1b00:87:98:247:2|

Jeśli **Shared CDN** jest aktywny na Twoim hostingu, użyj tego adresu IP:

```bash
46.105.204.2
```

Jeśli potrzebujesz adresu IP **bramy wyjściowej** hostingu (gateway), użyj poniższego adresu IP:

```bash
51.68.11.191
```

### Klaster 003

Tutaj znajdziesz adresy IP **klastra** według kraju (w przypadku geolokalizacji):

|Kraj|Kod kraju|IPv4|IPv6|
|---|---|----|---|
|Francja|FR|213.186.33.4|2001:41d0:1:1b00:213:186:33:4|
|Irlandia|IE|188.165.7.4|2001:41d0:1:1b00:188:165:7:4|
|Portugalia|PT|94.23.79.4|2001:41d0:1:1b00:94:23:79:4|
|Wielka Brytania|UK|87.98.255.4|2001:41d0:1:1b00:87:98:255:4|
|Włochy|IT|94.23.64.4|2001:41d0:1:1b00:94:23:64:4|
|Hiszpania|ES|87.98.231.4|2001:41d0:1:1b00:87:98:231:4|
|Polska|PL|87.98.239.4|2001:41d0:1:1b00:87:98:239:4|
|Czechy|CZ|94.23.175.4|2001:41d0:1:1b00:94:23:175:4|
|Niderlandy|NL|94.23.151.4|2001:41d0:1:1b00:94:23:151:4|
|Finlandia|FI|188.165.143.4|2001:41d0:1:1b00:188:165:143:4|
|Litwa|LT|188.165.31.4|2001:41d0:1:1b00:188:165:31:4|
|Niemcy|DE|87.98.247.4|2001:41d0:1:1b00:87:98:247:4|

Jeśli **Shared CDN** jest aktywny na Twoim hostingu, użyj tego adresu IP:

```bash
46.105.204.3
```

Jeśli potrzebujesz adresu IP **bramy wyjściowej** hostingu (gateway), użyj poniższego adresu IP:

```bash
51.68.11.195
```

### Klaster 005

Tutaj znajdziesz adresy IP **klastra** według kraju (w przypadku geolokalizacji):

|Kraj|Kod kraju|IPv4|IPv6|
|---|---|----|---|
|Francja|FR|213.186.33.16|2001:41d0:1:1b00:213:186:33:16|
|Irlandia|IE|188.165.7.16|2001:41d0:1:1b00:188:165:7:16|
|Portugalia|PT|94.23.79.16|2001:41d0:1:1b00:94:23:79:16|
|Wielka Brytania|UK|87.98.255.16|2001:41d0:1:1b00:87:98:255:16|
|Włochy|IT|94.23.64.16|2001:41d0:1:1b00:94:23:64:16|
|Hiszpania|ES|87.98.231.16|2001:41d0:1:1b00:87:98:231:16|
|Polska|PL|87.98.239.16|2001:41d0:1:1b00:87:98:239:16|
|Czechy|CZ|94.23.175.16|2001:41d0:1:1b00:94:23:175:16|
|Niderlandy|NL|94.23.151.16|2001:41d0:1:1b00:94:23:151:16|
|Finlandia|FI|188.165.143.16|2001:41d0:1:1b00:188:165:143:16|
|Litwa|LT|188.165.31.16|2001:41d0:1:1b00:188.165.31.16|
|Niemcy|DE|87.98.247.16|2001:41d0:1:1b00:87:98:247:16|

Jeśli **Shared CDN** jest aktywny na Twoim hostingu, użyj tego adresu IP:

```bash
46.105.204.5
```

Jeśli potrzebujesz adresu IP **bramy wyjściowej** hostingu (gateway), użyj poniższego adresu IP:

```bash
51.68.11.199
```

### Klaster 006

Tutaj znajdziesz adresy IP **klastra** według kraju (w przypadku geolokalizacji):

|Kraj|Kod kraju|IPv4|IPv6|
|---|---|----|---|
|Francja|FR|213.186.33.17|2001:41d0:1:1b00:213:186:33:17|
|Irlandia|IE|188.165.7.17|2001:41d0:1:1b00:188:165:7:17|
|Portugalia|PT|94.23.79.17|2001:41d0:1:1b00:94:23:79:17|
|Wielka Brytania|UK|87.98.255.17|2001:41d0:1:1b00:87:98:255:17|
|Włochy|IT|94.23.64.17|2001:41d0:1:1b00:94:23:64:17|
|Hiszpania|ES|87.98.231.17|2001:41d0:1:1b00:87:98:231:17|
|Polska|PL|87.98.239.17|2001:41d0:1:1b00:87:98:239:17|
|Czechy|CZ|94.23.175.17|2001:41d0:1:1b00:94:23:175:17|
|Niderlandy|NL|94.23.151.17|2001:41d0:1:1b00:94:23:151:17|
|Finlandia|FI|188.165.143.17|2001:41d0:1:1b00:188:165:143:17|
|Litwa|LT|188.165.31.17|2001:41d0:1:1b00:188:165:31:17|
|Niemcy|DE|87.98.247.17|2001:41d0:1:1b00:87:98:247:17|

Jeśli **Shared CDN** jest aktywny na Twoim hostingu, użyj tego adresu IP:

```bash
46.105.204.6
```

Jeśli potrzebujesz adresu IP **bramy wyjściowej** hostingu (gateway), użyj poniższego adresu IP:

```bash
51.68.11.203
```

### Klaster 007

Tutaj znajdziesz adresy IP **klastra** według kraju (w przypadku geolokalizacji):

|Kraj|Kod kraju|IPv4|IPv6|
|---|---|----|---|
|Francja|FR|213.186.33.18|2001:41d0:1:1b00:213:186:33:18|
|Irlandia|IE|188.165.7.18|2001:41d0:1:1b00:188:165:7:18|
|Portugalia|PT|94.23.79.18|2001:41d0:1:1b00:94:23:79:18|
|Wielka Brytania|UK|87.98.255.18|2001:41d0:1:1b00:87:98:255:18|
|Włochy|IT|94.23.64.18|2001:41d0:1:1b00:94:23:64:18|
|Hiszpania|ES|87.98.231.18|2001:41d0:1:1b00:87:98:231:18|
|Polska|PL|87.98.239.18|2001:41d0:1:1b00:87:98:239:18|
|Czechy|CZ|94.23.175.18|2001:41d0:1:1b00:94:23:175:18|
|Niderlandy|NL|94.23.151.18|2001:41d0:1:1b00:94:23:151:18|
|Finlandia|FI|188.165.143.18|2001:41d0:1:1b00:188:165:143:18|
|Litwa|LT|188.165.31.18|2001:41d0:1:1b00:188:165:31:18|
|Niemcy|DE|87.98.247.18|2001:41d0:1:1b00:87:98:247:18|

Jeśli **Shared CDN** jest aktywny na Twoim hostingu, użyj tego adresu IP:

```bash
46.105.204.7
```

Jeśli potrzebujesz adresu IP **bramy wyjściowej** hostingu (gateway), użyj poniższego adresu IP:

```bash
51.68.11.207
```

### Klaster 010

Tutaj znajdziesz adresy IP **klastra** według kraju (w przypadku geolokalizacji):

|Kraj|Kod kraju|IPv4|IPv6|
|---|---|----|---|
|Francja|FR|213.186.33.19|2001:41d0:1:1b00:213:186:33:19|
|Irlandia|IE|188.165.7.19|2001:41d0:1:1b00:188:165:7:19|
|Portugalia|PT|94.23.79.19|2001:41d0:1:1b00:94:23:79:19|
|Wielka Brytania|UK|87.98.255.19|2001:41d0:1:1b00:87:98:255:19|
|Włochy|IT|94.23.64.19|2001:41d0:1:1b00:94:23:64:19|
|Hiszpania|ES|87.98.231.19|2001:41d0:1:1b00:87:98:231:19|
|Polska|PL|87.98.239.19|2001:41d0:1:1b00:87:98:239:19|
|Czechy|CZ|94.23.175.19|2001:41d0:1:1b00:94:23:175:19|
|Niderlandy|NL|94.23.151.19|2001:41d0:1:1b00:94:23:151:19|
|Finlandia|FI|188.165.143.19|2001:41d0:1:1b00:188:165:143:19|
|Litwa|LT|188.165.31.19|2001:41d0:1:1b00:188:165:31:19|
|Niemcy|DE|87.98.247.19|2001:41d0:1:1b00:87:98:247:19|

Jeśli **Shared CDN** jest aktywny na Twoim hostingu, użyj tego adresu IP:

```bash
46.105.204.10
```

Jeśli potrzebujesz adresu IP **bramy wyjściowej** hostingu (gateway), użyj poniższego adresu IP:

```bash
51.68.11.211
```

### Klaster 011

Tutaj znajdziesz adresy IP **klastra** według kraju (w przypadku geolokalizacji):

|Kraj|Kod kraju|IPv4|IPv6|
|---|---|----|---|
|Francja|FR|213.186.33.40|2001:41d0:1:1b00:213:186:33:40|
|Irlandia|IE|188.165.7.40|2001:41d0:1:1b00:188:165:7:40|
|Portugalia|PT|94.23.79.40|2001:41d0:1:1b00:94:23:79:40|
|Wielka Brytania|UK|87.98.255.40|2001:41d0:1:1b00:87:98:255:40|
|Włochy|IT|94.23.64.40|2001:41d0:1:1b00:94:23:64:40|
|Hiszpania|ES|87.98.231.40|2001:41d0:1:1b00:87:98:231:40|
|Polska|PL|87.98.239.40|2001:41d0:1:1b00:87:98:239:40|
|Czechy|CZ|94.23.175.40|2001:41d0:1:1b00:94:23:175:40|
|Niderlandy|NL|94.23.151.40|2001:41d0:1:1b00:94:23:151:40|
|Finlandia|FI|188.165.143.40|2001:41d0:1:1b00:188:165:143:40|
|Litwa|LT|188.165.31.40|2001:41d0:1:1b00:188:165:31:40|
|Niemcy|DE|87.98.247.40|2001:41d0:1:1b00:87:98:247:40|

Jeśli **Shared CDN** jest aktywny na Twoim hostingu, użyj tego adresu IP:

```bash
46.105.204.11
```

Jeśli potrzebujesz adresu IP **bramy wyjściowej** hostingu (gateway), użyj poniższego adresu IP:

```bash
51.68.11.215
```

### Klaster 012

Tutaj znajdziesz adresy IP **klastra** według kraju (w przypadku geolokalizacji):

|Kraj|Kod kraju|IPv4|IPv6|
|---|---|----|---|
|Francja|FR|213.186.33.48|2001:41d0:1:1b00:213:186:33:48|
|Irlandia|IE|188.165.7.48|2001:41d0:1:1b00:188:165:7:48|
|Portugalia|PT|94.23.79.48|2001:41d0:1:1b00:94:23:79:48|
|Wielka Brytania|UK|87.98.255.48|2001:41d0:1:1b00:87:98:255:48|
|Włochy|IT|94.23.64.48|2001:41d0:1:1b00:94:23:64:48|
|Hiszpania|ES|87.98.231.48|2001:41d0:1:1b00:87:98:231:48|
|Polska|PL|87.98.239.48|2001:41d0:1:1b00:87:98:239:48|
|Czechy|CZ|94.23.175.48|2001:41d0:1:1b00:94:23:175:48|
|Niderlandy|NL|94.23.151.48|2001:41d0:1:1b00:94:23:151:48|
|Finlandia|FI|188.165.143.48|2001:41d0:1:1b00:188:165:143:48|
|Litwa|LT|188.165.31.48|2001:41d0:1:1b00:188:165:31:48|
|Niemcy|DE|87.98.247.48|2001:41d0:1:1b00:87:98:247:48|

Jeśli **Shared CDN** jest aktywny na Twoim hostingu, użyj tego adresu IP:

```bash
46.105.204.12
```

Jeśli potrzebujesz adresu IP **bramy wyjściowej** hostingu (gateway), użyj poniższego adresu IP:

```bash
51.68.11.219
```

### Klaster 013

Tutaj znajdziesz adresy IP **klastra** według kraju (w przypadku geolokalizacji):

|Kraj|Kod kraju|IPv4|IPv6|
|---|---|----|---|
|Francja|FR|213.186.33.24|2001:41d0:1:1b00:213:186:33:24|
|Irlandia|IE|188.165.7.24|2001:41d0:1:1b00:188:165:7:24|
|Portugalia|PT|94.23.79.24|2001:41d0:1:1b00:94:23:79:24|
|Wielka Brytania|UK|87.98.255.24|2001:41d0:1:1b00:87:98:255:24|
|Włochy|IT|94.23.64.24|2001:41d0:1:1b00:94:23:64:24|
|Hiszpania|ES|87.98.231.24|2001:41d0:1:1b00:87:98:231:24|
|Polska|PL|87.98.239.24|2001:41d0:1:1b00:87:98:239:24|
|Czechy|CZ|94.23.175.24|2001:41d0:1:1b00:94:23:175:24|
|Niderlandy|NL|94.23.151.24|2001:41d0:1:1b00:94:23:151:24|
|Finlandia|FI|188.165.143.24|2001:41d0:1:1b00:188:165:143:24|
|Litwa|LT|188.165.31.24|2001:41d0:1:1b00:188:165:31:24|
|Niemcy|DE|87.98.247.24|2001:41d0:1:1b00:87:98:247:24|

Jeśli **Shared CDN** jest aktywny na Twoim hostingu, użyj tego adresu IP:

```bash
46.105.204.13
```

Jeśli potrzebujesz adresu IP **bramy wyjściowej** hostingu (gateway), użyj poniższego adresu IP:

```bash
51.68.11.223
```

### Klaster 014

Tutaj znajdziesz adresy IP **klastra** według kraju (w przypadku geolokalizacji):

|Kraj|Kod kraju|IPv4|IPv6|
|---|---|----|---|
|Francja|FR|213.186.33.87|2001:41d0:1:1b00:213:186:33:87|
|Irlandia|IE|188.165.7.87|2001:41d0:1:1b00:188:165:7:87|
|Portugalia|PT|94.23.79.87|2001:41d0:1:1b00:94:23:79:87|
|Wielka Brytania|UK|87.98.255.87|2001:41d0:1:1b00:87:98:255:87|
|Włochy|IT|94.23.64.87|2001:41d0:1:1b00:94:23:64:87|
|Hiszpania|ES|87.98.231.87|2001:41d0:1:1b00:87:98:231:87|
|Polska|PL|87.98.239.87|2001:41d0:1:1b00:87:98:239:87|
|Czechy|CZ|94.23.175.87|2001:41d0:1:1b00:94:23:175:87|
|Niderlandy|NL|94.23.151.87|2001:41d0:1:1b00:94:23:151:87|
|Finlandia|FI|188.165.143.87|2001:41d0:1:1b00:188:165:143:87|
|Litwa|LT|188.165.31.87|2001:41d0:1:1b00:188:165:31:87|
|Niemcy|DE|87.98.247.87|2001:41d0:1:1b00:87:98:247:87|

Jeśli **Shared CDN** jest aktywny na Twoim hostingu, użyj tego adresu IP:

```bash
46.105.204.14
```

Jeśli potrzebujesz adresu IP **bramy wyjściowej** hostingu (gateway), użyj poniższego adresu IP:

```bash
51.68.11.227
```

### Klaster 015

Tutaj znajdziesz adresy IP **klastra** według kraju (w przypadku geolokalizacji):

|Kraj|Kod kraju|IPv4|IPv6|
|---|---|----|---|
|Francja|FR|213.186.33.3|2001:41d0:1:1b00:213:186:33:3|
|Irlandia|IE|188.165.7.3|2001:41d0:1:1b00:188:165:7:3|
|Portugalia|PT|94.23.79.3|2001:41d0:1:1b00:94:23:79:3|
|Wielka Brytania|UK|87.98.255.3|2001:41d0:1:1b00:87:98:255:3|
|Włochy|IT|94.23.64.3|2001:41d0:1:1b00:94:23:64:3|
|Hiszpania|ES|87.98.231.3|2001:41d0:1:1b00:87:98:231:3|
|Polska|PL|87.98.239.3|2001:41d0:1:1b00:87:98:239:3|
|Czechy|CZ|94.23.175.3|2001:41d0:1:1b00:94:23:175:3|
|Niderlandy|NL|94.23.151.3|2001:41d0:1:1b00:94:23:151:3|
|Finlandia|FI|188.165.143.3|2001:41d0:1:1b00:188:165:143:3|
|Litwa|LT|188.165.31.3|2001:41d0:1:1b00:188:165:31:3|
|Niemcy|DE|87.98.247.3|2001:41d0:1:1b00:87:98:247:3|

Jeśli **Shared CDN** jest aktywny na Twoim hostingu, użyj tego adresu IP:

```bash
46.105.204.15
```

Jeśli potrzebujesz adresu IP **bramy wyjściowej** hostingu (gateway), użyj poniższego adresu IP:

```bash
51.68.11.231
```

### Klaster 017

Tutaj znajdziesz adresy IP **klastra** według kraju (w przypadku geolokalizacji):

|Kraj|Kod kraju|IPv4|IPv6|
|---|---|----|---|
|Francja|FR|213.186.33.50|2001:41d0:1:1b00:213:186:33:50|
|Irlandia|IE|188.165.7.50|2001:41d0:1:1b00:188:165:7:50|
|Portugalia|PT|94.23.79.50|2001:41d0:1:1b00:94:23:79:50|
|Wielka Brytania|UK|87.98.255.50|2001:41d0:1:1b00:87:98:255:50|
|Włochy|IT|94.23.64.50|2001:41d0:1:1b00:94:23:64:50|
|Hiszpania|ES|87.98.231.50|2001:41d0:1:1b00:87:98:231:50|
|Polska|PL|87.98.239.50|2001:41d0:1:1b00:87:98:239:50|
|Czechy|CZ|94.23.175.50|2001:41d0:1:1b00:94:23:175:50|
|Niderlandy|NL|94.23.151.50|2001:41d0:1:1b00:94:23:151:50|
|Finlandia|FI|188.165.143.50|2001:41d0:1:1b00:188:165:143:50|
|Litwa|LT|188.165.31.50|2001:41d0:1:1b00:188:165:31:50|
|Niemcy|DE|87.98.247.50|2001:41d0:1:1b00:87:98:247:50|

Jeśli **Shared CDN** jest aktywny na Twoim hostingu, użyj tego adresu IP:

```bash
46.105.204.17
```

Jeśli potrzebujesz adresu IP **bramy wyjściowej** hostingu (gateway), użyj poniższego adresu IP:

```bash
51.68.11.239
```

### Klaster 020

Tutaj znajdziesz adresy IP **klastra** według kraju (w przypadku geolokalizacji):

|Kraj|Kod kraju|IPv4|IPv6|
|---|---|----|---|
|Francja|FR|46.105.57.169|2001:41d0:301::20|
|Irlandia|IE|51.254.78.227|2001:41d0:301:3::20|
|Portugalia|PT|5.135.59.60|2001:41d0:301:2::20|
|Wielka Brytania|UK|51.254.94.183|2001:41d0:301:12::20|
|Włochy|IT|37.59.236.156|2001:41d0:301:11::20|
|Hiszpania|ES|37.59.203.111|2001:41d0:301:4::20|
|Polska|PL|178.32.149.185|2001:41d0:301:5::20|
|Czechy|CZ|51.254.181.43|2001:41d0:301:6::20|
|Niderlandy|NL|37.59.164.205|2001:41d0:301:7::20|
|Finlandia|FI|5.196.208.117|2001:41d0:301:8::20|
|Litwa|LT|5.196.129.52|2001:41d0:301:9::20|
|Niemcy|DE|5.135.108.219|2001:41d0:301:1::20|
|Belgia|BE|5.196.203.200|2001:41d0:301:10::20|

Jeśli **Shared CDN** jest aktywny na Twoim hostingu, użyj tego adresu IP:

```bash
46.105.204.20
```

Jeśli potrzebujesz adresu IP **bramy wyjściowej** hostingu (gateway), użyj poniższego adresu IP:

```bash
91.134.248.253
```

### Klaster 021

Tutaj znajdziesz adresy IP **klastra** według kraju (w przypadku geolokalizacji):

|Kraj|Kod kraju|IPv4|IPv6|
|---|---|----|---|
|Francja|FR|188.165.53.185|2001:41d0:301::21|
|Irlandia|IE|188.165.6.20|2001:41d0:301:6::21|
|Portugalia|PT|94.23.75.235|2001:41d0:301:2::21|
|Wielka Brytania|UK|94.23.152.220|2001:41d0:301:12::21|
|Włochy|IT|94.23.69.227|2001:41d0:301:11::21|
|Hiszpania|ES|87.98.230.241|2001:41d0:301:4::21|
|Polska|PL|188.165.23.19|2001:41d0:301:5::21|
|Czechy|CZ|94.23.173.184|2001:41d0:301:6::21|
|Niderlandy|NL|94.23.144.60|2001:41d0:301:7::21|
|Finlandia|FI|188.165.139.219|2001:41d0:301:8::21|
|Litwa|LT|188.165.30.41|2001:41d0:301:9::21|
|Niemcy|DE|94.23.162.9|2001:41d0:301:1::21|
|Belgia|BE|178.32.40.72|2001:41d0:301:10::21|

Jeśli **Shared CDN** jest aktywny na Twoim hostingu, użyj tego adresu IP:

```bash
46.105.204.21
```

Jeśli potrzebujesz adresu IP **bramy wyjściowej** hostingu (gateway), użyj poniższego adresu IP:

```bash
91.134.248.245
```

### Klaster 023

Tutaj znajdziesz adresy IP **klastra** według kraju (w przypadku geolokalizacji):

|Kraj|Kod kraju|IPv4|IPv6|
|---|---|----|---|
|Francja|FR|164.132.235.17|2001:41d0:301::23|
|Irlandia|IE|79.137.112.24|2001:41d0:301:3::23|
|Portugalia|PT|5.135.68.66|2001:41d0:301:2::23|
|Wielka Brytania|UK|178.32.59.150|2001:41d0:301:12::23|
|Włochy|IT|178.32.140.171|2001:41d0:301:11::23|
|Hiszpania|ES|51.254.16.36|2001:41d0:301:4::23|
|Polska|PL|87.98.235.184|2001:41d0:301:5::23|
|Czechy|CZ|94.23.169.83|2001:41d0:301:6::23|
|Niderlandy|NL|94.23.148.187|2001:41d0:301:7::23|
|Finlandia|FI|178.32.17.246|2001:41d0:301:8::23|
|Litwa|LT|37.59.69.122|2001:41d0:301:9::23|
|Niemcy|DE|87.98.242.65|2001:41d0:301:1::23|
|Belgia|BE|137.74.229.68|2001:41d0:301:10::23|

Jeśli **Shared CDN** jest aktywny na Twoim hostingu, użyj tego adresu IP:

```bash
46.105.204.23
```

Jeśli potrzebujesz adresu IP **bramy wyjściowej** hostingu (gateway), użyj poniższego adresu IP:

```bash
91.134.248.235
```

### Klaster 024

Tutaj znajdziesz adresy IP **klastra** według kraju (w przypadku geolokalizacji):

|Kraj|Kod kraju|IPv4|IPv6|
|---|---|----|---|
|Francja|FR|188.165.61.82|2001:41d0:301::24|
|Irlandia|IE|188.165.6.81|2001:41d0:301:3::24|
|Portugalia|PT|5.135.68.67|2001:41d0:301:2::24|
|Wielka Brytania|UK|178.32.59.194|2001:41d0:301:12::24|
|Włochy|IT|178.32.140.172|2001:41d0:301:11::24|
|Hiszpania|ES|51.255.132.41|2001:41d0:301:4::24|
|Polska|PL|94.23.88.105|2001:41d0:301:5::24|
|Czechy|CZ|94.23.169.75|2001:41d0:301:6::24|
|Niderlandy|NL|94.23.149.14|2001:41d0:301:7::24|
|Finlandia|FI|188.165.138.2|2001:41d0:301:8::24|
|Litwa|LT|164.132.150.73|2001:41d0:301:9::24|
|Niemcy|DE|178.33.38.88|2001:41d0:301:1::24|
|Belgia|BE|213.32.81.103|2001:41d0:301:10::24|

Jeśli **Shared CDN** jest aktywny na Twoim hostingu, użyj tego adresu IP:

```bash
46.105.204.24
```

Jeśli potrzebujesz adresu IP **bramy wyjściowej** hostingu (gateway), użyj poniższego adresu IP:

```bash
91.134.248.230
```

### Klaster 026

Tutaj znajdziesz adresy IP **klastra** według kraju (w przypadku geolokalizacji):

|Kraj|Kod kraju|IPv4|IPv6|
|---|---|----|---|
|Francja|FR|87.98.154.146|2001:41d0:301::26|
|Irlandia|IE|188.165.4.35|2001:41d0:301:3::26|
|Portugalia|PT|51.254.64.107|2001:41d0:301:2::26|
|Wielka Brytania|UK|91.134.201.112|2001:41d0:301:12::26|
|Włochy|IT|94.23.66.212|2001:41d0:301:11::26|
|Hiszpania|ES|188.165.129.145|2001:41d0:301:4::26|
|Polska|PL|178.32.205.96|2001:41d0:301:5::26|
|Czechy|CZ|137.74.234.211|2001:41d0:301:6::26|
|Niderlandy|NL|137.74.180.117|2001:41d0:301:7::26|
|Finlandia|FI|137.74.48.119|2001:41d0:301:8::26|
|Litwa|LT|188.165.29.126|2001:41d0:301:9::26|
|Niemcy|DE|94.23.160.29|2001:41d0:301:1::26|
|Belgia|BE|178.32.43.46|2001:41d0:301:10::26|

Jeśli **Shared CDN** jest aktywny na Twoim hostingu, użyj tego adresu IP:

```bash
46.105.204.26
```

Jeśli potrzebujesz adresu IP **bramy wyjściowej** hostingu (gateway), użyj poniższego adresu IP:

```bash
91.134.248.211
```

### Klaster 027

Tutaj znajdziesz adresy IP **klastra** według kraju (w przypadku geolokalizacji):

|Kraj|Kod kraju|IPv4|IPv6|
|---|---|----|---|
|Francja|FR|54.36.91.62|2001:41d0:301::27|
|Irlandia|IE|54.36.31.145|2001:41d0:301:3::27|
|Portugalia|PT|193.70.24.82|2001:41d0:301:2::27|
|Wielka Brytania|UK|54.36.203.165|2001:41d0:301:12::27|
|Włochy|IT|178.32.138.212|2001:41d0:301:11::27|
|Hiszpania|ES|213.32.37.233|2001:41d0:301:4::27|
|Polska|PL|178.32.203.125|2001:41d0:301:5::27|
|Czechy|CZ|54.37.182.230|2001:41d0:301:6::27|
|Niderlandy|NL|54.36.41.83|2001:41d0:301:7::27|
|Finlandia|FI|188.165.140.194|2001:41d0:301:8::27|
|Litwa|LT|51.255.97.18|2001:41d0:301:9::27|
|Niemcy|DE|91.134.179.251|2001:41d0:301:1::27|
|Belgia|BE|193.70.58.226|2001:41d0:301:10::27|

Jeśli **Shared CDN** jest aktywny na Twoim hostingu, użyj tego adresu IP:

```bash
46.105.204.27
```

Jeśli potrzebujesz adresu IP **bramy wyjściowej** hostingu (gateway), użyj poniższego adresu IP:

```bash
54.37.121.239
```

### Klaster 028

Tutaj znajdziesz adresy IP **klastra** według kraju (w przypadku geolokalizacji):

|Kraj|Kod kraju|IPv4|IPv6|
|---|---|----|---|
|Francja|FR|51.91.236.193|2001:41d0:301::28|
|Irlandia|IE|92.222.139.190|2001:41d0:301:3::28|
|Portugalia|PT|217.182.39.251|2001:41d0:301:2::28|
|Wielka Brytania|UK|193.70.71.149|2001:41d0:301:12::28|
|Włochy|IT|51.255.117.202|2001:41d0:301:11::28|
|Hiszpania|ES|54.36.145.173|2001:41d0:301:4::28|
|Polska|PL|213.32.10.111|2001:41d0:301:5::28|
|Czechy|CZ|54.38.116.114|2001:41d0:301:6::28|
|Niderlandy|NL|176.31.23.191|2001:41d0:301:7::28|
|Finlandia|FI|51.255.135.35|2001:41d0:301:8::28|
|Litwa|LT|51.83.29.135|2001:41d0:301:9::28|
|Niemcy|DE|54.37.173.127|2001:41d0:301:1::28|
|Belgia|BE|193.70.70.144|2001:41d0:301:10::28|

Jeśli **Shared CDN** jest aktywny na Twoim hostingu, użyj tego adresu IP:

```bash
46.105.204.28
```

Jeśli potrzebujesz adresu IP **bramy wyjściowej** hostingu (gateway), użyj poniższego adresu IP:

```bash
91.134.248.249
```

### Klaster 029

Tutaj znajdziesz adresy IP **klastra** według kraju (w przypadku geolokalizacji):

|Kraj|Kod kraju|IPv4|IPv6|
|---|---|----|---|
|Francja|FR|51.91.236.255|2001:41d0:301::29|
|Irlandia|IE|92.222.139.156|2001:41d0:301:3::29|
|Portugalia|PT|46.105.159.220|2001:41d0:301:2::29|
|Wielka Brytania|UK|178.32.48.109|2001:41d0:301:12::29|
|Włochy|IT|178.32.137.139|2001:41d0:301:11::29|
|Hiszpania|ES|188.165.132.144|2001:41d0:301:4::29|
|Polska|PL|213.32.10.205|2001:41d0:301:5::29|
|Czechy|CZ|5.196.248.55|2001:41d0:301:6::29|
|Niderlandy|NL|51.83.124.4|2001:41d0:301:7::29|
|Finlandia|FI|79.137.116.129|2001:41d0:301:8::29|
|Litwa|LT|164.132.14.117|2001:41d0:301:9::29|
|Niemcy|DE|145.239.222.45|2001:41d0:301:1::29|
|Belgia|BE|178.32.44.140|2001:41d0:301:10::29|

Jeśli **Shared CDN** jest aktywny na Twoim hostingu, użyj tego adresu IP:

```bash
46.105.204.29
```

Jeśli potrzebujesz adresu IP **bramy wyjściowej** hostingu (gateway), użyj poniższego adresu IP:

```bash
91.134.248.192
```

### Klaster 030

Tutaj znajdziesz adresy IP **klastra** według kraju (w przypadku geolokalizacji):

|Kraj|Kod kraju|IPv4|IPv6|
|---|---|----|---|
|Francja|FR|145.239.37.162|2001:41d0:301::30|
|Irlandia|IE|178.32.77.113|2001:41d0:301:3::30|
|Portugalia|PT|5.135.68.91|2001:41d0:301:2::30|
|Wielka Brytania|UK|91.134.177.228|2001:41d0:301:12::30|
|Włochy|IT|94.23.73.16|2001:41d0:301:11::30|
|Hiszpania|ES|149.202.105.228|2001:41d0:301:4::30|
|Polska|PL|188.165.21.8|2001:41d0:301:5::30|
|Czechy|CZ|94.23.168.143|2001:41d0:301:6::30|
|Niderlandy|NL|149.202.25.75|2001:41d0:301:7::30|
|Finlandia|FI|188.165.140.151|2001:41d0:301:8::30|
|Litwa|LT|188.165.24.146|2001:41d0:301:9::30|
|Niemcy|DE|51.255.232.79|2001:41d0:301:1::30|
|Belgia|BE|213.32.107.241|2001:41d0:301:10::30|

Jeśli **Shared CDN** jest aktywny na Twoim hostingu, użyj tego adresu IP:

```bash
46.105.204.30
```

Jeśli potrzebujesz adresu IP **bramy wyjściowej** hostingu (gateway), użyj poniższego adresu IP:

```bash
51.178.146.199
```

### Klaster 031

Tutaj znajdziesz adresy IP **klastra** według kraju (w przypadku geolokalizacji):

|Kraj|Kod kraju|IPv4|IPv6|
|---|---|----|---|
|Francja|FR|146.59.209.152|2001:41d0:301::31|
|Irlandia|IE|188.165.5.107|2001:41d0:301:3::31|
|Portugalia|PT|51.178.229.47|2001:41d0:301:2::31|
|Wielka Brytania|UK|178.32.52.177|2001:41d0:301:12::31|
|Włochy|IT|94.23.66.84|2001:41d0:301:11::31|
|Hiszpania|ES|51.255.26.63|2001:41d0:301:4::31|
|Polska|PL|87.98.236.253|2001:41d0:301:5::31|
|Czechy|CZ|217.182.52.81|2001:41d0:301:6::31|
|Niderlandy|NL|213.32.108.83|2001:41d0:301:7::31|
|Finlandia|FI|178.32.10.72|2001:41d0:301:8::31|
|Litwa|LT|188.165.30.182|2001:41d0:301:9::31|
|Niemcy|DE|151.80.4.219|2001:41d0:301:1::31|
|Belgia|BE|217.182.187.17|2001:41d0:301:10::31|

Jeśli **Shared CDN** jest aktywny na Twoim hostingu, użyj tego adresu IP:

```bash
46.105.204.31
```

Jeśli potrzebujesz adresu IP **bramy wyjściowej** hostingu (gateway), użyj poniższego adresu IP:

```bash
141.94.87.67
```

### Klaster 051

Tutaj znajdziesz adresy IP **klastra** według kraju (w przypadku geolokalizacji):

|Kraj|Kod kraju|IPv4|IPv6|
|---|---|----|---|
|Canada|CA|51.161.122.78|2607:5300:202:0:0::51|

Jeśli **Shared CDN** jest aktywny na Twoim hostingu, użyj tego adresu IP:

```bash
46.105.204.51
```

Jeśli potrzebujesz adresu IP **bramy wyjściowej** hostingu (gateway), użyj poniższego adresu IP:

```bash
51.161.94.36
```

### Cluster 100

Tutaj znajdziesz adresy IP **klastra** według kraju (w przypadku geolokalizacji):

|Kraj|Kod kraju|IPv4|IPv6|
|---|---|----|---|
|Francja|FR|5.135.23.164|2001:41d0:301::100|
|Irlandia|IE|188.165.0.143|2001:41d0:301:3::100|
|Portugalia|PT|94.23.76.76|2001:41d0:301:2::100|
|Wielka Brytania|UK|87.98.254.187|2001:41d0:301:12::100|
|Włochy|IT|178.32.143.165|2001:41d0:301:11::100|
|Hiszpania|ES|178.33.119.211|2001:41d0:301:4::100|
|Polska|PL|94.23.89.116|2001:41d0:301:5::100|
|Czechy|CZ|94.23.172.226|2001:41d0:301:6::100|
|Niderlandy|NL|94.23.146.244|2001:41d0:301:7::100|
|Finlandia|FI|188.165.137.37|2001:41d0:301:8::100|
|Litwa|LT|188.165.26.152|2001:41d0:301:9::100|
|Niemcy|DE|87.98.243.177|2001:41d0:301:1::100|
|Belgia|BE|91.121.217.51|2001:41d0:301:10::100|

Jeśli **Shared CDN** jest aktywny na Twoim hostingu, użyj tego adresu IP:

```bash
46.105.204.100
```

Jeśli potrzebujesz adresu IP **bramy wyjściowej** hostingu (gateway), użyj poniższego adresu IP:

```bash
54.36.142.130
```

## Sprawdź również

[Uruchomienie strony podpiętej w opcji MultiSite na Twoim hostingu](/pages/web_cloud/web_hosting/multisites_configure_multisite)

[Włącz HTTPS za pomocą certyfikatu SSL na Twoim hostingu](/pages/web_cloud/web_hosting/ssl-activate-https-website)

[Zoptymalizuj wydajność swojej strony www](/pages/web_cloud/web_hosting/optimise_your_website_performance)

W przypadku wyspecjalizowanych usług (pozycjonowanie, rozwój, etc.) skontaktuj się z [partnerami OVHcloud](/links/partner).
 
Jeśli chcesz otrzymywać wsparcie w zakresie konfiguracji i użytkowania Twoich rozwiązań OVHcloud, zapoznaj się z naszymi [ofertami pomocy](/links/support).
 
Dołącz do [grona naszych użytkowników](/links/community).