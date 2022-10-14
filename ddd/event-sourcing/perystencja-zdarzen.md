# Perystencja zdarzeń

## Zdarzenie persystentne

<pre class="language-java"><code class="lang-java"><strong>class PersistableEvent {
</strong>    private final UUID eventId;
    private final UUID aggregateId;
    private final UUID userId;
    private final UUID correlationId;
    private final UUID causationId;
    private final Integer version;
    private final String eventName;
    private final String eventData;
}</code></pre>

## Zdarzenie w EventStore

<pre class="language-java"><code class="lang-java"><strong>class EventData {
</strong>    private final UUID eventId;
    private final String eventType;
    private final Boolean isJson;
    private final byte[] data;
    private final byte[] metadata;
}</code></pre>

<figure><img src="../../.gitbook/assets/Zrzut ekranu 2022-10-14 o 14.07.40.png" alt=""><figcaption></figcaption></figure>

