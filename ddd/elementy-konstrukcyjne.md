# Elementy konstrukcyjne

* Część wszechobecnego języka
* Określają strukturę modelu
  * Niezależność od technologii pozwala na łatwiejszą komunikację z biznesem.
* Komunikacja w zespole
  * Elementy konstrukcyjne umożliwiają na łatwiejszą komunikację z biznesem. Pozwalają podobnie jak developerom frontendu design pokazanie elementów biznesowi by szybciej dostać feedback.

## Zachowania

* Zdarzenia
* Komendy
* Zapytania (widoki)
* Reguły i agregaty
* Polityki

## Struktura

* Wartości
  * Byty nie zmieniające się w czasie (np. 2zł).
  * Opisują elementy encji.
* Encje
  * Byty zmieniające się w czasie&#x20;
  * Np. samochód. Może zostać pomalowany, może zostać zmieniony, ale nadal pozostaje tym samym samochodem z numerem VIN.
* Serwisy Domenowe
  * Operacje które nie są ani Encjami, ani Wartościami.
  * Np. Wygenerowanie numeru identyfikatora odcinka video. Ani nie jest to encja, ani nie jest to wartość.
  * Są bezstanowe. Służą do wyliczeń.
  * To nie jest serwis aplikacyjny.&#x20;

## Cykl życia&#x20;

* Fabryki
  * Tworzenie skomplikowanych struktur - jeśli proces tworzenia jest skomplikowany
* Repozytoria
  * Utrwalanie encji i VO oraz ich odczyt
