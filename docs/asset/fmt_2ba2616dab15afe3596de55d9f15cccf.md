
# Python 的开发非常活跃

仅在大约 3 个月的时间里，我写这本书的时间里，就有 2 次语言的完整更新（发布的版本是 2.2 和 2.3）。但不仅仅如此，还有对后者的更新而不改变版本号。现在，2003 年 10 月 16 日，版本 2.3.2 是当前的。在版本 2.4 中，应该会有相当多的变化，因此 Python 可以做更多的事情（例如处理 64 位字符代码）。

## Python 文档指南

如果你完全是编程新手，理解编程语言文档是如何混乱的可能会很困难。但一旦你能弄明白，通常和经常从语言文档中获得帮助要比在邮件列表上为特定函数请求帮助容易得多。

Python 的文档可以在网上找到，网址为 `http://www.python.org/doc/`。在这里你也可以找到各种主题的指南和 HowTo。文档分为 7 个类别：模块概览、教程、库参考、Macintosh 参考、语言参考、语言扩展和 Python / C API。

### 类别说明

#### Python 文档概览

##### Module overview

以下是 Python 发行版中包含的所有模块的概览。每个模块也有相应的文档。

##### Tutorial

这里提供了关于 Python 最基本使用的全面教程。如果你已经会编程，只是还不了解 Python，这是一个很好的起点。

##### Library reference

对 Python 中最常用的库进行回顾，并提供比模块概览中更详尽的使用示例。

##### Macintosh reference

回顾特定于 Macintosh 的库。

##### Language reference

语言使用和结构回顾（语法、函数、类等）

##### Extensions and embedding

关于如何使用 C / C++ 扩展 Python、在其他应用程序中嵌入 Python 等的指南。

##### Python / C API

对 Python 的 C API 的回顾，该 API 使 C 程序员能够在其应用程序中使用 Python。

## Language Reference GUI and IDLE - 它是什么？

GUI 是 Graphic User Interface 的缩写，是部分创建虚拟窗口、按钮、菜单等的程序。这允许用户通过点击等来调用与所述元素关联的函数，其目的可以是向文本框发送文本、检索文件或将其发送到外部存储设备（如硬盘）、绘制图形等等。GUI 组件的代码可在 Python 的 `Tk` 库中见到。来自 `Tk` 库的窗口的代码可以通过基本窗口顶部的单词 `Tk` 来识别。

```python
>>> from Tkinter import Label
>>> childAfLabel = Label()
```

由于如前所述，`Tk` 中存在 GUI 组件的基本模型，工匠 `Tkinter` 可以发出 `Tk`，声明必须提供基本窗口构造的代码以构建 `Label()` 的副本，在本例中我选择将其命名为 `childrenAfLabel`，因为与其他孩子一样，它有其起源，从中它在母亲中继承，该术语也用于其他丹麦计算机语言书籍中。在英语中，母亲被称为父类 parent。在 Python 中，也使用术语主类或基本类。

### Immediate mode

从旧的 DOS 中，你可能知道提示符 `dose c:`。在 Python 中，`>>>` 用作相应的清晰消息。Python 处于 Immediate 或也称为交互模式的消息。从这里开始你的 Python 编程，但当然，成熟的 Python 程序员也会返回并使用，例如。当测试新的程序片段时。

### Comments

当你编程时，不时需要插入注释 - 程序的一部分，你和其他人可以阅读，但计算机语言会跳过。在 Python 中，`#`（井号 - 在丹麦语中称为花园门或牛排符号）标记。注释从花园门开始并延续程序行。

**Ex. 1:**

```python
>>> # Python runs over comments
>>> print "Comments are for you and not for the computer."
```

Comments are for you and not for the computer.

也可以打印井号，如果它是文本字符串的一部分。

**Ex. 2:**

```python
>>> print "Here we print a hash sign #"
```

Here we print a hash sign #

在此示例中，没有注释。牛排符号在这里是文本字符串的一部分。Python 应该喜欢响应它而不是绕过它。请注意，井号在这里被打印出来，而在它发挥其正确作用的示例中则没有。

注释在引号中 par 字符串也可以用 3 个引号（单引号或双引号）括起来。

**Ex. 1:**

```python
>>> print """
Name: The cliff island Bornholm
Population: 44.500
"""
```

Name: The cliff island Bornholm

Population: 44,500

### Arithmetic operators

加法 `+` ex: `3 + 4 = 12`

减法 `-` ex: `3 - 4 = -1`

乘法 `*` ex: `3 * 4 = 12`

指数表示 `**` ex: `3 ** 4 = 81`

除法 `/` ex: `3/4 = 0`（向下舍入到最接近的整数）

除法 `//` ex: `3 // 4 = 0`（向下舍入到最接近的整数）

取模 `%` ex: `3.0 % 4.0 = 0.75`

**危险：注意整数除法**

```python
>>> 25/24
1
```

25 除以 24 应该得到 1.0416666666666667，但 Python 自动向下下降到最接近的整数，在本例中为 1。

```python
>>> 25 / 24.0
1.0416666666666667
```

### Variables

变量是指向计算机内存（RAM）中多个地址的指针，其中数据，可能有多种东西，例如。数字和文本字符串被放置。

#### 变量声明

```python
>>> x = y = z = 0
>>> x
0
>>> y
0
>>> z
0
```

注意：在 Python 中，使用 `==` 表示等于，使用 `=` 表示赋值。

#### 变量可以被覆盖

```python
>>> e = 1000 # global variable variable
>>> def nix():
...     global e
...     e = 25
...
>>> e
1000
>>> nix()
>>> e
25
```

#### 变量地址

```python
>>> a = 25
>>> type(a)
<type 'int'>
>>> a = 12.4
>>> type(a)
<type 'float'>
```

变量在 RAM 中的地址可以用 `id` 找到

```python
>>> a = 12.4
>>> id(a)
136095956
```

### Boolean expressions / variables

布尔表达式/变量可以取/赋 2 个值且仅 2 个。这 2 个值是 true（真）和 false（假）。

**Ex. 1:**

```python
>>> 2 == 3
0
>>> 2 == 2
1
```

### Write interactively

在交互模式下，数字可以用 2 个不同的函数输入：`raw_input`，其中数字作为文本接收，以及 `input` 将数字作为数字接收。

### Scripts

如果以及当你需要在 Python 中开发更大的项目时，你需要将你的 Python 代码保存为可以反复使用的单独文件。

在 Linux 中，Python 脚本可以通过在程序的第一行插入 `#!/usr/bin/env python` 使其直接可执行。

脚本可以通过以下命令分配可执行模式或权限：

```bash
$ chmod +x myscript.py
```

### If, elif and else

```python
>>> def findMax(a, b, c):
...     max = a
...     if b > a:
...         max = b
...     if c > b:
...         max = c
...     return max
...
>>> findMax(37, 2 * 19, 43)
43
```

### Function definition and call

```python
>>> def function():
...     a = 4 * 5
...     return a
...
>>> function()
20
```

带参数的函数：

```python
>>> def f(a):
...     return a * 1.25
...
>>> f(75)
93.75
```

### Lists

列表是零到多个相关空间的变量。其方括号知道列表。

```python
>>> list = []
>>> list.append("Ypnasted")
```

切片：

```python
>>> l = [1,2,3,3,4,5,6,7,8,9]
>>> print l[0]
1
>>> print l[0:4]
[1, 2, 3, 3]
```

### Tuples

元组由逗号分隔的 anal 值组成。

```python
>>> t = 1,2,3,4,5
>>> t
(1, 2, 3, 4, 5)
```

### Dictionary

```python
>>> dictionary = {}
>>> postal_codes = {"Rønne": 3700, "Allinge": 3770}
```

### Escape sequences

- 换行
- 水平制表符
- 回车

### Number system

#### 十六进制和八进制数

在 Python 中，十六进制数以前导零后跟 `x` 指定，并以十六进制数字结尾，例如。`0x49` 对应于 `9 + 4 * 16 = 73` 在我们正常的 10 进制系统中。

```python
>>> for i in range(0,9):
...     print "10 i", i, ". is:", 10 ** i
...
```

打印十六进制数：

```python
>>> for i in range(0,17):
...     print hex(i)
...
```

```python
>>> a = 0x49
>>> a
73
```

```python
>>> "x41", chr(65)
('A', 'A')
```

## PYTHON 数据结构

在编程中，'数据结构'是一种组织数据的结构。数据结构的选择很重要，因为它们对性能有不同的意义，并且根据计划使用的算法而表现不同。数据结构是一种抽象描述，与“数据类型”不同。数据类型可能是例如 `Integer`、`String` 或 `boolean`。它具有明确的意义，而数据结构描述的是未定义的东西，例如列表或数组。

在不同的类别中有许多不同的数据结构。我们有“线性数据结构” (`List`, `Stack`, `Queue`, 等)。另一个在编程中占有重要地位的结构类别是 "`Tree`" 。它们比例如 `Stack` 稍微复杂一些。许多数据结构已经内置于编程语言中（例如 `Python` 中的 `list`），并且一些现成的模块和库已实现并准备好该结构。尽管如此，了解它们“内部”是如何工作的仍然很重要。有三种不同的数据结构。

- `Stack` (Linear Data Structure)
- `Queue` (Linear Data Structure)
- `Linked List` (Linear Data Structure)

## 先决条件

你可以在 Python 和面向对象方面学习基础知识。你已经完成了异常练习。

### 栈

栈是一种长数据结构，就像它听起来一样，像一个栈或堆栈。想象一个盘子堆，其中一个盘子代表一个对象、变量或你存储的任何东西。为了处理“存取”操作，你从顶部开始工作。该方法称为“LIFO”（后进先出）。栈包含相同的数据类型。

通常使用一组特定的方法：

1. `.push()`（添加）
2. `.pop()`（删除）
3. `.peek()`（显示顶部内容而不改变栈）
4. `.is_empty()`（根据栈是否为空返回 True / False）
5. `.size()`（返回栈中元素的数量）

一个具有指定座位数目的栈。栈的实现可以如下所示：

```python
class Stack:
    def __init__(self):
        self.items = []
    def is_empty(self):
        return self.items == []
    def push(self, item):
        self.items.append(item)
    def pop(self):
        try:
            return self.items.pop()
        except IndexError:
            return "Empty list."
    def peek(self):
        return self.items[len(self.items) - 1]
    def size(self):
        return len(self.items)
```

使用栈可以如下进行：

```python
>>> myList.pop()
'Empty list.'
>>> myList.size()
0
```

VisuAlgo Stack Queue

### 队列

队列是一种线性数据结构，让人联想到栈。不同之处在于队列两端都是开放的。一端用于添加元素，另一端用于移除元素。该方法称为“先进先出”。

通常使用的方法有：

1. `.enqueue()`（添加）
2. `.dequeue()`（删除）
3. `.peek()`（显示顶部内容而不改变队列）
4. `.is_empty()`（根据队列是否为空返回 True / False）
5. `.size()`（返回队列中元素的数量）

一个没有指定位置数量的队列。队列的实现可能如下所示：

```python
class Queue:
    def __init__(self):
        self.items = []
    def is_empty(self):
        return self.items == []
    def enqueue(self, item):
        self.items.insert(0, item)
    def dequeue(self):
        try:
            return self.items.pop()
        except IndexError:
            return "Empty list."
    def peek(self):
        return self.items[len(self.items) - 1]
    def size(self):
        return len(self.items)
```

使用队列：

```python
>>> from queue import Queue
>>> myList = Queue()
>>> myList.is_empty()
True
>>> myList.enqueue("Tiger")
>>> myList.enqueue("Lion")
>>> myList.enqueue("Moose")
>>> myList.is_empty()
False
>>> myList.dequeue()
'Tiger'
>>> myList.peek()
'Lion'
>>> myList.enqueue("Godzilla")
>>> myList.dequeue()
'Lion'
```

VisuAlgo Stack Linked list

对于队列和栈，我们都使用了 Python 内置的列表：用于存储值，因此到目前为止我们只制作了 Python 列表的特殊版本。想法是我们不应该在不自己构建整个数据结构的情况下使用列表。为了成功，我们将使用节点并构建自己的链表。队列和栈也只是链表的特殊版本。

我们可以把一个常规的列表 / 数组想象成下面的图片。数组在内存中以位的形式存储，在该位中，值一个接一个地排列。然后我们不需要知道每个值的位置，只需要知道数组即可。

![Array in memory](img/image2155.jpg)

Array in memory

对于节点链表，我们不能假设值彼此相邻，而是分配到内存中的不同位置。因此，链表中的每个值都必须链接到下一个值。我们为此使用 `Node` 类。

![Linked list of nodes](img/image2162.jpg)

A linked list of nodes

最简单的 `Node` 类版本只包含两个属性，一个用于保存数据，一个用于跟踪下一个节点。我们将非空列表中的第一个节点称为头，列表的头部。要访问链表中的节点，必须有一个对头的引用。从头开始，我们可以通过跟随节点中的指针来访问剩余的节点。下一个节点的 `next` 属性包含 `None` 以表明它是最后一个节点。

图片中的列表称为单向链表。还有双向链表；然后每个节点都链接到前一个节点和后一个节点。另一种常见类型是循环链表。在循环链表中，最后一个节点链接到第一个。

![Circular Single Link List](img/image2169.jpg)

Circular Single Link List

然后当然还有循环双向链表，它们可以是有序的或无序的。有序列表会自动对列表进行排序。向列表添加新数据时，会搜索整个列表以找到正确的顺序位置。无序列表只添加到值，通常是列表的最后一个。

VisuAlgo Stack Nod class

然后我们应该看看节点类的代码可能是什么样子。需要的代码很少，因为我们只需要一个用于数据，一个用于下一个节点的属性。
