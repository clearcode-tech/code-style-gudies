## Java Rule 17: Методы формирования моделей

1. Создание и обновление модели должно производиться методами самой модели. Стандартным способом является использование
`.builder()` и `.toBuilder()`. 
    
Исключения:
   1. Когда внутри одного класса в рамках многих разных методов формируется последовательно объект
      т.е. когда метод разбит на много мелких. 
   2. При сложном формировании модели для создания или обновления с использованием сторонних сервисов используется Mapper.
2. Примеры наименований:
- markAs...
- set...
- update...
- build...


  Названия методов должны быть бизнесовые, если им можно дать логичное бизнесовое имя. Необходимо выбирать названия так,
  чтобы при усложнении логики метода не было необходимости менять название метода.
Примеры:
```
    public Document buildNewSentToSigningDraft(String documentExternalId) {

        return this.toBuilder()
            .id(null)
            .sentDate(null)
            .externalId(documentExternalId)
            .build();
    }
```
````
    public Client setTenantId(TenantId tenantId) {

        return this.toBuilder()
            .tenantId(tenantId.getValue())
            .build();
    }
````
Если метод предполагает создание новой модели, то он должен находиться в static factories и называться build/of.
Пример:
````
//region Static factories

    public static NamedModelDTO of(NamedModel namedModel) {

        return NamedModelDTO.builder()
            .id(namedModel.getId())
            .name(namedModel.getName())
            .build();
    }

//endregion
````
