

![](img/1490b3cf638678afadc8c48abc1698d5_333_0.png)

## 图 14.4：代码部署流水线

| CLOUD PROVIDER | MODEL INVENTORY MANAGEMENT TOOLS | FEATURES AND USES |
|---|---|---|
| AWS | SageMaker 模型注册表 | 只要开发出新模型，您就可以在那里注册它，每次训练时，都可以创建最新版本。它支持：<br>- 模型审计<br>- 模型血缘跟踪、关联元数据管理<br>- 创建新模型版本 |

![](img/1490b3cf638678afadc8c48abc1698d5_335_0.png)

## 图 14.5：集中式模型库存管理

实现模型库存管理主要有两种方式：

- **分布式模型管理：** 手动开发或由各种自动化流水线生成的模型可以存储在相应的账户中。例如，不同的组织单位可以将其模型注册到其自己的 ML UAT/测试账户。

- **集中式模型管理：** 如图 14.5 所示，自动化流水线开发的模型可以存储在共享服务账户中。您可以创建模型包组来存储与模型关联的不同版本。在部署时，使用特定版本从包组中进行部署。

**注意** 实施模型库存管理以跟踪模型血缘、管理模型元数据并审计模型使用。

## 日志记录和审计

跟踪各平台组件执行的操作以进行审计是必不可少的。通过跟踪 ML 操作，您可以协助进行模型调试、性能监控、审计以及 ML 平台的运行状况监控。图 14.6 显示了日志记录和审计参考架构。

下表列出了 AWS、Azure 和 Google 提供的日志记录和审计工具功能：

| CLOUD PROVIDER | LOGGING AND AUDITING TOOLS | FEATURES AND USES |
|---|---|---|
| AWS | AWS CloudTrail | 跟踪 AWS 服务的操作。<br>将日志存储在 S3 中。<br>日志包含事件名称、用户身份、事件时间、事件源和源 IP 地址。<br>用户可以直接从 AWS 控制台访问日志。<br>与 Splunk 集成以进行下游分析。<br>跟踪 SageMaker 实例中的活动。<br>审计归属的最佳做法是为每个用户创建角色。 |
| Azure | Azure Activity Logs<br>Azure Monitor<br>Azure Storage<br>Azure Sentinel | 跟踪对 Azure 资源执行的操作。<br>日志可以发送到 Azure 存储或 Azure Monitor 以进行进一步分析。<br>Azure 存储提供诸如 Azure Blob Storage 等选项。<br>Azure Sentinel 提供高级安全监控、事件响应和报告。 |
| Google | Google Cloud Audit Logs<br>Google Cloud Storage<br>Google Cloud Logging<br>Google's Security Command Center | 捕获发送到其他下游系统以进行分析的日志。<br>将日志存储在 Google Cloud 存储桶中。<br>日志可以使用 Google 的集中式监控系统 Google Cloud Logging 进行分析。<br>安全命令中心提供安全和合规性监控、漏洞扫描和威胁检测功能。 |

> **提示** 实施强大的审计系统以跟踪所有活动并监控可疑活动。为每个用户创建角色，以便在审计期间对这些活动进行适当的归属。

## 数据和工件血缘跟踪

跟踪数据和工件血缘至关重要，因为它将帮助您复制整个数据处理、模型构建和部署过程，以满足法规和合规要求。本节回顾了需要跟踪的不同工件，如图 14.7 所示。

![](img/1490b3cf638678afadc8c48abc1698d5_338_0.png)

## 图 14.6：日志记录和审计架构

下表列出了 AWS 提供的用于跟踪代码、数据集、元数据、容器、训练作业、模型和终端节点版本的工具：

| Category | Tools | Description |
|---|---|---|
| 代码版本控制 | GitLab, Bitbucket, CodeCommit | 代码仓库可帮助您跟踪代码工件的版本。您可以使用提交 ID 进行检入和检出，以便跟踪工件的版本。 |
| 数据集版本控制 | S3, DVC | 您可以通过使用合适的 S3 数据分区方案来跟踪数据集的版本。上传新数据集时，可以添加唯一的 S3 存储桶/前缀来标识数据集。DVC 是另一种开源数据集版本控制系统，在创建新数据集时可以与 GitLab 和 Bitbucket 等源代码控制系统集成，S3 可继续作为您的后端存储。 |
| 元数据跟踪 | SageMaker 血缘跟踪服务 | 通过提供数据集属性和血缘等详细信息，可以跟踪与数据集关联的元数据。 |
| 容器版本控制 | Amazon ECR (Elastic Container Registry) | Amazon ECR 使用包含仓库 URI 和镜像摘要 ID 的镜像 URL 来跟踪容器版本。 |
| 训练作业版本控制 | SageMaker | SageMaker 的训练作业包含其 ARN 名称和其他元数据，例如超参数、容器、数据集和模型输出的 URI。 |
| 模型版本控制 | 模型包 | 可以使用模型包来跟踪模型版本，模型包包含其自身的 ARN 名称以及模型 URI 和容器 URI 等详细信息。 |
| 终端节点版本控制 | SageMaker | 作为创建 SageMaker 终端节点的一部分，您可以向终端节点配置数据添加其他元数据，例如使用的模型。 |

**注意** 实施数据和工件血缘跟踪系统，以了解模型的工作原理并识别潜在问题。

下表列出了 Azure 提供的跟踪工具：

| ARTIFACT | TRACKING TOOLS | DESCRIPTION |
|---|---|---|
| 代码版本控制 | Azure DevOps | 跟踪代码版本，并与 Git 仓库良好集成。 |
| 数据集版本控制 | Azure 机器学习数据集 | 用于跟踪数据集版本。 |
| 元数据跟踪 | Azure 机器学习服务 | 帮助跟踪模型训练指标、数据集属性和实验配置等元数据。 |
| 容器版本控制 | Azure 容器注册表 | 跟踪容器镜像及其版本。 |
| 训练作业版本控制 | Azure 机器学习服务 | 管理训练作业版本以及超参数、训练数据和输出等其他参数。 |
| 模型版本控制 | Azure 机器学习服务 | 跟踪模型版本。模型可以作为 Web 服务部署，并可以跟踪模型属性、部署配置和版本信息等元数据。 |
| 工件版本控制 | Azure DevOps, Azure Data Factory, Azure Data Catalog | 用于跟踪机器学习生命周期中工件的版本。 |

下表列出了 Google 提供的跟踪工具：

| ARTIFACT | TRACKING TOOLS | DESCRIPTION |
|---|---|---|
| 代码版本控制 | Git, Google Cloud 源代码仓库 | 支持集成 Git 和 Google Cloud 源代码仓库，以帮助跟踪代码版本。 |
| 数据集版本控制 | Google Cloud Storage | 数据集可以存储在 Google Cloud Storage 的版本化存储桶中，这样您就可以跟踪数据集的不同版本。 |
| 元数据跟踪 | Cloud 元数据目录 | 可以通过关联属性、描述和血缘等元数据，来跟踪模型数据集和其他工件的不同版本。 |
| 容器版本控制 | Google Cloud 容器注册表 | 可以跟踪容器镜像的不同版本。 |
| 训练作业版本控制 | Google Cloud AI 平台 | 可以跟踪训练作业、模型和终端节点的不同版本。 |
| 工件版本控制 | Kubeflow, 数据目录, Dataflow | 提供服务以跟踪机器学习生命周期中的工件。 |

