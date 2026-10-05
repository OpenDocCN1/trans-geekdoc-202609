

# 使用 Python 进行软计算与机器学习

这个字符集有一个惊人的属性：所有大写字母都被认为小于所有小写字母，因此字符串“Z”的排序在字符串“a”之前。

- Unicode 值是由零或多个 32 位 Unicode 字符组成的字符串。Unicode 字符集涵盖了几乎每种编写语言和几乎发明的每一个特殊字符。

我们将主要讨论对 `str` 值的操作，但大多数 Unicode 操作都是相似或相同，不同在于 Unicode 字面量前面带有一个字母 `u`：例如，“abc”是 `str` 类型，u“abc”是 `unicode` 类型。

# 字符串字面量

在 Python 中，你可以使用单引号（'...'）或双引号（"..."）包裹字符串常量。

```
>>> cloneName = 'Clem'

>>> cloneName
'Clem'

>>> print cloneName
Clem

>>> fairName = "Future Fair"

>>> print fairName
Future Fair

>>> fairName
'Future Fair'
```

当在交互模式（conversational mode）下显示字符串值时，Python 通常会使用单引号。在内部，无论你使用哪种引号，值都是相同的。同样注意，`print` 语句只显示字符串的内容，而不会带任何引号。

要将整数（`int` 类型）值 `i` 转换为等等字符串，使用函数 `str(i)`：

```
>>> str(-497)
'-497'

>>> str(000)
'0'
```

# Python 2.7 编程教程 167

逆操作是将字符串 $s$ 转换回整数，写为 "int(s)"：

```python
>>> int("-497")
-497
>>> int("-0")
0
>>> int ("0122 this ain’t no number")
Traceback (most recent call last):
File "stdin>", line 1, in ?
  ValueError: invalid literal for int(): 012this ain’t no number
```

上面的示例显示了尝试转换不是有效数字的字符串时发生的情况。要将包含基数为 $B$ 的数字的字符串 $s$，使用形式 "int(s, B)"：

```python
>>> int ('0F', 16 )
15
>>> int ("101101", 2)
21
>>> int ("0177776", 8 )
65534
```

要获取单字符字符串 $s$ 中包含的 8 位整数代码，使用函数 "ord($s$)"。反函数是将整数 $i$ 转换为代码为 $i$ 的字符，使用 "chr($i$)"。每个字符的数值由 `chr(ASCII 字符集)` 定义：

```python
>>> chr(97 )
'a'
>>> ord('a')
97
>>> chr(65)
'A'
>>> ord('A')
65
```

除了代码在 32 到 127（包含）范围内的打印字符外，Python 字符串还可以包含任何其他不可打印的特殊字符。例如，空字符（其官方名称为 NUL）是代码为零的字符。编写此类字符的一种方法是使用这种形式：

```
`\NN`
```

其中 N 是该字符的十六进制（基 16）代码：

```python
>>> chr(0)
```

```
`\x00`
```

```
>>> ord('\x00')
```

你可能可能需要处理的另一个特殊字符是换行符，其官方名称为 LF（代表 "line feed"）。使用特殊转义序列 "\n" 来产生该字符。

```python
>>> s = "Two-line\nstring."
```

```
>>> s
'Two-line\nstring.'

```
>>> print s
Two-line
string.
```

如你所示，当在交互模式下显示换行符时，它显示为 "\n"，但当你打印它时，随后的字符将出现在下一行。该字符的代码是 10：

```python
>>> ord('\n')
10
```

```
>>> chr(10)
\n
```

Python 还有许多其他此类转义序列。“转义序列”一术是指一种约定，即特殊字符（“转义字符”）会改变其后字符的含义。Python 的转义字符是反斜杠（\）。

| 输入 | 代码 | 名称 | 含义 |
|---|---|---|---|
| \b | 8 | BS | 退格 (backspace) |
| \t | 9 | HT | 制表符 (tab) |
| \" | 34 | " | 双引号 (Double quote) |
| \' | 39 | ' | 单引号 (Single quote) |
| | 92 | \ | 反斜杠 (Backslash) |

另一种获取包含换行符的字符串的方法：使用*三*对引号（单引号或双引号）包裹字符串。

> 注意，在 Python 的交互模式下，当你按下回车结束行时，Python 知道该行未完成，而不是显示通常“>>>”。

# 字符串索引

要从字符串中提取一个或多个字符，你需要知道字符串是如何编号的。

# 字符串方法

字符串的许多操作都是方法。以下章节描述了一些常用的方法。

.center(): 居中文本

给定字符串 s，为了产生在指定长度字段内居中的新字符串，使用此方法：

```python
>>> k = "Ni"
>>> k.center(5)
' Ni   '
```

```
>>> "<->".center(12)
'    <->    '
```

注意在第一个示例中，我们要求 Python 在长度为 5 的字段内居中字符串 "Ni"。Python 随机添加剩余的空间。

.ljust() 和 .rjust(): 右侧填充长度

另一个实用的字符串方法是在给定长度的字段内左对齐。通用形式为：

s.ljust(n)

对于任何字符串 s，该方法返回一个包含 s 的字符并在之后添加足够空间以形成长度为 n 的新字符串。

```
>>> "Ni".ljust(4)
'Ni  '
>>> "Too long to fit".ljust(4)
'Too long to fit'
```

注意 .ljust() 方法永远不会返回更短的字符串。如果长度不够，它只返回原始值。

有一个类似的方法可以将字符串值右对齐：

s.rjust(n)

该方法返回在值之前添加足够的空间。与 .rjust() 方法一样，它永远不会返回比原始短的字符串。

```
>>> "Ni".rjust(4)
'  Ni'
>>> m = "floccinaucinihilipification"
>>> m.rjust(4)
'floccinaucinihilipification'
```

# .strip(), .lstrip(), 和 .rstrip(): 删除开头和结尾空白

有时你想从字符串中移除空白（空格、制表符和换行符）。对于字符串 s，使用这些方法可以移除开头和结尾空白：

- s.strip() 返回去除了任何开头或结尾字符的 s。
- s.lstrip() 仅移除开头空白。
- s.rstrip() 仅移除结尾空白。

```python
>>> spaceCase = '\n \t Moon \t\t ''
>>> spaceCase
'
 \t Moon \t\t '
```

