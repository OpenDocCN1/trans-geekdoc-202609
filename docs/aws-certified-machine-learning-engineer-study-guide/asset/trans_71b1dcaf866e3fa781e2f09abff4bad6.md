

# 基础设施即代码与 MLOps 编排

由于现代基础设施已实现虚拟化，通过手动流程管理和配置计算资源变得不切实际且容易出错。这就是**基础设施即代码**（**IaC**）发挥作用的地方，它允许您以声明方式使用机器可读的配置文件来定义和管理基础设施。`AWS CloudFormation` 和 `Terraform` 是两款流行的 IaC 工具，可让您自动设置和管理基础设施。`AWS CloudFormation` 为您提供了一种通用语言，用于描述和预配云环境中的所有基础设施资源。使用 `AWS CloudFormation`，您可以使用简单的文本文件（采用 JSON 或 YAML 格式），以自动化且安全的方式，为跨所有区域和账户的应用程序建模并预配所需的所有资源。`Terraform` 由 HashiCorp 开发，是一款开源 IaC 工具，可让您安全高效地构建、更改和版本化基础设施。它提供了一致的 CLI 工作流来管理数百种云服务。这两种工具都能确保您的基础设施设置具有可重复性、一致性和版本控制，就像应用程序代码一样。然而，`AWS CloudFormation` 和 `Terraform` 要求开发人员使用特定的配置语言，这可能会带来限制。这些工具使用 JSON、YAML 和 HashiCorp 配置语言 (HCL)，限制了用于定义基础设施的编程语言选择。许多开发人员更倾向于使用他们更熟悉的语言，例如 JavaScript 或 Python。这就是 `AWS Cloud Development Kit` (`AWS CDK`) 发挥作用的地方。借助 `AWS CDK`，开发人员可以使用 JavaScript、TypeScript、Python、Java、C# 和 Go 来创建 IaC。[图 6.8](#c006.xhtml#c06-fig-8) 说明了这些服务如何融入 CI/CD 流水线和 IaC 领域。

![图 6.8 CI/CD 流水线。](images/c06f008.png)

[图 6.8](#c006.xhtml#rc06-fig-8) CI/CD 流水线。

## MLOps 编排

编排工具在自动化和管理复杂的 ML 工作流中起着关键作用。MLOps 将 DevOps 原则融入 ML，确保 ML 模型的持续集成、交付和部署。

对于考试而言，除了已介绍的 `Amazon SageMaker Pipelines` 之外，您还需要了解其他选项：即 `AWS Step Functions` 和 `Amazon Managed Workflows for Apache Airflow`。`AWS Step Functions` 是一项强大的编排服务，可让您将多项 AWS 服务协调到无服务器工作流中，从而更轻松地构建和监控自动化流程。`Amazon Managed Workflows for Apache Airflow` 是另一项关键编排服务，它简化了 Apache Airflow 的设置和运行，允许您以编程方式创作、调度和监控工作流。这些工具对于管理 ML 流水线的各个阶段至关重要，从数据预处理和特征工程到模型训练、评估和部署。现在让我们更详细地回顾这两种编排工具。

### AWS Step Functions

`AWS Step Functions` 是一项无服务器编排服务，可让您将多项 AWS 服务协调到可扩展的工作流中。通过使用 `AWS Step Functions`，您可以设计和运行复杂的工作流，这些工作流由各个单独的任务组成，每个任务代表流程中的一个步骤。该服务提供可视化界面来构建工作流，从而更轻松地监控和管理每个步骤的执行。在结合 `Amazon SageMaker AI` 的 MLOps 背景下，`AWS Step Functions` 可以编排整个 ML 生命周期，从数据预处理和特征工程到模型训练、调优和部署。您可以定义捕获任务序列的状态机，`AWS Step Functions` 可确保每个步骤按正确顺序执行并妥善处理错误。此外，`AWS Step Functions` 支持大规模并行工作流，支持数据密集型 ML 任务的并发执行。这种编排能力简化了 ML 流水线的管理，提高了可重复性，并增强了 ML 运营的整体效率。

### Amazon Managed Workflows for Apache Airflow

`Amazon Managed Workflows for Apache Airflow` (`MWAA`) 是一项托管服务，可简化 Apache Airflow（一个开源工作流编排平台）的设置和运行。Airflow 允许您以编程方式创作、调度和监控工作流，使其成为管理复杂数据流水线的理想选择。借助 `MWAA`，AWS 负责 Airflow 环境的预配、扩展和维护，让您能够专注于构建和管理工作流，而无需承担基础设施管理的开销。`MWAA` 可与其他 AWS 服务（如 `S3`、`Redshift` 和 `Elastic Map Reduce` (`EMR`)）无缝集成，使您能够创建高度可扩展且可靠的数据工作流。在 MLOps 背景下，`MWAA` 可用于编排 ML 流水线的各个阶段，包括数据提取、转换、加载 (ETL)、模型训练、评估和部署。通过利用 `MWAA`，组织可以确保其数据工作流高效、一致且具有弹性，为其 ML 运营提供坚实的基础。

### 选择编排工具

在 AWS 中为 ML 工作流选择编排工具时，考虑工作流的复杂性以及团队对工具的熟悉程度非常重要。

`AWS Step Functions` 是一项无服务器、易于使用的编排服务，可与其他 AWS 服务无缝集成。它非常适合编排端到端 ML 流水线，提供用于设计和监控工作流的可视化界面。它非常适合寻求简便性和最小运维开销的团队。

`MWAA` 面向更可定制和灵活的编排需求。它支持复杂的工作流并提供丰富的插件生态系统，使其成为数据工程任务和熟悉 Apache Airflow 的团队的完美选择。`MWAA` 负责 Airflow 环境的预配、扩展和维护，让您能够专注于工作流管理。

`Amazon SageMaker Pipelines` 专为 ML 工作流而设计。它提供内置的编排功能，允许 ML 工程师和数据科学家定义、可视化和自动化端到端 ML 流程。`Amazon SageMaker Pipelines` 可与其他 `Amazon SageMaker` 服务无缝集成，使其成为管理整个 ML 生命周期（从数据预处理和特征工程到模型训练、调优和部署）的绝佳选择。

在 `AWS Step Functions`、`Amazon MWAA` 和 `Amazon SageMaker Pipelines` 之间进行选择，最终取决于您的具体用例。`AWS Step Functions` 和 `Amazon MWAA` 为各种工作流提供通用编排，而 `Amazon SageMaker Pipelines` 专为 ML 量身定制，确保与整个 `Amazon SageMaker` 生态系统无缝集成。

[图 6.9](#c006.xhtml#c06-fig-9) 总结了您刚学习的存储库和编排服务，以帮助简化您的 ML 工作流并确保高效、可重复的运营。

![图 6.9 存储库和编排服务。](images/c06f009.png)

[图 6.9](#c006.xhtml#rc06-fig-9) 存储库和编排服务。

在接下来的章节中，我们将重点关注 `Amazon SageMaker Pipelines`，这是考试的一个关键要求。

## 自动化模型构建和部署

