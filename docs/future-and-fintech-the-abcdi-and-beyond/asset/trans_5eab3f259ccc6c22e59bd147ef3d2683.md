

## 8.4.2 用于 Azure 上数据处理和治理的 AI/ML 工具

微软最近推出了 **Azure Purview**（预览版），这是其统一的数据治理服务，用于管理跨本地和云端系统的企业数据。它是 **Azure Data Catalog** 的扩展和增强版本。它可以提供客户数据资产的整体、最新视图，并具备智能功能，包括自动化数据发现、敏感数据分类和端到端数据血缘。它利用 **Microsoft Information Protection** 背后的 AI/ML 技术，帮助用户识别敏感信息、对其进行分类，并实施适当的保护策略。它还可以结合业务词汇表/分类法来增强数据索引和搜索。微软应用 Purview 来满足其自身对 **GDPR** 和 **加州消费者隐私法案 (CCPA)** 等数据隐私法规的合规要求，并且也可以在客户端利用它来将合规风险降至最低。

Azure 还为用户提供了多种开发 ML 模型的选项：**Azure Machine Learning**、**Azure Cognitive Services**、**Azure SQL Managed Instance Machine Learning Services**、**Azure Synapse Analytics 中的机器学习**、**Azure SQL Edge 中结合 ONNX 的机器学习和 AI**，以及 **Azure Databricks**，它们各自具有特定的功能和用途。特别是，**Azure Cognitive Services** 包含用于 **OCR**（**表单识别器**）、语音数据（**语音服务**）、文本数据（**翻译**、**文本分析**、**语言理解**、**问答生成**）和异常检测（**异常检测器**）等的预训练 ML 模型。

## 8.4.3 用于 Google Cloud Platform (GCP) 上数据处理和治理的 AI/ML 工具

**Cloud DLP** 是 GCP 的全托管服务，用于敏感数据发现、分类和保护。除了确定性规则外，**Cloud DLP** 还采用 AI/ML 算法，从 **Cloud Storage/Datastore/BigQuery** 中的数据资产识别敏感信息、对文本和图像进行匿名化和转换，并提供风险分析以衡量敏感数据保护情况。与其他一些云平台一样，自动检测几乎可以实时进行，用户可以构建工作流，在将数据移动到存储桶之前扫描其敏感性，以防止 **PII** 泄露。

支持 AI/ML 的 **Google Cloud Data Catalog** 是数据治理的有用工具。它由智能 **Cloud Search** 提供支持，并与 **Cloud DLP** 交互，利用 **DLP** 强大的自动标记机制自动识别敏感数据。它可以自动编目 **BigQuery**、**Cloud Storage**、**Cloud Bigtable** 和 **Google Sheets** 中的数据资产，以及 **Pub/Sub** 中的主题。还可以创建和使用自定义标签进行数据搜索。

**Cloud Dataprep (Trifacta)** 是一项无服务器、可扩展且智能的数据清洗服务。它使用户能够以可视化方式探索、清理和准备结构化和非结构化数据，以供下游分析、商业智能和 ML 使用。除了确定性数据质量规则外，它还使用 ML 来推导概率数据质量规则，以评估数据是否适合特定用途。**Cloud Dataprep** 还可以根据所选数据推断用户的数据转换意图，并自动生成一组按排名排序的建议和模式以匹配所选内容。

全托管的 **Google Cloud AI Platform** 为用户提供了一个强大的工具箱，用于开发用于数据管理等目的的自有 ML 模型。与 **Amazon SageMaker** 一样，它也提供端到端 ML 工作流的全覆盖。它利用其他 Google Cloud 服务，例如用于标记训练数据的 **Data Labeling Service**、用于数据准备的 **BigQuery**、用于数据清洗的 **Dataprep**、托管 **Jupyter Notebook** 和用于 ML 模型训练的 **AI Platform Training**、用于模型验证的 **AI Explanations** 和 **What-If Tool**、用于模型服务的 **AI Platform Prediction**、用于无代码自动模型选择的 **AutoML**、用于模型性能监控的 **Continuous evaluation**、用于 **CI/CD** 的 **MLOps tools**，以及用于 **TensorFlow** 实例的企业级支持和托管服务 **TensorFlow Enterprise**。**Google Contact Center AI** 和 **Document AI** 套件也提供了可潜在用于数据管理的工具。此外，**BigQuery ML** 允许用户使用 **结构化查询语言 (SQL)** 创建和评估各种统计和 ML 模型并进行模型预测。

在 2021 年 5 月的 **Google Data Cloud Summit** 上，Google 宣布了 **Dataplex**（预览版），这是一个智能数据结构，用于在元数据、智能、生命周期、治理和安全方面实现统一数据管理。Google 的 AI/ML 能力被用于自动化数据发现、元数据生成/丰富、数据生命周期管理和数据质量保证工作流。此外，**BigQuery** 现在结合其“内置”机器学习能力引入了数据异常检测。

## 8.4.4 集成数据、分析和 ML 平台

除了主要的公共云服务外，集成数据、分析和 ML 平台（如 **Databricks**、**Snowflake+Datarobot**、**Dataiku**、**Alteryx**、**SAS** 和 **MathWorks**）允许用户利用数据准备、ML 模型训练和 AI 辅助自动化方面的丰富功能，构建自己的定制化智能数据管理解决方案和管道。

许多通用 ML 算法可以作为定制 AI/ML 数据管理解决方案的构建模块。例如，流行的 ML 编程库/模块（如 **Scikit-Learn**、**Keras**、**Caffe**、**PyTorch**、**MXNet** 和 **Tensorflow**）实现了各种各样的 ML 算法，包括数十种半监督、弱监督和迁移学习算法。还有主动学习库，如 **ModAL**、**Libact** 和 **Alipy**。你可以在 **Python** 的 **PyPI 存储库** 中找到其他 ML 包。下面列出了一些专业 ML 包和插件的示例：

*   **Snorkel** 利用标注函数 —— 能够结合领域特定规则、逻辑和启发式方法的代码片段 —— 以编程方式为未标注实例分配标签。
*   **OpenAI API** 是 **GPT-2** 和 **GPT-3** 语言 API 的开发者；**OpenAI Gym** 是一个用于开发和比较强化学习算法的工具包。
*   **Synthetic Data Vault** 包含用于深度学习算法（如 **变分自编码器 (VAE)** 和 **生成对抗网络 (GAN)**）的开源库，用于生成和评估合成数据，以及用于合成数据生成的强大聚类算法 **高斯混合模型 (GMM)**。
*   **Dataiku** 提供 **Active Learning Plugin**，通过高效的数据标注流程提高数据质量，而结合 **Dataiku** 的深度学习图像插件的迁移学习也有助于加速计算机视觉领域的学习。

## 8.5 案例研究：Informatica 如何利用 AI/ML 改进数据管理

**Informatica** 是一家企业云数据管理和数据集成解决方案提供商。它是在应用 AI/ML 以增强企业数据管理中的自动化和智能化方面的行业领导者。

