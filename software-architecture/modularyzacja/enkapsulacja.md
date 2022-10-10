# Enkapsulacja

Modularyzacja wymaga kontraktów. Może to być osiągnięte za pomocą enkapsulacji.

Koncepty poza obiektem nie powinny wiedzieć o tym, co znajduje się w danym obiekcie, poza tym, co jest w kontrakcie.

Droga myślenia dotyczy wszystkiego. Obiektów, modułów, mikroserwisów.

Brak kontraktu skutkuje brakiem modularyzacji.

Kontrakt nie musi skutkować modularyzacją.

### Enkapsulacja

* ukrywanie szczegółów jak vs co
* ukrywanie tego co zmienne

### Modularyzacja

1. Wypisz ważne decyzje związane z designem
2. Takie, które mają dużą szansę na zmianę
3. Projektuj moduły tak, aby te zmiany enkapsulować

### Częste "zapachy" enkapsulacji

* Niepełna abstrakcja
* Brak abstrakcji
* Cieknąca abstrakcja
* Niewykorzystana abstrakcja

Jako klient kodu - nie chcę wiedzieć jak działa środek. Ma działać, gdy wywołam to, co wywołuję!
