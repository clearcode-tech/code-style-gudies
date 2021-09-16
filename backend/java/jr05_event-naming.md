## Java Rule 5: Именования для обработки событий


### Правила для именования, связанные с событиями Kafka

При составлении имени handler'a исходим из правила: {Что делаем}On{Какое событие}Handler. В некоторых случаях такое именование получается длинным, но главная цель - добиться уникального имени, т.к. при куче обработчиков одного и того же события должна отличаться часть {Что делаем}. При этом сама эта часть должна быть хоть и короткой, но достаточно понятной.
   
**Пример:**
Событие **{Что делаем}** - обработка успешного подписания документа (DocumentSigning), слушаем события **{Какое событие}** - успешное подписание файла (FileSigningSucceededEvent).

* Kafka **{Какое событие}** On **{Какое событие}** Handler -> `KafkaDocumentSigningOnFileSigningSucceededEventHandler`
* Kafka **{Какое событие}** On **{Какое событие}** Subscriber -> `KafkaDocumentSigningOnFileSigningSucceededEventSubscriber`
* Kafka **{Какое событие}** On **{Какое событие}** SubscriberProvider -> `KafkaDocumentSigningOnFileSigningSucceededEventSubscriberProvider`
* **{Какое событие}** On **{Какое событие}** SubscriberGroup -> `documentSigningOnFileSigningSucceededEventSubscriberGroup`


### Правила для именования, связанные с событиями WebSocket

1. Внутри пакета WebSocket не будет двух handler'ов одного и того же события, поэтому их можно просто именовать {Какое событие}Handler.

2. При формировании имени группы по правилу eventHandlerClassName.replace(“Handler”, ““) + “Group“ возникает проблема неуникальности в рамках всей системы, поэтому для веб-сокетов правило чуть дорабатывается до вида: eventHandlerClassName.replace(“Handler”, ““) + “WebSocketGroup“

Таким образом для WebSocket событий на примере события DocumentSigningRedirectEvent:

* **{Какое событие}** Handler -> `DocumentSigningRedirectEventHandler`
* Kafka **{Какое событие}** Subscriber -> `KafkaDocumentSigningRedirectEventSubscriber`
* Kafka **{Какое событие}** SubscriberProvider -> `KafkaDocumentSigningRedirectEventSubscriberProvider`
* **{Какое событие}** WebSocketSubscriberGroup -> `documentSigningRedirectEventWebSocketSubscriberGroup`
