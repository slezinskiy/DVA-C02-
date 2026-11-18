# Amazon EKS

**Категорія:** Containers  
**Призначення:** Керований Kubernetes control plane для запуску
Kubernetes workloads.

## Словник термінів

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

## Типовий екзаменаційний сценарій

Потрібна сумісність із Kubernetes API та ecosystem → EKS.

## Екзаменаційна пастка

EKS не є ECS. Розрізняйте IAM доступ до cluster API та IAM Role для AWS
API з Pod.

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

- [AWS Documentation — Amazon EKS](https://docs.aws.amazon.com/)
- [DVA-C02 Exam
  Guide](https://docs.aws.amazon.com/aws-certification/latest/developer-associate-02/developer-associate-02.html)
