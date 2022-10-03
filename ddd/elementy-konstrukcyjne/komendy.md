# Komendy

W przypadku gdy w serwisie parametrów jest dużo i są one problematyczne do wyjaśnienia (np. czemu określony parametr w ogóle jest potrzebny), można takie parametry enkapsulować, a najlepiej robić to za pomocą komend.

Takie serwisy nie są już obsługiwane na zasadzie komend, tylko w takim wypadku mamy tzw. CommandHandlery.

Serwis aplikacyjny może rosnąć do nieskończoności - co może być błędem. W ten sposób mogą się urodzić bardzo kłopotliwe serwisy. CommandHandlery zamiast tego mają jedno konkretne zadanie do zrealizowania.

Command Bus - mediator między komendami wrzucanymi przez użytkowników a systemem który posiada command handlery.

Command handlery dają też większe możliwości działania - np. określony klient może mieć inne CommandHandlery jeśli zachodzi taka potrzeba. Można je również wersjonować. Kod jest otwarty na rozszerzenia, a zamknięty na modyfikacje.

Commandy dają nam możliwości wspierania architektury typu multi tennant. Jeśli jednak aplikacja jest prosta - np. jest zwykłym CRUDem, architektura 3 warstwowa staje się lepszym rozwiązaniem.
