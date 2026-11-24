# Greenilo — zmiana cen i edycja ofert

Greenilo to wewnętrzny panel do kontroli ofert sprzedażowych na Allegro. Łączy lokalną listę produktów i skaner cen konkurencji z oficjalnym Allegro REST API.

## Co robi program

- Importuje listę produktów z pliku `linki.txt` oraz wyniki analizy z arkuszy XLSX.
- Uruchamia skaner, który sprawdza ceny ofert konkurencyjnych dla produktów z listy.
- Pobiera przez Allegro API listę własnych ofert, ich ceny, dostępny stan oraz status publikacji.
- Pokazuje oferty aktywne, nieaktywne, w trakcie aktywacji, zakończone i takie, których nie znaleziono na koncie.
- Łączy rekord z Allegro po dokładnym numerze oferty (`offerId`), bez zgadywania na podstawie podobnego tytułu.
- Wyświetla rekomendację ceny na podstawie zaimportowanego wyniku analizy.
- Pozwala wysłać zmianę ceny pojedynczej oferty po sprawdzeniu i potwierdzeniu kwoty przez użytkownika.

## Jak działa integracja

Program korzysta z Allegro REST API oraz OAuth 2.0 Authorization Code z PKCE. Użytkownik loguje się na stronie Allegro i sam zatwierdza dostęp. Integracja wymaga uprawnień do odczytu oraz edycji ofert.

Panel pobiera dane ofert i ich status publikacji. Przy zmianie ceny wysyła do Allegro wyłącznie nowe pole ceny w wybranej ofercie. Nie zmienia ceny samoczynnie i nie obsługuje zamówień, płatności ani wiadomości.

Każde żądanie API zawiera identyfikator `User-Agent` wygenerowany w Allegro Developer Apps, aby Allegro mogło rozpoznać aplikację.

## Dane i bezpieczeństwo

Lista ofert, wyniki skanowania i ustawienia panelu są przechowywane lokalnie na komputerze użytkownika. Token OAuth jest chroniony mechanizmem Windows DPAPI dla bieżącego konta Windows. Dane logowania do Allegro są wprowadzane bezpośrednio na stronie Allegro; program nie zapisuje hasła do konta.

## Przeznaczenie

Program jest przeznaczony do własnego użytku sprzedawcy Greenilo w celu monitorowania własnych ofert i ręcznego zarządzania ich cenami na Allegro.

## Wsparcie

Program jest narzędziem wewnętrznym. W przypadku pytań dotyczących jego działania skontaktuj się z administratorem konta Greenilo.
