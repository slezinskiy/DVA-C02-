# AWS CodePipeline

**Категорія:** Developer Tools  
**Призначення:** Керований CI/CD pipeline, що з’єднує source, build,
test, approval та deploy actions.

## Словник термінів

| Термін                  | Визначення українською                                                                          |
|-------------------------|-------------------------------------------------------------------------------------------------|
| **Pipeline**            | Автоматизований workflow доставки змін від source через build/test до deploy.                   |
| **Stage**               | Послідовний етап pipeline, який містить actions і виконується у визначеному порядку.            |
| **Action**              | Операція всередині CodePipeline stage, наприклад Source, Build, Test, Approval або Deploy.      |
| **Source**              | Етап або provider pipeline, який отримує вихідний код/артефакт із Git, S3 чи іншого джерела.    |
| **Build**               | Етап CI, що компілює код, запускає тести та формує build artifacts.                             |
| **Deploy**              | Етап доставки application artifact до цільового середовища.                                     |
| **Artifact**            | Файл або набір файлів, переданий між actions/stages через artifact store.                       |
| **Artifact Store**      | S3 bucket, де CodePipeline зберігає artifacts між actions і stages.                             |
| **Approval**            | Manual approval action, що призупиняє pipeline до рішення уповноваженої особи.                  |
| **Change Detection**    | Механізм виявлення змін у source provider, який запускає нове pipeline execution.               |
| **Execution Mode**      | Режим обробки паралельних запусків pipeline: SUPERSEDED, QUEUED або PARALLEL.                   |
| **Cross-Region Action** | Action в іншому AWS Region; потребує належних permissions і artifact store у регіоні виконання. |

## Типовий екзаменаційний сценарій

Потрібен workflow від commit до deployment → CodePipeline.

## Екзаменаційна пастка

Pipeline складається з stages/actions; сам build може виконувати
CodeBuild.

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

- [AWS Documentation — AWS CodePipeline](https://docs.aws.amazon.com/)
- [DVA-C02 Exam
  Guide](https://docs.aws.amazon.com/aws-certification/latest/developer-associate-02/developer-associate-02.html)
