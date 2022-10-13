# Anomalie współbieżnego dostępu

* Read uncommitted zapobiega zapisowi dirty write
* Read committed zapobiega dirty write i dirty read - domyślne ustawienie dla np. Oracle 11g, PostgreSQL, SQL Server 2012

## Write skew

* warunek „maksymalnie 3 aktywne plany subskrypcji”&#x20;
* dwie transakcje w tym samym czasie sprawdzają stan
  * widzą dwa aktywne plany
* dwie transakcje dodają „trzeci” plan w rezultacie są 4 plany
