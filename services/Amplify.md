# AWS Amplify

**Категорія:** Developer Tools  
**Призначення:** Інструменти для frontend hosting та
створення/підключення backend можливостей.

## Словник термінів

| Термін                    | Визначення українською                                                                             |
|---------------------------|----------------------------------------------------------------------------------------------------|
| **Amplify Hosting**       | Керований хостинг web applications із Git-based CI/CD, preview deployments та CDN.                 |
| **Backend**               | Набір backend capabilities застосунку, наприклад authentication, data, storage і functions.        |
| **Authentication**        | Інтеграція Amplify з Cognito для sign-up, sign-in, сесій і користувачів.                           |
| **Data**                  | Шар даних Amplify, який створює API та інтеграцію зі сховищем, залежно від конфігурації.           |
| **Storage**               | Функціональність для зберігання файлів, зазвичай на базі Amazon S3.                                |
| **Build Settings**        | Налаштування команд, build phases, artifacts та environment variables для CI/CD.                   |
| **Branch Deployment**     | Автоматичне розгортання окремого середовища для підключеної Git branch.                            |
| **Preview Deployment**    | Тимчасове середовище для перевірки змін branch або pull request до злиття.                         |
| **Environment Variables** | Параметри конфігурації для build або застосунку; секрети не слід вбудовувати в публічний frontend. |

## Типовий екзаменаційний сценарій

Потрібен Git-based hosting frontend із build/deploy → Amplify Hosting.

## Екзаменаційна пастка

Amplify — не універсальна заміна всім backend-сервісам; перевіряйте, які
саме ресурси він створює.

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

- [AWS Documentation — AWS Amplify](https://docs.aws.amazon.com/)
- [DVA-C02 Exam
  Guide](https://docs.aws.amazon.com/aws-certification/latest/developer-associate-02/developer-associate-02.html)
