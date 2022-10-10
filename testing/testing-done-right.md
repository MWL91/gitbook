# Testing done right

## Znane problemy

1. Dużo mockowania
   1. Jeśli tego jest dużo - to znaczy że wszystko patrzy na wszystko i że jest to źle napisane.
   2. Sprawia to zabetonowanie struktury złego kodu
2. Wielolinijkowe testy
3. Mała zmiana wpływa na bardzo dużo testów
   1. Testy patrzą na rzeczy na które nie powinny patrzeć (np. testujemy za nisko)

## TDD

Zawsze najpierw na czerwono, potem kod byle jak, na zielono, a potem refaktoryzacja.

## Czym jest jednostka (unit)

* unit to niekoniecznie klasa
* unit to niekoniecznie metoda
* unitem może być logicznie powiązany ze sobą zestaw klas / funkcji

## Prawo Demeter

* Nie tworzyć głębokich powiązań (hello laravel relation!)
