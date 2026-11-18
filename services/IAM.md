# AWS IAM

**Категорія:** Security, Identity, and Compliance  
**Призначення:** Керування principals, permissions, roles та policies
для AWS APIs і ресурсів.

## Словник термінів

| Термін                     | Визначення українською                                                                                                                |
|----------------------------|---------------------------------------------------------------------------------------------------------------------------------------|
| **Principal**              | Суб’єкт, від імені якого виконується AWS request: IAM user, role session, federated user або AWS service.                             |
| **User**                   | IAM identity для людини або застосунку; для AWS workloads зазвичай рекомендовано roles замість довготривалих user keys.               |
| **Group**                  | Колекція IAM users зі спільними identity-based policies.                                                                              |
| **Role**                   | IAM identity з permissions і trust policy, яку principal може assume для тимчасових credentials.                                      |
| **Policy**                 | JSON документ зі statements, що визначають Allow/Deny для actions, resources та conditions.                                           |
| **Identity-based**         | Policy, прикріплена до user/group/role і яка визначає permissions identity.                                                           |
| **Resource-based**         | Policy на самому resource, яка визначає, які principals можуть звертатися до нього.                                                   |
| **Trust Policy**           | Політика IAM role, що визначає, які principals можуть викликати sts:AssumeRole або іншу дозволену операцію отримання ролі.            |
| **Action**                 | Назва AWS API permission у policy, наприклад s3:GetObject.                                                                            |
| **Resource ARN**           | Amazon Resource Name, що ідентифікує resource у policy Resource element.                                                              |
| **Effect**                 | Значення Allow або Deny для policy statement.                                                                                         |
| **Condition**              | Додаткові умови застосування statement, наприклад source IP, MFA або resource tags.                                                   |
| **Explicit/Implicit Deny** | Explicit deny — пряма заборона; implicit deny — відсутність Allow. Explicit deny має пріоритет.                                       |
| **Least Privilege**        | Принцип надання лише мінімально необхідних permissions.                                                                               |
| **Managed/Inline Policy**  | Managed policy — окремий повторно використовуваний об’єкт; inline policy вбудована в одну identity.                                   |
| **Permission Boundary**    | Політика, яка задає максимальну множину permissions для IAM user або role; сама по собі не надає дозволів.                            |
| **Session Policy**         | Додаткова policy, що обмежує permissions тимчасової role session, але не розширює їх.                                                 |
| **ABAC**                   | Attribute-Based Access Control — модель доступу, у якій permissions визначаються атрибутами principals і resources, часто через tags. |
| **MFA**                    | Multi-Factor Authentication — додатковий фактор підтвердження identity.                                                               |
| **Access Key**             | Пара access key ID і secret access key для підписання AWS API requests; секретний ключ не можна розкривати.                           |
| **Instance Profile**       | Контейнер для IAM role, який прикріплюється до EC2 instance і надає тимчасові credentials застосункам на інстансі.                    |

## Типовий екзаменаційний сценарій

Lambda/EC2 має викликати AWS API → надати execution/instance role із
мінімальними permissions.

## Екзаменаційна пастка

Explicit Deny перекриває Allow. Не вбудовуйте довготривалі access keys у
код.

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

- [AWS Documentation — AWS IAM](https://docs.aws.amazon.com/)
- [DVA-C02 Exam
  Guide](https://docs.aws.amazon.com/aws-certification/latest/developer-associate-02/developer-associate-02.html)
