# Client side load balancer



```
	Server side load balancing
		Single point of failure
		Niższa wydajność
			Wąskie gardło
			Dodatkowy element sieciowy
		Często wymaga manualnej aktualizacji
	Client side load balacing
		Cała praca wykonywana jest po stronie klienta
		Używamy Service Discovery
		Mniejszy koszt infrastrukuturalny
		Większa kontrola po stronie klienta
	Wady Client side load balacing
		Wymaga bilblioteki
		W teorii wszyscy mogą wybrać tą samą instancję
	Algorytmy wyboru instancji
		WeightedResposeTimeRule
			Czasy odpowiedzi instancji
		AvailabilityFilteringRule
			Liczba połączeń
		RoundRobinRule
			Kolejne zapytania do kolejnych instancji
```
