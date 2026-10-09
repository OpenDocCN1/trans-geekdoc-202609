
- else: 这行代码开始 else 代码块，当 if 语句中的条件（检查挂载点是否存在）评估为 False 时，该代码块将执行。换言之，如果指定的挂载点不存在于已挂载的文件系统列表中，则 else 语句内的代码块将会执行。

- print("S3 bucket mount failed."): 这行代码打印一条消息，表明 S3 存储桶的挂载操作失败。当指定的挂载点不存在于已挂载的文件系统列表中时，该代码会被执行。

现在，既然你已经成功使用 dbutils.fs.mount 函数将 S3 存储桶挂载到 Databricks 上，你便可以开始在 Databricks 内部对 S3 进行读写操作。下方的代码创建了一个塔可（taco）DataFrame，将其保存在挂载的 S3 存储桶中，然后再次读取它：

```python
[In]: data_to_write = [("Chicken Taco", 5.99),
                      ("Beef Taco", 6.49),
                      ("Vegetarian Taco", 4.99)]
[In]: df = spark.createDataFrame(data_to_write, ["Taco",
                                                "Price"])
[In]: df = df.repartition(1)
[In]: MOUNT_NAME = "/mnt/datalake-central"
[In]: df.write.mode("overwrite").parquet(
             MOUNT_NAME + "/taco_data_parquet"
             )
[In]: df_read = spark.read.parquet(MOUNT_NAME + "/taco_data_parquet")
[In]: df_read.show()
```

让我们来逐段解析代码的不同部分：

1. 创建 DataFrame：

```python
[In]: data_to_write = [("Chicken Taco", 5.99),
                      ("Beef Taco", 6.49),
                      ("Vegetarian Taco", 4.99)]
[In]: df = spark.createDataFrame(data_to_write,
                               ["Taco", "Price"])
```

这一部分创建了一个名为 df 的 DataFrame，其中包含塔可数据。它使用 spark.createDataFrame() 方法从元组列表 data_to_write 创建 DataFrame，其中每个元组包含一个塔可名称及其价格。列名“Taco”和“Price”在第二个参数中指定。

2. 保存 DataFrame：

```python
[In]: df = df.repartition(1)
[In]: MOUNT_NAME = "/mnt/datalake-central"
[In]: df.write.mode("overwrite").parquet(
              MOUNT_NAME + "/taco_data_parquet"
          )
```

这一部分使用 df.repartition(1) 将 DataFrame 重新分区为单个分区。Spark 中的分区是数据集的逻辑划分，允许并行处理。然后，它定义了挂载点 /mnt/datalake-central。最后，它使用 df.write.mode("overwrite").parquet() 将 DataFrame 保存为挂载的 S3 存储桶中名为“taco_data_parquet”的 Parquet 文件，如果存在现有文件则进行覆盖。

该文件将保存在 EC2 实例上的 S3 存储桶中，位于名为“taco_data_parquet/”的文件夹内，具体文件名如下：

```text
part-00000-tid-6689481035778156686-b47d6778-9a4c-48b3-950c-3ac770289ab1-453-1-c000.snappy.parquet
```

以及诸如“_SUCCESS”文件等其他文件，该文件指示写入操作已成功完成。snappy 文件包含实际数据，而其他文件属于 Spark 的内部处理过程，可以忽略。

3. 读取 DataFrame：

```python
[In]: df_read = spark.read.parquet(
       MOUNT_NAME + "/taco_data_parquet")
```

这一部分使用 spark.read.parquet() 将挂载的 S3 存储桶中的 Parquet 文件“taco_data_parquet”读回到一个名为 df_read 的 DataFrame 中。

4. 显示 DataFrame：

```python
[In]: df_read.show()
```

最后这一部分使用 show() 方法显示 DataFrame df_read 的内容。输出将显示具有"Taco"和"Price"列的 DataFrame 内容，如下所示：

| 塔可 (Taco) | 价格 (Price) |
| --- | --- |
| Chicken Taco | 5.99 |
| Beef Taco | 6.49 |
| Vegetarian Taco | 4.99 |

## 总结

在本章中，我们引导读者完成了在 Amazon Web Services (AWS) 上搭建深度学习环境以及配置必要工具和服务的过程。更具体地说，我们提供了关于如何创建 AWS 账户、配置 EC2 实例、设置 Amazon S3、创建项目目录、配置虚拟环境以及安装和配置依赖项（特别是 PySpark、PyTorch、TensorFlow、Airflow、Boto3 和 JupyterLab）的详细说明。我们还提供了关于如何设置 Databricks 账户和工作区的说明。

在下一章中，我们将介绍使用 PySpark 为深度学习任务准备数据的过程。我们将深入探讨数据探索、数据预处理、特征工程以及将数据格式化为 PyTorch 和 TensorFlow 兼容格式的关键方面。

# 第 3 章

## 使用 PySpark 为深度学习进行数据准备

本章介绍了使用 PySpark 为深度学习任务准备数据的过程。我们深入探讨了数据预处理、特征工程以及将数据格式化为 PyTorch 和 TensorFlow 兼容格式的关键方面。

数据预处理包括一系列旨在清洗和转换原始数据，使其适用于建模目的的步骤。这些步骤包括处理缺失值、缩放特征以及编码分类变量。为了说明这些概念，本章提供了代码示例，包括使用 VectorAssembler 组装特征向量，随后使用 StandardScaler 对其进行缩放。

特征工程在提升输入特征的质量和指导能力方面起着重要作用。它涉及创建新特征或转换现有特征，以封装更多信息。技术方法可能包括生成多项式特征、推导交互项以及处理日期时间特征（例如计算两个时间戳之间的差异或自特定事件以来经过的时间）。

此外，本章还涉及为深度学习任务格式化数据这一关键步骤。在预处理和特征工程之后，处理后的数据需要转换为与 PyTorch 和 TensorFlow 兼容的张量格式，以便这些框架能够高效处理。我们提供了代码示例，以说明如何将数据转换为 PyTorch 和 TensorFlow 张量，以及如何使用由数据加载器函数创建的 DataLoader 对象将数据组织为批次。

在深入探讨这些主题之前，重要的是首先要考虑 PySpark 的并行处理能力如何提高数据处理效率，特别是针对大型数据集。诸如重新分区、广播连接、缓存、使用高效的文件格式（如 Parquet）、优化 Shuffle 分区以及启用自适应查询执行 (AQE) 等技术，将在优化这些数据准备任务的性能方面发挥关键作用。

为了说明 PySpark 并行处理以及为大型数据集和深度学习准备数据这些概念，我们将使用一个包含特斯拉股票价格的历史数据集。该数据集将用于演示 PyTorch 和 TensorFlow 中的深度学习任务，特别是第 4 章和第 5 章分别涵盖的回归模型。

## 数据集

我们从 Yahoo! Finance 网站下载了 CSV 格式的特斯拉股票价格数据集，并使用以下链接将其存储在 AWS S3 存储桶中：

https://finance.yahoo.com/quote/TSLA/history/

让我们首先探索这个数据集，然后再使用它来说明 PySpark 如何为使用 PyTorch 和 TensorFlow 进行深度学习进行并行处理和数据准备。数据探索是理解数据集特征和模式的基础，并指导后续的预处理和特征工程步骤。我们的探索将包括打印数据集的前十行、执行描述性统计、检查缺失值以及可视化数据。通过这种使用 PySpark 的探索，我们获得了关于数据结构和分布的见解，为有效的深度学习数据准备奠定了基础。

我们首先导入脚本所需的库：

```python
[In]: import boto3
[In]: import matplotlib.pyplot as plt
[In]: from pyspark.sql import SparkSession
[In]: from pyspark.sql.functions import col
[In]: import pyspark.sql.functions as F
[In]: import numpy as np
```

以下是关于这些库的说明：

- boto3: 此库用于与 AWS 服务交互。它将在 copy_file_from_s3 函数中用于从 S3 存储桶下载特斯拉股票 CSV 文件。
- matplotlib.pyplot: 此库将用于在 visualize_data 方法中基于 DataFrame 创建可视化图表。
- 来自 pyspark.sql 的 SparkSession: 这是使用 DataFrame API 编程 Spark 的入口点。它将用于初始化以创建用于数据处理操作的 SparkSession 对象。
- 来自 pyspark.sql.functions 的 col: 此函数将在 check_for_null_values 方法中用于引用 DataFrame 列。

