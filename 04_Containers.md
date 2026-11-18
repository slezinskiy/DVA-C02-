# Containers — довідник DVA-C02

Тематичний довідник із визначеннями термінів, практичними сценаріями та
типовими екзаменаційними пастками.

## Amazon ECR

**Призначення:** Керований registry для зберігання OCI/Docker container
images.

### Ключові терміни

| Термін                   | Визначення українською                                                                                                   |
|--------------------------|--------------------------------------------------------------------------------------------------------------------------|
| **Registry**             | Приватний або публічний реєстр ECR, що містить repositories container images.                                            |
| **Repository**           | Логічне сховище CodeArtifact packages або ECR container images; конкретна структура залежить від сервісу.                |
| **Image**                | Незмінний пакет шарів і metadata, з якого запускається container.                                                        |
| **Tag**                  | Людиночитна мітка образу, наприклад v1.2; може вказувати на інший digest, якщо tags mutable.                             |
| **Digest**               | Криптографічний hash образу або артефакту, який ідентифікує точний вміст незалежно від tag.                              |
| **Layer**                | Окремий файловий шар container image, який може спільно використовуватися різними образами.                              |
| **Lifecycle Policy**     | Правила ECR для автоматичного expiration або архівування образів, наприклад видалення старих чи невикористовуваних tags. |
| **Image Scanning**       | Перевірка container images на відомі vulnerabilities у packages і залежностях.                                           |
| **Enhanced Scanning**    | Безперервне vulnerability scanning через Amazon Inspector із оновленням findings.                                        |
| **Repository Policy**    | Resource policy ECR repository, яка визначає доступ principals/accounts до push/pull.                                    |
| **Authentication Token** | Тимчасовий Docker password, отриманий через GetAuthorizationToken для login до ECR.                                      |
| **Cross-account Access** | Надання іншому AWS account дозволу push/pull через repository policy та IAM permissions.                                 |
| **Replication**          | Автоматичне копіювання ECR images між Regions або accounts.                                                              |

**Типовий екзаменаційний сценарій:** ECS/EKS має завантажити приватний
контейнерний образ → ECR плюс IAM/repository policy.

**Екзаменаційна пастка:** ECR зберігає образи, але не запускає
контейнери.

------------------------------------------------------------------------

## Amazon ECS

**Призначення:** AWS-native оркестратор контейнерів на EC2 або Fargate.

### Ключові терміни

| Термін                   | Визначення українською                                                                                                         |
|--------------------------|--------------------------------------------------------------------------------------------------------------------------------|
| **Cluster**              | Логічна група ECS tasks, services і capacity providers.                                                                        |
| **Task Definition**      | Шаблон ECS task: опис контейнерів, образів, CPU/memory, мережі, volumes, logging та IAM roles.                                 |
| **Task**                 | Запущений екземпляр ECS task definition, який містить один або кілька контейнерів.                                             |
| **Service**              | Контролер ECS, що підтримує desired count tasks і керує їх deployments та load balancing.                                      |
| **Container Definition** | Опис одного контейнера в task definition: image, ports, resources, environment, logging і secrets.                             |
| **EC2 Launch Type**      | Режим ECS, де tasks розміщуються на EC2 instances, якими керує користувач.                                                     |
| **Fargate**              | Serverless compute engine для контейнерів, де AWS керує серверами, а користувач задає ресурси task.                            |
| **Capacity Provider**    | Механізм ECS для визначення способу надання capacity через Fargate або EC2 Auto Scaling.                                       |
| **Desired Count**        | Кількість tasks, яку ECS service має підтримувати.                                                                             |
| **Deployment**           | Процес заміни старих tasks новою revision task definition.                                                                     |
| **Task Role**            | IAM role, доступна коду всередині ECS task для звернення до AWS services.                                                      |
| **Task Execution Role**  | IAM role, яку ECS agent/Fargate використовує для запуску task: завантаження image з ECR, надсилання logs та отримання secrets. |
| **awsvpc**               | ECS network mode, у якому кожен task отримує власний ENI та приватну IP-адресу.                                                |
| **Service Discovery**    | Інтеграція ECS із AWS Cloud Map для виявлення tasks через DNS/API.                                                             |
| **Health Check**         | Перевірка стану container або load balancer target, що впливає на заміну task і routing.                                       |
| **Service Auto Scaling** | Автоматична зміна desired count ECS service на основі CloudWatch metrics/policies.                                             |
| **ECS Exec**             | Механізм запуску команд у працюючому контейнері ECS через захищений канал.                                                     |

**Типовий екзаменаційний сценарій:** Потрібно запускати контейнери без
Kubernetes control plane → ECS.

**Екзаменаційна пастка:** Task Role належить застосунку в контейнері;
Task Execution Role потрібна агенту ECS для pull image, logs та startup
secrets.

------------------------------------------------------------------------

## Amazon EKS

**Призначення:** Керований Kubernetes control plane для запуску
Kubernetes workloads.

### Ключові терміни

| Термін                 | Визначення українською                                                                                                                            |
|------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------|
| **Cluster**            | EKS cluster — кероване середовище Kubernetes у конкретному AWS Region, що включає control plane і підключені compute nodes або Fargate workloads. |
| **Control Plane**      | Керована AWS частина Kubernetes: API server, etcd та компоненти керування кластером.                                                              |
| **Worker Node**        | Вузол, на якому запускаються Kubernetes Pods; може бути EC2 або Fargate.                                                                          |
| **Managed Node Group** | Група EC2 worker nodes, життєвим циклом якої керує EKS.                                                                                           |
| **Fargate Profile**    | Правило, що визначає, які EKS Pods запускати на Fargate.                                                                                          |
| **Pod**                | Найменша deployable одиниця Kubernetes, що містить один або кілька тісно пов’язаних контейнерів із shared network/storage context.                |
| **Deployment**         | Kubernetes controller, який керує ReplicaSets і підтримує бажану кількість Pod, rollout та rollback.                                              |
| **ReplicaSet**         | Kubernetes controller, який підтримує задану кількість Pod replicas.                                                                              |
| **Service**            | Стабільна мережна абстракція Kubernetes для доступу до групи Pods через selector і virtual IP/DNS.                                                |
| **Ingress**            | Kubernetes ресурс для маршрутизації HTTP/HTTPS трафіку до Services; потребує ingress controller.                                                  |
| **ConfigMap**          | Kubernetes об’єкт для несекретних конфігураційних даних.                                                                                          |
| **Secret**             | Kubernetes об’єкт для чутливих значень; безпека залежить від RBAC та encryption at rest.                                                          |
| **Namespace**          | Логічний простір імен Kubernetes для групування та ізоляції ресурсів.                                                                             |
| **kubeconfig**         | Файл kubectl із параметрами cluster, user authentication і context.                                                                               |
| **IAM Auth**           | Автентифікація клієнта Kubernetes API через AWS IAM identity.                                                                                     |
| **Access Entries**     | Механізм EKS для зіставлення IAM principals із Kubernetes access policies/groups.                                                                 |
| **IRSA**               | IAM Roles for Service Accounts — механізм EKS, що дозволяє Kubernetes service account отримати IAM role через OIDC federation.                    |
| **Pod Identity**       | Механізм EKS для надання IAM role Pods через EKS Pod Identity Agent та associations.                                                              |
| **CNI**                | Container Network Interface; AWS VPC CNI надає Pods IP-адреси з VPC.                                                                              |
| **Add-on**             | Підтримуваний пакет Kubernetes infrastructure software, наприклад VPC CNI, CoreDNS або kube-proxy.                                                |
| **HPA**                | Horizontal Pod Autoscaler — controller, який змінює кількість Pods за CPU/memory/custom metrics.                                                  |
| **Cluster Autoscaler** | Компонент, що змінює кількість worker nodes, коли Pods не можуть бути розміщені або capacity надлишкова.                                          |

**Типовий екзаменаційний сценарій:** Потрібна сумісність із Kubernetes
API та ecosystem → EKS.

**Екзаменаційна пастка:** EKS не є ECS. Розрізняйте IAM доступ до
cluster API та IAM Role для AWS API з Pod.

------------------------------------------------------------------------
