

# 用于生物医学应用的的机器学习

倒数第二个（第五个）如所示：`integerlist[3:-1]`。增量地看，切片并没有固定要求必须选取范围内的每个元素。另一种选项是使用步长符号，例如，选择范围内的每第二个元素：`integerlist[0:5:2]`。

## 1.4. 控制流

与许多编程语言一样，Python 提供了各种类型的语句来引导代码流，允许循环、中断（break）和条件语句。在书中，我们将考虑 `if`、`for` 和 `while` 语句，但也可能遇到 `except` 语句（指定异常处理程序和/或清理代码）或 `with` 语句（允许在运行代码块之前执行初始化和终止代码）。所有的控制流语句都有共同的形式。在伪代码中其形式如下：

该结构最核心的特征是：

- 确保在条件语句末尾放置冒号；
- 控制流语句之后紧跟缩进的语句。

在 Python 中，代码流几乎完全通过代码缩进来控制（见图 1.3）。这些缩进表示代码块属于流语句。然而，要跳出循环，只需将代码块恢复与之前的代码块对齐即可。这与 MATLAB（使用语句）以及 C/C++（将所有控制流放在括号内）不同。

### 1.4.1 练习题

- 在你的 IDE 中创建列表：`vowels=('a', 'b', 'c', 'd', 'e')`
- 你将如何索引字母 'd'？
- 从 'b' 到 'd' 进行切片（包含两端）；
- 向列表添加字母 'f'。
- 下面代码的输出是什么？

```python
b = "Introduction to Python"
print(b[3:7])
```

> 9 代码、练习题和答案可以在 github.com/MachineLearningBiomedical-Applications/notebooks 获取。

# Python 编程

主
(块 #1)

缩进

For 循环
(块 #2)

If 语句
(块 #3)

```python
# doing some coding ...
units=[1,2,3,4,5]
total=0
for number in units:
    sq=calculate_square(number)
    print(numbers)
    total+=number
    if number < 3:
        print('{}'.format(number))
    print('the square of {} is {}'.format(number,sq))
print('the total is {}'.format(total))
```

回到主程序 (块 #1)

1 is less than 3
square of 1 is 1
2 is less than 3
square of 2 is 4
square of 3 is 9
square of 4 is 16
square of 5 is 25
total is {format(total)

```

图 1. 使用缩进控制流。

## 3. 这段代码哪里错了？

```python
a = "Introduction to Python"
a[2]="b"
```

### 1.4.2 调试

探索缩进错误提供了一个有用的框架，用于突出 Python 的异常处理和错误消息，因为如果之前的代码示例包含错误且不小心删除了循环中间的缩进，Python 解释器将抛出 `IndexError` 错误（图 1.4），标亮错误行，并使用 `^` 符号标明行内位置。通常情况下，Python 的错误消息应该是相当自解释解释的。然而，有时你会遇到你不理解的消息。在这种情况下，建议求助于在线支持论坛，如 Stack Overflow.¹10

## 1.5. 条件 (if) 语句

从 `if` 开始，让我们依次查看每个类型控制流的结构。在伪代码中，Python 的 `if` 语句遵循以下形式：

```python
if condition:
    statement
    statement
```

¹10 https://stackoverflow.com/

# 用于生物医学应用的机器学习

| 行 | 代码 | 备注 |
| :--- | :--- | :--- |
| 1 | #doing some coding .... | |
| 2 | units=[1,2,3,4,5] | |
| 3 | | |
| 4 | total=0 | |
| 5 | for number in units: | |
| 6 | calculate square of number | |
| 9 | #sum numbers | |
| 10 | total+=total_number | 修改的行 |
| 11 | if number < 3: | 错误行 |
| 12 | print('{} is less than 3'.format(number)) | |
| 13 | | |
| 14 | print('the square of {} is {}.'.format(number,sq)) | |
| 15 | print('the total is {}.format(total)), line 11 | |
| 16 | if number < 3: | |
| | IndentationError: unexpected indent | 位置在 line=5 |

**图 1.4** 调试。

其中条件语句必须求值为布尔值（True/False），但其他限制很少。一些示例包括：

BMI=27

```python
if BMI > 25.0:
   print('This person is overweight')
```

或者 name='John'

```python
if name=='John':
   print("This person's name is John ")
```

所有的条件语句形式（在第 1.2.3 节“布尔运算符”中描述）都可以通过 `is` 使用。也可以通过使用 `and` 或 `or` 使用组合条件：

```python
a=10
b=12
```

```python
if a < 15 and b > 10:
   print('run the following block of code')
```

