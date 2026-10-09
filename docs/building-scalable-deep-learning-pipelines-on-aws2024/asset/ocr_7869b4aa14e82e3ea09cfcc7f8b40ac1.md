```
    dtype=torch.float32
    )
    return features, labels
```

The `spark_df_to_tensor` function takes a DataFrame as input and returns a tuple containing features and labels as PyTorch tensors. Inside the function, it uses NumPy and PyTorch to perform the necessary conversions. This function is crucial for preprocessing data before training and evaluating the deep learning regression model.

# Module 5: main.py

We now come to the main module, which orchestrates the entire workflow—data preprocessing, model training, model evaluation, and utility function:

```
[In]: import logging
[In]: import torch
[In]: import torch.optim as optim
[In]: import torch.nn as nn
[In]: from torch.utils.data import DataLoader
[In]: from typing import Tuple
[In]: from pyspark.sql import DataFrame
[In]: from data_processing import load_data, preprocess_data
[In]: from model_training import create_data_loader,
    train_model
[In]: from model_evaluation import evaluate_model
[In]: import utils

[In]: logging.basicConfig(level=logging.INFO)
[In]: logger = logging.getLogger(__name__)

[In]: def main(
    data_file_path: str,
    num_epochs: int = 100,
```