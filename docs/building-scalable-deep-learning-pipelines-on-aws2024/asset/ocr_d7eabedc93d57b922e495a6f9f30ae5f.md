# Data Preparation with PySpark for PyTorch

In this subsection, we combine the individual code snippets we have used to prepare the Tesla stock dataset for a PyTorch deep learning model:

```
"[In]: import logging
[In]: from pyspark.sql import SparkSession
[In]: from pyspark.ml.feature import VectorAssembler,
     StandardScaler
[In]: from pyspark.sql import DataFrame
[In]: import numpy as np
[In]: import torch
[In]: from torch.utils.data import DataLoader, TensorDataset
[In]: import boto3
[In]: logging.basicConfig(level=logging.INFO)
[In]: logger = logging.getLogger(__name__)"
```

```
"[In]: def load_data(file_path: str) -> DataFrame:
    '''
    Load stock price data from a CSV file using
    SparkSession.
    '''
    spark = (SparkSession.builder
             .appName("StockPricePrediction")
             .getOrCreate())
    df = spark.read.csv(
            file_path,
            header=True,
            inferSchema=True
            )
    return df"
```