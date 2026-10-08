

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

# sprintf(string format, ...)

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

# string str_repeat(string text, integer count)

`str_repeat` 函数返回一个由 `text` 参数重复 `count` 参数指定的次数组成的字符串。

```php
<?php
print(str_repeat("PHP!<BR>\n", 10));
?>
```

# integer strcasecmp(string first, string second)

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

# strchr

此函数是 `strstr` 的别名。

# integer strcmp(string first, string second)

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

# **integer strcspn(string text, string set)**

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

# **string strstr(string text, string substring)**

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

# integer strlen(string)

使用 `strlen` 函数获取字符串的长度。

# integer strpos(string data, string substring, integer offset)

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

# strchr

这是 `strrpos` 的别名。

# integer strrpos(string text, string character)

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

# integer strspn(string text, string set)

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

# string substr(string text, string substring)

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

# string addslashes(string text, string characters)

`addslashes` 函数返回按照 C 语言风格转义字符后的文本。简单来说，这意味着特殊字符被替换为代码，例如 \n 替换换行符，其他 ASCII 32-126 字符被替换为反斜八进制码。

可选的 `characters` 参数可以包含要转义的字符列表，这将覆盖转义所有特殊字符的默认设置。字符使用八进制表示法。你可以使用两个点来指定范围，如下例所示。

```php
<?php
$s = addslashes($s, "0..\37");
```

