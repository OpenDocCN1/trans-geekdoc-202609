

# 12 数据操作

- NumPy 操作
- Pandas 操作
- 数据清洗

![](img/d75fea3635f5553f1cb0585b399b1b4b_88_0.png)

# 12 数据分析

Python 主要通过 Pandas 和 Numpy 这两个库来处理各种格式的数据。我们在之前的章节中已经学习了这两个库的重要特性。在本章中，我们将看到每个库的某些基础示例，介绍如何操作数据以及执行不同的任务，如数据清洗、分析等。

## NumPy 操作

要开始使用 NumPy，我们需要导入 numpy 来创建 NumPy 数组（arrays）。

```
In [ ]: import numpy
```

让我们使用 array() 函数创建一个数组并将其打印出来。

```
In [2]: import numpy
ar = numpy.array([1,5,7])
print(ar)

[1 5 7]
```

ar 是一个 1 维数组，我们也可以在另一个数组内部创建一个或多个 1 维数组来创建一个 2 维数组。

```
In [8]: import numpy
ar = numpy.array([[1,5,7],[2,3,9]])
print(ar)

[[1 5 7]
[2 3 9]]
```

![](img/d75fea3635f5553f1cb0585b399b1b4b_89_0.png)

我们可以在创建数组时使用 ndmin 参数来指定数组的维度。

```
In [10]: import numpy
ar = numpy.array([1,5,7], ndmin = 2 )
print(ar)

[[1 5 7]]
```

虽然我们传递了一个 1 维数组，但由于 ndmin 参数指定了数组的维度，它变成了一个 2 维数组。

我们创建了一个整数数组，所以让我们使用 dtype 参数使用相同的值创建字符串数组和浮点数数组。

```
In [11]: import numpy
ar_str = numpy.array([1,5,7], dtype = str )
ar_flt = numpy.array([1,5,7], dtype = float )
print(ar_str)
print(ar_flt)

['1' '5' '7']
[1. 5. 7. ]
```

ar_str 是字符串字面量数组，ar_flt 是浮点数数组。我们也可以同样使用 complex 作为 dtype 将这些数字改为复数。

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

ar_str, ar_flt 和 ar_cmx 是用相同数据创建的数组，但数据类型分别为字符串、浮点数和复数。

## Pandas 操作

Pandas 通过 Series、Data Frame 和 Panel 处理数据。我们将学习创建每一种对象。

### Pandas Series

我们已经知道 Pandas Series 是什么。可以使用 Series() 函数创建 pandas Series，所以让我们导入 pandas 创建 series。

```
In [14]: import pandas
sr = pandas.Series([1,5,7])
print(sr)

0    1
1    5
2    7
dtype: int64
```

如你所见，我们的数据索引从 0 到 2，数据类型为整数，我们可以在 index 参数中指定自己的索引。

```
In [16]: import pandas
sr = pandas.Series([1,5,7], index = ['A','B','C'])
print(sr)

A    1
B    5
C    7
dtype: int64
```

就像 ndarrays 一，我们也可以在创建 series 时使用 dtype 参数指定 pandas series 的数据类型。

```
In [18]: import pandas
sr = pandas.Series([1,5,7], dtype = complex )
print(sr)

0    1.0+0j
1    5.0+0j
2    7.0+0j
dtype: complex
```

## 数据操作

我们可以使用 ndarray 创建 pandas series。

```
In [19]: import numpy
import pandas
ar = numpy.array([1,5,7])
sr = pandas.Series(ar, copy = True)
print(sr)

0    1
1    5
2    7
dtype: int64
```

传递 ndarray 作为 series 的数据，data 参数是必需的，还使用了 copy 参数创建数据的副本。如果你想获取没有索引的数据，使用 values 函数。

```
In [21]: import numpy
import pandas
ar = numpy.array([1,5,7])
sr = pandas.Series(ar)
print(sr.values)

[1 5 7]
```

可以使用 array 函数打印上面的更详细版本 ![](img/d75fea3635f5553f1cb0585b399b1b4b_92_0.png)。

注意 NumPy 和 Pandas 之间的 array 函数差异。Pandas Data Frames 以表格形式对齐数据。可以使用 DataFrame() 函数创建 pandas DataFrame。字典的键是列，值是行内容。我们在这里也可以使用 index 参数。

```
In [23]: import pandas
df = pandas.DataFrame({"Product":['Cookies','Biscuits'], "Sales":[157,227]})
Product   Sales
Cookies     157
Biscuits    227
```

可以使用 ndarrays 分别定义列。

```
In [24]: import pandas
df = pandas.DataFrame([[157,227]], columns=['Cookies','Biscuits'], index=[0,1])
0  Cookies     157
1  Biscuits    227
```

数据存储在 ndarray 中，列在 DataFrame 的参数中定义。我们可以使用以下语法向 DataFrame 添加列。

```
In [44]: import pandas
df = pandas.DataFrame([[1,3],[6,2]], index=['A','B'], columns=['C1','C2'])
df['C3'] = df['C1']*5
print(df)

   C1  C2  C3
A   1   3   5
B   6   2  30
```

我们可以从 DataFrame 中删除列。

```
In [45]: import pandas
df = pandas.DataFrame([[1,3],[6,2]], index=['A','B'], columns=['C1','C2','C3'])
del df['C3']
print(df)

   C1  C2
A   1   3
B   6   2
```

我们可以使用语法打印 DataFrame 的一列。

```
In [46]: import pandas
df = pandas.DataFrame([[1,3],[6,2]], index=['A','B'], columns=['C1','C2'])
print(df['C1'])

A    1
B    6
Name: C1, dtype: int32
```

## 切片语法

要从 ndarray 或 pandas series 或 pandas dataframes 获取单个元素，我们需要使用切片语法 `array[start:end:step(optional)]`。让我们从目前为止创建的数组中提取一些元素。

```
In [59]: import numpy as np
ar1 = np.array([[1, 5]])
ar2 = np.array([[1, 3], [5, 2]])
ar3 = np.array([[1, 3], [5, 2], [2, 4], [4, 6]])

# 切片 1 维数组
print(ar1[0])

# 切片 2 维数组
print(ar2[0,1])

# 切片 3 维数组
print(ar3[1,0,1])
```

在 2 维或更多维数组中使用逗号进一步切片，下面的图将帮助你更好地理解 3 维数组的切片。

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

第一切片

ar3[1,0]

```
[[[1, 3], [5, 2]], [[2, 4], [4, 6]]]
```

第二切片

ar3[1,0,1]

```
4
```

最终切片

