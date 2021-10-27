## Common Rule 2: Порядок полей класса



При перечислении полей класса, их порядок должен сохраняться. Это вносит определённый порядок, уменьшает хаос в коде.

#### В конструкторе

В случае с наследованием - первыми идут поля, которые объявлены в базовом/-ых классах, и в той последовательности, в которой они указаны в родительских классах.

Например, для Java это даже IDEA поддерживает. Добавили поле класса, нажали Alt + Enter на нём, и IDEA предложит добавить это поле как входной параметр конструктора. И если сделать эту операцию, то IDEA добавит параметр в конструктор согласно порядку полей при объявлении. 

Java:

```
public class OtherService {

    private final Client client;

    private final SomeService someService;
}

public class SomeService extends OtherService {

    private final DateParser dateParser;

    private final SomeExtractor someExtractor;

    /**
     * ...
     *
     * @param client ...
     * @param someService ...
     * @param dateParser ...
     * @param someExtractor ...
     */
    @Inject
    public SomeService(
        Client client,
        SomeService someService,
        DateParser dateParser,
        SomeExtractor someExtractor
    ) {
        super(client, someService);
        this.dateParser = dateParser;
        this.someExtractor = someExtractor;
    }
}
```

Typescript:

```
@Injectable({
    providedIn: "root"
})
public class SomeService {

    private readonly DateParser _dateParser;

    private readonly SomeExtractor _someExtractor;

    /**
     * ...
     *
     * @param dateParser ...
     * @param someExtractor ...
     */
    constructor(DateParser dateParser, SomeExtractor someExtractor) {
    
        this._dateParser = dateParser;
        this._someExtractor = someExtractor;
    }
}
```


#### В билдере

При использовании .boulder() и .toBuilder() мы сохраняем порядок полей класса.

```
public class M {

    private final String firstName;

    private final String lastName;

    private final int age;

    private final String company;
}

public class SomeService {

    public M create(
        String firstName,
        String lastName,
        int age,
        String company
    ) {
        this.someRepository.insert(
            M.builder()
                .firstName(firstName)
                .lastName(lastName)
                .age(age)
                .company(company)
                .build()
        );
    }

    public M update(M model, String lastName, String company) {

        this.someRepository.update(
            model.tobuilder()
                .lastName(lastName)
                .company(company)
                .build()
        );
    }
}
```


#### В сигнатуре метода

В сигнатуре метода также сохраняется первоначальный порядок полей одного класса.

```
public class M {

    private final String firstName;

    private final String lastName;

    private final int age;

    private final String company;
}

public class SomeService {

    public M update(
        M model,
        String firstName,
        String lastName,
        int age,
        String company
    ) {
        this.someRepository.update(
            model.tobuilder()
                .firstName(firstName)
                .lastName(lastName)
                .age(age)
                .company(company)
                .build()
        );
    }
}
```
