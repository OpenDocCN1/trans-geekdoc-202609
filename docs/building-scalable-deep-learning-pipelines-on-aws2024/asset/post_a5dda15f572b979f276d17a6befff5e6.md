
This condition evaluates to True if the script is being run directly and False if it is being imported as a module. This is a common best practice in Python programming, as it allows the script to be used both as a standalone program and as a reusable module.

- `copy_and_print_data()`: This line calls the function `copy_and_print_data()` if the script is run directly. In other words, when the Python interpreter executes this script directly, it will invoke the `copy_and_print_data()` function.

We save the script as “spark_data_processing.py” in the “/home/ubuntu/airflow/dags” directory. To execute it, we have the option of navigating to this directory using the following command in the JupyterLab interface terminal or executing the script directly on the EC2 command-line interface:

```
[In]: cd /home/ubuntu/airflow/dags
```

Next, we activate the virtual environment “myenv” with the command

```
[In]: source myenv/bin/activate
```

Finally, with the virtual environment activated, we run the script using the command

```
[In]: python3 spark_data_processing.py
```

This initiates the execution of the script, which involves copying the Tesla stock CSV file from the S3 bucket to the local directory and printing the first five observations of the DataFrame.

After running the code, we obtain the following output:

```
[Out]: First 5 observations of the DataFrame:
```

| Date | Open | High | Low | Close | Volume |
|:---|:---|:---|:---|:---|:---|
| 2/23/24 | 195.31 | 197.57 | 191.50 | 191.97 | 78670300 |
| 2/22/24 | 194.00 | 198.32 | 191.36 | 197.41 | 92739500 |
| 2/21/24 | 193.36 | 199.44 | 191.95 | 194.77 | 103844000 |
| 2/20/24 | 196.13 | 198.60 | 189.13 | 193.76 | 104545800 |
| 2/16/24 | 202.06 | 203.17 | 197.40 | 199.95 | 111173600 |

The daily dataset ranges from February 26, 2019, to February 23, 2024 (1,258 observations). The output displays the first five observations from this historical dataset. Each trading day captures real-time fluctuations in the Tesla stock price. These observations highlight key indicators—Open, High, Low, Close, and Volume—illustrating price movements over a specific timeframe. Their definitions are as follows:

- **Open**: The opening price of Tesla stock on the given date
- **High**: The highest price of Tesla stock reached during the trading session on the given date
- **Low**: The lowest price of Tesla stock reached during the trading session on the given date
- **Close**: The closing price of Tesla stock on the given date
- **Volume**: The trading volume, representing the total number of shares traded on the given date

## Predicting Tesla Stock Price with PyTorch

In this section, we utilize the dataset explored in the previous section to implement a deep learning algorithm for predicting Tesla’s stock prices. In this dataset, the features of the model consist of Open, High, Low, and Volume, while the target variable is the Close price. The opening price of the stock can provide valuable information about market sentiment at the beginning of a trading day, reflecting investors’ initial reactions to news, events, or overnight developments. Similarly, trading volume is important because high trading volumes often indicate increased investor interest and can signal potential price movements. Volume can also be used as a proxy for liquidity, which is essential for accurate price discovery. As for the highest and lowest prices reached during a trading session, they provide insights into price volatility and trading range. High prices indicate the highest level of buying interest, while low prices represent the lowest level of selling interest. Analyzing the range between high and low prices can help identify trends, support, and resistance levels.

By incorporating these features into our predictive model, we can capture both fundamental market dynamics (such as opening sentiment and trading activity) and technical aspects (such as price volatility and trading range), which are essential for predicting stock prices accurately. However, it’s worth noting that the purpose of our model is illustration rather than providing a complete account. While these features are valuable, incorporating additional features such as technical indicators, fundamental data, or market sentiment could further enhance the predictive power of our model. This, however, is outside the scope of this chapter.

We leverage the capabilities of PySpark for data processing and PyTorch for building, training, and evaluating the neural network model. The Python code is designed to handle an end-to-end workflow, from data loading and preprocessing to model training, evaluation, and prediction. In Chapter 8, we will demonstrate how to deploy this code using Apache Airflow.

The entire modeling process consists of the following ten steps:

- Step 1: Imports
- Step 2: Logging Setup
- Step 3: Data Loading
- Step 4: Data Preprocessing
- Step 5: DataLoader Creation
- Step 6: Model Training
- Step 7: Model Evaluation
- Step 8: Main
- Step 9: Helper
- Step 10: Execution

Let's dive deep into the code step by step:

### Step 1: Imports

In this initial step, we introduce the libraries and modules imported in the code. These imports enable data processing, modeling, and logging:

```
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
```

Here’s a breakdown of the imports and their significance:

- **logging**: This library is utilized for generating log messages during the execution of the code. It enables tracking the program’s progress, debugging issues, and monitoring activities. In our code, logging will be used to log informational and error messages during various stages such as data loading, preprocessing, model training, and evaluation.
- **subprocess**: This module enables the code to execute system commands and interact with other programs. It’s used in our code for copying data from an AWS S3 bucket to a local directory on EC2 before data processing.
- **typing**: This module allows specifying the expected types of function arguments and return values. It will be employed in our code in function annotations for specifying argument and return types.
- **numpy**: This is a fundamental package for scientific computing with Python. It provides support for large, multidimensional arrays and matrices, along with a collection of mathematical functions to operate on these arrays. In our code, NumPy is used for converting Spark DataFrame columns to NumPy arrays.
- **torch, torch.nn, torch.optim**: These are components of PyTorch, a machine learning library primarily used for deep learning applications. They are used in our code for defining and training the neural network model.
- **DataLoader, TensorDataset**: These are classes from PyTorch’s torch.utils.data module. DataLoader is used to load datasets in batches during training and inference, while TensorDataset is a dataset wrapper that allows convenient access to tensors. They are used in the code for creating data loaders for training and testing the neural network model.
- **pyspark.sql, pyspark.ml.feature, DataFrame**: These are components of PySpark and will be used in our code for loading, preprocessing, and manipulating structured data in Spark DataFrames before converting them into PyTorch tensors for training the neural network model. Specifically, pyspark.sql is used for Spark DataFrame operations and pyspark.ml.feature for data preprocessing tasks such as feature assembling and scaling, and DataFrame represents the DataFrame class used in PySpark for data manipulation and analysis.

### Step 2: Logging Setup

In this step, we configure the logging system to ensure effective monitoring of the code's execution and to facilitate debugging and tracking of program progress:

```
[In]: logging.basicConfig(level=logging.INFO)
[In]: logger = logging.getLogger(__name__)
```

Here is what the two lines mean:

- **logging.basicConfig(level=logging.INFO)**: This line configures the logging system to display log messages with the INFO level or higher. It ensures that log messages of sufficient importance are shown during the execution of the code.
