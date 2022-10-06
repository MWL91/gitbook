# Coupling

Miara połączeń między poszczególnymi elementami.

### Rodzaje

1. Content Coupling - najmniej akceptowalny (bezpośrednie używanie szczegółów implemtacyjnych innego modułu).
2. Common Coupling - wspólny wzajemny składnik jest używany przez 2 inne moduły
3. External Coupling - komunikacja bazująca na tym, że określone moduły do komunikacji ze sobą potrzebują działania zewnętrznego narzędzia (np. API).
4. Control Coupling - jeden moduł mówi drugiemu jak ma przekazywać swoją pracę (np. przez przekazanie flagi)
5. Stamp Coupling - struktura z jednego modułu wykorzystuje tylko część z drugiego, a przekazywana jest cała struktura.
6. Data Coupling - najbardziej porządany - przekazujemy wszystko czego potrzemujemy i nic więcej.

### Tight vs. Loose

Mocny coupling - couplig do detali. Zmiana jednego modułu wpływa na inny moduł.

Luźny coupling - coupling do abstrakcji. Redukuje liczbę założeń która wymaga działania do wymiany między modułami.

### Explicite vs. Implicite

Może istnieć coupling niejawny - czyli np. coś zapisuje dane do bazy danych, a coś innego z tego czyta. Ta pierwsza aplikacja zmienia nagle format zapisu danych i rozwiązanie 2 przestaje działać.

### Semantic coupling

Polega na tym, że jeden moduł korzysta z konceptów innego modułu.

### Logical coupling

## Metryki couplingu

* Liczba połączeń
  * wejściowy vs. wyjściowy
* Niestabilność
  * wyjściowy / (wejściowy + wyjściowy)

<figure><img src="../../.gitbook/assets/Zrzut ekranu 2022-10-6 o 18.00.49.png" alt=""><figcaption></figcaption></figure>

## Drivery architektoniczne

### Usuwalność

1. Design for removability
2. Podejście wspierające
   1. minimalizację couplingu
   2. modularyzację
   3. minimalizację czasu na przepisanie modułu

## Prawo Demeter

* Dobra praktyka projektowania
* Zakłada brak wiedzy o detalach innych modułów / obiektów
* Wspiera loose coupling
* Możemy wywołać metody przekazanego obiektu
* Możemy wywołać metody obiektów które powstały w lokalnym obiekcie
* Nie możemy wywołać obiektu przez obiekt, który ma inny obiekt by coś zrobić (np. długa relacja Eloquenta nie jest ok).
* Nasz obiekt nie może wiedzieć więcej, niż powinien wiedzieć.

## Coupling na poziomie systemu

* Temporal - czas - mając dwie usługi muszą one być dostępne by móc się komunikować
* Spatial - muszę znać adres by z czymś się komunikować (topologia)
* Platform - serializacja klas do platformy

## Podsumowanie

1. Coupling powinien być jawny
2. Coupling jest nieunikniony
3. Loose coupling to droga do modularyzacji
4. Loose coupling to subiektywne określenie
5. Coupling w systemie ma różną naturę

## Narzędzia do mierzenia couplingu

{% embed url="https://www.sonarqube.org/" %}

{% embed url="https://github.com/qossmic/deptrac" %}

{% embed url="https://github.com/adamtornhill/code-maat" %}
