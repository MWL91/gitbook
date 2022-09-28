# Zachowania

Jeżeli nasze Encje są mutowalne (w przeciwieństwie to ValueObjectów), to należy umożliwić ich zmienianie poprzez wykonywanie określonych reguł biznesowych.

Unikamy getterów i setterów dla encji. Niezmienniki zapewniamy przez wystawienie ifów.

Dany kontekst ma określone zestawy warunkowe.

Gdy niezmienniki zależne są od cyklu życia, rozbijamy zachowania na mniejsze metody, albo w szczególnym wypadku na mniejsze klasy.

Jeśli znajdziemy klasę, która ma bardzo, bardzo dużo stanów (np. wymagało by to napisania 20 klas) należy rozbić taki problem na mniejsze klastry. Np. określone stany dokumentów oznaczające cięcia procesów.

W takiej sytuacji dobrze jest używać wzorców projektowych takich jak&#x20;

* Strategia
* Specyfikacja
* Polityka
* Memento
* Kolekcje

Porównywanie danych

* naturalny vs. wygenerowany klucz
* naturalny (np. ISBN jeśli to książka)
* wygenerowany ręcznie klucz
