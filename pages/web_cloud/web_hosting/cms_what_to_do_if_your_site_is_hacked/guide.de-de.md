---
title: "Anwendungsbeispiele - Ihre Website ist von einem Hack betroffen"
excerpt: "Diese Anleitung erklärt, wie Sie Ihre gehackte Website reparieren"
updated: 2022-11-15
---

## Ziel

Dieses Tutorial beschreibt notwendige Maßnahmen, wenn Sie feststellen, dass Ihre Website gehackt wurde. Befolgen Sie die unten aufgeführten 4 Schritte nacheinander, um Ihre Webseite wiederherzustellen.

Ein Hack kann diverse Folgen haben (nicht erschöpfende Liste):

- Ihre Website erscheint nicht mehr oder nur teilweise, ohne Änderungen (FTP, SQL, DNS) Ihrerseits.
- Ihre Website wird auf eine andere Website weitergeleitet.
- Ihre Website zeigt unerwünschtes Verhalten in Form von Werbeeinblendungen (Pop-ups, Fehlermeldungen etc.).
- Die Datenbank Ihrer Website ist plötzlich gefüllt.
- Sie erhalten über Ihr Hosting SPAM, der von infizierten Skripte generiert wird.

**Dieses Tutorial erklärt, wie Sie Ihre gehackte Website wiederherstellen können.**

> [!warning]
> OVHcloud stellt Ihnen Dienstleistungen zur Verfügung, für deren Konfiguration und Verwaltung Sie die alleinige Verantwortung tragen. Es liegt somit bei Ihnen, sicherzustellen, dass diese ordnungsgemäß funktionieren.
> 
> Dieses Tutorial soll Sie bei allgemeinen Aufgaben bestmöglich unterstützen. Dennoch empfehlen wir Ihnen, falls Sie Hilfe brauchen, einen [spezialisierten Dienstleister](/links/partner) zu kontaktieren oder Ihre Fragen in der OVHcloud Community zu stellen. Leider können wir Ihnen für administrative Aufgaben keine weitergehende technische Unterstützung anbieten. Weitere Informationen finden Sie am [Ende dieser Anleitung](#go-further).
>

## Voraussetzungen

- Ihre Webseite befindet sich auf einem [OVHcloud Webhosting](/links/web/hosting).
- Sie haben Zugriff auf Ihr [OVHcloud Kundencenter](/links/manager).

## In der praktischen Anwendung

Das Hacken einer Website hängt systematisch mit **mindestens** einem der folgenden Punkte zusammen:

- Die Website-Software wurde länger nicht aktualisiert.
- Malware auf einem der Geräte, die Sie zur Verwaltung Ihrer Website verwenden.
- Installation von "inoffiziellen" Plugins oder Themes, insbesondere wenn Sie ein Content Managment System (CMS) wie WordPress, Joomla!, PrestaShop oder Drupal verwenden.
- Passwörter (FTP, SQL, CMS-Backend, etc.) sind zu kurz oder zu generisch, insbesondere wenn diese nie geändert werden.
- Ein Skript Ihrer Website öffnet absichtlich Ports auf Ihrem Webhosting, **ohne** zu überprüfen, was diese Ports empfangen.
- Die FTP-Zugangsrechte ("CHMOD") des Hostings sind nicht strikt genug.

**Der Hack einer Website rührt nicht von einer Sicherheitslücke im Webhosting her.** Nur die Skripte/Dateien, die auf dem Webhosting gehostet werden, können dem Hosting Anweisungen erteilen. Sie können veranlassen, standardmäßig bestimmte Ports zu öffnen oder bestimmte Aktionen durchzuführen.<br>
Die Skripte enthalten Befehle, die das Hosting dann ausführt.

## Schritt 1: Scannen Sie alle Ihre Geräte

Führen Sie eine Anti-Virus- und Anti-Malware-Analyse aller Geräte durch (PC, Mac, Smartphone, Tablet, etc.), die zur Administration oder Verwaltung Ihrer Website genutzt werden.

> [!warning]
>
> Wenn Sie Geräte verwenden, die unter *Linux*, *Mac OS* oder anderen Betriebssystemen laufen, bei denen allgemein davon ausgegangen wird, dass geringes Risiko für  Virus- oder Malware-Befall besteht, **führen Sie trotzdem diese Analyse durch**.
>
> **Kein Betriebssystem ist gegen schädliche Software oder Viren immun.**
>

> [!success]
>
> Wir empfehlen, für jedes Ihrer Geräte mehrere Anti-Virus/Anti-Malware (kostenlos oder kostenpflichtig) zu verwenden.
> Manche Viren oder Malware können je nach verwendeter Anti-Viren-Software resistent sein.
> Es gibt Varianten von Anti-Virus/Anti-Malware, die Sie "lokal" auf Ihrem Gerät installieren oder direkt online über Internet verwenden können.
>

Wenn ein Virus oder Schadsoftware gefunden wird, führen Sie eine Bereinigung mit Ihrer Anti-Virus/Anti-Malware-Software durch, **bevor** Sie zum nächsten Schritt übergehen.

### Schritt 2: Passwörter ändern <a name="step2"></a> 

Wenn eine Website gehackt wurde, ändern Sie alle zugehörigen Passwörter.

Für OVHcloud Dienste verwenden Sie unsere Dokumentation:

- [Passwort für den Zugang zu Ihrer OVHcloud Kundenkennung ändern](/pages/account_and_service_management/account_information/manage-ovh-password)
- [Den Zugang zu Ihrem OVHcloud Kundencenter mit Zwei-Faktor-Authentifizierung absichern](/pages/account_and_service_management/account_information/secure-ovhcloud-account-with-2fa)
- [Passwort für den Zugang zum FTP-Speicherplatz Ihres Webhostings ändern](/pages/web_cloud/web_hosting/ftp_change_password)
- [Passwort für den Zugriff auf Ihre Datenbank ändern](/pages/web_cloud/web_hosting/sql_change_password)

Wir empfehlen Ihnen auch die Verwendung eines [Passwort-Managers](/pages/account_and_service_management/account_information/manage-ovh-password#einen-passwort-manager-verwenden).

> [!warning]
> 
> Wenn Sie das Passwort Ihrer Datenbank ändern, vergessen Sie nicht, auch das Passwort in der Konfigurationsdatei Ihrer Website zu aktualisieren. Andernfalls wird die Verbindung zwischen der Datenbank und den Dateien im FTP-Speicherplatz Ihres Webhostings unterbrochen und Ihre Website wird einen Datenbankverbindungsfehler anzeigen.
>

> [!primary]
>
> Wenn Sie ein CMS wie WordPress, Joomla!, PrestaShop oder Drupal verwenden, lesen Sie die offizielle Dokumentation Ihres CMS, um das Passwort für den Zugang zum Verwaltungsbereich Ihres CMS (Backend) zu ändern.
>

### Schritt 3: Suche nach böswilligen Dateien und Sicherheitslücken

> [!warning]
>
> Wenn Sie Schwierigkeiten haben, die unten beschriebenen Aktionen durchzuführen, wenden Sie sich an einen [spezialisierten Dienstleister](/links/partner) für Cyber-Sicherheit.
>

Folgen Sie unserer Anleitung zu [Statistiken und Logs Ihres Webhostings](/pages/web_cloud/web_hosting/logs_and_statistics), um in den "Web"-Logs nach den entsprechenden Einträgen zu suchen, die Schadcode in die Website injizieren.

Beginnen Sie mit der Suche ab dem Datum, an dem Sie den Hack bemerkt haben, und gehen Sie dann durch die Log-History.

Suchen Sie nach ungewöhnlichen "POST"-Anfragen. In der Regel haben Schaddateien alphanumerische Namen ohne besondere Bedeutung (**Beispiele**: az78e4jFn.txt, oij8bh4.html, udh73hd45.php, mlkjc23d.js, etc.).

Finden Sie die IP-Adresse, die entsprechende Anfragen ausgeführt hat. Suchen Sie anschließend in Ihren Logs nach dieser Adresse, um alle von dieser IP für Ihre Website angeforderten Aktionen einzusehen.

> [!primary]
>
> Im Allgemeinen rufen mehrere IP-Adressen im gleichen Zeitraum die schädlichen Skripte auf, die nach dem Hack vorhanden sind.
> Analysieren Sie alle Logs Ihres Hostings.
>

Verfolgen Sie so die Sicherheitslücken in Ihrer Website nach und listen Sie dabei die schädlichen Dateien auf, auf die Sie stoßen.

> [!success]
>
> Über einschlägige Webseiten (die nicht von OVHcloud verwaltet werden) können Sie Informationen zu angreifenden IPs abrufen. Sie können einen dieser Dienste verwenden, um Informationen wie den IP-Anbieter, dessen Geolokalisierung, die Verwaltung usw. abzurufen.
>
> Wenn Sie absolut sicher sind, dass es sich um eine unerwünschte IP-Adresse handelt, können Sie den Zugang zu Ihrem Hosting sperren, indem Sie unsere Dokumentation zu den [Zugriffsbeschränkungen über die Datei ".htaccess"](/pages/web_cloud/web_hosting/htaccess_how_to_block_a_specific_ip_address_from_accessing_your_website) befolgen.
> 

### Schritt 4: Schadcode entfernen und Sicherheitslücken beheben

Für diesen Schritt sind drei Fallbeispiele möglich.

> [!alert]
>
> **Wichtig**: In jedem Fall könnte ein Hacker, wenn Sie Schadcode entfernen, aber Sicherheitslücken nicht schließen, diese erneut ausnutzen, um Schadcode wieder auf Ihrem Hosting zu platzieren. Er könnte sogar eine neue Hintertür einrichten.
>
> Die Wiederherstellung zum Zustand vor dem Hack erfordert ein **sofortiges** Update und die Durchführung eines **Sicherheitsaudits**, um alle Sicherheitslücken zu identifizieren.
>
T
#### Fall 1 - OVHcloud verfügt über ein Backup Ihrer Website (FTP Speicherplatz und Datenbank)

Abhängig vom Datum des Vorfalls auf Ihrem Hosting (weniger als 14 Tage) kann OVHcloud Ihnen ein (außervertragliches) Backup zur Verfügung stellen.

Lesen Sie hierzu unsere 3 Anleitungen:

- [FTP-Speicherplatz Ihres Webhostings wiederherstellen](/pages/web_cloud/web_hosting/ftp_save_and_backup)
- [SQL-Backup Ihrer Datenbank abrufen](/pages/web_cloud/web_hosting/sql_database_export)
- [SQL-Backup in Ihre Datenbank importieren](/pages/web_cloud/web_hosting/sql_importing_mysql_database)
 
Gleichen Sie die Zeitpunkte für die Wiederherstellung Ihres FTP-Speicherplatzes und Ihrer SQL-Datenbank so weit wie möglich an.

>[!warning]
>
> OVHcloud setzt Sicherheitsroboter ein, die von Ihrem Hosting ausgehende Angriffe erkennen können. Diese deaktivieren Ihr Hosting und und informieren Sie per E-Mail, dass Ihr Hosting deaktiviert wurde.
> Zusätzlich zu dieser E-Mail erscheint in der Regel eine "403 Forbidden" Fehlerseite, wenn Sie auf Ihre Website zugreifen.
>
> Wenn sich Ihr Hosting im Zustand "Disabled" befindet, wird auch die über Ihr [OVHcloud Kundencenter](/links/manager) verfügbare Option zur automatischen Wiederherstellung deaktiviert.
> Sie müssen eine "manuelle" Wiederherstellung Ihrer Website durchführen, die verbleibenden schadhaften Elemente entfernen und alle Sicherheitslücken in diesem Backup beheben. Dies muss durchgeführt werden, **bevor** das Hosting reaktiviert wird.
>
> Um das Webhosting wiederherzustellen, befolgen Sie die Anweisungen in Schritt 4 [dieser Anleitung](/pages/web_cloud/web_hosting/diagnostic_403_forbidden).
>

Ihre Website sollte wieder verfügbar sein, wenn diese Aktionen korrekt durchgeführt wurden.

#### Fall 2 - Sie verfügen über Ihr eigenes Backup vor dem Hack

Lesen Sie hierzu unsere 2 Anleitungen:

- [FTP-Speicherplatz Ihres Webhostings wiederherstellen](/pages/web_cloud/web_hosting/ftp_save_and_backup)
- [SQL Backup in Ihre Datenbank importieren](/pages/web_cloud/web_hosting/sql_importing_mysql_database)

>[!warning]
>
> OVHcloud setzt Sicherheitsroboter ein, die von Ihrem Hosting ausgehende Angriffe erkennen können. Diese deaktivieren Ihr Hosting und und informieren Sie per E-Mail, dass Ihr Hosting deaktiviert wurde.
> Zusätzlich zu dieser E-Mail erscheint in der Regel eine "403 Forbidden" Fehlerseite, wenn Sie auf Ihre Website zugreifen.
>
> Wenn sich Ihr Hosting im Zustand "Disabled" befindet, führen Sie eine "manuelle" Wiederherstellung Ihrer Website durch, beseitigen Sie die verbleibenden schadhaften Elemente und beheben Sie alle Sicherheitslücken in diesem Backup. Dies muss durchgeführt werden, **bevor** das Hosting reaktiviert wird.
>
> Um das Webhosting wiederherzustellen, befolgen Sie die Anweisungen in Schritt 4 [dieser Anleitung](/pages/web_cloud/web_hosting/diagnostic_403_forbidden).
>

Ihre Website sollte wieder verfügbar sein, wenn diese Aktionen korrekt durchgeführt wurden.

#### Fall 3 - Es ist kein Backup für Ihre Website verfügbar

In [Schritt 2](#step2) dieser Anleitung müssen Sie die zuvor erfassten Dateien und Code manuell löschen und die Sicherheitslücken Ihrer Website korrigieren.

Um sich mit dem Speicherplatz Ihres Hostings zu verbinden, lesen Sie [unsere Anleitung](/pages/web_cloud/web_hosting/ftp_connection).

>[!warning]
>
> OVHcloud setzt Sicherheitsroboter ein, die von Ihrem Hosting ausgehende Angriffe erkennen können. Diese deaktivieren Ihr Hosting und und informieren Sie per E-Mail, dass Ihr Hosting deaktiviert wurde.
> Zusätzlich zu dieser E-Mail erscheint in der Regel eine "403 Forbidden" Fehlerseite, wenn Sie auf Ihre Website zugreifen.
>
> Wenn sich Ihr Hosting im Zustand "Disabled" befindet, führen Sie eine "manuelle" Wiederherstellung Ihrer Website durch, beseitigen Sie die verbleibenden schadhaften Elemente und beheben Sie alle Sicherheitslücken in diesem Backup. Dies muss durchgeführt werden, **bevor** das Hosting reaktiviert wird.
>
> Um das Webhosting wiederherzustellen, befolgen Sie die Anweisungen in Schritt 4 [dieser Anleitung](/pages/web_cloud/web_hosting/diagnostic_403_forbidden).
>

Ihre Website sollte wieder verfügbar sein, wenn diese Aktionen korrekt durchgeführt wurden.

### Schritt 5: Ihre Website aktualisieren

Aktualisieren Sie Ihre Website im Hinblick auf Quellcode, Sicherheitseinstellungen und verwendete Sprachversionen (insbesondere PHP).

Überprüfen Sie die FTP-Zugriffsrechte ("CHMOD") für alle in Ihrem Speicherplatz gehosteten Ordner und Dateien.
Standardmäßig empfehlen wir, keine höheren "CHMOD"-Rechte als **705** für Ordner und **604** für Dateien zu verwenden.

Weitere Informationen zu den "CHMOD"-Rechten finden Sie im Abschnitt "Nützliche Informationen" unseres [Tutorials zur Nutzung des FTP-Clients Filezilla](/pages/web_cloud/web_hosting/ftp_filezilla_user_guide#useful-information).

Wenn Sie ein CMS verwenden (Wordpress, Joomla!, PrestaShop, Drupal, etc.), aktualisieren Sie Ihre Plugins, Themes und das CMS selbst.
Verwenden Sie nur "offizielle" Plugins/Themes und halten Sie Ihre Website so regelmäßig und umfassend wie möglich auf dem neuesten Stand.

Sichern Sie Ihre Kontaktformulare mindestens mit einem "Captcha"-System ab, um zu vermeiden, dass Bots SPAM über diese Methode versenden. Wenn die "mail()"-Funktion von PHP ebenfalls auf Ihrem Hosting gesperrt wurde, lesen Sie hierzu [unsere Anleitung](/pages/web_cloud/web_hosting/mail_function_script_records), um die Sperrung zu beheben.

Lesen Sie auch unsere Anleitung zur [Sicherung Ihrer Website](/pages/web_cloud/web_hosting/secure_your_website), um das Risiko eines erneuten Hacks möglichst gering zu halten.

## Weiterführende Informationen <a name="go-further"></a>

[Mit dem Speicherplatz Ihres Webhostings verbinden](/pages/web_cloud/web_hosting/ftp_connection)

[Konfiguration Ihres Webhostings ändern](/pages/web_cloud/web_hosting/configure_your_web_hosting)

[Application Firewall aktivieren](/pages/web_cloud/web_hosting/multisites_activating_application_firewall)

[Die Performance Ihrer Website optimieren](/pages/web_cloud/web_hosting/optimise_your_website_performance)

Kontaktieren Sie für spezialisierte Dienstleistungen (SEO, Web-Entwicklung etc.) die [OVHcloud Partner](/links/partner).

Wenn Sie Hilfe bei der Nutzung und Konfiguration Ihrer OVHcloud Lösungen benötigen, beachten Sie unsere [Support-Angebote](/links/support).

Treten Sie unserer [User Community](/links/community) bei.