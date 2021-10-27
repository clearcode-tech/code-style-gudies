## Common Rule 10: Цепочки вызовов с вложенными выражениями



Если после закрывающей скобки первого выражения, которое не уместилось в одну строчку, следует цепочка вызовов, то следует сделать дополнительный отступ (4 пробела) для закрывающей скобки и всех аргументов первого выражения. Добиваемся того, чтобы закрывающая скобка первого выражения находилась ровно над последующей цепочкой вызовов.

</br>Примеры корректного оформления цепочек вызовов:
```
String emailHtml = Arrays.stream(
        this.welcomeEmailTemplate.render(emailData.getVerificationLink())
            .body()
            .split(StringUtils.LF)
    )
    .filter((String line) -> !line.isEmpty())
    .collect(Collectors.joining(StringUtils.LF));
```
```
String emailHtml = Arrays.stream(
        this.rejectedImmediateEmailTemplate.render(
                emailData.getPersonName(),
                emailData.getLegalEntity(),
                emailData.getRejectionComment(),
                emailData.getLink()
            )
            .body()
            .split(StringUtils.LF)
    )
    .filter(Predicate.not(String::isEmpty))
    .collect(Collectors.joining(StringUtils.LF));
```
```
String subject = this.i18nServiceSupplier.get(Lang.RU)
    .at("emails.rejectedDaily.subject", emailData.getPersonName())
    .orElse(null);
```
