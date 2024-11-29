---
title: 'Transfer domeny GoDaddy do OVHcloud'
excerpt: 'Dowiedz się więcej o transferze domeny z systemu GoDaddy do OVHcloud'
updated: 2024-06-28
---

## Wprowadzenie

Transfer domeny GoDaddy wymaga zastosowania określonej procedury.

**Dowiedz się, jak wykonać transfer domeny GoDaddy do OVHcloud**

> [!warning]
>
> [rejestrator](/links/web/domains-what-is-registrar) domeny reprezentuje organizację/autoryzowanego dostawcę, w którym domena jest zarejestrowana/zarejestrowana przez osobę prywatną, stowarzyszenie lub organizację. To u tego samego rejestratora odnawiasz rejestrację domeny (zazwyczaj raz w roku).
>
> Jeśli OVHcloud jest już rejestratorem Twojej domeny **przed** rozpoczęciem odpowiedniej procedury, przychodzący transfer domeny nie jest właściwą procedurą. Procedura transferu domeny ma zastosowanie **tylko** do domen zarejestrowanych u innego operatora niż OVHcloud.
>
> Aby przenieść zarządzanie domeną na inne konto klienta OVHcloud, odpowiednią metodą jest **zmiana kontaktów**. Procedura opisana jest w [tym przewodniku](/pages/account_and_service_management/account_information/managing_contacts).
> Jeśli musisz również zmienić **właściciela** domeny, musisz zmienić **przed** zmianą kontaktów domeny. W tym celu postępuj zgodnie z instrukcjami zawartymi w przewodniku dotyczącym [zmiany właściciela domeny](/pages/web_cloud/domains/trade_domain).
>

## Wymagania początkowe

- Domena jest zarejestrowana u operatora GoDaddy.
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

### Etap 1 - Odblokowanie domeny w GoDaddy

Blokada domeny chroni ją przed nieautoryzowanym transferem.
GoDaddy włącza tę domyślną ochronę. Aby przenieść domenę do OVHcloud, musisz ją wyłączyć.

Postępuj zgodnie z instrukcjami zawartymi w [dokumentacji dedykowanej dla GoDaddy](https://pl.godaddy.com/help/odblokuj-lub-zablokuj-domene-410){.external}.

### Etap 2 - Uzyskanie kodu autoryzacyjnego 

Przed rozpoczęciem procedury transferu domeny OVHcloud poprosi o podanie kodu autoryzacyjnego lub "Auth code". Możesz go uzyskać, otwierając stronę Twojego portfolio `Domeny`{.action} w GoDaddy.

Postępuj zgodnie z instrukcjami zawartymi w [dokumentacji dedykowanej GoDaddy](https://pl.godaddy.com/help/przenoszenie-posiadanej-domeny-z-godaddy-3560){.external}.

### Etap 3 - Rozpocznij transfer domeny do OVHcloud

Po uzyskaniu kodu autoryzacyjnego możesz przenieść domenę zgodnie z instrukcjami zawartymi w przewodniku "[Transfer domeny do OVHcloud](/pages/web_cloud/domains/transfer_incoming_generic_domain)".

## Sprawdź również <a name="go-further"></a>

[Transfer domeny do OVHcloud](/pages/web_cloud/domains/transfer_incoming_generic_domain)

[Przeniesienie strony WWW i kont e-mail do OVHcloud](/pages/web_cloud/web_hosting/hosting_migrating_to_ovh)

W przypadku wyspecjalizowanych usług (pozycjonowanie, rozwój, etc.) skontaktuj się z [partnerami OVHcloud](/links/partner).

Jeśli chcesz otrzymywać wsparcie w zakresie konfiguracji i użytkowania Twoich rozwiązań OVHcloud, zapoznaj się z naszymi [ofertami pomocy](/links/support).

Dołącz do [grona naszych użytkowników](/links/community).