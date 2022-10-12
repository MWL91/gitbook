# CAP, Base, Eventual Consistency

## CAP

* consistency - wszystkie klienty widzą ten sam stan danych
* availability - każdy klient może pisać/czytać
* partition tolerance - system funkcjonuje poprawnie mimo wystąpienia podziału sieci

<figure><img src="../../.gitbook/assets/Zrzut ekranu 2022-10-12 o 16.11.19.png" alt=""><figcaption></figcaption></figure>

* C+A => MySQL, Postgres
* A+P => Cassandra, CouchDB, Riak
* C+P => HBase, MongoDB, Redis

## Model transakcji BASE

* Basically Available - wysoka dostępność
* Soft state - wystarczająco świeże

## Eventual consistency - odroczone osiągnięcie spójności

* wybieramy dostępność kosztem spójności
* teoretyczna gwarancja, że zakładając brak modyfikacji zasobu, ostatecznie wszystkie odczyty będą zwracały najnowszą wartość
* N - liczba węzłów klastra
* W - węzły uczestniczące w zapisie
* R - węzły uczestniczące w odczycie

<figure><img src="../../.gitbook/assets/Zrzut ekranu 2022-10-12 o 16.17.09.png" alt=""><figcaption><p>Słaba spójność [N=3 W=1 R=1]</p></figcaption></figure>

<figure><img src="../../.gitbook/assets/Zrzut ekranu 2022-10-12 o 16.20.02.png" alt=""><figcaption><p>Silna spójność [N=3 W=2 R=2]</p></figcaption></figure>

### Dobór parametrów spójności

spójność:

* silna: W + R > N&#x20;
* słaba: W + R <= N

wydajność:

* odczytu: W >> R&#x20;
* zapisu: R >> W
