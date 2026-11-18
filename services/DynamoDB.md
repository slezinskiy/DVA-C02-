# Amazon DynamoDB

**Категорія:** Database  
**Призначення:** Serverless NoSQL key-value/document database із
доступом за ключами.

## Словник термінів

| Термін                           | Визначення українською                                                                                                                                                                                                          |
|----------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| **Table**                        | Логічна таблиця DynamoDB, що містить items. Кожна таблиця має primary key, який однозначно ідентифікує item.                                                                                                                    |
| **Item**                         | Окремий запис у DynamoDB, набір пар attribute-value. Різні items однієї таблиці можуть мати різні атрибути.                                                                                                                     |
| **Attribute**                    | Поле item у DynamoDB: ім’я та значення певного типу (наприклад String, Number, Binary, Map або List).                                                                                                                           |
| **Partition Key**                | Обов’язкова частина primary key DynamoDB. Її значення використовується для розподілу даних між фізичними partitions; рівномірний розподіл допомагає уникнути hot partitions.                                                    |
| **Sort Key**                     | Друга, необов’язкова частина composite primary key. Дозволяє зберігати кілька items з одним partition key та впорядковувати/фільтрувати їх за sort key.                                                                         |
| **Simple/Composite Primary Key** | Simple key складається лише з partition key; composite key — з partition key та sort key. Primary key унікально визначає item у таблиці.                                                                                        |
| **GSI**                          | Global Secondary Index — індекс із власними partition key і, за потреби, sort key. Дозволяє виконувати Query за альтернативним ключем; може охоплювати всю таблицю.                                                             |
| **LSI**                          | Local Secondary Index — індекс із тим самим partition key, що й таблиця, але іншим sort key. Створюється під час створення таблиці.                                                                                             |
| **Query**                        | Операція DynamoDB, яка читає items за обов’язковою умовою partition key і необов’язковою умовою sort key. Зазвичай ефективніша за Scan.                                                                                         |
| **Scan**                         | Операція DynamoDB, що переглядає items таблиці або індексу. FilterExpression застосовується після читання, тому Scan може споживати значну кількість read capacity.                                                             |
| **FilterExpression**             | Умова, яка відкидає непотрібні елементи з уже прочитаних результатів Query або Scan. Не зменшує кількість прочитаних даних чи витрачену read capacity.                                                                          |
| **ProjectionExpression**         | Список атрибутів, які потрібно повернути у відповіді. Зменшує розмір payload, але зазвичай не зменшує read capacity, витрачену на читання.                                                                                      |
| **ConditionExpression**          | Умова, яку DynamoDB перевіряє перед записом або зміною item. Дозволяє реалізувати conditional write та уникати перезапису застарілих даних.                                                                                     |
| **UpdateExpression**             | Вираз для зміни атрибутів item без повного перезапису: SET, REMOVE, ADD або DELETE.                                                                                                                                             |
| **RCU/WCU**                      | Read Capacity Unit і Write Capacity Unit для provisioned mode. Для стандартних розмірів одна RCU відповідає одному strongly consistent read до 4 KB/с або двом eventually consistent reads; одна WCU — одному запису до 1 KB/с. |
| **RRU/WRU**                      | Read Request Unit і Write Request Unit, що використовуються для обліку запитів у on-demand mode. Фактичне споживання залежить від розміру item та типу операції/узгодженості.                                                   |
| **On-Demand**                    | Режим DynamoDB без ручного provisioned capacity. Оплата залежить від кількості read/write request units; підходить для змінного або непередбачуваного навантаження.                                                             |
| **Provisioned**                  | Режим, у якому задають read і write capacity. Можна використовувати Auto Scaling для автоматичного коригування ємності.                                                                                                         |
| **Strong/Eventual Consistency**  | Strongly consistent read повертає найсвіжіші успішні записи (підтримується для таблиць і LSI, але не GSI/Streams). Eventually consistent read може тимчасово повертати старі дані, але коштує менше capacity.                   |
| **Streams**                      | DynamoDB Streams фіксує зміни items у порядку їх модифікації та зберігає записи до 24 годин. Типово інтегрується з Lambda для event-driven обробки.                                                                             |
| **TTL**                          | Time to Live — атрибут із Unix epoch timestamp, після якого DynamoDB асинхронно видаляє item. Видалення не відбувається точно в момент expiration.                                                                              |
| **DAX**                          | DynamoDB Accelerator — сумісний із DynamoDB in-memory cache для мікросекундної затримки читання. Не є заміною базі даних і не прискорює всі типи запитів.                                                                       |
| **Global Tables**                | Багаторегіональна реплікація DynamoDB для локального читання/запису в кількох AWS Regions. Підтримує multi-Region applications; конфлікти записів вирішуються за правилами сервісу.                                             |
| **Transactions**                 | TransactWriteItems і TransactGetItems забезпечують ACID-операції над кількома items/таблицями в межах підтримуваних лімітів.                                                                                                    |
| **Batch**                        | BatchGetItem і BatchWriteItem об’єднують кілька операцій в один API-запит. Не забезпечують атомарність; необроблені елементи потрібно повторити.                                                                                |
| **PITR**                         | Point-in-Time Recovery — безперервне резервне копіювання, що дозволяє відновити таблицю до конкретного моменту в межах періоду зберігання.                                                                                      |
| **PartiQL**                      | SQL-сумісний інтерфейс для читання та зміни даних DynamoDB. Не перетворює DynamoDB на реляційну базу даних.                                                                                                                     |
| **Hot Key**                      | Partition key, до якого надходить непропорційно багато запитів. Може створити гарячу partition і спричинити throttling.                                                                                                         |
| **Adaptive Capacity**            | Механізм DynamoDB, який автоматично перерозподіляє доступну throughput capacity на користь partitions із вищим навантаженням; не усуває поганий key design.                                                                     |

## Типовий екзаменаційний сценарій

Потрібен дуже низьколатентний key-value/document доступ із
масштабуванням → DynamoDB.

## Екзаменаційна пастка

GSI не підтримує strong reads; FilterExpression не зменшує прочитану
capacity; TTL асинхронний; BatchWrite не атомарний.

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

- [AWS Documentation — Amazon DynamoDB](https://docs.aws.amazon.com/)
- [DVA-C02 Exam
  Guide](https://docs.aws.amazon.com/aws-certification/latest/developer-associate-02/developer-associate-02.html)
