# Podejścia do rozpraszania systemów

## Function as a service

Gdy potrzebny jest Edge Computing.&#x20;

* Lambda@Edge, CloudflareWorkers.&#x20;
* Dla sporadycznie używanych modułów.
* np. AWS lambda
* wąska odpowiedzialność - robią jedną rzecz
* są uruchamiane przez zdarzenia
* płacimy tylko za czas w których funkcja działa, a nie za czas w których funkcja jest uśpiona
* komunikacja asynchroniczna

## Nanoserwisy

Gdy mamy ogromny ruch i usługi o globalnym zakresie.

W normalnej skali może być to anti-pattern.

* małe serwisy
* sporo kaskadowych wywołań
* sporo komunikacji synchronicznej
* duży narzut infrastrukturalny

## Mikroserwisy

Większość systemów która wymaga rozproszenia. Brak ekstremalnej globalnej skali.

* Wielkość determinizowana przez domenę
* Autonomia
* Mało kaskadowych wywołań
* Sporo komunikacji asynchronicznej

## Bounded Context a system rozproszony

* Ziarnistość serwisów
* Ilość agregatów w kontekście

## Modularny monolit

* Możemy z nim zajść naprawdę daleko
* Głównym driverem jest skala - ruchu / zasobów / organizacji
* Serwisy mogą mieć różną wielkość w zależności od potrzeb
