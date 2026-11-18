# AWS Secrets Manager

**Категорія:** Security, Identity, and Compliance  
**Призначення:** Безпечне зберігання, отримання та ротація application
secrets.

## Словник термінів

| Термін                   | Визначення українською                                                                                     |
|--------------------------|------------------------------------------------------------------------------------------------------------|
| **Secret**               | Об’єкт Secrets Manager із конфіденційним значенням, metadata та версіями.                                  |
| **Secret Value**         | Фактичне секретне значення: пароль БД, API key або credentials JSON.                                       |
| **Secret ARN**           | Amazon Resource Name, який однозначно ідентифікує secret.                                                  |
| **KMS Encryption**       | Шифрування secret value за допомогою AWS KMS key.                                                          |
| **Rotation**             | Процес регулярної заміни секретного значення або оновлення key material для зниження ризику компрометації. |
| **Rotation Lambda**      | Lambda function, яку Secrets Manager викликає для автоматичної зміни secret у цільовій системі.            |
| **Staging Labels**       | Мітки Secrets Manager, що вказують на версії secret, наприклад AWSCURRENT, AWSPREVIOUS та AWSPENDING.      |
| **AWSCURRENT**           | Staging label для актуальної версії secret, яку має використовувати застосунок.                            |
| **AWSPREVIOUS**          | Staging label, що зазвичай позначає попередню версію secret.                                               |
| **AWSPENDING**           | Staging label для нової версії secret під час процесу rotation.                                            |
| **Version**              | Незмінна версія secret value; staging labels вказують на відповідні версії.                                |
| **GetSecretValue**       | API, що повертає secret value та metadata для авторизованого principal.                                    |
| **Resource Policy**      | Policy на secret, яка визначає principals/accounts із доступом до нього.                                   |
| **Cross-account Access** | Доступ principal з іншого AWS account через resource policy, IAM permissions і за потреби AssumeRole.      |
| **Caching**              | Локальне кешування secret для зменшення latency та API costs; cache має враховувати ротацію.               |

## Типовий екзаменаційний сценарій

Потрібно зберігати DB credentials і автоматично їх ротувати → Secrets
Manager.

## Екзаменаційна пастка

Не логувати секрети. Застосунок має коректно перечитувати значення після
ротації.

## Як готуватися до цього сервісу

- Розпізнавайте, яку проблему сервіс вирішує, і коли його обирати
  замість альтернатив.
- Звертайте увагу на IAM permissions, resource policies та service
  roles.
- Розумійте event flow, retries, idempotency, throttling і dead-letter
  handling, якщо вони застосовні.
- Порівнюйте availability, consistency, scaling, latency та cost
  trade-offs.

## Офіційні джерела

- [AWS Documentation — AWS Secrets
  Manager](https://docs.aws.amazon.com/)
- [DVA-C02 Exam
  Guide](https://docs.aws.amazon.com/aws-certification/latest/developer-associate-02/developer-associate-02.html)
