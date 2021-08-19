## Common Rule 11: Методы и переменные



1. Не дублируем контекст класса в названиях полей и методов.
</br>Пример дублирования в enum:
```
    public enum EmailNotificationType {

        WELCOME_EMAIL_TYPE,

        INVITE_EMAIL_TYPE,

        RESET_PASSWORD_EMAIL_TYPE
    }
```
</br>Пример корректного наименования в enum:
```
    public enum EmailNotificationType {

        WELCOME,

        INVITE,

        RESET_PASSWORD
    }
```

</br>Пример дублирования в class:
```
     public class Document {

        private final documentId;

        private final documentNumber;

        private final documentType;
    }
```
</br>Пример корректного наименования в class:
```
     public class Document {

        private final id;

        private final number;

        private final type;
     }
```

<br>
2. Весь hardcode (значения String и примитивов взятые не из пропертей/конфигураций) выносим в константы.
