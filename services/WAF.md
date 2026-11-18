# AWS WAF

**Категорія:** Security, Identity, and Compliance  
**Призначення:** Фільтрація HTTP(S) запитів за правилами для захисту web
apps та APIs.

## Словник термінів

| Термін                   | Визначення українською                                                                                                    |
|--------------------------|---------------------------------------------------------------------------------------------------------------------------|
| **Web ACL**              | Набір правил AWS WAF, який асоціюється з web resource і визначає, які HTTP(S) запити дозволяти, блокувати або перевіряти. |
| **Rule**                 | Умова AWS WAF, що зіставляє HTTP request із критеріями та застосовує action.                                              |
| **Rule Group**           | Повторно використовуваний набір WAF rules, який можна додати до Web ACL.                                                  |
| **Managed Rule Group**   | Готовий набір правил AWS або стороннього provider для типових web threats.                                                |
| **IP Set**               | Список IPv4/IPv6 CIDR ranges, який можна використовувати в WAF rules.                                                     |
| **Regex Pattern Set**    | Набір regular expressions для пошуку шаблонів у частинах HTTP request.                                                    |
| **Rate-based Rule**      | Правило AWS WAF, яке обмежує запити за кількістю протягом заданого вікна для визначених aggregation keys.                 |
| **SQLi Match**           | Умова WAF для виявлення ознак SQL injection у вибраних частинах запиту.                                                   |
| **XSS Match**            | Умова WAF для виявлення ознак cross-site scripting у запиті.                                                              |
| **Scope-down Statement** | Додаткова умова, яка звужує запити, до яких застосовується rule group або rate-based rule.                                |
| **Allow/Block/Count**    | WAF actions: Allow пропускає, Block відхиляє, Count лише рахує збіги.                                                     |
| **CAPTCHA/Challenge**    | Actions, які вимагають CAPTCHA або browser challenge перед подальшим доступом.                                            |
| **Logging**              | Запис WAF request logs у destination для аналізу та troubleshooting.                                                      |
| **Association**          | Прив’язка Web ACL до підтримуваного ресурсу, наприклад CloudFront або ALB.                                                |

## Типовий екзаменаційний сценарій

Потрібно блокувати SQL injection, XSS або rate abuse на web endpoint →
WAF.

## Екзаменаційна пастка

WAF фільтрує web requests; Security Group/NACL контролюють мережевий
трафік.

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

- [AWS Documentation — AWS WAF](https://docs.aws.amazon.com/)
- [DVA-C02 Exam
  Guide](https://docs.aws.amazon.com/aws-certification/latest/developer-associate-02/developer-associate-02.html)
