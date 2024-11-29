---
title: "Skonfiguruj adres IPv6 dla swojej strony www"
excerpt: "Dowiedz się, jak sprawdzić, czy Twoja strona WWW jest kompatybilna z adresem IPv6"
updated: 2024-03-12
---

## Wprowadzenie

Sieć internetowa działa od początku lat 1990. zgodnie z normą IPv4. Ta norma pozwala na podanie adresu IP X.X.X.X (lub "X" to liczby od 0 do 255.) dla każdej maszyny podłączonej do sieci internetowej (serwery, komputery, smartfony, tablety, itp.). Jednakże norma ta ogranicza liczbę urządzeń podłączonych do sieci internetowej do około 4 miliardów, co w 2022 roku stanowiło mniej niż jedno urządzenie podłączone do sieci dla dwóch osób na Ziemi.

W rezultacie wprowadzono protokół **IPv6**, aby umożliwić podłączenie do sieci internetowej do 340oC urządzeń. Jego wdrożenie trwa od czasu do czasu, ponieważ cała sieć internetowa musi zawierać nową normę. 

Ponieważ adresy IPv4 są obecnie mniej dostępne, trudniej jest dodać nowe maszyny do sieci internetowej z normą IPv4. Połączenia z adresem IPv6 są jednak użyteczne tylko wtedy, gdy Twoja strona WWW jest również dostępna z tym samym protokołem. Im więcej stron internetowych będzie dostępnych w IPv6, tym bardziej różne podmioty działające w sieci internetowej będą przełączać swoje urządzenia/maszyny na nowy protokół.

Więcej informacji znajdziesz w artykule [Wikipedia](https://pl.wikipedia.org/wiki/IPv6){.external} dotyczącym protokołu IPv6.

Nasze pakiety hostingowe są kompatybilne z IPv6 od 2011 roku. Aktywacja tego protokołu była do niedawna opcjonalną opcją podczas konfiguracji. 

**Dowiedz się, jak sprawdzić, czy Twoja strona WWW jest kompatybilna z protokołem IPv6 i jak ją skonfigurować z adresem IPv6.**

## Wymagania początkowe

- Posiadanie [domeny](/links/web/domains){.external} w Panelu klienta OVHcloud.
- Posiadanie [hostingu](/links/web/hosting){.external}.
- Dostęp do [Panelu klienta OVHcloud](/links/manager){.external}.

## W praktyce

> [!warning]
>
> OVHcloud oddaje do Twojej dyspozycji usługi, których konfiguracja, zarządzanie i odpowiedzialność spoczywa na Ciebie. W związku z tym należy zapewnić ich prawidłowe funkcjonowanie.
> 
> Oddajemy w Twojej ręce niniejszy przewodnik, którego celem jest pomoc w jak najlepszym wykonywaniu bieżących zadań. W przypadku trudności zalecamy skorzystanie z pomocy [wyspecjalizowanego usługodawcy](/links/partner) i/lub kontakt z producentem oprogramowania. Niestety firma OVH nie będzie mogła udzielić wsparcia w tym zakresie. Więcej informacji znajduje się w sekcji ["Sprawdź również"](#go-further) niniejszego tutoriala.
> 

Jeśli Twoja strona nie jest skonfigurowana tak, aby działała z adresem IPv6, możesz dodać [adres IPv6 Twojego hostingu OVHcloud](/pages/web_cloud/web_hosting/clusters_and_shared_hosting_IP) do strefy DNS aktywnej domeny. Celem jest umożliwienie przeglądarkom internetowym znalezienia adresu IPv6 powiązanego z Twoją stroną WWW za pomocą Twojej domeny.

### Sprawdź kompatybilność IPv6 ze stroną www

Aby sprawdzić, czy Twoja strona WWW używa już adresu IPv6, użyj strony [ipv6-test.com](https://ipv6-test.com/validate.php){.external}. Dowiedz się, czy Twoja strona WWW odpowiada na ten nowy protokół IP. Jeśli tak nie jest, przejdź do opisu w naszym przewodniku.

### Etap 1: pobrać adres IPv6 Twojego hostingu

Zaloguj się do [Panelu klienta OVHcloud](/links/manager){.external}. W sekcji `Web Cloud`{.action} kliknij przycisk `Hosting`{.action}, wybierz odpowiedni hosting i przejdź do zakładki `Informacje ogólne`{.action}.

W ramce **IPv6** skopiuj wpis i przejdź do kolejnego etapu.

![IPv6](/pages/assets/screens/control_panel/product-selection/web-cloud/web-hosting/general-information/find-ipv6.png){.thumbnail}

### Etap 2: skonfiguruj aktywną strefę DNS Twojej domeny

> [!warning]
>
> Opcje CDN nie są kompatybilne z adresami IPv6. Jeśli skonfigurujesz adres IPv6 dla Twojej strony WWW, internauci nie będą korzystać z CDN.
>
> Dodanie, zmiana lub usunięcie wpisu DNS w strefie DNS domeny powoduje, że czas propagacji wynosi od **4 do 24 godzin**, aby stało się w pełni skuteczne.
>

Aby przeglądarka znalazła adres IPv6 z Twoją domeną, zmodyfikuj aktywną strefę DNS Twojej domeny. Skorzystaj z naszego przewodnika "[Edycja strefy DNS OVHcloud](/pages/web_cloud/domains/dns_zone_edit)", aby utworzyć wpis DNS typu **AAAA**.

W części `Web Cloud`{.action} kliknij `Domeny`{.action}. Wybierz nazwę domeny i przejdź do zakładki `Strefa DNS`{.action}. Kliknij przycisk `Dodaj rekord`{.action} po prawej stronie tabeli. 

Wpisz wcześniej skopiowany adres IPv6, używając typu rekordu **AAAA**.

![IPv6](/pages/assets/screens/control_panel/product-selection/web-cloud/domain-dns/dns-zone/add-dns-zone-entry-aaaa.png){.thumbnail}

## Przejdź dalej <a name="go-further"></a>

[Edycja strefy DNS OVHcloud](/pages/web_cloud/domains/dns_zone_edit)

W przypadku wyspecjalizowanych usług (pozycjonowanie, rozwój, etc.) skontaktuj się z [partnerami OVHcloud](/links/partner).

Jeśli chcesz otrzymywać wsparcie w zakresie konfiguracji i użytkowania Twoich rozwiązań OVHcloud, zapoznaj się z naszymi [ofertami pomocy](/links/support).

Dołącz do [grona naszych użytkowników](/links/community). 