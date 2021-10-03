# Budowanie systemów o wysokiej dostępności

## Po co?

Zawsze przed decyzją, o tym jaki poziom dostępności klient powinien mieć w swoim projekcie, powinna decydować albo cena albo dostępność. Zależność ta wynika z tego, że wysoka dostępność wymaga na ogół bardziej skomplikowanej infrastruktury.

Łatwiej jest założyć, że mamy stronę o dostępności 99,5% oraz bazę danych o dostępności 99,5% co daje 99,0% i zaaceptować takie rozwiązanie, niż dokładać 3 load balancery, 3 aplikacje www i 3 bazy danych które się automatycznie klonują, bo taka infrastruktura choć będzie mieć większą dostępność, będzie o wiele droższa.

## Zasady budowania aplikacji o wysokiej dostępności

1. N+1 design / N+2 design. Zawsze dostaw jednego developera więcej, zawsze dostaw jedną maszynę więcej, zawsze posiadaj zapas +1
2. Design for rollback - projektuj tak, by dało się zmianę wycofać
3. Design to be disabled - projektuj tak, by określony feature dało się wyłączyć bez wpływu na resztę systemu
4. Design to be monitored - sprawdzaj i monitoruj zmiany
5. Design for multiple livesites - projektuj tak, by możliwe było kierowanie ruchu z np. określonego kontynentu na określoną instancję, nie zawsze taką samą
6. Use mature technologies - być może nowości są fajne, ale używaj technologii która działa, by mieć pewność, że będzie działać w przyszłości
7. Asynchroius design - projektuj tak, by aplikacja działała asynchronicznie
8. Stateless system - jak się da, spraw by system był bezstanowy
9. Scale out not up - dostaw maszyę, nie zwiększaj obecnej maszyny \(software design\)
10. Buy when non-core - kupuj technologie zewnętrzne, jeśli nie są one twoim core biznesowym \(slack, jira, itd.\)
11. Use commodity hardware - fajnie używać najnowszych kart graficznych, ale używaj takich technologii które są szeroko dostępne, by nie było z tym problemu
12. Build small, Release small, Fail fast
13. Isolate faults - gdy coś robisz i nie wiesz czy to zadziała, zrób to tylko na jednej instancji
14. Automatition over pepole - automatyzuj rzeczy tak, by możliwe było ograniczanie developerów i zawodności człowieka

