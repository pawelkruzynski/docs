---
title: "Przywracanie plików z kopii zapasowej OVHcloud"
excerpt: "Dowiedz się, jak przywrócić plik lub całą przestrzeń dyskową Twojego hostingu"
updated: 2023-12-04
---

## Wprowadzenie 

W ramach usługi hostingu OVHcloud otrzymujesz dostęp do przestrzeni dyskowej, na której możesz hostować Twoje strony WWW. Może się zdarzyć, że z jakiegoś powodu, na przykład w wyniku usunięcia lub modyfikacji pliku, Twoja strona WWW stanie się niedostępna i będziesz potrzebował przywrócić pojedynczy plik lub wszystkie dane przechowywane na przestrzeni dyskowej.

> [!primary]
> 
> Kopie zapasowe proponowane przez OVHcloud dla hostingu współdzielonego są niezamówione. Oferujemy je jako uzupełnienie Twoich usług, które pomogą Ci w nagłych wypadkach. Zalecamy regularne wykonywanie Twoich własnych kopii zapasowych, aby zapobiec ewentualnej utracie danych.
> 
> Wykonując kopię zapasową bezpieczeństwa Twojej strony WWW i używając bazy danych, wykonaj również kopię zapasową bazy danych. Zapoznaj się z naszym przewodnikiem, aby [tworzenie i pobieranie kopii zapasowej bazy danych na hostingu WWW](/pages/web_cloud/web_hosting/sql_database_export).
> 

**Dowiedz się, jak przywrócić plik lub całą przestrzeń dyskową Twojego hostingu.**

## Wymagania początkowe

- Posiadanie oferty [hostingu](/links/web/hosting){.external} (nie dotyczy hostingu [Cloud Web](/links/web/hosting-cloud-web-offer)).
- W zależności od użytej metody, posiadanie dostępu do interfejsu zarządzania usługą hostingu WWW w [Panelu klienta](/links/manager){.external} lub posiadanie hasła użytkownika FTP umożliwiającego zalogowanie do przestrzeni dyskowej. 

## W praktyce

Zanim przystąpisz do operacji, upewnij się, że wśród dostępnych dat przywrócenia przestrzeni dyskowej hostingu możesz wybrać odpowiadającą Ci datę.

- dzisiaj, o 00:01 rano;
- wczoraj, o 00:01 rano;
- przedwczoraj, o 00:01 rano;
- poprzednia niedziela, o 01:00 rano;
- niedziela dwa tygodnie temu, o 01:00 rano.

Jeśli chcesz wykorzystać starszą kopię zapasową, OVHcloud nie będzie w stanie Ci jej dostarczyć. Ewentualnie wykorzystaj kopię zapasową, którą wykonałeś osobiście w przeszłości.

Określ również metodę przywracania, której użyjesz.

|Metoda przywracania|Opis|
|---|---|
|Przywracanie w Panelu klienta|Pozwala przywrócić całą zawartość przestrzeni dyskowej. Aktualna zawartość przestrzeni dyskowej zostanie zastąpiona wybraną kopią zapasową.|
|Przywracanie plików za pomocą programu lub interfejsu|Pozwala zalogować się do kopii zapasowej przestrzeni dyskowej tylko w trybie odczytu. Jest to metoda wymagająca większych umiejętności technicznych, pozwala jednak przywrócić jeden lub kilka plików z wcześniejszą datą bez konieczności usuwania całej zawartości przestrzeni dyskowej.|

> [!warning]
>
> Metoda **przywracania w Panelu klienta OVHcloud** sprawdź, czy co najmniej **połowa całkowitej przestrzeni dyskowej FTP** w pakiecie hostingowym jest nadal dostępna.
> Na przykład, jeśli dysponujesz usługą hostingu **Performance**, 250 GB musi być nadal dostępne w dostępnych 500 GB.
>
> Nasze roboty instalują na Twoim hostingu kopię zapasową, zanim usuną zawartość FTP, która zostanie zastąpiona przywróceniem danych.
>
> Aby sprawdzić rozmiar używany na Twoim hostingu, zaloguj się do [Panelu klienta OVHcloud](/links/manager). Przejdź do sekcji `Web Cloud`{.action} i kliknij `Hosting`{.action}. Wybierz odpowiedni hosting. 
>
> Wykorzystany limit pojawia się na stronie, która się wyświetla:
>
>![ftp quota](/pages/assets/screens/control_panel/product-selection/web-cloud/web-hosting/general-information/find-disk-space.png){.thumbnail}
>
> Jeśli używana przestrzeń dyskowa FTP jest większa niż połowa całkowitej przestrzeni dyskowej FTP w Twojej ofercie hostingu, możesz lokalnie pobrać duże elementy Twojej strony WWW (w tym celu możesz użyć [Filezilla](/pages/web_cloud/web_hosting/ftp_filezilla_user_guide)). Usuń je z przestrzeni FTP. Zmniejszy to rozmiar przestrzeni dyskowej FTP, której używasz i będziesz mógł przywrócić dane z Panelu klienta OVHcloud.
>

Przejdź do sekcji dotyczącej wybranej przez Ciebie metody przywracania przestrzeni dyskowej. 

- [Przywracanie przestrzeni dyskowej w Panelu klienta](#viacontrolpanel)
- [Przywracanie pliku za pomocą programu lub interfejsu](#viainterface)

### Przywracanie przestrzeni dyskowej w Panelu klienta <a name="viacontrolpanel"></a>

> [!warning]
>
> Ta metoda przywracania kopii zapasowej jest niedostępna, jeśli Twój hosting został umieszczony przez naszych administratorów w trybie "konserwacji" lub jeśli nie posiada on praw dostępu FTP (`chmod`) po wykonaniu jakiejś czynności.
>
> Aby metoda ta działała, uprawnienia `chmod` do katalogu głównego hostingu muszą być obowiązkowo `705`.
>

> [!primary]
> **Strona w trybie konserwacji**
> 
> Aby dowiedzieć się, czy Twoja strona została umieszczona w trybie konserwacji, zapoznaj się z naszym przewodnikiem [Co zrobić w przypadku strony “403 forbidden”?](/pages/web_cloud/web_hosting/diagnostic_403_forbidden). 
> 
> W tym przypadku:
>
> - Do [kontaktu administratora](/pages/account_and_service_management/account_information/managing_contacts#dostep-do-zarzadzania-kontaktami) hostingu wysyłamy e-mail z naszymi zespołami. 
> - Status "konserwacji" pojawia się w Twoim [Panelu klienta OVHcloud](/links/manager){.external}. W sekcji `Web Cloud`{.action} kliknij Twoją usługę w sekcji `Hosting`{.action}, a następnie zakładkę `Informacje ogólne`{.action}.
> - Strona (-y), na której (-ych) hostowane są strony "403 Forbidden".
>

Przed rozpoczęciem operacji zaloguj się do [Panelu klienta](/links/manager){.external}, kliknij `Hosting`{.action} , następnie wybierz nazwę odpowiedniego hostingu. Przejdź do zakładki `FTP - SSH`{.action} i kliknij przycisk `Przywróć kopię zapasową`{.action}.

![kopia zapasowa](/pages/assets/screens/control_panel/product-selection/web-cloud/web-hosting/ftp-ssh/restore-backup.png){.thumbnail}

W oknie, które się wyświetla wybierz z rozwijanego menu odpowiednią dla Ciebie datę:

|Wyświetlane oznaczenie daty|Data wykonania kopii zapasowej|
|---|---|
|D-1|dzisiaj, o 00:01 rano;|
|D-2|wczoraj, o 00:01 rano;|
|D-3|przedwczoraj, o 00:01 rano;|
|1 tydzień temu|poprzednia niedziela, o 01:00 rano;|
|2 tygodnie temu|niedziela dwa tygodnie temu, o 01:00 rano.|

Po wybraniu daty, kliknij przycisk `Dalej`{.action}. 

![kopia zapasowa](/pages/assets/screens/control_panel/product-selection/web-cloud/web-hosting/ftp-ssh/restore-backup-step-1.png){.thumbnail}

Poświęć chwilę, aby upewnić się, że żaden plik nie zostanie usunięty w wyniku przywrócenia przestrzeni dyskowej, np. plik, który zapisałeś na przestrzeni po wybranej dacie przywrócenia. Jak zostało wspomniane wyżej, przywrócenie przestrzeni dyskowej spowoduje usunięcie wszystkich aktualnych danych, które zostaną zastąpione danymi z kopii zapasowej.

Kiedy jesteś gotowy do uruchomienia przywracania kopii zapasowej, kliknij przycisk `Zatwierdź`{.action}.

> [!primary]
>
>Automatyczne przywracanie może trwać od kilku minut do kilku godzin. Jeśli trwa to **więcej niż 24 godziny**, skontaktuj się z [OVHcloud support](/links/support).
>

### Przywracanie pliku za pomocą programu lub interfejsu <a name="viainterface"></a>

Operacja składa się z kilku etapów. Upewnij się, że posiadasz hasło użytkownika FTP umożliwiające dostęp do przestrzeni dyskowej. 

> [!warning]
>
> Rozwiązanie to wymaga znajomości programu lub interfejsu, którego będziesz używał. Poniżej zamieszczamy kilka informacji dotyczących sposobu postępowania. W przypadku trudności zalecamy skorzystanie z pomocy specjalisty lub kontakt z producentem programu lub interfejsu. Niestety firma OVHcloud nie będzie mogła udzielić wsparcia w tym zakresie.
>

#### Etap 1: wybranie programu lub interfejsu, którego będziesz używał

Na wstępie określ program lub interfejs, którego będziesz używał do łączenia się z kopią zapasową Twojej przestrzeni dyskowej. Jeśli już wybrałeś program lub interfejs, przejdź od razu do etapu 2. W przeciwnym razie zalecamy użycie jednego z trzech rozwiązań:

- **program FileZilla**: pobierz program ze strony producenta. OVHcloud udostępnia przewodnik [Korzystanie z programu FileZilla na Twoim hostingu](/pages/web_cloud/web_hosting/ftp_filezilla_user_guide){.external}, w którym znajdziesz instrukcje obsługi programu. Pamiętaj, że przewodnik OVHcloud nie zastępuje oficjalnej dokumentacji producenta programu Filezilla.

- **program Cyberduck**: pobierz program ze strony producenta. OVHcloud udostępnia przewodnik [Korzystanie z programu Cyberduck na Twoim hostingu](/pages/web_cloud/web_hosting/ftp_cyberduck_user_guide_on_mac){.external}, w którym znajdziesz instrukcje obsługi programu. Pamiętaj, że przewodnik OVHcloud nie zastępuje oficjalnej dokumentacji producenta programu Filezilla.

- **interfejs FTP Explorer**: zaloguj się do interfejsu w [Panelu klienta](/links/manager){.external}. Po zalogowaniu, kliknij `Hosting`{.action}, następnie wybierz odpowiedni hosting. Przejdź do zakładki `FTP - SSH`{.action} i kliknij przycisk `FTP Explorer`{.action}.

Kiedy jesteś gotowy do rozpoczęcia operacji, przejdź do następnego etapu.

![kopia zapasowa](/pages/assets/screens/control_panel/product-selection/web-cloud/web-hosting/ftp-ssh/ftp-explorer.png){.thumbnail}

#### Etap 2: logowanie do kopii zapasowej przestrzeni dyskowej

W wybranym interfejsie lub programie zaloguj się do przestrzeni dyskowej, aby uzyskać dostęp do zawartości kopii zapasowej, którą chcesz przywrócić. Potrzebna Ci do tego będzie nazwa użytkownika FTP, hasło oraz nazwa hosta Twojego serwera. 

Możesz odnaleźć te informacje w zakładce `FTP - SSH`{.action} na Twoim hostingu. Jeśli nie posiadasz hasła dla użytkownika FTP, zapoznaj się z instrukcjami zawartymi w przewodniku [Zmiana hasła do konta FTP](/pages/web_cloud/web_hosting/ftp_change_password){.external}.

![kopia zapasowa](/pages/assets/screens/control_panel/product-selection/web-cloud/web-hosting/ftp-ssh/login-infos.png){.thumbnail}

Uzupełnij Twoją nazwę głównego użytkownika („login”) FTP sufiksem wskazującym kopię zapasową, do której chcesz się zalogować. W uzyskaniu dostępu do wybranej kopii zapasowej pomogą Ci poniższe wskazówki:

|Data wykonania kopii zapasowej|Sufiks do dodania:|Przykład uzupełnionej nazwy użytkownika|
|---|---|---|
|dzisiaj, o 00:01 rano;|-snap0|uzytkownikftp**-snap0**|
|wczoraj, o 00:01 rano;|-snap1|uzytkownikftp**-snap1**|
|przedwczoraj, o 00:01 rano;|-snap2|uzytkownikftp**-snap2**|
|poprzednia niedziela, o 01:00 rano;|-snap3|uzytkownikftp**-snap3**|
|niedziela dwa tygodnie temu, o 01:00 rano.|-snap4|uzytkownikftp**-snap4**|

Pamiętaj, aby zastąpić informację ogólną „uzytkownikftp” Twoją nazwą głównego użytkownika FTP. Zachowaj natomiast sufiks określający datę kopii zapasowej, do której chcesz uzyskać dostęp.

Metoda logowania do Twojej przestrzeni dyskowej jest różna w zależności od używanego interfejsu lub programu. Poniżej obrazek przedstawiający logowanie do przestrzeni przez interfejs FTP Explorer. 

![kopia zapasowa](/pages/assets/screens/other/web-tools/net2ftp/login-interface-snap0.png){.thumbnail}

#### Etap 3: pobieranie wybranego pliku lub plików

Po zalogowaniu się, pobierz wybrany plik lub pliki. W tym celu przejrzyj zawartość Twojej przestrzeni dyskowej i zapisz lokalnie pliki. Operacja przebiega różnie w zależności od używanego programu lub interfejsu.

Zanim przejdziesz do kolejnego etapu, upewnij się, że pobrałeś wszystkie pliki, które zamierzasz przywrócić, następnie wyloguj się z przestrzeni dyskowej.

> [!success]
>
> Jeśli korzystasz z interfejsu **FTP Explorer**, sprawdź [stronę pomocy](https://net2ftp.cluster020.hosting.ovh.net/help.html){.external}, aby poprawnie wykonać odzyskiwanie plików. Strona ta jest również dostępna poprzez przycisk `Help Guide`{.action} na dole interfejsu logowania do **FTP Explorer**.
>
> Jeśli do logowania się do przestrzeni dyskowej FTP używasz innego oprogramowania, zalecamy zapoznanie się z oficjalną dokumentacją dotyczącą oprogramowania, aby móc poprawnie wykonywać operacje.
>

#### Etap 4: przywracanie wybranego pliku lub plików

Kiedy masz już plik lub pliki, zaloguj się ponownie do przestrzeni dyskowej. Nie dodawaj jednak sufiksu do Twojego użytkownika FTP, aby się zalogować. Jeśli nie wpiszesz sufiksu, zyskasz dostęp do aktualnej zawartości Twojej przestrzeni dyskowej, a nie to wcześniejszej kopii zapasowej.

Po zalogowaniu wgraj wybrany plik lub pliki. W tym celu przejrzyj zawartość Twojego komputera, następnie wybierz pliki i zastąp nimi stare pliki.

> [!success]
>
> Jeśli korzystasz z interfejsu **FTP Explorer**, sprawdź [stronę pomocy](https://net2ftp.cluster020.hosting.ovh.net/help.html){.external}, aby poprawnie wykonać przywracanie plików. Strona ta jest również dostępna poprzez przycisk `Help Guide`{.action} na dole interfejsu logowania do **FTP Explorer**.
>
> Jeśli do logowania się do przestrzeni dyskowej FTP używasz innego oprogramowania, zalecamy zapoznanie się z oficjalną dokumentacją dotyczącą oprogramowania, aby móc poprawnie wykonywać operacje.
>

## Sprawdź również

[Korzystanie z programu FileZilla na Twoim hostingu](/pages/web_cloud/web_hosting/ftp_filezilla_user_guide){.external}

[Korzystanie z programu Cyberduck na Twoim hostingu](/pages/web_cloud/web_hosting/ftp_cyberduck_user_guide_on_mac){.external}

[Tworzenie i pobieranie kopii zapasowej bazy danych na hostingu WWW](/pages/web_cloud/web_hosting/sql_database_export)

W przypadku wyspecjalizowanych usług (pozycjonowanie, rozwój, etc.) skontaktuj się z [partnerami OVHcloud](/links/partner).

Jeśli chcesz otrzymywać wsparcie w zakresie konfiguracji i użytkowania Twoich rozwiązań OVHcloud, zapoznaj się z naszymi [ofertami pomocy](/links/support).

Dołącz do [grona naszych użytkowników](/links/community).