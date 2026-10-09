

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

