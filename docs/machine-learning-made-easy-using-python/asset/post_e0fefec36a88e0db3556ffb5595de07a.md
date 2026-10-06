
# 12 DATA OPERATIONS

- NumPy operations
- Pandas operations
- Cleaning data

![](img/d75fea3635f5553f1cb0585b399b1b4b_88_0.png)

# 12 DATA ANALYSIS

Python handles data of various formats mainly through the two libraries, Pandas and Numpy. We have already seen the important features of these two libraries in the previous chapters. In this chapter we will see some basic examples from each of the libraries on how to operate on data and perform different tasks like cleaning the data, analytics, etc.

## NumPy Operations

To start working with NumPy, we need to import numpy to create NumPy arrays.

```
In [ ]: import numpy
```

Let's create an array, using the array() function and print it.

```
In [2]: import numpy
ar = numpy.array([1,5,7])
print(ar)

[1 5 7]
```

ar is a 1-Dimensional array, we can also create a 2-Dimensional array by creating one or more 1-Dimensional array inside of another array

```
In [8]: import numpy
ar = numpy.array([[1,5,7],[2,3,9]])
print(ar)

[[1 5 7]
[2 3 9]]
```

![](img/d75fea3635f5553f1cb0585b399b1b4b_89_0.png)

We can specify the dimension of an array during creation using the ndmin parameter

```
In [10]: import numpy
ar = numpy.array([1,5,7], ndmin = 2 )
print(ar)

[[1 5 7]]
```

Although we passed a 1-Dimensional array, it became a 2-Dimensional array because of the specification of the dimensions of the array in the ndmin parameter.

We created an array with integers so, let's create arrays with strings and floats using the dtype parameter with the same values

```
In [11]: import numpy
ar_str = numpy.array([1,5,7], dtype = str )
ar_flt = numpy.array([1,5,7], dtype = float )
print(ar_str)
print(ar_flt)

['1' '5' '7']
[1. 5. 7. ]
```

ar_str is an array of string literals and ar_flt is an array of floats. We can also change these numbers to complex numbers the same way using complex as dtype

```
In [13]: import numpy
ar_str = numpy.array([1,5,7], dtype = str )
ar_flt = numpy.array([1,5,7], dtype = float ) evenar_cmx = numpy.array([1,5,7], dtype = complex )
print(ar_str)
print(ar_flt)
print(ar_cmx)

['1' '5' '7']
[1. 5. 7.]
[1.+0.j 5.+0.j 7.+0.j]
```

ar_str, ar_flt and ar_cmx are arrays created with same data, but with different data types as strings, floats and complex numbers respectively.

## Pandas Operations

Pandas handles data through Series, Data Frame, and Panel. We will learn to create each of these.

### Pandas Series

We already know what Pandas Series is. A pandas Series can be created using the Series() function so, let's import pandas and create series.

```
In [14]: import pandas
sr = pandas.Series([1,5,7])
print(sr)

0    1
1    5
2    7
dtype: int64
```

As you see our data indexed form 0 to 2 with the data type printed as integer, we can specify our own indexes in the index parameter

```
In [16]: import pandas
sr = pandas.Series([1,5,7], index = ['A','B','C'])
print(sr)

A    1
B    5
C    7
dtype: int64
```

Like ndarrays, we can also specify the data type in pandas series using dtype parameter during series creation

```
In [18]: import pandas
sr = pandas.Series([1,5,7], dtype = complex )
print(sr)

0    1.000000+0.000000j
1    5.000000+0.000000j
2    7.000000+0.000000j
dtype: complex128
```

## DATA OPERATIONS

We can use a ndarray to create a pandas series

```
In [19]: import numpy
import pandas
_ar = numpy.array([1,5,7])
sr = pandas.Series(data = ar, copy = True)
# is as same as sr = pandas.Series(ar, copy = True)
print(sr)

0    1
1    5
2    7
dtype: int64
```

We passed the ndarray as the data for the series, the data parameter isn't necessary, also used the copy parameter to create a copy of the data. If you want to get the data without indexes use the values function

```
In [21]: import numpy
import pandas
ar = numpy.array([1,5,7])
sr = pandas.Series(ar)
print(sr.values)

[1 5 7]
```

You can print a more detailed version of the above using the array function

![](img/d75fea3635f5553f1cb0585b399b1b4b_92_0.png)

Also note the difference in array function between NumPy and Pandas.

## Data Frames

Pandas Data Frames aligns data in tabular fashion. A pandas DataFrame can be created using the DataFrame() function. Dictionary keys are the columns and their values are the content of the rows. We can also use index parameter here

```
In [23]: import pandas
df = pandas.DataFrame({"Product":['Cookies','Biscuits'], "Sales":[157,227]})
Product   Sales
Cookies     157
Biscuits    227
```

We can define the columns separately using ndarrays

```
In [24]: import pandas
df = pandas.DataFrame([[157,227]], columns=['Cookies','Biscuits'], index=[0,1])
# Actually
0  Cookies     157
1  Biscuits    227
```

The data is stored in the ndarray and the columns are defined in the DataFrame's parameter to act as the data. We can add columns to the DataFrame using the syntax

```
In [44]: import pandas
df = pandas.DataFrame([[1,3],[6,2]], index=['A','B'], columns=['C1','C2'])
df['C3'] = df['C1']*5
print(df)

   C1  C2  C3
A   1   3   5
B   6   2  30
```

We can delete columns from the DataFrame

```
In [45]: import pandas
df = pandas.DataFrame([[1,3],[6,2]], index=['A','B'], columns=['C1','C2','C3'])
del df['C3']
print(df)

   C1  C2
A   1   3
B   6   2
```

We can print a column of the DataFrame using the syntax

```
In [46]: import pandas
df = pandas.DataFrame([[1,3],[6,2]], index=['A','B'], columns=['C1','C2'])
print(df['C1'])

A    1
B    6
Name: C1, dtype: int32
```

## Slicing Syntax

To get a single element from a ndarray or pandas series or pandas dataframes we need to use the slice syntax array[start:end:step(optional)]. Let's extract some elements from the arrays we have created so far

```
In [59]: import numpy as np
ar1 = np.array([[1, 5]])
ar2 = np.array([[1, 3], [5, 2]])
ar3 = np.array([[1, 3], [5, 2], [2, 4], [4, 6]])

# Slicing 1-Dimensional array
print(ar1[0])

# Slicing 2-Dimensional array
print(ar2[0,1])

# Slicing 3-Dimensional array
print(ar3[1,0,1])
```

We use a comma to slice further in 2 or more dimensional arrays, the following figure will help you understand the slicing of the 3-Dimensional array better

```
ar3[]

```
[[[1, 3],
[5, 2]],
[[2, 4],
[4, 6]]]
```

![](img/d75fea3635f5553f1cb0585b399b1b4b_95_0.png)

ar3[1]

```
[[[1, 3], [5, 2]], [[2, 4], [4, 6]]]
```

First Slice

ar3[1,0]

```
[[[1, 3], [5, 2]], [[2, 4], [4, 6]]]
```

Second Slice

ar3[1,0,1]

```
[[[1, 3], [5, 2]], [[2, 4], [4, 6]]]
```

ar3[1,0,1]

```
4
```

Final Slice

Slicing may seem a bit tough for beginners due to the dimensions, that’s why I created the figure to help you understand slicing better. If you are confident try solving the slicing questions in the Exercise

To get an element from a pandas series, we use the series[explicit_index or implicit_index] syntax

```
In [4]: import pandas as pan
sr = pan.Series([1, 3, 5], index=['a','b','c'])

print(sr['a']) #Implicit indexing
print(sr[0])    #Explicit indexing
```

If you have indexes like numbers like these

```
In [6]: import pandas as pan
sr = pan.Series([1, 3, 5], index = [2,4,6])
```

If you want the second element using the implicit index [indexing defined in index parameter] use series.loc<label> syntax and using the explicit indexing [ 0,1,2,... ] use series.iloc<index> syntax syntax

```
In [7]: import pandas as pan
sr = pan.Series([1, 3, 5], index=[2,4,6])

print(sr.loc[4])
print(sr.iloc[1])
```

We can modify or delete the elements using slicing

```
In [9]: import pandas as pan
sr = pan.Series([1, 3, 5], index=[2,4,6])

sr[4] = 7
print(sr)

del sr[6]
print(sr)

2    1
4    7
6    5
dtype: int64
2    1
4    7
dtype: int64
```
