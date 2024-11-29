---
title: "Geolokalizacja strony WWW w danym kraju"
excerpt: "Dowiedz się, jak geolokalizować Twoją stronę WWW za pomocą geolokalizowanych adresów IP"
updated: 2022-12-22
---

## Wprowadzenie
  
Wyszukiwarki (Google, Bing, Yahoo, ...) wykorzystują roboty do indeksowania i pozycjonowania na wszystkich stronach internetowych. W pierwszej kolejności odnoszą się one do lokalizowanych geograficznie stron w kraju, z którego prowadzą Państwo badania.

**Przykład**: Jeśli korzystasz z wyszukiwarki i umieścisz się w Anglii, znajdziesz strony z geolokalizacją w Anglii, która wyświetla się wyżej w wynikach wyszukiwania niż inne strony.

Ta geolokalizacja opiera się na adresie IP hostingu, na którym znajduje się Twoja strona WWW.

Opcja geolokalizacji na Twoim hostingu może być przydatna w pozycjonowaniu (SEO), jeśli Twoja strona WWW jest wyświetlana głównie w innym kraju niż kraj, w którym znajduje się Twój hosting.

**Dowiedz się, jak korzystać z geolokalizacji Twojej strony WWW przy użyciu geolokalizowanych adresów IP.**
  
## Wymagania początkowe

- Dostęp do [Panelu klienta OVHcloud](/links/manager)
- Posiadanie [hostingu OVHcloud](/links/web/hosting)
- Posiadanie [domeny](/links/web/domains)
  
## W praktyce

Dla stron www odwiedzanych głównie za granicą i hostowanych na naszej infrastrukturze hostingu współdzielonego OVHcloud proponujemy opcję geolokalizacji za pomocą adresu IP. Umożliwia lepsze pozycjonowanie stron www w kraju, w którym znajduje się wybrany adres IP z opcją.

Aby skorzystać z opcji geolokalizacji IP, zaloguj się do [Panelu klienta OVHcloud](/links/manager){.external}.

Po zalogowaniu przejdź do sekcji `Web Cloud`{.action}, kliknij przycisk `Hosting`{.action}, następnie wybierz odpowiedni hosting z listy.<br>
Następnie kliknij zakładkę `MultiSite`{.action}, a następnie przycisk `...`{.action} znajduje się po prawej stronie Twojej domeny w tabeli. Następnie kliknij polecenie `Zmień domenę`{.action}.

![hosting multisite](/pages/assets/screens/control_panel/product-selection/web-cloud/web-hosting/multisite/modify-a-domain.png){.thumbnail}

W nowym oknie, które się wyświetla zaznacz kratkę `Geolokalizacja IP`{.action}, aby wyświetlić rozwijane menu.

![geolokacja opcja](/pages/assets/screens/control_panel/product-selection/web-cloud/web-hosting/multisite/country-ip-selection.png){.thumbnail}

Wybierz adres IP kraju, dla którego chcesz zlokalizować swoją stronę WWW, spośród 12 proponowanych krajów: *Republika Czeska, Finlandia, Francja, Niemcy, Irlandia, Włochy, Litwa, Holandia, Polska, Portugalia, Hiszpania, Wielka Brytania*.

Kliknij przycisk `Dalej`{.action}, a następnie kliknij `Zatwierdź`{.action} w oknie podsumowującym.

>[!primary]
>
> Jeśli aktywna strefa DNS Twojej domeny jest w pełni zarządzana w Twoim [Panelu klienta OVHcloud](/links/manager), wpis A w strefie DNS Twojej domeny zostanie automatycznie zmieniony. Możesz sprawdzić, czy adres IP został zaktualizowany w naszym przewodniku dotyczącym [edycji strefy DNS OVHcloud](/pages/web_cloud/domains/dns_zone_edit).
>
> W przeciwnym razie przeprowadź ręcznie zmianę u dostawcy zarządzającego aktywną strefą DNS Twojej domeny. Zapoznaj się z dokumentacją [tutaj](/pages/web_cloud/web_hosting/clusters_and_shared_hosting_IP) zawierającą listę adresów IP naszej infrastruktury hostingu współdzielonego OVHcloud.
>
> W każdym przypadku, aby modyfikacja stała się w pełni skuteczna i widoczna w Internecie, konieczny będzie okres propagacji od **4 do 24 godzin**.
>

## Sprawdź również

W przypadku wyspecjalizowanych usług (pozycjonowanie, rozwój, etc.) skontaktuj się z [partnerami OVHcloud](/links/partner).

Jeśli chcesz otrzymywać wsparcie w zakresie konfiguracji i użytkowania Twoich rozwiązań OVHcloud, zapoznaj się z naszymi [ofertami pomocy](/links/support).

Dołącz do [grona naszych użytkowników](/links/community). 