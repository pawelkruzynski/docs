---
title: 'Transfer domeny Gandi do OVHcloud'
excerpt: 'Dowiedz się więcej o transferze domeny z systemu Gandi do OVHcloud'
updated: 2024-06-28
---

## Wprowadzenie

Transfer domeny Gandi wymaga zastosowania określonej procedury.

> [!warning]
>
> [rejestrator](/links/web/domains-what-is-registrar) domeny reprezentuje organizację/autoryzowanego dostawcę, w którym domena jest zarejestrowana/zarejestrowana przez osobę prywatną, stowarzyszenie lub organizację. To u tego samego rejestratora odnawiasz rejestrację domeny (zazwyczaj raz w roku).
>
> Jeśli OVHcloud jest już rejestratorem Twojej domeny **przed** rozpoczęciem odpowiedniej procedury, przychodzący transfer domeny nie jest właściwą procedurą. Procedura transferu domeny ma zastosowanie **tylko** do domen zarejestrowanych u innego operatora niż OVHcloud.
>
> Aby przenieść zarządzanie domeną na inne konto klienta OVHcloud, odpowiednią metodą jest **zmiana kontaktów**. Procedura opisana jest w [tym przewodniku](/pages/account_and_service_management/account_information/managing_contacts).
> Jeśli musisz również zmienić **właściciela** domeny, musisz zmienić **przed** zmianą kontaktów domeny. W tym celu postępuj zgodnie z instrukcjami zawartymi w przewodniku dotyczącym [zmiany właściciela domeny](/pages/web_cloud/domains/trade_domain).
>

**Dowiedz się, jak wykonać transfer domeny Gandi do OVHcloud**

> [!warning]
>
> Usługa Gandimail jest powiązana z Twoją domeną. Domena przestanie działać, gdy tylko zostanie przeniesiona poza Gandi. 
>
> Adresy e-mail powiązane z tą domeną zostaną definitywnie usunięte 7 dni później, **w tym wszystkie treści**.
>
> Dlatego ważne jest, abyś przed przeniesieniem domeny wykonał kopię zapasową ich treści.
>

## Wymagania początkowe

- Domena jest zarejestrowana u operatora Gandi.
- Domena istnieje od ponad 60 dni.
- W ciągu ostatnich 60 dni domena nie została przeniesiona ani nie zmienił właściciela.
- Nazwa domeny ma status "OK" lub "możliwy do przeniesienia".
- Nazwa domeny nie wygasła i ma datę wygaśnięcia umożliwiającą zakończenie procesu transferu w odpowiednim czasie (zalecane: ponad 60 dni).

Musisz również:

- Posiadanie możliwości odblokowania domeny.
- Posiadanie kodu transferu lub możliwość jego uzyskania.
- Posiadanie uprawnień do złożenia wniosku o transfer domeny.
- Właściciel i/lub administratorzy domeny zostali poinformowani o wszczęciu procedury transferu domeny.

> [!warning]
>
> OVHcloud udostępnia różnorodne usługi, jednak to Ty odpowiadasz za ich konfigurację i zarządzanie nimi. Ponosisz więc odpowiedzialność za ich prawidłowe funkcjonowanie.
>
> Oddajemy w Twoje ręce niniejszy przewodnik, którego celem jest pomoc w jak najbardziej optymalnym wykonywaniu bieżących zadań. Niemniej jednak w przypadku trudności zalecamy skontaktowanie się z [wyspecjalizowanym dostawcą](/links/partner) lub kontakt z aktualnym operatorem. Niestety firma OVH nie jest w stanie udzielić Ci wsparcia w tym zakresie. Więcej informacji znajduje się w sekcji [Sprawdź również](#go-further) niniejszego przewodnika.
>

## W praktyce

> [!primary]
>
> Aktywna strefa DNS domeny zawiera konfigurację DNS zastosowaną do Twojej domeny. Dzięki niemu możesz powiązać domenę z Twoimi usługami, takimi jak konta e-mail lub strona WWW.
>
> Jeśli oprócz nazwy domeny posiadasz również aktywną strefę DNS dla domeny u dotychczasowego operatora, sprawdź u jego służb, czy strefa DNS zastosowana do Twojej domeny nie zostanie usunięta po zakończeniu transferu.
>
> Rekordy usuwają strefę DNS obecną u nich w momencie zakończenia transferu Twojej domeny. W takim przypadku przed rozpoczęciem operacji związanych z transferem domeny utwórz ponownie strefę DNS w OVHcloud.
>
> Aby to zrobić, zapoznaj się z następującymi przewodnikami:
>
> - [Utwórz strefę DNS w OVHcloud](/pages/web_cloud/domains/dns_zone_create)
> - [Edycja strefy DNS OVHcloud](/pages/web_cloud/domains/dns_zone_edit)
>
> Upewnij się również, że dotychczasowy operator nie zamknie dodatkowych usług, takich jak na przykład adresy e-mail powiązane z Twoją domeną.
>
> Jeśli oprócz transferu Twojej domeny chcesz przenieść usługi z nią powiązane (strona WWW, konto e-mail, etc.), zapoznaj się z naszym przewodnikiem "[Przeniesienie strony WWW i powiązanych z nią usług do OVHcloud](/pages/web_cloud/web_hosting/hosting_migrating_to_ovh)".
> Ten przewodnik wyjaśnia, jak migrować wszystkie usługi bez przerw w ciągłości usług.
>
> Jeśli wykonujesz wyłącznie transfer Twojej domeny bez przenoszenia innych usług, upewnij się, że pobrałeś serwery DNS aktywne dla Twojej domeny od aktualnego **operatora** i wypełnisz ten przewodnik podczas etapu 3 "[Transfer domeny do OVHcloud](/pages/web_cloud/domains/transfer_incoming_generic_domain)"
> Dzięki temu nie będziesz musiał przerywać przypisywania domeny do przypisanych usług zewnętrznych.
>

## Etap 1 - Wyłącz blokadę transferu

> [!warning]
>
> Większość rozszerzeń zawiera funkcję blokady przed transferem, która jest dostępna w [Whois](/links/web/domains-whois) pod nazwą "transferProhibited".
>
> Ta blokada zapobiega przypadkowemu przeniesieniu domeny.
>
> Dopóki blokada jest aktywna, transfer nie jest możliwy.
>

Aby odblokować domenę w Gandi, postępuj zgodnie z instrukcjami zawartymi w [Dokumentacja dedykowana Gandi](https://docs.gandi.net/en/domain_names/transfer_out/transfer_lock.html){.external}.

### Etap 2 - Uzyskanie kodu autoryzacyjnego

Kod autoryzacyjny zabezpiecza nazwę domeny przed nieautoryzowanym transferem realizowanym przez osoby trzecie. Ten kod jest niezbędny, aby zezwolić na transfer domeny do nowego operatora.

Aby uzyskać kod transferu Twojej domeny, wykonaj kroki opisane w [dokumentacji Gandi](https://docs.gandi.net/en/domain_names/transfer_out/auth_info.html){.external}.

### Etap 3 - Rozpocznij transfer Twojej domeny do OVHcloud
  
Po uzyskaniu kodu autoryzacyjnego możesz przenieść domenę zgodnie z instrukcjami zawartymi w przewodniku "[Transfer domeny do OVHcloud](/pages/web_cloud/domains/transfer_incoming_generic_domain)".

> [!warning]
>
> W ciągu 24 godzin od rozpoczęcia transferu, Gandi wyśle Ci powiadomienie e-mailem o rezygnacji z domeny.
> W wiadomości tej można również umieścić link pozwalający na zaakceptowanie transferu w miejsce Gandi, co skróci czas rezerwowania.
> Okres rezerwowy to okres 5 dni (8 dni w przypadku domen zarządzanych przez AFNIC) pozwalający na anulowanie transferu.
> Po upływie tego terminu (5 dni "pełnych") transfer zostanie automatycznie zakończony.
>

## Sprawdź również <a name="go-further"></a>

[Przeniesienie strony WWW i kont e-mail do OVHcloud](/pages/web_cloud/web_hosting/hosting_migrating_to_ovh)

W przypadku wyspecjalizowanych usług (pozycjonowanie, rozwój, etc.) skontaktuj się z [partnerami OVHcloud](/links/partner).

Jeśli chcesz otrzymywać wsparcie w zakresie konfiguracji i użytkowania Twoich rozwiązań OVHcloud, zapoznaj się z naszymi [ofertami pomocy](/links/support).

Dołącz do [grona naszych użytkowników](/links/community).