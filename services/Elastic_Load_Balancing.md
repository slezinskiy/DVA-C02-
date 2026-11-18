# Elastic Load Balancing

**Категорія:** Networking and Content Delivery  
**Призначення:** Керований розподіл трафіку між targets у кількох
Availability Zones.

## Словник термінів

| Термін                   | Визначення українською                                                                                               |
|--------------------------|----------------------------------------------------------------------------------------------------------------------|
| **ALB**                  | Application Load Balancer — Layer 7 балансувальник HTTP/HTTPS із host/path/header routing.                           |
| **NLB**                  | Network Load Balancer — Layer 4 балансувальник TCP/TLS/UDP/QUIC із високою продуктивністю та низькою latency.        |
| **GWLB**                 | Gateway Load Balancer — балансувальник для масштабування virtual appliances, наприклад firewalls.                    |
| **CLB**                  | Classic Load Balancer — попереднє покоління ELB із базовими Layer 4/7 функціями.                                     |
| **Listener**             | Компонент load balancer, що приймає з’єднання на певному protocol/port і застосовує правила маршрутизації.           |
| **Listener Rule**        | Умова й action ALB listener, що визначають маршрутизацію запиту.                                                     |
| **Target Group**         | Група backend targets (EC2, IP, Lambda тощо), до яких load balancer маршрутизує запити.                              |
| **Target**               | Backend resource у target group: EC2, IP, Lambda або інший підтримуваний тип.                                        |
| **Health Check**         | Періодична перевірка стану target, за результатами якої load balancer визначає, чи можна надсилати йому трафік.      |
| **Cross-Zone**           | Розподіл трафіку між targets у різних AZ, а не лише локальними targets.                                              |
| **Sticky Sessions**      | Прив’язка клієнта до одного target протягом сесії через cookies.                                                     |
| **Deregistration Delay** | Період graceful draining активних запитів перед видаленням target із групи.                                          |
| **TLS Termination**      | Завершення TLS на load balancer, який розшифровує трафік і передає його backend.                                     |
| **SNI**                  | Server Name Indication — TLS extension, що дозволяє listener використовувати кілька сертифікатів для різних доменів. |

## Типовий екзаменаційний сценарій

HTTP path/host routing → ALB; TCP/UDP/TLS high-performance routing →
NLB.

## Екзаменаційна пастка

ALB — Layer 7; NLB — Layer 4. Health checks визначають healthy targets.

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

- [AWS Documentation — Elastic Load
  Balancing](https://docs.aws.amazon.com/)
- [DVA-C02 Exam
  Guide](https://docs.aws.amazon.com/aws-certification/latest/developer-associate-02/developer-associate-02.html)
