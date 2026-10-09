# Model Building, Training, and Evaluation with PyTorch

In this subsection, we consolidate the code for predicting diabetes with PyTorch with and without K-fold cross validation.

# Diabetes Classification Without K-Fold Cross-Validation

```
[In]: import boto3
[In]: import logging
[In]: import numpy as np
[In]: import torch
[In]: import torch.nn as nn
[In]: import torch.optim as optim
[In]: from torch.utils.data import DataLoader, TensorDataset
[In]: from sklearn.metrics import (
        accuracy_score,
        precision_score,
        recall_score,
        f1_score,
        confusion_matrix,
        roc_auc_score
    )
[In]: from pyspark.sql import SparkSession
[In]: from pyspark.ml.feature import (
        VectorAssembler,
        StandardScaler
    )
[In]: from pyspark.sql.functions import col
[In]: class DataPreprocessor:
```