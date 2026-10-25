

## 4.3.2 Zeros

zeros() 函数将创建一个指定大小的新数组，内容填充为零值。传递给该函数的参数是一个数组或元组，用于指定要创建的数组每个维度的长度。下面的示例创建一个 3 x 5 的二维零数组。

```python
# create zero array
from numpy import zeros
a = zeros([3,5])
print(a)
```

Listing 4.5: 使用 zeros() 函数创建数组的示例。

运行示例将打印创建的零数组的内容。

```
[[ 0. 0. 0. 0. 0.]
 [ 0. 0. 0. 0. 0.]
 [ 0. 0. 0. 0. 0.]]
```

Listing 4.6: 使用 zeros() 函数创建数组的示例输出。

## 4.3.3 Ones

ones() 函数将创建一个指定大小的新数组，内容填充为一值。传递给该函数的参数是一个数组或元组，用于指定要创建的数组每个维度的长度。下面的示例创建一个 5 元素的一维数组。

```python
# create one array
from numpy import ones
a = ones([5])
print(a)
```

Listing 4.7: 使用 ones() 函数创建数组的示例。

运行示例将打印创建的 ones 数组的内容。

```
[ 1. 1. 1. 1. 1.]
```

Listing 4.8: 使用 ones() 函数创建数组的示例输出。

## 4.4 Combining Arrays

NumPy 提供了许多函数，可从现有数组创建新数组。让我们来看看你可能需要或遇到的两个最常用函数。

### 4.4.1 Vertical Stack

给定两个或多个现有数组，你可以使用 vstack() 函数将它们垂直堆叠。例如，给定两个一维数组，你可以通过垂直堆叠它们来创建一个包含两行的新二维数组。下面的示例演示了这一点。

```python
# create array with vstack
from numpy import array
from numpy import vstack
# create first array
a1 = array([1,2,3])
print(a1)
# create second array
a2 = array([4,5,6])
print(a2)
# vertical stack
a3 = vstack((a1, a2))
print(a3)
print(a3.shape)
```

Listing 4.9: 使用 vstack() 函数从其他数组创建数组的示例。

运行示例首先打印两个分别定义的一维数组。数组被垂直堆叠，生成一个新的 2 × 3 数组，其内容和形状将被打印。

```
[1 2 3]
[4 5 6]
[[1 2 3]
 [4 5 6]]
(2, 3)
```

Listing 4.10: 使用 vstack() 函数从其他数组创建数组的示例输出。

### 4.4.2 Horizontal Stack

给定两个或多个现有数组，你可以使用 hstack() 函数将它们水平堆叠。例如，给定两个一维数组，你可以创建一个新的一维数组或一行，其中第一个和第二个数组的列被连接。下面的示例演示了这一点。

```python
# create array with hstack
from numpy import array
from numpy import hstack
# create first array
a1 = array([1,2,3])
print(a1)
# create second array
a2 = array([4,5,6])
print(a2)
# create horizontal stack
a3 = hstack((a1, a2))
print(a3)
print(a3.shape)
```

Listing 4.11: 使用 hstack() 函数从其他数组创建数组的示例。

运行示例首先打印两个分别定义的一维数组。然后将数组水平堆叠，生成一个包含 6 个元素的新的一维数组，其内容和形状将被打印。

```
[1 2 3]
[4 5 6]
[1 2 3 4 5 6]
(6,)
```

Listing 4.12: 使用 hstack() 函数从其他数组创建数组的示例输出。

## 4.5 Extensions

本节列出了一些你可能希望探索的扩展教程的想法。

- 尝试以自己的大小或使用新数据创建数组的不同方式。
- 为创建数组的 3 个额外 NumPy 函数定位并开发示例。
- 为合并数组的 3 个额外 NumPy 函数定位并开发示例。

如果你探索了这些扩展中的任何一个，我很乐意了解。

## 4.6 Further Reading

如果你希望深入了解，本节提供了更多关于该主题的资源。

### 4.6.1 Books

- *Python数据分析*, 2017. http://amzn.to/2B1sfXi
- *优雅的SciPy*, 2017. http://amzn.to/2yujXnT
- *NumPy指南*, 2015. http://amzn.to/2j3kEzd

### 4.6.2 References

- NumPy 参考。https://docs.scipy.org/doc/numpy-1.13.0/reference/
- N维数组。https://docs.scipy.org/doc/numpy-1.13.0/reference/arrays.ndarray.html
- 数组创建例程。https://docs.scipy.org/doc/numpy-1.13.0/reference/routines.array-creation.html

### 4.6.3 API

- numpy.array() API。
  https://docs.scipy.org/doc/numpy-1.13.0/reference/generated/numpy.array.html
- numpy.empty() API。
  https://docs.scipy.org/doc/numpy-1.13.0/reference/generated/numpy.empty.html
- numpy.zeros() API。
  https://docs.scipy.org/doc/numpy-1.13.0/reference/generated/numpy.zeros.html
- numpy.ones() API。
  https://docs.scipy.org/doc/numpy-1.13.0/reference/generated/numpy.ones.html
- numpy.vstack() API。
  https://docs.scipy.org/doc/numpy-1.13.0/reference/generated/numpy.vstack.html
- numpy.hstack() API。
  https://docs.scipy.org/doc/numpy-1.13.0/reference/generated/numpy.hstack.html

## 4.7 Summary

在本教程中，你了解了 NumPy 中的 N维数组，用于在 Python 中表示数值和操作数据。具体来说，你学习了：

- 什么是 ndarray 以及如何在 Python 中创建和检查数组。
- 创建新空数组和带默认值数组的关键函数。
- 如何合并现有数组以创建新数组。

### 4.7.1 Next

在下一章中，你将了解如何对 NumPy 数组进行切片、索引和重塑。

## Chapter 5

### Index, Slice and Reshape NumPy Arrays

机器学习数据表示为数组。在 Python 中，数据几乎普遍表示为 NumPy 数组。如果你是 Python 新手，可能会对一些 Pythonic 的数据访问方式感到困惑，例如负索引和数组切片。在本教程中，你将了解如何在 NumPy 数组中正确操作和访问数据。完成本教程后，你将知道：

- 如何将列表数据转换为 NumPy 数组。
- 如何使用 Pythonic 索引和切片访问数据。
- 如何调整数据大小以满足某些机器学习 API 的期望。

让我们开始吧。

### 5.1 Tutorial Overview

本教程分为 4 部分；它们是：

- 1. 从列表到数组
- 2. 数组索引
- 3. 数组切片
- 4. 数组重塑

### 5.2 From List to Arrays

一般来说，我建议使用 Pandas 或甚至 NumPy 函数从文件加载数据。本节假设你已通过其他方式加载或生成数据，并且数据现在使用 Python 列表表示。让我们看看如何将列表中的数据转换为 NumPy 数组。

### 5.2.1 One-Dimensional List to Array

你可能会加载数据或生成数据，并将其作为列表访问。你可以通过调用 array() NumPy 函数将一维数据列表转换为数组。

```python
# create one-dimensional array
from numpy import array
# list of data
data = [11, 22, 33, 44, 55]
# array of data
data = array(data)
print(data)
print(type(data))
```

Listing 5.1: 创建一维数组的示例。

运行示例将一维列表转换为 NumPy 数组。

```
[11 22 33 44 55]
<class 'numpy.ndarray'>
```

Listing 5.2: 创建一维数组的示例输出。

### 5.2.2 Two-Dimensional List of Lists to Array

在机器学习中，你更有可能拥有二维数据。即一个数据表，其中每行表示一个新观测，每列表示一个新特征。也许你生成了数据或使用自定义代码加载了数据，现在你有一个列表的列表。每个列表表示一个新观测。你可以像上面一样，通过调用 array() 函数将列表的列表转换为 NumPy 数组。

```python
# create two-dimensional array
from numpy import array
# list of data
data = [[11, 22],
        [33, 44],
        [55, 66]]
# array of data
data = array(data)
print(data)
print(type(data))
```

Listing 5.3: 创建二维数组的示例。

运行示例显示数据已成功转换。

```
[[11 22]
 [33 44]
 [55 66]]
<class 'numpy.ndarray'>
```

Listing 5.4: 创建二维数组的示例输出。

