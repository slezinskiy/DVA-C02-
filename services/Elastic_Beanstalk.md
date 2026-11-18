# AWS Elastic Beanstalk

**Категорія:** Compute  
**Призначення:** PaaS-подібний сервіс розгортання застосунків із
керуванням середовищем та базовими AWS-ресурсами.

## Словник термінів

| Термін                     | Визначення українською                                                                              |
|----------------------------|-----------------------------------------------------------------------------------------------------|
| **Application**            | Контейнер Elastic Beanstalk для application versions, environments і saved configurations.          |
| **Application Version**    | Версія пакета застосунку, завантажена в Elastic Beanstalk і доступна для розгортання в environment. |
| **Environment**            | Набір AWS-ресурсів Elastic Beanstalk, на якому працює конкретна версія застосунку.                  |
| **Web/Worker Tier**        | Web tier обслуговує HTTP requests; worker tier обробляє фонові повідомлення, зазвичай із SQS.       |
| **Platform**               | Набір OS, runtime та web server, на основі якого Beanstalk запускає застосунок.                     |
| **Configuration Template** | Збережена конфігурація environment, яку можна повторно застосувати.                                 |
| **Environment Variables**  | Параметри, які Beanstalk передає застосунку під час виконання.                                      |
| **.ebextensions**          | Каталог YAML/JSON конфігурацій для налаштування ресурсів та EC2 environment.                        |
| **.platform**              | Каталог platform hooks і конфігурацій для сучасних Beanstalk platforms.                             |
| **Rolling**                | Deployment policy, що оновлює instances групами, зберігаючи частину старої версії доступною.        |
| **Immutable**              | Deployment policy, що створює нові instances з новою версією і перемикає їх після перевірки.        |
| **Blue/Green**             | Два окремі environments: нову версію тестують і перемикають CNAME/traffic після перевірки.          |
| **All-at-once**            | Deployment policy, що одночасно оновлює всі instances і може спричинити downtime.                   |

## Типовий екзаменаційний сценарій

Потрібно розгорнути web app без ручного створення всіх EC2/ELB/ASG
компонентів → Elastic Beanstalk.

## Екзаменаційна пастка

Beanstalk керує середовищем, але не є окремою мовою чи runtime. Worker
environment часто інтегрується із SQS.

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

- [AWS Documentation — AWS Elastic
  Beanstalk](https://docs.aws.amazon.com/)
- [DVA-C02 Exam
  Guide](https://docs.aws.amazon.com/aws-certification/latest/developer-associate-02/developer-associate-02.html)
