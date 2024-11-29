---
title: "Tutorial - Jak zablokować dostęp do mojej strony dla niektórych adresów IP za pomocą pliku .htaccess?"
excerpt: "Odkryj operacje możliwe przy użyciu pliku .htaccess, w celu zablokowania dostępu do Twojej strony WWW dla niektórych adresów IP"
updated: 2024-03-14
---

## Wprowadzenie 

Tutorial ten pomoże Ci zabezpieczyć dostęp do Twoich stron WWW z sieci zewnętrznej, zapobiec włamaniom i próbom ataków DDoS lub je naprawić.

Możesz to zrobić, używając pliku ".htaccess", pliku tekstowego wykrywanego przez serwer www (Apache), który pozwala na zdefiniowanie specjalnych reguł w katalogu i wszystkich jego podkatalogach.

Możesz utworzyć kilka plików ".htaccess" w [przestrzeni FTP](/pages/web_cloud/web_hosting/ftp_connection) Twojego hostingu, ale **jeden** na katalog lub subkatalog, aby uniknąć konfliktów między różnymi plikami ".htaccess".

**Dowiedz się, jak zablokować dostęp do Twojej strony WWW dla niektórych adresów IP poprzez plik ".htaccess".**

> [!warning]
>
> OVHcloud oddaje do Twojej dyspozycji usługi, których konfiguracja, zarządzanie i odpowiedzialność spoczywa na Ciebie. W związku z tym należy zapewnić ich prawidłowe funkcjonowanie.
> 
> Oddajemy w Twojej ręce niniejszy przewodnik, którego celem jest pomoc w jak najlepszym wykonywaniu bieżących zadań. W przypadku trudności zalecamy skorzystanie z pomocy [wyspecjalizowanego usługodawcy](/links/partner). Niestety firma OVHcloud nie będzie mogła udzielić wsparcia w tym zakresie. Więcej informacji znajduje się w sekcji [Sprawdź również](#go-further) niniejszego przewodnika.
>

## Wymagania początkowe

- Posiadanie [hostingu OVHcloud](/links/web/hosting)

## W praktyce

> [!primary]
>
> Plik ".htaccess" może być umieszczony w kilku różnych folderach przy jednoczesnym przestrzeganiu zasady tylko **tylko** pliku ".htaccess" dla każdego katalogu lub podfolderu.
>
> Parametry określone przez plik ".htaccess" odnoszą się do katalogu, w którym jest zainstalowany, oraz do wszystkich jego podkatalogów.
>
> Aby edytować (lub utworzyć) te katalogi, zaloguj się do przestrzeni FTP Twojego hostingu. W razie potrzeby skorzystaj z przewodnika "[Dostęp do przestrzeni dyskowej](/pages/web_cloud/web_hosting/ftp_connection)".
>

### Blokuj IP, zakres adresów IP, domenę lub wszystkie adresy IP w danym kraju 

Aby zablokować dostęp do Twojego hostingu za pomocą ".htaccess".<br>
Zalecamy ostrożność podczas tworzenia składni oraz ustawień, które blokujesz, aby uniknąć blokady Twojej strony WWW podczas wyświetlania strony i/lub hostowanych skryptów.<br>
W przypadku błędu możesz zawsze zalogować się do [przestrzeni FTP](/pages/web_cloud/web_hosting/ftp_connection) Twojego hostingu, aby poprawić tę sytuację. 

> [!primary]
>
> Hosting współdzielony działa obecnie z **Apache 2.4**. Od wersji **Apache 2.3** wprowadzono zmienne i zmieniła się składnia edycji ograniczeń/zezwoleń na dostęp.
>
> Ponieważ poprzednia składnia jest bardzo popularna, jest ona nadal aktywna w naszych infrastrukturach. Jednak Apache* jest uważany za przestarzałą i wkrótce może nie być już dostępny. W niniejszym tutorialu znajdują się przykłady opisujące obydwie składnie.
>
> Szczegółowe informacje na temat nowej składni znajdują się na następujących oficjalnych stronach:
>
> - [Dokumentacja kontroli dostępu Apache 2.4](https://httpd.apache.org/docs/2.4/en/howto/access.html){.external}
> - [Dokumentacja dotycząca modułu mod_authz_core Apache 2.4](https://httpd.apache.org/docs/2.4/mod/mod_authz_core.html){.external}
>

#### Zablokuj IP

Aby zablokować określony adres IP, wprowadź jeden z dwóch poniższych kodów do Twojego pliku ".htaccess":

> [!tabs]
> Składnia historyczna
>>
>> ```bash
>> Deny from IP_address
>> ```
>>
> Składnia od Apache 2.3
>>
>> ```bash
>> <RequireAll>
>> Require all granted
>> Require not ip IP_address
>> </RequireAll>
>> ```
>>

- **Przykład**: jeśli chcesz zablokować adres IP 203.0.113.0, musisz napisać jeden z dwóch poniższych kodów:

> [!tabs]
> Składnia historyczna
>>
>> ```bash
>> Deny from 203.0.113.0
>> ```
>>
> Składnia od Apache 2.3
>>
>> ```bash
>> <RequireAll>
>> Require all granted
>> Require not ip 203.0.113.0
>> </RequireAll>
>> ```
>>

#### Zablokuj zakres adresów IP

Aby zablokować zakres adresów IP, wprowadź jeden z dwóch poniższych kodów do pliku ".htaccess":

> [!tabs]
> Składnia historyczna
>>
>> ```bash
>> Deny from IP_range
>> ```
>>
> Składnia od Apache 2.3
>>
>> ```bash
>> <RequireAll>
>> Require all granted
>> Require not ip IP_range
>> </RequireAll>
>> ```
>>

- **Przykład**: jeśli chcesz zablokować wszystkie adresy IP 203.0.113.x, wpisz jeden z dwóch poniższych kodów:

> [!tabs]
> Składnia historyczna
>>
>> ```bash
>> Deny from 203.0.113
>> ```
>>
> Składnia od Apache 2.3
>>
>> ```bash
>> <RequireAll>
>> Require all granted
>> Require not ip 203.0.113
>> </RequireAll>
>> ```
>>

#### Zablokuj domenę

Niektóre domeny mają dostęp do Twojego hostingu poprzez przekierowania lub zapytania.

Aby zablokować domenę, wprowadź jeden z dwóch poniższych kodów do pliku ".htaccess":

> [!tabs]
> Składnia historyczna
>>
>> ```bash
>> Deny from domain
>> ```
>>
> Składnia od Apache 2.3
>>
>> ```bash
>> <RequireAll>
>> Require not host domain
>> </RequireAll>
>> ```
>>

- **Przykład**: jeśli chcesz zablokować domenę domain.tld, napisz jeden z dwóch kodów:

> [!tabs]
> Składnia historyczna
>>
>> ```bash
>> Deny from domain.tld
>> ```
>>
> Składnia od Apache 2.3
>>
>> ```bash
>> <RequireAll>
>> Require not host domain.tld
>> </RequireAll>
>> ```
>>

#### Blokuj adresy IP danego kraju

> [!primary]
>
> Wszystkie adresy IP (w tym publiczne adresy IP) posiadają geolokalizację na poziomie kraju. Pozwala to na zapoznanie się z pochodzeniem strumieni IP i fizyczne wykrycie IP. 
>
> Plik ".htaccess" pozwala na zablokowanie adresów IP lokalizowanych geograficznie w danym kraju. 
> Oznacza to, że wszystkie osoby, które będą starały się odwiedzić Twoją stronę z tego kraju, zostaną zablokowane (chyba że będą korzystały z połączenia VPN z geolokalizacją IP w innym kraju).
>
> Blokowanie przez ".htaccess" odbywa się za pomocą dwuliterowych "Country Codes" (ISO 3166-1 alpha2) krajów.
>
> Kilka stron WWW zawiera listę krajów oraz ich odpowiednich kodów "Country Codes" (w tym [https://www.iban.com/country-codes](https://www.iban.com/country-codes){.external} (niezależny od OVHcloud).
>

Aby zablokować wszystkie adresy IP danego kraju, wprowadź jeden z dwóch poniższych kodów do pliku ".htaccess":

> [!tabs]
> Składnia historyczna
>>
>> ```bash
>> SetEnvIf GEOIP_COUNTRY_CODE Country_Code BlockCountry
>> Deny from env=BlockCountry
>> ```
>>
> Składnia od Apache 2.3 
>> Umieść wszystko na górze ".htaccess"
>>
>> ```bash
>> RewriteCond %{ENV:GEOIP_COUNTRY_CODE} ^(Country_Code)$
>> RewriteRule ^(.*)$ - [F,L]
>> ```
>>

- **Przykład**: jeśli chcesz zablokować geolokalizowane adresy IP na Fidżi (FJ) i Grenlandii (GR), musisz napisać jeden z następujących kodów:

> [!tabs]
> Składnia historyczna
>>
>> ```bash
>> SetEnvIf GEOIP_COUNTRY_CODE FJ BlockCountry
>> SetEnvIf GEOIP_COUNTRY_CODE GR BlockCountry
>> Deny from env=BlockCountry
>> ```
>>
> Składnia od Apache 2.3 
>> Umieść wszystko na górze ".htaccess"
>>
>> ```bash
>> RewriteCond %{ENV:GEOIP_COUNTRY_CODE} ^(FJ|GR)$
>> RewriteRule ^(.*)$ - [F,L]
>> ```
>>

### Aby autoryzować tylko kilka IP, zakres IP lub wszystkie adresy IP w danym kraju

Zamiast ograniczać dostęp do jednego lub kilku adresów IP i dawać innym dostęp do Twojego hostingu, możesz wykonać operację odwrotną, blokując wszystkie adresy IP i zezwalając na dostęp do Twojej usługi tylko jednym lub więcej adresów IP.

#### Zezwalaj na jeden lub kilka adresów IP

Aby nadać tylko jednemu adresowi IP dostęp do Twojej usługi, wprowadź jeden z dwóch poniższych kodów w Twoim pliku ".htaccess":

> [!tabs]
> Składnia historyczna
>>
>> ```bash
>> order deny,allow
>> deny from all
>> Allow from IP_address
>> ```
>>
> Składnia od Apache 2.3
>>
>> ```bash
>> Require ip IP_address
>> ```
>>

- **Przykład**: jeśli chcesz autoryzować dostęp do hostingu tylko dla adresów IP 203.0.113.0 i 203.0.113.1, wpisz jeden z dwóch poniższych kodów:

> [!tabs]
> Składnia historyczna
>>
>> ```bash
>> order deny,allow
>> deny from all
>> Allow from 203.0.113.0
>> Allow from 203.0.113.1
>> ```
>>
> Składnia od Apache 2.3
>>
>> ```bash
>> Require ip 203.0.113.0 203.0.113.1
>> ```
>>

#### Zezwalaj na przedział adresów IP

Aby zezwolić na dostęp do zakresu adresów IP, wprowadź jeden z dwóch poniższych kodów w pliku ".htaccess":

> [!tabs]
> Składnia historyczna
>>
>> ```bash
>> order deny,allow
>> deny from all
>> Allow from IP_range
>> ```
>>
> Składnia od Apache 2.3 
>> Umieść wszystko na górze ".htaccess"
>>
>> ```bash
>> Require ip IP_range
>> ```
>>

- **Przykład**: jeśli chcesz autoryzować dostęp do Twojego hostingu tylko dla adresów IP 203.0.113.x, wpisz jeden z dwóch poniższych kodów:

> [!tabs]
> Składnia historyczna
>>
>> ```bash
>> order deny,allow
>> deny from all
>> Allow from 203.0.113
>> ```
>>
> Składnia od Apache 2.3 
>> Umieść wszystko na górze ".htaccess"
>>
>> ```bash
>> Require ip 203.0.113
>> ```
>>

#### Zatwierdź wszystkie adresy IP danego kraju

Aby zezwolić na dostęp do Twojej usługi dla wszystkich adresów IP danego kraju, wprowadź do Twojego pliku ".htaccess" jeden z dwóch poniższych kodów:

> [!tabs]
> Składnia historyczna
>>
>> ```bash
>> order deny,allow
>> deny from all
>> SetEnvIf GEOIP_COUNTRY_CODE Country_Code AllowCountry
>> Allow from env=AllowCountry
>> ```
>>
> Składnia od Apache 2.3 
>> Umieść wszystko na górze ".htaccess"
>>
>> ```bash
>> RewriteCond %{ENV:GEOIP_COUNTRY_CODE} !^(Country_Code)$
>> RewriteRule ^(.*)$ - [F,L]
>> ```
>>

- **Przykład**: jeśli chcesz autoryzować dostęp do hostingu wyłącznie na Fidżi (FJ) i Grenlandii (GR), musisz napisać jeden z dwóch kodów:

> [!tabs]
> Składnia historyczna
>>
>> ```bash
>> order deny,allow
>> deny from all
>> SetEnvIf GEOIP_COUNTRY_CODE FJ AllowCountry
>> SetEnvIf GEOIP_COUNTRY_CODE GR AllowCountry
>> Allow from env=AllowCountry
>> ```
>>
> Składnia od Apache 2.3 
>> Umieść wszystko na górze ".htaccess"
>>
>> ```bash
>> RewriteCond %{ENV:GEOIP_COUNTRY_CODE} !^(FJ|GR)$
>> RewriteRule ^(.*)$ - [F,L]
>> ```
>>

## Suplementy do pliku ".htaccess"

Niezależnie od bezpieczeństwa ogólnego dostępu do hostingu plik ".htaccess" pozwala na wykonywanie innych operacji. Poniżej znajdziesz trzy dodatkowe tutoriale OVHcloud dotyczące tego tematu:

- [Chroń interfejs administracyjny swojej strony za pomocą ".htaccess"](/pages/web_cloud/web_hosting/htaccess_protect_directory_by_password).
- [Zapisz adresy URL za pomocą mod_rewrite](/pages/web_cloud/web_hosting/htaccess_url_rewriting_using_mod_rewrite).
- [Wykonywanie innych operacji przy użyciu pliku ".htaccess"](/pages/web_cloud/web_hosting/htaccess_what_else_can_you_do).

## Sprawdź również <a name="go-further"></a>

W przypadku wyspecjalizowanych usług (pozycjonowanie, rozwój, etc.) skontaktuj się z [partnerami OVHcloud](/links/partner).

Jeśli chcesz otrzymywać wsparcie w zakresie konfiguracji i użytkowania Twoich rozwiązań OVHcloud, zapoznaj się z naszymi [ofertami pomocy](/links/support).

Dołącz do [grona naszych użytkowników](/links/community).