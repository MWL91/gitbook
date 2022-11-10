# API prywatne i API publiczne

## Publiczne

* Udostępnione klientom nad którymi nie mamy kontroli.
* Każda zmiana niekompatybilna wstecz musi być wdrożona w nowej wersji API.
* Próbujemy zachować interoperacyjność różnych wersji

## Prywatne

* Udostępnione klientom nad którymi mamy kontrolę
* Jest jedna wersja - zawsze aktualna
* Stosujemy zmiany odroczone

### Zmiany odroczone

* ten sam mechanizm przy [wdrożeniach bez niedostępności](../mikroserwisy/wdrozenia-bez-niedostepnosci.md)
* wyznaczamy konkretne odstępy między niekompatybilnymi operacjami - na ogół minimum 2 sprinty
