
along with values for the 25th, 50th, and 75th percentiles. The output of Listing 3.1 is here:

| January | February | March |
| --- | --- | --- |
| apples | 10 | 30 | 20 |
| oranges | 50 | 40 | 60 |
| beer | 1000 | 2000 | 3000 |
| count | January | February | March |
| | 3.000000 | 3.000000 | 3.000000 |
| mean | 353.333333 | 690.000000 | 1026.666667 |
| std | 560.386771 | 1134.504297 | 1709.073823 |
| min | 10.000000 | 30.000000 | 20.000000 |
| 25% | 30.000000 | 35.000000 | 40.000000 |
| 50% | 50.000000 | 40.000000 | 60.000000 |
| 75% | 525.000000 | 1020.000000 | 1530.000000 |
| max | 1000.000000 | 2000.000000 | 3000.000000 |

## PANDAS NUMERIC DATAFRAMES

Listing 3.2 displays the contents of pandas-numeric-df.py that illustrates how to define a Pandas DataFrame whose rows and columns are numbers (but the column labels are characters).

> LISTING 3.2: pandas-numeric-df.py

```python
import pandas as pd
```

```python
df1 = pd.DataFrame(np.random.randn(10, 4), columns=['A', 'B', 'C', 'D'])
```

```python
df2 = pd.DataFrame(np.random.randn(7, 3), columns=['A', 'B', 'C'])
```

```python
df3 = df1 + df2
```

The essence of Listing 3.2 involves initializing the DataFrames df1 and df2, and then defining the DataFrame df3 as the sum of df1 and df2. The output from Listing 3.2 is here:

| | A | B | C | D |
| --- | --- | --- | --- | --- |
| 0 | 0.0457 | -0.0141 | 1.3809 | NaN |
| 1 | -0.9555 | -1.5010 | 0.0372 | NaN |
| 2 | -0.6627 | 1.5348 | -0.8599 | NaN |
| 3 | -2.2459 | 1.2373 | -0.1337 | NaN |
| 4 | 1.1415 | 1.9517 | -2.3204 | NaN |
| 5 | -0.0499 | -1.6497 | -1.0846 | NaN |
| 6 | -1.0476 | -0.7486 | -0.8055 | NaN |
| 7 | NaN | NaN | NaN | NaN |
| 8 | NaN | NaN | NaN | NaN |
| 9 | NaN | NaN | NaN | NaN |

Keep in mind that the default behavior for operations involving a DataFrame and Series is to align the DataFrame columns; this results in a row-wise output. Here is a simple illustration:

```python
names = pd.Series(['SF', 'San Jose', 'Sacramento'])
sizes = pd.Series([852469, 1015785, 485199])

df = pd.DataFrame({'Cities': names, 'Size': sizes})
df = pd.DataFrame({'City name': names, 'sizes': sizes})

print(df)
```

The output of the preceding code block is here:

| | City name | sizes |
| --- | --- | --- |
| 0 | SF | 852469 |
| 1 | San Jose | 1015785 |
| 2 | Sacramento | 485199 |

## PANDAS BOOLEAN DATAFRAMES

Pandas supports Boolean operations on DataFrames, such as the logical or, the logical and, and the logical negation of a pair of DataFrames. Listing 3.3 displays the contents of pandas-boolean-df.py that illustrates how to define a Pandas DataFrame whose rows and columns are Boolean values.

# LISTING 3.3: pandas-boolean-df.py

```python
import pandas as pd

df1 = pd.DataFrame({'a' : [1, 0, 1], 'b' : [0, 1, 1]}, dtype=bool)
df2 = pd.DataFrame({'a' : [0, 1, 1], 'b' : [1, 1, 0]}, dtype=bool)

print("df1 & df2")
print(df1 & df2)

print("df1 | df2")
print(df1 | df2)

print("df1 ^ df2")
print(df1 ^ df2)
```

Listing 3.3 initializes the DataFrames df1 and df2, and then computes df1 & df2, df1 | df2, df1 ^ df2, which represent the logical AND, the logical OR, and the logical negation, respectively, of df1 and df2. The output from launching the code in Listing 3.3 is here:

| | a | b |
| --- | --- | --- |
| 0 | False | False |
| 1 | False | True |
| 2 | False | False |

| | df1 | df2: |
| --- | --- | --- |
| 0 | True | True |
| 1 | True | True |
| 2 | True | True |

| | df1 | df2: |
| --- | --- | --- |
| 0 | True | True |
| 1 | True | False |
| 2 | False | True |

## Transposing a DataFrame

The T attribute (as well as the transpose function) enables you to generate the transpose of a DataFrame, similar to a NumPy array. For example, the following code snippet defines df1 and then displays the transpose of df1:

```python
df1 = pd.DataFrame({'a' : [1, 0, 1], 'b' : [0, 1, 1]}, dtype=int)
print("df1.T:")
print(df1.T)
```

The output is:

| | 0 | 1 | 2 |
| --- | --- | --- | --- |
| a | 1 | 0 | 1 |
| b | 0 | 1 | 1 |

The following code snippet defines df1 and df2 and then displays their sum:

```python
df1 = pd.DataFrame({'a' : [1, 0, 1], 'b' : [0, 1, 1]}, dtype=int)
df2 = pd.DataFrame({'a' : [3, 3, 3], 'b' : [5, 5, 5]}, dtype=int)

print("df1 + df2")
print(df1 + df2)
```

The output is:

| | a | b |
| --- | --- | --- |
| 0 | 4 | 5 |
| 1 | 3 | 6 |
| 2 | 4 | 6 |

## PANDAS DATAFRAMES AND RANDOM NUMBERS

Listing 3.4 displays the contents of pandas-random-df.py that illustrates how to create a Pandas DataFrame with random numbers.

# LISTING 3.4: pandas-random-df.py

```python
import pandas as pd
import numpy as np

df = pd.DataFrame(np.random.randint(1, 5, size=(5, 2)), columns=['a', 'b'])
df = df.agg(['sum', 'mean'])

print("Contents of dataframe:")
print(df)
```

Listing 3.4 defines the Pandas df that consists of 5 rows and 2 columns of random integers between 1 and 5. Notice that the columns of df are labeled "a" and "b". In addition, the next code snippet adds rows consisting of the sum and the mean of both columns. The output of Listing 3.4 is:

| | a | b |
| --- | --- | --- |
| 0 | 1.0 | 2.0 |
| 1 | 1.0 | 1.0 |
| 2 | 4.0 | 3.0 |
| 3 | 3.0 | 1.0 |
| 4 | 1.0 | 2.0 |
| sum | 10.0 | 9.0 |
| mean | 2.0 | 1.8 |

## COMBINING PANDAS DATRAMES (1)

Listing 3.5 displays the contents of pandas-combine-df.py that illustrates how to combine DataFrames.

# LISTING 3.5: pandas-combine-df.py

```python
import pandas as pd
import numpy as np

df = pd.DataFrame({'foo1' : np.random.randn(5),
                   'foo2' : np.random.randn(5)})

print("contents of df:")
print(df)

print("contents of foo1:")
print(df.foo1)

print("contents of foo2:")
print(df.foo2)
```

Listing 3.5 defines the Pandas df that consists of 5 rows and 2 columns (labeled "foo1" and "foo2") of random real numbers between 0 and 5. The next portion of Listing 3.5 displays the contents of df and foo1. The output of Listing 3.5 is here:

```text
contents of df:
foo1           foo2
0  0.274680 -0.848669
1  0.399771 -0.814679
2  0.454443 -0.363392
3  0.473753  0.550849
4 -0.211783 -0.015014
contents of foo1:
0  0.256773
1  1.204322
2  1.040515
3  -0.518414
4  0.634141
Name: foo1, dtype: float64
contents of foo2:
0  -2.506550
1  -0.896516
2  -0.222393
3  0.934574
4  0.527033
```

## COMBINING PANDAS DATRAMES (2)

Pandas supports the "concat" method in DataFrames in order to concatenate DataFrames. Listing 3.6 displays the contents of weather-data.py.

```python
import pandas as pd

can_weather = pd.DataFrame({
    "city": ["Vancouver","Toronto","Montreal"],
    "temperature": [72,65,50],
    "humidity": [40,20,25]
})

us_weather = pd.DataFrame({
    "city": ["SF","Chicago","LA"],
    "temperature": [60,40,85],
    "humidity": [35,15,55]
})

df = pd.concat([can_weather, us_weather])
print(df)
```

The output of the preceding code block is here:

| | city | temperature | humidity |
| --- | --- | --- | --- |
| 0 | Vancouver | 72 | 40 |
| 1 | Toronto | 65 | 20 |
| 2 | Montreal | 50 | 25 |
| 3 | SF | 60 | 35 |
| 4 | Chicago | 40 | 15 |
| 5 | LA | 85 | 55 |

## DATA MANIPULATION WITH PANDAS DATRAMES (1)

As a simple example, suppose that we have a two-person company that keeps track of income and expenses on a quarterly basis, and we want to calculate the profit/loss for quarter, and also the overall profit/loss.

Listing 3.7 displays the contents of pandas-quarterly-df.py which illustrates how to define a Pandas DataFrame consisting of income-related values.

# LISTING 3.7: pandas-quarterly-df.py

```python
import pandas as pd

summary = {
    'Quarter': ['Q1', 'Q2', 'Q3', 'Q4'],
    'Cost': [23500, 34000, 57000, 32000],
    'Revenue': [40000, 40000, 40000, 40000]
}

df = pd.DataFrame(summary)

print("Entire Dataset:\n", df)
print("Quarter:\n", df.Quarter)
print("Cost:\n", df.Cost)
print("Revenue:\n", df.Revenue)
```

Listing 3.7 defines the variable summary that contains hardcoded quarterly information about cost and revenue for our two-person company. In general these hard-coded values would be replaced by data from another source (such as a CSV file), so think of this code sample as a simple way to illustrate some of the functionality that is available in Pandas DataFrames.

The variable df is a Pandas DataFrame based on the data in the summary variable. The three print statements display the quarters, the cost, and the revenue.
