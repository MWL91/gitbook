# Rozproszone Sagi

### Pocess manager

<figure><img src="../.gitbook/assets/Zrzut ekranu 2022-11-10 o 15.07.44.png" alt=""><figcaption><p>Jeśli coś przestanie działać w środku, to przestaje działać na dobre</p></figcaption></figure>

### Rozproszona Saga

<figure><img src="../.gitbook/assets/Zrzut ekranu 2022-11-10 o 15.09.09.png" alt=""><figcaption></figcaption></figure>

<figure><img src="../.gitbook/assets/Zrzut ekranu 2022-11-10 o 15.10.19.png" alt=""><figcaption><p>Saga która zadziałała poprawnie</p></figcaption></figure>

Saga w systemie orkiestracyjnym.

<figure><img src="../.gitbook/assets/Zrzut ekranu 2022-11-10 o 15.12.01.png" alt=""><figcaption></figcaption></figure>

## Różnice kompensacja rollback

W kompensacji tworzymy akcję "zwrócono 200zł" zamiast usuwać rekord w bazie danych.

Nasza saga powinna być idempotentna.

### Saga również może ulec awarii

Saga musi być idempotencja, bo jeśli saga ulegnie awarii, nie powinno stać się nic złego w procesie.

### Do sagi można użyć następujących narzędzi

* [https://aws.amazon.com/step-functions/](https://aws.amazon.com/step-functions/)
* [https://github.com/uber/cadence](https://github.com/uber/cadence)
* [https://conductor.netflix.com/](https://conductor.netflix.com/)
* [https://camunda.com/](https://camunda.com/)
* [https://masstransit-project.com/](https://masstransit-project.com/)
* [Narzędzie z phpersów](../software-architecture/orkiestracja.md)

## Saga - cechy

* Wszystko albo nic
* Kompensacja
* Idempotentność
* Użyj gotowych narzędzi
* Dwa razy się zastanów
  * Może nie musi być to robione synchronicznie
  * Być może mikroserwisy są zbyt małe
