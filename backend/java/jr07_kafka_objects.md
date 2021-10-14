## Java Rule 7: Объекты Kafka

#### Наименование

- event: предназначения события + Event. Например, **DocumentPrintFormCreated**Event.
- topic: предназначения события + Event. Например, **DocumentPrintFormCreated**Topic.
- publisher: Kafka + полное название события + Publisher. Например, Kafka**DocumentPrintFormCreated**EventPublisher.
- handler: логика обработчика + On + полное название события + Handler. Например, SendNotificationOn**DocumentPrintFormCreated**EventHandler.
- subscriber: Kafka + полное название обработчика c заменой Handler на Subscriber. Например, KafkaSendNotificationOn**DocumentPrintFormCreated**EventSubscriber.
- provider: полное название подписчика + Provider.  Например, KafkaSendNotificationOn**DocumentPrintFormCreated**EventSubscriberProvider.


#### Размещение

- event: Создаётся в commons. Место размещения _ru/ekd/commons/pubsub/events_.
- topic: Создаётся там же где event. Место размещения _ru/ekd/commons/pubsub/topics_.
- publisher: Создаётся в том модуле, где будет производиться отправка события в топик. Место размещения для commons - _ru/ekd/commons/pubsub_kafka_, путь для monolith _.../pubsub_kafka/publishers_.
- handler: Создаётся в том модуле, где происходит приём события. Место размещения .../business_logic/pubsub.
- subscriber: Создаётся в том же модуле, где и обработчик. Место размещения ru/ekd/server_ekd/pubsub_kafka/subscribers
- provider: Создаётся в том же модуле, где и подписчик. Место размещение вместе с подписчиком.

#### Настройка publisher и provider

Для работоспособности требуется забиндить издателя и поставщика экземпляров подписчиков.
KafkaPubSubModule размещается в _.../pubsub_kafka_.
В модуле есть 2 метода configurePublishers и configureSubscribers для указания классов, которые нужно подключить.
Пример подключения издателя: `publishers.addBinding().to(KafkaSendNotificationOnDocumentPrintFormCreatedEventSubscriberProvider.class);`.