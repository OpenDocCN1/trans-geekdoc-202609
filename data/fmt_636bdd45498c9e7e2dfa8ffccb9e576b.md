
此函数可编写为最多接受五个参数。按顺序，这些参数分别为：错误编号（对应表 8.1）、文本错误消息、发现错误的文件名、发生错误的具体行号，以及错误发生时存在的变量。定义一个接受所有这些参数的函数可能如下所示：

```
function report_errors ($num, $msg, $file, $line, $vars) {...}
```

为了利用这一概念，`report_errors.php` 文件（脚本 8.2）将最后重写一次。

### 创建您自己的错误处理程序

**1.** 在文本编辑器或 IDE 中打开 `report_errors.php`（脚本 8.2）（如果尚未打开）。

**2.** 删除 `ini_set()` 和 `error_reporting()` 行（脚本 8.3）。

当您建立自己的错误处理函数时，错误报告级别不再有任何意义，因此调整它们的那行代码可以删除。调整 `display_errors` 设置也毫无意义，因为错误处理函数将控制错误是否显示。

**脚本 8.3.** 通过定义您自己的错误处理函数，您可以自定义 PHP 脚本处理错误的方式。

```
<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Transitional//EN"
    "http://www.w3.org/TR/xhtml1/DTD/xhtml1-transitional.dtd">
<html xmlns="http://www.w3.org/1999/xhtml" xml:lang="en" lang="en">
<head>
    <meta http-equiv="Content-Type" content="text/html; charset=utf-8" />
    <title>Handling Errors</title>
</head>
<body>

<h2>Testing Error Handling</h2>
<?php # Script 8.3 - handle_errors.php

// Flag variable for site status:
define('LIVE', FALSE);

// Create the error handler:
function my_error_handler ($e_number, $e_message, $e_file, $e_line, $e_vars) {

    // Build the error message:
    $message = "An error occurred in script '$e_file' on line $e_line: $e_message\n";

    // Append $e_vars to $message:
    $message .= print_r ($e_vars, 1);

    if (!LIVE) { // Development (print the error).
        echo '<pre>' . $message . "\n";
        debug_print_backtrace();
        echo '</pre><br />';
    } else { // Don't show the error.
        echo '<div class="error">A system error occurred. We apologize for the
            inconvenience.</div><br />';
    }

} // End of my_error_handler() definition.

// Use my error handler:
set_error_handler ('my_error_handler');

// Create errors:
foreach ($var as $v) {}
$result = 1/0;

?>
</body>
</html>
```

**3.** 在脚本创建错误之前，添加：

```
define ('LIVE', FALSE);
```

此常量将作为一个标志，用于指示站点当前是否处于上线状态。这是一个重要的区别，因为您处理错误和在浏览器中揭示信息的方式，在开发站点和站点上线时应有很大不同。

之所以在函数外部设置此常量，有两个原因。首先，我希望将该函数视为一个黑盒，它无需我深入内部修改即可完成我需要的工作。其次，在许多站点中，可能还有其他设置（如数据库连接信息）也是针对上线环境与开发环境特定的。因此，条件语句也可以引用此常量来调整那些设置。

**4.** 开始定义错误处理函数：

```
function my_error_handler ($e_number, $e_message, $e_file, $e_line, $e_vars) {
```

`my_error_handler()` 函数设置为接收自定义错误处理程序可接收的完整五个参数。

**5.** 使用接收到的值创建错误消息。

```
$message = "An error occurred in script '$e_file' on line $e_line: $e_message\n";
```

错误消息将首先引用发生错误的文件名和行号。随后附加上实际的错误消息。当函数被调用时（即发生错误时），所有这些值都会被传递给函数。

**6.** 将任何现有变量添加到错误消息中：

```
$message .= print_r ($e_vars, 1);
```

发生错误时，`$e_vars` 变量将接收所有存在的变量及其值。因为这可能包含有用的调试信息，所以将其添加到消息中。

`print_r()` 函数通常用于打印变量的结构和值；它对于数组特别有用。如果使用第二个参数（1 或 TRUE）调用该函数，结果将被返回而不是打印。因此，这一行将所有变量信息添加到 `$message` 中。

**7.** 根据站点是否上线打印不同的消息：

```
if (!LIVE) {
    echo '<pre>' . $message . "\n";
    debug_print_backtrace();
    echo '</pre><br />';
} else {
    echo '<div class="error">A system error occurred. We apologize for the inconvenience.</div><br />';
}
```

如果站点未上线（即 `LIVE` 为 `FALSE`），这在站点开发期间通常是这种情况，则应打印详细的错误消息。为了便于查看，错误消息会在 HTML `PRE` 标签内打印。此外，还会调用一个有用的调试函数 `debug_print_backtrace()`。该函数返回大量关于已调用函数、已包含文件等的信息。

在开发阶段，详细的错误消息会打印在 Web 浏览器中。（在包含更多代码的实际脚本中，这些消息会更有用。）

如果站点已上线，将打印一条简单的道歉消息，让用户知道发生了错误，但不透露具体问题。在这种情况下，您也可以使用 `error_log()` 函数（见侧栏）将详细错误消息通过电子邮件发送或写入日志。

一旦站点上线，将打印更友好（且泄露信息更少）的错误。此处，针对脚本中的三个错误，每个都打印了一条消息。

**8.** 完成函数并告诉 PHP 使用它：

```
}
set_error_handler('my_error_handler');
```

这第二行是关键，它告诉 PHP 使用自定义错误处理程序，而不是 PHP 的默认处理程序。

**9.** 将文件保存为 `handle_errors.php`，将其放在您的 Web 目录中，并在 Web 浏览器中测试它。

**10.** 将 `LIVE` 的值改为 TRUE，保存，然后重新测试脚本。

### 记录 PHP 错误

在脚本 8.3 中，错误处理方式仅是详细打印出来或不打印。另一种选择是*记录*错误：以某种方式永久记录它们。为此，`error_log()` 函数指示 PHP 如何记录错误。其语法为：

```
error_log (message, type, destination, extra headers);
```

*message* 值应为记录错误的文本（即脚本 8.3 中的 `$message`）。*type* 指示错误如何记录。选项为数字 0、1、3 和 4：使用计算机的默认记录方法 (0)、通过电子邮件发送 (1)、写入文本文件 (3) 或发送给 Web 服务器的记录处理程序 (4)。

*destination* 参数可以是文件名（用于记录类型 3）或电子邮件地址（用于记录类型 1）。*extra headers* 参数仅在发送电子邮件时使用（记录类型 1）。destination 和 extra headers 都是可选的。

要查看错误处理程序在实际站点上的表现，只需更改这一个值。

***

提示

如果您的 PHP 页面使用特殊的 HTML 格式——如影响布局和字体处理的 CSS 标签——请将此信息添加到您的错误报告函数中。

***

提示

显然，在实际站点中，您可能需要做的不仅仅是为不便道歉（特别是当错误严重影响页面功能时）。尽管如此，这个示例演示了如何轻松调整错误处理以适应具体情况。

***

提示

如果您不想让错误处理函数报告每一个通知、错误或警告，可以检查错误编号值（传递给函数的第一个参数）。例如，要在站点上线时忽略通知，您需要将主条件语句更改为

```
if (!LIVE) {
    echo '<pre>' . $message . "\n";
    debug_print_backtrace();
    echo '</pre><br />';
} elseif ($e_number != E_NOTICE) {
    echo '<div class="error">A system error occurred. We apologize for the inconvenience.</div><br />';
}
```

### PHP 调试技巧

说到调试，您将从经验中最好地学到特定类型错误的成因。了解常见成因将缩短修复错误所需的时间。为了加快学习过程，**表 8.2** 列出了最常见 PHP 错误的可能原因。

**表 8.2. 常见 PHP 错误**

![Image](img/08tab02.jpg)

您将遇到的第一种、也是最常见的错误类型是语法错误，它会阻止脚本执行。此类错误会导致类似 ![Image](img/circle-a.jpg) 所示的消息，每位 PHP 开发人员都见过太多次了。为避免编程时犯此类错误，请务必：

![Image](img/08_figure_18_a.jpg)

![Image](img/circle-a.jpg) 解析错误因无效的 PHP 语法而阻止脚本运行。此错误是由于打印 `$array['key']` 的值时未将其放在花括号内引起的。

- 每个语句（但不包括循环和条件判断等语言结构）都要以分号结尾。

- 所有引号、圆括号、花括号和方括号必须成对匹配（每个左符号必须有对应的右符号）。

- 引号使用要一致（单引号只能用单引号闭合，双引号只能用双引号闭合）。

- 根据需要，使用反斜杠转义字符串中的所有单引号和双引号。

关于语法错误，还有一点您应该明白：PHP 错误消息指出错误发生在第 12 行，并不意味着错误实际上就在那一行。至少，PHP 认为的第 12 行与您的文本编辑器指示的第 12 行之间存在差异的情况并不少见。因此，虽然 PHP 的指引对追踪问题很有用，但请将引用的行号视为起点而非绝对位置。

如果 PHP 报告文档最后一行有错误，这几乎总是因为不匹配的圆括号、花括号或引号直到那时才被捕获。

您将遇到的第二种错误类型源于函数的误用。例如，在缺少适当参数的情况下调用函数时就会发生此错误。PHP 在尝试执行代码时会发现此错误。在后续章节中，您使用 `header()` 函数、Cookie 或会话时可能会看到此类错误。

要修复错误，您需要做一些侦探工作，看看犯了什么错以及错在哪里。但首先，请始终仔细阅读并信任 PHP 提供的错误消息。虽然引用的行号不一定总是正确，但 PHP 错误描述非常详细，通常很有帮助，且几乎总是 100% 正确的。

#### 调试脚本

- 开启 `display_errors`。

使用前面的步骤为脚本启用 `display_errors`，或者如果可能，在开发应用程序时为整个服务器启用它。

- 使用注释。

正如您可以使用注释来记录脚本，也可以用它们来排除有问题的行。如果 PHP 报告第 12 行有错误，那么注释掉该行应该能消除错误。如果不能，则说明错误在别处。只需小心，不要因不当地仅注释掉代码块的一部分而引入更多错误：脚本的语法必须保持完整。

- 使用 `print` 和 `echo` 函数。

在更复杂的脚本中，我经常使用 `echo` 语句在脚本执行过程中给自己留下关于正在发生什么的提示 ![Image](img/circle-b.jpg)。当脚本有多个步骤时，可能不容易知道问题是发生在第 2 步还是第 5 步。通过使用 `echo` 语句，您可以将问题范围缩小到特定的节点。

![Image](img/08_figure_19_b.jpg)

![Image](img/circle-b.jpg) 通过留下脚本正在执行操作的提示，可以完成更复杂的调试。

- 检查打印变量时使用的引号。

程序员误用单引号，然后纳闷为什么变量无法正确打印，这种情况并不少见。请记住，单引号按字面意思处理文本，必须使用双引号才能打印出变量的值。

- 跟踪变量 ![Image](img/circle-c.jpg)。

![Image](img/08_figure_20_c.jpg)

![Image](img/circle-c.jpg) 打印变量的名称和值是跟踪它们在脚本执行过程中变化的最简单方法。

脚本无法工作，很可能是因为您引用了错误的变量、用错名称引用了正确的变量，或者变量的值不是您所预期的。要检查这些可能性，请使用 `print` 或 `echo` 语句在脚本的关键点打印出变量的值。这只是一个简单的

```
echo "<p>\$var = $var</p>\n";
```

或

```
echo "<p>\$var is $var</p>\n";
```

第一个美元符号被转义，以便打印变量的名称。第二个变量引用将打印其值。

***

**使用 `die()` 和 `exit()`**

错误管理中常用的两个函数是 `die()` 和 `exit()`（它们技术上属于语言结构而非函数，但这有关系吗？）。当脚本中调用 `die()` 或 `exit()` 时，整个脚本将终止。如果发生重要事件失败——如建立数据库连接——两者都可用于阻止脚本继续执行。您也可以向 `die()` 和 `exit()` 传递一个字符串，该字符串将在浏览器中打印出来。

您常会在 `OR` 条件语句中看到 `die()` 或 `exit()` 的用法。例如：

```
include('config.inc.php') OR die ('Could not open the file. ');
```

有了这一行，如果 PHP 无法包含配置文件，将执行 `die()` 语句并打印“Could not open the file.”消息。您将在本书和 PHP 手册中看到此用法的变体，因为这是一种无需使用自定义错误处理程序即可处理错误的快速但可能过度的方法。

***

- 打印数组值。

对于更复杂的变量类型（数组和对象），`print_r()` 和 `var_dump()` 函数无需循环即可打印其值。两个函数完成相同的任务，尽管 `var_dump()` 的报告比 `print_r()` 更详细。

***

提示

许多文本编辑器都包含用于检查圆括号、方括号和引号是否匹配的实用程序。

***

提示

如果你无法在复杂的脚本中找到解析错误，请首先使用 `/* */` 注释使整个 PHP 代码失效。然后逐个取消注释各个部分（通过移动开始或结束注释字符）并重新运行脚本，直到推断出哪些行导致了错误。不过要注意如何注释掉控制结构，因为花括号必须继续匹配，以避免解析错误。例如：

```
if (condition) {  

    /* Start comment.  

    Inert code.  

    End comment. */  

}
```

---

**提示**

为了使 `print_r()` 的结果在 Web 浏览器中更具可读性，请将其包裹在 HTML `<pre>`（预格式化）标签中。这一行是我最喜欢的调试工具之一：

```
echo '<pre>' . print_r($var, 1) . '</pre>';
```

---

### SQL 和 MySQL 调试技术

最常见的 SQL 错误由以下问题引起：

*   引号或括号使用不平衡

*   列值中的撇号未转义

*   列名、表名或函数名拼写错误

*   在连接查询中模糊地引用列

*   将查询的子句（`WHERE`、`GROUP BY`、`ORDER BY`、`LIMIT`）放在了错误的顺序

此外，使用 MySQL 时还可能遇到以下情况：

*   不可预测或不合适的查询结果

*   无法访问数据库

由于你将从 PHP 中运行动态网站的查询，因此你需要一种在该上下文中调试 SQL 和 MySQL 错误的方法（PHP 不会报告你的 SQL 问题）。

#### 调试 SQL 问题

要判断你遇到的是 MySQL（或 SQL）问题而不是 PHP 问题，你需要一套查找和修复问题的系统。幸运的是，调试 MySQL 和 SQL 问题应采取的步骤很容易定义，且应不假思索地遵循。如果你有任何 MySQL 或 SQL 错误需要调试，只需遵循以下步骤序列。

> **为了强调重点，接下来的这一系列步骤可能是本章甚至全书中最有用的调试技术。在任何 PHP-MySQL Web 应用程序中，当你得不到预期结果时，很可能都需要遵循这些步骤。**

#### 调试 SQL 查询

**1.** 在 PHP 脚本中打印出任何适用的查询。

确切知道 PHP 脚本试图执行什么查询，是解决 SQL 和 MySQL 问题最有用的第一步。
