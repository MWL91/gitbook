# Wybór bazy danych

{% embed url="https://db-engines.com/en/ranking" %}

### RDBMS

* Oracle&#x20;
* MySQL&#x20;
* Microsoft SQL&#x20;
* PostgreSQL&#x20;
* IBM Db2

### NoSQL

* Document - MongoDB&#x20;
* Key-Value - Redis&#x20;
* Wide-Column - Cassandra&#x20;
* Graph - Neo4J
* Timeseries - InuxDB

### NewSQL

* Spanner&#x20;
* CockroachDB&#x20;
* YugaByte&#x20;
* MemSQL&#x20;
* VoltDB

## Kryteria wyboru

### Dostępność w CAP

* poprawna odpowiedź
* zdrowy węzeł
* odpowiedź w skończonym czasie

### Wysoka dostępność (HA)

* uptime
* cały system
* odpowiedź w zadanym czasie

#### Wysoka dostępność - strategie

* master-slave (leader-follower)&#x20;
* multi-master (multi-leader)&#x20;
* hot-standby

<figure><img src="../../.gitbook/assets/Zrzut ekranu 2022-10-13 o 13.48.18.png" alt=""><figcaption><p>SQL vs NewSQL</p></figcaption></figure>

## Latencja vs model danych

### Relacyjne bazy danych

Model relacyjny jest uniwersalny ale:

* transakcje kosztują
* analiza i wykonanie zapytań kosztuje
* relacje kosztują

Jeśli to nam przestaje wystarczać (za mała latencja), albo zbyt duży ruch, należy szukać rozwiązania w baz No-sql.

### Key-value (Redis)

Szukanie tylko po kluczu:

* cache
* sesje
* liczniki (HyperLogLog)
* tablice wyników

### Wide column (Cassandra)

* szukanie po kluczu&#x20;
* proste zapytania po wartościach

### Dokumenty (MongoDB)

* nieustrukturyzowane dane
* modele hierarchiczne
* synchronizacja (Google Firestore)

### Grafy (Neo4j)

* rekomendacje&#x20;
* sieci społecznościowe&#x20;
* wykrywanie oszustw&#x20;
* role i uprawnienia

### Koszty operacyjne

* utrzymanie&#x20;
* konfiguracja
* infrastruktura

### Wielo-modelowe bazy danych

* CosmosDB&#x20;
* Yugabyte&#x20;
* FaunaDB&#x20;
* PostgreSQL&#x20;
* FoundationDB

## Podsumowanie

* z RDBMS jesteśmy w stanie zajść bardzo daleko&#x20;
* skalowanie przez modularyzację
* latencja jest kluczowa
  * spójność&#x20;
  * model danych
* koszty operacyjne
