
## CHAPTER 6 DEEP LEARNING WITH PYTORCH FOR CLASSIFICATION

### Model Building, Training, and Evaluation with PyTorch

In this subsection, we consolidate the code for predicting diabetes with PyTorch with and without K-fold cross validation.

### Diabetes Classification Without K-Fold Cross-Validation

```python
[In] import boto3
[In] import logging
[In] import numpy as np
[In] import torch
[In] import torch.nn as nn
[In] import torch.optim as optim
[In] from torch.utils.data import DataLoader, TensorDataset
[In] from sklearn.metrics import (
    accuracy_score,
    precision_score,
    recall_score,
    f1_score,
    confusion_matrix,
    roc_auc_score
)
[In] from pyspark.sql import SparkSession
[In] from pyspark.ml.feature import (
    VectorAssembler,
    StandardScaler
)
[In] from pyspark.sql.functions import col
```

```python
[In] class DataPreprocessor:
    """
    Preprocesses the diabetes dataset.
    """

    def __init__(self, spark, data_file_path):
        """
        Initializes the DataPreprocessor.

        Args:
            spark (pyspark.sql.SparkSession):
                The Spark session.
            data_file_path (str):
                The path to the data file.
        """
        self.spark = spark
        self.data_file_path = data_file_path

    def preprocess(self):
        """
        Performs data preprocessing.

        Returns:
            tuple:
                A tuple containing train and test
                DataFrames.
        """
        try:
            diabetes_df = self.spark.read.csv(
                self.data_file_path,
                header=True,
                inferSchema=True
            )
            diabetes_df = diabetes_df.filter(
                (col("Glucose") != 0)
                & (col("BloodPressure") != 0)
                & (col("BMI") != 0)
            )
            feature_cols = [
                "Pregnancies",
                "Glucose",
                "BloodPressure",
                "BMI",
                "DiabetesPedigreeFunction",
                "Age",
            ]
            assembler = VectorAssembler(
                inputCols=feature_cols,
                outputCol="features"
            )
            diabetes_df = assembler.transform(diabetes_df)
            scaler = StandardScaler(
                inputCol="features",
                outputCol="scaled_features"
            )
            scaler_model = scaler.fit(diabetes_df)
            diabetes_df = scaler_model.transform(diabetes_df)
            train_df, test_df = diabetes_df.randomSplit(
                [0.8, 0.2],
                seed=42
            )
            return train_df, test_df
        except Exception as e:
            logging.error(
                f"Error occurred during data "
                f"preprocessing: {str(e)}"
            )
            raise e
```

```python
[In] class DiabetesClassifierModel(nn.Module):
    """
    Neural network model for diabetes classification.
    """

    def __init__(self, input_size, output_size):
        """
        Initializes the DiabetesClassifierModel.

        Args:
            input_size (int): The input size.
            output_size (int): The output size.
        """
        super(DiabetesClassifierModel, self).__init__()
        self.model = nn.Sequential(
            nn.Linear(input_size, 64),
            nn.ReLU(),
            nn.Linear(64, 32),
            nn.ReLU(),
            nn.Linear(32, 16),
            nn.ReLU(),
            nn.Linear(16, output_size),
        )

    def forward(self, x):
        """
        Defines the forward pass of the model.
        """
        return self.model(x)
```

```python
[In] def count_zeros(self):
    """
    Counts the number of zero values for each column in
    the dataset and displays the counts.
    """
    if self.data is not None:
        zero_counts = self.data.select([
            pyspark_sum((col(c) == 0).cast("int")).alias(c)
            for c in self.data.columns
        ])
        print("Zero Counts:")
        zero_counts.show()
    else:
        print("Data not loaded.")
```

```python
[In] def data_summary(self):
    """
    Displays a summary of the dataset, excluding certain
    columns, and filtering out rows with zero values in
    specific columns.
    """
    if self.data is not None:
        print("Data Summary (excluding 'Outcome',
              'SkinThickness', 'Insulin'):")
        columns_to_exclude = ['Outcome',
                              'SkinThickness',
                              'Insulin']
        summary_cols = [c for c in self.data.columns
                       if c not in columns_to_exclude]
        filtered_data = self.data.filter(
            (col("Glucose") != 0)
            & (col("BloodPressure") != 0)
            & (col("BMI") != 0)
        )
        filtered_data.select(summary_cols).describe().show()
    else:
        print("Data not loaded.")
```

```python
[In] def count_outcome(self):
    """
    Counts the occurrences of each outcome value in the dataset.
    """
    if self.data is not None:
        print("Outcome Counts:")
        outcome_counts = self.data.filter(
            (col("Glucose") != 0)
            & (col("BloodPressure") != 0)
            & (col("BMI") != 0)
        ).groupBy("Outcome").count()
        outcome_counts.show()
    else:
        print("Data not loaded.")
```

```python
[In] def explore_feature_distributions(self):
    """
    Plots histograms for the distribution of each feature in the dataset.
    """
    if self.data is not None:
        print("Feature Distributions:")
        for column in self.data.columns:
            if column not in ['SkinThickness', 'Insulin']:
                print(f"Feature: {column}")
                if column in ["Glucose",
                               "BloodPressure",
                               "BMI"]:
                    filtered_data = self.data.filter(
                        (col(column) != 0)
                        & (col("Glucose") != 0)
                        & (col("BloodPressure") != 0)
                        & (col("BMI") != 0)
                    )
                else:
                    filtered_data = self.data
                plot_data = filtered_data.select(column).toPandas()
                plot_data.plot(kind='hist', title=column)
        else:
            print("Data not loaded.")
```

```python
[In] def calculate_feature_target_correlation(self):
    """
    Calculates the correlation between each
    feature and the
    target variable ('Outcome').
    """
    if self.data is not None:
        print("Feature-Target Correlation "
              "(excluding 'SkinThickness', 'Insulin'):")
        for column in self.data.columns:
            if column not in ['Outcome',
                              'SkinThickness',
                              'Insulin']:
                correlation = self.data.filter(
                    (col(column) != 0)
                    & (col("Glucose") != 0)
                    & (col("BloodPressure") != 0)
                    & (col("BMI") != 0)
                ).stat.corr(column, 'Outcome')
                print(f"{column}: {correlation}")
        else:
            print("Data not loaded.")
```

```python
[In] def copy_file_from_s3(bucket_name, file_key, local_path):
    """
    Copies a file from an AWS S3 bucket to a local path.

    Args:
        bucket_name (str): The name of the S3 bucket.
        file_key (str): The key of the file in the S3 bucket.
        local_path (str):
            The local path where the file will be copied.
    """
    try:
        s3 = boto3.client('s3')
        s3.download_file(bucket_name, file_key, local_path)
        print(f"File {file_key} downloaded to {local_path}")
    except Exception as e:
        print(f"An error occurred while downloading file",
              f"{file_key}:", str(e))
```

```python
[In] if __name__ == "__main__":
    spark = (SparkSession.builder
             .appName("PimaDatasetExplorer")
             .getOrCreate())
    local_file_path = "/home/ubuntu/airflow/dags/diabetes.csv"
    s3_bucket_name = "instance1bucket"
    s3_file_key = "diabetes.csv"
    copy_file_from_s3(
        s3_bucket_name,
        s3_file_key,
        local_file_path
    )
    
    explorer = PimaDatasetExplorer(local_file_path)
    explorer.preprocess_data()
    explorer.handle_missing_values()
    explorer.count_zeros()
    explorer.data_summary()
    explorer.count_outcome()
    explorer.explore_feature_distributions()
    explorer.calculate_feature_target_correlation()
```
