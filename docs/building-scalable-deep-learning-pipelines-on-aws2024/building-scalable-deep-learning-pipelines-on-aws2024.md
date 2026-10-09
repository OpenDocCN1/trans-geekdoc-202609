# AWS 可扩展深度学习流水线构建指南























*献给我的经理们，他们赋予我有意义的项目，磨练了我的数据科学技能。*

*献给我的数据科学同行，感谢他们接受了我的第一本书，《使用 PySpark 进行分布式机器学习：轻松从 Pandas 和 Scikit-Learn 迁移》。*





































ix

# 作者简介

![](img/1c89d4486f90c87568fa6a42d46ae02a_9_0.png)

**Abdelaziz Testas**，博士，是一位经验丰富的数据科学家，在数据分析和机器学习领域拥有十余年经验。他在英格兰利兹大学获得经济学博士学位，并在苏格兰格拉斯哥大学获得同一领域的硕士学位。此外，他还在美国获得了多项计算机科学和数据科学认证。

在过去十年中，Abdelaziz 担任尼尔森（Nielsen）的首席数据科学家，在增强公司的受众测量能力方面发挥了关键作用。他在规划、启动和执行端到端的数据科学项目，以及开发推动尼尔森数字广告和内容评级产品进步的方法论方面起到了至关重要的作用。他在媒体测量和数据科学方面的专业知识推动了创新解决方案的创建。

最近，Abdelaziz 转型进入公共部门，加入了加利福尼亚州医疗准入与信息部（HCAI）。在新角色中，他利用其编码和数据科学领导能力产生有意义的影响，支持 HCAI 确保所有加利福尼亚人都能享有优质、公平和可负担医疗服务的使命。

Abdelaziz 还是由 Apress 于 2023 年 11 月出版的《*使用 PySpark 进行分布式机器学习：从 Pandas 和 Scikit-Learn 轻松迁移*》一书的作者。

# 技术审稿人简介

![](img/1c89d4486f90c87568fa6a42d46ae02a_10_0.png)

Abhik Choudhury 是一位高级分析管理顾问和数据科学家，在设计和实施跨行业组织的可扩展数据解决方案方面拥有 12 年经验。在职业生涯中，他建立了对 AI/ML、云计算、数据库管理系统、数据建模、ETL 流程和大数据技术的深刻理解。他的专长在于领导跨职能团队，并与各层级的利益相关者合作，以推动纵向制药和医疗索赔以及药品批发分销领域的数据驱动决策。Abhik 的技术技能涵盖广泛的领域，包括架构云解决方案、商业智能、数据可视化、机器学习算法、概率与统计、数据分析、数据仓库、数据质量、线性代数、云计算、大数据、数据治理和关系数据库。Abhik 具有使用 Python、R、SQL、UNIX 和 DAX 等语言以及 Scikit-Learn、Pandas、SciPy、NumPy、Matplotlib、XGBoost、NLTK、ggplot2、dplyr 和 tidyverse 等包的实际操作经验。此外，他还有使用 Google Cloud Platform、IBM Watson、Microsoft PowerBI、Jupyter Notebook、GIT、Tensor、PyTorch、MySQL、SAP BusinessObjects、IBM DB2、SAP HANA、Hadoop 和 Microsoft Excel 等工具和技术的工作经验。Abhik 于 2022 年 12 月在美国佐治亚理工学院完成了分析学硕士学位。在此之前，他于 2011 年 5 月从印度西孟加拉邦理工大学获得电子与通信工程 Bachelor of Technology (B.Tech.) 学位。他已获得 IBM DB2 数据库开发人员、SAP BusinessObjects BI 工具开发人员和 Google Cloud 专业数据工程师的认证。自 2022 年 8 月起，Abhik 担任美国 IBM 公司的高级分析管理顾问，负责为医疗和制药客户设计和实施可扩展的数据架构解决方案。他还使用 Google Cloud Platform 在架构、构建和管理法律和合规数据平台方面发挥了关键作用。此外，他领导了有益的数据架构技术和工具的调查与适应，以及运营数据存储企业数据模型和策略的开发与实施。此前，作为美国 IBM 的高级数据科学家（2021 年 9 月至 2022 年 8 月），Abhik 利用 Python 清洗和分析原始数据，基于药品批发分销患者数据预测阿片类药物处方者。他还使用 R 和 Tableau 对大型客户数据集进行了购物篮分析和关联规则挖掘。此外，他执行了探索性数据分析，开发了预测员工流失率的机器学习模型，进行了客户细分分析，并进行了预测股价的时间序列分析。在那之前，作为美国 IBM 的高级商业智能工程师（2019 年 7 月至 2021 年 8 月），Abhik 创建了可扩展的数据模型，构建了高效的 ETL 管道，使用 BigQuery ML 开发回归和分类模型，并在 Vertex AI 中设计了基于 Tensor 的机器学习模型。Abhik 还在部署库存优化应用程序和在 PowerBI 中创建仪表板方面发挥了重要作用。在 2012 年 3 月至 2018 年 7 月担任 IBM 商业智能分析师期间，Abhik 使用 SAP BusinessObjects BI 报告工具在供应链范围内实施分析报告。Abhik 还致力于构建报告和 universe，并利用 SQL、数据仓库程序、Tableau 和其他可视化工具进行数据智能。

# 致谢

我要向所有为本书创作做出贡献的 Apress 人员表示衷心的感谢。特别是，我要感谢执行编辑 Celestin John，他给了我写这本第二本书以及我的第一本书《*使用 PySpark 进行分布式机器学习：从 Pandas 和 Scikit-Learn 轻松迁移*》的机会。Celestin 宝贵的指导和支持在两个项目期间都起到了关键作用。

特别感谢协调编辑 Kripa Joseph，他勤勉的监督确保了每个细节都得到仔细处理。我也感谢开发编辑 Laura Berendson，她凭借专业知识将内容塑造为其最终形式。

我要感谢技术审稿人 Abhik Choudhury，他彻底的审阅和专业知识极大地增强了所呈现材料的技术准确性和深度。

非常感谢 Apress 的整个团队，他们对卓越的承诺和协作精神使出版过程成为一次有益的体验。你们的共同努力对这本书的诞生起到了至关重要的作用，我对你们的贡献深表感激。

# 引言

随着数据的指数级增长和对复杂 AI 应用需求的增加，传统的本地基础设施通常无法提供现代深度学习工作流所需的计算能力和可扩展性。因此，随着组织寻求为其机器学习任务提供可扩展且高效的解决方案，基于云的深度学习变得越来越重要。通过利用云服务的灵活性、可扩展性和成本效益，组织可以克服硬件限制，并加速先进机器学习算法的开发和部署。

将 PySpark、PyTorch、TensorFlow 和 Apache Airflow 与 Amazon Web Services (AWS) 集成，包括 Amazon Simple Storage Service (S3) 和 Amazon Elastic Compute Cloud (EC2)，为大规模构建和部署深度学习模型提供了强大的工具。AWS 作为市场份额最大的最流行云服务提供商，为高效执行这些任务提供了坚实的基础架构。

本书专为希望构建可扩展 AWS 深度学习管道或希望增强将云服务与深度学习框架集成技能的数据科学家、机器学习工程师和 AI 从业者设计。它提供了使用 PySpark、PyTorch、TensorFlow 和 Airflow 的组合在 AWS 上构建深度学习管道的综合指南。我们展示了整个工作流，从使用 S3 和 PySpark 进行数据摄取和预处理开始，到使用 Apache Airflow 安排模型运行结束。管道中的每个阶段都被剖析，提供清晰的解释、动手示例以及来自实际应用的经验见解。




# 引言

该流水线具有多项优势。首先，它利用 PySpark 在大规模数据处理中的可扩展性以及 EC2 实例的算力来进行模型训练，确保资源的高效利用。其次，基于云的方法提供了灵活性，允许根据工作负载需求进行资源扩展，并轻松调配资源。第三，PySpark 和 Apache Airflow 凭借其分布式计算能力简化了数据处理任务，实现了高效的预处理、转换和工作流编排。第四，Amazon S3 的大容量存储促进了不间断的数据存储和检索，支持海量数据集的处理。最后，预处理（PySpark）、模型开发、训练和评估（PyTorch、TensorFlow）、模型编排（Apache Airflow）、存储（S3）以及计算（EC2）之间的关注点分离简化了架构并增强了模块化，便于简化的工作流管理。

本书还研究了 JupyterLab 和 Databricks，以进一步增强开发和部署过程。JupyterLab 提供了一个理想的交互式计算环境，用于数据探索和原型开发，而 Databricks 则提供了一个用于大数据处理和高级分析的协作平台。

这些云服务与数据科学工具的集成促进了端到端的工作流，推动了深度学习流水线各环节间的协作与效率。

本书共分为十章。第 1 章向读者介绍深度学习流水线的基础知识，强调此类框架中可扩展性的重要性。此外，还提供了 AWS 作为可扩展性平台的概述，为后续章节深入探讨在 AWS 云上设置、配置和优化深度学习环境奠定了基础。

第 2 章指导读者配置专为深度学习任务定制的 AWS 服务，建立开发环境，并保护 AWS 环境以服务于深度学习流水线。本章是读者有效利用 AWS 资源构建可扩展深度学习解决方案的关键起点。

第 3 章专注于使用 PySpark 进行数据预处理和特征工程，而第 4 章和第 5 章探索使用 PyTorch 和 TensorFlow 进行回归任务的深度学习，涵盖了框架介绍、模型构建及训练技术。第 6 章和第 7 章则将重点转向使用 PyTorch 和 TensorFlow 进行分类任务的深度学习。

在第 8 章中，我们展示了如何使用 Apache Airflow 构建可扩展的数据处理流水线。我们创建完整的 AWS 工作流，包括使用 PySpark 预处理数据、使用 PyTorch 和 TensorFlow 开发深度学习模型，以及使用 Airflow 运行代码。

第 9 章展示了增强深度学习模型性能的先进技术，包括处理过拟合和欠拟合、实现正则化技术、早停策略以及模型微调，以提高准确性和效率。

最后，在第 10 章中，我们通过展示如何使用 Amazon Managed Workflows for Apache Airflow (MWAA) 部署深度学习模型，深入探讨了部署过程，并提供了关于此工作流编排托管选项的见解。

综合来看，这些章节提供了在 AWS 上构建端到端可扩展深度学习流水线的全面指南，涵盖从数据预处理、模型训练到生产环境中的部署和监控。本书是对我们首本书 *《使用 PySpark 进行分布式机器学习：从 Pandas 和 Scikit-Learn 轻松迁移》*（Apress，2023 年 11 月）的补充，该书专注于从 Pandas 和 Scikit-Learn 等小规模工具向 PySpark 的过渡。虽然第一本书强调可扩展的机器学习工作流，但本书在此基础上扩展，重点在于在云中构建可扩展的深度学习工作流。两本书之间存在少量重叠，特别是在使用 Pima 数据集进行糖尿病分类方面，我们在本书中通过 PyTorch 和 TensorFlow 的视角重新审视了这一部分。这使我们能够展示这些平台为深度学习工作流提供的增强灵活性和可扩展性。

# 第 1 章
### AWS 上可扩展深度学习流水线的概述

随着数据量的激增和对复杂 AI 应用需求的增加，传统本地基础设施往往无法提供现代深度学习工作流所需的计算能力和可扩展性。因此，基于云的深度学习变得越来越重要。

在本章中，我们将介绍一种有效利用这些基于云解决方案的深度学习流水线，通过整合关键技术和实现服务。该流水线将在全书中详细阐述，它结合了流行的大数据框架——PySpark、PyTorch、TensorFlow 和 Apache Airflow（作为独立部署、Docker 容器化设置或通过 Amazon Managed Workflows for Apache Airflow (MWAA) 提供的托管服务）——与 Amazon Web Services (AWS) 云解决方案，包括 Amazon Simple Storage Service (S3) 和 Amazon Elastic Compute Cloud (EC2)。AWS 作为拥有最大市场份额的领先云服务提供商，为高效执行这些任务提供了强大的基础设施。

本章的第一部分详细考察了 AWS 上此深度学习工作流的主要组件。它涵盖了整个流水线，从使用 S3 进行数据摄入到使用 Apache Airflow 调度模型运行。后续章节将深入探讨流水线的每个阶段，提供清晰的解释、实战示例以及来自实际应用的见解。

### AWS 上深度学习工作流的组件

图 1-1 展示了一个利用 Amazon Web Services (AWS) 的强大功能来处理大规模数据处理、模型训练、评估和部署任务的综合深度学习流水线。该流水线的核心是 Amazon S3，作为集中式数据源，用于存储原始数据集、预处理数据和模型工件。数据预处理由 PySpark 支持，使存储在 S3 中的大数据集的分布式数据处理成为可能。该流水线利用 PyTorch 和 TensorFlow 构建和训练深度学习模型，利用它们的灵活性和可扩展性。Amazon EC2 实例为模型训练提供必要的计算资源，确保云资源的高效利用。Apache Airflow，无论是作为独立部署、Docker 容器化设置还是通过 Amazon MWAA 提供的托管服务，都负责将训练好的模型编排部署到生产环境，简化部署过程并确保任务的顺利执行。

让我们详细分解该图表，从数据源开始。

![](img/1c89d4486f90c87568fa6a42d46ae02a_19_0.png)
*图 1-1. AWS 上深度学习工作流的组件*

### 数据源 (S3)

这代表数据源自 Amazon S3 的初始点，S3 是由 AWS 提供的基于云的存储服务。S3 通常用于存储各种类型的数据，包括原始数据集、预处理数据和模型检查点（如权重）。存储在 S3 中的数据可以被流水线中的其他组件访问和利用，包括数据预处理、模型训练、模型评估、模型部署以及监控和维护。

S3 中的源数据可以复制到 EC2 上的本地目录，然后输入深度学习模型，或者作为流水线的一部分进行复制，这意味着从 S3 检索数据并将其集成到机器学习 (ML) 流水线的各个阶段的过程是自动化的，以提高效率和可扩展性。

以下是两个示例（使用 AWS 命令行界面 (CLI) 配合 subprocess 和 Boto3），说明如何将名为 “TLSA_stock.csv” 的 CSV 文件（将在第 4 章和第 5 章中分别用于使用 PyTorch 和 TensorFlow 预测特斯拉股票价格）从名为 “instance1bucket” 的 S3 桶复制到 EC2 上名为 “/home/ubuntu/airflow/dags” 的本地目录。

使用带有 subprocess 的 AWS CLI：

```python
[In]: import subprocess

[In]: try:
    subprocess.run([
        "aws", "s3", "cp",
        "s3://instance1bucket/TLSA_stock.csv",
        "/home/ubuntu/airflow/dags/"
    ], check=True)
    print("Download successful.")
except subprocess.CalledProcessError as e:
    print(f"Error occurred: {e}")

[Out]: Download successful.
```

这段代码利用 Python 中的 subprocess 模块通过 AWS 命令行界面 (CLI) 将文件 “TLSA_stock.csv” 从 S3 桶 “instance1bucket” 复制到本地目录


在 EC2 实例上的 `"/home/ubuntu/airflow/dags/"` 目录。`subprocess.run()` 函数使用指定的源路径和目标路径执行 AWS CLI 命令 `"aws s3 cp"`。

try/except 块用于处理命令执行期间可能出现的潜在错误。如果命令成功，try 块会打印 `"Download successful."`。如果命令失败并引发 `subprocess.CalledProcessError`，except 块会捕获该错误并打印一条指示发生错误的消息，同时附带错误详情。

`subprocess.run()` 中的 `check=True` 参数确保如果命令返回非零退出状态，则引发 `CalledProcessError`，从而触发 except 块。在此示例中，输出表明文件已成功从 S3 存储桶下载到本地目录。

运行此代码后，我们可以使用标准文件系统命令（例如 Linux/MacOS 中的 `'ls'`）来检查文件是否存在于该目录中：

```
[In]: ls /home/ubuntu/airflow/dags/
```

使用 Boto3：

```
[In]: import boto3
```

```
[In]: try:
    s3_client = boto3.client('s3')
    bucket_name = 'instance1bucket'
    key = 'TSLA_stock.csv'
    local_path = '/home/ubuntu/airflow/dags/TSLA_stock.csv'
    s3_client.download_file(bucket_name, key, local_path)
    print("Download successful.")
except Exception as e:
    print(f"An error occurred: {e}")
```

```
[Out]: Download successful.
```

在此代码中，使用 Boto3（Python 的官方 AWS SDK（软件开发工具包））与 Amazon S3 服务进行交互。使用 `s3_client.download_file()` 方法将文件 “TSLA_stock.csv” 从 S3 存储桶 “instance1bucket” 下载到 EC2 实例上的本地目录 “/home/ubuntu/airflow/dags/”。运行此代码后，文件 “TSLA_stock.csv” 应出现在指定的本地目录中。

将文件从目录复制到 S3 存储桶的过程，本质上是将文件从 S3 复制到目录过程的逆过程。

使用 subprocess 调用 AWS CLI：

```python
[In]: import subprocess

[In]: try:
         subprocess.run([
            "aws", "s3", "cp",
            "/home/ubuntu/airflow/dags/TSLA_stock.csv",
            "s3://instance1bucket/"
            ], check=True)
         print("File uploaded successfully.")
     except Exception as e:
         print(f"An error occurred: {e}")
```
[Out]: File uploaded successfully.

在此代码中，与从 S3 下载的代码相比，我们反转了源路径和目标路径的顺序。

使用 Boto3：

```python
[In]: import boto3

[In]: try:
         s3_client = boto3.client('s3')
         bucket_name = 'instance1bucket'
         key = 'TSLA_stock.csv'
         local_path = '/home/ubuntu/airflow/dags/TSLA_stock.csv'
         s3_client.upload_file(local_path, bucket_name, key)
         print("File uploaded successfully.")
     except Exception as e:
         print(f"An error occurred: {e}")

[Out]: File uploaded successfully.
```

在此代码中，与从 S3 下载的代码相比，我们反转了参数的顺序。换句话说，对于下载，参数为

s3_client.download_file(bucket_name, key, local_path)

对于上传，参数为

s3_client.upload_file(local_path, bucket_name, key)

值得注意的是，如果目标位置（本例中为 S3 存储桶）中已经存在该文件，并且我们尝试上传具有相同键（文件名）的文件，通常会用新文件覆盖现有文件。

## 数据预处理 (PySpark)

一旦按照上述步骤从 S3 检索到数据，它将使用 PySpark 进行预处理。PySpark 是一个分布式数据处理框架，能够对大型数据集进行高效的数据清洗、转换和特征工程。

利用 PySpark 进行预处理任务相比传统库如 Pandas 和 Scikit-Learn 具有独特的优势。首先，其分布式特性使 PySpark 在处理大数据任务时，相较于单节点处理工具具有卓越的扩展性和性能。其次，通过利用 PySpark 的分布式处理能力，预处理任务可以在多个节点上并行化，从而减少处理时间并实现对大规模数据集的高效处理。此外，PySpark 与其他机器学习流水线组件无缝集成，促进了从数据摄取到模型部署的一致且简化的工作流。

在 *《Distributed Machine Learning with PySpark: Migrating Effortlessly from Pandas and Scikit-Learn》*（Apres，2023 年 11 月）中，我们展示了从 Pandas 和 Scikit-Learn 等小数据库过渡到 PySpark 可以相对简单。虽然 Pandas 和 Scikit-Learn 主要设计用于小数据处理和分析，但在许多情况下，由于语法相似性，过渡变得更加容易。PySpark 提供了类似 Pandas 和 Scikit-Learn 的功能，包括数据预处理和特征工程。PySpark 中这些熟悉功能的存在，使习惯了使用 Pandas 和 Scikit-Learn 的数据科学家能够更顺畅地过渡。

在本节中，我们提供了一个使用 PySpark 创建 DataFrame 的简单示例，随后在 EC2 实例上打印该 DataFrame，作为其功能初步介绍。在第 3 章中，我们将深入探讨使用 PySpark 的数据准备技术。这包括更高级的主题，如数据探索、预处理、特征工程，以及为 PyTorch 和 TensorFlow 格式化数据：

```
[In]: from pyspark.sql import SparkSession
```

```
[In]: try:
    spark = (SparkSession.builder
        .appName("TacosDataFrame")
        .getOrCreate())
    data = [("Taco 1", "Beef", 2.50),
        ("Taco 2", "Chicken", 2.00),
        ("Taco 3", "Vegetarian", 2.00),
        ("Taco 4", "Fish", 3.00)]
    schema = ["Taco Name", "Type", "Price"]
    tacos_df = spark.createDataFrame(data, schema)

    # Cache the DataFrame to optimize performance
    tacos_df.cache()

    tacos_df.show()
except Exception as e:
    print(f"An error occurred: {e}")
finally:
    spark.stop()
```

[Out]:

| Taco Name | Type | Price |
|---|---|---|
| Taco 1 | Beef | 2.5 |
| Taco 2 | Chicken | 2.0 |
| Taco 3 | Vegetarian | 2.0 |
| Taco 4 | Fish | 3.0 |

上述代码创建了一个包含塔可相关数据（塔可名称、类型和价格）的 PySpark DataFrame，然后使用 `show()` 方法打印该 DataFrame。

以下是每行代码的解释：

- `from pyspark.sql import SparkSession`: 该语句从 PySpark 库的 `pyspark.sql` 模块中导入 `SparkSession` 类。`SparkSession` 是使用 DataFrame 应用程序编程接口 (API) 对 Spark 进行编程的主要接口。它促进与 Spark 的交互，并启用创建 DataFrame，这是分布式数据处理任务所必需的。

- `spark = SparkSession.builder`: 这一行使用 `SparkSession.builder` 方法创建一个新的 SparkSession。

- `.appName("TacosDataFrame")`: 这一行将 Spark 作业的应用名称设置为 “TacosDataFrame”。

- `.getOrCreate()`: 这一行如果存在现有的 SparkSession 则获取它，如果不存在则创建一个新的。

- `data = [("Taco 1", "Beef", 2.50), ...]`: 这一行定义了一个塔可相关数据的示例数据集。列表中的每个元组代表一行数据，包含三个值：塔可名称、类型和价格。

- `schema = ["Taco Name", "Type", "Price"]`: 这一行定义了 DataFrame 的模式（schema）。它指定列名为 “Taco Name”、“Type” 和 “Price”。

- `tacos_df = spark.createDataFrame(data, schema)`: 这一行使用 SparkSession 的 `createDataFrame()` 方法创建一个名为 `tacos_df` 的 DataFrame。它接受两个参数：数据（在 `data` 中定义）和模式（在 `schema` 中定义）。

- `tacos_df.cache()`: 将 DataFrame 缓存在内存中，以增强后续访问该 DataFrame 多次的操作性能。在处理大型数据集或进行计算密集型操作时，缓存特别有益，可防止不必要的重新计算。此方法在首次计算后将中间 DataFrame 存储在内存中，由对 DataFrame 的第一个操作（如转换或行动）触发。




## 模型构建（PyTorch 和 TensorFlow）

在此管道步骤中，来自 PySpark 的预处理数据被用于使用 PyTorch 和 TensorFlow 框架构建深度学习模型。这些是广受欢迎的深度学习框架，以其在构建和训练神经网络模型时的灵活性和可扩展性而闻名。

PyTorch 由 Facebook 人工智能研究实验室（FAIR）开发，是一个开源机器学习框架。它于 2016 年 10 月发布，基于 Torch 库构建，并提供了更具 Python 风格（Pythonic）的接口。该框架的创建专注于灵活性、易用性和动态计算图。其关键特性之一是动态计算，这使得模型构建和调试更加直观。由于其用户友好的 API、详尽的文档以及对自动微分等高级特性的支持，PyTorch 在研究人员和开发者中广受欢迎。随着时间的推移，PyTorch 已成为深度学习社区中最广泛使用的框架之一，支撑着研究项目、生产系统和教育倡议。

TensorFlow 由 Google Brain 开发，最早于 2015 年 11 月作为开源机器学习库发布。该框架旨在具备可扩展性、灵活性和高效性，能够处理研究和生产工作负载。它引入了计算图的概念，允许用户定义复杂的神经网络架构，并在 CPU、GPU 或 TPU 上高效执行。TensorFlow 的初始版本提供了一个用于构建和训练深度学习模型的底层 API。然而，为了使深度学习更易于访问，Google 于 2017 年 3 月引入了 Keras 作为 TensorFlow 的高层 API。Keras 简化了构建和训练神经网络的过程，在保持 TensorFlow 性能和可扩展性的同时，提供了更易用的接口。Keras 整合到 TensorFlow 中促使其在各个行业和学术机构中的广泛采用，使其成为世界上最流行的深度学习框架之一。

在本节中，我们将概述这两个框架之间的通用步骤，而在第 4–7 章中，我们将深入探讨具体的实施细节，并演示如何使用这两个框架执行每个步骤：

- 数据加载和预处理：PyTorch 和 TensorFlow 都需要数据加载和预处理步骤来为训练准备数据。这可能涉及从文件读取数据、归一化以及将数据拆分为训练集和验证集等任务。
- 模型构建：在两个框架中，我们都定义神经网络模型的架构。这包括指定层的数量、层的类型（例如，全连接层、卷积层、循环层）、激活函数以及其他相关参数。
- 定义损失函数和优化器：PyTorch 和 TensorFlow 都允许我们根据任务选择损失函数（例如，回归使用均方误差 (MSE)，分类使用类别交叉熵）以及用于优化模型参数的优化器（例如，随机梯度下降 (SGD)、Adam）。
- 模型训练：两个框架中的训练循环都涉及遍历数据批次，将它们通过模型以获得预测值，计算损失，反向传播梯度，并使用优化器更新模型参数。
- 模型评估：训练完成后，我们在单独的验证集或测试集上使用适当的指标（如准确率、精确率、召回率或均方误差，具体取决于任务）来评估模型的性能。
- 推理：一旦模型经过训练和评估，我们就可以将其用于对新的、未见过的数据进行预测。这涉及将新数据通过训练好的模型并获取预测结果。

虽然 PyTorch 和 TensorFlow 之间的一般工作流程相似，但它们在 API、语法和具体实施细节上存在差异。例如：

- 在 PyTorch 中，我们使用 `nn.Module` 类定义模型，并在 `forward` 方法中构建前向传播过程；而在 TensorFlow 中，我们使用 `tf.keras.Model` 类，并在 `call` 方法中定义前向传播过程。
- PyTorch 强调动态计算图，允许更高的灵活性和更简单的调试，而 TensorFlow 最初使用静态计算图，但在 TensorFlow 2.0 及更高版本中采用了更具动态性的方法。
- TensorFlow 具有高层 API Keras，它为构建和训练神经网络模型提供了更简单、更易用的接口，而 PyTorch 的 API 更底层，提供了更大的灵活性。

以下是使用 PyTorch 和 TensorFlow/Keras 定义神经网络模型的示例，以说明它们在 API 和语法上的差异。我们首先使用 PyTorch 中的 `nn.Module` 定义一个神经网络模型，它指定了一个具有一个隐藏层的前馈网络（我们将在书的其他章节中探讨如何使用更多层）：

```python
import torch
import torch.nn as nn

class PyTorchModel(nn.Module):
    def __init__(self, input_size, hidden_size, output_size):
        super(PyTorchModel, self).__init__()
        
        # 输入层：全连接层
        self.fc1 = nn.Linear(input_size, hidden_size)
        
        # 激活层：ReLU 函数
        self.relu = nn.ReLU()
        
        # 输出层：全连接层
        self.fc2 = nn.Linear(hidden_size, output_size)

    def forward(self, x):
        # 应用输入层
        x = self.fc1(x)
        
        # 应用激活层
        x = self.relu(x)
        
        # 应用输出层
        x = self.fc2(x)
        return x
```

在 TensorFlow 中使用 `tf.keras.Model` 的等效代码如下：

```python
import tensorflow as tf
from tensorflow.keras import layers

class TensorFlowModel(tf.keras.Model):
    def __init__(self, hidden_size, output_size):
        super(TensorFlowModel, self).__init__()
        
        # 输入层：全连接 (dense) 层
        self.fc1 = layers.Dense(hidden_size, activation='relu')
        
        # 输出层：全连接 (dense) 层
        self.fc2 = layers.Dense(output_size)

    def call(self, inputs):
        # 应用输入层
        x = self.fc1(inputs)
        
        # 应用输出层
        x = self.fc2(x)
        return x
```

为了运行此代码，需要正确安装和配置 PySpark 以支持 Python 3（我们将在下一章介绍如何做）。将 PySpark 代码保存为文件，例如 "tacos_dataframe.py"，保存在 EC2 实例上，然后使用以下两种选项之一执行脚本：

1. 作为 Python 脚本运行：
   您可以 SSH 连接到您的 EC2 实例，并使用 Python 解释器执行脚本，如下所示：
   ```
   [In]: python3 tacos_dataframe.py
   ```
   这种方法利用您 EC2 实例的本地资源和 Spark 安装来创建和处理 DataFrame。

2. 使用 spark-submit 运行：
   或者，您可以通过使用 "spark-submit" 将脚本提交给本地 Spark 实例来利用 Spark 的分布式计算能力，如下所示：
   ```
   [In]: spark-submit tacos_dataframe.py
   ```
   此方法允许您的脚本以分布式方式执行，利用 Spark 提供的计算资源。

- `tacos_df.show()`: 这一行使用 `show()` 方法打印 DataFrame `tacos_df` 的内容（默认显示 DataFrame 的前 20 行）。
- `try/except` 块：
  - 在 `try` 块内部：执行显示带有 `tacos_df.show()` 的 DataFrame 等操作。
  - `except Exception as e:` 捕获操作期间可能发生的任何异常，处理运行时错误，例如数据处理问题或 Spark 连接问题。
- `finally` 块：
  - `spark.stop()`: 停止 `SparkSession`，释放与其相关的资源。使用 `finally` 确保无论 `try` 块是成功完成还是发生异常，都会执行此清理工作。

另一方面，`tacos_df.persist()` 提供了对存储级别更详细的控制，允许根据数据集的大小和可用的系统资源在仅内存、仅磁盘或两者结合之间进行选择。这种方法在涉及迭代算法或对同一 DataFrame 进行多个操作的场景中特别有益，因为它消除了为每个操作从头重新计算 DataFrame 的需要。




```python
## 应用输入层
x = self.fc1(inputs)

## 应用激活层 (ReLU)
x = tf.nn.relu(x)

## 应用输出层
x = self.fc2(x)
return x
```

在上述两个示例中，我们可以看到神经网络模型在 PyTorch 和 TensorFlow/Keras 中定义和使用的区别：

- 在 PyTorch 中，我们通过继承 `nn.Module` 来定义模型，并重写 `forward` 方法以指定前向传播的计算过程；而在 TensorFlow/Keras 中，我们继承 `tf.keras.Model` 来定义模型，并在 `call` 方法中实现前向传播的计算过程。
- PyTorch 使用如 `nn.Linear` 和 `nn.ReLU` 等模块来定义层，而 TensorFlow/Keras 使用 `tf.keras.layers.Dense` 以及如 `tf.nn.relu` 等激活函数。

我们可以看到，模型的整体工作流和使用方式是相似的，但在模型的定义和调用方式上存在语法上的差异。

这种类型的神经网络架构可用于回归和分类任务（这也是本书的重点），但需要根据具体的任务要求进行一些修改：

- **输出层激活函数：** 对于回归任务，输出层通常不应使用激活函数，或者可以使用线性激活函数，以便网络能够输出连续值。对于分类任务，输出层可能根据类别数量使用不同的激活函数。对于二元分类，我们可能会使用 Sigmoid 激活函数。对于多类分类，我们可能会使用 Softmax 激活函数。
- **损失函数：** 对于回归任务，我们通常使用如均方误差 (MSE) 或平均绝对误差 (MAE) 等损失函数。对于分类任务，我们通常使用交叉熵损失（或对数损失）用于二元分类，或使用类别交叉熵损失用于多类分类。
- **评估指标：** 使用的评估指标取决于任务类型。对于回归，我们可能会使用平均绝对误差 (MAE) 或均方误差 (MSE) 等指标。对于分类，我们可能会使用准确率、精确率、召回率或 F1 分数等指标。

在本书中，我们将展示如何使用深度学习来预测连续变量（如股价）和二元结果（如糖尿病诊断）。由于这些模型能够分析复杂数据并做出准确预测，因此它们在金融和医疗领域得到广泛应用。此外，值得注意的是，这些模型可以很容易地修改以处理金融和医疗领域以外的案例，展示了其通用性和跨领域的适用性。

了解如何使用深度学习进行此类预测任务，为从业者（数据科学家、机器学习工程师、研究人员和分析师）提供了关于神经网络的基础知识。这包括诸如前馈网络（神经网络的基本架构）、反向传播（用于训练神经网络的算法）和梯度下降（用于最小化损失函数的优化算法）等概念。这也为理解针对特定数据类型设计的专用模型奠定了坚实基础。例如，卷积神经网络 (CNN) 常用于计算机视觉任务中的图像数据，而循环神经网络 (RNN) 则用于处理时间序列或文本等顺序数据。尽管这些模型存在差异，但它们共享许多底层概念和原则，包括激活函数、权重初始化和优化技术。

## 模型训练 (EC2)

一旦我们使用 PyTorch 或 TensorFlow 构建了深度学习模型，下一步就是在由 Amazon EC2 实例提供的计算资源上训练它们。EC2（弹性计算云）是一种云服务，提供可扩展的云计算能力，使深度学习模型的高效训练成为可能。

EC2 实例提供了一系列针对不同工作负载优化的实例类型，包括专为深度学习任务定制的类型。EC2 提供的实例类型可分为若干类别：通用型、内存优化型、存储优化型、计算优化型和加速计算型。对于所有机器学习和深度学习应用程序，加速计算型实例是首选。

让我们详细讨论每种类型：

### 通用型

通用型实例提供了计算能力、内存容量和网络功能的混合，适用于广泛的工作负载。它们特别适用于需要均衡利用这些资源的任务，如托管 Web 服务器和管理代码仓库。

这些实例中最突出的是：

- **M4：** Amazon EC2 提供的第四代通用型实例。
- **M5、T3、T2：** 这些实例分别属于“M5”和“T3”代际，即第五代和第六代。“T2”实例也是第六代的一部分，与“T3”实例一起推出。
- **M6g、T4g：** 这些实例分别属于“M6g”和“T4g”代际。它们是最新一代的通用型实例，由 AWS Graviton2 处理器驱动，与前几代相比，性能和效率有所提升。

### 内存优化型

内存优化型实例旨在为在内存中处理大型数据集的工作负载提供快速性能。根据其内存容量和性能特征，它们可以分为两类：

- **内存容量中等到大、性能特征均衡，适用于通用工作负载的实例**——示例包括：
  - R4
  - R5
  - R6g
- **内存容量大、具备高性能能力，适用于内存密集型应用和高要求工作负载的实例**——示例包括：
  - R7g
  - R8g
  - X1e
  - X2gd

### 存储优化型

存储优化型实例专为需要广泛、顺序访问本地存储的大型数据集的任务而设计。这些实例旨在提供每秒数万次低延迟随机输入/输出操作 (IOPS)，满足具有严格性能要求的应用程序需求。它们可分为以下类别：

- **通用存储优化型实例**（专为需要高性能访问本地存储大型数据集的任务设计）：
  - I4g
  - I4i
  - I3
  - D2
- **增强型存储优化实例**（为苛刻的存储密集型工作负载提供增强的性能和功能）：
  - Im4gn
  - Is4gen
  - I3en
  - D3
  - D3n
  - H1

### 计算优化型

计算优化型实例在驱动计算密集型应用方面表现出色，利用高性能处理器提供卓越的速度和效率。这些实例专为高度依赖计算能力的任务量身定制，包括批处理、媒体转码、科学建模、HPC（高性能计算）、专用游戏服务器、广告服务器引擎、机器学习推理以及其他苛刻的计算密集型工作负载。

这些实例可分为以下类别：

- **高级计算优化型实例**（采用尖端技术和为苛刻的计算密集型工作负载优化的性能处理器）：
  - C7g
  - C7gn
  - C7i
  - C7a
- **标准计算优化型实例**（为计算密集型应用提供性能与成本效益的平衡）：
  - C6g
  - C6gn
  - C6i
  - C6in
  - C6a
- **遗留计算优化型实例**（来自前几代，仍为某些计算密集型任务提供可靠性能）：
  - C5
  - C5n
  - C5a
  - C4

### 加速计算型

加速计算型实例利用硬件加速器或协处理器的强大功能，与运行在常规 CPU 上的软件相比，更高效地执行浮点数计算、图形处理或数据模式匹配等任务。对于所有机器学习和深度学习应用程序，这些类型的实例是首选。它们以卓越的速度和精度著称，非常适合处理复杂的计算任务。这些实例可分为以下类型：




## 基于图形处理器（GPU）的实例
（配备 GPU 加速器，针对并行处理任务（如机器学习、深度学习和图形处理）进行了优化）：
- P2
- P3
- P4
- P5
- G5
- G5g
- G4dn
- G4ad
- G3

## 张量处理器（TPU）实例
（配备 TPU，这是 Google 专为机器学习任务开发的专用硬件加速器）：
- Trn1

## 推理加速器实例
（针对机器学习模型中的推理任务进行了优化，提供高吞吐量和低延迟）：
- Inf2
- Inf1

## 深度学习加速器实例
（专为深度学习工作负载定制，为训练和推理任务提供优化的性能）：
- DL1
- DL2q

## 基于 FPGA 的实例
（配备 FPGA 的实例，FPGA 是适用于各种计算任务的可定制硬件加速器）：
- F1

## 视频转码实例
（针对视频转码应用进行了优化，提供高效的多媒体内容处理能力）：
- VT1

在选择用于构建基于 PyTorch 或 TensorFlow 的深度模型的合适 EC2 实例类型时，应考虑几个因素以确保最佳的性能和效率。对于深度学习任务，特别是涉及复杂模型训练和评估的任务，通常更倾向于选择加速计算实例，因为它们具有卓越的速度和精度。这些实例利用专用硬件加速器或协处理器，与传统 CPU 相比，能够以更高的效率执行浮点数计算、图形处理和数据模式匹配等任务。配备图形处理器（GPU）的实例（例如 NVIDIA Tesla V100），由于其并行处理能力，非常适合加速深度学习训练。

此外，配备张量处理器（TPU）的实例（例如 Trn1）也可用于某些类型模型的更快训练。基于 GPU 的实例（例如 P2、P3、P4、P5、G5 等）特别适合深度学习中固有的并行处理任务，包括训练和推理。因此，对于使用 PyTorch 或 TensorFlow 的深度学习模型，选择在 Amazon EC2 上使用基于 GPU 或 TPU 的实例可以确保加速的性能以及高效的训练和评估流程。

在 EC2 实例上训练深度模型相较于在传统本地服务器上训练具有几个优势。首先，EC2 实例可以根据工作负载需求进行扩展或缩减，允许用户按需调整计算资源。这种可扩展性确保了不同复杂度和规模的模型都能高效训练，而不受硬件限制。

此外，EC2 实例提供了对各种预配置机器镜像（Amazon Machine Images (AMI)）和深度学习框架的访问，简化了训练环境的设置和配置过程。用户可以从流行的深度学习框架（如 TensorFlow 和 PyTorch）中选择，并利用为这些框架优化的预构建 AMI。

要为您的深度学习流水线设置或配置一个 EC2 实例，您需要配置该实例以满足特定要求，例如选择实例类型、配置存储、设置网络以及应用安全设置。

以下是 EC2 实例配置的关键步骤：

- 选择一个 AMI（Amazon 机器镜像）：
  - AMI 是一个预配置的模板，包含启动实例所需的操作系统、应用服务器和应用程序。您可以从各种公共 AMI（如 Amazon Linux、Ubuntu、Windows）中选择，或者创建自己的自定义 AMI。

- 选择实例类型：
  - 实例类型决定了用于您的实例的主机计算机的硬件。不同的实例类型提供不同的 CPU、内存、存储和网络容量的组合。例如，t2.micro 是一种通用型实例类型，而 p3.2xlarge 则是针对机器学习和 GPU 工作负载优化的。

- 配置存储：
  - 通过指定附加的弹性块存储（EBS）卷的类型和大小来配置实例的存储。例如，对于通用工作负载，您可以选择一个 16 GB 的 gp3 卷。

- 设置网络：
  - 您必须配置实例的网络，包括选择虚拟私有云（VPC）、选择子网以及决定实例是否拥有公有 IP 地址。实例还必须放置在适当的安全组中，该安全组定义了入站和出站流量规则。

- 应用安全设置：
  - 安全设置包括为实例的 SSH 访问分配密钥对，以及应用安全组规则来控制进出实例的流量。安全组充当虚拟防火墙。

- 启动实例：
  - 一旦所有配置都指定完毕，EC2 实例将被启动。此过程涉及分配必要的资源、部署操作系统以及设置网络和安全配置。

- 启动后配置：
  - 在实例运行后，您需要执行额外的设置任务，例如安装软件、配置应用程序以及连接到其他 AWS 服务。

在下一章中，我们将探讨如何手动以及通过 Amazon CloudFormation 配置 EC2 实例，以及如何安装和配置必要的软件和应用。

## 模型评估（EC2）

使用验证数据集评估训练后的模型，以评估其性能和泛化能力。评估指标用于衡量模型从数据中学习以及泛化到未见过的样本的程度。

对于回归任务，常用的度量包括均方误差（MSE）和 R 平方。MSE 衡量预测值与实际值之间的平均平方差。R 平方衡量因变量中可由自变量预测的方差比例，提供了模型拟合度的指示。

对于分类任务，常用以下评估指标：

- 准确率（Accuracy）：这衡量在总实例中分类正确的实例（真阳性和真阴性）的比例。

- 精确率（Precision）：这衡量在所有阳性预测中真正阳性预测的比例，重点关注阳性预测的准确性。

- 召回率（Recall）：这衡量在所有实际阳性实例中真正阳性预测的比例，重点关注模型识别所有阳性实例的能力。

- F1 分数（F1 Score）：这是精确率和召回率的谐波平均值或加权平均值，在精确率和召回率之间提供平衡，特别是在处理不平衡类别时。

- ROC-AUC（受试者工作特征曲线下面积）：ROC-AUC 衡量 ROC 曲线下的面积，该曲线绘制了真阳性率（敏感度）与假阳性率（1 - 特异度）的关系。它提供了模型在不同阈值下区分正类和负类能力的综合度量。

- 马修斯相关系数（MCC）：MCC 是观测到的和预测的二元分类之间的相关系数，考虑了混淆矩阵的所有四个值（真阳性、真阴性、假阳性、假阴性）。其范围从 -1 到 1，1 表示完美预测，0 表示随机预测，-1 表示预测和观测完全不一致。

混淆矩阵提供了计算诸如 MCC 等指标所需的组成部分。它是实际类别标签与预测类别标签的表格表示，允许对模型性能进行详细分析。

我们将在后续章节中使用其中一些指标。更具体地说，在第 **4** 章和第 **6** 章中，我们将计算 MSE 和 R 平方来评估深度学习回归模型；而在第 **5** 章和第 **7** 章中，我们将计算准确率、精确率、召回率和 F1 来评估深度学习分类模型。

## 模型部署（Airflow）

Apache Airflow 被用于编排训练后的模型部署到生产环境，调度和管理与模型部署相关的任务，以确保平滑且可靠的部署过程。这些任务可能包括模型版本管理、设置推理 API 以及监控生产环境中的模型性能。

Apache Airflow 最初由 Airbnb 在 2014 年开发，用于管理复杂的工作流和数据管道，后来在 2015 年开源，使全球开发者能够做出贡献。自此，它成为 Apache 软件基金会内的一个突出项目。由于其在工作流和管道管理中的灵活性、可扩展性和健壮性，它获得了广泛流行。其功能，如任务调度、依赖管理和可扩展性，吸引了除数据工程之外的广泛行业和用例。

此外，围绕 Airflow 的活跃社区通过不断添加新功能、改进文档和提供支持，促成了其增长。随着组织越来越多地采用数据驱动的方法和技术，对 Airflow 等可靠编排工具的需求变得更加明显，这进一步推动了其流行度。





在本节中，我们将向读者展示如何编排第一个有向无环图（DAG）。在第 8 章中，我们将创建一个完整的 AWS 管道，该管道包括使用 PySpark 对数据进行预处理；使用 PyTorch 和 TensorFlow 构建、训练和评估模型；以及使用 Airflow 部署模型。

在编排 DAG 之前，让我们首先演示 Python 代码通常是如何执行的。为了说明这一点，我们将使用 PySpark 创建一个 DataFrame，对其执行操作，并计算塔可（tacos）的平均价格：

```python
from pyspark.sql import SparkSession
from pyspark.sql.types import (
    StructType, StructField, StringType, FloatType
)
from pyspark.sql.functions import avg

def create_taco_dataframe(spark):
    """
    Create a DataFrame containing taco data.

    Parameters:
    spark (SparkSession): The SparkSession object.

    Returns:
    DataFrame: DataFrame containing taco data.
    """
    schema = StructType([
        StructField("Taco", StringType(), True),
        StructField("Price", FloatType(), True)
    ])

    data = [
        ("Chicken Taco", 2.50),
        ("Beef Taco", 3.00),
        ("Fish Taco", 3.50),
        ("Vegetarian Taco", 2.00)
    ]
    taco_df = spark.createDataFrame(data, schema)
    return taco_df

def calculate_average_price(taco_df):
    """
    Calculate the average price of tacos.

    Parameters:
    taco_df (DataFrame): DataFrame containing taco data.

    Returns:
    float: Average price of tacos.
    """
    avg_price = taco_df.select(avg("Price")).first()[0]
    return avg_price

def main():
    """
    Main function to demonstrate PySpark DataFrame operations.
    """
    spark = (
        SparkSession.builder
        .appName("TacoPrices")
        .getOrCreate()
    )

    taco_df = create_taco_dataframe(spark)
    taco_df.show()

    avg_price = calculate_average_price(taco_df)
    print("Average Price of Tacos:", avg_price)

    spark.stop()

if __name__ == "__main__":
    main()
```

输出：

| 塔可 | 价格 |
| --- | --- |
| 鸡肉塔可 | 2.5 |
| 牛肉塔可 | 3.0 |
| 鱼肉塔可 | 3.5 |
| 素食塔可 | 2.0 |

塔可的平均价格：2.75

上述代码经历了许多步骤：导入必要的模块、定义函数、创建主函数以及条件执行。以下是代码在每个步骤中执行内容的说明：

- **导入必要模块**：代码首先从 PySpark 导入所需的模块，包括用于创建 Spark 应用的 `SparkSession`；用于定义 DataFrame 模式（schema）的 `StructType`、`StructField`、`StringType` 和 `FloatType`；以及用于计算平均价格的 `pyspark.sql.functions` 中的 `avg` 函数。
- **定义函数**：定义了两个函数：
    - `create_taco_dataframe(spark)`：此函数创建一个包含塔可名称及其价格的 DataFrame。它定义了一个具有两个字段的模式：类型为 `StringType` 的 `"Taco"` 和类型为 `FloatType` 的 `"Price"`。然后，它创建一个包含塔可数据的元组列表，并使用 `SparkSession` 的 `createDataFrame` 方法创建 DataFrame。
    - `calculate_average_price(taco_df)`：此函数通过从 DataFrame `taco_df` 中选择 `"Price"` 列，应用 `avg` 函数并获取结果来计算塔可的平均价格。
- **主函数**：定义 `main()` 函数以执行程序的主要逻辑。在主函数内部：
    - 使用应用程序名称 `"TacoPrices"` 初始化 `SparkSession`。
    - 调用 `create_taco_dataframe()` 函数以创建包含塔可数据的 DataFrame。
    - 在 DataFrame 上调用 `show()` 方法以显示其内容。
    - 调用 `calculate_average_price()` 函数以计算塔可的平均价格。
    - 打印平均价格。
    - 最后，停止 `SparkSession` 以释放资源。
- **条件执行**：代码块 `if __name__ == "__main__"` 确保只有当脚本直接运行时（而不是作为模块导入时），`main()` 函数才会被执行。

现在，让我们将此代码迁移到 Apache Airflow。下面的代码设置了一个 Apache Airflow DAG，用于自动化使用 PySpark 创建包含塔可数据的 DataFrame、计算塔可的平均价格，并将结果保存到 Parquet 文件的过程。该 DAG 配置了默认参数、任务依赖关系和其他参数，以定义工作流的行为：

```python
from airflow import DAG
from airflow.operators.python_operator import PythonOperator
from datetime import datetime
from pyspark.sql import SparkSession
from pyspark.sql.types import (StructType, StructField, StringType, FloatType)
from pyspark.sql.functions import avg

def create_taco_dataframe(**context):
    """
    Create a DataFrame containing taco data and save it
    to a Parquet file.

    Parameters:
        context (dict):
            The context dictionary containing task
            metadata.

    Returns:
        None
    """
    schema = StructType([
        StructField("Taco", StringType(), True),
        StructField("Price", FloatType(), True)
    ])

    data = [
        ("Chicken Taco", 2.50),
        ("Beef Taco", 3.00),
        ("Fish Taco", 3.50),
        ("Vegetarian Taco", 2.00)
    ]

    spark = SparkSession.builder.getOrCreate()
    taco_df = spark.createDataFrame(data, schema)

    taco_df.show()

    taco_df.write.parquet(
        "/home/ubuntu/airflow/dags/taco_prices.parquet",
        mode="overwrite"
    )

def calculate_average_price(**context):
    """
    Calculate the average price of tacos from the DataFrame.

    Parameters:
        context (dict):
            The context dictionary containing task metadata.

    Returns:
        None
    """
    spark = SparkSession.builder.getOrCreate()
    taco_df = spark.read.parquet(
        "/home/ubuntu/airflow/dags/taco_prices.parquet"
    )
    avg_price = taco_df.select(avg("Price")).first()[0]
    print("Average Price of Tacos:", avg_price)

default_args = {
    'owner': 'airflow',
    'start_date': datetime(2024, 3, 20),
    'retries': 1
}

dag = DAG(
    'taco_prices_dag',
    default_args=default_args,
    description='DAG to calculate average taco prices',
    schedule_interval=None,
    catchup=False
)

create_taco_dataframe_task = PythonOperator(
    task_id='create_taco_dataframe_task',
    python_callable=create_taco_dataframe,
    provide_context=True,
    dag=dag
)

calculate_average_price_task = PythonOperator(
    task_id='calculate_average_price_task',
    python_callable=calculate_average_price,
    provide_context=True,
    dag=dag
)

create_taco_dataframe_task >> calculate_average_price_task
```

要运行该 DAG，我们遵循以下步骤：

1. **激活虚拟环境**：在运行 DAG 之前，请激活安装了 Apache Airflow 及其依赖项的虚拟环境。这确保使用正确的 Python 环境来执行 DAG 任务。在此项目中，我们创建了一个名为 "myenv" 的环境：

   ```bash
   source /home/ubuntu/myenv/bin/activate
   ```

   此命令激活位于 `/home/ubuntu/myenv` 的名为 "myenv" 的 Python 虚拟环境。当我们激活虚拟环境时，它会修改 shell 环境，使其使用该特定虚拟环境关联的 Python 解释器和包。这确保在该 shell 会话中执行的任何 Python 命令都将使用虚拟环境中的 Python 版本和已安装的包，而不是全局系统 Python 环境。

2. **导航至 DAG 目录**：激活虚拟环境后，导航到您的 DAG 脚本所在的目录。这通常是存储您的 Apache Airflow DAG 文件的目录。在此项目中，我们使用的是 `airflow/dags` 目录：

   ```bash
   cd /home/ubuntu/airflow/dags
   ```

   此命令将当前目录更改为 DAG 脚本 (`taco_prices_dag.py`) 保存所在的目录。

3. **运行 Apache Airflow Web 服务器和调度器**：一旦进入包含 DAG 脚本的目录，我们启动 Apache Airflow web 服务器和调度器以初始化 Airflow 环境：

   ```bash
   airflow webserver &
   airflow scheduler &
   ```

   这些命令在后台启动 Airflow web 服务器和调度器进程。Web 服务器提供 Airflow 用户界面，而调度器则编排 DAG 和任务的执行。





## 4. 触发 DAG：在 Web 服务器和调度器运行之后，使用 Airflow 命令行界面（CLI）触发 DAG：

```
[In]: airflow dags trigger taco_prices_dag
```

该命令用于触发 taco_prices_dag DAG 的执行。

在深入代码并更详细地解释 DAG 的每个组件之前，需要指出的是，Apache Airflow 提供了多种部署选项，每种选项都适用于不同的环境和需求。这里讨论的是独立部署选项，即 Airflow 将直接安装在单一机器上并运行，这将在下一章（“在 AWS 上设置深度学习环境”）中详细探讨。这种设置非常简单，非常适合测试。它受到个人开发者和处理较不复杂 DAG 的小型团队的欢迎。虽然独立 Airflow 易于设置且所需资源较少，但它存在诸如可扩展性有限等局限性，因此不太适合大型生产环境。

在下一章中，我们还将研究第二种选择——Docker 容器化设置，其中 Airflow 在隔离的 Docker 容器中运行。与独立部署相比，这种方法提供了更多的灵活性和可扩展性。使用 Docker，Airflow 及其依赖项被打包到容器中，确保在开发、预发布和生产环境中保持一致的环境。这种设置非常适合需要管理依赖项、避免冲突并通过添加更多容器轻松扩展 Airflow 环境的团队。

在第 10 章中，我们将探索第三种选择：Amazon Managed Workflows for Apache Airflow (MWAA)，这是由 AWS 提供的一种完全托管服务。MWAA 负责 Airflow 的设置、扩展和维护，使用户可以专注于编写和运行其 DAG。该选项最适合需要高可用性、可靠性以及与其他 AWS 服务无缝集成的生产环境。

现在让我们深入代码，更详细地解释 DAG 的每个组件：

### 1. 导入语句：

```
[In]: from airflow import DAG
[In]: from airflow.operators.python_operator import PythonOperator
[In]: from datetime import datetime
[In]: from pyspark.sql import SparkSession
[In]: from pyspark.sql.types import (StructType, StructField, StringType, FloatType)
[In]: from pyspark.sql.functions import avg
```

这些导入语句引入了创建 Apache Airflow DAG、定义 PythonOperator 任务、处理 datetime 对象以及与 PySpark 交互所需的模块和类。使用 `from airflow.operators.python_operator import PythonOperator` 语句时，请确保您的 Airflow 版本与 PythonOperator 的导入兼容。PythonOperator 的导入路径可能因您的 Airflow 版本而异。例如，在 Airflow 2.x 中，导入路径已从 `airflow.operators.python_operator` 更改为 `airflow.operators.python`。如果您使用的是 Airflow 2.x 或更高版本，请更新导入语句如下所示：

```
[In]: from airflow.operators.python import PythonOperator
```

### 2. 任务函数：

```
[In]: def create_taco_dataframe(**context):
    """
    Create a DataFrame containing taco data and
    save it to a Parquet file.

    Parameters:
        context (dict):
            The context dictionary containing
            task metadata.

    Returns:
        None
    """
    schema = StructType([
        StructField("Taco", StringType(), True),
        StructField("Price", FloatType(), True)
    ])
    data = [("Chicken Taco", 2.50),
            ("Beef Taco", 3.00),
            ("Fish Taco", 3.50),
            ("Vegetarian Taco", 2.00)]
    spark = SparkSession.builder.getOrCreate()
    taco_df = spark.createDataFrame(data, schema)
    taco_df.show()
    taco_df.write.parquet(
        "/home/ubuntu/airflow/dags/taco_prices.parquet",
        mode="overwrite"
    )
```

```
[In]: def calculate_average_price(**context):
    """
    Calculate the average price of tacos from the DataFrame.

    Parameters:
        context (dict):
            The context dictionary containing task metadata.

    Returns:
        None
    """
    spark = SparkSession.builder.getOrCreate()
    taco_df = spark.read.parquet(
        "/home/ubuntu/airflow/dags/taco_prices.parquet"
    )
    avg_price = taco_df.select(avg("Price")).first()[0]
    print("Average Price of Tacos:", avg_price)
```

该代码创建了两个任务函数：

-   **create_taco_dataframe**：此函数创建一个包含塔可（taco）数据的 PySpark DataFrame，该数据框有两列，分别为“Taco”和“Price”。然后，它将此 DataFrame 保存为 Parquet 文件。Parquet 是一种列式存储格式，对于存储和查询结构化数据非常高效。它提供了诸如压缩、高效编码以及对嵌套数据结构的原生支持等优势。将数据存储为 Parquet 格式对大数据处理任务有益，因为它提高了查询性能，降低了存储成本，并促进了与 Apache Spark 和 Hadoop 等各种数据处理框架的兼容性。
-   **calculate_average_price**：此函数从保存在 Parquet 文件中的 DataFrame 计算塔可的平均价格。

### 3. 默认参数：

```
[In]: default_args = {
    'owner': 'airflow',
    'start_date': datetime(2024, 3, 20),
    'retries': 1
}
```

`default_args` 定义了 DAG 的默认配置参数，包括 DAG 的所有者、DAG 运行的开始日期以及每个任务的重试次数。

### 4. DAG 定义：

```
[In]: dag = DAG('taco_prices_dag',
                default_args=default_args,
                description='DAG to calculate average taco prices',
                schedule_interval=None,
                catchup=False
                )
```

此部分定义了一个名为 `taco_prices_dag` 的新 DAG，使用了指定的 `default_args`、描述、调度间隔（None 表示该 DAG 未被调度，需要手动触发）以及补抓（catchup）设置（设置为 False 以防止补抓错过的 DAG 运行）。我们可以将该 DAG 设置为自动运行，方法是将 `schedule_interval` 从 `None` 更改为 `'@daily'`，如下所示：

```
[In]: dag = DAG('taco_prices_dag',
                default_args=default_args,
                description='DAG to calculate average taco prices',
                schedule_interval='@daily',
                catchup=False
                )
```

`@daily` cron 表达式指定该 DAG 应每天运行一次。因此，该 DAG 不再需要手动触发，而是将根据指定的计划自动运行。如果我们希望每周、每月或每季度运行，cron 表达式将分别修改为 `@weekly`、`@monthly` 或 `@quarterly`。

### 5. 任务操作符：

在 DAG 中定义了两个 `PythonOperator` 任务：

-   `create_taco_dataframe_task`：此任务调用 `create_taco_dataframe` 函数。
-   `calculate_average_price_task`：此任务调用 `calculate_average_price` 函数。

### 6. 提供上下文：

```
[In]: provide_context=True
```

为两个任务设置了 `provide_context=True`，以便将包含任务元数据的 Airflow 上下文字典传递给任务函数。这允许访问信息，例如 DAG 运行 ID 和任务执行日期。

### 7. 任务依赖关系：

```
[In]: create_taco_dataframe_task >> calculate_average_price_task
```

使用 `>>` 操作符在任务之间建立依赖关系，表示 `calculate_average_price_task` 应在 `create_taco_dataframe_task` 之后运行。

一旦 DAG `taco_prices_dag` 成功运行，我们通常会在 Airflow 用户界面 (UI) 上观察到以下输出：

#### 任务执行日志：

-   您将看到每个任务生成的日志，指示其执行状态、遇到的任何错误以及执行期间生成的任何输出。
-   例如，`create_taco_dataframe_task` 将显示日志，展示创建包含塔可数据的 DataFrame 的过程以及将其保存为 Parquet 文件的过程。
-   类似地，`calculate_average_price_task` 将显示日志，展示从保存在 Parquet 文件中的 DataFrame 计算塔可平均价格的过程。

#### 任务状态：

-   每个任务的状态将在 Apache Airflow UI 中更新，指示任务是否成功执行（success）、遇到错误（failed）或正在运行（running）。
-   您将能够监控每个任务的进度，并识别执行过程中可能发生的任何问题。

#### 输出数据：

-   如果任务成功执行，您将获得由 DAG 的任务生成的输出数据。
-   例如，在 `create_taco_dataframe_task` 运行后，您将拥有一个 Parquet 文件（`taco_prices.parquet`），其中包含已保存到指定位置（`/home/ubuntu/airflow/dags/`）的包含塔可数据的 DataFrame。





- `calculate_average_price_task` 将输出塔可（tacos）的平均价格，该价格会被打印到任务日志中，并可在 Apache Airflow 界面中查看。

**执行元数据：**

- Apache Airflow 维护每次 DAG 运行的元数据，包括开始时间、结束时间、持续时间以及与每个任务执行相关的任何相关元数据等详细信息。
- 您可以在 Apache Airflow 界面或通过 Airflow 的后端数据库访问这些元数据。

利用 Apache Airflow 提供了更具可扩展性和可管理性的工作流编排方法，这是通过用 Airflow DAG 定义替换独立脚本中的 `main()` 函数来实现的。

让我们讨论一下这种替换是如何进行的：

- **任务函数：** 在 `main()` 函数内执行的每个逻辑步骤或操作都会成为 Airflow DAG 中的一个独立任务。例如，`create_taco_dataframe` 函数和 `calculate_average_price` 函数将成为 DAG 中的独立任务。
- **DAG 定义：** 我们不再使用 `main()` 函数，而是在 Airflow 中定义一个 DAG 对象。该 DAG 对象封装了工作流，包括任务依赖关系、调度以及其他参数。DAG 定义提供了一种结构化表示和管理工作流的方式。
- **任务依赖关系：** 在独立脚本中，`main()` 函数内的函数调用顺序决定了执行顺序。在 Airflow DAG 中，任务依赖关系通过使用 `>>` 等操作符显式定义，以指示哪些任务依赖于其他任务。这确保了任务按正确的顺序执行。
- **执行上下文：** 在独立脚本中，函数在 `main()` 函数的上下文中顺序执行。在 Airflow 中，每个任务在 DAG 运行的上下文中独立执行。Airflow 根据 DAG 定义自动管理任务执行、调度、重试和错误处理。
- **触发执行：** 虽然 `main()` 函数通常通过直接运行脚本来触发，但 Airflow DAG 的执行可以手动触发、基于调度触发，或对外部事件做出响应。这种触发是使用 Airflow 的命令行界面 (CLI)、Web 界面或通过网络接口通过其 API 以编程方式完成的。

上述内容表明，用 Airflow DAG 替换 `main()` 函数提供了更具可扩展性和可管理性的工作流编排方法。Airflow 的基于 DAG 的方法允许对复杂工作流进行更好的监控、调度和管理，特别是在数据处理管道和 ETL（提取、转换、加载）任务中。

总体而言，整个管道（从使用 S3 进行数据摄取的第一步开始，到在 Apache Airflow 上调度模型运行结束）具有几个优势：

- 首先，它利用了 PySpark 在大规模数据处理方面的可扩展性以及 EC2 实例在模型训练方面的计算能力，确保高效利用资源。
- 其次，基于云的方法提供了灵活性，允许根据工作负载需求扩展资源并轻松配置资源。
- 第三，PySpark 和 Apache Airflow 凭借其分布式计算能力简化了数据处理任务，实现了高效预处理、转换和工作流编排。
- 第四，Amazon S3 的大容量存储促进了不间断的数据存储和检索，支持大规模数据集的处理。
- 最后，在预处理（PySpark）、模型开发、训练和评估（PyTorch、TensorFlow）、模型编排（Apache Airflow）、存储（S3）和计算（EC2）之间关注点的分离简化了架构并增强了模块化，从而促进简化的工作流管理。

## 项目目录结构

在开始一个新项目时，首先需要考虑的事项之一是如何组织构成该项目的文件和目录。精心设计的 项目目录结构 提供了多项好处，包括组织性、协作性、可复现性和文档化：

- **组织性：** 清晰且合乎逻辑的结构有助于跟踪所有项目文件，使查找所需内容更容易，并避免杂乱。
- **协作性：** 在与团队合作时，标准化的目录布局确保了贡献者之间的一致性，并减少了关于在哪里查找特定文件的困惑。
- **可复现性：** 组织良好的项目目录更易于复现实验或分析，因为所有必要的数据、代码和输出都整齐地组织并记录在案。
- **文档化：** 目录结构本身作为一种形式的文档，提供了对项目架构、组件和工作流的洞察。

理想的目录结构应具备以下属性：

- 直观且易于导航。
- 避免不必要的目录嵌套或过于复杂的层级结构。
- 应根据内容类型划分为逻辑部分。
- 使用有意义的目录和文件名称，以反映其内容和目的。
- 在目录中包含 README 文件或文档，以提供关于如何使用其中包含的文件的其他上下文和指导。

图 1-2 是一个预测特斯拉股价的项目可能如何结构的示例。

# 第 1 章    AWS 上可扩展深度学习管道概述

```
项目目录结构
├── data
│   └── TSLA_stock.csv
├── logs
├── output
│   ├── TSLA_stock.parquet
│   │   ├── _SUCCESS
│   │   └── part-00000-2c717885-1e92-4091-b73e-c07fb2f42ba8-c000.snappy.parquet
│   └── TSLA_stock_train.parquet
│       ├── _SUCCESS
│       └── part-00000-3931d223-097a-4b7f-a6df-6ddc8abfbc5c-c000.snappy.parquet
├── src
│   ├── pyspark_code
│   │   └── data_preprocessing.py
│   ├── pytorch_code
│   │   ├── model.py
│   │   └── model_training.py
│   └── main.py
├── tests
│   └── test.py
├── visualizations
│   └── plot.png
├── README.md
├── config.yaml
└── requirements.txt
```

**图 1-2.** *预测特斯拉股价的项目目录结构*

为了理解特斯拉股价预测项目的组织方式，让我们详细检查目录结构：

- `data`: 此目录包含项目的输入数据。在这种情况下，它是一个名为 `TSLA_stock.csv` 的 CSV 文件，包含特斯拉的历史股票数据。
- `logs`: 此目录可能包含项目执行期间生成的日志文件。将日志与其他项目文件分开是常见的做法，以便于管理。
- `output`: 此目录存储项目生成的输出文件。它包含两个子目录：
    - `TSLA_stock.parquet`: 此目录保存 Parquet 文件，代表与特斯拉股票相关的处理数据。
    - `TSLA_stock_train.parquet`: 与前面的目录类似，此目录包含代表机器学习模型训练数据的 Parquet 文件。
- `src`: 此目录包含项目的源代码。它进一步组织到子目录中：
    - `pyspark_code`: 包含与用于数据清理或转换的 PySpark 数据预处理相关的 Python 文件。
    - `pytorch_code`: 包含用于 PyTorch 模型开发和训练的 Python 文件。
    - `main.py`: 这是项目的主入口点，项目的不同组件在此进行编排。
- `tests`: 此目录保存项目的测试文件。在这种情况下，有一个名为 `test.py` 的 Python 文件，其中包含项目组件的单元测试。
- `visualizations`: 此目录存储项目生成的可视化输出。它包含一个名为 `plot.png` 的 PNG 文件，这是与特斯拉股票分析相关的图表或绘图。
- `README.md`: 这是一个提供项目信息的 markdown 文件。它通常包括设置项目的说明、其用途概览以及其他相关详细信息。
- `requirements.txt`: 此文件列出了运行项目所需的依赖项。它通常包括项目执行所需的 Python 包及其版本。
- `config.yaml`: 此文件包含项目的配置设置。它可能包括数据预处理、模型训练或项目其他方面的参数。下面是一个基本的 `config.yaml` 文件示例，可以添加到特斯拉项目中，用于表示和概述结构：

```yaml
project:
  name: Tesla Stock Prediction
  version: 1.0
  author: Abdelaziz Testas

data:
  input_path: data/TSLA_stock.csv
  output_path: output/TSLA_stock.parquet
  train_output_path: output/TSLA_stock_train.parquet

preprocessing:
  missing_values_strategy: fillna
  fillna_value: 0
  scaling_method: standard_scaler

training:
```




model_type: pytorch
batch_size: 32
epochs: 50
learning_rate: 0.001
train_split: 0.8
random_seed: 42

[In]: logging:
    log_level: INFO
    log_file_path: logs/project.log

[In]: visualization:
    plot_output_path: visualizations/plot.png
    plot_type: line
    x_axis: Date
    y_axis: Close

[In]: aws_s3:
    bucket_name: instance1bucket
    region: us-west-2
    input_file_key: TSLA_stock.csv
    output_file_key: TSLA_stock_output.parquet

## 虚拟环境

除了创建清晰定义的项目结构外，建议还创建虚拟环境（例如 myenv）来管理项目的依赖关系，并确保在不同环境中的一致性和可复现性。这会将项目的依赖项与系统上的其他 Python 项目隔离开来，防止冲突，并确保无论系统配置如何，项目都能在一致的环境中运行。下一章将解释如何创建这样的环境，以及上述所示的项目目录结构。

# 第 1 章 AWS 上可扩展深度学习流程概览

## 开发环境

在研究了 AWS 上完整深度学习工作流程的组件，并讨论了设计项目目录结构以及在 EC2 上设置虚拟环境的重要性后，让我们深入探讨实际编写代码和开发机器学习模型的地方。

为了本书项目的目的，我们将主要使用 JupyterLab。然而，还有其他流行的深度学习开发环境选项，包括 Jupyter Notebook、PyCharm 和 Visual Studio Code (VS Code)。Databricks 是另一个值得注意的选项，特别适合基于 Spark 的工作流程和大规模数据处理。它提供了一个统一的分析平台，包括协作笔记本、数据工程工具和机器学习功能，全部集成在可扩展的云环境中。虽然 Databricks 在大数据处理任务方面表现出色，但与 JupyterLab、Jupyter Notebook、PyCharm 或 VS Code 等其他环境相比，它可能不是深度学习特定任务的首选，因为后者为机器学习模型开发提供了更多专门的功能。

JupyterLab 和 Jupyter Notebook 都是 Jupyter 生态系统的一部分，为数据科学和机器学习任务提供交互式计算环境。这两者的主要区别在于其用户界面和功能。

Jupyter Notebook 提供了一个经典的界面，用户可以在其中创建和运行代码单元格，查看输出，并使用 Markdown 单元格记录其工作流程。它为原型设计和实验提供了直观且易于使用的环境。另一方面，JupyterLab 是一个更先进且可扩展的界面，建立在 Jupyter Notebook 的功能之上。它提供灵活且集成的环境，具有多个面板、标签页工作区和拖放功能等特性。JupyterLab 增强了大规模项目的支持，允许用户同时处理多个笔记本、文本文件、终端和自定义扩展。此外，JupyterLab 的模块化架构使用户能够通过特定任务或工作流程的扩展来定制其环境。

对于快速测试或小代码片段，使用像 Nano 这样的轻量级文本编辑器来创建 Python 脚本就足够了。

在下一章中，我们将演示如何设置这些工具，以创建一个高效且富有生产力的深度学习开发环境。

# 摘要

在本章中，我们考察了一个综合的深度学习流水线，利用亚马逊云服务（AWS）的强大功能来处理大规模数据处理、模型训练和部署任务。该流水线的核心是 Amazon S3，作为集中式数据源，用于存储原始数据集、预处理数据和模型工件。数据预处理由 PySpark 支持， enabling 在存储在 S3 中的大数据集上进行分布式数据处理。该流水线利用 PyTorch 和 TensorFlow 来构建和训练深度学习模型，充分发挥其灵活性和可扩展性。Amazon EC2 实例提供了模型训练和评估所需的计算资源，确保云资源的高效利用。Apache Airflow 协调将训练好的模型部署到生产环境，简化了部署流程，确保任务的顺利和逻辑执行。我们还探讨了设计项目目录结构和在 EC2 上设置虚拟环境的重要性，以及用于编写代码和开发机器学习模型的工具。

在下一章中，我们将指导读者在 AWS 上设置环境并配置必要的工具和服务的过程。这为后续章节奠定了基调，我们将深入探讨构建和部署可扩展流水线。

# 第 2 章
## 在 AWS 上设置深度学习环境

在上一章中，我们探讨了基于云的深度学习在应对数据量增长和 AI 应用复杂性带来的挑战方面日益增长的重要性。我们介绍了将强大框架——PySpark、PyTorch、TensorFlow 和 Apache Airflow——与亚马逊云服务（AWS）云解决方案（特别是 Amazon S3 和 EC2）集成的深度学习流水线。该流水线为管理现代深度学习工作流程的需求提供了可扩展且高效的方法。

通过对流水线组件及其在深度学习工作流程中的角色有了坚实的理解，我们现在将重点转向设置环境，以便读者在实践中应用这些概念。我们将逐步介绍在 AWS 上配置必要工具和服务的过程，以确保完全功能性的设置。这个环境将为后续章节中构建和部署可扩展流水线奠定基础。

我们将按照以下步骤设置深度学习环境：

- 创建 AWS 账户：这是访问 AWS 服务和资源的第一步。通过创建 AWS 账户，您可以访问 AWS 管理控制台，在那里您可以管理您的 EC2 实例、S3 存储桶和其他 AWS 服务。
- 配置 EC2：这一步在云中创建虚拟服务器（实例）以运行应用程序和工作负载。我们研究手动和自动化选项。
- 设置 Amazon S3：此步骤涉及创建存储桶、配置访问权限以及上传或下载数据。
- 创建项目目录并设置虚拟环境：在配置 EC2 实例后，您设置项目目录并配置开发或数据分析的环境。这包括安装必要软件、设置 Python 环境和组织项目文件等任务。
- 安装和配置依赖项：在这一步中，您需要安装和配置各种依赖项，以便在 AWS 上有效构建和部署可扩展的深度学习流水线。这些包括安装 PySpark、PyTorch、TensorFlow、Airflow 和 JupyterLab 等。

我们将逐一探讨这些步骤，从创建 AWS 账户开始。

### 创建 AWS 账户

在您开始设置亚马逊网络服务（AWS）上的深度学习环境之前，您首先需要创建一个 AWS 账户。此账户将授予您访问广泛 AWS 服务的权限，为构建和部署深度学习流水线提供基础基础设施。

以下是创建 AWS 账户的步骤：

- 访问 AWS 网站：导航至 https://aws.amazon.com/ 的 AWS 网站，并点击页面右上角的“Sign in to the Console”（登录控制台）按钮。
- 创建新的 AWS 账户：如果您是 AWS 的新用户，请点击“Create a new AWS account”（创建新的 AWS 账户）按钮开始注册过程。如果您已有 AWS 账户，可以使用现有凭据登录。
- 提供账户信息：输入您的电子邮件地址并为您的 AWS 账户选择密码。您还需要提供一些关于您和您组织的基本信息。
- 验证您的身份：AWS 将要求您通过电子邮件或电话验证来确认您的身份。按照提示完成此步骤。
- 选择支持计划：系统将提示您选择一个支持计划。对于大多数刚开始使用 AWS 的用户来说，免费层提供了充足的资源用于探索实验。




## 输入付款信息

若要使用超出免费层限制的 AWS 服务，您需要提供付款信息。AWS 提供按量付费定价模式，这意味着您只需为所使用的服务付费，无需签订长期合同或进行预付承诺。

## 审阅并确认

请审阅您的账户信息、服务条款和定价详情，然后确认创建您的 AWS 账户。

一旦您的 AWS 账户创建成功，您即可访问 AWS 管理控制台，从而开始配置深度学习环境所需的资源。

# 配置 Amazon EC2 实例

Amazon EC2 提供可扩展的云计算能力，允许您启动称为“实例”的虚拟服务器，以运行您的应用程序和工作负载。配置 EC2 实例是设置深度学习环境的第一步，为训练和推理任务提供所需的计算能力。

在本节中，我们将探讨手动配置方法和使用 AWS CloudFormation 的自动化配置方法。

手动配置 EC2 实例的步骤如下：

- 导航至 EC2 仪表板：登录 AWS 管理控制台，点击“Services”下拉菜单，选择“EC2”，然后从 EC2 服务页面点击“EC2 Dashboard”。
- 启动实例：点击“Launch Instance”按钮，开始实例创建流程。
- 选择 Amazon Machine Image (AMI)：选择一个 AMI 作为您的 EC2 实例的基础。您可以从各种预配置的 AMI 中进行选择，包括针对 TensorFlow 和 PyTorch 等深度学习框架优化的 AMI。
- 选择实例类型：选择最适合您计算需求的实例类型。就本书的项目而言，我们选择了“t2.xlarge”实例类型，它提供 16 GiB 内存和四个 vCPU。虽然该实例不包含 GPU，但它适合运行书中描述的各种演示和实验。然而，对于可能需要加速处理的生产级深度学习任务，您需要一个带有专用 GPU 的实例。
- 配置实例详细信息：自定义实例设置，包括实例数量、网络设置和存储选项。例如，选择一个运行 Ubuntu Server 22.04 LTS（指支持长期支持的 Ubuntu 22.04 操作系统版本）的“t2.xlarge”实例，HVM 虚拟化（硬件虚拟机，提供更好的性能和兼容性），以及 SSD 卷类型（固态硬盘存储，提供更快的磁盘 I/O 性能）。
- 添加存储：指定附加到您 EC2 实例的存储卷。您可以选择多种类型的存储，包括 Amazon Elastic Block Store (EBS) 卷和实例存储卷。
- 配置安全组：为您的 EC2 实例定义安全组，以控制入站和出站流量。确保开放必要的端口，以便与您的深度学习环境进行通信。配置 EC2 实例的安全组涉及定义控制实例入站和出站流量的规则。以下是操作方法：
    - 导航至安全组部分：在启动您的 EC2 实例后，前往 AWS 管理控制台中的 EC2 仪表板。在左侧导航窗格的“Network & Security”部分下，点击“Security Groups”。
    - 创建新的安全组：如果您没有适合您深度学习环境的现有安全组，可以通过点击“Create Security Group”按钮创建一个新安全组。
    - 定义入站规则：在创建或选定的安全组中，定义入站规则以控制流向您的 EC2 实例的传入流量。例如，您可能希望允许 SSH 访问（端口 22）用于远程管理，访问 Jupyter notebook 或 JupyterLab（端口 8888），以及 Apache Airflow 的 Web 界面（默认端口 8080）。您也可以根据需要开放其他端口，以便与其他服务或应用通信。
    - 定义出站规则：同样，定义出站规则以控制从您的 EC2 实例发出的传出流量。默认情况下，允许所有出站流量，但您可以根据具体要求进行限制。
    - 审阅并应用更改：审阅已配置的安全组规则，确保它们满足您的安全性和连接性需求。满意后，点击“Save”或“Apply Changes”按钮以将更改应用到安全组。
    - 将安全组与您的 EC2 实例关联：最后，将新创建或更新的安全组与您的 EC2 实例关联。您可以通过在 EC2 仪表板中选择该实例，点击“Actions”下拉菜单，并选择“Security” ➤ “Change Security Groups”来完成此操作。选择所需的安全组，然后点击“Assign Security Groups”。
- 审阅并启动：审阅实例配置详情并进行必要调整。满意后，点击“Launch”按钮以启动您的 EC2 实例。
- 创建密钥对：如果您尚未创建 SSH 密钥对，系统将提示您创建一个。此密钥对用于通过 SSH 安全连接到您的 EC2 实例。
- 访问您的 EC2 实例：一旦您的 EC2 实例启动，您可以使用 SSH 或其他远程访问方法访问它。首先连接到您的实例，并根据您的深度学习需求对其进行配置。
- 启动和停止您的 EC2 实例：在您的 EC2 实例启动后，您可能需要根据使用情况要求启动或停止它。操作方法如下：
    - 启动实例：在 AWS 管理控制台中导航至 EC2 仪表板。选择您要启动的实例，并从“Actions”下拉菜单中选择“Instance State” ► “Start instance”。
    - 停止实例：同样，要停止实例，请从 EC2 仪表板中选择该实例，并从“Actions”下拉菜单中选择“Instance State” ► “Stop instance”。
    - 注意：如果您在工作完成后未停止实例，将产生费用。请务必在不再需要时停止实例，以避免不必要的成本。

遵循这些步骤，您将成功配置一个 Amazon EC2 实例。

您也可以使用 Amazon CloudFormation 自动执行这些步骤——这是一种允许您使用简单文本文件来定义和配置云基础设施的工具。例如，下面的脚本利用 Amazon CloudFormation 自动化创建一个具有以下配置的 EC2 实例：t2.xlarge 实例类型、40 GB gp3 EBS 卷，以及允许 SSH 访问的安全组：

```yaml
AWSTemplateFormatVersion: "2010-09-09"
Description: Provision a t2.xlarge EC2 instance with a 40 GB gp3 EBS volume for deep learning tasks

Resources:
  DeepLearningEC2Instance:
    Type: AWS::EC2::Instance
    Properties:
      InstanceType: t2.xlarge
      KeyName: instance1keypair.pem
      SubnetId: subnet-04856bd3f80a406e6
      ImageId: ami-05134c8ef96964280
      BlockDeviceMappings:
        - DeviceName: /dev/sda1
          Ebs:
            VolumeSize: 40
            VolumeType: gp3
      SecurityGroupIds:
        - !Ref InstanceSecurityGroup
  InstanceSecurityGroup:
    Type: AWS::EC2::SecurityGroup
    Properties:
      GroupDescription: Enable SSH access
      VpcId: vpc-09f1a4805e4bd7aa6
      SecurityGroupIngress:
        - IpProtocol: tcp
          FromPort: 22
          ToPort: 22
          CidrIp: 0.0.0.0/0

Outputs:
  InstanceId:
    Description: Instance ID of the newly created EC2 instance
    Value: !Ref DeepLearningEC2Instance
```

此脚本自动创建具有特定配置的 EC2 实例，包括实例类型、存储卷和安全设置。以下是脚本各部分的详细说明：

- AWSTemplateFormatVersion 和 Description：脚本通过 AWSTemplateFormatVersion 指定 CloudFormation 模板格式的版本，设置为 "2010-09-09"。这表明所使用的 CloudFormation 语法版本。Description 字段提供了模板目的的简要概述。在此情况下，它描述了脚本将配置一个 t2.xlarge EC2 实例，该实例配有 40 GB gp3 EBS 卷，旨在用于深度学习任务。
- Resources 部分：脚本的核心是 Resources 部分，其中定义了 EC2 实例及其相关配置。在此部分中，有两个关键资源：DeepLearningEC2Instance 和 InstanceSecurityGroup。
- DeepLearningEC2Instance：该资源代表 EC2 实例本身。Type 设置为 AWS::EC2::Instance，表示该资源将创建一个 EC2 实例。在 Properties 下配置了多个属性：
    - InstanceType 将实例类型指定为 t2.xlarge，这是一种适用于多种工作负载的通用型实例。




### EC2 实例属性

- **KeyName** 设置为 `instance1keypair.pem`，这是用于访问实例的 SSH 密钥对的名称。这确保了通过 SSH 安全地访问实例。
- **SubnetId** 设置为 `subnet-04856bd3f80a406e6`，表明将在指定 VPC 内的哪个子网中启动实例。这允许控制实例运行的网络环境。
- **ImageId** 指定了 AMI（Amazon Machine Image）ID `ami-05134c8ef96964280`，它定义了实例的操作系统和初始软件配置。此 AMI 作为实例的基础镜像。
- **BlockDeviceMappings** 定义了存储配置，将 40 GB 的 gp3 EBS（Elastic Block Store）卷附加到实例。`DeviceName` `/dev/sda1` 指定了根卷，并且 `VolumeType` 设置为 gp3，这是一种通用型 SSD。
- **SecurityGroupIds** 将实例与一个安全组关联，该安全组在脚本稍后定义。安全组控制进出实例的流量。

### InstanceSecurityGroup

- **InstanceSecurityGroup**：此资源定义了与 EC2 实例关联的安全组。`Type` 设置为 `AWS::EC2::SecurityGroup`，表明此资源将创建一个安全组。`Properties` 部分指定了以下内容：
    - **GroupDescription** 提供了安全组用途的简要说明，在此情况下是启用 SSH 访问。
    - **VpcId** 设置为 `vpc-09f1a4805e4bd7aa6`，将安全组链接到特定的 VPC（Virtual Private Cloud）。
    - **SecurityGroupIngress** 定义了入站流量规则。脚本允许来自任何 IP 地址（`CidrIp: 0.0.0.0/0`）的 22 端口（SSH）的 TCP 流量。虽然这在测试时很方便，但由于安全问题，不建议在生产环境中使用。

### Outputs 部分

`Outputs` 部分提供了关于脚本创建的资源的信息。具体来说，它输出了新创建的 EC2 实例的 `InstanceId`。这允许你在堆栈创建后轻松引用实例 ID，这对于进一步的自动化或管理任务非常有用。

上述脚本采用 YAML 格式，但你也可以以 JSON 格式编写 CloudFormation 模板。如下所示的 JSON 脚本中演示的，两种格式都提供相同的 CloudFormation 功能：

```json
{
"AWSTemplateFormatVersion": "2010-09-09",
"Description": "Provision a t2.xlarge EC2 instance with a 40 GB gp3 EBS volume for deep learning tasks",
"Resources": {
"DeepLearningEC2Instance": {
"Type": "AWS::EC2::Instance",
"Properties": {
"InstanceType": "t2.xlarge",
"KeyName": "instance1keypair.pem",
"SubnetId": "subnet-04856bd3f80a406e6",
"ImageId": "ami-05134c8ef96964280",
"BlockDeviceMappings": [
{
"DeviceName": "/dev/sda1",
"Ebs": {
"VolumeSize": 40,
"VolumeType": "gp3"
}
}
],
"SecurityGroupIds": [
{
"Ref": "InstanceSecurityGroup"
}
]
}
},
"InstanceSecurityGroup": {
"Type": "AWS::EC2::SecurityGroup",
"Properties": {
"GroupDescription": "Enable SSH access",
"VpcId": "vpc-09f1a4805e4bd7aa6",
"SecurityGroupIngress": [
{
"IpProtocol": "tcp",
"FromPort": 22,
"ToPort": 22,
"CidrIp": "0.0.0.0/0"
}
]
},
"Outputs": {
"InstanceId": {
"Description": "Instance ID of the newly created EC2 instance",
"Value": {
"Ref": "DeepLearningEC2Instance"
}
}
}
}
```

## 设置 Amazon S3

Amazon Simple Storage Service（S3）是 Amazon Web Services（AWS）提供的高度可扩展的存储服务。Amazon S3 为存储和访问大量数据提供了可靠且经济实惠的解决方案。它提供高可用性、持久性和可扩展性，使其成为存储数据集、模型检查点、训练日志以及深度学习工作流所需的其他资源的理想选择。通过设置 Amazon S3，你可以集中管理数据存储，并在多个 EC2 实例和用户之间轻松共享资源。

以下是设置 Amazon S3 的步骤：

- **导航到 S3 仪表板**：登录到 AWS 管理控制台，点击“Services”下拉菜单，并从可用服务列表中 select “S3”。这将直接带你到 S3 仪表板，你可以在那里管理你的存储桶（buckets）和对象。
- **创建一个存储桶**：点击“Create bucket”按钮以创建一个新的 S3 存储桶。为你的存储桶选择一个唯一的名称，并选择你希望存储桶所在的 AWS 区域。一旦存储桶创建完成，你将看到一条消息，如“Successfully created bucket ‘your-bucket-name.’”。
- **配置存储桶属性**：配置 S3 存储桶的属性，包括存储类、加密设置和版本控制选项。你可以根据数据存储需求和合规性要求选择合适的设置。要配置 S3 存储桶的属性，可以按照以下步骤进行：
    - **选择存储桶**：在 S3 仪表板上显示的存储桶列表中，选择你要配置属性的存储桶。
    - **访问存储桶属性**：选择存储桶后，点击存储桶详细信息窗格中的“Properties”选项卡。此选项卡允许你为选定的存储桶配置各种属性。
    - **配置属性**：在“Properties”选项卡中，你将找到配置各种设置的选项，例如：
        - **存储类**：为你的数据选择合适的存储类，如 Standard（标准）、Intelligent-Tiering（智能分层）、Standard-IA（标准-不频繁访问）、One Zone-IA（单区域-不频繁访问）、Glacier 等。每种存储类都有不同的定价和访问特性。
        - **加密设置**：启用服务端加密以加密存储在存储桶中的对象。你可以选择 Amazon S3 管理的密钥（SSE-S3）、AWS Key Management Service（SSE-KMS）或客户提供的密钥（SSE-C）。
        - **版本控制**：启用版本控制以在存储桶中保留对象的多个版本。这有助于保护对象免受意外删除或覆盖的影响。
        - **保存更改**：配置完所需的属性后，确保点击相应的按钮（如“Save changes”或“Apply”）保存更改。
    - **设置存储桶权限**：定义 S3 存储桶的访问控制设置，以管理谁可以访问存储桶中存储的数据以及他们可以执行的操作。你可以在存储桶和对象级别设置权限。要设置存储桶权限并定义 S3 存储桶的访问控制设置，请遵循以下步骤：
        - **选择存储桶**：选择你要设置权限的存储桶。
        - **选中存储桶后**：你应该看到一个标记为“Permissions”的选项卡。
        - **点击此选项卡**：访问所选存储桶的权限设置。
        - **在 Permissions 选项卡下**：你将找到设置存储桶策略、访问控制列表（ACL）和阻止公共访问设置的选项。
        - **点击“Bucket Policy”**：使用 JSON 语法定义存储桶策略。存储桶策略允许你指定谁可以访问存储桶以及他们可以执行的操作。
        - **或者**：你可以通过点击 Permissions 选项卡下的“Access control list (ACL)”来设置存储桶访问控制列表（ACL）。
        - **ACL** 允许你向预定义的用户组授予特定权限，例如向经过身份验证的用户授予读取或写入访问权限。
        - **定义所需权限后**：使用存储桶策略或 ACL 定义权限后，检查设置以确保它们符合你的安全要求。
        - **满意后**：一旦你对权限配置感到满意，保存或应用更改以强制执行 S3 存储桶的访问控制设置。
        - **如果需要设置对象级别的权限**（即针对存储桶内的单个文件），你可以通过修改对象 ACL 来实现。这可以通过选择存储桶内的特定对象并相应地调整其权限设置来完成。
- **上传数据到存储桶**：一旦你的 S3 存储桶设置完成，你就可以开始向其中上传数据。你可以通过 S3 控制台直接上传数据，使用 AWS 命令行界面（CLI），或将 S3 与其他 AWS 服务集成以实现顺畅的数据传输。

以下是从 EC2 与 S3 交互的步骤。

要从 EC2 实例访问存储在 S3 存储桶中的数据，你需要配置 Identity and Access Management（IAM）角色和策略，以授予必要的权限。IAM 角色允许你在不暴露 AWS 凭据的情况下安全地验证和授权对 S3 资源的访问。切勿在脚本中硬编码 AWS 凭据，因为这会带来重大的安全风险。相反，考虑使用以下安全的替代方案：

- **IAM 角色**：将 IAM 角色附加到你的 EC2 实例，以自动提供必要的权限，而无需在代码中嵌入凭据。
- **环境变量**：将敏感凭据存储在环境变量中，应用程序可以访问这些变量而不需要硬编码。
- **AWS Secrets Manager**：使用 AWS Secrets Manager 安全地存储和检索凭据，例如数据库密码或 API 密钥。

要使用 IAM 角色实现安全访问，请遵循以下步骤：

1. 登录到 AWS 管理控制台并打开 IAM 控制台。
2. 导航到“Roles”部分并点击“Create role”。





3.  选择将使用此角色的服务（在本例中为 EC2）。
4.  附加必要的策略以授予访问 S3 资源的权限（例如，用于完全访问权限的 AmazonS3FullAccess）。
5.  审核并命名你的角色，然后创建它。
6.  在 AWS 管理控制台中导航至 EC2 仪表盘。
7.  选择你要附加 IAM 角色的 EC2 实例。
8.  点击“Actions” ➤ “Security” ➤ “Modify IAM role”。
9.  从下拉菜单中选择你之前创建的 IAM 角色，并确认附加操作。
10. 一旦 IAM 角色附加到 EC2 实例，你就可以使用 AWS SDK 或 AWS CLI 等命令行工具以编程方式访问 S3 数据。

## 创建项目目录

在配置好 Amazon EC2 实例后，创建项目目录是一个合乎逻辑的步骤。这对于高效地组织和管理工作至关重要。它提供了一个结构化的环境，用于存储所有与项目相关的文件（包括源代码、数据、文档和输出），从而便于导航和协作。通过指定目录，版本控制变得更加简单，确保更改被准确跟踪，协作顺畅进行。此外，组织良好的项目目录通过封装所有必要的文件和依赖项，增强了可重复性，使在不同环境中共享和复现结果变得更加容易。它还促进了可扩展性和可维护性，允许在不影响整体组织的情况下添加新组件。最终，项目目录作为有效的项目管理、文档编制和协作的基础，为项目的成功做出贡献。

在前一章中，我们为特斯拉股票预测项目概述了一个目录结构，但我们没有深入探讨生成该结构的代码。下面的 Bash 脚本是在 EC2 上的 JupyterLab 笔记本环境中执行的，它建立了包含组织数据、源代码和输出文件所需的具体子目录和文件的结构。脚本末尾的 tree 命令展示了已创建目录的结构，以便进行可视化展示：

```bash
%bash
project_dir="Project Directory Structure"
mkdir -p "$project_dir"
mkdir -p "$project_dir/data"
touch "$project_dir/data/TSLA_stock.csv"
mkdir -p "$project_dir/src/pyspark_code"
touch "$project_dir/src/main.py"
touch "$project_dir/src/pyspark_code/data_preprocessing.py"
mkdir -p "$project_dir/src/pytorch_code"
touch "$project_dir/src/pytorch_code/model.py"
touch "$project_dir/src/pytorch_code/model_training.py"
mkdir -p "$project_dir/output"
mkdir -p "$project_dir/output/TSLA_stock.parquet"
touch "$project_dir/output/TSLA_stock.parquet/_SUCCESS"
touch "$project_dir/output/TSLA_stock.parquet/part-00000-2c717885-1e92-4091-b73e-c07fb2f42ba8-c000.snappy.parquet"
mkdir -p "$project_dir/output/TSLA_stock_train.parquet"
touch "$project_dir/output/TSLA_stock_train.parquet/_SUCCESS"
touch "$project_dir/output/TSLA_stock_train.parquet/part-00000-3931d223-097a-4b7f-a6df-6ddc8abfcb5c-c000.snappy.parquet"
mkdir -p "$project_dir/logs"
mkdir -p "$project_dir/tests"
touch "$project_dir/tests/test.py"
mkdir -p "$project_dir/visualizations"
touch "$project_dir/visualizations/plot.png"
touch "$project_dir/README.md"
touch "$project_dir/config.yaml"
touch "$project_dir/requirements.txt"
tree "$project_dir" --dirsfirst
```

以下是脚本各部分的作用说明：

- `%%bash`：这是 Jupyter 笔记本中的一个单元格魔法命令，允许你在代码单元格中直接运行 Bash 命令。当你在 Jupyter 单元格的顶部包含 `%%bash` 时，它指示笔记本将整个单元格解释为 Bash 命令，而不是 Python 代码。
- `project_dir="Project Directory Structure"`：这一行定义了一个名为 `project_dir` 的变量，并为其赋值“Project Directory Structure”。该变量将用于指定主项目目录的名称。
- `mkdir -p “$project_dir”`：此命令创建由 `project_dir` 变量指定的主项目目录。`-p` 选项确保在需要时创建中间目录，并且如果目录已存在，命令不会抛出错误。
- `mkdir -p “$project_dir/data”`：在主项目目录内创建一个名为“data”的子目录。
- `touch “$project_dir/data/TSLA_stock.csv”`：在“data”子目录内创建一个名为“TSLA_stock.csv”的空文件。在现实场景中，通常不会本地创建空文件，而是将现有的 CSV 文件上传到 Amazon S3 存储桶。文件存储在 S3 中后，你可以轻松使用 `aws s3 cp` 等命令将其复制到 EC2 实例上的本地目录。
- 类似的 `mkdir` 和 `touch` 命令用于在项目目录中创建不同用途的目录和文件，例如源代码（`src`）、输出（`output`）及其各自的子目录。
- `tree “$project_dir” --dirfirst`：此命令使用 `tree` 命令生成项目目录结构的可视化表示。`--dirfirst` 选项确保在输出中目录列在文件之前。

**注意** tree 命令并未预装在包括 Amazon Linux 或 Mac 上的 Ubuntu 在内的所有系统上，我们在本项目中使用了这些系统。要在 Ubuntu 上安装 tree 命令，我们使用了以下命令：`sudo apt-get install tree`；对于 Amazon Linux：`sudo yum install tree`。

使用 tree 命令的 Bash 代码输出显示了 `project_dir` 及其子目录的目录结构，展示了创建的文件和文件夹，如图 2-1 所示（从 JupyterLab 笔记本保存为图像）。

```text
Project Directory Structure
|-- data
|   `-- TSLA_stock.csv
|-- logs
|-- output
|   |-- TSLA_stock.parquet
|   |   `-- _SUCCESS
|   |   `-- part-00000-2c717885-1e92-4091-b73e-c07fb2f42ba8-c000.snappy.parquet
|   `-- TSLA_stock_train.parquet
|       |-- _SUCCESS
|       `-- part-00000-3931d223-097a-4b7f-a6df-6ddc8abfcb5c-c000.snappy.parquet
|-- src
|   |-- pyspark_code
|   |   `-- data_preprocessing.py
|   |-- pytorch_code
|   |   |-- model.py
|   |   `-- model_training.py
|   `-- main.py
|-- tests
|   `-- test.py
|-- visualizations
|   `-- plot.png
|-- README.md
|-- config.yaml
`-- requirements.txt
```

**图 2-1.** *用于预测特斯拉股价的项目目录结构*

第 2 章 在 AWS 上设置深度学习环境

## 创建虚拟环境

除了建立明确定义的项目结构外，建议创建一个虚拟环境（例如，myenv）来管理依赖项并确保在各种环境中的可重复性。这种做法将项目的依赖项与系统上的其他 Python 项目隔离开来，从而防止冲突并确保无论系统配置如何都能保持一致的执行。一旦你的 EC2 实例启动并运行，请遵循以下步骤在 Ubuntu 操作系统上创建、激活和取消激活虚拟环境：

步骤 1：导航到你的主目录：

```bash
cd /home/ubuntu
```

步骤 2：创建一个虚拟环境：

```bash
python3 -m venv myenv
```

此命令假设你的系统上已安装 Python 3。某些系统可能仍然默认使用 Python 2.7，这与 venv 模块不兼容。你可以通过运行以下命令来检查你的 Python 版本：

```bash
python3 -version
```

如果未安装 Python 3，你可以安装它，例如在 Ubuntu 上使用以下命令：

```bash
sudo apt-get update
sudo apt-get install python3
```

在 Amazon Linux 上：

```bash
sudo yum update
sudo yum install python3
```





`python3 -m venv myenv` 命令会创建一个名为“myenv”的虚拟环境。虚拟环境是为项目提供的隔离 Python 环境。您可以从 EC2 实例上的任何目录访问此环境。一旦激活，无论当前工作目录在哪里，您都可以使用“myenv”虚拟环境中的 Python 解释器和已安装的包。这种灵活性允许您在 EC2 实例上的任何位置处理 Python 项目，提供了便利性和易用性。

让我们检查一下虚拟环境 `myenv` 内部的内容：

```
[In]: ls myenv
[Out]: bin include lib lib64 pyvenv.cfg
```

这些是在 Python 虚拟环境中创建的标准目录和文件。

让我们逐一分解这些项目的内容：

- **bin**：此目录包含虚拟环境的可执行文件。当您激活虚拟环境时，这些二进制文件会被添加到您的 PATH 中，以便虚拟环境中的 Python 解释器、`pip` 和其他工具优先于全局工具使用。

- **include**：此目录包含编译包含 C 扩展的某些 Python 包所需的 C 头文件。

- **lib**：此目录包含 Python 标准库以及在虚拟环境中运行 Python 脚本所需的其他共享库。

让我们查看该目录内部：

```
[In]: ls myenv/lib
[Out]: python3.9
```

- **lib64**：此目录是指向 `lib` 目录的符号链接。这是为了与使用 `lib64` 目录来存放 64 位库的系统保持兼容。

- **pyvenv.cfg**：这是虚拟环境的配置文件。它存储与虚拟环境相关的设置和元数据。

这些目录和文件共同构成了 Python 虚拟环境的结构。当您激活虚拟环境时，`bin` 目录会被添加到您的 PATH 开头，确保虚拟环境中的 Python 解释器和其他工具优先使用。

**步骤 3：激活虚拟环境**

```
[In]: source myenv/bin/activate
```

该命令用于激活虚拟环境。激活后，您的 shell 提示符会发生变化，以指示您现在正在“myenv”虚拟环境中工作。

**步骤 4：停用虚拟环境**

```
[In]: deactivate
```

当您想要退出或停用当前激活的虚拟环境并返回到全局 Python 环境时，使用 `deactivate` 命令。这在一个项目工作结束后，或者当您想要切换到不同的虚拟环境或全局 Python 环境时非常有用。

**注意** 虽然虚拟环境对于管理项目内的依赖关系非常有效，但 Docker 提供了另一种方法。它允许您将应用程序及其依赖关系容器化，确保其在不同环境中运行的一致性。我们将在演示如何为 Airflow 设置 Docker 容器时更详细地探讨 Docker。

## 安装和配置依赖项

设置好虚拟环境后，为了有效地在 AWS 上构建和部署可扩展的深度学习流水线，需要安装和配置各种依赖项。本节提供指导，介绍如何在虚拟环境中安装和配置最常用的机器学习和工具库。这些库包括 PySpark、PyTorch、TensorFlow、Airflow 和 JupyterLab。此外，如果偏好使用 Databricks 框架来预处理存储在 S3 上作为深度学习项目输入数据之前，还介绍了创建 Databricks 账户并设置工作区的说明。

### 安装 PySpark

按照以下步骤安装 PySpark：

**步骤 1：激活虚拟环境**

如果您尚未激活虚拟环境，请导航到主目录（例如，“/home/ubuntu”），并激活“myenv”虚拟环境：

```
[In]: cd /home/ubuntu
[In]: source myenv/bin/activate
```

**步骤 2：安装 PySpark**

激活虚拟环境后，使用 `pip` 安装 PySpark：

```
[In]: pip install pyspark
[Out]: Successfully installed py4j-0.10.9.7 pyspark-3.5.1
```

“Successfully installed py4j-0.10.9.7 pyspark-3.5.1”这一行是 `pip install pyspark` 命令的输出。它表明 PySpark 包及其依赖项 Py4J 已成功下载并安装到您的虚拟环境（“myenv”）中。

- **py4j-0.10.9.7**：这是 Py4J 库的版本，它是 Python 和 Java 之间的桥梁。PySpark 使用 Py4J 与基于 Java 的 Spark 框架进行交互。

- **pyspark-3.5.1**：这是已安装的 PySpark 库本身的版本。

此输出确认 PySpark 和 Py4J 都已正确安装，并可在您的虚拟环境中使用。您也可以通过运行导入 PySpark 的 Python 脚本来验证安装是否完成：

```
[In]: python -c "import pyspark; print(pyspark.__version__)"
[Out]: 3.5.1
```

该命令打印出已安装的 PySpark 版本，在这种情况下为 3.5.1。

### 安装 PyTorch

在激活虚拟环境后，使用 `pip` 安装 PyTorch。您可以根据系统配置和需求选择合适的命令。例如，要安装支持 GPU 加速的统一计算设备架构（CUDA）的 PyTorch，可以使用以下命令：

```
[In]: pip install torch torchvision torchaudio
```

安装完成后，您可以通过运行导入 PyTorch 的 Python 脚本来验证：

```
[In]: python -c "import torch; print(torch.__version__)"
[Out]: 2.2.2+cu121
```

该命令打印出已安装的 PyTorch 版本，在这种情况下为 2.2.2。如后缀“+cu121”所示，这包括支持 GPU 加速的 CUDA。

> **注意** CUDA（统一计算设备架构）是由 NVIDIA 创建的并行计算平台和应用编程接口（API）模型。它允许软件开发者利用 NVIDIA GPU（图形处理单元）的算力进行通用处理任务，包括深度学习和科学模拟。

### 安装 TensorFlow

使用 `pip` 按照以下方式安装 TensorFlow 和 Keras：

```
[In]: pip install tensorflow keras
```

此命令安装 TensorFlow 和 Keras，后者现在是 TensorFlow 的一部分，作为其用于构建神经网络的高层 API。

安装完成后，您可以通过运行导入 TensorFlow 和 Keras 的 Python 脚本来验证：

```
[In]: python -c "import tensorflow as tf; print(tf.__version__)"
[In]: python -c "import keras; print(keras.__version__)"
[Out]: 2.16.1
[Out]: 3.2.1
```

输出指示以下版本：

- TensorFlow 版本：2.16.1
- Keras 版本：3.2.1

### 安装 Boto3

Boto3 是亚马逊云科技（AWS）的 Python SDK。它允许开发者使用 Python 代码与 AWS 服务进行交互。使用 Boto3，您可以以编程方式访问和管理各种 AWS 资源，例如 EC2 实例、S3 存储桶、DynamoDB 表等。

您可以使用以下 `pip` 命令安装 Boto3：

```
[In]: pip install boto3
```

安装完成后，您可以通过运行导入 Boto3 的 Python 脚本来验证：

```
[In]: python -c "import boto3; print(boto3.__version__)"
[Out]: 1.34.84
```

输出显示版本 1.34.84 已成功安装。

### 安装 Airflow

在 EC2 上使用 Apache Airflow 主要有三个选项：独立版、基于 Docker 的版本以及通过 Amazon 托管 Apache Airflow 工作流（MWAA）完全托管的版本。在本节中，我们提供设置独立版和基于 Docker 的 Airflow 版本的说明，而有关使用 MWAA 的指导将在第 10 章中提供。

### 独立安装

在本小节中，提供了在 EC2 实例上使用独立安装方式设置 Airflow 的详细说明。此设置允许在没有额外抽象层的情况下直接控制 Airflow 环境。

请按照以下步骤执行此安装：

**步骤 1：激活您的环境**

```
[In]: source /home/ubuntu/myenv/bin/activate
```

**步骤 2：更新并安装依赖项**

```
[In]: sudo apt update
[In]: sudo apt install python3-pip sqlite3 libpq-dev
```

- `sudo apt update`：此命令更新用于升级的包列表。
- `sudo apt install python3-pip sqlite3 libpq-dev`：安装必要的依赖项，包括 Python 3 pip、SQLite 和 PostgreSQL 开发文件。





## 第 3 步：安装支持 PostgreSQL 的 Apache Airflow

```
[In]: pip install "apache-airflow[postgres]==2.5.0" \
    --constraint \
    "https://raw.githubusercontent.com/apache/airflow/constraints-2.5.0/constraints-3.7.txt"
```

- 该行安装支持 PostgreSQL 的 Apache Airflow。它指定了版本 2.5.0，并从约束文件（constraints file）安装额外的依赖项。

## 第 4 步：初始化 Airflow 数据库

```
[In]: airflow db init
```

该行初始化 Airflow 元数据库。

## 第 5 步：安装并配置 PostgreSQL

```
[In]: sudo apt-get install postgresql postgresql-contrib
[In]: sudo -i -u postgres
[In]: psql
```

代码解释：

- 第 1 行：安装 PostgreSQL 及额外的 contrib 包。
- 第 2 行：切换到 PostgreSQL 用户。
- 第 3 行：进入 PostgreSQL 命令行界面。

## 第 6 步：在 PostgreSQL shell 中

```
[In]: CREATE DATABASE airflow;
[In]: CREATE USER your-username WITH PASSWORD 'your-password';
[In]: GRANT ALL PRIVILEGES ON DATABASE airflow TO your-username;
[In]: \q
[In]: exit
```

- CREATE DATABASE airflow;：创建一个名为 "airflow" 的数据库
- CREATE USER your-username WITH PASSWORD 'your-password';：创建一个具有指定用户名和密码的用户
- GRANT ALL PRIVILEGES ON DATABASE airflow TO your-username;：将 "airflow" 数据库的所有权限授予创建的用户
- \q：退出 PostgreSQL shell
- exit：退出 PostgreSQL 用户会话

这些指令为 Airflow 创建了一个用于存储其元数据的 PostgreSQL 数据库。此外，代码创建了一个专用的用户，用于访问此数据库。至关重要的是，将 "your-username" 替换为您选择的用户名，并将 "your-password" 替换为强密码。该用户将拥有 "airflow" 数据库的完全权限，确保 Airflow 能够有效管理其元数据。执行这些命令后，您将退出 PostgreSQL shell 并返回到命令行。

通过为 Airflow 创建独立的数据库和用户，您可以确保 PostgreSQL 实例具有更好的安全性和组织性，将 Airflow 的数据与其他数据库和用户隔离。此外，使用权限受限的专用用户可以降低对 Airflow 元数据进行未授权访问的风险。

## 第 7 步：更新 Airflow 配置

在这一步中，我们设置 Apache Airflow 所需的配置和设置：

```
[In]: cd airflow
[In]: sed -i 's#sqlite:///home/ubuntu/airflow/airflow.db#postgresql+psycopg2://your-username:your-password@localhost/airflow#g' airflow.cfg
[In]: sed -i 's#SequentialExecutor#LocalExecutor#g' airflow.cfg
```

代码解释：

- 第 1 行：更改目录到 Airflow 配置目录。
- 第 2 行：将 Airflow 配置文件中的 SQLite 连接字符串替换为 PostgreSQL 连接字符串。您需要将“your-username”和“your-password”替换为您在第 6 步中为 PostgreSQL 数据库设置的实际用户名和密码。这确保 Airflow 使用适当的凭据连接到正确的数据库。
- 第 3 行：将 Airflow 配置文件中的 SequentialExecutor 替换为 LocalExecutor。

在 Apache Airflow 配置中将 SQLite 切换到 PostgreSQL，并将 SequentialExecutor 切换到 LocalExecutor 的目的是为了增强可扩展性和健壮性，如下所述：

### 从 SQLite 切换到 PostgreSQL

- SQLite 适用于开发和测试目的，但可能不适合生产环境，尤其是在处理多个 Airflow 用户、高并发和大量数据时。
- PostgreSQL 是一个强大的、开源的关系型数据库管理系统，以其可扩展性、可靠性和功能丰富而闻名。通过切换到 PostgreSQL，您可以更好地处理并发访问，管理更大的数据集，并确保生产环境中的数据完整性。

### 从 SequentialExecutor 切换到 LocalExecutor

- Airflow 中的 SequentialExecutor 在单个进程中顺序运行任务，随着任务数量及其依赖关系的增加，这可能成为性能瓶颈。
- 另一方面，LocalExecutor 允许 Airflow 在多个工作进程之间并行化任务执行，从而提高性能和可扩展性。每个任务可以独立执行，从而更有效地利用可用的计算资源。

## 第 8 步：创建管理员用户

```
[In]: airflow users create -u your-username -f your-first-name -l your-last-name -r Admin -e your@mail.com
```

在 Apache Airflow 中创建管理员用户对于安全地管理和管理 Airflow 实例至关重要。通过创建管理员用户，您建立了一个拥有特权的用户，允许他们执行管理任务，如管理连接、变量、池和用户，以及访问敏感信息，如 DAG 运行和日志。在创建管理员用户时，至关重要的是选择强密码并限制访问仅必要的专业人员。这有助于防止未授权访问并保护 Airflow 内的敏感信息。将管理角色分配给特定用户还有助于在 Airflow 实例内执行安全策略。管理员用户有权配置访问控制、设置权限和监控用户活动，确保 Airflow 环境的完整性和安全性。

## 第 9 步：启动 Airflow web 服务器和调度器

```
[In]: airflow webserver &
[In]: airflow scheduler
```

- airflow webserver &：此命令在后台启动 Airflow web 服务器。Web 服务器提供了一个用于管理和监控 Airflow 工作流的用户界面（UI）。通过使用 & 符号在后台运行 web 服务器，即使您注销终端会话，它也可以继续运行。这确保当您没有主动登录服务器时，Web UI 仍然可访问。
- airflow scheduler：此命令启动 Airflow 调度器。调度器负责根据定义的调度（例如 cron 表达式）和任务之间的依赖关系（定义在 DAG 中）触发任务实例。它持续监控 DAG 中需要执行的任务，并根据其调度和依赖关系触发它们。

建议将这些命令在单独的终端会话中运行。分开运行允许更好地监控和排查每个组件的问题。像 tmux 或 screen 这样的工具提供会话管理功能，允许您分离和重新连接终端会话，确保 web 服务器和调度器即使在您注销终端会话后也能继续运行。

## 第 10 步：访问 Airflow UI

- 打开网络浏览器并导航到您的 EC2 实例的公共 IP 地址或域名，后跟 Airflow 端口（默认为 8080）：

```
[In]: http://<your_ec2_public_ip>:8080
```

- 系统将提示您输入用户名和密码。
- 输入您之前创建的凭据，您应该能够登录到 Airflow UI。

为了设置 8080 端口以访问 Airflow UI，通常您需要确保您的 EC2 实例的安全组允许 8080 端口的入站流量，并且 Airflow 配置为监听 8080 端口。

以下是操作方法：

### EC2 安全组配置

- 进入 AWS 管理控制台并导航到 EC2 仪表板。
- 选择运行 Airflow 的实例。
- 在实例详情窗格的底部，找到安全组部分并单击关联的安全组。
- 在安全组设置中，单击“入站规则”选项卡。
- 单击“编辑入站规则”并添加一条规则，允许来自您的 IP 地址或任何地方的 8080 端口的流量（生产环境不建议开放给任何地方）。
- 保存更改。

### 配置 Airflow 监听 8080 端口

- 通过 SSH 连接到您的 EC2 实例。
- 使用 cd 命令导航到 Airflow 配置目录：

```
[In]: cd airflow
```

- 使用文本编辑器（例如 Nano）编辑 airflow.cfg 文件：

```
[In]: nano airflow.cfg
```

- 在配置文件中找到 web_server_port 参数并将其设置为 8080：

```
[In]: web_server_port = 8080
```

- 保存更改并退出文本编辑器。
- 保存 airflow.cfg 文件的更改后，您需要重启 Airflow web 服务器以使更改生效。这通常可以通过停止并重启 Airflow web 服务器进程来完成。
- 您可以通过终止当前会话然后启动新会话来重启 Airflow web 服务器，方法如下：
  - 查找 Airflow web 服务器的进程 ID（PID）：

```
[In]: ps aux | grep 'airflow webserver'
```

  - 确定与 Airflow web 服务器进程关联的 PID。
  - 使用其 PID 终止 Airflow web 服务器进程：

```
[In]: kill <PID>
```





- 重新启动 Airflow Web 服务器：

```
[In]: airflow webserver &
```

## 基于 Docker 的部署

在 Docker 中运行 Apache Airflow 相比传统独立安装具有显著优势，它提供了一个简化且一致的环境，从而简化了设置过程，减少了配置错误，并增强了可移植性。Docker 将 Airflow 及其依赖项封装在容器内，确保了工作流在不同系统（无论是开发、测试还是生产环境）上的可靠执行。

要在 Docker 中设置 Apache Airflow，您需要安装 Docker 和 Docker Compose。Docker 将应用程序（包括所有必要的代码、库和依赖项）打包成容器，确保在不同环境中保持一致性。Docker Compose 通过允许您定义和管理多容器应用程序，进一步简化了这一过程，这对于像 Apache Airflow 这样复杂的设置特别有用，因为在这些设置中，Web 服务器、调度器、数据库等服务必须协同工作。

Apache Airflow 项目提供了一个官方的 `docker-compose.yml` 文件，该文件定义了所有必需的服务，包括用于工作流管理的 Airflow Web 服务器、用于任务执行的调度器、用于元数据存储的 Postgres、用于任务队列管理的 Redis，以及用于执行任务和触发延迟操作的 workers 和 triggerers。

在 Linux 操作系统（例如 Ubuntu）上安装 Docker 以进行测试的最简单方法是使用 Docker 提供的便利脚本，位于 `https://get.docker.com/`。在您的 EC2 实例上安装 Docker 后，您使用官方的 Docker Compose 配置来设置并运行 Airflow。

请遵循以下步骤：

### 步骤 1：创建脚本文件。

- 一旦您通过 SSH 连接到 EC2 实例，首先创建一个新的 shell 脚本文件：

```
[In]: nano install-docker.sh
```

- 将 Docker 提供的整个脚本内容复制并粘贴到该文件中。该脚本位于 https://get.docker.com/，用于自动化 Docker 安装过程。

### 步骤 2：使脚本可执行。

- 粘贴脚本后，按 Ctrl + X，然后按 Y，最后按 Enter 保存并关闭文件。
- 通过运行以下命令设置脚本为可执行：

```
[In]: chmod +x install-docker.sh
```

### 步骤 3：以 root 权限运行脚本。

- 执行脚本以管理员权限安装 Docker：

```
[In]: sudo ./install-docker.sh
```

- 脚本将检测您的 Linux 发行版和版本，然后相应地进行 Docker 安装。

### 步骤 4：验证 Docker 安装。

- 脚本完成后，运行以下命令验证 Docker 是否正确安装：

```
[In]: docker -version
```

- 您应该看到实例上安装的 Docker 版本，确认安装成功。

### 步骤 5：运行测试 Docker 容器。

- 为确保 Docker 正常工作，运行一个测试 Docker 容器：

```bash
[In]: sudo docker run hello-world
```

- 该命令将下载并运行一个测试镜像，如果成功，将显示确认消息。

### 步骤 6：安装 Docker Compose。

- 使用以下命令下载并安装 Docker Compose：

```bash
[In]: sudo curl -L \
         "https://github.com/docker/compose/releases/latest/download/" \
         "docker-compose-$(uname -s | tr '[:upper:]' '[:lower:]')" \
         "-$(uname -m)" -o /usr/bin/docker-compose
```

```bash
[In]: sudo chmod 755 /usr/bin/docker-compose
```

第一条命令从官方 GitHub 仓库下载最新版本的 Docker Compose 二进制文件，选择适合您系统的正确版本并将其保存为 /usr/bin/docker-compose。第二条命令通过设置适当的权限使 Docker Compose 二进制文件可执行。

- 通过检查 Docker Compose 的版本确认安装：

```
[In]: docker-compose -version
```

### 步骤 7：下载 Airflow Docker Compose 配置。

- Apache Airflow 提供了一个官方的 Docker Compose 设置，使运行 Airflow 变得轻松。下载 docker-compose.yaml 文件，该文件包含在 Docker 容器中运行 Airflow 及其相关服务（如 PostgreSQL 和 Redis）的配置：

```
[In]: curl -Lf0 \
'https://airflow.apache.org/docs/apache-airflow/' \
'2.7.2/docker-compose.yaml'
```

### 步骤 8：准备环境。

- 创建 Airflow 将用于 DAG、日志和插件的目录：

```
[In]: mkdir -p ./dags ./logs ./plugins
```

- 创建 .env 文件以设置必要的环境变量，包括您的用户 ID 和组 ID，以避免权限问题：

```
[In]: echo -e "AIRFLOW_UID=$(id -u)\nAIRFLOW_GID=0" > .env
```

### 步骤 9：初始化 Airflow 数据库。

- 运行以下命令初始化 Airflow 数据库：

```
[In]: docker compose up airflow-init
```

### 步骤 10：启动 Airflow 服务。

- 数据库初始化完成后，启动 Airflow Web 服务器、调度器和其他必要服务：

```
[In]: docker compose up -d
```

- 通过检查状态确保所有 Airflow 容器都在运行：

```
[In]: docker compose ps
```

### 步骤 11：访问 Airflow Web 界面。

- 获取您的 EC2 实例的公共 IP：
    - 您可以在 AWS 管理控制台中您的 EC2 实例详情下找到公共 IP。
- 在安全组中打开所需端口：
    - 默认情况下，Airflow 的 Web 服务器运行在 8080 端口。
    - 确保您的 EC2 实例关联的安全组中打开了 8080 端口。您可以在安全组中添加入站规则，允许来自您的 IP 地址的 8080 端口的流量。

入站规则示例：

- 类型：自定义 TCP 规则
- 协议：TCP
- 端口范围：8080
- 源：您的 IP（或 0.0.0.0/0 表示开放访问）

- 在您的浏览器中访问 Airflow：
    - 打开网络浏览器并导航至：

```
[In]: http://<your-ec2-public-ip>:8080
```

    - 将 `<your-ec2-public-ip>` 替换为您 EC2 实例的实际公共 IP。
    - 您应该能看到 Airflow 登录页面/Airflow 仪表板。

## 安装 JupyterLab

JupyterLab 是一个开源的基于 Web 的交互式开发环境 (IDE)，用于 Jupyter 笔记本、代码和数据。它提供了一种灵活且可扩展的架构，可用于处理多种编程语言（包括 Python）中的代码、数据和可视化。

以下是逐步说明，用于在 EC2 实例上安装和配置 JupyterLab：

### 步骤 1：安装 JupyterLab

- 连接到您的 EC2 实例并打开命令提示符。
- 激活您的虚拟环境：

```
[In]: source myenv/bin/activate
```

- 运行以下命令使用 pip 下载并安装 JupyterLab 及其依赖项：

```
[In]: pip install jupyterlab
```

### 步骤 2：生成 Jupyter Notebook 配置

- 运行以下代码生成 Jupyter Notebook 配置文件：

```
[In]: jupyter notebook --generate-config
```

生成 Jupyter Notebook 配置文件允许您自定义 Jupyter Notebook 环境的各个方面，例如指定默认设置、配置安全选项以及设置认证机制。

### 步骤 3：为 JupyterLab 设置密码

```
[In]: jupyter notebook password
```

### 步骤 4：启动 JupyterLab

- 运行以下命令在 8888 端口上启动 JupyterLab，并监听所有可用的 IP 地址：

```
[In]: jupyter lab --ip=0.0.0.0 --port=8888 --no-browser
```

### 步骤 5：配置安全组并访问 JupyterLab

- 更新安全组：确保您的 EC2 实例的安全组允许 8888 端口的入站流量。为此：
    - 前往 AWS 管理控制台中的 EC2 仪表板。
    - 在左侧菜单中，在 Network & Security 下选择 Security Groups。
    - 选择与您的 EC2 实例关联的安全组。
    - 点击 Inbound rules 选项卡，然后选择 Edit inbound rules。
    - 添加一条规则，允许来自您的 IP 或任何 IP（0.0.0.0/0，出于测试目的；出于安全原因，请谨慎使用此选项）的 8888 端口上的自定义 TCP 流量。
- 访问 JupyterLab：打开网络浏览器并导航至 `http://<your_ec2_instance_ip>:8888`。

现在，您应该能够使用您生成的密码在 EC2 实例上访问 Jupyter。

## 设置 Databricks 账户和工作区

如果您更喜欢使用 Databricks 对数据进行处理，以下步骤概述了创建 Databricks 账户、设置工作区以及将其与您的 AWS 账户连接的过程：

### 步骤 1：注册 Databricks

- 前往位于 https://www.databricks.com/ 的 Databricks 网站。
- 点击右上角的 “Try Databricks” 按钮。
- 填写创建账户所需的信息，包括您的名和姓、电子邮件地址、公司、职位和国家，并选择您的云提供商（在本例中为 AWS；其他为 Microsoft Azure 和 Google Cloud Platform）。




## 步骤 2：确认您的电子邮件。

- 注册后，请查看来自 Databricks 的验证邮件。
- 点击邮件中的验证链接以确认您的电子邮件地址。

## 步骤 3：登录 Databricks。

- 电子邮件确认后，使用您的凭据登录 Databricks 平台。

## 步骤 4：创建工作区。

- 登录后，系统将提示您创建一个 Databricks 工作区。
- 为您的工作区选择一个名称。
- 按照屏幕上的说明完成工作区的创建过程。

## 步骤 5：探索 Databricks。

- 工作区创建完成后，您可以开始探索 Databricks 环境。
- 熟悉工作区界面、笔记本及其他功能。

## 步骤 6：从 Databricks 访问 S3。

- 在使用 Databricks 时，可以使用不同的方法来访问 S3 存储桶。对于测试和快速搭建，您可以在 Databricks 中运行以下代码：

```python
ACCESS_KEY = "your-access-key"
SECRET_KEY = "your-secret-key"
AWS_BUCKET_NAME = "your-bucket-name"
MOUNT_NAME = "/mnt/datalake-central"
dbutils.fs.mount(
    source=f"s3a://{ACCESS_KEY}:{SECRET_KEY}@{AWS_BUCKET_NAME}/",
    mount_point=MOUNT_NAME,
    extra_configs={
        "fs.s3a.access.key": ACCESS_KEY,
        "fs.s3a.secret.key": SECRET_KEY
    }
)
```

此代码包含两个主要部分——变量赋值和挂载 S3 存储桶：

### 变量赋值

- ACCESS_KEY：从环境变量中获取 AWS 访问密钥。
- SECRET_KEY：从环境变量中获取 AWS 秘密密钥。
- AWS_BUCKET_NAME：存储您想要挂载的 S3 存储桶名称。
- MOUNT_NAME：指定 S3 存储桶的挂载点。在此示例中，挂载名称为“datalake-central”，但可以是任何名称。在挂载名称前加上 /mnt/ 是 Linux 环境中的常见约定，尤其是在挂载外部存储设备或网络共享时。

### 挂载 S3 存储桶

- dbutils.fs.mount：此函数用于挂载 S3 存储桶。它接受几个参数：
    - source：S3 存储桶的 URL，包括访问密钥和秘密密钥。这种格式允许 Databricks 使用提供的凭据对 S3 存储桶进行身份验证。
    - mount_point：S3 存储桶将挂载到的本地挂载点。
    - extra_configs：额外配置，在此情况下为 S3 存储桶的访问密钥和秘密密钥。extra_configs 参数为挂载操作提供额外的配置。此处，它再次包含访问密钥和秘密密钥，这是访问 S3 存储桶所必需的。

通过执行此代码，您将把指定的 S3 存储桶挂载到 Databricks 环境中的指定挂载点，从而可以像操作本地文件系统一样与该 S3 存储桶交互。

您可以按照以下方式从 AWS 管理控制台获取代码所需的访问密钥和秘密密钥：

- 前往 AWS 管理控制台 ([https://aws.amazon.com/console/](https://aws.amazon.com/console/)) 并使用您的 AWS 账户凭据登录。
- 登录后，在 AWS 管理控制台的服务列表中选择一个服务，导航至 IAM（身份和访问管理）服务。
- 在 IAM 控制台中，从左侧导航窗格中选择“Users”。
- 选择要为其创建访问密钥和秘密密钥对的 IAM 用户。
- 在“Security credentials”选项卡中，向下滚动至“Access keys”部分。
- 点击“Create access key”按钮。
- 在“Use case”下选择“Application running on an AWS compute service”，并在屏幕底部确认消息“I understand the above recommendation and want to proceed to create an access key”。
- 创建访问密钥后，您将看到访问密钥 ID 和秘密访问密钥。请记下这些凭据，因为它们只会显示一次。如果您丢失了它们，将需要创建一个新的访问密钥。
- 确保与访问密钥对关联的 IAM 用户或角色具有执行 S3 操作所需的权限。这可以通过附加适当的策略（如 AmazonS3FullAccess）来实现。

这种方法的一个问题是代码中硬编码凭据带来的安全风险，这可能导致意外泄露。另一个问题与维护有关：更新凭据需要修改代码，这可能很繁琐。

更好的解决方案是使用 IAM 角色，AWS 会安全地管理这些角色，无需在代码中指定访问 S3 所需的凭据。这种方法更加安全且易于扩展，尤其是在生产环境中。

IAM 角色是您可以创建并分配特定权限的 AWS 身份，允许受信任的实体（如运行 Databricks 的 EC2 实例）假设该角色并在 AWS 中执行操作。当将 IAM 角色附加到托管您的 Databricks 集群的 EC2 实例时，AWS 会自动为这些实例提供临时凭据。这些凭据由 AWS 轮换和管理，从而消除了在代码中嵌入访问密钥的需要。

请按照以下步骤在 Databricks 中设置和使用 IAM 角色：

## 步骤 1：创建具有 S3 访问权限的 IAM 角色。

- 登录 AWS 管理控制台并前往 IAM 服务。
- 创建一个新的角色：
    - 在左侧菜单中点击 Roles，然后点击 Create role。
    - 选择 EC2 作为受信任实体，因为该角色将由运行 Databricks 的 EC2 实例假设。
- 附加策略：
    - 将 AmazonS3FullAccess 策略附加到角色，或者创建一个根据您的需求定制特定 S3 权限的自定义策略。
- 完成角色创建：
    - 为角色命名（例如，DatabricksS3AccessRole）并完成创建过程。

## 步骤 2：将 IAM 角色附加到 Databricks 集群。

- 在 AWS 管理控制台中，导航至 EC2 仪表板。
- 识别组成您的 Databricks 集群的 EC2 实例。
- 附加 IAM 角色：
    - 选择每个实例，前往 Actions > Security > Modify IAM role，并附加您创建的 DatabricksS3AccessRole。

## 步骤 3：在 Databricks 中无需硬编码凭据即可访问 S3。

- 成功创建 IAM 角色并将其附加到您的 Databricks 集群后，现在您可以安全地访问您的 S3 存储桶，而无需硬编码任何凭据。以下代码片段演示了如何使用 IAM 角色挂载 S3 存储桶：

```python
AWS_BUCKET_NAME = "your-bucket-name"
MOUNT_NAME = "/mnt/datalake-central"
dbutils.fs.mount(
    source=f"s3a://{AWS_BUCKET_NAME}/",
    mount_point=MOUNT_NAME
)
```

您可以运行以下代码来测试挂载是否成功：

```python
MOUNT_NAME = "/mnt/datalake-central"
mounts = dbutils.fs.mounts()
mount_point_exists = any(
    mount.mountPoint == MOUNT_NAME for mount in mounts
)
if mount_point_exists:
    print("S3 bucket was successfully mounted.")
else:
    print("S3 bucket mount failed.")
```

`S3 bucket was successfully mounted.`

以下是每行代码的解析：

- MOUNT_NAME = “/mnt/datalake-central”：这行代码定义了一个名为 MOUNT_NAME 的变量，并将其赋值为“/mnt/datalake-central”。该变量存储在 Databricks 文件系统中 S3 存储桶挂载点的路径。
- mounts = dbutils.fs.mounts()：这行代码使用 dbutils.fs 模块中的 mounts() 函数获取 Databricks 环境中当前所有已挂载文件系统的列表。列表中的每一项代表一个已挂载的文件系统。
- mount_point_exists = any(mount.mountPoint == MOUNT_NAME for mount in mounts)：这行代码检查指定的挂载点是否存在于已挂载的文件系统中。它使用带有 any() 函数的生成器表达式，遍历每个已挂载的文件系统（mount），并检查其 mountPoint 属性是否与 MOUNT_NAME 变量中存储的值匹配。
- if mount_point_exists:：这行代码开始一个 if 语句，检查 mount_point_exists 变量是否为 True。如果指定的挂载点存在于已挂载的文件系统中，则条件评估为 True，if 语句内部的代码块将被执行。
- print(“S3 bucket was successfully mounted.”)：这行代码打印一条消息，指示 S3 存储桶已成功挂载。如果指定的挂载点存在于已挂载的文件系统中，则该行代码将被执行。




- else: 这行代码开始 else 代码块，当 if 语句中的条件（检查挂载点是否存在）评估为 False 时，该代码块将执行。换言之，如果指定的挂载点不存在于已挂载的文件系统列表中，则 else 语句内的代码块将会执行。

- print("S3 bucket mount failed."): 这行代码打印一条消息，表明 S3 存储桶的挂载操作失败。当指定的挂载点不存在于已挂载的文件系统列表中时，该代码会被执行。

现在，既然你已经成功使用 dbutils.fs.mount 函数将 S3 存储桶挂载到 Databricks 上，你便可以开始在 Databricks 内部对 S3 进行读写操作。下方的代码创建了一个塔可（taco）DataFrame，将其保存在挂载的 S3 存储桶中，然后再次读取它：

```python
[In]: data_to_write = [("Chicken Taco", 5.99),
                      ("Beef Taco", 6.49),
                      ("Vegetarian Taco", 4.99)]
[In]: df = spark.createDataFrame(data_to_write, ["Taco",
                                                "Price"])
[In]: df = df.repartition(1)
[In]: MOUNT_NAME = "/mnt/datalake-central"
[In]: df.write.mode("overwrite").parquet(
             MOUNT_NAME + "/taco_data_parquet"
             )
[In]: df_read = spark.read.parquet(MOUNT_NAME + "/taco_data_parquet")
[In]: df_read.show()
```

让我们来逐段解析代码的不同部分：

1. 创建 DataFrame：

```python
[In]: data_to_write = [("Chicken Taco", 5.99),
                      ("Beef Taco", 6.49),
                      ("Vegetarian Taco", 4.99)]
[In]: df = spark.createDataFrame(data_to_write,
                               ["Taco", "Price"])
```

这一部分创建了一个名为 df 的 DataFrame，其中包含塔可数据。它使用 spark.createDataFrame() 方法从元组列表 data_to_write 创建 DataFrame，其中每个元组包含一个塔可名称及其价格。列名“Taco”和“Price”在第二个参数中指定。

2. 保存 DataFrame：

```python
[In]: df = df.repartition(1)
[In]: MOUNT_NAME = "/mnt/datalake-central"
[In]: df.write.mode("overwrite").parquet(
              MOUNT_NAME + "/taco_data_parquet"
          )
```

这一部分使用 df.repartition(1) 将 DataFrame 重新分区为单个分区。Spark 中的分区是数据集的逻辑划分，允许并行处理。然后，它定义了挂载点 /mnt/datalake-central。最后，它使用 df.write.mode("overwrite").parquet() 将 DataFrame 保存为挂载的 S3 存储桶中名为“taco_data_parquet”的 Parquet 文件，如果存在现有文件则进行覆盖。

该文件将保存在 EC2 实例上的 S3 存储桶中，位于名为“taco_data_parquet/”的文件夹内，具体文件名如下：

```text
part-00000-tid-6689481035778156686-b47d6778-9a4c-48b3-950c-3ac770289ab1-453-1-c000.snappy.parquet
```

以及诸如“_SUCCESS”文件等其他文件，该文件指示写入操作已成功完成。snappy 文件包含实际数据，而其他文件属于 Spark 的内部处理过程，可以忽略。

3. 读取 DataFrame：

```python
[In]: df_read = spark.read.parquet(
       MOUNT_NAME + "/taco_data_parquet")
```

这一部分使用 spark.read.parquet() 将挂载的 S3 存储桶中的 Parquet 文件“taco_data_parquet”读回到一个名为 df_read 的 DataFrame 中。

4. 显示 DataFrame：

```python
[In]: df_read.show()
```

最后这一部分使用 show() 方法显示 DataFrame df_read 的内容。输出将显示具有"Taco"和"Price"列的 DataFrame 内容，如下所示：

| 塔可 (Taco) | 价格 (Price) |
| --- | --- |
| Chicken Taco | 5.99 |
| Beef Taco | 6.49 |
| Vegetarian Taco | 4.99 |

## 总结

在本章中，我们引导读者完成了在 Amazon Web Services (AWS) 上搭建深度学习环境以及配置必要工具和服务的过程。更具体地说，我们提供了关于如何创建 AWS 账户、配置 EC2 实例、设置 Amazon S3、创建项目目录、配置虚拟环境以及安装和配置依赖项（特别是 PySpark、PyTorch、TensorFlow、Airflow、Boto3 和 JupyterLab）的详细说明。我们还提供了关于如何设置 Databricks 账户和工作区的说明。

在下一章中，我们将介绍使用 PySpark 为深度学习任务准备数据的过程。我们将深入探讨数据探索、数据预处理、特征工程以及将数据格式化为 PyTorch 和 TensorFlow 兼容格式的关键方面。

# 第 3 章

## 使用 PySpark 为深度学习进行数据准备

本章介绍了使用 PySpark 为深度学习任务准备数据的过程。我们深入探讨了数据预处理、特征工程以及将数据格式化为 PyTorch 和 TensorFlow 兼容格式的关键方面。

数据预处理包括一系列旨在清洗和转换原始数据，使其适用于建模目的的步骤。这些步骤包括处理缺失值、缩放特征以及编码分类变量。为了说明这些概念，本章提供了代码示例，包括使用 VectorAssembler 组装特征向量，随后使用 StandardScaler 对其进行缩放。

特征工程在提升输入特征的质量和指导能力方面起着重要作用。它涉及创建新特征或转换现有特征，以封装更多信息。技术方法可能包括生成多项式特征、推导交互项以及处理日期时间特征（例如计算两个时间戳之间的差异或自特定事件以来经过的时间）。

此外，本章还涉及为深度学习任务格式化数据这一关键步骤。在预处理和特征工程之后，处理后的数据需要转换为与 PyTorch 和 TensorFlow 兼容的张量格式，以便这些框架能够高效处理。我们提供了代码示例，以说明如何将数据转换为 PyTorch 和 TensorFlow 张量，以及如何使用由数据加载器函数创建的 DataLoader 对象将数据组织为批次。

在深入探讨这些主题之前，重要的是首先要考虑 PySpark 的并行处理能力如何提高数据处理效率，特别是针对大型数据集。诸如重新分区、广播连接、缓存、使用高效的文件格式（如 Parquet）、优化 Shuffle 分区以及启用自适应查询执行 (AQE) 等技术，将在优化这些数据准备任务的性能方面发挥关键作用。

为了说明 PySpark 并行处理以及为大型数据集和深度学习准备数据这些概念，我们将使用一个包含特斯拉股票价格的历史数据集。该数据集将用于演示 PyTorch 和 TensorFlow 中的深度学习任务，特别是第 4 章和第 5 章分别涵盖的回归模型。

## 数据集

我们从 Yahoo! Finance 网站下载了 CSV 格式的特斯拉股票价格数据集，并使用以下链接将其存储在 AWS S3 存储桶中：

https://finance.yahoo.com/quote/TSLA/history/

让我们首先探索这个数据集，然后再使用它来说明 PySpark 如何为使用 PyTorch 和 TensorFlow 进行深度学习进行并行处理和数据准备。数据探索是理解数据集特征和模式的基础，并指导后续的预处理和特征工程步骤。我们的探索将包括打印数据集的前十行、执行描述性统计、检查缺失值以及可视化数据。通过这种使用 PySpark 的探索，我们获得了关于数据结构和分布的见解，为有效的深度学习数据准备奠定了基础。

我们首先导入脚本所需的库：

```python
[In]: import boto3
[In]: import matplotlib.pyplot as plt
[In]: from pyspark.sql import SparkSession
[In]: from pyspark.sql.functions import col
[In]: import pyspark.sql.functions as F
[In]: import numpy as np
```

以下是关于这些库的说明：

- boto3: 此库用于与 AWS 服务交互。它将在 copy_file_from_s3 函数中用于从 S3 存储桶下载特斯拉股票 CSV 文件。
- matplotlib.pyplot: 此库将用于在 visualize_data 方法中基于 DataFrame 创建可视化图表。
- 来自 pyspark.sql 的 SparkSession: 这是使用 DataFrame API 编程 Spark 的入口点。它将用于初始化以创建用于数据处理操作的 SparkSession 对象。
- 来自 pyspark.sql.functions 的 col: 此函数将在 check_for_null_values 方法中用于引用 DataFrame 列。




- `F from pyspark.sql.functions`：这是 `pyspark.sql.functions` 的别名。导入它是为了简化对 PySpark 函数的调用，该别名在多种方法中均有使用。

- `numpy as np`：这个库将用于数值运算以及调整可视化中的刻度位置。

接下来定义一个名为 DataProcessor 的类，旨在 SparkSession 环境中处理各种数据任务。在类内部，我们定义了几个方法，分别用于加载数据、执行描述性统计、检查空值以及可视化数据：

```python
class DataProcessor:
    def __init__(self, spark_session):
        self.spark = spark_session
```

- 在类定义中，有一个作为构造器的 `__init__` 方法。

- `__init__` 方法接收一个参数 `spark_session`，代表一个 SparkSession 对象。

- 在 `__init__` 方法内部，`self.spark` 属性被赋值为作为参数传入的 `spark_session` 对象。这种赋值确保 DataProcessor 类的每个实例都能访问到一个 SparkSession 对象。

在类内部，我们首先定义 `load_data` 方法，该方法设计用于使用 SparkSession 从 CSV 文件加载特斯拉股票价格数据：

```python
def load_data(self, file_path: str):
    """
    Load stock price data from a CSV file using
    SparkSession.
    """
    try:
        df = self.spark.read.csv(
            file_path,
            header=True,
            inferSchema=True
        )
        return df
    except Exception as e:
        print(f"Error loading data: {str(e)}")
    return None
```

- 该方法有两个参数：`self`，即类实例的引用；以及 `file_path`，一个表示包含特斯拉股票价格数据的 CSV 文件路径的字符串。

- 由三引号包围的文档字符串（docstring）简要说明了该方法的目的，即使用 SparkSession 从 CSV 文件加载股票价格数据。

- 该方法以 `try` 代码块开始，表示内部代码将被执行，且任何发生的异常都会被捕获和处理。

- 在 `try` 代码块内部，该方法使用 SparkSession 对象（`self.spark`）的 `read.csv` 方法读取由 `file_path` 参数指定的 CSV 文件。提供参数 `header=True` 和 `inferSchema=True`，分别指定 CSV 文件的第一行包含列标题，以及根据列的数据类型推断 DataFrame 的 schema。

- 如果数据成功加载，方法返回包含股票价格数据的 DataFrame。如果在数据加载过程中发生异常（例如，文件未找到、文件格式无效），方法会捕获异常并执行 `except` 代码块内的代码。

- 在 `except` 代码块中，打印一条指示错误性质的错误消息，并返回 `None` 以表明数据加载过程未成功。

随后，类内部的 `print_first_n_rows` 方法打印 DataFrame 的前 `n` 行：

```python
def print_first_n_rows(self, df, n=10):
    """Print the first n rows of the DataFrame."""
    print(f"First {n} rows of the DataFrame:")
    df.show(n)
```

- 该方法有三个参数：`self`，即类实例的引用；`df`，需要打印其前 `n` 行的 DataFrame；以及 `n`，一个表示要打印行数的整数（默认为 10）。

- 文档字符串简要说明了该方法的目的，即打印 DataFrame 的前 `n` 行。

- 该方法开始时先打印一条消息，指示将要打印的行数，使用 f-string 格式化包含 `n` 的值。

- 调用 DataFrame（`df`）的 `show` 方法，并传入参数 `n`，该参数指定了要显示的行列数。

继续推进，`calculate_descriptive_statistics` 方法计算 DataFrame 的描述性统计量：

```python
def calculate_descriptive_statistics(self, df):
    """Calculate descriptive statistics of the
    DataFrame."""
    print("Descriptive Statistics:")
    df.summary().show()
```

- 该方法有两个参数：`self`，即类实例的引用；以及 `df`，需要计算其描述性统计量的 DataFrame。

- 文档字符串简要说明了该方法的目的，即计算 DataFrame 的描述性统计量。

- 该方法开始时先打印一条消息，表明正在计算描述性统计量。

- 调用 DataFrame（`df`）的 `summary` 方法。该方法计算包括计数、平均值、标准差以及最小值和最大值在内的摘要统计量。

继续 DataProcessor 类中的数据探索方法，下面的 `visualize_data` 方法基于 DataFrame 创建可视化：

```python
def visualize_data(self, df):
    """Create visualizations based on DataFrame."""
    print("Data Visualization:")
    try:
        df_pd = df.toPandas()
        plt.figure(figsize=(10, 6))
        plt.plot(df_pd['Date'], df_pd['Close'])
        plt.xlabel('Date')
        plt.ylabel('Closing Price')
        plt.title('Tesla Stock Closing Prices Over Time')
        plt.xticks(rotation=45, ha='right')
        plt.gca().invert_xaxis()
        plt.xticks(
            np.arange(
                0,
                len(df_pd['Date']),
                step=max(len(df_pd['Date']) // 10, 1)
            )
        )
        plt.show()
    except Exception as e:
        print(f"Error visualizing data: {str(e)}")
```

- 该方法有两个参数：`self`，即类实例的引用；以及 `df`，需要从中创建可视化的 DataFrame。

- 文档字符串简要说明了该方法的目的，即基于 DataFrame 创建可视化。

- 该方法开始时先打印一条消息，表明正在执行数据可视化。

- 在 `try` 代码块内部，该方法使用 `toPandas` 方法将 Spark DataFrame（`df`）转换为 Pandas DataFrame（`df_pd`）。这种转换对于使用 Matplotlib 绘图是必需的。

- 随后使用 Matplotlib 创建特斯拉股票收盘价随时间变化的折线图。调用 `plt.plot` 函数，以 `df_pd['Date']` 作为 x 轴数据，`df_pd['Close']` 作为 y 轴数据。

- 该方法设置了图表的各种属性，如 x 轴和 y 轴的标签、标题，以及调整 x 轴刻度的旋转角度以增强可读性。

- 使用 `plt.gca().invert_xaxis()` 反转 x 轴，以确保日期按时间顺序显示。

- 使用 `plt.xticks` 调整 x 轴上的刻度位置，以改善可读性。此行代码确保 x 轴上大约有十个刻度。

- 最后，使用 `plt.show()` 显示图表。

- 如果在数据可视化过程中发生异常（例如，绘图数据无效），方法会捕获异常并执行 `except` 代码块内的代码。它会打印一条指示错误性质的错误消息。

进入下一步，`check_for_null_values` 方法检查 DataFrame 中的缺失值：

```python
def check_for_null_values(self, df):
    """Check for null values in the DataFrame."""
    print("Null Value Check:")
    
    null_counts = df.select([col(c).isNull()\
        .cast("int").alias(c) for c in df.columns])\
        .agg(*[F.sum(c).alias(c) for c in df.columns])\
        .toPandas()
    
    print(null_counts)
```

- 该方法有两个参数：`self`，即类实例的引用；以及 `df`，需要检查其中空值的 DataFrame。

- 文档字符串简要说明了该方法的目的，即检查 DataFrame 中的空值。

- 该方法开始时先打印一条消息，表明正在执行空值检查。

- 在单行代码中，该方法使用一系列 Spark DataFrame 操作来计算每一列的空值数量：

    - `df.select(...)`：选择 DataFrame 的列。

    - `[col(c).isNull().cast("int").alias(c) for c in df.columns]`：构造一个列表推导式，迭代 DataFrame 列中的每一列（`c`）。对于每一列，创建一个表达式将空值转换为整数（空值为 1，非空值为 0），并将结果别名为该列名。

    - `.agg(*[F.sum(c).alias(c) for c in df.columns])`：使用 `sum` 函数聚合每一列的空值数量。列表推导式前的 `*` 用于将该列表推导式解包为 `agg` 函数的独立参数。





- `toPandas()`：该方法将结果 DataFrame 转换为 Pandas DataFrame，以便于展示和分析结果。将 DataFrame 转换为 Pandas 格式可以使其与 Pandas 生态系统无缝集成，从而让用户能够利用其丰富的功能进行进一步的分析和可视化。

- 包含每列空值计数的结果 DataFrame 被存储在 `null_counts` 变量中。

- 随后打印 `null_counts` DataFrame 以显示每列的空值计数。

接下来讨论 `DataProcessor` 类之外的函数，我们有 `copy_file_from_s3` 函数，它用于将 CSV 文件从 S3 存储桶复制到 EC2 实例上的本地文件路径：

```python
[In]: def copy_file_from_s3(
        bucket_name: str,
        file_key: str,
        local_file_path: str
        ):
        """
        Copy file from S3 bucket to local file path.
        """
        try:
            s3 = boto3.client('s3')
            s3.download_file(bucket_name, file_key, local_file_path)
            print(f"File downloaded from S3 bucket {bucket_name} "
                  f"to local file path: {local_file_path}")
        except Exception as e:
            print(f"Error copying file from S3: {str(e)}")
```

- 在函数内部，使用 try-except 块来处理文件复制过程中可能出现的任何潜在错误。

- 在 try 块中
  - 使用 `boto3.client('s3')` 方法创建了一个 S3 客户端对象（`s3`）。此客户端提供对 Amazon S3 服务的访问权限。
  - 然后调用 `s3.download_file()` 方法，将文件从指定的 S3 存储桶（`bucket_name`）和键（`file_key`）下载到本地文件路径（`local_file_path`）。
  - 文件成功下载后，会打印一条确认消息，指示源 S3 存储桶和目标本地文件路径。
  - 如果在文件复制过程中发生异常（例如，由于网络问题或权限不正确），它将被 except 块捕获。
  - 在 except 块中
    - 打印一条错误消息，指示文件复制过程中发生错误的性质。这有助于诊断和排查出现的问题。

继续看主函数，这是脚本的主入口点。它初始化 SparkSession，从 S3 复制文件，初始化 DataProcessor，加载数据，并执行数据处理任务：

```python
[In]: def main(s3_bucket_name: str, s3_file_key: str, local_file_path: str):
    """
    Main function for stock price prediction.

    This function initializes a SparkSession, copies
    a file from an S3 bucket to a local file path,
    initializes a DataProcessor object, loads data
    from the local file, and performs various data
    processing tasks.

    :param s3_bucket_name:
        Name of the S3 bucket containing the file
    :param s3_file_key:
        Key of the file within the S3 bucket
    :param local_file_path:
        Local file path to save the downloaded file
    """
    spark = (SparkSession.builder
        .appName("StockPricePrediction")
        .getOrCreate())

    copy_file_from_s3(
        s3_bucket_name,
        s3_file_key,
        local_file_path
    )

    data_processor = DataProcessor(spark)
    df = data_processor.load_data(local_file_path)
    if df is not None:
        data_processor.print_first_n_rows(df)
        data_processor.calculate_descriptive_statistics(df)
        data_processor.check_for_null_values(df)
        data_processor.visualize_data(df)
    else:
        print("Error loading data. Exiting.")
```

- 该函数接受三个参数：`s3_bucket_name`、`s3_file_key` 和 `local_file_path`，分别代表包含文件的 S3 存储桶的名称、文件在 S3 存储桶中的键以及保存下载文件的本地文件路径。

- 在函数内部
  - 使用 `SparkSession.builder` 方法创建了一个 SparkSession 对象，应用名称为 “StockPricePrediction”。如果已经存在 SparkSession，则会重用该会话；否则，将创建一个新会话。
  - 调用 `copy_file_from_s3` 函数，将文件从指定的 S3 存储桶（`s3_bucket_name`）和键（`s3_file_key`）复制到本地文件路径（`local_file_path`）。
  - 使用之前创建的 SparkSession 初始化了一个 DataProcessor 对象。
  - 使用 DataProcessor 的 `load_data` 方法从本地文件加载数据。如果 DataFrame 加载成功（`df is not None`），则使用 DataProcessor 对象的方法执行各种数据处理任务：
    - 打印 DataFrame 的前 n 行（`print_first_n_rows`）
    - 计算 DataFrame 的描述性统计量（`calculate_descriptive_statistics`）
    - 检查 DataFrame 中的空值（`check_for_null_values`）
    - 基于 DataFrame 创建可视化（`visualize_data`）
  - 如果在数据加载过程中发生错误，将打印错误消息，并显示 “Error loading data. Exiting.”（加载数据时出错。正在退出。）消息终止程序。

进入最后一步，条件块检查该脚本是否作为主程序直接运行。它设置 S3 存储桶名称、文件键和本地文件路径的参数，然后使用这些参数调用主函数：

```python
[In]: if __name__ == "__main__":
    s3_bucket_name = 'instance1bucket'
    s3_file_key = 'TSLA_stock.csv'
    local_file_path = '/home/ubuntu/airflow/dags/TSLA_stock.csv'
    main(s3_bucket_name, s3_file_key, local_file_path)
```

- 在该块内部，定义了三个变量：
  - `s3_bucket_name`：一个字符串变量，表示文件所在的 S3 存储桶的名称
  - `s3_file_key`：一个字符串变量，表示文件在 S3 存储桶中的键
  - `local_file_path`：一个字符串变量，表示文件将被下载的本地文件路径

- 使用这些变量作为参数调用主函数。该函数协调整个数据处理过程，包括初始化 `SparkSession`、从 S3 存储桶复制文件、加载数据以及执行各种数据处理任务。

通过将代码封装在主函数中并条件性地执行，该脚本可以作为一个模块被导入到其他脚本中，而不会执行主功能。这增强了代码的可复用性和模块化。然而，当在第 8 章中将脚本作为有向无环图（DAG）在 Airflow 中运行时，不需要主函数，因为 Airflow 负责协调 DAG 内任务的执行。DAG 中的每个任务可以利用脚本中的特定函数或类，而无需执行主功能。

要运行该脚本，我们首先将其保存为 `tesla_stock_exploration.py`，激活 EC2 实例上的虚拟环境，然后使用以下命令运行 Python 脚本：

```bash
[In]: cd /home/ubuntu
[In]: source myenv/bin/activate
[In]: python3 tesla_stock_exploration.py
```

让我们现在检查代码的输出。

第一个输出是由 `copy_file_from_s3` 函数产生的消息，表明 CSV 文件已成功从 S3 存储桶下载到本地文件路径：

```text
[Out]: File downloaded from S3 bucket instance1bucket to local file
path: /home/ubuntu/airflow/dags/TSLA_stock.csv
```

第二个输出是由 `print_first_n_rows` 方法生成的包含 DataFrame 前 10 行的表格。这显示了特斯拉股票的 Date、Open、High、Low、Close 和 Volume 列。打印前 10 个观察值提供了一种简单有效的方法来快速概览数据集，并在进行更详细的分析或处理之前验证一切正常：

| 日期 | 开盘 | 最高 | 最低 | 收盘 | 成交量 |
|---|---|---|---|---|---|
| 2024/2/23 | 195.31 | 197.57 | 191.50 | 191.97 | 78,670,300 |
| 2024/2/22 | 194.00 | 198.32 | 191.36 | 197.41 | 92,739,500 |
| 2024/2/21 | 193.36 | 199.44 | 191.95 | 194.77 | 103,844,000 |
| 2024/2/20 | 196.13 | 198.60 | 189.13 | 193.76 | 104,545,800 |
| 2024/2/16 | 202.06 | 203.17 | 197.40 | 199.95 | 111,173,600 |
| 2024/2/15 | 189.16 | 200.88 | 188.86 | 200.45 | 120,831,800 |
| 2024/2/14 | 185.30 | 188.89 | 183.35 | 188.71 | 81,203,000 |
| 2024/2/13 | 183.99 | 187.26 | 182.11 | 184.02 | 86,759,500 |
| 2024/2/12 | 192.11 | 194.73 | 187.28 | 188.13 | 95,498,600 |
| 2024/2/09 | 190.18 | 194.12 | 189.48 | 193.57 | 84,476,300 |




第三个输出是数据集中每个数值列的汇总统计量，由 DataProcessor 类中的 `calculate_descriptive_statistics` 方法生成：

| 统计项 | 开盘价    | 最高价    | 最低价     | 收盘价   | 成交量    |
|---------|---------|---------|---------|---------|-----------|
| 数量   | 1,258   | 1,258   | 1,258   | 1,258   | 1,258     |
| 平均值    | 176.37  | 180.31  | 172.10  | 176.31  | 133,933,068 |
| 标准差  | 105.44  | 107.68  | 102.90  | 105.28  | 85,052,921  |
| 最小值     | 12.07   | 12.45   | 11.80   | 11.93   | 29,401,800  |
| 25%     | 57.20   | 59.10   | 55.59   | 57.63   | 81,203,000  |
| 50%     | 202.59  | 208.00  | 198.50  | 203.33  | 109,536,700 |
| 75%     | 251.45  | 256.59  | 246.35  | 251.92  | 157,577,100 |
| 最大值     | 411.47  | 414.50  | 405.67  | 409.97  | 914,082,000 |

该输出提供了数据集中数值数据的综合摘要，包括集中趋势、离散程度和分布度的度量。它有助于理解数据的整体特征和变异性。

以下是对这些数据的解读：

- **数量**：每个数值列都有 1,258 个观测值。
- **平均值**：每个数值列的平均值如下：
  - 开盘价：176.4
  - 最高价：180.3
  - 最低价：172.1
  - 收盘价：176.3
  - 成交量：133,933,068
- **标准差**：每个数值列的标准差值如下：
  - 开盘价：105.4
  - 最高价：107.7
  - 最低价：102.9
  - 收盘价：105.3
  - 成交量：85,052,921

这些标准差值表示每列数据相对于平均值的偏差或分散程度。标准差越大，意味着数据的分散性越高；标准差越小，则表明分散性越低。

- **最小值**：每个数值列的最小值如下：
  - 开盘价：12.1
  - 最高价：12.5
  - 最低价：11.8
  - 收盘价：11.9
  - 成交量：29,401,800
- **第 25 百分位数 (Q1)**：每个数值列的第 25 百分位数值如下：
  - 开盘价：57.2
  - 最高价：59.1
  - 最低价：55.6
  - 收盘价：57.6
  - 成交量：81,203,000

这些百分位数值指示了数据的分布情况。例如，开盘价列的第 25 百分位数为 57.2，这意味着该列中 25% 的数据点低于此值。

- **第 50 百分位数 (中位数或 Q2)**：每个数值列的中位数值如下：
  - 开盘价：202.6
  - 最高价：208.0
  - 最低价：198.5
  - 收盘价：203.3
  - 成交量：109,536,700

这些中位数值反映了每列数据的集中趋势。换句话说，它们代表了将数据集分为两等份的数值。中位数常被称为第 50 百分位数，因为它将数据集分为相等的两部分，其中 50% 的数据点低于此值，50% 高于此值。

- **第 75 百分位数 (Q3)**：每个数值列的第 75 百分位数值如下：
  - 开盘价：251.5
  - 最高价：256.6
  - 最低价：246.4
  - 收盘价：251.9
  - 成交量：157,577,100

这些百分位数值反映了每列内部数据的分布情况。具体来说，第 75 百分位值代表低于该值的数据点占该列数据总量的 75%。第 75 百分位数常用于统计分析中，以了解数据的分散程度或变异性，特别是相对于中位数和其他四分位数的关系。

- **最大值**：每个数值列的最大值如下：
  - 开盘价：411.5
  - 最高价：414.5
  - 最低价：405.7
  - 收盘价：409.9
  - 成交量：914,082,000

下一个输出由 `check_for_null_values` 方法生成，表明数据集中的每一列均不存在空值：

| 日期 | 开盘价 | 最高价 | 最低价 | 收盘价 | 成交量 |
| --- | --- | --- | --- | --- | --- |
| 0 | 0 | 0 | 0 | 0 | 0 |

处理空值是机器学习中的一个关键环节，因为缺失数据可能会显著影响模型的性能和准确性。通常使用填充技术来处理缺失值。一种简单的方法是均值/中位数/众数填充，即用相应列的均值、中位数或众数来替换缺失值。

预测性填充涉及使用机器学习模型根据数据集中的其他特征来预测并填补缺失值。该方法可以提供更准确的填充结果，但需要额外的建模工作。

删除策略涉及移除包含缺失值的数据。当缺失值的比例较小时，使用行删除；移除包含缺失数据的行，这种方法简单但如果处理不当可能会导致有价值信息的丢失。如果某列缺失值比例很高且对分析不重要，则可采用列删除。这种方法简化了数据集，但可能会丢弃潜在有用的信息。

特征工程也可以在处理缺失数据方面发挥作用。创建二进制指示变量来标记缺失值的存在，有助于模型学习与缺失数据相关的模式。这种技术使模型能够考虑到数据缺失的事实，并潜在地利用这些信息改进预测。

特斯拉股价数据集中所有列均无缺失值是一个积极指标，表明数据集在缺失数据方面是完整的。由于没有空值需要处理，因此无需立即对包含缺失值的行或列进行填充或删除。没有空值简化了数据预处理阶段，并增强了后续分析或建模任务可靠性的信心。

最后一个输出是由 `visualize_data` 方法生成的股价随时间变化的收盘价图表（图 3-1）。

![](img/1c89d4486f90c87568fa6a42d46ae02a_151_0.png)

图 3-1. 特斯拉股价收盘价

将目标变量随时间绘制作为数据探索的一部分，提供了数据的可视化摘要，有助于识别模式和异常值，并指导后续的建模决策，最终实现更有依据、更有效的预测建模。在我们的情况下，绘制实际收盘价为我们评估预测模型的性能提供了有价值的参考点，正如我们将在第 4 章和第 5 章中看到的。当我们使用深度学习模型生成预测时，我们可以将预测的收盘价叠加在与实际收盘价相同的图表上。这使我们能够直观地比较模型预测值随时间与实际值的吻合程度。

## PySpark 的并行处理

在 PySpark 中，并行处理通过将任务分解为并发运行的独立子任务来提高计算的效率和速度。这是通过跨多个数据分区分配处理来实现的。在集群的多个核心和节点上分配计算的能力，使得能够快速处理大型数据集。

为了说明如何优化并行性，我们首先关注重新分区技术。为此，让我们修改特斯拉股价探索代码，移除那些对于展示该技术影响并非必需的功能，例如计算描述性统计量、数据可视化和检查空值。我们还将添加功能，打印重新分区前后的分区数量，以突出其对数据分布的影响，并包含一个步骤，将 DataFrame 重新分区为指定数量的分区（例如，10 个），展示此操作如何潜在提升数据处理性能。

首先，下面的代码添加了打印重新分区前后分区数量的功能：

```python
[In]: def print_partition_info(self, df):
       """打印 DataFrame 中的分区数量。"""
       num_partitions = df.rdd.getNumPartitions()
       print(f"number of partitions: {num_partitions}")
```

此代码使用 DataFrame 底层 RDD（弹性分布式数据集）上的 `getNumPartitions()` 方法获取并显示特斯拉股价 DataFrame 中的分区数量。这有助于我们理解重新分区前后数据是如何分布在各个分区中的。

为了将 DataFrame 重新分区为指定数量的分区（例如，10 个），我们如更新特斯拉股价探索代码中的主函数如下：

```python
[In]: def main(
           s3_bucket_name: str,
           s3_file_key: str,
           local_file_path: str
       ):
       ...
       # 打印初始分区信息
       data_processor.print_partition_info(df)

       # 重新分区 DataFrame
       repartitioned_df = df.repartition(10)
       print("After repartitioning:")
       data_processor.print_partition_info(repartitioned_df)

       # 打印重新分区后的
       # DataFrame 的前几行
       data_processor.print_first_n_rows(repartitioned_df)
```




现在主函数包含在重新分区之前和之后打印分区信息的步骤。`data_processor.print_partition_info(df)` 方法显示重新分区之前的分区数量。随后，使用 `df.repartition(10)` 将 DataFrame 重新分区为十个分区，重新分配数据以潜在地提高性能或更好地管理数据分布。最后，打印更新后的分区信息以显示重新分区的效果。

以下是使用特斯拉股票价格数据集进行重新分区的完整代码：

```python
import boto3
from pyspark.sql import SparkSession

class DataProcessor:
  def __init__(self, spark_session):
    self.spark = spark_session

  def load_data(self, file_path: str):
    """
    使用 SparkSession 从 CSV 文件加载股票价格数据。
    """
    try:
      df = self.spark.read.csv(
        file_path, header=True, inferSchema=True
      )
      return df
    except Exception as e:
      print(f"Error loading data: {str(e)}")
      return None

  def print_first_n_rows(self, df, n=10):
    """Print the first n rows of the DataFrame."""
    print(f"First {n} rows of the DataFrame:")
    df.show(n)

  def print_partition_info(self, df):
    """Print the number of partitions in the DataFrame."""
    num_partitions = df.rdd.getNumPartitions()
    print(f"Initial number of partitions: {num_partitions}")

def copy_file_from_s3(
        bucket_name: str,
        file_key: str,
        local_file_path: str
        ):
    """
    Copy file from S3 bucket to local file path.
    """
    try:
        s3 = boto3.client('s3')
        s3.download_file(bucket_name, file_key, local_file_path)
        print(
            f"File downloaded from S3 bucket {bucket_name} to "
            f"local file path: {local_file_path}"
        )
    except Exception as e:
        print(f"Error copying file from S3: {str(e)}")

def main(
        s3_bucket_name: str,
        s3_file_key: str,
        local_file_path: str
        ):
    """
    Main function to demonstrate repartitioning of stock price data.

    This function initializes a SparkSession, copies a file from an S3 bucket to a local file path, initializes a DataProcessor object, loads data from the local file, prints partition info, repartitions the DataFrame, and prints partition info again.

    :param s3_bucket_name: Name of the S3 bucket containing the file
    :param s3_file_key: Key of the file within the S3 bucket
    :param local_file_path: Local file path to save the downloaded file
    """
    # Initialize SparkSession
    spark = SparkSession.builder \
            .appName("StockPriceRepartitioning") \
            .getOrCreate()

    # Copy file from S3 bucket
    copy_file_from_s3(
        s3_bucket_name,
        s3_file_key,
        local_file_path
    )

    # Initialize DataProcessor
    data_processor = DataProcessor(spark)

    # Load data
    df = data_processor.load_data(local_file_path)
    if df is not None:
        # Print initial partition info
        data_processor.print_partition_info(df)

        # Repartition the DataFrame
        repartitioned_df = df.repartition(10)
        print("After repartitioning:")
        data_processor.print_partition_info(repartitioned_df)

        # Print the first few rows of the repartitioned DataFrame
        data_processor.print_first_n_rows(repartitioned_df)
    else:
        print("Error loading data. Exiting.")

if __name__ == "__main__":
    s3_bucket_name = 'instance1bucket'
    s3_file_key = 'TSLA_stock.csv'
    local_file_path = '/home/ubuntu/airflow/dags/TSLA_stock.csv'
    main(s3_bucket_name, s3_file_key, local_file_path)
```

**输出：**

```text
Initial number of partitions: 1

After repartitioning:
number of partitions: 10

First 10 rows of the DataFrame:

| Date     | Open   | High   | Low    | Close  | Volume     |
|----------|--------|--------|--------|--------|------------|
| 9/26/19  | 15.38  | 16.22  | 15.16  | 16.17  | 178267500  |
| 8/25/22  | 302.36 | 302.96 | 291.60 | 296.07 | 53230000   |
| 9/13/23  | 270.07 | 274.98 | 268.10 | 271.30 | 111673700  |
| 11/26/19 | 22.35  | 22.37  | 21.81  | 21.93  | 119211000  |
| 5/17/21  | 191.85 | 196.58 | 187.07 | 192.28 | 97171200   |
| 6/4/19   | 12.07  | 12.93  | 11.97  | 12.91  | 207112500  |
| 4/3/19   | 19.15  | 19.74  | 19.14  | 19.45  | 118791000  |
| 6/23/21  | 210.67 | 219.07 | 210.01 | 218.86 | 93297600   |
| 11/20/20 | 166.00 | 167.50 | 163.02 | 163.20 | 98735700   |
| 12/22/20 | 216.00 | 216.63 | 204.74 | 213.45 | 155148000  |
```

在这个示例中，初始 DataFrame 只有一个分区，随后被重新分区为十个分区。由于只有一个分区，并行处理受到限制，因为 Spark 每次只能处理一个数据块。如果集群有更多可用的核心，它们可能会利用率不足，因为只执行了一个任务。通过使用 `repartition(10)` 函数将分区数从一增加到十，特斯拉股票价格数据被重新分配到十个分区中，使每个分区变得更小。Spark 现在可以并行执行多达十个任务。这意味着同时处理了更多数据，从而减少了完成分析所需的总时间。

可以使用 `Coalesce` 根据工作负载和数据特征来优化分区数量。例如，下面的代码将之前重新分区的 DataFrame 的分区数从十减少到五：

```python
coalesced_df = repartitioned_df.coalesce(5)
data_processor.print_partition_info(coalesced_df)
```

在重新分区过程中，PySpark 会在分区之间交换数据，这通常是时间和资源上昂贵的操作。这些交换的次数由 `spark.sql.shuffle.partitions` 配置定义。默认情况下，在 Spark 3.x 中设置为 200，但可以根据数据大小和集群可用资源进行调整。下面的代码显示了如何设置交换分区数量：

```python
spark.conf.set("spark.sql.shuffle.partitions", "20")
```

还有其他技术可以提高 PySpark 中的性能和并行性。其中之一是将重新分区的 DataFrame 保存为 Parquet 格式：

```python
repartitioned_df.write.parquet("/home/ubuntu/airflow/dags/tesla_stock.parquet")
```

将重新分区的 DataFrame 缓存以保持其在内存中以便在后续操作中更快访问，是另一种帮助提高性能的技术：

```python
repartitioned_df.cache()
```

当对同一个 DataFrame 执行多个操作时，这特别有用，因为它避免了每次使用时重新计算 DataFrame。

在 PySpark 中处理大型数据集时，另一种提高性能的技术是广播。这涉及有效地将大型 DataFrame（例如 `repartitioned_df`）与较小的 DataFrame（例如 `small_df`）进行连接：

```python
from pyspark.sql.functions import broadcast

small_df = spark.createDataFrame([
        ("2023-08-25", 5.5),
        ("2023-08-26", 6.0),
    ],
    ["Date", "AdditionalData"])

# Broadcast join
joined_df = repartitioned_df.join(
        broadcast(small_df),
        on="Date",
        how="left"
    )
```

广播较小的 DataFrame 允许 Spark 将其分发到所有工作节点，从而避免了常规连接所需的交换操作。对于涉及大型和小型数据集的连接，这可以显著提高性能。

在 PySpark 中处理大型数据集时，将大型数据集保存为 Parquet 格式是另一种提高性能的方法，因为 Parquet 支持压缩和优化的读取操作。将 DataFrame 保存为 Parquet 格式有助于减少存储空间，并由于其优化的布局而提高读取速度。

下面的代码将重新分区的特斯拉股票价格数据集保存为 Parquet 格式：

```python
repartitioned_df.write.parquet(
        "/home/ubuntu/airflow/dags/tesla_stock.parquet")
```

最后，启用自适应查询执行（AQE）可以根据运行时统计信息优化查询执行。它可以通过优化连接策略或根据实际处理的数据调整交换分区数量等决策来调整查询计划，从而提高性能。




# 第 3 章 使用 PySpark 为深度学习准备数据

`[In]: spark.conf.set("spark.sql.adaptive.enabled", "true")`

**注意** 自适应查询执行（AQE）主要与 Apache Spark 中的 SQL 操作相关，特别是在使用 DataFrame 和 Spark SQL API 时。但是，由于 PySpark 中的 DataFrame API 是建立在 Spark SQL 之上的抽象层，因此您对 DataFrame 执行的大多数操作（如 groupBy、join、agg 等）在内部都会转换为 SQL 查询。因此，AQE 也可以优化这些操作。

下面是结合了上述技术更新后的特斯拉股价重新分区脚本：

```python
[In]: import boto3
[In]: from pyspark.sql import SparkSession
[In]: from pyspark.sql.functions import broadcast

[In]: class DataProcessor:
    def __init__(self, spark_session):
        self.spark = spark_session

    def load_data(self, file_path: str):
        try:
            df = self.spark.read.csv(
                file_path,
                header=True,
                inferSchema=True
            )
            return df
        except Exception as e:
            print(f"Error loading data: {str(e)}")
            return None

    def print_first_n_rows(self, df, n=10):
        print(f"First {n} rows of the DataFrame:")
        df.show(n)

    def print_partition_info(self, df):
        num_partitions = df.rdd.getNumPartitions()
        print(f"Number of partitions: {num_partitions}")

    def copy_file_from_s3(
        bucket_name: str,
        file_key: str,
        local_file_path: str
    ):
        try:
            s3 = boto3.client('s3')
            s3.download_file(bucket_name, file_key, local_file_path)
            print(f"File downloaded from S3 bucket {bucket_name} to local file path: {local_file_path}")
        except Exception as e:
            print(f"Error copying file from S3: {str(e)}")

    def main(
        s3_bucket_name: str,
        s3_file_key: str,
        local_file_path: str
    ):
        spark = SparkSession.builder \
            .appName("StockPriceOptimization") \
            .config("spark.sql.adaptive.enabled", "true") \
            .config("spark.sql.shuffle.partitions", "20") \
            .getOrCreate()

        copy_file_from_s3(
            s3_bucket_name,
            s3_file_key,
            local_file_path
        )
        data_processor = DataProcessor(spark)
        df = data_processor.load_data(local_file_path)

        if df is not None:
            data_processor.print_partition_info(df)

            # Repartition the DataFrame
            repartitioned_df = df.repartition(10)
            data_processor.print_partition_info(repartitioned_df)

            # Coalesce partitions
            coalesced_df = repartitioned_df.coalesce(5)
            data_processor.print_partition_info(coalesced_df)

            # Example broadcast join
            small_df = spark.createDataFrame([
                ("2023-08-25", 5.5),
                ("2023-08-26", 6.0),
            ], ["Date", "AdditionalData"])
            joined_df = repartitioned_df.join(
                broadcast(small_df), on="Date", how="left")

            # Save as Parquet
            repartitioned_df.write.parquet(
                "/home/ubuntu/airflow/dags/tesla_stock.parquet"
            )

            # Print the first few rows
            data_processor.print_first_n_rows(repartitioned_df)
        else:
            print("Error loading data. Exiting.")

[In]: if __name__ == "__main__":
        s3_bucket_name = 'instance1bucket'
        s3_file_key = 'TSLA_stock.csv'
        local_file_path = '/home/ubuntu/airflow/dags/TSLA_stock.csv'
        main(s3_bucket_name, s3_file_key, local_file_path)
```

### 使用 PySpark 为 PyTorch 准备数据

在探索了特斯拉股票数据集并演示了如何提高 PySpark 的并行处理能力之后，我们现在可以开始审视深度学习框架的数据准备主题，首先重点关注 PyTorch。具体而言，我们将考察如何使用 PySpark 进行数据预处理、特征工程和数据格式化。我们通过导入必要的模块开始，然后演示数据准备过程的每个步骤：

```python
[In]: import logging
[In]: from pyspark.sql import SparkSession
[In]: from pyspark.ml.feature import VectorAssembler, StandardScaler
[In]: from pyspark.sql import DataFrame
[In]: import numpy as np
[In]: import torch
[In]: from torch.utils.data import DataLoader, TensorDataset
[In]: import boto3
```

这段代码导入了执行数据准备任务和与 S3 交互所需的模块和库。具体来说：

-   **logging**：logging 模块将在整个代码中用于记录程序执行期间的消息、警告和错误。
-   **来自 pyspark.sql 的 SparkSession**：SparkSession 将在 load_data() 函数中用于创建 SparkSession 对象，以读取 CSV 数据并创建 DataFrame 对象。
-   **来自 pyspark.ml.feature 的 VectorAssembler 和 StandardScaler**：这些将在 preprocess_data() 函数中用于特征工程。VectorAssembler 将原始特征列组装为单个特征向量列，而 StandardScaler 将输入特征缩放为均值零且标准差为一。
-   **来自 pyspark.sql 的 DataFrame**：DataFrame 将在整个代码中广泛使用，以表示和操作表格格式的数据。
-   **numpy as np**：NumPy 将用于将 Spark DataFrame 列转换为 NumPy 数组，以便进一步处理。
-   **torch 以及来自 torch.utils.data 的 DataLoader 和 TensorDataset**：这些将在 create_data_loader() 函数中用于创建 PyTorch DataLoader 以进行批处理。DataLoader、TensorDataset 和 torch 将用于处理张量（tensors）并创建数据加载器，以便在模型训练期间高效地加载数据。
-   **boto3**：Boto3 将在 copy_file_from_s3() 函数中用于与 AWS S3 交互，并从指定的 S3 存储桶下载文件到本地文件路径。

在下一步中，我们为 Python 脚本设置日志记录：

```python
[In]: logging.basicConfig(level=logging.INFO)
[In]: logger = logging.getLogger(__name__)
```

-   **logging.basicConfig(level=logging.INFO)**：这行代码配置日志记录系统。它将日志级别设置为 INFO，这意味着只有严重程度为 INFO 及以上级别的消息才会被记录。其他可能的级别包括 DEBUG、WARNING、ERROR 和 CRITICAL。
-   **logger = logging.getLogger(name)**：这行代码创建一个名为 logger 的记录器对象。name 变量表示当前模块的名称。当 Python 直接执行脚本（作为主程序）时，name 被设置为 “main”。然而，当脚本作为模块被另一个脚本导入时，name 被设置为该模块的名称。这允许模块在记录消息时识别自身。默认情况下，此记录器设置为日志记录层级的根记录器。它允许从代码库的不同部分记录消息并独立控制其行为。可以使用 logger.info()、logger.warning() 和 logger.error() 等方法使用 logger 记录消息。

继续向下，我们定义了一个名为 load_data 的函数，它使用 SparkSession 从 CSV 文件加载特斯拉股价数据。该函数接受文件路径作为输入并返回一个 DataFrame：

以下是该功能实现的详细说明：

-   **def load_data(file_path: str) -> DataFrame**：这行定义了函数 load_data，包含一个类型为 str 的参数 file_path。返回注解 -> DataFrame 表示该函数返回一个 DataFrame 对象。
-   **"""Load stock price data from a CSV file using SparkSession."""**：这是一个文档字符串，简要描述了该函数的功能。
-   **spark = SparkSession.builder**：这行使用 builder 方法创建一个名为 spark 的 SparkSession 对象。SparkSession 是 PySpark 中 Spark 功能的入口点。
-   **.appName("StockPricePrediction")**：这将应用程序名称设置为 "StockPricePrediction"。该名称将在 Spark UI 中可见。





- `.getOrCreate()`: 此方法用于获取一个现有的 SparkSession，如果不存在则创建一个新的 SparkSession。
- `df = spark.read.csv(file_path, header=True, inferSchema=True)`: 这一行使用 spark.read.csv 方法读取位于指定 file_path 处的 CSV 文件。它设置 header=True 以表明 CSV 文件的第一行包含列名，并设置 inferSchema=True 以自动推断各列的数据类型。
- `return df`: 最后，函数返回包含从 CSV 文件加载的数据的 DataFrame df。

进入下一步，我们定义一个名为 `preprocess_data` 的函数，该函数接受一个 DataFrame `df` 作为输入并返回一个 DataFrame。该函数通过组装特征向量（使用 VectorAssembler）、进行缩放（使用 StandardScaler）以及执行特征工程来处理数据：

```python
[In]: def preprocess_data(df: DataFrame) -> DataFrame:
    """
    Preprocess the data by assembling feature vectors
    using VectorAssembler, scaling them using
    StandardScaler, and performing feature engineering.
    """
    assembler = VectorAssembler(
        inputCols=['Open', 'High', 'Low', 'Volume'],
        outputCol='features'
    )
    df = assembler.transform(df)
    logger.info(
        "First 5 observations after assembling features:")
    df.show(5, truncate=False)
    df = perform_feature_engineering(df)
    logger.info(
        "First 5 observations after feature engineering:")
    df.show(5, truncate=False)
    scaler = StandardScaler(
        inputCol="features",
        outputCol="scaled_features",
        withStd=True, withMean=True)
    scaler_model = scaler.fit(df)
    df = scaler_model.transform(df)
    df = df.select('scaled_features', 'Close')
    return df
```

- `def preprocess_data(df: DataFrame) -> DataFrame:`: 这一行定义了函数 preprocess_data，它有一个类型为 DataFrame 的参数 df。返回注解 -> DataFrame 表明该函数返回一个 DataFrame 对象。
- `"""Preprocess the data by assembling feature vectors using VectorAssembler, scaling them using StandardScaler, and performing feature engineering."""`: 这是一个 docstring（文档字符串），提供了对该函数功能的简要描述。
- `assembler = VectorAssembler(inputCols=['Open', 'High', 'Low', 'Volume'], outputCol='features')`: 这一行创建一个名为 assembler 的 VectorAssembler 对象，并指定了输入列（'Open'、'High'、'Low'、'Volume'）和输出列名称 'features'。VectorAssembler 将多个列合并为一个单独的向量列。
- `df = assembler.transform(df)`: 这一行对 DataFrame df 应用 VectorAssembler，创建一个名为 'features' 的新列，其中包含组装好的特征向量。
- `logger.info("First 5 observations after assembling features:")`: 此日志记录一条信息消息，表明将显示组装特征后的前五个观测值。
- `df.show(5, truncate=False)`: 这一行显示 DataFrame df 在组装特征后的前五个观测值，且不截断列值。
- `df = perform_feature_engineering(df)`: 这一行通过调用 perform_feature_engineering 函数对 DataFrame df 应用额外的特征工程步骤。
- `logger.info("First 5 observations after feature engineering:")`: 此日志记录一条信息消息，表明将显示特征工程后的前五个观测值。
- `df.show(5, truncate=False)`: 这一行显示 DataFrame df 在特征工程后的前五个观测值，且不截断列值。
- `scaler = StandardScaler(inputCol="features", outputCol="scaled_features", withStd=True, withMean=True)`: 这一行创建一个名为 `scaler` 的 `StandardScaler` 对象，并指定了输入列（`"features"`）、输出列（`"scaled_features"`）以及缩放选项（`withStd=True`、`withMean=True`）。
- `scaler_model = scaler.fit(df)`: 这一步将 `StandardScaler` 拟合到 DataFrame `df`，从而创建一个缩放器模型。
- `df = scaler_model.transform(df)`: 这一行使用缩放器模型对 DataFrame `df` 进行转换，对 `'features'` 列进行缩放，并将缩放后的值存储在一个名为 `'scaled_features'` 的新列中。
- `df = df.select('scaled_features', 'Close')`: 这一行从 DataFrame `df` 中选择 `'scaled_features'` 和 `'Close'` 列。
- `return df`: 最后，函数返回经过预处理的 DataFrame `df`。

继续到下一步，我们定义一个名为 `perform_feature_engineering` 的函数，该函数接受一个 DataFrame `df` 作为输入并返回一个 DataFrame。该函数执行特征工程操作以增强数据的预测能力。它向 DataFrame `df` 添加新列，以捕获来自现有特征的相关信息，包括：

- **价格区间交互：** 代表最高价（High）与最低价（Low）之间的差值
- **价格变动交互：** 代表收盘价（Close）与开盘价（Open）之间的差值
- **成交量–价格交互：** 代表成交量（Volume）与收盘价（Close）的乘积

```python
[In]: def perform_feature_engineering(df: DataFrame) -> DataFrame:
    """
    Perform feature engineering operations to enhance the data's predictive power.

    This function adds new columns to the DataFrame df to capture relevant information from existing features, including:

    - Price Range Interaction:
        Represents the difference between High and Low prices.

    - Price Change Interaction:
        Represents the difference between Close and Open prices.

    - Volume-Price Interaction:
        Represents the product of Volume and Close prices.

    Parameters:

    df (DataFrame):
        The input DataFrame containing the raw data.

    Returns:

    DataFrame:
        The DataFrame df with additional engineered features.
    """

    df = df.withColumn('price_range', df['High'] - df['Low'])

    df = df.withColumn('price_change', df['Close'] - df['Open'])

    df = df.withColumn(
        'volume_price_interaction',
        df['Volume'] * df['Close']
    )

    return df
```

- `def perform_feature_engineering(df: DataFrame) -> DataFrame:`: 这一行定义了函数 perform_feature_engineering，它有一个类型为 DataFrame 的参数 df。返回注解 -> DataFrame 表明该函数返回一个 DataFrame 对象。
- `"""Perform feature engineering operations to enhance the data's predictive power...""":`: 这是一个 docstring，提供了对该函数功能的简要描述。
- `df = df.withColumn('price_range', df['High'] - df['Low']):`: 这一行为 DataFrame df 添加一个名为 'price_range' 的新列，该列代表 'High'（最高价）和 'Low'（最低价）价格之间的差值。它使用 PySpark 的 withColumn 函数来实现这一点。
- `df = df.withColumn('price_change', df['Close'] - df['Open']):`: 这一行为 DataFrame df 添加另一个名为 'price_change' 的新列，该列代表 'Close'（收盘价）和 'Open'（开盘价）价格之间的差值。
- `df = df.withColumn('volume_price_interaction', df['Volume'] * df['Close']):`: 这一行为 DataFrame df 添加第三个名为 'volume_price_interaction' 的新列，该列代表 'Volume'（成交量）和 'Close'（收盘价）的乘积。
- `return df`: 最后，函数返回在执行完特征工程操作后的 DataFrame df。

为了继续，我们定义了 `print_first_5_observations` 函数，该函数打印 DataFrame 的前五行，并带有一个自定义标题：

```python
[In]: def print_first_5_observations(df: DataFrame, heading: str):
    """
    Print the first 5 observations of the DataFrame with a
    custom heading.
    """
    logger.info(heading)
    df.show(5, truncate=False)
```

- `df: DataFrame`: 包含要打印的数据的 DataFrame。
- `heading: str`: 在打印 DataFrame 之前显示的自定义标题。
- `logger.info(heading)`: 使用 logger.info() 函数记录自定义标题。此标题为打印的 DataFrame 提供上下文信息。
- `df.show(5, truncate=False)`: 在 DataFrame df 上调用 show() 方法，参数为 5 和 `truncate=False`。该方法显示 DataFrame 的前五行，且不会截断任何列的值。





随后，我们定义 `convert_to_tensor` 函数，该函数负责将特征和标签转换为 PyTorch 张量：

```python
In]: def convert_to_tensor(features, labels):
    """
    Convert features and labels to PyTorch tensors.
    """
    tensor_features = torch.tensor(
        features,
        dtype=torch.float32
    )
    tensor_labels = torch.tensor(labels, dtype=torch.float32)
    return tensor_features, tensor_labels
```

- `features`：需要转换为 PyTorch 张量的特征数据。
- `labels`：需要转换为 PyTorch 张量的标签数据。
- `convert_to_tensor` 函数使用 PyTorch 库中的 `torch.tensor()` 函数将特征和标签转换为 PyTorch 张量。
- `dtype=torch.float32` 参数指定结果张量的数据类型应为 32 位浮点数。
- 转换后的张量分别赋值给变量 `tensor_features` 和 `tensor_labels`。
- 最后，该函数返回一个元组 `(tensor_features, tensor_labels)`，其中 `tensor_features` 是包含转换后特征的 PyTorch 张量，`tensor_labels` 是包含转换后标签的 PyTorch 张量。

继续往下，我们定义 `create_data_loader` 函数，该函数负责为数据的批量处理创建一个 PyTorch `DataLoader` 对象：

```python
In: def create_data_loader(features, labels, batch_size):
    """
    Create a Pytorch DataLoader for batch processing.
    """
    tensor_features, tensor_labels = convert_to_tensor(
        features,
        labels
    )
    dataset = TensorDataset(tensor_features, tensor_labels)
    data_loader = DataLoader(
        dataset,
        batch_size=batch_size,
        shuffle=True
    )
    return data_loader
```

`create_data_loader` 函数具有以下参数：

- `features`：要包含在 DataLoader 中的特征数据
- `labels`：要包含在 DataLoader 中的相应标签数据
- `batch_size`：处理数据的期望批次大小

就功能而言：

- 该函数首先调用 `convert_to_tensor()` 函数将特征和标签转换为 PyTorch 张量。
- 使用转换后的张量，它创建一个 PyTorch `TensorDataset`，这是一个将特征和标签一起保持的数据集包装器。
- `TensorDataset` 允许在训练期间对数据批次进行迭代。
- 最后，该函数创建一个 PyTorch `DataLoader` 对象，有助于从数据集中迭代数据批次。
- `batch_size` 参数指定每个批次中的样本数量，而 `shuffle=True` 参数确保在每个 epoch 之前对数据进行打乱，以防止模型学习序列模式。

`create_data_loader` 函数返回一个 PyTorch `DataLoader` 对象，可用于训练或验证过程。此函数对于在深度学习模型训练期间高效处理大型数据集至关重要。它支持批量处理，有助于加快训练过程并优化内存使用。

在下一步中，我们定义 `copy_file_from_s3` 函数，该函数负责将文件从 Amazon S3 存储桶复制到本地文件路径：

```python
In]: def copy_file_from_s3(
             bucket_name: str,
             file_key: str,
             local_file_path: str
             ):
             """
Copy file from S3 bucket to local file path.
"""
s3 = boto3.client('s3')
s3.download_file(bucket_name, file_key, local_file_path)
logger.info(
    f"File downloaded from S3 bucket {bucket_name}"
    f"to local file path: {local_file_path}"
)
```

以下是对该函数参数和功能的解释：

参数：

- `bucket_name`：要从中复制文件的 S3 存储桶名称
- `file_key`：文件在 S3 存储桶内的键（或路径）
- `local_file_path`：复制文件保存到的本地文件路径

功能：

- 该函数首先使用 `boto3` 库创建与 Amazon S3 服务的连接。
- 然后，它使用 S3 客户端的 `download_file` 方法，从给定的 S3 存储桶（`bucket_name`）和文件键（`file_key`）下载指定文件到指定的本地文件路径（`local_file_path`）。
- 文件成功下载后，它使用 `logger` 对象记录一条信息消息，指示文件已从 S3 存储桶下载到本地文件路径。

该函数没有显式返回任何值，但它执行了上述描述的文件复制操作。此函数用于检索存储在 Amazon S3 存储桶中的文件，并将其引入本地环境以进行进一步处理或分析。它可以用于各种场景，例如下载机器学习任务的数据集、获取配置文件或在不同的存储系统之间传输数据。

继续数据准备流程，我们定义主函数，该函数作为脚本或应用程序的入口点：

```python
[In]: def main():
        s3_bucket_name = 'instance1bucket'
        s3_file_key = 'TSLA_stock.csv'
        local_file_path = '/home/ubuntu/airflow/dags/TSLA_stock.csv'
        copy_file_from_s3(
        s3_bucket_name,
        s3_file_key,
        local_file_path
        )
        df = load_data(local_file_path)
        print_first_5_observations(df, "First 5 observations:")
        df = preprocess_data(df)
        print_first_5_observations(
        df,
        "First 5 observations after scaling:"
        )
        df_features = np.array(
        df.select('scaled_features')
        .rdd.map(lambda x: x.scaled_features.toArray())
        .collect()
)
df_labels = np.array(
    df.select('Close')
    .rdd.map(lambda x: x.Close)
    .collect()
)

batch_size = 32
train_loader = create_data_loader(
    df_features,
    df_labels,
    batch_size
)

logger.info(
    "First 5 observations after scaling"
    "and converting to tensors:"
)
print(train_loader.dataset[:5])
```

这个主函数协调整个数据准备过程，从将数据文件从 S3 存储桶复制到本地存储，到预处理数据，将其转换为适合模型训练的格式，最后创建一个用于高效批量处理的 `DataLoader`。让我们逐一检查这些步骤：

### 从 S3 存储桶复制文件

- 该函数指定了 S3 存储桶的名称（`s3_bucket_name`）、桶内文件的键（`s3_file_key`）以及文件将被复制到的本地文件路径（`local_file_path`）。
- 然后，它调用 `copy_file_from_s3` 函数将文件从指定的 S3 存储桶复制到本地文件路径。

### 加载数据

- 该函数使用 `load_data` 函数从本地文件路径（`local_file_path`）加载数据，并将其赋值给 DataFrame 变量 `df`。

### 打印前五个观察值

- 该函数使用 `print_first_5_observations` 函数和自定义标题“First 5 observations:”打印 DataFrame（`df`）的前五个观察值。

### 预处理数据

- 该函数通过调用 `preprocess_data` 函数对加载的数据进行预处理，并将预处理后的 DataFrame 重新赋值给 `df`。
- 预处理后，它再次使用自定义标题“First 5 observations after scaling:”打印 DataFrame 的前五个观察值。

### 将数据转换为 NumPy 数组

- 该函数将包含缩放特征和‘Close’值的 Spark DataFrame 列转换为 NumPy 数组（分别为 `df_features` 和 `df_labels`）。
- 这些数组将用作训练模型的输入特征和标签。

### 创建 DataLoader

- 该函数使用 `create_data_loader` 函数创建一个用于批量处理的 PyTorch `DataLoader`（`train_loader`）。此 `DataLoader` 将在模型训练期间用于迭代训练数据批次。

### 打印作为张量的前五个观察值

- 该函数记录一条信息消息，指示将打印缩放并转换为张量后的前五个观察值。
- 然后，它打印 `DataLoader` 数据集的前五个观察值。

在数据准备的最终过程中，我们有一个条件语句，用于检查脚本是作为主程序运行还是作为模块导入到另一个脚本中：

```python
[In]: if __name__ == "__main__":
    main()
```

如果脚本被直接执行（即作为主程序），条件 `__name__ == "__main__"` 求值为 `True`，并且 `if` 语句内部的代码块被执行。如果脚本作为模块导入到另一个脚本中，条件 `__name__ == "__main__"` 求值为 `False`，并且 `if` 语句内部的代码块不被执行。在此上下文中，当脚本直接运行时，会调用 `main()`，这意味着主函数将被执行，从而启动数据准备过程。这种结构允许脚本既可以直接运行，也可以作为模块导入到其他脚本中，而不会导致非预期的副作用。





要运行该脚本，我们首先需要将其保存为 `pyspark_pytorch_preparation.py`，在 EC2 实例上激活虚拟环境，然后使用以下命令运行它：

```
[In]: cd /home/ubuntu
[In]: source myenv/bin/activate
[In]: python3 pyspark_pytorch_preparation.py
```

现在让我们检查代码的输出。

第一个输出由 `print_first_5_observations` 函数生成，展示了 DataFrame 的前五个观察值：

| 日期 | 开盘价 | 最高价 | 最低价 | 收盘价 | 成交量 |
|---|---|---|---|---|---|
| 2/23/24 | 195.31 | 197.57 | 191.50 | 191.97 | 78,670,300 |
| 2/22/24 | 194.00 | 198.32 | 191.36 | 197.41 | 92,739,500 |
| 2/21/24 | 193.36 | 199.44 | 191.95 | 194.77 | 103,844,000 |
| 2/20/24 | 196.13 | 198.60 | 189.13 | 193.76 | 104,545,800 |
| 2/16/24 | 202.06 | 203.17 | 197.40 | 199.95 | 111,173,600 |

该表格由六列组成：日期、开盘价、最高价、最低价、收盘价和成交量。每一行代表一个特定日期，每一列代表特斯拉股票在该日期的不同属性。此输出提供了从 CSV 文件加载的原始数据在应用任何预处理或特征工程之前的初步视图。理解数据的初始结构和内容对于识别任何初步趋势或模式以及决定适当的预处理步骤至关重要。

第二个输出由 `preprocess_data` 函数生成，显示了组装特征后的前五个观察值：

| 日期 | 开盘价 | 最高价 | 最低价 | 收盘价 | 成交量 | 特征 |
|:--|:--|:--|:--|:--|:--|:--|
| 2/23/24 | 195.31 | 197.57 | 191.50 | 191.97 | 78,670,300 | [195.31, 197.57, 191.50, 78670300] |
| 2/22/24 | 194.00 | 198.32 | 191.36 | 197.41 | 92,739,500 | [194.00, 198.32, 191.36, 92739500] |
| 2/21/24 | 193.36 | 199.44 | 191.95 | 194.77 | 103,844,000 | [193.36, 199.44, 191.95, 103844000] |
| 2/20/24 | 196.13 | 198.60 | 189.13 | 193.76 | 104,545,800 | [196.13, 198.60, 189.13, 104545800] |
| 2/16/24 | 202.06 | 203.17 | 197.40 | 199.95 | 111,173,600 | [202.06, 203.17, 197.40, 111173600] |

以下是表中每一列的解释：

- 日期：股票价格观察的日期。
- 开盘价：该日期股票的开盘价格。
- 最高价：该日期交易时段内股票的最高价格。
- 最低价：该日期交易时段内股票的最低价格。
- 收盘价：该日期股票的收盘价格。
- 成交量：该日期股票的成交量（交易股数）。
- 特征：此列代表每个观察值组装后的特征向量。特征是从‘开盘价’、‘最高价’、‘最低价’和‘成交量’列中提取的，并合并为单个向量。向量中的每个元素对应这些特征之一。例如，第一行表明在 2024 年 2 月 23 日，股票开盘价为 195.31 美元，最高价达到 197.57 美元，最低价跌至 191.50 美元，收盘价为 191.97 美元，成交量为 78,670,300 股。与此观察值对应的特征向量是 [195.31, 197.57, 191.50, 78,670,300]。同样，后续的行表示随后日期的股票价格观察值及其相应的特征向量。

在 PySpark 中使用 `VectorAssembler` 组装特征向量通过整合多个输入列为一个向量列简化了工作流。这种整合简化了特征工程过程，便于在数据集中管理和操作特征。此外，利用 Spark 的分布式计算能力，`VectorAssembler` 能够实现高效的数据处理，特别适用于处理大规模数据集。通过组装特征向量，Spark 可以在集群中的多个节点上并行化计算，从而提高处理速度和可扩展性。

第三个输出显示了特征工程后的前五个观察值。由于开盘价、最高价、最低价、收盘价、成交量和特征列与之前的表格相同，为清晰起见，我们已省略它们。相反，此表重点关注新添加的列：

| 日期 | ... | 价格区间 | 价格变化 | 成交量-价格交互 |
| :--- | :--- | :--- | :--- | :--- |
| 2/23/24 | ... | 6.07 | -3.34 | 15,102,337,569.07 |
| 2/22/24 | ... | 6.96 | 3.41 | 18,307,705,065.98 |
| 2/21/24 | ... | 7.49 | 1.41 | 20,225,696,295.38 |
| 2/20/24 | ... | 9.47 | -2.37 | 20,256,793,685.27 |
| 2/16/24 | ... | 5.77 | -2.11 | 22,229,160,986.48 |

# 第 3 章 使用 PySpark 为深度学习进行数据准备

以下是表中每个新列的解释：

- price_range：表示最高价与最低价之间的差值
- price_change：表示收盘价与开盘价之间的差值
- volume_price_interaction：表示成交量与收盘价的乘积

让我们使用 2/23/24 的数据，分解这些新列是如何生成的：

价格区间：

- 197.57 − 191.50 = 6.07

价格变化：

- 191.97 − 195.31 = −3.34

成交量-价格交互：

- 78,670,300 × 191.97 = 15,102,337,569.07

这些工程特征中的每一个都可以提供有价值的信息，从而增强预测特斯拉股价模型的预测性能：

- 价格区间可以提供关于股票波动性的见解。较高的价格区间可能表明市场不确定性时期或显著的价格波动，而较低的价格区间可能暗示相对稳定性。纳入此特征允许模型捕捉价格变动的幅度，这对于预测未来的价格变化非常有价值。
- 价格变化提供了关于交易时段内价格变动方向的信息。正的价格变化表明股票收盘价高于开盘价，而负的价格变化则表明相反。通过包含此特征，模型可以捕捉日内价格动态以及投资者情绪或市场势头的潜在趋势。
- 成交量与收盘价之间的交互反映了相对于价格变动的交易活动水平。高成交量伴随着显著的价格变化可能表明强烈的市场参与和投资者对股票的兴趣。相反，低成交量伴随价格变化可能暗示弱势的市场情绪或缺乏投资者信心。通过纳入此特征，模型可以考虑交易活动与价格动态之间的相互作用，这可以提供关于市场行为和潜在价格变动的额外见解。

下一个输出显示了缩放后的前五个观察值：

| scaled_features | 收盘价 |
| --- | --- |
| [0.1796, 0.1602, 0.1885, -0.6497] | 191.97 |
| [0.1672, 0.1672, 0.1872, -0.4843] | 197.41 |
| [0.1612, 0.1776, 0.1929, -0.3538] | 194.77 |
| [0.1874, 0.1698, 0.1655, -0.3455] | 193.76 |
| [0.2437, 0.2123, 0.2459, -0.2676] | 199.95 |

此表显示了缩放后的特征以及缩放后前五个观察值对应的收盘价。scaled_features 列包含特征的缩放值，而 Close 列包含相应的收盘价格。

缩放是数据准备中的重要步骤，因为它确保特征处于相似的尺度，使其更适合模型训练。缩放后的特征表示为 0 到 1 之间的值，这有助于更一致和有效的建模。最终，缩放有助于提高模型的性能、稳定性和可解释性，从而从数据中得出更准确的预测和见解。

最终输出显示了缩放并转换为张量后的前五个观察值。Features 列包含缩放后的特征值，而 Close 列包含相应的收盘价格：

| Features | Close |
| :--- | :--- |
| [0.1797, 0.1602, 0.1885, -0.6497] | 191.97 |
| [0.1672, 0.1672, 0.1872, -0.4843] | 197.41 |
| [0.1612, 0.1776, 0.1929, -0.3538] | 194.77 |
| [0.1874, 0.1698, 0.1655, -0.3455] | 193.76 |
| [0.2437, 0.2123, 0.2459, -0.2676] | 199.95 |

由于我们在这里所做的仅仅是将数据转换为张量，因此这与上一个表中的输出相同。输出保持不变，因为将数据转换为张量不会改变其值；它只是将数据结构更改为适合使用 PyTorch 处理的格式。

将数据转换为张量使我们能够以适合使用 PyTorch 训练深度学习模型的格式准备输入特征和目标变量。尽管数据的值保持不变



# 使用 PySpark 为 TensorFlow 进行数据准备

到目前为止，代码专门针对 PyTorch 设计。然而，通过一些小的修改，例如将 PyTorch 特有的函数替换为 TensorFlow 的等价函数，可以将其改编以适配 TensorFlow 的深度学习任务。

下面的代码演示了这一修改过程，展示如何使用 PySpark 为 TensorFlow 执行数据预处理、特征工程和数据格式化。我们首先导入必要的模块，然后逐步演示数据准备过程的每一个步骤：

```python
import logging

from pyspark.sql import SparkSession

from pyspark.ml.feature import VectorAssembler, StandardScaler

from pyspark.sql import DataFrame

import numpy as np

import tensorflow as tf

from tensorflow.keras.utils import to_categorical

import boto3
```

- `logging`：日志记录模块将在整个代码中使用，以记录程序执行期间的消息、警告和错误。
- 来自 `pyspark.sql` 的 `SparkSession`：`SparkSession` 将在 `load_data()` 函数中使用，用于创建 SparkSession 对象以读取 CSV 数据并创建 DataFrame 对象。
- 来自 `pyspark.ml.feature` 的 `VectorAssembler` 和 `StandardScaler`：这些将在 `preprocess_data()` 函数中用于特征工程。`VectorAssembler` 将原始特征列组装为单个特征向量列，而 `StandardScaler` 则将输入特征缩放为零均值和单位标准差。
- 来自 `pyspark.sql` 的 `DataFrame`：DataFrame 将在整个代码中广泛使用，以表示和操作表格格式的数据。
- `numpy as np`：NumPy 将在将 Spark DataFrame 列转换为 NumPy 数组以进行进一步处理的过程中使用。
- `tensorflow as tf`：TensorFlow 将在 `create_data_loader()` 函数中使用，以创建用于批量处理的 TensorFlow Dataset。
- `boto3`：Boto3 将在 `copy_file_from_s3()` 函数中使用，以与 AWS S3 交互并从指定的 S3 存储桶下载文件到本地文件路径。

在下一步中，我们设置日志记录：

```python
logging.basicConfig(level=logging.INFO)
logger = logging.getLogger(__name__)
```

- 这些行配置日志记录系统，以输出级别为 INFO 或更高的日志消息。然后为当前脚本创建一个名为 `logger` 的日志记录器对象。

接下来，我们创建 `load_data` 函数，该函数使用 SparkSession 从 CSV 文件加载特斯拉股价数据：

```python
def load_data(file_path: str) -> DataFrame:
    """
    Load stock price data from a CSV file using SparkSession.
    """
    spark = (SparkSession.builder
             .appName("StockPricePrediction")
             .getOrCreate())
    df = spark.read.csv(
        file_path,
        header=True,
        inferSchema=True
    )
    return df
```

- 该函数接受一个字符串类型的单个参数 `file_path`，并返回一个 DataFrame 对象。
- 使用三引号包围的文档字符串提供了对函数目的的简要描述，即使用 SparkSession 从 CSV 文件加载股价数据。
- 在函数内部，使用构建器模式创建了一个名为 `spark` 的 SparkSession 对象。调用构建器方法以初始化 SparkSession 配置。`appName` 方法将应用程序名称设置为 "StockPricePrediction"。最后，`getOrCreate()` 确保重用现有的 SparkSession 或在需要时创建新的 SparkSession。
- 该函数使用 SparkSession `spark` 从位于指定 `file_path` 的 CSV 文件中读取数据。它利用 `read.csv` 方法读取 CSV 文件，其中 `header=True` 表示第一行包含列标题，而 `inferSchema=True` 指示 Spark 自动推断列的数据类型。
- 将数据加载到名为 `df` 的 DataFrame 后，函数返回该 DataFrame。返回的 DataFrame 包含从 CSV 文件加载的特斯拉股价数据，可在程序中进行进一步处理或分析。

随后，我们定义 `preprocess_data` 函数，通过组装特征向量、缩放特征和进行特征工程来预处理输入 DataFrame。该函数使用 PySpark 的 `VectorAssembler` 和 `StandardScaler` 来执行这些任务：

```python
def preprocess_data(df: DataFrame) -> DataFrame:
    """
    Preprocess the data by assembling feature vectors using VectorAssembler, scaling them using StandardScaler, and performing feature engineering.
    """
    assembler = VectorAssembler(
        inputCols=['Open', 'High', 'Low', 'Volume'],
        outputCol='features'
    )
    df = assembler.transform(df)
    logger.info(
        "First 5 observations after assembling features:"
    )
    df.show(5, truncate=False)

    df = perform_feature_engineering(df)

    logger.info(
        "First 5 observations after feature engineering:"
    )
    df.show(5, truncate=False)

    scaler = StandardScaler(
        inputCol="features",
        outputCol="scaled_features",
        withStd=True, withMean=True
    )

    scaler_model = scaler.fit(df)

    df = scaler_model.transform(df)

    df = df.select('scaled_features', 'Close')

    return df
```

- 该函数接受一个 DataFrame `df` 作为输入，并在预处理后返回一个 DataFrame。
- 文档字符串提供了对函数目的的简要描述，即通过组装特征向量、使用 StandardScaler 对它们进行缩放以及执行特征工程来预处理数据。
- 在函数内部，创建一个名为 `assembler` 的 `VectorAssembler`，用于使用输入列 ‘Open’、‘High’、‘Low’ 和 ‘Volume’ 组装特征向量，输出列名为 ‘features’。然后应用 `transform` 方法，使用 assembler 转换输入 DataFrame `df`。
- 使用 `logger.info` 函数提供日志信息，以指示预处理步骤的进度。使用 `df.show` 方法显示组装特征后 DataFrame 的前五个观察值。
- 调用 `perform_feature_engineering` 函数，以在 DataFrame `df` 上执行额外的特征工程操作。
- 另一个预处理步骤涉及使用 `StandardScaler` 对特征进行缩放。创建一个名为 `scaler` 的 `StandardScaler` 对象，指定输入和输出列，以及标准化选项。然后对 DataFrame 应用 `fit` 方法以获取缩放器模型，并使用该模型转换 DataFrame。
- 最后，修改 DataFrame 以仅选择 ‘scaled_features’ 和 ‘Close’ 列，然后从函数中返回它。该 DataFrame 包含已预处理的数据，准备好用于进一步分析或建模。

在下一步中，我们创建 `perform_feature_engineering` 函数，该函数对 DataFrame 应用各种特征工程操作，例如创建交互项和从现有特征中提取有用信息：

```python
def perform_feature_engineering(df: DataFrame) -> DataFrame:
    """
    Perform feature engineering operations such as creating interaction terms, generating polynomial
    features, or extracting useful information from existing features.
    """
    df = df.withColumn('price_range', df['High'] - df['Low'])
    df = df.withColumn('price_change', df['Close'] - df['Open'])

    df = df.withColumn(
        'volume_price_interaction',
        df['Volume'] * df['Close']
    )

    return df
```

- 该函数接受一个 DataFrame `df` 作为输入，并在执行特征工程后返回一个 DataFrame。
- 文档字符串提供了对函数目的的简要描述，即执行特征工程操作，例如创建交互项。
- 在函数内部，对 DataFrame `df` 执行特征工程操作：
    - 通过从每个观察值的 ‘High’ 价格中减去 ‘Low’ 价格，创建新列 'price_range'。这捕捉了每只股票的价格范围。
    - 通过从 ‘Close’ 价格中减去 ‘Open’ 价格，创建另一个新列 'price_change'。这代表给定时间段内的价格变化。




此外，通过 `Volume` 列与 `Close` 价格相乘生成了一个名为 `volume_price_interaction` 的新列。该交互项捕捉了交易量与股价之间的关系。

- 在这些特征工程操作之后，函数返回修改后的 DataFrame `df`，其中包含新创建的列以及原始特征。这些工程化的特征对于提高机器学习模型的性能或从数据中获取洞察可能非常有价值。

接下来，我们创建 `print_first_5_observations` 函数，用于打印 DataFrame 的前五个观察值，并附带自定义标题：

```python
[In]: def print_first_5_observations(df: DataFrame,
          heading: str):
          """
          Print the first 5 observations of the DataFrame with
          a custom heading.
          """
          logger.info(heading)
          df.show(5, truncate=False)
```

- 该函数接受两个参数：DataFrame `df` 和字符串 `heading`。它不返回任何值。
- 文档字符串提供了对该函数目的的简要描述，即打印 DataFrame 的前五个观察值并附带自定义标题。
- 在函数内部，使用 `logger.info` 函数记录传入的自定义标题。
- 随后使用 `df.show` 方法显示 DataFrame `df` 的前五个观察值。参数 `truncate=False` 确保显示的列不被截断，从而展示每个列的完整内容。

在下一步中，我们定义 `create_data_loader` 函数，用于创建用于批量处理的 TensorFlow Dataset：

```python
[In]: def create_data_loader(features, labels, batch_size):
        """
        Create a TensorFlow Dataset for batch processing.
        """
        dataset = tf.data.Dataset.from_tensor_slices(
            (features, labels)
        )
        dataset = dataset.shuffle(buffer_size=10000)
        dataset = dataset.batch(batch_size)
        return dataset
```

- 该函数接受三个参数：`features`、`labels` 和 `batch_size`。它不直接返回任何值，而是返回一个 TensorFlow Dataset 对象。
- 文档字符串提供了对该函数目的的简要描述，即创建用于批量处理的 TensorFlow Dataset。
- 在函数内部，使用 `tf.data.Dataset.from_tensor_slices` 方法创建了一个 TensorFlow Dataset。该方法沿第一个维度切分输入张量 `features` 和 `labels`，以创建数据集的独立元素。每个元素由一对对应的特征和标签组成。
- 随后，使用 `shuffle` 方法对创建的数据集进行洗牌，缓冲区大小为 10000。洗牌有助于随机化数据集中元素的顺序，这在训练过程中可能有助于防止模型过拟合。
- 接下来，对洗牌后的数据集应用 `batch` 方法，将元素分组为大小为 `batch_size` 的批次。批处理允许在训练期间高效地按批次处理数据，从而减少内存使用并提高计算效率。
- 最后，函数返回创建的数据集，该数据集现已准备好用于在 TensorFlow 中训练机器学习模型。此数据集可以按批次进行迭代，以有效训练模型。

继续往下，我们创建 `copy_file_from_s3` 函数，用于将文件从 Amazon S3 存储桶复制到本地文件路径：

```python
[In]: def copy_file_from_s3(bucket_name: str, file_key: str, local_file_path: str):
        """ Copy file from S3 bucket to local file path. """
        s3 = boto3.client('s3')
        s3.download_file(bucket_name, file_key, local_file_path)
        logger.info(f"File downloaded from S3 bucket {bucket_name}"
                    f"to local file path: {local_file_path}")
```

- 该函数接受三个参数：`bucket_name`、`file_key` 和 `local_file_path`。它不返回任何值。
- 文档字符串提供了对该函数目的的简要描述，即将文件从 S3 存储桶复制到本地文件路径。
- 在函数内部，使用 `s3 = boto3.client('s3')` 创建了一个 Amazon S3 的 `boto3.client` 实例。该客户端允许与 S3 服务进行交互。
- 然后调用 `s3.download_file` 方法，将文件从指定的 S3 存储桶（`bucket_name`）和文件键（`file_key`）下载到本地文件路径（`local_file_path`）。此方法处理从 S3 到本地系统的实际文件传输。
- 在文件成功下载后，使用 `logger.info` 函数记录信息，指示文件已从 S3 存储桶下载到本地文件路径。消息中包含诸如 S3 存储桶名称和文件保存的本地文件路径等详细信息。

在下一步中，我们定义 `main` 函数，该函数通过按顺序调用必要的函数来编排整个过程。它从 S3 存储桶复制文件、加载数据、预处理数据、将其转换为 NumPy 数组，并创建用于批量处理的 TensorFlow Dataset：

```python
[In]: def main():
         s3_bucket_name = 'instance1bucket'
         s3_file_key = 'TSLA_stock.csv'
         local_file_path = '/home/ubuntu/airflow/dags/TSLA_stock.csv'
         copy_file_from_s3(
             s3_bucket_name,
             s3_file_key,
             local_file_path
         )

         df = load_data(local_file_path)
         print_first_5_observations(df, "First 5 observations:")
         df = preprocess_data(df)
         print_first_5_observations(
             df,
             "First 5 observations after scaling:")

         df_features = np.array(
             df.select('scaled_features')
             .rdd.map(lambda x: x.scaled_features.toArray())
             .collect()
         )
         df_labels = np.array(
             df.select('Close')
             .rdd.map(lambda x: x.Close)
             .collect()
         )

         batch_size = 32
         train_dataset = create_data_loader(
             df_features,
             df_labels,
             batch_size
         )

         for features, labels in train_dataset.take(1):
             logger.info(
                 "First 5 observations after scaling"
                 "and converting to TensorFlow Dataset:"
             )
             logger.info(features[:5])
             logger.info("First 5 labels with no scaling:")
             logger.info(labels[:5])
```

- 该函数首先初始化变量 `s3_bucket_name`、`s3_file_key` 和 `local_file_path`，其值分别代表 S3 存储桶名称、文件键（存储桶内的路径）以及 S3 文件将下载到的本地文件路径。
- 然后调用 `copy_file_from_s3` 函数，传递 S3 存储桶名称、文件键和本地文件路径作为参数。该函数负责将指定文件从 S3 存储桶下载到本地文件路径。
- 在下载文件后，该函数使用 `load_data` 函数将数据从本地文件路径加载到 DataFrame `df` 中。
- 随后两次调用 `print_first_5_observations` 函数，以显示 DataFrame `df` 的前五个观察值并附带自定义标题。第一次调用打印任何预处理之前的初始观察值，而第二次调用打印缩放后的观察值。

接下来，通过调用 `preprocess_data` 函数将特征工程过程应用于 DataFrame `df`。该函数组装特征向量，使用 StandardScaler 对其进行缩放，并执行额外的特征工程操作。

`preprocess_data` 函数返回修改后的 DataFrame `df`，其中现在包含缩放后的特征和额外的工程化特征。

随后，从 DataFrame `df` 中提取特征和标签，并分别转换为 NumPy 数组 `df_features` 和 `df_labels`。这些数组对于创建用于训练机器学习模型的 TensorFlow Dataset 是必需的。

使用 `create_data_loader` 函数创建一个 TensorFlow Dataset `train_dataset`，该函数将特征和标签批次化为指定大小（`batch_size`）的批次。

最后，一个循环遍历 `train_dataset` 的第一个批次，记录缩放后特征的前五个观察值以及前五个标签。

最后，下面的条件块确保 `main` 函数仅在脚本直接运行时执行，而在作为模块被其他脚本导入时不执行：

```python
if __name__ == "__main__":
    main()
```

`__name__` 变量是 Python 中的一个特殊内置变量，代表当前模块的名称。当 Python 解释器直接运行脚本时，它会将 `__name__` 的值设置为 `"__main__"`。





- 条件语句检查 `__name__` 的值是否等于 `"_main_"`。如果相等，则表示该脚本正作为主程序执行，条件语句下方的代码块将会被执行。

- 在这种情况下，代码块由单个函数调用组成：`main()`。此调用执行脚本前部定义的主函数，该函数协调执行各种任务，例如下载数据、预处理以及为训练准备数据。

通过将 `main()` 函数调用包裹在 `if __name__ == "__main__":` 条件语句中，脚本可以被导入到其他脚本中作为模块，而不会自动执行 `main()` 函数。这使得脚本中定义的函数和类可以用作其他 Python 程序中的可重用组件。

为了运行该脚本，我们首先将其保存为 `pyspark_tensorflow_preparation.py`，激活 EC2 实例上的虚拟环境，然后使用以下命令运行 Python 脚本：

```
[In]: cd /home/ubuntu
[In]: source myenv/bin/activate
[In]: python3 pyspark_tensorflow_preparation.py
```

现在让我们检查代码的输出。

第一个输出由 `print_first_5_observations` 函数生成，显示了数据处理前 DataFrame 的前五行。它包含日期、开盘价、最高价、最低价、收盘价和成交量等列。此输出提供了用于训练 TensorFlow 模型的数据概览：

| Date | Open | High | Low | Close | Volume |
|---|---|---|---|---|---|
| 2/23/24 | 195.31 | 197.57 | 191.50 | 191.97 | 78,670,300 |
| 2/22/24 | 194.00 | 198.32 | 191.36 | 197.41 | 92,739,500 |
| 2/21/24 | 193.36 | 199.44 | 191.95 | 194.77 | 103,844,000 |
| 2/20/24 | 196.13 | 198.60 | 189.13 | 193.76 | 104,545,800 |
| 2/16/24 | 202.06 | 203.17 | 197.40 | 199.95 | 111,173,600 |

第二个输出由 `preprocess_data(df)` 函数生成，显示了使用 `VectorAssembler` 组装特征向量后 DataFrame 的前五行。它添加了一个名为 "features" 的新列，其中包含组装后的特征：

| Date | Open | High | Low | Close | Volume | Features |
|---|---|---|---|---|---|---|
| 2/23/24 | 195.31 | 197.57 | 191.50 | 191.97 | 78,670,300 | [195.31, 197.57, 191.5, 78,670,300] |
| 2/22/24 | 194.00 | 198.32 | 191.36 | 197.41 | 92,739,500 | [194.0, 198.32, 191.36, 92,739,500] |
| 2/21/24 | 193.36 | 199.44 | 191.95 | 194.77 | 103,844,000 | [193.36, 199.44, 191.95, 103,844,000] |
| 2/20/24 | 196.13 | 198.60 | 189.13 | 193.76 | 104,545,800 | [196.13, 198.6, 189.13, 104,545,800] |
| 2/16/24 | 202.06 | 203.17 | 197.40 | 199.95 | 111,173,600 | [202.06, 203.17, 197.4, 111,173,600] |

第三个输出由 `perform_feature_engineering(df)` 函数生成，显示了执行特征工程操作后 DataFrame 的前五行。基于原始列添加了诸如 “price_range”、"price_change" 和 "volume_price_interaction" 等新列。由于 Open, High, Low, Close, Volume 和 Features 列与上一张表相同，我们在下表中省略了这些列，以便关注新列：

| Date | Price Range | Price Change | Volume-Price Interaction |
| :--- | :--- | :--- | :--- |
| 2/23/24 | 6.07 | -3.34 | 15,102,337,569.07 |
| 2/22/24 | 6.96 | 3.41 | 18,307,705,065.96 |
| 2/21/24 | 7.49 | 1.41 | 20,225,696,295.38 |
| 2/20/24 | 9.47 | -2.37 | 20,256,793,685.27 |
| 2/16/24 | 5.77 | -2.11 | 22,229,160,986.48 |

第四个输出由 `preprocess_data(df)` 函数生成，展示了使用 `StandardScaler` 对特征进行缩放后 DataFrame 的前五行。它包含 "scaled_features" 列以及 "Close" 列：

| Scaled Features | Close |
| :--- | :--- |
| [0.18, 0.16, 0.19, -0.65] | 191.97 |
| [0.17, 0.17, 0.19, -0.48] | 197.41 |
| [0.16, 0.18, 0.19, -0.35] | 194.77 |
| [0.19, 0.17, 0.17, -0.35] | 193.76 |
| [0.24, 0.21, 0.25, -0.27] | 199.95 |

最后一个输出显示了缩放并转换为张量后的前五个观测值。从理论上讲，输出应该与上一张表相同，因为我们在这里所做的只是将数据转换为张量。

然而，读者可能会观察到不同的结果，这是由于数据的 shuffle（洗牌）操作导致的，这可能导致每个批次内样本顺序的变化。

### 将所有内容整合在一起

在本节中，我们将整合在探索、并行处理和准备过程中展示的各个代码片段。这展示了每个步骤如何集成以形成全面的数据探索和准备管道。通过结合前面探讨的各种技术和功能，我们展示了使用 PySpark 为 PyTorch 和 TensorFlow 深度学习任务探索和准备数据的端到端工作流程。

### 使用 PySpark 进行数据探索

在这个小节中，我们将结合用于探索特斯拉股票数据集的代码片段，包括打印数据集的前十行、执行描述性统计、检查缺失值以及在折线图中可视化收盘价随时间的变化：

```python
[In]: import boto3
[In]: import matplotlib.pyplot as plt
[In]: from pyspark.sql import SparkSession
[In]: from pyspark.sql.functions import col
[In]: import pyspark.sql.functions as F
[In]: import numpy as np

[In]: class DataProcessor:
    def __init__(self, spark_session):
        self.spark = spark_session
```

```python
[In]: def load_data(self, file_path: str):
    """
    使用 SparkSession 从 CSV 文件加载股票价格数据。
    """
    try:
        df = self.spark.read.csv(
            file_path,
            header=True,
            inferSchema=True
        )
        return df
    except Exception as e:
        print(f"Error loading data: {str(e)}")
        return None
```

```python
[In]: def print_first_n_rows(self, df, n=10):
    """Print the first n rows of the DataFrame."""
    print(f"First {n} rows of the DataFrame:")
    df.show(n)
```

```python
[In]: def calculate_descriptive_statistics(self, df):
    """Calculate descriptive statistics of the
    DataFrame."""
    print("Descriptive Statistics:")
    df.summary().show()
```

```python
[In]: def visualize_data(self, df):
    """Create visualizations based on DataFrame."""
    print("Data Visualization:")
    try:
        df_pd = df.toPandas()
        plt.figure(figsize=(10, 6))
```

```python
plt.plot(df_pd['Date'], df_pd['Close'])
plt.xlabel('Date')
plt.ylabel('Closing Price')
plt.title('Tesla Stock Closing Prices Over Time')
plt.xticks(rotation=45, ha='right')
plt.gca().invert_xaxis()
plt.xticks(np.arange(0, len(df_pd['Date']),
step=max(len(df_pd['Date']) // 10, 1)))
plt.show()
except Exception as e:
print(f"Error visualizing data: {str(e)}")
```

```python
[In]: def check_for_null_values(self, df):
    """Check for null values in the DataFrame."""
    print("Null Value Check:")
    null_counts = df.select([col(c).isNull()
.cast("int").alias(c) for c in df.columns])
.agg(*[F.sum(c).alias(c) for c in df.columns])
.toPandas()
print(null_counts)
```

```python
[In]: def copy_file_from_s3(bucket_name: str, file_key: str,
local_file_path: str):
    """
    将文件从 S3 存储桶复制到本地文件路径。
    """
    try:
        s3 = boto3.client('s3')
        s3.download_file(bucket_name, file_key, local_
file_path)
        print(
```

```python
f"File downloaded from S3 bucket
{bucket_name}"
f"to local file path: {local_file_path}"
)
except Exception as e:
print(f"Error copying file from S3: {str(e)}")
```

```python
[In]: def main(
s3_bucket_name: str,
s3_file_key: str,
local_file_path: str
):
    """
    股票价格预测的主函数。
    该函数初始化一个 SparkSession，将文件从 S3 存储桶
    复制到本地文件路径，初始化 DataProcessor 对象，
    从本地文件加载数据，并执行各种数据处理任务。
    :param s3_bucket_name:
    包含文件的 S3 存储桶名称
    :param s3_file_key:
    S3 存储桶中文件的键
    :param local_file_path:
    保存下载文件的本地文件路径
    """
    spark = (SparkSession.builder
.appName("StockPricePrediction")
.getOrCreate())
```




## PySpark 中的并行处理

在本小节中，我们展示了用于演示在 PySpark 中加速处理大型数据集的各种技术的代码：

```python
import boto3
from pyspark.sql import SparkSession
from pyspark.sql.functions import broadcast

class DataProcessor:
    def __init__(self, spark_session):
        self.spark = spark_session

    def load_data(self, file_path: str):
        try:
            df = self.spark.read.csv(
                file_path,
                header=True,
                inferSchema=True
            )
            return df
        except Exception as e:
            print(f"Error loading data: {str(e)}")
            return None

    def print_first_n_rows(self, df, n=10):
        print(f"First {n} rows of the DataFrame:")
        df.show(n)

    def print_partition_info(self, df):
        num_partitions = df.rdd.getNumPartitions()
        print(f"Number of partitions: {num_partitions}")

def copy_file_from_s3(
        bucket_name: str,
        file_key: str,
        local_file_path: str
    ):
    try:
        s3 = boto3.client('s3')
        s3.download_file(bucket_name, file_key, local_file_path)
        print(f"File downloaded from S3 bucket\n      {bucket_name} "
              f"to local file path: {local_file_path}")
    except Exception as e:
        print(f"Error copying file from S3: {str(e)}")

def main(
    s3_bucket_name: str,
    s3_file_key: str,
    local_file_path: str
):
    spark = SparkSession.builder \
        .appName("StockPriceOptimization") \
        .config("spark.sql.adaptive.enabled", "true") \
        .config("spark.sql.shuffle.partitions", "20") \
        .getOrCreate()
    copy_file_from_s3(
        s3_bucket_name,
        s3_file_key,
        local_file_path
    )
    data_processor = DataProcessor(spark)
    df = data_processor.load_data(local_file_path)
    if df is not None:
        data_processor.print_partition_info(df)
        # Repartition the DataFrame
        repartitioned_df = df.repartition(10)
        data_processor.print_partition_info(repartitioned_df)
        # Coalesce partitions
        coalesced_df = repartitioned_df.coalesce(5)
        data_processor.print_partition_info(coalesced_df)

        # Example broadcast join
        small_df = spark.createDataFrame([
            ("2023-08-25", 5.5),
            ("2023-08-26", 6.0),
        ], ["Date", "AdditionalData"])
        joined_df = repartitioned_df.join(
            broadcast(small_df), on="Date", how="left")

        # Save as Parquet
        repartitioned_df.write.parquet(
            "/home/ubuntu/airflow/dags/tesla_stock.parquet"
        )

        # Print the first few rows
        data_processor.print_first_n_rows(repartitioned_df)
    else:
        print("Error loading data. Exiting.")

if __name__ == "__main__":
    s3_bucket_name = 'instance1bucket'
    s3_file_key = 'TSLA_stock.csv'
    local_file_path = '/home/ubuntu/airflow/dags/TSLA_stock.csv'
    main(s3_bucket_name, s3_file_key, local_file_path)
```

### 使用 PySpark 为 PyTorch 进行数据准备

在本小节中，我们将之前用于为 PyTorch 深度学习模型准备特斯拉股票数据集的各个独立代码片段组合在一起：

```python
import logging
from pyspark.sql import SparkSession
from pyspark.ml.feature import VectorAssembler, StandardScaler
from pyspark.sql import DataFrame
import numpy as np
import torch
from torch.utils.data import DataLoader, TensorDataset
import boto3

logging.basicConfig(level=logging.INFO)
logger = logging.getLogger(__name__)

def load_data(file_path: str) -> DataFrame:
    '''
    Load stock price data from a CSV file using SparkSession.
    '''
    spark = (SparkSession.builder
             .appName("StockPricePrediction")
             .getOrCreate())
    df = spark.read.csv(
        file_path,
        header=True,
        inferSchema=True
    )
    return df

def preprocess_data(df: DataFrame) -> DataFrame:
    """
    Preprocess the data by assembling feature vectors using VectorAssembler, 
    scaling them using StandardScaler, and performing feature engineering.
    """
    assembler = VectorAssembler(
        inputCols=['Open', 'High', 'Low', 'Volume'],
        outputCol='features'
    )
    df = assembler.transform(df)
    logger.info("First 5 observations after assembling features:")
    df.show(5, truncate=False)
    
    df = perform_feature_engineering(df)
    logger.info("First 5 observations after feature engineering:")
    df.show(5, truncate=False)
    
    scaler = StandardScaler(
        inputCol="features",
        outputCol="scaled_features",
        withStd=True, withMean=True
    )
    scaler_model = scaler.fit(df)
    df = scaler_model.transform(df)
    df = df.select('scaled_features', 'Close')
    return df

def perform_feature_engineering(df: DataFrame) -> DataFrame:
    """
    Perform feature engineering operations to enhance the data's predictive power.

    This function adds new columns to the DataFrame `df` to capture relevant 
    information from existing features, including:

    - Price Range Interaction: Represents the difference between High and Low prices.
    - Price Change Interaction: Represents the difference between Close and Open prices.
    - Volume-Price Interaction: Represents the product of Volume and Close prices.

    Parameters:
    df (DataFrame): The input DataFrame containing the raw data.

    Returns:
    DataFrame: The DataFrame `df` with additional engineered features.
    """
    df = df.withColumn('price_range', df['High'] - df['Low'])
    df = df.withColumn('price_change', df['Close'] - df['Open'])
    df = df.withColumn(
        'volume_price_interaction',
        df['Volume'] * df['Close']
    )
    return df

def print_first_5_observations(df: DataFrame, heading: str):
    """
    Print the first 5 observations of the DataFrame with a custom heading.
    """
    logger.info(heading)
    df.show(5, truncate=False)

def convert_to_tensor(features, labels):
    """
    Convert features and labels to PyTorch tensors.
    """
    tensor_features = torch.tensor(
        features,
        dtype=torch.float32
    )
    tensor_labels = torch.tensor(labels, dtype=torch.float32)
    return tensor_features, tensor_labels

def create_data_loader(features, labels, batch_size):
    """
    Create a PyTorch DataLoader for batch processing.
    """
    tensor_features, tensor_labels = convert_to_tensor(features, labels)
    dataset = TensorDataset(tensor_features, tensor_labels)
    data_loader = DataLoader(
        dataset,
        batch_size=batch_size,
        shuffle=True
    )
    return data_loader

def copy_file_from_s3(bucket_name: str, file_key: str, local_file_path: str):
    """
    Copy file from S3 bucket to local file path.
    """
    s3 = boto3.client('s3')
    s3.download_file(bucket_name, file_key, local_file_path)
    logger.info(
        f"File downloaded from S3 bucket {bucket_name}"
        f"to local file path: {local_file_path}"
    )
```





# 使用 PySpark 为 TensorFlow 准备数据

在本小节中，我们将之前用于准备特斯拉股票数据集以供 TensorFlow 深度学习模型使用的独立代码片段进行了整合：

```python
[In]: import logging
[In]: from pyspark.sql import SparkSession
[In]: from pyspark.ml.feature import VectorAssembler, StandardScaler
[In]: from pyspark.sql import DataFrame
[In]: import numpy as np
[In]: import tensorflow as tf
[In]: from tensorflow.keras.utils import to_categorical
[In]: import boto3

[In]: logging.basicConfig(level=logging.INFO)
[In]: logger = logging.getLogger(__name__)

[In]: def load_data(file_path: str) -> DataFrame:
    """
    Load stock price data from a CSV file using SparkSession.
    """
    spark = (SparkSession.builder
        .appName("StockPricePrediction")
        .getOrCreate()
    )
    df = spark.read.csv(
        file_path,
        header=True,
        inferSchema=True
    )
    return df

[In]: def preprocess_data(df: DataFrame) -> DataFrame:
    """
    Preprocess the data by assembling feature vectors using VectorAssembler, scaling them using StandardScaler, and performing feature engineering.
    """
    assembler = VectorAssembler(
        inputCols=['Open', 'High', 'Low', 'Volume'],
        outputCol='features'
    )
    df = assembler.transform(df)
    
    logger.info(
        "First 5 observations after assembling features:"
    )
    df.show(5, truncate=False)
    
    df = perform_feature_engineering(df)
    
    logger.info(
        "First 5 observations after feature engineering:"
    )
    df.show(5, truncate=False)
    
    scaler = StandardScaler(
        inputCol="features",
        outputCol="scaled_features",
        withStd=True, withMean=True
    )
    scaler_model = scaler.fit(df)
    df = scaler_model.transform(df)
    df = df.select('scaled_features', 'Close')
    return df

[In]: def perform_feature_engineering(df: DataFrame) -> DataFrame:
    """
    Perform feature engineering operations such as creating interaction terms, generating polynomial features, or extracting useful information from existing features.
    """
    df = df.withColumn('price_range', df['High'] - df['Low'])
    df = df.withColumn('price_change', df['Close'] - df['Open'])
    df = df.withColumn(
        'volume_price_interaction',
        df['Volume'] * df['Close']
    )
    return df

[In]: def print_first_5_observations(df: DataFrame, heading: str):
    """
    Print the first 5 observations of the DataFrame with a custom heading.
    """
    logger.info(heading)
    df.show(5, truncate=False)

[In]: def create_data_loader(features, labels, batch_size):
    """
    Create a TensorFlow Dataset for batch processing.
    """
    dataset = tf.data.Dataset.from_tensor_slices(
        (features, labels)
    )
    dataset = dataset.shuffle(buffer_size=10000)
    dataset = dataset.batch(batch_size)
    return dataset

[In]: def copy_file_from_s3(bucket_name: str, file_key: str, local_file_path: str):
    """
    Copy file from S3 bucket to local file path.
    """
    s3 = boto3.client('s3')
    s3.download_file(bucket_name, file_key, local_file_path)
    logger.info(
        f"File downloaded from S3 bucket {bucket_name}"
        f"to local file path: {local_file_path}"
    )

[In]: def main():
    s3_bucket_name = 'instance1bucket'
    s3_file_key = 'TSLA_stock.csv'
    local_file_path = '/home/ubuntu/airflow/dags/TSLA_stock.csv'
    copy_file_from_s3(
        s3_bucket_name,
        s3_file_key,
        local_file_path
    )
    
    df = load_data(local_file_path)
    print_first_5_observations(df, "First 5 observations:")
    df = preprocess_data(df)
    print_first_5_observations(
        df,
        "First 5 observations after scaling:"
    )
    
    df_features = np.array(
        df.select('scaled_features')
        .rdd.map(lambda x: x.scaled_features.toArray())
        .collect()
    )
    df_labels = np.array(
        df.select('Close')
        .rdd.map(lambda x: x.Close).collect()
    )
    
    batch_size = 32
    train_loader = create_data_loader(
        df_features, df_labels, batch_size
    )
    
    logger.info(
        "First 5 observations after scaling and converting to tensors:"
    )
    print(train_loader.dataset[:5])

    for features, labels in train_loader.dataset.take(1):
        logger.info(
            "First 5 observations after scaling and"
            "converting to TensorFlow Dataset:"
        )
        logger.info(features[:5])
        logger.info("First 5 labels with no scaling:")
        logger.info(labels[:5])

[In]: if __name__ == "__main__":
    main()
```

# 摘要

在本章中，我们探讨了 PySpark 的并行处理功能如何提高数据处理效率，特别是针对大型数据集。我们研究了诸如重新分区、广播连接、缓存、将数据保存为 Parquet 格式、优化 shuffle 分区以及启用自适应查询执行 (AQE) 等技术，以提升这些数据准备任务的性能。

我们还介绍了使用 PySpark 为深度学习任务准备数据的过程。我们探讨了这一过程中的关键方面，包括数据探索（加载数据、打印数据集的前十行、执行描述性统计、检查空值以及可视化数据）、数据准备（预处理和特征工程）以及为 PyTorch 和 TensorFlow 格式化数据。

数据探索是理解数据特征和模式的基础。预处理涉及清洗和转换原始数据，使其适用于建模目的，而特征工程在提高输入特征的质量和预测能力方面发挥着重要作用。格式化确保处理后的数据被转换为与 PyTorch 和 TensorFlow 兼容的张量格式，以便进行高效处理。

在下一章中，我们将开始构建、训练和评估深度学习算法的旅程，从 PyTorch 回归开始。

# 使用 PyTorch 进行回归的深度学习

在本章中，我们开始探索使用 PyTorch 构建深度学习模型。该框架与 TensorFlow（我们将在第 5 章和第 7 章中探讨）一起，代表了构建和训练神经网络的行业标准。在这里，我们专注于回归，这是机器学习中的一个基本问题，其目标是预测连续的数值。

与线性回归等传统算法相比，用于回归任务的深度学习 approach 具有若干优势。深度学习模型可以自动从复杂的数据集中学习复杂的模式和关系，捕捉线性模型可能难以有效处理的非线性和交互作用。此外，深度学习模型能够随着大型数据集进行扩展，并在处理包含多个特征的数据集时（例如与股票价格、交易量以及其他影响金融市场的因素相关的特征）可能提供更好的预测性能。

然而，必须承认的是，与传统算法相比，深度学习模型通常需要更多的计算资源和数据，这使得它们在计算上非常密集


对于资源有限的应用程序而言，这可能是潜在且不切实际的。而这正是 AWS 发挥作用的地方。Amazon Web Services 提供可扩展且灵活的云计算解决方案，为高效部署和运行深度学习模型提供必要的基础设施。此外，深度学习模型通常被视为黑盒，这使得它们比线性回归等传统算法更难以解释。它们还需要大量的超参数调优，这一问题我们将在第 9 章中重新探讨。尽管如此，深度学习模型在广泛的任务中继续展现出卓越的性能，并且仍然是积极研究和发展的领域。

为了展示如何使用 PyTorch 进行回归任务，我们将构建、训练并评估一个神经网络模型，并使用它来预测特斯拉股价。这种预测在金融领域至关重要，因为准确预测股价可以为投资决策和风险管理策略提供依据。然而，需要注意的是，本章中该模型的目的是用于演示，我们并不旨在开发一个用于商业用途的模型。

## 数据集

我们将使用从 Yahoo! Finance 获取的特斯拉股票历史每日数据集。该数据集以 CSV 格式下载，随后存储在名为“instance1bucket”的 AWS S3 存储桶中，可通过以下链接访问：

https://finance.yahoo.com/quote/TSLA/history/

我们在前一章中详细探索了这个数据集。在本节中，我们将加载 CSV 文件，将其从 S3 存储桶复制到 EC2 实例上的本地目录，并打印前五行以让我们回顾特征和目标变量长什么样。

我们首先导入必要的模块：

```python
import subprocess
from pyspark.sql import SparkSession
import logging
```

- `import subprocess`：这一行导入了 subprocess 模块，该模块通常用于执行 shell 命令或与系统 shell 进行交互。在我们的代码中，subprocess 将用于执行 `aws s3 cp` 命令，以便将 CSV 文件从 S3 存储桶复制到本地目录。
- `from pyspark.sql import SparkSession`：这一行从 pyspark.sql 模块导入了 SparkSession 类。SparkSession 是利用 Spark 的 Dataset 和 DataFrame API 的起点，为 Spark 框架内的编程任务提供接口。它允许我们创建 DataFrame 和 Dataset 对象、与 Spark SQL 交互以及配置 Spark 属性。在我们接下来的代码中，SparkSession 将用于创建 Spark 应用程序并将 CSV 文件加载到 DataFrame 中。
- `import logging`：这一行导入了 logging 模块，该模块提供了一个从 Python 程序生成日志消息的框架。它通常用于调试、监控和排查 Python 应用程序和脚本的问题。在我们的代码中，logging 用于在数据加载和复制过程中记录信息和错误消息，提供反馈并辅助调试。

接下来，我们定义 `load_data` 函数，该函数使用 SparkSession 从 CSV 文件加载特斯拉股价数据：

```python
def load_data(file_path: str):
    """
    Load stock price data from a CSV file using
    SparkSession.
    """
    spark = (SparkSession.builder
             .appName("StockPricePrediction")
             .getOrCreate())
    df = spark.read.csv(
        file_path,
        header=True,
        inferSchema=True
    )
    return df
```

让我们分解该函数：

- `def load_data(file_path: str):` 这一行定义了函数 `load_data`，该函数有一个参数 `file_path`，它是一个表示 CSV 文件路径的字符串。
- `""" Load stock price data from a CSV file using SparkSession. """`：这是一个文档字符串（docstring），为函数提供文档说明。它描述了函数的目的，即使用 SparkSession 从 CSV 文件加载股价数据。
- `spark = SparkSession.builder`：这一行使用 builder 方法实例化一个 SparkSession 对象，从而能够配置 Spark 属性和设置。
- `.appName("StockPricePrediction")`：这将应用程序名称设置为 "StockPricePrediction"。这是可选的，但有助于在 Spark 监控工具中识别应用程序。当在 Airflow DAG（有向无环图）中执行 Spark 作业时，正如我们将在第 8 章中演示的那样，设置描述性的应用程序名称可以极大地帮助在 Airflow 界面和日志中跟踪和管理 Spark 作业。
- `.getOrCreate()`：此方法返回当前环境中正在运行的现有 SparkSession，如果不存在则创建一个新的。
- `df = spark.read.csv(file_path, header=True, inferSchema=True)`：这一行使用 SparkSession 对象的 `read.csv()` 方法将位于 `file_path` 的 CSV 文件读取到 DataFrame (`df`) 中。`header=True` 参数表示 CSV 文件的第一行包含列名，而 `inferSchema=True` 指示 Spark 自动推断每列的数据类型。
- `return df`：最后，函数返回包含加载数据的 DataFrame `df`。

下一步是定义 `copy_and_print_data` 函数，该函数将 CSV 文件从 AWS 上的 S3 存储桶复制到 EC2 实例上的本地目录，并打印前五个观测值：

```python
def copy_and_print_data():
    """
    Copy a CSV file from an S3 bucket to a local directory and print the first 5 observations.
    """
    s3_bucket_path = "s3://instance1bucket/TSLA_stock.csv"
    local_file_path = "/home/ubuntu/airflow/dags/TSLA_stock.csv"
    logging.basicConfig(level=logging.INFO)
    logger = logging.getLogger(__name__)

    try:
        subprocess.run(
            [
                "aws", "s3", "cp",
                s3_bucket_path,
                local_file_path
            ],
            check=True
        )
        df = load_data(local_file_path)
        print("First 5 observations of the DataFrame:")
        df.show(5)

    except FileNotFoundError:
        logger.error(f"Data file not found at {s3_bucket_path}")
    except subprocess.CalledProcessError as e:
        logger.error(f"Error copying data from S3: {e}")
```

让我们分解该函数：

- `def copy_and_print_data()`：这一行定义了无参数的函数 `copy_and_print_data`。该函数将 CSV 文件从 AWS 上的 S3 存储桶复制到 EC2 实例上的本地目录，并打印前五个观测值。
- `""" Copy a CSV file from an S3 bucket to a local directory and print the first 5 observations. """`：这是一个文档字符串，简要描述该函数执行的操作。
- `s3_bucket_path = "s3://instance1bucket/TSLA_stock.csv"`：这一行定义了 AWS S3 存储桶中 CSV 文件的路径。
- `local_file_path = "/home/ubuntu/airflow/dags/TSLA_stock.csv"`：这一行定义了 CSV 文件将在 EC2 实例上本地复制到的路径。
- `logging.basicConfig(level=logging.INFO)`：这一行配置 logging 模块以显示 INFO 级别的日志消息。
- `logger = logging.getLogger(__name__)`：这一行初始化一个专用于此模块的 logger 对象。
- `try:`：这开始一个 try-except 块，用于处理执行期间可能发生的潜在异常。
- `subprocess.run(["aws", "s3", "cp", s3_bucket_path, local_file_path], check=True)`：这一行执行一个子进程，使用 AWS CLI 命令 `aws s3 cp` 将 CSV 文件从 S3 存储桶复制到 EC2 实例上的本地目录。`check=True` 参数确保如果子进程命令未成功完成，则引发异常。
- `df = load_data(local_file_path)`：这一行调用 `load_data` 函数将 CSV 文件加载到 DataFrame (`df`) 中。
- `print("First 5 observations of the DataFrame:")`：这一行打印一条描述性消息，表示将打印 DataFrame 的前五个观测值。
- `df.show(5)`：这一行使用 PySpark 的 `show()` 方法显示 DataFrame `df` 的前五行。
- `except FileNotFoundError:`：此 except 子句处理 `FileNotFoundError` 异常，该异常在找不到指定文件时发生。
- `except subprocess.CalledProcessError as e:`：此 except 子句处理 `CalledProcessError` 异常，该异常在执行子进程命令时发生错误时出现。
- `logger.error(f"Data file not found at {s3_bucket_path}")`：如果找不到指定文件，这一行记录一条错误消息。
- `logger.error(f"Error copying data from S3: {e}")`：如果执行子进程命令时发生错误，这一行记录一条错误消息。

最后，我们定义主函数：

```python
if __name__ == "__main__":
    copy_and_print_data()
```

- `if __name__ == "__main__":`：这是一行常用的代码，仅当脚本直接运行时执行 Python 程序，而不是作为模块导入到另一个脚本中时。它检查特殊变量 `__name__` 是否等于 `"__main__"`。


如果脚本是直接运行的，此条件评估为 `True`；如果它是作为模块被导入的，则评估为 `False`。这是 Python 编程中一种常见的最佳实践，因为它允许脚本既可作为独立程序使用，也可作为可复用模块使用。

- `copy_and_print_data()`: 这行代码调用 `copy_and_print_data()` 函数，前提是脚本被直接运行。换句话说，当 Python 解释器直接执行此脚本时，它将调用 `copy_and_print_data()` 函数。

我们将脚本保存为 “spark_data_processing.py”，位于 “/home/ubuntu/airflow/dags” 目录中。要执行它，我们可以选择通过以下命令在 JupyterLab 接口终端中导航到该目录，或者直接在 EC2 命令行界面中执行该脚本：

```
[In]: cd /home/ubuntu/airflow/dags
```

接下来，我们使用以下命令激活虚拟环境 “myenv”：

```
[In]: source myenv/bin/activate
```

最后，在激活虚拟环境后，我们使用以下命令运行脚本：

```
[In]: python3 spark_data_processing.py
```

这将启动脚本的执行，该过程涉及从 S3 存储桶复制特斯拉股票 CSV 文件到本地目录，并打印 DataFrame 的前五个观测值。

运行代码后，我们得到以下输出：

```
[Out]: First 5 observations of the DataFrame:
```

| 日期 | 开盘价 | 最高价 | 最低价 | 收盘价 | 成交量 |
|:---|:---|:---|:---|:---|:---|
| 2/23/24 | 195.31 | 197.57 | 191.50 | 191.97 | 78670300 |
| 2/22/24 | 194.00 | 198.32 | 191.36 | 197.41 | 92739500 |
| 2/21/24 | 193.36 | 199.44 | 191.95 | 194.77 | 103844000 |
| 2/20/24 | 196.13 | 198.60 | 189.13 | 193.76 | 104545800 |
| 2/16/24 | 202.06 | 203.17 | 197.40 | 199.95 | 111173600 |

该每日数据集涵盖从 2019 年 2 月 26 日到 2024 年 2 月 23 日的时间范围（共 1,258 个观测值）。输出显示了此历史数据集中的前五个观测值。每个交易日都捕捉了特斯拉股价的实时波动。这些观测值突出了关键指标——开盘价、最高价、最低价、收盘价和成交量——展示了特定时间段内的价格变动。它们的定义如下：

- **开盘价（Open）**：特斯拉股票在给定日期的开盘价格
- **最高价（High）**：特斯拉股票在给定日期的交易时段内达到的最高价格
- **最低价（Low）**：特斯拉股票在给定日期的交易时段内达到的最低价格
- **收盘价（Close）**：特斯拉股票在给定日期的收盘价格
- **成交量（Volume）**：交易量，代表给定日期内交易的总股数

## 使用 PyTorch 预测特斯拉股价

在本节中，我们利用前一节中探索的数据集，实现一种用于预测特斯拉股价的深度学习算法。在该数据集中，模型的特征由开盘价、最高价、最低价和成交量组成，而目标变量是收盘价。股票的开盘价可以提供有关交易日开始时市场情绪的重要信息，反映投资者对新闻、事件或隔夜发展的初始反应。同样，交易量也很重要，因为高交易量通常表明投资者兴趣增加，并可能预示潜在的价格变动。成交量也可用作流动性的代理指标，这对准确的价格发现至关重要。至于交易时段内达到的最高价和最低价，它们提供了关于价格波动性和交易范围的洞察。最高价表明买入兴趣的最高水平，而最低价则代表卖出兴趣的最低水平。分析最高价和最低价之间的范围有助于识别趋势、支撑位和阻力位。

通过将这些特征纳入我们的预测模型，我们可以捕捉基本市场动态（如开盘情绪和交易活动）和技术方面（如价格波动性和交易范围），这些对于准确预测股价至关重要。然而，值得注意的是，我们的模型目的是说明性的，而非提供完整描述。虽然这些特征很有价值，但纳入额外特征（如技术指标、基本数据或市场情绪）可以进一步增强模型的预测能力。不过，这超出了本章的范围。

我们利用 PySpark 的数据处理能力和 PyTorch 来构建、训练和评估神经网络模型。Python 代码旨在处理端到端的工作流程，从数据加载和预处理到模型训练、评估和预测。在第 8 章中，我们将演示如何使用 Apache Airflow 部署此代码。

整个建模过程包括以下十个步骤：

- 步骤 1：导入
- 步骤 2：日志记录设置
- 步骤 3：数据加载
- 步骤 4：数据预处理
- 步骤 5：数据加载器创建
- 步骤 6：模型训练
- 步骤 7：模型评估
- 步骤 8：主函数
- 步骤 9：辅助函数
- 步骤 10：执行

让我们深入逐步查看代码：

### 步骤 1：导入

在这一步中，我们介绍代码中导入的库和模块。这些导入支持数据处理、建模和日志记录：

```
[In]: import logging
[In]: import subprocess
[In]: from typing import Tuple
[In]: import numpy as np
[In]: import torch
[In]: import torch.nn as nn
[In]: import torch.optim as optim
[In]: from torch.utils.data import DataLoader, TensorDataset
[In]: from pyspark.sql import SparkSession
[In]: from pyspark.ml.feature import VectorAssembler, StandardScaler
[In]: from pyspark.sql import DataFrame
```

以下是这些导入及其重要性的分解：

- **logging**：此库用于在代码执行过程中生成日志消息。它有助于跟踪程序进度、调试问题和监控活动。在我们的代码中，日志记录将用于记录数据加载、预处理、模型训练和评估等各个阶段的信息性消息和错误消息。
- **subprocess**：此模块允许代码执行系统命令并与其他程序交互。在我们的代码中，它用于在数据处理之前从 AWS S3 存储桶复制数据到 EC2 上的本地目录。
- **typing**：此模块允许指定函数参数和返回值的预期类型。它将在我们的代码中用于函数注释，以指定参数和返回类型。
- **numpy**：这是 Python 科学计算的基础包。它提供对大型多维数组和矩阵的支持，以及操作这些数组的数学函数集合。在我们的代码中，NumPy 用于将 Spark DataFrame 列转换为 NumPy 数组。
- **torch, torch.nn, torch.optim**：这些是 PyTorch 的组件，PyTorch 是一个主要用于深度学习应用的机器学习库。在我们的代码中，它们用于定义和训练神经网络模型。
- **DataLoader, TensorDataset**：这些是来自 PyTorch 的 torch.utils.data 模块的类。DataLoader 用于在训练和推理期间按批次加载数据集，而 TensorDataset 是一个数据集封装器，允许方便地访问张量。它们在代码中用于创建用于训练和测试神经网络模型的数据加载器。
- **pyspark.sql, pyspark.ml.feature, DataFrame**：这些是 PySpark 的组件，将在我们的代码中用于在将结构化数据转换为 PyTorch 张量以训练神经网络模型之前，在 Spark DataFrame 中加载、预处理和操作数据。具体而言，pyspark.sql 用于 Spark DataFrame 操作，pyspark.ml.feature 用于特征组装和缩放等数据预处理任务，而 DataFrame 代表 PySpark 中用于数据操作和分析的 DataFrame 类。

### 步骤 2：日志记录设置

在这一步中，我们配置日志记录系统，以确保有效监控代码执行并促进调试和程序进度跟踪：

```
[In]: logging.basicConfig(level=logging.INFO)
[In]: logger = logging.getLogger(__name__)
```

以下是这两行代码的含义：

- **logging.basicConfig(level=logging.INFO)**：此代码行配置日志系统以显示 INFO 级别或更高级别的日志消息。它确保在代码执行期间显示足够重要的日志消息。





- `logger = logging.getLogger(__name__)`：该行创建一个专门针对当前模块的名为 `logger` 的日志记录器对象。它允许在模块内记录日志消息，有助于跟踪程序进度、调试问题以及监控活动。

### 步骤 3：数据加载函数 (load_data)

在此步骤中，我们定义 `load_data` 函数，用于从存储在 AWS S3 上的 CSV 文件中加载特斯拉股价数据。该数据包含 2019 年 2 月 26 日至 2024 年 2 月 23 日期间特斯拉股票的日期、开盘价、最高价、最低价、成交量和收盘价：

```python
def load_data(file_path: str) -> DataFrame:
    """
    Load stock price data from a CSV file using SparkSession.
    """
    try:
        spark = (SparkSession.builder
                 .appName("StockPricePrediction")
                 .getOrCreate())
        df = spark.read.csv(
                 file_path,
                 header=True,
                 inferSchema=True
                 )
        return df
    except Exception as e:
        raise RuntimeError(
                 f"Error loading data from {file_path}: {e}"
                 )
```

让我们考察该函数中 `SparkSession` 的使用以及数据加载和异常处理的过程：

#### 使用 SparkSession

- `SparkSession` 是访问 Spark 功能并在 Spark 中处理数据的主要入口点。在 `load_data` 函数中，`SparkSession` 用于创建 Spark 应用程序上下文，这使得可以对分布在集群多个节点上的大型数据集进行高效并行处理。
- 通过使用 `SparkSession`，代码利用了 Apache Spark 的分布式计算能力，实现了可扩展的高性能数据处理。

#### 数据加载过程

- 在 `load_data` 函数内部，使用 `SparkSession.builder` 方法创建 `SparkSession`。这配置了 Spark 应用程序的设置，例如应用程序名称。
- 然后，该函数使用 `spark.read.csv` 方法将 CSV 文件读取到 DataFrame 中。
- `header=True` 参数指定 CSV 文件的第一行包含列名，而 `inferSchema=True` 则从数据中推断 DataFrame 的架构。
- 加载的 DataFrame 随后由函数返回。

#### 异常处理

- 代码使用 try–except 块来处理数据加载过程中可能发生的潜在异常。异常可能由各种原因引起，例如文件缺失、权限问题或数据格式不一致。
- 如果在 try 块中执行代码时发生异常，它会被 except 块捕获。except 子句随后抛出 `RuntimeError`，并提供包含错误来源的提示信息。

### 步骤 4：数据预处理函数 (preprocess_data)

在此步骤中，我们定义 `preprocess_data` 函数，该函数负责预处理加载的特斯拉股价数据：

```python
def preprocess_data(df: DataFrame) -> DataFrame:
    """
    Preprocess the data by assembling feature vectors using
    VectorAssembler and scaling them using StandardScaler.
    """
    assembler = VectorAssembler(
        inputCols=['Open', 'High', 'Low', 'Volume'],
        outputCol='features'
    )
    df = assembler.transform(df)

    scaler = StandardScaler(
        inputCol="features",
        outputCol="scaled_features",
        withStd=True,
        withMean=True
    )
    scaler_model = scaler.fit(df)
    df = scaler_model.transform(df)
    df = df.select('scaled_features', 'Close')
    return df
```

`preprocess_data` 函数负责准备加载的特斯拉股价数据以进行模型训练。预处理是机器学习管道中的关键步骤，因为它通过将原始数据转换为适合训练的格式来有助于提高模型性能。

预处理步骤包括特征向量组装和特征缩放：

#### 特征向量组装

- 使用 PySpark 进行预处理的第一步是组装特征向量，它们是代表数据不同特征的一组数值。在这种情况下，它们代表特斯拉股票的开盘价、最高价、最低价和成交量。（目标变量，即收盘价，不包括在内。）
- 使用 PySpark 的 `VectorAssembler` 将这些特征列连接成一个单一的特征向量列，从而促进更顺畅的处理并便于输入 PyTorch 机器学习模型。

#### 特征缩放

- 一旦特征向量组装完成，下一步就是特征缩放。特征缩放是将特征值标准化或归一化到相似尺度的过程。这一点很重要，因为在模型训练期间，幅度较大的特征可能会主导幅度较小的特征。
- 使用 PySpark 的 `StandardScaler` 对特征向量进行缩放。它通过减去均值并除以标准差来标准化特征值，确保每个特征的均值为 0 且标准差为 1。
- 缩放后的特征向量存储在一个名为 `scaled_features` 的新列中，该列在 DataFrame 中替换了原始的特征向量。

关于 `preprocess_data` 函数的实现细节：

- 在函数内部，使用 `inputCols` 参数初始化 `VectorAssembler`，该参数指定要组装到特征向量中的列，以及 `outputCol` 参数，该参数指定输出列的名称。
- 然后，在 DataFrame 上调用 `VectorAssembler` 的 `transform` 方法来组装特征向量。
- 同样地，使用 `inputCol` 参数初始化 `StandardScaler`，该参数指定包含特征向量的列，以及 `outputCol` 参数，该参数指定缩放特征输出列的名称。
- 对 DataFrame 应用 `StandardScaler` 的 `fit` 方法以计算用于特征缩放的统计摘要（均值和标准差），然后调用 `transform` 方法来缩放特征向量。

通过执行特征向量组装和特征缩放，`preprocess_data` 函数为使用 PyTorch 进行后续模型训练准备了特斯拉股价数据。这些预处理步骤有助于确保数据被适当格式化和缩放，以实现 PyTorch 机器学习模型的最佳性能。

### 步骤 5：DataLoader 创建函数 (create_data_loader)

在此步骤中，我们定义 `create_data_loader` 函数，该函数在创建训练集和测试集的 DataLoader 对象中起着关键作用：

```python
def create_data_loader(
            features,
            labels,
            batch_size=32,
            num_workers=4) -> DataLoader:
    """
    Convert the preprocessed data into PyTorch
    tensors and
    create DataLoader objects for both the training
    and test
    sets.
    
    Args:
        features (Tensor): The input features.
        labels (Tensor): The corresponding labels.
        batch_size (int):
            The number of samples per batch to load.
            Defaults to
            32.
        num_workers (int):
            The number of subprocesses to use for data
            loading. Defaults to 4.
        
    Returns:
        DataLoader: A PyTorch DataLoader for the dataset.
    """
    dataset = TensorDataset(features, labels)
    return DataLoader(
        dataset,
        batch_size=batch_size,
        shuffle=True
    )
```

`create_data_loader` 函数负责将预处理数据转换为 PyTorch 张量并创建 DataLoader 对象。这些 DataLoader 对象对于在训练和测试阶段有效地向机器学习模型提供数据至关重要。

该函数接受预处理后的特征和标签作为输入，并将它们转换为 PyTorch `TensorDataset`，这是一种包装张量的数据集。然后，它使用 `TensorDataset` 为训练集和测试集创建 DataLoader 对象。DataLoader 中的 `num_workers` 参数允许并行数据加载，这可以显著加快数据准备阶段的速度，特别是在处理大型数据集或复杂预处理步骤时。

DataLoader 是一种 PyTorch 工具，通过自动对数据进行批处理和必要时打乱顺序来提供高效的数据加载。DataLoader 在管理模型训练期间的数据批次方面起着至关重要的作用。DataLoader 并不是一次性将整个数据集输入模型，而是将数据集分割成指定大小的批次。这种批处理过程允许更高效的计算，特别是当处理可能无法一次性装入内存的大型数据集时。它还启用了小批量梯度下降，该方法基于数据子集更新模型参数，从而带来更快的收敛和更好的泛化能力。




## 数据加载器与数据洗牌

数据加载器（DataLoader）对于数据洗牌同样至关重要。在模型训练期间，打乱数据顺序是必需的，以防止模型学习到特定于数据集的顺序或模式。

DataLoader 提供了洗牌数据的选项，确保模型在训练过程中看到的每个批次都包含来自数据集的随机样本选择。这种随机性有助于防止模型对训练数据过拟合，并提高其泛化到未见过数据的能力。

关于 `create_data_loader` 函数的实现细节：

- 在函数内部，预处理后的特征和标签使用 TensorDataset 构造函数组合成一个 PyTorch TensorDataset。
- 通过向 DataLoader 构造函数传递 TensorDataset 以及指定的批次大小和洗牌参数，为训练集和测试集分别创建 DataLoader 对象。
- 然后，该函数返回这些 DataLoader 对象，它们可用于在模型训练和评估过程中迭代遍历数据批次。

通过创建 DataLoader 对象，`create_data_loader` 函数实现了机器学习管道中训练和测试阶段的数据高效加载与管理。DataLoader 处理数据批处理和洗牌的能力有助于提高训练效率、模型性能及泛化能力。

### 第 6 步：模型训练函数（`train_model`）

在这一步中，我们创建 `train_model` 函数，该函数负责使用训练数据训练神经网络模型：

`train_model` 函数的任务是利用训练数据训练神经网络模型。神经网络的训练涉及根据预测输出与实际目标之间的差异，迭代更新模型的参数（权重和偏置）。

让我们更详细地解释这一过程：

#### 迭代训练

- 该函数针对指定的轮次（epochs）次数遍历训练数据集。每个轮次代表对整个训练数据集的一次完整遍历。
- 在每个轮次中，该函数遍历数据的小批次（mini-batches）。此过程由 DataLoader 对象辅助完成，它自动对数据进行批处理。
- 对于每个小批次，模型使用当前参数值进行预测（前向传播），计算预测输出与实际目标之间的损失，然后更新模型参数以最小化损失（反向传播）。

#### 使用反向传播进行参数更新

- 反向传播是训练神经网络的关键算法。它涉及计算损失函数相对于模型参数的梯度，这些梯度表示每个参数对误差的贡献程度。
- 在计算梯度后，优化器（在此情况下为 Adam 优化器）沿最小化损失的方向调整模型的参数。
- 此过程对训练数据集中的每个小批次以及多个轮次重复进行，通过最小化损失函数逐步提高模型的性能。

关于 `train_model` 函数实现的具体细节：

- 在函数内部，存在一个嵌套循环结构，其中外层循环遍历轮次，内层循环遍历数据的小批次。
- 对于每个小批次，调用优化器的 `zero_grad` 方法将所有模型参数的梯度重置为零。
- 然后调用模型的前向方法对输入数据进行预测，随后使用指定的损失函数（criterion）和实际标签计算损失。
- 在计算损失后，调用 backward 方法计算损失相对于模型参数的梯度。
- 最后，调用优化器的 `step` 方法基于计算出的梯度更新模型参数，有效地执行一次优化步骤。

通过实现迭代训练过程和基于反向传播的参数更新，`train_model` 函数使 PyTorch 神经网络模型能够从训练数据中学习，并在随后的轮次中提高其性能。这种迭代优化过程是机器学习中神经网络训练成功的基础。

### 第 7 步：模型评估函数（`evaluate_model`）

在这一步中，我们创建 `evaluate_model` 函数，该函数在测试数据上评估训练好的神经网络模型：

```python
def evaluate_model(
    model,
    test_loader,
    criterion
) -> Tuple[float, float]:
    """
    在测试数据上评估训练好的模型，
    以评估其性能。
    计算测试损失以及额外的
    评估指标，如 R-squared 分数。
    """
    with torch.no_grad():
        model.eval()
        predictions = []
        targets = []
        test_loss = 0.0
        for inputs, labels in test_loader:
            outputs = model(inputs)
            loss = criterion(outputs, labels.unsqueeze(1))
            test_loss += loss.item() * inputs.size(0)
            predictions.extend(outputs.squeeze().tolist())
            targets.extend(labels.tolist())

        test_loss /= len(test_loader.dataset)
        predictions = torch.tensor(predictions)
        targets = torch.tensor(targets)
        ss_res = torch.sum((targets - predictions) ** 2)
        ss_tot = torch.sum((targets - torch.mean(targets)) ** 2)
        r_squared = 1 - ss_res / ss_tot
        logger.info(f"Test Loss: {test_loss:.4f}")
        logger.info(f"R-squared Score: {r_squared:.4f}")
        return test_loss, r_squared.item()
```

`evaluate_model` 函数评估训练好的神经网络模型在未见过的测试数据上的性能。评估对于理解模型对新的、未见过的样本的泛化程度以及识别任何潜在问题（如过拟合）至关重要。

该函数计算测试损失，该损失衡量模型预测与测试数据集中实际目标之间的差异。这通常使用诸如均方误差（MSE）或平均绝对误差（MAE）等损失函数完成。在此情况下，使用 MSE 损失函数。通过平均测试数据集中所有样本的个体损失来计算总测试损失。

除了测试损失外，该函数还计算一个额外的评估指标：R-squared 分数（也称为决定系数）。R-squared 分数衡量目标变量（在此情况下为收盘价）的方差中，可以通过模型中的自变量（特征）预测的比例。它的取值范围从 0 到 1，较高的值表示更好的模型拟合度。分数为 1 表示完美拟合，而分数为 0 表示模型的预测效果不比简单使用目标变量的平均值更好。

在 `evaluate_model` 函数内部，使用 `model.eval()` 将模型设置为评估模式。该函数遍历测试 DataLoader 中的数据小批次，使用训练好的模型进行预测，并计算每个小批次的测试损失。它还累积预测值和实际目标，以便在遍历完所有小批次后计算 R-squared 分数。

R-squared 分数使用以下公式计算：

```python
r_squared = 1 - ss_res / ss_tot
```

其中 `ss_res` 是残差平方和（预测值与目标值之间的差值之和的平方），`ss_tot` 是总平方和。

`logger.info` 记录测试损失和 R-squared 分数，以提供有关模型在测试数据集上性能的见解。这些指标有助于评估模型的预测能力并识别改进领域。

### 第 8 步：主函数（`main`）

在这一步中，我们将讨论主函数，它是执行代码的入口点：

```python
def main(
    data_file_path: str,
    num_epochs: int = 100,
    batch_size: int = 32,
    learning_rate: float = 0.001
):
    """
    用于训练和评估特斯拉股价预测深度学习模型的
    主函数。

    参数：
        data_file_path (str): 包含股价数据的
        CSV 文件的路径。
        num_epochs (int): 训练模型的轮次数。默认为 100。
        batch_size (int): 训练期间数据加载的批次大小。默认为 32。
        learning_rate (float): 优化器的学习率。默认为 0.001。
    """




learning_rate（float）：优化器的学习率。默认值为 0.001。

num_workers（int）：用于数据加载的子进程数量。默认值为 4。

Raises: 引发 FileNotFoundError：如果找不到指定的数据文件。

```python
"""
try:
    subprocess.run([
        "aws", "s3", "cp",
        "s3://instance1bucket/TSLA_stock.csv",
        "/home/ubuntu/airflow/dags/"
    ])
    
    df = load_data(data_file_path)
    df = preprocess_data(df)
    
    train_df, test_df = df.randomSplit([0.8, 0.2], seed=42)
    
    train_features, train_labels = \
        spark_df_to_tensor(train_df)
    test_features, test_labels = spark_df_to_tensor(test_df)
    
    train_loader = create_data_loader(
        train_features,
        train_labels,
        batch_size=batch_size,
        num_workers=num_workers
    )
    
    test_loader = create_data_loader(
        test_features,
        test_labels,
        batch_size=batch_size,
        num_workers=num_workers
    )
    
    input_size = train_features.shape[1]
    output_size = 1
    
    model = nn.Sequential(
        nn.Linear(input_size, 64),
        nn.ReLU(),
        nn.Linear(64, 32),
        nn.ReLU(),
        nn.Linear(32, 16),
        nn.ReLU(),
        nn.Linear(16, output_size)
    )
    
    criterion = nn.MSELoss()
    optimizer = optim.Adam(
        model.parameters(),
        lr=learning_rate
    )
    
    train_model(
        model,
        train_loader,
        criterion,
        optimizer,
        num_epochs
    )
    
    evaluate_model(model, test_loader, criterion)

    torch.save(model.state_dict(), 'trained_model.pth')

except FileNotFoundError:
    logger.error(f"Data file not found at {data_file_path}")
```

让我们来探讨该函数的作用，并将其分解为单独的操作，包括数据加载、预处理、模型初始化、训练、保存和评估：

- 主函数协调特斯拉股价预测的整个过程，从数据加载到模型评估。它充当机器学习流水线的中央协调者。
- 主函数首先使用 `subprocess.run` 方法从 AWS S3 存储桶将数据复制到 EC2 上的本地目录。这是数据加载的前置步骤。接下来，它使用 `load_data` 函数从 CSV 文件中加载特斯拉股价数据，并将文件路径作为参数传入。
- 在数据加载之后，主函数使用 PyTorch 初始化神经网络模型。它定义了模型架构，指定输入特征的数量（从数据集中动态推断）以及输出大小（固定为 1，用于预测单个值（即股价））。此外，模型包含三个隐藏层，分别包含 64、32 和 16 个神经元，每个层后面都跟随一个整流线性单元（ReLU）激活函数。
- 初始化完成后，主函数使用 `train_model` 函数开始训练模型。它指定了诸如 epoch 数、批次大小、学习率、损失函数和优化器等参数。在训练过程中，模型参数会根据训练数据迭代更新，以最小化损失函数。
- 训练完成后，主函数使用 `torch.save` 方法将训练好的模型参数保存到文件中。这使得模型可以重复使用或部署以对新数据进行预测，而无需重新训练。
- 随后，主函数使用 `evaluate_model` 函数在测试数据上评估训练好的模型的性能。它计算测试损失和 R-squared 分数等指标，以评估模型在未见数据上的泛化能力。
- 主函数包含错误处理机制，例如使用 `try-except` 块捕获数据加载期间未找到文件的错误。这确保了代码能够处理意外问题，并提供有用的错误信息以便调试。

通过在 main 函数中封装这些阶段，代码实现了模块化和结构化的设计，使其更容易理解和维护。主函数作为中央协调者，整合了机器学习流水线的不同组件，以完成特斯拉股价预测的任务。在第 8 章中，我们将通过部署代码通过 Apache Airflow 来探索对此流程的进一步增强。

### 步骤 9：辅助函数 (spark_df_to_tensor)

在这一步中，我们创建 **spark_df_to_tensor** 辅助函数，它将 Spark DataFrame 列转换为 PyTorch 张量：

```python
[In]: def spark_df_to_tensor(
        df: DataFrame
    ) -> Tuple[torch.Tensor, torch.Tensor]:
        """
        Converts Spark DataFrame columns to PyTorch tensors.
        """
        features = torch.tensor(
            np.array(
                df.rdd.map(lambda x: x.scaled_features.toArray())
                .collect()
            ),
            dtype=torch.float32
        )
        labels = torch.tensor(
            np.array(
                df.rdd.map(lambda x: x.Close).collect()
            ),
            dtype=torch.float32)
        return features, labels
```

**spark_df_to_tensor** 函数用于将 Spark DataFrame 列转换为 PyTorch 张量。这种转换是必要的，因为 PyTorch 张量是在神经网络模型中表示和操作数据的主要数据结构。

该函数接受一个包含预处理特征和标签的 Spark DataFrame 作为输入。它从 DataFrame 中提取特征向量和标签，并使用 DataFrame 的 RDD（弹性分布式数据集）的 **collect** 方法将它们转换为 NumPy 数组。

然后，使用 torch.tensor 构造函数将这些 NumPy 数组转换为 PyTorch 张量，该构造函数可以从类数组对象创建张量。最后，该函数以元组形式返回特征张量和标签张量，准备好作为训练或评估神经网络模型的输入。

关于 spark_df_to_tensor 函数的实现细节：

- 在函数内部，通过使用 lambda 函数将每一行映射到其对应的特征向量数组，从 DataFrame 中提取特征向量。
- 使用 `toArray()` 方法将 Spark 向量列转换为 NumPy 数组。
- 同样，使用 `collect` 方法从 DataFrame 中提取标签并转换为 NumPy 数组。
- 然后，使用 `torch.tensor` 构造函数将特征数组和标签数组转换为 PyTorch 张量。
- 最后，以元组形式返回特征张量和标签张量。

通过提供将 Spark DataFrame 列转换为 PyTorch 张量的便捷接口，spark_df_to_tensor 函数促进了基于 PySpark 的数据处理流水线与基于 PyTorch 的机器学习模型的集成。这使得数据可以在数据预处理阶段（使用 PySpark 执行）和模型训练/评估阶段（使用 PyTorch 执行）之间流动，而无需手动转换或兼容性问题。此外，将数据转换为张量确保了与 PyTorch 基于张量的操作和自动微分功能的兼容性，这对于训练神经网络模型至关重要。最后，这种将 Spark DataFrame 列转换为 PyTorch 张量的机制简化了数据处理工作流，并支持在大规模数据集上高效训练和评估神经网络模型。

# 步骤 10：执行

此步骤中的代码通常位于脚本末尾，作为直接运行脚本时执行代码的入口点。它调用 main 函数，并传入指定的数据文件路径作为参数，启动使用 PyTorch 机器学习技术进行特斯拉股价预测的整个过程：

```python
[In]: if __name__ == "__main__":
        data_file_path = "/home/ubuntu/airflow/dags/TSLA_stock.csv"
        main(data_file_path)
```

在第 8 章中，我们展示了如何使用 Apache Airflow 优化此代码部署过程，Apache Airflow 是一个强大的工作流管理平台。我们强调了 Airflow 高级的任务调度和编排能力，这些能力消除了对传统 main 函数的需求。相反，我们利用 Airflow 的有向无环图（DAG）方法，其中每个节点代表数据管道中的特定任务。Airflow 自动化任务依赖关系，支持并行执行，促进重试，并提供全面的监控和日志记录功能。这增强了可扩展性并提高了运营效率，为简化和自动化的管道铺平了道路。

为了运行代码，我们将文件保存为 "tesla_stock_price_prediction.py"，并在 JupyterLab 终端中执行（或者我们也可以直接在 EC2 实例上运行）。由于我们创建了一个名为 "myenv" 的环境，因此按以下方式激活它：

```bash
[In]: source /home/ubuntu/myenv/bin/activate
```





激活环境后，我们使用 Python 3 执行代码，命令如下：

```python
[In]: python3 tesla_stock_price_prediction.py
```

代码输出显示了三个主要指标：

- 训练过程中每个 epoch 的损失值
- 测试损失
- 训练完成后的 R² 分数

**训练损失：**

| 轮次 | 损失 |
| :--- | :--- |
| 1/100 | 48533.29 |
| 2/100 | 40968.77 |
| 3/100 | 26662.96 |
| 4/100 | 13865.01 |
| 5/100 | 3026.32 |
| 6/100 | 1682.71 |
| 7/100 | 1077.39 |
| 8/100 | 475.19 |
| 9/100 | 1194.83 |
| 10/100 | 1361.66 |
| ... | ... |
| 100/100 | 11.12 |

**测试损失：** 20.54

**R² 分数：** 0.998

让我们逐一解释这些指标：

### 训练损失

训练期间计算的损失函数值代表了模型在训练数据上的表现。数值越低，表明表现越好。

正如上面样本表中前十个 epoch 所示，损失值随着每个 epoch 的推进而下降。例如，第一个 epoch 的损失值为 48,533，而到第十个 epoch 时，损失值约为 1,362。当模型达到第 100 个 epoch 时，训练损失约为 11，即初始损失的 0.02%。这表明在第 100 个 epoch 之后，模型在训练数据上达到了相对较低的错误率，说明它有效地学习了训练数据中存在的模式。

### 测试损失

测试损失值是在测试集（本例中为总数据集的 20%）上计算的，用于评估模型对未见数据的泛化能力。如上所述，测试损失约为 21。这与训练损失相对接近，表明模型没有过度拟合训练数据，并且对未见数据具有较好的泛化能力。测试损失略高于训练损失是符合预期且合理的，因为模型通常需要一定程度的泛化能力来处理未见数据，这通常会导致测试损失略微偏高。

### R² 分数

R² 分数（在测试集上计算）是一个衡量模型拟合优度的指标，它表示因变量的方差中可由自变量预测的比例。数值越接近 1，表示拟合效果越好。

模型取得了令人印象深刻的 R² 分数 0.998，表明它解释了因变量方差的 99.8%。这种高水平的解释能力证明了预测值与实际值之间存在强相关性，说明模型有效地捕捉了数据中的潜在模式。

为了进一步验证模型的性能，我们可以比较实际值和预测值。下面的代码通过首先以表格形式比较前十个实际值和预测值，然后绘制所有特斯拉股价的实际值和预测值曲线，实现了这一目标。

**注意** 这段代码依赖于我们之前运行用于训练和评估模型的 `tesla_stock_price_prediction.py` 模块。该代码通过从 `tesla_stock_price_prediction.py` 模块导入的 `preprocess_data` 函数缩放特征来预处理数据，并加载由该模块生成的预训练模型权重。

让我们从导入必要的模块开始：PyTorch 库、NumPy、Matplotlib，以及来自 `tesla_stock_price_prediction` 模块的 `load_data` 和 `preprocess_data` 函数：

```python
[In]: import torch
[In]: import numpy as np
[In]: import matplotlib.pyplot as plt
[In]: from tesla_stock_price_prediction import (
          load_data,
          preprocess_data
          )
```

然后我们定义一个主函数，执行以下任务：

- 从包含股价数据的 CSV 文件加载测试数据
- 使用从 `tesla_stock_price_prediction` 模块导入的 `preprocess_data` 函数缩放特征来预处理数据
- 使用 PyTorch 定义神经网络模型架构
- 从文件中加载预训练模型权重
- 使用加载的模型在预处理后的测试数据进行预测
- 并排打印前十个实际股价和预测股价
- 绘制所有实际值和预测值的折线图以进行可视化

```python
[In]: def main():
         """
         Load test data, preprocess it, and make predictions
         using a pre-trained model.

         This function loads test data from a CSV file,
         preprocesses it, loads a pre-trained PyTorch model,
         makes predictions on the test data, and visualizes
         the actual vs. predicted stock prices.
         """

         test_data_file_path = \
             "/home/ubuntu/airflow/dags/TSLA_stock.csv"

         test_data = load_data(test_data_file_path)
         test_data = preprocess_data(test_data)

         test_features = \
             test_data.select('scaled_features').collect()

         test_features = np.array(
               [
                     row.scaled_features.toArray()
                     for row in test_features
               ],
               dtype=np.float64
         )

         input_size = 4
         output_size = 1
         model = torch.nn.Sequential(
                 torch.nn.Linear(input_size, 64),
                 torch.nn.ReLU(),
                 torch.nn.Linear(64, 32),
                 torch.nn.ReLU(),
                 torch.nn.Linear(32, 16),
                 torch.nn.ReLU(),
                 torch.nn.Linear(16, output_size)
         )

         model.load_state_dict(
                 torch.load(
                         '/home/ubuntu/airflow/dags/trained_model.pth',
                         map_location=torch.device('cpu')
                 )
         )
         model.eval()

         test_features_tensor = torch.tensor(
                 test_features,
                 dtype=torch.float64
         )

         model = model.double()

         with torch.no_grad():
             predictions = model(
                 test_features_tensor
             ).squeeze().numpy()
             actual_labels = test_data.select('Close').collect()
             actual_labels = np.array(
                 [row.Close for row in actual_labels],
                 dtype=np.float64
             )

             actual_labels = actual_labels[::-1]
             predictions = predictions[::-1]

             print("Top 10 Actual vs Predicted Values:")
             print("Actual\tPredicted")
             for i in range(10):
                 print(f"{actual_labels[i]:.4f}\t{predictions[i]:.4f}")

             plt.figure(figsize=(10, 6))
             plt.plot(actual_labels, label='Actual')
             plt.plot(predictions, label='Predicted')
             plt.xlabel('Index')
             plt.ylabel('Price')
             plt.title(
                 'Actual vs Predicted Tesla Stock Prices '
                 '(Feb 26, 2019 to Feb 23, 2024)'
             )

             plt.legend()
             plt.grid(True)
             plt.show()

[In]: if __name__ == "__main__":
    main()
```

该代码定义了一个名为 `main()` 的函数，该函数涵盖了使用预训练 PyTorch 模型预测特斯拉股价的过程：

- 该函数首先通过文档字符串（docstring）定义其目的，说明它从 CSV 文件加载测试数据，对其进行预处理，加载预训练的 PyTorch 模型，在测试数据上进行预测，并可视化实际股价与预测股价。
- 首先，它设置测试数据 CSV 文件的路径。然后，它使用自定义函数（`load_data` 和 `preprocess_data`）加载并预处理测试数据，将其转换为适合模型的格式。
- 接下来，使用 PyTorch 的 Sequential API 定义神经网络模型架构，该架构包含几个带有 ReLU 激活函数的线性层。
- 使用 `torch.load()` 和 `model.load_state_dict()` 从文件中加载预训练模型权重。然后通过使用 `model.eval()` 将模型置于评估模式。
- 测试数据特征被转换为 PyTorch 张量，并转换为适当的数据类型（`torch.float64`）。模型也通过 `model = model.double()` 转换为双精度。
- 使用预训练模型对测试数据进行预测。获取测试数据的实际标签，并将实际值和预测值反转，以使其与正确的时间顺序对齐。
- 打印前十个实际值与预测值的对比。
- 最后，使用 Matplotlib 可视化实际股价和预测股价，其中 x 轴表示索引，y 轴表示价格。图表标题指示了被可视化数据的时间范围。
- 最后，仅当脚本直接作为主程序运行时（即 `__name__` == `"__main__"`），才执行 `main()` 函数。这确保了当脚本直接执行时执行函数内的代码，但当它作为模块导入到另一个脚本时则不执行。

代码有两个输出：

- 显示前十个实际值和预测目标值的表格
- 绘制所有实际值和预测目标值的图表





从表格开始，我们添加了一列“% 变化”，尽管该列并非由代码生成，但旨在直观展示实际值与预测值之间的差异：

| 日期 | 实际值 | 预测值 | % 变化 |
| --- | --- | --- | --- |
| 2/23/24 | 192 | 196 | 2% |
| 2/22/24 | 197 | 196 | -1% |
| 2/21/24 | 195 | 197 | 1% |
| 2/20/24 | 194 | 196 | 1% |
| 2/16/24 | 200 | 202 | 1% |
| 2/15/24 | 200 | 196 | -2% |
| 2/14/24 | 189 | 187 | -1% |
| 2/13/24 | 184 | 186 | 1% |
| 2/12/24 | 188 | 192 | 2% |
| 2/09/24 | 194 | 193 | -1% |

数据表明，预测值与实际值之间的最大差异为 abs(2%)，这表明两者高度吻合。

转到图表，图 4-1 展示了所有特斯拉股价（1,258 个观测值）的实际值和预测值。两条线的接近程度证实了模型的强大性能。

![](img/1c89d4486f90c87568fa6a42d46ae02a_271_0.png)

*图 4-1.* *特斯拉股价的实际值与预测值*

# 整合所有内容

在本节中，我们将本章中检查的代码各个组件进行整合，以构建一个全面的代码库。这部分包含三个子部分：探索特斯拉股票数据集、使用 PySpark 和 PyTorch 预测特斯拉股价，以及并排绘制实际值和预测值。

## 探索特斯拉股票数据集

下面的脚本将 TSLA（特斯拉）股价 CSV 文件从 S3 存储桶复制到本地目录 “/home/ubuntu/airflow/dags/”，将数据加载到 Spark DataFrame 中，然后打印该 DataFrame 的前五个观测值：

```python
[In]: import subprocess
[In]: from pyspark.sql import SparkSession
[In]: import logging

[In]: def load_data(file_path: str):
    """
    Load stock price data from a CSV file using
    SparkSession.
    """
    spark = (SparkSession.builder
             .appName("StockPricePrediction")
             .getOrCreate())
    df = spark.read.csv(
            file_path,
            header=True,
            inferSchema=True
           )
    return df

[In]: def copy_and_print_data():
    """
    Copy a CSV file from an S3 bucket to a local
    directory and
    print the first 5 observations.
    """
    s3_bucket_path = "s3://instance1bucket/TSLA_stock.csv"
    local_file_path = "/home/ubuntu/airflow/dags/TSLA_stock.csv"
    logging.basicConfig(level=logging.INFO)
    logger = logging.getLogger(__name__)

    try:
        subprocess.run(
            [
                "aws", "s3", "cp",
                s3_bucket_path,
                local_file_path
            ],
            check=True
        )
        df = load_data(local_file_path)
        print("First 5 observations of the DataFrame:")
        df.show(5)

    except FileNotFoundError:
        logger.error(f"Data file not found at {s3_bucket_path}")
    except subprocess.CalledProcessError as e:
        logger.error(f"Error copying data from S3: {e}")

[In]: if __name__ == "__main__":
    copy_and_print_data()
```

## 使用 PySpark 和 PyTorch 预测特斯拉股价

下面的脚本执行以下任务：

- 使用 SparkSession 从 CSV 文件加载股价数据
- 通过组装特征向量并对它们进行缩放来预处理数据
- 将预处理后的数据拆分为训练集和测试集
- 将数据转换为 PyTorch 张量，并加载到 DataLoader 对象中以进行批处理
- 定义、训练和评估用于预测特斯拉股价的深度模型
- 保存训练好的模型以备将来使用

```python
[In]: import logging
[In]: import subprocess
[In]: from typing import Tuple
[In]: import numpy as np
[In]: import torch
[In]: import torch.nn as nn
[In]: import torch.optim as optim
[In]: from torch.utils.data import DataLoader, TensorDataset
[In]: from pyspark.sql import SparkSession
[In]: from pyspark.ml.feature import VectorAssembler, StandardScaler
[In]: from pyspark.sql import DataFrame
[In]: logging.basicConfig(level=logging.INFO)
[In]: logger = logging.getLogger(__name__)

[In]: def load_data(file_path: str) -> DataFrame:
    """
    Load stock price data from a CSV file using
    SparkSession.
    """
    try:
        spark = (SparkSession.builder
                 .appName("StockPricePrediction")
                 .getOrCreate())
        df = spark.read.csv(
                    file_path,
                    header=True,
                    inferSchema=True
                )
        return df
    except Exception as e:
        raise RuntimeError(
            f"Error loading data from {file_path}: {e}"
        )

[In]: def preprocess_data(df: DataFrame) -> DataFrame:
    """
    Preprocess the data by assembling feature
    vectors using
    VectorAssembler and scaling them using
    StandardScaler.
    """
    assembler = VectorAssembler(
        inputCols=['Open', 'High', 'Low', 'Volume'],
        outputCol='features'
    )
    df = assembler.transform(df)
    scaler = StandardScaler(
        inputCol="features",
        outputCol="scaled_features",
        withStd=True,
        withMean=True
    )
    scaler_model = scaler.fit(df)
    df = scaler_model.transform(df)
    df = df.select('scaled_features', 'Close')
    return df

[In]: def create_data_loader(
    features,
    labels,
    batch_size=32,
    num_workers=4) -> DataLoader:
    """
    Convert the preprocessed data into PyTorch tensors and create DataLoader objects for both the training and test sets.

    Args:
        features (Tensor): The input features.
        labels (Tensor): The corresponding labels.
        batch_size (int):
            The number of samples per batch to load.
            Defaults to 32.
        num_workers (int):
            The number of subprocesses to use for data
            loading.
            Defaults to 4.

    Returns:
        DataLoader: A PyTorch DataLoader for the dataset.
    """
    dataset = TensorDataset(features, labels)
    return DataLoader(
        dataset,
        batch_size=batch_size,
        shuffle=True
    )

[In]: def train_model(
        model,
        train_loader,
        criterion,
        optimizer,
        num_epochs
    ):
        """
        Train the model on the training data using the
        DataLoader and the defined loss function and
        optimizer. Iterate over the data for a specified
        number of epochs, calculate the loss, and update the
        model parameters.
        """
        for epoch in range(num_epochs):
            for inputs, labels in train_loader:
                optimizer.zero_grad()
                outputs = model(inputs)
                loss = criterion(outputs, labels.unsqueeze(1))
                loss.backward()
                optimizer.step()
            logger.info(
                f"Epoch [{epoch + 1}/{num_epochs}],"
                f"Loss: {loss.item():.4f}"
            )

[In]: def evaluate_model(
            model,
            test_loader,
            criterion
    ) -> Tuple[float, float]:
        """
        Evaluate the trained model on the test data to assess
        its performance.
        Calculate the test loss and additional evaluation
        metrics such as the R-squared score.
        """
        with torch.no_grad():
            model.eval()
            predictions = []
            targets = []
            test_loss = 0.0
            for inputs, labels in test_loader:
                outputs = model(inputs)
                loss = criterion(outputs, labels.unsqueeze(1))
                test_loss += loss.item() * inputs.size(0)
                predictions.extend(outputs.squeeze().tolist())
            targets.extend(labels.tolist())

            test_loss /= len(test_loader.dataset)
            predictions = torch.tensor(predictions)
            targets = torch.tensor(targets)
            ss_res = torch.sum((targets - predictions) ** 2)
            ss_tot = torch.sum((targets - torch.mean(targets)) ** 2)
            r_squared = 1 - ss_res / ss_tot
            logger.info(f"Test Loss: {test_loss:.4f}")
            logger.info(f"R-squared Score: {r_squared:.4f}")
            return test_loss, r_squared.item()

[In]: def main(
        data_file_path: str,
        num_epochs: int = 100,
        batch_size: int = 32,
        learning_rate: float = 0.001
    ):
        """
        Main function for training and evaluating a deep
        learning model for Tesla stock price prediction.

        Args:
            data_file_path (str): The path to the CSV file
            containing stock price data.
            num_epochs (int): The number of epochs for
            training the model. Defaults to 100.
            batch_size (int): The batch size for data loading
            during training. Defaults to 32.
            learning_rate (float): The learning rate for the
            optimizer. Defaults to 0.001.
        """
```





### 比较和绘制实际值与预测值

下面的脚本执行以下操作：

- 从包含股票价格数据的 CSV 文件中加载测试数据
- 通过使用从 `tesla_stock_price_prediction` 模块导入的 `preprocess_data` 函数对特征进行缩放，对数据进行预处理
- 使用 PyTorch 定义神经网络模型架构
- 从文件中加载预训练的模型权重
- 使用加载的模型对预处理后的测试数据进行预测
- 并排打印前十个实际股票价格和预测价格
- 在折线图上绘制所有实际值和预测值以进行可视化

```python
import torch
import numpy as np
import matplotlib.pyplot as plt
from tesla_stock_price_prediction import (
    load_data,
    preprocess_data
)
```

```python
def main():
    """
    加载测试数据，进行预处理，并使用预训练模型
    进行预测。
    
    此函数从 CSV 文件中加载测试数据，
    对其进行预处理，加载预训练的 PyTorch 模型，
    对测试数据进行预测，并可视化
    实际与预测的股票价格。
    """
    test_data_file_path = \
        "/home/ubuntu/airflow/dags/TSLA_stock.csv"
    test_data = load_data(test_data_file_path)
    test_data = preprocess_data(test_data)
    
    test_features = \
        test_data.select('scaled_features').collect()
    
    test_features = np.array([
        row.scaled_features.toArray()
        for row in test_features
    ],
        dtype=np.float64)
    
    input_size = 4
    output_size = 1
    model = torch.nn.Sequential(
        torch.nn.Linear(input_size, 64),
        torch.nn.ReLU(),
        torch.nn.Linear(64, 32),
        torch.nn.ReLU(),
        torch.nn.Linear(32, 16),
        torch.nn.ReLU(),
        torch.nn.Linear(16, output_size)
    )
    model.load_state_dict(
        torch.load(
            '/home/ubuntu/airflow/dags/trained_model.pth',
            map_location=torch.device('cpu')
        )
    )
    model.eval()
    test_features_tensor = torch.tensor(
        test_features,
        dtype=torch.float64
    )
    model = model.double()
    with torch.no_grad():
        predictions = model(
            test_features_tensor
        ).squeeze().numpy()
    actual_labels = test_data.select('Close').collect()
    actual_labels = np.array(
        [
            row.Close for row in actual_labels
        ],
        dtype=np.float64
    )
    
    actual_labels = actual_labels[:-1]
    predictions = predictions[:-1]

    print("Top 10 Actual vs Predicted Values:")
    print("Actual\tPredicted")
    for i in range(10):
        print(f"{actual_labels[i]:.4f}\t{predictions[i]:.4f}")

    plt.figure(figsize=(10, 6))
    plt.plot(actual_labels, label='Actual')
    plt.plot(predictions, label='Predicted')
    plt.xlabel('Index')
    plt.ylabel('Price')
    plt.title(
        'Actual vs Predicted Tesla Stock Prices\n(Feb 26, 2019 to Feb 23, 2024)'
    )
    plt.legend()
    plt.grid(True)
    plt.show()

if __name__ == "__main__":
    main()
```

# 摘要

在本章中，我们开始了使用 PyTorch 进行深度学习的探索。我们的重点是回归，这是机器学习中的一项基本任务，旨在预测连续的数值。我们讨论了深度学习在回归方面的优势，例如它能够捕捉数据中的复杂模式和关系，这对于具有非线性和交互作用的数据集特别有用。然而，我们也承认了这些模型的黑盒特性，这使得解释变得困难。更重要的是，我们强调了深度学习算法的计算强度，这是一个挑战，可以通过使用 Amazon Web Services (AWS) 作为可扩展云计算基础设施的解决方案来缓解，这对于高效部署和运行深度学习模型至关重要。

我们通过构建和评估一个用于预测特斯拉股票价格的神经网络，展示了 PyTorch 在回归中的应用，结果显示其具有低 MSE 和高 R-squared 分数表现强劲。此外，我们还简要讨论了早停和过拟合，这些主题我们将在第 9 章中进一步探讨。

在下一章中，我们将展示如何使用 TensorFlow 遵循类似的步骤，重现使用 PyTorch 的过程。我们将使用相同的特斯拉股票数据集进行模型比较，以便直接评估两个框架中实现的模型的性能和特征。

# 第 5 章

# 使用 TensorFlow 进行回归深度学习

在上一章中，我们开始了探索用于回归任务的深度学习模型的旅程。我们训练并评估了一个 PyTorch 模型，并使用它来预测特斯拉的每日股票价格。在本章中，我们将展示如何使用 TensorFlow 复制相同的过程。我们将使用相同的数据集来直接比较两个框架中模型的性能。此外，我们将利用 PySpark 的分布式计算能力来预处理该数据集。

值得注意的是，与上一章讨论的传统预测模型（如线性回归）相比，深度学习算法的优缺点在当前章节中仍然适用。

本章首先回顾了特斯拉股票数据集的样子，随后构建、训练并评估了 TensorFlow 回归模型。接着，它将本章讨论的代码片段结合起来，最后以对关键要点的总结收尾。

## 数据集

我们将使用从 Yahoo! Finance 获取的相同特斯拉股票每日历史数据集。该数据集以 CSV 格式下载，然后存储位于 Amazon Web Services (AWS) S3 中名为 “instance1bucket” 的桶中，链接如下：

<https://finance.yahoo.com/quote/TSLA/history/>

我们在第 3 章中详细探索了这个数据集，并在第 4 章中使用它来训练和评估 PyTorch 深度学习回归模型。作为提醒，以下是数据集中的前五个观测值：

| 日期 | 开盘价 | 最高价 | 最低价 | 收盘价 | 成交量 |
| :--- | :--- | :--- | :--- | :--- | :--- |
| 2/23/24 | 195.31 | 197.57 | 191.50 | 191.97 | 78670300 |
| 2/22/24 | 194.00 | 198.32 | 191.36 | 197.41 | 92739500 |
| 2/21/24 | 193.36 | 199.44 | 191.95 | 194.77 | 103844000 |
| 2/20/24 | 196.13 | 198.60 | 189.13 | 193.76 | 104545800 |
| 2/16/24 | 202.06 | 203.17 | 197.40 | 199.95 | 111173600 |

该数据集涵盖从 2019 年 2 月 26 日到 2024 年 2 月 23 日，包含 1,258 个观测值。每个交易日都记录了特斯拉股价的实时波动。这些观测值提供了关于关键指标——开盘价、最高价、最低价、收盘价和成交量——的见解，描绘了特定时间段内的价格变动。

它们的定义如下：

- **开盘价 (Open)**：给定日期特斯拉股票的开盘价格
- **最高价 (High)**：给定日期交易时段内特斯拉股票达到的最高价格




- **Low：** 在给定日期的交易时段内，特斯拉股票达到的最低价格
- **Close：** 给定日期特斯拉股票的收盘价
- **Volume：** 成交量，代表在给定日期内交易的所有股份总数

## 使用 TensorFlow 预测特斯拉股价

在本节中，我们将利用前一章节概述的数据集来实现一种深度学习算法，旨在预测特斯拉的股价。该数据集包含主要特征，包括开盘价（Open）、最高价（High）、最低价（Low）和成交量（Volume），其中收盘价（Close）作为目标变量。通过将这些特征整合到我们的预测模型中，我们可以有效地捕捉基本市场动态（如开盘情绪和交易活动）以及技术方面（如价格波动和交易范围），这些对于精确的股价预测都至关重要。

必须认识到，我们的模型目的是示意性的，而非详尽无遗的。虽然当前的特征集提供了有价值的见解，但纳入技术指标、基本面数据或市场情绪等额外特征可以进一步增强我们模型的预测能力。然而，这些增强超出了本章的范围。

为了便于数据处理，我们利用 PySpark 的分布式计算能力，同时使用 TensorFlow 构建和训练神经网络模型。Python 代码支持端到端的工作流，从数据加载开始，最终进行模型评估。在第 8 章中，我们将展示如何使用 Apache Airflow 部署此代码。

在本章中，我们对方法采用了面向对象的途径。这标志着比前一章节有了进一步的进步，因为我们引入了一个名为 `TSLARegressor` 的类。该类作为中心化枢纽，用于组织和协调对 TSLA 股价进行回归分析所需的各项功能。在该类内部，每个方法都专门负责回归工作流程中的特定任务，包括数据加载、特征预处理、模型创建与训练、性能评估以及预测生成。

虽然前一章节中使用的函数式方法仍然有效，但转向面向对象的方法带来了诸多益处。通过将功能封装在类中，我们增强了代码的模块化、可读性和可重用性。这种结构化的方法简化了回归分析工作流的开发和维护。此外，利用类使我们能够实现更好的代码组织和抽象，随着项目的演变，便于管理和扩展。

然而，建模步骤与前一章节相同，包括以下内容：

- 导入模块
- 日志配置
- 数据加载
- 数据预处理
- 创建数据加载器
- 模型训练
- 模型评估
- 主函数
- 执行

让我们查看代码并详细深入了解这些步骤，从导入开始。

### 步骤 1：导入模块

```python
import logging
import numpy as np
import tensorflow as tf
from pyspark.sql import SparkSession
from pyspark.ml.feature import VectorAssembler, StandardScaler
from sklearn.metrics import r2_score
from tensorflow.keras.models import Sequential
from tensorflow.keras.layers import Dense
import matplotlib.pyplot as plt
```

- `import logging`：此导入用于在代码中启用日志记录功能，允许我们在执行期间记录信息、警告和错误。在我们接下来的代码中，logging 模块将用于在 `main()` 函数中记录关于测试损失和 R2 分数的信息。此外，当发生异常时，它还用于记录错误。

- `import numpy as np`：此导入将 NumPy 模块别名为 `np`，使引用更加便捷。在我们的代码中，NumPy 将用于数组操作和数学运算。具体而言，它将在 `TSLARegressor` 类的 `convert_to_numpy()` 方法中用于将 Spark 数据帧转换为 NumPy 数组以进行进一步处理。

- `import tensorflow as tf`：这是我们的 TensorFlow 深度学习框架。它在代码中广泛用于构建、训练和评估我们的神经网络模型。它用于创建 Sequential 模型及其层，使用优化器和损失函数编译模型，训练模型并评估其性能。

- `from pyspark.sql import SparkSession`：此行从 `pyspark.sql` 模块导入 SparkSession 类，这对于创建 SparkSession 对象是必需的。在代码中，SparkSession 用于创建用于 Spark 相关操作的 SparkSession 对象，例如从 CSV 文件读取数据和创建 Spark 数据帧。

- `from pyspark.ml.feature import VectorAssembler, StandardScaler`：此行从 `pyspark.ml.feature` 模块导入 VectorAssembler 和 StandardScaler 类，它们用于特征工程和预处理。在代码中，这些类在 `preprocess_data()` 方法中用于组装特征向量并在训练模型前对特征进行标准化。

- `from sklearn.metrics import r2_score`：此行从 `sklearn.metrics` 模块导入 r2_score 函数，用于计算 R 方分数（R-squared score），这是一种评估回归模型性能的指标。在代码中，r2_score 在 `predict_and_evaluate()` 方法中用于计算训练模型的 R2 分数。

- `from tensorflow.keras.models import Sequential`：此行从 `tensorflow.keras.models` 模块导入 Sequential 类，用于在 TensorFlow Keras 中创建顺序神经网络模型。在代码中，Sequential 在 `create_and_train_model()` 方法中用于定义神经网络模型的架构。

- `from tensorflow.keras.layers import Dense`：此行从 `tensorflow.keras.layers` 模块导入 Dense 层类，用于向神经网络模型添加全连接层。在代码中，Dense 层在 `create_and_train_model()` 方法中用于定义神经网络模型的隐藏层。

- `import matplotlib.pyplot as plt`：此行从 Matplotlib 库导入 pyplot 模块，用于创建图表和绘图等可视化。在代码中，pyplot 在 `plot_actual_vs_predicted()` 函数中用于创建实际值与预测值的散点图。

### 步骤 2：类定义

在此步骤中，我们定义一个类，封装数据加载、预处理、模型创建、训练、评估和预测等各种方法：

```python
class TSLARegressor:
    """
    TSLA 股价回归类。
    """
    def __init__(self):
        """
        初始化 TSLARegressor 对象。
        """
        self.logger = logging.getLogger(__name__)
        self.spark = (SparkSession.builder
                      .appName("TSLA_Regression")
                      .getOrCreate())
        self.input_shape = None
        self.model = None
```

该代码定义了一个名为 `TSLARegressor` 的 Python 类，它作为创建能够执行 TSLA（特斯拉）股价回归任务的对象的蓝图。

让我们分解一下代码：

- `class TSLARegressor:`：此行启动了对名为 `TSLARegressor` 的类的定义。
- `""" Class for TSLA stock price regression. """`：这是一个文档字符串（docstring），提供该类目的的简要描述，即对 TSLA 股价执行回归分析。
- `def __init__(self):`：这是 `TSLARegressor` 类的初始化方法（构造函数）。当创建该类对象时自动调用。
- `""" Initialize TSLARegressor object. """`：这是 `__init__` 方法的文档字符串，提供其目的的简要描述。
- `self.logger = logging.getLogger(__name__)`：此行为 `TSLARegressor` 类的每个对象创建一个名为 `logger` 的实例属性。它将 logging 模块中的 logger 对象分配给 `logger` 属性。此 logger 用于在代码执行期间记录信息、警告和错误。
- `self.spark = SparkSession.builder.appName("TSLA Regression").getOrCreate()`: 此行为每个对象创建一个名为 `spark` 的实例属性，用于...





## 步骤 2：TSLARegressor 类

`TSLARegressor` 类使用 `SparkSession.builder` 创建一个 `SparkSession` 对象，通过 `appName()` 将应用程序名称设置为“TSLA_Reğression”，并使用 `getOrCreate()` 获取现有的 SparkSession 或创建一个新的 SparkSession。此 SparkSession 用于 Spark 相关操作，例如从 CSV 文件读取数据以及创建 Spark 数据帧（DataFrame）。

- `self.input_shape = None`：这行代码创建了一个名为 `input_shape` 的实例属性，并将其初始化为 None。该属性旨在存储神经网络模型的输入数据形状。
- `self.model = None`：这行代码创建了一个名为 `model` 的实例属性，并将其初始化为 None。该属性旨在存储训练好的神经网络模型。

在后续步骤中，我们将在 `TSLARegressor` 类内定义一系列方法，用于数据加载、预处理、模型创建、训练、评估和预测。

### 步骤 3：`preprocess_data` 方法定义

在本步骤中，我们在 `TSLARegressor` 类内定义 `preprocess_data()` 方法。模型的特征在经过 PySpark 的 `VectorAssembler` 从加载的数据中组装时 undergo 转换，该工具将多个列整合为单一的特征向量。随后，使用 `StandardScaler` 对特征进行缩放，以标准化每个特征的值，确保均值为 0 且标准差为 1：

```python
[In]: def preprocess_data(
    self,
    file_path,
    feature_cols=['Open', 'High', 'Low', 'Volume'],
    train_ratio=0.8,
    seed=42
):
    """
    Preprocesses the data.

    Parameters:
        - file_path (str): Path to the CSV file.
        - feature_cols (list): List of feature columns.
        - train_ratio (float): Ratio of training data.
        - seed (int): Random seed for splitting data.

    Returns:
        - tuple: Tuple containing train and test DataFrames.
    """
    df = self.spark.read.csv(
        file_path,
        header=True,
        inferSchema=True
    )
    assembler = VectorAssembler(
        inputCols=feature_cols,
        outputCol='features'
    )
    df = assembler.transform(df)
    scaler = StandardScaler(
        inputCol='features',
        outputCol='scaled_features',
        withMean=True,
        withStd=True
    )
    scaler_model = scaler.fit(df)
    df = scaler_model.transform(df)
    train_df, test_df = df.randomSplit(
        [train_ratio, 1-train_ratio],
        seed=seed
    )
    return train_df, test_df
```

该方法为训练 TensorFlow 神经网络模型准备数据。

以下是其功能分解：

- **读取数据**：该方法使用 PySpark 的 `read.csv()` 方法将位于 `file_path` 的 CSV 文件读取到 Spark 数据帧中。`header=True` 参数表示第一行包含列名，而 `inferSchema=True` 启用自动模式（schema）推断。
- **特征组装**：使用 PySpark 的 `VectorAssembler`，该方法将指定的特征列（`['Open', 'High', 'Low', 'Volume']`）合并为名为 `'features'` 的单一特征向量列。这种整合便于将特征作为单个实体进行处理。
- **特征缩放**：使用 PySpark 的 `StandardScaler` 对特征向量列 `'features'` 进行缩放，以确保每个特征的均值为 0，标准差为 1。此归一化步骤有助于防止具有较大数值的特征主导训练过程，并确保特征对模型的贡献是均等的。
- **数据划分**：最后，该方法使用 Spark 的 `randomSplit()` 方法将数据帧划分为训练集和测试集。`train_ratio` 参数确定训练数据的比例，而 `seed` 参数通过提供数据划分的随机种子来确保持可复现性。
- **返回**：该方法返回一个包含训练数据帧和测试数据帧的元组。

### 步骤 4：`convert_to_numpy` 方法定义

在本步骤中，我们定义 `convert_to_numpy` 方法，该方法负责将分别包含训练数据和测试数据的 Spark 数据帧 `train_df` 和 `test_df` 转换为 NumPy 数组：

```python
[In]: def convert_to_numpy(self, train_df, test_df):
       """
       Convert Spark DataFrames to numpy arrays.

       Parameters:
       - train_df (DataFrame): Spark DataFrame containing training data.
       - test_df (DataFrame): Spark DataFrame containing test data.

       Returns:
       - tuple: Tuple containing train and test numpy arrays
         for features and labels.
       """
       train_features = np.array(
           train_df.select('scaled_features')
           .rdd.map(lambda x: x.scaled_features.toArray())
           .collect()
       )
       train_labels = np.array(
           train_df.select('Close')
           .rdd.map(lambda x: x.Close).collect())
       test_features = np.array(
           test_df.select('scaled_features')
           .rdd.map(lambda x: x.scaled_features.toArray())
           .collect()
       )
       test_labels = np.array(
           test_df.select('Close')
           .rdd.map(lambda x: x.Close).collect()
       )
       return train_features, train_labels, \
           test_features, test_labels
```

`convert_to_numpy` 方法通过将 Spark 数据帧转换为 NumPy 数组来实现与 TensorFlow 的兼容性，因为 TensorFlow 通常处理 NumPy 数据结构。它接受两个参数：`train_df` 和 `test_df`，它们是分别包含训练数据和测试数据的 Spark 数据帧。

该方法返回一个包含四个 NumPy 数组的元组：`train_features`、`train_labels`、`test_features` 和 `test_labels`。方法内部的转换过程如下：

- `train_features`：将训练数据帧（`train_df`）的 `'scaled_features'` 列转换为 NumPy 数组
- `train_labels`：将训练数据帧（`train_df`）的 `'Close'` 列转换为 NumPy 数组
- `test_features`：将测试数据帧（`test_df`）的 `'scaled_features'` 列转换为 NumPy 数组
- `test_labels`：将测试数据帧（`test_df`）的 `'Close'` 列转换为 NumPy 数组

在实现上，该方法使用 Spark 的 `select` 方法从数据帧中提取特定列。然后，它将这些列转换为 RDD（弹性分布式数据集）以启用并行处理。对 RDD 的每一行应用 `map` 函数以提取所选列的值，随后使用 `np.array` 函数将它们转换为 NumPy 数组。最后，从 RDD 中收集 NumPy 数组，并作为元组的一部分返回。

### 步骤 5：`create_and_train_model` 方法定义

接下来，我们定义 `create_and_train_model` 方法，该方法负责使用 TensorFlow 的 Keras API 构建并训练神经网络模型：

```python
[In]: def create_and_train_model(
                self,
                train_features,
                train_labels,
                epochs=100,
                batch_size=32
        ):
            """
            Create and train the neural network model.

            Parameters:
            - train_features (ndarray): Training features.
            - train_labels (ndarray): Training labels.
            - epochs (int): Number of epochs for training.
            - batch_size (int): Batch size for training.

            Returns:
            - None
            """
            self.input_shape = (train_features.shape[1],)
            self.model = Sequential([
                Dense(64, activation='relu',
                        input_shape=self.input_shape),
                Dense(32, activation='relu'),
                Dense(16, activation='relu'),
                Dense(1)
            ])
            self.model.compile(optimizer='adam', loss='mse')
            self.model.fit(
                train_features,
                train_labels,
                epochs=epochs,
                batch_size=batch_size
            )
```

`create_and_train_model` 方法负责创建具有指定架构的 TensorFlow 神经网络模型，并使用提供的训练特征和标签进行训练。

以下是该方法的参数及其功能分解：

**参数：**

- `train_features` (ndarray)：包含训练特征的 NumPy 数组。
- `train_labels` (ndarray)：包含相应训练标签的 NumPy 数组。





- epochs (int): 训练过程中的轮数（对完整数据集的迭代次数）。默认值设为 100。
- batch_size (int): 每次梯度更新处理的样本数。默认值设为 32。

返回：
- None

### 模型架构
- 该方法初始化了一个顺序模型（Sequential），这是一个线性的层堆栈。向模型中添加了四个具有不同配置的密集层（dense layers）：
    - 第一层（Dense(64, activation='relu', input_shape=self.input_shape)）拥有 64 个单元，使用 ReLU 激活函数，并接受由特征数量定义的输入形状。
    - 后续层（Dense(32, activation='relu'), Dense(16, activation='relu')）分别拥有 32 个和 16 个单元，均使用 ReLU 激活函数。
    - 最后一层（Dense(1)）拥有单个单元，代表输出层。

### 编译
- 使用 Adam 优化器（optimizer='adam'）和均方误差损失函数（loss='mse'）对模型进行编译。

### 训练
- 使用训练特征和标签对编译后的模型进行训练（self.model.fit）。训练过程运行指定的轮数（epochs），并使用指定的批次大小（batch_size）。

### 超参数选择
- 轮数（Epochs）：选择 100 轮是基于神经网络训练中的常见做法，旨在平衡学习数据模式与避免过拟合之间的关系。虽然没有进行大规模的实验，但 100 轮是一个合理的起点，通常允许模型收敛。
- 批次大小（Batch Size）：选择批次大小为 32，因为它是广泛接受的标准，在计算效率和模型准确性之间取得了平衡。这是一个常用的默认值，在大多数情况下表现良好，在训练速度和泛化能力之间提供了良好的权衡。

## 步骤 6：evaluate_model 方法定义

在此步骤中，我们在 TSLARegressor 类内创建 evaluate_model 方法，该方法负责使用测试数据评估已训练的神经网络模型：

```python
[In]: def evaluate_model(self, test_features, test_labels):
    """
    Evaluate the trained model.
    
    Parameters:
    - test_features (ndarray): Test features.
    - test_labels (ndarray): Test labels.
    
    Returns:
    - float: Test loss.
    """
    test_loss = self.model.evaluate(test_features, test_labels)
    return test_loss
```

evaluate_model 方法通过计算测试数据上的损失来评估已训练的神经网络模型。

以下是该方法的参数及其功能的解释：

### 参数
- test_features (ndarray)：包含测试特征的 NumPy 数组
- test_labels (ndarray)：包含相应测试标签的 NumPy 数组

### 返回
- float：测试损失，指示模型在测试数据上的表现

### 评估
- 该方法使用已训练模型（self.model）的 evaluate 函数来计算测试数据上的损失。
- 它向 evaluate 函数传入测试特征和标签，该函数根据模型的预测和真实标签计算损失。

### 测试损失
- 计算出的测试损失作为方法的输出返回。该值提供了关于模型在未见数据上表现的见解。测试损失越低，表明表现越好，因为这意味着模型的预测更接近真实标签。

## 步骤 7：predict_and_evaluate 方法定义

在此步骤中，我们创建 predict_and_evaluate 方法，该方法的作用是预测值使用已训练的神经网络模型，然后根据 R 平方分数评估其性能：

```python
[In]: def predict_and_evaluate(self, test_features, test_labels):
        """
        Predict and evaluate the neural network model.
        
        Parameters:
            - test_features (ndarray): Test features.
            - test_labels (ndarray): Test labels.
            
        Returns:
            - float: R2 score.
        """
        test_predictions = self.model.predict(test_features)
        r2_score_value = r2_score(test_labels, test_predictions)
        return r2_score_value
```

该方法使用已训练的神经网络模型（self.model）对测试特征进行预测，并使用 R 平方分数评估其性能。

让我们分解该方法的参数和功能：

### 参数
- test_features (ndarray)：包含测试特征的 NumPy 数组
- test_labels (ndarray)：包含相应测试标签的 NumPy 数组

### 返回
- float：R 平方分数，衡量因变量（测试标签）中方差中有多少比例可以由自变量（测试特征）在模型中预测

### 预测
- 该方法首先使用已训练模型（self.model）的 predict 函数对测试特征进行预测。
- 预测值存储在变量 test_predictions 中。

### 评估（R 平方分数）
- 然后，该方法通过将预测值（test_predictions）与真实测试标签（test_labels）进行比较来计算 R 平方分数。
- 使用 Scikit-Learn 库中的 r2_score 函数来完成此任务。

### R 平方分数计算
- R 平方分数指示因变量中方差有多大比例可以由自变量预测。
- 较高的 R 平方分数（接近 1）表明因变量中更大比例的方差可以由自变量预测，这意味着模型对数据的拟合更好。
- 计算出的 R 平方分数作为方法的输出返回，提供了模型在测试数据上预测性能的度量。

## 步骤 8：plot_actual_vs_predicted 函数定义

我们现在位于 TSLARegressor 类之外。我们创建 plot_actual_vs_predicted 函数，该函数使用 Matplotlib 绘制测试数据的实际值与预测值：

```python
[In]: def plot_actual_vs_predicted(tsla_regressor, test_features, test_labels):
    """
    Plot actual vs. predicted values.

    Parameters:
      - tsla_regressor (TSLARegressor):
        Instance of TSLARegressor class.
      - test_features (ndarray): Test features.
      - test_labels (ndarray): Test labels.

    Returns:
      - None
    """
    test_predictions = tsla_regressor.model.predict(test_features)

    print("Actual    Predicted")
    for actual, predicted in zip(test_labels, test_predictions):
        print(f"{actual:.2f}  {predicted[0]:.2f}")

    plt.figure(figsize=(10, 6))
    plt.scatter(test_labels, test_predictions, color='blue')
    plt.plot(
        [test_labels.min(), test_labels.max()],
        [test_labels.min(), test_labels.max()],
        'k--', lw=3
    )
    plt.xlabel('Actual')
    plt.ylabel('Predicted')
    plt.title('Actual vs. Predicted Values')
    plt.show()
```

让我们分解该函数完成的内容：

### 参数
- tsla_regressor (TSLARegressor)：TSLARegressor 类的实例，包含已训练的神经网络模型（model）
- test_features (ndarray)：包含测试特征的 NumPy 数组
- test_labels (ndarray)：包含相应测试标签的 NumPy 数组

### 返回
- None

### 预测
- 该函数首先使用已训练的神经网络模型（tsla_regressor.model.predict(test_features)）预测测试特征的值。
- 预测值存储在变量 test_predictions 中。

### 打印实际值与预测值
- 该函数并排打印实际值和预测值以供比较。
- 它通过循环遍历每一对实际值和预测值，并将它们格式化为两位小数进行打印。

### 绘制实际值与预测值
- 该函数创建一个散点图，以可视化实际值和预测值之间的关系。
- 实际值绘制在 x 轴上（test_labels），预测值绘制在 y 轴上（test_predictions）。
- 此外，还绘制了一条对角虚线，代表实际值和预测值相同的理想场景。

### 图表定制
- 该函数通过设置 x 轴和 y 轴的标签以及提供标题来定制图表。
- 使用 plt.show() 显示图表。

### 可视化
- 此可视化允许直观地评估模型的预测值与实际值的匹配程度。
- 点沿对角虚线紧密聚集，表明实际值和预测值之间存在强相关性，意味着模型表现良好。




## 第 9 步：主函数定义

在本步骤中，我们创建主函数，它作为主要入口点来协调脚本的整个工作流。它接受一个参数 `file_path`，代表包含待处理数据的 CSV 文件的路径：

```python
def main(file_path):
    """
    主函数，用于协调整个工作流。
    
    参数:
        - file_path (str): CSV 文件的路径。
    
    返回:
        - None
    """
    try:
        tsla_regressor = TSLARegressor()
        train_df, test_df = \
            tsla_regressor.preprocess_data(file_path)
        train_features, train_labels, test_features, \
        test_labels = tsla_regressor.convert_to_numpy(
            train_df,
            test_df
        )
        tsla_regressor.create_and_train_model(
            train_features,
            train_labels
        )
        test_loss = tsla_regressor.evaluate_model(
            test_features,
            test_labels
        )
        r2_score_value = tsla_regressor.predict_and_evaluate(
            test_features,
            test_labels
        )

        logging.info("Test Loss: {}".format(test_loss))
        logging.info("R2 Score: {}".format(r2_score_value))

        plot_actual_vs_predicted(
            tsla_regressor,
            test_features,
            test_labels
        )

    except Exception as e:
        logging.error(f"An error occurred: {e}")
```

该函数首先实例化 `TSLARegressor` 类的一个对象，命名为 `tsla_regressor`。然后，它调用 TSLARegressor 实例的 `preprocess_data` 方法来预处理指定 CSV 文件中的数据。处理后的数据被拆分为训练集和测试集。接着，调用 `convert_to_numpy` 方法将包含训练和测试数据的 Spark DataFrame 转换为 NumPy 数组，以便进一步处理。随后，调用 `create_and_train_model` 方法，使用训练特征和标签创建并训练神经网络模型。模型训练完成后，使用 `evaluate_model` 方法评估模型在测试数据上的表现，计算测试损失。此外，调用 `predict_and_evaluate` 方法对测试数据进行预测并计算 R2 分数。最后，函数使用 logging 模块记录测试损失和 R2 分数。如果在工作流执行过程中发生异常，该异常会被捕获，并使用 logging 模块记录错误信息。

## 第 10 步：条件代码块

在最后一步中，条件代码块检查脚本是否作为主程序直接运行：

```python
if __name__ == "__main__":
    logging.basicConfig(level=logging.INFO)
    file_path = "/home/ubuntu/airflow/dags/TSLA_stock.csv"
    main(file_path)
```

-   `if __name__ == "__main__":`：此条件检查脚本是否被直接执行，而不是作为模块被导入到另一个脚本中。
-   `logging.basicConfig(level=logging.INFO)`：此行配置日志系统以显示 INFO 级别或更高级别的日志消息。这确保了严重级别为 INFO 或更高的日志消息会被显示。
-   `file_path = "/home/ubuntu/airflow/dags/TSLA_stock.csv"`：此行定义了包含 TSLA 股票数据的 CSV 文件的路径。
-   `main(file_path)`：此行调用主函数，并传入指定的 `file_path` 作为参数。主函数将协调脚本的整个工作流，包括数据预处理、模型训练、性能评估以及绘制实际值与预测值的对比图。

为了运行代码，我们将代码保存为“tesla_stock_price_prediction.py”并在 Jupyter Lab 终端中执行（我们也可以在 EC2 实例上直接运行）。由于我们创建了一个名为“myenv”的环境，我们按以下方式激活它：

```bash
source /home/ubuntu/myenv/bin/activate
```

在激活环境后，我们使用 Python 3 通过以下命令执行代码：

```bash
python3 tesla_stock_price_prediction.py
```

现在，让我们查看代码的输出。

第一个输出显示了在 TSLA 股票价格回归模型训练和评估过程中获得的训练损失、测试损失和 R2 分数：

训练损失：

| 轮次 (Epoch) | 损失 (Loss) |
| :--- | :--- |
| 1 | 41,731 |
| 2 | 40,362 |
| 3 | 39,658 |
| 4 | 33,450 |
| 5 | 19,520 |
| 6 | 5,492 |
| 7 | 2,532 |
| 8 | 1,984 |
| 9 | 1,657 |
| 10 | 1,231 |
| ... | ... |
| 100 | 14 |

测试损失：12.11

R2 分数：0.998

我们现在将逐一解释这些指标：

**训练损失：**
-   它显示了训练过程中每个轮次（epoch）的训练损失。
-   每一行代表一个轮次以及该轮次对应的损失值。
-   随着训练的推进，损失逐渐降低。这表明模型正在学习更好地拟合训练数据。最初，损失相对较高，但随着每个轮次的进行迅速降低，直至收敛到一个较低的值。在我们的输出中，训练损失从 41,731 显著降低到 14，表明模型正在学习并改善对训练数据的拟合程度。

**测试损失：**
-   它代表在模型训练完成后，在测试数据集上计算得出的损失（均方误差）。
-   测试损失指示了已训练的模型对未见数据的泛化能力。
-   在我们的输出中，测试损失约为 12，这意味着在测试数据上，模型的预测平均偏差为这个数值（以与目标变量相同的单位衡量，对于股票价格而言是美元）。

**R2 分数：**
-   R2 分数（也称为决定系数）是一个统计量，表示因变量（在此情况下为股票价格）的方差中，可以由自变量（特征）预测的比例。
-   它的取值范围从 0 到 1，1 表示完美拟合。
-   在我们的输出中，R2 分数为 0.998，这意味着模型可以解释测试数据中约 99.8% 的方差，表明具有极高的预测准确性。

综上所述，输出表明模型训练有效，训练损失随轮次增加而降低，且评估指标（测试损失和 R2 分数）显示其在未见数据上表现良好。

代码的第二个输出是前十个 TSLA 实际股票价格与回归模型预测价格的对比：

| 实际值 (Actual) | 预测值 (Predicted) | 百分比差异 (% Difference) |
| :--- | :--- | :--- |
| 118.85 | 117.87 | -1% |
| 123.22 | 122.63 | 0% |
| 283.15 | 282.61 | 0% |
| 284.8 | 281.55 | -1% |
| 34.57 | 35.09 | 2% |
| 34.03 | 34.17 | 0% |
| 281.52 | 280.22 | 0% |
| 283.48 | 282.09 | 0% |
| 143.75 | 138.58 | -4% |
| 209.14 | 211.78 | 1% |

我们添加了实际值与预测值之间的百分比差异，以便更易于解读。如果预测值低于实际值，百分比差异将为负数，表示低估。如果预测值高于实际值，百分比差异将为正数，表示高估。如果预测值与实际值完全相同，百分比差异将为 0%。

在我们的输出中，对于某些条目，例如第二行（实际值 123.22 对比 预测值 122.63），预测值略低于实际值，导致非常小的负百分比差异（小于 −1%），四舍五入后为 0%。同样，在第五行（实际值 34.57 对比 预测值 35.09）中，预测值略高于实际值，导致约为 2% 的正百分比差异。

总体而言，最大差异为 −4%，且 50% 的预测值与实际值吻合（约 0% 差异），表明匹配度很高。

最终输出是一个散点图，用于可视化所有观测值中实际值与预测值之间的关系。在图 5-1 中，实际值绘制在 x 轴上（test_labels），预测值绘制在 y 轴上（test_predictions）。此外，还绘制了一条对角虚线，以表示实际值与预测值相同的理想情况。





![](img/1c89d4486f90c87568fa6a42d46ae02a_318_0.png)

图 5-1。实际值与预测值

  该图表允许对模型预测值与实际值的吻合程度进行可视化评估。我们可以看到数据点紧密聚集在对角虚线周围，这表明实际值与预测值之间存在强相关性，暗示模型性能良好。

## TensorFlow 与 PyTorch

  利用前一章中我们使用 PyTorch 得到的结果以及本章中使用 TensorFlow 得到的结果，我们现在可以比较这两种模型的性能。通过分析训练损失、测试损失和 R2 分数，我们可以了解这两种算法在预测 TSLA 股票价格方面的表现。

  下表比较了 PyTorch 和 TensorFlow 在前 10 个 epoch 和第 100 个 epoch 的训练损失：

| Epoch | PyTorch | TensorFlow |
| :--- | :--- | :--- |
| 1/100 | 48,533 | 41,731 |
| 2/100 | 40,969 | 40,362 |
| 3/100 | 26,663 | 39,658 |
| 4/100 | 13,865 | 33,450 |
| 5/100 | 3,026 | 19,520 |
| 6/100 | 1,683 | 5,492 |
| 7/100 | 1,077 | 2,532 |
| 8/100 | 475 | 1,984 |
| 9/100 | 1,195 | 1,657 |
| 10/100 | 1,362 | 1,231 |
| ... | ... | ... |
| 100/100 | 11 | 14 |

  基于此数据，我们可以做出以下评论：

- PyTorch 的初始训练损失值通常高于 TensorFlow。
- 两种框架都显示训练损失随着 epoch 的增加而持续下降，表明优化是有效的。
- PyTorch 和 TensorFlow 在损失减少方面表现出相似的趋势，两者最终都收敛到较低的值。
- 在某些 epoch 中，PyTorch 和 TensorFlow 之间的损失值存在微小差异，但总体而言，趋势是可比的。
- 在训练接近尾声时，两种框架都达到了较低的训练损失值，表明模型有效地收敛了。

  关于测试损失和 R 平方分数，我们有以下数据：

| Metric | PyTorch | TensorFlow |
| :--- | :--- | :--- |
| Test loss | 20.54 | 12.11 |
| R-squared | 0.998 | 0.998 |

  该表显示，PyTorch 模型获得的测试损失为 20.54，而 TensorFlow 模型实现了更低的测试损失 12.11。有趣的是，两种模型都表现出几乎相同的 R 平方值 0.998，表明在捕捉测试数据方差方面具有极高的解释力和预测准确性。尽管测试损失存在差异，但可比的 R 平方值表明两种框架在解释 TSLA 股票价格方面都产生了具有相似预测性能的模型。

  虽然这种比较在很大程度上是公平对等的（因为我们使用了相同的特斯拉股票数据集），但在 PyTorch 和 TensorFlow 中实现模型的实际差异超出了数据模型架构的范围。在 TensorFlow 中，静态计算图的使用要求预先定义模型的结构。这种方法允许 TensorFlow 优化图以提高性能，使其特别适合效率至关重要的生产环境。然而，这种静态特性可能会使开发过程变得更加僵化，因为对模型的任何修改都需要重新定义图。这可能会减慢模型优化的迭代过程，尤其是在灵活性至关重要的研究环境中。

  另一方面，PyTorch 的动态计算图允许实时修改，提供更灵活、更直观的开发体验。这种动态性使 PyTorch 在实验阶段具有高度优势，此时模型经常被调整和测试。能够随时更改图简化了调试，允许开发者在运行时检查和修改模型的行为，从而更快地迭代和解决问题。

  此外，每个框架的易用性和生态系统也起着至关重要的作用。TensorFlow，特别是自 TensorFlow 2.0 以来取得的进步以及 Keras 作为其高级 API 的持续集成，变得越来越易于访问和用户友好。该框架的综合生态系统，包括用于部署的工具如 TensorFlow Serving，使其成为从开发到生产的全流程机器学习流水线的可靠选择。

  相比之下，PyTorch 简洁的界面，加上其与 NumPy 等 Python 库的无缝集成，为开发者提供了更直观的体验，特别是对于深度学习新手来说。其生态系统正在快速发展，PyTorch Lightning 和 TorchServe 等工具进一步扩展了其功能。它仍然在研究环境中表现出色，其灵活性和易用性是其显著优势。

  最终，虽然两种框架都是强大且能够交付高性能模型的，但选择 TensorFlow 还是 PyTorch 往往取决于项目的具体需求。TensorFlow 的静态图和稳健的部署工具使其成为生产环境的有力候选者，而 PyTorch 的动态图和直观界面则特别适合研究和实验。

## 综合所有内容

  在本节中，我们将整合本章代码探索中的各种元素，以开发一个内聚的代码库。我们还提供了更多关于为什么为模型选择特定层和激活函数的背景，以帮助读者理解设计选择。此外，我们包含一个 environment.yml 文件，以便读者轻松复制环境。

## 层和激活函数

**层选择：**
  模型使用一系列密集层，分别包含 64、32 和 16 个神经元。这种神经元数量的逐渐减少有助于模型通过更多神经元在初始层中捕获复杂模式，随后的层专注于精炼和降低数据复杂性。这种设计通过逐步缩小模型的关注点来帮助防止过拟合。

**激活函数—ReLU：**
  ReLU（修正线性单元）被用作隐藏层中的激活函数，因为它在处理非线性数据和避免梯度消失问题方面效率很高。ReLU 以加速训练期间的收敛而闻名，使其成为许多深度学习模型的优选，特别是对于涉及股票价格等复杂数据的任务。

**输出层：**
  输出层由一个没有激活函数（线性）的单个神经元组成。这种选择对于旨在预测连续值的回归模型来说很典型。线性激活确保输出可以跨越所有可能的值，这对于准确预测股票价格是必要的。

### environment.yml

  此文件指定了项目中使用的 Python 包版本，使读者能够轻松重建相同的设置。

  以下是配置：

```
name: tsla_regression
channels:
 - defaults
dependencies:
 - python=3.12.3
 - numpy=1.26.4
 - tensorflow=2.17.0
 - pyspark=3.5.2
 - scikit-learn=1.5.1
 - matplotlib=3.9.2
```

### TensorFlow 回归代码

  以下是构建、训练和评估用于预测特斯拉股票价格的 TensorFlow 回归模型的代码：

```python
[In]: import logging
[In]: import numpy as np
[In]: import tensorflow as tf
[In]: from pyspark.sql import SparkSession
[In]: from pyspark.ml.feature import VectorAssembler, StandardScaler
[In]: from sklearn.metrics import r2_score
[In]: from tensorflow.keras.models import Sequential
[In]: from tensorflow.keras.layers import Dense
[In]: import matplotlib.pyplot as plt
[In]: class TSLARegressor:
    """
    Class for TSLA stock price regression.
    """

    def __init__(self):
        """
        Initialize TSLARegressor object.
        """
        self.logger = logging.getLogger(__name__)
        self.spark = (SparkSession.builder
                      .appName("TSLA_Regression")
                      .getOrCreate())
        self.input_shape = None
        self.model = None

[In]:     def preprocess_data(
            self,
            file_path,
            feature_cols=['Open', 'High', 'Low', 'Volume'],
            train_ratio=0.8,
            seed=42
        ):
            """
            Preprocesses the data.

            Parameters:
            - file_path (str): Path to the CSV file.
            - feature_cols (list): List of feature columns.
            - train_ratio (float): Ratio of training data.
            - seed (int): Random seed for splitting data.
            """
```



`

```python
返回：
    - tuple: 包含训练集和测试集 DataFrame 的元组。
"""
df = self.spark.read.csv(
        file_path,
        header=True,
        inferSchema=True
)
 assembler = VectorAssembler(
        inputCols=feature_cols,
        outputCol='features'
)
df = assembler.transform(df)
scaler = StandardScaler(
        inputCol='features',
        outputCol='scaled_features',
        withMean=True,
        withStd=True
)
scaler_model = scaler.fit(df)
df = scaler_model.transform(df)
train_df, test_df = df.randomSplit(
        [train_ratio, 1-train_ratio],
        seed=seed
)
return train_df, test_df
```

```python
[In]: def convert_to_numpy(self, train_df, test_df):
"""
将 Spark DataFrame 转换为 numpy 数组。

参数：
    - train_df (DataFrame):
        包含训练数据的 Spark DataFrame。
    - test_df (DataFrame):
        包含测试数据的 Spark DataFrame。

返回：
    - tuple:
        包含训练集和测试集的 numpy 数组，
        对应于
        特征和标签。
"""
train_features = np.array(
    train_df.select('scaled_features')
    .rdd.map(lambda x: x.scaled_features.toArray())
    .collect()
)
train_labels = np.array(
    train_df.select('Close')
    .rdd.map(lambda x: x.Close).collect()
)
test_features = np.array(
    test_df.select('scaled_features')
    .rdd.map(lambda x: x.scaled_features.toArray())
    .collect()
)
test_labels = np.array(
    test_df.select('Close')
    .rdd.map(lambda x: x.Close).collect()
)
return train_features, train_labels, \
test_features, test_labels
```

```python
[In]: def create_and_train_model(
        self,
        train_features,
        train_labels,
        epochs=100,
        batch_size=32
    ):
        """
        创建并训练神经网络模型。

        参数：
        - train_features (ndarray): 训练特征。
        - train_labels (ndarray): 训练标签。
        - epochs (int): 训练的 epoch 数量。
        - batch_size (int): 训练的批次大小。

        返回：
        - None
        """

        self.input_shape = (train_features.shape[1],)
        self.model = Sequential([
            Dense(64, activation='relu',
                  input_shape=self.input_shape),
            Dense(32, activation='relu'),
            Dense(16, activation='relu'),
            Dense(1)
        ])
        self.model.compile(optimizer='adam', loss='mse')
        self.model.fit(
            train_features,
            train_labels,
            epochs=epochs,
                batch_size=batch_size
            )
```

```python
[In]: def evaluate_model(self, test_features, test_labels):
            """
            评估训练好的模型。

            参数：
                - test_features (ndarray): 测试特征。
                - test_labels (ndarray): 测试标签。

            返回：
                - float: 测试损失值。
            """
            test_loss = self.model.evaluate(
                test_features,
                test_labels
            )
            return test_loss
```

```python
[In]: def predict_and_evaluate(self, test_features,
                                test_labels):
            """
            预测并评估神经网络模型。

            参数：
                - test_features (ndarray): 测试特征。
                - test_labels (ndarray): 测试标签。

            返回：
                - float: R2 分数。
            """
test_predictions = self.model.predict(
      test_features
)
r2_score_value = r2_score(
    test_labels,
    test_predictions
)
return r2_score_value
```

```python
In: def plot_actual_vs_predicted(
    tsla_regressor,
    test_features,
    test_labels
):
    """
    绘制实际值与预测值的对比图。

    参数：
      - tsla_regressor (TLSARegressor):
          TLSARegressor 类的实例。
      - test_features (ndarray): 测试特征。
      - test_labels (ndarray): 测试标签。

    返回：
      - None
    """

    test_predictions = tsla_regressor.model.predict(
        test_features
    )

    print("Actual    Predicted")
    for actual, predicted in zip(
test_labels, test_predictions
): 
    print(f"{actual:.2f}  {predicted[0]:.2f}")
plt.figure(figsize=(10, 6))
plt.scatter(test_labels, test_predictions,
            color='blue')
plt.plot(
    [test_labels.min(), test_labels.max()],
    [test_labels.min(), test_labels.max()],
    'k--', lw=3
)
plt.xlabel('Actual')
plt.ylabel('Predicted')
plt.title('Actual vs. Predicted Values')
plt.show()
```

```python
[In]: def main(file_path):
        """
        主函数，用于协调整个工作流。
        
        参数：
            - file_path (str): CSV 文件的路径。
            
        返回：
            - None
        """
        try:
            tsla_regressor = TLSARegressor()
            train_df, test_df = tsla_regressor.
                preprocess_data(
                file_path
                )
	train_features, train_labels, test_features, \
	test_labels = tsla_regressor.convert_to_numpy(
		train_df,
		test_df
	)
	tsla_regressor.create_and_train_model(
		train_features,
		train_labels
	)
	test_loss = tsla_regressor.evaluate_model(
		test_features,
		test_labels
	)
	r2_score_value = tsla_regressor.predict_and_evaluate(
		test_features,
		test_labels
	)

	logging.info("Test Loss: {}".format(test_loss))
	logging.info("R2 Score: {}".format(r2_score_value))

	plot_actual_vs_predicted(
		tsla_regressor,
		test_features,
		test_labels
	)

except Exception as e:
	logging.error(f"An error occurred: {e}")
```

```python
[In]: if __name__ == "__main__":
    logging.basicConfig(level=logging.INFO)
    file_path = "/home/ubuntu/airflow/dags/TSLA_stock.csv"
    main(file_path)
```

# 摘要

在本章中，我们继续探索用于回归任务的深度学习模型。我们构建、训练并评估了一个 TensorFlow 深度学习模型，利用它来预测特斯拉的每日股价。虽然该深度学习回归模型并非旨在用于商业用途，但它展示了显著的性能，实现了超过 99% 的 R 平方值。这一性能与上一章使用 PyTorch 进行预测所获得的结果相当。

在下一章中，我们将把重点转向分类任务。我们将深入研究如何利用 PyTorch 对分类变量进行分类，这标志着我们在深度学习探索中的一个新阶段。

## 第 6 章

# 使用 PyTorch 进行深度学习的分类

在第 *4* 章和第 *5* 章中，我们探索了用于回归任务的深度学习。在本章和下一章中，我们将把重点转向分类，这是深度学习的另一个基本任务。回归和分类是两种不同类型的机器学习任务：回归旨在根据输入特征预测连续的数值，例如前面章节中演示的预测特斯拉股价。相比之下，分类则涉及将输入数据分配到预定义类别或类中。本章的目标是根据诸如怀孕次数、血糖水平、血压、身体质量指数（BMI）、年龄以及糖尿病家族史（也称为糖尿病遗传函数）等属性，预测一名女性被诊断为糖尿病的概率。

我们利用 Spark 进行数据预处理，以展示其在处理大型数据集时的分布式计算能力。虽然我们的数据集相对较小，但这些概念和代码适用于更大的数据集，这使得本练习在生产环境中具有很高的价值。小型数据集允许我们深入探讨诸如数据增强、迁移学习、重采样、模型复杂度、数据质量和数据表示等重要主题——这些都是深度学习的关键方面。

在开发本项目代码时，我们遵循了关键的建模步骤：数据预处理、模型定义、模型训练和模型评估。我们还 incorporated 了额外的功能，例如将数据从 S3 桶复制到 EC2 上的本地目录以进行处理，并在建模过程中处理错误和日志消息，以便于调试和监控。此外，我们使用 K 折交叉验证来评估模型，以确保我们的结论不依赖于单一的测试数据集。

本章首先检查糖尿病数据集，随后构建、训练和评估 PyTorch 分类模型。然后我们介绍 K 折交叉验证，整合本章中讨论的各个代码片段，最后以对关键要点的总结作为结束。

## 数据集

本项目使用的数据集是著名的 Pima 印第安人糖尿病数据集。Pima 指的是 Pima 人，他们是一群原产于美国西南部的原住民部落，主要居住在现在的亚利桑那州。

该数据集包含 768 条记录。每条记录代表一名 Pima 印第安女性，并包含各种与健康相关的属性，以及一个目标变量（结果），指示该女性是否患有糖尿病。该数据集适用于旨在根据明确定义的特征（如怀孕次数、血糖水平、血压、身体质量指数（BMI）、年龄以及糖尿病家族史（糖尿病遗传函数））预测糖尿病结果的分类任务。

`



该数据集最初由美国国家糖尿病、消化和肾脏疾病研究所创建。在本项目中，我们从专为数据科学家设计的平台 Kaggle 获取了该数据集。以下是贡献者姓名、大致上传日期、数据集名称、站点名称，以及我们下载 CSV 文件副本并将其存储在 AWS S3 桶的 URL：

| 字段 | 值 |
| :--- | :--- |
| 标题 | Pima Indians Diabetes Database |
| 来源 | Kaggle |
| URL | www.kaggle.com/uciml/pima-indians-diabetes-database |
| 贡献者 | UCI Machine Learning |
| 日期 | 2016 |

我们的书籍 *Distributed Machine Learning with PySpark: Migrating Effortlessly from Pandas and Scikit-Learn*（Apress，2023 年 11 月）中曾对皮马印第安人糖尿病数据集进行过探索，其中使用逻辑回归来解决这一分类问题。虽然逻辑回归是二元分类的稳健方法，但深度学习提供了捕捉简单模型可能忽视的数据复杂模式的新机遇。

本节中的 PySpark 代码对该数据集进行了多种类型的数据探索，包括以下内容：

- **处理缺失值**：代码统计数据集中每列的缺失值数量并显示这些计数。这有助于了解缺失数据的程度，并潜在地决定处理这些数据的策略。
- **统计零值数量**：它统计数据集中每列的零值数量。这种探索可以揭示潜在问题，例如缺失或错误的数据，特别是在零值可能无效的特征中（例如，血压、葡萄糖水平）。
- **数据摘要**：代码提供了数据集的摘要。它为数值列计算统计信息，如平均值、标准差、最小值、最大值和四分位数。此摘要有助于理解不同特征的分布和数值范围。
- **统计结果值数量**：它统计数据集中每种结果值出现的次数。这种探索有助于理解数据集中糖尿病病例的分布。
- **特征分布**：代码绘制了相关特征分布的直方图。可视化特征分布可以提供对数据潜在模式、潜在离群值以及数据是否偏斜的洞察。
- **计算特征与目标的关联性**：它计算每个特征与目标变量（结果）之间的相关性。这种探索有助于了解哪些特征可能与目标变量具有更强的相关性，这对于分类等预测建模任务至关重要。

让我们逐步查看代码，从导入语句开始。在解释完代码后，我们将转向输出结果。

### 步骤 1：导入

```python
[In]: from pyspark.sql import SparkSession
[In]: from pyspark.sql.functions import col, sum as pyspark_sum
[In]: import boto3
```

让我们分解导入语句及其在即将出现的代码中的用途：

- `from pyspark.sql import SparkSession`：此行从 pyspark.sql 模块导入 SparkSession 类。SparkSession 作为访问 Spark 的入口点，为分布式数据处理的各种功能提供支持。在即将出现的代码中，它被用于创建一个名为 `spark` 的 Spark 会话对象，从而启用与 Spark DataFrame API 的交互以进行数据加载和操作。
- `from pyspark.sql.functions import col, sum as pyspark_sum`：此行从 pyspark.sql.functions 模块导入特定函数。`col` 是一个用于引用 DataFrame 中列的函数，而 `sum` 是一个用于计算列中值总和的聚合函数。这些函数在 `PimaDatasetExplorer` 类的各种方法中用于数据预处理、处理缺失值以及计算特征与目标变量之间的相关性。
- `import boto3`：此行导入 `boto3` 模块，它是 Python 的官方 AWS SDK。Boto3 提供了一个易于使用的界面，以便以编程方式与各种 AWS 服务（如 S3 和 EC2）进行交互。在我们的代码中，`boto3` 在 `copy_file_from_s3()` 函数中用于与 AWS S3 服务交互，以便从 S3 桶下载 `diabetes.csv` 文件到 EC2 实例上的本地路径。

### 步骤 2：类定义

在这一步中，我们定义了一个名为 `PimaDatasetExplorer` 的类，该旨在用于使用 PySpark 探索和皮马印第安人糖尿病数据集：

```python
[In]: class PimaDatasetExplorer:
    """
    用于使用 PySpark 探索和分析皮马印第安人糖尿病数据集的类。
    """
    def __init__(self, file_path):
        """
        初始化 PimaDatasetExplorer 对象。

        参数：
            file_path (str): 数据集文件的路径。
        """
        self.file_path = file_path
        self.data = None
```

之后，我们在 `PimaDatasetExplorer` 类内定义了一系列方法，从 `load_data` 方法开始。

### 步骤 3：load_data 方法定义

`load_data` 方法定义在类内部，负责将指定文件路径中的数据加载到 PySpark DataFrame 中：

```python
[In]: def load_data(self):
        """
        从指定文件路径将数据集加载到 PySpark DataFrame 中。
        """
        try:
            self.data = spark.read.csv(
                self.file_path,
                header=True,
                inferSchema=True
            )
            self.data.cache()
        except Exception as e:
            print(
                "在加载数据时发生错误：", str(e)
            )
        self.data = None
```

该方法以一个描述其目的（即加载数据集）的文档字符串开始。在一个 `try` 块中，该方法将从 `self.file_path` 指定路径读取 CSV 文件到 PySpark DataFrame（`self.data`）。`header=True` 参数表示 CSV 文件的第一行包含列名，而 `inferSchema=True` 指示 Spark 在加载过程中自动推断每列的数据类型。

如果加载成功，使用 `cache()` 方法缓存 DataFrame（`self.data`）。缓存将 DataFrame 内容存储在内存或磁盘上，减少了在后续操作中重新计算 DataFrame 转换或操作的需要，这可以提高性能（在我们的相对较小的数据集中可能不明显，但对于大型数据集这是一个良好的实践）。

如果在加载过程中发生异常，该方法使用 `except` 块捕获该异常。它打印一条错误消息，指示加载数据时发生错误，并附带从异常中获取的具体错误消息（`str(e)`）。

最后，如果发生错误，将对象的数据属性设置为 `None`，以指示数据集未成功加载。这确保了后续操作可以在继续进一步分析或处理之前检查数据集是否成功加载。

### 步骤 4：preprocess_data 方法定义

在这一步中，我们在类中定义了一个名为 `preprocess_data` 的方法，正如文档字符串所示，它执行数据预处理步骤：

```python
[In]: def preprocess_data(self):
        """
        对数据集执行预处理步骤。
        """
        self.load_data()
```

- 该方法以 `self` 作为第一个参数，指向类的实例。
- 文档字符串 "Performs preprocessing steps on the dataset" 提供了对 `preprocess_data` 方法所做工作的简要描述。
- `self.load_data()`：此行调用 `load_data` 方法，该方法将数据集加载到内存中作为 PySpark DataFrame。

### 步骤 5：handle_missing_values 方法定义

`handle_missing_values` 方法定义在 `PimaDatasetExplorer` 类中。它旨在统计数据集中每列的缺失值数量并显示这些计数：

```python
[In]: def handle_missing_values(self):
        """
        统计数据集中每列的缺失值数量并显示这些计数。
        """
        if self.data is not None:
            missing_counts = self.data.select(
                [
                    pyspark_sum(
                        col(c).isNull().cast("int")
                    ).alias(c)
                    for c in self.data.columns
                ]
            )
            print("缺失值计数：")
            missing_counts.show()
        else:
            print("数据未加载。")
```

该方法以一个文档字符串开始，明确了该方法的目的。在此情况下，目的是统计数据集中每列的缺失值数量并显示这些计数。然后，它通过检查 `self.data` 是否为 `None` 来验证数据集是否已加载。如果数据集已加载，它将继续统计缺失值。

为了统计缺失值，该方法构建了一个名为 `missing_counts` 的 DataFrame。它使用列表推导式遍历数据集中的每一列（`c`），利用 PySpark 函数来确定值



为 null。具体而言，它使用 `isNaN()` 来识别空值，使用 `cast("int")` 将布尔结果转换为整数（0 或 1），并使用 `pyspark.sum` 计算每列缺失值的总和。每列的缺失值计数都以其原始列名作为别名。

在计数过程之后，该方法打印一个标题，指示将显示缺失值计数，然后使用 `show()` 方法显示缺失值计数 DataFrame。每一行对应数据集中的一列，每行中的值表示该列中缺失值的数量。

如果数据未加载（即 `self.data` 为 `None`），该方法会打印一条消息，声明数据未加载，告知用户在进行缺失值分析之前需要加载数据集。这确保了关于数据集状态的清晰度，并防止在未加载的数据上进行分析。

## 步骤 6：count_zeros 方法定义

在此阶段，我们在 `PimaDatasetExplorer` 类中定义 `count_zeros` 方法，其目的是统计数据集中每列零值出现的次数，然后展示这些计数（我们将在讨论输出时解释其目的）：

```python
[In]: def count_zeros(self):
        """
        Counts the number of zero values for each
        column in the
        dataset and displays the counts.
        """
        if self.data is not None:
            zero_counts = self.data.select([
                pyspark_sum((col(c) == 0).cast("int")).
                alias(c)
                for c in self.data.columns
            ])
        print("Zero Counts:")
        zero_counts.show()
    else:
        print("Data not loaded.")
```

在文档字符串之后，该方法开始检查数据集是否已加载。此检查通过验证 `self.data` 是否为非 `None` 来执行。如果数据集已加载，该方法将继续执行零值计数。对于计数零值，该方法构建了一个名为 `zero_counts` 的 DataFrame。它利用列表推导式遍历数据集中的每一列（`c`）。在此推导式中，使用 PySpark 函数来评估值是否等于零。具体而言，`(col(c) == 0)` 评估列中的值是否等于零，`cast("int")` 将布尔结果转换为整数（0 或 1），`pyspark_sum` 计算每列零值的总和。每列的零值计数都以其原始列名作为别名。

在执行完计数操作后，该方法打印一个标题，宣布将显示零值计数。然后使用 `show()` 方法显示零值计数 DataFrame。显示的 DataFrame 中的每一行对应数据集中的一列，每行中的值指示该列中零值的数量。

如果数据集未加载（即 `self.data` 为 `None`），该方法会打印一条消息，表明数据未加载。此消息作为提醒，在尝试进行零值分析之前先加载数据集。

## 步骤 7：data_summary 方法定义

`PimaDatasetExplorer` 类中的 `data_summary` 方法提供了糖尿病数据集中相关特征的摘要：

```python
[In]: def data_summary(self):
    """
    Displays a summary of the dataset, excluding certain
    columns, and filtering out rows with zero values in
    specific columns.

    Note: The 'SkinThickness' and 'Insulin' columns are
    excluded from the summary because they contain a
    large number of zero values, which are considered
    invalid because these measurements should not be zero
    in a living person and could
    skew the results.
    """
    if self.data is not None:
        print(
            "Data Summary ("
            "excluding 'Outcome', 'SkinThickness', 'Insulin')"
        )
        columns_to_exclude = [
            'Outcome',
            'SkinThickness',
            'Insulin'
        ]
        summary_cols = [
            c for c in self.data.columns
            if c not in columns_to_exclude
        ]
        filtered_data = self.data.filter(
            (col("Glucose") != 0)
            & (col("BloodPressure") != 0)
            & (col("BMI") != 0)
        )
        filtered_data.select(summary_cols).\
            describe().show()
    else:
        print("Data not loaded.")
```

让我们逐步分解该方法：

- 它以描述其目的的文档字符串开始。
- 然后它验证数据集是否已加载，确保 `self.data` 不为 `None`。如果数据集已加载，该方法将继续生成数据摘要。
- 为了生成摘要，该方法首先打印一个标题，指示将显示数据集的摘要。然后定义一个名为 `columns_to_exclude` 的列表，包含要从摘要中排除的列名（'Outcome', 'SkinThickness', 'Insulin'）。
- 接下来，该方法使用列表推导式构建一个名为 `summary_cols` 的列表。此列表包含数据集中的所有列（`self.data.columns`），但不包括 `columns_to_exclude` 中指定的列。
- 随后，该方法过滤数据集（`self.data`），以排除特定列（'Glucose', 'BloodPressure', 'BMI'）值为零的行。这是通过使用 PySpark 中的 `filter()` 方法实现的，条件确保指定的列中没有值为零的情况。
- 在过滤数据集之后，该方法仅选择 `summary_cols` 中指定的列，并使用 `describe()` 方法生成描述性统计。这些统计提供了对数据分布的中心趋势、离散程度和形状的见解。
- 最后，该方法通过调用生成的摘要 DataFrame 上的 `show()` 方法来显示摘要。
- 如果数据集未加载（即 `self.data` 为 `None`），该方法会打印一条消息，表明数据未加载。

## 步骤 8：count_outcome 方法定义

在此，我们定义 `count_outcome` 方法，它是 `PimaDatasetExplorer` 类的一部分。该方法用于统计糖尿病数据集中每种结果值出现的次数：

```python
[In]: def count_outcome(self):
        """
        Counts the occurrences of each outcome value in the dataset.
        """
        if self.data is not None:
            print("Outcome Counts:")
            outcome_counts = self.data.filter(
                (col("Glucose") != 0)
                & (col("BloodPressure") != 0)
                & (col("BMI") != 0)
            ).groupBy("Outcome").count()
            outcome_counts.show()
        else:
            print("Data not loaded.")
```

让我们将其分解：

- 该方法以文档字符串开始，简要解释其目的。
- 然后它检查数据集是否已加载，确保 `self.data` 不为 `None`。如果数据集已加载，该方法将继续统计结果出现的次数。
- 为了统计每种结果值出现的次数，该方法构建了一个名为 `outcome_counts` 的 DataFrame。它过滤数据集以排除特定列（`'Glucose', 'BloodPressure', 'BMI'`）值为零的行（无效数据）。这是通过使用 PySpark 中的 `filter()` 方法实现的，确保指定的列中没有值为零的情况。
- 在过滤数据集之后，该方法按 `Outcome` 列（目标变量）对数据进行分组，并使用 `groupBy()` 和 `count()` 函数计算每种结果值的出现次数。
- 计算计数完成后，该方法打印一个标题，指示将显示结果计数。然后使用 `show()` 方法显示结果计数 DataFrame。显示的 DataFrame 中的每一行代表一个结果值，相应的计数指示该结果值在数据集中出现的次数。
- 如果数据集未加载（即 `self.data` 为 `None`），该方法会打印一条消息，表明数据未加载。

## 步骤 9：explore_feature_distributions 方法定义

在此步骤中，我们定义 `explore_feature_distributions` 方法，该方法旨在通过直方图分析和可视化数据集中每个特征分布：

```python
[In]: def explore_feature_distributions(self):
      """
      Plots histograms for the distribution of each
      feature in the
      dataset.
      """
      if self.data is not None:
          print("Feature Distributions:")
          for column in self.data.columns:
              if column not in ['SkinThickness',
                                 'Insulin']:
                  print(f"Feature: {column}")
                  if column in [
                      "Glucose",
                      "BloodPressure",
                      "BMI"
                  ]:
                      filtered_data = self.data.filter(
                          (col(column) != 0)
                          & (col("Glucose") != 0)
                          & (col("BloodPressure") != 0)
                          & (col("BMI") != 0)
                      )
```




## 代码片段

```python
else:
    filtered_data = self.data

plot_data = filtered_data.select(column). \
    toPandas()
plot_data.plot(kind='hist', title=column)
else:
    print("Data not loaded.")
```

让我们逐步解析：

- 在该方法中，第一步是验证 `self.data` 是否为 `None`，以检查数据集是否已加载。这确保只有当数据集可用于分析时，方法才会继续执行。
- 确认数据集已加载后，该方法开始探索特征分布。它首先打印一个标题，表示将检查特征分布。
- 接下来，该方法遍历数据集中的每一列。对于每一列，它会检查该列是否不在排除列表中，该列表包括类似 `'SkinThickness'` 和 `'Insulin'` 的列。此排除机制确保这些特定列不会包含在特征分布分析中。
- 对于正在分析的每个特征，该方法会打印一个指示特征名称的标签。然后，它会检查该特征是否属于指定列：`'Glucose'`、`'BloodPressure'` 和 `'BMI'`。如果是，则过滤数据集以排除这些列中存在零值的行。
- 如果该特征不属于指定列，则该方法使用未过滤的数据集进行分析。
- 最后，该方法首先使用 `toPandas()` 方法将选中的数据转换为 Pandas DataFrame，然后使用 `plot(kind='hist')` 方法为所选特征绘制直方图。这会生成一个显示该特征值分布的直方图。
- 如果数据集未加载（即 `self.data` 为 `None`），该方法会打印一条消息，提示数据未加载。

### 第 10 步：calculate_feature_target_correlation 方法定义

在这一步中，我们将创建 `calculate_feature_target_correlation` 方法，该方法负责计算每个特征与目标变量（`Outcome`）之间的相关性：

```python
[In]: def calculate_feature_target_correlation(self):
       """
       计算每个特征与目标变量 (Outcome) 之间的相关性。

       注意：'SkinThickness' 和 'Insulin' 列被排除在相关性计算之外，因为它们包含大量零值，这些值被认为是无效的，因为在活体中这些测量值不应为零，且可能会扭曲结果。
       """
```

```python
if self.data is not None:
    print(
        "Feature-Target Correlation "
        "(excluding 'SkinThickness', 'Insulin'):"
    )
    for column in self.data.columns:
        if column not in [
            'Outcome',
            'SkinThickness',
            'Insulin'
        ]:
            correlation = self.data.filter(
                (col(column) != 0)
                & (col("Glucose") != 0)
                & (col("BloodPressure") != 0)
                & (col("BMI") != 0)
            ).stat.corr(column, 'Outcome')
            print(f"{column}: {correlation}")
else:
    print("Data not loaded.")
```

该代码的解释如下：

- 在文档字符串之后，执行一项检查以确保数据集已加载（`self.data is not None`）。这确保只有当数据集可用时，相关性计算才会继续。
- 数据集加载完成后，该方法继续计算特征与目标变量之间的相关性。它首先打印一个标题，表示将计算特征与目标变量的相关性。
- 接下来，该方法遍历数据集中的每一列。对于每一列，它检查该列是否不在排除列表中（`'Outcome'`、`'SkinThickness'`、`'Insulin'`）。此排除机制确保这些特定列不会包含在相关性分析中。
- 对于正在分析的每个特征，该方法计算该特征与目标变量（`'Outcome'`）之间的相关性。此计算通过过滤数据集来执行，以排除该特征或任何指定列（`'Glucose'`、`'BloodPressure'`、`'BMI'`）中存在零值的行。然后调用 `stat.corr()` 方法来计算特征与目标变量之间的相关性。
- 计算出的相关值随后与特征名称一起打印出来，从而提供关于每个特征与目标变量之间关系的强度和方向的见解。
- 如果数据集未加载（即 `self.data` 为 `None`），该方法会打印一条消息，提示数据未加载。

### 第 11 步：copy_file_from_s3 函数定义

在 `PimaDatasetExplorer` 类之外，我们现在定义 `copy_file_from_s3` 函数。该函数负责将 `diabetes.csv` 文件从 AWS S3 桶复制到 EC2 实例上的本地路径：

```python
[In] def copy_file_from_s3(bucket_name, file_key, local_path):
    """
    将 CSV 文件从 AWS S3 桶复制到本地路径。

    参数:
        bucket_name (str): S3 桶的名称。
        file_key (str): S3 桶中文件的键。
        local_path (str):
            文件将复制到的本地路径。
    """
    try:
        s3 = boto3.client('s3')
        s3.download_file(bucket_name, file_key,
            local_path)
        print(f"File {file_key} downloaded to {local_path}")
    except Exception as e:
        print(f"An error occurred while downloading file {file_key}: {str(e)}")
```

在 `copy_file_from_s3` 函数内部

- 文档字符串提供了该方法的用途及其参数的文档说明。
- 使用 try-except 块来处理文件复制过程中可能发生的潜在异常。
- 在 try 块内部，该方法使用 `boto3` 库中的 `boto3.client()` 函数启动与 AWS S3 服务的连接。这建立了一个客户端以与 S3 服务进行交互。
- 然后，该函数使用 S3 客户端的 `download_file` 方法，将文件从指定的 S3 桶（`bucket_name`）中，按照给定的键（`file_key`）复制到指定的本地路径（`local_path`）。
- 如果文件复制过程成功，系统将打印一条消息，确认文件已下载到指定的本地路径。
- 如果在文件复制过程中发生异常，`except` 块将捕获该异常并打印一条错误消息，指示在下载文件时发生了错误，并附带异常提供的具体错误消息（`str(e)`）。这确保了用户在文件复制过程中遇到任何问题时会收到通知，从而便于故障排除和错误解决。

### 第 12 步：主程序

在最后一步中，我们定义 `if __name__ == "__main__":` 块。这是 Python 中一种常见的条件语句，它允许代码仅在脚本直接运行时执行，而在作为模块导入时不执行。这确保了以下代码仅在脚本作为主程序运行时执行：

```python
[In]: if __name__ == "__main__":
      spark = (SparkSession.builder
              .appName("PimaDatasetExplorer")
              .getOrCreate())
      local_file_path = "/home/ubuntu/airflow/dags/diabetes.csv"
      s3_bucket_name = "instance1bucket"
      s3_file_key = "diabetes.csv"
      copy_file_from_s3(
        s3_bucket_name,
        s3_file_key,
        local_file_path
      )
      explorer = PimaDatasetExplorer(local_file_path)
      explorer.preprocess_data()
      explorer.handle_missing_values()
      explorer.count_zeros()
      explorer.data_summary()
      explorer.count_outcome()
      explorer.explore_feature_distributions()
      explorer.calculate_feature_target_correlation()
```

在此块内部

- `SparkSession` 类创建一个具有指定应用程序名称的 Spark 会话（如果存在则获取现有的）。
- `local_file_path` 被定义为数据集文件将存储的本地路径。
- `s3_bucket_name` 被定义为将复制数据集文件的 S3 桶的名称。
- `s3_file_key` 被定义为数据文件在 S3 桶中的键。
- 调用 `copy_file_from_s3` 函数，将数据集文件从指定的 S3 桶复制到 EC2 实例上的本地文件路径。
- 使用本地文件路径作为参数，创建 `PimaDatasetExplorer` 类的实例。




## 第 6 章 使用 PyTorch 进行深度学习的分类任务

- 调用 `PimaDatasetExplorer` 实例的 `preprocess_data` 方法来加载和预处理数据集。
- 调用 `PimaDatasetExplorer` 实例的多个方法来探索和分析数据集：
  - `handle_missing_values`：统计每列的缺失值数量
  - `count_zeros`：统计每列的零值数量
  - `data_summary`：显示数据集的摘要
  - `count_outcome`：统计每个结果值出现的次数
  - `explore_feature_distributions`：绘制特征分布直方图
  - `calculate_feature_target_correlation`：计算特征与目标变量之间的相关性

这段代码编排了加载、预处理和分析数据集的整个流程，展示了 `PimaDatasetExplorer` 类的功能。

为了运行代码，我们将其保存为 “diabetes_data_exploration.py” 并在 JupyterLab 终端中执行（我们也可以在 EC2 实例上直接运行）。由于我们创建了一个名为 “myenv” 的环境，因此按以下方式激活它：

```
[In]: source /home/ubuntu/myenv/bin/activate
```

激活环境后，我们使用 Python 3 通过以下命令执行代码：

```
[In]: python3 diabetes_data_exploration.py
```

现在可以检查代码的输出结果了。

第一个输出是一条确认消息，表明文件 “diabetes.csv” 已成功下载到指定本地路径 “/home/ubuntu/airflow/dags/diabetes.csv”。这证实了 “copy_file_from_s3” 函数执行时没有发生任何错误：

```
[Out]: File diabetes.csv downloaded to /home/ubuntu/airflow/dags/diabetes.csv
```

第二个输出是由 `handle_missing_values()` 方法生成的缺失值统计：

| Pregnancies | Glucose | BloodPressure | SkinThickness | Insulin | BMI | DiabetesPedigreeFunction | Age | Outcome |
|---|---|---|---|---|---|---|---|---|
| 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 |

输出显示所有计数均为零，表明各列中均不存在缺失值。

第三个输出是由 `count_zeros()` 方法生成的，代表数据集中每列零值的统计数量：

| Pregnancies | Glucose | BloodPressure | SkinThickness | Insulin | BMI | DiabetesPedigreeFunction | Age | Outcome |
|---|---|---|---|---|---|---|---|---|
| 111 | 5 | 35 | 227 | 374 | 11 | 0 | 0 | 500 |

输出表明 DiabetesPedigreeFunction 和 Age 中没有 0 值的案例，但其他变量有许多 0 值的案例。例如，111 个案例中 Pregnancies 变量的值为 0，这是合理的，因为样本中有些女性没有孩子。此外，500 个案例中 Outcome 变量的值为 0，表明这些女性没有糖尿病。然而，Glucose、BloodPressure、SkinThickness、Insulin 或 BMI 为 0 值在逻辑上是不合理的。

处理无效读数有三种常见方法：排除含有 0 值的列或特征，排除含有 0 值的行，或者用均值或平均值填补 0 值。在本章中，我们选择了选项 1 和 2：

- 选项 1：排除 SkinThickness 和 Insulin，因为 0 值的案例数量过大（分别为 227 和 374）。如果排除行而不是列，会使样本量变得太小。
- 选项 2：排除 Glucose、BloodPressure 和 BMI 为 0 值的行。无效案例的数量没有那么大，因此排除行不会显著影响样本量。

下一个输出是由 `data_summary()` 方法生成的，提供了在处理完无效读数（即排除 'Outcome'、'SkinThickness' 和 'Insulin'）后，数据集中相关特征的统计度量摘要：

| | 摘要 | Pregnancies | Glucose | Blood Pressure | BMI | Diabetes PedigreeFunction | Age |
| --- | --- | --- | --- | --- | --- | --- | --- |
| 数量 | 724 | 724 | 724 | 724 | 724 | 724 | 724 |
| 均值 | 3.87 | 121.88 | 72.40 | 32.47 | 0.47 | 33.35 | |
| 标准差 | 3.36 | 30.75 | 12.38 | 6.89 | 0.33 | 11.77 | |
| 最小值 | 0 | 44 | 24 | 18.2 | 0.078 | 21 | |
| 最大值 | 17 | 199 | 122 | 67.1 | 2.42 | 81 | |

以下是每个特征摘要统计量的详细分解：

- Pregnancies：数量 724；均值 3.87；标准差 3.36；最小值 0；最大值 17
- Glucose：数量 724；均值 121.88；标准差 30.75；最小值 44；最大值 199
- BloodPressure：数量 724；均值 72.40；标准差 12.38；最小值 24；最大值 122
- BMI：数量 724；均值 32.47；标准差 6.89；最小值 18.2；最大值 67.1
- DiabetesPedigreeFunction：数量 724；均值 0.47；标准差 0.33；最小值 0.078；最大值 2.42
- Age：数量 724；均值 33.35；标准差 11.77；最小值 21；最大值 81

这些摘要统计量提供了每个特征的中心趋势、离散程度和取值范围的见解，有助于理解数据集的特征。事实上，仔细检查后，数据中有一些数值看起来可疑。例如：

- Glucose：最小值为 44，这对于血糖测量值来说似乎异常低。虽然血糖水平可能落在该范围内，但低于 70 mg/dL 的数值通常被认为是低血糖，这可能表明数据存在问题。
- BloodPressure：最小值为 24，极低且不太可能是有效的血压读数。通常，低于 90/60 mmHg 的血压值被认为是低血压，这可能表明数据收集过程中存在错误。
- BMI：最小值为 18.2，处于健康 BMI 范围内但偏向低端。值得调查这些低 BMI 值是否有效，或者它们是否可能是异常值或数据错误。
- DiabetesPedigreeFunction：最小值为 0.078，作为与糖尿病相关的遗传风险因素，这似乎异常低。虽然该值可能是低的，但为了确保准确性，可能需要进一步调查。
- Age：最小值为 21，在合理范围内。然而，根据数据集的背景，值得验证这个最低年龄是否适用于被研究的人群。
- Pregnancies：最后，数据中妊娠次数的最大值为 17。虽然从生物学上讲女性可能怀孕 17 次，但这极为罕见，在大多数人群中将被视为异常值。

这些可疑值可能是数据中的异常值或错误，通常需要进行进一步调查和数据验证，以确保数据集的完整性。就我们的演示目的而言，我们将继续使用这个数据集，但不应期望其表现优异。然而，这展示了数据探索（特别是描述性统计）如何识别潜在问题。它还突出了机器学习中的数据质量概念。

下一个输出是由 `count_outcome()` 方法生成的，显示了结果为 1（表示糖尿病）和结果为 0（表示无糖尿病）的案例数量：

| Outcome | 计数 |
| --- | --- |
| 1 | 249 |
| 0 | 475 |

在这个数据集中，有 249 个案例的结果为 1（糖尿病），475 个案例的结果为 0（无糖尿病）。像这样一个不平衡的数据集，其中一个结果（此处为 0）的实例数量远多于另一个结果，可能会在机器学习任务中产生影响。

下一个输出是由 `calculate_feature_target_correlation()` 方法生成的每个具有有效读数的特征与目标变量（Outcome）之间的相关系数：

| 特征 | 相关系数值 |
| --- | --- |
| Pregnancies | 0.261 |
| Glucose | 0.488 |
| BloodPressure | 0.167 |
| BMI | 0.299 |
| DiabetesPedigreeFunction | 0.185 |
| Age | 0.246 |

相关系数衡量两个变量之间线性关系的强度和方向。正相关表示当一个变量增加时，另一个变量也倾向于增加，而负相关表示当一个变量增加时，另一个变量倾向于减少。

在深度学习分类任务中，理解特征与目标变量之间的相关性在以下几个方面可能有所帮助：

- 特征选择：具有较高相关系数值的特征更有可能对目标变量的预测产生更强的影响。在特征选择过程中，例如在神经网络架构设计中，选择与目标变量高度相关的特征可以产生更高效、预测性能更好的模型。根据上述相关系数，Glucose 对模型的影响最大，其次是 BMI、Pregnancies、Age、DiabetesPedigreeFunction 和 BloodPressure。
- 模型可解释性：了解哪些特征与目标变量具有更高的相关性，可以为输入特征与目标变量之间的底层关系提供见解。这些信息有助于解释训练后模型的预测结果，并理解哪些特征对分类最为重要。鉴于深度学习模型通常被认为是“黑箱”，这一点尤为重要。
- 模型优化：在训练过程中，理解特征与目标变量之间的相关性可以指导优化策略。例如，在使用技术优化深度学习模型时


与梯度下降类似，相关性较高的特征可能会获得更多权重更新，从而可能带来更快的收敛速度和更好的模型性能。

-   **特征工程**：特征工程在提升模型性能方面起着至关重要的作用。通过利用特征与目标变量之间相关性信息，数据科学家可以对特征变换、特征交互或新特征的创建做出明智的决策，以增强模型捕获数据中相关模式的能力。

由 `explore_feature_distributions()` 方法生成的最终输出，表示为糖尿病数据集中各个列生成的直方图（图 6-1 至 6-6）。

![](img/1c89d4486f90c87568fa6a42d46ae02a_366_0.png)

**图 6-1. 怀孕次数直方图**

![](img/1c89d4486f90c87568fa6a42d46ae02a_367_0.png)

**图 6-2. 血糖直方图**

![](img/1c89d4486f90c87568fa6a42d46ae02a_367_1.png)

**图 6-3. 血压直方图**

![](img/1c89d4486f90c87568fa6a42d46ae02a_368_0.png)

**图 6-4. 体质指数（BMI）直方图**

![](img/1c89d4486f90c87568fa6a42d46ae02a_368_1.png)

**图 6-5. 糖尿病家族史函数（Pedigree Function）直方图**

![](img/1c89d4486f90c87568fa6a42d46ae02a_369_0.png)

**图 6-6. 年龄直方图**

直方图显示，血糖和血压似乎呈近似正态分布，而其他特征则向右偏斜。右偏分布（也称为正偏斜）意味着大多数数据点集中在直方图的左侧，并有一条向右延伸的尾部。换句话说，该分布是不对称的，右侧有较长的尾部。

偏斜数据会以多种方式影响深度学习模型的性能和训练动态：

-   **模型偏差**：偏斜数据可能会引入训练模型的偏差，因为模型可能会更偏向于多数类（在分类任务中）或数据中占主导地位的模式。这可能导致泛化性能较差，尤其是在少数类或较少见的模式上。
-   **模型学习**：在偏斜数据上训练的深度学习模型可能会优先考虑学习在多数类中更普遍的特征和模式，从而可能忽略或低估少数类或不常见模式的代表性。因此，模型可能难以很好地泛化到新的、未见过的数据点，特别是来自代表性不足的类别的数据点。
-   **损失函数不平衡**：在分类任务中，不平衡的类别会导致训练期间损失函数的不平衡。这种不平衡可能导致模型优先考虑最小化多数类的损失，而牺牲少数类的损失，从而进一步加剧训练模型的偏差。

实际上，解决深度学习中的偏斜数据问题通常涉及采用专门的采样策略，例如过采样少数类或欠采样多数类。这些策略旨在平衡训练数据中的类别分布，并减轻偏斜对模型训练的影响。

虽然解决这些问题超出了本书的范围，但在评估我们基于此偏斜数据训练的深度学习模型的性能时，我们将使用考虑到类别不平衡的适当评估指标，即精确率、召回率和 F1 分数。这些指标提供了对模型在所有类别上性能的更全面评估，而不仅仅依赖于准确率。

## 使用 PyTorch 预测糖尿病

在本节中，我们将构建、训练和评估一个神经网络模型，并使用它来预测皮马印第安女性患糖尿病的可能性，使用我们刚刚探索过的数据集。我们使用六个特征：怀孕次数、血压、体质指数（BMI）、血糖水平、糖尿病家族史函数和年龄。这些特征是预测糖尿病存在与否的重要因素。

我们利用 Spark 的分布式计算能力进行数据预处理，并使用 PyTorch 开发深度学习模型。代码已组织为以下步骤：

1.  **数据预处理**：
    - 使用 Spark 从 AWS S3 上的 CSV 文件加载糖尿病数据集。
    - 过滤特定列（血糖、血压、BMI）中的无效记录。
    - 使用 `VectorAssembler` 将特征列组合成单个向量。
    - 使用 `StandardScaler` 对组合后的特征进行缩放。
    - 将预处理后的数据分割为训练集和测试集。
2.  **模型定义**：
    - 使用 PyTorch 定义用于糖尿病分类的神经网络模型架构。该模型由多个具有 ReLU 激活函数的全连接层组成。
3.  **模型训练**：
    - 使用定义的神经网络模型、损失函数、优化器和训练数据加载器初始化模型训练器。
    - 在训练数据集上训练神经网络模型，持续指定的轮数。
    - 根据优化过程更新模型参数以最小化损失。
4.  **模型评估**：
    - 使用测试集评估训练好的模型。
    - 计算各种性能指标，如准确率、精确率、召回率、F1 分数、ROC-AUC 分数和混淆矩阵，以评估模型在分类糖尿病方面的有效性。
5.  **附加功能**：
    - 将数据文件从 S3 存储桶复制到 EC2 本地目录进行处理，演示与 AWS 服务的集成。
    - 处理错误并记录日志消息，用于建模过程中的调试和监控。

这些步骤封装了利用 Spark 进行数据预处理和利用 PyTorch 进行深度学习模型开发的端到端过程，用于构建、训练和评估糖尿病分类的神经网络模型。

在进行任何任务之前，第一步是导入必要的库。

## 步骤 1：导入

```python
[In]: import boto3
[In]: import logging
[In]: import numpy as np
[In]: import torch
[In]: import torch.nn as nn
[In]: import torch.optim as optim
[In]: from torch.utils.data import DataLoader, TensorDataset
[In]: from sklearn.metrics import (
    accuracy_score,
    precision_score,
    recall_score,
    f1_score,
    confusion_matrix,
    roc_auc_score
)
[In]: from pyspark.sql import SparkSession
[In]: from pyspark.ml.feature import (
    VectorAssembler,
    StandardScaler
)
[In]: from pyspark.sql.functions import col
```

以下是每个导入语句及其目的的详细分解，以及它们将在即将出现的代码中如何使用：

-   **`import boto3`**：
    此语句导入了 `boto3` 库，它是亚马逊网络服务（AWS）的 Python SDK。它用于与 S3 交互以下载文件。在我们的代码中，此导入用于 `copy_file_from_s3` 函数中，与亚马逊 S3 交互并从指定的 S3 存储桶下载文件。

-   **`import logging`**：
    此语句导入了 Python 内置的 `logging` 模块，该模块提供了显示 Python 程序日志消息的框架。在代码中，`logging` 用于处理日志消息，包括错误、警告和信息消息。它用于调试和监控目的。

-   **`import numpy as np`**：
    此语句导入了 NumPy 库并将其别名为 `np`。NumPy 是 Python 中强大的数值计算库。在我们的代码中，使用 NumPy 数组进行各种数值计算，例如数据预处理和将数据转换为 NumPy 数组。

-   **`import torch`**：
    此语句导入了 PyTorch 库，它是由 Facebook AI 研究实验室开发的开源机器学习框架。在我们的代码中，PyTorch 用于处理张量和神经网络操作，包括模型定义、训练和评估。

-   **`import torch.nn as nn`**：
    此语句从 PyTorch 导入了神经网络模块 `nn`。在代码中，`nn` 模块用于定义用于糖尿病分类的神经网络模型架构。它提供了创建神经网络层和激活函数的构建模块。





- `import torch.optim as optim`：
    - 此语句从 PyTorch 中导入优化模块 `optim`。`optim` 模块将用于指定训练神经网络模型时的优化算法和参数。它包含了如 Adam 和 SGD 等各种优化算法的实现。

- `from torch.utils.data import DataLoader, TensorDataset`：
    - 这些导入用于在模型训练期间处理数据加载和批次处理。`DataLoader` 和 `TensorDataset` 将用于在模型训练期间高效地加载和批处理数据。

- `from sklearn.metrics import accuracy_score, precision_score, recall_score, f1_score, confusion_matrix, roc_auc_score`：
    - 这些语句从 Scikit-Learn (`sklearn`) 库中导入了特定的性能指标。在代码中，这些指标在 `ModelEvaluator` 类中用于计算准确率、精确率、召回率、F1 分数、混淆矩阵和 ROC-AUC 分数等性能指标，以评估训练好的模型。

- `from pyspark.sql import SparkSession`：
    - 此语句从 `pyspark.sql` 模块中导入 `SparkSession` 类。它将在代码的主执行部分用于创建 Spark 会话，以便使用 Spark DataFrame API 处理结构化数据。

- `from pyspark.ml.feature import VectorAssembler, StandardScaler`：
    - 这些语句从 `pyspark.ml.feature` 模块中导入了特定的特征工程工具。`VectorAssembler` 和 `StandardScaler` 将在 `DataPreprocessor` 类中用于执行特征工程任务，例如将多个特征列组装成单个向量以及缩放特征。

- `from pyspark.sql.functions import col`：
    - 此语句从 `pyspark.sql.functions` 模块中导入 `col` 函数。它将在 `DataPreprocessor` 类中用于通过名称引用 DataFrame 列，从而在 Spark SQL 查询中方便地进行列操作，特别是用于基于特定列值过滤记录。

完成这些导入后，我们进入建模过程的第 2 步，即数据预处理。

## 步骤 2：数据预处理

在此建模步骤中，我们定义了一个 `DataPreprocessor` 类及其 `preprocess` 方法。这段代码加载数据，执行无效行的过滤、特征组装、特征缩放，并将数据划分为训练集和测试集：

```python
class DataPreprocessor:
    """
    预处理糖尿病数据集。
    """

    def __init__(self, spark, data_file_path):
        """
        初始化 DataPreprocessor。
        
        Args:
            spark (pyspark.sql.SparkSession):
                Spark 会话。
            data_file_path (str):
                数据文件的路径。
        """
        self.spark = spark
        self.data_file_path = data_file_path

    def preprocess(self):
        """
        执行数据预处理。
        
        Returns:
            tuple:
                包含训练集和测试集 DataFrame 的元组。
        """
        try:
            diabetes_df = self.spark.read.csv(
                self.data_file_path,
                header=True,
                inferSchema=True
            )
            diabetes_df = diabetes_df.filter(
                (col("Glucose") != 0)
                & (col("BloodPressure") != 0)
                & (col("BMI") != 0)
            )
            
            feature_cols = [
                "Pregnancies",
                "Glucose",
                "BloodPressure",
                "BMI",
                "DiabetesPedigreeFunction",
                "Age",
            ]
            assembler = VectorAssembler(
                inputCols=feature_cols,
                outputCol="features"
            )
            diabetes_df = assembler.transform(diabetes_df)
            scaler = StandardScaler(
                inputCol="features",
                outputCol="scaled_features"
            )
            scaler_model = scaler.fit(diabetes_df)
            diabetes_df = scaler_model.transform(diabetes_df)
            train_df, test_df = diabetes_df.randomSplit(
                [0.8, 0.2],
                seed=42
            )
            return train_df, test_df
        except Exception as e:
            logging.error(
                f"Error occurred during data preprocessing: {str(e)}"
            )
            raise e
```

代码定义了一个名为 `DataPreprocessor` 的 Python 类，它封装了预处理糖尿病数据集的功能。在该类中，有一个构造函数方法 `__init__`，它使用两个参数初始化类实例：`spark`，表示 Spark 会话；以及 `data_file_path`，指示数据文件的路径。核心预处理功能在类的 `preprocess` 方法中实现。该方法首先使用 Spark 的 `read.csv` 方法将 CSV 数据文件读取为 Spark DataFrame（`diabetes_df`），并指定文件包含表头行且自动推断模式。然后，它过滤 DataFrame 以移除某些列（Glucose、BloodPressure 和 BMI）值为零的记录，因为这些是生物学上不可能存在的值，很可能表示数据缺失或错误。保留这些值可能会对模型的准确性和预测能力产生负面影响。接下来，定义了一个特征列列表，包括妊娠次数、血糖水平、血压、身体质量指数（BMI）、糖尿病家族遗传因素和年龄等特征。

随后，创建一个 `VectorAssembler` 对象，将这些特征列组装成一个名为 "features" 的单个向量列。这个组装后的特征列随后被添加到 DataFrame 中。在特征组装之后，实例化一个 `StandardScaler` 对象以缩放特征，确保它们具有相似的尺度，从而提升模型性能。这对于对输入数据尺度敏感的神经网络尤为重要。缩放器拟合到 DataFrame 以计算统计摘要，并使用拟合好的缩放器转换 DataFrame 以获得缩放后的特征。最后，使用 80-20 的分割比例将预处理后的数据划分为训练集和测试集，即 80% 的数据用于训练，20% 用于测试。在 `randomSplit` 方法中使用 `seed=42` 确保每次运行代码时数据都以相同的方式分割，从而增强结果的可复现性。训练集和测试集 DataFrame 作为元组从 `preprocess` 方法中返回。

如果在预处理过程中发生任何异常，代码会在 `try-except` 块中处理它们。如果捕获到异常，使用 Python 的 `logging.error` 方法记录错误消息，其中包含异常的详细信息。

## 步骤 3：模型定义

在此步骤中，我们使用 PyTorch 定义用于糖尿病分类的神经网络模型架构。该架构指定了模型的层数和激活函数：

```python
class DiabetesClassifierModel(nn.Module):
    """
    用于糖尿病分类的神经网络模型。
    """

    def __init__(self, input_size, output_size):
        """
        初始化 DiabetesClassifierModel。

        Args:
            input_size (int): 输入尺寸。
            output_size (int): 输出尺寸。
        """
        super(DiabetesClassifierModel, self).__init__()
        self.model = nn.Sequential(
            nn.Linear(input_size, 64),
            nn.ReLU(),
            nn.Linear(64, 32),
            nn.ReLU(),
            nn.Linear(32, 16),
            nn.ReLU(),
            nn.Linear(16, output_size),
        )

    def forward(self, x):
        """
        定义模型的前向传播。

        Args:
            x (torch.Tensor): 输入张量。

        Returns:
            torch.Tensor: 输出张量。
        """
        return self.model(x)
```

代码定义了一个名为 `DiabetesClassifierModel` 的 Python 类，它作为用于糖尿病分类的神经网络模型。在该类中，有两个主要方法：`__init__` 和 `forward`。

`__init__` 方法作为构造函数，负责初始化模型。它接受两个参数：`input_size`，表示输入特征的大小；以及 `output_size`，指示输出大小（即分类的类别数量）。

在 `__init__` 方法内部，该类继承自 `nn.Module`，这是 PyTorch 中所有神经网络模块的基类。神经网络架构使用 PyTorch 的 `nn.Sequential` 容器定义，该容器通过自动按定义顺序连接层来简化模型定义。该容器允许层进行清晰的线性排列，使模型更易于阅读和维护。

该架构由几个全连接（线性）层组成，输出大小从 `input_size` 递减到 `output_size`。在每个线性层之后，应用整流线性单元（ReLU）激活函数。ReLU 函数为模型引入非线性，这对于网络学习数据中的复杂模式至关重要。如果没有这种非线性，模型将仅仅是输入的线性组合，这可能会严重限制其预测能力。




## 步骤 4：模型训练

该模型使用了三个隐藏层，分别包含 64、32 和 16 个神经元。虽然这种架构提供了坚实的基础，但它可能不是最优的，并且根据数据集的大小和复杂度，可能会导致过拟合或欠拟合。由于缺少诸如 Dropout 或 L2 正则化等正则化技术，模型可能会过拟合训练数据，从而捕捉噪声而非通用模式。相反，如果架构过于简单，无法捕捉数据集的底层结构，模型可能会欠拟合。此外，当前的训练方法将数据集一次性划分为训练集和测试集，这可能会引入变异性并影响模型性能。这些潜在问题——包括对 Dropout、早停、L1/L2 正则化和交叉验证等技术的需求——将在第 9 章中得到解决。第 9 章还将展示如何利用 PyTorch 的学习率调度器来进一步增强模型性能和泛化能力。

`forward` 方法定义了模型的前向传播，规定了输入数据如何通过神经网络进行处理以产生输出预测。它接受一个参数 `x`，代表包含特征的输入张量。在 `forward` 方法中，输入张量 `x` 通过神经网络模型（`self.model`）进行处理。模型产生的输出张量随后作为前向传播的结果返回。

在这一步中，我们定义了 `ModelTrainer` 类及其 `train` 方法。代码使用神经网络模型、损失函数、优化器和训练数据加载器初始化模型训练器。它通过基于优化过程更新参数来训练模型：

```python
class ModelTrainer:
    """
    糖尿病分类器模型的训练器。
    """
    def __init__(self, model, criterion, optimizer, train_loader):
        """
        初始化 ModelTrainer。

        参数:
            model (torch.nn.Module):
                神经网络模型。
            criterion (torch.nn.Module):
                损失函数。
            optimizer (torch.optim.Optimizer):
                优化器。
            train_loader (torch.utils.data.DataLoader):
                训练数据加载器。
        """
        self.model = model
        self.criterion = criterion
        self.optimizer = optimizer
        self.train_loader = train_loader

    def train(self, epochs=100, lr=0.01):
        """
        训练模型。

        参数:
            epochs (int, 可选):
                训练轮数。默认为 100。
            lr (float, 可选):
                学习率。默认为 0.01。
        """
        try:
            for epoch in range(epochs):
                self.model.train()
                for inputs, targets in self.train_loader:
                    self.optimizer.zero_grad()
                    outputs = self.model(inputs)
                    loss = self.criterion(
                        outputs.squeeze(),
                        targets
                    )
                    loss.backward()
                    self.optimizer.step()
                    if (epoch + 1) % 10 == 0:
                        logging.info(
                            f"Epoch [{epoch + 1}/{epochs}],"
                            f"Loss: {loss.item():.4f}"
                        )
        except Exception as e:
            logging.error(
                f"Error occurred during model training:"
                f"{str(e)}"
            )
            raise e
```

`ModelTrainer` 类旨在促进糖尿病分类器模型的训练过程。其主要作用是管理训练循环，在训练数据上执行模型的前向和反向传播。

在 `__init__` 方法中，训练器通过四个关键组件进行初始化：神经网络模型（`model`）、损失函数（`criterion`）、优化器（`optimizer`）和训练数据加载器（`train_loader`）。这些组件对于有效训练模型至关重要。该方法作为 `ModelTrainer` 类的构造函数，确保在训练开始前所有必要的组件都已正确设置。每个参数都记录了其预期的类型和用途，从而增强了代码的可读性和可维护性。

`train` 方法是 `ModelTrainer` 类的核心，负责执行训练循环。在该方法内部，模型经过指定轮数的训练，每轮由对训练数据集的多次迭代组成。在每次迭代期间，模型被设置为训练模式（`self.model.train()`）。这一步骤很重要，因为某些层（如 Dropout 或批归一化）在训练模式下的行为与评估模式下不同。例如，Dropout 在训练期间随机禁用某些神经元以防止过拟合，但在评估期间所有神经元都处于激活状态。

随后重置梯度（`self.optimizer.zero_grad()`）。清零梯度是必要的，因为 PyTorch 中梯度默认是累积的。如果没有这一步骤，之前的梯度信息将干扰当前的反向传播过程，导致模型参数更新不正确。

执行前向传播（`outputs = self.model(inputs)`），模型处理输入数据并产生输出预测。然后通过将模型预测与实际目标值进行比较来计算损失（`loss = self.criterion(outputs.squeeze(), targets)`）。反向传播（`loss.backward()`）计算损失相对于模型参数的梯度，优化器步骤（`self.optimizer.step()`）根据这些梯度更新模型参数。

此外，该方法定期（每十个轮次）记录损失以监控训练进度。记录损失有助于在训练早期诊断梯度消失或过拟合等问题，以便必要时进行调整。

实现了异常处理以捕获并记录训练过程中可能出现的任何错误。这确保了问题被识别和报告，便于调试和模型优化。

## 步骤 5：模型评估

在这一步中，我们定义了 `ModelEvaluator` 类及其 `evaluate` 方法。此代码使用测试数据集评估训练好的模型。它计算诸如准确率、精确率、召回率、F1 分数、ROC-AUC 分数和混淆矩阵等性能指标，以评估模型的有效性：

```python
class ModelEvaluator:
    """
    糖尿病分类器模型的评估器。
    """
    def __init__(self, model, test_loader, y_test_np):
        """
        初始化 ModelEvaluator。

        参数:
            model (torch.nn.Module):
                神经网络模型。
            test_loader (torch.utils.data.DataLoader):
                测试数据加载器。
            y_test_np (numpy.ndarray):
                测试数据的真实标签。
        """
        self.model = model
        self.test_loader = test_loader
        self.y_test_np = y_test_np

    def evaluate(self):
        """
        评估模型。
        """
        try:
            with torch.no_grad():
                self.model.eval()
                predictions = []
                probabilities = []
                for inputs, _ in self.test_loader:
                    outputs = self.model(inputs)
                    probabilities.extend(
                        torch.sigmoid(outputs)
                        .squeeze().tolist()
                    )
                    predictions.extend(
                        outputs.squeeze().tolist()
                    )

                y_pred = np.array(
                    [1 if pred > 0.5 else 0
                    for pred in probabilities]
                )

                accuracy = accuracy_score(
                    self.y_test_np,
                    y_pred
                )
                precision = precision_score(
                    self.y_test_np,
                    y_pred
                )
                recall = recall_score(self.y_test_np, y_pred)
                f1 = f1_score(self.y_test_np, y_pred)

                logging.info(f"Accuracy: {accuracy:.4f}")
                logging.info(f"Precision: {precision:.4f}")
                logging.info(f"Recall: {recall:.4f}")
                logging.info(f"F1 Score: {f1:.4f}")

                conf_matrix = confusion_matrix(
                    self.y_test_np,
                    y_pred
                )
                logging.info(
                    "Confusion Matrix:\n" + str(conf_matrix)
                )
                roc_auc = roc_auc_score(
                    self.y_test_np, probabilities
                )
                logging.info(f"ROC-AUC Score: {roc_auc:.4f}")
        except Exception as e:
            logging.error(
                f"Error occurred during model "
                f"evaluation: {str(e)}"
            )
            raise e
```

`ModelEvaluator` 类充当糖尿病分类器模型的评估器，负责评估其在测试数据上的性能。

该类通过三个关键组件初始化：神经网络模型（`model`）、测试数据加载器（`test_loader`）和测试数据的真实标签（`y_test_np`）。这些组件对于准确评估模型性能至关重要。`__init__` 方法充当构造函数，确保在评估开始前所有必要元素都已正确设置。每个参数都记录了其预期的类型和用途，从而增强了代码的清晰度和易用性。

`evaluate` 方法是 `ModelEvaluator` 类的核心，负责执行评估过程。在该方法内部


模型被设置为评估模式（`self.model.eval()`），这一点非常重要，因为某些层（例如 dropout）在训练和评估期间的表现不同。

- 使用训练好的模型为测试数据生成预测结果。使用 `torch.no_grad()` 上下文管理器以确保禁用梯度计算，从而在评估过程中节省内存和计算时间。

为了获得最终预测结果：

- 使用 sigmoid 函数（`torch.sigmoid(outputs)`）计算概率，该函数将原始输出分数转换为概率。
- 基于这些概率确定最终预测标签（`y_pred`），使用 0.5 作为阈值对预测结果进行分类。

随后计算各种性能指标：

- 准确率（Accuracy）：衡量正确分类样本的比例
- 精确率（Precision）：表示所有阳性预测中真实阳性预测的比例
- 召回率（Recall）：表示所有实际阳性样本中真实阳性预测的比例
- F1 分数：提供精确率和召回率之间的平衡

此外，该方法还计算并记录以下指标：

- 混淆矩阵（Confusion Matrix）：提供真实阳性、假阳性、真实阴性和假阴性的详细分解
- ROC-AUC 分数：衡量模型在不同阈值下区分类别的能力，提供其性能的摘要

在 `evaluate` 方法中实现了异常处理，用于捕获和记录评估过程中可能出现的任何错误。这确保了潜在问题能够被识别和报告，从而便于有效的调试和错误解决。

## 步骤 6：附加功能

此最终步骤中的代码包括 `copy_file_from_s3` 函数、日志配置以及主执行部分。这些代码处理诸如从 AWS S3 存储桶复制数据、设置日志以进行监控以及编排建模过程的主执行流程等附加任务：

```python
def copy_file_from_s3(bucket_name, file_name, local_dir):
    """
    Copies a file from S3 bucket to local directory.

    Args:
        bucket_name (str): The name of the S3 bucket.
        file_name (str):
            The name of the file to be copied.
        local_dir (str):
            The local directory where the file will be copied.
    """
    try:
        s3 = boto3.client("s3")
        s3.download_file(
            bucket_name,
            file_name,
            local_dir + file_name
        )
    except Exception as e:
        logging.error(
            f"Error occurred during file copying: "
            f"{str(e)}"
        )
        raise e
```

```python
if __name__ == "__main__":
    logging.basicConfig(level=logging.INFO)
    spark = (SparkSession.builder
            .appName("DiabetesClassifier")
            .getOrCreate())
    copy_file_from_s3(
        "instance1bucket",
        "diabetes.csv",
        "/home/ubuntu/airflow/dags/"
    )

    data_preprocessor = DataPreprocessor(
        spark,
        "/home/ubuntu/airflow/dags/diabetes.csv"
    )
    train_df, test_df = data_preprocessor.preprocess()

    X_train_np = np.array(
        train_df.select("scaled_features")
        .rdd.flatMap(lambda x: x).collect(),
        dtype=np.float32,
    )
    y_train_np = np.array(
        train_df.select("Outcome")
        .rdd.flatMap(lambda x: x).collect(),
        dtype=np.float32,
    )

    train_dataset = TensorDataset(
        torch.tensor(X_train_np),
        torch.tensor(y_train_np)
    )
    train_loader = DataLoader(
        train_dataset,
        batch_size=64,
        shuffle=True
    )

    input_size = X_train_np.shape[1]
    output_size = 1
    model = DiabetesClassifierModel(
        input_size,
        output_size
    )
    criterion = nn.BCEWithLogitsLoss()
    optimizer = optim.Adam(model.parameters(), lr=0.01)
    model_trainer = ModelTrainer(
        model,
        criterion,
        optimizer, train_loader
    )
    model_trainer.train()

    X_test_np = np.array(
        test_df.select("scaled_features")
        .rdd.flatMap(lambda x: x).collect(),
        dtype=np.float32,
    )
    y_test_np = np.array(
        test_df.select("Outcome")
        .rdd.flatMap(lambda x: x).collect()
    )

    test_dataset = TensorDataset(
        torch.tensor(X_test_np),
        torch.tensor(y_test_np, dtype=torch.float32)
    )
    test_loader = DataLoader(
        test_dataset,
        batch_size=64,
        shuffle=False
    )

    model_evaluator = ModelEvaluator(
        model,
        test_loader,
        y_test_np
    )

    model_evaluator.evaluate()
```

这段代码由一个 Python 脚本组成，负责将糖尿病 CSV 文件从 Amazon S3 存储桶复制到 EC2 上的本地目录，使用 Spark 执行数据预处理，并使用 PyTorch 训练和评估糖尿病分类模型。

让我们分解如下：

### 从 S3 复制文件

- 定义了 `copy_file_from_s3` 函数，用于将文件从 S3 存储桶复制到本地目录。它接受三个参数：`bucket_name`（S3 存储桶的名称）、`file_name`（要复制的文件名称）和 `local_dir`（文件将复制到其中的本地目录）。
- 在函数内部，使用 `boto3` 库创建了一个 S3 客户端。然后调用 `download_file` 方法，将指定文件从 S3 存储桶下载到本地目录。

### 数据预处理

- 在设置日志后，使用 `SparkSession` 创建了一个 Spark 会话。该会话配置了应用程序名称“DiabetesClassifier”。
- 调用 `copy_file_from_s3` 函数，将名为“diabetes.csv”的文件从 S3 存储桶“instance1bucket”复制到本地目录“/home/ubuntu/airflow/dags/”。
- 创建了 `DataPreprocessor` 类的实例，指定了 Spark 会话和糖尿病数据集文件的路径。
- 调用 `DataPreprocessor` 实例的 `preprocess` 方法进行数据预处理，从而得到训练集和测试集 DataFrame（`train_df` 和 `test_df`）。

### 模型训练和评估

- 训练集和测试集 DataFrame 被转换为 NumPy 数组（`X_train_np`、`y_train_np`、`X_test_np`、`y_test_np`），用于训练和评估。
- 使用 PyTorch 的 DataLoaders 和 TensorDataset 从 NumPy 数组创建训练集和测试集（`train_dataset`、`test_dataset`）。
- 实例化了糖尿病分类模型（`DiabetesClassifierModel`），以及损失函数（`BCEWithLogitsLoss`）和优化器（`Adam`）。
- 使用模型、损失函数、优化器和训练 DataLoader 创建了 `ModelTrainer` 类的实例。然后调用 `ModelTrainer` 实例的 `train` 方法来训练模型。
- 使用模型、测试 DataLoader 和真实标签创建了 `ModelEvaluator` 类的另一个实例。调用 `ModelEvaluator` 实例的 `evaluate` 方法来评估训练好模型的性能。

这段代码展示了一个完整的流水线，用于构建、训练和评估糖尿病分类模型，其中包含文件处理、使用 Spark 进行的数据预处理以及使用 PyTorch 进行的深度学习。

为了运行代码，我们将其保存为“diabetes_classifier_pipeline.py”，并在 JupyterLab 终端中执行了它（或者，我们也可以直接在 EC2 实例上运行它）。由于我们创建了一个名为“myenv”的环境，我们按如下方式激活了它：

```bash
source /home/ubuntu/myenv/bin/activate
```

激活环境后，我们使用 Python 3 通过以下命令执行了代码：

```bash
python3 diabetes_classifier_pipeline.py
```

代码的第一个输出是一个训练进度表，总结了糖尿病分类模型在多个轮次（epochs）上的训练情况：

| Epoch | Loss |
| :-- | :-- |
| 10 | 0.5899 |
| 20 | 0.4330 |
| 30 | 0.4608 |
| 40 | 0.4612 |
| 50 | 0.5155 |
| 60 | 0.4025 |
| 70 | 0.3406 |
| 80 | 0.4323 |
| 90 | 0.4822 |
| 100 | 0.3203 |

训练进度表中的每一行代表一个 epoch，指示 epoch 编号和对应的损失值。例如，行“Epoch 10/100, Loss 0.5899”意味着在 10 个 epoch 的训练后，模型的损失约为 0.59。同样，随后的行提供了训练结束（本例中为 100 个 epoch）前不同 epoch 的损失值。

损失值是使用 `BCEWithLogitsLoss` 函数计算的，该函数代表 Binary Cross-Entropy with Logits Loss（带 Logits 的二元交叉熵损失）。该函数通常用于二元分类任务，如本场景中的糖尿病预测任务。





## 基于损失值的观察：

-   **趋势**：起初损失值存在波动，但整体呈现下降趋势，表明模型性能有所提升。在训练过程中的某些 epoch 内，损失值先上升后再次下降，这表明训练过程存在一定的不稳定性。

-   **数值量级**：损失值大约在 0.32 到 0.59 之间。训练末期损失值的下降表明模型正在收敛于更优的解。

-   **优化**：波动的损失值反映了优化过程。模型通过调整参数来最小化损失函数，而不断下降的损失值表明模型的预测结果与训练数据中的实际目标值之间的对齐程度正在逐步提高。

第二个输出是评估指标表：

| 指标 | 数值 |
| --- | --- |
| 准确率 (Accuracy) | 0.7607 |
| 精确率 (Precision) | 0.6585 |
| 召回率 (Recall) | 0.6585 |
| F1 分数 (F1 Score) | 0.6585 |
| ROC-AUC 分数 (ROC-AUC Score) | 0.8135 |

让我们逐一解释这些指标：

**准确率 (Accuracy)**：准确率衡量的是在测试数据集中所有实例中分类正确的实例所占的比例。在数学上，它计算为预测正确的实例数与实例总数之比。例如，准确率为 0.7607 意味着测试数据集中约有 76.07% 的实例被模型正确分类。

**精确率 (Precision)**：精确率衡量的是模型做出的所有阳性预测中真阳性预测所占的比例。它关注的是阳性预测的正确性，计算方式为真阳性数与真阳性数和假阳性数之和的比值。精确率为 0.6585 表明模型预测为阳性的实例中，约有 65.85% 实际上是阳性的。

**召回率 (Recall)**：召回率也称为灵敏度，衡量的是测试数据集中所有实际阳性实例中真阳性预测所占的比例。它关注的是捕获所有阳性实例的能力，计算方式为真阳性数与真阳性数和假阴性数之和的比值。召回率为 0.6585 意味着所有实际为阳性的实例中，约有 65.85% 被模型正确识别。

**F1 分数 (F1 Score)**：F1 分数是精确率和召回率的调和平均值，在两者之间提供平衡。它同时考虑了假阳性和假阴性，计算公式为 $2 \times \frac{\text{精确率} \times \text{召回率}}{\text{精确率} + \text{召回率}}$。F1 分数为 0.6585 表明了模型在精确率和召回率两方面的综合有效性，分数越高表示性能越好。

**ROC-AUC 分数 (ROC-AUC Score)**：ROC-AUC 分数衡量模型在不同阈值下区分阳性和阴性实例的能力。0.8135 的分数表明模型在类间区分度上表现较高，能够良好地区分两类。

模型还输出了混淆矩阵：

```
[[62 14]
 [14 27]]
```

混淆矩阵提供了模型性能的详细分解：

-   **真阳性 (TP)**: 27
-   **假阳性 (FP)**: 14
-   **真阴性 (TN)**: 62
-   **假阴性 (FN)**: 14

这表明模型：

-   正确预测了 62 个阴性实例（真阴性）
-   错误地预测了 14 个阴性实例为阳性（假阳性）
-   未能识别出 14 个阳性实例（假阴性）
-   正确预测了 27 个阳性实例（真阳性）

基于这些数据，我们可以如下复现评估指标表中的计算：

Accuracy = $\frac{\text{TP} + \text{TN}}{\text{TP} + \text{TN} + \text{FP} + \text{FN}}$

代入数值：

```
Accuracy = (27+62)/(27+62+14+14) = 89/117
 = 0.7607
```

Precision 计算为 $\frac{\text{TP}}{\text{TP} + \text{FP}} = \frac{27}{27+14}$。

$Precision = \frac{27}{41} = 0.6585$

Recall 计算为 $\frac{\text{TP}}{\text{TP} + \text{FN}}$。

代入数值：

$Recall = \frac{27}{27+14} = \frac{27}{41} = 0.6585$

$\text{F1\ score} = 2 \times \left[ \frac{\text{precision} \times \text{recall}}{\text{precision} + \text{recall}} \right]$

代入数值：

$F1 = 2 \times \left[ \frac{0.6585 \times 0.6585}{0.6585 + 0.6585} \right] = 0.6585$

基于这两个输出（损失值和评估指标），模型表现一般。其中一个原因是探索阶段观察到的类别不平衡和特征偏差。此外，样本量有限，且存在潜在的数据质量问题。

在 Pima 数据集的实际应用场景中，将考虑以下几个改进方面：

-   **数据质量**：对于该数据集，确保数据质量非常重要，尽管其规模有限。例如，在数据探索过程中，我们观察到 Glucose 属性的最小值为 44，这可能暗示低血糖并引发对数据完整性的担忧。同样，BloodPressure 项显示了一个异常低的最小值 24，这对于有效的血压读数来说极不可能，表明数据收集过程中可能存在错误。此外，DiabetesPedigreeFunction 特征的最小值为 0.078，作为与糖尿病相关的遗传风险因子，这一数值明显偏低。另外，Pregnancies 字段显示的最大计数为 17，虽然在生物学上是可能的，但极为罕见。这些观察结果强调了需要进一步审查和验证以确保数据集可靠性。

-   **重采样**：重采样技术，如少数类过采样或多数类欠采样，可以帮助平衡数据集中类别的分布，从而改进模型性能并减少对多数类的偏见。

-   **数据增强**：尽管传统上数据增强与图像数据相关联，但它对于 Pima 数据集仍然有益。通过转换（如扰动特征值或引入噪声）生成额外的合成数据点，我们可以有效地扩展数据集的大小。这种增强使数据集多样化，通过向葡萄糖水平、血压测量值、BMI 值或其他数值特征添加小的随机变化，可能提高模型的泛化能力。这种变化有助于生成多样化的训练样本，防止模型过度依赖数据中的特定值或模式。

-   **迁移学习**：虽然迁移学习在非图像任务中应用不如在图像任务中常见，但它仍能为 Pima 数据集带来好处。通过利用在相关任务或数据集上预训练模型的知识，我们可以在小数据集上对这些模型进行微调。这种自适应有助于模型更高效地捕获相关模式，从而在有限的训练数据下提高性能。

-   **模型复杂度**：平衡模型复杂度至关重要，特别是对于像 Pima 这样的小型数据集。复杂的模型可能会面临过拟合的风险，因此找到模型复杂度与数据集大小之间的正确平衡，以有效捕获潜在模式同时避免过拟合，是必要的。例如，在探索过程中，我们发现 Glucose 和 BMI 是最强的预测因子。仅基于这些特征构建更小的模型可能会提供更好的结果。

-   **数据表示**：有效的数据表示对于像 Pima 这样的小型数据集至关重要。预处理技术，如特征提取或降维，可以增强输入数据的质量并促进深度神经网络的训练。

-   **超参数调优**：进一步调优学习率、批次大小和网络架构等超参数可能提高模型的收敛性和性能。正则化、Dropout 或不同的优化算法等高级技术也可能有助于缓解过拟合并提高泛化能力。在第 9 章中，我们将探索其中的一些技术。

-   **交叉验证**：采用 K 折交叉验证对于获得模型性能的可靠估计至关重要，特别是对于像 Pima 这样的小型数据集。该方法通过在一组多个折上评估模型，减少了因单次数据划分的变异性而导致过拟合或欠拟合的风险。下文将详细探讨这一选项。





## 使用交叉验证增强模型评估

K折交叉验证对于获得模型性能的可靠估计至关重要，尤其是在数据有限的情况下。通过将数据集划分为K个折，并在这些折上迭代执行训练和测试过程，该技术确保了每个数据点都被用于训练和验证。这种方法通过平均多个子集的性能来降低过拟合和欠拟合的风险，从而实现更均衡的评估。此外，K折交叉验证最大化了可用数据的使用，有助于超参数调整，并帮助解决诸如类别不平衡等问题，最终使模型在未见数据上具有更好的泛化能力。

要在原始代码中实现K折交叉验证，我们遵循以下步骤：

- **步骤 1：导入 KFold**

```python
from sklearn.model_selection import KFold
```

此导入启用了 Scikit-Learn 中的 KFold 类，这是实现K折交叉验证所必需的。

- **步骤 2：定义折数**

```python
k_folds = 5
kfold = KFold(n_splits=k_folds, shuffle=True, random_state=42)
```

这设置了五折的K折交叉验证，在划分前对数据进行洗牌，并使用随机种子以确保可重复性。

- **步骤 3：遍历每个折**

```python
fold_results = []

for fold, (train_idx, test_idx) in enumerate(kfold.split(X_np)):
    logging.info(f"Training fold {fold + 1}/{k_folds}")

    X_train, X_test = X_np[train_idx], X_np[test_idx]
    y_train, y_test = y_np[train_idx], y_np[test_idx]

    # Convert to PyTorch datasets
    train_dataset = TensorDataset(
        torch.tensor(X_train),
        torch.tensor(y_train)
    )
    test_dataset = TensorDataset(
        torch.tensor(X_test),
        torch.tensor(y_test)
    )

    # Create DataLoaders
    train_loader = DataLoader(
        train_dataset,
        batch_size=64,
        shuffle=True
    )
    test_loader = DataLoader(
        test_dataset,
        batch_size=64,
        shuffle=False
    )

    # Initialize the model, criterion, and optimizer
    input_size = X_train.shape[1]
    output_size = 1
    model = DiabetesClassifierModel(input_size, output_size)
    criterion = nn.BCEWithLogitsLoss()
    optimizer = optim.Adam(model.parameters(), lr=0.01)

    # Train the model
    model_trainer = ModelTrainer(
        model,
        criterion,
        optimizer,
        train_loader
    )
    model_trainer.train()

    # Evaluate the model
    model_evaluator = ModelEvaluator(
        model,
        test_loader,
        y_test
    )
    results = model_evaluator.evaluate()

    # Append results to the fold_results list
    fold_results.append(results)
```

在这段代码中，K折交叉验证在主函数中实现。数据集首先经过预处理并转换为 NumPy 数组（X_np 用于特征，y_np 用于标签）。使用 Scikit-Learn 中的 KFold 类创建K折划分，其中 k_folds = 5，意味着数据集被划分为五个折。

在循环内部，使用K折划分确定训练和测试索引。然后将相应的数据划分为训练集和测试集。为训练数据和测试数据创建 PyTorch 数据集，然后将其加载到 DataLoaders 中，以便在模型训练期间促进批处理。

对于每个折，初始化模型，使用 ModelTrainer 类进行训练，并使用 ModelEvaluator 类进行评估。计算每个折的评估指标——如准确率、精确率、召回率、F1 分数和 ROC-AUC 分数——并将它们存储在列表中。

- **步骤 4：聚合各折的结果**

```python
avg_accuracy = np.mean([result['accuracy'] for result in fold_results])
avg_precision = np.mean([result['precision'] for result in fold_results])
avg_recall = np.mean([result['recall'] for result in fold_results])
avg_f1 = np.mean([result['f1'] for result in fold_results])
avg_roc_auc = np.mean([result['roc_auc'] for result in fold_results])

logging.info(f"Average Accuracy: {avg_accuracy:.4f}")
logging.info(f"Average Precision: {avg_precision:.4f}")
logging.info(f"Average Recall: {avg_recall:.4f}")
logging.info(f"Average F1 Score: {avg_f1:.4f}")
logging.info(f"Average ROC-AUC Score: {avg_roc_auc:.4f}")
```

在所有折处理完成后，对结果进行平均，以提供模型性能的更稳健的估计。然后记录这些平均性能，提供模型在不同数据子集上泛化能力的全面视图。K折交叉验证确保模型的评估不依赖于单一的训练-测试划分，从而提供对其能力更均衡、更准确的评估。

下表显示了K折交叉验证的结果：

| 折 | 准确率 | 精确率 | 召回率 | F1 分数 | ROC-AUC 分数 |
| :--- | :--- | :--- | :--- | :--- | :--- |
| 折 1 | 0.7586 | 0.5833 | 0.6512 | 0.6154 | 0.8347 |
| 折 2 | 0.7103 | 0.6774 | 0.3962 | 0.5000 | 0.7966 |
| 折 3 | 0.7586 | 0.6078 | 0.6739 | 0.6392 | 0.8048 |
| 折 4 | 0.8000 | 0.7826 | 0.6545 | 0.7129 | 0.8711 |
| 折 5 | 0.7569 | 0.7297 | 0.5192 | 0.6067 | 0.8242 |
| **平均值** | **0.7569** | **0.6762** | **0.5790** | **0.6148** | **0.8263** |

结果显示，模型在各折中表现一致，平均准确率为 75.69%，鉴于小型糖尿病数据集，这表明性能合理。其他指标——精确率、召回率、F1 分数和 ROC-AUC——也提供了关于模型预测能力的见解，其中 ROC-AUC 分数平均为 0.8263，表明具有良好的判别能力。

## 综合所有内容

在本节中，我们将本章中讨论的用于探索 Pima 糖尿病数据集以及构建、训练和评估 PyTorch 深度学习模型（带或不带K折交叉验证）的各个独立代码片段进行整合。

### 探索 Pima 糖尿病数据集

```python
from pyspark.sql import SparkSession
from pyspark.sql.functions import col, sum as pyspark_sum
import boto3

class PimaDatasetExplorer:
    """
    Class for exploring and analyzing a Pima Indian Diabetes
    dataset using PySpark.
    """
    
    def __init__(self, file_path):
        """
        Initializes the PimaDatasetExplorer object.
        
        Args:
            file_path (str): The path to the dataset file.
        """
        self.file_path = file_path
        self.data = None

    def load_data(self):
        """
        Loads the dataset from the specified file path into a PySpark DataFrame.
        """
        try:
            self.data = spark.read.csv(
                self.file_path,
                header=True,
                inferSchema=True
            )
            self.data.cache()
        except Exception as e:
            print(
                "An error occurred while loading the data:",
                str(e)
            )
            self.data = None

    def preprocess_data(self):
        """
        Performs preprocessing steps on the dataset.
        """
        self.load_data()

    def handle_missing_values(self):
        """
        Counts the number of missing values for each column
        in the dataset and displays the counts.
        """
        if self.data is not None:
            missing_counts = self.data.select([
                pyspark_sum(col(c).isNull()).cast("int").alias(c)
                for c in self.data.columns
            ])
            print("Missing Value Counts:")
            missing_counts.show()
```




## 第6章 使用PyTorch进行深度学习分类

### 使用PyTorch进行模型构建、训练与评估

在本小节中，我们整合了使用PyTorch进行糖尿病预测的代码，分别涉及有和没有K折交叉验证的情况。

### 无K折交叉验证的糖尿病分类

```python
[In] import boto3
[In] import logging
[In] import numpy as np
[In] import torch
[In] import torch.nn as nn
[In] import torch.optim as optim
[In] from torch.utils.data import DataLoader, TensorDataset
[In] from sklearn.metrics import (
    accuracy_score,
    precision_score,
    recall_score,
    f1_score,
    confusion_matrix,
    roc_auc_score
)
[In] from pyspark.sql import SparkSession
[In] from pyspark.ml.feature import (
    VectorAssembler,
    StandardScaler
)
[In] from pyspark.sql.functions import col
```

```python
[In] class DataPreprocessor:
    """
    对糖尿病数据集进行预处理。
    """

    def __init__(self, spark, data_file_path):
        """
        初始化 DataPreprocessor。

        Args:
            spark (pyspark.sql.SparkSession):
                Spark 会话。
            data_file_path (str):
                数据文件的路径。
        """
        self.spark = spark
        self.data_file_path = data_file_path

    def preprocess(self):
        """
        执行数据预处理。

        Returns:
            tuple:
                包含训练集和测试集 DataFrame
                的元组。
        """
        try:
            diabetes_df = self.spark.read.csv(
                self.data_file_path,
                header=True,
                inferSchema=True
            )
            diabetes_df = diabetes_df.filter(
                (col("Glucose") != 0)
                & (col("BloodPressure") != 0)
                & (col("BMI") != 0)
            )
            feature_cols = [
                "Pregnancies",
                "Glucose",
                "BloodPressure",
                "BMI",
                "DiabetesPedigreeFunction",
                "Age",
            ]
            assembler = VectorAssembler(
                inputCols=feature_cols,
                outputCol="features"
            )
            diabetes_df = assembler.transform(diabetes_df)
            scaler = StandardScaler(
                inputCol="features",
                outputCol="scaled_features"
            )
            scaler_model = scaler.fit(diabetes_df)
            diabetes_df = scaler_model.transform(diabetes_df)
            train_df, test_df = diabetes_df.randomSplit(
                [0.8, 0.2],
                seed=42
            )
            return train_df, test_df
        except Exception as e:
            logging.error(
                f"数据预处理过程中发生错误: {str(e)}"
            )
            raise e
```

```python
[In] class DiabetesClassifierModel(nn.Module):
    """
    用于糖尿病分类的神经网络模型。
    """

    def __init__(self, input_size, output_size):
        """
        初始化 DiabetesClassifierModel。

        Args:
            input_size (int): 输入尺寸。
            output_size (int): 输出尺寸。
        """
        super(DiabetesClassifierModel, self).__init__()
        self.model = nn.Sequential(
            nn.Linear(input_size, 64),
            nn.ReLU(),
            nn.Linear(64, 32),
            nn.ReLU(),
            nn.Linear(32, 16),
            nn.ReLU(),
            nn.Linear(16, output_size),
        )

    def forward(self, x):
        """
        定义模型的前向传播。
        """
        return self.model(x)
```

```python
[In] def count_zeros(self):
    """
    统计数据集中每列的零值数量并显示统计结果。
    """
    if self.data is not None:
        zero_counts = self.data.select([
            pyspark_sum((col(c) == 0).cast("int")).alias(c)
            for c in self.data.columns
        ])
        print("零值计数:")
        zero_counts.show()
    else:
        print("数据未加载。")
```

```python
[In] def data_summary(self):
    """
    显示数据集的摘要，排除特定列，并过滤特定列中包含零值的行。
    """
    if self.data is not None:
        print("数据摘要（排除 'Outcome',
              'SkinThickness', 'Insulin'）:")
        columns_to_exclude = ['Outcome',
                              'SkinThickness',
                              'Insulin']
        summary_cols = [c for c in self.data.columns
                       if c not in columns_to_exclude]
        filtered_data = self.data.filter(
            (col("Glucose") != 0)
            & (col("BloodPressure") != 0)
            & (col("BMI") != 0)
        )
        filtered_data.select(summary_cols).describe().show()
    else:
        print("数据未加载。")
```

```python
[In] def count_outcome(self):
    """
    统计数据集中每个结果值的出现次数。
    """
    if self.data is not None:
        print("结果值计数:")
        outcome_counts = self.data.filter(
            (col("Glucose") != 0)
            & (col("BloodPressure") != 0)
            & (col("BMI") != 0)
        ).groupBy("Outcome").count()
        outcome_counts.show()
    else:
        print("数据未加载。")
```

```python
[In] def explore_feature_distributions(self):
    """
    绘制数据集中每个特征分布的直方图。
    """
    if self.data is not None:
        print("特征分布:")
        for column in self.data.columns:
            if column not in ['SkinThickness', 'Insulin']:
                print(f"特征: {column}")
                if column in ["Glucose",
                               "BloodPressure",
                               "BMI"]:
                    filtered_data = self.data.filter(
                        (col(column) != 0)
                        & (col("Glucose") != 0)
                        & (col("BloodPressure") != 0)
                        & (col("BMI") != 0)
                    )
                else:
                    filtered_data = self.data
                plot_data = filtered_data.select(column).toPandas()
                plot_data.plot(kind='hist', title=column)
        else:
            print("数据未加载。")
```

```python
[In] def calculate_feature_target_correlation(self):
    """
    计算每个特征与目标变量（'Outcome'）之间的相关性。
    """
    if self.data is not None:
        print("特征-目标相关性 "
              "（排除 'SkinThickness', 'Insulin'）:")
        for column in self.data.columns:
            if column not in ['Outcome',
                              'SkinThickness',
                              'Insulin']:
                correlation = self.data.filter(
                    (col(column) != 0)
                    & (col("Glucose") != 0)
                    & (col("BloodPressure") != 0)
                    & (col("BMI") != 0)
                ).stat.corr(column, 'Outcome')
                print(f"{column}: {correlation}")
        else:
            print("数据未加载。")
```

```python
[In] def copy_file_from_s3(bucket_name, file_key, local_path):
    """
    从 AWS S3 存储桶复制文件到本地路径。

    Args:
        bucket_name (str): S3 存储桶的名称。
        file_key (str): 文件在 S3 存储桶中的键。
        local_path (str):
            文件将被复制到的本地路径。
    """
    try:
        s3 = boto3.client('s3')
        s3.download_file(bucket_name, file_key, local_path)
        print(f"文件 {file_key} 已下载到 {local_path}")
    except Exception as e:
        print(f"下载文件 {file_key} 时发生错误:",
              str(e))
```

```python
[In] if __name__ == "__main__":
    spark = (SparkSession.builder
             .appName("PimaDatasetExplorer")
             .getOrCreate())
    local_file_path = "/home/ubuntu/airflow/dags/diabetes.csv"
    s3_bucket_name = "instance1bucket"
    s3_file_key = "diabetes.csv"
    copy_file_from_s3(
        s3_bucket_name,
        s3_file_key,
        local_file_path
    )
    
    explorer = PimaDatasetExplorer(local_file_path)
    explorer.preprocess_data()
    explorer.handle_missing_values()
    explorer.count_zeros()
    explorer.data_summary()
    explorer.count_outcome()
    explorer.explore_feature_distributions()
    explorer.calculate_feature_target_correlation()
```




## 第 6 章 使用 PyTorch 进行深度学习的分类任务

### 参数与返回值
- `x` (`torch.Tensor`)：输入张量。
- 返回值：`torch.Tensor`：输出张量。

```python
return self.model(x)
```

### ModelTrainer 类
```python
class ModelTrainer:
    """
    用于糖尿病分类器模型的训练器。
    """
    
    def __init__(
        self, model,
        criterion,
        optimizer,
        train_loader
    ):
        """
        初始化 ModelTrainer。
        
        参数:
            model (torch.nn.Module):
                神经网络模型。
            criterion (torch.nn.Module):
                损失函数。
            optimizer (torch.optim.Optimizer):
                优化器。
            train_loader (torch.utils.data.DataLoader):
                训练数据加载器。
        """
        self.model = model
        self.criterion = criterion
        self.optimizer = optimizer
        self.train_loader = train_loader

    def train(self, epochs=100, lr=0.01):
        """
        训练模型。

        参数:
            epochs (int, 可选):
                训练轮数。默认为 100。
            lr (float, 可选):
                学习率。默认为 0.01。
        """
        try:
            for epoch in range(epochs):
                self.model.train()
                for inputs, targets in self.train_loader:
                    self.optimizer.zero_grad()
                    outputs = self.model(inputs)
                    loss = self.criterion(
                        outputs.squeeze(),
                        targets
                    )
                    loss.backward()
                    self.optimizer.step()
                if (epoch + 1) % 10 == 0:
                    logging.info(
                        f"Epoch [{epoch + 1}/{epochs}],"
                        f"Loss: {loss.item():.4f}"
                    )
        except Exception as e:
            logging.error(
                f"Error occurred during model training: "
                f"{str(e)}"
            )
            raise e
```

### ModelEvaluator 类
```python
class ModelEvaluator:
    """
    用于糖尿病分类器模型的评估器。
    """
    def __init__(self, model, test_loader, y_test_np):
        """
        初始化 ModelEvaluator。

        参数:
            model (torch.nn.Module):
                神经网络模型。
            test_loader (torch.utils.data.DataLoader):
                测试数据加载器。
            y_test_np (numpy.ndarray):
                测试数据的真实标签。
        """
        self.model = model
        self.test_loader = test_loader
        self.y_test_np = y_test_np

    def evaluate(self):
        """
        评估模型。
        """
        try:
            with torch.no_grad():
                self.model.eval()
                predictions = []
                probabilities = []
                for inputs, _ in self.test_loader:
                    outputs = self.model(inputs)
                    probabilities.extend(
                        torch.sigmoid(outputs)
                        .squeeze().tolist()
                    )
                    predictions.extend(
                        outputs.squeeze().tolist()
                    )

            y_pred = np.array(
                [1 if pred > 0.5 else 0
                 for pred in probabilities]
            )

            accuracy = accuracy_score(
                self.y_test_np,
                y_pred
            )
            precision = precision_score(
                self.y_test_np,
                y_pred
            )
            recall = recall_score(self.y_test_np, y_pred)
            f1 = f1_score(self.y_test_np, y_pred)

            logging.info(f"Accuracy: {accuracy:.4f}")
            logging.info(f"Precision: {precision:.4f}")
            logging.info(f"Recall: {recall:.4f}")
            logging.info(f"F1 Score: {f1:.4f}")
            
            conf_matrix = confusion_matrix(
                self.y_test_np,
                y_pred
            )
            logging.info(
                "Confusion Matrix:\n" + str(conf_matrix)
            )
            
            roc_auc = roc_auc_score(
                self.y_test_np, probabilities
            )
            logging.info(f"ROC-AUC Score: {roc_auc:.4f}")

        except Exception as e:
            logging.error(
                f"Error occurred during model "
                f"evaluation: {str(e)}"
            )
            raise e
```

### 辅助函数：copy_file_from_s3
```python
def copy_file_from_s3(bucket_name, file_name, local_dir):
    """
    将文件从 S3 存储桶复制到本地目录。

    参数:
        bucket_name (str):
            S3 存储桶的名称。
        file_name (str):
            要复制的文件名。
        local_dir (str):
            文件将被复制到的本地目录。
    """
    try:
        s3 = boto3.client("s3")
        s3.download_file(
            bucket_name,
            file_name,
            local_dir + file_name
        )
    except Exception as e:
        logging.error(
            f"Error occurred during file copying: "
            f"{str(e)}"
        )
        raise e
```

### 主执行逻辑
```python
if __name__ == "__main__":
    logging.basicConfig(level=logging.INFO)
    spark = SparkSession.builder \
        .appName("DiabetesClassifier") \
        .getOrCreate()
    
    copy_file_from_s3(
        "instance1bucket",
        "diabetes.csv",
        "/home/ubuntu/airflow/dags/"
    )

    data_preprocessor = DataPreprocessor(
        spark,
        "/home/ubuntu/airflow/dags/diabetes.csv"
    )
    train_df, test_df = data_preprocessor.preprocess()

    X_train_np = np.array(
        train_df.select("scaled_features")
        .rdd.flatMap(lambda x: x).collect(),
        dtype=np.float32,
    )
    y_train_np = np.array(
        train_df.select("Outcome")
        .rdd.flatMap(lambda x: x).collect(),
        dtype=np.float32,
    )

    train_dataset = TensorDataset(
        torch.tensor(X_train_np),
        torch.tensor(y_train_np)
    )
    train_loader = DataLoader(
        train_dataset,
        batch_size=64,
        shuffle=True
    )

    input_size = X_train_np.shape[1]
    output_size = 1
    model = DiabetesClassifierModel(
        input_size,
        output_size
    )
    criterion = nn.BCEWithLogitsLoss()
    optimizer = optim.Adam(model.parameters(), lr=0.01)
    model_trainer = ModelTrainer(
        model, criterion,
        optimizer,
        train_loader
    )
    model_trainer.train()

    X_test_np = np.array(
        test_df.select("scaled_features")
        .rdd.flatMap(lambda x: x).collect(),
        dtype=np.float32,
    )
    y_test_np = np.array(
        test_df.select("Outcome")
        .rdd.flatMap(lambda x: x).collect()
    )

    test_dataset = TensorDataset(
        torch.tensor(X_test_np),
        torch.tensor(y_test_np, dtype=torch.float32)
    )
    test_loader = DataLoader(
        test_dataset,
        batch_size=64,
        shuffle=False
    )

    model_evaluator = ModelEvaluator(
        model,
        test_loader,
        y_test_np
    )
    model_evaluator.evaluate()
```

### 使用 K 折交叉验证进行糖尿病分类

```python
import boto3
import logging
import numpy as np
import torch
import torch.nn as nn
import torch.optim as optim
from torch.utils.data import DataLoader, TensorDataset
from sklearn.metrics import (
    accuracy_score,
    precision_score,
    recall_score,
    f1_score,
    confusion_matrix,
    roc_auc_score,
)
from sklearn.model_selection import KFold
from pyspark.sql import SparkSession
from pyspark.ml.feature import VectorAssembler, StandardScaler
from pyspark.sql.functions import col

class DataPreprocessor:
    """
    预处理糖尿病数据集。
    """
    def __init__(self, spark, data_file_path):
        """
        初始化 DataPreprocessor。

        参数:
            spark (pyspark.sql.SparkSession): Spark 会话。
            data_file_path (str): 数据文件的路径。
        """
        self.spark = spark
        self.data_file_path = data_file_path

    def preprocess(self):
        """
        执行数据预处理。

        返回值:
            pyspark.sql.DataFrame: 预处理后的 DataFrame。
        """
        try:
            diabetes_df = self.spark.read.csv(
                self.data_file_path,
                header=True, inferSchema=True
            )
            diabetes_df = diabetes_df.filter(
                (col("Glucose") != 0)
                & (col("BloodPressure") != 0)
                & (col("BMI") != 0)
            )
            feature_cols = [
                "Pregnancies",
                "Glucose",
                "BloodPressure",
                "BMI",
                "DiabetesPedigreeFunction",
                "Age",
            ]

            assembler = VectorAssembler(
                inputCols=feature_cols,
                outputCol="features"
            )
            diabetes_df = assembler.transform(diabetes_df)

            scaler = StandardScaler(
                inputCol="features", 
                outputCol="scaled_features"
            )
            scaler_model = scaler.fit(diabetes_df)
            diabetes_df = scaler_model.transform(diabetes_df)
            
            return diabetes_df

        except Exception as e:
            logging.error(
                f"Error occurred during data "
                f"preprocessing: {str(e)}"
            )
            raise e

class DiabetesClassifierModel(nn.Module):
    """
    用于糖尿病分类的神经网络模型。
    """
```




## 代码实现

```python
def __init__(self, input_size, output_size):
    """
    初始化 DiabetesClassifierModel。

    参数:
        input_size (int): 输入大小。
        output_size (int): 输出大小。
    """
    super(DiabetesClassifierModel, self).__init__()
    self.model = nn.Sequential(
        nn.Linear(input_size, 64),
        nn.ReLU(),
        nn.Linear(64, 32),
        nn.ReLU(),
        nn.Linear(32, 16),
        nn.ReLU(),
        nn.Linear(16, output_size),
    )

def forward(self, x):
    """
    定义模型的前向传播。

    参数:
        x (torch.Tensor): 输入张量。

    返回:
        torch.Tensor: 输出张量。
    """
    return self.model(x)
```

```python
class ModelTrainer:
    """
    糖尿病分类器模型的训练器。
    """
    def __init__(
        self,
        model,
        criterion,
        optimizer,
        train_loader
    ):
        """
        初始化 ModelTrainer。

        参数:
            model (torch.nn.Module): 神经网络模型。
            criterion (torch.nn.Module): 损失函数。
            optimizer (torch.optim.Optimizer): 优化器。
            train_loader (torch.utils.data.DataLoader):
                训练数据加载器。
        """
        self.model = model
        self.criterion = criterion
        self.optimizer = optimizer
        self.train_loader = train_loader

    def train(self, epochs=100, lr=0.01):
        """
        训练模型。

        参数:
            epochs (int, 可选):
                训练轮数。默认为 100。
            lr (float, 可选):
                学习率。默认为 0.01。
        """
        try:
            for epoch in range(epochs):
                self.model.train()
                for inputs, targets in self.train_loader:
                    self.optimizer.zero_grad()
                    outputs = self.model(inputs)
                    loss = self.criterion(
                        outputs.squeeze(),
                        targets
                    )
                    loss.backward()
                    self.optimizer.step()
                if (epoch + 1) % 10 == 0:
                    logging.info(
                        f"Epoch [{epoch + 1}/{epochs}], Loss: {loss.item():.4f}"
                    )
        except Exception as e:
            logging.error(
                f"Error occurred during model training: {str(e)}"
            )
            raise e
```

```python
class ModelEvaluator:
    """
    糖尿病分类器模型的评估器。
    """
    def __init__(self, model, test_loader, y_test_np):
        """
        初始化 ModelEvaluator。

        参数:
            model (torch.nn.Module): 神经网络模型。
            test_loader (torch.utils.data.DataLoader):
                测试数据加载器。
            y_test_np (numpy.ndarray):
                测试数据的真实标签。
        """
        self.model = model
        self.test_loader = test_loader
        self.y_test_np = y_test_np

    def evaluate(self):
        """
        评估模型。
        """
        try:
            with torch.no_grad():
                self.model.eval()
                predictions = []
                probabilities = []
                for inputs, _ in self.test_loader:
                    outputs = self.model(inputs)
                    probabilities.extend(
                        torch.sigmoid(outputs).squeeze().tolist()
                    )
                    predictions.extend(
                        output.squeeze().tolist()
                    )
                y_pred = np.array(
                    [1 if pred > 0.5 else 0 for pred in probabilities]
                )
                accuracy = accuracy_score(
                    self.y_test_np,
                    y_pred
                )
                precision = precision_score(
                    self.y_test_np,
                    y_pred
                )
                recall = recall_score(self.y_test_np, y_pred)
                f1 = f1_score(self.y_test_np, y_pred)

                logging.info(f"Accuracy: {accuracy:.4f}")
                logging.info(f"Precision: {precision:.4f}")
                logging.info(f"Recall: {recall:.4f}")
                logging.info(f"F1 Score: {f1:.4f}")

                # 混淆矩阵
                conf_matrix = confusion_matrix(
                    self.y_test_np,
                    y_pred
                )
                logging.info(
                    "Confusion Matrix:\n" + str(conf_matrix)
                )

                # ROC-AUC 分数
                roc_auc = roc_auc_score(
                    self.y_test_np,
                    probabilities
                )
                logging.info(f"ROC-AUC Score: {roc_auc:.4f}")

                # 将指标以字典形式返回
                return {
                    'accuracy': accuracy,
                    'precision': precision,
                    'recall': recall,
                    'f1': f1,
                    'roc_auc': roc_auc
                }
        except Exception as e:
            logging.error(
                f"Error occurred during model evaluation: {str(e)}"
            )
            raise e
```

```python
def copy_file_from_s3(bucket_name, file_name, local_dir):
    """
    将文件从 S3 存储桶复制到本地目录。

    参数:
        bucket_name (str): S3 存储桶的名称。
        file_name (str): 要复制的文件名。
        local_dir (str):
            文件将被复制到的本地目录。
    """
    try:
        s3 = boto3.client("s3")
        s3.download_file(
            bucket_name,
            file_name,
            local_dir + file_name
        )
    except Exception as e:
        logging.error(
            f"Error occurred during file copying: {str(e)}"
        )
        raise e
```

```python
if __name__ == "__main__":
    logging.basicConfig(level=logging.INFO)

    spark = SparkSession.builder.appName("DiabetesClassifier").getOrCreate()

    # 从 S3 复制文件
    copy_file_from_s3(
        "instance1bucket",
        "diabetes.csv",
        "/home/ubuntu/airflow/dags/"
    )

    data_preprocessor = DataPreprocessor(
        spark, "/home/ubuntu/airflow/dags/diabetes.csv"
    )
    diabetes_df = data_preprocessor.preprocess()

    # 将 Spark DataFrame 转换为 numpy 数组
    X_np = np.array(
        diabetes_df.select("scaled_features").rdd.flatMap(lambda x: x).collect(),
        dtype=np.float32,
    )
    y_np = np.array(
        diabetes_df.select("Outcome").rdd.flatMap(lambda x: x).collect(),
        dtype=np.float32,
    )

    # 实现 K 折交叉验证
    k_folds = 5
    kfold = KFold(
        n_splits=k_folds,
        shuffle=True,
        random_state=42
    )

    fold_results = []
    for fold, (train_idx, test_idx) in enumerate(kfold.split(X_np)):
        logging.info(f"Training fold {fold + 1}/{k_folds}")

        X_train, X_test = X_np[train_idx], X_np[test_idx]
        y_train, y_test = y_np[train_idx], y_np[test_idx]

        # 转换为 PyTorch 数据集
        train_dataset = TensorDataset(
            torch.tensor(X_train),
            torch.tensor(y_train)
        )
        test_dataset = TensorDataset(
            torch.tensor(X_test),
            torch.tensor(y_test)
        )

        # 创建 DataLoader
        train_loader = DataLoader(
            train_dataset,
            batch_size=64,
            shuffle=True
        )
        test_loader = DataLoader(
            test_dataset,
            batch_size=64,
            shuffle=False
        )

        # 初始化模型、损失函数和优化器
        input_size = X_train.shape[1]
        output_size = 1
        model = DiabetesClassifierModel(input_size, output_size)
        criterion = nn.BCEWithLogitsLoss()
        optimizer = optim.Adam(model.parameters(), lr=0.01)

        # 训练模型
        model_trainer = ModelTrainer(
            model,
            criterion,
            optimizer,
            train_loader
        )
        model_trainer.train()

        # 评估模型
        model_evaluator = ModelEvaluator(
            model,
            test_loader,
            y_test
        )
        results = model_evaluator.evaluate()

        # 将结果添加到 fold_results 列表
        fold_results.append(results)

    # 聚合各折的结果
    avg_accuracy = np.mean(
        [result['accuracy'] for result in fold_results]
    )
    avg_precision = np.mean(
        [result['precision'] for result in fold_results]
    )
    avg_recall = np.mean(
        [result['recall'] for result in fold_results]
    )
    avg_f1 = np.mean(
        [result['f1'] for result in fold_results]
    )
    avg_roc_auc = np.mean(
        [result['roc_auc'] for result in fold_results]
    )

    logging.info(f"Average Accuracy: {avg_accuracy:.4f}")
    logging.info(f"Average Precision: {avg_precision:.4f}")
    logging.info(f"Average Recall: {avg_recall:.4f}")
    logging.info(f"Average F1 Score: {avg_f1:.4f}")
    logging.info(f"Average ROC-AUC Score: {avg_roc_auc:.4f}")
```

## 总结

在本章中，我们研究了深度学习中的一个重要任务：分类。我们构建、训练并评估了一个 PyTorch 多层算法，利用它根据各种属性（如怀孕次数、血糖水平、血压、体质指数 [BMI]、年龄和糖尿病家族史）来预测糖尿病诊断的概率。

我们使用 Spark 进行数据预处理，以突出其分布式计算能力，这对于管理大型数据集至关重要。尽管使用的是相对较小的数据集，但我们涵盖了机器学习中的一些基本主题，包括数据增强、迁移学习、数据质量和模型复杂度。此外，为了确保对模型性能进行更可靠的评估，我们实施了 K 折交叉验证，这使我们能够在多个数据子集上评估模型，从而降低了过拟合或欠拟合的风险。



我们的代码开发强调了关键的建模步骤，例如数据加载、预处理、定义模型架构、训练和评估。此外，我们还集成了额外功能，例如从 S3 存储桶复制数据到 EC2 本地目录进行处理，展示了与 AWS 服务的集成，并在整个建模过程中处理错误和日志消息以用于调试和监控。

在下一章中，我们将继续探讨深度学习分类的主题，这次使用 TensorFlow。我们将演示如何复制使用 PyTorch 时的相同步骤。

## 第 7 章
## 使用 TensorFlow 进行深度学习分类

在上一章中，我们构建、训练并评估了一个 PyTorch 多层深度学习模型，并使用它来预测糖尿病诊断的概率。我们的代码开发强调了关键的建模步骤，例如数据加载、预处理、定义模型架构、训练和评估。此外，我们还集成了额外功能，例如从 S3 存储桶复制数据到 EC2 本地目录进行处理，展示了与 AWS 服务的集成，并在整个建模过程中处理错误和日志消息以用于调试和监控。我们还利用 PySpark 进行数据处理，展示了其分布式计算能力。

在本章中，我们继续探讨深度学习分类的主题，这次使用 TensorFlow。我们演示了如何复制使用 PyTorch 时的相同步骤。为了能够对两个模型的性能进行公平的比较，我们使用与 PyTorch 相同的 Pima 糖尿病数据集。

此外，我们引入了使用 keras_tuner 进行超参数调整的方法，使我们能够自动化搜索最优的模型架构和学习率。这种方法通过潜在地产生比手动选择超参数更好的性能指标，从而增强我们的模型训练过程。

本章首先回顾了糖尿病数据集的情况。然后，它在 TensorFlow 中构建、训练并评估了一个多层深度学习分类模型，并将其性能与上一章中 PyTorch 的结果进行比较。在用固定超参数评估模型并将其性能与 PyTorch 进行比较后，我们继续对其进行微调，以进一步提升其性能。接下来，本章将整章中使用的代码整合到一个统一的章节中。最后，本章以对关键要点的总结作为结尾。

## 数据集

我们在上一章中非常详细地探讨了 Pima 糖尿病数据集。在本节中，我们编写代码将 CSV 文件从 S3 存储桶复制到 EC2 上的本地目录，然后打印前 10 条记录，以让我们回忆起特征和目标变量的样子：

```python
from pyspark.sql import SparkSession
import os

spark = SparkSession.builder \
     .appName("Read CSV from S3") \
     .getOrCreate()

bucket_name = "instance1bucket"
file_key = "diabetes.csv"
local_file_path = "/home/ubuntu/airflow/dags/diabetes.csv"

os.system(
    f"aws s3 cp s3://{bucket_name}/{file_key} "
    f"{local_file_path}"
)

df = spark.read.csv(
    local_file_path,
    header=True,
    inferSchema=True
)

selected_columns = [
    'Pregnancies',
    'Glucose',
    'BloodPressure',
    'BMI',
    'DiabetesPedigreeFunction',
    'Age',
    'Outcome'
]

df_selected = df.select(selected_columns)
df_selected.show(10)

spark.stop()
```

我们现在将逐步探索代码，首先导入必要的库：

- `from pyspark.sql import SparkSession`：这从 pyspark.sql 模块中导入 SparkSession 类。SparkSession 是使用 Dataset 和 DataFrame API 编程 Spark 的入口点。
- `import os`：这导入内置的 os 模块，该模块提供了一种可移植的方式来使用依赖于操作系统的功能。

然后，我们创建一个新的 SparkSession，指定的应用名称为“Read CSV from S3”，或者如果可用则检索现有的会话。appName 方法设置 Spark 应用的名称：

```python
spark = (SparkSession.builder
         .appName("Read CSV from S3")
         .getOrCreate())
```

我们使用括号 () 来促进多行代码的可读性。或者，可以选择在每行末尾使用反斜杠字符 \。

在下一步中，代码定义了 S3 存储桶和文件详情：

```python
bucket_name = "instance1bucket"
file_key = "diabetes.csv"
local_file_path = "/home/ubuntu/airflow/dags/diabetes.csv"
```

这些变量保存了 S3 存储桶名称、文件键（桶内文件的路径）以及文件将复制到的本地文件路径。

继续前进，代码使用 os.system 函数执行 shell 命令。它使用 AWS CLI 命令 aws s3 cp 将由 bucket_name 和 file_key 指定的 S3 存储桶中的文件 diabetes.csv 复制到由 local_file_path 指定的本地目录：

```python
os.system(
    f"aws s3 cp s3://{bucket_name}/{file_key} "
    f"{local_file_path}"
)
```

下一行使用 Spark 的 `read.csv` 方法将位于 `local_file_path` 的 CSV 文件读取到 DataFrame (df) 中。它指定 CSV 文件的第一行包含表头 (header=True)，并从数据中推断 DataFrame 的模式 (inferSchema=True)：

```python
df = spark.read.csv(
    local_file_path,
    header=True,
    inferSchema=True
)
```

然后，代码选择适当的列（回忆一下，上一章中我们排除了 `SkinThickness` 和 `Insulin`，因为它们有很多无效读数）：

```python
selected_columns = [
    'Pregnancies',
    'Glucose',
    'BloodPressure',
    'BMI',
    'DiabetesPedigreeFunction',
    'Age',
    'Outcome'
]
df_selected = df.select(selected_columns)
```

下一行使用 show() 方法显示 DataFrame df_selected 的前 10 条记录：

```python
df_selected.show(10)
```

最后，我们停止 SparkSession 以释放分配给它的资源。在完成 Spark 作业后停止 SparkSession 是一个良好的实践：

```python
spark.stop()
```

为了执行代码，我们将其保存为“print_top10_records.py”并在 JupyterLab 终端中运行它。在创建一个名为“myenv”的环境后，我们使用以下命令激活它：

```bash
source /home/ubuntu/myenv/bin/activate
```

一旦环境被激活，我们使用“spark-submit”执行以下命令来运行代码：

```bash
spark-submit print_top10_records.py
```

或者，我们可以使用 Python 3 解释器通过以下命令执行代码：

```bash
python3 print_top10_records.py
```

代码的输出是一个表格，显示了 Pima 糖尿病数据集的前 10 行：

| Pregnancies | Glucose | BloodPressure | BMI | DiabetesPedigreeFunction | Age | Outcome |
|---|---|---|---|---|---|---|
| 6 | 148 | 72 | 33.6 | 0.627 | 50 | 1 |
| 1 | 85 | 66 | 26.6 | 0.351 | 31 | 0 |
| 8 | 183 | 64 | 23.3 | 0.672 | 32 | 1 |
| 1 | 89 | 66 | 28.1 | 0.167 | 21 | 0 |
| 0 | 137 | 40 | 43.1 | 2.288 | 33 | 1 |
| 5 | 116 | 74 | 25.6 | 0.201 | 30 | 0 |
| 3 | 78 | 50 | 31.0 | 0.248 | 26 | 1 |
| 10 | 115 | 0 | 35.3 | 0.134 | 29 | 0 |
| 2 | 197 | 70 | 30.5 | 0.158 | 53 | 1 |
| 8 | 125 | 96 | 0.0 | 0.232 | 54 | 1 |

以下是表格中每一列的说明：

- **Pregnancies**：怀孕次数。
- **Glucose**：口服葡萄糖耐量试验 2 小时后的血浆葡萄糖浓度。
- **BloodPressure**：舒张压（mm Hg）。
- **BMI (Body Mass Index)**：身体质量指数，这是基于身高和体重的体脂测量指标。
- **DiabetesPedigreeFunction**：根据家族史对患糖尿病可能性进行评分的函数。
- **Age**：个人的年龄（以年为单位）。




- 结果变量：这是目标变量，指示个体是否患有糖尿病。1 表示该人患有糖尿病，0 表示该人未患糖尿病。

请注意，血压（BloodPressure）和体重指数（BMI）中存在值为 0 的行，这表明读数无效。这些行将在模型训练和评估期间从数据集中排除。

## 使用 TensorFlow 预测糖尿病

在本节中，我们将利用上一节描述的糖尿病数据集，训练并评估一个 TensorFlow 深度学习模型，以预测皮马印第安女性患糖尿病的可能性。建模步骤大体上沿袭了前一章的方法，在该章中我们使用 PyTorch 开发了类似的分类模型。与前一章一样，我们利用 PySpark 进行数据预处理。

代码将对应以下建模步骤：

- 第 1 步：导入
  - 导入必要的库和模块，如 logging、PySpark、TensorFlow 和 Scikit-Learn
- 第 2 步：日志配置
  - 配置日志设置，如日志级别，并创建一个日志记录器对象
- 第 3 步：自定义回调
  - 实现一个自定义的 Keras 回调，以便在模型训练期间打印 Epoch 信息
- 第 4 步：数据预处理
  - 使用 PySpark 对糖尿病数据进行预处理，包括读取数据、过滤、特征工程、缩放以及分割为训练集和测试集等任务
- 第 5 步：模型定义与训练
  - 定义 TensorFlow (Keras) 顺序模型的架构，并使用预处理后的数据训练模型
- 第 6 步：模型评估
  - 使用测试数据评估训练好的 TensorFlow (Keras) 模型，并计算评估指标，如准确率、精确率、召回率和 F1 分数
- 第 7 步：主程序
  - 定义 `if __name__ == "__main__":` 块，作为脚本的主入口点，在此编排数据预处理、模型训练和评估

尽管这些步骤与 PyTorch 大体相似，但读者会注意到，与 PyTorch 相比，Keras 通常提供更高阶的接口，这可能导致某些任务的代码更简短。Keras 抽象了许多实现细节，并为构建和训练神经网络提供了更直观、更易用的 API。

例如，用于定义模型架构和训练模型的 TensorFlow (Keras) 代码简洁明了，因为 Keras 提供了预构建的层和模块，使得只需几行代码即可轻松定义神经网络架构。另一方面，PyTorch 设计得更为灵活和可定制，这可能导致代码片段较长，尤其是在定义复杂模型或实现自定义训练循环时。PyTorch 提供了一个低阶 API，赋予用户对模型行为和训练过程更大的控制权。

在模型训练方面，Keras 提供了高阶方法 `model.fit()`，它自动化了训练过程的许多部分。该方法抽象了诸如遍历 Epoch 和批次、计算损失以及执行优化步骤等细节。这使得用极少的样板代码训练模型变得非常容易，特别有利于快速原型开发和实验。

相比之下，PyTorch 要求用户手动实现训练循环，显式地遍历 Epoch 和批次，计算损失并执行优化步骤。虽然这种方法可能更冗长，但它为训练过程提供了更大的灵活性和控制力，允许实现自定义训练过程并尝试不同的优化技术。

对于模型评估，Keras 提供了一个方便的内置方法 `model.evaluate()` 用于评估模型性能。该方法计算准确率、损失以及在模型编译时指定的任何其他评估指标。这种简化的方法简化了评估过程，使直接从模型获取性能指标变得容易。

在 PyTorch 中，模型评估通常涉及使用外部库（如 Scikit-Learn）或实现自定义评估函数来手动计算评估指标。虽然 PyTorch 没有与 `model.evaluate()` 直接等效的功能，但它提供了根据具体需求定制评估过程的灵活性，允许对评估指标和过程进行更精细的控制。

现在，让我们逐步深入 TensorFlow 代码，从导入开始：

### 第 1 步：导入

```python
import logging
from pyspark.sql import SparkSession
from pyspark.ml.feature import VectorAssembler, StandardScaler
from pyspark.sql.functions import col
from sklearn.metrics import (
    accuracy_score,
    precision_score,
    recall_score,
    f1_score
)
from tensorflow.keras.models import Sequential
from tensorflow.keras.layers import Dense, ReLU
from tensorflow.keras.optimizers import SGD
from tensorflow.keras.callbacks import Callback
import numpy as np
```

以下是这些导入的含义及其在即将出现的代码中用途的说明：

- `import logging`：用于设置日志配置并在脚本中记录日志消息。它将在即将出现的代码中的 `DiabetesProcessor` 和 `DiabetesModelTrainer` 类中用于记录数据预处理和模型训练的相关信息。它还将用于 `CustomCallback` 类中，以便在模型训练期间记录 Epoch 信息。
- `from pyspark.sql import SparkSession`：用于创建 `SparkSession`，这对于与 Spark 交互以及执行 DataFrame 操作至关重要。它在主脚本中用于创建 `SparkSession` 以进行数据预处理和模型训练。
- `from pyspark.ml.feature import VectorAssembler, StandardScaler`：这些是 PySpark 数据预处理过程中组装特征向量和缩放特征所需的类。它们在 `DiabetesProcessor` 类中用于在训练模型之前组装特征向量并缩放特征。
- `from pyspark.sql.functions import col`：用于在数据过滤和操作期间按名称访问 DataFrame 列。它在 `DiabetesProcessor` 类中用于过滤出某些列为零的行。
- `from sklearn.metrics import accuracy_score, precision_score, recall_score, f1_score`：这些导入用于计算训练好的模型在测试数据上的评估指标，如准确率、精确率、召回率和 F1 分数。它们在 `DiabetesModelEvaluator` 类中用于计算训练好的 TensorFlow (Keras) 模型的评估指标。
- `from tensorflow.keras.models import Sequential`：用于在 TensorFlow (Keras) 中定义 `Sequential` 模型架构以训练神经网络。它在 `DiabetesModelTrainer` 类中用于定义神经网络模型的架构。
- `from tensorflow.keras.layers import Dense, ReLU`：这些用于指定神经网络架构中的全连接（`Dense`）层和激活函数（`ReLU`）。它们在 `DiabetesModelTrainer` 类中用于指定神经网络模型的层。
- `from tensorflow.keras.optimizers import SGD`：用于在编译 Keras 模型时指定随机梯度下降（SGD）优化器。它在 `DiabetesModelTrainer` 类的代码中用于指定训练神经网络模型的优化器。
- `from tensorflow.keras.callbacks import Callback`：用于定义自定义 Keras 回调（`CustomCallback`），以便在模型训练期间记录 Epoch 信息。它在 `DiabetesModelTrainer` 类中使用。
- `import numpy as np`：以别名 `np` 导入 NumPy 库。NumPy 是 Python 科学计算的基础包，提供对多维数组和数学函数的支持。它将在代码中用于将 PySpark DataFrame 列转换为 NumPy 数组，以便进行模型训练和评估。

### 第 2 步：日志配置

下面两行代码在 Python 中设置日志配置并创建一个日志记录器对象：

```python
logging.basicConfig(level=logging.INFO)
logger = logging.getLogger(__name__)
```





第一行 `logging.basicConfig(level=logging.INFO)` 初始化了日志系统，并配置为记录 INFO 级别或更高优先级的消息。这意味着只有 INFO、WARNING、ERROR 或 CRITICAL 级别的消息会被记录，而 DEBUG 级别的消息将被忽略。`basicConfig()` 函数允许我们配置根记录器（root logger），它是 Python 日志模块使用的主记录器。

第二行 `logger = logging.getLogger(__name__)` 创建了一个名为 `logger` 的记录器对象。`getLogger()` 函数用于获取记录器实例，而 `__name__` 是 Python 中的一个特殊变量，代表当前模块的名称。通过使用 `__name__`，记录器的名称将与定义它的当前模块名称保持一致。这有助于识别日志消息的来源，因为记录器名称将与模块名称对应。

## 步骤 3：自定义回调

以下代码在 Python 中定义了一个名为 `CustomCallback` 的自定义 Keras 回调：

```python
class CustomCallback(Callback):
    """Custom Keras callback for printing epoch information."""
    def on_epoch_end(self, epoch, logs=None):
        """Prints epoch information every 10 epochs."""
        if (epoch + 1) % 10 == 0:
            logger.info(
                f"Epoch [{(epoch + 1)}/{self.params['epochs']}], "
                f"Loss: {logs['loss']:.4f}"
            )
```

`CustomCallback` 类继承自 Keras 库提供的 `Callback` 类，允许在神经网模型训练期间执行自定义操作：

- 文档字符串 `"""Custom Keras callback for printing epoch information."""` 提供了对该回调用途的简要说明。
- 在类内部，有一个方法 `on_epoch_end(self, epoch, logs=None)`，它在模型训练过程中每个 epoch 结束时由 Keras 调用。该方法每十个 epoch 打印一次 epoch 信息。
- 在 `on_epoch_end` 方法内部，有一个条件语句用于检查当前 epoch 编号加一是否能被 10 整除。如果可以，则使用 `logger.info()` 函数记录当前 epoch 的信息。记录的信息包括 epoch 编号、总 epoch 数以及日志字典中的损失值。

## 步骤 4：数据预处理

在此步骤中，我们在将数据输入算法之前对 Pima 糖尿病数据进行预处理。以下代码定义了一个名为 `DiabetesProcessor` 的 Python 类，负责使用 PySpark 预处理这些数据：

```python
class DiabetesProcessor:
    """Class for preprocessing diabetes data."""
    @staticmethod
    def preprocess_data(spark, data_file_path, train_parquet_path, test_parquet_path):
        """Preprocesses the diabetes data using PySpark."""
        try:
            diabetes_df = spark.read.csv(
                data_file_path,
                header=True,
                inferSchema=True
            )
            diabetes_df = diabetes_df.filter(
                (col("Glucose") != 0) &
                (col("BloodPressure") != 0) &
                (col("BMI") != 0)
            )
            feature_cols = [
                "Pregnancies",
                "Glucose",
                "BloodPressure",
                "BMI",
                "DiabetesPedigreeFunction",
                "Age"
            ]
            assembler = VectorAssembler(
                inputCols=feature_cols,
                outputCol="features"
            )
            diabetes_df = assembler.transform(diabetes_df)
            scaler = StandardScaler(
                inputCol="features",
                outputCol="scaled_features"
            )
            scaler_model = scaler.fit(diabetes_df)
            diabetes_df = scaler_model.transform(diabetes_df)

            train_df, test_df = diabetes_df.randomSplit(
                [0.8, 0.2],
                seed=42
            )
            train_df.write.parquet(
                train_parquet_path,
                mode="overwrite"
            )
            test_df.write.parquet(
                test_parquet_path,
                mode="overwrite"
            )
            logger.info("Data preprocessing completed.")
        except Exception as e:
            logger.error(
                f"Error occurred during data preprocessing: {str(e)}"
            )
```

以下是有关 `DiabetesProcessor` 类及其内部 `preprocess_data` 方法的更多详细信息：

- 文档字符串 `"""Class for preprocessing diabetes data."""` 提供了对该类用途的简要说明。
- 在类内部，有一个静态方法 `preprocess_data(spark, data_file_path, train_parquet_path, test_parquet_path)`，用于执行实际的数据预处理。该方法接受四个参数：`spark`（SparkSession 对象）、`data_file_path`（糖尿病数据文件的路径）、`train_parquet_path`（保存预处理后的训练数据的路径）以及 `test_parquet_path`（保存预处理后的测试数据的路径）。`@staticmethod` 装饰器用于将此方法声明为静态方法，表明它不需要访问实例或其属性，可以直接在类上调用，而无需创建 `DiabetesProcessor` 的实例。
- 在该方法中，使用 Spark 的 `read.csv()` 方法从 CSV 文件读取糖尿病数据。随后，过滤掉葡萄糖（Glucose）、血压（BloodPressure）和 BMI 列值为零的行，以表示无效读数。
- 接下来进行特征工程，其中选定的特征列（包括 "Pregnancies"、"Glucose"、"BloodPressure"、"BMI"、"DiabetesPedigreeFunction" 和 "Age"）使用 `VectorAssembler` 组装成一个单一的特征向量。此向量化过程为进一步的分析准备了数据。`VectorAssembler` 的 `inputCols` 参数指定要组装的列，而 `outputCol` 参数指定包含组装后的特征向量的输出列名称。
- 然后使用 `StandardScaler` 对组装好的特征向量进行缩放。`inputCol` 参数指定包含待缩放特征向量的列，而 `outputCol` 参数指定包含缩放后特征向量的输出列名称。
- 在 `VectorAssembler` 和 `StandardScaler` 对象上调用 `transform` 函数，以将转换应用于糖尿病数据 DataFrame。该函数将 `VectorAssembler` 和 `StandardScaler` 定义的转换应用于输入 DataFrame，并返回一个包含转换后特征的新 DataFrame。
- 然后使用 PySpark 的 `randomSplit()` 方法将预处理后的数据划分为训练集和测试集。这确保模型在数据的一部分（在本例中为 80%）上进行训练，并在另一部分（20%）上进行评估，从而促进无偏的模型评估。
- 最后，将预处理后的数据写入 Parquet 文件以供后续使用。在 PySpark 中将数据保存为 Parquet 格式具有多种优势，包括高效的存储、列式存储格式、内置压缩以及与大数据处理框架的兼容性。
- 使用 `try-except` 块实现了错误处理，以捕获预处理过程中可能发生的任何异常。如果发生异常，则使用 `logger.error()` 记录错误消息。这确保了在数据预处理过程中遇到的任何问题都得到妥善处理并记录，以便用于调试。

> **注意** 将数据保存到 Parquet 格式是在大数据环境中处理大型数据集的广泛采用方法。Parquet 的列式存储格式按列而非行存储数据，使其对针对特定列的查询具有极高的效率，从而减少磁盘读取并加快查询速度。它还提供了比 CSV 或 JSON 等格式更好的压缩率，导致文件更小，I/O 操作更快——这对于大规模数据处理至关重要。

Parquet 支持架构演进，允许在不重写整个数据集的情况下添加或删除列，这在动态生产环境中极其宝贵。它与 Apache Spark、Hadoop 和 AWS Glue 等大数据框架的兼容性确保了跨分布式系统的高效处理。Parquet 的列式特性，结合谓词下推（predicate pushdown）等功能——即在数据读取阶段尽可能早地进行过滤，以最小化需要处理的数据量——通过跳过无关的数据块来优化数据扫描，进一步提升性能。此外，Parquet 对复杂数据类型（如嵌套结构、数组和映射）的支持，增加了存储和查询复杂数据模型的灵活性。

虽然 Parquet 在存储和查询大型数据集方面表现出色，但值得注意的是，诸如 AWS Glue 和 Spark SQL 等替代方法可以进一步增强数据管理和处理。尽管这些工具超出了本书的范围，但 AWS Glue 自动发现、编录和转换数据的能力，以及 Spark SQL 在 Spark 应用程序内部直接执行复杂转换和查询的能力，都是值得考虑的强力选项。

## 步骤 5：模型定义与训练

本步骤中的代码定义了用于训练 TensorFlow (Keras) 模型的 `DiabetesModelTrainer` 类：

```python
class DiabetesModelTrainer:
    """Class for training the TensorFlow (Keras) model."""

    @staticmethod
    def train_tensorflow_model(
        X_train,
    ...
```





## 代码实现

```python
y_train,
epochs=100,
lr=0.01
):
    """Trains the TensorFlow (Keras) model."""
    try:
        model = Sequential([
            Dense(64, input_dim=X_train.shape[1]),
            ReLU(),
            Dense(32),
            ReLU(),
            Dense(16),
            ReLU(),
            Dense(1, activation='sigmoid')
        ])
        optimizer = SGD(learning_rate=lr)
        model.compile(loss='binary_crossentropy',
                      optimizer=optimizer,
                      metrics=['accuracy'])
        custom_callback = CustomCallback()
        model.fit(
            X_train,
            y_train,
            epochs=epochs,
            verbose=0,
            callbacks=[custom_callback]
        )
        logger.info("Model training completed.")
        return model
    except Exception as e:
        logger.error(
            f"Error occured during "
            f"model training: {str(e)}"
        )
```

在这段代码中：

- 文档字符串 `"""Class for training the TensorFlow (Keras) model."""` 简要说明了该类的用途。
- 在该类内部，有一个静态方法 `train_tensorflow_model(X_train, y_train, epochs=100, lr=0.01)`，负责训练 TensorFlow (Keras) 模型。该方法接受四个参数：`X_train`（用于训练的输入特征）、`y_train`（用于训练的目标标签）、`epochs`（训练的轮数，默认值为 100）以及 `lr`（优化器的学习率，默认值为 0.01）。使用 `@staticmethod` 装饰器将该方法声明为静态方法，表明它不需要访问实例或其属性，可以直接在类上调用，而无需创建 `DiabetesModelTrainer` 的实例。
- 在方法内部，使用 Keras 的 Sequential API 定义了一个神经网络模型。该模型由几个全连接（Dense）层组成，这些层使用整流线性单元（ReLU）激活函数，最后以一个使用 sigmoid 激活函数的输出层结尾。
- 配置了一个优化器（具有指定学习率的随机梯度下降），并使用二元交叉熵损失函数和准确率作为评估指标来编译模型。
- 实例化了一个自定义回调（`CustomCallback`），以便在模型训练期间记录信息。
- 对模型对象调用 fit 方法，使用输入特征（`X_train`）和目标标签（`y_train`）训练指定轮数的模型。将 `custom_callback` 传递给 `callbacks` 参数，以启用训练过程中轮次信息的记录。
- 模型训练成功完成后，会生成一条日志消息，表明模型训练已完成，并返回训练好的模型。
- 使用 try-except 块实现错误处理，以捕获模型训练过程中可能发生的任何异常。如果发生异常，则使用 `logger.error()` 记录错误消息。这确保了在模型训练过程中遇到的任何问题都能得到适当处理并记录在案，以便用于调试。

## 步骤 6：模型评估

在此步骤中，我们定义 `DiabetesModelEvaluator` 类，它负责评估用于糖尿病预测训练的 TensorFlow (Keras) 模型。它包含使用各种评估指标（如准确率、精确率、召回率和 F1 分数）来评估模型性能的方法：

```python
class DiabetesModelEvaluator:
    """Class for evaluating the TensorFlow (Keras)
    model."""
    @staticmethod
    def evaluate_model(model, X_test, y_test):
        """Evaluates the TensorFlow (Keras) model."""
        try:
            y_pred = (model.predict(X_test) > 0.5).astype(int)
            accuracy = accuracy_score(y_test, y_pred)
            precision = precision_score(y_test, y_pred)
            recall = recall_score(y_test, y_pred)
            f1 = f1_score(y_test, y_pred)
            logger.info(f"Accuracy: {accuracy:.4f}")
            logger.info(f"Precision: {precision:.4f}")
            logger.info(f"Recall: {recall:.4f}")
            logger.info(f"F1 Score: {f1:.4f}")
        except Exception as e:
            logger.error(
                f"Error occurred during model "
                f"evaluation: {str(e)}"
            )
```

让我们更仔细地看看这段代码：

- 文档字符串 `"""Class for evaluating the TensorFlow (Keras) model."""` 简要说明了该类的用途。
- 在该类内部，有一个静态方法 `evaluate_model(model, X_test, y_test)`，用于评估 TensorFlow (Keras) 模型的性能。该方法接受三个参数：`model`（训练好的 Keras 模型）、`X_test`（用于测试的输入特征）和 `y_test`（用于测试的真实标签）。使用 `@staticmethod` 装饰器将该方法声明为静态方法，表明它不需要访问实例或其属性，可以直接在类上调用，而无需创建 `DiabetesModelEvaluator` 的实例。
- 在方法内部，使用训练好的模型（`model.predict(X_test)`）生成预测值，并通过阈值处理获得二分类预测。使用 Scikit-Learn 的指标函数（分别为 `accuracy_score`、`precision_score`、`recall_score` 和 `f1_score`）计算准确率、精确率、召回率和 F1 分数等多个评估指标。
- 使用 `logger` 在信息级别记录包括准确率、精确率、召回率和 F1 分数在内的评估结果，以提供模型性能的见解。
- 使用 try–except 块实现错误处理，以捕获评估过程中可能发生的任何异常。如果发生异常，则使用 `logger.error()` 记录错误消息。这确保了在模型评估过程中遇到的任何问题都能得到适当处理并记录在案，以便用于调试。

## 步骤 7：主函数

在此最终步骤中，我们定义主函数，确保以下代码仅在脚本直接运行时执行，而在作为模块导入到其他脚本时不执行：

```python
if __name__ == "__main__":

    try:
        spark = (SparkSession.builder
                 .appName("DiabetesClassification")
                 .config("spark.executor.instances", "4")
                 .config("spark.executor.memory", "4g")
                 .config("spark.executor.cores", "2")
                 .config("spark.driver.memory", "2g")
                 .getOrCreate())
        
        data_file_path = "/home/ubuntu/airflow/dags/diabetes.csv"
        
        train_parquet_path = \
            "/home/ubuntu/airflow/dags/diabetes_train.parquet"
        
        test_parquet_path = \
            "/home/ubuntu/airflow/dags/diabetes_test.parquet"
        
        DiabetesProcessor.preprocess_data(
            spark,
            data_file_path,
            train_parquet_path,
            test_parquet_path
        )
        
        train_diabetes_df = spark.read.parquet(train_parquet_path)
        
        X_train = np.array(train_diabetes_df.select("scaled_features").rdd.flatMap(lambda x: x).collect())
        y_train = np.array(train_diabetes_df.select("Outcome").rdd.flatMap(lambda x: x).collect())

        trained_model = DiabetesModelTrainer.train_tensorflow_model(X_train, y_train)

        test_diabetes_df = spark.read.parquet(test_parquet_path)
        X_test = np.array(test_diabetes_df.select("scaled_features").rdd.flatMap(lambda x: x).collect())
        y_test = np.array(test_diabetes_df.select("Outcome").rdd.flatMap(lambda x: x).collect())

        DiabetesModelEvaluator.evaluate_model(trained_model, X_test, y_test)

    except Exception as e:
        logger.error(f"An error occurred: {str(e)}")
```

以下是此代码的说明：

- `if __name__ == "__main__":` 块是 Python 脚本的入口点。它确保以下代码仅在脚本直接运行时执行，而在作为模块导入到其他脚本时不执行。
- 在 try 块内部，执行若干步骤以预处理糖尿病数据、训练 TensorFlow (Keras) 模型并评估其性能。这些步骤被包裹在 try–except 块中，以处理任何潜在的异常。
- 首先，使用 `SparkSession.builder` API 创建一个 SparkSession。SparkSession 是 Spark 功能的入口点，允许脚本与 Spark 交互并执行分布式数据处理。
- SparkSession 配置了各种属性，如应用程序名称（`appName`）、执行器实例数量（`spark.executor.instances`）、执行器内存（`spark.executor.memory`）、执行器核心数（`spark.executor.cores`）和驱动器内存（`spark.driver.memory`）。这些配置可优化数据处理任务的资源分配。
- 定义了输入糖尿病数据文件（`data_file_path`）、预处理训练数据 Parquet 文件（`train_parquet_path`）和预处理测试数据 Parquet 文件（`test_parquet_path`）的路径。
- 调用 `DiabetesProcessor.preprocess_data()` 方法，使用 PySpark 预处理糖尿病数据。该方法从 CSV 文件中读取原始糖尿病数据，并应用数据清洗和特征工程



转换，并将预处理后的数据写入 Parquet 文件，以实现高效存储和检索。

-   随后，从 Parquet 文件加载预处理后的训练数据到 Spark DataFrame（train diabetes df）中，并从该 DataFrame 中提取输入特征（X_train）和目标标签（y_train）。这些特征和标签被转换为 NumPy 数组，用于训练 TensorFlow (Keras) 模型。
-   调用 `DiabetesModelTrainer.train_tensorflow_model()` 方法，使用预处理后的训练数据来训练 TensorFlow (Keras) 模型。该方法利用 Keras 提供的 Sequential API 构建、编译并训练神经网络模型。
-   模型训练完成后，从 Parquet 文件加载预处理后的测试数据到 Spark DataFrame（test diabetes df）中，并从该 DataFrame 中提取输入特征（X_test）和目标标签（y_test）。同样地，这些特征和标签被转换为 NumPy 数组，用于模型评估。
-   最后，调用 `DiabetesModelEvaluator.evaluate_model()` 方法，使用测试数据评估训练好的 TensorFlow (Keras) 模型的性能。该方法计算评估指标，如准确率、精确率、召回率和 F1 分数，并使用 logger 记录结果。
-   如果在 try 块的执行过程中发生任何异常，它们将被捕获并使用 `logger.error()` 进行记录。这确保了在数据预处理、模型训练或评估过程中遇到的任何错误或问题都能得到适当处理和记录，以便用于调试。

为了运行代码，我们将其保存为 “diabetes_classification_tensorflow.py”，并在 JupyterLab 终端中执行。在创建名为 “myenv” 的环境后，我们通过以下命令激活它：

```
[In]: source /home/ubuntu/myenv/bin/activate
```

激活环境后，我们使用 Python 3 通过以下命令执行代码：

```
[In]: python3 diabetes_classification_tensorflow.py
```

代码的第一个输出是下方的 Epoch 和 Loss 表格。这展示了在 TensorFlow (Keras) 模型训练过程中，每第十个 Epoch 的损失值：

| Epoch | Loss |
| :--- | :--- |
| 10/100 | 0.6353 |
| 20/100 | 0.5995 |
| 30/100 | 0.5723 |
| 40/100 | 0.5581 |
| 50/100 | 0.5513 |
| 60/100 | 0.5472 |
| 70/100 | 0.5316 |
| 80/100 | 0.5275 |
| 90/100 | 0.5181 |
| 100/100 | 0.5123 |

在此表中：

-   Epoch 编号表示在指定的总 Epoch 数中，训练过程当前的迭代次数。
-   损失值代表预测结果与实际结果之间的误差或差异。它是衡量模型性能好坏的一个指标，数值越低表示性能越好。

第二个输出是指标表格。该表格展示了在测试集上对训练好的 TensorFlow (Keras) 模型进行测试后计算出的各种评估指标：

| Metric | Value |
| :--- | :--- |
| Accuracy | 0.7692 |
| Precision | 0.7059 |
| Recall | 0.5854 |
| F1 Score | 0.6400 |

表格中指标的定义如下：

-   准确率（Accuracy）：准确率指标衡量模型所作所有预测中正确预测的比例。
-   精确率（Precision）：精确率表示模型所做所有阳性预测中真实阳性预测的比例。它衡量了模型避免假阳性预测的能力。
-   召回率（Recall）：召回率，也称为敏感度或真阳性率，衡量模型在数据集中所有实际阳性实例中正确识别出的真实阳性预测的比例。
-   F1 分数（F1 Score）：F1 分数是精确率和召回率的加权平均值。它在精确率和召回率之间取得平衡，提供一个单一指标来评估模型的性能。

根据 Epoch/Loss 表格和指标表格，我们可以得出关于 TensorFlow (Keras) 模型性能的几项结论：

**Epoch/Loss 表格：**

-   随着 Epoch 数的增加，损失值持续下降。这表明模型正在学习并随着 Epoch 的推进而提升性能。
-   损失值随 Epoch 减少的趋势表明模型正在有效地最小化误差，从而提高预测的准确性。

**指标表格：**

-   准确率指标提供了模型在预测阳性和阴性实例时正确性的总体衡量。0.77 的准确率表明模型在测试数据集上正确预测了大约 77% 的结果。
-   精确率、召回率和 F1 分数提供了关于模型在预测阳性结果（即糖尿病病例）方面表现的见解。
-   0.71 的精确率表明，大约 71% 的预测阳性结果是正确的，从而最小化了假阳性预测。
-   0.59 的召回率表明，模型正确识别了大约 59% 的实际阳性实例，从而最小化了假阴性预测。
-   0.64 的 F1 分数（精确率和召回率的加权平均值）在精确率和召回率之间取得了平衡。这表明模型在最小化假阳性和假阴性之间达到了合理的平衡。

总体而言，考虑到前一章中讨论的已知问题（如类别不平衡、特征偏斜以及 Pima 数据集中潜在的数据质量问题），模型的性能是合理的。改进的关键领域包括处理数据异常、通过重采样平衡类别分布、通过数据增强多样化数据集，以及考虑迁移学习以利用预训练模型。平衡模型复杂度、优化数据表示以及微调超参数对于提升性能也至关重要，特别是对于 Pima 这样的小型数据集。

## TensorFlow 与 PyTorch

基于前一章中我们使用 PyTorch 的结果以及本章中采用 TensorFlow 的情况，我们现在可以开展这两个模型性能的比较分析。由于我们使用了相同的 Pima 糖尿病数据集，这允许进行一对一的公平比较。通过考察训练损失、精确率、召回率和 F1 分数，我们可以获得关于这两种算法在识别糖尿病病例方面预测能力的见解。这样的比较对于指导框架选择和模型在实际生产环境中的部署决策具有不可估量的价值。

首先从损失值比较开始，下表比较了训练期间生成的两个模型的损失值：

| Epoch | TensorFlow | PyTorch |
| :--- | :--- | :--- |
| 10/100 | 0.6353 | 0.5899 |
| 20/100 | 0.5995 | 0.4330 |
| 30/100 | 0.5723 | 0.4608 |
| 40/100 | 0.5581 | 0.4612 |
| 50/100 | 0.5513 | 0.5155 |
| 60/100 | 0.5472 | 0.4025 |
| 70/100 | 0.5316 | 0.3406 |
| 80/100 | 0.5275 | 0.4323 |
| 90/100 | 0.5181 | 0.4822 |
| 100/100 | 0.5123 | 0.3203 |

基于上表中的数据，我们可以观察到以下几点：

-   TensorFlow 在训练过程中表现出损失值的持续下降，表明其优化和学习过程有效。另一方面，PyTorch 的损失值出现波动，暗示其优化动态或学习行为可能存在潜在变化。
-   TensorFlow 和 PyTorch 模型的损失值在每个 Epoch 中都有所不同，表明模型在收敛行为上可能存在差异。TensorFlow 和 PyTorch 模型的损失值模式并未遵循相同的趋势，这表明两个框架在优化或学习动态方面存在差异。

接着进行评估指标比较，下表比较了在测试数据上生成的准确率、精确率、召回率和 F1 分数：

| Metric | TensorFlow | PyTorch |
| :--- | :--- | :--- |
| Accuracy | 0.7692 | 0.7607 |
| Precision | 0.7059 | 0.6585 |
| Recall | 0.5854 | 0.6585 |
| F1 Score | 0.6400 | 0.6585 |

基于这些数据，我们可以作出以下评论：

-   准确率：PyTorch 模型的准确率（0.76）略低于 TensorFlow 模型的准确率（0.77）。两个模型都表现出较高的准确率，表明它们在测试数据集上进行正确预测时都较为有效。准确率的细微差异可能归因于模型优化或数据处理方面的变化。
-   精确率：PyTorch 模型的精确率（0.66）低于 TensorFlow 模型的精确率（0.71）。这表明 TensorFlow 模型的假阳性率较低，因此在识别真实阳性实例方面略好一些。





- **召回率**：PyTorch 模型的召回率 (0.66) 高于 TensorFlow 模型 (0.59)。这表明 PyTorch 模型能捕获更大比例的实际正例，对于需要尽可能识别出更多正例的任务可能更有利。

- **F1 分数**：PyTorch 模型的 F1 分数 (0.66) 略高于 TensorFlow 模型 (0.64)。F1 分数平衡了精确率和召回率，表明 PyTorch 模型在精确率和召回率之间提供了略好的整体平衡。

总体而言，TensorFlow 和 PyTorch 模型在准确率、精确率、召回率和 F1 分数方面都表现出可比的性能。尽管模型之间存在细微差异，但这些差异属于误差范围内，或者可能源于优化策略或随机初始化的变化。尽管性能很高，但仍存在改进空间。提高数据质量、采用重采样和数据增强技术、探索迁移学习、调整模型复杂度、改善数据表示以及微调超参数，都可以进一步优化模型性能。

## 通过超参数调优优化模型性能

目前获得的结果来自使用固定超参数的模型。考虑到输入样本较小，这些结果是合理的。TensorFlow 提供了一个强大的工具来改进模型性能：超参数调优。通过利用 `keras_tuner`，我们可以系统地搜索最佳的超参数组合，将模型优化到超越手动选择所能达到的水平。

为了增强我们的模型，我们将使用 `keras_tuner` 的超参数调优过程替换固定的超参数。这种方法允许我们探索更广泛的模型配置，并找出表现最好的那一个。

### 步骤 1：必要的导入

在进行超参数调优之前，我们需要确保已导入必要的模块。来自 `keras_tuner` 的 `HyperModel` 类将帮助我们定义具有可调整超参数的模型架构，而 `RandomSearch` 将促进寻找这些超参数的最佳组合：

```python
[In]: from keras_tuner import HyperModel, RandomSearch
```

### 步骤 2：定义 DiabetesHyperModel 类

接下来，我们创建 `DiabetesHyperModel` 类，该类扩展了来自 `keras_tuner` 的 `HyperModel` 类。这个类允许我们定义模型架构，特别是指定哪些参数是可调整的。在此情况下，我们指定每个全连接层（dense layer）的单元数量和学习率是要调整的超参数。

在 `build` 方法中，我们定义了一个包含三个全连接层的基本顺序模型。对于每个全连接层，单元数量由 `hp.Int` 决定，它允许 `keras_tuner` 在指定范围内探索不同的值。同样，学习率使用 `hp.Float` 设置，提供调优器可探索的范围。模型使用标准的二元交叉熵损失函数和准确率作为指标进行编译：

```python
[In]: class DiabetesHyperModel(HyperModel):
    """用于调优 Keras 模型的 HyperModel。"""

    def build(self, hp):
        model = Sequential()
        model.add(
            Dense(
                units=hp.Int('units_1',
                             min_value=32,
                             max_value=128,
                             step=32
                             ),
                input_dim=X_train.shape[1]
            )
        )
        model.add(ReLU())
        model.add(
            Dense(
                units=hp.Int(
                    'units_2',
                    min_value=16,
                    max_value=64,
                    step=16
                )
            )
        )
        model.add(ReLU())
        model.add(
            Dense(
                units=hp.Int(
                    'units_3',
                    min_value=8,
                    max_value=32,
                    step=8
                )
            )
        )
        model.add(ReLU())
        model.add(Dense(1, activation='sigmoid'))
        
        optimizer = SGD(
            learning_rate=hp.Float(
                'lr',
                1e-4,
                1e-2,
                sampling='log'
            )
        )
        model.compile(loss='binary_crossentropy',
                      optimizer=optimizer,
                      metrics=['accuracy'])
        return model
```

### 步骤 3：将调优器集成到 DiabetesModelTrainer 中

定义了 `DiabetesHyperModel` 类后，我们现在将 `keras_tuner` 集成到模型训练过程中。我们修改 `DiabetesModelTrainer` 类中的 `train_tensorflow_model` 方法，使用 `RandomSearch`，这是一种系统地探索 `DiabetesHyperModel` 类中定义的超参数空间的调优器。

在此方法中，我们实例化调优器，指定参数，如试验次数 (`max_trials`) 和每次试验的执行次数 (`executions_per_trial`)。然后，调优器通过迭代不同的超参数组合来搜索最佳模型配置。找到最佳模型后，它会被返回，并可进一步训练和评估：

```python
[In]: class DiabetesModelTrainer:
    """用于训练 TensorFlow (Keras) 模型的类。"""

    @staticmethod
    def train_tensorflow_model(
        X_train,
        y_train,
        X_test,
        y_test,
        epochs=50
    ):
        """使用 keras_tuner 训练 TensorFlow (Keras) 模型。"""
        try:
            tuner = RandomSearch(
                DiabetesHyperModel(),
                objective='val_accuracy',
                max_trials=5,
                executions_per_trial=3,
                directory='tuner_dir',
                project_name='diabetes_tuning'
            )
            tuner.search(
                X_train,
                y_train,
                epochs=epochs,
                validation_data=(X_test, y_test),
                verbose=1
            )
            best_model = tuner.get_best_models(num_models=1)[0]
            logger.info("Best model training completed.")
            return best_model
        except Exception as e:
            logger.error(
                f"Error occurred during model training: "
                f"{str(e)}"
            )
```

**注意** 在此代码中，我们选择使用 Keras Tuner 进行超参数调优，因为它是 TensorFlow 生态系统内的原生工具，专门设计用于与 TensorFlow 模型无缝配合工作。Keras Tuner 提供了简单且灵活的接口来定义和搜索超参数，使其成为调优使用 TensorFlow 构建的深度学习和模型的理想选择。

或者，我们也可以使用 Scikit-Learn 库中的 `GridSearchCV`，这是一种广泛用于各种机器学习模型超参数调优的方法。虽然 `GridSearchCV` 强大且通用，但我们在此示例中选择了 Keras Tuner，因为它与 TensorFlow 的原生集成简化了调优过程，并确保与 TensorFlow 特定功能和函数的兼容性。对于感兴趣的用户，我们在 *Distributed Machine Learning with PySpark: Migrating Effortlessly from Pandas and Scikit-Learn*（Apress，2023 年 11 月）中详细介绍了 `GridSearchCV`。

下表比较了调优后的模型与固定超参数模型的结果。如所示，具有调优超参数的模型在多个指标上显示出改进的性能，证实了超参数调优在优化模型性能方面的有效性：

| 指标 | 调优模型 | 固定超参数模型 |
| :--- | :--- | :--- |
| 准确率 | 0.7863 | 0.7692 |
| 精确率 | 0.7500 | 0.7059 |
| 召回率 | 0.5854 | 0.5854 |
| F1 分数 | 0.6575 | 0.6400 |

超参数调优只是提高模型性能的一种方式。在第 9 章中，我们将进一步深入探讨调优，并探索提高模型性能的其他方法，从而更深入地理解如何有效地优化深度学习模型。

## 将所有部分结合在一起

在本节中，我们将构建、训练和评估用于糖尿病预测的 TensorFlow (Keras) 模型（带和不带 Keras Tuner）的各个代码片段整合起来。

## 使用固定超参数构建和训练 TensorFlow 模型

```python
[In]: import logging
[In]: from pyspark.sql import SparkSession
[In]: from pyspark.ml.feature import VectorAssembler, StandardScaler
[In]: from pyspark.sql.functions import col
[In]: from sklearn.metrics import (
    accuracy_score,
    precision_score,
    recall_score,
    f1_score
)
[In]: from tensorflow.keras.models import Sequential
[In]: from tensorflow.keras.layers import Dense, ReLU
[In]: from tensorflow.keras.optimizers import SGD
[In]: from tensorflow.keras.callbacks import Callback
[In]: import numpy as np
```





```python
[In]: logging.basicConfig(level=logging.INFO)
[In]: logger = logging.getLogger(__name__)

[In]: class CustomCallback(Callback):
    """用于打印 epoch
    信息的自定义 Keras 回调。"""
    def on_epoch_end(self, epoch, logs=None):
        """每 10 个 epoch 打印一次 epoch 信息。"""
        if (epoch + 1) % 10 == 0:
            logger.info(
                f"Epoch [{epoch + 1}/{self."
                f"params['epochs']}], "
                f"Loss: {logs['loss']:.4f}"
            )

[In]: class DiabetesProcessor:
    """用于预处理糖尿病数据的类。"""
    @staticmethod
    def preprocess_data(spark, data_file_path,
                        train_parquet_path, test_parquet_path):
        """使用 PySpark
        预处理糖尿病数据。"""
        try:
            diabetes_df = spark.read.csv(
                data_file_path,
                header=True,
                inferSchema=True
            )
            diabetes_df = diabetes_df.filter(
                (col("Glucose") != 0)
                & (col("BloodPressure") != 0)
                & (col("BMI") != 0)
            )
            feature_cols = [
                "Pregnancies",
                "Glucose",
                "BloodPressure",
                "BMI",
                "DiabetesPedigreeFunction",
                "Age"
            ]

            assembler = VectorAssembler(
                inputCols=feature_cols,
                outputCol="features")

            diabetes_df = assembler.
                transform(diabetes_df),

            scaler = StandardScaler(
                inputCol="features",
                outputCol="scaled_features"
            )

            scaler_model = scaler.fit(diabetes_df)

            diabetes_df = scaler_model.
                transform(diabetes_df)

            train_df, test_df = diabetes_df.randomSplit(
                [0.8, 0.2],
                seed=42
            )

            train_df.write.parquet(
                train_parquet_path,
                mode="overwrite"
            )

            test_df.write.parquet(
                test_parquet_path,
                mode="overwrite"
            )

            logger.info("数据预处理已完成。")
        except Exception as e:
            logger.error(
                f"数据预处理期间发生错误： "
                f"{str(e)}"
            )

[In]: class DiabetesModelTrainer:
    """用于训练 TensorFlow (Keras)
    模型的类。"""

    @staticmethod
    def train_tensorflow_model(
        X_train,
        y_train,
        epochs=100,
        lr=0.01
    ):
        """训练 TensorFlow (Keras) 模型。"""
        try:
            model = Sequential([
                Dense(64, input_dim=X_train.shape[1]),
                ReLU(),
                Dense(32),
                ReLU(),
                Dense(16),
                ReLU(),
                Dense(1, activation='sigmoid')
            ])
            optimizer = SGD(learning_rate=lr)
            model.compile(loss='binary_crossentropy',
                          optimizer=optimizer,
                          metrics=['accuracy'])

            custom_callback = CustomCallback()
            model.fit(X_train, y_train, epochs=epochs,
                      verbose=0, callbacks=[custom_callback])
            logger.info("模型训练已完成。")
            return model

        except Exception as e:
            logger.error(
                f"模型训练期间发生错误： "
                f"{str(e)}"
            )

[In]: class DiabetesModelEvaluator:
    """用于评估 TensorFlow (Keras)
    模型的类。"""
    @staticmethod
    def evaluate_model(model, X_test, y_test):
        """评估 TensorFlow (Keras) 模型。"""
        try:
            y_pred = (model.predict(X_test) > 0.5).astype(int)
            accuracy = accuracy_score(y_test, y_pred)
            precision = precision_score(y_test, y_pred)
            recall = recall_score(y_test, y_pred)
            f1 = f1_score(y_test, y_pred)
            logger.info(f"准确率：{accuracy:.4f}")
            logger.info(f"精确率：{precision:.4f}")
            logger.info(f"召回率：{recall:.4f}")
            logger.info(f"F1 分数：{f1:.4f}")
        except Exception as e:
            logger.error(
                f"模型评估期间发生错误： "
                f"{str(e)}"
            )

[In]: if __name__ == "__main__":
    try:
        spark = (SparkSession.builder
                 .appName("DiabetesClassification")
                 .config("spark.executor.instances", "4")
                 .config("spark.executor.memory", "4g")
                 .config("spark.executor.cores", "2")
                 .config("spark.driver.memory", "2g")
                 .getOrCreate())

        data_file_path = "/home/ubuntu/airflow/dags/diabetes.csv"

        train_parquet_path = \
            "/home/ubuntu/airflow/dags/diabetes_train.parquet"
        test_parquet_path = \
            "/home/ubuntu/airflow/dags/diabetes_test.parquet"

        DiabetesProcessor.preprocess_data(
            spark,
            data_file_path,
            train_parquet_path,
            test_parquet_path
        )

        train_diabetes_df = spark.read.parquet(train_parquet_path)

        X_train = np.array(train_diabetes_df.select(
            "scaled_features")
            .rdd.flatMap(lambda x: x).collect()
        )
        y_train = np.array(
            train_diabetes_df.select("Outcome")
            .rdd.flatMap(lambda x: x).collect())

        trained_model = \
            DiabetesModelTrainer.train_tensorflow_model(
                X_train,
                y_train
            )

        test_diabetes_df = spark.read.parquet(test_parquet_path)
        X_test = np.array(
            test_diabetes_df.select("scaled_features")
            .rdd.flatMap(lambda x: x).collect())
        y_test = np.array(
            test_diabetes_df.select("Outcome")
            .rdd.flatMap(lambda x: x).collect()
        )

        DiabetesModelEvaluator.evaluate_model(
            trained_model,
            X_test,
            y_test
        )

    except Exception as e:
        logger.error(f"发生错误：{str(e)}")
```

## 通过超参数调优优化 TensorFlow 模型

```python
[In]: import logging
[In]: from pyspark.sql import SparkSession
[In]: from pyspark.ml.feature import VectorAssembler, StandardScaler
[In]: from pyspark.sql.functions import col
[In]: from sklearn.metrics import (
    accuracy_score,
    precision_score,
    recall_score,
    f1_score
)
[In]: from tensorflow.keras.models import Sequential
[In]: from tensorflow.keras.layers import Dense, ReLU
[In]: from tensorflow.keras.optimizers import SGD
[In]: from tensorflow.keras.callbacks import Callback
[In]: from keras_tuner import HyperModel, RandomSearch
[In]: import numpy as np
[In]: logging.basicConfig(level=logging.INFO)
[In]: logger = logging.getLogger(__name__)

[In]: class CustomCallback(Callback):
    """用于打印 epoch 信息的自定义 Keras 回调。"""
    def on_epoch_end(self, epoch, logs=None):
        """每 10 个 epoch 打印一次 epoch 信息。"""
        if (epoch + 1) % 10 == 0:
            logger.info(
                f"Epoch [{epoch + 1}/{self."
                f"params['epochs']}], "
                f"Loss: {logs['loss']:.4f}")

[In]: class DiabetesProcessor:
    """用于预处理糖尿病数据的类。"""
    @staticmethod
    def preprocess_data(
            spark,
            data_file_path,
            train_parquet_path,
            test_parquet_path
    ):
        """使用 PySpark
        预处理糖尿病数据。"""
        try:
            diabetes_df = spark.read.csv(
                data_file_path,
                header=True,
                inferSchema=True
            )
            diabetes_df = diabetes_df.filter(
                (col("Glucose") != 0)
                & (col("BloodPressure") != 0)
                & (col("BMI") != 0)
            )
            feature_cols = [
                "Pregnancies",
                "Glucose",
                "BloodPressure",
                "BMI",
                "DiabetesPedigreeFunction",
                "Age"
            ]
            assembler = VectorAssembler(
                inputCols=feature_cols,
                outputCol="features")
            diabetes_df = assembler.
                transform(diabetes_df)
            scaler = StandardScaler(
                inputCol="features",
                outputCol="scaled_features"
            )
            scaler_model = scaler.fit(diabetes_df)
            diabetes_df = scaler_model.
                transform(diabetes_df)
            train_df, test_df = diabetes_df.randomSplit(
                [0.8, 0.2],
                seed=42
            )
            train_df.write.parquet(
                train_parquet_path,
                mode="overwrite"
            )
            test_df.write.parquet(
                test_parquet_path,
                mode="overwrite"
            )
            logger.info("数据预处理已完成。")
        except Exception as e:
```





```python
logger.error(
    f"Error occurred during data preprocessing: "
    f"{str(e)}"
)
```

```python
[In]: class DiabetesHyperModel(HyperModel):
    """用于调优 Keras 模型的 HyperModel。"""
    def build(self, hp):
        model = Sequential()
        model.add(
            Dense(
                units=hp.Int('units_1',
                             min_value=32,
                             max_value=128,
                             step=32
                             ),
                input_dim=X_train.shape[1]
                )
        )
        model.add(ReLU())
        model.add(
            Dense(
                units=hp.Int(
                    'units_2',
                    min_value=16,
                    max_value=64,
                    step=16
                    )
            )
        )
        model.add(ReLU())
        model.add(
            Dense(
                units=hp.Int(
                    'units_3',
                    min_value=8,
                    max_value=32,
                    step=8
                )
            )
        )
        model.add(ReLU())
        model.add(Dense(1, activation='sigmoid'))
        optimizer = SGD(
            learning_rate=hp.Float(
                'lr',
                1e-4,
                1e-2,
                sampling='log'
            )
        )
        model.compile(loss='binary_crossentropy', optimizer=optimizer, metrics=['accuracy'])
        return model
```

```python
[In]: class DiabetesModelTrainer:
    """用于训练 TensorFlow (Keras) 模型的类。"""
    @staticmethod
    def train_tensorflow_model(
        X_train,
        y_train,
        X_test,
        y_test,
        epochs=50
    ):
        """使用 keras_tuner 训练 TensorFlow (Keras) 模型。"""
        try:
            tuner = RandomSearch(
                DiabetesHyperModel(),
                objective='val_accuracy',
                max_trials=5,
                executions_per_trial=3,
                directory='tuner_dir',
                project_name='diabetes_tuning'
            )
            tuner.search(
                X_train,
                y_train,
                epochs=epochs,
                validation_data=(X_test, y_test),
                verbose=1
            )
            best_model = tuner.get_best_models(num_models=1)[0]
            logger.info("最佳模型训练完成。")
            return best_model
        except Exception as e:
            logger.error(
                f"模型训练过程中发生错误: "
                f"{str(e)}"
            )
```

```python
[In]: class DiabetesModelEvaluator:
    """用于评估 TensorFlow (Keras) 模型的类。"""
    @staticmethod
    def evaluate_model(model, X_test, y_test):
        """评估 TensorFlow (Keras) 模型。"""
        try:
            y_pred = (model.predict(X_test) > 0.5).astype(int)
            accuracy = accuracy_score(y_test, y_pred)
            precision = precision_score(y_test, y_pred)
            recall = recall_score(y_test, y_pred)
            f1 = f1_score(y_test, y_pred)
            logger.info(f"准确率: {accuracy:.4f}")
            logger.info(f"精确率: {precision:.4f}")
            logger.info(f"召回率: {recall:.4f}")
            logger.info(f"F1 分数: {f1:.4f}")
        except Exception as e:
            logger.error(
                f"模型评估过程中发生错误: "
                f"{str(e)}"
            )
```

```python
[In]: if __name__ == "__main__":
    try:
        spark = (
            SparkSession.builder
            .appName(
                "DiabetesProcessingAndTensorFlowTraining"
            )
            .config("spark.executor.instances", "4")
            .config("spark.executor.memory", "4g")
            .config("spark.executor.cores", "2")
            .config("spark.driver.memory", "2g")
            .getOrCreate()
        )

        data_file_path = "/home/ubuntu/airflow/dags/diabetes.csv"
        train_parquet_path = ("/home/ubuntu/airflow/dags/diabetes_train.parquet")
        test_parquet_path = ("/home/ubuntu/airflow/dags/diabetes_test.parquet")

        DiabetesProcessor.preprocess_data(
            spark,
            data_file_path,
            train_parquet_path,
            test_parquet_path
        )

        train_diabetes_df = spark.read.parquet(
            train_parquet_path
        )
        X_train = np.array(
            train_diabetes_df
            .select("scaled_features")
            .rdd.flatMap(lambda x: x)
            .collect()
        )
        y_train = np.array(
            train_diabetes_df
            .select("Outcome")
            .rdd.flatMap(lambda x: x)
            .collect()
        )

        test_diabetes_df = spark.read.parquet(
            test_parquet_path
        )
        X_test = np.array(
            test_diabetes_df
            .select("scaled_features")
            .rdd.flatMap(lambda x: x)
            .collect()
        )
        y_test = np.array(
            test_diabetes_df
            .select("Outcome")
            .rdd.flatMap(lambda x: x)
            .collect()
        )

        best_model = DiabetesModelTrainer.train_tensorflow_model(
            X_train,
            y_train,
            X_test,
            y_test
        )

        DiabetesModelEvaluator.evaluate_model(
            best_model,
            X_test,
            y_test
        )

    except Exception as e:
        logger.error(f"发生错误: {str(e)}")
```

# 摘要

在本章中，我们继续探索深度学习分类的话题，继上一章使用 PyTorch 之后，这次我们使用了 TensorFlow。我们演示了如何复制在 PyTorch 中使用的相同步骤，包括数据加载、预处理、定义模型架构、训练和评估。此外，我们还整合了额外的功能，例如将数据从 S3 存储桶复制到 EC2 本地目录进行处理，展示了与 AWS 服务的集成，并在整个建模过程中处理错误和日志消息，用于调试和监控。

为了实现两个模型性能的公平比较，我们使用了与 PyTorch 相同的皮马（Pima）糖尿病数据集。主要结论是，两个模型（PyTorch 和 TensorFlow）的性能相当。

我们还介绍了使用 keras_tuner 进行超参数调优，这有助于提高 TensorFlow 模型的性能。通过自动搜索最佳配置，我们获得了比手动选择超参数更好的结果。

在下一章中，我们将转向另一个同样重要的话题：如何使用 Apache Airflow 简化 AWS 上的管道流程。

# 第 8 章

## 使用 Apache Airflow 构建可扩展的深度学习管道

在前几章中，我们构建了可扩展的深度学习管道，并在 AWS EC2 实例上手动执行它们。虽然这种非自动化的方法在行业中很常见，但它并不总是最高效的。一方面，它缺乏对工作流状态和进度的可见性，需要单独实现监控和日志记录。另一方面，在修改或扩展工作流时也可能带来挑战。确实，如果没有专门的编排框架，将工作流扩展以管理大量数据或计算资源可能是令人生畏的。此外，如果没有标准化的方法，确保实验的可重复性变得具有挑战性，主要依赖于版本控制和文档。

采用 Apache Airflow 运行工作流可以有效解决这些问题。它促进了基于预定义时间表或触发的自动化执行，最大限度地减少了手动干预的需求。此外，它开箱即用地提供了全面的监控和日志记录功能使用户能够轻松跟踪工作流进度并排查出现的问题。当你在 Airflow 中运行 DAG（有向无环图）时，你可以确保任务根据其依赖关系以正确的顺序执行。Airflow 专门设计用于随着工作流的规模和复杂性的增长而扩展，有效地管理大量数据和计算资源。此外，它通过将工作流封装为代码、促进版本控制，并使团队成员能够分享以进行实验复现和随时间跟踪变更，从而促进可重复性。

在本章中，我们将演示如何使用 Apache Airflow 构建可扩展的数据处理管道。我们将创建完整的 AWS 工作流，包括使用 PySpark 预处理数据，使用 PyTorch 和 TensorFlow 开发深度学习模型，以及使用 Airflow 运行代码。更具体地说，我们将分别使用第 4 章和第 7 章中的特斯拉股票和糖尿病数据集，以及那些章节中的独立回归和分类脚本。这将允许我们演示如何通常运行 Python 脚本，并将其与作为 Apache Airflow DAG 更高效地执行进行对比。

我们将首先创建一个用于使用 PySpark 和 PyTorch 预测特斯拉股价的 Apache Airflow 管道，然后继续对使用 PySpark 和 TensorFlow 进行糖尿病分类执行相同的操作。

### 用于特斯拉股价预测的 Airflow 管道

在本节中，我们演示如何使用 Apache Airflow 构建可扩展的数据处理工作流。我们将创建一个 AWS 管道，包括使用 PySpark 预处理数据，使用 PyTorch 开发深度学习模型，以及使用 Airflow 运行代码。

为了实现这一点，我们将使用与第 4 章相同的特斯拉数据集。代码也将与该章节保持一致，主要区别在于本章采用更模块化的方法。一个模块化的





# 第 8 章 使用 Apache Airflow 构建可扩展的深度学习管道

...这种 方法可以简化开发并增强系统灵活性。每个组件，例如用于大数据处理的 PySpark、用于机器学习任务的 PyTorch 以及用于工作流编排的 Airflow，都可以被视为一个独立的模块。这种模块化设计允许更轻松地集成、定制以及跨项目复用。通过将任务封装在 Airflow DAG（有向无环图）中，每个模块可以独立进行编排和调度，从而实现高效的工作流管理。此外，设计可复用模块可确保一致性并减少不同项目间的开发开销。可扩展性和性能考量至关重要，特别是对于处理大型数据集的 PySpark 作业以及针对高效训练和推理进行优化的 PyTorch 模型。

在第 4 章中，我们通过 `main()` 函数手动执行了代码。这种方法与将代码作为 Airflow DAG 运行之间的主要区别在于，`main()` 函数编排各种任务的执行，而将代码集成到 Airflow DAG 时，通常不需要单独的 `main()` 函数以同样的方式编排任务。相反，任务被显式地定义为 Airflow DAG 的一部分，使用如 `PythonOperator` 或 `BashOperator` 等算子。每个算子对应一个特定任务，任务之间的依赖关系在 DAG 定义中使用 `>>` 运算符指定。

为了说明这一区别，我们将首先研究在没有 Apache Airflow DAG 的情况下，如何使用 `main()` 函数运行特斯拉股票价格预测代码。之后，我们将演示如何将完全相同的代码（不带 main 函数）作为 DAG 运行。

## 无 Airflow DAG 的特斯拉股票价格预测

在本小节中，我们以使用 PySpark 和 PyTorch 进行特斯拉股票预测为例，说明如何运行一个模块化的独立 Python 脚本，而不使用 Airflow DAG。我们为该项目开发了五个模块：

- `data_processing.py`：该模块负责使用 PySpark 加载和预处理特斯拉股票数据。
- `model_training.py`：该模块处理 PyTorch 深度学习回归模型的训练。
- `model_evaluation.py`：该模块用于评估 PyTorch 深度学习模型。
- `utils.py`：该模块提供工具函数，用于将 Spark DataFrame 列转换为 PyTorch 张量。
- `main.py`：此最终模块负责编排整体工作流。

让我们逐一查看这五个模块，从 `data_processing.py` 模块开始：

### 模块 1：data_processing.py

该模块旨在预处理特斯拉股票数据：

```python
from pyspark.sql import SparkSession
from pyspark.ml.feature import VectorAssembler, StandardScaler
from pyspark.sql import DataFrame

def load_data(file_path: str) -> DataFrame:
    """
    Load stock price data from a CSV file using
    SparkSession.
    """
    spark = SparkSession.builder \
        .appName("StockPricePrediction") \
        .getOrCreate()
    df = spark.read.csv(
        file_path,
        header=True,
        inferSchema=True
    )
    return df

def preprocess_data(df: DataFrame) -> DataFrame:
    """
    Preprocess the data by assembling feature
    vectors using
    VectorAssembler and scaling them using
    StandardScaler.
    """
    assembler = VectorAssembler(
        inputCols=['Open', 'High', 'Low', 'Volume'],
        outputCol='features'
    )
    df = assembler.transform(df)

    scaler = StandardScaler(
        inputCol="features",
        outputCol="scaled_features",
        withStd=True,
        withMean=True
    )
    scaler_model = scaler.fit(df)
    df = scaler_model.transform(df)
    df = df.select('scaled_features', 'Close')
    return df
```

让我们逐步深入代码：

- 首先，代码从 PySpark 导入必要的模块，包括用于初始化 Spark 功能的 `SparkSession`，以及来自机器学习（ML）特征模块的 `VectorAssembler` 和 `StandardScaler`。此外，它还从 `pyspark.sql` 导入 `DataFrame`，这是结构化数据的一种表示形式。
- `load_data` 函数接收一个文件路径作为输入，指向包含股票价格数据的 CSV 文件。它利用 `SparkSession.builder` 创建一个名为 “StockPricePrediction” 的 Spark 会话。然后，它将 CSV 文件读取为 DataFrame `df`，使 Spark 能够高效地处理分布式数据操作。`header=True` 参数表示第一行包含列名，而 `inferSchema=True` 指示 Spark 从数据中推断列类型。
- `preprocess_data` 函数接收一个 DataFrame `df` 作为输入，并执行机器学习任务所需的预处理步骤。首先，它利用 `VectorAssembler` 组装特征向量。在这里，它从 DataFrame 中选择 ‘Open’（开盘价）、‘High’（最高价）、‘Low’（最低价）和 ‘Volume’（成交量）列，构建一个名为 ‘features’ 的新列，其中包含这些特征的向量。
- 尽管后续的机器学习任务（即训练和评估）是使用 PyTorch 而不是 PySpark 进行的，但使用 `VectorAssembler` 组装特征在处理大型数据集时仍然非常有益。通过将相关特征整合到单个向量列中，它简化了数据准备过程，并确保输入 PyTorch 的数据与其期望的数据保持一致。这种整合简化了数据预处理与机器学习模型之间的接口，促进了从数据准备到模型训练的顺利过渡，并提高了整体工作流效率。
- 接下来，该模块采用 `StandardScaler` 对特征向量进行缩放。缩放对于归一化特征并确保它们具有相似的范围至关重要，这可以提高机器学习算法的性能和收敛速度。`withStd=True` 参数表示数据应被缩放为单位标准差，而 `withMean=True` 在缩放前对数据进行居中处理。
- 缩放后，函数选择包含缩放后特征向量的 'scaled_features' 列，以及代表目标变量（收盘股价）的 'Close' 列。处理后的 DataFrame `df` 被返回，准备用于模型训练和评估。

## 模块 2：model_training.py

该模块利用 PyTorch 库创建和训练一个用于监督学习任务（特斯拉股票价格预测）的神经网络回归模型：

```python
import torch
import torch.nn as nn
import torch.optim as optim
from torch.utils.data import DataLoader, TensorDataset

def create_data_loader(
    features,
    labels,
    batch_size=32
) -> DataLoader:
    """
    Convert the preprocessed data into PyTorch tensors and
    Create DataLoader objects for both the training
    and test
    sets.
    """
    dataset = TensorDataset(features, labels)
    return DataLoader(
        dataset,
        batch_size=batch_size,
        shuffle=True
    )

def train_model(
    model, train_loader, criterion, optimizer, num_epochs
):
    """
    Train the model on the training data using the
    DataLoader
    and the defined loss function and optimizer.
    Iterate over
    the data for a specified number of epochs,
    calculate the
    loss, and update the model parameters.
    """
    for epoch in range(num_epochs):
        for inputs, labels in train_loader:
            optimizer.zero_grad()
            outputs = model(inputs)
            loss = criterion(outputs, labels.unsqueeze(1))
            loss.backward()
            optimizer.step()
        print(
            f"Epoch [{epoch + 1}/{num_epochs}], "
            f"Loss: {loss.item():.4f}"
        )
```

让我们拆解代码以便更好地理解：

- 代码通过从 PyTorch 导入必要的模块开始，包括用于核心功能的 `torch`，用于构建神经网络组件的 `torch.nn`，用于优化算法的 `torch.optim`，以及用于处理数据加载和批处理的 `torch.utils.data` 中的 `DataLoader` 和 `TensorDataset`。`DataLoader` 从 PySpark 的角度来看尤为重要，因为它在训练期间有效地管理数据的加载和批处理。在 PySpark 等分布式环境中，通常会处理大型数据集，



DataLoader 确保数据以可控的批次输入模型，这有助于优化内存使用并提高计算效率。它还处理数据洗牌和并行加载，这对于提高模型性能和缩短训练时间至关重要。

- 定义了 `create_data_loader` 函数，用于将预处理后的数据转换为 PyTorch 张量，并为训练集和测试集创建 DataLoader 对象。该函数接收特征和标签作为输入，这些是来自上一模块的预处理数据。它们被转换为 `TensorDataset`，将特征和标签组合成一个数据集。然后，基于此数据集创建一个 DataLoader，指定所需的 `batch_size`，并启用每个纪元的数据洗牌。
- 接下来，定义了 `train_model` 函数，用于使用 DataLoader、定义的损失函数（criterion）和优化器，在训练数据上训练神经网络回归模型。该函数对数据进行指定纪元次数的迭代，每次迭代都会计算损失，并根据反向传播过程中计算的梯度更新模型参数。
- 在训练循环中，对于从 `train_loader` 加载的每个输入和标签批次，首先将优化器的梯度清零（`optimizer.zero_grad()`），确保来自之前迭代的梯度不会累积。然后，模型应用于输入以生成预测值（`outputs = model(inputs)`）。使用指定的 criterion 计算这些预测值与实际标签之间的损失。
- 计算损失后，梯度通过网络向后传播（`loss.backward()`），使 PyTorch 能够计算损失相对于模型参数的梯度。最后，优化器基于这些梯度更新模型参数（`optimizer.step()`）。
- 在整个训练过程中，会打印当前纪元和损失等信息，以监控模型进度。这个迭代训练循环将持续指定的纪元次数，随时间逐渐提高模型性能。

## 模块 3：model_evaluation.py

该模块旨在评估训练后的 PyTorch 模型在测试数据集上的性能：

```python
import torch

def evaluate_model(model, test_loader, criterion):
    """
    在测试数据上评估训练好的模型，
    以评估其性能。
    计算测试损失以及额外的
    评估指标，
    例如 R 平方得分。
    """
    with torch.no_grad():
        model.eval()
        predictions = []
        targets = []
        test_loss = 0.0
        for inputs, labels in test_loader:
            outputs = model(inputs)
            loss = criterion(outputs, labels.unsqueeze(1))
            test_loss += loss.item() * inputs.size(0)
            predictions.extend(outputs.squeeze().tolist())
            targets.extend(labels.tolist())

        test_loss /= len(test_loader.dataset)
        predictions = torch.tensor(predictions)
        targets = torch.tensor(targets)
        ss_res = torch.sum((targets - predictions) ** 2)
        ss_tot = torch.sum((targets - torch.mean(targets)) ** 2)
        r_squared = 1 - ss_res / ss_tot
        print(f"Test Loss: {test_loss:.4f}")
        print(f"R-squared Score: {r_squared:.4f}")
        return test_loss, r_squared.item()
```

让我们分解代码以理解其功能：

- 代码首先导入 torch 库，这是 PyTorch 的核心库。
- 定义了 `evaluate_model` 函数，用于评估模型在测试数据集上的性能。它接受三个主要输入：`model`，即待评估的训练好的 PyTorch 模型；`test_loader`，包含测试数据的 DataLoader 对象；以及 `criterion`，用于评估的损失函数，通常与训练时使用的相同。
- 在函数内部，评估过程封装在一个 `with torch.no_grad()` 块中（由于评估期间不需要梯度，因此禁用梯度计算），并使用 `model.eval()` 将模型切换到评估模式。
- 接下来，函数初始化空列表 `predictions` 和 `targets`，分别用于存储模型的预测值和实际目标值。此外，`test_loss` 被初始化以累加整个测试数据集的总损失。
- 该函数迭代遍历来自 `test_loader` 的数据批次，利用模型为每个批次计算预测值。使用指定的 criterion 计算预测输出与实际标签之间的损失。测试损失通过将损失乘以批次大小并加到 `test_loss` 上来累加。
- 然后通过使用 `outputs.squeeze().tolist()` 移除额外维度后，将预测输出追加到 `predictions` 列表中。同样，实际标签被追加到 `targets` 列表中。
- 遍历完所有批次后，通过将 `test_loss` 除以测试数据集中的样本总数，计算出整个数据集的平均测试损失。
- 将 `predictions` 和 `targets` 列表转换为 PyTorch 张量。然后脚本计算残差平方和（`ss_res`）和总平方和（`ss_tot`），以计算 R 平方得分，这是一个衡量回归模型拟合数据程度的指标。
- 最后，打印测试损失和 R 平方得分以供评估。该函数以元组形式返回测试损失和 R 平方得分。

## 模块 4：utils.py

实用模块通常是一组在整个项目不同部分中使用的函数的集合。在我们要做的案例中，只有一个函数 `spark_df_to_tensor`，它负责将 Spark DataFrame 列转换为 PyTorch 张量：

```python
import numpy as np
import torch
from typing import Tuple
from pyspark.sql import DataFrame

def spark_df_to_tensor(df: DataFrame) -> Tuple[torch.Tensor, torch.Tensor]:
    """
    将 Spark DataFrame 列转换为 PyTorch 张量。
    """
    features = torch.tensor(
        np.array(
            df.rdd.map(lambda x: x.scaled_features.toArray())
            .collect()
        ),
        dtype=torch.float32
    )
    labels = torch.tensor(
        np.array(
            df.rdd.map(lambda x: x.Close).collect()
        ),
        dtype=torch.float32
    )
    return features, labels
```

`spark_df_to_tensor` 函数接收 DataFrame 作为输入，并返回一个包含特征和标签（作为 PyTorch 张量）的元组。在函数内部，它使用 NumPy 和 PyTorch 进行必要的转换。这个函数对于训练和评估深度学习回归模型之前的数据预处理至关重要。

## 模块 5：main.py

现在我们来到主模块，它协调整个工作流程——数据预处理、模型训练、模型评估以及实用函数：

```python
import logging
import torch
import torch.optim as optim
import torch.nn as nn
from torch.utils.data import DataLoader
from typing import Tuple
from pyspark.sql import DataFrame
from data_processing import load_data, preprocess_data
from model_training import create_data_loader, train_model
from model_evaluation import evaluate_model
import utils

logging.basicConfig(level=logging.INFO)
logger = logging.getLogger(__name__)

def main(
    data_file_path: str,
    num_epochs: int = 100,
    batch_size: int = 32,
    learning_rate: float = 0.001
):
    """
    用于训练和评估特斯拉股价预测深度
    学习模型的主函数。
    参数:
        data_file_path (str):
            包含股价数据的 CSV 文件路径。
        num_epochs (int):
            模型训练的纪元数量。
            默认为 100。
        batch_size (int):
            训练期间数据加载的批次大小。
            默认为 32。
        learning_rate (float):
            优化器的学习率。
            默认为 0.001。
    异常:
        FileNotFoundError: 如果指定的数据
        文件未找到。
    """
    try:
        df = load_data(data_file_path)
        df = preprocess_data(df)
    except FileNotFoundError as e:
        logger.error(f"File not found: {e}")
        raise
    # ... (代码继续)
```





```python
train_df, test_df = df.randomSplit([0.8, 0.2],
        seed=42)

train_features, train_labels = utils.spark_df_to_tensor(
        train_df
    )
test_features, test_labels = utils.spark_df_to_tensor(
        test_df
    )
train_loader = create_data_loader(
    train_features,
    train_labels,
    batch_size=batch_size
    )
test_loader = create_data_loader(
    test_features,
    test_labels,
    batch_size=batch_size
    )
input_size = train_features.shape[1]
output_size = 1
model = nn.Sequential(
    nn.Linear(input_size, 64),
    nn.ReLU(),
    nn.Linear(64, 32),
    nn.ReLU(),
    nn.Linear(32, 16),
    nn.ReLU(),
    nn.Linear(16, output_size)
)

criterion = nn.MSELoss()
optimizer = optim.Adam(
    model.parameters(),
    lr=learning_rate
)

train_model(
    model,
    train_loader,
    criterion,
    optimizer,
    num_epochs
)

evaluate_model(model, test_loader, criterion)

torch.save(model.state_dict(), 'trained_model.pth')

except FileNotFoundError:
    logger.error(f"Data file not found at {data_file_path}")

if __name__ == "__main__":
    data_file_path = "/home/ubuntu/airflow/dags/TSLA_stock.csv"
    main(data_file_path)
```

## 第 8 章：使用 Apache Airflow 构建可扩展的深度学习管道

代码首先导入了 PyTorch 模块（`torch.optim`、`torch.nn`）、PySpark DataFrame（`pyspark.sql.DataFrame`）以及自定义模块（`data_processing`、`model_training`、`model_evaluation` 和 `utils`）。这些导入对于数据处理、模型训练和评估至关重要。随后，配置日志以显示 INFO 级别的消息，并初始化一个名为 `name` 的记录器。

在下一步中，模块定义了主函数。该函数接受几个参数，例如 `data_file_path`、`num_epochs`、`batch_size` 和 `learning_rate`。在此函数内部，执行以下步骤：

- 数据加载与预处理：该函数从由 `data_file_path` 指定的 CSV 文件加载数据，进行预处理，然后将其划分为训练集和测试集。
- 数据转换：使用自定义函数 `utils.spark_df_to_tensor` 将 Spark DataFrame 的特征和标签转换为 PyTorch 张量。
- 模型定义：使用 `nn.Sequential` 定义前馈神经网络模型。该模型由多个带有 ReLU 激活函数的线性层组成。
- 损失函数与优化器：使用均方误差（MSE）损失作为训练模型的准则，并采用 Adam 优化器来优化模型参数。
- 模型训练：调用 `train_model` 函数，使用训练数据加载器、准则、优化器和指定的迭代次数来训练模型。
- 模型评估：训练完成后，使用 `evaluate_model` 函数和测试数据加载器对训练好的模型进行评估。
- 模型保存：最后，将训练好的模型的状态字典保存到一个名为 `trained_model.pth` 的文件中。

最后，`__name__ == "__main__"` 块确保主函数仅在脚本直接运行时执行，而在作为模块导入到其他脚本中时不执行。它将 `data_file_path` 变量设置为特斯拉股票 CSV 文件的路径，并以该路径作为参数调用主函数。

为了运行代码，我们首先激活了“myenv”环境，然后导航到 EC2 实例上存储代码的目录“home/ubuntu/airflow/dags”，并执行“main.py”模块以编排特斯拉股价预测工作流：

```text
[In]: source activate myenv
[In]: cd home/ubuntu/airflow/dags
[In]: python3 main.py
```

代码的第一个输出是特斯拉股价预测模型训练过程中每个迭代周期的损失值：

| 迭代周期 (Epoch) | 损失 (Loss) |
|---|---|
| 1 | 49250.46 |
| 2 | 55661.49 |
| 3 | 24399.93 |
| 4 | 10579.51 |
| 5 | 2365.65 |
| 6 | 1972.29 |
| 7 | 1864.98 |
| 8 | 1288.25 |
| 9 | 736.96 |
| 10 | 625.62 |
| ... | ... |
| 100 | 9.70 |

以下是表中两列的解释：

- Epoch（迭代周期）：此列指示训练迭代周期的数量，即对整个训练数据集进行迭代的次数。
- Loss（损失）：此列表示每个迭代周期的训练损失。训练损失衡量模型预测值与训练数据中实际值之间的匹配程度。在训练初期，由于模型以随机的权重和偏置开始，并逐渐调整以最小化损失，因此损失值较高是预期之中的。

以下是训练损失随迭代周期变化的过程：

- 在初始迭代周期（例如第 1 和第 2 个周期），损失值极高（即 49,250 和 55,661），表明模型预测存在显著误差。这是训练开始时的预期现象，此时模型参数是随机初始化的。
- 随着训练的推进，损失值稳步下降。例如，到第 10 个迭代周期时，损失已降至 625.6，表明模型的预测值正在接近特斯拉的实际股价。

到第 100 个迭代周期时，训练损失已显著降低至 9.7，这表明模型很好地学习了训练数据中的模式。这种较低的训练损失表明模型在训练数据上的预测值与实际特斯拉股价紧密吻合。

第二个输出是测试损失和 R 平方值，如下所示：

| 指标 (Metric) | 数值 (Value) |
| :--- | :--- |
| 测试损失 (Test Loss) | 25.3015 |
| R 平方 (R-squared) | 0.9976 |

在此表中，我们提供了评估特斯拉股价预测模型性能的关键指标：

- 测试损失：此指标表示模型在独立测试数据集上进行预测时的误差。在特斯拉股价预测模型的背景下，25.3 的测试损失意味着，平均而言，模型的预测值与实际特斯拉股价偏差约为 25.3 美元。较低的测试损失值通常表明性能更好，因为这意味着模型的预测值更接近实际价格。
- R 平方得分：R 平方得分也称为决定系数，用于衡量模型预测值解释实际特斯拉股价方差的程度。0.9976 的 R 平方得分表明，模型解释了特斯拉股价约 99.76% 的变异性。换句话说，模型在预测特斯拉股价方面非常准确，因为它可以解释实际价格中观察到的大部分变异性。

训练损失的下降趋势表明，模型在训练迭代周期过程中已经学习并改进了其预测能力。测试损失和 R 平方指标表明，特斯拉股价预测模型表现优异，具有较低的测试损失和较高的 R 平方得分，这表明预测准确，且对特斯拉股价变异性的解释能力很强。

## 使用 Airflow DAG 进行特斯拉股价预测

现在，我们来到了本章的核心：将工作流编排为 Airflow DAG，而不是使用带有 `main()` 函数的独立脚本。在上一小节中，我们通过 `main()` 函数手动执行特斯拉股价预测代码，该函数编排了各种任务（预处理、模型训练和模型评估）的执行。当将代码集成到 Airflow DAG 中时，不再需要单独的 `main()` 函数以相同的方式编排任务。相反，任务被显式地定义为 Airflow DAG 的一部分，使用诸如 `PythonOperator` 或 `BashOperator` 等算子。每个算子对应一个特定任务，并使用 DAG 定义中的 `>>` 运算符指定任务之间的依赖关系。

为了演示如何将上一小节中的确切相同代码作为 DAG 运行，我们将按照以下步骤定义和编排 `tesla_stock_prediction` DAG：

- 导入：导入必要的库和模块。
- 默认参数：定义 DAG 的配置设置，如所有者、开始日期和重试次数。
- DAG 定义：创建具有唯一标识符、描述和其他设置的 DAG 对象。
- 预处理数据任务：定义执行 `preprocess_data_task` 函数以加载和预处理特斯拉股票数据的 `PythonOperator(preprocess_data_task)`。
- 训练模型任务：定义执行 `train_model_task` 函数以使用预处理数据训练深度学习回归模型的 `PythonOperator(train_model_task)`。
- 评估模型任务：定义执行 `evaluate_model_task` 函数以评估训练好模型的 `PythonOperator(evaluate_model_task)`。
- 任务依赖：使用 `>>` 运算符设置任务之间的依赖关系，指示任务应执行的顺序。

让我们一步步了解代码，从导入必要的模块开始：

### 步骤 1：导入

在此部分，我们导入工作流所需的各个库和模块：

512





## 导入说明

以下代码段展示了 Airflow DAG 中所需的导入语句：

```python
from datetime import datetime, timedelta
from airflow import DAG
from airflow.operators.python_operator import PythonOperator
import logging
import torch
import torch.optim as optim
import torch.nn as nn
from torch.utils.data import DataLoader
import numpy as np
from pyspark.sql import DataFrame
from typing import Tuple
from utils import spark_df_to_tensor
from data_processing import load_data, preprocess_data
from model_training import create_data_loader, train_model
from model_evaluation import evaluate_model
```

每个导入语句都引入了 DAG 中特定任务所需的功能，例如定义工作流、处理数据、执行深度学习任务以及记录用于监控和调试的日志消息。具体来说：

- `datetime`, `timedelta`：用于处理日期和时间间隔。它们用于在 `default_args` 字典中设置开始日期和重试延迟。
- `DAG`, `PythonOperator`：这些类从 Airflow 库导入，用于定义工作流和任务。它们用于创建 DAG（DAG 类）并定义任务（PythonOperator 类），例如 `preprocess_data_task`、`train_model_task` 和 `evaluate_model_task`。
- `logging`：此模块导入用于配置 DAG 执行期间的日志设置并记录日志消息。它用于配置记录器 (`logging.basicConfig`) 和记录消息 (`logger.error`)。
- `torch`, `optim`, `nn`, `DataLoader`：这些从 PyTorch 库导入，用于深度学习任务。它们在 `train_model_task` 和 `evaluate_model_task` 中用于定义神经网络回归模型、损失函数、优化器和数据加载器。
- `numpy`：此模块导入用于数值运算。它在 `train_model_task` 中用于数组操作，因为 PyTorch 与 NumPy 数组互操作性良好。
- `DataFrame`：此类从 PySpark 库导入，用于表示数据。它用于 `data_processing` 模块中的 `load_data` 和 `preprocess_data` 函数，这些函数在 `preprocess_data_task` 中被调用。
- `Tuple`：此类导入用于表示元组。它用于数据处理任务中的类型注解。
- `utils`, `data_processing`, `model_training`, `model_evaluation`：这些是从项目目录导入的自定义模块。它们包含用于各种任务的函数和工具：
    - `utils`：包含 `spark_df_to_tensor` 函数
    - `data_processing`：包含 `load_data` 和 `preprocess_data` 函数
    - `model_training`：包含 `create_data_loader` 和 `train_model` 函数
    - `model_evaluation`：包含 `evaluate_model` 函数

## 第 2 步：默认参数

在此部分，我们定义 Airflow DAG 的默认参数。我们还设置数据文件路径和日志记录：

```python
data_file_path = "/home/ubuntu/airflow/dags/TSLA_stock.csv"

logging.basicConfig(level=logging.INFO)
logger = logging.getLogger(__name__)

default_args = {
    'owner': 'airflow',
    'depends_on_past': False,
    'start_date': datetime(2024, 5, 1),
    'email_on_failure': False,
    'email_on_retry': False,
    'retries': 1,
    'retry_delay': timedelta(minutes=5),
}
```

默认参数如下：

- `owner`: 指定 DAG 的所有者
- `depends_on_past`: 确定任务实例是否依赖于前一个任务实例的成功
- `start_date`: 指定 DAG 的开始日期
- `email_on_failure`: 确定是否在失败时发送电子邮件
- `email_on_retry`: 确定是否在重试时发送电子邮件
- `retries`: 指定失败任务实例的重试次数
- `retry_delay`: 指定重试之间的延迟

## 第 3 步：DAG 定义

在此部分，我们定义 Airflow DAG 本身：

```python
dag = DAG(
    'tesla_stock_prediction',
    default_args=default_args,
    description='DAG for Tesla stock price prediction',
    schedule_interval=None,
)
```

以下是每个参数的含义：

- `'tesla_stock_prediction'`: 这是我们 DAG 的唯一标识符。它用于在 Airflow 中引用该 DAG。
- `default_args=default_args`: 此参数指定 DAG 的默认参数，我们在前面已定义。这些默认参数确定 DAG 执行的各种设置和行为。
- `description='DAG for Tesla stock price prediction'`: 这提供了我们 DAG 的描述，解释其目的或功能。
- `schedule_interval=None`: 此参数确定 DAG 的计划间隔。在这种情况下，它设置为 None，表示该 DAG 没有定期运行，而是手动或外部触发。

DAG 的计划功能与在没有 DAG 的情况下运行代码相比是一个重要属性。使用 cron 表达式将 `schedule_interval` 设置为特定值，例如 `0 0 * * *`，意味着 DAG 将在每月的每一天（无论星期几）的 00:00（午夜）运行。其他 cron 表达式的示例包括：

- `0 12 * * MON-FRI`：DAG 将在每周一至周五的 12:00 p.m.（中午）运行。
- `0 0 1 * *`：DAG 将在每月第一天的 00:00（午夜）运行。
- `0 0 * JAN,FEB,MAR *`：DAG 将在一月、二月和三月的每一天的 00:00（午夜）运行。
- `0 0 1,15 * *`：DAG 将在每月 1 日和 15 日的 00:00（午夜）运行。

例如，以下配置将确保 DAG 每天 00:00（午夜）运行：

```python
dag = DAG(
    'tesla_stock_prediction',
    default_args=default_args,
    description='An example DAG with a specific schedule interval',
    schedule_interval='0 0 * * *'
)
```

我们还可以将 DAG 安排为每天（每天午夜）、每周（每周一午夜）或每月（每月第一天天午夜）运行，如下所示：

```python
dag = DAG(
    'tesla_stock_prediction',
    default_args=default_args,
    description='A DAG scheduled to run daily',
    schedule_interval='@daily'
)
```

```python
dag = DAG(
    'tesla_stock_prediction',
    default_args=default_args,
    description='A DAG scheduled to run weekly',
    schedule_interval='@weekly'
)
```

```python
dag = DAG(
    'tesla_stock_prediction',
    default_args=default_args,
    description='A DAG scheduled to run monthly',
    schedule_interval='@monthly'
)
```

## 第 4 步：数据预处理任务

在此部分，我们定义一个名为 “preprocess_data_task” 的任务，用于执行特斯拉股票数据的预处理：

```python
def preprocess_data_task():
    try:
        df = load_data(data_file_path)
        df = preprocess_data(df)
    except Exception as e:
        logger.error(f"Error in preprocessing data: {str(e)}")
        raise
```

```python
preprocess_data_task = PythonOperator(
    task_id='preprocess_data_task',
    python_callable=preprocess_data_task,
    dag=dag,
)
```

该任务负责在用于模型训练和评估之前对特斯拉股票数据进行预处理。这是我们工作流中确保数据处于适当格式以供进一步处理的必要步骤。

以下是代码各部分的功能说明：

- 我们定义了一个函数 `preprocess_data_task()`，封装了预处理逻辑。在函数内部，我们使用 `load_data()` 函数加载数据，然后使用 `preprocess_data()` 函数对其进行预处理。
- 我们使用 try–except 块来处理预处理过程中可能出现的任何异常。如果发生错误，我们使用 logger 记录错误消息并抛出异常。
- 我们创建了一个名为 `preprocess_data_task` 的 `PythonOperator`，它在触发时执行 `preprocess_data_task()` 函数。我们指定任务 ID 为 “preprocess_data_task”，要调用的函数为 `python_callable=preprocess_data_task`，任务所属的 DAG 为 `dag=dag`。





### 步骤 5：训练模型任务

在本节中，我们定义了一个名为“train_model_task”的任务，该任务使用预处理后的数据训练深度学习回归模型：

```python
[In]: def train_model_task():
    try:
        df = load_data(data_file_path)
        df = preprocess_data(df)
        train_df, test_df = df.randomSplit([0.8, 0.2], seed=42)
        train_features, train_labels = spark_df_to_tensor(train_df)
        train_loader = create_data_loader(
            train_features,
            train_labels,
            batch_size=32
        )

        input_size = train_features.shape[1]
        output_size = 1
        model = nn.Sequential(
            nn.Linear(input_size, 64),
            nn.ReLU(),
            nn.Linear(64, 32),
            nn.ReLU(),
            nn.Linear(32, 16),
            nn.ReLU(),
            nn.Linear(16, output_size)
        )
        criterion = nn.MSELoss()
        optimizer = optim.Adam(model.parameters(), lr=0.001)
        train_model(
            model,
            train_loader,
            criterion,
            optimizer,
            num_epochs=100
        )
    except Exception as e:
        logger.error(f"Error in training model: {str(e)}")
        raise

[In]: train_model_task = PythonOperator(
               task_id='train_model_task',
               python_callable=train_model_task,
               dag=dag,
           )
```

该任务负责使用预处理后的数据训练深度学习回归模型。这是我们工作流中创建能够预测特斯拉股价的模型的关键步骤。

以下是代码各部分的作用：

- 我们定义了一个函数 `train_model_task()`，其中封装了训练逻辑。在函数内部，我们加载预处理后的数据；将其划分为训练集和测试集；将数据转换为 PyTorch 张量；创建数据加载器；定义模型架构、损失函数和优化器；最后，使用 `train_model()` 函数训练模型。

- 我们使用 try-except 块来处理训练过程中可能发生的任何异常。如果发生错误，我们将使用 logger 记录错误信息并抛出异常。

- 我们创建了一个名为 train_model_task 的 PythonOperator，当触发时执行 train_model_task() 函数。我们将任务 ID 指定为 “train_model_task”，调用的函数指定为 python_callable=train_model_task，任务所属的 DAG 指定为 dag=dag。

### 步骤 6：评估模型任务

在本节中，我们定义了一个名为“evaluate_model_task”的任务，该任务使用测试数据评估已训练的深度学习回归模型：

```python
[In]: def evaluate_model_task():
    try:
        df = load_data(data_file_path)
        df = preprocess_data(df)
        train_df, test_df = df.randomSplit([0.8, 0.2], seed=42)
        test_features, test_labels = spark_df_to_tensor(test_df)
        test_loader = create_data_loader(
                        test_features,
                        test_labels,
                        batch_size=32
                    )
        
        input_size = test_features.shape[1]
        output_size = 1
        model = nn.Sequential(
            nn.Linear(input_size, 64),
            nn.ReLU(),
            nn.Linear(64, 32),
            nn.ReLU(),
            nn.Linear(32, 16),
            nn.ReLU(),
            nn.Linear(16, output_size)
        )
        model.load_state_dict(torch.load('trained_model.pth'))
        
        criterion = nn.MSELoss()
        evaluate_model(model, test_loader, criterion)
    except Exception as e:
        logger.error(f"Error in evaluating model: {str(e)}")
        raise

[In]: evaluate_model_task = PythonOperator(
    task_id='evaluate_model_task',
    python_callable=evaluate_model_task,
    dag=dag,
)
```

该任务负责使用测试数据评估已训练的深度学习回归模型的性能。这是我们工作流中评估模型对未见数据泛化能力的关键步骤。

以下是代码各部分的作用：

- 我们定义了一个函数 `evaluate_model_task()`，其中封装了评估逻辑。在函数内部，我们加载预处理后的数据，将其划分为训练集和测试集，将测试数据转换为 PyTorch 张量，创建数据加载器，加载已训练的模型，最后使用 `evaluate_model()` 函数评估模型。

- 我们使用 try-except 块来处理评估过程中可能发生的任何异常。如果发生错误，我们将使用 logger 记录错误信息并抛出异常。

- 我们创建了一个名为 evaluate_model_task 的 PythonOperator，当触发时执行 evaluate_model_task() 函数。我们将任务 ID 指定为 "evaluate_model_task"，调用的函数指定为 python_callable=evaluate_model_task，任务所属的 DAG 指定为 dag=dag。

### 步骤 7：任务依赖关系

在本节中，我们定义了 DAG 中各任务之间的依赖关系：

```python
[In]: preprocess_data_task >> train_model_task >> evaluate_model_task
```

这些任务依赖关系确保我们的工作流按正确的顺序执行，每个任务都依赖于其前置任务的成功完成。在这种情况下，数据预处理必须在模型训练开始前完成，且模型训练必须在模型评估开始前完成。

以下是代码各部分的作用：

- preprocess_data_task >> train_model_task：该语句设置了 "preprocess_data_task" 和 "train_model_task" 任务之间的依赖关系。这意味着 "train_model_task" 任务只有在 "preprocess_data_task" 任务成功完成后才开始执行。

- train_model_task >> evaluate_model_task：该语句设置了 “train_model_task” 和 “evaluate_model_task” 任务之间的依赖关系。这意味着 “evaluate_model_task” 任务只有在 “train_model_task” 任务成功完成后才开始执行。

要在 AWS EC2 实例上执行代码，我们首先激活了名为 “myenv” 的虚拟环境，以确保必要的依赖项可用。接下来，我们导航到存放股价预测 DAG 的目录。最后，我们使用以下命令在 Apache Airflow 中触发了名为 “stock_price_prediction” 的 DAG：

```bash
[In]: source /home/ubuntu/myenv/bin/activate
[In]: cd /home/ubuntu/airflow/dags
[In]: airflow dags trigger stock_price_prediction
```

该 DAG 的输出与没有 DAG 的主函数输出非常相似，尽管存在一些细微差异，主要源于训练损失、测试损失和 R 平方值的波动。这些差异可归因于训练集和测试集样本随机选择的差异。

第一个输出是在训练 PyTorch 模型预测特斯拉股价过程中，每个纪元记录的训练损失值：

| 纪元 | 损失 |
| :--- | :--- |
| 1 | 30359.38 |
| 2 | 25931.21 |
| 3 | 34454.88 |
| 4 | 19568.01 |
| 5 | 4835.51 |
| 6 | 2016.92 |
| 7 | 1076.98 |
| 8 | 2502.23 |
| 9 | 1652.30 |
| 10 | 1186.91 |
| ... | ... |
| 100 | 8.50 |

在此表中，我们有两个列：

- 纪元：此列代表训练纪元的数量，即对整个训练数据集的迭代次数。每个纪元包括对整个数据集进行一次前向传播和一次反向传播。

- 损失：此列指示模型在每个纪元期间计算的损失或误差值。在股价预测的背景下，此损失值表示预测股价与实际观察价格之间的差异。值越低，表明性能越好，因为这意味着模型的预测更接近实际价格。

以下是对该数据的解读：

- 在初始纪元中，损失值相对较高（例如，第 1 个纪元为 30,359），表明模型的预测与训练数据集中的实际股价相距甚远。

- 随着训练的进展，损失值逐渐降低（例如，第 10 个纪元为 1,187）。这表明模型正在从数据中学习，并随着时间的推移做出更好的预测。在后期纪元，损失值变得非常低（例如，第 100 个纪元为 8.5），表明模型已经收敛，并正在做出非常准确的预测。

第二个输出是训练后模型在独立测试数据集上的性能指标：

| 指标 | 值 |
| :--- | :--- |
| 测试损失 | 25.3016 |
| R 平方得分 | 0.9976 |

在此表中，两个性能指标的含义如下：

- 测试损失：此指标专门衡量模型在测试数据集上的预测误差或损失。它代表模型对未见数据的泛化能力。较低的测试损失表明性能更好，因为这意味着模型的预测更接近测试数据集中的实际值。在这种情况下，测试损失报告为 25.3。





- **R 方得分（决定系数）**：该指标评估模型预测值与测试数据集中实际值之间的拟合优度。其取值范围为 0 到 1，其中 1 表示完美拟合。0.9976 的 R 方得分表明模型解释了测试数据围绕其均值约 99.76% 的方差。换句话说，模型的预测值与测试数据集中的实际值非常接近。

较低的测试损失与较高的 R 方得分表明模型在针对新数据进行准确预测时表现良好。

## 用于糖尿病预测的 Airflow 管道

在上一节中，我们为回归任务——预测特斯拉股价——创建了一个 Airflow 管道。在本节中，我们将为分类任务——预测糖尿病——构建一个类似的 Airflow 管道。更具体地说，我们将创建一个 AWS 管道，该管道包括使用 PySpark 对数据进行预处理、使用 TensorFlow 开发深度学习分类模型以及使用 Airflow 运行代码。

与我们在回归任务中的方法类似，我们将首先演示如何在没有 Airflow DAG 的情况下执行糖尿病分类代码。这将涉及使用 `main()` 函数来编排管道中的任务。我们将使用*第 7 章*中介绍的相同糖尿病数据集。代码结构将主要镜像前述章节，主要区别在于本章呈现了更具模块化的方法。在演示了如何在没有 Airflow DAG 的情况下运行代码之后，我们将说明如何将其与 DAG 集成。

## 无需 Airflow DAG 的糖尿病预测

在本小节中，我们说明如何使用 `main()` 函数在没有 Airflow DAG 的情况下运行糖尿病预测管道。代码已组织为以下四个模块：

- `preprocessing.py`：该模块负责使用 PySpark 加载和预处理糖尿病数据。
- `model_training.py`：该模块处理 TensorFlow 深度学习分类模型的训练。
- `model_evaluation.py`：该模块用于评估 TensorFlow 深度学习分类模型。
- `main.py`：该模块包含 `main()` 函数，用于编排整体工作流程。

让我们逐一介绍这四个模块，从 `preprocessing.py` 模块开始：

### 模块 1：preprocessing.py

该模块包含使用 PySpark 对糖尿病数据进行预处理，以便输入 TensorFlow 模型的代码：

```python
from pyspark.sql import SparkSession
from pyspark.ml.feature import VectorAssembler, StandardScaler
import logging
from pyspark.sql.functions import col
logger = logging.getLogger(__name__)

def preprocess_data(
    data_file_path,
    train_parquet_file_path,
    test_parquet_file_path
):
    """
    Preprocess diabetes data.
    
    Args:
        data_file_path (str):
            Path to the diabetes data CSV file.
        train_parquet_file_path (str):
            Path to save the preprocessed training data.
        test_parquet_file_path (str):
            Path to save the preprocessed testing data.
    """
    try:
        spark = (SparkSession.builder
                 .appName("DiabetesProcessing")
                 .getOrCreate())
        
        diabetes_df = spark.read.csv(
            data_file_path,
            header=True,
            inferSchema=True
        )
        
        diabetes_df = diabetes_df.filter(
            (col("Glucose") != 0)
            & (col("BloodPressure") != 0)
            & (col("BMI") != 0)
        )
        
        feature_cols = [
            "Pregnancies",
            "Glucose",
            "BloodPressure",
            "BMI",
            "DiabetesPedigreeFunction",
            "Age"
        ]
        
        assembler = VectorAssembler(
            inputCols=feature_cols,
            outputCol="features"
        )
        diabetes_df = assembler.transform(diabetes_df)
        
        scaler = StandardScaler(
            inputCol="features",
            outputCol="scaled_features"
        )
        scaler_model = scaler.fit(diabetes_df)
        diabetes_df = scaler_model.transform(diabetes_df)
        
        train_df, test_df = diabetes_df.randomSplit(
            [0.8, 0.2],
            seed=42
        )
        
        train_df.write.parquet(
            train_parquet_file_path,
            mode="overwrite"
        )
        test_df.write.parquet(
            test_parquet_file_path,
            mode="overwrite"
        )
        
        logger.info(
            "Data preprocessing completed successfully."
        )
    except Exception as e:
        logger.error(
            f"Error occurred during preprocessing: {str(e)}"
        )
```

该模块封装了在 PySpark 环境中对糖尿病数据集进行预处理所需的步骤，使其准备就绪以供 TensorFlow 模型使用。以下是代码的简要说明：

- **导入所需库**：该模块导入了必要的库，如 `SparkSession`、`VectorAssembler`、`StandardScaler`、`logging` 以及 `pyspark.sql.functions` 中的函数。
- **设置记录器**：它设置了一个以模块命名的记录器。
- **`preprocess_data` 函数**：此函数是预处理的主入口点。它接受三个参数：
  - `data_file_path`：糖尿病数据 CSV 文件的路径
  - `train_parquet_file_path`：保存预处理训练数据的路径
  - `test_parquet_file_path`：保存预处理测试数据的路径
- **SparkSession 设置**：它创建了一个名为“DiabetesProcessing”的 `SparkSession`。
- **读取数据**：包含糖尿病数据的 CSV 文件使用 Spark 的 `read.csv` 方法读取到 DataFrame 中。
- **数据过滤**：过滤掉葡萄糖（Glucose）、血压（BloodPressure）和 BMI 等于 0 的行。
- **特征选择**：选择特征列——“Pregnancies”、“Glucose”、“BloodPressure”、“BMI”、“DiabetesPedigreeFunction” 和 “Age”。
- **特征向量化**：使用 `VectorAssembler` 创建特征向量，将选定的特征列组合成名为 "features" 的单一路量列。
- **特征缩放**：使用 `StandardScaler` 对特征进行缩放以标准化它们。
- **数据分割**：使用 80-20 的分割比例将预处理后的数据分为训练集和测试集。
- **保存数据**：预处理的训练数据和测试数据被保存为 Parquet 文件。
- **日志记录**：记录一条消息，指示数据预处理成功完成。如果预处理过程中发生任何异常，它会记录包含异常详情的错误消息。

## 模块 2：model_training.py

该模块负责使用预处理后的数据训练 TensorFlow 分类模型：

```python
import numpy as np
from pyspark.sql import SparkSession
from tensorflow.keras.models import Sequential
from tensorflow.keras.layers import Dense
from tensorflow.keras.optimizers import SGD
from tensorflow.keras.callbacks import Callback
import logging

logger = logging.getLogger(__name__)

class CustomCallback(Callback):
    """Custom callback for printing epoch information."""
    def on_epoch_end(self, epoch, logs=None):
        """Print epoch information at the end of each epoch."""
        if (epoch + 1) % 10 == 0:
            logger.info(
                f"Epoch [{(epoch + 1)}/{self.params['epochs']}], "
                f"Loss: {logs['loss']:.4f}"
            )

def train_tensorflow_model(
    train_parquet_file_path,
    model_save_path
):
    """Train a TensorFlow model.

    Args:
        train_parquet_file_path (str):
            Path to the preprocessed training data.
        model_save_path (str):
            Path to save the trained model.
    """
    try:
        spark = (SparkSession.builder
                 .appName("TensorFlowTraining")
                 .getOrCreate())
```




## 模块 2：model_training.py

```python
train_diabetes_df = spark.read.parquet(train_parquet_file_path)

X_train = np.array(
    train_diabetes_df.select("scaled_features")
    .rdd.flatMap(lambda x: x)
    .collect()
)

y_train = np.array(
    train_diabetes_df.select("Outcome")
    .rdd.flatMap(lambda x: x)
    .collect()
)

model = Sequential()
model.add(Dense(
    64,
    input_dim=X_train.shape[1],
    activation='relu'
))
model.add(Dense(32, activation='relu'))
model.add(Dense(1, activation='sigmoid'))

optimizer = SGD(learning_rate=0.01)
model.compile(
    loss='binary_crossentropy',
    optimizer=optimizer,
    metrics=['accuracy']
)

custom_callback = CustomCallback()
model.fit(
    X_train,
    y_train,
    epochs=100,
    verbose=0,
    callbacks=[custom_callback]
)

model.save(model_save_path)

logger.info("Model training completed successfully.")
except Exception as e:
    logger.error(
        f"Error occurred during model training: {str(e)}"
    )
```

我们来拆解一下这段代码：

- **导入所需库**：该模块导入了必要的库，例如 NumPy、来自 PySpark 的 SparkSession，以及 TensorFlow 的各个组件，包括用于创建顺序模型的 Sequential、用于添加全连接层的 Dense、用于随机梯度下降优化的 SGD、用于创建自定义回调的 Callback，以及用于记录日志的 logging。
- **自定义回调**：定义了一个名为 CustomCallback 的自定义回调，它继承自 TensorFlow 的 Callback 类。此回调用于在训练过程中每个 epoch 结束时打印 epoch 信息。
- **train_tensorflow_model 函数**：此函数是训练 TensorFlow 模型的主入口点。它接受两个参数：
  - train_parquet_file_path：预处理后的 Parquet 格式训练数据的路径
  - model_save_path：保存训练好的 TensorFlow 模型的路径
- **SparkSession 设置**：创建一个名为 “TensorFlowTraining” 的 SparkSession。
- **加载数据**：将 Parquet 训练数据加载到名为 train_diabetes_df 的 PySpark DataFrame 中。
- **数据转换**：将 PySpark DataFrame 转换为 NumPy 数组（X_train 和 y_train），作为 TensorFlow 模型的输入和输出使用。
- **模型定义**：定义了一个包含三层的全连接顺序模型——两个带有 ReLU 激活函数的全连接层，以及一个带有 sigmoid 激活函数的全连接层。
- **模型编译**：使用二元交叉熵损失函数、指定学习率的 SGD 优化器以及准确率作为评估指标来编译模型。
- **回调设置**：创建之前定义的自定义回调实例（custom_callback）。
- **模型训练**：使用自定义回调打印 epoch 信息，将模型拟合到训练数据上，训练 100 个 epoch。
- **模型保存**：将训练好的模型保存到指定路径。
- **日志记录**：记录一条消息，指示模型训练成功完成。如果在训练过程中发生任何异常，则记录包含异常详情的错误消息。

### 模块 3：model_evaluation.py

该模块负责使用预处理后的测试数据评估 TensorFlow 分类模型的性能：

```python
import numpy as np
from pyspark.sql import SparkSession
from sklearn.metrics import accuracy_score, precision_score, recall_score, f1_score
from tensorflow.keras.models import load_model
import logging

logger = logging.getLogger(__name__)

def evaluate_model(
    test_parquet_file_path,
    model_load_path
):
    """
    Evaluate a TensorFlow model.
    
    Args:
        test_parquet_file_path (str):
            Path to the preprocessed testing data.
        model_load_path (str):
            Path to load the trained model.
    """
    try:
        spark = SparkSession.builder \
                .appName("ModelEvaluation") \
                .getOrCreate()

        model = load_model(model_load_path)

        test_diabetes_df = spark.read.parquet(
            test_parquet_file_path
        )

        X_test = np.array(
            test_diabetes_df.select("scaled_features")
            .rdd.flatMap(lambda x: x)
            .collect()
        )

        y_test = np.array(
            test_diabetes_df.select("Outcome")
            .rdd.flatMap(lambda x: x)
            .collect()
        )

        y_pred = (model.predict(X_test) > 0.5).astype(int)

        accuracy = accuracy_score(y_test, y_pred)
        precision = precision_score(y_test, y_pred)
        recall = recall_score(y_test, y_pred)
        f1 = f1_score(y_test, y_pred)

        logger.info(f"Accuracy: {accuracy:.4f}")
        logger.info(f"Precision: {precision:.4f}")
        logger.info(f"Recall: {recall:.4f}")
        logger.info(f"F1 Score: {f1:.4f}")
    
    except Exception as e:
        logger.error(
            f"Error occurred during model evaluation: {str(e)}"
        )
```

我们来拆解一下这段代码：

- **导入所需库**：该模块导入了必要的库，例如 NumPy、来自 PySpark 的 SparkSession、来自 sklearn.metrics 的各种评估指标、来自 TensorFlow 的 load_model 以及 logging。
- **evaluate_model 函数**：此函数是评估 TensorFlow 模型的主入口点。它接受两个参数：
  - test_parquet_file_path：预处理后的 Parquet 格式测试数据的路径
  - model_load_path：加载训练好的 TensorFlow 模型的路径
- **SparkSession 设置**：创建一个名为 “ModelEvaluation” 的 SparkSession。
- **加载模型**：使用 load_model 从指定路径加载训练好的 TensorFlow 模型。
- **加载测试数据**：将 Parquet 测试数据加载到名为 test_diabetes_df 的 PySpark DataFrame 中。
- **数据转换**：将 PySpark DataFrame 转换为 NumPy 数组（X_test 和 y_test），用于模型评估。
- **模型预测**：使用加载的模型对测试数据的结果（y_pred）进行预测。应用 0.5 的阈值将概率转换为二元预测。
- **计算评估指标**：使用来自 sklearn.metrics 的 accuracy_score、precision_score、recall_score 和 f1_score 计算准确率、精确率、召回率和 F1 分数等评估指标。
- **日志记录**：记录评估指标，包括准确率、精确率、召回率和 F1 分数。
- **错误处理**：如果在模型评估过程中发生任何异常，则记录包含异常详情的错误消息。

## 模块 4：main.py

我们现在来到了主模块。这个脚本是协调糖尿病预测的 TensorFlow 分类模型预处理、训练和评估工作流的主入口点（main.py）：

```python
import logging
from preprocessing import preprocess_data
from model_training import train_tensorflow_model
from model_evaluation import evaluate_model

logging.basicConfig(level=logging.INFO)
logger = logging.getLogger(__name__)

def main():
    preprocess_data(
        "/home/ubuntu/airflow/dags/diabetes.csv",
        "/home/ubuntu/airflow/dags/diabetes_train.parquet",
        "/home/ubuntu/airflow/dags/diabetes_test.parquet"
    )
    logger.info("Data preprocessing completed.")
    
    train_tensorflow_model(
        "/home/ubuntu/airflow/dags/diabetes_train.parquet",
        "/home/ubuntu/airflow/dags/diabetes_model.h5"
    )
    logger.info("Model training completed.")
    
    evaluate_model(
        "/home/ubuntu/airflow/dags/diabetes_test.parquet",
        "/home/ubuntu/airflow/dags/diabetes_model.h5"
    )
    logger.info("Model evaluation completed.")

if __name__ == "__main__":
    main()
```

我们来拆解一下这段代码：

- **导入所需库**：该脚本导入了用于记录日志的 logging，以及来自相应模块的 `preprocess_data`、`train_tensorflow_model` 和 `evaluate_model` 函数。
- **日志设置**：配置日志以显示级别为 INFO 的消息。
- **主函数**：此函数是协调工作流的主入口点。它执行以下步骤：
  - 调用 preprocess_data 函数预处理糖尿病数据，将预处理后的训练和测试数据保存为 Parquet 文件。
  - 记录一条消息，指示数据预处理完成。
  - 调用 train_tensorflow_model 函数，使用预处理后的训练数据训练 TensorFlow 模型，并保存训练好的模型。
  - 记录一条消息，指示模型训练完成。
  - 调用 evaluate_model 函数，使用预处理后的测试数据评估训练好的模型。
  - 记录一条消息，指示模型评估完成。
- **__name__ == "__main__" 检查**：此检查确保只有在直接运行脚本时才执行主函数，而不是在将其作为模块导入到其他脚本中时执行。

该脚本协调了从数据预处理到模型训练和评估的整个工作流，并记录消息以指示每个步骤的完成。提供给预处理、训练和评估函数的路径指示了输入数据和训练好的模型的存储或检索位置。

要运行代码，我们首先激活了 “mynv” 环境，然后导航到存储代码的 EC2 实例上的目录 “home/ubuntu/airflow/dags”，并执行 “main.py” 模块以协调糖尿病预测工作流。




```
[In]: source activate myenv
[In]: cd home/ubuntu/airflow/dags
[In]: python3 main.py
```

代码的第一个输出提供了TensorFlow糖尿病分类模型在训练过程中，每十个epoch的损失值：

| 轮次 (Epoch) | 损失值 (Loss) |
| :--- | :--- |
| 10 | 0.5857 |
| 20 | 0.5705 |
| 30 | 0.5663 |
| 40 | 0.5611 |
| 50 | 0.5543 |
| 60 | 0.5484 |
| 70 | 0.5410 |
| 80 | 0.5359 |
| 90 | 0.5296 |
| 100 | 0.5273 |

输出表格中的每一行对应于一个特定的epoch，并记录了每个epoch结束时的损失值。各列的含义如下：

- **Epoch（轮次）**: 此列指示轮次编号，代表在训练过程中对完整训练数据集进行的一次完整遍历。
- **Loss（损失值）**: 此列表示每个epoch结束后获得的损失值。损失值是衡量模型预测与训练数据集中实际标签匹配程度的指标。损失值越低，表明性能越好，意味着模型预测更接近实际标签。

例如，在第一个记录的epoch（第10个epoch）中，损失值约为0.59，这表明在对训练数据集进行第一次完整遍历后，模型预测与实际标签之间的平均偏差约为0.59。随着后续epoch训练的推进，损失值通常会逐渐降低，这表明模型正在提高其准确预测的能力。到训练结束时（第100个epoch），损失值已降至0.53，这表明与早期轮次相比，模型相对于实际标签的平均偏差更低。

第二个输出代表了在测试数据集上评估糖尿病分类模型后获得的评估指标：

| 指标 | 值 |
| --- | --- |
| 准确率 (Accuracy) | 0.7692 |
| 精确率 (Precision) | 0.7059 |
| 召回率 (Recall) | 0.5854 |
| F1 分数 (F1 Score) | 0.6400 |

每个指标的含义如下：

- **Accuracy（准确率）**: 此指标代表模型的整体准确性，指示在所有实例中正确分类的比例。在这种情况下，模型的准确率为0.7692，意味着大约76.92%的实例被正确分类。
- **Precision（精确率）**: 精确率是衡量模型在所有预测为正的实例中正确识别正实例的能力。0.7059的精确率表明，在所有被模型预测为正的实例中，大约70.59%是真正的正实例。
- **Recall（召回率）**: 召回率也称为灵敏度，衡量模型正确分类的实际正实例的比例。0.5854的召回率意味着模型正确识别了大约58.54%的所有实际正实例。
- **F1 Score（F1 分数）**: F1分数是精确率和召回率的调和平均值或加权平均值，提供单一指标以平衡精确率和召回率。更高的F1分数表明整体性能更好。在这种情况下，F1分数为0.64，表明精确率和召回率之间取得了合理的平衡。

正如我们在第7章已经知道的那样，结果并非最优，表明模型性能仍有改进空间。这主要归因于样本有限且分布不平衡，以及潜在的数据质量问题。

## 使用 Airflow DAG 进行糖尿病预测

在上一小节中，我们通过 main() 函数手动执行了糖尿病预测代码，编排了各种任务（预处理、模型训练和模型评估）的执行。在当前小节中，我们将把这个 main() 函数转换为 Apache Airflow DAG。在将代码集成到 DAG 时，不需要单独的 main() 函数来编排任务。相反，任务在 Airflow DAG 中使用 PythonOperator 或 BashOperator 等操作符显式定义。每个操作符对应一个特定任务，任务之间的依赖关系在 DAG 定义中使用 >> 操作符指定。

让我们演示一下如何运行与上一小节相同的代码作为名为 diabetes_processing_and_training 的 DAG。该 DAG 取代了 main() 函数，而三个模块（preprocessing.py、model_training.py 和 model_evaluation.py）保持不变。

我们从导入语句开始。

### 步骤 1：导入

以下导入语句引入了在 Apache Airflow DAG 中定义和执行任务所需的类和函数，用于数据预处理、模型训练和模型评估：

```
[In]: from datetime import datetime, timedelta
[In]: from airflow import DAG
[In]: from airflow.operators.python_operator import PythonOperator
[In]: from preprocessing import preprocess_data
[In]: from model_training import train_tensorflow_model
[In]: from model_evaluation import evaluate_model
```

以下是每行的作用：

- **from datetime import datetime, timedelta**: 此行从 datetime 模块导入 datetime 和 timedelta 类。这些类用于处理日期和时间，其中 timedelta 特别适用于添加或减去时间间隔。
- **from airflow import DAG**: 此行从 airflow 模块导入 DAG 类。DAG 是 Apache Airflow 中的一个基本概念，代表具有依赖关系的任务集合。
- **from airflow.operators.python_operator import PythonOperator**: 此行从 Airflow operators 包中的 python_operator 模块导入 PythonOperator 类。PythonOperator 用于在 Airflow DAG 中将 Python 函数作为任务执行。
- **from preprocessing import preprocess_data**: 此行从 preprocessing 模块导入 preprocess_data 函数，用于预处理糖尿病数据。
- **from model_training import train_tensorflow_model**: 此行从 model_training 模块导入 train_tensorflow_model 函数，用于训练 TensorFlow 机器学习分类模型。
- **from model_evaluation import evaluate_model**: 此行从 model_evaluation 模块导入 evaluate_model 函数，用于评估训练好的 TensorFlow 机器学习模型。

### 步骤 2：定义默认参数

在此步骤中，我们定义 default_args 字典，该字典指定了各种默认参数，如所有者、开始日期、电子邮件设置、重试次数和重试延迟：

```
[In]: default_args = {
    'owner': 'airflow',
    'depends_on_past': False,
    'start_date': datetime(2024, 2, 25),
    'email_on_failure': False,
    'email_on_retry': False,
    'retries': 1,
    'retry_delay': timedelta(minutes=5),
}
```

这段代码定义了一个名为 default_args 的字典，其中包含 Apache Airflow DAG 的各种配置参数。字典中的每个键值对代表一个特定的配置选项：

- **’owner’: ’airflow’**: 指定 DAG 的所有者。这通常是负责维护该 DAG 的人员或团队的用户名或标识符。
- **’depends_on_past’: False**: 指示任务的执行是否依赖于同一任务前一次运行的成功。将其设置为 False 意味着任务可以独立于其先前的执行状态运行。
- **’start_date’: datetime(2024, 2, 25)**: 设置 DAG 执行的开始日期。这里，datetime(2024, 2, 25) 创建一个表示 2024 年 2 月 25 日的 datetime 对象，指定 DAG 何时开始运行任务。
- **’email_on_failure’: False**: 确定当 DAG 中的任务失败时是否应发送电子邮件通知。将其设置为 False 将禁用失败电子邮件通知。
- **’email_on_retry’: False**: 控制当任务在失败后重试时是否应发送电子邮件通知。与 ’email_on_failure’ 类似，将其设置为 False 将禁用重试电子邮件通知。
- **’retries’: 1**: 定义任务在失败情况下应重试的次数。在这里，任务将在初始失败后重试一次。




- `retry_delay`: timedelta(minutes=5): 指定任务重试之间的时间间隔。在此情况下，如果任务失败，将在 5 分钟后进行重试。

## 步骤 3：创建 DAG 对象

在这一步中，我们使用 DAG 类实例化 DAG 对象。这将创建一个名为 `diabetes_processing_and_training` 的 DAG，并应用指定的默认参数：

```python
[In]: dag = DAG(
       'diabetes_processing_and_training',
       default_args=default_args,
       description=('Process diabetes data with PySpark '
                    'and train TensorFlow model'),
       schedule_interval=None,
       )
```

此代码块初始化了一个名为 `dag` 的 DAG 对象，具有特定的属性和配置：

- `diabetes_processing_and_training`：指定 DAG 的名称。该名称用于在 Airflow 中识别该 DAG。
- `default_args=default_args`：将之前定义的 `default_args` 字典分配给 DAG 构造函数的 `default_args` 参数。这确保了 `default_args` 中指定的默认配置参数应用于该 DAG。
- `description=('Process diabetes data with PySpark and train TensorFlow model')`：为 DAG 提供描述。此描述作为该 DAG 设计目标或目的的简要总结。
- `schedule_interval=None`：设置 DAG 执行的时间间隔。在此处，`None` 表示该 DAG 不会按计划定期运行。相反，它可以被手动触发或由外部事件触发。

## 步骤 4：定义任务

在这一步中，我们定义了三个任务，对应于上一小节的三个模块：数据预处理、训练 TensorFlow 模型以及评估训练好的模型。

我们首先定义 `preprocess_task`，它将在 Airflow DAG 中作为任务执行带有指定参数的 `preprocess_data` 函数：

```python
[In]: preprocess_task = PythonOperator(
    task_id='preprocess_data',
    python_callable=preprocess_data,
    op_kwargs={
        'data_file_path': ("/home/ubuntu/airflow/dags"
                            "/diabetes.csv"),
        'train_parquet_file_path': ("/home/ubuntu/airflow/dags"
                            "/diabetes_train.parquet"),
        'test_parquet_file_path': ("/home/ubuntu/airflow/dags"
                            "/diabetes_test.parquet")
    },
    dag=dag,
)
```

此代码创建了一个名为 `preprocess_task` 的 `PythonOperator` 类实例。让我们分解此次实例化的每个部分：

- `PythonOperator`：这是 Airflow 库中的一个类，用于在 Airflow DAG 中执行 Python 函数作为任务。
- `task_id='preprocess_data'`：这指定了任务的唯一标识符。在此情况下，其名称为 'preprocess_data'。
- `python_callable=preprocess_data`：此参数指定了操作员将执行的 Python 函数。在此处，它被设置为 `preprocess_data`，表明 `preprocess_data` 函数将被作为任务执行。
- `op_kwargs`：此参数指定了需要传递给 Python 函数（`preprocess_data`）的关键字参数（kwargs）。它是一个包含 `preprocess_data` 函数所需参数的字典。这些参数包括数据文件、训练 Parquet 文件和测试 Parquet 文件的路径：
  - `data_file_path`：糖尿病数据 CSV 文件的路径。
  - `train_parquet_file_path`：保存预处理后的训练数据为 Parquet 文件的路径。
  - `test_parquet_file_path`：保存预处理后的测试数据为 Parquet 文件的路径。
- `dag=dag`：此参数指定了任务所属的 Airflow DAG。它将任务分配给脚本中先前创建的 DAG 对象（`dag`）。

下一个代码块与前面的类似，但它定义了一个名为 `train_task` 的不同任务：

```python
[In]: train_task = PythonOperator(
            task_id='train_tensorflow_model',
            python_callable=train_tensorflow_model,
            op_kwargs={
                'train_parquet_file_path': ("/home/ubuntu/airflow/dags"
                                            "/diabetes_train.parquet"),
                'model_save_path': ("/home/ubuntu/airflow/dags"
                                    "/diabetes_model.h5")
            },
            dag=dag,
        )
```

该任务将在 Airflow DAG 中执行带有指定参数的 `train_tensorflow_model` 函数。让我们分解如下：

- `PythonOperator`：这是 Airflow 库中的一个类，用于在 Airflow DAG 中执行 Python 函数作为任务。
- `task_id='train_tensorflow_model'`：这指定了任务的唯一标识符。在此情况下，其名称为 ‘train_tensorflow_model’。
- `python_callable=train_tensorflow_model`：此参数指定了操作员将执行的 Python 函数。在此处，它被设置为 `train_tensorflow_model`，表明 `train_tensorflow_model` 函数将被作为任务执行。
- `op_kwargs`：此参数指定了需要传递给 Python 函数（`train_tensorflow_model`）的关键字参数（kwargs）。它是一个包含 `train_tensorflow_model` 函数所需参数的字典：
  - `train_parquet_file_path`：预处理后的训练数据 Parquet 文件的路径。
  - `model_save_path`：保存训练好的 TensorFlow 模型文件的路径。
- `dag=dag`：此参数指定了任务所属的 Airflow DAG。它将任务分配给脚本中先前创建的 DAG 对象（`dag`）。

下一个代码块也与前面的类似，但它又定义了一个名为 `evaluate_task` 的任务：

```python
[In]: evaluate_task = PythonOperator(
     task_id='evaluate_model',
     python_callable=evaluate_model,
     op_kwargs={
         'test_parquet_file_path': ("/home/ubuntu/airflow/dags"
                                     "/diabetes_test.parquet"),
         'model_load_path': ("/home/ubuntu/airflow/dags"
                             "/diabetes_model.h5")
     },
     dag=dag,
)
```

此代码定义了一个任务（`evaluate_task`），它将在 Airflow DAG 中执行带有指定参数的 `evaluate_model` 函数。让我们分解代码的每个部分：

- `PythonOperator`：此类来自 Airflow 库，用于在 Airflow DAG 中执行 Python 函数作为任务。
- `task_id='evaluate_model'`：这指定了任务的唯一标识符。在此情况下，其名称为 'evaluate_model'。
- `python_callable=evaluate_model`：此参数指定了操作员将执行的 Python 函数。在此处，它被设置为 `evaluate_model`，表明 `evaluate_model` 函数将被作为任务执行。
- `op_kwargs`：此参数指定了需要传递给 Python 函数（`evaluate_model`）的关键字参数（kwargs）。它是一个包含 `evaluate_model` 函数所需参数的字典：
  - `test_parquet_file_path`：预处理后的测试数据 Parquet 文件的路径。
  - `model_load_path`：加载训练好的 TensorFlow 模型文件的路径。
- `dag=dag`：此参数指定了任务所属的 Airflow DAG。它将任务分配给脚本中先前创建的 DAG 对象（`dag`）。

## 步骤 5：定义任务依赖关系

在这个最后一步中，我们定义了任务之间的依赖关系：

```python
[In]: preprocess_task >> train_task >> evaluate_task
```

这行代码定义了 Airflow DAG 中的任务依赖关系：

- `preprocess_task >> train_task >> evaluate_task`：这一行指定了任务的执行顺序。它使用 `>>` 运算符来定义任务之间的依赖关系。
  - `preprocess_task`：此任务代表预处理步骤，必须在继续下一步之前完成。
  - `train_task`：此任务代表 TensorFlow 模型的训练。它依赖于预处理任务（`preprocess_task`）的完成。一旦预处理完成，训练即可开始。
  - `evaluate_task`：此任务代表 TensorFlow 模型的评估。它依赖于训练任务（`train_task`）的完成。一旦训练完成，即可评估模型。

这一步确保了任务按正确的顺序执行：先预处理数据，然后训练 TensorFlow 模型，最后评估其性能。它在 Airflow DAG 中建立了工作流。

要在 AWS EC2 实例上执行代码，我们首先激活了名为“myenv”的虚拟环境，以确保所需的依赖项可用。接下来，我们导航到目录



糖尿病预测的 DAG 位于此处。最后，我们在 Apache Airflow 中触发了名为 “diabetes_processing_and_training” 的 DAG，使用的命令如下：

```
[In]: source /home/ubuntu/myenv/bin/activate
[In]: cd /home/ubuntu/airflow/dags
[In]: airflow dags trigger diabetes_processing_and_training
```

DAG 生成的输出与在没有 DAG 的情况下运行主函数的输出非常相似，尽管由于训练和测试样本的随机选择过程存在差异，导致略有不同。

代码的第一个输出提供了 TensorFlow 糖尿病分类模型在训练过程中每十个迭代的损失值：

| Epoch | Loss |
|---|---|
| 10 | 0.6083 |
| 20 | 0.5830 |
| 30 | 0.5728 |
| 40 | 0.5623 |
| 50 | 0.5605 |
| 60 | 0.5589 |
| 70 | 0.5485 |
| 80 | 0.5469 |
| 90 | 0.5413 |
| 100 | 0.5332 |

第二个输出提供了基于测试数据的指标。它们共同提供了对训练后的模型在预测糖尿病结果方面的整体性能和有效性的洞察。更高的准确率、精确度、召回率和 F1 分数表明模型性能和预测能力更好：

| Metric | Value |
| :--- | :--- |
| Accuracy | 0.7436 |
| Precision | 0.6571 |
| Recall | 0.5610 |
| F1 Score | 0.6053 |

正如在第 7 章和前一小节中讨论的那样，结果表明性能不佳，凸显了提高模型有效性的潜在领域。这主要归因于数据集的受限和不平衡性质，以及潜在的数据质量问题。

## 综合所有内容

在本节中，我们整合了使用和不使用 Apache Airflow DAG 进行特斯拉股价和糖尿病预测的独立代码。

### 不使用 Airflow DAG 的特斯拉股价预测

在本小节中，我们展示了使用 main() 函数执行特斯拉股价预测算法的代码，即不使用 Airflow DAG：

模块 1: data_processing.py

```
[In]: from pyspark.sql import SparkSession

[In]: from pyspark.ml.feature import VectorAssembler, StandardScaler

[In]: from pyspark.sql import DataFrame
```

```
[In]: def load_data(file_path: str) -> DataFrame:
    """
    Load stock price data from a CSV file using SparkSession.
    """
    spark = SparkSession.builder \
        .appName("StockPricePrediction") \
        .getOrCreate()
    df = spark.read.csv(
        file_path,
        header=True,
        inferSchema=True
    )
    return df
```

```
[In]: def preprocess_data(df: DataFrame) -> DataFrame:
    """
    Preprocess the data by assembling feature vectors using
    VectorAssembler and scaling them using StandardScaler.
    """
    assembler = VectorAssembler(
        inputCols=['Open', 'High', 'Low', 'Volume'],
        outputCol='features'
    )
    df = assembler.transform(df)
        scaler = StandardScaler(
            inputCol="features",
            outputCol="scaled_features",
            withStd=True,
            withMean=True
        )
        scaler_model = scaler.fit(df)
        df = scaler_model.transform(df)
        df = df.select('scaled_features', 'Close')
        return df
```

模块 2: model_training.py

```
[In]: import torch
[In]: import torch.nn as nn
[In]: import torch.optim as optim
[In]: from torch.utils.data import DataLoader, TensorDataset

[In]: def create_data_loader(
            features,
            labels,
            batch_size=32
        ) -> DataLoader:
    """
    Convert the preprocessed data into PyTorch
    tensors and
    Create DataLoader objects for both the training
    and test
    sets.
    """
    dataset = TensorDataset(features, labels)
    return DataLoader(
        dataset,
        batch_size=batch_size,
        shuffle=True
    )
```

```
[In]: def train_model(
        model, train_loader, criterion, optimizer, num_epochs
    ):
        """
        Train the model on the training data using the
        DataLoader
        and the defined loss function and optimizer.
        Iterate over
        the data for a specified number of epochs,
        calculate the
        loss, and update the model parameters.
        """

        for epoch in range(num_epochs):
            for inputs, labels in train_loader:
                optimizer.zero_grad()
                outputs = model(inputs)
                loss = criterion(outputs, labels.
                                  unsqueeze(1))
                loss.backward()
                optimizer.step()

    print(
        f"Epoch [{epoch + 1}/{num_epochs}], "
        f"Loss: {loss.item():.4f}"
    )
```

模块 3: model_evaluation.py

```
[In]: import torch

[In]: def evaluate_model(model, test_loader, criterion):
    """
    Evaluate the trained model on the test data to
    assess its
    performance.
    Calculate the test loss and additional
    evaluation metrics
    such as the R-squared score.
    """
    with torch.no_grad():
        model.eval()
        predictions = []
        targets = []
        test_loss = 0.0
        for inputs, labels in test_loader:
            outputs = model(inputs)
            loss = criterion(outputs, labels.
            unsqueeze(1))
            test_loss += loss.item() * inputs.size(0)
            predictions.extend(outputs.squeeze().
            tolist())
            targets.extend(labels.tolist())

        test_loss /= len(test_loader.dataset)
        predictions = torch.tensor(predictions)
        targets = torch.tensor(targets)
        ss_res = torch.sum((targets - predictions) ** 2)
        ss_tot = torch.sum((targets - torch.
        mean(targets)) ** 2)
        r_squared = 1 - ss_res / ss_tot
        print(f"Test Loss: {test_loss:.4f}")
        print(f"R-squared Score: {r_squared:.4f}")
        return test_loss, r_squared.item()
```

模块 4: utils.py

```
[In]: import numpy as np
[In]: import torch
[In]: from typing import Tuple
[In]: from pyspark.sql import DataFrame

[In]: def spark_df_to_tensor(
        df: DataFrame
    ) -> Tuple[torch.Tensor, torch.Tensor]:
    """
    Converts Spark DataFrame columns to PyTorch tensors.
    """
    features = torch.tensor(
        np.array(
            df.rdd.map(lambda x: x.scaled_features.
                toArray())
                .collect()
        ),
        dtype=torch.float32
    )
    labels = torch.tensor(
        np.array(
            df.rdd.map(lambda x: x.Close).collect()
        ),
        dtype=torch.float32
    )
    return features, labels
```

模块 5: main.py

```
[In]: import logging
[In]: import torch
[In]: import torch.optim as optim
[In]: import torch.nn as nn
[In]: from torch.utils.data import DataLoader
[In]: from typing import Tuple
[In]: from pyspark.sql import DataFrame
[In]: from data_processing import load_data, preprocess_data
[In]: from model_training import create_data_loader, train_model
[In]: from model_evaluation import evaluate_model
[In]: import utils

[In]: logging.basicConfig(level=logging.INFO)
[In]: logger = logging.getLogger(__name__)

[In]: def main(
        data_file_path: str,
        num_epochs: int = 100,
        batch_size: int = 32,
        learning_rate: float = 0.001
    ):
        """
        Main function for training and evaluating a deep
        learning
        model for Tesla stock price prediction.

        Args:
            data_file_path (str):
                The path to the CSV file containing
                stock price
                data.
            num_epochs (int):
                The number of epochs for training the model.
                Defaults to 100.
            batch_size (int):
                The batch size for data loading during
                training.
                Defaults to 32.
            learning_rate (float):
                The learning rate for the optimizer.
                Defaults to
                0.001.

        Raises:
            FileNotFoundError: If the specified data
            file is not
            found.

        '''
        try:
            df = load_data(data_file_path)
            df = preprocess_data(df)
            train_df, test_df = df.randomSplit([0.8, 0.2],
            seed=42)
            train_features, train_labels = utils.spark_df_
            to_tensor(
                train_df
            )
            test_features, test_labels = utils.spark_df_
            to_tensor(
                test_df
            )
```





```python
train_loader = create_data_loader(
        train_features,
        train_labels,
        batch_size=batch_size
    )
    test_loader = create_data_loader(
        test_features,
        test_labels,
        batch_size=batch_size
    )

    input_size = train_features.shape[1]
    output_size = 1
    model = nn.Sequential(
        nn.Linear(input_size, 64),
        nn.ReLU(),
        nn.Linear(64, 32),
        nn.ReLU(),
        nn.Linear(32, 16),
        nn.ReLU(),
        nn.Linear(16, output_size)
    )

    criterion = nn.MSELoss()
    optimizer = optim.Adam(
        model.parameters(),
        lr=learning_rate
    )

    train_model(
        model,
        train_loader,
        criterion,
        optimizer, num_epochs
    )

    evaluate_model(model, test_loader, criterion)

    torch.save(model.state_dict(), 'trained_model.pth')

except FileNotFoundError:
    logger.error(f"Data file not found at {data_file_path}")

if __name__ == "__main__":
    data_file_path = "/home/ubuntu/airflow/dags/TSLA_stock.csv"
    main(data_file_path)
```

## 使用 Airflow DAG 预测特斯拉股价

在本小节中，我们展示了使用 Airflow DAG 执行特斯拉股价预测算法的代码。此代码取代了上一小节中讨论的 `main()` 函数。在分享代码之前，我们想补充一些关于在处理各种数据集时可以提高任务效率的注释。虽然为了简洁和清晰，这些技术并未在当前代码中实现，但它们对于在生产环境中优化和扩展工作流具有重要的参考价值。

首先，当处理在多个任务间共享的小型数据集时，使用广播变量（broadcast variables）可以提高效率。广播数据集允许在每个节点上缓存一份只读副本，从而减少网络流量并加快任务执行速度。如果相同的数据集将被用于多个任务（例如训练和评估），这将特别有用。

您可以使用一行代码来实现这一点：

```python
broadcast_df = sc.broadcast(df.collect())
```

其次，为了使 DAG 更加灵活和可扩展，您可以基于配置文件或参数生成动态 DAG。这种方法允许 DAG 通过定义数据集路径、模型配置和其他参数来适应不同的数据集或模型。这些配置可以在 YAML 或 JSON 文件中定义，然后在 DAG 定义中加载，以动态创建任务和工作流。

以下是一个加载配置文件的示例：

```python
import yaml

with open('/home/ubuntu/airflow/dags/config.yaml', 'r') as file:
    config = yaml.safe_load(file)
```

最后，为了防止模型训练过程中的中断，您可以实现模型检查点（model checkpoints）。这涉及定期保存模型的状态，以便在发生故障时可以从最后一个保存的检查点恢复训练。

基本步骤如下：

- 在训练期间保存检查点：

```python
torch.save({
         'model_state_dict': model.state_dict(),
         'optimizer_state_dict': optimizer.state_dict(),
         'epoch': epoch,
         'loss': loss
     }, checkpoint_path)
```

- 从检查点加载以恢复训练：

```python
checkpoint = torch.load(checkpoint_path)
model.load_state_dict(checkpoint['model_state_dict'])
optimizer.load_state_dict(checkpoint['optimizer_state_dict'])
```

这种方法确保了长时间运行的训练过程如果中断，可以从最后一个检查点继续，从而防止进度丢失。

以下是本章中用于使用 Airflow DAG 执行特斯拉股价预测算法的代码：

```python
from datetime import datetime, timedelta
from airflow import DAG
from airflow.operators.python_operator import PythonOperator
import logging
import torch
import torch.optim as optim
import torch.nn as nn
from torch.utils.data import DataLoader
import numpy as np
from pyspark.sql import DataFrame
from typing import Tuple
from utils import spark_df_to_tensor
from data_processing import load_data, preprocess_data
from model_training import create_data_loader, train_model
from model_evaluation import evaluate_model

data_file_path = "/home/ubuntu/airflow/dags/TSLA_stock.csv"
logging.basicConfig(level=logging.INFO)
logger = logging.getLogger(__name__)

default_args = {
    'owner': 'airflow',
    'depends_on_past': False,
    'start_date': datetime(2024, 5, 1),
    'email_on_failure': False,
    'email_on_retry': False,
    'retries': 1,
    'retry_delay': timedelta(minutes=5),
}

dag = DAG(
    'tesla_stock_prediction',
    default_args=default_args,
    description='DAG for Tesla stock price prediction',
    schedule_interval=None,
)

def preprocess_data_task():
    try:
        df = load_data(data_file_path)
        df = preprocess_data(df)
    except Exception as e:
        logger.error(f"Error in preprocessing data: {str(e)}")
        raise

preprocess_data_task = PythonOperator(
    task_id='preprocess_data_task',
    python_callable=preprocess_data_task,
    dag=dag,
)

def train_model_task():
    try:
        df = load_data(data_file_path)
        df = preprocess_data(df)
        train_df, test_df = df.randomSplit([0.8, 0.2], seed=42)
        train_features, train_labels = spark_df_to_tensor(train_df)
        train_loader = create_data_loader(
            train_features,
            train_labels,
            batch_size=32
        )
        
        input_size = train_features.shape[1]
        output_size = 1
        model = nn.Sequential(
            nn.Linear(input_size, 64),
            nn.ReLU(),
            nn.Linear(64, 32),
            nn.ReLU(),
            nn.Linear(32, 16),
            nn.ReLU(),
            nn.Linear(16, output_size)
        )
        criterion = nn.MSELoss()
        optimizer = optim.Adam(model.parameters(), lr=0.001)
        train_model(
            model,
            train_loader,
            criterion,
            optimizer,
            num_epochs=100
        )
    except Exception as e:
        logger.error(f"Error in training model: {str(e)}")
        raise

train_model_task = PythonOperator(
    task_id='train_model_task',
    python_callable=train_model_task,
    dag=dag,
)

def evaluate_model_task():
    try:
        df = load_data(data_file_path)
        df = preprocess_data(df)
        train_df, test_df = df.randomSplit([0.8, 0.2], seed=42)
        test_features, test_labels = spark_df_to_tensor(test_df)
        test_loader = create_data_loader(
            test_features,
            test_labels,
            batch_size=32
        )
        
        input_size = test_features.shape[1]
        output_size = 1
        model = nn.Sequential(
            nn.Linear(input_size, 64),
            nn.ReLU(),
            nn.Linear(64, 32),
            nn.ReLU(),
            nn.Linear(32, 16),
            nn.ReLU(),
            nn.Linear(16, output_size)
        )
        model.load_state_dict(torch.load('trained_model.pth'))
        
        criterion = nn.MSELoss()
        evaluate_model(model, test_loader, criterion)
    except Exception as e:
        logger.error(f"Error in evaluating model: {str(e)}")
        raise

evaluate_model_task = PythonOperator(
    task_id='evaluate_model_task',
    python_callable=evaluate_model_task,
    dag=dag,
)

preprocess_data_task >> train_model_task >> evaluate_model_task
```

## 不使用 Airflow DAG 的糖尿病预测

在本小节中，我们展示了使用 `main()` 函数执行糖尿病预测算法的代码：

模块 1：preprocessing.py

```python
from pyspark.sql import SparkSession
from pyspark.ml.feature import VectorAssembler, StandardScaler
import logging
from pyspark.sql.functions import col
logger = logging.getLogger(__name__)

def preprocess_data(
        data_file_path,
        train_parquet_file_path,
        test_parquet_file_path
    ):
        """
        Preprocess diabetes data.

        Args:
            data_file_path (str):
                Path to the diabetes data CSV file.
            train_parquet_file_path (str):
                Path to save the preprocessed training data.
            test_parquet_file_path (str):
                Path to save the preprocessed testing data.
        """
        try:
            spark = (SparkSession.builder
                     .appName("DiabetesProcessing")
                     .getOrCreate())
            diabetes_df = spark.read.csv(
                data_file_path,
                header=True,
            )
```





### 模块 1：preprocessing.py

```python
inferSchema=True.
)
diabetes_df = diabetes_df.filter(
	(col("Glucose") != 0)
	& (col("BloodPressure") != 0)
	& (col("BMI") != 0)
)
feature_cols = ["Pregnancies",
	"Glucose",
	"BloodPressure",
	"BMI",
	"DiabetesPedigreeFunction",
	"Age"]

assembler = VectorAssembler(
	inputCols=feature_cols,
	outputCol="features"
)

diabetes_df = assembler.transform(diabetes_df)
scaler = StandardScaler(
	inputCol="features",
	outputCol="scaled_features"
)
scaler_model = scaler.fit(diabetes_df)
diabetes_df = scaler_model.transform(diabetes_df)
train_df, test_df = diabetes_df.randomSplit(
	[0.8, 0.2],
	seed=42
)

train_df.write.parquet(
    train_parquet_file_path,
    mode="overwrite"
)

test_df.write.parquet(
    test_parquet_file_path,
    mode="overwrite"
)

logger.info(
    "数据预处理成功完成。")

except Exception as e:
    logger.error(
        f"预处理期间发生错误：{str(e)}")
```

## 模块 2：model_training.py

```python
import numpy as np
from pyspark.sql import SparkSession
from tensorflow.keras.models import Sequential
from tensorflow.keras.layers import Dense
from tensorflow.keras.optimizers import SGD
from tensorflow.keras.callbacks import Callback
import logging

logger = logging.getLogger(__name__)

class CustomCallback(Callback):
    """用于打印轮次信息的自定义回调。"""
    def on_epoch_end(self, epoch, logs=None):
        """在每个轮次结束时打印
轮次信息。"""
        if (epoch + 1) % 10 == 0:
            logger.info(
                f"轮次 [{(epoch + 1)}/{self.params['epochs']}], "
                f"损失：{logs['loss']:.4f}"
            )

def train_tensorflow_model(
        train_parquet_file_path,
        model_save_path
    ):
    """训练一个 TensorFlow 模型。

    参数：
        train_parquet_file_path (str):
            指向预处理后训练数据的路径。
        model_save_path (str):
            保存训练后模型的路径。
    """
    try:
        spark = (SparkSession.builder
                 .appName("TensorFlowTraining")
                 .getOrCreate())

        train_diabetes_df = spark.read.parquet(
            train_parquet_file_path
        )

        X_train = np.array(
            train_diabetes_df.select("scaled_features")
            .rdd.flatMap(lambda x: x)
            .collect()
        )
        y_train = np.array(
            train_diabetes_df.select("Outcome")
            .rdd.flatMap(lambda x: x)
            .collect()
        )

        model = Sequential()
        model.add(Dense(
            64,
            input_dim=X_train.shape[1],
            activation='relu'
        ))
        model.add(Dense(32, activation='relu'))
        model.add(Dense(1, activation='sigmoid'))

        optimizer = SGD(learning_rate=0.01)
        model.compile(
            loss='binary_crossentropy',
            optimizer=optimizer,
            metrics=['accuracy']
        )

        custom_callback = CustomCallback()
        model.fit(
            X_train,
            y_train,
            epochs=100,
            verbose=0,
            callbacks=[custom_callback]
        )
        model.save(model_save_path)

        logger.info("模型训练成功完成。")
    except Exception as e:
        logger.error(
            f"模型训练期间发生错误：{str(e)}"
        )
```

### 模块 3：model_evaluation.py

```python
import numpy as np
from pyspark.sql import SparkSession
from sklearn.metrics import accuracy_score, precision_score, recall_score, f1_score
from tensorflow.keras.models import load_model
import logging

logger = logging.getLogger(__name__)

def evaluate_model(
        test_parquet_file_path,
        model_load_path
    ):
    """
    评估一个 TensorFlow 模型。

    参数：
        test_parquet_file_path (str):
            指向预处理后测试数据的路径。
        model_load_path (str):
            加载训练后模型的路径。
    """
    try:
        spark = SparkSession.builder \
            .appName("ModelEvaluation") \
            .getOrCreate()

        model = load_model(model_load_path)

        test_diabetes_df = spark.read.parquet(
            test_parquet_file_path
        )

        X_test = np.array(
            test_diabetes_df.select("scaled_features")
            .rdd.flatMap(lambda x: x)
            .collect()
        )

        y_test = np.array(
            test_diabetes_df.select("Outcome")
            .rdd.flatMap(lambda x: x)
            .collect()
        )

        y_pred = (model.predict(X_test) > 0.5).astype(int)

        accuracy = accuracy_score(y_test, y_pred)
        precision = precision_score(y_test, y_pred)
        recall = recall_score(y_test, y_pred)
        f1 = f1_score(y_test, y_pred)

        logger.info(f"准确率：{accuracy:.4f}")
        logger.info(f"精确率：{precision:.4f}")
        logger.info(f"召回率：{recall:.4f}")
        logger.info(f"F1 分数：{f1:.4f}")
    except Exception as e:
        logger.error(
            f"模型评估期间发生错误：{str(e)}"
        )
```

### 模块 4：main.py

```python
import logging
from preprocessing import preprocess_data
from model_training import train_tensorflow_model
from model_evaluation import evaluate_model

logging.basicConfig(level=logging.INFO)
logger = logging.getLogger(__name__)

def main():
    preprocess_data(
        "/home/ubuntu/airflow/dags/diabetes.csv",
        "/home/ubuntu/airflow/dags/diabetes_train.parquet",
        "/home/ubuntu/airflow/dags/diabetes_test.parquet"
    )
    logger.info("数据预处理完成。")
    train_tensorflow_model(
        "/home/ubuntu/airflow/dags/diabetes_train.parquet",
        "/home/ubuntu/airflow/dags/diabetes_model.h5"
    )
    logger.info("模型训练完成。")
    evaluate_model(
        "/home/ubuntu/airflow/dags/diabetes_test.parquet",
        "/home/ubuntu/airflow/dags/diabetes_model.h5"
    )
    logger.info("模型评估完成。")

if __name__ == "__main__":
    main()
```

## 使用 Airflow DAG 进行糖尿病预测

在本小节中，我们展示了使用 Airflow DAG 执行糖尿病预测算法的代码。这取代了上一小节中讨论的 `main()` 函数：

```python
from datetime import datetime, timedelta
from airflow import DAG
from airflow.operators.python_operator import PythonOperator
from preprocessing import preprocess_data
from model_training import train_tensorflow_model
from model_evaluation import evaluate_model

default_args = {
    'owner': 'airflow',
    'depends_on_past': False,
    'start_date': datetime(2024, 2, 25),
    'email_on_failure': False,
    'email_on_retry': False,
    'retries': 1,
    'retry_delay': timedelta(minutes=5),
}

dag = DAG(
    'diabetes_processing_and_training',
    default_args=default_args,
    description=('使用 PySpark 处理糖尿病数据 '
                 '并训练 TensorFlow 模型'),
    schedule_interval=None,
)

preprocess_task = PythonOperator(
    task_id='preprocess_data',
    python_callable=preprocess_data,
    op_kwargs={
        'data_file_path': ('/home/ubuntu/airflow/dags/diabetes.csv'),
        'train_parquet_file_path': ('/home/ubuntu/airflow/dags/diabetes_train.parquet'),
        'test_parquet_file_path': ('/home/ubuntu/airflow/dags/diabetes_test.parquet')
    },
    dag=dag,
)

train_task = PythonOperator(
    task_id='train_tensorflow_model',
    python_callable=train_tensorflow_model,
    op_kwargs={
        'train_parquet_file_path': ('/home/ubuntu/airflow/dags/diabetes_train.parquet'),
        'model_save_path': ('/home/ubuntu/airflow/dags/diabetes_model.h5')
    },
    dag=dag,
)
```





# 摘要

  在本章中，我们演示了如何使用 Apache Airflow 构建可扩展的数据处理流水线。我们创建了完整的 AWS 工作流，该工作流包括使用 PySpark 对数据进行预处理，使用 PyTorch 和 TensorFlow 开发深度学习模型，以及使用 Airflow 在 AWS 上运行代码以处理回归和分类任务。此外，我们通过使代码模块化增强了其功能，并展示了如何在不使用 Apache Airflow DAG 和使用 Apache Airflow DAG 两种情况下运行该代码。

  在下一章中，我们将深入探讨用于增强深度学习模型性能的先进技术。主题将包括处理过拟合、实施正则化技术（如 dropout）、采用早停策略以及微调模型以提高准确性和效率。

# 第 9 章

# 提高模型性能的技术

在之前的章节中，我们使用默认参数训练和评估了模型，且没有尝试提高其性能。在本章中，我们将考察各种提高深度学习模型性能的技术。实现一个能很好地泛化到未见过的数据的模型是机器学习中的一个关键目标。过拟合是一个常见问题，它发生在模型在训练数据上表现良好但在验证集或测试集上表现不佳时。

我们将探讨解决过拟合的技术，包括 dropout、早停以及 L1 和 L2 正则化，这些技术通过对模型的参数施加约束来防止过拟合。Dropout 涉及在训练过程中随机“丢弃”（即设为零）一部分神经元，这有助于防止网络过于依赖特定神经元，并鼓励网络更好地泛化。早停涉及在训练过程中监控模型在验证集上的表现，一旦性能停止提升就停止训练过程。

L1 和 L2 正则化向用于训练模型的损失函数中添加惩罚项。L1 正则化（在线性模型中被称为 Lasso）将权重的绝对值添加到损失函数中，鼓励稀疏性。在神经网络中，这鼓励权重稀疏，导致更少的连接和潜在的更简单的模型。L2 正则化（在线性模型中被称为 Ridge）将权重的平方值添加到损失函数中，鼓励整体上较小的权重。在神经网络中，L2 正则化通过惩罚大权重来帮助防止过拟合，尽管与 L1 正则化相比，其对稀疏性的影响可能不那么明显。

此外，我们将涵盖超参数优化，包括微调学习率和网络架构，以识别在验证集上表现最好的模型。这将手动完成，也可以使用 Keras Tuner 自动完成。

本章首先考察基准模型，该模型将作为比较正则化和超参数微调结果的基准。然后我们将详细探讨每项技术：dropout、早停、L1 和 L2 正则化、学习率调整以及通过改变层数和神经元数量来修改模型容量。在将本章使用的代码整合到一个统一部分之前，我们将演示如何使用 Keras Tuner 进行自动超参数优化。本章最后以一个强调关键要点的部分结束。

## 基准模型

我们从一个基准神经网络模型架构开始，该架构与第 5 章中用于预测特斯拉股价的 TensorFlow 模型保持一致，但为了符合当前章节的目标进行了一些修改。该模型由多个具有 ReLU 激活函数的全连接层组成，后接一个输出层。该模型作为我们实施正则化技术（dropout、早停、L1 和 L2 正则化）和微调增强的起点。

脚本以导入必要的库开始：

- **logging**：用于记录信息和错误
- **numpy**：用于数值操作
- **tensorflow**：用于构建和训练神经网络
- **pyspark.sql**：用于处理 Spark DataFrame
- **pyspark.ml.feature**：用于特征转换
- **sklearn.metrics**：用于计算 R2 分数
- **matplotlib.pyplot**：用于绘制训练损失

```python
[In]: import logging
[In]: import numpy as np
[In]: import tensorflow as tf
[In]: from pyspark.sql import SparkSession
[In]: from pyspark.ml.feature import VectorAssembler, StandardScaler
[In]: from sklearn.metrics import r2_score
[In]: from tensorflow.keras.models import Sequential
[In]: from tensorflow.keras.layers import Dense
[In]: import matplotlib.pyplot as plt
```

接下来，我们定义 TLSARegressor 类，该类封装了数据预处理、模型训练和评估的整个过程。该类以一个 init 方法开始，该方法用于初始化 TLSARegressor 对象。此方法设置了一个日志记录器，初始化一个 Spark 会话，并定义了 input_shape 和 model 属性以供后续使用：

```python
[In]: class TSLARegressor:
    """
    用于特斯拉股价回归的类。
    """
    def __init__(self):
        """
        初始化 TSLARegressor 对象。
        """
        self.logger = logging.getLogger(__name__)
        self.spark = SparkSession.builder \
                .appName("TSLA_Regression") \
                .getOrCreate()
        self.input_shape = None
        self.model = None
```

继续类内部的内容，我们有 preprocess_data 方法。该方法通过读取 CSV 文件到 Spark DataFrame 中，将特征列组装成单个向量列，使用 StandardScaler 对特征进行缩放，并根据 train_ratio 将数据划分为训练集和测试集来预处理输入数据：

```python
[In]: def preprocess_data(
        self,
        file_path,
        feature_cols=['Open', 'High', 'Low', 'Volume'],
        train_ratio=0.8,
        seed=42
    ):
        """
        预处理数据。
```

参数：

- file_path (str)：CSV 文件的路径。
- feature_cols (list)：特征列列表。
- train_ratio (float)：训练数据比例。
- seed (int)：用于划分数据的随机种子。

返回值：

- tuple：包含训练和测试 DataFrame 的元组。

```python
        """
        df = self.spark.read.csv(
            file_path,
            header=True,
            inferSchema=True
        )
        assembler = VectorAssembler(
            inputCols=feature_cols, outputCol='features')
        df = assembler.transform(df)
        scaler = StandardScaler(
            inputCol='features',
            outputCol='scaled_features',
            withMean=True,
            withStd=True
        )
        scaler_model = scaler.fit(df)
        df = scaler_model.transform(df)
        train_df, test_df = df.randomSplit(
            [train_ratio, 1-train_ratio],
            seed=seed
        )
        return train_df, test_df
```





## 第 9 章 提高模型性能的技巧

```python
scaler = StandardScaler(
    inputCol='features',
    outputCol='scaled_features',
    withMean=True,
    withStd=True
)
scaler_model = scaler.fit(df)
df = scaler_model.transform(df)
train_df, test_df = df.randomSplit(
    [train_ratio, 1-train_ratio],
    seed=seed
)
return train_df, test_df
```

接下来，我们有 `convert_to_numpy` 方法，该方法通过从 Spark DataFrame 中提取并收集缩放后的特征和标签到 NumPy 数组，从而将 Spark DataFrame 转换为 NumPy 数组：

```python
def convert_to_numpy(self, train_df, test_df):
    """
    将 Spark DataFrame 转换为 numpy 数组。

    参数:
        - train_df (DataFrame):
            包含训练数据的 Spark DataFrame。
        - test_df (DataFrame):
            包含测试数据的 Spark DataFrame。

    返回:
        - tuple:
            包含特征和标签的
            训练集和测试集 numpy
            数组的元组。
    """
    train_features = np.array(
        train_df.select('scaled_features')
            .rdd.map(lambda x: x.scaled_features.toArray())
        .collect()
    )
    train_labels = np.array(
        train_df.select('Close')
            .rdd.map(lambda x: x.Close).collect()
    )
    test_features = np.array(
        test_df.select('scaled_features')
            .rdd.map(lambda x: x.scaled_features.toArray())
        .collect()
    )
    test_labels = np.array(
        test_df.select('Close')
            .rdd.map(lambda x: x.Close).collect()
    )
    return (train_features,
        train_labels,
        test_features,
        test_labels
    )
```

过渡到下一个方法，我们有 `create_and_train_model` 方法，该方法用于创建并训练神经网络模型：

- 定义一个具有多个全连接层（Dense layers）的顺序神经网络模型
- 使用 Adam 优化器和均方误差（Mean Squared Error）损失函数编译模型
- 在训练数据上训练模型

```python
def create_and_train_model(
    self,
    train_features,
    train_labels,
    epochs=100,
    batch_size=32
):    
    """
    创建并训练神经网络模型。

    参数:
    - train_features (ndarray): 训练特征。
    - train_labels (ndarray): 训练标签。
    - epochs (int): 训练的轮数。
    - batch_size (int): 训练的批量大小。

    返回:
    - History:
    包含每个
    轮次的损失值的
    训练历史记录。
    """
    self.input_shape = (train_features.shape[1],)
    self.model = Sequential([
        Dense(
            64,
            activation='relu',
            input_shape=self.input_shape
        ),
        Dense(
            32,
            activation='relu'
        ),
        Dense(
            16,
            activation='relu'
        ),
        Dense(1)
    ])
    self.model.compile(optimizer='adam', loss='mse')
    history = self.model.fit(
        train_features,
        train_labels,
        epochs=epochs,
        batch_size=batch_size,
        verbose=0
    )
    return history
```

继续进入下一步，我们有 `evaluate_model` 方法。该方法通过使用模型的 `evaluate` 方法计算测试损失，从而在测试数据上评估训练好的模型：

```python
def evaluate_model(self, test_features, test_labels):
    """
    评估训练好的模型。

    参数:
        - test_features (ndarray): 测试特征。
        - test_labels (ndarray): 测试标签。

    返回:
        - float: 测试损失。
    """
    test_loss = self.model.evaluate(
        test_features,
        test_labels
    )
    return test_loss
```

继续下一个方法，我们有 `predict_and_evaluate` 方法，该方法通过以下方式在测试数据上预测特斯拉（Tesla）股价并评估模型：

- 对测试特征进行预测
- 计算 R2 分数以评估模型的性能

```python
def predict_and_evaluate(
        self,
        test_features,
        test_labels
    ):
    """
    预测并评估神经网络模型。

    参数:
        - test_features (ndarray): 测试特征。
        - test_labels (ndarray): 测试标签。

    返回:
        - float: R2 分数。
    """
    test_predictions = self.model.predict(test_features)
    r2_score_value = r2_score(test_labels, test_predictions)
    return r2_score_value
```

在下一步中，我们过渡到主函数，该函数协调整个工作流。该函数位于 `TSLARegressor` 类之外，它实例化一个 `TSLARegressor` 对象，然后调用方法来预处理数据、将数据转换为 NumPy 数组、创建并训练模型，以及评估模型。它还记录测试损失和 R2 分数，并使用 Matplotlib 绘制每轮的训练损失：

```python
def main(file_path):
    """
    协调整个工作流的主函数。

    参数:
        - file_path (str): CSV 文件的路径。

    返回:
        - None
    """
    try:
        tsla_regressor = TSLARegressor()
        train_df, test_df = tsla_regressor.preprocess_data(
            file_path
        )
        train_features, train_labels, test_features, \
        test_labels = tsla_regressor.convert_to_numpy(
            train_df,
            test_df
        )
        history = tsla_regressor.create_and_train_model(
            train_features,
            train_labels
        )
        test_loss = tsla_regressor.evaluate_model(
            test_features,
            test_labels
        )
        r2_score_value = tsla_regressor.predict_and_evaluate(
            test_features,
            test_labels
        )

        logging.info("Test Loss: {}".format(test_loss))
        logging.info("R2 Score: {}".format(r2_score_value))

        plt.plot(history.history['loss'])
        plt.title('Model Loss')
        plt.xlabel('Epoch')
        plt.ylabel('Loss')

        plt.show()

    except Exception as e:
        logging.error(f"An error occurred: {e}")
```

在最后一步，我们有主函数，它作为脚本工作流的入口点：

```python
if __name__ == "__main__":
    logging.basicConfig(level=logging.INFO)
    file_path = "/home/ubuntu/airflow/dags/TSLA_stock.csv"
    main(file_path)
```

该函数配置日志级别为 INFO，定义 CSV 数据的文件路径，并在脚本作为主模块执行时，使用文件路径调用 main 函数。

函数的执行流程如下：

- 数据预处理：读取并处理 CSV 数据，缩放特征，并将其拆分为训练集和测试集
- 数据转换：将 Spark DataFrame 转换为 NumPy 数组，以便与 TensorFlow 兼容
- 模型训练：创建神经网络模型，在训练数据上训练它，并记录训练损失
- 模型评估：在测试数据上评估训练好的模型，并计算 R2 分数
- 日志记录和绘图：记录评估指标并绘制训练损失

要使用 Python 3 从 `/home/ubuntu/airflow/dags` 目录运行脚本，并考虑到名为 `myenv` 的虚拟环境，我们遵循了以下步骤：

激活名为 `myenv` 的虚拟环境：

```bash
source /path/to/myenv/bin/activate
```

更改目录到 `/home/ubuntu/airflow/dags`：

```bash
cd /home/ubuntu/airflow/dags
```

使用 Python 3 运行脚本，指定脚本名称 `predict_tsla_stock.py`：

```bash
python3 predict_tsla_stock.py
```

此命令使用 Python 3 从 `/home/ubuntu/airflow/dags` 目录执行 `predict_tsla_stock.py` 脚本。

代码作为整个 TSLA 股价回归工作流的一部分，产生两个主要输出。第一个输出是评估指标（测试损失和 R2 分数），使用 `logging.info` 方法打印：

```python
logging.info("Test Loss: {}".format(test_loss))
logging.info("R2 Score: {}".format(r2_score_value))
```

以下是输出：

```text
Test Loss: 15.5924
R2 Score: 0.9987
```

测试损失使用 `evaluate_model` 方法计算并记录：

```python
test_loss = tsla_regressor.evaluate_model(
    test_features, test_labels
)
```

R2 分数使用 `predict_and_evaluate` 方法计算并记录：

```python
r2_score_value = tsla_regressor.predict_and_evaluate(
    test_features, test_labels
)
```

相对较低的测试损失（15.5924）和非常高的 R2 分数（0.9987）的组合表明模型在测试数据上表现非常出色。低测试损失表明预测值接近实际值，而高 R2 分数表明模型解释了数据中几乎所有的变异性。





第二个输出是训练损失随 epoch 变化的绘图，该图保存为 `model_loss_plot.png`，使用以下代码：

```python
[In]: plt.plot(history.history['loss'])
[In]: plt.title('Model Loss')
[In]: plt.xlabel('Epoch')
[In]: plt.ylabel('Loss')
[In]: plt.axvline(
    x=10,
    color='r',
    linestyle='--',
    label='Epoch 10 plateau'
    )
[In]: plt.savefig('model_loss_plot.png')
[In]: plt.show()
```

训练历史，包含每个 epoch 的损失值，是由 `create_and_train_model` 方法返回并用于绘制损失曲线的：

```python
[In]: history = tsla_regressor.create_and_train_model(
    train_features,
    train_labels
    )
```

该绘图如图 9-1 所示。

![](img/1c89d4486f90c87568fa6a42d46ae02a_612_0.png)

**图 9-1. 模型损失**

训练损失图显示在第 10 个 epoch 之后是一条水平线（用虚线垂直线标出），表明训练损失值不再进一步降低，而是保持相对恒定。这通常意味着模型学习已达到平台期。

这可能意味着以下几点：

- 模型已收敛到一个局部最小值，意味着它找到了一组权重，进一步训练不会显著降低损失。
- 学习率可能太低，无法逃离局部最小值；或者它可能恰好合适，表明模型已从数据中充分学习。
- 模型从给定数据中学习的能力可能已经饱和，意味着考虑到其架构和超参数，它已经从训练数据中学到了能学的极限。

换言之，当前的性能水平很可能是该模型在现有架构、训练数据和超参数下所能达到的最佳状态。或者，这可能表明存在过拟合，意味着模型过于紧密地拟合训练数据，可能无法很好地泛化到未见过数据。

在本案例中，由于模型在验证集上的表现令人满意，训练损失的平台期可能表明模型在训练数据上的学习过程已趋于稳定。由于损失值较低且模型在验证数据上表现良好（由较低的测试损失和较高的 R2 分数判断），这可以是训练成功的标志。

在生产环境中，当怀疑模型存在过拟合时，通常会采取以下措施：

- **审查平台期：** 确认训练损失和验证损失是否都已进入平台期，这可以通过绘制两条损失曲线来可视化。
- **调整超参数：** 尝试不同的学习率、批大小或训练时长。
- **简化模型：** 如果模型似乎过拟合，考虑通过减少层数或神经元数量来简化模型架构。或者，如果模型似乎欠拟合，考虑使用更深或更复杂的架构。
- **数据增强：** 使用数据增强技术来人工增加训练数据集的大小和多样性。
- **正则化：** 实施或调整正则化技术，如 dropout、L1 正则化、L2 正则化或早停，以防止过拟合。

在本章其余部分，我们将通过一个使用 TensorFlow 预测特斯拉股票价格的例子，来探讨如何实施这些策略中的一些。

## 早停（Early Stopping）

早停涉及在训练期间监控模型在验证集上的表现，并在性能开始下降时停止训练过程。这通过防止模型开始记忆数据中的噪声之前就停止训练，从而避免模型对训练数据过拟合。

为了在我们的基线模型训练过程中添加早停，我们需要修改 `create_and_train_model` 方法。具体来说，我们需要添加一个早停回调（callback），用于监控某个指标（例如损失），并在监控指标在特定数量的 epoch 内没有改进时停止训练。

以下是我们如何修改 `create_and_train_model` 方法以包含早停机制：

```python
[In]: from tensorflow.keras.callbacks import EarlyStopping

[In]: def create_and_train_model(
         self,
         train_features,
         train_labels,
         epochs=100,
         batch_size=32
     ):
    self.input_shape = (train_features.shape[1],) 
    self.model = Sequential([ 
        Dense( 
            64, 
            activation='relu', 
            input_shape=self.input_shape 
        ), 
        Dense( 
            32, 
            activation='relu' 
        ), 
        Dense( 
            16, 
            activation='relu' 
        ), 
        Dense(1) 
    ]) 

    early_stopping = EarlyStopping( 
        monitor='val_loss', 
        patience=10, 
        restore_best_weights=True 
    ) 

    self.model.compile(optimizer='adam', loss='mse') 
    history = self.model.fit( 
        train_features, 
        train_labels, 
        epochs=epochs, 
        batch_size=batch_size, 
        verbose=0,
        callbacks=[early_stopping], 
        validation_split=0.2 
    ) 
    return history
```

在以上修改中：

- 我们从 `tensorflow.keras.callbacks` 导入了 `EarlyStopping` 回调。
- 我们实例化了一个 `EarlyStopping` 回调，参数如下：
    - `monitor='val_loss'`：它监控验证损失。
    - `patience=10`：如果监控指标没有改进，它等待 10 个 epoch 后再停止。
    - `restore_best_weights=True`：它恢复具有最佳验证损失的 epoch 的模型权重。
- 我们将 `early_stopping` 回调添加到 `fit` 方法的 `callbacks` 参数列表中。
- 我们在 `fit` 方法中包含了 `validation_split=0.2` 参数，指定在训练期间应使用 20% 的训练数据进行验证。这是早停回调监控验证损失所必需的。

运行包含此修改的基线模型后，我们得到的第一个输出是以下早停信息：

```
[Out]: Epoch 87: early stopping
[Out]: Restoring model weights from the end of the best epoch: 77
[Out]: Epochs completed: 87
```

以下是对此输出的解释：

- **[Epoch 87: early stopping]** 意味着早停被激活，因为验证指标在指定的耐心期（patience period）内没有改进。耐心期是指在停止训练前，等待验证指标改进的 epoch 数量。例如，耐心期为 10 个 epoch 意味着如果验证指标连续 10 个 epoch 没有改进，训练将停止。
- **[Restoring model weights from the end of the best epoch: 77]** 意味着最佳模型（具有最低验证损失或最高验证 R 方分数）是在第 77 个 epoch 找到的。模型权重已从该 epoch 恢复。恢复权重意味着将模型恢复到指定 epoch 时的状态，确保用于进一步评估的模型参数是产生最佳验证性能的那些参数。
- **[Epochs completed: 87]** 意味着完成了 87 个 epoch，包括耐心期（即 10 个耐心期 + 77），随后触发了早停。

第二个输出是早停点时的损失和 R 方分数：

```
[Out]: Loss at early stopping point: 16.40
[Out]: R2 score at early stopping point: 0.9986
```

这意味着在早停点，损失值为 16.40，R2 分数为 0.9986。

最后，一旦选中最佳模型（在早停之后），代码会在测试集上评估该模型，以获取其在未见过数据上性能的无偏估计：

```
[Out]: Test Loss: 15.21
[Out]: R2 Score: 0.9987
```

这意味着使用测试数据集，模型达到了 15.21 的损失值和 0.9987 的 R2 分数。

## Dropout

Dropout 是一种技术，其中随机选择的神经元在训练过程中以一定概率被忽略。这有助于防止神经元的共适应（co-adaptation），并迫使网络学习更鲁棒的特征。Dropout 有效地模拟了同时训练具有不同架构的多个神经网络。

为了在我们的基线神经网络模型中添加 dropout 层，我们需要修改定义模型架构的代码部分。具体来说，我们将在 `create_and_train_model` 方法中密集层之间插入 dropout 层。Dropout 层通过在训练期间每次更新时随机将一部分输入单元设为 0 来帮助防止过拟合，这对正则化有益。

以下是添加了 dropout 层的修改后 `create_and_train_model` 方法：

```python
[In]: from tensorflow.keras.layers import Dropout

[In]: def create_and_train_model(
            self,
            train_features,
            train_labels,
```





```python
epochs=100,
batch_size=32
):
    self.input_shape = (train_features.shape[1],)
    self.model = Sequential([
        Dense(
            64,
            activation='relu',
            input_shape=self.input_shape
        ),
        Dropout(0.5),
        Dense(
            32,
            activation='relu'
        ),
        Dropout(0.5),
        Dense(
            16,
            activation='relu'
        ),
        Dropout(0.5),
        Dense(1)
    ])
    self.model.compile(optimizer='adam', loss='mse')
    history = self.model.fit(
        train_features,
        train_labels,
        epochs=epochs,
        batch_size=batch_size,
        verbose=0
    )
    return history
```

我们对基准模型进行了以下修改：

- 在文件开头添加了 `from tensorflow.keras.layers import Dropout`。
- 在模型架构的全连接层之间引入了 `Dropout(0.5)` 层。Dropout 率设置为 0.5，这意味着在训练过程中，前一个全连接层输出的 50% 将被随机丢弃。根据所需的正则化程度，此比率可以调整为其他值（例如 0.2 或 0.3）。

在应用上述 Dropout 修改运行基准模型后，我们得到了以下输出：

- 测试损失：72.67
- R2 分数：0.9939

0.5 的 Dropout 率并不罕见，但在某些情况下可能过于激进。Dropout 率通常介于 0.2 到 0.5 之间，具体取决于模型和数据的具体需求及特征。

使用 0.2 的 Dropout 率运行模型后，我们得到了以下输出：

- 测试损失：41.8448
- R2 分数：0.9965

尽管与 0.5 的 Dropout 率相比，在 0.2 的 Dropout 率下我们看到了指标的提升（更低的损失和更高的 R2 分数），但在生产环境中，我们通常通过比较训练指标和测试指标来检查模型是否存在欠拟合或过拟合。如果模型欠拟合（即在训练数据和测试数据上的表现都较差），Dropout 可能过于激进，降低其比率可能有所帮助。如果模型过拟合（即在训练数据上表现良好，但在测试数据上表现较差），我们可能需要更多的 Dropout。

## L1 和 L2 正则化

L1 和 L2 正则化技术根据模型参数的大小在损失函数中引入一个惩罚项。L1 正则化包含参数的绝对值，而 L2 正则化涉及参数的平方值。这促使模型保持较小的参数值，从而缓解过拟合。

要将 L1 和 L2 正则化整合到基准神经网络模型中，我们必须调整 `create_and_train_model` 方法。具体来说，需要在模型架构中定义全连接层的地方添加正则化。

以下是更新了 L1 正则化的 `create_and_train_model` 方法：

```python
from tensorflow.keras.regularizers import l1

def create_and_train_model(
    self,
    train_features,
    train_labels,
    epochs=100,
    batch_size=32
):
    self.input_shape = (train_features.shape[1],)
    self.model = Sequential([
        Dense(
            64,
            activation='relu',
            kernel_regularizer=l1(0.01),
            input_shape=self.input_shape
        ),
        Dense(
            32,
            activation='relu',
            kernel_regularizer=l1(0.01)
        ),
        Dense(
            16,
            activation='relu',
            kernel_regularizer=l1(0.01)
        ),
        Dense(1)
    ])
    self.model.compile(optimizer='adam', loss='mse')
    history = self.model.fit(
        train_features,
        train_labels,
        epochs=epochs,
        batch_size=batch_size,
        verbose=0
    )
    return history
```

在此修改中，我们在基准模型中添加以下内容：

- `from tensorflow.keras.regularizers import l1`
- 在每个全连接层的定义中，我们添加了 `kernel_regularizer` 参数并将其设置为 `l1(0.01)`。这将对每个全连接层的权重应用 L1 正则化，正则化强度为 0.01。此值提供适中的正则化效果。它通常被选为起点，并根据训练过程中的模型表现进行调整。典型值范围从 0.001 到 0.1，并根据模型训练期间的经验观察进行调整。

要添加 L2 正则化，我们可以采用类似的方法，但使用 Keras 中的 `l2` 函数：

```python
from tensorflow.keras.regularizers import l2

def create_and_train_model(
    self,
    train_features,
    train_labels,
    epochs=100,
    batch_size=32
):
    self.input_shape = (train_features.shape[1],)
    self.model = Sequential([
        Dense(
            64,
            activation='relu',
            kernel_regularizer=l2(0.01),
            input_shape=self.input_shape
        ),
        Dense(
            32,
            activation='relu',
            kernel_regularizer=l2(0.01)
        ),
        Dense(
            16,
            activation='relu',
            kernel_regularizer=l2(0.01)
        ),
        Dense(1)
    ])
    self.model.compile(optimizer='adam', loss='mse')
    history = self.model.fit(
        train_features,
        train_labels,
        epochs=epochs,
        batch_size=batch_size,
        verbose=0
    )
    return history
```

在此修改中，我们在基准模型中添加以下内容：

- `from tensorflow.keras.regularizers import l2`
- 在每个全连接层的定义中，我们添加了 `kernel_regularizer` 参数并将其设置为 `l2(0.01)`。这将对每个全连接层的权重应用 L2 正则化，正则化强度为 0.01。我们可以根据需要调整正则化强度。

在将 L1 和 L2 正则化技术整合到基准 TensorFlow 模型后，我们评估了具有不同正则化强度的模型性能。输出提供了不同正则化强度如何影响模型性能指标（特别是测试损失和 R2 分数）的见解。

当应用强度为 0.01 的 L1 正则化时，我们得到以下结果：

- 测试损失：20.1664
- R2 分数：0.9988

与基准模型值相比，我们观察到测试损失适度增加，R2 分数略微下降：

- 测试损失（基准）：15.5924
- R2 分数（基准）：0.9987

这种增加表明 L1 正则化并未显著改善模型的泛化能力，这表明模型很可能没有过拟合。然而，R2 分数保持在 0.9987 的高位，表明即使有正则化，模型也保留了其预测能力。

值得注意的是，观察到的性能指标值可能会受到模型权重随机初始化和数据采样变化等因素的影响，在比较基准和正则化结果时应考虑这些因素。

将 L1 正则化强度增加到 0.1 导致测试损失产生更明显的影响：

- 测试损失：61.8990
- R2 分数：0.9989

这种增加表明，更强的 L1 正则化导致模型拟合训练数据的能力降低，可能表明存在轻微的欠拟合。然而，R2 分数保持在 0.9989 的相对较高水平，表明模型仍然捕捉到了数据中方差的大部分。

另一方面，应用强度为 0.01 的 L2 正则化导致测试损失略低于 L1 正则化：

- 测试损失：19.9371
- R2 分数：0.9988

这表明与 L1 正则化相比，L2 正则化在缓解过拟合（如果存在）方面略有帮助。同样，R2 分数保持在 0.9988 的高位，表明模型保持了其预测性能。

将 L2 正则化强度增加到 0.1 导致测试损失与使用较高 L1 正则化强度获得的结果相似：

- 测试损失：61.4426
- R2 分数：0.9989

在过拟合的模型中，这表明较强的 L2 正则在减少过拟合方面具有与较强 L1 正则化相似的效果。尽管正则化强度较高，R2 分数仍保持在 0.9989 的高位，表明模型仍然保持其预测能力。

总体而言，输出展示了正则化强度与模型性能之间的权衡。虽然较强的正则化有助于防止过拟合并改善泛化能力，但过强的正则化可能导致欠拟合和预测性能的下降。因此，根据数据集的具体特征以及偏差与方差之间期望的平衡，选择合适的正则化强度至关重要。




# 学习率

学习率是训练深度学习模型时的一个关键超参数。它决定了在向损失函数最小值移动过程中每次迭代的步长。选择合适的学习率会显著影响模型的性能和收敛速度。

如果学习率过低，优化算法可能会收敛得非常慢，或者陷入局部最小值。另一方面，如果学习率过高，算法可能会在最小值附近振荡而无法收敛，这会阻止模型达到最佳性能。

要尝试在我们的神经网络模型中使用不同的学习率，我们应该在 `create_and_train_model` 方法中编译模型时修改优化器参数。默认情况下，TensorFlow 的 Adam 优化器使用 0.001 的学习率。然而，调整学习率会对模型的训练过程和收敛产生显著影响。

因此，我们可以自定义学习率以满足特定需求并提高模型性能。

以下是包含自定义学习率修改的基础代码的相关部分：

```python
[In]: from tensorflow.keras.optimizers import Adam

[In]: def create_and_train_model(
        self,
        train_features,
        train_labels,
        epochs=100,
        batch_size=32,
        learning_rate=0.001
    ):
    self.input_shape = (train_features.shape[1],)
    self.model = Sequential([
        Dense(
            64,
            activation='relu',
            input_shape=self.input_shape
        ),
        Dense(
            32,
            activation='relu'
        ),
        Dense(
            16,
            activation='relu'
        ),
        Dense(1)
    ])
    optimizer = Adam(learning_rate=learning_rate)
    self.model.compile(optimizer=optimizer, loss='mse')
    history = self.model.fit(
        train_features,
        train_labels,
        epochs=epochs,
        batch_size=batch_size,
        verbose=0
    )
    return history
```

在这个修改后的 `create_and_train_model` 函数代码中：
- 我们在方法签名中添加了一个 `learning_rate` 参数，允许在调用方法时指定学习率。在基础模型中，该参数的默认值为 0.001。
- 我们更新了优化器的实例化，使其使用 `Adam(learning_rate=learning_rate)`，从而使学习率可自定义。

我们可以如下调用该方法并使用不同的学习率：

```python
[In]: history = tsla_regressor.create_and_train_model(
        train_features,
        train_labels,
        learning_rate=0.0005
       )
```

我们使用 0.01 的中等学习率进行了实验。该值高于默认值（0.001），但仍处于神经网络训练中常用的合理范围内。中等学习率可以在不冒不稳定风险的情况下加速训练初期，使模型更快地向收敛推进。使用此学习率获得的结果显示出良好的性能：

测试损失：16.9786
R2 分数：0.9986

这些指标表明，使用学习率 0.01 训练的模型实现了相对较低的测试损失和较高的 R2 分数，与基础模型相比，显示出良好的预测性能和泛化能力：

基础模型：0.001
测试损失（基础模型）：15.5924
R2 分数（基础模型）：0.9987

另一方面，我们也使用更保守的学习率 0.0001 进行了实验。该值显著低于默认值，可被视为保守，导致更慢但可能更稳定的训练进程。使用此学习率获得的结果如下：

测试损失：1056.1927
R2 分数：0.9111

虽然与基础模型和使用学习率 0.01 训练的模型相比，测试损失明显更高，但 R2 分数仍然相对较高，表明模型保留了相当一部分预测能力。然而，显著较高的测试损失表明，由于学习率较为保守，训练进程可能较慢，可能需要更多的 epoch 才能达到收敛。

总体而言，这些实验说明了不同学习率对模型训练和性能的影响。虽然 0.01 的中等学习率导致了更快的收敛和良好的性能，但 0.0001 的保守学习率导致了较慢的进程，但仍保持了合理的预测能力。学习率的选择应根据数据集的具体特征以及训练速度与稳定性之间的期望平衡来调整。

# 模型容量

神经网络模型的容量是指其学习和表示数据中复杂模式的能力。容量不足会导致欠拟合，即模型无法捕捉数据的潜在结构。相反，过大的容量会导致过拟合，即模型学习了训练数据中的噪声，而不是实际的模式。通过改变层数和神经元数量来调整模型容量是优化性能的关键步骤。在基础模型中，TSLARegressor 类中定义的神经网络模型由以下层组成：

- 输入层：由传递给第一个隐藏层的 input_shape 参数隐式定义
- 第一个隐藏层：64 个神经元，ReLU 激活函数
- 第二个隐藏层：32 个神经元，ReLU 激活函数
- 第三个隐藏层：16 个神经元，ReLU 激活函数
- 输出层：1 个神经元，无激活函数（回归任务的典型配置）

要修改基础模型中的模型容量，我们会调整 `create_and_train_model` 方法中隐藏层内的神经元数量。具体来说，我们可以修改密集层中的神经元数量。

以下是我们可以调整模型容量的代码相关部分：

```python
[In]: def create_and_train_model(
    self,
    train_features,
    train_labels,
    epochs=100,
    batch_size=32
):
    self.input_shape = (train_features.shape[1],)
    self.model = Sequential([
        Dense(
            128,
            activation='relu',
            input_shape=self.input_shape
        ),
        Dense(
            64,
            activation='relu'
        ),
        Dense(
            32,
            activation='relu'
        ),
        Dense(1)
    ])
    self.model.compile(optimizer='adam', loss='mse')
    history = self.model.fit(
        train_features,
        train_labels,
        epochs=epochs,
        batch_size=batch_size,
        verbose=0
    )
    return history
```

在这个例子中，我们增加了每个隐藏层中的神经元数量，超出了基础模型的容量。基础模型的隐藏层分别有 64、32 和 16 个神经元。现在，我们将模型容量增加，使每个对应的隐藏层分别拥有 128、64 和 32 个神经元。这些调整使模型具有更大的复杂性和灵活性，以捕捉数据中的细微模式。

使用这种修改后的架构，我们获得了以下结果：

测试损失：10.7748  
R2 分数：0.9991

我们还使用中等容量进行了实验：

```python
[In]: def create_and_train_model(
        self,
        train_features,
        train_labels,
        epochs=100,
        batch_size=32
    ):
    self.input_shape = (train_features.shape[1],)
    self.model = Sequential([
    Dense(
        96,
        activation='relu',
        input_shape=self.input_shape
    ),
    Dense(
        48,
        activation='relu'
    ),
    Dense(
        24,
        activation='relu'
    ),
    Dense(1)
    ])
    self.model.compile(optimizer='adam', loss='mse')
    history = self.model.fit(
        train_features,
        train_labels,
        epochs=epochs,
        batch_size=batch_size,
        verbose=0
    )
    return history
```

中等容量模型的结果如下：

测试损失：11.3233
R2 分数：0.9990

提醒一下，基础模型的配置如下：

```python
[In]: def create_and_train_model(
        self,
        train_features,
        train_labels,
        epochs=100,
        batch_size=32
        ):
    self.input_shape = (train_features.shape[1],)
    self.model = Sequential([
    Dense(
        64,
        activation='relu',
        input_shape=self.input_shape
    ),
```





```python
    Dense(
        32,
        activation='relu'
    ),
    Dense(
        16,
        activation='relu'
    ),
    Dense(1)
])
self.model.compile(optimizer='adam', loss='mse')
history = self.model.fit(
    train_features,
    train_labels,
    epochs=epochs,
    batch_size=batch_size,
    verbose=0
)

return history
```

结果如下：

测试损失（基准模型）：15.5924
R2 分数（基准模型）：0.9987

通过增加模型容量，我们观察到性能指标有显著提升。测试损失从基准模型的 15.59 降低到高容量模型的 10.77，R2 分数从 0.9987 提升至 0.9991。这表明增加的容量使模型能够捕捉数据中更复杂的模式，从而提高了性能。

对于中等容量模型，结果也显示优于基准模型，测试损失为 11.32，R2 分数为 0.9990。虽然不如最高容量模型显著，但这种中等配置仍展示了比基准模型更好的泛化能力。

这些结果凸显了调整模型容量以平衡复杂性和泛化能力的重要性。虽然较高容量的模型可以提供更好的性能，但至关重要的是要监测过拟合情况，并确保模型对于给定的任务不过于复杂。

除了实验不同层中的神经元数量外，我们还探索了改变神经网络层数的影响。具体来说，我们实验了两种不同的架构：宽模型和更深模型。

宽模型在每层中有更多神经元，但整体层数较少。这种架构有助于我们理解宽层与深层相比对模型性能的影响：

```python
[In]: def create_and_train_model(
      self,
      train_features,
      train_labels,
      epochs=100,
      batch_size=32
      ):
    self.input_shape = (train_features.shape[1],)
    self.model = Sequential([
        Dense(
            128,
            activation='relu',
            input_shape=self.input_shape
        ),
    Dense(
        128,
        activation='relu'
    ),
    Dense(1)
])
self.model.compile(optimizer='adam', loss='mse')
history = self.model.fit(
    train_features,
    train_labels,
    epochs=epochs,
    batch_size=batch_size,
    verbose=0
)
return history
```

该模型架构的结果如下：

测试损失：12.7816
R2 分数：0.9989

更深模型拥有更多层，但每层神经元较少。这种架构有助于我们理解深层与宽层相比对模型性能的影响：

```python
[In]: def create_and_train_model(
        self,
        train_features,
        train_labels,
        epochs=100,
        batch_size=32
    ):
    self.input_shape = (train_features.shape[1],)
    self.model = Sequential([
        Dense(
            64,
            activation='relu',
            input_shape=self.input_shape
        ),
        Dense(
            64,
            activation='relu'
        ),
        Dense(
            32,
            activation='relu'
        ),
        Dense(
            16,
            activation='relu'
        ),
        Dense(
            8,
            activation='relu'
        ),
        Dense(1)
    ])
    self.model.compile(optimizer='adam', loss='mse')
    history = self.model.fit(
        train_features,
        train_labels,
        epochs=epochs,
        batch_size=batch_size,
        verbose=0
    )
    return history
```

更深模型的结果如下：

测试损失：10.2026
R2 分数：0.9991

宽模型在两个隐藏层中各有 128 个神经元，结果为测试损失 12.78，R2 分数 0.9989。这表明在较少层中使用较多神经元使模型能够良好地学习和泛化。然而，其性能不如更深模型优化。

更深模型具有五个隐藏层，神经元数量逐渐减少（分别为 64、64、32、16 和 8 个神经元），实现了测试损失 10.20 和 R2 分数 0.9991。该模型优于宽模型，表明在每层保持中等神经元数量的同时增加深度有助于捕捉数据中更复杂的模式。

让我们将这些结果与基准结果进行比较：

测试损失：15.5924
R2 分数：0.9987

宽模型和深模型均显示优于基准模型的性能。特别是更深模型，取得了最佳结果，凸显了增加模型深度以捕捉更精细数据模式的潜在优势。这些实验说明了调整神经元数量和层数以优化神经网络性能的重要性。

## 使用 Keras Tuner 实现超参数优化自动化

在前面的章节中，像层数和这样的超参数是通过手动实验选择的。虽然这种方法有时能产生令人满意的结果，但它本质上耗时且容易次优选择。随着模型变得复杂，对系统化、自动化的超参数调优方法的需求变得明显。

超参数优化存在多种方法，包括网格搜索和随机搜索。网格搜索穷举测试指定范围内参数的所有可能组合，这可能在计算上昂贵但全面。另一方面，随机搜索随机采样超参数组合，提供了更有效的但不够全面的参数空间探索。

在本节中，我们使用 Keras Tuner，一个简化并自动化超参数优化过程的工具。与网格搜索或随机搜索不同，Keras Tuner 专为深度学习模型设计，并与 Keras 无缝集成，使其成为我们需求的自然选择。通过自动化搜索最佳超参数，Keras Tuner 不仅节省时间，还通过系统地探索广泛的超参数组合来增强模型性能。我们将通过下面的代码示例展示其用法（完整代码将在“将所有部分结合”一节中提供），该示例优化了神经网络的每层的学习率和单位数量。

要将 Keras Tuner 整合到我们的工作流中，第一步是导入必要的库。

### 步骤 1：导入必要的库

```python
[In]: from keras_tuner import HyperModel, RandomSearch
```

*HyperModel* 允许我们定义模型结构以及需要调优的超参数。*RandomSearch* 是处理探索不同超参数组合的调优器。

### 步骤 2：定义 TSLAHyperModel 类

```python
[In]: class TSLAHyperModel(HyperModel):
        """
        用于特斯拉股价回归的 HyperModel 类。
        定义模型架构，并允许 Keras Tuner
        搜索最佳超参数。
        """
        def build(self, hp):
            model = Sequential()
            model.add(
                Dense(
                    units=hp.Int(
                        'units_1',
                        min_value=32,
                        max_value=256,
                        step=32
                    ),
                    activation='relu',
                    input_shape=(self.input_shape,)
                )
            )
            model.add(
                Dense(
                    units=hp.Int(
                        'units_2',
                        min_value=16,
                        max_value=128,
                        step=16
                    ),
                    activation='relu'
                )
            )
            model.add(
                Dense(
                    units=hp.Int(
                        'units_3',
                        min_value=8,
                        max_value=64,
                        step=8
                    ),
                    activation='relu'
                )
            )
            model.add(Dense(1))

            model.compile(
                optimizer=tf.keras.optimizers.Adam(
                    learning_rate=hp.Choice(
                        'learning_rate',
                        values=[1e-2, 1e-3, 1e-4]
                    )
                ),
                loss='mse'
            )
            return model
```

在这一步中，我们定义了一个自定义的 TSLAHyperModel 类，该继承自 *HyperModel* 类。该类指定了神经网络的架构和需要调优的超参数。build 方法正是在这里



模型结构已定义，其中超参数（如每层的单元数量 `units_1`、`units_2`、`units_3`）和学习率通过 `hp`（超参数）对象动态设置。这种设置允许 Keras Tuner 系统地探索这些参数的不同组合。

### 步骤 3：将调优器集成到模型训练过程中

```python
def create_and_train_model(
    self,
    train_features,
    train_labels,
    test_features,
    test_labels,
    epochs=100,
    batch_size=32
):
    """
    使用 Keras Tuner 进行超参数优化，
    创建并训练神经网络模型。

    参数:
    - train_features (ndarray): 训练特征。
    - train_labels (ndarray): 训练标签。
    - test_features (ndarray): 测试特征。
    - test_labels (ndarray): 测试标签。
    - epochs (int): 训练轮数。
    - batch_size (int): 训练批次大小。

    返回:
    - History:
      包含每个轮次损失值的训练历史。
    """
    self.input_shape = train_features.shape[1]

    tsla_hypermodel = TSLAHyperModel()
    tsla_hypermodel.input_shape = self.input_shape
    tuner = RandomSearch(
        tsla_hypermodel,
        objective='val_loss',
        max_trials=5,
        executions_per_trial=3,
        directory='tuner_dir',
        project_name='tsla_regression'
    )

    tuner.search(
        train_features,
        train_labels,
        epochs=epochs,
        batch_size=batch_size,
        validation_data=(test_features, test_labels),
        verbose=1
    )

    self.model = tuner.get_best_models(num_models=1)[0]
    return self.model.fit(
        train_features,
        train_labels,
        epochs=epochs,
        batch_size=batch_size,
        verbose=1,
        validation_data=(test_features, test_labels)
    )
```

在此处，我们通过更新 `create_and_train_model` 方法将 Keras Tuner 集成到我们的模型训练过程中。该方法现在使用 `TSLAHyperModel` 类来定义模型架构，并配置 *RandomSearch* 调优器以探索不同的超参数组合。`tuner.search` 函数执行调优过程，在此期间，调优器训练具有不同超参数的多个模型，并使用验证数据对它们进行评估。搜索完成后，选出最佳模型并进一步进行训练。

就结果而言，在 100 个轮次的训练过程中，训练损失和验证损失均呈现稳定下降的趋势。这些结果基于调优过程中选定的最佳超参数，包括每层的最优单元数和最有效的学习率。最终验证损失低至 12.39，表明模型具有较强的泛化能力，在最小化训练数据误差和在未见过的验证数据上表现良好之间保持了良好的平衡。

在使用优化后的超参数训练后，模型在测试数据集上进行了评估。最终测试损失为 9.16，表明模型在未见的测试数据上表现一致。R2 分数衡量因变量方差中可由自变量预测的比例，其值令人印象深刻地达到了 0.9992。这一高 R2 分数表明，该模型凭借其调优后的层结构和学习率，解释了测试数据中几乎全部的变异性，使其成为预测 TSLA 股票价格的高准确性预测器。

## 综合所有内容

在本节中，我们展示了包含多项增强功能的基线 TSLA 股票价格回归模型的集成版本。在我们的探索过程中，我们引入了对模型架构的各种改进，包括早停、Dropout 正则化、L1 和 L2 正则化以及自定义学习率。我们还利用 Keras Tuner 进行了自动超参数优化。这些修改每一项都旨在增强模型的性能、鲁棒性和泛化能力。

下面，我们提供了一个统一的代码片段，将这些增强功能整合到一个连贯的模型中，从基线模型开始。

### 基线模型

```python
import logging
import numpy as np
import tensorflow as tf
from pyspark.sql import SparkSession
from pyspark.ml.feature import VectorAssembler, StandardScaler
from sklearn.metrics import r2_score
from tensorflow.keras.models import Sequential
from tensorflow.keras.layers import Dense
import matplotlib.pyplot as plt

class TSLARegressor:
    """
    用于 TSLA 股票价格回归的类。
    """
    def __init__(self):
        """
        初始化 TSLARegressor 对象。
        """
        self.logger = logging.getLogger(__name__)
        self.spark = SparkSession.builder \
                          .appName("TSLA_Regression") \
                          .getOrCreate()
        self.input_shape = None
        self.model = None

    def preprocess_data(
            self,
            file_path,
            feature_cols=['Open', 'High', 'Low', 'Volume'],
            train_ratio=0.8,
            seed=42
    ):
        """
        预处理数据。

        参数:
            - file_path (str): CSV 文件的路径。
            - feature_cols (list): 特征列列表。
            - train_ratio (float): 训练数据比例。
            - seed (int): 数据划分的随机种子。

        返回:
            - tuple: 包含训练和测试 DataFrame 的元组。
        """
        df = self.spark.read.csv(
            file_path,
            header=True,
            inferSchema=True
        )
        assembler = VectorAssembler(
            inputCols=feature_cols, outputCol='features')
        df = assembler.transform(df)
        scaler = StandardScaler(
            inputCol='features',
            outputCol='scaled_features',
            withMean=True,
            withStd=True
        )
        scaler_model = scaler.fit(df)
        df = scaler_model.transform(df)
        train_df, test_df = df.randomSplit(
            [train_ratio, 1-train_ratio],
            seed=seed
        )
        return train_df, test_df

    def convert_to_numpy(self, train_df, test_df):
        """
        将 Spark DataFrame 转换为 numpy 数组。

        参数:
            - train_df (DataFrame):
                包含训练数据的 Spark DataFrame。
            - test_df (DataFrame):
                包含测试数据的 Spark DataFrame。

        返回:
            - tuple:
                包含特征和标签的训练和测试
                numpy 数组的元组。
        """
        train_features = np.array(
            train_df.select('scaled_features')
            .rdd.map(lambda x: x.scaled_features.
            toArray())
            .collect()
        )
        train_labels = np.array(
            train_df.select('Close')
            .rdd.map(lambda x: x.Close).collect())
        test_features = np.array(
            test_df.select('scaled_features')
            .rdd.map(lambda x: x.scaled_features.
            toArray())
            .collect()
        )
        test_labels = np.array(
            test_df.select('Close')
            .rdd.map(lambda x: x.Close).collect())
        return (train_features,
            train_labels,
            test_features,
            test_labels)

    def create_and_train_model(
        self,
        train_features,
        train_labels,
        epochs=100,
        batch_size=32
    ):
        """
        创建并训练神经网络模型。

        参数:
         - train_features (ndarray): 训练
         特征。
         - train_labels (ndarray): 训练标签。
         - epochs (int): 训练轮数。
         - batch_size (int): 训练批次大小。

        返回:
         - History:
        包含每个轮次
        损失值的训练历史。
        """
        self.input_shape = (train_features.shape[1],)
        self.model = Sequential([
         Dense(
         64,
         activation='relu',
         input_shape=self.input_shape
         ),
         Dense(
         32,
         activation='relu'
         ),
         Dense(
         16,
         activation='relu'
         ),
         Dense(1)
        ])
        self.model.compile(optimizer='adam', loss='mse')
        history = self.model.fit(
            train_features,
            train_labels,
            epochs=epochs,
            batch_size=batch_size,
            verbose=0
        )
        return history

    def evaluate_model(self, test_features, test_labels):
        """
        评估已训练的模型。
        
        参数:
        - test_features (ndarray): 测试特征。
        - test_labels (ndarray): 测试标签。
        
        返回:
        - float: 测试损失。
        """
        test_loss = self.model.evaluate(
            test_features,
            test_labels
        )
        return test_loss

    def predict_and_evaluate(
        self,
        test_features,
        test_labels
    ):
        """
        """
```




# 第9章
## 提升模型性能的技巧

### 早停（Early Stopping）

```python
import logging
import numpy as np
import tensorflow as tf
from pyspark.sql import SparkSession
from pyspark.ml.feature import VectorAssembler, StandardScaler
from sklearn.metrics import r2_score
from tensorflow.keras.models import Sequential
from tensorflow.keras.layers import Input, Dense
from tensorflow.keras.callbacks import EarlyStopping

class TSLARegressor:
    """
    TSLA股票价格回归类。
    """
    def __init__(self):
        """
        初始化 TSLARegressor 对象。
        """
        self.logger = logging.getLogger(__name__)
        self.spark = SparkSession.builder \
            .appName("TSLA_Regression") \
            .getOrCreate()
        self.input_shape = None
        self.model = None

    def preprocess_data(
        self,
        file_path,
        feature_cols=['Open', 'High', 'Low', 'Volume'],
        train_ratio=0.8,
        seed=42
    ):
        """
        预处理数据。
        
        参数：
            - file_path (str): CSV文件路径。
            - feature_cols (list): 特征列列表。
            - train_ratio (float): 训练数据比例。
            - seed (int): 用于分割数据的随机种子。
        
        返回：
            - tuple: 包含训练集和测试集数据框的元组。
        """
        
        df = self.spark.read.csv(
            file_path,
            header=True,
            inferSchema=True
        )
        
        assembler = VectorAssembler(
            inputCols=feature_cols, outputCol='features')
        df = assembler.transform(df)
        scaler = StandardScaler(
                inputCol='features',
                outputCol='scaled_features',
                withMean=True,
                withStd=True
            )
        scaler_model = scaler.fit(df)
        df = scaler_model.transform(df)
        train_df, test_df = df.randomSplit(
                [train_ratio, 1-train_ratio],
                seed=seed
            )
        return train_df, test_df

    def convert_to_numpy(self, train_df, test_df):
        """
        将 Spark 数据框转换为 numpy 数组。

        参数：
            - train_df (DataFrame):
                包含训练数据的 Spark 数据框。
            - test_df (DataFrame):
                包含测试数据的 Spark 数据框。

        返回：
            - tuple:
                包含特征和标签的训练集和测试集
                numpy
                数组的元组。
        """
        train_features = np.array(
            train_df.select('scaled_features')
            .rdd.map(lambda x: x.scaled_features.
            toArray())
            .collect()
        )
        train_labels = np.array(
            train_df.select('Close')
            .rdd.map(lambda x: x.Close).collect())
        test_features = np.array(
            test_df.select('scaled_features')
            .rdd.map(lambda x: x.scaled_features.
            toArray())
            .collect()
        )
        test_labels = np.array(
            test_df.select('Close')
            .rdd.map(lambda x: x.Close).collect()
        )
        return (train_features,
                train_labels,
                test_features,
                test_labels
        )

    def create_and_train_model(
            self,
            train_features,
            train_labels,
            epochs=100,
            batch_size=32
    ): 
        """
        创建并训练神经网络模型。

        参数：
            - train_features (ndarray): 训练特征。
            - train_labels (ndarray): 训练标签。
            - epochs (int): 训练轮数。
            - batch_size (int): 训练批次大小。

        返回：
            - History:
                包含每个轮次
                损失值的训练历史。
        """
        self.input_shape = (train_features.shape[1],)
        self.model = Sequential([
            Dense(
                64,
                activation='relu',
                input_shape=self.input_shape
            ),
            Dense(
                32,
                activation='relu'
            ),
            Dense(
                16,
                activation='relu'
            ),
            Dense(1)
        ])
        self.model.compile(optimizer='adam', loss='mse')
        history = self.model.fit(
                train_features,
                train_labels,
                epochs=epochs,
                batch_size=batch_size,
                verbose=0
            )
            return history

    def evaluate_model(self, test_features, test_labels):
        """
        评估训练好的模型。

        参数：
            - test_features (ndarray): 测试特征。
            - test_labels (ndarray): 测试标签。

        返回：
            - float: 测试损失。
        """
        test_loss = self.model.evaluate(
            test_features,
            test_labels
        )
        return test_loss

    def predict_and_evaluate(
        self,
        test_features,
        test_labels
    ):
        """
        预测并评估神经网络模型。

        参数：
            - test_features (ndarray): 测试特征。
            - test_labels (ndarray): 测试标签。

        返回：
            - float: R2 分数。
        """
        test_predictions = self.model.predict(test_features)
        r2_score_value = r2_score(test_labels, test_predictions)
        return r2_score_value

def main(file_path):
    """
    用于编排整个工作流的主函数。
    
    参数：
    - file_path (str): CSV文件路径。
    
    返回：
    - None
    """
    try:
        tsla_regressor = TSLARegressor()
        train_df, test_df = tsla_regressor.preprocess_data(file_path)
        train_features, train_labels, test_features, \
        test_labels = tsla_regressor.convert_to_numpy(
            train_df,
            test_df
        )
        history = tsla_regressor.create_and_train_model(
            train_features,
            train_labels
        )
        test_loss = tsla_regressor.evaluate_model(
            test_features,
            test_labels
        )
        r2_score_value=tsla_regressor.predict_and_evaluate(
            test_features,
            test_labels
        )

        logging.info("测试损失: {}".format(test_loss))
        logging.info("R2 分数: {}".format(r2_score_value))

        plt.plot(history.history['loss'])
        plt.title('模型损失')
        plt.xlabel('轮次')
        plt.ylabel('损失')

        plt.show()
    except Exception as e:
        logging.error(f"发生错误: {e}")

if __name__ == "__main__":
    logging.basicConfig(level=logging.INFO)
    file_path = "/home/ubuntu/airflow/dags/TSLA_stock.csv"
    main(file_path)
```

### Dropout（随机丢弃）

```python
import logging
import numpy as np
import tensorflow as tf
from pyspark.sql import SparkSession
from pyspark.ml.feature import VectorAssembler, StandardScaler
from sklearn.metrics import r2_score
from tensorflow.keras.models import Sequential
from tensorflow.keras.layers import Dense
from tensorflow.keras.layers import Dropout

class TSLARegressor:
    """
    TSLA股票价格回归类。
    """
    def __init__(self):
        """
        初始化 TSLARegressor 对象。
        """
        self.logger = logging.getLogger(__name__)
        self.spark = SparkSession.builder \
            .appName("TSLA_Regression") \
            .getOrCreate()
        self.input_shape = None
        self.model = None
    def preprocess_data(
        self,




## L1 正则化

```python
import logging
import numpy as np
import tensorflow as tf
from pyspark.sql import SparkSession
from pyspark.ml.feature import VectorAssembler, StandardScaler
from sklearn.metrics import r2_score
from tensorflow.keras.models import Sequential
from tensorflow.keras.layers import Dense
from tensorflow.keras.regularizers import l1

class TSLARegressor:
    """
    TSLA 股票价格回归类。
    """
    def __init__(self):
        """
        初始化 TSLARegressor 对象。
        """
        self.logger = logging.getLogger(__name__)
        self.spark = SparkSession.builder \
            .appName("TSLA_Regression") \
            .getOrCreate()
        self.input_shape = None
        self.model = None

    def preprocess_data(
        self,
        file_path,
        feature_cols=['Open', 'High', 'Low', 'Volume'],
        train_ratio=0.8,
        seed=42
    ):
        """
        预处理数据。

        参数:
        - file_path (str): CSV 文件的路径。
        - feature_cols (list): 特征列列表。
        - train_ratio (float): 训练数据比例。
        - seed (int): 用于数据分割的随机种子。

        返回:
        - tuple: 包含训练和测试 DataFrame 的元组。
        """
        df = self.spark.read.csv(
            file_path,
            header=True,
            inferSchema=True
        )
        assembler = VectorAssembler(
            inputCols=feature_cols, outputCol='features')
        df = assembler.transform(df)
        scaler = StandardScaler(
            inputCol='features',
            outputCol='scaled_features',
            withMean=True,
            withStd=True
        )
        scaler_model = scaler.fit(df)
        df = scaler_model.transform(df)
        train_df, test_df = df.randomSplit(
            [train_ratio, 1-train_ratio],
            seed=seed
        )
        return train_df, test_df

    def convert_to_numpy(self, train_df, test_df):
        """
        将 Spark DataFrame 转换为 numpy 数组。

        参数:
        - train_df (DataFrame):
            包含训练数据的 Spark DataFrame。
        - test_df (DataFrame):
            包含测试数据的 Spark DataFrame。

        返回:
        - tuple:
            包含特征和标签的训练集和测试集
            numpy 数组的元组。
        """
        train_features = np.array(
            train_df.select('scaled_features')
            .rdd.map(lambda x: x.scaled_features.
            toArray())
            .collect()
        )
        train_labels = np.array(
            train_df.select('Close')
            .rdd.map(lambda x: x.Close).collect()
        )
        test_features = np.array(
            test_df.select('scaled_features')
            .rdd.map(lambda x: x.scaled_features.
            toArray())
            .collect()
        )
        test_labels = np.array(
            test_df.select('Close')
            .rdd.map(lambda x: x.Close).collect()
        )
        return (train_features,
                train_labels,
                test_features,
                test_labels
               )

    def create_and_train_model(
        self,
        train_features,
        train_labels,
        epochs=100,
        batch_size=32
    ):
        """
        创建并训练神经网络模型。

        参数:
        - train_features (ndarray): 训练特征。
        - train_labels (ndarray): 训练标签。
        - epochs (int): 训练轮数。
        - batch_size (int): 训练批次大小。

        返回:
        - History:
        包含每个训练轮次
        损失值的训练历史。
        """
        self.input_shape = (train_features.shape[1],)
        self.model = Sequential([
            Dense(
                64,
                activation='relu',
                input_shape=self.input_shape,
                kernel_regularizer=l1(0.01)
            ),
            Dense(
                32,
                activation='relu',
                kernel_regularizer=l1(0.01)
            ),
            Dense(
                16,
                activation='relu',
                kernel_regularizer=l1(0.01)
            ),
            Dense(1)
        ])
        self.model.compile(optimizer='adam', loss='mse')
        history = self.model.fit(
            train_features,
            train_labels,
            epochs=epochs,
            batch_size=batch_size,
            verbose=0
        )
        return history

    def evaluate_model(self, test_features, test_labels):
        """
        评估训练好的模型。

        参数:
        - test_features (ndarray): 测试特征。
        - test_labels (ndarray): 测试标签。

        返回:
        - float: 测试损失。
        """
        test_loss = self.model.evaluate(
            test_features,
            test_labels
        )
        return test_loss

    def predict_and_evaluate(
        self,
        test_features,
        test_labels
    ):
        """
        预测并评估神经网络模型。

        参数:
        - test_features (ndarray): 测试特征。
        - test_labels (ndarray): 测试标签。

        返回:
        - float: R2 分数。
        """
        test_predictions = self.model.predict(test_features)
        r2_score_value = r2_score(test_labels, test_predictions)
        return r2_score_value

def main(file_path):
    """
    主函数，用于编排整个工作流程。

    参数:
    - file_path (str): CSV 文件的路径。

    返回:
    - None
    """
    try:
        tsla_regressor = TSLARegressor()
        train_df, test_df = tsla_regressor.preprocess_data(
            file_path
        )
        train_features, train_labels, test_features, \
        test_labels = tsla_regressor.convert_to_numpy(
            train_df,
            test_df
        )
        history = tsla_regressor.create_and_train_model(
            train_features,
            train_labels
        )
        test_loss = tsla_regressor.evaluate_model(
            test_features,
            test_labels
        )
        r2_score_value = tsla_regressor.predict_and_evaluate(
            test_features,
            test_labels
        )

        logging.info("测试损失: {}".format(test_loss))
        logging.info("R2 分数: {}".format(r2_score_value))

    except Exception as e:
        logging.error(f"发生错误: {e}")

if __name__ == "__main__":
    logging.basicConfig(level=logging.INFO)
    file_path = "/home/ubuntu/airflow/dags/TSLA_stock.csv"
    main(file_path)
```

## 第 9 章 提升模型性能的技术





# L2 正则化

```python
import logging
import numpy as np
import tensorflow as tf
from pyspark.sql import SparkSession
from pyspark.ml.feature import VectorAssembler, StandardScaler
from sklearn.metrics import r2_score
from tensorflow.keras.models import Sequential
from tensorflow.keras.layers import Dense
from tensorflow.keras.regularizers import l2

class TSLARegressor:
    """
    TSLA 股价回归类。
    """
    def __init__(self):
        """
        初始化 TSLARegressor 对象。
        """
        self.logger = logging.getLogger(__name__)
        self.spark = SparkSession.builder \
                      .appName("TSLA_Regression") \
                      .getOrCreate()
        self.input_shape = None
        self.model = None

    def preprocess_data(
            self,
            file_path,
            feature_cols=['Open', 'High', 'Low', 'Volume'],
            train_ratio=0.8,
            seed=42
    ):
        """
        预处理数据。

        参数：
            - file_path (str): CSV 文件路径。
            - feature_cols (list): 特征列列表。
            - train_ratio (float): 训练数据比例。
            - seed (int): 数据划分的随机种子。

        返回：
            - tuple: 包含训练和测试 DataFrame 的元组。
        """
        df = self.spark.read.csv(
            file_path,
            header=True,
            inferSchema=True
        )
        assembler = VectorAssembler(
            inputCols=feature_cols, outputCol='features')
        df = assembler.transform(df)
        scaler = StandardScaler(
            inputCol='features',
            outputCol='scaled_features',
            withMean=True,
            withStd=True
        )
        scaler_model = scaler.fit(df)
        df = scaler_model.transform(df)
        train_df, test_df = df.randomSplit(
            [train_ratio, 1-train_ratio],
            seed=seed
        )
        return train_df, test_df

    def convert_to_numpy(self, train_df, test_df):
        """
        将 Spark DataFrame 转换为 numpy 数组。

        参数：
            - train_df (DataFrame):
                包含训练数据的 Spark DataFrame。
            - test_df (DataFrame):
                包含测试数据的 Spark DataFrame。

        返回：
            - tuple:
                包含特征和标签的训练和测试 numpy 数组的元组。
        """
        train_features = np.array(
            train_df.select('scaled_features')
            .rdd.map(lambda x: x.scaled_features.
            toArray())
            .collect()
        )
        train_labels = np.array(
            train_df.select('Close')
            .rdd.map(lambda x: x.Close).collect())
        test_features = np.array(
            test_df.select('scaled_features')
            .rdd.map(lambda x: x.scaled_features.
            toArray())
            .collect()
        )
        test_labels = np.array(
            test_df.select('Close')
            .rdd.map(lambda x: x.Close).collect()
        )
        return (train_features,
        train_labels,
        test_features,
        test_labels
        )

    def create_and_train_model(
        self,
        train_features,
        train_labels,
        epochs=100,
        batch_size=32
    ):
        """
        创建并训练神经网络模型。
        参数：
        - train_features (ndarray): 训练特征。
        - train_labels (ndarray): 训练标签。
        - epochs (int): 训练轮数。
        - batch_size (int): 训练批量大小。
        返回：
        - History:
        包含每个 epoch 损失值的训练历史。
        """
        self.input_shape = (train_features.shape[1],)
        self.model = Sequential([
            Dense(
                64,
                activation='relu',
                input_shape=self.input_shape,
                kernel_regularizer=l2(0.01)
            ),
            Dense(
                32,
                activation='relu',
                kernel_regularizer=l2(0.01)
            ),
            Dense(
                16,
                activation='relu',
                kernel_regularizer=l2(0.01)
            ),
            Dense(1)
        ]
        self.model.compile(optimizer='adam', loss='mse')
        history = self.model.fit(
            train_features,
            train_labels,
            epochs=epochs,
            batch_size=batch_size,
            verbose=0
        )
        return history

    def evaluate_model(self, test_features, test_labels):
        """
        评估训练好的模型。

        参数：
        - test_features (ndarray): 测试特征。
        - test_labels (ndarray): 测试标签。

        返回：
        - float: 测试损失。
        """
        test_loss = self.model.evaluate(
            test_features,
            test_labels
        )
        return test_loss

    def predict_and_evaluate(
        self,
        test_features,
        test_labels
    ):
        """
        预测并评估神经网络模型。
        参数：
        - test_features (ndarray): 测试特征。
        - test_labels (ndarray): 测试标签。
        返回：
        - float: R2 分数。
        """
        test_predictions = self.model.predict(test_features)
        r2_score_value = r2_score(test_labels, test_predictions)
        return r2_score_value

def main(file_path):
    """
    协调整个工作流程的主函数。

    参数：
    - file_path (str): CSV 文件路径。

    返回：
    - None
    """
    try:
        tsla_regressor = TSLARegressor()
        train_df, test_df = tsla_regressor.preprocess_data(
            file_path
        )
        train_features, train_labels, test_features, \
        test_labels = tsla_regressor.convert_to_numpy(
            train_df,
            test_df
        )
        history = tsla_regressor.create_and_train_model(
            train_features,
            train_labels
        )
        test_loss = tsla_regressor.evaluate_model(
            test_features,
            test_labels
        )
        r2_score_value = tsla_regressor.predict_and_evaluate(
            test_features,
            test_labels
        )

        logging.info("Test Loss: {}".format(test_loss))
        logging.info("R2 Score: {}".format(r2_score_value))

    except Exception as e:
        logging.error(f"An error occurred: {e}")

if __name__ == "__main__":
    logging.basicConfig(level=logging.INFO)
    file_path = "/home/ubuntu/airflow/dags/TSLA_stock.csv"
    main(file_path)
```

# 学习率

```python
import logging
import numpy as np
import tensorflow as tf
from pyspark.sql import SparkSession
from pyspark.ml.feature import VectorAssembler, StandardScaler
from sklearn.metrics import r2_score
from tensorflow.keras.models import Sequential
from tensorflow.keras.layers import Dense
from tensorflow.keras.optimizers import Adam

class TSLARegressor:
    """
    TSLA 股价回归类。
    """
```





## 第 9 章 提升模型性能的技术

# 模型容量

```python
import logging
import numpy as np
import tensorflow as tf
from pyspark.sql import SparkSession
from pyspark.ml.feature import VectorAssembler, StandardScaler
from sklearn.metrics import r2_score
from tensorflow.keras.models import Sequential
from tensorflow.keras.layers import Dense
import matplotlib.pyplot as plt

class TSLARegressor:
    """
    TSLA 股价回归的类。
    """

    def __init__(self):
        """
        初始化 TSLARegressor 对象。
        """
        self.logger = logging.getLogger(__name__)
        self.spark = SparkSession.builder \
            .appName("TSLA_Regression") \
            .getOrCreate()
        self.input_shape = None
        self.model = None

    def preprocess_data(
        self,
        file_path,
        feature_cols=['Open', 'High', 'Low', 'Volume'],
        train_ratio=0.8,
        seed=42
    ):
        """
        预处理数据。

        参数：
            - file_path (str): CSV 文件的路径。
            - feature_cols (list): 特征列列表。
            - train_ratio (float): 训练数据比例。
            - seed (int): 用于分割数据的随机种子。

        返回值：
            - tuple: 包含训练和测试 DataFrame 的元组。
        """
        df = self.spark.read.csv(
            file_path,
            header=True,
            inferSchema=True
        )
        assembler = VectorAssembler(
            inputCols=feature_cols, outputCol='features')
        df = assembler.transform(df)
        scaler = StandardScaler(
            inputCol='features',
            outputCol='scaled_features',
            withMean=True,
            withStd=True
        )
        scaler_model = scaler.fit(df)
        df = scaler_model.transform(df)
        train_df, test_df = df.randomSplit(
            [train_ratio, 1-train_ratio],
            seed=seed
        )
        return train_df, test_df

    def convert_to_numpy(self, train_df, test_df):
        """
        将 Spark DataFrame 转换为 numpy 数组。

        参数：
            - train_df (DataFrame):
                包含训练数据的 Spark DataFrame。
            - test_df (DataFrame):
                包含测试数据的 Spark DataFrame。

        返回值：
            - tuple:
                包含特征和标签的训练及测试 numpy 数组的元组。
        """
        train_features = np.array(
            train_df.select('scaled_features')
                    .rdd.map(lambda x: x.scaled_features.toArray())
                    .collect()
        )
        train_labels = np.array(
            train_df.select('Close')
                    .rdd.map(lambda x: x.Close).collect()
        )
        test_features = np.array(
            test_df.select('scaled_features')
                   .rdd.map(lambda x: x.scaled_features.toArray())
                   .collect()
        )
        test_labels = np.array(
            test_df.select('Close')
                   .rdd.map(lambda x: x.Close).collect()
        )
        return (train_features,
                train_labels,
                test_features,
                test_labels
        )

    def create_and_train_model(
        self,
        train_features,
        train_labels,
        epochs=100,
        batch_size=32
    ):
        """
        创建并训练神经网络模型。

        参数：
        - train_features (ndarray): 训练特征。
        - train_labels (ndarray): 训练标签。
        - epochs (int): 训练的轮数（epochs）。
        - batch_size (int): 训练的批量大小。

        返回值：
        - History:
            包含每个 epoch 损失值的训练历史。
        """
        self.input_shape = (train_features.shape[1],)
        self.model = Sequential([
            Dense(
                64,
                activation='relu',
                input_shape=self.input_shape
            ),
            Dense(
                32,
                activation='relu'
            ),
            Dense(
                16,
                activation='relu'
            ),
            Dense(1)
        ])
        optimizer = Adam(learning_rate=0.01)
        self.model.compile(optimizer=optimizer, loss='mse')
        history = self.model.fit(
            train_features,
            train_labels,
            epochs=epochs,
            batch_size=batch_size,
            verbose=0
        )
        return history

    def evaluate_model(self, test_features, test_labels):
        """
        评估训练好的模型。

        参数：
        - test_features (ndarray): 测试特征。
        - test_labels (ndarray): 测试标签。

        返回值：
        - float: 测试损失。
        """
        test_loss = self.model.evaluate(
            test_features,
            test_labels
        )
        return test_loss

    def predict_and_evaluate(
        self,
        test_features,
        test_labels
    ):
        """
        预测并评估神经网络模型。

        参数：
        - test_features (ndarray): 测试特征。
        - test_labels (ndarray): 测试标签。

        返回值：
        - float: R2 分数。
        """
        test_predictions = self.model.predict(test_features)
        r2_score_value = r2_score(test_labels, test_predictions)
        return r2_score_value

def main(file_path):
    """
    协调整个工作流的主函数。

    参数：
    - file_path (str): CSV 文件的路径。

    返回值：
    - None
    """
    try:
        tsla_regressor = TSLARegressor()
        train_df, test_df = tsla_regressor.preprocess_data(file_path)
        train_features, train_labels, test_features, test_labels = tsla_regressor.convert_to_numpy(
            train_df,
            test_df
        )
        history = tsla_regressor.create_and_train_model(
            train_features,
            train_labels
        )
        test_loss = tsla_regressor.evaluate_model(
            test_features,
            test_labels
        )
        r2_score_value = tsla_regressor.predict_and_evaluate(
            test_features,
            test_labels
        )
        
        logging.info("测试损失: {}".format(test_loss))
        logging.info("R2 分数: {}".format(r2_score_value))

        plt.plot(history.history['loss'])
        plt.title('模型损失')
        plt.xlabel('Epoch')
        plt.ylabel('Loss')

        plt.show()

    except Exception as e:
        logging.error(f"发生错误: {e}")

if __name__ == "__main__":
    logging.basicConfig(level=logging.INFO)
    file_path = "/home/ubuntu/airflow/dags/TSLA_stock.csv"
    main(file_path)
```





## 使用神经网络进行 TSLA 股价回归

```python
    Dense(
        64,
        activation='relu'
    ),
    Dense(
        32,
        activation='relu'
    ),
    Dense(1)
])
self.model.compile(optimizer='adam', loss='mse')
history = self.model.fit(
    train_features,
    train_labels,
    epochs=epochs,
    batch_size=batch_size,
    verbose=0
)
return history

def evaluate_model(self, test_features, test_labels):
    """
    评估已训练的模型。

    参数:
    - test_features (ndarray): 测试特征。
    - test_labels (ndarray): 测试标签。

    返回:
    - float: 测试损失。
    """
    test_loss = self.model.evaluate(
        test_features,
        test_labels
    )
    return test_loss

def predict_and_evaluate(
    self,
    test_features,
    test_labels
):
    """
    预测并评估神经网络模型。

    参数:
    - test_features (ndarray): 测试特征。
    - test_labels (ndarray): 测试标签。

    返回:
    - float: R2 分数。
    """
    test_predictions = self.model.predict(test_features)
    r2_score_value = r2_score(test_labels, test_predictions)
    return r2_score_value

def main(file_path):
    """
    编排整个工作流程的主函数。

    参数:
    - file_path (str): CSV 文件的路径。

    返回:
    - None
    """
    try:
        tsla_regressor = TSLARegressor()
        train_df, test_df = tsla_regressor.preprocess_data(
            file_path
        )
        train_features, train_labels, test_features, test_labels = tsla_regressor.convert_to_numpy(
            train_df,
            test_df
        )
        history = tsla_regressor.create_and_train_model(
            train_features,
            train_labels,
            test_features,
            test_labels
        )
        test_loss = tsla_regressor.evaluate_model(
            test_features,
            test_labels
        )
        r2_score_value = tsla_regressor.predict_and_evaluate(
            test_features,
            test_labels
        )
        logging.info("Test Loss: {}".format(test_loss))
        logging.info("R2 Score: {}".format(r2_score_value))

        plt.plot(history.history['loss'])
        plt.title('Model Loss')
        plt.xlabel('Epoch')
        plt.ylabel('Loss')

        plt.show()

    except Exception as e:
        logging.error(f"An error occurred: {e}")

if __name__ == "__main__":
    logging.basicConfig(level=logging.INFO)
    file_path = "/home/ubuntu/airflow/dags/TSLA_stock.csv"
    main(file_path)
```

## 使用 Keras Tuner 自动化超参数调优

```python
import logging
import numpy as np
import tensorflow as tf
from pyspark.sql import SparkSession
from pyspark.ml.feature import VectorAssembler, StandardScaler
from sklearn.metrics import r2_score
from tensorflow.keras.models import Sequential
from tensorflow.keras.layers import Dense
import matplotlib.pyplot as plt
from keras_tuner import HyperModel, RandomSearch

class TSLAHyperModel(HyperModel):
    """
    用于 TSLA 股价回归的 HyperModel 类。
    定义模型架构，并允许 Keras Tuner
    搜索最佳超参数。
    """
    def build(self, hp):
        model = Sequential()
        model.add(
            Dense(
                units=hp.Int(
                    'units_1',
                    min_value=32,
                    max_value=256,
                    step=32
                ),
                activation='relu',
                input_shape=(self.input_shape,)
            )
        )
        model.add(
            Dense(
                units=hp.Int(
                    'units_2',
                    min_value=16,
                    max_value=128,
                    step=16
                ),
                activation='relu'
            )
        )
        model.add(
            Dense(
                units=hp.Int(
                    'units_3',
                    min_value=8,
                    max_value=64,
                    step=8
                ),
                activation='relu'
            )
        )
        model.add(Dense(1))

        model.compile(
            optimizer=tf.keras.optimizers.Adam(
                learning_rate=hp.Choice(
                    'learning_rate',
                    values=[1e-2, 1e-3, 1e-4]
                )
            ),
            loss='mse'
        )
        return model

class TSLARegressor:
    """
    用于 TSLA 股价回归的类。
    """
    def __init__(self):
        """
        初始化 TSLARegressor 对象。
        """
        self.logger = logging.getLogger(__name__)
        self.spark = SparkSession.builder \
            .appName("TSLA_Regression") \
            .getOrCreate()
        self.input_shape = None
        self.model = None

    def preprocess_data(
        self,
        file_path,
        feature_cols=['Open', 'High', 'Low', 'Volume'],
        train_ratio=0.8,
        seed=42
    ):
        """
        对数据进行预处理。

        参数:
        - file_path (str): CSV 文件的路径。
        - feature_cols (list): 特征列的列表。
        - train_ratio (float): 训练数据的比例。
        - seed (int): 用于拆分数据的随机种子。

        返回:
        - tuple: 包含训练和测试数据框的元组。
        """
        df = self.spark.read.csv(
            file_path,
            header=True,
            inferSchema=True
        )
        assembler = VectorAssembler(
            inputCols=feature_cols,
            outputCol='features'
        )
        df = assembler.transform(df)
        scaler = StandardScaler(
            inputCol='features',
            outputCol='scaled_features',
            withMean=True,
            withStd=True
        )
        scaler_model = scaler.fit(df)
        df = scaler_model.transform(df)
        train_df, test_df = df.randomSplit(
            [train_ratio, 1-train_ratio],
            seed=seed
        )
        return train_df, test_df

    def convert_to_numpy(self, train_df, test_df):
        """
        将 Spark 数据框转换为 numpy 数组。

        参数:
        - train_df (DataFrame):
          包含训练数据的 Spark 数据框。
        - test_df (DataFrame):
          包含测试数据的 Spark 数据框。

        返回:
        - tuple:
          包含特征和标签的 numpy 数组的训练和测试元组。
        """
        train_features = np.array(
            train_df.select('scaled_features')
            .rdd.map(lambda x: x.scaled_features.toArray())
            .collect()
        )
        train_labels = np.array(
            train_df.select('Close')
            .rdd.map(lambda x: x.Close)
            .collect()
        )
        test_features = np.array(
            test_df.select('scaled_features')
            .rdd.map(lambda x: x.scaled_features.toArray())
            .collect()
        )
        test_labels = np.array(
            test_df.select('Close')
            .rdd.map(lambda x: x.Close)
            .collect()
        )
        return (
            train_features,
            train_labels,
            test_features,
            test_labels
        )

    def create_and_train_model(
        self,
        train_features,
        train_labels,
        test_features,
        test_labels,
        epochs=100,
        batch_size=32
    ):
        """
        使用 Keras Tuner 进行超参数优化，创建并训练神经网络模型。

        参数:
        - train_features (ndarray): 训练特征。
        - train_labels (ndarray): 训练标签。
        - test_features (ndarray): 测试特征。
        - test_labels (ndarray): 测试标签。
        - epochs (int): 训练轮数。
        - batch_size (int): 训练时的批次大小。

        返回:
        - History:
          包含每个轮次损失值的训练历史。
        """
        self.input_shape = train_features.shape[1]

        tsla_hypermmodel = TSLAHyperModel()
        tsla_hypermmodel.input_shape = self.input_shape

        tuner = RandomSearch(
            tsla_hypermmodel,
            objective='val_loss',
            max_trials=5,
            executions_per_trial=3,
            directory='tuner_dir',
            project_name='tsla_regression'
        )

        tuner.search(
            train_features,
            train_labels,
            epochs=epochs,
            batch_size=batch_size,
            validation_data=(test_features, test_labels),
            verbose=1
        )

        self.model = tuner.get_best_models(num_models=1)[0]
        return self.model.fit(
            train_features,
            train_labels,
            epochs=epochs,
            batch_size=batch_size,
            verbose=1,
            validation_data=(test_features, test_labels)
        )

    def evaluate_model(self, test_features, test_labels):
        """
        评估已训练的模型。

        参数:
        - test_features (ndarray): 测试特征。
        - test_labels (ndarray): 测试标签。

        返回:
        - float: 测试损失。
        """
        test_loss = self.model.evaluate(
            test_features,
            test_labels
        )
        return test_loss

    def predict_and_evaluate(self, test_features, test_labels):
        """
        预测并评估神经网络模型。

        参数:
        - test_features (ndarray): 测试特征。
        - test_labels (ndarray): 测试标签。

        返回:
        - float: R2 分数。
        """
        test_predictions = self.model.predict(test_features)
        r2_score_value = r2_score(test_labels, test_predictions)
        return r2_score_value
```





```python
def main(file_path):
    """
    Main function to orchestrate the entire workflow.
    
    Parameters:
    - file_path (str): Path to the CSV file.
    
    Returns:
    - None
    """
    try:
        tsla_regressor = TSLARegressor()
        train_df, test_df = tsla_regressor.preprocess_data(
            file_path
        )
        
        train_features, train_labels, test_features, test_labels = tsla_regressor.convert_to_numpy(
            train_df,
            test_df
        )
        
        history = tsla_regressor.create_and_train_model(
            train_features,
            train_labels,
            test_features,
            test_labels,
            epochs=100,
            batch_size=32
        )
        
        test_loss = tsla_regressor.evaluate_model(
            test_features,
            test_labels
        )
        r2_score_value = tsla_regressor.predict_and_evaluate(
            test_features,
            test_labels
        )

        logging.info("Test Loss: {}".format(test_loss))
        logging.info("R2 Score: {}".format(r2_score_value))

        plt.plot(history.history['loss'])
        plt.title('Model Loss')
        plt.xlabel('Epoch')
        plt.ylabel('Loss')
        plt.savefig('model_loss_plot.png')
        plt.show()

    except Exception as e:
        logging.error(f"An error occurred: {e}")

if __name__ == "__main__":
    logging.basicConfig(level=logging.INFO)
    file_path = "/home/ubuntu/airflow/dags/TSLA_stock.csv"
    main(file_path)
```

# 摘要

在本章中，我们研究了改进深度学习模型性能的多种技术。为了解决过拟合问题，我们探讨了提前停止、Dropout（随机失活）以及 L1 和 L2 正则化。这些方法通过对模型参数施加约束来防止过拟合。此外，我们还介绍了超参数优化，包括微调学习率和网络架构，以在验证集上找出表现最佳的模型。我们展示了如何手动实现这一过程，以及如何使用 Keras Tuner 来实现。

在下一章，也是本书的最后一章，读者将学习将训练好的模型部署到生产环境以及监控其性能的最佳实践。

# 第 10 章

## 部署和监控深度学习模型

将机器学习模型部署到生产环境是任何数据科学项目生命周期中的关键步骤。然而，这一过程通常会在可扩展性、可靠性和可维护性方面带来挑战。Amazon Web Services (AWS) 提供的一项全托管服务——Apache Airflow 托管工作流 (MWAA)——通过简化和自动化复杂工作流的部署和编排（包括模型部署）来解决这些挑战。

在第 2 章中，我们演示了如何独立部署 Airflow 作为深度学习服务，以及在 Docker 容器内部署。我们探讨了这些部署方式的利弊，特别是在灵活性和控制力方面。在第 8 章中，我们使用独立的 Apache Airflow 构建了可扩展的数据处理管道，整合了使用 PySpark 的预处理步骤，并使用 PyTorch 和 TensorFlow 构建深度学习模型，所有这些都在 Airflow DAG（有向无环图）中编排，用于回归和分类任务。虽然这些方法提供了显著的控制力，但它们需要手动安装和配置 Apache Airflow，以及手动触发 DAG，从而增加了复杂性和维护开销。

在本章中，我们引入第三种选择：使用 Amazon MWAA 部署深度学习模型。该服务简化了在云中设置、管理和扩展 Apache Airflow 环境的过程，无需手动管理基础设施。使用 MWAA 的主要优势在于其托管性质，使用户免受服务器管理、扩展和基础设施维护的负担。借助 MWAA，用户可以专注于构建工作流和应用，确信底层基础设施由 AWS 处理。

此外，我们将探索监控解决方案，以确保已部署模型的性能和可靠性，利用 Amazon MWAA 控制台进行工作流监控，并利用 Amazon CloudWatch 进行全面的指标和日志跟踪。通过监控深度学习模型，用户可以检测诸如模型漂移、资源瓶颈和延迟问题等问题，从而能够及时干预并确保高水平的性能、可靠性和合规性。

## 部署和监控深度学习模型的步骤

在本节中，我们研究了专门使用 Amazon 托管工作流 Apache Airflow (MWAA) 部署和监控深度学习模型所涉及的主要步骤。我们首先简要概述这些步骤，然后逐一详细探讨。

首先简要总结，主要包含六个步骤：

**步骤 1：设置环境**
- 访问 Amazon MWAA 控制台并创建一个新的 MWAA 环境。
- 通过指定用于 DAG 文件的 S3 存储桶、配置网络（包括 VPC 和子网）以及设置安全配置来配置环境。

**步骤 2：开发 DAG**
- 通过开发一个 Airflow DAG 来编排部署过程开始。该 DAG 定义任务、设置依赖关系并执行 Python 函数。例如，DAG 可以包括预处理数据、训练模型和部署模型的任务。
- 确保 DAG 代码结构良好，并包含所有必要的依赖项。

**步骤 3：上传到 S3**
- 将 DAG 文件上传到可由 MWAA 环境访问的 S3 存储桶。这通常使用 AWS CLI 或 AWS 管理控制台完成。

**步骤 4：配置 MWAA 环境**
- 配置 MWAA 环境以包含已上传的 DAG 文件。指定 DAG 执行所需的任何其他设置，如环境变量、连接和插件。这确保环境已正确设置以执行 DAG。

**步骤 5：触发 DAG 执行**
- 在 Amazon MWAA 环境中手动或基于预定义计划触发 DAG 的执行。这将启动部署过程并执行 DAG 中定义的任务，如预处理数据、训练模型和部署模型。

**步骤 6：监控执行**
- 从 MWAA 控制台监控 DAG 的执行。跟踪任务进度，查看日志，并排查部署过程中可能出现的问题。

在概述了使用 Amazon MWAA 的部署过程所涉及的步骤后，让我们逐一进行详细检查，从设置环境开始。

## 步骤 1：设置环境

设置 Amazon MWAA 环境包括指定用于 DAG 文件的 S3 存储桶以及配置网络和安全设置。请遵循以下步骤以确保环境正确配置并准备就绪：

**步骤 1：访问 Amazon MWAA 控制台**
- 使用您的 AWS 凭证登录 AWS 管理控制台。
- 在 AWS 管理控制台中，在搜索栏中输入 “MWAA”，并从服务列表中选择 “Managed Apache Airflow”。

**步骤 2：创建新的 MWAA 环境**
- 在 Amazon MWAA 仪表板上，点击 “Create environment” 按钮。

**步骤 3：指定环境详情**
- 为您的 MWAA 环境输入一个唯一的名称。
- 选择您要使用的 Apache Airflow 版本。

**步骤 4：指定 DAG 的 S3 存储桶和文件夹**
- 输入存储 DAG 文件的 S3 存储桶名称。
- 输入 S3 存储桶中 DAG 文件所在的文件夹路径（例如，dags/）。

**步骤 5：配置执行角色**
- 选择具有必要权限的现有 AWS 身份和访问管理 (IAM) 角色，或创建一个新角色。
- 确保该角色具有访问 S3 存储桶、CloudWatch 日志以及您的 DAG 可能使用的其他 AWS 服务所需的权限。

**步骤 6：配置网络**

在创建 MWAA 环境之前，您需要设置虚拟私有云 (VPC)。VPC 确保您的 MWAA 环境与其他 AWS 资源（如 S3 存储桶、数据库以及工作流可能需要的其他服务）之间的安全交互。请遵循以下步骤设置您的 VPC：

- 创建 VPC：
- 导航到 VPC 服务：在 AWS 管理控制台中，在页面顶部的搜索栏中输入 “VPC”，并从下拉列表中选择 VPC，如图 10-1 所示。





![](img/1c89d4486f90c87568fa6a42d46ae02a_718_0.png)

*图 10-1. 通过 AWS 管理控制台搜索导航至 VPC 服务*

- 在 VPC 仪表板上，点击 *创建 VPC*，如图 10-2 所示。

![](img/1c89d4486f90c87568fa6a42d46ae02a_718_1.png)

*图 10-2. AWS 上的 VPC 仪表板*

点击“*创建 VPC*”后，按照图 10-3 中的步骤进行操作：

- 选择具有单个或多个公共及私有子网的 VPC。
- 指定 CIDR 块（例如，*10.0.0.0/16*）。

![](img/1c89d4486f90c87568fa6a42d46ae02a_719_0.png)

*图 10-3. 在 AWS 上创建 VPC*

- 有关更多详细信息，请参阅 AWS VPC 文档：`https://docs.aws.amazon.com/vpc/latest/userguide/what-is-amazon-vpc.html`
- **创建子网：**
    - 导航至 VPC 仪表板中的子网部分，如图 10-4 所示。

![](img/1c89d4486f90c87568fa6a42d46ae02a_720_0.png)

*图 10-4. 在 AWS 的 VPC 仪表板中导航至子网部分*

- 如图 10-5 所示，点击“创建子网”。

![](img/1c89d4486f90c87568fa6a42d46ae02a_721_0.png)

*图 10-5. 在 AWS 上创建子网*

- 在不同可用区中创建至少两个私有子网。
- 为子网命名以便轻松识别（例如，Private-Subnet-1 和 Private-Subnet-2）。
- 重复该过程以为 NAT 网关创建公共子网。
- 有关更多详细信息，请参阅 AWS 文档：`https://docs.aws.amazon.com/vpc/latest/userguide/how-it-works.html`
- **创建并附加互联网网关：**
    - 导航至互联网网关部分。
    - 点击“创建互联网网关”。
    - 通过选择“操作”并选择“附加到 VPC”将互联网网关附加到您的 VPC。
- 有关更多详细信息，请参阅 AWS “使用互联网网关启用 VPC 互联网访问”文档：`https://docs.aws.amazon.com/vpc/latest/userguide/VPC_Internet_Gateway.html#Add_IGW_Attach_Gateway`
- **创建 NAT 网关：**
    - 如图 10-6 所示，导航至 NAT 网关部分。

![](img/1c89d4486f90c87568fa6a42d46ae02a_723_0.png)

*图 10-6. 在 AWS 上导航至 NAT 网关部分*

- 如图 10-7 所示，点击“创建 NAT 网关”。

![](img/1c89d4486f90c87568fa6a42d46ae02a_724_0.png)

*图 10-7. 在 AWS 上创建 NAT 网关*

- 选择将创建 NAT 网关的公共子网。
- 为 NAT 网关分配一个弹性 IP。
- 有关更多详细信息，请参阅 AWS NAT 网关文档：`https://docs.aws.amazon.com/vpc/latest/userguide/vpc-nat-gateway.html`
- **更新路由表：**
    - 导航至路由表部分。
    - 更新私有子网的路由表，以便将通过 NAT 网关的路由指向互联网流量。
    - 有关更多详细信息，请参阅 AWS “配置路由表”文档：`https://docs.aws.amazon.com/vpc/latest/userguide/VPC_Route_Tables.html`
- **配置安全组：**
    - 如图 10-8 所示，导航至安全组。

![](img/1c89d4486f90c87568fa6a42d46ae02a_725_0.png)

*图 10-8. 在 AWS VPC 仪表板中导航至安全组*

- 为您的 MWAA 环境创建具有必要入站和出站规则的安全组。
- 在创建 MWAA 环境时，将这些安全组与该环境关联。
- 有关更多详细信息，请参阅 AWS “使用安全组控制您的 AWS 资源的流量”文档：`https://docs.aws.amazon.com/vpc/latest/userguide/vpc-security-groups.html`

**步骤 7：配置环境类**

- 为您的 MWAA 环境选择合适的实例类。这将决定分配给您环境的计算资源。
- 指定您环境的最大工作节点数。
- 指定您环境的最小工作节点数。
- 定义调度器的数量。
- 为 Airflow 添加任何自定义配置。
- 通过提供 S3 路径来指定任何自定义插件。
- 提供 requirements.txt 文件的 S3 路径以包含额外的 Python 依赖项。
- 检查您设置的所有配置。
- 点击“创建环境”按钮以创建您的 MWAA 环境。
- 创建过程可能需要几分钟时间。
- 您可以在 Amazon MWAA 仪表板上监控环境的状态。

一旦环境创建完成且状态为活动（active），您就可以使用指定的 S3 存储桶和文件夹开始部署和管理您的 DAG。

## 步骤 2：开发 DAG

在设置好 Amazon MWAA 环境后，下一步是开发 DAG。为了说明目的，让我们开发一个简化的 DAG（`simple_mwaa_dag.py`）。这提供了对如何在 Airflow 中定义任务、设置任务依赖关系以及执行 Python 函数的基础理解。

下面的 DAG 定义了默认参数、DAG 本身、用于任务的 Python 函数以及任务并设置任务依赖关系。该 DAG 执行两个 Python 任务：一个用于打印当前日期和时间，另一个用于打印预定义的消息。当由 Airflow 编排时，这些任务确保它们按定义的顺序执行：

```python
from airflow import DAG
from airflow.operators.python_operator import PythonOperator
from datetime import datetime, timedelta

# Define default arguments

default_args = {
    'owner': 'airflow',
    'depends_on_past': False,
    'start_date': datetime(2023, 1, 1),
    'email_on_failure': False,
    'email_on_retry': False,
    'retries': 1,
    'retry_delay': timedelta(minutes=5),
}

# Define the DAG

dag = DAG(
    'simple_mwaa_dag',
    default_args=default_args,
    description='A simple DAG for MWAA',
    schedule_interval=timedelta(days=1),
)
```

```python
# Define Python functions for tasks

def print_current_date():
    print(f"Current date and time: {datetime.now()}")

def print_message():
    print("Hello, this is a message from your DAG!")
```

```python
# Define tasks

t1 = PythonOperator(
    task_id='print_date',
    python_callable=print_current_date,
    dag=dag,
)

t2 = PythonOperator(
    task_id='print_message',
    python_callable=print_message,
    dag=dag,
)
```

```python
# Set task dependencies

t1 >> t2
```

该 DAG 从 ‘print_date’ 任务开始，该任务利用 PythonOperator 执行 “print_current_date” 函数。在该函数内部，使用 Python 的 `datetime.now()` 函数获取当前日期和时间，并将此信息打印到 Airflow 日志中。一旦 ‘print_date’ 任务成功完成，Airflow 就会进入 ‘print_message’ 任务。与前一个任务类似，它使用 PythonOperator 执行 “print_message” 函数。在该函数内部，一条简单的消息 “Hello, this is a message from your DAG!” 会被打印到 Airflow 日志中。

这些任务通过任务依赖关系链接在一起，由 `>>` 运算符表示，确保 ‘print_message’ 任务仅在 ‘print_date’ 任务成功完成后才运行。这种依赖关系确保了 DAG 内部任务执行的逻辑顺序。

## 步骤 3：上传到 S3

在 DAG 开发完成后，下一步是将 DAG 部署到 Amazon MWAA。此部署中的第一个任务是将包含 DAG 的文件上传到 Amazon MWAA 环境可访问的 Amazon S3 存储桶。下面的命令将 `simple_mwaa_dag.py` DAG 文件从 Amazon EC2 上的 `/home/ubuntu/airflow/dags/` 目录上传到 `instance1bucket` S3 存储桶中的 `dags` 文件夹：

```bash
aws s3 cp /home/ubuntu/airflow/dags/simple_mwaa_dag.py \
      s3://instance1bucket/dags/
```

DAG 文件及其依赖项通常在加载到 S3 存储桶之前被打包成 zip 文件。在这个简单的示例中，DAG 文件（`simple_mwaa_dag.py`）没有外部依赖项；因此，部署时无需将其打包成 zip 文件。然而，随着 DAG 复杂性的增加以及引入诸如自定义 Python 模块或第三方库等外部依赖项，将 DAG 打包成 zip 文件变得必不可少。

一个复杂 DAG 的好例子是我们第 8 章开发的 `tesla_stock_prediction` DAG。在该章中，我们创建了一个 Airflow 管道，该管道包括使用 PySpark 对特斯拉股票数据进行预处理，以及使用 PyTorch 构建、训练和评估一个深度学习模型来预测特斯拉股价。该 DAG 包含以下五个模块：

- `data_processing.py`：对特斯拉股票数据进行预处理
- `model_training.py`：利用 PyTorch 库创建和训练用于特斯拉股价预测的神经网络回归模型





- `model_evaluation.py`：评估训练好的 PyTorch 模型在测试数据集上的性能
- `utils.py`：工具模块，将 Spark DataFrame 列转换为 PyTorch 张量
- `tesla_stock_prediction.py`：编排整个工作流程的 DAG

以下是这些模块中包含的代码：

### data_processing.py

```python
from pyspark.sql import SparkSession
from pyspark.ml.feature import VectorAssembler, StandardScaler
from pyspark.sql import DataFrame

def load_data(file_path: str) -> DataFrame:
    """
    使用 SparkSession 从 CSV 文件加载股价数据。
    """
    spark = SparkSession.builder \
        .appName("StockPricePrediction") \
        .getOrCreate()
    df = spark.read.csv(
        file_path,
        header=True,
        inferSchema=True
    )
    return df

def preprocess_data(df: DataFrame) -> DataFrame:
    """
    通过使用 VectorAssembler 组装特征向量，
    并使用 StandardScaler 对其进行缩放来预处理数据。
    """
    assembler = VectorAssembler(
        inputCols=['Open', 'High', 'Low', 'Volume'],
        outputCol='features'
    )
    df = assembler.transform(df)
    scaler = StandardScaler(
        inputCol="features",
        outputCol="scaled_features",
        withStd=True,
        withMean=True
    )
    scaler_model = scaler.fit(df)
    df = scaler_model.transform(df)
    df = df.select('scaled_features', 'Close')
    return df
```

### model_training.py

```python
import torch
import torch.nn as nn
import torch.optim as optim
from torch.utils.data import DataLoader, TensorDataset

def create_data_loader(features, labels, batch_size=32) -> DataLoader:
    """
    将预处理后的数据转换为 PyTorch 张量，
    并为训练集和测试集创建 DataLoader 对象。
    """
    dataset = TensorDataset(features, labels)
    return DataLoader(
        dataset,
        batch_size=batch_size,
        shuffle=True
    )

def train_model(model, train_loader, criterion, optimizer, num_epochs):
    """
    使用 DataLoader、定义的损失函数和优化器
    在训练数据上训练模型。
    迭代指定数量的轮次（epochs），
    计算损失并更新模型参数。
    """
    for epoch in range(num_epochs):
        for inputs, labels in train_loader:
            optimizer.zero_grad()
            outputs = model(inputs)
            loss = criterion(outputs, labels.unsqueeze(1))
            loss.backward()
            optimizer.step()

            print(
                f"Epoch [{epoch + 1}/{num_epochs}], "
                f"Loss: {loss.item():.4f}"
            )
```

### model_evaluation.py

```python
import torch

def evaluate_model(model, test_loader, criterion):
    """
    在测试数据上评估训练好的模型，
    以评估其性能。
    计算测试损失以及 R 平方分数等
    其他评估指标。
    """
    with torch.no_grad():
        model.eval()
        predictions = []
        targets = []
        test_loss = 0.0
        for inputs, labels in test_loader:
            outputs = model(inputs)
            loss = criterion(outputs, labels.unsqueeze(1))
            test_loss += loss.item() * inputs.size(0)
            predictions.extend(outputs.squeeze().tolist())
            targets.extend(labels.tolist())

        test_loss /= len(test_loader.dataset)
        predictions = torch.tensor(predictions)
        targets = torch.tensor(targets)

        ss_res = torch.sum((targets - predictions) ** 2)
        ss_tot = torch.sum((targets - torch.mean(targets)) ** 2)
        r_squared = 1 - ss_res / ss_tot
        print(f"Test Loss: {test_loss:.4f}")
        print(f"R-squared Score: {r_squared:.4f}")
        return test_loss, r_squared.item()
```

### utils.py

```python
import numpy as np
import torch
from typing import Tuple
from pyspark.sql import DataFrame

def spark_df_to_tensor(df: DataFrame) -> Tuple[torch.Tensor, torch.Tensor]:
    """
    将 Spark DataFrame 列转换为 PyTorch 张量。
    """
    features = torch.tensor(
        np.array(
            df.rdd.map(lambda x: x.scaled_features.toArray())
            .collect()
        ),
        dtype=torch.float32
    )
    labels = torch.tensor(
        np.array(
            df.rdd.map(lambda x: x.Close).collect()
        ),
        dtype=torch.float32
    )
    return features, labels
```

### tesla_stock_prediction.py

```python
from datetime import datetime, timedelta
from airflow import DAG
from airflow.operators.python_operator import PythonOperator
import logging
import torch
import torch.optim as optim
import torch.nn as nn
from torch.utils.data import DataLoader
import numpy as np
from pyspark.sql import DataFrame
from typing import Tuple
from utils import spark_df_to_tensor
from data_processing import load_data, preprocess_data
from model_training import create_data_loader, train_model
from model_evaluation import evaluate_model

data_file_path = "/home/ubuntu/airflow/dags/TSLSA_stock.csv"
logging.basicConfig(level=logging.INFO)
logger = logging.getLogger(__name__)

default_args = {
    'owner': 'airflow',
    'depends_on_past': False,
    'start_date': datetime(2024, 5, 1),
    'email_on_failure': False,
    'email_on_retry': False,
    'retries': 1,
    'retry_delay': timedelta(minutes=5),
}

dag = DAG(
    'tesla_stock_prediction',
    default_args=default_args,
    description='用于特斯拉股价预测的 DAG',
    schedule_interval=None,
)

def preprocess_data_task():
    try:
        df = load_data(data_file_path)
        df = preprocess_data(df)
    except Exception as e:
        logger.error(f"Error in preprocessing data: {str(e)}")
        raise

preprocess_data_task_obj = PythonOperator(
    task_id='preprocess_data_task',
    python_callable=preprocess_data_task,
    dag=dag,
)

def train_model_task():
    try:
        df = load_data(data_file_path)
        df = preprocess_data(df)
        train_df, test_df = df.randomSplit([0.8, 0.2], seed=42)
        train_features, train_labels = spark_df_to_tensor(train_df)
        train_loader = create_data_loader(
            train_features,
            train_labels,
            batch_size=32
        )

        input_size = train_features.shape[1]
        output_size = 1
        model = nn.Sequential(
            nn.Linear(input_size, 64),
            nn.ReLU(),
            nn.Linear(64, 32),
            nn.ReLU(),
            nn.Linear(32, 16),
            nn.ReLU(),
            nn.Linear(16, output_size)
        )
        criterion = nn.MSELoss()
        optimizer = optim.Adam(model.parameters(), lr=0.001)
        train_model(
            model,
            train_loader,
            criterion,
            optimizer,
            num_epochs=100
        )
    except Exception as e:
        logger.error(f"Error in training model: {str(e)}")
        raise

train_model_task_obj = PythonOperator(
    task_id='train_model_task',
    python_callable=train_model_task,
    dag=dag,
)

def evaluate_model_task():
    try:
        df = load_data(data_file_path)
        df = preprocess_data(df)
        train_df, test_df = df.randomSplit([0.8, 0.2], seed=42)
        test_features, test_labels = spark_df_to_tensor(test_df)
        test_loader = create_data_loader(
            test_features,
            test_labels,
            batch_size=32
        )
        input_size = test_features.shape[1]
        output_size = 1
        model = nn.Sequential(
            nn.Linear(input_size, 64),
            nn.ReLU(),
            nn.Linear(64, 32),
            nn.ReLU(),
            nn.Linear(32, 16),
            nn.ReLU(),
            nn.Linear(16, output_size)
        )
        model.load_state_dict(torch.load('trained_model.pth'))

        criterion = nn.MSELoss()
        evaluate_model(model, test_loader, criterion)
    except Exception as e:
        logger.error(f"Error in evaluating model: {str(e)}")
        raise

evaluate_model_task_obj = PythonOperator(
    task_id='evaluate_model_task',
    python_callable=evaluate_model_task,
    dag=dag,
)

preprocess_data_task_obj >> train_model_task_obj >> evaluate_model_task_obj
```

以下 Python 代码将包含 DAG 逻辑和任务实现的五个模块（data_processing.py、model_training.py、model_evaluation.py、utils.py 和 tesla_stock_prediction.py）打包成一个 zip 文件。此外，该代码创建一个列出 DAG 运行所需所有依赖项的 requirements.txt 文件，并将 DAG 文件上传到 Amazon S3：

```python
import os
import zipfile
import boto3

# 定义包含 DAG 文件的目录
dags_directory = '/home/ubuntu/airflow/dags'
```





# 定义要包含在 zip 文件中的文件名
```python
[In]: files_to_zip = [
        'data_processing.py',
        'model_training.py',
        'model_evaluation.py',
        'utils.py',
        'tesla_stock_prediction.py',
        'requirements.txt'
    ]

# 定义 zip 文件的名称
[In]: zip_file_name = 'tesla_stock_prediction.zip'

# 创建一个包含指定文件的 zip 文件
[In]: with zipfile.ZipFile(zip_file_name, 'w') as zip_file:
        for file_name in files_to_zip:
            file_path = os.path.join(dags_directory,
                                     file_name)
            zip_file.write(file_path, arcname=file_name)

# 将 zip 文件上传到 S3 存储桶
[In]: bucket_name = 'instance1bucket'
[In]: s3_client = boto3.client('s3')
[In]: s3_client.upload_file(
        zip_file_name,
        bucket_name,
        f'dags/{zip_file_name}')

# 清理：删除 zip 文件
[In]: os.remove(zip_file_name)
[In]: print("Files zipped and uploaded successfully.")
```

此代码准备并上传 DAG 文件到 Amazon S3。首先，导入必要的库。这包括用于与操作系统交互的 `os`，用于处理 zip 文件操作的 `zipfile`，以及用于与 Amazon Web Services (AWS) 服务（如 S3）交互的 `boto3`。包含 DAG 文件的目录被指定为 `dags_directory`，设置为 `/home/ubuntu/airflow/dags`。该目录包含构成 DAG 的 Python 文件以及执行所需的其他相关文件。定义了一个名为 `files_to_zip` 的列表，其中包含将被打包到 zip 文件中的文件名。这些文件包括定义 DAG 逻辑的 Python 脚本：

- data_processing.py
- model_training.py
- model_evaluation.py
- utils.py
- tesla_stock_prediction.py
- requirements.txt

zip 文件的名称被指定为 `zip_file_name`，设置为 `tesla_stock_prediction.zip`。该文件将作为准备好部署的 DAG 文件打包集合。启动 `zipfile.ZipFile` 上下文管理器来创建由 `zip_file_name` 指定的 zip 文件。在此上下文中，`files_to_zip` 中列出的每个文件都被添加到 zip 文件中。`arcname` 参数确保文件在 zip 文件中存储时具有与 `dags_directory` 中相同的目录结构。

一旦 zip 文件创建并填入了必要的文件，就需要将其上传到 S3 存储桶。桶名称被指定为 `instance1bucket`，并初始化用于 S3 的 `boto3` 客户端。然后在客户端上调用 `upload_file` 方法，指定本地 zip 文件、目标存储桶以及文件在存储桶中应存储的路径。

上传成功后，使用 `os.remove(zip_file_name)` 删除本地 zip 文件以清理工作区。最后，打印一条成功消息，表明文件已成功打包并上传。

以这种方式将 DAG 及其依赖项打包在一起，简化了部署过程，确保了所有必要组件的包含，并促进了不同环境中版本控制和依赖管理的一致性。

## 步骤 4：配置 MWAA 环境

在将 DAG 文件上传到指定的 S3 存储桶之后，部署流程的下一步是配置 MWAA 环境，以包含已上传的 DAG 并指定任何额外的设置，例如环境变量、连接和插件。这一步对于确保 MWAA 环境能够根据您的要求有效地管理和执行 DAG 至关重要。

要配置 MWAA 环境：

- 首先，访问 Amazon MWAA 控制台并导航到您打算部署 DAG 的目标 MWAA 环境的环境设置。
- 在环境配置中，找到专门用于 DAG 的部分，并指定已上传 DAG 文件的 S3 路径。这告知 MWAA DAG 文件在 S3 存储桶中的位置，并允许其检索该文件以执行。

除了指定 DAG 文件外：

- 设置环境变量，以提供 DAG 在运行时所需的配置参数或机密信息。

- 环境变量可以包括设置，如数据库连接字符串、API 密钥或 DAG 运行所需的任何其他敏感信息。

- 通过在 MWAA 环境中配置环境变量，您确保 DAG 能够访问必要的资源，而无需直接在 DAG 代码中暴露敏感信息。

此外，包含额外 Airflow 操作员、钩子或传感器的插件可能支持 DAG 内的特定功能：

- 确保在 MWAA 环境中安装并配置必要的插件，以提供执行 DAG 所需的功能。

- 这包括安装任何自定义或第三方插件，并在 MWAA 环境中指定其配置。

## 步骤 5：触发 DAG 执行

当 DAG 在 Amazon MWAA 环境中成功部署和配置后，您可以手动或在 MWAA 环境中基于预定义的计划触发其执行：

- 手动执行：您可以从 MWAA 控制台手动触发 DAG 的执行。在 MWAA 控制台中导航到 DAGs 视图，找到该 DAG，并通过单击“Trigger DAG”按钮来启动其执行。这将立即开始执行 DAG，您可以从 MWAA 控制台监控其进度并查看日志。
- 计划执行：或者，您可以计划 DAG 基于预定义的计划自动运行。在 MWAA 环境配置中，使用 `schedule_interval` 参数指定 DAG 执行的期望计划间隔。例如，要每天触发 DAG 执行，您可以在 DAG 定义中设置 `schedule_interval=timedelta(days=1)`。然后，Amazon MWAA 将根据指定的计划自动触发 DAG 的执行。

## 步骤 6：监控执行

一旦触发，Amazon MWAA 将根据定义的依赖关系和计划间隔开始执行 DAG 任务。任务将按照指定的顺序运行（例如，在 simple_mwaa_dag.py DAG 中，print_date 先执行，随后是 print_message）。您可以从 MWAA 控制台监控 DAG 执行的进度，查看任务日志，并排查可能出现的任何问题。

监控深度学习模型对于许多原因至关重要，特别是在由 Amazon MWAA 等服务管理生产环境中。一个原因是确保模型随时间的性能和准确性。由于数据分布的变化（数据漂移）或输入特征与目标变量之间关系的变化（概念漂移），模型可能会出现性能退化。持续监控有助于早期检测此类问题，从而允许及时进行重新训练或调整以保持准确性。

运营效率是监控深度学习模型的另一个关键原因。通过跟踪资源利用情况——如 CPU、GPU 和内存使用率——您可以确保模型高效运行并识别可能出现的任何瓶颈。监控延迟也至关重要，特别是对于满足响应时间要求至关重要的实时应用程序。确保模型可靠运行并在需要时可用是维持系统完整性的基础。监控可以检测模型操作中的故障或错误，便于快速故障排除并最小化停机时间。此外，它有助于理解和管理模型在变化负载下的可扩展性。

更重要的是，合规性和治理在许多行业中越来越重要，特别是那些处理敏感数据的行业，如金融和医疗保健。监控模型确保维护审计跟踪，这对于法规合规至关重要。最后，安全是受益于细致监控的另一个关键方面。通过检测异常模式或异常值，监控可以提醒您潜在的安全漏洞。

您可以通过两种方式监控您的深度学习模型：

- 通过 MWAA 控制台和 Apache Airflow UI 进行直接的 DAG 监控
- 使用 Amazon CloudWatch 进行全面的指标和日志跟踪

MWAA 控制台和 Apache Airflow UI 允许您设置、管理和监控包含数据预处理、模型训练、评估和部署等任务的工作流程。这使您能够自动化和计划这些任务，同时密切关注其执行和性能。

要使用 MWAA 控制台监控在 Amazon MWAA 中运行的 DAG，请按照以下步骤操作：

- 登录 AWS 管理控制台并导航到 Amazon MWAA 服务。
- 选择您的 DAG 正在运行的 MWAA 环境。这将打开环境详情页面。





- 在环境详情页面中，您将看到一个打开 Airflow UI 的选项。单击“Open Airflow UI”按钮，即可进入 Apache Airflow 网页界面。

- 监控 DAG：
  - DAG 视图：在 Airflow UI 中，您可以查看所有 DAG 的列表。此视图允许您检查每个 DAG 的状态、最近一次运行情况和调度计划。
  - 图形视图：点击特定的 DAG 可查看图形视图，该视图展示了 DAG 的结构以及每个任务的状态。
  - 树状视图：树状视图提供了随时间变化的 DAG 运行和任务状态的分层视图。
  - 甘特图：甘特图视图有助于可视化 DAG 中每个任务随时间变化的持续时间。
  - 代码视图：您还可以查看 DAG 的代码，以确保逻辑正确实现。
  - 日志：为了进行详细的调试和监控，您可以访问每个任务实例的日志，以查看输出以及在执行过程中发生的任何错误。

Amazon CloudWatch 通过跟踪各种指标和日志、创建仪表板以及设置警报来提供强大的监控功能，以便在发生性能问题、故障或其他关键事件时通知您。通过结合使用 MWAA 和 CloudWatch，您可以确保您的深度学习模型持续提供价值，同时保持高性能、可靠性和合规性的标准。

CloudWatch 提供了几项功能，可以帮助您跟踪 MWAA 环境、DAG 运行以及底层基础设施。以下是您可以如何使用 CloudWatch 来实现这一目的：

- 指标收集：
  - MWAA 指标：MWAA 会自动将指标发布到 CloudWatch。这些指标包括有关环境健康状况的信息，例如调度器、工作程序和网络服务器的状态，以及任务级和 DAG 级指标。
  - 自定义指标：您还可以使用 boto3 库将自定义指标从您的 DAG 或任务推送到 CloudWatch。例如，您可以发布诸如模型推理时间、准确率分数或资源使用率等指标。

- 日志监控：
  - 任务日志：可以将 Airflow 任务日志发送到 CloudWatch 日志。这允许您查看和搜索单个任务的日志，这对调试和监控模型的性能非常有用。
  - MWAA 环境日志：MWAA 还可以将与环境本身相关的日志发送到 CloudWatch 日志。这包括来自调度器、网络服务器和其他组件的日志。

- 警报和通知：
  - CloudWatch 警报：您可以基于 CloudWatch 指标设置警报，以便在特定事件发生时收到通知，例如任务高故障率、延迟增加或其他性能问题。
  - Amazon SNS：使用 Amazon Simple Notification Service (SNS) 在触发警报时接收通知（电子邮件、短信等）。

- 仪表板：
  - CloudWatch 仪表板：创建自定义仪表板以可视化您的 MWAA 环境和模型的指标和日志。这可以包括显示任务成功/失败率、执行时间、资源使用率和其他相关指标的图表。

# 摘要

在本书的最后这一章中，我们深入探讨了部署和监控深度学习模型的过程。使用 Amazon MWAA 简化了在云中设置、管理和扩展 Apache Airflow 环境的过程，消除了对手动基础设施管理的需求。

我们研究了部署过程中的步骤，包括设置环境、开发 DAG、上传到 S3、配置 MWAA 环境以及触发和监控 DAG 执行。本章重点关注两个监控工具：Amazon MWAA 控制台和 Amazon CloudWatch。我们还强调了监控深度学习模型的重要性，以确保其随时间保持性能和准确性，维持运营效率，遵守合规性和治理标准，并增强安全性。

# 索引

- **A**
  - 访问控制列表 (ACLs)，73
  - 准确率，29, 385-387, 395, 461, 465, 545
  - 自适应查询执行 (AQE)，116, 145, 146, 210
  - Airflow
    - Docker，95-100
    - 在 EC2 上，87
    - MWAA，87
    - 独立安装
      - 访问 airflow UI，93-95
      - 激活您的环境，87
      - 管理员用户，91, 92
      - 配置和设置，90, 91
      - 数据库，88
      - 安装和配置 PostgreSQL，88
      - 抽象层，87
      - 端口 8080，94
      - PostgreSQL shell，88, 89
      - PostgreSQL 支持，88
      - 调度器，92
      - tmux/screen，92
    - 更新和安装依赖项，87
    - web 服务器，92, 94
  - Airflow web 服务器，38, 92, 94, 95, 99
  - Amazon CloudFormation，28, 64
  - Amazon CloudWatch，704, 736-738
  - Amazon Elastic Block Store (EBS)，61
  - Amazon Machine Images (AMIs)，26, 61, 67
  - Amazon S3，2, 3, 70-75, 126, 184, 729, 731
  - Amazon S3 存储桶，78, 162, 164, 183, 381, 719
  - AmazonS3FullAccess 策略，107
  - Amazon Simple Storage Service (S3)
    - 配置存储桶属性，71, 72
    - 创建存储桶，71
    - IAM 角色，74, 75
    - 导航到 S3 仪表板，71
    - 可靠且具成本效益，70
    - 上传数据，74
  - Amazon Web Services (AWS)，1, 2, 56, 361, 703, 731
  - 一个 `__init__` 方法，118
  - Apache Airflow，30, 56
    - 活跃社区，30
    - 优势，48, 49
    - DAG
      - 配置，34, 36, 37
      - 默认参数，43
      - 定义，44
      - 导入语句，40
      - 提供上下文，45
      - 运行，37–39
      - 任务依赖项，45
      - 任务函数，41–43
      - 任务操作符，45
    - 深度学习，703
    - 部署选项，39
    - 开发，30
    - 糖尿病预测（参见 糖尿病预测）
    - Docker 容器化设置，39
    - 功能，30
    - MWAA，39
    - 替换，main() 函数，47, 48
    - 可扩展的数据处理管道，490, 584, 703
    - 独立 Airflow，39
    - 特斯拉股价预测（参见 特斯拉股价预测）
    - UI，46, 47
  - 应用程序接口 (API)，9, 85
  - AWS 账户
    - AWS 网站，59
    - 构建和部署，59
    - 创建一个新的 AWS 账户，59
    - 付款信息，60
    - 提供账户信息，59
    - 审查和确认，60
    - 支持计划，59
    - 验证您的身份，59
  - AWS CLI，4–6, 59, 75, 219, 434, 705
  - AWS CloudFormation，60
  - AWS 管理控制台，58, 62, 99, 105, 106, 705–708, 735
  - AWS Secrets Manager，74

- **B**
  - 反向传播，18, 236, 237, 373, 498
  - 平衡模型复杂度，390, 463
  - 基线模型，586
    - 调整超参数，602
    - convert_to_numpy 方法，591, 637
    - create_and_train_model 方法，592, 639
    - 当前性能水平，602
    - 数据增强，602
    - evaluate_model 方法，594, 640
    - 库，587
    - 日志记录，587
    - main 函数，596, 641
    - matplotlib.pyplot，587
    - 模型损失，601
    - 模型简化，602
    - numpy，587
    - 过拟合，602
    - 性能，验证集，602
    - predict_and_evaluate 方法，595, 641
    - preprocess_data 方法，588, 636
    - pyspark.ml.feature，587
    - pyspark.sql，587
    - 正则化，587, 603
    - 审查平台期，602
    - sklearn.metrics，587
    - tensorflow，587
    - 测试损失，599, 642
    - 训练损失图，601
    - TSLARegressor 类，587, 588, 635
  - BCEWithLogitsLoss 函数，384
  - 黑盒，214, 273, 353
  - BlockDeviceMappings，67
  - Boto3，86, 117, 151, 325, 361
  - boto3.client('s3') 方法，126
  - 广播连接，116, 210
  - 存储桶策略，73
  - 内置日志模块，362

- **C**
  - cache() 方法，327
  - 缓存，10, 116, 144, 210, 327, 567
  - calculate_average_price 函数，34, 45, 47
  - calculate_average_price(taco_df) 函数，34
  - calculate_descriptive_statistics 方法，121, 132
  - calculate_feature_target_correlation 方法()，338–340, 344, 352
  - CalledProcessError 异常，220
  - check_for_null_values 方法，117, 123, 135
  - 分类，321
  - 云计算解决方案，214
  - 命令行界面 (CLI)，4, 39, 48, 221
  - 统一计算设备架构 (CUDA)，85
  - 混淆矩阵，29, 30, 378, 387
  - convert_to_numpy() 方法，279, 287, 299, 591, 637
  - convert_to_tensor() 函数，160, 162
  - 卷积神经网络 (CNNs)，19
  - copy_and_print_data()，217, 218, 221
  - copy_file_from_s3() 函数，128, 151, 175, 183, 186, 340–343, 382
  - count_outcome 方法，334, 335, 352
  - count_zeros() 方法，330, 331, 347
  - create_and_train_model() 方法，281, 288, 289, 299, 592, 600, 603, 607, 639




# 索引

create_data_loader() 函数，150, 161, 162, 182, 187, 233, 234  
create_taco_dataframe 函数，43  
create_taco_dataframe(spark) 函数，33  
CSV 文件，4, 51, 117, 125, 176, 216, 250, 327, 435  
CustomCallback 类，441, 445  
自定义回调 (CustomCallback)，438, 444, 453, 536  
自定义 Keras 回调，438, 443, 444

## D

数据增强，322, 389, 463, 466, 602  
Databricks，55, 83  
- 访问 S3，103  
- 凭据，108  
- dbutils.fs.mount 函数，110  
- else;，110  
- 如果 mount_point_exists 为真，109  
- 代码行，109  
- 挂载操作，105  
- MOUNT_NAME，109  
- mount_point_exists = any(mount.mountPoint == MOUNT_NAME for mount in mounts)，109  
- mounts = dbutils.fs.mounts()，109  
- print("S3 桶挂载失败。")，110  
- print("S3 桶挂载成功。")，109  
- 变量赋值，104  
- 创建账户，102  
- AWS 管理控制台，105, 106  
- 确认您的电子邮件，103  
- DataFrame，111–113  
- 环境，105  
- 探索，103  
- IAM 角色，107, 108  
- 登录，103  
- 注册，102  
- 创建工作区，103  
数据探索，116  
- 使用 PySpark，191–195  
DataFrame，111–113, 120–122, 125, 221, 222, 226, 228, 258  
DataFrame (self.data)，327  
数据框架，1, 450  
数据库，8  
DataLoader，225, 233, 234  
使用 PySpark 进行数据准备  
- 用于 PyTorch，149, 199–205  
  - 批处理，165  
  - convert_to_tensor() 函数，160, 162  
  - copy_file_from_s3，162  
  - create_data_loader 函数，161, 162  
  - 数据准备流程，149  
  - df = assembler.transform(df)，155  
  - 功能，163  
  - 正在运行，167  
  - load_data() 函数，150  
  - logging.basicConfig(level=logging.INFO)，151  
  - logger = logging.getLogger(name)，151  
  - logging 模块，150  
  - main()，167  
  - NumPy，150  
  - 参数，163  
  - perform_feature_engineering，156  
  - preprocess_data 函数，168  
  - price_change，171  
  - price_range，171  
  - print_first_5_observations 函数，159, 168  
  - pyspark.sql，150  
  - scaled_features 列，173  
  - 缩放后的特征值，173  
  - 缩放，173  
  - StandardScaler，150  
  - tensor_features，160  
  - 特斯拉股价，171  
  - VectorAssembler，150  
  - volume_price_interaction，171  
- 用于 TensorFlow，174, 205–210  
  - appName 方法，176  
  - batch 方法，183  
  - Boto3，175  
  - copy_file_from_s3 函数，183, 186  
  - create_data_loader 函数，182, 187  
  - 来自 pyspark.sql 的 DataFrame，175  
  - 特征工程操作，180  
  - load_data 函数，176  
  - 日志信息，179  
  - logging 模块，174  
  - main() 函数，188  
  - NumPy，175  
  - perform_feature_engineering 函数，179  
  - preprocess_data(df) 函数，189  
  - preprocess_data 函数，177  
  - 预处理步骤，179  
  - price_change，180  
  - print_first_5_observations 函数，181, 186  
  - pyspark_tensorflow_preparation.py，188  
  - s3.download_file 方法，184  
  - 洗牌，183  
  - 来自 pyspark.sql 的 SparkSession，174  
  - StandardScaler，175  
  - tensorflow as tf，175  
  - tf.data.Dataset.from_tensor_slices 方法，182  
  - VectorAssembler，175, 178  
  - volume_price_interaction，181  
数据预处理，2, 56, 115, 278, 321, 428  
DataPreprocessor 类，364, 367, 382  
DataProcessor 类，118, 121, 125, 132  
DataProcessor 对象，128, 129  
数据表示，90, 322, 463  
数据集，116–137, 276–277, 321, 323  
数据集，特斯拉股票，214  
- load_data，216  
- logging 模块，215  
- 模块，215  
- pyspark.sql 模块，215  
- SparkSession，216  
- subprocess 模块，215  
数据来源，S3，3  
- AWS CLI，4  
- Boto3，5, 6  
- check=True 参数，5  
- EC2，4  
- 逆向过程  
  - AWS CLI，6  
  - Boto3，6, 7  
  - 参数，7  
- s3_client.download_file() 方法，6  
- try/except 块，5  
data_summary() 方法，331–334, 349  
更深的模型，626, 628  
深度学习，703  
- 神经网络，18  
- 任务，25  
- 变量，18  
AWS 上的深度学习环境  
- 创建账户，59, 60  
- Amazon EC2 实例，60–70  
- Amazon S3，70–75  
- Databricks，102–113  
- 依赖项，83–86  
- 安装  
  - airflow，87–100  
  - Boto3，86  
  - JupyterLab，100–102  
- 项目目录，75–79  
- 虚拟环境，80–83  
深度学习模型的部署与监控 (MWAA)，704, 735, 738  
- CloudWatch，737, 738  
- DAG 开发，705, 716–718  
- DAG 执行，705, 733, 734  
- 环境设置，704  
  - 访问 MWAA 控制台，706  
  - 配置，716  
  - 创建 MWAA 环境，706  
  - 创建过程，716  
  - DAG 文件，707  
  - 环境类，715  
  - 环境详情，706  
  - 执行角色，707  
  - 互联网网关，711, 712  
  - NAT 网关，712–714  
  - 网络配置，707  
  - 路由表，714  
  - S3 桶，707  
  - 安全组，715  
  - 子网，710, 711  
  - VPC，707–709  
- 监控执行，706  
- CloudWatch，736  
- 合规与治理，735  
- 持续监控，734  
- 正在运行的 DAGs，735, 736  
- 故障与错误，735  
- 延迟，734  
- MWAA 控制台，735  
- 运营效率，734  
- 性能与准确率，734  
- 监控工具，738  
- MWAA 环境  
  - 配置，705, 732, 733  
  - S3 上传，705  
  - 命令，719  
  - DAG 文件，719, 731  
  - DAG 模块，719, 731  
  - DAGs 打包，732  
  - data_processing.py 模块，720, 721  
  - files_to_zip，731  
  - instance1bucket，731  
  - model_evaluation.py 模块，723, 724  
  - model_training.py 模块，721–723  
  - Python 代码包，729, 730  
  - requirements.txt 文件，729  
  - tesla_stock_prediction，719  
  - tesla_stock_prediction.py 模块，725–729  
  - utils.py 模块，724, 725  
深度学习工作流组件，2, 3  
- 数据预处理（*参见* PySpark 数据预处理）  
- 数据来源（*参见* 数据来源，S3）  
- 模型构建（*参见* PyTorch; TensorFlow）  
- 模型部署（*参见* Apache Airflow）  
- 模型评估，28, 29  
- 模型训练，EC2（*参见* Elastic Compute Cloud (EC2)）  
def__init__(self)，282  
依赖项安装与配置  
- Keras，85, 86  
- PySpark，83, 84  
- PyTorch，85  
- TensorFlow，85, 86  

开发环境，55–56, 100  
使用 K 折交叉验证的糖尿病分类，415–428  
不使用 K 折交叉验证的糖尿病分类，403–415  
糖尿病分类器模型，372, 376, 383, 384  
DiabetesClassifierModel 类，369  
diabetes_classifier_pipeline.py，383  
diabetes.csv，326, 340, 345, 382, 434  
DiabetesHyperModel 类，467, 469  
DiabetesModelEvaluator 类，453, 455  
DiabetesModelEvaluator.evaluate_model() 方法，459  
DiabetesModelTrainer 类，450, 452, 469  
DiabetesModelTrainer.train_tensorflow_model() 方法，459  
DiabetesPedigreeFunction，349–353, 388, 437  
糖尿病预测  
- 使用 Airflow DAG  
  - AWS EC2 实例，556  
  - DAG 对象，550  
  - 默认参数，548, 549  
  - evaluate_task，554, 555  
  - 执行，582–584  
  - 导入，547, 548  
  - main() 函数，546  
  - 指标，558  
  - preprocess_task，551, 552  
  - 任务依赖关系，556  
  - 训练损失，557  
  - train_task，553, 554  
- 不使用 Airflow DAG  
  - 列，544  
  - 评估指标，545, 546  
  - main() 函数，529, 574  
  - main.py 模块，529, 541–543, 581  
  - model_evaluation.py 模块，529, 538–541, 579, 580  
  - model_training.py 模块，529, 533, 535–537, 576–579  
  - 模块，529  
  - myenv 环境，543, 544  
  - preprocessing.py 模块，529–533, 574, 576  
  - 脚本编排，543  
  - 训练损失，544, 545  
DiabetesProcessor 类，441, 442, 445, 447, 448, 458  
DiabetesProcessor.preprocess_data() 方法，458  
有向无环图 (DAGs)，31, 130, 247, 489  
Docker，703  
- 访问 airflow Web 界面，99, 100  
- airflow 及其依赖项，95  
- Airflow 服务，99  
- compose，95  
- Compose 配置，98  
- 配置，95  
- Docker Compose，97  
- 下载，98  
- 初始化 Airflow 数据库，99  
- 安装，95  
- 包，95  
- 准备环境，98  
- 运行测试 Docker 容器，97  
- 可执行脚本，96  
- 脚本文件，96  
- 具有 root 权限的脚本，96  
- 验证 Docker 安装，96  
文档字符串，120–122, 152, 176, 329, 335  
文档字符串 """类，447, 452, 454  
文档字符串 """自定义 Keras 回调，445  
download_file 方法，6, 126, 163, 184, 382  
Dropout，585, 651–658  
- create_and_train_model 方法，607  
- dropout 比率，609  
- 层，607  
- 修改，基线模型，609  
- 神经元，607  
- 欠拟合/过拟合，609  
- 损失值，606  
- 输出，605, 606  
- 性能，验证集，603  
- 训练过程，603  
- TSLARegressor 类，643  
弹性块存储 (EBS)，27, 61, 67  
弹性计算云 (EC2)，1, 19  
- 加速计算类型，23–25  
- 优势，26  
- 计算优化类型，22, 23  
- 通用型，19, 20  
- GPU，25  
- 实例类型，19, 56  
- 内存优化类型，20, 21  
- 模型评估，28, 29  
- 预配置机器镜像，26  
- 设置/配置，26–28  
- 存储优化类型，21, 22  
- TPU，25  
环境变量，74, 98, 104, 705, 733  
Epoch/Loss 表，462  
错误处理，48, 244, 449, 453, 455, 541  
evaluate_model 函数，238, 239, 244  
evaluate_model 方法，291, 292, 299, 594, 640  
异常处理，228, 229, 373, 378  
explore_feature_distributions() 方法，336, 344, 354  

## E

早停法，585, 643–650  
- create_and_train_model 方法，603  
- EarlyStopping 回调，605





# 索引

### F

- Facebook 人工智能研究实验室 (FAIR)，13, 362
- 特征工程，115, 136, 354, 448
- 前馈网络，15, 18
- FileNotFoundError 异常，220
- file_path 参数，119
- Fit 方法，179, 231, 453, 605
- F1 得分，18, 29, 358, 386, 462, 466, 541, 558
- 基本市场动态，223, 277

### G

- getOrCreate()，153, 176, 217, 283
- 梯度下降，18, 233, 354
- 梯度，14, 236, 373, 498, 499, 501
- 图形处理单元 (GPUs)，24, 25, 85
- 网格搜索，629

### H

- handle_missing_values() 方法，329, 330, 345
- HVM 虚拟化，61
- 超参数优化
  - Keras Tuner，586, 690–701
  - 网格搜索，629
  - 模型训练过程，632
  - 随机搜索，629, 630
  - R2 得分，634
  - 测试数据集，634
  - 训练过程，634
  - TSLAHyperModel 类，630, 631, 634, 691
  - tuner.search 函数，634
- 超参数调优
  - TensorFlow，390
  - DiabetesHyperModel 类，467
  - DiabetesModelTrainer，469, 470
  - 导入，467
  - keras_tuner，467
  - 模型性能，466
  - 优化模型性能，471

### I

- 身份与访问管理 (IAM) 角色，74, 75, 105–108
- import os，434
- 入站规则，62, 93, 99, 102
- \_\_init\_\_ 方法，118, 282, 372
- 中容量模型，623, 625
- 每秒输入/输出操作次数 (IOPS)，21
- isNull()，330

### J

- JupyterLab，55, 76
  - 配置，101
  - 配置安全组与访问，101, 102
  - 集成开发环境，100
  - 安装，100
  - 设置密码，101
  - 启动，101
- JupyterLab 终端，247, 344, 383, 436, 460
- Jupyter Notebook，55, 77, 100, 101

### K

- Keras，13, 85, 86, 612
- Keras 的 Sequential API，452
- Keras Tuner
  - 超参数优化，629–634, 690–700
- K 折交叉验证，390
  - 均衡评估，391
  - 重要性，391
  - 导入 KFold，391
  - 遍历每个折，392–395
  - 折的数量，391

### L

- L1 和 L2 正则化，658–674
  - 基线神经网络模型，610
  - 基线 TensorFlow 模型，614
  - create_and_train_model 方法，610
  - Keras，612
  - 损失函数，586, 610
  - 修改，基线模型，612, 613
  - 神经网络，586
  - 输出，615
  - 过拟合，615
  - R2 得分，614, 615
  - 平方值，参数，610
  - 平方值，权重到损失函数，586
  - 测试损失，614, 615
  - 值，参数，610
- 学习率，674–682
  - create_and_train_model 函数，618
  - 高，616
  - 影响，模型训练与性能，619
  - 低，616
  - 中等学习率，618
  - TensorFlow 的 Adam 优化器，616
  - 测试损失，619
  - 训练深度学习模型，616
- 作为 Lasso 的线性模型，586
- 作为 Ridge 的线性模型，586
- load_data 函数，151, 166, 174, 186, 216, 228, 493
- load_data 方法，118, 129, 327, 328
- LocalExecutor，90, 91
- local_file_path，128, 130, 163, 186, 219, 343
- logger.error() 方法，449, 453, 459
- 日志记录，179, 362, 373, 598
- logging.basicConfig(level=logging.INFO)，444
- Logging 模块，150, 174, 215, 279, 362, 444
- 逻辑回归，323
- 损失函数不平衡，358

### M

- 机器学习 (ML)，4, 22, 55, 135, 181, 230, 247, 352, 491
- main() 函数，188, 254, 255, 279, 342–344, 596, 597, 641
- 托管 Apache Airflow 工作流 (MWAA)，1, 39, 87, 703
- Matplotlib，123, 596
- Matplotlib 库，281
- matplotlib.pyplot，117, 281, 587
- Matthews 相关系数 (MCC)，29
- 平均绝对误差 (MAE)，18, 239
- 均方误差 (MSE)，14, 18, 28, 239
- 方法日志，373
- 指标表，385, 387, 461–463
- missing_counts DataFrame，329
- 模型偏差，357
- 模型容量，682–690
  - 基线模型，620
  - 基线模型配置，623
  - 基线结果，628
  - 更深层模型，626, 628
  - 容量过剩，619
  - 改进，性能指标，624
  - 容量不足，619
  - 中等容量，622
  - 神经元数量，隐藏层，620, 621
  - 结果，622, 623, 625
  - TSLARegressor 类，层，620
  - 调优模型容量，625
  - 宽模型，625, 628
- 模型复杂度，390, 428, 463, 466, 621
- model.eval()，239, 254
- model.evaluate() 方法，440
- ModelEvaluator 类，363, 374, 376, 394, 453
- model.fit() 方法，440
- 建模步骤，278, 322, 364, 429, 438
- 模型学习，358
- model.load_state_dict()，254
- model_loss_plot.png，600
- ModelTrainer 类，372, 373, 394
- myenv，37, 38, 81, 221, 247, 383, 508, 598

### N

- \_\_name\_\_ 变量，187
- 神经网络架构，17, 353, 369, 443
- 神经网络，13, 18, 86, 213, 367, 586
- null_counts DataFrame，125
- NumPy，150, 225, 362, 443
- NumPy 数组，246, 287–289, 292, 293, 296, 591
- num_workers 参数，233

### O

- on_epoch_end 方法，445
- os.system 函数，434
- 出站规则，62
- 过拟合，183, 234, 291, 309, 370, 428, 585

### P, Q

- 并行处理
  - 在 PySpark 中，195–199
- 括号 ()，434
- Parquet 格式，43, 144, 145, 449, 540
- 性能指标，360, 363, 374, 377, 440, 527, 624
- perform_feature_engineering(df) 函数，189
- perform_feature_engineering 函数，179
- Pima，322
- Pima 数据集，388–390, 396–402, 463
- PimaDatasetExplorer 类，325, 326, 330, 343
- PimaDatasetExplorer 实例，344
- Pima 数据集，PyTorch
  - 数据增强，389
  - 数据质量，388
  - 数据表示，390
  - 探索，396–402
  - 超参数调优，390
  - K 折交叉验证，390
  - 模型复杂度，390
  - 重采样技术，389
  - 迁移学习，389
- Pima 糖尿病数据集，TensorFlow 分类
  - CSV 文件，432
  - 导入必要的库，433–438
- Pima 印第安人糖尿病数据集，322, 323, 326
- plot_actual_vs_predicted() 函数，281
- plt.show()，123, 297
- PostgreSQL，87–91, 98
- 精确率，29, 377, 386, 388, 461, 465
- predict_and_evaluate() 方法，280, 299, 595, 599, 641
- 使用 PyTorch 预测糖尿病
  - 附加功能，360, 378, 380, 381, 383, 384
  - 数据预处理，382, 383
  - 评估指标，385–388
  - 从 S3 复制文件，382
  - 基于损失值的观察，385
  - 数据预处理，359
  - DataPreprocessor 类，364, 367
  - randomSplit 方法，367
  - VectorAssembler 对象，367
  - 特征，359
  - 导入库，361
    - boto3，361
    - logging，362
    - NumPy，362
    - pyspark.ml.feature，364
    - pyspark.sql.functions，364
    - pyspark.sql 模块，363
    - sklearn.metrics，363
    - torch，362
    - torch.nn，362
    - torch.optim，363
    - torch.utils.data，363
  - 模型定义，359
    - DiabetesClassifier 模型，369
    - forward 方法，370
    - 隐藏层，370
    - \_\_init\_\_ 方法，369
    - 层与激活函数，368
    - 模型性能，370
    - ReLU 激活函数，369
  - 模型评估，360
    - ModelEvaluator 类
      - 糖尿病分类模型，376
      - 基本组件，376
      - evaluate 方法，376, 377
      - 异常处理，378
      - \_\_init\_\_ 方法，376
      - 获取最终预测，377
      - 性能指标，374, 377
  - 模型训练，360
    - 模型训练
      - 异常处理，373
      - 前向传播，373
      - 梯度，373
      - \_\_init\_\_ 方法，372
      - 方法日志，373
      - ModelTrainer 类，370, 372, 373
      - 神经网络模型，360
  - Pima 数据集（参见 Pima 数据集，PyTorch）
- 使用 TensorFlow 预测糖尿病
  - 自定义 Keras 回调，438, 444, 445
  - 数据预处理，445–449
  - 数据处理，439
  - 导入，438, 441
    - col，442
    - logging，441
    - numpy，443
    - Sequential，442
    - sklearn.metrics，442
    - SparkSession，442
    - tensorflow.keras.callbacks，443
    - tensorflow.keras.layers，443
    - tensorflow.keras.optimizers，443
  - VectorAssembler，442
  - StandardScaler，442
  - Keras，439
  - 日志配置，438, 443, 444
  - main 函数，456–462
  - 模型架构与训练，439
  - 模型定义与训练，439, 450–453
  - model.evaluate()，440
  - 模型评估，439, 453–455
  - model.fit()，440
- predict_tsla_stock.py，598, 599
- preprocess_data(df) 函数，189, 190
- preprocess_data() 函数，150, 168, 187, 230–232
- preprocess_data() 方法，280, 328, 344, 447, 588, 636
- 预处理，14, 211, 230, 390
- print_first_5_observations 函数，168, 181, 186
- print_first_n_rows 方法，120, 131
- print_top10_records.py，436
- 进程 ID (PID)，94
- 项目目录
  - %%bash，77
  - 设计，75
  - mkdir 和 touch 命令，78
  - mkdir-p “$project_dir”，78
  - mkdir-p “$project_dir/data”，78
  - project_dir=”项目目录结构”，78, 79
  - 可重现性，75
  - 可扩展性与维护，75
  - 结构，76, 77
  - 结构化环境，75
  - tree “$project_dir” --dirsfirst，78
  - tree 命令，79
  - TSLA_stock.csv，78
- 项目目录结构，56
  - 属性，50
  - 优势，49
  - 特斯拉股价，50, 51
  - config.yaml，53
  - data，51
  - logs，51
  - output，52
  - README.md，53
  - 表示与概述，53, 54
  - requirements.txt，53
  - src，52
  - tests，52
  - vizualization，52
- 供应 Amazon EC2 实例
  - 访问你的 EC2 实例，63
  - 添加存储，61
  - Amazon CloudFormation，64
  - AMI，61
  - 关联安全组，63
  - AWS 模板格式版本，66





# 索引

- 配置 Amazon EC2 实例（续）
  - 选择实例类型，61
  - 配置，66
  - 配置实例详情，61
  - DeepLearningEC2 实例，66, 67
  - 描述，66
  - EBS 卷，64–66
  - InstanceSecurityGroup，68
  - JSON 脚本，68–70
  - 创建密钥对，63
  - 启动实例，60
  - 导航至 EC2 仪表板，60
  - 注意，64
  - Outputs 部分，68
  - Resources 部分，66, 67
  - 审核并应用更改，63
  - 审核并启动，63
  - 安全组，62
  - SSH 访问，64–66
  - 启动实例，64
  - 停止实例，64
  - 训练和推理任务，60
  - YAML 格式，68
- PySpark，83, 84, 116, 150, 230, 257, 329, 431
- PySpark 代码
  - 计算特征，324
  - 统计结果值，324
  - 统计零值，324
  - 数据摘要，324
  - 特征分布，324
  - 处理缺失值，323
- PySpark DataFrame
  - 代码解释，9–11
  - 创建，8, 9
  - 墨西哥卷饼的价格，31–33
  - 条件执行，34
  - 定义函数，33
  - 导入所需模块，33
  - main() 函数，34
  - 脚本执行，12
- PySpark 数据预处理，7, 56
  - 优势，7
  - 数据库，8
  - 集成，8
- PySpark 函数
  - calculate_feature_target_correlation 方法，338–340
  - 类定义，326
  - copy_file_from_s3 函数，340–342
  - 相关系数，352, 353
  - explore_feature_distributions() 方法，354
  - 特征工程，354
  - 特征选择，353
  - 模型可解释性，353
  - 模型优化，353
  - count_outcome 方法，334, 335
  - count_outcome() 方法，352
  - count_zeros() 方法，347
  - count_zeros 方法定义，330, 331
  - 数据集的特性，350
  - data_summary 定义，331–334
  - data_summary() 方法，349
  - diabetes_data_exploration.py，344
  - 糖尿病遗传函数（DiabetesPedigreeFunction）和年龄（Age），349
  - explore_feature_distributions 方法，336–338
  - handle_missing_values 定义，329, 330
  - handle_missing_values() 方法，345
  - 直方图，357
  - 导入，325
  - 无效读数，349
  - load_data 方法定义，327, 328
  - main 函数，342–344
  - preprocess_data 方法定义，328
  - 偏斜的数据分布
    - 损失函数不平衡，358
    - 模型偏差，357
    - 模型学习，358
    - 采样策略，358
  - 统计信息，350
  - 可疑值，352
  - 不平衡数据集，352
  - pyspark.ml.feature，150, 226, 280, 364, 442
  - pyspark_pytorch_preparation.py，168
  - PySpark show() 方法，220
  - PySpark 的并行处理，116, 136–149, 210
  - pyspark.sql，117, 150, 174, 434
  - pyspark.sql.functions，117, 118, 364, 442
  - 从 pyspark.sql.functions 导入 col，325
  - 从 pyspark.sql 导入 SparkSession，325
  - pyspark.sql 模块，215, 226, 280, 325
  - PySpark 的 randomSplit() 方法，449
- Python 3，12, 80, 248, 301, 345, 460, 598
- Python 编程，221
- PyTorch，56, 61, 85, 439
  - 数据加载和预处理，14
  - 数据模型构建，14
  - 开发，13
  - 评估指标，18
  - 特征，13
  - 推理，14
  - 损失函数，14, 18
  - 模型评估，14
  - 模型训练，14
  - 神经网络模型，15–17
  - 优化器，14
  - 输出层激活函数，17
  - *对比* TensorFlow，305–308
  - 工作流，15
- PyTorch DataLoader 对象，161, 162
- PyTorch 机器学习模型，230, 232
- PyTorch 多层算法，428
- PyTorch 张量，160, 162, 202, 226, 245, 254, 492, 502
- 使用 PyTorch 预测特斯拉股价，223
  - 探索特斯拉股票数据集，258
  - 基本市场动态，223
  - 建模过程，224
  - DataLoader 创建函数，232–234
  - 数据加载函数，227–229
  - 数据预处理函数，229–232
  - 执行，247
  - 辅助函数，245–247
  - 导入，224–226
  - 日志记录设置，226, 227
  - main 函数，240–244
  - 模型评估函数，238–240
  - 模型训练函数，234–237
  - 绘制实际值与预测值对比，269–272
  - 以及 PySpark，260–268
  - Python 代码，223
  - 技术方面，223
  - 交易量，223

# R

- 随机搜索，629, 630
- randomSplit() 方法，286, 367
- read.csv() 方法，217, 285, 448
- 召回率，386, 462
- 受试者工作特征曲线下面积（ROC-AUC），29
- 整流线性单元（ReLU），243, 309, 369, 452
- 循环神经网络（RNNs），19
- 回归，321
- 重分区，116, 137–139, 210
- 重采样技术，389
- 弹性分布式数据集（RDDs），138, 245, 288
- 右偏分布，357
- ROC-AUC 分数，360, 363, 378, 386, 394, 395
- R2 分数，279, 280, 299, 302, 303, 305, 599
- r2_score 函数，280
- R 平方分数，239, 240, 248, 249, 273, 294, 307, 501
- RuntimeError，229

# S

- s3_bucket_name，128, 130, 186, 343
- Scikit-Learn，363, 440
- s3.download_file() 方法，126, 184
- 安全组，62, 63, 93, 101, 715
- Sequential 类，280
- SequentialExecutor，90, 91
- s3_file_key，128, 130, 343
- show() 方法，9, 11, 34, 220, 330, 331, 335, 436
- 简单存储服务（S3），1, 70
- sklearn.metrics，280, 363, 442, 540, 587
- 软件开发工具包（SDK），6, 75
- Spark DataFrame (diabetes_df)，367
- Spark DataFrames，280
- spark_data_processing.py，221
- spark_df_to_tensor 辅助函数，245, 246
- SparkSession，117, 118, 215, 216, 228, 280, 363, 382, 434, 436, 458
- SparkSession.builder API，458
- SparkSession.builder 方法，10, 128, 228
- SparkSession 类，9, 215, 280, 343, 363, 434
- SparkSession 对象，117–119, 128, 150, 152, 216, 217
- SQLite，87, 90
- SSH 密钥对，63, 67
- StandardScaler，115, 150, 175, 231, 280, 448, 588
- StandardScaler 对象，156, 179, 367, 448
- stat.corr() 方法，340
- @staticmethod 装饰器，448, 452, 455
- 随机梯度下降（SGD），14, 443, 453, 536
- StockPricePrediction，128, 152, 217, 494
- Subprocess 模块，4, 215
- subprocess.run() 方法，5, 243

# T

- TensorDataset，150, 162, 225–226, 233, 363
- tensor_features，160
- TensorFlow，56, 61, 85, 86, 213
  - 计算图，13
  - 数据加载和预处理，14
  - 开发，13
  - 评估指标，18
  - 推理，14
  - Keras，13
  - 损失函数，14, 18
  - 模型构建，14
  - 模型评估，14
  - 模型训练，14
  - 神经网络模型，15–17
  - 优化器，14
  - 输出层激活函数，17
  - *对比* PyTorch，305–308
  - 工作流，15
- tensorflow.keras.callbacks，443, 605
- tensorflow.keras.layers 模块，281
- TensorFlow (Keras) 模型，450, 453, 460
- tensorflow.keras.models，280, 442
- tensorflow.keras.optimizers，443
- 具有固定超参数的 TensorFlow 模型，472–479
- 具有超参数调优的 TensorFlow 模型，479–487
- TensorFlow *对比* PyTorch
  - 对比分析，463
  - 评估指标，465, 466
  - 损失值对比，64, 465
- 使用 TensorFlow 预测特斯拉股价，277
  - 实际值与预测值对比，305
  - environment.yml，310
  - 层和激活函数，309
  - 建模步骤，278
    - 条件块，300–303
    - convert_to_numpy 方法，286–288
    - create_and_train_model 方法，288–291
    - evaluate_model_method，291, 292
  - 导入，279–281
  - 日志记录设置，281–283
  - main 函数，298, 299
  - plot_actual_vs_predicted 函数，295–297
  - predict_and_evaluate 方法，293–295
  - preprocess_data() 方法，283–286
  - 面向对象方法，278
- TensorFlow 回归代码，310–319
- TSLARegressor，278
- 张量处理单元（TPUs），24, 25
- 特斯拉股价预测
  - main() 函数，491
  - 模块化方法，490
  - 模块化设计，491
  - 算子，491
  - PyTorch，491
  - 可扩展性和性能，491
  - 使用 Airflow DAG
    - AWS EC2 实例，525
    - 检查点，568
    - 列，526
    - DAG 定义，512, 516–518
    - 数据集，567
    - 默认参数，512, 515
    - 动态 DAGs，568
    - 模型评估任务，512, 522–524
    - 执行，569, 571–573
    - 实现，568
    - 导入，512, 513
    - 数据解释，527
    - 加载配置，568
    - main() 函数，511, 567
    - 输出，525
    - 性能指标，527, 528
    - 数据预处理任务，512, 518, 519
    - stock_price_prediction，525
    - 任务依赖，512, 524, 525
    - 任务，513, 514
    - 训练损失值，525, 526
    - 模型训练任务，512, 520–522
  - 不使用 Airflow DAG
    - 列，509
    - data_processing.py 模块，492–495, 559, 560
    - 关键指标，510, 511
    - main() 函数，507, 508
    - main.py 模块，492, 503, 504, 506, 564, 566, 567
    - model_evaluation.py 模块，492, 499–502, 562, 563
    - model_training.py 模块，492, 496, 498, 560–562
    - 模块，492, 507
    - myenv 环境，508
    - 输出，508, 510
    - 训练损失，509, 511
    - utils.py 模块，492, 502, 503, 563
- tesla_stock_price_prediction.py，247, 250, 300
- 测试损失，599, 615, 619, 642
- tf.data.Dataset.from_tensor_slices 方法，182
- .toPandas()，125
- toPandas 方法，123
- torch.load()，254
- torch.save 方法，244
- torch.utils.data，150, 225, 363
- 训练损失，248, 249, 301–303, 463, 509
- train_model 函数，235, 237, 244
- 迁移学习，322, 389, 463, 466
- Transform 函数，448
- TSLAHyperModel 类，630, 631, 691
- tsla_regressor，296, 299
- TSLARegressor 类，278, 279, 282, 283, 291, 295, 296, 299, 587, 588, 596, 620, 635

# U

- 用户界面（UI），38, 45, 47, 55, 92





# **V**

- VectorAssembler，115，150，154，155，170，230，231，280，283，285，367，448
- VectorAssembler，StandardScaler，442
- 虚拟环境，54–56
  - 激活，82
  - bin，81
  - 创建，80
  - 依赖项，80
  - 目录和文件，81
  - EC2 实例，80
  - include，81
  - lib64，82
  - myenv，81
  - 导航，80
  - Python 3，80
  - pyvenv.cfg，82
  - 可复现性，80
  - Ubuntu，80
- 虚拟私有云（VPC），27，68，70
- visualize_data 方法，117，121，136

# **W, X**

- 宽模型，625，628

# **Y**

- YAML 格式，68

# **Z**

- zero_counts 数据框，331
- zero_grad 方法，237

