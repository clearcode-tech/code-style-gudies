## Java Rule 17: Методы формирования моделей

1. В сервисах моделей при создании и обновлении использование `.builder()` и `.toBuilder()` должно быть вынесено в модель, на котором вызывается `.builder()` и`.toBuilder()`.
   Исключения:
   1. Когда внутри одного класса в рамках многих разных методов формируется последовательно объект
      т.е. когда метод разбит на много мелких. 
   2. При сложном формировании модели для создания или обновления с использованием сторонних сервисов используется Mapper.
2. Правила наименования.
- markAs...
- set...
- update...
- build...


  Имена методов необходимо выбирать так, чтобы при усложнении логики метода не было необходимости менять наименование
  метода.

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
