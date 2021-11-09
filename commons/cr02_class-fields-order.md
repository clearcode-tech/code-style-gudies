## Common Rule 2: Порядок полей класса при объявлении и в конструкторе

### Поля в классе группировать по модификаторам доступа, а внутри групп - в алфавитном порядке.
Исключения — классы моделей и DTO.

IDEA поддерживает автоматическую сортировку полей классов. Настройка для Java:

1. Перейти в настройки `File | Settings | Editor | Code Style | Java | Arrangement`.
2. Убрать все галочки из `Grouping rules`.
3. Удалить из `Matching rules` все правила, не касающиеся `field`.
   Оставшиеся правила будут группировать поля по модификаторам доступа.
4. Для каждого оставшегося правила задать `Order: order by name`. Теперь поля в группе будут отсортированы по алфавиту.
5. Задать стандартные пустые строки после заголовка класса и вокруг полей: перейти в раздел `Blank lines` и в полях
   `After class header` и `Around field` вписать **1**.
6. Теперь, когда вам нужна пересортировка полей в классе, вы можете кликнуть `Code | Rearrange Code`, и поля в текущем 
   открытом файле будут отсортированы в соответствии с заданными правилами.


![Arrangement](../images/commons/02/idea_settings_for_field_sorting.png)


### При перечислении полей в классе, их порядок должен сохраняться и в конструкторе.

В случае наследования в перечислении в конструкторе первыми идут поля, которые объявлены в базовом/-ых классах.

IDEA поддерживает автоматическое добавление полей в конструктор для Java. После того как добавили поле класса, нажмите Alt + Enter на нём, и IDEA предложит добавить это поле как входной параметр конструктора. И если сделать эту операцию, то IDEA добавит параметр в конструктор согласно порядку полей при объявлении. 

Java:

```
@Singleton
public final class SomeService {
    //region Fields

    private final DateParser dateParser;

    private final SomeExtractor someExtractor;
    
    //endregion
    //region Ctor

    @Inject
    public SomeService(DateParser dateParser, SomeExtractor someExtractor) {
    
        this.dateParser = dateParser;
        this.someExtractor = someExtractor;
    }
    
    //endregion
}
```

Typescript:

```
@Injectable({
    providedIn: "root",
})
public class SomeService {
    //region Fields

    private readonly DateParser _dateParser;

    private readonly SomeExtractor _someExtractor;
    
    //endregion
    //region Ctor
    
    constructor(DateParser dateParser, SomeExtractor someExtractor) {
    
        this._dateParser = dateParser;
        this._someExtractor = someExtractor;
    }
    
    //endregion
}
```
