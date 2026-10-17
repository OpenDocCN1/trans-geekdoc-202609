
## `Python 字符类`

`字符类` 是方便的表达式，比前一节的“裸”形式更短、更简单。以下是一些常用的字符序列，用于表示数字和字母的模式：

`\\d` 匹配一个数字

`\\w` 匹配一个字符（数字或字母）

`\\s` 匹配一个空白字符（空格、换行、回车或制表）

`\\b` 匹配单词和非单词之间的边界

`\\n`、`\\r`、`\\t` 分别表示换行、回车和制表

`\\` 用于转义任何字符

基于前面的定义，`\\d+` 匹配一个或多个数字，`\\w+` 匹配一个或多个字符，这两者都是比使用字符集更简洁的表达式。此外，我们还可以重新表述前一节中的表达式：

`\\d` 等价于 `\[0-9\]`，而 `\\D` 等价于 `\[^0-9\]`

`\\s` 等价于 `\[ \\t\\n\\r\\f\\v\]`，匹配任何非空白字符，而 `\\S` 正好相反（匹配 `\[^ \\t\\n\\r\\f\\v\]`）

`\\w` 等价于 `\[a-zA-Z0-9_\]`，匹配任何字母数字字符，而 `\\W` 正好相反（匹配 `\[^a-zA-Z0-9_\]`）

其他示例：

`\\d{2}` 等价于 `\[0-9\]\[0-9\]`

`\\d{3}` 等价于 `\[0-9\]\\{3\\}`

`\\d{2,4}` 等价于 `\[0-9\]\\{2,4\\}`

`\\d{5,}` 等价于 `\[0-9\]\\{5,\\}`

`^\\d+$` 等价于 `^\[0-9\]+$`

花括号（“{}”）称为量词，用于指定前置表达式中字符的数量或范围。

## `使用 re 模块匹配字符类`

`re` 模块提供以下用于在文本字符串中匹配或搜索正则表达式一次或多次出现的方法：

`match()`：判断正则表达式是否匹配字符串的*开头*。

`search()`：在字符串中查找任意位置的匹配。

`findall()`：找出所有匹配的子串并返回列表。

`finditer()`：找出所有匹配的子串并返回迭代器。

## `注意`

*The* `match()` *函数仅匹配到字符串的开头。*

下一节展示如何在 `re` 模块中使用 `match()` 函数。

## `使用 re.match() 方法`

`re.match()` 方法尝试在文本字符串中匹配正则表达式（可选标志），语法如下：

`re.match(pattern, string, flags=0)` 

`pattern` 参数是要在 `string` 参数中匹配的正则表达式。`flags` 参数使用位运算符（`|` 符号）可以指定多个标志。

`re.match` 方法在成功时返回匹配对象，在失败时返回 `None`。使用匹配对象的 `group(num)` 或 `groups()` 方法可以获取匹配表达式。

`group(num=0)`：返回整体匹配（或特定子组 num）  

`groups()`：返回所有匹配子组的元组（如果没有子组则返回空元组）

## `注意`

*The* `re.match()` *方法仅匹配文本字符串的开头，这与后文讨论的* `re.search()` *方法不同。*

下面的代码块演示如何使用 `group()` 函数在正则表达式中：

```python
>>> import re
>>> p = re.compile('(a(b)c)de')
>>> m = p.match('abcde')
>>> m.group(0) 'abcde'
>>> m.group(1) 'abc'
>>> m.group(2) 'b'
```

注意 `group()` 方法中更高的数字匹配更深层嵌套的表达式。

[Listing C.2](#appC.xhtml#listC.2) 显示 `MatchGroup1.py` 的内容，该文件说明如何使用 `group()` 函数匹配字母数字文本字符串和字母文本字符串。

***LISTING C.2: MatchGroup1.py***

```python
import re
line1 = 'abcd123'
line2 = 'abcdefg'
mixed = re.compile(r"^\[a-z0-9\]{5,7}$")
line3 = mixed.match(line1)
line4 = mixed.match(line2)
print('line1:',line1)
print('line2:',line2)
print('line3:',line3)
print('line4:',line4)
print('line5:',line4.group(0))
line6 = 'a1b2c3d4e5f6g7'
mixed2 = re.compile(r"^(\[a-z\]+\[0-9\]+){5,7}$")
line7 = mixed2.match(line6)
print('line6:',line6)
print('line7:',line7.group(0))
print('line8:',line7.group(1))
line9 = 'abc123fgh4567'
mixed3 = re.compile(r"^(\[a-z\]\*\[0-9\]\*){5,7}$")
line10 = mixed3.match(line9)
print('line9:',line9)
print('line10:',line10.group(0))
```

[Listing C.2](#appC.xhtml#listC.2) 的输出如下：  
line1: abcd123 line2: abcdefg line3: <_sre.SRE_Match object at 0x100485440> line4: <_sre.SRE_Match object at 0x1004854a8> line5: abcdefg line6: a1b2c3d4e5f6g7 line7: a1b2c3d4e5f6g7 line8: g7 line9: abc123fgh4567 line10: abc123fgh4567  

注意 line3 和 line7 涉及两种相似但不同的正则表达式。变量 `mixed` 指定由小写字母 followed by digits 组成的序列，且字符串长度在 5 到 7 之间。字符串 'abcd123' 满足所有条件。

然而，`mixed2` 指定由一个或多个“字母+数字”对组成的模式，且匹配对的数量在 5 到 7 之间。此例中，字符串 'abcd123' 以及 'a1b2c3d4e5f6g7' 都满足条件。

第三个正则表达式 `mixed3` 指定每个“字母+数字”对可以包含零个或多个小写字母和零个或多个数字，且这样的对的数量在 5 到 7 之间。从输出可以看出，`mixed3` 的正则表达式能够匹配任意顺序的小写字母和数字。

在前面的示例中，正则表达式指定了字符串长度的范围，下限为五，上限为七。

但也可以指定仅下限（无上限）或仅上限（无下限）。

[Listing C.3](#appC.xhtml#listC.3) 显示 `MatchGroup2.py` 的内容，该文件说明如何使用正则表达式和 `group()` 函数匹配字母数字文本字符串和字母文本字符串。

***LISTING C.3: MatchGroup2.py***

```python
import re
alphas = re.compile(r"^\[abcde\]{5,}")
line1 = alphas.match("abcde").group(0)
line2 = alphas.match("edcba").group(0)
line3 = alphas.match("acbedf").group(0)
line4 = alphas.match("abcdefghi").group(0)
line5 = alphas.match("abcdefghi abcdef")
print('line1:',line1)
print('line2:',line2)
print('line3:',line3)
print('line4:',line4)
print('line5:',line5)
```

[Listing C.3](#appC.xhtml#listC.3) 初始化变量 `alphas` 为一个正则表达式，匹配以 a 到 e 之间的任意字母开头，且至少包含五个字符的字符串。随后代码通过 `alphas` 正则对多个文本字符串进行匹配，`line1` 到 `line4` 分别通过 `group(0)` 获取第一个匹配子组。

[Listing C.3](#appC.xhtml#listC.3) 的输出如下：

line1: abcde line2: edcba line3: acbed line4: abcde line5: <_sre.SRE_Match object at 0x1004854a8> 

[Listing C.4](#appC.xhtml#listC.4) 显示 `MatchGroup3.py` 的内容，该文件说明如何使用正则表达式与 `group()` 函数匹配文本中的单词。

***LISTING C.4: MatchGroup3.py***

```python
import re
line = "Giraffes are taller than elephants"; 
matchObj = re.match( r'(.\*) are(\\.\*)', line, re.M|re.I)
if matchObj: 
    print("matchObj.group()  : ", matchObj.group())
    print("matchObj.group(1) : ", matchObj.group(1))
    print("matchObj.group(2) : ", matchObj.group(2))
else: 
    print("matchObj does not match line:", line)
```

[Listing C.4](#appC.xhtml#listC.4) 的输出如下：

matchObj.group()  :  Giraffes are matchObj.group(1) :  Giraffes matchObj.group(2) :  

