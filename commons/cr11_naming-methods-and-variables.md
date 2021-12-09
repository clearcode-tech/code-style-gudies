## Common Rule 11: Именование методов и переменных



1. Не дублируем контекст класса в названиях полей и методов.<br><br>

    Пример дублирования в enum:
    ```
        public enum EmailNotificationType {
    
            WELCOME_EMAIL_TYPE,
    
            INVITE_EMAIL_TYPE,
    
            RESET_PASSWORD_EMAIL_TYPE
        }
    ```

    Пример корректного наименования в enum:
    ```
        public enum EmailNotificationType {
    
            WELCOME,
    
            INVITE,
    
            RESET_PASSWORD
        }
    ```

    Пример дублирования в class:
    ```
         public class Document {
    
            private final documentId;
    
            private final documentNumber;
    
            private final documentType;
        }
    ```

    Пример корректного наименования в class:
    ```
         public class Document {
    
            private final id;
    
            private final number;
    
            private final type;
         }
    ```

<br>
2. Весь hardcode (значения String и примитивов взятые не из пропертей/конфигураций) выносим в константы.
