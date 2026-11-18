# Amazon ECS

**Категорія:** Containers  
**Призначення:** AWS-native оркестратор контейнерів на EC2 або Fargate.

## Словник термінів

| Термін                   | Визначення українською                                                                                                         |
|--------------------------|--------------------------------------------------------------------------------------------------------------------------------|
| **Cluster**              | Логічна група ECS tasks, services і capacity providers.                                                                        |
| **Task Definition**      | Шаблон ECS task: опис контейнерів, образів, CPU/memory, мережі, volumes, logging та IAM roles.                                 |
| **Task**                 | Запущений екземпляр ECS task definition, який містить один або кілька контейнерів.                                             |
| **Service**              | Контролер ECS, що підтримує desired count tasks і керує їх deployments та load balancing.                                      |
| **Container Definition** | Опис одного контейнера в task definition: image, ports, resources, environment, logging і secrets.                             |
| **EC2 Launch Type**      | Режим ECS, де tasks розміщуються на EC2 instances, якими керує користувач.                                                     |
| **Fargate**              | Serverless compute engine для контейнерів, де AWS керує серверами, а користувач задає ресурси task.                            |
| **Capacity Provider**    | Механізм ECS для визначення способу надання capacity через Fargate або EC2 Auto Scaling.                                       |
| **Desired Count**        | Кількість tasks, яку ECS service має підтримувати.                                                                             |
| **Deployment**           | Процес заміни старих tasks новою revision task definition.                                                                     |
| **Task Role**            | IAM role, доступна коду всередині ECS task для звернення до AWS services.                                                      |
| **Task Execution Role**  | IAM role, яку ECS agent/Fargate використовує для запуску task: завантаження image з ECR, надсилання logs та отримання secrets. |
| **awsvpc**               | ECS network mode, у якому кожен task отримує власний ENI та приватну IP-адресу.                                                |
| **Service Discovery**    | Інтеграція ECS із AWS Cloud Map для виявлення tasks через DNS/API.                                                             |
| **Health Check**         | Перевірка стану container або load balancer target, що впливає на заміну task і routing.                                       |
| **Service Auto Scaling** | Автоматична зміна desired count ECS service на основі CloudWatch metrics/policies.                                             |
| **ECS Exec**             | Механізм запуску команд у працюючому контейнері ECS через захищений канал.                                                     |

## Типовий екзаменаційний сценарій

Потрібно запускати контейнери без Kubernetes control plane → ECS.

## Екзаменаційна пастка

Task Role належить застосунку в контейнері; Task Execution Role потрібна
агенту ECS для pull image, logs та startup secrets.

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

- [AWS Documentation — Amazon ECS](https://docs.aws.amazon.com/)
- [DVA-C02 Exam
  Guide](https://docs.aws.amazon.com/aws-certification/latest/developer-associate-02/developer-associate-02.html)
