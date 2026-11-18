# Amazon CloudWatch

**Категорія:** Management and Governance  
**Призначення:** Моніторинг metrics, logs, alarms, dashboards і
operational telemetry.

## Словник термінів

| Термін                  | Визначення українською                                                                                                         |
|-------------------------|--------------------------------------------------------------------------------------------------------------------------------|
| **Metric**              | Числовий показник, виміряний у часі, наприклад CPU utilization або кількість помилок.                                          |
| **Namespace**           | Логічний контейнер CloudWatch metrics, який розділяє метрики за сервісом або застосунком.                                      |
| **Dimension**           | Пара атрибут-значення, що ідентифікує конкретний ресурс або варіант метрики.                                                   |
| **Statistic**           | Агрегат метрики за період: Average, Sum, Minimum, Maximum або SampleCount.                                                     |
| **Period**              | Часовий інтервал, за який CloudWatch агрегує datapoints для графіка або alarm.                                                 |
| **Resolution**          | Частота metric datapoints; custom metrics можуть мати standard або high resolution.                                            |
| **Custom Metric**       | Метрика, яку застосунок публікує в CloudWatch через API або Embedded Metric Format.                                            |
| **Log Group**           | Контейнер CloudWatch Logs для log streams зі спільними налаштуваннями retention та permissions.                                |
| **Log Stream**          | Послідовність log events від одного джерела або екземпляра джерела всередині log group.                                        |
| **Log Event**           | Окремий запис CloudWatch Logs із timestamp і message.                                                                          |
| **Retention**           | Період зберігання log events у log group, після якого старі записи видаляються.                                                |
| **Metric Filter**       | Правило CloudWatch Logs, що знаходить шаблони в log events і перетворює збіги на CloudWatch metric.                            |
| **Subscription Filter** | Фільтр, який передає відповідні log events у Lambda, Kinesis або Firehose.                                                     |
| **Logs Insights**       | Query engine для пошуку, фільтрації та агрегації CloudWatch Logs.                                                              |
| **Alarm**               | CloudWatch об’єкт, який порівнює metric або expression із порогом/умовою та переходить у стан OK, ALARM або INSUFFICIENT_DATA. |
| **Composite Alarm**     | Alarm, який комбінує стани інших alarms логічним виразом.                                                                      |
| **Dashboard**           | Панель CloudWatch із графіками, alarms та віджетами для спостереження.                                                         |
| **Anomaly Detection**   | Функція, яка навчається на історії метрики та формує очікуваний діапазон значень.                                              |
| **Agent**               | CloudWatch Agent, що збирає системні metrics і logs із EC2/on-premises servers.                                                |
| **EMF**                 | Embedded Metric Format — JSON формат log events, з якого CloudWatch автоматично витягує custom metrics.                        |

## Типовий екзаменаційний сценарій

Потрібно створити alarm за помилками або latency → CloudWatch.

## Екзаменаційна пастка

Metric Filter перетворює логи на метрики; X-Ray — окремий distributed
tracing сервіс.

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

- [AWS Documentation — Amazon CloudWatch](https://docs.aws.amazon.com/)
- [DVA-C02 Exam
  Guide](https://docs.aws.amazon.com/aws-certification/latest/developer-associate-02/developer-associate-02.html)
