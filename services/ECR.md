# Amazon ECR

**Категорія:** Containers  
**Призначення:** Керований registry для зберігання OCI/Docker container
images.

## Словник термінів

| Термін                   | Визначення українською                                                                                                   |
|--------------------------|--------------------------------------------------------------------------------------------------------------------------|
| **Registry**             | Приватний або публічний реєстр ECR, що містить repositories container images.                                            |
| **Repository**           | Логічне сховище CodeArtifact packages або ECR container images; конкретна структура залежить від сервісу.                |
| **Image**                | Незмінний пакет шарів і metadata, з якого запускається container.                                                        |
| **Tag**                  | Людиночитна мітка образу, наприклад v1.2; може вказувати на інший digest, якщо tags mutable.                             |
| **Digest**               | Криптографічний hash образу або артефакту, який ідентифікує точний вміст незалежно від tag.                              |
| **Layer**                | Окремий файловий шар container image, який може спільно використовуватися різними образами.                              |
| **Lifecycle Policy**     | Правила ECR для автоматичного expiration або архівування образів, наприклад видалення старих чи невикористовуваних tags. |
| **Image Scanning**       | Перевірка container images на відомі vulnerabilities у packages і залежностях.                                           |
| **Enhanced Scanning**    | Безперервне vulnerability scanning через Amazon Inspector із оновленням findings.                                        |
| **Repository Policy**    | Resource policy ECR repository, яка визначає доступ principals/accounts до push/pull.                                    |
| **Authentication Token** | Тимчасовий Docker password, отриманий через GetAuthorizationToken для login до ECR.                                      |
| **Cross-account Access** | Надання іншому AWS account дозволу push/pull через repository policy та IAM permissions.                                 |
| **Replication**          | Автоматичне копіювання ECR images між Regions або accounts.                                                              |

## Типовий екзаменаційний сценарій

ECS/EKS має завантажити приватний контейнерний образ → ECR плюс
IAM/repository policy.

## Екзаменаційна пастка

ECR зберігає образи, але не запускає контейнери.

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

- [AWS Documentation — Amazon ECR](https://docs.aws.amazon.com/)
- [DVA-C02 Exam
  Guide](https://docs.aws.amazon.com/aws-certification/latest/developer-associate-02/developer-associate-02.html)
