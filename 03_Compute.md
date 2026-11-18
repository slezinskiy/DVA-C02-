# Compute — довідник DVA-C02

Тематичний довідник із визначеннями термінів, практичними сценаріями та
типовими екзаменаційними пастками.

## Amazon EC2

**Призначення:** Віртуальні сервери з повним контролем над ОС, типом
інстансу та програмним середовищем.

### Ключові терміни

| Термін                   | Визначення українською                                                                                                                    |
|--------------------------|-------------------------------------------------------------------------------------------------------------------------------------------|
| **Instance**             | Віртуальний сервер EC2 із AMI, instance type, storage, networking і security configuration.                                               |
| **AMI**                  | Образ EC2, який містить операційну систему та налаштування запуску (визначення наведено в розділі EC2).                                   |
| **Instance Type/Family** | Розмір і сімейство EC2, що визначають vCPU, memory, network та оптимізацію workload.                                                      |
| **User Data**            | Скрипт або cloud-init configuration, яку EC2 передає інстансу під час запуску для bootstrap/автоматичного налаштування.                   |
| **Metadata**             | Інформація про EC2 instance, доступна через Instance Metadata Service, зокрема instance ID та IAM credentials.                            |
| **IMDSv2**               | Захищений режим EC2 Instance Metadata Service, який вимагає отримати session token перед читанням metadata.                               |
| **Instance Profile**     | Контейнер для IAM role, який прикріплюється до EC2 instance і надає тимчасові credentials застосункам на інстансі.                        |
| **Security Group**       | Stateful virtual firewall для ENI/resource. Дозволяє правила allow; відповідь на дозволене з’єднання пропускається автоматично.           |
| **EBS**                  | Elastic Block Store — persistent block storage, яке може існувати незалежно від життєвого циклу EC2 instance.                             |
| **Instance Store**       | Тимчасове локальне сховище на фізичному хості; дані можуть бути втрачені при зупинці/завершенні instance або відмові хоста.               |
| **Placement Group**      | Стратегія розміщення instances: Cluster для низької latency/high throughput, Spread для ізоляції, Partition для розподілу великих систем. |
| **ASG**                  | Auto Scaling Group — група EC2, яка підтримує desired capacity і масштабується за policies.                                               |
| **Launch Template**      | Шаблон параметрів запуску EC2: AMI, instance type, networking, storage, IAM profile та інші налаштування.                                 |
| **Spot**                 | Модель EC2 capacity зі зниженою ціною, за якої AWS може перервати instance; підходить для fault-tolerant workload.                        |
| **On-Demand**            | Оплата за фактичне використання EC2 без довгострокового зобов’язання.                                                                     |
| **Savings Plans**        | Знижка в обмін на погодинне зобов’язання щодо compute usage на 1 або 3 роки.                                                              |
| **Elastic IP**           | Статична публічна IPv4 адреса AWS, яку можна перепризначати між сумісними ресурсами.                                                      |
| **ENI**                  | Elastic Network Interface — віртуальна мережева карта AWS із private IP, security groups та іншими мережевими атрибутами.                 |

**Типовий екзаменаційний сценарій:** Потрібен контроль над ОС, агентами
або довготривалим процесом → EC2.

**Екзаменаційна пастка:** IAM Role через Instance Profile краще за
статичні access keys. Stop зберігає інстанс; Terminate видаляє його.

------------------------------------------------------------------------

## AWS Elastic Beanstalk

**Призначення:** PaaS-подібний сервіс розгортання застосунків із
керуванням середовищем та базовими AWS-ресурсами.

### Ключові терміни

| Термін                     | Визначення українською                                                                              |
|----------------------------|-----------------------------------------------------------------------------------------------------|
| **Application**            | Контейнер Elastic Beanstalk для application versions, environments і saved configurations.          |
| **Application Version**    | Версія пакета застосунку, завантажена в Elastic Beanstalk і доступна для розгортання в environment. |
| **Environment**            | Набір AWS-ресурсів Elastic Beanstalk, на якому працює конкретна версія застосунку.                  |
| **Web/Worker Tier**        | Web tier обслуговує HTTP requests; worker tier обробляє фонові повідомлення, зазвичай із SQS.       |
| **Platform**               | Набір OS, runtime та web server, на основі якого Beanstalk запускає застосунок.                     |
| **Configuration Template** | Збережена конфігурація environment, яку можна повторно застосувати.                                 |
| **Environment Variables**  | Параметри, які Beanstalk передає застосунку під час виконання.                                      |
| **.ebextensions**          | Каталог YAML/JSON конфігурацій для налаштування ресурсів та EC2 environment.                        |
| **.platform**              | Каталог platform hooks і конфігурацій для сучасних Beanstalk platforms.                             |
| **Rolling**                | Deployment policy, що оновлює instances групами, зберігаючи частину старої версії доступною.        |
| **Immutable**              | Deployment policy, що створює нові instances з новою версією і перемикає їх після перевірки.        |
| **Blue/Green**             | Два окремі environments: нову версію тестують і перемикають CNAME/traffic після перевірки.          |
| **All-at-once**            | Deployment policy, що одночасно оновлює всі instances і може спричинити downtime.                   |

**Типовий екзаменаційний сценарій:** Потрібно розгорнути web app без
ручного створення всіх EC2/ELB/ASG компонентів → Elastic Beanstalk.

**Екзаменаційна пастка:** Beanstalk керує середовищем, але не є окремою
мовою чи runtime. Worker environment часто інтегрується із SQS.

------------------------------------------------------------------------

## AWS Lambda

**Призначення:** Serverless compute для виконання коду у відповідь на
події або API-виклики.

### Ключові терміни

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

**Типовий екзаменаційний сценарій:** Подієвий код без керування
серверами → Lambda.

**Екзаменаційна пастка:** Execution Role визначає доступ функції до AWS;
resource policy визначає, хто може її викликати. Reserved і Provisioned
Concurrency — різні речі.

------------------------------------------------------------------------
