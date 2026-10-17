

Figure 8.11: SageMaker 托管架构

SageMaker 托管服务提供多种模型推理选项，以满足不同需求，从实时推理到批量推理。以下是数据科学家可用于模型托管评估和测试的一些选项：

*   最常见的模型服务用例之一是持续进行的低延迟实时预测。对于此用例，您应考虑 SageMaker 托管服务中的 `real-time inference` 选项。SageMaker 实时推理为模型托管提供多种选项，包括单模型托管、单个端点后面单个容器中的多模型托管，以及单个端点后面使用不同容器的多模型托管。

*   有时，您会有用于间歇性预测的模型，流量高峰之间有空闲期。对于此类需求，您可以考虑 SageMaker 托管服务中的 `Serverless` 选项。使用无服务器推理的关键优势是消除了基础设施配置和管理开销。它也更具成本效益，因为在未使用时无需为基础设施付费，而实时推理则不同，无论是否有推理流量，您都需要为基础设施付费。但是，当模型首次调用或调用之间存在较长空闲时间以允许 SageMaker 无服务器推理启动实例时，无服务器推理可能会因冷启动而出现延迟。

*   有时，推理的有效载荷大小可能非常大，生成预测需要很长时间。在这种情况下，实时端点无法工作，因为有效载荷大小和推理时间较长。对于此类用例，您可以考虑 SageMaker 托管的 `the asynchronous inference` 选项。异步推理将传入请求排队并异步处理（顾名思义）。使用异步推理时，输入数据和预测输出存储在 S3 中，而不是直接从端点 API 发送有效载荷并获取响应。当预测完成时，您会收到 AWS SNS 服务的通知。

*   另一种模型推理模式是 `batch inference`。这是当您有大量推理需要执行，且不需要单独生成和返回预测时。例如，您可能需要为大量用户运行购买倾向模型，并将输出存储在数据库中以供下游使用。对于此使用模式，您可以考虑 SageMaker Batch Transform 功能进行模型推理。批量推理也更具成本效益，因为您只需在运行批量作业时启动基础设施。

讨论了完成 ML 项目所涉及的各种任务，从数据准备到使用不同 SageMaker 功能进行模型部署，现在让我们简要谈谈自动化的需求。数据科学家经常进行迭代实验和模型开发，涉及不同的数据集、新功能和各种训练脚本。跟踪每次运行的配置和模型指标变得至关重要。为了简化和自动化这些重复性任务，可以构建自动化管道，支持各种 ML 过程，如数据处理、模型训练和模型测试。

有多种可用于自动化和编排的工具，包括 SageMaker 的 Pipelines 功能。它允许创建 `Directed Acyclic Graph` (`DAG`) 以高效地编排和自动化 ML 工作流。SageMaker Pipelines 与 Airflow 相似，Airflow 是在 `Chapter 7`、`Open-Source ML Platforms` 中讨论的开源工作流编排工具。

此外，AWS Step Functions 是构建自动化工作流编排的另一种选择，提供灵活性和可扩展性，以适应各种 ML 任务。通过利用这些工具，数据科学家可以提高其 ML 工作流的效率、可重复性和组织性。

# 构建数据科学环境的最佳实践

数据科学环境旨在让数据科学家使用各种 ML 框架和库进行快速实验。为数据科学家提供此类环境时，应遵循以下一些最佳实践：

*   `Run large-scale model training using the SageMaker Training service instead of Studio notebooks`: SageMaker Studio 笔记本旨在使用小数据集进行快速实验。虽然可以为某些大型模型训练作业配置大型 EC2 实例，但始终为笔记本运行大型 EC2 实例并不具成本效益。

*   `Abstract infrastructure configuration details from data scientists`: 使用 SageMaker 时需要考虑许多基础设施配置，例如网络配置、IAM 角色、加密密钥、EC2 实例类型和存储选项。为了让数据科学家的生活更轻松，应将这些细节从数据科学家中抽象出来。例如，不要让数据科学家输入特定的网络配置，而是将这些详细信息存储为环境变量或自定义 SDK 选项，供数据科学家选择。

*   `Create self-service provisioning`: 为了防止配置瓶颈，考虑构建自助服务配置功能以简化用户入职。例如，使用 AWS Service Catalog 创建 ML 产品以实现自动化用户入职。

*   `Use Studio notebook local mode for quick model training job testing`: SageMaker 支持本地模式，这意味着您可以在 Studio 笔记本中模拟本地运行训练作业。使用 SageMaker 训练作业时，会有启动单独基础设施的开销。在本地运行这些测试可以帮助加快实验速度。

*   `Set up guardrails`: 这有助于防止数据科学家犯错，例如为模型训练使用错误的实例类型或忘记使用数据加密密钥。您可以使用 AWS 服务控制策略来帮助进行护栏管理。

*   `Clean up unused resources`: 定期审查并清理未使用的笔记本、端点和其他资源，以避免不必要的成本。

*   `Use Spot instances`: 为了成本优化，如果可能，请考虑为训练作业使用 Amazon EC2 Spot 实例。Spot 实例可以显著降低训练成本，同时保持高性能。但是，由于 Spot 实例可能会被意外收回，因此启用训练检查点非常重要，以便训练可以从上次检查点恢复，而不是从头开始重新训练。

*   `Use built-in algorithms and managed containers for training`: SageMaker 提供了一系列用于不同 ML 任务的内置算法和用于不同 ML 框架的托管训练容器。利用这些现有资源可以大幅减少所需的工程工作量，无需从头开始构建自己的算法。

*   `Build automated pipelines for repeatable ML experimentation, model building, and model testing`: 拥有自动化管道可以大幅减少手动工作量并改进不同实验的跟踪。根据您的技术标准和偏好，考虑不同的编排技术选项。

通过遵循这些最佳实践，您可以充分利用 SageMaker Studio 的功能，简化 ML 工作流，并确保平台的成本效益和安全使用。

# 实践练习 – 使用 AWS 服务构建数据科学环境

