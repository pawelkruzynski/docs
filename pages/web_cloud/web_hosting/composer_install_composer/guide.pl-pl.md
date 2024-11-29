---
title: "Instalacja Composer na hostingu"
excerpt: "Dowiedz się, jak zainstalować i zrobić pierwsze kroki w Composer"
updated: 2023-02-24
---

## Wprowadzenie 

[Composer](https://getcomposer.org/){.external} jest menedżerem zależności stworzonym dla języka PHP. Pozwala deweloperom PHP na umieszczanie w programach zewnętrznych bibliotek. "Composer" umożliwiło projektom PHP ułatwienie dystrybucji bibliotek i utrzymania ich kodu. Poza tym, od momentu utworzenia tego narzędzia, w ramach społeczności PHP udostępniano liczne dobre praktyki rozwoju, które poprawiły biblioteki społeczności PHP. Te dobre praktyki są dokumentowane w formie [PSR](http://www.php-fig.org/){.external}.

**Dowiedz się, jak zainstalować i zrobić pierwsze kroki z Composer**

> [!warning]
>
> OVHcloud oddaje do Twojej dyspozycji usługi, których konfiguracja, zarządzanie i odpowiedzialność spoczywa na Ciebie. W związku z tym należy zapewnić ich prawidłowe funkcjonowanie.
> 
> Oddajemy w Twojej ręce niniejszy przewodnik, którego celem jest pomoc w jak najlepszym wykonywaniu bieżących zadań. W przypadku trudności zalecamy skorzystanie z pomocy [wyspecjalizowanego usługodawcy](/links/partner) i/lub kontakt z producentem oprogramowania. Niestety firma OVH nie będzie mogła udzielić wsparcia w tym zakresie. Więcej informacji znajduje się w sekcji ["Sprawdź również"](#go-further) niniejszego tutoriala.
> 

## Wymagania początkowe

- Posiadanie [hostingu](/links/web/hosting){.external} z dostępem SSH
- Dostęp do [Panelu klienta OVHcloud](/links/manager){.external}.

## W praktyce

Połącz się z hostingiem za pomocą SSH, korzystając z naszego przewodnika na temat [korzystanie z SSH przy pomocy hostingu www OVHcloud](/pages/web_cloud/web_hosting/ssh_on_webhosting).

Sprawdź, czy używasz kompatybilnej wersji PHP w wierszu poleceń:

```bash
php —version
```

Jeśli nie jest to prawidłowa wersja, możesz skonfigurować alias:

```bash
alias php='/usr/local/php8.0/bin/php'
```

Zalecamy pobyt w katalogu głównym Twojego hostingu, aby nie udostępniać publicznie plików "Composer". Następnie wprowadź następującą komendę:

```bash
curl -sS https://getcomposer.org/installer | php
```

"Composer" jest już dostępny na Twoim hostingu.

### Przykłady zastosowania

Jeśli chcesz zainstalować **Symfony 2**, możesz na przykład uruchomić następujące polecenie:

```bash
php composer.phar create-project symfony/framework-standard-edition my_project_name "2.7.*"
```

Możesz również korzystać z API OVHcloud z Twojego hostingu za pomocą oficjalnej werappera. W tym celu dodaj plik o nazwie *composer.json* zawierający listę zależności, których potrzebujesz. Oto przykład tego pliku za pomocą wrappera API OVHcloud:

```json
1. {
2.     "name": "Przykład Aplikacji",
3.     "opis": "This is an example of OVHcloud API wrapper use",
4.     "require": {
5.         "ovh/ovh": "1.1.*"
6.     }
7. }
```

Aby go zainstalować, wprowadź następującą komendę do tego samego katalogu:

```bash
php composer.phar install
```

Aby korzystać z tej biblioteki, zapoznaj się z dokumentacją oraz kodem dostępnym na stronie [GitHub](https://github.com/ovh/php-ovh){.external}

## Sprawdź również <a name="go-further"></a>

W przypadku wyspecjalizowanych usług (pozycjonowanie, rozwój, etc.) skontaktuj się z [partnerami OVHcloud](/links/partner).

Jeśli chcesz otrzymywać wsparcie w zakresie konfiguracji i użytkowania Twoich rozwiązań OVHcloud, zapoznaj się z naszymi [ofertami pomocy](/links/support).

Dołącz do [grona naszych użytkowników](/links/community).