## Angular Rule 4: Порядок свойств CSS

Для определения порядка свойств мы пользуемся рекомендациями SMACSS (Scalable and Modular Architecture for CSS), которые устанавливают порядок категорий:
1. Box
2. Border
3. Background
4. Text
5. Other

Источник: http://smacss.com/book/formatting#grouping

Полный порядок свойств: https://github.com/cahamilton/css-property-sort-order-smacss/blob/master/index.js

Для поддержки этого правила в проекте должен быть настроен линтер, который подскажет, если порядок был нарушен.

### Использование Stylelint, установленного в UI-проекте

В IDEA открыть настройки: File | Settings | Languages & Frameworks | Style Sheets | Stylelint

   - Поставить галочку `Enable`

   - Задать настройки (могут отличаться в зависимости от версии IDEA)
     - Stylelint package: `<project>/node_modules/stylelint`
     - Configuration file: `<project>/stylelint.config.js`
     - Run for files: `{**/*,*}.{scss,html}` 

### Установка Stylelint в UI-проект

1. Установить `stylelint`:
    ```
    yarn add stylelint --dev
    ```
2. Установить `stylelint-order`:
    ```
    yarn add stylelint-order --dev
    ```
3. Установить `stylelint-config-property-sort-order-smacss`:
    ```
    yarn add stylelint-config-property-sort-order-smacss --dev
    ```
3. Установить `postcss-less`:
    ```
    yarn add postcss-less --dev
    ```
4. Создать файл конфигурации `stylelint.config.js`. Для генерации файла можно воспользоваться пакетом
   stylelint-config-standard. Перед массивом `rules` добавить настройки `plugins`, `extends` и `customSyntax`
   со следующим содержанием:
    ```
    module.exports = {
        "plugins": [
            "stylelint-order"
         ],
        "extends": "stylelint-config-property-sort-order-smacss",
        "customSyntax": "postcss-less", 
        "rules": [
            ... Rules go here ...
        ]
    }
    ```
