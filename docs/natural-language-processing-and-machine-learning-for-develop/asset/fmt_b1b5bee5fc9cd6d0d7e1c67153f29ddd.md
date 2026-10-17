
contents of df:         January  February  March apples        10        30     20 oranges       50        40     60 beer        1000      2000   3000   contents of January: apples       10 oranges      50 beer       1000 Name: January, dtype: int64   Number of Rows: 3   Number of Columns: 3   Number of Rows and Columns: (3, 3)   Column Names: Index(\['January', 'February', 'March'\], dtype='object')   Column types: January     int64 February    int64 March       int64 dtype: object   Description:           January     February        March count     3.000000     3.000000     3.000000 mean    353.333333   690.000000  1026.666667 std     560.386771  1134.504297  1709.073823 min      10.000000    30.000000    20.000000 25%      30.000000    35.000000    40.000000 50%      50.000000    40.000000    60.000000 75%     525.000000  1020.000000  1530.000000 max    1000.000000  2000.000000  3000.000000 

## `Pandas` Boolean Data Frames

`Pandas` supports Boolean operations on Data frames, such as the logical OR, the logical AND, and the logical negation of a pair of Data frames. [Listing 2.3](#ch02.xhtml#list2.3) displays the contents of `pandas_boolean_df.py` that illustrates how to define a `Pandas` data frame whose rows and columns are Boolean values.

***LISTING 2.3:** `pandas_boolean_df.py`***

```python
import pandas as pd
df1 = pd.DataFrame({'a': [1, 0, 1], 'b': [0, 1, 1]}, dtype=bool)
df2 = pd.DataFrame({'a': [0, 1, 1], 'b': [1, 1, 0]}, dtype=bool)
print("df1 & df2:")
print(df1 & df2)
print("df1 | df2:")
print(df1 | df2)
print("df1 ^ df2:")
print(df1 ^ df2)
```

[Listing 2.3](#ch02.xhtml#list2.3) initializes the Data frames `df1` and `df2`, and then computes `df1 & df2`, `df1 | df2`, `df1 ^ df2`, which represent the logical AND, the logical OR, and the logical negation, respectively, of `df1` and `df2`. The output from launching the code in [Listing 2.3](#ch02.xhtml#list2.3) is here:

`df1 & df2`:       a      b 0  False  False 1  False   True 2   True  False  
`df1 | df2`:      a     b 0  True  True 1  True  True 2  True  True  
`df1 ^ df2`:       a      b 0   True   True 1   True  False 2  False   True 

### `Transposing` a `Pandas` Data Frame

The `T` attribute (as well as the `transpose` function) enables you to generate the transpose of a `Pandas` data frame, similar to a `NumPy` `ndarray`. The transpose operation switches rows to columns and columns to rows. For example, the following code snippet defines a `Pandas` data frame `df1` and then displays the transpose of `df1`:

```python
df1 = pd.DataFrame({'a': [1, 0, 1], 'b': [0, 1, 1]}, dtype=int)
print("df1.T:")
print(df1.T)
```

The output is here:

`df1.T`:    0  1  2 a  1  0  1 b  0  1  1 

The following code snippet defines `Pandas` data frames `df1` and `df2` and then displays their sum:

```python
df1 = pd.DataFrame({'a' : [1, 0, 1], 'b' : [0, 1, 1]}, dtype=int)
df2 = pd.DataFrame({'a' : [3, 3, 3], 'b' : [5, 5, 5]}, dtype=int)
print("df1 + df2:")
print(df1 + df2)
```

The output is here:

`df1 + df2`:    a  b 0  4  5 1  3  6 2  4  6 

## `Pandas` Data Frames and Random Numbers

[Listing 2.4](#ch02.xhtml#list2.4) displays the contents of `pandas_random_df.py` that illustrates how to create a `Pandas` data frame with random numbers.

***LISTING 2.4:** `pandas_random_df.py`***

```python
import pandas as pd
import numpy as np
df = pd.DataFrame(np.random.randint(1, 5, size=(5, 2)), columns=['a','b'])
df = df.append(df.agg(['sum', 'mean']))
print("Contents of data frame:")
print(df)
```

[Listing 2.4](#ch02.xhtml#list2.4) defines the `Pandas` data frame `df` that consists of 5 rows and 2 columns of random integers between 1 and 5. Notice that the columns of `df` are labeled “a” and “b.” In addition, the next code snippet appends two rows consisting of the sum and the mean of the numbers in both columns. The output of [Listing 2.4](#ch02.xhtml#list2.4) is here:

         a    b 0      1.0  2.0 1      1.0  1.0 2      4.0  3.0 3      3.0  1.0 4      1.0  2.0 sum   10.0  9.0 mean   2.0  1.8 

[Listing 2.5](#ch02.xhtml#list2.5) displays the contents of `pandas_combine_df.py` that illustrates how to combine `Pandas` data frames.

***LISTING 2.5:** `pandas_combine_df.py`***

```python
import pandas as pd
import numpy as np
df = pd.DataFrame({'foo1' : np.random.randn(5), 'foo2' : np.random.randn(5)})
print("contents of df:")
print(df)
print("contents of foo1:")
print(df.foo1)
print("contents of foo2:")
print(df.foo2)
```

[Listing 2.5](#ch02.xhtml#list2.5) defines the `Pandas` data frame `df` that consists of 5 rows and 2 columns (labeled “foo1” and “foo2”) of random real numbers between 0 and 5. The next portion of [Listing 2.5](#ch02.xhtml#list2.5) displays the contents of `df` and `foo1`. The output of [Listing 2.5](#ch02.xhtml#list2.5) is here:

contents of df:       foo1      foo2 0  0.274680 \_0.848669 1 \_0.399771 \_0.814679 2  0.454443 \_0.363392 3  0.473753  0.550849 4 \_0.211783 \_0.015014 contents of foo1: 0    0.256773 1    1.204322 2    1.040515 3   \_0.518414 4    0.634141 Name: foo1, dtype: float64 contents of foo2: 0   \_2.506550 1   \_0.896516 2   \_0.222923 3    0.934574 4    0.527033 Name: foo2, dtype: float64 

## Reading CSV Files in `Pandas`

`Pandas` provides the `read_csv()` method for reading the contents of CSV files. For example, [Listing 2.6](#ch02.xhtml#list2.6) displays the contents of `sometext.txt` that contains labeled data (spam or ham), and [Listing 2.7](#ch02.xhtml#list2.7) displays the contents of `read_csv_file.py` that illustrates how to read the contents of a CSV file.

***LISTING 2.6:** `sometext.csv`***

```
type    text ham     Available only for today ham     I'm joking with you spam    Free entry in 2 a wkly comp ham     U dun say so early hor ham     I don't think he goes to usf spam    FreeMsg Hey there ham     my brother is not sick ham     As per your request Melle spam    WINNER!! As a valued customer 
```

***LISTING 2.7:** `read_csv_file.py`***

```python
import pandas as pd
import numpy as np
df = pd.read_csv('sometext.csv', delimiter='\\t')
print("=> First five rows:")
print(df.head(5))
```

[Listing 2.7](#ch02.xhtml#list2.7) reads the contents of `sometext.csv`, whose columns are separated by a tab (“\\t”) delimiter. Launch the code in [Listing 2.7](#ch02.xhtml#list2.7) and you will see the following output:

\=> First five rows:   type                           text 0   ham      Available only for today 1   ham           I'm joking with you 2  spam   Free entry in 2 a wkly comp 3   ham        U dun say so early hor 4   ham  I don't think he goes to usf 

The default value for the `head()` method is 5, but you can display the first n rows of a data frame `df` with the code snippet `df.head(n)`.

You can also use the `sep` parameter specifies a different separator, and the `names` parameter specifies the column names in the data that you want to read, an example of which is here:

```python
df2 = pd.read_csv("data.csv",sep="|", 
                  names=["Name","Surname","Height","Weight"])
```

`Pandas` also provides the `read_table()` method for reading the contents of CSV files, which uses the same syntax as the `read_csv()` method.

## The `loc()` and `iloc()` Methods in `Pandas`

If you want to display the contents of a record in a data frame, specify the index of the row in the `Pandas` `loc()` method. For example, the following code snippet displays the data by feature name in a Data frame `df`:

```python
df.loc[feature_name]
```

Select the first row of the “height” column in a Data frame:

```python
df.loc[0], ['height']
```

However, the following code snippet uses the `iloc()` function to display the first 8 records of the name column with this code snippet:

```python
df.iloc[0:8]['name']
```

## Converting Categorical Data to Numeric Data

One common task in machine learning involves converting a feature containing character data into a feature that contains numeric data. [Listing 2.8](#ch02.xhtml#list2.8) displays the contents of `cat2numeric.py` that illustrates how to replace a text field with a corresponding numeric field.

***LISTING 2.8:** `cat2numeric.py`**
