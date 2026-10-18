

## [4.8 Python 中的输入和输出](#contents.xhtml#rsec4_8)

内置的 `input()` 函数用于从键盘获取用户输入。括号内的参数用于提示键盘输入。输入函数会自动识别用户输入的是字符串、数字还是列表。但是，当输入被输入时，首先将其转换为字符串。即使是整数值，也会通过类型转换转换为整数。

![](images/list4_14.jpg)

假设用户输入了 abc 作为名称。

输出：Hello abc

产生输出的方法是使用 `print()` 函数，传递零个或多个用逗号分隔的表达式。不带参数的打印，即 `print()` 是为了换行。默认情况下，Python `print()` 函数以新行结束，即 `print()` 函数会自动换行。

![](images/list4_15.jpg)

输出：

one

two

## [4.9 列表](#contents.xhtml#rsec4_9)

列表是 Python 的一个强大功能。它们与数组相同。列表是一种用于声明序列的数据类型。列表是用方括号中用逗号分隔的项目声明的。要访问列表项，使用索引号。值得注意的是，列表可能包含不同类型的项目。列表可以包含字符串、整数以及对象。此外，列表在声明后仍可更改。

![](images/list4_16.jpg)

输出：Banana

![](images/list4_17.jpg)

输出：

22, ‘Banana’, 5, 6

22, ‘Banana’, 5

5

**注意：** 元组与列表相同，区别在于元组是不可变的，即声明后不能更改。

## [4.10 字典](#contents.xhtml#rsec4_10)

Python 字典具有键和值，并用花括号编写。但是，字典中的键应该是唯一的，而值可以相同。要访问任何项，请在方括号内使用键名。

![](images/list4_18.jpg)

输出：10

## [4.11 Python 条件和 if-else](#contents.xhtml#rsec4_11)

Python if-else 语句与逻辑条件一起使用，例如- 等于、不等于、小于等于、大于等于、大于和小于。if 语句使用 `if` 关键字指定。

![](images/list4_19.jpg)

输出：value of b is greater than a

**关键点** Python 使用缩进来定义作用域

此外，`elif` 关键字用于检查如果前一个条件不为真，则尝试此条件，而 `else` 在任何前面的条件为假时执行。greater than equal to, greater than, and less than。elif 语句使用 `elif` 关键字指定。

![](images/list4_20.jpg)

输出：value of b is greater than a

## [4.12 循环](#contents.xhtml#rsec4_12)

通常，任何编程语言的语句都是按顺序执行的。但是，可能存在需要执行不同路径的情况。循环块允许执行一个或多个语句多次。Python 支持两个循环命令：

*   While 循环

*   For 循环

**While 循环**：While 循环用于执行语句或语句块，直到给定条件满足。当语句变为假后，while 之后的第一个语句将被执行。

![](images/list4_21.jpg)

输出：

0

1

2

3

4

Goodbye

While 也可以与 else 语句一起使用

![](images/list4_22.jpg)

输出：

0

1

2

3

4

Goodbye

**For 循环**：在 Python 中，for 循环用于顺序遍历，例如，列表或数组。

![](images/list4_23.jpg)

输出：

apple

mango

banana

![](images/list4_24.jpg)

输出：

0,1,2,3,4

## [4.13 Python 中的函数](#contents.xhtml#rsec4_13)

函数是一段接受一些输入、执行一些计算并产生输出的语句块。基本上，函数用于将重复执行的任务组合在一起。函数在被调用时执行。Python 中有一些内置函数，例如 `print()`，也可以使用 `def` 关键字创建函数。要调用函数，请使用该函数的名称，后跟一个括号。

![](images/list4_25.jpg)![](images/list4_26.jpg)

输出：

Odd

Even

## [4.14 Python 中的类和对象](#contents.xhtml#rsec4_14)

如前所述，Python 是一种面向对象的语言。类类似于对象构造函数或创建对象的蓝图，而对象是带有实际值的类的副本。类便于将数据和功能捆绑在一起。每个类都有自己的数据成员和成员函数，可以使用对象访问。尽管如此，一个类可以有许多对象。类的属性始终是公共的，并使用点 (.) 运算符访问。要创建类，使用关键字 `class`。

![](images/list4_27.jpg)

输出：5

![](images/list4_28a.jpg)![](images/list4_28b.jpg)

输出：

animal

I am a animal

I am a dog

要创建现实生活中的应用程序，我们需要了解一个名为 `init()` 的特殊函数，它是用于创建类新实例的初始化方法。特别是，`init()` 方法用于在创建对象时为对象属性赋值。

![](images/list4_29.jpg)

输出：

John

36

## [4.15 Python 中的文件处理](#contents.xhtml#rsec4_15)

文件在磁盘上有一个位置，存储着一些信息。像 Java 和 C++ 一样，Python 也支持文件处理，并使用户能够通过读取和写入文件来处理文件。文件中的每行代码都包含一系列字符。此外，每行都以一个名为行尾 (EOL) 的特殊终止符结束，它告诉解释器新行已开始。大多数文件操作都是使用文件对象完成的。

### [4.15.1 `open()` 函数](#contents.xhtml#rsec4_15_1)

显然，在读取或写入文件之前，必须先打开它。要打开文件以进行读取或写入，使用 `open()` 函数。`open()` 函数创建一个文件对象，并接受两个参数，即文件名和模式。语法：

`open(filename; mode)`

mode 字段告诉如何打开文件。例如：

r: 仅打开文件以供读取

rb: 以二进制格式打开文件以供只读

w: 打开文件仅供写入

r+: 以二进制格式打开文件以同时进行读取和写入

wb: 以二进制格式打开文件以供只写

a: 打开文件以供追加

a+: 打开文件以同时进行追加和读取

如果指定名称的文件不存在，它将抛出 `FileNotFoundError` 错误。

### [4.15.2 `close()` 函数](#contents.xhtml#rsec4_15_2)

`close()` 方法关闭文件对象，并禁止对该文件执行任何进一步操作。

语法：

`fileObject.close()`

![](images/list4_30.jpg)

输出：

Name of the file: foo.txt

### [4.15.3 `read()` 函数](#contents.xhtml#rsec4_15_3)

此函数从打开的文件中读取一个字符串。

语法：

`fileObject.read([count])`

count 参数指定要从指定文件中读取的字节数。如果缺少 count 参数，文件将被读取直到文件末尾。

![](images/list4_31.jpg)

输出：

The first 10 characters from the file named foo.txt.

## [4.16 `write()` 函数](#contents.xhtml#rsec4_16)

此函数允许用户将字符串写入打开的文件。值得注意的是，write 函数不会隐式添加换行符，即字符串末尾。

语法：

`fileObject.write(string)`

![](images/list4_32.jpg)

输出：

Python is a high level language

Python follows OOPS concepts

## 活动

### 选择题

1.  如何在 Python 代码中插入注释？

    1.  \\ \*This is a comment\* \\

    2.  #This is a comment

    3.  “This is a comment”

    4.  None of these

2.  哪个不是合法的变量名？

    1.  abc

    2.  10abc

    3.  \_abc

    4.  abc\_abc

3.  以下 Python 表达式的值是多少？

    1.  9.0

    2.  9

    3.  4.0

    4.  4

4.  以下代码的输出是什么？

    x = 100

    y = 50

    print(x and y)

    1.  True

    2.  False

    3.  100

    4.  50

5.  在 Python 中输出 “hello world” 的正确语法是什么？

    1.  print(“hello world”)

