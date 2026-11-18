# Amazon ElastiCache

**Категорія:** Database  
**Призначення:** Керований in-memory cache для зменшення latency та
навантаження на бази даних.

## Словник термінів

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

## Типовий екзаменаційний сценарій

Потрібен загальний кеш для застосунку або сесій → ElastiCache.

## Екзаменаційна пастка

DAX спеціалізований для DynamoDB; ElastiCache — загальний кеш для різних
застосунків.

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

- [AWS Documentation — Amazon ElastiCache](https://docs.aws.amazon.com/)
- [DVA-C02 Exam
  Guide](https://docs.aws.amazon.com/aws-certification/latest/developer-associate-02/developer-associate-02.html)
