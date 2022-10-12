# Wersjonowanie API

## Kiedy?

* Gdy złamiemy kompatybilność wsteczną
* Zmiana modelu biznesowego

## Reprezetacja

* Nie mieszać reprezentacji i zasobu w URLu.
* Pamiętaj o tym co wersjonujesz - czy encję, czy reprezentację
* Np. reprezentacja w wersji 2 jsona tego samego usera może odbywać się za pomocą nagłówka Accept, np:
  * Accept: application/v2+json
  * Accept: application/vnd.dna.v2.hal+json
  * Accept: application/json;version=2.3

### Wersjonowanie w URL

Użytkownicy rzadko przepinają się w całości na nowe api. Chcę mieć możliwość wykorzystania części API starego i części api nowego, jeśli jest taka potrzeba.

Wersjonowanie w URL ma sens, jeśli:

* zmieniamy całkowicie nasz model biznesowy
* zmienimy całkowicie metodę działania (np. nie java tylko php i inny serwer).
