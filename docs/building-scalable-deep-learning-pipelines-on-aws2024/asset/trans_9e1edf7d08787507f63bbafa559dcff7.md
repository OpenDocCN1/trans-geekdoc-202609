

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

