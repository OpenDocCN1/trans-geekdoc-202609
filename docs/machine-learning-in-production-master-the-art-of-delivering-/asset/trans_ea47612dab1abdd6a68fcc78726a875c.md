

## 安装代码编辑器

可以选择以下任意一种代码编辑器；不过，首选的是 Visual Studio Code：

Visual Studio Code (https://code.visualstudio.com)

Sublime Text (https://www.sublimetext.com)

Notepad++ (https://notepad-plus-plus.org/downloads/)

## Hello World！

Python 是一种具有动态语义的解释型、面向对象的高级编程语言。其简单易学的语法强调可读性，从而降低了程序维护成本。Python 支持模块和包，鼓励模块化编程和代码重用。它是在 OSI 批准的开源许可证下开发的，可免费用于分发，甚至可用于商业用途。Python 软件包索引 (PyPI) 为 Python 托管了数千个第三方模块。

打开终端并键入 python 以打开 Python 控制台。

现在你已在 Python 控制台中。

### 示例：1.1 Python 中的 Hello world

```
1. print("Hello World")
2. Hello World
```

要退出控制台，可以使用：

```
1. exit()
```

## 执行 Python 文件

让我们创建一个名为 hello_world.py 的文件，并将 print("Hello World") 添加到其中。

现在，在终端中运行该文件：

```
python hello_world.py
```

你应得到以下输出：

Hello World

## 数据结构

数据结构无非是将数据以特定方式存储在内存中并进行管理，以便以后能够轻松访问和修改。Python 自带一套全面的数据结构，它们在编程中起着重要作用，因为这些结构可重用、易于访问且易于管理。

### 常见数据结构

本节将学习一些常见的数据结构。

### 数组

数组是同类项的集合。在单个数组中可以使用相同的数据类型。

### 示例：1.2 数组数据类型

```
1. import array as arr
2.
3. my_array = arr.array("i", (1, 2, 3, 4, 5))
4.
5. print(my_array)
6. array('i', [1, 2, 3, 4, 5])
7.
8. print(my_array[1])
9. 2
```

### 字典

字典定义为用逗号分隔的 **键:值** 对，并用花括号括起来。

### 示例：1.3 字典数据类型

```
1. my_dict = {'name': 'Adam', 'emp_id': 3521, 'dept': 'Marketing'}
2. print(my_dict['name'])
3. Adam
```

### 列表

它是用方括号括起来的异构项集合。在列表中可以使用相同或不同的数据类型。

### 示例：1.4 列表数据类型

```
1. my_list=['apple', 4, 'banana', 6]
2. print(my_list[0])
3. apple
```

### 集合

集合是用花括号括起来的唯一（非重复）元素集合。集合可以包含异构元素。

### 示例：1.5 集合数据类型

```
1. my_set = {3,5,6}
2. print(my_set)
3. {3, 5, 6}
```

```
1. my_set = {1, 2.0, (3,5,6), 'Test'}
2. print(my_set)
3. {1, 2.0, 'Test', (3, 5, 6)}
```

### 字符串

字符串用于存储文本数据。它可以用单引号 ('') 或双引号 ("") 表示。

### 示例：1.6 字符串数据类型

```
1. print('The cat was chasing the mouse')
2. The cat was chasing the mouse
```

### 元组

元组是用圆括号（可选）包围的元素集合，且是不可变的，即无法更改。

### 示例：1.7 元组数据类型

```
1. my_tuple_1 = ('apple', 4, 'banana', 6)
2. print(my_tuple_1[0])
3. apple
```

元组可以在没有圆括号的情况下声明，如下所示：

```
1. my_tuple_2 = 1, 2.0, (3,5,6), 'Test'
2. print(my_tuple_2[0])
3. 1
```

## 控制语句和循环

Python 有几种控制语句和循环。让我们来看看它们。

### if...else

if 语句在指定条件为真时执行一段代码。而 else 语句在指定条件为假时执行一段代码。此外，如果第一个条件为假，可以使用 elif（else if）语句来检查新条件。

语法：

```
if condition1:
    Code to be executed
elif condition2:
    Code to be executed
else:
    Code to be executed
```

### 示例：1.8 if...else 控制语句

```
1. x = 26
2. y = 17
3.
4. if(x > y):
5.     print('x is greater than y')
6. elif(x == y):
7.     print('x and y are equal')
8. else:
9.     print('y is greater than x')
10.
11.x is greater than y
```

### for 循环

当你想遍历字符串、列表、字典或元组等序列或可迭代对象时使用它。它会执行一定次数的代码块。

语法：

```
for val in sequence:
Code to be executed
```

### 示例：1.9 for 循环

```
1. num = 2
2. for i in range(1, 11):
3.     print(num, 'X', i, '=', num*i)
4.
5. 2 X 1 = 2
6. 2 X 2 = 4
7. 2 X 3 = 6
8. 2 X 4 = 8
9. 2 X 5 = 10
10. 2 X 6 = 12
11. 2 X 7 = 14
12. 2 X 8 = 16
13. 2 X 9 = 18
14. 2 X 10 = 20
```

在前面的示例中，range() 函数使用 start、stop 和 step 参数生成一组连续的数字。

### while 循环

当你想无限期执行一段代码直到满足指定条件时使用它。此外，如果第一个条件为假，可以使用 else 语句执行一次代码块。

语法：

```
while condition:
Code to be executed
```

### 示例：1.10 while 循环

```
1. num = 1
2. while num <= 10:
3.     if num % 2 == 0:
4.         print(num)
5.     num = num + 1
6.
7. 2
8. 4
9. 6
10. 8
11. 10
```

## pass 语句

在 Python 中，pass 语句充当占位符。如果你计划在循环、函数定义、类定义或 if 语句中稍后添加代码，可以编写 pass 以避免任何错误，因为它什么也不做。它允许开发人员稍后编写逻辑或条件，并继续执行剩余代码。

语法：

```
if condition:
pass
```

### 示例：1.11 pass 语句

```
1. num = 10
2. if num % 2 == 0:
3.     pass
```

## 函数

开发人员使用函数来多次执行相同的任务。函数是一段可以接受参数、执行某些操作并返回值的代码。Python 使开发人员能够使用预定义或内置函数，也可以编写用户定义的函数来执行特定任务。

### 示例：1.12 预定义或内置函数

```
1. print("Hello World")
2. Hello World # Output
```

### 示例：1.13 用户定义函数

```
1. a = 5
2. b = 2
3.
4. # Function definition
5. def add():
6.     print(a+b)
7.
8. # Calling a function
9. add()
10.
11. # Output
12. 7
```

## 面向对象编程 (OOP)

Python 是一门面向对象的语言，因此 Python 中的一切都是对象。让我们来理解其关键概念及其重要性：

**类：** 类充当对象的模板。它使用 **class** 关键字定义，就像在创建新函数时使用 **def** 关键字一样。Python 类包含对象和方法，可以使用句点 (.) 访问它们。

**对象：** 对象是类的实例。它描述了类的结构，包含类变量、实例变量和方法。

**方法：** 简单来说，它是在创建类时定义的函数。

**__init__：** 为了通过赋值自动初始化数据成员，在创建类的实例时应使用 **__init__** 方法。每次创建类的对象时都会调用它。其用法等同于 C++ 和 Java 中的构造函数。

**self：** 它帮助我们访问类的方法和属性。你可以随意命名；但根据惯例和可读性，最好将其声明为 self。

### 示例：1.14 类定义

```
1. class Multiply:
2.     def mul(self):
3.         result = self.num1 * self.num2       Class definition
4.         return result
5.
6.     def __init__(self,num1,num2):
7.         self.num1 = num1
8.         self.num2 = num2
9.
10.   a = Multiply(5,6)
11.             Passing parameters to class
12.   a.mul()            Calling method of class
13.   30
```

> 注意：遵循变量、函数和方法的标准命名约定。例如：
> * 对于变量、函数、方法、包和模块：my_variable
> * 对于类和异常：MyClass
> * 对于常量：MY_CONSTANT

## 数值 Python (NumPy)

简单来说，它是一个数组处理包。NumPy 是 Numerical Python 的缩写。默认情况下，NumPy 数组的数据类型由其元素定义。在 NumPy 中，数组的维度称为秩；例如，2-D 数组表示秩为 2 的数组。

NumPy 因其速度而广受欢迎。在处理大型数据集时，使用 NumPy 会体会到其中的差别。

你可以使用 pip 安装 NumPy 包：

```
pip install numpy
```

### 示例：1.15 NumPy 数组

```
1. import numpy as np
2. # Rank 0 Array (scalar)
3. my_narray = np.array(42)
4. print(my_narray)
5. 42
6.
7. print("Dimension: ", my_narray.ndim)
8. Dimension: 0
9.
10.   print("Shape: ", my_narray.shape)
11.   Shape: ()
12.
```
