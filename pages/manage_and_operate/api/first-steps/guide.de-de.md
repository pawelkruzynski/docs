---
title: Erste Schritte mit der OVHcloud API
excerpt: Erfahren Sie hier, wie Sie die OVHcloud API verwenden
updated: 2024-06-07
---

> [!primary]
> Diese Übersetzung wurde durch unseren Partner SYSTRAN automatisch erstellt. In manchen Fällen können ungenaue Formulierungen verwendet worden sein, z.B. bei der Beschriftung von Schaltflächen oder technischen Details. Bitte ziehen Sie im Zweifelsfall die englische oder französische Fassung der Anleitung zu Rate. Möchten Sie mithelfen, diese Übersetzung zu verbessern? Dann nutzen Sie dazu bitte den Button "Beitragen" auf dieser Seite.
>

## Ziel

Die unter [https://api.ovh.com/](https://api.ovh.com/){.external} verfügbare API erlaubt es Ihnen, OVHcloud Produkte zu bestellen, zu verwalten, zu aktualisieren und zu konfigurieren, ohne ein grafisches Interface wie das Kundencenter zu verwenden.

**Hier erfahren Sie, wie Sie die OVHcloud API verwenden und mit Ihren Anwendungen verbinden.**

## Voraussetzungen

- Sie verfügen über einen aktiven OVHcloud Kunden-Account und dessen Zugangsdaten.
- Sie sind auf der Webseite der [OVHcloud API](https://api.ovh.com/){.external}.

## In der praktischen Anwendung

> [!warning]
> OVHcloud stellt Ihnen Dienstleistungen zur Verfügung, für deren Konfiguration und Verwaltung Sie die alleinige Verantwortung tragen. Es liegt somit bei Ihnen, sicherzustellen, dass diese ordnungsgemäß funktionieren.
> 
> Diese Anleitung soll Sie bei allgemeinen Aufgaben bestmöglich unterstützen. Dennoch empfehlen wir Ihnen, falls Sie Hilfe brauchen, einen [spezialisierten Dienstleister](https://partner.ovhcloud.com/de/directory/) zu kontaktieren und/oder Ihre Fragen in der OVHcloud Community zu stellen. Leider können wir Ihnen für administrative Aufgaben keine weitergehende technische Unterstützung anbieten. Weitere Informationen finden Sie am [Ende dieser Anleitung](#gofurther).
>

### Grundlegende Funktionen

#### Verbindung mit der OVHcloud API

Klicken Sie auf der [OVHcloud API Seite](https://api.ovh.com/) auf `Explore the OVH API`{.action}, um die Liste der API-Funktionen anzuzeigen.

Um die API für Ihre Dienste zu verwenden, loggen Sie sich mit Ihren OVHcloud Zugangsdaten ein:

- Klicken Sie oben rechts auf `Authentication`{.action}.
- Klicken Sie anschließend auf `Login with OVHcloud SSO`{.action}.
- Geben Sie Ihre OVHcloud Kunden-Zugangsdaten ein.
- Klicken Sie auf den Button `Authorize`{.action}, um API-Aufrufe von dieser Seite aus zuzulassen.

![API](images/login.png){.thumbnail} 

> [!primary]
>
> Wenn Ihr OVHcloud Account durch [Zwei-Faktor-Authentifizierung](/pages/account_and_service_management/account_information/secure-ovhcloud-account-with-2fa) geschützt ist, müssen Sie auch den per SMS, OTP-Anwendung oder U2F-Schlüssel generierten Code eingeben.
>

#### Die mit API verfügbaren Dienste analysieren

Alle OVHcloud Dienste, die über API-Zugang verwaltet werden können werden in der Liste links angezeigt.

![API](images/api-list.png){.thumbnail} 

Um zum Beispiel die zu Domainnamen gehörenden API-Aufrufe anzuzeigen, klicken Sie auf **/domain** in der Liste.

Nachdem Sie auf die Dienstbezeichnung geklickt haben, wird die Liste der verfügbaren API-Funktionen angezeigt. 

![API](images/api-displayed.png){.thumbnail}

Sie haben auch einen Selektor auf der linken Seite der Produktliste, mit dem Sie zwischen den API-Zweigen **/v1** und **/v2** wählen können. Wenn Sie mit dem Prinzip der API-Verzweigung nicht vertraut sind, lesen Sie [unsere Dokumentation zur API v2](/pages/manage_and_operate/api/apiv2).

#### API-Aufrufe ausführen

Es sind 4 HTTP-Methoden für die API verfügbar: 

**GET** 

Die GET-Methode dient dem Abruf von Daten aus einer Ressource.

Um zum Beispiel die Liste Ihrer Domainnamen abzurufen, verwenden Sie folgenden Aufruf:
 
> [!api]
>
> @api {v1} /domain GET /domain
>

**POST**

Die POST-Methode wird verwendet, um zusätzliche Daten an die Ressource zu senden. 

Um zum Beispiel einen Eintrag zu Ihrer DNS Zone hinzuzufügen, verwenden Sie folgenden Aufruf:

> [!api]
>
> @api {v1} /domain POST /domain/zone/{zoneName}/record
>

**PUT**

Die PUT-Methode dient dazu, die aktuellen Ressourcen-Daten durch die Daten der Abfrage zu ersetzen.

Um beispielsweise einen Eintrag in Ihrer DNS Zone zu korrigieren, verwenden Sie folgenden Aufruf:

> [!api]
>
> @api {v1} /domain PUT /domain/zone/{zoneName}/record/{id}
>

**DELETE**

Die DELETE-Methode wird verwendet, um die Ressource zu löschen.

Um beispielsweise einen Eintrag in Ihrer DNS Zone zu löschen, verwenden Sie folgenden Aufruf:

> [!api]
>
> @api {v1} /domain DELETE /domain/zone/{zoneName}/record/{id}
>

##### Parameter der API

Nachdem Sie auf den Endpunkt Ihrer Wahl geklickt haben, können Sie im Bereich **Request** Ausführungsvariablen eingeben.
 
Um zum Beispiel einen TXT Eintrag in Ihrer DNS Zone hinzuzufügen, editieren Sie die folgenden Einstellungen:
 	
![API](images/parameters.png){.thumbnail} 
 
Wenn Sie die Parameter festgelegt haben, können Sie die Ausführung des Aufrufs starten, indem Sie auf `TRY`{.action} klicken. 

Der Tab `Response` zeigt den Bericht zur Durchführung des API-Aufrufs.

![API](images/result.png){.thumbnail} 

Die Tabs `PHP` und `Python` enthalten die Elemente, die entsprechend der Anwendungssprache in Ihrem Skript hinzugefügt werden müssen.

### Fortgeschrittene Nutzung: OVHcloud API mit einer Anwendung verbinden

#### Schlüssel für Ihre Anwendung erstellen

Jede Anwendung, die mit der OVHcloud API kommunizieren möchte, muss zuerst freigegeben werden.

Klicken Sie hierzu auf folgenden Link: [https://eu.api.ovh.com/createToken/](https://eu.api.ovh.com/createToken/){.external}.

Geben Sie Ihre Kundenkennung, Ihr Passwort und den Namen Ihrer Anwendung ein. Der Name kann nützlich sein, um anderen Personen Zugriff zu gewähren.

Sie können auch eine Beschreibung der Anwendung und eine Zeitangabe hinzufügen. 

Der Eintrag `Rights` erlaubt es, die Verwendung der Anwendung auf bestimmte Funktionen zu beschränken.<br>
Um eine HTTP-Methode für alle Endpunkte zu erlauben, geben Sie im Feld einen Stern (`*`) ein. Im folgenden Beispiel werden alle GET-Abfragen erlaubt:

![API keys](images/api-keys.png){.thumbnail} 

Wenn Sie auf `Create Keys`{.action} klicken, erhalten Sie drei Schlüssel:

- Den Anwendungsschlüssel **AK**. Zum Beispiel:

```console
7kbG7Bk7S9Nt7ZSV
```

- Den geheimen, nicht zur Veröffentlichung bestimmten Anwendungsschlüssel **AS**. Zum Beispiel:

```console
EXEgWIz07P0HYwtQDs7cNIqCiQaWSuHF
```

- Den geheimen, nicht zur Veröffentlichung bestimmten "**Consumer Key**" oder **CK**. Zum Beispiel:

```console
MtSwSrPpNjqfVSmJhLbPyr2i45lSwPU1
```

In diesem Fall ist der Schlüssel vom Typ **CK** an Ihren Account gebunden.

Der **CK**-Token kann für die Übertragung von Rechten verwendet werden. Weitere Informationen finden Sie in dieser Anleitung: [How to manage a customer’s account via OVHcloud API](/pages/manage_and_operate/api/api_right_delegation) (EN).

#### Erste Verwendung der API

Sobald Ihre drei Schlüssel (**AK**, **AS**, **CK**) verfügbar sind, können Sie die API Anfragen signieren. Die Signatur wird wie folgt berechnet:

```console
"$1$" + SHA1_HEX(AS+"+"+CK+"+"+METHOD+"+"+QUERY+"+"+BODY+"+"+TSTAMP)
```

Um die Entwicklung Ihrer Anwendungen zu vereinfachen, stellt OVHcloud API-Wrapper in mehreren Sprachen bereit.
Wenn Sie diese verwenden, müssen Sie sich nicht um die Berechnung der Signatur kümmern und können sich auf die Programmierung Ihrer Anwendung konzentrieren.

- *Go* : <https://github.com/ovh/go-ovh>
- *Perl*: <https://github.com/ovh/perl-ovh>
- *Python*: <https://github.com/ovh/python-ovh>
- *PHP*: <https://github.com/ovh/php-ovh>
- *Node.js*: <https://github.com/ovh/node-ovh>
- *C#*: <https://github.com/ovh/csharp-ovh>

Hier ein Beispiel für die Nutzung der Rubrik `/me` zur Verwaltung Ihres OVHcloud Kunden-Accounts:

```python
import ovh

# Instantiate. Visit https://api.ovh.com/createToken/?GET=/me
# to get your credentials
client = ovh.Client(
    endpoint='ovh-eu',
    application_key='<application key>',
    application_secret='<application secret>',
    consumer_key='<consumer key>',
)

# Print nice welcome message
print("Welcome", client.get('/me')['firstname'])
```

#### Schlüssel auflisten und widerrufen

Es gibt derzeit keine Option im Kundencenter, mit der Sie Ihre Schlüssel auflisten und widerrufen können. Dazu kann das API-Portal verwendet werden:

- Erhalten Sie die Schlüssel-IDs mit dem folgenden Aufruf:

> [!api]
>
> @api {v1} /me GET /me/api/application
>

- Erhalten Sie die Schlüsseldetails mit dem folgenden Aufruf:

> [!api]
>
> @api {v1} /me GET /me/api/application/{applicationId}
>

- Widerrufen Sie einen Schlüssel mit dem folgenden Aufruf:

> [!api]
>
> @api {v1} /me DELETE /me/api/application/{applicationId}
>

## Weiterführende Informationen <a name="gofurther"></a>

[Domainnamen über die API verwalten](/pages/web_cloud/domains/api_domain_intro) (EN)

[OVHcloud Kunden-Account über die API verwalten](/pages/manage_and_operate/api/api_right_delegation) (EN)

Für den Austausch mit unserer User Community gehen Sie auf <https://community.ovh.com/en/>.
