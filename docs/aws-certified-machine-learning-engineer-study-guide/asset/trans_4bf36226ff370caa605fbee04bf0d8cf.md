

# 面向 ML 工作负载的 Trusted Advisor 建议

Trusted Advisor 的建议对于管理 ML 工作负载的复杂性特别有益。通过持续监控您的 AWS 资源，AWS Trusted Advisor 有助于确保您的 ML 基础设施符合最佳实践，并配置为实现最佳性能。这包括识别提高数据预处理、模型训练和推理任务效率的机会。例如，AWS Trusted Advisor 可能会建议为您的 Amazon SageMaker AI 终端节点启用自动扩展以高效处理不同的负载，或者它可能会建议优化您的存储配置以提高数据访问速度。借助 AWS Trusted Advisor 提供的见解，您可以维护一个安全、高效且具有成本效益的 ML 环境，从而使您能够专注于开发和部署高质量的 ML 模型。

## AWS Budgets

AWS Budgets 是一项功能强大的服务，允许您为 AWS 资源设置自定义成本和使用预算，帮助您有效监控和控制支出。对于 ML 工作负载，AWS Budgets 在管理与 ML 生命周期各个阶段（如数据预处理、模型训练和推理）相关的成本方面特别有益。通过为不同的 ML 项目或团队设置特定预算，您可以确保支出符合财务目标，并防止意外的成本超支。此外，AWS Budgets 允许您在实际或预测支出超过预定义阈值时通过电子邮件或短信接收警报，从而实现主动的成本管理和及时干预。

在 ML 工作负载的背景下，AWS Budgets 提供了多项优势。例如，您可以创建成本分配标签，按项目、部门或任何其他相关标准对 ML 资源进行分类。这使您能够准确跟踪和分配成本，确保每个 ML 项目都在其预算范围内。AWS Budgets 还与 AWS Cost Explorer 集成，使您能够直观地查看预算执行情况，并做出数据驱动的决策以优化 ML 基础设施。通过利用 AWS Budgets，您可以控制 ML 支出，高效分配资源，并确保 ML 计划的财务可持续性。

## 定价模型

AWS 为计算基础设施提供了多种定价模型，每种模型均旨在根据不同的使用模式和需求提供灵活性和成本效益。对于 ML 工作负载，选择正确的定价模型对于在确保最佳性能的同时管理成本至关重要。主要定价模型包括按需实例、预留实例、Savings Plans、竞价型实例和专用主机。这些模型提供不同程度的承诺、成本节省和灵活性，使您能够根据特定的项目需求和预算限制定制 ML 基础设施。

* **`On-Demand Instances`** 按即用即付模式收费，使其成为不可预测的 ML 工作负载的理想选择，这些工作负载需要灵活性，无需长期承诺。它们允许您按小时或秒（取决于实例类型）支付计算容量费用。
* **`Reserved Instances`** 则通过承诺在一年或三年内使用特定容量，为稳态和可预测的工作负载提供显著的成本节省。
* **`Savings Plans`** 为预留实例提供了一个更灵活的替代方案，允许您承诺在一年或三年内使用特定金额的用量（以美元/小时衡量）。在撰写本书时，有三种不同的 Savings Plans：Compute Savings Plans（适用于 Amazon EC2、AWS Lambda 和 AWS Fargate 用量）、EC2 Instance Savings Plans 和 Amazon SageMaker Savings Plans。
* **`Spot Instances`** 允许您以较低的价格竞购闲置的 EC2 容量，使其适用于灵活的、容错的 ML 任务，如批处理和数据预处理。
* **`Dedicated Hosts`** 提供专供您使用的物理服务器，确保敏感 ML 工作负载的合规性和安全性。

[表 7.1](#c007.xhtml#c07-tbl-1) 总结了这些 AWS 定价模型，重点介绍了每种模型的工作原理、最适用的场景以及租户类型（基础设施是与其他 AWS 客户共享还是专用于您的 AWS 账户）。该表可作为了解 ML 计算基础设施可用不同定价选项的有用参考。

[表 7.1](#c007.xhtml#rc07-tbl-1) 面向计算基础设施的 AWS 定价模型。

| 定价模型 | 工作原理 | 租户类型 | 用例和 ML 相关性 |
| --- | --- | --- | --- |
| 按需 | 为使用的计算时间付费，无长期承诺 | 共享 | 适合不可预测的工作负载和探索性数据分析。适用于临时模型训练和测试新算法。 |
| 预留实例 | 以折扣价承诺 1 年或 3 年的容量 | 共享/专用 | 最适合稳态、可预测的工作负载。对于长期 ML 项目和生产环境具有成本效益。 |
| Savings Plans | 承诺一年或三年内特定的美元/小时用量以获取更低价格 | 共享/专用 | 适合用量可预测的工作负载。降低持续训练和推理任务的成本。 |
| 竞价型实例 | 以较低价格竞购闲置容量：可能被中断 | 共享 | 适合灵活、容错的应用程序。适用于非关键 ML 任务，如批处理和数据预处理。 |
| 专用主机 | 为专供您使用的物理服务器付费 | 专用 | 最适合需要物理隔离的法规要求。确保敏感 ML 工作负载的合规性和安全性。 |

AWS 提供的多种定价模型可以帮助您优化成本以满足预算，确保高效的资源利用，并维护 ML 环境的性能和安全性。

### Amazon SageMaker Savings Plan

Amazon SageMaker Savings Plans 为 ML 工作负载提供了一种灵活且具有成本效益的定价模型。您承诺在一年或三年期限内使用一致的用量（以美元/小时衡量），并可获得高达 64% 的显著成本节省（与按需定价相比）。这些 Savings Plans 会自动应用于符合条件的 Amazon SageMaker AI 实例用量，包括 Amazon SageMaker Studio Notebook、Amazon SageMaker On-Demand Notebook、Amazon SageMaker Processing、Amazon SageMaker Data Wrangler、Amazon SageMaker Training、Amazon SageMaker Real-Time Inference 和 Amazon SageMaker Batch Transform。这种灵活性允许您在不失去节省成本优势的情况下切换实例类型或区域，从而更轻松地在优化 ML 基础设施的同时管理成本。

除了成本节省，Amazon SageMaker Savings Plans 还在 AWS Savings Plans 中提供了最大的灵活性。您可以将用量从一种实例类型更改为另一种，或跨不同区域移动工作负载，同时仍可享受承诺的 Savings Plan 价格。例如，您可以随时将在美国东部（俄亥俄州）运行的 CPU 实例 `ml.c5.xlarge` 切换为美国西部（俄勒冈州）的 `inf1.2xlarge` 实例用于推理工作负载，并继续按 Savings Plan 价格付费。这种适应性确保您可以高效管理 ML 项目，而无需担心意外的成本激增，使其成为希望优化 ML 投资的组织的理想选择。

## 摘要

