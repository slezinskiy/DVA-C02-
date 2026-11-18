# AWS KMS

**Категорія:** Security, Identity, and Compliance  
**Призначення:** Керування криптографічними ключами для шифрування,
дешифрування та підпису.

## Словник термінів

| Термін                    | Визначення українською                                                                                                                          |
|---------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------|
| **KMS Key**               | Логічний ресурс KMS для криптографічних операцій та керування key material.                                                                     |
| **Key Material**          | Криптографічні дані, що лежать в основі KMS key.                                                                                                |
| **AWS Owned/Managed Key** | AWS owned keys контролюються AWS поза account; AWS managed keys створюються й адмініструються AWS у customer account.                           |
| **Customer Managed Key**  | KMS key, яким керує користувач і для якого можна налаштовувати policy, grants, rotation та lifecycle.                                           |
| **Key Policy**            | Основна resource policy KMS key, яка визначає principals та дозволені операції з ключем.                                                        |
| **Grant**                 | Делегований набір permissions для principal/service на операції з KMS key.                                                                      |
| **Envelope Encryption**   | Схема шифрування, де дані шифруються data key, а data key окремо шифрується KMS key.                                                            |
| **Data Key**              | Ключ шифрування даних, який KMS може згенерувати та повернути в plaintext і зашифрованому вигляді.                                              |
| **GenerateDataKey**       | KMS API, що генерує data key і повертає plaintext та encrypted копії.                                                                           |
| **Encrypt/Decrypt**       | KMS API для шифрування/розшифрування даних безпосередньо KMS key у межах розмірних обмежень.                                                    |
| **Rotation**              | Процес регулярної заміни секретного значення або оновлення key material для зниження ризику компрометації.                                      |
| **Alias**                 | Людиночитне ім’я-покажчик на KMS key, яке можна перепризначити.                                                                                 |
| **ARN**                   | Amazon Resource Name — ідентифікатор KMS resource.                                                                                              |
| **Multi-Region Key**      | Пов’язані KMS keys у різних Regions із сумісним key material для multi-Region cryptographic use cases.                                          |
| **Encryption Context**    | Набір не секретних key-value metadata, криптографічно пов’язаних із KMS encryption operation; для decrypt має бути переданий той самий context. |

## Типовий екзаменаційний сценарій

Потрібне кероване шифрування даних із контролем ключів → KMS.

## Екзаменаційна пастка

Перевіряйте Key Policy разом з IAM policy; KMS key policy є ключовою
частиною authorization.

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

- [AWS Documentation — AWS KMS](https://docs.aws.amazon.com/)
- [DVA-C02 Exam
  Guide](https://docs.aws.amazon.com/aws-certification/latest/developer-associate-02/developer-associate-02.html)
