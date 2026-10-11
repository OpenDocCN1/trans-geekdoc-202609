
### 依赖说明

- `tensorflow as tf`：TensorFlow 将在 `create_data_loader()` 函数中使用，以创建用于批量处理的 TensorFlow Dataset。
- `boto3`：Boto3 将在 `copy_file_from_s3()` 函数中使用，以与 AWS S3 交互并从指定的 S3 存储桶下载文件到本地文件路径。

### 日志记录设置

```python
logging.basicConfig(level=logging.INFO)
logger = logging.getLogger(__name__)
```

这些行配置日志记录系统，以输出级别为 `INFO` 或更高的日志消息。然后为当前脚本创建一个名为 `logger` 的日志记录器对象。

### `load_data` 函数

接下来，我们创建 `load_data` 函数，该函数使用 `SparkSession` 从 CSV 文件加载特斯拉股价数据：

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

- 该函数接受一个字符串类型的单个参数 `file_path`，并返回一个 `DataFrame` 对象。
- 使用三引号包围的文档字符串提供了对函数目的的简要描述，即使用 `SparkSession` 从 CSV 文件加载股价数据。
- 在函数内部，使用构建器模式创建了一个名为 `spark` 的 `SparkSession` 对象。调用构建器方法以初始化 `SparkSession` 配置。`appName` 方法将应用程序名称设置为 `"StockPricePrediction"`。最后，`getOrCreate()` 确保重用现有的 `SparkSession` 或在需要时创建新的 `SparkSession`。
- 该函数使用 `SparkSession` `spark` 从位于指定 `file_path` 的 CSV 文件中读取数据。它利用 `read.csv` 方法读取 CSV 文件，其中 `header=True` 表示第一行包含列标题，而 `inferSchema=True` 指示 Spark 自动推断列的数据类型。
- 将数据加载到名为 `df` 的 `DataFrame` 后，函数返回该 `DataFrame`。返回的 `DataFrame` 包含从 CSV 文件加载的特斯拉股价数据，可在程序中进行进一步处理或分析。

### `preprocess_data` 函数

随后，我们定义 `preprocess_data` 函数，通过组装特征向量、缩放特征和进行特征工程来预处理输入 `DataFrame`。该函数使用 PySpark 的 `VectorAssembler` 和 `StandardScaler` 来执行这些任务：

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

- 该函数接受一个 `DataFrame` `df` 作为输入，并在预处理后返回一个 `DataFrame`。
- 文档字符串提供了对函数目的的简要描述，即通过组装特征向量、使用 `StandardScaler` 对它们进行缩放以及执行特征工程来预处理数据。
- 在函数内部，创建一个名为 `assembler` 的 `VectorAssembler`，用于使用输入列 `'Open'`、`'High'`、`'Low'` 和 `'Volume'` 组装特征向量，输出列名为 `'features'`。然后应用 `transform` 方法，使用 `assembler` 转换输入 `DataFrame` `df`。
- 使用 `logger.info` 函数提供日志信息，以指示预处理步骤的进度。使用 `df.show` 方法显示组装特征后 `DataFrame` 的前五个观察值。
- 调用 `perform_feature_engineering` 函数，以在 `DataFrame` `df` 上执行额外的特征工程操作。
- 另一个预处理步骤涉及使用 `StandardScaler` 对特征进行缩放。创建一个名为 `scaler` 的 `StandardScaler` 对象，指定输入和输出列，以及标准化选项。然后对 `DataFrame` 应用 `fit` 方法以获取缩放器模型，并使用该模型转换 `DataFrame`。
- 最后，修改 `DataFrame` 以仅选择 `'scaled_features'` 和 `'Close'` 列，然后从函数中返回它。该 `DataFrame` 包含已预处理的数据，准备好用于进一步分析或建模。

### `perform_feature_engineering` 函数

在下一步中，我们创建 `perform_feature_engineering` 函数，该函数对 `DataFrame` 应用各种特征工程操作，例如创建交互项和从现有特征中提取有用信息：

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

- 该函数接受一个 `DataFrame` `df` 作为输入，并在执行特征工程后返回一个 `DataFrame`。
- 文档字符串提供了对函数目的的简要描述，即执行特征工程操作，例如创建交互项。
- 在函数内部，对 `DataFrame` `df` 执行特征工程操作：
  - 通过从每个观察值的 `'High'` 价格中减去 `'Low'` 价格，创建新列 `'price_range'`。这捕捉了每只股票的价格范围。
  - 通过从 `'Close'` 价格中减去 `'Open'` 价格，创建另一个新列 `'price_change'`。这代表给定时间段内的价格变化。
- 此外，通过 `Volume` 列与 `Close` 价格相乘生成了一个名为 `volume_price_interaction` 的新列。该交互项捕捉了交易量与股价之间的关系。
- 在这些特征工程操作之后，函数返回修改后的 `DataFrame` `df`，其中包含新创建的列以及原始特征。这些工程化的特征对于提高机器学习模型的性能或从数据中获取洞察可能非常有价值。

### `print_first_5_observations` 函数

接下来，我们创建 `print_first_5_observations` 函数，用于打印 `DataFrame` 的前五个观察值，并附带自定义标题：

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

- 该函数接受两个参数：`DataFrame` `df` 和字符串 `heading`。它不返回任何值。
- 文档字符串提供了对该函数目的的简要描述，即打印 `DataFrame` 的前五个观察值并附带自定义标题。
- 在函数内部，使用 `logger.info` 函数记录传入的自定义标题。
- 随后使用 `df.show` 方法显示 `DataFrame` `df` 的前五个观察值。参数 `truncate=False` 确保显示的列不被截断，从而展示每个列的完整内容。

### `create_data_loader` 函数

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
- 随后，使用 `shuffle` 方法对创建的数据集进行洗牌，缓冲区大小为 `10000`。洗牌有助于随机化数据集中元素的顺序，这在训练过程中可能有助于防止模型过拟合。
- 接下来，对洗牌后的数据集应用 `batch` 方法，将元素分组为大小为 `batch_size` 的批次。批处理允许在训练期间高效地按批次处理数据，从而减少内存使用并提高计算效率。
- 最后，函数返回创建的数据集，该数据集现已准备好用于在 TensorFlow 中训练机器学习模型。此数据集可以按批次进行迭代，以有效训练模型。

### `copy_file_from_s3` 函数

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
- 然后调用 `s3.download_file` 方法，将文件从指定的 S3 存储桶 `bucket_name` 和文件键 `file_key` 下载到本地文件路径 `local_file_path`。此方法处理从 S3 到本地系统的实际文件传输。
- 在文件成功下载后，使用 `logger.info` 函数记录信息，指示文件已从 S3 存储桶下载到本地文件路径。消息中包含诸如 S3 存储桶名称和文件保存的本地文件路径等详细信息。

### `main` 函数

在下一步中，我们定义 `main` 函数，该函数通过按顺序调用必要的函数来编排整个过程。它从 S3 存储桶复制文件、加载数据、预处理数据、将其转换为 NumPy 数组，并创建用于批量处理的 TensorFlow Dataset：
