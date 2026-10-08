

## 核心 PHP 编程

正则表达式提供了一种强大的方法来测试字符串中是否存在特定模式。它们使用一种自己的语言来描述模式，这种语言主要由符号组成。PHP 有几个使用正则表达式的函数。你可能希望查看第 16 章，该章节详细介绍了正则表达式。

### 布尔型 ereg(string pattern, string text, array matches)

`ereg` 函数将 `pattern` 参数评估为正则表达式，并尝试在 `text` 参数中查找匹配项。如果提供了可选的 `matches` 参数，则每个匹配项都将添加到数组中。如果至少有一个匹配项，则返回 TRUE，否则返回 FALSE。

`matches` 数组中的第一个元素（索引为0）将包含整个正则表达式的匹配项。`matches` 的后续元素将包含子表达式的匹配项。这些是示例中用括号括的表达式。

此函数在第 16 章中讨论。

```php
<?php
// show User Agent
print("User Agent: $HTTP_USER_AGENT<BR>\n");

// try to parse User Agent
if (ereg("^.+)/([0-9]+)\.\(", $HTTP_USER_AGENT, $matches)) {
    print("Full match: $matches[0]<BR>\n");
    print("Browser: $matches[1]<BR>\n");
    print("Major Version: $matches[2]<BR>\n");
    print("Minor Version: $matches[3]<BR>\n");
} else {
    print("User Agent not recognized");
}
?>
```

### 字符串 ereg_replace(string pattern, string replacement, string text)

使用 `ereg_replace` 替换文本中的子字符串。每当模式匹配 `text` 参数中的子字符串时，它就会被 `replacement` 参数替换。`text` 参数本身保持不变，但会返回修改后的版本。

如果模式中包含括号中的子表达式，`replacement` 参数可以包含一个特殊代码，用于指定要替换哪个子表达式。格式是使用两个反斜杠后跟一个数字（0 到 9）。0 匹配整个表达式；1 到 9 分别匹配对应的子表达式。子表达式从左到右编号，这考虑了嵌套的子表达式。

正则表达式在第 16 章中有深入讨论。

图 9-11. ereg_replace。

![](img/58e6a0f5d6a8a41d4645d8c07b3bf1e3_284_0.png)

```php
<?php
// swap newlines for break tags
$text = "line1\nline2\nline3\n";
print (ereg_replace("\n", "<BR>", $text));
```

```php
<?php
print("*<HR\n");
```

```php
<?php
//mix up these words
$text = "one two three four";
print (ereg_replace("/([a-z]+) ([a-z]+) ([a-z]+) ([a-z]+)/", "\4 \2 \3", $text));
```

### 布尔型 eregi(string pattern, string text, array matches)

`eregi` 函数的操作与 `ereg` 相同，不同之处在于匹配字母时时不区分大小写。

正则表达式在第 16 章中有深入讨论。

### 字符串 eregi_replace(string pattern, string replacement, string text)

`eregi_replace` 函数的操作与 `ereg_replace` 相同，不同之处在于不区分大小写。

### 数组 split(string pattern, string text, integer limit)

`split` 函数从 `text` 参数中返回一个子字符串数组。`pattern` 参数将作为字段分隔符。可选的 `limit` 参数设置返回的最大元素数量。`split` 没有不区分大小写的版本。

将此函数与 `explode` 比较，后者使用简单的字符串来分隔子字符串。正则表达式的处理比直接的字符串匹配慢，因此在可能的情况下请使用 `explode`。

```php
<?php
$paragraph = "This is a short paragraph. Each ";
$paragraph .= "sentence will be extracted by ";
$paragraph .= "the split function. As a ";
$paragraph .= "result, you will be amazed!";

$sentence = split("\\.!\?", $paragraph);

for($index = 0; $index < count($sentence); $index++)
{
    print("\$index. $sentence[$index]<BR\n");
}
?>
```

## Perl 兼容正则表达式 (PCRE)

Andrei Zievski 为 PHP 增加了对 Perl 兼容正则表达式的支持。表达式被分隔符包围，通常是 `/` 或 `|` 字符，可以是数字、字母或反斜杠以外的任何打印字符。在第二个分隔符之后，你可以放置一个或多个修饰。这些是改变正则表达式解释方式的字母。

在大多数情况下，本节中的函数符合 Perl 5 中的正则表达式工作方式。有少数非常小的差异。由于范围很窄，你可能不会遇到，而且在详细解释正则表达式之前，它们可能没有太大意义。如果你感兴趣，可以阅读 PHP 在线手册中的优秀笔记 <http://www.php.net/manual/html/ref.pcre.html》。

### 数组 preg_grep(string pattern, array data)

`preg_grep` 函数比较 `data` 参数中匹配给定模式的元素。

### 布尔型 preg_match(string pattern, string text, array matches)

`preg_match` 函数是 `ereg` 的等效函数。它将 `pattern` 评估为正则表达式并尝试在 `text` 中查找匹配项。如果提供了可选的 `matches` 参数，则每个匹配项都将添加到数组中。如果至少有一个匹配项，则返回 TRUE，否则返回 FALSE。

`matches` 数组中的第一个元素（索引为0）将包含整个正则表达式的匹配项。`matches` 的后续元素将包含子表达式的匹配项。这些是示例中用括号括的表达式。

```php
<?php
// show User Agent
print("User Agent: $HTTP_USER_AGENT<BR>\n");

// try to parse User Agent
if (ereg("^.+)/([0-9]+)\.\(", $HTTP_USER_AGENT, $matches)) {
    print("Full match: $matches[0]<BR>\n");
    print("Browser: $matches[1]<BR>\n");
    print("Major Version: $matches[2]<BR>\n");
    print("Minor Version: $matches[3]<BR>\n");
} else {
    print("User Agent not recognized");
}
?>
```

### 整数 preg_match_all(string pattern, string text, array matches, integer order)

`preg_match_all` 函数的操作与 `preg_match` 类似，但不是在找到匹配时停止，而是寻找后续的匹配项。`matches` 参数是必须的，并将接收一个二维数组。填充此数组的方法由 `order` 参数决定。它可以设置为 `PREG_PATTERN_ORDER`（默认值）或 `PREG_SET_ORDER`。

图 9-12. preg_match_all.

![](img/58e6a0f5d6a8a41d4645d8c07b3bf1e3_284_0.png)

