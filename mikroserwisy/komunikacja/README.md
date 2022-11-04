# Komunikacja

## Design for failure

Zawsze projektuj z myślą o tym, że coś się może nie udać. Nie ważne, jak bardzo dbamy o zabezpieczenia i stabilość systemu - każda dobra aplikacja powinna być projektowana pod potencjalny błąd.

> Dobra dekompozycja zmniejsza potrzebę integracji.

* Cache&#x20;
* Retry&#x20;
* Rate limiters&#x20;
* Fallback&#x20;
* Circuit breakers&#x20;
* Metrics
* Komunikacja asynchroniczna
* Testowanie (Chaos Monkey z wyłączaniem poszczególnych usług i sprawdzaniem jak działa system).

## Style komunikacji

* Fire & Forget
* Request - Response
* Request - Stream
* Channel
