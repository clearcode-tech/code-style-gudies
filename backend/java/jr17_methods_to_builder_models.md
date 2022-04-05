## Java Rule 17: Методы формирования моделей

1. В сервисах моделей использование `.toBuilder()` должно быть вынесено в модель, на котором вызывается `.toBuilder()`.
   Исключение - когда внутри одного класса в рамках многих разных методов формируется последовательно объект.
   т.е. когда метод разбит на много мелки.
2. Правила наименования
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
