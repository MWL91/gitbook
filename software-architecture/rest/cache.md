# Cache

## Kontrola cache w request - nagłówki:

* nagłówek odpowiedzi Expires
  * Określa ważność zasobu
  * Expires: Sun, 08 Apr 2019 18:03:53 GMT
* nagłówek Cache-Control
  * w jaki sposób możemy kontrolować cachowanie
  * public - zapis cache publicznie
  * private - wyłącznie przeglądarka usera
  * no-cache - brak cache
  * no-store - wyłącza możliwość przechowywania kopii
  * max-age - jak długo może być zapisana wiadomość cache
  * s-magage - jak długo może być zapisana wiadomość w cache publicznym
  * max-stale - maksymalny czas akceptowania wygasłej kopii
  * max-validate - walidacja dla cache
  * proxy-revalidate - walidacja dla cache publicznych
  * przykład: Cache-control: private, max-age: 3600

## Optymistyczne blokowanie

Nagłówek E-tag pozwala na optymistyczne blokowanie, za pomocą if-match.

{% embed url="https://developer.mozilla.org/en-US/docs/Web/HTTP/Headers/ETag" %}

W takiej sytuacji serwer odpowiada kodem 200, albo 412 gdy wersja edycyjna jest starsza.

