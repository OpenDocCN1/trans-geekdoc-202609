
#### 会话测试脚本页面

本节提供了一个教程示例，说明如何编写多个脚本页面并利用会话概念使它们协同工作。

为了帮助我们测试会话概念，我编写了 3 个 PHP 脚本。

#### 1. SessionPage1.php

```php
<?php
#### SessionPage1.php
#- Copyright 2003 (c) HerongYang.com. All Rights Reserved.
#
   session_start();
   $quantity = 3;
   $_SESSION['quantity'] = $quantity;
   if (isset($_SESSION['count'])) {
      $count = $_SESSION['count'];
   } else {
      $count = 0;
   }
   $count++;
   $_SESSION['count'] = $count;
#
   print "<pre>\n";
   print "\nI am buying $quantity PHP books.\n";

   print "\n<a href=SessionPage2.php>Next</a>\n";
   print "\nCounter = $count\n";
   print "Session name = ".session_name()."\n";
   print "Session id = ".session_id()."\n";
#
   print "\nContents of \$_GET:\n";
   foreach ($_GET as $k => $v) {
      print "   $k = $v\n";
   }
#
   print "\nContents of \$_POST:\n";
   foreach ($_POST as $k => $v) {
      print "   $k = $v\n";
   }
#
   print "\nContents of \$_COOKIE:\n";
   foreach ($_COOKIE as $k => $v) {
      print "   $k = $v\n";
   }
   print "</pre>\n";
?>
```

#### 2. SessionPage2.php

```php
<?php
#### SessionPage2.php
#- Copyright 2003 (c) HerongYang.com. All Rights Reserved.
#
   session_start();
   $quantity = $_SESSION['quantity'];
   $price = 9.99;
   $_SESSION['price'] = $price;
   $count = $_SESSION['count'];
   $count++;
   $_SESSION['count'] = $count;
#
   print "<pre>\n";
   print "\nI am buying $quantity PHP books.\n";
   print "The unit price is $price per book.\n";
#
   print "\n<a href=SessionPage3.php>Next</a> ";
   print " <a href=SessionPage1.php>Prev</a>\n";
   print "\nCounter = $count\n";
   print "Session name = ".session_name()."\n";
   print "Session id = ".session_id()."\n";
#
   print "\nContents of \$_GET:\n";
   foreach ($_GET as $k => $v) {
      print "   $k = $v\n";
   }
#
   print "\nContents of \$_POST:\n";
   foreach ($_POST as $k => $v) {
      print "   $k = $v\n";
   }
#
   print "\nContents of \$_COOKIE:\n";
   foreach ($_COOKIE as $k => $v) {
      print "   $k = $v\n";
   }
   print "</pre>\n";
?>
```

#### 3. SessionPage3.php

```php
<?php
#### SessionPage3.php
#- Copyright 2003 (c) HerongYang.com. All Rights Reserved.
#
   session_start();
   $quantity = $_SESSION['quantity'];
   $price = $_SESSION['price'];
   $total = $quantity * $price;
   $count = $_SESSION['count'];
   $count++;
   $_SESSION['count'] = $count;
#
   print "<pre>\n";
   print "\nI am buying $quantity PHP books.\n";
   print "The unit price is $price per book.\n";
   print "The total price is $total.\n";
#
   print "\n<a href=SessionPage2.php>Prev</a>\n";
   print "\nCounter = $count\n";
   print "Session name = ".session_name()."\n";
   print "Session id = ".session_id()."\n";
#
   print "\nContents of \$_GET:\n";
   foreach ($_GET as $k => $v) {
      print "   $k = $v\n";
   }
#
   print "\nContents of \$_POST:\n";
   foreach ($_POST as $k => $v) {
      print "   $k = $v\n";
   }
#
   print "\nContents of \$_COOKIE:\n";
   foreach ($_COOKIE as $k => $v) {
      print "   $k = $v\n";
   }
   print "</pre>\n";
?>
```

#### 运行会话测试脚本页面

本节提供了一个教程示例，说明如何运行通过会话概念连接的多个脚本页面。页面输出证明了会话概念正在工作。

如果你运行 `http://localhost/SessionPage1.php`，你应该会得到：

```
I am buying 3 PHP books.

Next

Counter = 1
Session name = PHPSESSID
Session id = o9oipjgc4r3fqmfk8mlldl5sl5

Contents of $_GET:

Contents of $_POST:

Contents of $_COOKIE:
```

如果你在第一页点击“Next”，你将运行 `http://localhost/SessionPage2.php`，并应该得到：

```
I am buying 3 PHP books.
The unit price is 9.99 per book.

Next  Prev

Counter = 2
Session name = PHPSESSID
Session id = o9oipjgc4r3fqmfk8mlldl5sl5

Contents of $_GET:

Contents of $_POST:

Contents of $_COOKIE:
   PHPSESSID = o9oipjgc4r3fqmfk8mlldl5sl5
```

如果你在第二页点击“Next”，你将运行 `http://localhost/SessionPage3.php`，并应该得到：

```
I am buying 3 PHP books.
The unit price is 9.99 per book.
The total price is 29.97.

Prev

Counter = 3
Session name = PHPSESSID
Session id = o9oipjgc4r3fqmfk8mlldl5sl5

Contents of $_GET:

Contents of $_POST:

Contents of $_COOKIE:
   PHPSESSID = o9oipjgc4r3fqmfk8mlldl5sl5
```

正如你所见，会话概念正在工作。此处应注意几点：

*   数据可以在一个页面中存入会话，并在另一个页面中检索。例如，数量在第一页存入会话，并在第二页和第三页中检索。
*   会话名称是在 `php.ini` 文件中定义的字符串。
*   会话 ID 由 PHP 创建，并作为 Cookie 进行管理。
*   你可以使用会话对象来管理特定会话中访问的页面计数。但你不能使用会话对象来管理所有会话中访问的页面计数。要跨会话管理信息，你需要一个比会话更高层级的概念。例如，应用程序和服务器概念就高于会话概念。

#### 不使用 Cookie 管理会话 ID

本节描述了什么是数组——键和值的有序对。如果使用顺序整数键，数组就是一个简单的索引列表。如果使用字符串键，数组就是一个映射。

如果你不想使用 Cookie 技术来管理会话 ID，可以尝试使用 URL 透明参数来管理会话 ID。以下是我测试 URL 透明参数的步骤：

1. 打开并编辑配置文件 `\php\php.ini`：

```
session.use_cookies = 0
session.use_trans_sid = 1
```

2. 重新运行 `http://localhost/SessionPage1.php`，我得到了：

```
I am buying 3 PHP books.

Next

Counter = 1
Session name = PHPSESSID
Session id = mg04r204ctuloo2uegmih14ri5
Session module = files

Contents of $_GET:

Contents of $_POST:

Contents of $_COOKIE:
```

3. 在第一页点击“Next”，浏览器上的 URL 地址变为：`http://localhost/SessionPage2.php?PHPSESSID=mg04r204ctuloo2uegmih14ri5`。浏览器显示：

```
I am buying 3 PHP books.
The unit price is 9.99 per book.

Next  Prev

Counter = 2
Session name = PHPSESSID
Session id = mg04r204ctuloo2uegmih14ri5

Contents of $_GET:
   PHPSESSID = mg04r204ctuloo2uegmih14ri5

Contents of $_POST:

Contents of $_COOKIE:
```

4. 在第二页点击“Next”，浏览器上的 URL 地址变为：`http://localhost/SessionPage3.php?PHPSESSID=mg04r204ctuloo2uegmih14ri5`。浏览器显示：

```
I am buying 3 PHP books.
The unit price is 9.99 per book.
The total price is 29.97.

Prev

Counter = 3
Session name = PHPSESSID
Session id = mg04r204ctuloo2uegmih14ri5

Contents of $_GET:
   PHPSESSID = mg04r204ctuloo2uegmih14ri5

Contents of $_POST:

Contents of $_COOKIE:
```

输出显示会话概念仍然正常工作。但这里发生了几件有趣的事情：

*   如果你要求 PHP 使用透明会话 ID 管理，它将修改所有链接以将会话 ID 作为 URL 地址的一部分包含在内。查看浏览器中第一页的源代码，你应该会看到“Next”按钮的 URL 被修改为 `href=SessionPage2.php?PHPSESSID=mg04r204ctuloo2uegmih14ri5`。
*   输出显示现在会话 ID 存储在 `$_GET` 数组中。
*   由于会话 ID 存储在浏览器的 URL 字段中，每个人都能看到它。因此这比将会话 ID 存储在 Cookie 中**安全性更低**。

PHP Tutorials - Herong's Tutorial Examples

∟Creating and Managing Sessions in PHP Scripts

∟Where Is Session Data Stored

本节提供了一个教程示例，说明如何找出 PHP 引擎存储会话数据的位置。`session.save_path` 设置指定了会话数据的目录名称。

PHP 将会话数据存储在哪里？答案并不那么显而易见。

由于我是在 CGI 模式下运行 PHP 引擎，PHP 脚本页面是以 PHP 可执行程序的单独实例运行的。因此没有简单的方法将会话数据存储在内存中并在不同的 PHP 脚本页面之间共享。如果不存储在内存中，会话数据可以存储在硬盘上并在 PHP 页面之间共享。让我们看看能否找到会话数据在硬盘上的存储位置。

首先再次运行 `http://localhost/SessionPage1.php`：

```
I am buying 3 PHP books.

Next

Counter = 1
Session name = PHPSESSID
Session id = mg04r204ctuloo2uegmih14ri5
Session module = files

Contents of $_GET:

Contents of $_POST:

Contents of $_COOKIE:
```

然后使用 Windows 查找工具搜索包含 "mg04r204ctuloo2uegmih14ri5" 的文件名。不出所料，你应该会得到 `\tmp\sess_mg04r204ctuloo2uegmih14ri5`。在文本编辑器中打开此文件，你应该会看到：

```
quantity|i:3;count|i:1;
```

文件格式非常简单，会话数据以明文形式存储，以“;”作为分隔符。如果你想更改会话数据的存储位置，可以修改 `\php\php.ini` 中的 `session.save_path` 设置。例如：

```
session.save_path = "\herong\temp"
```

PHP Tutorials - Herong's Tutorial Examples

∟Sending and Receiving Cookies in PHP Scripts

本章提供了关于 Cookie 的教程示例和注释。主题包括理解 Cookie 概念；使用 `setcookie()` 函数发送 Cookie；使用 `$_COOKIE` 数组接收 Cookie；启用输出缓冲；创建持久 Cookie；指定 Cookie 域和路径。

> What Is a Cookie
>
> Sending and Receiving Cookies
>
> Sending and Receiving Cookies - Example
>
> ob_start() - Output Buffering Function
>
> Persistent Cookies Saved on Hard Disk
>
> Other Cookie Properties - Domain and Path

要点：

*   `setcookie()` 必须在向 HTTP 响应输出任何内容**之前**调用。主要原因是 PHP 默认不缓冲 HTTP 响应。但你可以通过使用 `ob_start()` 函数来改变此行为。
*   持久 Cookie 存储在浏览器本地机器上的 Cookie 文件中。
*   持久 Cookie 可以拥有一个以自纪元以来的秒数表示的过期时间。
*   Web 浏览器仅在域和路径均与请求的域和路径匹配时才会发回 Cookie。
*   要使 Cookie 对顶级域的所有子域可用，请将 domain 属性设置为顶级域名。

PHP Tutorials - Herong's Tutorial Examples

∟Sending and Receiving Cookies in PHP Scripts

∟What Is a Cookie

本节描述什么是 Cookie——一段由 Web 服务器发送给浏览器的信息。服务器期望浏览器将所有 Cookie 发回服务器。

#### What Is a Cookie?

Cookie 是一段由 Web 服务器发送给 Web 浏览器的信息，由浏览器保存，稍后再发回服务器。Cookie 在 HTTP 头部中传输。

Cookie 从服务器移动到浏览器，再回到服务器，如下图所示：
