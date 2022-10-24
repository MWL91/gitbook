# Dostępność

## Proces określania dostępności

* Zebranie procesów biznesowych
* Określenie poziomu dostępności dla określonego procesu biznesowego
* Podział systemu na jednostki wdrożeniowe
* Mapowanie procesów na jednostki wdrożeniowe
* Rozrzucenie procesów na jednostki wdrożeniowe biorące w nich udział

## Przykład

* Zalogowany użytkownik dokonuje zakupu nowej subskrybcji
* Maksymalna niedostępność
  * chwilowo: 60s
  * dziennie: 5min

### Systemy w procesie:

* użytkownicy
* subskrypcje
* plany subskrypcji
* płatności

### Rozrzucenie

* użytkownicy 2s / 10s
* subskrypcje 5s / 30s
* plany subskrypcji 20s / 1m
* płatności 30s / 3m
