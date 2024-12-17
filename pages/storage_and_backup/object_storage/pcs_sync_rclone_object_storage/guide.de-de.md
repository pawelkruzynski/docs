---
title: Object Storage Swift - Verwendung von Object Storage mit Rclone
updated: 2021-10-27
---

## Einleitung

OVH Object Storage kann über Rclone synchronisiert werden.

**In dieser Anleitung erfahren Sie, wie Sie Ihren Object Storage über Ihr OVH Kundencenter synchronisieren.**

Rclone ist ein externes Synchronisierungsprogramm. Weitere Details zur Nutzung finden Sie direkt in der [offiziellen Dokumentation](https://Rclone.org/).

## Voraussetzungen

- Sie haben einen *Object Storage* Container eingerichtet (über das Kundencenter oder via Horizon).
- Sie haben einen OpenStack-Benutzer eingerichtet.

## Vorgehensweise

Wenn Sie Ihren Container und Ihren OpenStack-Benutzer eingerichtet haben, sind nur noch zwei Schritte notwendig:

- Die Konfigurationsdatei für Rclone herunterladen:

Sobald Sie Ihren OpenStack-Benutzer eingerichtet haben, können Sie in Ihrem Kundencenter die für Rclone notwendige Konfigurationsdatei abrufen.

Dabei gehen Sie wie folgt vor: Wenn Sie sich in Ihrem Kundencenter auf der Seite der OpenStack-Benutzer befinden, klicken Sie auf den Schraubenschlüssel rechts neben dem Benutzer und gehen dann auf `Rclone Konfigurationsdatei herunterladen`{.external}.

![Download der Rclone-Konfigurationsdatei](images/download_file.png){.thumbnail}

- Rclone konfigurieren:

Wenn Sie die Datei heruntergeladen haben, können Sie den nachfolgenden Befehl ausführen, um Ihren neuen Storage hinzuzufügen:

```sh
Rclone config
```

Sie werden dann aufgefordert, die in Ihrer Datei angegebenen Konfigurationsdaten einzugeben.

> [!primary]
>
> Sie können auch den Inhalt Ihrer Datei kopieren und an den für die Konfiguration von Rclone vorgesehenen Stellen einfügen (*.config/Rclone/Rclone.conf*).
> 

Sobald Ihre Konfiguration abgeschlossen ist, können Sie sie testen, indem Sie beispielsweise eine Liste Ihrer Container abrufen:

```sh
Rclone lsd BackupStorage
```

*BackupStorage* entspricht dem Namen Ihres Storage.

Auf der offiziellen Website von Rclone finden Sie eine ausführliche Dokumentation zur Vorgehensweise bei der Synchronisierung Ihres Object Storage mit Rclone: [Offizielle Dokumentation von Rclone](https://Rclone.org/swift/){.external}.

## Weiterführende Informationen

Wenn Sie Schulungen oder technische Unterstützung bei der Implementierung unserer Lösungen benötigen, wenden Sie sich an Ihren Vertriebsmitarbeiter oder klicken Sie auf [diesen Link](/links/professional-services), um einen Kostenvoranschlag zu erhalten und eine persönliche Analyse Ihres Projekts durch unsere Experten des Professional Services Teams anzufordern.

Für den Austausch mit unserer User Community gehen Sie auf <https://community.ovh.com/en/>.
