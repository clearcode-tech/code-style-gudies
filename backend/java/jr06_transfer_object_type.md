## Java Rule 6: Виды объектов для передачи данных между слоями

- DTO - для перемещения данных между сервисами, а так же между backend-UI.
Используется на всех уровнях. Размещается в _.../controllers_dto_ если объект не уходит глубже ControllerService, иначе в _.../business_logic/dto_.
- Cache - между Validator и ControllerService. Не может использоваться глубже ControllerService. Размещается в _.../business_logic/validations/caches_.
- Data - может быть частью Cache. Может использоваться в бизнес-логике. Отличается от DTO тем, что в качестве полей может иметь @Entity.
- Raw - для извлечения данных из БД. Используется в репозитории. Аннотируется @Entity и @Sql. Размещается в _.../business_logic/models_.
