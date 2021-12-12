## Common Rule 13: Цепочки вызовов



Для первого многострочного выражения в цепочке вызовов, которое не уместилось в одну строку, действуют правила:
- Аргументы первого выражения имеют дополнительный отступ (4 пробела).
- Закрывающая скобка первого выражения имеет дополнительный отступ (4 пробела) и находится на уровне следующего
выражения цепочки вызовов.

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
