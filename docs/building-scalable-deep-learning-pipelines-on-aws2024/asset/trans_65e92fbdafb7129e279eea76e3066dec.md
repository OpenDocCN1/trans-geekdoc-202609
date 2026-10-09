

在 EC2 实例上的 `"/home/ubuntu/airflow/dags/"` 目录。`subprocess.run()` 函数使用指定的源路径和目标路径执行 AWS CLI 命令 `"aws s3 cp"`。

try/except 块用于处理命令执行期间可能出现的潜在错误。如果命令成功，try 块会打印 `"Download successful."`。如果命令失败并引发 `subprocess.CalledProcessError`，except 块会捕获该错误并打印一条指示发生错误的消息，同时附带错误详情。

`subprocess.run()` 中的 `check=True` 参数确保如果命令返回非零退出状态，则引发 `CalledProcessError`，从而触发 except 块。在此示例中，输出表明文件已成功从 S3 存储桶下载到本地目录。

运行此代码后，我们可以使用标准文件系统命令（例如 Linux/MacOS 中的 `'ls'`）来检查文件是否存在于该目录中：

```
[In]: ls /home/ubuntu/airflow/dags/
```

使用 Boto3：

```
[In]: import boto3
```

```
[In]: try:
    s3_client = boto3.client('s3')
    bucket_name = 'instance1bucket'
    key = 'TSLA_stock.csv'
    local_path = '/home/ubuntu/airflow/dags/TSLA_stock.csv'
    s3_client.download_file(bucket_name, key, local_path)
    print("Download successful.")
except Exception as e:
    print(f"An error occurred: {e}")
```

```
[Out]: Download successful.
```

在此代码中，使用 Boto3（Python 的官方 AWS SDK（软件开发工具包））与 Amazon S3 服务进行交互。使用 `s3_client.download_file()` 方法将文件 “TSLA_stock.csv” 从 S3 存储桶 “instance1bucket” 下载到 EC2 实例上的本地目录 “/home/ubuntu/airflow/dags/”。运行此代码后，文件 “TSLA_stock.csv” 应出现在指定的本地目录中。

将文件从目录复制到 S3 存储桶的过程，本质上是将文件从 S3 复制到目录过程的逆过程。

使用 subprocess 调用 AWS CLI：

```python
[In]: import subprocess

[In]: try:
         subprocess.run([
            "aws", "s3", "cp",
            "/home/ubuntu/airflow/dags/TSLA_stock.csv",
            "s3://instance1bucket/"
            ], check=True)
         print("File uploaded successfully.")
     except Exception as e:
         print(f"An error occurred: {e}")
```
[Out]: File uploaded successfully.

在此代码中，与从 S3 下载的代码相比，我们反转了源路径和目标路径的顺序。

使用 Boto3：

```python
[In]: import boto3

[In]: try:
         s3_client = boto3.client('s3')
         bucket_name = 'instance1bucket'
         key = 'TSLA_stock.csv'
         local_path = '/home/ubuntu/airflow/dags/TSLA_stock.csv'
         s3_client.upload_file(local_path, bucket_name, key)
         print("File uploaded successfully.")
     except Exception as e:
         print(f"An error occurred: {e}")

[Out]: File uploaded successfully.
```

在此代码中，与从 S3 下载的代码相比，我们反转了参数的顺序。换句话说，对于下载，参数为

s3_client.download_file(bucket_name, key, local_path)

对于上传，参数为

s3_client.upload_file(local_path, bucket_name, key)

值得注意的是，如果目标位置（本例中为 S3 存储桶）中已经存在该文件，并且我们尝试上传具有相同键（文件名）的文件，通常会用新文件覆盖现有文件。

## 数据预处理 (PySpark)

一旦按照上述步骤从 S3 检索到数据，它将使用 PySpark 进行预处理。PySpark 是一个分布式数据处理框架，能够对大型数据集进行高效的数据清洗、转换和特征工程。

利用 PySpark 进行预处理任务相比传统库如 Pandas 和 Scikit-Learn 具有独特的优势。首先，其分布式特性使 PySpark 在处理大数据任务时，相较于单节点处理工具具有卓越的扩展性和性能。其次，通过利用 PySpark 的分布式处理能力，预处理任务可以在多个节点上并行化，从而减少处理时间并实现对大规模数据集的高效处理。此外，PySpark 与其他机器学习流水线组件无缝集成，促进了从数据摄取到模型部署的一致且简化的工作流。

在 *《Distributed Machine Learning with PySpark: Migrating Effortlessly from Pandas and Scikit-Learn》*（Apres，2023 年 11 月）中，我们展示了从 Pandas 和 Scikit-Learn 等小数据库过渡到 PySpark 可以相对简单。虽然 Pandas 和 Scikit-Learn 主要设计用于小数据处理和分析，但在许多情况下，由于语法相似性，过渡变得更加容易。PySpark 提供了类似 Pandas 和 Scikit-Learn 的功能，包括数据预处理和特征工程。PySpark 中这些熟悉功能的存在，使习惯了使用 Pandas 和 Scikit-Learn 的数据科学家能够更顺畅地过渡。

在本节中，我们提供了一个使用 PySpark 创建 DataFrame 的简单示例，随后在 EC2 实例上打印该 DataFrame，作为其功能初步介绍。在第 3 章中，我们将深入探讨使用 PySpark 的数据准备技术。这包括更高级的主题，如数据探索、预处理、特征工程，以及为 PyTorch 和 TensorFlow 格式化数据：

```
[In]: from pyspark.sql import SparkSession
```

```
[In]: try:
    spark = (SparkSession.builder
        .appName("TacosDataFrame")
        .getOrCreate())
    data = [("Taco 1", "Beef", 2.50),
        ("Taco 2", "Chicken", 2.00),
        ("Taco 3", "Vegetarian", 2.00),
        ("Taco 4", "Fish", 3.00)]
    schema = ["Taco Name", "Type", "Price"]
    tacos_df = spark.createDataFrame(data, schema)

    # Cache the DataFrame to optimize performance
    tacos_df.cache()

    tacos_df.show()
except Exception as e:
    print(f"An error occurred: {e}")
finally:
    spark.stop()
```

[Out]:

| Taco Name | Type | Price |
|---|---|---|
| Taco 1 | Beef | 2.5 |
| Taco 2 | Chicken | 2.0 |
| Taco 3 | Vegetarian | 2.0 |
| Taco 4 | Fish | 3.0 |

上述代码创建了一个包含塔可相关数据（塔可名称、类型和价格）的 PySpark DataFrame，然后使用 `show()` 方法打印该 DataFrame。

以下是每行代码的解释：

- `from pyspark.sql import SparkSession`: 该语句从 PySpark 库的 `pyspark.sql` 模块中导入 `SparkSession` 类。`SparkSession` 是使用 DataFrame 应用程序编程接口 (API) 对 Spark 进行编程的主要接口。它促进与 Spark 的交互，并启用创建 DataFrame，这是分布式数据处理任务所必需的。

- `spark = SparkSession.builder`: 这一行使用 `SparkSession.builder` 方法创建一个新的 SparkSession。

- `.appName("TacosDataFrame")`: 这一行将 Spark 作业的应用名称设置为 “TacosDataFrame”。

- `.getOrCreate()`: 这一行如果存在现有的 SparkSession 则获取它，如果不存在则创建一个新的。

- `data = [("Taco 1", "Beef", 2.50), ...]`: 这一行定义了一个塔可相关数据的示例数据集。列表中的每个元组代表一行数据，包含三个值：塔可名称、类型和价格。

- `schema = ["Taco Name", "Type", "Price"]`: 这一行定义了 DataFrame 的模式（schema）。它指定列名为 “Taco Name”、“Type” 和 “Price”。

- `tacos_df = spark.createDataFrame(data, schema)`: 这一行使用 SparkSession 的 `createDataFrame()` 方法创建一个名为 `tacos_df` 的 DataFrame。它接受两个参数：数据（在 `data` 中定义）和模式（在 `schema` 中定义）。

- `tacos_df.cache()`: 将 DataFrame 缓存在内存中，以增强后续访问该 DataFrame 多次的操作性能。在处理大型数据集或进行计算密集型操作时，缓存特别有益，可防止不必要的重新计算。此方法在首次计算后将中间 DataFrame 存储在内存中，由对 DataFrame 的第一个操作（如转换或行动）触发。

