# Cohesion (Kohezja)

Miara tego jak poszczególne funkcje przynależą do danego modułu.

> **Kohezja** ([łac.](https://pl.wikipedia.org/wiki/%C5%81acina) _cohaere_ – nieodłączny) – ogólna nazwa zjawiska stawiania oporu przez ciała fizyczne, poddawane rozdzielaniu na części. Jej miarą jest [praca](https://pl.wikipedia.org/wiki/Praca\_\(fizyka\)) potrzebna do rozdzielenia określonego ciała na części, podzielona przez powierzchnię powstałą na skutek tego rozdzielenia.

Cel: rozbijanie oprogramowania na małe moduły.



* Miara dobrego pogrupowania elementów w moduły
* Wysoka kohezja wspomaga modularyzację
* Redukuje coupling pomiędzy modułami

## Typy kohezji

Od najmniej do najbardziej oczekiwanej

1. Coincidental - elementy wpadły do klasy przez przypadek
2. Logical - wiąże logiczne byty ze sobą, ale nie mają one ze sobą nic wspólnego
3. Temporal - w module mamy funkcje, które wykonują się w tym samym czasie
4. Procedural - operacje w module są w tej samej procedurze
5. Communicational - funkcje korzystają z tych samych struktur danych
6. Sequential - łańuch wywołań (np. przygotowanie kursu -> pipes and sink)
7. Functional - związane z funkcją (np. moduł kalkulatora zawiera wszystkie operacje wewnątrz danego modułu)

### Metryki

* Lack of Cohesion of Methods (LCOM).
* Brak Kohezji metod klasy

<figure><img src="../../.gitbook/assets/Zrzut ekranu 2022-10-7 o 09.21.42.png" alt=""><figcaption></figcaption></figure>

```java
class CompanySubscription {
 Enrollment enrollment;
 Instant expirationDate;
 Payments payments;
 void enroll(SubscriberId subscriberId) {
 enrollment.add(subscriberId);
 }
 void withdraw(SubscriberId subscriberId)) {
 enrollment.withdraw(subscriberId);
 }
 void renew(Instant till) {
 expirationDate = till;
 }
 void pay(Money amount) {
 payments.add(new Payment(amount));
 }
}
```
