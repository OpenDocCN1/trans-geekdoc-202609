
array(`[False, False, False, False, False, True, True, True, False, False]`, dtype=bool)

尝试评估整个数组的真假将给出我们之前看到的相同 `ValueError`：

```
In [40]:
(x > 4) and (x < 8)
---------------------------------------------------------------------------
ValueError                                Traceback (most recent call last)
<ipython-input-40-3d24f1ffd63d> in <module>()
----> 1 (x > 4) and (x < 8)
ValueError: The truth value of an array with more than one element is ambiguous. Use a.any() or a.all()
```

所以请记住这一点：`and` 和 `or` 对整个对象执行单次布尔评估，而 `&` 和 `|` 对对象的内容（单个位或字节）执行多次布尔评估。对于布尔 NumPy 数组，后者几乎总是期望的操作。

### 4.4 花式索引

花式索引在概念上很简单：它意味着传递一个索引数组以一次性访问多个数组元素。

#### 花式索引的优势

花式索引支持一次性选择多个元素。它还消除了通过索引从数组返回多个元素时的重复问题。

例如，考虑以下数组：

```
In [1]:
import numpy as np
rand = np.random.RandomState(42)
x = rand.randint(100, size=10)
print(x)
[51 92 14 71 60 20 82 86 74 74]
```

假设我们想要访问三个不同的元素。我们可以这样做：

```
In [2]:
[x[3], x[7], x[2]]
Out[2]:
[71, 86, 14]
```

或者，我们可以传递一个单一的索引列表或数组以获得相同的结果：

```
In [3]:
ind = [3, 7, 4]
x[ind]
Out[3]:
array([71, 86, 60])
```

使用花式索引时，结果的形状反映的是 `索引数组` 的形状，而不是 `被索引数组` 的形状：

```
In [4]:
ind = np.array([[3, 7],
                [4, 5]])
x[ind]
Out[4]:
array([[71, 86],
       [60, 20]])
```

花式索引也适用于多维情况。考虑以下数组：

```
In [5]:
X = np.arange(12).reshape((3, 4))
X
Out[5]:
array([[ 0,  1,  2,  3],
       [ 4,  5,  6,  7],
       [ 8,  9, 10, 11]])
```

与标准索引一样，第一个索引指的是行，第二个指的是列：

```
In [6]:
row = np.array([0, 1, 2])
col = np.array([2, 1, 3])
X[row, col]
Out[6]:
array([ 2,  5, 11])
```

请注意，结果中的第一个值是 `X[0, 2]`，第二个是 `X[1, 1]`，第三个是 `X[2, 3]`。

```
In [7]:
X[row[:, np.newaxis], col]
Out[7]:
array([[ 2,  1,  3],
       [ 6,  5,  7],
       [10,  9, 11]])
```

在这里，每个行值都与每个列向量匹配，这正如我们在算术运算的广播中所见。例如：

```
In [8]:
row[:, np.newaxis] * col
Out[8]:
array([[0, 0, 0],
       [2, 1, 3],
       [4, 2, 6]])
```

永远要记住，使用花式索引时，返回值反映的是索引的广播形状，而不是被索引数组的形状。

### 4.5 Python: NumPy 的结构化数组

NumPy 的结构化数组类似于 C 语言中的 `Struct`。它用于将不同类型和大小的数据分组。结构化数组使用称为字段的数据容器。每个数据字段可以包含任意类型和大小的数据。数组元素可以通过点号表示法访问。

#### 结构化数组的属性

*   数组中的所有结构体具有相同数量的字段。
*   所有结构体具有相同的字段名称。

例如，考虑一个学生的结构化数组，它包含姓名、年级、分数等不同字段。

![https://media.geeksforgeeks.org/wp-content/uploads/20191228142752/WhatsApp-Image-2019-12-28-at-2.27.07-PM.jpeg](image_rsrc9TW.jpg)

图 4.5 学生的结构

数组 student 中的每条记录都具有 `Struct` 类的结构。结构的数组被称为 struct，因为在数组中为新结构体添加任何新字段都包含空数组。

**示例 1：**

```
# Python program to demonstrate
# Structured array
import numpy as np
a = np.array([('Sana', 2, 21.0), ('Mansi', 7, 29.0)],
             dtype=[('name', (np.str_, 10)), ('age', np.int32), ('weight', np.float64)])
print(a)
```

输出：
`[('Sana', 2, 21.0) ('Mansi', 7, 29.0)]`

**示例 2：** 结构数组可以通过使用 `numpy.sort()` 方法并将 `order` 作为参数传递来进行排序。该参数接受需要根据其进行排序的字段的值。

```
# Python program to demonstrate
# Structured array
import numpy as np
a = np.array([('Sana', 2, 21.0), ('Mansi', 7, 29.0)],
             dtype=[('name', (np.str_, 10)), ('age', np.int32), ('weight', np.float64)])
# Sorting according to the name
b = np.sort(a, order='name')
print('Sorting according to the name', b)
# Sorting according to the age
b = np.sort(a, order='age')
print('\n Sorting according to the age', b)
```

输出：
Sorting according to the name `[('Mansi', 7, 29.0) ('Sana', 2, 21.0)]`
Sorting according to the age `[('Sana', 2, 21.0) ('Mansi', 7, 29.0)]`

### 4.6 使用 Pandas 进行数据操作

Pandas 是一个用 Python 编写的开源数据分析和数据操作库。Pandas 为您提供了数据结构和函数，以无缝处理结构化数据。Pandas 这个名字指的是 "Panel Data"（面板数据），即结构化数据集。Pandas 有两个主要的类可供操作，即 `DataFrame` 和 `Series`。

**示例：**

```
# importing the pandas library
import pandas as pd
# creating a dataframe object
student_register = pd.DataFrame()
# assigning values to the
# rows and columns of the
# dataframe
student_register['Name'] = ['Abhijit','Smriti','Akash','Roshni']
student_register['Age'] = [20, 19, 20, 14]
student_register['Student'] = [False, True, True, False]
student_register
```

输出：
![Data-Manipulation-python-1](image_rsrc9TX.jpg)

正如你所见，DataFrame 对象分别有四行 `[0, 1, 2, 3]` 和三列 `["Name", "Age", "Student"]`。包含索引值即 `[0, 1, 2, 3]` 的列称为 `索引列`，这是 pandas 数据图中的默认部分。我们也可以根据需要更改它，因为 Python 很强大。

接下来，出于某些原因，我们想要在数据图中添加一个新学生，即你想向现有的 DataFrame 添加一行，这可以通过以下代码片段实现。

一个重要的概念是 Python 的 `dataframe` 对象由作为 `series` 对象的行组成，它们堆叠在一起形成一个表。因此，添加新行意味着创建一个新的 `series` 对象并将其追加到 DataFrame。

**示例：**

```
# creating a new pandas
# series object
new_person = pd.Series(['Mansi', 19, True],
                       index = ['Name', 'Age','Student'])
# using the .append() function
# to add that row to the dataframe
student_register.append(new_person, ignore_index = True)
```

输出：
![Python-data-manipulation](image_rsrc9TY.jpg)

在处理和整理任何数据之前，你需要获得其全貌，这包括统计结论，如标准差（`std`）、均值及其四分位数分布。此外，你需要知道每一列的确切信息，即它存储什么类型的值以及有多少个唯一值。有三个支持函数，`.shape`、`.info()` 和 `.describe()`，分别输出表的形状、行和列的信息，以及 DataFrame 的统计信息（仅限数值列）。

**示例：**

```
# for showing the dimension
# of the dataframe
print('Shape')
print(student_register.shape)
# showing info about the data
print("\n\n Info\n")
student_register.info()
# for showing the statistical
# info of the dataframe
print("\n\n Describe")
student_register.describe()
```

输出：
![data-manipulation-python-2](image_rsrc9TZ.jpg)

输出：
![data-manipulation-python-2](image_rsrc9U0.jpg)
