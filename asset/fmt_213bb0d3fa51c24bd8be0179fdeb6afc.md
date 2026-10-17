
如果你喜欢阅读文档，最好的第三方文档出版物之一是 Doug Hellman 编写的 pymotw（“每周 Python 模块”），他的主页地址为：

`http://pymotw.com/2/`

> 注意：书中的 Python 脚本适用于 Python 2.7.5，尽管它们的大部分可能可能与 Python 2.6 兼容，但这些脚本需要经过某种程度的转换（例如 `print()` 命令的语法）才能与 Python 3 兼容。

# PYTHON 工具

Anaconda Python 分发版适用于 Windows、Linux 和 Mac，可以在此处下载：

`http://continuum.io/downloads`

Anaconda 非常适合如 NumPy 和 SciPy 等模块（将在第 2 章和第 4 章中讨论），如果你是 Windows 用户，Anaconda 看起来是更好的替代方案。

## easy_install 和 pip

当你需要安装 Python 模块时，`easy_install` 和 `pip` 都非常易于使用。

每当你需要安装 Python 模块时（书中有很多这样的模块），请使用以下语法运行 `easy_install` 或 `pip`：

```
easy_install <module-name>
pip install <module-name>
```

> **注意**：基于 Python 的模块更容易安装，而用 C 编写代码的模块通常更快，但在安装方面更困难。

`virtualenv` 工具允许你创建隔离的 Python 环境，其主页在此：

`http://virtualenv.org/en/latest/virtualenv.html`

`virtualenv` 解决了为不同应用程序保留正确依赖项和版本（间接地保留权限）的问题。如果你是 Python 初学者，现在可能不需要 `virtualenv`，但请记住这个工具。

另一个非常好工具是 IPython（曾获得 Jolt 奖），它的主页在这里：

`http://ipy.org/install.html`

IPython 的两个非常棒的功能是制表扩展和“?”

这里展示了制表扩展的一个示例：

```python
Python 2.7.5 -- Anaconda 1.6.1 (x86_64) -- (default, Jun 28
              2013, 22:20:13)
Type "copyright", "credits" or "license" for more
Information.
```

```
IPython 0.13.2 -- An enhanced Interactive Python.
? -> Introduction and overview of IPython's features.
%quickref -> IPython's own help system.
help
object? -> Details about 'object', use 'object??' for
              extra details.
```

```
[1] di divmod
%dirs dir divmod
```

在之前的会话中，如果你输入字符 `di`，IPython 将显示：

```
[1] di divmod
%dirs dir divmod
```

如果你在提示符下输入 `dir`，IPython 会显示：

```
[1] dir divmod
%dirs dir divmod
```

如果你已经达到了此处所学内容的极限，并希望获取关于 TensorFlow 1.x 的更深层次的技术知识，请考虑在本序言前面提到的推荐书籍，以及即将出版的关于 TensorFlow 2 的书籍。

书中出现的代码示例和图表可以通过发送邮件至出版者 `info@merclearning.com` 来获取。

本章将对 Python 进行快速介绍，并提供用于安装 Python 模块的工具，以及如何在 Python 中处理某些数据类型的示例。本章不包含任何关于 Python 的历史信息，也不包含诸如创建 Python 类、继承、线程或任何超出介绍性材料的主题。原因非常简单：本章的目的是为了让你熟悉足够的 Python 知识，以便你能够学习后续章节中的内容。

Python 中的多行语句可以使用换行符或反斜杠（`\"\\\"`）字符结束，如下：

```
total = x1 + \
x2 + \
x3
```

显然，你可以将 `x1`、`x2` 和 `x3` 放在同一行，没有理由使用三行独立的代码；但是，当你需要添加一组无法单行容纳的变量时，此功能就很有用了。

你可以通过使用分号（`;`）分隔每个语句来在一行内指定多个语句，如下：

```
a=10; b=5; print a; print a+b
```

上述代码段的输出在此处：

```
10
15
```

注意：在 Python 中不建议使用分号和续行符。

Python 允许单引号（`''`）、双引号（`\"\"`）和三引号（`\"\"\"`）

```
word = 'word'
line = "This is a sentence."
para = """This is a paragraph. This paragraph contains
more than one sentence."""
```

以字母“r”（代表“raw”，原始）开头的字符串字面量会将所有内容视为字面字符，并“转义”元字符的含义，如下：

```
a1 = r'\n'
a2 = r'\r'
a3 = r'\t'
```

```
print('a1:', a2, 'a3')
```

上述代码块的输出在此处：

```
a1: \n a2: \r a3: \t
b1: ' ' b2: ""
```

你可以在一对双引号中嵌入单引号（反之亦然），以便显示单引号或双引号。实现相同结果另一种方法是在单引号或双引号之前加上反斜杠（`\\\"`）字符。以下代码块说明了这些技术：

```
b1 = """
b2 = '""'
b3 = '\\\""'
b4 = '\\\"'
```

```
print('b1:', b1, 'b2:', b2)
print('b3:', b3, 'b4:', b4)
```

上述代码块的输出在此处：

```
b1: ' b2: ""
b3: ' b4: ""
```

不在字符串字面量内的井号（`#`）是表示注释开始的字符。此外，`#` 之后直到物理行末尾的所有字符都是注释的一部分（并被 Python 解释器忽略）。考虑以下代码块：

```python
#!/usr/bin/python
# First comment
print "Hello, Python!"; # second comment
```

这将产生以下结果：

Hello, Python!

注释可以位于语句或表达式后的同一行：

`name = "Tom Jones" # 这也是一条注释`

你可以像下面一样对多行进行注释：

- `# 这是注释一`
- `# 这是注释二`
- `# 这是注释三`

Python 中的空行是指仅包含空白字符、注释或二者兼备的行。

早些时候你看到了如何从命令行启动 Python 解释器并输入 Python 命令。然而，你在 Python 解释器中输入的所有内容仅对当前会话有效：如果你退出解释器然后重新启动，你之前的定义将失效。幸运的是，Python 允许你将代码存储在文本文件中，正如下一节讨论的那样。

Python 模块（module）是一个包含 Python 语句的文本文件。在上一节中，你看到了 Python 解释器允许你测试定义在当前会话中有效的代码段。如果你想保留代码段和其他定义，请将它们放在文本文件中，这样你就可以在 Python 解释器之外执行这些代码。当模块首次被导入时，Python 最外层的语句将从上到下执行，这将设置它的变量和函数。

Python 模块可以从从命令行运行，所示：

```
python First.py
```

作为示例，将以下两个语句放在文本文件 `First.py` 中：

```python
x = 3
print x
```

现在输入以下命令：

```python
python First.py
```

上一个命令的输出是 3，这与在 Python 解释器中执行上述代码的结果相同。

当直接运行 Python 模块时，特殊变量 `__name__` 被设置为 `__main__`。你经常会在 Python 模块中看到以下类型的代码：

```python
if __name__ == '__main__':
    # 在这里做一些事情
    print 'Running directly'
```

上述代码段允许 Python 判断一个 Python 模块是从命令行启动的，还是导入到另一个 Python 模块中的。

Python 标准模块库提供了许多可以简化你的 Python 脚本的模块。标准库模块列表在此处：

`http://www.python.org/doc/`

一些重要的 Python 模块包括 `cgi`, `math`, `os`, `pickle`, `random`, `re`, `socket`, `sys`, 和 `time`。

书中的代码示例使用了 `math`, `os`, `random`, `re`, `sys` 和 `urllib` 模块。你需要在代码中导入这些模块才能在代码中使用它们。例如，以下代码块展示了如何导入四个标准 Python 模块：

```python
import datetime
import re
import sys
import time
```

此外，Python 还提供了可以从解释器访问的 `help()` 和 `dir()` 函数。`help()` 函数显示文档，而 `dir()` 函数显示定义的符号。例如，如果你输入 `help(sys)`，将看到 `sys` 模块的文档，而 `dir(sys)` 则列出定义的符号。

以下命令显示了如何获取函数的更多信息：

```python
>>> dir(str)
```

上一个命令生成了以下输出：

```
['__add__', '__class__', '__contains__', '__doc__', '__eq__', '__format__', '__ge__', '__getattr__', '__getitem__', '__getnewargs__', '__gt__', '__hash__', '__init__', '__le__', '__len__', '__lt__', '__mod__', '__mul__', '__ne__', '__new__', '__reduce_ex__', '__repr__', '__rmod__', '__rmul__', '__setattr__', '__sizeof__', '__str__', '__subclasshook', 'capitalize', 'center', 'count', 'decode', 'encode', 'endswith', 'expandtabs', 'find', 'format', 'index', 'isalnum', 'isalpha', 'isdigit', 'islower', 'isspace', 'istitle', 'isupper', 'join', 'ljust', 'lower', 'lstrip', 'partition', 'replace', 'rfind', 'rindex', 'rjust', 'rpartition', 'rsplit', 'rstrip', 'split', 'splitlines', 'startswith', 'strip', 'swapcase', 'title', 'translate', 'upper', 'zfill']
```

注意，虽然 `dir()` 没有列出内置函数和变量的名称，但你可以从自动导入并命名为 `__builtins__` 的标准模块获取这些信息：

```python
>>> dir(__builtins__)
```

以下命令显示了如何获取关于函数的更多信息：

```python
help(str.lower)
```

上一个命令的输出在此处：

Help on method_descriptor:

```
lower(...)
S.lower() -> string
```

> 返回字符串 S 的小写转换副本。

Python 执行一些编译时检查，其他检查（包括类型、名称等）则推到代码执行阶段。因此，如果你的 Python 代码引用了一个不存在的用户定义函数，代码将成功编译。事实上，只有当代码执行路径引用该不存在的函数时，代码才会抛出异常。

作为一个简单的示例，考虑以下 Python 函数 `myFunc`，它引用了一个名为 `DoesNotExist` 的不存在函数：

```python
def myFunc(x):
    if x == 3:
        print DoesNotExist(x)
    else:
        print 'x: ',x
```

上述代码只有在向 `myFunc` 函数传递值 `3` 时才会失败，随后 Python 会抛出一个错误。

# Python 中的简单数据类型

Python 支持原始数据类型，例如数字（整数、浮点数和指数数）、字符串和日期。Python 还支持更复杂的数据类型，如列表（或数组）、元组和字典。接下来的几节将讨论一些 Python 原始数据类型，并提供展示如何对这些类型执行各种操作的代码片段。

Python 提供了算术运算来处理数字，其操作方式与其他编程语言相似。以下示例涉及整数的算术运算。

```python
>>> 2+2
```

```python
>>> 4/3
1
>>> 3*8
24
```

以下示例将数字赋值给两个变量并计算它们的乘积：

```python
>>> x = 4
>>> y = 7
>>> x * y
28
```

以下示例演示了涉及整数的算术运算：

```python
>>> 2+2
4
>>> 4/3
1
>>> 3*8
24
```

注意，两个整数的除法（`"/"`）实际上是截断，只保留整数结果。以下示例将浮点数转换为指数形式：

```python
>>> fnum = 0.00012345689000007
>>> "%.14e"%fnum
'1.23456890000070e-04'
```

你可以使用 `int()` 函数和 `float()` 函数将字符串转换为数字：

```python
word1 = "123"
word2 = "456.78"
```

```python
var1 = int(word1)
var2 = float(word2)
print("var1: ",var1, " var2: ",var2)
```

上述代码块的输出在此：

var1: 123 var2: 456.78

或者，你可以使用 `eval()` 函数：

```python
word1 = "123"
word2 = "456.78"
var1 = eval(word1)
var2 = eval(word2)
print("var1: ",var1, " var2: ",var2)
```

如果你尝试转换不是有效整数或浮点数的字符串，Python 会抛出异常，因此建议将代码放置在 `try/except` 块中（本文章稍后部分会讨论）。

## 处理其他进制

Python 中的数字是 10 进制（默认），但你可以轻松地将数字转换为其他进制。例如，以下代码块初始化变量 `x` 的值为 `1234`，然后分别显示 2 进制、8 进制和 16 进制数字：

```python
>>> x = 1234
>>> bin(x) '0b100110101010'
>>> oct(x) '002322'
>>> hex(x) '0x4d2'
```

如果你想抑制 `0b`、`0o` 或 `0x` 前缀，可以使用 `format()` 函数，如下所示：

```python
>>> format(x, 'b') '100110101010' (注：此处原文示例输出似乎与1234不符，但此处原文翻译逻辑)
```

负整数用负号显示：

```python
>>> x = -1234
>>> format(x, 'b') '-10011010010'
>>> format(x, 'x') '-4d2'
```

## chr() 函数

Python 的 `chr()` 函数接收一个正整数作为参数，并将其转换为对应的字母值（如果存在）。字母 A 到 Z 的十进制表示为 65 到 90（对应于十六进制的 41 到 5a），小写字母 a 到 z 的十进制表示为 97 到 122（十六进制的 61 到 7a）。

这是一个使用 `chr()` 函数打印大写字母 A 的示例：

```python
>>> chr(65)
>>> 'A'
```

以下代码打印范围内范围内整数的 ASCII 值：

```python
result = ""
for x in range(65, 91):
    result = result+chr(x)
print "result: ", result
```

Python 2 使用 ASCII 字符串，而 Python 3 使用 UTF-8。你可以通过以下行表示一个字符范围：

```python
for x in range(65, 91):
```

然而，以下代码片段更直观：

```python
for x in range(ord('A'), ord('z') + 1):
```

## Python 中的 round() 函数
