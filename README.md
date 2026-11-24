# Allegro Panel Greenilo — panel sprzedaży i magazynu

Allegro Panel Greeniloo to lokalna aplikacja webowa w Pythonie i Flasku do obsługi ofert, produktów i procesów sprzedażowych na kilku platformach. Serwer działa na komputerze użytkownika, a panel otwiera się w przeglądarce pod adresem `http://localhost:5000`.

## Co robi program

- Prowadzi lokalny magazyn produktów i powiązanych ofert.
- Importuje i eksportuje dane z arkuszy Excel.
- Pomaga zarządzać ofertami oraz stanami na Allegro, Empik, OLX i Vinted.
- Obsługuje wybrane procesy związane z zamówieniami, sprzedażą, zwrotami i aktualizacją stanów.
- Udostępnia narzędzia do przygotowywania i publikowania treści na Facebooku.
- Przechowuje dane aplikacji w lokalnej bazie SQLite.

Zakres dostępnych działań zależy od platformy i skonfigurowanego konta.

## Integracje z platformami

Allegro i OLX łączą się z kontem przez ich mechanizmy autoryzacji. Empik korzysta z danych integracyjnych skonfigurowanych przez użytkownika. Funkcje Vinted używają automatyzacji przeglądarki Playwright; użytkownik loguje się samodzielnie w uruchomionym profilu przeglądarki. Poszczególne funkcje Facebooka wymagają podłączenia i ustawień konta użytkownika.

Program może odczytywać dane kont oraz wykonywać skonfigurowane operacje, takie jak aktualizacja oferty lub stanu. Przed podłączeniem kont zapoznaj się z zakresem uprawnień i zasadami danej platformy.

## API

Aplikacja ma wewnętrzne trasy API używane przez jej panel webowy. Wymagają zalogowania do MultiSales Pro. Nie jest to osobna, publiczna usługa API: domyślnie działa lokalnie pod `localhost:5000` i nie udostępnia oddzielnego uwierzytelniania kluczem API ani publicznej specyfikacji API.

## Dane i bezpieczeństwo

Baza SQLite, przesłane pliki, profile przeglądarki i ustawienia są przechowywane lokalnie. Dane dostępowe integracji, w tym tokeny OAuth, są zapisywane w bazie aplikacji. Chroń folder programu i wykonuj kopie zapasowe bazy. Nie publikuj bazy, plików sesji, kluczy ani danych kont w repozytorium.

Każda instalacja powinna używać własnego konta Allegro Panel Greenilo i własnych połączeń z platformami. Program nie zawiera wspólnych danych logowania do kont sprzedażowych.

## Instalacja w Windows

1. Zainstaluj Python 3.11 lub nowszy z Python Launcher (`py`).
2. Uruchom `instaluj.bat`. Skrypt tworzy środowisko `.venv`, instaluje zależności i pobiera Chromium dla Playwright.
3. Uruchom `uruchom.bat`.
4. Otwórz `http://localhost:5000` i utwórz własne konto. Przy pierwszym uruchomieniu konto tworzy się lokalnie na komputerze, na którym działa serwer.
5. Dodaj własne integracje w ustawieniach programu.

Pozostaw okno serwera otwarte podczas pracy. Aby go zatrzymać, naciśnij Ctrl+C w tym oknie.

## Przeznaczenie

Allegro Panel Greenilo jest narzędziem do lokalnej obsługi własnych procesów sprzedażowych. Nie zawiera gotowych danych kont marketplace ani publicznego hostingu. Korzystaj z integracji zgodnie z regulaminami i dokumentacją poszczególnych platform.
