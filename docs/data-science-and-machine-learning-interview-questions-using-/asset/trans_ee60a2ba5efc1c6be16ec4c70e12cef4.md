

## Q50: **kwargs

**答：** `**kwargs` 也是可变参数，但以字典输入的形式出现，也称为关键字可变长参数。

![Image](OEBPS/images/37.jpg)

## Q51: 编写一个简单的 Lambda 表达式？

**答：**
```python
sumlambda = lambda x, y: x + y
print(sumlambda(2, 3))
```

在上述示例中，我们定义了一个接受两个参数并执行加法运算的 lambda 表达式。返回结果为 `x + y`，但无需显式使用 `return`，因为它仅包含单个语句。

## Q52: Python 中的 Lambda 形式包含语句？真还是假？

**答：** 该陈述为真，因为 Python 中的 lambda 必须是单行表达式。

## Q53: 解释 filter 函数？

**答：** filter 函数是一个工具函数，可根据某个条件跳过值。

![Image](OEBPS/images/38.jpg)

## Q54: 解释读写文件所涉及的步骤？

**答：** 这两种情况都涉及三个步骤：

1.  打开文件。
2.  使用相应的函数（`read` 或 `write`）读取或写入文件。
3.  关闭文件。

**写入示例：**

```python
a = open('hello.txt', 'a')  # 以写入模式打开文件
a.write('welcome to files with python')  # 将此行写入文件
a.close()  # 关闭文件
```

上述代码将欢迎消息写入 `hello.txt` 文件。

**读取示例：**

```python
a = open('hello.txt', 'r')  # 以读取模式打开文件
text = a.read()  # 将文件的全部内容读入内存
print(text)  # 打印读取的文本
a.close()  # 关闭文件
```

## Q55: 解释 “with 语句” 这一术语？

**答：** 每当存在相互关联的操作块时，`with` 语句就会很有用。

```python
with expression [as variable]:
    with-block
```

在上述语句中，我们可以看到 `with` 块将在 `with` 语句的帮助下，在变量打开的上下文中被使用。

```python
with open('output.txt', 'w') as f:
    f.write('|Python!')
```

在上述示例中，文件会在 `with` 块的作用域结束时自动关闭，其优势在于无需使用 `close` 显式关闭文件。

## Q56: 解释读取大文件的首选方式？

**答：**
```python
with open("sampleread.txt", "r+") as ip:
    for singleLine in ip:
        print(singleLine)
```

上述代码借助 `with` 语句以读取模式打开文件。因此，文件操作一结束，文件就会自动关闭。

此外，上述代码每次仅将单行加载到内存中，从而节省内存，或使该程序即使在内存占用较低的计算机上也能运行。

## Q57: 解释 Python 中的模块。

**答：** 模块（包括内置模块和用户自定义模块）是编写可复用代码集或复用通用代码集的方式。

Python 提供了许多内置模块，如 `math`、`os`、`sys` 等。

要使用模块，必须借助 `import` 语句或 `from ... import` 语句导入它。

## Q58: 解释导入模块的不同方式。

**答：** 模块可以使用 `import` 语句或 `from ... import` 语句导入。

区别在于我们是想要整个模块，还是仅想要其中的特定部分。

当我们想要导入特定模块（注：原文指模块中的特定部分）时，首选 `from ... import` 语句。

```python
from math import pi
print(pi)
```

当需要导入整个模块时，首选 `import` 语句。

```python
import math
print(math.pi)
```

正如你在 `import` 语句中所见，无论何时想要从模块获取变量或方法，都必须使用模块名。

## Q59: 我们可以创建自己的模块吗？

**答：** 是的，我们可以创建自己的模块。任何 Python 文件本身就是一个模块。

例如，考虑以下包含如下代码的 `mathop.py` 文件：

```python
def sum(a, b):
    return a + b

def sub(a, b):
    return (a - b)
```

在另一个名为 `usage.py` 的文件中，我们可以编写以下代码：

```python
import mathop
print(mathop.sum(99, 100))
print(mathop.sub(99, 100))
print(dir(mathop))
```

上述代码从模块读取并执行所需操作。

如果文件位于不同目录中，例如 `com` 文件夹，则可以通过以下方式导入：

`com.modulename`

## Q60: 简要解释 os 模块及其相应函数。

**答：** `os` 模块提供了各种函数来执行与操作系统相关的功能，特别是文件操作方面。

以下是一些重要函数：

*   `os.chdir("D:/pythoneg/intro/pyFolder")`：用于更改当前工作目录。
*   `os.mkdir('pyFolder')`：用于创建新目录。
*   `os.remove()`：用于删除特定文件。
*   `os.getcwd()`：用于获取当前工作目录。
*   `os.environ`：用于打印环境相关详细信息。
*   `os.system(' dir>>1.txt')`：用于执行命令行相关命令。例如，执行 `dir` 命令（Windows 命令提示符命令）以列出目录。
*   `os.walk(dir)`：用于列出特定目录下的子目录和文件。

## Q61: 使用 os 模块打印目录结构。

**答：**
```python
import os

rootDir = 'D:/nodejstraining/NodeJSExample/NodeJSExample'
for dirName, subdirList, fileList in os.walk(rootDir):
    print('Found directory: %s' % dirName)
    for fname in fileList:
        print('\t%s' % fname)
```

在上述示例中，我们借助 `os.walk` 函数打印目录结构，该函数可以列出特定目录下的目录名、子目录列表和文件列表。

## Q62: 解释 dir 函数。

**答：** `dir` 函数用于打印模块暴露的各种函数。

例如，`dir(math)` 会打印 `math` 模块中的所有函数。

```python
import math
print(dir(math))
```

**输出：**

```
['__doc__', '__loader__', '__name__', '__package__', '__spec__', 'acos', 'acosh', 'asin', 'asinh', 'atan', 'atan2', 'atanh', 'ceil', 'copysign', 'cos', 'cosh', 'degrees', 'e', 'erf', 'erfc', 'exp', 'expm1', 'fabs', 'factorial', 'floor', 'fmod', 'frexp', 'fsum', 'gamma', 'gcd', 'hypot', 'inf', 'isclose', 'isfinite', 'isinf', 'isnan', 'ldexp', 'lgamma', 'log', 'log10', 'log1p', 'log2', 'modf', 'nan', 'pi', 'pow', 'radians', 'sin', 'sinh', 'sqrt', 'tan', 'tanh', 'tau', 'trunc']
```

## Q63: 解释 Python 中的异常处理。

**答：** 异常处理借助 `try...except` 块支持。

任何可能逻辑上导致问题的语句都会放在 `try` 块中。

如果发生异常，相应的处理会在 `except` 块中完成。

一个 `try` 可以包含多个 `except` 块。

![Image](OEBPS/images/39.jpg)

在上述示例中，我们将接受用户输入并将其类型转换为 `int` 的代码放在 `try` 块中。我们有两个 `except` 块：一个捕获特定异常，另一个捕获通用 `Exception`。根据引发的异常，相应的 `except` 块会被调用。

要打印异常的完整详细信息，我们使用别名，即 `except Exception as e:` 为异常创建一个别名。

如果没有发生异常，将执行 `else` 块。

## Q64: 如何创建用户自定义异常？

**答：** Python 支持用户自定义异常。

要创建我们自己的异常，必须创建一个类，其名称为我们想要的异常名称，该类继承自 `Exception`，并借助 `raise` 语句相应地使用它。

![Image](OEBPS/images/40.jpg)

## Q65: raise 语句有什么用？

**答：** `raise` 语句用于根据某些条件或约束在运行时生成异常。

## Q66: 如何在 Python 中创建自己的类？解释构造函数。

**答：** 我们可以在 Python 中创建自己的类。类的构造函数通过 `__init__` 方法指定。

