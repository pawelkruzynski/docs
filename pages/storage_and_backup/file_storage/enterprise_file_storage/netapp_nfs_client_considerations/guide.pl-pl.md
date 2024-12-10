---
title: "Enterprise File Storage - Szczegóły dotyczące wybranych klientów NFS"
excerpt: "Specyficzne parametry, które należy sprawdzić i/lub wdrożyć w odniesieniu do oferty Enterprise File Storage"
updated: 2024-11-08
---

## Wprowadzenie

**Dowiedz się, jak zezwolić niektórym klientom NFS na dostęp do odczytu/zapisu w Twoim magazynie Enterprise File Storage.**

## Wymagania początkowe

- Wykupienie usługi [Enterprise File Storage](/links/storage/enterprise-file-storage)

## W praktyce

### Klientów NFS systemu Microsoft Windows

### Upewnij się, że użytkownik systemu Windows używany do uzyskania dostępu do Twojej usługi Entreprise File Storage ma wystarczające uprawnienia

Moment obrotowy UID/GID musi być skonfigurowany na 0 (prawo unix root).

Jeśli tak się nie stanie, wystąpią błędy dostępu do Twojej usługi Entreprise File Storage, ponieważ gdy NFS jest autoryzowany na maszynie z systemem Windows, użytkownik UNIX jest tworzony z domyślnym identyfikatorem UID i GID na -2 (lub 4294967294).

Aby uniknąć tej sytuacji, UID i GID mogą zostać wymuszone do 0 na maszynie z systemem Windows, która uzyskuje dostęp do Entreprise File Storage.

- Uruchom edytor rejestru na komputerze klienckim.
- Zlokalizuj `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\ClientForNFS\CurrentVersion\Default`.
- Utwórz dwie wartości DWORD: AnonymousUid i AnonymousGid.
- Ustaw te wartości na UID i GID na 0.
- Uruchom ponownie usługę NFS na maszynie klienckiej.

> [!primary]
>
> **Materiały referencyjne:**
>
> - <https://techcommunity.microsoft.com/t5/running-sap-applications-on-the/installation-configuration-of-windows-nfs-client-to-enable/ba-p/367084>
> - <https://learn.microsoft.com/en-gb/archive/blogs/msdn/sfu/can-i-set-up-user-name-mapping-in-windows-vista>
> - <https://learn.microsoft.com/en-us/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc753302(v=ws.10)?redirectedfrom=MSDN>
> - <https://kb.netapp.com/on-prem/ontap/da/NAS/NAS-KBs/Unable_to_perform_write_operations_on_an_export_mounted_on_a_Windows_machine>

#### Poproś o włączenie funkcji "showmount" w interfejsie wsparcia OVHcloud

Ze względów bezpieczeństwa opcja "showmount" umożliwiająca wyświetlanie dostępnych udziałów na serwerze NFS jest domyślnie wyłączona.
Jeśli jednak podczas niektórych operacji zapisu wystąpią błędy typu "invalid device error" lub jeśli korzystasz z aplikacji, która powinna używać tej funkcji, otwórz [zgłoszenie w dziale obsługi OVHcloud](https://help.ovhcloud.com/csm?id=csm_get_help), aby w wyjątkowych przypadkach je włączyć.

> [!primary]
>
> **Dokumentacja źródłowa:**
>
> - <https://learn.microsoft.com/en-us/windows-server/administration/windows-commands/showmount>

## Sprawdź również

Jeśli potrzebujesz szkolenia lub pomocy technicznej w celu wdrożenia naszych rozwiązań, skontaktuj się z przedstawicielem handlowym lub kliknij [ten link](/links/professional-services), aby uzyskać wycenę i poprosić o spersonalizowaną analizę projektu od naszych ekspertów z zespołu Professional Services.

Przyłącz się do [społeczności użytkowników](/links/community).
