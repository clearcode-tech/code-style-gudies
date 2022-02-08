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

   - Stylelint package:
     `<project>/node_modules/stylelint`

   - Configuration file:
     `<project>/stylelint.config.js`

   - Run for files: 
     `{**/*,*}.{scss,html}` 

### Установка Stylelint в UI-проект

1. Установить `stylelint`:
    ```
    npm install --save-dev stylelint
    ```
    ```
    yarn add stylelint --dev
    ```
2. Установить `stylelint-order`:
    ```
    npm install --save-dev stylelint-order
    ```
    ```
    yarn add stylelint-order --dev
    ```
3. Установить `stylelint-config-property-sort-order-smacss`:
    ```
    npm install --save-dev stylelint-config-property-sort-order-smacss
    ```
    ```
    yarn add stylelint-config-property-sort-order-smacss --dev
    ```
4. Для получения начального файла конфигурации установить `stylelint-config-standard`:
    ```
    npm install --save-dev stylelint-config-standard
    ```
    ```
    yarn add stylelint-config-standard --dev
    ```
    Перенести файл конфигурации из `<project>/node_modules/stylelint-config-recommended/index.js` в `<project>/stylelint.config.js`. После этого `stylelint-config-standard` можно удалить:
    ```
    npm uninstall stylelint-config-standard
    ```
    ```
    yarn remove stylelint-config-standard
    ```
5. В файл конфигурации `stylelint.config.js` перед массивом `rules` добавить настройки:
    ```
    module.exports = {
        "plugins": [
            "stylelint-order"
         ],
        "extends": 'stylelint-config-property-sort-order-smacss',
        "rules": [
            ... Rules go here ...
        ]
    }
    ```
