

ax.legend()

![](img/fe3427740784586362e0a35d3200b425_218_0.png)

## Histogram

The “hist” method can be used to generate a Histogram in matplotlib. The sample code below will allow passing of categorical data such as the points column from the “wine review” dataset to auto calculate the occurrences of each class.

```
# creation of figure and axis
fig, ax = plt.subplots()
# plotting histogram
ax.hist(wine_reviews['points'])
# setting title and labels
ax.set_title('Wine Review Scores')
ax.set_xlabel('Points')
ax.set_ylabel('Frequency')
```

![](img/fe3427740784586362e0a35d3200b425_219_0.png)

## Bar Chart

The “bar” method can be used to generate a bar chart in matplotlib. These charts are not capable of auto calculating the occurrences of each category, so the “value_counts” function from the Pandas library needs to be used. Any set of categorical data lacking a wide variety of categories can be easily plotted using the bar chart. However, any data set containing more than 30 categories of data are too complicated to yield an easy to understand bar chart. The sample code below will allow creation of a bar chart from the “wine review” dataset using the “value_counts” function.

```
# creation of figure and axis
fig, ax = plt.subplots()
# counting the occurrence of each class
data = wine_reviews['points'].value_counts()
# getting x and y data
points = data.index
frequency = data.values
# creation of bar chart
ax.bar(points, frequency)
# setting title and labels
ax.set_title('Wine Review Scores')
ax.set_xlabel('Points')
ax.set_ylabel('Frequency')
```

![](img/fe3427740784586362e0a35d3200b425_220_0.png)

## Pandas

Pandas provide highly intuitive and user-friendly high-level data structures. "Pandas" has achieved popularity in the machine learning algorithm developer community, with built-in techniques for data aggregation, grouping, and filtering as well as results of time series analysis. The Pandas library has two primary structures: one-dimensional "Series" and two-dimensional "Data Frames."

Some of the key features provided by “Pandas” are listed below:

- A quick and effective "Data Frame object" with embedded indexing to be used in data manipulation activities.
- Tools to read and write data between internal memory data structures and multiple file formats, such as "CSV" and text, "Microsoft Excel," "SQL databases," and quick "HDF5 format".
- Intelligent data alignment and integrated management of incomplete data by achieving automatic label driven computational alignment and readily manipulating unorganized data into an orderly manner.
- Flexible reconstructing and pivoting of datasets.
- Smart label-based slicing and indexing of big data sets, as well as the creation of data subsets.
- Columns can be added to and removed from data structures to achieve the desired size of the database.
- Aggregation or transformation of data using a sophisticated "Group By" system enabling execution of the "split-apply-combine" technique on the data.
- Highly efficient merge and join functions of the data set.
- "Hierarchical axis indexing" offers a simple way to work in a low dimensional data structure even with high dimensional data.
- Time-series functionalities, including "date range generation and frequency conversion, moving window statistics, moving window linear regressions, date shifting, and lagging." Also the creation of "domain-specific time offsets" and capability of joining time series with no data loss.
- Having most of the underlying code in "Cython" or "C," Pandas boasts high performance and efficiency.
- Python, in combination with Pandas, is being used in a broad range of academic and industrial sectors, including Financial Services, Statistics, Neurobiology, Economics, Marketing and Advertising, Online Data Analytics, among others.

The two types of Data Structures offered by Pandas are: “Pandas DataFrame” and “Pandas Series.”

## Pandas DataFrame

It is defined as “2-D labeled data structure with columns of a potentially different type”. It has a high resemblance to the Excel spreadsheet, as shown in the picture below, with multiple similar features for analysis, modification, and extraction of valuable insights from the data. You can create a “Pandas DataFrame” by entering datasets from “Excel,” “CSV,” and “MySQL database,” among others.

| | NAME | AGE | DESIGNATION |
|---|---|---|---|
| 1 | a | 20 | VP |
| 2 | b | 27 | CEO |
| 3 | c | 35 | CFO |
| 4 | d | 55 | VP |
| 5 | e | 18 | VP |
| 6 | f | 21 | CEO |
| 7 | g | 35 | MD |

For instance, in the picture above assume “Keys” are represented by the name of the columns and “Values” are represented by the list of items in that column, a “Python dictionary” can be used to represent this as shown in the code below:

```
my_dict = {
    'name': ["a", "b", "c", "d", "e", "f", "g"],
    'age': [20, 27, 35, 55, 18, 21, 35],
    'designation': ["VP", "CEO", "CFO", "VP", "VP", "CEO", "MD"]
}
```

The “Pandas DataFrame” can be created from this dictionary by using the code below:

```
import pandas as pd
df = pd.DataFrame(my_dict)
```

The resulting “DataFrame” is shown in the picture below which resembles the excel spreadsheet:

|   | age | designation | name |
|---|---|---|---|
| 0 | 20 | VP | a |
| 1 | 27 | CEO | b |
| 2 | 35 | CFO | c |
| 3 | 55 | VP | d |
| 4 | 18 | VP | e |
| 5 | 21 | CEO | f |
| 6 | 35 | MD | g |

If you would like to define index values for the rows, you will have to add the “index” parameter in the “DataFrame ()” clause as shown below:

```
df = pd.DataFrame(my_dict, index=[1, 2, 3, 4, 5, 6, 7])
```

To obtain “string” indexes for the data instead of numeric, use the code below:

```
df = pd.DataFrame(
    my_dict,
    index=["First", "Second", "Third", "Fourth", "Fifth", "Sixth",
           "Seventh"]
)
```

Now, as these index values are uniform, you could execute the code below to utilize the “NumPy arrays” as index values:

```
np_arr = np.array([10, 20, 30, 40, 50, 60, 70])
df = pd.DataFrame(my_dict, index=np_arr)
```

Similar to “NumPy”, the columns of “DataFrame” are also homogeneous.
You can use dictionary like syntax or add the column name with
“DataFrame”, to view the data type of the column, as shown in the code
below:

```
df['age'].dtype  # Dict Like Syntax
df.age.dtype  # DataFrame.ColumnName
df.name.dtype  # DataFrame.ColumnName
```

You can use the code below to selectively view the record or rows available
within the “Pandas DataFrame,” by using the “head ( )” function for the
first five rows and “tail ( )” function for the last five rows. For instance, use
the code below to view the first 3 rows of the data:

```
df.head(3)  # Display first 3 Rows
```

## Pandas Series

It can be defined as a "one-dimensional labeled array capable of holding
data of any type (integer, string, float, python objects)." Simply put, it is
like a column in an excel spreadsheet. To generate a “Pandas Series” from
an array, a “NumPy” module must be imported and used with “array ()”
function, as shown in the code below:

```
import pandas as pd
import numpy as np

# simple array
data = np.array(['m', 'a', 'c', 'h', 'T', 'n', 'e'])
ser = pd.Series(data)
print(ser)
```

## Data Visualization with Scatter Plots

A scatter plot can be defined as "a two-dimensional data visualization that uses dots to represent the values obtained for two different variables-one plotted along the x-axis and the other plotted along the y-axis." It is also known as “scatter graph” or "scatter chart." For instance, the "scatter plot" seen in the picture below depicts a fictional set of height and weight measures for children. Each "dot" in the plot is used to represent an individual, with measures of their height along the "x-axis" and weight along the "y-axis."

![](img/fe3427740784586362e0a35d3200b425_225_0.png)

