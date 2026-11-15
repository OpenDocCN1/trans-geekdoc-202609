

另一个有用的相关函数是 `str_word_count()`，它返回字符串中的单词数。例如：

```php
echo str_word_count( "Hello, world!" ); // Displays 2
```

## 访问字符串中的字符

你可能在想如何访问字符串中的单个字符。PHP 让这变得很容易。要访问字符串中特定位置，或 _索引_，的字符，请使用：

```php
$character = $string[index];
```

换句话说，你在字符串变量名后的方括号中放置索引。字符串索引从 0 开始，因此字符串中的第一个字符索引为 0，第二个字符索引为 1，以此类推。你可以通过这种方式读取和更改字符。以下是一些示例：

```php
$myString = "Hello, world!";
echo $myString[0] . "<br />"; // Displays 'H'
echo $myString[7] . "<br />"; // Displays 'w'
$myString[12] = '?';
echo $myString . "<br />"; // Displays 'Hello, world?'
```

如果需要从字符串中提取一系列字符，可以使用 PHP 的 `substr()` 函数。该函数接受以下参数：

- 要从中提取字符的字符串
- 开始提取字符的位置。如果使用负数，`substr()` 将从字符串末尾开始倒数
- 要提取的字符数。如果使用负数，`substr()` 会从字符串末尾跳过那么多字符，而不是提取。此参数为可选；如果省略，`substr()` 将从起始位置提取到字符串末尾

以下是一些展示如何使用 `substr()` 的示例：

```php
$myString = "Hello, world!";
echo substr( $myString, 0, 5 ) . "<br />"; // Displays 'Hello'
echo substr( $myString, 7 ) . "<br />"; // Displays 'world!'
echo substr( $myString, -1 ) . "<br />"; // Displays '!'
echo substr( $myString, -5, -1 ) . "<br />"; // Displays 'orld'
```

你不能使用 `substr()` 修改字符串中的字符。如果需要更改字符串中的字符，请改用 `substr_replace()`。本函数将在本章后面介绍。

## 搜索字符串

了解一段文本是否包含在另一段文本中通常很有用。PHP 提供了几个字符串函数，让你可以在一个字符串中搜索另一个字符串：

- strstr() 告诉你搜索文本是否在字符串中
- strpos() 和 strrpos() 分别返回搜索文本首次和最后出现的索引位置
- substr_count() 告诉你搜索文本在字符串中出现的次数
- strpbrk() 在字符串中搜索字符列表中的任意字符

### 使用 strstr() 搜索字符串

如果你只想知道某段文本是否出现在字符串中，请使用 strstr()。它接受两个参数：要搜索的字符串和搜索文本。如果找到文本，strstr() 返回从找到的文本开始到字符串结束的部分。如果未找到文本，它返回 false。例如：

```php
$myString = "Hello, world!";
echo strstr( $myString, "wor" ) . "<br />"; // Displays 'world!'
echo ( strstr( $myString, "xyz" ) ? "Yes" : "No" ) . "<br />"; // Displays 'No'
```

从 PHP 5.3 开始，你还可以传递一个可选的第三个布尔参数。默认值为 false。如果传入 true，strstr() 则返回从字符串开始到找到的文本之前字符的部分：

```php
$myString = "Hello, world!";
echo strstr( $myString, "wor", true ); // Displays 'Hello, '
```

### 使用 strpos() 和 strrpos() 定位文本

要找出一段文本在另一字符串中的确切位置，请使用 strpos()。此函数接受与 strstr() 相同的两个参数：要搜索的字符串和要查找的搜索文本。如果找到文本，strpos() 返回文本在字符串中首个字符的索引。如果未找到，strpos() 返回 false：

```php
$myString = "Hello, world!";
echo strpos( $myString, "wor" ); // Displays '7'
echo strpos( $myString, "xyz" ); // Displays '' (false)
```

当搜索的文本出现在字符串开头时，存在一个陷阱。在这种情况下，strpos() 返回 0（找到的文本的首个字符索引），但如果不小心，很容易将其误认为是 false 的返回值。例如，以下代码将错误地显示 "Not found"：

```php
$myString = "Hello, world!";
if ( !strpos( $myString, "Hel" ) ) echo "Not found";
```

因此，如果你要检查的是 false 返回值，需要显式测试。以下代码可以正确工作：

```php
$myString = "Hello, world!";
if ( strpos( $myString, "Hel" ) === false ) echo "Not found";
```

strpos() 可以接受一个可选的第三个参数：字符串中开始搜索的索引位置。以下是一个示例：

```php
$myString = "Hello, world!";
echo strpos( $myString, "o" ) . "<br />"; // Displays '4'
echo strpos( $myString, "o", 5 ) . "<br />"; // Displays '8'
```

你可以使用这个第三个参数，结合 strpos() 返回匹配文本位置的事实，来反复查找字符串中搜索文本的所有出现——例如：

```php
$myString = "Hello, world!";
$pos = 0;
while ( ( $pos = strpos( $myString, "l", $pos ) ) !== false ) {
    echo "The letter 'l' was found at position: $pos<br />" ;
    $pos++;
}
```

此代码产生图 5-1 所示的输出。

![](img/1ddec54918a4802eb9b4febec3d4e7f6_117_0.png)

图 5-1

strpos() 有一个姊妹函数 strrpos()，功能基本相同；唯一的区别是 strrpos() 查找字符串中的最后一个匹配项，而不是第一个：

```php
$myString = "Hello, world!";
echo strpos( $myString, "o" ) . "<br />" ; // Displays '4'
echo strrpos( $myString, "o" ) . "<br />" ; // Displays '8'
```

与 strpos() 类似，你可以传递一个可选的第三个参数，指示开始搜索的索引位置。如果此索引位置为负数，strrpos() 将从字符串末尾开始向前数那么多字符，而不是从开头开始。

### 使用 substr_count() 查找出现次数

偶尔你可能需要知道某段文本在字符串中出现的次数。例如，如果你正在编写一个简单的搜索引擎，可以在文本字符串中搜索关键字，以查看该文本对关键字的相关性；关键字出现的次数越多，文本相关的可能性就越大。

你可以使用 `strpos()` 和循环轻松找出出现次数，但 PHP 像大多数其他事情一样，为你提供了一个完成这项工作的函数：`substr_count()`。要使用它，只需传递要搜索的字符串和要查找的文本，函数将返回该文本在字符串中被找到的次数。例如：

```php
$myString = "I say, nay, nay, and thrice nay!";
echo substr_count( $myString, "nay" ); // Displays '3'
```

你还可以传递一个可选的第三个参数来指定开始搜索的索引位置，以及一个可选的第四个参数来指示函数在放弃前应搜索多少个字符。以下是使用这些第三个和第四个参数的一些示例：

```php
$myString = "I say, nay, nay, and thrice nay!";
echo substr_count( $myString, "nay", 9 ) . "<br />"; // Displays '2'
echo substr_count( $myString, "nay", 9, 6 ) . "<br />"; // Displays '1'
```

### 使用 strpbrk() 搜索字符集

如果你需要找出字符串是否包含某个字符集中的任意一个字符，该怎么办？例如，你可能希望确保提交的表单字段出于安全原因不包含某些字符。PHP 为你提供了一个名为 `strpbrk()` 的函数，让你可以轻松执行此类搜索。它接受两个参数：要搜索的字符串和包含要查找的字符列表的字符串。该函数返回从第一个匹配字符到字符串末尾的部分。如果字符串中未找到该字符集中的任何字符，`strpbrk()` 返回 false。

以下是一些示例：

```php
$myString = "Hello, world!";
echo strpbrk( $myString, "abcdef" ); // Displays 'ello, world!'
echo strpbrk( $myString, "xyz" ); // Displays '' (false)
```

```php
$username = "matt@example.com";
if ( strpbrk( $username, "@!" ) ) echo "@ and ! are not allowed in usernames";
```

### 替换字符串中的文本

除了能够在较大字符串中搜索文本外，你还可以用不同的文本替换字符串的部分内容。本节讨论了三个用于替换文本的有用 PHP 函数：

- str_replace() 替换目标字符串中搜索文本的所有出现
- substr_replace() 将目标字符串的指定部分替换为另一个字符串
- strtr() 将目标字符串中的某些字符替换为其他字符

### 使用 str_replace() 替换所有出现

str_replace() 让你将指定字符串的所有出现替换为新字符串。它相当于在文字处理器中使用“全部替换”选项。

