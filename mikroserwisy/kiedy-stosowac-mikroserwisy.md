# Kiedy stosować mikroserwisy

Mikroserwisy powinno się stosować gdy skala projektu jest zbyt duża, by została ogarnięta przez system monolityczny. Alternatywnie wtedy, gdy określona funkcjonalność musi się bezwzględnie cechować bardzo wysoką dostępnością.

## Przyczyny organizacyjne

### Skala zespołu i organizacja pracy

Jeśli zespół developerski jest na tyle duży, że nie da się go ogarnąć w systemie monolitycznym, mikroserwisy mogą być dobrym rozwiązaniem.

### Proces wytwarzania i względy bezpieczeństwa

Jeśli np. nasza aplikacja musi być prawnie certyfikowana, mikroserwis może być dobrym rozwiązaniem.

## Przyczyny techniczne

### Zasoby

Niektóre elementy w systemie mogą mieć bardzo duże potrzeby zasobowe (np. walidacja video).

### Odporność na błędy

Jeśli np. zabraknie nam zasobów w mikroserwisie, nie brakuje zasobów w pozostałej części aplikacji.

### Skalowanie

Łatwiejsze dopasowywanie charakterystyki skalowania do tego w jaki sposób będzie to używane.

### Dostępność

Łatwiejszy deployment, bo deployowany jest konkretny mikroserwis.

## Anty-przyczyny

* Najlepsza praktyka - to błędne podejście - to ma swoje wady i zalety
* Sposób na modularyzację - możemy zawsze stworzyć rozproszony monolit
* Częstsze wydania - ok, ale być może prostsze będą feature flagi

