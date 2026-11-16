
用量统计。数据科学家、分析师和数据工程师使用此目录来发现、理解和访问与其项目相关的数据。

> **提示** 建立共享的集中式数据湖，以促进公司范围内的治理、协作和无缝数据访问。

![](img/1490b3cf638678afadc8c48abc1698d5_309_0.png)

**图 13.14：** 数据管理架构

### 数据转换

数据转换是将原始数据转换为 ML 模型可直接使用的格式和结构的过程。它包括数据清洗、数据准备、特征转换、数据归一化、降维等等。

### 数据版本控制

数据版本控制是为数据集分配版本并跟踪模型中使用的数据的任何更改的过程。它可帮助您在必要时恢复到旧版本，并且您可以跟踪不同模型训练实验中使用的数据集的血缘。这有助于提升 ML 实验的可追溯性和可重复性。

### 数据科学试验平台

如图 13.15 所示，数据科学或机器学习试验平台应提供全面的工具和服务，帮助数据科学家和团队为其项目开展多个单人或团队协作试验。请考虑以下因素：

| 功能 | 描述 | 示例工具/服务 |
|---|---|---|
| 数据查询和分析 | 团队必须能够探索数据、分析数据、执行 SQL 分析或数据转换，并可视化结果。例如，使用 Amazon Athena 通过 SQL 查询数据湖中的数据。 | Amazon Athena<br>Google BigQuery ML<br>Dataflow<br>Azure HDInsight、Azure Data Lake Analytics |
| 代码编写 | 团队应能够使用 IDE 和笔记本编写和编辑代码。例如，Amazon SageMaker Notebook Instance 和 SageMaker Studio 可用于代码编写、数据处理、模型训练和试验。 | Amazon SageMaker Notebook、<br>SageMaker Studio<br>AI Platform<br>Notebook<br>Azure ML Studio |
| 数据处理 | 这包括用于数据预处理和转换的工具，例如数据清洗、数据整理和特征工程。例如，使用 Amazon Data Wrangler 进行数据导入、转换、可视化和分析。Amazon SageMaker Processing 可用于大规模数据处理，包括与 Apache Spark 和 scikit-learn 集成。 | Amazon Data Wrangler、SageMaker Processing<br>Google AI Hub<br>Azure Machine Learning Studio |
| 预训练 | 预训练是在大型未标注数据集上训练模型的过程。它有助于使用非监督或半监督学习从数据中识别一般模式和特征。随后，可在较小的标注数据子集上使用该模型，为特定任务开发更好的预测。 | |
| 自动触发器 | 在机器学习试验项目中设置事件或触发器，以自动化各种步骤。例如，当有新数据可用或模型已更新时，它们可以触发另一个工作流以在生产环境中部署模型，或发起对训练模型的评估。 | |
| 特征存储 | 启用跨团队共享常用特征，用于模型训练和推理。 | Amazon SageMaker Feature Store<br>Vertex AI Feature Store<br>Azure Machine Learning |
| 模型训练和调优 | 包括使用各种技术和算法进行训练和测试、评估模型以及进行超参数调优的能力。例如，使用 Amazon SageMaker 训练/调优服务。 | Amazon SageMaker Training/Tuning Service<br>Google Cloud AutoML<br>Vertex AI<br>Azure ML Studio<br>Azure Automated Machine Learning |
| 模型评估 | 在机器学习试验平台中，模型评估是关键步骤，可帮助您比较不同试验、进行超参数调优，并选择最适合部署的模型。根据任务类型和问题领域，使用准确率、精确率、F1 分数和召回率等指标比较不同训练模型的性能。模型评估决定了模型在未见数据上的泛化能力及其解决问题的能力。 | Amazon SageMaker Training/Tuning Service<br>Google Cloud AutoML<br>Vertex AI<br>Azure ML Studio<br>Azure Automated Machine Learning |
| 容器化 | 能够将模型和工作流构建、测试和部署为容器化应用程序或服务。例如，使用 Amazon ECR 存储训练、处理和推理容器。 | Amazon ECR<br>Kubernetes Engine<br>Azure 容器注册表 |
| 源代码控制 | 使用 Git 等源代码控制系统管理代码，以便跟踪更改并实现团队成员之间的协作，确保可重复性。例如，Artifacts 仓库是用于管理库程序包和镜像公共库站点的私有程序包仓库。 | Git |
| 数据科学库访问 | 提供对 NumPy、Pandas、scikit-learn、PyTorch 和 TensorFlow 等数据科学库的便捷访问，以便轻松进行开发和试验。 | NumPy、Pandas、scikit-learn、PyTorch、TensorFlow |
| 自助式目录 | 使用 ML 工具、服务和产品，使数据科学家和团队成员能够快速访问其 ML 需求。 | 自助式目录 |
| 实现自助式目录 | 开发各种 ML 工具、服务和产品的自助式目录，以便其他团队成员（例如数据科学家）可以通过自助式门户预配 SageMaker Studio 或 Canvas 等工具。 | 实现自助式目录 |

## 混合和边缘计算

混合计算和边缘计算是机器学习领域中两种不同的计算方法，可用于兼顾两者的优势（见图 13.16）。

### 混合计算场景

在混合计算中，一些典型做法如下：

![](img/1490b3cf638678afadc8c48abc1698d5_312_0.png)

**图 13.15：** ML 试验平台的组件

- 在云中部署模型以提高可扩展性和性能，然后在边缘部署某些模型以提高安全性。
- 您可以在本地基础架构中进行数据存储、数据预处理和模型训练，并将分布式处理、大规模训练和模型托管卸载到云中。
- 混合计算可帮助您进行资源优化、成本优化和数据治理。

### 边缘计算

边缘计算的一些注意事项如下：

- > 它将数据处理和模型训练带到更靠近数据生成点或数据源的边缘设备（例如 IoT 设备、传感器或边缘服务器）。
- > 对于需要以极低延迟、降低带宽并提高安全性和隐私性实时处理数据的用例，它非常有用。

> 注意 混合计算和边缘计算在远程医疗监测、自动驾驶汽车和工业 IoT 等用例中尤其有用。

### 为边缘设计模型

为边缘设计模型时，需要考虑一些特定因素，例如以下几点：

- > **模型大小：** 模型应足够小，以适配边缘设备。
- > **模型延迟：** 模型延迟应足够低，以满足应用程序的要求。
- > **模型准确性：** 模型应足够准确，以满足应用程序的要求。

为满足这些要求，您可能需要采用量化和模型剪枝等模型压缩技术来减小模型大小。此外，模型应设计为可在离线或间歇连接场景下运行。

![](img/1490b3cf638678afadc8c48abc1698d5_313_0.png)

**图 13.16：** 机器学习中的混合和边缘计算

- > **数据同步、延迟和网络连接：** 在混合和边缘计算场景中，数据同步延迟和网络
