

比列表上的速度快数量级。在一个大数据世界中，应用程序可能需要对海量基于数组的数据进行大量处理，这种性能优势可能至关重要。根据 libraries.io 的数据，超过 450 个 Python 库依赖 NumPy。许多流行的数据科学库（如 Pandas、SciPy（科学 Python）和 Keras（用于深度学习））都是基于 NumPy 构建的或依赖于 NumPy。

在本章中，我们将探索数组的基本功能。列表可以有多个维度。您通常使用嵌套循环或带有多个 for 子句的列表推导式来处理多维列表。NumPy 的一个优势是“面向数组的编程”，它使用带有内部迭代的函数式编程风格，使数组操作简洁直观，消除显式编程循环的外部迭代中可能出现的那类错误。

在本章的“数据科学简介”部分，我们将开始多部分介绍 pandas 库，您将在许多数据科学案例研究章节中使用它。大数据应用通常比 NumPy 的数组需要更灵活的集合——这些集合支持混合数据类型、自定义索引、缺失数据、结构不一致的数据以及需要操作成适合您所使用的数据库和数据分析包的形式的数据。我们将介绍类似于数组的 pandas 一维 Series 和二维 DataFrame，并开始演示它们的强大功能。读完本章后，您将了解四种类似于数组的集合——列表、数组、Series 和 DataFrame。我们将在“深度学习”章节中添加第五种——张量。

## 7.2 从现有数据创建数组

NumPy 文档建议将 numpy 模块导入为 np，以便您可以使用 "np." 访问其成员：

```
In [1]: import numpy as np
```

numpy 模块提供了用于创建数组的各种函数。在此我们使用 array 函数，它接收一个数组或其他元素集合作为参数，并返回包含该参数元素的新数组。让我们传递一个列表：

单击此处查看代码图像

```
In [2]: numbers = np.array([2, 3, 5, 7, 11])
```

`array` 函数将其参数的内容复制到 `array` 中。让我们查看函数 `array` 返回的对象类型并显示其内容：

单击此处查看代码图像

```
In [3]: type(numbers)
Out[3]: numpy.ndarray

In [4]: numbers
Out[4]: array([ 2,  3,  5,  7, 11])
```

请注意，`type` 是 `numpy.ndarray`，但所有 `array` 都输出为“array”。在输出 `array` 时，NumPy 用逗号和空格将每个值与下一个值分隔开，并使用相同的字段宽度 _右对齐_ 所有值。它根据占用 _最多_ 字符位置的值来确定字段宽度。在此例中，值 11 占据两个字符位置，因此所有值都按两个字符字段格式化。这就是为什么在 [ 和 2 之间有一个前导空格。

### 多维参数

`array` 函数复制其参数的维度。让我们从一个两行三列的列表创建一个 `array`：

单击此处查看代码图像

```
In [5]: np.array([[1, 2, 3], [4, 5, 6]])
Out[5]:
array([[1, 2, 3],
       [4, 5, 6]])
```

NumPy 根据数组的维度数自动格式化 `array`，对齐每行中的列。

## 7.3 数组属性

`array` 对象提供 **属性**，使您能够发现其结构和内容的信息。在本节中，我们将使用以下 `array`：

单击此处查看代码图像

```
In [1]: import numpy as np

In [2]: integers = np.array([[1, 2, 3], [4, 5, 6]])

In [3]: integers
Out[3]:
array([[1, 2, 3],
       [4, 5, 6]])

In [4]: floats = np.array([0.0, 0.1, 0.2, 0.3, 0.4])

In [5]: floats
Out[5]: array([0. , 0.1, 0.2, 0.3, 0.4])
```

NumPy 不会在浮点值的小数点右侧显示尾随 0。

### 确定数组的元素类型

array 函数根据其参数的元素确定数组的元素类型。您可以使用数组的 dtype 属性来检查元素类型：

单击此处查看代码图像

```
In [6]: integers.dtype
Out[6]: dtype('int64') # int32 on some platforms

In [7]: floats.dtype
Out[7]: dtype('float64')
```

如您将在下一节中看到，各种数组创建函数接收 dtype 关键字参数，以便您可以指定数组的元素类型。

出于性能原因，NumPy 使用 C 编程语言编写并使用 C 的数据类型。默认情况下，NumPy 将整数存储为 NumPy 类型 int64 值（对应于 C 中的 64 位（8 字节）整数），并将浮点数存储为 NumPy 类型 float64 值（对应于 C 中的 64 位（8 字节）浮点数）。在我们的示例中，您最常见的类型是 int64、float64、bool（用于布尔值）以及用于非数值数据（如字符串）的 object。支持的类型完整列表位于 https://docs.scipy.org/doc/numpy/user/basics.types.html。

### 确定数组的维度

属性 `ndim` 包含 `array` 的维度数，属性 `shape` 包含指定 `array` 维度的 `tuple`：

单击此处查看代码图像

```
In [8]: integers.ndim
Out[8]: 2

In [9]: floats.ndim
Out[9]: 1

In [10]: integers.shape
Out[10]: (2, 3)

In [11]: floats.shape
Out[11]: (5,)
```

在此，`integers` 有 2 行 3 列（6 个元素），`floats` 是一维的，因此片段 [11] 显示一个包含逗号的一元素元组，其中包含 `floats` 的元素数量（5）。

### 确定 `array` 的元素数量和元素大小

您可以使用属性 `size` 查看 `array` 的元素总数，并使用 `itemsize` 查看存储每个元素所需的字节数：

单击此处查看代码图像

```
In [12]: integers.size
Out[12]: 6

In [13]: integers.itemsize # 4 if C compiler uses 32-bit ints
Out[13]: 8

In [14]: floats.size
Out[14]: 5

In [15]: floats.itemsize
Out[15]: 8
```

请注意，`integers` 的 `size` 是 `shape` 元组值的乘积——每行三个元素的两行，总共六个元素。在每种情况下，`itemsize` 都是 8，因为 `integers` 包含 `int64` 值，而 `floats` 包含 `float64` 值，每个值占用 8 字节。

### 遍历多维数组的元素

您通常将使用简洁的函数式编程技术来操作数组。但是，由于数组是可迭代的，如果您愿意，可以使用外部迭代：

单击此处查看代码图像

```
In [16]: for row in integers:
  ...:     for column in row:
  ...:         print(column, end=' ')
  ...:     print()
  ...:
1 2 3
4 5 6
```

您可以通过使用其 flat 属性，像遍历一维数组一样遍历多维数组：

单击此处查看代码图像

```
In [17]: for i in integers.flat:
  ...:     print(i, end=' ')
  ...:
1 2 3 4 5 6
```

## 7.4 用特定值填充数组

NumPy 提供了 zeros、ones 和 full 函数，分别用于创建包含 0、1 或指定值的数组。默认情况下，zeros 和 ones 创建包含 float64 值的数组。我们稍后将展示如何自定义元素类型。这些函数的第一个参数必须是整数或整数元组，用于指定所需的维度。对于整数，每个函数都返回一个带有指定元素数量的一维数组：

单击此处查看代码图像

```
In [1]: import numpy as np

In [2]: np.zeros(5)
Out[2]: array([ 0.,  0.,  0.,  0.,  0.])
```

对于整数元组，这些函数返回带有指定维度的多维数组。您可以使用 zeros 和 ones 函数的 dtype 关键字参数来指定数组的元素类型：

单击此处查看代码图像

```
In [3]: np.ones((2, 4), dtype=int)
Out[3]:
array([[1, 1, 1, 1],
       [1, 1, 1, 1]])
```

full 返回的数组包含具有第二个参数的值和类型的元素：

单击此处查看代码图像

```
In [4]: np.full((3, 5), 13)
Out[4]:
array([[13, 13, 13, 13, 13],
       [13, 13, 13, 13, 13],
       [13, 13, 13, 13, 13]])
```

## 7.5 从范围创建数组

NumPy 提供了用于从范围创建数组的优化函数。我们专注于简单的等间距整数和浮点范围，但 NumPy 还支持非线性范围。¹

¹ https://docs.scipy.org/doc/numpy/reference/routines.array-creation.html.

### 使用 arange 创建整数范围

让我们使用 NumPy 的 arange 函数来创建整数范围——类似于使用内置函数 range。在每种情况下，arange 首先确定结果数组的元素数量，分配内存，然后将指定的值范围存储在数组中：

单击此处查看代码图像

```
In [1]: import numpy as np
```

