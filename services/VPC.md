# Amazon VPC

**Категорія:** Networking and Content Delivery  
**Призначення:** Ізольована мережа AWS із CIDR, subnets, routes,
security controls та endpoints.

## Словник термінів

| Термін                         | Визначення українською                                                                                                            |
|--------------------------------|-----------------------------------------------------------------------------------------------------------------------------------|
| **VPC**                        | Ізольована логічна мережа AWS із CIDR, subnets, route tables та network controls.                                                 |
| **CIDR**                       | Нотація діапазону IP-адрес, наприклад 10.0.0.0/16.                                                                                |
| **Subnet**                     | Діапазон IP-адрес у VPC, який належить одній Availability Zone.                                                                   |
| **Public/Private Subnet**      | Public subnet має route до Internet Gateway; private subnet не має прямого inbound/outbound маршруту через IGW.                   |
| **Route Table**                | Набір маршрутів, що визначає next hop для трафіку з subnet.                                                                       |
| **IGW**                        | Internet Gateway — компонент VPC для маршрутизації між VPC та інтернетом.                                                         |
| **NAT Gateway**                | Керований NAT для outbound internet access із private subnet; не приймає ініційовані з інтернету inbound connections.             |
| **Security Group**             | Stateful virtual firewall для ENI/resource. Дозволяє правила allow; відповідь на дозволене з’єднання пропускається автоматично.   |
| **NACL**                       | Network ACL — stateless firewall на рівні subnet із правилами allow і deny; потрібно явно враховувати inbound та outbound трафік. |
| **Gateway/Interface Endpoint** | Gateway endpoint маршрутизує S3/DynamoDB через route tables; interface endpoint створює ENI та використовує PrivateLink.          |
| **PrivateLink**                | Технологія приватного доступу до сервісів через interface endpoints.                                                              |
| **Peering**                    | Приватне з’єднання двох VPC; peering не підтримує транзитивну маршрутизацію.                                                      |
| **Transit Gateway**            | Центральний hub для з’єднання багатьох VPC та on-premises networks.                                                               |
| **Flow Logs**                  | Записи metadata про IP traffic до/з VPC, subnet або ENI.                                                                          |
| **ENI**                        | Elastic Network Interface — віртуальна мережева карта з IP addresses і security groups.                                           |
| **EIP**                        | Elastic IP — статична публічна IPv4 адреса AWS.                                                                                   |
| **Egress-only IGW**            | IPv6 gateway, що дозволяє outbound internet traffic, але блокує ініційовані з інтернету inbound connections.                      |

## Типовий екзаменаційний сценарій

Потрібен приватний доступ до S3/DynamoDB → Gateway Endpoint; до багатьох
AWS APIs → Interface Endpoint.

## Екзаменаційна пастка

Security Group stateful; NACL stateless. Public subnet сама по собі не
робить EC2 публічним — потрібні public IP та route.

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

- [AWS Documentation — Amazon VPC](https://docs.aws.amazon.com/)
- [DVA-C02 Exam
  Guide](https://docs.aws.amazon.com/aws-certification/latest/developer-associate-02/developer-associate-02.html)
