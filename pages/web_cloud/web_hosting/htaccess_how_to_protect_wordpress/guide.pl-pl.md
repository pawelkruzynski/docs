---
title: "Tutorial - Użyj pliku htaccess w systemie WordPress"
excerpt: "Dowiedz się, jak zabezpieczyć blog WordPress jednym lub kilkoma plikami htaccess"
updated: 2024-05-28
---

## Wprowadzenie

Tutorial wyjaśnia, jak skonfigurować niektóre funkcjonalności hostingu za pomocą jednego lub kilku plików **.htaccess**, zwłaszcza w celu zmiany ustawień niektórych lub wszystkich Twoich stron WWW (przekierowania, zakazy dostępu, ograniczone uprawnienia, kontrola cache, itp.).

> [!warning]
>
> OVHcloud oddaje do Twojej dyspozycji usługi, których konfiguracja, zarządzanie i odpowiedzialność spoczywa na Ciebie. W związku z tym należy zapewnić ich prawidłowe funkcjonowanie.
>
> Oddajemy do Twojej dyspozycji niniejszy tutorial, którego celem jest pomoc w jak najlepszym wykonywaniu bieżących zadań. W przypadku trudności zalecamy skorzystanie z pomocy [wyspecjalizowanego usługodawcy](/links/partner) lub [edytora CMS WordPress](https://wordpress.com/support/){.external}. Niestety firma OVHcloud nie będzie mogła udzielić wsparcia w tym zakresie. Więcej informacji znajduje się w sekcji ["Sprawdź również"](#go-further) niniejszego tutoriala.
>

**Dowiedz się, jak zabezpieczyć moduł WordPress korzystając z jednego lub kilku plików htaccess.**

## Wymagania początkowe

- Posiadanie [hostingu](/links/web/hosting) i zainstalowanie modułu WordPress
- Możliwość korzystania z klienta FTP takiego jak [FileZilla](https://filezilla-project.org/). Zapoznaj się z naszym przewodnikiem "[Użyj FileZilla](/pages/web_cloud/web_hosting/ftp_filezilla_user_guide)".

Pliki **.htaccess** mogą być tworzone i modyfikowane przy pomocy edytorów tekstu, takich jak:

- [Notatnik](https://support.microsoft.com/pl-pl/windows/pomoc-w-aplikacji-notatnik-4d68c388-2ff2-0e7f-b706-35fb2ab88a8c){.external} systemu Windows;
- [TextEdit](https://support.apple.com/pl-pl/guide/textedit/welcome/mac){.external} na macOS;
- [Notepad++](https://notepad-plus-plus.org/){.external}.

> [!primary]
>
> Zaproponowane poniżej rozwiązania w zakresie bezpieczeństwa nie są wyczerpujące.
>
> Na przykład, jeśli używasz innego **C**ontent **M**anagement **S**ystem (**CMS**) niż WordPress, dostępne są inne rozwiązania bezpieczeństwa.
>
> Jeśli nie korzystasz z CMS-a, OVHcloud udostępnia również tutorial dotyczący [ochrona katalogu lub interfejsu administracyjnego Twojej strony WWW za pomocą plików .htaccess](/pages/web_cloud/web_hosting/htaccess_protect_directory_by_password).
>
> W przypadku pytań dotyczących tworzenia, użytkowania lub programowania Twojej strony WWW, skontaktuj się z naszym [społecznością użytkowników](/links/community) lub naszymi [partnerami OVHcloud](/links/partner). Zespoły pomocy OVHcloud nie będą w stanie udzielić Ci wsparcia w tym zakresie.
>

## FAQ

### Czym jest plik **.htaccess**?

Plik **.htaccess** pozwala na skonfigurowanie serwera www. W przypadku hostingu współdzielonego chodzi o serwer open source "**Apache**". Składnia tego pliku jest definiowana przez organ, który edytuje i utrzymuje **Apache**. W przeciwieństwie do większości plików konfiguracyjnych serwera, pliki **.htaccess** znajdują się w katalogach stron www, a dokładniej w przestrzeni dyskowej FTP Twojego hostingu. Plik **.htaccess** będzie miał wpływ na katalog, w którym jest obecny, oraz na wszystkie podkatalogi znajdujące się wewnątrz.

Nasze pakiety hostingowe nie zezwalają na pliki konfiguracyjne serwera. Jednak pliki **.htaccess** umożliwiają modyfikację niektórych funkcji i zachowań. Ponadto, nie ma potrzeby restartu serwera **Apache**, aby uwzględnić informacje i zmiany zapisane w pliku **.htaccess**. Wszystkie nasze oferty[hosting OVHcloud](/links/web/hosting) pozwalają na skonfigurowanie plików **.htaccess**.

Punkt przed nazwą pliku **.htaccess** (który sam nie ma rozszerzenia) oznacza ukryty plik. Ponadto pliki te nie są dostępne dla użytkowników z zewnątrz odwiedzających Twoją stronę WWW.

### Co to jest serwer www?

Serwer www to oprogramowanie pozwalające na wymianę informacji w sieci przy użyciu protokołu *HTTP*.<br>
Istnieje kilka z nich, w tym *Apache*, *Nginx*, *Tomcat* lub moduł http zawarty w *NodeJS*.

### Jakie środki ostrożności należy podjąć?

Nieprawidłowa konfiguracja pliku **.htaccess** może powodować błędy na serwerze (np. błąd 500: *Internal Server Error*), a nawet spowodować, że usługa będzie całkowicie niedostępna. Przyzwyczaij się do systematycznych kopii zapasowych wersji plików funkcjonalnych, tak aby przywrócić poprzedni stan w przypadku wystąpienia anomalii w wyniku modyfikacji.

Podobnie, jeśli nie masz przyzwyczajenia do obsługi tego typu pliku, przeprowadź test dla każdego elementu, który zmienisz. Dzięki temu unikasz utraty czasu, aby odnaleźć linie, które spowodowały usterkę Twojego serwera www. Błąd konfiguracji lub prosty błąd w ustawieniach mogą zagrażać konfiguracji serwera WWW i w związku z tym jego działaniu.

### Jakie narzędzia?

- klient FTP do pobierania plików (FileZilla, Cyberduck);
- edytor tekstu.

### Gdzie znajdują się pliki .htaccess w programie WordPress?

Jak zostało wspomniane we wstępie, na tym samym hostingu możesz mieć kilka plików **.htaccess**. Każdy z tych plików definiuje reguły dla katalogu, w którym się znajduje, oraz katalogów, które zawiera.

Większość zmian zostanie zrealizowana na poziomie **rdzenia strony internetowej**. Zainstalowany domyślnie plik **.htaccess** umieszczony w katalogu głównym witryny zawiera następujące wiersze:

```bash
# BEGIN WordPress
# Wygenerowane są wytyczne (linie) między "BEGIN WordPress" i "END WordPress"
# dynamicznie, i powinny być modyfikowane tylko za pomocą filtrów WordPress.
# Wszelkie zmiany w dyrektywach znajdujących się między tymi znacznikami będą przeciążone.

<IfModule mod_rewrite.c>
RewriteEngine On
RewriteRule .* - [E=HTTP_AUTHORIZATION:%{HTTP:Authorization}]
RewriteBase /
RewriteRule ^index\.php$ - [L]
RewriteCond %{REQUEST_FILENAME} !-f
RewriteCond %{REQUEST_FILENAME} !-d
RewriteRule . /index.php [L]
</IfModule>

# END WordPress
```

**Wyjaśnienia powyższego kodu**:

- **#** : znak używany do umieszczania linii w komentarzu.
- **RewriteEngine On**: aktywuje moduł Apache `mod_rewrite`, pozwalający na przekierowanie adresu URL na pokład (pozwala również na przekierowanie adresu URL na inny adres URL).
- **RewriteRule**: składnia ta jest napisana zgodnie ze schematem `RewriteRule Model Substytucja`. Zapis może być wyświetlany kilka razy w pliku **.htaccess** (tak jest w pliku domyślnym, że znajduje się w katalogu głównym instalacji WordPress). Kolejność zapisu w pliku jest kluczowa, uważaj na kolejność zapisywania reguł.
- **RewriteBase**: wskazuje, że korzeń witryny jest `/`.
- **RewriteCond**: są to warunki wstępne dla następującej reguły. W naszym przypadku pierwszy warunek wyłącza adresy URL zawierające ścieżkę do prawdziwego pliku, podczas gdy drugi wyklucza, że podkatalogi.

### Co mogę dodać do pliku **.htaccess** przy użyciu WordPress?

Istnieje kilka sposobów definiowania i modyfikowania parametrów, które zmieniają zachowanie serwera (niektóre ograniczenia istnieją jednak w zależności od hostingu):

- modyfikować pliki konfiguracyjne Twojego serwera;
- dodawanie lub modyfikowanie dyrektyw w pliku konfiguracyjnym **wp-config.php** w katalogu głównym Twojej strony WWW;
- zmiana lub dodanie dyrektyw w pliku **.htaccess** do katalogu głównego.

## W praktyce

> [!warning]
>
> Przed przejściem przez kolejne etapy, należy przekierować protokół HTTP na HTTPS. W tym celu postępuj zgodnie z instrukcjami zawartymi w naszym przewodniku ["Aktywacja protokołu HTTPS na stronie WWW za pomocą certyfikatu SSL"](/pages/web_cloud/web_hosting/ssl-activate-https-website#etap-1-aktywacja-certyfikatu-ssl-na-hostingu).

### Nie wyświetlaj katalogów i podkatalogów

Aby uniknąć sytuacji, w której wszystkie osoby odwiedzające Twoją stronę WWW będą wyświetlały zawartość podkatalogów (a tym samym dostarczały hakerom informacje o zastosowanych tematach lub rozszerzeniach), zablokuj wyświetlanie treści dodając tę linię do Twojego pliku **.htaccess**:

```bash
Options All -Indexes
```

### Chroń plik konfiguracyjny

Twój plik **wp-config.php**, obecny na Twojej stronie WWW, zawiera wrażliwe informacje dotyczące konfiguracji. Zablokuj dostęp do tego pliku, dodając następujące wiersze w pliku **.htaccess**:

```bash
<Files wp-config.php>
    order allow,deny
    deny from all
    satisfy all
</Files>
```

### Zablokuj adres IP

Jeśli zidentyfikowałeś złośliwy adres IP, w pliku **.htaccess**wpisz poniższy wiersz:

> [!tabs]
> **IPv4**
>>
>>```bash
>> <Limit GET POST>
>>   order allow,deny 
>>   deny from 203.0.113.0
>>   allow from all
>> </Limit>
>>```
>>
>> W tym przykładzie `203.0.113.0` oznacza adres IPv4, który ma zostać zablokowany.
>>
> **IPv6**
>>
>>```bash
>> <Limit GET POST>
>>   order allow,deny 
>>   deny from 2001:db8:1:1b00:203:0:113:0
>>   allow from all
>> </Limit>
>>```
>>
>> W tym przykładzie `2001:db8:1:1b00:203:0:113:0` oznacza adres IPv6, który ma zostać zablokowany.
>>

Aby uzyskać więcej informacji na ten temat, zapoznaj się z naszym przewodnikiem dotyczącym ["ograniczenia dostępu przez IP poprzez plik .htaccess"](/pages/web_cloud/web_hosting/htaccess_how_to_block_a_specific_ip_address_from_accessing_your_website).

#### Zablokuj adres IP z katalogu wp-admin (lub z innych katalogów)

Katalog **wp-admin** pozwala na połączenie z Twoim interfejsem administracyjnym (metoda działa również z innymi katalogami, ale odpowiadają one adresom URL, które nie prowadzą do określonego interfejsu). Aby chronić ten katalog, zezwalaj na dostęp do jednego lub kilku adresów IP przy użyciu następującego kodu, który ma zostać umieszczony w Twojej **.htaccess**:

> [!tabs]
> **IPv4**
>>
>>```bash
>> <Limit GET POST PUT>
>>   order deny,allow 
>>   deny from all
>>   allow from 203.0.113.0
>>   allow from 203.0.113.1
>> </Limit>
>>```
>>
>> W tym przykładzie tylko adresy IPv4 `203.0.113.0` i `203.0.113.1` są autoryzowane do dostępu do katalogu, w którym znajduje się plik .htaccess.
>>
> **IPv6**
>>
>>```bash
>> <Limit GET POST PUT>
>>   order deny,allow 
>>   deny from all
>>   allow from 2001:db8:1:1b00:203:0:113:0
>>   allow from 2001:db8:1:1b00:203:0:113:1
>> </Limit>
>>```
>>
>> W tym przykładzie tylko adresy IPv6 `2001:db8:1:1b00:203:0:113:0` i `2001:db8:1:1b00:203:0:113:1` są autoryzowane do dostępu do katalogu, w którym znajduje się plik .htaccess.

### Ważne informacje

- Przed wykonaniem operacji zapisz funkcjonalną wersję Twojego pliku **.htaccess**.
- Jeśli wprowadzone przez Ciebie zmiany powodują błąd, zastąp (za pośrednictwem klienta FTP) plik **.htaccess** w linii poprzedniej wersji.
- Możesz zarządzać ustawieniami w pliku **wp-config.php**.
- Pliki **.htaccess** są szczególnie skuteczne w zarządzaniu adresami URL, przekierowaniami i zabezpieczeniami strony www.

## Sprawdź również <a name="go-further"></a>

Sprawdź [tutorial dostępny na stronie internetowej Fundacji Apache](https://httpd.apache.org/docs/2.4/en/howto/htaccess.html).

W przypadku wyspecjalizowanych usług (pozycjonowanie, rozwój, etc.) skontaktuj się z [partnerami OVHcloud](/links/partner).

Jeśli chcesz otrzymywać wsparcie w zakresie konfiguracji i użytkowania Twoich rozwiązań OVHcloud, zapoznaj się z naszymi [ofertami pomocy](/links/support).

Dołącz do [grona naszych użytkowników](/links/community).