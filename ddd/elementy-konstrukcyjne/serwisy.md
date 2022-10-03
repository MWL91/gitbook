# Serwisy

## Serwis domenowy

* Należy do warstwy domenowej
* Testowalny w izolacji i jednostkowo
* Bezstanowy

```java
class PauseSubscriptionDomainService {
 Result pause(Subscriber subscriber, IndividualSubsription subscription) {
 LoyalityPoints points = subscriber.currentPoints();
 if (points.qualifyToPremium()) {
 return subscription.pause(new CanAlwaysPausePolicy());
 }
 return subscription.pause(new StandardPausingPolicy());
 }
}

class PauseSubscriptionDomainServiceSpec extends Specification {
 PauseSubscriptionDomainService service = new PauseSubscriptionService()
 def 'premium subscriber can always pause subscription'() {
 given:
 IndividualSubscription sub = anIndividualSubscription(with10Pauses())
 and:
 Subscriber subscriber = withLoyalityPoints(enoughToBePremium())
 when:
 Result result = pauseSubscriptionService.pause(subscriber, sub)
 then:
 result.isSuccessful()
 }
}
```

Serwis dostaje obiekty domenowe i wykonuje część potrzebnej logiki.

W naszym przypadku sprawdzamy czy subskrubent ma odpowiednią liczbę punktów lojalnościowych i w zależności od tego jest inna specyfikacja pauzowania.

## Serwis aplikacyjny

* Nie zawiera logiki domenowej (koordynacja biznesu)
* Komunikuje się z zewnętrznymi systemami
* Zajmuje się logowaniem, transakcjami, autoryzacją, błędami
* Operacje typu bulk

```java
class PauseIndividualSubscriptionService {
 //...
 private final IndividualSubscriptionRepository subscriptionRepository;
 private final IndividualSubscriberRepository subscriberRepository;
 private final PauseSubscriptionDomainService pauseDomainService;
 //transakcja
 //logowanie
 //autoryzacja
 AppResult pause(SubsciptionId subscriptionId, SubscriberId subscriberIdr) {
 IndividualSubscription individualSubscription
 = subscriptionRepository.findBy(subscriptionId);
 Subscriber subscriber = subscriberRepository.findBy(subscriberId);
 Result result =
 pauseDomainService.pause(subscriber, individualSubscription);
 if (result.isSuccessful()) {
 repository.save(individualSubscription);
 }
 return transform(result);
 }
}
```

Ten serwis wyjmuje dane z bazy danych i zapisuje je w bazie. Przeprowadza więc operacje na warstwie aplikacyjnej.

##
