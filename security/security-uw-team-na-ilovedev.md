# Security (UW Team na ILoveDev)

## Security

* SPF
* DKIM
* DMARC

> spf -all

Osobna subdomena do komunikacji mailowej

> dig cname \[domain] + short

Usuwaj zbędne domeny. Ukrywaj zbędne domeny.

Nie pozwalaj zakładać tych samych kont na wartości wcześniej usunięte.

## Https

* crt.sh
* Po certyfikacje da się wczytać subdomeny i np. w ten sposób dojść do aplikacji testowej, która zawiera pełną dokumentację API, bo developer jej nie schował
* Każda domena https jest publiczna!
* Ochrona
  * Alias Shield
  * AKAMAI / CloudFlare
  * NEUSTAR

### Cloudflare

* View DNS info - historia DNS
* Trzeba zmienić i nie dopuszczać historii IP bezpośredniej

Odetnij ruch z POSu twojego proxy

Cachuj co się da - jak się nie da, użyj microcacheingu&#x20;



Wyrzucaj content na zewnątrz

Wirtualnie oddzielaj pliki od danych

Request rozdzielić od contentu statycznego i dynamicznego.



{% embed url="https://mrugalski.pl/" %}
