# SLA / SLO / SLI

## Service Level Agreement

* Umowa z klientem dotycząca poziomu świadczenia usług
* Deklarujemy np. procent czasu, w którym w danym okresie usługa będzie dostępna
* Wprowadzamy refundację, albo kary umowne, za nie wywiązanie się z umowy

np. dostępność 99,95 tygodniowo

* 7 dni \* 24h \* 60min = 10080 min
* 10080 \* 99,95% = 10075 min
* Aplikacja może być niedostępna przez 5 minut w tygodniu

<figure><img src="../.gitbook/assets/Zrzut ekranu 2022-10-24 o 16.28.37.png" alt=""><figcaption></figcaption></figure>

Na wyższym poziomie dostępności, potrzebujemy automatów, które będą dbać o zapewnianie ciągłości usług.

np. 1500ms opóźnienia dla 99,9 percentyla dodania kursu.

np. maksymalnie 0.1% żądania zakończy się błędem

## Service Level Objective

* Wewnętrzny cel poziomu świadczenia usług
* Zapewnia bufor pomiędzy umową z klientem a momentem podjęcia akcji naprawy
* Mierzalne cechy / metryki danego systemu, takie jak dostępność, opóźnienia, przepustowość, poziom błędów etc.
* Wskaźniki mierzące zdrowie systemu

### Przykłady

* Miesięczna dostępność platformy
* Tygodniowa dostępność procesu biznesowego
* Procent żądań zakończonych sukcesem
* Czas odpowiedzi 99 percentyla żądań

## Kompletny przykład

* SLA: 99,9% żądań do serwera ma opóźnienie <200ms
* SLO: 99,95% żądań do serwera ma opóźnienie <180ms
* SLI: opóźnianie żądań do serwera

## Budżet błędów

* Error budget
* jeżeli mamy wyższą niezawodność niż planowana, możemy "wydać" różnicę
* jeżeli budżet topnieje, to np. wstrzymujemy wdrożenia -> ważniejsze jest to, żeby platforma działała zgodnie z SLA / SLO.

### Jak zacząć?

* Dla nowych aplikacji SLA / SLO powinno być częścią wymagań
* Dla istniejących systemów określamy je bazując na SLA
