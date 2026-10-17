
You can change default values of environment variables in Pandas, an example of which is shown here:

```python
import pandas as pd
display_settings = {
    'max_columns': 8,
    'expand_frame_repr': True,
    # Wrap to multiple pages
    'max_rows': 20,
    'precision': 3,
    'show_dimensions': True
}
for op, value in display_settings.items():
    pd.set_option("display.{}".format(op), value)
```

Include the preceding code block in your own code if you want Pandas to display a maximum of 20 rows and 8 columns, and floating point numbers displayed with 3 decimal places. Set `expand_frame_repr` to `True` if you want the output to “wrap around” to multiple pages. The preceding for loop iterates through `display_settings` and sets the options equal to their corresponding values.

In addition, the following code snippet displays all Pandas options and their current values in your code:

```python
print(pd.describe_option())
```

There are various other operations that you can perform with options and their values (such as the `pd.reset()` method for resetting values), as described in the Pandas user guide:

*[https://pandas.pydata.org/pandas-docs/stable/user_guide/options.html](https://pandas.pydata.org/pandas-docs/stable/user_guide/options.html)*

### **Pandas Data Frames**

In simplified terms, a Pandas data frame is a two-dimensional data structure, and it’s convenient to think of the data structure in terms of rows and columns. Data frames can be labeled (rows as well as columns), and the columns can contain different data types. The source of the dataset for a Pandas data frame can be a data file, a database table, a web service, and so forth. Pandas data frame features include:

*   Data Frame Methods

*   Data Frame Statistics

*   Grouping, Pivoting, and Reshaping

*   Handle Missing Data

*   Join Data Frames

The Pandas code samples in this chapter show you almost all the features in the preceding list.

### **Data Frames and Data Cleaning Tasks**

The specific tasks that you need to perform depend on the structure and contents of a dataset. In general you will perform a workflow with the following steps, not necessarily always in this order (and some might be optional). All of the following steps can be performed with a Pandas data frame:

*   Read data into a data frame

*   Display top of data frame

*   Display column data types

*   Display nonmissing values

*   Replace NA with a value

*   Iterate through the columns

*   Statistics for each column

*   Find Missing Values

*   Total missing values

*   Percentage of missing values

*   Sort table values

*   Print summary information

*   Columns with > 50% missing

*   Rename columns

This chapter contains sections that illustrate how to perform many of the steps in the preceding list.

### **Alternatives to Pandas**

Before delving into Pandas code samples, there are alternatives to Pandas that offer very useful features, some of which are in the following list:

*   PySpark (for large datasets)

*   Dask (for distributed processing)

*   Modin (faster performance)

*   Datatable (R data.table for Python)

The inclusion of these alternatives is not intended to diminish Pandas: indeed, you might not need any of the functionality in the preceding list. However, you might need such functionality in the future, so it’s worthwhile for you to know about these alternatives now (and there may be even more powerful alternatives at some point in the future).

## **A Pandas Data Frame with NumPy Example**

[Listing 2.1](#ch02.xhtml#list2.1) displays the contents of pandas_df.py that illustrates how to define several Pandas data frames and display their contents.

***LISTING 2.1: pandas_df.py***

```python
import pandas as pd
import numpy as np
myvector1 = np.array([1,2,3,4,5])
print("myvector1:")
print(myvector1)
print()
mydf1 = pd.DataFrame(myvector1)
print("mydf1:")
print(mydf1)
print()
myvector2 = np.array([i for i in range(1,6)])
print("myvector2:")
print(myvector2)
print()
mydf2 = pd.DataFrame(myvector2)
print("mydf2:")
print(mydf2)
print()
myarray = np.array([[10,30,20],[50,40,60],[1000,2000,3000]])
print("myarray:")
print(myarray)
print()
mydf3 = pd.DataFrame(myarray)
print("mydf3:")
print(mydf3)
print()
```

[Listing 2.1](#ch02.xhtml#list2.1) starts with standard import statements for Pandas and NumPy, followed by the definition of two one-dimensional NumPy arrays and a two-dimensional NumPy array. The NumPy syntax ought to be familiar to you from the examples in Chapter [1](#ch01.xhtml). Each NumPy variable is followed by a corresponding Pandas data frame mydf1, mydf2, and mydf3. Now launch the code in [Listing 2.1](#ch02.xhtml#list2.1) and you will see the following output, and you can compare the NumPy arrays with the Pandas data frames:

myvector1: [1 2 3 4 5] mydf1: 0 0 1 1 2 2 3 3 4 4 5 myvector2: [1 2 3 4 5] mydf2: 0 0 1 1 2 2 3 3 4 4 5 myarray: [[ 10 30 20] [ 50 40 60] [1000 2000 3000]] mydf3: 0 1 2 0 10 30 20 1 50 40 60 2 1000 2000 3000

By contrast, the following code block illustrates how to define a Pandas Series:

names = pd.Series(['SF', 'San Jose', 'Sacramento'])
sizes = pd.Series([852469, 1015785, 485199])
df = pd.DataFrame({ 'Cities': names, 'Size': sizes })
print(df)

Create a Python file with the preceding code (along with the required import statement) and when you launch that code you will see the following output:

City name sizes 0 SF 852469 1 San Jose 1015785 2 Sacramento 485199
