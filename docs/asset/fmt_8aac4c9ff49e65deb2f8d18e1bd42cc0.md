
市场上有各种商业产品可以监控密钥泄露。这允许你扫描意外暴露在公共仓库中的密钥。

## 服务帐户身份充（Service accountation）

IAM 的核心功能之一是可以身份充服务帐户。身份充是指允许其他用户和资源像服务帐户一样操作的能力。

- 服务帐户用户（Service Account User）：此角色具有 `iam.serviceAccounts.actAs` 权限，允许主体访问服务帐户可以访问的所有资源。假设主体是一个用户并拥有“服务帐户用户”角色。该主体就可以身份充该服务帐户，以便在该帐户上设置 Cloud SQL。

- 此角色还允许将服务帐户链接到资源。然而，这不会允许主体为服务帐户创建短期令牌，或使用 Google Cloud CLI 身份充服务帐户。如果你需要这些功能，你需要“服务帐户令牌创建者”（Service Account Token Creator）角色。

- 服务帐户令牌创建者（Service Account Token Creator）：这允许主体身份充服务帐户以创建 OAuth 2.0 访问令牌，你可以使用它与 Google API 进行验证。它还允许主体签名 JSON Web Tokens (JWT) 和签名二进制块，以便用于验证。

要从 Google Cloud 外部或从 GKE 工作负载身份充服务帐户，请使用工作负载标识（Workload Identity）角色。

在为主体授予身份充能力时有几点考虑：

- 在项目、文件夹或组织级别授予该角色时要小心。这将允许主体对该项目、文件夹或组织内创建的任何服务帐户进行操作。这不是惯做法。

- 在特定的服务帐户上授予角色将允许主体在该帐户上代表另一个用户进行操作。这是惯做法。

## 跨项目服务帐户访问

在企业环境中管理服务帐户时，可以在单个项目中进行管理。这样，你就可以对服务帐户治理和生命周期过程提供更强的控制，并监控任何威胁向量的活动。当你有一个项目实现跨多个项目的自动化或监控任务，并需要访问它们时，这种设计模式会非常有用。这需要一个项目的服务帐户能够调用其他项目的资源。

![](img/f681dfc12450e3a4c257352b70dbceca_135_0.png)

如图 6.5 所示，为了支持这一点，Google Cloud 引入了允许服务账户访问资源项目的功能。默认行为是，您可以在一个项目中创建服务账户，并将其附加到另一个项目中的资源。如果您不希望具有这种行为，可以设置组织策略来防止它。

在存放服务账户的项目组织策略中，检查以下布尔值约束：

- 确保对项目没有强制执行 `iam.disableCrossProjectServiceAccountUsage` 布尔值约束。当不强制执行此约束时，Cloud IAM 会为项目添加一个置留（lien），以防止项目被删除。该置留的来源为 `iam.googleapis.com/cross-project-service-accounts`。强烈建议不要删除此置留。

建议对项目强制执行 `iam.restrictCrossProjectServiceAccountLienRemoval` 布尔值约束。该布尔值约束确保了主体如果在组织层级具有 `resourcemanager.projects.updateLiens` 权限，则可以删除项目置留。如果未强制执行此约束，主体如果在项目层级具有此权限，也可以删除项目置留。

在启用此功能之前，建议您创建一个适当的设计，并理解此过程可能为企业带来的所有依赖关系，并确保您已经考虑了此类决策的优缺点。如果您更新了组织策略，强烈建议不要更改它，特别是在生产环境中，因为您的 Google Cloud 资源可能无法正常工作。

在介绍服务账户活动之前，让我们快速回顾如何配置 WIF。

### 使用 Okta 配置工作负载身份联合 (Workload Identity Federation)

WIF 允许在不需要服务账户密钥的情况下访问 Google Cloud 服务，从而允许来自本地或其他云提供商的访问。在接下来的配置中，我们假设使用如 Okta 的第三方 OIDC 提供程序连接到 Google Cloud 服务。将利用 OAuth 2.0 RFC 6749 定义的客户端凭据流。该流要求应用程序通过传递 client ID 和 client Secret 来进行身份验证，之后获取令牌。机器到机器（M2M）应用程序（如 CLI、批处理作业或后端服务）以应用程序本身进行身份验证和授权，而不是通过用户。在这种情况下，典型的身份验证方案（如用户名+密码或社交登录）并不适用。相反，使用的是 OAuth 客户端凭据流。

> 注意：如果您的应用程序需要用户上下文，请考虑使用 OAuth 2.0 代表用户访问 Google APIs 而不是 WIF。您可以在 https://packt.link/Uycpj 找到详细信息。

### 服务账户

深入配置之前，让我们看看此场景下发生的数据流：

![](img/f681dfc12450e3a4c257352b70dbceca_137_0.png)

在图 6.6 所示的数据流中，您会注意到使用客户端凭据向 Okta 授权服务器发起调用以获取 OIDC 令牌。然后，在获取调用 Google Cloud 服务的访问令牌之前，令牌会被传递给两个 Google Cloud 端点。现在让我们配置 WIF 所需的步骤：

- 1. 从 Okta 生成客户端凭据。如果您不熟悉该流程，请参考 Okta 关于如何生成客户端凭据的文档。

- 2. 使用以下 `gcloud` 命令创建工作负载身份池：

```bash
gcloud iam workload-identity-pools create workload-id-pool location="global" description="Testing workload identity federation with Okta" display-name="workload-id-pool"
```

- 3. 为我们创建的池创建一个 OIDC 提供程序：

```bash
gcloud iam workload-identity-pools create-oidc okta-provider workload-identity-pool="workload-id-pool" issuer-uri="okta-issuer-url" location="global" attribute-mapping="google.subject=assertion.sub" - allowed-audiences="<在此输入客户端 ID>"
```

### Google Cloud 身份和访问管理

- 4. 为服务账户添加 IAM 策略绑定：

```
gcloud iam service-accounts add-iam-policy-binding okhtagcpsvacct@PROJECT_ID.iamserviceaccount.com role=iam.workloadidentityUser member=principal://iam.googleapis.com/projects/73105681369/locations/global/workloadidentityPools/workload-id-pool-1/subject/authz-server-ub>
```

- 5. 使用允许的受众值更新提供程序：

```
gcloud beta workload-identity-providers describe-oidc okta-provider allowed-audiences="api/24ww2ds-23" workload-identity-pool="workload-id-pool-1" location="global"
```

- 6. 使用以下 `gcloud` 命令验证 and 和 sub 值是否设置正确：

```
gcloud iam workload-identity-pools providers describe okta-provider --workload-identity-pool="workload-id-pool" location="global"
```

- 7. 现在，下载 JSON 配置文件，并在像以前使用服务账户密钥的地方使用它。

服务账户对您的 Google Cloud 组织构成了巨大的威胁向量，监控服务账户活动是至关重要的。在下一节中，我们将介绍如何操作。

### 服务账户活动监控实践

了解服务账户活动对于确保没有攻击者或滥用服务账户非常重要。Google Cloud 提供 Cloud Monitoring 来查看服务账户和服务账户密钥的使用指标。这些指标让您查看使用模式，从而帮助识别异常。API（例如 Google Maps 和 YouTube）包含在这些服务账户密钥的指标中。因此，非身份验证密钥对的使用统计是可用的。

要在 Metrics Explorer 中查看受监控资源的指标，请遵循以下步骤：

- 1. 在 Google Cloud 控制台中，进入 Monitoring 中的 Metrics 页面。

2. 进入 Metrics Explorer。

3. 在工具栏中，选择 Explorer 标签。

4. 选择 Configuration 标签。

5. 展开 Select metric 菜单，在过滤栏输入 IAM Service Account，然后使用子菜单选择资源类型和指标（关闭 Active resources 和 metrics）：

   - I. 在 Active resources 菜单中，选择 IAM Service Account。

   - II. 在 Active metric 菜单中，选择 Service_account。

- 6. 在 Active metrics 菜单中，选择服务账户指标。在选择的时间范围内可用以下指标：

   - I. 对于账户使用，选择 Service account authentication events。

   - II. 对于账户使用，选择 Service account key authentication。

- 7. 点击 Apply。

- 8. 可：配置如何查看数据，可以使用 Filter、Group By、Aggregator 和 chart type 菜单。

- 9. 可：更改图形设置：

   - I. 对于每天报告一次样本的配额和其他指标，将时间设置为至少一周，并将绘图类型设置为堆叠柱状图。

   - II. 对于分布值指标，将绘图类型选择热力图。

### Google Cloud 身份与访问管理 (IAM)

到目前为止，我们已经看到了用户管理的服务账户，但某些服务账户是由 Google 创建并管理的。在继续介绍 IAM 策略绑定之前，我们将简要查看这些账户。

#### 服务代理 (Service agents)

如果你使用了某个受托管的服务（例如安全命令中心 Security Command Center 或 DLP），Google 将在你的项目中为你创建一个服务账户。这些被称为服务代理。以下是服务代理工作方式的示例：

- **安全中心代理**: `service-53984177202@security-center-api-staging.iam.gserviceaccount.com`

- **风险管理器服务代理**: `organizations-720164443624@gcp-sa-riskmanager.iam.gserviceaccount.com`

服务代理通常具有以下内容：

- 服务代理邮箱地址中使用的域名

- 授予服务代理在项目上的角色

- 在你激活使用该服务代理的 API 后，Google 会自动授予该角色

涉及服务代理时有以下考虑事项：

- 服务代理角色的权限可能会随时更改。

- Google 随时可能引入新的服务代理，包括针对现有服务和新服务。此外，每个服务代理邮箱地址的格式可能会更改。

- 不要为这些服务账户分配任何身份冒充（principal impersonation）权限。

> 注意
> 所有服务账户都可以被冒充，但只有某些允许被冒充。

- 无法为服务代理创建密钥。

现在我们已经详细介绍了服务账户，接下来将转向深入学习 IAM 策略绑定。

#### IAM 策略绑定

在 Google Cloud 中，访问通过 IAM 策略绑定进行管理。IAM 策略附加到特定的资源上（请记住，资源可以是一个服务账户）。IAM 策略包含一组角色绑定，这些绑定与一个或多个主体（principals）关联。

回想一下，主体可以是以下一项或多个项：

- Google 账号（Gmail 账号是 Google 账户的一种形式）

- 服务账户

- Google 组

- Google Workspace 账号

- Cloud Identity 域

- 所有已身份验证的用户

- 所有用户

IAM 策略绑定（有时称为绑定）将角色与策略附加的资源上的主体以及该资源的所有后代资源上的主体关联（例如，附加到文件夹的策略适用于该文件夹下的所有资源）。

#### 策略结构

IAM 策略由角色定义和额外细节组成。角色绑定定义了特定用户或组可以访问的资源。一个角色与一个或多个主体关联，并带有任何适用条件。元数据（包括标签和版本）提供了有关策略的额外信息。

让我们了解创建 IAM 策略的某些原则：

- 每个 IAM 策略中最多可以包含 1,500 个主体。单个策略中最多可以指定 250 个唯一组。请注意，如果你使用了 IAM 条件或向许多具有长标识符的主体授予角色，IAM 可能会将策略限制为较少的主体。

- IAM 会跟踪每个主体在允许策略（allow policy）的角色绑定中出现的次数。这种方法不会对出现在多个角色中的主体进行去重。例如，主体 `alice@acme.com` 在允许策略中出现了 50 次角色绑定；你可以向允许策略的角色绑定中额外添加 1,450 个主体。无论域或 Google 组中有多少个个人成员，该域或该组都只被视为单个主体。

- 关于请求的任何额外信息（例如其来源或目标资源）都可以用作条件，以进一步限制角色绑定。条件访问通常用于判断用户的请求是否可以被授予。条件角色绑定（conditional role binding）指的是包含条件的角色绑定。某些 Google Cloud 服务不接受 IAM 策略中的条件。

#### Google 身份与访问管理

现在我们已经理解了这些原则，让我们来看策略的结构。IAM 策略包含以下字段：

- 一个 `etag` 字段，用于并发控制，确保策略的一致性更新。IAM 通过策略中的 `etag` 字段支持并发控制。每当更新 IAM 策略时，`etag` 字段的值也会同步更新。因此，具有 `etag` 字段但没有角色绑定的 IAM 策略是无效的。

- 有一个可选的 `version` 列，指示策略的架构版本。

- 此外，IAM 策略可以包含 `auditConfig` 字段，它定义了每个服务如何记录每个服务类型的活动，包括组织、文件夹、项目结算账户。

在修改 IAM 策略后的 60 秒内，新策略将生效。在某些情况下，更改可能需要长达七分钟才能传播到 Google Cloud。

这是一个简单的策略示例：

```json
{
  "bindings": [
    {
      "members": [
        "user:bob@acme.com"
      ],
      "role": "roles/owner"
    }
  ],
  "etag": "BwUjMhSzpY =",
  "version": 1
}
```

在此简单的策略示例中，所有者（Owner）基础角色被授予 bob@acme.com 且没有任何限制。通过此位置授予 bob@acme.com 的访问权限几乎是无限的。

以下是一个绑定了多个角色的策略示例。每个角色绑定都为其接收者授予相应的权限：

```json
{
  "bindings": [
    {
      "members": [
        "user:bob@acme.com"
      ],
      "role": "roles/owner"
    }
  ]
}
```

另一方面，group:prod@acme.com Google 组组仅在满足角色绑定条件时才会被包含。因此，它仅将生效到 2024 年 7 月 1 日。

现在让我们来看看 Google Cloud 中的策略继承是如何工作的。

#### 策略继承与资源层级结构

策略继承描述了策略如何应用于资源层级结构中较低位置的资源。有效策略是指资源的策略通过其所有父级一直传递到资源层级的顶端。在该序列中，它是以下内容的组合：

- 在资源上设置的策略

- 在层级结构中资源的所有祖先资源层级设置的策略

每个角色绑定（从父资源获取）对资源有效策略的影响都将单独评估。如果任何高级别的角色绑定提供了访问权限，将授予特定的访问请求。当在资源的任何层级添加新的角色绑定时，继承策略的访问范围就会扩大。

为了理解策略继承，让我们考虑这样一个场景：你在资源层级结构的不同级别为用户 Bob 授予了两个不同的 IAM 角色。

要在组织层级为 Bob 授予角色，你为你的组织设置了以下策略：

```json
{
  "bindings": [
    {
      "members": [
        "user:bob@acme.com"
      ],
      "role": "roles/storage.objectViewer"
    }
  ],
  "etag": "BwujMjhCsNaY=",
  "version": 1
}
```

此策略授予 Bob 存储对象查看者角色 (`roles/storage.objectViewer`)。由于你在组织层级设置了策略，Bob 可以对组织内所有项目和所有 Cloud Storage 对象使用这些权限。

要在项目层级为 Bob 授予角色，你在项目上设置了以下策略：

```json
{
  "bindings": [
    {
      "members": [
        "user:bob@acme.com"
    ],
      "role": "roles/storage.objectCreator"
    }
  ],
  "etag": "BwUjhCsNaY =",
  "version": 1
}
```
