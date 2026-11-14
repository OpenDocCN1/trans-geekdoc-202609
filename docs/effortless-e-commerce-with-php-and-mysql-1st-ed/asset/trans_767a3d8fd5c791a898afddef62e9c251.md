

- 5. 开始定义错误处理函数：

```php
function my_error_handler ($e_number, $e_message, $e_file, $e_line,
   $e_vars) {
global $live, $contact_email;
```

PHP 允许你定义自己的错误处理函数。通过这样做，你可以精确控制报告哪些错误、以何种方式报告以及报告的详细程度。每当发生 PHP 错误，或使用 `trigger_error()` 触发错误时，不久将创建的脚本都会调用此函数。唯一的例外是解析错误和其他严重的 PHP 错误，这些错误会阻止脚本首先被执行。

错误处理函数可以定义为接收两到五个参数。在这里，我使用了全部五个参数。第一个参数是数字错误指示器，可能被赋予如 2 这样的值，代表 `E_WARNING`。第二个参数是接收到的错误消息。下一个参数是发生错误的文件名，第四个参数是错误发生的行号。第五个参数是错误发生时存在的所有变量的数组。这可以作为有用的调试信息（说到调试，信息几乎总是越多越好）。

- 6. 开始创建详细的错误消息：

```php
$message = "An error occurred in script '$e_file' on line $e_line:
   \n$e_message\n";
```

详细的错误消息将以相关文件名、行号和消息字符串开头。

- 7. 添加回溯信息：

```php
$message .= "<pre>" . print_r(debug_backtrace(), 1) . "</pre>\n";
```

`backtrace` 本质上是错误发生前发生的所有事情。这将包括已执行的文件、已调用的函数、传递给函数的参数以及存在的变量。你可以通过调用 `debug_backtrace()` 函数获取回溯信息，该函数返回一个数组。要将该数组添加到错误消息中，请将其（或创建该数组的函数调用）作为第一个参数传递给 `print_r()`，并将 `1` 或 `true` 用作 `print_r()` 中的第二个参数值。为 `print_r()` 提供正数的第二个参数会告诉函数返回值，而不是打印它。我将此代码包裹在 HTML 预格式化标签 `<pre>...</pre>` 中，以便更易读。

如果你不想要详细的回溯，可以简单地将变量及其值列表追加到消息中，如下所示：

```php
$message .= "<pre>" . print_r ($e_vars, 1) . "</pre>\n";
```

- 8. 如果网站未上线，则在浏览器中显示错误消息：

```php
if (!$live) {
    echo '<div class="error">' . nl2br($message) . '</div>';
}
```

对于未上线的网站，最好能立即收到任何问题的通知。在这里，错误消息将在一个被赋予 error 类的 `<div>` 中打印。为了将换行符（\n）转换为 HTML 换行标签，应用了 nl2br() 函数。图 3.5 显示了浏览器中的示例详细错误消息。

![](img/4f47e47c67bd619ac73250f11c9fc7ce_76_0.png)

图 3.5

- 9. 如果网站已上线，则通过电子邮件发送错误：

```php
} else {
    error_log($message, 1, $contact_email, 'From:admin@example.com');
}
```

error_log() 函数可以以不同方式记录错误。其第一个参数是错误消息。第二个是目标类型，1 表示电子邮件（默认值为零会将消息发送到操作系统的日志）。第三个参数是目标本身；对于电子邮件，这是“收件人”电子邮件地址。第四个参数仅用于发送电子邮件，用于添加任何其他标头，例如“发件人”电子邮件地址。

> **注意**
> 希望在经过充分测试、已上线的网站中，客户永远不会看到即使是通用错误消息，因为所有漏洞都已修复。

- 10. 如果网站已上线，且错误不是通知，则显示通用消息：

```php
if ($e_number != E_NOTICE) {
    echo '<div class="error">A system error occurred. We apologize for the inconvenience.</div>';
}
```

如果网站已上线，用户不应看到详细的错误消息（那将是严重的安全违规）；相反，他们将收到一个模糊的响应。但是，发生的一些错误可能不是实际问题，只是对功能没有影响的技术疏忽。此类错误作为通知引发，因此只有当错误不是通知级别时才会报告。实际上，如果网站已上线，图 3.5 中指示的错误不会被报告。图 3.6 显示了用户遇到另一种类型的错误时可能看到的内容。

![](img/4f47e47c67bd619ac73250f11c9fc7ce_77_0.png)

- 11. 完成 my_error_handler() 函数：

```php
}
// End of $live IF-ELSE.
return true;
}
// End of my_error_handler() definition.
```

错误处理函数应返回非假值以指示错误已被处理。如果函数返回 false，则 PHP 的默认错误处理程序也会被调用（在已上线的网站上这将是糟糕的）。

- 12. 应用错误处理程序：

```php
set_error_handler('my_error_handler');
```

这一行实际上告诉 PHP 使用自定义函数来处理错误。如果不执行此函数调用，PHP 仍将使用其默认处理程序。这也是解析错误不会通过你自己的错误处理程序的原因，因为解析错误阻止了 PHP 脚本的执行。

- 13. 保存文件。

## HTML 模板

要创建网站的浏览器端，你应先设计一个或多个 HTML 模板，以描绘最终动态网站的外观。对于本网站，我想使用一种优雅的设计，而不会喧宾夺主（即不会掩盖网站在销售的内容：其内容本身）。我无法创建这样的设计。我在网上搜索可用的 Web 模板，最终选择了由 spyka Webmaster (www.spyka.net) 创建的免费 Kilo 主题。为将该模板定制到本网站，我更新了本网站理论名称和标语的标头，更改了顶部导航项，修改了侧边内容栏，调整了页脚，并对 CSS 做了一些调整。你可以从我的网站下载代码来查看最终效果。

> **提示**
> 随意使用你自己的设计，或根据喜好调整 Kilo 主题。

在屏幕右侧，如果用户未登录，我希望网站显示登录表单（图 3.7），但如果已登录，则显示一些账户管理链接（图 3.8）。如果登录用户是管理员，他们将看到一组额外的选项（图 3.9）。

网站的内容将按类别组织，同样列在右侧。非付费订阅的访客只能看到可用的内容（标题和简短描述）；付费订阅者可以查看内容本身。

![](img/4f47e47c67bd619ac73250f11c9fc7ce_78_0.png)

图 3.7

![](img/4f47e47c67bd619ac73250f11c9fc7ce_78_1.png)

图 3.8

![](img/4f47e47c67bd619ac73250f11c9fc7ce_78_2.png)

图 3.9

为了将此 HTML 设计融入网站的每个页面，我将使用一种标准技术：将模板分解为头部文件和尾部文件。每个页面将包含头部，然后显示特定于页面的内容，最后包含尾部。一旦你完成了基本模板（或多个模板）的定制，就可以开始创建各个文件了。

### 创建头部

头部需要启动 HTML 页面，包含任何必要的 CSS 和 JavaScript，并编写页面主体，直到特定于页面的内容开始的位置。

- 1. 如果尚未打开，请在文本编辑器或 IDE 中打开设计好的模板文件。

- 2. 从模板文件复制所有 HTML，直到特定于页面的内容：

```html
<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Strict//EN"
"http://www.w3.org/TR/xhtml1/DTD/xhtml1-strict.dtd">
<html xmlns="http://www.w3.org/1999/xhtml">
<head>
<meta http-equiv="Content-Type" content="text/html;
charset=utf-8" />
<title>Knowledge is Power: And It Pays to Know</title>
<link rel="stylesheet" href="css/styles.css" type="text/css" />
</head>
<body>
<div id="wrap">
<div class="header">
<!-- TITLE -->
<h1><a href="index.php">Knowledge is Power</a></h1>
<h2>and it pays to know</h2>
<!-- END TITLE -->
</div>
<div id="nav">
<ul>
<!-- MENU -->
<li class="selected"><a href="index.php"><span>Home</span></a></li>
<li><a href="about.php"><span>About</span></a></li>
<li><a href="contact.php"><span>Contact</span></a></li>
<li><a href="register.php"><span>Register</span></a></li>
<!-- END MENU -->
```

> 如果你的网站使用多个模板，只需创建多个头部和尾部文件，然后为每个特定页面包含相应的文件即可。

