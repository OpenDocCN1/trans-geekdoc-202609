
# 转义字符

`\` 字符可用于为紧随其后的字符赋予特殊含义。在用 `echo()` 函数写入文本字符串时，在字符串内部包含引号非常为有用。由于字符串本身被引号包围，PHP 解析器会被额外的引号所困惑并返回错误信息。通过在额外的引号前加上一个反斜线字符进行转义，可以避免这个问题。

此外，换行语法 `"\n"` 可在文本区域中移动到新行，`"\t"` 可用于跨越文本区域。

以下示例创建了一个包含转义引号的 HTML 文本区域内容，并演示了换行和制表符功能。包含 `rows` 和 `cols` (列) HTML 属性值的引号也经过了转义。

![](img/7faa63a7fa0add8f53300594ebae949f_23_0.png)

```html
<?php
echo("<textarea rows=\"5\" cols=\"48\">");
echo("Utinam populus Romanus unam cervicem habet\\");
echo("\n\n\t\t Caligula A.D. 12-41");
echo("</textarea>");
?>
```

![](img/7faa63a7fa0add8f53300594ebae949f_23_1.png)

# 保留字

本页表格包含了 PHP 语言本身的单词。在为变量、函数或标签选择标识符名称时，不能使用这些词。

![](img/7faa63a7fa0add8f53300594ebae949f_24_0.png)

| 关键字 | eval() | switch |
|---|---|---|
| and | exception | TRUE |
| array() | exit() | unset() |
| as | extends | use |
| break | FALSE | var |
| case | for | xor |
| function | foreach | while |
| class | function | |
| const | global | Constants |
| continue | if | _FILE_ |
| declare | include() | _LINE_ |
| default | include_once() | _FUNCTION_ |
| do | isset() | _CLASS_ |
| die() | list() | _METHOD_ |
| echo() | new | |
| else | NULL | Predefined Variables |
| elseif | old_function | _COOKIE |
| empty() | or | |
| enddeclare | php_user_filter | _ENV |
| endfor | print() | _GET |
| endforeach | require() | _POST |
| endif | require_once() | _REQUEST |
| endswitch | return() | _SERVER |
| endwhile | static | _SESSION |

# 变量

变量是 PHP 脚本中用于存储数据以便操作的地方。所有变量都以 `$` 字符开头，后跟一个你选择的具有意义的名称。在命名变量时，可以使用任何字母、数字和 `_` 下划线字符，但变量名不能以数字开头。以下都是有效的变量名：

```
$abc

$my_first_variable

$var123
```

使用 `=` 运算符将数据分配给变量。赋值语句像所有 PHP 语句一样，应该以分号结束。

下面的示例重现了第 22 页的文本示例。在这种情况下，整个文本内容被赋值给变量 `$str`。这使得脚本更加高效，因为整个文本内容现在只需调用一次 `echo()` 函数即可写入文本区域，而不是像之前调用五次。

![](img/7faa63a7fa0add8f53300594ebae949f_25_0.png)

![](img/7faa63a7fa0add8f53300594ebae949f_25_1.png)

注意，在调用 `echo()` 函数时 `$str` 变量没有被引号包围，它不会被视为字面量。

通过 Apache 在网络浏览器中打开此示例，生成的页面与第 22 页底部显示的之前的示例完全相同。

# 数据类型

PHP 是一种弱类型语言，因此它的变量可以存储不同类型的数据，例如数字、文本字符串或布尔值。这与 C++ 和 Java 等编程语言不同，这些语言必须声明变量为特定的数据类型，然后只能在其存储声明类型的数据。

PHP 变量中可以存储的数据类型包括：

- 字符串 (String) – 在双引号 (`"..."`) 或单引号 (`'...'`) 中指定的空格、文本和数字字符
- 整数 (Integer) – 没有小数部分的数字，例如 1,000
- 浮点数 (Floating-point) – 有小数部分的数字，如 3.142
- 布尔值 (Boolean) – 用不区分大小写的 PHP 关键字 `TRUE` 或 `FALSE` 表示的真值。

在给不应被引号包围的变量分配数值值时，否则它们将被视为字符串值。

![](img/7faa63a7fa0add8f53300594ebae949f_26_0.png)

此外，通过给变量分配不区分大小写的 PHP 关键字 `NULL`，可以设置为没有任何值。

```php
<?php
$str = "Here is a string";
$int = 77; $fl = 3.142; $non = NULL;
echo ("String:$str<br> ");
echo ("Integer:$int<br> ");
echo ("Floating-point:$fl<br> ");
echo ("Null:$non ");
?>
```

![](img/7faa63a7fa0add8f53300594ebae949f_26_1.png)

vartype.php

```
http://localhost/vartype.php
File Edit View Favorites Tools Help
Address http://localhost/vartype.php Go
String:Here is a string
Integer:77
Floating-point:3.142
Null
Done Local intranet
```

# 函数

函数是由 PHP 脚本执行一次或多次的 PHP 代码。函数和变量构成了所有 PHP 脚本的基础。

PHP 有许多内置函数，例如 `echo()`，但你可以使用声明中的 `function` 关键字来创建自己的函数。
