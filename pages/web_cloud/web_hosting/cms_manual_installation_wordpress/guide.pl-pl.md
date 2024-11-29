---
title: "Tutorial - Zainstaluj ręcznie WordPress"
excerpt: "Dowiedz się, jak ręcznie zainstalować CMS WordPress"
updated: 2023-04-06
---

## Wprowadzenie

Tutorial ten pomoże Ci ręcznie zainstalować CMS (Content Management System) WordPress w kilku etapach.

> [!warning]
>
> OVHcloud oddaje do Twojej dyspozycji usługi, których konfiguracja, zarządzanie i odpowiedzialność spoczywa na Ciebie. W związku z tym należy zapewnić ich prawidłowe funkcjonowanie.
> 
> Oddajemy w Twojej ręce niniejszy przewodnik, którego celem jest pomoc w jak najlepszym wykonywaniu bieżących zadań. W przypadku trudności zalecamy skorzystanie z pomocy [wyspecjalizowanego usługodawcy](/links/partner) lub [edytora CMS WordPress](https://wordpress.com/support/){.external}. Niestety firma OVHcloud nie będzie mogła udzielić wsparcia w tym zakresie. Więcej informacji znajduje się w sekcji ["Sprawdź również"](#go-further) niniejszego przewodnika.
>

> [!success]
>
> Aby zainstalować moduł WordPress **automatycznie** z poziomu [Panelu klienta OVHcloud](/links/manager), zapoznaj się z naszą dokumentacją dotyczącą [instalacji modułu za pomocą jednego kliknięcia](/pages/web_cloud/web_hosting/cms_install_1_click_modules).
>
> Aby zainstalować **ręcznie inny CMS** (Joomla!, Drupal, PrestaShop), zapoznaj się z naszą dokumentacją dotyczącą [ręczna instalacja CMS](/pages/web_cloud/web_hosting/cms_manual_installation).
>

**Dowiedz się, jak ręcznie zainstalować CMS WordPress.**

## Wymagania

- Posiadanie oferty[hostingu](/links/web/hosting), która zawiera przynajmniej jedną bazę danych.
- Posiadanie [domeny](/links/web/domains)
- Zalogowanie do[Panelu klienta OVHcloud](/links/manager){.external}

## W praktyce

### Etap 1 - przygotowanie instalacji <a name="step1"></a>

Aby zainstalować CMS **WordPress** na Twoim hostingu [hosting](/links/web/hosting), konieczne są pewne przygotowania.

Postępuj zgodnie z **wszystkie etapy** opisane w tutorialu dotyczącym [Ręczna instalacja CMS](/pages/web_cloud/web_hosting/cms_manual_installation) i przejdź do etapu 2 poniżej.

### Etap 2 - zakończenie ręcznej instalacji <a name="step3"></a>

> [!success]
>
> Przed kontynuowaniem instalacji, usuń cache przeglądarki internetowej, aby uniknąć błędów.
>

#### 2.1 - Przejście do strony WordPress za pomocą przeglądarki

Wpisz swoją domenę na pasku wyszukiwania przeglądarki internetowej.

Jeśli pliki źródłowe WordPress zostały poprawnie umieszczone w katalogu głównym, pojawi się strona WordPress pozwalająca na wybór języka:

![hosting](/pages/assets/screens/other/cms/wordpress/installation-select-language.png){.thumbnail}

Wybierz język strony i kliknij na `Continue`{.action}.

#### 2.2 - Powiązanie modułu WordPress z bazą danych

WordPress poprosi Cię o pobranie danych do logowania do bazy danych:

![hosting](/pages/assets/screens/other/cms/wordpress/installation-start.png){.thumbnail}

Przygotuj dane do logowania do bazy danych (w razie potrzeby sprawdź **etap 1.4** tutoriala na stronie [ręczna instalacja CMS](/pages/web_cloud/web_hosting/cms_manual_installation)), następnie kliknij na `Let's go !`{.action}, aby kontynuować.

Pojawi się następująca strona:

![hosting](/pages/assets/screens/other/cms/wordpress/installation-config-db.png){.thumbnail}

Wpisz wymagane informacje dotyczące bazy danych:

- *Database Name*: nazwa ta została zdefiniowana podczas tworzenia bazy danych w [Panelu klienta OVHcloud](/links/manager).

- *Username*: nazwa bazy danych jest identyczna, jeśli korzystasz z bazy danych zawartej w Twoim hostingu.
W przypadku baz danych utworzonych w ramach usługi Web Cloud Databases, zapoznaj się z informacjami podanymi w przewodniku **etap 1.4** w przewodniku dotyczącym [ręczna instalacja CMS](/pages/web_cloud/web_hosting/cms_manual_installation).

- *Password*: otrzymasz e-mail podczas tworzenia bazy danych. Możliwe, że zmieniłeś ją w międzyczasie.

- *Database Host*: wprowadź nazwę serwera Twojej bazy danych w e-mailu instalacyjnym lub w Panelu klienta. 

> [!primary]
> 
> - Nazwa serwera bazy danych zawarta w ofercie hostingu WWW ma zazwyczaj taką formę: `NameOfYourDatabase.mysql.db`. 
>
> - Nazwa serwera bazy danych Web Cloud Databases zaczyna się od Twojego identyfikatora klienta OVHcloud i ma następującą formę: `OVHID(without-ovh)-XXX.eu.clouddb.ovh.net` gdzie **"X"** należy zastąpić odniesieniem do Twojej usługi Web Cloud Databases.
>

- *Table Prefix*: jeśli instalacja jest wykonywana z nową bazą danych, wprowadź odpowiedni prefiks. Jeśli używasz bazy danych wykorzystywanej już przez inną stronę WWW, sprawdź **etap 1.4** tutoriala na [ręczna instalacja CMS](/pages/web_cloud/web_hosting/cms_manual_installation), aby nie wpisywać prefiksu tabeli już używanego w Twojej bazie danych.

Kliknij polecenie `Submit`{.action}, aby potwierdzić dane do logowania do bazy danych.

Jeśli wszystko przebiegło pomyślnie, wyświetli się następna strona:

![hosting](/pages/assets/screens/other/cms/wordpress/installation-step-after-db-1.png){.thumbnail}

Kliknij polecenie `Run the installation`{.action}.

#### 2.3 - Zdefiniuj dostęp administratora do usługi "back-office" dla modułu WordPress oraz do e-maila kontaktowego

Po zainstalowaniu modułu WordPress pojawi się problem z informacjami o przyszłej stronie WWW, w tym z utworzeniem identyfikatora Administratora WordPress.

Następnie będziesz mógł przejść do panelu administracyjnego, znanego jako "Back-office", Twojego CMS WordPress.

![hosting](/pages/assets/screens/other/cms/wordpress/installation-config-admin-user.png){.thumbnail}

Wpisz wymagane informacje:

- *Site Title*: wprowadź nazwę swojej strony.
- *Username*: zdefiniuj identyfikator administratora Twojego CMS.
- *Password*: zdefiniuj hasło dla tego identyfikatora administratora.
- *Your Email*: wprowadź poprawny adres e-mail.
- *Search Engine Visibility*: usuń zaznaczenie w tym polu, aby wyszukiwarki wskazywały WordPress.

Kliknij polecenie `Install WordPress`{.action} jak tylko wszystko jest poprawnie opisane.

#### 2.4 - Zakończenie ręcznej instalacji i przetestowanie dostępu "Administrator"

Instalacja zostanie zakończona, jeśli pojawi się następna strona:

![hosting](/pages/assets/screens/other/cms/wordpress/installation-successfull.png){.thumbnail}

Teraz kliknij przycisk `Log in`{.action}, aby przetestować dostęp do "Back-office" Twojego nowego CMS WordPress za pomocą identyfikatorów administratora utworzonych przed etapem 3.3.

> [!primary]
>
> OVHcloud nie zapewnia wsparcia w zakresie rozwiązań zewnętrznych, takich jak WordPress, dlatego nie może Ci towarzyszyć w korzystaniu z ani w konfiguracji CMS WordPress.
>
> Do tego celu zachęcamy do korzystania z forum dedykowanego do rozwiązania WordPress.
>

Po zalogowaniu pojawi się następująca strona:

![hosting](/pages/assets/screens/other/cms/wordpress/admin-interface.png){.thumbnail}

> [!success]
>
> Możesz teraz rozpocząć tworzenie zawartości swojej strony WordPress!
>

## Sprawdź również <a name="go-further"></a>

[Oficjalna strona WordPress](https://wordpress.org)

W przypadku wyspecjalizowanych usług (pozycjonowanie, rozwój, etc.) skontaktuj się z [partnerami OVHcloud](/links/partner).

Jeśli chcesz otrzymywać wsparcie w zakresie konfiguracji i użytkowania Twoich rozwiązań OVHcloud, zapoznaj się z naszymi [ofertami pomocy](/links/support).

Dołącz do [grona naszych użytkowników](/links/community). 