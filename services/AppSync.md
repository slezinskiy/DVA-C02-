# AWS AppSync

**Категорія:** Application Integration  
**Призначення:** Керований GraphQL API, що об’єднує джерела даних і
підтримує realtime subscriptions.

## Словник термінів

| Термін                 | Визначення українською                                                                                                     |
|------------------------|----------------------------------------------------------------------------------------------------------------------------|
| **GraphQL**            | Мова запитів до API, де клієнт описує потрібні поля та структуру відповіді.                                                |
| **Schema**             | Контракт GraphQL API: типи, поля, аргументи та доступні операції.                                                          |
| **Query**              | GraphQL операція читання даних, яка повертає запитані клієнтом поля.                                                       |
| **Mutation**           | GraphQL операція для створення, оновлення або видалення даних.                                                             |
| **Subscription**       | GraphQL операція для отримання realtime updates від AppSync.                                                               |
| **Resolver**           | Логіка, яка отримує значення конкретного поля GraphQL із data source або обчислює його.                                    |
| **Data Source**        | Backend, до якого AppSync звертається для читання або зміни даних, наприклад DynamoDB, Lambda або HTTP endpoint.           |
| **Pipeline Resolver**  | Resolver AppSync, який послідовно запускає кілька functions, передаючи між ними context і результат.                       |
| **VTL**                | Velocity Template Language — шаблонна мова, яку AppSync використовує в resolver request/response mapping templates.        |
| **APPSYNC_JS**         | JavaScript runtime AppSync для написання resolver і pipeline functions.                                                    |
| **Authorization Mode** | Спосіб автентифікації/авторизації запитів AppSync, наприклад API key, IAM, Cognito User Pools, OIDC або Lambda authorizer. |
| **Conflict Detection** | Механізм AppSync для виявлення одночасних змін одного запису та застосування обраної стратегії розв’язання конфліктів.     |

## Типовий екзаменаційний сценарій

Клієнту потрібен GraphQL API з realtime оновленнями → AppSync.

## Екзаменаційна пастка

GraphQL — API-модель, не база даних. User Pool і IAM — різні режими
авторизації.

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

- [AWS Documentation — AWS AppSync](https://docs.aws.amazon.com/)
- [DVA-C02 Exam
  Guide](https://docs.aws.amazon.com/aws-certification/latest/developer-associate-02/developer-associate-02.html)
