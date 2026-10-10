

# 云图数据库服务

一些云服务商也提供自己的图数据库服务。例如，`Azure Cosmos DB` 支持 LPG，`AWS Neptune` 支持 RDF 和 LPG，`IBM Graph` 支持 LPG，而 `Graph Database on Alibaba Cloud` 支持 LPG。此外，许多第三方 SaaS 图数据库产品也可在云市场上获得。自托管的 `Neo4j` 数据库可部署在包括 `Amazon Web Services`、`Google Cloud Platform` 和 `Microsoft Azure` 在内的主要云平台上。全托管的 `Neo4j (Aura)` 可在 `GCP` 上使用。`TigerGraph Cloud` 可通过 `AWS`、`Azure` 和 `GCP` 的云市场获得。云市场上可用的其他图数据库包括 `GCP` 上的 `JanusGraph`（由 `Google Cloud Bigtable` 支持）和 `AWS`，`AWS`、`GCP` 和 `Azure` 上的 `Dgraph`，`AWS` 和 `Azure` 上的 `Virtuoso`，以及 `AWS` 和 `Azure` 上的 `OrientDB` 等。

## 图计算框架

图计算引擎从图存储中读取图数据，并处理数据以获取查询结果和分析。它们实现全局图计算算法。虽然图数据库通常针对事务进行优化（联机事务处理，即 OLTP），但图计算引擎通常针对批量扫描和处理数据进行优化（联机分析处理，即 OLAP）。有内存/单机图计算引擎，如 `Cassovary`，也有分布式图计算引擎，如 `Apache Giraph`、`Apache Spark – GraphX`、`GraphLab`、`Tencent Plato`、`Katana Graph Engine` 和 `Microsoft Graph Engine`。`Apache TinkerPop` 是一个属性图计算框架，同时适用于图数据库（OLTP）和图分析系统（OLAP），并支持内存和分布式图计算。

## 面向信息处理的机器学习解决方案

有许多用于信息处理的机器学习解决方案和工具包，它们在知识图谱的构建和维护中发挥着重要作用。接下来将讨论一些相关的流行开源 ML 库和工具包。

### Transformers

该代码库包含用于 `Pytorch` 和 `TensorFlow 2.0` 的最先进的预训练通用 NLP 模型（如 `BERT`、`GPT-2`、`RoBERTa`、`XLM`、`DistilBert` 和 `XLNet`）。特别是，它包含语言表征自监督学习方法的实现，如用于在标注数据有限时增强 NER 的 `ELECTRA` 和 `ALBERT`。

### spaCy

它提供工业级的 `Python` NLP，专为生产环境设计。它包含 60 多种语言常见 NLP 任务的预训练模型和管道。它是一个流行的开源库，用于构建信息抽取或自然语言理解应用程序，以及为深度学习预处理文本。

### Spark NLP

它是一个构建在 `Apache Spark ML` 之上的 NLP 库。它拥有 190 多种语言中 1,100 多个预训练管道和模型的丰富集合，并支持许多最先进的 transformers。

### HanLP

Han Language Processing 是一个构建在 `PyTorch` 和 `TensorFlow 2.x` 之上的多语言 NLP 库。它为与知识图谱相关的常见 NLP 任务提供解决方案，包括 NER、句法和语义依存分析、文档分类等。版本 2.1 涵盖英语和中文等 104 种语言。

### Gensim

它是一个用于主题建模、文档索引和相似度检索等 NLP 任务的 `Python` 库。它在内存管理和分布式计算方面高度优化，因此可以处理大规模文本语料库。然而，对于其核心优势之外的其他 NLP 任务，需要利用其他库。

### PyTorch Geometric

它是一个用于几何深度学习的方法库，处理图和其他非规则结构上的深度学习。它包含许多图神经网络变体，包括 `GCN`、图注意力网络（`GAT`）、图循环网络（`GRN`）以及图自编码器/变分自编码器。

### DGL (Deep Graph Library) 和 DGL-KE

`DGL` 是一个实现图神经网络模型的开源库，由 `Amazon Web Services (AWS)` 的研究人员贡献。在 `DGL` 之上，`AWS` 开发了 `DGL-KE`，这是一套用于深度图学习知识嵌入的工具，亚马逊用它来驱动他们自己的知识图谱，包括支持 Alexa 问答服务的那个。`DGL-KE` 在不同的并行计算环境下提供不同的计算优化，从而显著提高了知识嵌入算法的性能。

也有用于信息处理的云 SaaS NLP API。示例包括：

#### AWS 上的 NLP

`Amazon Textract` 可自动从手写和扫描文档的表单和表格中提取文本和数据。`Amazon Comprehend` 是 `AWS` 内置的用于从非结构化数据中抽取信息的工具。用户只需提供少量自己的数据样本，即可训练自定义 ML 模型，以构建用于实体识别和文档分类的定制应用程序。`AWS Marketplace` 上的 `Twinword` 可以识别文本片段之间的距离、关系和相似度。`AWS` 将构建在 `MXNet` 之上的深度学习 NLP 框架 `GluonNLP` 与 `SageMaker` 集成。`AWS` 最近还与 `Hugging Face` 合作，将 `Transformers` 库中的数千个 NLP 模型引入 `Amazon SageMaker`。

#### Google Natural Language API 和 AutoML Natural Language

`Natural Language API` 包含用于 NLU 应用的预训练模型，如情感分析、实体分析、实体情感分析、内容分类和句法分析。`AutoML Natural Language` 是一个无代码工具，用户只需上传自己的训练数据即可训练和测试自定义 ML 模型。

#### Microsoft Azure 知识挖掘解决方案

`Azure Cognitive Search` 不仅是一个搜索工具，还提供 AI 扩充功能，以有意义地索引非结构化数据。`Azure Cognitive Services` 除其他认知 API 外，还包括用于自然语言文本含义预测和信息抽取的 `Language Understanding Intelligence Service (LUIS)`，以及用于情感分析、关键短语提取和语言检测的 `Text Analytics` 服务。这些 API 解决方案提供对预构建模型的访问。或者，用户也可以通过 `Azure Databricks` 或 `Azure HDInsight` 访问 `Spark NLP` 来构建自定义模型，后者提供全托管的 Spark 服务。

## 语义中间件解决方案

语义中间件基于语义标准而非单纯交换数据，在应用程序之间交换信息。它比传统中间件更强大。传统中间件仅基于数据模式使用连接器，而语义连接器则利用推理实现原生互操作性。语义中间件解决方案通常利用机器学习算法从非结构化数据源中提取和处理信息。语义中间件以及企业数据和信息集成解决方案提供商的示例包括：

### Cambridge Semantics 的 Anzo 平台

`Anzo` 构建在 `AnzoGraph DB` 之上，后者是 Cambridge Semantics 自家的图数据库，采用内存 MPP 处理范式，并针对 OLAP 进行了优化。`AnzoGraph DB` 支持 `RDF*`、LPG 和 Cypher。除了 W3C 标准化、知识查询、知识推理、本体管理和元数据管理等标准知识图谱功能外，它还将知识图谱与一套丰富的 AI/ML 工具和图算法集成，用于数据整理、信息抽取、知识图谱补全、知识图谱管理、图遍历、模式匹配、图分析、推荐制定等。结合内置的知识图谱工作流，该平台支持为现代数据集成和数据管理实现数据结构。`Anzo` 平台构成了 `Anzo Smart Data Lake` 解决方案的骨干。该平台还为 `TIBCO Spotfire`、`Tableau` 和 `Microsoft Power BI` 等第三方商业智能工具提供连接。

