# Publikacja zdarzeń

## Agregat

<figure><img src="../../.gitbook/assets/Zrzut ekranu 2022-10-3 o 10.37.41.png" alt=""><figcaption></figcaption></figure>

1. Przyjmuje komendy (niebieska)
2. Sprawdza szereg założeń biznesowych (ciemna żółta -> normalnie różowa)
3. Zmienia stan (pomarańczowa)

To zadaniem agregatu jest wywołanie zdarzenia, a nie serwisu domenowego czy serwisu aplikacyjnego.

### Wewnętrzna kolekcja zdarzeń w agregacie

protected Raise - metoda pozwalająca na dodanie zdarzenia do wewnętrznej kolekcji agregatu.

public GetChanges - pobieranie stanu kolekcji, bez możliwości mutacji

public ClearChanges - pozwala na mutacje, ale tylko poprzez wyczyszczenie całej kolekcji

### Implementacja w agregacie

1. Metoda - komenda. Niebieska karteczka.
2. Następnie sprawdzenia (ify) - niezmienniki. Żółte karteczki (doc. różowe)
3. Ustawienie zmiany wewnątrz agregatu
4. Raise - wysłanie zdarzenia do wykonania

## Publikacja z wewnętrznej kolekcji

1. Użyta metoda pause.
2. Serwis aplikacyjny pobiera agregat dzięki repozytorium
3. Pauzuje operację w agregacie
4. Pobiera zmiany (getChanges)
5. Za pomocą domain event publishera publikuje te wydarzenia. Nie wiemy co zostanie wykorzystane, więc interfejs powinien być wspólny. To nie musi być event jak w Laravelu - to może być np. Kafka, albo jakiś inny serwis w zależności od potrzeb
6. Czyści wydarzenia z agregatu
7. Zapisuje repozutorium

```java
class PauseIndividualSubscriptionService {
 //...
 private final IndividualSubscriptionRepository repository;
 private final DomainEventPublisher eventPublisher;
 AppResult pause(SubscriptionId subscription) {
 //db transaction start
 IndividualSubscription individualSubscription =
 repository.findBy(subscription);
 individualSubscription.pause();
 List<DomainEvents> events = individualSubscription.getChanges();
 eventPublisher.publish(events);
 individualSubscription.clearChanges();
 repository.save(individualSubscription);
 //db transaction commit
 return success();
 }
}
```

## Zwracanie zdarzeń przez agregat

Alternatywnie można nauczyć agregat zwracania listy wydarzeń. Łamie to jednak CQS. Świadome złamanie nie jest jednak problemem, jeśli takie są problemy.

Nie potrzebujemy już tutaj metod opisanych w [wewnętrznej kolekcji zdarzeń w agregacie](publikacja-zdarzen.md#wewnetrzna-kolekcja-zdarzen-w-agregacie).

Może być to lista, ale może to być też Either. W takiej sytuacji nie potrzebujemy kolekcji.

Zasada działania zwracania przez agregat będzie bardo podobnie obsługiwana jak to co mamy w naszym wcześniejszym przykładzie, tylko zamiast metody getChanges mamy zwracane wydarzenia które możemy persystować.

Oba przypadki testowane są w podobny sposób.

```java
class PauseIndividualSubscriptionService {
 //...
 private final IndividualSubscriptionRepository repository;
 private final DomainEventPublisher eventPublisher;
 AppResult pause(SubscriptionId subscription) {
 //db transaction start
 IndividualSubscription individualSubscription
 = repository.findBy(subscription);
 List<DomainEvents> events = individualSubscription.pause();
 eventPublisher.publish(events);
 repository.save(individualSubscription);
 //db transaction commit
 return success();
 }
```

## Statyczna klasa publikująca

1. Działanie agregatu
2. Wrzucenie eventu
3. Poinformowanie listenerów

Tutaj mogą się pojawić problemy z tym, że należy zadbać o sagę. Jeśli coś się wyrzuci w między czasie, mogą pojawić się spore problemy.
