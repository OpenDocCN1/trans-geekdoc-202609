

# 例如，如果我想在运行时环境中设置默认时区，我可以编辑 php.ini 并更改 "date.timezone" 设置：

```
>edit \php\php.ini

; 定义日期函数使用的默认时区
date.timezone = Europe/Paris
```

现在 PHP 引擎将以 Europe/Paris 作为默认时区运行。

## [PHP 教程 - Herong 的教程示例](#part0001.xhtml)

### [PHP 7.3 简介与安装](#part0003.xhtml)

### Hello.php - 我的第一个 PHP 脚本

本节提供了一个教程示例，介绍如何编写第一个 PHP 脚本 Hello.php，并使用 PHP CLI 和 PHP CGI 运行它。

使用记事本等任意文本编辑器，输入第一个 PHP 脚本 Hello.php：

```
Hello <?php echo "world!"; ?>
```

首先使用 PHP CLI 运行它：

```
herong> \php\php Hello.php

Hello world!
```

然后使用 PHP CGI 运行它：

```
herong> \php\php-cgi Hello.php

X-Powered-By: PHP/7.3.0
Content-type: text/html; charset=UTF-8

Hello world!
```

正如预期的那样，两个版本的 PHP 引擎都运行良好。PHP CGI 版本确实为我生成了 HTTP 响应头。

但请注意，PHP 7.3 中的 "Content-type" 设置为 "UTF-8"，这与 PHP 5.6 不同。请看 PHP 5.6 的输出：

```
>\php5.6\php-cgi Hello.php
Content-type: text/html
X-Powered-By: PHP/5.6.6

Hello world!
```

## [PHP 教程 - Herong 的教程示例](#part0001.xhtml)

### [PHP 7.3 简介与安装](#part0003.xhtml)

### "php -a" - PHP 交互式 Shell

本节提供了一个教程示例，介绍如何将 PHP 引擎作为交互式 Shell 运行，即 `php -a`，它允许你输入一条 PHP 语句并立即在屏幕上看到结果。

在上一教程中，我学习了如何运行 PHP 引擎来执行存储在文件中的 PHP 脚本。

PHP 引擎也可以用作交互式 Shell，从控制台获取 PHP 脚本并逐行交互式地执行。

以下是运行 PHP 引擎作为交互式 Shell 的一个会话：

```
herong> \php\php -a

Interactive shell

php > print "I am tossing a coin...\n";
I am tossing a coin...
php > $coin = rand(0,1);
php > if ($coin==1) {
php {    print "   Head\n";
php { } else {
php {    print "   Tail\n";
php { }
   Head
php > exit

C:\herong>
```

很酷。这确实是一个有助于学习 PHP 的好工具。只需输入一条 PHP 语句，即可立即在屏幕上看到显示的结果。

## [PHP 教程 - Herong 的教程示例](#part0001.xhtml)

### [PHP 7.3 简介与安装](#part0003.xhtml)

### 下载和安装 PHP 文档

本节提供了一个教程示例，介绍如何下载和安装 HTML 格式的 PHP 文档。

为了帮助学习 PHP 语言和内置扩展，我们还应该下载 PHP 文档：

1. 访问 [php.net/download-docs.php](http://php.net/download-docs.php) 并下载 "English" 和 "Many HTML files" 版本的 "tar.gz" 格式。你将得到一个名为 "php_manual_en.tar.gz" 的文件，大小为 11,269,511 字节。

2. 将 "php_manual_en.tar.gz" 解压到 `\php\html` 文件夹。

3. 在 Web 浏览器中打开 `\php\html\index.html` 并将其加入书签。

![PHP 文档 - HTML 版本](Images/image00229.jpeg)

PHP 文档 - HTML 版本

## [PHP 教程 - Herong 的教程示例](#part0001.xhtml)

### PHP 脚本文件语法

本章提供关于 PHP 脚本文件语法的教程笔记和示例代码。主题包括在脚本文件中包含 PHP 代码段使用什么标签；脚本文件处理规则；如何将 1 条语句拆分为多行，如何在 PHP 脚本中输入注释。

> [PHP 脚本源代码文件格式](#part0014.xhtml)

> [PHP 脚本处理规则](#part0015.xhtml)

> [PHP 语句分隔符和注释](#part0016.xhtml)

要点：

*   PHP 处理标签 `<?php ... ?>` 用于将 PHP 代码段包含到 PHP 脚本文件中。

*   所有非 PHP 文本段在 PHP 执行前都会被转换为 PHP print 语句。

*   所有 PHP 代码段和转换后的 print 语句会被合并为单个 PHP 代码块以供执行。

*   分号 `;` 用作 PHP 语句分隔符。

*   注释可以用 Perl、Java 或 C 风格输入到 PHP 代码段中。

## [PHP 教程 - Herong 的教程示例](#part0001.xhtml)

### [PHP 脚本文件语法](#part0013.xhtml)

### PHP 脚本源代码文件格式

本节描述 PHP 脚本源代码文件格式——一个将 PHP 代码段混合到非 PHP 文本中的文本文件。混合 PHP 代码最常用的方法是使用 PHP 处理标签 `?php`。

与其他任何脚本语言一样，PHP 通过将 PHP 代码段混合在输入文本中，将文本信息从输入转换为输出。这种混合了 PHP 代码和非 PHP 文本的输入称为 PHP 脚本源代码，通常存储为文本文件。

由于多个 PHP 代码段可以与非 PHP 文本混合，PHP 脚本源代码将如下所示：

```
text PHP_code text PHP_code text PHP_code ...
```

当你请求 PHP 处理 PHP 脚本源代码时，它将使用以下 3 条默认规则将 PHP 代码段与非 PHP 文本分离：

1. PHP 处理标签：`<?php PHP_code ?>` - `?php` 标签中包含的所有内容将作为 PHP 代码处理。例如：

```
Hello <?php
   $name = "Herong";
   echo $name;
?>
, Nice to meet you!
```

2. PHP 处理标签简写：`<? PHP_code ?>` - `?` 标签中包含的所有内容将作为 PHP 代码处理。例如：

```
Hello <?
   $name = "Herong";
   echo $name;
?>
, Nice to meet you!
```

3. HTML "script" 标签：`<script language="php">PHP_code</script>` - "script" 起始标签和 "script" 结束标签之间的所有内容将作为 PHP 代码处理。例如：

```
Hello <script language="php">
   $name = "Herong";
   echo $name;
</script>
, Nice to meet you!
```

PHP 处理标签是将 PHP 代码混合到非 PHP 文本中以创建 PHP 脚本源代码文件的最常用方法。由于大多数 PHP 脚本旨在生成网页，PHP 脚本源代码中的非 PHP 文本主要由 HTML 标签组成。下面是一个生成简单网页的 PHP 脚本源代码示例：

```
<html>
<head>
<title>Welcome Page</title>
</head>
<body>
<p>
Hello <?php
   $name = "Herong";
   echo $name;
?>
, Nice to meet you!
</p>
</body>
</html>
```

## [PHP 教程 - Herong 的教程示例](#part0001.xhtml)

### [PHP 脚本文件语法](#part0013.xhtml)

### PHP 脚本处理规则

本节描述 PHP 脚本源代码处理规则——所有非 PHP 文本段被转换为 print 语句并与 PHP 代码段合并，形成单个代码块。

正如我在上一节中提到的，PHP 脚本源代码是非 PHP 文本段和 PHP 代码段的序列。PHP 引擎将按 3 个逻辑步骤处理源代码：

*   将每个非 PHP 文本段转换为带有 print 语句的 PHP 代码段。

*   将所有 PHP 代码段连接成单个最终 PHP 代码块。

*   执行最终的 PHP 代码块。

换句话说，PHP 脚本源代码可以被视为单个 PHP 代码块。所有非 PHP 文本段只是以一种特殊方式编写的 PHP print 语句。

PHP 的处理规则与 Active Server Page (ASP) 的处理规则非常相似。

现在让我们看一个示例 PHP 脚本源代码文件：

```
<?php
/* HeadOrTail.php
#- Copyright 2003 (c) HerongYang.com. All Rights Reserved.
*/ ?>
I am tossing a coin now. Guess what the result will be?
<?php $coin = rand(0,1); ?>
<?php if ($coin==1) { ?>
   Head
<?php } else { ?>
   Tail
<?php } ?>
```

如果你用 PHP 引擎处理此脚本，你将得到：

```
herong> \php\php HeadOrTail.php

I am tossing a coin now. Guess what the result will be?
   Tail
```

基于 PHP 引擎处理规则，从 PHP 引擎处理的角度来看，上述脚本与以下脚本完全相同：

