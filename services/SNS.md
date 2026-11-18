# Amazon SNS

**Категорія:** Application Integration  
**Призначення:** Pub/sub сервіс для fan-out повідомлень багатьом
підписникам.

## Словник термінів

| Термін                   | Визначення українською                                                                                                                      |
|--------------------------|---------------------------------------------------------------------------------------------------------------------------------------------|
| **Topic**                | Іменований канал SNS, у який publisher надсилає повідомлення для доставки subscribers.                                                      |
| **Publisher**            | Клієнт або AWS service, який публікує повідомлення в SNS topic.                                                                             |
| **Subscriber**           | Endpoint або сервіс, підписаний на SNS topic і здатний отримувати його повідомлення.                                                        |
| **Subscription**         | Підписка зв’язує SNS topic із endpoint і визначає протокол доставки та параметри повідомлень.                                               |
| **Fan-out**              | Архітектурний патерн, у якому одне повідомлення SNS доставляється кільком незалежним subscribers, наприклад SQS queues.                     |
| **Message Attributes**   | Додаткові структуровані метадані SNS message, які можуть використовуватися subscription filter policies.                                    |
| **Filter Policy**        | JSON-умова SNS subscription, що визначає, які повідомлення доставляти конкретному subscriber.                                               |
| **Raw Message Delivery** | Режим subscription, у якому endpoint отримує початкове message body без SNS JSON envelope.                                                  |
| **FIFO Topic**           | SNS topic із FIFO-поведінкою, message ordering і deduplication.                                                                             |
| **Deduplication**        | Механізм FIFO, який виявляє дублікати за deduplication ID або content-based hash.                                                           |
| **Delivery Policy**      | Налаштування retry для доставки повідомлень до HTTP/S endpoint.                                                                             |
| **DLQ**                  | Dead-letter queue для асинхронних Lambda invocations: місце призначення повідомлень, які не вдалося успішно обробити після повторних спроб. |

## Типовий екзаменаційний сценарій

Одне повідомлення потрібно доставити кільком незалежним споживачам →
SNS.

## Екзаменаційна пастка

SNS не є чергою для довготривалого споживання. Часто поєднується з
окремою SQS queue для кожного consumer.

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

- [AWS Documentation — Amazon SNS](https://docs.aws.amazon.com/)
- [DVA-C02 Exam
  Guide](https://docs.aws.amazon.com/aws-certification/latest/developer-associate-02/developer-associate-02.html)
