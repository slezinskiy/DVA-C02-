# Amazon Kinesis

**Категорія:** Analytics  
**Призначення:** Сімейство сервісів для приймання, потокової обробки та
доставки подій.

## Словник термінів

| Термін               | Визначення українською                                                                                                                                                    |
|----------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| **Data Streams**     | Amazon Kinesis Data Streams — керований потік записів, які producers публікують, а consumers читають і обробляють.                                                        |
| **Data Firehose**    | Amazon Data Firehose — керована доставка потокових даних до призначень, наприклад S3, Redshift, OpenSearch або HTTP endpoint, із буферизацією та опційною трансформацією. |
| **Producer**         | Застосунок або сервіс, який створює та надсилає записи до потоку або повідомлення до черги/topic.                                                                         |
| **Consumer**         | Застосунок або сервіс, який отримує записи з потоку або повідомлення з черги/topic і виконує їх обробку.                                                                  |
| **Shard**            | Одиниця ємності та паралелізму Kinesis Data Streams. Кожен shard має діапазон partition keys і власний порядок sequence numbers.                                          |
| **Partition Key**    | Значення, за яким Kinesis Data Streams обчислює hash і спрямовує запис до shard; однаковий key спрямовує записи до того самого shard.                                     |
| **Sequence Number**  | Ідентифікатор запису в межах shard Kinesis; допомагає визначити позицію запису та порядок читання.                                                                        |
| **Retention**        | Період, протягом якого записи залишаються доступними в Kinesis Data Streams для повторного читання.                                                                       |
| **Enhanced Fan-Out** | Режим Kinesis Data Streams, у якому registered consumer отримує виділену пропускну здатність читання через HTTP/2 SubscribeToShard.                                       |
| **KCL**              | Kinesis Client Library — бібліотека, що координує читання shard, балансування між workers і збереження checkpoint для consumer application.                               |
| **Checkpoint**       | Збережена позиція читання в shard, з якої consumer може продовжити обробку після перезапуску.                                                                             |
| **Resharding**       | Операція збільшення або зменшення кількості shard Kinesis Data Streams для зміни загальної пропускної здатності.                                                          |
| **Buffering**        | Накопичення даних до досягнення заданого розміру або часу перед доставкою, зокрема в Firehose.                                                                            |

## Типовий екзаменаційний сценарій

Потрібен контроль consumer та повторне читання потоку → Data Streams;
потрібна керована доставка в S3 → Firehose.

## Екзаменаційна пастка

Kinesis Streams — журнал потоку для consumer; SQS — черга повідомлень.
Не плутати Data Streams із Data Firehose.

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

- [AWS Documentation — Amazon Kinesis](https://docs.aws.amazon.com/)
- [DVA-C02 Exam
  Guide](https://docs.aws.amazon.com/aws-certification/latest/developer-associate-02/developer-associate-02.html)
