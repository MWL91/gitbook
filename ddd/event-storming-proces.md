# Event storming - proces

## Przygotowanie (przed event stormingiem)

1. Co jest w tej firmie core domain? Jaki jest wyróżnik biznesowy? Co trzeba zbudować.
2. Co jest domenami wspierającymi? Czyli tymi, które trzeba zrobić, ale nie są kluczowe.
3. Co jest domenami generycznymi? Co możemy kupić z zewnątrz?

### Kogo zaprosić?

Spotkanie prowadzi facilitator.

* Ekspertów domenowych
* Stake Holderów
* Modelarza
* Programistów

## Odkrywanie domen

1. Struktura organizacji
   1. Które domeny są ze sobą połączone i w jaki sposób?
2. Patrzenie na ekspertów domenowych
   1. Np. gdy obsługa klienta lokalnego jest inna niż zagranicznego
3. Język domenowy ekspertów
   1. Co oni mówią i jak oni mówią?
   2. Unikać duplikatów w języku - jeśli jest to coś innego, to należy to zawsze zaznaczyć. Utrzymywać definicję (nawet słowniczek).
4. Wartość biznesowa
   1. Core domain, czy tylko jedna, czy jest ich więcej?
5. Kroki procesu biznesowego
   1. Jak zmienia się proces biznesowy w czasie?
6. Jak z czasem zmieniają się Domeny i Subdomeny

## Przygotowanie big picture event storming

1. Przestrzeń - duża ściana
2. Ściana
3. Karteczki
4. Flamastry
5. Flipchart
6. Minutnik

### Faza 0: Rozpoczęcie spotkania

Przedstawienie celu spotkania&#x20;

### Faza 1: Chaotyczna eksploracja

* Event - pomarańczowa karteczka
* Wyłącznie istotne zdarzenia z punktu widzenie systemu, ale jednocześnie każda karteczka jest ważna, bo może otwierać dyskusję do elementu który normalnie byłby pominięty.
* Każdy uczestnik ma za zadanie napisać jakieś istotne zdarzenie i przykleić je na ścianę
* Zdarzenia w czasie przeszłym np. "Zamówienie zostało opłacone"
* Każdy pracuje osobo, by wyeliminować samca alfa
* Zakończenie gdy pierwsza osoba skończy

### Faza 2: Wprowadzenie osi czasu

* Wprowadzenie struktury
* Usunięcie duplikatów
* Pojawienie się niejasności

### Faza 3: Opowieść od końca

* Walidacja, czy to się udało?
* Jakich wydarzeń brakuje?
* Cognitive workload

### Faza 4: Ludzie i systemy

* Np. używamy dropboxa
* Np. Pan Mietek odpowiada za wysyłkę
* Systemem może być dział firmy
* Nie każdy event ma swojego aktora

### Faza 5: Problemy i okazje

* Zaznaczanie ważnych problemów czerwoną karteczką

## Definicja metryk biznesowych

## Process level event storming

### Połączenie event stormingu w określone procesy

* Na takim wydarzeniu może być już znacznie mniej osób, ale napewno powinni być ownerzy poszczególnych procesów, którzy ostatecznie decydują o kształcie aplikacji.
* Analiza części pierwszych polegająca a rozbiciu poszczególnych evetów na eventy z kontekstem.

#### Kolejność

1. Actor (żółta karteczka) - kupujący klient
2. Command (niebieska karteczka) - dodaj produkt do koszyka
3. System (różowa karteczka) - produkt musi być dostępny na stanie; ilość dodanych do koszyka produktów nie przekracza maksymalnej ilości zamówień na jedną osobę;
4. Event (pomarańczowa karteczka z Big Picture Event Storming) - produkt został dodany do koszyka
5. Policy (łososiowa karteczka) - zmniejsz stan dostępności o ilość produktów dodanych do koszyka
6. Widok (zielona karteczka) - wyświetl zamówienie w koszyku

### Następnie dodanie do nich bounded contextów.

* Pozwala wydzielić moduły w aplikacji - warto o nich myśleć jak osobnych, niezależnych od siebie elementów. Niezależnie od tego czy jest to montolit czy mikroserwisy, lepiej nawet działać w zakresie modułowego monolitu.

#### 7 taktyk porozumienia

Any organization that designs a system (defined broadly) will produce a design whose structure is a copy of the organization's communication structure.

1. Conformist - minimalizacja kosztów migracji np. integracja z FB z dużym couplingiem
2. Customer-supplier&#x20;
   1. jeden dostarcza, inny odbiera np. klient chce kupić od dostawcy
   2. Indywidualne kontrakty dla każdego klienta
3. Open host
   1. Customer-supplier, ale customerów są miliony
   2. Jeden wspólny kontrakt dla wszystkich
4. Published language
   1. Kontrakt jest delegowany na 3 stronę
   2. Częste wersjonowania API (po nagłówkach http - Accept)
5. Shared Kernel
   1. Powszechne użycie przez wszystkich
   2. Ownerem są wszyscy
   3. np. sposób kodowania danych
6. Anti Corruption Layer
   1. Przeciwieństwo shared kernela
   2. [https://learn.microsoft.com/pl-pl/azure/architecture/patterns/anti-corruption-layer](https://learn.microsoft.com/pl-pl/azure/architecture/patterns/anti-corruption-layer)
7. Separate ways

### Walidacja

* Czy wszystkie eventy faktycznie są potrzebne w systemie? Jaka jest ich rola? Czy należą do określonego bounded contextu?
