# Database — довідник DVA-C02

Тематичний довідник із визначеннями термінів, практичними сценаріями та
типовими екзаменаційними пастками.

## Amazon Aurora

**Призначення:** Реляційна БД, сумісна з MySQL/PostgreSQL, з cluster
storage та writer/reader instances.

### Ключові терміни

| Термін                    | Визначення українською                                                                                                               |
|---------------------------|--------------------------------------------------------------------------------------------------------------------------------------|
| **DB Cluster**            | Aurora database cluster із shared storage volume та одним або кількома DB instances.                                                 |
| **Writer**                | Aurora instance, який обробляє write operations і зазвичай також read requests.                                                      |
| **Reader**                | Aurora Replica, яка обслуговує read-only запити та може стати writer після failover.                                                 |
| **Cluster Endpoint**      | Aurora endpoint, який спрямовує з’єднання до поточного writer instance кластера.                                                     |
| **Reader Endpoint**       | Aurora endpoint, що розподіляє read-only з’єднання між доступними Aurora Replicas.                                                   |
| **Instance Endpoint**     | Endpoint, що адресує конкретний Aurora DB instance, а не автоматично вибраний writer/reader.                                         |
| **Shared Cluster Volume** | Розподілене спільне storage Aurora, доступне всім instances кластера; compute і storage масштабуються окремо.                        |
| **Aurora Replica**        | Додатковий DB instance у кластері Aurora, який читає зі спільного storage та допомагає масштабувати читання/підвищувати доступність. |
| **Failover**              | Автоматичне або ручне перемикання writer role на доступну репліку при відмові поточного writer.                                      |
| **Global Database**       | Aurora конфігурація для реплікації даних між AWS Regions із низькою затримкою та disaster recovery.                                  |
| **Serverless v2**         | Режим Aurora, який автоматично масштабує compute capacity у межах заданого діапазону ACUs.                                           |
| **Backtrack**             | Функція Aurora MySQL, що дозволяє повернути кластер до попереднього моменту без відновлення з backup.                                |
| **Parameter Group**       | Набір налаштувань engine для Aurora DB instances або cluster.                                                                        |
| **RDS Proxy**             | Керований database proxy, який об’єднує та повторно використовує DB connections, зменшуючи connection overhead.                      |
| **Snapshot**              | Point-in-time копія EBS volume або backup snapshot бази даних; точний зміст залежить від сервісу.                                    |

**Типовий екзаменаційний сценарій:** Потрібна керована реляційна БД із
високою доступністю та read replicas → Aurora.

**Екзаменаційна пастка:** Reader endpoint спрямовує read connections;
cluster endpoint — до writer. Не плутати Aurora Replica із DynamoDB
Global Tables.

------------------------------------------------------------------------

## Amazon DynamoDB

**Призначення:** Serverless NoSQL key-value/document database із
доступом за ключами.

### Ключові терміни

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

**Типовий екзаменаційний сценарій:** Потрібен дуже низьколатентний
key-value/document доступ із масштабуванням → DynamoDB.

**Екзаменаційна пастка:** GSI не підтримує strong reads;
FilterExpression не зменшує прочитану capacity; TTL асинхронний;
BatchWrite не атомарний.

------------------------------------------------------------------------

## Amazon ElastiCache

**Призначення:** Керований in-memory cache для зменшення latency та
навантаження на бази даних.

### Ключові терміни

| Термін                | Визначення українською                                                                                       |
|-----------------------|--------------------------------------------------------------------------------------------------------------|
| **Valkey/Redis OSS**  | In-memory key-value data store із підтримкою структур даних, replication і кешування.                        |
| **Memcached**         | Простий розподілений in-memory key-value cache без вбудованої persistence/replication моделі Redis.          |
| **Cache Hit/Miss**    | Hit — ключ знайдено в кеші; miss — потрібно завантажити дані з основного джерела.                            |
| **Cache Aside**       | Патерн: застосунок спершу перевіряє кеш, за cache miss читає БД, а потім записує результат у кеш.            |
| **Lazy Loading**      | Патерн, коли cache наповнюється лише після запиту та cache miss.                                             |
| **Write-through**     | Патерн, за якого зміна основного сховища супроводжується оновленням кешу.                                    |
| **TTL**               | Час життя cache key, після якого ключ стає простроченим.                                                     |
| **Eviction**          | Видалення ключів із кешу за політикою витіснення, наприклад LRU, коли досягнуто ліміту пам’яті.              |
| **Node**              | Окремий обчислювальний вузол ElastiCache, що надає пам’ять і обробляє запити.                                |
| **Shard**             | Група вузлів, що зберігає частину keyspace у cluster-mode enabled deployment.                                |
| **Replication Group** | Керована група ElastiCache nodes із primary та replicas.                                                     |
| **Cluster Mode**      | Режим, що визначає, чи розподілено keyspace між shards (enabled), чи використовується один shard (disabled). |
| **Multi-AZ**          | Розміщення primary та replicas у різних AZ для failover і доступності.                                       |
| **Failover**          | Перемикання на резервний instance/endpoint після відмови основного ресурсу.                                  |

**Типовий екзаменаційний сценарій:** Потрібен загальний кеш для
застосунку або сесій → ElastiCache.

**Екзаменаційна пастка:** DAX спеціалізований для DynamoDB; ElastiCache
— загальний кеш для різних застосунків.

------------------------------------------------------------------------

## Amazon RDS

**Призначення:** Керована реляційна БД із backup, patching, monitoring і
мережевою інтеграцією.

### Ключові терміни

| Термін                    | Визначення українською                                                                                                                     |
|---------------------------|--------------------------------------------------------------------------------------------------------------------------------------------|
| **DB Instance**           | Керований екземпляр реляційної БД RDS із engine, compute, storage і network configuration.                                                 |
| **Engine**                | Тип СУБД RDS, наприклад MySQL, PostgreSQL, MariaDB, Oracle або SQL Server.                                                                 |
| **Instance Class**        | Профіль CPU, memory та network для DB instance.                                                                                            |
| **DB Subnet Group**       | Набір VPC subnets, з яких RDS розміщує DB instance; для Multi-AZ потрібні subnet у різних AZ.                                              |
| **Multi-AZ**              | Розміщення ресурсу або його standby/replicas у кількох Availability Zones для підвищення доступності та стійкості до відмови AZ.           |
| **Read Replica**          | Копія RDS database instance, що реплікує зміни з source DB і використовується для масштабування читання. Зазвичай має окремий endpoint.    |
| **Automated Backup**      | Автоматичні резервні копії RDS для point-in-time recovery у межах retention period.                                                        |
| **Snapshot**              | Ручна point-in-time копія RDS DB instance або cluster, яка зберігається до видалення користувачем і може бути використана для відновлення. |
| **PITR**                  | Point-in-Time Recovery — безперервне резервне копіювання, що дозволяє відновити таблицю до конкретного моменту в межах періоду зберігання. |
| **Maintenance Window**    | Період, коли RDS може виконувати заплановані maintenance operations.                                                                       |
| **Parameter Group**       | Набір параметрів конфігурації database engine.                                                                                             |
| **Option Group**          | Набір додаткових engine-specific options для підтримуваних RDS engines.                                                                    |
| **RDS Proxy**             | Керований proxy між застосунком і RDS/Aurora, який об’єднує та повторно використовує database connections.                                 |
| **IAM DB Authentication** | Автентифікація до підтримуваних DB engines через тимчасовий IAM token замість постійного DB password.                                      |
| **KMS Encryption**        | Шифрування RDS storage, snapshots і backups за допомогою KMS key.                                                                          |

**Типовий екзаменаційний сценарій:** Потрібен керований SQL database
engine → RDS; потрібне масштабування читання → Read Replica.

**Екзаменаційна пастка:** Multi-AZ переважно для HA/failover; Read
Replica для read scaling. Не ототожнюйте їх.

------------------------------------------------------------------------
