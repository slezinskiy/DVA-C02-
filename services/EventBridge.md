# Amazon EventBridge

**Категорія:** Application Integration  
**Призначення:** Serverless event bus для маршрутизації подій за
правилами та інтеграції сервісів.

## Словник термінів

| Термін                         | Визначення українською                                                                                                   |
|--------------------------------|--------------------------------------------------------------------------------------------------------------------------|
| **Event**                      | Структуроване повідомлення про подію, зазвичай JSON із source, detail-type, time та detail.                              |
| **Event Bus**                  | Канал EventBridge, який приймає події від джерел і маршрутизує їх за правилами до targets.                               |
| **Default/Custom/Partner Bus** | Default bus отримує AWS service events; custom bus — події застосунків; partner bus — події інтегрованих SaaS providers. |
| **Rule**                       | Конфігурація EventBridge, що зіставляє події за pattern або schedule та надсилає збіги до targets.                       |
| **Event Pattern**              | JSON-умова, яка визначає, які поля та значення події мають збігтися, щоб правило спрацювало.                             |
| **Target**                     | Сервіс або ресурс, до якого EventBridge передає подію після збігу з правилом.                                            |
| **Input Transformer**          | Налаштування EventBridge, яке витягує поля з початкової події та формує змінений payload для target.                     |
| **Archive**                    | Сховище EventBridge для збереження подій із event bus з метою подальшого replay.                                         |
| **Replay**                     | Повторне надсилання архівованих подій до event bus для відновлення або повторної обробки.                                |
| **Scheduler**                  | Amazon EventBridge Scheduler — керований сервіс одноразового або періодичного запуску AWS API actions за розкладом.      |
| **Retry**                      | Повторна доставка події до target після тимчасової помилки згідно з retry policy.                                        |
| **DLQ**                        | SQS queue для подій, які EventBridge не зміг доставити після повторних спроб.                                            |
| **Schema Registry**            | Каталог схем подій для їх пошуку, документування та генерації code bindings.                                             |

## Типовий екзаменаційний сценарій

Потрібно маршрутизувати події за вмістом до різних targets →
EventBridge.

## Екзаменаційна пастка

Не тотожний SQS: EventBridge маршрутизує події, SQS буферизує
повідомлення.

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

- [AWS Documentation — Amazon EventBridge](https://docs.aws.amazon.com/)
- [DVA-C02 Exam
  Guide](https://docs.aws.amazon.com/aws-certification/latest/developer-associate-02/developer-associate-02.html)
