```
Out[9]:
count   1309
unique   2
top    False
freq    809
Name: survived, dtype: object
```

For non-numeric data, describe displays different descriptive statistics:

+   • count is the total number of items in the result.
+   • unique is the number of unique values (2) in the result—True (survived) and False (died).
+   • top is the most frequently occurring value in the result.
+   • freq is the number of occurrences of the top value.

# 9.12.5 Passenger Age Histogram

Visualization is a nice way to get to know your data. Pandas has many built-in visualization capabilities that are implemented with Matplotlib. To use them, first enable Matplotlib support in IPython:

```
In [10]: %matplotlib
```

A histogram visualizes the distribution of numerical data over a range of values. A DataFrame’s hist method automatically analyzes each numerical column’s data and produces a corresponding histogram. To view histograms of each numerical data column, call hist on your DataFrame:

lick here to view code image

```
In [11]: histogram = titanic.hist()
```

The Titanic dataset contains only one numerical data column, so the diagram shows one histogram for the age distribution. For datasets with multiple numerical columns, hist creates a separate histogram for each numerical column.