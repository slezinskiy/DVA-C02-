# AWS CloudFormation

**Категорія:** Management and Governance  
**Призначення:** IaC сервіс для декларативного створення й оновлення AWS
resources.

## Словник термінів

| Термін                  | Визначення українською                                                                                                        |
|-------------------------|-------------------------------------------------------------------------------------------------------------------------------|
| **Template**            | JSON/YAML декларативний опис AWS resources, parameters, conditions, mappings і outputs.                                       |
| **Stack**               | Керована група ресурсів, створена з template та оновлювана як одна одиниця.                                                   |
| **Resource**            | AWS ресурс, оголошений у секції Resources template; CloudFormation створює та керує його життєвим циклом.                     |
| **Parameter**           | Вхідне значення template, яке користувач передає під час створення чи оновлення stack.                                        |
| **Output**              | Значення, яке CloudFormation показує або експортує після deployment, наприклад ARN чи endpoint.                               |
| **Mapping**             | Опис типів полів і правил індексації документів у OpenSearch.                                                                 |
| **Condition**           | Логічний вираз, що визначає, чи створювати ресурс або застосовувати властивість.                                              |
| **Intrinsic Function**  | Вбудована функція template, наприклад Ref, Fn::GetAtt, Fn::Sub або Fn::Join, для посилань та обчислень.                       |
| **Change Set**          | Попередній план змін CloudFormation stack, який показує, які ресурси буде створено, змінено або видалено до виконання update. |
| **Drift Detection**     | Механізм CloudFormation, який порівнює фактичну конфігурацію ресурсів із конфігурацією, описаною у template.                  |
| **Stack Policy**        | JSON policy, що обмежує, які ресурси дозволено змінювати під час stack update.                                                |
| **DeletionPolicy**      | Атрибут, який визначає долю ресурсу при видаленні зі stack: Delete, Retain або Snapshot (де підтримується).                   |
| **UpdateReplacePolicy** | Атрибут, який визначає долю старого фізичного ресурсу, коли update вимагає його заміни.                                       |
| **DependsOn**           | Атрибут, що задає явну залежність і порядок створення/видалення ресурсів.                                                     |
| **Nested Stack**        | CloudFormation stack, вкладений як resource в інший stack для модульної організації template.                                 |
| **StackSet**            | Механізм розгортання template у багатьох AWS accounts і Regions.                                                              |
| **Custom Resource**     | Ресурс із користувацькою логікою provisioning, яку реалізує Lambda або SNS-backed provider.                                   |
| **Rollback**            | Повернення stack до попереднього стану після невдалого create/update.                                                         |

## Типовий екзаменаційний сценарій

Потрібно повторювано створювати інфраструктуру з template →
CloudFormation.

## Екзаменаційна пастка

Drift — різниця між template і фактичним ресурсом. Retain зберігає
ресурс після видалення stack.

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

- [AWS Documentation — AWS CloudFormation](https://docs.aws.amazon.com/)
- [DVA-C02 Exam
  Guide](https://docs.aws.amazon.com/aws-certification/latest/developer-associate-02/developer-associate-02.html)
