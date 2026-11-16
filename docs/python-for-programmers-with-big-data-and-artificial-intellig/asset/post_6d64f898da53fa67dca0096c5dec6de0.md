
## flatten vs. ravel

You can take a multidimensional array and flatten it into a single dimension with the methods **flatten** and **ravel**. Method **flatten** *deep copies* the original array's data:

Click here to view code image

```python
In [8]: grades = np.array([[87, 96, 70], [100, 87, 90]])

In [9]: grades
Out[9]:
array([[ 87, 96, 70],
       [100, 87, 90]])

In [10]: flattened = grades.flatten()

In [11]: flattened
Out[11]: array([ 87, 96, 70, 100, 87, 90])

In [12]: grades
Out[12]:
array([[ 87, 96, 70],
       [100, 87, 90]])
```

To confirm that **grades** and **flattened** do *not* share the data, let's modify an element of **flattened**, then display both arrays:

Click here to view code image

```python
In [13]: flattened[0] = 100

In [14]: flattened
Out[14]: array([100, 96, 70, 100, 87, 90])

In [15]: grades
Out[15]:
array([[ 87, 96, 70],
       [100, 87, 90]])
```

Method **ravel** produces a *view* of the original array, which *shares* the **grades** array's data:

Click here to view code image

```python
In [16]: raveled = grades.ravel()

In [17]: raveled
Out[17]: array([ 87, 96, 70, 100, 87, 90])

In [18]: grades
Out[18]:
array([[ 87, 96, 70],
       [100, 87, 90]])
```

To confirm that `grades` and `raveled` share the same data, let's modify an element of `raveled`, then display both arrays:

Click here to view code image

```python
In [19]: raveled[0] = 100

In [20]: raveled
Out[20]: array([100, 96, 70, 100, 87, 90])

In [21]: grades
Out[21]:
array([[100, 96, 70],
       [100, 87, 90]])
```

## Transposing Rows and Columns

You can quickly **transpose** an `array`'s rows and columns—that is “flip” the `array`, so
the rows become the columns and the columns become the rows. The **T attribute**
returns a transposed _view_ (shallow copy) of the `array`. The original `grades` array
represents two students’ grades (the rows) on three exams (the columns). Let's
transpose the rows and columns to view the data as the grades on three exams (the
rows) for two students (the columns):

Click here to view code image

```python
In [22]: grades.T
Out[22]:
array([[100, 100],
       [ 96, 87],
       [ 70, 90]])
```

Transposing does _not_ modify the original `array`:

```python
In [23]: grades
Out[23]:
array([[100, 96, 70],
       [100, 87, 90]])
```

## Horizontal and Vertical Stacking

You can combine arrays by adding more columns or more rows—known as *horizontal stacking* and *vertical stacking*. Let’s create another 2-by-3 array of grades:

Click here to view code image

```python
In [24]: grades2 = np.array([[94, 77, 90], [100, 81, 82]])
```

Let’s assume `grades2` represents three additional exam grades for the two students in the `grades` array. We can combine `grades` and `grades2` with NumPy’s **hstack (horizontal stack) function** by passing a tuple containing the arrays to combine. The extra parentheses are required because `hstack` expects one argument:

Click here to view code image

```python
In [25]: np.hstack((grades, grades2))
Out[25]:
array([[100, 96, 70, 94, 77, 90],
       [100, 87, 90, 100, 81, 82]])
```

Next, let’s assume that `grades2` represents two more students’ grades on three exams. In this case, we can combine `grades` and `grades2` with NumPy’s **vstack (vertical stack) function**:

Click here to view code image

```python
In [26]: np.vstack((grades, grades2))
Out[26]:
array([[100, 96, 70],
       [100, 87, 90],
       [94, 77, 90],
       [100, 81, 82]])
```

## 7.14 INTRO TO DATA SCIENCE: PANDAS SERIES AND DATAFRAMES

NumPy’s `array` is optimized for homogeneous numeric data that’s accessed via integer indices. Data science presents unique demands for which more customized data structures are required. Big data applications must support mixed data types, customized indexing, missing data, data that’s not structured consistently and data that needs to be manipulated into forms appropriate for the databases and data analysis packages you use.

**Pandas** is the most popular library for dealing with such data. It provides two key collections that you'll use in several of our Intro to Data Science sections and throughout the data science case studies—*Series* for one-dimensional collections and *DataFrames* for two-dimensional collections. You can use pandas’ *MultiIndex* to manipulate multi-dimensional data in the context of `Series` and `DataFrames`.

Wes McKinney created pandas in 2008 while working in industry. The name pandas is derived from the term “panel data,” which is data for measurements over time, such as stock prices or historical temperature readings. McKinney needed a library in which the same data structures could handle both time- and non-time-based data with support for data alignment, missing data, common database-style data manipulations, and more. 4

4 McKinney, Wes. Python for Data Analysis: Data Wrangling with Pandas, NumPy, and IPython, pp. 123-165. Sebastopol, CA: O'Reilly Media, 2018.

NumPy and pandas are intimately related. `Series` and `DataFrames` use arrays “under the hood.” `Series` and `DataFrames` are valid arguments to many NumPy operations. Similarly, `arrays` are valid arguments to many `Series` and `DataFrame` operations.

Pandas is a massive topic—the PDF of its documentation 5 is over 2000 pages. In this and the next chapters’ Intro to Data Science sections, we present an introduction to pandas. We discuss its `Series` and `DataFrames` collections, and use them in support of data preparation. You’ll see that `Series` and `DataFrames` make it easy for you to perform common tasks like selecting elements a variety of ways, filter/map/reduce operations (central to functional-style programming and big data), mathematical operations, visualization and more.

5 For the latest pandas documentation, see http://pandas.pydata.org/pandas-docs/stable/.

### 7.14.1 pandas Series

A `Series` is an enhanced one-dimensional `array`. Whereas `array`s use only zero-based integer indices, `Series` support custom indexing, including even non-integer indices like strings. `Series` also offer additional capabilities that make them more convenient for many data-science oriented tasks. For example, `Series` may have missing data, and many `Series` operations ignore missing data by default.

#### Creating a Series with Default Indices

By default, a `Series` has integer indices numbered sequentially from 0. The following creates a `Series` of student grades from a list of integers:

Click here to view code image

```python
In [1]: import pandas as pd

In [2]: grades = pd.Series([87, 100, 94])
```

The initializer also may be a tuple, a dictionary, an array, another `Series` or a single value. We'll show a single value momentarily.

#### Displaying a Series

Pandas displays a `Series` in two-column format with the indices _left aligned_ in the left column and the values _right aligned_ in the right column. After listing the `Series` elements, pandas shows the data type (`dtype`) of the underlying `array`'s elements:

```python
In [3]: grades
Out[3]:
0    87
1   100
2    94
dtype: int64
```

Note how easy it is to display a `Series` in this format, compared to the corresponding code for displaying a list in the same two-column format.

#### Creating a Series with All Elements Having the Same Value

You can create a `Series` of elements that all have the same value:

Click here to view code image

```python
In [4]: pd.Series(98.6, range(3))
Out[4]:
0    98.6
1    98.6
2   98.6
dtype: float64
```

The second argument is a one-dimensional iterable object (such as a list, an `array` or a `range`) containing the `Series`' indices. The number of indices determines the number of elements.

#### Accessing a Series' Elements

You can access a Series's elements via square brackets containing an index:

```python
In [5]: grades[0]
Out[5]: 87
```

#### Producing Descriptive Statistics for a Series

`Series` provides many methods for common tasks including producing various descriptive statistics. Here we show `count`, `mean`, `min`, `max` and `std` (standard deviation):

Click here to view code image

```python
In [6]: grades.count()
Out[6]: 3

In [7]: grades.mean()
Out[7]: 93.66666666666667

In [8]: grades.min()
Out[8]: 87

In [9]: grades.max()
Out[9]: 100

In [10]: grades.std()
Out[10]: 6.506407098647712
```

Each of these is a functional-style reduction. Calling `Series` method `describe` produces all these stats and more:

Click here to view code image

```python
In [11]: grades.describe()
Out[11]:
```
