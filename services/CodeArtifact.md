# AWS CodeArtifact

**Категорія:** Developer Tools  
**Призначення:** Керований приватний repository для пакетів і програмних
залежностей.

## Словник термінів

| Термін                  | Визначення українською                                                                                        |
|-------------------------|---------------------------------------------------------------------------------------------------------------|
| **Domain**              | Керований deployment OpenSearch Service, що містить кластер, мережеві та security налаштування.               |
| **Repository**          | Логічне сховище CodeArtifact packages або ECR container images; конкретна структура залежить від сервісу.     |
| **Package**             | Окрема бібліотека або програмний компонент, опублікований у package repository разом із версіями та metadata. |
| **Package Version**     | Конкретний незмінний реліз пакета з власними artifacts і metadata.                                            |
| **npm**                 | JavaScript package manager/registry format, який CodeArtifact може проксувати, зберігати та обслуговувати.    |
| **Maven**               | Java build ecosystem і формат координат/артефактів, який CodeArtifact підтримує як repository format.         |
| **PyPI**                | Python Package Index — екосистема пакетів Python, яку CodeArtifact може зберігати та обслуговувати.           |
| **NuGet**               | .NET package ecosystem, який CodeArtifact підтримує для зберігання та поширення пакетів.                      |
| **Upstream Repository** | Інший CodeArtifact repository, з якого repository може отримувати packages, якщо локально їх немає.           |
| **External Connection** | Зв’язок CodeArtifact repository з публічним package repository, наприклад npmjs або PyPI.                     |
| **Repository Policy**   | Resource policy CodeArtifact repository, яка визначає, які principals можуть читати/публікувати packages.     |
| **Auth Token**          | Тимчасовий authorization token, який клієнт використовує для автентифікації до CodeArtifact repository.       |
| **Publish**             | Операція завантаження нової package version до CodeArtifact repository.                                       |
| **Install**             | Операція отримання package та його залежностей із налаштованого repository.                                   |

## Типовий екзаменаційний сценарій

Потрібен приватний package registry для build dependencies →
CodeArtifact.

## Екзаменаційна пастка

CodeArtifact зберігає пакети; ECR зберігає container images.

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

- [AWS Documentation — AWS CodeArtifact](https://docs.aws.amazon.com/)
- [DVA-C02 Exam
  Guide](https://docs.aws.amazon.com/aws-certification/latest/developer-associate-02/developer-associate-02.html)
