## Common Rule: Оформление if / else / switch



1. Всегда использовать скобки для блока кода { }. Даже если в блоке кода одна строка.

   ```
   if (condition) {
       
       doSomething();
   }
   ```

2. else и else if всегда переносятся на новую строку.

   ```
   if (condition1) {
   
       doSomething1();
   }
   else if (condition2) {
   
       doSomething2();
   }
   else {
   
       doSomething3();
   }
   ```

3. Если условие в одну строку, то после открывающей фигурной скобки { пустая строка.

   ```
   if (condition1) {
       -- пустая строка --
       doSomething1();
   }
   else if (condition2) {
       -- пустая строка --
       doSomething2();
   }
   else {
       -- пустая строка --
       doSomething3();
   }
   ```

4. Если условие более, чем в одну строку, то после открывающей фигурной скобки { пустой строки не нужно.

   ```
   if (
       condition1
       && condition2
   ) {
       doSomething1();
   }
   else if (
       condition3
       || condition4
   ) {
       doSomething2();
   }
   else {
       -- пустая строка --
       doSomething3();
   }
   ```

5. Оформление `switch`:
   ```
   switch (...) {

       case X:
           ...
           break;

       case Y:
           ...
           break; 
       ...

       default:
           ...
   }
   ```
