
# Q8: Explain various statistical measures supported by pandas.

**Ans:**

*   **axes:** Print row index as well as column index.
*   **sum:** Calculates the sum of all series.
*   **mean:** Calculates mean of all series.
*   **median:** Calculates the median of all series.
*   **std:** Calculates standard deviation.
*   **count:** Calculates sum of various series.
*   **cumsum:** Calculates cumulative sum.

```python
import pandas as pd
import numpy as np

d = {'Name': pd.Series(['Raja', 'Raju', 'Ricky', 'Shiv', 'Vishnu', 'Ramesh', 'Mahender',
                        'Lious', 'Salman', 'SRK', 'VV', 'MM']),
     'Age': pd.Series([25, 26, 25, 23, 30, 29, 23, 34, 40, 30, 51, 46]),
     'Rating': pd.Series([4.23, 3.24, 3.98, 2.56, 3.20, 4.6, 3.8, 3.78, 2.98, 4.80, 4.10, 3.65])}
```

![](OEBPS/images/90.jpg)

**Output:**

![](OEBPS/images/p84.jpg)

```
axes
[RangeIndex(start=0, stop=12, step=1), Index(['Age', 'Name', 'Rating'], dtype='object')]

sum
Age       382
Name    RajaRajuRickyShivVishnuRameshMahenderLiousSalm•
Rating    44.92
dtype: object

sum of axis 1
0     29.23
1     29.24
2     28.98
3     25.56
4     33.20
5     33.60
6     26.80
7     37.78
8     42.98
9     34.80
10    55.10
11    49.65
dtype: float64

mean
Age      31.833333
Rating    3.743333
dtype: float64

std
Age      9.232682
Rating    0.661628
dtype: float64

count
Age      12
Name     12
Rating   12
dtype: int64

median
Age      29.50
Rating    3.79
dtype: float64

cumsum
    Age  Name                              Rating
0    25  Raja                                4.23
1    51  RajaRaju                            7.47
2    76  RajaRajuRicky                      11.45
3    99  RajaRajuRickyShiv                  14.01
4   129  RajaRajuRickyShivVishnu            17.21
5   158  RajaRajuRickyShivVishnuRamesh      21.81
6   181  RajaRajuRickyShivVishnuRameshMahender 25.61
7   215  RajaRajuRickyShivVishnuRameshMahenderLious 29.39
8   255  RajaRajuRickyShivVishnuRameshMahenderLiousSalman 32.37
9   285  RajaRajuRickyShivVishnuRameshMahenderLiousSalm… 37.17
10  336  RajaRajuRickyShivVishnuRameshMahenderLiousSalm… 41.27
11  382  RajaRajuRickyShivVishnuRameshMahenderLiousSalm… 44.92
```

Most of the measures can be easily made available with the help of `describe()` function.

```python
import pandas as pd
import numpy as np

d = {'Name': pd.Series(['Raja', 'Raju', 'Ricky', 'Shiv', 'Vishnu', 'Ramesh', 'Mahender',
                        'Lious', 'Salman', 'SRK', 'VV', 'MM']),
     'Age': pd.Series([25.00, 26, 25, 23, 30, 29, 23, 34, 40, 30, 51, 46.00]),
     'Rating': pd.Series([4.2320, 3.274, 3.98, 2.5628, 3.20, 4.600, 3.800, 3.780, 2.980, 4.8000, 4.1000, 3.65])}

df = pd.DataFrame(d)
print(df.describe())
```

**Output:**

![](OEBPS/images/p86.jpg)

---

# Q9: Explain reindexing.

**Ans:** Reindexing allows us to modify the index of one data frame by keeping the other data frame as reference. It can also be achieved by passing index and corresponding columns.

![](OEBPS/images/91.jpg)

**Output:**

![](OEBPS/images/p87.jpg)

---

# Q10: Explain bfill and ffill.

**Ans:** While reindexing `NaN` can be introduced. `bfill` and `ffill` are used to handle `NaN`.

![](OEBPS/images/92.jpg)

**Output:**

![](OEBPS/images/p87a.jpg)

*   **Bfill:** Fills the value from ahead value into the previous `NaN` value.
*   **FFill:** Fills the value from behind value into the missing `NaN` value.

```python
print(df2.reindex_like(df1, method='ffill'))
```

![](OEBPS/images/93.jpg)

---

# Q11: What all type of iterations are provided in pandas data frame?

**Ans:**

*   **iteritems():** To iterate over the (key, value) pairs.
*   **iterrows():** Iterate over the rows as (index, series) pairs.
*   **itertuples():** Iterate over the rows as namedtuples.

Consider the following data frame sample:

![](OEBPS/images/p88.jpg)

```python
for key, value in df.iteritems():
    print(key, value)
```

**Output:**

![](OEBPS/images/p88a.jpg)

```
Name: Age, dtype: int64
0     25
1     26
2     25
3     23
4     30
5     29
6     23
7     34
8     40
9     30
10    51
11    46
Name: Name, dtype: object
0     Raja
1     Raju
2     Ricky
3     Shiv
4     Vishnu
5     Ramesh
6     Mahender
7     Lious
8     Salman
9     SRK
10    VV
11    MM
Name: Rating, dtype: float64
0     4.23
1     3.24
2     3.98
3     2.56
4     3.20
5     4.60
6     3.80
7     3.78
8     2.98
9     4.80
10    4.10
11    3.65
```

```python
for row_index, row in df.iterrows():
    print(row_index, row)
```

```
0 Age 25
Name Raja
Rating 4.23
Name: 0, dtype: object
1 Age 26
Name Raju
Rating 3.24
Name: 1, dtype: object
2 Age 25
Name Ricky
Rating 3.98
Name: 2, dtype: object
3 Age 23
Name Shiv
Rating 2.56
Name: 3, dtype: object
4 Age 30
Name Vishnu
Rating 3.2
Name: 4, dtype: object
5 Age 29
Name Ramesh
Rating 4.6
Name: 5, dtype: object
6 Age 23
Name Mahender
Rating 3.8
Name: 6, dtype: object
7 Age 34
Name Lious
Rating 3.78
Name: 7, dtype: object
8 Age 40
Name Salman
Rating 2.98
Name: 8, dtype: object
9 Age 30
Name SRK
Rating 4.8
Name: 9, dtype: object
10 Age 51
Name VV
Rating 4.1
Name: 10, dtype: object
11 Age 46
Name MM
Rating 3.65
Name: 11, dtype: object
```

```python
for row in df.itertuples():
    print(row)
```

**Output:**

```
Pandas(Index=0, Age=25, Name='Raja', Rating=4.23)
Pandas(Index=1, Age=26, Name='Raju', Rating=3.24)
Pandas(Index=2, Age=25, Name='Ricky', Rating=3.98)
Pandas(Index=3, Age=23, Name='Shiv', Rating=2.56)
Pandas(Index=4, Age=30, Name='Vishnu', Rating=3.2)
Pandas(Index=5, Age=29, Name='Ramesh', Rating=4.6)
Pandas(Index=6, Age=23, Name='Mahender', Rating=3.8)
Pandas(Index=7, Age=34, Name='Lious', Rating=3.78)
Pandas(Index=8, Age=40, Name='Salman', Rating=2.98)
Pandas(Index=9, Age=30, Name='SRK', Rating=4.8)
Pandas(Index=10, Age=51, Name='VV', Rating=4.1)
Pandas(Index=11, Age=46, Name='MM', Rating=3.65)
```

---

# Q12: Explain how sorting is supported in pandas?

**Ans:**

*   **sort_index:** Allows sorting on index (row) or column wise.
*   **sort_values:** Allows sorting on values.

Consider the following data frame:

![](OEBPS/images/p91.jpg)

```python
sorted_df = unsorted_df.sort_values(by='col1')
print(sorted_df)
```

![](OEBPS/images/94.jpg)

```python
sorted_df = unsorted_df.sort_index(axis=1)
print(sorted_df)
```

![](OEBPS/images/95.jpg)

```python
sorted_df = unsorted_df.sort_index()
print(sorted_df)
```

![](OEBPS/images/96.jpg)

```python
sorted_df = unsorted_df.sort_index(ascending=False)
print(sorted_df)
```

![](OEBPS/images/p93.jpg)

---

# Q13: How to override default reload option in pandas?

**Ans:**

![](OEBPS/images/97.jpg)

---

# Q14: Explain various slicing options available with pandas?

**Ans:** Pandas supports the following slicing:

*   **.loc()** Label based
*   **.iloc()** Integer based
*   **.ix()** Both Label and Integer based

Consider the following data frame:

![](OEBPS/images/98.jpg) ![](OEBPS/images/99.jpg) ![](OEBPS/images/100.jpg) ![](OEBPS/images/101.jpg)

**Output:**

![](OEBPS/images/102.jpg) ![](OEBPS/images/103.jpg) ![](OEBPS/images/104.jpg) ![](OEBPS/images/105.jpg) ![](OEBPS/images/106.jpg)

---

# Q15: Explain advanced statistics with pandas.

**Ans:** Pandas support peak to peak, percentage change, covariance, and correlation on different series in data frame.

![](OEBPS/images/107.jpg)

**Output**

Data frame

![](OEBPS/images/p95.jpg)

**Pct change**

![](OEBPS/images/p96a.jpg)

**Covariance:**

![](OEBPS/images/p96b.jpg)

**Correlation:**

![](OEBPS/images/p96c.jpg)

---

# Q16: Explain rolling function.

**Ans:** Rolling function allows us to define window size and perform various operations w.r.t. the window.
