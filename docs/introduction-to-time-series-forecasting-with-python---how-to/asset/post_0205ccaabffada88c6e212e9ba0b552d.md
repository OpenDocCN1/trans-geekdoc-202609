
## 3.4 Sliding Window With Multiple Steps

The number of time steps ahead to be forecasted is important. Again, it is traditional to use different names for the problem depending on the number of time-steps to forecast:

- **One-step Forecast**: This is where the next time step (t+1) is predicted.
- **Multi-step Forecast**: This is where two or more future time steps are to be predicted.

All of the examples we have looked at so far have been one-step forecasts. There are a number of ways to model multi-step forecasting as a supervised learning problem. For now, we are focusing on framing multi-step forecast using the sliding window method. Consider the same univariate time series dataset from the first sliding window example above:

```text
time, measure
1,    100
2,    110
3,    108
4,    115
5,    120
```

Listing 3.7: Example of a small contrived time series dataset.

We can frame this time series as a two-step forecasting dataset for supervised learning with a window width of one, as follows:

```text
X1,  y1,   y2
?,     100,  110
100,  110,  108
110,  108,  115
108,  115,  120
115,  120,  ?
120,  ?,     ?
```

Listing 3.8: Example of a univariate time series dataset as a multi-step or sequence prediction supervised learning problem.

We can see that the first row and the last two rows cannot be used to train a supervised model. It is also a good example to show the burden on the input variables. Specifically, that a supervised model only has X1 to work with in order to predict both y1 and y2. Careful thought and experimentation are needed on your problem to find a window width that results in acceptable model performance.

## 3.5 Summary

In this lesson, you discovered how you can re-frame your time series prediction problem as a supervised learning problem for use with machine learning methods. Specifically, you learned:

- Supervised learning is the most popular way of framing problems for machine learning as a collection of observations with inputs and outputs.
- Sliding window is the way to restructure a time series dataset as a supervised learning problem.
- Multivariate and multi-step forecasting time series can also be framed as supervised learning using the sliding window method.

### 3.5.1 Next

This concludes Part I of the book. Next in Part II you will learn about data preparation for time series, starting with how to load time series data.

# Part II: Data Preparation

## Chapter 4: Load and Explore Time Series Data

The Pandas library in Python provides excellent, built-in support for time series data. Once loaded, Pandas also provides tools to explore and better understand your dataset. In this lesson, you will discover how to load and explore your time series dataset. After completing this tutorial, you will know:

- How to load your time series dataset from a CSV file using Pandas.
- How to peek at the loaded data and query using date-times.
- How to calculate and review summary statistics.

Let’s get started.

### 4.1 Daily Female Births Dataset

In this lesson, we will use the Daily Female Births Dataset as an example. This dataset describes the number of daily female births in California in 1959. You can learn more about the dataset in Appendix A.4. Place the dataset in your current working directory with the filename `daily-total-female-births.csv`.

### 4.2 Load Time Series Data

Pandas represents time series datasets as a Series. A Series¹ is a one-dimensional array with a time label for each row. The main function for loading CSV data in Pandas is the read_csv() function². We can use this to load the time series as a Series object, instead of a DataFrame, as follows:

```python
# load dataset using read_csv()
from pandas import read_csv
series = read_csv('daily-total-female-births.csv', header=0, index_col=0, parse_dates=True, squeeze=True)
print(type(series))
print(series.head())
```

¹ http://pandas.pydata.org/pandas-docs/stable/generated/pandas.Series.html  
² http://pandas.pydata.org/pandas-docs/stable/generated/pandas.read_csv.html

Listing 4.1: Example of loading a CSV using **read_csv()**.

Note the arguments to the **read_csv()** function. We provide it a number of hints to ensure the data is loaded as a **Series**.

- **header=0**: We must specify the header information at row 0.
- **parse_dates=True**: We give the function a hint that data in the first column contains dates that need to be parsed.
- **index_col=0**: We hint that the first column contains the index information for the time series.
- **squeeze=True**: We hint that we only have one data column and that we are interested in a **Series** and not a **DataFrame**.

One more argument you may need to use for your own data is **date_parser** to specify the function to parse date-time values. In this example, the date format has been inferred, and this works in most cases. In those few cases where it does not, specify your own date parsing function and use the **date_parser** argument. Running the example above prints the same output, but also confirms that the time series was indeed loaded as a **Series** object.

```text
<class 'pandas.core.series.Series'>
Date
1959-01-01    35
1959-01-02    32
1959-01-03    30
1959-01-04    31
1959-01-05    44
Name: Births, dtype: int64
```

Listing 4.2: Output of loading a CSV using **read_csv()**.

### 4.3 Exploring Time Series Data

Pandas also provides tools to explore and summarize your time series data. In this section, we'll take a look at a few, common operations to explore and summarize your loaded time series data.

#### 4.3.1 Peek at the Data

It is a good idea to take a peek at your loaded data to confirm that the types, dates, and data loaded as you intended. You can use the **head()** function to peek at the first 5 records or specify the first n number of records to review. For example, you can print the first 10 rows of data as follows.

```python
# summarize first few lines of a file
from pandas import read_csv
series = read_csv('daily-total-female-births.csv', header=0, index_col=0, parse_dates=True, squeeze=True)
print(series.head(10))
```

Listing 4.3: Example of printing the first 10 rows of a time series.

Running the example prints the following:

```text
Date
1959-01-01    35
1959-01-02    32
1959-01-03    30
1959-01-04    31
1959-01-05    44
1959-01-06    29
1959-01-07    45
1959-01-08    43
1959-01-09    38
1959-01-10    27
Name: Births, dtype: int64
```

Listing 4.4: Output of printing the first 10 rows of a dataset.

You can also use the tail() function to get the last n records of the dataset.

#### 4.3.2 Number of Observations

Another quick check to perform on your data is the number of loaded observations. This can help flush out issues with column headers not being handled as intended, and to get an idea on how to effectively divide up data later for use with supervised learning algorithms. You can get the dimensionality of your Series using the size parameter.

```python
# summarize the dimensions of a time series
from pandas import read_csv
series = read_csv('daily-total-female-births.csv', header=0, index_col=0, parse_dates=True, squeeze=True)
print(series.size)
```

Listing 4.5: Example of printing the dimensions of a time series.

Running this example we can see that as we would expect, there are 365 observations, one for each day of the year in 1959.

```text
365
```

Listing 4.6: Output of printing the dimensions of a dataset.

#### 4.3.3 Querying By Time

You can slice, dice, and query your series using the time index. For example, you can access all observations in January as follows:

```python
# query a dataset using a date-time index
from pandas import read_csv
series = read_csv('daily-total-female-births.csv', header=0, index_col=0, parse_dates=True, squeeze=True)
print(series['1959-01'])
```

Listing 4.7: Example of querying a time series by date-time.
