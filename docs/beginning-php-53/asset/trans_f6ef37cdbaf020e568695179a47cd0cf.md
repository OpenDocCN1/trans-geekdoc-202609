

```php
echo preg_match( "/^\\d+:/", "12: The Sting" ); // Displays "1"
echo preg_match( "/^\\d+:/", "Die Hard 2: Die Harder" ); // Displays "0"
```

脱字符（^）指定模式的其余部分仅在字符串开头处匹配。同样，你可以使用美元符号（$）将模式锚定到字符串末尾：

```php
echo preg_match( "/\\([G|PG|PG-13|R|NC-17)\\)$/", "The Sting [PG]" ); // Displays "1"
echo preg_match( "/\\([G|PG|PG-13|R|NC-17)\\)$/", "[PG] Amadeus" ); // Displays "0"
```

通过组合这两个锚点，你可以确保字符串仅包含所需的模式，不包含其他内容：

```php
echo preg_match( "/^Hello, \\w+$/", "Hello, world" ); // Displays "1"
echo preg_match( "/^Hello, \\w+$/", "Hello, world!" ); // Displays "0"
```

第二次匹配失败，因为目标字符串在所查找的模式和字符串末尾之间包含一个非单词字符（!）。

你可以使用其他锚点来更好地控制匹配。以下是可在正则表达式中使用的锚点完整列表：

| 锚点 | 含义 |
| :--- | :--- |
| ^ | 在字符串开头处匹配 |
| $ | 在字符串末尾处匹配 |
| \\b | 在单词边界处匹配（\\w 字符和 \\W 字符之间） |
| \\B | 在非单词边界处匹配 |
| \\A | 在字符串开头处匹配 |
| \\z | 在字符串末尾处匹配 |
| \\Z | 在字符串末尾处匹配，或在字符串末尾的换行符之前匹配 |
| \\G | 在传递给 preg_match() 函数的起始偏移字符位置处匹配 |

需要注意的是，锚点本身不匹配任何字符；它只是确保模式出现在目标字符串的指定位置。

\A 和 \z 与 ^ 和 $ 相似。区别在于，如果在多行模式下匹配多行字符串（本章后面“使用模式修饰符更改匹配行为”部分将解释），^ 和 $ 也会分别匹配行的开头和结尾。\A 和 \z 仅分别匹配目标字符串的开头和结尾。

\z 在从文件中读取行时很有用，这些行末尾可能有换行符，也可能没有。

\b 和 \B 在搜索文本中的完整单词时非常方便：

```php
echo preg_match( "/over/", "My hovercraft is full of eels" ); // Displays "1"
echo preg_match( "/\bover\b/", "My hovercraft is full of eels" ); // Displays "0"
echo preg_match( "/\bover\b/", "One flew over the cuckoo's nest" ); // Displays "1"
```

使用 \b 时，字符串的开头或结尾也被视为单词边界：

```php
echo preg_match( "/\bover\b/", "over and under" ); // Displays "1"
```

通过使用 \b 锚点，以及子表达式中的备选项，可以进一步增强早期的“日期检测”示例，使其仅匹配两位或四位年份（而不匹配三位年份）：

```php
echo preg_match ( "/\b(jan|feb|mar|apr|may|jun|jul|aug|sep|oct|nov|dec)" .
"\/\d(1,2)\/(\d{2}|\d{4})\b/", "jul/15/2006" ); // Displays "1"
echo preg_match ( "/\b(jan|feb|mar|apr|may|jun|jul|aug|sep|oct|nov|dec)" .
"\/\d(1,2)\/(\d{2}|\d{4})\b/", "jul/15/206" ); // Displays "0"
```

表达式的最后一部分读作：“匹配两位或四位数字，后跟单词边界（或字符串结尾）”：

```
(\d{2}|\d{4})\b
```

你还可以创建自己的锚点类型；例如，你可以仅在文本出现在和号之前时匹配，或仅在其出现在大写字母之后时匹配（而不实际将和号或大写字母包含在匹配中）。这种自定义锚点称为前瞻和后顾断言，超出了本章的范围；不过，你可以在 PHP 手册中阅读有关它们的内容，网址为 http://www.php.net/manual/en/regexp.reference.assertions.php。

## 使用 preg_match_all() 查找多个匹配项

虽然 preg_match() 函数在许多字符串匹配场景中很有用，但它只在目标字符串中找到第一个模式匹配。有时你想查找字符串中的所有匹配项。例如，你可能想提取电子邮件消息中提到的所有电话号码列表，或统计 HTML 网页中的链接数量。

要查找字符串中正则表达式的所有匹配项，请使用 `preg_match_all()` 函数。`preg_match_all()` 接受与 `preg_match()` 相同的参数：

- 正则表达式
- 要搜索的字符串
- 用于保存匹配项的数组（注意，对于 `preg_match_all()`，数组不是可选的）
- 匹配操作的可选标志
- 开始搜索的可选偏移量

与 `preg_match()` 类似，`preg_match_all()` 将匹配项数作为整数返回。与 `preg_match()` 不同，后者的返回值只能是 0 或 1，而 `preg_match_all()` 返回字符串中的匹配项总数：

```php
$text = "Call Mary on 499 012 3456, John on 876 543 2101, or Karen:
777 111 2345";
echo preg_match_all( "/\b\d{3} \d{3} \d{4}\b/", $text, $matches ); //
Displays "3"
```

`preg_match_all()` 将所有匹配项存储在作为第三个参数传递给它的数组中。匹配项存储在数组的第一个元素中（索引为零），作为嵌套数组：

```php
$scores = "John: 143 points, Anna: 175 points, and Nicole: 119 points";
preg_match_all( "/\w+:\s\d+ points/", $scores, $matches );
echo $matches[0][0] . "<br />"; // Displays "John: 143 points"
echo $matches[0][1] . "<br />"; // Displays "Anna: 175 points"
echo $matches[0][2] . "<br />"; // Displays "Nicole: 119 points"
```

```
// The following code displays:
//
// John scored 143
// Anna scored 175
// Nicole scored 119
```

如果你的表达式包含子模式，则来自这些子模式的文本匹配项存储在后续数组元素中。请参考以下示例：

```php
$scores = "John: 143 points, Anna: 175 points, and Nicole: 119 points";
preg_match_all( "/(\w+):\s(\d+) points/", $scores, $matches );
echo $matches[0][0] . "<br />"; // Displays "John: 143 points"
echo $matches[0][1] . "<br />"; // Displays "Anna: 175 points"
echo $matches[0][2] . "<br />"; // Displays "Nicole: 119 points"
```

```
// The following code displays:
//
// John scored 143
// Anna scored 175
// Nicole scored 119
```

```php
echo $matches[1][0] . " scored " . $matches[2][0] . "<br />";
echo $matches[1][1] . " scored " . $matches[2][1] . "<br />";
echo $matches[1][2] . " scored " . $matches[2][2] . "<br />";
```

从这个示例可以看出，索引为 1 的元素是一个嵌套数组，包含来自第一个子模式（玩家姓名）的所有匹配项，而索引为 2 的元素包含来自第二个子模式（分数）的所有匹配项。表达式中的每个子模式，匹配项数组中都会创建一个额外元素。

如果你愿意，可以让 preg_match_all() 交换索引，使第一个索引表示匹配项编号，第二个索引表示子模式编号。（你可能会发现这种方式的数组更易于处理。）要实现此目的，请将 PREG_SET_ORDER 标志作为第四个参数传递给 preg_match_all()：

```php
$scores = "John: 143 points, Anna: 175 points, and Nicole: 119 points";
preg_match_all( "/(\w+)\:\s(\d+) points/", $scores, $matches, PREG_SET_ORDER
);
echo $matches[0][0] . "<br />"; // Displays "John: 143 points"
echo $matches[1][0] . "<br />"; // Displays "Anna: 175 points"
echo $matches[2][0] . "<br />"; // Displays "Nicole: 119 points"
```

```
// The following code displays:
// John scored 143
// Anna scored 175
// Nicole scored 119
```

```php
echo $matches[0][1] . " scored " . $matches[0][2] . "<br />";
echo $matches[1][1] . " scored " . $matches[1][2] . "<br />";
echo $matches[2][1] . " scored " . $matches[2][2] . "<br />";
```

请注意，数组元素的嵌套已被颠倒。匹配项数组中的每个顶层元素现在都是一个嵌套数组，其中包含作为元素 0 的完整匹配字符串，以及作为元素 1 和 2 的每个子模式匹配项。

与 preg_match() 类似，你也可以传递 PREG_OFFSET_CAPTURE 标志以访问目标字符串中每个匹配项（或子模式匹配项）的位置。这会使每个匹配项作为两个元素的嵌套数组返回（而不是字符串），第一个元素是匹配的文本，第二个元素是偏移量。最终结果是，匹配项数组包含三层嵌套：子模式编号（整个模式则为零），然后是匹配项编号，然后是匹配的文本和偏移量。例如：

```php
$scores = "John: 143 points, Anna: 175 points, and Nicole: 119 points";
preg_match_all( "/(\w+)\:\s(\d+) points/", $scores, $matches,
PREG_OFFSET_CAPTURE );
```

```
// The following code displays:
// John: 143 points (position: 0)
// Anna: 175 points (position: 18)
// Nicole: 119 points (position: 40)
```

```php
echo $matches[0][0][0] . " (position: " . $matches[0][0][1] . ")<br />";
echo $matches[0][1][0] . " (position: " . $matches[0][1][1] . ")<br />";
echo $matches[0][2][0] . " (position: " . $matches[0][2][1] . ")<br />";
```

你可以按以下方式组合 PREG_SET_ORDER 和 PREG_OFFSET_CAPTURE：

```php
preg_match_all( "/(\w+)\:\s(\d+) points/", $scores, $matches, PREG_SET_ORDER
| PREG_OFFSET_CAPTURE );
```

在这种情况下，匹配项数组的顶层将包含匹配项编号，第二层将包含子模式编号，第三层将包含匹配的文本和偏移量。

