
mean of 0 and a standard deviation of 1.

Next, the variable url is initialized with the location of a website that returns CSV-based data. The names variable contains an array of column names that are used to label the columns of the CSV-based data. Next, the dataframe is initialized with the contents of the CSV-based data (retrieved from the location specified by the url).

The next portion initializes the variable array with the left-most columns of every row in the dataframe, and the variable y is initialized with the ninth column of the variable array. The next portion invokes the fit method of the StandardScaler class in order to fit the data contained in X, and the result is used to initialize the variable scaler. The next statement invokes transform() method on the contents of X and the results are used to initialize the variable scaler, which concludes the required data transformations (finally!).

The final portion displays all the columns of the first five rows of the scaler. The output is here:

```
minimum: 1
median: 3.0
maximum: 6
values: [2.735e+02, 6.200e+04, 3.000e+02, 4.600e+03, 1.000e+00, 2.000e+00]
```

first 5 prices:
0: 42.0
1: 38.0
2: 49.0
3: 60.0
4: 61.0

Name: price, dtype: float64

median price: 62.0

correlation matrix:

| | price |
| :--- | :--- |
| price | 1.000000 |
| size | 0.535796 |
| bathrms | 0.516719 |
| stories | 0.421190 |
| garagepl | 0.383302 |
| Unnamed: 0 | 0.376000 |
| bedrooms | 0.366494 |

## PANDAS DATAFRAMES, NUMPY FUNCTIONS, AND LARGE DATASETS

Pandas DataFrames containing numeric data can be used in conjunction with NumPy functions such as log, exp, and sqrt (and other NumPy functions). Example of such functions are shown here:

```
df.exp(df)
np.asarray(df)
df.T.dot(df)
```

The dot method on Series implements a dot product:

```
s1 = pd.Series(np.arange(5, 10))
s1.dot(s1)
```

However, a Pandas DataFrame is not intended to be a direct replacement for ndarray as some of its indexing semantics are quite different from a matrix.

Another challenge that you might face: what do you do with large datasets that exceed the memory of your machine? The solution involves a “chunking” technique for reading portions of data into memory. Chunking enables you to “stream” data from a file into a Pandas DataFrame, and you can specify the number of rows in a “chunk” of data. An example of chunking is shown here:

```python
import pandas as pd
mydata = pd.DataFrame()

# Modify chunksize based on your requirements
for chunk in pd.read_csv('myfile.csv', iterator=True, chunksize=5000):
    mydata = pd.concat([mydata, chunk], ignore_index=True)
```

## WORKING WITH PANDAS SERIES

A Pandas Series is a one-dimensional labeled array that can be populated with any data type: integers, strings, floating point numbers, Python objects, and so forth. The axis labels are collectively referred to as the index. Create Pandas Series as shown here in the Python REPL:

```python
>>> s = pd.Series(data, index=index)
```

The variable data in the preceding code snippet is a scalar value, a Python dict, an ndarray, and so forth. The variable index is a list of axis labels, which consists of different values, as discussed in the following subsections.

### From ndarray

If the variable data in the code snippet below is an ndarray, then index must be the same length as the variable data:

```python
>>> s = pd.Series(data, index=index)
```

However, if no index is passed, an index will be automatically created with the values [0, ..., len(data) - 1]. Here is another example:

```python
>>> s = pd.Series(np.random.randn(5), index=['a', 'b', 'c', 'd', 'e'])
>>> s
```

The output of the preceding code snippet in the Python REPL here:

```
a  0.4691
b -0.2829
c -1.5091
d -1.1356
e  1.2121
dtype: float64
```

```python
>>> s.index
```

The output of the preceding code snippet in the Python REPL here:

```python
Index(['a', 'b', 'c', 'd', 'e'], dtype='object')
```

```python
>>> pd.Series(np.random.randn(5))
```

The output of the preceding code snippet in the Python REPL here:

```
0    0.1234
1    0.5678
2   -0.9012
3    0.3456
4    0.7890
dtype: float64
```

Note that Pandas DataFrame supports unique index values. However, if the index contains duplicate values, an exception will be raised. Here is an example:

```python
>>> d = {'a': [1, 2, 3], 'b': [4, 5, 6]}
>>> df = pd.DataFrame(d, index=['0', '1', '0'])
print(df)
   a  b
0  1  4
1  2  5
0  3  6
```

The output of the preceding code snippet in the Python REPL here:

```python
>>> df.index
Index(['0', '1', '0'], dtype='object')
```

```python
>>> df = pd.DataFrame({'a': [1, 2, 3], 'b': [4, 5, 6]}, index=['0', '1', '0'])
>>> df.index.is_unique
False
```

The following shows shows if the index is unique:

```python
>>> df = pd.DataFrame({'a': [1, 2, 3], 'b': [4, 5, 6]}, index=['0', '1', '2'])
>>> df.index.is_unique
True
```

The following shows how to reset the index of a DataFrame:

```python
>>> df = pd.DataFrame({'a': [1, 2, 3], 'b': [4, 5, 6]}, index=['0', '1', '0'])
>>> df.reset_index()
   index  a  b
0     0  1  4
1     1  2  5
2     0  3  6
```

The following shows how to reset the index and drop the old index:

```python
>>> df = pd.DataFrame({'a': [1, 2, 3], 'b': [4, 5, 6]}, index=['0', '1', '0'])
>>> df.reset_index(drop=True)
   a  b
0  1  4
1  2  5
2  3  6
```

 following shows how to set the index of a DataFrame:

```python
>>> df = pd.DataFrame({'a': [1, 2, 3], 'b': [4, 5, 6]})
>>> df.set_index('a')
     b
a
1  4
2  5
3  6
```

The following shows how to set the index and modify the original DataFrame:

```python
>>> df = pd.DataFrame({'a': [1, 2, 3], 'b': [4, 5, 6]})
>>> df.set_index('a', inplace=True)
     b
a
1  4
2  5
3  6
```

The following shows how to swap the index and the columns:

```python
>>> df = pd.DataFrame({'a': [1, 2, 3], 'b': [4, 5, 6]}, index=['0', '1', '2'])
>>> df.swapframe()
     0  1  2
a  1  2  3
b  4  5  6
```

The following shows how to rename the index labels of a DataFrame:

```python
>>> df = pd.DataFrame({'a': [1, 2, 3], 'b': [4, 5, 6]}, index=['0', '1', '2'])
>>> df.rename(index={'0': 'x', '1': 'y'})
     a  b
x  1  4
y  2  5
2  3  6
```

The following shows how to rename the column labels of a DataFrame:

```python
>>> df = pd.DataFrame({'a': [1, 2, 3], 'b': [4, 5, 6]})
>>> df.rename(columns={'a': 'alpha', 'b': 'beta'})
   alpha  beta
0      1      4
1      2      5
2      3      6
```

The following shows how to replace the columns of a DataFrame:

```python
>>> df = pd.DataFrame({'a': [1, 2, 3], 'b': [4, 5, 6]})
>>> df.columns = ['alpha', 'beta']
   alpha  beta
0      1      4
1      2      5
2      3      6
```

The following shows how to replace the index of a DataFrame:

```python
>>> df = pd.DataFrame({'a': [1, 2, 3], 'b': [4, 5, 6]})
>>> df.index = ['x', 'y', 'z']
   a  b
x  1  4
y  2  5
z  3  6
```

The following shows how to add a row to a DataFrame:

```python
>>> df = pd.DataFrame({'a': [1, 2, 3], 'b': [4, 5, 6]})
>>> df.loc[3] = [7, 8]
   a  b
0  1  4
1  2  5
2  3  6
3  7  8
```

The following shows how to delete a row from a DataFrame:

```python
>>> df = pd.DataFrame({'a': [1, 2, 3], 'b': [4, 5, 6]})
>>> df.drop(1)
   a  b
0  1  4
2  3  6
3  7  8
```

The following shows how to delete a column from a DataFrame:

```python
>>> df = pd.DataFrame({'a': [1, 2, 3], 'b': [4, 5, 6]})
>>> df.drop('b', axis=1)
   a
0  1
1  2
2  3
3  7
```

The following shows how to update a value in a DataFrame:

```python
>>> df = pd.DataFrame({'a': [1, 2, 3], 'b': [4, 5, 6]})
>>> df.loc[0, 'a'] = 10
   a  b
0 10  4
1  2  5
2  3  6
3  7  8
```

The following shows how to update multiple values in a DataFrame:

```python
>>> df = pd.DataFrame({'a': [1, 2, 3], 'b': [4, 5, 6]})
>>> df.loc[0:1, ['a', 'b']] = [[10, 20], [30, 40]]
   a   b
0 10  20
1 30  40
2  3  6
3  7  8
```

The following shows how to map a function over a Series:

```python
>>> df = pd.DataFrame({'a': [1, 2, 3], 'b': [4, 5, 6]})
>>> df['a'] = df['a'].map(lambda x: x**2)
   a  b
0  1  4
1  4  5
2  9  6
3  7  8
```

The following shows how to apply a function along an axis:

```python
>>> df = pd.DataFrame({'a': [1, 2, 3], 'b': [4, 5, 6]})
>>> df.apply(lambda x: x.sum(), axis=0)
a     6
b    15
dtype: int64
```

## GROUP BY OPERATIONS
[PAGE 156 - content missing in source]

The following shows how to apply a function to each row:

```python
>>> df = pd.DataFrame({'a': [1, 2, 3], 'b': [4, 5, 6]})
>>> df.apply(lambda x: x.sum(), axis=1)
0    5
1    7
2    9
dtype: int64
```

The following shows how to group by and aggregate:

```python
>>> df = pd.DataFrame({'a': [1, 1, 2, 2], 'b': [4, 5, 6, 7]})
>>> df.groupby('a').agg(['sum', 'mean'])
      sum  mean
a             
1     9   4.5
2    13   6.5
```
