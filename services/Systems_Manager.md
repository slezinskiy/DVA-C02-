# AWS Systems Manager

**Категорія:** Management and Governance  
**Призначення:** Операційне керування EC2/hybrid nodes, параметрами,
патчами та автоматизацією.

## Словник термінів

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

## Типовий екзаменаційний сценарій

Потрібен shell до EC2 без відкриття SSH port або віддалений запуск
команд → Systems Manager.

## Екзаменаційна пастка

Session Manager потребує SSM Agent, IAM permissions і мережевого доступу
до SSM endpoints.

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

- [AWS Documentation — AWS Systems
  Manager](https://docs.aws.amazon.com/)
- [DVA-C02 Exam
  Guide](https://docs.aws.amazon.com/aws-certification/latest/developer-associate-02/developer-associate-02.html)
