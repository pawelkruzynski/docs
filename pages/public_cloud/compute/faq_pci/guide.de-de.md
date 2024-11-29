---
title: FAQ Public Cloud OVHcloud
excerpt: Hier finden Sie die am häufigsten gestellten Fragen zu den OVHcloud Public Cloud Diensten
updated: 2024-10-11
---
<style>
details>summary {
    color:rgb(33, 153, 232) !important;
    cursor: pointer;
}
details>summary::before {
    content:'\25B6';
    padding-right:1ch;
}
details[open]>summary::before {
    content:'\25BC';
}
</style>


## Public Cloud FAQ

### Optionen und Abrechnung

/// details | Wie funktioniert die Abrechnung der Public Cloud?

Die Abrechnung erfolgt zwischen dem 01\. und 05\. eines Monats und richtet sich nach dem Verbrauch des Vormonats. Wenn Sie sich für die monatliche Abrechnung entschieden haben, wird Ihnen die Monatspauschale für den kommenden Monat zusammen mit dem Verbrauch des Vormonats (Instanzen, Object Storage) berechnet. Bei einer Umstellung auf die monatliche Abrechnung einer Ressource erfolgt eine sofortige anteilige Abrechnung für den laufenden Monat.

Beachten Sie, dass jede Instanz abgerechnet wird, bis sie aus Ihrem OVHcloud Kundencenter gelöscht wird.  
Sie können Ihren Verbrauch anhand von Prognosen aus Ihrer Nutzungshistorie verfolgen. Darüber hinaus können Sie für jedes Public Cloud Projekt eine separate Abrechnung wählen, was eine Neuabrechnung innerhalb Ihres Unternehmens ermöglicht.

Um von einem Abrechnungsmodus zum anderen zu wechseln, nutzen Sie unsere Anleitung: [Von der stündlichen auf monatliche Abrechnung umstellen](/pages/account_and_service_management/managing_billing_payments_and_services/changing_hourly_monthly_billing).

> [!success]
> Profitieren Sie von reduzierten Preisen, indem Sie Ihre Public Cloud-Ressourcen für einen Zeitraum von 1 bis 36 Monaten abonnieren. Weitere Informationen finden Sie auf unserer Webseite: [Savings Plan](/links/public-cloud/savings-plan).

///

/// details | Wie füge ich eine Public Cloud Instanz an den Savings Plan an, den ich gerade bestellt habe?

Es sind keine Aktionen erforderlich. Jede bereits erstellte (oder in Kürze erstellte) Instanz, die dem für Ihren [Savings Plan](/links/public-cloud/savings-plan) gewählten Modell entspricht, wird automatisch in diese integriert, sofern die im Savings Plan enthaltenen Ressourcen nicht ausgeschöpft sind.

///

/// details | Wie kann ich meine Instanzen anpassen, wenn ich mehr oder weniger Ressourcen benötige?

Jede Instanz kann über das Kundencenter auf eine leistungsstärkere Instanz der gleichen Reihe umgestellt werden, indem Sie im Dashboard der Instanz links auf `Bearbeiten`{.action} klicken. Wenn die Option "Flex" gewählt wurde, können Sie diese auch auf ein günstigeres Modell herunterstufen. Diese Option erfordert eine fixe Speicherplatzgröße von 50 GB für alle Modelle und ermöglicht so eine Anpassung in beide Richtungen.

In jedem Fall erfordert die Umstellung der Instanz einen Neustart.

///

/// details | Sind Public Cloud Instanzen mit *cloud-init* kompatibel?

Ja, die von OVHcloud bereitgestellten Cloud-Images enthalten *cloud-init*-Skripte, mit denen Instanzen beim Start personalisiert werden können. Die Infrastruktur liefert die Informationen zur Personalisierung der Instanz über einen Metadatenserver, der direkt von *cloud-init* kontaktiert wird.

///

/// details | Ist Virtualisierung mit Instanzen möglich (*Nested*)?

Ja und nein.

Ja, da die Option aktiviert ist (*Flag* "CPU VMX" ist verfügbar). Damit können Sie jede darauf basierende Virtualisierungslösung mit Ihrer Instanz verwenden (KVM, QEMU, VirtualBox, Xen, HyperV, etc.).

Nein, denn sobald eine Live-Migration Ihrer Instanz stattfindet (und das kann jederzeit geschehen, basierend auf dem Lebenszyklus des zugrunde liegenden Hypervisors), kann dies einen *Kernel Panic* auslösen.

Weitere Informationen finden Sie unter [diesem Link](https://www.linux-kvm.org/page/Nested_Guests#Limitations).

///

### Bei einer Instanz anmelden

/// details | Wie kann ich mich mit einer Public Cloud Instanz verbinden?

Die Verbindung erfolgt mit einem SSH-Schlüsselpaar, das bei der Erstellung Ihrer Public Cloud-Instanz konfiguriert werden muss.

Lesen Sie die Anleitung [Erste Public Cloud Instanz erstellen und auf dieser einloggen](/pages/public_cloud/compute/public-cloud-first-steps).

///

/// details | Ich habe den SSH-Schlüssel verloren oder möchte ihn ändern, wie gehe ich dazu vor?

Wenn Sie sich nach dem Verlust Ihres privaten Schlüssels nicht mehr verbinden können, ändern Sie den öffentlichen Schlüssel Ihrer Instanz, indem Sie diese in den "Rescue"-Modus versetzen.

Lesen Sie die Anleitung zum [Ändern des SSH-Schlüssels](/pages/public_cloud/compute/replacing_lost_ssh_key).

///

/// details | Wie kann ich OpenStack-Benutzer erstellen und verwalten?  

Um die Horizon- oder OpenStack-APIs verwenden zu können, müssen Sie zunächst einen OpenStack-Benutzer anlegen. Sie können eine unbegrenzte Anzahl erstellen.

Lesen Sie die Anleitung [Einen OpenStack User erstellen oder löschen](/pages/public_cloud/compute/create_and_delete_a_user).

///

### Backups

/// details | Kann ich Backups meiner Public Cloud Server erstellen?

Sie können jederzeit über Ihr OVHcloud Kundencenter ein Backup einer Instanz erstellen. Mit dieser können Sie Ihre Instanz auf eine frühere Konfiguration zurücksetzen oder neu erstellen. Diese Backups werden wie die Images in "Private Image" gespeichert und abgerechnet. Über die OpenStack-APIs haben Sie die Möglichkeit, sie außerhalb der OVHcloud-Infrastruktur oder für andere Projekte herunterzuladen.

Lesen Sie die Anleitung [Backup einer Instanz erstellen](/pages/public_cloud/compute/save_an_instance).

///

/// details | Kann ich die Größe eines Volumes im laufenden Betrieb erhöhen, während die Disk weiterhin genutzt wird?

Nein, ein Volume muss zuerst ausgehängt werden, um es vergrößern zu können.

///

/// details | Wie viele zusätzliche Volumes kann ich einer Instanz hinzufügen?

Sie können bis zu 25 zusätzliche Volumes an eine Instanz anhängen.

///

### Netzwerk

/// details | Wie viele IPv6-Adressen werden mit meiner Instanz ausgeliefert?

Jede Instanz wird mit einer IPv6-Adresse ausgeliefert.

///

/// details | Kann ich die öffentliche IP-Adresse meiner Instanz ändern?

Die öffentlichen IPs werden den Instanzen automatisch zugewiesen und können daher nicht geändert werden. Um die öffentliche IP-Adresse einer Instanz zu verwalten, empfehlen wir die Verwendung von Additional IPs. So können Sie unabhängig von einer der Instanz automatisch zugewiesenen öffentlichen Adresse eine oder mehrere Additional IP-Adressen zu Ihrer Instanz hinzufügen.

Weitere Informationen finden Sie in der Anleitung "[Eine Additional IP erwerben](/pages/public_cloud/public_cloud_network_services/additional-ip-buy)".

///

/// details | Wie viele Additional IPs kann ich an jede Instanz anhängen?

Sie können bis zu 256 Additional IPs pro Instanz anhängen.

///

/// details | Wie kann ich ein privates Netzwerk zwischen meinen Servern einrichten?

Public Cloud enthält eine SDN-Lösung (Software Defined Network). Diese ermöglicht es, dynamische private Netzwerke zu erstellen und diese dann über Ihr Kundencenter oder die API mit den Instanzen zu verbinden.

Diese privaten Netzwerke werden durch die vRack Technologie von OVHcloud unterstützt, die allen anderen Diensten des Unternehmens, wie Private Cloud oder Dedicated Server, gemeinsam ist. Sie bietet so die Möglichkeit, alle Ihre Infrastrukturelemente bei OVHcloud einzeln und sicher kommunizieren zu lassen.

Lesen Sie die Anleitung [vRack Public Cloud](/pages/public_cloud/public_cloud_network_services/getting-started-07-creating-vrack).

Das private Netzwerk verfügt standardmäßig über den nativen Schutz von OpenStack. Diese beinhalten verschiedene Mechanismen wie den Schutz vor IP-Spoofing.<br>
Auf der Instanzen-Seite kann dies zu Blockaden von Netzwerkpaketen führen, je nach Ihren Bedürfnissen (pfSense, Router, CARP Protokoll, etc.).

Je nach Bedarf müssen Sie die Funktion `Port Security` im privaten Port oder Netzwerk deaktivieren.
Bitte lesen Sie die Anleitung zur [Verwaltung der Firewall- und Port-Security-Regeln über Netzwerke mit OpenStack CLI](/pages/public_cloud/compute/security_group_private_network).

Weitere Informationen finden Sie in der [OpenStack Dokumentation](https://docs.openstack.org/developer/dragonflow/specs/mac_spoofing.html) oder auf [superuser.openstack.org](https://superuser.openstack.org/articles/managing-port-level-security-openstack/).

///


### Sicherheit

/// details | Wie werden meine Server geschützt?

OVHcloud schützt seine gesamte Infrastruktur mit seinem exklusiven DDoS-Schutz. Darüber hinaus können Sie OpenStack-Sicherheitsgruppen hinzufügen: Dieser Schutz entspricht einer Firewall und wird direkt auf der OpenStack-Infrastruktur verwaltet, also Ihren Instanzen vorangestellt.

Lesen Sie die Anleitung [Eine Sicherheitsgruppe in Horizon erstellen und konfigurieren](/pages/public_cloud/compute/setup_security_group).

Mithilfe dieser Schutzmaßnahmen, zusammen mit denen, die Sie selbst auf Ihren Servern einrichten, können Sie die Zuverlässigkeit Ihrer Deployments optimieren.

///

/// details | Wie kann ich überprüfen, ob meine Instanz für die Sicherheitslücke "MDS" anfällig ist?

Die Anfälligkeit für die [Sicherheitslücke "MDS"](https://www.kernel.org/doc/html/latest/admin-guide/hw-vuln/mds.html) kann mit folgendem Befehl überprüft werden:

```bash
cat /sys/devices/system/cpu/vulnerabilities/mds
```

Auch wenn das Ergebnis `Vulnerable` ist, besteht kein Grund zur Sorge, da der zugrunde liegende Hypervisor Ihre Dienste schützt.

Sie können diese Sicherheitslücke auch direkt auf der Instanz abwehren, indem Sie entweder [über das OVHcloud Kundencenter](/pages/public_cloud/compute/first_steps_with_public_cloud_instance) oder mit einem Befehl wie diesem einen Hard Reboot Ihrer Instanz durchführen:

```bash
openstack server reboot --hard $serverID
```

///

/// details | Wie kann ich überprüfen, ob meine Instanz für die Sicherheitslücke "SSBD" anfällig ist?

Die Anfälligkeit für die [Sicherheitslücke "SSBD"](https://www.kernel.org/doc/html/latest/userspace-api/spec_ctrl.html) kann mit folgendem Befehl überprüft werden:

```bash
cat /sys/devices/system/cpu/vulnerabilities/ssbd
```

Auch wenn das Ergebnis `Vulnerable` ist, besteht kein Grund zur Sorge, da der zugrunde liegende Hypervisor Ihre Dienste schützt.

Dies kann nicht direkt über die Instanz behoben werden, da der *SSBD Flag* für Ihre Instanz nicht bereitgestellt wird.

Der Grund dafür ist, dass dies bei einigen Betriebssystemen Instabilität verursachen kann.

///

## Weiterführende Informationen

Treten Sie unserer [User Community](/links/community) bei.
