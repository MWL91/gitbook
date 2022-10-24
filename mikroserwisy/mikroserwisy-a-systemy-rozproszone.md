# Mikroserwisy a systemy rozproszone

## Czym są mikroserwisy?

Szczególny przypadek systemu rozproszonego, nastawiony na zapewnienie autonomii.

### Rodzaje autonomii

1. Autonomia rozwoju - biznes musi samodzielnie decydować o zmianach, niezależnie od innych aplikacji.
2. Autonomia wdrożeń - chcę wdrażać wtedy, gdy potrzebuję wdrożenia, a nie wtedy gdy wdrażamy cały system.
3. Autonomia technologii - dobieramy narzędzie do danego problemu. Coś może być w Laravelu, a coś innego w Nest.

O wielkości mikroserwisu nie decyduje ilość lini kodu. Mikroserwisy nie są małe. Należy je zawsze dzielić per biznes, nigdy przez ilość kodu. Ilość linii na poziomie 50K nie są problemem.

Nie chcemy małych usług, bo rośnie nam zawodność systemu i temporal coupling.

Rośnie nam złożoność systemu.

### Mikroserwis jest produktem

Jest zorientowany biznesowo. Komponenty techniczne świetnie czują się jako biblioteki, co nie znaczy że musi być mikroserwisem.

### Kiedy robić serwis techniczny

* Skalowalność i zasoby
* Odporność
* Różne technologie
* Utrzymanie stanu
* Licencjonowanie, bezpieczeństwo, wymagania funkcjonalne itd.
