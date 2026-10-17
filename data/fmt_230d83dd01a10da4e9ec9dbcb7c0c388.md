
函数在 `subject` 字符串中搜索匹配 `pattern` 正则表达式的子字符串，并用 `replacement` 参数进行替换。可选的 `limit` 参数如果不设置，则替换所有匹配项。`replacement` 参数可以包含数字类型的引用；该类型的引用将被匹配正则表达式的括号部分替换。`n` 参数可以取 0 到 99 的值；`\0` 对应于整个模式。如果找到了匹配模式的子字符串，函数返回修改后的 `subject`；否则，返回字符串的原始值。`preg_replace()` 函数的前三个参数可以是一维数组。处理带有字符串键的数组时，按照它们在数组中的顺序引用。如果 `replacement` 数组的元素多于 `pattern` 数组，`preg_replace()` 会从两个数组中顺序提取元素并用于搜索和替换。如果 `pattern` 参数是数组而 `replacement` 参数是字符串，则目标字符串与 `pattern` 数组的每个元素进行比较，并将任何匹配项替换为 `replacement` 字符串。也就是说，`pattern` 数组的每个元素被用作模式，替换字符串是固定的。pattern 为字符串且 replacement 为数组的选项没有意义。

兼容 Perl 的正则表达式必须包含在分隔符。在 II.2.1 中，使用单引号作为分隔符。除了字母数字或反斜杠外的任何符号都可以作为分隔符。正则表达式内部使用的分隔符必须由转义字符反斜杠引导。结束分隔符可以是影响整个正则表达式的修饰符。`i` 修饰符指定正则表达式不区分大小写；`s` 修饰符意味着正则表达式跨越多行。

![](img/a893312ec68b8170fe567f785e95c06e_134_0.png)

### II.2.1. 从 HTML 页面删除标签

```php
<?php
// 提取 index.html 文件的内容
$content = file_get_contents("index.html");

// 模式数组
$search = array("<script[^>]*?</script>",
    "<<\/!\*?[^<]*?>",
    "([\r\n\s]+",
    "quot|#34;", "i",
    "amp|#38;", "i",
    "lt|#60;", "i",
    "gt|#62;", "i",
    "nbsp|#160;", "i",
    "iexcl|#161;", "i",
    "cent|#162;", "i",
    "pound|#163;", "i",
    "copy|#169;", "i",
    "&#\(d+);", "e");

// 替换数组
$replace = array(
    "",
    "\\",
    "",
    "&",
    "<",
    ">",
    "",
    chr(161),
    chr(162),
    chr(163),
    chr(169),
    "chr(\\1)");

// 删除标签并在浏览器窗口中显示
echo preg_replace($search, $replace, $content);
?>
```

如果必须删除所有 HTML 标签，通常使用 `strip_tags()` 函数是最方便的（列表 II.2.2）。

> 注意 `strip_tags()` 函数不应删除的标签可以在可选的第二个参数中指定。

### 列表 II.2.2. 使用 strip_tags() 函数

```php
<?php
// 提取 index.htm 文件的内容
$content = file_get_contents("index.htm");

// 删除标签并在浏览器窗口中显示
echo strip_tags($content);
?>
```

136 第 II.2 章：正则表达式

然而，`strip_tags()` 函数并不总是方便使用，因为它会将删除的标签替换为空格；此外，常见的 HTML 实体编码（如 `&nbsp;`）保持不变。

## II.2.3. 提取 HTML 页面标题

可以使用 `preg_match()` 正则表达式函数提取 HTML 页面的标题，该函数的语法如下：

```
int preg_match(string pattern, array matches [, int flags, , int offset))
```

函数在 `subject` 字符串中搜索匹配 `pattern` 正则表达式。如果指定了可选的 `matches` 数组，则搜索结果将保存在其中。数组的 `$matches[0]` 元素将保存匹配的字符串

根据整个模式，$matches[1] 元素将包含匹配第一组括号内子模式的字符串，$matches[2] 元素将包含匹配第二组括号内子模式的字符串，依此类推。返回的 $matches 数组的格式由可选的标志参数控制。当此参数设置为 PREG_OFFSET_CAPTURE 时，对于每个找到的匹配项，函数返回一个数组，其中第 0 个元素是匹配的字符串，第 1 个元素是其在字符串中的偏移量。搜索从字符串开始从左到右。可以使用可选的 offset 参数指定备起始位置。preg_match() 函数在未找到匹配项时返回 0，在找到匹配项时返回 1。

上一节使用的技术无法提取页面标题，因为它可能包含角括号。因此，必须使用 `<title>` 和 `</title>` 标签，并用 U 修饰符控制“贪婪性”。默认情况下，正则表达式是“贪婪的”；也就是说，它们从所有找到的匹配中返回最长匹配。U 修饰符反转这种“贪婪性”，返回所有选择中最短的匹配。

## 列表 II.2.4. 提取 HTML 页面标题

```php
<?php
// 提取 index.html文件的内容
$content = file_get_contents("index.html");

// 正则表达式
$pattern = "<title>(.*)</title>|si";

// 提取 HTML 页面的标题
if (preg_match($pattern, $content, $out)) {
    echo $out[1];
}
?>
```

正则表达式的贪婪性也可以通过 `*` 序列使用；也就是说，列表 II.2.4 中的正则表达式可以重写为 `<title>(.*?)</title>|si`。`*` 序列允许局部控制贪婪性，例如当整个正则表达式需要是贪婪的但其某部分不是贪婪的时。

## 第 II.2 章：正则表达式 125 页

## II.2.4. 将 MySQL 日期格式转换为日历格式

可以使用列表 II.2.5 所示的脚本将日期格式转换为日历格式。

列表 II.2.5. 从 YYYY-MM-DD 格式转换为 DD.MM.YYYY 格式

`preg_match()` 函数产生的搜索结果可以保存在可选第三参数指定的数组中。第 0 个数组元素将包含对整个正则表达式的匹配；第一个数组元素将包含对第一组括号内正则表达式的匹配（年份）；第二个数组元素将包含对第二组括号内正则表达式的匹配（月份）；第三个数组元素将包含对第三组括号内正则表达式的匹配（日期）。

## II.2.5. 验证电子邮件地址格式

假设地址格式应为 `something@server.com`。此外，地址由 `@` 字符分隔成两个部分；这些是用户名和域名。用户名可以包含大写和小写字母、数字、下划线、点和连字符。为了检查用户名和域名之间的分隔符，必须在正则表达式中添加 `@` 字符。用户名一样，域名可以使用大写和小写字母、数字、下划线、点和连字符。因此，可以构造以下用于验证电子邮件地址用户名和域名格式是否适当的正则表达式：

```
[0-9a-z_]+@[0-9a-z_^\.]+
```

## 第二部分：解决方案

为了检查一级域名（例如 .com、.ed 或 .gov），必须添加以下正则表达式：

\.[a-z]{2,6}

你应该意识到最近创建了几个一级域名，如 .info 和 .travel。三字母的正则表达式无法适用于这些新的一级域名；必须使用二到六个字母组成的正则表达式来检查一级域名。

点号 `.` 在正则表达式中表示任何字符；因此，正则表达式中表示匹配目标字符串中点的点号，必须用反斜杠进行转义。

用于确认电子邮件地址格式规则的组合正则表达式如下：

```
|[0-9a-z_]+\@[0-9a-z_]+\.[a-z]{2,6}|
```

`i` 修饰符告诉解释器在搜索目标字符串时忽略大小写。

如果目标字符串包含的唯一信息是电子邮件地址，则必须使用 `^` 和 `$` 字符将正则表达式锚定在字符串的开头和结尾。生成的表达式如下：

```
^[0-9a-z_]+\@[0-9a-z_]+\.[a-z]{2,6}$
```

验证电子邮件格式的完整代码可能所示列表 II.2.6。

## II.2.6. 检查电子邮件格式

```php
<form method=post>
<input size=60 type=text name=value=<?php $_POST['name']; ?>>
<input type=submit value='Check'>
</form><br>
<?php
// HTML 表单处理程序
if(isset($_POST['name']))
{
if(preg_match("^[0-9a-z_]+\@[0-9a-z_]+\.[a-z]{2,6}$",
$_POST['name']))
{
  echo "The email address format is correct.";
} else {
  echo "The email address format is wrong.";
}
?>
```

## 第 II.2 章：正则表达式 127 页

## II.2.6. 验证 URL

构造一个对应所有可能 URL 的正则表达式并不容易。通常会在正则表达式的复杂性与其表示 URL 格式的准确性之间寻求折中方案。

在构造所需的正则表达式时，假设 URL 格式如下：

```
http://host/path/
```

带有不同扩展名（例如 .html,.php,.pl 或 .cgi）的名称是 URL 的可选部分。文件名后面可能跟着可选参数。

满足这些 URL 格式条件的正则表达式可能是：

```
#^((http://)?[-a-zZ-9_\.]+)|([-a-zZ-9_]+))+\.(html|php|pl|cgi))?\n([-a-zZ-9_:&&?+=!/\-\*%$]+)+\#i
```

使用该正则表达式的脚本所示列表 II.2.7。

## 列表 II.2.7. 检查 URL 格式

```php
<form method=post>
<input size=60 type=text name=name value=<?php $_POST['name']; ?>>
<input type=submit value='Check'>
</form><br>
<?php
// HTML 表单处理程序
if(isset($_POST['name'])) {"
```

## 128 页 第二部分：解决方案

```php
$Pattern = "^##(http://)?[-a-z0-9_\.]+\(([-a-z0-9_]+\]+\.(html|php|pl|cgi))?\([-a-z0-9_@&\;=\=\-!/\*\$]+)?$#i";
if (preg_match($Pattern, $_POST['name']))
{
    echo "The URL format is correct.";
}
else
{
    echo "The URL format is incorrect.";
}
?>
```

## 11.2.7. 将文本 URL 转换为链接

可以使用 II.2.6 节中考虑的表达式将文本 URL 转换为超链接。完整代码所示列表 II.2.8。

## 11.2.8. 将文本 URL 转换为链接

```php
<?php
// 提取 index.html文件的内容
$content = file_get_contents("index.html");

// 正则表达式
$pattern = "<title>(.*)</title>|si";

// 提取 HTML 页面的标题
if (preg_match($pattern, $content, $out)) {
    echo $out[1];
}
?>
```

## 第 II.2 章：正则表达式 129 页

## II.2.8. 验证输入

验证输入符合某些要求是一项重要任务。Web 开发者通常认为向字段中输入的将是数字。然而，此类字段也可以输入文本。这可能在最好的情况下执行失败，在最坏的情况下导致破坏（见第 I.5 和 II.5 节）。

整数可以很容易检查：为此目的有一个特殊类 `\d`。此外，正则表达式必须用 `^` 和 `$` 字符锚定在目标字符串的开头和结尾。这样做会导致输入一个数字后可以输入任何内容：正则表达式将找到该数字并忽略其他内容。检查字符串为整数的正则表达式如下：

```
^\d]*$
```

检查浮点的正则表达式有三部分。检查整数部分与检查整数的表达式相同：`[\d]*`。点由点字符表示，必须用反斜杠进行转义。检查小数部分可以用 `\.\d]*` 描述。将这些片段组合产生检查浮点数的正则表达式：`^[\d]*\.\d]*$`。最后的处理考虑了整数和小数之间分隔符的不同格式，这两者可以使用点（例如 23.56）和逗号（例如 23,56）。对应的正则表达式是：`^[\d]*[.,][d]*$`。然而，此表达式将无法匹配整数。为了这个问题，必须在 `[.,]` 类之后插入标记字符。最终表达式如下：

```
^[\d]*[.,][]?\d]*$
```

因此，解决方案所示列表 II.2.9。

## 列表 II.2.9. 验证数字输入

```php
<form method = post>
Quantity <input size=60 type=text-number
value<=?= $_POST['number']; ?> ?><br>
Price <input size=60 type=text-price
value<=?= $_POST['price']; ?> ?><br>
<input type = submit value = 'Verify'>
```

```php
</form><br>
<?php
// HTML 表单处理器
if (isset($_POST['number']) && isset($_POST['price'])) {
    if (!preg_match("/^\d+$/", $_POST['number'])) {
        exit("物品数量格式错误。");
    }
    if (!preg_match("/^\d+([.,.])?(\d+)?/", $_POST['price'])) {
        exit("价格格式错误。");
    }
    echo number_format($_POST['number']*$_POST['price'], 2, '.', '');
}
?>
```

## II.2.9. 转换大小写

必须更改字母大小写的问题是应用 `preg_replace_callback()` 函数的理想候选对象。该函数与 `preg_replace()` 函数相似，不同在于实际的替换是由回调函数执行的。该函数的语法如下：

```
mixed preg_replace_callback(mixed pattern, callback,
mixed subject [, int limit])
```

该函数没有使用 `preg_replace()` 函数中的替换参数，而是指定了一个回调函数。该函数接收找到的匹配项数组，并返回替换字符串。

## II.2.10. 转换文本大小写

```php
<?php
$text = "PROGRAMMING is an ART worth devoting your entire LIFE to.";
$text = preg_replace_callback(
    "/[A-Z]{2,}/",
    "replace_text",
    $text
);
```

```php
echo $text;
function replace_text($matches)
{
  return substr($matches[0], 1).strtolower(substr($matches[0], 1));
}
```

正则表达式 `[A-Z]{2,}` 搜索所有连续两个或多个大写字母的单词。这些单词将被 `replace_text()` 回调函数返回的结果所替换。该函数的参数是一个匹配字符串的数组，数组中的第一个元素包含正则表达式中连续括号括号的匹配项。该函数保持每个匹配字符串的第一个字母不变，并借助 `strtolower()` 函数将其余字母转换为小写。

PHP 有一个特殊的函数可以将单词的第一个字母转换为大写，并将其其余部分转换为小写：`ucfirst()`。然而，在大多数情况下，它无法正常地处理国家语言字符；因此，为了在所有服务器上进行无故障操作，列表 II.2.10 中提供的解决方案更为佳。

![](img/a893312ec68b8170fe567f785e95c06e_144_0.png)

## II.2.10. 拆分长字符串

长字符串（如 II.2.8 节中的问题）可以使用使用自定义回调函数的 `preg_replace_callback()` 函数处理（列表 II.2.11）。

## II.2.11. 拆分长字符串
