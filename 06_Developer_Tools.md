# Developer Tools — довідник DVA-C02

Тематичний довідник із визначеннями термінів, практичними сценаріями та
типовими екзаменаційними пастками.

## AWS Amplify

**Призначення:** Інструменти для frontend hosting та
створення/підключення backend можливостей.

### Ключові терміни

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

**Типовий екзаменаційний сценарій:** Потрібен Git-based hosting frontend
із build/deploy → Amplify Hosting.

**Екзаменаційна пастка:** Amplify — не універсальна заміна всім
backend-сервісам; перевіряйте, які саме ресурси він створює.

------------------------------------------------------------------------

## AWS CloudShell

**Призначення:** Браузерна shell-сесія з AWS CLI та інструментами для
роботи з AWS.

### Ключові терміни

| Термін              | Визначення українською                                                                                       |
|---------------------|--------------------------------------------------------------------------------------------------------------|
| **Browser Shell**   | Браузерне shell-середовище AWS із попередньо автентифікованим доступом до account та AWS CLI.                |
| **IAM Session**     | CloudShell працює з IAM identity поточного AWS Console session і використовує її permissions.                |
| **Persistent Home** | Домашній каталог CloudShell зберігає файли між сесіями в межах відповідного Region та квот.                  |
| **AWS CLI**         | Командний інтерфейс для виклику AWS APIs; у CloudShell зазвичай уже встановлений і налаштований.             |
| **Upload/Download** | Можливість передавати файли між локальним комп’ютером і CloudShell environment.                              |
| **Region**          | AWS Region, у якому створено CloudShell environment і зберігається його home directory.                      |
| **Profile**         | AWS CLI named profile із credentials/settings; у CloudShell часто використовується поточна Console identity. |

**Типовий екзаменаційний сценарій:** Потрібен CLI без локального
встановлення інструментів → CloudShell.

**Екзаменаційна пастка:** CloudShell не є EC2, яким користувач
адмініструє ОС.

------------------------------------------------------------------------

## AWS CodeArtifact

**Призначення:** Керований приватний repository для пакетів і програмних
залежностей.

### Ключові терміни

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

**Типовий екзаменаційний сценарій:** Потрібен приватний package registry
для build dependencies → CodeArtifact.

**Екзаменаційна пастка:** CodeArtifact зберігає пакети; ECR зберігає
container images.

------------------------------------------------------------------------

## AWS CodeBuild

**Призначення:** Керований build/test service для компіляції коду та
створення артефактів.

### Ключові терміни

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

**Типовий екзаменаційний сценарій:** Потрібно компілювати й тестувати
код у CI → CodeBuild.

**Екзаменаційна пастка:** CodeBuild не оркеструє весь pipeline і не є
deployment service.

------------------------------------------------------------------------

## AWS CodeDeploy

**Призначення:** Автоматизоване розгортання застосунків на EC2,
on-premises, Lambda та ECS.

### Ключові терміни

| Термін                       | Визначення українською                                                                               |
|------------------------------|------------------------------------------------------------------------------------------------------|
| **Application**              | Логічний контейнер CodeDeploy для deployment groups і revisions.                                     |
| **Deployment Group**         | Набір targets і правил розгортання для CodeDeploy application.                                       |
| **Revision**                 | Версія пакета застосунку, яку CodeDeploy розгортає на targets.                                       |
| **AppSpec**                  | Файл, що описує файли, permissions, lifecycle hooks або deployment configuration.                    |
| **Lifecycle Event**          | Етап deployment, на якому CodeDeploy запускає визначені scripts/hooks.                               |
| **Hook**                     | Користувацький script або Lambda hook, що запускається на певному lifecycle event.                   |
| **In-place**                 | Оновлення застосунку на тих самих instances; під час deployment можлива тимчасова недоступність.     |
| **Blue/Green**               | Розгортання нової версії в окремому середовищі з подальшим перемиканням traffic.                     |
| **Canary**                   | Стратегія traffic shifting: спочатку невелика частка трафіку переходить на нову версію, потім решта. |
| **Linear**                   | Стратегія, що збільшує частку трафіку на нову версію рівними кроками через інтервали.                |
| **Rollback**                 | Повернення deployment до попередньої працездатної revision після помилки або за ручним запитом.      |
| **Deployment Configuration** | Параметри швидкості оновлення instances або traffic shifting під час deployment.                     |
| **Agent**                    | CodeDeploy agent на EC2/on-premises instance, який отримує deployment instructions і виконує їх.     |

**Типовий екзаменаційний сценарій:** Потрібно контролювати rollout і
lifecycle hooks → CodeDeploy.

**Екзаменаційна пастка:** CodeDeploy розгортає; CodeBuild збирає;
CodePipeline координує.

------------------------------------------------------------------------

## AWS CodePipeline

**Призначення:** Керований CI/CD pipeline, що з’єднує source, build,
test, approval та deploy actions.

### Ключові терміни

| Термін                  | Визначення українською                                                                          |
|-------------------------|-------------------------------------------------------------------------------------------------|
| **Pipeline**            | Автоматизований workflow доставки змін від source через build/test до deploy.                   |
| **Stage**               | Послідовний етап pipeline, який містить actions і виконується у визначеному порядку.            |
| **Action**              | Операція всередині CodePipeline stage, наприклад Source, Build, Test, Approval або Deploy.      |
| **Source**              | Етап або provider pipeline, який отримує вихідний код/артефакт із Git, S3 чи іншого джерела.    |
| **Build**               | Етап CI, що компілює код, запускає тести та формує build artifacts.                             |
| **Deploy**              | Етап доставки application artifact до цільового середовища.                                     |
| **Artifact**            | Файл або набір файлів, переданий між actions/stages через artifact store.                       |
| **Artifact Store**      | S3 bucket, де CodePipeline зберігає artifacts між actions і stages.                             |
| **Approval**            | Manual approval action, що призупиняє pipeline до рішення уповноваженої особи.                  |
| **Change Detection**    | Механізм виявлення змін у source provider, який запускає нове pipeline execution.               |
| **Execution Mode**      | Режим обробки паралельних запусків pipeline: SUPERSEDED, QUEUED або PARALLEL.                   |
| **Cross-Region Action** | Action в іншому AWS Region; потребує належних permissions і artifact store у регіоні виконання. |

**Типовий екзаменаційний сценарій:** Потрібен workflow від commit до
deployment → CodePipeline.

**Екзаменаційна пастка:** Pipeline складається з stages/actions; сам
build може виконувати CodeBuild.

------------------------------------------------------------------------

## Amazon Q Developer

**Призначення:** AI-помічник розробника для генерації, пояснення,
тестування та модернізації коду.

### Ключові терміни

| Термін              | Визначення українською                                                                         |
|---------------------|------------------------------------------------------------------------------------------------|
| **Code Completion** | Підказки коду в IDE, згенеровані на основі контексту поточного файлу/проєкту.                  |
| **Code Generation** | Створення коду або фрагментів за природномовним запитом і контекстом.                          |
| **IDE Integration** | Підключення Amazon Q Developer до IDE для code suggestions, chat та developer workflows.       |
| **Refactoring**     | Перебудова структури коду для підтримуваності без зміни зовнішньої поведінки.                  |
| **Transformation**  | Допомога в оновленні застосунку, runtime або мовної версії.                                    |
| **Agentic Coding**  | Багатокрокова робота AI агента з аналізом репозиторію та внесенням змін у код.                 |
| **Context**         | Код, файли та інструкції, які Q Developer враховує під час відповіді або генерації.            |
| **Data Privacy**    | Правила обробки коду й даних користувача, включно з налаштуваннями використання content.       |
| **Responsible AI**  | Практики відповідального використання AI: перевірка результатів, безпека та людський контроль. |
| **Code Review**     | Аналіз змін коду для пошуку дефектів, проблем якості та потенційних security issues.           |

**Типовий екзаменаційний сценарій:** Потрібна AI-assisted допомога в IDE
або AWS development workflow → Q Developer.

**Екзаменаційна пастка:** Згенерований код потрібно перевіряти,
тестувати та сканувати; AI не замінює security review.

------------------------------------------------------------------------

## AWS X-Ray

**Призначення:** Distributed tracing для аналізу шляху запиту через
сервіси.

### Ключові терміни

| Термін              | Визначення українською                                                                                                |
|---------------------|-----------------------------------------------------------------------------------------------------------------------|
| **Trace**           | Набір пов’язаних даних X-Ray про шлях одного запиту через розподілену систему.                                        |
| **Segment**         | Частина X-Ray trace, що описує роботу одного сервісу або компонента під час обробки запиту.                           |
| **Subsegment**      | Вкладена частина segment, що деталізує операцію, наприклад виклик БД або HTTP-запит.                                  |
| **Trace ID**        | Глобальний ідентифікатор trace, що пов’язує сегменти одного запиту між сервісами.                                     |
| **Sampling**        | Вибірковий запис traces для контролю обсягу telemetry та вартості.                                                    |
| **Sampling Rule**   | Правило, що визначає, які запити записувати, на основі service, URL, HTTP method та інших умов.                       |
| **Annotation**      | Індексовані структуровані поля X-Ray trace, які можна використовувати у фільтрах пошуку.                              |
| **Metadata**        | Додаткові довільні дані X-Ray trace, які зберігаються для діагностики, але не індексуються для пошуку як annotations. |
| **Service Map**     | Візуалізація сервісів і залежностей, побудована на основі X-Ray traces.                                               |
| **Trace Context**   | Контекст поточного trace, який передається між сервісами для кореляції distributed request.                           |
| **Instrumentation** | Додавання SDK, agent або автоматичної інструментації для збору trace data.                                            |

**Типовий екзаменаційний сценарій:** Потрібно знайти, який сервіс
спричиняє latency у distributed request → X-Ray.

**Екзаменаційна пастка:** CloudWatch — metrics/logs/alarms; X-Ray —
trace одного запиту та залежностей.

------------------------------------------------------------------------
