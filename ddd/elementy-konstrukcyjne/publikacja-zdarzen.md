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
5. Publikacja z wewnętrznej kolekcji - przykład na dole:&#x20;
   1. Użyta metoda pause.
   2. Serwis aplikacyjny pobiera agregat dzięki repozytorium
   3. Pauzuje operację w agregacie
   4. Pobiera zmiany (getChanges)
   5. Za pomocą event publishera publikuje te wydarzenia - dispatch
   6. Czyści wydarzenia z agregatu
   7. Zapisuje repozutorium

```
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
