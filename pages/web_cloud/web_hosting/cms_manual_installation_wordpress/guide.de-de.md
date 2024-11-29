---
title: "Tutorial - Manuelle Installation von WordPress"
excerpt: "Diese Anleitung erklärt, wie Sie Ihr WordPress CMS eigenständig installieren"
updated: 2023-04-03
---

## Ziel

Dieses Tutorial hilft Ihnen Schritt für Schritt bei der manuellen Installation eines WordPress CMS (Content Management System).

> [!warning]
> OVHcloud stellt Ihnen Dienstleistungen zur Verfügung, für deren Konfiguration und Verwaltung Sie die alleinige Verantwortung tragen. Es liegt somit bei Ihnen, sicherzustellen, dass diese ordnungsgemäß funktionieren.
> 
> Dieses Tutorial soll Sie bei allgemeinen Aufgaben bestmöglich unterstützen. Dennoch empfehlen wir Ihnen, falls Sie Hilfe brauchen, einen [spezialisierten Dienstleister](/links/partner) zu kontaktieren oder Ihre Fragen in der [WordPress Community](https://wordpress.com/support/){.external} zu stellen. Leider können wir Ihnen für administrative Aufgaben keine weitergehende technische Unterstützung anbieten. Weitere Informationen finden Sie am [Ende dieser Anleitung](#go-further).
>

> [!success]
>
> Um WordPress **automatisch** in Ihrem [OVHcloud Kundencenter](/links/manager) zu installieren, lesen Sie unsere Anleitung zur [Installation Ihrer Website mit 1-Klick-Modulen](/pages/web_cloud/web_hosting/cms_install_1_click_modules).
>
> Um ein **anderes CMS manuell** zu installieren (Joomla!, Drupal, PrestaShop), lesen Sie unsere Anleitung zur [manuellen Installation eines CMS](/pages/web_cloud/web_hosting/cms_manual_installation).
>

**Dieses Tutorial erklärt, wie Sie Ihr WordPress CMS eigenständig installieren.**

## Voraussetzungen

- Sie verfügen über ein [Webhosting](/links/web/hosting), das mindestens eine Datenbank enthält.
- Sie verfügen über einen [Domainnamen](/links/web/domains).
- Sie haben Zugriff auf Ihr [OVHcloud Kundencenter](/links/manager).

## In der praktischen Anwendung

### Schritt 1: Installation vorbereiten <a name="step1"></a> 

Um das CMS **WordPress** auf Ihrem [Webhosting](/links/web/hosting) zu installieren, sind einige Vorbereitungen erforderlich.

Führen Sie zunächst **alle Schritte** in unserer Anleitung zur [manuellen Installation eines CMS](/pages/web_cloud/web_hosting/cms_manual_installation) aus, bevor Sie mit Schritt 2 fortfahren.

### Schritt 2: Manuelle Installation abschließen <a name="step2"></a>

> [!success]
>
> Bevor Sie mit der Installation fortfahren, leeren Sie den Cache Ihres Browsers, um Fehler zu vermeiden.
>

#### 2.1 WordPress im Browser öffnen

Geben Sie Ihren Domainnamen in die Adresszeile Ihres Webbrowsers ein.

Wenn die Quelldateien korrekt im Wurzelverzeichnis platziert wurden, erscheint die Seite zur Auswahl der Sprache für WordPress.

![hosting](/pages/assets/screens/other/cms/wordpress/installation-select-language.png){.thumbnail}

Wählen Sie die Sprache für die Website aus und klicken Sie auf `Weiter`{.action}.

#### 2.2 WordPress mit Ihrer Datenbank verbinden

WordPress fragt nun nach den Login-Daten für Ihre Datenbank.

![hosting](/pages/assets/screens/other/cms/wordpress/installation-start.png){.thumbnail}

Halten Sie die Zugangsdaten für Ihre Datenbank bereit. (Sie können bei Bedarf **Schritt 1.4** des Tutorials zur [manuellen Installation eines CMS](/pages/web_cloud/web_hosting/cms_manual_installation) verwenden). Klicken Sie auf `Let's go!`{.action}, um fortzufahren.

Folgende Seite wird angezeigt:

![hosting](/pages/assets/screens/other/cms/wordpress/installation-config-db.png){.thumbnail}

Geben Sie die angeforderten Informationen zur Datenbank ein:

- Database name: Dieser Name wurde bei der Erstellung der Datenbank im [OVHcloud Kundencenter](/links/manager) definiert.

- Database username: Dieser ist identisch mit dem Datenbanknamen, wenn Sie eine im Webhosting inkludierte Datenbank verwenden. Für Datenbanken, die mit Web Cloud Databases erstellt wurden, lesen Sie die Informationen in **Schritt 1.4** des Tutorials zur [manuellen Installation eines CMS](/pages/web_cloud/web_hosting/cms_manual_installation).

- Database password: Es wurde Ihnen bei der Erstellung der Datenbank per E-Mail gesendet. Möglicherweise haben Sie es inzwischen geändert.

- Database host: Der Servername Ihrer Datenbank, ebenfalls in der Installationsmail enthalten und einsehbar in Ihrem OVHcloud Kundencenter. 

> [!primary]
> 
> - Der Servername einer Datenbank, die in einem Webhosting inklusive ist, hat regulär folgendes Format: `DatenbankName.mysql.db`. 
>
> - Der Servername einer Web Cloud Databases Datenbank leitet sich von Ihrer OVHcloud Kundenkennung ab und hat folgendes Format: `OVHID(ohne-ovh)-XXX.eu.clouddb.ovh.net` wobei  **XXX** für die Referenz Ihrer Web Cloud Databases Instanz steht.
>

- Table prefix: Wenn die Installation mit einer neuen Datenbank erfolgt, geben Sie ein Präfix Ihrer Wahl ein. Wenn Sie eine Datenbank eingeben, die bereits von einer anderen Website verwendet wird, lesen Sie die Informationen in **Schritt 1.4** des Tutorials zur [manuellen Installation eines CMS](/pages/web_cloud/web_hosting/cms_manual_installation), um kein in Ihrer Datenbank bereits verwendetes Tabellenpräfix einzugeben.

Klicken Sie auf `Submit`{.action}, um die Verbindungsinformationen zur Datenbank zu bestätigen.

Wenn alle Eingaben korrekt waren, erscheint folgende Seite:

![hosting](/pages/assets/screens/other/cms/wordpress/installation-step-after-db-1.png){.thumbnail}

Klicken Sie auf `Run the installation`{.action}.

#### 2.3 Administrator-Zugang zum Backend von WordPress einrichten

Nach der Installation fragt WordPress nach Informationen zu Ihrer künftigen Website, und erstellt Ihren Administrator-Zugang.

Dieser ermöglicht Ihnen den Zugriff auf den Verwaltungsbereich Ihres WordPress CMS (Backend).

![hosting](/pages/assets/screens/other/cms/wordpress/installation-config-admin-user.png){.thumbnail}

Geben Sie die angeforderten Informationen ein:

- Site title: Geben Sie den Titel Ihrer Website ein.
- Username: Legen Sie die Administrator-Kennung Ihres CMS fest.
- Password: Legen Sie ein Passwort für diese Administrator-Kennung fest.
- Your Email: Geben Sie eine gültige E-Mail-Adresse ein.
- Search engine visibility: Haken Sie diese Option an, um Ihre Website von Suchmaschinenreferenzierungen auszuschließen.

Klicken Sie auf `Install WordPress`{.action}, sobald alles korrekt eingegeben ist.

#### 2.4 Die manuelle Installation abschließen und den Administrator-Zugang testen

Die Installation ist vollständig, wenn folgende Seite angezeigt wird:

![hosting](/pages/assets/screens/other/cms/wordpress/installation-successfull.png){.thumbnail}

Klicken Sie auf den Button `Log in`{.action}, um den Zugriff auf den Verwaltungsbereich Ihres neuen WordPress mit den zuvor in Schritt 3.3 erstellten Login-Daten zu testen.

> [!primary]
>
> Die OVHcloud Teams bieten keinen Support für externe Software wie WordPress und können Ihnen nicht bei der Verwendung oder Konfiguration Ihres WordPress CMS weiterhelfen.
>
> Wenden Sie sich für Unterstützung an die WordPress Community.
>

Wenn Sie eingeloggt sind, erscheint folgende Seite:

![hosting](/pages/assets/screens/other/cms/wordpress/admin-interface.png){.thumbnail}

> [!success]
>
> Sie können nun mit der Erstellung des Inhalts Ihrer WordPress Website beginnen!
>

## Weiterführende Informationen <a name="go-further"></a>

[Offizielle Website WordPress](https://wordpress.org)

Kontaktieren Sie für spezialisierte Dienstleistungen (SEO, Web-Entwicklung etc.) die [OVHcloud Partner](/links/partner).

Wenn Sie Hilfe bei der Nutzung und Konfiguration Ihrer OVHcloud Lösungen benötigen, beachten Sie unsere [Support-Angebote](/links/support).

Treten Sie unserer [User Community](/links/community) bei.