## Common Rule 13: Цепочки вызовов



1. Цепочка вызовов пишется по правилу - 1 вызов на 1 строчку.
    ```
    Optional<DocumentSigner> documentSigner = documentSigners.stream()
        .sorted(Comparator.comparing(DocumentSigner::getSigningOrder))
        .filter(Predicate.not(DocumentSigner::isMadeDecision))
        .findFirst();
    ```
   Исключением будет случай, когда цепочка состоит не более чем из 3 вызовов и умещается в одну строчку.
    ```
    Document document = documents.stream().filter(Document::isDraft).findFirst();
    ```
    ```
    Application updatedApplication = application.toBuilder().signedDate(Instant.now()).build();
    ```

2. Для первого многострочного выражения в цепочке вызовов, которое не уместилось в одну строку, действуют правила:
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
        .filter(Predicate.not(String::isEmpty))
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
