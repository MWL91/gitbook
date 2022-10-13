# Rozproszony konsensus

## Paxos

Mówi się, że rozumie go tylko kilka osób na świecie.

{% embed url="https://www.youtube.com/watch?v=SRsK-ZXTeZ0&ab_channel=DistributedSystemsCourse" %}

## Raft

Replication and Fault Tolerant - nastawiony na czytelność i pragmatyzm.

### Dekompozycja Raft

1. wybór lidera (leader election) - wybór jednego lidera i późniejsze reelekcje
2. replikacja logu (log replication) - lider aktualizuje log i replikuje go na pozostałe instancje&#x20;
3. bezpieczeństwo (safety) - raz zapisany indeks nie może być zmieniony na innej instancji

### Role w RAFT

każdy z serwerów w klastrze RAFT może mieć w danym momencie jedną z trzech ról:

1. lider (leader)&#x20;
2. stronnik (follower)&#x20;
3. kandydat (candidate)

### Kadencje (terms)

* czas działania jest podzielony na kadencje
* każda kadencja może mieć tylko jednego lidera
* niektóre kadencje nie mają liderów (nieudane wybory)
* każda instancja utrzymuje aktualną kadencję
  * wymieniana w każdej komendzie
  * dostajemy nowszą kadencję - wracamy do statusu follower
  * dostajemy starszą kadencję - zwracamy błąd

### Zdalnie wywoływane procedury (RPC)

Podstawowym budulcem RAFT są wywoływane przez lidera zdalne procedury.

<figure><img src="../../.gitbook/assets/Zrzut ekranu 2022-10-13 o 09.16.53.png" alt=""><figcaption><p>Wybory RAFT</p></figcaption></figure>

Mamy poszczególne klastry z czasem odpowiedzi. Jeśli czas odpowiedzi jest niski, to klaster prosi o głos na samego siebie. Jeśli klastry nie zdążyły odpowiedzieć, a dostały prośbę o głos, głosują na lidera.

### Replikacja logu

<div>

<figure><img src="../../.gitbook/assets/Zrzut ekranu 2022-10-13 o 09.20.41.png" alt=""><figcaption></figcaption></figure>

 

<figure><img src="../../.gitbook/assets/Zrzut ekranu 2022-10-13 o 09.20.51.png" alt=""><figcaption></figcaption></figure>

</div>

### Wady RAFT

* wymaga działania większości node'ów
* cały ruch przechodzi przez jednego lidera
* brak wsparcia dla problemu bizantyjskich generałów
