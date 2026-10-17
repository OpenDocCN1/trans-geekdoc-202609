
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

下一行使用 `show()` 方法显示 DataFrame `df_selected` 的前 10 条记录：

```python
df_selected.show(10)
```

最后，我们停止 `SparkSession` 以释放分配给它的资源。在完成 Spark 作业后停止 `SparkSession` 是一个良好的实践：

```python
spark.stop()
```

为了执行代码，我们将其保存为 `print_top10_records.py` 并在 JupyterLab 终端中运行它。在创建一个名为 `myenv` 的环境后，我们使用以下命令激活它：

```bash
source /home/ubuntu/myenv/bin/activate
```

一旦环境被激活，我们使用 `spark-submit` 执行以下命令来运行代码：

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

请注意，血压（`BloodPressure`）和体重指数（`BMI`）中存在值为 0 的行，这表明读数无效。这些行将在模型训练和评估期间从数据集中排除。

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

### 步骤 3：自定义回调

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

### 步骤 4：数据预处理

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
```
