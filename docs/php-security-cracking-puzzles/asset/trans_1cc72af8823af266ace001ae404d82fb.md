

## I.4.12. 在数据库中保存图像

在在上一个任务中，建议你将 MP3 文件保存到数据库中。现在有一项更重要的存储任务——在数据库中保存图像。与之前的脚本不同，有必要对图像的存储进行组织，例如每页显示三张图像，而不是指向它们的链接（图 I.4.13）。图像不应保存存在服务器的临时文件中。相反，它必须直接从数据库传输到客户端。

![](img/a893312ec68b8170fe567f785e95c06e_56_0.png)

图 I.4.13. 从数据库下载图像

## I.4.13. 从数据库转储文件中下载数据

在将数据从一台服务器移动到另一台服务器时，通常会使用所谓的数据库转储（database dumps）。数据库转储是包含顺序 SQL 指令的文本文件，执行这些指令后，可以让你在每个 SQL 服务器上重建数据库（列表 I.4.7）。

> 注意：在列表 I.4.7 中所示转储文件可以在随附光盘的 /scripts/4/catalog.sql 文件中找到。

## 列表 I.4.7. 数据库转储

```
CREATE TABLE catalogs (\
id_catalog int(11) NOT NULL auto_increment,
name tinytext NOT NULL,
PRIMARY KEY (id_catalog),
FULLTEXT KEY name (name)
);
INSERT INTO catalogs VALUES (1, 'Processors');
INSERT INTO catalogs VALUES (2, 'Motherboards');
INSERT INTO catalogs VALUES (3, 'Video adapters');
INSERT INTO catalogs VALUES (4, 'Hard disks');
INSERT INTO catalogs VALUES (5, 'RAM');
```

PHP 语言的 MySQL 应用程序接口包含了 `mysql_query()` 函数，它允许你只执行一个查询。编写一个脚本，以确保从数据库转储文件中执行多个 SQL 查询。

## 第 1.5 章：会话（Sessions）与 Cookie（Cookies）

![](img/a893312ec68b8170fe567f785e95c06e_58_0.png)

构成 Web 基础的 HTTP 不是一种面向会话的协议。这意味着 Web 服务器无法确定客户端之前是否访问过服务器或访问过特定页面。网站上的任何图像或内容都可以在不下载其他图像或内容的情况下被下载。因此，如果用户已被授权访问一个页面，他或她必须被授权访问另一个页面。为了实现这一点，用户必须再次提供密码。这种情况对于大型应用程序来说是不方便的。因此，引入了 cookies 和 sessions。

Cookies 是存储在客户端计算机上的小型文本文件。当用户尝试访问安装了该 cookie 的服务器时，客户端浏览器会发送一个 HTTP 请求头，根据该请求头，服务器确定它之前安装过该 cookie。Cookie 文件存储变量名以及 Cookie 的有效期。这个有效期可能从几秒到几年不等。会话 Cookie（session cookie）存储在浏览器的内存中，而不是客户端的硬盘。

会话（Sessions）也是小型文本文件；但它们存储在服务器上。只有唯一的 SID 被发送给客户端。因此，数据永远不会离开服务器，服务器仅与客户端交换 SID。SID 的有效性受浏览器运行时间或服务器设置的。

## 第一部分：谜题

会话和 Cookie 在构建 Web 应用中起着重要作用。它们经常被用作攻击的目标，也被用作防御攻击的工具。

## I.5.1. 在线用户

在许多 Web 应用中（如聊天、论坛和电子商务网站），有必要跟踪当前活跃的用户以及他们离开网站的时间。这种技术对于控制网站的受保护区域也可能有用。例如，如果只有两个用户可以访问受保护区域，但你注意到第三个用户在场，这将允许你防止渗透，或至少将后果降至最低。

假设用户授权已在网站上实现，并且用户名注册在名为 `$_SESSION['user']` 的超全局数组中。如果用户不是授权用户，系统将显示“Anonymous”（匿名）而不是用户名。

## I.5.2. 自定义会话机制

实现一种自定义会话机制，根据该机制，用户名将存储在 MySQL 数据库而不是文件中。

![](img/a893312ec68b8170fe567f785e95c06e_59_0.png)

为了解决这个问题，使用 `session_set_save_handler()` 函数是非常方便的，它允许你注册自定义的会话处理函数。

## I.5.3. 使用会话保护 HTML 表单

假设在 index.php 文件中有一个 HTML 授权表单。该文件的代码如列表 I.5.1。

- I.5.1. 授权系统组成部分的 HTML 表单代码

```html
<table>
<form action=handler.php>
```

## 第 I.5 章：会话与 Cookie

```html
<form action=handler.php method="post">
<tr>
<td>用户名：</td>
<td><input type="text" name="name"></td>
</tr>
<tr>
<td>密码：</td>
<td><input type="password" name="pass"></td>
</tr>
<tr>
&nbsp;</td>
<td><input type="submit" value="登录"></td>
</tr>
</form>
</table>
```

如列表 I.5.1 所示，handler.php 接收数据。会话通过这种在 handler.php 中处理。

## 列表 I.5.2. handler.php

```php
<?php
session_start();
if ($_POST['name'] == 'admin' && $_POST['pass'] == 'admin') {
    $_SESSION['user'] = 'admin';
    echo "登录成功";
} else {
    echo "登录失败";
}
?>
```

## I.5.4. 客户端上的 Cookie 状态

用户经常在浏览器中禁用 Cookie。为了让 Web 应用正常工作，必须在客户端上启用 Cookie。

## I.5.5. 伪造 Cookie

假设有一个启用 Cookie 的脚本。通过该脚本，将 Cookie 设置为管理员，然后是编辑，最后是用户。

## 列表 I.5.3. 使用 Cookie

```php
<?php
setcookie("user", "admin", time() + 3600);
if (isset($_COOKIE['user'])) {
    echo "欢迎，" . $_COOKIE['user'];
}
?>
```

列表 I.5.3 所示的脚本可以在随附光盘的 /scripts/5/5.php 中找到。

![](img/a893312ec68b8170fe567f785e95c06e_61_0.png)

## I.5.6. 绕过会话保护的 HTML 表单

在 I.5.3 节中，你需要开发一个受会话保护的 HTML 表单，防止被自动填充。这种保护只能通过使用一个接收服务器 Cookie 并将其发送服务器的脚本来绕过。换句话之，这种脚本模拟了浏览器的操作。现在，创建一个实现这种行为的脚本。

## I.5.7. 跨站脚本

在 I.3.20 节中，建议你开发一个用户认证系统，将注册用户的信息记录在名为 text.txt 的文件中（列表 I.5.4）。该文件中的每行都对应一个用户，并按以下格式出现：

```
用户名::密码::邮箱::URL
```

用户名、密码、邮箱地址和主页之间用双号（::）隔开。

![](img/a893312ec68b8170fe567f785e95c06e_62_1.png)

text.txt 文件和注册新用户的脚本 (1.php) 可以在光盘上的 /scripts/5/5.7 目录下找到。

## 列表 I.5.4. text.txt 文件

```
igor::1234::igor@mail.ru::http://www.softtime.ru
cheops::dwert::cheops@mail.ru::http://www.softtime.ru
wet::gordon:::
```

