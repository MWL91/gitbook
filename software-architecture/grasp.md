# GRASP

## Odpowiedzialność

### Wykonywania

* akcji
* tworzenia nowych obiektów
* koordynacji

### Wiedzy

* o swoich danych
* o innych obiektach, danych które obiekt może policzyć itd.

## Controller pattern

* Wejściowy obiekt operacji biznesowej (np. serwis aplikacyjny). Start obsługi akcji biznesowej.
* Pierwszy obiekt pod warstwą UI
* Np. serwis pobierający dane z repozytorium i delegujące je do agregatu gdzie dzieją się rzeczy

## Creator pattern

* Kto może tworzyć obiekty?
* Obiekty X tworzą obiekty Y jeżeli:
  * X agreguje Y
  * X ściśle używa Y
  * X ma wszystkie dane do stworzenia Y

## Indirection pattern (nie bezpośredniość)

Aplikacja nie musi wiedzieć w którą stronę przebiega bezpośrednie flow aplikacji.

<figure><img src="../.gitbook/assets/Zrzut ekranu 2022-10-10 o 17.18.34.png" alt=""><figcaption></figcaption></figure>

W przykładzie występuje moduł przygotowania, który umożliwia działanie całej aplikacji, ale poszczególne metody o sobie nie wiedzą. Tutaj można użyć architektury typu mikro-jądro.

#### Związane wzorce projektowe

* adapter
* mediator
* fasada
* bridge

## Information Expert ( Ekspert informacji)

Klasa eksperta dostaje najwięcej informacji, bo jej się to należy.

Przydziel odpowiedzialność obiektowi który ma najwięcej danych potrzebnych do wypełnienia zadania.

## High Cohesion + Low Coupling

## Polimorfizm

* Dla różniących się zachowań, użyj polimorfizmu
* Klient abstrakcji nie używa if-else
* Klient nie sprawdza konkretnej implementacji

## Chroniona zmienność

* Ulotna logika musi być chroniona
* Ukrywamy zmienne rzeczy
* Enkapsulacja
* Np. lista odcinków musi być ukryta pod klasą kursu, bo zasady mogą się zmienić wewnątrz

## Pure fabrications

np. repozytorium

* Sztuczny obiekt&#x20;
* Zwiększa kohezję
* Zmniejsza coupling
* np. Serwis domenowy

## Pragmatyzm

Zawsze rób tak, żeby to miało sens ;)



{% embed url="https://en.wikipedia.org/wiki/GRASP_(object-oriented_design)" %}

{% embed url="https://patrykwozinski.medium.com/grasp-dd7ac5384371" %}

{% embed url="http://kurs.aspnetmvc.pl/Wzorce/Zasady_GRASP" %}

