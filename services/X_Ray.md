# AWS X-Ray

**Категорія:** Developer Tools  
**Призначення:** Distributed tracing для аналізу шляху запиту через
сервіси.

## Словник термінів

| Термін              | Визначення українською                                                                                                |
|---------------------|-----------------------------------------------------------------------------------------------------------------------|
| **Trace**           | Набір пов’язаних даних X-Ray про шлях одного запиту через розподілену систему.                                        |
| **Segment**         | Частина X-Ray trace, що описує роботу одного сервісу або компонента під час обробки запиту.                           |
| **Subsegment**      | Вкладена частина segment, що деталізує операцію, наприклад виклик БД або HTTP-запит.                                  |
| **Trace ID**        | Глобальний ідентифікатор trace, що пов’язує сегменти одного запиту між сервісами.                                     |
| **Sampling**        | Вибірковий запис traces для контролю обсягу telemetry та вартості.                                                    |
| **Sampling Rule**   | Правило, що визначає, які запити записувати, на основі service, URL, HTTP method та інших умов.                       |
| **Annotation**      | Індексовані структуровані поля X-Ray trace, які можна використовувати у фільтрах пошуку.                              |
| **Metadata**        | Додаткові довільні дані X-Ray trace, які зберігаються для діагностики, але не індексуються для пошуку як annotations. |
| **Service Map**     | Візуалізація сервісів і залежностей, побудована на основі X-Ray traces.                                               |
| **Trace Context**   | Контекст поточного trace, який передається між сервісами для кореляції distributed request.                           |
| **Instrumentation** | Додавання SDK, agent або автоматичної інструментації для збору trace data.                                            |

## Типовий екзаменаційний сценарій

Потрібно знайти, який сервіс спричиняє latency у distributed request →
X-Ray.

## Екзаменаційна пастка

CloudWatch — metrics/logs/alarms; X-Ray — trace одного запиту та
залежностей.

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

- [AWS Documentation — AWS X-Ray](https://docs.aws.amazon.com/)
- [DVA-C02 Exam
  Guide](https://docs.aws.amazon.com/aws-certification/latest/developer-associate-02/developer-associate-02.html)
