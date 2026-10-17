
### Amazon 资源名称 (ARN)

这是您的 IAM 用户的 ARN，用于在整个 AWS 中唯一标识您的 IAM 用户。例如，您可以使用 ARN 在允许用户写入 Amazon S3 存储桶的 IAM 策略中将 IAM 用户指定为 `Principal`。IAM 用户的 ARN 可能如下所示：

```
arn:aws:iam::123456789012:user/Dario
```

### 唯一标识符

仅当您使用 API、Tools for Windows PowerShell 或 AWS CLI 创建 IAM 用户时才会返回此 ID；您在控制台中看不到此 ID。

### IAM 角色

IAM 角色是您可以在 AWS 账户中创建的另一种 IAM 身份类型。就像 IAM 用户一样，IAM 角色附带特定的权限策略，定义其被允许执行的操作和被允许访问的 AWS 资源。然而，与 IAM 用户不同，角色旨在由需要它的任何人 `assumed`，而不是绑定到单一身份。

此外，角色没有长期凭证，例如密码或访问密钥。相反，当您代入角色时，它会为您的角色会话期间提供临时安全凭证。这实际上是一件好事，因为短期凭证通过限制代入 IAM 角色授予的权限的时间范围，减少了 ML 工作负载的攻击面。

IAM 角色的 ARN 可能如下所示：

```
arn:aws:sts::123456789012:assumed-role/Accounting-Role/Mario
```

IAM 角色可由以下实体代入：

*   同一 AWS 账户或另一 AWS 账户中的 IAM 用户
*   同一 AWS 账户中的 IAM 角色
*   服务主体（代表 AWS 服务的 IAM 主体）
*   经过身份提供商 (IdP) 认证的外部用户

### Amazon SageMaker Role Manager

Amazon SageMaker Role Manager 为多种 ML 人员角色提供建议权限，包括数据科学家角色、MLOps 角色和 SageMaker AI 计算角色。

每个角色都以选定的 ML 活动及其关联权限的形式拥有建议权限，如表 8.1 所示。

**表 8.1：ML 预定义权限**

| ML 活动 | 说明 |
| --- | --- |
| 访问所需的 AWS 服务 | 访问 Amazon S3、Amazon ECR、Amazon CloudWatch 和 Amazon EC2 的权限。作业和终端节点的执行角色所必需。 |
| 运行 Studio Classic 应用程序 | 在 Studio Classic 环境中操作的权限。域和用户配置文件执行角色所必需。 |
| 管理 ML 作业 | 审核、查询血缘和可视化实验的权限。 |
| 管理模型 | 管理 SageMaker AI 作业全生命周期的权限。 |
| 管理管道 | 管理 SageMaker 管道和管道执行的权限。 |
| 搜索和可视化实验 | 审核、查询血缘和可视化 SageMaker AI 实验的权限。 |
| 管理模型监控 | 管理 SageMaker AI Model Monitor 的监控计划的权限。 |
| Amazon S3 完全访问 | 执行所有 Amazon S3 操作的权限。 |
| Amazon S3 存储桶访问 | 对指定 Amazon S3 存储桶执行操作的权限。 |
| 查询 Athena 工作组 | 运行和管理 Amazon Athena 查询的权限。 |
| 管理 AWS Glue 表 | 为 SageMaker AI Feature Store 和 Data Wrangler 创建和管理 AWS Glue 表的权限。 |
| SageMaker Canvas 核心访问 | 在 SageMaker Canvas 中执行实验的权限（即基本数据准备、模型构建、验证）。 |
| SageMaker Canvas 数据准备（由 Data Wrangler 提供支持） | 在 SageMaker Canvas 中执行端到端数据准备的权限（即聚合、转换和分析数据；在大型数据集上创建和调度数据准备作业）。 |
| SageMaker Canvas AI 服务 | 访问来自 Amazon Bedrock、Amazon Textract、Amazon Rekognition 和 Amazon Comprehend 的即用型模型的权限。此外，用户可微调来自 Amazon Bedrock 和 Amazon SageMaker JumpStart 的基础模型。 |
| SageMaker Canvas MLOps | SageMaker Canvas 用户直接将模型部署到终端节点的权限。 |
| SageMaker Canvas Kendra 访问 | SageMaker Canvas 访问 Amazon Kendra 以进行企业文档搜索的权限。该权限仅授予您在 Amazon Kendra 中选定的索引名称。 |
| 使用 MLflow | 管理 MLflow 中的实验、运行和模型的权限。 |
| 管理 MLflow Tracking Servers | 管理、启动和停止 MLflow Tracking Servers 的权限。 |
| MLflow 所需的 AWS 服务访问权限 | MLflow Tracking Servers 访问 S3、Secrets Manager 和 Model Registry 的权限。 |
| 运行 Studio EMR Serverless 应用程序 | 在 Amazon SageMaker Studio 上创建和管理 EMR Serverless 应用程序的权限。 |

#### 数据科学家角色

使用此角色可配置权限，以便在 SageMaker AI 环境中执行常规 ML 开发和实验。此角色包含以下预选 ML 活动：

*   运行 Studio Classic 应用程序
*   管理 ML 作业
*   管理模型
*   管理 AWS Glue 表
*   SageMaker Canvas AI 服务
*   SageMaker Canvas MLOps
*   SageMaker Canvas Kendra 访问
*   使用 MLflow
*   MLflow 所需的 AWS 服务访问权限
*   运行 Studio EMR Serverless 应用程序

#### MLOps 角色

选择此角色可配置运营活动的权限。此角色包含以下预选 ML 活动：

*   运行 Studio Classic 应用程序
*   管理模型
*   管理管道
*   搜索和可视化实验
*   Amazon S3 完全访问

#### SageMaker AI 计算角色

此角色包含以下预选 ML 活动：

*   访问所需的 AWS 服务

### IAM 用户组

您可以使用 IAM 用户组来管理多个 IAM 用户的权限。借助 IAM 用户组，您可以将特定权限分配给组内的所有成员。例如，您可以创建一个 `ML-Trainers` 组，并赋予其专门针对 ML 任务定制的权限，例如在 Amazon SageMaker AI 中创建训练作业。添加到此组的任何用户将自动继承这些权限。如果新的 ML 工程师加入您的组织并需要创建训练作业的能力，您只需将他们添加到 `ML-Trainers` 组即可。同样，如果员工的工作发生变动，您可以通过在组之间移动他们来更新其权限，而无需单独编辑他们的权限。

就像 IAM 用户和 IAM 角色一样，您也可以将策略附加到 IAM 用户组，确保所有成员都获得策略中定义的权限。例如，`ML-Trainers` 组可以拥有一个授予 `sagemaker:CreateTrainingJob` 权限的策略。但是，重要的是要注意，IAM 用户组不能在策略中被标识为委托人，因为 IAM 用户组与权限相关，而非认证。委托人是经过认证的 IAM 实体，由单个 IAM 用户或 IAM 角色表示。

现在您已经理解了身份的概念，您可能想知道 AWS 如何知道给定的 IAM 用户/角色/组被允许对特定 AWS 资源（例如 Amazon S3 存储桶）执行某项操作（例如写入）。这就是*访问策略*概念发挥作用的地方，将在下一节中介绍。

### 访问策略

访问策略（或简称为策略）构成了 AWS 授权的关键组件。AWS 中的策略是一个对象，用于指定与其关联的身份或资源的权限。当委托人（如 IAM 用户或 IAM 角色）在成功认证后发出请求时，AWS 会评估与其身份关联的策略，以确定应允许还是拒绝该请求。此评估的结果称为策略的*效力*，其值为 `allow` 或 `deny`。策略中概述的权限称为*操作*，管辖委托人被允许对策略中指定的 AWS 资源执行的操作。策略也可能包含*条件*，指定策略生效的条件。

大多数此类策略在 AWS 中以 JSON 文档形式存储。

考试所需了解的策略将在后续章节中概述。有关访问策略的更多信息，请访问 `https://docs.aws.amazon.com/IAM/latest/UserGuide/access_policies.html#access_policy-types`。

### 基于身份的策略

基于身份的策略是控制身份（IAM 用户、IAM 用户组和 IAM 角色）可以执行哪些操作、针对哪些 AWS 资源以及在什么条件下执行的 JSON 文档。以下示例显示了一个 JSON 策略，允许 IAM 用户在 `us-east-1` 区域的 `123456789012` 账户中对 Vehicles 表 (`table/Vehicles`) 执行所有 Amazon DynamoDB 操作 (`dynamodb:*`)：

```json
{
  "Version": "2012-10-17",
  "Statement": {
    "Effect": "Allow",
    "Action": "dynamodb:*",
    "Resource": "arn:aws:dynamodb:us-east-1:123456789012:table/Vehicles"
  }
}
```

将此策略附加到您的 IAM 用户后，该用户将拥有在 DynamoDB 实例中对 Vehicles 表执行所有操作的权限。通常，IAM 用户拥有多个策略，这些策略共同定义了其总体权限。

未经策略明确允许的操作或资源，默认均被拒绝。例如，如果前述策略是附加到某 IAM 用户的唯一策略，则该用户可对 Vehicles 表执行 DynamoDB 操作，但无法与其他表交互。同样，该用户也受限于无法在 Amazon EC2、Amazon S3 或任何其他 AWS 服务中执行操作，因为该策略未授予这些服务的权限。

### 基于资源的策略

基于资源的策略是附加到 AWS 资源（而非 AWS 身份）的 JSON 文档。这些策略授予指定委托人对该资源执行特定操作的权限，并定义了这些权限适用的条件。

以下 JSON 文档是一个 S3 存储桶的 AWS 基于资源的策略示例，它授予委托人 `arn:aws:iam::123456789012:user/Dario` 向存储桶 `your-unique-bucket-name` 写入数据的权限：

```json
{
  "Version": "2012-10-17",
  "Statement": [
    {
      "Effect": "Allow",
      "Principal": {
        "AWS": "arn:aws:iam::123456789012:user/Dario"
      },
      "Action": "s3:PutObject",
      "Resource": "arn:aws:s3:::your-unique-bucket-name/*"
    }
  ]
}
```

在该策略中：

*   `Effect` 设置为 `Allow`，表示允许该操作。
*   `Principal` 指定了 ARN 为 `arn:aws:iam::123456789012:user/Dario` 的 IAM 用户 Dario。
*   `Action` 为 `s3:PutObject`，允许用户向存储桶写入对象。
*   `Resource` 指定了存储桶的 ARN，并包含通配符 (`*`) 以允许写入存储桶内的任何对象。

请将 `your-unique-bucket-name` 替换为您的 S3 存储桶的实际名称。

### 权限边界

权限边界是一项高级 IAM 功能，用于定义基于身份的策略可授予 IAM 身份的**最大权限**。当为 IAM 身份设置权限边界时，该实体只能执行同时被其基于身份的策略和权限边界允许的操作。

以下 JSON 文档是一个权限边界策略示例，它将 IAM 用户 Dario 的权限限制为仅使用 DynamoDB、S3 和 CloudWatch 服务：

```json
{
  "Version": "2012-10-17",
  "Statement": [
    {
      "Effect": "Allow",
      "Action": [
        "dynamodb:*",
        "s3:*",
        "cloudwatch:*"
      ],
      "Resource": "*"
    }
  ]
}
```

当您将此权限边界策略附加到 IAM 用户 Dario 时，它会限制该用户的权限，但本身不提供任何权限。在本例中，该策略将 Dario 的最大权限设定为 Amazon DynamoDB、Amazon S3 和 Amazon CloudWatch 中的所有操作。即使 Dario 拥有允许访问其他服务（包括 IAM）的权限策略，他也永远无法在任何其他服务中执行操作。

### 服务控制策略

如果您的 AWS 账户属于一个包含多个账户的大型组织，这些账户旨在履行不同的业务职能，您可以实施服务控制策略 (SCP)，作为在整个组织中统一管理权限的一种一致方式。

SCP 是强大的工具，允许您为组织或组织单元 (OU) 内账户中的 IAM 用户和角色定义**最大权限**。这些 JSON 策略充当护栏，设定可执行和不可执行操作的边界，提供额外的控制、安全性和合规性层。例如，为强制执行一项组织策略，即仅允许在指定 OU 内的账户中于特定区域创建 EC2 实例，您可以创建一个 SCP，显式拒绝除指定区域外的任何区域的 `ec2:RunInstances` 操作，并将此 SCP 应用于 AWS 组织内的相关 OU。通过使用 SCP，您可以确保仅允许经过批准的操作，从而降低意外或恶意活动的风险。

此外，SCP 可应用于成员账户内的所有委托人，包括 AWS 账户根用户。这意味着，即使用户通过其他策略获得了权限，SCP 中的显式拒绝也将覆盖任何允许，从而有效限制其操作。SCP 对于在大型复杂组织中强制执行合规性和治理特别有用。通过集中管理权限，您可以简化安全运营，并在所有账户中保持一致的策略，确保 AWS 环境保持安全且受到良好监管。

要了解有关 SCP 的更多信息，请访问 `https://docs.aws.amazon.com/organizations/latest/userguide/orgs_manage_policies_scps.html`。

## 保护基础设施和数据

在 AWS 中保护基础设施对于保护敏感数据和确保 ML 工作流的完整性至关重要。AWS 安全的基本组件之一是虚拟私有云 (VPC)，它通过创建 AWS 云中一个逻辑隔离的区域来提供网络隔离，您可以在其中定义虚拟网络并启动 AWS 资源。VPC 使您能够控制网络设置，如 IP 地址范围、子网、路由表和网关，为您的 ML 基础设施提供安全环境。

### 使用 VPC 进行网络隔离

VPC 是 AWS 网络隔离的基石。创建 VPC 后，您可以在一个逻辑隔离的网络中启动 AWS 资源，如 Amazon SageMaker 笔记本、训练作业和推理端点。这种隔离允许您定义 IP 地址范围、创建子网和配置路由表，确保您的 ML 资源安全地与 AWS 网络的其他部分和外部网络分隔开。

在 VPC 中，NACL 作为**无状态**防火墙，在子网层面控制入站和出站流量。无状态意味着之前发送或接收的流量信息不会被保存。NACL 允许您定义规则，根据 IP 地址、协议和端口显式允许或拒绝流量。这一额外的安全层符合纵深防御原则，有助于保护您的 ML 基础设施免受未经授权的访问和潜在威胁。

*安全组*作为 ML 实例的**有状态**防火墙，在实例层面控制入站和出站流量。有状态意味着之前发送或接收的流量信息会被保存。因此，如果安全组允许入站流量通过端口 443 到达 EC2 实例，无论出站安全组规则如何，响应流量都会自动被允许返回。安全组可附加到各种 AWS 资源，如 Amazon EC2 实例、Amazon RDS 实例、Amazon 弹性负载均衡器 (ELB) 和 Amazon SageMaker 笔记本。通过定义安全组规则，您可以指定允许哪些流量到达您的 ML 资源。这些规则也可以基于 IP 地址、协议和端口，确保只有授权流量可以访问您的 ML 基础设施。安全组的一项关键功能是能够在规则中引用其他安全组或定义的前缀列表作为源。这使您无需知道资源的具体 IP 地址即可管理对资源组的访问，例如拥有动态分配 IP 的 ELB。

### 私有连接

#### 私有连接选项
