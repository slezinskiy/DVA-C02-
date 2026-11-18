# Management and Governance — довідник DVA-C02

Тематичний довідник із визначеннями термінів, практичними сценаріями та
типовими екзаменаційними пастками.

## AWS AppConfig

**Призначення:** Кероване розповсюдження конфігурацій і feature flags
без повного redeploy.

### Ключові терміни

| Термін                    | Визначення українською                                                                                   |
|---------------------------|----------------------------------------------------------------------------------------------------------|
| **Application**           | Логічний контейнер AppConfig для configuration profiles та environments одного застосунку.               |
| **Environment**           | Набір AWS-ресурсів Elastic Beanstalk, на якому працює конкретна версія застосунку.                       |
| **Configuration Profile** | Опис джерела конфігурації, її типу та validator у межах application.                                     |
| **Hosted Configuration**  | Конфігураційний документ, який зберігається безпосередньо в AWS AppConfig.                               |
| **Deployment Strategy**   | Налаштування швидкості поширення конфігурації, відсотків rollout та bake time.                           |
| **Gradual Deployment**    | Поступове розгортання конфігурації на частину targets із подальшим збільшенням охоплення.                |
| **Validator**             | Lambda function або JSON Schema, що перевіряє конфігурацію перед deployment.                             |
| **Feature Flag**          | Прапорець конфігурації, що вмикає або вимикає функціональність без зміни та повторного розгортання коду. |
| **Rollback**              | Повернення до попередньої конфігурації після помилок або спрацювання alarm thresholds.                   |
| **Agent**                 | AppConfig Agent, який отримує, кешує та надає конфігурацію локальному застосунку.                        |
| **Extension**             | Розширення AppConfig, яке запускає інтеграційні дії на певних етапах lifecycle.                          |

**Типовий екзаменаційний сценарій:** Потрібно поступово змінювати
runtime configuration/feature flags → AppConfig.

**Екзаменаційна пастка:** Parameter Store зберігає параметри; AppConfig
керує контрольованим rollout конфігурації.

------------------------------------------------------------------------

## AWS CDK

**Призначення:** IaC framework, що дозволяє описувати AWS resources
мовами програмування та синтезувати CloudFormation.

### Ключові терміни

| Термін          | Визначення українською                                                                                                       |
|-----------------|------------------------------------------------------------------------------------------------------------------------------|
| **App**         | Кореневий контейнер AWS CDK application, що містить один або кілька stacks.                                                  |
| **Stack**       | Одиниця CDK deployment, яка синтезується в CloudFormation stack.                                                             |
| **Construct**   | Будівельний блок AWS CDK, який інкапсулює один або кілька AWS resources та їх конфігурацію.                                  |
| **L1/L2/L3**    | Рівні CDK constructs: L1 відображає CloudFormation resources, L2 надає зручні абстракції, L3 — готові архітектурні patterns. |
| **Synthesis**   | Етап CDK, на якому application перетворюється на CloudFormation templates (cloud assemblies).                                |
| **Bootstrap**   | Підготовка AWS environment до CDK deployment: створення ресурсів для assets і deployment roles.                              |
| **Context**     | Об’єкт Lambda context із метаданими поточного invocation: request ID, назва функції, memory limit і час до timeout.          |
| **Asset**       | Файл або Docker image, який CDK завантажує/публікує в bootstrap resources перед deployment.                                  |
| **Environment** | Набір AWS-ресурсів Elastic Beanstalk, на якому працює конкретна версія застосунку.                                           |
| **cdk diff**    | Команда, що порівнює локально синтезований template із розгорнутим stack і показує очікувані зміни.                          |
| **cdk deploy**  | Команда, що синтезує та розгортає CDK stack через CloudFormation.                                                            |

**Типовий екзаменаційний сценарій:** Потрібна програмна абстракція для
IaC → CDK.

**Екзаменаційна пастка:** CDK синтезує CloudFormation templates; саме
CloudFormation виконує deployment.

------------------------------------------------------------------------

## AWS CLI

**Призначення:** Командний інтерфейс для виклику AWS APIs та
автоматизації.

### Ключові терміни

| Термін                        | Визначення українською                                                                                                |
|-------------------------------|-----------------------------------------------------------------------------------------------------------------------|
| **Profile**                   | Named set of AWS CLI credentials та settings у config/credentials files.                                              |
| **Region**                    | AWS географічний регіон, до якого CLI надсилає запити, якщо команда не задає інше.                                    |
| **Output**                    | Формат виводу AWS CLI, наприклад json, yaml, text або table.                                                          |
| **–query/JMESPath**           | Параметр –query використовує JMESPath для фільтрації та перетворення JSON-відповіді перед виведенням.                 |
| **Pagination**                | Автоматичне отримання кількох сторінок API results, коли сервіс повертає continuation token.                          |
| **–no-paginate**              | Вимикає автоматичне отримання наступних сторінок і повертає лише першу відповідь API.                                 |
| **–page-size**                | Задає кількість елементів, яку CLI запитує на одній сторінці від сервісу.                                             |
| **–max-items**                | Обмежує загальну кількість елементів, які CLI повертає користувачу.                                                   |
| **–starting-token**           | Дозволяє продовжити пагінований результат із token, отриманого попереднім CLI-викликом.                               |
| **–dry-run**                  | Параметр для підтримуваних API, що перевіряє можливість виконання операції без фактичної зміни ресурсу.               |
| **–debug**                    | Вмикає детальний debug output CLI, включно з діагностикою запитів і відповідей.                                       |
| **Credential Provider Chain** | Порядок джерел, з яких AWS CLI/SDK шукає credentials: environment, profile, role, SSO та інші підтримувані providers. |

**Типовий екзаменаційний сценарій:** Потрібно автоматизувати AWS
operations у shell/CI → AWS CLI.

**Екзаменаційна пастка:** `--query` фільтрує вивід CLI; це не те саме,
що API-side `--filter` параметр.

------------------------------------------------------------------------

## AWS CloudFormation

**Призначення:** IaC сервіс для декларативного створення й оновлення AWS
resources.

### Ключові терміни

| Термін                  | Визначення українською                                                                                                        |
|-------------------------|-------------------------------------------------------------------------------------------------------------------------------|
| **Template**            | JSON/YAML декларативний опис AWS resources, parameters, conditions, mappings і outputs.                                       |
| **Stack**               | Керована група ресурсів, створена з template та оновлювана як одна одиниця.                                                   |
| **Resource**            | AWS ресурс, оголошений у секції Resources template; CloudFormation створює та керує його життєвим циклом.                     |
| **Parameter**           | Вхідне значення template, яке користувач передає під час створення чи оновлення stack.                                        |
| **Output**              | Значення, яке CloudFormation показує або експортує після deployment, наприклад ARN чи endpoint.                               |
| **Mapping**             | Опис типів полів і правил індексації документів у OpenSearch.                                                                 |
| **Condition**           | Логічний вираз, що визначає, чи створювати ресурс або застосовувати властивість.                                              |
| **Intrinsic Function**  | Вбудована функція template, наприклад Ref, Fn::GetAtt, Fn::Sub або Fn::Join, для посилань та обчислень.                       |
| **Change Set**          | Попередній план змін CloudFormation stack, який показує, які ресурси буде створено, змінено або видалено до виконання update. |
| **Drift Detection**     | Механізм CloudFormation, який порівнює фактичну конфігурацію ресурсів із конфігурацією, описаною у template.                  |
| **Stack Policy**        | JSON policy, що обмежує, які ресурси дозволено змінювати під час stack update.                                                |
| **DeletionPolicy**      | Атрибут, який визначає долю ресурсу при видаленні зі stack: Delete, Retain або Snapshot (де підтримується).                   |
| **UpdateReplacePolicy** | Атрибут, який визначає долю старого фізичного ресурсу, коли update вимагає його заміни.                                       |
| **DependsOn**           | Атрибут, що задає явну залежність і порядок створення/видалення ресурсів.                                                     |
| **Nested Stack**        | CloudFormation stack, вкладений як resource в інший stack для модульної організації template.                                 |
| **StackSet**            | Механізм розгортання template у багатьох AWS accounts і Regions.                                                              |
| **Custom Resource**     | Ресурс із користувацькою логікою provisioning, яку реалізує Lambda або SNS-backed provider.                                   |
| **Rollback**            | Повернення stack до попереднього стану після невдалого create/update.                                                         |

**Типовий екзаменаційний сценарій:** Потрібно повторювано створювати
інфраструктуру з template → CloudFormation.

**Екзаменаційна пастка:** Drift — різниця між template і фактичним
ресурсом. Retain зберігає ресурс після видалення stack.

------------------------------------------------------------------------

## AWS CloudTrail

**Призначення:** Аудит AWS API activity та подій акаунта.

### Ключові терміни

| Термін                 | Визначення українською                                                                                                          |
|------------------------|---------------------------------------------------------------------------------------------------------------------------------|
| **Management Event**   | CloudTrail подія керування AWS ресурсом або конфігурацією, наприклад створення EC2 instance чи зміна IAM policy.                |
| **Data Event**         | CloudTrail подія доступу до даних усередині ресурсу, наприклад GetObject/PutObject для S3; зазвичай потребує явного ввімкнення. |
| **Read/Write Event**   | Класифікація management events: read-only події читають стан, write events змінюють ресурси або конфігурацію.                   |
| **Trail**              | Конфігурація CloudTrail, яка доставляє event logs до S3 і, за потреби, CloudWatch Logs.                                         |
| **Event History**      | Перегляд останніх 90 днів management events у регіоні без створення trail.                                                      |
| **CloudTrail Lake**    | Кероване сховище event data з SQL-подібними запитами для аудиту та розслідувань.                                                |
| **Insights**           | Функція, що виявляє аномальні зміни обсягу API calls або частоти помилок management events.                                     |
| **Multi-Region Trail** | Trail, який записує події з усіх увімкнених AWS Regions account.                                                                |
| **Organization Trail** | Trail організації AWS Organizations, що централізовано збирає події member accounts.                                            |
| **Log Integrity**      | Перевірка незмінності CloudTrail logs за допомогою digest files і криптографічних хешів.                                        |
| **UserIdentity**       | Поле event, яке описує IAM/federated identity, що ініціювала API request.                                                       |
| **EventSource**        | Поле з назвою AWS service endpoint, який отримав API request, наприклад ec2.amazonaws.com.                                      |
| **EventName**          | Поле з назвою викликаної API operation, наприклад RunInstances.                                                                 |

**Типовий екзаменаційний сценарій:** Потрібно з’ясувати, хто виконав AWS
API дію → CloudTrail.

**Екзаменаційна пастка:** CloudTrail не замінює application logs у
CloudWatch.

------------------------------------------------------------------------

## Amazon CloudWatch

**Призначення:** Моніторинг metrics, logs, alarms, dashboards і
operational telemetry.

### Ключові терміни

| Термін                  | Визначення українською                                                                                                         |
|-------------------------|--------------------------------------------------------------------------------------------------------------------------------|
| **Metric**              | Числовий показник, виміряний у часі, наприклад CPU utilization або кількість помилок.                                          |
| **Namespace**           | Логічний контейнер CloudWatch metrics, який розділяє метрики за сервісом або застосунком.                                      |
| **Dimension**           | Пара атрибут-значення, що ідентифікує конкретний ресурс або варіант метрики.                                                   |
| **Statistic**           | Агрегат метрики за період: Average, Sum, Minimum, Maximum або SampleCount.                                                     |
| **Period**              | Часовий інтервал, за який CloudWatch агрегує datapoints для графіка або alarm.                                                 |
| **Resolution**          | Частота metric datapoints; custom metrics можуть мати standard або high resolution.                                            |
| **Custom Metric**       | Метрика, яку застосунок публікує в CloudWatch через API або Embedded Metric Format.                                            |
| **Log Group**           | Контейнер CloudWatch Logs для log streams зі спільними налаштуваннями retention та permissions.                                |
| **Log Stream**          | Послідовність log events від одного джерела або екземпляра джерела всередині log group.                                        |
| **Log Event**           | Окремий запис CloudWatch Logs із timestamp і message.                                                                          |
| **Retention**           | Період зберігання log events у log group, після якого старі записи видаляються.                                                |
| **Metric Filter**       | Правило CloudWatch Logs, що знаходить шаблони в log events і перетворює збіги на CloudWatch metric.                            |
| **Subscription Filter** | Фільтр, який передає відповідні log events у Lambda, Kinesis або Firehose.                                                     |
| **Logs Insights**       | Query engine для пошуку, фільтрації та агрегації CloudWatch Logs.                                                              |
| **Alarm**               | CloudWatch об’єкт, який порівнює metric або expression із порогом/умовою та переходить у стан OK, ALARM або INSUFFICIENT_DATA. |
| **Composite Alarm**     | Alarm, який комбінує стани інших alarms логічним виразом.                                                                      |
| **Dashboard**           | Панель CloudWatch із графіками, alarms та віджетами для спостереження.                                                         |
| **Anomaly Detection**   | Функція, яка навчається на історії метрики та формує очікуваний діапазон значень.                                              |
| **Agent**               | CloudWatch Agent, що збирає системні metrics і logs із EC2/on-premises servers.                                                |
| **EMF**                 | Embedded Metric Format — JSON формат log events, з якого CloudWatch автоматично витягує custom metrics.                        |

**Типовий екзаменаційний сценарій:** Потрібно створити alarm за
помилками або latency → CloudWatch.

**Екзаменаційна пастка:** Metric Filter перетворює логи на метрики;
X-Ray — окремий distributed tracing сервіс.

------------------------------------------------------------------------

## AWS Systems Manager

**Призначення:** Операційне керування EC2/hybrid nodes, параметрами,
патчами та автоматизацією.

### Ключові терміни

| Термін                 | Визначення українською                                                                                       |
|------------------------|--------------------------------------------------------------------------------------------------------------|
| **SSM Agent**          | Агент на managed node, який отримує та виконує Systems Manager commands.                                     |
| **Managed Node**       | EC2 або підтримуваний on-premises/server node, зареєстрований у Systems Manager.                             |
| **Session Manager**    | Можливість Systems Manager для інтерактивного доступу до managed nodes без відкриття inbound SSH/RDP портів. |
| **Run Command**        | Systems Manager функція віддаленого виконання команд або документів на одному чи багатьох managed nodes.     |
| **Automation**         | Можливість Systems Manager автоматизувати операції над AWS resources та managed nodes через runbooks.        |
| **Document**           | JSON/YAML опис команди, automation workflow або інструкцій для managed nodes.                                |
| **Runbook**            | Automation document із послідовністю кроків для remediation або maintenance.                                 |
| **Parameter Store**    | Ієрархічне сховище Systems Manager для конфігураційних значень і SecureString secrets.                       |
| **SecureString**       | Зашифрований параметр Systems Manager Parameter Store, який використовує AWS KMS для захисту значення.       |
| **Patch Manager**      | Функція для сканування та встановлення OS patches на managed nodes.                                          |
| **Maintenance Window** | Розкладений часовий інтервал для виконання maintenance tasks на вибраних targets.                            |
| **State Manager**      | Механізм підтримки бажаного стану managed nodes через associations із documents.                             |
| **Inventory**          | Збір metadata про managed nodes: software, configuration, network та інші дані.                              |
| **Distributor**        | Функція для пакування, публікації та розгортання програмних пакетів на managed nodes.                        |
| **OpsCenter**          | Інструмент для централізації operational issues (OpsItems) та їх розслідування.                              |

**Типовий екзаменаційний сценарій:** Потрібен shell до EC2 без відкриття
SSH port або віддалений запуск команд → Systems Manager.

**Екзаменаційна пастка:** Session Manager потребує SSM Agent, IAM
permissions і мережевого доступу до SSM endpoints.

------------------------------------------------------------------------
