# AWS AppConfig

**Категорія:** Management and Governance  
**Призначення:** Кероване розповсюдження конфігурацій і feature flags
без повного redeploy.

## Словник термінів

| Термін                    | Визначення українською                                                                                   |
|---------------------------|----------------------------------------------------------------------------------------------------------|
| **Application**           | Логічний контейнер AppConfig для configuration profiles та environments одного застосунку.               |
| **Environment**           | Набір AWS-ресурсів Elastic Beanstalk, на якому працює конкретна версія застосунку.                       |
| **Configuration Profile** | Опис джерела конфігурації, її типу та validator у межах application.                                     |
| **Hosted Configuration**  | Конфігураційний документ, який зберігається безпосередньо в AWS AppConfig.                               |
| **Deployment Strategy**   | Налаштування швидкості поширення конфігурації, відсотків rollout та bake time.                           |
| **Gradual Deployment**    | Поступове розгортання конфігурації на частину targets із подальшим збільшенням охоплення.                |
| **Validator**             | Lambda function або JSON Schema, що перевіряє конфігурацію перед deployment.                             |
| **Feature Flag**          | Прапорець конфігурації, що вмикає або вимикає функціональність без зміни та повторного розгортання коду. |
| **Rollback**              | Повернення до попередньої конфігурації після помилок або спрацювання alarm thresholds.                   |
| **Agent**                 | AppConfig Agent, який отримує, кешує та надає конфігурацію локальному застосунку.                        |
| **Extension**             | Розширення AppConfig, яке запускає інтеграційні дії на певних етапах lifecycle.                          |

## Типовий екзаменаційний сценарій

Потрібно поступово змінювати runtime configuration/feature flags →
AppConfig.

## Екзаменаційна пастка

Parameter Store зберігає параметри; AppConfig керує контрольованим
rollout конфігурації.

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

- [AWS Documentation — AWS AppConfig](https://docs.aws.amazon.com/)
- [DVA-C02 Exam
  Guide](https://docs.aws.amazon.com/aws-certification/latest/developer-associate-02/developer-associate-02.html)
