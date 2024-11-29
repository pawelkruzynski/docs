---
title: "Tutorial - Wie kann ich den Zugang zu meiner Website für bestimmte IP-Adressen über eine .htaccess Datei sperren?"
excerpt: "Erfahren Sie hier die Möglichkeiten, um mit .htaccess Dateien den Zugriff auf Ihre Website für bestimmte IP-Adressen zu blockieren"
updated: 2024-03-14
---

## Ziel 

Dieses Tutorial hilft Ihnen dabei, den Zugang zu Ihren Webseiten von externen Netzwerken abzusichern sowie unbefugten Zugriff und DoS-Angriffe (Denial of Service) zu verhindern.

Sie können das mithilfe einer ".htaccess" Datei erreichen. Es handelt sich dabei um eine spezielle Textdatei, die vom Webserver (Apache) gelesen wird und es ermöglicht, bestimmte Regeln für ein Verzeichnis und dessen Unterverzeichnisse festzulegen.

Sie können mehrere ".htaccess" Dateien in [FTP-Bereich](/pages/web_cloud/web_hosting/ftp_connection) Ihres Hostings erstellen, jedoch nur **eine einzige** pro Verzeichnis oder Unterverzeichnis, um Konflikte zwischen verschiedenen ".htaccess" Dateien zu vermeiden.

**Diese Anleitung erklärt, wie Sie den Zugang zu Ihrer Seite für bestimmte IP-Adressen über eine ".htaccess" Datei blockieren.**

> [!warning]
> OVHcloud stellt Ihnen Dienstleistungen zur Verfügung, für deren Konfiguration und Verwaltung Sie die alleinige Verantwortung tragen. Es liegt somit bei Ihnen, sicherzustellen, dass diese ordnungsgemäß funktionieren.
> 
> Diese Anleitung soll Sie bei allgemeinen Aufgaben bestmöglich unterstützen. Dennoch empfehlen wir Ihnen, falls Sie Hilfe brauchen, einen [spezialisierten Dienstleister](/links/partner) zu kontaktieren oder Ihre Fragen in der OVHcloud Community zu stellen. Leider können wir Ihnen für administrative Aufgaben keine weitergehende technische Unterstützung anbieten. Weitere Informationen finden Sie am [Ende dieser Anleitung](#go-further).
>

## Voraussetzungen

- Sie haben ein [OVHcloud Webhosting](/links/web/hosting) in Ihrem Kunden-Account.

## In der praktischen Anwendung

> [!primary]
>
> Die ".htaccess" kann in mehreren verschiedenen Ordnern angelegt werden, wobei die Voraussetzung **nur einer** ".htaccess" Datei pro Ordner oder Unterordner einzuhalten ist.
>
> Die Parameter einer ".htaccess" Datei gelten für das Verzeichnis, in dem sie sich befindet, sowie für alle Unterverzeichnisse.
>
> Um diese Verzeichnisse zu bearbeiten (oder zu erstellen), loggen Sie sich in den FTP-Bereich Ihres Hostings ein. Falls nötig lesen Sie die Anleitung "[Mit dem Speicherplatz eines Webhostings verbinden](/pages/web_cloud/web_hosting/ftp_connection)".
>

### Eine IP, einen IP-Bereich, eine Domain oder alle IPs eines Landes blockieren 

Es sind mehrere Regeln verfügbar, um die Zugänge zu Ihrem Hosting über die ".htaccess" zu sperren.<br>
Achten Sie auf die Syntax und die Blockierungseinstellungen, damit Sie sich nicht selbst vom Aufruf Ihrer gehosteten Seiten und/oder Skripte aussperren.<br>
Im Fehlerfall können Sie sich jederzeit in den [FTP-Bereich](/pages/web_cloud/web_hosting/ftp_connection) Ihres Hostings einloggen, um den Fehler zu korrigieren. 

> [!primary]
>
> Shared Hosting funktioniert derzeit mit **Apache 2.4**. Seit der Version **Apache 2.3** wurden Variablen implementiert und die Syntax für Zugriffsberechtigungen wurde weiterentwickelt.
>
> Da die alte Syntax sehr häufig verwendet wird, ist sie immer noch auf unseren Infrastrukturen aktiv. Allerdings gilt sie seitens *Apache* als veraltet und ist möglicherweise nicht mehr lange verfügbar. In diesem Tutorial finden Sie Beispiele für beide Varianten der Syntax.
>
> Mehr Informationen zur neuen Syntax finden Sie auf folgenden offiziellen Seiten:
>
> - [Dokumentation zur Zugriffskontrolle Apache 2.4](https://httpd.apache.org/docs/en/howto/access.html){.external}
> - [Dokumentation zu mod_authz_core Apache 2.4](https://httpd.apache.org/docs/2.4/mod/mod_authz_core.html){.external}
>
>

##### Eine IP blockieren

Um eine bestimmte IP-Adresse zu blockieren, tragen Sie einen der beiden folgenden Codes in Ihrer ".htaccess"-Datei ein:

> [!tabs]
> Historische Syntax
>>
>> ```bash
>> Deny from IP_address
>> ```
>>
> Syntax ab Apache 2.3
>>
>> ```bash
>> <RequireAll>
>> Require all granted
>> Require not ip IP_address
>> </RequireAll>
>> ```
>>

- **Beispiel**: Wenn Sie die IP-Adresse 203.0.113.0 blockieren möchten, müssen Sie einen der folgenden Codes einfügen:

> [!tabs]
> Historische Syntax
>>
>> ```bash
>> Deny from 203.0.113.0
>> ```
>>
> Syntax ab Apache 2.3
>>
>> ```bash
>> <RequireAll>
>> Require all granted
>> Require not ip 203.0.113.0
>> </RequireAll>
>> ```
>>

#### Einen IP-Bereich blockieren

Um einen IP-Adressbereich zu blockieren, tragen Sie einen der beiden folgenden Codes in Ihrer ".htaccess" ein:

> [!tabs]
> Historische Syntax
>>
>> ```bash
>> Deny from IP_range
>> ```
>>
> Syntax ab Apache 2.3
>>
>> ```bash
>> <RequireAll>
>> Require all granted
>> Require not ip IP_range
>> </RequireAll>
>> ```
>>

- **Beispiel**: Wenn Sie alle IP-Adressen in 203.0.113.x blockieren möchten, tragen Sie einen der folgenden Codes ein:

> [!tabs]
> Historische Syntax
>>
>> ```bash
>> Deny from 203.0.113
>> ```
>>
> Syntax ab Apache 2.3
>>
>> ```bash
>> <RequireAll>
>> Require all granted
>> Require not ip 203.0.113
>> </RequireAll>
>> ```
>>

##### Eine Domain blockieren

Domains können über Weiterleitungen oder Anfragen auf Ihr Hosting zugreifen.

Um eine Domain zu blockieren, tragen Sie einen der folgenden Codes in Ihre ".htaccess" Datei ein:

> [!tabs]
> Historische Syntax
>>
>> ```bash
>> Deny from domain
>> ```
>>
> Syntax ab Apache 2.3
>>
>> ```bash
>> <RequireAll>
>> Require not host domain
>> </RequireAll>
>> ```
>>

- **Beispiel**: Wenn Sie "domain.tld" blockieren möchten, fügen Sie einen der folgenden Codes ein:

> [!tabs]
> Historische Syntax
>>
>> ```bash
>> Deny from domain.tld
>> ```
>>
> Syntax ab Apache 2.3
>>
>> ```bash
>> <RequireAll>
>> Require not host domain.tld
>> </RequireAll>
>> ```
>>

#### Die IPs eines Landes blockieren

> [!primary]
>
> Alle IP-Adressen (insbesondere öffentliche IP-Adressen) sind national geolokalisiert. So erhalten Sie einen Überblick über die Herkunft des Traffics und können die zugehörigen IP-Adressen physisch verorten. 
>
> Mit der ".htaccess" können Sie alle geolokalisierten IPs eines Landes blockieren. 
> Das bedeutet, alle Zugriffe auf Ihre Website aus diesem Land werden gesperrt (abgesehen von Nutzern, die eine VPN-Verbindung mit einer geolokalisierten IP eines anderen Landes nutzen).
>
> Blockierungen über ".htaccess" werden über die "Country Codes" (ISO Standard 3166-1 alpha2) der Länder durchgeführt.
>
> Mehrere Websites listen die jeweiligen Länder und deren "Country Codes" auf, darunter [https://www.iban.com/country-codes](https://www.iban.com/country-codes){.external} (unabhängig von OVHcloud).
>

Um alle IP-Adressen eines Landes zu blockieren, tragen Sie einen der folgenden Codes in Ihre ".htaccess"-Datei ein:

> [!tabs]
> Historische Syntax
>>
>> ```bash
>> SetEnvIf GEOIP_COUNTRY_CODE Country_Code BlockCountry
>> Deny from env=BlockCountry
>> ```
>>
> Syntax ab Apache 2.3
>> An oberster Stelle der ".htaccess" zu platzieren
>>
>> ```bash
>> RewriteCond %{ENV:GEOIP_COUNTRY_CODE} ^(Country_Code)$
>> RewriteRule ^(.*)$ - [F,L]
>> ```
>>

- **Beispiel**: Wenn Sie geolokalisierte IP-Adressen von Fiji (FJ) und Grönland (GR) blockieren möchten, müssen Sie einen der folgenden Codes einfügen:

> [!tabs]
> Historische Syntax
>>
>> ```bash
>> SetEnvIf GEOIP_COUNTRY_CODE FJ BlockCountry
>> SetEnvIf GEOIP_COUNTRY_CODE GR BlockCountry
>> Deny from env=BlockCountry
>> ```
>>
> Syntax ab Apache 2.3
>> An oberster Stelle der ".htaccess" zu platzieren
>>
>> ```bash
>> RewriteCond %{ENV:GEOIP_COUNTRY_CODE} ^(FJ|GR)$
>> RewriteRule ^(.*)$ - [F,L]
>> ```
>>

### Um nur einige IPs, einen IP-Bereich oder alle IPs eines Landes zu erlauben

Anstatt den Zugang für eine oder mehrere IPs zu beschränken und allen anderen Zugang zu Ihrem Hosting zu gewähren, können Sie den umgekehrten Schritt tun, indem Sie alle IPs blockieren und dann nur einer oder mehreren IPs Zugriff auf Ihren Dienst gewähren.

#### Eine oder mehrere IPs erlauben

Um nur einer IP den Zugriff auf Ihren Dienst zu erlauben, tragen Sie einen der folgenden Codes in Ihre ".htaccess" Datei ein:

> [!tabs]
> Historische Syntax
>>
>> ```bash
>> order deny,allow
>> deny from all
>> Allow from IP_address
>> ```
>>
> Syntax ab Apache 2.3
>>
>> ```bash
>> Require ip IP_address
>> ```
>>

- **Beispiel**: Wenn Sie nur den IPs 203.0.113.0 und 203.0.113.1 den Zugriff auf Ihr Hosting erlauben möchten, verwenden Sie einen der folgenden Codes:

> [!tabs]
> Historische Syntax
>>
>> ```bash
>> order deny,allow
>> deny from all
>> Allow from 203.0.113.0
>> Allow from 203.0.113.1
>> ```
>>
> Syntax ab Apache 2.3
>>
>> ```bash
>> Require ip 203.0.113.0 203.0.113.1
>> ```
>>

#### Einen IP-Bereich erlauben

Um einem IP-Bereich den Zugriff auf Ihren Dienst zu erlauben, tragen Sie einen der folgenden Codes in Ihre ".htaccess" Datei ein:

> [!tabs]
> Historische Syntax
>>
>> ```bash
>> order deny,allow
>> deny from all
>> Allow from IP_range
>> ```
>>
> Syntax ab Apache 2.3
>> An oberster Stelle der ".htaccess" zu platzieren
>>
>> ```bash
>> Require ip IP_range
>> ```
>>

- **Beispiel**: Wenn Sie nur dem IP-Bereich 203.0.113.x den Zugriff auf Ihr Hosting erlauben möchten, fügen Sie einen der folgenden Codes ein:

> [!tabs]
> Historische Syntax
>>
>> ```bash
>> order deny,allow
>> deny from all
>> Allow from 203.0.113
>> ```
>>
> Syntax ab Apache 2.3
>> An oberster Stelle der ".htaccess" zu platzieren
>>
>> ```bash
>> Require ip 203.0.113
>> ```
>>

#### Alle IPs eines Landes erlauben

Um allen IP-Adressen eines Landes den Zugriff auf Ihren Dienst zu erlauben, tragen Sie einen der folgenden Codes in Ihre ".htaccess" Datei ein:

> [!tabs]
> Historische Syntax
>>
>> ```bash
>> order deny,allow
>> deny from all
>> SetEnvIf GEOIP_COUNTRY_CODE Country_Code AllowCountry
>> Allow from env=AllowCountry
>> ```
>>
> Syntax ab Apache 2.3
>> An oberster Stelle der ".htaccess" zu platzieren
>>
>> ```bash
>> RewriteCond %{ENV:GEOIP_COUNTRY_CODE} !^(Country_Code)$
>> RewriteRule ^(.*)$ - [F,L]
>> ```
>>

- **Beispiel**: Wenn Sie nur Fiji (FJ) und Grönland (GR) Zugang zu Ihrem Hosting gewähren möchten, müssen Sie einen der folgenden Codes einfügen:

> [!tabs]
> Historische Syntax
>>
>> ```bash
>> order deny,allow
>> deny from all
>> SetEnvIf GEOIP_COUNTRY_CODE FJ AllowCountry
>> SetEnvIf GEOIP_COUNTRY_CODE GR AllowCountry
>> Allow from env=AllowCountry
>> ```
>>
> Syntax ab Apache 2.3
>> An oberster Stelle der ".htaccess" zu platzieren
>>
>> ```bash
>> RewriteCond %{ENV:GEOIP_COUNTRY_CODE} !^(FJ|GR)$
>> RewriteRule ^(.*)$ - [F,L]
>> ```
>>

### Weitere Aktionen mit ".htaccess"

Abgesehen von der Zugriffssicherheit auf Ihr Hosting erlaubt die ".htaccess" Datei noch weitere Aktionen. Nachfolgend finden Sie weitere OVHcloud Tutorials zum Thema:

- [Den Adminbereich Ihrer Website mit einer .htaccess Datei schützen](/pages/web_cloud/web_hosting/htaccess_protect_directory_by_password)
- [Fortgeschrittene Operationen mit .htaccess Dateien](/pages/web_cloud/web_hosting/htaccess_what_else_can_you_do)

## Weiterführende Informationen <a name="go-further"></a>

Kontaktieren Sie für spezialisierte Dienstleistungen (SEO, Web-Entwicklung etc.) die [OVHcloud Partner](/links/partner).

Wenn Sie Hilfe bei der Nutzung und Konfiguration Ihrer OVHcloud Lösungen benötigen, beachten Sie unsere [Support-Angebote](/links/support).

Treten Sie unserer [User Community](/links/community) bei.