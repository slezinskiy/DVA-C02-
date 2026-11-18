# AWS Step Functions

**Категорія:** Application Integration  
**Призначення:** Керована оркестрація багатокрокових workflow між Lambda
та іншими сервісами.

## Словник термінів

| Термін              | Визначення українською                                                                                                                                   |
|---------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------|
| **State Machine**   | Опис workflow у Step Functions як набору станів і переходів між ними.                                                                                    |
| **State**           | Окремий крок state machine, який виконує дію, перевіряє умову, очікує або завершує workflow.                                                             |
| **Task**            | Стан, який виконує роботу через AWS service integration, Lambda або інший task resource.                                                                 |
| **Choice**          | Стан Step Functions для умовного розгалуження на основі значень у state input.                                                                           |
| **Pass**            | Стан, який передає input до output або формує статичні дані без зовнішнього виклику.                                                                     |
| **Wait**            | Стан, який призупиняє workflow на заданий інтервал або до timestamp.                                                                                     |
| **Parallel**        | Стан, який запускає кілька гілок workflow паралельно та очікує їх завершення.                                                                            |
| **Map**             | Стан, який повторює набір кроків для елементів масиву вхідних даних.                                                                                     |
| **Distributed Map** | Режим Map для масштабної паралельної обробки великої кількості items через child workflow executions.                                                    |
| **Succeed**         | Термінальний стан успішного завершення workflow.                                                                                                         |
| **Fail**            | Термінальний стан, який завершує workflow із помилкою.                                                                                                   |
| **ASL**             | Amazon States Language — JSON-формат, яким описують стани, переходи, retries і обробку помилок Step Functions.                                           |
| **Standard**        | Тип Step Functions workflow для довготривалих процесів із тривалою історією виконання та exactly-once workflow execution semantics за правилами сервісу. |
| **Express**         | Тип Step Functions workflow для високочастотних коротких процесів; має іншу модель історії, тривалості та ціноутворення.                                 |
| **Retry**           | Налаштування Step Functions, яке повторює стан після визначених помилок із параметрами інтервалу, backoff і максимальної кількості спроб.                |
| **Catch**           | Налаштування Step Functions для перехоплення помилки та переходу до альтернативного стану.                                                               |
| **Execution**       | Один запуск state machine із конкретним input, execution ARN, status та history.                                                                         |
| **Task Token**      | Токен callback pattern, який зовнішня система повертає через SendTaskSuccess/SendTaskFailure для продовження workflow.                                   |

## Типовий екзаменаційний сценарій

Потрібно координувати кроки, retries, branching, wait та error handling
→ Step Functions.

## Екзаменаційна пастка

Lambda виконує код; Step Functions координує workflow. Standard і
Express мають різні характеристики виконання та історії.

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

- [AWS Documentation — AWS Step Functions](https://docs.aws.amazon.com/)
- [DVA-C02 Exam
  Guide](https://docs.aws.amazon.com/aws-certification/latest/developer-associate-02/developer-associate-02.html)
