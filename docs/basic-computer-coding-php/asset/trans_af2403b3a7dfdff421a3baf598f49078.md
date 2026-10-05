

# PHP 简介

PHP 也已成为生成 XML 文档、图形、Flash 动画、PDF 文件等内容的流行语言。

# 命令行脚本

PHP 可以从命令行运行脚本，就像 Perl、awk 或 Unix shell 一样。你可能使用命令行脚本执行系统管理任务，例如备份和日志解析；甚至某些 CRON 任务脚本也可以通过这种方式完成（非视觉化 PHP 任务）。

# 客户端 GUI 应用程序

使用 PHP-GTK，你可以在 PHP 中编写完整的跨平台 GUI 应用程序。然而，我们专注于第一项：使用 PHP 开发动态网页内容。PHP 运行在所有主流操作系统上，从包括 Linux、FreeBSD、Ubuntu、Debian 和 Solaris 在内的 Unix 变体到 Windows 和 Mac OS X。它可以配合所有领先的 Web 服务器，包括 Apache、Microsoft IIS 和 Netscape/iPlanet 服务器。该语言本身非常灵活。

你不限于输出 HTML 或文本文件——可以生成任何文档格式。PHP 支持生成 PDF 文件、GIF、JPEG 和 PNG 图像以及 Flash 电影。

![](img/f8aa82c4ef45031ca4eadc2bb946c87a_18_0.png)

PHP 最显著的特征之一是对数据库的广泛支持。PHP 支持所有主流数据库（包括 MySQL、PostgreSQL、Oracle、Sybase、MS-SQL、DB2 以及符合 ODBC 的数据库），甚至支持更新的 NoSQL 风格数据库，如 SQLite 和 MongoDB。通过 PHP，从数据库创建动态内容的网页非常简单。

最后，PHP 提供了一个 PHP 代码库来执行常用任务，如数据库抽象、错误处理等，使用了 PHP 扩展和应用程序库（PEAR）。PEAR 是一个用于复用 PHP 组件的框架和分发系统。你可以在此处了解更多信息。

# 1.1.2 PHP 的常见用途

- PHP 执行系统功能，即对系统上的文件进行创建、打开、读取、写入和关闭。
- PHP 可以处理表单，即从文件中收集数据、将数据保存到文件中、通过电子邮件发送数据、向用户返回数据。
- 你可以通过 PHP 在数据库中添加、删除、修改元素。
- 访问 cookie 变量并设置 cookie。
- 使用 PHP，你可以限制用户访问你网站的某些页面。
- 它可以加密数据。

# 1.1.3 PHP 的特性

五个重要的特性使得 PHP 的实用性成为可能——

- 简单性
- 效率性
- 安全性
- 灵活性
- 熟悉性

# 1.1.4 PHP 中的“Hello World”脚本

为了感受 PHP，首先从简单的 PHP 脚本开始。由于“Hello, World!” 是一个必不可少的示例，我们首先将创建一个友善的小型“Hello, World!”脚本。

如前所述，PHP 嵌入在 HTML 中。这意味着在你普通的 HTML（或者如果你追求前沿则使用 XHTML）中，你会有像这样的 PHP 语句——

```html
<head>
  <title>Hello World</title>
</head>
<body>
  <?php echo "Hello, World!";?>
</body>
</html>
```

它将产生以下结果—— Hello, World!

如果你检查上述示例的 HTML 输出，你会发现从服务器发送到 Web 浏览器的输出是纯 HTML。解释器是执行编译成机器指令的计算机程序，实际上执行工作。所有 PHP 代码必须包含在页面中最常见的特殊标记中：

```php
<?php echo "Hello, World!"; ?>

```

<?php echo "Hello, World!"; ?>
```

```html
<script language="php">
<?php echo "Hello, World!"; ?>
</script>
```

在你的教程中，从下一章我们将开始配置 PHP 环境，然后我们将挖掘所有与 PHP 相关的概念。

# 1.1.5 PHP 的历史

PHP 是一种“嵌入 HTML 的脚本语言”，主要用于动态应用程序。该定义的第一部分意味着 PHP 代码可以与 HTML 穿插，从而轻松生成动态网页。作为一种脚本语言，PHP 代码需要 PHP 处理器的存在。PHP 代码通常以文本脚本的形式运行。它是一种开源技术，运行在大多数操作系统和大多数 Web 服务器上。PHP 由 Rasmus Lerdorf 在 1994 年用 C 语言编写的，用于监控他的在线简历和个人信息。因此，PHP 最初代表“Home Page”（个人首页）。1995 年 6 月 8 日，Lerdorf 将 PHP 与了自己的 Form 结合（泛称为 PHP/FI）。两个程序员 Zeev Suraki 和 Andi Gutmans 重建了 PHP 核心，并在 1997 年发布了更新后的 PHP/FI 2。此时，该缩写正式更改为 PHP:HyperText Preprocessor（超文本预处理器）。（这是一个缩写。）

PHP 4 于 2000 年 5 月发布，带有 Zend Engine 1.0。PHP 4 的许多新特性包括面向对象编程、包含 PCRE。所有返回到页面的输出是纯 HTML。PHP 5 于 2004 年 7 月发布，提高了速度和可靠性。PHP 5 的许多新特性包括：

- 改进面向对象编程
- 集成 SQLite
- 异常处理
- SOAP 支持
- 更好的 XML 工具
- 迭代器

PHP 6 自 2006 年 10 月开始开发。最重的变化将是对 Unicode 的原生支持。不受欢迎且过时的特性（如 Magic Quotes、register_globals、safe_mode）将在 PHP 6 中消失。尽管 PHP 主要仍用于服务器端生成网页，但也可以用于执行命令行脚本或在 GTK+ 的帮助下创建图形应用程序。（94c87a_22.png）

软件是一个泛指，指的是一组数据或计算机指令，用于指示计算机如何工作，与构建系统的物理硬件相反，硬件实际上执行工作。

