
# Pandas Data Structures

Pandas provides two primary data structures for data manipulation and analysis: `Series` and `DataFrame`. Both of these data structures are built on top of NumPy arrays, which enable efficient and high-performance operations. The following is a detailed explanation of `Series` and `DataFrame` and how they work.

## Series

A `Series` is a one-dimensional, labeled array capable of holding any data type, including integers, floats, strings, and Python objects. The basic structure of a `Series` consists of two components: data and index.

### Data

The data in a `Series` is a one-dimensional NumPy array that holds the actual data values. The data can be of various types, such as integers, floats, or strings.

### Index

The index is an array-like structure that labels each element in the data array. By default, the index is a zero-based integer sequence, but you can also provide custom labels for the index. This makes it easy to reference and manipulate data elements based on their labels.

To create a `Series`, you can use the `pd.Series()` constructor and pass in a list, dictionary, or NumPy array as data. You can also provide an optional `index` parameter to specify custom labels for the data elements.

## DataFrame

A `DataFrame` is a two-dimensional, size-mutable, and heterogeneous tabular data structure with labeled axes (rows and columns). It can be thought of as a collection of `Series` objects, where each column is a `Series`. `DataFrame`s are designed to handle a wide variety of data types, making them versatile and powerful tools for data manipulation and analysis.

The basic structure of a `DataFrame` consists of three components: data, index, and columns.

### Data

The data in a `DataFrame` is stored as a collection of one or more `Series` objects, where each column represents a separate `Series`. The data in each `Series` can be of various types, such as integers, floats, or strings.

### Index

The index is an array-like structure that labels each row in the `DataFrame`. Like the `Series` index, the `DataFrame` index can be a zero-based integer sequence or have custom labels.

### Columns

The columns are an array-like structure that labels each column in the `DataFrame`. Column labels are used to reference and manipulate specific columns in the `DataFrame`.

To create a `DataFrame`, you can use the `pd.DataFrame()` constructor and pass in a variety of data types, such as a dictionary, a list of dictionaries, a 2D NumPy array, or even a list of `Series`. You can also provide optional `index` and `columns` parameters to specify custom row and column labels.

Both `Series` and `DataFrame` provide a wide range of methods and functionality for data manipulation and analysis. These include:

*   **Data selection**: You can select specific rows, columns, or elements in a `DataFrame` or `Series` using indexing, slicing, and boolean conditions.
*   **Data cleaning**: You can handle missing data, drop unwanted rows or columns, and replace specific values in a `DataFrame` or `Series`.
*   **Data transformation**: You can apply functions to elements in a `DataFrame` or `Series`, create new columns, or reshape the data structure.
*   **Data aggregation and summarization**: You can perform various aggregation functions, like `sum`, `mean`, or `count`, on a `DataFrame` or `Series`. You can also use the `GroupBy` functionality to group data based on specific criteria and perform aggregation operations on each group.
*   **Sorting and ranking**: You can sort a `DataFrame` or `Series` based on index or column values, and rank data elements based on specific criteria.
*   **Time series functionality**: You can work with time series data, resample data at different frequencies, and perform rolling window calculations on a `DataFrame` or `Series`.

By understanding the structure and functionality of `Series` and `DataFrame`, you can effectively manipulate and analyze data in Pandas, allowing you to tackle a wide range of data-related tasks.

# Load and Modify Dataset

To access and modify the data from the provided CSV file, follow these step-by-step instructions:

## Download CSV File

First, download the `Customer_Churn_Modelling.csv` file from the GitHub repository to your local machine. You can do this by visiting the following URL in your web browser:

[https://raw.githubusercontent.com/kittenpub/database-repository/main/Customer_Churn_Modelling.csv](https://raw.githubusercontent.com/kittenpub/database-repository/main/Customer_Churn_Modelling.csv)

Right-click on the page and select "Save As" to save the file to your desired location.

## Load Data

To load the data from the CSV file, you'll need to use the `pd.read_csv()` function in Pandas:

```python
import pandas as pd

# Replace 'path/to/your/csv' with the actual file path on your local machine
file_path = 'path/to/your/csv/Customer_Churn_Modelling.csv'
data = pd.read_csv(file_path)
```

## Inspect the Data

Before modifying the data, it's essential to understand its structure and contents. You can use various Pandas functions to inspect the `DataFrame`:

```python
# Display the first few rows of the DataFrame
print(data.head())

# Display the shape (number of rows and columns) of the DataFrame
print(data.shape)

# Display the data types of each column in the DataFrame
print(data.dtypes)

# Display summary statistics for numerical columns
print(data.describe())
```

## Access and Modify Data

Now that you have an understanding of the data, you can access and modify it using various Pandas functions and methods. The following are some examples:

### Select specific columns

```python
# Select the 'Surname' column
surname = data['Surname']

# Select multiple columns, like 'CreditScore' and 'Age'
selected_columns = data[['CreditScore', 'Age']]
```

### Select specific rows using slicing

```python
# Select the first 10 rows of the DataFrame
first_10_rows = data[:10]
```

### Select rows based on conditions

```python
# Select rows where 'Exited' equals 1 (churned customers)
churned_customers = data[data['Exited'] == 1]
```

### Modify data values

```python
# Update the 'CreditScore' column by adding 10 points to each value
data['CreditScore'] = data['CreditScore'] + 10
```

### Add a new column

```python
# Add a new column 'CreditScore_Categories' based on the 'CreditScore' values
def credit_score_category(score):
    if score < 300:
        return 'Bad'
    elif score < 600:
        return 'Poor'
    elif score < 700:
        return 'Fair'
    elif score < 800:
        return 'Good'
    else:
        return 'Excellent'

data['CreditScore_Categories'] = data['CreditScore'].apply(credit_score_category)
```

### Drop a column

```python
# Drop the 'RowNumber' column
data = data.drop('RowNumber', axis=1)
```

### Save the modified DataFrame to a new CSV file

```python
# Save the modified DataFrame to a new CSV file
data.to_csv('Modified_Customer_Churn_Modelling.csv', index=False)
```

These are just a few examples of how to access and modify the data using Pandas for complex data manipulation tasks.
