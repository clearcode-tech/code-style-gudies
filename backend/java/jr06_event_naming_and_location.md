## Java Rule 6: Создание и расположение сущностей, связанных с обработкой событий


### Правила для именования, связанные с событиями Kafka

При составлении имени handler'a исходим из правила: {Что делаем}On{Какое событие}Handler. В некоторых случаях такое именование получается длинным, но главная цель - добиться уникального имени, т.к. при куче обработчиков одного и того же события должна отличаться часть {Что делаем}. При этом сама эта часть должна быть хоть и короткой, но достаточно понятной.
   
**Пример:**
**{Что делаем}** - выполняем подписание документа (DocumentSigning), **{Какое событие}** - успешное подписание файла (FileSigningSucceededEvent).

* Kafka **{Какое событие}** Publisher -> `KafkaDocumentSigningOnFileSigningSucceededEventPublisher`
* **{Что делаем}** On **{Какое событие}** Handler -> `DocumentSigningOnFileSigningSucceededEventHandler`
* Kafka **{Что делаем}** On **{Какое событие}** Subscriber -> `KafkaDocumentSigningOnFileSigningSucceededEventSubscriber`
* Kafka **{Что делаем}** On **{Какое событие}** SubscriberProvider -> `KafkaDocumentSigningOnFileSigningSucceededEventSubscriberProvider`
* **{Что делаем}** On **{Какое событие}** SubscriberGroup -> `documentSigningOnFileSigningSucceededEventSubscriberGroup`


### Правила для именования, связанные с событиями WebSocket

1. Внутри пакета WebSocket не будет двух handler'ов одного и того же события, поэтому их можно просто именовать {Какое событие}Handler.

2. При формировании имени группы по такому же правилу (**{Какое событие}** SubscriberGroup) возникает проблема неуникальности в рамках всей системы, поэтому для веб-сокетов правило дополняется до вида: **{Какое событие}** WebSocketEventSubscriberGroup.

Таким образом для WebSocket событий на примере события DocumentSigningRedirectEvent:

* **{Какое событие}** Payload -> `DocumentSigningRedirectEventPayload`
* **{Какое событие}** Handler -> `DocumentSigningRedirectEventHandler`
* Kafka **{Какое событие}** Subscriber -> `KafkaDocumentSigningRedirectEventSubscriber`
* Kafka **{Какое событие}** SubscriberProvider -> `KafkaDocumentSigningRedirectEventSubscriberProvider`
* **{Какое событие}** WebSocketEventSubscriberGroup -> `documentSigningRedirectWebSocketEventSubscriberGroup`

### Размещение

- event: Создаётся в commons. Место размещения _ru/ekd/commons/pubsub/events_.
- topic: Создаётся там же, где event. Место размещения _ru/ekd/commons/pubsub/topics_.
- publisher: Создаётся в том модуле, где будет производиться отправка события в топик. Если отправка события может понадобиться более, чем одному модулю, то _publisher_ располагается в commons. Место размещения для commons - _ru/ekd/commons/pubsub_kafka_, путь для monolith _.../pubsub_kafka/publishers_.
- handler: Создаётся в том модуле, где происходит приём события. Место размещения .../business_logic/pubsub.
- subscriber: Создаётся в том же модуле, где и обработчик. Место размещения _.../server-.../pubsub_kafka/subscribers_
- provider: Создаётся в том же модуле, где и подписчик. Место размещения вместе с подписчиком.

### Настройка publisher и provider

Для работоспособности требуется забиндить издателя и поставщика экземпляров подписчиков.
{server_name}KafkaPubSubModule размещается в _.../pubsub_kafka_.
В модуле есть 2 метода: `configurePublishers` для указания издателей и `configureSubscribers` для указания подписчиков, которые нужно подключить.
Пример подключения издателя: 
```
publishers.addBinding().to(KafkaSendNotificationOnDocumentPrintFormCreatedEventSubscriberProvider.class);
this.bind(new TypeLiteral<Publisher<DocumentPrintFormCreatedEvent>>() { }) .to(KafkaSendNotificationOnDocumentPrintFormCreatedEventSubscriberProvider.class);
```
