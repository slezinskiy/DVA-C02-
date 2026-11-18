# Amazon EFS

**Категорія:** Storage  
**Призначення:** Еластична спільна мережева файлова система для Linux
workloads.

## Словник термінів

| Термін                     | Визначення українською                                                                                                    |
|----------------------------|---------------------------------------------------------------------------------------------------------------------------|
| **File System**            | Спільна мережева файлова система EFS, доступна Linux clients через NFS.                                                   |
| **Mount Target**           | Мережевий endpoint EFS у subnet/AZ, через який клієнти монтують файлову систему.                                          |
| **NFS**                    | Network File System — мережевий протокол доступу до файлів; EFS підтримує NFSv4.1.                                        |
| **Access Point**           | EFS endpoint із заданим root directory та POSIX identity для ізольованого доступу застосунку.                             |
| **POSIX Permissions**      | Права Linux filesystem: власник, група та read/write/execute для owner/group/others.                                      |
| **UID/GID**                | Числові ідентифікатори Linux user і group, які визначають власність файлів та права доступу.                              |
| **Performance Mode**       | Профіль EFS для характеристик latency та масштабування I/O, наприклад General Purpose або Max I/O (де підтримується).     |
| **Throughput Mode**        | Спосіб надання throughput EFS: Bursting, Provisioned або Elastic.                                                         |
| **Bursting**               | Throughput mode, де доступна пропускна здатність залежить від обсягу збережених даних і burst credits.                    |
| **Elastic Throughput**     | Режим, який автоматично підлаштовує throughput під фактичний workload.                                                    |
| **Provisioned Throughput** | Режим, де користувач задає throughput незалежно від обсягу даних.                                                         |
| **Lifecycle Management**   | Автоматичне переміщення файлів у дешевші EFS storage classes після періоду без доступу.                                   |
| **IA**                     | Infrequent Access — дешевший клас EFS для файлів, до яких звертаються нечасто.                                            |
| **One Zone**               | EFS storage class, що зберігає дані в одній AZ; дешевший, але з нижчою доступністю при втраті AZ.                         |
| **Encryption**             | Шифрування EBS volume і snapshots за допомогою AWS KMS. Шифрування захищає дані at rest та підтримується прозоро для EC2. |

## Типовий екзаменаційний сценарій

Кілька Linux instances потребують спільної файлової системи → EFS.

## Екзаменаційна пастка

EFS — file storage через NFS; EBS — block storage для instance; S3 —
object storage.

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

- [AWS Documentation — Amazon EFS](https://docs.aws.amazon.com/)
- [DVA-C02 Exam
  Guide](https://docs.aws.amazon.com/aws-certification/latest/developer-associate-02/developer-associate-02.html)
