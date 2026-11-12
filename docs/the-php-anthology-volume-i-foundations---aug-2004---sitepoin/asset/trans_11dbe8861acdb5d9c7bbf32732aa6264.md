

occurred. 最后，$errContext（在本示例中我们尚未使用它）包含一个数组，其中包含错误发生点的所有全局变量的名称和值。在某些情况下，这些信息可能对调试有用，例如，它包含 $_SERVER 变量，其中可以找到访客浏览器的详细信息。

定义自定义错误处理函数后，我们需要做的就是使用 set_error_handler 告诉 PHP 新的处理程序。

执行此脚本将生成以下 HTML：

```
<h2>Custom Error Message</h2>
<b>E_USER_ERROR</b> in /home/username/www/errorhandling/6.php on
line 31<br />
Error connecting to MySQL Server: Access denied for user:
'wronguser@localhost' (Using password: YES)
```

需要注意的是，该示例生成了两条错误消息：一条是由 mysql_connect 函数产生的 E_WARNING，我们已通过错误抑制运算符将其抑制；另一条是我们通过 trigger_error 生成的 E_USER_ERROR。如前所述，错误抑制运算符和 error_reporting 函数仅适用于 PHP 的内置错误处理程序，而不适用于您定义的自定义处理程序。这意味着自定义处理程序实际上会捕获这两个错误，如以下脚本所示：

```
<?php
/**
 * Custom Error handler
 *
 * @param int error level number
 * @param string error message
 * @param string php script where error occurred
 * @param int line number in script where error was triggered
 * @param array current state of all global variables
 */
function myErrorHandler($errLvl, $errMsg, $errFile, $errLine,
 $errContext)
{
 // Switch statement watching for specific error levels
 switch ($errLvl) {
 case E_USER_ERROR:
 $error = "<h2>Custom Error Message</h2>
 <b>E_USER_ERROR</b> in $errFile on line $errLine<br />
 $errMsg";
 break;
 // Catch all other errors
 default:
 $error = "<h2>Default Error Message</h2>
 <b>Level: $errLvl</b> in $errFile on line $errLine<br />
 $errMsg";
 break;
 }
 echo $error;
 }

// Set the custom error handler
set_error_handler('myErrorHandler');

// Attempt to disable E_WARNING messages (applies to built-in
// handler only)
error_reporting(E_ALL ^ E_WARNING);

// Trigger an error
if (!@mysql_connect('localhost','wronguser','wrongpassword')) {
    trigger_error('Error connecting to MySQL Server: ' .
    mysql_error(), E_USER_ERROR);
}
?>
```

尽管我们试图通过 error_reporting 函数和错误抑制运算符禁用 E_WARNING 消息，但上述示例仍会报告这两个错误。

## 触发的错误与条件执行

PHP 的自定义错误处理机制实际上为您的应用程序引入了另一层错误处理，这一次是在全局级别。在使用此机制之前，理解这种方法的后果非常重要。

到目前为止，您可能已在调用时将错误处理构建到代码中。以下是一个典型示例：

```
<?php
// Some function which updates the database
function updateUserDetails($name, $password, $email)
{
    // If update succeeds...
    return TRUE;
}

// If update failed
return FALSE;
}

// If a form was submitted
if (isset($_GET['submitUserDetailsForm'])) {
    // Perform "call time" error checking
    if (updateUserDetails($_GET['name'], $_GET['password'],
        $_GET['email'])) {
        echo 'Update succeeded';
    } else {
        echo 'Update failed. Please try again';
    }
}
?>
```

这段代码（旨在说明一种常见模式，而非可运行示例）展示了错误处理通常如何构建到应用程序中。调用 updateUserDetails 函数的代码会检查从函数中获取的值（TRUE 或 FALSE），并作出相应响应。

PHP 的自定义错误处理机制不允许这种模式。让我们看看上述示例的等效写法：

```
<?php
// Some function which updates the database
function updateUserDetails($name, $password, $email)
{
    // If update failed
    trigger_error('Update failed', E_USER_WARNING);
}

// If a form was submitted
if (isset($_GET['submitUserDetailsForm'])) {
    updateUserDetails($_GET['name'], $_GET['password'],
        $_GET['email']);
}
?>
```

调用 updateUserDetails 函数的代码现在无法检查函数是否成功。相反，您的自定义错误处理程序必须对函数做出响应，由于它与 updateUserDetails 或调用它的代码完全独立地定义，因此要使其正确响应会很困难。有方法可以将自定义错误处理与您的应用程序更紧密地集成，但通常涉及复杂的变通方法和 hack，最终导致难以维护且易于损坏的代码。

在 PHP 4 中，开发者在处理错误时会面临一个问题，即条件错误检查仅在发生错误的点起作用，而自定义错误处理在全局级别运行，并且与代码的逻辑流程断开连接。如前所述，PHP 5 引入了一种新的错误处理机制，称为 **异常处理**，它将允许您在错误发生的点 *和* 全局级别处理错误。目前，最好不要过度使用 PHP 的自定义错误处理；而是将其简单视为网站的“看门狗”，确保记录发生的错误，以便下次有时间时可以更正它们。PHP 4 的一个良好过渡解决方案是 PEAR::Error 类，它是核心 PEAR 安装的一部分。使用 PEAR::Error，当您准备利用 PHP 5 中将包含的新错误处理时，您的代码应该相当容易修改。有关 PEAR::Error 的建议阅读材料可在本章末尾找到。

## 如何记录和报告错误？

自定义错误处理程序变得有用的地方在于创建您稍后可以访问的错误日志，并在调整应用程序时参考它们。为了方便起见，PHP 自带 error_log 函数，可用于写入日志文件或发送包含错误报告的电子邮件等操作。此函数可在自定义错误处理程序内部用于存储错误数据。例如：

```
<?php
/**
 * Custom Error handler
 *
 * @param int error level number
 * @param string error message
 * @param string php script where error occurred
 * @param int line number in script where error was triggered
 * @param array current state of all global variables
 */
function myErrorHandler($errLvl, $errMsg, $errFile, $errLine,
                        $errContext)
{
    $time = date('YmdHis');
    $errMsg = htmlspecialchars($errMsg);
    $error = <<<EOD
####START ERROR####
Level: $errLvl
File: $errFile
Line: $errLine
Time: $time

$errMsg
####END ERROR####

EOD;
error_log($error, 3, 'log/errors.log');
switch ($errLvl) {
  case E_USER_ERROR:
    echo 'System is temporarily unavailable. ' .
      'Please try again later';
    break;
  }
}

// Set the custom error handler
set_error_handler('myErrorHandler');

// Trigger an error
if (!@mysql_connect('localhost', 'wronguser', 'wrongpassword')) {
  trigger_error('Error connecting to MySQL Server: ' .
    mysql_error(), E_USER_ERROR);
}
?>
```

自定义错误处理程序现在以易于使用 PHP 字符串函数解析的格式记录错误。它将这些错误记录到 errors.log 文件中，该文件如下所示：

```
####START ERROR####
Level: 256
File: c:\htdocs\phpanth\errorhandling\8.php
Line: 39
Time: 20031012233727

Error connecting to MySQL Server: Access denied for user:
'wronguser@127.0.0.1' (Using password: YES)
####END ERROR####
```

## 电子邮件过载

尽管 error_log 能够发送包含错误消息的电子邮件，但请小心！您的收件箱中可能会出现比您预期的更多内容。您可以通过 php.ini 值 ignore_repeated_errors 和 ignore_repeated_source 控制错误报告的频率——有关详细信息，请参见附录 A。

当然，您并不局限于仅使用 error_log 函数来创建日志文件。您可以决定编写自己的类来记录错误，或者考虑使用 PEAR::Log[4]，它提供了更多选项来捕获应用程序中的数据。

## 如何优雅地显示错误？

既然您已经了解了如何定义自己的自定义错误处理程序，我可以向您展示如何使用 PHP 的输出缓冲（我将在第二卷第 5 章中详细讨论，并在 PHP Manual[5] 中描述），以便您的生产网站能优雅地告知用户“暂时遇到困难”，而无需在部分呈现的 HTML 页面上贴上丑陋的错误消息。以下示例演示了这种方法，并提供了一个更全面的自定义错误处理程序，它能够处理多个错误级别：

```
<?php
/**
 * Custom Error handler
 *
 * @param int error level number
 * @param string error message
 * @param string php script where error occurred
 * @param int line number in script where error was triggered
 * @param array current state of all global variables
 */
function myErrorHandler($errLvl, $errMsg, $errFile, $errLine,
$errContext)
{
    switch ($errLvl) {
        // Handle ERRORs
        case E_USER_ERROR:
            // Stop and clean the second buffer
```

[4] http://pear.php.net/package/Log
[5] http://www.php.net/manual/en/ref.outcontrol.php

