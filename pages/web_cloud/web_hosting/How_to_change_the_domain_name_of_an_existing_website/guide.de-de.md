---
title: "Anwendungsbeispiele - Domainnamen einer Website ändern"
excerpt: "Erfahren Sie hier, wie Sie den Domainnamen einer bestehenden Website ändern"
updated: 2022-10-25
---

## Ziel

Während der Lebensdauer Ihrer Website kann es vorkommen, dass Sie den zu deren Zugang verwendeten Domainnamen ändern müssen.<br>Der häufigste Fall ist eine Änderung des Unternehmensnamens.

In diesem Tutorial erklären wir Ihnen die wichtigsten Schritte, die Sie bei der Änderung des Domainnamen für den Besuch Ihrer Website unternehmen müssen.

**Diese Anleitung erklärt, wie Sie eine Website auf einen neuen Domainnamen umstellen.**

> [!warning]
> OVHcloud stellt Ihnen Dienstleistungen zur Verfügung, für deren Konfiguration und Verwaltung Sie die alleinige Verantwortung tragen. Es liegt somit bei Ihnen, sicherzustellen, dass diese ordnungsgemäß funktionieren.
> 
> Dieses Tutorial soll Sie bei allgemeinen Aufgaben bestmöglich unterstützen. Dennoch empfehlen wir Ihnen, falls Sie Hilfe brauchen, einen [spezialisierten Dienstleister](/links/partner) zu kontaktieren oder Ihre Fragen in der OVHcloud Community zu stellen. Leider können wir Ihnen für administrative Aufgaben keine weitergehende technische Unterstützung anbieten. Weitere Informationen finden Sie am [Ende dieser Anleitung](#go-further).
>

## Voraussetzungen

- Sie verfügen über einen [Domainnamen](/links/web/domains).
- Sie verfügen über ein [OVHcloud Webhosting](/links/web/hosting).
- Sie haben Zugriff auf Ihr [OVHcloud Kundencenter](/links/manager).

## In der praktischen Anwendung

> [!warning]
>
> Die Änderung des Domainnamens, über den auf Ihre Website zugegriffen wird, kann Auswirkungen auf deren SEO haben. 
> Achten Sie daher genau auf die Änderungen, die Sie vornehmen, und kontaktieren Sie bei Bedarf einen [spezialisierten Dienstleister](/links/partner) für SEO.
>

Um den Domainnamen für den Zugang zu Ihrer Website zu ändern, müssen mehrere Schritte in einer bestimmten Reihenfolge durchgeführt werden.

### Schritt 1: Die neue Domain auf Ihrem Webhosting <a name="step1"></a> deklarieren

Melden Sie Ihren neuen Domainnamen unter Verwendung unserer Dokumentation zum [Hinzufügen einer Multisite auf Ihrem Webhosting](/pages/web_cloud/web_hosting/multisites_configure_multisite). Aktivieren Sie auch die Subdomain `www`, wenn Sie möchten, dass Ihre Website auch unter `www.NeueDomain.tld`, zusätzlich zu `NeueDomain.tld` angezeigt wird.

Für Schritt 1 sind mehrere Bedingungen zu erfüllen:

- Ihre neue Domain muss auf dasselbe Wurzelverzeichnis verweisen wie die Domain, die derzeit für den Zugang zu Ihrer Website verwendet wird.
- Überprüfen Sie, ob Ihre neue Domain korrekt auf die IP-Adresse Ihres Webhostings verweist. Um die IP-Adresse abzurufen, loggen Sie sich in Ihr [OVHcloud Kundencenter](/links/manager) ein, gehen Sie in den Bereich `Web Cloud`{.action}, klicken Sie auf `Hosting-Pakete`{.action} und wählen Sie Ihr Hosting aus. Sie finden die Adresse unter **IPv4** im Tab `Allgemeine Informationen`{.action}.

> [!warning]
>
> Wenn Sie die Optionen **Länder-IP** oder **CDN** auf Ihrer neuen Domain aktivieren, ermitteln Sie die richtige IP-Adresse mithilfe unserer Dokumentation: [Verzeichnis von IP-Adressen für die Webhosting Cluster](/pages/web_cloud/web_hosting/clusters_and_shared_hosting_IP)).
>
> Um die Nummer des Clusters zu finden, in dem sich Ihr Webhosting befindet, gehen Sie in den Bereich `Web Cloud`{.action}, klicken Sie auf den Bereich `Hosting-Pakete`{.action}, wählen Sie dann den Tab `FTP-SSH`{.action}. Sie sehen die Cluster-Nummer unter **FTP- und SFTP-Server**: `ftp.clusterXXX.ovh.net` (wobei `XXX` die Cluster-Nummer ist).
>

> **SSL-Zertifikate**
>
> Wenn die aktuell für den Zugang zu Ihrer Website verwendete Domain über ein SSL Zertifikat verfügt, lesen Sie unsere beiden Anleitungen, um die nachfolgenden Aktionen durchzuführen:
> - [SSL-Zertifikat auf einem Webhosting verwalten](/pages/web_cloud/web_hosting/ssl_on_webhosting)
> - [Website auf HTTPS umstellen](/pages/web_cloud/web_hosting/ssl-activate-https-website)
>
> Für das kostenlose SSL *Let's Encrypt* Zertifikat genügt es, die Option `SSL` **ab sofort** für Ihre neue Domain zu aktivieren. Gehen Sie hierzu in den Tab `Multisite`{.action} Ihres Hostings. Klicken Sie anschließend auf den Button `Aktionen`{.action} und dann auf `SSL-Zertifikat neu erstellen`{.action}. Die Regenerierung dauert mindestens 2 Stunden.
>
> Die über OVHcloud bestellbaren kostenpflichtigen SSL-Zertifikate *Sectigo DV* und *Sectigo EV*  sind nur für einen einzigen Domainnamen und deren Subdomain `www` gültig.<br>
> **Wenn Sie [Schritt 3](#step3) dieser Anleitung erreicht haben**, müssen Sie Ihr kostenpflichtiges SSL-Zertifikat löschen, um dann ein neues für Ihren neuen Domainnamen zu bestellen<br>
> *Achtung, die Löschung ist unwiderruflich und für die verbleibende Zeit Ihres alten SSL-Zertifikats erfolgt keine Rückerstattung. Stellen Sie sicher, dass die Schritte 1 und 2 korrekt durchgeführt werden.*
>
> Im Fall eines selbst installierten Zertifikats (*Custom*), kontaktieren Sie Ihren Anbieter um zu erfahren, welche Möglichkeiten Sie in dieser Situation haben.
>

Wenn alle Aktionen korrekt durchgeführt wurden, sind die Multisite-Einträge Ihrer Domains identisch, **außer Sie verwenden ein kostenpflichtiges SSL-Zertifikat vom Typ *Sectigo DV*, *Sectigo EV* oder *Custom***.

![Multisites](/pages/assets/screens/control_panel/product-selection/web-cloud/web-hosting/multisite/all-domain-same-config-enable.png){.thumbnail}

> [!primary]
>
> Nach Schritt 1 ist eine Propagationszeit von 4 bis maximal 24 Stunden erforderlich, bis die Änderungen wirksam sind.
>

Wenn Ihre Website keine Datenbanken verwendet und/oder keine URL für Ihre Website umgeschrieben wird, muss diese bereits korrekt mit Ihrer neuen Domain angezeigt werden. Gehen Sie in diesem Fall direkt zu [Schritt 3](#step3) dieser Anleitung. Ist das nicht der Fall, fahren Sie mit Schritt 2 fort.

### Schritt 2: Umschreiben der URLs Ihrer Website auf die neue Domain

Die meisten Websites verwenden Datenbanken, um zu funktionieren. Die Baumstruktur dieser Domains wird üblicherweise um die ursprünglich für Ihre Website verwendete Domain erstellt. Für diese Websites sind weitere Maßnahmen erforderlich.

> [!warning]
>
> Achtung, die in Schritt 2 beschriebenen Operationen sind äußerst sensibel und können schwerwiegende Folgen für Ihre Website haben, wenn sie nicht mit Vorsicht durchgeführt werden. Sollten Sie Zweifel haben, wenden Sie sich an einen [spezialisierten Dienstleister](/links/partner).
>
> Wir empfehlen Ihnen, vor jeder Aktion eine [Sicherung Ihres FTP-Speicherplatzes](/pages/web_cloud/web_hosting/ftp_save_and_backup) sowie eine [Sicherung Ihrer Datenbank](/pages/web_cloud/web_hosting/sql_database_export) abzurufen. So können Sie Ihre Website im Fall eines Fehlers wiederherstellen.
>

Wir werden zwei Arten von Websites unterscheiden: 

- CMS (*Content Management System*) wie WordPress, Joomla!, PrestaShop, Drupal
- Individuelle Websites, die von Ihnen oder Ihrem Anbieter entwickelt wurden

#### Fall 1: Ihre Website ist ein CMS

Die meisten CMS erlauben es, direkt über den Admin-Verwaltungsbereich im *Backend*, die ursprünglich für Ihre Website angegebene Domain durch eine andere zu ersetzen.

Da die CMS von Drittanbietern entwickelt werden und nicht von OVHcloud verwaltet werden, finden Sie im Folgenden die Links zur offiziellen Dokumentation der CMS, die auf unseren Webhostings zur Installation angeboten werden:

- WordPress: <https://wordpress.org/support/article/changing-the-site-url/>
- Joomla!: Der Herausgeber dieses Programms bietet keine Dokumentation zur Änderung der Domain für den Zugang zu Ihrer Website. Kontaktieren Sie bitte den Herausgeber zu diesem Thema. Weiere Informationen finden Sie auf den offiziellen Seiten [docs.joomla.org](https://docs.joomla.org/){.external} oder [forum.joomla.org](https://forum.joomla.org/){.external}.
- Drupal: Der Herausgeber dieses Programms bietet keine Dokumentation zur Änderung der Domain für den Zugang zu Ihrer Website. Kontaktieren Sie bitte den Herausgeber zu diesem Thema. Weitere Informationen finden Sie auf der offiziellen Seite [drupal.org](https://drupal.org){.external}.
- PrestaShop: Der Herausgeber dieses Programms bietet keine Dokumentation zur Änderung der Domain für den Zugang zu Ihrer Website. Kontaktieren Sie bitte den Herausgeber zu diesem Thema. FWeitere Informationen finden Sie auf der [offiziellen Seite](https://help-center.prestashop.com){.external}.

Bitte beachten Sie, dass bei diesen CMS Änderungen auch direkt vorgenommen werden können, indem Sie die verwendete [Datenbank editieren](/pages/web_cloud/web_hosting/sql_create_database). Ändern Sie dazu die URL Ihrer Website in der entsprechenden Tabelle.

Für andere CMS, die nicht von OVHcloud als automatische Installation angeboten werden, wenden Sie sich bitte an die jeweiligen Herausgeber, um diese Umschreibung auf sichere Weise durchzuführen. 

#### Fall 2: Sie haben eine individuell gestaltete Website

Um Ihre URLs auf Ihren neuen Domainnamen umzuschreiben, [verbinden Sie sich mit der Datenbank Ihrer Website](/pages/web_cloud/web_hosting/sql_create_database) und ersetzen Sie anschließend Ihren alten Domainnamen in der entsprechenden Tabelle mit dem neuen Domainnamen. 

Überprüfen Sie auch in Ihrer `.htaccess` Datei, ob URL-Einträge auf Ihren neuen Domainnamen aktualisiert werden müssen.

Wenn Sie einen Dienstleister für die Erstellung Ihrer Website beauftragt haben, kontaktieren Sie ihn, damit dieser die Änderung sicher durchführt.

> [!success]
>
> Sobald Schritt 2 abgeschlossen ist, wird Ihre Website unter dem neuen Domainnamen angezeigt.
>

### Schritt 3: Den alten Domainnamen entfernen <a name="step3"></a>

Um *duplicate content* zu vermeiden, muss der Multisite-Eintrag des alten Domainnamens entfernt werden. Sobald Ihre Website unter dem neuen Domainnamen funktionsfähig ist, verwenden Sie unsere Anleitung zur [Verwaltung von Multisites](/pages/web_cloud/web_hosting/multisites_configure_multisite), um ihn zu löschen.

> [!warning]
>
> Denken Sie daran, sich um Ihr SSL *Sectigo EV*, *Sectigo DV* oder *Custom* Zertifikat zu kümmern, wie in [Schritt 1](#step1) beschrieben.
>

Sofern der alte Domainname bei OVHcloud registriert ist, kann er nach dem Entfernen im Tab "Multisite" mithilfe einer [permanenten sichtbare Weiterleitung (301)](/pages/web_cloud/domains/redirect_domain_name) umgeleitet werden. So können Ihre Besucher automatisch auf Ihre Website weitergeleitet werden, wenn sie den alten Domainnamen über die Adresszeile eines Browsers aufrufen.

## Weiterführende Informationen <a name="go-further"></a>

[Mehrere Websites auf einem Webhosting einrichten](/pages/web_cloud/web_hosting/multisites_configure_multisite)

[SSL-Zertifikat auf einem Webhosting verwalten](/pages/web_cloud/web_hosting/ssl_on_webhosting)

[Website auf HTTPS umstellen](/pages/web_cloud/web_hosting/ssl-activate-https-website)

[Weiterleitung von bei OVHcloud verwalteten Domainnamen](/pages/web_cloud/domains/redirect_domain_name)

[Verzeichnis von IP-Adressen für die Webhosting Cluster](/pages/web_cloud/web_hosting/clusters_and_shared_hosting_IP)    

Kontaktieren Sie für spezialisierte Dienstleistungen (SEO, Web-Entwicklung etc.) die [OVHcloud Partner](/links/partner).

Wenn Sie Hilfe bei der Nutzung und Konfiguration Ihrer OVHcloud Lösungen benötigen, beachten Sie unsere [Support-Angebote](/links/support).

Treten Sie unserer [User Community](/links/community) bei.