

*   **模型评估**：对于模型选择和评估，Spark ML 提供了用于交叉验证、超参数调优和模型评估指标的实用程序。你可以在 [https://spark.apache.org/docs/latest/api/python/reference/api/pyspark.ml.evaluation.MulticlassClassificationEvaluator.html](https://spark.apache.org/docs/latest/api/python/reference/api/pyspark.ml.evaluation.MulticlassClassificationEvaluator.html) 找到评估器列表。以下代码块演示了如何使用 `BinaryClassificationEvaluator` 并结合 `areaUnderPR` 指标来评估模型：

```
From pyspark.ml.evaluation import BinaryClassificationEvaluator
dataset = spark.createDataFrame(scoreAndLabels, ["raw", "label"])
evaluator = BinaryClassificationEvaluator()
evaluator.setRawPredictionCol("raw")
evaluator.evaluate(dataset)
evaluator.evaluate(dataset, {evaluator.metricName: "areaUnderPR"})
```

*   **管道**：Spark ML 还支持管道概念，类似于 scikit-learn。通过管道概念，你可以将一系列转换和模型训练步骤排序为一个统一的可重复步骤：

```
from pyspark.ml import Pipeline
from pyspark.ml.classification import LogisticRegression
from pyspark.ml.feature import HashingTF, Tokenizer
lr_tokenizer = Tokenizer(inputCol, outputCol)
lr_hashingTF = HashingTF(inputCol=tokenizer.getOutputCol(), outputCol)
lr_algo = LogisticRegression(maxIter, regParam)
lr_pipeline = Pipeline(stages=[lr_tokenizer, lr_hashingTF, lr_algo])
lr_model = lr_pipeline.fit(training)
```

*   **模型保存**：Spark ML 管道可以序列化为一种称为 Mleap bundle 的序列化格式，这是 Spark 的外部库。序列化的 Mleap bundle 可以反序列化回 Spark 以进行批量评分，或用于 Mleap 运行时来运行实时 API。你可以在 [https://combust.github.io/mleap-docs/](https://combust.github.io/mleap-docs/) 找到更多关于 Mleap 的详细信息。以下代码展示了将 Spark 模型序列化为 Mleap 格式的语法：

```
import mleap.pyspark
from pyspark.ml import Pipeline, PipelineModel
lr_model.serializeToBundle("saved_file_path", lr_model.transform(dataframe))
```

Spark 是一个多功能框架，能够实现大规模数据处理和机器学习。虽然它在传统机器学习任务中表现出色，但也为神经网络训练提供了有限的支持，包括多层感知机算法。然而，为了获得更全面的深度学习功能，我们将在即将到来的章节中探讨专门的机器学习库，包括 TensorFlow 和 PyTorch。

# 理解 TensorFlow 深度学习库

TensorFlow 最初于 2015 年发布，是一个流行的开源机器学习库，主要由 Google 支持，主要用于深度学习。各种规模的公司都使用 TensorFlow 来训练和构建最先进的深度学习模型，用于各种用例，包括计算机视觉、语音识别、问答、文本摘要、预测和机器人技术。

TensorFlow 的工作原理基于计算图的概念，数据流经表示数学运算的节点。核心思想是构建一个操作和张量的图，张量是携带数据的 `n` 维数组。张量的示例可以是标量值（例如 `1.0`）、一维向量（例如 `[1.0, 2.0, 3.0]`）、二维矩阵（例如 `[[1.0, 2.0, 3.0]`, `[4.0, 5.0, 6.0]]`）甚至更高维的矩阵。在这些张量上执行操作，允许进行加法或矩阵乘法等数学计算。以下图示显示了一个示例计算图，用于对张量执行一系列数学运算：

![](OEBPS/Images/B20836_05_04.png)

图 5.4：数据流图

在上述计算图中，矩形节点是数学运算，而圆圈代表张量。这个特定的图显示了一个用于执行人工神经元张量操作的计算图，即执行 `W` 和 `X` 的矩阵乘法，然后加上 `b`，最后应用 `ReLU` 激活函数。等效的数学公式如下：

![](OEBPS/Images/B20836_05_001.png)

TensorFlow 允许用户使用其高级 API 定义和操作计算图，或者直接使用其低级组件。这种灵活性使研究人员和开发人员能够创建复杂的模型和算法。此外，TensorFlow 支持分布式计算，允许图在多个设备或机器上执行，这对于处理大规模机器学习任务至关重要。这种分布式架构使 TensorFlow 能够利用集群或 GPU 的能力来加速深度学习模型的训练和推理。

## 安装 TensorFlow

TensorFlow 可以在基于 Python 的环境中使用 `pip install --upgrade tensorflow` 命令进行安装。安装后，TensorFlow 可以像任何其他 Python 库包一样使用。

## TensorFlow 的核心组件

TensorFlow 库提供了一套丰富的功能，用于不同的机器学习步骤，从数据准备到模型服务。以下图示说明了 TensorFlow 库的核心构建块：

![](OEBPS/Images/B20836_05_05.png)

图 5.5：TensorFlow 组件

使用 TensorFlow 2.x 训练机器学习模型涉及以下主要步骤：

1.  **准备数据集**：TensorFlow 2.x 提供了一个 `tf.data` 库，用于高效地从源（例如文件）加载数据、转换数据（例如更改数据集的值）以及设置数据集以进行训练（例如配置批量大小或数据预取）。这些数据类提供了将数据传递给训练算法以进行优化模型训练的高效方式。TensorFlow `Keras` API 还提供了一系列内置类（MNIST、CIFAR、IMDB、MNIST Fashion 和 Reuters Newswire），用于构建简单的深度学习模型。你也可以将 NumPy 数组或 Python 生成器（表现得像迭代器的函数）馈送到 TensorFlow 中的模型进行模型训练，但 `tf.data` 是推荐的方法。

2.  **定义神经网络**：TensorFlow 2.x 提供了多种方法来使用或构建神经网络用于模型训练。你可以使用预制估计器（`tf.estimator` 类），例如 `DNNRegressor` 和 `DNNClassifier` 来训练模型。或者，你可以使用 `tf.keras` 类创建自定义神经网络，它提供了一系列原语，例如 `tf.keras.layers` 用于构建神经网络层，以及 `tf.keras.activation` 例如 ReLU、`Sigmoid` 和 `Softmax` 用于构建神经网络。Softmax 通常用作多类问题中神经网络的最后输出。它将一组实数（正数和负数）作为输入，并将向量归一化为概率分布，以表示不同类标签的概率，例如不同类型的手写数字。对于二进制分类问题，通常使用 Sigmoid，它返回 0 到 1 之间的值。

