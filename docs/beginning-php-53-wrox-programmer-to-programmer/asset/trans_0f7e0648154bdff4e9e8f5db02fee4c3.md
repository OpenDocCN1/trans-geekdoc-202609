

# 字符串

你在第 3 章中简要地看过了字符串的概念。在编程术语中，字符串简单来说就是字符序列。例如，值 "hello""how are you?""123" 和 "!@#$%" 都是有效的字符串值。

从根本上说，Web 是基于字符串数据的。HTML 和 XHTML 由纯文本字符串组成，HTTP 头部信息（将在第 16 章中详细介绍）以及当然的 URL 也是如此。正如你想象的，这意味着像 PHP 这样的 Web 编程语言专门为处理字符串而设计的。事实上，PHP 有近 100 个直接用于字符串操作的内置函数。

例如，你可以使用 PHP 的字符串函数来：

- 在字符串中搜索文本
- 将字符串中的某些文本替换为另一个字符串
- 格式化字符串以便更易阅读或处理
- 使用流行的编码格式对字符串进行编码和解码

除了这些之外，你还可以使用正则表达式（你将在第 18 章学习它们）来处理字符串。

在本章中，你将学习 PHP 字符串的基础知识——如何创建字符串和变量，以及如何访问字符串中的字符。然后你将探索 PHP 的字符串函数。本章并不旨在涵盖 PHP 中的每一个字符串函数；这个主题本身就可以写成一整本书。相反，你将学习在日常情况下可能需要的最有用（最常用）的函数。

> 如果你想查看 PHP 字符串函数的完整列表，可以在 PHP 在线手册找到：www.php.net/manual/en/ref/strings.php。

# 第二部分：学习语言

## 创建和访问字符串

正如你在第 3 章中学的，创建一个字符串就像给新变量名分配字符串字面量值一样简单：

```php
$myString = 'hello';
```

在这个示例中，字符串字面量 (hello) 被包含在单引号（'）中。你也可以使用双引号（"),如下：

```php
$myString = "hello";
```

单引号和双引号的作用不同。如果你将字符串包含在单引号中，PHP 将完全按照输入的方式使用字符串。然而，双引号为你提供了一些额外功能：

- 字符串中的任何变量名都会解析并替换为变量的值
- 你可以通过转义在字符串中包含特殊字符

以下是一些示例，以让你清楚这些区别：

对于 "Hello, world!"，注意双引号允许将 $myString 变量替换为 $myString 的实际值。然而，使用单引号时，文本 $myString 将原样保留。

对于使用的 "Hi there" 示例，\ 被替换为实际的制表符；因此输出中 Hi 和 there 之间有很大的间隙！包含在单引号中的相同字符串会导致 \ 字符被直接传递。

以下是你可以在双引号字符串中使用的更常用的序列列表：

| 序列 | 含义 |
| :--- | :--- |
| \n | 换行符 (ASCII 10) |
| \r | 回车 (ASCII 13) |
| \t | 水平制表符 (ASCII 9) |
| \v | 垂直制表符 (ASCII 11) |
| \f | 换页 (ASCII 12) |
| \\ | 反斜杠（与转义序列的开头相反） |
| \$ | $ 符号（与变量名的开头相反） |
| \* | 双引号（与标记字符串结束的双引号相反） |

# 第 5 章：字符串

在单引号字符串中，你实际上可以使用一些转义序列。使用 \ 在字符串中包含字面量单引号。如果你恰好想在单引号字符串中包含字面量字符 \，请使用 \\——即一个转义的反斜杠后跟一个转义的引号。

通过这种方式，你可以在 PHP 中定义多行字符串。要这样做，在引号之间插入换行符：

```php
$myString = "
I stay long; but my Father comes:
A blessing is a double grace;
league";
```

# 在字符串中包含复杂表达式

你可以通过包含变量（以 $ 符号开头）在双引号字符串中插入变量的值，有时这会变得复杂。考虑以下情况：

```php
$favoriteAnimal = "cat";
echo "My favorite animals are $favoriteAnimals";
```

这段代码存在歧义；PHP 应该插入 $favoriteAnimal 的值加上 "s" 字符吗？还是插入（不存在的）变量 $favoriteAnimals？事实上，PHP 尝试后者，结果是：

My favorite animals are

幸运的是，你可以使用大括号解决这个问题，如下所示：

```php
$favoriteAnimal = "cat";
echo "My favorite animals are {$favoriteAnimal}";
```

这产生了结果：

My favorite animals are cats

你也可以在 $ 符号后放置左大括号，效果相同：

```php
echo "My favorite animals are {$favoriteAnimal}";
```

重要的是，你可以使用大括号来区分变量名和字符串的其余部分。你可以使用大括号语法插入复杂的变量值，例如数组元素和属性（你将在接几章学习数组和对象）。只需确保整个表达式被大括号包围即可：

```php
$Array["age"] = 34;
echo "My age is {$Array["age"]}"; // 显示 "My age is 34",
```

当然，如果你不想使用大括号，可以通过拼接字符串值来创建字符串：

# 使用自定义分隔符

在大多数情况下，引号是字符串字面量的良好分隔符，有时使用自定义分隔符会有帮助。如果你需要指定包含大量单引号和双引号的长字符串，在字符串内转义许多引号是非常的。你可以通过两种方式使用自定义分隔符：heredoc 语法和 nowdoc 语法。Heredoc 等同于使用双引号：变量名被替换为变量值，并且可以使用转义序列来表示特殊字符。Heredoc 的工作方式如下：

```php
$String = <<DELIMITER
(insert string here)
DELIMITER;
```

DELIMITER 是你想用分隔符的文本。它必须只包含字母、数字和下划线，并且以字母或下划线开头。传统上，heredoc 分隔符大写，就像常量一样。nowdoc 语法类似，区别在于分隔符被包含在单引号内：

```php
$String = <<'DELIMITER'
(insert string here)
DELIMITER;
```

这是一个 heredoc 语法示例：

```php
$religion = 'Hebrew';

$String = <<END_TEXT
"I am a $religion, he cries and then 'I fear the Lord of God had made the sea and the dry land!'"
END_TEXT;

echo "<pre>$String</pre>";
```

此示例显示以下输出：

```
"I am a Hebrew, he cries and then 'I fear the Lord of God who had made the sea and the dry land!'"
```

这是使用 nowdoc 语法的相同示例：

```php
$religion = 'Hebrew';

$myString = <<END_TEXT
"I am a $religion, he cries and then 'I fear the Lord of God
Heaven who made the sea and the dry land!"
END_TEXT;

echo "<pre>$myString</pre>";
```

此内容的输出如下（注意这次 $religion 变量没有被替换）：

"I am a $religion, he cries and then 'I fear the Lord of God Heaven who made the sea and the dry land!"

nowdoc 语法是在 PHP 5.3.0 中引入的。

# 创建字符串的其他方法

你不需要分配量值来创建字符串变量；你可以分配任何表达式的结果：

```php
$myString = $yourString;
$myString = "how " . "are " . "you";
$myString = ($x > 100) ? "Big number" : "Small number";
```

许多 PHP 函数返回字符串值，你可以将其赋值给变量（或在浏览器中显示）。例如，你在第 11 章中学习的 file_get_contents() 将文件内容读取到字符串中。

# 查找字符串的长度

一旦你有了字符串变量你就可以用 strlen() 函数找到它的长度。该函数接受一个字符串值作为参数，并返回其中字符的数量。例如：

```php
$myString = "hello";
echo strlen($myString) . "<br />"; // 显示 5
echo strlen("goodbye") . "<br />"; // 显示 7
```

如果你想遍历字符串中的所有字符，或者想验证字符串以确保其长度正确，strlen() 经常非常有用。例如，以下代码确保字符串变量 $year 的长度为 4 个字符：

```php
if (strlen($year) != 4) {
    echo "年份需要包含 4 个字符。请重试。";
}
else {
    // 处理年份
}
```

