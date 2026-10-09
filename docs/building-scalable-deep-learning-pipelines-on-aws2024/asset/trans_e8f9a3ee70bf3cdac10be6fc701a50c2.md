
## PySpark 中的并行处理

在本小节中，我们展示了用于演示在 PySpark 中加速处理大型数据集的各种技术的代码：

```python
import boto3
from pyspark.sql import SparkSession
from pyspark.sql.functions import broadcast

class DataProcessor:
    def __init__(self, spark_session):
        self.spark = spark_session

    def load_data(self, file_path: str):
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

    def print_first_n_rows(self, df, n=10):
        print(f"First {n} rows of the DataFrame:")
        df.show(n)

    def print_partition_info(self, df):
        num_partitions = df.rdd.getNumPartitions()
        print(f"Number of partitions: {num_partitions}")

def copy_file_from_s3(
        bucket_name: str,
        file_key: str,
        local_file_path: str
    ):
    try:
        s3 = boto3.client('s3')
        s3.download_file(bucket_name, file_key, local_file_path)
        print(f"File downloaded from S3 bucket\n      {bucket_name} "
              f"to local file path: {local_file_path}")
    except Exception as e:
        print(f"Error copying file from S3: {str(e)}")

def main(
    s3_bucket_name: str,
    s3_file_key: str,
    local_file_path: str
):
    spark = SparkSession.builder \
        .appName("StockPriceOptimization") \
        .config("spark.sql.adaptive.enabled", "true") \
        .config("spark.sql.shuffle.partitions", "20") \
        .getOrCreate()
    copy_file_from_s3(
        s3_bucket_name,
        s3_file_key,
        local_file_path
    )
    data_processor = DataProcessor(spark)
    df = data_processor.load_data(local_file_path)
    if df is not None:
        data_processor.print_partition_info(df)
        # Repartition the DataFrame
        repartitioned_df = df.repartition(10)
        data_processor.print_partition_info(repartitioned_df)
        # Coalesce partitions
        coalesced_df = repartitioned_df.coalesce(5)
        data_processor.print_partition_info(coalesced_df)

        # Example broadcast join
        small_df = spark.createDataFrame([
            ("2023-08-25", 5.5),
            ("2023-08-26", 6.0),
        ], ["Date", "AdditionalData"])
        joined_df = repartitioned_df.join(
            broadcast(small_df), on="Date", how="left")

        # Save as Parquet
        repartitioned_df.write.parquet(
            "/home/ubuntu/airflow/dags/tesla_stock.parquet"
        )

        # Print the first few rows
        data_processor.print_first_n_rows(repartitioned_df)
    else:
        print("Error loading data. Exiting.")

if __name__ == "__main__":
    s3_bucket_name = 'instance1bucket'
    s3_file_key = 'TSLA_stock.csv'
    local_file_path = '/home/ubuntu/airflow/dags/TSLA_stock.csv'
    main(s3_bucket_name, s3_file_key, local_file_path)
```

### 使用 PySpark 为 PyTorch 进行数据准备

在本小节中，我们将之前用于为 PyTorch 深度学习模型准备特斯拉股票数据集的各个独立代码片段组合在一起：

```python
import logging
from pyspark.sql import SparkSession
from pyspark.ml.feature import VectorAssembler, StandardScaler
from pyspark.sql import DataFrame
import numpy as np
import torch
from torch.utils.data import DataLoader, TensorDataset
import boto3

logging.basicConfig(level=logging.INFO)
logger = logging.getLogger(__name__)

def load_data(file_path: str) -> DataFrame:
    '''
    Load stock price data from a CSV file using SparkSession.
    '''
    spark = (SparkSession.builder
             .appName("StockPricePrediction")
             .getOrCreate())
    df = spark.read.csv(
        file_path,
        header=True,
        inferSchema=True
    )
    return df

def preprocess_data(df: DataFrame) -> DataFrame:
    """
    Preprocess the data by assembling feature vectors using VectorAssembler, 
    scaling them using StandardScaler, and performing feature engineering.
    """
    assembler = VectorAssembler(
        inputCols=['Open', 'High', 'Low', 'Volume'],
        outputCol='features'
    )
    df = assembler.transform(df)
    logger.info("First 5 observations after assembling features:")
    df.show(5, truncate=False)
    
    df = perform_feature_engineering(df)
    logger.info("First 5 observations after feature engineering:")
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

def perform_feature_engineering(df: DataFrame) -> DataFrame:
    """
    Perform feature engineering operations to enhance the data's predictive power.

    This function adds new columns to the DataFrame `df` to capture relevant 
    information from existing features, including:

    - Price Range Interaction: Represents the difference between High and Low prices.
    - Price Change Interaction: Represents the difference between Close and Open prices.
    - Volume-Price Interaction: Represents the product of Volume and Close prices.

    Parameters:
    df (DataFrame): The input DataFrame containing the raw data.

    Returns:
    DataFrame: The DataFrame `df` with additional engineered features.
    """
    df = df.withColumn('price_range', df['High'] - df['Low'])
    df = df.withColumn('price_change', df['Close'] - df['Open'])
    df = df.withColumn(
        'volume_price_interaction',
        df['Volume'] * df['Close']
    )
    return df

def print_first_5_observations(df: DataFrame, heading: str):
    """
    Print the first 5 observations of the DataFrame with a custom heading.
    """
    logger.info(heading)
    df.show(5, truncate=False)

def convert_to_tensor(features, labels):
    """
    Convert features and labels to PyTorch tensors.
    """
    tensor_features = torch.tensor(
        features,
        dtype=torch.float32
    )
    tensor_labels = torch.tensor(labels, dtype=torch.float32)
    return tensor_features, tensor_labels

def create_data_loader(features, labels, batch_size):
    """
    Create a PyTorch DataLoader for batch processing.
    """
    tensor_features, tensor_labels = convert_to_tensor(features, labels)
    dataset = TensorDataset(tensor_features, tensor_labels)
    data_loader = DataLoader(
        dataset,
        batch_size=batch_size,
        shuffle=True
    )
    return data_loader

def copy_file_from_s3(bucket_name: str, file_key: str, local_file_path: str):
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

