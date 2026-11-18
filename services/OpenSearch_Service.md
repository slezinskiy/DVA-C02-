# Amazon OpenSearch Service

**Категорія:** Analytics  
**Призначення:** Керований пошуковий та аналітичний рушій для
повнотекстового пошуку, логів і observability.

## Словник термінів

| Термін             | Визначення українською                                                                                                           |
|--------------------|----------------------------------------------------------------------------------------------------------------------------------|
| **Domain**         | Керований deployment OpenSearch Service, що містить кластер, мережеві та security налаштування.                                  |
| **Cluster**        | Набір OpenSearch nodes, які разом зберігають shards та обробляють запити.                                                        |
| **Node**           | Окремий вузол OpenSearch cluster із роллю data, ingest або cluster manager.                                                      |
| **Index**          | Логічна колекція документів OpenSearch, оптимізована для пошуку та аналітики.                                                    |
| **Document**       | JSON-запис, який індексується та зберігається в OpenSearch.                                                                      |
| **Mapping**        | Опис типів полів і правил індексації документів у OpenSearch.                                                                    |
| **Inverted Index** | Структура пошукового індексу, що зіставляє терміни з документами, у яких вони зустрічаються.                                     |
| **Analyzer**       | Компонент OpenSearch, який розбиває текст на tokens і може нормалізувати їх перед індексацією або пошуком.                       |
| **Shard**          | Одиниця ємності та паралелізму Kinesis Data Streams. Кожен shard має діапазон partition keys і власний порядок sequence numbers. |
| **Replica**        | Копія shard OpenSearch, що підвищує доступність і може розподіляти навантаження читання.                                         |
| **Query DSL**      | JSON-мова OpenSearch для побудови пошукових запитів, фільтрів і умов.                                                            |
| **Aggregation**    | Операція OpenSearch для групування та обчислення статистики над набором документів.                                              |
| **Snapshot**       | Резервна копія OpenSearch indexes та cluster state, яка зберігається у snapshot repository, зазвичай S3.                         |
| **Ingestion**      | Надходження, перетворення та індексація даних у OpenSearch через clients або ingestion pipelines.                                |

## Типовий екзаменаційний сценарій

Потрібен повнотекстовий пошук або пошук по логах → OpenSearch.

## Екзаменаційна пастка

Не є транзакційною реляційною БД чи заміною DynamoDB для key-value
доступу.

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

- [AWS Documentation — Amazon OpenSearch
  Service](https://docs.aws.amazon.com/)
- [DVA-C02 Exam
  Guide](https://docs.aws.amazon.com/aws-certification/latest/developer-associate-02/developer-associate-02.html)
