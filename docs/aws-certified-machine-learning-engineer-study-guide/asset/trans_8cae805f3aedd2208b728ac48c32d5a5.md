
# 面向 ML 工作负载的 AWS 存储服务

在接下来的章节中，将介绍 AWS 为 ML 工作负载提供的主要存储服务。我们将从三个与 `Amazon SageMaker` 原生集成的存储服务开始：`Amazon S3`、`Amazon Elastic File System (EFS)` 和 `Amazon FSx for Lustre`。

## Amazon Simple Storage Service (S3)

`Amazon S3` 是一种对象存储服务，提供行业领先的耐久性、可用性、可扩展性、安全性和性能。

对象存储是一种以称为 `objects`（对象）的非结构化格式持久化和管理数据的存储类型。随着组织踏上数字化转型之旅，其存储大量非结构化数据（如照片、视频、电子邮件、网页、传感器数据和音频文件）的能力已成为其数字化转型的关键方面。

`Amazon S3` 将这些数据分布在多个物理设备上，但允许用户通过唯一标识符（即对象的 `Uniform Resource Identifier (URI)`，统一资源标识符）高效地访问内容。

对象存储的主要优势在于近乎无限的可扩展性，以及为数据湖、云原生应用程序、分析、日志文件和 ML 等用例存储大量数据的较低成本。

对象存储还提供更高的数据耐久性和弹性，因为它将对象存储在多个设备、跨多个系统，甚至跨多个可用区和区域上。这使得规模近乎无限，并提高了数据的弹性和可用性。

凭借与 `Amazon SageMaker` 的原生集成，`Amazon S3` 是 AWS 上最具成本效益且用户友好的 ML 操作存储选项之一。它提供一系列存储类别以适应不同的访问模式和预算，使其成为存储训练数据和模型工件的多功能选择。此外，`Amazon S3` 与各种 AWS 服务（如 `AWS Lambda`、`Amazon Elastic Container Services (ECS)` 和 `Amazon Elastic Kubernetes Services (EKS)`）的集成简化了构建、训练和部署 ML 模型的过程。

[图 2.4](#c002.xhtml#c02-fig-4) 展示了一个简单的工作流，突出了 `Amazon S3` 和 `Amazon SageMaker` 在 ML 生命周期中如何相互交互。

![图 2.4 ML 生命周期中 Amazon S3 的使用。](images/c02f004.png)

[图 2.4](#c002.xhtml#rc02-fig-4) ML 生命周期中 Amazon S3 的使用。

为了备考，请确保您对 `Amazon S3` 存储类别有很好的理解，如[表 2.4](#c002.xhtml#c02-tbl-4)所述。

[表 2.4](#c002.xhtml#rc02-tbl-4) Amazon S3 存储类别。

| S3 存储类别 | 说明 |
| --- | --- |
| S3 Standard | 专为频繁访问的数据设计 |
| S3 Intelligent-Tiering | 根据不断变化的数据访问模式，自动在两个访问层级之间移动数据以优化成本 |
| S3 Express One Zone | 高性能、单可用区存储类别，为延迟敏感型应用程序提供一致的个位数毫秒级数据访问 |
| S3 Standard-IA (infrequent access) | 适用于访问频率较低但需要在需要时快速访问的数据，成本低于 S3 Standard |
| S3 One Zone-IA | 适用于不需要多可用区弹性的非频繁访问数据，提供更低的存储成本 |
| S3 Glacier Instant Retrieval | 专为需要即时访问的长期、极少访问的数据设计，提供低检索时间和成本 |
| S3 Glacier Flexible Retrieval | 用于检索时间从几分钟到几小时不等的归档数据，提供低成本存储 |
| S3 Glacier Deep Archive | 为长期数据归档提供最低成本存储，检索时间长达 12 小时 |
| S3 Outposts | 将 S3 存储引入您的本地环境，确保一致的性能并满足数据驻留要求 |

### Amazon Athena

`Amazon Athena` 是一项无服务器的交互式查询服务，允许您使用标准 SQL 直接分析 `Amazon S3` 中的数据。

借助 `Amazon Athena`，您可以针对存储在 S3 中的数据执行 SQL 查询。示例包括 CSV、JSON 或列式数据格式，如 `Apache Parquet` 和 `Apache ORC`。

### 用例

基于专为持久化大量非结构化数据而设计的弹性架构，`Amazon S3` 最适合以下用例：

*   **数据湖和 ML。** 数据湖是一个集中式存储库，允许您按任何规模以原始格式存储所有数据。您可以使用数据湖运行数据处理、数据分析、ML 和高性能计算 (HPC) 应用程序，以释放数据的价值。
*   **数据备份和恢复。** 凭借 `Amazon S3` 强大的复制和数据保护功能，您可以构建满足恢复时间目标 (RTO)、恢复点目标 (RPO) 和合规要求的应用程序。
*   **数据归档。** 您可以将“冷”数据（必须为合规而保留的非频繁访问数据）保留到 `Amazon S3 Glacier` 存储类别中，以降低成本、消除运营复杂性并满足组织的数据归档要求。
*   **生成式人工智能 (AI)。** 在撰写本书时，`Amazon S3` 为超过 350 万亿个对象存储了 EB 级数据，平均每秒处理超过 1 亿次请求。凭借这种大规模的可扩展性，`Amazon S3` 是准备和训练大语言模型 (LLM) 的理想存储服务。LLM 在自监督和半监督训练过程中，通过从海量数据中学习统计关系进行训练。我们将在后续章节中介绍这些概念。

## Amazon Elastic File System (EFS)

`Amazon EFS` 是一种无服务器、完全弹性的 AWS `file-based`（基于文件）存储服务。其无服务器特性意味着无需管理、配置和创建底层基础设施；AWS 将为您执行这些任务。

`Amazon EFS` 使您能够在 AWS 上创建和配置分布式文件系统，并将其挂载到各种 AWS 计算资源，包括 `Amazon EC2` 实例、`Amazon EKS` 集群、`Amazon ECS`、`AWS Lambda` 函数等。无需预置、部署、修补或维护。

它还支持流行的 NFS 4.0 和 4.1 (`NFSv4`) 协议，从而实现与需要 NFS 的工作负载的无缝集成。

然后您可以共享这些文件，通过 `Amazon EFS` 生命周期管理优化成本，并通过 `AWS Backup` 和 `Amazon EFS` 复制进一步保护数据。

其弹性能力意味着该服务将按需将工作负载扩展到 PB 级存储和 GB/秒级吞吐量，开箱即用。

采用 `pay-as-you-go`（按量付费）定价模式，您可以利用其内置的生命周期管理功能降低总拥有成本 (TCO)，该功能旨在智能地将“冷”数据移动到成本优化的非频繁访问和归档 `EFS` 存储类别。

作为 `Amazon S3` 的替代方案，如果您的训练数据已驻留在 `Amazon EFS` 中，您可以轻松地在 `Amazon SageMaker` 中访问和使用这些数据进行模型训练。这种集成简化了工作流，使您能够在高效开发和部署 ML 模型的同时，利用 `Amazon EFS` 可扩展且高性能的存储能力。

[图 2.5](#c002.xhtml#c02-fig-5) 展示了一个示例工作流，显示了如何在 ML 生命周期中使用 `Amazon EFS` 存储训练数据和学习工件。

![图 2.5 ML 生命周期中 Amazon EFS 的使用。](images/c02f005.png)

[图 2.5](#c002.xhtml#rc02-fig-5) ML 生命周期中 Amazon EFS 的使用。
