# Security, Identity, and Compliance — довідник DVA-C02

Тематичний довідник із визначеннями термінів, практичними сценаріями та
типовими екзаменаційними пастками.

## Amazon Cognito

**Призначення:** Керування автентифікацією користувачів і федерацією
identity providers для застосунків.

### Ключові терміни

| Термін                      | Визначення українською                                                                                              |
|-----------------------------|---------------------------------------------------------------------------------------------------------------------|
| **User Pool**               | Amazon Cognito каталог користувачів для реєстрації, входу, керування профілями та видачі JWT.                       |
| **Identity Pool**           | Cognito компонент, який обмінює автентифіковану або гостьову identity на тимчасові AWS credentials через IAM roles. |
| **App Client**              | Ідентифікатор застосунку в User Pool із налаштуваннями OAuth flows, callback URLs, token validity та client secret. |
| **Hosted UI**               | Готовий Cognito web interface для signup/signin та OAuth authorization flow.                                        |
| **User Attributes**         | Стандартні й custom поля профілю користувача, наприклад email, phone_number або custom attributes.                  |
| **Groups**                  | Логічні групи користувачів User Pool, які можуть брати участь у role mapping та authorization.                      |
| **Federation**              | Автентифікація користувачів через зовнішніх identity providers, наприклад Google, SAML або OIDC.                    |
| **OIDC/SAML**               | Стандарти федеративної identity: OIDC використовує OAuth 2.0/JWT, SAML — XML assertions.                            |
| **JWT**                     | JSON Web Token — підписаний токен із claims, який передає твердження про користувача або авторизаційний контекст.   |
| **ID/Access/Refresh Token** | ID token описує identity, access token містить authorization scopes, refresh token дозволяє отримувати нові токени. |
| **MFA**                     | Multi-Factor Authentication — додатковий фактор входу, наприклад TOTP або SMS залежно від налаштувань.              |
| **Lambda Triggers**         | Cognito lifecycle hooks, які викликають Lambda під час signup, authentication і генерації токенів.                  |
| **Role Mapping**            | Правила Identity Pool, що зіставляють claims/groups із IAM roles.                                                   |

**Типовий екзаменаційний сценарій:** Потрібні sign-up/sign-in та JWT →
User Pool; потрібні тимчасові AWS credentials користувачеві → Identity
Pool.

**Екзаменаційна пастка:** User Pool автентифікує; Identity Pool видає
AWS credentials. Це різні функції.

------------------------------------------------------------------------

## AWS IAM

**Призначення:** Керування principals, permissions, roles та policies
для AWS APIs і ресурсів.

### Ключові терміни

| Термін                     | Визначення українською                                                                                                                |
|----------------------------|---------------------------------------------------------------------------------------------------------------------------------------|
| **Principal**              | Суб’єкт, від імені якого виконується AWS request: IAM user, role session, federated user або AWS service.                             |
| **User**                   | IAM identity для людини або застосунку; для AWS workloads зазвичай рекомендовано roles замість довготривалих user keys.               |
| **Group**                  | Колекція IAM users зі спільними identity-based policies.                                                                              |
| **Role**                   | IAM identity з permissions і trust policy, яку principal може assume для тимчасових credentials.                                      |
| **Policy**                 | JSON документ зі statements, що визначають Allow/Deny для actions, resources та conditions.                                           |
| **Identity-based**         | Policy, прикріплена до user/group/role і яка визначає permissions identity.                                                           |
| **Resource-based**         | Policy на самому resource, яка визначає, які principals можуть звертатися до нього.                                                   |
| **Trust Policy**           | Політика IAM role, що визначає, які principals можуть викликати sts:AssumeRole або іншу дозволену операцію отримання ролі.            |
| **Action**                 | Назва AWS API permission у policy, наприклад s3:GetObject.                                                                            |
| **Resource ARN**           | Amazon Resource Name, що ідентифікує resource у policy Resource element.                                                              |
| **Effect**                 | Значення Allow або Deny для policy statement.                                                                                         |
| **Condition**              | Додаткові умови застосування statement, наприклад source IP, MFA або resource tags.                                                   |
| **Explicit/Implicit Deny** | Explicit deny — пряма заборона; implicit deny — відсутність Allow. Explicit deny має пріоритет.                                       |
| **Least Privilege**        | Принцип надання лише мінімально необхідних permissions.                                                                               |
| **Managed/Inline Policy**  | Managed policy — окремий повторно використовуваний об’єкт; inline policy вбудована в одну identity.                                   |
| **Permission Boundary**    | Політика, яка задає максимальну множину permissions для IAM user або role; сама по собі не надає дозволів.                            |
| **Session Policy**         | Додаткова policy, що обмежує permissions тимчасової role session, але не розширює їх.                                                 |
| **ABAC**                   | Attribute-Based Access Control — модель доступу, у якій permissions визначаються атрибутами principals і resources, часто через tags. |
| **MFA**                    | Multi-Factor Authentication — додатковий фактор підтвердження identity.                                                               |
| **Access Key**             | Пара access key ID і secret access key для підписання AWS API requests; секретний ключ не можна розкривати.                           |
| **Instance Profile**       | Контейнер для IAM role, який прикріплюється до EC2 instance і надає тимчасові credentials застосункам на інстансі.                    |

**Типовий екзаменаційний сценарій:** Lambda/EC2 має викликати AWS API →
надати execution/instance role із мінімальними permissions.

**Екзаменаційна пастка:** Explicit Deny перекриває Allow. Не вбудовуйте
довготривалі access keys у код.

------------------------------------------------------------------------

## AWS KMS

**Призначення:** Керування криптографічними ключами для шифрування,
дешифрування та підпису.

### Ключові терміни

| Термін                    | Визначення українською                                                                                                                          |
|---------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------|
| **KMS Key**               | Логічний ресурс KMS для криптографічних операцій та керування key material.                                                                     |
| **Key Material**          | Криптографічні дані, що лежать в основі KMS key.                                                                                                |
| **AWS Owned/Managed Key** | AWS owned keys контролюються AWS поза account; AWS managed keys створюються й адмініструються AWS у customer account.                           |
| **Customer Managed Key**  | KMS key, яким керує користувач і для якого можна налаштовувати policy, grants, rotation та lifecycle.                                           |
| **Key Policy**            | Основна resource policy KMS key, яка визначає principals та дозволені операції з ключем.                                                        |
| **Grant**                 | Делегований набір permissions для principal/service на операції з KMS key.                                                                      |
| **Envelope Encryption**   | Схема шифрування, де дані шифруються data key, а data key окремо шифрується KMS key.                                                            |
| **Data Key**              | Ключ шифрування даних, який KMS може згенерувати та повернути в plaintext і зашифрованому вигляді.                                              |
| **GenerateDataKey**       | KMS API, що генерує data key і повертає plaintext та encrypted копії.                                                                           |
| **Encrypt/Decrypt**       | KMS API для шифрування/розшифрування даних безпосередньо KMS key у межах розмірних обмежень.                                                    |
| **Rotation**              | Процес регулярної заміни секретного значення або оновлення key material для зниження ризику компрометації.                                      |
| **Alias**                 | Людиночитне ім’я-покажчик на KMS key, яке можна перепризначити.                                                                                 |
| **ARN**                   | Amazon Resource Name — ідентифікатор KMS resource.                                                                                              |
| **Multi-Region Key**      | Пов’язані KMS keys у різних Regions із сумісним key material для multi-Region cryptographic use cases.                                          |
| **Encryption Context**    | Набір не секретних key-value metadata, криптографічно пов’язаних із KMS encryption operation; для decrypt має бути переданий той самий context. |

**Типовий екзаменаційний сценарій:** Потрібне кероване шифрування даних
із контролем ключів → KMS.

**Екзаменаційна пастка:** Перевіряйте Key Policy разом з IAM policy; KMS
key policy є ключовою частиною authorization.

------------------------------------------------------------------------

## AWS STS

**Призначення:** Видача тимчасових security credentials для ролей,
федерації та cross-account access.

### Ключові терміни

| Термін                        | Визначення українською                                                                                                          |
|-------------------------------|---------------------------------------------------------------------------------------------------------------------------------|
| **Temporary Credentials**     | Короткоживучі credentials: access key ID, secret access key і session token.                                                    |
| **AssumeRole**                | Операція AWS STS, яка дозволяє principal отримати тимчасові credentials для IAM role за умови довіри та дозволів.               |
| **AssumeRoleWithWebIdentity** | STS API, який обмінює OIDC web identity token на тимчасові credentials IAM role.                                                |
| **AssumeRoleWithSAML**        | STS API, який обмінює SAML assertion на тимчасові credentials IAM role.                                                         |
| **GetSessionToken**           | STS API для отримання тимчасових credentials, зокрема для MFA-protected API sessions.                                           |
| **GetCallerIdentity**         | STS API, який повертає account, ARN і user ID поточного caller.                                                                 |
| **Role Session**              | Тимчасовий контекст після AssumeRole із власними credentials та строком дії.                                                    |
| **External ID**               | Додаткове значення в AssumeRole для cross-account access, яке допомагає захистити сторонній сервіс від confused deputy problem. |
| **Session Duration**          | Час дії тимчасових credentials role session у межах встановлених обмежень.                                                      |
| **Session Name**              | Ім’я role session, яке відображається в CloudTrail і допомагає ідентифікувати caller.                                           |
| **Session Policy**            | Додаткова policy для тимчасової session, яка звужує effective permissions.                                                      |
| **Web Identity Federation**   | Обмін зовнішнього OIDC token на AWS temporary credentials через STS.                                                            |

**Типовий екзаменаційний сценарій:** Потрібен тимчасовий доступ до
іншого AWS account → STS AssumeRole.

**Екзаменаційна пастка:** Тимчасові credentials мають expiration і
session token; External ID часто застосовується для third-party
cross-account access.

------------------------------------------------------------------------

## AWS Secrets Manager

**Призначення:** Безпечне зберігання, отримання та ротація application
secrets.

### Ключові терміни

| Термін                   | Визначення українською                                                                                     |
|--------------------------|------------------------------------------------------------------------------------------------------------|
| **Secret**               | Об’єкт Secrets Manager із конфіденційним значенням, metadata та версіями.                                  |
| **Secret Value**         | Фактичне секретне значення: пароль БД, API key або credentials JSON.                                       |
| **Secret ARN**           | Amazon Resource Name, який однозначно ідентифікує secret.                                                  |
| **KMS Encryption**       | Шифрування secret value за допомогою AWS KMS key.                                                          |
| **Rotation**             | Процес регулярної заміни секретного значення або оновлення key material для зниження ризику компрометації. |
| **Rotation Lambda**      | Lambda function, яку Secrets Manager викликає для автоматичної зміни secret у цільовій системі.            |
| **Staging Labels**       | Мітки Secrets Manager, що вказують на версії secret, наприклад AWSCURRENT, AWSPREVIOUS та AWSPENDING.      |
| **AWSCURRENT**           | Staging label для актуальної версії secret, яку має використовувати застосунок.                            |
| **AWSPREVIOUS**          | Staging label, що зазвичай позначає попередню версію secret.                                               |
| **AWSPENDING**           | Staging label для нової версії secret під час процесу rotation.                                            |
| **Version**              | Незмінна версія secret value; staging labels вказують на відповідні версії.                                |
| **GetSecretValue**       | API, що повертає secret value та metadata для авторизованого principal.                                    |
| **Resource Policy**      | Policy на secret, яка визначає principals/accounts із доступом до нього.                                   |
| **Cross-account Access** | Доступ principal з іншого AWS account через resource policy, IAM permissions і за потреби AssumeRole.      |
| **Caching**              | Локальне кешування secret для зменшення latency та API costs; cache має враховувати ротацію.               |

**Типовий екзаменаційний сценарій:** Потрібно зберігати DB credentials і
автоматично їх ротувати → Secrets Manager.

**Екзаменаційна пастка:** Не логувати секрети. Застосунок має коректно
перечитувати значення після ротації.

------------------------------------------------------------------------

## AWS WAF

**Призначення:** Фільтрація HTTP(S) запитів за правилами для захисту web
apps та APIs.

### Ключові терміни

| Термін                   | Визначення українською                                                                                                    |
|--------------------------|---------------------------------------------------------------------------------------------------------------------------|
| **Web ACL**              | Набір правил AWS WAF, який асоціюється з web resource і визначає, які HTTP(S) запити дозволяти, блокувати або перевіряти. |
| **Rule**                 | Умова AWS WAF, що зіставляє HTTP request із критеріями та застосовує action.                                              |
| **Rule Group**           | Повторно використовуваний набір WAF rules, який можна додати до Web ACL.                                                  |
| **Managed Rule Group**   | Готовий набір правил AWS або стороннього provider для типових web threats.                                                |
| **IP Set**               | Список IPv4/IPv6 CIDR ranges, який можна використовувати в WAF rules.                                                     |
| **Regex Pattern Set**    | Набір regular expressions для пошуку шаблонів у частинах HTTP request.                                                    |
| **Rate-based Rule**      | Правило AWS WAF, яке обмежує запити за кількістю протягом заданого вікна для визначених aggregation keys.                 |
| **SQLi Match**           | Умова WAF для виявлення ознак SQL injection у вибраних частинах запиту.                                                   |
| **XSS Match**            | Умова WAF для виявлення ознак cross-site scripting у запиті.                                                              |
| **Scope-down Statement** | Додаткова умова, яка звужує запити, до яких застосовується rule group або rate-based rule.                                |
| **Allow/Block/Count**    | WAF actions: Allow пропускає, Block відхиляє, Count лише рахує збіги.                                                     |
| **CAPTCHA/Challenge**    | Actions, які вимагають CAPTCHA або browser challenge перед подальшим доступом.                                            |
| **Logging**              | Запис WAF request logs у destination для аналізу та troubleshooting.                                                      |
| **Association**          | Прив’язка Web ACL до підтримуваного ресурсу, наприклад CloudFront або ALB.                                                |

**Типовий екзаменаційний сценарій:** Потрібно блокувати SQL injection,
XSS або rate abuse на web endpoint → WAF.

**Екзаменаційна пастка:** WAF фільтрує web requests; Security Group/NACL
контролюють мережевий трафік.

------------------------------------------------------------------------
