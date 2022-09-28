# Zdarzenia

Zdarzenia co do zasady są to proste struktury.

Zawierają unikalny identyfikator.

Mogą mieć identyfikator przyczyny zdarzenia.

Mają identyfikator obiektu który wyemitował zdarzenie.

## Zdarzenia zewnętrzne

Publiczne. Integracyjne.

Są używane do komunikacji między Bounded Contextami.

Stają się częścią publicznego kontraktu.

Są wersjonowane.

## Zdarzenia wewnętrzne

Są używane do komunikacji wewnątrz Bounded Contextu.

Kompilator pilnuje kontraktu.

## Grupowanie zdarzeń

Zdarzenia mogą być pogrupowane w jedną klasę, np. zdarzenia z jednego bounded contextu lub jednego agregatu.

## Niemutowalność

Zdarzenia nie są mutowalne - nie są edytowalne w czasie.

