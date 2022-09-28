# Value Object

1. Niemutowalność
2. Mogą sprawdzać niezmienniki domenowe - przy czym nie w konstrruktorze, a w czymś co będzie robić instancjonowanie
   1. Np. jakaś wartość może się zmienić w czasie i może nie być załadowana w czasie.
3. Mogą umożliwiać kolejność walidacji
   1. Np. mogą przetwarzać po kolei mniejsze porcje danych
4. Mogą mieć zachowania - jeśli te zachowania nie mają wartości ubocznych
5. Value objecty mogą być komponowane (pamiętać o niemutowalności)
6. Umożliwiają porównywanie się np. equals
