

code 创建包含逗号分隔的值列表的字符串：

单击此处查看代码图像

```
In [4]: letters_list = ['A', 'B', 'C', 'D']
In [5]: ','.join(letters_list)
Out[5]: 'A,B,C,D'
```

单击此处查看代码图像

```
In [6]: ','.join([str(i) for i in range(10)])
Out[6]: '0,1,2,3,4,5,6,7,8,9'
```

在“文件和异常”章节，你将了解如何处理包含逗号分隔值的文件。这些被称为 **CSV 文件**，是一种常见的数据存储格式，可由 Microsoft Excel 或 Google Sheets 等电子表格应用程序加载。在数据科学案例研究章节中，你将看到许多关键库（如 NumPy、Pandas 和 Seaborn）提供处理 CSV 数据的内置功能。

### 字符串方法 partition 和 rpartition

字符串方法 `partition` 根据方法的 `separator` 参数将字符串拆分为三个字符串的元组。这三个字符串是

- 分隔符之前的原始字符串部分，
- 分隔符本身，以及
- 分隔符之后的字符串部分。

这可能对于拆分更复杂的字符串很有用。请考虑表示学生姓名和成绩的字符串：

```
'Amanda: 89, 97, 92'
```

让我们将原始字符串拆分为学生姓名、分隔符 ’ : ’ 以及表示成绩列表的字符串：

![](img/34b7fc2f1ee27beb73bca14927d42340_322_0.png)

```
In [7]: 'Amanda: 89, 97, 92'.partition(': ')
Out[7]: ('Amanda', ': ', '89, 97, 92')
```

要想从字符串末尾查找分隔符，请使用 rpartition 方法进行拆分。例如，请考虑以下 URL 字符串：

```
'http://www.deitel.com/books/PyCDS/table_of_contents.html'
```

让我们使用 rpartition 将 'table_of_contents.html' 从 URL 的其余部分拆分出来：

![](img/34b7fc2f1ee27beb73bca14927d42340_322_1.png)

```
In [8]: url = 'http://www.deitel.com/books/PyCDS/table_of_contents.html'

In [9]: rest_of_url, separator, document = url.rpartition('/')

In [10]: document
Out[10]: 'table_of_contents.html'

In [11]: rest_of_url
Out[11]: 'http://www.deitel.com/books/PyCDS'
```

### 字符串方法 splitlines

在“文件和异常”章节中，你将从文件读取文本。如果将大量文本读入字符串，你可能希望根据换行符将字符串拆分为行列表。splitlines 方法返回一个新字符串列表，表示在原始字符串的每个换行符处拆分的文本行。请记住，Python 使用嵌入的 \n 字符来存储多行字符串以表示换行符，如片段 [13] 所示：

![](img/34b7fc2f1ee27beb73bca14927d42340_322_2.png)

```
In [12]: lines = """This    is line 1
...:     This is line2
...:     This is     line3"""

In [13]: lines
Out[13]: 'This is line 1\nThis is line2\nThis is line3'
```

```
In [14]: lines.splitlines()
Out[14]: ['This is line 1', 'This is line2', 'This is line3']
```

向 splitlines 传递 True 会保留每个字符串末尾的换行符：

单击此处查看代码图像

```
In [15]: lines.splitlines(True)
Out[15]: ['This is line 1\\n', 'This is line2\\n', 'This is line3']
```

## 8.10 字符和字符测试方法

许多编程语言都有单独的字符串和字符类型。在 Python 中，字符仅仅是一个单字符字符串。

Python 提供字符串方法来测试字符串是否符合某些特征。例如，如果调用该方法的字符串仅包含数字字符（0–9），则字符串方法 isdigit 返回 True。当验证必须仅包含数字的用户输入时，你可以使用此方法：

单击此处查看代码图像

```
In [1]: '-27'.isdigit()
Out[1]: False

In [2]: '27'.isdigit()
Out[2]: True
```

如果调用该方法的字符串是字母数字（即仅包含数字和字母），则字符串方法 isalnum 返回 True：

单击此处查看代码图像

```
In [3]: 'A9876'.isalnum()
Out[3]: True

In [4]: '123 Main Street'.isalnum()
Out[4]: False
```

下表显示了许多字符测试方法。如果满足所述条件，每个方法都返回 True，否则返回 False：

| 字符串方法 | 说明 |
| :--- | :--- |
| `isalnum()` | 如果字符串仅包含 *字母数字* 字符（即数字和字母），则返回 `True`。 |
| `isalpha()` | 如果字符串仅包含 *字母* 字符，则返回 `True`。 |
| `isdecimal()` | 如果字符串仅包含 *十进制整数* 字符（即基数为 10 的整数）且不包含 `+` 或 `-` 符号，则返回 `True`。 |
| `isdigit()` | 如果字符串仅包含数字（例如，`'0'`、`'1'`、`'2'`），则返回 `True`。 |
| `isidentifier()` | 如果字符串表示有效的 *标识符*，则返回 `True`。 |
| `islower()` | 如果字符串中的所有字母字符均为 *小写* 字符（例如，`'a'`、`'b'`、`'c'`），则返回 `True`。 |
| `isnumeric()` | 如果字符串中的字符表示 *数值* 且不包含 `+` 或 `-` 符号和小数点，则返回 `True`。 |
| `isspace()` | 如果字符串仅包含 *空白* 字符，则返回 `True`。 |
| `istitle()` | 如果字符串中每个单词的首字符是单词中唯一的大写字符，则返回 `True`。 |
| `isupper()` | 如果字符串中的所有字母字符均为大写字符（例如，`'A'`、`'B'`、`'C'`），则返回 `True`。 |

## 8.11 原始字符串

请记住，字符串中的反斜杠字符引入转义序列——例如 \n 表示换行符，\t 表示制表符。因此，如果希望在字符串中包含反斜杠，则必须使用两个反斜杠字符 \\。这会使某些字符串难以读取。例如，Microsoft Windows 在指定文件位置时使用反斜杠分隔文件夹名称。要表示 Windows 上的文件位置，你可能会编写：

单击此处查看代码图像

```
In [1]: file_path = 'C:\\MyFolder\\MySubFolder\\MyFile.txt'

In [2]: file_path
Out[2]: 'C:\\MyFolder\\MySubFolder\\MyFile.txt'
```

对于此类情况，以字符 r 开头的原始字符串更方便。它们将每个反斜杠视为普通字符，而非转义序列的开头：

单击此处查看代码图像

```
In [3]: file_path = r'C:\\MyFolder\\MySubFolder\\MyFile.txt'

In [4]: file_path
Out[4]: 'C:\\MyFolder\\MySubFolder\\MyFile.txt'
```

Python 将原始字符串转换为常规字符串，其内部表示中仍使用两个反斜杠字符，如上一个片段所示。原始字符串可以使代码更易读，尤其是在使用下一节将讨论的正则表达式时。正则表达式通常包含许多反斜杠字符。

## 8.12 正则表达式简介

有时你需要在文本中识别 *模式*，例如电话号码、电子邮件地址、邮政编码、网页地址、社会安全号码等。一个 **正则表达式** 字符串描述了用于 *匹配* 其他字符串中字符的 *搜索模式*。

正则表达式可以帮助你从非结构化文本（如社交媒体帖子）中提取数据。它们还非常重要，可确保在尝试处理数据之前数据格式正确。³

³ 正则表达式主题可能比你使用过的大多数其他 Python 功能更具挑战性。掌握此主题后，你通常会编写比使用常规字符串处理技术更简洁的代码，从而加快代码开发过程。你还将处理平时可能不易考虑的边缘情况，从而可能避免微妙的错误。

### 验证数据

在处理文本数据之前，你通常会使用正则表达式来 *验证数据*。例如，你可以检查：

- 美国邮政编码由五个数字组成（例如 02215）或五个数字后跟连字符和四个额外数字（例如 02215-4775）。
- 姓氏字符串仅包含字母、空格、撇号和连字符。
- 电子邮件地址仅包含允许顺序中的允许字符。
- 美国社会安全号码包含三个数字、一个连字符、两个数字、一个连字符和四个数字，并遵循关于每组数字中可使用的特定数字的其他规则。

你很少需要为这些常见项目创建自己的正则表达式。类似以下网站：

- https://regex101.com
- http://www.regexlib.com
- https://www.regular-expressions.info

