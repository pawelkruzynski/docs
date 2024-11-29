---
title: Was tun, wenn eine “Index of“-Seite angezeigt wird?
excerpt: Erfahren Sie hier, wie Sie Ihre Website wieder online bringen, wenn eine “Index of“-Seite angezeigt wird
updated: 2023-05-04
---

## Ziel 

Eine **Index of**-Seite erscheint in mindestens einem der folgenden Fälle:

- Ihr Domainname ist in der [Multisite-Konfiguration](/pages/web_cloud/web_hosting/multisites_configure_multisite) nicht korrekt auf Ihr Zielverzeichnis eingestellt.
- Das Zielverzeichnis, auf das Ihr Domainname verweist, enthält keine Datei namens **index.html** oder **index.php**.

![index_of](/pages/assets/screens/other/browsers/errors/index-of.png){.thumbnail}

**Diese Anleitung erklärt, wie Sie die Anzeige einer "Index of"-Seite korrigieren.**

> [!warning]
> OVHcloud stellt Ihnen Dienstleistungen zur Verfügung, für deren Konfiguration und Verwaltung Sie die alleinige Verantwortung tragen. Es liegt somit bei Ihnen, sicherzustellen, dass diese ordnungsgemäß funktionieren.
> 
> Diese Anleitung soll Sie bei allgemeinen Aufgaben bestmöglich unterstützen. Dennoch empfehlen wir Ihnen, falls Sie Hilfe brauchen, einen [spezialisierten Dienstleister](/links/partner) zu kontaktieren und/oder Ihre Fragen in der OVHcloud Community zu stellen. Leider können wir Ihnen für administrative Aufgaben keine weitergehende technische Unterstützung anbieten. Weitere Informationen finden Sie am [Ende dieser Anleitung](#go-further).
>

## Voraussetzungen

- Sie verfügen über einen [Domainnamen](/links/web/domains).
- Sie haben ein [OVHcloud Webhosting](/links/web/hosting) in Ihrem Kunden-Account.
- Sie haben Zugriff auf Ihr [OVHcloud Kundencenter](/links/manager).

## In der praktischen Anwendung

### Den Ursprung der "Index of"-Seite verstehen

Über die `Multisite`-Konfiguration Ihres Hostings wird Ihr Domainname mit einem Zielverzeichnis im [FTP-Speicherplatz](/pages/web_cloud/web_hosting/ftp_connection) Ihres Webhostings verknüpft. Dies geschieht über den Tab [Multisite](/pages/web_cloud/web_hosting/multisites_configure_multisite) Ihres Webhostings in Ihrem [OVHcloud Kundencenter](/links/manager).

Die Seite "**Index of**" ist ein Anzeichen dafür, dass Ihr Verzeichnis keine Indexdatei, also **index.php** oder **index.html** enthält. Eine solche Datei repräsentiert die Startseite bzw. den Einstiegspunkt Ihrer Website. Der Name dieser Datei ist standardisiert.

Ihr Domainname muss daher im Bereich `Multisite`{.action} Ihres Webhostings mit dem Wurzelverzeichnis verknüpft werden, das eine **index.php** oder **index.html** enthält.

> [!primary]
>
> Wenn Sie Ihren Domainnamen temporär mit einem `Wurzelverzeichnis` verknüpfen möchten, das keine **index.php** oder **index.html** Datei enthält, können Sie verhindern, dass die Auflistung von Ordnern auf Ihrer Website angezeigt wird, indem Sie [diesem Tutorial](/pages/web_cloud/web_hosting/htaccess_what_else_can_you_do#verzeichnis-browsing-verhindern) folgen. Sie können auch den Zugang zu Ihren Ordnern [mit einem Passwort schützen](/pages/web_cloud/web_hosting/htaccess_protect_directory_by_password).
>
> Wir empfehlen Ihnen, einen [spezialisierten Dienstleister](/links/partner) zu kontaktieren, falls Sie Schwierigkeiten haben, diese Konfiguration einzurichten. Unsere Support-Teams sind nicht in der Lage, Sie bei Änderungen an der internen Programmierung Ihrer Webseite zu unterstützen.

### Die häufigste Ursache einer "Index of"-Seite beheben

Sie haben die Dateien Ihrer Website **mydomain.ovh** per [FTP](/pages/web_cloud/web_hosting/ftp_connection) in den `www`-Ordner Ihres OVHcloud Webhostings importiert. Ihr Domainname ist jedoch nicht mit diesem Ordner in der Spalte `Wurzelverzeichnis` Ihrer `Multisite`-Konfiguration verknüpft.

![index_multisite](/pages/assets/screens/control_panel/product-selection/web-cloud/web-hosting/multisite/root-folders-empty.png){.thumbnail}

Ändern Sie das `Wurzelverzeichnis`, indem Sie in der Zeile des betreffenden Domainnames auf die Schaltfläche `...`{.action} klicken und dann `Domain bearbeiten`{.action} auswählen.

![modify_domain](/pages/assets/screens/control_panel/product-selection/web-cloud/web-hosting/multisite/modify-domain.png){.thumbnail}

Führen Sie im neuen Fenster die folgenden Aktionen aus:

- Setzen Sie einen Haken bei `Auch die Subdomain www.mydomain.ovh ändern`{.action} (1).
- Geben Sie den Ordnernamen Ihrer Webseite, der die **index.php** oder **index.html** enthält, als `Wurzelverzeichnis` (2) an.
- Klicken Sie auf `Weiter`{.action} (3).

![change_root_folder](/pages/assets/screens/control_panel/product-selection/web-cloud/web-hosting/multisite/change-root-folder-step-1.png){.thumbnail}

> [!primary]
>
> Den `www`-Ordner als `Wurzelverzeichnis` zu verwenden ist nicht zwingend. Sie können Ihre Webseite auch in einem anderen Ordner innerhalb Ihres [FTP-Speicherplatzes](/pages/web_cloud/web_hosting/ftp_connection) installieren.
>

Klicken Sie anschließend auf `Bestätigen`{.action}.

![modify_root_folder_confirm](/pages/assets/screens/control_panel/product-selection/web-cloud/web-hosting/multisite/change-root-folder-step-2.png){.thumbnail}

Sie erhalten das Ergebnis innerhalb weniger Minuten (denken Sie daran, Ihren Browser zu aktualisieren) wie in der folgenden Abbildung dargestellt:

![multisite_modified](/pages/assets/screens/control_panel/product-selection/web-cloud/web-hosting/multisite/root-folders-full-www.png){.thumbnail}

Überprüfen Sie, ob Ihre Webseite korrekt angezeigt wird. Wenn dies nicht der Fall ist, starten Sie Ihr Gerät neu und leeren Sie den Cache Ihres Browsers.

Stellen Sie außerdem sicher, dass eine Datei namens **index.php** oder **index.html** in Ihrem Zielverzeichnis vorhanden ist.

## Weiterführende Informationen <a name=“go-further“></a>

[Die häufigsten Fehler bei 1-Klick-Modulen beheben](/pages/web_cloud/web_hosting/diagnostic_errors_module1clic)

[Fehler “Seite nicht installiert” beheben](/pages/web_cloud/web_hosting/multisites_website_not_installed)

[Mehrere Websites auf einem Webhosting einrichten](/pages/web_cloud/web_hosting/multisites_configure_multisite)

Kontaktieren Sie für spezialisierte Dienstleistungen (SEO, Web-Entwicklung etc.) die [OVHcloud Partner](/links/partner).

Wenn Sie Hilfe bei der Nutzung und Konfiguration Ihrer OVHcloud Lösungen benötigen, beachten Sie unsere [Support-Angebote](/links/support).

Treten Sie unserer [User Community](/links/community) bei.