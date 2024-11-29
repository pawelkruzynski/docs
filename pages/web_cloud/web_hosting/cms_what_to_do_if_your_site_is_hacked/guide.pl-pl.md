---
title: "Przykłady zastosowania - Porady po włamaniu się na stronę WWW"
excerpt: "Dowiedz się, jak naprawić stronę WWW"
updated: 2022-11-15
---
  
## Wprowadzenie

Tutorial ten ma na celu pomoc w przypadku stwierdzenia włamania na Twoją stronę WWW. Poniżej znajdziesz **4 etapy, które należy przeprowadzić w kolejności**, aby zmienić tę sytuację.

Piractwo może pojawić się na kilka sposobów (niewyczerpująca lista):

- Twoja strona WWW nie wyświetla się poprawnie lub w ogóle nie pojawia się bez żadnej zmiany (FTP, SQL lub DNS);
- Twoja strona WWW zostanie przekierowana na inną stronę;
- Twoja strona WWW generuje niechciane "reklamy" (Pop-ups, okna błędów, itp.);
- baza danych na Twojej stronie WWW jest nagle wypełniona;
- otrzymasz ze swojego hostingu wiadomości SPAM generowane przez zainfekowane skrypty.

**Odkryj nasze porady dotyczące naprawy zhakowanej strony WWW.**

> [!warning]
>
> OVHcloud oddaje do Twojej dyspozycji usługi, których konfiguracja, zarządzanie i odpowiedzialność spoczywa na Ciebie. W związku z tym należy zapewnić ich prawidłowe funkcjonowanie.
> 
> Oddajemy do Twojej dyspozycji niniejszy tutorial, którego celem jest pomoc w jak najlepszym wykonywaniu bieżących zadań. W przypadku trudności zalecamy skorzystanie z pomocy [wyspecjalizowanego usługodawcy](/links/partner). Niestety firma OVHcloud nie będzie mogła udzielić wsparcia w tym zakresie. Więcej informacji znajduje się w sekcji ["Sprawdź również"](#go-further) niniejszego przewodnika.
>

## Wymagania początkowe

- Posiadanie [hostingu WWW Cloud](/links/web/hosting) na Twojej stronie WWW z hostingiem
- Dostęp do [Panelu klienta OVHcloud](/links/manager)

## W praktyce

Piractwo strony internetowej jest systematycznie związane z **co najmniej** jednym z poniższych punktów:

- brak aktualizacji strony internetowej;
- program szpiegowski na jednym z urządzeń, których używasz do zarządzania Twoją stroną WWW;
- korzystanie z wtyczki lub tematu "nieoficjalny", zwłaszcza jeśli korzystasz z systemu zarządzania treścią (CMS), takiego jak WordPress, Joomla!, PrestaShop lub Drupal;
- hasła (FTP, SQL, back-office) dla systemów CMS, itp.) zbyt krótkie lub zbyt łatwe do znalezienia, tym bardziej, jeśli nie zostały one nigdy zmienione;
- skrypt Twojej strony, który celowo otwiera porty na poziomie Twojego hostingu WWW **bez** sprawdź, co otrzymane przez te porty;
- nieco zbyt liberalne prawa dostępu do FTP "CHMOD".

**Włamanie do strony WWW nie wynika z braku bezpieczeństwa hostingu.** Tylko skrypty/pliki, które hostuje, mogą wydawać polecenia na hostingu. Mogą oni zażądać od niego otwarcia niektórych portów dostępu, które są domyślnie zamknięte lub wykonania niektórych operacji.<br>
Skrypty zarządzać, hosting uruchomić.

### Etap 1 - skanowanie wszystkich urządzeń

Przeprowadź analizę anty-wirusową i anty-spywares wszystkich urządzeń (PC, Mac, smartfon/Iphone, tablet,...), z których możesz zarządzać swoją stroną www.

> [!warning]
>
> Jeśli używasz urządzeń działających w systemie *Linux*, *Mac OS* lub innych systemów operacyjnych, w przypadku których powszechnie stwierdza się, że nie istnieje ryzyko występowania wirusa lub oprogramowania "szpiegowskiego", **przeprowadź taką analizę**.
>
> **Żaden system operacyjny nie jest odporny na złośliwe oprogramowanie/wirusy.**
>

> [!success]
>
> Zalecamy używanie kilku antywirusowych/anty-spywares (darmowych lub płatnych) dla każdego urządzenia.
> Faktycznie, niektóre wirusy lub spywares mogą utrzymywać się w zależności od używanego oprogramowania antywirusowego.
> Istnieją wersje antywirusowe/anty-spywares, które można zainstalować "lokalnie" na urządzeniu lub używać bezpośrednio "online" w Internecie.
>

Jeśli wirus lub oprogramowanie szpiegowskie zostanie wykryte, usuń go za pomocą oprogramowania antywirusowego/antyspywares **przed**, aby przejść do następnego etapu.

### Etap 2 - zmiana hasła <a name="step2"></a>

Jeśli strona WWW została zhakowana i przez środki ostrożności, zmień wszystkie hasła związane z tą stroną.

W przypadku OVHcloud skorzystaj z naszej dokumentacji dotyczącej:

- [Zmiana hasła do konta klienta OVHcloud](/pages/account_and_service_management/account_information/manage-ovh-password).
- [Zabezpieczenie dostępu do Panelu klienta OVHcloud za pomocą weryfikacji dwuetapowej](/pages/account_and_service_management/account_information/secure-ovhcloud-account-with-2fa).
- [Zmień hasło dostępowe do przestrzeni dyskowej FTP Twojego hostingu](/pages/web_cloud/web_hosting/ftp_change_password).
- [Zmiana hasła do bazy danych](/pages/web_cloud/web_hosting/sql_change_password).

Zalecamy również użycie [menedżera haseł](/pages/account_and_service_management/account_information/manage-ovh-password#uzycie-managera-hasel).

> [!warning]
> 
> Zmieniając hasło do bazy danych, pamiętaj o aktualizacji również hasła w pliku konfiguracyjnym Twojej strony WWW. W przeciwnym razie połączenie między bazą danych a plikami znajdującymi się na przestrzeni FTP Twojego hostingu WWW zostanie przerwane, a Twoja strona wyświetla "błąd podczas logowania do bazy danych".
>

> [!primary]
>
> Jeśli korzystasz z systemu CMS, takiego jak WordPress, Joomla!, PrestaShop lub Drupal, skorzystaj z oficjalnej dokumentacji swojego systemu CMS, aby zmienić hasło dostępowe do panelu zarządzania CMS ("Back-office").
>

### Etap 3 - wyszukaj złośliwe pliki i luki w zabezpieczeniach

> [!warning]
>
> W przypadku trudności z wykonaniem opisanych poniżej operacji, należy skontaktować się z [wyspecjalizowanym dostawcą](/links/partner) w zakresie bezpieczeństwa cybernetycznego.
>

Skorzystaj z naszego przewodnika na temat [statystyki i logi Twojego hostingu www](/pages/web_cloud/web_hosting/logs_and_statistics), aby wyszukać złośliwe elementy wprowadzone na Twoją stronę WWW. Informacje znajdziesz w logach "www". 

Rozpocznij poszukiwania od dnia, w którym widziałeś hacking, a następnie przejdź do historii Twoich logów.

Wyszukaj zapytania "POST", które pochodzą ze zwykłego katalogu. Złośliwe pliki mają zwykle nazwy alfanumeryczne bez żadnego znaczenia (**przykłady**: az78e4jFn.txt, oij8bh4.html, udh73hd45.php, mlkjc23d.js, ...)

Znajdź adres IP, który wykonał złośliwe zapytanie. Następnie wyszukaj ten adres w Twoich logach, aby sprawdzić wszystkie operacje wymagane przez ten adres IP na Twojej stronie.

> [!primary]
>
> Zazwyczaj kilka złośliwych adresów IP w tym samym czasie wywołuje złośliwe skrypty obecne po włamaniu.
> Przeanalizuj wszystkie logi Twojego hostingu.
>

W ten sposób usuń luki bezpieczeństwa występujące na Twojej stronie WWW, a jednocześnie zaznacz szkodliwe pliki.

> [!success]
>
> Kilka stron WWW (nie obsługiwanych przez OVHcloud) pozwala na uzyskanie informacji o złośliwych adresach IP. Możesz użyć jednego z nich do pobierania informacji, takich jak dostawca IP, jego geolokalizacja, menedżer, itp...
>
> Jeśli jesteś absolutnie pewien, że chodzi o złośliwy adres IP, możesz zablokować dostęp do Twojego hostingu zgodnie z naszą dokumentacją dotyczącą [ograniczenia dostępu przez plik ".htaccess"](/pages/web_cloud/web_hosting/htaccess_how_to_block_a_specific_ip_address_from_accessing_your_website).
> 

### Etap 4 - Usunięcie złośliwych elementów i usunięcie luk w zabezpieczeniach

W tym etapie możliwe są trzy przypadki: 

> [!alert]
>
> **Ważne**: W każdym przypadku, jeśli usuniesz złośliwe kody bez usunięcia luk bezpieczeństwa, haker może ponownie wykorzystać je, aby umieścić złośliwy kod na Twoim hostingu. Miałby nawet szansę stworzyć nowe drzwi.
>
> Przywrócenie przed piractwem będzie wymagało aktualizacji **natychmiastowej** oraz przeprowadzenia koniecznego **audytu bezpieczeństwa** w celu zidentyfikowania wszystkich luk bezpieczeństwa.
>

#### Przypadki nr 1 - OVHcloud posiada kopię zapasową Twojej strony WWW (przestrzeń dyskowa FTP i baza danych)

W zależności od daty włamania na Twojej stronie (mniej niż 14 dni), OVHcloud może dostarczyć Ci kopię zapasową (niezawartą w umowie).

W tym celu zapoznaj się z naszymi 3 przewodnikami:

- [Przywracanie przestrzeni dyskowej FTP z Twojego hostingu www](/pages/web_cloud/web_hosting/ftp_save_and_backup)
- [Pobranie kopii zapasowej SQL bazy danych](/pages/web_cloud/web_hosting/sql_database_export)
- [Import kopii zapasowej SQL do bazy danych](/pages/web_cloud/web_hosting/sql_importing_mysql_database)

Wybierz maksymalnie dwie daty przywrócenia przestrzeni dyskowej FTP i bazy danych SQL.

>[!warning]
>
> OVHcloud dysponuje robotami bezpieczeństwa, które mogą wykrywać złośliwe operacje wykonywane z poziomu Twojego hostingu. Strony dezaktywują Twój hosting i powiadamiają e-mail, że Twój hosting został wyłączony.
> Jako uzupełnienie tego e-maila, zazwyczaj pojawia się strona "403 Forbidden", gdy próbujesz wejść na Twoją stronę.
>
> Jeśli Twój hosting jest wyłączony, roboty przywracania automatycznego dostępne w [Panelu klienta OVHcloud](/links/manager) zostaną również wyłączone.
> Musisz wykonać ręczne przywracanie strony, usunąć pozostałości złośliwych elementów, a następnie usunąć luki bezpieczeństwa występujące w kopii zapasowej. To **przed** włączyć hosting.
>
> Aby ponownie włączyć hosting WWW, postępuj zgodnie z instrukcjami etapu 4 tego [przewodnika](/pages/web_cloud/web_hosting/diagnostic_403_forbidden).
>

Twoja strona WWW powinna pojawić się ponownie, jeśli operacje te zostały wykonane prawidłowo.

#### Przypadki nr 2 - dysponujesz Twoją własną kopią zapasową przed włamaniem

W tym celu zapoznaj się z naszymi 2 przewodnikami:

- [Przywracanie przestrzeni dyskowej FTP z Twojego hostingu www](/pages/web_cloud/web_hosting/ftp_save_and_backup)
- [Import kopii zapasowej SQL do bazy danych](/pages/web_cloud/web_hosting/sql_importing_mysql_database)

>[!warning]
>
> OVHcloud dysponuje robotami bezpieczeństwa, które mogą wykrywać złośliwe operacje wykonywane z poziomu Twojego hostingu. Strony dezaktywują Twój hosting i powiadamiają e-mail, że Twój hosting został wyłączony.
> Jako uzupełnienie tego e-maila, zazwyczaj pojawia się strona "403 Forbidden", gdy próbujesz wejść na Twoją stronę.
>
> Jeśli Twój hosting jest "wyłączony", przywracaj stronę ręcznie, usuń resztki złośliwych elementów, a następnie usuń luki bezpieczeństwa występujące w kopii zapasowej. To **przed** włączyć hosting.
>
> Aby ponownie włączyć hosting WWW, postępuj zgodnie z instrukcjami etapu 4 tego [przewodnika](/pages/web_cloud/web_hosting/diagnostic_403_forbidden).
>

Twoja strona WWW powinna pojawić się ponownie, jeśli operacje te zostały wykonane prawidłowo.

### Przypadki nr 3 - żadna kopia zapasowa nie jest dostępna dla Twojej strony WWW

Musisz ręcznie usunąć wykryte wcześniej pliki i złośliwe kody w [Etap 2](#step2) z tego przewodnika, a następnie usunąć luki bezpieczeństwa na Twojej stronie.

Aby zalogować się do przestrzeni dyskowej Twojego hostingu, zapoznaj się z [naszym przewodnikiem](/pages/web_cloud/web_hosting/ftp_connection).

> [!warning]
>
> OVHcloud dysponuje robotami bezpieczeństwa, które mogą wykrywać złośliwe operacje wykonywane z poziomu Twojego hostingu. Strony dezaktywują Twój hosting i powiadamiają e-mail, że Twój hosting został wyłączony.
> Jako uzupełnienie tego e-maila, zazwyczaj pojawia się strona "403 Forbidden", gdy próbujesz wejść na Twoją stronę.
>
> Jeśli Twój hosting jest "wyłączony", usuń pozostałości złośliwych elementów, a następnie usuń luki bezpieczeństwa w kopii zapasowej **przed**, aby ponownie włączyć hosting.
>
> Aby ponownie włączyć hosting WWW, postępuj zgodnie z instrukcjami etapu 4 tego [przewodnika](/pages/web_cloud/web_hosting/diagnostic_403_forbidden).
>

Twoja strona WWW powinna pojawić się ponownie, jeśli operacje te zostały wykonane prawidłowo.

### Etap 5 - Aktualizacja strony

Zaktualizuj Twoją stronę WWW, używaj jej kodu źródłowego, dostępnych parametrów zabezpieczeń, dostępnych wersji językowych (w tym PHP).

Sprawdź uprawnienia dostępu FTP "CHMOD" dla każdego z Twoich katalogów i plików przechowywanych w Twojej przestrzeni dyskowej.
Domyślnie zalecamy maksymalne wykorzystanie uprawnień "CHMOD" **705** w przypadku katalogów i **604** w przypadku plików.
Więcej informacji na temat uprawnień "CHMOD" znajduje się w sekcji "Przydatne informacje" w naszym [tutorial dotyczący korzystania z klienta FTP Filezilla](/pages/web_cloud/web_hosting/ftp_filezilla_user_guide#useful-information).

Jeśli korzystasz z CMS (Wordpress, Joomla!, PrestaShop, Drupal,...), aktualizuj wtyczki, temat i sam CMS.
Uruchom wtyczki/tematy "oficjalne" i aktualizuj stronę internetową tak regularnie, jak to możliwe i wyczerpująco.

Zabezpiecz swoje formularze kontaktowe za pomocą systemu Captcha, aby zapobiec wysyłaniu przez złośliwe roboty SPAM. Jeśli funkcja "mail()" PHP została również zablokowana na Twoim hostingu, w celu rozwiązania tej blokady, zapoznaj się z [naszym przewodnikiem](/pages/web_cloud/web_hosting/mail_function_script_records).

Zapoznaj się również z naszym przewodnikiem dotyczącym [jak zabezpieczyć Twoją stronę internetową](/pages/web_cloud/web_hosting/secure_your_website), aby zminimalizować ryzyko ponownego włamania.

## Sprawdź również <a name="go-further"></a>

[Logowanie do przestrzeni dyskowej hostingu WWW](/pages/web_cloud/web_hosting/ftp_connection)

[Zmiana konfiguracji hostingu](/pages/web_cloud/web_hosting/configure_your_web_hosting)

[Włącz firewall aplikacyjny](/pages/web_cloud/web_hosting/multisites_activating_application_firewall)

[Optymalizacja wydajności strony](/pages/web_cloud/web_hosting/optimise_your_website_performance)

W przypadku wyspecjalizowanych usług (pozycjonowanie, rozwój, etc.) skontaktuj się z [partnerami OVHcloud](/links/partner).

Jeśli chcesz otrzymywać wsparcie w zakresie konfiguracji i użytkowania Twoich rozwiązań OVHcloud, zapoznaj się z naszymi [ofertami pomocy](/links/support).

Dołącz do [grona naszych użytkowników](/links/community).