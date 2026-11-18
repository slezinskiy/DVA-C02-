# Amazon Cognito

**Категорія:** Security, Identity, and Compliance  
**Призначення:** Керування автентифікацією користувачів і федерацією
identity providers для застосунків.

## Словник термінів

| Термін                      | Визначення українською                                                                                              |
|-----------------------------|---------------------------------------------------------------------------------------------------------------------|
| **User Pool**               | Amazon Cognito каталог користувачів для реєстрації, входу, керування профілями та видачі JWT.                       |
| **Identity Pool**           | Cognito компонент, який обмінює автентифіковану або гостьову identity на тимчасові AWS credentials через IAM roles. |
| **App Client**              | Ідентифікатор застосунку в User Pool із налаштуваннями OAuth flows, callback URLs, token validity та client secret. |
| **Hosted UI**               | Готовий Cognito web interface для signup/signin та OAuth authorization flow.                                        |
| **User Attributes**         | Стандартні й custom поля профілю користувача, наприклад email, phone_number або custom attributes.                  |
| **Groups**                  | Логічні групи користувачів User Pool, які можуть брати участь у role mapping та authorization.                      |
| **Federation**              | Автентифікація користувачів через зовнішніх identity providers, наприклад Google, SAML або OIDC.                    |
| **OIDC/SAML**               | Стандарти федеративної identity: OIDC використовує OAuth 2.0/JWT, SAML — XML assertions.                            |
| **JWT**                     | JSON Web Token — підписаний токен із claims, який передає твердження про користувача або авторизаційний контекст.   |
| **ID/Access/Refresh Token** | ID token описує identity, access token містить authorization scopes, refresh token дозволяє отримувати нові токени. |
| **MFA**                     | Multi-Factor Authentication — додатковий фактор входу, наприклад TOTP або SMS залежно від налаштувань.              |
| **Lambda Triggers**         | Cognito lifecycle hooks, які викликають Lambda під час signup, authentication і генерації токенів.                  |
| **Role Mapping**            | Правила Identity Pool, що зіставляють claims/groups із IAM roles.                                                   |

## Типовий екзаменаційний сценарій

Потрібні sign-up/sign-in та JWT → User Pool; потрібні тимчасові AWS
credentials користувачеві → Identity Pool.

## Екзаменаційна пастка

User Pool автентифікує; Identity Pool видає AWS credentials. Це різні
функції.

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

- [AWS Documentation — Amazon Cognito](https://docs.aws.amazon.com/)
- [DVA-C02 Exam
  Guide](https://docs.aws.amazon.com/aws-certification/latest/developer-associate-02/developer-associate-02.html)
