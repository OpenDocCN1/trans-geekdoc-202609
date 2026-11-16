

```python
In [2]: numbers = np.arange(1, 6)

In [3]: numbers
Out[3]: array([1, 2, 3, 4, 5])

In [4]: numbers * 2
Out[4]: array([ 2, 4, 6, 8, 10])

In [5]: numbers ** 3
Out[5]: array([ 1, 8, 27, 64, 125])

In [6]: numbers # numbers is unchanged by the arithmetic operators
Out[6]: array([1, 2, 3, 4, 5])
```

代码段 [6] 显示算术运算符没有修改 numbers。运算符 + 和 * 是 *可交换的*，因此代码段 [4] 也可以写成 2 * numbers。

增量赋值 *修改* 左操作数中的每个元素。

单击此处查看代码图像

```python
In [7]: numbers += 10

In [8]: numbers
Out[8]: array([11, 12, 13, 14, 15])
```

## 广播

通常，算术运算要求两个操作数为相同 *大小和形状* 的 *数组*。当一个操作数是单个值（称为 **标量**）时，NumPy 将执行逐元素计算，就好像标量是一个与另一个操作数形状相同的 *数组*，但其所有元素的值均为标量值。这称为 **广播**。代码段 [4]、[5] 和 [7] 均使用此功能。例如，代码段 [4] 等效于：

单击此处查看代码图像

```python
numbers * [2, 2, 2, 2, 2]
```

广播也可以应用于大小和形状不同的 *数组* 之间，从而实现一些简洁而强大的操作。我们将在本章后面介绍 NumPy 的通用函数时展示更多广播示例。

## 数组之间的算术运算

您可以对形状相同的 `arrays` 执行算术运算和增量赋值。让我们相乘下面创建的一维 `arrays numbers` 和 `numbers2`，它们各包含五个元素：

单击此处查看代码图像

```python
In [9]: numbers2 = np.linspace(1.1, 5.5, 5)

In [10]: numbers2
Out[10]: array([ 1.1, 2.2, 3.3, 4.4, 5.5])

In [11]: numbers * numbers2
Out[11]: array([ 12.1, 26.4, 42.9, 61.6, 82.5])
```

结果是一个新数组，由对每个操作数中的 `arrays element-wise` 相乘而成——11 * 1.1、12 * 2.2、13 * 3.3 等等。整数 `arrays` 与浮点数之间的算术运算结果为浮点数 `array`。

## 比较数组

您可以将 `arrays` 与单个值和其他 `arrays` 进行比较。比较按 `element-wise` 执行。此类比较将生成布尔值 `arrays`，其中每个元素的 `True` 或 `False` 值指示比较结果：

单击此处查看代码图像

```python
In [12]: numbers
Out[12]: array([11, 12, 13, 14, 15])

In [13]: numbers >= 13
Out[13]: array([False, False, True, True, True])

In [14]: numbers2
Out[14]: array([ 1.1, 2.2, 3.3, 4.4, 5.5])

In [15]: numbers2 < numbers
Out[15]: array([ True, True, True, True, True])

In [16]: numbers == numbers2
Out[16]: array([False, False, False, False, False])

In [17]: numbers == numbers
Out[17]: array([ True, True, True, True, True])
```

代码段 [13] 使用广播来确定 `numbers` 中的每个元素是否大于或等于 13。其余代码段比较每个 `array` 操作数的对应元素。

## 7.8 NumPy 计算方法

一个 `array` 拥有各种使用其内容进行计算的方法。默认情况下，这些方法忽略 `array` 的形状，并在计算中使用 *所有* 元素。例如，计算 `array` 的平均值时，会先求和其所有元素（不考虑形状），然后除以元素总数。您也可以对每个维度执行这些计算。例如，在二维数组中，您可以计算每行的平均值和每列的平均值。

考虑一个表示四名学生三次考试成绩的 `array`：

单击此处查看代码图像

```python
In [1]: import numpy as np

In [2]: grades = np.array(([87, 96, 70], [100, 87, 90],
   ...:
   ...: [94, 77, 90], [100, 81, 82]))
   ...:

In [3]: grades
Out[3]:
array([[ 87, 96, 70],
       [100, 87, 90],
       [ 94, 77, 90],
       [100, 81, 82]])
```

我们可以使用方法来计算 `sum`、`min`、`max`、`mean`、`std`（标准差）和 `var`（方差）——每个方法都是函数式编程风格的 *归约*：

单击此处查看代码图像

```python
In [4]: grades.sum()
Out[4]: 1054

In [5]: grades.min()
Out[5]: 70

In [6]: grades.max()
Out[6]: 100

In [7]: grades.mean()
Out[7]: 87.83333333333333
In [8]: grades.std()
Out[8]: 8.792357792739987
In [9]: grades.var()
Out[9]: 77.30555555555556
```

### 按行或列计算

许多计算方法可以在特定的数组维度上执行，这些维度称为数组的轴。这些方法接收一个 axis 关键字参数，用于指定计算中使用的维度，为您提供了一种在二维数组中按行或列进行计算的快速方法。

假设您想计算由 grades 的列表示的每次考试的平均成绩。指定 axis=0 将在每个列中的所有行值上执行计算：

单击此处查看代码图像

```python
In [10]: grades.mean(axis=0)
Out[10]: array([95.25, 85.25, 83. ])
```

上述 95.25 是第一列成绩（87、100、94 和 100）的平均值，85.25 是第二列成绩（96、87、77 和 81）的平均值，83 是第三列成绩（70、90、90 和 82）的平均值。同样，NumPy 不会在小数点右侧显示 ‘83. ’ 中的尾随 0。还要注意，它以相同的字段宽度显示所有元素值，这就是为什么 ‘83. ’ 后面跟有两个空格。

同样，指定 axis=1 将在每个单独行中的所有列值上执行计算。要计算每个学生所有考试的平均成绩，我们可以使用：

单击此处查看代码图像

```python
In [11]: grades.mean(axis=1)
Out[11]: array([84.33333333, 92.33333333, 87. , 87.66666667])
```

这会产生四个平均值——每行对应一个。因此，84.33333333 是第 0 行成绩（87、96 和 70）的平均值，其余平均值对应其余各行。

NumPy 数组拥有更多计算方法。有关完整列表，请参见

https://docs.scipy.org/doc/numpy/reference/arrays.ndarray.html

### 7.9 通用函数

NumPy 提供数十种独立的通用函数（或称为 ufuncs），用于执行各种逐元素操作。每个函数使用一个或两个数组或类数组（例如列表）参数来完成其任务。在对数组使用 + 和 * 等运算符时，会调用其中一些函数。每个函数都返回一个包含结果的新数组。

让我们创建一个数组，并使用 sqrt 通用函数计算其值的平方根：

单击此处查看代码图像

```python
In [1]: import numpy as np

In [2]: numbers = np.array([1, 4, 9, 16, 25, 36])

In [3]: np.sqrt(numbers)
Out[3]: array([1., 2., 3., 4., 5., 6.])
```

让我们使用 add 通用函数相加两个形状相同的数组：

单击此处查看代码图像

```python
In [4]: numbers2 = np.arange(1, 7) * 10

In [5]: numbers2
Out[5]: array([10, 20, 30, 40, 50, 60])

In [6]: np.add(numbers, numbers2)
Out[6]: array([11, 24, 39, 56, 75, 96])
```

表达式 np.add(numbers, numbers2) 等效于：

```python
numbers + numbers2
```

## 通用函数的广播

让我们使用 `multiply` 通用函数将 `numbers2` 的每个元素乘以标量值 5：

单击此处查看代码图像

```python
In [7]: np.multiply(numbers2, 5)
Out[7]: array([ 50, 100, 150, 200, 250, 300])
```

表达式 `np.multiply(numbers2, 5)` 等效于：

```python
numbers2 * 5
```

让我们将 `numbers2` 调整为 2 行 3 列的 `array`，然后将其值与一个包含三个元素的一维 `array` 相乘：

单击此处查看代码图像

```python
In [8]: numbers3 = numbers2.reshape(2, 3)

In [9]: numbers3
Out[9]:
array([[10, 20, 30,
       [40, 50, 60]])

In [10]: numbers4 = np.array([2, 4, 6])

In [11]: np.multiply(numbers3, numbers4)
Out[11]:
array([[ 20, 80, 180,
       [ 80, 200, 360]])
```

之所以可行，是因为 `numbers4` 的长度与 `numbers3` 的每一行相同，因此 NumPy 可以将 `numbers4` 视作以下 `array` 来应用乘法运算：

```python
array([[2, 4, 6],
       [2, 4, 6]])
```

如果通用函数接收两个不支持广播的形状不同的 `array`s，将发生 `ValueError`。您可以在以下网址查看广播规则：

