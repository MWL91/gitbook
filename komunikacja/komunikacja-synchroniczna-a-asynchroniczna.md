# Komunikacja synchroniczna a asynchroniczna

## Request synchroniczny

* Blokujące IO
* kod wykonywany w kolejności pisania
* łatwy debug i monitoring
* wątek per żądanie

<figure><img src="../../.gitbook/assets/Zrzut ekranu 2022-11-4 o 13.58.01.png" alt=""><figcaption></figcaption></figure>

## Request asynchroniczny

* nieblokujące IO&#x20;
* potrzeba dodatkowych bibliotek&#x20;
* nieoczywisty kod&#x20;
* pętla zdarzeń (event loop)

<figure><img src="../../.gitbook/assets/Zrzut ekranu 2022-11-4 o 14.02.16.png" alt=""><figcaption></figcaption></figure>

## Wzorce obsługi żądań

* wątek per żądanie
* pętla zdarzeń (event loop)

### Podejście syncchroniczne - wady

* słaba utylizacja CPU&#x20;
* duże zużycie pamięci&#x20;
* context switch&#x20;
* ograniczona przepustowość

### Fibers

* lekkie wątki&#x20;
* zachowują kolejność wykonywania kodu&#x20;
* lepsza utylizacja zasobów niż wątki&#x20;
* włókno per żądanie

## Podejście strumieniowe

* strumienie danych&#x20;
* real-time&#x20;
* niższe zużycie pamięci&#x20;
* łatwa kompozycja wywołań (RX)

<figure><img src="../../.gitbook/assets/Zrzut ekranu 2022-11-4 o 14.06.42.png" alt=""><figcaption></figcaption></figure>
