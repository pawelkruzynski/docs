---
title: "Composer auf einem Webhosting installieren"
excerpt: "Diese Anleitung erklärt, wie Sie Composer installieren und erste Schritte ausführen"
updated: 2023-03-07
---

## Ziel 

[Composer](https://getcomposer.org/){.external} ist ein für PHP erstellter Dependency Manager. PHP-Entwickler können externe Bibliotheken in ihre Programme einbinden. Composer vereinfacht die Verteilung von Bibliotheken und die Wartung des Codes von PHP-Projekten. Seit der Veröffentlichung dieses Tools wurden zahlreiche Best Practices für die Entwicklung etabliert und somit die Bibliotheken der PHP-Community verbessert. Diese bewährten Verfahren werden in der Form [SRP](http://www.php-fig.org/){.external} dokumentiert.

**Diese Anleitung erklärt, wie Sie Composer installieren und gibt ein Anwendungsbeispiel.**

> [!warning]
> OVHcloud stellt Ihnen Dienstleistungen zur Verfügung, für deren Konfiguration und Verwaltung Sie die alleinige Verantwortung tragen. Es liegt somit bei Ihnen, sicherzustellen, dass diese ordnungsgemäß funktionieren.
> 
> Diese Anleitung soll Sie bei allgemeinen Aufgaben bestmöglich unterstützen. Dennoch empfehlen wir Ihnen, falls Sie Hilfe brauchen, einen [spezialisierten Dienstleister](/links/partner) zu kontaktieren oder Ihre Fragen in der OVHcloud Community zu stellen. Leider können wir Ihnen für administrative Aufgaben keine weitergehende technische Unterstützung anbieten. Weitere Informationen finden Sie am [Ende dieser Anleitung](#go-further).
>

## Voraussetzungen

- Sie haben ein [OVHcloud Webhosting](/links/web/hosting) mit SSH-Zugang in Ihrem Kunden-Account.
- Sie haben Zugriff auf Ihr [OVHcloud Kundencenter](/links/manager).

## In der praktischen Anwendung

Verbinden Sie sich via SSH mit Ihrem Hosting mithilfe unserer Anleitung zur [Verwendung von SSH mit Ihrem OVHcloud Webhosting](/pages/web_cloud/web_hosting/ssh_on_webhosting).

Verwenden Sie die Kommandozeile, um zu überprüfen, ob die PHP-Version kompatibel ist:

```bash
php --version
```

Wenn es sich nicht um eine korrekte Version handelt, können Sie einen Alias konfigurieren:

```bash
alias php='/usr/local/php8.0/bin/php'
```

Wir empfehlen Ihnen, im Wurzelverzeichnis Ihres Webhostings zu bleiben, damit die Dateien von Composer nicht öffentlich zugänglich sind. Führen Sie anschließend folgenden Befehl aus:

```bash
curl -sS https://getcomposer.org/installer | php
```

Composer ist ab sofort für Ihr Webhosting verfügbar.

### Anwendungsbeispiel

Wenn Sie **Symfony 2** installieren möchten, können Sie zum Beispiel folgenden Befehl ausführen:

```bash
php composer.phar create-project symfony/framework-standard-edition my_project_name "2.7.*"
```

Sie können auch die OVHcloud API über Ihr Hosting mit dem offiziellen Wrapper verwenden. Fügen Sie hierzu eine Datei mit dem Namen *composer.json* hinzu, die Ihre benötigte Dependency-Liste enthält. Hier ein Beispiel dieser Datei mit dem OVHcloud API Wrapper:

```json
1. {
2.     "name": "Example Application",
3.     "description": "This is an example of OVHcloud APIs wrapper usage",
4.     "require": {
5.         "ovh/ovh": "1.1.*"
6.     }
7. }
```

Um sie zu installieren starten Sie folgenden Befehl im gleichen Ordner:

```bash
php composer.phar install
```

Beachten Sie die Dokumentation zu dieser Library sowie den Code, verfügbar auf [GitHub](https://github.com/ovh/php-ovh){.external}.

## Weiterführende Informationen <a name="go-further"></a>

Kontaktieren Sie für spezialisierte Dienstleistungen (SEO, Web-Entwicklung etc.) die [OVHcloud Partner](/links/partner).

Wenn Sie Hilfe bei der Nutzung und Konfiguration Ihrer OVHcloud Lösungen benötigen, beachten Sie unsere [Support-Angebote](/links/support).

Treten Sie unserer [User Community](/links/community) bei.