

方便且高效地处理数据。在本章中，我们将更详细地讨论列表和元组。

我们将演示常见的列表和元组操作。你会发现，列表（可修改）和元组（不可修改）具有许多共同功能。每种都可以保存相同或不同类型的项目。列表可根据需要动态调整大小，在执行时增长和缩小。我们讨论一维列表和二维列表。

在前一章中，我们演示了随机数生成并模拟了掷六面骰子。我们以本章的下一个数据科学入门部分作为结尾，该部分使用可视化库 Seaborn 和 Matplotlib 交互式地开发包含骰子频率的静态柱状图。在下一章的数据科学入门部分中，我们将展示一个动画可视化，其中柱状图会随着骰子掷出次数的增加而动态变化——你将看到大数定律“在行动中”。

## 5.2 列表

在此，我们将更详细地讨论列表，并解释如何引用特定的列表元素。本节中展示的许多功能适用于所有序列类型。

### 创建列表

列表通常存储同构数据，即相同数据类型的值。考虑包含五个整数元素的列表 c：

单击此处查看代码图像

```python
In [1]: c = [-45, 6, 0, 72, 1543]

In [2]: c
Out[2]: [-45, 6, 0, 72, 1543]
```

它们也可以存储异构数据，即多种不同类型的数据。例如，以下列表包含学生的名（字符串）、姓（字符串）、绩点平均分（浮点数）和毕业年份（整数）：

```python
['Mary', 'Smith', 3.57, 2022]
```

### 访问列表元素

你通过编写列表名称，后跟元素的 **索引**（即其 **位置编号**），并用方括号（`[ ]`，称为 **订阅运算符**）括起来来引用列表元素。以下图表显示了标记了元素名称的列表 `c`：

![](img/34b7fc2f1ee27beb73bca14927d42340_172_0.png)

列表中的第一个元素的索引为 `0`。因此，在五元素列表 `c` 中，第一个元素名为 `c[0]`，最后一个元素为 `c[4]`：

```python
In [3]: c[0]
Out[3]: -45

In [4]: c[4]
Out[4]: 1543
```

### 确定列表长度

要获取列表长度，请使用内置 `len` 函数：

```python
In [5]: len(c)
Out[5]: 5
```

### 使用负索引从列表末尾访问元素

列表也可以使用 *负索引* 从末尾访问：

![](img/34b7fc2f1ee27beb73bca14927d42340_172_1.png)

因此，列表 `c` 的最后一个元素（`c[4]`）可以通过 `c[-1]` 访问，其第一个元素可以通过 `c[-5]` 访问：

```python
In [6]: c[-1]
Out[6]: 1543

In [7]: c[-5]
Out[7]: -45
```

### 索引必须是整数或整数表达式

索引必须是整数或整数表达式（或我们很快将看到的 *切片*）：

```python
In [8]: a = 1

In [9]: b = 2

In [10]: c[a + b]
Out[10]: 72
```

使用非整数索引值会导致 TypeError。

### 列表是可变的

列表是可变的——其元素可以被修改：

单击此处查看代码图像

```python
In [11]: c[4] = 17

In [12]: c
Out[12]: [-45, 6, 0, 72, 17]
```

你很快就会发现，你还可以插入和删除元素，从而更改列表的长度。

### 某些序列是不可变的

Python 的字符串和元组序列是不可变的——它们不能被修改。你可以获取字符串中的单个字符，但尝试向其中一个字符赋予新值会导致 TypeError：

单击此处查看代码图像

```python
In [13]: s = 'hello'

In [14]: s[0]
Out[14]: 'h'

In [15]: s[0] = 'H'
```

TypeError
Traceback (most recent call last)
<ipython-input-15-812ef2514689> in <module>()
----> 1 s[0] = 'H'

TypeError: 'str' object does not support item assignment

### 尝试访问不存在的元素

使用超出范围的列表、元组或字符串索引会导致 IndexError：

单击此处查看代码图像

```python
In [16]: c[100]
IndexError
Traceback (most recent call last)
ipython-input-16-9a31eale1a13> in <module>()
----> 1 c[100]

IndexError: list index out of range
```

### 在表达式中使用列表元素

列表元素可用作表达式中的变量：

```python
In [17]: c[0] + c[1] + c[2]
Out[17]: -39
```

### 使用 += 向列表追加元素

先从空列表 [] 开始，然后使用 for 语句和 += 将值 1 到 5 追加到列表中——列表会动态增长以容纳每个项目：

单击此处查看代码图像

```python
In [18]: a_list = []

In [19]: for number in range(1, 6):
    ...:     a_list += [number]
    ...:

In [20]: a_list
Out[20]: [1, 2, 3, 4, 5]
```

当 += 的左操作数是列表时，右操作数必须是 *可迭代对象*；否则会发生 `TypeError`。在片段 [19] 的套件中，*number* 两侧的方括号创建一个单元素列表，我们将其追加到 *a_list*。如果右操作数包含多个元素，+= 会将它们全部追加。以下将 'Python' 的字符追加到列表 *letters* 中：

单击此处查看代码图像

```python
In [21]: letters = []

In [22]: letters += 'Python'

In [23]: letters
Out[23]: ['P', 'y', 't', 'h', 'o', 'n']
```

如果 += 的右操作数是元组，其元素也会被追加到列表中。本章稍后，我们将使用列表方法 *append* 向列表添加项目。

### 使用 + 连接列表

你可以使用 + 运算符 **连接** 两个列表、两个元组或两个字符串。结果是一个 *新* 的同类型序列，包含左操作数的元素，后跟右操作数的元素。原始序列保持不变：

单击此处查看代码图像

```python
In [24]: list1 = [10, 20, 30]

In [25]: list2 = [40, 50]

In [26]: concatenated_list = list1 + list2

In [27]: concatenated_list
Out[27]: [10, 20, 30, 40, 50]
```

如果 + 运算符的操作数是不同的序列类型，则会发生 *TypeError*——例如，连接列表和元组会出错。

### 使用 *for* 和 *range* 访问列表索引和值

列表元素也可以通过其索引和订阅运算符（[]）访问：

单击此处查看代码图像

```python
In [28]: for i in range(len(concatenated_list)):
    ...:     print(f'{i}: {concatenated_list[i]}')
    ...:
0: 10
1: 20
2: 30
3: 40
4: 50
```

函数调用 `range(len(concatenated_list))` 生成一系列整数，表示 `concatenated_list` 的索引（在此例中为 0 到 4）。以这种方式循环时，必须确保索引在范围内。稍后，我们将展示使用内置函数 `enumerate` 访问元素索引和值的更安全方法。

### 比较运算符

你可以使用比较运算符按元素比较整个列表：

单击此处查看代码图像

```python
In [29]: a = [1, 2, 3]

In [30]: b = [1, 2, 3]

In [31]: c = [1, 2, 3, 4]

In [32]: a == b # True: corresponding elements in both are equal
Out[32]: True

In [33]: a == c # False: a and c have different elements and lengths
Out[33]: False

In [34]: a < c # True: a has fewer elements than c
Out[34]: True

In [35]: c >= b # True: elements 0-2 are equal but c has more elements
Out[35]: True
```

## 5.3 元组

如前一章所述，元组是不可变的，通常存储异构数据，但数据也可以是同构的。元组的长度是其元素的数量，在程序执行期间不能更改。

### 创建元组

要创建空元组，请使用空括号：

```python
In [1]: student_tuple = ()

In [2]: student_tuple
Out[2]: ()

In [3]: len(student_tuple)
Out[3]: 0
```

请记住，可以通过用逗号分隔其值来打包元组：

单击此处查看代码图像

```python
In [4]: student_tuple = 'John', 'Green', 3.3

In [5]: student_tuple
Out[5]: ('John', 'Green', 3.3)

In [6]: len(student_tuple)
Out[6]: 3
```

输出元组时，Python 始终在括号中显示其内容。你可以用可选括号括起来元组的逗号分隔值列表：

单击此处查看代码图像

```python
In [7]: another_student_tuple = ('Mary', 'Red', 3.3)

In [8]: another_student_tuple
Out[8]: ('Mary', 'Red', 3.3)
```

以下代码创建一个单元素元组：

单击此处查看代码图像

```python
In [9]: a_singleton_tuple = ('red',) # note the comma

In [10]: a_singleton_tuple
Out[10]: ('red',)
```

紧跟字符串 'red' 后的逗号 (,) 将 a_singleton_tuple 标识为元组——括号是可选的。如果省略逗号，括号将

