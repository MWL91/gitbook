# Service Discovery

Stosowany wtedy, gdy chcemy utworzyć wiele instancji do różnych usług, które mogą być otwierane i zamykane (autoskalowanie).

Pozwala usłudze pamiętać tylko nazwę usługi.

Można poprosić o wszystkie instancje, które aktualnie są dostępne.

W przypadku autoskalowania, powstająca usługa musi zarejestrować się w API:

* Serwis często podaje endpoint do healthcheck&#x20;

Serwisy pobierają adresy innych serwisów&#x20;

* Tych zarejestrowanych i dostępnych&#x20;
* Mogą trzymać te wartości w cache&#x20;

Dzięki cacheowi ServiceDiscovery nie jest single point of failure
