
```
>>> f(47, 48, 29)

47 48 29

>>> f(47, 48, 49, 50)

Traceback (most recent call last):

File "stdin>", line 1, in =

TypeError: f() takes at most 3 arguments (4)

>>>
```

这是另一个特性：函数的调用者可以提供所谓的“name=value”形式的关键字参数。如果函数中有一个具有匹配关键字的参数，则该参数将被设为 `value`。

- 如果调用者的调用者同时提供了位置参数和关键字参数，则所有位置参数必须在所有关键字参数之前。
- 关键字参数可以以任何顺序出现。
- 以下是一些使用关键字参数调用函数的示例。

```
>>> g(p0, p1, k0="K-0", k1="K-1")

...    print p0, p1, k0

>>> g(33,44)

33 44 K-0 K-1

>>> g(33,44,"K-9","beep")

33 44 K-9 beep

>>> g(55,66,k1="whirr")

55 66 K-0 whirr

>>> g(7,8,k0="click",k1="clank")

7 8 clank clank

>>>
```

# 额外位置参数

你可以这样声明函数，使其接受任何位置参数。要做到这一点，请在你的参数列表中使用“*name”形式的参数。

- 如果你使用这个特殊参数，它必须位于列表中所有位置参数和关键字参数之后。
- 当函数被调用时，该名称将绑定到一个元组 `tuple`，该元组包含调用者提供的任何位置参数，以及对应其他参数之外的参数。

这是一个此类函数的示例。

```
>>> def h(i, j=-99, *extras):

... print i, j, extras

...

>>> h(0)

0 -99 ()

>>> h(1,2)

1 2 ()

>>> h(3,4,5,6,7,8,9)

3 4 (5, 6, 7, 8, 9)

>>>
```

# 额外关键字参数

你可以这样声明函数，使其除了你声明的任何关键字参数外，还可以接受任意数量的关键字参数。

要做到这一点，将“**name”形式的参数放在你参数列表的最后。

当函数被调用时，该名称将绑定到一个字典 `dictionary`，该字典包含了传入的任何关键字类型参数，且这些名称与你函数的关键字类型参数不匹配。在该字典中，键是调用者使用的名称，值是调用者传递的值。

这是一个示例。

```
>>> def k(p0, p1, nickname='Noman', *extras, **extraKeys):

... print p0, p1, nickname, extras, extraKeys

>>> k(1,2,3)

1 2 3 () {}

>>> k(4,5)

4 5 Noman () {}

>>> k(1,2,nickname='Jack')

1 2 Jack () {}

>>> k(4,5,6,a=7)

4 5 Noman (6,) {'a': 7}

>>>
```

# 文档接口

Python 有一种首选的方法来记录函数。如果函数体的第一行是一个字符串，那么该字符串将与函数一起保存。通过使用 `f.__doc__` 这种表达式可以检索该字符串，其中 `f` 是函数名。

这是一个带有文档字符串的函数示例。

```python
def pythag(a, b):
    """返回边为 a 和 b 的直角形的斜边"""
    return (a*a + b*b)**0.5
```

```
>>> pythag(3,4)
5.0
>>> pythag(1,1)
1.414213562373095
>>> pythag.__doc__
'返回边为 a 和 b 的直角形的斜边'
```

当你开始构建复杂的程序时，应用这一总体原则至关重要：分而治之。换句话说，不要将你的程序构建为一个巨大的语句块，而是将其分成逻辑部分，再继续细分，直到部分足够小。

Python 有许多工具可以帮助你分而治之。在第 8 节“定义函数”中，我们学习了如何将一组语句封装成函数，以及如何调用该函数并检索结果。

## 使用 Python 进行科学计算和机器学习

早在在第 2.3 节“更多数学运算”中，我们就首次接触了另一个重要工具：Python 的模块系统。Python 没有内置计算平方根的函数，但有一个内置模块 `math`，其中包含一个计算平方根的 `sqrt()` 函数。

通常，模块是可以导入并在程序使用的函数包。你也可以创建自己的模块。让我们详细查看 Python 的模块系统。

- 在第 9.1 节“从模块导入项”中，我们学习如何从现有模块导入项。
- 第 9.2 节“导入整个模块”展示了使用模块项的方法。
- 第 9.4 节“构建你自己的模块”。

# 使用模块

在第 2.2 节“赋值语句”中，我们学习过有一个被称为“全局命名空间”的区域，Python 在存储你定义的变量的名称和值。

Python `dir()` 函数返回当前全局命名空间中定义的所有名称的列表。这是一个对话示例；假设你刚刚在对话模式下启动了 Python。

```python
>>> dir()
['__builtins__', '__doc__', '__name__']
>>> frankness = 0.79
>>> dir()
['__builtins__', '__doc__', '__name__', 'frankness']
>>> def oi():
    print "Oi!"

>>> dir()
['__builtins__', '__doc__', '__name__', 'frankness', 'oi']
>>> type(frankness)
<type 'float'>
```

# Python 2.7 编程教程 219

```python
>>> type(oi)
<type 'function'>
>>>
```

当 Python 启动时，总是会定义三个变量：`__builtins__`、`__doc__` 和 `__name__`。这些变量用于高级工作，我们现在不需要关心。

注意，当我们定义一个变量 `frankness` 时，下次调用 `dir()` 时，`frankness` 会出现在结果列表中。当我们定义一个函数 `oi` 时，它的名称也会被添加。注意，你也可以使用 `type(function)` 来查找任何已定义名称类型：`frankness` 的类型为 `float`，而 `oi` 的类型为 `function`。

现在让我们看看当我们将 `math` 模块导入到全局命名空间时会发生什么：

```python
>>> from math import *
>>> dir()
['__builtins__', '__doc__', '__name__', 'acos', 'asin', 'atan', 'atan2', 'ceil', 'cos', 'cosh', 'degrees', 'e', 'exp', 'fabs', 'floor', 'fmod', 'frankness', 'frexp', 'hypot', 'ldexp', 'log', 'log10', 'modf', 'oi', 'pi', 'pow', 'radians', 'sin', 'sinh', 'tan', 'tanh']
>>> sqrt(64)
8.0
>>> pi*10.0
31.415926535897931
>>> cos(0.0)
>>>
```

如你所示，我们定义的名称 `oi` 和 `frankness` 仍然在那里，但 `math` 模块所有的变量和函数现在都在全局命名空间中了，我们可以像使用 `sqrt()` 和 `pi` 那样使用它们。

通常情况下，这种形式的导入语句会将模块中的所有函数和变量复制到当前命名空间：

```python
from someModule import *
```

然而，你也可以选择要导入哪些项。使用这种形式的语句：

```python
from someModule import item1, item2, ...
```

其中关键字 `import` 后面跟着一个逗分隔分隔列表。

这是另一个例子。假设你刚刚启动了一个全新的 Python 会话，并且只想导入 `sqrt()` 函数和常量 `pi`：

```python
>>> dir()
['__builtins__', '__doc__', '__name__']
>>> math import sqrt, pi
>>> dir()
['__builtins__', '__doc__', '__name__', 'pi', 'sqrt']
>>> sqrt(25.0)
5.0
>>> cos(0.0)
Traceback (most recent call last):
File "stdin>", line 1, in <module>
NameError: name 'cos' is not defined
```

我们没有请求 `cos()` 函数，所以它不在全局命名空间中。

# 导入整个模块

某些模块内部包含几百个不同的项。在这种情况下，你可能不想让所有项弄乱你的全局命名空间。另一种导入模块的方法。这里是通用形式：

```python
import moduleName
```

该语句只向当前命名空间添加一个名称——模块本身的名称。然后你可以使用这种形式的表达式来引用该模块内的任何项：

```python
moduleName.itemName
```

这是一个示例，再次使用内置的 `math` 模块。假设你刚刚启动了一个新的 Python 会话，并且还没有向命名空间添加任何内容。

```python
>>> dir()
['__builtins__', '__doc__', '__name__']
```

```python
>>> import math
>>> dir()
['__builtins__', '__doc__', '__name__', 'math']
>>> type(math)
<type 'module'>
>>> math.sqrt(121.0)
11.0
>>> math.pi
3.1415926535897931
>>> math.cos(0.0)
1.0
```

如你所示，使用这种形式的导入只向命名空间添加一个名称，该名称的类型为 `module`。

我们还应该提到另一个的一个额外功能。如果你想导入整个模块 `$M_1$`，但你想用另一个名称 `$M_2$` 来引用它的内容，请使用这种形式的语句：

```python
import $M_1$ as $M_2$
```

一个示例：

```python
>>> dir()
['__builtins__', '__doc__', '__name__']
>>> import math as crunch
>>> dir()
['__builtins__', '__doc__', '__name__', 'crunch']
>>> type(crunch)
<type 'module'>
>>> crunch.pi
3.1415926535897931
>>> crunch.sqrt(888.888)
29.81422479287362
```

你可以将 Python 内置的 `dir()` 函数应用于模块对象，以查找其内部定义的名称：

```python
>>> import math
>>> dir()
['__builtins__', '__doc__', '__name__', 'math']
>>> dir(math)
['__doc__', '__file__', '__name__', 'acos', 'asin', 'atan', 'atan2', 'ceil', 'cos', 'cosh', 'degrees', 'e', 'exp', 'fabs', 'floor', 'fmod', 'frexp', 'hypot', 'ldexp', 'log', 'log10', 'modf', 'pi', 'pow', 'radians', 'sin', 'sinh', 'tan', 'tanh']
```

```python
>>> >>> treeFile.open('trees')
>>> for treeLine in treeFile:
...
    print treeLine.rstrip()
...
```

yew

oak

alligator juniper

与 `.readline()` 方法一样，当你以这种方式迭代文件的行时，这些行将包含换行符。如果上面的示例没有使用 `.strip()` 来修剪这些行，那么每行输出后面都会跟着一个空行，因为 `print` 语句会添加一个换行。

### 随机访问设备的文件定位

对于磁盘文件等随机访问设备，有一些方法可以让你找到文件中的当前位置，并移动到不同的位置。

- `F.tell()` 返回你在文件 `F` 中的当前位置。
例如，`F.seek(80, 1)` 将文件位置移动到文件起始之后 80 个字符处。
- `F.seek(N, 2)` 移动到相对于文件末尾 N 个字符的位置。例如，`F.seek(0, 2)` 将移动到文件末尾；`F.seek(-200, 2)` 将你的位置移动到文件末尾前 200 字节处。

```python
>>> treeFile = open ("trees")
>>> treeFile.tell()
0L
>>> treeFile.read(6)
'yew'noa'
>>> treeFile.tell()
6L
>>> treeFile.seek(1)
>>> treeFile.tell()
```

```python
1L
>>> treeFile.read(5)
'ew\noa'
>>> treeFile.tell()
6L
>>> treeFile.seek(1, 1)
>>> treeFile.tell()
7L
>>> treeFile.seek(-3, 1)
>>> treeFile.tell()
4L
>>> treeFile.seek(0, 2)
>>> treeFile.tell()
26L
>>> treeFile.seek(-3, 2)
>>> treeFile.tell()
23L
>>> treeFile.read()
'er\n'
```

## 写入文件

要创建一个磁盘文件，使用如下通用形式的语句打开文件：

```python
F = open (filename, "w")
```

第二个参数 `"w"` 指定写入权限。如果可能，Python 将创建一个同名的空文件。如果已存在同名文件，且你对它有写入权限，则现有文件将被删除。

要向你创建的文件写入内容，请使用此方法：

```python
F.write(s)
```

其中 `s` 是任何字符串表达式。

# 警告

你通过 `.write()` 方法发送到文件的数据在通过调用文件对象的 `.close()` 方法关闭它之前，可能不会真正出现在磁盘文件中。

这是由于一种名为“缓冲” `buffering` 的机制。Python 会累积你发送到文件的数据，直到达到一定的数量，然后它会通过写入操作将这些数据“刷新” `flush` 到物理文件中。Python 在你关闭文件时也会将数据刷新到文件。

如果你想确保写入到文件的数据在不关闭文件的情况下物理上确实存在于文件中，请对文件对象调用 `.flush()` 方法。

```python
>>> sports = open ("sportfile", "w")
>>> sports.write ( ('tennis\nrugby\nquoits\n')
>>> sports.close()
>>> sportFile = open ("sportfile")
>>> sportFile.readline()
'tennis\n'
>>> sportFile.readline()
'rugby\n'
>>> sportFile.readline()
'quoits\n'
','
```

这是一个演示 `.flush()` 方法作用的详细示例。

```python
>>> sporting = open('sports', 'w')
>>> sporting.write('golf\n')
>>> echo = open('sports')
>>> echo.read()
''
>>> echo.close()
>>> sporting.flush()
>>> echo = open('sports')
>>> echo.read()
'golf\n'
>>> echo.close()
>>> sporting.write('soccer')
>>> sporting.close()
>>> open('sports').read()
'golf\nsoccer'
```

# 面向对象编程

到为止，我们已经使用了 Python 的一些内置类型，如 `int`、`float`、`list` 和 `file`。

现在是时候探索 Python 更强大的功能了：创建你自己的类型。

这是一个大步，让我们从回顾编程语言的一些特性开始。

# 蜗牛赛技术简史

企业家 Malek 想要开发一种服务来帮助非营利组织筹资金。以下是蜗牛赛设计的方案：

![](img/e1ab17402154bec3fa9783fe234_0.png)

在比赛开始时，蜗牛们背上用可降解墨水写着的名字被放在起线上，Malek 开始计时。当每只蜗牛越过终点时，Malek 记录它们的时间。

Malek 想编写一个 Python 程序来打印比赛结果。我们将回顾 1960 年左右的编程。

# 标量变量

1960 年左右的语言是 FORTRAN。很多工作是使用标量变量完成的，即每个变量持有一个数字。假设我们刚刚进行了蜗牛赛，Judy 用了 87.3 分钟，而 Kyle 用了 96.6 分钟。我们可以用这些值创建 Python 变量：

```python
judy = 87.3
kyle = 96.6
```

为了找到胜利者，可以使用语句：
