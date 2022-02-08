## Java Rule 15: Мапперы

1. Код построения DTO и моделей (builder()...build()) должен располагаться внутри реализации интерфейса
Mapper<SomeEntity, SomeDTO> или Mapper2<SomeEntity, AnotherEntity, SomeDTO>.

2. Наименование реализации производить по правилу:
 - для моделей -> название класса + Mapper
`public final class DocumentMapper implements Mapper<CreatedDocumentDTO, Document>`
- для DTO, Data, Details -> название класса - суффикс (DTO, Data, Details) + Mapper
`public final class CreatedDocumentMapper implements Mapper<Document, CreatedDocumentDTO>`

3. Реализации размещать в директории .../business_logic/services/mappers.

4. В комментарии над классом нужно указать источник и результат маппинга:
`Сервис для преобразования {@link DocumentSentToSigningResult} в {@link SentToSigningDocumentDTO}`.

5. Мапперы можно переиспользовать в других мапперах через агрегацию.

Мапперы помогают убрать из менеджеров код, не имеющий отношение к бизнес-логике, но в сервисах допускается построение
моделей перед отправкой их в БД - в сервисах можно обойтись без маппера.
