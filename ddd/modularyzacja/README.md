# Modularyzacja

## Zmiany są nieuniknione

1. Wymagania
2. Technologie
3. Zespoły

### Należy umożliwić łatwe zmiany

1. Jasny zakres zmiany (jasno sprecyzowane miejsce do zmiany)
2. Zmiana nie wymaga kaskadowych zmian
3. Niska "lepkość" (low viscosity)

### Ewolucyjność

Możliwość dodawania i ciągłego zapewniania wprowadzania wybranych driverów architektonicznych.

## Modularyzacja

Moduł - grupa logicznie związanych ze sobą funkcji.

* Zawężają zakres zmiany
* Powodują że zmiany nie są propagowane

### Moduły a Bounded Context

Bounded Context: Przygotowywanie Video

Moduły: Validacja video. Konwersja video.

Bounded Context może mieć kilka modułów.

### Zalety modułów

1. Łatwiejsze zrozumienie (utrzymywalność)
2. Elastyczność, testowalność
3. Wymienialność, reużywalność
4. Zrównoleglenie prac

### Modularyzacja nie jest celem

Jeśli system nie musi być ewolucyjny (nie zmienia się), modularyzacja nie jest potrzebna. Jeśli ograniczeniem jest czas - nie można wprowadzić modularyzacji. Musi ona przyśpieszać pracę, a nie ją spowalniać.

Jeśli jednak planuje się zrobić system, który maiłby się zmieniać, modularyzacja bardzo ułatwia pracę. Jeśli miałby się zmieniać silnik bazodanowy - podział na moduły ma 100% sensu. Jeśli biznes będzie się zmieniał i zasady obsługi będą się zmieniać z czasem - warto jest wprowadzić modularyzację również na bazie biznesowej.

## Książki

{% embed url="https://www.amazon.com/Design-Patterns-Object-Oriented-Addison-Wesley-Professional-ebook/dp/B000SEIBB8" %}

{% embed url="https://www.amazon.com/Building-Evolutionary-Architectures-Support-Constant/dp/1491986360" %}

{% embed url="https://www.amazon.com/Structured-Design-Fundamentals-Discipline-Computer/dp/B000H39SJE/ref=sr_1_2?keywords=structured+design&qid=1568114933&s=books&sr=1-2" %}

