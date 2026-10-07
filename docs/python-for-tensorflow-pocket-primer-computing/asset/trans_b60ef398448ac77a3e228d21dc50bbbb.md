

作为一个简单的示例，考虑以下 Python 函数 `myFunc`，它引用了一个名为 `DoesNotExist` 的不存在函数：

```python
def myFunc(x):
    if x == 3:
        print DoesNotExist(x)
    else:
        print 'x: ',x
```

上述代码只有在向 `myFunc` 函数传递值 `3` 时才会失败，随后 Python 会抛出一个错误。
现在你已经了解了一些基本概念（例如如何使用 Python 解释器）以及如何启动自定义 Python 模块，下一节将讨论 Python 中的原始数据类型。

# Python 中的简单数据类型

Python 支持原始数据类型，例如数字（整数、浮点数和指数数）、字符串和日期。Python 还支持更复杂的数据类型，如列表（或数组）、元组和字典。接下来的几节将讨论一些 Python 原始数据类型，并提供展示如何对这些类型执行各种操作的代码片段。

# 数字处理

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

# 处理其他进制

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

# chr() 函数

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

# Python 中的 round() 函数

Python 的 `round()` 函数允许你将小数值舍入到最近的精度：

```python
>>> round(1.23, 1)
1.2
>>> round(-3.4, 1)
-3.4
```

# Python 中的数字格式化

Python 允许你在打印数字时指定小数位数，如下所示：

```python
>>> x = 1.23456
>>> format(x, '.2f')
'1.23'
>>> format(x, '.3f')
'1.235'
>>> 'value is {:.3f}'.format(x)
'value is 1.235'
```

```python
>>> decimal import Decimal
>>> a = Decimal('4.2')
>>> b = Decimal('2.1')
>>> a + b
Decimal('6.3')
>>> print(a + b)
6.3
>>> (a + b) == Decimal('6.3')
True
>>> x = 1234.56789
>>> #两位小数
>>> format(x, '.2f')
'1234.57'
>>> # 10字符右对齐
>>> format(x, '>10.1f')
'     1234.6'
>>> # 左对齐
>>> format(x, '<10.1f')
'1234.6    '
>>> # 对齐
>>> format(x, '^10.1f')
'  1234.6   '
>>> # 千分位分隔符
>>> format(x, ',')
'1,234.56789'
>>> format(x, ',.1f')
'1,234.6'
```

# 处理分数

Python 支持 `Fraction()` 函数（定义在 fractions 模块中），它接受两个整数分别表示分数的分子和分母（必须非零）。以下是 Python 中定义和操作分数的几个示例：

```python
>>> from fractions import Fraction
>>> a = Fraction(5, 4)
>>> b = Fraction(7, 16)
>>> print(a + b)
27/16
>>> print(a * b)
35/64
>>> # 获取分子/分母
>>> c = a * b
>>> c.numerator
35
```

```python
>>> c.denominator
64
>>> # 转换为浮点数
>>> float(c)
0.546875
```

```python
>>> # 限制值的分母
>>> print(c.limit_denominator(8))
4
```

```python
>>> # 将浮点数转换为分数
>>> x = 3.75
>>> y = Fraction(*x.as_ratio())
>>> y
Fraction(15, 4)
```

深入研究字符串的 Python 代码，下一节将简要讨论 Unicode 和 UTF-8，两者都是字符编码。

# Unicode 和 UTF-8

Unicode 字符串由一组 0 到 0x1ffff 之间的数字组成，每个数字代表一组字节。编码是将 Unicode 字符串转换为字节序列的方式。在各种编码中，UTF-8（Unicode 格式）可能是常见的，它也是许多系统的默认编码。UTF-8 中的数字 8 表示编码使用 8 位数字，而 UTF-16 使用 16 位数字（但这种编码不常见）。

ASCII 字符集是 UTF-8 的子集，因此有效的 ASCII 字符串不需要重新编码即可作为 UTF-8 字符串读取。此外，Unicode 字符串可以转换为 UTF-8 字符串。

# 支持 Unicode，这意味着你可以渲染不同语言的字符。Unicode 数据可以以相同的方式存储和操作。如下所示，通过在前面加上字母 “u” 创建 Unicode 字符串：

```python
>>> u'Hello from Python!'
u'Hello from Python!'
```

可以通过指定 Unicode 值将特殊字符包含在字符串中。例如，以下字符串在字符串中嵌入了一个空格（Unicode 值为 0x20）：

```python
>>> u'Hello\u020from Python!'
u'Hello from Python!'
```

列表 1.1 显示了 `Unicode1.py` 的内容，说明了如何显示日语字符串和另一个中文（普通话）字符串。

# 列表 1.1 Unicode.py

```python
chinese = u'\u5c07\u63ae\u8ae HTML5
\u53ca\u517\u4ed6'
hiragana = u'\uD3 \u3063
\u304B\u3063\u3053\u3043\u3043 \u3067\u3059 !'
```

```python
print 'Chinese:', chinese
print 'Hiragana:', hiragana
```

列表 1.2 [注：可能是 1.1] 的输出在此：

Chinese: 將探討 HTML5 及其他
Hiragana: D3 は かっこいい です!

本章的下一部分将向你如何使用内置 Python 函数“切分”文本字符串。

# 处理字符串

Python 2 中的字符串是 ASCII 编码字节的序列。你可以使用 `+` 运算符拼接两个字符串。以下示例打印了一个字符串，然后拼接两个单字母字符串：

```python
>>> 'abc'
'abc'
>>> 'a' + 'b'
'ab'
```

你可以使用 `+` 或 `*` 拼接相同的字符串，如下所示：

```python
>>> 'a' + 'a' + 'a'
'aaa'
>>> 'a' * 3
'aaa'
```

你可以将字符串赋值给变量并使用 print 命令打印它们：

```python
>>> print 'abc'
abc
```

