

# 服务模式

## Software as a Service (SaaS)

在 SaaS 模式下，云服务提供商将其运行在自有基础设施上的应用程序出租给客户。除了平台和底层基础设施外，软件应用程序的维护也由云服务提供商负责。我们可以通过 Web 浏览器、应用浏览器等方式，在任意设备上访问这些软件程序。电子邮件（Gmail）和云存储（Google Drive）是 SaaS 的两个典型例子。

## Data as a Service (DaaS)

与已流行十余年的上述三种服务模式不同，DaaS 是一种刚开始广泛应用的服务。这部分原因是通用云计算服务最初并非为管理海量数据工作负载而构建；它们主要面向应用托管和基础数据存储需求（而非数据集成、分析和处理）。

SaaS 消除了在本地计算机上安装和管理软件的必要性。同样，Data-as-a-Service 方法论的核心是利用应用程序编程接口（API）按需从多个来源交付数据。其旨在简化数据访问，并提供可供以多种形式使用的精选数据集或数据流。这些格式通常通过数据虚拟化进行统一。事实上，DaaS 架构可能包含多种数据管理技术，如数据虚拟化、数据服务、自助式分析。

从最基本的形式来看，DaaS 使组织能够访问其可用的、日益增长的数据源数量和复杂度，从而为消费者提供最相关的洞察。数据民主化是每家想要从数据中获取实际价值的公司的绝对必要条件。它通过采用更以数据为中心的运营和程序方法，为将组织数据货币化并获得竞争优势提供了巨大潜力。

# GCP 提供的服务

用户可以使用 Google Cloud Platform 提供的全面服务选择。每一项服务都可归入 [图 1.10](#ch01.xhtml#fig1-10) 所示的类别之一：

![](images/Figure_1.10.png)

**图 1.10：GCP 的服务**

*   **存储**：Google 提供用于存储非结构化项目的 `Cloud Storage`、用于以传统方式共享文件的 `Filestore`，以及用于虚拟机的 `persistent disk`。
*   **计算**：`Compute Engine`、`App Engine`、`Cloud Run`、`Kubernetes Engine` 和 `Cloud Functions` 是 GCP 提供的核心计算服务。
*   **关系型数据库**：`Cloud SQL` 支持 `MySQL`、`PostgreSQL` 和 `Microsoft SQL Server`；`Cloud Spanner` 是一个能够在全球范围内运行的大规模可扩展数据库。
*   **NoSQL 数据库**：`Bigtable`、`Firestore`、`Memorystore` 和 `Firebase Realtime Database` 是 Google 提供的不同 NoSQL 服务。
    *   处理海量分析工作时，`Bigtable` 是最高效的解决方案。
    *   `Firestore` 非常适合用于构建客户端 Web 和移动应用。
    *   `Firebase Realtime Database` 适合用户间的实时数据同步，如协作式应用开发所需。
    *   `Memorystore` 是一种完全在内存中运行的数据存储，通常用于缓存频繁访问的数据以加速应用性能。
*   **数据仓库**：`BigQuery` 是 Google 提供的数据仓库服务。
*   **网络**：虚拟私有云（`VPC`）是 GCP 上的本地网络。通过 `VPC Network Peering`，虚拟私有云可相互连接。用户可利用基于互联网的 `Cloud VPN` 在 VPC 和本地网络之间建立受保护连接；或者通过 `Cloud Interconnect` 或 `Peering` 建立专用私有连接。为便于将应用和数据集迁移到其平台，GCP 提供了多样化的选项。`Anthos` 作为混合云部署的替代方案。
*   **数据分析**：Google 在数据分析领域表现卓越。
    *   `Pub/Sub` 用作缓冲，服务于无法应对数据激增的服务。
    *   `Dataproc` 是由 Dataproc 托管的 `Hadoop` 和 `Spark` 实现。
    *   `Dataflow` 是基于 `Apache Beam` 的托管实现。
    *   `Dataprep` 允许不懂代码的用户进行数据处理，其底层利用 `Dataflow`。
    *   用户可使用 `google looker studio` 通过图表、图形等可视化数据。
*   **AI 与 ML**：平台为不同客户群提供 AI 和 ML 服务。`Vertex AI` 为新手提供 `AUTOML` 选项；为经验丰富的用户提供通过 API 进行预测的训练模型；为高级 AI 从业者提供各种选项。
*   **CI/CD 与开发工具**：
    *   `Cloud Build` 支持开发持续集成/持续部署（CI/CD）流水线。
    *   托管在 GCP 上的私有 Git 仓库称为 `Cloud Source Repositories`。
    *   `Artifact Registry` 扩展了 `Container Registry` 的功能，是 Google Cloud 推荐的容器注册表。它为存储和管理语言包及 Docker 容器镜像提供了单一位置。
*   **安全与身份管理**：
    *   `IAM`（Identity and Access Management，身份和访问管理）允许为用户和应用分配角色。
    *   存储在 GCP 中的所有内容默认均已加密。`Cloud Key Management` 让公司能够控制其加密密钥。
    *   `Secret Manager` 可安全存储 API 密钥、密码、证书及其他敏感信息。
*   **运维套件**：`Cloud Operations` 套件包含 Monitoring、Logging、Error Reporting、Trace、Debugger 和 Profiler 功能。
*   **安全命令中心**：`Security Command Center` 向您展示活跃的安全威胁和漏洞，以及合规性违规情况。
*   **基础设施即代码**：`Cloud Deployment Manager` 可帮助自动化 Google Cloud Platform 资源的创建和管理。

# GCP 的层级结构

**资源** 是指在 Google Cloud Platform 上投入使用的任何事物。Google Cloud 中的所有内容都具有清晰的层级结构，类似于父子关系。GCP 遵循的层级结构如 [图 1.11](#ch01.xhtml#fig1-11) 所示：

![](images/Figure_1.11.png)

**图 1.11：GCP 的层级结构**

`Organization` 节点是 GCP 层级的起点，可代表一个组织或公司。组织是文件夹和项目及其各自资源的祖先。应用于组织的访问控制策略适用于其所有关联的项目和资源。

但是，如果像上一节那样使用个人邮箱 ID 创建账号，将无法看到组织。相反，如果使用 Google Workspace 账号登录并创建项目，组织将自动提供。此外，没有组织的情况下，仅有少量的资源管理器功能可用。

