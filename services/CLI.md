# AWS CLI

**Категорія:** Management and Governance  
**Призначення:** Командний інтерфейс для виклику AWS APIs та
автоматизації.

## Словник термінів

| Термін                        | Визначення українською                                                                                                |
|-------------------------------|-----------------------------------------------------------------------------------------------------------------------|
| **Profile**                   | Named set of AWS CLI credentials та settings у config/credentials files.                                              |
| **Region**                    | AWS географічний регіон, до якого CLI надсилає запити, якщо команда не задає інше.                                    |
| **Output**                    | Формат виводу AWS CLI, наприклад json, yaml, text або table.                                                          |
| **–query/JMESPath**           | Параметр –query використовує JMESPath для фільтрації та перетворення JSON-відповіді перед виведенням.                 |
| **Pagination**                | Автоматичне отримання кількох сторінок API results, коли сервіс повертає continuation token.                          |
| **–no-paginate**              | Вимикає автоматичне отримання наступних сторінок і повертає лише першу відповідь API.                                 |
| **–page-size**                | Задає кількість елементів, яку CLI запитує на одній сторінці від сервісу.                                             |
| **–max-items**                | Обмежує загальну кількість елементів, які CLI повертає користувачу.                                                   |
| **–starting-token**           | Дозволяє продовжити пагінований результат із token, отриманого попереднім CLI-викликом.                               |
| **–dry-run**                  | Параметр для підтримуваних API, що перевіряє можливість виконання операції без фактичної зміни ресурсу.               |
| **–debug**                    | Вмикає детальний debug output CLI, включно з діагностикою запитів і відповідей.                                       |
| **Credential Provider Chain** | Порядок джерел, з яких AWS CLI/SDK шукає credentials: environment, profile, role, SSO та інші підтримувані providers. |

## Типовий екзаменаційний сценарій

Потрібно автоматизувати AWS operations у shell/CI → AWS CLI.

## Екзаменаційна пастка

`--query` фільтрує вивід CLI; це не те саме, що API-side `--filter`
параметр.

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

- [AWS Documentation — AWS CLI](https://docs.aws.amazon.com/)
- [DVA-C02 Exam
  Guide](https://docs.aws.amazon.com/aws-certification/latest/developer-associate-02/developer-associate-02.html)
