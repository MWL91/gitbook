# Read model

## Trudności

* Wyświetlanie danych z wielu agregatów na jednym widoku
* Raporty
* Wyszukiwanie
* Wprowadzanie zmian w widokach
* RODO

## Brak problemów gdy mamy jeden agregat

Jeśli mamy jeden agregat, nie pojawia się nam problemy, związane z wydajnością, gdy ilość eventów nie jest zbyt duża. Pozbywamy się modeli i persystencji ORMowej, zapis działa na dokumentach, więc działa stosunkowo szybko.

<figure><img src="../../.gitbook/assets/Zrzut ekranu 2022-10-14 o 14.34.51.png" alt=""><figcaption></figcaption></figure>

## Długo żyjący agregat

Nie dużo odczytu, ale dużo zapisu w różnych miejscach.

<figure><img src="../../.gitbook/assets/Zrzut ekranu 2022-10-14 o 14.37.53.png" alt=""><figcaption><p>Repozytorium zapisuje event, ale również model</p></figcaption></figure>

Może być to anti-pattern, jednak to co poświęcamy to latencja przy zapisie. Decyzja podjęta świadomie upraszcza nam sprawy związane z późniejszym odczytem.

## Duże obciążenie

Gdy odczyt jest naprawdę duży.

Sugeruje się wykorzystanie osobnej bazy danych i evetual cosistency.

<figure><img src="../../.gitbook/assets/Zrzut ekranu 2022-10-14 o 14.42.02.png" alt=""><figcaption></figcaption></figure>

## Potrzeba prezentacji wielu agregatów

### Composit UI.

Wiele zapytań o poszczególne agregaty.

<figure><img src="../../.gitbook/assets/Zrzut ekranu 2022-10-14 o 14.43.37.png" alt=""><figcaption></figcaption></figure>

To co można zrobić, to dodanie obsługi wielu zapytań requestowych zwracanych jako jedno API po stronie serwera na frontendzie.

* Monolityczny UI
* Mikrofrontendy

## Problemy związane z RODO

* Wrażliwe dane w jednym agregacie - odpowiedzialność za dane wrażliwe jest w osobnym miejscu które możemy usunąć
* Usuwanie strumienia - eventy są niemutowalne, ale strumień danych można już edytować

W przypadku wydarzeń publicznych:

* Dane są zreplikowane w wielu miejscach
* Każdy moduł odczytowy musi realizować prawo do zapomnienia
* Usuwanie strumienia

## Raporty i ich wyszukiwanie

W przypadku raportów mamy problem wydajnościowy.

W takiej sytuacji można stworzyć publiczny read-model.

<figure><img src="../../.gitbook/assets/Zrzut ekranu 2022-10-14 o 14.53.38.png" alt=""><figcaption></figcaption></figure>

## Zdarzenia publiczne i prywatne

Nie zawsze należy udostępniać wydarzenia do read-modelu.&#x20;

Np. jeśli mamy program do edycji tekstu, wydarzeniem prywatnym będzie edycja pogrubienia, kursywy czy dodania tekstu, ale wydarzeniem publicznym (dla read-modelu), będzie już jego modyfikacja.

### Zdarzenia publiczne

* Outbox
* Mogą być wzbogacane
* Globalna kolejność musi być istotna
* Mogą być przetwarzane w różnym tempie

## Spójność końcowa

* Ktoś inny zapisuje, ktoś inny odczytuje
* Przekazanie zlecenia

### Zachowanie spójności kocowej

* Czytanie własnych zapisów
  * Na bazie zwróconego sukcesu
  * Na bazie zwróconego zdarzenia
* Spowalnianie użytkownika
  * Strona z potwierdzeniem albo podsumowaniem
  * Wydłużenie przetwarzania komendy

## Podsumowanie

* Odczyt może być spójny, ale płacimy latencją
* Lokalne modele odczytowe + kompozytowy UI może rozwiązywać problemy
* Agregowane modele odczytowe i zdarzenia publiczne są rozwiązaniem, ale tylko wtedy gdy faktycznie mamy problem z dużą ilością danych. Nie powinny one jednak używać wewnętrznych wydarzeń, tylko swoich własnych - publicznych.

