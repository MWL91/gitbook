# Komunikacja Fire & Forge

* Request-Reply -> Message driven
* Fire & Forget (One-Way) -> Event driven

## Kolejka

<figure><img src="../../.gitbook/assets/Zrzut ekranu 2022-11-4 o 14.12.22.png" alt=""><figcaption></figcaption></figure>

### Przykłady użycia

* równoległe przetwarzanie
* przetwarzanie w tle
* bufor

### Przykłady narzędzi

* Amazon SQS
* RabbitMQ (Direct Exchange)
* Google PubSub (Topic z jedną subskrypcją)
* Kafka (Topic z jedną grupą konsumentów)

## Publish Subscribe

<figure><img src="../../.gitbook/assets/Zrzut ekranu 2022-11-4 o 14.17.18.png" alt=""><figcaption></figcaption></figure>



### Przypadki użycia

* notykacja
  * innych serwisów
  * urządzeń klienckich

### Przykłady narzędzi

* Amazon SNS
* RabbitMQ (Fanout Exchange)
* Google PubSub (Topic z wieloma subskrypcjami)
* Kafka (Topic z wieloma konsumentami)

<figure><img src="../../.gitbook/assets/Zrzut ekranu 2022-11-4 o 14.19.39.png" alt=""><figcaption></figcaption></figure>

W przypadku wielu instancji, musimy wybrać lidera do publikacji.

### Semantyka dostarczania wiadomości

* at most once - najwyżej raz dojdzie, ale może nie dojść
  * Gdy chcemy mieć dużo danych
* at least once - przynajmniej raz - outbox pattern
  * Może będą duplikaty, ale będzie to dostarczone
* exactly once - system zachowuje się tak jakby wiadomość została dostarczona tylko raz
  * Mogą być jednak dostarczone wielokrotnie, ale potraktowane tak jakby były raz

### Przetwarzanie wiadomości

* deduplikacja - mogę sprawdzić po stronie klienta, czy wiadomość nie została już obsłużona
* idempotentność - mogę przejąć wiadomości 2 razy i zachować się tak samo

### Kolejność dostarczania wiadomości

<figure><img src="../../.gitbook/assets/Zrzut ekranu 2022-11-4 o 14.27.14.png" alt=""><figcaption></figcaption></figure>

## Problem poison messages

### po stronie producenta

* zaprzestanie wysyłania
* oznaczenie jako niepoprawne

### po stronie konsumenta

* dead letter queue
