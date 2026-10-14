

*   经过身份提供商 (IdP) 认证的外部用户

### Amazon SageMaker Role Manager

Amazon SageMaker Role Manager 为多种 ML 人员角色提供建议权限，包括数据科学家角色、MLOps 角色和 SageMaker AI 计算角色。

每个角色都以选定的 ML 活动及其关联权限的形式拥有建议权限，如 [表 8.1](#c008.xhtml#c08-tbl-1) 所示。

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

*   **数据科学家角色** — 使用此角色可配置权限，以便在 SageMaker AI 环境中执行常规 ML 开发和实验。此角色包含以下预选 ML 活动：
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

*   **MLOps 角色** — 选择此角色可配置运营活动的权限。此角色包含以下预选 ML 活动：
    *   运行 Studio Classic 应用程序
    *   管理模型
    *   管理管道
    *   搜索和可视化实验
    *   Amazon S3 完全访问

*   **SageMaker AI 计算角色** — 此角色包含以下预选 ML 活动：
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

