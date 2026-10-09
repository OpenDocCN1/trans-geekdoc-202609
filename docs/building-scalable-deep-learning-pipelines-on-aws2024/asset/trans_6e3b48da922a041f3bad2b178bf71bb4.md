

从表格开始，我们添加了一列“% 变化”，尽管该列并非由代码生成，但旨在直观展示实际值与预测值之间的差异：

| 日期 | 实际值 | 预测值 | % 变化 |
| --- | --- | --- | --- |
| 2/23/24 | 192 | 196 | 2% |
| 2/22/24 | 197 | 196 | -1% |
| 2/21/24 | 195 | 197 | 1% |
| 2/20/24 | 194 | 196 | 1% |
| 2/16/24 | 200 | 202 | 1% |
| 2/15/24 | 200 | 196 | -2% |
| 2/14/24 | 189 | 187 | -1% |
| 2/13/24 | 184 | 186 | 1% |
| 2/12/24 | 188 | 192 | 2% |
| 2/09/24 | 194 | 193 | -1% |

数据表明，预测值与实际值之间的最大差异为 abs(2%)，这表明两者高度吻合。

转到图表，图 4-1 展示了所有特斯拉股价（1,258 个观测值）的实际值和预测值。两条线的接近程度证实了模型的强大性能。

![](img/1c89d4486f90c87568fa6a42d46ae02a_271_0.png)

*图 4-1.* *特斯拉股价的实际值与预测值*

# 整合所有内容

在本节中，我们将本章中检查的代码各个组件进行整合，以构建一个全面的代码库。这部分包含三个子部分：探索特斯拉股票数据集、使用 PySpark 和 PyTorch 预测特斯拉股价，以及并排绘制实际值和预测值。

## 探索特斯拉股票数据集

下面的脚本将 TSLA（特斯拉）股价 CSV 文件从 S3 存储桶复制到本地目录 “/home/ubuntu/airflow/dags/”，将数据加载到 Spark DataFrame 中，然后打印该 DataFrame 的前五个观测值：

```python
[In]: import subprocess
[In]: from pyspark.sql import SparkSession
[In]: import logging

[In]: def load_data(file_path: str):
    """
    Load stock price data from a CSV file using
    SparkSession.
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

[In]: def copy_and_print_data():
    """
    Copy a CSV file from an S3 bucket to a local
    directory and
    print the first 5 observations.
    """
    s3_bucket_path = "s3://instance1bucket/TSLA_stock.csv"
    local_file_path = "/home/ubuntu/airflow/dags/TSLA_stock.csv"
    logging.basicConfig(level=logging.INFO)
    logger = logging.getLogger(__name__)

    try:
        subprocess.run(
            [
                "aws", "s3", "cp",
                s3_bucket_path,
                local_file_path
            ],
            check=True
        )
        df = load_data(local_file_path)
        print("First 5 observations of the DataFrame:")
        df.show(5)

    except FileNotFoundError:
        logger.error(f"Data file not found at {s3_bucket_path}")
    except subprocess.CalledProcessError as e:
        logger.error(f"Error copying data from S3: {e}")

[In]: if __name__ == "__main__":
    copy_and_print_data()
```

## 使用 PySpark 和 PyTorch 预测特斯拉股价

下面的脚本执行以下任务：

- 使用 SparkSession 从 CSV 文件加载股价数据
- 通过组装特征向量并对它们进行缩放来预处理数据
- 将预处理后的数据拆分为训练集和测试集
- 将数据转换为 PyTorch 张量，并加载到 DataLoader 对象中以进行批处理
- 定义、训练和评估用于预测特斯拉股价的深度模型
- 保存训练好的模型以备将来使用

```python
[In]: import logging
[In]: import subprocess
[In]: from typing import Tuple
[In]: import numpy as np
[In]: import torch
[In]: import torch.nn as nn
[In]: import torch.optim as optim
[In]: from torch.utils.data import DataLoader, TensorDataset
[In]: from pyspark.sql import SparkSession
[In]: from pyspark.ml.feature import VectorAssembler, StandardScaler
[In]: from pyspark.sql import DataFrame
[In]: logging.basicConfig(level=logging.INFO)
[In]: logger = logging.getLogger(__name__)

[In]: def load_data(file_path: str) -> DataFrame:
    """
    Load stock price data from a CSV file using
    SparkSession.
    """
    try:
        spark = (SparkSession.builder
                 .appName("StockPricePrediction")
                 .getOrCreate())
        df = spark.read.csv(
                    file_path,
                    header=True,
                    inferSchema=True
                )
        return df
    except Exception as e:
        raise RuntimeError(
            f"Error loading data from {file_path}: {e}"
        )

[In]: def preprocess_data(df: DataFrame) -> DataFrame:
    """
    Preprocess the data by assembling feature
    vectors using
    VectorAssembler and scaling them using
    StandardScaler.
    """
    assembler = VectorAssembler(
        inputCols=['Open', 'High', 'Low', 'Volume'],
        outputCol='features'
    )
    df = assembler.transform(df)
    scaler = StandardScaler(
        inputCol="features",
        outputCol="scaled_features",
        withStd=True,
        withMean=True
    )
    scaler_model = scaler.fit(df)
    df = scaler_model.transform(df)
    df = df.select('scaled_features', 'Close')
    return df

[In]: def create_data_loader(
    features,
    labels,
    batch_size=32,
    num_workers=4) -> DataLoader:
    """
    Convert the preprocessed data into PyTorch tensors and create DataLoader objects for both the training and test sets.

    Args:
        features (Tensor): The input features.
        labels (Tensor): The corresponding labels.
        batch_size (int):
            The number of samples per batch to load.
            Defaults to 32.
        num_workers (int):
            The number of subprocesses to use for data
            loading.
            Defaults to 4.

    Returns:
        DataLoader: A PyTorch DataLoader for the dataset.
    """
    dataset = TensorDataset(features, labels)
    return DataLoader(
        dataset,
        batch_size=batch_size,
        shuffle=True
    )

[In]: def train_model(
        model,
        train_loader,
        criterion,
        optimizer,
        num_epochs
    ):
        """
        Train the model on the training data using the
        DataLoader and the defined loss function and
        optimizer. Iterate over the data for a specified
        number of epochs, calculate the loss, and update the
        model parameters.
        """
        for epoch in range(num_epochs):
            for inputs, labels in train_loader:
                optimizer.zero_grad()
                outputs = model(inputs)
                loss = criterion(outputs, labels.unsqueeze(1))
                loss.backward()
                optimizer.step()
            logger.info(
                f"Epoch [{epoch + 1}/{num_epochs}],"
                f"Loss: {loss.item():.4f}"
            )

[In]: def evaluate_model(
            model,
            test_loader,
            criterion
    ) -> Tuple[float, float]:
        """
        Evaluate the trained model on the test data to assess
        its performance.
        Calculate the test loss and additional evaluation
        metrics such as the R-squared score.
        """
        with torch.no_grad():
            model.eval()
            predictions = []
            targets = []
            test_loss = 0.0
            for inputs, labels in test_loader:
                outputs = model(inputs)
                loss = criterion(outputs, labels.unsqueeze(1))
                test_loss += loss.item() * inputs.size(0)
                predictions.extend(outputs.squeeze().tolist())
            targets.extend(labels.tolist())

            test_loss /= len(test_loader.dataset)
            predictions = torch.tensor(predictions)
            targets = torch.tensor(targets)
            ss_res = torch.sum((targets - predictions) ** 2)
            ss_tot = torch.sum((targets - torch.mean(targets)) ** 2)
            r_squared = 1 - ss_res / ss_tot
            logger.info(f"Test Loss: {test_loss:.4f}")
            logger.info(f"R-squared Score: {r_squared:.4f}")
            return test_loss, r_squared.item()

[In]: def main(
        data_file_path: str,
        num_epochs: int = 100,
        batch_size: int = 32,
        learning_rate: float = 0.001
    ):
        """
        Main function for training and evaluating a deep
        learning model for Tesla stock price prediction.

        Args:
            data_file_path (str): The path to the CSV file
            containing stock price data.
            num_epochs (int): The number of epochs for
            training the model. Defaults to 100.
            batch_size (int): The batch size for data loading
            during training. Defaults to 32.
            learning_rate (float): The learning rate for the
            optimizer. Defaults to 0.001.
        """
```

