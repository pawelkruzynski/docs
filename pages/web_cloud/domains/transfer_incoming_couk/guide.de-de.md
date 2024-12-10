---
title: Transfer einer .uk-Domain zu OVHcloud
excerpt: Erfahren Sie hier, wie Sie Domainnamen mit UK-Ländercode zu OVHcloud transferieren
updated: 2024-06-28
---

## Ziel

Für den Transfer einer .uk-Domain (oder einer ähnlichen Domain) ist ein spezifischer Vorgang erforderlich.

> [!warning]
> OVHcloud stellt Ihnen Dienstleistungen zur Verfügung, für deren Konfiguration und Verwaltung Sie die alleinige Verantwortung tragen. Es liegt somit bei Ihnen, sicherzustellen, dass diese ordnungsgemäß funktionieren.
> 
> Diese Anleitung soll Sie bei allgemeinen Aufgaben bestmöglich unterstützen. Dennoch empfehlen wir Ihnen, falls Sie Hilfe brauchen, einen [spezialisierten Dienstleister](/links/partner) zu kontaktieren und/oder Ihre Fragen in der OVHcloud Community zu stellen. Leider können wir Ihnen für administrative Aufgaben keine weitergehende technische Unterstützung anbieten. Weitere Informationen finden Sie am [Ende dieser Anleitung](#go-further).
>

**In dieser Anleitung erfahren Sie, wie Sie .uk-Domains zu OVHcloud transferieren.**

> [!warning]
>
> Wenn der zu ändernde Domainname aktuell bei OVHcloud registriert ist, ist ein eingehender Domaintransfer nicht der passende Vorgang. Die vorliegende Anleitung betrifft lediglich den Wechsel des Registrars (OVHcloud) des Domainnamens.
>
> Um die Verwaltung des Domainnamens einem anderen OVHcloud Kunden-Account zu übertragen, muss stattdessen eine **Änderung der Kontakte** durchgeführt werden. Die Vorgehensweise wird in [dieser Anleitung](/pages/account_and_service_management/account_information/managing_contacts) beschrieben.
>
> Wenn auch der **Inhaber des Domainnamens** geändert werden muss, sollte dies erfolgen, **bevor** Sie die Kontakte des Domainnamens ändern. Verwenden Sie dazu unsere Anleitung zum [Inhaberwechsel für Domainnamen](/pages/web_cloud/domains/trade_domain).
>
> Wenn Sie neben dem Transfer Ihrer Domain auch die dazugehörigen Dienste (Website, E-Mail, etc.) migrieren möchten, lesen Sie zuerst unsere Anleitung „[Website und dazugehörige Dienste zu OVHcloud migrieren](/pages/web_cloud/web_hosting/hosting_migrating_to_ovh)“, bevor Sie fortfahren.
> In dieser Anleitung erfahren Sie, wie Sie alle Ihre Dienstleistungen ohne Unterbrechung migrieren.
>
> Wenn Sie Ihren Domainnamen nur transferieren, ohne Ihre anderen Dienste zu verlegen, stellen Sie sicher, dass Sie die aktiven DNS-Server für Ihren Domainnamen von Ihrem **aktuellen Registrar** erfahren, um diese direkt in Schritt 3 der Anleitung „[Domainnamen zu OVHcloud transferieren](/pages/web_cloud/domains/transfer_incoming_generic_domain)“ einzugeben.
> So wird vermieden, dass die Zuordnung zwischen Ihrem Domainnamen und den zugehörigen externen Diensten unterbrochen wird.
>

## Voraussetzungen

- Ihre Domain darf sich nicht in der **Redemption**-Phase befinden oder den Status "Pending Delete" haben.
- Die Domain darf nicht bei Ihrem Registrar blockiert sein. 
- Die Angaben des Inhabers müssen im Whois der [Domain](https://www.nominet.uk/whois/){.external} aktuell sein.
- Sie haben Zugriff auf den Autorisierungscode, der an die E-Mail-Adresse des Inhabers versandt wird. 

> [!primary]
>
> Der Zeitraum der **Redemption**-Phase beträgt maximal 90 Tage ab dem Ablaufdatum der Domain. Im Falle eines Transfers erlaubt dieser Zeitraum die Wiederherstellung der Domain und entsperrt so die Möglichkeit, diese zu transferieren.

## Betroffene Endungen

- .uk
- .co.uk
- .ac.uk
- .gov.uk
- .me.uk
- .net.uk
- .org.uk
- .plc.uk
- .sch.uk

## In der praktischen Anwendung

### Transferverfahren

#### Schritt 1: Änderung des TAG Ihrer Domain

Um Ihre Domain zu OVHcloud transferieren zu können, müssen Sie zuerst den OVHcloud TAG bei Ihrem aktuellen Registrar angeben. Der OVHcloud TAG ist “OVH-FR“. Die Liste der TAGs der verschiedenen Registrare ist auf der [offiziellen Seite der Registry Nominet](https://registrars.nominet.uk/uk-namespace/registrar-agreement/list-of-registrars/){.external} verfügbar.

> [!primary]
>
> Wenn Sie den TAG Ihrer Domain nicht über Ihren aktuellen Registrar ändern können, können Sie bei der Nominet Registry beantragen, die Änderung für Sie durchzuführen. Nominet berechnet eine Gebühr für diese Dienstleistung.
>
> Weitere Informationen finden Sie auf der [Nominet-Website](https://www.nominet.uk/domain-support/){.external}.

#### Schritt 2: Transfer-Autorisierungscode erhalten

Sobald Sie den TAG geändert haben, erhält der Inhaber der Domain nach einigen Minuten per E-Mail einen Autorisierungscode (“authcode“). Dieser ist 5 Tage gültig und ermöglicht es, die (kostenlose) Bestellung der Domain bei OVHcloud zu starten.

#### Schritt 3: Bestellung des kostenlosen Transfers

Sobald Sie über Ihren Autorisierungscode verfügen, können Sie die Transfer-Bestellung Ihrer Domain auf der [OVHcloud Website](/links/website) ausführen. Der Bestellvorgang läuft dann ab wie bei der Bestellung generischer Domains.

Ihre Domain wird in wenigen Stunden in Ihrem [OVHcloud Kundencenter](/links/manager) angezeigt.

### Zusätzliche Informationen

#### Kosten für einen .uk-Domaintransfer

Der Transfer ist kostenlos.

#### Gültigkeit des Autorisierungscode

Der Autorisierungscode wird nach der Änderung des TAG automatisch generiert. Wenn die Bestellung nicht innerhalb von 5 Tagen ausgeführt wird, wird der Transfer vom Registrar abgebrochen.

#### Verlängerung der Domain nach einem Transfer

Da der Transfer kostenlos ist, ändert sich nichts am Ablaufdatum. Um die Domain nach dem Transfer zu verlängern, gehen Sie auf [die Website von OVHcloud](https://www.ovh.co.uk/cgi-bin/order/renew.cgi).

## Weiterführende Informationen <a name="go-further"></a>

[Domainnamen zu OVHcloud transferieren](/pages/web_cloud/domains/transfer_incoming_generic_domain)

Treten Sie unserer [User Community](/links/community) bei.
