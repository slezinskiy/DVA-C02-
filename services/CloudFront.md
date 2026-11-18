# Amazon CloudFront

**Категорія:** Networking and Content Delivery  
**Призначення:** Глобальна CDN для кешування та доставки контенту через
edge locations.

## Словник термінів

| Термін                    | Визначення українською                                                                                                      |
|---------------------------|-----------------------------------------------------------------------------------------------------------------------------|
| **Distribution**          | Конфігурація CloudFront із origins, cache behaviors, domains, TLS та правилами доставки.                                    |
| **Origin**                | Джерело контенту CloudFront, наприклад S3 bucket або HTTP server, звідки CloudFront отримує об’єкти.                        |
| **Edge Location**         | Локація CloudFront, де контент кешується або обробляється ближче до користувача.                                            |
| **Regional Edge Cache**   | Проміжний рівень кешу між edge locations і origin, який збільшує ймовірність cache hit.                                     |
| **Cache Behavior**        | Правило, що визначає обробку запитів для path pattern: origin, cache policy та дозволені methods.                           |
| **Cache Policy**          | Політика CloudFront, яка визначає cache key (headers, cookies, query strings) та TTL для об’єктів.                          |
| **Origin Request Policy** | Політика, що визначає headers, cookies та query strings, які передаються до origin без обов’язкового включення в cache key. |
| **TTL**                   | Час життя об’єкта в CloudFront cache, визначений cache policy та cache-control headers origin.                              |
| **Cache Hit Ratio**       | Частка запитів, які CloudFront обслуговує з кешу, а не з origin.                                                            |
| **Invalidation**          | Запит CloudFront видалити відповідні об’єкти з edge caches, щоб наступні запити отримали оновлену версію з origin.          |
| **OAC**                   | Origin Access Control — рекомендований механізм підписаного доступу CloudFront до приватного S3 origin.                     |
| **OAI**                   | Origin Access Identity — старіший механізм CloudFront для доступу до приватного S3 bucket.                                  |
| **Signed URL**            | Підписаний URL із обмеженнями доступу та строком дії для одного ресурсу.                                                    |
| **Signed Cookie**         | Підписані cookies, які дозволяють доступ до набору приватних CloudFront objects.                                            |
| **Geo Restriction**       | Налаштування, що дозволяє або блокує доставку контенту користувачам із визначених країн.                                    |
| **Lambda@Edge**           | Запуск Lambda function на CloudFront edge locations для зміни viewer/origin requests або responses.                         |
| **CloudFront Functions**  | Легкий JavaScript runtime на edge для швидких операцій над viewer requests/responses.                                       |
| **WAF**                   | AWS Web Application Firewall, який фільтрує HTTP(S) запити до CloudFront distribution.                                      |

## Типовий екзаменаційний сценарій

Потрібно зменшити latency доставки статичного/динамічного контенту →
CloudFront.

## Екзаменаційна пастка

CloudFront — CDN, не DNS. Для приватного S3 origin використовуйте OAC у
сучасних конфігураціях.

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

- [AWS Documentation — Amazon CloudFront](https://docs.aws.amazon.com/)
- [DVA-C02 Exam
  Guide](https://docs.aws.amazon.com/aws-certification/latest/developer-associate-02/developer-associate-02.html)
