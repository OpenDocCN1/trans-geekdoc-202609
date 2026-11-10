
深受程序员喜爱，因其简洁的语法和可读的呈现方式，它提供了学习基础知识的机会，包括理解语法是什么以及变量和类型等基础主题。

## 2.8.1 Python 语法

Python 语法是指定义 Python 代码结构的规则集合。与其他编程语言不同，Python 强调可读性并使用缩进来定义代码块。

### Python 语法的关键特性

大小写敏感：Python 区分大小写，因此 `Variable` 和 `variable` 被视为两个不同的标识符。

缩进：Python 中缩进是强制性的，用于定义代码块。例如：
```
# Indentation
if True:
    print("This is indented")  # Proper indentation
```

注释：单行注释以 `#` 开头，而多行注释用三引号 (`'''` 或 `"""`) 包围。
```
# This is a single-line comment

"""
This is a
multi-line comment
"""
```

无分号：Python 不要求使用分号 (`;`) 来终止语句，使代码更简洁。

## 2.8.2 变量

Python 中的变量是用于存储数据的容器。与某些语言不同，Python 不要求显式声明变量类型；它会根据赋予的值自动确定类型。

### 定义变量

变量使用 `=` 运算符进行赋值。
```
# Defining Variables
x = 10        # Integer
name = "John" # String
price = 10.5  # Float
```

### 变量命名规则

* 必须以字母（a-z、A-Z）或下划线（`_`）开头。
* 不能以数字开头。
* 只能包含字母数字字符和下划线。
* 不能使用保留关键字，如 `if`、`else`、`for` 等。

示例
```
# Rules for Naming Variables
_age = 25
name = "Alice"
is_valid = True
```

## 2.8.3 数据类型

Python 支持各种数据类型，可大致分为基本类型和高级类型。以下是常用的数据类型：

### 数值类型

`int`：用于整数。
```
age = 25
```
`float`：用于小数。
```
price = 19.99
```
`complex`：用于复数。
```
z = 2 + 3j
```

### 文本类型

`str`：表示用引号（单引号或双引号）括起来的字符序列。
```
name = "John"
message = 'Hello, World!'
```

### 布尔类型

`bool`：表示 True 或 False。
```
is_active = True
is_logged_in = False
```

### 序列类型

`list`：一个有序集合，允许重复且可容纳多种数据类型。
```
fruits = ["apple", "banana", "cherry"]
```
`tuple`：与列表类似但不可变（不能更改）。
```
coordinates = (10, 20)
```
`range`：表示数字序列。
```
numbers = range(5)  # 0, 1, 2, 3, 4
```

### 字典类型

`dict`：存储键值对。
```
person = {"name": "Alice", "age": 25}
```

### 集合类型

`set`：一个无序的唯一项集合。
```
unique_numbers = {1, 2, 3, 4}
```
`frozenset`：集合的不可变版本。
```
mylist = ['apple', 'banana','orange']
x = frozenset(mylist)
```

### None 类型

`None`：表示空值或无值。
```
x = None
```

## 2.8.4 类型检查和类型转换

### 类型检查

使用 `type()` 函数检查变量的数据类型。
```
# Type Checking
print(type(10))          # <class 'int'>
print(type("Hello"))     # <class 'str'>
print(type(3.14))        # <class 'float'>
```

### 类型转换

Python 允许使用类型转换函数如 `int()`、`float()` 和 `str()` 将一种数据类型转换为另一种。
```
# Type Conversion
x = "10"
y = int(x)  # Converts string to integer
print(type(y))  # <class 'int'>
```

### 变量赋值
```
# Variable Assignment
a = 5
b = 3.2
c = "Python"
print(a, b, c)
```

### 基本数据类型
```
# Basic Data Types
x = 10          # int
y = 20.5        # float
z = "Hello"     # str
is_valid = True # bool
print(type(x), type(y), type(z), type(is_valid))
```

### 数据结构
```
# List
numbers = [1, 2, 3, 4, 5]
print(numbers[0])  # Accessing first element

# Dictionary
person = {"name": "Alice", "age": 30}
print(person["name"])  # Accessing value by key
```

基本语法、变量和数据类型是 Python 编程的基础。在此基础上，你将能够构建简单的程序，并随着时间的推移，继续学习更复杂的话题，如数据结构、函数和面向对象编程。

# 2.9 基本输入和输出操作

Python 提供了简单直观的方式来处理输入和输出（I/O）操作。这些操作允许用户与程序交互，要么提供输入，要么接收输出。

## 2.9.1 输入操作

Python 使用 `input()` 函数从用户获取输入。该函数从标准输入（键盘）读取一行并将其作为字符串返回。

### 语法
```
variable = input(prompt)
```
`prompt`：显示给用户的可选消息。

### 示例
```
name = input("Enter your name: ")
print("Hello, " + name + "!")
```

### `input()` 的特性

* 总是返回字符串。
* 你可以使用类型转换，例如 `int()` 或 `float()`，将输入转换为其他数据类型。

### 带类型转换的示例
```
age = int(input("Enter your age: "))
print("You are", age, "years old.")
```

## 2.9.2 输出操作

Python 使用 `print()` 函数进行输出。该函数将数据写入标准输出（控制台）。

### 语法
```
print(*objects, sep=' ', end='\n', file=sys.stdout, flush=False)
```

### 参数

* `objects`：要打印的值。多个值可以用逗号分隔。
* `sep`：值之间的分隔符（默认为空格）。
* `end`：输出末尾附加的字符串（默认为换行符）。
* `file`：指定输出文件（默认为标准输出）。
* `flush`：如果为 True，则强制立即写入输出。

### 示例
```
print("Hello, World!")
```

### 带参数的示例
```
print("Python", "is", "fun", sep="-", end="!!!\n")
```

输出
```
Python-is-fun!!!
```

## 2.9.3 格式化输出

Python 提供了多种格式化输出的方式，使其更易读。

### 使用 f-string（Python 3.6 及更高版本）
```
name = "Alice"
age = 25
print(f"My name is {name} and I am {age} years old.")
```

### 使用 `.format()` 方法
```
print("My name is {} and I am {} years old.".format(name, age))
```

### 使用 `%` 运算符
```
print("My name is %s and I am %d years old." % (name, age))
```

## 2.9.4 文件输入和输出

对于更高级的输入和输出，Python 允许从文件读取和向文件写入。

### 写入文件
```
with open("output.txt", "w") as file:
    file.write("Hello, File!")
```

### 从文件读取
```
with open("output.txt", "r") as file:
    content = file.read()
    print(content)
```

## 2.9.5 常见用例

### 获取用户输入
```
num1 = int(input("Enter first number: "))
num2 = int(input("Enter second number: "))
print("Sum:", num1 + num2)
```

### 以自定义格式显示结果
```
result = 3.14159
print(f"The value of pi is approximately {result:.2f}.")
```

### 处理文本文件
```
with open("data.txt", "r") as file:
    lines = file.readlines()
    for line in lines:
        print(line.strip())
```

在运行此程序之前，请确保 `data.txt` 文件存在于当前目录中。以下是示例 `data.txt` 文件内容的示例：
```
This is line 1
This is line 2
```

`strip()` 从字符串中移除前导和尾随字符（默认为空白字符）。

### 关键点

* 使用 `input()` 获取用户输入（总是返回字符串；如有需要请转换）。
* 使用 `print()` 显示输出，并可进行自定义选项（例如 `sep`、`end`）。
* Python 支持多种格式化输出的方式，包括 f-string 和 `.format()`。
* 文件 I/O 将输入/输出操作的范围扩展到控制台之外。

# 2.10 编写和运行 Python 程序

Python 是一种动态且用户友好的编程语言，允许开发者以多种方式编写和执行程序。因此，编写和运行 Python 程序是发挥该语言优势的核心。以下是编写和运行 Python 代码的多种方式概述。

## 2.10.1 编写 Python 程序
