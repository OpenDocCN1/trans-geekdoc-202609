
此函数可编写为最多接受五个参数。按顺序，这些参数分别为：错误编号（对应[表 8.1](#ch08.html#ch08table01)）、文本错误消息、发现错误的文件名、发生错误的具体行号，以及错误发生时存在的变量。定义一个接受所有这些参数的函数可能如下所示：

```
function report_errors ($num, $msg, $file, $line, $vars) {...}
```

为了利用这一概念，`report_errors.php` 文件（[脚本 8.2](#ch08.html#ch08ex02)）将最后重写一次。

### 创建您自己的错误处理程序

**1.** 在文本编辑器或 IDE 中打开 `report_errors.php`（[脚本 8.2](#ch08.html#ch08ex02)）（如果尚未打开）。

**2.** 删除 `ini_set()` 和 `error_reporting()` 行（[脚本 8.3](#ch08.html#ch08ex03)）。

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

在[脚本 8.3](#ch08.html#ch08ex03) 中，错误处理方式仅是详细打印出来或不打印。另一种选择是*记录*错误：以某种方式永久记录它们。为此，`error_log()` 函数指示 PHP 如何记录错误。其语法为：

```
error_log (message, type, destination, extra headers);
```

*message* 值应为记录错误的文本（即[脚本 8.3](#ch08.html#ch08ex03) 中的 `$message`）。*type* 指示错误如何记录。选项为数字 0、1、3 和 4：使用计算机的默认记录方法 (0)、通过电子邮件发送 (1)、写入文本文件 (3) 或发送给 Web 服务器的记录处理程序 (4)。

*destination* 参数可以是文件名（用于记录类型 3）或电子邮件地址（用于记录类型 1）。*extra headers* 参数仅在发送电子邮件时使用（记录类型 1）。destination 和 extra headers 都是可选的。
