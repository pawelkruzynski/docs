---
title: "Tutorial - Ręczna instalacja PrestaShop"
excerpt: "Dowiedz się, jak ręcznie zainstalować CMS PrestaShop"
updated: 2023-04-07
---
  
## Wprowadzenie

Tutaj znajdziesz wszystkie elementy do ręcznego zainstalowania systemu CMS (Content Management System) PrestaShop.

> [!warning]
>
> OVHcloud oddaje do Twojej dyspozycji usługi, których konfiguracja, zarządzanie i odpowiedzialność spoczywają na Ciebie. W związku z tym należy zapewnić ich prawidłowe funkcjonowanie.
> 
> Oddajemy w Twojej ręce niniejszy przewodnik, którego celem jest pomoc w jak najlepszym wykonywaniu bieżących zadań. W przypadku trudności zalecamy skorzystanie z pomocy [wyspecjalizowanego usługodawcy](/links/partner) lub [edytora CMS PrestaShop](https://www.prestashop.com/en/support){.external}. Niestety firma OVH nie będzie mogła udzielić wsparcia w tym zakresie. Więcej informacji znajduje się w sekcji ["Sprawdź również"](#go-further) niniejszego przewodnika.
>

> [!success]
>
> Aby zainstalować PrestaShop **automatycznie** z poziomu [Panelu klienta OVHcloud](/links/manager), zapoznaj się z naszą dokumentacją dotyczącą [instalacji modułu "za jednym kliknięciem"](/pages/web_cloud/web_hosting/cms_install_1_click_modules).
>
> Aby zainstalować **ręcznie inny CMS** (WordPress, Joomla!, Drupal), zapoznaj się z naszą dokumentacją dotyczącą [ręczna instalacja CMS](/pages/web_cloud/web_hosting/cms_manual_installation).
>

**Dowiedz się, jak ręcznie zainstalować CMS PrestaShop**
  
## Wymagania początkowe

- Posiadanie oferty[hostingu](/links/web/hosting), która zawiera co najmniej jedną bazę danych.
- Posiadanie [domeny](/links/web/domains)
- Dostęp do [Panelu klienta OVHcloud](/links/manager){.external}
  
## W praktyce

### Etap 1 - przygotowanie instalacji <a name="step1"></a>

Aby zainstalować CMS **PrestaShop** na Twoim hostingu [hosting www](/links/web/hosting), konieczne są pewne przygotowania.

Postępuj zgodnie z **wszystkie etapy** opisane w tutorialu dotyczącym[Ręczna instalacja CMS](/pages/web_cloud/web_hosting/cms_manual_installation) i przejdź do etapu 2 poniżej.

### Etap 2 - zakończenie ręcznej instalacji <a name="step2"></a>

> [!success]
>
> Przed kontynuowaniem instalacji, usuń cache przeglądarki internetowej, aby uniknąć błędów.
>

Jeśli nie pobrałeś najnowszej dostępnej wersji PrestaShop, pojawi się następująca strona:

![PrestaShop installation step 1](/pages/assets/screens/other/cms/prestashop/install-update-version.png){.thumbnail}

Kliknij `No thanks`{.action}, jeśli chcesz zachować wersję PrestaShop, którą właśnie przesłałeś lub na `Yes please!`{.action}, jeśli chcesz korzystać z najnowszej wersji CMS-a.

#### 2.1 - Przejdź na stronę PrestaShop za pomocą przeglądarki

Wpisz swoją domenę na pasku wyszukiwania przeglądarki internetowej.

Jeśli pliki źródłowe Twojego PrestaShop zostały poprawnie umieszczone w katalogu głównym, wyświetli się strona PrestaShop, na której można wybrać język:

![PrestaShop installation step 2](/pages/assets/screens/other/cms/prestashop/install-select-language.png){.thumbnail}

Wybierz język strony i kliknij na `Next`{.action}.

#### 2.2 - Zatwierdź warunki korzystania z usługi

Zapoznaj się z warunkami korzystania, zaznacz kratkę `I agree to the above terms and conditions`{.action} i kliknij `Next`{.action}.

![PrestaShop installation step 3](/pages/assets/screens/other/cms/prestashop/install-licence-agreement-3.png){.thumbnail}

#### 2.3 - Wpisz dane dotyczące sklepu online

PrestaShop poprosi Cię o zestaw informacji dotyczących Twojego przyszłego sklepu internetowego:

![PrestaShop instalacja step 4](/pages/assets/screens/other/cms/prestashop/install-store-infos-4.png){.thumbnail}

**Informacje o sklepie**

- *Shop name*: Wpisz nazwę sklepu internetowego
- *Main activity*: Wybierz swój sektor spośród propozycji z rozwijanego menu
- *Country*: Wybierz kraj
- *Enable SSL*: Zaznacz **Yes**, aby zmienić adres URL na "https://". Musisz posiadać aktywny certyfikat SSL na Twoim hostingu lub domenie. Aby uzyskać więcej informacji na ten temat, zapoznaj się z naszym przewodnikiem dotyczącym [zarządzania certyfikatem SSL na Twoim hostingu OVHcloud](/pages/web_cloud/web_hosting/ssl_on_webhosting).

**Twoje konto**

- *First name*: Wpisz swoje imię
- *Last name*: Wpisz swoje nazwisko
- *E-mail address*: Wpisz swój adres e-mail
- *Shop password*: Wybierz hasło do panelu administracyjnego sklepu online (backoffice)
- *Re-type to confirm*: Wpisz ponownie hasło

Sprawdź wprowadzone informacje i kliknij na `Next`{.action}.

#### 2.4 - Zainstaluj domyślną zawartość Twojego sklepu

PrestaShop proponuje zainstalowanie treści i modułów dla przyszłej strony e-commerce:

![PrestaShop instalacja step 5](/pages/assets/screens/other/cms/prestashop/install-store-content-5.png){.thumbnail}

Dokonaj wyboru i kliknij na `Next`{.action}.

#### 2.5 - Powiązanie PrestaShop z bazą danych OVHcloud

![PrestaShop instalacja step 6](/pages/assets/screens/other/cms/prestashop/install-db-config-6.png){.thumbnail}

Przygotuj dane dostępowe do bazy danych (w razie potrzeby sprawdź **etap 1.4** w przewodniku dotyczącym [ręczna instalacja CMS](/pages/web_cloud/web_hosting/cms_manual_installation).

Wpisz wymagane informacje dotyczące bazy danych:

- *Database server address*: wprowadź nazwę serwera Twojej bazy danych, zawartą w e-mailu instalacyjnym lub w Panelu klienta. 

> [!primary]
> 
> - Nazwa serwera bazy danych zawartej w ofercie hostingu WWW ma zazwyczaj taką formę: `NameOfYourDatabase.mysql.db`. 
>
> - Nazwa serwera bazy danych Cloud Databases zaczyna się od Twojego identyfikatora klienta OVHcloud i ma następującą formę: `aa00000-XXX.eu.clouddb.ovh.net`, **"aa00000"** odnosi się do twojego identyfikatora OVHcloud bez **"-ovh"**, a **"X"** należy zastąpić pozostałą częścią odniesienia do usługi Web Cloud Databases.
>

- *Database name*: nazwa ta została zdefiniowana podczas tworzenia bazy danych w [Panelu klienta OVHcloud](/links/manager).

- *Database login*: nazwa bazy danych jest identyczna, jeśli korzystasz z bazy danych zawartej w Twoim hostingu.
W przypadku baz danych utworzonych w ramach usługi WWW Cloud Databases, zapoznaj się z informacjami podanymi w przewodniku ["Ręczna instalacja CMS"](/pages/web_cloud/web_hosting/cms_manual_installation) w punkcie **etap 1.4**) .

- *Database password*: zdefiniowałeś ją podczas tworzenia bazy danych. Możliwe, że zmieniłeś ją w międzyczasie.

- *Tables prefix*: jeśli instalacja jest wykonywana z nową bazą danych, wprowadź odpowiedni prefiks. Jeśli korzystasz z bazy danych wykorzystywanej już przez inną stronę WWW, zapoznaj się z **krokiem 1.4** w naszym przewodniku dotyczącym [ręczna instalacja CMS](/pages/web_cloud/web_hosting/cms_manual_installation), aby nie wprowadzić prefiksu tabeli już używanego w Twojej bazie danych.

- *Drop existing tables*: **Usuń zaznaczenie, jeśli korzystasz już z bazy danych na innej stronie WWW**.

> [!alert]

>
> Jeśli zaznaczysz kratkę **Drop existing tables**, usunie to wszystkie tabele już istniejące w Twojej bazie danych.
>

Kliknij polecenie `Test your database connection now!`{.action} w celu sprawdzenia wprowadzonych parametrów:

![PrestaShop instalacja step 6-1](/pages/assets/screens/other/cms/prestashop/install-db-config-6-1.png){.thumbnail}

Jeśli pojawi się komunikat "Twoja baza danych", kliknij przycisk `Next`{.action}. W przeciwnym razie sprawdź ustawienia, które wprowadziłeś, aż połączenie zacznie działać. W razie potrzeby sprawdź **etap 1.4** tutoriala w sprawie [ręczna instalacja CMS](/pages/web_cloud/web_hosting/cms_manual_installation).

#### 2.6 - Zakończ instalację PrestaShop

Ostatni etap to podsumowanie instalacji, którą właśnie przeprowadziłeś:

![PrestaShop instalacja step 7](/pages/assets/screens/other/cms/prestashop/install-resume-7.png){.thumbnail}

Pobierz dane do logowania modułu PrestaShop przed opuszczeniem strony.

> [!warning]

>
> **Ze względów bezpieczeństwa zalecamy usunięcie folderu instalacyjnego z przestrzeni FTP.**
>
> Aby wykonać tę operację, zapoznaj się z naszym przewodnikiem ["Jak zalogować się do przestrzeni dyskowej FTP hostingu OVHcloud"](/pages/web_cloud/web_hosting/ftp_connection) i naciśnij [forum PrestaShop](https://www.prestashop.com/forums/){.external}, aby upewnić się, że usuniesz odpowiednie pliki.
>

> [!success]
>
> Możesz teraz rozpocząć tworzenie zawartości strony PrestaShop!
>
  
## Sprawdź również <a name="go-further"></a>

[Oficjalna strona PrestaShop](https://prestashop.com)
 
W przypadku wyspecjalizowanych usług (pozycjonowanie, rozwój, etc.) skontaktuj się z [partnerami OVHcloud](/links/partner).
 
Jeśli chcesz otrzymywać wsparcie w zakresie konfiguracji i użytkowania Twoich rozwiązań OVHcloud, zapoznaj się z naszymi [ofertami pomocy](/links/support).
 
Dołącz do [grona naszych użytkowników](/links/community).