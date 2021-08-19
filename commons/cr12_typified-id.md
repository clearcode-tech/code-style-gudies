## Common Rule 12: Типизированные ID



При извлечении типизированного ID из модели, использовать сокращённый вариант.

Правильный вариант:
```
ClientUserId clientUserId = ClientUserId.of(clientUser);
```

Неправильный вариант:
```
ClientUserId clientUserId = ClientUserId.of(clientUser.getId())
```

Совсем неправильный вариант:
```
ClientUserId clientUserId = ClientUserId.of(clientUser.getClientUserId())
```
<br>
Если из модели нужно извлечь типизированный ID одноимённого поля, то у модели следует имплементировать интерфейс типизированного ID (такие интерфейсы называются ModelWith + ModelName + Id).

Правильный вариант:

```
UserId userId = UserId.of(clientUser);
```

Неправильный вариант:
```
UserId userId = UserId.of(clientUser.getUserId())
```
