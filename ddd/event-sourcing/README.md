# Event sourcing

Przechowywanie informacji w zdarzeniach pozwala nam na nie gubienie informacji.

Np. użytkownik usunął produkt z koszyka pokaże nam jakąś aktualizację, ale nie pokaże tego, co się stało.

Event sourcing pozwala na:

* lepsze zapisywanie informacji
* polepszenie standardu obsługi
* analizę błędu na produkcji
* analizy biznesowe

## Zapis logów

Sam zapis logów pozwala na zapisanie wszelkich informacji, ale z drugiej strony jeśli mamy zapisane dane w innym miejscu, dane mogą się zdesynchronizować.

### Dwa źródła danych

* Replikacja&#x20;
* Integracja&#x20;
* Historia&#x20;
* Analiza

## Event sourcing

Zapewnia budowanie danych na podstawie wydarzeń, które wystąpiły w systemie.

* Brak utraty informacji&#x20;
* Audit trail&#x20;
* Obserwowalność&#x20;
* Analiza danych

<figure><img src="../../.gitbook/assets/Zrzut ekranu 2022-10-13 o 14.53.58.png" alt=""><figcaption></figcaption></figure>
