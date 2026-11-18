# AWS Lambda

**Категорія:** Compute  
**Призначення:** Serverless compute для виконання коду у відповідь на
події або API-виклики.

## Словник термінів

| Термін                      | Визначення українською                                                                                                                                                    |
|-----------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| **Function**                | Окрема одиниця коду AWS Lambda з власною конфігурацією, версіями, роллю виконання та параметрами масштабування.                                                           |
| **Handler**                 | Кодова точка входу для Lambda (визначення наведено в розділі Lambda).                                                                                                     |
| **Runtime**                 | Кероване середовище виконання Lambda для певної мови програмування або власний runtime.                                                                                   |
| **Invocation**              | Один запуск Lambda function у відповідь на синхронний або асинхронний виклик чи подію від event source.                                                                   |
| **Event**                   | Вхідний payload invocation, який описує запит або подію для обробки Lambda.                                                                                               |
| **Context**                 | Об’єкт Lambda context із метаданими поточного invocation: request ID, назва функції, memory limit і час до timeout.                                                       |
| **Execution Role**          | IAM role, яку Lambda assume під час виконання функції. Дозволяє коду звертатися до S3, DynamoDB, CloudWatch Logs та інших ресурсів.                                       |
| **Resource Policy**         | Політика на самій Lambda function, яка визначає, які principals або AWS services можуть викликати функцію.                                                                |
| **Timeout**                 | Максимальний час виконання одного Lambda invocation; після його перевищення Lambda завершує виконання з timeout error.                                                    |
| **Memory**                  | Обсяг пам’яті, налаштований для Lambda. Від нього залежить також доступна CPU-потужність та інші ресурси виконання.                                                       |
| **/tmp**                    | Тимчасова файлова система Lambda для проміжних файлів. Дані можуть зберігатися між повторними викликами в тому самому execution environment, але не є постійним сховищем. |
| **Layer**                   | ZIP-архів із бібліотеками, runtime dependencies або іншими файлами, які підключаються до Lambda function окремо від основного deployment package.                         |
| **Version**                 | Незмінний snapshot коду та конфігурації Lambda function. Published version має числовий номер.                                                                            |
| **Alias**                   | Іменований покажчик на одну Lambda version або розподіл трафіку між двома версіями; зручно для deployment і rollback.                                                     |
| **Reserved Concurrency**    | Резервує concurrency для функції та встановлює її верхню межу одночасних executions. Значення 0 зупиняє нові виклики.                                                     |
| **Provisioned Concurrency** | Попередньо ініціалізує задану кількість Lambda execution environments, щоб зменшити cold start latency.                                                                   |
| **Cold Start**              | Додаткова затримка першого виклику в новому execution environment через підготовку середовища, завантаження runtime та ініціалізацію коду.                                |
| **Event Source Mapping**    | Конфігурація Lambda, яка опитує підтримуване джерело подій (наприклад SQS, Kinesis або DynamoDB Streams) і передає batches у функцію.                                     |
| **DLQ**                     | Dead-letter queue для асинхронних Lambda invocations: місце призначення повідомлень, які не вдалося успішно обробити після повторних спроб.                               |
| **Destinations**            | Налаштування асинхронної Lambda, яке надсилає результат invocation (успіх або невдачу) до підтримуваного destination, наприклад SQS, SNS, EventBridge або іншої Lambda.   |
| **VPC**                     | Мережа, до якої Lambda підключає execution environment через ENI, щоб звертатися до приватних ресурсів. Для доступу в інтернет із private subnet зазвичай потрібен NAT.   |
| **SnapStart**               | Оптимізація cold start для підтримуваних Java runtimes: Lambda створює snapshot ініціалізованого execution environment і відновлює його під час запуску.                  |
| **Function URL**            | HTTPS endpoint, який надає прямий доступ до Lambda function без окремого API Gateway. Підтримує AWS_IAM або NONE authentication type.                                     |

## Типовий екзаменаційний сценарій

Подієвий код без керування серверами → Lambda.

## Екзаменаційна пастка

Execution Role визначає доступ функції до AWS; resource policy визначає,
хто може її викликати. Reserved і Provisioned Concurrency — різні речі.

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

- [AWS Documentation — AWS Lambda](https://docs.aws.amazon.com/)
- [DVA-C02 Exam
  Guide](https://docs.aws.amazon.com/aws-certification/latest/developer-associate-02/developer-associate-02.html)
