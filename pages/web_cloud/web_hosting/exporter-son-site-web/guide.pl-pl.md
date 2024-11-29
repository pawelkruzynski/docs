---
title: "Eksportowanie witryny internetowej"
excerpt: "Dowiedz się, jak wyeksportować swoją witrynę internetową OVHcloud"
updated: 2022-02-03
---

## Wprowadzenie 

Niniejszy przewodnik przedstawia etapy procedury eksportu wszystkich elementów Twojej witryny internetowej w standardowym formacie z poziomu [hostingu WWW OVHcloud](/links/web/hosting){.external}.

**Dowiedz się, jak wyeksportować swoją witrynę internetową w hostingu OVHcloud.**

## Wymagania początkowe

- Posiadanie [hostingu WWW OVHcloud](/links/web/hosting){.external}
- Dostęp do [panelu klienta OVHcloud](/links/manager){.external}.

## W praktyce

### Etap 1: pobranie plików z Twojej przestrzeni dyskowej FTP

#### 1.1 Zaloguj się do przestrzeni dyskowej.

Aby zalogować się do przestrzeni dyskowej, powinieneś posiadać następujące elementy:

- aktywne konto FTP lub SSH;
- hasło powiązane z kontem FTP lub SSH;
- adres serwera;
- port połączenia z serwerem.

Dane te otrzymasz w wiadomości e-mail potwierdzającej instalację hostingu. Jeśli nie posiadasz wskazanych wyżej informacji, zaloguj się do [panelu klienta OVHcloud](/links/manager){.external} w sekcji „Web” i kliknij `Hostingi`{.action} . Wybierz odpowiedni hosting i przejdź do karty `FTP - SSH`{.action}. 

![export-website](/pages/assets/screens/control_panel/product-selection/web-cloud/web-hosting/ftp-ssh/tab-pro.png){.thumbnail}

Wyświetlą się wówczas dane dotyczące Twojej przestrzeni dyskowej. Dzięki nim będziesz mógł odnaleźć dane potrzebne do zalogowania się do przestrzeni dyskowej. Jeśli potrzebujesz więcej informacji, zapoznaj się z przewodnikiem: [„Logowanie do przestrzeni dyskowej hostingu WWW”](/pages/web_cloud/web_hosting/ftp_connection){.external}. W razie utraty hasła zapoznaj się z instrukcjami zawartymi w przewodniku[„Zmiana hasła do konta FTP”](/pages/web_cloud/web_hosting/ftp_change_password){.external}.

Gdy będziesz posiadał już wszystkie potrzebne informacje, możesz pobrać pliki z przestrzeni dyskowej na dwa sposoby:

- **program kompatybilny z protokołem FTP lub SFTP**: zainstaluj na Twoim komputerze odpowiedni program, np. [ FileZilla](/pages/web_cloud/web_hosting/ftp_filezilla_user_guide). Jeśli chcesz uzyskać pomoc w zakresie korzystania z tego programu, skontaktuj się z jego producentem.

- **dostęp przez SSH**: wpisz odpowiednie komendy w terminalu, aby połączyć się z przestrzenią dyskową. Do tego dostępu konieczne są bardziej zaawansowane umiejętności techniczne oraz [posiadanie hostingu OVHcloud](/links/web/hosting){.external}. Aby uzyskać więcej informacji, zapoznaj się z naszą instrukcją [„Korzystanie z dostępu SSH do hostingu WWW”](/pages/web_cloud/web_hosting/ssh_on_webhosting){.external}. 

#### 1.2 Pobranie plików z przestrzeni dyskowej.

Po zalogowaniu się do przestrzeni dyskowej pobierz pliki Twojej witryny. **Zalecamy szczególną ostrożność przy wyborze katalogu, w którym znajdują się pliki Twojej witryny.** W przypadku instalacji tylko jednej strony WWW na hostingu, pliki powinny znaleźć się w katalogu „www”. Jeśli jednak zainstalowałeś na Twoim hostingu więcej witryn WWW, z pewnością skonfigurowałeś różne katalogi dla domen w opcji **MultiSite**.

Aby sprawdzić, w którym katalogu powinna zostać opublikowana strona WWW, przejdź do karty `MultiSite`{.action} w panelu klienta OVHcloud. W tabeli, która się wyświetla dla wybranej domeny znajdź `Katalog główny`{.action}.

![export-website](/pages/assets/screens/control_panel/product-selection/web-cloud/web-hosting/multisite/root-folders.png){.thumbnail}

### Etap 2: utworzenie i pobranie kopii bazy danych (opcjonalnie)

> [!primary]
>
> Ten etap jest opcjonalny, jeśli Twoja witryna nie wykorzystuje bazy danych.
>

Z naszego przewodnika dowiesz się, jak utworzyć i pobrać kopię zapasową bazy danych:
[„Tworzenie i pobieranie kopii zapasowej bazy danych na hostingu WWW”](/pages/web_cloud/web_hosting/sql_database_export){.external}.

Jeśli korzystasz z **serwera Web Cloud Databases** w Twojej witrynie, zapoznaj się z sekcją poświęconą kopii zapasowej w naszym przewodniku:
[Tworzenie i eksportowanie bazy danych na serwerze baz danych](/pages/web_cloud/web_cloud_databases/save-export-on-database-server){.external}.

### Etap 3: pobranie logów z hostingu OVHcloud

Jeśli chcesz pobrać historię logów Twojej witryny, możesz to zrobić z poziomu planu hostingu WWW.

Kliknij przycisk `Hosting`{.action} i wybierz odpowiednie rozwiązanie. Kliknij zakładkę `Statystyki i logi`{.action}. Następnie kliknij link pod napisem `Zobacz logi`{.action}:

![export-website](/pages/assets/screens/control_panel/product-selection/web-cloud/web-hosting/statistics-and-logs/view-logs.png){.thumbnail}

Pojawi się okno z różnymi typami dostępnych logów. Są one podzielone według miesięcy:

| Typ  	| Opis                                                                                                                                                                                         	|
|-------	|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------	|
| Web   	| Tutaj znajdziesz logi dotyczące odwiedzin Twojej witryny, a także działań wykonywanych z jej poziomu. Dzięki temu możesz wykryć np. próby włamania. 	|
| FTP   	| w tych logach są przechowywane połączenia z FTP.                                                                                                                     	|
| Error 	| różne błędy generowane przez Twoją witrynę.                                                                                                                                                    	|
| CGI   	| przeprowadzone wywołania skryptów cgi.bin.                                                                                                                                     	|
| out   	| statystyki hostingu w zakresie wywołań zewnętrznych.                                                                                                                  	|
| ssh   	| te logi przedstawiają różne połączenia zrealizowane za pomocą protokołu SSH.                                                                                                                      	|
| cron  	| wynik realizacji zaplanowanych przez Ciebie zadań.                                                                                                                                                	|

![export-website](/pages/assets/screens/other/web-tools/logs/raw-logs-general.png){.thumbnail}

Po wybraniu logów danego typu i z konkretnego miesiąca, są one prezentowane dzień po dniu:

![export-website](/pages/assets/screens/other/web-tools/logs/raw-logs.png){.thumbnail}

## Sprawdź również

[Logowanie do przestrzeni dyskowej hostingu](/pages/web_cloud/web_hosting/ftp_connection){.external}.

[Zmiana hasła do konta FTP](/pages/web_cloud/web_hosting/ftp_change_password){.external}.

[Korzystanie z programu FileZilla na Twoim hostingu](/pages/web_cloud/web_hosting/ftp_filezilla_user_guide){.external}.

[Korzystanie z dostępu przez SSH do hostingu WWW](/pages/web_cloud/web_hosting/ssh_on_webhosting){.external}. 

[Tworzenie i pobieranie kopii zapasowej bazy danych na hostingu WWW](/pages/web_cloud/web_hosting/sql_database_export){.external}.

[Pierwsze kroki z usługą Cloud Databases](/pages/web_cloud/web_cloud_databases/starting_with_clouddb){.external}.

W przypadku wyspecjalizowanych usług (pozycjonowanie, rozwój, etc.) skontaktuj się z [partnerami OVHcloud](/links/partner).

Jeśli chcesz otrzymywać wsparcie w zakresie konfiguracji i użytkowania Twoich rozwiązań OVHcloud, zapoznaj się z naszymi [ofertami pomocy](/links/support).

Dołącz do [grona naszych użytkowników](/links/community). 