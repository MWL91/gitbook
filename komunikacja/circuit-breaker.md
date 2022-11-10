# Circuit breaker

## Jeśli zewnętrzny serwer zawodzi, to:

* Nie powinniśmy długo czekać na błędną odpowiedź
* Przy ciągłych problemach lepiej od razu przestać ten serwer odpytywać

## Metryki

* W takiej sytuacji należy określić metryki
* Procent nieudanych połączeń X w oknie czasowym Y
* Przekroczenie zdefiniowanego progu błędów (Z): odcięcie następnych połączeń
* W przeciwnym wypadku kontynuacja



* Obwód zamknięty - możemy rozmawiać z naszym klientem.
* Obwód otwarty - nie możemy rozmawiać z naszym klientem.

<figure><img src="../.gitbook/assets/Zrzut ekranu 2022-11-10 o 15.58.17.png" alt=""><figcaption></figcaption></figure>

<figure><img src="../.gitbook/assets/Zrzut ekranu 2022-11-10 o 16.00.34.png" alt=""><figcaption></figcaption></figure>

## Przykłady

* Resilience4j
* Polly
* [ganesha](https://ackintosh.github.io/ganesha/)

## Kiedy nie ma to sensu

* Kiedy połączeń między serwisami jest mało
  * Zbieranie statystyk trwa zbyt długo
  * Włączenie / wyłączenie obwodu będzie rzadkie
