---
title: 'E-Mail-Accounts mit MX Plan erstellen'
excerpt: 'Erfahren Sie hier, wie Sie einen MX Plan E-Mail-Account erstellen'
updated: 2024-06-13
---

> [!primary]
> Diese Übersetzung wurde durch unseren Partner SYSTRAN automatisch erstellt. In manchen Fällen können ungenaue Formulierungen verwendet worden sein, z.B. bei der Beschriftung von Schaltflächen oder technischen Details. Bitte ziehen Sie im Zweifelsfall die englische oder französische Fassung der Anleitung zu Rate. Möchten Sie mithelfen, diese Übersetzung zu verbessern? Dann nutzen Sie dazu bitte den Button "Beitragen" auf dieser Seite.
>

## Ziel

Sie haben gerade eine MX Plan E-Mail-Lösung erworben. Diese bietet Ihnen E-Mail-Accounts die mit Domainnamen verknüpft sind.

**Diese Anleitung erklärt, wie Sie einen E-Mail-Account mit Ihrem MX Plan erstellen.**

## Voraussetzungen

- Sie verfügen über ein MX Plan Angebot, entweder in einem [OVHcloud Webhosting](/links/web/hosting) enthalten, separat bestellt, oder enthalten in [Kostenloses Hosting 100M](/links/web/domains-free-hosting).
- Sie haben Zugriff auf Ihr [OVHcloud Kundencenter](/links/manager), Bereich `Web Cloud`{.action}.

> [!primary]
>
> **Sonderfälle**
>
> - Hinweis zu Kostenloses Hosting 100M: Es muss zuerst [aktiviert werden](/pages/web_cloud/web_hosting/activate_start10m), um einen E-Mail-Account zu erstellen. Sie können diese Operation über Ihr [OVHcloud Kundencenter](/links/manager) durchführen, indem Sie die betreffende Domain auswählen.
> - Bei einem Webhosting muss der [inkludierte MX Plan aktiviert werden](/links/web/hosting), bevor Sie die übrigen Schritte dieser Anleitung durchführen. Lesen Sie hierzu unsere Anleitung zur [Aktivierung der im Webhosting enthaltenen E-Mail-Accounts](/pages/web_cloud/web_hosting/activate-email-hosting).

## ## In der praktischen Anwendung <a name="instructions"></a>

Je nach Aktivierungsdatum Ihres Dienstes und je nachdem, ob Ihr Dienst vor Kurzem migriert wurde, verfügen Sie entweder über die historische oder die neue MX Plan Version. Bevor Sie fortfahren, ermitteln Sie zunächst Ihre Dienstversion.

Loggen Sie sich hierzu in Ihr [OVHcloud Kundencenter](/links/manager) ein. Öffnen Sie im Bereich `Web Cloud`{.action} den Eintrag `E-Mails`{.action} und wählen Sie dann den Namen des betreffenden MX Plan Dienstes aus. Fahren Sie entsprechend Ihrer MX Plan Version fort.

|Historische MX Plan Version|Neue MX Plan Version|
|---|---|
|![E-Mail](images/mxplan-creation-legacy-step1.png){.thumbnail}<br> Ihr Angebot wird im Abschnitt „Abo“ angezeigt.|![E-Mail](images/mxplan-creation-new-step1.png){.thumbnail}<br>Die `Server-Referenz` steht in der Box „Zusammenfassung“.|
|Weiter zur [historischen MX Plan Version](#mxplanlegacy)|Weiter zur [neuen MX Plan Version](#newmxplan)|

### Neue MX Plan Version <a name="newmxplan"></a>

#### Zugang zur Verwaltung des E-Mail-Dienstes

Bei der neuen MX Plan Version sollte die Anzeige der folgenden Abbildung entsprechen. Ist das nicht der Fall, überprüfen Sie [mithilfe der oben stehenden Informationen](./#instructions), dass Sie den richtigen Schritten folgen.

![E-Mail](images/mxplan-creation-new-step1.png){.thumbnail}

#### Einen E-Mail-Account erstellen

Um einen neuen E-Mail-Account zu erstellen, gehen Sie in den Tab `E-Mail-Accounts`{.action}. Das angezeigte Fenster enthält bereits vorhandene E-Mail-Accounts sowie die Anzahl der Accounts, die Sie noch anlegen können. Klicken Sie auf den Button `Account hinzufügen`{.action}.

![E-Mail](images/mxplan-creation-new-step2.png){.thumbnail}

Geben Sie im neu angezeigten Fenster die angeforderten Informationen ein.

- **E-Mail Account**: Im Textfeld ist bereits ein vorläufiger Name angegeben. Fügen Sie hier Ihre gewünschte E-Mail-Adresse ein (zum Beispiel vorname.name). Der Domainname der E-Mail-Adresse ist bereits in der Liste vorausgewählt.

> [!warning]
>
> Die Wahl des Namens Ihrer E-Mail-Adresse muss folgende Bedingungen erfüllen:
>
> - Mindestens 2 Zeichen
> - Maximal 32 Zeichen
> - Keine Zeichen mit Akzent
> - Keine Sonderzeichen außer `.`, `,`, `-` und `_`

- **Vorname**: Geben Sie einen Vornamen an.
- **Name**: Geben Sie einen Nachnamen an.
- **Anzeigename**: Geben Sie den Namen an, der als Absender angezeigt werden soll, wenn E-Mails mit dieser Adresse verschickt werden.
- **Passwort**: Wählen Sie ein Passwort und bestätigen Sie es. Aus Sicherheitsgründen empfehlen wir Ihnen, Passwörter nicht mehrfach zu verwenden, sondern ein neues auszuwählen, das keinerlei Zusammenhang mit Ihren persönlichen Angaben hat (beispielsweise Namen, Vornamen oder Ihr Geburtsdatum). Es wird empfohlen, das Passwort regelmäßig zu ändern.

> [!warning]
>
> Die Wahl des Passworts muss folgende Bedingungen erfüllen:
>
> - Mindestens 9 Zeichen
> - Maximal 30 Zeichen
> - Keine Zeichen mit Akzent

Wenn Sie die Felder ausgefüllt haben, klicken Sie auf den Button `Weiter`{.action}.

![E-Mail](images/mxplan-creation-new-step3.png){.thumbnail}

Überprüfen Sie die in der Übersicht angezeigten Informationen. Sind alle Angaben korrekt, klicken Sie auf `Bestätigen`{.action}. Der neu hinzugefügte Account erscheint nun in der Tabelle. Warten Sie kurz ab, bis der Account verfügbar ist.

Führen Sie diesen Schritt so oft wie nötig durch (je nach Anzahl Ihrer Accounts).

#### E-Mails einsehen

Gehen Sie auf die [Webmail Loginseite](/links/web/email) und geben Sie die betreffende E-Mail-Adresse sowie das zugehörige Passwort ein. Klicken Sie anschließend auf den Button `Login`{.action}.

Beim ersten Login werden Sie aufgefordert, die Sprache sowie Ihre Zeitzone festzulegen. Daraufhin wird Ihr Postfach angezeigt. Um herauszufinden, wie Sie Ihre E-Mail-Adresse mit Outlook Web App (OWA) nutzen, lesen Sie unsere Anleitung zur [Verwendung von E-Mail-Accounts über Outlook Web App (OWA)](/pages/web_cloud/email_and_collaborative_solutions/using_the_outlook_web_app_webmail/email_owa).

![E-Mail](images/mxplan-creation-new-step5.png){.thumbnail}

Um Ihre E-Mails über ein E-Mail-Programm einzusehen, finden Sie die entsprechenden Informationen im Bereich "[E-Mail-Account von einem Client aus anzeigen](#configdevices)".

#### Einen E-Mail Account löschen

In der neuen MX Plan Version wird das Löschen eines Accounts als *Zurücksetzen des Accounts* bezeichnet.

> [!warning]
>
> Bevor Sie E-Mail-Accounts löschen, überprüfen Sie, dass diese nicht verwendet werden. Eine Sicherung dieser Accounts kann notwendig sein. Wenn nötig lesen Sie die Anleitung ["Ihre E-Mail-Adresse manuell migrieren"](/pages/web_cloud/email_and_collaborative_solutions/migrating/manual_email_migration), in der beschrieben wird, wie Sie Daten eines Accounts über Ihr Kundencenter oder ein E-Mail-Programm exportieren.

Klicken Sie im Tab `E-Mail-Accounts`{.action} auf den Button `...`{.action} rechts vom zu löschenden Account und danach auf `Diesen Account zurücksetzen`{.action}.

![E-Mail](images/mxplan-new-reset.png){.thumbnail}

### Historische MX Plan Version <a name="mxplanlegacy"></a>

#### Zugang zur Verwaltung des E-Mail-Dienstes

Bei der historischen MX Plan Version sollte die Anzeige der folgenden Abbildung entsprechen. Ist das nicht der Fall, überprüfen Sie [mithilfe der oben stehenden Informationen](./#instructions), dass Sie den richtigen Schritten folgen.

![E-Mail](images/mxplan-creation-legacy-step1.png){.thumbnail}

#### Einen E-Mail Account erstellen

Um eine neue E-Mail-Adresse zu erstellen, gehen Sie in den Tab `E-Mails`{.action}. Die angezeigte Tabelle enthält alle E-Mail-Accounts, die im Rahmen Ihres MX Plan Angebots erstellt wurden. Klicken Sie nun auf den Button `Eine E-Mail-Adresse erstellen`{.action}.

![E-Mail](images/mxplan-creation-legacy-step2.png){.thumbnail}

Geben Sie im angezeigten Fenster die angeforderten Informationen ein.

- **Name des Accounts**: Fügen Sie hier Ihre gewünschte E-Mail-Adresse ein (zum Beispiel vorname.name). Die betreffende Domain ist bereits standardmäßig angegeben.
- **Kontobeschreibung**: Geben Sie eine kurze Beschreibung ein, damit Sie diesen Account später von anderen Accounts in Ihrem OVHcloud Kundencenter unterscheiden können.
- **Account-Größe**: Wählen Sie die gewünschte Account-Größe aus. Hierbei handelt es sich um den Speicherplatz, den Ihr Account zum Speichern von Nachrichten nutzen kann. 
- **Passwort**: Wählen Sie ein Passwort und bestätigen Sie es. Aus Sicherheitsgründen empfehlen wir Ihnen, Passwörter nicht mehrfach zu verwenden, sondern ein neues auszuwählen, das keinerlei Zusammenhang mit Ihren persönlichen Angaben hat (beispielsweise Namen, Vornamen oder Ihr Geburtsdatum). Es wird empfohlen, das Passwort regelmäßig zu ändern.

Wenn Sie die Felder ausgefüllt haben, klicken Sie auf den Button `Weiter`{.action}. 

![E-Mail](images/mxplan-creation-legacy-step3.png){.thumbnail}

Überprüfen Sie die in der Übersicht angezeigten Informationen. Sind alle Angaben korrekt, klicken Sie erneut auf `Weiter`{.action}. Klicken Sie zum Abschluss auf `Bestätigen`{.action}, um den E-Mail-Account zu erstellen. Warten Sie kurz ab, bis der Account verfügbar ist.

Führen Sie diesen Schritt so oft wie nötig durch (je nach Anzahl Ihrer Accounts).

#### E-Mails einsehen 

Gehen Sie auf die [Webmail Loginseite](/links/web/email) und geben Sie die betreffende E-Mail-Adresse sowie das zugehörige Passwort ein. Klicken Sie anschließend auf den Button `Login`{.action}.

Daraufhin wird Ihr Postfach angezeigt. Weitere Informationen finden Sie in unserer Anleitung zur [Verwendung Ihres E-Mail-Accounts mit RoundCube Webmail](/pages/web_cloud/email_and_collaborative_solutions/mx_plan/email_roundcube).

![E-Mail](images/mxplan-creation-legacy-step4.png){.thumbnail}

Um Ihre E-Mails über ein E-Mail-Programm einzusehen, finden Sie die entsprechenden Informationen im Bereich "[E-Mail-Account von einem Client aus anzeigen](#configdevices)".

#### Einen E-Mail Account löschen

> [!warning]
>
> Bevor Sie E-Mail-Accounts löschen, überprüfen Sie, dass diese nicht verwendet werden. Eine Sicherung dieser Accounts kann notwendig sein. Wenn nötig lesen Sie die Anleitung [Ihre E-Mail-Adresse manuell migrieren](/pages/web_cloud/email_and_collaborative_solutions/migrating/manual_email_migration), in der beschrieben wird, wie Sie Daten eines Accounts über Ihr Kundencenter oder ein E-Mail-Programm exportieren.

Klicken Sie im Tab `E-Mail-Accounts`{.action} rechts neben dem zu löschenden Account auf `...`{.action} und dann auf `Account löschen`{.action}.

![E-Mail](images/mxplan-legacy-reset.png){.thumbnail}

### E-Mail-Account von einem Client aus anzeigen <a name="configdevices"></a>

Sie können Ihre E-Mail-Accounts auf Ihrem gewünschten Gerät konfigurieren (z. B. einem Smartphone oder Tablet). Folgen Sie hierzu unseren Konfigurationsanleitungen:

> [!tabs]
> **Windows**
>>
>> - [Mail auf Windows 10](/pages/web_cloud/email_and_collaborative_solutions/mx_plan/how_to_configure_windows_10)
>> - [Outlook](/pages/web_cloud/email_and_collaborative_solutions/mx_plan/how_to_configure_outlook_2016)
>> - [Thunderbird](/pages/web_cloud/email_and_collaborative_solutions/mx_plan/how_to_configure_thunderbird_windows)
>>
> **Apple**
>>
>> - [macOS Mail](/pages/web_cloud/email_and_collaborative_solutions/mx_plan/how_to_configure_mail_macos)
>> - [Mail für iPhone oder iPad](/pages/web_cloud/email_and_collaborative_solutions/mx_plan/how_to_configure_ios)
>> - [Outlook Mac OS](/pages/web_cloud/email_and_collaborative_solutions/mx_plan/how_to_configure_outlook_2016_mac)
>> - [Thunderbird](/pages/web_cloud/email_and_collaborative_solutions/mx_plan/how_to_configure_thunderbird_mac)
>>
> **Android**
>>
>> - [Android](/pages/web_cloud/email_and_collaborative_solutions/mx_plan/how_to_configure_android)
>>
> **Andere**
>>
>> - [Interface Gmail](/pages/web_cloud/email_and_collaborative_solutions/mx_plan/how_to_configure_gmail)
>>

Wenn Sie nur die Informationen zur Konfiguration Ihres E-Mail-Accounts benötigen, verwenden Sie die folgenden Einstellungen:

> [!alert]
>
> Vergewissern Sie sich, dass die oben rechts auf dieser Seite angezeigte Markierung Ihrem Land bzw. Region enptspricht. **Die folgenden Einstellungen sind je nach Land/Region unterschiedlich.**

> [!tabs]
> **IMAP-Konfiguration (empfohlen)**
>>
>> |Information|Beschreibung|
>> |---|---|
>> |Nutzername|Geben Sie die **vollständige E-Mail-Adresse ein**|
>> |Passwort|Geben Sie das Passwort des E-Mail-Accounts ein|
>> |Server (eingehend)|imap.mail.ovh.net **oder** ssl0.ovh.net|
>> |Port|993|
>> |Sicherheitstyp|SSL/TLS|
>>
> **POP-Konfiguration**
>>
>> |Information|Beschreibung|
>> |---|---|
>> |Nutzername|Geben Sie die **vollständige E-Mail-Adresse ein**|
>> |Passwort|Geben Sie das Passwort des E-Mail-Accounts ein|
>> |Server (eingehend)|pop.mail.ovh.net **oder** ssl0.ovh.net|
>> |Port|995|
>> |Sicherheitstyp|SSL/TLS|
>>
> **SMTP-Konfiguration**
>>
>> |Information|Beschreibung|
>> |---|---|
>> |Nutzername|Geben Sie die **vollständige E-Mail-Adresse ein**|
>> |Passwort|Geben Sie das Passwort des E-Mail-Accounts ein|
>> |Server (ausgehend)|smtp.mail.ovh.net **oder** ssl0.ovh.net|
>> |Port|465|
>> |Sicherheitstyp|SSL/TLS|
>>

> [!warning]
>
> Sollten Sie Schwierigkeiten bei der Konfiguration des E-Mail-Accounts in Ihrem Client haben, [verwenden Sie unsere Konfigurationsanleitungen](/products/web-cloud-email-collaborative-solutions-mx-plan) oder wenden Sie sich an den Herausgeber der von Ihnen verwendeten Anwendung, falls die Einrichtung spezielle Anpassungen erfordert.
>

## Weiterführende Informationen

Treten Sie unserer [User Community](/links/community) bei.
