## Common Rule 12: Типизированные ID



1. При извлечении типизированного ID из модели, использовать сокращённый вариант.
</br>Правильный вариант:
</br>
``
ClientUserId clientUserId = ClientUserId.of(clientUser);
``
</br>Неправильный вариант:
</br>
``
ClientUserId clientUserId = ClientUserId.of(clientUser.getId())
``
</br>Неправильный вариант:
</br>
``
ClientUserId clientUserId = ClientUserId.of(clientUser.getClientUserId())
``
</br>
</br>Если из модели нужно извлечь типизированный ID одноимённого поля, то у модели следует имплементировать интерфейс типизированного ID (такие интерфейсы называются ModelWith + ModelName + Id).
</br>Правильный вариант:
</br>
``
UserId userId = UserId.of(clientUser);
``
</br>Неправильный вариант:
</br>
``
UserId userId = UserId.of(clientUser.getUserId())
``
