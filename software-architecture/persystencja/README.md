# Persystencja

## Transakcyjność

* zgrupowanie odczytów i zapisów w nierozrywalną całość
* traktowana jako jedna operacja
* transakcja kończy się sukcesem (ang. commit)
* albo porażką (ang. rollback)

### ACID

* atomowość (ang. atomicity)
  * zapis uda się w całości - wszystko się zapisze, albo nic
* spójność (ang. consistency)&#x20;
  * nie są naruszone „niezmienniki”&#x20;
  * nie są naruszone zasady integralności&#x20;
  * dane są w poprawnym stanie
* izolacja (ang. isolation)&#x20;
  * izoluje współbieżne transakcje - zapewnia, że transakcje na siebie nie wpływają
* trwałość (ang. durability)
  * jeżeli był commit - dane zostaną zapisane
  * dane są na dysku
  * zazwyczaj za pomocą tzw. write-ahead log

