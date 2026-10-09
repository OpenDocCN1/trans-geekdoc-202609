

- `toPandas()`：该方法将结果 DataFrame 转换为 Pandas DataFrame，以便于展示和分析结果。将 DataFrame 转换为 Pandas 格式可以使其与 Pandas 生态系统无缝集成，从而让用户能够利用其丰富的功能进行进一步的分析和可视化。

- 包含每列空值计数的结果 DataFrame 被存储在 `null_counts` 变量中。

- 随后打印 `null_counts` DataFrame 以显示每列的空值计数。

接下来讨论 `DataProcessor` 类之外的函数，我们有 `copy_file_from_s3` 函数，它用于将 CSV 文件从 S3 存储桶复制到 EC2 实例上的本地文件路径：

```python
[In]: def copy_file_from_s3(
        bucket_name: str,
        file_key: str,
        local_file_path: str
        ):
        """
        Copy file from S3 bucket to local file path.
        """
        try:
            s3 = boto3.client('s3')
            s3.download_file(bucket_name, file_key, local_file_path)
            print(f"File downloaded from S3 bucket {bucket_name} "
                  f"to local file path: {local_file_path}")
        except Exception as e:
            print(f"Error copying file from S3: {str(e)}")
```

- 在函数内部，使用 try-except 块来处理文件复制过程中可能出现的任何潜在错误。

- 在 try 块中
  - 使用 `boto3.client('s3')` 方法创建了一个 S3 客户端对象（`s3`）。此客户端提供对 Amazon S3 服务的访问权限。
  - 然后调用 `s3.download_file()` 方法，将文件从指定的 S3 存储桶（`bucket_name`）和键（`file_key`）下载到本地文件路径（`local_file_path`）。
  - 文件成功下载后，会打印一条确认消息，指示源 S3 存储桶和目标本地文件路径。
  - 如果在文件复制过程中发生异常（例如，由于网络问题或权限不正确），它将被 except 块捕获。
  - 在 except 块中
    - 打印一条错误消息，指示文件复制过程中发生错误的性质。这有助于诊断和排查出现的问题。

继续看主函数，这是脚本的主入口点。它初始化 SparkSession，从 S3 复制文件，初始化 DataProcessor，加载数据，并执行数据处理任务：

```python
[In]: def main(s3_bucket_name: str, s3_file_key: str, local_file_path: str):
    """
    Main function for stock price prediction.

    This function initializes a SparkSession, copies
    a file from an S3 bucket to a local file path,
    initializes a DataProcessor object, loads data
    from the local file, and performs various data
    processing tasks.

    :param s3_bucket_name:
        Name of the S3 bucket containing the file
    :param s3_file_key:
        Key of the file within the S3 bucket
    :param local_file_path:
        Local file path to save the downloaded file
    """
    spark = (SparkSession.builder
        .appName("StockPricePrediction")
        .getOrCreate())

    copy_file_from_s3(
        s3_bucket_name,
        s3_file_key,
        local_file_path
    )

    data_processor = DataProcessor(spark)
    df = data_processor.load_data(local_file_path)
    if df is not None:
        data_processor.print_first_n_rows(df)
        data_processor.calculate_descriptive_statistics(df)
        data_processor.check_for_null_values(df)
        data_processor.visualize_data(df)
    else:
        print("Error loading data. Exiting.")
```

- 该函数接受三个参数：`s3_bucket_name`、`s3_file_key` 和 `local_file_path`，分别代表包含文件的 S3 存储桶的名称、文件在 S3 存储桶中的键以及保存下载文件的本地文件路径。

- 在函数内部
  - 使用 `SparkSession.builder` 方法创建了一个 SparkSession 对象，应用名称为 “StockPricePrediction”。如果已经存在 SparkSession，则会重用该会话；否则，将创建一个新会话。
  - 调用 `copy_file_from_s3` 函数，将文件从指定的 S3 存储桶（`s3_bucket_name`）和键（`s3_file_key`）复制到本地文件路径（`local_file_path`）。
  - 使用之前创建的 SparkSession 初始化了一个 DataProcessor 对象。
  - 使用 DataProcessor 的 `load_data` 方法从本地文件加载数据。如果 DataFrame 加载成功（`df is not None`），则使用 DataProcessor 对象的方法执行各种数据处理任务：
    - 打印 DataFrame 的前 n 行（`print_first_n_rows`）
    - 计算 DataFrame 的描述性统计量（`calculate_descriptive_statistics`）
    - 检查 DataFrame 中的空值（`check_for_null_values`）
    - 基于 DataFrame 创建可视化（`visualize_data`）
  - 如果在数据加载过程中发生错误，将打印错误消息，并显示 “Error loading data. Exiting.”（加载数据时出错。正在退出。）消息终止程序。

进入最后一步，条件块检查该脚本是否作为主程序直接运行。它设置 S3 存储桶名称、文件键和本地文件路径的参数，然后使用这些参数调用主函数：

```python
[In]: if __name__ == "__main__":
    s3_bucket_name = 'instance1bucket'
    s3_file_key = 'TSLA_stock.csv'
    local_file_path = '/home/ubuntu/airflow/dags/TSLA_stock.csv'
    main(s3_bucket_name, s3_file_key, local_file_path)
```

- 在该块内部，定义了三个变量：
  - `s3_bucket_name`：一个字符串变量，表示文件所在的 S3 存储桶的名称
  - `s3_file_key`：一个字符串变量，表示文件在 S3 存储桶中的键
  - `local_file_path`：一个字符串变量，表示文件将被下载的本地文件路径

- 使用这些变量作为参数调用主函数。该函数协调整个数据处理过程，包括初始化 `SparkSession`、从 S3 存储桶复制文件、加载数据以及执行各种数据处理任务。

通过将代码封装在主函数中并条件性地执行，该脚本可以作为一个模块被导入到其他脚本中，而不会执行主功能。这增强了代码的可复用性和模块化。然而，当在第 8 章中将脚本作为有向无环图（DAG）在 Airflow 中运行时，不需要主函数，因为 Airflow 负责协调 DAG 内任务的执行。DAG 中的每个任务可以利用脚本中的特定函数或类，而无需执行主功能。

要运行该脚本，我们首先将其保存为 `tesla_stock_exploration.py`，激活 EC2 实例上的虚拟环境，然后使用以下命令运行 Python 脚本：

```bash
[In]: cd /home/ubuntu
[In]: source myenv/bin/activate
[In]: python3 tesla_stock_exploration.py
```

让我们现在检查代码的输出。

第一个输出是由 `copy_file_from_s3` 函数产生的消息，表明 CSV 文件已成功从 S3 存储桶下载到本地文件路径：

```text
[Out]: File downloaded from S3 bucket instance1bucket to local file
path: /home/ubuntu/airflow/dags/TSLA_stock.csv
```

第二个输出是由 `print_first_n_rows` 方法生成的包含 DataFrame 前 10 行的表格。这显示了特斯拉股票的 Date、Open、High、Low、Close 和 Volume 列。打印前 10 个观察值提供了一种简单有效的方法来快速概览数据集，并在进行更详细的分析或处理之前验证一切正常：

| 日期 | 开盘 | 最高 | 最低 | 收盘 | 成交量 |
|---|---|---|---|---|---|
| 2024/2/23 | 195.31 | 197.57 | 191.50 | 191.97 | 78,670,300 |
| 2024/2/22 | 194.00 | 198.32 | 191.36 | 197.41 | 92,739,500 |
| 2024/2/21 | 193.36 | 199.44 | 191.95 | 194.77 | 103,844,000 |
| 2024/2/20 | 196.13 | 198.60 | 189.13 | 193.76 | 104,545,800 |
| 2024/2/16 | 202.06 | 203.17 | 197.40 | 199.95 | 111,173,600 |
| 2024/2/15 | 189.16 | 200.88 | 188.86 | 200.45 | 120,831,800 |
| 2024/2/14 | 185.30 | 188.89 | 183.35 | 188.71 | 81,203,000 |
| 2024/2/13 | 183.99 | 187.26 | 182.11 | 184.02 | 86,759,500 |
| 2024/2/12 | 192.11 | 194.73 | 187.28 | 188.13 | 95,498,600 |
| 2024/2/09 | 190.18 | 194.12 | 189.48 | 193.57 | 84,476,300 |

