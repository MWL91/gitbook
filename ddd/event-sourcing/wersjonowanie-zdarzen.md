# Wersjonowanie zdarzeń

Zdarzenia są niemutowalne, ale mogą się zmieniać, zatem należy znaleźć rozwiązanie na wersjonowanie zdarzenia.

## Silny schemat

* ItemWasAdded\_v1,&#x20;
* ItemWasAdded\_v2

Struktura zapisana na poziomie typu.

Nie interesuje nas mechanizm serializacji.

#### Problemy ze skalowaniem (ilość wersji może być duża).

* Upcastowanie - każda nowa wersja zdarzenia może być zmapowana z poprzedniej wersji tego zdarzenia.
* Zawsze upcastuj do najnowszej wersji, ponieważ wydarzenie znajduje się na etapie repozytorium i jeśli określonych danych może brakować - może stać się koniecznym integracja / pobranie danych.

## Słaby schemat (weak schema)

* Informacje o strukturze są persystowane (JSON, XML)
* Wersjonowanie jest przezroczyste dla kodu domenowego
* Mapowanie zamiast serializacji

#### Mapowanie

| Pole jest w JSON | Pole jest w Object | Akcja            |
| ---------------- | ------------------ | ---------------- |
| TAK              | TAK                | Użyj JSONa       |
| TAK              | NIE                | Zignoruj         |
| NIE              | TAK                | Wartość domyślna |

## Zmiany - copy\&replace

Nie możemy usuwać naszych wydarzeń, ale możemy usuwać i modyfikować strumienie.

W takiej sytuacji należy istniejące modele zamienić na nowy strumień.

### Problemy

* Klienci nasłuchujący
* Wewnętrzne modele odczytu
* Zewnętrzne modele odczytu
* Audyt

## Zmiana semantyki

* Temperatura (np. zmiana z C na F)
* Waluta (np. z zł na €)
* Długość (np. z cm na m)

Należy zawsze zdefiniować szczegóły danych.

Nowe znaczenie = Nowe zdarzenie

## Potrzeba wersjonowania w praktyce

* Jak stabilna jest Twoja domena?
* Czy przeprowadzono dogłębny Event Storming?
* Jaka jest ziarnistość agregatów?
