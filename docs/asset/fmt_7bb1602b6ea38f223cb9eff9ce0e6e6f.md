
作业完成后，请检查 S3 中的 `s3://MLSA-DataLake-Serving-<your initials>/ml-customer-churn/<date>/<guid>/` 路径，查看是否生成了新的 csv 文件。打开该文件，查看在文件中是否看到了处理后的数据集。

你现在已成功构建了一个 AWS Glue 作业，用于用于机器学习的数据处理和特征工程。现在，通过创建一个爬虫（crawler）来爬取 `MLSA-DataLake-Serving-<your initials>` 存储桶中新处理的数据，使其在 Glue 目录中可用，并对其运行一些查询。你应该能看到创建一个新表，其中包含多个分区（例如 `ml-customer-churn`、`date` 和 `GUID`），对应不同的训练数据集。你可以使用 GUID 分区作为查询条件查询数据。

### 使用 Glue 工作流构建数据流水线

现在，创建一个流水线，它将运行一个数据摄取作业，然后为数据创建数据库目录，并运行数据处理作业以生成训练数据集：

- 首先，点击 Glue 管理控制台左侧面板中的“Workflows”（工作流）链接。
- 点击“Add Workflow”（添加工作流），并在下一个屏幕上为你的工作流输入名称。然后，点击“Add Workflow”按钮。
- 选择你创建的工作流并点击“Add Trigger”（添加触发器）。选择“Add New”（新建）选项卡，然后为触发器输入名称，并选择“on-demand”（按需）触发器类型。
- 在 UI 设计器中，你将看到出现一个新的“Add Node”（添加节点）图标。点击“Add Node”图标，选择“Crawler”（爬虫）选项卡，并选择 `bank_customer_db_crawler`，然后点击“Add”（添加）。
- 在 UI 设计器中，点击爬虫图标，你将看到出现了一个新的“Add Trigger”（添加触发器）图标。点击“Add Trigger”图标，选择“Add new”选项卡，选择“After ANY event”（任何事件发生后）作为触发器逻辑，然后点击“Add”（添加）。
- 在 UI 设计器中，点击“Add Node”图标，选择“jobs”（作业）选项卡，并选择 `customer_churn_process` 作业。

7. 在工作流 UI 设计器上，最终的工作流应该看起来所示所示：

![](img/bd21298357d8484151447cff0b2f138b_140_0.png)

图 4.7 - Glue 数据流设计

8. 现在，你已准备好运行工作流。选择该工作流，并在“Actions”（操作）下拉列表中选择“Run”（运行）。你可以通过选择 Run ID 并点击“View run details”（查看运行详情）来监控运行状态。你应该能看到类似于下面的截图：

![](img/bd21298357d8484151447cff0b2f138b_140_1.png)

图 4.8 - Glue 工作流执行

9. 尝试删除 `customer_data` 和 `churn_list` 表并重新运行工作流。查看是否创建了新表。检查 `s3://MLSA-DataLake-Serving-<your initials>/ml-customer-churn/<date>/` S3 位置，验证是否创建了带有新数据集的新文件夹。

恭喜！你已经完成了实验，并学习了如何构建一个简单的数据湖及其支持组件，以实现数据目录、数据查询和数据处理。

## 总结

在本章中，我们涵盖了机器学习的数据管理考虑因素，以及企业级数据管理平台对于机器学习的形态。现在，你应该了解数据管理与机器学习生命周期的交点，以及如何在 AWS 上设计数据湖架构。为了将所学付实践，你还使用 Lake Formation 构建了数据湖。你练习了用于数据发现、查询和下游机器学习任务的数据摄取、处理和数据建模。你还培养了使用 AWS 数据管理工具的实战技能。

# scikit-learn 概述

`scikit-learn` 主要构建在三个基础库之上：NumPy、SciPy 和 matplotlib。NumPy 是一个基于 Python 的库，用于管理大型多维数组和矩阵，并提供了额外的数学函数来对数组和矩阵进行操作。SciPy 提供了科学计算功能，如优化、线性代数和傅里叶变换。Matplotlib 用于数据可视化的数据图表绘制。`scikit-learn` 是处理一系列常见数据处理和模型构建任务的既充分又有效的工具。

## 安装 scikit-learn

你可以轻松地在 Mac、Windows 和 Linux 等不同操作系统上安装 `scikit-learn` 包。`scikit-learn` 库包托管在 Python 包索引网站（https://pypi.org/）和 Anaconda 包存储库（https://anaconda.org/anaconda/repo）上。若要在你的环境中安装它，你可以使用 PIP 包管理器或 Conda 包管理器。包管理器允许你在你的操作系统中安装和管理库包的安装。

要使用 PIP 或 Conda 包管理器安装 `scikit-learn` 库，你可以简单地运行 `pip install -U scikit-learn` 从 PyPI 索引安装它，或者在你想使用 Conda 环境时运行 `conda install scikit-learn`。你可以在 https://pip.pypa.io/ 了解更多关于 PIP 的信息，可以在 http://docs.conda.io 了解 Conda。

## scikit-learn 的核心组件

`scikit-learn` 为机器学习提供了全 Python 类，从数据处理到构建可重复的流水线。图显示了 `scikit-learn` 库包中的主要组件：

![](img/bd21298357d8484151447cff0b2f138b_146_0.png)

图 5.1 – scikit-learn 组件

## 理解 scikit-learn 机器学习库

现在，让我们仔细观察这些组件如何支持机器学习生命周期的不同阶段：

- **准备数据：** 对于数据操作和处理，通常使用 `pandas` 库。它提供了核心的数据加载和保存函数，以及用于数据操作（如数据选择、数据排列和数据统计测量）的实用程序。`pandas` 构建在 NumPy 之上。`pandas` 库还自带一些可视化功能，如饼图、散点图和箱线图。

`scikit-learn` 提供了一系列用于数据处理和转换的转换器（transformers），如填充缺失值、对类别值、归一化以及文本和图像的特征提取。你可以在 https://scikit-learn.org/stable/data_transforms.html 找到转换器的完整列表。你也可以创建自定义转换器的灵活性。

- **模型训练：** `scikit-learn` 提供了大量的机器学习算法（也称为估计器 estimators），用于分类和回归（例如逻辑回归、K 近邻算法和随机森林），以及聚类（例如 k-means）。你可以在 https://scikit-learn.org/stable/index.html 找到算法的完整列表。下面的示例代码显示了使用 `RandomForestClassifier` 算法使用带标签数据集训练模型的语法：

```python
from sklearn.ensemble import RandomForestClassifier

model = RandomForestClassifier(max_depth, max_features, n_estimators)

model.fit(train_X, train_y)
```

- **模型评估：** `scikit-learn` 拥有用于超参数调优和交叉验证的实用程序，以及用于模型评估的指标。你可以在 https://scikit-learn.org/stable/model_selection.html 找到模型选择和评估实用程序的完整列表。下面的示例代码显示了用于评估分类模型准确性的 `accuracy_score` 类：

```python
from sklearn.metrics import accuracy_score

acc = accuracy_score(true_label, predicted_label)
```

- **模型保存：** `scikit-learn` 可以使用 Python 对象序列化（pickle 或 joblib）保存模型产物。序列化的 pickle 文件可以被加载到内存中进行预测。下面的示例代码显示了使用 `joblib` 类保存模型的语法：

```python
import joblib

joblib.dump(model, "saved_model_name.joblib")
```

- **流水线（Pipeline）：** `scikit-learn` 还提供了一个流水线工具，可以将转换器和估计器连接成单一的处理流水线，并作为一个单一单元重复使用。当你需要为模型训练和模型预测预处理数据时，这特别有用，因为这两部分数据需要相同的方式处理：

```python
from sklearn.pipeline import Pipeline
from sklearn.preprocessing import StandardScaler
from sklearn.ensemble import RandomForestClassifier

pipe = Pipeline([('scaler', StandardScaler()), (RF, RandomForestClassifier())])

pipe.fit(X_train, y_train)
```

如你所见，上手 `scikit-learn` 机器学习包来实验和构建机器学习模型是非常简单的。`scikit-learn` 非常适用于常见的回归、分类和聚类机器学习任务；如果你需要在大型数据集或多台机器上训练机器学习，`scikit-learn` 通常不会是正确的选择，除非算法（例如 `SGDRegressor`）支持增量训练（递进式训练）。接下来，我们将查看一些可以处理大规模机器学习的机器学习库。

## 理解 Apache Spark ML 机器学习库

Apache Spark 是一个用于大规模数据处理的分布式数据处理框架。它允许基于 Spark 的应用程序跨分布式机器集群在内存中加载和处理数据，以加速处理时间。

一个 Spark 集群由一个主节点和工作节点组成，用于运行不同的 Spark 应用。它们由集群管理器（例如 Mesos、YARN 或 standalone）协调，负责为应用程序分配资源。具体来说，执行器配置了诸如 CPU 核心数和内存等资源。一旦分配了执行器，集群管理器就会应用程序代码（Java 或 Python 文件）发送给执行器。下面的图显示了驱动程序如何与集群管理器和执行器交互以运行任务：

![](img/bd21298357d8484151447cff0b2f138b_149_0.png)

图 5.2 – 在集群上运行 Spark 应用

每个 Spark 应用都获得自己的执行器集，这些执行器在应用程序运行期间保持开启。执行器之间是隔离的，仅通过外部存储共享数据。

Spark 的机器学习包称为 MLlib，它运行在分布式 Spark 架构之上。它可以处理无法放入单机内存的大数据集并训练模型。它提供了不同语言的 API，包括 Python、Java、Scala 和 R。从角度来看，它与 `scikit-learn` 非常相似。Spark 非常受欢迎被各种规模的公司采用。Netflix、Uber 和 Pinterest 等大公司使用 Spark 进行大规模数据处理和转换以及运行机器学习模型。

# 理解 Apache Spark ML 学习库

要开始使用 Spark 功能，你需要创建一个 Spark session。Spark session 会创建一个 `SparkContext` 对象，它是 Spark 功能的入口。以下示例代码展示了如何创建一个 Spark session：

```python
from pyspark.sql import SparkSession

spark = SparkSession.builder.appName('appname').getOrCreate()
```

Spark DataFrame 可以从许多不同的数据源构建，例如结构化数据文件（如 CSV 或 JSON）和外部数据库。以下示例代码显示了将 CSV 文件读取到 Spark DataFrame 中：

```python
dataFrame = spark.read.format('csv').load(file_path)
```

Spark 中有许多用于数据处理和转换的转换器（transformers），例如 `Tokenizer`（将文本分解为单词）和 `StandardScaler`（将特征归一化为单位标准差或零均值）。你可以在 https://spark.apache.org/docs/2.1.0/ml-features.html找到支持的转换器列表。

要使用转换器，首先你必须用参数初始化它，然后在包含数据的 DataFrame 上调用 `fit()` 函数，最后调用 `transform()` 函数来转换 DataFrame 中的特征：

```python
from pyspark.ml.feature import StandardScaler

scaler = StandardScaler(inputCol="features", outputCol="scaledFeatures",withStd=True,withMean=False)

scalerModel = scaler.fit(dataFrame)

scaledData = scalerModel.transform(dataFrame)
```

- **模型训练：** Spark ML 支持大量用于分类、聚类、推荐和主题建模的机器学习算法。你可以在 https://spark.apache.org/docs/1.4.1/mllib-guide.html 机器学习算法列表。以下代码示例展示了如何训练逻辑回归模型：

```python
from pyspark.ml.classification import LogisticRegression

lr_algo = LogisticRegression(maxIter=regParam, elasticNetParam=Param)

lr_model = lr_algo.fit(dataFrame)
```

- **模型评估：** 对于模型选择、超参数调优和模型评估指标，Spark ML 提供了交叉验证工具。你可以在 https://spark.apache.org/docs/latest/api/python/pyspark.ml.evaluation.MulticlassClassificationEvaluator.html?highlight=model%20evaluation找到评估器列表：

```python
from pyspark.ml.evaluation import BinaryClassificationEvaluator

dataset = spark.createDataFrame(scoreLabels, ["raw", "label"])

evaluator = BinaryClassificationEvaluator()

evaluator.setRawPredictionCol("raw")

evaluator.evaluate(dataset, {evaluator.metricName: "areaUnderPR"})
```

- **Pipeline（Pipeline）：** Spark ML 还支持类似于 `scikit-learn` 的流水线概念。通过流水线概念，你可以将一系列转换和模型训练步骤序列化为一个统一的可重复步骤：

```python
from pyspark.ml import Pipeline
from pyspark.ml.classification import LogisticRegression
from pyspark.ml.feature import HashingTF, Tokenizer

lr_tokenizer = Tokenizer(inputCol, outputCol)

l_hashingTF = HashingTF(inputCol=tokenizer, getOutputCol(), outputCol)

lr_algo = LogisticRegression(maxIter, regParam)

lr_pipeline = Pipeline(stages=[lr_tokenizer, lr_hashingTF, lr_algo])

lr_model = lr_pipeline.fit(training)
```

- **模型保存：** Spark ML 流线可以序列化为一种名为 MLeap bundle 的序列化格式，这是 Spark 的外部库。序列化的 MLeap bundle 可以被反序列化到 Spark 用于批量评分，或化到 MLeap 运行时用于实时 API。你可以在 https://combust.github.io/mleap-docs/ 找到更多关于 MLeap 的详情。以下代码显示了将 Spark 模型序列化为 MLeap 格式的语法：

```python
import mleap.pyspark
from pyspark.ml import Pipeline, PipelineModel

lr_model.serializeToBundle("saved_file_path", lr_model.transform(dataframe))
```
