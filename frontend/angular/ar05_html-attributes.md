## Angular Rule 5: Html атрибуты

1. Порядок расположения атрибутов в теге:
- Структурные директивы: `ngIf`, `ngFor`, `*ngSwitch`.
- Класс: `class="..."`.
- Mat-атрибуты: `mat-button`, `mat-menu-item` и т.п.
- Общие атрибуты html: `id`, `appearance`, и т.п.
- Атрибуты angular: `[label]`, `[formGroup]`, `[searchable]`, `[multiple]` и другие input компоненты.
- Обработчики событий: `(click)`, `(change)`, `(hide)` и другие output компоненты.

Пример написания длинных class:
```
<div 
    [class.very-long-class-name1]="true"
    [class.very-long-class-name2]="true"
>
</div>
```
