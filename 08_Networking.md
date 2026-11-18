# Networking and Content Delivery — довідник DVA-C02

Тематичний довідник із визначеннями термінів, практичними сценаріями та
типовими екзаменаційними пастками.

## Amazon API Gateway

**Призначення:** Керований сервіс для створення, захисту та публікації
REST, HTTP і WebSocket APIs.

### Ключові терміни

| Термін            | Визначення українською                                                                                                                             |
|-------------------|----------------------------------------------------------------------------------------------------------------------------------------------------|
| **REST API**      | API Gateway REST API (v1) — ресурсно-орієнтований API з resources, methods, stages, authorizers та integrations.                                   |
| **HTTP API**      | Полегшений API Gateway тип для HTTP workloads із нижчою latency/вартістю; підтримує Lambda/HTTP integrations та JWT/Lambda authorizers.            |
| **WebSocket API** | API для двостороннього постійного з’єднання клієнта із сервером через WebSocket.                                                                   |
| **Resource**      | Шлях/ресурс REST API, який формує endpoint і містить methods, наприклад /orders/{id}.                                                              |
| **Method**        | HTTP-операція на resource (GET, POST, PUT, DELETE) з налаштуваннями authorization та integration.                                                  |
| **Route**         | Правило HTTP/WebSocket API, яке зіставляє запит із backend integration.                                                                            |
| **Integration**   | Зв’язок API Gateway із backend: Lambda, HTTP endpoint, AWS service або mock.                                                                       |
| **Lambda Proxy**  | Режим, у якому API Gateway передає Lambda request/context і очікує від неї HTTP response у визначеному форматі.                                    |
| **Stage**         | Розгорнуте середовище API Gateway, наприклад dev або prod, що посилається на конкретний deployment.                                                |
| **Deployment**    | Kubernetes controller, який керує ReplicaSets і підтримує бажану кількість Pod, rollout та rollback.                                               |
| **Authorizer**    | Компонент API Gateway/AppSync, який перевіряє identity та дозволи запиту перед його передаванням до backend.                                       |
| **IAM Auth**      | Авторизація через AWS SigV4; викликач повинен мати iam:execute-api:Invoke permission.                                                              |
| **API Key**       | Ключ для ідентифікації клієнта у usage plan та обліку quota/throttling; не замінює надійну автентифікацію.                                         |
| **Usage Plan**    | Налаштування API Gateway REST API, що пов’язує API keys із quota та throttling limits. API key сам по собі не є механізмом сильної автентифікації. |
| **Throttling**    | Обмеження швидкості запитів за rate і burst limits для захисту API та backend.                                                                     |
| **Quota**         | Ліміт кількості запитів за певний період у usage plan.                                                                                             |
| **CORS**          | Cross-Origin Resource Sharing — механізм браузера для дозволу запитів із іншого origin.                                                            |
| **Custom Domain** | Власне доменне ім’я для API Gateway, налаштоване з TLS certificate та DNS mapping.                                                                 |
| **Private API**   | REST API, доступний через interface VPC endpoint, а не з публічного інтернету.                                                                     |
| **Access Logs**   | Журнали запитів API Gateway із request ID, status, latency та іншими вибраними полями.                                                             |

**Типовий екзаменаційний сценарій:** Потрібен керований API front door
із throttling/auth/stages → API Gateway.

**Екзаменаційна пастка:** API key не є повноцінною автентифікацією.
Lambda Function URL простіший, але має менше API management features.

------------------------------------------------------------------------

## Amazon CloudFront

**Призначення:** Глобальна CDN для кешування та доставки контенту через
edge locations.

### Ключові терміни

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

**Типовий екзаменаційний сценарій:** Потрібно зменшити latency доставки
статичного/динамічного контенту → CloudFront.

**Екзаменаційна пастка:** CloudFront — CDN, не DNS. Для приватного S3
origin використовуйте OAC у сучасних конфігураціях.

------------------------------------------------------------------------

## Elastic Load Balancing

**Призначення:** Керований розподіл трафіку між targets у кількох
Availability Zones.

### Ключові терміни

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

**Типовий екзаменаційний сценарій:** HTTP path/host routing → ALB;
TCP/UDP/TLS high-performance routing → NLB.

**Екзаменаційна пастка:** ALB — Layer 7; NLB — Layer 4. Health checks
визначають healthy targets.

------------------------------------------------------------------------

## Amazon Route 53

**Призначення:** DNS, domain registration та DNS-based routing із health
checks.

### Ключові терміни

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

**Типовий екзаменаційний сценарій:** Потрібно DNS failover або
latency-based routing → Route 53.

**Екзаменаційна пастка:** Alias record може вказувати на підтримувані
AWS resources і працює на zone apex; CNAME має обмеження apex.

------------------------------------------------------------------------

## Amazon VPC

**Призначення:** Ізольована мережа AWS із CIDR, subnets, routes,
security controls та endpoints.

### Ключові терміни

| Термін                         | Визначення українською                                                                                                            |
|--------------------------------|-----------------------------------------------------------------------------------------------------------------------------------|
| **VPC**                        | Ізольована логічна мережа AWS із CIDR, subnets, route tables та network controls.                                                 |
| **CIDR**                       | Нотація діапазону IP-адрес, наприклад 10.0.0.0/16.                                                                                |
| **Subnet**                     | Діапазон IP-адрес у VPC, який належить одній Availability Zone.                                                                   |
| **Public/Private Subnet**      | Public subnet має route до Internet Gateway; private subnet не має прямого inbound/outbound маршруту через IGW.                   |
| **Route Table**                | Набір маршрутів, що визначає next hop для трафіку з subnet.                                                                       |
| **IGW**                        | Internet Gateway — компонент VPC для маршрутизації між VPC та інтернетом.                                                         |
| **NAT Gateway**                | Керований NAT для outbound internet access із private subnet; не приймає ініційовані з інтернету inbound connections.             |
| **Security Group**             | Stateful virtual firewall для ENI/resource. Дозволяє правила allow; відповідь на дозволене з’єднання пропускається автоматично.   |
| **NACL**                       | Network ACL — stateless firewall на рівні subnet із правилами allow і deny; потрібно явно враховувати inbound та outbound трафік. |
| **Gateway/Interface Endpoint** | Gateway endpoint маршрутизує S3/DynamoDB через route tables; interface endpoint створює ENI та використовує PrivateLink.          |
| **PrivateLink**                | Технологія приватного доступу до сервісів через interface endpoints.                                                              |
| **Peering**                    | Приватне з’єднання двох VPC; peering не підтримує транзитивну маршрутизацію.                                                      |
| **Transit Gateway**            | Центральний hub для з’єднання багатьох VPC та on-premises networks.                                                               |
| **Flow Logs**                  | Записи metadata про IP traffic до/з VPC, subnet або ENI.                                                                          |
| **ENI**                        | Elastic Network Interface — віртуальна мережева карта з IP addresses і security groups.                                           |
| **EIP**                        | Elastic IP — статична публічна IPv4 адреса AWS.                                                                                   |
| **Egress-only IGW**            | IPv6 gateway, що дозволяє outbound internet traffic, але блокує ініційовані з інтернету inbound connections.                      |

**Типовий екзаменаційний сценарій:** Потрібен приватний доступ до
S3/DynamoDB → Gateway Endpoint; до багатьох AWS APIs → Interface
Endpoint.

**Екзаменаційна пастка:** Security Group stateful; NACL stateless.
Public subnet сама по собі не робить EC2 публічним — потрібні public IP
та route.

------------------------------------------------------------------------
