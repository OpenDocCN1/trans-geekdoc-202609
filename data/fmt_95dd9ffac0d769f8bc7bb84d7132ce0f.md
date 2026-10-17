
## Python 逻辑运算符

### `or` 运算符

对于 2 个对象 `x`、`y`，当 `x` 为真时，`x or y` 的结果为 `x`；当 `x` 为假时，`x or y` 的结果为 `y`。

```
print(3 or 2, end=' ')            # 因为 3 为真，3 or 2 的结果为 3
print(0 or 2, end=' ')            # 因为 0 为假，0 or 2 的结果为 2
print(False or True, end=' ')
print("" or 2)                    # 因为空字符串 "" 为假，"" or 2 的结果为 2
```

```
3 2 True 2
```

### `and` 运算符

对于 2 个对象 `x`、`y`，当 `x` 为真时，`x and y` 的结果为 `y`；当 `x` 为假时，`x and y` 的结果为 `x`。

```
print(3 and 2, end=' ')       # 因为 3 为真，3 and 2 的结果为 2
print(0 and 2, end=' ')       # 因为 0 为假，0 and 2 的结果为 0
print("" and 2, end=' ')      # 因为空字符串 "" 为假，
                              #   "" and 2 的结果为 ""，所以无输出
print(False and True)
```

```
2 0 False
```

Python 还有移位运算符（如按位与 `&`、按位或 `|`、异或 `^`、取反 `~`、左移 `<<`、右移 `>>`）和其他运算符。感兴趣的读者可自行查阅相关资料。

## 复合赋值运算符

运算符 `=` 也可以与其他算术运算符和位运算符结合使用。例如：

`+=` `-=` `*=` `/=` `%=` `**=` `&=` `|=` `^=` `~=` `<<=` `>>=`

```
x = 3
print(id(x))
x += 2  # x = x + 2
print(id(x))
```

`x += 2` 等价于 `x = x + 2`，意味着将原 `x` 对象加上 `2` 得到一个对象，然后变量名 `x` 引用该加法运算的结果对象。因此，前后的变量名 `x` 代表 2 个不同的对象。

## 成员运算符

运算符 `in` 和 `not in` 用于判断一个值（对象）是否在容器对象中。例如：

```
print("h" in "hwdong")
print("h" not in "hwdong")
```

```
True
False
```

## 下标运算符 `[]`

可以通过给**下标运算符 `[]`** 传递下标来访问容器对象的元素，例如：

```
s = "hwdong"
print(s[0], s[1], s[2], s[3], s[4], s[5])
print(s[-6], s[-5], s[-4], s[-3], s[-2], s[-1])
```

下标从 0 开始，字符串对象 `s` 由一系列字符组成，第一个字符的下标为 0，第二个字符的下标为 1，……，长度为 `n` 的字符串下标为 `0, 1, 2, ..., n-1`。

下标也可以是负整数，其中 `-1` 指最后一个字符，`-n` 指第一个字符。

## 字符串格式化

### `%` 格式化

使用格式字符 `%` 将某些数据格式化为字符串，创建新字符串。例如：

```
s2 = '%s %s %f' % ("The score", "of LiPing is: ", 78.5)
print(s2)
```

格式字符串 `'%s %s %f'` 中的 `%s` 和 `%f` 分别表示后面三个输出项（`"The score"`、`"of LiPing is: "`、`78.5`）前两个为字符串，最后一个为实数。

### `format()` 方法

使用字符串 `str` 的 `format()` 方法格式化字符串，即依次用 `format()` 方法中的数据替换字符串中的占位符 `{}`。例如：

```
print("{} {} {}".format("The score", "of LiPing is: ", 78.5))
```

# 1.1.4 控制语句

程序通常“自上而下”顺序执行每条语句。有时需要根据某个条件是否满足，决定是否执行某些语句，或重复执行某些语句。Python 的条件语句和循环语句是根据条件决定如何执行某些语句的控制语句。

## 1. `if` 语句

### 基本语法

```
if expression:
    program block
```

表示如果 `if` 关键字后表达式的结果为 `True` 或非零，则执行其中的程序块，例如：

```
score = float(input())
if score >= 60:
    print("Congratulations!")
    print("Passed the exam.")
```

```
60.5
Congratulations!
Passed the exam.
```

**注意**：

*   `if` 表达式后必须跟冒号：
*   在 Python 中，**对齐方式**（缩进）表示一组语句属于同一个程序块，例如 `if` 程序块中的 2 条语句。

Python 中属于同一程序块的代码必须正确缩进，否则 Python 解释器会报错。例如：

```
score = float(input())
if score >= 60:
    print("Congratulations!")
print("Passed the exam.")
```

```
File "", line 4
    print("Passed the exam.")
    ^
IndentationError: unindent does not match any outer indentation level
```

### `if-else` 结构

`if` 和 `else` 可以组合使用，表示“如果……否则……”。即当 `if` 中的条件表达式为 `True` 时，执行 `if` 子句中的程序块，否则执行 `else` 子句中的程序块。`else` 后面没有条件表达式。格式如下：

```
if expression:
    code block 1
else:
    code block 2
```

示例：

```
score = float(input("Please enter the score:"))
if score >= 60:                          # If score >= 60, execute the program block in if
    print("Congratulations!")
    print("Passed the exam.")
else:                                  # Otherwise, execute the else block
    print("You failed the test.")
    print("Keep working hard, come on!")
```

```
Please enter grade: 67.5
Congratulations!
Passed the exam.
```

### `if-elif-else` 结构

对于多重条件，可以使用 `if` 的另一种形式 `if...elif...else`，表示“如果……否则如果……否则”。

```
if expression 1:
    code block 1
elif expression 2:
    code block 2
elif expression 3:
    code block 3
else:
    code block
```

含义：如果 `expression 1` 的结果为 `True`，则执行 `expression 1` 中的“程序块 1”，不再执行其他程序块；否则如果 `expression 2` 的结果为 `True`，则执行 `expression 2` 中的“程序块 2”；否则如果 `expression 3` 的结果为 `True`，则执行 `expression 3` 中的“程序块 3”；如果前面的表达式全为 `False`，则执行 `else` 子句中的程序块。

示例：

```
score = float(input("Please enter the student's score: "))
if score < 60:                   # If score < 60, execute this if block
    print("Failure")
elif score < 70:                 # Otherwise, if score < 70, execute this elif block
    print("Pass")
elif score < 80:                 # Otherwise, if score < 80, execute this elif block
    print("Medium")
elif score < 90:                 # Otherwise, if score < 90, execute this elif block
    print("Good")
else:                          # Otherwise (other cases), execute this else block
    print("Excellent")
```

```
Please enter student grade: 90.5
Excellent
```

## 2. `while` 语句

`while` 语句的格式如下：

```
while expression:
    code block
```

即当关键字 `while` 中的 `expression` 为 `True` 时，重复执行其中的程序块。

### 示例 1：计算 1 到 100 的和

```
i = 1
s = 0
while i <= 100:
    s = s + i     # equivalent to s += i            
    i += 1
print(s)
```

```
5050
```

### 示例 2：统计学生成绩平均分

```
total_score = 0
i = 0
score = float(input("Please enter the student's score:"))
while True:
    total_score += score
    i += 1
    score = float(input("Please enter the student's score:"))
    if score < 0:
        break                       # keyword break is used to break out of the loop
    
print('The average score is:', total_score / i)
```

```
Please enter student grade: 45.6
Please enter student grade: 56.7
Please enter student grade: 89.7
Please enter student grade: 78.6
Please enter student grade: -2
Average grade: 67.65
```

在循环的程序块中嵌套了一个 `if` 条件语句，如果条件语句表达式 `score < 0` 为 `True`，则执行其中的 `break` 语句。`break` 是 Python 的关键字，用于跳出循环语句，即不再执行循环语句。

## 3. `for` 语句

`for` 关键字也表示循环语句，意为迭代访问容器对象或可迭代对象中的每个元素。格式为：

```
for e in container:
    code block
```

表示迭代遍历容器对象 `container` 中的每个元素 `e`，并执行其中的程序块语句。

示例：

```
for ch in "hwdong":
    print(ch, end=",")
```

```
h,w,d,o,n,g,
```

依次迭代访问字符串中的每个元素，即每个字符，然后用 `print()` 函数输出字符 `ch`。

# 1.1.5 Python 常用容器类型

正如字符串是一些字符的容器一样，Python 提供了列表、元组、集合、字典等容器类型。

## 1. list (列表)

列表 `list` 是一组数据元素（对象）的有序序列。定义列表对象用一对左右方括号 `[ ]` 括起来，数据元素之间用逗号分隔。

示例：

```
a = [2, 5, 8]
print(a)
type(a)
```

```
[2, 5, 8]
list
```

列表中的数据元素可以是不同类型，甚至可以包含其他对象的列表对象：

```
my_list = [2, 3.14, True, [3, 6, 9], 'python']
print(my_list)
print(type(my_list))       # Print the type of my_list, that is, the list type
```

```
[2, 3.14, True, [3, 6, 9], 'python']
<class 'list'>
```

另一个示例：

```
a = [[1, 2, 3], [4, 5, 6]]
print(a)
```

```
[[1, 2, 3], [4, 5, 6]]
```

### 索引

与字符串一样，可以通过下标访问元素：

```
print("my_list[0]:", my_list[0])
print("my_list[3]:", my_list[3])
print("my_list[-2]:", my_list[-1])
```

```
my_list[0]: 2
my_list[3]: [3, 6, 9]
my_list[-2]: python
```

列表对象的元素可以通过下标修改：

```
print(my_list)
my_list[-2] = [8, 9]
print(my_list)
```

```
[2, 3.14, True, [3, 6, 9], 'python']
[2, 3.14, True, [8, 9], 'python']
```

即下标 `-2` 的元素值指向新对象 `[8, 9]`，如图 1-2 所示：

![](img/file204.png)

图 1-2 给列表元素赋值不同对象使列表元素指向不同对象

### 切片

可以使用 `[start:end:step]` 来访问列表对象按起始下标、结束下标、步长筛选出的子列表。这种访问列表对象的方式称为**切片**。

```
print(my_list)
print(my_list[2:4])
print(my_list[0:4:2])
```

```
[2, 3.14, True, [8, 9], 'python']
[True, [8, 9]]
[2, True]
```

`step` 的默认值为 1。如果不指定起始下标 `start`，默认为 0；如果不指定结束下标 `end`，默认为最后一个元素之后的位置。例如：

```
list_2 = my_list[:]  # all elements
print(list_2)
```

```
[2, 3.14, True, [8, 9], 'python']
```

返回所有元素的列表。**注意**：切片操作会创建新的列表对象。因此以下代码会输出不同的 `id` 值：

```
print(id(my_list))
print(id(list_2))
```

```
1535447525504
1535447326144
```

如果切片操作放在赋值语句的左边，表示修改切片对应的子列表内容：

```
print(my_list)
my_list[2:4] = [13, 9]
print(my_list)
```

```
[2, 3.14, True, [8, 9], 'python']
[2, 3.14, 13, 9, 'python']
```

修改后的列表如图 1-3 所示：

![](img/file205.png)

图 1-3 通过切片替换列表的部分内容

### `for` 遍历所有元素

与字符串一样，当然可以用 `for` 循环等访问列表对象中的元素。

```
for e in my_list:
    print(e, end=" ")
```

```
2 3.14 True [8, 9] python
```

甚至可以用 `for` 循环迭代遍历一个容器或可迭代对象来创建新的列表对象。

```
alist = [e**2 for e in [0, 1, 2, 3, 4, 5]]
print(alist)
```

```
[0, 1, 4, 9, 16, 25]
```

表示对 `[0, 1, 2, 3, 4, 5]` 的每个元素 `e` 计算 `e**2`，并用这些值创建一个列表对象。这种在 `[]` 中通过迭代计算值来创建新列表对象的公式称为**列表推导式**。也可以包含更复杂的计算公式，如包含条件语句：

```
alist = [0, 1, 2, 3, 4, 5]
alist = [x ** 2 for x in alist if x % 2 == 0]
print(alist)
```

```
[0, 4, 16]
```

# Python 内置数据结构与函数

## 内置函数 `range(n)`

Python 的内置函数 `range(n)` 是一个**迭代器对象**，它生成 0 到 n 之间的整数（不包括 n）。迭代器对象不是容器，但你也可以使用 `for` 来遍历该对象的元素。
