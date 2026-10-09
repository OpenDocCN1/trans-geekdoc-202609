

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

