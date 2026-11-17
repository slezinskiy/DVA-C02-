# Elastic Load Balancing

**Категорія:** Networking and Content Delivery\
**Призначення:** Керований розподіл трафіку між targets у кількох
Availability Zones. \## Словник термінів \| Термін \| Визначення \|
\|---\|---\| \| **ALB** \| Ключовий компонент або поняття Elastic Load
Balancing; визначає відповідну частину конфігурації, виконання чи
інтеграції сервісу. \| \| **NLB** \| Ключовий компонент або поняття
Elastic Load Balancing; визначає відповідну частину конфігурації,
виконання чи інтеграції сервісу. \| \| **GWLB** \| Ключовий компонент
або поняття Elastic Load Balancing; визначає відповідну частину
конфігурації, виконання чи інтеграції сервісу. \| \| **CLB** \| Ключовий
компонент або поняття Elastic Load Balancing; визначає відповідну
частину конфігурації, виконання чи інтеграції сервісу. \| \|
**Listener** \| Компонент load balancer, який приймає з'єднання на
protocol/port. \| \| **Listener Rule** \| Ключовий компонент або поняття
Elastic Load Balancing; визначає відповідну частину конфігурації,
виконання чи інтеграції сервісу. \| \| **Target Group** \| Набір backend
targets, до яких load balancer маршрутизує трафік. \| \| **Target** \|
Сервіс або ресурс, якому передається подія. \| \| **Health Check** \|
Перевірка доступності та працездатності target. \| \| **Cross-Zone** \|
Ключовий компонент або поняття Elastic Load Balancing; визначає
відповідну частину конфігурації, виконання чи інтеграції сервісу. \| \|
**Sticky Sessions** \| Ключовий компонент або поняття Elastic Load
Balancing; визначає відповідну частину конфігурації, виконання чи
інтеграції сервісу. \| \| **Deregistration Delay** \| Ключовий компонент
або поняття Elastic Load Balancing; визначає відповідну частину
конфігурації, виконання чи інтеграції сервісу. \| \| **TLS Termination**
\| Ключовий компонент або поняття Elastic Load Balancing; визначає
відповідну частину конфігурації, виконання чи інтеграції сервісу. \| \|
**SNI** \| Ключовий компонент або поняття Elastic Load Balancing;
визначає відповідну частину конфігурації, виконання чи інтеграції
сервісу. \|

## Типовий екзаменаційний сценарій

HTTP path/host routing → ALB; TCP/UDP/TLS high-performance routing →
NLB.

## Екзаменаційна пастка

ALB --- Layer 7; NLB --- Layer 4. Health checks визначають healthy
targets.

## Що повторити

-   Призначення сервісу та його місце в архітектурі.
-   Ключові API, інтеграції та IAM permissions.
-   Обробку помилок, retries, throttling і logging, якщо вони
    застосовні.
-   Обмеження, моделі оплати та актуальні квоти в офіційній
    документації.

## Офіційна документація

-   [AWS Documentation --- Elastic Load
    Balancing](https://docs.aws.amazon.com/)
-   [DVA-C02 Exam
    Guide](https://docs.aws.amazon.com/aws-certification/latest/developer-associate-02/developer-associate-02.html)
