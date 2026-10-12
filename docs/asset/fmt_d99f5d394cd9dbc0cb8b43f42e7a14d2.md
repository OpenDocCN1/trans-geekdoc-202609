
在每种情况下，结果都是一个布尔数组，NumPy 为处理这些布尔结果提供了许多直接的模式。

### 布尔数组操作

给定一个布尔数组，可以执行许多有用的操作。我们将使用之前创建的二维数组 `x`。

**In [14]:**

```python
print(x)
```

```text
[[5 0 3 3]
 [7 9 3 5]
 [2 4 7 6]]
```

#### 统计条目

要统计布尔数组中 `True` 条目的数量，`np.count_nonzero` 很有用：

**In [15]:**

```python
###### how many values less than 6?
np.count_nonzero(x < 6)
```

**Out[15]:**

```text
8
```

我们看到有 8 个数组条目小于 6。获取此信息的另一种方法是使用 `np.sum`；在这种情况下，`False` 解释为 `0`，`True` 解释为 `1`：

**In [16]:**

```python
np.sum(x < 6)
```

**Out[16]:**

```text
8
```

`sum()` 的优势在于，与其他 NumPy 聚合函数一样，这种求和操作也可以沿着行或列进行：

**In [17]:**

```python
###### 每行中有多少个值小于 6？
np.sum(x < 6, axis=1)
```

**Out[17]:**

```text
array([4, 2, 2])
```

这将统计矩阵中每行小于 6 的值的数量。

如果我们想快速检查是否有任意值为真，或者所有值均为真，可以使用（你猜对了）`np.any` 或 `np.all`：

**In [18]:**

```python
###### 是否存在大于 8 的值？
np.any(x > 8)
```

**Out[18]:**

```text
True
```

**In [19]:**

```python
###### 是否存在小于零的值？
np.any(x < 0)
```

**Out[19]:**

```text
False
```

**In [20]:**

```python
###### 所有值是否都小于 10？
np.all(x < 10)
```

**Out[20]:**

```text
True
```

**In [21]:**

```python
###### 所有值是否都等于 6？
np.all(x == 6)
```

**Out[21]:**

```text
False
```

`np.all` 和 `np.any` 也可以沿特定轴使用。例如：

**In [22]:**

```python
###### 每行的所有值是否都小于 8？
np.all(x < 8, axis=1)
```

**Out[22]:**

```text
array([True, False, True], dtype=bool)
```

这里第一行和第三行的所有元素都小于 8，而第二行并非如此。

最后，一个快速警告：正如在[聚合操作：最小值、最大值及介于两者之间的一切](https://jakevdp.github.io/PythonDataScienceHandbook/02.04-computation-on-arrays-aggregates.html)中提到的，Python 拥有内置的 `sum()`、`any()` 和 `all()` 函数。这些函数的语法与 NumPy 版本不同，特别是当用于多维数组时，它们将会失败或产生意外结果。请务必确保在这些示例中使用 `np.sum()`、`np.any()` 和 `np.all()`。

### 布尔运算符

我们已经看到了如何统计，比如说，降雨量小于 4 英寸的所有天数，或降雨量大于 2 英寸的所有天数。但如果我们想了解降雨量小于 4 英寸**且**大于 1 英寸的所有天数怎么办？这可以通过 Python 的位逻辑运算符 `&`、`|`、`^` 和 `~` 来实现。就像标准算术运算符一样，NumPy 将这些重载为 ufuncs，它们在（通常是布尔）数组上逐元素工作。

例如，我们可以按如下方式解决这类复合问题：

**In [23]:**

```python
np.sum((inches > 0.5) & (inches < 1))
```

**Out[23]:**

```text
29
```

所以我们看到，有 29 天的降雨量在 0.5 到 1.0 英寸之间。

请注意，这里的括号很重要——由于运算符优先级规则，如果去掉括号，该表达式将按如下方式求值，从而导致错误：

`inches > (0.5 & inches) < 1`

利用 `A AND B` 等价于 `NOT (NOT A OR NOT B)` 的原理，我们可以用另一种方式计算相同的结果：

**In [24]:**

```python
np.sum(~((inches <= 0.5) | (inches >= 1)))
```

**Out[24]:**

```text
29
```

在数组上结合比较运算符和布尔运算符，可以实现各种高效的逻辑操作。

下表总结了位布尔运算符及其等价的 ufuncs：

| 运算符 | 等价 ufunc |
| :--- | :--- |
| `&` | `np.bitwise_and` |
| `|` | `np.bitwise_or` |
| `^` | `np.bitwise_xor` |
| `~` | `np.bitwise_not` |

使用这些工具，我们可以开始回答关于天气数据的各类问题。以下是结合掩码与聚合计算的一些结果示例：

**In [25]:**

```python
print("无雨天数:      ", np.sum(inches == 0))
print("有雨天数:         ", np.sum(inches != 0))
print("降雨量 > 0.5 英寸的天数:", np.sum(inches > 0.5))
print("降雨量 < 0.2 英寸的雨天  :", np.sum((inches > 0) &
(inches < 0.2)))
```

```text
无雨天数:      215
有雨天数:         150
降雨量 > 0.5 英寸的天数: 37
降雨量 < 0.2 英寸的雨天: 75
```

### 布尔数组作为掩码

一种更强大的模式是使用布尔数组作为掩码，以选取数据的特定子集。回到之前的 `x` 数组，假设我们想要一个包含数组中所有小于 5 的值的数组：

**In [26]:**

```python
x
```

**Out[26]:**

```text
array([[5, 0, 3, 3],
       [7, 9, 3, 5],
       [2, 4, 7, 6]])
```

我们可以轻松获得该条件对应的布尔数组，正如我们已经看到的：

**In [27]:**

```python
x < 5
```

**Out[27]:**

```text
array([[False, True,  True,  True],
       [False, False, True, False],
       [True,  True, False, False]], dtype=bool)
```

现在要从数组中选取这些值，我们只需使用这个布尔数组进行索引；这被称为掩码操作：

**In [28]:**

```python
x[x < 5]
```

**Out[28]:**

```text
array([0, 3, 3, 3, 2, 4])
```

返回的是一个一维数组，包含所有满足该条件的值；换句话说，即掩码数组为 `True` 的位置对应的所有值。

然后我们可以随意对这些值进行操作。例如，我们可以对西雅图雨量数据计算一些相关统计量：

**In [29]:**

```python
##### 构建所有雨天的掩码
rainy = (inches > 0)
##### 构建所有夏季天数的掩码（6 月 21 日是第 172 天）
days = np.arange(365)
summer = (days > 172) & (days < 262)
print("2014 年雨天的中位数降水量 (英寸):  ",
np.median(inches[rainy]))
print("2014 年夏季的中位数降水量 (英寸): ",
np.median(inches[summer]))
print("2014 年夏季的最大降水量 (英寸):",
np.max(inches[summer]))
print("非夏季雨天的中位数降水量 (英寸):",
np.median(inches[rainy & ~summer]))
```

```text
2014 年雨天的中位数降水量 (英寸):   0.194881889764
2014 年夏季的中位数降水量 (英寸):  0.0
2014 年夏季的最大降水量 (英寸): 0.850393700787
非夏季雨天的中位数降水量 (英寸): 0.200787401575
```

通过结合布尔运算、掩码操作和聚合，我们可以非常快速地回答此类数据集问题。

### 旁注：关键字 and/or 与运算符 &/| 的对比

一个常见的困惑点在于关键字 `and` 和 `or` 与运算符 `&` 和 `|` 之间的区别。何时该用哪一个？

区别在于：`and` 和 `or` 衡量整个对象的真假，而 `&` 和 `|` 作用于对象内部的每一位。

当你使用 `and` 或 `or` 时，相当于要求 Python 将对象视为单个布尔实体。在 Python 中，所有非零整数都将评估为 `True`。因此：

**In [30]:**

```python
bool(42), bool(0)
```

**Out[30]:**

```text
(True, False)
```

**In [31]:**

```python
bool(42 and 0)
```

**Out[31]:**

```text
False
```

**In [32]:**

```python
bool(42 or 0)
```

**Out[32]:**

```text
True
```

当你在整数上使用 `&` 和 `|` 时，表达式作用于元素的位，将 `and` 或 `or` 应用于组成该数字的各个位：

**In [33]:**

```python
bin(42)
```

**Out[33]:**

```text
'0b101010'
```

**In [34]:**

```python
bin(59)
```

**Out[34]:**

```text
'0b111011'
```

**In [35]:**

```python
bin(42 & 59)
```

**Out[35]:**

```text
'0b101010'
```

**In [36]:**

```python
bin(42 | 59)
```

**Out[36]:**

```text
'0b111011'
```

注意，二进制表示的对应位按顺序比较以产生结果。

当你在 NumPy 中拥有一个布尔值数组时，可以将其视为一串位，其中 `1 = True`，`0 = False`，`&` 和 `|` 的结果与上述类似：

**In [37]:**

```python
A = np.array([1, 0, 1, 0, 1, 0], dtype=bool)
B = np.array([1, 1, 1, 0, 1, 1], dtype=bool)
A | B
```

**Out[37]:**

```text
array([ True,  True,  True, False,  True,  True], dtype=bool)
```

在这些数组上使用 `or` 将尝试评估整个数组对象的真假，这不是一个定义明确的值：

**In [38]:**

```python
A or B
```

```text
---------------------------------------------------------------------------
ValueError                                Traceback (most recent call last)
<ipython-input-38-5d8e4f2e21c0> in <module>()
----> 1 A or B
ValueError: The truth value of an array with more than one element is ambiguous. Use a.any() or a.all()
```

同样，在给定数组上进行布尔表达式运算时，应使用 `|` 或 `&` 而不是 `or` 或 `and`：

**In [39]:**

```python
x = np.arange(10)
(x > 4) & (x < 8)
```

**Out[39]:**

```text
array([False, False, False, False, False, True, True, True, False, False], dtype=bool)
```

尝试评估整个数组的真假将给出我们之前看到的相同 `ValueError`：

**In [40]:**

```python
(x > 4) and (x < 8)
```

```text
---------------------------------------------------------------------------
ValueError                                Traceback (most recent call last)
<ipython-input-40-3d24f1ffd63d> in <module>()
----> 1 (x > 4) and (x < 8)
ValueError: The truth value of an array with more than one element is ambiguous. Use a.any() or a.all()
```

所以请记住这一点：`and` 和 `or` 对整个对象执行单次布尔评估，而 `&` 和 `|` 对对象的内容（单个位或字节）执行多次布尔评估。对于布尔 NumPy 数组，后者几乎总是期望的操作。

## 4.4 花式索引

花式索引在概念上很简单：它意味着传递一个索引数组以一次性访问多个数组元素。

### 花式索引的优势

花式索引支持一次性选择多个元素。它还消除了通过索引从数组返回多个元素时的重复问题。

例如，考虑以下数组：

**In [1]:**

```python
import numpy as np
rand = np.random.RandomState(42)
x = rand.randint(100, size=10)
print(x)
```

```text
[51 92 14 71 60 20 82 86 74 74]
```

假设我们想要访问三个不同的元素。我们可以这样做：

**In [2]:**

```python
[x[3], x[7], x[2]]
```

**Out[2]:**

```text
[71, 86, 14]
```

或者，我们可以传递一个单一的索引列表或数组以获得相同的结果：

**In [3]:**

```python
ind = [3, 7, 4]
x[ind]
```

**Out[3]:**

```text
array([71, 86, 60])
```

使用花式索引时，结果的形状反映的是 `索引数组` 的形状，而不是 `被索引数组` 的形状：

**In [4]:**

```python
ind = np.array([[3, 7],
                [4, 5]])
x[ind]
```

**Out[4]:**

```text
array([[71, 86],
       [60, 20]])
```

花式索引也适用于多维情况。考虑以下数组：

**In [5]:**

```python
X = np.arange(12).reshape((3, 4))
X
```

**Out[5]:**

```text
array([[ 0,  1,  2,  3],
       [ 4,  5,  6,  7],
       [ 8,  9, 10, 11]])
```

与标准索引一样，第一个索引指的是行，第二个指的是列：

**In [6]:**

```python
row = np.array([0, 1, 2])
col = np.array([2, 1, 3])
X[row, col]
```

**Out[6]:**

```text
array([ 2,  5, 11])
```

请注意，结果中的第一个值是 `X[0, 2]`，第二个是 `X[1, 1]`，第三个是 `X[2, 3]`。

**In [7]:**

```python
X[row[:, np.newaxis], col]
```

**Out[7]:**

```text
array([[ 2,  1,  3],
       [ 6,  5,  7],
       [10,  9, 11]])
```

在这里，每个行值都与每个列向量匹配，这正如我们在算术运算的广播中所见。例如：

**In [8]:**

```python
row[:, np.newaxis] * col
```

**Out[8]:**

```text
array([[0, 0, 0],
       [2, 1, 3],
       [4, 2, 6]])
```

永远要记住，使用花式索引时，返回值反映的是索引的广播形状，而不是被索引数组的形状。

## 4.5 Python: NumPy 的结构化数组

NumPy 的结构化数组类似于 C 语言中的 `Struct`。它用于将不同类型和大小的数据分组。结构化数组使用称为字段的数据容器。每个数据字段可以包含任意类型和大小的数据。数组元素可以通过点号表示法访问。

### 结构化数组的属性

*   数组中的所有结构体具有相同数量的字段。
*   所有结构体具有相同的字段名称。

例如，考虑一个学生的结构化数组，它包含姓名、年级、分数等不同字段。

![`media.geeksforgeeks.org/wp-content/uploads/20191228142752/WhatsApp-Image-2019-12-28-at-2.27.07-PM.jpeg`](img/image_rsrc9TW.jpg)

图 4.5 学生的结构

数组 student 中的每条记录都具有 `Struct` 类的结构。结构的数组被称为 struct，因为在数组中为新结构体添加任何新字段都包含空数组。

**示例 1：**

```python
##### Python program to demonstrate
##### Structured array
import numpy as np
a = np.array([('Sana', 2, 21.0), ('Mansi', 7, 29.0)],
             dtype=[('name', (np.str_, 10)), ('age', np.int32), ('weight', np.float64)])
print(a)
```

输出：

```text
[('Sana', 2, 21.0) ('Mansi', 7, 29.0)]
```

**示例 2：** 结构数组可以通过使用 `numpy.sort()` 方法并将 `order` 作为参数传递来进行排序。该参数接受需要根据其进行排序的字段的值。
