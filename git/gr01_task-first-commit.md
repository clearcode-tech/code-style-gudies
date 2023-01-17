## Git Rule: Первый коммит к задаче



Первый коммит к задаче должен включать в себя только изменение версии:

- в `build.sbt` и `conf/version`, если это Play проект
- в `pom.xml`, если это Maven проект
- в `version.ts`, если это Angular проект

Сообщение к коммиту должно быть в форме:

```
EN-XXX Версия задачи

{Название задачи в Jira}.
```

`EN-XXX` - номер задачи. Префикс зависит от проекта. Указано в Jira.

### Примеры версий
- Play проект: 
  - в `build.sbt` изменить `version := "2.5.1"` на `version := "2.5.1.HRL-270"`
- Maven проект:
  - в `pom.xml` изменить `<version>2.5.1</version>` на `<version>2.5.1.HRL-270-SNAPSHOT</version>`
- Angular проект:
  - в `version.ts` изменить `export const version = "2.7.0"` на `export const version = "2.7.0.HRL-270"`

