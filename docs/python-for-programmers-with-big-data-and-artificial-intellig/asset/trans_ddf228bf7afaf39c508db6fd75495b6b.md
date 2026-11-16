

点击此处查看代码图像

```
In [3]: '{0} {0} {1}'.format('Happy', 'Birthday')
Out[3]: 'Happy Happy Birthday'
```

请注意，我们使用了位置编号 0（'Happy'）两次——你可以按任意顺序引用每个参数任意多次。

### 引用关键字参数

你可以通过占位符中的键引用关键字参数：

点击此处查看代码图像

```
In [4]: '{first} {last}'.format(first='Amanda', last='Gray')
Out[4]: 'Amanda Gray'

In [5]: '{last} {first}'.format(first='Amanda', last='Gray')
Out[5]: 'Gray Amanda'
```

## 8.3 连接和重复字符串

在前面的章节中，我们使用 + 运算符连接字符串，使用 * 运算符重复字符串。你也可以使用增量赋值执行这些操作。字符串是不可变的，因此每个操作都会将一个新的字符串对象赋值给变量：

点击此处查看代码图像

```
In [1]: s1 = 'happy'

In [2]: s2 = 'birthday'

In [3]: s1 += ' ' + s2

In [4]: s1
Out[4]: 'happy birthday'

In [5]: symbol = '>'

In [6]: symbol *= 5

In [7]: symbol
Out[7]: '>>>>>'
```

## 8.4 从字符串中删除空白字符

有多种字符串方法可用于删除字符串两端的空白字符。每种方法都返回一个新字符串，同时保持原字符串不变。由于字符串是不可变的，因此每个看似修改字符串的方法都会返回一个新字符串。

### 删除前导和尾随空白字符

让我们使用字符串方法 `strip` 来删除字符串的前导和尾随空白字符：

点击此处查看代码图像

```
In [1]: sentence = '\t \n This is a test string. \t\t \n'
In [2]: sentence.strip()
Out[2]: 'This is a test string.'
```

### 删除前导空白字符

方法 `lstrip` 仅删除前导空白字符：

点击此处查看代码图像

```
In [3]: sentence.lstrip()
Out[3]: 'This is a test string. \t\t \n'
```

### 删除尾随空白字符

方法 `rstrip` 仅删除尾随空白字符：

点击此处查看代码图像

```
In [4]: sentence.rstrip()
Out[4]: '\t \n This is a test string.'
```

正如输出所示，这些方法删除所有类型的空白字符，包括空格、换行符和制表符。

## 8.5 更改字符大小写

在前面的章节中，你使用了字符串方法 `lower` 和 `upper` 将字符串转换为全小写或全大写字母。你也可以使用方法 capitalize 和 title 来更改字符串的大小写形式。

### 仅大写字符串的首字符

方法 capitalize 复制原始字符串并返回一个新字符串，其中仅首字母大写（这有时称为句子大小写形式）：

点击此处查看代码图像

```
In [1]: 'happy birthday'.capitalize()
Out[1]: 'Happy birthday'
```

### 大写字符串中每个单词的首字符

方法 title 复制原始字符串并返回一个新字符串，其中每个单词仅首字符大写（这有时称为图书标题大小写形式）：

点击此处查看代码图像

```
In [2]: 'strings: a deeper look'.title()
Out[2]: 'Strings: A Deeper Look'
```

## 8.6 字符串的比较运算符

可以使用比较运算符比较字符串。请记住，字符串是基于其底层整数数值进行比较的。因此，大写字母比小写字母“小”，因为大写字母的整数值较低。例如，'A' 是 65，'a' 是 97。你已经看到，可以使用 ord 检查字符代码：

点击此处查看代码图像

```
In [1]: print(f'A: {ord("A")}; a: {ord("a")}')
A: 65; a: 97
```

让我们使用比较运算符比较字符串 'Orange' 和 'orange'：

点击此处查看代码图像

```
In [2]: 'Orange' == 'orange'
Out[2]: False

In [3]: 'Orange' != 'orange'
Out[3]: True

In [4]: 'Orange' < 'orange'
Out[4]: True

In [5]: 'Orange' <= 'orange'
Out[5]: True

In [6]: 'Orange' > 'orange'
Out[6]: False

In [7]: 'Orange' >= 'orange'
Out[7]: False
```

## 8.7 搜索子字符串

你可以在字符串中搜索一个或多个相邻字符（称为 _子字符串_），以统计出现次数、判断字符串是否包含子字符串，或确定子字符串在字符串中所处的索引位置。本节展示的每种方法都使用底层数值按字典顺序比较字符。

### 统计出现次数

字符串方法 `count` 返回其参数在调用该方法的字符串中出现的次数：

点击此处查看代码图像

```
In [1]: sentence = 'to be or not to   be that is the question'

In [2]: sentence.count('to')
Out[2]: 2
```

如果将第二个参数指定为 `start_index`，`count` 仅搜索切片 `string[start_index:]` ——即从 `start_index` 到字符串末尾：

点击此处查看代码图像

```
In [3]: sentence.count('to', 12)
Out[3]: 1
```

如果将第二个和第三个参数指定为 *起始索引* 和 *结束索引*，`count` 仅搜索切片 *字符串*[*起始索引*:*结束索引*]——即从 *起始索引* 到（但不包括）*结束索引*：

点击此处查看代码图像

```
In [4]: sentence.count('that', 12, 25)
Out[4]: 1
```

与 `count` 类似，本节展示的其他每种字符串方法都带有 *起始索引* 和 *结束索引* 参数，用于仅搜索原始字符串的一个切片。

### 在字符串中定位子字符串

字符串方法 `index` 在字符串中搜索子字符串，并返回子字符串首次出现的索引；否则，将发生 `ValueError`：

点击此处查看代码图像

```
In [5]: sentence.index('be')
Out[5]: 3
```

字符串方法 `rindex` 与 `index` 执行相同的操作，但从字符串末尾开始搜索，并返回子字符串最后出现的 *最后* 索引；否则，将发生 `ValueError`：

点击此处查看代码图像

```
In [6]: sentence.rindex('be')
Out[6]: 16
```

字符串方法 `find` 和 `rfind` 执行与 `index` 和 `rindex` 相同的任务，但如果未找到子字符串，则返回 -1，而不会导致 `ValueError`。

### 确定字符串是否包含子字符串

如果只需知道字符串是否包含子字符串，请使用运算符 `in` 或 `not in`：

点击此处查看代码图像

```
In [7]: 'that' in sentence
Out[7]: True

In [8]: 'THAT' in sentence
Out[8]: False

In [9]: 'THAT' not in sentence
Out[9]: True
```

### 定位字符串开头或结尾的子字符串

字符串方法 startswith 和 endswith 在字符串以指定子字符串开头或结尾时返回 True：

点击此处查看代码图像

```
In [10]: sentence.startswith('to')
Out[10]: True

In [11]: sentence.startswith('be')
Out[11]: False

In [12]: sentence.endswith('question')
Out[12]: True

In [13]: sentence.endswith('quest')
Out[13]: False
```

## 8.8 替换子字符串

一种常见的文本操作是定位子字符串并替换其值。方法 replace 接受两个子字符串。它在字符串中搜索第一个参数中的子字符串，并用第二个参数中的子字符串替换每个出现项。该方法返回包含结果的新字符串。让我们将制表符替换为逗号：

点击此处查看代码图像

```
In [1]: values = '1\t2\t3\t4\t5'

In [2]: values.replace('\t', ',')
Out[2]: '1,2,3,4,5'
```

方法 replace 可接收一个可选的第三个参数，指定要执行的最大替换次数。

## 8.9 分割和连接字符串

当你阅读一个句子时，你的大脑会将其分解为单个单词，即 **词元**，每个词元都传达含义。像 IPython 这样的解释器会对语句进行词元化，将其分解为关键字、标识符、运算符及其他编程语言元素等单独的组件。词元通常由空格、制表符和换行符等空白字符分隔，尽管也可以使用其他字符——这些分隔符称为 **分隔符**。

### 分割字符串

我们先前展示过，字符串方法 `split` 在 _无_ 参数时会在每个空白字符处将字符串分解为子字符串，从而对其进行词元化，然后返回一个词元列表。要在自定义分隔符（例如每个逗号-空格对）处对字符串进行词元化，请指定 `split` 用于对字符串进行词元化的分隔符字符串（例如 ', '）：

![](img/34b7fc2f1ee27beb73bca14927d42340_320_0.png)

```
In [1]: letters = 'A, B, C, D'

In [2]: letters.split(', ')
Out[2]: ['A', 'B', 'C', 'D']
```

如果将整数作为第二个参数提供，它指定最大分割次数。最后一个词元是在达到最大分割次数后字符串的剩余部分：

![](img/34b7fc2f1ee27beb73bca14927d42340_320_1.png)

```
In [3]: letters.split(', ', 2)
Out[3]: ['A', 'B', 'C, D']
```

还有一个 `rsplit` 方法，它执行与 `split` 相同的任务，但从字符串末尾向开头处理最大分割次数。

### 连接字符串

字符串方法 `join` 连接其参数中的字符串，该参数必须是仅包含字符串值的可迭代对象；否则，将发生 `TypeError`。连接项之间的分隔符是你调用 `join` 的字符串。以下
