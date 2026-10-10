

## 用于数据处理和治理的 AI/ML 工具

### 资源利用与工作负载优化

在资源利用和工作负载/性能优化方面，Informatica CLAIRE 拥有智能优化器，可为大数据工作负载决定最佳引擎，并能根据成本和启发式规则智能地更改 ETL 的连接顺序。NetApp Active IQ 为最佳存储健康状况提供可操作的智能洞察。Datadog 应用 ML 自动分析基础设施和应用程序性能，并检测应用程序和服务的异常错误率、延迟升高和网络问题。Splunk Machine Learning Toolkit 和 Splunk Machine Learning Environment 赋予用户利用机器日志/消息数据将 ML 模型投入运行的能力，并允许对预训练模型进行部分拟合，以便用户利用迁移学习定制自己的应用程序。

### 机器学习目录

机器学习目录可跨多个数据源自动且持续地爬取和索引企业数据资产，以建立目录。它们还可能包含血缘追踪、自然语言查询、ML 推荐和动态敏感数据屏蔽等功能。ML 数据目录市场的供应商包括 Alation、Collibra、Informatica、Oracle、IBM、Talend Data Catalog、erwin Data Catalog 和 Google Cloud Data Catalog 等。一些目录由知识图谱驱动或可搜索知识图谱，例如 Collibra、Informatica、data.world 和 Cambridge Semantics Anzo Catalog。Alation 和 Collibra 是主动数据治理的先驱之一，主动数据治理涵盖数据质量、数据发现、数据安全和治理。

### 数据隐私保护与访问控制

数据隐私保护和访问控制策略是数据治理 2.0 的两个基本要素。AI/ML 算法可帮助检测数据漏洞，并推荐或应用适当的安全策略。自动化数据治理平台（如 Immuta、Privacera 和 BigID）提供 GDPR 合规工具，用于敏感数据识别、数据扩散控制（特别是针对 PII）、数据访问控制/监控和策略执行。Data Capsule 是一种用于自动敏感数据追踪和策略执行的智能范式。在此范式中，数据及其关联策略的组合形成一个胶囊；胶囊经分析程序（如 ETL 和机器学习）处理后，策略会根据分析程序中的数据操作集自动相应更新。生成的更新后策略（残留策略）随后与分析程序的输出相结合，形成一个新的胶囊。通过这种方式，数据隐私策略从一开始就与数据封装在一起，并自动级联到下游数据处理和模型运行中。

许多此类专业解决方案也可在公有云上获取，例如适用于 AWS/Azure/GCP 的 Informatica、AWS 上的 Alation Data Catalog 和 Data Governance、AWS/GCP 上的 Collibra Data Governance and Catalog、AWS/Azure/GCP 上的 Immuta、AWS/Azure 上的 Zaloni’s Arena，以及 AWS/Azure/GCP 上的 Tamr。

公有云提供商（如 AWS、Azure 和 GCP）为其客户提供大量基于云的数据、分析和 AI/ML 服务，这些服务为 AI/ML 辅助的数据管理解决方案提供了构建模块。除了通过云市场提供的第三方托管数据管理解决方案外，公有云平台上还提供许多原生/集成 ML 功能和支持技术，可促进构建用于安全且自动化的数据处理和分析的智能管道，甚至可从原始数据实时获得有用洞察。

[表 8.1](#chap8.xhtml#tab8-1) 总结了前三大公有云平台上的主要原生/集成 ML 能力。这绝不代表这些云平台上用于数据管理的所有 AI/ML 能力的完整列表。其中一些 AI/ML 功能将在下文中更详细地讨论。其他一些将在 [第 5 章](#chap5.xhtml) 中讨论。

**表 8.1.** 主流公有云平台上用于数据管理的主要 ML 能力

![](images/p296.jpg)

### 8.4.1 亚马逊云科技 (AWS) 上用于数据处理和治理的 AI/ML 工具

AWS 拥有令人印象深刻的数据处理和数据治理技术栈。其中许多已启用 AI/ML 或赋能 AI/ML。

#### Amazon SageMaker

Amazon SageMaker 是 AWS 的全托管机器学习服务，可帮助用户完成端到端的 ML 工作流，包括数据标注、数据清洗、特征管理、模型训练、模型验证、模型部署、模型监控、持续集成和持续交付 (CI/CD)。它还提供 AutoML 功能，可自动探索不同解决方案以找到最佳模型。此外，SageMaker 还为常见用例提供预置的 ML 解决方案，支持一键部署。

#### Amazon Kendra

Amazon Kendra 是一款基于 ML 的企业搜索工具，用于搜索跨越多样化的内部/外部以及本地/云端数据源的文档中的数据和信息。查询可通过自然语言搜索输入执行。Kendra 可获取配置数据源内的文档以及用户提供的可选常见问题解答 (FAQ) 集，然后使用智能 ML 算法为这些文档和 FAQ 构建搜索索引。NLP 和 NLU 不仅用于语义查询，还用于帮助提取和索引这些文档之间的关键词、概念和关系。用户也有灵活性创建自己的自定义索引。所有这些功能使 Kendra 能够综合考虑内容、用户上下文和查询输入，实现智能搜索。它不仅具有高度可扩展性并与其他 AWS 服务紧密集成，搜索结果还能考虑组织的安全模型，仅向用户交付适当安全级别的内容。

#### Amazon Macie

针对 PII 识别和去标识化，Amazon Macie 是 AWS 提供的全托管数据安全和数据隐私服务。它允许用户定义一组标准，通过确定性方法和/或智能 AI/ML 算法检测敏感数据。发现结果可发送至下游流程（如 `AWS Lambda` 和 `AWS Step Functions`），以进行自动修复，包括去标识化。Macie 可扫描 AWS 简单云存储 (S3) 存储桶中的数据项。对于其他 AWS 存储中的数据项，用户可将其临时移至 S3 进行扫描。可通过 AWS 管理控制台、AWS 命令行工具（`AWS CLI` 和 `AWS Tools for PowerShell`）、AWS SDK 和 Amazon Macie REST API 访问 Macie。

#### Amazon Connect AI/ML 功能

对于通常需要实时信息和分析的联络中心活动，Amazon Connect 提供了多项 AI/ML 功能，例如 Connect Wisdom（预览版），它接收实时客户输入（如语音、聊天），在知识库中搜索内容，并提供相关推荐/答案，以实现更快、更有效的客户服务。Connect Customer Profiles 可快速从多个来源汇总统一的客户档案信息，使座席拥有关于客户的所有信息，从而实时提供更好的个性化服务。Connect Contact Lens 提供由 ML 驱动的实时联络中心分析，分析联系记录以标准化并确保服务质量、预防冲突、促进客户服务培训，并自动生成警报以升级客户问题。Connect Tasks 是一款工具，可帮助分配、优先处理和跟踪客户服务任务，并根据可用性和专业知识管理后续行动。Connect Voice ID（预览版）使用声纹进行实时客户身份验证，增加了一层安全保护。

#### 其他适用的 AWS AI/ML 服务

其他适用的 AWS AI/ML 和 AI/ML 赋能服务包括例如：

*   Amazon Textract，用于从扫描文档中提取数据，
*   Amazon Comprehend，用于在文本中发现洞察和关系，
*   AWS Lake Formation FindMatches，用于记录匹配，

