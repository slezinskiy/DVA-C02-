# DVA-C02 — міжсервісні порівняння та екзаменаційні сценарії

## Домени іспиту

| Домен                            | Частка |
|----------------------------------|-------:|
| Development with AWS Services    |    32% |
| Security                         |    26% |
| Deployment                       |    24% |
| Troubleshooting and Optimization |    18% |

## Сервіс за вимогою

| Вимога                             | Сервіс                      |
|------------------------------------|-----------------------------|
| Подієвий serverless код            | Lambda                      |
| HTTP API front door                | API Gateway                 |
| GraphQL API                        | AppSync                     |
| Черга для асинхронного decoupling  | SQS                         |
| Pub/sub fan-out                    | SNS                         |
| Event routing за payload           | EventBridge                 |
| Багатокрокова оркестрація          | Step Functions              |
| Потокові дані з consumer control   | Kinesis Data Streams        |
| Керована доставка потоку           | Kinesis Data Firehose       |
| SQL по даних S3                    | Athena                      |
| Повнотекстовий пошук               | OpenSearch                  |
| Key-value/document database        | DynamoDB                    |
| Реляційна база                     | RDS/Aurora                  |
| Загальний in-memory cache          | ElastiCache                 |
| DynamoDB cache                     | DAX                         |
| Container image registry           | ECR                         |
| AWS-native container orchestration | ECS                         |
| Kubernetes                         | EKS                         |
| Віртуальний сервер                 | EC2                         |
| Platform-managed deployment        | Elastic Beanstalk           |
| CDN                                | CloudFront                  |
| DNS                                | Route 53                    |
| HTTP path/host routing             | ALB                         |
| TCP/UDP load balancing             | NLB                         |
| Identity та AWS permissions        | IAM                         |
| User sign-in                       | Cognito User Pool           |
| Temporary AWS credentials          | STS / Cognito Identity Pool |
| Encryption keys                    | KMS                         |
| Secret rotation                    | Secrets Manager             |
| Web request filtering              | WAF                         |
| Build/test                         | CodeBuild                   |
| Deployment                         | CodeDeploy                  |
| CI/CD orchestration                | CodePipeline                |
| IaC template deployment            | CloudFormation              |
| IaC using programming languages    | CDK                         |
| API audit                          | CloudTrail                  |
| Metrics/logs/alarms                | CloudWatch                  |
| Distributed tracing                | X-Ray                       |
| Remote command/session             | Systems Manager             |
| Application config rollout         | AppConfig                   |
| Block storage                      | EBS                         |
| Shared file system                 | EFS                         |
| Object storage                     | S3                          |

## Ключові порівняння

### SNS vs SQS vs EventBridge

| Критерій       | SNS                 | SQS                              | EventBridge    |
|----------------|---------------------|----------------------------------|----------------|
| Модель         | Pub/sub             | Queue                            | Event bus      |
| Мета           | Fan-out             | Buffering/decoupling             | Event routing  |
| Фільтрація     | Subscription filter | Зазвичай у consumer              | Event pattern  |
| Replay/archive | Не основна функція  | Повідомлення живуть до retention | Archive/replay |

### CloudTrail vs CloudWatch vs X-Ray

| Сервіс     | Питання                                       |
|------------|-----------------------------------------------|
| CloudTrail | Хто виконав AWS API дію?                      |
| CloudWatch | Які метрики та логи показують стан?           |
| X-Ray      | Де запит витратив час у розподіленій системі? |

### Cognito User Pool vs Identity Pool

- User Pool автентифікує користувачів і видає JWT.
- Identity Pool видає тимчасові AWS credentials через IAM roles.
- Для доступу до AWS resources застосунку потрібна відповідна IAM
  policy.

### Security Group vs NACL

- Security Group — stateful, на рівні ENI/ресурсу, лише allow rules.
- NACL — stateless, на рівні subnet, allow і deny rules.
- Для NACL потрібно явно дозволяти потрібний зворотний трафік.

### ALB vs NLB

- ALB: HTTP/HTTPS, path/host/header routing, Layer 7.
- NLB: TCP/UDP/TLS, Layer 4, висока продуктивність і низька затримка.

### RDS Multi-AZ vs Read Replica

- Multi-AZ — доступність і failover.
- Read Replica — масштабування читання.
- Не вважайте standby у класичному Multi-AZ deployment звичайною read
  replica.

### CodeBuild vs CodeDeploy vs CodePipeline

- CodeBuild — build і test.
- CodeDeploy — deployment.
- CodePipeline — оркестрація source/build/test/deploy stages.

### S3 vs EBS vs EFS

- S3 — object storage.
- EBS — block storage для EC2.
- EFS — shared network file system через NFS.

## Екзаменаційні пастки

1.  SQS receive не видаляє повідомлення — після успішної обробки
    потрібен DeleteMessage.
2.  SQS може повторно доставити повідомлення — потрібна idempotency.
3.  Visibility Timeout має покривати час обробки повідомлення.
4.  DLQ ізолює невдалі повідомлення, але не виправляє їх.
5.  SNS + SQS — типовий fan-out pattern з окремими чергами consumer.
6.  EventBridge маршрутизує події; SQS буферизує роботу.
7.  Lambda execution role і Lambda resource policy мають різне
    призначення.
8.  Lambda у VPC не отримує автоматично outbound internet access.
9.  API Gateway API key не є повноцінною автентифікацією.
10. KMS Key Policy потрібно перевіряти разом з IAM permissions.
11. Secrets Manager rotation потребує коректної логіки застосунку.
12. CloudTrail — аудит API; CloudWatch Logs — application/system logs.
13. X-Ray — tracing, а не заміна metrics.
14. CloudFormation drift означає різницю між template та фактичним
    ресурсом.
15. ECR зберігає images; ECS/EKS запускають workloads.
16. ECS Task Role — для коду; Task Execution Role — для ECS/Fargate
    agent.
17. Security Group stateful, NACL stateless.
18. Gateway VPC Endpoint призначений для S3 і DynamoDB; інші сервіси
    часто використовують Interface Endpoint.
19. S3 має strong read-after-write consistency для PUT/DELETE.
20. CloudFront OAC — сучасний рекомендований механізм доступу до
    приватного S3 origin.
21. DynamoDB GSI не підтримує strongly consistent reads.
22. DynamoDB FilterExpression не зменшує прочитану capacity.
23. DynamoDB TTL видаляє items асинхронно.
24. DynamoDB BatchWriteItem не є атомарною транзакцією.
25. DAX — спеціалізований кеш DynamoDB; ElastiCache — загальний кеш.

## Базові терміни

| Термін                | Пояснення                                                        |
|-----------------------|------------------------------------------------------------------|
| API                   | Контракт взаємодії між компонентами.                             |
| SDK                   | Бібліотека для виклику AWS APIs із коду.                         |
| ARN                   | Amazon Resource Name — ідентифікатор AWS ресурсу.                |
| Region                | Географічний регіон AWS.                                         |
| Availability Zone     | Ізольована зона доступності в регіоні.                           |
| Idempotency           | Повтор запиту не створює небажаних додаткових змін.              |
| Exponential Backoff   | Збільшення часу між retry.                                       |
| Jitter                | Випадкове відхилення retry delay.                                |
| Throttling            | Обмеження запитів через перевищення пропускної здатності/ліміту. |
| DLQ                   | Черга для повідомлень, які не вдалося обробити.                  |
| Encryption at Rest    | Шифрування даних у сховищі.                                      |
| Encryption in Transit | Шифрування даних під час передачі.                               |
| Least Privilege       | Мінімально необхідні дозволи.                                    |
| CI/CD                 | Continuous Integration / Continuous Delivery або Deployment.     |
| Artifact              | Файл/пакет, що передається між build і deploy.                   |
| Canary                | Поступове введення нової версії для частини трафіку.             |
| Blue/Green            | Два середовища з перемиканням трафіку.                           |
| RTO                   | Максимально допустимий час відновлення.                          |
| RPO                   | Максимально допустима втрата даних у часовому вимірі.            |

## Чекліст

- [ ] Розрізняю SNS, SQS, EventBridge і Step Functions.
- [ ] Розумію sync, async та poll-based Lambda invocations.
- [ ] Розрізняю execution role, resource policy і trust policy.
- [ ] Розумію Cognito User Pool та Identity Pool.
- [ ] Розрізняю S3, EBS, EFS, RDS, DynamoDB та ElastiCache.
- [ ] Розумію DynamoDB keys, indexes, Query/Scan, consistency, TTL і
  Streams.
- [ ] Розумію KMS, Secrets Manager і STS.
- [ ] Розрізняю CodeBuild, CodeDeploy та CodePipeline.
- [ ] Розрізняю CloudTrail, CloudWatch і X-Ray.
- [ ] Розрізняю ECR, ECS та EKS.
- [ ] Розумію ALB/NLB, SG/NACL та VPC endpoints.
- [ ] Знаю retry, backoff, jitter, idempotency та DLQ.

## Офіційні джерела

- [DVA-C02 Exam
  Guide](https://docs.aws.amazon.com/aws-certification/latest/developer-associate-02/developer-associate-02.html)
- [In-Scope AWS
  Services](https://docs.aws.amazon.com/aws-certification/latest/developer-associate-02/dva-02-in-scope-services.html)
- [Domain 1 —
  Development](https://docs.aws.amazon.com/aws-certification/latest/developer-associate-02/developer-associate-02-domain1.html)
- [Domain 2 —
  Security](https://docs.aws.amazon.com/aws-certification/latest/developer-associate-02/developer-associate-02-domain2.html)
- [Domain 3 —
  Deployment](https://docs.aws.amazon.com/aws-certification/latest/developer-associate-02/developer-associate-02-domain3.html)
- [Domain 4 — Troubleshooting and
  Optimization](https://docs.aws.amazon.com/aws-certification/latest/developer-associate-02/developer-associate-02-domain4.html)
