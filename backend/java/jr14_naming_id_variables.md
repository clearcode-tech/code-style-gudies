## Java Rule 14: Именование ID переменных

Если в рамках одного метода требуется ввести несколько переменных с ID одной и той же модели, но с разными типами
данных, то следует придерживаться правила именования:

 - `String` (ID в виде строки) -> someId+AsString
 - `UUID` (ID в виде UUID) -> someId+Value
 - `SomeId` (Типизированный ID) -> someId

Пример:

    ```
    public DocumentDTO someMethod(String documentIdAsString) {

        ...
        UUID documentIdValue = UUID.fromString(documentIdAsString);
        DocumentId documentId = DocumentId.of(documentIdValue);
        ...
    }
    ```

Если такая переменная одна, то просто `someId` для любого типа.
