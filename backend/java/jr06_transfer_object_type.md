## Java Rule 6: Виды объектов для передачи данных между слоями

- DTO - для перемещения данных между серверами, а также между backend и UI.
Используется на всех уровнях. Размещается в _.../controllers_dto, если DTO не уходит глубже ControllerService, иначе в _.../business_logic/dto_.
- Cache - между Validator и ControllerService. Не может использоваться глубже ControllerService. Размещается в _.../business_logic/validations/caches_.
- Data - может быть частью Cache. Может использоваться в бизнес-логике.
Отличается от DTO тем, что не выходит за пределы сервера и в качестве полей может иметь сущность из БД.
- Details - для информации извлечённой в ходе какого-либо парсинга.
- Raw - для извлечения данных из БД. Используется в репозитории. Аннотируется @Entity и @Sql. Размещается в _.../business_logic/models_.
Например, `DocumentRegistryRawSqlCount`.
