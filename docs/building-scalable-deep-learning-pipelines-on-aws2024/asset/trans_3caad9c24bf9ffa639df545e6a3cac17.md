

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

