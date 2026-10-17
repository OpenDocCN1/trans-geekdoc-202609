
similar_text 函数比较两个字符串并返回它们共有的字符数量。如果存在，`percentage` 参数将接收相似率。将此函数与 `metaphone` 和 `soundex` 进行比较。`similar_text` 使用的算法来自 Ian Oliver 的著作《Programming Classics: Implementing the World's Best Algorithms》。该书由 Prentice Hall 出版，你可以在 Prentice Hall Ptr 网站 `http://www.phptr.com/ptrbooks/ptr_0131004131.html` 了解。

图 9-6. `similar_text`

![](img/58e6a0f5d6a8a41d4645d8c07b3bf1e3_247_0.png)

```php
<?php
//创建两个字符串
$left = "Leon Atkinson";
$right = "Vicky Atkinson";
```

```php
<?php
//测试它们有多相似
$i = similar_text($left, $right, $pers);
?>
```

```php
<?php
//打印结果
print($i . " shared characters<BR>\n");
print($percent . %similar<BR>\n");
?>
```

# string soundex(string text)

`soundex` 函数根据单词的读音返回一个标识符。发音相似的单词具有相似或相同的 soundex 码。`soundex` 是四个字符并以字母开头。将此函数与 `similar_text` 和 `metaphone` 函数进行比较。

`soundex` 算法由 Donald Knuth 在《The Art of Computer Programming》第 3 中描述。

```php
<?php
print(soundex("lion"));
print("<BR>");
print(soundex("lying"));
?>
```

# 字符串 (Strings)

# PHP 核心编程

大部分情况下，字符串函数从其他字符串创建字符串或报告字符串的属性。例外是 `eval` 函数，它像执行 PHP 脚本中的代码行一样执行字符串。

## array count_chars(string data, integer mode)

`count_chars` 函数通过存在的字符对字符串进行分析。`mode` 参数控制返回值。模式 0、1 和 2 返回数组。模式 3 和 4 返回字符串。如果省略 `mode`，则使用模式 0。

如果 `mode` 为 0，数组按 ASCII 代码 0–255 索引。每个元素设为每个字符的计数。如果 `mode` 为 1，只返回计数大于零的元素。如果 `mode` 为 2，只返回计数等于零的元素。模式 3 返回一个包含输入字符串中每个字符的字符串。模式 4 包含一个未出现在输入字符串中的所有字符的字符串。

```php
<?php
//打印发现字符的计数
foreach(count_chars("Core PHP", 1) as $key=>$value)
{
    print("$key:
    $value<BR\n");
}

//打印发现的字符列表
print("Characters: ' . count_chars("PHP", 3) . "<BR\n");
?>
```

## eval(string phpcode)

`eval` 函数尝试执行 `phpcode` 参数，就像它是你的 PHP 脚本中的一行代码一样。对于所有字符串，双引号会导致字符串对嵌入字符串和其他特殊字符求值，因此你可能希望使用单引号或用反斜杠转义美元符号。在某些方面，`eval` 类似于 `include` 或 `require`。除了 `eval` 作用于字符串而非文件这一明显区别外，`eval` 从期望 PHP 代码的模式下开始。如果你需要切换到向浏览器传递纯 HTML 的模式，你需要插入关闭 PHP 标签 (`?>`)。为什么你可能想

# PHP 核心编程

在包含纯 HTML 的字符串上执行 `eval`？这可能是因为代码存储在数据库中。

在对任何包含可能来自表单变量数据的字符串调用 `eval` 时，请务必极其小心。这包括最初通过表单设置的数据库字段。可能的情况下，请使用 `$`运算符代替 `eval`。

```php
<?php
// 构造的示例
//eval() 行可以替换为
$$varName = 1;

$varName = "$varValue";
eval("\\$$varName = 1;");
print($varValue . "<BR>\n");

// 对使用 eval 的更真实的模拟
// 使用来自数据库的数据
$code_from_database = "B<?\nprint(date(\"Y-m-d\")); ?></B>";
eval("?>" . $code_from_database);
```

## sprintf(string format, ...)

`sprintf` 函数的操作与 `printf` 函数相同，不同在于它不是将组合后的字符串发送到浏览器，而是返回字符串。详细讨论请参见 `printf` 的描述。此函数提供了一种控制数字表示的简单方法。通常情况下，PHP 可能会打印没有小数部分的双精度数

```php
<?php
$x = 3.00;

// 按 PHP 默认方式打印 $x
print($x . "<BR>\n");

// 格式化 $x 的值，使其
// 显示小数点后两位小数
$s = sprintf("%.2f", $x);
print($s . "<BR>\n");
?>
```

IT-SC 书籍 249

## string str_repeat(string text, integer count)

`str_repeat` 函数返回一个由 `text` 参数重复 `count` 参数指定的次数组成的字符串。

```php
<?php
print(str_repeat("PHP!<BR>\n", 10));
?>
```

## integer strcasecmp(string first, string second)

`strcasecmp` 函数的操作与 `strcmp` 相同，区别在于大写字母和小写字母被视为相同。查看 `soundex`、`metaphone` 和 `similar_text` 获取比较字符串的替代方法。

```php
<?php
$first = "abc";
$second = "Abc";
if (strcasecmp($first, $second) == 0) {
    print("strings are equal");
} else {
    print("strings are not equal");
}
?>
```

## strchr

此函数是 `strstr` 的别名。

## integer strcmp(string first, string second)

`strcmp` 比较第一个字符串和第二个字符串。如果第一个字符串小于第二个字符串，则返回小于零的。如果它们相等，则返回零。如果第一个字符串大于第二个字符串，则返回大于零的。比较通过 ASCII 值进行。此函数用于比较二进制数据是安全的。

# PHP 核心编程

查看 `soundex`、`metaphone` 和 `similar_text` 获取比较字符串的替代方法。

```php
<?php
$first = "abc";
$second = "xyz";
if (strcmp($first, $second) == 0) {
    print("strings are equal");
} else {
    print("strings are not equal");
}
?>
```

## integer strcspn(string text, string set)

`strcspn` 函数返回 `text` 参数中第一个属于 `set` 参数字符集的字符的位置。将此函数与 `strcspn` 进行比较。

```php
<?php
$text = "red cabbage";
$set = "abc";
$position = strcspn($text, $set);

// 打印 'red '
print(substr($text, 0, $position));
?>
```

## string strstr(string text, string substring)

`strstr` 函数是下面 `strstr` 的不区分大小写版本。返回 `text` 参数中从 `substring` 参数第一次出现处到末尾的部分文本。

```php
<?php
$text = "Although he had help, Leon is the author";
?>
```

PHP 核心编程

```php
<?php
print("Full text: $text <BR>\n");
print("Looking for 'leon':" . strrpos($text,"leon"));
```

## integer strlen(string)

使用 `strlen` 函数获取字符串的长度。

## integer strpos(string data, string substring, integer offset)

`strpos` 函数返回 `substring` 参数在 `data` 参数中的位置。如果 `substring` 参数不是字符串，它将被视为 ASCII 码。如果 `substring` 出现多次，则返回第一次出现的位置。如果 `substring` 完全不存在，则返回 FALSE。`offset` 参数指示 PHP 从指定位置之后开始搜索。位置从零开始计数。

当你正在搜索简单字符串时，此函数是 `ereg` 的良好替代方案。它不包含任何解析正则表达式的开销。它用于二进制字符串是安全的。

```php
<?php
$text = "Hello, World!";
// 检查是否存在空格
if(strpos($text, 32)) {
    print("There is a space in '$text<BR>\n");
}

// 找到 World 出现在字符串中的位置
```

```php
<?php
print("World is at position " . 
strpos($text, "World") . "<BR>\n");
?>
```

## strchr

这是 `strrpos` 的别名。

## integer strrpos(string text, string character)

`strrpos` 函数的操作与 `strpos` 类似。它返回第二个参数在第一个参数中最后一次出现。然而，只使用了第二个参数的第一个字符。此函数提供了一种非常简洁的方法来去掉路径的最后部分，如下例所示。

```php
<?php
// 设置测试字符串
$path = "/usr/local/apache";

// 找到最后一个斜杠
$pos = strrpos($path, "/");

// 打印最后一个斜杠之后的所有内容
print(substr($path, $pos+1));
?>
```

## integer strspn(string text, string set)

`strspn` 函数返回 `text` 参数中第一个不属于 `set` 参数字符集的位置。将此函数与 `strcspn` 进行比较。

```php
<?php
$text = "cabbage";
$set = "abc";
$position = strspn($text, $set);

// 打印 'cabba'
print(substr($text, 0, $position));
?>
```

## string substr(string text, string substring)

`substr` 函数返回 `text` 参数中从 `substring` 参数第一次出现处到末尾的部分。如果 `substring` 参数不是字符串，它将被视为 ASCII 码。如果 `substring` 出现多次，则返回第一次出现的位置。`offset` 参数指示 PHP 从指定位置之后开始。位置从零开始计数。如果 `start` 为负数，计数将从 `text` 参数的最后一个字符开始向回。

返回的字符数由 `length` 参数或字符串末尾决定。如果 `length` 为负数，返回的字符串将包含末尾的许多字符。在任何情况下，如果 `start` 和 `length` 的组合导致负长度，则返回单个字符。此函数用于二进制字符串是安全的。

```php
<?php
$text = "My dog's name is Angus."
// 替换为 Gus
print(substr_replace($text, "Gus", 17, 5));
```

# 编码与解码

本节函数将数据从一种形式转换为另一种。这包括删除某些字符、替换某些字符以及将数据翻译为编码形式。

## string addslashes(string text, string characters)

`addslashes` 函数返回按照 C 语言风格转义字符后的文本。简单来说，这意味着特殊字符被替换为代码，例如 `\n` 替换换行符，其他 ASCII 32-126 字符被替换为反斜八进制码。

可选的 `characters` 参数可以包含要转义的字符列表，这将覆盖转义所有特殊字符的默认设置。字符使用八进制表示法。你可以使用两个点来指定范围，如下例所示。

```php
<?php
$s = addslashes($s, "0..\37");
```

## string addslashes(string text)

`addslashes` 函数返回文本参数，并在数据库查询中具有特殊含义的字符前加上反斜杠。这些字符包括单引号 (`''`)、双引号 (`"`) 以及反斜杠本身 (`\`)。

```php
php // add slashes to text
$phrase = addslashes("I don't know");

// build query
$Query = "SELECT *";
$Query .= "FROM comment ";
$Query .= "WHERE text like '%$phrase'";

print($Query);
```

## string base64_decode(string data)

`base64_decode` 函数将数据从 MIME base64 编码翻译为 8 位数据。base64 编码用于跨协议传输数据（例如电子邮件），否则原始二进制数据将会被损坏。

```php
$data = "VGhpcyBppcyBhlAptdWx0aS1aSW51IG1lc3NhZ2UK";
print(base64_decode($data));
```

## string base64_encode(string text)

`base64_encode` 函数将文本（例如电子邮件）转换为可以无损通过 7 位系统传输的形式。

```php
$text = "This is a \nmulti-line message\n";
print(base64_encode($text));
```

# Core PHP Programming

?>

## string basename(string path)

`basename` 函数只返回路径的文件部分。目录被理解为由斜杠字符 (`/`) 分隔的数字和字母字符串。在 Windows 上运行时，也会使用反斜杠 (`\`)。该函数的反面函数是 `dirname`，它返回目录。

```php
<?
$path="/usr/local/bin/ls";
print(basename($path));
?>
```

## string bin2hex(string data)

`bin2hex` 函数返回数据参数，并将每个字节替换为其十六进制表示。数字以小端格式返回。也就是说，第一个数字是最高有效位。

```php
<?
//print book title in hex
//436f7265205048502050726f677216dd696e6
$s = "Core PHP Programming";
$s = bin2hex($s);
print($s);
?>
```

## string chop(string text)

`chop` 函数返回删除了末尾空格的文本参数。如果您想同时删除末尾和开头空格，请使用 `trim` 函数。如果您想删除开头空格，请使用 `ltrim`。空格包括空格、制表和其他非打印字符，包括空字符 (ASCII 0)。

```php
<?
print("\" " . chop("This has whitespace ") . "\"
?>
```

## string chr(integer ascii_code)

使用 `chr` 获取 ASCII 码对应的字符。此函数对于您需要使用没有反斜杠代码或反斜杠代码具有歧义非打印字符的情况很有帮助。想象一个向格式化文本文件写入内容的脚本。通常您会使用 `\n` 作为行结束标记。当您的脚本从 Windows 移动到 Linux 时，行为可能会有所不同，因为 Windows 使用回车符而不是换行符。如果您希望确保每行都以换行符结束，可以在下面的示例中使用 `chr(10)`。

当然，您也可以使用反斜杠代码来指定 ASCII 码，如附录 A 所示和第 2 章讨论的那样。`chr` 的另一个替代方案是 `sprintf`。`%c` 代码代表单个字符，您可以指定字符的 ASCII 值。此外，某些函数（如 `ereg_replace`）接受解释为 ASCII 码的整数。

如果您需要字符的 ASCII 码，请使用 `ord`。附录 B 列出了 ASCII 码。
