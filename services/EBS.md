# Amazon EBS

**Категорія:** Storage  
**Призначення:** Блокове сховище, яке підключається до EC2 як
віртуальний диск.

## Словник термінів

| Термін                    | Визначення українською                                                                                                                                                                   |
|---------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| **Volume**                | Віртуальний блоковий диск EBS, який можна підключити до EC2 у тій самій Availability Zone.                                                                                               |
| **Snapshot**              | Інкрементальна point-in-time резервна копія EBS volume. Після першого snapshot наступні зберігають лише змінені блоки; із snapshot можна створити volume в іншій AZ або Region.          |
| **Volume Type**           | Клас EBS volume, який визначає характеристики продуктивності та ціну. Основні типи: gp3/gp2 (general purpose SSD), io2/io1 (provisioned IOPS SSD), st1 (throughput HDD), sc1 (cold HDD). |
| **IOPS**                  | Input/Output Operations Per Second — кількість операцій читання/запису за секунду. Важливо для workload із великою кількістю дрібних випадкових операцій.                                |
| **Throughput**            | Обсяг даних, який передається за одиницю часу, зазвичай MiB/s. Особливо важливий для послідовного читання/запису.                                                                        |
| **Latency**               | Затримка між запитом на I/O та його завершенням. Низька latency важлива для транзакційних і чутливих до часу застосунків.                                                                |
| **Provisioned IOPS**      | Задана користувачем продуктивність IOPS для підтримуваних типів EBS, насамперед io1/io2; допомагає передбачити продуктивність інтенсивного I/O.                                          |
| **Encryption**            | Шифрування EBS volume і snapshots за допомогою AWS KMS. Шифрування захищає дані at rest та підтримується прозоро для EC2.                                                                |
| **Multi-Attach**          | Функція io1/io2, яка дозволяє підключити один EBS volume до кількох сумісних EC2 instances в одній AZ. Потрібна кластерна файлова система або механізм координації запису.               |
| **Elastic Volumes**       | Можливість змінити розмір, тип або продуктивність підтримуваного EBS volume без від’єднання від EC2, з урахуванням обмежень модифікації.                                                 |
| **Root/Data Volume**      | Root volume містить операційну систему EC2; data volume зберігає дані застосунку окремо від системного диска.                                                                            |
| **AZ Scope**              | EBS volume прив’язаний до однієї Availability Zone. Для використання в іншій AZ створюють snapshot і відновлюють із нього новий volume у цільовій AZ.                                    |
| **Fast Snapshot Restore** | Функція, яка забезпечує повну продуктивність EBS volume, створеного зі snapshot, без поступової ініціалізації блоків у вибраних AZ.                                                      |

## Типовий екзаменаційний сценарій

Потрібен постійний block device для EC2 → EBS.

## Екзаменаційна пастка

EBS volume прив’язаний до Availability Zone; для перенесення
використовують snapshot і створюють volume в іншій AZ.

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

- [AWS Documentation — Amazon EBS](https://docs.aws.amazon.com/)
- [DVA-C02 Exam
  Guide](https://docs.aws.amazon.com/aws-certification/latest/developer-associate-02/developer-associate-02.html)
