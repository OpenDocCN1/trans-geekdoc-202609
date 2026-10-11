
# PHP 会话管理

## 内置会话变量和函数

5. `$_SESSION` - 一个附加到当前会话的内置数组，充当存储器。你可以在 PHP 脚本中在 `$_SESSION` 中存储任意数量的键值对，并在另一个脚本中稍后检索它们，前提是该脚本与第一个脚本共享同一个会话。

6. `session_name()` - 一个用于设置和获取当前会话名称的内置函数。

7. `session_id()` - 一个用于设置和获取当前会话 ID 的内置函数。

8. `session_destroy()` - 一个用于销毁当前会话的内置函数。当当前会话被销毁时，存储在 `$_SESSION` 中的信息将被移除。

## 会话测试脚本页面

本节提供了一个教程示例，说明如何编写多个脚本页面并利用会话概念使它们协同工作。

为了帮助我们测试会话概念，我编写了 3 个 PHP 脚本。

### 1. SessionPage1.php

```php
<?php
#  SessionPage1.php
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

### 2. SessionPage2.php

```php
<?php
#  SessionPage2.php
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

### 3. SessionPage3.php

```php
<?php
#  SessionPage3.php
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

## 运行会话测试脚本页面

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

## 不使用 Cookie 管理会话 ID

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
