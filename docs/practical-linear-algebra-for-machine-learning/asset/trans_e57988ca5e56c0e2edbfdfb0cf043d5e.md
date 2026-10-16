
```
b = np.int32(a)
print('Array "b": ', b)
print('Type array "b": ', type(b))
print('Array "b" data type: ', b.dtype)

# Turn Python list into a NumPy array of type np.float32 (same as Python float)
c = np.float32(a)
print('Array "c": ', c)
print('Type array "c": ', type(c))
print('Array "c" data type: ', c.dtype)
```

```
Type "a": <class 'list'>
Array "b": [1 2 1]
Type array "b": <class 'numpy.ndarray'>
Array "b" data type: int32
Array "c": [1. 2. 1.3]
Type array "c": <class 'numpy.ndarray'>
Array "c" data type: float32
```

我们使用 NumPy 的 .dtype 方法来确定数组内部的数据类型。更改 NumPy 数组类型的推荐方法是使用 .astype() 方法。请看下面的示例：

```
# Import NumPy library
import numpy as np

# Define a Python list
a = [1, 2, 4]
print('Type "a": ', type(a))

# Turn Python list into a NumPy array of type np.int32 (Integer (-2147483648 to 2147483647))
b = np.int32(a)
print('Array "b": ', b)
print('Type array "b": ', type(b))

# Turn Python list into a NumPy array of type np.float32 (same as Python float)
c = b.astype(np.float32)
print('Array "c": ', c)
print('Type array "c": ', type(c))
```

```
Type "a": <class 'list'>
Array "b": [1 2 4]
Type array "b":  <class 'numpy.ndarray'>
Array "c":  [1. 2. 4.]
Type array "c":  <class 'numpy.ndarray'>
```

## 3.3. 定义 NumPy 数组

数组本质上是一个一维或多维的值网格。特别是在 NumPy 数组中，所有值都来自同一类型（整数、浮点数）。我们将如何定义 NumPy 数组？对于 NumPy 数组，我们有以下定义：

- **Rank:** 数组拥有的维度数。
- **Shape:** 一个元组，表示每个维度中的元素数量。Ex: 数组的形状为 (2,4,10) 表示我们有一个三维数组，其在第一、第二和第三维度中分别有 2、4 和 10 个元素。

### 3.3.1 从列表创建数组

现在让我们开始使用 Python。我们从最常见的方法开始。让我们从列表创建一个 NumPy 数组：

```
# Import NumPy library
import numpy as np

# Define a Python list
mylist = [1, 2, 4, 8]

# Create a NumPy array from the list
numpy_array = np.array(mylist)
print('Array: ', numpy_array)
```

```
Array:  [1 2 4 8]
```

![](img/37669628775ca7a07835165249fef088_17_0.png)

Fig. 3.1. 上面，我们使用 np.array 函数将列表转换为 NumPy 数组

如果我们不定义列表而只是像下面这样输入数字会怎样：

```
# Import NumPy library
import numpy as np

# Naively input the numbers
numpy_array = np.array(1,2,4,8)
print('Array: ', numpy_array)
```

> 运行上面的代码，看看你会得到什么输出。

现在，让我们定义一个二维数组：

```
# Import NumPy library
import numpy as np

# Naively input the numbers
row1 = [2,4,6,8]
row2 = [1,3,5,7]
numpy_array = np.array([row1,row2])
print('Array: ', numpy_array)

# Get the shape
print('Shape: ', numpy_array.shape)
```

```
Array:  [[2 4 6 8]
 [1 3 5 7]]
Shape:  (2, 4)
```

![](img/37669628775ca7a07835165249fef088_18_0.png)

**Fig. 3.2.** 上面，我们将列表转换为二维 NumPy 数组

让我们再次看一下上面的代码。我们定义了一个矩阵。**np.array** 内部的参数是一个列表，其每个元素都是另一个列表（见上图）！内部列表 row1 和 row2 构成了矩阵的行，并且必须具有相同的大小！想想为什么？这是一个简单的示例，展示了如何创建数组。** .shape** 方法用于返回 NumPy 数组的形状。上面的输出显示我们有一个矩阵，有两行四列。

### 3.3.2 特殊函数

我们可以使用一些特殊的 NumPy 函数创建 NumPy 数组。下面我列出了几个供参考：

```
# Import NumPy library
import numpy as np

### Defining arrays using special functions ###
# Arguments:
# shape: The shape of the numpy array
# dtype: Specifying the data type (not required)

# Defining an all-zero array
zeroArray = np.zeros(shape=(3,5), dtype=np.int16 )
print("zeroArray: ", zeroArray)

# Defining an all-one array
onesArray = np.ones(shape=(3,5), dtype=np.float32 )
print("onesArray: ", onesArray)

# Defining an array filled with one specific element
fullArray = np.full(shape=(3,5), fill_value=4.2, dtype=np.float64 )
print("fullArray: ", fullArray)
```

```
zeroArray: [[0 0 0 0 0]
 [0 0 0 0 0]
 [0 0 0 0 0]]
onesArray: [[1. 1. 1. 1. 1.]
 [1. 1. 1. 1. 1.]
 [1. 1. 1. 1. 1.]]
fullArray: [[4.2 4.2 4.2 4.2 4.2]
 [4.2 4.2 4.2 4.2 4.2]
 [4.2 4.2 4.2 4.2 4.2]]
```

![](img/37669628775ca7a07835165249fef088_19_0.png)

![](img/37669628775ca7a07835165249fef088_19_1.png)

Fig. 3.3. 定义填充有特定元素的数组

最重要的特殊函数之一是 np.arange，它类似于 Python 的 range 内置函数。np.arange 的使用示例如下：

```
# Import NumPy library
import numpy as np

# Define a NumPy array using np.arange
# np.arange defines an interval of numbers
# Arguments:
#   start: Starting of the interval.
#   stop: Ending of the interval.
#   step: Step size.
# NOTE: The interval includes "start" number but does NOT include "stop" number.
arr = np.arange(start=3,stop=10,step=2)
print("Array: ", arr)
```

```
Array: [3 5 7 9]
```

![](img/37669628775ca7a07835165249fef088_20_0.png)

Fig. 3.4. NumPy 索引从 0 开始到无穷大！通过定义 np.arange(start=3,stop=10,step=2)，起始索引为 3。停止索引为 10 但它不包含在范围内。步长为 2 表示每隔一个索引被选中，即我们只选择绿色索引并跳过橙色索引

### 3.3.3 通用函数

NumPy 为了执行逐元素操作，提供了一些通用函数。看看下面演示的一些通用函数：

```
# Import NumPy library
import numpy as np

v = np.array([1, 3, 5])
w = np.array([2, 4, 6])

# Exponential operation
print('e^v= ', np.exp(v))

# The square root of an array
print('v^{1/2}= ', np.sqrt(v))

# Adding two vectors
print('v+w= ', np.add(v, w))

# Sin and Cos of an array
print('Sin(v)= ', np.sin(v))
print('Cos(v)= ', np.cos(v))
```

运行上面的代码查看结果。

### 3.3.4 随机数组

有时希望定义一个包含随机数的数组。完成此任务的方法有很多，具体取决于我们想要使用的随机数类型。例如，我们是否想要生成随机整数、浮点数等？看看下面的方法：

```
# Import NumPy library
import numpy as np

### Defining arrays with random elements ###
# Arguments:
#   size: The size of the numpy array

# Defining a random array
randArray = np.random.random(size=(2,3))
print("randArray: ", randArray)

# Defining a random array with integer elements
# high: The highest element that is allowed to be generated is `` high-1``
# low: The lowest integer that is allowed to be generated
randintArray = np.random.randint(low=1, high=5, size=(2,3))
print("randintArray: ", randintArray)
```

```
randArray:  [[0.65055144 0.12510875 0.09906024]
 [0.47333278 0.67082837 0.7673982 ]]
randintArray:  [[4 4 1]
 [1 2 2]]
```

**CAVEAT**

由于我们生成了一个随机向量，如果你使用上面的 Python 代码，你绝对不会得到我上面报告的结果！虽然这是显而易见的，对吧？

## 3.4. 基本算术运算

让我们先通过一些示例介绍基本算术运算：

```
# Import NumPy library
import numpy as np

# Create two arrays
a = np.array([[1,5],[0,8]], dtype=np.float32)
b = np.array([[2,1],[5,2]], dtype=np.float32)
print('a= ', a)
print('b= ', b)

# Elementwise adding
# a + b and np.add(a, b) are the same.
# Check to see if a + b and np.add(a, b) are the same using ``assert ``.
# .all() method check if all elements of a matrix is True.
print('a + b= ', a + b)
assert((a + b == np.add(a, b)).all())

# Elementwise subtraction
print('a - b= ', a - b)
assert((a - b == np.subtract(a, b)).all())

# Elementwise multiplication
print('a * b= ', a * b)
assert((a * b == np.multiply(a, b)).all())

# Elementwise division
print('a / b= ',a / b)
assert((a / b == np.divide(a, b)).all())

# Elementwise square
print('a^2= ', np.square(a))
assert((a ** 2 == np.square(a)).all())
```

```
a= [[1. 5.]
    [0. 8.]]
b= [[2. 1.]
    [5. 2.]]
a + b= [[ 3.   6.]
        [ 5.  10.]]
a - b= [[-1.   4.]
        [-5.   6.]]
a * b= [[ 2.   5.]
        [ 0.  16.]]
a / b= [[0.5 5. ]
```
