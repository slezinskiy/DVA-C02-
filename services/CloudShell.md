# AWS CloudShell

**Категорія:** Developer Tools  
**Призначення:** Браузерна shell-сесія з AWS CLI та інструментами для
роботи з AWS.

## Словник термінів

| Термін              | Визначення українською                                                                                       |
|---------------------|--------------------------------------------------------------------------------------------------------------|
| **Browser Shell**   | Браузерне shell-середовище AWS із попередньо автентифікованим доступом до account та AWS CLI.                |
| **IAM Session**     | CloudShell працює з IAM identity поточного AWS Console session і використовує її permissions.                |
| **Persistent Home** | Домашній каталог CloudShell зберігає файли між сесіями в межах відповідного Region та квот.                  |
| **AWS CLI**         | Командний інтерфейс для виклику AWS APIs; у CloudShell зазвичай уже встановлений і налаштований.             |
| **Upload/Download** | Можливість передавати файли між локальним комп’ютером і CloudShell environment.                              |
| **Region**          | AWS Region, у якому створено CloudShell environment і зберігається його home directory.                      |
| **Profile**         | AWS CLI named profile із credentials/settings; у CloudShell часто використовується поточна Console identity. |

## Типовий екзаменаційний сценарій

Потрібен CLI без локального встановлення інструментів → CloudShell.

## Екзаменаційна пастка

CloudShell не є EC2, яким користувач адмініструє ОС.

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

- [AWS Documentation — AWS CloudShell](https://docs.aws.amazon.com/)
- [DVA-C02 Exam
  Guide](https://docs.aws.amazon.com/aws-certification/latest/developer-associate-02/developer-associate-02.html)
