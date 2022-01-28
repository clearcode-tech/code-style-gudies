## Java Rule 14: Наименование ID переменных

Если в рамках одного метода потребуется ввести 2 или 3 ID переменные одной и той же модели, но разных типов данных,
то следует придерживаться правила наименования:

 - `String` -> someId+AsString
 - `UUID` -> someId+Value
 - `SomeId` -> someId

Если такая переменная одна, то просто `someId`

    ```
    public DocumentDTO someMethod(String documentIdAsString) {

        ...
        UUID documentIdValue = UUID.fromString(documentIdAsString);
        DocumentId documentId = DocumentId.of(documentIdValue);
        ...
    }
    ```
