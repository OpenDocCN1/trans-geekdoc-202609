

## 31. PHP – PHP for PERL Developers 183
- 相似点
- 差异点

## PART 3: 函数参考 185

## 32. PHP – 函数参考 186

## Part 1: 学习 PHP

### 1. PHP – 简介

PHP 最初是一个小型开源项目，随着越来越多的人发现它有多有用而不断发展。Rasmus Lerdorf 在 1994 年推出了第一个版本的 PHP。

- PHP 是递归缩写词，代表 "PHP: Hypertext Preprocessor"。
- PHP 是一种服务器端脚本语言，嵌入于 HTML 中。它用于管理动态内容、数据库、会话跟踪，甚至构建整个电子商务网站。
- 它与多种流行数据库集成，包括 MySQL、PostgreSQL、Oracle、Sybase、Informix 和 Microsoft SQL Server。
- PHP 的执行速度非常快，尤其是在 Unix 侧作为 Apache 模块编译时。MySQL 服务器启动后，即使是非常复杂的查询和巨大的结果集，也能在创纪录的时间内执行。
- PHP 支持大量主要协议，如 POP3、IMAP 和 LDAP。PHP4 增加了对 Java 和分布式对象架构（COM 和 CORBA）的支持，使多层开发首次成为可能。
- PHP 很宽容：PHP 语言尽可能地宽容。
- PHP 语法类似于 C 语言。

#### PHP 的常见用途

PHP 执行系统函数，即从系统上的文件中，它可以创建、打开、读取、写入和关闭文件。PHP 的其他用途包括：

- PHP 可以处理表单，即从文件中收集数据，将数据保存到文件，通过电子邮件发送数据，将数据返回给用户。
- 你可以通过 PHP 在数据库中添加、删除、修改元素。
- 访问 Cookie 变量并设置 Cookie。
- 使用 PHP，你可以限制用户访问网站的某些页面。
- 它可以加密数据。

#### PHP 的特性

五个重要特性使 PHP 的实用性成为可能：

- 简单性
- 效率
- 安全性
- 灵活性
- 熟悉度

#### PHP 中的 "Hello World" 脚本

要初步了解 PHP，首先从简单的 PHP 脚本开始。由于 "Hello, World!" 是一个基本示例，我们将先创建一个友好的小型 "Hello, World!" 脚本。

如前所述，PHP 嵌入于 HTML。这意味着在你的普通 HTML（或如果你追求前沿技术的 XHTML）中，你会看到这样的 PHP 语句：

```html
<html>
<head>
<title>Hello World</title>
<body>
<?php echo "Hello, World!";?>
</body>
</html>
```

它将产生以下结果：

```
Hello, World!
```

如果你检查上述示例的 HTML 输出，你会注意到 PHP 代码不存在于从服务器发送到 Web 浏览器的文件中。网页中所有的 PHP 都会被处理并从页面中剔除；从 Web 服务器返回到客户端的只有纯 HTML 输出。

所有 PHP 代码都必须包含在 PHP 解析器识别的三种特殊标记标签之一中。

```
<?php PHP code goes here ?>
<?   PHP code goes here ?>
<script language="php"> PHP code goes here </script>
```

最常用的标签是 <?php...?>，我们在教程中也将使用相同的标签。

从下一章开始，我们将在你的机器上进行 PHP 环境设置，然后我们将探讨与 PHP 相关的几乎所有概念，让你熟悉 PHP 语言。

### 2. PHP – 环境设置

为了开发和运行 PHP 网页，你的计算机系统需要安装三个关键组件。

**Web 服务器** - PHP 可以与几乎所有 **Web 服务器** 软件一起工作，包括 Microsoft 的 Internet Information Server (IIS)，但最常用的是免费可用的 Apache 服务器。在此免费下载 Apache：http://httpd.apache.org/download.cgi

**数据库** - PHP 可以与几乎所有数据库软件一起工作，包括 Oracle 和 Sybase，但最常用的是免费可用的 MySQL 数据库。在此免费下载 MySQL：http://www.mysql.com/downloads/index.html

**PHP 解析器** - 为了处理 PHP 脚本指令，必须安装一个解析器以生成可以发送到 **Web 浏览器** 的 HTML 输出。本教程将指导你如何在计算机上安装 PHP 解析器。

#### PHP 解析器安装

在继续之前，重要的是要确保你的机器上已正确设置环境，以便使用 PHP 开发 Web 程序。

将以下地址输入到浏览器的地址框中。

```
http://127.0.0.1/info.php
```

如果这显示一个显示 PHP 安装相关信息的页面，那么意味着你已正确安装 PHP 和 Web 服务器。否则，你需要按照给定的过程在计算机上安装 PHP。

本节将指导你在以下四个平台上安装和配置 PHP：

- 在带有 Apache 的 Linux 或 Unix 上安装 PHP
- 在带有 Apache 的 Mac OS X 上安装 PHP
- 在带有 IIS 的 Windows NT/2000/XP 上安装 PHP
- 在带有 Apache 的 Windows NT/2000/XP 上安装 PHP

#### 在带有 Apache 的 Linux 或 Unix 上安装 PHP

如果你计划在 Linux 或任何其他 Unix 变体上安装 PHP，那么以下是先决条件列表：

- PHP 源代码分发 http://www.php.net/downloads.php 最新的 Apache 源代码分发 http://httpd.apache.org/download.cgi
- 一个正常工作的 PHP 支持的数据库，如果你打算使用一个（例如 MySQL、Oracle 等）
- PHP 必须连接的任何其他受支持的软件（邮件服务器、BCMath 包、JDK 等等）
- ANSI C 编译器
- GNU make 实用程序 - 你可以在此免费下载：http://www.gnu.org/software/make

现在，以下是在你的 Linux 或 Unix 机器上安装 Apache 和 PHP5 的步骤。如果你的 PHP 或 Apache 版本不同，请相应注意。

- 如果你还没有这样做，请解压并解包你的 Apache 源代码分发。除非你有理由这样做，否则 /usr/local 是标准位置。
```
gunzip -c apache_1.3.x.tar.gz
tar -xvf apache_1.3.x.tar
```
- 如下构建 Apache 服务器
```
cd apache_1.3.x
./configure --prefix=/usr/local/apache --enable-so
make
make install
```
- 解压并解包你的 PHP 源代码分发。除非你有理由这样做，否则 /usr/local 是标准位置。
```
gunzip -c php-5.x.tar.gz
tar -xvf php-5.x.tar
cd php-5.x
```
- 配置并构建你的 PHP，假设你使用的是 MySQL 数据库。
```
./configure --with-apxs=/usr/sbin/apxs \
--with-mysql=/usr/bin/mysql
make
make install
```
- 安装 php.ini 文件。编辑此文件以获取配置指令：
```
cd ../php-5.x
cp php.ini-dist /usr/local/lib/php.ini
```
- 告诉你的 Apache 服务器你希望从哪里提供文件，以及你希望使用哪些扩展名来识别 PHP 文件。**.php** 是标准，但你可以使用 .html、.phtml 或任何你想要的扩展名。
  - 转到你的 HTTP 配置文件（/usr/local/apache/conf 或你的任何路径）
  - 用文本编辑器打开 httpd.conf。搜索单词 DocumentRoot（应该出现两次），并将两个路径都更改为你希望提供文件的目录（在我们的例子中，/home/httpd）。我们建议使用主目录而不是默认的 /usr/local/apache/htdocs，因为它更安全，但不必位于主目录中。你将把所有 PHP 文件保存在此目录中。
- 添加至少一个 PHP 扩展指令，如以下代码的第一行所示。在第二行中，我们还添加了第二个处理程序，以将所有 HTML 文件解析为 PHP
```
AddType application/x-httpd-php .php
AddType application/x-httpd-php .html
```
- 重新启动你的服务器。每次更改 HTTP 配置或 php.ini 文件时，你都必须停止并重新启动服务器。
```
cd ../bin
./apachectl start
```
- 将文档根目录权限设置为全局可执行。目录中的实际 PHP 文件只需全局可读（644）。如果必要，将下面的 /home/httpd 替换为你的文档根目录：
```
chmod 755 /home/httpd/html/php
```
- 打开文本编辑器。键入：<?php phpinfo(); ?>。将此文件保存在 Web 服务器的文档根目录中，文件名为 info.php。
- 启动任何 Web 浏览器并浏览该文件。你必须始终使用 HTTP 请求（http://www.testdomain.com/info.php 或 http://localhost/info.php 或 http://127.0.0.1/info.php），而不是文件名（/home/httpd/info.php），才能正确解析该文件。

你应该看到一个关于新 PHP 安装的长信息表，恭喜你！

#### 在带有 Apache 的 Mac OS X 上安装 PHP

Mac 用户可以选择二进制安装或源代码安装。事实上，你的 OS X 可能预装了 Apache 和 PHP。这可能是一个相当旧的构建版本，并且可能缺少许多不常用的扩展。

但是，如果你只想在笔记本电脑上快速设置 Apache + PHP + MySQL/PostgreSQL，这无疑是最简单的方法。你只需要编辑 Apache 配置文件并打开 Web 服务器。

所以，请按照以下步骤操作：

- 以 root 身份在文本编辑器中打开 Apache 配置文件。
```
sudo open -a TextEdit /etc/httpd/httpd.conf
```

