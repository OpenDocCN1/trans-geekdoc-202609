
# 第 7 章 – Python 的内置函数

正如上一章所述，此处将讨论 Python 的内置函数。目的是介绍那些能让你提高生产力的函数。首先，函数为编程语言提供了生产力和结构。Python 拥有大量有价值的内置函数，使编程更简单、更快捷、更强大。

## `input()` 函数

项目通常需要输入，输入可能来自各种来源：控制台、鼠标点击、数据库、另一台计算机的存储或网络。由于控制台是收集输入最常用的方法，Python 为其用户提供了 `input()` 函数。该函数具有一个名为提示字符串的可选参数。调用 `input` 函数时，提示字符串将显示在屏幕上，程序流程将停止，直到用户输入一条信息。然后对该信息进行解析，`input()` 函数将用户的输入作为字符串返回。

为了演示，这里有一个收集姓名和年龄控制台输入的示例程序：

```
name = input("Are you Sam? ")
print("It’s my pleasure " + name + "!")
print("article " + age bracket + " the length, " + the person’s name + "!")
```

在保存代码之前，请检查要在第二行打印的字符串。你会注意到在 'you' 之后和双引号之前有一个空格。这个空格确保当执行打印指令时，'you' 和输入的 'name' 之间会有一个空间。第四行的打印指令中也可以看到类似的情况，'you're' 与 'age' 输入之间由一个空格隔开，'old' 与 'name' 输入之间也由一个空格隔开。

将代码保存为 `input_input.py` 并运行它。Python Shell 将在第一行显示字符串：

```
Are you Sam?
```

现在需要做出反应，程序将停止执行，直到获得关键字输入。让我们输入名字 Jeff 并按回车，看看会发生什么：

```
It's my pleasure, Sam!
You don’t mind telling your age.
```

程序现已继续执行下一个输入函数，并等待控制台输入。让我们输入 22 作为 Jeff 的年龄，看看程序接下来会做什么：

```
In this way, you're 22 years of age, Sam!
```

在获得控制台反应后，程序打印了最后的字符串。以下是 Python Shell 上的完整输出：

```
Are you Sam?
It's my pleasure, Sam!
Your age, if you don't mind
22
Thus, you're 22 years of age, Sam!
```

## `range()` 函数

Python 有一种逐渐高效的方法来处理一系列数字和算术运算，这就是使用其内置函数之一：`range()`。`range` 函数在 'for 循环' 中特别有用。

这是一个 `range()` 函数的例子：

```
>>> range(5)
range(0, 5)
```

上述语句 `range(5)` 创建一个迭代器，该迭代器从零开始生成数字，并以 4 结束（5-1）。要显示数字列表，可以使用命令 `list(range(n))`：

```
>>> list(range(5))
[0, 1, 2, 3, 4]
```

通过使用两个参数调用 `range()` 函数：`range(start, end)`，你可以更好地控制列表输出。

示例：

```
>>> range(5, 9)
range(5, 9)
```

显示列表：

```
>>> list(range(5, 9))
[5, 6, 7, 8]
```

上述 `range()` 的示例展示了步长为 1 的增长。通过引入第三个参数 'step'，你可以改变 Python 增加数字的方式。它可以是负数或正数，但绝不能为零。格式如下：`range(begin, end, step)`。

示例：

```
>>> range(10, 71, 5)
range(10, 71, 5)
```

调用 list，我们将看到这组数字：

```
>>> list(range(10, 71, 5))
[5, 20, 35, ...]
```

## `print()` 函数

Python 3 将 print 从语句变成了函数。因此，你必须始终将打印参数放在圆括号内。

示例：

```
print("This is Python 3 print function")
print(s)
print(5)
```

`print()` 函数可以打印括号内的任意数量的值；它们应由逗号分隔。例如：

```
a = 3.14
b = "age"
c = 32
print("a = ", a, b, c)
```

结果：

```
a = 3.14 age 32
```

Python shell 显示的值之间带有空格。

## `abs()`

`abs()` 函数返回单个数字的绝对值。它接受一个整数或浮点数作为参数，并始终返回一个正值。

示例：

```
>>> abs(-10)
10
>>> abs(5)
10
```

当复数用作参数时，`abs()` 函数返回其模：

```
>>> abs(3 + 4j)
5.0
```

## `max()`

`max()` 函数至少接受两个参数，并返回其中最大的一个。

示例：

```
>>> max(9, 12, 6, 15)
15
>>> max(-2, -7, -35, -4)
-2
```

## `min()`

`min()` 函数至少接受两个参数，并返回其中最小的一个。

示例：

```
>>> min(23, -109, 5, 2)
-109
>>> min(7, 26, 0, 4)
0
```

## `type()`

`type()` 函数返回给定参数的数据类型。

示例：

```
>>> type("This is a string")
<class 'str'>
>>> type(12)
<class 'int'>
>>> type(2 + 3j)
<class 'complex'>
>>> type(215.65)
<class 'float'>
```

## `len()`

`len()` 函数返回对象的长度或作为参数给定的列表中项目的数量。

示例：

```
>>> len("pneumonoultramicroscopicsilicovolcanoconiosi")
44
>>> s = ("winter", "spring", "summer", "fall")
>>> len(s)
4
```

## Python 内置函数列表

这是 Python 内置函数的列表：

```
abs() all() any() ascii() bin() bool() bytearray() bytes() callable() chr() classmethod() compile() complex() delattr() dict() dir() divmod() enumerate() eval() exec() filter() float() format() frozenset() getattr() globals() hasattr() hash() help() hex() id() __import__() input() int() isinstance() issubclass() iter() len() list() locals() map() max() memoryview() min() next() object() oct() open() ord() pow() print() property() range() repr() reversed() round() set() setattr() slice() sorted() staticmethod() str() sum() super() tuple() type() vars() zip()
```

本章结束时，你会注意到最后一部分只给出了语法而没有实际代码；这留给你作为一种作业形式去插入它们。如果有什么不明白的地方，请返回本章开头并运行你的代码。介绍了 Python 的这些内置函数后，你将在下一章学习 Python 编程中的条件语句。你必须记住，没有条件语句的语言是不存在的，即使是英语也有 'if' 和其他条件词。请跟我一起进入下一章吧！

