---
title: "Zmiana hasła do konta FTP"
excerpt: "Dowiedz się, jak zmienić hasło dla użytkownika FTP utworzonego na Twoim hostingu"
updated: 2024-02-29
---

## Wprowadzenie 

Wraz z pakietami hostingowymi OVHcloud zyskujesz dostęp do przestrzeni dyskowej plików online dostępnej w protokole **FTP**: przestrzeni dyskowej FTP.

Dostęp do przestrzeni dyskowej możliwy jest za pomocą **użytkownika FTP** oraz przypisanego do niego hasła.

W szczególności dostęp ten umożliwia [umieszczenie strony w Internecie](/pages/web_cloud/web_hosting/hosting_how_to_get_my_website_online).

**Dowiedz się, jak zmienić hasło do konta FTP utworzonego na Twoim hostingu.**

> [!warning]
>
> OVHcloud oddaje do Twojej dyspozycji usługi, których konfiguracja, zarządzanie i odpowiedzialność spoczywają na Ciebie. W związku z tym należy zapewnić ich prawidłowe funkcjonowanie.
>
> Oddajemy w Twojej ręce niniejszy przewodnik, którego celem jest pomoc w jak najlepszym wykonywaniu bieżących zadań. W przypadku trudności zalecamy skorzystanie z pomocy [wyspecjalizowanego usługodawcy](/links/partner). Niestety firma OVHcloud nie będzie mogła udzielić wsparcia w tym zakresie. Więcej informacji znajduje się w sekcji ["Sprawdź również"](#go-further) niniejszego przewodnika.
>

## Wymagania początkowe

- Posiadanie [hostingu OVHcloud](/links/web/hosting).
- Dostęp do [Panelu klienta OVHcloud](/links/manager).

## W praktyce

### Etap 1: dostęp do zarządzania użytkownikami FTP

Zaloguj się do [Panelu klienta OVHcloud](/links/manager), przejdź do sekcji `Web Cloud`{.action}, kliknij `Hosting`{.action}, a następnie wybierz odpowiednią nazwę hostingu. Wybierz kartę `FTP-SSH`{.action}.

Tabela wyświetla *użytkowników FTP* utworzonych na Twoim hostingu. Użytkownicy ci umożliwiają dostęp do Twojej przestrzeni dyskowej FTP, aby umieścić w Internecie pliki z Twojej strony WWW. Użytkownik jest tworzony automatycznie podczas instalacji hostingu.

### Etap 2: zmiana hasła użytkownika FTP

> [!primary]
>
> Aby uzyskać więcej informacji na temat dobrych praktyk w zakresie zarządzania hasłami, zapoznaj się z instrukcjami zawartymi w tym [przewodniku](/pages/account_and_service_management/account_information/manage-ovh-password).
>

W zależności od pakietu [hostingowego OVHcloud](/links/web/hosting) zmiana hasła do konta FTP w zakładce `FTP-SSH`{.action} zostanie wykonana na dwie różne sposoby:

- **w przypadku pakietów, które nie pozwalają na utworzenie drugiego użytkownika FTP** (oferty *Darmowy hosting 100M* i *Perso*): kliknij *piktogram w formie ołówka* w kolumnie `Hasło`{.action} tabeli, która się wyświetla, wprowadź nowe hasło **zgodnie z polityką haseł**, a następnie potwierdź zmianę, klikając *zielony przycisk* do zatwierdzenia.

![change-ftp-password-step1-perso](/pages/assets/screens/control_panel/product-selection/web-cloud/web-hosting/ftp-ssh/change-password-perso.png){.thumbnail}

- **w przypadku pakietów umożliwiających utworzenie kilku użytkowników FTP** (oferty *Pro* i *Performance*): kliknij przycisk `...`{.action} po prawej stronie odpowiedniego użytkownika FTP a następnie kliknij `Zmień hasło`{.action}. W oknie, które się wyświetla wprowadź nowe hasło **zgodnie z polityką haseł**, potwierdź, wprowadzając je ponownie i klikając przycisk `Zatwierdź`{.action}.

![change-ftp-password-pro](/pages/assets/screens/control_panel/product-selection/web-cloud/web-hosting/ftp-ssh/change-password-pro.png){.thumbnail}

> [!primary]
>
> Nowe hasło powinno być zgodne z następującą **polityką haseł** :
>
>- Minimum 8 znaki;
>- Maksymalnie 30 znaków;
>- Przynajmniej jedna wielka litera;
>- Przynajmniej jedna mała litera;
>- Przynajmniej jedną cyfrę;
>- Składać się wyłącznie z cyfr i liter.

Następnie przejdź do zakładki `Zadania w realizacji`{.action} i odśwież stronę regularnie. Efekty modyfikacji to zaledwie kilka minut.

### Etap 3: dostęp do Twojej przestrzeni dyskowej

Aby uzyskać dostęp do przestrzeni FTP, zapoznaj się z naszym przewodnikiem "[Logowanie do przestrzeni dyskowej Twojego hostingu](/pages/web_cloud/web_hosting/ftp_connection)".

## Sprawdź również <a name="go-further"></a>

[Tworzenie i zarządzanie hasłem do konta](/pages/account_and_service_management/account_information/manage-ovh-password)

[Logowanie do przestrzeni dyskowej hostingu](/pages/web_cloud/web_hosting/ftp_connection)

[Umieszczenie strony WWW w Internecie](/pages/web_cloud/web_hosting/hosting_how_to_get_my_website_online)

W przypadku wyspecjalizowanych usług (pozycjonowanie, rozwój, etc.) skontaktuj się z [partnerami OVHcloud](/links/partner).

Jeśli chcesz otrzymywać wsparcie w zakresie konfiguracji i użytkowania Twoich rozwiązań OVHcloud, zapoznaj się z naszymi [ofertami pomocy](/links/support).

Dołącz do [grona naszych użytkowników](/links/community).