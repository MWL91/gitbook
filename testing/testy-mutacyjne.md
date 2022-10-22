# Testy mutacyjne

{% embed url="https://infection.github.io/" %}

Determinizm w testach.

Zapewnia działanie w każdych warunkach, dzięki czemu testy są dokładniejsze.

Pozwala ustawić losową wykonywalność testów

Dobre narzędzie do dokładnych testów, ale niekoniecznie do całej aplikacji na CI/CD.

## KPI

TotalDefetedMutants = KilledCount + TimeOutCount + ErrorCount

MSI = TotalDefetedMutants / TotalMutants

TotalCoveredMutants

## Wady

* Są kosztowne (ilość plików \* ilość mutantów)
* Najlepiej działa w feature testach
* Problemy z istniejącym już codebase
* Za dużo obiecują - za mało dają ;)&#x20;
