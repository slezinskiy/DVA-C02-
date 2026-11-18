# Amazon RDS

**Категорія:** Database  
**Призначення:** Керована реляційна БД із backup, patching, monitoring і
мережевою інтеграцією.

## Словник термінів

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

## Типовий екзаменаційний сценарій

Потрібен керований SQL database engine → RDS; потрібне масштабування
читання → Read Replica.

## Екзаменаційна пастка

Multi-AZ переважно для HA/failover; Read Replica для read scaling. Не
ототожнюйте їх.

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

- [AWS Documentation — Amazon RDS](https://docs.aws.amazon.com/)
- [DVA-C02 Exam
  Guide](https://docs.aws.amazon.com/aws-certification/latest/developer-associate-02/developer-associate-02.html)
