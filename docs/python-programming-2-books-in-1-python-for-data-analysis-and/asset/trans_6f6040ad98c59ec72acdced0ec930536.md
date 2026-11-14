

12. 要验证安装，请导航到安装 Python 的目录，然后双击 python.exe 文件。

## MACINTOSH

1. 从官方 Python 网站，点击“下载”图标并选择 Mac。
2. 点击“下载 Python 3.8.0”按钮以查看所有可下载的文件。
3. 在随后的屏幕上，选择要下载的 Python 版本。在本书中，我们将使用“稳定版本”下的 Python 3 版本。因此，向下滚动页面，在 Python 3.8.0 下点击“下载 macOS 64-bit 安装程序”链接，如下图所示。

![](img/fe3427740784586362e0a35d3200b425_131_0.png)

4. 将显示标题为“python-3.8.0-macosx10.9.pkg”的弹出窗口。
5. 点击“保存文件”以开始下载文件。
6. 下载完成后，双击保存的文件图标，将显示“安装 Python”弹出窗口。
7. 点击“继续”以继续，将出现条款和条件弹出窗口。
8. 点击 Agree，然后点击“安装。”
9. 将显示请求管理员权限和密码的通知。输入系统密码以开始安装。
10. 安装完成后，将出现“安装成功”消息。点击“关闭”按钮，即全部完成。
11. 要验证安装，请导航到安装 Python 的目录，然后双击 python 启动器图标，它将带您进入 Python 终端。

## LINUX

- 对于 Red Hat、CentOS 或 Fedora，安装 python3 和 python3-devel 软件包。
- 对于 Debian 或 Ubuntu，安装 python3.x 和 python3.x-dev 软件包。
- 对于 Gentoo，安装 '=python-3.x.*' ebuild（您可能需要先取消屏蔽它）。

1. 从官方 Python 网站，点击“下载”图标并选择 Linux/UNIX。
2. 点击“下载 Python 3.8.0”按钮以查看所有可下载的文件。
3. 在随后的屏幕上，选择要下载的 Python 版本。在本书中，我们将使用“稳定版本”下的 Python 3 版本。因此，向下滚动页面，在 Python 3.8.0 下点击“下载 Gzipped 源码压缩包”链接，如下图所示。
4. 将显示标题为“python-3.7.5.tgz”的弹出窗口。
5. 点击“保存文件”以开始下载文件。
6. 下载完成后，双击保存的文件图标，将出现“安装 Python”弹出窗口。
7. 按照屏幕上的提示完成安装过程。

![](img/fe3427740784586362e0a35d3200b425_132_0.png)

## 开始使用

在计算机上安装 Python 终端后，您现在可以开始编写和执行 Python 代码。所有 Python 代码都作为 (.py) 文件写在文本编辑器中，并在 Python 解释器命令行上执行，如下面的代码所示，其中“nineplanets.py”是 Python 文件的名称：

```
`"C: \Users\Your Name\python nineplanets.py"`
```

您可以在 Mac、Windows 或 Linux 命令行上键入下面的代码，直接在命令行本身中测试一小段代码，而无需将其写入文件，如下所示：

```
"C:\\Users\\Your Name\\python"
```

如果上面的命令不起作用，请改用下面的代码：

```
"C:\\Users\\Your Name\\py"
```

### 缩进

缩进（即代码前的空格数）对 Python 编码结构至关重要。在大多数编程语言中，缩进是为了增强代码的可读性而添加的。然而，在 Python 中，缩进用于指示执行代码的一个子集，如下面的代码所示：

```
if 7 > 2:
    print('Seven is greater than two')
```

缩进位于带有 print 命令的第二行代码之前。如果跳过缩进，代码如下编写，将触发错误：

```
if 7 > 2:
print('Seven is greater than two')
```

空格数可以修改，但至少需要一个空格。例如，您可以使用更高的缩进执行下面的代码，但对于特定的代码集，必须使用相同数量的空格，否则会收到错误。

```
if 7 > 2:
    print('Seven is greater than two')
```

### 添加注释

在 Python 中，可以通过将代码注释行以“#”开头来添加注释，如下示例所示：

```
#Any relevant comments will be added here
print('Nine planets')
```

注释用作代码的描述，Python 终端不会执行它们。请务必记住，代码行末尾的任何注释都会导致 Python 终端跳过整行代码，如下面的代码所示。在测试代码时，如果需要停止执行，注释可能非常有用。

```python
print('Nine Planets') #Comments added here
```

可以通过将每行代码以“#”开头来添加多行注释，如下所示：

```python
#Comments added here
#Supplementing the comments here
#Further adding the comments here
print('Nine Planets')
```

## Python 变量

在 Python 中，变量主要用于保存数据值，而无需为此执行命令。只需将所需值赋给变量即可创建变量，如下示例所示：

```python
A = 999
B = 'Patricia'
print(A)
print(B)
```

变量可以在没有特定数据类型的情况下声明。变量的数据类型也可以在初始声明后修改，如下示例所示：

```python
A = 999 # A has data type set as int
A = 'Patricia' # A now has data type str
print(A)
```

适用于 Python 变量名称的一些规则如下：

1. 变量名可以短至单个字母，也可以是 height、weight 等更具描述性的单词。
2. 变量名只能以下划线或字母开头。
3. 变量名不能以数字开头。
4. 变量名可以包含下划线或字母数字字符。不允许其他特殊字符。
5. 变量名区分大小写。例如，‘weight’、‘Weight’ 和 ‘WEIGHT’ 将被视为 3 个不同的变量。

## 为变量赋值

在 Python 中，多个变量可以在单行代码中被赋予不同的值，如下示例所示：

```python
A, B, C = 'violet', 'maroon', 'teal'
print(A)
print(B)
print(C)
```

或者，多个变量可以在单行代码中被赋予相同的值，如下示例所示：

```python
A, B, C = 'violet'
print(A)
print(B)
print(C)
```

## Python 数据类型

Python 支持多种数据类型，如下所示。要扎实理解变量的概念，您必须学习所有 Python 数据类型。

| 类别 | 数据类型 | 示例语法 |
|---|---|---|
| 文本 | "str" | 'Nine Planets' "Nine Planets" """Nine Planets""" |
| 布尔值 | "bool" | 'True' 'False' |
| 映射（混合数据类型，键值对关联数组） | "dict" | {'key8': 8.0, 5: True} |
| 序列（可能包含混合数据类型） | "list" | [8.0, 'character', True] |
| 序列（可能包含混合数据类型） | "tuple" | (8.0, 'character', True) |
| 序列（可能包含混合数据类型） | "range" | range(11, 51) range(110, 51, 11, -11, -51, -110) |
| 二进制 | "bytes" | b'byte sequences' b'byte sequences' bytes([121, 91, 75, 110]) |
| 二进制 | "bytearray" | bytearray(b'byte sequences') bytearray(b'byte sequences') bytearray([121, 91, 75, 110]) |
| 二进制 | "memoryview" | |
| 集合 | "set" | {8.0, 'character', True} |
| （无序、无重复、混合数据类型） | "frozenset" | frozenset([8.0, 'character', True]) |
| 数值 | "int" | 35 |
| | "float" | 155e3 |
| | "complex" | 155 + 2.1j |
| 省略号（NumPy 数组中的索引） | "ellipsis" | ... 'Ellipsis' |

要查看任何对象的数据类型，可以使用“type()”函数，如下示例所示：

```python
A = 'Violet'
print(type(A))
```

## 为变量指定数据类型

只需为变量声明一个值即可创建新变量。此设置的数据值将反过来为变量赋予数据类型。

要为变量指定特定数据类型，请使用下面列出的构造函数：

| 构造函数 | 数据类型 |
|---|---|
| A = str('Nine Planets') | str |
| A = int(55) | Int（必须是整数，可正可负，无小数，无长度限制） |
| A = float(14e6) | Float（浮点数必须是带有一个或多个小数的正数或负数；可能是科学 |

