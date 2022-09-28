# Łamanie reguł biznesowych

1. Obsługa wyjątków
   1. Ma wady np. stacktrace może być dostępny na produkcji
   2. Musi zostać wyłapany gdy wystąpi
2. Zwracanie rezultatu
   1. Np. osobny ValueObject do rezultatu
3. Try
   1. Albo to co miało być zwrócone, albo wyjątek
4. Either
   1. Zwraca prawą (właściwą) albo lewą (nie właściwą) stronę.
   2. [https://github.com/php-fp/php-fp-either](https://github.com/php-fp/php-fp-either)
