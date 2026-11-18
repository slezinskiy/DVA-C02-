# Amazon EC2

**Категорія:** Compute  
**Призначення:** Віртуальні сервери з повним контролем над ОС, типом
інстансу та програмним середовищем.

## Словник термінів

| Термін                   | Визначення українською                                                                                                                    |
|--------------------------|-------------------------------------------------------------------------------------------------------------------------------------------|
| **Instance**             | Віртуальний сервер EC2 із AMI, instance type, storage, networking і security configuration.                                               |
| **AMI**                  | Образ EC2, який містить операційну систему та налаштування запуску (визначення наведено в розділі EC2).                                   |
| **Instance Type/Family** | Розмір і сімейство EC2, що визначають vCPU, memory, network та оптимізацію workload.                                                      |
| **User Data**            | Скрипт або cloud-init configuration, яку EC2 передає інстансу під час запуску для bootstrap/автоматичного налаштування.                   |
| **Metadata**             | Інформація про EC2 instance, доступна через Instance Metadata Service, зокрема instance ID та IAM credentials.                            |
| **IMDSv2**               | Захищений режим EC2 Instance Metadata Service, який вимагає отримати session token перед читанням metadata.                               |
| **Instance Profile**     | Контейнер для IAM role, який прикріплюється до EC2 instance і надає тимчасові credentials застосункам на інстансі.                        |
| **Security Group**       | Stateful virtual firewall для ENI/resource. Дозволяє правила allow; відповідь на дозволене з’єднання пропускається автоматично.           |
| **EBS**                  | Elastic Block Store — persistent block storage, яке може існувати незалежно від життєвого циклу EC2 instance.                             |
| **Instance Store**       | Тимчасове локальне сховище на фізичному хості; дані можуть бути втрачені при зупинці/завершенні instance або відмові хоста.               |
| **Placement Group**      | Стратегія розміщення instances: Cluster для низької latency/high throughput, Spread для ізоляції, Partition для розподілу великих систем. |
| **ASG**                  | Auto Scaling Group — група EC2, яка підтримує desired capacity і масштабується за policies.                                               |
| **Launch Template**      | Шаблон параметрів запуску EC2: AMI, instance type, networking, storage, IAM profile та інші налаштування.                                 |
| **Spot**                 | Модель EC2 capacity зі зниженою ціною, за якої AWS може перервати instance; підходить для fault-tolerant workload.                        |
| **On-Demand**            | Оплата за фактичне використання EC2 без довгострокового зобов’язання.                                                                     |
| **Savings Plans**        | Знижка в обмін на погодинне зобов’язання щодо compute usage на 1 або 3 роки.                                                              |
| **Elastic IP**           | Статична публічна IPv4 адреса AWS, яку можна перепризначати між сумісними ресурсами.                                                      |
| **ENI**                  | Elastic Network Interface — віртуальна мережева карта AWS із private IP, security groups та іншими мережевими атрибутами.                 |

## Типовий екзаменаційний сценарій

Потрібен контроль над ОС, агентами або довготривалим процесом → EC2.

## Екзаменаційна пастка

IAM Role через Instance Profile краще за статичні access keys. Stop
зберігає інстанс; Terminate видаляє його.

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

- [AWS Documentation — Amazon EC2](https://docs.aws.amazon.com/)
- [DVA-C02 Exam
  Guide](https://docs.aws.amazon.com/aws-certification/latest/developer-associate-02/developer-associate-02.html)
