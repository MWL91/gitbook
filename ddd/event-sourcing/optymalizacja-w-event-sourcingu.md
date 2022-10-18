# Optymalizacja w Event Sourcingu

## Problemy z wydajnością

* Dużo zdarzeń per agregat
* Duże zdarzenia
* Dużo zapisów w ciągu krótkiego czasu
* Dużo zdarzeń w bazie

## Dużo zdarzeń per agregat

Przykładowe modele

* Polisa
* Koszyk
* Draft model
* Rachunek rozliczeniowy

### Snapshot techniczny

Utworzenie zdarzenia aplikującego złączony stan zdarzeń snapshotowanych, by zmniejszyć ilość sapshotów w bazie danych.

### Snapshot domenowy

Koniec miesiąca może automatycznie tworzyć snapshot, jeśli istnieje taka domena.

Może to być naturalny snapshot w naszych agregatach.

## Duże zdarzenia

* Dokumenty
* Formularze
* CMSy / CRMy

### Rozbijanie

* Task based UI
* Weryfikacja niezmienników
* Szukanie elementów składowych

### Operowanie na diff-ach

Zamiast snapshot po snapshocie - robimy diff, czyli która linijka została zmieniona.

## Dużo zapisów w ciągu krótkiego czasu

* Przetwarzanie transakcji giełdowych
* Import danych
* Internet of Things

Rozwiązaniem jest trzymanie agregatu w pamięci.

Model aktorów.

Cache zdarzeń + sticky-session.

Cache snapshotu + sticky-session.

## Dużo zdarzeń w bazie

* Co będzie za 5-10 lat?
* Mnóstwo małych operacji
* Wielu użytkowników

### Cold storage

Przeniesienie starych, nie używanych danych do bazy, w której zachowamy informacje, ale nie jest normalnie używana.

### Kompaktowanie

Usunięcie niepotrzebnych danych / spłaszczenie niepotrzebnych danych.



Na każdy problem istnieje sensowne rozwiązanie.

W wielu wypadkach snapshoty mogą w ogóle nie być potrzebne.
