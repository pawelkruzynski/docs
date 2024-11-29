---
title: "Die Sicherheit Ihrer Website optimieren"
excerpt: "Erfahren Sie hier, wie Sie die Sicherheit Ihrer Website erhöhen"
updated: 2024-01-29
---

## Ziel 

Diese Anleitung bietet Ihnen grundlegendes Wissen, um die Verfügbarkeit Ihrer Dienstleistungen zu gewährleisten, die Integrität Ihrer Daten zu schützen und den Zugang zu Ihren Lösungen zu sichern. Die Maßnahmen wie hier beschrieben betreffen nur Webseiten, die auf OVHcloud [Webhosting-Diensten](/links/web/hosting) gehostet werden.

Die nachstehenden Empfehlungen sind nach abnehmender Wichtigkeit und zunehmendem technischen Schwierigkeitsgrad angeordnet. Die zuerst beschriebenen Schritte sind also am wichtigsten. Die Sicherheit Ihrer Website kann danach bemessen werden, welches Element am wenigsten geschützt ist. Wir empfehlen deshalb, möglichst alle Maßnahmen durchzuführen.

Sollten Sie jedoch Schwierigkeiten haben, einige der hier beschriebenen Operationen durchzuführen, wenden Sie sich an die [OVHcloud Community](/links/community) oder [unsere Partner](/links/partner).

**Diese Anleitung erklärt, wie Sie Ihre Website schützen.**

> [!warning]
> OVHcloud stellt Ihnen Dienstleistungen zur Verfügung, für deren Konfiguration und Verwaltung Sie die alleinige Verantwortung tragen. Es liegt somit bei Ihnen, sicherzustellen, dass diese ordnungsgemäß funktionieren.
> 
> Diese Anleitung soll Sie bei allgemeinen Aufgaben bestmöglich unterstützen. Dennoch empfehlen wir Ihnen, falls Sie Hilfe brauchen, einen [spezialisierten Dienstleister](/links/partner) zu kontaktieren und/oder Ihre Fragen in der OVHcloud Community zu stellen. Leider können wir Ihnen für administrative Aufgaben keine weitergehende technische Unterstützung anbieten. Weitere Informationen finden Sie am [Ende dieser Anleitung](#go-further).
>

## Voraussetzungen

- Sie haben ein [OVHcloud Webhosting](/links/web/hosting) in Ihrem Kunden-Account.
- Sie haben Zugriff auf Ihr [OVHcloud Kundencenter](/links/manager).
- Sie verfügen über die [Login-Daten](/pages/web_cloud/web_hosting/ftp_connection#schritt-1-erforderliche-verbindungsinformationen-abrufen) für den Speicherplatz Ihres Hostings.
- Sie haben Zugriff auf das [Admin-Interface für Ihre Webseite](https://wordpress.org/support/article/first-steps-with-wordpress/){.external}.

## In der praktischen Anwendung

### Schritt 1: Überprüfen Sie die Sicherheit Ihrer lokalen Systeme <a name="local"></a>

Dieser erste Schritt ist von entscheidender Bedeutung. Die Infektion Ihrer Geräte mit böswilliger Software kann dazu führen, dass Angreifer Zugriff auf alle Ihre Tastatur-Eingaben haben. Jegliche Login-Daten, die Sie für die das OVHcloud Kundencenter oder dem Verwaltungsinterface Ihrer Website verwenden, könnten somit beeinträchtigt sein.

Darüber hinaus kann das an Bedeutung zunehmende Phänomen "[Ransomware](https://www.bsi.bund.de/DE/Themen/Verbraucherinnen-und-Verbraucher/Cyber-Sicherheitslage/Methoden-der-Cyber-Kriminalitaet/Schadprogramme/Ransomware/ransomware_node.html){.external}" (2020 in Frankreich etwa 400 Fälle) nicht nur zur Verschlüsselung Ihrer persönlichen Daten führen, sondern auch Ihre Geschäftstätigkeiten unterbrechen, da Ihre Software und Hardware nicht mehr funktional sind.

Überprüfen Sie zunächst die Sicherheit Ihres Windows-, Mac- oder Linux-Systems:

- Überprüfen Sie Ihr Betriebssystem und Ihre Software auf Updates.
- Führen Sie einen vollständigen Scan aus, nachdem Sie Ihr Anti-Virus-/Anti-Malware-Programm aktualisiert haben.
- Ändern Sie regelmäßig das Administratorpasswort Ihrer Systeme (für mehr Informationen zu angemessenen Passwörtern folgen Sie den Anweisungen in [dieser Anleitung](/pages/account_and_service_management/account_information/all_about_username#ein-starkes-und-einzigartiges-passwort-erstellen)).

### Schritt 2: Ihr OVHcloud Kundencenter absichern

Um Ihren Kunden-Account zu schützen, aktivieren Sie die [Zwei-Faktor-Authentifizierung](/pages/account_and_service_management/account_information/secure-ovhcloud-account-with-2fa) und folgen Sie den Anweisungen in dieser [Anleitung](/pages/account_and_service_management/account_information/all_about_username).

Denken Sie daran, [Ihre Account-Informationen](/pages/account_and_service_management/account_information/all_about_username#personliche-daten-im-account-verwalten) zu aktualisieren und eine **Zweit-E-Mail-Adresse** hinzuzufügen.<br>
Wenn Ihre Zugangsdaten verloren gehen und/oder die Haupt-E-Mail-Adresse Ihres OVHcloud Kunden-Accounts nicht verfügbar ist, sind eine Backup-E-Mail-Adresse sowie aktuelle persönliche Daten wichtig, um Ihnen schnell weiterhelfen zu können.

### Schritt 3: Führen Sie regelmäßig Sicherungen Ihrer Seite durch <a name="backup"></a>

> [!primary]
>
> Die regelmäßige Sicherung Ihrer Daten ist unabhängig vom betroffenen Angebot die wichtigste Maßnahme im Bereich der IT-Sicherheit. Es wird immer möglich sein, eine Software neu zu installieren oder ein neues Gerät zu bestellen, aber es ist sehr schwierig, Daten nach deren Verlust wiederherzustellen.
>
> OVHcloud führt regelmäßig Sicherungen aller Daten auf der Infrastruktur durch. Allerdings kann ein Fehler bei der Handhabung wie z.B. eine Löschung von Datenbanken im Produktivbetrieb  oder die Nichtverlängerung Ihrer Dienste zum endgültigen Verlust Ihrer Daten führen.
>

Speichern Sie zunächst die Daten Ihrer Datenbank (FTP **UND** Datenbank-Dateien), indem Sie die Anweisungen in [dieser Anleitung](/pages/web_cloud/web_hosting/exporter-son-site-web) befolgen. Importieren Sie diese auf Ihrem lokalen Gerät oder einem externen Datenträger, zum Beispiel auf einem NAS oder einem USB Laufwerk.

Webseitensoftware (CMS) bietet die Möglichkeit, automatische Backup-Plugins zu installieren.<br>
Konsultieren Sie die offiziellen Foren Ihres bevorzugten CMS oder kontaktieren Sie die [OVHcloud Community](/links/community) zu diesem Thema.

### Schritt 4: Betrügerische E-Mails erkennen

Phishing-E-Mails stellen ebenfalls eine Bedrohung für die Sicherheit Ihrer Website dar, da sie Schadsoftware enthalten deren Installation auslösen können. Lesen Sie in [dieser Anleitung](/pages/account_and_service_management/account_information/phishing_care), wie Sie diese erkennen und sich davor schützen können.

### Schritt 5: Einrichtung der automatischen Verlängerung

Wenn Ihre Dienste nicht verlängert werden, ist OVHcloud gesetzlich verpflichtet, nach Ablauf Ihres Abonnements alle Daten aus Ihrem Hosting-Angebot sowie alle zugehörigen Backups vollständig zu löschen. Wir senden unseren Kunden Ablaufbenachrichtigungen, um sie an die Verlängerungsfristen zu erinnern.<br>
Diese E-Mails können jedoch in Ihren Spam-Ordnern eingehen, oder die primäre E-Mail-Adresse Ihres OVHcloud Kunden-Accounts ist möglicherweise unverfügbar.

Wenn Ihre Website ein wichtiger Teil Ihrer Geschäftstätigkeiten ist, [aktivieren Sie die automatische Verlängerung](/pages/account_and_service_management/managing_billing_payments_and_services/how_to_use_automatic_renewal#ubersicht-meine-dienste-aufrufen) für alle Ihre OVHcloud Dienste.<br>
Wir empfehlen Ihnen auch, die **Gültigkeit der von Ihnen hinterlegten Zahlungsmittel** regelmäßig zu überprüfen.

### Schritt 6: Überprüfen, dass Ihre Website auf dem neuesten Stand ist

Prüfen Sie regelmäßig auf Updates für Ihre Website gemäß den Anweisungen in [dieser Anleitung](/pages/web_cloud/web_hosting/diagnostic_403_forbidden#22-ihre-website-aktualisieren).

Denken Sie auch daran, eine aktuelle Version von [PHP](/pages/web_cloud/web_hosting/configure_your_web_hosting) auf Ihrem Hosting zu verwenden.

### Schritt 7: HTTPS aktivieren

Ermöglichen Sie die verschlüsselte Verbindung zu Ihrer Website über das Protokoll **HTTPS** gemäß dieser [Anleitung](/pages/web_cloud/web_hosting/ssl-activate-https-website). Die Aktivierung dieses Protokolls erlaubt es, den Datenaustausch über Ihre Website zu verschlüsseln (insbesondere Angaben, die Benutzer in Formulare eingeben).

### Schritt 8: Formulare schützen

Eingabe-Formulare auf Webseiten sind bevorzugte Ziele von Hackern/Spammern. Schützen Sie Ihre Formulare vor Angriffen, indem Sie **CAPTCHA**-Plugins einrichten.

### Schritt 9: Sicherheitsplugin auf Ihrer Website einrichten

Fügen Sie Ihrer Website ein vom Herausgeber des CMS empfohlenes Sicherheitsplugin hinzu:

- [WordPress](https://wordpress.com/de/){.external}
- [Joomla](https://www.joomla.de/){.external}
- [Drupal](https://www.drupal.de/){.external}
- [PrestaShop](https://www.prestashop.com/de){.external}

### Schritt 10: Überprüfen Sie Ihr Webhosting auf schädliche Dateien

Loggen Sie sich hierzu in Ihrem [FTP-Speicherplatz](/pages/web_cloud/web_hosting/ftp_connection) ein. Es erfordert technische Kenntnisse, um kompromittierte Dateien auf Ihrem Hosting zu erkennen. Sollten Sie Schwierigkeiten haben, diese Überprüfung durchzuführen, wenden Sie sich an unsere [Partner](/links/partner).

Im Zweifelsfall können Sie auch die in [Schritt 1](#local) dieser Anleitung beschriebenen Überprüfungen durchführen und das [Passwort Ihres FTP-Bereichs ändern](/pages/web_cloud/web_hosting/ftp_change_password).

### Schritt 11: Testen Sie die Backups Ihrer Website

Die [Sicherungen](#backup) der Daten Ihrer Webseite (FTP-Dateien und Datenbanken) sollten regelmäßig durchgeführt werden. Es besteht aber keine Garantie, dass diese auch im Ernstfall Ihre Daten korrekt wiederherstellen können. Testen Sie auch die Sicherungen Ihrer Datenbank, um sicherzustellen, dass sie nicht korrupt sind.

Sie können diese Tests lokal durchführen, etwa indem Sie Ihre Daten einer Software wie [WAMP](https://www.wampserver.com/en/){.external} importieren. Achten Sie daher darauf, Ihre lokale Lösung so einzurichten, dass die Konfiguration in allen Punkten der unserer [Shared Hosting Server entspricht](https://webhosting-infos.hosting.ovh.net/).

Sie können auch in einem anderen Ordner Ihres Webhostings eine **Testversion** Ihrer Webseite erstellen (z.B.: test.meinedomain.tld). (Es ist hierbei möglich, ein Basistemplate zu verwenden).

### Schritt 12: Den Zugang zu Ihrer Website mit der Datei “.htaccess“ absichern

Die Datei “.htaccess“ ist eine Apache-Konfigurationsdatei (HTTP), die vom Webserver Ihres Webhostings ausgeführt wird. Sie dient u.a. folgenden Funktionen:

- [Blockieren des Zugriffs auf Ihre Website für bestimmte IP-Adressen](/pages/web_cloud/web_hosting/htaccess_how_to_block_a_specific_ip_address_from_accessing_your_website)
- [Verzeichnis oder Verwaltungsinterface Ihrer Website mit einer “.htpasswd“ Datei schützen](/pages/web_cloud/web_hosting/htaccess_protect_directory_by_password)
- [WordPress CMS schützen](/pages/web_cloud/web_hosting/htaccess_how_to_protect_wordpress)

## Weiterführende Informationen <a name="go-further"></a>

[Was tun, wenn Ihre WordPress Seite gehackt wurde?](/pages/web_cloud/web_hosting/cms_what_to_do_if_your_site_is_hacked)

[Was tun, wenn Ihr Hosting aus Sicherheitsgründen deaktiviert wurde?](/pages/web_cloud/web_hosting/diagnostic_403_forbidden)

Kontaktieren Sie für spezialisierte Dienstleistungen (SEO, Web-Entwicklung etc.) die [OVHcloud Partner](/links/partner).

Treten Sie unserer [User Community](/links/community) bei.