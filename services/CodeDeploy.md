# AWS CodeDeploy

**Категорія:** Developer Tools  
**Призначення:** Автоматизоване розгортання застосунків на EC2,
on-premises, Lambda та ECS.

## Словник термінів

| Термін                       | Визначення українською                                                                               |
|------------------------------|------------------------------------------------------------------------------------------------------|
| **Application**              | Логічний контейнер CodeDeploy для deployment groups і revisions.                                     |
| **Deployment Group**         | Набір targets і правил розгортання для CodeDeploy application.                                       |
| **Revision**                 | Версія пакета застосунку, яку CodeDeploy розгортає на targets.                                       |
| **AppSpec**                  | Файл, що описує файли, permissions, lifecycle hooks або deployment configuration.                    |
| **Lifecycle Event**          | Етап deployment, на якому CodeDeploy запускає визначені scripts/hooks.                               |
| **Hook**                     | Користувацький script або Lambda hook, що запускається на певному lifecycle event.                   |
| **In-place**                 | Оновлення застосунку на тих самих instances; під час deployment можлива тимчасова недоступність.     |
| **Blue/Green**               | Розгортання нової версії в окремому середовищі з подальшим перемиканням traffic.                     |
| **Canary**                   | Стратегія traffic shifting: спочатку невелика частка трафіку переходить на нову версію, потім решта. |
| **Linear**                   | Стратегія, що збільшує частку трафіку на нову версію рівними кроками через інтервали.                |
| **Rollback**                 | Повернення deployment до попередньої працездатної revision після помилки або за ручним запитом.      |
| **Deployment Configuration** | Параметри швидкості оновлення instances або traffic shifting під час deployment.                     |
| **Agent**                    | CodeDeploy agent на EC2/on-premises instance, який отримує deployment instructions і виконує їх.     |

## Типовий екзаменаційний сценарій

Потрібно контролювати rollout і lifecycle hooks → CodeDeploy.

## Екзаменаційна пастка

CodeDeploy розгортає; CodeBuild збирає; CodePipeline координує.

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

- [AWS Documentation — AWS CodeDeploy](https://docs.aws.amazon.com/)
- [DVA-C02 Exam
  Guide](https://docs.aws.amazon.com/aws-certification/latest/developer-associate-02/developer-associate-02.html)
