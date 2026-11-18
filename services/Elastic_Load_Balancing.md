# Elastic Load Balancing

**Категорія:** Networking and Content Delivery

**Призначення:** Керований розподіл трафіку між targets у кількох
Availability Zones.

## Словник термінів

| Термін                   | Визначення                                                                                                                        |
|--------------------------|-----------------------------------------------------------------------------------------------------------------------------------|
| **ALB**                  | У контексті Elastic Load Balancing це поняття описує відповідний елемент сервісу, його налаштування або поведінку під час роботи. |
| **NLB**                  | У контексті Elastic Load Balancing це поняття описує відповідний елемент сервісу, його налаштування або поведінку під час роботи. |
| **GWLB**                 | У контексті Elastic Load Balancing це поняття описує відповідний елемент сервісу, його налаштування або поведінку під час роботи. |
| **CLB**                  | У контексті Elastic Load Balancing це поняття описує відповідний елемент сервісу, його налаштування або поведінку під час роботи. |
| **Listener**             | Компонент load balancer, який приймає з’єднання на protocol/port.                                                                 |
| **Listener Rule**        | У контексті Elastic Load Balancing це поняття описує відповідний елемент сервісу, його налаштування або поведінку під час роботи. |
| **Target Group**         | Набір backend targets, до яких load balancer маршрутизує трафік.                                                                  |
| **Target**               | Сервіс або ресурс, якому передається подія.                                                                                       |
| **Health Check**         | Перевірка доступності та працездатності target.                                                                                   |
| **Cross-Zone**           | У контексті Elastic Load Balancing це поняття описує відповідний елемент сервісу, його налаштування або поведінку під час роботи. |
| **Sticky Sessions**      | У контексті Elastic Load Balancing це поняття описує відповідний елемент сервісу, його налаштування або поведінку під час роботи. |
| **Deregistration Delay** | У контексті Elastic Load Balancing це поняття описує відповідний елемент сервісу, його налаштування або поведінку під час роботи. |
| **TLS Termination**      | У контексті Elastic Load Balancing це поняття описує відповідний елемент сервісу, його налаштування або поведінку під час роботи. |
| **SNI**                  | У контексті Elastic Load Balancing це поняття описує відповідний елемент сервісу, його налаштування або поведінку під час роботи. |

## Типовий екзаменаційний сценарій

HTTP path/host routing → ALB; TCP/UDP/TLS high-performance routing →
NLB.

## Екзаменаційна пастка

ALB — Layer 7; NLB — Layer 4. Health checks визначають healthy targets.

## Що повторити

- Призначення сервісу та типові сценарії використання.
- Основні API, інтеграції та необхідні IAM permissions.
- Обробку помилок, retries, throttling і logging, якщо вони застосовні.
- Обмеження та взаємодію з іншими AWS-сервісами.

## Офіційна документація

- [AWS Documentation — Elastic Load
  Balancing](https://docs.aws.amazon.com/)
- [DVA-C02 Exam
  Guide](https://docs.aws.amazon.com/aws-certification/latest/developer-associate-02/developer-associate-02.html)
