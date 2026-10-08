
scikit-learn 主要构建在三个基础库之上：NumPy、SciPy 和 matplotlib。NumPy 是一个基于 Python 的库，用于管理大型多维数组和矩阵，并提供了额外的数学函数来对数组和矩阵进行操作。SciPy 提供了科学计算功能，如优化、线性代数和傅里叶变换。Matplotlib 用于数据可视化的数据图表绘制。scikit-learn 是处理一系列常见数据处理和模型构建任务的既充分又有效的工具。

## 安装 scikit-learn

你可以轻松地在 Mac、Windows 和 Linux 等不同操作系统上安装 scikit-learn 包。scikit-learn 库包托管在 Python 包索引网站（https://pypi.org/）和 Anaconda 包存储库（https://anaconda.org/anaconda/repo）上。若要在你的环境中安装它，你可以使用 PIP 包管理器或 Conda 包管理器。包管理器允许你在你的操作系统中安装和管理库包的安装。

要使用 PIP 或 Conda 包管理器安装 scikit-learn 库，你可以简单地运行 `pip install -U scikit-learn` 从 PyPI 索引安装它，或者在你想使用 Conda 环境时运行 `conda install scikit-learn`。你可以在 https://pip.pypa.io/ 了解更多关于 PIP 的信息，可以在 http://docs.conda.io 了解 Conda。

## scikit-learn 的核心组件

scikit-learn 为机器学习提供了全 Python 类，从数据处理到构建可重复的流水线。图显示了 scikit-learn 库包中的主要组件：

![](img/bd21298357d8484151447cff0b2f138b_146_0.png)

图 5.1 – scikit-learn 组件

## 理解 scikit-learn 机器学习库

现在，让我们仔细观察这些组件如何支持机器学习生命周期的不同阶段：

- **准备数据：** 对于数据操作和处理，通常使用 pandas 库。它提供了核心的数据加载和保存函数，以及用于数据操作（如数据选择、数据排列和数据统计测量）的实用程序。pandas 构建在 NumPy 之上。pandas 库还自带一些可视化功能，如饼图、散点图和箱线图。

scikit-learn 提供了一系列用于数据处理和转换的转换器（transformers），如填充缺失值、对类别值、归一化以及文本和图像的特征提取。你可以在 https://scikit-learn.org/stable/data_transforms.html 找到转换器的完整列表。你也可以创建自定义转换器的灵活性。

- **模型训练：** scikit-learn 提供了大量的机器学习算法（也称为估计器 estimators），用于分类和回归（例如逻辑回归、K 近邻算法和随机森林），以及聚类（例如 k-means）。你可以在 https://scikit-learn.org/stable/index.html 找到算法的完整列表。下面的示例代码显示了使用 RandomForestClassifier 算法使用带标签数据集训练模型的语法：

```python
from sklearn.ensemble import RandomForestClassifier
model = RandomForestClassifier(max_depth, max_features, n_estimators)
model.fit(train_X, train_y)
```

- **模型评估：** scikit-learn 拥有用于超参数调优和交叉验证的实用程序，以及用于模型评估的指标。你可以在 https://scikit-learn.org/stable/model_selection.html 找到模型选择和评估实用程序的完整列表。下面的示例代码显示了用于评估分类模型准确性的 accuracy_score 类：

```python
from sklearn.metrics import accuracy_score
acc = accuracy_score(true_label, predicted_label)
```

**模型保存：** scikit-learn 可以使用 Python 对象序列化（pickle 或 joblib）保存模型产物。序列化的 pickle 文件可以被加载到内存中进行预测。下面的示例代码显示了使用 joblib 类保存模型的语法：

```python
import joblib
joblib.dump(model, "saved_model_name.joblib")
```

**流水线（Pipeline）：** scikit-learn 还提供了一个流水线工具，可以将转换器和估计器连接成单一的处理流水线，并作为一个单一单元重复使用。当你需要为模型训练和模型预测预处理数据时，这特别有用，因为这两部分数据需要相同的方式处理：

```python
from sklearn.pipeline import Pipeline
from sklearn.preprocessing import StandardScaler
from sklearn.ensemble import RandomForestClassifier

pipe = Pipeline([('scaler', StandardScaler()), (RF, RandomForestClassifier())])
pipe.fit(X_train, y_train)
```

如你所见，上手 scikit-learn 机器学习包来实验和构建机器学习模型是非常简单的。scikit-learn 非常适用于常见的回归、分类和聚类机器学习任务；如果你需要在大型数据集或多台机器上训练机器学习，scikit-learn 通常不会是正确的选择，除非算法（例如 SGDRegressor）支持增量训练（递进式训练）。接下来，我们将查看一些可以处理大规模机器学习的机器学习库。

## 理解 Apache Spark ML 机器学习库

Apache Spark 是一个用于大规模数据处理的分布式数据处理框架。它允许基于 Spark 的应用程序跨分布式机器集群在内存中加载和处理数据，以加速处理时间。

一个 Spark 集群由一个主节点和工作节点组成，用于运行不同的 Spark 应用。（*此处原文存在大量重复段落，已根据要求去重并保留核心逻辑*）它们由集群管理器（例如 Mesos、YARN 或 standalone）协调，负责为应用程序分配资源。具体来说，执行器配置了诸如 CPU 核心数和内存等资源。一旦分配了执行器，集群管理器就会应用程序代码（Java 或 Python 文件）发送给执行器。下面的图显示了驱动程序如何与集群管理器和执行器交互以运行任务：

![](img/bd21298357d8484151447cff0b2f138b_149_0.png)

图 5.2 – 在集群上运行 Spark 应用

每个 Spark 应用都获得自己的执行器集，这些执行器在应用程序运行期间保持开启。执行器之间是隔离的，仅通过外部存储共享数据。

Spark 的机器学习包称为 MLlib，它运行在分布式 Spark 架构之上。它可以处理无法放入单机内存的大数据集并训练模型。它提供了不同语言的 API，包括 Python、Java、Scala 和 R。从角度来看，它与 scikit-learn 非常相似。Spark 非常受欢迎被各种规模的公司采用。Netflix、Uber 和 Pinterest 等大公司使用 Spark 进行大规模数据处理和转换以及运行机器学习模型。
