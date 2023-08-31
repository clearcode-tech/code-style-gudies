## Common Rule 8: Пустые строки

1. Блоки кода с разной семантикой разделяются пустой строкой.
   ```       
    /**
     *  ...
     *
     * @return ...
     */
    public String someMethod(String another) {
        ...
   
        var person1 = this.call(...);
        var person2 = this.call(...);
        var person3 = this.call(...);
        var person4 = this.call(...);
       
        var document1 = this.call(...);
        var document2 = this.call(...);
        var document3 = this.call(...);
        var document4 = this.call(...);
   
        ...
    }
    ```
2. После однострочной сигнатуры метода всегда ставится пустая строка.
   ```
    /**
     * ...
     *
     * @return ...
     */
    public String someMethod(String another) {
        
        this.call();
        ...
    }
    ```
3. Перед блоком кода в if/else всегда ставится пустая строка.
    ```
    /**
     * ...
     *
     * @return ...
     */
    public void someMethod(String another) {
   
        if (condition1) {
   
            doSomething1();
        }
        else (condition2) {
   
            doSomething2();
        }
    }
    ```
4. Перед return всегда добавляется пустая строка.
    ```
    /**
     * ...
     *
     * @return ...
     */
    public String someMethod(String another) {
      
        String some2 = this.asdAsadasdasdAsdasdasdas(some1)
            .filter(...)
            .findAny()
            .orElseThrow();
        
        return another + some2;
    }
    ```
    ```
    /**
     * ...
     *
     * @return ...
     */
    public String someMethod(String another) {
          
        String some1 = ...;
        String some2 = ...;
       
        return some1 + some2;
    }
    ```
   Исключение: в методе есть одно однострочное объявление переменной, которая в следующей строке 
   используется в return.
    ```       
    /**
     * ...
     *
     * @return ...
     */
    public String someMethod(String another) {
        
        String some = this.service.doSomething(another);
        return another + some;
    }
   
   /**
     * ...
     *
     * @return ...
     */
    public String someMethod(String another) {
        
        try {
   
            String some = this.service.doSomething(another);
            return another + some;
        }
        catch (...) {
   
            ...
        }
    }
    ```
