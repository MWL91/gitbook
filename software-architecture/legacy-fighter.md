# Legacy Fighter

## Zdrowe relacje z frameworkiem

Kod nie musi być angnostyczny od frameworka, ale powinien rozumieć jego zachowania i używać go z rozwagą. Jeśli np. korzysta się z architektury hexagonalnej, można widzieć framework, jako elementy na zewnątrz, tak by jego zmiana była potencjalnie możliwa.

Frameworki nie zawsze są najlepsze do komunikacji z bazą danych.

* Nadużywają joinów (np. eloquent zapewnia bardzo łatwy dostęp do danych, do których dostępu bezpośredniego nie powinno być, zgodnie z zasadą Demeter)
* Niedoużywają single-data - czasem dobrze mieć tabelę z read-modelem która się aktualizuje
* Denormalizują dane

Jeśli to możliwe, łącz dane ręcznie - bardziej świadomie. Trzymaj bogaty model danych.

Gdy mamy aplikacje inne dla innych ról, powinny one korzystać z bogatego modelu danych, który ma kontrakt, te dane dostarczający.

## Problemy biznesowe

Problemy biznesowe nie są widoczne w kodzie, ale są widoczne w organizacji.

Event / Command jest odpowiednim wzorcem dla obsługi eventów.

CRUD jest odpowiedni tam, gdzie jest CRUD, a nie wydarzenia.



{% embed url="https://www.youtube.com/watch?v=oA-DaJnCHUs" %}



{% embed url="https://www.youtube.com/watch?v=uj25PbkHb94" %}

{% embed url="https://microservices.io/patterns/data/transactional-outbox.html" %}

{% embed url="https://www.youtube.com/watch?v=GEjp_jOT2K4" %}

{% embed url="https://github.com/RailsEventStore/ecommerce" %}
