

使用快捷方式可以排除列定义。不过，只有在更新所有值或在创建表时已指定默认值的情况下，此方法才可行。

```
INSERT INTO members ($name, $bio, $ip);
```

INSERT 完成后，可以调用 mysql_insert_id()，它将返回最后一次成功插入的 ID。

```
$result = mysql_query("INSERT INTO members ( " .
  $name . ", " .
  $bio . ", " .
  $ip . ")");
```

```
$rowID = mysql_insert_id($result);
```

## 删除

DELETE 语句用于从表中删除一行或多行。与其他语句一样，你可以使用 WHERE、AND、OR 等创建条件。

```
DELETE FROM users WHERE id=3
```

也可以通过省略条件来删除数据库中的所有行：

```
DELETE FROM users
```

注意 DELETE 语句非常强大，应格外小心使用。

## 条件

MySQL 中的条件用于限制返回的数据量。例如，如下 SQL 查询将返回数据库中的所有用户：

```
SELECT * FROM users
```

## WHERE

如果你希望发生这种情况，这没问题。你可能只希望返回某些用户，甚至是一个特定用户。这可以通过 WHERE 条件来完成。

```
SELECT * FROM users WHERE id=3
```

## AND

当需要匹配多个条件时，使用 AND 条件。例如，你想要返回已注册且拥有有效账户的成员数据库。

```
SELECT * FROM users WHERE active=1 AND registered="yes"
```

可以使用任意组合的条件语句，但只能有一个 WHERE 语句。

## OR

当只希望一个条件匹配时，使用 OR 语句。例如，你想要返回级别为 admin 或 mod 的用户。可以将其视为 SQL 中的 if..else。

```
SELECT * FROM users WHERE level='admin' OR level='mod'
```

在尝试深入挖掘数据时，MySQL 中的条件非常有用，尤其是在开始组合它们时。花几分钟创建非常复杂的 SQL 语句并不罕见。

## 探索 Flash

Flash 不仅是一种技术，也是 Adobe 开发工具的名称，用于创建支持 Flash 的内容。这种内容可以是从简单的横幅广告到带有视频和用户交互的完整数据库驱动型网站的任何东西。

## Flash IDE

Flash IDE（集成开发环境）如图 2.4 所示，是一款功能强大的开发工具，具有许多有用的特性。

### 图 2.4

Flash CS3 IDE 默认布局

![](img/d9d48cd53eee0fbc1ebc363c322fac2c_80_0.png)

更新的工具之一是代码编辑器，也称为 ActionScript 面板。如图 2.5 所示，这是你为 Flash 应用程序编写 ActionScript 代码的地方。最新版本拥有强大的代码补全、高级调试以及语法高亮等新特性。

### 图 2.5 Flash CS3 中的 ActionScript 面板

![](img/d9d48cd53eee0fbc1ebc363c322fac2c_81_0.png)

你将在其中度过大部分开发时间。面板不是唯一的编辑器；你可以创建完整的 ActionScript 文件，如图 2.6 所示，并将其包含在应用程序中。

要创建自定义 AS 文件，请选择 File > New。从中间列中选择 ActionScript 3 File。将文件保存为 Sample.as 到桌面。

![](img/d9d48cd53eee0fbc1ebc363c322fac2c_82_0.png)

## 替代编辑器

市面上有许多 ActionScript 编辑器。我个人最喜欢的是来自 powerflasher 的 [FDT](http://fdt.powerflasher.com/)。该编辑器提供最大的自定义选项，并集成到 Eclipse 编辑器中，许多其他公司都依赖于它。

同时创建一个新的 FLA 并将其保存到桌面。现在打开代码编辑器并添加以下代码：

```
#include "Sample.as"
```

这一行代码将 Sample.as 的内容包含到你的应用程序中。这意味着你可以将所有 ActionScript 写在外部文件中，Flash 在测试或构建应用程序时会知道要包含它。

## 支持 Flash 的设备

Flash 不再仅仅是用于为 Web 创建花哨图形的简单动画工具。现在，你可以在手机、媒体播放器甚至某些相机等一系列产品上找到已安装的 Flash。手机技术尤其有趣，因为这些设备通常拥有活跃的互联网连接，这意味着你可以为移动设备和桌面开发富互联网应用程序（RIA）。

## 继续前进

你现在应该对 Flash 是什么及其在最新版本中的进步有了基本了解。本书将解释 Flash 与 ActionScript 的各个方面，特别是在处理 PHP 和数据管理方面。

不过，如需更详细的 Flash CS3 指南，我强烈推荐由 John Wiley & Sons, Inc. 出版的 Adobe Flash CS3 Professional Bible。

## 摘要

在本章中，你了解了 Web 服务器以及如何修改配置文件来设置自定义开发或生产环境。这些信息包括自定义错误页面、应用程序特定模块以及保护内容的最佳实践。

一旦理解了使用 Web 服务器的基础知识，下一步就是学习如何使用 PHP。这涵盖了 PHP 的基础知识以及本书各章的具体内容。

本章后半部分包含了关于 MySQL 以及如何处理数据库中数据的信息。

最后一部分是 Flash 的概述以及如何使用开发环境。如需更详细的概述，已给出一些参考资料。

## 第 3 章

### 建立连接

- 了解 Flash 中的通信
- 将 Flash 连接到 PHP
- 将 PHP 连接到 MySQL

“建立连接”是一个用于描述连接到各种数据源过程的短语。在本章中，它是以各种方式连接 ActionScript (Flash)、PHP 和 MySQL 的过程。这些数据可以是一个简单的网站，也可以是 Flash 作为前端显示的数据库驱动型内容管理系统。

如果尚未安装这三个组件，在继续本章之前，请参阅第 1 章。

每个部分的第一部分侧重于每种连接类型提供的内容，并接着给出示例，以提供完整的最终结果图景。

### 了解 Flash 中的通信

开发独立应用程序缺乏某些功能，主要是处理动态数据的能力。在较小的应用程序中，你可以使用扁平文件，例如 XML 文件，但随着项目不断增长，这些文件会带来问题。

基于简单文本文件的应用程序也会受到文件锁定的影响，当太多人访问文件时可能会发生这种情况。当这种情况发生时，Apache 和/或 PHP 可能会抛出错误，导致用户无法使用网站。

### 确定 PHP 的状态

在 Flash 中设置与 PHP 连接的第一步是确定 PHP 是否已正确安装并运行。这是通过创建一个简单的 PHP 文件来完成的，该文件输出已安装 PHP 版本的当前配置设置。

PHP 函数 phpinfo() 通过构建一个自定义 HTML 页面来输出配置信息，如图 3.1 所示。

> **警告** 将 phpinfo 文件留在服务器上可能存在安全风险。最好只在需要查看时上传它，然后将其删除。

以下是一个示例信息文件，用于调用 phpinfo() 函数。

```
<?php
// output php configuration settings
phpinfo();
?>
```

### 图 3.1

以下是 phpinfo 函数的输出，显示了当前的 PHP 配置设置。

![](img/d9d48cd53eee0fbc1ebc363c322fac2c_85_0.png)

如果看到 phpinfo 文件（通常为紫色，并以已安装的 PHP 版本开头），则表示安装正确。

但是，如果你看到下载 PHP 文件的对话框，则表示 Apache 配置不当或未启用 PHP 支持。这种设置级别在第 1 章和随 Apache 提供的帮助文件中有所介绍。在罕见情况下，你可能会看到“找不到服务器”页面，这可能意味着 Apache 未安装或未运行。

假设 PHP 和 Apache 都已正常运行，你可以继续进行将 Flash 连接到 PHP 的过程。

### 使用各种连接类型

Flash 提供多种不同的通信选项。确定在项目中使用哪种通信方式，取决于该特定应用程序的预期功能集。

### 单向通信

Flash 中的单向通信是将数据发送到 Web 服务器而不关心或不在乎是否有响应返回的过程。这主要用于打开 URL，但也可用于在不打算处理结果的情况下更新文件。这种通信类型通常用于简单触发事件或运行某种清理系统。

例如，如果你的网站需要定期清理文件（删除、重命名、移动），将此功能附加到前端系统是个好主意，因为服务器资源仅在为该用户提供内容时才会被占用。这将通过幕后的单向通信启动。

> **注意** “查看即更新” 概念不应用于备份解决方案，因为查看缓慢可能导致备份丢失。

以下是 Flash 中单向通信的示例：

```
var serverFile:String = "http://localhost/callLink.php";
var urlRequest:URLRequest = new URLRequest(serverFile);
navigateToURL(urlRequest);
```

navigateToURL 函数接受两个参数。第一个参数是 URLRequest 实例，第二个参数是窗口或目标。默认情况下，窗口为 _self，这意味着如果存在当前浏览器，新页面将加载到当前浏览器中。

但是，在某些情况下，你可能希望打开一个新浏览器窗口，可以通过添加第二个参数来实现。

```
var serverFile:String = "http://localhost/callLink.php";
```

