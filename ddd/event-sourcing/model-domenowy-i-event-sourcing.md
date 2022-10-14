# Model domenowy i event sourcing

## Reprezentowanie zdarzeń w kodzie

* proste i niemutowalne struktury mają unikalny identykator
* mogą mieć identykator przyczyny
* zdarzenia mają identykator obiektu, który wygenerował obiekt

<figure><img src="../../.gitbook/assets/Zrzut ekranu 2022-10-14 o 12.43.56.png" alt=""><figcaption></figcaption></figure>

## Agregat

* Agregat otrzymuje strumień zdarzeń, następie wykonywana jest na nim określona akcja, powodująca publikację wydarzeń wewnątrz agregatu, by finalnie zapisać wywołane wydarzenia do następnego odtworzenia stanu.
* Agregat sprawdza niezmienniki.
* Komunikacja z agregatem możliwa jest tylko przez obiekt który jest korzeniem (aggregate root)

<figure><img src="../../.gitbook/assets/Zrzut ekranu 2022-10-14 o 12.49.08.png" alt=""><figcaption></figcaption></figure>

## Publikacja zdarzeń

Zdarzenie reprezentuje zmianę stanu.

* wewnętrzna kolekcja zdarzeń&#x20;
* zwracanie zdarzeń&#x20;
* statyczna klasa publikująca

## Elastyczna struktura modelu

* zmiana modelu bez zmiany schematu
* równoległe modele
* konieczność ręcznego mapowania

## Uproszczenie testów

* Given / When / Then
* Umożliwia to tworzenie zdarzeń i zachowywanie systemów jeśli określone eventy się wydarzą
* Wszystko staje się łatwiejsze dzięki komendom / eventom
