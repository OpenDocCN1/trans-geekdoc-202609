
在你编写的每个 Web 应用程序中，需要做的最重要的事情之一就是确保 Web 页面的用户没有传递你的恶意文本。正如我们在第 8 章中讨论的，如果你不小心，可能会发现你的页面充满了你不想要的 HTML 标签（如 `<img>`、`<div>` 等）或 JavaScript。如果某些字符决定在你的表单字段中乱扔一样丢入像 `<script> alert("you stink");</script>` 这样的内容，你也会发现结果陷入。

`strip_tags()` 函数将移除所有的 HTML 和 PHP 标签，但第二个参数中显式允许的标签除外。如果你允许 `<b>` 和 `<i>` 标签，可以使用：

```
strip_tags($str, "<b><i></b>");
```

`ADDSLASHES()` 此函数旨在与你的数据库和更新语句配合。

```
string addslashes(string str);
```

如果你看一个典型的插入语句，你会发现一个潜在问题：

```
insert into table_name(char_field, numeric-field)
values ('$str', $num);
```

如果 `$str` 中的值包含像 "ain't" 这样的缩写怎么办？你可能会得到错误，因为单引号会混淆 MySQL。你需要转义字符串中出现的所有单引号（`'``）、双引号（`"`）和 NULL。例如：

```php
$str1 = "let's see";
$str2 = "you know";
$str1 = addslashes($str1);
$result = mysql_query("insert into show_stuff($stuff_desc, stuff_stuff) values('$str1', '$str2');\
echo mysql_affected_rows();
```

所以，鉴于这个问题，你需要对所有的表单输入都通过 `addslashes()` 吗？不一定。这取决于你的 `php.ini` 文件中的 `magic_quotes_gpc` 设置。如果它设置为 `on`（这是默认值），来自 Get、Post 或 Cookies 的数据会被自动转义，因此你不需要担心将信息通过 `addslashes()`。

## 第 6 章：PHP 内置函数

> 提示：确保检查你 `php.ini` 中的 `magic_quotes` 设置。再次提醒，你可以利用 MySQL 的描述性查询来实现相同的结果。查询 "show columns from table_name" 和 "describe table_name" 可以获取你所需的所有信息，从而让你无须使用这些函数。

例如：

```
$str = "Where is the final space";
echo strpos($str, " ");
```

将返回 "18"。

### SUBSTR()
此函数根据数字偏移量返回字符串的一部分。

```
string substr (string string, int start [, int length])
```

例如：

```
echo substr("this is my string", 5);
```

将返回第五个字符之后的所有内容。在这种情况下为 "is my string"。可选的第三参数可以表示要返回的字符数。例如：

```
echo substr("this is my string", 5,-2);
```

将返回 "is"。第四个参数中的负数指定字符串末尾的字符。例如：

```
echo substr("this is my string", 5,-7);
```

将打印 "is my"。

> 提示：`substr` 函数与 `strpos()` 和 `strpos()` 等函数配合非常好。

### STRREV()
此函数反转字符串的顺序。

```
string strrev (string string)
```

`strrev()` 在你的编程生涯中可能出现并不频繁。在书中，它被用于信用卡验证算法。

### STRTOLOWER()
此函数将整个字符串转换为小写。

```
string strtolower (string str)
```

当你在处理文件名等内容时特别有用。由于 Unix 文件名对大小写敏感，你可能希望确保你写入的所有文件都全小写字母。我们在处理密码时也会使用此函数。

### STR()
此函数获取第一个参数中的字符串，并将第二个参数中的每个字符翻译为第三个参数中对应的字符。

```
string strtr(string str, string from, string to)
or
string strtr(string str, each, associative array)
```

所以接接中的 *a* 将被调整为 *i*，每个 *o* 将转换为 *a*。

```
strtr($str, "ao", "iu")
```

注意它是一次完成所有替换的。例如，这段代码：

```
$str = "i";
echo strtr($str, "iu", "uv");
```

你可能认为该函数会先将 "i" 变成 "u"，然后将 "u" 变成 "v"。并非如此。它会批量进行替换，因此此操作的输出是 "u"。

此函数也可以仅用两个参数工作。在这种情况下，第二个参数应被替换为字符串中对应的值。

```
$str = "this are strings";
$replace_array = array("this"->"these", "is"->"are");
echo strtr($str, $replace_array);
```

这段代码打印 "these are strings"。再次：

### UCFIRST()
此函数将字符串中的第一个字符转换为大写。

```
string ucfirst(string str);
```

注意它保持了第一个字符之后的所有内容不变。如果你想确保字符串的第一个且仅是第一个字符大写，你必须执行类似这样的操作。

```
$str = "this is My string";
echo ucfirst(strtolower($str));
```

这将打印 "This is my string"。

### UCWORDS()
此函数将字符串中每个单词的第一个字母转换为大写。

```
string ucwords(string str);
```

像 `ucfirst()` 一样，`ucwords()` 不触碰不是单词开头的字符。

### TRIM()
此函数移除字符串开头和结尾的任何空白，包括回车符、换行符、空格和制表符。

```
string trim(string str)
```

PHP 还有 `ltrim()` 函数用于仅移除字符串开头的空白，或用 `chop()` 仅移除字符串结尾的空白。

### HTMLSPECIALCHARS
此函数将 <、>、& 转换为正确的 HTML 实体：&lt; &gt; &amp; 和 &quot;。

```
string htmlspecialchars(string string)
```

这对于向浏览器打印 HTML 源很有用。

除了 `htmlspecialchars()` 外，你还可以使用 `htmlentities()`。`htmlentities()` 转换每一个具有 HTML 实体的字符。例如，版权符号被转换为 &copy;。

### GET_HTML_TRANSLATION_TABLE()
此函数获取具有 HTML 实体的字符完整列表，或者 `htmlspecialchars()` 使用的字符。你可以通过在函数中包含 `HTML_ENTITIES` 或 `HTML_SPECIALCHARS` 来指定你需要访问的内容。例如 `get_html_translation_table(HTML_ENTITIES)` 会获取字符及其实体的完整列表。

每个字符及其实体都以键=>值对的形式存储在关联数组中。结果数组可以配合 `strtr()` 函数使用。

### NUMBER_FORMAT
此函数根据你的规范格式化数字。

```
string number_format(float number, int decimals, [[string dec_point], [string thousands_sep]])
```

第一个参数是你想要格式化的数字。第二个参数将指定位数。

## 第二部分：使用 PHP

你可以通过两种方式使用此函数。首先，你可以在第一个参数中放置一个正则表达式，并在第二个参数中检查它的是否存在。该函数将返回 TRUE 或 FALSE，取决于搜索结果。例如：

```php
if (ereg("http://.*", $str)) {
    echo "This is a URL:";
}
```

第三个参数是一个由正则表达式创建的数组。正则表达式中将成为元素的部分由正则表达式中的括号标出。

```
ereg("(....)(..)-(.*)", $publish_date, $date_array);
```

此示例节取自内容管理器（Content Manager）应用程序，它创建了一个数组 `$date_array`，其中第一个元素将是正则表达式匹配的完整字符串。数组中的接三个元素将是正则表达式所指示的部分。因此，`$date_array[1]` 将包含 4 个字符，而 `$date_array[2]` 和 `$date_array[3]` 将各包含 2 个字符。

请注意，通过 `ereg()` 的第三个参数创建的数组始终包含 11 个元素。即使你在括号内有超过 10 个子字符串，数组中也只包含前 10 个。如果你有少于 10 个子字符串，数组仍将包含 11 个元素。如果你想测试数组元素是否存在任何内容，必须针对空字符串（""")进行测试。`isset()` 将始终测试为 TRUE。运行此代码后：

```php
$publish_date = "2000-10-02";
ereg("(....)(..)-(.*)", $publish_date, $date_array);
```

`$date_array` 将包含以下内容：

```
[0] => 2000-10-02
[1] => 2000
[2] => 10
[3] => 02
[4] =>
[5] =>
[6] =>
[7] =>
[8] =>
[9] =>
```

请注意 `ereg()` 执行的是大小敏感匹配。

## 第 6 章：PHP 内置函数

### EREGI()
此函数是 `ereg()` 的不区分大小版本。

```php
int eregi(string pattern, string string [, array regs])
```

### EREG_REPLACE()
你可以使用此函数根据复杂模式进行字符串替换。

```php
string ere_replace(string pattern, string replacement, string string)
```

如果你想删除 URL 中的查询字符串（querystring），可以使用这个：

```php
$url = "http://www.phpmysqlbook.com/index.php?var=hello";
$parsed_url = ere_replace("\?.*$", "\1", $url);
echo $parsed_url;
```

这将将打印 http://www.phpmysqlbook.com/index.php。这个正则表达式匹配问号以及从它开始到行尾的所有字符。问号必须用反斜杠转义，因为它在正则表达式中具有特定含义。问号后面匹配任意数量的字符，直到美元符号（行尾字符）。它需要用反斜杠转义，如果没有反斜杠，PHP 将认为该字符代表一个变量。

但你通常需要比这更多的功能。如果你想在替换字符串中保留你正在搜索的字符串？或者如果你的搜索包含不同的偏移括号集？这里有一个简单的示例。我们想通过在字符串中现有的两个 name=value 对之间添加一个额外的 name=value 对来替换当前的查询字符串。也就是说，我们想在 "var=hello" 和 "var2=yup" 之后放入 "newvar-here"。

```php
$url = "http://www.phpmysqlbook.com/index.php?var=hellovar2=yup";
$parsed_url = ere_replace("(..?.*$", "\1newvar-here&", $url);
echo $parsed_url;
```

这将创建如下内容：

http://www.phpmysqlbook.com/index.php?var=hellonewvar-here&var2=yup

在这里，单组括号表示 1。然后，通过使用符号 `\1`，我们可以将该部分包含在新创建的字符串中。如果额外的括号指示了多个部分，你可以通过匹配需要的部分将其回结果中。

```php
$url = "this is a test ";
$parsed_url = ere_replace("(this.a).*(test)", "\1 regular expression", $url);
echo $parsed_url;
```

这些命令的结果是："this is a regular expression test"
正则表达式匹配 "this" 和 "test" 之间的所有内容。我们使用括号指示一个以 "this" 开头并到字母 "a" 的子字符串。接下来的 \ 部分匹配任意数量的字符。最后，“test" 是另一个子字符串。这些子字符串在第二个参数中输出，`\1` 输出第一个子字符串，`\2` 输出第二个子字符串。
正则表达式匹配是大小敏感的。

### EREGI_REPLACE()
这与 `preg_replace()` 相同，区别是匹配是不区分大小写的。

# 本书未使用的正则表达式函数

以下正则表达式函数虽然没有在书示例中使用，但了解它们仍然很有用。

### SQL_REGCASE()
这个小函数将修改字符串，以便你可以在不区分大小写的正则表达式中使用它们。

```php
string sql_regcase(string string)
```

这可能用于修改字符串，以便你可以在不区分大小写的正则表达式中使用它们。
