---
title: "Tutorial - htaccess-Dateien mit WordPress verwenden"
excerpt: "Erfahren Sie hier, wie Sie Ihre WordPress Website mit einer oder mehreren htaccess-Dateien absichern"
updated: 2024-05-28
---

## Ziel

In dieser Anleitung erfahren Sie, wie Sie bestimmte Funktionen Ihres Webhostings mit **.htaccess**-Dateien konfigurieren, insbesondere um die Einstellungen Ihrer Website teilweise oder vollständig zu ändern (Weiterleitungen, Zugangsbeschränkungen, Datei-Berechtigungen, Cache-Kontrolle etc.).

> [!warning]
> OVHcloud stellt Ihnen Dienstleistungen zur Verfügung, für deren Konfiguration und Verwaltung Sie die alleinige Verantwortung tragen. Es liegt somit bei Ihnen, sicherzustellen, dass diese ordnungsgemäß funktionieren.
> 
> Dieses Tutorial soll Sie bei allgemeinen Aufgaben bestmöglich unterstützen. Dennoch empfehlen wir Ihnen, falls Sie Hilfe brauchen, einen [spezialisierten Dienstleister](/links/partner) zu kontaktieren oder Ihre Fragen in der [WordPress Community](https://wordpress.com/support/){.external} zu stellen. Leider können wir Ihnen für administrative Aufgaben keine weitergehende technische Unterstützung anbieten. Weitere Informationen finden Sie am [Ende dieser Anleitung](#go-further).
>

**Dieses Tutorial erklärt, wie Sie Ihr WordPress mit .htaccess-Dateien absichern.**

## Voraussetzungen

- Sie verfügen über ein [Webhosting](/links/web/hosting) und haben WordPress installiert.
- Sie haben einen FTP-Client, z.B. [FileZilla](https://filezilla-project.org/) installiert, wie in unserem [Tutorial zu FileZilla](/pages/web_cloud/web_hosting/ftp_filezilla_user_guide) erläutert.

**.htaccess**-Dateien können mit Texteditoren erstellt und bearbeitet werden, zum Beispiel:

- [Notepad](https://support.microsoft.com/de-de/windows/hilfe-in-windows-editor-4d68c388-2ff2-0e7f-b706-35fb2ab88a8c){.external} in Windows
- [TextEdit](https://support.apple.com/de-de/guide/textedit/welcome/mac){.external} in macOS
- [Notepad++](https://notepad-plus-plus.org/){.external}

> [!primary]
>
> Die unten aufgeführten Sicherheitslösungen sind nicht umfassend.
>
> Wenn Sie zum Beispiel ein anderes **C**ontent **M**anagement **S**ystem (**CMS**) als WordPress verwenden, gibt es andere Sicherheitslösungen.
>
> Wenn Sie kein CMS verwenden, stellt Ihnen OVHcloud auch ein [Tutorial zum Schützen von Verzeichnissen oder des Verwaltungsinterface Ihrer Website über .htaccess Dateien](/pages/web_cloud/web_hosting/htaccess_protect_directory_by_password) zur Verfügung.
>
> Kontaktieren Sie bei Fragen unsere [User Community](/links/community) oder [OVHcloud Partner](/links/partner). Die Support-Teams von OVHcloud werden Ihnen zu diesen Themen keine Hilfe bieten können.
>

## FAQ

### Was ist eine .htaccess-Datei?

Mit einer **.htaccess**-Datei können Sie einen Webserver konfigurieren. Bei Webhostings handelt es sich um den Open Source Webserver **Apache**. Die Syntax dieser Datei wird von der Organisation definiert, die **Apache** entwickelt. Im Gegensatz zu den meisten Konfigurationsdateien eines Servers befinden sich die **.htaccess**-Dateien in den Verzeichnissen von Websites, genauer: im FTP-Speicherplatz Ihres Webhostings. Eine **.htaccess**-Datei hat Auswirkungen auf das Verzeichnis, in dem sie liegt, sowie auf alle Unterverzeichnisse dieses Ordners.

Unsere Webhosting-Angebote erlauben keine Serverkonfigurationsdateien. Die **.htaccess**-Dateien ermöglichen es jedoch, bestimmte Eigenschaften und Verhaltensweisen zu ändern. Darüber hinaus ist es nicht notwendig, **Apache** neu zu starten, damit die Inhalte und Änderungen in der **.htaccess**-Datei berücksichtigt werden. Mit unseren [OVHcloud Webhostings](/links/web/hosting) können **.htaccess**-Dateien konfiguriert werden.

Der Punkt vor dem Dateinamen **.htaccess** (der selbst keine Endung hat) kennzeichnet eine versteckte Datei. Außerdem sind diese Dateien für externe Benutzer, die Ihre Website aufrufen, nicht verfügbar.

### Was ist ein Webserver?

Ein Webserver ist eine Software, mit der Informationen über ein Netzwerk über das *Hypertext Transfer Protocol (HTTP)* ausgetauscht werden können.
Es gibt mehrere davon, zum Beispiel *Apache*, *Nginx*, *Tomcat* oder das HTTP-Modul in *NodeJS*.

### Welche Vorsichtsmaßnahmen sind zu treffen?

Eine fehlerhafte Konfiguration Ihrer **.htaccess**-Datei kann Fehler auf Ihrem Server verursachen (zum Beispiel einen Fehler 500: *Internal Server Error*) oder Ihren Dienst unzugänglich machen. Denken Sie daran, systematisch Backups der Versionen Ihrer funktionalen Dateien durchzuführen, um bei Fehlfunktionen nach einer Änderung zu einem früheren Zustand zurückkehren zu können.

Wenn Sie diese Art von Datei nicht regelmäßig bearbeiten, testen Sie jedes Element, das Sie ändern. So vermeiden Sie Zeitverlust, da Sie nicht erst die Zeilen identifizieren müssen, welche Fehlfunktionen Ihres Webservers verursachen. Konfigurationsfehler oder falsche Syntax können den Betrieb Ihres Webservers beeinträchtigen.

### Welche Werkzeuge verwenden?

- FTP-Client, um Ihre Dateien zu übertragen (FileZilla, Cyberduck)
- Texteditor

### Wo befinden sich die .htaccess Dateien in WordPress?

Sie können mehrere **.htaccess**-Dateien auf demselben Webhosting anlegen. Jede dieser Dateien legt die Regeln für das Verzeichnis fest, in dem sie sich befindet, sowie dessen Unterverzeichnisse.

Die meisten Änderungen werden im **Wurzelverzeichnis** vorgenommen. Die **.htaccess**-Datei im Wurzelverzeichnis der Website enthält folgende Zeilen:

```bash
# BEGIN WordPress
# Zeilen (directives) zwischen "BEGIN WordPress" und "END WordPress" werden
# dynamisch generiert und dürfen nur über WordPress Filter geändert werden.
# Jede Änderung zwischen diesen Markern wird überschrieben.

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

**Erläuterungen zum Code**:

- **#**: Wird zur Kennzeichnung einer Kommentarzeile verwendet.
- **RewriteEngine On**: Aktiviert das Apache Modul `mod_rewrite`, mit dem URLs umgeschrieben werden können (ermöglicht auch die Weiterleitung einer URL auf eine andere URL).
- **RewriteRule**: Diese Syntax wird nach dem Muster `RewriteRule Substitution` geschrieben und kann mehrfach in der **.htaccess**-Datei verwendet werden (dies ist der Fall in der Standarddatei, die Sie im Wurzelverzeichnis der WordPress-Installation finden). Die Anordnung der Regeln ist von entscheidender Bedeutung. Achten Sie auf die Reihenfolge in der die Regeln geschrieben werden.
- **RewriteBase**: Gibt an, dass die Wurzel der Website `/` ist.
- **RewriteCond**: Dies sind Voraussetzungen für die unmittelbar folgende Regel. In diesem Fall schließt die erste Vorbedingung URLs aus, die einen Pfad zu einer Datei enthalten, während die zweite Vorbedingung die Unterverzeichnisse ausschließt.

### Was kann ich zu einer .htaccess-Datei für WordPress hinzufügen?

Es gibt mehrere Möglichkeiten, die Einstellungen zu konfigurieren, die das Verhalten des Servers ändern (einige Einschränkungen existieren jedoch je nach Hosting):

- Konfigurationsdateien Ihres Servers bearbeiten
- Richtlinien zur Konfigurationsdatei **wp-config.php*** im Wurzelverzeichnis hinzufügen oder ändern
- Regeln der **.htaccess**-Datei ändern oder hinzufügen

## In der praktischen Anwendung

> [!warning]
>
> Bevor Sie den folgenden Schritten folgen, leiten Sie HTTP-Anfragen nach HTTPS um. Folgen Sie hierzu den Anweisungen in unserer Anleitung: [Website mit SSL-Zertifikat auf HTTPS umstellen](/pages/web_cloud/web_hosting/ssl-activate-https-website#schritt-1-ssl-zertifikat-fur-das-hosting-aktivieren)

### Die Anzeige von Verzeichnissen und Unterverzeichnissen verhindern

Um zu vermeiden, dass Besucher Ihrer Website deren Verzeichnisstruktur anzeigen können (und damit Informationen zu den verwendeten Themes und Plugins preiszugeben), blockieren Sie die Anzeige von Unterverzeichnissen, indem Sie diese Zeile in Ihrer Datei hinzufügen:

```bash
Options All -Indexes
```

### Ihre Konfigurationsdatei schützen

Ihre Datei **wp-config.php**, die sich im Wurzelverzeichnis Ihrer Website befindet, enthält sensible Konfigurationsinformationen. Verhindern Sie den Zugriff auf diese Datei, indem Sie folgende Zeilen in Ihrer **.htaccess**-Datei hinzufügen:

```bash
<Files wp-config.php>
    order allow,deny
    deny from all
    satisfy all
</Files>
```

### Eine IP-Adresse blockieren

Wenn Sie eine zu sperrende IP-Adresse identifiziert haben, geben Sie diese Zeilen in Ihre **.htaccess**-Datei ein:

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
>> Ersetzen Sie `203.0.113.0` mit der zu blockierenden IPv4-Adresse.
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
>> Ersetzen Sie `2001:db8:1:1b00:203:0:113:0` mit der zu blockierenden IPv6-Adresse.
>>

Weitere Informationen zu diesem Thema finden Sie in unserer Anleitung zur [IP-basierten Zugriffsbeschränkung über die .htaccess-Datei](/pages/web_cloud/web_hosting/htaccess_how_to_block_a_specific_ip_address_from_accessing_your_website).

#### Zugang zum Verzeichnis wp-admin (oder anderen Verzeichnissen) nach IP blockieren

Das Verzeichnis **wp-admin** enthält den Zugang zum Administrationssinterface der Installation. (Die Methode funktioniert auch mit anderen Verzeichnissen, deren URLs nicht zu einem Verwaltungszugang führen). Zum Schutz dieses Verzeichnisses beschränken Sie den Zugriff auf eine oder mehrere IP-Adressen mit folgendem Code in Ihrer **.htaccess**:

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
>> In diesem Beispiel können nur die IPv4-Adressen `203.0.113.0` und `203.0.113.1` auf das Verzeichnis zugreifen, in dem sich die .htaccess-Datei befindet.
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
>> In diesem Beispiel können nur die IPv6-Adressen `2001:db8:1:1b00:203:0:113:0` und `2001:db8:1:1b00:203:0:113:1` auf das Verzeichnis zugreifen, in dem sich die .htaccess-Datei befindet.

### Wichtige Informationen

- Sichern Sie vor jeder Änderung eine funktionale Version Ihrer **.htaccess**-Datei.
- Wenn Ihre Änderungen zu einem Fehler führen, ersetzen Sie (über Ihren FTP-Client) die **.htaccess**-Datei mit der vorherigen Version.
- Sie können bestimmte Einstellungen in der Datei **wp-config.php** verwalten.
- **.htaccess**-Dateien sind besonders effizient für die Verwaltung von URLs, Weiterleitungen und die Sicherheit Ihrer Website.

## Weiterführende Informationen <a name="go-further"></a>

[Offizielles Apache .htaccess tutorial](https://httpd.apache.org/docs/2.4/de/howto/htaccess.html)

Kontaktieren Sie für spezialisierte Dienstleistungen (SEO, Web-Entwicklung etc.) die [OVHcloud Partner](/links/partner).

Wenn Sie Hilfe bei der Nutzung und Konfiguration Ihrer OVHcloud Lösungen benötigen, beachten Sie unsere [Support-Angebote](/links/support).

Treten Sie unserer [User Community](/links/community) bei.