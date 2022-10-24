# Błędne założenia przy rozpraszaniu systemu

## Sieć nie jest niezawodna!

Sieć może przestać działać. Call do endpointu na zewnątrz, może nie zwrócić danych. Jakieś elementy mogą być czasowo niedostępne.

Należy obsługiwać ten problem! Należy to móc testować.

Nie można spinać ze sobą 2 systemów za pośrednictwem transakcji bazodanowej. Np. określone dane muszą być zaktualizowane później i oczekiwać na określone dane.

Minimalizuj liczbę połączeń między serwisami. Promuj autonomię.

## Opóźnienie nie wynosi zero

Zanim określona akcja się wydarzy, potrzebujemy poczekać na to, żeby określone elementy się wykonały.

Trzymaj dane bliżej klienta, używaj cache'a.

Nie doprowadzaj do sytuacji, w której musimy przejść przez kilkanaście serwisów, by wykonać określoną operację.

## Przepustowość nie jest nieskończona

## Sieć nie jest bezpieczna

Jeśli mamy mikroserwisy, dane się między poszczególnymi serwisami przemieszczają.

## Topologia sieci się zmienia

W kontekście chmury topologia sieci się zmienia! Adres IP może bardzo szybko się zmienić i nie chcemy mieć couplingu na tym. Można zastosować messenging, albo service discovery.

## Nie ma jednego administratora

Dobre logowanie, dobry monitoring, dobre CI/CD są elementami koniecznymi!

Zawsze przygotuj się do rollbacku do starej wersji.

## Koszt transportu nie wynosi zero

Serializacja i deserializacja danych może być droga.

## Sieć nie jest jednorodna

Czasem interfejs może być wystawiany do wielu urządzeń, więc należy stosować publiczne systemy połączeń.

Musimy utrzymywać określone połączenia między sobą.
