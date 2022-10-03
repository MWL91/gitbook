# Transport zdarzeń

## Domain event publisher

* Musi pomagać na wymienialność publishera
* Powinien mieć swój interfejs

## Just Forward Domain Event Publisher

* publish and handle inside same DB transaction
* podobne do statycznej klasy publikującej
* całość wykonuje się po wykonaniu wszystkich wydarzeń - czyli komenda z powodów biznesowych została zaakceptowana

<figure><img src="../../.gitbook/assets/Zrzut ekranu 2022-10-3 o 11.40.28.png" alt=""><figcaption></figcaption></figure>

### Efekty uboczne - wewnętrzne

* Rosnąca transakcja
  * Spada skalowalność
  * Spada user experience
* Implementacja gotowa na przetwarzanie asyncchroniczne

### Efekty uboczne - zewnętrzne

* Np. email może zostać wysłany - użytkownik wtedy oczekuje na wykonanie transakcji, która jeśli np. email nie działa, spowoduje błąd.

### Podsumowanie

* (+) Łatwe w implementacji
* (-) Niejawne efekty uboczne
* (-) Niejawne wiązanie

## Transport w następnych transakcjach

* Łatwa implementacja
* Brak wiązania
* Problem zawodności

### Rozwiązania efektów ubocznych

* Odwracanie kolejności w kodzie - najpierw transakcja, potem efekty uboczne.
* Callback jeśli mamy problem i coś do wycofania
* Transakcja listenera też może się wydarzyć - może nie jest to problem (np. jeśli raz nie dostanę maila, to nic się nie stanie).
* Jeśli następuje sytuacja w której Listener MUSI wykonać określoną operację zawsze, do bazy danych można zapisać całe wydarzenie, tak by mogło ono być wywołana przez listener w późniejszym czasie, w przypadku błędu.

<figure><img src="../../.gitbook/assets/Zrzut ekranu 2022-10-3 o 11.51.03.png" alt=""><figcaption><p>Przykład rozwiązania problemów z efektami ubocznymi</p></figcaption></figure>

## Store and forward - outbox pattern

Zapisanie wszystkiego albo niczego. Zapis zarówno zdarzenia, jak i obecnego stanu.

1. Pobierz wydarzenia
2. Opublikuj je
3. Oznacz jako wysłane

Jeśli wystąpi problem z bazą danych przy zapisie wydarzenia jako wysłane, może się ono wysłać ponownie.

```java
public class StoreAndForwardDomainEventPublisher implements DomainEventPublisher {
 private final JustForwardDomainEventPublisher simplePublisher;
 private final EventsStorage eventsStorage;
 public void publish(DomainEvent event) {
 //2.2 save in the same db in the same transaction (atomicity)
 eventsStorage.save(event);
 }
 //4. periodic publish
 public void publishAllPeriodically() {
 // 4.1 - fetch
 List<DomainEvent> domainEvents = eventsStorage.yetToPublish();
 // 4.2 - publish
 domainEvents.forEach(simplePublisher::publish);
 // 4.3 - mark as sent
 eventsStorage.markAsSent(domainEvents);
 }
}
```

<figure><img src="../../.gitbook/assets/Zrzut ekranu 2022-10-3 o 12.01.02.png" alt=""><figcaption></figcaption></figure>

### Podsumowanie

* (-) bardziej złożona implementacja
  * deduplikaccja
  * ponawianie
  * problem wielu instancji aplikacji
* (+) brak wiązania
* (+) gwarancja dostarczenia
  * niezawodność
