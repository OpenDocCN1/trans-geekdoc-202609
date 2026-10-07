
对于旧版本的 PHP，设置时区并不重要；如果你没有指定时区，PHP 引擎会尝试通过查询运行它的服务器来确定。然而，这个过程在某种程度上不可靠，并且不再被采用。因此，从 PHP 5.3 开始，如果你在没有先配置时区的情况下尝试使用 PHP 的任何日期相关功能，引擎将符合警告信息。

幸运的是，在 PHP 中设置时区相对简单。要做到这一点，请遵循以下步骤：

- 1. 首先查看时区是否已经设置。在你创建的 `testing.php` 脚本生成的页面上，找到 `date.timezone` 条目（它可能在页面的中间位置）。如果 `Master Value` 列没有值或时区错误，你需要设置你的时区，请继续第 2 步。但是，如果该列包含你服务器的正确时区（例如 `America/Los_Angeles`），则 PHP 的时区已设置正确，你可以跳过这些后续步骤。
- 2. 在 `testing.php` 页面顶部查找 `Loaded Configuration File` 条目。这是用于配置你的 PHP 引擎的 `php.ini` 文件路径。
- 3. 使用文本编辑器打开此文件，例如记事本（Windows）、TextEdit（Mac）或 Text Editor（Ubuntu）。

你可能需要 root（管理员）权限才能访问此文件。如果你没有管理员权限，请要求你的服务器管理员为你设置时区。

- 4. 在文件中搜索此行代码：

`;date.timezone =`

如果由于某些原因这不在你的 `php.ini` 文件中，只需添加它即可。

- 5. 删除行首的分号，并在等号后的末尾添加你服务器的时区。在 http://www.php.net/timezones 可以在文件中找到你的时区。例如，如果你的服务器位于洛杉矶，你会将该行更改为：

`date.timezone = America/Los_Angeles`

- 6. 保存文件并退出编辑器。
- 7. 使用适用于你安装的方法重启 Apache。例如，在 Ubuntu 上，使用本章前面介绍的系统管理服务（System Administration Services）；或者在 Windows 上，从 WampsServer 图标选择“所有服务”；在 Mac 上，运行 `/Applications/MAMP/MAMP` 应用程序并点击“Start Servers”，然后再次点击“Start Servers”。
- 8. 为了测试设置是否生效，重新加载 `testing.php` 脚本并查找 `date.timezone` 条目。它现在应该显示你在第 5 步中设置的时区，作为页面上方 `Default timezone` 条目。大功告成！

如果你（不想）编辑你的 `php.ini` 文件，你还有其他方法来设置时区：

- 在你 站的文档根目录下创建一个 `.htaccess` 文件，并添加一条指令来设置时区：

```
php_value date.timezone America/Los_Angeles
```

- 或者，为了设置你创建的每个 PHP 脚本的开头，添加以下行代码：

```
date_default_timezone_set( "America/Los_Angeles" );
```

你可以在附 B 中找到更多关于配置 PHP 的信息，包括 `php.ini` 文件和 `.htaccess` 文件。

## 运行 PHP 的其他方法

本章专注于在计算机上启动 PHP 的最简单方法。你已经查看了 Ubuntu 上的 Apache、PHP 和 MySQL 软件包，在 Windows 上使用 WampsServer 安装完整的 Apache/PHP/MySQL 设置，以及在 Mac 上使用 MAMP 进行相同的操作。

你还可以其他几种方式运行 PHP。接下来的章节将简要介绍它们。

## 第 2 章：你的第一个 PHP 脚本

### 使用其他 Web 服务器运行 PHP

正如本章前面提到的，你并不局限于使用 Apache 运行 PHP。在 Windows 上也可以与微软的 Internet 信息服务器 (IIS) 运行，还可以与 Zeus 等其他 Web 服务器运行。

一种常见的配置是在 Windows 上将 PHP 与 IIS 使用。这带给你无需安装 Apache 的优势，而且你可以在同一个 Web 服务器上运行 ASP.NET 等其他微软技术。你可以将 PHP 安装为 ISAPI 模块（这意味着它可以与 IIS 集成），或者作为独立的 CGI 二进制文件。对于更高性能，推荐使用 ISAPI 方法。

本书没有介绍安装过程的细节，但你可以在 www.php.net 网站上找到如何让 PHP 在 IIS 上工作：

```
http://www.php.net/manual/en/install.windows.iis.php
```

### 自己编译 PHP

你在本章早期学到的安装技术适用于 PHP 的预编译二进制文件。这有助于保持简单性，因为处理二进制文件（特别是在 Windows 计算机上）比从源代码编译 PHP 要容易。

然而，从源码编译 PHP 很有用：

- 你想在 PHP 发布二进制包之前尝试最新版本（作为快照）
- 你想深入底层并调优 PHP

PHP 各版本的 二进制文件是可用的，这省去了你从头编译的麻烦。编译 PHP 的基本步骤：

- 1. 在你的计算机上安装 C 编译器（Ubuntu 安装相关程序包；Windows 安装 Visual C++；Mac 安装 Xcode。）
- 2. 从 http://www.php.net/downloads 下载源码或从 http://snapshots.php.net 下载最新快照并解压文件。
- 3. 在发行目录下运行 `configure` 脚本以设置各种编译选项。这允许你指定将 PHP 编译为 Apache 模块，并包含特定的库。
- 4. 运行 `make` 来编译 PHP。
- 5. 运行 `make install` 安装二进制文件。

这是一个非常简化的概述，在实践中你通常需要安装其他库和应用程序进行 PHP。你可以在 http://www.php.net/manual/en/install.php 找到为 UNIX、Windows 和 Mac OS 系统编译 PHP 的详细信息。

### 远程运行 PHP

如果你觉得在自己的计算机上安装 PHP 有些困难，你始终可以使用网站托管账户创建并测试 PHP 脚本（假设该账户支持 PHP）。如果支持 ssh，你可以使用 ssh 连接到服务器并在命令行中开发和测试 PHP 脚本。

要通过 ssh 访问服务器，你需要一个 ssh 客户端（Ubuntu 安装 ssh 包；Windows 尝试 putty (http://www.putty.org/)）。Mac OS 预装了 ssh 客户端。

如果你的托管账户支持 PHP 但不支持 ssh，你可以在计算机上使用文本编辑器编写 PHP 脚本，然后通过 FTP 将上传到 Web 服务器进行测试。这可能是一个繁琐的过程，因为你每次想测试更改都要刷新脚本，但比没有要好！

### 创建你的第一个脚本

现在你已经成功在计算机上安装了 PHP，是时候编写你的第一个正式 PHP 脚本了。此脚本将执行非常简单的操作：在浏览器窗口中显示文本“Hello, world!”。一旦该脚本运行，你就可以学习如何以各种方式增强它。

要创建这个简单的脚本，打开你的文本编辑器并输入以下内容：

```php
<?php
echo "Hello, world!";
?>
```

### 第二2章：你的第一个 PHP 脚本

这个脚本非常简单，但让我们逐行分析，以探索 PHP 的一些特性。

第一行告诉 PHP 引擎后面将会有一些 PHP 代码：

```php
<?php
```

为什么你需要这一行呢？这是因为 PHP 可以嵌入到 HTML Web 页面中。当 PHP 引擎开始处理页面时，它会假设自己处理的是普通的旧 HTML，除非另有说明。通过使用 PHP 分隔符 `<?php`，你是在告诉 PHP 引擎将 `<?php` 之后跟的任何内容都视为 PHP 代码，而不是 HTML。

下一行显示消息“Hello, world!”：

```php
echo "Hello, world!";
```

PHP 的 `echo()` 语句接收一段文本——在本例中为 "Hello, world!"——并将其作为 页面的一部分发送到浏览器。浏览器随后向访问者显示 "Hello, world!"。该行末尾的分号告诉 PHP 你已经到达了语句的结束，它应该寻找下一个语句（或 PHP 代码的结束）。

`echo()` 并不非要给一段文本；它可以显示任何可以显示的内容，如数字或表达式的结果。你将在下一章中了解到更多关于数据类型和表达式的知识。

`echo()` 的替代方案是 `print()` 语句，它的工作方式完全相同，只是会返回一个值（true）。通常情况下，如果你愿意，可以在代码中使用 `print()` 代替 `echo()`。

你脚本的最后一行告诉 PHP 引擎它已到达当前 PHP 代码段的结束，接后的行（如果有的话）再次包含纯 HTML：

```php
?>
```

### 在 HTML 中嵌入 PHP

正如你所察觉到的，PHP 的优点之一是你可以将 PHP 代码嵌入到 HTML 中。事实上，你编写的任何 .php 脚本默认都会被视为 HTML 页面。如果页面包含 `<?php ... ?>` 标签，PHP 引擎将把文件内容原封不动地发送给浏览器。

### 试一试：创建一个样式页面

你可以使用此功能，通过 CSS 表格添加适当的 HTML 头部和页脚，来让你的“Hello, world!”变得更漂亮。在编辑以下代码并将其保存为文档根文件夹下的 `hello_pretty.php` 后：

```html
<!DOCTYPE html PUBLIC "//W3//DTD HTML 1.0 Strict//EN"
<html xmlns="http://www.w3.org/TR/html4/DTD/html4-strict.dtd" xml:lang="en" lang="en">
<head>
  <title>Hello</title>
<link rel="stylesheet" type="text/css" href="common.css" />
</head>
```

#### 第一部分：上手运行 PHP

```html
<body>
<h1><?php echo "Hello, world!"; ?></h1>
</body>
</html>
```

接下来，输入以下 CSS 代码并将其保存为同一文件夹下的 `common.css`：

```css
/* 页面主体 */
body { font-family: Arial, Helvetica, sans-serif; }

/* 定义列表 */
dl { width: 100%; margin: 2em; padding: 0; clear: both; overflow: auto; }
dt { width: 30%; float: left; margin: 0; padding: 5.9px 5px; }
dt { border-top: 1px solid #DDDBB7; font-weight: bold; overflow: auto; clear; }
dd { width: 60%; float: left; margin: 0; padding: 6px 5px 0px; border-top: 1px solid #DDDBB7; overflow: auto; }

/* 标题 */
h1 { font-weight: bold; margin: 30px 14px; color: #666; font-size: 1.5em; }
h2 { font-weight: bold; margin: 30px 12px; color: #666; font-size: 1.3em; }
h3 { font-weight: normal; margin: 30px 12px; color: #666; font-size: 1.2em; }
h4 { font-weight: bold; margin: 25px 12px; color: #666; font-size: 1.1em; }
h5 { font-weight: bold; margin: 25px 12px; color: #666; font-size: 0.9em; }

/* 表单 */
label { display: block; float: left; clear: both; text-align: right; margin: 0.6em 5px 0; width: 40%; }
input, select, textarea { float: right; margin: 1em 0; width: 57%; border: 1px solid #666; }
input[type=radio], input[type=checkbox], input[type=submit], input[type=reset], input[type=image] { width: auto; }
```

在浏览器的地址栏中输入 `http://localhost/hello_pretty.php` 来运行你的 PHP 脚本。你会看到一个更有样式的页面，如图 2-13 所示。

![](img/ede05b7b7796b82cbd9a513122fb183_63_0.png)

图 2-13

### 第二章：你的 PHP 脚本 如何工作

这个示例展示了如何在 HTML 页面中嵌入 PHP。正如你所察觉到的，PHP 的优点之一是你可以将 PHP 代码嵌入到 HTML 中。事实上，你编写的任何 .php 脚本默认都会被视为 HTML 页面。如果页面包含 `<?php ... ?>` 标签，PHP 引擎将把文件内容原封不动地发送给浏览器。首先，一个 DOCTYPE 标签声明该页面是 HTML 1.0 严格版：

```html
<!DOCTYPE html PUBLIC "//W3//DTD HTML 1.0 Strict//EN"
<html xmlns="http://www.w3.org/TR/html4/DTD/html4-strict.dtd" xml:lang="en" lang="en">
```

接下来，`head` 元素包含了页面标题“Hello”，并链接到 CSS 表格：

```html
<head>
<title>Hello</title>
<link rel="stylesheet" type="text/css" href="common.css" />
</head>
```

最后，`body` 元素包含了 `h1`（标题），使用了 PHP 代码输出“Hello, world!”

```html
<body>
<h1><?php echo "Hello, world!"; ?></h1>
</body>
</html>
```

注意 `<?php ?>` 标签包裹的 PHP 代码——`echo "Hello, world!";`——被替换成了静态文本。

`echo()` 语句接收一段文本——在本例中为 "Hello, world!"——并将其作为 页面的一部分发送到浏览器。浏览器随后向访问者显示 "Hello, world!"。该行末尾的分号告诉 PHP 你已经到达了语句的结束，它应该寻找下一个语句（或 PHP 代码的结束）。

`echo()` 并不非要给一段文本；它可以显示任何可以显示的内容，如数字或表达式的结果。你将在下一章中了解到更多关于数据类型和表达式的知识。

`echo()` 的替代方案是 `print()` 语句，它的工作方式完全相同，只是会返回一个值（true）。通常情况下，如果你愿意，可以在代码中使用 `print()` 代替 `echo()`。

你脚本的最后一行告诉 PHP 引擎它已到达当前 PHP 代码段的结束，接后的行（如果有的话）再次包含纯 HTML：

```php
?>
```

#### 第一部分：上手运行 PHP：增强脚本

“Hello, world!” 示例展示了如何编写一个 PHP 脚本。正如你所察觉到的，PHP 的优点之一是你可以将 PHP 代码嵌入到 HTML 中。事实上，你编写的任何 .php 脚本默认都会被视为 HTML 页面。如果页面包含 `<?php ... ?>` 标签，PHP 引擎将把文件内容原封不动地发送给浏览器。通过使用 `<?php ?>` 标签，你从静态页面转变为动态页面。

这里的 `common.css` 样式表：
