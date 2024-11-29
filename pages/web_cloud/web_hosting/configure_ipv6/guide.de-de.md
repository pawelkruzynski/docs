---
title: "IPv6 für Ihre Website konfigurieren"
excerpt: "Diese Anleitung erklärt, wie Sie Ihre Website über eine IPv6-Adresse verfügbar machen"
updated: 2024-03-12
---

## Ziel

Das Internet läuft seit Anfang der 1990er Jahre unter Verwendung von IPv4. Mit diesem Standard werden mit dem öffentlichen Netzwerk verbundenen Geräten IP-Adressen im Format X.X.X.X (wobei "X" für Zahlen zwischen 0 und 255 steht) zur Verfügung gestellt (Server, Computer, Smartphones, etc.). Dieses Protokoll begrenzt jedoch die Anzahl der an das Internet angeschlossenen Geräte auf etwa 4 Milliarden, was für 2022 im Schnitt weniger als ein Gerät je zwei Personen der Weltbevölkerung bedeutet.

Aus diesem Grund wurde das **IPv6**-Protokoll eingeführt, mit dem bis zu 340 Sextillionen Geräte an das Internet angeschlossen werden können. Die umfassende Bereitstellung von IPv6 braucht Zeit, da die neue Norm für das gesamte Internet integriert werden muss.

Da weniger IPv4-Adressen zur Verfügung stehen, ist es schwieriger, neue Geräte mit dem IPv4-Standard ins Internet zu bringen. Verbindungen über IPv6-Adressen sind aber nur anwendbar, wenn die öffentlichen Ressourcen (z.B. Ihre Website) mit diesem Protokoll verfügbar sind. Das bedeutet, je mehr Websites mit IPv6 verfügbar werden, desto wichtiger wird es für alle beteiligten Akteure, auf dieses neue Protokoll umzusteigen.

Weitere Informationen finden Sie im [Wikipedia-Artikel](https://de.wikipedia.org/wiki/IPv6){.external} zum IPv6-Protokoll.

Unsere Webhostings sind seit 2011 mit IPv6 kompatibel, doch die Aktivierung dieses Protokolls war bis vor kurzem eine optionale Konfigurationseinstellung.  

**Diese Anleitung erklärt, wie Sie prüfen, ob Ihre Website über IPv6 erreichbar ist und wie Sie die IPv6-Adresse Ihres Webhostings konfigurieren.**

## Voraussetzungen

- Sie verfügen über einen [Domainnamen](/links/web/domains).
- Sie verfügen über ein [OVHcloud Webhosting](/links/web/hosting).
- Sie haben Zugriff auf Ihr [OVHcloud Kundencenter](/links/manager).

## In der praktischen Anwendung

> [!warning]
> OVHcloud stellt Ihnen Dienstleistungen zur Verfügung, für deren Konfiguration und Verwaltung Sie die alleinige Verantwortung tragen. Es liegt somit bei Ihnen, sicherzustellen, dass diese ordnungsgemäß funktionieren.
> 
> Diese Anleitung soll Sie bei allgemeinen Aufgaben bestmöglich unterstützen. Dennoch empfehlen wir Ihnen, falls Sie Hilfe brauchen, einen [spezialisierten Dienstleister](/links/partner) zu kontaktieren oder Ihre Fragen in der OVHcloud Community zu stellen. Leider können wir Ihnen für administrative Aufgaben keine weitergehende technische Unterstützung anbieten. Weitere Informationen finden Sie am [Ende dieser Anleitung](#go-further).
>

Wenn Ihre Website nicht bereits mit IPv6 funktioniert, können Sie die [IPv6-Adresse Ihres OVHcloud Webhostings](/pages/web_cloud/web_hosting/clusters_and_shared_hosting_IP) der aktiven DNS-Zone Ihres Domainnamens hinzufügen. Ziel ist es, dass Webbrowser eine IPv6-Adresse finden, die mit Ihrer Website über Ihren Domainnamen verknüpft ist.

### Die IPv6-Verfügbarkeit Ihrer Website überprüfen

Um zu überprüfen, ob Ihre Website bereits eine IPv6-Adresse verwendet, können Sie Ihre URL auf der Website [ipv6-test.com](https://ipv6-test.com/validate.php){.external} eingeben. Es wird geprüft, ob Ihre Website auf dieses IP-Protokoll reagiert. Ist das nicht der Fall, führen Sie die nachfolgenden Schritte aus.

### Schritt 1: IPv6-Adresse Ihres Webhostings abrufen

Loggen Sie sich in Ihrem [OVHcloud Kundencenter](/links/manager) ein. Klicken Sie im Bereich `Web Cloud`{.action} auf `Hosting-Pakete`{.action}, wählen Sie das betreffende Hosting aus und gehen Sie dann auf den Tab `Allgemeine Informationen`{.action}.

Kopieren Sie im Abschnitt **IPv6** die Adresse und gehen Sie zum nächsten Schritt über.

![IPv6](/pages/assets/screens/control_panel/product-selection/web-cloud/web-hosting/general-information/find-ipv6.png){.thumbnail}

### Schritt 2: DNS-Zone Ihres Domainnamens konfigurieren

> [!warning]
>
> Unsere CDN-Optionen sind derzeit mit IPv6-Adressen nicht kompatibel. Wenn Sie eine IPv6-Adresse für Ihre Website konfigurieren, profitieren Ihre Besucher nicht vom CDN.
>
> Beachten Sie, dass ein Hinzufügen, Ändern oder Löschen von DNS-Einträgen in der aktiven DNS-Zone eines Domainnamens eine Propagationszeit von **4 bis 24 Stunden** benötigt, um voll wirksam zu sein.
>

Damit ein Browser die IPv6-Adresse Ihres Domainnamens aufrufen kann, bearbeiten Sie die aktive DNS-Zone Ihres Domainnamens. Verwenden Sie bei Bedarf unsere Anleitung "[Bearbeiten der OVHcloud DNS-Zone](/pages/web_cloud/domains/dns_zone_edit)", um einen DNS-Eintrag vom Typ **AAAA** zu erstellen.

Klicken Sie im Bereich `Web Cloud`{.action} auf `Domainnamen`{.action}. Wählen Sie Ihren Domainnamen aus und gehen Sie dann auf den Tab `DNS-Zone`{.action}. Klicken Sie rechts neben der Tabelle auf den Button `Eintrag hinzufügen`{.action}. 

Tragen Sie die zuvor kopierte IPv6-Adresse als Typ **AAAA** ein.

![IPv6](/pages/assets/screens/control_panel/product-selection/web-cloud/domain-dns/dns-zone/add-dns-zone-entry-aaaa.png){.thumbnail}

## Weiterführende Informationen <a name="go-further"></a>

[Bearbeiten der OVHcloud DNS-Zone](/pages/web_cloud/domains/dns_zone_edit)

Kontaktieren Sie für spezialisierte Dienstleistungen (SEO, Web-Entwicklung etc.) die [OVHcloud Partner](/links/partner).

Wenn Sie Hilfe bei der Nutzung und Konfiguration Ihrer OVHcloud Lösungen benötigen, beachten Sie unsere [Support-Angebote](/links/support).

Treten Sie unserer [User Community](/links/community) bei.