

随后，我们定义 `convert_to_tensor` 函数，该函数负责将特征和标签转换为 PyTorch 张量：

```python
In]: def convert_to_tensor(features, labels):
    """
    Convert features and labels to PyTorch tensors.
    """
    tensor_features = torch.tensor(
        features,
        dtype=torch.float32
    )
    tensor_labels = torch.tensor(labels, dtype=torch.float32)
    return tensor_features, tensor_labels
```

- `features`：需要转换为 PyTorch 张量的特征数据。
- `labels`：需要转换为 PyTorch 张量的标签数据。
- `convert_to_tensor` 函数使用 PyTorch 库中的 `torch.tensor()` 函数将特征和标签转换为 PyTorch 张量。
- `dtype=torch.float32` 参数指定结果张量的数据类型应为 32 位浮点数。
- 转换后的张量分别赋值给变量 `tensor_features` 和 `tensor_labels`。
- 最后，该函数返回一个元组 `(tensor_features, tensor_labels)`，其中 `tensor_features` 是包含转换后特征的 PyTorch 张量，`tensor_labels` 是包含转换后标签的 PyTorch 张量。

继续往下，我们定义 `create_data_loader` 函数，该函数负责为数据的批量处理创建一个 PyTorch `DataLoader` 对象：

```python
In: def create_data_loader(features, labels, batch_size):
    """
    Create a Pytorch DataLoader for batch processing.
    """
    tensor_features, tensor_labels = convert_to_tensor(
        features,
        labels
    )
    dataset = TensorDataset(tensor_features, tensor_labels)
    data_loader = DataLoader(
        dataset,
        batch_size=batch_size,
        shuffle=True
    )
    return data_loader
```

`create_data_loader` 函数具有以下参数：

- `features`：要包含在 DataLoader 中的特征数据
- `labels`：要包含在 DataLoader 中的相应标签数据
- `batch_size`：处理数据的期望批次大小

就功能而言：

- 该函数首先调用 `convert_to_tensor()` 函数将特征和标签转换为 PyTorch 张量。
- 使用转换后的张量，它创建一个 PyTorch `TensorDataset`，这是一个将特征和标签一起保持的数据集包装器。
- `TensorDataset` 允许在训练期间对数据批次进行迭代。
- 最后，该函数创建一个 PyTorch `DataLoader` 对象，有助于从数据集中迭代数据批次。
- `batch_size` 参数指定每个批次中的样本数量，而 `shuffle=True` 参数确保在每个 epoch 之前对数据进行打乱，以防止模型学习序列模式。

`create_data_loader` 函数返回一个 PyTorch `DataLoader` 对象，可用于训练或验证过程。此函数对于在深度学习模型训练期间高效处理大型数据集至关重要。它支持批量处理，有助于加快训练过程并优化内存使用。

在下一步中，我们定义 `copy_file_from_s3` 函数，该函数负责将文件从 Amazon S3 存储桶复制到本地文件路径：

```python
In]: def copy_file_from_s3(
             bucket_name: str,
             file_key: str,
             local_file_path: str
             ):
             """
Copy file from S3 bucket to local file path.
"""
s3 = boto3.client('s3')
s3.download_file(bucket_name, file_key, local_file_path)
logger.info(
    f"File downloaded from S3 bucket {bucket_name}"
    f"to local file path: {local_file_path}"
)
```

以下是对该函数参数和功能的解释：

参数：

- `bucket_name`：要从中复制文件的 S3 存储桶名称
- `file_key`：文件在 S3 存储桶内的键（或路径）
- `local_file_path`：复制文件保存到的本地文件路径

功能：

- 该函数首先使用 `boto3` 库创建与 Amazon S3 服务的连接。
- 然后，它使用 S3 客户端的 `download_file` 方法，从给定的 S3 存储桶（`bucket_name`）和文件键（`file_key`）下载指定文件到指定的本地文件路径（`local_file_path`）。
- 文件成功下载后，它使用 `logger` 对象记录一条信息消息，指示文件已从 S3 存储桶下载到本地文件路径。

该函数没有显式返回任何值，但它执行了上述描述的文件复制操作。此函数用于检索存储在 Amazon S3 存储桶中的文件，并将其引入本地环境以进行进一步处理或分析。它可以用于各种场景，例如下载机器学习任务的数据集、获取配置文件或在不同的存储系统之间传输数据。

继续数据准备流程，我们定义主函数，该函数作为脚本或应用程序的入口点：

```python
[In]: def main():
        s3_bucket_name = 'instance1bucket'
        s3_file_key = 'TSLA_stock.csv'
        local_file_path = '/home/ubuntu/airflow/dags/TSLA_stock.csv'
        copy_file_from_s3(
        s3_bucket_name,
        s3_file_key,
        local_file_path
        )
        df = load_data(local_file_path)
        print_first_5_observations(df, "First 5 observations:")
        df = preprocess_data(df)
        print_first_5_observations(
        df,
        "First 5 observations after scaling:"
        )
        df_features = np.array(
        df.select('scaled_features')
        .rdd.map(lambda x: x.scaled_features.toArray())
        .collect()
)
df_labels = np.array(
    df.select('Close')
    .rdd.map(lambda x: x.Close)
    .collect()
)

batch_size = 32
train_loader = create_data_loader(
    df_features,
    df_labels,
    batch_size
)

logger.info(
    "First 5 observations after scaling"
    "and converting to tensors:"
)
print(train_loader.dataset[:5])
```

这个主函数协调整个数据准备过程，从将数据文件从 S3 存储桶复制到本地存储，到预处理数据，将其转换为适合模型训练的格式，最后创建一个用于高效批量处理的 `DataLoader`。让我们逐一检查这些步骤：

### 从 S3 存储桶复制文件

- 该函数指定了 S3 存储桶的名称（`s3_bucket_name`）、桶内文件的键（`s3_file_key`）以及文件将被复制到的本地文件路径（`local_file_path`）。
- 然后，它调用 `copy_file_from_s3` 函数将文件从指定的 S3 存储桶复制到本地文件路径。

### 加载数据

- 该函数使用 `load_data` 函数从本地文件路径（`local_file_path`）加载数据，并将其赋值给 DataFrame 变量 `df`。

### 打印前五个观察值

- 该函数使用 `print_first_5_observations` 函数和自定义标题“First 5 observations:”打印 DataFrame（`df`）的前五个观察值。

### 预处理数据

- 该函数通过调用 `preprocess_data` 函数对加载的数据进行预处理，并将预处理后的 DataFrame 重新赋值给 `df`。
- 预处理后，它再次使用自定义标题“First 5 observations after scaling:”打印 DataFrame 的前五个观察值。

### 将数据转换为 NumPy 数组

- 该函数将包含缩放特征和‘Close’值的 Spark DataFrame 列转换为 NumPy 数组（分别为 `df_features` 和 `df_labels`）。
- 这些数组将用作训练模型的输入特征和标签。

### 创建 DataLoader

- 该函数使用 `create_data_loader` 函数创建一个用于批量处理的 PyTorch `DataLoader`（`train_loader`）。此 `DataLoader` 将在模型训练期间用于迭代训练数据批次。

### 打印作为张量的前五个观察值

- 该函数记录一条信息消息，指示将打印缩放并转换为张量后的前五个观察值。
- 然后，它打印 `DataLoader` 数据集的前五个观察值。

在数据准备的最终过程中，我们有一个条件语句，用于检查脚本是作为主程序运行还是作为模块导入到另一个脚本中：

```python
[In]: if __name__ == "__main__":
    main()
```

如果脚本被直接执行（即作为主程序），条件 `__name__ == "__main__"` 求值为 `True`，并且 `if` 语句内部的代码块被执行。如果脚本作为模块导入到另一个脚本中，条件 `__name__ == "__main__"` 求值为 `False`，并且 `if` 语句内部的代码块不被执行。在此上下文中，当脚本直接运行时，会调用 `main()`，这意味着主函数将被执行，从而启动数据准备过程。这种结构允许脚本既可以直接运行，也可以作为模块导入到其他脚本中，而不会导致非预期的副作用。

