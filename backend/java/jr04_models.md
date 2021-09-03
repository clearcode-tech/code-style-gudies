## Java Rule 4: Создание модели данных

Создание модели на бекенде включает в себя следующие части:

- Класс и интерфейсы:
  - Класс: `business_logic/models/{{Name}}.java`
  - Интерфейс для типизации ID: `business_logic/models/ids/{{Name}}Id.java`. Методы:
    - `static {{Name}}Id of(ModelWith{{Name}}Id model)`
    - `static {{Name}}Id of(UUID {{name}}Id)`
  - Интерфейс модели `business_logic/models/ids/ModelWith{{Name}}Id.java`. Методы:
    - `UUID get{{Name}}Id()`
  
- Миграция `Add_{{name}}_table.sql`
  - Primary key (пишется отдельно через CONSTRAINT)
  - Foreign keys
  - Индексы для foreign keys

- Репозиторий:
  - Интерфейс: `business_logic/repositories/{{Name}}Repository.java`
  - Реализация Ebean: `repositories_ebean/Ebean{{Name}}Repository.java`
  - Binding: в специфичный для сервера файл `*EbeanRepositoriesModule.java` добавить строку биндинга интерфейса с релизацией Ebean.

- Сервис модели `business_logic/services/models/{{Name}}Service.java`
