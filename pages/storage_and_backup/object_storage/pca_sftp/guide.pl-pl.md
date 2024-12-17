---
title: Cloud Archive Swift - Zarzadzaj swoimi archiwami za pomoca programu SFTP/SCP
excerpt: Przewodnik ten wyjasnia, jak zarzadzac usuga Public Cloud Archive.
updated: 2022-05-13
---

## Wstep
Object Storage to rozwiązanie do przechowywania danych zarządzane głównie przez API OpenStack.

Jeśli nie chcesz zarządzać przestrzenią dyskową z poziomu linii poleceń, skorzystaj z wdrożonego przez nas rozwiązania, dzięki któremu możesz połączyć się ze swoim kontenerem PCA za pomocą programu SFTP.

### Wymagania
- Program SFTP: [WinSCP](https://winscp.net/eng/download.php){.external}
- Login i hasło OpenStack
- TenantName projektu

## Program SFTP
W tym przewodniku korzystamy z programu WinSCP, ale możesz używać wybranego programu SFTP. Konfiguracja programów SFTP jest podobna.

## ID OpenStack
Login i hasło OpenStack możesz wygenerować postępując zgodnie z informacjami zawartymi w tym [przewodniku](/pages/public_cloud/compute/create_and_delete_a_user).

## TenantName
TenantName to nazwa Twojego projektu Horizon. Aby pobrać tę informację, należy zalogować się do interfejsu OpenStack: [https://horizon.cloud.ovh.net/](https://horizon.cloud.ovh.net/){.external}. Po zalogowaniu informacja ta będzie widoczna w górnej części strony.

![horizon](images/image1.png){.thumbnail}

## Logowanie
- Host Name: gateways.storage.<region>.cloud.ovh.net
- User Name: pca
- Password: <TenantName>.<Użytkownik_Openstack>.<Hasło_Openstack>

![connexion](images/image2.png){.thumbnail}

## Przykad
Jeśli utworzyłeś kontener PCA w SBG:

- Host Name: gateways.storage.sbg.cloud.ovh.net
- User Name: pca
- Password: 971891XXXX1214.f6nBXXXXXAmcv.SfPeASYfuWeqBZgXXXXX2XhF3DY12RkD

![connexion](images/image3.png){.thumbnail}

## Ustawienia WinSCP
W tej części wyłączymy dwie opcje w programie WinSCP:

**Transfer Resume / Transfer to Temporary Filename:** Ta opcja musi zostać wyłączona, ponieważ przywracanie nie jest możliwe w przypadku usługi PCA i WinSCP może zwrócić błąd.

- W sekcji "Endurance" wybierz "Disable".

![connexion](images/conf1.png){.thumbnail}

**Preserve Timestamp:** TimeStamp odnosi się do daty modyfikacji pliku. Wyłączamy tę opcję, ponieważ w PCA zastępujemy tę datę datą uploadu pliku.

- W sekcji "Transfer" kliknij na "Edit...".

![connexion](images/conf2.png){.thumbnail}

- Odznacz "Preserve timestamp".

![connexion](images/conf3.png){.thumbnail}

## Odzyskiwanie danych
Odyskiwanie danych wymaga odblokowania obiektu. Dla wybranego obiektu należy wykonać zapytanie GET. Jeśli polecenie to nie zostanie wcześniej wykonane, program SFTP zgłosi błąd podczas próby pobrania pliku. Zapoznaj się z naszym przewodnikiem dotyczącym odblokowania obiektu: [tutaj](/pages/storage_and_backup/object_storage/pca_unlock).

## Sprawdź również

Jeśli potrzebujesz szkolenia lub pomocy technicznej w celu wdrożenia naszych rozwiązań, skontaktuj się z przedstawicielem handlowym lub kliknij [ten link](/links/professional-services), aby uzyskać wycenę i poprosić o spersonalizowaną analizę projektu od naszych ekspertów z zespołu Professional Services.

Przyłącz się do społeczności naszych użytkowników na stronie <https://community.ovh.com/en/>.