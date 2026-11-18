# DVA-C02 — міжсервісні порівняння та екзаменаційні сценарії

## Домени іспиту

Відсотки нижче наведені як структура доменів у відповідній версії exam
guide; перед іспитом звіряйте їх з актуальним офіційним guide.

| Домен                            | Частка |
|----------------------------------|-------:|
| Development with AWS Services    |    32% |
| Security                         |    26% |
| Deployment                       |    24% |
| Troubleshooting and Optimization |    18% |

## Сервіс за вимогою

| Вимога в задачі                                   | Найімовірніший сервіс                                    |
|---------------------------------------------------|----------------------------------------------------------|
| Подієвий serverless код                           | AWS Lambda                                               |
| HTTP API front door                               | API Gateway                                              |
| GraphQL API та realtime subscriptions             | AWS AppSync                                              |
| Черга для асинхронного decoupling                 | Amazon SQS                                               |
| Pub/sub fan-out                                   | Amazon SNS                                               |
| Маршрутизація подій за payload/schedule           | Amazon EventBridge                                       |
| Багатокрокова оркестрація                         | AWS Step Functions                                       |
| Потік записів із контролем shard/consumer         | Kinesis Data Streams                                     |
| Керована доставка потоку до S3/інших destinations | Amazon Data Firehose                                     |
| SQL-запити до даних у S3                          | Amazon Athena                                            |
| Повнотекстовий пошук і log analytics              | Amazon OpenSearch Service                                |
| Key-value/document database                       | Amazon DynamoDB                                          |
| Реляційна база даних                              | Amazon RDS або Aurora                                    |
| Спільне POSIX file storage                        | Amazon EFS                                               |
| Блоковий диск для EC2                             | Amazon EBS                                               |
| Object storage                                    | Amazon S3                                                |
| Кеш у пам’яті                                     | Amazon ElastiCache або DynamoDB DAX залежно від сценарію |
| Секрети з автоматичною ротацією                   | AWS Secrets Manager                                      |
| Параметри конфігурації та feature flags           | Systems Manager Parameter Store або AWS AppConfig        |
| Інфраструктура як код                             | AWS CloudFormation або AWS CDK                           |
| Build/test у CI                                   | AWS CodeBuild                                            |
| Pipeline release orchestration                    | AWS CodePipeline                                         |
| Deployment на EC2/on-premises/Lambda/ECS          | AWS CodeDeploy                                           |
| Container image registry                          | Amazon ECR                                               |
| Container orchestration                           | Amazon ECS або Amazon EKS                                |
| DNS routing                                       | Amazon Route 53                                          |
| CDN і edge caching                                | Amazon CloudFront                                        |
| Layer 7 HTTP load balancing                       | Application Load Balancer                                |
| Layer 4 network load balancing                    | Network Load Balancer                                    |
| Audit API activity                                | AWS CloudTrail                                           |
| Metrics, logs і alarms                            | Amazon CloudWatch                                        |
| Distributed tracing                               | AWS X-Ray                                                |
| Тимчасові AWS credentials / role assumption       | AWS STS                                                  |
| Permission management                             | AWS IAM                                                  |
| Ключі та криптографічні операції                  | AWS KMS                                                  |
| Web application firewall                          | AWS WAF                                                  |

## Важливі відмінності

| Пара сервісів/понять                     | Як розрізняти                                                                                                                                              |
|------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------|
| SNS vs SQS                               | SNS — pub/sub push fan-out; SQS — durable queue, з якої consumer забирає повідомлення.                                                                     |
| EventBridge vs SNS                       | EventBridge маршрутизує події за event patterns/schedules; SNS — простий pub/sub topic.                                                                    |
| Kinesis Data Streams vs Data Firehose    | Streams дає контроль над shard і consumer processing; Firehose керує буферизацією та доставкою до destination.                                             |
| DynamoDB Query vs Scan                   | Query використовує partition key; Scan переглядає таблицю/індекс і часто дорожчий.                                                                         |
| DynamoDB GSI vs LSI                      | GSI має інший partition key і може бути доданий після створення таблиці; LSI використовує той самий partition key і створюється під час створення таблиці. |
| DynamoDB Streams vs Kinesis              | DynamoDB Streams фіксує зміни таблиці; Kinesis Data Streams — загальний сервіс потокових записів.                                                          |
| Lambda execution role vs resource policy | Execution role визначає, що функція може робити; resource policy — хто може викликати функцію.                                                             |
| Reserved vs Provisioned Concurrency      | Reserved обмежує/резервує concurrency; Provisioned заздалегідь готує execution environments.                                                               |
| EBS vs EFS vs S3                         | EBS — block storage для EC2; EFS — спільна файлова система; S3 — object storage через API.                                                                 |
| RDS Multi-AZ vs Read Replica             | Multi-AZ — доступність/failover; Read Replica — масштабування читання (залежно від engine/configuration).                                                  |
| Security Group vs NACL                   | Security Group stateful і працює на ENI; NACL stateless і працює на subnet.                                                                                |
| IAM role vs IAM user                     | Role надає тимчасові credentials через AssumeRole; user може мати довготривалі credentials.                                                                |
| CloudWatch vs CloudTrail                 | CloudWatch — operational monitoring; CloudTrail — аудит хто і які AWS API calls виконав.                                                                   |
| Secrets Manager vs Parameter Store       | Secrets Manager орієнтований на secrets та rotation; Parameter Store — ієрархічні параметри й SecureString.                                                |
| API Gateway vs ALB                       | API Gateway — API management/auth/throttling; ALB — балансування HTTP(S) traffic до targets.                                                               |
| CodeDeploy vs CodePipeline               | CodeDeploy виконує deployment; CodePipeline оркеструє весь release workflow.                                                                               |

## Підхід до ситуаційних питань

1.  Визначте головну вимогу: latency, durability, ordering,
    availability, security, deployment чи cost.
2.  Відкиньте сервіси, які не відповідають моделі взаємодії (queue,
    pub/sub, stream, API, database).
3.  Перевірте важливі обмеження: ordering, delivery guarantees,
    consistency, retry, timeout та payload size.
4.  Виберіть найменш складне рішення, яке повністю задовольняє вимоги
    задачі.
5.  Перевірте IAM: хто викликає сервіс, яку роль assume і які resource
    policies потрібні.
