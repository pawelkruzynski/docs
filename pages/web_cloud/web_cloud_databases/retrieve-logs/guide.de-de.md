---
title: "Web Cloud Databases - Logs verwalten"
excerpt: "Erfahren Sie hier, wie Sie die Logs von Datenbanken, die auf Ihrem Web Cloud Databases Server"
updated: 2024-11-25
---

## Ziel

Ein Log ist ein Ereignis, das auf einem Computersystem (Server, Computer, Anwendung, Website, Datenbank, Computernetzwerk, etc.) aufgetreten ist.  
Ein Log kann z.B. Folgendes enthalten:

- Der Zeitstempel (Datum, Uhrzeit, Minute, Sekunde, etc.) des Ereignisses.
- Die Art des Ereignisses (Login, Logout, Fehler, Download, Upload, Alarm, etc.).
- Zusätzliche Informationen zum Ereignis (angezeigte Seite oder Datei, gestartete Anwendung, Remoteserver aufgerufen, Name einer geladenen oder heruntergeladenen Datei, etc.)
- Der Ursprung des Ereignisses (Benutzer-ID, Quell-IP, Quellprogramm, etc.).
- Systemstatus, in dem das Ereignis stattfindet (verfügbare Ressourcen, verbleibender Speicher, CPU-Auslastung, etc.).

In den meisten Fällen werden die Logs direkt von den Computersystemen erstellt, in denen die Ereignisse stattfinden.
Sie werden in Textdateien gespeichert, die auch als Logdateien bezeichnet werden.

Aus diesem Grund können Sie mit Log-Dateien folgende Aktionen ausführen:

- Analyse des Verhaltens des IT-Systems, das die Logs generiert
- Identifizieren von Fehlern, die auf dem Computersystem aufgetreten sind
- Beheben von Fehlern im Computersystem
- Optimierung und Verbesserung der IT-Systemleistung

Ihr Angebot [Web Cloud Databases](/links/web/databases) erstellt also eigene Logs.

In manchen Situationen kann es notwendig sein, Logs Ihres Web Cloud Databases Servers oder dessen Datenbanken abzurufen.

**Diese Anleitung erklärt, wie Sie die Logs von Web Cloud Databases anzeigen und verwalten können.**

## Voraussetzungen

- Sie nutzen den Dienst [Web Cloud Databases](/links/web/databases).
- Sie haben Zugriff auf Ihr [OVHcloud Kundencenter](/links/manager).

## In der praktischen Anwendung

> [!warning]
>
> Diese Anleitung soll Sie bei allgemeinen Aufgaben bestmöglich unterstützen. Bei Schwierigkeiten kontaktieren Sie bitte einen [spezialisierten Dienstleister](/links/partner). Leider können wir Ihnen bei der Interpretation der Logs Ihrer Web Cloud Databases keine weitergehende technische Unterstützung anbieten. Weitere Informationen finden Sie am [Ende dieser Anleitung](#go-further).
>

### Die Logs Ihrer Web Cloud Databases in Echtzeit anzeigen

So greifen Sie auf die Logs Ihrer Web Cloud Databases in Echtzeit zu:

1. Loggen Sie sich in Ihr [OVHcloud Kundencenter](/links/manager) ein.
2. Klicken Sie oben im Kundencenter auf den Tab `Web Cloud`{.action}.
3. Klicken Sie in der linken Spalte auf das Dropdown-Menü `Web Cloud Databases`{.action}.
4. Wählen Sie die betreffende Web Cloud Databases Instanz aus.
5. Klicken Sie auf den Tab `Logs`{.action}.

![Web Cloud Databases](/pages/assets/screens/control_panel/product-selection/web-cloud/web-cloud-databases/logs/tab.png){.thumbnail}

In dieser integrierten Konsole finden Sie in Echtzeit die Logs Ihrer Web Cloud Databases Lösung.

> [!primary]
>
> Wie bereits erwähnt, sind die Logs hier nur in Echtzeit verfügbar. Das bedeutet, dass diese Logs nur angezeigt werden, wenn sie erstellt werden, während Sie sich im Tab `Logs`{.action} befinden.
>
> Wenn Sie den Tab `Logs`{.action} verlassen und später darauf zurückkehren, wird der zuvor angezeigte Verlauf nicht mehr angezeigt.
>

### Loghistorie Ihrer Web Cloud Databases abrufen

Um den Logverlauf Ihrer Web Cloud Databases abzurufen, muss eine SFTP-Verbindung verwendet werden.

> [!warning]
>
> Vergewissern Sie sich vor dem Login, dass die öffentliche IP-Adresse Ihres Interzugangs auf Ihrem Web Cloud Databases Server mit der Option `SFTP` autorisiert ist.
>
> Um dies zu überprüfen, rufen Sie die öffentliche IP-Adresse Ihres aktuellen Internetzugriffspunkts ab und folgen Sie dem Abschnitt **Autorisieren einer IP-Adresse** in [dieser Anleitung](/pages/web_cloud/web_cloud_databases/starting_with_clouddb).
>

So finden Sie die SFTP-Verbindungsinformationen zu Ihrer Web Cloud Databases Lösung:

1. Loggen Sie sich in Ihr [OVHcloud Kundencenter](/links/manager) ein.
2. Klicken Sie oben im Kundencenter auf den Tab `Web Cloud`{.action}.
3. Klicken Sie in der linken Spalte auf das Dropdown-Menü `Web Cloud Databases`{.action}.
4. Wählen Sie die betreffende Web Cloud Databases Lösung aus.
5. Im Tab `Allgemeine Informationen`{.action} finden Sie den Bereich `Verbindungsinformationen`{.action}.
6. Unter `SFTP`{.action} finden Sie alle notwendigen Informationen, um sich via SFTP zu verbinden.

> [!primary]
>
> Wenn Sie das `Server-Passwort` nicht kennen, klicken Sie auf den Button `...`{.action} rechts, um es zu ändern.
>

![Web Cloud Databases](/pages/assets/screens/control_panel/product-selection/web-cloud/web-cloud-databases/general-information/sftp-login.png){.thumbnail}

Nachdem Sie die SFTP-Login-Daten abgerufen haben, verbinden Sie sich über einen FTP-Client (FileZilla, Cyberduck, WinSCP, etc.).

Gehen Sie in FileZilla links oben in das Menü `File`{.action} und klicken Sie dann auf `Site Manager`{.action}.

Klicken Sie auf `New Site`{.action} und geben Sie die zuvor ermittelten Parameter ein.

![Web Cloud Databases](/pages/assets/screens/other/web-tools/filezilla/site-manager.png){.thumbnail}

Die Log-Datei `stdout.log` befindet sich im Wurzelverzeichnis.

Laden Sie diese Datei herunter, um sie zu öffnen.

> [!primary]
>
> Im SFTP-Wurzelverzeichnis Ihres Web Cloud Databases Servers kann eine zusätzliche Logdatei mit dem Namen `slow-query.log` angezeigt werden.  
> Diese Datei enthält den Verlauf der langsamen Anfragen, die auf Ihrem Web Cloud Databases Server ausgeführt wurden. 
> 
> Standardmäßig ist der Wert für Web Cloud Databases-Lösungen in der Variable **long_query_time** auf 1 Sekunde festgelegt.
> 
> Mit dieser Datei können Sie Ihre Skripte und den Inhalt Ihrer Datenbanken optimieren, um die Performance Ihrer dazugehörigen Dienste zu verbessern.
>

### Logs Ihrer Web Cloud Databases Lösung auf der Logs Data Platform abonnieren <a name="wcdb-ldp"></a>

[Logs Data Platform](/links/manage-operate/ldp) ist eine Plattform für die Verwaltung Ihrer Logs. Sie kann nützlich sein, wenn Sie über eine sehr große Infrastruktur verfügen oder wenn Ihre Dienste eine große Anzahl an Logs generieren. Diese Plattform wurde entwickelt, um die Aggregation und Verwaltung der Logs zu vereinfachen.

Sie ruft Logs ab, die von Ihrer Infrastruktur, Websites oder Anwendungen generiert wurden, zum Beispiel:

- Um sie zu speichern.
- Zur Anzeige in Echtzeit-Dashboards.
- Zur Ermöglichung komplexer Abfragen durch die Benutzer.
- Zum Filtern nach Datum, Anwendung, Typ oder Inhalt.

Weitere Informationen zur Logs Data Platform finden Sie in unserer [Einführung zu Logs Data Platform](/pages/manage_and_operate/observability/logs_data_platform/getting_started_introduction_to_LDP) (EN).

Da die [Web Cloud Databases](/links/web/databases) mit vielen verschiedenen Diensten (Shared Hosting, VPS, Dedicated Server etc.) genutzt werden können, können diese zusätzlich zu den bereits verfügbaren Echtzeit-Logs auch per Stream der Logs Data Platform abonniert werden.

So abonnieren Sie einen Datenstrom auf der Logs Data Platform für Ihre Web Cloud Databases:

1. Verbinden Sie sich mit Ihrem [OVHcloud Kundencenter](/links/manager).
2. Klicken Sie oben im Kundencenter auf den Tab `Web Cloud`{.action}.
3. Klicken Sie in der linken Spalte auf das Dropdown-Menü `Web Cloud Databases`{.action}.
4. Wählen Sie die betreffende Web Cloud Databases Instanz aus.
5. Klicken Sie auf der angezeigten Seite auf den Tab `Logs`{.action}.
6. Klicken Sie auf der rechten Seite der Box, in der Ihre Logs in Echtzeit angezeigt werden, auf den Button `Abonnieren`{.action}.

![Web Cloud Databases](/pages/assets/screens/control_panel/product-selection/web-cloud/web-cloud-databases/logs/tab-subscribe.png){.thumbnail}

Wenn Sie in Ihrem [OVHcloud Kundencenter](/links/manager) über mehrere Logs Data Platform Lösungen verfügen, wählen Sie in der Dropdown-Liste direkt unter der Schaltfläche `Stream hinzufügen` die Referenz der Logs Data Platform aus, die Sie abonnieren möchten.

![Web Cloud Databases](/pages/assets/screens/control_panel/product-selection/web-cloud/web-cloud-databases/logs/data-stream.png){.thumbnail}

Für das Abonnement Ihrer Web Cloud Databases Lösung ergeben sich zwei Szenarien.

#### Fall 1 - Abonnieren eines bereits bestehenden Feeds auf Ihrer Logs Data Platform Lösung <a name="wcdb-ldp-case1"></a>

Wenn der betreffende Stream bereits vorhanden ist, wird er in der Tabelle am Ende der Seite als Zeile angezeigt.  
Um in diesem Fall Ihre Web Cloud Databases Lösung für diesen bestehenden Feed zu abonnieren, klicken Sie einfach auf den Button `Abonnieren`{.action} rechts in der Zeile des betreffenden Feeds.

Nach einigen Sekunden wird in Ihrem Kundencenter eine Meldung angezeigt, dass das Abonnement erfolgreich erstellt wurde.

#### Fall 2 - Einen neuen Datenstrom auf Ihrer Logs Data Platform abonnieren

Wenn der betreffende Stream noch nicht vorhanden ist, klicken Sie auf `Stream hinzufügen`{.action}.  
Sie werden dann auf eine neue Seite in Ihrem OVHcloud Kundencenter weitergeleitet, auf der Sie einen neuen Datenstrom auf Ihrer Logs Data Platform erstellen und hinzufügen können.

![Web Cloud Databases](/pages/assets/screens/control_panel/product-selection/bare-metal-cloud/logs-data-platform/data-stream/add-data-stream.png){.thumbnail}

Wenn nötig, lesen Sie unsere Anleitungen „[Einführung in Logs Data Platform](/pages/manage_and_operate/observability/logs_data_platform/getting_started_introduction_to_LDP)“ (EN) und „[Schneller Start mit Logs Data Platform](/pages/manage_and_operate/observability/logs_data_platform/getting_started_quick_start)“ (EN), um diese Aktionen durchzuführen.

Wenn Sie alle Formulare und Informationen eingegeben haben, klicken Sie auf `Speichern`{.action}.

Sie werden dann auf den Tab `Streams` Ihrer Logs Data Platform Lösung weitergeleitet.

Abonnieren Sie nun Ihre Web Cloud Databases Lösung für Ihren neu erstellten Feed auf Ihrer Logs Data Platform Lösung.

Um dies zu tun, gehen Sie, wie [zuvor](#wcdb-ldp) erklärt, in den Tab `Logs`{.action} Ihrer Web Cloud Databases-Lösung, um diesen neuen Stream zu abonnieren, und folgen Sie dann dieses Mal dem oben beschriebenen [Fall 1](#wcdb-ldp-case1).

## Weiterführende Informationen <a name="go-further"></a>

[Erste Schritte mit Ihren Web Cloud Databases](/pages/web_cloud/web_cloud_databases/starting_with_clouddb)

[Einführung in Logs Data Platform](/pages/manage_and_operate/observability/logs_data_platform/getting_started_introduction_to_LDP) (EN)

[Schneller Einstieg mit Logs Data Platform](/pages/manage_and_operate/observability/logs_data_platform/getting_started_quick_start) (EN)
 
Kontaktieren Sie für spezialisierte Dienstleistungen (SEO, Web-Entwicklung etc.) die [OVHcloud Partner](/links/partner).
 
Treten Sie unserer [User Community](/links/community) bei.