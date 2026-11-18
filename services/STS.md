# AWS STS

**Категорія:** Security, Identity, and Compliance  
**Призначення:** Видача тимчасових security credentials для ролей,
федерації та cross-account access.

## Словник термінів

| Термін                        | Визначення українською                                                                                                          |
|-------------------------------|---------------------------------------------------------------------------------------------------------------------------------|
| **Temporary Credentials**     | Короткоживучі credentials: access key ID, secret access key і session token.                                                    |
| **AssumeRole**                | Операція AWS STS, яка дозволяє principal отримати тимчасові credentials для IAM role за умови довіри та дозволів.               |
| **AssumeRoleWithWebIdentity** | STS API, який обмінює OIDC web identity token на тимчасові credentials IAM role.                                                |
| **AssumeRoleWithSAML**        | STS API, який обмінює SAML assertion на тимчасові credentials IAM role.                                                         |
| **GetSessionToken**           | STS API для отримання тимчасових credentials, зокрема для MFA-protected API sessions.                                           |
| **GetCallerIdentity**         | STS API, який повертає account, ARN і user ID поточного caller.                                                                 |
| **Role Session**              | Тимчасовий контекст після AssumeRole із власними credentials та строком дії.                                                    |
| **External ID**               | Додаткове значення в AssumeRole для cross-account access, яке допомагає захистити сторонній сервіс від confused deputy problem. |
| **Session Duration**          | Час дії тимчасових credentials role session у межах встановлених обмежень.                                                      |
| **Session Name**              | Ім’я role session, яке відображається в CloudTrail і допомагає ідентифікувати caller.                                           |
| **Session Policy**            | Додаткова policy для тимчасової session, яка звужує effective permissions.                                                      |
| **Web Identity Federation**   | Обмін зовнішнього OIDC token на AWS temporary credentials через STS.                                                            |

## Типовий екзаменаційний сценарій

Потрібен тимчасовий доступ до іншого AWS account → STS AssumeRole.

## Екзаменаційна пастка

Тимчасові credentials мають expiration і session token; External ID
часто застосовується для third-party cross-account access.

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

- [AWS Documentation — AWS STS](https://docs.aws.amazon.com/)
- [DVA-C02 Exam
  Guide](https://docs.aws.amazon.com/aws-certification/latest/developer-associate-02/developer-associate-02.html)
