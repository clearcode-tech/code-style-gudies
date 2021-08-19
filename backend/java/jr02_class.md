## Java Rule 2: Java классы



#### Общие правила для классов

1. Если класс может быть финализирован, то следует это сделать.

2. Используем аннотации lombok и javax для облегчения кода.

3. Не используем setter, чтобы не нарушать иммутабельность.


#### Правила для моделей (Entity)

1. Используем аннотации:
- lombok.AllArgsConstructor(access = AccessLevel.PRIVATE) -- без необходимости не расширяем видимость конструктора
- lombok.NoArgsConstructor(access = AccessLevel.PRIVATE, force = true) -- без необходимости не расширяем видимость конструктора
- lombok.Builder -- (или SuperBuilder если есть наследование)
- lombok.Getter
- lombok.EqualsAndHashCode(callSuper = true, onlyExplicitlyIncluded = true) --
- javax.persistence.Entity

2. Все модели (Entity) мы наследуем от BaseModel.

3. Для удобства работы с моделями - для всех полей класса делаем enum отображение:
```
public final class DocumentSigningRequest extends BaseModel {

    private final UUID documentSignerId;

    private final String state;

    public enum Fields implements ModelField<DocumentSigningRequest> {

        DOCUMENT_SIGNER_ID("documentSignerId"),

        STATE("state"),

        @Getter
        private final Field field;

        Fields(String name) {

            this.field = this.extractField(name, DocumentSigningRequest.class);
        }
    }
}
```
