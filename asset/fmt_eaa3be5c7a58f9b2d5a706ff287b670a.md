
即使对于涉及大数据的数据管理任务，我们仍可能面临面向 AI/ML 目的的数据可用性和易用性受限的问题，这限制了我们训练高性能 ML 模型的能力。对于有监督和无监督学习任务，我们可能首先需要使用数据集成工具来统一跨孤岛的训练数据。对于通常需要大量标注数据的有监督学习，有一些策略可应对标注数据不足的问题，例如通过众包、合成数据、半监督学习、弱监督学习以及带反馈循环的主动学习。迁移学习也被证明能大幅减少文本、图像、音频和视频数据应用所需的标注训练样本数量。我们还需要节约用数据，并建立长期数据收集策略，主动且全面地评估组织需要收集哪些新数据项，包括当下虽无即时用途但未来可能有帮助的数据，并开始日积月累地收集此类数据。我们必须谨慎对待丢弃原始数据。例如，采用传统 ETL 方法构建数据仓库时，如果仅存储最终转换后的数据，可能会丢失嵌入在原始数据中的某些信息，而这些信息恢复成本高昂甚至根本无法恢复。历史上，我们仅保留转换后的数据以降低存储成本，但随着存储成本降低，我们需要仔细权衡存储成本与因丢失潜在有价值信息而产生的机会成本。除了数据记录，其他数据资产（如元数据、分析结果、图表、仪表板、BI 报表、模型、数据 API 以及模型/API 的元数据）也可纳入收集范围。除满足法规留存要求外，所有这些都有助于数据编目、血缘追踪和 ML 模型训练。

### 弥合 AI/ML 知识鸿沟

数据运维和业务运维团队对 AI/ML 技术缺乏了解是一个合理的担忧。DataOps 和业务专家通常不具备完全掌握底层 ML 算法内部运作的技术诀窍。这就是团队中的数据科学家可以发挥作用的地方：他们可以向其他同事普及基础知识、选择合适的算法、训练高性能模型、了解局限性、评估适用性并监控模型性能。此外，如前所述，已有许多内置 AI/ML 且开箱即用的应用，面向所有人而非仅限数据科学家。技术公司、学术研究机构和开源社区持续推动 AI/ML 的普及，我们应期待更多面向各类业务领域的用户友好型 AI/ML 工具。认为 AI/ML 只是少数技术特权阶层专属的观念是一种误解。我们有责任紧跟最新进展并尝试应用。由于许多 AI/ML 应用需要用户反馈来改进（例如聊天机器人），我们使用得越多、提供的反馈越多，其性能就能变得越好。持续的用户反馈也有助于缓解数据可用性问题。

### ML 算法在数据管理中的局限性

现有 ML 算法的质量、准确性和能力可能无法满足所有相关数据管理任务的需求。一般来说，标注数据（及有监督学习）比未标注数据（及无监督学习）更具信息量。然而，对于许多（如果不是大多数）数据管理任务而言，标注数据难以获取。即使有标注数据可用，针对不同的数据标注机制和不同级别的标注准确性，也需要不同的机器学习方法。有一些通用框架可处理标注数据不足的问题，如半监督学习和弱监督学习，但它们可能需要针对特定用例进行调整。面向数据管理的 ML 算法质量仍处于持续研究和改进之中。特别是在利用 AI/ML 将领域知识嵌入数据清洗过程中，挑战依然存在，要让机器像人类专家一样胜任地判断保留、修改或重新格式化哪些数据，并非易事。知识图谱在一定程度上有助于提供更好的上下文、揭示更多关联，并拓展机器寻找额外模式和规则以更自主地处理数据的能力。然而，建立数据转换规则的数据处理过程仍主要是一项依赖人力的密集型工作。

### 资源限制与预算分配

缺乏足够资源可能阻碍运维团队开展 AI/ML 辅助的数据管理计划。若因预算限制，则预算分配决策可参考成本/收益分析，纳入未来企业需求考量，而非仅寻求满足当前需求的最低成本方案。在有限预算内，我们可以通过一些易于实施的 AI/ML 辅助流程优化和/或自动化，从效率快速见效处着手，实现初步资源节约。这将让运维团队腾出更多时间专注于进一步创新等。这样，获得的效率提升可通过良性循环自我强化。

### 与企业系统集成

数据管理不能孤立进行。它需要与业务运营和风险管理紧密集成。AI/ML 辅助的数据管理系统也需要其他先进技术的支持，以更好地发挥其潜力。企业系统（包括数据管理系统）需要通过 API、微服务和消息系统（如 `Google Cloud Pub/Sub` 和 `Apache Kafka`）等技术进行互通。数据系统内部数据资产间的连接以及企业系统间的连接，可由企业知识图谱捕捉，而企业知识图谱本身可结合其他 AI/ML 工具进行开发和支持。

## 参考文献

[1] T. Kraska, A. Beutel, E. H. Chi, J. Dean and N. Polyzotis, *The Case for Learned Index Structures*, 2018. [Online]. Available: <https://arxiv.org/abs/1712.01208>

## 第 9 章

### 利用云基础设施进行数据集成的技术与策略

**葛智宇**

#### 9.1 简介

全球各地的企业越来越依赖数据来提供业务洞察和高级分析，以支持数据驱动的决策。这一目标需要一个设计良好的企业数据存储和处理框架，该框架能集成来自组织各部门、多个数据源、多种格式的数据。云基础设施不仅能提供存储空间和计算能力，还能为跨不同业务单元和支持职能部门管理、集成和共享数据提供坚实基础。规模经济也使得云实施成为一种具有成本效益的解决方案。企业日益意识到，基于云的数据解决方案应成为其企业数据战略的重要组成部分。本章讨论企业可用于利用云基础设施进行数据集成的最新技术和策略。

#### 9.2 云数据集成服务

我们首先对主要的云数据集成服务进行高层概览。以三大主要云服务提供商 Amazon Web Services (AWS) [[1]](#chap9.xhtml#rref1)、Azure [[2]](#chap9.xhtml#rref2) 和 Google Cloud Platform (GCP) [[3]](#chap9.xhtml#rref3) 的数据集成服务为例进行并行讨论。其他主要云服务提供商也在其各自的平台上提供类似的服务。下文的表 9.1 对这些公有云平台上可用的一些常见云集成服务提供了高层概览。

云平台在数据移动方面提供了极大的灵活性。主要云服务提供商开发并维护大量连接器，用于从各种外部来源（包括客户本地系统、物联网设备和其他云平台）摄取数据。特别是 AWS 和 GCP 都拥有多个解决方案组件，可针对不同规模、来源和延迟的组合摄取数据。例如，本地数据库可使用 `AWS Database Migration Service`、`Azure Database Migration Service` 和 `Google Cloud Storage Transfer Service` 进行批量加载。来自物联网设备的流式数据可通过 `AWS Kinesis`、`Azure Event Hubs` 和 `GCP Pub/Sub` 进行传输。这种数据移动的灵活性使企业能够将来自不同来源的数据聚合到云环境中，以便进一步集成。

**表 9.1.** 常见云数据集成服务摘要

![](img/p312.jpg)

在数据存储库方面，云拥有巨大的存储空间，对单个客户而言容量几乎无限。企业可以使用云数据湖来存放来自各种数据源的结构化、半结构化和非结构化数据，具有高耐久性、灵活性、可用性、可扩展性和安全性。与本地数据中心相比，它是一种低成本的替代方案。数据湖可托管在 `Amazon Simple Storage Service (S3)`、`Azure Data Lake Storage` 和 `Google Cloud Storage` 上。数据仓库可由 AWS 上的 `Redshift`、Azure 上的 `Synapse Analytics`（前身为 `SQL Data Warehouse`）和 GCP 上的 `BigQuery` 进行管理。`Delta Lake` 在现有数据湖之上增加了一个结构化的 ACID（原子性、一致性、隔离性和持久性）事务层，是最新的最先进数据存储库，能显著提升数据管理和数据利用在速度、容量、质量和功能方面相较于数据湖的水平。云上的托管 `Delta Lake` 服务由 `Databricks` 提供。

云上的数据处理利用了云基础设施自带的巨大算力。可使用具有自动扩缩容功能的 `Spark` 和 `Hadoop` 集群进行高级分布式处理。还可应用 `Parquet` 列式格式和智能数据分区，以进一步最大化数据处理效率、降低延迟并提高吞吐量。在 AWS 上，`EMR (Elastic Map-Reduce)` 是一项完全托管的数据湖服务，支持分布式数据处理。`Google Cloud Dataproc` 提供类似的服务、功能和性能。`Azure Data Lake` 是微软完全托管的数据湖服务，包含 4 个关键构建模块：(i) 核心数据湖基础设施，(ii) `Azure Data Lake Storage (ADLS)`，(iii) `Azure Data Lake Analytics (ADLA)`，和 (iv) `Azure HDInsight`。`AWS Glue` 是一项完全托管的 ETL（抽取、转换、加载）服务。其 Azure 对应产品是 `Azure Data Factory`，GCP 对应产品是 `Cloud Data Fusion`。云上还提供第三方托管的企业级分布式数据处理解决方案，如 `Databricks`、`Snowflake`、`Confluent` 和 `Cloudera`。

云平台还提供数据生命周期管理工具，用于创建、执行和管理数据管道，创建和维护数据目录，以及跟踪数据血缘。`AWS Data Pipeline`、`Azure Data Factory` 和 `GCP Dataflow` 可用于在云中调度常规的数据移动和数据处理活动。它们都能与本地和基于云的存储系统集成。`AWS Glue` 可为 ETL 生成数据目录，`Azure Purview Data Catalog` 和 `GCP Data Catalog` 也能实现相同功能。`AWS Glue DataBrew` 可跟踪和可视化数据血缘，安装在 `Amazon EMR` 之上的 `Apache Atlas` 提供血缘、发现和分类功能。在 Azure 上，`Data Factory`、`Data Share`、`Power BI` 和数据存储系统可在数据移动过程中捕获数据血缘，而 `Azure Purview` 可将血缘信息拼接在一起，展示端到端的数据集依赖关系。`GCP Cloud Data Fusion` 提供数据集级和字段级的血缘，并可随时间跟踪血缘。`Informatica Enterprise Data Catalog` 是一项在 AWS、Azure 和 GCP 上均可用的第三方托管服务，可利用 AI 驱动的数据目录跟踪数据血缘。`Zaloni Arena` 是一个包含数据目录服务的端到端 DataOps 平台，也可在 AWS Marketplace 上获取。

## 参考文献

[2] J. Leskovec, A. Rajaraman and J. D. Ullman, *Mining of Massive Datasets,* 3rd Ed. UK: Cambridge University Press, 2020.

[3] H. Song, M. Kim, D. Park, Y. Shin and J. Lee, *Learning from Noisy Labels with Deep Neural Networks: A Survey,* 2021. [Online]. Available: [`arxiv.org/abs/2007.08199`](https://arxiv.org/abs/2007.08199)

[4] B. Davay and Y. Bogdanov, “Disrupting risk management through emerging technologies”, Spark+AI Summit 2020, [`databricks.com/session_na20/disrupting-risk-management-through-emerging-technologies`](https://databricks.com/session_na20/disrupting-risk-management-through-emerging-technologies). Accessed: June 24, 2020.

[5] Informatica. *Artificial Intelligence for the Data-Driven Intelligent Enterprise,* 2020. Accessed: December 31, 2020. [Online]. Available: [`www.informatica.com/content/dam/informatica-com/en/collateral/white-paper/artificial-intelligence-for-data-driven-disruption_white-paper_3328en.pdf`](https://www.informatica.com/content/dam/informatica-com/en/collateral/white-paper/artificial-intelligence-for-data-driven-disruption_white-paper_3328en.pdf)

[6] T. Hospedales, A. Antoniou, P. Micaelli and A. Storkey, *Meta-Learning in Neural Networks: A Survey,* 2020. Accessed: November 7, 2020. [Online]. Available: [`arxiv.org/abs/2004.05439`](https://arxiv.org/abs/2004.05439)

© 2022 World Scientific Publishing Company

[`doi.org/10.1142/9789811250903_0009`](https://doi.org/10.1142/9789811250903_0009)

#### 9.3 云中的数据安全、隐私与访问控制

除了原生云解决方案外，主要云平台上还提供第三方托管的统一数据分析解决方案，这些方案不仅处理端到端的数据管道和数据生命周期管理，还能与下游分析、数据科学、机器学习建模、可视化以及 BI 报表系统集成。其中一个例子是 `Databricks`，它利用云基础设施为高效、及时、可靠且安全的大数据管理提供企业级解决方案，并提供用于下游分析、BI 和机器学习工作流的工具与服务。`Databricks` 可在 `AWS`、`Azure` 和 `GCP` 上使用。

我们的讨论仅涉及这些公有云平台上丰富数据服务的冰山一角，而且这些平台提供商不断推出新的数据服务并增强现有服务。凭借如此强大的云数据功能，这为企业在数字化转型过程中尽可能使用云作为企业数据集成平台提供了有力依据。

尽管数据安全、隐私和访问控制也是内置于云平台的基础服务之一，但该主题值得专门讨论。在本节中，我们将讨论云上用于解决数据安全、隐私和访问控制问题的功能和工具。对数据迁移策略和云中敏感信息保护的影响将在本章最后一节讨论。

在云数据中心强大的物理安全之上，主要的云数据安全功能包括身份管理、防火墙、入侵检测/防范、加密、访问控制策略和数据恢复。主要云提供商拥有专门且资质优良的安全专家，他们持续监控安全威胁并改进数据保护，以确保云安全保持最新状态。重要的是要理解，云数据安全是云提供商和客户的**共同责任**。云提供商负责其全球基础设施，包括硬件、软件、网络和设施，以及其托管服务的内置安全功能。客户负责其使用的云 `IaaS`、`PaaS` 和托管服务产品的用户配置。对于不同产品，用户配置集合可能不同，但总体而言，客户应用程序和客户数据的访问控制是客户的责任。帮助客户控制此类访问的工具（如身份管理、防火墙配置和访问策略管理）可通过云提供商提供的安全服务和云市场获得。如果使用得当，它们提供的保护至少与本地安全系统一样安全有效。

尽管云安全功能和工具强大，但如果这些工具被误用（例如，客户端防火墙配置错误），且客户内部数据保护政策和程序设计不稳健或执行不力，数据泄露仍可能发生，2019 年 Capital One 数据泄露事件即是例证。为了充分享受云安全基础设施的优势并弥补技能和知识差距，企业必须培训内部云管理员和内部用户正确使用云安全机制，确保每个人都了解其功能和潜在漏洞，并制定和严格执行合理的云安全政策。（请记住，用户是信息安全链中最关键也最薄弱的一环。）企业不应仅因 Capital One 此类安全漏洞事件而退避云技术。如果防火墙配置不当或政策未被遵守，同类泄露也可能发生在本地数据中心。与本地安全系统相比，对于大规模企业数据保护，云安全基础设施允许更便捷地部署和访问先进工具和功能，以实现实时或近实时的安全漏洞检测和防范（如带有事件日志记录的入侵检测/防范系统）。云安全日志还赋予客户跟踪应用程序和数据访问事件的能力，以便在需要时进行进一步分析/调查。因此，底线是——信任云安全基础设施，了解它，并正确使用它。

除了数据安全，保护客户数据隐私也是云提供商的重中之重。未经客户同意，云提供商不会访问或使用客户内容，并提供 `API` 供客户配置驻留在云上的数据以及在云环境中开发和/或部署的客户服务的访问控制权限。客户可以选择共享什么数据以及如何共享，无论是内部还是外部。为了满足监管对数据驻留和隐私的要求，全球云基础设施允许客户完全控制其数据所在的物理区域。许多云数据服务还具备屏蔽、加密、删除和/或追踪个人数据使用情况的能力。客户可以对自己的数据实施额外的隐私增强技术（如匿名化和差分隐私），或利用云市场上第三方供应商的数据隐私解决方案。对于个人身份信息 (`PII`) 管理，`Amazon Macie` 和 `Google Cloud Data Loss Prevention (DLP)` 是云提供商直接提供的全托管服务示例，用于敏感数据发现、分类和保护。在 `Azure` 上，可使用 `Azure Cognitive Search` 和 `Microsoft Presidio` 检测 `PII`。更多关于敏感数据识别和追踪的讨论见下一节。
