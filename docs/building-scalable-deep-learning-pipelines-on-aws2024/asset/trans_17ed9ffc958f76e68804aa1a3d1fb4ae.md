

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

