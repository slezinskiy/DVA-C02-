# AWS CodeBuild

**Категорія:** Developer Tools  
**Призначення:** Керований build/test service для компіляції коду та
створення артефактів.

## Словник термінів

| Термін                                 | Визначення українською                                                                              |
|----------------------------------------|-----------------------------------------------------------------------------------------------------|
| **Build Project**                      | Конфігурація CodeBuild із source, build environment, IAM role, buildspec, artifacts і cache.        |
| **Build Environment**                  | Обчислювальне середовище з OS, runtime, compute type та environment variables.                      |
| **buildspec.yml**                      | YAML-файл, який задає команди та фази отримання source, збірки, тестування і публікації.            |
| **Source**                             | Репозиторій або інше джерело коду, яке CodeBuild отримує перед запуском.                            |
| **Artifact**                           | Файл або набір файлів, створений/переданий етапом build pipeline і доступний наступним етапам.      |
| **install/pre_build/build/post_build** | Послідовні фази buildspec: встановлення залежностей, підготовка, build/test та завершальні команди. |
| **Cache**                              | Збереження залежностей або проміжних результатів між builds для скорочення часу збірки.             |
| **Service Role**                       | IAM role, яку CodeBuild assume для доступу до source, logs, artifacts та інших AWS resources.       |
| **Privileged Mode**                    | Режим build container, потрібний, наприклад, для запуску Docker daemon і створення images.          |
| **Reports**                            | Збережені результати тестів і code coverage, які CodeBuild показує як test reports.                 |
| **Batch Build**                        | Запуск кількох пов’язаних builds паралельно або в матричній конфігурації.                           |

## Типовий екзаменаційний сценарій

Потрібно компілювати й тестувати код у CI → CodeBuild.

## Екзаменаційна пастка

CodeBuild не оркеструє весь pipeline і не є deployment service.

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

- [AWS Documentation — AWS CodeBuild](https://docs.aws.amazon.com/)
- [DVA-C02 Exam
  Guide](https://docs.aws.amazon.com/aws-certification/latest/developer-associate-02/developer-associate-02.html)
