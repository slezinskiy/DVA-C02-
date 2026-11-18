# AWS CDK

**Категорія:** Management and Governance  
**Призначення:** IaC framework, що дозволяє описувати AWS resources
мовами програмування та синтезувати CloudFormation.

## Словник термінів

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

## Типовий екзаменаційний сценарій

Потрібна програмна абстракція для IaC → CDK.

## Екзаменаційна пастка

CDK синтезує CloudFormation templates; саме CloudFormation виконує
deployment.

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

- [AWS Documentation — AWS CDK](https://docs.aws.amazon.com/)
- [DVA-C02 Exam
  Guide](https://docs.aws.amazon.com/aws-certification/latest/developer-associate-02/developer-associate-02.html)
