# Amazon API Gateway

**Категорія:** Networking and Content Delivery  
**Призначення:** Керований сервіс для створення, захисту та публікації
REST, HTTP і WebSocket APIs.

## Словник термінів

| Термін            | Визначення українською                                                                                                                             |
|-------------------|----------------------------------------------------------------------------------------------------------------------------------------------------|
| **REST API**      | API Gateway REST API (v1) — ресурсно-орієнтований API з resources, methods, stages, authorizers та integrations.                                   |
| **HTTP API**      | Полегшений API Gateway тип для HTTP workloads із нижчою latency/вартістю; підтримує Lambda/HTTP integrations та JWT/Lambda authorizers.            |
| **WebSocket API** | API для двостороннього постійного з’єднання клієнта із сервером через WebSocket.                                                                   |
| **Resource**      | Шлях/ресурс REST API, який формує endpoint і містить methods, наприклад /orders/{id}.                                                              |
| **Method**        | HTTP-операція на resource (GET, POST, PUT, DELETE) з налаштуваннями authorization та integration.                                                  |
| **Route**         | Правило HTTP/WebSocket API, яке зіставляє запит із backend integration.                                                                            |
| **Integration**   | Зв’язок API Gateway із backend: Lambda, HTTP endpoint, AWS service або mock.                                                                       |
| **Lambda Proxy**  | Режим, у якому API Gateway передає Lambda request/context і очікує від неї HTTP response у визначеному форматі.                                    |
| **Stage**         | Розгорнуте середовище API Gateway, наприклад dev або prod, що посилається на конкретний deployment.                                                |
| **Deployment**    | Kubernetes controller, який керує ReplicaSets і підтримує бажану кількість Pod, rollout та rollback.                                               |
| **Authorizer**    | Компонент API Gateway/AppSync, який перевіряє identity та дозволи запиту перед його передаванням до backend.                                       |
| **IAM Auth**      | Авторизація через AWS SigV4; викликач повинен мати iam:execute-api:Invoke permission.                                                              |
| **API Key**       | Ключ для ідентифікації клієнта у usage plan та обліку quota/throttling; не замінює надійну автентифікацію.                                         |
| **Usage Plan**    | Налаштування API Gateway REST API, що пов’язує API keys із quota та throttling limits. API key сам по собі не є механізмом сильної автентифікації. |
| **Throttling**    | Обмеження швидкості запитів за rate і burst limits для захисту API та backend.                                                                     |
| **Quota**         | Ліміт кількості запитів за певний період у usage plan.                                                                                             |
| **CORS**          | Cross-Origin Resource Sharing — механізм браузера для дозволу запитів із іншого origin.                                                            |
| **Custom Domain** | Власне доменне ім’я для API Gateway, налаштоване з TLS certificate та DNS mapping.                                                                 |
| **Private API**   | REST API, доступний через interface VPC endpoint, а не з публічного інтернету.                                                                     |
| **Access Logs**   | Журнали запитів API Gateway із request ID, status, latency та іншими вибраними полями.                                                             |

## Типовий екзаменаційний сценарій

Потрібен керований API front door із throttling/auth/stages → API
Gateway.

## Екзаменаційна пастка

API key не є повноцінною автентифікацією. Lambda Function URL простіший,
але має менше API management features.

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

- [AWS Documentation — Amazon API Gateway](https://docs.aws.amazon.com/)
- [DVA-C02 Exam
  Guide](https://docs.aws.amazon.com/aws-certification/latest/developer-associate-02/developer-associate-02.html)
