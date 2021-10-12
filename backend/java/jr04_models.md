## Java Rule 4: Создание модели данных

Создание модели с именем {{Name}} включает в себя следующие части:

- Класс и интерфейсы:
  - Класс: `business_logic/models/{{Name}}.java`.
  - Интерфейс для типизации ID: `business_logic/models/ids/{{Name}}Id.java`.
  - Интерфейс модели, которая содержит ID созданной модели: `business_logic/models/ids/ModelWith{{Name}}Id.java`.
  
- Миграция с созданием соответствующей таблицы в БД.

- Репозиторий:
  - Интерфейс: `business_logic/repositories/{{Name}}Repository.java`.
  - Реализация Ebean: `repositories_ebean/Ebean{{Name}}Repository.java`.
  - Binding: в специфичный для сервера файл `*EbeanRepositoriesModule.java` добавить строку биндинга интерфейса с релизацией Ebean.

- Сервис модели `business_logic/services/models/{{Name}}Service.java`.
