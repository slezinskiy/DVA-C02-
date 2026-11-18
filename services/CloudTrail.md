# AWS CloudTrail

**Категорія:** Management and Governance  
**Призначення:** Аудит AWS API activity та подій акаунта.

## Словник термінів

| Термін                 | Визначення українською                                                                                                          |
|------------------------|---------------------------------------------------------------------------------------------------------------------------------|
| **Management Event**   | CloudTrail подія керування AWS ресурсом або конфігурацією, наприклад створення EC2 instance чи зміна IAM policy.                |
| **Data Event**         | CloudTrail подія доступу до даних усередині ресурсу, наприклад GetObject/PutObject для S3; зазвичай потребує явного ввімкнення. |
| **Read/Write Event**   | Класифікація management events: read-only події читають стан, write events змінюють ресурси або конфігурацію.                   |
| **Trail**              | Конфігурація CloudTrail, яка доставляє event logs до S3 і, за потреби, CloudWatch Logs.                                         |
| **Event History**      | Перегляд останніх 90 днів management events у регіоні без створення trail.                                                      |
| **CloudTrail Lake**    | Кероване сховище event data з SQL-подібними запитами для аудиту та розслідувань.                                                |
| **Insights**           | Функція, що виявляє аномальні зміни обсягу API calls або частоти помилок management events.                                     |
| **Multi-Region Trail** | Trail, який записує події з усіх увімкнених AWS Regions account.                                                                |
| **Organization Trail** | Trail організації AWS Organizations, що централізовано збирає події member accounts.                                            |
| **Log Integrity**      | Перевірка незмінності CloudTrail logs за допомогою digest files і криптографічних хешів.                                        |
| **UserIdentity**       | Поле event, яке описує IAM/federated identity, що ініціювала API request.                                                       |
| **EventSource**        | Поле з назвою AWS service endpoint, який отримав API request, наприклад ec2.amazonaws.com.                                      |
| **EventName**          | Поле з назвою викликаної API operation, наприклад RunInstances.                                                                 |

## Типовий екзаменаційний сценарій

Потрібно з’ясувати, хто виконав AWS API дію → CloudTrail.

## Екзаменаційна пастка

CloudTrail не замінює application logs у CloudWatch.

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

- [AWS Documentation — AWS CloudTrail](https://docs.aws.amazon.com/)
- [DVA-C02 Exam
  Guide](https://docs.aws.amazon.com/aws-certification/latest/developer-associate-02/developer-associate-02.html)
