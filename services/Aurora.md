# Amazon Aurora

**Категорія:** Database  
**Призначення:** Реляційна БД, сумісна з MySQL/PostgreSQL, з cluster
storage та writer/reader instances.

## Словник термінів

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

## Типовий екзаменаційний сценарій

Потрібна керована реляційна БД із високою доступністю та read replicas →
Aurora.

## Екзаменаційна пастка

Reader endpoint спрямовує read connections; cluster endpoint — до
writer. Не плутати Aurora Replica із DynamoDB Global Tables.

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

- [AWS Documentation — Amazon Aurora](https://docs.aws.amazon.com/)
- [DVA-C02 Exam
  Guide](https://docs.aws.amazon.com/aws-certification/latest/developer-associate-02/developer-associate-02.html)
