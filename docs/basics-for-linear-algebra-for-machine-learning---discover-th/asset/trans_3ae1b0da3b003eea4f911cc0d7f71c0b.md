

## 5.5 数组重塑

对数据进行切片后，您可能需要重塑它。例如，某些库（如 scikit-learn）可能要求将一维输出变量数组（y）重塑为具有一列和每列结果的二维数组。某些算法（如 Keras 中的长短期记忆循环神经网络）要求将输入指定为由样本、时间步和特征组成的三维数组。了解如何重塑 NumPy 数组非常重要，以便您的数据满足特定 Python 库的要求。我们将研究这两个示例。

### 5.5.1 数据形状

NumPy 数组具有 **shape** 属性，该属性返回数组每个维度长度的元组。例如：

```
# shape of one-dimensional array
from numpy import array
# define array
data = array([11, 22, 33, 44, 55])
print(data.shape)
```

清单 5.32: 访问一维数组 **shape** 的示例。

运行该示例将为一维打印一个元组。

```
(5,)
```

清单 5.33: 一维数组 **shape** 的示例输出。

对于二维数组，将返回包含两个长度的元组。

```
# shape of a two-dimensional array
from numpy import array
# list of data
data = [[11, 22],
        [33, 44],
        [55, 66]]
# array of data
data = array(data)
print(data.shape)
```

清单 5.34: 访问二维数组 **shape** 的示例。

运行该示例将返回包含行数和列数的元组。

```
(3, 2)
```

清单 5.35: 二维数组 **shape** 的示例输出。

您可以在 **shape** 维度中使用数组维度的大小，例如指定参数。元组的元素可以像数组一样访问，第 0 个索引表示行数，第 1 个索引表示列数。例如：

```
# row and column shape of two-dimensional array
from numpy import array
# list of data
data = [[11, 22],
        [34, 44],
        [55, 66]]
# array of data
data = array(data)
print('Rows: %d' % data.shape[0])
print('Cols: %d' % data.shape[1])
```

清单 5.36: 按行和列访问二维数组 shape 的示例。

运行该示例将访问每个维度的特定大小。

```
Rows: 3
Cols: 2
```

清单 5.37: 按行和列输出二维数组 shape 的示例。

### 5.5.2 将一维数组重塑为二维数组

通常需要将一维数组重塑为具有一列和多个数组的二维数组。NumPy 在 NumPy 数组对象上提供 reshape() 函数，可用于重塑数据。reshape() 函数接受一个参数，用于指定数组的新形状。在将一维数组重塑为具有一列的二维数组的情况下，元组将是数组作为第一个维度的形状（data.shape[0]）和第二个维度的 1。

```
data = data.reshape((data.shape[0], 1))
```

清单 5.38: 使用 reshape() 函数将数据从 1D 重塑为 2D 的示例。

将所有这些结合起来，我们得到了以下完整示例。

```
# reshape 1D array to 2D
from numpy import array
# define array
data = array([11, 22, 33, 44, 55])
print(data.shape)
# reshape
data = data.reshape((data.shape[0], 1))
print(data.shape)
```

清单 5.39: 使用 reshape() 函数更改一维数组形状的示例。

运行该示例将打印一维数组的形状，将数组重塑为 5 行 1 列，然后打印此新形状。

```
(5,)
(5, 1)
```

清单 5.40: 使用 reshape() 函数更改一维数组形状的示例输出。

### 5.5.3 将二维数组重塑为三维数组

通常需要将每行表示一个序列的二维数据重塑为三维数组，以供期望一个或多个时间步和一个或多个特征的多个样本的算法使用。一个很好的示例是 Keras 深度学习库中的 LSTM 循环神经网络模型。可以直接使用 reshape 函数，指定新的维度。当每个序列在每个时间步都有多个时间步和一个观测值（特征）时，这一点很明显。我们可以使用数组 shape 属性中的大小来指定样本数（行）和列数（时间步），并将特征数固定为 1。

```
data.reshape((data.shape[0], data.shape[1], 1))
```

清单 5.41: 使用 reshape() 函数将数据从 2D 重塑为 3D 的示例。

将所有这些结合起来，我们得到了以下完整示例。

```
# reshape 2D array to 3D
from numpy import array
# list of data
data = [[11, 22],
        [33, 44],
        [55, 66]]
# array of data
data = array(data)
print(data.shape)
# reshape
data = data.reshape((data.shape[0], data.shape[1], 1))
print(data.shape)
```

清单 5.42: 使用 reshape() 函数更改二维数组形状的示例。

运行该示例首先打印二维数组中每个维度的大小，重塑数组，然后总结新三维数组的形状。

```
(3, 2)
(3, 2, 1)
```

清单 5.43: 使用 reshape() 函数更改二维数组形状的示例输出。

## 5.6 扩展

本节列出了您可能希望探索的扩展教程的一些想法。

- 开发一个索引、切片和重塑您自己的小型数据数组的示例。
- 从 CSV 文件加载一个小型真实数据集，并将其拆分为输入和输出元素
- 从 CSV 文件加载一个小型真实数据集，并将其拆分为训练和测试元素。

如果您探索了这些扩展中的任何一项，我很乐意了解。

## 5.7 进一步阅读

如果您希望深入了解，本节提供了更多关于该主题的资源。

### 5.7.1 图书

- *Python 数据分析*，2017 年。
  http://amzn.to/2B1sfXi
- *优雅的 SciPy*，2017 年。
  http://amzn.to/2yujXnT
- *NumPy 指南*，2015 年。
  http://amzn.to/2j3kEzd

### 5.7.2 参考文献

- NumPy 参考。
  https://docs.scipy.org/doc/numpy-1.13.0/reference/
- N 维数组。
  https://docs.scipy.org/doc/numpy-1.13.0/reference/arrays.ndarray.html
- 数组创建例程。
  https://docs.scipy.org/doc/numpy-1.13.0/reference/routines.array-creation.html
- NumPy 索引。
  https://docs.scipy.org/doc/numpy-1.13.0/user/basics.indexing.html
- SciPy 索引。
  https://docs.scipy.org/doc/numpy/reference/arrays.indexing.html
- 索引例程。
  https://docs.scipy.org/doc/numpy-1.13.0/reference/routines.indexing.html

### 5.7.3 API

- numpy.array() API。
  https://docs.scipy.org/doc/numpy-1.13.0/reference/generated/numpy.array.html
- numpy.reshape() API。
  https://docs.scipy.org/doc/numpy/reference/generated/numpy.reshape.html

## 5.8 总结

在本教程中，您了解了如何使用 Python 访问和重塑 NumPy 数组中的数据。具体来说，您学习了：

- 如何将列表数据转换为 NumPy 数组。
- 如何使用 Pythonic 索引和切片访问数据。
- 如何调整数据大小以满足某些机器学习 API 的要求。

### 5.8.1 下一节

在下一章中，您将了解数组广播以及 Python 中管理它的规则。

## 第 6 章

## NumPy 数组广播

大小不同的数组不能相加、相减或一般用于算术运算。克服此问题的一种方法是复制较小的数组，使其具有与较大数组相同的维度和大小。这称为数组广播，在 NumPy 执行数组算术运算时可用，可大大减少并简化您的代码。在本教程中，您将了解数组广播的概念以及如何在 NumPy 中实现它。完成本教程后，您将了解：

- 大小不同的数组进行算术运算的问题。
- 广播的解决方案以及一维和二维中的常见示例。
- 数组广播的规则以及广播失败的情况。

让我们开始吧。

### 6.1 教程概览

本教程分为 4 部分，分别是：

- 1. 数组算术运算的局限性
- 2. 数组广播
- 3. NumPy 中的广播
- 4. 广播的局限性

### 6.2 数组算术运算的局限性

您可以直接对 NumPy 数组执行算术运算，例如加法和减法。例如，可以将两个数组相加以创建一个新数组，其中每个索引处的值相加。例如，可以将数组 a 定义为 [1, 2, 3]，将数组 b 定义为 [1, 2, 3]，将它们相加将生成一个新数组，其值为 [2, 4, 6]。

