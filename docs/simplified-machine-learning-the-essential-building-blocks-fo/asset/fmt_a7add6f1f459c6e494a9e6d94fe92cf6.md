
In this example, we have two sample datasets, `data_source1` and `data_source2`, each with an ID and Name column. We create two separate DataFrames, `df1` and `df2`, to represent data from these two different sources. We use the `pd.concat()` function from pandas to concatenate the DataFrames vertically, effectively integrating the data. The `ignore_index=True` argument is used to reindex the resulting DataFrame.

## Aggregation

Another important feature is data aggregation. It combines multiple data points into summary statistics. For example, you can aggregate daily sales data into monthly or yearly totals.

Data aggregation involves combining multiple data points into summary statistics or aggregating data at a higher level of granularity. Python provides tools like the pandas library to perform data aggregation. [Code 2.12](#ch02.xhtml#cd2-12) is demonstrating data aggregation using pandas:

**Code 2.12: Python code for aggregation**

```python
import pandas as pd

# Sample data
data = {'Date': ['2021-01-01', '2021-01-01', '2021-01-02', '2021-01-02'],
        'Sales': [1000, 1200, 800, 900]}
df = pd.DataFrame(data)

# Display the original DataFrame
print("Original DataFrame:")
print(df)

# Data aggregation: Sum of sales by date
aggregated_df = df.groupby('Date')['Sales'].sum().reset_index()

# Display the aggregated DataFrame
print("\nAggregatedDataFrame (Sum of Sales by Date):")
print(aggregated_df)
```

The following is the output of [Code 2.12](#ch02.xhtml#cd2-12):

![](images/2.12.png)

Figure 2.12: Output of code 2.12

In this code, we start with a sample DataFrame (`df`) containing two columns, Date and Sales. We use the `groupby()` method in pandas to group the data by the Date column. We apply an aggregation function (`sum()`) to the sales column within each group to calculate the sum of sales for each date. We use `reset_index()` to reset the index of the resulting DataFrame, creating a new DataFrame (`aggregated_df`) that contains the aggregated data. The resulting `aggregated_df` contains the sum of sales for each unique date in the original dataset.

> **Note:** You can perform various types of aggregation functions (for example, mean, median, count, max, min) depending on your specific analysis or reporting requirements. Adjust the code based on your dataset and the type of aggregation you need to perform.

## Data splitting

Divide the dataset into training, validation, and test sets for Machine Learning purposes.

Data splitting is a crucial step when preparing data for Machine Learning. It involves dividing your dataset into training, validation, and test sets. [Code 2.13](#ch02.xhtml#cd2-13) is a Python code example using the `sklearn.model_selection` module to split a dataset:

**Code 2.13: Python code for data splitting**

```python
import numpy as np
from sklearn.model_selection import train_test_split

# Sample dataset (features and labels)
X = np.random.rand(100, 2) # 100 samples with 2 features
y = np.random.randint(0, 2, 100) # Binary labels (0 or 1)

# Split the data into training, validation, and test sets
X_train, X_temp, y_train, y_temp = train_test_split(X, y, test_size=0.4, random_state=42)
X_valid, X_test, y_valid, y_test = train_test_split(X_temp, y_temp, test_size=0.5, random_state=42)

# Display the sizes of the resulting sets
print("Training set size:", X_train.shape[0])
print("Validation set size:", X_valid.shape[0])
print("Test set size:", X_test.shape[0])
```

The following is the output of [Code 2.13](#ch02.xhtml#cd2-13):

![](images/2.13.png)

Figure 2.13: Output of code 2.13

In this code, we create a synthetic dataset with features (`X`) and binary labels (`y`) as an example. We use `train_test_split` from the `sklearn.model_selection` module to split the data into three sets: training, validation, and test. The `test_size` parameter specifies the size of the validation and test sets, and the `random_state` parameter ensures reproducibility. The resulting sets, `X_train`, `X_valid`, `X_test`, `y_train`, `y_valid`, and `y_test`, contain the feature and label subsets for training, validation, and testing, respectively.

You can adjust the `test_size` parameter to control the ratio of data allocated to the validation and test sets. Make sure to customize the code according to your specific dataset and Machine Learning task.

## Normalization

Normalization means scaling numerical features to the same range to prevent certain features from dominating others. Normalization scales data features to a consistent range, typically between 0 and 1. It is useful when features have different units or magnitudes. Min-max scaling and z-score normalization are common methods. [Code 2.14](#ch02.xhtml#cd2-14) is a Python code example using the `sklearn.preprocessing` module to normalize data between 0 and 1:

**Code 2.14: Python code for data normalization**

```python
import numpy as np
from sklearn.preprocessing import MinMaxScaler

# Sample data
data = np.array([[10, 20],
                 [15, 30],
                 [5, 10],
                 [25, 40]])

# Create a MinMaxScaler instance
scaler = MinMaxScaler()

# Fit the scaler to the data and transform the data
normalized_data = scaler.fit_transform(data)

# Display the normalized data
print("Normalized Data:")
print(normalized_data)
```

The following is the output of [Code 2.14](#ch02.xhtml#cd2-14):

![](images/2.14.png)

Figure 2.14: Output of code 2.14

In this code, we start with sample data in a NumPy array (`data`) with two features. We create an instance of the `MinMaxScaler` from the `sklearn.preprocessing` module. We fit the scaler to the data using `fit_transform`, which scales the data between zero and one based on the minimum and maximum values in each feature. The resulting `normalized_data` contains the data after normalization, where each feature has values between zero and one.

This code demonstrates how to normalize data using min-max scaling. It is a simple yet effective technique to ensure that your features are on the same scale and do not dominate each other when training Machine Learning models.

## Standardization

Standardization (z-score scaling) transforms data so that it has a mean of 0 and a standard deviation of one. It is beneficial when you want to center the data and give it a consistent spread.

Standardization, often referred to as z-score scaling, is a technique used to transform data so that it has a mean of 0 and a standard deviation of one. This makes the data have a standardized distribution with properties suitable for certain Machine Learning algorithms. [Code 2.15](#ch02.xhtml#cd2-15) is an example using the `sklearn.preprocessing` module to standardize data:

**Code 2.15: Python code for data standardization**

```python
import numpy as np
from sklearn.preprocessing import StandardScaler

# Sample data
data = np.array([[10, 20],
                 [15, 30],
                 [5, 10],
                 [25, 40]])

# Create a StandardScaler instance
scaler = StandardScaler()

# Fit the scaler to the data and transform the data
standardized_data = scaler.fit_transform(data)

# Display the standardized data
print("Standardized Data:")
print(standardized_data)
```

The following is the output of [Code 2.15](#ch02.xhtml#cd2-15):

![](images/2.15.png)

Figure 2.15: Output of code 2.15
