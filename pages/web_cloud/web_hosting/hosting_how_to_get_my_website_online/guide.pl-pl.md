---
title: "Uruchomienie strony WWW na hostingu"
description: "Dowiedz się, jak uruchomić stronę WWW na Twoim hostingu OVHcloud"
updated: 2024-03-21
---

## Wprowadzenie 

W sieci istnieje bardzo wiele rodzajów stron WWW. 

Możesz uruchomić Twoją stronę WWW (bloga, sklep internetowy czy stronę prezentującą Twoją działalność) na **hostingu OVHcloud**, o ile jest ona kompatybilna z [konfiguracją infrastruktury OVHcloud](https://webhosting-infos.hosting.ovh.net){.external}.

**Dowiedz się, jak zainstalować stronę WWW na Twoim hostingu OVHcloud.**

## Wymagania początkowe

- Posiadanie [hostingu OVHcloud](/links/web/hosting){.external}
- Otrzymanie wiadomości e-mail z potwierdzeniem, że Twój hosting został zainstalowany
- Posiadanie [domeny](/links/web/domains){.external}, pod którą będzie Twoja strona WWW
- Dostęp do [Panelu klienta OVHcloud](/links/manager){.external}
- Aktualizacja w [płatności](/pages/account_and_service_management/managing_billing_payments_and_services/invoice_management#pay-bills) i [odnowienie](/pages/account_and_service_management/managing_billing_payments_and_services/how_to_use_automatic_renewal#renewal-management) powiązanych usług (domena i hosting).

## W praktyce

### Etap 1: określenie ram projektu

Jasno określony cel jest kluczowy dla realizacji Twojego projektu. Do czego zamierzasz wykorzystać Twoją stronę WWW? Jak ją uruchomić online? Hosting OVHcloud daje Ci kilka możliwości.

- **Użycie gotowego modułu OVHcloud**: w tej opcji wybierasz gotowe do użycia rozwiązanie, które dowolnie personalizujesz pod względem struktury strony (szablon, teksty itd.). OVHcloud oferuje cztery kompatybilne z naszą infrastrukturą moduły za 1 kliknięciem, które można znaleźć na stronie internetowej OVHcloud ["Tworzenie strony internetowej z modułami za 1 kliknięciem"](/links/web/hosting-website){.external}. Możesz również zapoznać się z przewodnikiem ["Instalacja strony WWW za pomocą modułów 1 kliknięcia"](/pages/web_cloud/web_hosting/cms_install_1_click_modules).

- **Ręczna instalacja gotowego systemu CMS**: w tej opcji wybierasz gotowe do użycia rozwiązanie, które dowolnie personalizujesz pod względem struktury strony (szablon, teksty itd.) i samodzielnie instalujesz na Twoim hostingu OVHcloud.

- **Samodzielna budowa strony WWW**: ta opcja wymaga kompetencji w zakresie programowania, ale daje możliwość stworzenia projektu na miarę.

- **Przeniesienie istniejącej strony WWW do OVHcloud**: operacja ta może mieć krytyczne znaczenie, jeśli niewskazana jest przerwa w dostępie do strony WWW.  W przypadku wyboru tej opcji zachęcamy do zapoznania się z przewodnikiem: [Przeniesienie strony WWW i kont e-mail do OVHcloud](/pages/web_cloud/web_hosting/hosting_migrating_to_ovh)

Po przeanalizowaniu powyższych opcji, masz dwie możliwości:

- **chcesz użyć gotowego modułu OVHcloud**: zapoznaj się z instrukcjami w przewodniku [Automatyczna instalacja strony WWW za pomocą modułu CMS](/pages/web_cloud/web_hosting/cms_install_1_click_modules);

- **nie chcesz użyć gotowego modułu OVHcloud**: przeprowadź ręczną instalację Twojej strony WWW na hostingu OVHcloud. Informacje zawarte w przewodniku pomogą Ci w przeprowadzeniu operacji, nie zastąpią jednak wsparcia wyspecjalizowanego webmastera.
 
> [!warning]
>
> OVHcloud świadczy usługi, za których konfigurację i  zarządzanie odpowiada użytkownik. W związku z tym na Tobie spoczywa odpowiedzialność za zapewnienie prawidłowego funkcjonowania stron i aplikacji WWW.
> 
> W tym przewodniku znajdziesz pomoc w zakresie podstawowych zadań związanych z uruchomieniem strony WWW. Zalecamy jednak skorzystanie z usług wyspecjalizowanego webmastera i/lub skontaktowanie się z nim w przypadku jakichkolwiek trudności. OVHcloud nie będzie w stanie w tym zakresie zapewnić dodatkowego wsparcia. Więcej informacji znajduje się w sekcji „Sprawdź również”.

>

### Etap 2: wgranie plików strony WWW na przestrzeń dyskową

Ręczna instalacja strony WWW na hostingu wymaga przeprowadzenia kilku operacji. Niektóre z nich mogą być opcjonalne w zależności od strony WWW, którą instalujesz. Możliwe są też różne sposoby przeprowadzenia operacji. W przypadku większości aktualnych projektów rozróżniamy dwa główne etapy uruchamiania strony WWW na hostingu. Pierwszy z nich to wgranie plików strony WWW na przestrzeń dyskową.

Proces uruchomienia strony dzieli się na kilka etapów.

#### 1. Pobranie plików strony WWW

Upewnij się, czy posiadasz pliki, które chcesz umieścić online.  Jeśli przenosisz istniejącą stronę WWW do OVHcloud, pobierz pliki od poprzedniego dostawcy hostingu.

#### 2. Zaloguj się do przestrzeni dyskowej

Aby zalogować się do przestrzeni dyskowej, powinieneś posiadać następujące elementy:

- aktywne konto FTP lub SSH;
- hasło powiązane z kontem FTP lub SSH;
- adres serwera;
- port połączenia z serwerem.

Dane te otrzymasz w wiadomości e-mail potwierdzającej instalację hostingu. Jeśli nie posiadasz wskazanych wyżej informacji, zaloguj się do [Panelu klienta](/links/manager){.external} i kliknij `Hosting`{.action}. Wybierz odpowiedni hosting i przejdź do zakładki `FTP - SSH`{.action}. 

![instalacja strony www](/pages/assets/screens/control_panel/product-selection/web-cloud/web-hosting/ftp-ssh/tab-pro.png){.thumbnail}

Wyświetlą się wówczas dane dotyczące Twojej przestrzeni dyskowej. Dzięki nim będziesz mógł odnaleźć dane potrzebne do zalogowania się do przestrzeni dyskowej. Jeśli potrzebujesz więcej informacji, zapoznaj się z przewodnikiem: [Logowanie do przestrzeni dyskowej hostingu](/pages/web_cloud/web_hosting/ftp_connection). Jeśli nie posiadasz hasła, zapoznaj się z instrukcjami zawartymi w przewodniku [Zmiana hasła do konta FTP](/pages/web_cloud/web_hosting/ftp_change_password).

Gdy będziesz posiadał już wszystkie potrzebne informacje, możesz uzyskać dostęp do przestrzeni dyskowej trzema różnymi metodami:

- **FTP Explorer**: umożliwia dostęp do przestrzeni dyskowej przy użyciu przeglądarki internetowej. Aby skorzystać z tej opcji, pozostań w zakładce`FTP - SSH`{.action} i kliknij przycisk `FTP Explorer`{.action};

- **program kompatybilny z protokołem FTP lub SFTP**: zainstaluj na Twoim komputerze odpowiedni program, np. FileZilla. Jeśli chcesz uzyskać pomoc w zakresie korzystania z tego programu, skontaktuj się z jego producentem.

- **dostęp przez SSH**: wpisz odpowiednie komendy w terminalu, aby połączyć się z przestrzenią dyskową.  W przypadku tego dostępu konieczne są bardziej zaawansowane umiejętności techniczne oraz posiadanie [hostingu OVHcloud](/links/web/hosting){.external} z dostępem SSH.

#### 3. Zapisanie plików na przestrzeni dyskowej

Po zalogowaniu się do przestrzeni dyskowej, wgraj pliki strony WWW na Twój hosting. **Zalecamy szczególną ostrożność przy wyborze katalogu, w którym zapiszesz pliki.** W przypadku instalacji tylko jednej strony WWW na hostingu, pliki powinny znaleźć się w katalogu „www”. Jeśli jednak zainstalowałeś na Twoim hostingu kilka stron WWW, z pewnością skonfigurowałeś kilka różnych katalogów dla domen w opcji **MultiSite**.

Aby sprawdzić, w którym katalogu powinna zostać opublikowana strona WWW, przejdź do zakładki `MultiSite`{.action} w Panelu klienta. W tabeli, która się wyświetla dla wybranej domeny znajdź `Katalog główny`{.action}. Następnie opublikuj w nim pliki strony WWW.

Istnieje możliwość, że na Twojej przestrzeni dyskowej znajdziesz plik zatytułowany „index.html”. Plik ten mógł zostać utworzony przez OVHcloud podczas instalacji hostingu, aby wyświetlić domyślną stronę na Twojej stronie WWW. W takim przypadku pamiętaj, aby go usunąć podczas uruchomienia Twojej strony.

> [!primary]
>
> Plik "index.php" zawsze przejdzie przez plik "index.html". W związku z tym, gdy oba są obecne, wywoływany jest tylko "index.php".

![instalacja strony www](/pages/assets/screens/control_panel/product-selection/web-cloud/web-hosting/multisite/root-folders.png){.thumbnail}

### Etap 3: 

> [!primary]
>
> Ta część jest opcjonalna, jeśli Twoja strona internetowa nie musi być połączona z bazą danych.
>

Obecnie niemal wszystkie systemy zarządzania treścią (WordPress, Joomla!, etc.) wykorzystują bazę danych do przechowywania elementów dynamicznych, takich jak komentarze czy artykuły. Połączenie plików strony WWW z bazą danych jest zatem niezbędne, aby strona poprawnie działała. Umożliwia to plik konfiguracyjny zawierający informacje dotyczące połączenia z bazą danych. 

W zależności od typu używanej strony WWW połączenie to musi zostać przeprowadzone ręcznie lub przez interfejs wygenerowany przez CMS. Połączenie realizowane jest w kilku etapach. Niektóre z nich mogą być opcjonalne.

#### 1. Pobranie istniejącej bazy danych 

Jeśli przenosisz istniejącą stronę WWW do OVHcloud, pobierz bazę danych od poprzedniego dostawcy hostingu. W przypadku nowej strony, przejdź do kolejnego etapu.

#### 2. Utworzenie bazy danych w OVHcloud 

Jeśli dysponujesz już bazą danych (zawartą w ofercie [hostingu OVHcloud](/links/web/hosting){.external},[Web Cloud Databases](https://www.ovh.pl/cloud-databases/){.external}), przygotuj nazwę użytkownika i hasło, nazwę bazy oraz adres serwera. Następnie przejdź do kolejnego etapu.

Jeśli chcesz utworzyć nową bazę danych w OVHcloud, zaloguj się do [Panelu klienta](/links/manager){.external} i kliknij `Hosting`{.action}. Zaznacz nazwę odpowiedniego hostingu i przejdź do zakładki `Baza danych`{.action}.

Następnie kliknij przycisk `Utwórz bazę danych`{.action} lub, jeśli przycisk się nie wyświetla, kliknij przycisk `Operacje`{.action}, po czym przycisk `Utwórz bazę danych`{.action}. Teraz postępuj zgodnie z kolejnymi instrukcjami, które się wyświetlą.

![instalacja strony www](/pages/assets/screens/control_panel/product-selection/web-cloud/web-hosting/databases/tab.png){.thumbnail}

#### 3. Import istniejącej bazy danych

Jeśli przenosisz stronę WWW do OVHcloud, zaimportuj istniejącą bazę danych do nowo utworzonej bazy. W przypadku nowej strony, przejdź do kolejnego etapu.

Istnieje kilka metod importu. OVHcloud oferuje jedną z nich w Panelu klienta. Po kliknięciu na listę baz danych utworzonych w Twojej usłudze w Panelu klienta OVHcloud kliknij przycisk `...`{.action} znajdujący się po prawej stronie bazy danych, a następnie kliknij `Importuj plik`{.action}.

#### 4. Połączenie strony WWW z bazą danych

Kiedy baza danych jest już dostępna, a pliki zapisane na Twojej przestrzeni dyskowej możesz połączyć stronę z bazą. Przygotuj informacje potrzebne do zalogowania się do bazy danych: nazwa użytkownika, hasło, nazwa bazy danych oraz adres serwera. 

Sposób połączenia strony z bazą zależy od typu strony (np. rodzaju CMS’a), którą chcesz uruchomić. Operacja ta wymaga konfiguracji Twojej strony WWW, a nie samego rozwiązania OVHcloud. Zalecamy zatem skontaktowanie się z administratorem strony lub wyspecjalizowanym w tym zakresie webmasterem.

### Etap 4: dostęp do Twojej strony WWW

Po zapisaniu plików na przestrzeni dyskowej i połączeniu z nią bazy danych (jeśli Twoja strona WWW używa bazy) możesz otworzyć Twoją stronę w przeglądarce.  Powinna wyświetlić się poprawnie. 

Jeśli nie wyświetla się, zalecamy następujące kroki:

- **sprawdź konfigurację domeny**: możliwe, że konfiguracja DNS domeny nie pozwala poprawnie wyświetlać strony, którą właśnie zainstalowałeś na Twoim hostingu.  Upewnij się, że rekord A skonfigurowany aktualnie w strefie DNS Twojej domeny odpowiada adresowi IP Twojego hostingu;

- **upewnij się, że nie brakuje żadnego pliku**: możliwe, że podczas zapisywania plików na Twoim hostingu OVHcloud pominąłeś jakieś pliki lub wystąpił błąd. Zalecamy ostrożność podczas wykonywania operacji, aby nie nastąpiło zerwanie połączenia pomiędzy stroną WWW a bazą danych (jeśli strona używa bazy).

- **sprawdź, czy kod strony nie zawiera błędu**: istnieje możliwość, że pobrane pliki zawierają błędy i nie pozwalają serwerowi wyświetlać poprawnie części lub całej zawartości Twojej strony.

Przypominamy, że w przypadku trudności podczas uruchamiania Twojej strony na hostingu możesz skontaktować się z wyspecjalizowanym webmasterem lub administratorem usługi (np. zainstalowanego CMS).

## Sprawdź również

[Przeniesienie strony WWW i kont e-mail do OVHcloud](/pages/web_cloud/web_hosting/hosting_migrating_to_ovh)

[Automatyczna instalacja strony WWW za pomocą modułu CMS](/pages/web_cloud/web_hosting/cms_install_1_click_modules)

[Logowanie do przestrzeni dyskowej hostingu](/pages/web_cloud/web_hosting/ftp_connection)

[Zmiana hasła do konta FTP](/pages/web_cloud/web_hosting/ftp_change_password)

W przypadku wyspecjalizowanych usług (pozycjonowanie, rozwój, etc.) skontaktuj się z [partnerami OVHcloud](/links/partner).

Jeśli chcesz otrzymywać wsparcie w zakresie konfiguracji i użytkowania Twoich rozwiązań OVHcloud, zapoznaj się z naszymi [ofertami pomocy](/links/support).

Dołącz do [grona naszych użytkowników](/links/community).