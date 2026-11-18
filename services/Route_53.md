# Amazon Route 53

**Категорія:** Networking and Content Delivery  
**Призначення:** DNS, domain registration та DNS-based routing із health
checks.

## Словник термінів

| Термін                  | Визначення українською                                                                                       |
|-------------------------|--------------------------------------------------------------------------------------------------------------|
| **Hosted Zone**         | Контейнер DNS records Route 53 для домену або піддомену; може бути public або private.                       |
| **Public/Private Zone** | Public hosted zone відповідає на публічні DNS-запити; private zone — лише з асоційованих VPC.                |
| **Record Set**          | DNS запис, який зіставляє доменне ім’я з адресою або іншим DNS target.                                       |
| **A/AAAA**              | DNS типи записів для IPv4 (A) та IPv6 (AAAA).                                                                |
| **CNAME**               | DNS запис-псевдонім одного hostname на інше; не дозволений для zone apex.                                    |
| **Alias**               | Route 53 extension, що спрямовує ім’я на підтримуваний AWS resource і може використовуватися на apex domain. |
| **MX**                  | DNS запис, що визначає mail servers домену.                                                                  |
| **TXT**                 | Текстовий DNS запис, часто для domain verification і email policies.                                         |
| **NS**                  | Name Server records, що визначають authoritative DNS servers hosted zone.                                    |
| **SOA**                 | Start of Authority record із метаданими та параметрами DNS zone.                                             |
| **TTL**                 | Час, протягом якого DNS resolver може кешувати відповідь.                                                    |
| **Health Check**        | Перевірка endpoint або CloudWatch alarm, яку Route 53 використовує для routing/failover.                     |
| **Failover**            | Routing policy, що повертає primary endpoint і переходить на secondary при недоступності primary.            |
| **Weighted**            | Routing policy, яка розподіляє DNS responses між records за заданими weights.                                |
| **Latency**             | Latency-based routing, яке вибирає endpoint у Region із найменшою затримкою для користувача.                 |
| **Geolocation**         | Routing policy, що вибирає endpoint за географічним розташуванням DNS resolver.                              |
| **Geoproximity**        | Routing policy, що спрямовує користувачів до географічно близьких ресурсів із можливістю bias.               |
| **Multivalue**          | Routing policy, що повертає кілька healthy records у DNS response.                                           |
| **DNSSEC**              | DNS Security Extensions — криптографічна перевірка автентичності DNS-відповідей.                             |

## Типовий екзаменаційний сценарій

Потрібно DNS failover або latency-based routing → Route 53.

## Екзаменаційна пастка

Alias record може вказувати на підтримувані AWS resources і працює на
zone apex; CNAME має обмеження apex.

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

- [AWS Documentation — Amazon Route 53](https://docs.aws.amazon.com/)
- [DVA-C02 Exam
  Guide](https://docs.aws.amazon.com/aws-certification/latest/developer-associate-02/developer-associate-02.html)
