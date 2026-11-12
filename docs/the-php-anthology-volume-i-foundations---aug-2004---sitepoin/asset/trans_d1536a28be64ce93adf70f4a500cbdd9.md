
ob_end_clean();
// Clean out the main buffer
ob_clean();
// Display an error message
echo '
<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Strict//EN"
"http://www.w3.org/TR/xhtml1/DTD/xhtml1-strict.dtd">
<html xmlns="http://www.w3.org/1999/xhtml">
<head>
<title> Temporary Interruption </title>
<meta http-equiv="Content-Type"
content="text/html; charset=iso-8859-1" />
</head>
<body>
<h2>Temporary Interruption</h2>
The site is currently down for non-scheduled maintenance.<br />
Please try again shortly
</body>
</html>';
// End and flush the main buffer
ob_end_flush();
// Stop execution
exit();
break;
// Handle WARNINGs
case E_USER_WARNING:
// Clean out the main buffer
ob_clean();
// Display an error message
echo '<b>Warning:</b> ' . $errMsg;
break;
// Handle NOTICEs
case E_USER_NOTICE:
// Display an error message
echo '<b>Notice:</b> ' . $errMsg;
break;
}
}
```

这个自定义错误处理程序能够处理三种错误级别：E_USER_ERROR、E_USER_WARNING 和 E_USER_NOTICE。你会注意到，它在每个级别处理输出缓冲区的方式略有不同。E_USER_ERROR 消息（如前所述，这是一个致命错误）会导致处理程序清除两个输出缓冲区（共有两个，其原因稍后会变得显而易见），并显示关于网站宕机的消息；这会完全移除可能已发送到缓冲区的任何 HTML。E_USER_WARNING 错误会导致第二个缓冲区被擦除并替换为错误消息；结果，HTML 页面的正文被错误消息替换。E_USER_NOTICE 行为将通知错误添加到第二个缓冲区中——它只是附加到现有 HTML 之后。

看看页面主体现在的样子：

```
// Set the custom error handler
set_error_handler('myErrorHandler');
// Start an output buffer for ERRORs
ob_start()
?>
<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Strict//EN"
    "http://www.w3.org/TR/xhtml1/DTD/xhtml1-strict.dtd">
<html xmlns="http://www.w3.org/1999/xhtml">
<head>
<title> Custom Error Handling with Buffering </title>
<meta http-equiv="Content-Type"
    content="text/html; charset=iso-8859-1" />
</head>
<body>
<h2>Example Errors</h2>
<?php
// Start a second output buffer for NOTICES and WARNINGs
ob_start();
?>
```

如上所示，在指示 PHP 使用我们的自定义错误处理程序后，我们将一个输出缓冲区嵌套在另一个缓冲区内，以便页面的页头和页脚位于与正文分开的缓冲区中。

```
<a href="?<?php echo $_SERVER['PHP_SELF']; ?>?triggerError=error">
Trigger a Fatal Error</a><br />
<a href="?<?php echo $_SERVER['PHP_SELF']; ?>?triggerError=warning">
Trigger a Warning</a><br />
<a href="?<?php echo $_SERVER['PHP_SELF']; ?>?triggerError=notice">
Trigger a Notice</a><br />

<?php
// Generate sample errors
if (isset($_GET['triggerError'])) {
switch ($_GET['triggerError']) {
```

```
case 'error':
    trigger_error('A fatal error', E_USER_ERROR);
    break;
case 'warning':
    trigger_error('You have been warned!', E_USER_WARNING);
    break;
case 'notice':
    trigger_error('Please take note!', E_USER_NOTICE);
    break;
}
}
// Finish and display the second buffer
ob_end_flush();
?>
</body>
</html>
<?php
// Finish the main buffer
ob_end_flush();
?>
```

在页面正文中，在第二个缓冲区内，我们使用了 trigger_error 来演示处理程序，并使用 $_GET 变量 triggerError。

执行脚本时，你会发现致命错误会导致呈现完全不同的页面（如 E_USER_ERROR 的自定义错误处理程序中定义）；警告错误会用警告消息替换三个链接，而错误通知会添加到三个链接下方。

只要小心处理，就可以将自定义处理程序与输出控制相结合，以优雅的方式（从网站访问者的角度）处理错误。不过请注意，最好保持这类代码简洁务实，而不是构建过于复杂的东西，原因将在 "如何在 PHP 中实现自定义错误处理程序？" 中讨论，位于 "触发的错误与条件执行" 节。

## 进一步阅读

- [PHP 中的错误处理](http://www.devshed.com/Server_Side/PHP/ErrorHandling)

这个两部分系列深入探讨了 PHP 的自定义错误处理功能以及如何将其与输出缓冲相结合。

- [错误处理](http://www.derickrethans.nl/errorhandling/talk.html)

Derick Rethans，PHP 的领先开发者之一，在这个很棒的教程中对从 HTTP 状态页面到调试和分析 PHP 代码的错误处理技术进行了简洁的分析。

- [PEAR-Error 详解](http://www.php-mag.net/itr/online_artikel/psecom,id,330,nodeid,114.html)

Alexander Merz 在 PHP 杂志上发表的这篇免费文章中详细考察了 PEAR::Error。

## 附录 A：PHP 配置

这是一个关于配置 PHP 的快速参考，涵盖了你需要了解的最重要的一般设置，无论是在实时环境中运行应用程序，还是因为它们影响安全性或编码方式。

### 配置机制

配置 PHP 的主要机制是 php.ini 文件。作为主文件，它让你可以控制所有配置设置。条目通常采用以下格式：

```
setting = value
```

不过，在做出更改之前，请务必阅读文件中提供的注释。有一些小技巧，例如在 Unix 上 include_path 使用冒号 (:) 作为分隔符，而在 Windows 上使用分号 (;)。

大多数 Web 主机不会让你访问 php.ini 文件，除非你对系统拥有根访问权限（如果你使用的是廉价虚拟托管服务，通常不是这种情况）。你的下一个选择是使用 .htaccess 文件来配置 PHP（假设 Web 服务器是 Apache）。

.htaccess 文件是一个纯文本文件，你将其放在公共 Web 目录中，以确定 Apache 在从该目录提供页面时的行为；例如，你可以标识允许公众访问的页面。请注意，.htaccess 文件的效果是递归的——它也适用于子目录。

要使用 .htaccess 文件配置 PHP，你的托管提供商必须在 Apache 主 httpd.conf 配置文件中为你的 Web 目录应用 AllowOverride Options 或 AllowOverride All 设置。假设已完成此操作，有两个 Apache 指令可用于修改 PHP 的配置：

**php_flag**
用于具有布尔值的设置（即 on/off 或 1/0），例如 register_globals

**php_value** 用于为设置指定字符串值，例如你可能使用的 include_path 设置

以下是示例 .htaccess 文件：

```
# Switch off register globals
php_flag register_globals off

# Set the include path
php_value include_path ".:/home/username/pear"
```

控制 PHP 配置的最后一种机制是 ini_set 和 ini_alter 函数组，它们允许你修改配置设置，以及 ini_get，它允许你检查配置设置，还有 ini_restore，它将 PHP 的配置重置为由 php.ini 和任何 .htaccess 文件定义的默认值。使用 ini_set，这里有一个示例，允许我们在连接到 MySQL 时避免定义主机、用户名和密码：

```
ini_set('mysql.default_host', 'localhost');
ini_set('mysql.default_user', 'harryf');
ini_set('mysql.default_password', 'secret');

if (!mysql_connect()) {
 echo mysql_error();
} else {
 echo 'Success';
}
```

请注意，PHP 为某些设置（例如 error_reporting）提供了替代函数，这些函数与 ini_set 的作用基本相同。使用哪个是个人偏好的问题。

请注意，某些设置（例如 register_globals）只能通过 php.ini 或 .htaccess 才能有用地修改，因为这些设置会在 PHP 开始执行脚本之前影响其行为。

此外，某些配置设置只能在 php.ini 中更改，例如 extension_dir，它告诉 PHP 查找 PHP 扩展的目录。要完整参考控制设置，请参阅 PHP 手册[1]。

