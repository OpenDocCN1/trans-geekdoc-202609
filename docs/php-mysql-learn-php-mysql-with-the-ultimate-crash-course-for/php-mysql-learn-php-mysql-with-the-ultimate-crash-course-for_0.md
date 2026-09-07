# PHP & MySQL：初学者终极速成指南






## 引言
感谢你的下载，并祝贺你下载了`PHP: Learn PHP and MySQL with the Ultimate Beginners Crash Course In No Time!`。这本书包含了关于如何使用正确的语法和关键词创建代码的经过证明步骤和策略。它还提供了如何正确使用数组和条件语句的提示。为了充分利用其应用作用，你还将学习如何执行数学运算。你也将学习如何打开、读取、写入和关闭文件。书中包含示例程序，可以作为你编写代码时的指南。本书还包含了关于 `MySQL` 和 `PHP` 的有用信息，包括它们的特性，甚至讨论了 `MySQL` 和 `PostgreSQL` 之间的差异。再次感谢下载！本文旨在就涵盖的主题提供准确且可靠的信息。本书的销售基于以下理念：出版者不承担渲染、官方许可或其他形式的责任。

## 第 1 章：PHP 简介
PHP 代表 `PHP: Hypertext Preprocessor`（超文本预处理器），是一种开源脚本语言，其脚本在服务器上执行。它可以免费下载并使用。它是 Web 开发的理想选择，推荐初学者学习。它可以嵌入 `HTML` 中。此外，它还可以用于 `WordPress` 和 `Facebook`。

一个 `PHP` 文件可以包含 `HTML`、`JavaScript`、`CSS`、`PHP` 代码和文本。`PHP` 与客户端 `JavaScript` 的区别在于代码是在服务器上执行的生成发送给客户端的 `HTML`。运行脚本后，即使客户端不知道底层代码也能收到结果。可以配置 Web 服务器使用 `PHP` 处理 `HTML` 文件。

PHP 简单到初学者也能理解，但它也为高级程序员提供了许多高级特性。你甚至可以在几小时内开始编写简单的脚本。请注意，尽管它的创建重点是服务器端脚本，但你可以用它做更多事情。

### 为什么你应该学习 PHP
你可能认为，如果你精通使用 `JavaScript`，那么学习 PHP 就不不再了。然而，与 `PHP` 相比，`JavaScript` 实际上限制大得多。`JavaScript` 运行在客户端或浏览器中，这意味着它只知道你浏览器中发生的情况以及你访问的网站。

另一方面，`PHP` 运行在你访问的网站所在的计算机或服务器上。它可以访问该计算机上的每个文件和信息，这使其能够创建发送到浏览器的自定义 `HTML` 页面、运行任务、执行计算并处理该网站的 cookie。

PHP 可以在服务器上打开、创建、写入、读取、关闭和删除文件。它可以生成页面内容、收集表单数据并发送和接收 cookie。它还可以删除、添加和修改数据库中的数据。此外，它可以加密数据以及控制用户访问。

通过 `PHP`，你可以输出 `PDF` 文件、图像和 Flash 电影。你不局限于 `HTML`。你甚至可以输出文本，例如 `XML` 和 `XHTML`。换句话说，`PHP` 实际上可以做任何事情。由于它专注于服务器端脚本，它可以完成任何其他 `CGI` 程序能做的事情以及更多。

`PHP` 脚本主要用于以下领域：

- 服务器端脚本。




即使你没有浏览器或服务器，你仍然可以运行 PHP。你只需要一个 PHP 解析器。对于使用 Windows 任务计划程序或 Linux 的 `cron` 定期执行的脚本，建议使用 PHP。你也可以使用这些脚本进行简单的文本处理。

### 创建桌面应用程序

虽然 PHP 并不是创建带有图形用户界面的桌面应用程序的首选，但如果你想在应用程序中包含高级功能，仍然可以使用它。你可以使用 `PHP-GTK` 来创建此类客户端应用程序。此外，你还可以编写跨平台应用程序。`PHP-GTK` 实际上是一个 PHP 扩展，它在主发行版中并不可用。

你可以在任何主流操作系统上使用 PHP，包括 Unix、Linux、Microsoft Windows、RISC OS 和 Mac OS X。PHP 还支持今天大多数流行的 Web 服务器，如 `Apache` 和 `IIS`。任何可以使用 `FastCGI` PHP 二进制文件的 Web 服务器（如 `nginx` 和 `lighttpd`）也可以使用 PHP。PHP 可以作为 CGI 处理器或模块存在。

你可以自由地选择任何支持 PHP 的 Web 服务器和操作系统。此外，你可以选择面向对象编程、过程化编程或两者的结合。PHP 可以自动生成你的文件并将其保存到文件系统中，而不是将其打印出来。

PHP 的主要优势之一是它支持多种数据库。使用特定的数据库扩展或抽象层（如 `PDO`），可以非常容易地编写启用数据库支持的网页。你还可以通过 `ODBC` 扩展连接到支持开放数据库连接标准的数据库。

此外，PHP 支持通过 `IMAP`、`LDAP`、`SNMP`、`POP3`、`NNTP`、`COM` 和 `HTTP` 等协议与其他服务进行通信。你甚至可以使用你选择的协议进行交互并打开原始网络套接字。PHP 还支持 Java 安装以及在所有编程语言之间的 `WDDX` 数据交换。

PHP 还具有文本处理功能，包括 Perl 兼容正则表达式以及用于解析和访问 XML 文件的其他工具。PHP 标准化了 XML 扩展，并增加了 `XML Reader`、`XML Writer` 和 `Simple XML` 支持。PHP 还有增加了 `PECL` 扩展，例如 `XDebug`。

## 在你的电脑上设置 PHP

为了开始使用 PHP，你需要寻找支持 `MySQL` 和 PHP 的 Web 托管。你也可以先安装 Web 服务器，然后安装 `MySQL` 和 PHP。然而，如果你的服务器已经支持 PHP，那么你就不再需要执行上述指令。你只需要创建 `.php` 文件并将它们放在你的目录中。服务器将自动解析它们。你不再需要编译或安装任何东西。今天大多数 Web 托管实际上都支持 PHP，因为它是免费的。

## 第 2 章：MySQL

`MySQL` 是一个免费提供的开源关系型数据库管理系统 (RDBMS)。它利用结构化查询语言 (`SQL`)，这是访问、管理和添加数据库内容最常用的语言。它还以经过证明的可靠性、快速处理、灵活性易用性而闻名。`MySQL` 是几乎每个开源 PHP 应用程序的关键部分。一些最流行的基于 PHP/MySQL 的脚本包括 `Joomla`、`phpBB` 和 `osCommerce`。

### MySQL 到底是什么？

要理解 `MySQL` 是什么，你必须知道什么是计算机数据库。本质上，计算机数据库是数据的集合。`MySQL` 和其他专门的数据库软件只是允许用户访问、管理和添加数据库内容的程序。

`MySQL` 和其他专门的数据库软件只是允许用户访问、管理和添加数据库内容的程序。

`MySQL` 和其他专门的数据库软件只是允许用户访问、管理和添加数据库内容的程序。

用于检索的专门数据库软件。

用于检索的专门数据库软件。

用于检索的专门数据库软件。

用于检索的专门数据库软件。

用于检索的专门数据库软件。

用于检索的专门数据库软件。

`MySQL` 数据库系统。

`MySQL` 数据库管理系统。

`MySQL` 数据库服务器。

` MySQL 与服务器






PostgreSQL 的一些重要特性包括 TOAST 数据压缩、参数化和静态 SQL 执行器、改进的缓存管理、强大的可扩展性、异步提交以及先进的基于成本的优化器。PostgreSQL 能够使用快速的压缩方案对数据进行解压缩和压缩，使其能够存放在特定的磁盘空间中。压缩数据非常好，因为它不仅节省磁盘空间，还能更快地读取数据。

MySQL 的一些核心特性包括广泛的 ANSI SQL 99 子集及扩展、通过 `LIST`、`SET`、`HASH` 和 `RANGE` 进行表分区、网络协议压缩、通过行更改事件或语句的内置复制、触发器、SSL 支持、游标、存储过程、可更新视图以及 Unicode 支持。

如果你是一个不为自己的网站编写程序的站管理员，你可能不会觉得 MySQL 和 PostgreSQL 之间的差异有多大。你关心的可能主要是你的 Web 主机是否拥有你应用程序所需的数据库软件。通常情况下，如果你使用 CMS 或任何其他流行的博客软件，可以预期它使用 MySQL。几乎所有的商业 Web 主机都将 MySQL 作为其托管包的一部分。

### 你需要学习 MySQL 吗？

普通的站管理员不需要学习 SQL 或 MySQL，因为他们使用的软件极可能完成了数据的存储和检索。他们只需要学习如何使用他们的软件。将 MySQL 和类似的数据库想象成汽车引擎。为了能够开车，你真的不需要学习如何设计汽车引擎。同样，为了能够使用博客软件，你不需要学习直接读写 MySQL 数据库。

另一方面，如果你是一个程序员，你需要学习 SQL，以便编写访问 MySQL 和其他 SQL 数据库的计算机程序。当然，你还需要学习一种合适的编程语言。如果你想是否必须成为程序员才能成为站管理员，答案是否定的。你可以在不知道编程的情况下成为站管理员。你可以通过手动编写 HTML 代码来创建一个网站。

## 第 3 章：语法、注释、大小写敏感、换行和表单

### 语法

你可以将 PHP 脚本放在文档的任何地方。它们通常以 `<?php` 开始，以 `?>` 结束。它们的文件扩展名为 `.php`，通常包含 PHP 脚本代码和 HTML 标签。不要忘记使用分号（`;`）结束 PHP 语句。

考虑以下 PHP 代码示例：

```php
<?php
echo “Testing code”;
?>
```

如果你运行这段代码，你将得到输出：
Testing code

### 注释

注释是不执行或不作为程序一部分读取的代码。它们的唯一目的是供可能需要额外信息的用户阅读。如果你想让其他人更好地理解你的程序，或者你想提醒自己曾经做过什么，你可以在程序中包含注释。如果你决定在几年后回来看你的程序，你的注释将非常有帮助。它们可以提醒你自己在创建代码时的想法。

考虑以下示例：

```php
<?php
### 这是一个单行注释
// 这是一个单行注释
/* 
这是一个 
多行
注释
*/
// 这是一个省略了代码行部分内容的注释
$w = 2 /* + 10 */ + 3;
echo $w;
?>
```

如果你运行这段代码，你将得到输出：
5

### 大小写敏感

PHP 中的函数、关键字和类是不区分大小写的。

  考虑这个示例：

```php
<?php
echo “Testing code ”;
ECHO “Testing code ”;
EcHo “Testing code ”;
?>
```

如果你运行这段代码，你将得到输出：
Testing code Testing code Testing code

然而，PHP 中的变量名是区分大小写的。

看这个示例：

```php
<?php
$color = “blue”;
echo “The sky is ” . $color . "\n“;
echo “The sky is “ . $coLOR . "\n“;
echo “The sky is “ . $COLOR . "\n“;
?>
```

如果你运行这段代码，你将得到输出：
The sky is blue 
The sky is 
The sky is

你会发现，第一个语句是唯一显示变量 `$color` 值的。这是因为 `$color`、`$coLOR` 和 `$COLOR` 被视为不同的变量。

### 换行

要创建一个新行，你只需要在语句后放置 `\n`。

考虑以下内容：

```php
<?php
echo “The sky is \n“;
echo “The rose is \n“;
?>
```

如果你运行这段代码，你将得到输出：
The sky is
The rose is

### 处理表单

PHP 的最大优势之一是它可以处理表单。

## 第 4 章：数组

数组是一个可以存储多个值的特殊变量。例如，你可以在数组中存储多个项目。

```php
$name1 = “Wendy”;
$name2 = “Dawn”;
```

### 如何创建数组

使用 `array()` 函数来创建数组。可以传递任意数量的参数。实际上有三种数组：关联数组、索引数组和多维数组。

### 关联数组

关联数组具有命名的键。关联数组的语法为 `array(key => value)`。例如：

```php
<?php
$price = array (“cantaloupes” => “2”, “grapes” => “3”, “strawberries” => “4”);
echo “Cantaloupes cost “ . $price['oranges'] . “dollars each.”;
?>
```

### 索引数组

索引数组具有数字索引。索引数组的语法为 `array(value1, value2)`。编写索引数组有两种：你可以允许索引自动分配，也可以手动分配。

自动分配：
```php
$fruits = array (“apples”, “bananas”, “kiwis”);
```

手动分配：
```php
$fruits[0] = “apples”;
$fruits[1] = “bananas”;
$fruits[2] = “kiwis”;
```

### 多维数组

多维数组包含其他数组。这是一个二维数组的示例：

```php
<?php
$fruits = array (
array (“apples”, 10, 6),
array (“bananas”, 4, 5),
array (“kiwis”, 11, 10)
);
?>
```

在 PHP 5.4 中，`array()` 可以被 `[]` 替换。这被称为短数组语法。例如：

```php
<?php
$name = [
    “Wendy” => “Dawn”,
    “Dawn” => “Wendy”,
];
?>
```

字符串或整数可以是键。值也可以是任何类型。此外，预计会发生以下键转换：

浮点数：它被转换为整数，截断小数部分。例如，键 `9.7` 将存储在 `9` 下。





`String`。包含有效整数的字符串会被转换为整数类型。例如，键 `9` 将被存储在 `9` 下，而键 `09` 不会被转换，因为它不是有效的十进制整数。

`Bool`。它也会转换为整数。例如，键 `false` 将被存储在 `0` 下，而键 `true` 将被存储在 `1` 下。

`Null`。它被转换为空字符串。例如，键 `null` 将被存储在 `" "` 下。

对象和数组永远不能用键。如果你尝试将它们用键，将得到一个非法偏移类型警告。

如果你声明了多个具有相同键的元素，最后一个将使用使用，而其他的将被覆盖。

考虑以下示例：

```php
<?php
$array = array (
    1 => "w",
    "1" => "x",
    1.5 => "y",
    true => "z",
);

var_dump ($array);
?>
```

如果你运行这段代码，你将得到如下输出：

```text
array (1) {
    [1] =>
    string (1) "z"
}
```

这是结果输出，因为所有的键都被转换成了 `1`。对于每一个新元素，值都会被覆盖，这就是为什么留下了值 `"z"`。PHP 数组中可以同时包含字符串键和整数键，因为 PHP 无法区分关联数组和索引数组。

### 方括号语法

数组 `[key]` 语法可以用于访问数组元素。如果你想访问数组元素，大括号和方括号可以交替使用。从 PHP 5.4 开始，你可以直接对方法调用和函数调的结果进行数组引用。在较早的版本中，你只能使用临时变量进行数组引用。从 PHP 5.5 开始，你已经可以对数组字面量进行数组引用。再次注意，你不能访问未定义的键，就像你不能访问任何未定义的变量一样。如果你这样做，将得到一个 `E_NOTICE` 级别的错误消息和 `NULL` 输出。

当使用方括号语法创建或修改数组时，你可以显式地在它们中设置值。你可以通过给数组赋值来实现这一点。键应该在括号中指定，或者省略产生空括号 `[]`。如果你想更改一个值，可以通过其键为元素分配另一个值。如果你想删除一个键值对或键，可以使用 `unset()` 函数。

然而，数组不能重新索引。如果你想删除并移动，可以使用 `array_values()` 函数。

### 一些常用的数组函数

- `asort`：它对数组排序并保持索引。
- `arsort`：它反序对数组排序并保持索引。
- `array`：它创建数组
- `compact`：它创建包含变量的数组
- `current`：它返回数组中的当前元素
- `each`：它从数组返回当前的键和值对，并移动数组。
- `end`：它将内部指针设置为最后一个元素。
- `extract`：它将变量导入到当前的符号表中。
- `in_array`：它验证值是否存在于数组中
- `key_exists`：它是 `array_key_exists` 的另一个名字。
- `ksort`：它按键对数组排序。
- `krsort`：它按键对数组排序，但是反序的。
- `key`：它从数组获取键。
- `list`：它像处理数组一样分配变量。
- `natsort`：它通过自然顺序对数组排序。
- `natcasesort`：它按不区分大小的自然排序算法对数组排序。
- `next`：它移动内部数组指针。
- `prev`：它回溯内部数组指针。
- `pos`：它是 `current` 的另一个术语。
- `range`：它创建包含各种元素的数组。
- `rsort`：它反序对数组排序。
- `reset`：它将内部指针设置为第一个元素。
- `shuffle`：它打乱数组。
- `sort`：它对数组排序。
- `sizeof`：它是 `count` 的另一个术语。
- `uasort`：它使用用户定义的比较函数对数组排序并保持索引。
- `uksort`：它使用用户定义的比较函数按键排序数组。
- `usort`：它使用用户定义的比较函数按值排序数组。
- `array_chunk`：它将数组分割为
- `array_combine`：它将数组合并为
- `array_count_values`：它统计每个
- `array_diff`：它计算差集
- `array_diff_assoc`：它计算差集
- `array_diff_key`：它计算差集
- `array_diff_unique`：它计算差集
- `array_fill`：它用...填充数组
- `array_fill_keys`：它用...填充数组
- `array_filter`：它过滤数组
- `array_group`：它分组数组
- `array_diff`：它计算差集
- `array_diff_assoc`：它计算差集
- `array_diff_key`：它计算差集
- `array_diff_unique`：它计算差集
- `array_keys`：它返回键
- `array_intersect`：它计算交集
- `array_intersect_assoc`：它计算关联交集
- `array_intersect_key`：它计算键交集
- `array_intersect_unique`：它计算唯一交集
- `array_merge`：它合并数组
- `array_merge_recursive`：它递归合并
- `array_multisort`：它对多个数组排序
- `array_pop`：它弹出最后一个元素
- `array_pad`：它用...填充数组
- `array_product`：它计算乘积
- `array_rand`：它随机选择一个
- `array_push`：它推送至少一个
- `array_reduce`：它迭代减少
- `array_replace`：它替换数组
- `array_shift`：它从头部移动元素
- `array_slice`：它截取部分
- `array_splice`：它删除部分
- `array_sum`：它计算和
- `array_unique`：它消除重复值
- `array_values`：它返回值
- `array_unshift`：它在开头前置至少一个一个
- `array_walk`：它将用户提供的函数应用到数组的每个成员

## 第 5 章：条件语句

条件语句用于根据不同的条件执行各种操作。通常，当你编写代码时，目标是针对特定目的执行操作。在 PHP 中，你可以使用这些条件语句：

- `switch`：它让你选择一个要执行的代码块。
- `if`：如果条件为真，它让你执行代码。
- `if...else...else`：如果上一个条件为假，它让你指定一个新的测试条件。
- `if...else`：如果条件为真，它让你执行一段代码，如果为假，则执行另一个。

### if 语句




如上所述，`if` 语句允许您在条件判定为真时执行代码。其语法如下：

```
if (condition)
{
    block of code;
}
```

请看以下示例：

```php
<?php
$time = date (“Hour”);
If ($time < “10”)
{
    echo “Good morning!”;
}
?>
```

如果您运行这段代码，您将得到如下输出：

Good morning!

当且仅当小时或时间小于 10 时。

### If… Else 语句

您可以使用 `if… else` 语句在条件判定为真时执行一段代码，在条件判定为假时执行另一段代码。其语法如下：

```
if (condition)
{
    block of code to execute if the condition is true;
}
else 
{
    block of code to execute if the condition is false;
}
```

请考虑以下示例：

```php
<?php
$time = date (“Hour”);
if ($time < “10”)
{
    echo “Good morning!”;
}
else
{
    echo “Good afternoon!”;
}
?>
```

如果您运行这段代码，您将得到如下输出：

Good morning!

当时间小于 10 时。否则，您将得到如下输出：

Good afternoon!

### If… Else if… Else 语句

该语句用于在第一个条件判定为假时指定新的测试条件。其语法如下：

```
if (condition)
{
    block of code to execute if the condition is true;
}
else if (condition)
{
    block of code to execute if the condition is true;
}
else 
{
    block of code to execute if the condition is false;
}
```

请看以下示例：

```php
<?php
$time = date (“Hour”);
if ($time < “10”)
{
    echo “Good morning!”;
}
else if ($time < “20”)
{
    echo “Good afternoon!”;
}
else
{
    echo “Good night!”;
}
?>
```

如果您运行这段代码，您将得到如下输出：

Good morning!

当时间小于 10 时。您将得到如下输出：

Good afternoon!

当时间小于 20 时。否则，您将得到如下输出：

Good night!

### Switch 语句

它用于根据给定的条件执行操作。在 PHP 中，有许多代码块可以使用 `switch` 来选择您想要执行的特定代码块。其语法如下：

```
switch (name) {
    case label 1:
        block of code if name = label 1;
        break;
    case label 2:
        block of code if name = label 2;
        break;
    …
    default:
        block of code if name is different from all the labels;
}
```

### Break 语句

`Break` 用于防止代码块自动运行到下一个 `case`。如果未找到匹配项，则使用 `Default`。请考虑以下示例：

```php
<?php
$color = “pink”;
switch ($color)
{
    case “pink”:
        echo “The color of the shirt is pink!”;
        break;
    case “yellow”:
        echo “The color of the shirt is yellow!”;
        break;
    case “purple”:
        echo “The color of the shirt is purple!”;
        break;
    default:
        echo “The color of the shirt is neither pink, yellow, nor purple!”;
}
?>
```

如果您运行这段代码，您将得到如下输出：

The color of the shirt is pink!

在编写代码时，在 `switch` 语句中包含一个 `default` 情况始终是一个好主意。请注意，`default` 之前没有 `case` 单词，因为 `default` 是一个特殊的关键字。

### Continue 语句

`Continue` 用于停止循环的当前迭代。它会停止但不终止循环。它也被放在包含循环执行代码的语句块内部，就像 `break` 一样。它的前面是条件测试。在遇到 `continue` 语句的迭代中，将在跳过循环剩余代码的情况下开始下一次迭代。例如：

```php
<?php
$array = array (2, 4, 6, 8, 10);
foreach ($array as $value)
{
    if ($value ==4) continue;
    echo “The value is $value <br/>”;
}
?>
```

如果您运行这段代码，您将得到如下输出：

The value is 2
The value is 4
The value is 6
The value is 10

在上面的示例中，循环显示数组的值。然而，当条件变为真时，它跳过了代码并打印了下一个值。

## 第 6 章：数字与数学运算

数据类型 `integer` 和 `float` 是数字，可以存储在变量中。

例如：

```
$intvar = 5;
$floatvar = 11.4;
```

在 PHP 中，值会自动存储为相应的数据类型。您也可以执行数学运算。您只需要通过使用数学运算符两个数字来指示数学运算即可。

例如，您可以使用加号 (`+`) 运算符：

```
2 + 3
```

您也可以使用变量：

```
$var2 + $var3;
```

如果您想在数学运算中使用数字，但不应将它们包含在引号中。如果您使用了引号，将无法对这些字符串执行数学运算。

请考虑以下示例：

```php
<?php
$var1 = “2”;
$var2 = 4;
$total = $var1 + $var2;
?>
```

由于 `var1` 是字符串，PHP 会将其转换为数字。然而，在到达第三条语句时数字进行了相加。

```php
<?php
$var1 = “y”;
$var2 = 4;
$total = $var1 + $var2;
?>
```

由于 `y` 不是 PHP 可以转换的数字，`total` 的结果变成了 4。通常，这种转换并不是程序员预期的。

### 数学运算符

- `+` 表示加法。用于数字相加。
- `-` 表示减法。用于从第一个数字中减去第二个数字。
- `*` 表示乘法。用于数字相乘。
- `/` 表示除法。用于用第一个数字除以第二个数字。
- `%` 称为模。它在执行除法时识别余数。

### 运算顺序

可以同时执行多个数学运算。请看以下示例：

```
$total = 2 + 3 * 4 + 2;
```

记住，您的数学语句的顺序至关重要。您可能会得到不同的输出。因此，当您在代码中使用数学运算符时必须小心。在 PHP 中，先执行除法和乘法。然后执行减法和加法。此外，在所有其他因素相等的情况下，PHP 可以从左到右开始。

如果您运行上面的代码，您将得到如下输出：

16



你得到 16 是因为 PHP 先执行乘法过程。在 `$total = 2 + 3 * 4 + 2` 中，`3 * 4` 先执行。因此，将 `3` 乘以 `4` 得到 `12`。对于其他的加法运算符，PHP 从左到右读取代码。它将 `2` 加到 `12`（即 `3 * 4` 的结果）上。最后，它执行最后一个加法过程。`2 + 12` 等于 `14`，然后加上 `2`，所以你得到了 `16`。

如果你想改变操作顺序，可以使用括号。当你使用括号时，括号内的任何内容都会首先执行。看下面的示例：

```php
$total = (2 + 3) * 4 + 2;
```

如果你运行这段代码，你将得到输出：

```
22
```

你得到 22 是因为 `2 + 3` 在括号内，所以它们先执行。`2` 和 `3` 相加得到 `5`，然后乘以 `4`。你的代码实际上变成了 `(5) * 4 + 2`。如之前提到的，默认情况下先执行乘法和除法。但由于你使用了一组括号，内部的操作会先执行。由于没有需要执行的除法，因此执行了乘法。你得到 `20 + 2`。最后，你执行最后一个加法过程。`20` 加 `2` 等于 `22`。

在一组括号内嵌套另一组括号也是可能的。如果你想改变该括号内部的操作顺序，可以这样做。理想情况下，如果你的数学表达式有多个答案，你应该在需要的地方使用括号。

### 递增与递减

在 PHP 中，你可以使用快捷方法给变量加 1。考虑以下示例：

```php
$counter = $counter + 1;
```

同样地，你可以编写更短的代码来执行完全相同的操作：

```php
$counter++;
```

看这个示例：

```php
$counter = 0;
$counter++;
$echo $counter;
```

如果你运行上述代码，你将得到输出：

```
1
```

这是因为使用 `++` 会向你 `$counter` 的现有值加 `1`。同样，你也可以使用 `--` 减 1。所以，如果你想从 `$counter` 的现有值中减 1，只需编写 `$counter--;` 即可。

还有另一个快捷方法可以给变量加上数字。你可以使用 `+=1` 给该特定变量加 `1`。你也可以通过这个快捷方法给变量加任何数字。同样，你也可以用它来进行减法、除法或乘法。看下面的示例。以下你可以使用相同格式的一些语句：

```php
$counter/=2;
$counter*=3;
$counter-=2;
$counter+=3;
```

上述语句相对于 `$counter` 分别加上数值 `3`、减去 `2`、乘以 `3` 并除以 `2`。

### 内置高级数学函数

在 PHP 中，你实际上可以执行复杂的数学运算，例如获取数字的平方根。看这个示例：

```php
$rootvar = sqrt (25);
$rootvar = srqt ($number);
```

使用 `$rootvar = sqrt (25)` 和 `$rootvar = srqt ($number)`（注意：`srqt` 可能是 `sqrt` 的拼写错误），PHP 提供了内置函数来处理这些操作。

### 数字格式化

如果你想格式化数字，可以使用 `number_format()`。这允许你指定小数位数、小数点分隔符和千分位分隔符。



一旦你完成对文件的修改，就必须使用函数 `fclose()`将其关闭。它需要一个文件指针作为参数。如果关闭成功，它返回 true；如果失败则返回 false。

### 读取文件

在使用 `fopen()` 函数打开文件后，你可以使用 `fread()` 函数对其进行读取。它需要两个参数。它从句柄引用的文件指针读取指定长度的字节。当读取到指定长度、到达文件末尾、发生套接超时或数据包可用时，它将停止读取。

你可以使用 `filesize()` 函数查找文件的长度。它接受文件名作为参数，并返回以字节为单位的大小。如果失败或返回读取的字符串，它会返回 false。请注意，`fread()` 函数是从文件指针的当前位置读取的。如果你想找到文件指针的当前位置，必须使用 `ftell()` 函数。如果你想回退文件指针的位置，则必须使用 `rewind()`。

请看下面的示例：

```php
<?php
$filename = "/testfile.txt";
$file = fopen($filename, "r");
if ($file == false)
{
    echo ("Opening File Error");
    exit();
}
$filesize = filesize($filename);
$filetext = fread($file, $filesize);
fclose($file);
echo ("The size of the file is $filesize bytes");
echo("<pre> $text </pre>");
?>
```

在上面的示例中，文本文件 `testfile.txt`的内容被赋值给变量，然后作为输出显示。

### 写入文件

如果你想写入新文件或向现有文件追加文本，可以使用 `fwrite()` 函数。它需要两个参数来指定文件指针和要写入的数据字符串。如果你想指定写入数据的长度，可以包含第三个整数参数。尽管第三个整数参数是可选的。如果你不包含第三个参数，写入将在达到指定长度后停止。

`fwrite()` 函数将字符串的内容写入句柄指向的文件流。在出错时返回 false，否则返回字节数。如果你使用的是区分区分文本文件和二进制文件的系统（例如 Windows），你应该在 `fopen()` 的模式参数中包含 `'b'` 来打开文件。此外，如果句柄是以追加模式打开的，`fwrite()` 将变成原子的，除非字符串的大小超过了文件系统的块大小。你不再需要在调用 `fwrite()` 之前对资源进行 `flock()` 操作。你可以无中断地写入所有数据。

请看下面的示例：

```php
<?php
$file = fopen("testfile.txt", "w");
echo fwrite($file, "Testing sample!");
fclose($file);
?>
```

如果你运行上述代码，你将得到输出：

15

为什么？你得到 15 是因为 `Testing sample!` 包括空格在内共有十五个字符。

我可能让你感兴趣的其他书籍预览：

[HTML：从入门到精通学者指南](http://www.amazon.com/gp/product/B00YDSJ8VC?Version=1&entries=0)

《HTML: Step by Step Beginners Guide to HTML》一本书将在书中提供所有必要的信息和培训，你将需要这些信息之后使用其他语言甚至更复杂的 HTML 来提升你的技能。

我们之所以从 HTML 开始我们的“学习 Web 设计”系列，是因为它是世界上每个网站的核心。无论一个网站是多么基础或复杂，HTML 始终存在那里，并且对于它的存在至关重要。

为了完美理解这些材料，我们将从最基础开始学习一切。我们将进行一些练习，因为掌握编程的唯一途径就是不断的练习和学习。

书中的所有材料可以在一天内学完，但以后练习和提升你的技能对于成为一名优秀的程序员是至关重要的。

你可以从[此处]查看/下载书籍](http://www.amazon.com/gp/product/B00YDSJ8VC?Version=1&entries=0)。

## Java

通过这本初学者极速入门课程快速学习 Java 编程！

随着智能手机和平板电脑的发展，今天的应用程序变得越来越强大。两者都被公司广泛使用，而且对初学者来说是一种友好的语言。

尽管 Java 作为一个平台非常流行，但合格程序员仍然短缺。无论你是 Java 的完全新手，还是已经熟悉其他语言，这本书都将提供一个坚实的基础。

我们之所以从 HTML 开始我们的“学习 Web 设计”系列，是因为它是世界上每个网站的核心。无论一个网站是多么基础或复杂，HTML 始终存在那里，并且对于它的存在至关重要。

为了完美理解这些材料，我们将从最基础开始学习一切。我们将进行一些练习，因为掌握编程的唯一途径就是不断的练习和学习。

书中的所有材料可以在一天内学完，但以后练习和提升你的技能对于成为一名优秀的程序员是至关重要的。

你可以从[此处]查看/下载书籍](http://www.amazon.com/gp/product/B00YDSJ8VC?Version=1&entries=0)。

## C#

通过这本初学者极速入门课程快速学习 C# 编程！

如果你对 C++ 编程世界有先验知识，那么你会在 `C#`（读作 See Sharp）中发现熟悉的术语和代码结构。它与 `.NET` 框架配合工作，最初设计作为 Java 的答案。

今天，两者都被公司广泛使用，而且对初学者来说是一种友好的语言。

以下是你将在书内找到的一些核心课程：

- 理解 `C#` 程序结构
- `C#` 编码规范
- 精通变量和数据类型
- 获取输入和使用类型转换
- 算术、条件、关系和逻辑运算符
- 使用流程控制语句
- 生成随机数
- 以及更多！

我希望你喜欢它！

你可以从[此处]查看/下载书籍](http://www.amazon.com/Learn-Programming-Ultimate-Course-Beginners-ebook/dp/B010N2OLRW)。

## HTML5 & CSS3

通过实践项目在一天内学习 CSS3 和 HTML5 并熟练掌握它们！

这本书包含了关于如何使用 HTML5 和 CSS3 设计项目的经过证明的步骤和策略。




不断进化的不仅是硬件。驱动我们硬件的软件也发生了飞跃性的发展。这些软件所承担的程序化流程也同样共享这一进步。

本书将向你介绍互联网下一代技术中最重要的两个方面——`HTML5` 和 `CSS3`。在极不遥的未来，这些系统将运行在每一个尖端网站、Web 应用或移动应用程序中——事实上，许多平台现在已经适配了它们。继续读下去，站在互联网下一代边疆的前沿吧！

希望你喜欢这本书！

你可以从[此处](http://www.amazon.com/HTML5-CSS3-Hands--Programming-Beginners-ebook/dp/B010WC4YIY/ref=asap_bc?ie=UTF8)查看或下载本书。


再次感谢你下载这本书！

希望这本书能够帮助你学习 `PHP` 和 `MySQL`，以及如何编写代码。

下一步是应用你在书中学到的所有知识。

![](img/image00067.jpeg)

最后，如果你喜欢这本书，请花时间分享你的想法并在 Amazon 上发表评论。我们将不胜感激！

[点击此处在 Amazon 上发表评论。](http://www.amazon.com/gp/product/B010Y767LO?*Version*=1&*entries*=0)

感谢并祝你好运！

## 订阅免费 Kindle 电子书

![Description: C:\Users\Pec\Desktop\³²⁰A1A588BAA7A0F9532997D5981C977CAF16C594CC0851607^pimgpsh\_fullsize\_distr.jpg](http://unibulpress.com/)]

[点击此处订阅我们的列表，开始在收件箱中接收免费的 Kindle 电子书。](http://unibulpress.com/)

