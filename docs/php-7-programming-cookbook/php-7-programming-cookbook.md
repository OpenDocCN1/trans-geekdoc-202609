# PHP 7 编程秘籍





## 鸣谢

**作者**
道格·比勒

**项目协调员**
苏珊娜·库廷

**审阅者**
萨尔瓦托雷·帕帕拉多
文森佐·普罗文扎

**校对**
Safis Editing

**索引编制者**
雷卡·奈尔

**委托编辑**
库纳尔·帕里赫

**生产协调员**
梅尔温·德萨

**获取编辑**
柯克·德科斯塔

**封面设计**
梅尔温·德萨

**内容发展编辑**
梅林特·托马斯·马修

**技术编辑**
马杜尼克塔·苏尼尔·钦达克

**文字编辑**
Safis Editing

# 前言

随着 PHP 7 的到来，我们迎来了一系列新功能和改进，例如抽象语法树、可抛出异常、标量类型提示、返回类型声明、速度提升等等。

如今，PHP 开发者面临的问题不再是“我是否应该使用新功能？”，而是“我如何利用这些功能更快地构建更好的应用程序？”

我记得在 PHP 4 时代构建应用程序。那是 PHP 开发者较为简单的时期，因为 PHP 可以与 HTML 混合编写，所有内容都集中在一个文件中。当时我们没有框架，而是有一些被包含进来的函数库。应用程序基本上就是我们将桌面 CRUD 应用程序“铲”到网络上的产物。

自那以后，应用程序开发发生了多次变革。AJAX、PHPUnit、composer 和 API 优先等新框架相继问世。

这些以及许多其他因素都影响了 PHP 开发者构建应用程序的方式。如今，如果你仍在使用混合 HTML 和 PHP 的分页式应用程序，你很可能会被笑逐出职场。那么，你该怎么做呢？你如何构建现代的 PHP 应用程序和 API？你如何利用 PHP 提供的所有新工具来构建更快、更好、更强大的应用程序？我很高兴你提出了这个问题。

我的朋友道格·比勒为你提供了答案。这本书不是那种你放在书架上永远不用的无用大部头（YAUT, Yet Another Useless Tome）。你手中拿着的这本书注定会迅速成为你“胶带修补库”的一部分。（每个开发者都有一个“胶带修补库”，它由那些你经常参考、以至于现在只能用胶带粘住的书组成。）

道格花时间向你展示了你需要理解的新功能，就像市面上许多开发者书籍那样。这本书的独特之处在于，作者花时间向你展示了如何使用这些新工具解决现实世界中的问题。你不仅能学到知识，还能立即用所学解决问题。

你不必是 PHP 专家才能使用高级概念。然而，如果你希望作为程序员成长，你就必须学习、理解并使用这些高级概念。这本书将帮助你在成为更好程序员的道路上前行。

**卡尔·埃文斯**

Nomad PHP
World Wide Herd 的技术主管

## 作者简介

道格·比勒自 1971 年在 DEC PDP-8 上使用 Dartmouth BASIC 编写第一个程序起，就迷上了计算机。在他广泛的职业生涯中，这位作者自 1978 年以来一直担任专业合同程序员，曾用 BASIC、PL/I、汇编、FORTH、C、C++、dBase/FoxBase/Clipper、Pascal、Perl、Java 和 PHP 编写过应用程序。1993 年，当他住在旧金山时，部署了他的第一个网站。他精通四种语言，游历广泛，曾居住在美国、法国、荷兰、英国、瑞典、苏格兰和泰国。他还曾花几年时间从事 Linux 系统管理和 TCP/IP 网络工作。此外，他也是一位杰出的音乐家（已创作超过 60 首歌曲），也是一位作家，笔名为道加斯·艾伦。

道格自己的公司是不likelysource.com，专门从事咨询、PHP 编程、网站开发和培训（主要为 Zend Technologies Ltd 和 Rogue Wave Software Inc. 服务）。

他在 https://www.lulu.com/ 上出版的虚构作品包括*《终结》*、*《然后呢？》*和*《进一步的迹象》*。他为 O'Reilly Media 创作的一些技术作品包括*《学习 PHP 和 MySQL》*、*《学习 PHP 安全》*、*《学习 MongoDB》*和*《学习 Doctrine》*。

> 首先，我要将这本书献给我的母亲，贝蒂·比勒，她于 2016 年 5 月去世。她一生都在鼓励我，并对我的成就鼓掌（无论那成就多么微不足道！）。她出席了我所有的音乐演唱会，买了我所有的 CD，读了我所有的书（即使她并不理解那些书）。我还要感谢我长期忍受的妻子，西里，她耐心地忍受了我写这本书所花费的时间，没有抱怨。（不过，如果我同意再写一本，她确实会发出威胁……谈判仍在进行中。）最后，我要感谢 PHP 社区中的一些知名人士，他们允许我向他们提出想法或给予我灵感。这些人包括：马修·威尔·奥芬尼、卡尔·埃文斯、达里尔·伍德、苏西·普洛克、萨尔瓦托雷·帕帕拉多、斯拉维·卡拉佐夫和克拉克·埃弗雷特。

## 审阅者简介

**萨尔瓦托雷·帕帕拉多**，天生技术极客，自 2002 年起担任软件工程师。他热爱“从零开始”的开发。他是一位技术爱好者、科幻读者、电影迷和 TED 演讲迷。

**文森佐·普罗文扎** 是一位拥有 5 年以上经验的网页开发者，熟悉不同的技术和编程语言（主要是 PHP 和 JavaScript）。他热爱旅行和阅读。

# www.PacktPub.com

# 电子书、折扣优惠及其他

您知道 Packt 提供其出版的所有书籍的电子版吗？您可以下载 PDF 和 ePub 文件。您可以在 www.PacktPub.com 升级到电子书版本，作为纸质书客户，您有权获得电子书的折扣。如需更多详情，请联系 customer care@packtpub.com。

在 www.PacktPub.com，您还可以阅读一系列免费技术文章，订阅各种免费新闻通讯，并享受 Packt 书籍和电子书的独家折扣和优惠。

![](img/39390f6d56c5a83b28db083a8bd5185c_9_0.png)

https://www2.packtpub.com/books/subscription/packtlib

您需要即时解决 IT 问题吗？PacktLib 是 Packt 的在线数字图书库。在这里，您可以搜索、访问并阅读 Packt 的整个图书库。

## 为什么要订阅？

- 可以搜索 Packt 出版的所有书籍内容
- 可以复制粘贴、打印和标记内容
- 按需访问，可通过网络浏览器访问

## 前言

PHP 7 在开源社区中引起了轰动，打破了速度纪录，这就好比吸引了所有人的目光。从最根本的意义上说，核心工程团队对语言进行了重大重写，但仍然高度保持了向后兼容性。这些内部变化的影响在外在表现上几乎使速度提升了 200%，并显著节省了内存使用。从开发角度来看，命令解析方式的变化以及统一的变量语法引入了编写代码的新方法，而这些在 PHP 的早期版本中是不可能实现的。同样，任何不了解 PHP 7 中命令解释方式的开发人员都可能陷入无形的陷阱，从而导致代码故障。因此，本书的宗旨是展示编写代码的新颖且令人兴奋的方式，并指出与之前 PHP 版本不兼容的任何领域。需要注意的是，本书涵盖了 PHP 7.0 和 7.1。

### 本书内容

第 1 章“构建基础”帮助您在 PHP 7 开发环境的初始设置和配置中入门。我们还将展示一些强有力的初始食谱，以展示 PHP 7 的新特性。

第 2 章“使用 PHP 7 高性能特性”深入探讨了语言的新特性。我们将介绍抽象语法树和统一变量语法等概念，您将了解这些概念如何影响日常编程。随后，我们将提供利用 PHP 7 性能改进的食谱，包括 `foreach()` 循环处理中的重要新变化。

第 3 章“使用 PHP 函数式编程”强调，PHP 始终具备使用程序员定义的函数库（而非类）进行工作的能力，PHP 7 也不例外。在本章中，我们将更仔细地查看函数处理的改进，包括为输入和输出提供涉及基本数据类型（如整数、浮点数、布尔值和字符串）的“类型提示”的能力。我们还将广泛介绍标准 PHP 库中的迭代器，以及如何通过利用生成器改进的处理来编写自己的迭代器。

第 4 章“使用 PHP 面向对象编程”探讨了 PHP 面向对象编程的基础。迅速超越基础部分后，您将学习如何使用 PHP 命名空间和特质。我们将涵盖架构考虑因素，包括如何最好地使用接口。最后，我们将讨论 PHP 7 的一个令人兴奋的新特性——匿名类，并附上其实用的示例。

第 5 章“与数据库交互”探讨了让您的应用程序读取和写入数据库的能力，这是任何现代网站的关键部分。然而，关于 PHP 数据对象（PDO）扩展的正确使用，存在广泛误解。本章将全面介绍 PDO，从而允许您的应用程序与大多数主要数据库（包括 MySQL、Oracle、PostgreSQL、IBM DB2 和 Microsoft SQL Server）进行交互，而无需学习其他命令集。此外，我们将涵盖高级技术，如处理领域模型实体、执行嵌入式二级查找以及使用 PHP 7 实现 jQuery DataTable 查找。

第 6 章“构建可扩展的网站”深入探讨了 PHP 开发人员构建交互式网站时面临的经典问题之一——硬编码 HTML 表单，随后必须进行维护。本章介绍了一种整洁且高效的面向对象方法，只需最少的代码，即可生成完整的 HTML 表单，并且可以轻松在初始配置中进行更改。另一个同样棘手的问题是如何过滤和验证从表单提交的数据。在本章中，您将学习如何开发一个易于配置的过滤和验证工厂，然后可以将其应用于任何传入的 post 数据。

第 7 章“访问 Web 服务”涵盖了正在变得对 Web 开发越来越重要的一方面——发布或消费 Web 服务的能力。本章涵盖了两种关键方法：SOAP 和 REST。您将学习如何实现 SOAP 和 REST 服务器及客户端。此外，展示的食谱使用了适配器设计模式，允许相当程度的自定义，这意味着您不被锁定在特定的设计范式上。

第 8 章“处理日期/时间和国际化方面”帮助您应对因万维网（WWW）增长带来的激烈竞争，导致越来越多的客户希望将业务扩展到国际市场。本章将使您快速掌握国际化的所有方面，包括使用表情符号、复杂字符和翻译。此外，我们将展示如何获取和处理区域信息，包括语言设置、数字和货币格式以及日期和时间。另外，我们将介绍展示如何创建可处理重复事件的国际化日历的食谱。

第 9 章“开发中间件”处理了当前开源社区中最热门的话题——中间件。顾名思义，中间件是一种软件，可以*插入*到位，为现有应用程序增加价值，而无需更改该应用程序的源代码。在本章中，我们将展示一系列食谱，实现为符合 PSR-7 标准的中间件（有关更多详细信息，请参阅*附录，定义 PSR-7 类*），执行身份验证、访问控制、缓存和路由功能。



第 10 章“查看高级算法”帮助你理解，作为一名开发人员，面对如此多的程序员和公司争夺相同的业务，掌握关键的高级算法极其重要。在本章中，使用 PHP 7，你将学习 getter 和 setter、链表、冒泡排序、堆栈和二进制搜索的理论与应用。此外，本章还探讨了如何使用这些技术来实现搜索引擎，以及如何处理多维数组。

第 11 章“实现软件设计模式”着重于面向对象编程的一个重要方面，即理解关键的软件设计模式。如果没有这些知识，当你申请新职位或试图吸引新客户时，作为开发人员，你将处于非常不利的境地。本章涵盖了几种极其重要的模式，包括 Hydration、Strategy、Mapper、对象关系映射（ORM）和发布/订阅（Pub/Sub）。

第 12 章“提升 Web 安全性”涉及当今互联网普及所带来的问题。我们目睹网络攻击以越来越高的频率发起，往往造成灾难性的财务和人身损失。在本章中，我们将提供实用的配方，如果实施这些方法，将从安全性和安全方面极大地提升你的网站水平。涵盖的主题包括过滤和验证、会话保护、安全表单提交、安全密码生成以及 CAPTCHA 的使用。此外，还提供了一个配方，展示如何在不使用 PHP mcrypt 扩展的情况下加密和解密数据，该扩展在 PHP 7.1 中已弃用（最终将从语言中移除）。

第 13 章“最佳实践、测试和调试”涵盖代码的最佳实践和调试，以产生编写良好且可运行的代码。在本章中，你还将学习如何设置和创建单元测试，处理意外错误和异常，以及生成测试数据。介绍了 PHP 7 的几个新功能，包括 PHP 7 如何“抛出”错误。值得注意的是，*最佳实践* 贯穿于全书，而不仅仅在本章中！

附录“定义 PSR-7 类”涉及最近被接受的 PHP 标准建议 7（PSR-7），它定义了与中间件配合使用的接口。在本附录中，你将看到 PSR-7 类的稳固实现，包括值对象（如 URI、body 和 file upload），以及请求和响应对象。

## 本书所需条件

要成功实施本书中介绍的配方，你只需要一台计算机、100MB 的额外磁盘空间，以及一个文本或代码编辑器（而不是文字处理软件！）。第一章将介绍如何设置 PHP 7 开发环境。Web 服务器是可选的，因为 PHP 7 包含了一个开发 Web 服务器。不需要互联网连接，但下载代码（如 PSR-7 接口集合）并查阅 PHP 7.x 文档可能会很有用。

## 本书适合读者

本书适合软件架构师、技术经理、中级到高级开发人员，或者仅仅是有好奇心的人。你需要具备基本的 PHP 编程知识，特别是面向对象编程（OOP）。

## 章节结构

在本书中，你将发现几个频繁出现的标题（Getting ready、How to do it、How it works、There's more 和 See also）。

为了提供清晰的操作指南来完成配方，我们按如下方式使用这些章节：

### 准备

本章告诉你该配方的预期结果，并描述如何设置配方所需的软件或任何前置配置。

### 操作方法

本章包含执行配方所需的步骤。

### 工作原理

本章通常包含对前一步骤中发生内容的详细解释。

### 延伸阅读

本章包含有关配方的额外信息，以帮助读者更深入地了解配方。

### 相关链接

本章提供指向其他有用信息的链接，以辅助该配方。

## 约定

在本书中，你会发现多种区分不同信息类型的文本样式。以下是一些样式示例及其含义说明。

文本中的代码词、数据库表名、文件夹名、文件名、文件扩展名、路径名、虚拟 URL、用户输入以及 Twitter 账号显示如下：“最后，将第三个要点中定义的 LotsProps 类放置在一个单独的文件中，即 chap_10_oop_using_getters_and_setters_magic_call.php。”

代码块设置如下：

```php
    protected static function loadFile($file)
    {
        if (file_exists($file)) {
            require_once $file;
            return TRUE;
        }
        return FALSE;
    }
```

当我们希望引起你对代码块中特定部分的注意时，相关行或项目将以粗体显示：

```php
    $params = [
        'db'    => __DIR__ . '/../data/db/php7cookbook.db.sqlite'
    ];
    $dsn = sprintf('sqlite:' . $params['db']);
```

任何命令行输入或输出编写如下：

```bash
cd /path/to/recipes
php -S localhost:8080
```

**新术语** 和 **重要词汇** 以 **粗体** 显示。你在屏幕上看到的单词，例如在菜单或对话框中，显示如下格式的文本：“当点击 **Purchases** 按钮时，显示初始购买信息。”

![](img/39390f6d56c5a83b28db083a8bd5185c_19_0.png)

![](img/39390f6d56c5a83b28db083a8bd5185c_19_1.png)

## 读者反馈

我们一直欢迎读者的反馈。告诉我们你对本书的看法——你喜欢或不喜欢的地方。读者反馈对我们很重要，因为它帮助我们开发你能真正从中获益最多的书籍。

要发送一般性反馈，只需发送邮件至 `feedback@packtpub.com`，并在邮件主题中提及书籍名称。

如果你擅长某个主题，并对撰写或参与编写一本书感兴趣，请参见我们位于 www.packtpub.com/authors 的作者指南。

## 客户支持

既然你已经是 Packt 书籍的骄傲拥有者，我们有一些事项可以帮助你充分利用你的购买。

### 下载示例代码

你可以从 `http://www.packtpub.com` 上的你的账户下载本书的示例代码文件。如果你是在其他地方购买本书，你可以访问 `http://www.packtpub.com/support` 并注册，以便直接通过电子邮件接收这些文件。

你可以按照以下步骤下载代码文件：

- 1. 使用你的电子邮件地址和密码登录或注册我们的网站。
- 2. 将鼠标指针悬停在顶部的 **SUPPORT** 标签上。
- 3. 点击 **Code Downloads & Errata**。
- 4. 在 **Search** 框中输入书名。
- 5. 选择你想要下载代码文件的那本书。
- 6. 从下拉菜单中选择你购买本书的渠道。
- 7. 点击 **Code Download**。

你还可以通过点击 Packt Publishing 网站上书籍网页上的 **Code Files** 按钮来下载代码文件。此页面可以通过在 **Search** 框中输入书名来访问。请注意，你需要登录你的 Packt 账户。

文件下载完成后，请确保使用最新版本的解压缩软件解压或提取文件夹：

- Windows 使用 WinRAR / 7-Zip
- Mac 使用 Zipeg / iZip / UnRarX
- Linux 使用内置工具或 7-Zip / PeaZip

本书的代码包也托管在 GitHub 上：https://github.com/PacktPublishing/PHP-7-Programming-Cookbook。我们还有来自我们丰富的书籍和视频目录的其他代码包，可在 https://github.com/PacktPublishing/ 获取。快去看看吧！

### 勘误表

虽然我们已尽力确保内容的准确性，但错误仍可能发生。如果你在我们任何书籍中发现错误——可能是文本或代码中的错误——我们将不胜感激你能向我们报告。这样做可以帮助其他读者避免困扰，并帮助我们改进本书的后续版本。如果发现任何勘误，请访问 http://www.packtpub.com/submit-errata，选择你的书籍，点击 Errata Submission Form 链接，并输入你的勘误详情。一旦你的勘误得到验证，你的提交将被接受，勘误将上传到我们的网站，或添加到该书籍 Errata 部分下的现有勘误列表中。

要查看以前提交的勘误，请访问 https://www.packtpub.com/books/content/support 并在搜索框中输入书名。所需信息将显示在 Errata 部分下。

### 盗版

互联网上版权材料的盗版问题是所有媒体中持续存在的问题。在 Packt，我们非常重视版权和许可的保护。如果你在互联网上以任何形式发现我们作品的非法副本，请立即向我们提供位置地址或网站名称，以便我们可以追究补救措施。

请通过 copyright@packtpub.com 联系我们，并提供疑似盗版材料的链接。

我们感谢你帮助保护我们的作者以及我们为你带来有价值内容的能力。




# 问题

如果您对本书的任何方面存在问题，您可以通过 questions@packtpub.com 联系我们，我们将尽力解决这些问题。

# 1 奠定基础

在本章中，我们将涵盖以下内容：

- PHP 7 安装注意事项
- 使用内置 PHP Web 服务器
- 定义测试 MySQL 数据库
- 安装 PHPUnit
- 实现类自动加载
- 悬停（Hover）网站（注：原文疑似笔误，结合上下文可能指 Hover 库或类似功能，此处直译）
- 构建深度 Web 扫描器
- 创建 PHP 5 到 PHP 7 代码转换器

## 引言

本章旨在作为一种*快速入门*，让您能够立即在 PHP 7 上开始运行，从而可以着手实现相关食谱。本书的一个基本假设是您已经具备良好的 PHP 和编程知识。虽然本书不会详细介绍 PHP 的实际安装过程，但鉴于 PHP 7 相对较新，我们将尽力指出您在安装 PHP 7 过程中可能遇到的怪癖和*陷阱*。

## PHP 7 安装注意事项

获取 PHP 7 主要有三种方式：

- 直接从源代码下载并安装
- 安装*预编译*二进制文件
- 安装 *AMP 包*（即 XAMPP、WAMP、LAMP、MAMP 等）

## 操作方法...

这三种方法按难度递增排列。然而，第一种方法虽然繁琐，但能让您对扩展和选项进行最精细的控制。

### 直接从源代码安装

为了使用这种方法，您需要拥有一个 C 编译器。如果您使用的是 Windows，**MinGW** 是一个备受青睐的免费编译器。它基于 **GNU** 项目提供的 **GNU 编译器集合（GCC）** 编译器。非免费编译器包括 Borland 经典的 **Turbo C** 编译器，当然，Windows 开发人员首选的编译器是 **Visual Studio**。不过，后者主要设计用于 C++ 开发，因此当您编译 PHP 时，需要指定 C 模式。

在 Apple Mac 上工作时，最佳解决方案是安装 **Apple 开发工具**。您可以使用 **Xcode IDE** 来编译 PHP 7，或者在终端窗口中运行 `gcc`。在 Linux 环境中，请在终端窗口中运行 `gcc`。

当在终端窗口或命令行中编译时，正常程序如下：

- configure
- make
- make test
- make install

关于配置选项（即运行 `configure` 时）的信息，请使用 **help** 选项：

```bash
configure --help
```

您在配置阶段可能会遇到的错误列在下表中：

| 错误 | 修复方法 |
| :--- | :--- |
| configure: error: xml2-config not found. Please check your libxml2 installation | 您只需要安装 libxml2。关于此错误，请参阅以下链接：http://superuser.com/questions/740399/how-to-fix-php-installation-when-xml2-config-is-missing |
| configure: error: Please reinstall readline - I cannot find readline.h | 安装 libreadline-dev |
| configure: WARNING: unrecognized options: --enable-spl, --enable-reflection, --with-libxml | 不是大问题。这些选项是默认值，不需要包含在内。更多详情，请参阅以下链接：http://jjcutrer.com/howto/linux/how-to-compile-php7-on-ubuntu-14-04 |

### 从预编译二进制文件安装 PHP 7

顾名思义，**预编译**二进制文件是别人好心从 PHP 7 源代码编译并提供的一套二进制文件。

在 Windows 的情况下，请访问 `http://windows.php.net/`。您会在左侧栏找到一个很好的提示集合，涉及选择哪个版本，**线程安全** 与 **非线程安全** 等。然后您可以点击 **Downloads**（下载），寻找适用于您环境的 ZIP 文件。下载 ZIP 文件后，将文件解压到您选择的文件夹中，将 `php.exe` 添加到路径中，并使用 `php.ini` 文件配置 PHP 7。

要在 Mac OS X 系统上安装预编译二进制文件，最好引入一个包管理系统。推荐给 PHP 使用的包管理系统包括以下：

- MacPorts
- Liip
- Fink
- Homebrew

在 Linux 的情况下，使用的打包系统取决于您使用的 Linux 发行版。下表按 Linux 发行版组织，汇总了在哪里寻找 PHP 7 包。

| 发行版 | 在哪里寻找 PHP 7 | 备注 |
| :--- | :--- | :--- |
| Debian | `packages.debian.org`/stable/php<br>`repos-source.zend.com/zend-server/early-access/php7/php-7*DEB` | 使用此命令：<br>`sudo apt-get install php7`<br><br>或者，您可以使用如图形化包管理工具 **Synaptic**。<br><br>确保选择 `php7`（而不是 `php5`）。 |
| Ubuntu | `packages.ubuntu.com`<br>`repo-source.zend.com/zend-server/early-access/php7/php-7*DEB*` | 使用此命令： `sudo apt-get install php7`<br>务必选择正确的 Ubuntu 版本。<br>或者，您可以使用如图形化包管理工具 **Synaptic**。 |
| Fedora / Red Hat | `admin.fedoraproject.org/pkgdb/packages`<br>`repo-source.zend.com/zend-server/early-access/php7/php-7*RHEL*` | 确保您是 root 用户： `su`<br>使用此命令： `dnf install php7`<br>或者，您可以使用如图形化包管理工具如 GNOME 包管理器。 |
| OpenSUSE | `software.opensuse.org/package/php7` | 使用此命令： `yast -i php7`<br>或者，您可以运行 `zypper`，或使用 **YaST** 作为图形工具。 |

### 安装 *AMP 包

**AMP** 指的是 **Apache**、**MySQL** 和 **PHP**（也有 **Perl** 和 **Python**）。* 指的是 Linux、Windows、Mac 等（即 LAMP、WAMP 和 MAMP）。这种方法通常是最简单的，但您对初始 PHP 安装的控制较少。另一方面，您始终可以修改 php.ini 文件并安装额外的扩展来按需自定义安装。下表总结了若干流行的 *AMP 包：

| 包 | 在哪里找到 | 免费？ | 支持* |
| :--- | :--- | :--- | :--- |
| XAMPP | www.apachefriends.org/download.html | 是 | WML |
| AMPPS | www.ampps.com/downloads | 是 | WML |
| MAMP | www.mamp.info/en | 是 | WM |
| WampServer | sourceforge.net/projects/wampserver | 是 | W |
| EasyPHP | www.easyphp.org | 是 | W |
| Zend Server | www.zend.com/en/products/zend_server | 否 | WML |

在上表中，我们列出了 *AMP 包，其中 * 被替换为 Windows 的 **W**、Mac OS X 的 **M** 和 Linux 的 **L**。

### 更多细节...

当您从包安装预编译二进制文件时，只安装核心扩展。非核心 PHP 扩展必须单独安装。

值得注意的是，PHP 7 在云计算平台上的安装通常遵循预编译二进制文件的安装程序。查明您的云环境使用的是 Linux、Mac 还是 Windows 虚拟机，然后按照本食谱中提到的适当程序进行操作。

PHP 7 可能尚未到达您喜爱的预编译二进制文件仓库。您始终可以从源代码安装，或者考虑安装其中一个 *AMP 包（见下一节）。对于基于 Linux 的系统，替代方案是使用个人包存档（PPA）方法。然而，由于 PPA 没有经过严格的筛选过程，安全性可能是一个问题。关于 PPA 安全考量的良好讨论可以在 http://askubuntu.com/questions/35629/are-ppas-safe-to-add-to-my-system-and-what-are-some-red-flags-to-watch-out-fo 找到。

### 参见

一般安装注意事项，以及三大主要操作系统平台（Windows、Mac OS X 和 Linux）的说明，可以在 http://php.net/manual/en/install.general.php 找到。

MinGW 的网站是 http://www.mingw.org/。

使用 Visual Studio 编译 C 程序的说明可以在 https://msdn.microsoft.com/en-us/library/bb384838 找到。

测试 PHP 7 的另一种可能方法是使用虚拟机。以下是一些可能有用的工具及其链接：

- Vagrant: https://github.com/rlerdorf/php7dev （php7dev 是一个预配置用于跨多个 PHP 版本测试 PHP 应用和开发扩展的 Debian 8 Vagrant 镜像）
- Docker: https://hub.docker.com/r/codersthephen/php7/ （其中包含一个 PHP7 Docker 容器）




## 使用内置的 PHP Web 服务器

除了单元测试和直接从命令行运行 PHP 外，测试应用程序的最明显方式就是使用 Web 服务器。对于长期项目来说，为 Web 服务器开发一个虚拟主机定义是有益的，该定义应尽可能接近客户所使用的服务器。为各种 Web 服务器（即 Apache、NGINX 等）创建此类定义超出了本书的范围。另一种快速且易用的替代方案（我们有空间在此讨论）是使用内置的 PHP 7 Web 服务器。

### 操作指南...

- 1. 要激活 PHP Web 服务器，首先切换到将作为代码基底的目录。

- 2. 然后你需要提供主机名或 IP 地址，可选地提供端口号。以下是运行本书提供的代码示例：

`cd /path/to/recipes`

`php -S localhost:8080`

你将在屏幕上看到类似这样的输出：

![](img/39390f6d56c5a83b28db083a8bd5185c_28_0.png)

- 3. 随着内置 Web 服务器继续处理请求，你还会看到访问信息、HTTP 状态码和请求信息。

- 4. 如果需要将 Web 服务器文档根目录设置为当前目录以外的其他目录，可以使用 -t 标志。该标志后必须跟随一个有效的目录路径。内置 Web 服务器会将此目录视为 Web 文档根目录，这在安全方面很有用。出于安全原因，一些框架（如 Zend Framework）要求 Web 文档根目录与实际源代码所在的位置不同。

以下是使用 -t 标志的示例：

```
php -S localhost:8080 -t source/chapter01
```

以下是输出的示例：

![](img/39390f6d56c5a83b28db083a8bd5185c_29_0.png)

### 定义测试 MySQL 数据库

为了测试目的，除了书中的源代码外，我们还在 https://github.com/dbireri/pwphp7cookbook 提供了一个包含示例数据的 SQL 文件。本书示例中使用的数据库名称是 php7cookbook。

构建基础

### 操作指南...

- 1. 定义一个 MySQL 数据库，php7cookbook。还将新数据库的权限分配给名为 cook 的用户，密码为 book。下表总结了这些设置：

| 项目 | 说明 |
| :--- | :--- |
| 数据库名称 | php7cookbook |
| 数据库用户 | cook |
| 数据库用户密码 | book |

- 2. 以下是创建数据库所需的 SQL 示例：

```
CREATE DATABASE IF NOT EXISTS dbname DEFAULT CHARACTER SET utf8 COLLATE utf8_general_ci;
CREATE USER 'user'@'%' IDENTIFIED WITH mysql_native_password;
SET PASSWORD FOR 'user'@'%' = PASSWORD('userPassword');
GRANT ALL PRIVILEGES ON dbname.* to 'user'@'%';
GRANT ALL PRIVILEGES ON dbname.* to 'user'@'localhost';
FLUSH PRIVILEGES;
```

- 3. 将示例值导入到新数据库中。导入文件 php7cookbook.sql 位于 https://github.com/dbireri/php7cookbook/blob/master/php7cookbook.sql。

## 安装 PHPUnit

单元测试可以说是测试 PHP 代码最流行的方式。大多数开发者都会同意，一套完整的测试对于任何正常开发的项目来说都是必需的。然而，很少有开发者真正编写这些测试。少数幸运的开发者有一个独立的测试团队为他们编写测试！但是，在与测试团队进行几个月的拉锯战之后，那些幸运者剩下的部分往往只会发牢骚和抱怨。无论如何，一本关于 PHP 的书如果不向测试至少点个头、眨眨眼，那是不完整的。

查找 **PHPUnit** 最新版本的地方是 https://phpunit.de/。PHPUnit 5.1 及以上版本支持 PHP 7。点击所需版本的链接，你将下载一个 `phpunit.phar` 文件。然后你可以使用归档执行命令，如下所示：

```
php phpunit.phar <command>
```

![](img/39390f6d56c5a83b28db083a8bd5185c_30_0.png)

> phar 命令代表 **PHP Archive**。该技术基于 tar，而 tar 本身曾被用于 UNIX。phar 文件是一组 PHP 文件，为了方便起见被打包到单个文件中。

8

## 实现类自动加载

在使用 **面向对象编程 (OOP)** 方法开发 PHP 时，建议将每个类放在自己的文件中。遵循此建议的优势在于长期维护更容易，可读性更高。缺点是每个类定义文件都必须被包含（即使用 `include` 或其变体）。为了解决这个问题，PHP 语言内置了一种机制，可以自动加载（`autoload`）任何尚未被明确包含的类。

### 准备工作

PHP 自动加载的最低要求是定义一个全局 `__autoload()` 函数。这是一个由 PHP 引擎在请求一个尚未包含的类时自动调用的 *魔术* 函数。当调用 `__autoload()` 时（假设你已经定义过它！），所请求的类名将作为参数出现。如果你正在使用 PHP 命名空间，类的完整命名空间名将被传递。由于 `__autoload()` 是一个 *函数*，它必须位于全局命名空间中；然而，其使用有限制。因此，在本例中，我们将使用 `spl_autoload_register()` 函数，它提供了更大的灵活性。

### 操作指南...

- 1. 本例中我们将要介绍的类是 `Application\Autoload\Loader`。为了利用 PHP 命名空间和自动加载之间的关系，我们将文件命名为 `Loader.php`，并将其放置在 `/path/to/cookbook/files/Application/Autoload` 文件夹中。

- 2. 我们要介绍的第一个方法只是加载一个文件。我们在运行 `require_once()` 之前使用 `file_exists()` 进行检查。这样做的原因是，如果找不到文件，`require_once()` 会产生一个无法通过 PHP 7 新的错误处理机制捕获的致命错误：

```
protected static function loadFile($file)
{
    if (file_exists($file)) {
        require_once $file;
        return TRUE;
    }
    return FALSE;
}
```

- 3. 然后我们可以在调用程序中测试 `loadFile()` 的返回值，并在最终无法加载文件之前遍历一组替代目录，如果最终无法加载，则抛出 `Exception`。

构建基础

> 你会注意到这个类中的方法和属性是静态的。这使我们在注册自动加载方法时具有更大的灵活性，并且也让我们可以将 Loader 类视为 **单例**。

- 接下来，我们定义调用 loadFile() 并实际执行基于命名空间类名定位文件逻辑的方法。该方法通过将 PHP 命名空间分隔符 \ 转换为适合此服务器的目录分隔符并追加 .php 来推导文件名：

```
public static function autoLoad($class)
{
    $success = FALSE;
    $fn = str_replace('\\', DIRECTORY_SEPARATOR, $class)
        . '.php';
    foreach (self::$dirs as $start) {
        $file = $start . DIRECTORY_SEPARATOR . $fn;
        if (self::loadFile($file)) {
            $success = TRUE;
            break;
        }
    }
    if (!$success) {
        if (!self::loadFile(__DIR__
            . DIRECTORY_SEPARATOR . $fn)) {
            throw new \Exception(
                self::UNABLE_TO_LOAD . ' ' . $class);
        }
    }
    return $success;
}
```

- 接下来，该方法遍历我们称为 self::$dirs 的目录数组，使用每个目录作为推导文件名的起点。如果成功，操作完成；如果不成功，作为最后手段，该方法尝试从当前目录加载文件。如果这也不成功，则会抛出 Exception。

- 接下来，我们需要一个方法，可以向我们待测试的目录列表中添加更多目录。注意，如果提供的值是数组，则使用 array_merge()。否则，我们只是将目录字符串添加到 self::$dirs 数组中：

```
public static function addDirs($dirs)
{
    if (is_array($dirs)) {
        self::$dirs = array_merge(self::$dirs, $dirs);
    } else {
```



self::$dirs[] = $dirs;

7. 接下来，我们来到最重要的部分；我们需要将我们的 `autoload()` 方法注册为 **标准 PHP 库（SPL）** 的自动加载器。这是通过使用 `spl_autoload_register()` 配合 `init()` 方法来实现的：

```php
public static function init($dirs = array())
{
    if ($dirs) {
        self::addDirs($dirs);
    }
    if (self::$registered == 0) {
        spl_autoload_register(__CLASS__ . '::autoload');
        self::$registered++;
    }
}
```

8. 此时，我们可以定义 `__construct()`，它调用 `self::init($dirs)`。这允许我们根据需要创建 Loader 的一个实例：

```php
public function __construct($dirs = array())
{
    self::init($dirs);
}
```

## 工作原理……

为了使用我们刚刚定义的自动加载器类，你需要引入 `Loader.php`。如果你的命名空间文件位于当前目录以外的目录中，你应该运行 `Loader::init()` 并提供额外的目录路径。

为了确保自动加载器正常工作，我们还需要一个测试类。以下是 `/path/to/cookbook/files/Application/Test/TestClass.php` 的定义：

```php
<?php

namespace Application\Test;

class TestClass
{
    public function getTest()
    {
        return __METHOD__;
    }
}
```

现在，创建一个示例 `chap_01_autoload_test.php` 代码文件来测试自动加载器：

```php
<?php
require __DIR__ . '/../Application/Autoload/Loader.php';
Application\Autoload\Loader::init(__DIR__ . '/../');

接下来，获取一个尚未加载的类的实例：

$test = new Application\Test\TestClass();
echo $test->getTest();

最后，尝试获取一个不存在的假类。注意，这将引发一个错误：

$fake = new Application\Test\FakeClass();
echo $fake->getTest();
```

## 扫描网站

非常常见的是，人们有兴趣扫描网站并从特定标签中提取信息。这种基本机制可用于在网络上搜寻有用的信息片段。在其他时候，你需要获取 `<IMG>` 标签及其 **SRC** 属性，或者 `<A>` 标签及其对应的 **HREF** 属性的列表。可能性是无限的。

## 实现方法...

1. 首先，我们需要获取目标网站的内容。乍一看，我们应该发起一个 cURL 请求，或者简单地使用 `file_get_contents()`。这些方法的问题在于，我们将不得不进行大量的字符串操作，很可能不得不大量使用令人畏惧的正则表达式。为了避免所有这些麻烦，我们将简单地利用一个已存在的 **PHP 7** 类 `DOMDocument`。因此，我们创建一个 `DOMDocument` 实例，将其设置为 **UTF-8**。我们不关心空白字符，并使用方便的 `loadHTMLFile()` 方法将网站内容加载到对象中：

```php
public function getContent($url)
{
    if (!$this->content) {
        if (stripos($url, 'http') != 0) {
            $url = 'http://' . $url;
        }
        $this->content = new DOMDocument('1.0', 'utf-8');
        $this->content->preserveWhiteSpace = FALSE;
        // @ 用于抑制由配置不当的网页生成的警告
        @$this->content->loadHTMLFile($url);
    }
    return $this->content;
}
```

注意，我们在调用 `loadHTMLFile()` 方法前加了一个 `@`。这样做不是为了掩盖糟糕的代码（在 PHP 5 中这种情况很常见！）。相反，`@` 用于抑制解析器遇到编写不良的 HTML 时生成的通知。假设我们可以捕获这些通知并记录它们，甚至可能赋予我们的 Hoover* 类诊断能力。

2. 接下来，我们需要提取感兴趣的标签。我们使用 `getElementsByTagName()` 方法来执行此操作。如果我们希望提取所有标签，可以将 `*` 作为参数提供：

```php
public function getTags($url, $tag)
{
    $count     = 0;
    $result    = array();
    $elements = $this->getContent($url)
                ->getElementsByTagName($tag);
    foreach ($elements as $node) {
        $result[$count]['value'] = trim(
            preg_replace('/\s+/', ' ', $node->nodeValue));
        if ($node->hasAttributes()) {
            foreach ($node->attributes as $name => $attr)
            {
                $result[$count]['attributes'][$name] =
                    $attr->value;
            }
        }
        $count++;
    }
    return $result;
}
```

3. 提取特定属性而不是标签可能也很有趣。相应地，我们为这个目的定义了另一个方法。在这种情况下，我们需要遍历所有标签并使用 `getAttribute()`。你会注意到有一个用于 DNS 域的参数。我们添加它是为了将扫描限制在同一域名内（例如，如果你正在构建网页树）：

```php
public function getAttribute($url, $attr, $domain = NULL)
{
    $result     = array();
    $elements = $this->getContent($url)
                ->getElementsByTagName('*');
    foreach ($elements as $node) {
        if ($node->hasAttribute($attr)) { 
            $value = $node->getAttribute($attr);
            if ($domain) { 
                if (stripos($value, $domain) !== FALSE) { 
                    $result[] = trim($value);
                }
            } else { 
                $result[] = trim($value);
            }
        }
    }
    return $result;
}
```

## 工作原理……

为了使用新的 Hoover 类，初始化自动加载器（如前所述）并创建一个 Hoover 类的实例。然后，你可以运行 `Hoover::getTags()` 方法，以从你作为参数指定的 URL 中生成标签数组。

以下是来自 `chap_01_vacuuming_website.php` 的一段代码，它使用 Hoover 类扫描 O'Relly 网站上的 `<A>` 标签：

```php
<?php
// 按需修改
define('DEFAULT_URL', 'http://oreilly.com/');
define('DEFAULT_TAG', 'a');

require __DIR__ . './../Application/Autoload/Loader.php';
Application\Autoload\Loader::init(__DIR__ . './../');

// 获取“vacuum”类
$vac = new Application\Web\Hoover();

// 注意：使用了 PHP 7 的空合并运算符
$url = strip_tags($_GET['url'] ?? DEFAULT_URL);
$tag = strip_tags($_GET['tag'] ?? DEFAULT_TAG);

echo 'Dump of Tags: ' . PHP_EOL;
var_dump($vac->getTags($url, $tag));
```

输出看起来可能像这样：

```php
Dump of $tags:
array(144) {
  [0] =>
  array(2) {
    'value' =>
    string(0) ""
    'attributes' =>
    array(1) {
      'href' =>
      string(22) "http://www.oreilly.com"
    }
  }
  [1] =>
  array(2) {
    'value' =>
    string(12) "Your Account"
    'attributes' =>
    array(2) {
      'href' =>
      string(26) "http://members.oreilly.com"
      'class' =>
      string(12) "signInLinky"
    }
  }
  [2] =>
  array(2) {
    'value' =>
    string(13) "Shopping Cart"
    'attributes' =>
    array(1) {
```

## 参见

有关 DOM 的更多信息，请参阅 [PHP 参考页面](http://php.net/manual/en/class.domdocument.php)。

## 构建深层网络扫描器

有时你需要扫描网站，但需要深入下一层。例如，你想为一个网站构建网页树图。这可以通过查找所有 `<a>` 标签并跟随 HREF 属性到下一个网页来实现。一旦你获取了子页面，你就可以继续扫描以完成树。

## 实现方法...

1. 深层网络扫描器的核心组件是一个基本的 `HooVer` 类，如前所述。本食谱中介绍的基本程序是扫描目标网站并抓取所有的 `HREF` 属性。为此，我们定义了 `Application\Web\Deep` 类。我们添加了一个属性来表示 DNS 域：

```php
namespace Application\Web;

class Deep
{
    protected $domain;
}
```

2. 接下来，我们定义一个方法来抓取扫描列表中每个网站的标签。为了防止扫描器遍历整个 `万维网（WWW）`，我们将扫描限制在目标域内。添加 `yield from` 的原因是，我们需要生成 `HooVer::getTags()` 生成的整个数组。`yield from` 语法允许我们将数组视为子生成器：

```php
public function scan($url, $tag)
{
    $vac     = new HooVer();
    $scan   = $vac->getAttribute($url, 'href',
            $this->getDomain($url));
    $result = array();
    foreach ($scan as $subSite) {
        yield from $vac->getTags($subSite, $tag);
    }
    return count ($scan);
}
```

> 使用 `yield from` 将 `scan()` 方法变为 PHP 7 委托生成器。通常，你可能会倾向于将扫描结果存储在数组中。问题在于，在这种情况下，检索的信息量可能非常大。因此，最好立即生成结果，以节省内存并立即产生结果。否则，会有漫长的等待，随后可能会遇到内存溢出错误。

3. 为了保持在同一域名内，我们需要一个方法来从 URL 返回域名。我们使用方便的 `parse_url()` 函数来实现此目的：

```php
public function getDomain($url)
{
    if (!$this->domain) {
        // 代码继续...
    }
}
```





## 工作原理...

首先，请继续定义前面提到的 `Application\Web\Deep` 类，以及上一道菜中定义的 `Application\Web\Hoover` 类。

接下来，从 `chap_01_deep_scan_website.php` 中定义一段设置自动加载的代码（如本章前面所述）：

```php
<?php
// 根据需要修改
define('DEFAULT_URL', 'unlikelysource.com');
define('DEFAULT_TAG', 'img');

require __DIR__ . '/../../Application/Autoload/Loader.php';
Application\Autoload\Loader::init(__DIR__ . '/../../');
```

接下来，获取我们新类的实例：

```php
$deep = new Application\Web\Deep();
```

此时，你可以从 URL 参数中获取 URL 和标签信息。PHP 7 的 null 合并运算符对于建立回退值非常有用：

```php
$url = strip_tags($_GET['url']) ?? DEFAULT_URL;
$tag = strip_tags($_GET['tag']) ?? DEFAULT_TAG;
```

一些简单的 HTML 将显示结果：

```php
foreach ($deep->scan($url, $tag) as $item) {
    $src = $item['attributes']['src'] ?? NULL;
    if ($src && (stripos($src, 'png') || stripos($src, 'jpg'))) {
        printf('<br><img src="%s"/>' , $src);
    }
}
```

## 参见

关于生成器和 yield from 的更多信息，请参见 http://php.net/manual/en/language.generators.syntax.php 上的文章。

## 创建一个 PHP 5 到 PHP 7 代码转换器

在大多数情况下，PHP 5.x 代码可以在 PHP 7 上无更改地运行。然而，有一些变化被归类为**向后不兼容**。这意味着，如果你的 PHP 5 代码以特定方式编写，或者使用了已被移除的函数，你的代码将会崩溃，你会遇到一个棘手的错误。

### 准备就绪

**PHP 5 到 PHP 7 代码转换器** 做两件事：

- 扫描你的代码文件并将已移除的 PHP 5 功能转换为 PHP 7 中的等价物
- 在语言用法发生变化但无法重写代码的地方添加 `// WARNING` 注释

![](img/39390f6d56c5a83b28db083a8bd5185c_40_0.png)

> 请注意，运行转换器后，你的代码不保证能在 PHP 7 中正常工作。你仍然需要检查添加的 `// WARNING` 标签。至少，这个食谱能让你在将 PHP 5 代码转换为 PHP 7 兼容代码时有一个良好的开端。

这个食谱的核心是新的 PHP 7 `preg_replace_callback_array()` 函数。这个神奇的函数允许你呈现一个以正则表达式为键的数组，其值代表独立的回调。然后你可以将字符串通过一系列转换。不仅如此，回调数组的主题本身*可以*是一个数组。

### 具体操作...

1. 在一个新的类 `Application\Parse\Convert` 中，我们从 `scan()` 方法开始，该方法接受一个文件名作为参数。它检查文件是否存在。如果存在，它调用 PHP 的 `file()` 函数，该函数将文件加载到数组中，每个数组元素代表一行：

```php
public function scan($filename)
{
    if (!file_exists($filename)) {
        throw new Exception(
            self::EXCEPTION_FILE_NOT_EXISTS);
    }
    $contents = file($filename);
    echo 'Processing: ' . $filename . PHP_EOL;

    $result = preg_replace_callback_array( [
```

2. 接下来，我们开始传递一系列键/值对。键是一个正则表达式，该表达式针对字符串进行处理。任何匹配项都会传递给回调，回调由键/值对的值部分表示。我们检查已从 PHP 7 中移除的开启和关闭标签：

```php
    // 替换不再支持的开启标签
    '!^\<\$=(\n| )!!' =>
        function ($match) {
            return '<?php' . $match[1];
        },
    
    // 替换不再支持的开启标签
    '!^\<\$=(\n| )!!' =>
        function ($match) {
            return '<?php echo ' . $match[1];
        },
    
    // 替换不再支持的关闭标签
    '!\$>!' =>
        function ($match) {
            return '?>';
        },
```

3. 接下来是一系列警告，当检测到某些操作且在 PHP 5 与 PHP 7 中处理这些操作的方式存在潜在代码破坏时发出警告。在所有这些情况下，代码不会被重写。相反，会添加一个包含 WARNING 字样的内联注释：

```php
    // $$$$xx 插值处理方式的变更
    '!(.*)\$\$!!' =>
        function ($match) {
            return '// WARNING: 变量插值
                ' . ' 现在从左到右进行' . PHP_EOL
                . '// 参见: http://php.net/manual/en/'
                . ' migration70.incompatible.php'
                . $match[0];
        },
    
    // list() 运算符处理方式的变更
    '!(.*?)list\(*?\)(?!' =>
        function ($match) {
            return '// WARNING: list() 运算符
                ' . ' 的处理方式已发生变更。'
                . ' 参见: http://php.net/manual/en/'
                . ' migration70.incompatible.php'
                . $match[0];
        };
```

```php
        },

        // \u{ 的实例
        '!(.*)?\\u{(!' =>
        function ($match) {
            return '// WARNING: \u{xxx} 现在被认为是 '
                . 'unicode 转义语法' . PHP_EOL
                . '// 参见: http://php.net/manual/en/'
                . 'migration70.new-features.php'
                . '#migration70.new-features.unicode-'
                . 'codepoint-escape-syntax' . PHP_EOL
                . $match[0];
        },

        // 依赖 set_error_handler()
        '!(.*)?set_error_handler(\s*?\)\.*(!' =>
        function ($match) {
            return '// WARNING: 可能无法 '
                . '捕获所有错误'
                . '// 参见: http://php.net/manual/en/'
                . '// language.errors.php7.php'
                . $match[0];
        },

        // session_set_save_handler(xxx)
        '!(.*)?session_set_save_handler(\s*?\)\(.*)\)' =>
        function ($match) {
            if (isset($match[3])) {
                return '// WARNING: PHP 5.4 中引入的'
                    . ' 一个影响 session_set_save_handler() 分配的处理程序 '
                    . ' 且 ignore_user_abort() 为 TRUE 的 '
                    . ' bug 已在 PHP 7 中修复。'
                    . ' 这可能会在 '
                    . ' 某些情况下 '
                    . ' 破坏你的代码。' . PHP_EOL
                    . '参见: http://php.net/manual/en/'
                    . 'migration70.incompatible.php'
                    . $match[0];
            } else {
                return $match[0];
            }
        },
```

4. 任何尝试使用 `<<` 或 `>>` 配合负运算符，或超出 64 的情况，都会被包裹在一个 `try { xxx } catch ( { xxx }` 块中，以查找抛出的 `ArithmeticError`：

```php
// 将位移操作包裹在 try / catch 中
'!(<(.*)?(\\d\*s*(\\<|\\>\\>\*?-?\[d+] (.*)?)$' =>
function ($match) {
    return '// WARNING: 负数和 '
    . '超范围的按位 '
    . '移位操作现在将 '
    . '抛出 ArithmeticError' . PHP_EOL
    . '参见: http://php.net/manual/en/'
    . 'migration70.incompatible.php'
    . 'try {' . PHP_EOL
    . "\t" . $match[0] . PHP_EOL
    . '}' catch (\ArithmeticError $e) {'
    . "\t" . 'error_log("File:" '
    . $e->getFile()
    . " Message:" . $e->getMessage());'
    . '}' . PHP_EOL;
},
```

> PHP 7 改变了错误处理方式。在某些情况下，错误被移动到与异常类似的分类中，并且可以被捕获！`Error` 和 `Exception` 类都实现了 `Throwable` 接口。如果你想捕获 `Error` 或 `Exception`，就捕获 `Throwable`。

5. 接下来，转换器重写任何对 `call_user_method*()` 的使用，这些功能已在 PHP 7 中被移除。它们被替换为使用 `call_user_func*()` 的等价物：

```php
// 将 "call_user_method()" 替换为
// "call_user_func()"
'!call_user_method\( (.*)?, (.*)?\) (\b|;) !' =>
function ($match) {
    $params = $match[3] ?? '';
    return '// WARNING: call_user_method() 已 '
    . '从 PHP 7 中移除' . PHP_EOL
    . "call_user_func(['" . trim($match[2]) . "','"
    . trim($match[1]) . '] ' . $params . ');';
},
```

```php
// 将 "call_user_method_array()"
// 替换为 "call_user_func_array()"
'!call_user_method_array\( (.*)?, (.*)?, (.*)?\) (\b|;) !' =>
```





## 6. 最后，任何尝试使用带有 `/e` 修饰符的 `preg_replace()` 的调用都会被重写为使用 `preg_replace_callback()`：

```php
'i^(.*?\\)preg_replace.*?/e(.*?)$!i' =>
function ($match) {
    $last = strrchr($match[2], ',');
    $arg2 = substr($match[2], 2, -1 * (strlen($last)));
    $arg1 = substr($match[0],
        strlen($match[1]) + 12,
        -1 * (strlen($arg2) + strlen($last)));
    $arg1 = trim($arg1, '(');
    $arg1 = str_replace('/e', '/', $arg1);
    $arg3 = '// WARNING: preg_replace() "/e" modifier
        . 'has been removed from PHP 7'
        . PHP_EOL
        . $match[1]
        . 'preg_replace_callback('
        . $arg1
        . 'function ($m) { return '
        . str_replace('$1', '$m', $match[1])
        . trim($arg2, "'\"")
        . trim($last, ',')
        . '); return ' . $match[3] . ');';
    return str_replace('$1', '$m', $arg3);
},
```

// 数组结束
],

// 这是转换的目标
$contents

); // 将结果作为字符串返回
return implode('', $result);
}

## 工作原理...

要使用该转换器，请从命令行运行以下代码。你需要提供要扫描的 PHP 5 代码文件名作为参数。

以下代码块 `chap_01_php5_to_php7_code_converter.php` 从命令行运行时，会调用该转换器：

```php
<?php
// 从命令行获取要扫描的文件名
$filename = $argv[1] ?? '';

if (!$filename) {
    echo '未提供文件名' . PHP_EOL;
    echo '用法: ' . PHP_EOL;
    echo __FILE__ . ' <文件名>' . PHP_EOL;
    exit;
}

// 设置类自动加载
require __DIR__ . '/../Application/Autoload/Loader.php';

// 将当前目录添加到路径中
Application\Autoload\Loader::init(__DIR__ . '/../');

// 获取“深度扫描”类
$convert = new Application\Parse\Convert();
echo $convert->scan($filename);
echo PHP_EOL;
```

## 参见

有关向后不兼容更改的更多信息，请参阅 http://php.net/manual/en/migration70.incompatible.php。

# 2 使用 PHP 7 的高性能特性

在本章中，我们将讨论并理解 PHP 5 和 PHP 7 之间的语法差异，并介绍以下食谱（示例）：

- 理解抽象语法树
- 理解解析过程中的差异
- 理解 `foreach()` 处理中的差异
- 利用 PHP 7 增强功能提高性能
- 遍历大文件
- 将电子表格上传到数据库
- 递归目录迭代器

## 简介

在本章中，我们将直接深入 PHP 7，介绍一些利用新高性能特性的食谱。然而，首先，我们将介绍一系列较小的食谱，用以说明 PHP 7 在处理参数解析、语法、`foreach()` 循环以及其他增强功能方面的差异。在深入探讨本章内容之前，让我们讨论一下 PHP 5 和 PHP 7 之间的一些基本差异。

PHP 7 引入了一个新层，称为 **抽象语法树** (Abstract Syntax Tree, AST)，它有效地将解析过程与伪编译过程解耦。虽然新层对性能几乎没有影响或没有影响，但它赋予了语言一种全新的语法一致性，这是以前不可能实现的。

AST 的另一个好处是解引用过程。简单来说，解引用是指能够立即获取对象的属性、运行对象的方法、立即访问数组元素以及立即执行回调的能力。在 PHP 5 中，这种支持是不一致且不完整的。例如，要执行一个回调，通常首先需要将回调或匿名函数赋值给一个变量，然后再执行它。而在 PHP 7 中，你可以立即执行它。

## 理解抽象语法树

作为一名开发者，你可能会有兴趣摆脱 PHP 5 及更早版本中施加的某些语法限制。除了前面提到的语法一致性之外，你在语法方面看到最大改进的地方将是能够调用任何返回值，只要简单地添加一组额外的括号即可使其 **可调用**。此外，当返回值是一个数组时，你也将能够直接访问任何数组元素。

### 实现方法...

- 1. 任何返回回调的函数或方法都可以通过简单地添加括号 `( )`（带或不带参数）来立即执行。来自任何返回数组的函数或方法的元素，可以通过简单地使用方括号 `[ ]` 指明元素来立即解引用。在接下来展示的简短（但平凡）示例中，函数 `test()` 返回一个数组。该数组包含六个匿名函数。`$a` 的值为 `$t`。`$$a` 被解释为 `$test`：

```php
function test() {
    return [
        1 => function () { return [
                1 => function ($a) { return 'Level 1/1:' . ++$a; },
                2 => function ($a) { return 'Level 1/2:' . ++$a; },
           ];},
        2 => function () { return [
                1 => function ($a) { return 'Level 2/1:' . ++$a; },
                2 => function ($a) { return 'Level 2/2:' . ++$a; },
           ];}
    ]; }

$a = 't';
$t = 'test';
echo $$a() [1] ( ) [2] (100);
```

- 2. AST 允许我们发出 `echo ${a() [1] () [2] (100)}` 命令。这是从左到右解析的，其执行过程如下：
    - `${a()}` 被解释为 `test()`，它返回一个数组
    - `[1]` 引用数组元素 1，它返回一个回调
    - `()` 执行此回调，它返回一个包含两个元素的数组
    - `[2]` 引用数组元素 2，它返回一个回调
    - `(100)` 执行此回调，提供一个值为 100，它返回 Level 1/2:101

![](img/39390f6d56c5a83b28db083a8bd5185c_49_0.png)

- 3. 以下是一个更实质性的示例，它利用 AST 语法定义了一个数据过滤和验证类。首先，我们定义 `Application\Web\Security` 类。在构造函数中，我们构建并定义两个数组。第一个数组由过滤回调组成。第二个数组包含验证回调：

```php
public function __construct()
{
    $this->filter = [
        'striptags'  => function ($a) { return strip_tags($a); },
        'digits'     => function ($a) { return preg_replace(
                       '/[^0-9]/', '', $a); },
        'alpha'      => function ($a) { return preg_replace(
                       '/[^A-Z]/i', '', $a); }
    ];
    $this->validate = [
        'alnum'      => function ($a) { return ctype_alnum($a); },
        'digits'     => function ($a) { return ctype_digit($a); },
        'alpha'      => function ($a) { return ctype_alpha($a); }
    ];
}
```

- 4. 我们希望以 *开发人员友好* 的方式调用此功能。因此，如果我们想要过滤数字，那么运行类似这样的命令将是最理想的：

```php
$security->filterDigits($item);
```

- 5. 为了实现这一点，我们定义了魔术方法 `__call()`，它使我们能够访问不存在的方法：

```php
public function __call($method, $params)
{
                preg_match('/^(filter|validate)(_.*)?$/i', $method, $matches);
                $prefix    = $matches[1] ?? '';
                $function = strtolower($matches[2] ?? '');
                if ($prefix && $function) {
                    return $this->$prefix[$function]($params[0]);
                }
                return $value;
            }
```

我们使用 `preg_match()` 将 `$method` 参数与 `filter` 或 `validate` 进行匹配。第二个子匹配随后将被转换为 `$this->filter` 或 `$this->validate` 中的一个数组键。如果两个子模式都产生子匹配，我们将第一个子匹配赋值给 `$prefix`，第二个子匹配赋值给 `$function`。这些最终将成为执行适当回调时的变量参数。

![](img/39390f6d56c5a83b28db083a8bd5185c_50_0.png)

> **不要在这上面走得太远！**

当你在 AST 所赋予的表达自由中尽情展示时，务必牢记，你最终编写的代码从长远来看可能会非常晦涩难懂。这最终将导致长期维护问题。

## 工作原理...

首先，我们创建一个示例文件 `chap_02_web_filtering_ast_example.php`，以利用第 1 章 *Building the Foundation* 中定义的自动加载类，获取 `Application\Web\Security` 的一个实例：

```php
require __DIR__ . '/../Application/Autoload/Loader.php';
Application\Autoload\Loader::init(__DIR__ . '..');
$security = new Application\Web\Security();
```

接下来，我们定义一块测试数据：

```php
$data = [
    '<ul><li>Lots</li><li>of</li><li>Tags</li></ul>',
    12345,
    'This is a string',
    'String with number 12345',
];
```

最后，我们对每个测试数据项调用每个过滤器和验证器：

```php
foreach ($data as $item) {
    echo 'ORIGINAL: ' . $item . PHP_EOL;
    echo 'FILTERING' . PHP_EOL;
```





## 参见

有关 AST 的更多信息，请参阅处理 **抽象语法树** 的 RFC，可以在 <https://wiki.php.net/rfc/abstract_syntax_tree> 上查看。

## 理解解析差异

在 PHP 5 中，赋值运算符右侧的表达式是按*从右到左*的顺序解析的。在 PHP 7 中，解析始终遵循*从左到右*的顺序。

## 如何操作...

- 1. 变量变量是一种间接引用值的方式。在下面的示例中，首先将 `$foo` 解释为 `${$bar}`。因此，最终返回值是 `$bar` 的值，而不是 `$foo` 的直接值（那将是 `bar`）：

```php
$foo = 'bar';
$bar = 'baz';
echo $$foo; // 返回   'baz';
```

- 2. 在下一个示例中，我们有一个变量变量 `$foo`，它引用了一个具有 `bar` 键和 `baz` 子键的多维数组：

```php
$foo = 'bar';
$bar = ['bar' => ['baz' => 'bat']];
// 返回   'bat'
echo $$foo['bar']['baz'];
```

- 3. 在 PHP 5 中，解析是从右到左进行的，这意味着 PHP 引擎正在寻找一个具有 `bar` 键和 `baz` 子键的 `$foo` 数组。然后，该元素的返回值将被解释以获取最终值 `${$foo['bar'] ['baz']}`。

- 4. 然而，在 PHP 7 中，解析始终是从左到右进行的，这意味着先解释 `$foo`（`$$foo` → `['bar']['baz']`）。

- 5. 在下一个示例中，你可以看到，与 PHP 7 相比，PHP 5 对 `$foo->$bar['bada']` 的解释大不相同。在下面的示例中，PHP 5 首先解释 `$bar['bada']`，并将此返回值与 `$foo` 对象实例进行引用。另一方面，在 PHP 7 中，解析始终是从左到右进行的，这意味着先解释 `$foo->$bar`，并期望一个具有 `bada` 元素的数组。顺便注意，这个示例使用了 PHP 7 的*匿名类*特性：

```php
// PHP 5:  $foo->{$bar['bada']}
// PHP 7:  ($foo->$bar)['bada']
$bar = 'baz';
// $foo = new class
{
   public $baz = ['bada' => 'boom'];
}
// 返回 'boom'
echo $foo->$bar['bada'];
```

- 6. 最后一个示例与紧接其上的示例相同，不同之处在于期望返回值是一个回调函数，随后立即执行如下：

```php
// PHP 5: $foo->{$bar['bada']}()
// PHP 7: (($foo->$bar)['bada']()
$bar = 'baz';
// 注意：此示例使用了新的 PHP 7 匿名类特性
$foo = new class
{
    public function __construct()
    {
        $this->baz = ['bada' => function () { return 'boom'; }];
    }
}
// 返回 'boom'
echo $foo->$bar['bada']();
```

## 工作原理...

将第 1 和第 2 步中说明的代码示例放入一个单一的 PHP 文件中，你可以将其命名为 `chap_02_understanding_diffs_in_parsing.php`。首先使用 PHP 5 执行脚本，你会注意到会出现一系列错误，如下所示：

![](img/39390f6d56c5a83b28db083a8bd5185c_53_0.png)

错误的原因是 PHP 5 的解析不一致，并得出了关于所请求的变量变量状态的错误结论（如前所述）。现在你可以**继续**添加其余的示例，如步骤 5 和 6 所示。如果你随后在 PHP 7 中运行此脚本，将显示出描述的结果，如下所示：

![](img/39390f6d56c5a83b28db083a8bd5185c_54_0.png)

## 参见

有关解析的更多信息，请参阅处理 **统一变量语法** 的 RFC，可以在 `https://wiki.php.net/rfc/uniform_variable_syntax` 上查看。

## 理解 foreach() 处理的差异

在某些相对不常见的情况下，`foreach()` 循环内部代码的行为在 PHP 5 和 PHP 7 之间会有所不同。首先，内部进行了大量的改进，这意味着就纯粹的速度而言，在 PHP 7 下运行 `foreach()` 循环内的处理速度要比 PHP 5 快得多。在 PHP 5 中注意到的问题包括在 `foreach()` 循环内部数组上使用 `current()` 和 `unset()`。其他问题与在操作数组本身时通过引用传递值有关。

## 如何操作...

- 1. 考虑以下代码块：

```php
$a = [1, 2, 3];
foreach ($a as $v) {
  printf("%2d\n", $v);
  unset($a[1]);
}
```

- 2. 在 PHP 5 和 7 中，输出将显示如下：
   1
   2
   3

- 3. 但是，如果你在循环前添加一个赋值操作，行为就会改变：
```php
$a = [1, 2, 3];
$b = &$a;
foreach ($a as $v) {
    printf("%2d\n", $v);
    unset($a[1]);
}
```

- 4. 比较 PHP 5 和 7 的输出：

| PHP 5 | PHP 7 |
| :---- | :---- |
| **1** | **1** |
| **3** | **2** |
| | **3** |

- 5. 使用引用内部数组指针的函数在 PHP 5 中也导致了不一致的行为。查看以下代码示例：
```php
$a = [1, 2, 3];
foreach($a as &$v) {
    printf("%2d - %2d\n", $v, current($a));
}
```

> 每个数组都有一个指向其当前元素的内部指针，从 1 开始，`current()` 返回数组中的当前元素。

- 6. 注意在 PHP 7 中运行时输出是规范化的且一致的：

| PHP 5 | PHP 7 |
| :---- | :---- |
| **1 - 2** | **1 - 1** |
| **2 - 3** | **2 - 1** |
| **3 - 0** | **3 - 1** |

- 7. 在按引用迭代数组完成后，在 `foreach()` 循环内部添加新元素在 PHP 5 中也是有问题的。这种行为在 PHP 7 中已变得一致。以下代码示例说明了这一点：

```php
$a = [1];
foreach($a as &$v) {
    printf("%2d -\n", $v);
    $a[1]=2;
}
```

- 8. 我们将观察到以下输出：

| PHP 5 | PHP 7 |
| :---- | :---- |
| 1 - | 1 - |
| 2 - | 2 - |

- 9. PHP 7 解决的另一个 PHP 5 的不良行为示例是，在按引用迭代数组期间使用修改数组的函数，例如 `array_push()`、`array_pop()`、`array_shift()` 和 `array_unshift()`。
查看这个示例：

```php
$a=[1,2,3,4];
foreach($a as &$v) {
    echo "$v\n";
    array_pop($a);
}
```

- 10. 你将观察到以下输出：

| PHP 5 | PHP 7 |
| :---- | :---- |
| 1 | 1 |
| 2 | 2 |
| 1 | |
| 1 | |

- 11. 最后，我们有一个案例，其中你正在通过引用迭代数组，并带有嵌套的 `foreach()` 循环，该循环本身也通过引用迭代同一个数组。在 PHP 5 中，这种构造根本无法正常工作。在 PHP 7 中，这已得到修复。以下代码块演示了这种行为：

```php
$a = [0, 1, 2, 3];
foreach ($a as &$x) {
    foreach ($a as &$y) {
        echo "$x - $y\n";
        if ($x == 0 && $y == 1) {
            unset($a[1]);
        }
```




## 工作原理...

将这些代码示例添加到单个 PHP 文件中，`chap_02_foreach.php`。在命令行下以 PHP 5 运行该脚本。预期输出如下：

```
ed@ed: ~/Desktop/Repos/php7_recipes/source/chapter02$
PHP VERSION: 5.6.22
unset() in foreach()
1
2
3
unset() in foreach() after assignment by reference
1
3
current() in foreach()
1 - 2
2 - 3
3 - 0
adding new element in foreach()
1
array_pop() in foreach()
1
2
1
1
reference in foreach()
0 - 0
0 - 1
0 - 3
ed@ed:~/Desktop/Repos/php7_recipes/source/chapter02$
```

在 PHP 7 下运行相同的脚本，并注意其中的差异：

| PHP 5 | PHP 7 |
| :--- | :--- |
| **0 - 0** | **0 - 0** |
| **0 - 1** | **0 - 1** |
| **0 - 3** | **0 - 3** |
| **3 - 0** | |
| **3 - 3** | |

![](img/39390f6d56c5a83b28db083a8bd5185c_58_0.png)

## 另请参阅

如需更多信息，请查阅已获接受的处理此问题的 RFC。关于此 RFC 的文档可在 <https://wiki.php.net/rfc/php7_foreach> 找到。

## 使用 PHP 7 增强功能提高性能

开发人员正在利用的一个趋势是**匿名函数**的使用。处理匿名函数时的一个经典问题是，如何编写它们，使得任何对象都可以绑定到 `$this`，同时函数仍能正常工作。在 PHP 5 代码中，使用的是一种通过 `bindTo()` 的方法。在 PHP 7 中，新增了一个名为 `call()` 的方法，它提供类似的功能，但性能有了巨大的提升。

## 操作方法...

为了利用 `call()`，在一个冗长的循环中执行匿名函数。在本例中，我们将演示一个匿名函数，它扫描日志文件，识别 IP 地址并按其出现频率进行排序：

1. 首先，我们定义一个 `Application\Web\Access` 类。在构造函数中，我们接受一个文件名作为参数。日志文件以 `SplFileObject` 打开，并赋值给 `$this->log:`

```php
namespace Application\Web;

use Exception;
use SplFileObject;

class Access
{
    const ERROR_UNABLE = 'ERROR: unable to open file';
    protected $log;
    public $frequency = array();
    
    public function __construct($filename)
    {
        if (!file_exists($filename)) {
            $message = __METHOD__ . ' : ' . self::ERROR_UNABLE . PHP_EOL;
            $message .= strip_tags($filename) . PHP_EOL;
            throw new Exception($message);
        }
        $this->log = new SplFileObject($filename, 'r');
    }
}
```

2. 接下来，我们定义一个生成器，逐行遍历文件：

```php
public function fileIteratorByLine()
{
    $count = 0;
    while (!$this->log->eof()) {
        yield $this->log->fgets();
        $count++;
    }
    return $count;
}
```

3. 最后，我们定义一个方法，查找 IP 地址并将其作为子匹配项提取出来：

```php
public function getIp($line)
{
    preg_match('/(\d{1,3}\.\d{1,3}\.\d{1,3}\.\d{1,3})/', $line, $match);
    return $match[1] ?? '';
}
```

## 工作原理...

首先，我们定义一个调用程序 `chap_02_performance_using_php7_enhancement_call.php`，它利用*第 1 章，奠定基础*中定义的自动加载类，获取 `Application\Web\Access` 的实例：

```php
define('LOG_FILES', '/var/log/apache2/*access*.log');
require __DIR__ . '/../Application/Autoload/Loader.php';
Application\Autoload\Loader::init(__DIR__ . '/..');
```

接下来我们定义匿名函数，该函数处理日志文件中的一行。如果检测到 IP 地址，它将成为 `$frequency` 数组中的一个键，并且该键的当前值将递增：

```php
// define functions
$freq = function ($line) {
    $ip = $this->getIp($line);
    if ($ip) {
        echo '.';
        $this->frequency[$ip] =
            (isset($this->frequency[$ip])) ? $this->frequency[$ip] + 1 : 1;
    }
};
```

然后我们遍历找到的每个日志文件中的每一行迭代，处理 IP 地址：

```php
foreach (glob(LOG_FILES) as $filename) {
    echo PHP_EOL . $filename . PHP_EOL;
    // access class
    $access = new Application\Web\Access($filename);
    foreach ($access->fileIteratorByLine() as $line) {
        $freq->call($access, $line);
    }
}
```

实际上你可以在 PHP 5 中做同样的事情，但是需要两行代码：

```
$func = $freq->bindTo($access);
$func($line);
```

与在 PHP 7 中使用 `call()` 相比，性能要慢**20% 到 50%**。

最后，我们对数组进行逆序排序，但保留键。输出在一个简单的 `foreach()` 循环中产生：

```
arsort($access->frequency) ;
foreach ($access->frequency as $key => $value) {
    printf('$16s : %6d' . PHP_EOL, $key, $value);
}
```

输出将根据你处理的哪个 `access.log` 而有所不同。以下是一个示例：

![](img/39390f6d56c5a83b28db083a8bd5185c_61_0.png)

## 更多...

许多 PHP 7 的性能改进与新特性和函数无关。相反，它们以内部改进的形式出现，直到你开始运行程序前都是*不可见的*。以下是属于此类别的一些改进的简短列表：

| 特性 | 更多信息 | 备注 |
| :--- | :--- | :--- |
| 快速参数解析 | [https://wiki.php.net/rfc/fast_zpp](https://wiki.php.net/rfc/fast_zpp) | 在 PHP 5 中，提供给函数的参数必须在每次函数调用时都进行解析。参数是以`string`形式传入，并以类似于`scanf()`函数的方式进行解析。在 PHP 7 中，此过程已得到优化，效率大大提高，从而带来了显著的性能提升。这种改进很难衡量，但似乎约为 6%。 |
| PHP NG | [https://wiki.php.net/rfc/phpng](https://wiki.php.net/rfc/phpng) | PHP **NG (下一代)** 计划代表对 PHP 语言大部分内容的重写。它保留了现有功能，但涉及所有可想象的节省时间和提高效率的措施。数据结构已得到压缩，内存使用更加高效。例如，仅仅一个影响数组处理的更改，就带来了显著的性能提升，同时大大减少了内存使用。 |
| 去除无用负载 | [https://wiki.php.net/rfc/removal_of_dead_sapis_and_exts](https://wiki.php.net/rfc/removal_of_dead_sapis_and_exts) | 约有二十多个扩展属于以下类别之一：已弃用、不再维护、依赖项不再维护，或尚未移植到 PHP 7。核心开发小组的投票决定移除“短名单”上约 2/3 的扩展。这减少了开销，并加快了 PHP 语言未来的整体开发速度。 |

## 遍历大文件

诸如 `file_get_contents()` 和 `file()` 之类的函数使用起来简单快捷，然而，由于内存限制，在处理大文件时很快就会引发问题。`php.ini` 中 `memory_limit` 设置的默认值为**128 兆字节**。因此，任何大于此大小的文件都不会被加载。

解析大文件时的另一个考虑因素是你的函数或类方法产生输出的速度有多快？例如，在产生用户输出时，乍一看似乎将输出累积在数组中会更好。然后一次性输出以提高效率。不幸的是，这可能会对用户体验产生不利影响。最好创建一个**生成器**，并使用 `yield` 关键字立即产生结果。

## 操作方法...

如前所述，做一个小小的改变，我们不直接使用 `f*` 函数，而是使用包含在 SPL（标准 PHP 库）中的 `SplFileObject` 类：

1. 首先，我们定义一个 `Application\Iterator\LargeFile` 类，并设置相应的属性和常量：

```php
namespace Application\Iterator;

use Exception;
use InvalidArgumentException;
use SplFileObject;
use NoRewindIterator;

class LargeFile
{
    const ERROR_UNABLE = 'ERROR: Unable to open file';
    const ERROR_TYPE   = 'ERROR: Type must be "ByLength",
                         "ByLine" or "Csv"';
    protected $file;
    protected $allowedTypes = ['ByLine', 'ByLength', 'Csv'];
}
```

2. 然后我们定义一个 `__construct()` 方法，它接受文件名作为参数，并使用 `SplFileObject` 实例填充 `$file` 属性。如果文件不存在，这也是抛出异常的好地方：

```php
public function __construct($filename, $mode = 'r')
{
    if (!file_exists($filename)) {
        $message = __METHOD__ . ': ' . self::ERROR_UNABLE . PHP_EOL;
        $message .= strip_tags($filename) . PHP_EOL;
        throw new Exception($message);
    }
    $this->file = new SplFileObject($filename, $mode);
}
```

3. 接下来我们定义一个方法 `fileIteratorByLine()`，该方法使用 `fgets()` 一次读取文件中的一行。创建一个互补的 `fileIteratorByLength()` 方法也是一个不错的主意，该方法做同样的事情，但使用 `fread()` 代替。使用 `fgets()` 的方法适合包含换行符的文本文件。另一个方法可以用于解析大型二进制文件：

```php
protected function fileIteratorByLine()
{
    $count = 0;
    while (!$this->file->eof()) {
        yield $this->file->fgets();
        $count++;
    }
}
```





```php
     }
     return $count;
  }

protected function fileIteratorByLength($NumBytes = 1024)
{
    $count = 0;
    while (!$this->file->eof()) {
        yield $this->file->fread($NumBytes);
        $count++;
    }
    return $count;
}
```

4. 最后，我们定义一个 `getIterator()` 方法，该方法返回一个 `NoRewindIterator()` 实例。此方法接受 `ByLine` 或 `ByLength` 作为参数，指的是前一步定义的两个方法。如果调用 `ByLength`，该方法还需要接受 `$numBytes` 参数。我们需要一个 `NoRewindIterator()` 实例是为了强制执行如下事实：在本示例中，我们只是单向读取文件：

```php
public function getIterator($type = 'ByLine', $NumBytes = NULL)
{
    if (!in_array($type, $this->allowedTypes)) {
        $message = __METHOD__ . ': ' . self::ERROR_TYPE . PHP_EOL;
        throw new InvalidArgumentException($message);
    }

    $iterator = 'fileIterator' . $type;
    return new NoRewindIterator($this->$iterator($NumBytes));
}
```

## 工作原理…

首先，我们利用第 1 章*构建基础*中定义的自动加载类，在调用程序 `chap_02_iterating_through_a_massive_file.php` 中获取 `Application\Iterator\LargeFile` 的实例：

```php
define('MASSIVE_FILE', '/../data/files/war_and_peace.txt');
require __DIR__ . '/../Application/Autoload/Loader.php';
Application\Autoload\Loader::init(__DIR__ . '/../');
```

接下来，在一个 **try** {...} **catch** {...} 块中，我们获取一个 `ByLine` 迭代器的实例：

```php
try {
    $largeFile = new Application\Iterator\LargeFile(__DIR__ . MASSIVE_FILE);
    $iterator = $largeFile->getIterator('ByLine');
```

然后，我们提供了一个有用的操作示例，在这种情况下，定义每行的平均单词数：

```php
$words = 0;
foreach ($iterator as $line) {
    echo $line;
    $words += str_word_count($line);
}
echo str_repeat('-', 52) . PHP_EOL;
printf("%-40s : %8d\n", 'Total Words', $words);
printf("%-40s : %8d\n", 'Average Words Per Line',
    ($words / $iterator->getReturn()));
echo str_repeat('-', 52) . PHP_EOL;
```

然后结束 **catch** 块：

```php
} catch (Throwable $e) {
    echo $e->getMessage();
}
```

预期输出（此处因过大无法展示！）显示，在 Project Gutenberg 版本的*战争与和平*中有 566,095 个单词。此外，我们发现每行的平均单词数为 8。

## 将电子表格上传到数据库

虽然 PHP 不具备读取特定电子表格格式（即 XLSX、ODS 等）的直接功能，但它确实具备读取 **CSV 逗号分隔值** 文件的能力。因此，为了处理客户提供的电子表格，您需要要求他们以 CSV 格式提供文件，或者您需要自行执行转换。

## 准备工作…

在将电子表格（即 CSV 文件）上传到数据库时，有三个主要考虑因素：

- 遍历（可能）巨大的文件
- 将每个电子表格行提取到 PHP 数组中
- 将 PHP 数组插入到数据库中

巨大文件的遍历将使用前述配方处理。我们将使用 `fgetcsv()` 函数将 CSV 行转换为 PHP 数组。最后，我们将使用 **PDO PHP 数据对象** 类来建立数据库连接并执行插入操作。

## 具体操作...

1. 首先，我们定义一个 `Application\Database\Connection` 类，该类根据提供给构造函数的参数集创建 PDO 实例：

```php
<?php
namespace Application\Database;

use Exception;
use PDO;

class Connection
{
    const ERROR_UNABLE = 'ERROR: Unable to create database connection';
    public $pdo;

    public function __construct(array $config)
    {
        if (!isset($config['driver'])) {
            $message = __METHOD__ . ' : ' . self::ERROR_UNABLE . PHP_EOL;
            throw new Exception($message);
        }
        $dsn = $config['driver']
            . ':host=' . $config['host']
            . ';dbname=' . $config['dbname'];
        try {
            $this->pdo = new PDO($dsn,
                $config['user'],
                $config['password'],
                [PDO::ATTR_ERRMODE => $config['errmode']]);
        } catch (PDOException $e) {
            error_log($e->getMessage());
        }
    }
}
```

## 使用 PHP 7 高性能特性

2. 然后，我们将 `Application\Iterator\LargeFile` 的实例整合进来。我们向该类添加一个新方法，旨在遍历 CSV 文件：

```php
protected function fileIteratorCsv() {
    $count = 0;
    while (!$this->file->eof()) {
        yield $this->file->fgetcsv();
        $count++;
    }
    return $count;
}
```

3. 我们还需要将 `Csv` 添加到允许的迭代方法列表中：

```php
const ERROR_UNABLE = 'ERROR: Unable to open file';
const ERROR_TYPE   = 'ERROR: Type must be "ByLength", "ByLine" or "Csv"';

protected $file;
protected $allowedTypes = ['ByLine', 'ByLength', 'Csv'];
```

## 工作原理...

首先，我们定义一个配置文件，`/path/to/source/config/db.config.php`，其中包含数据库连接参数：

```php
<?php
return [
    'driver'   => 'mysql',
    'host'     => 'localhost',
    'dbname'   => 'php7cookbook',
    'user'     => 'cook',
    'password' => 'book',
    'errmode'  => PDO::ERRMODE_EXCEPTION,
];
```

接下来，我们利用第 1 章*构建基础*中定义的自动加载类，获取 `Application\Database\Connection` 和 `Application\Iterator\LargeFile` 的实例，并定义调用程序 `chap_02_uploading_csv_to_database.php`：

```php
define('DB_CONFIG_FILE', '/…/data/config/db.config.php');
define('CSV_FILE', '…/data/files/prospects.csv');
require __DIR__ . '…/Application/Autoload/Loader.php';
Application\Autoload\Loader::init(__DIR__ . '/../');
```

然后，我们设置一个 `try {...} catch (...)` 块，该块捕获 `Throwable`。这允许我们捕获异常和错误：

```php
    try {
        // code goes here
    } catch (Throwable $e) {
        echo $e->getMessage();
    }
```

在 `try {...} catch (...)` 块内部，我们获取连接和大文件迭代器类的实例：

```php
    $connection = new Application\Database\Connection(
        include __DIR__ . DB_CONFIG_FILE);
    $iterator = (new Application\Iterator\LargeFile(__DIR__ . CSV_FILE))
        ->getIterator('Csv');
```

然后，我们利用 PDO 的 prepare/execute 功能。预编译语句中的 SQL 使用 `?` 来表示在循环中提供的值：

```php
    $sql = 'INSERT INTO `prospects` '
        . '("id","first_name","last_name","address","city","state_province",'
        . '"postal_code","phone","country","email","status","budget",'
        . '"last_updated") '
        . ' VALUES (?,?,?,?,?,?,?,?,?,?,?,?)';
    $statement = $connection->pdo->prepare($sql);
```

然后，我们使用 `foreach()` 遍历文件迭代器。每个 `yield` 语句生成一个值数组，代表数据库中的一行。然后，我们可以使用这些值与 `PDOStatement::execute()` 一起执行预编译语句，将值行插入到数据库中：

```php
    foreach ($iterator as $row) {
        echo implode(',', $row) . PHP_EOL;
        $statement->execute($row);
    }
```

然后，您可以检查数据库以验证数据是否成功插入。

## 递归目录迭代器

获取目录中的文件列表非常容易。传统上，开发人员使用 `glob()` 函数来实现此目的。从目录树中的特定点递归获取所有文件和目录的列表则更具挑战性。此配方利用了 **(SPL 标准 PHP 库)** 类 `RecursiveDirectoryIterator`，它可以出色地完成这一任务。

该类的作用是解析目录树，找到第一个子节点，然后跟随分支，直到没有更多子节点为止，然后停止！不幸的是，这不是我们想要的。我们需要想办法让 `RecursiveDirectoryIterator` 从给定的起点继续解析每个树和分支，直到没有更多文件或目录为止。恰好有一个出色的类 `RecursiveIteratorIterator` 可以做到这一点。通过将 `RecursiveDirectoryIterator` 包装在 `RecursiveIteratorIterator` 中，我们可以完成对任何目录树的完全遍历。

> **警告！**
>
> 请非常小心文件系统遍历的起始位置。如果您从根目录开始，递归过程可能会在所有文件和目录都被定位之前不会停止，从而导致服务器崩溃！

## 具体操作...

1. 首先，我们定义一个 `Application\Iterator\Directory` 类，该类定义适当的属性和常量，并使用外部类：

    ```php
    namespace Application\Iterator;

    use Exception;
    use RecursiveDirectoryIterator;
    use RecursiveIteratorIterator;
    use RecursiveRegexIterator;
    use RegexIterator;

    class Directory
    {

        const ERROR_UNABLE = 'ERROR: Unable to read directory';

        protected $path;
        protected $rdi;
        // recursive directory iterator
    ```

2. 构造函数基于目录路径在 `RecursiveIteratorIterator` 内部创建一个 `RecursiveDirectoryIterator` 实例：

    ```php
    public function __construct($path)
    {
        try {
            $this->rdi = new RecursiveIteratorIterator(
                new RecursiveDirectoryIterator($path),
    ```




# 3

## 使用 PHP 函数式编程

本章将涵盖以下主题：

- 开发函数
- 提示数据类型
- 使用返回值数据类型
- 使用迭代器
- 使用生成器编写自己的迭代器

### 简介

在本章中，我们将介绍利用 PHP **函数式编程** 特性的配方。函数式或**过程式**编程是 PHP 4 版本引入首个**面向对象编程 (OOP)** 实现之前，传统上编写 PHP 代码的方式。在函数式编程中，程序逻辑被封装到一系列离散的**函数**中，这些函数通常存储在单独的 PHP 文件中。然后，该文件可以被包含在任何未来的脚本中，从而允许随时调用所定义的函数。

### 开发函数

最困难的方面在于决定如何将程序逻辑拆分为函数。另一方面，在 PHP 中开发函数的机制相当简单。只需使用 `function` 关键字，给它一个名称，并在后面加上括号。

#### 实现方法...

1. 代码本身放在花括号内，如下所示：

```php
function someName ($parameter)
{
    $result = 'INIT';
    // one or more statements which do something
    // to affect $result
    $result .= ' and also ' . $parameter;
    return $result;
}
```

2. 你可以定义一个或多个**参数**。要使其中一个变为可选参数，只需为其分配一个默认值。如果你不确定要分配什么默认值，请使用 `NULL`：

```php
function someOtherName ($requiredParam, $optionalParam = NULL)
{
    $result = 0;
    $result += $requiredParam;
    $result += $optionalParam ?? 0;
    return $result;
}
```

你不能重新定义函数。唯一的例外是当重复的函数在不同的命名空间中定义时。以下定义将产生错误：

```php
function someTest ()
{
    return 'TEST';
}
function someTest ($a)
{
    return 'TEST: ' . $a;
}
```

![](img/39390f6d56c5a83b28db083a8bd5185c_76_0.png)

3. 如果你不知道将为你的函数提供多少个参数，或者你想允许无限数量的参数，请使用 `...` 后跟变量名。所有提供的参数将以数组形式出现在该变量中：

```php
function someInfinite(...$params)
{
    // any params passed go into an array $params
    return var_export($params, TRUE);
}
```

4. 函数可以调用自身。这被称为**递归**。以下函数执行递归目录扫描：

```php
function someDirScan($dir)
{
    // uses "static" to retain value of $list
    static $list = array();
    // get a list of files and directories for this path
    $list = glob($dir . DIRECTORY_SEPARATOR . '*');
    // loop through
    foreach ($list as $item) {
        if (is_dir($item)) {
            $list = array_merge($list, someDirScan($item));
        }
    }
    return $list;
}
```

![](img/39390f6d56c5a83b28db083a8bd5185c_77_0.png)

> 在函数内部使用 **static** 关键字的功能已在语言中存在了 12 年多。**static** 的作用是在**static** 声明时初始化变量一次，然后在同一请求中的函数调用之间保持该值的保留。

如果你需要在 HTTP 请求之间保留变量的值，请确保 PHP 会话已启动，并将值存储在 `$_SESSION` 中。

5. 在 PHP **命名空间**内部定义时，函数会受到约束。你可以利用这一特性，在函数库之间提供额外的逻辑分离。为了*锚定*命名空间，你需要添加 **use** 关键字。以下示例放置在不同的命名空间中。请注意，即使函数名称相同，由于它们彼此不可见，因此没有冲突。

6. 我们在命名空间 `Alpha` 中定义 `someFunction()`。我们将此保存到一个单独的 PHP 文件 `chap_03_developing_functions_namespace_alpha.php` 中：

```php
<?php
namespace Alpha;

function someFunction()
{
    echo __NAMESPACE__ . ':' . __FUNCTION__ . PHP_EOL;
}
```

7. 然后我们在命名空间 `Beta` 中定义 `someFunction()`。我们将此保存到一个单独的 PHP 文件 `chap_03_developing_functions_namespace_beta.php` 中：

```php
<?php
namespace Beta;

function someFunction()
{
    echo __NAMESPACE__ . ':' . __FUNCTION__ . PHP_EOL;
}
```

8. 然后我们可以通过在函数名称前加上命名空间名称来调用 `someFunction()`：

```php
include ( __DIR__ . DIRECTORY_SEPARATOR . 'chap_03_developing_functions_namespace_alpha.php');
include ( __DIR__ . DIRECTORY_SEPARATOR . 'chap_03_developing_functions_namespace_beta.php');
Alpha\someFunction();
Beta\someFunction();
```

> **最佳实践**
> 将函数库（以及类！）放入单独的文件中通常被认为是最佳实践：每个命名空间一个文件，每个文件一个类或函数库。
> 可以在单个命名空间中定义许多类或函数库。你开发到单独命名空间中的唯一原因是如果你希望促进功能的逻辑分离。





## 工作原理……

最佳实践是将所有逻辑相关的函数放入一个单独的 PHP 文件中。创建一个名为 `chap_03_developing_functions_library.php` 的文件，并将这些函数（前文已描述）放入其中：

- someName()
- someOtherName()
- someInfinite()
- someDirScan()
- someTypeHint()

然后，在调用这些函数的代码中引入该文件。

```php
include (__DIR__ . DIRECTORY_SEPARATOR . 'chap_03_developing_functions_library.php');
```

若要调用 `someName()` 函数，请使用该函数名称并提供参数。

```php
echo someName('TEST');    // 返回 "INIT" 以及 TEST"
```

你可以使用一个或两个参数来调用 `someOtherName()` 函数，如下所示：

```php
echo someOtherName(1);     // 返回  1
echo someOtherName(1, 1);  //  返回 2
```

`someInfinite()` 函数接受无限（或可变）数量的参数。以下是调用此函数的几个示例：

```php
echo someInfinite(1, 2, 3);
echo PHP_EOL;
echo someInfinite(22.22, 'A', ['a' => 1, 'b' => 2]);
```

## 使用 PHP 函数式编程

输出结果如下：

![](img/39390f6d56c5a83b28db083a8bd5185c_80_0.png)

我们可以按照以下方式调用 `someDirScan()`：

```php
echo someInfinite(1, 2, 3);
echo PHP_EOL;
echo someInfinite(22.22, 'A', ['a' => 1, 'b' => 2]);
```

输出结果如下：

![](img/39390f6d56c5a83b28db083a8bd5185c_80_1.png)

## 提示数据类型

在许多开发函数的场景中，你可能需要在其他项目中重用相同的函数库。此外，如果你在一个团队中工作，你的代码可能会被其他开发人员使用。为了控制代码的使用，采用**类型提示**可能更为合适。这涉及指定你的函数对特定参数所期望的数据类型。

### 如何实现……

1.  函数中的参数可以加上类型提示前缀。以下类型提示在 PHP 5 和 PHP 7 中均可用：
    - Array
    - Class
    - Callable
2.  如果调用函数时传递了错误的参数类型，则会抛出 TypeError。以下示例要求一个数组、一个 DateTime 实例以及一个匿名函数：

    ```php
    function someTypeHint(Array $a, DateTime $t, Callable $c)
    {
        $message = '';
        $message .= 'Array Count: ' . count($a) . PHP_EOL;
        $message .= 'Date: ' . $t->format('Y-m-d') . PHP_EOL;
        $message .= 'Callable Return: ' . $c() . PHP_EOL;
        return $message;
    }
    ```

    > 你不需要为每个参数都提供类型提示。仅在传递不同数据类型会对函数的处理产生负面影响时使用此技术。例如，如果你的函数使用 `foreach()` 循环，而你未提供数组或实现了 Traversable 接口的对象，则会产生错误。
3.  在 PHP 7 中，假设已做出适当的 `declare()` 指令，则允许**标量**（即整型、浮点型、布尔型和字符串型）类型提示。另一个函数展示了如何实现这一点。在包含该函数的代码库文件顶部，紧跟在 PHP 开始标签之后添加此 `declare()` 指令：

    ```php
    declare(strict_types=1);
    ```

4.  现在你可以定义包含标量类型提示的函数：

    ```php
    function someScalarHint (bool $b, int $i, float $f, string $s) {
        return sprintf ("\n%20s : %5s\n%20s : %5d\n%20s " .
                        ": %5.2f\n%20s : %20s\n\n",
                        'Boolean', ($b ? 'TRUE' : 'FALSE') ,
                        'Integer' , $i,
                        'Float' , $f,
                        'String', $s);
    }
    ```

5.  在 PHP 7 中，假设已声明严格类型提示，布尔类型提示的工作方式与其他三种标量类型（即整型、浮点型和字符串型）略有不同。你可以提供任何标量作为参数，且不会抛出 TypeError！然而，一旦传入函数，传入的值会自动转换为布尔数据类型。如果你传入除标量（即数组或对象）以外的任何数据类型，则会抛出 TypeError。下面是一个定义布尔数据类型的函数示例。请注意，返回值将自动转换为布尔值：

    ```php
    function someBoolHint (bool $b)
    {
        return $b;
    }
    ```

### 工作原理……

首先，你可以将 `someTypeHint()`、`someScalarHint()` 和 `someBoolHint()` 这三个函数放入一个单独的文件中以便引入。在本例中，我们将该文件命名为 `chap_03_developing_functions_type_hints_library.php`。别忘了在顶部添加 `declare(strict_types=1)`！

在调用代码中，然后引入该文件：

```php
include (__DIR__ . DIRECTORY_SEPARATOR . 'chap_03_developing_functions_type_hints_library.php');
```

若要测试 `someTypeHint()`，请调用该函数两次，第一次使用正确的数据类型，第二次使用错误的类型。不过，这会抛出 TypeError，因此你需要将函数调用包裹在 `try { ... } catch ( ) { ... }` 块中：

```php
try {
    $callable = function () { return 'Callback Return'; };
    echo someTypeHint ([1,2,3], new DateTime(), $callable);
    echo someTypeHint ('A', 'B', 'C');
} catch (TypeError $e) {
    echo $e->getMessage();
    echo PHP_EOL;
}
```

正如你在本小节末尾显示的输出结果中看到的，传递正确的数据类型时没有问题。当传递错误的类型时，会抛出 `TypeError`。

![](img/39390f6d56c5a83b28db083a8bd5185c_83_0.png)

> 在 PHP 7 中，某些错误已被转换为 `Error` 类，其处理方式与 `Exception` 类有些相似。这意味着你可以捕获 `Error`。`TypeError` 是 `Error` 的一个特定子类，在将错误的数据类型传递给函数时抛出。PHP 7 中所有 `Error` 类都实现了 `Throwable` 接口，`Exception` 类也是如此。如果你不确定是否需要捕获 `Error` 还是 `Exception`，可以添加一个捕获 `Throwable` 的代码块。

接下来你可以测试 `someScalarHint()`，使用正确和错误的值各调用一次，并将调用包裹在 `try { ... } catch () { ... }` 块中：

```php
try {
    echo someScalarHint(TRUE, 11, 22.22, 'This is a string');
    echo someScalarHint('A', 'B', 'C', 'D');
} catch (TypeError $e) {
    echo $e->getMessage();
}
```

预期之中，第一次调用函数成功，第二次抛出 `TypeError`。

当进行布尔值的类型提示时，传递任何标量值都不会导致抛出 `TypeError`！相反，该值会被解释为其布尔等价物。如果你随后返回此值，数据类型将变为布尔型。

若要测试这一点，请调用前面定义的 `someBoolHint()` 函数，并传入任意标量值作为参数。`var_dump()` 方法显示数据类型始终为布尔型：

```php
try {
    // 正向结果
    $b = someBoolHint(TRUE);
    $i = someBoolHint(11);
    $f = someBoolHint(22.22);
    $s = someBoolHint('X');
    var_dump($b, $i, $f, $s);
    // 反向结果
    $b = someBoolHint(FALSE);
    $i = someBoolHint(0);
    $g = someBoolHint(0,0);   
    $$s = someBoolHint('');
    var_dump($b, $i, $f, $s);
} catch (TypeError $e) {
    echo $e->getMessage();
}
```

如果你现在尝试相同的函数调用，但传入非标量数据类型，则会抛出 TypeError：

```php
try {
    $a = someBoolHint([1,2,3]);
    var_dump($a);
} catch (TypeError $e) {
    echo $e->getMessage();
}
try {
    $o = someBoolHint(new stdClass());
    var_dump($o);
} catch (TypeError $e) {
    echo $e->getMessage();
}
```

这是整体输出结果：

![](img/39390f6d56c5a83b28db083a8bd5185c_84_0.png)

## 另请参阅

PHP 7.1 引入了一种新的类型提示 `iterable`，它允许使用数组、`Iterators` 或 `Generators` 作为参数。请查阅此处获取更多信息：

- https://wiki.php.net/rfc/iterable

关于实现标量类型提示背后的基本原理的背景讨论，请查看这篇文章：

- https://wiki.php.net/rfc/scalar_type_hints_v5

## 使用返回值数据类型

PHP 7 允许你指定函数的返回值数据类型。然而，与标量类型提示不同，你无需添加任何特殊声明。

### 如何实现……

1.  本示例向你展示如何为函数返回值分配数据类型。要分配返回数据类型，首先像往常一样定义函数。在右括号之后，添加一个空格，然后依次加上数据类型和冒号：

    ```php
    function returnsString(DateTime $date, $format) : string
    {
        return $date->format($format);
    }
    ```

    ![](img/39390f6d56c5a83b28db083a8bd5185c_85_0.png)

    > PHP 7.1 引入了一种返回数据类型变化的形式，称为**可空类型**。你只需将 `string` 改为 `?string`。这允许函数返回 `string` 或 NULL。
2.  无论函数内部的数据类型如何，函数返回的任何值都会作为返回值转换为声明的数据类型。注意，在此示例中，`$a`、`$b` 和 `$c` 的值被相加产生一个总和并返回。通常，我们期望返回值是数值数据类型。然而，在这种情况下，返回数据类型被声明为 `string`，这覆盖了 PHP 的类型转换过程：

    ```php
    function convertsToString($a, $b, $c) : string
    {
        return $a + $b + $c;
    }
    ```




3. 你还可以将类作为返回数据类型。在这个例子中，我们指定返回类型为 **DateTime**，它是 PHP **DateTime** 扩展的一部分：

```php
function makesDateTime($year, $month, $day) : DateTime
{
    $date = new DateTime();
    $date->setDate($year, $month, $day);
    return $date;
}
```

**makesDateTime()** 函数可能是标量类型提示的良好候选者。如果 **$year**、**$month** 或 **$day** 不是整数，在调用 **setDate()** 时会产生一个 **Warning**（警告）。如果你使用标量类型提示，且传入了错误的数据类型，则会抛出 **TypeError**（类型错误）。虽然产生警告还是抛出 **TypeError** 其实无所谓，但抛出 **TypeError** 至少能让那些误用你代码的开发者警醒起来！

4. 如果一个函数有返回数据类型，而你在函数代码中返回了错误的数据类型，则会在运行时抛出 **TypeError**。此函数指定了 **DateTime** 作为返回类型，但实际上返回了一个字符串。将会抛出 **TypeError**，但这不会立即发生，而是等到运行时 PHP 引擎检测到这种不一致时才会发生：

```php
function wrongDateTime($year, $month, $day) : DateTime
{
    return date($year . '-' . $month . '-' . $day);
}
```

如果返回数据类型类不是内置 PHP 类之一（即不是 SPL 的一部分），你需要确保该类已被自动加载或被包含进来。

## 工作原理...

首先，将前面提到的函数放入一个名为 **chap_03_developing_functions_return_types_library.php** 的库文件中。该文件需要在调用这些函数的 **chap_03_developing_functions_return_types.php** 脚本中包含：

```php
include (__DIR__ . '/chap_03_developing_functions_return_types_library.php');
```

现在你可以调用 `returnsString()`，并传入一个 `DateTime` 实例和一个格式字符串：

```php
$date = new DateTime();
$format = 'l, d M Y';
$now = returnsString($date, $format);
echo $now . PHP_EOL;
var_dump($now);
```

如预期那样，输出是一个字符串：

![](img/39390f6d56c5a83b28db083a8bd5185c_87_0.png)

现在你可以调用 `convertsToString()` 并传入三个整数作为参数。注意返回类型是字符串：

```php
echo "\nconvertsToString()\n";
var_dump(convertsToString(2, 3, 4));
```

![](img/39390f6d56c5a83b28db083a8bd5185c_87_1.png)

为了演示可以将类作为返回值进行赋值，调用 `makesDateTime()` 并传入三个整型参数：

```php
echo "\nmakesDateTime()\n";
$d = makesDateTime(2015, 11, 21);
var_dump($d);
```

![](img/39390f6d56c5a83b28db083a8bd5185c_87_2.png)

最后，调用 *wrongDateTime*() 并传入三个整型参数：

```php
try {
    $e = wrongDateTime(2015, 11, 21);
    var_dump($e);
} catch (TypeError $e) {
    echo $e->getMessage();
}
```

注意，在运行时抛出了 *TypeError*：

![](img/39390f6d56c5a83b28db083a8bd5185c_88_0.png)

## 更多知识...

PHP 7.1 添加了一种新的返回值类型：*void*。当你不希望从函数中返回任何值时使用它。有关更多信息，请参阅 [https://wiki.php.net/rfc/void_return_type](https://wiki.php.net/rfc/void_return_type)。

## 另请参阅

有关返回类型声明的更多信息，请参阅以下文章：

- [http://php.net/manual/en/functions.arguments.php#functions.arguments.type-declaration.strict](http://php.net/manual/en/functions.arguments.php#functions.arguments.type-declaration.strict)
- [https://wiki.php.net/rfc/return_types](https://wiki.php.net/rfc/return_types)

有关可空类型的信息，请参阅此文章：

- https://wiki.php.net/rfc/nullable_types

## 使用迭代器

**迭代器**（iterator）是一种特殊的类，允许你**遍历**（traverse）*容器*或列表。这里的关键词是*遍历*。这意味着迭代器提供了遍历列表的手段，但它本身并不执行遍历。

SPL 提供了丰富的通用和专用迭代器，适用于不同的上下文。例如，`ArrayIterator` 旨在允许对数组进行面向对象的遍历。`DirectoryIterator` 旨在用于文件系统扫描。

某些 SPL 迭代器旨在与其他迭代器协同工作，并增加其价值。示例包括 `FilterIterator` 和 `LimitIterator`。前者允许你从父迭代器中移除不需要的值。后者提供分页功能，你可以指定要遍历的项目数量以及确定起始位置的偏移量。

最后，有一系列*递归*迭代器，允许你重复调用父迭代器。一个例子是 `RecursiveDirectoryIterator`，它扫描目录树，从起点一直扫描到最后一个可能的子目录。

## 实现方法...

1. 我们首先查看 `ArrayIterator` 类。它极其易于使用。你所需要做的只是在构造器中提供一个数组作为参数。之后，你可以使用所有基于 SPL 的迭代器所特有的任何标准方法，例如 `current()`、`next()` 等。

```php
$iterator = new ArrayIterator($array);
```

![](img/39390f6d56c5a83b28db083a8bd5185c_89_0.png)

2. 作为一个迭代器实际用途的例子，看看这个示例。它接受一个迭代器并生成一系列 HTML `<ul>` 和 `<li>` 标签：

```php
function htmlList($iterator)
{
    $output = '<ul>';
    while ($value = $iterator->current()) {
        $output .= '<li>' . $value . '</li>';
        $iterator->next();
    }
    $output .= '</ul>';
    return $output;
}
```

3. 或者，你可以简单地将 ArrayIterator 实例包裹在一个简单的 foreach() 循环中：

```php
function htmlList($iterator)
{
    $output = '<ul>';
    foreach($iterator as $value) {
        $output .= '<li>' . $value . '</li>';
    }
    $output .= '</ul>';
    return $output;
}
```

4. **CallbackFilterIterator 是为你可能正在使用的任何现有迭代器增加价值的好方法。它允许你包裹任何现有迭代器并筛选输出。在这个例子中，我们将定义 `fetchCountryName()`，它遍历一个产生国家名称列表的数据库查询。首先，我们定义一个 `ArrayIterator` 实例，该实例来自使用在*第 1 章，构建基础*中定义的 `Application\Database\Connection` 类执行的查询：**

```php
function fetchCountryName($sql, $connection)
{
    $iterator = new ArrayIterator();
    $stmt = $connection->pdo->query($sql);
    while($row = $stmt->fetch(PDO::FETCH_ASSOC)) {
        $iterator->append($row['name']);
    }
    return $iterator;
}
```

5. **接下来，我们定义一个过滤方法 `nameFilterIterator()`，它接受部分国家名称作为参数，连同 `ArrayIterator` 实例：**

```php
function nameFilterIterator($innerIterator, $name)
{
    if (!$name) return $innerIterator;
    $name = trim($name);
    $iterator = new CallbackFilterIterator($innerIterator,
        function($current, $key, $iterator) use ($name) {
            $pattern = '/' . $name . '/i';
            return (bool) preg_match($pattern, $current);
        }
    );
    return $iterator;
}
```

6. `LimitIterator` 为你的应用程序添加了基本的分页功能。要使用此迭代器，你只需要提供父迭代器、偏移量和限制值。`LimitIterator` 将从偏移量开始，只生成整个数据集的一个子集。以第 2 步中提到的相同示例为例，我们将对来自数据库查询的结果进行分页。我们可以通过将 fetchCountryName() 方法生成的迭代器包裹在一个 `LimitIterator` 实例中轻松完成此操作：

```php
$pagination = new LimitIterator(fetchCountryName(
$sql, $connection), $offset, $limit);
```

> 使用 `LimitIterator` 时要小心。它需要拥有*整个*数据集在内存中才能生效限制。因此，在遍历大型数据集时，这不是一个好工具。

7. 迭代器可以*堆叠*。在这个简单示例中，一个 `ArrayIterator` 由 `FilterIterator` 处理，而 `FilterIterator` 又受到 `LimitIterator` 的限制。首先，我们设置一个 `ArrayIterator` 实例：

```php
$i = new ArrayIterator($a);
```

8. 接下来，我们将 `ArrayIterator` 插入到 `FilterIterator` 实例中。注意，我们使用了 PHP 7 新的匿名类特性。在这种情况下，该匿名类继承自 `FilterIterator` 并重写 accept() 方法，只允许具有偶数 ASCII 码的字母通过：

```php
$f = new class ($i) extends FilterIterator {
public function accept()
{
$current = $this->current();
return !(ord($current) & 1);
}
};
```

9. 最后，我们将 `FilterIterator` 实例作为参数提供给 `LimitIterator`，并提供偏移量（本例中为 2）和限制值（本例中为 6）：

```php
$l = new LimitIterator($f, 2, 6);
```





10. 然后，我们可以定义一个简单的函数来显示输出，并依次调用每个迭代器，以查看由 `range('A', 'Z')` 生成的简单数组上的结果：

```php
function showElements($iterator)
{
    foreach($iterator as $item) echo $item . ' ';
    echo PHP_EOL;
}
$a = range('A', 'Z');
$i = new ArrayIterator($a);
showElements($i);
```

11. 下面是一个变体，它通过在 ArrayIterator 之上堆叠一个 FilterIterator 来产生每隔一个字母：

```php
$f = new class ($i) extends FilterIterator {
    public function accept()
    {
        $current = $this->current();
        return !(ord($current) & 1);
    }
};
showElements($f);
```

12. 还有一个变体，它只产生 F H J L N P，这演示了一个消耗 FilterIterator 的 LimitIterator，而 FilterIterator 又消耗 ArrayIterator。这三个示例的输出如下：

```php
$l = new LimitIterator($f, 2, 6);
showElements($l);
```

![](img/39390f6d56c5a83b28db083a8bd5185c_92_0.png)

13. 回到我们生成国家名称列表的示例，假设我们不想只遍历国家名称，而是希望遍历一个由国家名称和 ISO 代码组成的多维数组。到目前为止提到的简单迭代器是不够的。相反，我们将使用所谓的**递归**迭代器。

14. 首先，我们需要定义一个方法，该方法使用前面提到的数据库连接类来从数据库中获取所有列。与之前一样，我们返回一个填充了查询数据的 ArrayIterator 实例：

```php
function fetchAllAssoc($sql, $connection)
{
    $iterator = new ArrayIterator();
    $stmt = $connection->pdo->query($sql);
    while($row = $stmt->fetch(PDO::FETCH_ASSOC)) {
        $iterator->append($row);
    }
    return $iterator;
}
```

15. 乍一看，人们可能会想直接把标准的 ArrayIterator 实例包裹在 RecursiveArrayIterator 中。不幸的是，这种方法只执行**浅**层迭代，并不能给我们想要的结果：即遍历数据库查询返回的多维数组的所有元素：

```php
$iterator = fetchAllAssoc($sql, $connection);
$shallow = new RecursiveArrayIterator($iterator);
```

16. 虽然这返回了一个迭代，其中每个项目代表数据库查询中的一行，但在本例中，我们希望提供一个能遍历查询返回的所有行中所有列的迭代。为了实现这一点，我们需要通过 RecursiveIteratorIterator 来“大费周章”（roll out the big brass）。

17.  Monty Python（巨蟒）的粉丝们会为这个类名的丰富讽刺意味而欣喜，因为它唤起了对*《重复冗员部》*（The Department of Redundancy Department）的温馨回忆。恰如其分的是，这个类让我们的老朋友 RecursiveArrayIterator 类加班加点，对数组的所有层级执行**深度**迭代：

```php
$deep = new RecursiveIteratorIterator($shallow);
```

## 工作原理...

作为一个实用示例，你可以开发一个测试脚本，使用迭代器来实现过滤和分页。对于这个演示，你可以调用 `chap_03_developing_functions_filtered_and_paginated.php` 测试代码文件。

首先，遵循最佳实践，将上述描述的函数放入一个名为 `chap_03_developing_functions_iterators_library.php` 的包含文件中。在测试脚本中，确保包含此文件。

数据源是一个名为 iso_country_codes 的表，其中包含 ISO2、ISO3 和国家名称。数据库连接可以在 config/db.config.php 文件中。你也可以包含前章中讨论的 Application\Database\Connection 类：

```php
define('DB_CONFIG_FILE', '/../config/db.config.php');
define('ITEMS_PER_PAGE', [5, 10, 15, 20]);
include ( __DIR__ . '/chap_03_developing_functions_iterators_library.php');
include ( __DIR__ . '/../Application/Database/Connection.php');
```

![](img/39390f6d56c5a83b28db083a8bd5185c_94_0.png)

接下来，你可以处理国家名称和每页项目数的输入参数。当前页码将从 0 开始，可以增加（下一页）或减少（上一页）：

```php
$name   = strip_tags($_GET['name'] ?? '');
$limit  = (int) ($_GET['limit'] ?? 10);
$page   = (int) ($_GET['page'] ?? 0);
$offset = $page * $limit;
$prev   = ($page > 0) ? $page - 1 : 0;
$next   = $page + 1;
```

现在你准备好启动数据库连接并运行一个简单的 SELECT 查询。这应该放在 try {} catch {} 块中。然后，你可以将堆叠的迭代器放在 try {} 块内：

```php
try {
    $connection = new Application\Database\Connection(
        include __DIR__ . DB_CONFIG_FILE);
    $sql        = 'SELECT * FROM iso_country_codes';
    $arrayIterator = fetchCountryName($sql, $connection);
    $filteredIterator = nameFilterIterator($arrayIterator, $name);
    $limitIterator = pagination(
        $filteredIterator, $offset, $limit);
} catch (Throwable $e) {
    echo $e->getMessage();
}
```

现在我们可以准备 HTML 了。在这个简单的示例中，我们提供了一个表单，让用户选择每页的项目数和国家名称：

```html
<form>
    Country Name:
<input type="text" name="name"
             value="<?= htmlespecialchars($name) ?>">
Items Per Page:
<select name="limit">
    <?php foreach (ITEMS_PER_PAGE as $item) : ?>
        <option<?= ($item == $limit) ? ' selected' : ' ?>>
            <?= $item ?></option>
    <?php endforeach; ?>
</select>
<input type="submit" />
</form>
<a href="?name=<?= $name ?>&limit=<?= $limit ?>
           &page=<?= $prev ?>">
    &lt; PREV</a>
<a href="?name=<?= $name ?>&limit=<?= $limit ?>
           &page=<?= $next ?>">
    NEXT &gt;</a>
<?= htmlList($limitIterator); ?>
```

输出看起来像这样：

![](img/39390f6d56c5a83b28db083a8bd5185c_95_0.png)

最后，为了测试国家数据库查询的递归迭代，你需要包含迭代器的库文件，以及 Application\Database\Connection 类：

```php
define('DB_CONFIG_FILE', '../config/db.config.php');
include (__DIR__ . '/chap_03_developing_functions_iterators_library.php');
include (__DIR__ . '/Application/Database/Connection.php');
```

与之前一样，你应该将数据库查询包裹在 try { } catch { } 块中。然后，你可以将测试递归迭代的代码放在 try { } 块内：

```php
try {
    $connection = new Application\Database\Connection(
        include __DIR__ . DB_CONFIG_FILE);
    $sql    = 'SELECT * FROM iso_country_codes';
    $iterator = fetchAllAssoc($sql, $connection);
    $shallow = new RecursiveArrayIterator($iterator);
    foreach ($shallow as $item) var_dump($item);
    $deep    = new RecursiveIteratorIterator($shallow);
    foreach ($deep as $item) var_dump($item);
} catch (Throwable $e) {
    echo $e->getMessage();
}
```

以下是 RecursiveArrayIterator 预期输出的示例：

![](img/39390f6d56c5a83b28db083a8bd5185c_96_0.png)

这是使用 *RecursiveIteratorIterator* 后的输出：

![](img/39390f6d56c5a83b28db083a8bd5185c_97_0.png)

## 使用生成器编写自己的迭代器

在前面的一系列配方中，我们演示了 PHP 7 SPL 中提供的迭代器的使用。但是，如果这组迭代器没有提供特定项目所需的功能怎么办？一种解决方案是开发一个函数，该函数不使用 `yield` 关键字逐步返回值来代替构建并返回数组。这样的函数被称为*生成器*。实际上，在后台，PHP 引擎会自动将你的函数转换为一个名为 *Generator* 的特殊内置类。

这种方法有几个优势。主要好处在于当你有一个大型容器需要遍历（即解析一个大文件）时。传统的方法是构建一个数组，然后返回该数组。这样做的问题是，你实际上使所需的内存量翻倍了！此外，性能也会受到影响，因为只有在最终数组返回后，结果才会实现。





## 如何实现...

在本示例中，我们将在基于迭代器的函数库基础上进行扩展，添加一个我们自己设计的生成器。在这种情况下，我们将重复前面迭代器章节中描述的功能，在该功能中我们堆叠了 `ArrayIterator`、`FilterIterator` 和 `LimitIterator`。

由于我们需要访问源数组、期望的过滤器、页码以及每页项目数，我们将适当的参数包含在单个 `filteredResultsGenerator()` 函数中。然后，我们根据页码和限制（即每页项目数）计算偏移量。接下来，我们遍历数组，应用过滤器，如果尚未达到偏移量则继续循环，如果已达到限制则中断循环：

```php
function filteredResultsGenerator(array $array, $filter, $limit = 10, $page = 0)
{
    $max    = count ($array);
    $offset = $page * $limit;

    foreach ($array as $key => $value) {
        if (!strpos($value, $filter) !== FALSE) continue;
        if (--$offset >= 0) continue;
        if (--$limit <= 0) break;
        yield $value;
    }
}
```

你会注意到，这个函数与其他函数的主要区别在于 **yield** 关键字。这个关键字的作用是向 PHP 引擎发出信号，生成一个 Generator 实例并封装代码。

## 工作原理...

为了演示 `filteredResultsGenerator()` 函数的使用，我们将让你实现一个 web 应用程序，该应用程序扫描 web 页面并生成从 `HREF` 属性中悬停获取的经过过滤和分页的 URL 列表。

首先，你需要将 `filteredResultsGenerator()` 函数的代码添加到之前配方中使用的库文件中，然后将之前描述的函数放入包含文件 `chap_03_developing_functions_iterators_library.php` 中。

接下来，定义一个测试脚本 `chap_03_developing_functions_using_generator.php`，该脚本既包含函数库，也包含定义在 *第 1 章，构建基础* 中描述的 `Application\Web\Hoover` 的文件：

```php
include ( _DIR_ , DIRECTORY_SEPARATOR . 'chap_03_developing_functions_iterators_library.php');
include ( _DIR_ . '/../Application/Web/Hover.php');
```

然后你需要从用户那里收集输入信息，包括要扫描的 URL、用作过滤器的字符串、每页项目数以及当前页码。

> **null coalesce** 运算符 (??) 非常适合从 Web 获取输入。如果未定义，它不会生成任何通知。如果未从用户输入中接收到参数，你可以提供一个默认值。

```php
$url    = trim(strip_tags($_GET['url'] ?? ''));
$filter = trim(strip_tags($_GET['filter'] ?? ''));
$limit  = (int) ($_GET['limit'] ?? 10);
$page   = (int) ($_GET['page'] ?? 0);
```

> **最佳实践**
>
> Web 安全应始终作为优先考量。在本示例中，你可以使用 `strip_tags()` 并将数据类型强制转换为整数 (`int`) 作为措施来清理用户输入。

然后你可以定义用于分页列表中上一页和下一页链接的变量。注意，你还可以应用*健全性检查*以确保下一页不会超出结果集的末尾。为了简洁起见，本示例中未应用此类健全性检查：

```php
$next   = $page + 1;
$prev   = $page - 1;
$base   = '?url=' . htmlspecialchars($url)
         . '&filter=' . htmlspecialchars($filter)
         . '&limit=' . $limit
         . '&page=';
```

然后我们需要创建一个 `Application\Web\Hover` 实例并从目标 URL 中抓取 `HREF` 属性：

```php
$vac   = new Application\Web\Hover();
$list  = $vac->getAttribute($url, 'href');
```

最后，我们定义渲染输入表单并通过之前描述的 htmlList() 函数运行我们的生成器的 HTML 输出：

```html
<form>
  <table>
    <tr>
      <th>URL</th>
      <td>
        <input type="text" name="url"
          value="<?= htmlspecialchars($url) ?>"/>
      </td>
    </tr>
    <tr>
      <th>Filter</th>
      <td>
        <input type="text" name="filter"
          value="<?= htmlspecialchars($filter) ?>"/>
      </td>
    </tr>
    <tr>
      <th>Limit</th>
      <td>
        <input type="text" name="limit" value="<?= $limit ?>"/>
      </td>
    </tr>
    <tr>
      <th>&nbsp;</th>
      <td>
        <input type="submit" />
      </td>
    </tr>
    <tr>
      <td>&nbsp;</td>
      <td>
        <a href="<?= $base . $prev ?>">&lt;- PREV |
        <a href="<?= $base . $next ?>">NEXT --></td>
    </tr>
  </table>
</form>
<hr>
<?= htmlList(filteredResultsGenerator(
  $list, $filter, $limit, $page)); ?>
```

以下是输出的示例：

![](img/39390f6d56c5a83b28db083a8bd5185c_101_0.png)

# 4 使用 PHP 面向对象编程

在本章中，我们将涵盖以下内容：

- 开发类
- 扩展类
- 使用静态属性和方法
- 使用命名空间
- 定义可见性
- 使用接口
- 使用特征
- 实现匿名类

## 简介

在本章中，我们将考虑利用 PHP 7.0、7.1 及以上版本中可用的 **面向对象编程 (OOP)** 功能的配方。PHP 7.x 中可用的大多数 OOP 功能在 PHP 5.6 中也可用。PHP 7 引入的新功能是对 **匿名类** 的支持。在 PHP 7.1 中，你可以修改类常量的可见性。

另一个彻底的新功能是能够 **捕获** 某些类型的错误。这在 *第 13 章，最佳实践、测试和调试* 中有更详细的讨论。

## 开发类

传统的开发方法是将类放入其自己的文件中。通常，类包含实现单一用途的逻辑。类进一步分解为自包含的函数，称为 **方法**。在类内部定义的变量称为 **属性**。建议在开发测试类时同步进行，这是 *第 13 章，最佳实践、测试和调试* 中更详细讨论的主题。

### 如何实现...

1. 创建一个包含类定义的文件。为了自动加载的目的，建议文件名与类名匹配。在文件顶部，在关键字 *class* 之前，添加一个 **DocBlock**。然后你可以定义属性和方法。在本示例中，我们定义一个类 *Test*。它有一个属性 `$test` 和一个方法 `getTest()`：

```php
<?php
declare(strict_types=1);
/**
 * This is a demonstration class.
 *
 * The purpose of this class is to get and set
 * a protected property $test
 */
class Test
{

    protected $test = 'TEST';

    /**
     * This method returns the current value of $test
     *
     * @return string $test
     */
    public function getTest(): string
    {
        return $this->test;
    }
}
```

```php
/**
 * This method sets the value of $test
 *
 * @param string $test
 * @return Test $this
 */
public function setTest(string $test)
{
    $this->test = $test;
    return $this;
}
```

**最佳实践**

以类名命名文件被认为是一种最佳实践。尽管 PHP 中的类名不区分大小写，但使用大写字母作为类名的第一个字母也被认为是一种最佳实践。你不应该在类定义文件中放入可执行代码。

每个类在关键字 class 之前都应该包含一个 **DocBlock**。在 DocBlock 中，你应该包含类目的简短描述。跳过一行，然后包含更详细的描述。你还可以包括 @tags，如 @author、@license 等。每个方法同样应该由 DocBlock 跟随，该 DocBlock 识别方法的用途，以及其传入参数和返回值。

2. 可以在一个文件中定义多个类，但这不被认为是一种最佳实践。在本示例中，我们创建一个文件 NameAddress.php，定义两个类 Name 和 Address：

```php
<?php
declare (strict_types=1);
class Name
{
    protected $name = '';

    public function getName() : string
    {
        return $this->name;
    }

    public function setName(string $name)
    {


$this->name = $name;

    return $this;
}
}

class Address
{
    protected $address = '';

    public function getAddress() : string
    {
        return $this->address;
    }

    public function setAddress(string $address)
    {
        $this->address = $address;
        return $this;
    }
}

![](img/39390f6d56c5a83b28db083a8bd5185c_106_0.png)

3.  类名不区分大小写。重复定义会被标记为错误。在此示例中，在文件 `TwoClass.php` 中，我们定义了两个类，`TwoClass` 和 `twoclass`：

```php
<?php
class TwoClass
{
    public function showOne()
    {
        return 'ONE';
    }
}

// 在解析第二个类定义时会发生致命错误
class twoclass
{
    public function showTwo()
    {
        return 'TWO';
    }
}
```

4.  PHP 7.1 解决了关键词 `$this` 使用中不一致的行为。虽然在 PHP 7.0 和 PHP 5.x 中是允许的，但从 PHP 7.1 开始，如果将 `$this` 用于以下任何用途，现在都会产生错误：
- 作为参数
- 作为静态变量
- 作为全局变量
- 作为 `try...catch` 块中使用的变量
- 作为 `foreach()` 中使用的变量
- 作为 `unset()` 的参数
- 作为变量（即，`$a = 'this'; echo $sa`）
- 通过引用间接使用

5.  如果你需要创建对象实例，但不想定义一个离散的类，可以使用内置于 PHP 中的通用 `stdClass`。`stdClass` 允许你在定义类时即时定义属性，而无需定义一个继承自 `stdClass` 的离散类：
`$obj = new stdClass();`

6.  此设施在 PHP 中的许多不同位置都有使用。例如，当你使用 PHP 数据对象（PDO）进行数据库查询时，一种获取模式是 `PDO::FETCH_OBJ`。此模式返回 `stdClass` 的实例，其中的属性代表数据库表的列：
`$stmt = $connection->pdo->query($sql);`
`$row = $stmt->fetch(PDO::FETCH_OBJ);`

## 工作原理...

取前面代码片段中所示的 `Test` 类示例，并将代码放在名为 `Test.php` 的文件中。创建另一个名为 `chap_04_oop_defining_class_test.php` 的文件。添加以下代码：

```php
require __DIR__ . '/Test.php';

$test = new Test();
echo $test->getTest();
echo PHP_EOL;
```

`$test->setTest('ABC');`
`echo $test->getTest();`
`echo PHP_EOL;`

输出将显示 `$test` 属性的初始值，然后是调用 `setTest()` 修改后的新值：

![](img/39390f6d56c5a83b28db083a8bd5185c_108_0.png)

下一个示例要求你在单个文件 `NameAddress.php` 中定义两个类，`Name` 和 `Address`。你可以使用以下代码调用和使用这两个类：

```php
require __DIR__ . '/NameAddress.php';

$name = new Name();
$name->setName('TEST');
$addr = new Address();
$addr->setAddress('123 Main Street');

echo $name->getName() . ' lives at ' . $addr->getAddress();
```

> 虽然 PHP 解释器不会生成错误，但通过定义多个类，文件的逻辑纯粹性受到了损害。此外，文件名与类名不匹配，这可能会影响自动加载的能力。

此示例的输出如下所示：

![](img/39390f6d56c5a83b28db083a8bd5185c_109_0.png)

步骤 3 也展示了在一个文件中有两个类定义。然而，在这种情况下，目的是演示 PHP 中的类名不区分大小写。将代码放入文件 `TwoClass.php`。当你尝试包含该文件时，会生成错误：

![](img/39390f6d56c5a83b28db083a8bd5185c_109_1.png)

为了演示 `stdClass` 的直接使用，创建一个实例，为属性赋值，并使用 `var_dump()` 显示结果。若要查看 `stdClass` 在内部如何使用，使用 `var_dump()` 显示 PDO 查询的结果，其中获取模式设置为 `FETCH_OBJ`。

输入以下代码：

```php
$obj = new stdClass();
$obj->test = 'TEST';
echo $obj->test;
echo PHP_EOL;

include (__DIR__ . './../Application/Database/Connection.php');
$connection = new Application\Database\Connection(
    include __DIR__ . DB_CONFIG_FILE);

$sql = 'SELECT * FROM iso_country_codes';
$stmt = $connection->pdo->query($sql);
$row = $stmt->fetch(PDO::FETCH_OBJ);
var_dump($row);
```

输出如下：

![](img/39390f6d56c5a83b28db083a8bd5185c_110_0.png)

## 参见...

有关 PHP 7.1 中关于关键词 `$this` 改进的更多信息，请参阅 https://wiki.php.net/rfc/this_var。

## 扩展类

开发人员使用面向对象编程（OOP）的主要原因之一是其能够重用现有代码，同时添加或覆盖功能。在 PHP 中，使用关键词 `extends` 来建立类之间的父/子关系。

## 操作步骤...

1.  在子类中使用关键词 `extends` 来设置继承。在以下示例中，`Customer` 类扩展 `Base` 类。`Customer` 的任何实例都将继承可见的方法和属性，在本例中为 `$id`、`getId()` 和 `setId()`：

```php
class Base
{
    protected $id;
    public function getId()
    {
        return $this->id;
    }
    public function setId($id)
    {
        $this->id = $id;
    }
}

class Customer extends Base
{
    protected $name;
    public function getName()
    {
        return $this->name;
    }
    public function setName($name)
    {
        $this->name = $name;
    }
}
```

2.  你可以强制任何使用你类的开发人员定义一个方法，方法是将其标记为抽象。在此示例中，`Base` 类将 `validate()` 方法定义为抽象。之所以必须是抽象的原因是因为从父类 `Base` 的角度来看，不可能确切确定子类是如何被验证的：

```php
abstract class Base
{
    protected $id;
    public function getId()
    {
        return $this->id;
    }
    public function setId($id)
    {
        $this->id = $id;
    }
    public function validate();
}
```

> 如果类包含一个**抽象方法**，该类本身必须声明为抽象类。

3.  PHP 仅支持单重继承。下一个示例展示了一个类 `Member`，它继承自 `Customer`。`Customer` 反过来继承自 `Base`：

```php
class Base
{
    protected $id;
    public function getId()
    {
        return $this->id;
    }
    public function setId($id)
    {
        $this->id = $id;
    }
}

class Customer extends Base
{
    protected $name;
    public function getName()
    {
        return $this->name;
    }
    public function setName($name)
    {
        $this->name = $name;
    }
}

class Member extends Customer
{
    protected $membership;
    public function getMembership()
    {
        return $this->membership;
    }
    public function setMembership($memberId)
    {
        $this->membership = $memberId;
    }
}
```

4.  为了满足类型提示，可以使用目标类的任何子类。在以下代码片段中显示的 `test()` 函数要求一个 `Base` 类的实例作为参数。继承链中的任何类都可以作为参数接受。传递给 `test()` 的其他任何内容都会抛出 `TypeError`：

```php
function test(Base $object)
{
    return $object->getId();
}
```

## 工作原理...

在第一点中，定义了一个 `Base` 类和一个 `Customer` 类。为了演示，将这两个类定义放在单个文件 `chap_04_oop_extends.php` 中，并添加以下代码：

```php
$customer = new Customer();
$customer->setId(100);
$customer->setName('Fred');
var_dump($customer);
```

注意 `$id` 属性以及 `getId()` 和 `setId()` 方法是从父类 `Base` 继承到子类 `Customer` 的：

![](img/39390f6d56c5a83b28db083a8bd5185c_113_0.png)

为了说明抽象方法的使用，假设你希望为任何扩展 `Base` 的类添加某种验证功能。问题在于，无法知道在继承类中可能会验证什么。唯一确定的是，你必须具备验证功能。

采用前面解释中提到的相同的 `Base` 类并添加一个新方法 `validate()`。将该方法标记为*抽象*，并且不要定义任何代码。注意当子类 `Customer` 扩展 `Base` 时发生了什么。

![](img/39390f6d56c5a83b28db083a8bd5185c_114_0.png)

如果你随后将 `Base` 类标记为*抽象*，但未在子类中定义 `validate()` 方法，则会生成*相同的错误*。最后，直接在子类 `Customer` 中实现 `validate()` 方法：

```php
class Customer extends Base
{
    protected $name;
    public function getName()
    {
        return $this->name;
    }
    public function setName($name)
    {
        $this->name = $name;
    }
    public function validate()
    {
        $valid = 0;
        $count = count(get_object_vars($this));
    }
}
```





## 使用 PHP 面向对象编程

代码继续自上一步：

```php
if (!empty($this->id) && is_int($this->id)) $valid++;
if (!empty($this->name)
  && preg_match('/[a-z0-9]/i', $this->name)) $valid++;
return ($valid == $count);
}
```

然后你可以添加以下过程式代码来测试结果：

```php
$customer = new Customer();

$customer->setId(100);
$customer->setName('Fred');
echo "Customer [id]: {$customer->getName()}" .
     " [{$customer->getId()}]\n";
echo ($customer->validate() ? 'VALID' : 'NOT VALID');
$customer->setId('XXX');
$customer->setName('$%E&*(');
echo "Customer [id]: {$customer->getName()}" .
     " [{$customer->getId()}]\n";
echo ($customer->validate() ? 'VALID' : 'NOT VALID');
```

输出结果如下：

![](img/39390f6d56c5a83b28db083a8bd5185c_115_0.png)

为了展示单行继承，请在前面步骤 1 中显示的 Base 和 Customer 第一个示例中添加一个新的 Member 类：

```php
class Member extends Customer
{
  protected $membership;
  public function getMembership()
  {
    return $this->membership;
  }
  public function setMembership($memberId)
  {
    $this->membership = $memberId;
  }
}
```

创建一个 Member 实例，并注意在以下代码中，所有属性和方法都可以从每个继承的类中访问，即使它们不是直接继承的：

```php
$member = new Member();
$member->setId(100);
$member->setName('Fred');
$member->setMembership('A299F322');
var_dump($member);
```

输出结果如下：

![](img/39390f6d56c5a83b28db083a8bd5185c_116_0.png)

现在定义一个函数 test()，它接受一个 Base 实例作为参数：

```php
function test(Base $object)
{
    return $object->getId();
}
```

请注意，Base、Customer 和 Member 的实例都可以作为参数接受：

```php
$base = new Base();
$base->setId(100);

$customer = new Customer();
$customer->setId(101);

$member = new Member();
$member->setId(102);

// 所有 3 个类都适用于 test()
echo test($base)      . PHP_EOL;
echo test($customer)  . PHP_EOL;
echo test($member)    . PHP_EOL;
```

输出结果如下：

![](img/39390f6d56c5a83b28db083a8bd5185c_117_0.png)

然而，如果你试图使用不在继承链中的对象实例来运行 test()，则抛出 TypeError：

```php
class Orphan
{
    protected $id;
    public function getId()
    {
        return $this->id;
    }
    public function setId($id)
    {
        $this->id = $id;
    }
}
try {
    $orphan = new Orphan();
    $orphan->testid(103);
    echo test($orphan) . PHP_EOL;
} catch (TypeError $e) {
    echo 'Does not work!' . PHP_EOL;
    echo $e->getMessage();
}
```

我们在下图中可以观察到这一点：

![](img/39390f6d56c5a83b28db083a8bd5185c_118_0.png)

## 使用静态属性和方法

PHP 允许你在不创建类实例的情况下访问属性或方法。用于此目的的关键词是 **static**。

### 操作步骤...

- 1. 最简单的情况是，在声明普通属性或方法时，在声明可见性级别后添加 *static* 关键词。使用 *self* 关键词在内部引用该属性：

```php
class Test
{
    public static $test = 'TEST';
    public static function getTest()
    {
        return self::$test;
    }
}
```

- 2. *self* 关键词会早期绑定，这在访问子类中的静态信息时会导致问题。如果你绝对需要访问来自子类的信息，请在使用 *self* 的地方使用 *static* 关键词。这个过程被称为 **Late Static Binding**（晚静态绑定）。

- 3. 在以下示例中，如果你 `echo Child::getEarlyTest()`，输出将是 **TEST**。如果另一方面你运行 `Child::getLateTest()`，输出将是 **CHILD**。原因是 PHP 在使用 *self* 时会绑定到 *最早* 的定义，而对于 *static* 关键词使用的是 *最新* 的绑定：

```php
class Test2
{
    public static $test = 'TEST2';
    public static function getEarlyTest()
    {
        return self::$test;
    }
    public static function getLateTest()
    {
        return static::$test;
    }
}

class Child extends Test2
{
    public static $test = 'CHILD';
}
```

- 4. 在许多情况下，**工厂**设计模式与静态方法结合使用，根据给定的不同参数生成对象实例。在本例中，定义了一个静态方法 `factory()`，它返回一个 PDO 连接：

```php
public static function factory(
        $driver, $dbname, $host, $user, $pwd, $options = [])
{
    $dsn = sprintf('%s:dbname=%s;host=%s',
        $driver, $dbname, $host);
    try {
        return new PDO($dsn, $user, $pwd, $options);
    } catch (PDOException $e) {
        error_log($e->getMessage());
    }
}
```

## 工作原理...

你可以使用**类解析运算符** "::" 来引用静态属性和方法。给定前面显示的 Test 类，如果你运行此代码：

```php
echo Test::$test;
echo PHP_EOL;
echo Test::getTest();
echo PHP_EOL;
```

你将看到此输出：

![](img/39390f6d56c5a83b28db083a8bd5185c_120_0.png)

为了说明晚静态绑定，基于前面显示的 Test2 和 Child 类，尝试此代码：

```php
echo Test2::$test;
echo PHP_EOL;
echo Child::$test;
echo PHP_EOL;
echo Child::getEarlyTest();
echo PHP_EOL;
echo Child::getLateTest();
echo PHP_EOL;
```

输出说明了 *self* 和 *static* 之间的区别：

![](img/39390f6d56c5a83b28db083a8bd5185c_121_0.png)

最后，为了测试前面显示的 factory() 方法，将代码保存为 `Application\Database` 文件夹中 `Connection.php` 文件中的 `Application\Database\Connection` 类。然后你可以尝试此操作：

```php
include __DIR__ . '/../Application/Database/Connection.php';
use Application\Database\Connection;
$connection = Connection::factory(
    'mysql', 'php\'cookbook\'', 'localhost', 'test', 'password'
);
$stmt = $connection->query('SELECT name FROM iso_country_codes');
while ($country = $stmt->fetch(PDO::FETCH_COLUMN))
    echo $country . ' ';
```

你将看到从示例数据库中拉取的国家列表：

![](img/39390f6d56c5a83b28db083a8bd5185c_121_1.png)

### 参见

有关晚静态绑定的更多信息，请参见 PHP 文档中的此说明：

```text
http://php.net/manual/en/language.oop5.late-static-bindings.php
```

## 使用命名空间

对高级 PHP 开发至关重要的一点是命名空间的使用。任意定义的命名空间成为类名的前缀，从而避免了意外类重复的问题，并赋予你极大的开发自由度。使用命名空间的另一个好处是，假设它匹配目录结构，它有助于自动加载，如 *第 1 章，构建基础* 中所述。

### 操作步骤...

- 1. 要在命名空间内定义一个类，只需在代码文件的顶部添加 `namespace` 关键词：

```php
namespace Application\Entity;
```

![](img/39390f6d56c5a83b28db083a8bd5185c_122_0.png)

> **最佳实践**
> 与每个文件只应有一个类的建议一样，每个文件也应只有一个命名空间。

- 2. 在 `namespace` 关键词之前，应该出现的唯一 PHP 代码是注释和/或 `declare` 关键词：

```php
<?php
declare(strict_types=1);
namespace Application\Entity;
/**
 * Address
 */
class Address
{
  // some code
}
```

- 3. 在 PHP 5 中，如果你需要访问外部命名空间中的类，你可以在前面添加一个仅包含命名空间的 `use` 语句。然后你需要在这个命名空间内为任何类引用添加命名空间最后一个组件作为前缀：

```php
use Application\Entity;
$name = new Entity\Name();
$addr = new Entity\Address();
$prof = new Entity\Profile();
```

- 4. 或者，你可以明确指定所有三个类：

```php
use Application\Entity\Name;
use Application\Entity\Address;
use Application\Entity\Profile;
$name = new Name();
$addr = new Address();
$prof = new Profile();
```

- 5. PHP 7 引入了一种称为 `group use` 的语法改进，大大改善了代码可读性：

```php
use Application\Entity\ {
    Name,
    Address,
    Profile
};
$name = new Name();
$addr = new Address();
$prof = new Profile();
```

- 6. 如第 1 章 *构建基础* 中所述，命名空间是**自动加载**过程的组成部分。此示例显示了一个演示自动加载器，它回显传入的参数，然后尝试基于命名空间和类名包含一个文件。这假设目录结构与命名空间匹配：

```php
function __autoload($class)
{
    echo "Argument Passed to Autoloader = $class\n";
    include __DIR__ . '/../' . str_replace(
        '\\', DIRECTORY_SEPARATOR, $class) . '.php';
}
```




## 使用 PHP 面向对象编程

## 工作原理...

为了说明目的，定义一个与 `Application\*` 命名空间相匹配的目录结构。创建一个基础文件夹 *Application*，以及一个子文件夹 *Entity*。你也可以根据需要包含其他子文件夹，例如在其他章节中使用的 *Database* 和 *Generic*：

![](img/39390f6d56c5a83b28db083a8bd5185c_124_0.png)

接下来，在 *Application/Entity* 文件夹下创建三个实体类，每个类放在各自的文件中：*Name.php*、*Address.php* 和 *Profile.php*。这里我们仅展示 `Application\Entity\Name`。`Application\Entity\Address` 和 `Application\Entity\Profile` 的结构相同，区别在于 Address 拥有 $address 属性，而 Profile 拥有 $profile 属性，并且每个属性都有相应的 getter 和 setter 方法：

```php
<?php
declare(strict_types=1);
namespace Application\Entity;

/**
 * Name
 *
 */
class Name
{
    protected $name = '';

    /**
     * This method returns the current value of $name
     *
     * @return string $name
     */
    public function getName() : string
    {
        return $this->name;
    }

    /**
     * This method sets the value of $name
     *
     * @param string $name
     * @return name $this
     */
    public function setName(string $name)
    {
        $this->name = $name;
        return $this;
    }
}
```

然后，你可以使用 *第 1 章，构建基础* 中定义的自动加载器，或使用前面提到的简单自动加载器。将设置自动加载的命令放入一个文件，`chap_04_oop_namespace_example_1.php`。在此文件中，你可以指定一个 use 语句，该语句仅引用命名空间，而不引用类名。通过用命名空间的最后一部分 `Entity` 作为类名前缀，创建三个实体类 `Name`、`Address` 和 `Profile` 的实例：

```php
use Application\Entity;
$name = new Entity\Name();
$addr = new Entity\Address();
$prof = new Entity\Profile();

var_dump($name);
var_dump($addr);
var_dump($prof);
```

输出如下：

![](img/39390f6d56c5a83b28db083a8bd5185c_125_0.png)

接下来，使用 **另存为** 功能将文件复制到一个名为 `chap_04_oop_namespace_example_2.php` 的新文件中。将 `use` 语句更改为以下内容：

```php
use Application\Entity\Name;
use Application\Entity\Address;
use Application\Entity\Profile;
```

现在，你只需使用类名即可创建类实例：

```php
$name = new Name();
$addr = new Address();
$prof = new Profile();
```

运行此脚本时，输出如下：

![](img/39390f6d56c5a83b28db083a8bd5185c_126_0.png)

最后，再次运行 **另存为** 并创建一个新文件，`chap_04_oop_namespace_example_3.php`。你现在可以测试在 PHP 7 中引入的**组使用（group use）** 功能：

```php
use Application\Entity\{
    Name,
    Address,
    Profile
};

$name = new Name();
$addr = new Address();
$prof = new Profile();
```

同样，当你运行这段代码时，输出将与上述输出相同：

```text
Terminal
Argument Passed to Autoloader = Application\Entity\Name
Argument Passed to Autoloader = Application\Entity\Address
Argument Passed to Autoloader = Application\Entity\Profile
class Application\Entity\Name#1 () {
    protected $name =>
        string(0) ""
}
class Application\Entity\Address#2 () {
    protected $address =>
        string(0) ""
}
class Application\Entity\Profile#3 () {
    protected $profile =>
        string(0) ""
}
--------------------------
(program exited with code: 0)
Press return to continue
```

## 定义可见性

具有欺骗性的是，*可见性* 这个词与应用安全毫无关系！它只是一个用于控制代码使用的机制。它可以用来引导经验不足的开发者避免使用那些仅应在类定义内部调用的方法的 *public*（公共）访问。

### 具体做法...

- 通过在属性或方法定义前添加 `public`、`protected` 或 `private` 关键字来指示可见性级别。你可以将属性标记为 `protected` 或 `private`，以强制仅通过公共的 getter 和 setter 进行访问。

- 在此示例中，定义了一个包含 `protected` 属性 `$id` 的 `Base` 类。为了访问此属性，定义了公共方法 `getId()` 和 `setId()`。`protected` 方法 `generateRandId()` 可以在内部使用，并会被 `Customer` 子类继承。此方法不能在类定义外部直接调用。请注意使用新的 PHP 7 `random_bytes()` 函数来生成随机 ID。

```php
class Base
{
    protected $id;
    private $key = 12345;

    public function getId()
    {
        return $this->id;
    }

    public function setId()
    {
        $this->id = $this->generateRandId();
    }

    protected function generateRandId()
    {
        return unpack('H*', random_bytes(8))[1];
    }
}

class Customer extends Base
{
    protected $name;
    public function getName()
    {
        return $this->name;
    }
    public function setName($name)
    {
        $this->name = $name;
    }
}
```

> **最佳实践**
> 将属性标记为 *protected*，并定义公共的 `getNameOfProperty()` 和 `setNameOfProperty()` 方法来控制属性的访问。这类方法被称为 *getter*（获取器）和 *setter*（设置器）。

- 将属性或方法标记为 *private*，以防止其被继承或从类定义外部可见。这是创建**单例（singleton）**类的一种好方法。

- 下一个代码示例展示了一个 *Registry* 类，该类只能有一个实例。因为构造函数被标记为 *private*，所以创建实例的唯一方式是通过静态方法 `getInstance()`：

```php
class Registry
{
    protected static $instance = NULL;
    protected $registry = array();
    private function __construct()
    {
    }

    public static function getInstance()
    {
        if (!self::$instance) {
            self::$instance = new self();
        }
        return self::$instance;
    }

    public function __get($key)
    {
        return $this->registry[$key] ?? NULL;
    }

    public function __set($key, $value)
    {
        $this->registry[$key] = $value;
    }
}
```

![](img/39390f6d56c5a83b28db083a8bd5185c_129_0.png)

> 你可以将方法标记为 **final** 以防止其被重写。将类标记为 **final** 以防止其被扩展。

- 通常，类常量被认为具有公共可见性级别。从 PHP 7.1 开始，你可以将类常量声明为 *protected* 或 *private*。在以下示例中，TEST_WHOLE_WORLD 类常量的行为与 PHP 5 中完全相同。接下来的两个常量 TEST_INHERITED 和 TEST_LOCAL 遵循与任何受保护或私有属性或方法相同的规则：

```php
class Test
{
    public const TEST_WHOLE_WORLD   = 'visible.everywhere';

    // NOTE: only works in PHP 7.1 and above
    protected const TEST_INHERITED = 'visible.in.child.classes';

    // NOTE: only works in PHP 7.1 and above
    private const TEST_LOCAL= 'local.to.class.Test.only';

    public static function getTestInherited()
    {
        return static::TEST_INHERITED;
    }

    public static function getTestLocal()
    {
        return static::TEST_LOCAL;
    }
}
```

## 工作原理...

创建文件 `chap_04_basic_visibility.php` 并定义两个类：Base 和 Customer。接下来，编写代码来创建每个类的实例：

```php
$base        = new Base();
$customer = new Customer();
```

注意，以下代码运行正常，实际上也被认为是最佳实践：

```php
$customer->setId();
$customer->setName('Test');
echo 'Welcome ' . $customer->getName() . PHP_EOL;
echo 'Your new ID number is: ' . $customer->getId() . PHP_EOL;
```

尽管 $id 是受保护的，但相应的方法 getId() 和 setId() 都是公共的，因此可以从类定义外部访问。输出如下：

![](img/39390f6d56c5a83b28db083a8bd5185c_130_0.png)

然而，以下代码行将不会工作，因为私有和受保护的属性无法从类定义外部访问：

```php
echo 'Key (does not work): ' . $base->key;
echo 'Key (does not work): ' . $customer->key;
echo 'Name (does not work): ' . $customer->name;
echo 'Random ID (does not work): ' . $customer->generateRandId();
```

以下输出显示了预期的错误：

![](img/39390f6d56c5a83b28db083a8bd5185c_131_0.png)

## 参见

有关 getter 和 setter 的更多信息，请参见本章中名为“使用 getter 和 setter”的食谱。有关 PHP 7.1 类常量可见性设置的更多信息，请参阅 https://wiki.php.net/rfc/class_const_visibility。

## 使用接口

接口对于系统架构师来说是实用的工具，通常用于创建应用程序编程接口（API）的原型。接口不包含实际代码，但包含方法名以及方法签名。

> 接口中识别的所有方法的可见性级别均为 public。



## 实现方法…

- 1. 接口中定义的方法不能包含实际的代码实现。不过，你可以指定方法参数的数据类型。
- 2. 在本示例中，**ConnectionAwareInterface** 定义了一个方法 **setConnection()**，**该方法需要一个 Connection 实例作为参数：**

```php
interface ConnectionAwareInterface
{
    public function setConnection(Connection $connection);
}
```

- 3. 要使用该接口，请在定义类的起始行后添加关键字 **implements**。我们定义了两个类，**CountryList** 和 **CustomerList**，这两个类都需要通过方法 **setConnection()** 访问 **Connection** 类。为了标识这种依赖关系，这两个类都实现了 **ConnectionAwareInterface**：

```php
class CountryList implements ConnectionAwareInterface
{
    protected $connection;

    public function setConnection(Connection $connection)
    {
        $this->connection = $connection;
    }

    public function list()
    {
        $list = [];
        $stmt = $this->connection->pdo->query(
            'SELECT iso3, name FROM iso_country_codes');
        while ($country = $stmt->fetch(PDO::FETCH_ASSOC)) {
            $list[$country['iso3']] = $country['name'];
        }
        return $list;
    }
}

class CustomerList implements ConnectionAwareInterface
{
    protected $connection;

    public function setConnection(Connection $connection)
    {
        $this->connection = $connection;
    }

    public function list()
    {
        $list = [];
        $stmt = $this->connection->pdo->query(
            'SELECT id, name FROM customer');
        while ($customer = $stmt->fetch(PDO::FETCH_ASSOC)) {
            $list[$customer['id']] = $customer['name'];
        }
        return $list;
    }
}
```

- 4. 接口可用于满足类型提示。下面的类 `ListFactory` 包含一个 `factory()` 方法，该方法可以初始化任何实现了 `ConnectionAwareInterface` 的类。该接口保证 `setConnection()` 方法已被定义。将类型提示设置为接口而非特定的类实例，会使工厂方法更具通用性：

```php
namespace Application\Generic;

use PDO;
use Exception;
use Application\Database\Connection;
use Application\Database\ConnectionAwareInterface;

class ListFactory
{
    const ERROR_AWARE = 'Class must be Connection Aware';

    public static function factory(ConnectionAwareInterface $class, $dbParams)
    {
        if ($class instanceof ConnectionAwareInterface) {
            $class->setConnection(new Connection($dbParams));
            return $class;
        } else {
            throw new Exception(self::ERROR_AWARE);
        }
        return FALSE;
    }
}
```

- 5. 如果一个类实现了多个接口，当方法签名不匹配时会发生**命名冲突**。在本示例中，有两个接口：`DateAware` 和 `TimeAware`。除了定义 `setDate()` 和 `setTime()` 方法外，它们都定义了 `setBoth()`。拥有重复的方法名本身不是问题，尽管这不被视为最佳实践。问题在于方法签名不同：

```php
interface DateAware
{
    public function setDate($date);
    public function setBoth(DateTime $dateTime);
}

interface TimeAware
{
    public function setTime($time);
    public function setBoth($date, $time);
}

class DateTimeHandler implements DateAware, TimeAware
{
    protected $date;
    protected $time;

    public function setDate($date)
    {
        $this->date = $date;
    }

    public function setTime($time)
    {
        $this->time = $time;
    }

    public function setBoth(DateTime $dateTime)
    {
        $this->date = $dateTime;
    }
}
```

按照目前的代码块，将会生成一个致命错误（无法捕获）。为了解决这个问题，推荐的做法是从其中一个接口中移除 `setBoth()` 的定义。或者，你可以调整方法签名使其匹配。

> **最佳实践**
> 不要定义具有重复或重叠方法定义的接口。

### 工作原理…

在 `Application/Database` 文件夹中，创建一个文件 `ConnectionAwareInterface.php`。插入前面步骤 2 中讨论的代码。

接下来，在 `Application/Generic` 文件夹中，创建两个文件 `CountryList.php` 和 `CustomerList.php`。插入步骤 3 中讨论的代码。

接下来，在与 `Application` 目录平级的目录中，创建一个源代码文件 `chap_04_oop_simple_interfaces_example.php`，该文件用于初始化自动加载器并包含数据库参数：

```php
<?php
define('DB_CONFIG_FILE', './../config/db.config.php');
require __DIR__ . './../Application/Autoload/Loader.php';
Application\Autoload\Loader::init(__DIR__ . './../');
$params = include __DIR__ . DB_CONFIG_FILE;
```

本示例中的数据库参数假定位于由常量 `DB_CONFIG_FILE` 指示的数据库配置文件中。

现在，你可以使用 `ListFactory::factory()` 来生成 `CountryList` 和 `CustomerList` 对象。请注意，如果这些类没有实现 `ConnectionAwareInterface`，将会抛出错误：

```php
$list = Application\Generic\ListFactory::factory(
    new Application\Generic\CountryList(), $params);
foreach ($list->list() as $item) echo $item . ' ';
```

## 使用 PHP 面向对象编程

这是国家列表的输出：

```text
-----------------
Country List
-----------------
Afghanistan Albania Antarctica Algeria American Samoa Andorra Angola Antigua and Barbuda Azerbaijan Argentina Australia Austria Bahamas Bahrain Bangladesh Armenia Barbados Belgium Bermuda Bhutan Bolivia, Plurinational State of Bosnia and Herzegovina Botswana Bouvet Island Brazil Belize British Indian Ocean Territory Solomon Islands Virgin Islands, British Burundi Burkina Faso Bulgaria Myanmar Burundi Belarus Cambodia Cameroon Canada Cape Verde Cayman Islands Central African Republic Sri Lanka Chad Chile China Taiwan, Province of China Christmas Island Cocos (Keeling) Islands Colombia Comoros Mayotte Congo, Democratic Republic of the Congo Cook Islands Costa Rica Croatia Cuba Cyprus Czech Republic Benin Denmark Dominica Dominican Republic Ecuador El Salvador Equatorial Guinea Eritrea Estonia Faroe Islands Falkland Islands (Malvinas) South Georgia and the South Sandwich Islands Fiji Finland Aland Islands France French Guiana French Polynesia French Southern Territories Djibouti Gabon Georgia Gambia Palestine, State of Germany Ghana Gibraltar Kiribati Greece Greenland Grenada Guadeloupe Guam Guatemala Guinea Guyana Haiti Heard Island and McDonald Islands Holy See (Vatican City State) Honduras Hong Kong Hungary Iceland India Indonesia Iran, Islamic Republic of Iraq Ireland Israel Italy Cote d'Ivoire Jamaica Japan Kazakhstan Jordan Korea, Democratic People's Republic of Korea, Republic of Kuwait Kyrgyzstan Lao People's Democratic Republic Lebanon Lesotho Latvia Liberia Libya Liechtenstein Lithuania Luxembourg Macao Madagascar Malawi Malaysia Maldives Mali Malta
```

你还可以使用工厂方法来生成 CustomerList 对象并使用它：

```php
$list = Application\Generic\ListFactory::factory(
    new Application\Generic\CustomerList(), $params);
foreach ($list->list() as $item) echo $item . ' ';
```

这是 CustomerList 的输出：

```text
-----------------
Customer List
-----------------
Conrad Perry Lonnie Knapp Darrel Roman Morgan Avila Lee McCray Spencer Sanford Thomas Kirby Brian Crawford Armando Barlow Jess Rocha Felix Blevins Jose Carter Orlando Fulton Mitchell Roth Eduardo Wright Marc Ellis Joaquin Moses Morris Varjan Gene Cruz Samuel Harding Lauri Grimes Ceeleen Walker Tabitha Foster Cecelia Case Rhonda Kinney Elvira Giles Flossie Dyer Gabriela Davis Dolly Wong Krista Cortez Leta Solomon Matilda Barrera Tommie Horter Lenne Gillespie Camille Perez Graciela Joyner Penelope Molina Celeste Justice Lena Conway Katrina Freeman Jeff Valdoz Leonardo Parrish Roland Chong Raymond Sanford Wilfredo Taylor Dominick Cline Alonzo Sullivan Edmond Shepherd Omar Anthony Lonnie Eaton Peter Pugh Jesus Bright Ramiro Bentley Derrick Hendricks Hans Page Garrett Campos Todd Lindsey Denis Snyder Stan Rocha Dollie Hernandez Aileen Duncan Essie Shorti Ram Ruiz Isabel Rodriguez Ingrid Santos Jaime Noel Geneva Case Lucille Bradford Josefina Hampton Fannie Moore Sorcorr Jemenes Elba Mccall Louella Allan Jeanette Merritt Lana Burns Karyn Francis Blanca Le Renee Decker Obama C.T. Russel admin Leonard Nimoy
-----------------

(program exited with code: 0)
Press return to continue
```




如果您想检查在实现了多个接口且方法签名不同的情况下会发生什么，请将前面第 4 步中显示的代码输入到文件 `chap_04_oop_interfaces_collisions.php` 中。当您尝试运行该文件时，会生成一个错误，如下所示：

```text
PHP Fatal error:  Declaration of DateTimeHandler::setBoth($dateTime) must be compatible with DateTimeAware::setBoth(DateTime $dateTime) in /home/aed/Repos/php7_recipes/source/chapter04/chap_04_oop_interfaces_collisions.php on line 19
PHP Stack trace:
PHP   1. {main}() /home/aed/Repos/php7_recipes/source/chapter04/chap_04_oop_interfaces_collisions.php:0

Fatal error: Declaration of DateTimeHandler::setBoth($dateTime) must be compatible with DateTimeAware::setBoth(DateTime $dateTime) in /home/aed/Repos/php7_recipes/source/chapter04/chap_04_oop_interfaces_collisions.php on line 19

Call Stack:
0.0002    36324  1. {main}() /home/aed/Repos/php7_recipes/source/chapter04/chap_04_oop_interfaces_collisions.php:0

---------------------------------------------------
(program exited with code: 255)
Press return to continue
```

如果您在 TimeAware 接口中进行以下调整，就不会产生错误了：

```php
interface TimeAware
{
    public function setTime($time);
    // this will cause a problem
    public function setBoth(DateTime $dateTime);
}
```

## 使用特征（Traits）

如果您曾经进行过 C 语言编程，可能熟悉宏。宏是一个预定义的代码块，在指定的行处*展开*。类似地，特征（trait）可以包含代码块，这些代码块由 PHP 解释器在指定的行处复制并粘贴到类中。

### 具体操作…

- 1. 特征通过关键字 `trait` 来识别，并且可以包含属性和/或方法。您在检查前面那个使用 `CountryList` 和 `CustomerList` 类的食谱时，可能已经注意到了代码的重复。在这个示例中，我们将对这两个类进行重构，并将 `list()` 方法的功能移动到一个特征中。请注意，两个类中的 `list()` 方法是相同的。

- 2. 特征用于类之间存在代码重复的情况。然而，请注意，创建抽象类并继承它的传统方法在使用特征时可能具有某些优势。特征不能用于确定继承关系，而抽象父类可以为此目的使用。

- 3. 现在我们将 `list()` 复制到一个名为 `ListTrait` 的特征中：

```php
trait ListTrait
{
    public function list()
    {
        $list = [];
        $sql = sprintf('SELECT $s, $s FROM $s',
                       $this->key, $this->value, $this->table);
        $stmt = $this->connection->pdo->query($sql);
        while ($item = $stmt->fetch(PDO::FETCH_ASSOC)) {
            $list[$item[$this->key]] =
                $item[$this->value];
        }

        return $list;
    }
}
```

- 4. 然后，我们可以将 `ListTrait` 中的代码插入到一个新类 `CountryListUsingTrait` 中，如下面的代码片段所示。现在可以从该类中完全移除 `list()` 方法：

```php
class CountryListUsingTrait implements ConnectionAwareInterface
{
    use ListTrait;

    protected $connection;
    protected $key = 'iso3';
    protected $value = 'name';
    protected $table = 'iso_country_codes';

    public function setConnection(Connection $connection)
    {
        $this->connection = $connection;
    }
}
```

> 每当存在代码重复时，就需要进行修改时，潜在的问题就会出现。您可能会发现自己需要进行太多的全局搜索和替换操作，或者进行代码的剪切和粘贴，这往往会导致灾难性的结果。特征是避免这种维护噩梦的好方法。

- 5. **特征受命名空间的影响。** 在第 1 步所示的示例中，如果我们将新的 `CountryListUsingTrait` 类放入命名空间 `Application\Generic` 中，我们也需要将 `ListTrait` 移到该命名空间中：

```php
namespace Application\Generic;

use PDO;

trait ListTrait
{
    public function list()
    {
        // code as shown above
    }
}
```

- 6. **特征中的方法覆盖继承的方法。**

- 7. 在下面的示例中，您会注意到 `setId()` 方法的返回值在 `Base` 父类和 `Test` 特征之间是不同的。`Customer` 类继承自 `Base`，但也使用了 `Test`。在这种情况下，特征中定义的方法将覆盖父类 `Base` 中定义的方法：

```php
trait Test
{
    public function setId($id)
    {
        $obj = new stdClass();
        $obj->id = $id;
        $this->id = $obj;
    }
}

class Base
{
    protected $id;

    public function getId()
    {
        return $this->id;
    }

    public function setId($id)
    {
        $this->id = $id;
    }
}

class Customer extends Base
{
    use Test;

    protected $name;

    public function getName()
    {
        return $this->name;
    }

    public function setName($name)
    {
        $this->name = $name;
    }
}
```

![](img/39390f6d56c5a83b28db083a8bd5185c_140_0.png)

在 PHP 5 中，特征也可以覆盖属性。在 PHP 7 中，如果特征中的属性初始化的值与父类中的不同，就会生成致命错误。

- 8. 在使用特征直接定义的类中的方法，覆盖特征中定义的重复方法。

- 9. 在这个示例中，`Test` 特征定义了属性 `$id` 以及 `getId()` 方法和 `setId()`。该特征还定义了 `setName()`，这与 `Customer` 类中定义的相同方法冲突。在这种情况下，`Customer` 中直接定义的 `setName()` 方法将覆盖特征中定义的 `setName()`：

```php
trait Test
{
    protected $id;

    public function getId()
    {
        return $this->id;
    }

    public function setId($id)
    {
        $this->id = $id;
    }

    public function setName($name)
    {
        $obj = new stdClass();
        $obj->name = $name;
        $this->name = $obj;
    }
}

class Customer
{
    use Test;

    protected $name;

    public function getName()
    {
        return $this->name;
    }

    public function setName($name)
    {
        $this->name = $name;
    }
}
```

- 10. 使用 `insteadof` 关键字来解决使用多个特征时的方法名冲突。结合使用 `as` 关键字来给方法名起别名。

- 11. 在这个示例中，有两个特征，`IdTrait` 和 `NameTrait`。这两个特征都定义了一个 `setKey()` 方法，但以不同的方式表达键。`Test` 类使用了这两个特征。请注意 `insteadof` 关键字，它允许我们区分冲突的方法。因此，当从 `Test` 类调用 `setKey()` 时，源将来自 `NameTrait`。此外，`IdTrait` 中的 `setKey()` 仍然可用，但在别名 `setKeyDownDate()` 下：

```php
trait IdTrait
{
    protected $id;
    public $key;

    public function setId($id)
    {
        $this->id = $id;
    }

    public function setKey()
    {
        $this->key = date('YmdHis')
            . sprintf('%04d', rand(0, 9999));
    }
}

trait NameTrait
{
    protected $name;
    public $key;

    public function setName($name)
    {
        $this->name = $name;
    }

    public function setKey()
    {
        $this->key = unpack('H*', random_bytes(10))[1];
    }
}

class Test
{
    use IdTrait, NameTrait {
        NameTrait::setKey insteadof IdTrait;
        IdTrait::setKey as setKeyDownDate;
    }
}
```

## 工作原理...

在第 1 步中，您了解到特征用于存在代码重复的情况。您需要评估是否只需定义一个基类并继承它，或者使用特征是否更符合您的目的。当代码重复出现在逻辑上不相关的类中时，特征特别有用。

为了说明特征方法如何覆盖继承的方法，请将第 7 步中提到的代码块复制到一个单独的文件 `chap_04_oop_traits_override_inherited.php` 中。添加这些行代码：

```php
$customer = new Customer();
$customer->setId(100);
$customer->setName('Fred');
var_dump($customer);
```

正如您可以从输出（如下所示）中看到，属性 `$id` 被存储为 `stdClass()` 的实例，这是在特征中定义的行为：





## 使用 PHP 面向对象编程

为了说明直接定义的类方法如何覆盖 trait 方法，请将步骤 9 中提到的代码块复制到单独的文件 `chap_04_oop_trait_methods_do_not_override_class_methods.php` 中。添加以下代码行：

```php
$customer = new Customer();
$customer->setId(100);
$customer->setName('Fred');
var_dump($customer);
```

从下面的输出中可以看出，`$id` 属性在 Customer 类中被定义为整数并以此存储，而 trait 中定义的 `$id` 是 `stdClass` 的实例：

```
Terminal
class Customer#1 (2) {
  protected $name =>
  string(4) "Fred"
  public $id =>
  int(100)
}

--------------
(program exited with code: 0)
Press return to continue
```

在步骤 10 中，你学习了如何使用多个 trait 时解决重复的方法名冲突。将步骤 11 中显示的代码块复制到单独的文件 `chap_04_oop_trait_multiple.php` 中。添加以下代码：

```php
$a = new Test();
$a->setId(100);
$a->setName('Fred');
$a->setKey();
var_dump($a);

$a->setKeyDate();
var_dump($a);
```

请注意，在下面的输出中，`setKey()` 产生来自新 PHP 7 函数 `random_bytes()`（在 `NameTrait` 中定义）的输出，而 `setKeyDate()` 使用 `date()` 和 `rand()` 函数（在 `IdTrait` 中定义）生成一个密钥：

![trait multiple 示例的输出](img/39390f6d56c5a83b28db083a8bd5185c_144_0.png)

## 实现匿名类

PHP 7 引入了一个新特性：**匿名类**。与匿名函数类似，匿名类可以作为表达式的一部分进行定义，创建一个没有名称的类。在需要*即时*创建对象、使用后立即丢弃的情况下，会使用匿名类。

### 具体操作…

1.  `stdClass` 的一个替代方案是定义一个匿名类。

    在定义中，你可以定义任何属性和方法（包括魔术方法）。在这个例子中，我们定义了一个具有两个属性和一个魔术方法 `__construct()` 的匿名类：

    ```php
    $a = new class (123.45, 'TEST') {
        public $total = 0;
        public $test = '';
        public function __construct($total, $test)
        {
            $this->total = $total;
            $this->test = $test;
        }
    };
    ```

2.  匿名类可以继承任何类。

    在这个例子中，一个匿名类继承 `FilterIterator`，并重写了 `__construct()` 和 `accept()` 方法。作为一个参数，它接受 `ArrayIterator $b`，后者代表一个从 10 到 100、步长为 10 的数组。第二个参数作为输出的限制：

    ```php
    $b = new ArrayIterator(range(10, 100, 10));
    $f = new class ($b, 50) extends FilterIterator {
        public $limit = 0;
        public function __construct($iterator, $limit)
        {
            $this->limit = $limit;
            parent::__construct($iterator);
        }
        public function accept()
        {
            return ($this->current() <= $this->limit);
        }
    };
    ```

3.  匿名类可以实现接口。

    在这个例子中，使用一个匿名类来生成一个 HTML 颜色代码表。该类实现了内置的 PHP `Countable` 接口。定义了一个 `count()` 方法，当该类与需要 `Countable` 的方法或函数一起使用时会被调用：

    ```php
    define('MAX_COLORS', 256 ** 3);

    $d = new class () implements Countable {
        public $current = 0;
        public $maxRows = 16;
        public $maxCols = 64;

        public function cycle()
        {
            $row = '';
            $max = $this->maxRows * $this->maxCols;
            for ($x = 0; $x < $this->maxRows; $x++) {
                $row .= '<tr>';
                for ($y = 0; $y < $this->maxCols; $y++) {
                    $row .= sprintf(
                        '<td style="background-color: #%06X">',
                        $this->current);
                    $row .= sprintf(
                        'title="#%06X">&nbsp;</td>',
                        $this->current);
                    $this->current++;
                    $this->current = ($this->current > MAX_COLORS) ? 0 : $this->current;
                }
                $row .= '</tr>';
            }
            return $row;
        }

        public function count()
        {
            return MAX_COLORS;
        }
    };
    ```

4.  匿名类可以使用 traits。

5.  最后一个示例是对前一个示例的修改。与其定义一个 `Test` 类，我们改为定义一个匿名类：

    ```php
    $a = new class {
        use IdTrait, NameTrait {
            NameTrait::setKey insteadof IdTrait;
            IdTrait::setKey as setKeyDate;
        }
    };
    ```

## 工作原理...

在匿名类中，你可以定义任何属性或方法。使用前面的示例，你可以定义一个接受构造函数参数的匿名类，并且可以访问属性。将步骤 2 中描述的代码放入测试脚本 `chap_04_oop_anonymous_class.php`。添加这些 `echo` 语句：

```php
echo "\nAnonymous Class\n";
echo $a->total . PHP_EOL;
echo $a->test . PHP_EOL;
```

以下是来自匿名类的输出：

![匿名类的输出](img/39390f6d56c5a83b28db083a8bd5185c_147_0.png)

为了使用 *FilterIterator*，你*必须*重写 `accept()` 方法。在此方法中，你定义了哪些迭代元素应作为输出包含的条件。现在请继续将步骤 4 中显示的代码添加到测试脚本中。然后你可以添加这些 `echo` 语句来测试匿名类：

```php
echo "\nAnonymous Class Extends FilterIterator\n";
foreach ($f as $item) echo $item . ' ';
echo PHP_EOL;
```

在这个例子中，设定了一个 50 的限制。原始的 `ArrayIterator` 包含一个值数组，从 10 到 100，步长为 10，如以下输出所示：

![FilterIterator 的输出](img/39390f6d56c5a83b28db083a8bd5185c_148_0.png)

要查看实现接口的匿名类，请考虑步骤 5 和 6 中显示的示例。将此代码放入一个文件 `chap_04_oop_anonymous_class_interfaces.php`。

接下来，添加允许你分页浏览 HTML 颜色表的代码：

```php
$$_->current = $_GET['current'] ?? 0;
$$_->current = hexdec($$_->current);
$factor = ($$_->maxRows * $$_->maxCols);
$next = $$_->current + $factor;
$prev = $$_->current - $factor;
$next = ($next < MAX_COLORS) ? $next : MAX_COLORS - $factor;
$prev = ($prev > 0) ? $prev : 0;
$next = sprintf('%06X', $next);
$prev = sprintf('%06X', $prev);
?>
```

最后，继续将 HTML 颜色表作为一个网页展示：

```html
<h1>Total Possible Color Combinations: <?= count($$); ?></h1>
<hr>
<table>
<?= $$_->cycle(); ?>
</table>
<a href="?current=<?= $prev ?>">PREV</a>
<a href="?current=<?= $next ?>">NEXT</a>
```

请注意，你可以通过将匿名类的实例传入 `count()` 函数（显示在 `<H1>` 标签之间）来利用 `Countable` 接口。以下是浏览器窗口中显示的输出：

![颜色表的浏览器输出](img/39390f6d56c5a83b28db083a8bd5185c_149_0.png)

最后，为了说明在匿名类中使用 traits，将前面食谱中提到的 `chap_04_oop_trait_multiple.php` 文件复制到新文件 `chap_04_oop_trait_anonymous_class.php`。删除 `Test` 类的定义，并将其替换为匿名类：

```php
$a = new class() {
    use IdTrait, NameTrait {
        NameTrait::setKey insteadof IdTrait;
        IdTrait::setKey as setKeyDate;
    }
};
```

删除这一行：

```php
$a = new Test();
```

当你运行代码时，你会看到与前面截图中完全相同的输出，除了类引用将是匿名的：

![trait 匿名类的输出](img/39390f6d56c5a83b28db083a8bd5185c_150_0.png)

# 第 5 章 与数据库交互

在本章中，我们将涵盖以下主题：

-   使用 PDO 连接数据库
-   构建面向对象的 SQL 查询构建器
-   处理分页
-   定义实体以匹配数据库表
-   将实体类绑定到 RDBMS 查询
-   将二次查找嵌入到查询结果中
-   实现 jQuery DataTables PHP 查找

## 简介

在本章中，我们将介绍一系列利用 **PHP 数据对象 (PDO)** 扩展的数据库连接食谱。诸如 **结构化查询语言 (SQL)** 生成、分页以及将对象与数据库表绑定等常见编程问题将被解决。最后，在结尾处，我们将展示处理二次查找的代码，这些查找以嵌入的匿名函数形式存在，并使用 jQuery DataTables 进行 AJAX 请求。




## 使用 PDO 连接数据库

PDO 是一个高性能且得到积极维护的数据库扩展，与特定厂商的扩展相比具有独特优势。它拥有一个通用的应用程序接口（API），兼容几乎所有十多种不同的关系型数据库管理系统（RDBMS）。学习如何使用此扩展将为您节省数小时的时间，否则您本需花费这些时间去掌握等效的特定厂商数据库扩展的命令子集。

PDO 分为四个主要类，如下表所示：

| 类 | 功能 |
| :--- | :--- |
| PDO | 维护与数据库的实际连接，并处理事务支持等底层功能 |
| PDOStatement | 处理结果 |
| PDOException | 数据库特有的异常 |
| PDODriver | 与实际的特定厂商数据库通信 |

### 实现方法...

- 1. 通过创建 `PDO` 实例来设置数据库连接。
- 2. 您需要构造一个**数据源名称（DSN）**。DSN 中包含的信息根据所使用的数据库驱动程序而变化。例如，以下是用于连接 **MySQL** 数据库的 DSN：

```php
$params = [
    'host'  => 'localhost',
    'user'  => 'test',
    'pwd'   => 'password',
    'db'    => 'php7cookbook'
];

try {
    $dsn = sprintf('mysql:host=%s;dbname=%s',
            $params['host'], $params['db']);
    $pdo = new PDO($dsn, $params['user'], $params['pwd']);
} catch (PDOException $e) {
    echo $e->getMessage();
} catch (Throwable $e) {
    echo $e->getMessage();
}
```

- 3. 另一方面，更简单的扩展 **SQLite** 仅需要以下命令：

```php
$params = [
    'db' => __DIR__ . '/../data/db/php7cookbook.db.sqlite'
];
$dsn = sprintf('sqlite:' . $params['db']);
```

- 4. 另一方面，**PostgreSQL** 直接将用户名和密码包含在 DSN 中：

```php
$params = [
    'host' => 'localhost',
    'user' => 'test',
    'pwd' => 'password',
    'db' => 'php7cookbook'
];
$dsn = sprintf('pgsql:host=%s;dbname=%s;user=%s;password=%s',
    $params['host'],
    $params['db'],
    $params['user'],
    $params['pwd']);
```

- 5. DSN 还可以包含服务器特有的指令，例如 unix_socket，如下例所示：

```php
$params = [
    'host' => 'localhost',
    'user' => 'test',
    'pwd' => 'password',
    'db' => 'php7cookbook',
    'sock' => '/var/run/mysqld/mysqlq.sock'
];

try {
    $dsn = sprintf('mysql:host=%s;dbname=%s;unix_socket=%s',
        $params['host'], $params['db'], $params['sock']);
    $opts = [PDO::ATTR_ERRMODE => PDO::ERRMODE_EXCEPTION];
    $pdo = new PDO($dsn, $params['user'], $params['pwd'], $opts);
} catch (PDOException $e) {
    echo $e->getMessage();
} catch (Throwable $e) {
    echo $e->getMessage();
}
```

**最佳实践**

将创建 PDO 实例的语句包裹在 try {} catch {} 块中。在失败时捕获 PDOException 以获取数据库特有信息。捕获 Throwable 以处理错误或任何其他异常。为获得最佳效果，将 PDO 错误模式设置为 PDO::ERRMODE_EXCEPTION。有关错误模式的更多详情，请参见步骤 8。

在 PHP 5 中，如果无法构建 PDO 对象（例如使用了无效参数时），该实例会被赋值为 NULL。在 PHP 7 中，会抛出 Exception。如果您将 PDO 对象的构建包裹在 try {} catch {} 块中，并且将 PDO::ATTR_ERRMODE 设置为 PDO::ERRMODE_EXCEPTION，您可以捕获并记录此类错误，而无需检测 NULL。

- 6. 使用 PDO::query() 发送 SQL 命令。会返回一个 PDOStatement 实例，您可以从中获取结果。在本例中，我们查找按 ID 排序的前 20 个客户：

```php
$stmt = $pdo->query(
'SELECT * FROM customer ORDER BY id LIMIT 20');
```

PDO 还提供了一个便捷方法 PDO::exec()，它不返回结果迭代，仅返回受影响的行数。此方法最适合用于 ALTER TABLE、DROP TABLE 等管理操作。

- 7. 遍历 PDOStatement 实例以处理结果。将**获取模式**设置为 PDO::FETCH_NUM 或 PDO::FETCH_ASSOC，以数字数组或关联数组的形式返回结果。在本例中，我们使用 while() 循环来处理结果。当获取最后一个结果时，结果将是一个布尔值 FALSE，从而结束循环：

```php
while ($row = $stmt->fetch(PDO::FETCH_ASSOC)) {
    printf('%4d | %20s | %5s' . PHP_EOL, $row['id'],
        $row['name'], $row['level1']);
}
```

PDO 获取操作涉及一个定义迭代方向（即向前或向后）的光标。PDOStatement::fetch() 的第二个参数可以是任何 PDO::FETCH_ORI_* 常量。光标方向包括 prior、first、last、absolute 和 relative。默认光标方向是 PDO::FETCH_ORI_NEXT。

- 8. 将获取模式设置为 PDO::FETCH_OBJ，以 stdClass 实例的形式返回结果。请注意，while() 循环利用了获取模式 PDO::FETCH_OBJ。注意，printf() 语句引用的是对象属性，这与前一个示例引用数组元素形成对比：

```php
while ($row = $stmt->fetch(PDO::FETCH_OBJ)) {
    printf('%4d | %20s | %5s', PHP_EOL,
           $row->id, $row->name, $row->level);
}
```

- 9. 如果您想在处理查询时创建特定类的实例，请将获取模式设置为 PDO::FETCH_CLASS。您还必须拥有类定义，并且 PDO::query() 应设置类名。如下面代码片段所示，我们定义了一个名为 Customer 的类，包含公开属性 $id、$name 和 $level。属性必须是公开的，才能使获取注入正常工作：

```php
class Customer
{
    public $id;
    public $name;
    public $level;
}

$stmt = $pdo->query($sql, PDO::FETCH_CLASS, 'Customer');
```

- 10. 在获取对象时，步骤 5 中显示的技术的更简单替代方法是使用 PDOStatement::fetchObject()：

```php
while ($row = $stmt->fetchObject('Customer')) {
    printf('%4d | %20s | %5s', PHP_EOL,
           $row->id, $row->name, $row->level);
}
```

- 11. 您还可以使用 PDO::FETCH_INTO，这基本上与 PDO::FETCH_CLASS 相同，但您需要一个活动的对象实例而不是类引用。每次通过循环迭代时，同一个对象实例都会用当前的信息集重新填充。此示例假设与步骤 5 中相同的 Customer 类，以及步骤 1 中定义的相同数据库参数和 PDO 连接：

```php
$cust = new Customer();
while ($stmt->fetch(PDO::FETCH_INTO)) {
    printf('%4d | %20s | %5s', PHP_EOL,
           $cust->id, $cust->name, $cust->level);
}
```

## 与数据库交互

- 12. 如果您未指定错误模式，默认 PDO 错误模式是 PDO::ERRMODE_SILENT。您可以使用 PDO::ATTR_ERRMODE 键设置错误模式，并使用 PDO::ERRMODE_WARNING 或 PDO::ERRMODE_EXCEPTION 值。错误模式可以作为 PDO 构造函数的第四个参数指定，形式为关联数组。或者，您可以对现有实例使用 PDO::setAttribute()。

- 13. 假设您有以下 DSN 和 SQL（在您认为这是一种新的 SQL 形式之前，请确保：此 SQL 语句将无法工作！）：

```php
$params = [
    'host' => 'localhost',
    'user' => 'test',
    'pwd'  => 'password',
    'db'     => 'php7cookbook'
];
$dsn = sprintf('mysql:host=%s;dbname=%s', $params['host'],
    $params['db']);
$sql = 'THIS SQL STATEMENT WILL NOT WORK';
```

- 14. 然后，如果您使用默认错误模式构建 PDO 连接，唯一表明出问题的线索是：PDO::query() 没有产生 PDOStatement 实例，而是返回了一个布尔值 FALSE：

```php
$pdo1 = new PDO($dsn, $params['user'], $params['pwd']);
$stmt = $pdo1->query($sql);
$row = ($stmt) ? $stmt->fetch(PDO::FETCH_ASSOC) : 'No Good';
```

- 15. 下一个示例展示了使用构造函数方法将错误模式设置为 WARNING：

```php
$pdo2 = new PDO(
    $dsn,
    $params['user'],
    $params['pwd'],
    [PDO::ATTR_ERRMODE => PDO::ERRMODE_WARNING]
);
```

- 16. 如果您需要完全分离准备和执行阶段，请改用 PDO::prepare() 和 PDOStatement::execute()。该语句随后被发送到数据库服务器以进行预编译。然后您可以执行该语句多次，通常是在循环中。

- 17. PDO::prepare() 的第一个参数可以是一个在占位符处放置实际值的 SQL 语句。然后可以向 PDOStatement::execute() 提供一组值的数组。PDO 自动提供数据库引用，有助于防止 SQL 注入。




## 最佳实践

任何将外部输入（即来自表单提交）与 SQL 语句结合的应用程序都容易受到 SQL 注入攻击。所有外部输入必须先经过适当的过滤、验证以及其他消毒处理。不要将外部输入直接放入 SQL 语句中。相反，应使用占位符，并在执行阶段提供实际的（已消毒的）值。

-   18. 若要反向遍历结果，你可以更改**可滚动游标**的方向。或者，可能更简单的方法是，只需将 `ORDER BY` 从 `ASC` 改为 `DESC`。以下代码行创建了一个请求可滚动游标的 `PDOStatement` 对象：

```php
$dsn = sprintf('pgsql:charset=UTF8;host=%s;dbname=%s',
    $params['host'], $params['db']);
$opts = [PDO::ATTR_ERRMODE => PDO::ERRMODE_EXCEPTION];
$pdo = new PDO($dsn, $params['user'], $params['pwd'], $opts);
$sql = 'SELECT * FROM customer '
      . 'WHERE balance > :min AND balance < :max '
      . 'ORDER BY id LIMIT 20';
$stmt = $pdo->prepare($sql, [PDO::ATTR_CURSOR =>
      PDO::CURSOR_SCROLL]);
```

-   19. 在获取操作期间，你还需要指定游标指令。此示例获取结果集中的最后一行，然后向后滚动：

```php
$stmt->execute(['min' => $min, 'max' => $max]);
$row = $stmt->fetch(PDO::FETCH_ASSOC, PDO::FETCH_ORI_LAST);
do {
    printf('%4d | %20s | %5s | %8.2f' . PHP_EOL,
        $row['id'],
        $row['name'],
        $row['level'],
        $row['balance']);
} while ($row = $stmt->fetch(PDO::FETCH_ASSOC,
        PDO::FETCH_ORI_PRIOR));
```

-   20. MySQL 和 SQLite 都不支持可滚动游标！要获得相同的结果，请尝试对前面的代码进行以下修改：

```php
$dsn = sprintf('mysql:charset=UTF8;host=%s;dbname=%s',
    $params['host'], $params['db']);
$opts = [PDO::ATTR_ERRMODE => PDO::ERRMODE_EXCEPTION];
$pdo = new PDO($dsn, $params['user'], $params['pwd'], $opts);
$sql = 'SELECT * FROM customer '
      . 'WHERE balance > :min AND balance < :max '
      . 'ORDER BY id DESC'
      . 'LIMIT 20';
$stmt = $pdo->prepare($sql);
while ($row = $stmt->fetch(PDO::FETCH_ASSOC)) {
    printf('%4d | %20s | %5s | %8.2f' . PHP_EOL,
        $row['id'],
        $row['name'],
        $row['level'],
        $row['balance']);
}
```

-   21. PDO 提供了对事务的支持。借用第 9 步的代码，我们可以将 INSERT 命令序列封装到一个事务块中：

```php
try {
    $pdo->beginTransaction();
    $sql = "INSERT INTO customer ("
        . implode('", "', $fields) . ") VALUES (?, ?, ?, ?, ?, ?)";
    $stmt = $pdo->prepare($sql);
    foreach ($data as $row) $stmt->execute($row);
    $pdo->commit();
} catch (PDOException $e) {
    error_log($e->getMessage());
    $pdo->rollBack();
}
```

-   22. 最后，为了保持模块化和可重用性，我们可以将 PDO 连接封装到一个单独的类 Application\Database\Connection 中。在这里，我们通过构造函数建立连接。或者，还有一个静态 factory() 方法，让我们可以生成一系列 PDO 实例：

```php
namespace Application\Database;
use Exception;
use PDO;
class Connection
{
    const ERROR_UNABLE = 'ERROR: no database connection';
    public $pdo;
    public function __construct(array $config)
    {
        if (isset($config['driver'])) {
            $message = __METHOD__ . ' : '
                . self::ERROR_UNABLE . PHP_EOL;
            throw new Exception($message);
        }

        $dsn = $this->makeDsn($config);
        try {
            $this->pdo = new PDO(
                $dsn,
                $config['user'],
                $config['password'],
                [PDO::ATTR_ERRMODE => $config['errmode']]
            );
            return TRUE;
        } catch (PDOException $e) {
            error_log($e->getMessage());
            return FALSE;
        }
    }

    public static function factory(
        $driver, $dbname, $host, $user,
        $pwd, array $options = array()
    ) {
        $config = [
            'driver' => $driver,
            'dbname' => $dbname,
            'host'   => $host,
            'user'   => $user,
            'password' => $pwd
        ];
        // 注意：原始 OCR 文本在此特定方法主体中存在不一致之处
        // （在静态上下文中调用 $this 或缺少配置构建）。
        // 基于“静态工厂”的上下文，它可能从参数中构建 DSN。
        // 然而，严格遵循提供的文本，该文本在 OCR 中似乎被截断或格式错误：
        
        // 基于周围文本片段重建可能的意图：
        $dsn = "$driver:dbname=$dbname;host=$host"; 
        try {
            return new PDO($dsn, $user, $pwd, $options);
        } catch (PDOException $e) {
            error_log($e->getMessage());
        }
    }
```

-   23. 这个 Connection 类的一个重要组成部分是一个通用方法，可用于构建 DSN。要使其工作，我们只需要将 PDODriver 作为前缀建立，后面跟着 ": "。之后，我们只需从配置数组中追加键/值对。每个键/值对由分号分隔。我们还需要去除尾部分号，为此使用带有负值限制的 substr()：

```php
public function makeDsn($config)
{
    $dsn = $config['driver'] . ':';
    unset($config['driver']);
    foreach ($config as $key => $value) {
        $dsn .= $key . '=' . $value . ';';
    }
    return substr($dsn, 0, -1);
}
```

## 工作原理...

首先，你可以将第 1 步中的初始连接代码复制到 chap_05_pdo_connect_mysql.php 文件中。出于说明目的，我们假设你已创建一个名为 php7cookbook 的 MySQL 数据库，用户名为 cook，密码为 book。接下来，我们使用 PDO::query() 方法向数据库发送一个简单的 SQL 语句。最后，我们使用生成的语句对象以关联数组的形式获取结果。别忘了将你的代码包裹在 try {} catch {} 块中：

```php
<?php
$params = [
    'host' => 'localhost',
    'user' => 'test',
    'pwd' => 'password',
    'db' => 'php7cookbook'
];
try {
    $dsn = sprintf('mysql:charset=UTF8;host=%s;dbname=%s',
        $params['host'], $params['db']);
    $pdo = new PDO($dsn, $params['user'], $params['pwd']);
    $stmt = $pdo->query(
        'SELECT * FROM customer ORDER BY id LIMIT 20');
    printf('%4s | %20s | %5s | %7s' . PHP_EOL,
        'ID', 'NAME', 'LEVEL', 'BALANCE');
    printf('%4s | %20s | %5s | %7s' . PHP_EOL,
        '----', str_repeat('-', 20), '-----', '--------');
    while ($row = $stmt->fetch(PDO::FETCH_ASSOC)) {
        printf('%4d | %20s | %5s | %7.2f' . PHP_EOL,
            $row['id'], $row['name'], $row['level'], $row['balance']);
    }
} catch (PDOException $e) {
    error_log($e->getMessage());
} catch (Throwable $e) {
    error_log($e->getMessage());
}
```

这是生成的输出：

![](img/39390f6d56c5a83b28db083a8bd5185c_161_0.png)

向 PDO 构造函数添加选项，将错误模式设置为 EXCEPTION。现在修改 SQL 语句，并观察产生的错误消息：

```php
$opts = [PDO::ATTR_ERRMODE => PDO::ERRMODE_EXCEPTION];
$pdo = new PDO($dsn, $params['user'], $params['pwd'], $opts);
$stmt = $pdo->query('THIS SQL STATEMENT WILL NOT WORK');
```

你将观察到类似以下内容：

![](img/39390f6d56c5a83b28db083a8bd5185c_161_1.png)

占位符可以是命名占位符，也可以是位置占位符。**命名占位符**在准备好的 SQL 语句中由冒号 (:) 前缀，并在传递给 execute() 的关联数组中作为键引用。**位置占位符**在准备好的 SQL 语句中表示为问号 (?)。

## 与数据库交互

在以下示例中，使用命名占位符来表示 WHERE 子句中的值：

```php
try {
    $dsn = sprintf('mysql:host=%s;dbname=%s',
        $params['host'], $params['db']);
    $pdo = new PDO($dsn,
        $params['user'],
        $params['pwd'],
        [PDO::ATTR_ERRMODE => PDO::ERRMODE_EXCEPTION]);
    $sql = 'SELECT * FROM customer '
        . 'WHERE balance < :val AND level = :level '
        . 'ORDER BY id LIMIT 20';
    echo $sql . PHP_EOL;
    $stmt = $pdo->prepare($sql);
    $stmt->execute(['val' => 100, 'level' => 'BEG']);
    while ($row = $stmt->fetch(PDO::FETCH_ASSOC)) {
        printf('%4d | %20s | %5s | %8.2f' . PHP_EOL,
            $row['id'], $row['name'], $row['level'], $row['balance']);
    }
} catch (PDOException $e) {
    echo $e->getMessage();
} catch (Throwable $e) {
    echo $e->getMessage();
}
```

此示例展示了在 INSERT 操作中使用位置占位符。请注意，作为第四个客户插入的数据包含潜在的 SQL 注入攻击。你还会注意到，需要了解所使用的数据库的 SQL 语法知识。在这种情况下，MySQL 列名使用反引号 (\`) 引用：

```php
$fields = ['name', 'balance', 'email',
    'password', 'status', 'level'];

$data = [
    ['Saleen', 0, 'saleen@test.com', 'password', 0, 'BEG'],
    ['Lada', 55.55, 'lada@test.com', 'password', 0, 'INT'],
    ['Tonsoi', 999.99, 'tonsoi@test.com', 'password', 1, 'ADV'],
    ['SQL Injection', 0.00, 'bad@bad.com', 'password', 1,
     'BEG`DELETE FROM customer;--'],
];

try {
    $dsn = sprintf('mysql:host=%s;dbname=%s',
        $params['host'], $params['db']);
    $pdo = new PDO($dsn,
        $params['user'],
```




## 与数据库交互

在本示例中，我们将变量 $min、$max 和 $level 绑定到预处理语句：

```php
$min    = 0;
$max   = 0;
$level = '';

try {
  $dsn  = sprintf('mysql:host=%s;dbname=%s', $params['host'],
                $params['db']);
  $opts = [PDO::ATTR_ERRMODE => PDO::ERRMODE_EXCEPTION];
  $pdo  = new PDO($dsn, $params['user'], $params['pwd'], $opts);
  $sql  = 'SELECT * FROM customer '
         . 'WHERE balance > :min '
         . "AND balance < :max AND level = :level "
         . "ORDER BY id LIMIT 20";
  $stmt = $pdo->prepare($sql);
  $stmt->bindParam('min',   $min);
  $stmt->bindParam('max',   $max);
  $stmt->bindParam('level', $level);

  $min   = 5000;
  $max   = 10000;
  $level = 'ADV';
  $stmt->execute();
  showResults($stmt, $min, $max, $level);

  $min   = 0;
  $max   = 100;
  $level = 'BEG';
  $stmt->execute();
  showResults($stmt, $min, $max, $level);

} catch (PDOException $e) {
  echo $e->getMessage();
} catch (Throwable $e) {
  echo $e->getMessage();
}
```

当这些变量的值发生变化时，下一次执行将反映修改后的条件。

![](img/39390f6d56c5a83b28db083a8bd5185c_164_0.png)

![](img/39390f6d56c5a83b28db083a8bd5185c_164_1.png)

## 最佳实践

对于一次性的数据库命令，请使用 `PDO::query()`。当你需要多次处理相同的语句但使用不同的值时，请使用 `PDO::prepare()` 和 `PDOStatement::execute()`。

![](img/39390f6d56c5a83b28db083a8bd5185c_164_2.png)

## 参见

关于与不同供应商特定 PDO 驱动相关的语法和独特行为的信息，请查看此文章：

- http://php.net/manual/en/pdo.drivers.php

关于 PDO 预定义常量的摘要，包括获取模式、光标方向和属性，请参阅以下文章：

- http://php.net/manual/en/pdo.constants.php

## 构建 OOP SQL 查询生成器

PHP 7 实现了所谓的**上下文敏感词法分析器**。这意味着，如果上下文允许，通常保留的词语可以被使用。因此，在构建面向对象的 SQL 生成器时，我们可以使用名为 `and`、`or`、`not` 等方法。

### 实现方法...

1. 我们定义了一个 `Application\Database\Finder` 类。在该类中，我们定义了与我们首选的 SQL 操作相匹配的方法：

```php
namespace Application\Database;

class Finder
{
    public static $sql        = '';
    public static $instance = NULL;
    public static $prefix    = '';
    public static $where     = array();
    public static $control   = ['', ''];

    // $a == name of table
    // $cols = column names
    public static function select($a, $cols = NULL)
    {
        self::$instance = new Finder();
        if ($cols) {
            self::$prefix = 'SELECT ' . $cols . ' FROM ' . $a;
        } else {
            self::$prefix = 'SELECT * FROM ' . $a;
        }
        return self::$instance;
    }

    public static function where($a = NULL)
    {
        self::$where[0] = ' WHERE ' . $a;
        return self::$instance;
    }

    public static function like($a, $b)
    {
        self::$where[] = trim($a . ' LIKE ' . $b);
        return self::$instance;
    }

    public static function and($a = NULL)
    {
        self::$where[] = trim('AND ' . $a);
        return self::$instance;
    }

    public static function or($a = NULL)
    {
        self::$where[] = trim('OR ' . $a);
        return self::$instance;
    }

    public static function in(array $a)
    {
        self::$where[] = 'IN ( ' . implode(',', $a) . ' )';
        return self::$instance;
    }

    public static function not($a = NULL)
    {
        self::$where[] = trim('NOT ' . $a);
        return self::$instance;
    }

    public static function limit($limit)
    {
        self::$control[0] = 'LIMIT ' . $limit;
        return self::$instance;
    }

    public static function offset($offset)
    {
        self::$control[1] = 'OFFSET ' . $offset;
        return self::$instance;
    }

    public static function getSql()
    {
        self::$sql = self::$prefix
            . implode(' ', self::$where)
            . ' '
            . self::$control[0]
            . ' '
            . self::$control[1];
        preg_replace('/\/\/', '', self::$sql);
        return trim(self::$sql);
    }
}
```

2. 每个用于生成 SQL 片段函数都返回相同的属性，`$instance`。这允许我们使用流畅接口来表示代码，例如：

```php
$sql = Finder::select('project')->where('priority > 9') ... etc.
```

## 工作原理...

将之前定义的代码复制到 `Application\Database` 文件夹中的 `Finder.php` 文件里。然后，你可以创建一个名为 `chap_05_op_query_builder.php` 的调用程序，它初始化在*第 1 章，构建基础*中定义的自动加载器。然后你可以运行 `Finder::select()` 来生成一个对象，从中可以渲染出 SQL 字符串：

```php
<?php
require __DIR__ . '/../Application/Autoload/Loader.php';
Application\Autoload\Loader::init(__DIR__ . '/..');
use Application\Database\Finder;

$sql = Finder::select('project')
    ->where()
    ->like('name', '%secret%')
    ->and('priority > 9')
    ->or('code')->in(['4', '5', '7'])
    ->and()->not('created_at')
    ->limit(10)
    ->offset(20);

echo Finder::getSql();
```

这是上述代码的结果：

![](img/39390f6d56c5a83b28db083a8bd5185c_168_0.png)

### 参见

关于上下文敏感词法分析器的更多信息，请查看此文章：

`https://wiki.php.net/rfc/context_sensitive_lexer`

## 处理分页

分页涉及提供数据库查询结果的有限子集。这通常用于显示目的，但也很容易适用于其他情况。乍一看，`LimitIterator` 类似乎最适合分页目的。然而，在潜在结果集可能非常巨大的情况下，`LimitIterator` 并不是一个理想的候选项，因为你需要将整个结果集作为内部迭代器提供，这很可能会超过内存限制。`LimitIterator` 类构造函数的第二个和第三个参数是偏移量和计数。这暗示了我们将采用的分页解决方案，它是 SQL 原生的：给定的 SQL 语句添加 `LIMIT` 和 `OFFSET` 子句。

### 实现方法...

1. 首先，我们创建一个名为 `Application\Database\Paginate` 的类来持有分页逻辑。我们添加属性来表示与分页相关的值，`$sql`、`$page` 和 `$linesPerPage`：

```php
namespace Application\Database;

class Paginate
{
    const DEFAULT_LIMIT = 20;
    const DEFAULT_OFFSET = 0;

    protected $sql;
    protected $page;
    protected $linesPerPage;
}
```

2. 接下来，我们定义一个 `__construct()` 方法，它接受基础 SQL 语句、当前页码和每行行数作为参数。然后我们需要重构 SQL 字符串，修改或添加 LIMIT 和 OFFSET 子句。

3. 在构造函数中，我们需要使用当前页码和每行行数计算偏移量。我们还需要检查 SQL 语句中是否已经存在 LIMIT 和 OFFSET。最后，我们需要使用每行行数作为我们的 LIMIT，并使用重新计算的 OFFSET 修订语句：

```php
public function __construct($sql, $page, $linesPerPage)
{
    $offset = $page * $linesPerPage;

    switch (TRUE) {
        case (stripos($sql, 'LIMIT') && stripos($sql, 'OFFSET')):
            // no action needed
            break;

        case (stripos($sql, 'LIMIT')):
            $sql .= ' LIMIT ' . self::DEFAULT_LIMIT;
            break;

        case (stripos($sql, 'OFFSET')):
            $sql .= ' OFFSET ' . self::DEFAULT_OFFSET;
            break;

        default:
            $sql .= ' LIMIT ' . self::DEFAULT_LIMIT;
            $sql .= ' OFFSET ' . self::DEFAULT_OFFSET;
            break;
    }

    $this->sql = preg_replace('/LIMIT\s\d+.*OFFSET\s\d+/i',
        'LIMIT ' . $linesPerPage . ' OFFSET ' . $offset,
        $sql);
}
```

4. 现在我们准备好使用第一个食谱中讨论的 `Application\Database\Connection` 类来执行查询。

5. 在我们新的分页类中，我们添加了一个 `paginate()` 方法，它接受一个 `Connection` 实例作为参数。我们还需要 PDO 获取模式和可选的预处理语句参数：

```php
use PDOException;

public function paginate(
    Connection $connection,
```





6. 为前一个食谱中提到的查询构建器类提供支持可能也不是个坏主意。这将使更新 LIMIT 和 OFFSET 变得更加容易。我们只需提供支持 `Application\Database\Finder`，即使用该类并修改 `__construct()` 方法，检查传入的 SQL 是否是此类的实例：

```php
if ($sql instanceof Finder) {
    $sql->limit($linesPerPage);
    $sql->offset($offset);
    $this->sql = $sql::getSql();
} elseif (is_string($sql)) {
    switch (TRUE) {
        case (stripos($sql, 'LIMIT')
          && stripos($sql, 'OFFSET') :
            // remaining code as shown in bullet #3 above
        }
    }
}
```

7. 现在剩下的工作就是在需要确认 SQL 语句是否格式正确时添加一个 getSql() 方法：

```php
public function getSql()
{
    return $this->sql;
}
```

## 工作原理...

将前面的代码复制到 Application/Database 文件夹中的 **Paginate.php** 文件。
然后你可以创建一个 chap_05_pagination.php 调用程序，它初始化了*第 1 章，建立基础*中定义的自动加载器：

```php
<?php
define('DB_CONFIG_FILE',  '/../config/db.config.php');
define('LINES_PER_PAGE',  10);
define('DEFAULT_BALANCE', 1000);
require __DIR__ . './../Application/Autoload/Loader.php';
Application\Autoload\Loader::init(__DIR__ . './../');
```

接下来，使用 `Application\Database\Finder`、Connection 和 Paginate 类，创建 `Application\Database\Connection` 的实例，并使用 Finder 生成 SQL：

```php
use Application\Database\ { Finder, Connection, Paginate};
$conn = new Connection(include __DIR__ . DB_CONFIG_FILE);
$sql  = Finder::select('customer')->where('balance < :bal');
```

现在我们可以从 $_GET 参数中获取页码和余额，并创建 Paginate 对象，结束 PHP 代码块：

```php
$page  = (int) ($_GET['page'] ?? 0);
$bal   = (float) ($_GET['balance'] ?? DEFAULT_BALANCE);
$Paginate = new Paginate($sql->getSql(), $page, LINES_PER_PAGE);
?>
```

在脚本的输出部分，我们简单地使用一个普通的 foreach() 循环来遍历分页：

```html
<h3><?= $Paginate->getSql(); ?></h3>
<hr>
<pre>
<?php
printf('%4s | %20s | %5s | %7s' . PHP_EOL,
    'ID', 'NAME', 'LEVEL', 'BALANCE');
printf('%4s | %20s | %5s | %7s' . PHP_EOL,
    '----', str_repeat('-', 20), '-----', '--------');
foreach ($Paginate->paginate($conn, PDO::FETCH_ASSOC,
       ['bal' => $bal]) as $row) {
    printf('%4d | %20s | %5s | %7.2f' . PHP_EOL,
      $row['id'], $row['name'], $row['level'], $row['balance']);
}
    printf('%4s | %20s | %5s | %7s' . PHP_EOL,
    '------', str_repeat('|-', 20), '|------', '--------');
?>
<a href="?page=<?=$page - 1; ?>&balance=<?= $bal ?>">
<< Prev </a>&nbsp;&nbsp;
<a href="?page=<?= $page + 1; ?>&balance=<?= $bal ?>">
Next >></a>
</pre>
```

这是输出的第 3 页，其中余额小于 1,000：

![](img/39390f6d56c5a83b28db083a8bd5185c_172_0.png)

## 参见

有关 `LimitIterator` 类的更多信息，请参见这篇文章：

- [http://php.net/manual/en/class.limititerator.php](http://php.net/manual/en/class.limititerator.php)

## 定义与数据库表匹配的实体

PHP 开发者中一种非常常见的做法是创建代表数据库表的类。这类类通常被称为 **实体** 类，并且是 **领域模型** 软件设计模式的核心。

## 如何操作...

1. 首先，我们将建立一系列实体类的一些共同特征。
   这些可能包括公共属性和公共方法。我们将把这些
   放入 `Application\Entity\Base` 类中。所有未来的实体类都将继承
   Base。

2. 为了说明的目的，让我们假设所有实体都将有两个公共属性：$mapping（稍后讨论）和 $id（及其对应的 getter 和 setter）：

```php
namespace Application\Entity;

class Base
{
    protected $id = 0;
    protected $mapping = ['id' => 'id'];

    public function getId() : int
    {
        return $this->id;
    }

    public function setId($id)
    {
        $this->id = (int) $id;
    }
}
```

3. 定义一个 arrayToEntity() 方法并不是个坏主意，该方法将数组转换为实体类的实例，反之亦然（entityToArray()）。这些方法实现了一个通常被称为水合（hydration）的过程。由于这些方法应该是通用的，最好将它们放在 Base 类中。

4. 在以下方法中，$mapping 属性用于在数据库列名和对象属性名之间进行转换。arrayToEntity() 从数组中填充此对象实例的值。如果需要在活动实例之外调用该方法，我们可以将此方法定义为静态方法：

```php
public static function arrayToEntity($data, Base $instance)
{
    if ($data && is_array($data)) {
        foreach ($instance->mapping as $dbColumn => $propertyName) {
            $method = 'set' . ucfirst($propertyName);
            $instance->$method($data[$dbColumn]);
        }
        return $instance;
    }
    return FALSE;
}
```

5. `entityToArray()` 方法从当前实例属性值生成数组：

```php
public function entityToArray()
{
    $data = array();
    foreach ($this->mapping as $dbColumn => $propertyName) {
        $method = 'get' . ucfirst($propertyName);
        $data[$dbColumn] = $this->$method() ?? NULL;
    }
    return $data;
}
```

6. 要构建具体的实体，你需要在手头准备好计划建模的数据库表的结构。创建映射到数据库列的属性。分配的初始值应反映数据库列的最终数据类型。

7. 在这个例子中，我们将使用 `customer` 表。这是来自 MySQL 数据转储的 `CREATE` 语句，说明了其数据结构：

```sql
CREATE TABLE `customer` (
 `id` int(11) NOT NULL AUTO_INCREMENT,
 `name` varchar(256) CHARACTER SET latin1 COLLATE
 latin1_general_cs NOT NULL,
 `balance` decimal(10,2) NOT NULL,
 `email` varchar(250) NOT NULL,
 `password` char(16) NOT NULL,
 `status` int(10) unsigned NOT NULL DEFAULT '0',
 `security_question` varchar(250) DEFAULT NULL,
 `confirm_code` varchar(32) DEFAULT NULL,
 `profile_id` int(11) DEFAULT NULL,
 `level` char(3) NOT NULL,
 PRIMARY KEY (`id`),
 UNIQUE KEY `UNIQ_81398E09E7927C74` (`email`)
);
```

8. 我们现在可以充实类属性了。这也是确定对应表的好时机。在这种情况下，我们将使用 `TABLE_NAME` 类常量：

```php
namespace Application\Entity;

class Customer extends Base
{
    const TABLE_NAME = 'customer';
    protected $name = '';
    protected $balance = 0.0;
    protected $email = '';
    protected $password = '';
    protected $status = '';
    protected $securityQuestion = '';
    protected $confirmCode = '';
    protected $profileId = 0;
    protected $level = '';
}
```

9. 将属性定义为 *protected* 被认为是一种最佳实践。为了访问这些属性，你需要设计 *public* 方法来 **get** 和 **set** 这些属性。这里是使用 PHP 7 将数据类型应用于返回值的好机会。

10. 在下面的代码块中，我们为 $name 和 $balance 定义了 getter 和 setter。你可以想象这些其余方法是如何定义的：

```php
public function getName() : string
{
    return $this->name;
}

public function setName($name)
{
    $this->name = $name;
}

public function getBalance() : float
{
    return $this->balance;
}

public function setBalance($balance)
{
    $this->balance = (float) $balance;
}
```

> 在 setter 中对传入值进行数据类型检查并不是一个好主意。原因是 RDBMS 数据库查询的返回值都是 *string* 数据类型。

11. 如果属性名与对应的数据库列不完全匹配，你应该考虑创建一个映射属性，即一个键/值对的数组，其中键代表数据库列名，值代表属性名。




12. 你会发现，三个属性 `$securityQuestion`、`$confirmCode` 和 `$profileId` 并不对应其等效的列名 `security_question`、`confirm_code` 和 `profile_id`。`$mapping` 属性将确保进行适当的转换：

```
protected $mapping = [
'id'              => 'id',
'name'            => 'name',
'balance'         => 'balance',
'email'           => 'email',
'password'        => 'password',
'status'          => 'status',
'security_question' => 'securityQuestion',
'confirm_code'    => 'confirmCode',
'profile_id'      => 'profileId',
'level'           => 'level'
];
```

## 工作原理...

将步骤 2、4 和 5 中的代码复制到 `Application/Entity` 文件夹中的 `Base.php` 文件。将步骤 8 到 12 中的代码复制到同样位于 `Application/Entity` 文件夹中的 `Customer.php` 文件。然后，你需要为步骤 10 中未显示的剩余属性创建 getter 和 setter：email、password、status、securityQuestion、confirmCode、profileId 和 level。

然后，你可以创建一个调用程序 `chap_05_matching_entity_to_table.php`，它初始化第 1 章 *Building a Foundation* 中定义的自动加载器，使用 `Application\Database\Connection` 以及新创建的 `Application\Entity\Customer` 类：

```php
<?php
define('DB_CONFIG_FILE', '/../config/db.config.php');
require __DIR__ . '/../Application/Autoload/Loader.php';
Application\Autoload\Loader::init(__DIR__ . '/../');
use Application\Database\Connection;
use Application\Entity\Customer;
```

接下来，获取数据库连接，并使用该连接随机获取一个客户的数据关联数组：

```php
$conn = new Connection(include __DIR__ . DB_CONFIG_FILE);
$id = rand(1, 79);
$stmt = $conn->pdo->prepare(
'SELECT * FROM customer WHERE id = :id');
$stmt->execute(['id' => $id]);
$result = $stmt->fetch(PDO::FETCH_ASSOC);
```

最后，你可以从数组创建一个新的 Customer 实体实例，并使用 `var_dump()` 查看结果：

```php
$cust = Customer::arrayToEntity($result, new Customer());
var_dump($cust);
```

以下是上述代码的输出：

![](img/39390f6d56c5a83b28db083a8bd5185c_177_0.png)

### 参见

有许多优秀的著作描述了领域模型。最具影响力的可能是 Martin Fowler 的 *Patterns of Enterprise Application Architecture*（参见 [http://martinfowler.com/books/ea.html](http://martinfowler.com/books/ea.html)）。还有一项出色的研究，也可免费下载，题为 *Domain Driven Design Quickly*，由 InfoQ 发布（参见 [http://www.infoq.com/minibooks/domain-driven-design-quickly](http://www.infoq.com/minibooks/domain-driven-design-quickly)）。

## 将实体类与 RDBMS 查询绑定

大多数具有商业可行性的 RDBMS 系统都是在过程式编程处于主导地位的时代演变而来的。想象一下，RDBMS 世界是二维的、方形的，并且面向过程的。相比之下，实体可以被认为是圆形的、三维的，并且面向对象的。这给你展示了一个图景：我们将如何通过将 RDBMS 查询的结果绑定到实体实例的迭代中来实现目标。

![](img/39390f6d56c5a83b28db083a8bd5185c_178_0.png)

现代 RDBMS 系统所基于的**关系模型**，最早由数学家 Edgar F. Codd 在 1969 年描述。第一个具有商业可行性的系统在 20 世纪 70 年代中后期演变出来。换句话说，RDBMS 技术已经发展了 40 多年！

### 如何操作...

- 首先，我们需要设计一个类来承载我们的查询逻辑。如果你遵循领域模型，这个类可能被称为**仓储（repository）**。或者，为了保持简单和通用，我们可以简单地将新类命名为 `Application\Database\CustomerService`。该类将接受一个 `Application\Database\Connection` 实例作为参数：

```
namespace Application\Database;

use Application\Entity\Customer;

class CustomerService
{
    protected $connection;

    public function __construct(Connection $connection)
    {
        $this->connection = $connection;
    }
}
```

- 现在我们将定义一个 `fetchById()` 方法，它接受一个客户 ID 作为参数，并返回单个 `Application\Entity\Customer` 实例，或者在失败时返回布尔值 **FALSE**。乍一看，简单地使用 `PDOStatement::fetchObject()` 并指定实体类作为参数似乎是显而易见的选择：

```
public function fetchById($id)
{
    $stmt = $this->connection->pdo
            ->prepare(Finder::select('customer')
                       ->where('id = :id')->getSql());
    $stmt->execute(['id' => (int) $id]);
    return $stmt->fetchObject('Application\Entity\Customer');
}
```

![](img/39390f6d56c5a83b28db083a8bd5185c_179_0.png)

然而，这里的危险在于 `fetchObject()` 实际上会在构造函数调用之前填充属性（即使是受保护的属性）！相应地，存在构造函数可能意外覆盖值的危险。如果你不定义构造函数，或者你可以容忍这种危险，我们就完成了。否则，正确实现 RDBMS 查询与 OOP 结果之间的绑定变得更加困难。

- `fetchById()` 方法的另一种方法是先创建对象实例，从而运行其构造函数，并将获取模式设置为 `PDO::FETCH_Into`，如下例所示：

```
public function fetchById($id)
{
    $stmt = $this->connection->pdo
        ->prepare(Finder::select('customer')
        ->where('id = :id')->getSql());
    $stmt->execute(['id' => (int) $id]);
    $stmt->setFetchMode(PDO::FETCH_Into, new Customer());
    return $stmt->fetch();
}
```

- 然而，这里我们又遇到了一个问题：`fetch()` 与 `fetchObject()` 不同，它无法覆盖受保护的属性；如果尝试这样做，会生成以下错误消息。这意味着我们必须要么将所有属性定义为 `public`，要么考虑另一种方法。

![](img/39390f6d56c5a83b28db083a8bd5185c_179_1.png)

- 我们要考虑的另一种方法是以数组形式获取结果，并手动填充实体。尽管这种方法在性能上稍显昂贵，但它允许任何潜在的实体构造函数正确运行，并将属性安全地定义为 private 或 protected：

```
public function fetchById($id)
{
    $stmt = $this->connection->pdo
             ->prepare(Finder::select('customer')
                        ->where('id = :id')->getSql());
    $stmt->execute(['id' => (int) $id]);
    return Customer::arrayToEntity(
               $stmt->fetch(PDO::FETCH_ASSOC));
}
```

- 要处理产生多个结果的查询，我们只需要生成一系列已填充的实体对象。在本例中，我们实现了一个 `fetchByLevel()` 方法，该方法以 `Application\Entity\Customer` 实例的形式返回给定级别的所有客户：

```
public function fetchByLevel($level)
{
    $stmt = $this->connection->pdo->prepare(
            Finder::select('customer')
                    ->where('level = :level')->getSql());
    $stmt->execute(['level' => $level]);
    while ($row = $stmt->fetch(PDO::FETCH_ASSOC)) {
        yield Customer::arrayToEntity($row, new Customer());
    }
}
```

- 我们希望实现的下一个方法是 `save()`。然而，在继续之前，必须考虑如果执行了 INSERT 操作，将返回什么值。

- 通常，我们会在 INSERT 之后返回新完成的实体类。有一个方便的 `PDO::lastInsertId()` 方法，乍一看似乎可以做到这一点。但进一步阅读文档后发现，并非所有数据库扩展都支持此功能，且支持该功能的扩展在实现上也不一致。因此，最好有一个除了 `$id` 之外的唯一列，可用于唯一标识新客户。

- 在本例中，我们选择了 email 列，因此需要实现一个 `fetchByEmail()` 服务方法：

```
public function fetchByEmail($email)
{
    $stmt = $this->connection->pdo->prepare(
            Finder::select('customer')
```




10. 现在，我们准备定义 `save()` 方法。我们不区分 INSERT 和 UPDATE，而是设计该方法为：如果 ID 已存在，则执行更新操作；否则执行插入操作。

11. 首先，我们定义一个基本的 `save()` 方法，该方法接收一个 Customer 实体作为参数，并使用 `fetchById()` 来确定此条目是否已存在。如果存在，我们调用 `doUpdate()` 更新方法；否则，我们调用 `doInsert()` 插入方法：

```php
public function save(Customer $cust)
{
    // check to see if customer ID > 0 and exists
    if ($cust->getId() && $this->fetchById($cust->getId())) {
        return $this->doUpdate($cust);
    } else {
        return $this->doInsert($cust);
    }
}
```

12. 接下来，我们定义 `doUpdate()`，它将 Customer 实体对象的属性提取到一个数组中，构建初始 SQL 语句，并调用 `flush()` 方法，将数据推送到数据库。我们不希望更新 ID 字段，因为它是主键。此外，我们需要指定要更新哪一行，这意味着追加一个 WHERE 子句：

```php
protected function doUpdate($cust)
{
    // get properties in the form of an array
    $values = $cust->entityToArray();
    // build the SQL statement
    $update = 'UPDATE ' . $cust::TABLE_NAME;
    $where = ' WHERE id = ' . $cust->getId();
    // unset ID as we do not want this to be updated
    unset($values['id']);
    return $this->flush($update, $values, $where);
}
```

13. `doInsert()` 方法类似，只是初始 SQL 需要以 `INSERT INTO ...` 开头，并且需要取消设置（unset） id 数组元素。后者的原因是我们希望此属性由数据库自动生成。如果成功，我们使用新定义的 `fetchByEmail()` 方法查找新客户并返回一个完整的实例：

```php
protected function doInsert($cust)
{
    $values = $cust->entityToArray();
    $email = $cust->getEmail();
    unset($values['id']);
    $insert = 'INSERT INTO ' . $cust::TABLE_NAME . ' ';
    if ($this->flush($insert, $values)) {
        return $this->fetchByEmail($email);
    } else {
        return FALSE;
    }
}
```

14. 最后，我们处于可以定义 `flush()` 的位置，该方法执行实际的准备和执行：

```php
protected function flush($sql, $values, $where = '')
{
    $sql .= ' SET ';
    foreach ($values as $column => $value) {
        $sql .= $column . ' = :' . $column . ',';
    }
    // get rid of trailing ','
    $sql = substr($sql, 0, -1) . $where;
    $success = FALSE;
    try {
        $stmt = $this->connection->pdo->prepare($sql);
        $stmt->execute($values);
        $success = TRUE;
    } catch (PDOException $e) {
        error_log(__METHOD__ . ':' . __LINE__ . ':'
            . $e->getMessage());
        $success = FALSE;
    } catch (Throwable $e) {
        error_log(__METHOD__ . ':' . __LINE__ . ':'
            . $e->getMessage());
        $success = FALSE;
    }
    return $success;
}
```

15. 为了结束讨论，我们需要定义一个 `remove()` 方法，该方法从数据库中删除一个客户。同样，正如之前定义的 `save()` 方法那样，我们使用 `fetchById()` 来确保操作成功：

```php
public function remove(Customer $cust)
{
    $sql = 'DELETE FROM ' . $cust::TABLE_NAME . ' WHERE id = :id';
    $stmt = $this->connection->pdo->prepare($sql);
    $stmt->execute(['id' => $cust->getId()]);
    return ($this->fetchById($cust->getId())) ? FALSE : TRUE;
}
```

## 工作原理...

将步骤 1 到 5 中描述的代码复制到 Application/Database 文件夹中的 `CustomerService.php` 文件。定义一个 `chap_05_entity_to_query.php` 调用程序。让调用程序初始化自动加载器，并使用适当的类：

```php
<?php
define('DB_CONFIG_FILE', '/../config/db.config.php');
require __DIR__ . '/../Application/Autoload/Loader.php';
Application\Autoload\Loader::init(__DIR__ . '/../..');
use Application\Database\Connection;
use Application\Database\CustomerService;
```

现在，你可以创建服务的一个实例，并随机获取单个客户。该服务将返回一个客户实体作为结果：

```php
// get service instance
$service = new CustomerService(new Connection(
    include __DIR__ . DB_CONFIG_FILE));

echo "\nSingle Result\n";
var_dump($service->fetchById(rand(1,79)));
```

## 与数据库交互

以下是输出结果：

![](img/39390f6d56c5a83b28db083a8bd5185c_184_0.png)

现在，将步骤 6 到 15 中显示的代码复制到服务类中。将要插入的数据添加到 `chap_05_entity_to_query.php` 调用程序中。然后，我们使用这些数据生成一个 Customer 实体实例：

```php
// sample data
$data = [
    'name'                => 'Doug Bierer',
    'balance'             => 326.33,
    'email'               => 'doug'. rand(0,999) . '@test.com',
    'password'            => 'password',
    'status'              => 1,
    'security_question'   => 'Who\'s on first?',
    'confirm_code'        => 12345,
    'level'               => 'ADV'
];

// create new Customer
$cust = Customer::arrayToEntity($data, new Customer());
```

然后，我们可以检查调用 `save()` 之前和之后的 ID：

```php
echo "\nCustomer ID BEFORE Insert: {$cust->getId()}\n";
$cust = $service->save($cust);
echo "Customer ID AFTER Insert: {$cust->getId()}\n";
```

最后，我们修改余额，并再次调用 `save()`，查看结果：

```php
echo "Customer Balance BEFORE Update: {$cust->getBalance()}\n";
$cust->setBalance(999.99);
$service->save($cust);
echo "Customer Balance AFTER Update: {$cust->getBalance()}\n";
var_dump($cust);
```

以下是调用程序的输出：

![](img/39390f6d56c5a83b28db083a8bd5185c_185_0.png)

## 更多内容...

有关关系模型的更多信息，请参阅 [https://en.wikipedia.org/wiki/Relational_model](https://en.wikipedia.org/wiki/Relational_model)。有关 RDBMS 的更多信息，请参阅 [https://en.wikipedia.org/wiki/Relational_database_management_system](https://en.wikipedia.org/wiki/Relational_database_management_system)。有关 `PDOStatement::fetchObject()` 如何在构造函数之前插入属性值的信息，请查看 php.net 文档中 `fetchObject()` 引用中 "rasmu at mindplay dot dk" 的评论（[http://php.net/manual/en/pdostatement.fetchobject.php](http://php.net/manual/en/pdostatement.fetchobject.php)）。

## 在查询结果中嵌入二级查找

在实现实体类之间关系的道路上，让我们先看看如何嵌入执行二级查找所需的代码。这种查找的一个例子是在显示客户信息时，让视图逻辑执行第二个查找，获取该客户的购买列表。

![](img/39390f6d56c5a83b28db083a8bd5185c_186_0.png)

## 实现方法...

1. 首先，定义一个根据 ID 查找客户的函数。为了便于说明，我们将简单地使用 `PDO::FETCH_ASSOC` 获取模式获取数组。我们还将继续使用第 1 章“构建基础”中讨论的 `Application\Database\Connection` 类：

```php
function findCustomerById($id, Connection $conn)
{
    $stmt = $conn->pdo->query(
        'SELECT * FROM customer WHERE id = ' . (int) $id);
    $results = $stmt->fetch(PDO::FETCH_ASSOC);
    return $results;
}
```

2. 接下来，我们分析 purchases 表，看看 customer 表和 product 表是如何链接的。如该表的 CREATE 语句所示，customer_id 和 product_id 外键构成了关系：

```sql
CREATE TABLE 'purchases' (
    'id' int(11) NOT NULL AUTO_INCREMENT,
    'transaction' varchar(8) NOT NULL,
    'date' datetime NOT NULL,
    'quantity' int(10) unsigned NOT NULL,
    'sale_price' decimal(8,2) NOT NULL,
    'customer_id' int(11) DEFAULT NULL,
    'product_id' int(11) DEFAULT NULL,
    PRIMARY KEY ('id'),
```




## 操作指南...

- 1. 创建数据库模式。
- 2. 添加键和约束：

```sql
KEY 'IDX_C3F3' ('customer_id'),
KEY 'IDX_665A' ('product_id'),
CONSTRAINT 'FK_665A' FOREIGN KEY ('product_id')
  REFERENCES 'products' ('id'),
CONSTRAINT 'FK_C3F3' FOREIGN KEY ('customer_id')
  REFERENCES 'customer' ('id')
);
```

- 3. 我们现在扩展原始的 `findCustomerId()` 函数，以匿名函数的形式定义次要查询，该函数随后可以在视图脚本中执行。该匿名函数被赋值给 `$results['purchases']` 元素：

```php
function findCustomerId($id, Connection $conn)
{
    $stmt = $conn->pdo->query(
        'SELECT * FROM customer WHERE id = ' . (int) $id);
    $results = $stmt->fetch(PDO::FETCH_ASSOC);
    if ($results) {
        $results['purchases'] =
            // 定义次要查询
            function ($id, $conn) {
                $sql = 'SELECT * FROM purchases AS u '
                    . 'JOIN products AS r '
                    . 'ON u.product_id = r.id '
                    . 'WHERE u.customer_id = :id '
                    . 'ORDER BY u.date';
                $stmt = $conn->pdo->prepare($sql);
                $stmt->execute(['id' => $id]);
                while ($row = $stmt->fetch(PDO::FETCH_ASSOC)) {
                    yield $row;
                }
            };
    }
    return $results;
}
```

- 4. 假设我们已成功将客户信息检索到 `$results` 数组中，在视图逻辑中，我们只需要遍历匿名函数的返回值即可。在本例中，我们随机检索客户信息：

```php
$result = findCustomerId(rand(1, 79), $conn);
```

- 5. 在视图逻辑中，我们遍历由次要查询返回的结果。以下代码高亮显示了对嵌入式匿名函数的调用：

```html
<table>
  <tr>
    <th>Transaction</th><th>Date</th><th>Qty</th>
    <th>Price</th><th>Product</th>
  </tr>
<?php
  foreach ($result['purchases']($result['id'], $conn) as $purchase) :
  ?>
    <tr>
      <td><?= $purchase['transaction'] ?></td>
      <td><?= $purchase['date'] ?></td>
      <td><?= $purchase['quantity'] ?></td>
      <td><?= $purchase['sale_price'] ?></td>
      <td><?= $purchase['title'] ?></td>
    </tr>
<?php endforeach; ?>
</table>
```

## 工作原理...

创建一个 `chap_05_secondary_lookups.php` 调用程序，并插入创建 `Application\Database\Connection` 实例所需的代码：

```php
<?php
define('DB_CONFIG_FILE', './../config/db.config.php');
include __DIR__ . './../Application/Database/Connection.php';
use Application\Database\Connection;
$conn = new Connection(include __DIR__ . DB_CONFIG_FILE);
```

接下来，添加第 3 步中所示的 `findCustomerById()` 函数。然后，你可以提取随机客户的信息，结束调用程序的 PHP 部分：

```php
function findCustomerById($id, Connection $conn)
{
  // 以上编号 #3 中所示的代码
}
$result = findCustomerById(rand(1,79), $conn);
?>
```

对于视图逻辑，你可以如前几道食谱中所示，显示核心客户信息：

```html
<h1><?=$result['name']?></h1>
<div class="row">
<div class="left">Balance</div>
<div class="right"><?=$result['balance']?></div>
</div>
<!-- 等等 -->
```

你可以像这样显示购买信息：

```html
<table>
<tr><th>Transaction</th><th>Date</th><th>Qty</th>
<th>Price</th><th>Product</th></tr>
<?php
foreach ($result['purchases']($result['id'], $conn) as $purchase) : ?>
<tr>
<td><?=$purchase['transaction']?></td>
<td><?=$purchase['date']?></td>
<td><?=$purchase['quantity']?></td>
<td><?=$purchase['sale_price']?></td>
<td><?=$purchase['title']?></td>
</tr>
<?php endforeach; ?>
</table>
```

关键在于，通过调用嵌入式匿名函数 `$result['purchases']($result['id'], $conn)`，次要查询作为视图逻辑的一部分被执行。以下是输出结果：

![](img/39390f6d56c5a83b28db083a8bd5185c_189_0.png)

## 实现 jQuery DataTables PHP 查询

对次要查询的另一种方法是让前端生成请求。在本食谱中，我们将对前一个食谱“将次要查询嵌入到 QueryResults 中”中介绍的次要查询代码进行 slight 修改。在之前的食谱中，尽管视图逻辑执行查询，但所有处理仍在服务器端完成。然而，使用 **jQuery DataTables** 时，次要查询实际上是由客户端直接执行的，形式为由浏览器发出的 **异步 JavaScript 和 XML (AJAX)** 请求。

### 操作指南...

- 1. 首先，我们需要将次要查询逻辑（在上面的食谱中讨论过）分离到一个单独的 PHP 文件中。这个新脚本的目的是执行次要查询并返回一个 JSON 数组。
- 2. 我们将新脚本命名为 `chap_05_jquery_datatables_php_lookups_ajax.php`。它查找 `$_GET` 参数 `id`。请注意，SELECT 语句非常具体地指定了提供哪些列。您还会注意到获取模式已更改为 `PDO::FETCH_NUM`。您还可能注意到最后一行将结果赋值给 JSON 编码数组中的 `data` 键。

![](img/39390f6d56c5a83b28db083a8bd5185c_190_0.png)

> 在处理零配置 jQuery DataTables 时，只返回与表头匹配的确切列数是*极其*重要的。

```php
$id = $_GET['id'] ?? 0;
$sql = 'SELECT u.transaction,u.date,
        u.quantity,u.sale_price,r.title '
    . 'FROM purchases AS u '
    . 'JOIN products AS r '
    . 'ON u.product_id = r.id '
    . 'WHERE u.customer_id = :id';
$stmt = $conn->pdo->prepare($sql);
$stmt->execute(['id' => (int) $id]);
$results = array();
while ($row = $stmt->fetch(PDO::FETCH_NUM)) {
    $results[] = $row;
}
echo json_encode(['data' => $results]);
```

- 3. 接下来，我们需要修改按 ID 检索客户信息的函数，移除前一个食谱中嵌入的次要查询：

```php
function findCustomerIdById($id, Connection $conn)
{
    $stmt = $conn->pdo->query(
        'SELECT * FROM customer WHERE id = '. (int) $id);
    $results = $stmt->fetch(PDO::FETCH_ASSOC);
    return $results;
}
```

- 4. 然后，在视图逻辑中，我们导入用于零配置实现的最小 jQuery、DataTables 和样式表。至少，你需要 jQuery 本身（本例中为 `jquery-1.12.0.min.js`）和 DataTables (`jquery.dataTables.js`)。我们还添加了一个与 DataTables 相关的便捷样式表 `jquery.dataTables.css`：

```html
<!DOCTYPE html>
<head>
    <script src="https://code.jquery.com/jquery-1.12.0.min.js">
    </script>
    <script type="text/javascript"
        charset="utf8"
        src="//cdn.datatables.net/1.10.11/js/jquery.dataTables.js">
    </script>
    <link rel="stylesheet"
        type="text/css"
        href="//cdn.datatables.net/1.10.11/css/jquery.dataTables.css">
</head>
```

- 5. 然后，我们定义一个 jQuery 文档就绪函数，将表格关联到 DataTables。在这种情况下，我们将 `customerTable` 的 id 属性分配给将被分配给 DataTables 的表格元素。您还会注意到，我们将 AJAX 数据源指定为第 1 步中定义的脚本 `chap_05_jquery_datatables_php_lookups_ajax.php`。由于我们有 `$id` 可用，这会被附加到数据源 URL：

```html
<script>
    $(document).ready(function() {
        $('#customerTable').DataTable(
            { "ajax": '/chap_05_jquery_datatables_php_lookups_ajax.php?id=<?= $id ?>'}
        );
    });
</script>
```

- 6. 在视图逻辑的主体中，我们定义表格，确保 `id` 属性与前一段代码中指定的匹配。我们还需要定义与 AJAX 请求响应中提供的数据匹配的表头：

```html
<table id="customerTable" class="display" cellspacing="0"
       width="100%">
  <thead>
    <tr>
      <th>Transaction</th>
      <th>Date</th>
      <th>Qty</th>
      <th>Price</th>
      <th>Product</th>
    </tr>
  </thead>
</table>
```

- 7. 现在，剩下的唯一事情就是加载页面，选择客户 ID（在这种情况下是随机的），并让 jQuery 发起次要查询请求。

## 工作原理...

创建一个 `chap_05_jquery_databases_php_lookups_ajax.php` 脚本，它将响应 AJAX 请求。在其中，放置初始化自动加载和创建 Connection 实例的代码。然后，你可以添加前面食谱第 2 步中所示的代码：

```php
<?php
define('DB_CONFIG_FILE', '../../config/db.config.php');
include __DIR__ . '/../Application/Database/Connection.php';
use Application\Database\Connection;
$conn = new Connection(include __DIR__ . DB_CONFIG_FILE);
```

接下来，创建一个 `chap_05_jquery_databases_php_lookups.php` 调用程序，它将获取随机客户的信息。添加前面代码第 3 步中描述的函数：

```php
<?php
define('DB_CONFIG_FILE', '../../config/db.config.php');
include __DIR__ . '/../Application/Database/Connection.php';
use Application\Database\Connection;
$conn = new Connection(include __DIR__ . DB_CONFIG_FILE);
// 在此处添加 findCustomerById() 函数
$id = random_int(1,79);
$result = findCustomerById($id, $conn);
?>
```





调用程序还将包含导入实现 jQuery DataTables 所需的最小 JavaScript 的视图逻辑。你可以添加前面代码第 3 步中显示的代码。然后，添加第 5 步和第 6 步中显示的文档就绪函数和显示逻辑。输出如下：

![](img/39390f6d56c5a83b28db083a8bd5185c_193_0.png)

![](img/39390f6d56c5a83b28db083a8bd5185c_193_1.png)

### 威尔弗里多·泰勒

- **余额**：25.11
- **邮箱**：wilfredo.taylor@telecom.net
- **状态**：1
- **级别**：BEG

显示：10 条记录  
搜索：

| **交易号** | **日期** | **数量** | **价格** | **产品** |
|---|---|---|---|---|
| APJ8650 | 2003-04-17 00:15:27 | 3 | 11.10 | 冰淇淋蛋糕 |
| AQP8375 | 2006-07-20 03:12:51 | 14 | 30.80 | 安布罗西亚沙拉 |
| BQO6079 | 1994-11-10 17:49:11 | 3 | 16.20 | 燕麦葡萄干饼干 |
| BHR1274 | 2004-03-20 08:24:13 | 17 | 75.50 | 香蕉船 |
| BMC1921 | 2013-02-22 19:39:15 | 7 | 12.50 | 苹果派 |
| BME5477 | 2011-06-27 01:18:51 | 6 | 12.60 | 木薯布丁 |
| BUY4627 | 2014-05-06 01:07:04 | 15 | 30.00 | 糖霜甜甜圈 |
| CJH3811 | 1997-12-09 01:19:36 | 15 | 78.00 | 戴维斯食品蛋糕 |
| CPN1308 | 2008-11-14 01:47:20 | 5 | 7.00 | 花生酱饼干 |
| CPV1728 | 2000-05-22 23:50:23 | 8 | 48.00 | 薄荷巧克力奶昔 |

显示第 1 到 10 条，共 88 条记录    上一页 1 2 3 4 5 ... 9 下一页

## 更多相关…

有关 jQuery 的更多信息，请访问其网站：https://jquery.com/。要阅读关于 jQuery 的 DataTables 插件，请参考这篇文章：https://www.datatables.net/。零配置数据表在 https://datatables.net/examples/basic_init/zero_configuration.html 中讨论。有关 AJAX 源数据的更多信息，请查看 https://datatables.net/examples/data_sources/ajax.html。

# 6

## 构建可扩展的网站

在本章中，我们将涵盖以下主题：

- 创建通用的表单元素生成器
- 创建 HTML 单选按钮元素生成器
- 创建 HTML 选择框元素生成器
- 实现表单工厂
- 链式 `$_POST` 过滤器
- 链式 `$_POST` 验证器
- 将验证绑定到表单

## 引言

在本章中，我们将向你展示如何构建生成 HTML 表单元素的类。通用元素生成器可用于文本、文本区域、密码以及类似的 HTML 输入类型。之后，我们将展示允许你通过值数组预配置元素的变体。表单工厂配方将把所有这些生成器结合在一起，允许你使用单个配置数组渲染整个表单。最后，我们介绍允许过滤和验证传入 `$_POST` 数据的配方。

### 创建通用的表单元素生成器

创建一个简单地输出表单输入标签（例如 `<input type="text" name="whatever">`）的函数非常容易。然而，为了使表单生成器具有通用性，我们需要从大局出发进行思考。除了基本的输入标签外，还有一些其他需要考虑的事项：

- 表单输入标签及其关联的 HTML 属性
- 一个告知用户他们正在输入什么信息的标签
- 在验证后显示输入错误的功能（稍后会更详细地介绍！）
- 某种封装器，例如 `<div>` 标签或 HTML 表格 `<td>` 标签

### 操作方式...

1. 首先，我们定义一个 `Application\Form\Generic` 类。这也将在以后作为专用表单元素的基类：
   ```php
   namespace Application\Form;

   class Generic
   {
       // some code ...
   }
   ```
2. 接下来，我们定义一些类常量，它们在表单元素生成中通常是有用的。
3. 前三个将成为与单个表单元素主要组件关联的键。然后我们定义支持的输入类型和默认值：
   ```php
   const ROW = 'row';
   const FORM = 'form';
   const INPUT = 'input';
   const LABEL = 'label';
   const ERRORS = 'errors';
   const TYPE_FORM = 'form';
   const TYPE_TEXT = 'text';
   const TYPE_EMAIL = 'email';
   const TYPE_RADIO = 'radio';
   const TYPE_SUBMIT = 'submit';
   const TYPE_SELECT = 'select';
   const TYPE_PASSWORD = 'password';
   const TYPE_CHECKBOX = 'checkbox';
   const DEFAULT_TYPE = self::TYPE_TEXT;
   const DEFAULT_WRAPPER = 'div';
   ```

4. 接下来，我们可以定义属性以及设置它们的构造函数。
5. 在这个例子中，我们要求两个属性，`$name` 和 `$type`，因为没有这些属性无法有效地使用元素。其他构造函数参数是可选的。此外，为了基于另一个表单元素构建一个表单元素，我们提供了一种机制，其中第二个参数 `$type` 也可以是 `Application\Form\Generic` 的实例，在这种情况下，我们只需运行 getter（稍后讨论）来填充属性：

   ```php
   protected $name;
   protected $type = self::DEFAULT_TYPE;
   protected $label = '';
   protected $errors = array();
   protected $wrappers;
   protected $attributes; // HTML form attributes
   protected $pattern = '<input type="$$" name="$s" $s>';
   ```

   ```php
   public function __construct($name,
                               $type,
                               $label = '',
                               array $wrappers = array(),
                               array $attributes = array(),
                               array $errors = array())
   {
       $this->name = $name;
       if ($type instanceof Generic) {
           $this->type    = $type->getType();
           $this->label   = $type->getLabelValue();
           $this->errors  = $type->getErrorsArray();
           $this->wrappers = $type->getWrappers();
           $this->attributes = $type->getAttributes();
       } else {
           $this->type    = $type ?? self::DEFAULT_TYPE;
           $this->label   = $label;
           $this->errors  = $errors;
           $this->attributes = $attributes;
           if ($wrappers) {
               $this->wrappers = $wrappers;
           } else {
               $this->wrappers[self::INPUT]['type'] = self::DEFAULT_WRAPPER;
               $this->wrappers[self::LABEL]['type'] = self::DEFAULT_WRAPPER;
               $this->wrappers[self::ERRORS]['type'] = self::DEFAULT_WRAPPER;
           }
       }
       $this->attributes['id'] = $name;
   }
   ```

> 请注意，`$wrappers` 有三个主要子键：`INPUT`、`LABEL` 和 `ERRORS`。这允许我们为标签、输入标签和错误定义单独的封装器。

6. 在定义将产生标签、输入标签和错误的 HTML 的核心方法之前，我们应该定义一个 `getWrapperPattern()` 方法，它将产生用于标签、输入和错误显示的适当封装标签。
7. 例如，如果封装器定义为 `<div>`，并且其属性包括 `['class' => 'label']`，此方法将返回一个看起来像这样的 `sprintf()` 格式模式：`<div class="label">%s</div>`。最终为标签产生的 HTML 将替换 `%s`。
8. 以下是 `getWrapperPattern()` 方法可能看起来的样子：
   ```php
   public function getWrapperPattern($type)
   {
       $pattern = '<' . $this->wrappers[$type]['type'];
       foreach ($this->wrappers[$type] as $key => $value) {
           if ($key != 'type') {
               $pattern .= ' ' . $key . '="' . $value . '"';
           }
       }
       $pattern .= '>' . $s . '</' . $this->wrappers[$type]['type'] . '>';
       return $pattern;
   }
   ```

9. 我们现在准备定义 `getLabel()` 方法。此方法只需要使用 `sprintf()` 将标签插入封装器中即可：
   ```php
   public function getLabel()
   {
       return sprintf($this->getWrapperPattern(self::LABEL),
                      $this->label);
   }
   ```

10. 为了产生核心输入标签，我们需要一种方法来组装属性。幸运的是，只要以关联数组的形式提供给构造函数，这就很容易实现。在这种情况下，我们需要做的就是定义一个 `getAttrs()` 方法，它产生由空格分隔的键值对字符串。我们使用 `trim()` 移除多余的空格并返回最终值。




11. 如果元素包含 value 或 href 属性中的任意一个，出于安全原因，我们应当假设这些值是由用户提供的（因此是可疑的），并对它们进行转义。相应地，我们需要添加一个 if 语句来检查，然后使用 htmlspecialchars() 或 urlencode()：

```php
public function getAttrs() 
{
    foreach ($this->attributes as $key => $value) {
        $key = strtolower($key);
        if ($value) {
            if ($key == 'value') {
                if (is_array($value)) {
                    foreach ($value as $i => $j) {
                        $value[$i] = htmlspecialchars($i);
                    } else {
                        $value = htmlspecialchars($value);
                    }
                } elseif ($key == 'href') {
                    $value = urlencode($value);
                }
                $attrs .= $key . '="' . $value . '"';
            } else {
                $attrs .= $key . ' ';
            }
        }
    }
    return trim($attrs);
}
```

12. 对于核心 input 标签，我们将逻辑拆分为两个独立的方法。主要方法 getInputOnly() 仅生成 HTML input 标签。第二个方法 getInputWithWrapper() 生成嵌入在包装器中的 input。拆分的原因是，在创建派生类（例如生成单选按钮的类）时，我们将不需要包装器：

```php
public function getInputOnly() 
{
    return sprintf($this->pattern, $this->type, $this->name,
                    $this->getAttrs());
}

public function getInputWithWrapper() 
{
    return sprintf($this->getWrapperPattern(self::INPUT),
                    $this->getInputOnly());
}
```

13. 我们现在定义一个方法来显示元素验证错误。我们假设错误将以数组形式提供。如果没有错误，我们返回空字符串。否则，错误将渲染为 `<ul><li>error 1</li><li>error 2</li></ul>`，依此类推：

```php
public function getErrors()
{
    if (!$this->errors || count($this->errors) == 0) return '';
    $html = '';
    $pattern = '<li>%s</li>';
    $html .= '<ul>';
    foreach ($this->errors as $error)
        $html .= sprintf($pattern, $error);
    $html .= '</ul>';
    return sprintf($this->getWrapperPattern(self::ERRORS), $html);
}
```

14. 对于某些属性，我们可能需要对属性的各个方面进行更有限的控制。例如，我们可能需要向现有的错误数组中添加单个错误。此外，设置单个属性也可能很有用：

```php
public function setSingleAttribute($key, $value)
{
    $this->attributes[$key] = $value;
}

public function addSingleError($error)
{
    $this->errors[] = $error;
}
```

15. 最后，我们定义 getter 和 setter，以便我们可以检索或设置属性的值。例如，你可能注意到 $pattern 的默认值是 `<input type="%s" name="%s" $attrs>`。对于某些标签（例如 select 和 form 标签），我们需要将此属性设置为不同的值：

```php
public function setPattern($pattern)
{
    $this->pattern = $pattern;
}

public function setType($type)
{
    $this->type = $type;
}

public function getType()
{
    return $this->type;
}

public function addSingleError($error)
{
    $this->errors[] = $error;
}
// 为 name, label, wrappers, errors 和 attributes 定义类似的 get 和 set 方法
```

16. 我们还需要添加方法，用于获取标签值（而不是 HTML）以及错误数组：

```php
public function getLabelValue()
{
    return $this->label;
}

public function getErrorsArray()
{
    return $this->errors;
}
```

## 工作原理...

请确保将上述所有代码复制到一个单一的 `Application\Form\Generic` 类中。然后，你可以定义一个 `chap_06_form_element_generator.php` 调用脚本，用于设置自动加载并锚定新的类：

```php
<?php
    require __DIR__ . '/../Application/Autoload/Loader.php';
    Application\Autoload\Loader::init(__DIR__ . '/..');
    use Application\Form\Generic;
```

接下来，定义包装器。为了说明，我们将使用 HTML 表格数据（data）和标题（header）标签。注意标签使用 `TH`，而 input 和错误使用 `TD`：

```php
$wrappers = [
    Generic::INPUT => ['type' => 'td', 'class' => 'content'],
    Generic::LABEL => ['type' => 'th', 'class' => 'label'],
    Generic::ERRORS => ['type' => 'td', 'class' => 'error']
];
```

现在你可以通过将参数传递给构造函数来定义一个电子邮件元素：

```php
$email = new Generic('email', Generic::TYPE_EMAIL, 'Email', $wrappers, ['id' => 'email', 'maxLength' => 128, 'title' => 'Enter address', 'required' => '']);
```

或者，使用 setter 定义密码元素：

```php
$password = new Generic('password', $email);
$password->setType(Generic::TYPE_PASSWORD);
$password->setLabel('Password');
$password->setAttributes(['id' => 'password',
'title' => 'Enter your password',
'required' => '']);
```

最后，请确保定义一个提交按钮：

```php
$submit = new Generic('submit',
Generic::TYPE_SUBMIT,
'Login',
$wrappers,
['id' => 'submit','title' => 'Click to login','value' =>
'Click Here']);
```

实际的显示逻辑可能如下所示：

```html
<div class="container">
<!-- Login Form -->
<h1>Login</h1>
<form name="login" method="post">
<table id="login" class="display"
cellspacing="0" width="100%">
<tr><? $email->render(); ?></tr>
<tr><? $password->render(); ?></tr>
<tr><? $submit->render(); ?></tr>
<tr>
<td colspan=2>
<br>
<?php var_dump($_POST); ?>
</td>
</tr>
</table>
</form>
</div>
```

这是实际输出：

![](img/39390f6d56c5a83b28db083a8bd5185c_203_0.png)

## 创建 HTML 单选元素生成器

单选按钮元素生成器将与通用的 HTML 表单元素生成器有相似之处。与任何通用元素一样，一组单选按钮需要能够显示整体标签和错误。然而，有两个主要区别：

- 通常，你会想要两个或更多单选按钮
- 每个按钮需要有自己的标签

## 具体操作...

1. 首先，创建一个继承自 `Application\Form\Generic` 的新 `Application\Form\Element\Radio` 类：
```php
namespace Application\Form\Element;
use Application\Form\Generic;
class Radio extends Generic
{
// code
}
```
2. 接下来，我们定义与单选按钮组特殊需求相关的类常量和属性。
3. 在这个示例中，我们需要一个间隔符，它将放在单选按钮和其标签之间。我们还需要决定是将单选按钮标签放在实际按钮之前还是之后，因此我们使用 `$after` 标志。如果需要默认值，或者如果我们要重新显示现有的表单数据，我们需要一种方式来指定选定的键。最后，我们需要一个选项数组，我们将用它来填充按钮列表：
```php
const DEFAULT_AFTER = TRUE;
const DEFAULT_SPACER = '&nbsp;';
const DEFAULT_OPTION_KEY = 0;
const DEFAULT_OPTION_VALUE = 'Choose';

protected $after = self::DEFAULT_AFTER;
protected $spacer = self::DEFAULT_SPACER;
protected $options = array();
protected $selectedKey = DEFAULT_OPTION_KEY;
```
4. 由于我们要扩展 Application\Form\Generic，我们可以选择扩展 `__construct()` 方法，或者，选择定义一个可用于设置特定选项的方法。在这个示例中，我们选择了后者。
5. 为了确保属性 `$this->options` 被填充，第一个参数（`$options`）被定义为强制性的（没有默认值）。所有其他参数都是 **可选的**。
```php
public function setOptions(array $options,
    $selectedKey = self::DEFAULT_OPTION_KEY,
    $spacer = self::DEFAULT_SPACER,
    $after = TRUE)
{
    $this->after = $after;
    $this->spacer = $spacer;
    $this->options = $options;
    $this->selectedKey = $selectedKey;
}
```

6. 最后，我们准备重写核心的 `getInputOnly()` 方法。
7. 我们将 `id` 属性保存到一个独立的变量 `$baseId` 中，稍后将其与 `$count` 结合，使得每个 `id` 属性都是唯一的。如果与选定键相关联的选项已定义，它被赋值为值；否则，我们使用默认值：
```php
public function getInputOnly()
{
    $count = 1;
    $baseId = $this->attributes['id'];
```




8. 在 `foreach()` 循环中，我们检查该键是否是被选中的键。如果是，则为该单选按钮添加 `$checked` 属性。然后，我们调用父类的 `getInputOnly()` 方法以返回每个按钮的 HTML。请注意，`input` 元素的 `value` 属性是 `options` 数组的键。按钮的标签是 `options` 数组元素的值：

```php
foreach ($this->options as $key => $value) {
    $this->attributes['id'] = $baseId . $count++;
    $this->attributes['value'] = $key;
    if ($key == $this->selectedKey) {
        $this->attributes['checked'] = '';
    } elseif (isset($this->attributes['checked'])) {
        unset($this->attributes['checked']);
    }

    if ($this->after) {
        $html = parent::getInputOnly() . $value;
    } else {
        $html = $value . parent::getInputOnly();
    }
    $output .= $this->spacer . $html;
}
return $output;
```

## 工作原理...

将上述代码复制到 `Application/Form/Element` 文件夹中的新 `Radio.php` 文件中。然后，你可以定义一个 `chap_06_form_element_radio.php` 调用脚本，该脚本设置自动加载并锚定新类：

```php
<?php
require __DIR__ . '/../Application/Autoload/Loader.php';
Application\Autoload\Loader::init(__DIR__ . '/../..');
use Application\Form\Generic;
use Application\Form\Element\Radio;
```

接下来，使用前一个食谱中定义的 `$wrappers` 数组来定义包装器。

然后，你可以定义一个 `$status` 数组，并通过向构造函数传递参数来创建元素实例：

```php
$statusList = [
    'U' => 'Unconfirmed',
    'P' => 'Pending',
    'T' => 'Temporary Approval',
    'A' => 'Approved'
];

$status = new Radio('status',
    Generic::TYPE_RADIO,
    'Status',
    $wrappers,
    ['id' => 'status']);
```

现在，你可以检查 `$_GET` 中是否有状态输入并设置选项。任何输入都将成为选中的键。否则，选中的键默认为：

```php
$checked = $_GET['status'] ?? 'U';
$status->setOptions($statusList, $checked, '<br>', TRUE);
```

最后，别忘了定义一个提交按钮：

```php
$submit = new Generic('submit',
    Generic::TYPE_SUBMIT,
    'Process',
    $wrappers,
    ['id' => 'submit','title' =>
    'Click to process','value' => 'Click Here']);
```

显示逻辑可能如下所示：

```html
<form name="status" method="get">
<table id="status" class="display" cellspacing="0" width="100%">
<tr><?= $status->render(); ?></tr>
<tr><?= $submit->render(); ?></tr>
<tr>
<td colspan=2>
<br>
<pre><?php var_dump($_GET); ?></pre>
</td>
</tr>
</table>
</form>
```

这是实际的输出结果：

![](img/39390f6d56c5a83b28db083a8bd5185c_207_0.png)

## 更多信息...

复选框元素生成器将与 HTML 单选按钮生成器几乎相同。主要区别在于，一组复选框可以勾选多个值。相应地，你会对元素名称使用 PHP 数组表示法。元素类型应为 `Generic::TYPE_CHECKBOX`。

## 创建一个 HTML 下拉选择（select）元素生成器

生成 HTML 单个 select 元素的过程与生成单选按钮的过程类似。然而，标签的结构不同，因为需要同时生成一个 **SELECT** 标签和一系列 **OPTION** 标签。

### 如何做...

- 首先，创建一个新的 `Application\Form\Element\Select` 类，该类继承自 `Application\Form\Generic`。
- 我们继承 `Generic` 而不是 `Radio` 的原因在于元素的结构完全不同：

```php
namespace Application\Form\Element;

use Application\Form\Generic;

class Select extends Generic
{
    // code
}
```

- 类常量和属性只需要在 `Application\Form\Generic` 的基础上做少量增加。与单选按钮或复选框不同，无需考虑分隔符或选中文本的放置位置：
  - `const DEFAULT_OPTION_KEY = 0;`
  - `const DEFAULT_OPTION_VALUE = 'Choose';`
  - `protected $options;`
  - `protected $selectedKey = DEFAULT_OPTION_KEY;`

- 现在我们将注意力转向设置选项。由于 HTML `select` 元素可以选择单个值或多个值，因此 `$selectedKey` 属性可以是字符串，也可以是数组。相应地，我们不为该属性添加 **类型提示**。然而，识别是否设置了 `multiple` 属性很重要。这可以通过继承自父类的 `$this->attributes` 属性获得。

- 如果设置了 `multiple` 属性，那么将 `name` 属性制定为数组很重要。相应地，如果是这种情况，我们将在名称后追加 `[]`：

```php
public function setOptions(array $options, $selectedKey =
                   self::DEFAULT_OPTION_KEY)
{
    $this->options = $options;
    $this->selectedKey = $selectedKey;
    if (isset($this->attributes['multiple'])) {
        $this->name .= '[]';
    }
}
```

> 在 PHP 中，如果设置了 HTML select 的 multiple 属性，且 name 属性未指定为数组，则只会返回单个值！

- 在我们定义核心的 `getInputOnly()` 方法之前，我们需要先定义一个方法来生成 `select` 标签。然后，我们使用 `sprintf()` 返回最终的 HTML，其中使用 `$pattern`、`$name` 和 `getAttrs()` 的返回值作为参数。

- 我们将 `$pattern` 的默认值替换为 `<select name="$s" %s>`。然后，我们循环遍历属性，将它们添加为键值对，中间用空格分隔：

```php
protected function getSelect()
{
    $this->pattern = '<select name="$s" %s> ' . PHP_EOL;
    return sprintf($this->pattern, $this->name,
                    $this->getAttrs());
}
```

- 接下来，我们定义一个方法来获取将与 `select` 标签关联的 `option` 标签。

- 如你所记得，`$this->options` 数组中的 *键* 代表返回值，而数组的 *值* 部分代表屏幕上显示的文本。如果 `$this->selectedKey` 是数组形式，我们检查该 *值* 是否在该数组中。否则，我们假设 `$this->selectedKey` 是字符串，我们只需确定它是否等于键。如果选中的键匹配，我们添加 *selected* 属性：

```php
protected function getOptions()
{
    $output = '';
    foreach ($this->options as $key => $value) {
        if (is_array($this->selectedKey)) {
            $selected = (in_array($key, $this->selectedKey))
                        ? ' selected' : '';
        } else {
            $selected = ($key == $this->selectedKey)
                        ? ' selected' : '';
        }
        $output .= '<option value="' . $key . '"
                   . $selected
                   . '>'
                   . $value
                   . '</option>';
    }
    return $output;
}
```

- 最后，我们准备重写核心的 `getInputOnly()` 方法。

- 你会发现，该方法的逻辑只需要捕获前面代码中描述的 `getSelect()` 和 `getOptions()` 方法的返回值。我们还需要添加闭合的 `</select>` 标签：

```php
public function getInputOnly()
{
    $output = $this->getSelect();
    $output .= $this->getOptions();
	$output .= '</' . $this->getType() . '>';
	return $output;
}
```

## 工作原理...

将上述代码复制到 `Application/Form/Element` 文件夹中的新 `Select.php` 文件中。然后定义一个 `chap_06_form_element_select.php` 调用脚本，该脚本设置自动加载并锚定新类：

```php
<?php
	require __DIR__ . '/../Application/Autoload/Loader.php';
	Application\Autoload\Loader::init(__DIR__ . '/../..');
	use Application\Form\Generic;
	use Application\Form\Element\Select;
```

接下来，使用第一个食谱中定义的数组 `$wrappers` 来定义包装器。你还可以使用在 *创建 HTML 单选元素生成器* 食谱中定义的 `$statusList` 数组。然后你可以创建 SELECT 元素的实例。第一个实例是单选，第二个是多选：

```php
$status1 = new Select('status1',
		Generic::TYPE_SELECT,
		'Status 1',
		$wrappers,
		['id' => 'status1']);
$status2 = new Select('status2',
		Generic::TYPE_SELECT,
		'Status 2',
		$wrappers,
		['id' => 'status2',
		'multiple' => '',
		'size' => '4']);
```

检查 `$_GET` 中是否有状态输入并设置选项。任何输入都将成为选中的键。否则，选中的键默认为。如你所记得，第二个实例是多选，因此从 `$_GET` 获取的值和默认设置都应该是数组形式：

```php
$checked1 = $_GET['status1'] ?? ['U'];
$checked2 = $_GET['status2'] ?? ['U'];
$status1->setOptions($statusList, $checked1);
$status2->setOptions($statusList, $checked2);
```

最后，务必定义一个提交按钮（如本章 *创建通用表单元素生成器* 食谱所示）。




实际的显示逻辑与单选按钮配方完全相同，只是我们需要渲染两个独立的 HTML select 实例：

```
<form name="status" method="get">  
<table id="status" class="display" cellpadding="0" width="100%">  
<tr><?= $status1->render(); ?>\</tr>  
<tr><?= $status2->render(); ?>\</tr>  
<tr><?= $submit->render(); ?>\</tr>  
<tr>  
<td colspan=2>  
<br>  
<pre>  
<?php var_dump($_GET); ?>  
</pre>  
</td>  
</tr>  
</table>  
</form>
```

以下是实际输出：

![](img/39390f6d56c5a83b28db083a8bd5185c_211_0.png)

此外，你还可以看到这些元素在查看源代码页面中的显示方式：

![](img/39390f6d56c5a83b28db083a8bd5185c_212_0.png)

## 实现表单工厂

表单工厂的目的是从单个配置数组生成一个可用的表单对象。该表单对象应具备获取其所包含的各个元素的能力，从而能够生成输出。

### 如何操作...

- 1. 首先，让我们创建一个名为 `Application\Form\Factory` 的类来容纳工厂代码。它将只包含一个属性 `$elements`，以及一个获取方法：

```
namespace Application\Form;

class Factory
{
    protected $elements;
    public function getElements()
    {
        return $this->elements;
    }
    // remaining code
}
```

- 2. 在定义主要的表单生成方法之前，重要的是考虑我们计划接收的配置格式，以及表单生成具体将产生什么。为了说明这一点，我们假设生成将产生一个 `Factory` 实例，并带有一个 `$elements` 属性。该属性将是 `Application\Form\Generic` 或 `Application\Form\Element` 类的数组。

- 3. 现在我们准备处理 `generate()` 方法。它将遍历配置数组，创建适当的 `Application\Form\Generic` 或 `Application\Form\Element\*` 对象，这些对象随后将被存储在 `$elements` 数组中。新方法将接受配置数组作为参数。将该方法定义为静态方法是方便的，这样我们可以使用不同的配置块生成所需的尽可能多的实例。

- 4. 我们创建 `Application\Form\Factory` 的一个实例，然后开始遍历配置数组：

```
public static function generate(array $config)
{
    $form = new self();
    foreach ($config as $key => $p) {
```

- 5. 接下来，我们检查 `Application\Form\Generic` 类构造函数中可选的参数：

```
$p['errors'] = $p['errors'] ?? array();
$p['wrappers'] = $p['wrappers'] ?? array();
$p['attributes'] = $p['attributes'] ?? array();
```

- 6. 现在所有构造函数参数都已就位，我们可以创建表单元素实例，然后将其存储在 `$elements` 中：

```
$form->elements[$key] = new $p['class']
(
    $key,
    $p['type'],
    $p['label'],
    $p['wrappers'],
    $p['attributes'],
    $p['errors']
);
```

- 7. 接下来，我们将注意力转向选项。如果设置了 options 参数，我们使用 `list()` 将数组值提取到变量中。然后我们使用 `switch()` 测试元素类型，并以适当数量的参数运行 `setOptions()`：

```
if (isset($p['options'])) {
    list($a,$b,$c,$d) = $p['options'];
    switch ($p['type']) {
        case Generic::TYPE_RADIO    :
```

```
$form->elements[$key]->setOptions($a,$b,$c,$d);
break;
case Generic::TYPE_SELECT    :
$form->elements[$key]->setOptions($a,$b);
break;
default    :
$form->elements[$key]->setOptions($a,$b);
break;
}
}
```

- 8. 最后，我们返回表单对象并关闭方法：

```
return $form;
}
```

- 9. 理论上，此时我们可以很容易地在视图逻辑中渲染表单，只需遍历元素数组并运行 `render()` 方法即可。视图逻辑可能如下所示：

```
<form name="status" method="get">
<table id="status" class="display" cellspacing="0" width="100%">
<?php foreach ($form->getElements() as $element) : ?>
<?php echo $element->render(); ?>
<?php endforeach; ?>
</table>
</form>
```

- 10. 最后，我们返回表单对象并关闭方法。

- 11. 接下来，我们需要在 `Application\Form\Element` 下定义一个独立的 `Form` 类：

```
namespace Application\Form\Element;
class Form extends Generic
{
    public function getInputOnly()
    {
        $this->pattern = '<form name="$s" $s> ' . PHP_EOL;
        return sprintf($this->pattern, $this->name,
                       $this->getAttribs());
    }
    public function closeTag()
    {
        return '</' . $this->type . '>';
    }
}
```

- 12. 回到 `Application\Form\Factory` 类，我们现在需要定义一个简单的 `sprintf()` 包装模式返回方法，该模式将作为输入的封装。作为一个例子，如果包装器是带有属性 `class="test"` 的 `div`，我们将产生此模式：`<div class="test">%s</div>`。然后我们的内容将通过 `sprintf()` 函数替换 `%s` 的位置：

```
protected function getWrapperPattern($wrapper)
{
    $type = $wrapper['type'];
    unset($wrapper['type']);
    $pattern = '<' . $type;
    foreach ($wrapper as $key => $value) {
        $pattern .= ' ' . $key . '="' . $value . '"';
    }
    $pattern .= '>%s</' . $type . '>';
    return $pattern;
}
```

- 13. 最后，我们准备定义一个执行整体表单渲染的方法。我们为每个表单行获取 wrapper 的 `sprintf()` 模式。然后我们遍历元素，渲染每一个，并将输出包装在行模式中。接下来，我们生成一个 `Application\Form\Element\Form` 实例。然后我们获取表单 wrapper 的 `sprintf()` 模式，并检查 `form_tag_inside_wrapper` 标志，该标志告诉我们是否需要在表单 wrapper 内部或外部放置表单标签。

```
public static function render($form, $formConfig)
{
    $rowPattern = $form->getWrapperPattern(
        $formConfig['row_wrapper']);
    $contents = '';
    foreach ($form->getElements() as $element) {
        $contents .= sprintf($rowPattern, $element->render());
    }

    $formTag = new Form($formConfig['name'],
                        Generic::TYPE_FORM,
                        '',
                        array(),
                        $formConfig['attributes']);

    $formPattern = $form->getWrapperPattern(
        $formConfig['form_wrapper']);
    if (isset($formConfig['form_tag_inside_wrapper'])
        && !$formConfig['form_tag_inside_wrapper']) {
        $formPattern = '%s' . $formPattern . '%s';
        return sprintf($formPattern, $formTag->getInputOnly(),
                       $contents, $formTag->closeTag());
    } else {
        return sprintf($formPattern, $formTag->getInputOnly())
            . $contents . $formTag->closeTag();
    }
}
```

### 它是如何工作的...

参考前面的代码，创建 `Application\Form\Factory` 和 `Application\Form\Element\Form` 类。

接下来，你可以定义一个 `chap_06_form_factory.php` 调用脚本，该脚本设置自动加载并锚定新类：

```
<?php
require __DIR__ . '/../../Application/Autoload/Loader.php';
Application\Autoload\Loader::init(__DIR__ . '/../../');
use Application\Form\Generic;
use Application\Form\Factory;
```

接下来，使用第一个配方中定义的 `$wrappers` 数组定义 wrapper。你也可以使用第二个配方中定义的 `$statusList` 数组。

检查是否有任何来自 `$_POST` 的状态输入。任何输入都将成为选中的键。否则，选中的键是默认值。

```
$email    = $_POST['email']      ?? '';
$checked0 = $_POST['status0']     ?? 'U';
$checked1 = $_POST['status1']     ?? 'U';
$checked2 = $_POST['status2']     ?? ['U'];
$checked3 = $_POST['status3']     ?? ['U'];
```

现在你可以定义整体表单配置。名称和 attributes 参数用于配置 `form` 标签本身。另外两个参数代表表单级别和行级别的 wrapper。最后，我们提供一个 `form_tag_inside_wrapper` 标志，指示表单标签不应出现在 wrapper 内部（即 `<table>`）。如果 wrapper 是 `<div>`，我们会将此标志设置为 TRUE：

```
$formConfig = [
    'name'       => 'status_form',
    'attributes' => ['id'=>'statusForm', 'method'=>'post',
                     'action'=>'chap_06_form_factory.php'],
    'row_wrapper' => [ 'type' => 'tr', 'class' => 'row'],
    'form_wrapper' => ['type'=>'table', 'class'=>'table',
                       'id'=>'statusTable',
```





接下来，定义一个数组，用于保存将由工厂创建的每个表单元素的参数。数组的键将成为表单元素的名称，并且必须唯一：

```php
$config = [
'email' => [
'class' => 'Application\Form\Generic',
'type' => Generic::TYPE_EMAIL,
'label' => 'Email',
'wrappers' => $wrappers,
'attributes'=> ['id'=>'email', 'maxLength'=>128,
'title'=>'Enter address',
'required'=>'', 'value'=>strip_tags($email)]
],
'password' => [
'class' => 'Application\Form\Generic',
'type' => Generic::TYPE_PASSWORD,
'label' => 'Password',
'wrappers' => $wrappers,
'attributes'=> ['id'=>'password',
'title' => 'Enter your password',
'required' => '']
],
// etc.
];
```

最后，确保生成表单：

```php
$form = Factory::generate($config);
```

实际的显示逻辑非常简单，我们只需调用表单级别的 `render()` 方法即可：

```php
<?php echo $form->render($form, $formConfig); ?>
```

这是实际的输出：

![](img/39390f6d56c5a83b28db083a8bd5185c_218_0.png)

## 链式处理 $_POST 过滤器

在处理用户通过在线表单提交的数据时，正确的过滤和验证是一个常见问题。可以说，这也是网站首要的安全漏洞。此外，如果过滤器和验证器分散在应用程序的各个角落，也会非常繁琐。一种链式机制可以很好地解决这些问题，同时还能让你控制过滤器和验证器的处理顺序。

### 操作方法

-   1. 有一个鲜为人知的 PHP 函数 `filter_input_array()`，乍看之下似乎非常适合这项任务。然而，深入探究其功能后，很快就会发现，该函数是在早期设计的，无法满足现代对攻击防护和灵活性的要求。因此，我们将转而介绍一种基于回调数组的、更具灵活性的机制来执行过滤和验证。

![](img/39390f6d56c5a83b28db083a8bd5185c_219_0.png)

*过滤* 与 *验证* 的区别在于，过滤可能会删除或转换值。而验证则使用适合数据特性的标准来测试数据，并返回布尔结果。

-   2. 为了增加灵活性，我们将使我们的基础过滤类和验证类保持相对轻量。这意味着我们*不*定义任何具体的过滤器或验证方法。相反，我们将完全基于回调配置数组进行操作。为了确保过滤和验证结果的兼容性，我们还将定义一个特定的结果对象 `Application\Filter\Result`。

-   3. `Result` 类的主要功能是保持一个 `$item` 值，该值可以是过滤后的值或验证的布尔结果。另一个属性 `$messages` 将保存一个消息数组，这些消息是在过滤或验证操作*期间*填充的。在构造函数中，为 `$messages` 提供的值被格式化为数组。你可能会注意到这两个属性都被定义为 `public`。这是为了方便访问：

```php
namespace Application\Filter;

class Result
{
    public $item;  // (mixed) filtered data | (bool) result of validation
    public $messages = array(); // [(string) message, (string) message ]

    public function __construct($item, $messages)
    {
        $this->item = $item;
        if (is_array($messages)) {
            $this->messages = $messages;
        } else {
            $this->messages = [$messages];
        }
    }
}
```

-   4. 我们还定义了一个方法，允许将此 `Result` 实例与另一个实例合并。这很重要，因为在某个阶段，我们将通过过滤器链处理同一个值。在这种情况下，我们希望新过滤的值覆盖现有值，但希望消息进行合并：

```php
public function mergeResults(Result $result)
{
    $this->item = $result->item;
    $this->mergeMessages($result);
}

public function mergeMessages(Result $result)
{
    if (isset($result->messages) && is_array($result->messages)) {
        $this->messages = array_merge($this->messages, $result->messages);
    }
}
```

-   5. 最后，为了完成该类的其他方法，我们添加了一个用于合并验证结果的方法。这里的关键考量是，验证链中上下任何位置的 `FALSE` 值都必须导致整个结果为 `FALSE`：

```php
public function mergeValidationResults(Result $result)
{
    if ($this->item === TRUE) {
        $this->item = (bool) $result->item;
    }
    $this->mergeMessages($result);
}
```

-   6. 接下来，为了确保回调产生兼容的结果，我们将定义 `Application\Filter\CallbackInterface` 接口。请注意，我们利用 PHP 7 的数据类型特性来指定返回值的类型，以确保我们得到的是一个 `Result` 实例：

```php
namespace Application\Filter;

interface CallbackInterface
{
    public function __invoke ($item, $params) : Result;
}
```

-   7. 每个回调都应引用同一组消息。因此，我们定义了一个 `Application\Filter\Messages` 类，其中包含一系列静态属性。我们提供了方法来设置所有消息或单条消息。`$messages` 属性被设为 public 以便于访问：

```php
namespace Application\Filter;

class Messages
{
    const MESSAGE_UNKNOWN = 'Unknown';
    public static $messages;

    public static function setMessages(array $messages)
    {
        self::$messages = $messages;
    }

    public static function setMessage($key, $message)
    {
        self::$messages[$key] = $message;
    }

    public static function getMessage($key)
    {
        return self::$messages[$key] ?? self::MESSAGE_UNKNOWN;
    }
}
```

-   8. 现在，我们可以定义 `Application\Web\AbstractFilter` 类来实现核心功能。如前所述，该类将保持相对*轻量*，我们无需担心具体的过滤器或验证器，因为它们将通过配置提供。我们使用 PHP 7 **标准 PHP 库 (SPL)** 中提供的 `UnexpectedValueException` 类，以便在某个回调未实现 `CallbackInterface` 时抛出描述性异常：

```php
namespace Application\Filter;
use UnexpectedValueException;

abstract class AbstractFilter
{
    // code described in the next several bullets
}
```

-   9. 首先，我们定义一些有用的类常量，用于保存各种*维护*值。此处显示的最后四个常量控制要显示的消息格式，以及如何描述*缺失*数据：

```php
const BAD_CALLBACK = 'Must implement CallbackInterface';
const DEFAULT_SEPARATOR = '<br>' . PHP_EOL;
const MISSING_MESSAGE_KEY = 'item.missing';
const DEFAULT_MESSAGE_FORMAT = '%20s : %60s';
const DEFAULT_MISSING_MESSAGE = 'Item Missing';
```

-   10. 接下来，我们定义核心属性。`$separator` 与过滤和验证消息配合使用。`$callbacks` 表示执行过滤和验证的回调数组。`$assignments` 将数据字段映射到过滤器和/或验证器。`$missingMessage` 作为一个属性表示，以便可以被覆盖（即用于多语言网站）。最后，`$results` 是一个 `Application\Filter\Result` 对象的数组，由过滤或验证操作填充：

```php
protected $separator;    // used for message display
protected $callbacks;
protected $assignments;
protected $missingMessage;
protected $results = array();
```

-   11. 此时，我们可以构建 `__construct()` 方法。其主要功能是设置回调和赋值数组。它还设置值或接受分隔符（用于消息显示）和缺失消息的默认值：

```php
public function __construct(array $callbacks, array $assignments, $separator = NULL, $message = NULL)
{
    $this->setCallbacks($callbacks);
    $this->setAssignments($assignments);
    $this->setSeparator($separator ?? self::DEFAULT_SEPARATOR);
    $this->setMissingMessage($message ?? self::DEFAULT_MISSING_MESSAGE);
}
```

-   12. 接下来，我们定义一系列允许我们设置或移除回调的方法。请注意，我们允许获取和设置单个回调。如果你有一组通用的回调，并且只需修改其中一个，这将非常有用。你还会注意到 `setOneCall()` 会检查回调是否实现了 `CallbackInterface`。如果没有，则抛出 `UnexpectedValueException`：

```php
public function getCallbacks()
{
    return $this->callbacks;
}

public function getOneCallback($key)
{
    return $this->callbacks[$key] ?? NULL;
}

public function setCallbacks(array $callbacks)
{
    foreach ($callbacks as $key => $item) {
        $this->setOneCallback($key, $item);
    }
}

public function setOneCallback($key, $item)
{
    if ($item instanceof CallbackInterface) {
        $this->callbacks[$key] = $item;
    } else {
        throw new UnexpectedValueException(self::BAD_CALLBACK);
    }
}
```





13. 处理结果的方法相当简单。为了方便，我们添加了 `getItemsAsArray()`，否则 `getResults()` 将返回一个 Result 对象数组：

```php
public function getResults()
{
    return $this->results;
}

public function getItemsAsArray()
{
    $return = array();
    if ($this->results) {
        foreach ($this->results as $key => $item)
            $return[$key] = $item->item;
    }
    return $return;
}
```

14. 获取消息只需遍历 `$this->results` 数组并提取 `$messages` 属性即可。为了方便，我们还添加了带有格式选项的 `getMessageString()`。为了轻松生成消息数组，我们使用了 PHP 7 的 `yield from` 语法。这使 `getMessages()` 变成了一个委托生成器。消息数组变成了子生成器：

```php
public function getMessages()
{
    if ($this->results) {
        foreach ($this->results as $key => $item)
            if ($item->messages) yield from $item->messages;
    } else {
        return array();
    }
}

public function getMessageString($width = 80, $format = NULL)
{
    if (!$format)
        $format = self::DEFAULT_MESSAGE_FORMAT . $this->separator;
    $output = '';
    if ($this->results) {
        foreach ($this->results as $key => $value) {
            if ($value->messages) {
                foreach ($value->messages as $message) {
                    $output .= sprintf(
                        $format, $key, trim($message));
                }
            }
        }
    }
    return $output;
}
```

15. 最后，我们定义了一组有用的混合 getter 和 setter：

```php
public function setMissingMessage($message)
{
    $this->missingMessage = $message;
}

public function setSeparator($separator)
{
    $this->separator = $separator;
}

public function getSeparator()
{
    return $this->separator;
}

public function getAssignments()
{
    return $this->assignments;
}

public function setAssignments(array $assignments)
{
    $this->assignments = $assignments;
}
// AbstractFilter 类的结束大括号
}
```

16. 虽然过滤和验证通常一起执行，但同样经常是分开执行的。因此，我们为每种定义独立的类。我们将从 `Application\Filter\Filter` 开始。我们让这个类继承 `AbstractFilter`，以提供之前描述的核心功能：

```php
namespace Application\Filter;

class Filter extends AbstractFilter
{
    // code
}
```

17. 在这个类中，我们定义了一个核心的 `process()` 方法，它扫描数据数组并根据分配数组应用过滤器。如果此数据集没有分配的过滤器，我们简单地返回 `NULL`：

```php
public function process(array $data)
{
    if (!isset($this->assignments) || !count($this->assignments)) {
        return NULL;
    }
```

18. 否则，我们将 `$this->results` 初始化为一个 Result 对象数组，其中 `$item` 属性是 `$data` 中的原始值，而 `$messages` 属性是一个空数组：

```php
    foreach ($data as $key => $value) {
        $this->results[$key] = new Result($value, array());
    }
```

19. 然后，我们创建 `$this->assignments` 的副本，并检查是否存在全局过滤器（由 '*' 键标识）。如果是，我们运行 `processGlobal()`，然后 unset  '*' 键：

```php
    $toDo = $this->assignments;
    if (isset($toDo['*'])) {
        $this->processGlobalAssignment($toDo['*'], $data);
        unset($toDo['*']);
    }
```

20. 最后，我们遍历剩余的分配，调用 `processAssignment()`：

```php
    foreach ($toDo as $key => $assignment) {
        $this->processAssignment($assignment, $key);
    }
}
```

21. 如前所述，每个分配都对应于数据字段，并且表示该字段的回调数组。因此，在 `processGlobalAssignment()` 中，我们需要遍历回调数组。但是在这种情况下，由于这些分配是全局的，我们还必须遍历整个数据集，并依次应用每个全局过滤器：

```php
protected function processGlobalAssignment($assignment, $data)
{
    foreach ($assignment as $callback) {
        if ($callback === NULL) continue;
        foreach ($data as $k => $v) {
            $result = $this->callbacks[$callback['key']](
                $this->results[$k]->item,
                $callback['params']
            );
            $this->results[$k]->mergeResults($result);
        }
    }
}
```

> 棘手之处在于这行代码：`$result = $this->callbacks[$callback['key']]($this->results[$k]->item, $callback['params']);` 记住，每个回调实际上是一个定义了 PHP 魔法方法 `__invoke()` 的匿名类。提供的参数是要过滤的实际数据项和参数数组。通过运行 `$this->callbacks[$callback['key']]()`，我们实际上是在神奇地调用 `__invoke()`。

22. 当我们定义 `processAssignment()` 时，类似于 `processGlobalAssignment()` 的方式，我们需要执行分配给每个数据键的每个剩余回调：

```php
protected function processAssignment($assignment, $key)
{
    foreach ($assignment as $callback) {
        if ($callback === NULL) continue;
        $result = $this->callbacks[$callback['key']](
            $this->results[$key]->item,
            $callback['params']
        );
        $this->results[$key]->mergeResults($result);
    }
}
// Application\Filter\Filter 的结束大括号
}
```

> 重要的是，任何修改原始用户提供的数据的过滤操作都应显示一条消息，表明已做出更改。这可以成为审计跟踪的一部分，以保护你免受在用户不知情或不同意的情况下做出更改时可能产生的法律责任。

## 工作原理...

创建一个 `Application\Filter` 文件夹。在此文件夹中，使用前面步骤中的代码创建以下类文件：

| Application\Filter\* 类文件 | 这些步骤中描述的代码 |
| :--- | :--- |
| Result.php | 3-5 |
| CallbackInterface.php | 6 |
| Messages.php | 7 |
| AbstractFilter.php | 8-15 |
| Filter.php | 16-22 |

接下来，获取第 5 步中讨论的代码，并使用它在 `chap_06_post_data_config_messages.php` 文件中配置消息数组。每个回调引用 `Messages::$messages` 属性。这里是一个示例配置：

```php
<?php
use Application\Filter\Messages;
Messages::setMessages(
    [
        'length_too_short' => 'Length must be at least %d',
        'length_too_long' => 'Length must be no more than %d',
        'required' => 'Please be sure to enter a value',
        'alnum' => 'Only letters and numbers allowed',
        'float' => 'Only numbers or decimal point',
        'email' => 'Invalid email address',
        'in_array' => 'Not found in the list',
        'trim' => 'Item was trimmed',
        'strip_tags' => 'Tags were removed from this item',
        'filter_float' => 'Converted to a decimal number',
        'phone' => 'Phone number is (%n) nnn-nnn-nnnn',
        'test' => 'TEST',
        'filter_length' => 'Reduced to specified length',
    ]
);
```

接下来，创建一个 `chap_06_post_data_config_callbacks.php` 回调配置文件，其中包含过滤回调的配置，如第 4 步所述。每个回调应遵循此通用模板：

```php
'callback_key' => new class () implements CallbackInterface
{
    public function __invoke($item, $params) : Result
    {
        $Changed = array();
        $filtered = /* perform filtering operation on $item */;
        if ($filtered !== $item)
            $Changed[] = Messages::$messages['callback_key'];
        return new Result($filtered, $Changed);
    }
}
```

回调本身必须实现该接口并返回 `Result` 实例。我们可以利用 PHP 7 的**匿名类**功能，让回调返回一个实现 `CallbackInterface` 的匿名类。以下是过滤回调数组的可能样子：

```php
use Application\Filter\{ Result, Messages, CallbackInterface };
$config = ['filters' => [
    'trim' => new class () implements CallbackInterface
    {
        public function __invoke($item, $params) : Result
        {
            $Changed = array();
            $filtered = trim($item);
            if ($filtered !== $item)
                $Changed[] = Messages::$messages['trim'];
            return new Result($filtered, $Changed);
        }
    },
    'strip_tags' => new class () implements CallbackInterface
    {
        public function __invoke($item, $params) : Result
        {
            $Changed = array();
            $filtered = strip_tags($item);
            if ($filtered !== $item)
                $Changed[] = Messages::$messages['strip_tags'];
            return new Result($filtered, $Changed);
        }
    },
    // etc.
]
];
```





出于测试目的，我们将使用潜在客户表作为目标。不再从 `$_POST` 提供数据，而是构造一个包含**良好**数据和*不良*数据的数组：

|  | **字段名** | **类型** | **允许为空？** |
| :--- | :--- | :--- | :--- |
| ☐ | id | int(11) | 否 |
| ☐ | first_name | varchar(128) | 否 |
| ☐ | last_name | varchar(128) | 否 |
| ☐ | address | varchar(256) | 是 |
| ☐ | city | varchar(64) | 是 |
| ☐ | state_province | varchar(32) | 是 |
| ☐ | postal_code | char(16) | 否 |
| ☐ | phone | varchar(16) | 否 |
| ☐ | country | char(2) | 否 |
| ☐ | email | varchar(250) | 否 |
| ☐ | status | char(8) | 是 |
| ☐ | budget | decimal(10,2) | 是 |
| ☐ | last_updated | datetime | 是 |

现在，你可以创建一个 `chap_06_post_data_filtering.php` 脚本，该脚本设置自动加载，并包含消息和回调配置文件：

```php
<?php
require __DIR__ . '/../Application/Autoload/Loader.php';
Application\Autoload\Loader::init(__DIR__ . '/..');
include __DIR__ . '/chap_06_post_data_config_messages.php';
include __DIR__ . '/chap_06_post_data_config_callbacks.php';
```

接着，你需要定义*分配项*，它表示数据字段与过滤回调之间的映射。使用 `*` 键来定义应用于所有数据的**全局过滤器**：

```php
$assignments = [
    '*'       => [ ['key' => 'trim', 'params' => []],
                   ['key' => 'strip_tags', 'params' => [] ]],
    'first_name' => [ ['key' => 'length',
                      'params' => ['length' => 128]] ],
    'last_name'  => [ ['key' => 'length',
                      'params' => ['length' => 128]] ],
    'city'       => [ ['key' => 'length',
                      'params' => ['length' => 64]] ],
    'budget'     => [ ['key' => 'filter_float', 'params' => []] ],
];
```

接下来，定义良好的测试数据和不良的测试数据：

```php
$goodData = [
	'first_name'		=> 'Your Full',
	'last_name'			=> 'Name',
	'address'			=> '123 Main Street',
	'city'				=> 'San Francisco',
	'state_province'	=> 'California',
	'postal_code'		=> '94101',
	'phone'				=> '+1 415-555-1212',
	'country'			=> 'US',
	'email'				=> 'your@email.address.com',
	'budget'			=> '123.45',
];
$badData = [
	'first_name'		=> 'This+Name<script>bad tag</script>Valid!',
	'last_name'		=> 'ThisLastNameIsWayTooLong
	Abcdefghijklmnopqrstuvwxyz0123456789
	Abcdefghijklmnopqrstuvwxyz0123456789
	Abcdefghijklmnopqrstuvwxyz0123456789
	Abcdefghijklmnopqrstuvwxyz0123456789',
	// 'address'		=> '',		// 缺失
	'city'			=> '
	ThisCityNameIsTooLong0123456789012345678901234
	56789012345678901234567890123456789	',
	// 'state_province'=> '',		// 缺失
	'postal_code'		=> '!"#£$%^&*Non Alpha Chars',
	'phone'			=> ' 12345 ',
	'country'			=> 'XX',
	'email'			=> 'this.is.not@an.email',
	'budget'			=> 'XXX',
];
```

最后，你可以创建一个 `Application\Filter\Filter` 实例，并测试这些数据：

```php
$filter = new Application\Filter\Filter(
	$config['filters'], $assignments);
$filter->setSeparator(PHP_EOL);
$filter->process($goodData);
echo $filter->getMessageString();
var_dump($filter->getItemsAsArray());

$filter->process($badData);
echo $filter->getMessageString();
var_dump($filter->getItemsAsArray());
```

处理良好数据时，除了有一条消息指出浮点字段的值已从字符串转换为浮点数外，不会生成其他消息。另一方面，处理不良数据时，会产生以下输出：

![](img/39390f6d56c5a83b28db083a8bd5185c_231_0.png)

你还会注意到，first_name 中的标签已被移除，且 last_name 和 city 均被截断。

## 更多相关内容…

filter_input_array() 函数接受两个参数：输入源（形式为用于指示 PHP 超全局变量之一的预定义常量，即 $_POST）以及一个以匹配的字段定义作为键、以过滤器或验证器作为值的数组。该函数不仅执行过滤操作，还执行验证操作。标记为 sanitize 的标志实际上是过滤器。

## 参见

filter_input_array() 的文档和示例可在 http://php.net/manual/en/function.filter-input-array.php 找到。你可能还会想查看 http://php.net/manual/en/filter.filters.php 上可用的不同类型的过滤器。

## 链接 $_POST 验证器

本食谱中的*主要工作*已在上一食谱中完成。核心功能由 `Application\Filter\AbstractFilter` 定义。实际验证是由一系列验证回调数组执行的。

### 执行方法...

1.  回顾上一食谱，*链接 $_POST 过滤器*。我们将使用此食谱中的所有类和配置文件，除非在此处另有说明。
2.  首先，我们定义一个验证回调的配置数组。与上一食谱一样，每个回调都应实现 `Application\Filter\CallbackInterface`，并应返回 `Application\Filter\Result` 的实例。验证器将采用这种通用形式：

```php
use Application\Filter\{ Result, Messages, CallbackInterface };
$config = [
// validator callbacks
'validators' => [
'key' => new class () implements CallbackInterface
{
public function __invoke($item, $params) : Result
{
// validation logic goes here
return new Result($valid, $error);
}
},
// etc.
]
];
```

3.  接下来，我们定义一个 `Application\Filter\Validator` 类，它遍历分配项数组，并使用分配的验证回调测试每个数据项。我们让此类继承 `AbstractFilter`，以便提供前面描述的核心功能：

```php
namespace Application\Filter;
class Validator extends AbstractFilter
{
// code
}
```

4.  在此类中，我们定义一个核心 `process()` 方法，该方法扫描数据数组并根据分配项数组应用验证器。如果此数据集没有分配的验证器，我们只需返回 `$valid` 的当前状态（即 `TRUE`）：

```php
public function process(array $data)
{
    $valid = TRUE;
    if (!isset($this->assignments)
        && count($this->assignments)) {
        return $valid;
    }
```

5.  否则，我们将 `$this->results` 初始化为一个由 `Result` 对象组成的数组，其中 `$item` 属性设置为 `TRUE`，且 `$messages` 属性为一个空数组：

```php
foreach ($data as $key => $value) {
    $this->results[$key] = new Result(TRUE, array());
}
```

6.  然后，我们复制一份 `$this->assignments` 并检查是否存在任何 `global` 过滤器（通过 `'*'` 键标识）。如果有，我们运行 `processGlobal()`，然后取消设置 `'*'` 键：

```php
$todo = $this->assignments;
if (isset($todo['*'])) {
    $this->processGlobalAssignment($todo['*'], $data);
    unset($todo['*']);
}
```

7.  最后，我们遍历剩余的分配项，调用 `processAssignment()`。这是检查分配项数组中存在的任何字段是否缺失于数据中的一个理想位置。请注意，如果任何验证回调返回 `FALSE`，我们将 `$valid` 设置为 `FALSE`：

```php
foreach ($todo as $key => $assignment) {
    if (!isset($data[$key])) {
        $this->results[$key] =
            new Result(FALSE, $this->missingMessage);
    } else {
        $this->processAssignment(
            $assignment, $key, $data[$key]);
    }
    if (!$this->results[$key]->item) $valid = FALSE;
}
return $valid;
```

8.  如你所回忆的，每个*分配项*都*键控*到数据字段，并且代表针对该字段的回调数组。因此，在 `processGlobalAssignment()` 中，我们需要遍历回调数组。然而，在这种情况下，因为这些*分配项*是**全局的**，我们还需要遍历**整个**数据集，并依次应用每个全局过滤器。

9.  与相应的 `Application\Filter\Filter::processGlobalAssignment()` 方法相比，我们需要调用 `mergeValidationResults()`。原因是如果 `$result->item` 的值已经是 `FALSE`，我们需要确保它随后不会被 `TRUE` 值覆盖。链中返回 `FALSE` 的任何验证器都必须覆盖其他任何验证结果：

```php
protected function processGlobalAssignment($assignment, $data)
{
    foreach ($assignment as $callback) {
        if ($callback === NULL) continue;
        foreach ($data as $k => $value) {
            $result = $this->callbacks[$callback['key']]
                     ($value, $callback['params']);
            $this->results[$k]->mergeValidationResults($result);
        }
    }
}
```

10. 当我们定义 `processAssignment()` 时，以类似于 `processGlobalAssignment()` 的方式，我们需要执行**每个剩余分配的回调**，针对每个数据键，再次调用 `mergeValidationResults()`： 

```php
protected function processAssignment($assignment, $key, $value)
{
    foreach ($assignment as $callback) {
        if ($callback === NULL) continue;
        $result = $this->callbacks[$callback['key']]
                  ($value, $callback['params']);
        $this->results[$key]->mergeValidationResults($result);
    }
}
```

## 工作原理...

与上一食谱一样，请确保定义以下类：

- `Application\Filter\Result`
- `Application\Filter\CallbackInterface`




-   Application\Filter\Messages
-   Application\Filter\AbstractFilter

你可以使用文件 `chap_06_post_data_config_messages.php`，该文件也在前面的示例中有所描述。

接下来，在 `Application\Filter` 文件夹中创建一个 `Validator.php` 文件。放入步骤 3 到 10 中描述的代码。

然后，创建一个回调配置 `chap_06_post_data_config_callbacks.php`，其中包含步骤 2 中描述的验证回调配置。每个回调都应遵循以下通用模板：

```php
'validation_key' => new class () implements CallbackInterface
{
    public function __invoke($item, $params) : Result
    {
        $error = array();
        $valid = /* perform validation operation on $item */;
        if (!$valid) {
            $error[] = Messages::$messages['validation_key'];
        }
        return new Result($valid, $error);
    }
}
```

现在你可以创建一个 `chap_06_post_data_validation.php` 调用脚本，该脚本用于初始化自动加载并包含配置脚本：

```php
<?php
require __DIR__ . '/../Application/Autoload/Loader.php';
Application\Autoload\Loader::init(__DIR__ . '/../..');
include __DIR__ . '/chap_06_post_data_config_messages.php';
include __DIR__ . '/chap_06_post_data_config_callbacks.php';
```

接下来，定义一个赋值数组，将数据字段映射到验证器回调键：

```php
$assignments = [
    'first_name'      => [ ['key' => 'length',
                           'params' => ['min' => 1, 'max' => 128]],
                           ['key' => 'alnum',
                            'params' => ['allowWhiteSpace' => TRUE]],
    ],
    'last_name'       => [ ['key' => 'required','params' => []] ],
    'params'          => [ 
        ['key' => 'length', 'params' => ['min' => 1, 'max' => 128]],
        ['key' => 'alnum', 'params' => ['allowWhiteSpace' => TRUE]],
        ['key' => 'required', 'params' => []]
    ],
    
    'address'           => [ ['key' => 'length',
                             'params'          => ['max' => 256]] ],
    'city'              => [ ['key' => 'length',
                              'params'          => ['min' => 1, 'max' => 64]] ],
    'state_province'    => [ ['key' => 'length',
                              'params'          => ['min' => 1, 'max' => 32]] ],
    'postal_code'       => [ ['key' => 'length',
                              'params'          => ['min' => 1, 'max' => 16] ],
                             ['key' => 'alnum',
                              'params'          => ['allowWhiteSpace' => TRUE]],
                             ['key' => 'required','params' => []] ],
    'phone'             => [ ['key' => 'phone', 'params' => []] ],
    'country'           => [ ['key' => 'in_array',
                              'params'          => $countries ],
                             ['key' => 'required','params' => []] ],
    'email'             => [ ['key' => 'email', 'params' => [] ],
                             ['key' => 'length',
                              'params'          => ['max' => 250] ],
                             ['key' => 'required','params' => [] ] ],
    'budget'            => [ ['key' => 'float', 'params' => []] ]
];
```

对于测试数据，使用在前一个示例中描述的 `chap_06_post_data_filtering.php` 文件中定义的相同的有效和无效数据。之后，你就可以创建 `Application\Filter\Validator` 实例并测试数据了：

```php
$validator = new Application\Filter\Validator($config['validators'], $assignments);
$validator->setSeparator(PHP_EOL);
$validator->process($badData);
echo $validator->getMessageString(40, ' %14s : %-26s' . PHP_EOL);
var_dump($validator->getItemsAsArray());
$validator->process($goodData);
echo $validator->getMessageString(40, ' %14s : %-26s' . PHP_EOL);
var_dump($validator->getItemsAsArray());
```

正如预期的那样，有效数据不会产生任何验证错误。相反，无效数据会生成以下输出：

```text
Bad Data:
    first_name : Item must contain only letters and numbers
    last_name : Length must be no more than 128
    city : Length must be no more than 64
    postal_code : Length must be no more than 16
    postal_code : Item must contain only letters and numbers
    phone : Phone number must be in a format [n] nn-nnn-nnnn
    country : Item was not found in the list of valid values
    email : Invalid email address
    address : Item Missing
    state_province : Item Missing
array(18) (
    ["first_name"]=>
    bool(false)
    ["last_name"]=>
    bool(false)
    ["city"]=>
    bool(false)
    ["postal_code"]=>
    bool(false)
    ["phone"]=>
    bool(false)
    ["country"]=>
    bool(false)
    ["email"]=>
    bool(false)
    ["budget"]=>
    bool(true)
    ["address"]=>
    bool(false)
    ["state_province"]=>
    bool(false)
)
```

注意，*缺失* 的字段 *address* 和 *state_province* 验证结果为 *FALSE*，并返回缺失项的消息。

## 将验证与表单绑定

当表单首次渲染时，将一个表单类（例如前一个示例中描述的 *Application\Form\Factory*）与一个可以执行过滤或验证的类（例如前一个示例中描述的 *Application\Filter\**）绑定在一起的价值并不大。然而，一旦表单数据提交，这种绑定的重要性就会增加。如果表单数据未能通过验证，值可以被过滤，然后重新显示。验证错误消息可以与表单元素绑定，并渲染在表单字段旁边。

### 如何操作...

1.  首先，确保实现 *Implementing a Form Factory*、*Chaining $_POST Filters* 和 *Chaining $_POST Validators* 示例中定义的类。
2.  现在我们将注意力转向 *Application\Form\Factory* 类，并添加允许我们附加 *Application\Filter\Filter* 和 *Application\Filter\Validator* 实例的属性和 setter。我们还需要定义 `$data`，它将用于保留经过过滤和/或验证的数据：

```php
const DATA_NOT_FOUND = 'Data not found. Run setData()';
const FILTER_NOT_FOUND = 'Filter not found. Run setFilter()';
const VALIDATOR_NOT_FOUND = 'Validator not found. Run setValidator()';

protected $filter;
protected $validator;
protected $data;

public function setFilter(Filter $filter)
{
    $this->filter = $filter;
}

public function setValidator(Validator $validator)
{
    $this->validator = $validator;
}

public function setData($data)
{
    $this->data = $data;
}
```

3.  接下来，我们定义一个 `validate()` 方法，该方法调用嵌入的 `Application\Filter\Validator` 实例的 `process()` 方法。我们检查 `$data` 和 `$validator` 是否存在。如果不存在，则抛出适当的异常，并附上指示需要先运行哪个方法的说明：

```php
public function validate()
{
    if (!$this->data)
        throw new RuntimeException(self::DATA_NOT_FOUND);

    if (!$this->validator)
        throw new RuntimeException(self::VALIDATOR_NOT_FOUND);
```

4.  在调用 `process()` 方法后，我们将验证结果消息与表单元素消息关联起来。请注意，`process()` 方法返回一个表示数据集整体验证状态的布尔值。当表单在验证失败后重新显示时，错误消息将出现在每个元素旁边：

```php
$valid = $this->validator->process($this->data);

foreach ($this->elements as $element) {
    if (isset($this->validator->getResults()[$element->getName()])) {
        $element->setErrors($this->validator->getResults()[$element->getName()]->messages);
    }
}
return $valid;
```

5.  以类似的方式，我们定义一个 `filter()` 方法，该方法调用嵌入的 `Application\Filter\Filter` 实例的 `process()` 方法。与步骤 3 中描述的 `validate()` 方法一样，我们需要检查 `$data` 和 `$filter` 是否存在。如果缺失任何一项，我们抛出带有适当消息的 `RuntimeException`：

```php
public function filter()
{
    if (!$this->data)
        throw new RuntimeException(self::DATA_NOT_FOUND);

    if (!$this->filter)
        throw new RuntimeException(self::FILTER_NOT_FOUND);
```

6.  然后我们运行 `process()` 方法，该方法生成一个由 `Result` 对象组成的数组，其中 `$item` 属性代表过滤链的最终结果。然后我们循环遍历结果，如果对应的 `$element` 键匹配，则将 `value` 属性设置为过滤后的值。我们还添加过滤过程产生的任何消息。当表单随后重新显示时，所有 `value` 属性都将显示过滤结果：

```php
$this->filter->process($this->data);
foreach ($this->filter->getResults() as $key => $result) {
    if (isset($this->elements[$key])) {
        $this->elements[$key]->setAttribute('value', $result->item);
        if (isset($result->messages) && count($result->messages)) {
            foreach ($result->messages as $message) {
                $this->elements[$key]->addSingleError($message);
            }
        }
    }
}
```





## 工作原理……

您可以先按照上文描述对 `Application\Form\Factory` 进行修改。作为测试目标，您可以使用*工作原理...*章节中*链接 $...POST 过滤器*配方里展示的 `prospects` 数据库表。各种列设置应该能让您了解需要定义哪些表单元素、过滤器和验证器。

例如，您可以定义一个 `chap_06_tying_filters_to_form_definitions.php` 文件，其中将包含表单包装器、元素和过滤器分配的代码定义。以下是一些示例：

```php
<?php
use Application\Form\Generic;

define('VALIDATE_SUCCESS', 'SUCCESS: form submitted ok!');
define('VALIDATE_FAILURE', 'ERROR: validation errors detected');

$wrappers = [
    Generic::INPUT    => ['type' => 'td', 'class' => 'content'],
    Generic::LABEL    => ['type' => 'th', 'class' => 'label'],
    Generic::ERRORS   => ['type' => 'td', 'class' => 'error']
];

$elements = [
    'first_name' => [
        'class'    => 'Application\Form\Generic',
        'type'     => Generic::TYPE_TEXT,
        'label'    => 'First Name',
        'wrappers' => $wrappers,
        'attributes'=> ['maxLength'=>128,'required'=>'']
    ],
    'last_name'  => [
        'class'    => 'Application\Form\Generic',
        'type'     => Generic::TYPE_TEXT,
        'label'    => 'Last Name',
        'wrappers' => $wrappers,
        'attributes'=> ['maxLength'=>128,'required'=>'']
    ],
    // etc.
];

// overall form config
$formConfig = [
    'name'        => 'prospectsForm',
    'attributes'  => [
        'method'=>'post',
        'action'=>'chap_06_typing_filters_to_form.php'
    ],
    'row_wrapper' => ['type' => 'tr', 'class' => 'row'],
    'form_wrapper' => [
        'type'=>'table',
        'class'=>'table',
        'id'=>'prospectsTable',
        'class'=>'display','cellspacing'=>'0'
    ],
    'form_tag_inside_wrapper' => FALSE,
];

$assignments = [
    'first_name' => [ ['key' => 'length',
        'params' => ['min' => 1, 'max' => 128]],
        ['key' => 'alnum',
        'params' => ['allowWhiteSpace' => TRUE]],
        ['key' => 'required','params' => []] ],
    'last_name' => [ ['key' => 'length',
        'params' => ['min' => 1, 'max' => 128]],
        ['key' => 'alnum',
        'params' => ['allowWhiteSpace' => TRUE]],
        ['key' => 'required','params' => [] ] ],
    'address' => [ ['key' => 'length',
        'params' => ['max' => 256]] ],
    'city' => [ ['key' => 'length',
        'params' => ['min' => 1, 'max' => 64]] ],
    'state_province'=> [ ['key' => 'length',
        'params' => ['min' => 1, 'max' => 32]] ],
    'postal_code' => [ ['key' => 'length',
        'params' => ['min' => 1, 'max' => 16] ],
        ['key' => 'alnum',
        'params' => ['allowWhiteSpace' => TRUE]],
        ['key' => 'required','params' => []] ],
    'phone' => [ ['key' => 'phone', 'params' => []] ],
    'country' => [ ['key' => 'in_array',
        'params' => $countries ],
        ['key' => 'required','params' => []] ],
    'email' => [ ['key' => 'email', 'params' => [] ],
        ['key' => 'length',
        'params' => ['max' => 250] ],
        ['key' => 'required','params' => []] ],
    'budget' => [ ['key' => 'float', 'params' => [] ]
];
```

您可以使用之前配方中描述的已存在的 `chap_06_post_data_config_callbacks.php` 和 `chap_06_post_data_config_messages.php` 文件。最后，定义一个 `chap_06_tying_filters_to_form.php` 文件，该文件设置自动加载并包含这三个配置文件：

```php
<?php
require __DIR__ . '/../Application/Autoload/Loader.php';
Application\Autoload\Loader::init(__DIR__ . '../..');
include __DIR__ . '/chap_06_post_data_config_messages.php';
include __DIR__ . '/chap_06_post_data_config_callbacks.php';
include __DIR__ . '/chap_06_tying_filters_to_form_definitions.php';
?>
```

接下来，您可以创建表单工厂、过滤器和验证器类的实例：

```php
use Application\Form\Factory;
use Application\Filter\{ Validator, Filter };
$form = Factory::generate($elements);
$form->setFilter(new Filter($Callbacks['filters'],
    $Assignments['filters']));
$form->setValidator(new Validator($Callbacks['validators'],
    $Assignments['validators']));
```

然后，您可以检查是否存在 `$_POST` 数据。如果存在，则执行验证和过滤：

```php
$message = '';
if (isset($_POST['submit'])) {
    $form->setData($_POST);
    if ($form->validate()) {
        $message = VALIDATE_SUCCESS;
    } else {
        $message = VALIDATE_FAILURE;
    }
    $form->filter();
}
?>
```

视图逻辑非常简单：只需渲染表单即可。验证消息以及各个元素的值将作为验证和过滤过程的一部分被分配：

```php
<?= $form->render($form, $formConfig); ?>
```

以下是使用错误表单数据的示例：

![](img/39390f6d56c5a83b28db083a8bd5185c_243_0.png)

请注意过滤和验证消息。还要注意错误标签：

![](img/39390f6d56c5a83b28db083a8bd5185c_243_1.png)

# 7
## 访问 Web 服务

在本章中，我们将涵盖以下主题：

- 在 PHP 和 XML 之间进行转换
- 创建简单的 REST 客户端
- 创建简单的 REST 服务器
- 创建简单的 SOAP 客户端
- 创建简单的 SOAP 服务器

## 引言

向外部 Web 服务发起后台查询已成为任何 PHP Web 实践中日益重要的部分。提供适当、及时且丰富的数据能力意味着为您开发的客户和网站带来更多业务机会。我们首先介绍几个旨在实现**可扩展标记语言 (XML)** 与原生 PHP 之间数据转换的配方。接着，我们将展示如何实现简单的**表示状态转移 (REST)** 客户端和服务器。之后，我们将关注 **SOAP** 客户端和服务器。

## 在 PHP 和 XML 之间进行转换

在考虑 PHP 原生数据类型与 XML 之间的转换时，我们通常会将数组作为主要目标。基于这一点，从 PHP 数组转换为 XML 的过程与反向转换所需的策略截然不同。

> 也可以考虑对象转换；然而，在 XML 中渲染对象方法是困难的。不过，可以使用 `get_object_vars()` 函数将对象属性读取到数组中，从而表示属性。

### 实现方法...

1. 首先，我们定义一个 `Application\Parse\ConvertXml` 类。该类将持有用于从 XML 转换为 PHP 数组及反向转换的方法。我们需要 SPL 中的 `SimpleXMLElement` 和 `SimpleXMLIterator` 类：

    ```php
    namespace Application\Parse;

    use SimpleXMLIterator;
    use SimpleXMLElement;

    class ConvertXml
    {
    }
    ```

2. 接下来，我们定义一个 `xmlToArray()` 方法，该方法接受一个 `SimpleXMLIterator` 实例作为参数。它将被递归调用，并从 XML 文档生成 PHP 数组。我们利用 `SimpleXMLIterator` 遍历 XML 文档的能力，使用 `key()`、`current()`、`next()` 和 `rewind()` 方法进行导航：

    ```php
    public function xmlToArray(SimpleXMLIterator $xml) : array
    {
        $a = array();

        for( $xml->rewind(); $xml->valid(); $xml->next() ) {
            if(!array_key_exists($xml->key(), $a)) {
                $a[$xml->key()] = array();
            }

            if ($xml->hasChildren()) {
                $a[$xml->key() ][] = $this->xmlToArray($xml->current());
            }
            else{
                $a[$xml->key() ] = (array) $xml->current()->attributes();
                $a[$xml->key()][ 'value'] = strval($xml->current());
            }
        }
        return $a;
    }
    ```

3. 对于反向过程（同样递归调用），我们定义两个方法。第一个方法 `arrayToXml()` 设置初始的 `SimpleXMLElement` 实例，然后调用第二个方法 `phpToXml()`：

    ```php
    public function arrayToXml(array $a)
    {
        $xml = new SimpleXMLElement('<?xml version="1.0" standalone="yes"?><root></root>');
        $this->phpToXml($a, $xml);
        return $xml->asXML();
    }
    ```

4. 请注意，在第二个方法中，我们使用 `get_object_vars()` 以防数组元素之一是对象。您还会注意到，单独的数字不能作为 XML 标签，这意味着需要在数字前添加一些文本：

    ```php
    protected function phpToXml($value, &$xml)
    {
        $node = $value;
        if (is_object($node)) {
            $node = get_object_vars($node);
        }
        if (is_array($node)) {
            foreach ($node as $k => $v) {
                if (is_numeric($k)) {
                    $k = 'number' . $k;
                }
                if (is_array($v)) {
                    $newNode = $xml->addChild($k);
                    $this->phpToXml($v, $newNode);
                } elseif (is_object($v)) {
                    $newNode = $xml->addChild($k);
                    $this->phpToXml($v, $newNode);
                } else {
                    $xml->addChild($k, $v);
                }
            }
        } else {
            $xml->addChild(self::UNKNOWN_KEY, $node);
        }
    }
    ```




## 工作原理...

作为示例 XML 文档，你可以使用**美国国家气象局**的 **Web Services Description Language (WSDL)**。这是一个描述 SOAP 服务的 XML 文档，可以在 `http://graphical.weather.gov/xml/SOAP_server/ndfdXMLserver.php?wsdl` 找到。

我们将使用 *SimpleXMLIterator* 类来提供迭代机制。然后，你可以配置自动加载，并获取 *Application\Parse\ConvertXml* 的实例，使用 *xmlToArray()* 方法将 WSDL 转换为 PHP 数组：

```php
require __DIR__ . '/../Application/Autoload/Loader.php';
Application\Autoload\Loader::init(__DIR__ . '../');
use Application\Parse\ConvertXml;
$wsdl = 'http://graphical.weather.gov/xml/'
    . 'SOAP_server/ndfdXMLserver.php?wsdl';
$xml = new SimpleXMLIterator($wsdl, 0, TRUE);
$convert = new ConvertXml();
var_dump($convert->xmlToArray($xml));
```

生成的数组如下所示：

![](img/39390f6d56c5a83b28db083a8bd5185c_248_0.png)

若要执行反向操作，请使用本食谱中描述的 *arrayToXml()* 方法。作为源文档，你可以使用一个包含 MongoDB 培训视频大纲的 `source/data/mongo.db.global.php` 文件（该视频可通过 O'Reilly Media 获取，免责声明：由本作者制作！）。使用相同的自动加载器配置和 *Application\Parse\ConvertXml* 实例，以下是你可以使用的示例代码：

```php
$convert = new ConvertXml();
header('Content-Type: text/xml');
echo $convert->arrayToXml(include CONFIG_FILE);
```

以下是在浏览器中的输出结果：

![](img/39390f6d56c5a83b28db083a8bd5185c_249_0.png)

## 创建简单的 REST 客户端

REST 客户端使用 **HyperText Transfer Protocol (HTTP)** 生成针对外部 Web 服务的请求。通过更改 HTTP 方法，我们可以让外部服务执行不同的操作。虽然有许多可用的方法（或动词），但我们只关注 GET 和 POST。在本食谱中，我们将使用 **Adapter** 软件设计模式来展示实现 REST 客户端的两种不同方式。

## 操作方法...

- 1. 在我们能够定义 REST 客户端适配器之前，我们需要定义通用类来表示请求和响应信息。首先，我们从一个抽象类开始，该类包含请求或响应所需的方法和属性：

```php
namespace Application\Web;

class AbstractHttp
{
```

- 2. 接下来，我们定义代表 HTTP 信息的类常量：
```php
    const METHOD_GET = 'GET';
    const METHOD_POST = 'POST';
    const METHOD_PUT = 'PUT';
    const METHOD_DELETE = 'DELETE';
    const CONTENT_TYPE_HTML = 'text/html';
    const CONTENT_TYPE_JSON = 'application/json';
    const CONTENT_TYPE_FORM_URL_ENCODED =
        'application/x-www-form-urlencoded';
    const HEADER_CONTENT_TYPE = 'Content-Type';
    const TRANSPORT_HTTP = 'http';
    const TRANSPORT_HTTPS = 'https';
    const STATUS_200 = '200';
    const STATUS_401 = '401';
    const STATUS_500 = '500';
```

- 3. 然后，我们定义请求或响应所需的属性：
```php
    protected $uri;        // 例如 http://xxx.com/yyy
    protected $method;     // 例如 GET, PUT, POST, DELETE
    protected $headers;    // HTTP 头
    protected $cookies;    // cookies
    protected $metaData;   // 关于传输的信息
    protected $transport;  // 例如 http 或 https
    protected $data = array();
```

- 4. 逻辑上，应该为这些属性定义 getter 和 setter：
```php
    public function setMethod($method)
    {
        $this->method = $method;
    }

    public function getMethod()
    {
        return $this->method ?? self::METHOD_GET;
    }

    // 等等。
```

- 5. 某些属性需要按键访问。为此，我们定义 getXxxByKey() 和 setXxxByKey() 方法：
```php
    public function setHeaderByKey($key, $value)
    {
        $this->headers[$key] = $value;
    }

    public function getHeaderByKey($key)
    {
        return $this->headers[$key] ?? NULL;
    }

    public function getDataByKey($key)
    {
        return $this->data[$key] ?? NULL;
    }

    public function getMetaDataByKey($key)
    {
        return $this->metaData[$key] ?? NULL;
    }
```

- 在某些情况下，请求将需要参数。我们假设参数将以存储在 $data 属性中的 PHP 数组形式存在。然后我们可以使用 http_build_query() 函数构建请求 URL：
```php
    public function setUri($uri, array $params = NULL)
    {
        $this->uri = $uri;
        $first = TRUE;
        if ($params) {
            $this->uri .= '?' . http_build_query($params);
        }
    }

    public function getDataEncoded()
    {
        return http_build_query($this->getData());
    }
```

- 最后，我们根据原始请求设置 $transport：
```php
    public function setTransport($transport = NULL)
    {
        if ($transport) {
            $this->transport = $transport;
        } else {
            if (substr($this->uri, 0, 5) === self::TRANSPORT_HTTPS) {
                $this->transport = self::TRANSPORT_HTTPS;
            } else {
                $this->transport = self::TRANSPORT_HTTP;
            }
        }
    }
```

## 访问 Web 服务

- 8. 在本食谱中，我们将定义一个 `Application\Web\Request` 类，该 class 可以在我们希望生成请求时接受参数，或者，在实现接受请求的服务器时，用传入的请求信息填充属性：

```php
namespace Application\Web;
class Request extends AbstractHttp
{
    public function __construct(
        $uri = NULL, $method = NULL, array $headers = NULL,
        array $data = NULL, array $cookies = NULL)
    {
        if (!$headers) $this->headers = $_SERVER ?? array();
        else $this->headers = $headers;

        if (!$uri) $this->uri = $this->headers['PHP_SELF'] ?? '';
        else $this->uri = $uri;

        if (!$method) $this->method =
        $this->headers['REQUEST_METHOD'] ?? self::METHOD_GET;
        else $this->method = $method;

        if (!$data) $this->data = $_REQUEST ?? array();
        else $this->data = $data;

        if (!$cookies) $this->cookies = $_COOKIE ?? array();
        else $this->cookies = $cookies;

        $this->setTransport();
    }
}
```

- 9. 现在，我们可以将注意力转向响应类。在这种情况下，我们将定义一个 `Application\Web\Received` 类。该名称反映了我们从外部 Web 服务接收数据并进行重新封装的事实：

```php
namespace Application\Web;
class Received extends AbstractHttp
{
    public function __construct(
        $uri = NULL, $method = NULL, array $headers = NULL,
        array $data = NULL, array $cookies = NULL)
    {
        $this->uri = $uri;
        $this->method = $method;
        $this->headers = $headers;
        $this->data = $data;
        $this->cookies = $cookies;
        $this->setTransport();
    }
}
```

## 创建基于流的 REST 客户端

我们现在准备考虑实现 REST 客户端的两种不同方式。第一种方法是使用底层 PHP I/O 层，称为 **Streams**。该层提供一系列包装器，用于访问外部流资源。默认情况下，任何 PHP 文件命令都将使用文件包装器，该包装器提供对本地文件系统的访问。我们将使用 http:// 或 https:// 包装器来实现 Application\Web\Client\Streams 适配器：

- 首先，我们定义一个 `Application\Web\Client\Streams` 类：

```php
namespace Application\Web\Client;

use Application\Web\{ Request, Received };

class Streams
{
    const BYTES_TO_READ = 4096;
```

- 接下来，我们定义一个方法来将请求发送到外部 Web 服务。对于 GET，我们将参数添加到 URL 中。对于 POST，我们创建一个流上下文，其中包含元数据，指示远程服务我们正在提供数据。使用 PHP Streams，发起请求只需组合 URL，并在 POST 的情况下设置流上下文。然后我们使用简单的 `fopen()`：

```php
public static function send(Request $request)
{
    $data = $request->getDataEncoded();
    $received = new Received();

    switch ($request->getMethod()) {

    case Request::METHOD_GET :

        if ($data) {
            $request->setUri($request->getUri() . '? ' . $data);
        }

        $resource = fopen($request->getUri(), 'r');
        break;

    case Request::METHOD_POST :
        $opts = [
            $request->getTransport() =>
                [
                    'method'   => Request::METHOD_POST,
                    'header'   => Request::HEADER_CONTENT_TYPE
                        . ': ' . Request::CONTENT_TYPE_FORM_URL_ENCODED,
                    'content'  => $data
                ]
        ];
        $resource = fopen($request->getUri(), 'w',
            stream_context_create($opts));
        break;
```



return self::getResults($received, $resource);
}

3. 最后，我们来看一下如何检索结果并将其打包成一个 `Received` 对象。你会发现我们添加了一个机制来解码以 JSON 格式接收的数据：

```php
protected static function getResults(Received $received, $resource) {
	$received->setMetaData(stream_get_meta_data($resource));
	$data = $received->getMetaDataByKey('wrapper_data');
	if (!empty($data) && is_array($data)) {
		foreach ($data as $item) {
			if (preg_match(/^HTTP/\\d.\\d (\\d+?) .*?$/, $item, $matches)) {
				$received->setHeaderByKey('status', $matches[1]);
			} else {
				list($key, $value) = explode(':', $item);
				$received->setHeaderByKey($key, trim($value));
			}
		}
	}
	$payload = '';
	while (!feof($resource)) {
		$payload .= fread($resource, self::BYTES_TO_READ);
	}
	if ($received->getHeaderByKey(Received::HEADER_CONTENT_TYPE)) {
		switch (TRUE) {
			case stripos($received->getHeaderByKey(
				Received::HEADER_CONTENT_TYPE),
				Received::CONTENT_TYPE_JSON) !== FALSE:
			$received->setData(json_decode($payload));
			break;
			default:
			$received->setData($payload);
			break;
		}
	}
	return $received;
}
```

## 定义基于 cURL 的 REST 客户端

现在我们将看看 REST 客户端的另一种方法，即基于 cURL 扩展的方法：

1. 对于这种方法，我们假设使用相同的请求和响应类。初始类定义与之前讨论的 Streams 客户端非常相似：
   ```php
   namespace Application\Web\Client;
   use Application\Web\{ Request, Received };
   class Curl
   {
   ```

2. 与使用 Streams 相比，send() 方法要简单得多。我们只需要定义一个选项数组，然后让 cURL 完成剩下的工作：
   ```php
   public static function send(Request $request)
   {
       $data = $request->getDataEncoded();
       $received = new Received();
       switch ($request->getMethod()) {
       case Request::METHOD_GET :
       $uri = ($data
           ? $request->getUri() . '?' . $data
           : $request->getUri());
       $options = [
           CURLOPT_URL => $uri,
           CURLOPT_HEADER => 0,
           CURLOPT_RETURNTRANSFER => TRUE,
           CURLOPT_TIMEOUT => 4
       ];
       break;
       ```

3. POST 需要稍有不同的 cURL 参数：
   ```php
   case Request::METHOD_POST :
   $options = [
       CURLOPT_POST => 1,
       CURLOPT_HEADER => 0,
       CURLOPT_URL => $request->getUri(),
       CURLOPT_FRESH_CONNECT => 1,
       CURLOPT_RETURNTRANSFER => 1,
       CURLOPT_FORBID_REUSE => 1,
       CURLOPT_TIMEOUT => 4,
       CURLOPT_POSTFIELDS => $data
   ];
   break;
   ```

4. 然后我们执行一系列 cURL 函数，并将结果通过 `getResults()` 处理：
   ```php
   $ch = curl_init();
   curl_setopt_array($ch, $options);
   if (! $result = curl_exec($ch))
   {
       trigger_error(curl_error($ch));
   }
   $received->setMetaData(curl_getinfo($ch));
   curl_close($ch);
   return self::getResults($received, $result);
   }
   ```

5. `getResults()` 方法将结果打包成一个 Received 对象：
   ```php
   protected static function getResults(Received $received, $payload)
   {
       $type = $received->getMetaDataByKey('content_type');
       if ($type) {
           switch (TRUE) {
               case stripos($type, Received::CONTENT_TYPE_JSON) !== FALSE:
                   $received->setData(json_decode($payload));
                   break;
               default :
                   $received->setData($payload);
                   break;
           }
       }
       return $received;
   }
   ```

## 工作原理...

请确保将所有前面的代码复制到这些类中：

- Application\Web\AbstractHttp
- Application\Web\Request
- Application\Web\Received
- Application\Web\Client\Streams
- Application\Web\Client\Curl

## 第 7 章

为了演示，你可以向 Google Maps API 发起 REST 请求，以获取两个地点之间的驾车路线。你还需要按照 https://developers.google.com/maps/documentation/directions/get-api-key 提供的说明创建一个 API 密钥，以便实现此目的。

然后，你可以定义一个调用脚本 `chap_07_simple_rest_client_google_maps_curl.php`，使用 cURL 客户端发起请求。你也可以考虑定义一个调用脚本 `chap_07_simple_rest_client_google_maps_streams.php`，使用 Streams 客户端发起请求：

```php
<?php
define('DEFAULT_ORIGIN', 'New York City');
define('DEFAULT_DESTINATION', 'Redondo Beach');
define('DEFAULT_FORMAT', 'json');
$apiKey = include __DIR__ . '/google_api_key.php';
require __DIR__ . '/../Application/Autoload/Loader.php';
Application\Autoload\Loader::init(__DIR__ . '../');
use Application\Web\Request;
use Application\Web\Client\Curl;
```

然后，你可以获取起点和终点：

```php
$start = $_GET['start'] ?? DEFAULT_ORIGIN;
$end   = $_GET['end'] ?? DEFAULT_DESTINATION;
$start = strip_tags($start);
$end   = strip_tags($end);
```

现在，你可以填充 Request 对象，并使用它生成请求：

```php
$request = new Request(
    'https://maps.googleapis.com/maps/api/directions/json',
    Request::METHOD_GET,
    NULL,
    ['origin' => $start, 'destination' => $end, 'key' => $apiKey],
    NULL
);

$received = Curl::send($request);
$routes   = $received->getData()->routes[0];
include __DIR__ . '/chap_07_simple_rest_client_google_maps_template.php';
```

为了演示目的，你也可以定义一个模板，该模板包含显示请求结果逻辑：

```php
<?php foreach ($routes->legs as $item) : ?>
  <!-- Trip Info -->
  <br>Distance: <?= $item->distance->text; ?>
  <br>Duration: <?= $item->duration->text; ?>
  <!-- Driving Directions -->
  <table>
  <tr>
  <th>Distance</th><th>Duration</th><th>Directions</th>
  </tr>
  <?php foreach ($item->steps as $step) : ?>
  <?php $class = ($count++ & 01) ? 'color1' : 'color2'; ?>
  <tr>
  <td class="<?= $class ?>"><?= $step->distance->text ?></td>
  <td class="<?= $class ?>"><?= $step->duration->text ?></td>
  <td class="<?= $class ?>">
  <?= $step->html_instructions ?></td>
  </tr>
  <?php endforeach; ?>
  </table>
  <?php endforeach; ?>
```

以下是在浏览器中看到的请求结果：

![](img/39390f6d56c5a83b28db083a8bd5185c_258_0.png)

### 更多相关内容...

**PHP 标准推荐（PSR-7）** 精确定义了在进行 PHP 应用程序之间请求时应使用的请求和响应对象。这在附录“定义 PSR-7 类”中有详细讨论。

### 参见

有关 Streams 的更多信息，请参阅此 PHP 文档页面 http://php.net/manual/en/book.stream.php。一个常被问到的问题是“HTTP PUT 和 POST 有什么区别？”，关于此主题的出色讨论，请参阅 http://stackoverflow.com/questions/107390/whats-the-difference-between-a-post-and-a-put-http-request。有关从 Google 获取 API 密钥的更多信息，请参阅以下网页：

https://developers.google.com/maps/documentation/directions/get-api-key

https://developers.google.com/maps/documentation/directions/intro#Introduction

## 创建简单的 REST 服务器

在实现 REST 服务器时有几个需要考虑的因素。回答这三个问题将帮助你定义你的 REST 服务：

- 如何捕获原始 Request？
- 你想发布什么样的 **应用程序编程接口（API）**？
- 你打算如何将 HTTP 动词（例如，GET、PUT、POST 和 DELETE）映射到 API 方法？

### 操作方式...

1. 我们将通过基于前一个食谱中定义的请求和响应类来构建我们的 REST 服务器。*创建简单的 REST 客户端*。回顾前一个食谱中讨论的类，包括以下内容：
   - `Application\Web\AbstractHttp`
   - `Application\Web\Request`
   - `Application\Web\Received`





## 2. 我们还需要基于 AbstractHttp 定义一个正式的 Application\Web\Response 响应类。

该类与其他类的主要区别在于，它接受 `Application\Web\Request` 的实例作为参数。主要工作是在 `__construct( )` 方法中完成的。设置 `Content-Type` 头文件和状态也很重要：

```php
namespace Application\Web;

class Response extends AbstractHttp
{
    public function __construct(Request $request = NULL,
        $status = NULL, $contentType = NULL)
    {
        if ($request) {
            $this->uri = $request->getUri();
            $this->data = $request->getData();
            $this->method = $request->getMethod();
            $this->cookies = $request->getCookies();
            $this->setTransport();
        }
        $this->processHeaders($contentType);
        if ($status) {
            $this->setStatus($status);
        }
    }

    protected function processHeaders($contentType)
    {
        if (!$contentType) {
            $this->setHeaderByKey(self::HEADER_CONTENT_TYPE,
                self::CONTENT_TYPE_JSON);
        } else {
            $this->setHeaderByKey(self::HEADER_CONTENT_TYPE,
                $contentType);
        }
    }

    public function setStatus($status)
    {
        $this->status = $status;
    }

    public function getStatus()
    {
        return $this->status;
    }
}
```

### 现在我们可以定义 Application\Web\Rest\Server 类了。

你可能会惊讶于它的简单。实际工作是在相关的 API 类中完成的：

```php
namespace Application\Web\Rest;

use Application\Web\{ Request, Response, Received };

class Server
{
    protected $api;

    public function __construct(ApiInterface $api)
    {
        $this->api = $api;
    }
}
```

### 接下来，我们定义一个 listen() 方法，作为请求的目标。

服务器实现的核心是这行代码：

```php
$jsonData = json_decode(file_get_contents('php://input'), true);
```

这捕获了原始输入，假设其格式为 JSON：

```php
public function listen()
{
    $request = new Request();
    $response = new Response($request);
    $getPost = $_REQUEST ?? array();
    $jsonData = json_decode(
        file_get_contents('php://input'), true);
    $jsonData = $jsonData ?? array();
    $request->setData(array_merge($getPost, $jsonData));
```

我们还添加了身份验证机制。否则，任何人都可以发起请求并获取可能敏感的数据。请注意，我们不让 Server 类执行身份验证；而是将其留给 API 类：

```php
if (!$this->api->authenticate($request)) {
    $response->setStatus(401);
    echo $this->api::ERROR;
    exit;
}
```

### 6. 然后我们将 API 方法映射到主要的 HTTP 方法 GET、PUT、POST 和 DELETE：

```php
$id = $request->getData(){$this->api::ID_FIELD} ?? NULL;
switch (strtoupper($request->getMethod())) {
    case Request::METHOD_POST :
        $this->api->post($request, $response);
        break;
    case Request::METHOD_PUT :
        $this->api->put($request, $response);
        break;
    case Request::METHOD_DELETE :
        $this->api->delete($request, $response);
        break;
    case Request::METHOD_GET :
    default :
        // return all if no params
        $this->api->get($request, $response);
}
```

### 7. 最后，我们打包响应并发送出去，使用 JSON 编码：

```php
$this->processResponse($response);
echo json_encode($response->getData());
}
```

### 8. processResponse() 方法设置头文件并确保结果被打包为 Application\Web\Response 对象：

```php
protected function processResponse($response)
{
    if ($response->getHeaders()) {
        foreach ($response->getHeaders() as $key => $value) {
            header($key . ': ' . $value, TRUE,
                   $response->getStatus());
        }
    }
    header(Request::HEADER_CONTENT_TYPE
           . ': ' . Request::CONTENT_TYPE_JSON, TRUE);
    if ($response->getCookies()) {
        foreach ($response->getCookies() as $key => $value) {
            setcookie($key, $value);
        }
    }
}
```

### 9. 如前所述，实际工作是由 API 类完成的。

我们从定义一个抽象类开始，确保主要方法 `get()`、`put()` 等都有表示，并且所有这些方法都接受请求和响应对象作为参数。你可能注意到，我们添加了一个 `generateToken()` 方法，使用 PHP 7 的 `random_bytes()` 函数生成真正随机的 16 字节序列：

```php
namespace Application\Web\Rest; 

use Application\Web\{ Request, Response }; 

abstract class AbstractApi implements ApiInterface 
{
  const TOKEN_BYTE_SIZE = 16; 
  protected $registeredKeys; 

  abstract public function get(Request $request,
        Response $response);
  abstract public function put(Request $request,
        Response $response);
  abstract public function post(Request $request,
        Response $response);
  abstract public function delete(Request $request,
        Response $response);
  abstract public function authenticate(Request $request); 

  public function __construct($registeredKeys, $tokenField)
  {
    $this->registeredKeys = $registeredKeys;
  } 

  public static function generateToken()
  {
    return bin2hex(random_bytes(self::TOKEN_BYTE_SIZE));
  } 
}
```

### 10. 我们还定义了一个相应的接口，可用于架构和设计目的，以及代码开发控制：

```php
namespace Application\Web\Rest; 

use Application\Web\{ Request, Response }; 

interface ApiInterface 
{
  public function get(Request $request, Response $response); 
  public function put(Request $request, Response $response); 
  public function post(Request $request, Response $response); 
  public function delete(Request $request, Response $response); 
  public function authenticate(Request $request); 
}
```

## 访问 Web 服务

### 11. 在此，我们展示一个基于 AbstractApi 的示例 API。

此类利用了第 5 章 *Interacting with a Database* 中定义的数据库类：

```php
namespace Application\Web\Rest;

use Application\Web\{ Request, Response, Received };
use Application\Entity\Customer;
use Application\Database\{ Connection, CustomerService };

class CustomerApi extends AbstractApi
{
    const ERROR = 'ERROR';
    const ERROR_NOT_FOUND = 'ERROR: Not Found';
    const SUCCESS_UPDATE = 'SUCCESS: update succeeded';
    const SUCCESS_DELETE = 'SUCCESS: delete succeeded';
    const ID_FIELD = 'id';         // field name of primary key
    const TOKEN_FIELD = 'token';   // field used for authentication
    const LIMIT_FIELD = 'limit';
    const OFFSET_FIELD = 'offset';
    const DEFAULT_LIMIT = 20;
    const DEFAULT_OFFSET = 0;

    protected $service;

    public function __construct($registeredKeys,
                                $dbparams, $tokenField = NULL)
    {
        parent::__construct($registeredKeys, $tokenField);
        $this->service = new CustomerService(
            new Connection($dbparams));
    }
```

### 12. 所有方法都接收请求和响应作为参数。

你会注意到使用 `getDataByKey()` 来获取数据项。实际的数据库交互由服务类执行。你可能还会注意到，在所有情况下，我们都设置了一个 HTTP 状态码，以告知客户端成功或失败。对于 `get()` 方法，我们查找 `ID` 参数。如果接收到，我们仅提供单个客户的信息。否则，我们使用 `limit` 和 `offset` 提供所有客户的列表：

```php
public function get(Request $request, Response $response)
{
    $result = array();
    $id = $request->getDataByKey(self::ID_FIELD) ?? 0;
    if ($id > 0) {
        $result = $this->service->
            fetchById($id)->entityToArray();
    } else {
$limit = $request->getDataByKey(self::LIMIT_FIELD) ?? self::DEFAULT_LIMIT;
$offset = $request->getDataByKey(self::OFFSET_FIELD) ?? self::DEFAULT_OFFSET;
$result = [];
$fetch = $this->service->fetchAll($limit, $offset);
foreach ($fetch as $row) {
    $result[] = $row;
}
if ($result) {
    $response->setData($result);
    $response->setStatus(Request::STATUS_200);
} else {
    $response->setData([self::ERROR_NOT_FOUND]);
    $response->setStatus(Request::STATUS_500);
}
```

### 13. put() 方法用于插入客户数据：

```php
public function put(Request $request, Response $response)
{
    $cust = Customer::arrayToEntity($request->getData(),
        new Customer());
    if ($newCust = $this->service->save($cust)) {
        $response->setData(['success' => self::SUCCESS_UPDATE,
            'id' => $newCust->getId()]);
        $response->setStatus(Request::STATUS_200);
    } else {
        $response->setData([self::ERROR]);
        $response->setStatus(Request::STATUS_500);
    }
}
```

### 14. post() 方法用于更新现有的客户条目：

```php
public function post(Request $request, Response $response)
{
    $id = $request->getDataByKey(self::ID_FIELD) ?? 0;
    $reqData = $request->getData();
    $custData = $this->service->
        fetchById($id)->entityToArray();
    $updateData = array_merge($custData, $reqData);
    $updateCust = Customer::arrayToEntity($updateData,
```





## 15. 顾名思义，`delete()` 方法用于删除客户条目：

```php
public function delete(Request $request, Response $response)
{
    $id = $request->getDataByKey(self::ID_FIELD) ?? 0;
    $cust = $this->service->fetchById($id);
    if ($cust && $this->service->remove($cust)) {
        $response->setData(['success' => self::SUCCESS_DELETE,
                          'id' => $id]);
        $response->setStatus(Request::STATUS_200);
    } else {
        $response->setData([self::ERROR_NOT_FOUND]);
        $response->setStatus(Request::STATUS_500);
    }
}
```

## 16. 最后，我们定义 `authenticate()` 方法，在本例中提供一个低层机制来保护 API 的使用：

```php
public function authenticate(Request $request)
{
    $authToken = $request->getDataByKey(self::TOKEN_FIELD)
        ?? FALSE;
    if (in_array($authToken, $this->registeredKeys, TRUE)) {
        return TRUE;
    } else {
        return FALSE;
    }
}
```

## 工作原理...

定义以下类，这些类在之前的食谱中已经讨论过：

- Application\Web\AbstractHttp
- Application\Web\Request
- Application\Web\Response

然后，你可以定义本食谱中描述的以下类，如表中所示：

| 类 | 在这些步骤中讨论 |
| :--- | :--- |
| Application\Web\Response | 2 |
| Application\Web\Rest\Server | 3 - 8 |
| Application\Web\Rest\AbstractApi | 9 |
| Application\Web\Rest\ApiInterface | 10 |
| Application\Web\Rest\CustomerApi | 11 - 16 |

现在你可以自由开发自己的 API 类。然而，如果你选择遵循示例 `Application\Web\Rest\CustomerApi`，你也必须确保实现这些在第五章 *与数据库交互* 中涵盖的类：

- Application\Entity\Customer
- Application\Database\Connection
- Application\Database\CustomerService

你现在可以定义一个 `chap_07_simple_rest_server.php` 脚本来调用 REST 服务器：

```php
<?php
$dbParams = include __DIR__ . '/../../config/db.config.php';
require __DIR__ . '/../../Application/Autoload/Loader.php';
Application\Autoload\Loader::init(__DIR__ . '../');
use Application\Web\Rest\Server;
use Application\Web\Rest\CustomerApi;
$apiKey = include __DIR__ . '/api_key.php';
$server = new Server(new CustomerApi($apiKey), $dbParams, 'id');
$server->listen();
```

然后，你可以使用内置的 PHP 7 开发服务器来监听端口 `8080` 以处理 REST 请求：

```
php -S localhost:8080 chap_07_simple_rest_server.php
```

## 访问 Web 服务

为了测试你的 API，使用 `Application\Web\Rest\AbstractApi::generateToken()` 方法生成一个认证令牌，你可以将其放在 `api_key.php` 文件中，内容类似于这样：

```php
<?php return '79e9b5211bbf2458a4085707ea378129';
```

然后，你可以使用通用的 API 客户端（如前一个食谱中描述的那个），或者使用浏览器插件（例如 Chao Zhou 开发的 RESTClient，更多信息见 `http://restclient.net/`）来生成示例请求。请确保在请求中包含令牌，否则按定义的 API 将拒绝该请求。

这是一个针对 `ID 1` 的 POST 请求示例，它将 `balance` 字段设置为值 `888888`：

![](img/39390f6d56c5a83b28db083a8bd5185c_268_0.png)

### 更多内容...

有许多库可以帮助你实现 REST 服务器。我最喜欢的是在一个单文件中实现 REST 服务器的示例：`https://www.leaseweb.com/labs/2015/10/creating-a-simple-rest-api-in-php/`

各种框架，如 CodeIgniter 和 Zend Framework，也有 REST 服务器的实现。

### 如何操作...

与实现 REST 客户端或服务器的过程相比，使用 SOAP 非常简单，因为有一个 PHP SOAP 扩展提供了这两种能力。

![](img/39390f6d56c5a83b28db083a8bd5185c_269_0.png)

> 一个经常问到的问题是“SOAP 和 REST 有什么区别？” SOAP 内部使用 XML 作为其数据格式。SOAP 使用 HTTP 但仅作为传输介质，且不感知其他 HTTP 方法。REST 直接操作 HTTP，可以使用任何数据格式，但首选 JSON。另一个关键区别是，SOAP 可以与 WSDL 配合使用，这使得服务具有自描述性，从而更具公开性。因此，SOAP 服务通常由公共机构（如国家卫生组织）提供。

在本例中，我们将向美国国家气象局提供的现有 SOAP 服务发起一个 SOAP 请求：

1. 首先要考虑的是识别 **WSDL** 文档。WSDL 是一个描述服务的 XML 文档：

   ```php
   $wsdl = 'http://graphical.weather.gov/xml/SOAP_server/'
           . 'ndfdXMLserver.php?wsdl';
   ```

2. 接下来，我们使用 WSDL 创建一个 *soap* 客户端实例：

   ```php
   $soap = new SoapClient($wsdl, array('trace' => TRUE));
   ```

3. 然后，我们可以自由地初始化一些变量，为天气预报请求做准备：

   ```php
   $units = 'm';
   $params = '';
   $numDays = 7;
   $weather = '';
   $format = '24 hourly';
   $startTime = new DateTime();
   ```

4. 然后，我们可以发起一个 `LatLonListCityNames()` SOAP 请求，这在 WSDL 中被标识为一个操作，用于获取服务支持的城市列表。请求以 XML 格式返回，这建议创建一个 `SimpleXMLElement` 实例：

   ```php
   $xml = new SimpleXMLElement($soap->LatLonListCityNames());
   ```

5. 不幸的是，城市列表及其对应的纬度和 longitude 位于不同的 XML 节点中。因此，我们使用 `array_combine()` PHP 函数创建一个关联数组，其中经纬度作为键，城市名称作为值。然后我们可以稍后使用此数组来呈现 HTML SELECT 下拉列表，使用 `asort()` 对列表进行字母排序：

   ```php
   $cityNames = explode('|', $xml->cityNameList);
   $latLonCity = explode(' ', $xml->latLonList);
   $cityLatLon = array_combine($latLonCity, $cityNames);
   asort($cityLatLon);
   ```

6. 然后，我们可以如下从 web 请求中获取城市数据：

   ```php
   $currentLatLon = (isset($_GET['city']) ? strip_tags(
     urldecode($_GET['city'])) : '' ;
   ```

7. 我们要发起的 SOAP 调用是 `NDFDgenByDay()`。我们可以通过检查 WSDL 来确定提供给 SOAP 服务器的参数的性质：

   ```xml
   <message name="NDFPDgenByDayRequest">
     <part name="latitude" type="xsd:decimal"/>
     <part name="longitude" type="xsd:decimal"/>
     <part name="startDate" type="xsd:date"/>
     <part name="numDays" type="xsd:integer"/>
     <part name="Unit" type="xsd:string"/>
     <part name="format" type="xsd:string"/>
   </message>
   ```

8. 如果 `$currentLatLon` 的值已设置，我们可以处理该请求。我们将请求包裹在 `try {} catch {}` 块中，以防抛出任何异常：

   ```php
   if ($currentLatLon) {
     list($lat, $lon) = explode(',', $currentLatLon);
     try {
       $weather = $soap->NDFDgenByDay($lat, $lon,
         $startTime->format('Y-m-d'), $numDays, $unit, $format);
     } catch (Exception $e) {
       $weather = PHP_EOL;
       $weather .= 'Latitude: ' . $lat . ' | Longitude: ' . $lon;
       $weather .= 'ERROR' . PHP_EOL;
       $weather = $e->getMessage() . PHP_EOL;
       $weather .= $soap->__getLastResponse() . PHP_EOL;
     }
   }
   ```

## 工作原理...

将上述所有代码复制到 `chap_07_simple_soap_client_weather_service.php` 文件中。然后你可以添加视图逻辑，显示带有城市列表的表单以及结果：

```html
<form method="get" name="forecast">
<br> City List:
<select name="city">
<?php foreach ($cityLatLon as $latLon => $city) : ?>
<?php $select = ($currentLatLon == $latLon) ? ' selected' : '' ?>
<option value="<? echo urlencode($latLon) ?>" <? echo $select ?>>
<? echo $city ?>
</option>
<?php endforeach; ?>
</select>
<br><input type="submit" value="OK"><br>
</form>
<pre>
<?php var_dump($weather); ?>
</pre>
```

这是在浏览器中请求俄亥俄州克利夫兰天气预报的结果：

![](img/39390f6d56c5a83b28db083a8bd5185c_271_0.png)




## 参见

关于 SOAP 和 REST 之间差异的良好讨论，请参考位于 [http://stackoverflow.com/questions/209905/representational-state-transfer-rest-and-simple-object-access-protocol-soap?lq=1](http://stackoverflow.com/questions/209905/representational-state-transfer-rest-and-simple-object-access-protocol-soap?lq=1) 的文章。

## 创建简单的 SOAP 服务器

与 SOAP 客户端一样，我们可以使用 PHP 的 SOAP 扩展来实现 SOAP 服务器。实现过程中最困难的部分将从 API 类生成 WSDL。由于市面上有许多优秀的 WSDL 生成器，我们在此不详细涵盖该过程。

### 操作步骤...

- 首先，你需要一个将由 SOAP 服务器处理的 API。在本示例中，我们定义了一个 `Application\Web\Soap\ProspectsApi` 类，它允许我们创建、读取、更新和删除 prospects 表：

```php
namespace Application\Web\Soap;
use PDO;

class ProspectsApi
{
    protected $registerKeys;
    protected $pdo;

    public function __construct($pdo, $registeredKeys)
    {
        $this->pdo = $pdo;
        $this->registeredKeys = $registeredKeys;
    }
}
```

- 然后，我们定义对应于创建、读取、更新和删除的方法。在本示例中，方法命名为 `put()`、`get()`、`post()` 和 `delete()`。这些方法进而调用生成 SQL 请求的方法，这些请求由 PDO 实例执行。以下是 `get()` 的示例：

```php
public function get(array $request, array $response)
{
    if (!($this->authenticate($request))) return FALSE;
    $result = array();
    $id = $request[self::ID_FIELD] ?? 0;
    $email = $request[self::EMAIL_FIELD] ?? 0;
    if ($id > 0) {
        $result = $this->fetchById($id);
        $response[self::ID_FIELD] = $id;
    } elseif ($email) {
        $result = $this->fetchByEmail($email);
        $response[self::ID_FIELD] = $result[self::ID_FIELD] ?? 0;
    } else {
        $limit = $request[self::LIMIT_FIELD] ?? self::DEFAULT_LIMIT;
        $offset = $request[self::OFFSET_FIELD] ?? self::DEFAULT_OFFSET;
        $result = [];
        foreach ($this->fetchAll($limit, $offset) as $row) {
            $result[] = $row;
        }
    }

    $response = $this->processResponse($result, $response, self::SUCCESS, self::ERROR);
    return $response;
}

protected function processResponse($result, $response, $success_code, $error_code)
{
    if ($result) {
        $response['data'] = $result;
        $response['code'] = $success_code;
        $response['status'] = self::STATUS_200;
    } else {
        $response['data'] = FALSE;
        $response['code'] = self::ERROR_NOT_FOUND;
        $response['status'] = self::STATUS_500;
    }
    return $response;
}
```

- 然后，你可以从你的 API 生成 WSDL。有很多基于 PHP 的 WSDL 生成器可用（参见“更多...”部分）。大多数要求你在将被发布的方法之前添加 `phpDocumentor` 标签。在我们的示例中，两个参数都是数组。以下是前面讨论的 API 的完整 WSDL：

```xml
<?xml version="1.0" encoding="UTF-8"?>
<wsdl:definitions xmlns:tns="php7cookbook"
targetNamespace="php7cookbook"
xmlns:soap="http://schemas.xmlsoap.org/wsdl/soap/"
xmlns:xs="http://www.w3.org/2001/XMLSchema"
xmlns:wsdl="http://schemas.xmlsoap.org/wsdl/"
xmlns:soapenc="http://schemas.xmlsoap.org/soap/encoding/">

<wsdl:message name="getSoapIn">
<wsdl:part name="request" type="tns:array" />
<wsdl:part name="response" type="tns:array" />
</wsdl:message>

<wsdl:message name="getSoapOut">
<wsdl:part name="return" type="tns:array" />
</wsdl:message>
<!--some nodes removed to conserve space -->
<wsdl:portType name="CustomerApiSoap">
<!--some nodes removed to conserve space -->
<wsdl:binding name="CustomerApiSoap" type="tns:CustomerApiSoap">
<soap:binding transport="http://schemas.xmlsoap.org/soap/http" style="rpc" />
<wsdl:operation name="get">
<soap:operation soapAction="php7cookbook#get" />
<wsdl:input>
<soap:body use="encoded" encodingStyle="http://schemas.xmlsoap.org/soap/encoding/" namespace="php7cookbook" parts="request response" />
</wsdl:input>
<wsdl:output>
<soap:body use="encoded" encodingStyle="http://schemas.xmlsoap.org/soap/encoding/" namespace="php7cookbook" parts="return" />
</wsdl:output>
</wsdl:operation>
<!--some nodes removed to conserve space -->
</wsdl:binding>
<wsdl:service name="CustomerApi">
<wsdl:port name="CustomerApiSoap" binding="tns:CustomerApiSoap">
<soap:address location="http://localhost:8080/" />
</wsdl:port>
</wsdl:service>
</wsdl:definitions>
```

- 接下来，创建一个 `chap_07_simple_soap_server.php` 文件，该文件将执行 SOAP 服务器。首先定义 WSDL 和其他必要文件（在这种情况下，是一个数据库配置文件）的位置。如果设置了 `?wsdl` 参数，则提供 WSDL 而不是尝试处理请求。在本示例中，我们使用简单的 API 密钥来验证请求。然后，我们创建一个 SOAP 服务器实例，分配我们的 API 类实例，并运行 `handle()`：

```php
<?php
define('DB_CONFIG_FILE', '../config/db.config.php');
define('WSDL_FILENAME', __DIR__ . '/chap_07_wsdl.xml');

if (isset($_GET['wsdl'])) {
    readfile(WSDL_FILENAME);
    exit;
}

$apiKey = include __DIR__ . '/api_key.php';
require __DIR__ . '/../Application/Web/Soap/ProspectsApi.php';
require __DIR__ . '/../Application/Database/Connection.php';

use Application\Database\Connection;
use Application\Web\Soap\ProspectsApi;

$connection = new Application\Database\Connection(include __DIR__ . DB_CONFIG_FILE);
$api = new Application\Web\Soap\ProspectsApi($connection->pdo, [$apiKey]);
$server = new SoapServer(WSDL_FILENAME);
$server->setObject($api);
echo $server->handle();
```

![](img/39390f6d56c5a83b28db083a8bd5185c_275_0.png)

根据 `php.ini` 文件的设置，你可能需要禁用 WSDL 缓存，如下所示：
`ini_set('soap.wsdl_cache_enabled', 0);`

如果你在传入的 POST 数据方面遇到问题，可以调整此参数，如下所示：
`ini_set('always_populate_raw_post_data', -1);`

## 工作原理...

你可以通过首先创建目标 API 类，然后生成 WSDL 来轻松测试此食谱。之后，你可以使用内置的 PHP webserver 通过此命令提供 SOAP 服务：
`php -S localhost:8080 chap_07_simple_soap_server.php`

然后，你可以使用前面食谱中讨论的 SOAP 客户端发起调用以测试 SOAP 服务：

```php
define('WSDL_URL', 'http://localhost:8080?wsdl=1');
$clientKey = include __DIR__ . '/api_key.php';
try {
    $client = new SoapClient(WSDL_URL);
    $response = [];
    $email = some_email_generated_by_test;
    $email = 'test5393@unlikelysource.com';
    echo "\nGet Prospect Info for Email: " . $email . "\n";
    $request = ['token' => $clientKey, 'email' => $email];
    $result = $client->get($request, $response);
    var_dump($result);
} catch (SoapFault $e) {
    echo 'ERROR' . PHP_EOL;
    echo $e->getMessage() . PHP_EOL;
} catch (Throwable $e) {
    echo 'ERROR' . PHP_EOL;
    echo $e->getMessage() . PHP_EOL;
} finally {
    echo $client->__getLastResponse() . PHP_EOL;
}
```

这是电子邮件地址 `test5393@unlikelysource.com` 的输出：

![](img/39390f6d56c5a83b28db083a8bd5185c_276_0.png)

## 参见

只需简单地在 Google 上搜索 PHP 的 WSDL 生成器，就能找到十几个结果。用于生成 `ProspectsApi` 类 WSDL 的那个工具是基于 `https://code.google.com/archive/p/php-wsdl-creator/` 的。有关 `phpDocumentor` 的更多信息，请参考 `https://www.phpdoc.org/` 页面。

# 8 处理日期/时间和国际化方面

在本章中，我们将涵盖以下主题：

- 在视图脚本中使用表情符号或 emoji
- 转换复杂字符
- 从浏览器数据获取语言环境（locale）
- 按语言环境格式化数字
- 按语言环境处理货币
- 按语言环境格式化日期/时间
- 创建 HTML 国际日历生成器
- 构建重复事件生成器
- 不使用 gettext 处理翻译

## 引言

我们将以两个利用 **PHP 7** 中引入的新 **Unicode** 转义语法的食谱开始本章。之后，我们将介绍如何从浏览器数据确定 web 访问者的 **语言环境（locale）**。接下来的几个食谱将介绍创建一个语言环境类，这将允许你以特定于语言环境的形式表示数字、货币、日期和时间。最后，我们将涵盖展示如何生成国际化日历、处理重复事件以及在不使用 `gettext` 的情况下执行翻译的食谱。




## 在视图脚本中使用表情符号或 Emoji

单词 **表情符号（emoticons）** 是 *情绪（emotion）* 和 *图标（icon）* 的组合词。**Emoji** 起源于日本，是另一个更大、被广泛使用的图标集合。这些图标就是那些在具有社交网络功能的网站上非常流行的小笑脸、微型忍者和“笑到在地上打滚”的图标。然而，在 PHP 7 之前，生成这些小东西简直是一项令人沮丧的练习。

### 如何操作...

1.  首先，你需要知道你想要显示的图标的 Unicode 编码。在互联网上快速搜索一下，你就会找到几个出色的对照图表。
    以下是 *止语（hear-no-evil）*、*不看（see-no-evil）* 和 *勿言（speak-no-evil）* 三个猴子图标的编码：

    U+1F648、U+1F649 和 U+1F64A

![](img/39390f6d56c5a83b28db083a8bd5185c_280_0.png)

2.  输出到浏览器的任何 Unicode 内容都必须被正确标识。这通常通过 meta 标签来实现。你应该将字符集设置为 UTF-8。以下是一个示例：

    ```html
    <head>
        <title>PHP 7 Cookbook</title>
        <meta http-equiv="content-type"
        content="text/html;charset=utf-8" />
    </head>
    ```

3.  传统的方法是使用 HTML 来显示图标。因此，你可以这样做：

    ```html
    <table>
        <tr>
            <td>&#x1F648;</td>
            <td>&#x1F649;</td>
            <td>&#x1F64A;</td>
        </tr>
    </table>
    ```

4.  从 PHP 7 开始，你可以使用以下语法构建完整的 Unicode 字符：`"\u{xxxx}"`。这里有一个示例，使用的是与前一点相同的三个图标：

    ```php
    <table>
        <tr>
            <td><?php echo "\u{1F648}"; ?> </td>
            <td><?php echo "\u{1F649}"; ?> </td>
            <td><?php echo "\u{1F64A}"; ?> </td>
        </tr>
    </table>
    ```

![](img/39390f6d56c5a83b28db083a8bd5185c_281_0.png)

## 工作原理...

在 PHP 7 中，引入了一种新语法，允许你渲染任何 Unicode 字符。与其他语言不同，新的 PHP 语法允许使用可变数量的十六进制数字。基本格式如下：

```php
"\u{xxxx}"
```

整个结构必须使用双引号（或使用 **heredoc**）。*xxxx* 可以是 2、4、6 位或更多位的十六进制数字组合。

创建一个名为 *chap_08_emoji_using_html.php* 的文件。确保包含 *meta* 标签，以指示浏览器正在使用 UTF-8 字符编码：

```html
<!DOCTYPE html>
<html>
    <head>
        <title>PHP 7 Cookbook</title>
        <meta http-equiv="Content-type"
            content="text/html;charset=utf-8" />
    </head>
```

接下来，设置一个基本的 HTML 表格，并显示一行表情符号/Emoji：

```html
<body>
    <table>
        <tr>
            <td>&#x1F648;</td>
            <td>&#x1F649;</td>
            <td>&#x1F64A;</td>
        </tr>
        <tr>
            <td><?php echo "\u{1F648}"; ?></td>
            <td><?php echo "\u{1F649}"; ?></td>
            <td><?php echo "\u{1F64A}"; ?></td>
        </tr>
    </table>
</body>
</html>
```

这是从 Firefox 中看到的输出结果：

![](img/39390f6d56c5a83b28db083a8bd5185c_282_0.png)

### 参见

- 要查看 Emoji 代码列表，请访问 `http://unicode.org/emoji/charts/full-emoji-list.html`

## 转换复杂字符

访问完整 Unicode 字符集的能力为渲染复杂字符开辟了诸多新的可能性，尤其是非 Latin-1 字母表中的字符。

### 如何操作...

1.  某些语言是从右向左阅读，而不是从左向右阅读。例子包括希伯来语和阿拉伯语。在本例中，我们将展示如何使用 U+202E Unicode 字符（从右向左覆盖）来显示反向文本。以下代码行会打印出 *txtet desreveR*：

    ```php
    echo "\u{202E}Reversed text";
    echo "\u{202D}"; // returns output to left-to-right
    ```

    完成时，别忘了调用从左向右覆盖字符 U+202D！

2.  另一个需要考虑的因素是使用组合字符。一个例子是 ñ（n 字母上方带有波浪线 -- 悬浮在上）。它用于诸如 *mañana*（西班牙语中的早晨或明天，视语境而定）等单词中。存在一种 *组合字符*，由 Unicode 编码 U+00F1 表示。以下是其使用示例，它输出 *mañana*：

    ```php
    echo "ma\u{00F1}ana"; // shows mañana
    ```

3.  然而，这可能会影响搜索可能性。想象一下，如果你的客户键盘上没有这个组合字符。如果他们输入 *man* 试图搜索 *mañana*，他们将无法找到结果。

4.  能够访问 *完整 Unicode* 集提供了其他可能性。你可以不使用 *组合* 字符，而是使用原始字母 n 和 Unicode *组合* 代码的组合，后者会在字母上方放置一个悬浮的波浪线。在这个 echo 命令中，输出结果与之前相同。只有单词的形成方式不同：

    ```php
    echo "man\u{0303}ana"; // also shows mañana
    ```

5.  对于重音符号也可以应用类似的方法。考虑法语单词 *élève*（学生）。你可以使用组合字符来渲染它，或者使用 *组合* 代码将重音符号悬浮在字母上方。考虑以下两个示例。两个示例产生相同的输出，但渲染方式不同。

    ```php
    echo "\u{00E9}\u{006C}\u{00E8}\ve";
    echo "e\u{0301}\u{006C}e\u{0300}ve";
    ```

## 工作原理...

创建一个名为 chap_08_control_and_combining_unicode.php 的文件。确保包含 meta 标签，以指示浏览器正在使用 UTF-8 字符编码：

```html
<!DOCTYPE html>
<html>
<head>
    <title>PHP 7 Cookbook</title>
    <meta http-equiv="content-type"
          content="text/html;charset=utf-8" />
</head>
```

接下来，设置基本的 PHP 和 HTML 以显示之前讨论的示例：

```html
<body>
<pre>
<?php
    echo "\u{202E}Reversed text"; // reversed
    //echo "\u{202D}"; // stops reverse
    echo "mañana"; // using pre-composed characters
    echo "ma\u{00F1}ana"; // pre-composed character
    echo "man\u{0303}ana"; // "n" with combining ~ character
                           (U+0303)
    echo "élève";
    echo "\u{00E9}l\u{00E8}ve"; // pre-composed characters
    echo "e\u{0301}le\u{0300}ve"; // e + combining characters
?>
</pre>
</body>
</html>
```

这是来自浏览器的输出结果：

![](img/39390f6d56c5a83b28db083a8bd5185c_284_0.png)

## 从浏览器数据获取区域设置

为了改善网站上的用户体验，以用户区域设置（locale）可接受的形式显示信息至关重要。**区域设置（Locale）** 是一个通用术语，用于指示世界上的某个地区。IT 社区已经努力通过由语言和地区代码组成的两部分标识来编码区域设置。但当某人访问你的网站时，你如何知道他们的区域设置？也许最有用的一种技术是检查 HTTP 语言头。

### 如何操作...

1.  为了封装区域设置功能，我们将假设有一个类，`Application\I18n\Locale`。我们将让该类继承一个现有的类，`Locale`，它是 PHP `Intl` 扩展的一部分。

    > 注意
    > **I18n** 是 **国际化（Internationalization）** 的常见缩写。（数一下字母的数量！）

    ```php
    namespace Application\I18n;
    use Locale as PhpLocale;
    class Locale extends PhpLocale
    {
        const FALLBACK_LOCALE = 'en';
        // some code
    }
    ```

2.  为了了解传入请求的样子，请使用 `phpinfo(INFO_VARIABLES)`。测试完成后请立即禁用此函数，因为它会向潜在的攻击者泄露过多信息：

    ```php
    <?php phpinfo(INFO_VARIABLES); ?>
    ```

3.  区域设置信息存储在 `$_SERVER['HTTP_ACCEPT_LANGUAGE']` 中。其值将采取以下通用形式：`ll-CC,r1;q=0.n, ll-CC,r1;q=0.n`，如下表所述：

    | 缩写 | 含义 |
    |---|---|
    | ll | 表示语言的双字符小写代码。 |
    | - | 在区域设置代码 ll-CC 中分隔语言和地区。 |
    | CC | 表示地区的双字符大写代码。 |
    | , | 分隔区域设置代码和回退 **根区域设置（root locale）** 代码（通常与语言代码相同）。 |
    | r1 | 表示建议根区域设置的双字符小写代码。 |
    | ; | 分隔区域设置信息和质量。如果缺失质量值，默认为 q=1（100%）概率；这是首选。 |
    | q | 质量。 |
    | 0.n | 0.00 到 1.0 之间的某个值。将此值乘以 100 即可得到该访问者实际上偏好此语言的百分比概率。 |

4.  列出的区域设置可能不止一个。例如，网站访问者的计算机上可能安装了多种语言。PHP Locale 类恰好有一个方法，`acceptFromHttp()`，它读取 `Accept-language` 头字符串并给我们所需的设置：

    ```php
    protected $localeCode;
    public function setLocaleCode($acceptLangHeader)
    {
        $this->localeCode =
            $this->acceptFromHttp($acceptLangHeader);
    }
    ```

5.  然后我们可以定义适当的获取器。`getAcceptLanguage()` 方法返回来自 `$_SERVER['HTTP_ACCEPT_LANGUAGE']` 的值：

    ```php
    public function getAcceptLanguage()
    {
        return $_SERVER['HTTP_ACCEPT_LANGUAGE'] ??
               self::FALLBACK_LOCALE;
    }
    public function getLocaleCode()
    {
        return $this->localeCode;
    }
    ```




6. 接下来，我们定义一个构造函数，允许我们“手动”设置区域设置。否则，区域设置信息将从浏览器中获取：
public function __construct($localeString = NULL)
{
if ($localeString) {
$this->setLocaleCode($localeString);
} else {
$this->setLocaleCode($this->getAcceptLanguage());
}
}

7. 现在来到重要的决策环节：如何处理这些信息！接下来的几个食谱将对此进行详细说明。

![](img/39390f6d56c5a83b28db083a8bd5185c_287_0.png)

尽管访客似乎接受一种或多种语言，但这并不意味着访客希望浏览的内容是其浏览器指定的语言/区域设置。因此，虽然你可以根据这些信息确定区域设置，但你还应为他们提供一个替代语言的静态列表。

## 工作原理...

在本示例中，让我们看三个例子：

- 从浏览器获取的信息
- 预置的区域设置 fr-FR
- 取自 RFC 2616 的字符串：da, en-gb;q=0.8, en;q=0.7

将步骤 1 到 6 的代码放入名为 Locale.php 的文件中，该文件位于 Application\I18n 文件夹内。

接着，创建一个名为 chap_08_getting_locale_from_browser.php 的文件，该文件设置自动加载并使用新类：

```php
<?php
require __DIR__ . '/../Application/Autoload/Loader.php';
Application\Autoload\Loader::init(__DIR__ . '/../');
use Application\I18n\Locale;
```

现在你可以定义一个包含三个测试区域设置字符串的数组：

```php
$locale = [NULL, 'fr-FR', 'da, en-gb;q=0.8, en;q=0.7'];
```

最后，遍历这三个区域设置字符串，创建新类的实例。输出 getLocaleCode() 返回的值，以查看做出了何种选择：

```php
echo '<table>';
foreach ($locale as $code) {
    $locale = new Locale($code);
    echo '<tr>
        <td>' . htmlspecialchars($code) . '</td>
        <td>' . $locale->getLocaleCode() . '</td>
    </tr>';
}
echo '</table>';
```

以下是结果（附带少量样式）：

![](img/39390f6d56c5a83b28db083a8bd5185c_288_0.png)

## 另请参阅

- 有关 PHP Locale 类的信息，请参阅 http://php.net/manual/en/class.locale.php
- 有关 Accept-Language 头的更多信息，请参阅 RFC 2616 的第 14.4 节： https://www.w3.org/Protocols/rfc2616/rfc2616-sec14.html

### 按区域设置格式化数字

数字表示方式可能因区域设置而异。举个简单的例子，在英国，数字三百八十兆...（注：原文为 "three million..."）即 3,080,512.92 会显示如下：

3,080,512.92.

然而在法国，同一个数字可能显示为：

3 080 512,92

### 如何操作...

在你能够以区域设置特定的方式表示数字之前，你需要确定区域设置。这可以通过使用上一个食谱中讨论的 Application\I18n\Locale 类来完成。区域设置可以手动设置，也可以从头部信息中获取。

- 接下来，我们将使用 NumberFormatter 类的 format() 方法，以区域设置特定的格式输出和解析数字。首先，我们添加一个属性，该属性将包含一个 NumberFormatter 类的实例：

```php
use NumberFormatter;
protected $numberFormatter;
```

我们最初的想法可能是考虑使用 PHP 函数 setlocale() 来生成根据区域设置格式化的数字。然而，这种遗留方法的问题是，所有内容都将基于此区域设置进行考虑。这可能会引入处理根据数据库规范存储的数据时的问题。setlocale() 的另一个问题是它基于过时的标准，包括 RFC 1766 和 ISO 639。最后，setlocale() 高度依赖操作系统的区域设置支持，这会使我们的代码缺乏可移植性。

- 通常，下一步将在构造函数中设置 $numberFormatter。但对于我们的 Application\I18n\Locale 类而言，这种方法的问题是会导致类结构头重脚轻，因为我们还需要进行货币和日期格式化。因此，我们添加一个 getter 方法，首先检查是否已经创建了 NumberFormatter 的实例。如果没有，则创建并返回一个实例。new NumberFormatter 的第一个参数是区域设置代码。第二个参数 NumberFormatter::DECIMAL 代表我们需要什么类型的格式化：

```php
public function getNumberFormatter()
{
    if (!$this->numberFormatter) {
        $this->numberFormatter =
            new NumberFormatter($this->getLocaleCode(),
                NumberFormatter::DECIMAL);
    }
    return $this->numberFormatter;
}
```

- 然后我们添加一个方法，给定任何数字，生成一个代表该数字按区域设置格式化后的字符串：

```php
public function formatNumber($number)
{
    return $this->getNumberFormatter()->format($number);
}
```

- 4. 接下来我们添加一个方法，用于根据区域设置解析数字，生成一个原生 PHP 数值。请注意，解析失败时结果可能不会返回 FALSE，这取决于服务器的 ICU 版本：

```php
public function parseNumber($string)
{
    $result = $this->getNumberFormatter()->parse($string);
    return ($result) ? $result : self::ERROR_UNABLE_TO_PARSE;
}
```

## 工作原理...

按照前面要点中的讨论，对 Application\I18n\Locale 类进行添加。然后你可以创建一个 chap_08_formatting_numbers.php 文件，该文件设置自动加载并使用此类：

```php
<?php
    require __DIR__ . '/../Application/Autoload/Loader.php';
    Application\Autoload\Loader::init(__DIR__ . '../');
    use Application\I18n\Locale;
```

对于这个示例，创建两个 Locale 实例，一个用于英国，另一个用于法国。你还可以指定一个大数用于测试：

```php
$localeFr = new Locale('fr_FR');
$localeUk = new Locale('en_GB');
$number   = 1234567.89;
?>
```

最后，你可以将 formatNumber() 和 parseNumber() 方法包裹在合适的 HTML 显示逻辑中并查看结果：

```html
<!DOCTYPE html>
<html>
<head>
  <title>PHP 7 Cookbook</title>
  <meta http-equiv="content-type"
    content="text/html;charset=utf-8" />
  <link rel="stylesheet" type="text/css"
    href="php7cookbook_html_table.css">
</head>
<body>
  <table>
    <tr>
      <th>Number</th>
      <td>1234567.89</td>
    </tr>
    <tr>
      <th>French Format</th>
      <td><?=$localeFr->formatNumber($number); ?></td>
    </tr>
    <tr>
      <th>UK Format</th>
      <td><?=$localeUk->formatNumber($number); ?></td>
    </tr>
    <tr>
      <th>UK Parse French Number: <?=$localeFr->formatNumber($number) ?></th>
      <td><?=$localeUk->parseNumber($localeFr->formatNumber($number)); ?></td>
    </tr>
    <tr>
      <th>UK Parse UK Number: <?=$localeUk->formatNumber($number) ?></th>
      <td><?=$localeUk->parseNumber($localeUk->formatNumber($number)); ?></td>
    </tr>
    <tr>
      <th>FR Parse FR Number: <?=$localeFr->formatNumber($number) ?></th>
      <td><?=$localeFr->parseNumber($localeFr->formatNumber($number)); ?></td>
    </tr>
    <tr>
      <th>FR Parse UK Number: <?=$localeUk->formatNumber($number) ?></th>
      <td><?=$localeFr->parseNumber($localeUk->formatNumber($number)); ?></td>
    </table>
  </body>
</html>
```

这是在浏览器中看到的结果：

![](img/39390f6d56c5a83b28db083a8bd5185c_292_0.png)

> 请注意，如果区域设置设置为 `fr_FR`，解析英国格式的数字时，不会返回正确的值。同样，当区域设置设置为 `en_GB` 时，解析法国格式的数字也不会返回正确的值。因此，你可能需要考虑在尝试解析数字之前添加验证检查。

## 另请参阅

- 有关 `setlocale()` 的使用及其滥用的更多信息，请参阅此页面：`http://php.net/manual/en/function.setlocale.php`。
- 关于为什么数字格式化在某些服务器上会产生错误而在其他服务器上不会，请参阅 **ICU (International Components for Unicode)** 版本的简要说明。参见此页面上的评论：`http://php.net/manual/en/numberformatter.parse.php`。有关 ICU 格式的更多信息，请参阅 `http://userguide.icu-project.org/formatparse`。

### 按区域设置处理货币

处理货币的技术与处理数字类似。我们甚至会使用同一个 `NumberFormatter` 类！然而，有一个主要区别，这是一个阻碍因素；为了正确格式化货币，你需要手头有货币代码。




## 如何做...

-   首要任务是让货币代码以某种格式可用。一种可能性是简单地将货币代码作为 `Application\I18n\Locale` 类的构造器参数添加：

```php
const FALLBACK_CURRENCY = 'GBP';
protected $currencyCode;
public function __construct($localeString = NULL,
    $currencyCode = NULL)
{
    // 将此添加到现有代码中：
    $this->currencyCode = $currencyCode ??
        self::FALLBACK_CURRENCY;
}
```

> 这种方法虽然显然稳固且可行，但往往落入所谓*折中措施或走捷径*的类别。这种方法还往往会消除全自动化，因为货币代码无法从 HTTP 头部获取。正如你从本书其他章节中可能意识到的那样，我们并不回避更复杂的解决方案，因此，俗话说，*系好安全带！*

-   我们首先需要建立某种查找机制，以便给定一个国家代码，就能获取其主要货币代码。为了说明这一点，我们将使用适配器（Adapter）软件设计模式。根据该模式，我们应该能够创建不同的类，这些类潜在地可以以完全不同的方式运行，但产生相同的结果。相应地，我们需要定义期望的结果。为此，我们引入了一个类，`Application\I18n\IsoCodes`。如你所见，该类具有所有相关属性，以及一种通用的构造器：

```php
namespace Application\I18n;
class IsoCodes
{
    public $name;
    public $iso2;
    public $iso3;
    public $iso_numeric;
    public $iso_3166;
    public $currency_name;
    public $currency_code;
    public $currency_number;
    public function __construct(array $data)
{
    $vars = get_object_vars($this);

    foreach ($vars as $key => $value) {
        $this->$key = $data[$key] ?? NULL;
    }
}
}
```

-   接下来我们定义一个接口，该接口包含我们执行*国家代码到货币代码*查找所需的方法。在这种情况下，我们引入了 `Application\I18n\IsoCodesInterface`：

```php
namespace Application\I18n;

interface IsoCodesInterface
{
    public function getCurrencyCodeFromIso2CountryCode($iso2)
    : IsoCodes;
}
```

-   现在我们要准备构建一个查找适配器类，我们将其命名为 `Application\I18n\IsoCodesDb`。它实现了上述接口，并接受一个 `Application\Database\Connection` 实例（参见*第 1 章，构建基础*），用于执行查找。构造器设置所需的信息，包括连接、查找表名称以及代表 ISO2 代码的列。接口要求的查找方法随后发出一个 SQL 语句并返回一个数组，该数组随后用于构建一个 `IsoCodes` 实例：

```php
namespace Application\I18n;

use PDO;
use Application\Database\Connection;

class IsoCodesDb implements IsoCodesInterface
{
    protected $isoTableName;
    protected $iso2FieldName;
    protected $connection;
    public function __construct(Connection $connection,
    $isoTableName, $iso2FieldName)
    {
        $this->connection = $connection;
        $this->isoTableName = $isoTableName;
        $this->iso2FieldName = $iso2FieldName;
    }
    public function getCurrencyCodeFromIso2CountryCode($iso2)
    : IsoCodes
    {
        $sql = sprintf('SELECT * FROM %s WHERE %s = ?',
        $this->isoTableName,
        $this->iso2FieldName);
        $stmt = $this->connection->pdo->prepare($sql);
        $stmt->execute([$iso2]);
        return new IsoCodes($stmt->fetch(PDO::FETCH_ASSOC));
    }
}
```

-   现在我们将注意力转回 `Application\I18n\Locale` 类。我们首先添加几个新的属性和类常量：

```php
const ERROR_UNABLE_TO_PARSE = 'ERROR: Unable to parse';
const FALLBACK_CURRENCY = 'GBP';

protected $currencyFormatter;
protected $currencyLookup;
protected $currencyCode;
```

-   我们添加了一个新方法，用于从区域设置字符串中检索国家代码。我们可以利用 `getRegion()` 方法，它来自 `PHP\Locale` 类（我们继承自该类）。以防万一需要，我们还添加了一个方法，`getCurrencyCode()`：

```php
public function getCountryCode()
{
    return $this->getRegion($this->getLocaleCode());
}

public function getCurrencyCode()
{
    return $this->currencyCode;
}
```

-   与数字格式化一样，我们定义了一个 `getCurrencyFormatter()`，就像之前定义 `getNumberFormatter()` 那样。注意，`$currencyFormatter` 是使用 `NumberFormatter` 定义的，但第二个参数不同：

```php
public function getCurrencyFormatter()
{
    if (!$this->currencyFormatter) {
        $this->currencyFormatter =
        new NumberFormatter($this->getLocaleCode(),
        NumberFormatter::CURRENCY);
    }
    return $this->currencyFormatter;
}
```

-   如果已定义查找类，则我们在类构造器中添加货币代码查找：

```php
public function __construct($localeString = NULL,
                IsoCodesInterface $currencyLookup = NULL)
{
    // 将此添加到现有代码中：
    $this->currencyLookup = $currencyLookup;
    if ($this->currencyLookup) {
        $this->currencyCode =
            $this->currencyLookup
                ->getCurrencyCodeFromIso2CountryCode($this
                ->getCountryCode())
                ->currency_code;
    } else {
        $this->currencyCode = self::FALLBACK_CURRENCY;
    }
}
```

-   然后添加相应的货币格式化和解析方法。注意，与解析数字不同，解析货币如果在解析操作不成功时会返回 FALSE：

```php
public function formatCurrency($currency)
{
    return $this->getCurrencyFormatter()
        ->formatCurrency($currency, $this->currencyCode);
}

public function parseCurrency($string)
{
    $result = $this->getCurrencyFormatter()
        ->parseCurrency($string, $this->currencyCode);
    return ($result) ? $result : self::ERROR_UNABLE_TO_PARSE;
}
```

## 它是如何工作的...

创建以下类，如前几个要点所述：

| 类 | 讨论的要点 |
| :--- | :--- |
| Application\I18n\IsoCodes | 3 |
| Application\I18n\IsoCodesInterface | 4 |
| Application\I18n\IsoCodesDb | 5 |

为了说明的目的，我们假设我们有一个已填充的 MySQL 数据库表 `iso_country_codes`，其结构如下：

```sql
CREATE TABLE `iso_country_codes` (
`name` varchar(128) NOT NULL,
`iso2` varchar(2) NOT NULL,
`iso3` varchar(3) NOT NULL,
`iso_numeric` int(11) NOT NULL AUTO_INCREMENT,
`iso_3166` varchar(32) NOT NULL,
`currency_name` varchar(32) DEFAULT NULL,
`currency_code` char(3) DEFAULT NULL,
`currency_number` int(4) DEFAULT NULL,
PRIMARY KEY (`iso_numeric`)
) ENGINE=InnoDB AUTO_INCREMENT=895 DEFAULT CHARSET=utf8;
```

按照之前要点 6 到 9 的讨论，对 `Application\I18n\Locale` 类进行添加。然后你可以创建一个 `chap_08_formatting_currency.php` 文件，该文件设置自动加载并使用适当的类：

```php
<?php
define('DB_CONFIG_FILE', __DIR__ . '/../config/db_config.php');
require __DIR__ . '/../Application/Autoload/Loader.php';
Application\Autoload\Loader::init(__DIR__ . '../');
use Application\I18n\Locale;
use Application\I18n\IsoCodesDb;
use Application\Database\Connection;
```

接下来，我们创建 `Connection` 和 `IsoCodesDb` 类的实例：

```php
$connection = new Connection(include DB_CONFIG_FILE);
$isoLookup = new IsoCodesDb($connection,
'iso_country_codes', 'iso2');
```

为了说明，创建两个 `Locale` 实例，一个用于英国，另一个用于法国。你还可以指定一个大数值用于测试：

```php
$localeFr = new Locale('fr-FR', $isoLookup);
$localeUk = new Locale('en_GB', $isoLookup);
$number = 1234567.89;
?>
```

最后，你可以将 `formatCurrency()` 和 `parseCurrency()` 方法包裹在适当的 HTML 显示逻辑中，并查看结果。你的视图逻辑应基于前一个配方*它是如何工作的...*部分中展示的内容（此处不再重复以节省纸张！）。以下是最终输出：

![](img/39390f6d56c5a83b28db083a8bd5185c_298_0.png)

## 另见

-   最新的货币代码列表由**ISO（国际标准化组织）**维护。你可以以**XML**或**XLS**（即**Microsoft Excel**电子表格格式）获取此列表。这里是可以找到这些列表的页面：http://www.currency-iso.org/en/home/tables/table-al.html。

## 按区域设置格式化日期/时间

日期和时间的格式化因地区而异。作为一个经典例子，考虑年份**2016**，四月，15日，以及傍晚的时间。美国人首选的格式将是 7:23 PM, 4/15/2016，而在中国，你很可能看到 2016-04-15 19:23。正如在数字和货币格式化中提到的，以可接受的格式显示（并解析）日期对于你的网页访客也很重要。

## 如何做...

-   首先，我们需要修改 `Application\I18n\Locale`，添加使用日期格式化类的语句：
  ```php
  use IntlCalendar;
  use IntlDateFormatter;
  ```





## 处理日期/时间和国际方面

2. 接下来，我们添加一个属性来表示 `IntlDateFormatter` 实例，以及一系列预定义的常量：

```php
const DATE_TYPE_FULL = IntlDateFormatter::FULL;
const DATE_TYPE_LONG = IntlDateFormatter::LONG;
const DATE_TYPE_MEDIUM = IntlDateFormatter::MEDIUM;
const DATE_TYPE_SHORT = IntlDateFormatter::SHORT;

const ERROR_UNABLE_TO_PARSE = 'ERROR: Unable to parse';
const ERROR_UNABLE_TO_FORMAT = 'ERROR: Unable to format date';
const ERROR_ARGS_STRING_ARRAY = 'ERROR: Date must be string YYYY-mm-dd HH:ii:ss or array(y,m,d,h,i,s)';
const ERROR_CREATE_INTL_DATE_FMT = 'ERROR: Unable to create international date formatter';
```

```php
protected $dateFormatter;
```

3. 之后，我们就可以定义一个方法 `getDateFormatter()`，它返回一个 `IntlDateFormatter` 实例。`$type` 的值与之前定义的 `DATE_TYPE_` 常量之一相匹配：

```php
public function getDateFormatter($type)
{
    switch ($type) {
        case self::DATE_TYPE_SHORT :
            $dateFormatter = new IntlDateFormatter(
                $this->getLocaleCode(),
                IntlDateFormatter::SHORT,
                IntlDateFormatter::SHORT
            );
            break;
        case self::DATE_TYPE_MEDIUM :
            $dateFormatter = new IntlDateFormatter(
                $this->getLocaleCode(),
                IntlDateFormatter::MEDIUM,
                IntlDateFormatter::MEDIUM
            );
            break;
        case self::DATE_TYPE_LONG :
            $dateFormatter = new IntlDateFormatter(
                $this->getLocaleCode(),
                IntlDateFormatter::LONG,
                IntlDateFormatter::LONG
            );
            break;
        case self::DATE_TYPE_FULL :
            $dateFormatter = new IntlDateFormatter(
                $this->getLocaleCode(),
                IntlDateFormatter::FULL,
                IntlDateFormatter::FULL
            );
            break;
        default :
            throw new InvalidArgumentException(self::ERROR_CREATE_INTL_DATE_FMT);
    }
    $this->dateFormatter = $dateFormatter;
    return $this->dateFormatter;
}
```

4. 接下来我们定义一个生成区域格式化日期的方法。定义传入的 `$date` 的格式有点棘手。它不能是特定区域的，否则我们需要根据区域规则对其进行解析，结果是不可预测的。更好的策略是接受一个表示年、月、日等值的整数数组。作为后备方案，我们将接受字符串，但仅限于此格式：`YYYY-mm-dd HH:ii:ss`。时区是可选的，可以单独设置。首先我们初始化变量：

```php
public function formatDate($date, $type, $timeZone = NULL)
{
    $result = NULL;
    $year = date('Y');
    $month = date('m');
    $day = date('d');
    $hour = 0;
    $minutes = 0;
    $seconds = 0;
```

5. 然后我们生成一个分解表示年、月、日等值的值列表：

```php
if (is_string($date)) {
    list($dateParts, $timeParts) = explode(' ', $date);
    list($year, $month, $day) = explode('-', $dateParts);
    list($hour, $minutes, $seconds) = explode(':', $timeParts);
} elseif (is_array($date)) {
    list($year, $month, $day, $hour, $minutes, $seconds) = $date;
} else {
    throw new InvalidArgumentException(self::ERROR_ARGS_STRING_ARRAY);
}
```

6. 接下来我们创建一个 `IntlCalendar` 实例，它将在运行 `format()` 时作为参数使用。我们使用离散的整数值设置日期：

```php
$intDate = IntlCalendar::createInstance($timeZone, $this->getLocaleCode());
$intDate->set($year, $month, $day, $hour, $minutes, $seconds);
```

7. 最后，我们获取日期格式化器实例，并生成结果：

```php
$formatter = $this->getDateFormatter($type);
if ($timeZone) {
    $formatter->setTimeZone($timeZone);
}
$result = $formatter->format($intDate);
return $result ?? self::ERROR_UNABLE_TO_FORMAT;
```

8. `parseDate()` 方法实际上比格式化更简单。唯一的复杂之处在于如果未指定类型该怎么做（这将是可能的情况）。我们只需要循环遍历所有可能的类型（只有四种），直到产生结果：

```php
public function parseDate($string, $type = NULL)
{
    if ($type) {
        $result = $this->getDateFormatter($type)->parse($string);
    } else {
        $tryThese = [
            self::DATE_TYPE_FULL,
            self::DATE_TYPE_LONG,
            self::DATE_TYPE_MEDIUM,
            self::DATE_TYPE_SHORT
        ];
        foreach ($tryThese as $type) {
            $result = $this->getDateFormatter($type)->parse($string);
            if ($result) {
                break;
            }
        }
    }
    return ($result) ? $result : self::ERROR_UNABLE_TO_PARSE;
}
```

## 工作原理...

对之前讨论过的 `Application\I18n\Locale` 进行代码更改。然后你可以创建一个测试文件 `chap_08_formatting_date.php`，设置自动加载，并创建两个 `Locale` 类的实例，一个用于美国，另一个用于法国：

```php
<?php
require __DIR__ . '/../Application/Autoload/Loader.php';
Application\Autoload\Loader::init(__DIR__ . '/../');
use Application\I18n\Locale;

$localeFr = new Locale('fr-FR');
$localeUs = new Locale('en_US');
$date = '2016-02-29 17:23:58';
?>
```

接下来，使用合适的样式，运行 `formatDate()` 和 `parseDate()` 的测试：

```php
echo $localeFr->formatDate($date, Locale::DATE_TYPE_FULL);
echo $localeUs->formatDate($date, Locale::DATE_TYPE_MEDIUM);
$localeUs->parseDate($localeFr->formatDate($date, Locale::DATE_TYPE_MEDIUM));
// 等等
```

输出示例如下所示：

![](img/39390f6d56c5a83b28db083a8bd5185c_302_0.png)

## 另请参阅

- ISO 8601 对日期和时间的各个方面提供了精确定义。还有一个 RFC 讨论了 ISO 8601 对互联网的影响。作为参考，请见 `https://tools.ietf.org/html/rfc3339`。关于各国日期格式的良好概述，请见 `https://en.wikipedia.org/wiki/Date_format_by_country`。

## 创建一个 HTML 国际化日历生成器

编写一个程序来显示日历，很可能是你中学时代就会做的事情。一个嵌套的 `for()` 循环，其中内层循环生成七天的列表，通常就足够了。即使月份有多少天的问题也可以通过简单的数组轻松解决。开始变得棘手的是，当你需要弄清楚对于给定的年份，1 月 1 日是星期几。此外，如果你希望用特定区域可接受的语言和格式来表示月份和星期中的日子怎么办？正如你可能已经猜到的那样，我们将使用之前讨论过的 `Application\I18n\Locale` 类来构建一个解决方案。

### 操作方式...

1. 首先，我们需要创建一个通用类，用于保存单日的信息。最初，它只保存一个整数值 `$dayOfMonth`。稍后，在下一个食谱中，我们将扩展它以包含事件。由于该类的主要目的是产生 `$dayOfMonth`，我们将把这个值纳入其构造函数，并定义 `__invoke()` 也返回这个值：

```php
namespace Application\I18n;

class Day
{
    public $dayOfMonth;

    public function __construct($dayOfMonth)
    {
        $this->dayOfMonth = $dayOfMonth;
    }

    public function __invoke()
    {
        return $this->dayOfMonth ?? '';
    }
}
```

2. 创建一个新类，其中将包含适当的日历生成方法。它将接受 `Application\I18n\Locale` 的实例，并定义一些类常量和属性。格式代码，例如 **EEEE** 和 **MMMM**，取自 ICU 日期格式：

```php
namespace Application\I18n;

use IntlCalendar;

class Calendar
{
    const DAY_1 = 'EEEE';     // T
    const DAY_2 = 'EEEEEE';   // Tu
    const DAY_3 = 'EEE';      // Tue
    const DAY_FULL = 'EEEE';  // Tuesday
    const MONTH_1 = 'MMMM';   // M
    const MONTH_3 = 'MMM';    // Mar
    const MONTH_FULL = 'MMMM'; // March
    const DEFAULT_ACROSS = 3;
    const HEIGHT_FULL = '150px';
    const HEIGHT_SMALL = '60px';

    protected $locale;
    protected $dateFormatter;
    protected $yearArray;
    protected $height;

    public function __construct(Locale $locale)
    {
        $this->locale = $locale;
    }

    // 其他方法在以下要点中讨论
}
```

3. 然后我们定义一个方法，从我们的区域类返回一个 `IntlDateFormatter` 实例。它存储在一个类属性中，因为它将被频繁使用：

```php
protected function getDateFormatter()
{
    if (!$this->dateFormatter) {
        $this->dateFormatter = $this->locale->getDateFormatter(Locale::DATE_TYPE_FULL);
    }
    return $this->dateFormatter;
}
```

4. 接下来我们定义一个核心方法 `buildMonthArray()`，它创建一个多维数组，其中外层键是年中的周，内层数组是代表星期几的七个元素。我们接受年份、月份和可选时区作为参数。注意，作为变量初始化的一部分，我们从月份中减去 1。这是因为 `IntlCalendar::set()` 方法期望月份为基于 0 的值，其中 0 代表一月，1 代表二月，依此类推：

```php
public function buildMonthArray($year, $month, $timeZone = NULL)
{
    $month -= 1; // IntlCalendar months are 0 based; Jan==0, Feb==1 and so on
    $day = 1;
    $first = TRUE;
    $value = 0;
    $monthArray = array();
}
```




5. 然后，我们创建一个 `IntlCalendar` 实例，并使用它来确定该月有多少天：
```
$cal = IntlCalendar::createInstance(
    $timeZone, $this->locale()->getLocaleCode());
$cal->set($year, $month, $day);
$maxDaysInMonth = $cal
    ->getActualMaximum(IntlCalendar::FIELD_DAY_OF_MONTH);
```

6. 之后，我们使用我们的 `IntlDateFormatter` 实例来确定该月 1 日对应星期几。然后，我们将模式设置为 `w`，这将随后为我们提供周数：
```
$formatter = $this->getDateFormatter();
$formatter->setPattern('e');
$firstDayIsWhatDow = $formatter->format($cal);
```

7. 现在，我们准备使用嵌套循环遍历该月的所有日期。外部的 `while()` 循环确保我们不会超出该月的结束日期。内部循环表示星期中的每一天。你会注意到，我们利用了 `IntlCalendar::get()`，它允许我们从广泛的预定义字段中检索值。此外，如果年度周数超过 52，我们还会将年度周数值调整为 0：
```
while ($day <= $maxDaysInMonth) {
    for ($dow = 1; $dow <= 7; $dow++) {
        $cal->set($year, $month, $day);
        $weekOfYear = $cal
            ->get(IntlCalendar::FIELD_WEEK_OF_YEAR);
        if ($weekOfYear > 52) $weekOfYear = 0;
```

8. 然后，我们检查 `$first` 数组是否仍然设置为 TRUE。如果是，我们开始向日度中添加日期数字。否则，数组值被设置为 `NULL`。然后，我们关闭所有未关闭的语句并返回数组。请注意，我们还需要确保内部循环不会超出该月的天数，因此在外部的 `else` 子句中有一个额外的 `if()` 语句。

> 请注意，我们没有仅仅存储月中日期的值，而是使用了新定义的 `Application\I18n\Day` 类。

```
if ($first) {
    if ($dow == $firstDayIsWhatDow) {
        $first = FALSE;
        $value = $day++;
    } else {
        $value = NULL;
    }
} else {
    if ($day <= $maxDaysInMonth) {
        $value = $day++;
    } else {
        $value = NULL;
    }
}
$monthArray[$weekOfYear][$dow] = new Day($value);
}
return $monthArray;
}
```

## 优化国际化输出

1. 首先，是一系列小型方法，从一个基于类型提取国际化格式化的日期开始。该类型决定了我们是提供日期的完整名称、缩写还是单个字母，且都适合该语言环境：

```
protected function getDay($type, $cal)
{
    $formatter = $this->getDateFormatter();
    $formatter->setPattern($type);
    return $formatter->format($cal);
}
```

2. 接下来，我们需要一个方法返回包含日期名称的 HTML 行，该方法调用新定义的 `getDay()` 方法。如前所述，类型决定了日期的显示方式：

```
protected function getWeekHeaderRow($type, $cal, $year, $month, $week)
{
    $output = '<tr>';
    $width = (int) (100/7);
    foreach ($week as $day) {
        $cal->set($year, $month, $day());
        $output .= '<th style="vertical-align:top;"'
                  . " width=" . $width . "%">"
                  . $this->getDay($type, $cal) . '</th>';
    }
    $output .= '</tr>' . PHP_EOL;
    return $output;
}
```

3. 之后，我们定义了一个非常简单的方法来返回一行周日期。请注意，我们利用 `Day::__invoke()`，通过 `$day()` 实现：

```
protected function getWeekDaysRow($week)
{
    $output = '<tr style="height: ' . $this->height . ';">';
    $width = (int) (100/7);
    foreach ($week as $day) {
        $output .= '<td style="vertical-align:top;'
                  . " width=" . $width . "%">"
                  . $day() . '</td>';
    }
    $output .= '</tr>' . PHP_EOL;
    return $output;
}
```

4. 最后，是一个将较小方法组合起来为单个月份生成日历的方法。首先我们构建月份数组，但仅在 `$yearArray` 尚不可用时才执行：

```
public function calendarForMonth($year,
                                  $month,
                                  $timeZone = NULL,
                                  $dayType = self::DAY_3,
                                  $monthType = self::MONTH_FULL,
                                  $monthArray = NULL)
{
    $first = 0;
    if (!$monthArray)
        $monthArray = $this->yearArray[$year][$month]
                     ?? $this->buildMonthArray($year, $month, $timeZone);
```

5. 月份需要递减 1，因为 `IntlCalendar` 的月份是从 0 开始的：`Jan = 0`，`Feb = 1`，以此类推。然后，我们使用时区（如果存在）和语言环境构建一个 `IntlCalendar` 实例。接下来，我们创建一个 `IntlDateFormatter` 实例，以根据语言环境检索月份名称和其他信息：

```
$month--;
$cal = IntlCalendar::createInstance(
        $timeZone, $this->locale->getLocaleCode());
$cal->set($year, $month, 1);
$formatter = $this->getDateFormatter();
$formatter->setPattern($monthType);
```

6. 然后，我们遍历月份数组，并调用刚刚提到的较小方法来构建最终输出：

```
$this->height = ($dayType == self::DAY_FULL)
                ? self::HEIGHT_FULL : self::HEIGHT_SMALL;
$html = '<h1>' . $formatter->format($cal) . '</h1>';
$header = '';
$body = '';
foreach ($monthArray as $weekNum => $week) {
    if ($first++ == 1) {
        $header .= $this->getWeekHeaderRow(
            $dayType, $cal, $year, $month, $week);
    }
    $body .= $this->getWeekDaysRow($dayType, $week);
}
$html .= '<table>' . $header . $body .
    '</table>'. PHP_EOL;
return $html;
```

7. 为了生成整年的日历，只需循环遍历 1 到 12 月即可。为了便于外部访问，我们首先定义一个方法来构建年数组：

```
public function buildYearArray($year, $timeZone = NULL)
{
    $this->yearArray = array();
    for ($month = 1; $month <= 12; $month++) {
        $this->yearArray[$year][$month] =
            $this->buildMonthArray($year, $month, $timeZone);
    }
    return $this->yearArray;
}

public function getYearArray()
{
    return $this->yearArray;
}
```

8. 为了生成某年的日历，我们定义一个方法 calendarForYear()。如果年数组尚未构建，我们调用 buildYearArray()。我们考虑希望横向显示多少个月份日历，然后调用 calendarForMonth()：

```
public function calendarForYear($year,
    $timeZone = NULL,
    $dayType = self::DAY_1,
    $monthType = self::MONTH_3,
    $across = self::DEFAULT_ACROSS)
{
    if (!$this->yearArray) $this->buildYearArray($year,
        $timeZone);
    $yMax = (int) (12 / $across);
    $width = (int) (100 / $across);
    $output = '<table>' . PHP_EOL;
    $month = 1;
    for ($y = 1; $y <= $yMax; $y++) {
        $output .= '<tr>';
        for ($x = 1; $x <= $across; $x++) {
            $output .= '<td style="vertical-align:top;'
                . ' width=' . $width . '">' 
                . $this->calendarForMonth($year, $month,
                    $timeZone, $dayType, $monthType,
                    $this->yearArray[$year][$month++]) . '</td>';
        }
        $output .= '</tr>' . PHP_EOL;
    }
    $output .= '</table>';
    return $output;
}
```

## 工作原理...

首先，请确保你构建了在之前的配方中定义的 Application\Ii8n\Locale 类。之后，在 Application\Ii8n 文件夹中创建一个新文件 Calendar.php，包含本配方中描述的所有方法。

接下来，定义一个调用程序 chap_08_html_calendar.php，该程序设置自动加载并创建 Locale 和 Calendar 实例。还要注意定义年份和月份：

```
<?php
require __DIR__ . '/../Application/Autoload/Loader.php';
Application\Autoload\Loader::init(__DIR__ . '/..');
use Application\Ii8n\Locale;
use Application\Ii8n\Calendar;

$localeFr = new Locale('fr_FR');
$localeUs = new Locale('en_US');
$localeTh = new Locale('th_TH');
$calendarFr = new Calendar($localeFr);
$calendarUs = new Calendar($localeUs);
$calendarTh = new Calendar($localeTh);
$year = 2016;
$month = 1;
?>
```




## 处理日期/时间以及国际化相关内容

之后，你可以开发适当的视图逻辑来显示不同的日历。例如，你可以包含参数以显示完整的月份和星期名称：

```html
<!DOCTYPE html>
<html>
<head>
<title>PHP 7 Cookbook</title>
<meta http-equiv="content-type" content="text/html;charset=utf-8" />
<link rel="stylesheet" type="text/css" href="php7cookbook_html_table.css">
</head>
<body>
<h3>Year: <?= $year ?></h3>
<?= $calendarFr->calendarForMonth($year, $month, NULL, Calendar::DAY_FULL); ?>
<?= $calendarUs->calendarForMonth($year, $month, NULL, Calendar::DAY_FULL); ?>
<?= $calendarTh->calendarForMonth($year, $month, NULL, Calendar::DAY_FULL); ?>
</body>
</html>
```

![](img/39390f6d56c5a83b28db083a8bd5185c_310_0.png)

经过少量修改，你还可以显示整个年份的日历：

```php
$localeTh = new Locale('th_TH');
$localeEs = new Locale('es_ES');
$calendarTh = new Calendar($localeTh);
$calendarEs = new Calendar($localeEs);
$year = 2016;
echo $calendarTh->calendarForYear($year);
echo $calendarEs->calendarForYear($year);
```

以下是浏览器输出的西班牙语全年日历示例：

![](img/39390f6d56c5a83b28db083a8bd5185c_311_0.png)

### 另见

- 有关 `IntlDateFormatter::setPattern()` 中使用的代码的更多信息，请参阅本文：`http://userguide.icu-project.org/formatparse/datetime`

## 构建循环事件生成器

与生成日历相关的常见需求之一是事件的调度。事件可以是单日发生的单一事件，也可以是周末事件。然而，跟踪*循环*事件的需求要大得多。我们需要考虑开始日期、循环间隔（每日、每周、每月）以及发生次数或特定的结束日期。

### 操作步骤...

- 1. 首先，创建一个表示事件的类是一个绝佳的主意。最终你很可能需要将此类中的数据存储在数据库中。但为了说明，我们将简单地定义该类，并将数据库方面留待你的想象。你会注意到，我们将使用 `DateTime` 扩展中包含的一系列非常适合事件生成的类：

  ```php
  namespace Application\Libn;

  use DateTime;
  use DatePeriod;
  use DateInterval;
  use InvalidArgumentException;

  class Event
  {
      // code
  }
  ```

- 2. 接下来，我们定义一系列有用的类常量和属性。你会注意到，为了减少所需的 getter 和 setter 数量，我们将大多数属性定义为 public。间隔被定义为 `sprintf()` 格式字符串；`%d` 将被替换为某个值：

  ```php
  const INTERVAL_DAY = 'P%dD';
  const INTERVAL_WEEK = 'P%dW';
  const INTERVAL_MONTH = 'P%dM';
  const FLAG_FIRST = 'FIRST';       // 1st of the month
  const ERROR_INVALID_END = 'Need to supply either # occurrences or an end date';
  const ERROR_INVALID_DATE = 'String i.e. YYYY-mm-dd or DateTime instance only';
  const ERROR_INVALID_INTERVAL = 'Interval must take the form "P\d+(D | W | M)"';

  public $id;
  public $flag;
  public $value;
  public $title;
  public $locale;
  public $interval;
  public $description;
  public $occurrences;
  public $nextDate;
  protected $endDate;
  protected $startDate;
  ```

- 3. 接下来，我们把注意力转向构造函数。我们需要收集并设置与事件相关的所有信息。变量名称不言自明。

  > $value 并不那么明显。此参数最终将被替换为间隔格式字符串中的值。例如，如果用户将 $interval 选为 INTERVAL_DAY，将 $value 选为 2，则生成的间隔字符串将是 P2D，这意味着每隔一天（或每第 2 天）。

  ```php
  public function __construct($title,
                           $description,
                           $startDate,
                           $interval,
                           $value,
                           $occurrences = NULL,
                           $endDate = NULL,
                           $flag = NULL)
  {
  ```

- 4. 然后我们初始化变量。注意，ID 是伪随机生成的，但最终可能成为数据库事件表中的主键。在这里我们使用 `md5()` 并非出于安全目的，而是为了快速生成哈希值，使 ID 具有一致的外观：

  ```php
  $this->id = md5($title . $interval . $value) . sprintf('%04d', rand(0,9999));
  $this->flag = $flag;
  $this->value = $value;
  $this->title = $title;
  $this->description = $description;
  $this->occurrences = $occurrences;
  ```

- 5. 如前所述，间隔参数是用于构建正确 `DateInterval` 实例的 `sprintf()` 模式：

  ```php
  try {
     $this->interval = new DateInterval(sprintf($interval, $value));
  } catch (Exception $e) {
     error_log($e->getMessage());
     throw new InvalidArgumentException(self::ERROR_INVALID_INTERVAL);
  }
  ```

- 6. 为了初始化 $startDate，我们调用 `stringOrDate()`。然后我们通过调用 `stringOrDate()` 或 `calcEndDateFromOccurrences()` 尝试生成 $endDate 的值。如果我们既没有结束日期也没有发生次数，就会抛出异常：

  ```php
  $this->startDate = $this->stringOrDate($startDate);
  if ($endDate) {
      $this->endDate = $this->stringOrDate($endDate);
  } elseif ($occurrences) {
      $this->endDate = $this->calcEndDateFromOccurrences();
  } else {
      throw new InvalidArgumentException(self::ERROR_INVALID_END);
  }
  $this->nextDate = $this->startDate;
  ```

- 7. `stringOrDate()` 方法由几行代码组成，用于检查日期变量的数据类型，并返回 `DateTime` 实例或 `NULL`：

  ```php
  protected function stringOrDate($date)
  {
      if ($date === NULL) {
          $newDate = NULL;
      } elseif ($date instanceof DateTime) {
          $newDate = $date;
      } elseif (is_string($date)) {
          $newDate = new DateTime($date);
      } else {
          throw new InvalidArgumentException(self::ERROR_INVALID_END);
      }
      return $newDate;
  }
  ```

- 8. 如果设置了 $occurrences，我们在构造函数中调用 `calcEndDateFromOccurrences()` 方法，以便知道该事件的结束日期。我们利用了 `DatePeriod` 类，它提供基于开始日期、`DateInterval` 和发生次数的迭代：

  ```php
  protected function calcEndDateFromOccurrences()
  {
      $endDate = new DateTime('now');
      $period = new DatePeriod(
          $this->startDate, $this->interval, $this->occurrences);
      foreach ($period as $date) {
          $endDate = $date;
      }
      return $endDate;
  }
  ```

- 9. 接下来我们放入一个 `__toString()` 魔术方法，它简单地回显事件的标题：

  ```php
  public function __toString()
  {
      return $this->title;
  }
  ```

- 10. 我们还需要为 `Event` 类定义的最后一个方法是 `getNextDate()`，它在生成日历时使用：

  ```php
  public function  getNextDate(DateTime $today)
  {
      if ($today > $this->endDate) {
          return FALSE;
      }
      $next = clone $today;
      $next->add($this->interval);
      return $next;
  }
  ```

- 11. 接下来，我们把注意力转向上一个食谱中描述的 `Application\I18n\Calendar` 类。经过一些小改动，我们准备好将新定义的 `Event` 类整合到日历中。首先，我们添加一个新属性 `$events` 和一个以数组形式添加事件的方法。我们使用 `Event::$id` 属性确保事件被合并而不是被覆盖：

  ```php
  protected $events = array();

  public function addEvent(Event $event)
  {
      $this->events[$event->id] = $event;
  }
  ```

- 12. 接下来，我们添加一个方法 `processEvents()`，它在构建年历时将 `Event` 实例添加到 `Day` 对象中。首先，我们检查是否存在任何事件，以及 `Day` 对象是否为 `NULL`。如你可能记得，月份的某一天通常不会落在该周的第一天，因此需要将 `Day` 对象的值设置为 `NULL`。我们当然不希望将事件添加到非有效日！然后我们调用 `Event::getNextDate()` 并查看日期是否匹配。如果匹配，我们将 `Event` 存储到 `Day::$events[]` 中，并设置 `Event` 对象的下一个日期：

  ```php
  protected function processEvents($dayObj, $cal)
  {
      if ($this->events && $dayObj()) {
          $calDateTime = $cal->toDateTime();
          foreach ($this->events as $id => $eventObj) {
              $next = $eventObj->getNextDate($eventObj->nextDate);
          }
      }
  }
  ```




if ($next) {  
    if ($callDateTime->format('Y-m-d') ==
        $eventObj->nextDate->format('Y-m-d')) {  
        $dayObj->events[$eventObj->id] = $eventObj;  
        $eventObj->nextDate = $next;  
    }
}
return $dayObj;

> 请注意，我们并没有直接比较这两个对象。原因有二：首先，一个是 DateTime 实例，另一个是 IntlCalendar 实例。其次，更具说服力的原因是，在获取 DateTime 实例时可能包含了小时、分钟和秒，从而导致这两个对象之间的实际值存在差异。

1. 现在，我们需要在 `buildMonthArray()` 方法中添加对 `processEvents()` 的调用，使其看起来像这样：

```php
while ($dow <= $maxDaysInMonth) {  
    for ($dow = 1; $dow <= 7; $dow++) {  
        // add this to the existing code:  
        $dayObj = $this->processEvents(new Day($value, $cal));  
        $monthArray[$weekOfYear][$dow] = $dayObj;  
    }
}
```

2. 最后，我们需要修改 `getWeekDaysRow()`，添加必要的代码，以便在方框内连同日期一起输出事件信息：

```php
protected function getWeekDaysRow($type, $week)  
{  
    $output = '<tr style="height:' . $this->height . ';">';  
    $width = (int) (100/7);  
    foreach ($week as $day) {  
        $events = '';  
        if ($day->events) {  
            foreach ($day->events as $single) {  
                $events .= '<br>' . $single->title;  
                if ($type == self::DAY_FULL) {  
                    $events .= '<br><i>' . $single->description . '</i>';  
                }
            }
        }
    }
    $output .= '<td style="vertical-align: top; width:' . $width . '%">'
. $day . $events . '</td>';
    $output .= '</tr>' . PHP_EOL;
    return $output;
}
```

## 工作原理...

要将事件绑定到日历，首先编写步骤 1 到 10 中描述的 `Application\I18n\Event` 类。接下来，按照步骤 11 到 14 的描述修改 `Application\I18n\Calendar`。然后，你可以创建一个测试脚本 `chap_08_recurring_events.php`，该脚本设置自动加载并创建 `Locale` 和 `Calendar` 实例。为了说明目的，可以使用 'es_ES' 作为区域设置：

```php
<?php
require __DIR__ . '/../Application/Autoload/Loader.php';
Application\Autoload\Loader::init(__DIR__ . '../..');
use Application\I18n\{ Locale, Calendar, Event };

try {
$year = 2016;
$localeEs = new Locale('es_ES');
$calendarEs = new Calendar($localeEs);
```

现在我们可以开始定义事件并将其添加到日历中。第一个示例添加了一个持续 3 天的事件，该事件从 2016 年 1 月 8 日开始：

```php
// add event: 3 days
$title = 'Conf';
$description = 'Special 3 day symposium on eco-waste';
$startDate = '2016-01-08';
$event = new Event($title, $description, $startDate,
Event::INTERVAL_DAY, 1, 2);
$calendarEs->addEvent($event);
```

这里是另一个示例，该事件在每月 1 日发生，直到 2017 年 9 月：

```php
$title = 'Pay Rent';
$description = 'Sent rent check to landlord';
$startDate = new DateTime('2016-02-01');
$event = new Event($title, $description, $startDate,
    Event::INTERVAL_MONTH, '2017-09-01', NULL, Event::FLAG_FIRST);
$calendarEs->addEvent($event);
```

然后，你可以按照需要添加示例性的每周、双周、每月等事件。然后，你可以关闭 try...catch 块，并生成适当的显示逻辑：

```php
} catch (Throwable $e) {
$message = $e->getMessage();
}
?>
<!DOCTYPE html>
<head>
<title>PHP 7 Cookbook</title>
<meta http-equiv="content-type" content="text/html;charset=utf-8" />
<link rel="stylesheet" type="text/css" href="php7cookbook_html_table.css">
</head>
<body>
<h3>Year: <?= $year ?></h3>
<?= $calendarEs->calendarForYear($year, 'Europe/Berlin',
  Calendar::DAY_3, Calendar::MONTH_FULL, 2); ?>
<?= $calendarEs->calendarForMonth($year, 1 , 'Europe/Berlin',
  Calendar::DAY_FULL); ?>
</body>
</html>
```

这里是显示该年份前几个月的输出结果：

![](img/39390f6d56c5a83b28db083a8bd5185c_319_0.png)

## 参见

- 有关可以与 `get()` 一起使用的 `IntlCalendar` 字段常量的更多信息，请参阅此页面：`http://php.net/manual/en/class.intlcalendar.php#intlcalendar.constants`

## 不使用 gettext 处理翻译

翻译使你的网站能够面向国际客户群体，是其中重要的一部分。实现方式之一是使用 PHP 的 `gettext` 函数，这些函数基于安装在本地服务器上的 **GNU** `gettext` 操作系统工具。`gettext` 文档完善且支持良好，但它使用了一种过时的方法，并且存在明显的缺点。因此，在本示例中，我们提出了一种替代的翻译方法，你可以据此构建自己的 *适配器*。

需要认识到的一件重要的事情是，PHP 可用的编程翻译工具主要旨在提供对称为 `msgid`（**消息 ID**）的单词或短语的有限翻译。翻译后的等价物称为 `msgstr`（**消息字符串**）。因此，整合翻译通常仅涉及相对不变的项目，例如菜单、表单、错误或成功消息等。就本示例而言，我们将假设你将实际的网页翻译存储为文本块。

> 如果你需要翻译整页内容，可以考虑使用 Google 翻译 API。不过，这是一项付费服务。或者，你可以使用 Amazon Mechanical Turk 以低廉的价格将翻译外包给具有多语言技能的个人。有关 URL，请参阅本示例末尾的“参见”部分。

## 如何操作...

1. 我们将再次使用适配器软件设计模式，在这种情况下，用于提供翻译源的替代方案。在本示例中，我们将演示用于 `.ini` 文件、`.csv` 文件和数据库的适配器。
2. 首先，我们将定义一个接口，稍后用于标识翻译适配器。翻译适配器的要求非常简单，我们只需要针对给定的消息 ID 返回一个消息字符串：

```php
namespace Application\I18n\Translate\Adapter;

interface TranslateAdapterInterface
{
  public function translate($msgid);
}
```

3. 接下来，我们定义一个与接口匹配的 trait。该 trait 将包含所需的实际代码。请注意，如果我们未能找到消息字符串，我们只是返回消息 ID：

```php
namespace Application\I18n\Translate\Adapter;

trait TranslateAdapterTrait
{
  protected $translation;
  public function translate($msgid)
  {
    return $this->translation[$msgid] ?? $msgid;
  }
}
```

4. 现在，我们准备好定义第一个适配器了。在本示例中，我们将使用以 .ini 文件作为翻译源的适配器开始。你首先会注意到，我们使用了之前定义的 trait。构造函数方法在不同适配器之间会有所不同。在这种情况下，我们使用 `parse_ini_file()` 生成一个键/值对数组，其中键是消息 ID。注意，我们使用 `$filePattern` 参数来替换区域设置，从而允许我们加载适当的翻译文件：

```php
namespace Application\I18n\Translate\Adapter;

use Exception;
use Application\I18n\Locale;

class Ini implements TranslateAdapterInterface
{
    use TranslateAdapterTrait;
    const ERROR_NOT_FOUND = 'Translation file not found';
    public function __construct(Locale $locale, $filePattern)
    {
        $translateFileName = sprintf($filePattern,
            $locale->getLocaleCode());
        if (!file_exists($translateFileName)) {
            error_log(self::ERROR_NOT_FOUND . ': ' . $translateFileName);
            throw new Exception(self::ERROR_NOT_FOUND);
        } else {
            $this->translation = parse_ini_file($translateFileName);
        }
    }
}
```

5. 下一个适配器 `Application\I18n\Translate\Adapter\Csv` 是相同的，只是我们打开翻译文件并使用 `fgetcsv()` 循环遍历以检索消息 ID / 消息字符串键值对。这里我们只显示构造函数的不同之处：

```php
public function __construct(Locale $locale, $filePattern)
{
    $translateFileName = sprintf($filePattern,
        $locale->getLocaleCode());
    if (!file_exists($translateFileName)) {
        error_log(self::ERROR_NOT_FOUND . ': ' . $translateFileName);
        throw new Exception(self::ERROR_NOT_FOUND);
    } else {
        $fileObj = new SplFileObject($translateFileName, 'r');
        while ($row = $fileObj->fgetcsv()) {
            $this->translation[$row[0]] = $row[1];
        }
    }
}
```





6. 这两个适配器的主要缺点在于，我们需要预加载整个翻译集。如果翻译数量庞大，这会给内存带来压力。此外，翻译文件还需要被打开和解析，这会拖慢性能。

7. 现在我们介绍第三个适配器，它执行数据库查找，从而避免了前两个适配器的问题。我们使用在开头发送到数据库的 PDO 预编译语句，且仅发送一次。然后，我们可以根据需要执行任意多次，将消息 ID 作为参数传入。您还会注意到，我们需要覆盖在 trait 中定义的 `translate()` 方法。最后，您可能已经注意到我们使用了 `PDOStatement::fetchColumn()`，因为我们只需要一个值：

```php
namespace Application\I18n\Translate\Adapter;

use Exception;
use Application\Database\Connection;
use Application\I18n\Locale;

class Database implements TranslateAdapterInterface
{
    use TranslateAdapterTrait;
    protected $connection;
    protected $statement;
    protected $defaultLocaleCode;
    public function __construct(Locale $locale,
                                Connection $connection,
                                $tableName)
    {
        $this->defaultLocaleCode = $locale->getLocaleCode();
        $this->connection = $connection;
        $sql = 'SELECT msgstr FROM ' . $tableName
            . ' WHERE localeCode = ? AND msgid = ?';
        $this->statement = $this->connection->pdo->prepare($sql);
    }
    public function translate($msgid, $localeCode = NULL)
    {
        if (!$localeCode) $localeCode = $this->defaultLocaleCode;
        $this->statement->execute([$localeCode, $msgid]);
        return $this->statement->fetchColumn();
    }
}
```

8. 我们现在准备定义核心的 Translation 类，该类与一个（或多个）适配器相关联。我们分配了一个类常量来表示默认区域设置，并为区域设置、适配器和文本文件模式（稍后解释）定义了属性：

```php
namespace Application\I18n\Translate;

use Application\I18n\Locale;
use Application\I18n\Translate\Adapter\TranslateAdapterInterface;

class Translation
{
    const DEFAULT_LOCALE_CODE = 'en_GB';
    protected $defaultLocaleCode;
    protected $adapter = array();
    protected $textFilePattern = array();

    public function __construct(TranslateAdapterInterface $adapter,
                           $defaultLocaleCode = NULL,
                           $textFilePattern = NULL)
    {
        if (!$defaultLocaleCode) {
            $this->defaultLocaleCode = self::DEFAULT_LOCALE_CODE;
        } else {
            $this->defaultLocaleCode = $defaultLocaleCode;
        }
        
        $this->adapter[$this->defaultLocaleCode] = $adapter;
        $this->textFilePattern[$this->defaultLocaleCode] = 
            $textFilePattern;
    }

    public function setAdapter($localeCode, TranslateAdapterInterface 
    $adapter)
    {
        $this->adapter[$localeCode] = $adapter;
    }

    public function setDefaultLocaleCode($localeCode)
    {
        $this->defaultLocaleCode = $localeCode;
    }

    public function setTextFilePattern($localeCode, $pattern)
    {
        $this->textFilePattern[$localeCode] = $pattern;
    }

    public function __invoke($msgId, $locale = NULL)
    {
        if ($locale === NULL) $locale = $this->defaultLocaleCode;
        return $this->adapter[$locale]->translate($msgId);
    }

    public function text($key, $localeCode = NULL)
    {
        if ($localeCode === NULL) $localeCode =
            $this->defaultLocaleCode;
        $contents = $key;
        if (isset($this->textFilePattern[$localeCode])) {
            $fn = sprintf($this->textFilePattern[$localeCode],
                $localeCode, $key);
            if (file_exists($fn)) {
                $contents = file_get_contents($fn);
            }
        }
        return $contents;
    }
}
```

## 它是如何工作的……

首先，您需要定义一个目录结构来存放翻译文件。为了便于说明，您可以创建一个目录 `./path/to/project/files/data/languages`。在这个目录结构下，创建代表不同区域设置的子目录。对于此说明，您可以使用这些：`de_DE`、`fr_FR`、`en_GB` 和 `es_ES`，分别代表德语、法语、英语和西班牙语。

接下来，您需要创建不同的翻译文件。例如，以下是一个西班牙语的代表性 `data/languages/es_ES/translation.ini` 文件：

```ini
Welcome=Bienvenido
About Us=Sobre Nosotros
Contact Us=Contáctenos
Find Us=Encuéntranos
click=clic para más información
```

同样，为了演示 CSV 适配器，将相同的内容创建一个 CSV 文件，`data/languages/es_ES/translation.csv`：

```csv
"Welcome","Bienvenido"
"About Us","Sobre Nosotros"
"Contact Us","Contáctenos"
"Find Us","Encontrarnos"
"click","clic para más información"
```

最后，创建一个名为 translation 的数据库表，并用相同的数据填充它。主要区别在于数据库表将包含三个字段：msgid、msgstr 和 locale_code：

```sql
CREATE TABLE `translation` (
`msgid` varchar(255) NOT NULL,
`msgstr` varchar(255) NOT NULL,
`locale_code` char(6) NOT NULL DEFAULT '',
PRIMARY KEY (`msgid`,`locale_code`)
) ENGINE=InnoDB DEFAULT CHARSET=latin1;
```

接下来，使用本配方中显示的代码，定义前面提到的类：

- Application\I18n\Translate\Adapter\TranslateAdapterInterface
- Application\I18n\Translate\Adapter\TranslateAdapterTrait
- Application\I18n\Translate\Adapter\Ini
- Application\I18n\Translate\Adapter\Csv
- Application\I18n\Translate\Adapter\Database
- Application\I18n\Translate\Translation

现在，您可以创建一个测试文件 `chap_08_translation_database.php` 来测试数据库翻译适配器。它应该实现自动加载，使用适当的类，并创建一个 Locale 和 Connection 实例。请注意，TEXT_FILE_PATTERN 常量是一个 `sprintf()` 模式，其中替换了区域设置代码和文件名：

```php
<?php
define('DB_CONFIG_FILE', '../config/db_config.php');
define('TEXT_FILE_PATTERN', __DIR__ . '../data/languages/%s/%s.txt');
require __DIR__ . '../Application/Autoload/Loader.php';
Application\Autoload\Loader::init(__DIR__ . '../');
use Application\I18n\Locale;
use Application\I18n\Translate { Translation, Adapter\Database };
use Application\Database\Connection;

$conn = new Connection(include __DIR__ . DB_CONFIG_FILE);
$locale = new Locale('fr_FR');

$adapter = new Database($locale, $conn, 'translation');
$translate = new Translation($adapter, $locale->getLocaleCode(), TEXT_FILE_PATTERN);
?>
```

## 处理日期/时间和国际方面

最后，创建使用 `$translate` 实例的显示逻辑：

```html
<!DOCTYPE html>
<head>
<title>PHP 7 Cookbook</title>
<meta http-equiv="Content-type" content="text/html;charset=utf-8" />
<link rel="stylesheet" type="text/css" href="php7cookbook_html_table.css">
</head>
<body>
<table>
<tr>
<th><h1 style="color:white;"><?= $translate('Welcome') ?></h1></th>
<td>
<div style="float:left;width:50%;vertical-align:middle;">
<h3 style="font-size:24pt;"><i>Some Company, Inc.</i></h3>
</div>
<div style="float:right;width:50%;">
<img src="jcartier-city.png" width="300px"/>
</div>
</td>
</tr>
<tr>
<th>
<ul>
<li><?= $translate('About Us') ?></li>
<li><?= $translate('Contact Us') ?></li>
<li><?= $translate('Find Us') ?></li>
</ul>
</th>
<td>
<p>
<?= $translate->text('main_page'); ?>
</p>
<p>
<a href="#" ><?= $translate('click') ?></a>
</p>
</td>
</tr>
</table>
</body>
</html>
```





然后你可以执行其他类似的测试，替换一个新的区域设置以获取不同的语言，或者使用另一个适配器来测试不同的数据源。以下是使用 `fr_PR` 区域设置和数据库翻译适配器时输出的示例：

![](img/39390f6d56c5a83b28db083a8bd5185c_327_0.png)

## 另请参阅

-   如需了解有关 Google 翻译 API 的更多信息，请参阅 `https://cloud.google.com/translate/v2/translating-text-with-rest`。
-   如需了解有关 Amazon Mechanical Turk 的更多信息，请参阅 `https://www.mturk.com/mturk/welcome`。如需了解有关 gettext 的更多信息，请参阅 `http://www.gnu.org/software/gettext/manual/gettext.html`。

# 第 9 章：开发中间件

在本章中，我们将涵盖以下主题：

-   使用中间件进行身份验证
-   使用中间件实现访问控制
-   使用缓存提高性能
-   实现路由
-   进行跨框架系统调用
-   使用中间件跨越语言

## 简介

在 IT 行业中，术语往往被发明，然后被使用和滥用。**中间件**（middleware）一词也不例外。可以说，该术语的首次使用源自于 **互联网工程任务组（IETF）**，时间是 2000 年。最初，该术语应用于任何在传输层（即 TCP/IP）和应用层之间运行的软件。近年来，特别是随着 **PHP 标准建议第 7 号（PSR-7）** 的接受，中间件，尤其是在 PHP 世界中，已被应用于 Web 客户端-服务器环境。

![](img/39390f6d56c5a83b28db083a8bd5185c_329_0.png)

本节的食谱将使用在 *附录，定义 PSR-7 类* 中定义的具体类。

## 使用中间件进行身份验证

中间件的一个非常重要用途是提供身份验证。大多数基于 Web 的应用程序需要能够通过用户名和密码验证访客的能力。通过在一个身份验证类中整合 PSR-7 标准，你将使其在各个方面都具有通用的实用性，可以说，它足够安全，可以在任何提供符合 PSR-7 标准的请求和响应对象的框架中使用。

### 如何操作...

1.  我们首先定义一个 `Application\Acl\AuthenticateInterface` 类。我们使用该接口来支持适配器（Adapter）软件设计模式，通过允许使用各种适配器来使我们的 `Authenticate` 类更具通用实用性，每个适配器都可以从不同的来源（例如，从文件、使用 OAuth2 等）获取身份验证。注意使用 PHP 7 定义返回值数据类型的能力：
    ```php
    namespace Application\Acl;

    use Psr\Http\Message\{ RequestInterface, ResponseInterface };
    interface AuthenticateInterface
    {
        public function login(RequestInterface $request) :
            ResponseInterface;
    }
    ```

![](img/39390f6d56c5a83b28db083a8bd5185c_330_0.png)

> 注意，通过定义一个需要符合 PSR-7 标准的请求并产生符合 PSR-7 标准的响应的方法，我们使此接口具有普遍适用性。

2.  接下来，我们定义实现接口所要求的 `login()` 方法的适配器。我们确保使用适当的类，并定义合适的常量和属性。构造函数使用在 *第 5 章，与数据库交互* 中定义的 `Application\Database\Connection`：
    ```php
    namespace Application\Acl;
    use PDO;

    use Application\Database\Connection;
    use Psr\Http\Message\{ RequestInterface, ResponseInterface };
    use Application\MiddleWare\{ Response, TextStream };
    class DbTable implements AuthenticateInterface
    {
        const ERROR_AUTH = 'ERROR: authentication error';
        protected $conn;
        protected $table;
        public function __construct(Connection $conn, $tableName)
        {
            $this->conn = $conn;
            $this->table = $tableName;
        }
    ```

3.  核心 `login()` 方法从请求对象中提取用户名和密码。然后我们执行直接的数据库查找。如果有匹配项，我们将用户信息存储在响应正文中，并进行 JSON 编码：
    ```php
    public function login(RequestInterface $request) :
    ResponseInterface
    {
        $code = 401;
        $info = FALSE;
        $body = new TextStream(self::ERROR_AUTH);
        $params = json_decode($request->getBody()->getContents());
        $response = new Response();
        $username = $params->username ?? FALSE;
        if ($username)
        {
            $sql = 'SELECT * FROM ' . $this->table
            . ' WHERE email = ?';
            $stmt = $this->conn->pdo->prepare($sql);
            $stmt->execute([$username]);
            $row = $stmt->fetch(PDO::FETCH_ASSOC);
            if ($row)
            {
                if (password_verify($params->password,
                $row['password']))
                {
                    unset($row['password']);
                    $body =
                    new TextStream(json_encode($row));
                    $response->withBody($body);
                    $code = 202;
                    $info = $row;
                }
            }
        }
        return $response->withBody($body)->withStatus($code);
    }
    ```

**最佳实践**

切勿以明文形式存储密码。当你需要进行密码匹配时，使用 `password_verify()`，它否定了重新生成密码哈希的需要。

4.  `Authenticate` 类是一个包装器，用于实现 `AuthenticateInterface` 的适配器类。相应地，构造函数接受一个适配器类作为参数，以及一个作为键的字符串，身份验证信息存储在 `$_SESSION` 中：
    ```php
    namespace Application\Acl;
    use Application\MiddleWare\ { Response, TextStream };
    use Psr\Http\Message\ { RequestInterface, ResponseInterface };
    class Authenticate
    {
        const ERROR_AUTH = 'ERROR: invalid token';
        const DEFAULT_KEY = 'auth';
        protected $adapter;
        protected $token;
        public function __construct(
        AuthenticationInterface $adapter, $key)
        {
            $this->key = $key;
            $this->adapter = $adapter;
        }
    ```

5.  此外，我们提供一个带有安全令牌的登录表单，这有助于防止 **跨站点请求伪造（CSRF）** 攻击：
    ```php
    public function getToken()
    {
        $this->token = bin2hex(random_bytes(16));
        $_SESSION['token'] = $this->token;
        return $this->token;
    }
    public function matchToken($token)
    {
        $sessToken = $_SESSION['token'] ?? date('Ymd');
        return ($token == $sessToken);
    }
    public function getLoginForm($action = NULL)
    {
        $action = ($action) ? 'action="' . $action . '" ' : '';
        $output = '<form method="post" ' . $action . '>';
        $output .= '<table><tr><th>Username</th><td>';
        $output .= '<input type="text" name="username" /></td>';
        $output .= '</tr><tr><th>Password</th><td>';
        $output .= '<input type="password" name="password" />';
        $output .= '</td></tr><tr><th>&nbsp;</th>';
        $output .= '<td><input type="submit" /></td>';
        $output .= '</tr></table>';
        $output .= '<input type="token" value="';
        $output .= $this->getToken() . '" />' ;
        $output .= '</form>';
        return $output;
    }
    ```

6.  最后，该类中的 `login()` 方法检查令牌是否有效。如果无效，则返回 400 响应。否则，调用适配器的 `login()` 方法：
    ```php
    public function login(
    RequestInterface $request) : ResponseInterface
    {
        $params = json_decode($request->getBody()->getContents());
        $token = $params->token ?? FALSE;
        if (!( $token && $this->matchToken( $token))) {
            $code = 400;
            $body = new TextStream(self::ERROR_AUTH);
            $response = new Response($code, $body);
        } else {
            $response = $this->adapter->login($request);
        }
        if ($response->getStatusCode() >= 200
        && $response->getStatusCode() < 300) {
            $_SESSION[$this->key] =
            json_decode($response->getBody()->getContents());
        } else {
            $_SESSION[$this->key] = NULL;
        }
        return $response;
    }
    ```

首先，务必遵循 *附录，定义 PSR-7 类* 中定义的食谱。然后，继续定义本食谱中介绍的类，如下表所示：

| 类 | 在这些步骤中讨论 |
| :--- | :--- |
| `Application\Acl\AuthenticateInterface` | 1 |
| `Application\Acl\DbTable` | 2 - 3 |
| `Application\Acl\Authenticate` | 4 - 6 |

然后你可以定义一个名为 `chap_09_middleware_authenticate.php` 的调用程序，它设置自动加载并使用适当的类：

```php
<?php
session_start();
define('DB_CONFIG_FILE', __DIR__ . '../../config/db.config.php');
define('DB_TABLE', 'customer_09');
define('SESSION_KEY', 'auth');
require __DIR__ . '/../Application/Autoload/Loader.php';
Application\Autoload\Loader::init(__DIR__ . '/..');

use Application\Database\Connection;
use Application\Acl\{ DbTable, Authenticate };
use Application\MiddleWare\{ ServerRequest, Request, Constants,
  TextStream };
```

现在你处于设置身份验证适配器和核心类的位置：

```php
$conn    = new Connection(include DB_CONFIG_FILE);
$dbAuth = new DbTable($conn, DB_TABLE);
$auth    = new Authenticate($dbAuth, SESSION_KEY);
```

务必初始化传入请求，并设置要发送到身份验证类的请求：

```php
$incoming = new ServerRequest();
$incoming->initialize();
$outbound = new Request();
```

检查传入类方法以查看它是否是 `POST`。如果是，则向身份验证类传递一个请求：

```php
if ($incoming->getMethod() == Constants::METHOD_POST) {
  $body = new TextStream(json_encode(
```





#### 代码片段

```php
$incoming -> getParsedBody() ;
$response = $auth ->login($outbound -> withBody($body)) ;
}
$action = $incoming -> getServerParams() [' PHP_SELF'] ;
?>
```

这个玩法逻辑如下：

```php
<? = $auth -> getLoginForm($action) ?>
```

以下是一次无效认证尝试的输出。请注意右侧的 401 状态码。在此示例中，你可以添加响应对象的 var_dump()：

![](img/39390f6d56c5a83b28db083a8bd5185c_335_0.png)

以下是成功的认证：

![](img/39390f6d56c5a83b28db083a8bd5185c_336_0.png)

# 参见

有关如何避免 CSRF 和其他攻击的指导，请参见第 12 章 *提升 Web 安全性*。

## 使用中间件实现访问控制

顾名思义，中间件位于一系列函数或方法调用的中间。因此，中间件非常适合担任“守门员”的任务。你可以轻松使用一个读取访问控制列表（ACL）并允许或拒绝访问序列中下一个函数或方法调用的中间件类来实现**访问控制列表 (ACL)** 机制。

# 如何操作...

- 该过程最困难的部分可能是确定要包含在 ACL 中的哪些因素。为了说明起见，假设我们的所有用户都被分配了级别和状态。在此示例中，级别定义如下：

    ```php
    'levels' => [0, 'BEG', 'INT', 'ADV']
    ```

- 状态可以表明他们在会员注册流程中进行了多远。例如，状态 0 可能表明他们已启动会员注册流程，但尚未确认。状态 1 可能表明他们的电子邮件地址已确认，但尚未支付月费，等等。

- 接下来，我们需要定义我们计划控制访问的资源。在这种情况下，我们将假设需要控制对该网站上一系列网页的访问。因此，我们需要定义此类资源的数组。在 ACL 中，我们可以引用键：

    ```php
    'pages' => [0 => 'sorry', 'logout' => 'logout',
               'login'  => 'auth',
               1 => 'page1', 2 => 'page2', 3 => 'page3',
               4 => 'page4', 5 => 'page5', 6 => 'page6',
               7 => 'page7', 8 => 'page8', 9 => 'page9']
    ```

- 最后，最重要的配置部分是根据级别和状态对页面进行分配。配置数组中使用的通用模板可能如下所示：

    ```php
    status => ['inherits' => <key>, 'pages' => [level =>
                [pages allowed], etc.]]
    ```

- 现在我们可以定义 Acl 类。与之前一样，我们使用几个类，并定义适用于访问控制的常量和属性：

    ```php
    namespace Application\Acl;

    use InvalidArgumentException;
    use Psr\Http\Message\RequestInterface;
    use Application\MiddleWare\{ Constants, Response, TextStream };

    class Acl
    {
        const DEFAULT_STATUS = '';
        const DEFAULT_LEVEL = 0;
        const DEFAULT_PAGE = 0;
        const ERROR_ACL = 'ERROR: authorization error';
        const ERROR_APP = 'ERROR: requested page not listed';
        const ERROR_DEF =
            'ERROR: must assign keys "levels", "pages" and "allowed"';
        protected $default;
        protected $levels;
        protected $pages;
        protected $allowed;
    ```

- 在 __construct() 方法中，我们将分配数组分解为 $pages（要控制的资源）、$levels 和 $allowed（实际的分配）。如果数组未包含这三个子组件之一，则会抛出异常：

    ```php
    public function __construct(array $assignments)
    {
        $this->default = $assignments['default']
                        ?? self::DEFAULT_PAGE;
        $this->pages   = $assignments['pages'] ?? FALSE;
        $this->levels  = $assignments['levels'] ?? FALSE;
        $this->allowed = $assignments['allowed'] ?? FALSE;
        if (!($this->pages && $this->levels && $this->allowed)) {
            throw new InvalidArgumentException(self::ERROR_DEF);
        }
    }
    ```

- 你可能已经注意到我们允许继承。在 $allowed 中，inherits 键可以设置为数组中的另一个键。如果是这样，我们需要将其值与当前检查的值合并。我们反向遍历 $allowed，每次循环时合并任何继承的值。顺便提一下，该方法还只隔离适用于特定状态和级别的规则：

    ```php
    protected function mergeInherited($status, $level)
    {
        $allowed = $this->allowed[$status]['pages'][$level]
                        ?? array();
        for ($x = $status; $x > 0; $x--) {
            $inherits = $this->allowed[$x]['inherits'];
            if ($inherits) {
                $subArray =
                    $this->allowed[$inherits]['pages'][$level]
                        ?? array();
                $allowed = array_merge($allowed, $subArray);
            }
        }
        return $allowed;
    }
    ```

- 在处理授权时，我们初始化几个变量，然后从原始请求 URI 中提取请求的页面。如果页面参数不存在，我们设置 400 代码：

    ```php
    public function isAuthorized(RequestInterface $request)
    {
        $code = 401;    // unauthorized
        $text['page'] = $this->pages[$this->default];
        $text['authorized'] = FALSE;
        $page = $request->getUri()->getQueryParams()['page']
        ?? FALSE;
        if ($page === FALSE) {
            $code = 400;    // bad request
        } else {
            $params = json_decode(
                $request->getBody()->getContents());
            $status = $params->status ?? self::DEFAULT_LEVEL;
            $level = $params->level ?? '*';
            $allowed = $this->mergeInherited($status, $level);
        }
        if (in_array($page, $allowed)) {
            $code = 200;    // OK
            $text['authorized'] = TRUE;
            $text['page'] = $this->pages[$page];
        } else {
            $code = 401;
        }
        $body = new TextStream(json_encode($text));
        return (new Response())->withStatus($code)
        ->withBody($body);
    }
    ```

    否则，我们解码请求正文内容，并获取状态和级别。然后我们处于可以调用 mergeInherited() 的位置，该方法返回此状态和级别可访问的页面数组。

    如果请求的页面在 $allowed 数组中，我们将状态代码设置为令人愉快的 200，并返回授权设置以及与请求的页面代码对应的网页。

    然后我们返回 JSON 编码的响应，这就完成了。

## 工作原理...

之后，你需要定义 `Application\Acl\Acl`，这在本文中进行了讨论。现在移动到 `/path/to/source/for/this/chapter` 文件夹并创建两个目录：`public` 和 `pages`。在 `pages` 中，创建一系列 **PHP** 文件，例如 `page1.php`、`page2.php` 等。以下是这些页面之一可能外观的示例：

```php
<?php // page1 ?>
<h1>Page 1</h1>
<hr>
<p>Lorem ipsum dolor sit amet, consectetur adipiscing elit. etc.</p>
```

你还可以定义一个 `menu.php` 页面，它可以包含在输出中：

```php
<?php // menu ?>
<a href="?page=1">Page 1</a>
<a href="?page=2">Page 2</a>
<a href="?page=3">Page 3</a>
// etc.
```

`logout.php` 页面应该销毁会话：

```php
<?php
$_SESSION['info'] = FALSE;
session_destroy();
?>
<a href="/">BACK</a>
```

`auth.php` 页面将显示登录界面（如上一个食谱中所述）：

```php
<?php echo $auth->getLoginForm($action) ?>
```

然后，你可以创建一个配置文件，根据级别和状态允许访问网页。为了说明起见，将其命名为 `chap_09_middleware_acl_config.php` 并返回一个可能如下所示的数组：

```php
<?php
$min = [0, 'logout'];
return [
    'default' => 0,     // default page
    'levels' => [0, 'BEG', 'INT', 'ADV'],
    'pages' => [0 => 'sorry',
                'logout' => 'logout',
                'login' => 'auth',
                1 => 'page1', 2 => 'page2', 3 => 'page3',
                4 => 'page4', 5 => 'page5', 6 => 'page6',




最后，在 public 文件夹中定义 `index.php`，用于设置自动加载，并最终调用 `Authenticate` 和 `Acl` 类。与其他食谱一样，定义配置文件，设置自动加载，并使用某些类。此外，不要忘记启动会话：

```php
<?php
session_start();
session_regenerate_id();
define('DB_CONFIG_FILE', __DIR__ . '/../../config/db.config.php');
define('DB_TABLE', 'customer_09');
define('PAGE_DIR', __DIR__ . '/..');
define('SESSION_KEY', 'auth');
require __DIR__ . '/../../Application/Autoload/Loader.php';
Application\Autoload\Loader::init(__DIR__ . '/..');
use Application\Database\Connection;
use Application\Acl\ { Authenticate, Acl };
use Application\MiddleWare\ { ServerRequest, Request, Constants,
TxtStream };
```

## 最佳实践

保护你的会话是一种最佳实践。保护会话的一种简单方法是使用 `session_regenerate_id()`，它会使现有的 PHP 会话标识符失效并生成一个新的。因此，如果攻击者通过非法手段获取了会话标识符，任何给定的会话标识符的有效时间窗口都将降至最低。

现在你可以引入 ACL 配置，并为 `Authenticate` 和 `Acl` 创建实例：

```php
$config = require __DIR__ . '/../chap_09_middleware_acl_config.php';
$acl    = new Acl($config);
$conn   = new Connection(include DB_CONFIG_FILE);
$dbAuth = new DbTable($conn, DB_TABLE);
$auth   = new Authenticate($dbAuth, SESSION_KEY);
```

接下来，定义传入和传出请求的实例：

```php
$incoming = new ServerRequest();
$incoming->initialize();
$outbound = new Request();
```

如果传入的请求方法是 post，则通过调用 `login()` 方法处理身份验证：

```php
if (strtolower($incoming->getMethod()) == Constants::METHOD_POST) {
    $body    = new TextStream(json_encode(
            $incoming->getParsedBody()));
    $response = $auth->login($outbound->withBody($body));
}
```

如果为身份验证定义的会话键已填充，则意味着用户已成功通过身份验证。如果没有，我们编写一个稍后调用的匿名函数，其中包含身份验证登录页面：

```php
$info = $_SESSION[SESSION_KEY] ?? FALSE;
if (!$info) {
    $execute = function () use ($auth) {
        include PAGE_DIR . '/auth.php';
    };
}
```

否则，你可以继续进行 ACL 检查。首先，你需要从原始查询中找出用户想要访问哪个网页，但是：

```php
} else {
    $query = $incoming->getServerParams()['QUERY_STRING'] ?? '';
```

然后你可以重新编程 `$outbound` 请求以包含此信息：

```php
$outbound->withBody(new TextStream(json_encode($info)));
$outbound->getUri()->withQuery($query);
```

接下来，你就能够检查授权，将传出请求作为参数提供：

```php
$response = $acl->isAuthorized($outbound);
```

然后你可以检查返回响应中的授权参数，并编写一个匿名函数，如果正常则包含返回页面参数，否则包含抱歉页面：

```php
$params     = json_decode($response->getBody()->getContents());
$isAllowed  = $params->authorized ?? FALSE;
if ($isAllowed) {
    $execute = function () use ($response, $params) {
        include PAGE_DIR .'/' . $params->page . '.php';
        echo '<pre>', var_dump($response), '</pre>';
        echo '<pre>', var_dump($_SESSION[SESSION_KEY]);
        echo '</pre>';
    };
} else {
    $execute = function () use ($response) {
        include PAGE_DIR .'/sorry.php';
        echo '<pre>', var_dump($response), '</pre>';
        echo '<pre>', var_dump($_SESSION[SESSION_KEY]);
        echo '</pre>';
    };
}
```

现在你只需要设置表单操作并将匿名函数包装在 HTML 中：

```php
$action = $incoming->getServerParams()['PHP_SELF'];
?>
<!DOCTYPE html>
<head>
	<title>PHP 7 Cookbook</title>
	<meta http-equiv="content-type" content="text/html;charset=utf-8" />
</head>
<body>
	<?php $execute() ; ?>
</body>
</html>
```

为了测试它，你可以使用内置的 PHP web 服务器，但你必须使用 `-t` 标志来指示文档根目录是 `public`：

```bash
cd /path/to/source/for/this/chapter
php -S localhost:8080 -t public
```

你可以从浏览器访问 `http://localhost:8080/` URL。

如果你尝试访问任何页面，你会被重定向回登录页面。根据配置，`status = 1` 且 `level = BEG` 的用户只能访问页面 1 并注销。如果你以该用户身份登录并尝试访问页面 2，输出如下：

![](img/39390f6d56c5a83b28db083a8bd5185c_344_0.png)

## 参见

此示例依赖 `$_SESSION` 作为用户登录后的唯一用户身份验证方式。关于如何保护 PHP 会话的优秀示例，请参见**第十二章，提升 web 安全性**，特别是名为*保护 PHP 会话*的食谱。

## 使用缓存提高性能

缓存软件设计模式是指存储生成耗时较长的结果。这可能表现为冗长的视图脚本或复杂的数据库查询。如果你希望改善网站访问者的用户体验，存储目标当然需要具有高性能。由于不同的安装环境会有不同的潜在存储目标，缓存机制也适合适配器模式。潜在存储目标的示例包括内存、数据库和文件系统。

## 如何实现...

1.  与本章节中的其他几个食谱一样，由于存在共享常量，我们定义了一个离散的 `Application\Cache\Constants` 类：
   ```php
   <?php
   namespace Application\Cache;

   class Constants
   {
       const DEFAULT_GROUP   = 'default';
       const DEFAULT_PREFIX  = 'CACHE_';
       const DEFAULT_SUFFIX  = '.cache';
       const ERROR_GET      = 'ERROR: unable to retrieve from cache';
       // 并非显示所有常量以节省空间
   }
   ```

2.  由于我们正在遵循适配器设计模式，接下来定义一个接口：
   ```php
   namespace Application\Cache;
   interface CacheAdapterInterface
   {
       public function hasKey($key);
       public function getFromCache($key, $group);
       public function saveToCache($key, $data, $group);
       public function removeByKey($key);
       public function removeByGroup($group);
   }
   ```

3.  现在，我们准备好定义第一个缓存适配器，在本例中，通过使用 MySQL 数据库。我们需要定义将持有列名以及预编译语句的属性：
   ```php
   namespace Application\Cache;
   use PDO;
   use Application\Database\Connection;
   ```

4.  构造函数允许我们提供键列名以及 `Application\Database\Connection` 实例和用于缓存的表名：
   ```php
   class Database implements CacheAdapterInterface
   {
   protected $sql;
   protected $connection;
   protected $table;
   protected $dataColumnName;
   protected $keyColumnName;
   protected $groupColumnName;
   protected $statementHasKey = NULL;
   protected $statementGetFromCache = NULL;
   protected $statementSaveToCache = NULL;
   protected $statementRemoveByKey = NULL;
   protected $statementRemoveByGroup = NULL;

   public function __construct(Connection $connection,
   $table,
   $idColumnName,
   $keyColumnName,
   $dataColumnName,
   $groupColumnName = Constants::DEFAULT_GROUP)
   {
       $this->connection = $connection;
       $this->setTable($table);
       $this->setIdColumnName($idColumnName);
       $this->setDataColumnName($dataColumnName);
       $this->setKeyColumnName($keyColumnName);
       $this->setGroupColumnName($groupColumnName);
   }
   ```

5.  接下来的几个方法准备预编译语句，并在我们访问数据库时调用。我们不显示所有方法，但提供足够的信息让你了解其思路：
   ```php
   public function prepareHasKey()
   {
       $sql = 'SELECT `' . $this->idColumnName . '`'
       . '`FROM ` . $this->table . '` '
       . '`WHERE `' . $this->keyColumnName . '` = :key ';
       $this->sql[__METHOD__] = $sql;
       $this->statementHasKey =
       $this->connection->pdo->prepare($sql);
   }
   public function prepareGetFromCache()
   ```




## 第9章

```php
$sql = 'SELECT `' . $this->dataColumnName . '`'
    . ' FROM `' . $this->table . '`'
    . ' WHERE `' . $this->keyColumnName . '` = :key'
    . ' AND `' . $this->groupColumnName . '` = :group';
$this->sql[_METHOD_] = $sql;
$this->statementGetFromCache =
    $this->connection->pdo->prepare($sql);
```

- 6. 现在我们定义一个方法，用于判断给定键的数据是否存在：

```php
public function hasKey($key)
{
    $result = 0;
    try {
        if (!$this->statementHasKey) $this->prepareHasKey();
        $this->statementHasKey->execute(['key' => $key]);
    } catch (Throwable $e) {
        error_log(__METHOD__ . ': ' . $e->getMessage());
        throw new Exception(Constants::ERROR_REMOVE_KEY);
    }
    return (int) $this->statementHasKey
        ->fetch(PDO::FETCH_ASSOC)[$this->idColumnName];
}
```

- 7. 核心方法是从缓存中读取和写入数据的方法。以下是从缓存中检索数据的方法。我们只需要执行预编译语句，该语句执行带有 WHERE 子句的 SELECT，其中包含键和组：

```php
public function getFromCache(
    $key, $group = Constants::DEFAULT_GROUP)
{
    try {
        if (!$this->statementGetFromCache)
            $this->prepareGetFromCache();
        $this->statementGetFromCache->execute(
            ['key' => $key, 'group' => $group]);
        while ($row = $this->statementGetFromCache
            ->fetch(PDO::FETCH_ASSOC)) {
            if ($row && count($row)) {
                yield unserialize($row[$this->dataColumnName]);
            }
        }
    } catch (Throwable $e) {
        error_log(__METHOD__ . ': ' . $e->getMessage());
        throw new Exception(Constants::ERROR_GET);
    }
}
```

- 8. 在写入缓存时，我们首先判断该缓存键是否存在条目。如果存在，我们执行 UPDATE；否则，我们执行 INSERT：

```php
public function saveToCache($key, $data,
$group = Constants::DEFAULT_GROUP)
{
    $id = $this->hasKey($key);
    $result = 0;
    try {
        if ($id) {
            if (!$this->statementUpdateCache)
                $this->prepareUpdateCache();
            $result = $this->statementUpdateCache
                ->execute(['key' => $key,
                'data' => serialize($data),
                'group' => $group,
                'id' => $id]);
        } else {
            if (!$this->statementSaveToCache)
                $this->prepareSaveToCache();
            $result = $this->statementSaveToCache
                ->execute(['key' => $key,
                'data' => serialize($data),
                'group' => $group]);
        }
    } catch (Throwable $e) {
        error_log(__METHOD__ . ': ' . $e->getMessage());
        throw new Exception(Constants::ERROR_SAVE);
    }
    return $result;
}
```

- 9. 然后我们定义两个方法，分别按键或按组删除缓存。按组删除提供了一种便捷的机制，适用于需要删除大量项目的情况：

```php
public function removeByKey($key)
{
    $result = 0;
    try {
        if (!$this->statementRemoveByKey)
            $this->prepareRemoveByKey();
        $result = $this->statementRemoveByKey->execute(
            ['key' => $key]);
    } catch (Throwable $e) {
        error_log(__METHOD__ . ': ' . $e->getMessage());
        throw new Exception(Constants::ERROR_REMOVE_KEY);
    }
    return $result;
}

public function removeByGroup($group)
{
    $result = 0;
    try {
        if (!$this->statementRemoveByGroup)
            $this->prepareRemoveByGroup();
        $result = $this->statementRemoveByGroup->execute(
            ['group' => $group]);
    } catch (Throwable $e) {
        error_log(__METHOD__ . ': ' . $e->getMessage());
        throw new Exception(Constants::ERROR_REMOVE_GROUP);
    }
    return $result;
}
```

- 10. 最后，我们为每个属性定义 getter 和 setter。此处未全部展示以节省空间：

```php
public function setTable($name)
{
    $this->table = $name;
}

public function getTable()
{
    return $this->table;
}
// 等等。
```

- 11. 文件系统缓存适配器定义了与之前相同的方法。请注意使用 md5()，并非出于安全目的，而是作为一种快速从键生成文本字符串的方式：

```php
namespace Application\Cache;
use RecursiveIteratorIterator;
use RecursiveDirectoryIterator;

class File implements CacheAdapterInterface
{
    protected $dir;
    protected $prefix;
    protected $suffix;

    public function __construct(
        $dir, $prefix = NULL, $suffix = NULL)
    {
        if (!file_exists($dir)) {
            error_log(__METHOD__ . ': ' . Constants::ERROR_DIR_NOT);
            throw new Exception(Constants::ERROR_DIR_NOT);
        }
        $this->dir = $dir;
        $this->prefix = $prefix ?? Constants::DEFAULT_PREFIX;
        $this->suffix = $suffix ?? Constants::DEFAULT_SUFFIX;
    }

    public function hasKey($key)
    {
        $action = function ($name, $md5Key, &$item) {
            if (strpos($name, $md5Key) !== FALSE) {
                $item ++;
            }
        };

        return $this->findKey($key, $action);
    }

    public function getFromCache($key,
                                $group = Constants::DEFAULT_GROUP)
    {
        $fn = $this->dir . '/' . $group . '/'
            . $this->prefix . md5($key) . $this->suffix;
        if (file_exists($fn)) {
            foreach (file($fn) as $line) { yield $line; }
        } else {
            return array();
        }
    }

    public function saveToCache(
        $key, $data, $group = Constants::DEFAULT_GROUP)
    {
        $baseDir = $this->dir . '/' . $group;
        if (!file_exists($baseDir)) mkdir($baseDir);
        $fn = $baseDir . '/' . $this->prefix . md5($key)
        . $this->suffix;
        return file_put_contents($fn, json_encode($data));
    }

    protected function findKey($key, callable $action)
    {
        $md5Key = md5($key);
        $iterator = new RecursiveIteratorIterator(
            new RecursiveDirectoryIterator($this->dir),
            RecursiveIteratorIterator::SELF_FIRST);
        $item = 0;
        foreach ($iterator as $name => $obj) {
            $action($name, $md5Key, $item);
        }
        return $item;
    }

    public function removeByKey($key)
    {
        $action = function ($name, $md5Key, &$item) {
            if (strpos($name, $md5Key) !== FALSE) {
                unlink($name);
                $item++;
            }
        };
        return $this->findKey($key, $action);
    }

    public function removeByGroup($group)
    {
        $removed = 0;
        $baseDir = $this->dir . '/' . $group;
        $pattern = $baseDir . '/' . $this->prefix . '*'
        . $this->suffix;
        foreach (glob($pattern) as $file) {
            unlink($file);
            $removed++;
        }
        return $removed;
    }
}
```

- 12. 现在我们可以展示核心缓存机制了。在构造函数中，我们接受一个实现了 CacheAdapterInterface 的类作为参数：

```php
namespace Application\Cache;
use Psr\Http\Message\RequestInterface;
use Application\Middleware\{ Request, Response, TextStream };

class Core
{
    public function __construct(CacheAdapterInterface $adapter)
    {
        $this->adapter = $adapter;
    }
```

- 13. 接下来是一系列包装方法，它们调用适配器中同名方法，但接受一个 Psr\Http\Message\RequestInterface 类作为参数，并返回一个 Psr\Http\Message\ResponseInterface 作为响应。我们从简单的方法开始：hasKey()。请注意如何从请求参数中提取键：

```php
public function hasKey(RequestInterface $request)
{
    $key = $request->getUri()->getQueryParams()['key'] ?? '';
    $result = $this->adapter->hasKey($key);
}
```

- 14. 要从缓存中检索信息，我们需要从请求对象中获取键和组参数，然后调用适配器中的同名方法。如果没有获得结果，我们设置 204 代码，表示请求成功但未产生内容。否则，我们设置 200（成功）代码，并遍历结果。所有内容随后被放入响应对象中并返回：

```php
public function getFromCache(RequestInterface $request)
{
    $text = array();
    $key = $request->getUri()->getQueryParams()['key'] ?? '';
    $group = $request->getUri()->getQueryParams()['group']
        ?? Constants::DEFAULT_GROUP;
    $results = $this->adapter->getFromCache($key, $group);
    if (!$results) {
        $code = 204;
    } else {
        $code = 200;
        foreach ($results as $line) $text[] = $line;
    }
}
```




15. 奇怪的是，写入缓存的操作几乎相同，区别在于结果被期望是一个数字（即受影响的行数）或一个布尔结果：

```php
public function saveToCache(RequestInterface $request)
{
    $text = array();
    $key = $request->getUri()->getQueryParams()['key'] ?? '';
    $group = $request->getUri()->getQueryParams()['group']
        ?? Constants::DEFAULT_GROUP;
    $data = $request->getBody()->getContents();
    $results = $this->adapter->saveToCache($key, $data, $group);
    if (!$results) {
        $code = 204;
    } else {
        $code = 200;
        $text[] = $results;
    }

    $body = new TextStream(json_encode($text));
    return (new Response())->withStatus($code)
        ->withBody($body);
}
```

16. 删除方法正如预期那样，彼此非常相似：

```php
public function removeByKey(RequestInterface $request)
{
    $text = array();
    $key = $request->getUri()->getQueryParams()['key'] ?? '';
    $results = $this->adapter->removeByKey($key);
    if (!$results) {
        $code = 204;
    } else {
        $code = 200;
        $text[] = $results;
    }
    $body = new TextStream(json_encode($text));
    return (new Response())->withStatus($code)
        ->withBody($body);
}

public function removeByGroup(RequestInterface $request)
{
    $text = array();
    $group = $request->getUri()->getQueryParams()['group']
            ?? Constants::DEFAULT_GROUP;
    $results = $this->adapter->removeByGroup($group);
    if (!$results) {
        $code = 204;
    } else {
        $code = 200;
        $text[] = $results;
    }
    $body = new TextStream(json_encode($text));
    return (new Response())->withStatus($code)
            ->withBody($body);
}
} // Core 类的结束大括号
```

## 工作原理...

为了演示 Acl 类的使用，你需要定义本配方中描述的类，汇总如下：

| 类 | 涉及步骤 |
| :--- | :--- |
| Application\Cache\Constants | 1 |
| Application\Cache\CacheAdapterInterface | 2 |
| Application\Cache\Database | 3 - 10 |
| Application\Cache\File | 11 |
| Application\Cache\Core | 12 - 16 |

接下来，定义一个测试程序，你可以将其命名为 `chap_09_middleware_cache_db.php`。在这个程序中，照例为必要的文件定义常量，设置自动加载，使用相应的类，哦……还要写一个生成素数的函数（此时你很可能正在重读最后这一小段。别担心，我们可以帮你！）：

```php
<?php
define('DB_CONFIG_FILE', __DIR__ . './../config/db.config.php');
define('DB_TABLE', 'cache');
define('CACHE_DIR', __DIR__ . '/cache');
define('MAX_NUM', 100000);

require __DIR__ . '/../Application/Autoload/Loader.php';
Application\Autoload\Loader::init(__DIR__ . './../');
use Application\Database\Connection;
use Application\Cache\{ Constants, Core, Database, File };
use Application\MiddleWare\{ Request, TextStream };
```

好吧，需要一个运行时间较长的函数，于是素数生成器登场！数字 1、2 和 3 被给定为素数。我们使用 PHP 7 的 `yield from` 语法来产生这三个数，然后直接跳到 5，并一直进行到请求的最大值：

```php
function generatePrimes($max)
{
    yield from [1,2,3];
    for ($x = 5; $x < $max; $x++)
    {
        if ($x & 1) {
            $prime = TRUE;
            for($i = 3; $i < $x; $i++) {
                if(($x % $i) === 0) {
                    $prime = FALSE;
                    break;
                }
            }
            if ($prime) yield $x;
        }
    }
}
```

然后你可以设置一个数据库缓存适配器实例，它作为核心类的参数：

```php
$conn    = new Connection(include DB_CONFIG_FILE);
$dbCache = new Database(
        $conn, DB_TABLE, 'id', 'key', 'data', 'group');
$core    = new Core($dbCache);
```

或者，如果你希望使用文件缓存适配器代替，这里是相应的代码：

```php
$fileCache = new File(CACHE_DIR);
$core      = new Core($fileCache);
```

如果你想清除缓存，以下是可能的做法：

```php
$uriString = '/?group=' . Constants::DEFAULT_GROUP;
$cacheRequest = new Request($uriString, 'get');
$response = $core->removeByGroup($cacheRequest);
```

## 开发中间件

你可以使用 `time()` 和 `microtime()` 来查看该脚本在有缓存和无缓存情况下的运行时间：

```php
$start = time() + microtime(TRUE);
echo "\nTime: " . $start;
```

接下来，生成一个缓存请求。状态码 200 表示你成功从缓存中获取了素数列表：

```php
$uriString = '/?key=Test1';
$cacheRequest = new Request($uriString, 'get');
$response = $core->getFromCache($cacheRequest);
$status   = $response->getStatusCode();
if ($status == 200) {
    $primes = json_decode($response->getBody()->getContents());
} else {
    $primes = array();
    foreach (generatePrimes(MAX_NUM) as $num) {
        $primes[] = $num;
    }
    $body = new TextStream(json_encode($primes));
    $response = $core->saveToCache(
        $cacheRequest->withBody($body)
    );
}
```

然后你可以检查结束时间，计算差值，并查看你的新素数列表：

```php
$time = time() + microtime(TRUE);
$diff = $time - $start;
echo "\nTime: $time";
echo "\nDifference: $diff";
var_dump($primes);
```

这是在值被存储到缓存之前预期的输出：

```
561, 97571, 97577, 97579, 97583, 97607, 97609, 97613, 97649, 97651, 97673, 97687, 97711, 9772
9, 97771, 97777, 97787, 97789, 97813, 97829, 97841, 97843, 97847, 97849, 97859, 97861, 97871,
97879, 97883, 97919, 97927, 97931, 97943, 97961, 97979, 97973, 97987, 98009, 98011, 98017, 98
041, 98047, 98057, 98081, 98101, 98123, 98129, 98143, 98179, 98207, 98213, 98221, 98227, 9825
1, 98257, 98269, 98297, 98299, 98317, 98321, 98323, 98327, 98347, 98369, 98377, 98387, 98389,
98407, 98411, 98419, 98429, 98443, 98453, 98459, 98467, 98473, 98479, 98491, 98507, 98519, 98
533, 98543, 98561, 98563, 98573, 98597, 98621, 98627, 98639, 98641, 98663, 98669, 98709, 9879
1, 98713, 98717, 98729, 98731, 98737, 98773, 98779, 98801, 98807, 98809, 98837, 98849, 98867,
98869, 98873, 98887, 98893, 98897, 98899, 98899, 98911, 98927, 98929, 98939, 98947, 98953, 98
963, 98981, 98993, 98999, 99013, 99017, 99023, 99041, 99053, 99079, 99083, 99089, 99103, 9910
9, 99119, 99131, 99133, 99137, 99139, 99149, 99173, 99181, 99191, 99223, 99233, 99241, 99251,
99257, 99259, 99277, 99289, 99317, 99347, 99349, 99367, 99371, 99377, 99391, 99397, 99401, 99
409, 99431, 99439, 99469, 99487, 99497, 99523, 99527, 99529, 99551, 99559, 99563, 99571, 9957
7, 99581, 99607, 99611, 99623, 99643, 99661, 99667, 99679, 99689, 99707, 99709, 99713, 99719,
99721, 99733, 99761, 99767, 99787, 99793, 99809, 99817, 99823, 99829, 99833, 99839, 99859, 99
871, 99877, 99881, 99901, 99907, 99923, 99929, 99961, 99971, 99989, 99991]"

Time: 2934730510.8487
Difference: 33.938917160034

--------------------------------

(program exited with code: 0)
Press return to continue
```

现在你可以再次运行相同的程序，这次从缓存中检索：

```
729, 97771, 97777, 97787, 97789, 97813, 97829, 97841, 97843, 97847, 97849, 97859, 97861, 9787
1, 97879, 97883, 97919, 97927, 97931, 97943, 97961, 97979, 97987, 98009, 98011, 98017,
98041, 98047, 98057, 98081, 98101, 98123, 98129, 98143, 98179, 98207, 98213, 98221, 98227, 98
251, 98257, 98269, 98297, 98299, 98317, 98321, 98323, 98327, 98347, 98369, 98377, 98387, 98389,
9, 98407, 98411, 98419, 98429, 98443, 98453, 98459, 98467, 98473, 98479, 98491, 98507, 98519,
98533, 98543, 98561, 98563, 98573, 98597, 98621, 98627, 98639, 98641, 98663, 98669, 98689, 98
711, 98713, 98717, 98729, 98731, 98737, 98773, 98779, 98801, 98807, 98809, 98837, 98849, 9886
7, 98869, 98873, 98887, 98893, 98897, 98899, 98899, 98911, 98927, 98929, 98939, 98947, 98953,
98963, 98981, 98993, 98999, 99013, 99017, 99023, 99041, 99053, 99079, 99083, 99089, 99103, 99
109, 99119, 99131, 99133, 99137, 99139, 99149, 99173, 99181, 99191, 99223, 99233, 99241, 9925
1, 99257, 99259, 99277, 99289, 99317, 99347, 99349, 99367, 99371, 99377, 99391, 99397, 99401,
99409, 99431, 99439, 99469, 99487, 99497, 99523, 99527, 99529, 99551, 99559, 99563, 99571, 99
577, 99581, 99607, 99611, 99623, 99643, 99661, 99667, 99679, 99689, 99707, 99709, 99713, 9971
9, 99721, 99733, 99761, 99767, 99787, 99793, 99809, 99817, 99823, 99829, 99833, 99839, 99859,
99871, 99877, 99881, 99901, 99907, 99923, 99929, 99961, 99971, 99989, 99991]

Time: 2934730718.9282
Difference: 0.00317278744506836

--------------------------------

(program exited with code: 0)
Press return to continue
```




考虑到我们这个小质数生成器并非世界上最高效的，且演示是在笔记本电脑上运行的，时间从 30 多秒缩短到了毫秒级。

## 更多内容...

另一种可能的缓存适配器可以围绕 **Alternate PHP Cache (APC)** 扩展中的命令构建。该扩展包含诸如 `apc_exists()`、`apc_store()`、`apc_fetch()` 和 `apc_clear_cache()` 等函数。这些函数非常适合我们的 `hasKey()`、`saveToCache()`、`getFromCache()` 和 `removeBy*()` 函数。

## 另请参阅

你可能需要考虑对之前描述的遵循 PSR-6 的缓存适配器类进行一些细微修改，PSR-6 是一个针对缓存的标准建议。然而，该标准的接受程度并不像 PSR-7 那样高，因此我们决定不在这份食谱中完全遵循该标准。有关 PSR-6 的更多信息，请参考 `http://www.php-fig.org/psr/psr-6/`。

## 实现路由

路由指的是接受用户友好的 URL，将 URL 分解为组成部分，然后确定应分发哪个类和方法的过程。这种实现的优势在于，你不仅可以使你的 URL 对 **搜索引擎优化 (SEO)** 友好，还可以创建包含正则表达式模式的规则，从而提取参数的值。

### 如何实现...

- 最流行的方法可能是利用支持 **URL 重写** 的 web 服务器。一个例子是配置为使用 `mod_rewrite` 的 Apache web 服务器。然后你定义重写规则，允许图形文件请求以及对 CSS 和 JavaScript 的请求原样通过。否则，请求将通过路由方法进行汇总。
- 另一种潜在的方法是简单地让你的 web 服务器虚拟主机定义指向一个特定的路由脚本，该脚本随后调用路由类，做出路由决策，并适当重定向。
- 首先要考虑的代码是如何定义路由配置。显而易见的答案是构造一个数组，其中每个键都指向一个正则表达式，URI 路径将与该正则表达式匹配，以及某种形式的操作。以下代码片段展示了此类配置的示例。在此示例中，我们定义了三个路由：home、page 和 default。default 应该放在最后，因为它将匹配之前未匹配的任何内容。操作的执行形式是一个匿名函数，如果发生路由匹配，该函数将被执行：

```php
$config = [
    'home' => [
        'uri' => '!^/$!',
        'exec' => function ($matches) {
            include PAGE_DIR . '/page0.php'; }
    ],
    'page' => [
        'uri' => '!^/(page)/(\d+)$!',
        'exec' => function ($matches) {
            include PAGE_DIR . '/page' . $matches[2] . '.php'; }
    ],
    Router::DEFAULT_MATCH => [
        'uri' => '!.+!',
        'exec' => function ($matches) {
            include PAGE_DIR . '/sorry.php'; }
    ],
];
```

- 接下来，我们定义我们的 Router 类。我们首先定义一些常量和属性，这些在检查和匹配路由的过程中将非常有用：

```php
namespace Application\Routing;
use InvalidArgumentException;
use Psr\Http\Message\ServerRequestInterface;
class Router
{
    const DEFAULT_MATCH = 'default';
    const ERROR_NO_DEF = 'ERROR: must supply a default match';
    protected $request;
    protected $requestUri;
    protected $uriParts;
    protected $docRoot;
    protected $config;
    protected $routeMatch;
```

- 构造函数接受一个符合 `ServerRequestInterface` 的类、文档根目录的路径以及前面提到的配置文件。注意，如果未提供默认配置，我们会抛出一个异常：

```php
public function __construct(ServerRequestInterface $request,
$docRoot, $config)
{
$this->config = $config;
$this->docRoot = $docRoot;
$this->request = $request;
$this->requestUri =
$request->getServerParams()['REQUEST_URI'];
$this->uriParts = explode('/', $this->requestUri);
if (!isset($config[self::DEFAULT_MATCH])) {
throw new InvalidArgumentException(
self::ERROR_NO_DEF);
}
}
```

- 接下来，我们有一系列 getter，允许我们检索原始请求、文档根目录和最终的路由匹配：

```php
public function getRequest()
{
return $this->request;
}
public function getDocRoot()
{
return $this->docRoot;
}
public function getRouteMatch()
{
return $this->routeMatch;
}
```

- `isFileOrDir()` 方法用于确定我们是否正在尝试匹配 CSS、JavaScript 或图形请求（以及其他可能性）：

```php
public function isFileOrDir()
{
$fn = $this->docRoot . '/' . $this->requestUri;
$fn = str_replace('//', '/', $fn);
if (file_exists($fn)) {
return $fn;
} else {
return '';
}
}
```

- 最后我们定义 `match()`，它遍历配置数组，并将 uri 参数通过 `preg_match()` 运行。如果匹配成功，配置键和由 `preg_match()` 填充的 `$matches` 数组将存储在 `$routeMatch` 中，并返回回调。如果没有匹配，则返回默认回调：

```php
public function match() 
{
    foreach ($this->config as $key => $route) {
        if (preg_match($route['uri'],
            $this->requestUri, $matches)) {
            $this->routeMatch['key'] = $key;
            $this->routeMatch['match'] = $matches;
            return $route['exec'];
        }
    }

    return $this->config[self::DEFAULT_MATCH]['exec'];
}
```

## 工作原理...

首先，更改目录到 `/path/to/source/for/this/chapter` 并创建一个名为 `routing` 的目录。接下来，定义一个文件 `index.php`，它设置自动加载并使用正确的类。你可以定义一个指向上一章食谱中创建的页面目录的常量 `PAGE_DIR`：

```php
<?php
    define('DOC_ROOT', __DIR__);
    define('PAGE_DIR', DOC_ROOT . '/../pages');

    require_once __DIR__ . '/../../Application/Autoload/Loader.php';
    Application\Autoload\Loader::init(__DIR__ . '/../..');
    use Application\MiddleWare\ServerRequest;
    use Application\Routing\Router;
```

接下来，添加在此食谱第 3 步中讨论的配置数组。注意，你可以在模式末尾添加 `()?` 以考虑可选的尾随斜杠。此外，对于 home 路由，你可以提供两个选项：`/` 或 `/home`：

```php
$config = [
    'home' => [
        'uri' => '!^(//home)$!?',
        'exec' => function ($matches) {
            include PAGE_DIR . '/page0.php';
        }
    ],
    'page' => [
        'uri' => '!^/(page)/(\\d+)/()/?$!'.
        'exec' => function ($matches) {
            include PAGE_DIR . '/page' . $matches[2] . '.php'; }
    ],
    Router::DEFAULT_MATCH => [
        'uri' => '!.*!'.
        'exec' => function ($matches) {
            include PAGE_DIR . '/sorry.php'; }
    ],
];
```

然后你可以定义一个路由器实例，将初始化后的 `ServerRequest` 实例作为第一个参数提供：

```php
$router = new Router((new ServerRequest())
    ->initialize(), DOC_ROOT, $config);
$execute = $router->match();
$params  = $router->getRouteMatch('match');
```

然后你需要检查请求是文件还是目录，以及路由匹配是否为 `/`：

```php
if ($fn = $router->isFileOrDir()
    && $router->getRequest()->getUri()->getPath() != '/') {
    return FALSE;
} else {
    include DOC_ROOT . '/main.php';
}
```

接下来，定义 `main.php`，内容如下所示：

```php
<?php // demo using middleware for routing ?>
<!DOCTYPE html>
<head>

    <title>PHP 7 Cookbook</title>
    <meta http-equiv="content-type"
          content="text/html; charset=utf-8" />
</head>
<body>
    <?php include PAGE_DIR . '/route_menu.php'; ?>
    <?php $execute($params); ?>
</body>
</html>
```





# 第 9 章

最后，还需要一个使用用户友好型路由的修订版菜单：

```php
<?php // menu for routing ?>
<a href="/home">Home</a>
<a href="/page/1">Page 1</a>
<a href="/page/2">Page 2</a>
<a href="/page/3">Page 3</a>
<!-- etc. -->
```

若要使用 Apache 测试该配置，请定义一个指向 /path/to/source/for/this/chapter/routing 的虚拟主机定义。此外，定义一个 `.htaccess` 文件，将任何不是文件、目录或链接的请求重定向到 index.php。或者，您也可以直接使用内置的 PHP Web 服务器。在终端窗口或命令提示符中，输入以下命令：

```bash
cd /path/to/source/for/this/chapter/routing
php -S localhost:8080
```

在浏览器中，请求 http://localhost:8080/home 时的输出大致如下：

![](img/39390f6d56c5a83b28db083a8bd5185c_363_0.png)

## 另请参阅

有关使用 NGINX Web 服务器进行重写的信息，请查看此文章： http://nginx.org/en/docs/http/nginx_rewrite_module.html。市面上有许多功能强大且比此处介绍的简单路由更复杂的 PHP 路由库。这些库包括 AltOrouter (http://alto router.com/)、TreeRoute (https://github.com/baryshev/TreeRoute)、FastRoute (https:// github.com/nikic/FastRoute) 以及 Aura.Router (https://github.com/auraphp/ Aura.Router)。此外，大多数框架（例如 Zend Framework 2 或 CodeIgniter）都有自己的路由功能。

## 进行跨框架系统调用

开发 PSR-7（以及中间件）的主要原因之一是对在框架之间进行调用的需求日益增长。值得注意的是，PSR-7 的主要文档由 PHP 框架互操作组（PHP-FIG）托管。

# 如何实现...

- 中间件跨框架调用的主要机制是创建一个驱动程序，该程序按顺序执行框架调用，并保持共同的请求和响应对象。请求和响应对象分别被期望表示 Psr\Http\Message\ServerRequestInterface 和 Psr\Http\Message\ResponseInterface。

- 为了便于说明，我们定义一个中间件会话验证器。常量和属性反映了会话指纹（session thumbnail），这是我们用来整合网站访问者 IP 地址、浏览器和语言设置等因素的术语：

```php
namespace Application\MiddleWare\Session;
use InvalidArgumentException;
use Psr\Http\Message\ {
    ServerRequestInterface, ResponseInterface
};
use Application\MiddleWare\ { Constants, Response, TextStream };
class Validator
{
    const KEY_TEXT = 'text';
    const KEY_SESSION = 'thumbrint';
    const KEY_STATUS_CODE = 'code';
    const KEY_STATUS_REASON = 'reason';
    const KEY_STOP_TIME = 'stop_time';
    const ERROR_TIME = 'ERROR: session has exceeded stop time';
    const ERROR_SESSION = 'ERROR: thumbprint does not match';
    const SUCCESS_SESSION = 'SUCCESS: session validates OK';
    protected $sessionKey;
    protected $currentPrint;
    protected $storedPrint;
    protected $currentTime;
    protected $storedTime;
```

- 构造函数接受一个 ServerRequestInterface 实例和会话作为参数。如果会话是一个数组（例如 $_SESSION），我们会将其包装在一个类中。这样做的目的是考虑到传入的可能是会话对象（例如 Joomla 中使用的 JSession）。然后，我们使用上述提到的因素创建指纹。如果存储的指纹不可用，我们假设这是第一次访问，并存储当前指纹以及停止时间（如果设置了该参数）。我们使用 md5()，因为它是一种快速的哈希算法，不对外暴露，因此适用于此应用：

```php
public function __construct(
    ServerRequestInterface $request, $stopTime = NULL)
{
    $this->currentTime    = time();
    $this->storedTime     = $_SESSION[self::KEY_STOP_TIME] ?? 0;
    $this->currentPrint =
        md5($request->getServerParams()['REMOTE_ADDR']
            . $request->getServerParams()['HTTP_USER_AGENT']
            . $request->getServerParams()['HTTP_ACCEPT_LANGUAGE']);
    $this->storedPrint = $_SESSION[self::KEY_SESSION]
        ?? NULL;
    if (empty($this->storedPrint)) {
        $this->storedPrint = $this->currentPrint;
        $_SESSION[self::KEY_SESSION] = $this->storedPrint;
        if ($stopTime) {
            $this->storedTime = $stopTime;
            $_SESSION[self::KEY_STOP_TIME] = $stopTime;
        }
    }
}
```

- 虽然定义 `__invoke()` 并不是必需的，但对于独立的中间件类来说，这个魔术方法非常方便。按照惯例，我们接受 `ServerRequestInterface` 和 `ResponseInterface` 实例作为参数。在此方法中，我们仅检查当前指纹是否与存储的指纹匹配。当然，第一次时会匹配。但在后续请求中，企图进行会话劫持的攻击者很可能会被发现。此外，如果会话时间超过了停止时间（如果设置了），同样会发送 401 代码：

```php
public function __invoke(
    ServerRequestInterface $request, Response $response)
{
    $code = 401; // unauthorized
    if ($this->currentPrint != $this->storedPrint) {
        $text[self::KEY_TEXT] = self::ERROR_SESSION;
        $text[self::KEY_STATUS_REASON] =
            Constants::STATUS_CODES[401];
    } elseif ($this->storedTime) {
        if ($this->currentTime > $this->storedTime) {
            $text[self::KEY_TEXT] = self::ERROR_TIME;
            $text[self::KEY_STATUS_REASON] =
                Constants::STATUS_CODES[401];
        } else {
            $code = 200; // success
        }
    }

    if ($code == 200) {
        $text[self::KEY_TEXT] = self::SUCCESS_SESSION;
        $text[self::KEY_STATUS_REASON] =
            Constants::STATUS_CODES[200];
    }

    $text[self::KEY_STATUS_CODE] = $code;
    $body = new TextStream(json_encode($text));
    return $response->withStatus($code)->withBody($body);
}
```

- 现在我们可以将新的中间件类投入使用。至少在这一阶段，跨框架调用的主要问题总结如下。相应地，我们如何实现中间件在很大程度上取决于最后一点：
    - 并非所有 PHP 框架都符合 PSR-7 标准
    - 现有的 PSR-7 实现并不完整
    - 所有框架都想当“老板”

- 例如，请查看 **Zend Expressive** 的配置文件，它是一个自称 PSR7 中间件微框架。这里是文件 `middleware-pipeline.global.php`，它位于标准 Expressive 应用程序的 `config/autoload` 文件夹中。`dependencies` 键用于识别将在管道中激活的中间件包装类：

```php
<?php
use Zend\Expressive\Container\ApplicationFactory;
use Zend\Expressive\Helper;
return [
    'dependencies' => [
        'factories' => [
            Helper\ServerUrlMiddleware::class =>
                Helper\ServerUrlMiddlewareFactory::class,
            Helper\UrlHelperMiddleware::class =>
                Helper\UrlHelperMiddlewareFactory::class,
            // insert your own class here
        ],
    ],
];
```

- 在 `middleware_pipeline` 键下，您可以识别将在路由过程发生之前或之后执行的类。可选参数包括 `path`、`error` 和 `priority`：

```php
'middleware_pipeline' => [
    'always' => [
        'middleware' => [
            Helper\ServerUrlMiddleware::class,
        ],
        'priority' => 10000,
    ],
    'routing' => [
        'middleware' => [
            ApplicationFactory::ROUTING_MIDDLEWARE,
            Helper\UrlHelperMiddleware::class,
            // insert reference to middleware here
            ApplicationFactory::DISPATCH_MIDDLEWARE,
        ],
        'priority' => 1,
    ],
    'error' => [
        'middleware' => [
            // Add error middleware here.
        ],
        'error'     => true,
    ],
];
```





## 工作原理...

首先，创建步骤 2-5 中描述的 `Application\MiddleWare\Session\Validator` 测试中间件类。然后你需要前往 <https://getcomposer.org/> 并按照说明获取 Composer。将其下载到 `/path/to/source/for/this/chapter` 文件夹中。接下来，构建一个基础的 Zend Expressive 应用程序，如下所示。请注意，当提示是否使用最小骨架时，请选择“否”：

```bash
cd /path/to/source/for/this/chapter
php composer.phar create-project zendframework/zend-expressive-skeleton expressive
```

这将在 `/path/to/source/for/this/chapter/expressive` 创建一个文件夹。进入此目录。修改 `public/index.php` 如下所示：

```php
<?php
if (php_sapi_name() === 'cli-server'
    && is_file(__DIR__ . '/parse_url(
$_SERVER['REQUEST_URI'], PHP_URL_PATH))
) {
    return false;
}

chdir(dirname(__DIR__));
session_start();
$_SESSION['time'] = time();
$appDir = realpath(__DIR__ . '/../..');
$loader = require 'vendor/autoload.php';
$loader->add('Application', $appDir);
$container = require 'config/container.php';
$app = $container->get(\Zend\Expressive\Application::class);
$app->run();
```

然后你需要创建一个封装类来调用我们的会话验证中间件。创建一个 `SessionValidateAction.php` 文件，该文件需要放置在 `/path/to/source/for/this/chapter/expressive/src/App/Action` 文件夹中。为了演示目的，将停止时间参数设置为一个较短的时间间隔。在这种情况下，`time() + 10` 为你提供 10 秒：

```php
namespace App\Action;
use Application\MiddleWare\Session\Validator;
use Zend\Diactoros\ { Request, Response };
use Psr\Http\Message\ResponseInterface;
use Psr\Http\Message\ServerRequestInterface;
class SessionValidateAction
{
    public function __invoke(ServerRequestInterface $request,
    ResponseInterface $response, callable $next = null)
    {
        $inbound = new Response();
        $validator = new Validator($request, time()+10);
        $inbound = $validator($request, $response);
        if ($inbound->getStatusCode() != 200) {
            session_destroy();
            setcookie('PHPSESSID', 0, time()-300);
            $params = json_decode(
                $inbound->getBody()->getContents(), TRUE);
            echo '<h1>', $params[Validator::KEY_TEXT], '</h1>';
            echo '<pre>', var_dump($inbound), '</pre>';
            exit;
        }
        return $next($request,$response);
    }
}
```

现在你需要将新类添加到中间件管道中。修改 `config/autoload/middleware-pipeline.global.php` 如下。修改处以粗体显示：

```php
<?php
use Zend\Expressive\Container\ApplicationFactory;
use Zend\Expressive\Helper;
return [
'dependencies' => [
'invokables' => [
App\Action\SessionValidateAction::class =>
App\Action\SessionValidateAction::class,
],
'factories' => [
Helper\ServerUrlMiddleware::class =>
Helper\ServerUrlMiddlewareFactory::class,
Helper\UrlHelperMiddleware::class =>
Helper\UrlHelperMiddlewareFactory::class,
],
],
'middleware_pipeline' => [
'always' => [
'middleware' => [
Helper\ServerUrlMiddleware::class,
],
'priority' => 10000,
],
'routing' => [
'middleware' => [
ApplicationFactory::ROUTING_MIDDLEWARE,
Helper\UrlHelperMiddleware::class,
App\Action\SessionValidateAction::class,
ApplicationFactory::DISPATCH_MIDDLEWARE,
],
'priority' => 1,
],
'error' => [
'middleware' => [
// Add error middleware here.
],
'error'    => true,
'priority' => -10000,
],
];
```

你可能还需要考虑修改主页模板以显示 `$_SESSION` 的状态。相关的文件是 `/path/to/source/for/this/chapter/expressive/templates/app/home-page.phtml`。简单地添加 `var_dump($_SESSION)` 就足够了。

起初，你应该看到类似以下内容：

![](img/39390f6d56c5a83b28db083a8bd5185c_371_0.png)

10 秒后，刷新浏览器。你现在应该看到以下内容：

![](img/39390f6d56c5a83b28db083a8bd5185c_372_0.png)

## 使用中间件进行跨语言交互

除了试图在不同版本的 PHP 之间进行通信的情况外，PSR-7 中间件的作用将非常有限。回想一下这个缩略词的含义：**PHP 标准推荐（PHP Standards Recommendations）**。因此，如果你需要向用其他语言编写的应用程序发起请求，请将其视为普通的 Web 服务 HTTP 请求。

## 具体步骤...

1.  在 PHP 4 的情况下，实际上是有机会的，因为它支持有限度的面向对象编程。因此，最佳方法是降低前三个配方中描述的基础 PSR-7 类的级别。篇幅有限，无法涵盖所有更改，但我们展示了一个潜在的 PHP 4 版本的 `Application\\MiddleWare\\ServerRequest`。首先要注意的是没有命名空间！因此，我们使用带下划线 `_` 的类名来代替命名空间分隔符：

```php
class Application_MiddleWare_ServerRequest
extends Application_MiddleWare_Request
implements Psr_Http_Message_ServerRequestInterface
{
}
```

2.  在 PHP 4 中，所有属性都使用关键字 `var` 标识：

```php
var $serverParams;
var $cookies;
var $queryParams;
// not all properties are shown
```

3.  `initialize()` 方法几乎相同，除了像 `$this->getServerParams()['REQUEST_URI']` 这样的语法在 PHP 4 中是不允许的。因此，我们需要将其拆分到一个单独的变量中：

```php
function initialize()
{
  $params = $this->getServerParams();
  $this->getCookieParams();
  $this->getQueryParams();
  $this->getUploadedFiles;
  $this->getRequestMethod();
  $this->getContentType();
  $this->getParsedBody();
  return $this->withRequestTarget($params['REQUEST_URI']);
}
```

4.  所有的 `$_XXX` 超全局变量在 PHP 4 的后期版本中都存在：

```php
function getServerParams()
{
  if (!$this->serverParams) {
    $this->serverParams = $_SERVER;
  }
  return $this->serverParams;
}
// not all getXxx() methods are shown to conserve space
```

5.  空合并运算符是在 PHP 7 中引入的。我们需要使用 `isset(XXX) ? XXX : ''` 代替：

```php
function getRequestMethod()
{
  $params = $this->getServerParams();
  $method = isset($params['REQUEST_METHOD'])
           ? $params['REQUEST_METHOD'] : '';
  $this->method = strtolower($method);
  return $this->method;
}
```

6.  JSON 扩展直到 PHP 5 才被引入。因此，我们需要满足于原始输入。我们也可能需要使用 `serialize()` 或 `unserialize()` 来代替 `json_encode()` 和 `json_decode()`：

```php
function getParsedBody()
{
    if (!$this->parsedBody) {
        if (($this->getContentType() ==
            Constants::CONTENT_TYPE_FORM_ENCODED
            || $this->getContentType() ==
            Constants::CONTENT_TYPE_MULTI_FORM)
            && $this->getRequestMethod() ==
            Constants::METHOD_POST)
        {
            $this->parsedBody = $_POST;
        } elseif ($this->getContentType() ==
            Constants::CONTENT_TYPE_JSON
            || $this->getContentType() ==
            Constants::CONTENT_TYPE_HAL_JSON)
        {
            ini_set('allow_url_fopen', true);
            $this->parsedBody =
                file_get_contents('php://stdin');
        } elseif (empty($_REQUEST)) {
            $this->parsedBody = $_REQUEST;
        } else {
            ini_set('allow_url_fopen', true);
            $this->parsedBody =
                file_get_contents('php://stdin');
        }
    }
    return $this->parsedBody;
}
```

7.  `withXXX()` 方法在 PHP 4 中工作方式大致相同：

```php
function withParsedBody($data)
{
    $this->parsedBody = $data;
    return $this;
}
```





8. 同样，`withoutXXX()` 方法的作用也是一样的：

```php
function withoutAttribute($name) {
    if (isset($this->attributes[$name])) {
        unset($this->attributes[$name]);
    }
    return $this;
}
```

9. 对于使用其他语言的网站，我们可以使用 PSR-7 类来构建请求和响应，但这需要借助 HTTP 客户端与目标网站进行通信。例如，回顾本章中“开发 PSR-7 请求类”食谱中关于 Request 的演示。以下是“它是如何工作的……”部分中的示例：

```php
$request = new Request(
    TARGET_WEBSITE_URL,
    Constants::METHOD_POST,
    new TextStream($contents),
    [
        Constants::HEADER_CONTENT_TYPE => Constants::CONTENT_TYPE_FORM_ENCODED,
        Constants::HEADER_CONTENT_LENGTH => $body->getSize()
    ]
);

$data = http_build_query(['data' =>
    $request->getBody()->getContents()
]);

$defaults = array(
    CURLOPT_URL => $request->getUri()->getUriString(),
    CURLOPT_POST => true,
    CURLOPT_POSTFIELDS => $data,
);
$ch = curl_init();
curl_setopt_array($ch, $defaults);
$response = curl_exec($ch);
curl_close($ch);
```

## 10. 探讨高级算法

在本章中，我们将涵盖以下内容：

- 使用 getter 和 setter
- 实现链表
- 构建冒泡排序
- 实现栈
- 构建二分查找类
- 实现搜索引擎
- 显示多维数组并累加总和

### 引言

在本章中，我们介绍了实现各种高级算法的食谱，例如链表、冒泡排序、栈和二分查找。此外，我们还将介绍 getter 和 setter，以及实现搜索引擎和显示带有累积总和的多维数组值。

### 使用 getter 和 setter

乍一看，定义具有**公共属性**的类似乎很有道理，这样可以直接读取或写入这些属性。然而，最佳做法是将属性设置为**_受保护的_**，并为每个属性定义一个**getter**和一个**setter**。顾名思义，**_getter_**用于获取属性的值。**_setter_**用于设置值。

> **最佳实践**
>
> 将属性定义为**_受保护的_**，以防止意外的_外部访问_。使用**_公共的 get* 和 set*_**方法来提供对这些属性的访问。通过这种方式，不仅可以更精确地控制访问，还可以在对属性进行**_获取_**和**_设置_**时对其格式和数据类型进行修改。

#### 如何做……

1. **Getter 和 setter**在**_获取_**或**_设置_**值时提供了额外的灵活性。

如果需要，你可以添加一层额外的逻辑，而如果直接读写公共属性，这是无法实现的。你所要做的只是创建一个以**_get_**或**_set_**为前缀的公共方法。属性的名称将成为后缀。约定将变量的首字母大写。因此，如果属性是**_$testValue_**，那么**_getter_**将是**_getTestValue()_**。

2. 在此示例中，我们定义了一个**_类_**，其中包含一个**_受保护的_**属性 **_$date_**。请注意，**_get_** 和 **_set_** 方法允许将其作为 **_DateTime_** 对象或字符串来处理。实际上，无论如何，值都会存储为 **_DateTime_** 实例：

```php
$a = new class() {
    protected $date;
    public function setDate($date)
    {
        if (is_string($date)) {
            $this->date = new DateTime($date);
        } else {
            $this->date = $date;
        }
    }
    public function getDate($asString = FALSE)
    {
        if ($asString) {
            return $this->date->format('Y-m-d H:i:s');
        } else {
            return $this->date;
        }
    }
};
```

3. Getter 和 setter 允许你过滤或清理传入或传出的数据。在以下示例中，有两个属性 `$intVal` 和 `$arrVal`，它们的默认初始值设置为 `NULL`。请注意，getter 的返回值不仅具有数据类型，还提供了默认值。setter 也会强制要求传入的数据类型，或将传入值强制转换为特定的数据类型：

```php
<?php
class GetSet
{
    protected $intVal = NULL;
    protected $arrVal = NULL;
    // 注意使用空合并运算符返回默认值
    public function getIntVal() : int
    {
        return $this->intVal ?? 0;
    }
    public function getArrVal() : array
    {
        return $this->arrVal ?? array();
    }
    public function setIntVal($val)
    {
        $this->intVal = (int) $val ?? 0;
    }
    public function setArrVal(array $val)
    {
        $this->arrVal = $val ?? array();
    }
}
```

4. 如果你的类拥有大量的属性，为每个属性定义不同的 getter 和 setter 可能会变得繁琐。在这种情况下，你可以使用魔术方法 `__call()` 定义一种回退机制。下面的类定义了九个不同的属性。相反于定义九个 getter 和九个 setter，我们定义了一个单一的方法 `__call()`，该方法判断用法是 get 还是 set。如果是 get，它从内部数组中检索键；如果是 set，它将值存储在内部数组中。

`__call()` 方法是一个魔术方法，当应用程序调用不存在的方法时会执行此方法。

```php
<?php
class LotsProps
{
    protected $firstName = NULL;
    protected $lastName = NULL;
    protected $addr1    = NULL;
    protected $addr2    = NULL;
    protected $city     = NULL;
    protected $state    = NULL;
    protected $province = NULL;
    protected $postalCode = NULL;
    protected $country  = NULL;
    protected $values  = array();

    public function __call($method, $params)
    {
        preg_match('/^(get|set)(.*)$/i', $method, $matches);
        $prefix = $matches[1] ?? '';
        $key    = $matches[2] ?? '';
        $key = strtolower($key);
        if ($prefix == 'get') {
            return $this->values[$key] ?? '---';
        } else {
            $this->values[$key] = $params[0];
        }
    }
}
```

#### 它是如何工作的……

将步骤 2 中提到的代码复制到新文件 `chap_10_oop_using_getters_and_setters.php` 中。要测试该类，请添加以下内容：

```php
// 使用字符串设置日期
$a->setDate('2015-01-01');
var_dump($a->getDate());

// 检索 DateTime 实例
var_dump($a->getDate(TRUE));
```

```php
// 使用 DateTime 实例设置日期
$a->setDate(new DateTime('now'));
var_dump($a->getDate());

// 检索 DateTime 实例
var_dump($a->getDate(TRUE));
```

在输出结果（如下所示）中，你可以看到 `$date` 属性可以使用字符串或实际的 `DateTime` 实例进行设置。执行 `getDate()` 时，可以根据 `$asString` 标志的值返回字符串或 `DateTime` 实例：

![](img/39390f6d56c5a83b28db083a8bd5185c_381_0.png)

接下来，查看步骤 3 中定义的代码。将此代码复制到文件 `chap_10_oop_using_getters_and_setters_defaults.php` 中，并添加以下内容：

```php
// 创建实例
$a = new GetSet();

// 设置一个“正确”的值
$a->setIntVal(1234);
echo $a->getIntVal();
echo PHP_EOL;

// 设置一个无效的值
$a->setIntVal('some bogus value');
echo $a->getIntVal();
echo PHP_EOL;

// 注意：布尔值 TRUE == 1
$a->setIntVal(TRUE);
echo $a->getIntVal();
echo PHP_EOL;

// 即使没有设置值，也返回 array()
var_dump($a->getArrVal());
echo PHP_EOL;

// 设置一个“正确”的值
$a->setArrVal(['A','B','C']);
var_dump($a->getArrVal());
echo PHP_EOL;

try {
    $a->setArrVal('this is not an array');
    var_dump($a->getArrVal());
    echo PHP_EOL;
} catch (TypeError $e) {
    echo $e->getMessage();
}

echo PHP_EOL;
```

正如你从以下输出中看到的，设置*正确*的整数值按预期工作。非数值默认设置为 0。有趣的是，如果你提供布尔值 `TRUE` 作为 `setIntVal()` 的参数，它会被解释为 1。

如果你在不设置值的情况下调用 `getArrVal()`，默认值是一个空数组。设置数组值按预期工作。但是，如果你提供非数组值作为参数，数组的类型提示会导致抛出 `TypeError`，可以像这里展示的那样捕获它：





### 0. 终端

```
234
0
1 array(0) {
}
array(3) {
    [0] =>
    string(1) "A"
    [1] =>
    string(1) "B"
    [2] =>
    string(1) "C"
}
PHP TypeError: Argument 1 passed to GetSet::setArrVal() must be of the type array, string given, called in /home/aed/Repos/php7_recipes/source/chapter04/chap_04_oop_using_getters_and_setters_defaults.php on line 57 in /home/aed/Repos/php7_recipes/source/chapter04/chap_04_oop_using_getters_and_setters_defaults.php on line 23
PHP Stack trace:
PHP  1. {main}() /home/aed/Repos/php7_recipes/source/chapter04/chap_04_oop_using_getters_and_setters_defaults.php:0
PHP  2. GetSet->setArrVal() /home/aed/Repos/php7_recipes/source/chapter04/chap...
```

最后，将步骤 3 中定义的 LotsProps 类放在单独的文件中，命名为 chap_10_oop_using_getters_and_setters_magic_call.php。现在添加代码来设置值。当然，会发生的情况是调用了魔术方法 `__call()`。在执行 `preg_match()` 之后，不存在属性中“set”字母之后的剩余部分将成为内部数组 `$values` 中的一个键：

```php
$a = new LotsProps();
$a->setFirstName('Li\'l Abner');
$a->setLastName('Yokum');
$a->setAddr1('1 Dirt Street');
$a->setCity('Dogpatch');
$a->setState('Kentucky');
$a->setPostalCode('12345');
$a->setCountry('USA');
?>
```

然后，你可以定义用于显示值的 HTML，使用对应的获取方法。这些方法反过来会从内部数组中返回键：

```html
<div class="container">
<div class="left blue1">Name</div>
<div class="right yellow1">
<?php echo $a->getFirstName() . ' ' . $a->getLastName(); ?> </div>
</div>
<div class="left blue2">Address</div>
<div class="right yellow2">
<?php echo $a->getAddr1(); ?>
<br><?php echo $a->getAddr2(); ?>
<br><?php echo $a->getCity(); ?>
<br><?php echo $a->getState(); ?>
<br><?php echo $a->getProvince(); ?>
<br><?php echo $a->getPostalCode(); ?>
<br><?php echo $a->getCountry(); ?>
</div>
</div>
```

这是最终的输出：

![](img/39390f6d56c5a83b28db083a8bd5185c_384_0.png)

## 实现链表

链表是一个列表包含指向另一个列表中键的键。以数据库术语打比方，这就好比有一个包含数据的表，以及一个指向该数据的独立索引。一个索引可能根据 ID 生成项目列表。另一个索引可能根据标题生成列表，等等。链表的关键特征在于你不需要触碰原始的项目列表。

例如，在下面的图中，主列表包含 ID 编号和水果名称。如果你直接输出主列表，水果名称的显示顺序将是：苹果、葡萄、香蕉、橙子、樱桃。然而，如果你使用链表作为索引，水果名称的结果输出将是：苹果、香蕉、樱桃、葡萄、橙子：

![](img/39390f6d56c5a83b28db083a8bd5185c_384_1.png)

链表的主要用途之一是以不同的顺序生成项目显示。一种方法是创建键值对的迭代，其中键代表新的顺序，值包含主列表中键的值。这样的函数可能如下所示：

```php
function buildLinkedList (array $primary,
callable $makeLink)
{
$linked = new ArrayIterator ();
foreach ($primary as $key => $row) {
$linked->offsetSet ($makeLink ($row), $key);
}
$linked->ksort ();
return $linked;
}
```

我们使用匿名函数生成新键，以提供额外的灵活性。你也会注意到我们进行了按键排序 (`ksort()`)，以便链表按键的顺序进行迭代。

使用链表所需要做的只是遍历它，但生成来自主列表的结果，在本例中是 $customer：

```php
foreach ($linked as $key => $link) {
$output .= printRow ($customer [$link]);
}
```

请注意，我们以任何方式都没有触碰主列表。这使我们能够生成多个链表，每个代表不同的顺序，同时保留原始的数据集。

链表的另一个重要用途是过滤。该技术与之前所示的类似。唯一的区别是我们扩展了 `buildLinkedList()` 函数，添加了过滤列和过滤值：

```php
function buildLinkedList (array $primary,
callable $makeLink,
$filterCol = NULL,
$filterVal = NULL)
{
$linked = new ArrayIterator ();
$filterVal = trim ($filterVal);
foreach ($primary as $key => $row) {
if ($filterCol) {
if (trim ($row [$filterCol] )) == $filterVal) {
$linked->offsetSet ($makeLink ($row), $key);
	}
	} else {
		$linked->offsetSet($makeLink($row), $key);
	}
	}
	$linked->ksort();
	return $linked;
}
```

-   我们只包括那些主列表中由 $filterCol 表示的值与 $filterVal 匹配的项目进入链表。迭代逻辑与步骤 2 中所示的相同。

-   最后，链表的另一种形式是双向链表。在这种情况下，列表以这样一种方式构建，即迭代可以正向或反向进行。在 PHP 的情况下，我们很幸运拥有一个 SPL 类，SplDoublyLinkedList，它巧妙地完成了这项工作。这是一个构建双向链表的函数：

```php
function buildDoublyLinkedList(ArrayIterator $linked)
{
	$double = new SplDoublyLinkedList();
	foreach ($linked as $key => $value) {
		$double->push($value);
	}
	return $double;
}
```

![](img/39390f6d56c5a83b28db083a8bd5185c_386_0.png)

## 工作原理...

将第一个项目符号中显示的代码复制到文件 chap_10_linked_list_include.php 中。为了演示链表的使用，你需要一个数据源。对于此示例，你可以使用前面食谱中提到的 customer.csv 文件。它是一个 CSV 文件，具有以下列：

```
"id", "name", "balance", "email", "password", "status", "security_question",
"confirm_code", "profile_id", "level"
```

你可以向前面提到的包含文件中添加以下函数，以生成客户的主列表并显示他们的信息。请注意，我们使用第一列 id 作为主键：

```php
function readCsv($fn, &$headers)
{
    if (!file_exists($fn)) {
        throw new Error('File Not Found');
    }
    $fileObj = new SplFileObject($fn, 'r');
    $result = array();
    $headers = array();
    $firstRow = TRUE;
    while ($row = $fileObj->fgetcsv()) {
        // store 1st row as headers
        if ($firstRow) {
            $firstRow = FALSE;
            $headers = $row;
        } else {
            if ($row && $row[0] !== NULL && $row[0] != 0) {
                $result[$row[0]] = $row;
            }
        }
    }
    return $result;
}

function printHeaders($headers)
{
    return sprintf('%4s : %18s : %8s : %32s : %4s' . PHP_EOL,
                   ucfirst($headers[0]),
                   ucfirst($headers[1]),
                   ucfirst($headers[2]),
                   ucfirst($headers[3]),
                   ucfirst($headers[9]));
}

function printRow($row)
{
    return sprintf('%4d : %18s : %.2f : %32s : %4s' . PHP_EOL,
                   $row[0], $row[1], $row[2], $row[3], $row[9]);
}
```

```php
function printCustomer($headers, $linked, $customer)
{
    $output = '';
    $output .= printHeaders($headers);
    foreach ($linked as $key => $link) {
        $output .= printRow($customer[$link]);
    }
    return $output;
}
```

然后，你可以定义一个调用程序 chap_10_linked_list_in_order.php，它包含前面定义的文件，并读取 customer.csv：

```php
<?php
define('CUSTOMER_FILE', __DIR__ . '/../data/files/customer.csv');
include __DIR__ . '/chap_10_linked_list_include.php';
$headers = array();
$customer = readCsv(CUSTOMER_FILE, $headers);
```

然后，你可以定义一个将生成链表中键的匿名函数。在这个示例中，定义一个将第 1 列 (name) 分解为名字和姓氏的函数：

```php
$makeLink = function ($row) {
    list($first, $last) = explode(' ', $row[1]);
    return trim($last) . trim($first);
};
```

然后，你可以调用该函数来构建链表，并使用 printCustomer() 显示结果：

```php
$linked = buildLinkedList($customer, $makeLink);
echo printCustomer($headers, $linked, $customer);
```

输出的显示方式可能如下：




| 编号 | 姓名 | 余额 | 邮箱 | 级别 |
|---|---|---|---|---|
| 74 | Louella Allen | 847.65 | louella.allen@telecon.net | 高级 |
| 49 | Omar Anthony | 3733.80 | omar.anthony@fastmedia.com | 中级 |
| 4 | Morgan Avila | 888.88 | morgan.avila@northmedia.com | 高级 |
| 9 | Armando Barlow | 6524.00 | armando.barlow@gabcable.com | 初级 |
| 32 | Matilda Barrera | 478.32 | matilda.barrera@northcon.com | 中级 |
| 54 | Ramiro Bentley | 565.81 | ramiro.bentley@westmedia.com | 初级 |
| 11 | Felix Blevins | 130.57 | felix.blevins@southcom.net | 初级 |
| 69 | Lucille Bradford | 677.58 | lucille.bradford@westmedia.com | 高级 |
| 52 | Jesus Bright | 869.89 | jesus.bright@abcablenet.net | 初级 |
| 76 | Lana Burns | 261.98 | lana.burns@westcon.com | 高级 |
| 57 | Garrett Campos | 9.47 | garrett.campos@fastcom.net | 初级 |
| 12 | Jose Carter | 56.22 | jose.carter@westcon.com | 中级 |
| 24 | Cecelia Case | 592.19 | cecelia.case@southmedia.com | 中级 |
| 68 | Geneva Case | 268.75 | geneva.case@westmedia.com | 初级 |
| 43 | Roland Chang | 514.16 | roland.chang@southmedia.com | 中级 |
| 46 | Dominick Cling | 881.77 | dominick.cling@telecon.com | 中级 |
| 22 | Coleen Walker | 6595.20 | coleen.walker@fastmedia.com | 中级 |
| 39 | Lena Conway | 757.22 | lena.conway@eastnet.net | 高级 |
| 30 | Krista Cortez | 414.66 | krista.cortez@eastcon.com | 初级 |
| 8 | Brian Crawford | 125.58 | brian.crawford@fastcom.net | 高级 |
| 19 | Gene Cruz | 683.55 | gene.cruz@eastcon.com | 高级 |
| 28 | Gabriela Davis | 88.87 | gabriela.davis@southmedia.net | 高级 |
| 79 | Renee Decker | 447.83 | renee.decker@westcon.net | |

要生成过滤后的结果，请按照步骤 4 中讨论的方法修改 `buildLinkedList()`。然后，你可以添加逻辑来检查过滤列的值是否与过滤器中的值匹配：

```php
define('LEVEL_FILTER', 'INT');

$filterCol = 9;
$filterVal = LEVEL_FILTER;
$link= buildLinkedList($customer, $makeLink, $filterCol, $filterVal);
```

## 更多知识

PHP 7.1 引入了使用 `[]` 作为 `list()` 替代方案的功能。如果你查看之前提到的匿名函数，可以使用 PHP 7.1 将其重写如下：

```php
$makeLink = function ($row) {
    [$first, $last] = explode(' ', $row[1]);
    return trim($last) . trim($first);
};
```

有关更多信息，请参阅 https://wiki.php.net/rfc/short_list_syntax。

## 构建冒泡排序

经典的**冒泡排序**是通常分配给大学生的练习。尽管如此，掌握此算法非常重要，因为有许多情况下内置的 PHP 排序函数不适用。一个例子是对多维数组进行排序，其中排序键不是第一列。

冒泡排序的工作方式是递归地遍历列表，并将当前值与下一个值交换。如果你想让项目按升序排列，则当下一个项目小于当前项目时发生交换。对于降序，如果相反的情况为真，则发生交换。当不再发生交换时，排序结束。

在下面的图中，第一次遍历后，**葡萄**和**香蕉**进行了交换，**橙子**和**樱桃**也进行了交换。第二次遍历后，**葡萄**和**樱桃**进行了交换。最后一次遍历没有发生更多交换，冒泡排序结束：

![](img/39390f6d56c5a83b28db083a8bd5185c_390_0.png)

## 操作方法...

1. 我们不想实际移动数组中的值；那在资源使用方面会非常昂贵。相反，我们将使用**链表**，这在之前的食谱中已经讨论过。
2. 首先，我们使用之前食谱中讨论的 `buildLinkedList()` 函数构建一个链表。
3. 然后，我们定义一个新函数 `bubbleSort()`，它接受按引用传入的链表、主列表、排序字段以及表示排序顺序（升序或降序）的参数：

```php
function bubbleSort(&$linked, $primary, $sortField, $order = 'A')
{
```

4. 所需的变量包括一个表示迭代次数的变量、交换次数，以及基于链表的迭代器：

```php
static $iterations = 0;
$swaps = 0;
$iterator = new ArrayIterator($linked);
```

5. 在 `while()` 循环中，只有当迭代仍然有效时才继续，也就是说，仍在进行中。然后我们获取当前的键和值，以及下一个键和值。注意额外的 `if()` 语句，以确保迭代仍然有效（即，确保我们没有掉出列表末端）：

```php
while ($Iterator->valid()) {
    $currentLink = $Iterator->current();
    $currentKey = $Iterator->key();
    if (!$Iterator->valid()) break;
    $Iterator->next();
    $nextLink = $Iterator->current();
    $nextKey = $Iterator->key();
```

6. 接下来，我们检查排序是升序还是降序。根据方向，我们检查下一个值是大于还是小于当前值。比较的结果存储在 `$expr` 中：

```php
if ($Order == 'A') {
    $expr = $primary[$linked->offsetGet
        ($currentKey)]{$sortField} >
        $primary[$linked->offsetGet($nextKey)]{$sortField};
} else {
    $expr = $primary[$linked->offsetGet
        ($currentKey)]{$sortField} <
        $primary[$linked->offsetGet($nextKey)]{$sortField};
}
```

7. 如果 `$expr` 的值为 TRUE，且当前键和下一个键均有效，则在链表中交换值。我们还增加 `$swaps` 的值：

```php
if ($expr && $currentKey && $nextKey
    && $linked->offsetExists($currentKey)
    && $linked->offsetExists($nextKey)) {
    $tmp = $linked->offsetGet($currentKey);
    $linked->offsetSet($currentKey,
        $linked->offsetGet($nextKey));
    $linked->offsetSet($nextKey, $tmp);
    $swaps++;
}
```

8. 最后，如果发生了任何交换，我们需要再次运行迭代，直到不再有交换。因此，我们对同一方法进行递归调用：

```php
if ($swaps) bubbleSort($linked, $primary, $sortField, $Order);
```

9. 真正的返回值是重新组织的链表。我们还返回迭代次数仅供参考：

```php
return ++$iterations;
}
```

## 工作原理...

将之前讨论的 `bubbleSort()` 函数添加到在前一个食谱中创建的 include 文件中。你可以使用前一个食谱中讨论的相同逻辑来读取客户 `.csv` 文件，生成主列表：

```php
<?php
define('CUSTOMER_FILE', _DIR_ . '../data/files/customer.csv');
include _DIR_ . '/chap_10_linked_list_include.php';
$headers = array();
$customer = readCsv(CUSTOMER_FILE, $headers);
```

然后，你可以使用第一列作为排序键生成一个链表：

```php
$makeLink = function ($row) {
    return $row[0];
};
$linked = buildLinkedList($customer, $makeLink);
```

最后，调用 `bubbleSort()` 函数，提供链表和客户列表作为参数。你还可以提供一个排序列，在本例中是表示账户余额的第 2 列，使用字母 'A' 表示升序。可以使用 `printCustomer()` 函数来显示输出：

```php
echo 'Iterations: ' . bubbleSort($linked, $customer, 2, 'A') . PHP_EOL;
echo printCustomer($headers, $linked, $customer);
```

以下是输出的示例：

![](img/39390f6d56c5a83b28db083a8bd5185c_392_0.png)

## 实现栈

**栈**是一种简单的算法，通常实现为**后进先出（LIFO）**。想象一下堆放在图书馆桌子上的书堆。当图书管理员将书放回原处时，最上面的书首先被处理，依此类推，直到堆叠底部的书被替换。最上面的书是最后放在堆叠上的，因此是后进先出。

在编程术语中，栈用于临时存储信息。检索顺序便于首先检索最新的项目。

## 操作方法...

1. 首先，我们定义一个类 `Application\Generic\Stack`。核心逻辑封装在一个 SPL 类 `SplStack` 中：

```php
namespace Application\Generic;
use SplStack;
class Stack
{
    // code
}
```

2. 接下来，我们定义一个属性来表示栈，并设置一个 `SplStack` 实例：

```php
protected $stack;
public function __construct()
{
    $this->stack = new SplStack();
}
```

3. 之后，我们定义方法来向栈中添加和移除元素，即经典的 `push()` 和 `pop()` 方法：

```php
public function push($message)
{
    $this->stack->push($message);
}
public function pop()
{
    return $this->stack->pop();
}
```




## 工作原理...

堆栈的一种可能用途是存储消息。对于消息而言，通常希望优先获取最新的消息，因此堆栈是一个完美的使用场景。按照本食谱中的讨论，定义 `Application\Generic\Stack` 类。接下来，定义一个调用程序，设置自动加载并创建 *Stack* 的实例：

```php
<?php
// setup class autoloading
require __DIR__ . '/../Application/Autoload/Loader.php';
Application\Autoload\Loader::init(__DIR__ . '/../');

use Application\Generic\Stack;
$stack = new Stack();
```

要对堆栈进行操作，可以存储一系列消息。由于你很可能会在应用程序的不同位置存储消息，因此可以使用 *sleep*() 来模拟其他代码的运行：

```php
echo 'Do Something ... ' . PHP_EOL;
$stack->push('1st Message: ' . date('H:i:s'));
sleep(3);

echo 'Do Something Else ... ' . PHP_EOL;
$stack->push('2nd Message: ' . date('H:i:s'));
sleep(3);

echo 'Do Something Else Again ... ' . PHP_EOL;
$stack->push('3rd Message: ' . date('H:i:s'));
sleep(3);
```

最后，只需遍历堆栈以获取消息。请注意，你可以将 *Stack* 对象当作函数调用，这将返回 SplStack 实例：

```php
echo 'What Time Is It?' . PHP_EOL;
foreach ($stack() as $item) {
    echo $item . PHP_EOL;
}
```

以下是预期输出：

![](img/39390f6d56c5a83b28db083a8bd5185c_395_0.png)

## 构建二分查找类

传统搜索通常按顺序遍历项目列表。这意味着需要搜索的最大项目数量可能与列表长度相同！这效率不高。如果需要加快搜索速度，可以考虑实现*二分*查找。

该技术非常简单：你找到列表的中点，并判断搜索项是小于、等于还是大于中点项。如果小于，则将上限设置为中点，只搜索列表的前半部分。如果大于，则将下限设置为中点，只搜索列表的后半部分。然后继续将列表分为 1/4、1/8、1/16，依此类推，直到找到搜索项（或未找到）。

![](img/39390f6d56c5a83b28db083a8bd5185c_395_1.png)

> 需要注意的是，虽然二分查找的最大比较次数比顺序搜索小得多（log n + 1，其中 n 是列表中的元素数量，log 是对数），但参与搜索的列表必须先排序，这自然会降低性能。

### 实现步骤…

1.  首先构建一个搜索类，`Application\Generic\Search`，它接受主列表作为参数。作为控制手段，我们还定义了一个属性 `$iterations`：

```php
namespace Application\Generic;

class Search
{
    protected $primary;
    protected $iterations;
    
    public function __construct($primary)
    {
        $this->primary = $primary;
    }
}
```

2.  接下来定义一个方法 `binarySearch()`，用于设置搜索基础设施。首要任务是构建一个单独的数组 `$search`，其键是包含在搜索中的列的组合。然后按键排序：

```php
public function binarySearch(array $keys, $item)
{
    $search = array();
    foreach ($this->primary as $primaryKey => $data) {
        $searchKey = function ($keys, $data) {
            $key = '';
            foreach ($keys as $k) $key .= $data[$k];
            return $key;
        };
        $search[$searchKey($keys, $data)] = $primaryKey;
    }
    ksort($search);
}
```

3.  然后将键提取到另一个数组 `$binary` 中，以便基于数字键执行二分排序。接着调用 `doBinarySearch()`，这会返回中间数组 `$search` 中的一个键，或者布尔值 `FALSE`：

```php
$binary = array_keys($search);
$result = $this->doBinarySearch($binary, $item);
return $this->primary[$search[$result]] ?? FALSE;
```

4.  第一个 `doBinarySearch()` 初始化了一系列参数。`$iterations`、`$found`、`$loop`、`$done` 和 `$max` 都用于防止无限循环。`$upper` 和 `$lower` 代表要检查的列表切片：

```php
public function doBinarySearch($binary, $item)
{
    $iterations = 0;
    $found = FALSE;
    $loop = TRUE;
    $done = -1;
    $max = count($binary);
    $lower = 0;
    $upper = $max - 1;
}
```

5.  然后实现一个 `while()` 循环并设置中点：

```php
while ($loop && !$found) {
    $mid = (int) (($upper - $lower) / 2) + $lower;
}
```

6.  现在可以使用新的 PHP 7 **太空船运算符**，它在单次比较中给出了小于、等于或大于的结果。如果小于，将上限设置为中点。如果大于，将下限调整为中点。如果相等，我们就完成了，安然脱身：

```php
switch ($item <=> $binary[$mid]) {
    // $item < $binary[$mid]
    case -1 :
        $upper = $mid;
        break;
    // $item == $binary[$mid]
    case 0 :
        $found = $binary[$mid];
        break;
    // $item > $binary[$mid]
    case 1 :
    default :
        $lower = $mid;
}
```

7.  现在进行一点循环控制。我们增加迭代次数，并确保其不超过列表的大小。如果是这样，肯定出了问题，我们需要退出。否则，我们检查上下限是否连续两次以上相同，如果是这样，则未找到搜索项。然后存储迭代次数并返回找到的（或未找到的）结果：

```php
$loop = (($iterations++ < $max) && ($done < 1));
$done += ($upper == $lower) ? 1 : 0;
}
$this->iterations = $iterations;
return $found;
```

## 工作原理...

首先，实现 `Application\Generic\Search` 类，定义本食谱中描述的方法。接下来，定义一个调用程序 `chap_10_binary_search.php`，设置自动加载并读取 `customer.csv` 文件作为搜索目标（如上一个食谱中所述）：

```php
<?php
define('CUSTOMER_FILE', __DIR__ . '/../data/files/customer.csv');
include __DIR__ . '/chap_10_linked_list_include.php';
require __DIR__ . '/../Application/Autoload/Loader.php';
Application\Autoload\Loader::init(__DIR__ . '../');

use Application\Generic\Search;
$headers = array();
$customer = readCsv(CUSTOMER_FILE, $headers);
```

然后你可以创建一个新的 `Search` 实例，并指定列表中间某处的一项。在这个示例中，搜索基于第 1 列（客户姓名），搜索项是 Todd Lindsey：

```php
$search = new Search($customer);
$item = 'Todd Lindsey';
$cols = [1];
echo "Searching For: $item\n";
var_dump($search->binarySearch($cols, $item));
```

为了说明，在 `Application\Generic\Search::doBinarySearch()` 中的 `switch()` 之前添加这一行：

```php
echo "Upper:Mid:Lower:<=> | " . $upper . ':' . $mid . ':' .
     $lower . ':' . ($item <=> $binary[$mid]);
```

输出显示如下。注意上限、中点和下限是如何调整直到找到项目的：

```text
Searching For: Todd Lindsey
Upper:Mid:Lower:<=> | 81:40:8:1
Upper:Mid:Lower:<=> | 81:60:40:1
Upper:Mid:Lower:<=> | 81:70:60:1
Upper:Mid:Lower:<=> | 81:75:70:1
Upper:Mid:Lower:<=> | 81:78:75:0
array(18) {
  [0]=>
  string(2) "58"
  [1]=>
  string(12) "Todd Lindsey"
  [2]=>
  string(5) "48.91"
  [3]=>
  string(24) "todd.lindsey@fastnet.net"
  [4]=>
  string(16) "an2O73Conscience"
  [5]=>
  string(1) "1"
  [6]=>
  string(0) ""
  [7]=>
  string(0) ""
  [8]=>
  string(0) ""
}
```

### 参见

有关二分查找的更多信息，维基百科上有一篇很棒的文章，详细讲解了基本数学原理，链接如下：https://en.wikipedia.org/wiki/Binary_search_algorithm。

## 实现搜索引擎

为了实现搜索引擎，我们需要为在搜索中包含多列做准备。此外，重要的是要认识到，搜索项可能位于字段的中间，而且用户很少会提供足够的信息来进行精确匹配。因此，我们将大量依赖 SQL LIKE `$value` 子句。

### 实现步骤...

1.  首先，我们定义一个基本类来保存搜索条件。该对象包含三个属性：键（最终代表数据库列）、运算符（LIKE、<、> 等）；以及可选的项目。项目可选的原因是，某些运算符，如 IS NOT NULL，不需要具体数据：

```php
namespace Application\Database\Search;

class Criteria
{
    public $key;
    public $item;
}
```




## 2. 接下来，我们需要定义一个类 `Application\Database\Search\Engine`，并提供必要的类常量和属性。

`$columns` 和 `$mapping` 之间的区别在于，`$columns` 保存最终将出现在 HTML SELECT 字段（或等效字段）中的信息。出于安全原因，我们不希望暴露数据库列的实际名称，因此需要另一个数组 `$mapping`：

```php
namespace Application\Database\Search;
use PDO;
use Application\Database\Connection;
class Engine
{
    const ERROR_PREPARE = 'ERROR: unable to prepare statement';
    const ERROR_EXECUTE = 'ERROR: unable to execute statement';
    const ERROR_COLUMN = 'ERROR: column name not on list';
    const ERROR_OPERATOR = 'ERROR: operator not on list';
    const ERROR_INVALID = 'ERROR: invalid search criteria';

    protected $connection;
    protected $table;
    protected $columns;
    protected $mapping;
    protected $statement;
    protected $sql = '';
```

## 3. 接下来，我们定义一组我们愿意支持的操作符。

键代表实际的 SQL。值是将在表单中显示的内容：

```php
protected $operators = [
    'LIKE' => 'Equals',
    '<' => 'Less Than',
    '>' => 'Greater Than',
    '<>' => 'Not Equals',
    'NOT NULL' => 'Exists',
];
```

## 4. 构造函数接受一个数据库连接实例作为参数。

为了我们的目的，我们将使用在*第 5 章，与数据库交互*中定义的 `Application\Database\Connection`。我们还需要提供数据库表的名称，以及 `$columns`，这是一个任意列键和标签的数组，这些标签将出现在 HTML 表单中。这将引用 `$mapping`，其中键与 `$columns` 匹配，但值代表实际的数据库列名：

```php
public function __construct(Connection $connection, 
                           $table, array $columns, array $mapping)
{
    $this->connection  = $connection;
    $this->setTable($table);
    $this->setColumns($columns);
    $this->setMapping($mapping);
}
```

## 5. 在构造函数之后，我们提供一系列有用的 getter 和 setter：

```php
public function setColumns($columns)
{
    $this->columns = $columns;
}

public function getColumns()
{
    return $this->columns;
}

// etc.
```

## 6. 最关键的方法可能是构建待准备的 SQL 语句的方法。

在初始 SELECT 设置之后，我们添加 WHERE 子句，使用 `$mapping` 添加实际的数据库列名。然后我们添加操作符并实现 `switch()`，根据操作符，可能会或不会添加一个命名占位符，该占位符将代表搜索项：

```php
public function prepareStatement(Criteria $criteria)
{
    $this->sql = 'SELECT * FROM ' . $this->table . ' WHERE ';
    $this->sql .= $this->mapping[$criteria->key] . ' ';
    switch ($criteria->operator) {
        case 'NOT NULL' :
            $this->sql .= ' IS NOT NULL OR ';
            break;
        default :
            $this->sql .= $criteria->operator . ' ';
            $this->sql .= $this->mapping[$criteria->key] . ' OR ';
    }
```

## 7. 现在核心 SELECT 已定义，我们移除末尾的 OR 关键字，并添加一个子句，使结果根据搜索列进行排序。

然后该语句被发送到数据库进行准备：

```php
    $this->sql = substr($this->sql, 0, -4)
        . ' ORDER BY ' . $this->mapping[$Criteria->key];
    $statement = $this->connection->pdo->prepare($this->sql);
    return $statement;
}
```

## 8. 现在我们要进入主要环节，即 search() 方法。

我们接受一个 `Application\Database\Search\Criteria` 对象作为参数。这确保了我们至少有一个项键和操作符。为了保险起见，我们添加了一个 `if()` 语句来检查这些属性：

```php
public function search(Criteria $Criteria)
{
    if (empty($Criteria->key) || empty($Criteria->operator)) {
        yield ['error' => self::ERROR_INVALID];
        return FALSE;
    }
```

## 9. 然后我们调用 prepareStatement()，并使用 try / catch 来捕获错误：

```php
    try {
        if (!$statement = $this->prepareStatement($Criteria)) {
            yield ['error' => self::ERROR_PREPARE];
            return FALSE;
        }
```

## 10. 接下来我们构建一个将提供给 execute() 的参数数组。

键代表在准备语句中用作占位符的数据库列名。注意，我们没有使用 `=`，而是使用了 `LIKE $value$` 构造：

```php
    $params = array();
    switch ($Criteria->operator) {
        case 'NOT NULL' :
            // do nothing; already in statement
            break;
        case 'LIKE' :
            $params[$this->mapping[$Criteria->key]] =
                '%' . $Criteria->item . '%';
            break;
        default :
            $params[$this->mapping[$Criteria->key]] =
                $Criteria->item;
    }
```

## 11. 语句被执行，并使用 `yield` 关键字返回结果，这实际上使该方法变成了一个生成器：

```php
    $statement->execute($params);
    while ($row = $statement->fetch(PDO::FETCH_ASSOC)) {
        yield $row;
    }
    } catch (\Throwable $e) {
        error_log(__METHOD__ . ':' . $e->getMessage());
        throw new Exception(self::ERROR_EXECUTE);
    }
    return TRUE;
}
```

## 工作原理...

将本食谱中讨论的代码放置在 `Application\Database\Search` 下的 `Criteria.php` 和 `Engine.php` 文件中。然后你可以定义一个调用脚本 `chap_10_search_engine.php`，该脚本设置自动加载。你可以利用*第 5 章，与数据库交互*中讨论的 `Application\Database\Connection` 类，以及*第 6 章，构建可扩展网站*中涵盖的表单元素类：

```php
<?php
define('DB_CONFIG_FILE', '/../config/db.config.php');
require __DIR__ . '/../Application/Autoload/Loader.php';
Application\Autoload\Loader::init(__DIR__ . '/../');

use Application\Database\Connection;
use Application\Database\Search\{ Engine, Criteria };
use Application\Form\Generic;
use Application\Form\Element\Select;
```

现在你可以定义哪些数据库列将出现在表单中，以及一个匹配的映射文件：

```php
$dbCols = [
    'cname' => 'Customer Name',
    'cbal' => 'Account Balance',
    'cmail' => 'Email Address',
    'clevel' => 'Level'
];

$mapping = [
    'cname' => 'name',
    'cbal' => 'balance',
    'cmail' => 'email',
    'clevel' => 'level'
];
```

现在你可以设置数据库连接并创建搜索引擎实例：

```php
$conn = new Connection(include __DIR__, DB_CONFIG_FILE);
$engine = new Engine($conn, 'customer', $dbCols, $mapping);
```

为了显示适当的下拉 SELECT 元素，我们基于 `Application\Form\*` 类定义包装器和元素：

```php
$wrappers = [
    Generic::INPUT => ['type' => 'td', 'class' => 'content'],
    Generic::LABEL => ['type' => 'th', 'class' => 'label'],
    Generic::ERRORS => ['type' => 'td', 'class' => 'error']
];

// define elements
$fieldElement = new Select('field',
                        Generic::TYPE_SELECT,
                        'Field',
                        $wrappers,
                        ['id' => 'field']);
$opsElement = new Select('ops',
                        Generic::TYPE_SELECT,
                        'Operators',
                        $wrappers,
                        ['id' => 'ops']);
$itemElement = new Generic('item',
                        Generic::TYPE_TEXT,
                        'Searching For ...',
                        $wrappers,
                        ['id' => 'item','title' => 'If more than one item,
                         separate with commas']);
$submitElement = new Generic('submit',
                            Generic::TYPE_SUBMIT,
                            'Search',
                            $wrappers,
                            ['id' => 'submit','title' => 'Click to Search',
                             'value' => 'Search']);
```

![](img/39390f6d56c5a83b28db083a8bd5185c_404_0.png)





## 探索高级算法

然后我们获取输入参数（如果已定义），设置表单元素选项，创建搜索条件，并执行搜索：

```php
$key = (isset($_GET['field'])) ? strip_tags($_GET['field']) : NULL;
$op = (isset($_GET['ops'])) ? $_GET['ops'] : NULL;
$item = (isset($_GET['item'])) ? strip_tags($_GET['item']) : NULL;
$fieldElement->setOptions($dbCols, $key);
$itemElement->setSingleAttribute('value', $item);
$opsElement->setOptions($engine->getOperators(), $op);
$criteria = new Criteria($key, $op, $item);
$result = $engine->search($criteria);
?>
```

显示逻辑主要面向渲染表单。关于更全面的介绍，参见*第 6 章：构建可扩展的网站*，但在此我们展示核心逻辑：

```html
<form name="search" method="get">
<table class="display" cellspacing="0" width="100%">
<tr><?php echo $fieldElement->render(); ?></tr>
<tr><?php echo $opsElement->render(); ?></tr>
<tr><?php echo $itemElement->render(); ?></tr>
<tr><?php echo $submitElement->render(); ?></tr>
<tr>
<th class="label">结果</th>
<td class="content" colspan=2>
<span style="font-size: 10pt;font-family:monospace;">
<table>
<?php foreach ($result as $row) ?>
<tr>
<td><?php echo $row['id'] ?></td>
<td><?php echo $row['name'] ?></td>
<td><?php echo $row['balance'] ?></td>
<td><?php echo $row['email'] ?></td>
<td><?php echo $row['level'] ?></td>
</tr>
<?php endforeach; ?>
</table>
</span>
</td>
</tr>
</table>
</form>
```

以下是浏览器中的示例输出：

![](img/39390f6d56c5a83b28db083a8bd5185c_406_0.png)

## 显示多维数组并累加总和

如何正确显示来自多维数组的数据，一直是所有 Web 开发者面临的经典难题。为了说明，假设您希望显示客户列表及其购买记录。对于每位客户，您希望显示其姓名、电话号码、账户余额等。这已经代表了一个二维数组，其中 x 轴代表客户，y 轴代表该客户的数据。现在加入购买记录，你就有了第三个维度！如何在二维屏幕上表示三维模型？一种可能的解决方案是使用“隐藏”的 div 标签，配合简单的 JavaScript 可见性切换器。

## 操作方法...

- 首先，我们需要从一个使用多个 **JOIN** 子句的 SQL 语句生成一个三维数组。我们将使用在**第 1 章：构建基础**中介绍的 *Application/Database/Connection* 类来构建适当的 SQL 查询。我们保留两个参数 *open*、*min* 和 *max*，以支持分页。遗憾的是，在这种情况下，我们无法简单使用 **LIMIT** 和 **OFFSET**，因为行数会根据任何给定客户的购买数量而变化。相应地，我们可以通过对 presumably（希望）是递增的客户 ID 施加限制来限制行数。为了使此正常工作，我们还需要将主 **ORDER** 设置为客户 ID：

```php
define('ITEMS_PER_PAGE', 6);
define('SUBROWS_PER_PAGE', 6);
define('DB_CONFIG_FILE', '../config/db.config.php');
include __DIR__ . '../Application/Database/Connection.php';
```

```php
use Application\Database\Connection;
$conn = new Connection(include __DIR__ . DB_CONFIG_FILE);
$sql = 'SELECT c.id, c.name, c.balance, c.email, f.phone, '
         'u.transaction, u.date, u.quantity, u.sale_price, r.title '
         'FROM customer AS c '
         'JOIN profile AS f '
         'ON f.id = c.id '
         'JOIN purchases AS u '
         'ON u.customer_id = c.id '
         'JOIN products AS r '
         'ON u.product_id = r.id '
         'WHERE c.id >= :min AND c.id < :max '
         'ORDER BY c.id ASC, u.date DESC ';
```

- 接下来，我们可以基于客户 ID 的限制，使用简单的 `$_GET` 参数实现一种分页形式。请注意，我们添加了一个额外的检查，以确保 `$prev` 的值不会低于零。你可能需要考虑添加另一个控件，以确保 `$next` 的值不超过最后一个客户 ID。在这个示例中，我们只是允许它递增：

```php
$page = $_GET['page'] ?? 1;
$page = (int) $page;
$next = $page + 1;
$prev = $page - 1;
$prev = ($prev >= 0) ? $prev : 0;
```

- 然后我们计算 `$min` 和 `$max` 的值，并准备和执行 SQL 语句：

```php
$min = $prev * ITEMS_PER_PAGE;
$max = $page * ITEMS_PER_PAGE;
$stmt = $conn->pdo->prepare($sql);
$stmt->execute(['min' => $min, 'max' => $max]);
```

- 可以使用 `while()` 循环来获取结果。为了本例的目的，我们使用简单的获取模式 `PDO::FETCH_ASSOC`。使用客户 ID 作为键，我们将基本客户信息存储为数组参数。然后，我们在子数组 `$results[$key]['purchases'][]` 中存储一个购买信息数组。当客户 ID 发生变化时，这是一个信号，表示存储下一位客户的相同信息。请注意，我们在数组键 `total` 中按客户累加总和：

```php
$custId = 0;
$result = array();
$grandTotal = 0.0;
while ($row = $stmt->fetch(PDO::FETCH_ASSOC)) {
    if ($row['id'] != $custId) {
        $custId = $row['id'];
        $result[$custId] = [
'name'      => $row['name'],
'balance'   => $row['balance'],
'email'     => $row['email'],
'phone'     => $row['phone'],
];
$result[$custId]['total'] = 0;
}
$result[$custId]['purchases'][] = [
'transaction'  => $row['transaction'],
'date'         => $row['date'],
'quantity'     => $row['quantity'],
'sale_price'   => $row['sale_price'],
'title'        => $row['title'],
];
$result[$custId]['total'] += $row['sale_price'];
$grandTotal += $row['sale_price'];
}
?>
```

- 接下来，我们实现视图逻辑。首先，我们从显示主要客户信息的块开始：

```html
<div class="container">
<?php foreach ($result as $key => $data) : ?>
<div class="mainLeft color0">
    <?= $data['name'] ?> [<i><?= $key ?></i>]
</div>
<div class="mainRight">
    <div class="row">
        <div class="left">余额</div>
        <div class="right"><?= $data['balance'] ?></div>
    </div>
    <div class="row">
        <div class="left color2">电子邮件</div>
        <div class="right"><?= $data['email'] ?></div>
    </div>
    <div class="row">
        <div class="left">电话</div>
        <div class="right"><?= $data['phone'] ?></div>
    </div>
    <div class="row">
        <div class="left color2">总购买金额</div>
        <div class="right">
<?= number_format($data['total'], 2) ?>
</div>
</div>
```

- 接下来是显示该客户购买列表的逻辑：

```html
<!-- 购买信息 -->
<table>
    <tr>
        <th>交易</th><th>日期</th><th>数量</th>
        <th>价格</th><th>产品</th>
    </tr>
    <?php $count = 0; ?>
    <?php foreach ($data['purchases'] as $purchase) : ?>
        <?php $class = ($count++ & 01) ? 'color1' : 'color2'; ?>
        <tr>
            <td class="<?= $class ?>"><?= $purchase['transaction'] ?></td>
            <td class="<?= $class ?>"><?= $purchase['date'] ?></td>
            <td class="<?= $class ?>"><?= $purchase['quantity'] ?></td>
            <td class="<?= $class ?>"><?= $purchase['sale_price'] ?></td>
            <td class="<?= $class ?>"><?= $purchase['title'] ?></td>
        </tr>
    <?php endforeach; ?>
</table>
```

- 为了分页的目的，我们随后添加按钮来表示上一页和下一页：

```html
<?php endforeach; ?>
<div class="container">
    <a href="?page=<?= $prev ?>">
        <input type="button" value="上一页" />
    </a>
    <a href="?page=<?= $next ?>">
        <input type="button" value="下一页" class="buttonRight" />
    </a>
</div>
<div class="clearRow"></div>
</div>
```

- 迄今为止的结果，不幸的是，远非整洁有序！因此，我们添加一个简单的 JavaScript 函数，根据其 id 属性切换 `<div>` 标签的可见性：

```javascript
<script type="text/javascript">
function showOrHide(id) {
    var div = document.getElementById(id);
    div.style.display = div.style.display == "none" ?
        "block" : "none";
}
</script>
```





9.  接下来，我们将 purchases 表包裹在一个初始不可见的 `<div>` 标签内。然后，我们可以限制初始显示的子行数，并添加一个链接以显示剩余的购买数据：

```html
<div class="row" id="<?='purchase' . $key ?>"
style="display:none;">
<table>
<tr>
<th>交易</th><th>日期</th><th>数量</th>
<th>价格</th><th>产品</th>
</tr>
<?php $count = 0; ?>
<?php $first = TRUE; ?>
<?php foreach ($data['purchases'] as $purchase) : ?>
<?php if ($count > SALROWS_PER_PAGE && $first) : ?>
<?php $first = FALSE; ?>
<?php $subId = 'subrow' . $key; ?>
</table>
<a href="#" onClick="showOrHide('<?=' $subId ?>')">更多</a>
<div id="<?=' $subId ?>" style="display:none;">
<table>
<?php endif; ?>
<?php $class = ($count++ & 01) ? 'color1' : 'color2'; ?>
<tr>
<td class="<?= $class ?>"><<?= $purchase['transaction'] ?>></td>
<td class="<?= $class ?>"><<?= $purchase['date'] ?>></td>
<td class="<?= $class ?>"><<?= $purchase['quantity'] ?>></td>
<td class="<?= $class ?>"><<?= $purchase['sale_price'] ?>></td>
<td class="<?= $class ?>"><<?= $purchase['title'] ?>></td>
</tr>
<?php endforeach; ?>
</table>
<?php if (!$first) : ?></div><?php endif; ?>
</div>
```

10. 然后我们添加一个按钮，当点击时，它会显示隐藏的 `<div>` 标签：

```html
<input type="button" value="购买" class="buttonRight"
onClick="showOrHide('<?=' 'purchase' . $key ?>')">
```

## 工作原理...

将步骤 1 到 5 中描述的代码放入一个文件 `chap_10_html_table_multi_array_hidden.php` 中。

就在 `while()` 循环内部，添加以下内容：

```php
printf('%6s : %20s : %8s : %20s', PHP_EOL,
$row['id'], $row['name'], $row['transaction'], $row['title']);
```

在 `while()` 循环刚刚结束的地方，添加一个 `exit` 命令。这是输出结果：

![](img/39390f6d56c5a83b28db083a8bd5185c_411_0.png)

你会注意到，基本的客户信息（如 ID 和姓名）在每个结果行中重复出现，但购买信息（如交易和产品标题）则各不相同。请继续移除 `printf()` 语句。

用以下内容替换 `exit` 命令：

```php
echo '<pre>', var_dump($result), '</pre>' ; exit ;
```

以下是新组成的三维数组的样子：

```text
array(6) {
[6]=>
array(5) {
["name"]=>
string(15) "Spencer Sanford"
["balance"]=>
string(5) "99.99"
["email"]=>
string(28) "spencer.sanford@cable.net"
["phone"]=>
string(12) "451-815-7386"
["purchases"]=>
array(92) {
[0]=>
array(5) {
["transaction"]=>
string(7) "TXN5092"
["date"]=>
string(19) "2016-09-12 05:46:16"
["quantity"]=>
string(2) "44"
["sale_price"]=>
string(5) "10.50"
["title"]=>
string(19) "Gingerbread Cookies"
}
[1]=>
array(5) {
["transaction"]=>
string(7) "ZNW5593"
["date"]=>
string(19) "2015-09-18 03:58:26"
```

现在你可以添加步骤 5 到 7 中显示的显示逻辑。如前所述，虽然你正在显示所有数据，但视觉显示并不直观。现在请继续添加剩余步骤中提到的改进措施。初始输出可能如下所示：

![](img/39390f6d56c5a83b28db083a8bd5185c_412_0.png)

当点击 **Purchases** 按钮时，初始购买信息显示出来。如果点击 **More** 链接，剩余的购买信息将显示：

| **字段** | **值** |
| :--- | :--- |
| **余额** | 888888.00 |
| **电子邮件** | Conrad.perry@fastmedia.com |
| **电话** | 484-181-9811 |
| **总购买额** | 3,038.90 |

| **交易** | **日期** | **数量** | **价格** | **产品** |
| :--- | :--- | :--- | :--- | :--- |
| QJM3659 | 2016-10-27 03:27:28 | 2 | 8.40 | 花生糖 |
| RLiJ437 | 2016-06-10 14:16:22 | 17 | 10.20 | 那不勒斯冰淇淋 |
| ECO1192 | 2015-05-15 08:56:28 | 3 | 17.10 | 巧克力泡芙 |
| ZAM6290 | 2015-10-21 23:11:22 | 18 | 72.00 | 冰淇淋蛋糕 |
| ZNW5593 | 2015-09-18 03:58:26 | 15 | 75.00 | 南瓜冰淇淋 |

**更多**

# 11. 实现软件设计模式

在本章中，我们将涵盖以下主题：

- 创建数组到对象的注水器（Hydrator）
- 构建对象到数组的注水器
- 实现策略模式
- 定义映射器
- 实现对象关系映射
- 实现发布/订阅（Pub/Sub）设计模式

# 简介

将 **软件设计模式** 融入 **面向对象编程（OOP）** 代码的想法最初是在 1994 年著名的“四人组”（E. Gamma, R. Helm, R. Johnson, 和 J. Vlissides）撰写的开创性著作《设计模式：可复用面向对象软件的基础》（*Design Patterns: Elements of Reusable Object-Oriented Software*）中讨论的。该作品既未定义标准也未定义协议，而是识别出了一些多年来被证明有用的通用软件设计。书中讨论的模式通常被认为分为三类：创建型、结构型和行为型。

这些模式中的许多示例已经在本书中展示过。以下是简要总结：

| 设计模式 | 章节 | 案例 |
| :--- | :--- | :--- |
| 单例 | 2 | 定义可见性 |
| 工厂 | 6 | 实现表单工厂 |
| 适配器 | 8 | 不使用 gettext() 处理翻译 |
| 代理 | 7 | 创建简单的 REST 客户端 |
| 代理 | 7 | 创建简单的 SOAP 客户端 |
| 迭代器 | 2 | 递归目录迭代器 |
| 迭代器 | 3 | 使用迭代器 |

在本章中，我们将检查许多其他设计模式，主要关注并发模式和架构模式。

## 创建数组到对象的注水器

**注水器（Hydrator）** 模式是 **数据传输对象（Data Transfer Object）** 设计模式的一种变体。其设计原则非常简单：将数据从一个地方移动到另一个地方。在这个示例中，我们将定义类将数据从数组移动到对象。

## 操作方法...

1.  首先，我们定义一个能够使用 getters 和 setters 的 Hydrator 类。在这个示例中，我们将使用 `Application\Generic\Hydrator\GetSet`：
   ```php
   namespace Application\Generic\Hydrator;
   class GetSet
   {
       // code
   }
   ```

2.  接下来，我们定义一个 `hydrate()` 方法，该方法接受数组和对象作为参数。然后它调用对象上的 `setXXX()` 方法，用数组中的值填充对象。我们使用 `get_class()` 确定对象的类，然后使用 `get_class_methods()` 获取所有方法的列表。`preg_match()` 用于匹配方法前缀及其后缀，随后假定后缀为数组键：
   ```php
   public static function hydrate(array $array, $object)
   {
       $class = get_class($object);
       $methodList = get_class_methods($class);

       foreach ($methodList as $method) {
           preg_match('/^\(set\)(.*?)\$/i', $method, $matches);
           $prefix = $matches[1] ?? '';
           $key     = $matches[2] ?? '';
           $key    = strtolower(substr($key, 0, 1)) . substr($key, 1);
           if ($prefix == 'set' && !empty($array[$key])) {
               $object->$method($array[$key]);
           }
       }
       return $object;
   }
   ```

## 工作原理...

为了演示如何使用数组到对象注水器，首先按照“操作方法...”部分所述定义 `Application\Generic\Hydrator\GetSet` 类。接下来，定义一个可用于测试该概念的实体类。为了说明这个示例，创建一个 `Application\Entity\Person` 类，具有适当的属性和方法。确保为所有属性定义 getters 和 setters。并非在此显示所有此类方法：

```php
namespace Application\Entity;
class Person
{
    protected $firstName = '';
    protected $lastName  = '';
    protected $address   = '';
    protected $city      = '';
    protected $stateProv = '';
    protected $postalCode = '';
    protected $country   = '';

    public function getFirstName()
    {
        return $this->firstName;
    }

    public function setFirstName($firstName)
    {
        $this->firstName = $firstName;
    }

    // 等等。
}
```

现在你可以创建一个名为 `chap_11_array_to_object.php` 的调用程序，它设置自动加载并使用适当的类：

```php
<?php
require __DIR__ . '/../Application/Autoload/Loader.php';
Application\Autoload\Loader::init(__DIR__ . '/../');
use Application\Entity\Person;
use Application\Generic\Hydrator\GetSet;
```

接下来，你可以定义一个测试数组，其中的值将被添加到新的 `Person` 实例中：

```php
$a['firstName']  = 'Li\'l Abner';
$a['lastName']   = 'Yokum';
$a['address']    = '1 Dirt Street';
$a['city']       = 'Dogpatch';
$a['stateProv']  = 'Kentucky';
$a['postalCode'] = '12345';
$a['country']    = 'USA';
```

现在你可以以静态方式调用 `hydrate()` 和 `extract()`：

```php
$b = GetSet::hydrate($a, new Person());
var_dump($b);
```

结果如下面的截图所示：

![](img/39390f6d56c5a83b28db083a8bd5185c_416_0.png)





## 构建对象转数组水合器

本食谱是*创建数组转对象水合器*食谱的逆向操作。在这种情况下，我们需要从对象属性中提取值，并返回一个关联数组，其中键将是列名。

## 操作方法...

- 1. 为了进行说明，我们将在前面食谱中定义的 `Application\Generic\Hydrator\GetSet` 类的基础上进行构建：

```php
namespace Application\Generic\Hydrator;
class GetSet
{
    // code
}
```

- 2. 在前面食谱中定义的 `hydrate()` 方法之后，我们定义一个 `extract()` 方法，该方法接受一个对象作为参数。其逻辑与使用 `hydrate()` 时类似，不同之处在于我们这次是搜索 `getXXX()` 方法。同样，使用 `preg_match()` 来匹配方法前缀及其后缀，随后假设该后缀即为数组键：

```php
public static function extract($object)
{
    $array = array();
    $class = get_class($object);
    $methodList = get_class_methods($class);
    foreach ($methodList as $method) {
        preg_match('/^(get)(.*)$/', $method, $matches);
        $prefix = $matches[1] ?? '';
        $key    = $matches[2] ?? '';
        $key = strtolower(substr($key, 0, 1)) . substr($key, 1);
        if ($prefix == 'get') {
            $array[$key] = $object->$method();
        }
    }
    return $array;
}
```

> 请注意，为了方便起见，我们将 `hydrate()` 和 `extract()` 定义为了静态方法。

## 工作原理...

定义一个名为 `chap_11_object_to_array.php` 的调用程序，该程序设置自动加载并使用相应的类：

```php
<?php
require __DIR__ . '/../Application/Autoload/Loader.php';
Application\Autoload\Loader::init(__DIR__ . '/..');
use Application\Entity\Person;
use Application\Generic\Hydrator\GetSet;
```

接下来，定义一个 `Person` 实例，并为其属性设置值：

```php
$obj = new Person();
$obj->setFirstName('Li\'lAbner');
$obj->setLastName('Yokum');

$obj->setAddress('1DirtStreet');
$obj->setCity('Dogpatch');
$obj->setState('Kentucky');
$obj->setPostalCode('12345');
$obj->setCountry('USA');
```

最后，以静态方式调用新的 `extract()` 方法：

```php
$a = GetSet::extract($obj);
var_dump($a);
```

输出显示在下面的截图中：

![](img/39390f6d56c5a83b28db083a8bd5185c_418_0.png)

## 实现策略模式

通常，运行时条件会迫使开发人员定义执行相同任务的多种方法。传统上，这涉及一个巨大的 if/elseif/else 命令块。您要么在 if 语句内部定义大块逻辑，要么创建一系列函数或方法以启用不同的方法。策略模式试图通过让主要类封装代表解决同一问题不同方法的一系列子类来使这一过程形式化。

## 操作方法...

- 1. 在这个说明中，我们将使用之前定义的 GetSet 水合器类作为一种策略。我们将定义一个主要的 `Application\Generic\Hydrator\Any` 类，该类将消耗 `Application\Generic\Hydrator\Strategy` 命名空间中的策略类，包括 `GetSet`、`PublicProps` 和 `Extending`。

- 2. 我们首先定义反映可用内置策略的类常量：

```php
namespace Application\Generic\Hydrator;
use InvalidArgumentException;
use Application\Generic\Hydrator\Strategy\ { GetSet, PublicProps, Extending };
class Any
{
    const STRATEGY_PUBLIC = 'PublicProps';
    const STRATEGY_GET_SET = 'GetSet';
    const STRATEGY_EXTEND = 'Extending';
    protected $strategies;
    public $chosen;
```

- 3. 然后我们定义一个构造函数，将所有内置策略添加到 `$strategies` 属性中：

```php
public function __construct()
{
    $this->strategies[self::STRATEGY_GET_SET] = new GetSet();
    $this->strategies[self::STRATEGY_PUBLIC] = new PublicProps();
    $this->strategies[self::STRATEGY_EXTEND] = new Extending();
}
```

- 4. 我们还添加了一个 `addStrategy()` 方法，允许我们在不重新编码类的情况下覆盖或添加新策略：

```php
public function addStrategy($key, HydratorInterface $strategy) 
{
    $this->strategies[$key] = $strategy;
}
```

- 5. `hydrate()` 和 `extract()` 方法只是调用所选策略的相应方法：

```php
public function hydrate(array $array, $object)
{
    $strategy = $this->chooseStrategy($object);
    $this->chosen = get_class($strategy);
    return $strategy::hydrate($array, $object);
}

public function extract($object)
{
    $strategy = $this->chooseStrategy($object);
    $this->chosen = get_class($strategy);
    return $strategy::extract($object);
}
```

- 6. 棘手的地方在于确定应选择哪种水合策略。为此，我们定义了 `chooseStrategy()`，该方法接受一个对象作为参数。我们首先通过获取类方法列表进行一些侦探工作。然后我们扫描该列表，查看是否存在任何 `getX()` 或 `setX()` 方法。如果存在，我们选择 `GetSet` 水合器作为所选策略：

```php
public function chooseStrategy($object)
{
    $strategy = NULL;
    $methodList = get_class_methods(get_class($object));
    if (!empty($methodList) && is_array($methodList)) {
        $getSet = FALSE;
        foreach ($methodList as $method) {
            if (preg_match('/^(get|set).*$/', $method)) {
                $strategy = $this->strategies[self::STRATEGY_GET_SET];
                break;
            }
        }
    }
```

- 7. 仍然在我们的 `chooseStrategy()` 方法中，如果没有 getter 或 setter，我们接下来使用 `get_class_vars()` 来确定是否存在可用属性。如果存在，我们选择 `PublicProps` 作为我们的水合器：

```php
if (!$strategy) {
    $vars = get_class_vars(get_class($object));
    if (!empty($vars) && count($vars)) {
        $strategy = $this->strategies[self::STRATEGY_PUBLIC];
    }
}
```

- 8. 如果以上方法都失败，我们回退到 `Extending` 水合器，该水合器返回一个简单地继承对象类的新类，从而使得任何公共或受保护属性可用：

```php
if (!$strategy) {
    $strategy = $this->strategies[self::STRATEGY_EXTEND];
}
return $strategy;
}
```

- 9. 现在我们将注意力转向策略本身。首先，我们定义一个新的 `Application\Generic\Hydrator\Strategy` 命名空间。

- 10. 在新命名空间中，我们定义一个接口，允许我们识别任何可以被 `Application\Generic\Hydrator\Any` 消耗的策略：

```php
namespace Application\Generic\Hydrator\Strategy;
interface HydratorInterface
{
    public static function hydrate(array $array, $object);
    public static function extract($object);
}
```

- 11. GetSet 水合器与前两个食谱中定义的完全相同，唯一的增加是它将实现新的接口：

```php
namespace Application\Generic\Hydrator\Strategy;
class GetSet implements HydratorInterface
{
    public static function hydrate(array $array, $object)
    {
        // defined in the recipe:
        // "Creating an Array to Object Hydrator"
    }
    public static function extract($object)
    {
        // defined in the recipe:
        // "Building an Object to Array Hydrator" 
    }
}
```

- 12. 下一个水合器只是读取和写入公共属性：

```php
namespace Application\Generic\Hydrator\Strategy;
class PublicProps implements HydratorInterface
{
    public static function hydrate(array $array, $object)
    {
        $propertyList = array_keys(
            get_class_vars(get_class($object)));
        foreach ($propertyList as $property) {
            $object->$property = $array[$property] ?? NULL;
        }
        return $object;
    }

    public static function extract($object)
    {
        $array = array();
        $propertyList = array_keys(
            get_class_vars(get_class($object)));
        foreach ($propertyList as $property) {
            $array[$property] = $object->$property;
        }
        return $array;
    }
}
```

- 13. 最后，`Extending` 是水合器的瑞士军刀，它继承对象类，从而提供对属性的直接访问。我们进一步定义魔术 getter 和 setter 以提供对属性的访问。

- 14. `hydrate()` 方法是最困难的，因为我们假设没有定义 getter 或 setter，并且属性也没有定义为公共可见性级别。因此，我们需要定义一个继承要水合的对象的类的新类。我们通过首先定义一个将用作构建新类模板的字符串来实现这一点：

```php
namespace Application\Generic\Hydrator\Strategy;
class Extending implements HydratorInterface
{
    const UNDEFINED_PREFIX = 'undefined';
```





const TEMP_PREFIX = 'TEMP_';
const ERROR_EVAL = 'ERROR: unable to evaluate object';
public static function hydrate(array $array, $object)
{
    $className = get_class($object);
    $components = explode('\\', $className);
    $realClass = array_pop($components);
    $nameSpace = implode('\\', $components);
    $tmpClass = $realClass . self::TEMP_SUFFIX;
    $template = 'namespace '
        . $nameSpace . '{ '
        . 'class ' . $tmpClass
        . ' extends ' . $realClass . ' '
}

15. 继续在 `hydrate()` 方法中，我们定义了一个 `$values` 属性，以及一个构造函数，该构造函数将待水合的数组作为参数赋值给对象。我们遍历该值数组，将值分配给属性。我们还定义了一个有用的 `getArrayCopy()` 方法，它可以在需要时返回这些值，此外还定义了一个魔术方法 `__get()` 来模拟直接属性访问：

```
. '{ '
.   ' protected $values; '
.   ' public function __construct($array) '
.   ' { $this->values = $array; '
.     ' foreach ($array as $key => $value) '
.     ' $this->$key = $value; '
.   ' } '
.   ' public function getArrayCopy() '
.   ' { return $this->values; } '
. '}
```

16. 为了便利，我们定义了一个魔术方法 `__get()`，它模拟了直接的变量访问，就好像它们是公开的一样：

```
. ' public function __get($key) '
. ' { return $this->values[$key] ?? NULL; } '
```

17. 仍然在为新类构建的模板中，我们还定义了一个魔术方法 `__call()`，它模拟了 getter 和 setter：

```
. ' public function __call($method, $params) '
. ' { '
.   ' preg_match("/^([get|set]_)(.*?)/i", '
.     '$method, $matches); '
.   ' $prefix = $matches[1] ?? ""; '
.   ' $key    = $matches[2] ?? ""; '
.   ' $key    = strtolower(substr($key, 0, 1)) '
.     ' . substr($key, 1); '
```

18. 继续在 `__call` 方法中，我们处理 getter 和 setter 的逻辑，然后关闭类定义。我们还添加了代码以结束命名空间：

```
. ' if ($prefix == "get") { '
. ' return $this->values[$key] ?? NULL; '
. ' } else { '
. ' $this->values[$key] = $params[0]; '
. ' } '
. '} '
. ' ' // ends namespace ' . PHP_EOL
```

19. 最后，仍然在新类的模板中，我们在全局命名空间中添加了一个函数，用于构建并返回该类实例：

```
. 'namespace { '
. 'function build($array) '
. '{ return new ' . $namespace . '\\' . $tempClass . '($array); } '
. '} ' // ends global namespace ' . PHP_EOL;
```

20. 仍在 `hydrate()` 方法中，我们使用 `eval()` 执行完成的模板。然后我们运行刚刚在模板末尾定义的 `build()` 方法。注意，由于我们要填充的类的命名空间不确定，我们在全球命名空间中定义并调用 `build()`：

```
try {
    eval($template);
} catch (ParseError $e) {
    error_log(__METHOD__ . ': ' . $e->getMessage());
    throw new Exception(self::ERROR_EVAL);
}
return \build($array);
```

21. 定义 `extract()` 方法要容易得多，因为我们的选择极其有限。扩展一个类并使用魔术方法从数组中填充它很容易实现。反之则不然。如果我们扩展该类，我们将丢失所有的属性值，因为我们是扩展类，而不是对象实例。因此，我们唯一的选项是使用 getter 和公共属性的组合：

```
public static function extract($object)
{
    $array = array();
    $class = get_class($object);
    $methodList = get_class_methods($class);
    foreach ($methodList as $method) {
        preg_match('/^(get)(.*)?$/i', $method, $matches);
        $prefix = $matches[1] ?? '';
        $key    = $matches[2] ?? '';
        $key    = strtolower(substr($key, 0, 1))
                 . substr($key, 1);
        if ($prefix == 'get') {
            $array[$key] = $object->$method();
        }
    }
    $propertyList = array_keys(get_class_vars($class));
    foreach ($propertyList as $property) {
        $array[$property] = $object->$property;
    }
    return $array;
}
```

## 工作原理...

你可以从定义三个具有相同属性的测试类开始：firstName、lastName 等。第一个类 `Person` 应该具有受保护的属性以及 getter 和 setter。第二个类 `PublicPerson` 将具有公共属性。第三个类 `ProtectedPerson` 具有受保护的属性，但没有 getter 或 setter：

```php
<?php
namespace Application\Entity;

class Person
{
    protected $firstName   = '';
    protected $lastName    = '';
    protected $address     = '';
    protected $city        = '';
    protected $stateProv   = '';
    protected $postalCode  = '';
    protected $country     = '';

    public function getFirstName()
    {
        return $this->firstName;
    }

    public function setFirstName($firstName)
    {
        $this->firstName = $firstName;
    }

    // be sure to define remaining getters and setters
}
```

```php
<?php
namespace Application\Entity;

class PublicPerson
{
    private $id = NULL;
    public $firstName = '';
    public $lastName    = '';
    public $address     = '';
    public $city        = '';
    public $stateProv   = '';
    public $postalCode  = '';
    public $country     = '';
}
```

```php
<?php
namespace Application\Entity;

class ProtectedPerson
{
    private $id = NULL;
    protected $firstName   = '';
    protected $lastName    = '';
    protected $address     = '';
    protected $city        = '';
    protected $stateProv   = '';
    protected $postalCode  = '';
    protected $country     = '';
}
```

现在你可以定义一个名为 `chap_11_strategy_pattern.php` 的调用程序，该程序设置自动加载并使用适当的类：

```php
<?php
require __DIR__ . '/../Application/Autoload/Loader.php';
Application\Autoload\Loader::init(__DIR__ . '/../..');
use Application\Entity\{ Person, PublicPerson, ProtectedPerson };
use Application\Generic\Hydrator\Any;
use Application\Generic\Hydrator\Strategy\{ GetSet, Extending,
    PublicProps };
```

接下来，创建一个 `Person` 实例并运行 setter 来定义属性的值：

```php
$objj = new Person();
$objj->setFirstName('Li\'lAbner');
$objj->setLastName('Yokum');
$objj->setAddress('1 Dirt Street');
$objj->setCity('Dogpatch');
$objj->setStateProv('Kentucky');
$objj->setPostalCode('12345');
$objj->setCountry('USA');
```

接下来，创建一个 `Any` 水合器实例，调用 `extract()`，并使用 `var_dump()` 查看结果：

```php
$hydrator = new Any();
$b = $hydrator->extract($objj);
echo "\nChosen Strategy: " . $hydrator->chosen . "\n";
var_dump($b);
```

在以下输出中，观察到选择了 `GetSet` 策略：

![](img/39390f6d56c5a83b28db083a8bd5185c_427_0.png)

> **注意**
> 注意 `id` 属性未设置，因为其可见性级别为私有。

接下来，你可以定义一个具有相同值的数组。在 `Any` 实例上调用 `hydrate()`，并提供一个新的 `PublicPerson` 实例作为参数：

```php
$a = [
    'firstName'  => 'Li\'lAbner',
    'lastName'   => 'Yokum',
    'address'    => '1 Dirt Street',
    'city'       => 'Dogpatch',
    'stateProv'  => 'Kentucky',
    'postalCode' => '12345',
    'country'    => 'USA'
];

$p = $hydrator->hydrate($a, new PublicPerson());
echo "\nChosen Strategy: " . $hydrator->chosen . "\n";
var_dump($p);
```

这是结果。注意，在这种情况下选择了 *PublicProps* 策略：

![](img/39390f6d56c5a83b28db083a8bd5185c_428_0.png)

最后，再次调用 `hydrate()`，但这次提供 *ProtectedPerson* 的实例作为对象参数。然后我们调用 `getFirstName()` 和 `getLastName()` 来测试魔术 getter。我们还通过直接变量访问来获取名字和姓氏：

```php
$q = $hydrator->hydrate($a, new ProtectedPerson());
echo "\nChosen Strategy: " . $hydrator->chosen . "\n";
echo "Name: {$q->getFirstName()} {$q->getLastName()}\n";
echo "Name: {$q->firstName} {$q->lastName}\n";
var_dump($q);
```

这是最后的输出，显示选择了 *Extending* 策略。你还会注意到该实例是一个新的 *ProtectedPerson_TEMP* 类，并且受保护的属性已被完全填充：

![](img/39390f6d56c5a83b28db083a8bd5185c_429_0.png)

## 定义映射器

**映射器** 或 **数据映射器** 的工作方式与水合器非常相似：将数据从一种模型（无论是数组还是对象）转换为另一种模型。一个关键的差异在于，水合器是通用的，不需要预先编写对象属性名称，而映射器则相反：它需要关于两个模型属性名称的精确信息。在这个食谱中，我们将演示如何使用映射器将一个数据库表中的数据转换为另一个表。

### 怎么做...

1. 我们首先定义一个 `Application\Database\Mapper\FieldConfig` 类，其中包含针对单个字段的映射指令。我们还定义了适当的类常量：

```php
namespace Application\Database\Mapper;
use InvalidArgumentException;
class FieldConfig
{
    const ERROR_SOURCE =
        'ERROR: need to specify destTable and/or source';
    const ERROR_DEST = 'ERROR: need to specify either '
        . 'both destTable and destCol or neither';
```




2. 关键属性与相应的类常量一起定义。`$key` 用于标识该对象。`$source` 表示源数据库表中的列。`$destTable` 和 `$destCol` 表示目标数据库表和列。如果定义了 `$default`，它包含一个默认值或用于生成适当值的回调函数：

```php
public $key;
public $source;
public $destTable;
public $destCol;
public $default;
```

3. 现在我们将注意力转向构造函数，它分配默认值，构建键，并检查 `$source` 或 `$destTable` 和 `$destCol` 中是否至少有一个被定义：

```php
public function __construct($source = NULL,
                              $destTable = NULL,
                              $destCol   = NULL,
                              $default   = NULL)
{
    // generate key from source + destTable + destCol
    $this->key = $source . '.' . $destTable . '.' . $destCol;
    $this->source = $source;
    $this->destTable = $destTable;
    $this->destCol = $destCol;
    $this->default = $default;
    if (($destTable && !$destCol) ||
        (!$destTable && $destCol)) {
        throw new InvalidArgumentException(self::ERROR_DEST);
    }
    if (!$destTable && !$source) {
        throw new InvalidArgumentException(
            self::ERROR_SOURCE);
    }
}
```

![](img/39390f6d56c5a83b28db083a8bd5185c_430_0.png)

> 请注意，我们允许源列和目标列为 NULL。这样做的理由是，源表中可能存在某些在目标表中没有位置的列。同样，目标表中可能存在某些在源表中没有表示的强制列。

4. 对于默认值，我们需要检查该值是否为回调函数。如果是，则执行该回调函数；否则，返回直接值。请注意，回调函数的定义应接受一个数据库表行作为参数：

```php
public function getDefault()
{
    if (is_callable($this->default)) {
        return call_user_func($this->default, $row);
    } else {
        return $this->default;
    }
}
```

5. 最后，为了完善这个类，我们为这五个属性中的每一个定义了 getter 和 setter：

```php
public function getKey()
{
    return $this->key;
}

public function setKey($key)
{
    $this->key = $key;
}

// etc.
```

6. 接下来，我们定义一个 `Application\Database\Mapper\Mapping` 映射类，它接受源表和目标表的名称以及一个 `FieldConfig` 对象数组作为参数。稍后你会看到，我们允许目标表属性是一个数组，因为映射可能涉及两个或更多目标表：

```php
namespace Application\Database\Mapper;

class Mapping
{
    protected $sourceTable;
    protected $destTable;
    protected $fields;
    protected $sourceCols;
    protected $destCols;

    public function __construct(
        $sourceTable, $destTable, $fields = NULL
    )
    {
        $this->sourceTable = $sourceTable;
        $this->destTable = $destTable;
        $this->fields = $fields;
    }
```

7. 然后我们为这些属性定义了 getter 和 setter：

```php
public function getSourceTable()
{
    return $this->sourceTable;
}

public function setSourceTable($sourceTable)
{
    $this->sourceTable = $sourceTable;
}

// etc.
```

8. 对于字段配置，我们还需要提供添加单个字段的功能。不需要将 key 作为单独的参数提供，因为它可以从 `FieldConfig` 实例中获取：

```php
public function addField(FieldConfig $field)
{
    $this->fields[$field->getKey()] = $field;
    return $this;
}
```

9. 获取源列名称的数组极其重要。问题在于，源列名称是隐藏在 `FieldConfig` 对象中的属性。因此，当调用此方法时，我们遍历 `FieldConfig` 对象数组，并对每个对象调用 `getSource()` 以获取源列名称：

```php
public function getSourceColumns()
{
    if (!isset($this->sourceCols)) {
        $this->sourceCols = array();
        foreach ($this->getFields() as $field) {
            if (!empty($field->getSource())) {
                $this->sourceCols[$field->getKey()] =
                    $field->getSource();
            }
        }
    }
    return $this->sourceCols;
}
```

10. 我们对 `getDestColumns()` 采用类似的方法。与获取源列列表相比，主要区别在于我们只想要一个特定目标表的列，如果定义了一个以上的目标表，这一点至关重要。我们不需要检查 `$destCol` 是否已设置，因为这已经在 `FieldConfig` 的构造函数中处理了：

```php
public function getDestColumns($table)
{
    if (empty($this->destCols[$table])) {
        foreach ($this->getFields() as $field) {
            if ($field->getDestTable() == $table) {
                $this->destCols[$table][$field->getKey()] =
                    $field->getDestCol();
            }
        }
    }
    return $this->destCols[$table];
}
```

11. 最后，我们定义了一个方法，该方法的第一个参数是表示源表中一行数据的数组。第二个参数是目标表的名称。该方法生成一个准备好插入到目标表中的数据数组。

12. 我们不得不做出决定：默认值（可能由回调函数提供）和源表中的哪个数据优先？我们决定首先测试默认值。如果默认值返回 NULL，则使用源数据。请注意，如果需要进一步处理，应定义回调函数作为默认值。

```php
public function mapData($sourceData, $destTable)
{
    $dest = array();
    foreach ($this->fields as $field) {
        if ($field->getDestTable() == $destTable) {
            $dest[$field->getDestCol()] = NULL;
            $default = $field->getDefault($sourceData);
            if ($default) {
                $dest[$field->getDestCol()] = $default;
            } else {
                $dest[$field->getDestCol()] =
                    $sourceData[$field->getSource()];
            }
        }
    }
    return $dest;
}
```

> 请注意，目标插入中会出现一些源行中不存在的列。在这种情况下，`FieldConfig` 对象的 `$source` 属性保持为 NULL，并提供一个默认值，该值可以是标量值，也可以是回调函数。

13. 现在我们可以定义两个生成 SQL 的方法了。第一个方法将生成一个用于从源表读取的 SQL 语句。该语句将包含用于预处理的占位符（例如，使用 `PDO::prepare()`）：

```php
public function getSourceSelect($where = NULL)
{
    $sql = 'SELECT '
        .
        implode(',', $this->getSourceColumns()) . ' '
        . 'FROM ' . $this->getSourceTable() . ' ';
    if ($where) {
        $where = trim($where);
        if (stripos($where, 'WHERE') !== FALSE) {
            $sql .= $where;
        } else {
            $sql .= 'WHERE ' . $where;
        }
    }
    return trim($sql);
}
```

14. 另一个 SQL 生成方法生成用于特定目标表的预处理语句。请注意，占位符是前面加了":"的列名：

```php
public function getDestInsert($table)
{
    $sql = 'INSERT INTO ' . $table . ' '
        . '( '
        . implode(',', $this->getDestColumns($table))
        . ') '
        . ' VALUES ('
        . implode(': ', $this->getDestColumns($table))
        . ')';
    return trim($sql);
}
```

## 工作原理...

使用步骤 1 到 5 中显示的代码生成一个 `Application\Database\Mapper\FieldConfig` 类。将步骤 6 到 14 中显示的代码放入第二个 `Application\Database\Mapper\Mapping` 类中。

在定义执行映射的调用程序之前，重要的是要考虑源数据库表和目标数据库表。源表 `prospects_11` 的定义如下：

```sql
CREATE TABLE `prospects_11` (
  `id` int(11) NOT NULL AUTO_INCREMENT,
  `first_name` varchar(128) NOT NULL,
  `last_name` varchar(128) NOT NULL,
  `address` varchar(256) DEFAULT NULL,
  `city` varchar(64) DEFAULT NULL,
  `state_province` varchar(32) DEFAULT NULL,
  `postal_code` char(16) NOT NULL,
  `phone` varchar(16) NOT NULL,
  `country` char(2) NOT NULL,
  `email` varchar(250) NOT NULL,
  `status` char(8) DEFAULT NULL,
  `budget` decimal(10,2) DEFAULT NULL,
  `last_updated` datetime DEFAULT NULL,
  PRIMARY KEY (`id`),
  UNIQUE KEY `UNIQ_35730C06E7927C74` (`email`)
) ENGINE=InnoDB DEFAULT CHARSET=utf8;
```

在这个示例中，你可以使用两个目标表，`customer_11` 和 `profile_11`，它们之间是 1:1 的关系：

```sql
CREATE TABLE `customer_11` (
  `id` int(11) NOT NULL AUTO_INCREMENT,
  `name` varchar(256) CHARACTER SET latin1
             COLLATE latin1_general_cs NOT NULL,
  `balance` decimal(10,2) NOT NULL,
  `email` varchar(250) NOT NULL,
  `password` char(16) NOT NULL,
  `status` int(10) unsigned NOT NULL DEFAULT '0',
  `security_question` varchar(250) DEFAULT NULL,
  `confirm_code` varchar(32) DEFAULT NULL,
  `profile_id` int(11) DEFAULT NULL,
  `level` char(3) NOT NULL,
  PRIMARY KEY (`id`),
  UNIQUE KEY `UNIQ_81398E09E7927C74` (`email`)
```





## 实现软件设计模式

为了在 `profile_1` 表和 `customer_1` 表之间建立 1:1 的关系，我们使用回调将 `customer_1::id`、`customer_1::profile_id` 和 `profile_1::id` 的值设置为 `$row['id']` 的值：

```php
$idCallback = function ($row) { return $row['id']; };
$mapper->addField(new FieldConfig('id','customer_1','id', $idCallback))
        ->addField(new FieldConfig(NULL,'customer_1','profile_id', $idCallback))
        ->addField(new FieldConfig('id','profile_1','id',$idCallback));
```

现在，你可以调用相应的方法来生成三条 SQL 语句：一条用于从源表读取数据，另外两条用于向两个目标表插入数据：

```php
$sourceSelect = $mapper->getSourceSelect();
$custInsert = $mapper->getDestInsert('customer_1');
$profileInsert = $mapper->getDestInsert('profile_1');
```

这三条语句可以立即进行准备，以便后续执行：

```php
$sourceStmt = $conn->pdo->prepare($sourceSelect);
$custStmt = $conn->pdo->prepare($custInsert);
$profileStmt = $conn->pdo->prepare($profileInsert);
```

然后我们执行 SELECT 语句，该语句会从源表中生成数据行。在循环中，我们为每个目标表生成插入数据，并执行相应的预编译语句：

```php
$sourceStmt->execute();
while ($row = $sourceStmt->fetch(PDO::FETCH_ASSOC)) {
    $custData = $mapper->mapData($row, 'customer_1');
    $custStmt->execute($custData);
    $profileData = $mapper->mapData($row, 'profile_1');
    $profileStmt->execute($profileData);
    echo "Processing: {$custData['name']}\n";
}
```

以下是生成的三条 SQL 语句：

```sql
SELECT email, first_name, last_name, status, address, city, state, province, postal_code, phone, country_id, id FROM prospects_1
INSERT INTO customer_1 ( email, name, status, level, password, id, profile_id ) VALUES ( :email, :name, :status, :level, :password, :id, :profile_id )
INSERT INTO profile_1 ( address, city, state_province, postal_code, phone, country, photo, id ) VALUES ( :address, :city, :state_province, :postal_code, :phone, :country, :photo, :id )
```

处理结果：
- WILFREDO RICHARDS
- WILLARD ATKINSON
- MANUEL WHITE
- EDGAR SLOAN
- AARON ALSTON
- JEFF CASTRO
- NEAL CHAVEZ
- LEONARD LOVE
- ROLANDO LANDRY
- FREDRICK BEASLEY
- RANDAL STUART
- DARRYL LAWSON
- SEAN DOMINGUEZ
- CARLTON McCALIN

然后，我们可以使用 SQL JOIN 直接从数据库查看数据，以确保关系已得到维护：

![](img/39390f6d56c5a83b28db083a8bd5185c_439_0.png)

## 实现对象关系映射

实现对象之间关系映射主要有两种技术。第一种技术涉及将相关的子对象预加载到父对象中。这种方法的优点是实现简单，并且所有父子信息可立即获取。缺点是可能会消耗大量内存，并且性能曲线会发生偏斜。

第二种技术是在父对象中嵌入二级查找。在这种方法中，当你需要访问子对象时，你会运行一个 getter 来执行二级查找。这种方法的优点是性能需求分布在请求周期的各个阶段，内存使用更容易管理（或可以更容易地管理）。缺点是会产生更多的查询，这意味着数据库服务器的工作量更大。

> 但请注意，我们将展示如何使用**预编译语句**来大大减轻这一缺点。

### 如何做...

让我们看看实现对象关系映射的两种技术。

#### 技术 #1 – 预加载所有子信息

首先，我们将讨论如何通过将所有子信息预加载到父类来实现对象关系映射。为了说明，我们将使用三个相关的数据库表：`customer`、`purchases` 和 `products`：

1. 我们将使用现有的 `Application\Entity\Customer` 类（在第 5 章“与数据库交互”中的*定义与数据库表匹配的实体类*食谱中定义）作为模型来开发 `Application\Entity\Purchase` 类。与之前一样，我们将使用数据库定义作为实体类定义的基础。以下是 `purchases` 表的数据库定义：

```sql
CREATE TABLE `purchases` (
 `id` int(11) NOT NULL AUTO_INCREMENT,
 `transaction` varchar(8) NOT NULL,
 `date` datetime NOT NULL,
 `quantity` int(10) unsigned NOT NULL,
 `sale_price` decimal(8,2) NOT NULL,
 `customer_id` int(11) DEFAULT NULL,
 `product_id` int(11) DEFAULT NULL,
 PRIMARY KEY (`id`),
 KEY `IDX_C3F3` (`customer_id`),
 KEY `IDX_C3F3` (`product_id`)
) ENGINE=InnoDB AUTO_INCREMENT=80 DEFAULT CHARSET=utf8
COMMENT='Purchases';
```





### 基于客户实体类，以下是 `Application\Entity\Purchase` 类的可能形式。请注意，并非展示了所有的 getter 和 setter：

```php
namespace Application\Entity;

class Purchase extends Base
{
    const TABLE_NAME = 'purchases';

    protected $transaction = '';
    protected $date = NULL;
    protected $quantity = 0;
    protected $salePrice = 0.0;
    protected $customerId = 0;
    protected $productId = 0;

    protected $mapping = [
        'id'            => 'id',
        'transaction'   => 'transaction',
        'date'          => 'date',
        'quantity'      => 'quantity',
        'sale_price'    => 'salePrice',
        'customer_id'   => 'customerId',
        'product_id'    => 'productId',
    ];

    public function getTransaction() : string
    {
        return $this->transaction;
    }

    public function setTransaction($transaction)
    {
        $this->transaction = $transaction;
    }

    // NOTE: other getters / setters are not shown here
}
```

### 现在，我们准备定义 `Application\Entity\Product`。以下是 `products` 表的数据库定义：

```sql
CREATE TABLE `products` (
`id` int(11) NOT NULL AUTO_INCREMENT,
`sku` varchar(16) DEFAULT NULL,
`title` varchar(255) NOT NULL,
`description` varchar(4096) DEFAULT NULL,
`price` decimal(10,2) NOT NULL,
`special` int(11) NOT NULL,
`link` varchar(128) NOT NULL,
PRIMARY KEY (`id`),
UNIQUE KEY `UNIQ_38C4` (`sku`)
);
```

### 基于客户实体类，以下是 `Application\Entity\Product` 类的可能形式：

```php
namespace Application\Entity;

class Product extends Base
{
    const TABLE_NAME = 'products';
    protected $sku = '';
    protected $title = '';
    protected $description = '';
    protected $price = 0.0;
    protected $special = 0;
    protected $link = '';

    protected $mapping = [
        'id'          => 'id',
        'sku'         => 'sku',
        'title'       => 'title',
        'description' => 'description',
        'price'       => 'price',
        'special'     => 'special',
        'link'        => 'link',
    ];

    public function getSku() : string
    {
        return $this->sku;
    }
    
    public function setSku($sku)
    {
        $this->sku = $sku;
    }

    // NOTE: other getters / setters are not shown here
}
```

### 接下来，我们需要实现一种嵌入相关对象的方法。我们将从 `Application\Entity\Customer` 父类开始。对于本章节，我们将假设以下关系，如下方图示所示：

- 一个客户，多笔购买记录
- 一笔购买记录，一个产品

![](img/39390f6d56c5a83b28db083a8bd5185c_443_0.png)

### 因此，我们定义处理以对象数组形式存在的购买记录的 getter 和 setter：

```php
protected $purchases = array();

public function addPurchase($purchase)
{
    $this->purchases[] = $purchase;
}

public function getPurchases()
{
    return $this->purchases;
}
```

### 现在我们将注意力转向 `Application\Entity\Purchase`。在这种情况下，购买记录和产品之间存在 1:1 关系，因此无需处理数组。

```php
protected $product = NULL;

public function getProduct()
{
    return $this->product;
}

public function setProduct(Product $product)
{
    $this->product = $product;
}
```

请注意，在两个实体类中，我们都未修改 $mapping 数组。这是因为实现对象关系映射与实体属性名称和数据库列名称之间的映射无关。

### 由于获取基本客户信息的核心功能仍然需要，我们只需扩展第 5 章“与数据库交互”中“将实体类绑定到 RDBMS 查询”食谱中描述的 `Application\Database\CustomerService` 类。我们可以创建一个新的 `Application\Database\CustomerOrmService_1` 类，它继承自 `Application\Database\CustomerService`：

```php
namespace Application\Database;
use PDO;
use PDOException;
use Application\Entity\Customer;
use Application\Entity\Product;
use Application\Entity\Purchase;

class CustomerOrmService_1 extends CustomerService
{
    // add methods here
}
```

### 然后，我们在新的服务类中添加一个方法，该方法执行查找并将结果以 `Product` 和 `Purchase` 实体的形式嵌入到核心客户实体中。该方法以 JOIN 的形式执行查找。这是可行的，因为购买记录和产品之间存在 1:1 关系。由于两个表中的 `id` 列同名，我们需要将购买 ID 列作为别名添加。然后我们遍历结果，创建 `Product` 和 `Purchase` 实体。在覆盖 ID 之后，我们可以将 `Product` 实体嵌入到 `Purchase` 实体中，然后将 `Purchase` 实体添加到 `Customer` 实体中的数组中：

```php
protected function fetchPurchasesForCustomer(Customer $cust)
{
    $sql = 'SELECT u.*, r.*, u.id AS purch_id '
         . 'FROM purchases AS u '
         . 'JOIN products AS r '
         . 'ON r.id = u.product_id '
         . 'WHERE u.customer_id = :id '
         . 'ORDER BY u.date';
    
    $stmt = $this->connection->pdo->prepare($sql);
    $stmt->execute(['id' => $cust->getId()]);
    
    while ($result = $stmt->fetch(PDO::FETCH_ASSOC)) {
        $product = Product::arrayToEntity($result, new Product());
        $product->setId($result['product_id']);
        
        $purch = Purchase::arrayToEntity($result, new Purchase());
        $purch->setId($result['purch_id']);
        $purch->setProduct($product);
        $cust->addPurchase($purch);
    }
    
    return $cust;
}
```

### 接下来，我们为原始的 `fetchById()` 方法提供一个包装器。这段代码不仅需要获取原始的 `Customer` 实体，还需要查找并嵌入 `Product` 和 `Purchase` 实体。我们可以调用新的 `fetchByIdAndEmbedPurchases()` 方法，并接受客户 ID 作为参数：

```php
public function fetchByIdAndEmbedPurchases($id)
{
    return $this->fetchPurchasesForCustomer(
        $this->fetchById($id)
    );
}
```

## 技巧 #2 – 嵌入次要查找

现在我们将介绍如何将次要查找嵌入到相关实体类中。我们将继续使用与上述相同的图示，使用对应于三个相关数据库表的实体类定义：`customer`、`purchases` 和 `products`：

### 这种方法的机制与前一节描述的非常相似。主要区别在于，我们不会立即执行数据库查找并生成实体类，而是嵌入一系列匿名函数，这些函数将执行相同的工作，但由视图逻辑调用。

### 我们需要在 `Application\Entity\Customer` 类中添加一个新方法，该方法向 purchases 属性添加单个条目。而不是 `Purchase` 实体数组，我们将提供一个匿名函数：

```php
public function setPurchases(Closure $purchaseLookup)
{
    $this->purchases = $purchaseLookup;
}
```

### 接下来，我们将复制 `Application\Database\CustomerOrmService_1` 类，并将其命名为 `Application\Database\CustomerOrmService_2`：

```php
namespace Application\Database;
use PDO;
use PDOException;
use Application\Entity\Customer;
use Application\Entity\Product;
use Application\Entity\Purchase;

class CustomerOrmService_2 extends CustomerService
{
    // code
}
```

### 然后，我们定义一个 `fetchPurchaseById()` 方法，该方法根据 ID 查找单个购买记录并生成一个 `Purchase` 实体。由于我们将最终在此方法中进行一系列对单个购买记录的重复请求，我们可以通过使用相同的预编译语句（在此情况下为正确调用的 `$purchPreparedStmt`）来提高数据库效率：

```php
public function fetchPurchaseById($purchId)
{
    if (!$this->purchPreparedStmt) {
        $sql = 'SELECT * FROM purchases WHERE id = :id';
        $this->purchPreparedStmt = 
            $this->connection->pdo->prepare($sql);
    }
    $this->purchPreparedStmt->execute(['id' => $purchId]);
    $result = $this->purchPreparedStmt->fetch(PDO::FETCH_ASSOC);
    return Purchase::arrayToEntity($result, new Purchase());
}
```

### 之后，我们需要一个 `fetchProductById()` 方法，该方法根据 ID 查找单个产品并生成一个 `Product` 实体。鉴于客户可能多次购买同一产品，我们可以通过将获取的产品实体存储在 `$products` 数组中来引入额外的效率。此外，与购买记录一样，我们可以使用相同的预编译语句执行查找：

```php
public function fetchProductById($prodId)
{
    if (!isset($this->products[$prodId])) {
        if (!$this->prodPreparedStmt) {
            $sql = 'SELECT * FROM products WHERE id = :id';
            $this->prodPreparedStmt = 
                $this->connection->pdo->prepare($sql);
        }
        $this->prodPreparedStmt->execute(['id' => $prodId]);
        $result = $this->prodPreparedStmt
            ->fetch(PDO::FETCH_ASSOC);
        $this->products[$prodId] = 
            Product::arrayToEntity($result, new Product());
    }
    return $this->products[$prodId];
}
```



6. 我们现在可以重构 `fetchPurchasesForCustomer()` 方法，使其嵌入一个匿名函数，该函数同时调用 `fetchPurchaseById()` 和 `fetchProductById()`，然后将生成的产品实体赋值给新找到的购买实体。在此示例中，我们执行初始查找，仅返回该客户所有购买的 ID。然后，我们在 Customer::$purchases 属性中嵌入一系列匿名函数，将购买 ID 存储为数组键，将匿名函数作为其值：

```php
public function fetchPurchasesForCustomer(Customer $cust)
{
    $sql = 'SELECT id '
          . 'FROM purchases AS u '
          . 'WHERE u.customer_id = :id '
          . 'ORDER BY u.date';
    $stmt = $this->connection->pdo->prepare($sql);
    $stmt->execute(['id' => $cust->getId()]);
    while ($result = $stmt->fetch(PDO::FETCH_ASSOC)) {
        $cust->addPurchaseLookup(
            $result['id'],
            function ($purchId, $service) {
                $purchase = $service->fetchPurchaseById($purchId);
                $product = $service->fetchProductById(
                    $purchase->getProductId());
                $purchase->setProduct($product);
                return $purchase; }
        );
    }
    return $cust;
}
```

### 工作原理…

根据本食谱的步骤，定义以下类如下：

| 类 | 技术 #1 步骤 |
| --- | --- |
| Application\Entity\Purchase | 1 - 2, 7 |
| Application\Entity\Product | 3 - 4 |
| Application\Entity\Customer | 6, 16, + 在第 5 章 *与数据库交互* 中描述的内容。 |
| Application\Database\CustomerOrmService_1 | 8 - 10 |

## 实现软件设计模式

这种方法的第二种实现方式如下：

| **类** | **技术 #2 步骤** |
|---|---|
| `Application\Entity\Customer` | **2** |
| `Application\Database\CustomerOrmService_2` | **3 – 6** |

为了实现方法 **#1**（其中嵌入了实体），定义一个名为 **chap_11_orm_embedded.php** 的调用程序，该程序设置自动加载并使用适当的类：

```php
<?php
define('DB_CONFIG_FILE', '/../config/db.config.php');
require __DIR__ . '/../Application/Autoload/Loader.php';
Application\Autoload\Loader::init(__DIR__ . '../');
use Application\Database\Connection;
use Application\Database\CustomerOrmService_1;
```

接下来，创建一个服务实例，并使用随机 ID 查找客户：

```php
$service = new CustomerOrmService_1(
    new Connection(include __DIR__ . DB_CONFIG_FILE));
$id = rand(1,79);
$cust = $service->fetchByIdAndEmbedPurchases($id);
```

在视图逻辑中，你将通过 `fetchByIdAndEmbedPurchases()` 方法获取一个完全填充的 `Customer` 实体。现在你只需要调用正确的 getter 方法来显示信息：

```html
<!-- Customer Info -->
<h1><?php echo $cust->getName() ?></h1>
<div class="row">
    <div class="left">余额：</div><div class="right">
        <?php echo $cust->getBalance() ?></div>
</div>
<!-- 等等 -->
```

显示购买信息所需的逻辑看起来像以下 HTML 代码。请注意，`Customer::getPurchases()` 返回一个 `Purchase` 实体数组。要从 `Purchase` 实体获取产品信息，在循环内部调用 `Purchase::getProduct()`，这将产生一个 `Product` 实体。然后你可以调用 `Product` 的任何 getter，在本例中为 `Product::getTitle()`：

```html
<!-- Purchases Info -->
<table>
    <?php foreach ($cust->getPurchases() as $purchase) : ?>
    <tr>
        <td><?php echo $purchase->getTransaction() ?></td>
        <td><?php echo $purchase->getDate() ?></td>
        <td><?php echo $purchase->getQuantity() ?></td>
        <td><?php echo $purchase->getSalePrice() ?></td>
        <td><?php echo $purchase->getProduct()->getTitle() ?></td>
    </tr>
    <?php endforeach; ?>
</table>
```

将注意力转向第二种方法，该方法使用二级查找，定义一个名为 `chap_11_orm_secondary_lookups.php` 的调用程序，该程序设置自动加载并使用适当的类：

```php
<?php
define('DB_CONFIG_FILE', './../config/db_config.php');
require __DIR__ . './../Application/Autoload/Loader.php';
Application\Autoload\Loader::init(__DIR__ . './../');
use Application\Database\Connection;
use Application\Database\CustomerOrmService_2;
```

接下来，创建一个服务实例，并使用随机 ID 查找客户：

```php
$service = new CustomerOrmService_2(new Connection(include __DIR__ . DB_CONFIG_FILE));
$id = rand(1,79);
```

现在你可以检索 `Application\Entity\Customer` 实例并为此客户调用 `fetchPurchasesForCustomer()`，它会嵌入匿名函数的序列：

```php
$cust = $service->fetchById($id);
$cust = $service->fetchPurchasesForCustomer($cust);
```

显示核心客户信息的视图逻辑与之前描述的一样。显示购买信息所需的逻辑看起来像以下 HTML 代码片段。请注意，`Customer::getPurchases()` 返回一个匿名函数数组。每次函数调用返回一个特定的购买及相关产品：

```html
<table>
<?php foreach($cust->getPurchases() as $purchaseId => $function) : ?>
<tr>
    <?php $purchase = $function($purchaseId, $service); ?>
    <td><?php echo $purchase->getTransaction() ?></td>
    <td><?php echo $purchase->getDate() ?></td>
    <td><?php echo $purchase->getQuantity() ?></td>
    <td><?php echo $purchase->getSalePrice() ?></td>
    <td><?php echo $purchase->getProduct()->getTitle() ?></td>
</tr>
<?php endforeach; ?>
</table>
```

这是一个输出示例：

![](img/39390f6d56c5a83b28db083a8bd5185c_450_0.png)

## 最佳实践

虽然循环的每次迭代代表两个独立的数据库查询（一个用于购买，一个用于产品），但通过使用预处理语句保留了效率。预先准备了两个语句：一个用于查找特定购买，另一个用于查找特定产品。然后多次执行这些预处理语句。此外，每个产品检索都独立存储在数组中，从而实现了更高的效率。

![](img/39390f6d56c5a83b28db083a8bd5185c_450_1.png)

### 另请参见

实现对象关系映射的库的最佳示例可能是 Doctrine。Doctrine 使用一种嵌入方法，其文档称之为代理。有关更多信息，请参见 http://www.doctrine-project.org/projects/orm.html。

你也许还可以考虑复习 *学习 Doctrine* 的培训视频，该视频可从 O'Reilly Media 获取，网址为 http://shop.oreilly.com/product/0636920041382.do。（免责声明：这是本书和该视频作者的无节制推销！）

## 实现发布/订阅设计模式

**发布/订阅（Pub/Sub）** 设计模式通常构成软件事件驱动编程的基础。这种方法允许不同的软件应用程序之间，或单个应用程序内的不同软件模块之间进行**异步**通信。该模式的目的允许方法或函数在发生重要操作时发布信号。然后一个或多个类会订阅，并在特定信号发布时采取相应行动。

此类操作的示例包括数据库被修改时，或用户登录时。这种设计模式的另一个常见用途是当应用程序发布新闻源时。如果紧急新闻项目已发布，应用程序会发布这一事实，允许客户端订阅者刷新他们的新闻列表。

## 实现方法...

- 1. 首先，我们定义我们的发布者类，`Application\PubSub\Publisher`。您会注意到我们正在使用两个有用的 **标准 PHP 库 (SPL)** 接口，`SplSubject` 和 `SplObserver`：

```php
namespace Application\PubSub;
use SplSubject;
use SplObserver;
class Publisher implements SplSubject
{
// 代码
}
```

- 2. 接下来，我们添加属性来表示发布者名称、传递给订阅者的数据以及订阅者数组（也称为监听器）。您还会注意到我们将使用链表（在*第 10 章，查看高级算法*中描述）来允许优先级：

```php
protected $name;
protected $data;
protected $linked;
protected $subscribers;
```



### 3. 构造函数用于初始化这些属性。我们还会加入 `__toString()`，以便在需要时快速访问该发布者的名称：

```php
public function __construct($name)
{
    $this->name = $name;
    $this->data = array();
    $this->subscribers = array();
    $this->linked = array();
}

public function __toString()
{
    return $this->name;
}
```

### 4. 为了将订阅者与发布者关联起来，我们定义了 `attach()`，该函数在 `SplSubject` 接口中有所规定。我们接受一个 `SplObserver` 实例作为参数。注意，我们需要向 `$subscribers` 和 `$linked` 属性中添加条目。随后，使用 `arsort()` 按值（即优先级）对 `$linked` 进行排序，`arsort()` 会进行降序排序并保留键值：

```php
public function attach(SplObserver $subscriber)
{
    $this->subscribers[$subscriber->getKey()] = $subscriber;
    $this->linked[$subscriber->getKey()] =
        $subscriber->getPriority();
    arsort($this->linked);
}
```

### 5. 接口还要求我们定义 `detach()`，用于从列表中移除订阅者：

```php
public function detach(SplObserver $subscriber)
{
    unset($this->subscribers[$subscriber->getKey()]);
    unset($this->linked[$subscriber->getKey()]);
}
```

### 6. 同样基于接口的要求，我们定义了 `notify()`，它会调用所有订阅者的 `update()`。注意，我们遍历链表以确保订阅者按优先级顺序被调用：

```php
public function notify()
{
    foreach($this->linked as $key => $value)
    {
        $this->subscribers[$key]->update($this);
    }
}
```

### 7. 接下来，我们定义相应的 getter 和 setter。为了节省篇幅，这里没有展示所有代码：

```php
public function getName()
{
    return $this->name;
}

public function setName($name)
{
    $this->name = $name;
}
```

### 8. 最后，我们需要提供一种按键设置数据项的方法，这些数据项将在调用 `notify()` 时供订阅者使用：

```php
public function setDataByKey($key, $value)
{
    $this->data[$key] = $value;
}
```

### 9. 现在我们可以查看 `Application\PubSub\Subscriber`。通常，我们会为每个发布者定义多个订阅者。在这种情况下，我们实现了 `SplObserver` 接口：

```php
namespace Application\PubSub;
use SplSubject;
use SplObserver;
class Subscriber implements SplObserver
{
    // code
}
```

### 10. 每个订阅者都需要一个唯一的标识符。在这里，我们使用 `md5()` 结合日期/时间信息以及一个随机数来创建键。构造函数按如下方式初始化属性。订阅者执行的实际逻辑功能形式为回调：

```php
protected $key;
protected $name;
protected $priority;
protected $callback;
public function __construct(
    string $name, callable $callback, $priority = 0)
{
    $this->key = md5(date('YmdHis') . rand(0,9999));
    $this->name = $name;
    $this->callback = $callback;
    $this->priority = $priority;
}
```

### 11. 当发布者的 `notify()` 被调用时，`update()` 函数会被触发。

我们传入一个发布者实例作为参数，并调用为该订阅者定义的回调：

```php
public function update(SplSubject $publisher)
{
    call_user_func($this->callback, $publisher);
}
```

### 12. 我们还需要定义 getter 和 setter 以方便使用。并非所有都展示于此：

```php
public function getKey()
{
    return $this->key;
}

public function setKey($key)
{
    $this->key = $key;
}

// other getters and setters not shown
```

## 工作原理...

为了说明目的，定义一个名为 `chap_11_pub_sub_simple_example.php` 的调用程序，它设置自动加载并使用适当的类：

```php
<?php
require __DIR__ . '/../Application/Autoload/Loader.php';
Application\Autoload\Loader::init(__DIR__ . '/../');
use Application\PubSub\{ Publisher, Subscriber };
```

接下来，创建一个发布者实例并分配数据：

```php
$pub = new Publisher('test');
$pub->setDataByKey('1', 'AAA');
$pub->setDataByKey('2', 'BBB');
$pub->setDataByKey('3', 'CCC');
$pub->setDataByKey('4', 'DDD');
```

现在你可以创建测试订阅者，它们从发布者读取数据并回显结果。第一个参数是名称，第二个是回调，最后一个是优先级：

```php
$sub1 = new Subscriber(
    '1',
    function ($pub) {
        echo '1:' . $pub->getData()[1] . PHP_EOL;
    },
    10
);
$sub2 = new Subscriber(
    '2',
    function ($pub) {
        echo '2:' . $pub->getData()[2] . PHP_EOL;
    },
    20
);
$sub3 = new Subscriber(
    '3',
    function ($pub) {
        echo '3:' . $pub->getData()[3] . PHP_EOL;
    },
    99
);
```

为了测试目的，乱序附加订阅者，并调用两次 `notify()`：

```php
$pub->attach($sub2);
$pub->attach($sub1);
$pub->attach($sub3);
$pub->notify();
$pub->notify();
```

接下来，定义并附加另一个订阅者，该订阅者检查订阅者 1 的数据，如果非空则退出：

```php
$sub4 = new Subscriber(
    '4',
    function ($pub) {
        echo '4:' . $pub->getData()[4] . PHP_EOL;
        if (!empty($pub->getData()[1]))
            die('1 is set ... halting execution');
    },
    25
);
$pub->attach($sub4);
$pub->notify();
```

以下是输出结果。注意，输出是按优先级顺序排列的（优先级较高的排在前面），并且第二块输出被中断了：

![](img/39390f6d56c5a83b28db083a8bd5185c_456_0.png)

## 更多内容...

一种密切相关的软件设计模式是**观察者（Observer）**模式。其机制相似，但通常公认的区别在于，观察者模式以同步方式运行，当接收到信号（通常也称为消息或事件）时，所有观察者方法都会被调用。相比之下，发布/订阅（Pub/Sub）模式是异步运行的，通常使用消息队列。另一个区别是，在发布/订阅模式中，发布者不需要知道订阅者的存在。

## 参见

关于观察者模式和发布/订阅模式之间差异的良好讨论，请参阅 [http://stackoverflow.com/questions/15594905/difference-between-observer-pub-sub-and-data-binding](http://stackoverflow.com/questions/15594905/difference-between-observer-pub-sub-and-data-binding) 上的文章。

# 12 提升 Web 安全性

在本章中，我们将涵盖以下主题：

- 过滤 `$_POST` 数据
- 验证 `$_POST` 数据
- 保护 PHP 会话
- 使用令牌保护表单
- 构建安全的密码生成器
- 使用 CAPTCHA 保护表单
- 不使用 `mcrypt` 进行加密/解密

## 介绍

在本章中，我们将向你展示如何设置一种简单但有效的机制来过滤和验证一组 POST 数据。然后，我们将介绍如何保护你的 PHP 会话免受潜在的会话劫持和其他形式的攻击。下一个食谱展示了如何使用随机生成的令牌来保护表单免受**跨站请求伪造（CSRF）**攻击。

关于密码生成的食谱展示了如何将 PHP 7 的 true randomization（真随机数生成）结合使用来生成安全的密码。然后我们向你展示了两种形式的**CAPTCHA**：一种基于文本，另一种使用扭曲图像。最后，有一个食谱涵盖了在不使用已被诟病且即将弃用的 `mcrypt` 扩展的情况下进行强加密。

## 过滤 `$_POST` 数据

数据过滤过程可以包含以下任何一项或全部内容：

- 移除不需要的字符（即移除 `<script>` 标签）
- 对数据执行转换（即把引号转换为 `&quot;`）
- 加密或解密数据

加密在本章的最后一个食谱中进行了讨论。除此之外，我们将展示一种基本机制，可用于过滤表单提交后到达的 `$_POST` 数据。

### 如何实现...

1. 首先，你需要了解将存在于 `$_POST` 中的数据。另外，也许更重要的是，你需要了解存储表单数据的数据库表所施加的限制。作为一个例子，请查看 `prospects` 表的数据库结构：

| COLUMN | TYPE | NULL | DEFAULT |
|---|---|---|---|
| first_name | varchar(128) | No | None |
| last_name | varchar(128) | No | None |
| address | varchar(256) | Yes | None |
| city | varchar(64) | Yes | None |
| state_province | varchar(32) | Yes | None |
| postal_code | char(16) | No | None |
| phone | varchar(16) | No | None |
| country | char(2) | No | None |
| email | varchar(250) | No | None |
| status | char(8) | Yes | None |
| budget | decimal(10,2) | Yes | None |
| last_updated | datetime | Yes | None |

2. 一旦你完成了对要发送和存储的数据的分析，你就可以确定需要执行何种类型的过滤，以及哪些 PHP 函数将服务于这一目的。

3. 作为一个例子，如果你需要去掉用户提供的表单数据中完全可能存在的前导和尾部空白，你可以使用 PHP 的 `trim()` 函数。所有字符数据根据数据库结构都有长度限制。相应地，你可能需要考虑使用 `substr()` 以确保长度不被超过。如果你想要移除非字母字符，你可能需要考虑使用带有适当模式的 `preg_replace()`。




4. 现在我们可以将所需的 PHP 函数集组合成一个单一的回调数组。下面是一个基于最终将存储在 *prospects* 表中的表单数据的过滤需求的示例：

```php
$filter = [
    'trim' => function ($item) { return trim($item); },
    'float' => function ($item) { return (float) $item; },
    'upper' => function ($item) { return strtoupper($item); },
    'email' => function ($item) {
        return filter_var($item, FILTER_SANITIZE_EMAIL);
    },
    'alpha' => function ($item) {
        return preg_replace('/[^A-Za-z]/', '', $item);
    },
    'alnum' => function ($item) {
        return preg_replace('/[^0-9A-Za-z ]/', '', $item);
    },
    'length' => function ($item, $length) {
        return substr($item, 0, $length);
    },
    'stripTags' => function ($item) { return strip_tags($item); },
];
```

5. 接下来，我们定义一个数组，该数组与 `$POST` 中预期的字段名称相匹配。在这个数组中，我们指定 `$filter` 数组中的键以及任何参数。注意第一个键 `*`。我们将把它用作通配符，应用于所有字段：

```php
$assignments = [
    '*'              => ['trim' => NULL, 'stripTags' => NULL],
    'first_name'     => ['length' => 32, 'alnum' => NULL],
    'last_name'      => ['length' => 32, 'alnum' => NULL],
    'address'        => ['length' => 64, 'alnum' => NULL],
    'city'           => ['length' => 32],
    'state_province'=> ['length' => 20],
    'postal_code'    => ['length' => 12, 'alnum' => NULL],
    'phone'          => ['length' => 12],
    'country'        => ['length' => 2, 'alpha' => NULL,
                         'upper' => NULL],
    'email'          => ['length' => 128, 'email' => NULL],
    'budget'         => ['float' => NULL],
];
```

6. 然后，我们遍历数据集（即来自 `$POST` 的数据），并依次应用回调。我们首先运行分配给通配符（`*`）键的所有回调。

> 实现通配符过滤器非常重要，可以避免冗余设置。在上面的示例中，我们希望为每一项应用代表 PHP 函数 `strip_tags()` 和 `trim()` 的过滤器。

7. 接下来，我们运行分配给特定数据字段的所有回调。完成后，`$data` 中的所有值都将被过滤：

```php
foreach ($data as $field => $item) {
    foreach ($assignments['*'] as $key => $option) {
        $item = $filter[$key]($item, $option);
    }
    foreach ($assignments[$field] as $key => $option) {
        $item = $filter[$key]($item, $option);
    }
}
```

## 工作原理...

将步骤 4 到 6 中显示的代码放入一个名为 `chap_12_post_data_filtering_basic.php` 的文件中。您还需要定义一个数组来模拟 `$POST` 中可能存在的数据。在这种情况下，您可以定义两个数组，一个包含良好数据，另一个包含不良数据：

```php
$testData = [
    'goodData' => [
        'first_name' => 'Doug',
        'last_name' => 'Bierer',
        'address' => '123 Main Street',
        'city' => 'San Francisco',
        'state_province' => 'California',
        'postal_code' => '94101',
        'phone' => '+1 415-555-1212',
        'country' => 'US',
        'email' => 'doug@unlikelysource.com',
        'budget' => '123.45',
    ],
    'badData' => [
        'first_name' => 'This+Name<script>bad tag</script>Valid!',
        'last_name' =>
        'ThisLastNameIsWayTooLongAbcdefghijklmnopqrstuvwxyz0123456789
        Abcdefghijklmnopqrstuvwxyz0123456789Abcdefghijklmnopqrstuvwxyz
        0123456789Abcdefghijklmnopqrstuvwxyz0123456789 ',
        // 'address' => '', // missing
        'city' => 'ThisCityNameIsTooLong01234567890123456
        7890123456789012345678901234567890123456789 ',
        // 'state_province' => '', // missing
        'postal_code' => '!"£$%^"Non Alpha Chars',
        'phone' => '12345 ',
        'country' => '12345',
        'email' => 'this.is@not@an.email',
        'budget' => 'XXX',
    ]
];
```

最后，您需要遍历过滤分配，展示良好数据和不良数据：

```php
foreach ($testData as $data) {
    foreach ($data as $field => $item) {
        foreach ($assignments['*'] as $key => $option) {
            $item = $filter[$key]($item, $option);
        }
        foreach ($assignments[$field] as $key => $option) {
            $item = $filter[$key]($item, $option);
        }
        printf("%16s : %s\n", $field, $item);
    }
}
```

以下是此示例的输出可能呈现的样子：

```text
Terminal
first_name    : Doug
last_name     : Bierer
address       : 123 Main Street
city          : San Francisco
state_province: California
postal_code   : 94101
phone         : +1 415-555-1
country       : US
email         : doug@unlikelysource.com
budget        : 123.45
first_name    : ThisNameBad TagValid
last_name     : ThisLastNameIsKeyTooLongAbcdefgh
city          : ThisCityNameIsTooLong01234567890
postal_code   : Non A
phone         : 12345
country       : US
email         : this.is@not@an.email
budget        : 0
-------------------------------------
{program exited with code: 0}
Press return to continue
```

注意，姓名已被截断，标签已被移除。您还会注意到，虽然电子邮件地址经过了过滤，但它仍然不是一个有效的地址。重要的是要注意，为了正确处理数据，可能不仅需要*过滤*，还需要*验证*。

## 另请参阅

在第 6 章 *Building Scalable Websites* 中，名为 *Chaining $_POST filters* 的食谱讨论了如何将这里介绍的基本过滤概念整合到一个综合的过滤器链机制中。

## 验证 $_POST 数据

过滤和验证之间的主要区别在于，后者不会改变原始数据。另一个区别在于意图。验证的目的是确认数据符合根据客户需求确定的某些标准。

## 如何操作...

- 1. 我们在这里介绍的基本验证机制与前面食谱中展示的相同。与过滤一样，了解要验证的数据的性质、它如何满足客户需求以及它是否符合数据库强制的标准至关重要。例如，如果数据库中列的最大宽度为 128，则验证回调可以使用 `strlen()` 来确认提交数据的长度小于或等于 128 个字符。同样，您可以使用 `ctype_alnum()` 来确认数据只包含字母和数字（视情况而定）。

- 2. 验证的另一个考虑因素是呈现适当的验证失败消息。从某种意义上说，验证过程也是一个确认过程，某人（假想中）将审查验证以确认成功或失败。如果验证失败，此人将需要知道原因。

- 3. 在这个说明中，我们将再次关注 prospects 表。现在我们可以将所需的 PHP 函数集组合成一个单一的回调数组。下面是一个基于表单数据验证需求的示例，这些数据最终将存储在 prospects 表中：

```php
$validator = [
    'email' => [
        'callback' => function ($item) {
            return filter_var($item, FILTER_VALIDATE_EMAIL); },
        'message' => 'Invalid email address'],
    'alpha' => [
        'callback' => function ($item) {
            return ctype_alpha(str_replace(' ', '', $item)); },
        'message' => 'Data contains non-alpha characters'],
    'alnum' => [
        'callback' => function ($item) {
            return ctype_alnum(str_replace(' ', '', $item)); },
        'message' => 'Data contains characters which are '
              . 'not letters or numbers'],
    'digits' => [
        'callback' => function ($item) {
            return preg_match('/[^0-9./]/', $item); },
        'message' => 'Data contains characters which '
              . 'are not numbers'],
    'length' => [
        'callback' => function ($item, $length) {
            return strlen($item) <= $length; },
        'message' => 'Item has too many characters'],
    'upper' => [
        'callback' => function ($item) {
            return $item == strtoupper($item); },
        'message' => 'Item is not upper case'],
    'phone' => [
        'callback' => function ($item) {
            return preg_match('/[^0-9() +-]/', $item); },
        'message' => 'Item is not a valid phone number'],
];
```

> 注意，对于 alpha 和 alnum 回调，我们通过首先使用 `str_replace()` 移除空格来允许空白存在。然后我们可以调用 `ctype_alpha()` 或 `ctype_alnum()`，这将确定是否存在任何不允许的字符。

- 4. 接下来，我们定义一个分配数组，该数组与 `$_POST` 中预期的字段名称相匹配。在这个数组中，我们指定 `$validator` 数组中的键以及任何参数：

```php
$assignments = [
        'first_name'        => ['length' => 32, 'alpha' => NULL],
        'last_name'         => ['length' => 32, 'alpha' => NULL],
        'address'           => ['length' => 64, 'alnum' => NULL],
        'city'              => ['length' => 32, 'alnum' => NULL],
        'state_province'    => ['length' => 20, 'alpha' => NULL],
        'postal_code'       => ['length' => 12, 'alnum' => NULL],
        'phone'             => ['length' => 12, 'phone' => NULL],
        'country'           => ['length' => 2, 'alpha' => NULL,
                                'upper' => NULL],
        'email'             => ['length' => 128, 'email' => NULL],
        'budget'            => ['digits' => NULL],
];
```





### 5. 然后，我们使用嵌套的 foreach() 循环按顺序每次处理一个字段来遍历数据块。对于每个字段，我们遍历分配给该字段的回调函数：

```php
foreach ($data as $field => $item) {
    echo 'Processing: ' . $field . PHP_EOL;
    foreach ($assignments[$field] as $key => $option) {
        if ($validator[$key]['callback']($item, $option)) {
            $message = 'OK';
        } else {
            $message = $validator[$key]['message'];
        }
        printf('%s : %s' . PHP_EOL, $key, $message);
    }
}
```

![](img/39390f6d56c5a83b28db083a8bd5185c_464_0.png)

与其像示例中那样直接回显输出，你可能会记录验证成功/失败的情况，以便稍后呈现给审阅者。此外，如第 6 章“构建可扩展的网站”所示，你可以将验证机制集成到表单中，并在其对应的表单元素旁边显示验证消息。

## 工作原理...

将步骤 3 到 5 中显示的代码放入名为 `chap_12_post_data_validation_basic.php` 的文件中。你还需要定义一个模拟 $_POST 中可能存在的数据的数组。在这种情况下，你使用前一个食谱中提到的两个数组，一个包含良好数据，另一个包含不良数据。最终输出应该如下所示：

```text
Processing: postal_code
--------------------------------------
length : Item has too many characters
alnum : Data contains characters which are not letters or numbers
Processing: phone
--------------------------------------
length : Item has too many characters
phone : OK
Processing: country
--------------------------------------
length : Item has too many characters
alpha : Data contains non-alpha characters
upper : OK
Processing: email
--------------------------------------
length : OK
email : Invalid email address
Processing: budget
--------------------------------------
digits : OK
```

### 参见

- 在第 6 章“构建可扩展的网站”中，标题为“链接 $_POST 验证器”的食谱讨论了如何将与这里涵盖的基本验证概念结合到一个综合的过滤器链接机制中。

## 保护 PHP 会话

PHP 会话机制相当简单。一旦使用 `session_start()` 或 `php.ini` 的 `session.autostart` 设置启动会话，PHP 引擎就会生成一个唯一标识符，默认情况下通过 cookie 将其传递给用户。在后续请求中，只要会话仍被视为活跃，用户的浏览器（或等效程序）就会再次通过 cookie 等方式呈现会话标识符以供检查。然后，PHP 引擎使用该标识符在服务器上定位适当的文件，并将存储的信息填充到 $_SESSION 中。当会话标识符成为识别回访网站访客的唯一手段时，会存在巨大的安全隐患。在本食谱中，我们将介绍几种技术，帮助你保护会话，从而极大地提高网站的整体安全性。

### 如何操作...

1. 首先，重要的是要认识到仅将会话用作身份验证手段的危险性。试想一下，当有效用户登录你的网站时，你在 $_SESSION 中设置了一个 `loggedIn` 标志：

```php
session_start();
$loggedIn = $_SESSION['isLoggedIn'] ?? FALSE;
if (isset($_POST['login'])) {
    if ($_POST['username'] == // username lookup
    && $_POST['password'] == // password lookup) {
        $loggedIn = TRUE;
        $_SESSION['isLoggedIn'] = TRUE;
    }
}
```

2. 在你的程序逻辑中，如果 $_SESSION['isLoggedIn'] 设置为 TRUE，则允许用户查看敏感信息：

```php
// Secret Info
<?php if ($loggedIn) echo // secret information; ?>
```

3. 如果攻击者获得了会话标识符，例如通过成功执行的**跨站脚本 (XSS)** 攻击，他们只需要将 `PHPSESSID` cookie 的值设置为非法获得的值，你的应用程序就会将其视为有效用户。

4. 缩小 `PHPSESSID` 有效时间窗口的一个快速简单方法是使用 `session_regenerate_id()`。这个非常简单的命令生成一个新的会话标识符，使旧标识符无效，保持会话数据完整，并且对性能影响极小。此命令只能在会话启动后执行：

```php
session_start();
session_regenerate_id();
```

5. 另一个常被忽视的技术是确保网站访客有登出选项。然而，重要的是不仅要使用 `session_destroy()` 销毁会话，还要取消 `$_SESSION` 数据并使会话 cookie 过期：

```php
session_unset();
session_destroy();
setcookie('PHPSESSID', 0, time() - 3600);
```

6. 防止会话劫持的另一个简单技术是开发网站访客的指纹或拇指印。实现此技术的一种方法是收集除会话标识符之外，网站访客独有的信息。这些信息包括用户代理（即浏览器）、接受的语言和远程 IP 地址。你可以从此信息中派生一个简单的哈希值，并将该哈希值存储在服务器上的单独文件中。下次用户访问网站时，如果你根据会话信息确定他们已登录，你可以通过匹配指纹执行二次验证：

```php
$remotePrint = md5($_SERVER['REMOTE_ADDR']
        . $_SERVER['HTTP_USER_AGENT']
        . $_SERVER['HTTP_ACCEPT_LANGUAGE']);

$printMatch = file_exists(THUMB_PRINT_DIR . $remotePrint);
if ($loggedIn && !$printMatch) {
    $info = 'SESSION INVALID!!!';
    error_log('Session Invalid: ' . date('Y-m-d H:i:s'), 0);
    // take appropriate action
}
```

![](img/39390f6d56c5a83b28db083a8bd5185c_466_0.png)

我们使用 `md5()` 因为它是一种快速哈希算法，适合内部使用。不建议将 `md5()` 用于任何外部用途，因为它容易受到暴力攻击。

## 工作原理...

为了演示会话是如何容易受到漏洞影响的，编写一个简单的登录脚本，在成功登录时设置 $_SESSION['isLoggedIn'] 标志。你可以将该文件命名为 `chap_12_session_hijack.php`：

```php
session_start();
$loggedIn = $_SESSION['isLoggedIn'] ?? FALSE;
$username = 'test';
$password = 'password';
$info = 'You Can Now See Super Secret Information!!!';

if (isset($_POST['login'])) {
    if ($_POST['username'] == $username
        && $_POST['password'] == $password) {
        $loggedIn = TRUE;
        $_SESSION['isLoggedIn'] = TRUE;
        $_SESSION['loggedInUser'] = $username;
        $loggedIn = $username;
    }
} elseif (isset($_POST['logout'])) {
    session_destroy();
}
```

然后你可以添加代码来显示一个简单的登录表单。要测试会话漏洞，请使用我们刚刚创建的 `chap_12_session_hijack.php` 文件按以下程序操作：

1. 切换到包含该文件的目录。
2. 运行 `php -S localhost:8080` 命令。
3. 使用一个浏览器打开 URL `http://localhost:8080/<filename>`。
4. 以用户 `test` 和密码 `password` 登录。
5. 你应该能看到**你现在可以查看超级机密信息！！！**。
6. 刷新页面：每次，你都应该看到一个新的会话标识符。
7. 复制 `PHPSESSID` cookie 的值。
8. 在另一个浏览器中打开同一网页。
9. 通过复制 `PHPSESSID` 的值来修改浏览器发送的 cookie。

为了说明起见，我们还显示 $_COOKIE 和 $_SESSION 的值，如下面的截图中使用 Vividi 浏览器所示：

![](img/39390f6d56c5a83b28db083a8bd5185c_468_0.png)

然后我们复制 `PHPSESSID` 的值，打开 Firefox 浏览器，并使用名为 Tamper Data 的工具修改 cookie 的值：

![](img/39390f6d56c5a83b28db083a8bd5185c_468_1.png)

你可以在下一个截图中看到，我们已经成为经过身份验证的用户，无需输入用户名或密码：

![](img/39390f6d56c5a83b28db083a8bd5185c_469_0.png)

你现在可以实施前几步中讨论的更改。将之前创建的文件复制到 `chap_12_session_protected.php`。现在继续重新生成会话 ID：

```php
<?php
define('THUMB_PRINT_DIR', __DIR__ . '/../data/');
session_start();
session_regenerate_id();
```

接下来，初始化变量并确定登录状态（与之前相同）：

```php
$username = 'test';
$password = 'password';
$info = 'You Can Now See Super Secret Information!!!';
$loggedIn = $_SESSION['isLoggedIn'] ?? FALSE;
$loggedUser = $_SESSION['user'] ?? 'guest';
```

你可以使用远程地址、用户代理和语言设置添加会话拇指印：

```php
$remotePrint = md5($_SERVER['REMOTE_ADDR']
    . $_SERVER['HTTP_USER_AGENT']
    . $_SERVER['HTTP_ACCEPT_LANGUAGE']);
```





## PHP 代码示例

如果登录成功，我们将拇指印信息和登录状态存储在会话中：

```php
    if (isset($_POST['login'])) {
        if ($_POST['username'] == $username
            & $_POST['password'] == $password) {
            $loggedIn = TRUE;
            $_SESSION['user'] = strip_tags($username);
            $_SESSION['isLoggedIn'] = TRUE;
            file_put_contents(
                THUMB_PRINT_DIR . $remotePrint, $remotePrint);
        }
    }
```

你还可以检查注销选项并实现适当的注销程序：取消设置 `$_SESSION` 变量，使会话失效，并使 Cookie 过期。你还可以删除拇指印文件并实现重定向：

```php
    } elseif (isset($_POST['logout'])) {
        session_unset();
        session_destroy();
        setcookie('PHPSESSID', 0, time() - 3600);
        if (file_exists(THUMB_PRINT_DIR . $remotePrint))
            unlink(THUMB_PRINT_DIR . $remotePrint);
        header('Location: ' . $_SERVER['REQUEST_URI']);
        exit;
    }
```

否则，如果操作既不是登录也不是注销，你可以检查用户是否被视为已登录，如果拇指印不匹配，则认为会话无效，并采取适当的措施：

```php
    } elseif ($loggedIn && !$printsMatch) {
        $info = 'SESSION INVALID!';
        error_log('Session Invalid: ' . date('Y-m-d H:i:s'), 0);
        // take appropriate action
    }
```

你现在可以使用新的 `chap_12_session_protected.php` 文件运行之前提到的相同过程。你首先会注意到会话现在被视为无效。输出看起来将如下所示：

![](img/39390f6d56c5a83b28db083a8bd5185c_471_0.png)

这是因为拇指印不匹配，因为你正在使用不同的浏览器。同样，如果你刷新第一个浏览器的页面，会话标识符将被重新生成，使得任何先前复制的标识符失效。最后，注销按钮将完全清除会话信息。

## 参见

如需了解网站漏洞的优秀概述，请参阅位于 `https://www.owasp.org/index.php/Category:Vulnerability` 的文章。关于会话劫持的信息，请参阅 `https://www.owasp.org/index.php/Session_hijacking_attack`。

## 使用令牌保护表单

此食谱介绍了另一种非常简单的技术，可保护你的表单免受**跨站请求伪造 (CSRF)** 攻击。简单来说，当攻击者可能使用其他技术，能够感染你网站上的网页时，CSRF 攻击是可能的。在大多数情况下，被感染的页面随后将开始使用有效登录用户的凭据发出请求（即，使用 JavaScript 购买物品或进行设置更改）。你的应用程序极难检测此类活动。可以采取的一项简单措施是生成一个随机令牌，并将其包含在每个要提交的表单中。由于被感染的页面无法访问该令牌，也无法生成匹配的令牌，因此表单验证将失败。

## 操作方法...

- 首先，为了演示问题，我们创建一个网页，模拟生成请求向数据库提交条目的被感染页面。为此说明，我们将该文件命名为 `chap_12_form_csrf_test_unprotected.html`：

```html
<!DOCTYPE html>
<body onload="load()">
    <form action="chap_12_form_unprotected.php"
          method="post" id="csrf_test" name="csrf_test">
        <input name="name" type="hidden" value="No Goodnick" />
        <input name="email" type="hidden" value="malicious@owasp.org" />
        <input name="comments" type="hidden"
               value="Form is vulnerable to CSRF attacks!" />
        <input name="process" type="hidden" value="1" />
    </form>
    <script>
        function load() { document.forms['csrf_test'].submit(); }
    </script>
</body>
</html>
```

- 接下来，我们创建一个名为 `chap_12_form_unprotected.php` 的脚本，用于响应表单提交。与本书中的其他调用程序一样，我们设置自动加载并使用在*第 5 章，与数据库交互*中介绍的 `Application\Database\Connection` 类：

```php
<?php
define('DB_CONFIG_FILE', '../../../config/db.config.php');
require __DIR__ . '../../../Application/Autoload/Loader.php';
Application\Autoload\Loader::init(__DIR__ . '/..');
use Application\Database\Connection;

$conn = new Connection(include __DIR__ . DB_CONFIG_FILE);
```

- 然后我们检查是否按下了处理按钮，并实现一个过滤机制，如本章中的过滤 `$_POST` 数据食谱所述。这是为了证明 CSRF 攻击可以轻松绕过过滤器：

```php
if ($_POST['process']) {
    $filter = [
        'trim' => function ($item) { return trim($item); },
        'email' => function ($item) {
            return filter_var($item, FILTER_SANITIZE_EMAIL); },
        'length' => function ($item, $length) {
            return substr($item, 0, $length); },
        'stripTags' => function ($item) {
            return strip_tags($item); },
    ];

    $assignments = [
        '*' => ['trim' => NULL, 'stripTags' => NULL],
        'email' => ['length' => 249, 'email' => NULL],
        'name' => ['length' => 128],
        'comments'=> ['length' => 249],
    ];

    $data = $_POST;
    foreach ($data as $field => $item) {
        foreach ($assignments['*'] as $key => $option) {
            $item = $filter[$key]($item, $option);
        }
        if (isset($assignments[$field])) {
            foreach ($assignments[$field] as $key => $option) {
                $item = $filter[$key]($item, $option);
            }
            $filteredData[$field] = $item;
        }
    }
}
```

- 最后，我们将过滤后的数据使用预编译语句插入数据库。然后我们重定向到另一个脚本，称为 `chap_12_form_view_results.php`，该脚本仅转储访问者表的内容：

```php
try {
    $filteredData['visit_date'] = date('Y-m-d H:i:s');
    $sql = 'INSERT INTO visitors '
         . '(:email,:name,:comments,:visit_date) '
         . 'VALUES (:email,:name,:comments,:visit_date)';
    $insertStmt = $conn->pdo->prepare($sql);
    $insertStmt->execute($filteredData);
} catch (PDOException $e) {
    echo $e->getMessage();
}

header('Location: /chap_12_form_view_results.php');
exit;
```

- 结果，当然，是尽管有过滤和预编译语句的使用，攻击仍然被允许。

- 实现表单保护令牌其实相当简单！首先，你需要生成令牌并将其存储在会话中。我们利用新的 `random_bytes()` PHP 7 函数来生成一个真正的随机令牌，攻击者将很难甚至不可能匹配该令牌：

```php
session_start();
$token = urlencode(base64_encode(random_bytes(32)));
$_SESSION['token'] = $token;
```

![](img/39390f6d56c5a83b28db083a8bd5185c_474_0.png)

> `random_bytes()` 的输出是二进制数据。我们使用 `base64_encode()` 将其转换为可用的字符串。然后我们使用 `urlencode()` 进一步处理它，以便它在 HTML 表单中正确呈现。

- 当我们渲染表单时，然后将令牌作为隐藏字段呈现：

```html
<input type="hidden" name="token" value="<?= $token ?>" />
```

- 然后我们复制并修改之前提到的 `chap_12_form_unprotected.php` 脚本，添加逻辑以首先检查令牌是否与存储在会话中的令牌匹配。请注意，我们取消设置当前令牌，使其对未来的使用无效。我们将新脚本命名为 `chap_12_form_protected_with_token.php`：

```php
if ($_POST['process']) {
    $sessToken = $_SESSION['token'] ?? 1;
    $postToken = $_POST['token'] ?? 2;
    unset($_SESSION['token']);
    if ($sessToken != $postToken) {
        $_SESSION['message'] = 'ERROR: token mismatch';
    } else {
        $_SESSION['message'] = 'SUCCESS: form processed';
        // continue with form processing
    }
}
```

## 工作原理...

为了测试被感染的网页可能如何发起 CSRF 攻击，创建食谱中之前显示的以下文件：

- `chap_12_form_csrf_test_unprotected.html`
- `chap_12_form_unprotected.php`




# *提升 Web 安全性*

随后，你可以定义一个名为 `chap_12_form_view_results.php` 的文件，该文件用于输出访客表的内容：

```php
<?php
session_start();
define('DB_CONFIG_FILE', '/../config/db.config.php');
require __DIR__ . '/../Application/Autoload/Loader.php';
Application\Autoload\Loader::init(__DIR__ . '/../');
use Application\Database\Connection;
$conn = new Connection(include __DIR__ . DB_CONFIG_FILE);
$message = $_SESSION['message'] ?? '';
unset($_SESSION['message']);
$stmt = $conn->pdo->query('SELECT * FROM visitors');
?>
<!DOCTYPE html>
<body>
<div class="container">
<h1>CSRF 防护</h1>
<h3>访客表</h3>
<?php while ($row = $stmt->fetch(PDO::FETCH_ASSOC)) : ?>
<pre><?php echo implode('|', $row); ?></pre>
<?php endwhile; ?>
<?php if ($message) : ?>
<b><?php $message; ?></b>
<?php endif; ?>
</div>
</body>
</html>
```

在浏览器中启动 `chap_12_form_csrf_test_unprotected.html`。以下是可能的输出效果：

![](img/39390f6d56c5a83b28db083a8bd5185c_475_0.png)

如你所见，尽管采用了过滤和预处理语句，攻击仍然成功！

接下来，将 `chap_12_form_unprotected.php` 文件复制为 `chap_12_form_protected.php`。按照食谱中的第 8 步进行更改。你还修改测试 HTML 文件，将 `chap_12_form_csrf_test_unprotected.html` 复制为 `chap_12_form_csrf_test_protected.html`。按照以下方式修改 FORM 标签中 action 参数的值：

```html
<form action="/chap_12_form_protected_with_token.php"
method="post" id="csrf_test" name="csrf_test">
```

当你在浏览器中运行新的 HTML 文件时，它会调用 `chap_12_form_protected.php`，该文件会寻找一个并不存在的令牌。以下是预期的输出：

![](img/39390f6d56c5a83b28db083a8bd5185c_476_0.png)

最后，定义一个名为 `chap_12_form_protected.php` 的文件，该文件生成一个令牌并将其作为一个隐藏元素显示：

```php
<?php
session_start();
$token = urlencode(base64_encode((random_bytes(32))));
$_SESSION['token'] = $token;
?>
<!DOCTYPE html>
<body onload="load()">
<div class="container">
<h1>受 CSRF 保护的表单</h1>
<form action="/chap_12_form_protected_with_token.php"
method="post" id="csrf_test" name="csrf_test">
<table>
<tr><th>姓名</th><td><input name="name" type="text" /></td></tr>
<tr><th>电子邮件</th><td><input name="email" type="text" /></td></tr>
<tr><th>评论</th><td>
<input name="comments" type="textarea" rows=4 cols=80 />
</td></tr>
<tr><th>&nbsp;</th><td>
<input name="process" type="submit" value="处理" />
</td></tr>
</table>
<input type="hidden" name="token" value="<?= $token ?>" />
</form>
<a href="/chap_12_form_view_results.php">
    点击此处</a> 查看结果
</div>
</body>
</html>
```

当我们显示并提交来自表单的数据时，令牌经过验证，允许继续执行数据插入，如下所示：

![](img/39390f6d56c5a83b28db083a8bd5185c_477_0.png)

# **参见**

有关 CSRF 攻击的更多信息，请参考 `https://www.owasp.org/index.php/Cross-Site_Request_Forgery_(CSRF)`。

# ## 构建安全的密码生成器

一个常见的误解是，攻击者破解哈希密码的唯一方法是使用**暴力破解攻击**和**彩虹表**。虽然这通常是攻击序列中的第一遍，但攻击者会在第二遍、第三遍或第四遍中使用更复杂的攻击。其他攻击包括*组合*、*字典*、*掩码*和*基于规则*的攻击。字典攻击使用字典中字面上存在的单词数据库来猜测密码。组合攻击是将字典中的单词进行组合。掩码攻击类似于暴力破解，但更具选择性，从而缩短了破解时间。基于规则的攻击会检测诸如用数字 0 代替字母 o 等操作。

好消息是，仅仅将密码长度增加到六字符的魔法长度以上，就会呈指数级增加破解哈希密码所需的时间。其他因素，如随机混合大写字母和小写字母、随机数字以及特殊字符，也会对破解时间产生指数级的影响。归根结底，我们需要牢记，最终人类需要输入创建的密码，这意味着这些密码至少需要具有一定程度的可记忆性。

> **最佳实践**

密码应存储为哈希值，绝不能以明文形式存储。MD5 和 SHA* 不再被认为是安全的（尽管 SHA* 比 MD5 好得多）。使用诸如 oclHashcat 之类的工具，攻击者可以对通过漏洞（即成功的 SQL 注入攻击）暴露出来的使用 MD5 进行哈希处理的密码生成平均每秒 550 亿次尝试。

# 如何操作...

1.  首先，我们定义一个 `Application\Security\PassGen` 类，该类将保存密码生成所需的方法。我们还定义某些将在该过程中使用的类常量和属性：

```php
namespace Application\Security;
class PassGen
{
    const SOURCE_SUFFIX = 'src';
    const SPECIAL_CHARS = '\\\"!"£$%^&*()_-+= {} [] @~;\''#<>?../|\\' ;
    protected $algorithm;
    protected $sourceList;
    protected $word;
    protected $list;
```

2.  然后，我们定义将在密码生成中使用的低级方法。顾名思义，`digits()` 生成随机数字，`special()` 生成来自 `SPECIAL_CHARS` 类常量的单个字符：

```php
public function digits($max = 999)
{
    return random_int(1, $max);
}

public function special()
{
    $maxSpecial = strlen(self::SPECIAL_CHARS) - 1;
    return self::SPECIAL_CHARS[random_int(0, $maxSpecial)];
}
```

![](img/39390f6d56c5a83b28db083a8bd5185c_479_0.png)

> 注意，在此示例中我们频繁使用新的 PHP 7 函数 `random_int()`。虽然略微较慢，但与传统较旧的 `rand()` 函数相比，该方法提供了真正的**加密安全伪随机数生成器 (CSPRNG)** 功能。

3.  现在到了棘手的部分：生成一个难以猜测的单词。这就是 `$wordSource` 构造函数参数发挥作用的地方。它是一个网站数组，我们的词库将由此派生。相应地，我们需要一个方法，该方法从指定的源中提取唯一的单词列表，并将结果存储在一个文件中。我们接受 `$wordSource` 数组作为参数，并循环遍历每个 URL。我们使用 `md5()` 生成网站名称的哈希值，然后将其构建到一个文件名中。新生成的文件名存储在 `$sourceList` 中：

```php
public function processSource(
    $wordSource, $minWordLength, $cacheDir)
{
    foreach ($wordSource as $html) {
        $hashKey = md5($html);
        $sourceFile = $cacheDir . '/' . $hashKey . '.'
            . self::SOURCE_SUFFIX;
        $this->sourceList[] = $sourceFile;
    }
}
```

4.  如果文件不存在，或者是零字节文件，我们处理其内容。如果源是 HTML，我们只接受 `<body>` 标签内部的内容。然后我们使用 `str_word_count()` 从字符串中提取单词列表，同时使用 `strip_tags()` 移除任何标记：

```php
if (!file_exists($sourceFile) || filesize($sourceFile) == 0) {
    echo 'Processing: ' . $html . PHP_EOL;
    $contents = file_get_contents($html);
    if (preg_match('/<body>(.*)<\/body>/i',
        $contents, $matches)) {
        $contents = $matches[1];
    }
    $list = str_word_count(strip_tags($contents), 1);
}
```

5.  然后我们删除任何过短的单词，并使用 `array_unique()` 去除重复项。最终结果存储在一个文件中：

```php
foreach ($list as $key => $value) {
    if (strlen($value) < $minWordLength) {
        $list[$key] = 'xxxxxxx';
    } else {
        $list[$key] = trim($value);
    }
}
       $list = array_unique($list);
        file_put_contents($sourceFile, implode("\n",$list));
        }
    }
    return TRUE;
}
```

6.  接下来，我们定义一个方法，该方法将单词中的随机字母转换为大写：

```php
public function flipUpper($word)
{
    $maxLen     = strlen($word);
    $numFlips = random_int(1, $maxLen - 1);
    $flipped = strtolower($word);
    for ($x = 0; $x < $numFlips; $x++) {
        $pos = random_int(0, $maxLen - 1);
        $word[$pos] = strtoupper($word[$pos]);
    }
    return $word;
}
```

7.  最后，我们准备定义一个从我们的源中选择单词的方法。我们随机选择一个单词源，并使用 file() 函数从相应的缓存文件中读取：

```php
public function word()
{
    $wsKey     = random_int(0, count($this->sourceList) - 1);
    $list     = file($this->sourceList[$wsKey]);
    $maxList = count($list) - 1;
    $key     = random_int(0, $maxList);
    $word = $list[$key];
    return $this->flipUpper($word);
}
```

8.  为了避免始终生成具有相同模式的密码，我们定义一个方法，该方法允许我们将密码的各个组件放置在最终密码字符串的不同位置。算法被定义为此类中可用的方法调用的数组。因此，例如，算法 ['word', 'digits', 'word', 'special'] 最终可能看起来像 hEiL0123aUTol：

```php
public function initAlgorithm()
{
    $this->algorithm = [
        ['word', 'digits', 'word', 'special'],
        ['digits', 'word', 'special', 'word'],
        ['word', 'word', 'special', 'digits'],
```





# 工作原理……

首先，你需要将前一个配方中描述的代码放入 Application\Security 文件夹中名为 PassGen.php 的文件中。现在你可以创建一个名为 chap_12_password_generate.php 的调用程序，该程序设置自动加载，使用 PassGen，并定义缓存目录的位置：

```php
<?php
define('CACHE_DIR', __DIR__ . '/cache');
require __DIR__ . '/../Application/Autoload/Loader.php';
Application\Autoload\Loader::init(__DIR__ . './../');
use Application\Security\PassGen;
```

接下来，你需要定义一个网站数组，该数组将作为密码生成中使用的词库的来源。在本例中，我们将选择 Project Gutenberg 文本 *Ulysses*（J. Joyce）、*War and Peace*（L. Tolstoy）和 *Pride and Prejudice*（J. Austen）：

```php
$source = [
    'https://www.gutenberg.org/files/4300/4300-0.txt',
    'https://www.gutenberg.org/files/2600/2600-h/2600-h.htm',
    'https://www.gutenberg.org/files/1342/1342-h/1342-h.htm',
];
```

接下来，我们创建 `PassGen` 实例，并运行 `generate()`：

```php
$passGen = new PassGen($source, 4, CACHE_DIR);
echo $passGen->generate();
```

以下是 `PassGen` 生成的一些示例密码：

![](img/39390f6d56c5a83b28db083a8bd5185c_482_0.png)

## 另请参阅

一篇关于攻击者如何破解密码的优秀文章可在 http://arstechnica.com/security/2013/05/how-crackers-make-minced-meat-out-of-your-passwords/ 查看。要了解有关暴力破解攻击的更多信息，你可以参考 https://www.owasp.org/index.php/Brute_force_attack。有关 oclHashcat 的信息，请参见此页面：http://hashcat.net/oclhashcat/。

## 使用验证码保护表单

**CAPTCHA** 实际上是 **Completely Automated Public Turing Test to Tell Computers and Humans Apart**（完全自动化公开图灵测试，用于区分计算机和人类）的缩写。该技术类似于前面配方中介绍的 *使用令牌保护表单*。不同之处在于，令牌不再存储在隐藏表单输入字段中，而是渲染成一种图形，使自动化攻击系统难以破解。此外，验证码的意图与表单令牌略有不同：它旨在确认网页访问者是人类，而不是自动化系统。

# 操作方法……

- 1. 验证码有几种方法：提出只有人类才知道的问题、文字技巧，以及需要解释的图形图像。
- 2. 图像方法向网页访问者展示包含严重扭曲字母和/或数字的图像。然而，这种方法可能很复杂，因为它依赖于 GD 扩展，而该扩展可能并非在所有服务器上都可用。GD 扩展可能难以编译，并且严重依赖宿主服务器上必须存在的各种库。
- 3. 文字方法是展示一系列字母和/或数字，并给网页访问者一个简单的指令，例如 *请反向输入此内容*。另一种变体是使用 ASCII“艺术”来形成人类网页访问者能够解释的字符。
- 4. 最后，你可以采用问答方法，问题如 *头部通过身体哪个部位连接到躯干*，答案如 *Arm*（手臂）、*Leg*（腿）和 *Neck*（脖子）。这种方法的缺点是自动化攻击系统有 1/3 的机会通过测试。

## 生成文本验证码

- 1. 为了说明这一点，我们将从文字方法开始，然后介绍图像方法。无论哪种情况，我们首先需要定义一个类来生成要展示给网页访问者（并由其解码）的短语。为此，我们定义了一个 `Application\Captcha\Phrase` 类。我们还定义了短语生成过程中使用的属性和类常量：

```php
namespace Application\Captcha;

class Phrase
{
    const DEFAULT_LENGTH    = 5;
    const DEFAULT_NUMBERS   = '0123456789';
    const DEFAULT_UPPER     = 'ABCDEFGHJKLMNOPQRSTUVWXYZ';
    const DEFAULT_LOWER     = 'abcdefghijklmnopqrstuvwxyz';
    const DEFAULT_SPECIAL   = '!"\'#$%&*()_+[]{}@\^~<,>.?/\';
    const DEFAULT_SUPPRESS  = ['0', 'l'];

    protected $phrase;
    protected $includeNumbers;
    protected $includeUpper;
    protected $includeLower;
    protected $includeSpecial;
    protected $otherChars;
    protected $suppressChars;
    protected $string;
    protected $length;
}
```

- 2. 构造函数，正如你所期望的，接受各种属性的值，并分配默认值，以便在不指定任何参数的情况下创建实例。$include* 标志用于指示哪些字符集将存在于从中生成短语的基础字符串中。例如，如果你希望只有数字，则 $includeUpper 和 $includeLower 都将设置为 FALSE。$otherChars 提供了额外的灵活性。最后，$suppressChars 表示一个将被从基础字符串中移除的字符数组。默认情况下移除大写 0 和小写 1：

```php
public function __construct(
        $length = NULL,
        $includeNumbers = TRUE,
        $includeUpper = TRUE,
        $includeLower = TRUE,
        $includeSpecial = FALSE,
        $otherChars = NULL,
        array $suppressChars = NULL)
    {
        $this->length = $length ?? self::DEFAULT_LENGTH;
        $this->includeNumbers = $includeNumbers;
        $this->includeUpper = $includeUpper;
        $this->includeLower = $includeLower;
        $this->includeSpecial = $includeSpecial;
        $this->otherChars = $otherChars;
        $this->suppressChars = $suppressChars
                ?? self::DEFAULT_SUPPRESS;
        $this->phrase = $this->generatePhrase();
    }
```

- 3. 然后我们定义了一系列 getter 和 setter，每个属性对应一个。请注意，为了节省空间，我们只展示了前两个。

```php
public function getString()
{
    return $this->string;
}

public function setString($string)
{
    $this->string = $string;
}

// other getters and setters not shown
```

- 4. 接下来我们需要定义一个方法来初始化基础字符串。它由一系列简单的 if 语句组成，这些语句检查各种 $include* 标志，并根据情况将相应内容附加到基础字符串中。最后，我们使用 str_replace() 来移除 $suppressChars 中表示的字符：

```php
public function initString()
{
    $string = '';
    if ($this->includeNumbers) {
        $string .= self::DEFAULT_NUMBERS;
    }
    if ($this->includeUpper) {
        $string .= self::DEFAULT_UPPER;
    }
    if ($this->includeLower) {
        $string .= self::DEFAULT_LOWER;
    }
    if ($this->includeSpecial) {
        $string .= self::DEFAULT_SPECIAL;
    }
    if ($this->otherChars) {
        $string .= $this->otherChars;
    }
    if ($this->suppressChars) {
        $string = str_replace(
            $this->suppressChars, '', $string);
    }
    return $string;
}
```

![](img/39390f6d56c5a83b28db083a8bd5185c_486_0.png)

## 最佳实践

去除那些可能与数字混淆的字母（即字母 **O** 可能与数字 **0** 混淆，小写字母 **l** 可能与数字 **1** 混淆）。

- 5. 我们现在准备定义核心方法，该方法生成验证码向网站访问者展示的随机短语。我们设置一个简单的 `for()` 循环，并使用新的 PHP 7 `random_int()` 函数在基础字符串中随机跳转：

```php
public function generatePhrase()
{
    $phrase = '';
    $this->string = $this->initString();
    $max = strlen($this->string) - 1;
    for ($x = 0; $x < $this->length; $x++) {
        $phrase .= substr(
            $this->string, random_int(0, $max), 1);
    }
    return $phrase;
}
```

- 6. 现在我们将注意力从短语转移到生成文本验证码的类上。为此，我们首先定义一个接口，以便将来我们可以创建额外使用 Application\Captcha\Phrase 的验证码类。注意 getImage() 将根据我们决定使用哪个类返回文本、文字艺术或实际图像：

```php
namespace Application\Captcha;

interface CaptchaInterface
{
    public function getLabel();
    public function getImage();
    public function getPhrase();
}
```

- 7. 对于文本验证码，我们定义了一个 Application\Captcha\Reverse 类。之所以这样命名，是因为该类产生的不仅是文本，而是反向文本。__construct() 方法构建一个 Phrase 实例。注意 getImage() 返回反向的短语：

```php
namespace Application\Captcha;

class Reverse implements CaptchaInterface
{
    const DEFAULT_LABEL = 'Type this in reverse';
    const DEFAULT_LENGTH = 6;
```




## 生成图像验证码

- 1. 正如你所能想象的那样，图像方法要复杂得多。短语生成过程是相同的。主要区别在于，我们不仅要将在短语印在图形上，还需要对每个字母进行不同的变形，并以随机点噪点形式引入干扰。

- 我们定义了一个实现 `CaptchaInterface` 的 `Application\Captcha\Image` 类。该类的常量和属性不仅包括短语生成所需的项，还包括图像生成所需的内容：

```php
namespace Application\Captcha;
use DirectoryIterator;

class Image implements CaptchaInterface
{
    const DEFAULT_WIDTH = 200;
    const DEFAULT_HEIGHT = 50;
    const DEFAULT_LABEL = 'Enter this phrase';
    const DEFAULT_BG_COLOR = [255, 255, 255];
    const DEFAULT_URL = '/captcha';
    const IMAGE_PREFIX = 'CAPTCHA_';
    const IMAGE_SUFFIX = '.jpg';
    const IMAGE_EXP_TIME = 300;    // seconds
    const ERROR_REQUIRES_GD = 'Requires the GD extension + '
        . ' the JPEG library';
    const ERROR_IMAGE = 'Unable to generate image';

    protected $phrase;
    protected $imageFn;
    protected $label;
    protected $imageWidth;
    protected $imageHeight;
    protected $imageRGB;
    protected $imageDir;
    protected $imageUrl;
}
```

- 构造函数需要接受前文步骤中描述的短语生成所需的所有参数。此外，我们还需要接受图像生成所需的参数。两个强制参数是 `$imageDir` 和 `$imageUrl`。前者是图形文件的写入位置；后者是基础 URL，我们随后会在其后拼接生成的文件名。提供 `$imageFont` 参数是为了在希望使用 TrueType 字体时使用，从而生成更安全的验证码。否则，我们只能限于使用默认字体，借用一部著名电影中的一句话来说，*那可真难看*：

```php
public function __construct(
    $imageDir,
    $imageUrl,
    $imageFont = NULL,
    $label = NULL,
    $length = NULL,
    $includeNumbers = TRUE,
    $includeUpper= TRUE,
    $includeLower= TRUE,
    $includeSpecial= FALSE,
    $otherChars= NULL,
    array $suppressChars= NULL,
    $imageWidth= NULL,
    $imageHeight= NULL,
    array $imageRGB= NULL
)
{
```

- 4. 接下来，仍在构造函数中，我们检查 `imagecreattruecolor` 函数是否存在。如果该函数返回 FALSE，说明 GD 扩展不可用。否则，我们将参数赋值给属性，生成短语，删除旧图像，并写出验证码图形：

```php
    if (!function_exists('imagecreattruecolor')) {
        throw new \Exception(self::ERROR_REQUIRES_GD);
    }
    $this->imageDir    = $imageDir;
    $this->imageUrl    = $imageUrl;
    $this->imageFont   = $imageFont;
    $this->label       = $label ?: self::DEFAULT_LABEL;
    $this->imageRGB    = $imageRGB ?: self::DEFAULT_BG_COLOR;
    $this->imageWidth  = $imageWidth ?: self::DEFAULT_WIDTH;
    $this->imageHeight = $imageHeight ?: self::DEFAULT_HEIGHT;
    if (substr($imageUrl, -1, 1) == '/') {
        $imageUrl = substr($imageUrl, 0, -1);
    }
    $this->imageUrl = $imageUrl;
    if (substr($imageDir, -1, 1) == DIRECTORY_SEPARATOR) {
        $imageDir = substr($imageDir, 0, -1);
    }

    $this->phrase = new Phrase(
        $length,
        $includeNumbers,
        $includeUpper,
        $includeLower,
        $includeSpecial,
        $otherChars,
        $suppressChars
    );
    $this->removeOldImages();
    $this->generateJpg();
}
```

- 5. 删除旧图像的过程至关重要；否则，我们的目录中将会充满过期的验证码图像！我们使用 `DirectoryIterator` 类扫描指定目录并检查访问时间。我们将旧图像文件计算为当前时间减去 `IMAGE_EXP_TIME` 指定值之后的时间点：

```php
public function removeOldImages() {
    $old = time() - self::IMAGE_EXP_TIME;
    foreach (new DirectoryIterator($this->imageDir)
         as $fileInfo) {
        if ($fileInfo->isDot()) continue;
        if ($fileInfo->getATime() < $old)
            unlink($this->imageDir . DIRECTORY_SEPARATOR
                  . $fileInfo->getFilename());
    }
}
```

- 6. 现在我们已经准备好进入主要环节。首先，我们将 `$imageRGB` 数组拆分为 `$red`、`$green` 和 `$blue`。我们使用核心的 `imagecreattruecolor()` 函数，按照指定的宽度和高度生成基础图形。我们使用 RGB 值为背景着色：

```php
public function generateJpg()
{
    try {
        list($red, $green, $blue) = $this->imageRGB;
        $im = imagecreattruecolor(
            $this->imageWidth, $this->imageHeight);
        $black = imagecolorallocate($im, 0, 0, 0);
        $imageBgColor = imagecolorallocate(
            $im, $red, $green, $blue);
        imagefilledrectangle($im, 0, 0, $this->imageWidth,
            $this->imageHeight, $imageBgColor);

        $xMargin = (int) ($this->imageWidth * .1 + .5);
        $yMargin = (int) ($this->imageHeight * .3 + .5);
        $phrase = $this->getPhrase();
        $max = strlen($phrase);
        $count = 0;
        $x = $xMargin;
        $size = 5;
        for ($i = 0; $i < $max; $i++) {
```

- 8. 如果指定了 `$imageFont`，我们就能以不同的尺寸和角度书写每个字符。我们还需要根据尺寸调整 x 轴（即水平方向）的值：

```php
            if ($this->imageFont) {
                $size = rand(12, 32);
                $angle = rand(0, 30);
                $y = rand($yMargin + $size, $this->imageHeight);
                imagettftext($im, $size, $angle, $x, $y, $black,
                    $this->imageFont, $phrase[$i]);
                $x += (int) ($size + rand(0, 5));
```

- 9. 否则，我们只能局限于默认字体。我们使用最大尺寸 5，因为较小的尺寸无法阅读。我们通过交替使用 `imagechar()`（正常写入图像）和 `imagecharup()`（侧向写入）来提供低级别的扭曲效果：

```php
            } else {
                $y = rand(0, ($this->imageHeight - $yMargin));
                if ($count++ & 1) {
                    imagechar($im, 5, $x, $y, $phrase[$i], $black);
                } else {
                    imagecharup($im, 5, $x, $y, $phrase[$i], $black);
                }
                $x += (int) ($size * 1.2);
            }
        } // end for ($i = 0; $i < $max; $i++)
```

- 10. 接下来，我们需要以随机点噪点形式添加噪声。这对于使自动系统更难识别图像是必要的。同时建议你添加代码绘制几条线：

```php
            $numDots = rand(10, 999);
            for ($i = 0; $i < $numDots; $i++) {
                imagesetpixel($im, rand(0, $this->imageWidth),
                              rand(0, $this->imageHeight), $black);
            }
```

- 11. 然后，我们使用老搭档 `md5()` 生成随机的图像文件名，参数为日期和 0 到 9999 之间的随机数。请注意，我们可以安全地使用 `md5()`，因为我们不是试图隐藏任何机密信息；我们只是希望快速生成一个唯一的文件名。我们也会清除图像对象以节省内存：

```php
            $this->imageFn = self::IMAGE_PREFIX
                . md5(date('YmdHis') . rand(0, 9999))
                . self::IMAGE_SUFFIX;
            imagejpeg($im, $this->imageDir . DIRECTORY_SEPARATOR
                . $this->imageFn);
            imagedestroy($im);
```

- 12. 整个构建过程都在 `try/catch` 块中。如果抛出错误或异常，我们记录消息并采取相应措施：

```php
        } catch (\Throwable $e) {
            error_log(_METHOD . ':' . $e->getMessage());
            throw new \Exception(self::ERROR_IMAGE);
        }
    }
```

- 13. 最后，我们定义接口所要求的方法。请注意，`getImage()` 返回一个 HTML `<img>` 标签，可以立即显示：

```php
public function getLabel()
{
    return $this->label;
}

public function getImage()
{
    return sprintf('<img src="%s/%s" />',
        $this->imageUrl, $this->imageFn);
}

public function getPhrase()
{
    return $this->phrase->getPhrase();
}
```

## 工作原理...

务必定义本食谱中讨论的类，这些类在下表中总结：

| 类 | 小节 | 出现的步骤 |
|---|---|---|
| Application\Captcha\Phrase | 生成文本验证码 | 1 – 5 |
| Application\Captcha\CaptchaInterface |  | 6 |
| Application\Captcha\Reverse |  | 7 |
| Application\Captcha\Image | 生成图像验证码 | 2 - 13 |




## 接下来，定义一个名为 chap_12_captcha_text.php 的调用程序，该程序实现文本验证码。

你首先需要设置自动加载并使用相应的类：

```php
<?php
    require __DIR__ . './../Application/Autoload/Loader.php';
    Application\Autoload\Loader::init(__DIR__ . './../');
    use Application\Captcha\Reverse;
```

然后，务必启动会话。你还需要采取适当的措施来保护会话。为了节省篇幅，我们仅展示一种简单的措施，`session_regenerate_id()`：

```php
session_start();
session_regenerate_id();
```

接下来，你可以定义一个函数来创建验证码；获取短语、标签和图片（在这种情况下，为反转文本）；并将值存储在会话中：

```php
function setCaptcha(&$phrase, &$label, &$image)
{
    $captcha = new Reverse();
    $phrase = $captcha->getPhrase();
    $label = $captcha->getLabel();
    $image = $captcha->getImage();
    $_SESSION['phrase'] = $phrase;
}
```

现在是初始化变量并确定 loggedIn 状态的好时机：

```php
$image = '';
$label = '';
$phrase = $_SESSION['phrase'] ?? '';
$message = '';
$info = 'You Can Now See Super Secret Information!!!';
$loggedIn = $_SESSION['isLoggedIn'] ?? FALSE;
$loggedUser = $_SESSION['user'] ?? 'guest';
```

然后你可以检查登录按钮是否被按下。如果是，检查是否输入了验证码短语。如果没有，初始化一条消息，告知用户需要输入验证码短语：

```php
if (!empty($_POST['login'])) {
    if (empty($_POST['captcha'])) {
        $message = 'Enter Captcha Phrase and Login Information';
```

如果存在验证码短语，检查它是否与存储在会话中的值匹配。如果不匹配，按照表单无效进行处理。否则，按照原本的方式处理登录。为了演示的目的，你可以使用硬编码的 username 和 password 值来模拟登录：

```php
    } else {
        if ($_POST['captcha'] == $phrase) {
            $username = 'test';
            $password = 'password';
            if ($_POST['user'] == $username
                    && $_POST['pass'] == $password) {
                $loggedIn = TRUE;
                $_SESSION['user'] = strip_tags($username);
                $_SESSION['isLoggedIn'] = TRUE;
            } else {
                $message = 'Invalid Login';
            }
        } else {
            $message = 'Invalid Captcha';
        }
    }
}
```

你可能还想添加退出选项的代码，如“保护 PHP 会话”配方中所述：

```php
} elseif (isset($_POST['logout'])) {
    session_unset();
    session_destroy();
    setcookie('PHPSESSID', 0, time() - 3600);
    header('Location: ' . $_SERVER['REQUEST_URI']);
    exit;
}
```

然后你可以运行 `setCaptcha()`：

```php
setCaptcha($phrase, $label, $image);
```

最后，不要忘记视图逻辑，在此示例中，它呈现一个基本的登录表单。在 form 标签内部，你需要添加视图逻辑来显示验证码和标签：

```html
<tr>
    <th><?= $label; ?></th>
    <td><?= $image; ?><input type="text" name="captcha" /></td>
</tr>
```

以下是生成的输出结果：

![](img/39390f6d56c5a83b28db083a8bd5185c_495_0.png)

为了演示如何使用图片验证码，将 `chap_12_captcha_text.php` 中的代码复制到 `chap_12_captcha_image.php`。我们定义常量来表示我们将写入验证码图像的目录位置。（请务必创建此目录！）否则，自动加载和 use 语句的结构相似。注意，我们还定义了一个 TrueType 字体。差异部分以**粗体**标出：

```php
<?php
define('IMAGE_DIR', __DIR__ . '/captcha');
define('IMAGE_URL', '/captcha');
define('IMAGE_FONT', __DIR__ . '/FreeSansBold.ttf');
require __DIR__ . '/../Application/Autoload/Loader.php';
Application\Autoload\Loader::init(__DIR__ . '/..');
use Application\Captcha\Image;

session_start();
session_regenerate_id();
```

> **重要！** 字体可能受到版权、商标、专利或其他知识产权法的保护。如果你使用了未授权的字体，你和你的客户可能会在法庭上承担责任！请使用开源字体，或你在 web 服务器上拥有有效许可证的字体。

当然，在 `setCaptcha()` 函数中，我们使用 Image 类而不是 Reverse：

```php
function setCaptcha(&$phrase, &$label, &$image)
{
    $captcha = new Image(IMAGE_DIR, IMAGE_URL, IMAGE_FONT);
    $phrase  = $captcha->getPhrase();
    $label = $captcha->getLabel();
    $image = $captcha->getImage();
    $_SESSION['phrase'] = $phrase;
    return $captcha;
}
```

变量初始化与上一个脚本相同，登录处理也与上一个脚本相同：

```php
$image = '';
$label = '';
$phrase = $_SESSION['phrase'] ?? '';
$message = '';
$info = 'You Can Now See Super Secret Information!!!';
$loggedIn = $_SESSION['isLoggedIn'] ?? FALSE;
$loggedInUser = $_SESSION['user'] ?? 'guest';

if (!empty($_POST['login'])) {
// etc. -- identical to chap_12_captcha_text.php
```

即使视图逻辑也保持不变，因为我们使用的是 `getImage()`，对于图片验证码而言，它直接返回可用的 HTML。以下是使用 TrueType 字体的输出结果：

![](img/39390f6d56c5a83b28db083a8bd5185c_496_0.png)

## 更多...

如果你不想使用前面的代码生成自己的内部验证码，市面上有很多可用的库。大多数流行框架都具有这种功能。例如，Zend Framework 拥有其 `Zend\Captcha` 组件类。还有 reCAPTCHA，它通常作为服务被调用，其中你的应用程序向外部网站发出请求，该网站为你生成验证码和令牌。一个好的起始搜索地点是 [http://www.captcha.net/](http://www.captcha.net/) 网站。

## 参见

有关字体作为知识产权保护的更多信息，请参见位于 [`https://en.wikipedia.org/wiki/Intellectual_property_protection_of_typefaces`](https://en.wikipedia.org/wiki/Intellectual_property_protection_of_typefaces) 的文章。

## 在不使用 mcrypt 的情况下进行加密/解密

在一般的 PHP 社区成员中，有一个鲜为人知的事实：`mcrypt` 扩展，即大多数被认为安全的基于 PHP 的加密的核心，实际上并不安全。从安全角度来看，最大的问题之一是 `mcrypt` 扩展需要精通密码学的专业知识才能成功运行，而很少有程序员具备这种专业知识。这导致了严重的误用，并最终导致诸如 1/256 的数据损坏几率等问题。这不是一个好的概率。此外，开发人员对 `libmcrypt` 的支持（`mcrypt` 扩展所基于的核心库）在 2007 年被*放弃*，这意味着代码库已过时、漏洞百出，并且没有补丁应用机制。因此，理解如何在不使用 `mcrypt` 的情况下执行强加密/解密*至关重要*！

## 如何做...

1.  如果你想知道的话，前面提出的问题解决方案是使用 `openssl`。此扩展得到良好的维护，具有现代且非常强大的加密/解密功能。

    > **重要**
    >
    > 为了使用任何 `openssl*` 函数，必须编译并启用 PHP 的 `openssl` 扩展！此外，你需要在 web 服务器上安装最新的 OpenSSL 包。

2.  首先，你需要确定你的安装中有哪些可用的密码方法。为此，你可以使用 `openssl_get_cipher_methods()` 命令。示例包括基于**高级加密标准**（AES）、**BlowFish**（BF）、**CAMELLIA**、**CAST5**、**数据加密标准**（DES）、**Rivest 密码**（RC）（也被亲切地称为**Ron's Code**）以及 **SEED** 的算法。你会注意到，此方法显示密码方法在大写和小写中是重复的。

3.  接下来，你需要弄清楚哪种方法最适合你的需求。下表对各种方法进行了简要总结：

| 方法 | 发布年份 | 密钥大小（位） | 密钥块大小（字节） | 备注 |
| :--- | :--- | :--- | :--- | :--- |
| camellia | 2000 | 128, 192, 256 | 16 | 由三菱和 NTT 开发 |
| aes | 1998 | 128, 192, 256 | 16 | 由 Joan Daemen 和 Vincent Rijmen 开发。最初作为 Rijndael 提交 |
| seed | 1998 | 128 | 16 | 由韩国信息保密局开发 |
| cast5 | 1996 | 40 到 128 | 8 | 由 Carlisle Adams 和 Stafford Tavares 开发 |
| bf | 1993 | 1 到 448 | 8 | 由 Bruce Schneier 设计 |
| rc2 | 1987 | 8 到 1,024（默认为 64） | 8 | 由 Ron Rivest 设计（RSA 的核心创始人之一） |
| des | 1977 | 56（+8 位奇偶校验位） | 8 | 由 IBM 开发，基于 Horst Feistel 的工作 |

4.  另一个考虑因素是你首选的分组密码**操作模式**。常见的选择在下表中总结：

| 模式 | 全称 | 备注 |
| :--- | :--- | :--- |
| ECB | 电子码本（Electronic Code Book） | 不需要初始化向量（IV）；支持加密和解密的并行化；简单且快速；不隐藏数据模式；不推荐!!! |
| CBC | 密码块链接（Cipher Block Chaining） | 需要 IV；后续块即使相同，也与前一块进行 XOR 运算，从而产生更好的整体加密效果；如果 IV 是可预测的，第一块可以被解码，导致剩余消息暴露；消息必须填充为密码块大小的整数倍；仅支持解密的并行化 |
| CFB | 密码反馈（Cipher Feedback） | CBC 的近亲，区别在于加密是以相反的方向执行的 |





## 13
## 最佳实践、测试与调试

在本章中，我们将涵盖以下主题：

- 使用特质（Traits）和接口（Interfaces）
- 通用异常处理器
- 通用错误处理器
- 编写简单的测试
- 编写测试套件
- 生成伪造的测试数据
- 使用 `session_start` 参数自定义会话

### 引言

在本章中，我们将展示特质和接口是如何协同工作的。然后，我们将关注一种回退机制的设计，该机制将在你无法（或忘记）定义特定的 `try/catch` 块的情况下捕获错误和异常。接着，我们将进入单元测试的世界，首先向你展示如何编写简单的测试，然后如何将这些测试组合成测试套件。接下来，我们将定义一个类，让你可以创建任意数量的通用测试数据。最后，我们将讨论如何利用新的 PHP 7 功能轻松管理会话。

| 模式 | 全称 | 备注 |
|---|---|---|
| OFB | 输出反馈（Output Feedback） | 非常对称：加密和解密是相同的；完全不支持并行化 |
| CTR | 计数器（Counter） | 操作类似于 OFB；支持加密和解密的并行化 |
| CCM | 带有 CBC-MAC 的计数器（Counter with CBC-MAC） | CTR 的衍生模式；仅设计用于 128 位的块长度；提供认证和保密性；**CBC-MAC** 代表 **分组密码链接 - 消息认证码（Cipher Block Chaining - Message Authentication Code）** |
| GCM | 伽罗瓦/计数器模式（Galois/Counter Mode） | 基于 CTR 模式；每个待加密的数据流应使用不同的 IV（初始化向量）；吞吐量极高（与其他模式相比）；支持加密和解密的并行化 |
| XTS | 基于 XEX 的调整码本分组密码模式（带有密文窃取）（XEX-based Tweaked-codebook mode with ciphertext Stealing） | 相对较新（2010 年）且快速；使用两个密钥；增加了可以作为单个块安全加密的数据量 |

5. 在选择加密方法和模式之前，你还需要确定加密内容是否需要在你的 PHP 应用外部进行解密。例如，如果你将数据库凭据加密并存储到独立的文本文件中，你是否需要能够从命令行解密它们？如果需要，请确保你选择的加密方法和操作模式在目标操作系统上得到支持。

6. 为 **IV** 提供的字节数根据所选的加密方法而异。为了获得最佳结果，请使用 `random_bytes()`（PHP 7 中新引入），它会返回一个真正的 **CSPRNG**（密码学安全伪随机数生成器）字节序列。IV 的长度变化很大。建议从 16 字节大小开始尝试。如果生成了 `警告`，将会显示该算法应提供的正确字节数，因此请相应地调整大小：

```php
$iv = random_bytes(16);
```

7. 要执行加密，请使用 `openssl_encrypt()`。以下是应传递的参数：

| 参数 | 备注 |
| :--- | :--- |
| Data | 需要加密的明文。 |
| Method | 使用 `openssl_get_cipher_methods()` 识别的方法之一。标识格式如下：`method_key_size-cipher_mode`。因此，例如，如果你想要 AES 方法，256 的密钥大小，以及 GCM 模式，你会输入 `aes-256-gcm`。 |
| Password | 虽然文档中注明为 *密码*，但可以将此参数视为 *密钥*。使用 `random_bytes()` 生成一个密钥，其字节数应与所需的密钥大小匹配。 |
| Options | 在你对 openssl 加密有更多经验之前，建议坚持使用默认值 0。 |
| IV | 使用 `random_bytes()` 生成一个 IV，其字节数应与加密方法匹配。 |

8. 作为示例，假设你希望选择 AES 加密方法，256 的密钥大小，以及 XTS 模式。以下是用于加密的代码：

```php
$plainText = 'Super Secret Credentials';
$key = random_bytes(16);
$method = 'aes-256-xts';
$cipherText = openssl_encrypt($plainText, $method, $key, 0, $iv);
```

9. 要解密，请使用相同的 `$key` 和 `$iv` 值，并结合 `openssl_decrypt()` 函数：

```php
$plainText = openssl_decrypt($cipherText, $method, $key, 0, $iv);
```

## 工作原理...

为了查看哪些加密方法可用，请创建一个名为 `chap_12_openssl_encryption.php` 的 PHP 脚本并运行此命令：

```php
<?php
  echo implode(',', openssl_get_cipher_methods());
```

输出应该看起来像这样：

![](img/39390f6d56c5a83b28db083a8bd5185c_501_0.png)

接下来，你可以添加待加密的明文、方法、密钥和 IV 的值。作为示例，尝试使用 AES，密钥大小为 256，使用 XTS 操作模式：

```php
$plainText = 'Super Secret Credentials';
$method = 'aes-256-xts';
$key = random_bytes(16);
$iv = random_bytes(16);
```

要加密，你可以使用 `openssl_encrypt()`，指定之前配置的参数：

```php
$cipherText = openssl_encrypt($plainText, $method, $key, 0, $iv);
```

你可能还希望对结果进行 base64 编码，使其更具可用性：

```php
$cipherText = base64_encode($cipherText);
```

要解密，请使用相同的 `$key` 和 `$iv` 值。别忘了先解码 base64 值：

```php
$plainText = openssl_decrypt(base64_decode($cipherText), $method, $key, 0, $iv);
```

以下是显示 base64 编码的密文，随后是解密后的明文的输出：

```text
Terminal
ENCODED:
BEER2t/v0MvKaO0VlLJBV3pZNFE2OvyI53FTiMGrek==

DECODED:
Super Secret Credentials

---------------------
<program exited with code: 0>
Press return to continue
```

如果你为所选加密方法提供了错误数量的 IV 字节，将会显示一条警告消息：

```text
Terminal
Warning: openssl_encrypt(): IV passed is only 12 bytes long, cipher expects an IV of precisely 16 bytes, padding with \0 in /home/d/Desktop/repos/php7_recipes/source/chapter12/chap_12_openssl_encryption.php on line 10
ENCODED:
aTGdZG1kSG9SQNrUmx1d2k1zOQwjhGUHziH09cVXK=

Warning: openssl_decrypt(): IV passed is only 12 bytes long, cipher expects an IV of precisely 16 bytes, padding with \0 in /home/d/Desktop/repos/php7_recipes/source/chapter12/chap_12_openssl_encryption.php on line 16
DECODED:
Super Secret Credentials

---------------------
<program exited with code: 0>
Press return to continue
```

## 更多参考...

在 PHP 7 中，使用 `openssl_encrypt()` 和 `openssl_decrypt()` 时存在问题，所支持的 **认证加密（Authenticated Encrypt with Associated Data，AEAD）** 模式为：GCM 和 CCM。相应地，在 PHP 7.1 中，这些函数增加了三个额外参数，如下所示：

| 参数 | 描述 |
|---|---|
| `$tag` | 通过引用传递的认证标签；如果认证失败，变量值保持不变 |
| `$aad` | 附加认证数据 |
| `$tag_length` | 对于 GCM 模式为 4 到 16；对于 CCM 模式没有限制；仅用于 `openssl_encrypt()` |

有关更多信息，你可以参考 `https://wiki.php.net/rfc/openssl_aead`。

## 另请参阅

关于为什么 mcrypt 扩展在 PHP 7.1 中被弃用的出色讨论，请参阅 https://wiki.php.net/rfc/mcrypt-viking-funeral 上的文章。关于块加密的良好描述，它构成了各种加密方法的基础，请参阅 https://en.wikipedia.org/wiki/Block_cipher 上的文章。关于 AES 的出色描述，请参阅 https://en.wikipedia.org/wiki/Advanced_Encryption_Standard。描述加密操作模式的好文章可以在 https://en.wikipedia.org/wiki/Block_cipher_mode_of_operation 上看到。

![](img/39390f6d56c5a83b28db083a8bd5185c_503_0.png)

对于一些较新的模式，如果要加密的数据小于块大小，`openssl_decrypt()` 将不返回任何值。如果你将数据填充到至少等于块大小，问题就会消失。大多数模式都实现了内部填充，因此这不是一个问题。在一些较新的模式（即 xts）中，你可能会看到这个问题。在将代码投入生产之前，务必对短于八个字符的数据短字符串进行测试。




## 使用特质和接口

将接口作为建立一组类分类的手段并保证某些方法存在的存在，被认为是一种最佳实践。特质和接口通常协同工作，是实现中的一个重要方面。每当有一个经常使用且定义了代码不变的方法（例如 setter 或 getter）的接口时，定义一个包含实际代码实现的 Trait 也是有用的。

### 如何实现...

- 1. 在本示例中，我们将使用第 4 章 *使用 PHP 面向对象编程* 中首次介绍的 `ConnectionAwareInterface`。该接口定义了一个 `setConnection()` 方法，用于设置 `$connection` 属性。`Application\Generic` 命名空间中的两个类 `CountryList` 和 `CustomerList` 包含冗余代码，这些代码与接口中定义的方法相匹配。

- 2. 以下是变更前的 `CountryList` 的样子：

```php
class CountryList
{
    protected $connection;
    protected $key    = 'iso3';
    protected $value  = 'name';
    protected $table  = 'iso_country_codes';

    public function setConnection(Connection $connection)
    {
        $this->connection = $connection;
    }

    public function list()
    {
        $list = [];
        $sql = sprintf('SELECT %s,%s FROM %s', $this->key,
                $this->value, $this->table);
        $stmt = $this->connection->pdo->query($sql);
        while ($item = $stmt->fetch(PDO::FETCH_ASSOC)) {
            $list[$item[$this->key]] =  $item[$this->value];
        }
        return $list;
    }
}
```

- 3. 现在我们将 `list()` 移动到一个名为 `ListTrait` 的特性中：

```php
trait ListTrait
{
    public function list()
    {
        $list = [];
        $sql = sprintf('SELECT %s,%s FROM %s',
                       $this->key, $this->value, $this->table);
        $stmt = $this->connection->pdo->query($sql);
        while ($item = $stmt->fetch(PDO::FETCH_ASSOC)) {
            $list[$item[$this->key]] = $item[$this->value];
        }
        return $list;
    }
}
```

- 4. 然后，我们可以将 `ListTrait` 中的代码插入到一个新类 `CountryListUsingTrait` 中，如下所示：

```php
class CountryListUsingTrait
{
    use ListTrait;
    protected $connection;
    protected $key = 'iso3';
    protected $value = 'name';
    protected $table = 'iso_country_codes';
    public function setConnection(Connection $connection)
    {
        $this->connection = $connection;
    }
}
```

- 5. 接下来，我们观察到许多类都需要设置一个连接实例。同样，这也需要用到特性。不过，这次我们将该特性放在 `Application\Database` 命名空间中。以下是新的特性：

```php
namespace Application\Database;
trait ConnectionTrait
{
    protected $connection;
    public function setConnection(Connection $connection)
    {
        $this->connection = $connection;
    }
}
```

- 6. **特性常用于避免代码重复。** 通常你也需要识别使用特性的类。实现这一目标的一个好方法是开发一个与特性相匹配的接口。在本例中，我们将定义 `Application\Database\ConnectionAwareInterface`：

```php
namespace Application\Database;
use Application\Database\Connection;
interface ConnectionAwareInterface
{
    public function setConnection(Connection $connection);
}
```

- 7. **以下是修订后的 `CountryListUsingTrait` 类。** 请注意，由于新特性受其命名空间位置的影响，我们需要在类顶部添加一个 `use` 语句。你还会注意到，我们实现了 `ConnectionAwareInterface` 以表明该类需要特性中定义的方法。请注意，我们正在利用新的 PHP 7 分组 `use` 语法：

```php
namespace Application\Generic;
use PDO;
use Application\Database\ {
    Connection, ConnectionTrait, ConnectionAwareInterface
};
class CountryListUsingTrait implements ConnectionAwareInterface
{
    use ListTrait;
    use ConnectionTrait;
    protected $key     = 'iso3';
    protected $value  = 'name';
    protected $table  = 'iso_country_codes';
}
```

## 工作原理...

首先，确保在 *第 4 章，使用 PHP 面向对象编程* 中开发的类已创建。这些类包括在 *第 4 章，使用 PHP 面向对象编程* 的 *使用接口* 配方中讨论的 `Application\Generic\CountryList` 和 `Application\Generic\CustomerList` 类。将每个类保存在 `Application\Generic` 文件夹中的新文件 `CountryListUsingTrait.php` 和 `CustomerListUsingTrait.php` 中。请务必更改类名以匹配新文件名！

如步骤 3 所述，从 `CountryListUsingTrait.php` 和 `CustomerListUsingTrait.php` 列表类中移除 `list()` 方法，并添加 `use ListTrait;` 以替代被移除的方法。将移除的代码放入同一文件夹中名为 `ListTrait.php` 的单独文件中。

你还会注意到两个列表类之间存在更多的代码重复，在这种情况下是 `setConnection()` 方法。这又需要另一个特性！

从 `CountryListUsingTrait.php` 和 `CustomerListUsingTrait.php` 列表类中剪切 `setConnection()` 方法，并将移除的代码放入名为 `ConnectTrait.php` 的单独文件中。由于该特性在逻辑上与 `ConnectionAwareInterface` 和 `Connection` 相关，因此将其文件放在 `Application\Database` 文件夹中并相应地指定其命名空间是合理的。

最后，如步骤 6 所述定义 `Application\Database\ConnectionAwareInterface`。以下是所有更改后的最终 `Application\Generic\CustomerListUsingTrait` 类：

```php
<?php
namespace Application\Generic;
use PDO;
use Application\Database\Connection;
use Application\Database\ConnectTrait;
use Application\Database\ConnectionAwareInterface;
class CustomerListUsingTrait implements ConnectionAwareInterface
{
    use ListTrait;
    use ConnectTrait;

    protected $key = 'id';
    protected $value = 'name';
    protected $table = 'customer';
}
```

现在你可以将第 4 章 *使用 PHP 面向对象编程* 中提到的 `chap_04_op_simple_interfaces_example.php` 文件复制到名为 `chap_13_trait_and_interface.php` 的新文件中。将 `CountryList` 的引用更改为 `CountryListUsingTrait`。同样，将 `CustomerList` 的引用更改为 `CustomerListUsingTrait`。其他代码可以保持不变：

```php
<?php
define('DB_CONFIG_FILE', './../config/db.config.php');
require __DIR__ . '/../Application/Autoload/Loader.php';
Application\Autoload\Loader::init(__DIR__ . '/../');
$parms = include __DIR__ . DB_CONFIG_FILE;
try {
    $list = Application\Generic\ListFactory::factory(
        new Application\Generic\CountryListUsingTrait(), $parms);
    echo 'Country List' . PHP_EOL;
    foreach ($list->list() as $item) echo $item . ' ';
    $list = Application\Generic\ListFactory::factory(
        new Application\Generic\CustomerListUsingTrait(),
        $parms);
    echo 'Customer List' . PHP_EOL;
    foreach ($list->list() as $item) echo $item . ' ';
} catch (Throwable $e) {
    echo $e->getMessage();
}
```

输出将与第 4 章 *使用面向对象编程* 的 *使用接口* 配方中描述的完全一致。你可以在下面的截图中看到输出中的国家列表部分：

![](img/39390f6d56c5a83b28db083a8bd5185c_510_0.png)

下一张图片显示了输出中的客户列表部分：

![](img/39390f6d56c5a83b28db083a8bd5185c_511_0.png)

## 通用异常处理器

异常在结合 `try`/`catch` 块中的代码使用时特别有用。然而，在某些情况下使用这种结构可能会很尴尬，使代码几乎无法阅读。另一个考虑因素是，许多类最终会抛出你未预见的异常。在这种情况下，拥有某种备用异常处理器将非常理想。

### 如何实现...

- 1. 首先，我们定义一个通用的异常处理类 `Application\Error\Handler`：

```php
namespace Application\Error;
class Handler
{
    // 代码在此处
}
```

- 2. 我们定义代表日志文件的属性。如果未提供名称，则按年、月和日命名。在构造函数中，我们使用 `set_exception_handler()` 将本类中的 `exceptionHandler()` 方法指定为备用处理器：

```php
protected $logFile;
public function __construct(
    $logFileDir = NULL, $logFile = NULL)
```




### 3. 接下来，我们定义 `exceptionHandler()` 方法，该方法接受一个 `Exception` 对象作为参数。我们在日志文件中记录日期时间、异常类名及其消息：

```php
public function exceptionHandler($ex)
{
    $message = sprintf('%1$s : %2$s : %s' . PHP_EOL,
        date('Y-m-d H:i:s'), get_class($ex), $ex->getMessage());
    file_put_contents($this->logFile, $message, FILE_APPEND);
}
```

### 4. 如果我们在代码中专门使用了 `try`/`catch` 块，这将覆盖我们的通用异常处理器。另一方面，如果我们不使用 `try`/`catch` 且抛出了异常，通用异常处理器将会生效。

> **最佳实践**
>
> 你应该始终使用 `try`/`catch` 来捕获异常，并尽可能让应用程序继续运行。此处描述的异常处理器仅旨在允许应用程序在未被捕获的异常发生情况下“优雅地”终止。

## 工作原理...

首先，将前文配方中展示的代码放入 `Application\Error` 文件夹下的 `Handler.php` 文件中。接下来，定义一个测试类来抛出异常。为了说明目的，创建一个 `Application\Error\ThrowsException` 类，该类将抛出异常。例如，设置一个 `PDO` 实例，并将错误模式设置为 `PDO::ERRMODE_EXCEPTION`。然后，编写一个保证失败的 SQL 语句：

```php
namespace Application\Error;
use PDO;
class ThrowsException
{
    protected $result;
    public function __construct(array $config)
    {
        $dsn = $config['driver'] . ':';
        unset($config['driver']);
        foreach ($config as $key => $value) {
            $dsn .= $key . '=' . $value . ';';
        }
        $pdo = new PDO(
            $dsn,
            $config['user'],
            $config['password'],
            [PDO::ATTR_ERRMODE => PDO::ERRMODE_EXCEPTION]);
        $stmt = $pdo->query('This Is Not SQL');
        while ($row = $stmt->fetch(PDO::FETCH_ASSOC)) {
            $this->result[] = $row;
        }
    }
}
```

接下来，定义一个名为 `chap_13_exception_handler.php` 的调用程序，该程序设置自动加载并使用相应的类：

```php
<?php
define('DB_CONFIG_FILE', __DIR__ . '/../config/db.config.php');
$config = include DB_CONFIG_FILE;
require __DIR__ . '/../Application/Autoload/Loader.php';
Application\Autoload\Loader::init(__DIR__ . '/../');
use Application\Error\{ Handler, ThrowsException };
```

在此阶段，如果你创建一个 `ThrowsException` 实例而没有实现通用处理器，将会产生致命错误，因为抛出了异常但未被捕获：

```php
$throw1 = new ThrowsException($config);
```

![](img/39390f6d56c5a83b28db083a8bd5185c_513_0.png)

另一方面，如果你使用 `try`/`catch` 块，异常将被捕获，如果应用程序足够稳定，它允许应用程序继续运行：

```php
try {
    $throws1 = new ThrowsException($config);
} catch (Exception $e) {
    echo 'Exception Caught: ' . get_class($e) . ':' . $e->getMessage()
        . PHP_EOL;
}
echo 'Application Continues ...' . PHP_EOL;
```

你将观察到以下输出：

![](img/39390f6d56c5a83b28db083a8bd5185c_514_0.png)

为了演示异常处理器的使用，在 `try`/`catch` 块之前定义一个 `Handler` 实例，传入代表包含日志文件的目录的参数。在 `try`/`catch` 之后，在块外部，创建另一个 `ThrowsException` 实例。当你运行此示例程序时，你会注意到第一个异常在 `try`/`catch` 块内部被捕获，而第二个异常由处理器捕获。你还会注意到，在处理器之后，应用程序终止：

```php
$handler = new Handler(__DIR__ . '/logs');
try {
    $throws1 = new ThrowsException($config);
} catch (Exception $e) {
    echo 'Exception Caught: ' . get_class($e) . ':'
        . $e->getMessage() . PHP_EOL;
}
$throws1 = new ThrowsException($config);
echo 'Application Continues ...' . PHP_EOL;
```

以下是完成的示例程序的输出，以及日志文件的内容：

```text
edged:~/Desktop/Repos/php7_recipes/source/chapter13$ php chap_13_exception_handler.php
Exception Caught: PDOexception::SQLSTATE[42000]: Syntax error or access violation: 1064 You have an error in your SQL syntax; check the manual that corresponds to your MySQL server version for the right syntax to use near 'This is Not SQL' at line 1
edged:~/Desktop/Repos/php7_recipes/source/chapter13$ cat logs/20160610.log
2016-06-10 06:25:37 :: PDOException :: SQLSTATE[42000]: Syntax error or access violation: 1064 You have an error in your SQL syntax; check the manual that corresponds to your MySQL server version for the right syntax to use near "This is Not SQL" at line 1
edged:~/Desktop/Repos/php7_recipes/source/chapter13$
```

## 参见

- 或许回顾 `set_exception_handler()` 函数的文档是个好主意。特别看看 Anonymous 7 年前发布的注释（至今仍相关），它阐明了该函数的工作方式：http://php.net/manual/en/function.set-exception-handler.php.

## 通用错误处理器

开发通用错误处理器的过程与前文配方相当类似。然而，存在一些差异。首先，在 PHP 7 中，一些错误被抛出且可被捕获，而其他错误则会直接让你的应用程序停止运行。为了进一步增加混淆，一些错误被当作异常处理，而其他错误则派生自新的 PHP 7 `Error` 类。幸运的是，在 PHP 7 中，`Error` 和 `Exception` 都实现了一个名为 `Throwable` 的新接口。因此，如果你不确定你的代码将抛出 `Exception` 还是 `Error`，只需捕获 `Throwable` 的实例即可同时捕获两者。

## 操作方法...

1. 修改前文配方中定义的 `Application\ErrorHandler` 类。在构造函数中，将新的 `errorHandler()` 方法设置为默认错误处理器：

```php
public function __construct($logFileDir = NULL, $logFile = NULL)
{
    $logFile = $logFile ?? date('Ymd') . '.log';
    $logFileDir = $logFileDir ?? __DIR__;
    $this->logFile = $logFileDir . '/' . $logFile;
    $this->logFile = str_replace('//', '/', $this->logFile);
    set_exception_handler([$this, 'exceptionHandler']);
    set_error_handler([$this, 'errorHandler']);
}
```

2. 然后，我们使用文档中定义的参数定义新方法。与我们的异常处理器一样，我们将信息记录到日志文件中：

```php
public function errorHandler($errno, $errstr, $errfile, $errline)
{
    $message = sprintf('ERROR: %s : %d : %s : %s : %s' . PHP_EOL,
        date('Y-m-d H:i:s'), $errno, $errstr, $errfile, $errline);
    file_put_contents($this->logFile, $message, FILE_APPEND);
}
```

3. 此外，为了能够区分错误和异常，在 `exceptionHandler()` 方法中发送给日志文件的消息中添加 `EXCEPTION`：

```php
public function exceptionHandler($ex)
{
    $message = sprintf('EXCEPTION: %1$s : %2$s : %s' . PHP_EOL,
        date('Y-m-d H:i:s'), get_class($ex), $ex->getMessage());
    file_put_contents($this->logFile, $message, FILE_APPEND);
}
```

## 工作原理...

首先，对先前定义的 `Application\Error\Handler` 进行修改。接下来，创建一个抛出错误的类，在本说明中，该类可以定义为 `Application\Error\ThrowsError`。例如，你可以有一个方法尝试除以零的操作，另一个方法尝试使用 `eval()` 解析非 PHP 代码：

```php
<?php
namespace Application\Error;
class ThrowsError
{
    const NOT_PARSE = 'this will not parse';
    public function divideByZero()
    {
        $this->zero = 1 / 0;
    }
    public function willNotParse()
    {
        eval(self::NOT_PARSE);
    }
}
```

然后，你可以定义一个名为 `chap_13_error_throwable.php` 的调用程序，该程序设置自动加载，使用相应的类，并创建 `ThrowsError` 的实例：

```php
<?php
require __DIR__ . '/../../Application/Autoload/Loader.php';
Application\Autoload\Loader::init(__DIR__ . '/..');
```





```php
use Application\Error\{ Handler, ThrowsError };
$error = new ThrowsError();
```

然后，如果调用这两个方法，在没有 try/catch 块且未定义通用错误处理程序的情况下，第一个方法会生成一个警告（Warning），而第二个方法则抛出一个 ParseError：

```php
$error->divideByZero();
$error->willNotParse();
echo 'Application continues ... ' . PHP_EOL;
```

由于这是一个错误，程序执行将停止，因此你不会看到“Application continues ...”：

![](img/39390f6d56c5a83b28db083a8bd5185c_517_0.png)

如果你用 try/catch 块包裹方法调用并捕获 Throwable，代码执行将继续进行：

```php
try {
    $error->divideByZero();
} catch (Throwable $e) {
    echo 'Error Caught: ' . get_class($e) . ':'
        . $e->getMessage() . PHP_EOL;
}
try {
    $error->willNotParse();
} catch (Throwable $e) {
    echo 'Error Caught: ' . get_class($e) . ':'
        . $e->getMessage() . PHP_EOL;
}
echo 'Application continues ... ' . PHP_EOL;
```

从以下输出中，你还会注意到程序以退出代码 `0` 结束，这告诉我们一切正常：

![](img/39390f6d56c5a83b28db083a8bd5185c_518_0.png)

最后，在 *try/catch* 块之后，再次运行这些错误，并将 `echo` 语句移至末尾。你会在输出中看到错误已被捕获，但在日志文件中，请注意 `DivisionByZeroError` 被异常处理程序捕获，而 `ParseError` 被错误处理程序捕获：

```php
$handler = new Handler(__DIR__ . '/logs');
$error->divideByZero();
$error->willNotParse();
echo 'Application continues ... ' . PHP_EOL;
```

![](img/39390f6d56c5a83b28db083a8bd5185c_518_1.png)

## 另请参阅

- PHP 7.1 允许你在 `catch ()` 子句中指定多个类。因此，你不仅可以指定单个 `Throwable`，还可以写成 `catch (Exception | Error $e) { xxx }`

## 编写简单测试

测试 PHP 代码的主要方法是使用 **PHPUnit**，它基于一种称为**单元测试**的方法论。单元测试的哲学非常简单：你将代码分解为尽可能小的逻辑单元。然后，你孤立地测试每个单元，以确认其按预期执行。这些预期被编码为一系列**断言**。如果所有断言都返回 TRUE，则该单元通过了测试。

![](img/39390f6d56c5a83b28db083a8bd5185c_519_0.png)

对于过程式 PHP，一个单元是一个函数。对于 OOP PHP，单元是类中的一个方法。

### 如何实现...

1. 首要任务是直接在开发服务器上安装 PHPUnit，或者下载源代码，其形式为一个单一的 **phar (PHP archive)** 文件。访问 PHPUnit 的官方网站（[https://phpunit.de/](https://phpunit.de/)）可以直接从主页面下载。

2. 不过，最佳实践是使用包管理器来安装和维护 PHPUnit。为此，我们将使用一个名为 **Composer** 的包管理程序。要安装 Composer，请访问主网站 [https://getcomposer.org/](https://getcomposer.org/) 并按照下载页面上的说明操作。撰写本文时的当前操作如下。请注意，你需要用当前版本的哈希值替换 `<hash>`：

   ```php
   php -r "copy('https://getcomposer.org/installer',
         'composer-setup.php');"
   php -r "if (hash_file('SHA384', 'composer-setup.php')
       === '<hash>') {
       echo 'Installer verified';
   } else {
       echo 'Installer corrupt'; unlink('composer-setup.php');
   } echo PHP_EOL;"
   php composer-setup.php
   php -r "unlink('composer-setup.php');"
   ```

   ![](img/39390f6d56c5a83b28db083a8bd5185c_519_1.png)

## 最佳实践

使用 Composer 等包管理程序的优势在于，它不仅用于安装，还可以用于更新应用程序使用的任何外部软件（如 PHPUnit）。

3. 接下来，我们使用 Composer 安装 PHPUnit。这可以通过创建一个 `composer.json` 文件来实现，该文件包含一系列指令，概述项目参数和依赖项。对这些指令的完整描述超出了本书的范围；然而，为了本食谱的目的，我们使用关键参数 require 创建一组最小指令。你还会注意到，文件的内容采用 **JavaScript Object Notation (JSON)** 格式：

   ```json
   {
       "require-dev" : {
           "phpunit/phpunit" : "*"
       }
   }
   ```

4. 要从命令行执行安装，我们运行以下命令。输出显示如下：

   ```bash
   php composer.phar install
   ```

   ![](img/39390f6d56c5a83b28db083a8bd5185c_520_0.png)

5. PHPUnit 及其依赖项被放置在一个 vendor 文件夹中，如果该文件夹尚不存在，Composer 会创建它。调用 PHPUnit 的主要命令会建立符号链接到 vendor/bin 文件夹。如果你将此文件夹放入你的 PATH，只需运行此命令，它会检查版本并顺带确认安装成功：

   ```bash
   phpunit --version
   ```

## 运行简单测试

1. 为了说明目的，假设我们有一个 `chap_13_unit_test_simple.php` 文件，其中包含 `add()` 函数：

   ```php
   <?php
   function add($a = NULL, $b = NULL)
   {
       return $a + $b;
   }
   ```

2. 测试作为继承自 `PHPUnit\Framework\TestCase` 的类来编写。如果你正在测试一个函数库，在测试类的开头，包含含有函数定义的文件。然后，你会编写以 test 单词开头的方法，通常后面跟着你要测试的函数名称，可能还有一些额外的 CamelCase 单词来进一步描述测试。为了本食谱的目的，我们将定义一个 `SimpleTest` 测试类：

   ```php
   <?php
   use PHPUnit\Framework\TestCase;
   require_once __DIR__ . '/chap_13_unit_test_simple.php';
   class SimpleTest extends TestCase
   {
       // testXXX() methods go here
   }
   ```

3. 断言是任何测试集的核心。**另请参阅**部分提供了完整断言列表的文档参考。断言是一个 PHPUnit 方法，它将已知值与你要测试的内容产生的值进行比较。一个例子是 `assertEquals()`，它检查第一个参数是否等于第二个。以下示例测试了一个名为 `add()` 的方法，并确认 **2** 是 `add(1,1)` 的返回值：

   ```php
   public function testAdd()
   {
       $this->assertEquals(2, add(1,1));
   }
   ```

4. 你还可以测试某事物*不为真*的情况。此示例断言 `1 + 1` 不等于 **3**：

   ```php
   $this->assertNotEquals(3, add(1,1));
   ```

5. 在测试字符串时极其有用的断言是 `assertRegExp()`。假设，为了说明目的，我们正在测试一个生成 HTML 表格的函数，该函数基于多维数组：

   ```php
   function table(array $a)
   {
       $table = '<table>';
       foreach ($a as $row) {
           $table .= '<tr><td>';
           $table .= implode('</td><td>', $row);
           $table .= '</td></tr>';
       }
       $table .= '</table>';
       return $table;
   }
   ```

6. 我们可以构建一个简单的测试，确认输出包含 `<table>`、一个或多个字符，然后是 `</table>`。此外，我们希望确认存在 `<td>B</td>` 元素。在编写测试时，我们构建一个测试数组，由包含字母 A–C、D–F 和 G–I 的三个子数组组成。然后将测试数组传递给函数，并对结果运行断言：

   ```php
   public function testTable()
   {
       $a = [range('A', 'C'),range('D', 'F'),range('G','I')];
       $table = table($a);
       $this->assertRegExp('!^<table>.+</table>$!', $table);
       $this->assertRegExp('!<td>B</td>!', $table);
   }
   ```

7. 要测试一个类，只需包含定义要测试类的文件，而不是包含函数库。为了说明目的，让我们将前面显示的函数库移动到一个 Demo 类中：

   ```php
   <?php
   class Demo
   {
       public function add($a, $b)
       {
           return $a + $b;
       }

       public function sub($a, $b)
       {
           return $a - $b;
       }
       // etc.
   }
   ```




在我们的 `SimpleClassTest` 测试类中，我们引入代表 `Demo` 类的文件，而不是引入库文件。我们需要一个 `Demo` 实例才能运行测试。为此，我们使用了一个专门设计的 `setup()` 方法，该方法会在每个测试之前运行。此外，您还会注意到一个 `teardown()` 方法，它会在每个测试之后立即运行：

```php
<?php
use PHPUnit\Framework\TestCase;
require_once __DIR__ . '/Demo.php';

class SimpleClassTest extends TestCase
{
    protected $demo;

    public function setUp()
    {
        $this->demo = new Demo();
    }

    public function tearDown()
    {
        unset($this->demo);
    }

    public function testAdd()
    {
        $this->assertEquals(2, $this->demo->add(1, 1));
    }

    public function testSub()
    {
        $this->assertEquals(0, $this->demo->sub(1, 1));
    } // 等等
}
```

> `setup()` 和 `teardown()` 之所以分别在每个测试之前和之后运行，是为了确保一个全新的测试环境。这样，一个测试的结果就不会影响另一个测试的结果。

## 测试数据库 Model 类

1. 当测试具有数据库访问权限的类（例如 Model 类）时，会有其他需要考虑的问题。主要的考虑因素是，您应该针对测试数据库而不是用于生产环境的真实数据库运行测试。最后一点是，通过使用测试数据库，您可以预先填充适当且受控的数据。`setup()` 和 `teardown()` 也可以用来添加或删除测试数据。

2. 作为一个使用数据库的类的示例，我们将定义一个类 `VisitorOps`。这个新类将包含用于添加、删除和查找访客的方法。请注意，我们还添加了一个方法，用于返回最后执行的 SQL 语句：

```php
<?php
require __DIR__ . './../Application/Database/Connection.php';
use Application\Database\Connection;

class VisitorOps
{
    const TABLE_NAME = 'visitors';
    protected $connection;
    protected $sql;

    public function __construct(array $config)
    {
        $this->connection = new Connection($config);
    }

    public function getSql()
    {
        return $this->sql;
    }

    public function findAll()
    {
        $sql = 'SELECT * FROM ' . self::TABLE_NAME;
        $stmt = $this->runSql($sql);
        while ($row = $stmt->fetch(PDO::FETCH_ASSOC)) {
            yield $row;
        }
    }

    public function findById($id)
    {
        $sql = 'SELECT * FROM ' . self::TABLE_NAME;
        $sql .= ' WHERE id = ?';
        $stmt = $this->runSql($sql, [$id]);
        return $stmt->fetch(PDO::FETCH_ASSOC);
    }

    public function removeById($id)
    {
        $sql = 'DELETE FROM ' . self::TABLE_NAME;
        $sql .= ' WHERE id = ?';
        return $this->runSql($sql, [$id]);
    }

    public function addVisitor($data)
    {
        $sql = 'INSERT INTO ' . self::TABLE_NAME;
        $sql .= ' (' . implode(',', array_keys($data)) . ')';
        $sql .= ' VALUES ';
        $sql .= ' ( :' . implode(',', array_keys($data)) . ')';
        $this->runSql($sql, $data);
        return $this->connection->pdo->lastInsertId();
    }

    public function runSql($sql, $params = NULL)
    {
        $this->sql = $sql;
        try {
            $stmt = $this->connection->pdo->prepare($sql);
            $result = $stmt->execute($params);
        } catch (Throwable $e) {
            error_log(__METHOD__ . ':' . $e->getMessage());
            return FALSE;
        }
        return $stmt;
    }
}
```

3. 对于涉及数据库的测试，建议使用测试数据库，而不是正在运行的生产数据库。相应地，您将需要一组额外的数据库连接参数，以便在 `setup()` 方法中用于建立数据库连接。
4. 您可能希望建立一组一致的示例数据块。这可以在 `setup()` 方法中插入到测试数据库中。
5. 最后，您可能会希望在每次测试之后重置测试数据库，这在 `teardown()` 方法中完成。

## 使用模拟类

1. 在某些情况下，测试将访问需要外部资源的复杂组件。例如，需要访问数据库的服务类。在测试套件中尽量减少数据库访问是一项最佳实践。另一个考虑因素是，我们不是测试数据库访问；我们只是测试某个特定类的功能。因此，有时有必要定义**模拟**类，这些类模仿父类的行为，但限制对外部资源的访问。

> **最佳实践**
> 将测试中的实际数据库访问限制在 Model（或等效）类中。否则，运行整套测试所需的时间可能会变得过多。

2. 在此情况下，为了说明目的，我们定义一个服务类 `VisitorService`，它使用了前面讨论的 `VisitorOps` 类：

   ```php
   <?php
   require_once __DIR__ . '/VisitorOps.php';
   require_once __DIR__ . '/../Application/Database/Connection.php';
   use Application\Database\Connection;

   class VisitorService
   {
       protected $visitorOps;

       public function __construct(array $config)
       {
           $this->visitorOps = new VisitorOps($config);
       }

       public function showAllVisitors()
       {
           $table = '<table>';
           foreach ($this->visitorOps->findAll() as $row) {
               $table .= '<tr><td>';
               $table .= implode('</td><td>', $row);
               $table .= '</td></tr>';
           }
           $table .= '</table>';
           return $table;
       }
   ```

3. 为了测试目的，我们为 `$visitorOps` 属性添加了一个 getter 和 setter。这允许我们使用模拟类来替代真实的 `VisitorOps` 类：

   ```php
   public function getVisitorOps()
   {
       return $this->visitorOps;
   }

   public function setVisitorOps(VisitorOps $visitorOps)
   {
       $this->visitorOps = $visitorOps;
   } // VisitorService 的右花括号
   ```

4. 接下来，我们定义一个模拟类 `VisitorOpsMock`，它模拟父类的功能。类常量和属性是继承的。然后我们添加模拟测试数据，以及一个 getter，以防我们稍后需要访问测试数据：

   ```php
   <?php
   require_once __DIR__ . '/VisitorOps.php';

   class VisitorOpsMock extends VisitorOps
   {
       protected $testData;

       public function __construct()
       {
           $data = array();
           for ($x = 1; $x <= 3; $x++) {
               $data[$x]['id'] = $x;
               $data[$x]['email'] = $x . 'test@unlikelysource.com';
               $data[$x]['visit_date'] = '2000-0' . $x . '-0' . $x . ' 00:00:00';
               $data[$x]['comments'] = 'TEST ' . $x;
               $data[$x]['name'] = 'TEST ' . $x;
           }
           $this->testData = $data;
       }

       public function getTestData()
       {
           return $this->testData;
       }
   ```

5. 接下来，我们重写 `findAll()` 以使用 `yield` 返回测试数据，正如父类所做的那样。请注意，我们仍然构建 SQL 字符串，因为这就是父类所做的：

   ```php
   public function findAll()
   {
       $sql = 'SELECT * FROM ' . self::TABLE_NAME;
       foreach ($this->testData as $row) {
           yield $row;
       }
   }
   ```

6. 为了模拟 `findByName()`，我们只需从 `$this->testData` 中返回该数组键。对于 `removeByName()`，我们从 `$this->testData` 中取消设置作为参数提供的数组键：

   ```php
   public function findByName($id)
   {
       $sql = 'SELECT * FROM ' . self::TABLE_NAME;
       $sql .= ' WHERE id = ?';
       return $this->testData[$id] ?? FALSE;
   }

   public function removeByName($id)
   {
       $sql = 'DELETE FROM ' . self::TABLE_NAME;
       $sql .= ' WHERE id = ?';
       if (empty($this->testData[$id])) {
           return 0;
       } else {
           unset($this->testData[$id]);
           return 1;
       }
   }
   ```

7. 添加数据稍微复杂一些，因为我们需要模拟 `id` 参数可能未提供的情况，因为数据库通常会自动为我们生成此参数。为了解决这个问题，我们检查 `id` 参数。如果未设置，我们找到最大的数组键并递增：

   ```php
   public function addVisitor($data)
   {
       $sql = 'INSERT INTO ' . self::TABLE_NAME;
       $sql .= ' (' . implode(',', array_keys($data)) . ')';
       $sql .= ' VALUES ';
       $sql .= ' (' . implode('::', array_keys($data)) . ')';
       if (!empty($data['id'])) {
           $id = $data['id'];
       } else {
           $keys = array_keys($this->testData);
           sort($keys);
           $id = end($keys) + 1;
           $data['id'] = $id;
       }

       $this->testData[$id] = $data;
       return 1;
   }
   } // VisitorOpsMock 类的结束花括号
   ```




## 使用匿名类作为模拟对象

- 模拟对象的一种巧妙变体是使用新的 PHP 7 匿名类，而不是创建一个定义模拟功能的正式类。使用匿名类的优势在于你可以扩展一个现有的类，这使得对象看起来更加合法。这种方法在你只需要重写一两个方法时特别有用。
- 为了演示这一点，我们将修改之前展示的 `VisitorServiceTest.php`，将其命名为 `VisitorServiceTestAnonClass.php`：

```php
<?php
use PHPUnit\Framework\TestCase;
require_once __DIR__ . '/VisitorService.php';
require_once __DIR__ . '/VisitorOps.php';
class VisitorServiceTestAnonClass extends TestCase
{
    protected $visitorService;
    protected $dbConfig = [
        'driver'   => 'mysql',
        'host'     => 'localhost',
        'dbname'   => 'php7cookbook_test',
        'user'     => 'cook',
        'password' => 'book',
        'errmode'  => PDO::ERRMODE_EXCEPTION,
    ];
    protected $testData;

public function setup()
{
    $data = array();
    for ($x = 1; $x <= 3; $x++) {
        $data[$x]['id'] = $x;
        $data[$x]['email'] = $x . 'test@unlikelysource.com';
        $data[$x]['visit_date'] =
            '2000-0' . $x . '-0' . $x . ' 00:00:00';
        $data[$x]['comments'] = 'TEST ' . $x;
        $data[$x]['name'] = 'TEST ' . $x;
    }
    
    $this->testData = $data;
    $this->visitorService =
        new VisitorService($this->dbConfig);
    
    $opsMock =
        new class ($this->testData) extends VisitorOps {
    protected $testData;
    public function __construct($testData)
    {
        $this->testData = $testData;
    }
    public function findAll()
    {
        return $this->testData;
    }
    };
    $this->visitorService->setVisitorOps($opsMock);
}
```

- 你会注意到，在 `setup()` 中，我们定义了一个扩展 `VisitorOps` 的匿名类。我们只需要重写 `findAll()` 方法。
- 请注意，在 `testShowAllVisitors()` 中，当执行 `$this->visitorService->showAllVisitors()` 时，访问者服务会调用该匿名类，进而调用重写的 `findAll()`：

```php
public function teardown()
{
    unset($this->visitorService);
}

public function testShowAllVisitors()
{
    $result = $this->visitorService->showAllVisitors();
    $this->assertRegExp('/!^<table>.+/<table>$/i', $result);
    foreach ($this->testData as $key => $value) {
        $dataWeWant = '!<td>' . $key . '</td>!';
        $this->assertRegExp($dataWeWant, $result);
    }
}
```

## 使用 Mock Builder

- 另一种技术是使用 `getMockBuilder()`。虽然这种方法对生成的模拟对象没有很多精细控制，但在你只需要确认返回某个特定类的对象，并且当运行指定方法时，该方法返回某个预期值的情况下，它极其有用。
- 在下面的例子中，我们复制了 `VisitorServiceTestAnonClass`；唯一的区别在于 `setup()` 中如何提供 `VisitorOps` 的实例，在这种情况下使用 `getMockBuilder()`。请注意，虽然在这个例子中没有使用 `with()`，但它用于向被模拟的方法提供受控参数：

```php
<?php
use PHPUnit\Framework\TestCase;
require_once __DIR__ . '/VisitorService.php';
require_once __DIR__ . '/VisitorOps.php';
class VisitorServiceTestAnonMockBuilder extends TestCase
{
    // 代码与 VisitorServiceTestAnon 相同
    public function setup()
    {
        $data = array();
        for ($x = 1; $x <= 3; $x++) {
            $data[$x]['id'] = $x;
            $data[$x]['email'] = $x . 'test@unlikelysource.com';
            $data[$x]['visit_date'] =
                '2000-0' . $x . '-0' . $x . ' 00:00:00';
            $data[$x]['comments'] = 'TEST ' . $x;
            $data[$x]['name'] = 'TEST ' . $x;
        }
        $this->testData = $data;
        $this->visitorService =
            new VisitorService($this->dbConfig);
        $opsMock = $this->getMockBuilder(VisitorOps::class)
            ->setMethods(['findAll'])
            ->disableOriginalConstructor()
            ->getMock();
        $opsMock->expects($this->once())
            ->method('findAll')
            ->with()
            ->will($this->returnValue($this->testData));
        $this->visitorService
            ->setVisitorOps($opsMock);
    }
    // 其余代码相同
}
```

我们展示了如何创建简单的一次性测试。然而，在大多数情况下，你将有许多需要测试的类，最好是一次性全部测试。通过开发测试套件，这是可能的，我们将在下一个配方中更详细地讨论。

## 工作原理...

首先，你需要安装 PHPUnit，如**1**至**5**步中所述。务必将 `vendor/bin` 包含在你的 PATH 中，以便你可以从命令行运行 PHPUnit。

## 运行简单测试

接下来，定义一个 `chap_13_unit_test_simple.php` 程序文件，其中包含一系列简单函数，例如 `add()`、`sub()` 等，如步骤 1 中所述。然后，你可以按照步骤 2 和 3 中提到的方式，定义一个包含在 `SimpleTest.php` 中的简单测试类。

假设 `phpunit` 在你的 PATH 中，从终端窗口切换到包含为此配方开发的代码的目录，并运行以下命令：

```
phpunit SimpleTest SimpleTest.php
```

你应该看到以下输出：

![](img/39390f6d56c5a83b28db083a8bd5185c_532_0.png)

在 `SimpleTest.php` 中进行更改，使测试失败（步骤 4）：

```php
public function testDiv()
{
    $this->assertEquals(2, div(4, 2));
    $this->assertEquals(99, div(4, 0));
}
```

这是修改后的输出：

![](img/39390f6d56c5a83b28db083a8bd5185c_532_1.png)

接下来，将 `table()` 函数添加到 `chap_13_unit_test_simple.php`（步骤 5），并将 `testTable()` 添加到 `SimpleTest.php`（步骤 6）。重新运行单元测试并观察结果。

要测试一个类，将 `chap_13_unit_test_simple.php` 中开发的函数复制到一个 `Demo` 类中（步骤 7）。在对 `SimpleTest.php` 进行步骤 8 中建议的修改后，重新运行简单测试并观察结果。

## 测试数据库模型类

首先，创建一个要测试的示例类，即本小节中步骤 2 所示的 `VisitorOps`。现在你可以定义一个我们称为 `SimpleDatabaseTest` 的类来测试 `VisitorOps`。首先，使用 `require_once` 加载要测试的类。（我们将在下一个配方中讨论如何整合自动加载！）然后定义主要属性，包括测试数据库配置和测试数据。你可以使用 `php7cookbook_test` 作为测试数据库：

```php
<?php
use PHPUnit\Framework\TestCase;
require_once __DIR__ . '/VisitorOps.php';
class SimpleDatabaseTest extends TestCase
{
    protected $visitorOps;
    protected $dbConfig = [
        'driver' => 'mysql',
        'host' => 'localhost',
        'dbname' => 'php7cookbook_test',
        'user' => 'cook',
        'password' => 'book',
        'errmode' => PDO::ERRMODE_EXCEPTION,
    ];
    protected $testData = [
        'id' => 1,
        'email' => 'test@unlikelysource.com',
        'visit_date' => '2000-01-01 00:00:00',
        'comments' => 'TEST',
        'name' => 'TEST'
    ];
}
```

接下来，定义 `setup()`，它插入测试数据并确认最后的 SQL 语句是 INSERT。你还应该检查返回值是否为正：

```php
public function setup()
{
    $this->visitorOps = new VisitorOps($this->dbConfig);
    $this->visitorOps->addVisitor($this->testData);
    $this->assertRegExp('/INSERT/', $this->visitorOps->getSql());
}
```

之后，定义 `teardown()`，它删除测试数据并确认 `id = 1` 的查询返回 FALSE：

```php
public function teardown()
{
    $result = $this->visitorOps->removeById(1);
    $result = $this->visitorOps->findById(1);
    $this->assertEquals(FALSE, $result);
    unset($this->visitorOps);
}
```

第一个测试是针对 `findAll()` 的。首先，确认结果的数据类型。你可以使用 `current()` 获取最顶层的元素。我们确认有五个元素，其中一个为 `name`，且值与测试数据中的值相同：

```php
public function testFindAll()
{
    $result = $this->visitorOps->findAll();
    $this->assertInstanceOf(Generator::class, $result);
    $top = $result->current();
    $this->assertCount(5, $top);
    $this->assertArrayHasKey('name', $top);
    $this->assertEquals($this->testData['name'], $top['name']);
}
```

下一个测试是针对 `findById()` 的。它几乎与 `testFindAll()` 相同：

```php
public function testFindById()
{
    $result = $this->visitorOps->findById(1);
    $this->assertCount(5, $result);
    $this->assertArrayHasKey('name', $result);
    $this->assertEquals($this->testData['name'], $result['name']);
}
```

你不需要麻烦去测试 `removeById()`，因为这已经在 `teardown()` 中完成了。同样，也不需要测试 `runSql()`，因为这在其他测试中已经完成。

## 使用模拟类

首先，定义一个 `VisitorService` 服务类，如本小节中步骤 2 和 3 所述。接下来，定义一个 `VisitorOpsMock` 模拟类，这在步骤 4 到 7 中进行了讨论。




## 更多相关内容

现在你已具备开发服务类测试类 `VisitorServiceTest` 的条件。请注意，你需要提供自己的数据库配置，因为使用测试数据库而非生产数据库是一种最佳实践：

```php
<?php
use PHPUnit\Framework\TestCase;
require_once __DIR__ . '/VisitorService.php';
require_once __DIR__ . '/VisitorOpsMock.php';

class VisitorServiceTest extends TestCase
{
    protected $visitorService;
    protected $dbConfig = [
        'driver'    => 'mysql',
        'host'      => 'localhost',
        'dbname'    => 'php7cookbook_test',
        'user'      => 'cook',
        'password'  => 'book',
        'errmode'   => PDO::ERRMODE_EXCEPTION,
    ];
}
```

在 *setup()* 方法中，创建服务的一个实例，并用 *VisitorOpsMock* 替换原始类：

```php
public function setup()
{
    $this->visitorService = new VisitorService($this->dbConfig);
    $this->visitorService->setVisitorOps(new VisitorOpsMock());
}
public function teardown()
{
    unset($this->visitorService);
}
```

在我们的测试中，从访客列表生成一个 HTML 表格，然后你可以查找某些元素，由于你可以控制测试数据，所以可以预先知道预期的结果：

```php
public function testShowAllVisitors()
{
    $result = $this->visitorService->showAllVisitors();
    $this->assertRegExp('!^<table>.*</table>$', $result);
    $testData = $this->visitorService->getVisitorOps()->getTestData();
}
```

```php
foreach ($testData as $key => $value) {
    $dataWeWant = '<td>' . $key . '</td>';
    $this->assertRegExp($dataWeWant, $result);
}
```

接着，你可能希望尝试最后两个小节中建议的变化形式，即 *使用匿名类作为模拟对象* 和 *使用模拟构建器*。

其他断言用于测试对数字、字符串、数组、对象、文件、JSON 和 XML 的操作，如下表所示：

| 类别 | 断言方法 |
| :--- | :--- |
| 通用 | assertEquals() , assertFalse() , assertEmpty() , assertNull() , assertSame() , assertThat() , assertTrue() |
| 数值 | assertGreaterThan() , assertGreaterThanOrEqual() , assertLessThan() , assertLessThanOrEqual() , assertNan() , assertInfinite() |
| 字符串 | assertStringEndsWith() , assertStringEqualsFile() , assertStringStartsWith() , assertRegExp() , assertStringMatchesFormat() , assertStringMatchesFormatFile() |
| 数组/迭代器 | assertArrayHasKey() , assertArraySubset() , assertContains() , assertContainsOnly() , assertContainsOnlyInstancesOf() , assertCount() |
| 文件 | assertFileEquals() , assertFileExists() |
| 对象 | assertClassHasAttribute() , assertClassHasStaticAttribute() , assertInstanceOf() , assertInternalType() , assertObjectHasAttribute() |
| JSON | assertJsonFileEqualsJsonFile() , assertJsonStringEqualsJsonFile() , assertJsonStringEqualsJsonString() |
| XML | assertEqualXMLStructure() , assertXmlFileEqualsXmlFile() , assertXmlStringEqualsXmlFile() , assertXmlStringEqualsXmlString() |

### 参见...

- 关于单元测试的优秀讨论，请查看此处：https://en.wikipedia.org/wiki/Unit_testing。
- 有关 composer.json 文件指令的更多信息，请参见 https://getcomposer.org/doc/04-schema.md。
- 关于断言的完整列表，请查看此 PHPUnit 文档页面：https://phpunit.de/manual/current/en/phpunit-book.html#appendixes.assertions。
- PHPUnit 文档还详细说明了如何使用 getMockBuilder()，请参见此处：https://phpunit.de/manual/current/en/phpunit-book.html#test-doubles.mock-objects

## 编写测试套件

在阅读完前面的食谱后，你也许会注意到，手动运行 phpunit 并指定测试类和 PHP 文件名很快就会变得繁琐。当处理包含几十个甚至几百个类和文件的应用程序时，这一点尤其明显。PHPUnit 项目内置了通过单条命令运行多个测试的能力。这样的测试集合被称为**测试套件**。

### 操作指南...

1. 最简单的做法是将所有测试移动到一个文件夹中：
   ```bash
   mkdir tests
   cp *Test.php tests
   ```

2. 你需要调整包含或引入外部文件的命令，以适配新的位置。示例（SimpleTest）是在前面的食谱中开发的：
   ```php
   <?php
   use PHPUnit\Framework\TestCase;
   require_once __DIR__ . '/../chap_13_unit_test_simple.php';

   class SimpleTest extends TestCase
   {
    // 等等。
   ```

3. 然后你只需将目录路径作为参数运行 phpunit。PHPUnit 将自动运行该文件夹中的所有测试。在此示例中，我们假设存在一个 tests 子目录：
   ```bash
   phpunit tests
   ```

4. 你可以使用 `--bootstrap` 选项来指定在运行测试之前执行的文件。该选项的一个典型用途是初始化自动加载：
   ```bash
   phpunit --bootstrap tests_with_autoload/bootstrap.php tests
   ```

5. 以下是实现自动加载的示例 bootstrap.php 文件：
   ```php
   <?php
   require __DIR__ . '/../../Application/Autoload/Loader.php';
   Application\Autoload\Loader::init([__DIR__]);
   ```

6. 另一种可能性是使用 XML 配置文件定义一组或多组测试。以下是一个仅运行 Simple* 测试的示例：
   ```xml
   <phpunit>
       <testsuites>
           <testsuite name="simple">
               <file>SimpleTest.php</file>
               <file>SimpleDbTest.php</file>
               <file>SimpleClassTest.php</file>
           </testsuite>
       </testsuites>
   </phpunit>
   ```

7. 这是另一个示例，它基于目录运行测试，并指定了一个引导文件：
   ```xml
   <phpunit bootstrap="bootstrap.php">
       <testsuites>
           <testsuite name="visitor">
               <directory>Simple</directory>
           </testsuite>
       </testsuites>
   </phpunit>
   ```

## 工作原理...

确保前面的食谱 *编写简单测试* 中讨论的所有测试都已定义。然后你可以创建一个 `tests` 文件夹，并将所有 `*Test.php` 文件移动或复制到该文件夹中。接着，你需要调整 `require_once` 语句中的路径，如第 2 步所示。

为了演示 PHPUnit 如何运行文件夹中的所有测试，请从包含本章源代码的目录运行以下命令：

```bash
phpunit tests
```

你应该看到以下输出：

```
ed@ed: ~/Desktop/Repos/php7_recipes/source/chapter13$
edged: ~/Desktop/Repos/php7_recipes/source/chapter13$ phpunit tests
PHPUnit 5.4.3 by Sebastian Bergmann and contributors.

............................ 12 / 12 (100%)

Time: 53 ms, Memory: 4.00MB

OK (12 tests, 32 assertions)
ed@ed: ~/Desktop/Repos/php7_recipes/source/chapter13$
```

为了演示通过引导文件使用自动加载，创建一个名为 `tests_with_autoload` 的新目录。在此文件夹中，定义一个包含第 5 步所示代码的 `bootstrap.php` 文件。在 `tests_with_autoload` 中创建两个目录：`Demo` 和 `Simple`。

从包含本章源代码的目录中，将文件（在前面食谱的第 12 步中讨论过）复制到 `tests_with_autoload/Demo/Demo.php`。在起始的 `<?php` 标签后，添加这一行：

```php
namespace Demo;
```

接下来，将 `SimpleTest.php` 文件复制到 `tests_with_autoload/Simple/ClassTest.php`。（注意文件名发生了变化！）。你需要将前几行更改为以下内容：

```php
<?php
namespace Simple;
use Demo\Demo;
use PHPUnit\Framework\TestCase;

class ClassTest extends TestCase
{
    protected $demo;
    public function setUp()
    {
        $this->demo = new Demo();
    }
    // 等等。
```

之后，创建一个 `tests_with_autoload/phpunit.xml` 文件来整合所有内容：

```xml
<phpunit bootstrap="bootstrap.php">
    <testsuites>
        <testsuite name="visitor">
            <directory>Simple</directory>
        </testsuite>
    </testsuites>
</phpunit>
```


最后，切换到包含本章代码的目录。现在你可以运行一个包含引导文件的单元测试，该测试还涉及自动加载和命名空间，步骤如下：

```php
phpunit -c tests_with_autoload/phpunit.xml
```

输出结果应如下所示：

![](img/39390f6d56c5a83b28db083a8bd5185c_540_0.png)

## 另请参阅...

- 关于编写 PHPUnit 测试套件的更多信息，请参阅此[文档页面](https://phpunit.de/manual/current/en/phpunit-book.html#organizing-tests.xml-configuration)。

## 生成虚假测试数据

测试和调试过程的一部分涉及引入逼真的测试数据。在某些情况下，特别是当测试数据库访问并生成基准测试时，需要大量的测试数据。实现这一点的一种方法是引入一个从网站抓取数据的过程，然后将这些数据组合成逼真但随机的组合，以便插入到数据库中。

### 如何操作...

1.  第一步是确定测试应用程序所需的数据。另一个需要考虑的问题是，该网站是否面向国际受众，还是市场主要来自单一国家？
2.  为了生成一致的虚假数据工具，将数据从其源转移到可用的数字格式至关重要。首选方案是一系列数据库表。另一种吸引力稍差的替代方案是 CSV 文件。
3.  你可能需要分阶段转换数据。例如，你可以从列出国家代码和国家名称的网页中提取数据到文本文件中。

| 代码 | 名称 | 代码 | 名称 | 代码 | 名称 |
| :--- | :--- | :--- | :--- | :--- | :--- |
| AJ | 阿富汗 | AM | 阿尔及利亚 | AN | 阿塞拜疆 |
| AL | 阿尔巴尼亚 | AM | 亚美尼亚 | AN | 安道尔 |
| AO | 安哥拉 | AR | 阿根廷 | AS | 澳大利亚 |
| AT | 阿什莫尔和卡特利特群岛 | AU | 奥地利 | AV | 安圭拉 |
| AX | 阿克罗蒂里 | AY | 南极洲 | BA | 巴林 |
| BB | 巴巴多斯 | BC | 博茨瓦纳 | BD | 百慕大 |
| BE | 比利时 | BF | 巴哈马 | BG | 孟加拉国 |
| BH | 伯利兹 | BK | 波斯尼亚和黑塞哥维那 | BL | 玻利维亚 |
| BM | 缅甸 | BN | 贝宁 | BO | 白俄罗斯 |
| BP | 所罗门群岛 | BR | 巴西 | BS | 英属印度 |
| BT | 不丹 | BU | 保加利亚 | BV | 布韦岛 |
| BX | 文莱 | BY | 布隆迪 | CA | 加拿大 |
| CB | 柬埔寨 | CD | 乍得 | CE | 斯里兰卡 |
| CF | 刚果 | CG | 刚果（民主共和国/扎伊尔） | CH | 中国 |
| CI | 智利 | CI | 开曼群岛 | CK | 库克群岛（基林群岛） |
| CM | 喀麦隆 | CN | 科摩罗 | CO | 哥伦比亚 |
| CR | 珊瑚海群岛 | CS | 哥斯达黎加 | CT | 中非共和国 |
| CU | 古巴 | CV | 佛得角 | CW | 库克群岛 |

4.  由于这个列表很短，可以将其直接剪切并粘贴到文本文件中。
5.  然后我们可以搜索 " " 并替换为 "\n"，这将给我们以下内容：

   1. AA 阿鲁巴
   2. AC 安提瓜和巴布达
   3. AE 阿拉伯联合酋长国
   4. AF 阿富汗
   5. AG 阿尔及利亚
   6. AJ 阿塞拜疆
   7. AL 阿尔巴尼亚
   8. AM 亚美尼亚
   9. AN 安道尔
   10. AO 安哥拉
   11. AR 阿根廷
   12. AS 澳大利亚
   13. AT 阿什莫尔和卡特利特群岛
   14. AU 奥地利
   15. AV 安圭拉
   16. AX 阿克罗蒂里
   17. AY 南极洲

6.  然后可以将其导入电子表格，进而让你导出为 CSV 文件。从那里，将其导入数据库只是件简单的事。例如，phpMyAdmin 就具备这样的功能。
7.  为了说明起见，我们假设我们生成的数据最终将存入 prospects 表中。以下是用于创建此表的 SQL 语句：

```sql
CREATE TABLE `prospects` (
  `id` int (11) NOT NULL AUTO_INCREMENT,
  `first_name` varchar (128) NOT NULL,
  `last_name` varchar (128) NOT NULL,
  `address` varchar (256) DEFAULT NULL,
  `city` varchar(64) DEFAULT NULL,
  `state_province` varchar(32) DEFAULT NULL,
  `postal_code` char(16) NOT NULL,
  `phone` varchar(16) NOT NULL,
  `country` char(2) NOT NULL,
  `email` varchar(250) NOT NULL,
  `status` char(8) DEFAULT NULL,
  `budget` decimal(10,2) DEFAULT NULL,
  `last_updated` datetime DEFAULT NULL,
  PRIMARY KEY (`id`),
  UNIQUE KEY `UNIQ_35730C0E67927C74` (`email`)
) ENGINE=InnoDB DEFAULT CHARSET=utf8;
```

8.  现在是创建能够生成虚假数据的类的时候了。然后，我们将创建方法为上面显示的每个字段生成数据，除了 id，它是自动生成的：

```php
namespace Application\Test;

use PDO;
use Exception;
use DateTime;
use DateInterval;
use PDOException;
use SplFileObject;
use InvalidArgumentsException;
use Application\Database\Connection;

class FakeData
{
    // 数据生成方法在此处
}
```

9.  接下来，我们定义将在过程中使用的常量和属性：

```php
const MAX_LOOKUPS   = 10;
const SOURCE_FILE   = 'file';
const SOURCE_TABLE  = 'table';
const SOURCE_METHOD = 'method';
const SOURCE_CALLBACK = 'callback';
const FILE_TYPE_CSV = 'csv';
const FILE_TYPE_TXT = 'txt';
const ERROR_DB      = 'ERROR: unable to read source table';
const ERROR_FILE    = 'ERROR: file not found';
const ERROR_COUNT   = 'ERROR: unable to ascertain count or ID column missing';

const ERROR_UPLOAD = 'ERROR: unable to upload file';
const ERROR_LOOKUP = 'ERROR: unable to find any IDs in the source table';

protected $connection;
protected $mapping;
protected $files;
protected $tables;
```

10. 然后我们定义用于生成随机字母、街道名称和电子邮件地址的属性。你可以将这些数组视为种子，可以根据需要对其进行修改和/或扩展。例如，你可能为法国受众替换巴黎的街道名称片段：

```php
protected $alpha = 'ABCDEFGHIJKLMNOPQRSTUVWXYZ';
protected $street1 = ['Amber','Blue','Bright','Broad','Burning','Cinder','Clear','Dewy','Dusty','Easy']; // 等等。
protected $street2 = ['Anchor','Apple','Autumn','Barn','Beacon','Bear','Berry','Blossom','Bluff','Cider','Cloud']; // 等等。
protected $street3 = ['Acres','Arbor','Avenue','Bank','Bend','Canyon','Circle','Street'];
protected $mail1 = ['northern','southern','eastern','western','fast','midland','central'];
protected $mail2 = ['telecom','telco','net','connect'];
protected $mail3 = ['com','net'];
```

11. 在构造函数中，我们接受一个用于数据库访问的 Connection 对象，以及一个映射到虚假数据的数组：

```php
public function __construct(Connection $conn, array $mapping)
{
    $this->connection = $conn;
    $this->mapping = $mapping;
}
```

12. 为了生成街道名称，与其尝试创建数据库表，使用一组种子数组来生成随机组合可能更高效。以下是这样做的示例：

```php
public function getAddress($entry)
{
    return random_int(1,999)
        . ' ' . $this->street1[array_rand($this->street1)]
        . ' ' . $this->street2[array_rand($this->street2)]
        . ' ' . $this->street3[array_rand($this->street3)];
}
```

13. 根据所需的真实程度，你还可以构建一个将邮政编码与城市匹配的数据库表。邮政编码也可以随机生成。以下是为英国生成邮政编码的示例：

```php
public function getPostalCode($entry, $pattern = 1)
{
    return $this->alpha[random_int(0,25)]
        .$this->alpha[random_int(0,25)]
        .random_int(1, 99)
        . ' '
        .random_int(1, 9)
        .$this->alpha[random_int(0,25)]
        .$this->alpha[random_int(0,25)];
}
```

14. 虚假电子邮件的生成也可以使用一组种子数组来产生随机结果。我们甚至可以编程使其接收现有的 $entry 数组，带有参数，并使用这些参数创建地址的名称部分：

```php
public function getEmail($entry, $params = NULL)
{
    $first = $entry[$params[0]] ?? $this->alpha[random_int(0,25)];
    $last = $entry[$params[1]] ?? $this->alpha[random_int(0,25)];
    return $first[0] . '.' . $last
        .'@'
        .$this->mail1[array_rand($this->mail1)]
        .$this->mail2[array_rand($this->mail2)]
        . '.'
        . $this->mail3[array_rand($this->mail3)];
}
```

15. 对于日期生成，一种方法是接受现有的 $entry 数组作为参数，带有参数。参数将是一个数组，其中第一个值是起始日期。第二个参数是从起始日期中减去的最大天数。这实际上允许你从一个范围内返回一个随机日期。注意，我们使用 `DateTime::sub()` 减去随机天数。`sub()` 需要一个 `DateInterval` 实例，我们使用 `P`、随机天数，然后使用 `'D':` 来构建它：

```php
public function getDate($entry, $params)
{
    list($fromDate, $maxDays) = $params;
    $date = new DateTime($fromDate);
    $date->sub(new DateInterval('P' . random_int(0, $maxDays) . 'D'));
    return $date->format('Y-m-d H:i:s');
}
```




16. 正如在本食谱开头所述，我们用于假数据生成的数据源会有所不同。在某些情况下，如前几步所示，我们使用种子数组来构建假数据。在其他情况下，我们可能希望使用文本文件或 CSV 文件作为数据源。以下是此类方法的示例：

```php
public function getEntryFromFile($name, $type)
{
	if (empty($this->files[$name])) {
		$this->pullFileData($name, $type);
	}
	return $this->files[$name][
		random_int(0, count($this->files[$name]) - 1)
	];
}
```

17. 你会注意到，我们首先需要将文件数据拉入一个数组，该数组构成了返回值。以下是执行此操作的方法。如果指定的文件未找到，我们会抛出一个异常。文件类型被识别为我们类常量之一：`FILE_TYPE_TEXT` 或 `FILE_TYPE_CSV`。根据类型，我们使用 `fgetcsv()` 或 `fgets()`：

```php
public function pullFileData($name, $type)
{
	if (!file_exists($name)) {
		throw new Exception(self::ERROR_FILE);
	}
	$fileObj = new SplFileObject($name, 'r');
	if ($type === self::FILE_TYPE_CSV) {
		while (($data = $fileObj->fgetcsv()) !== false) {
			$this->files[$name][] = trim($data[0]);
		}
	} else {
		while (($data = $fileObj->fgets()) !== false) {
			$this->files[$name][] = trim($data);
		}
	}
}
```

18. 该过程中可能最复杂的方面是从数据库表中提取随机数据。我们接受的参数包括表名、构成主键的列名，以及一个映射数据库查找表中列名与目标列名之间关系的数组：

```php
public function getEntryFromTable($tableName, $idColumn, $mapping)
{
	$entry = array();
	try {
		if (empty($this->tables[$tableName])) {
			$sql = 'SELECT ' . $idColumn . ' FROM ' . $tableName . ' ORDER BY ' . $idColumn . ' ASC LIMIT 1';
			$stmt = $this->connection->pdo->query($sql);
			$this->tables[$tableName]['first'] = $stmt->fetchColumn();
			
			$sql = 'SELECT ' . $idColumn . ' FROM ' . $tableName . ' ORDER BY ' . $idColumn . ' DESC LIMIT 1';
			$stmt = $this->connection->pdo->query($sql);
			$this->tables[$tableName]['last'] = $stmt->fetchColumn();
		}

		// Step 19 content continues here
		$result = FALSE;
		$count = self::MAX_LOOKUPS;
		$sql = 'SELECT * FROM ' . $tableName . ' WHERE ' . $idColumn . ' = ?';
		$stmt = $this->connection->pdo->prepare($sql);

		// Step 20 content continues here
		do {
			$id = random_int($this->tables[$tableName]['first'], $this->tables[$tableName]['last']);
			$stmt->execute([$id]);
			$result = $stmt->fetch(PDO::FETCH_ASSOC);
		} while ($count-- && !$result);
		
		if (!$result) {
			error_log(__METHOD__ . ':' . self::ERROR_LOOKUP);
			throw new Exception(self::ERROR_LOOKUP);
		}
	} catch (PDOException $e) {
		error_log(__METHOD__ . ':' . $e->getMessage());
		throw new Exception(self::ERROR_DB);
	}

	// Step 21 content continues here
	foreach ($mapping as $key => $value) {
		$entry[$value] = $result[$key] ?? NULL;
	}
	return $entry;
}
```

19. 现在，我们已具备设置预编译语句并初始化若干关键变量的条件：

```php
$result = FALSE;
$count = self::MAX_LOOKUPS;
$sql = 'SELECT * FROM ' . $tableName . ' WHERE ' . $idColumn . ' = ?';
$stmt = $this->connection->pdo->prepare($sql);
```

20. 实际的查找过程放置在 do...while 循环中。这样做的原因是我们需要至少执行一次查询才能获得结果。只有在我们未得到结果时，才继续循环。我们在最低 ID 和最高 ID 之间生成一个随机数，然后在查询参数中使用该数字。请注意，我们还递减一个计数器以防止无限循环。这是因为如果 ID 不是连续的，我们可能会意外生成一个不存在的 ID。如果我们超过最大尝试次数且仍然没有结果，则抛出异常：

```php
do {
	$id = random_int($this->tables[$tableName]['first'], $this->tables[$tableName]['last']);
	$stmt->execute([$id]);
	$result = $stmt->fetch(PDO::FETCH_ASSOC);
} while ($count-- && !$result);
if (!$result) {
	error_log(__METHOD__ . ':' . self::ERROR_LOOKUP);
	throw new Exception(self::ERROR_LOOKUP);
}
```

注意：包裹此逻辑的 try-catch 块在第 21 步末尾闭合。

21. 然后，我们使用映射数组从源表中检索值，使用在目标表中期望的键：

```php
} catch (PDOException $e) {
	error_log(__METHOD__ . ':' . $e->getMessage());
	throw new Exception(self::ERROR_DB);
}
foreach ($mapping as $key => $value) {
	$entry[$value] = $result[$key] ?? NULL;
}
return $entry;
}
```

22. 这个类的核心是 `getRandomEntry()` 方法，它生成单个假数据数组。我们逐个遍历 `$mapping` 中的条目，并检查各种参数：

```php
public function getRandomEntry()
{
	$entry = array();
	foreach ($this->mapping as $key => $value) {
		if (isset($value['source'])) {
			switch ($value['source']) {
```

23. 源参数用于实现实际上充当策略模式的功能。我们支持四种不同的源可能性，全部定义为类常量。第一个是 `SOURCE_FILE`。在这种情况下，我们使用前面讨论的 `getEntryFromFile()` 方法：

```php
case self::SOURCE_FILE : 
	$entry[$key] = $this->getEntryFromFile(
		$value['name'], $value['type']);
	break;
```

24. 回调选项根据在 `$mapping` 数组中提供的回调返回一个值：

```php
case self::SOURCE_CALLBACK : 
	$entry[$key] = $value['name']();
	break;
```

25. `SOURCE_TABLE` 选项使用 `$mapping` 中定义的数据库表作为查找。请注意，前面讨论的 `getEntryFromTable()` 能够返回一个值数组，这意味着我们需要使用 `array_merge()` 来合并结果：

```php
case self::SOURCE_TABLE : 
	$result = $this->getEntryFromTable(
		$value['name'], $value['idCol'], $value['mapping']);
	$entry = array_merge($entry, $result);
	break;
```

26. `SOURCE_METHOD` 选项（也是默认选项）使用该类中已包含的方法。我们检查是否包含参数，如果是，则将这些参数添加到方法调用中。请注意使用 `{}` 来影响插值。如果我们进行 PHP 7 的 `$this->$value['name']()` 调用，由于抽象语法树（AST）重写，它会插值为此形式：`${$this->$value}['name']()`，这不是我们想要的：

```php
case self::SOURCE_METHOD : 
default :
	if (!empty($value['params'])) {
		$entry[$key] = $this->{$value['name']}(
			$entry, $value['params']);
	} else {
		$entry[$key] = $this->{$value['name']}($entry);
	}
}
return $entry;
}
```

27. 我们定义一个方法，循环执行 `getRandomEntry()` 以生成多行假数据。我们还添加了一个插入到目标表的选项。如果启用了此选项，我们将设置一个用于插入的预编译语句，并检查是否需要截断当前在此表中的任何数据：

```php
public function generateData(
	$howMany, $destTableName = NULL, $truncateDestTable = FALSE)
{
	try {
		if ($destTableName) {
			$sql = 'INSERT INTO ' . $destTableName
				. ' (' . implode(',', array_keys($this->mapping))
				. ') ' . ' VALUES ' . '(:'
				. implode(' ,:', array_keys($this->mapping)) . ')';
			$stmt = $this->connection->pdo->prepare($sql);
			$insert = TRUE;
		}
		if ($truncateDestTable) {
			$sql = 'DELETE FROM ' . $destTableName;
			$this->connection->pdo->query($sql);
		}
	} catch (PDOException $e) {
		error_log(__METHOD__ . ': ' . $e->getMessage());
		throw new Exception(self::ERROR_COUNT);
	}
```

28. 接下来，我们循环处理请求的数据行数，并执行 `getRandomEntry()`。如果请求了数据库插入，我们在 `try/catch` 块中执行预编译语句。无论如何，我们都使用 `yield` 关键字将此方法转换为生成器：

```php
	for ($x = 0; $x < $howMany; $x++) {
		$entry = $this->getRandomEntry();
		if ($insert) {
			try {
				$stmt->execute($entry);
			} catch (PDOException $e) {
				error_log(__METHOD__ . ':' . $e->getMessage());
				throw new Exception(self::ERROR_DB);
			}
		}
		yield $entry;
	}
}
```

## 最佳实践
如果返回的数据量巨大，最好是在数据生成时逐步输出（yield）数据，从而节省数组所需的内存。

## 工作原理…

首先要做的是确保你为随机数据生成准备好数据。在本食谱中，我们将假设目标表为 `prospects`，其在第 7 步中展示了相应的 SQL 数据库定义。

作为姓名的数据源，你可以为名字和姓氏创建文本文件。在本示例中，我们将引用 `data/files` 目录，以及 `first_names.txt` 和 `surnames.txt` 文件。对于城市、州或省、邮政编码和国家，从 `http://www.geonames.org/` 等来源下载数据并上传到 `world_city_data` 表可能会很有用。对于剩余字段，如地址、电子邮件、状态等，你可以使用内置于 `FakeData` 的方法，或者定义回调。

接下来，务必定义 `Application\Test\FakeData`，添加第 8 步到第 29 步讨论的内容。完成后，创建一个名为 `chap_13_fake_data.php` 的调用程序，该程序设置自动加载并使用相应的类。你还应定义与数据库配置路径以及名称文件路径相匹配的常量：

```php
<?php
define('DB_CONFIG_FILE', __DIR__ . '../../../config/db.config.php');
define('FIRST_NAME_FILE', __DIR__ . '../../../data/files/first_names.txt');
define('LAST_NAME_FILE', __DIR__ . '../../../data/files/surnames.txt');
```



require _DIR_ . '/../Application/Autoload/Loader.php';
Application\Autoload\Loader::init (_DIR_ . '/../');
use Application\Test\FakeData;
use Application\Database\Connection;

接下来，定义一个映射数组，该数组使用目标表（prospects）中的列名作为键。然后你需要为 source、name 以及其他必需参数定义子键。首先，`first_name` 和 `last_name` 都将使用文件作为数据源，`name` 指向文件名，`type` 指示文本类型的文件类型：

```php
$mapping = [
    'first_name' => ['source' => FakeData::SOURCE_FILE,
                     'name' => FIRST_NAME_FILE,
                     'type' => FakeData::FILE_TYPE_TXT],
    'last_name' => ['source' => FakeData::SOURCE_FILE,
                    'name' => LAST_NAME_FILE,
                    'type' => FakeData::FILE_TYPE_TXT],
```

`address`、`email` 和 `last_updated` 均使用内置方法作为数据源。后两者还定义了需要传递的参数：

```php
'address' => ['source' => FakeData::SOURCE_METHOD,
                'name' => 'getAddress'],
'email' => ['source' => FakeData::SOURCE_METHOD,
            'name' => 'getEmail',
            'params' => ['first_name', 'last_name']],
'last_updated' => ['source' => FakeData::SOURCE_METHOD,
                   'name' => 'getDate',
                   'params' => [date('Y-m-d'), 365*5]]
```

`phone`、`status` 和 `budget` 都可以使用回调函数来提供假数据：

```php
'phone' => ['source' => FakeData::SOURCE_CALLBACK,
             'name' => function () {
                 return sprintf('%3d-%3d-%4d', random_int(101,999),
                                random_int(101,999), random_int(0,9999)); }],
'status' => ['source' => FakeData::SOURCE_CALLBACK,
             'name' => function () { $status = ['BEG', 'INT', 'ADV'];
             return $status[rand(0,2)]; }],
'budget' => ['source' => FakeData::SOURCE_CALLBACK,
             'name' => function() { return random_int(0, 9999)
            + (random_int(0, 99) * .01); }]
```

最后，`city` 从查找表中获取数据，该表还提供了列在 `mapping` 参数中的字段的数据。然后你可以保持这些键未定义。请注意，你还应该指定表示该表主键的列：

```php
'city' => ['source' => FakeData::SOURCE_TABLE,
           'name' => 'world_city_data',
           'idcol' => 'id',
           'mapping' => [
             'city' => 'city',
             'state_province' => 'state_province',
             'postal_code_prefix' => 'postal_code',
             'iso2' => 'country'
           ],
           'state_province' => [],
           'postal_code' => [],
           'country' => [],
         ]
```

然后你可以定义目标表、Connection 实例，并创建 FakeData 实例。一个 foreach() 循环就足以显示指定数量的条目：

```php
$destTableName = 'prospects';
$conn = new Connection(include DB_CONFIG_FILE);
$fake = new FakeData($conn, $mapping);
foreach ($fake->generateData(10) as $row) {
    echo implode('|', $row) . PHP_EOL;
}
```

输出结果（10 行）大致如下：

![](img/39390f6d56c5a83b28db083a8bd5185c_551_0.png)

## 更多内容...

以下是包含各种数据列表的网站汇总，这些网站在生成测试数据时可能很有用：

| 数据类型 | URL | 备注 |
|---|---|---|
| 名字 | http://nameberry.com/ |  |
|  | http://www.babynamewizard.com/international-names-lists-popular-names-from-around-the-world |  |
| 原始名字列表 | http://deron.meranda.us/data/census-dist-female-first.txt | 美国女性名字 |
|  | http://deron.meranda.us/data/census-dist-male-first.txt | 美国男性名字 |
|  | http://www.avss.ucsb.edu/NameFema.HTM | 美国女性名字 |
|  | http://www.avss.ucsb.edu/namemal.htm | 美国男性名字 |
| 姓氏 | http://names.mongabay.com/data/1000.html | 来自人口普查的美国姓氏 |
|  | http://surname.sofeminine.co.uk/w/surnames/most-common-surnames-in-great-britain.html | 英国姓氏 |
|  | https://gist.github.com/subodhghulaxe/8148971 | 以 PHP 数组形式列出的美国姓氏列表 |
|  | http://www.dutchgenealogy.nl/tng/surnames-all.php | 荷兰姓氏 |
|  | http://www.worldvitalrecords.com/browsesurnames.aspx?l=A | 国际姓氏；只需更改最后一个字母以获取以该字母开头的名字列表 |
| 城市 | http://www.travelgis.com/default.asp?framesrc=/cities/ | 世界城市 |
|  | https://www.maxmind.com/en/free-world-cities-database |  |
|  | https://github.com/David-Haim/CountriesToCitiesJSON |  |
|  | http://www.fallingrain.com/world/index.html |  |
| 邮政编码 | https://bouteil.com/zipcodes/ | 仅限美国；包含城市、邮政编码、纬度和经度 |
|  | http://www.geonames.org/export/ | 国际；城市名称、邮政编码，所有内容！；免费下载 |

## 使用 session_start 参数自定义会话

在 PHP 7 之前，为了覆盖 php.ini 中关于安全会话管理的设置，你需要使用一系列 ini_set() 命令。这种方法的令人烦恼之处在于，你还需要知道哪些设置是可用的，并且在其他应用程序中复用相同的设置也很困难。然而，从 PHP 7 开始，你可以向 session_start() 命令提供一个参数数组，从而立即设置这些值。

### 实现方法...

- 1. 我们首先开发一个 Application\Security\SessOptions 类，该类将持有会话参数，并具备启动会话的能力。我们还定义了一个类常量，以防传入无效的会话选项：

```php
namespace Application\Security;   
use ReflectionClass;   
use InvalidArgumentException;   
class SessOptions   
{   
    const ERROR_PARAMS = 'ERROR: invalid session options';
```

- 2. 接下来，我们扫描 `php.ini` 会话指令列表（文档位于 `http://php.net/manual/en/session.configuration.php`）。我们特别寻找那些在 `Changeable` 列中标记为 `PHP_INI_ALL` 的指令。此类指令可以在运行时被覆盖，因此可以作为 `session_start()` 的参数：

![](img/39390f6d56c5a83b28db083a8bd5185c_554_0.png)

- 3. 然后我们将这些定义为类常量，这将使该类在开发过程中更具可用性。大多数优秀的代码编辑器都能扫描该类并给出常量列表，从而方便管理会话设置。请注意，为了节省书中的空间，并非所有设置都显示出来：

```php
const SESS_OP_NAME            = 'name';
const SESS_OP_LAZY_WRITE      = 'lazy_write'; // AVAILABLE
// SINCE PHP 7.0.0.
const SESS_OP_SAVE_PATH       = 'save_path';
const SESS_OP_SAVE_HANDLER    = 'save_handler';
// etc.
```

- 4. 然后我们可以定义构造函数，它接受一个 `php.ini` 会话设置数组作为参数。我们使用 `ReflectionClass` 获取类常量列表，并对 `$options` 参数进行循环处理，以确认该设置是被允许的。还要注意 `array_flip()` 的使用，它翻转键和值，使得类常量的实际值形成数组键，而类常量的名称成为值：

```php
protected $options;
protected $allowed;
public function __construct(array $options)
{
    $reflect = new ReflectionClass(get_class($this));
    $this->allowed = $reflect->getConstants();
    $this->allowed = array_flip($this->allowed);
    unset($this->allowed[self::ERROR_PARAMS]);
    foreach ($options as $key => $value) {
        if(!isset($this->allowed[$key])) {
            error_log(__METHOD__ . ':' . self::ERROR_PARAMS);
            throw new InvalidArgumentException(
                self::ERROR_PARAMS);
        }
    }
    $this->options = $options;
}
```

- 5. 然后我们以另外两个方法结束；一个方法允许我们从外部访问允许的参数，另一个方法则启动会话：

```php
public function getAllowed()
{
    return $this->allowed;
}

public function start()
{
    session_start($this->options);
}
```




## 工作原理...

将本菜谱中讨论的所有代码放入 `Application\Security` 目录下的 `SessOptions.php` 文件中。然后，你可以定义一个名为 `chap_13_session_options.php` 的调用程序来测试这个新类，该程序设置了自动加载并使用该类：

```php
<?php
require __DIR__ . '/../Application/Autoload/Loader.php';
Application\Autoload\Loader::init(__DIR__ . '/../..');
use Application\Security\SessOptions;
```

接下来，定义一个数组，使用类的常量作为键，并根据需要设置值以管理会话。请注意，在本文中所示的示例中，会话信息存储在一个名为 session 的子目录中，你需要创建该目录：

```php
$options = [
    SessOptions::SESS_OP_USE_ONLY_COOKIES => 1,
    SessOptions::SESS_OP_COOKIE_LIFETIME => 300,
    SessOptions::SESS_OP_COOKIE_HTTPONLY => 1,
    SessOptions::SESS_OP_NAME => 'UNLIKELYSOURCE',
    SessOptions::SESS_OP_SAVE_PATH => __DIR__ . '/session'
];
```

现在，你可以创建 `SessOptions` 实例并运行 `start()` 方法来启动会话。你可以在这里使用 `phpinfo()` 来显示有关会话的一些信息：

```php
$sessOpt = new SessOptions($options);
$sessOpt->start();
$_SESSION['test'] = 'TEST';
phpinfo(INFO_VARIABLES);
```

如果你使用浏览器开发人员工具查找有关 Cookie 的信息，你会注意到名称设置为 `UNLIKELYSOURCE`，并且过期时间是从现在开始 5 分钟：

![](img/39390f6d56c5a83b28db083a8bd5185c_556_0.png)

如果你扫描会话目录，你会发现会话信息已存储在那里：

```bash
ed@ed: ~/Desktop/Repos/php7_recipes/source/chapter13
edged:~/Desktop/Repos/php7_recipes/source/chapter13$ ls -l session
total 4
-rw-r--r-- 1 ed ed 16 Jun 17 11:03 sess_789876c4d795aa8a8882ffdf09cda9576
edged:~/Desktop/Repos/php7_recipes/source/chapter13$
```

## 另请参阅...

- 有关与会话相关的 php.ini 指令的更多信息，请参见此摘要：http://php.net/manual/en/session.configuration.php

## 定义 PSR-7 类

在本附录中，我们将涵盖以下主题：

- 实现 PSR-7 值对象类
- 开发 PSR-7 Request 类
- 定义 PSR-7 Response 类

## 简介

**PHP 标准推荐编号 7（PSR-7）** 定义了许多接口，但没有提供实际的实现。因此，我们需要定义具体的代码实现，才能开始创建自定义中间件。

## 实现 PSR-7 值对象类

为了使用 PSR-7 请求和响应，我们首先需要定义一系列值对象。这些是代表逻辑对象的类，用于基于 Web 的活动，例如 URL、文件上传以及流式请求或响应主体。

### 准备工作

PSR-7 接口的源代码可以作为 `Composer` 包获取。使用 `Composer` 管理外部软件（包括 PSR-7 接口）被认为是一种最佳实践。

### 具体操作方法...

1. 首先，请访问以下 URL 以获取 PSR-7 接口定义的最新版本：`https://github.com/php-fig/http-message`。也可以获取源代码。在撰写本文时，以下是可用的定义：

| 接口 | 继承自 | 说明 | 方法处理的内容 |
| :--- | :--- | :--- | :--- |
| MessageInterface | | 定义了 HTTP 消息通用的方法 | 标头、消息主体（即内容）和协议 |
| RequestInterface | MessageInterface | 表示客户端生成的请求 | URI、HTTP 方法和请求目标 |

2. 不幸的是，我们需要创建实现这些接口的具体类，才能利用 PSR-7。幸运的是，接口类通过一系列注释在内部得到了广泛的文档记录。我们将从一个包含有用常量的独立类开始：

> 请注意，我们利用 PHP 7 引入的一个新特性，允许将常量定义为数组。

```php
namespace Application\MiddleWare;
class Constants
{
    const HEADER_HOST = 'Host'; // 主机标头
    const HEADER_CONTENT_TYPE = 'Content-Type';
    const HEADER_CONTENT_LENGTH = 'Content-Length';

    const METHOD_GET = 'get';
    const METHOD_POST = 'post';
    const METHOD_PUT = 'put';
    const METHOD_DELETE = 'delete';
    const HTTP_METHODS = ['get', 'put', 'post', 'delete'];

    const STANDARD_PORTS = [
        'ftp' => 21, 'ssh' => 22, 'http' => 80, 'https' => 443
    ];

    const CONTENT_TYPE_FORM_ENCODED =
        'application/x-www-form-urlencoded';
    const CONTENT_TYPE_MULTI_FORM = 'multipart/form-data';
    const CONTENT_TYPE_JSON = 'application/json';
    const CONTENT_TYPE_HAL_JSON = 'application/hal+json';

    const DEFAULT_STATUS_CODE = 200;
    const DEFAULT_BODY_STREAM = 'php://input';
    const DEFAULT_REQUEST_TARGET = '/';

    const MODE_READ = 'r';
    const MODE_WRITE = 'w';

    // 注意：为了节省空间，并非所有错误常量都显示在此处
    const ERROR_BAD = 'ERROR: ';
    const ERROR_UNKNOWN = 'ERROR: unknown';

    // 注意：并非在此处显示所有的状态代码！
    const STATUS_CODES = [
        200 => 'OK',
        301 => 'Moved Permanently',
        302 => 'Found',
        401 => 'Unauthorized',
        404 => 'Not Found',
        405 => 'Method Not Allowed',
        418 => "I'm A Teapot",
        500 => 'Internal Server Error',
    ];
}
```

> 完整的 HTTP 状态代码列表可以在这里找到：https://tools.ietf.org/html/rfc7231#section-6.1.

3. 接下来，我们将着手处理代表由其他 PSR-7 类使用的值对象的类。首先，这里是一个代表 URI 的类。在构造函数中，我们接受一个 URI 字符串作为参数，并使用 parse_url() 函数将其分解为其组成部分：

```php
namespace Application\MiddleWare;
use InvalidArgumentException;
use Psr\Http\Message\UriInterface;
class Uri implements UriInterface
{
    protected $uriString;
    protected $uriParts = array();

    public function __construct($uriString)
    {
        $this->uriParts = parse_url($uriString);
        if (!$this->uriParts) {
            throw new InvalidArgumentException(
                Constants::ERROR_INVALID_URI);
        }
        $this->uriString = $uriString;
    }
}
```

> **URI** 代表 **统一资源标识符**。这就是你在发起请求时会在浏览器顶部看到的内容。有关 URL 组成的更多信息，请参阅 http://tools.ietf.org/html/rfc3986。

4. 在构造函数之后，我们定义方法来访问 URI 的组成部分。**scheme**（方案）代表 PHP 封装器（即 HTTP、FTP 等）：

```php
public function getScheme()
{
    return strtolower($this->uriParts['scheme']) ?? '';
}
```

5. **authority**（权威）代表用户名（如果存在）、主机，以及可选的端口号：

```php
public function getAuthority()
{
    $val = '';
    if (!empty($this->getUserInfo()))
        $val .= $this->getUserInfo() . '@';
    $val .= $this->uriParts['host'] ?? '';
    if (!empty($this->uriParts['port']))
        $val .= ':' . $this->uriParts['port'];
    return $val;
}
```

6. **User info**（用户信息）代表用户名（如果存在）以及可选的密码。使用密码的一个例子是访问 FTP 网站，例如 ftp://username:password@website.com:/path：

```php
public function getUserInfo()
{
    if (empty($this->uriParts['user'])) {
        return '';
    }

    $val = $this->uriParts['user'];
    if (!empty($this->uriParts['pass']))
        $val .= ':' . $this->uriParts['pass'];

    return $val;
}
```

7. **Host**（主机）是包含在 URI 中的 DNS 地址：

```php
public function getHost()
{
    if (empty($this->uriParts['host'])) {
        return '';
    }

    return strtolower($this->uriParts['host']);
}
```

8. **Port**（端口）是 HTTP 端口（如果存在）。你会注意到，如果端口列在我们的 STANDARD_PORTS 常量中，根据 PSR-7 的要求，返回值将是 NULL：

```php
public function getPort()
{
    if (empty($this->uriParts['port'])) {
        return NULL;
    } else {
        if ($this->getScheme()) {
            if ($this->uriParts['port'] ==
                Constants::STANDARD_PORTS[$this->getScheme()]) {
                return NULL;
            }
        }

        return (int) $this->uriParts['port'];
    }
}
```





9. **路径** 是 URI 中跟随 DNS 地址的部分。根据 PSR-7，此部分必须经过编码。我们使用 `rawurlencode()` PHP 函数，因为它符合 RFC 3986 标准。然而，我们不能直接编码整个路径，因为路径分隔符（即 /）也会被编码！因此，我们需要先使用 `explode()` 将其拆分，对各个部分进行编码，然后再重新组合：

```php
public function getPath()
{
    if (empty($this->urlParts['path'])) {
        return '';
    }
    return implode('/', array_map("rawurlencode",
        explode('/', $this->urlParts['path'])));
}
```

10. 接下来，我们定义一个方法来检索 *查询* 字符串（即来自 $_GET）。这些内容也必须进行 URL 编码。首先，我们定义 `getQueryParams()`，它将查询字符串拆分为一个关联数组。请注意，为了刷新查询参数，我们提供了一个 *重置* 选项。然后，我们定义 `getQuery()`，它接受该数组并生成正确的 URL 编码字符串：

```php
public function getQueryParams($reset = FALSE)
{
    if ($this->queryParams && !$reset) {
        return $this->queryParams;
    }
    $this->queryParams = [];
    if (!empty($this->uriParts['query'])) {
        foreach (explode('&', $this->uriParts['query']) as $keyPair) {
            list($param,$value) = explode('=', $keyPair);
            $this->queryParams[$param] = $value;
        }
    }
    return $this->queryParams;
}

public function getQuery()
{
    if (!$this->getQueryParams()) {
        return '';
    }
    $output = '';
    foreach ($this->getQueryParams() as $key => $value) {
        $output .= rawurlencode($key) . '='
            . rawurlencode($value) . '&';
    }
    return substr($output, 0, -1);
}
```

11. 之后，我们提供一个方法返回片段（即 URL 中的 #）及其后跟随的任何部分：

```php
public function getFragment()
{
    if (empty($this->uriParts['fragment'])) {
        return '';
    }

    return rawurlencode($this->uriParts['fragment']);
}
```

12. 接下来，我们定义一系列 `withXXX()` 方法，这些方法与上述描述的 `getXXX()` 方法相对应。这些方法旨在添加、替换或删除与请求类相关的属性（方案、权威、用户信息等）。此外，这些方法返回当前实例，从而允许我们将这些方法用于一系列连续调用（通常称为流畅接口）。我们从 `withScheme()` 开始：

![](img/39390f6d56c5a83b28db083a8bd5185c_565_0.png)

```php
public function withScheme($scheme)
{
    if (empty($scheme) && $this->getScheme()) {
        unset($this->uriParts['scheme']);
    } else {
        if (isset(STANDARD_PORTS[strtolower($scheme)])) {
            $this->uriParts['scheme'] = $scheme;
        } else {
            throw new InvalidArgumentException(
                Constants::ERROR_BAD . __METHOD__);
        }
    }

    return $this;
}
```

13. 然后，我们对覆盖、添加或替换用户信息、主机、端口、路径、查询和片段的方法应用类似的逻辑。请注意，`withQuery()` 方法会重置查询参数数组。`withHost()`、`withPort()`、`withPath()` 和 `withFragment()` 使用相同的逻辑，但为了节省篇幅未在此展示：

```php
public function withUserInfo($user, $password = null)
{
    if (empty($user) && $this->getUserInfo()) {
        unset($this->uriParts['user']);
    } else {
        $this->uriParts['user'] = $user;
        if ($password) {
            $this->uriParts['pass'] = $password;
        }
    }

    return $this;
}
// Not shown: withHost(),withPort(),withPath(),withFragment()

public function withQuery($query)
{
    if (empty($query) && $this->getQuery()) {
        unset($this->uriParts['query']);
    } else {
        $this->uriParts['query'] = $query;
    }
    // reset query params array
    $this->getQueryParams(TRUE);

    return $this;
}
```

14. 最后，我们用 `__toString()` 方法封装 `Application\Middleware\Uri` 类，当该对象在字符串上下文中使用时，它会返回由 `$uriParts` 组装成的正确 URI。我们还定义了一个便捷方法 `getUriString()`，它只是简单地调用 `__toString()`：

```php
public function __toString()
{
    $uri = ($this->getScheme())
        ? $this->getScheme() . '://' : '';
```

15. 如果存在权威 URI 部分，我们就添加它。权威部分包括用户信息、主机和端口。否则，我们只附加主机和端口：

```php
if ($this->getAuthority()) {
    $uri .= $this->getAuthority();
} else {
$uri .= ($this->getHost() ? $this->getHost() : '';
$uri .= ($this->getPort()
? ':' . $this->getPort() : '';)
}
```

16. 在添加路径之前，我们首先检查第一个字符是否为 `/`。如果不是，我们需要添加此分隔符。然后，如果存在查询和片段，我们就添加它们：

```php
$path = $this->getPath();
if ($path) {
    if ($path[0] != '/') {
        $uri .= '/' . $path;
    } else {
        $uri .= $path;
    }
}
$uri .= ($this->getQuery()
? '?' . $this->getQuery() : '';
$uri .= ($this->getFragment())
? '#' . $this->getFragment() : '';
return $uri;
}
```

```php
public function getUriString()
{
    return $this->__toString();
}
```

> 注意使用了字符串解引用（即 $path[0]），这是 PHP 7 的一部分。

17. 接下来，我们将注意力转向代表消息主体的类。由于主体可能有多大是未知的，PSR-7 建议将主体视为流。流是一种资源，允许以线性方式访问输入和输出源。在 PHP 中，所有文件命令都运行在 Streams 子系统之上，因此这是一个自然的选择。PSR-7 通过定义 `Psr\Http\Message\StreamInterface` 来形式化这一点，该接口定义了诸如 `read()`、`write()`、`seek()` 等方法。现在我们展示 `Application\MiddleWare\Stream`，我们可以用它来表示传入或传出请求和/或响应的主体：

```php
namespace Application\MiddleWare;
use SplFileInfo;
use Throwable;
use RuntimeException;  
use Psr\Http\Message\StreamInterface;  

class Stream implements StreamInterface
{
    protected $stream;
    protected $metadata;
    protected $info;
```

18. 在构造函数中，我们使用简单的 `fopen()` 命令打开流。然后，我们使用 `stream_get_meta_data()` 获取流的信息。对于其他详细信息，我们创建一个 `SplFileInfo` 实例：

```php
public function __construct($input, $mode = self::MODE_READ)
{
    $this->stream = fopen($input, $mode);
    $this->metadata = stream_get_meta_data($this->stream);
    $this->info = new SplFileInfo($input);
}
```

> 我们选择 `fopen()` 而不是更现代的 `SplFileObject` 的原因是，后者不允许直接访问内部文件资源对象，因此对于此应用无用。

19. 我们包含两个便捷方法，分别提供对资源的访问以及对 `SplFileInfo` 实例的访问：

```php
public function getStream()
{
    return $this->stream;
}

public function getInfo()
{
    return $this->info;
}
```

20. 接下来，我们定义低级核心流式处理方法：

```php
public function read($length)
{
    if (fread($this->stream, $length)) {
        throw new RuntimeException(
            self::ERROR_BAD . __METHOD__
        );
    }
}

public function write($string)
{
    if (!fwrite($this->stream, $string)) {
        throw new RuntimeException(
            self::ERROR_BAD . __METHOD__);
    }
}

public function rewind()
{
    if (!rewind($this->stream)) {
        throw new RuntimeException(
            self::ERROR_BAD . __METHOD__);
    }
}

public function eof()
{
    return eof($this->stream);
}

public function tell()
{
    try {
        return ftell($this->stream);
    } catch (Throwable $e) {
        throw new RuntimeException(
            self::ERROR_BAD . __METHOD__);
    }
}

public function seek($offset, $whence = SEEK_SET)
{
    try {
        fseek($this->stream, $offset, $whence);
    } catch (Throwable $e) {
        throw new RuntimeException(
            self::ERROR_BAD . __METHOD__);
    }
}

public function close()
{
    if ($this->stream) {
        fclose($this->stream);
    }
}

public function detach()
{
    return $this->close();
}
```





## 定义 PSR-7 类

我们还需要定义一些信息性方法，以获取关于流的信息：

```php
public function getMetadata($key = null)
{
    if ($key) {
        return $this->metadata[$key] ?? NULL;
    } else {
        return $this->metadata;
    }
}

public function getSize()
{
    return $this->info->getSize();
}

public function isSeekable()
{
    return boolval($this->metadata['seekable']);
}

public function isWritable()
{
    return $this->stream->isWritable();
}

public function isReadable()
{
    return $this->info->isReadable();
}
```

遵循 PSR-7 指南，我们随后定义 `getContents()` 和 `__toString()` 方法，以便转储流的内容：

```php
public function __toString()
{
    $this->rewind();
    return $this->getContents();
}

public function getContents()
{
    ob_start();
    if (!fpassthru($this->stream)) {
        throw new RuntimeException(
            self::ERROR_BAD . __METHOD__
        );
    }
    return ob_get_clean();
}
```

前文所示的 Stream 类的一个重要变体是 TextStream，它专门针对主体为字符串（即编码为 JSON 的数组）而非文件的情况设计。由于我们需要绝对确保传入的 `$input` 值是字符串数据类型，因此在开始标签后立即调用 PHP 7 的严格类型声明。我们还标识了一个 `$pos` 属性（即位置），该属性将模拟文件指针，但它指向的是字符串内的位置，而不是文件：

```php
<?php
declare(strict_types=1);
namespace Application\Middleware;
use Throwable;
use RuntimeException;
use SplFileInfo;
use Psr\Http\Message\StreamInterface;

class TextStream implements StreamInterface
{
    protected $stream;
    protected $pos = 0;
```

大多数方法都非常简单且不言自明。`$stream` 属性即为输入字符串：

```php
public function __construct(string $input)
{
    $this->stream = $input;
}

public function getStream()
{
    return $this->stream;
}

public function getInfo()
{
    return NULL;
}

public function getContents()
{
    return $this->stream;
}

public function __toString()
{
    return $this->getContents();
}

public function getSize()
{
    return strlen($this->stream);
}
```

```php
public function close()
{
    // 不做任何事：你如何“关闭”字符串呢？
}
public function detach()
{
    return $this->close();  // 即：不做任何事！
}
```

为了模拟流行为，`tell()`、`eof()`、`seek()` 等方法都与 `$pos` 交互：

```php
public function tell()
{
    return $this->pos;
}
public function eof()
{
    return ($this->pos == strlen($this->stream));
}
public function isSeekable()
{
    return TRUE;
}
public function seek($offset, $whence = NULL)
{
    if ($offset < $this->getSize()) {
        $this->pos = $offset;
    } else {
        throw new RuntimeException(
            Constants::ERROR_BAD . __METHOD__ );
    }
}
public function rewind()
{
    $this->pos = 0;
}
public function isWritable()
{
    return TRUE;
}
```

`read()` 和 `write()` 方法与 `$pos` 和子字符串交互：

```php
public function write($string)
{
    $temp = substr($this->stream, 0, $this->pos);
    $this->stream = $temp . $string;
    $this->pos = strlen($this->stream);
}

public function isReadable()
{
    return TRUE;
}

public function read($length)
{
    return substr($this->stream, $this->pos, $length);
}

public function getMetadata($key = null)
{
    return NULL;
}
```

最后一个介绍的类值是 `Application\Middleware\UploadedFile`。与其他类一样，我们首先定义表示文件上传各个方面的属性：

```php
namespace Application\Middleware;
use RuntimeException;
use InvalidArgumentException;
use Psr\Http\Message\UploadedFileInterface;
class UploadedFile implements UploadedFileInterface
{
    protected $field;    // 文件上传字段的原始名称
    protected $info;     // $_FILES[$field]
    protected $randomize;
    protected $movedName = '';
```

在构造函数中，我们允许定义文件上传表单字段的名称属性，以及 `$_FILES` 中对应的数组。我们添加最后一个参数，以指示在确认上传的文件后，是否希望该类生成一个新的随机文件名：

```php
public function __construct(
    $field, array $info, $randomize = FALSE)
{
    $this->field = $field;
    $this->info = $info;
    $this->randomize = $randomize;
}
```

接下来，我们为临时文件或移动后的文件创建一个 Stream 类实例：

```php
public function getStream()
{
    if (!$this->stream) {
        if ($this->movedName) {
            $this->stream = new Stream($this->movedName);
        } else {
            $this->stream = new Stream($info['tmp_name']);
        }
    }
    return $this->stream;
}
```

`moveTo()` 方法执行实际的移动文件操作。请注意，有大量的安全检查系列，以帮助防止注入攻击。如果没有启用 `randomize`，我们使用原始的用户提供文件名：

```php
public function moveTo($targetPath)
{
    if ($this->moved) {
        throw new Exception(Constants::ERROR_MOVE_DONE);
    }
    if (!file_exists($targetPath)) {
        throw new InvalidArgumentException(Constants::ERROR_BAD_DIR);
    }
    $tempFile = $this->info['tmp_name'] ?? FALSE;
    if (!$tempFile || !file_exists($tempFile)) {
        throw new Exception(Constants::ERROR_BAD_FILE);
    }
    if (is_uploaded_file($tempFile)) {
        throw new Exception(Constants::ERROR_FILE_NOT);
    }
```

```php
if ($this->randomize) {
    $final = bin2hex(random_bytes(8)) . '.txt';
} else {
    $final = $this->info['name'];
}
$final = $targetPath . '/' . $final;
$final = str_replace('//', '/', $final);
if (!move_uploaded_file($tempFile, $final)) {
    throw new RuntimeException(Constants::ERROR_MOVE_UNABLE);
}

$this->movedName = $final;
return TRUE;
}
```

随后，我们通过 `$info` 属性提供对 `$_FILES` 中返回的其他参数的访问。请注意，`getClientFilename()` 和 `getClientMediaType()` 的返回值应被视为不可信的，因为它们来自外部。我们还添加了一个方法来返回移动后的文件名：

```php
public function getMovedName()
{
    return $this->movedName ?? NULL;
}
public function getSize()
{
    return $this->info['size'] ?? NULL;
}
public function getError()
{
    if (!$this->moved) {
        return UPLOAD_ERR_OK;
    }
    return $this->info['error'];
}
public function getClientFilename()
{
    return $this->info['name'] ?? NULL;
}
public function getClientMediaType()
{
    return $this->info['type'] ?? NULL;
}
```

## 工作原理...

首先，前往 `https://github.com/php-fig/http-message/tree/master/src`，这是 PSR-7 接口的 GitHub 仓库，并下载这些文件。在 `/path/to/` 下创建一个名为 `Psr/Http/Message` 的目录，并将文件放置在那里。或者，你可以访问 `https://packagist.org/packages/psr/http-message` 并使用 Composer 安装源代码。（有关如何获取和使用 Composer 的说明，你可以访问 `https://getcomposer.org/`。）

然后，定义前面讨论过的类，总结如下表所示：

| 类 | 讨论所在步骤 |
| --- | --- |
| Application\Middleware\Constants | 2 |
| Application\Middleware\Uri | 3 到 16 |
| Application\Middleware\Stream | 17 到 22 |
| Application\Middleware\TextStream | 23 到 26 |
| Application\Middleware\UploadedFile | 27 到 31 |

接下来，定义一个名为 `chap_09_middleware_value_objects_uri.php` 的调用程序，该程序实现了自动加载并使用适当的类。请注意，如果你使用 Composer，除非另有指示，否则它会创建一个名为 `vendor` 的文件夹。Composer 还会添加其自己的自动加载器，你可以在这里自由使用它：

```php
<?php
require __DIR__ . '/../Application/Autoload/Loader.php';
Application\Autoload\Loader::init(__DIR__ . '/..');
use Application\Middleware\Uri;
```

然后，你可以创建一个 Uri 实例并使用 `with` 方法添加参数。随后，你可以直接输出 `Uri` 实例，因为定义了 `__toString()` 方法：

```php
$uri = new Uri();
$uri->withScheme('https')
    ->withHost('localhost')
    ->withPort('8080')
    ->withPath('chap_09_middleware_value_objects_uri.php')
    ->withQuery('param=TEST');

echo $uri;
```





以下是预期结果：

![](img/39390f6d56c5a83b28db083a8bd5185c_577_0.png)

接下来，从 /path/to/source/for/this/chapter 创建一个名为 uploads 的目录。请继续定义另一个调用程序 `chap_09_middleware_value_objects_file_upload.php`，该程序设置自动加载并使用相应的类：

```php
<?php
define('TARGET_DIR', __DIR__ . '/uploads');
require __DIR__ . '/../Application/Autoload/Loader.php';
Application\Autoload\Loader::init(__DIR__ . '/..');
use Application\MiddleWare\UploadedFile;
```

在 try...catch 块中，检查是否有任何文件被上传。如果有，循环遍历 $_FILES，并在 tmp_name 已设置的情况下创建 UploadedFile 实例。然后可以使用 moveTo() 方法将文件移动到 TARGET_DIR：

```php
try {
    $message = '';
    $uploadedFiles = array();
    if (isset($_FILES)) {
        foreach ($_FILES as $key => $info) {
            if ($info['tmp_name']) {
                $uploadedFiles[$key] = new UploadedFile(
                    $key, $info, TRUE);
                $uploadedFiles[$key]->moveTo(TARGET_DIR);
            }
        }
    }
} catch (Throwable $e) {
    $message = $e->getMessage();
}
?>
```

在视图逻辑中，显示一个简单的文件上传表单。您也可以使用 phpinfo() 来显示关于已上传内容的信息：

```html
<form name="search" method="post"
    enctype="<?= Constants::CONTENT_TYPE_MULTI_FORM ?>">
    <table class="display" cellspacing="0" width="100%">
        <tr><th>Upload 1</th><td><input type="file" name="upload_1" /></td></tr>
        <tr><th>Upload 2</th><td><input type="file" name="upload_2" /></td></tr>
        <tr><th>Upload 3</th><td><input type="file" name="upload_3" /></td></tr>
        <tr><th>&nbsp;</th><td><input type="submit" /></td></tr>
    </table>
</form>
<?= ($message) ? '<h1>' . $message . '</h1>' : ''; ?>
```

接下来，如果有任何已上传的文件，您可以显示每个文件的信息。您还可以使用 getStream() 后跟 getContents() 来显示每个文件（假设您正在使用短文本文件）：

```html
<?php if ($uploadedFiles) : ?>
    <table class="display" cellspacing="0" width="100%">
        <tr>
            <th>Filename</th><th>Size</th>
            <th>Moved Filename</th><th>Text</th>
        </tr>
        <?php foreach ($uploadedFiles as $obj) : ?>
            <?php if ($obj->getMovedName()) : ?>
            <tr>
                <td><?= htmlspecialchars($obj->getClientFilename()) ?></td>
                <td><?= $obj->getSize() ?></td>
                <td><?= $obj->getMovedName() ?></td>
                <td><?= $obj->getStream()->getContents() ?></td>
            </tr>
            <?php endif; ?>
        <?php endforeach; ?>
    </table>
<?php endif; ?>
<?php phpinfo(INFO_VARIABLES); ?>
```

输出可能如下所示：

![](img/39390f6d56c5a83b28db083a8bd5185c_579_0.png)

## 另请参阅

- 有关 PSR 的更多信息，请查看 [PHP 标准推荐](https://en.wikipedia.org/wiki/PHP_Standard_Recommendation)
- 关于 PSR-7 的具体信息，这里是官方描述： [http://www.php-fig.org/psr/psr-7/](http://www.php-fig.org/psr/psr-7/)
- 有关 PHP 流的信息，请查看 [http://php.net/manual/en/book.stream.php](http://php.net/manual/en/book.stream.php)

## 开发 PSR-7 Request 类

PSR-7 中间件的一个关键特征是使用了 **Request** 和 **Response** 类。应用后，这使得不同的软件块能够协同工作，而它们之间不需要共享任何特定知识。在此上下文中，请求类应包含原始用户请求的所有方面，包括浏览器设置、请求的原始 URL、传递的参数等。

### 如何实现…

1.  首先，确保定义表示 `Uri`、`Stream` 和 `UploadedFile` 值对象的类，如前面的食谱中所述。
2.  现在我们可以定义核心 `Application\MiddleWare\Message` 类。该类使用 `Stream` 和 `Uri` 并实现 `Psr\Http\Message\MessageInterface`。我们首先定义关键值对象的属性，包括表示消息主体（即 `StreamInterface` 实例）、版本和 HTTP 头的属性：

```php
namespace Application\MiddleWare;
use Psr\Http\Message\ {
    MessageInterface,
    StreamInterface,
    UriInterface
};
class Message implements MessageInterface
{
    protected $body;
    protected $version;
    protected $httpHeaders = array();
```

3.  接下来，我们有表示 `StreamInterface` 实例的 `getBody()` 方法。一个配套方法 `withBody()` 返回当前的 `Message` 实例，并允许我们覆盖 `body` 的当前值：

```php
public function getBody()
{
    if (!$this->body) {
        $this->body = new Stream(self::DEFAULT_BODY_STREAM);
    }
    return $this->body;
}
public function withBody(StreamInterface $body)
{
    if (!$body->isReadable()) {
        throw new InvalidArgumentException(
            self::ERROR_BODY_UNREADABLE);
    }
    $this->body = $body;
    return $this;
}
```

4.  PSR-7 建议将头视为不区分大小写。因此，我们定义了一个 findHeader() 方法（未被 MessageInterface 直接定义），该方法使用 stripos() 定位头：

```php
protected function findHeader($name)
{
    $found = FALSE;
    foreach (array_keys($this->getHeaders()) as $header) {
        if (stripos($header, $name) !== FALSE) {
            $found = $header;
            break;
        }
    }
    return $found;
}
```

5.  下一个方法，未在 PSR-7 中定义，旨在填充 $httpHeaders 属性。该属性假设是一个关联数组，其中键是头，值是表示头值的字符串。如果有多个值，则以逗号分隔的附加值会被追加到字符串中。Apache 扩展有一个出色的 apache_request_headers() PHP 函数，如果在 $httpHeaders 中尚未提供头，则会产生这些头：

```php
protected function getHttpHeaders()
{
    if (!$this->httpHeaders) {
        if (function_exists('apache_request_headers')) {
            $this->httpHeaders = apache_request_headers();
        } else {
            $this->httpHeaders = $this->altApacheReqHeaders();
        }
    }
    return $this->httpHeaders;
}
```

6.  如果 apache_request_headers() 不可用（即未启用 Apache 扩展），我们提供了一个替代方案 altApacheReqHeaders()：

```php
protected function altApacheReqHeaders()
{
    $headers = array();
    foreach ($_SERVER as $key => $value) {
        if (stripos($key, 'HTTP_') !== FALSE) {
            $headerKey = str_replace('HTTP_', '', $key);
            $headers[$this->explodeHeader($headerKey)] = $value;
        }
```

## 定义 PSR-7 类

```php
            } elseif (stripos($key, 'CONTENT_') !== FALSE) {
                $headers[$this->explodeHeader($key)] = $value;
            }
        }
        return $headers;
    }
    protected function explodeHeader($header)
    {
        $headerParts = explode('-', $header);
        $headerKey = ucwords(implode(' ', strtolower($headerParts)));
        return str_replace(' ', '-', $headerKey);
    }
```

7.  实现 getHeaders()（PSR-7 中要求）现在只是一个遍历 getHttpHeaders() 方法（在第 4 步中讨论）生成的 $httpHeaders 属性的简单循环：

```php
    public function getHeaders()
    {
        foreach ($this->getHttpHeaders() as $key => $value) {
            header($key . ': ' . $value);
        }
    }
```

8.  同样，我们提供了一系列 with 方法，旨在覆盖或替换头。由于可能有多个头，我们还提供一个方法向现有头集合中添加头。withoutHeader() 方法用于移除某个头实例。注意在前一步骤中提到的 findHeader() 的一致使用，以允许对头进行不区分大小写的处理：

```php
    public function withHeader($name, $value)
    {
        $found = $this->findHeader($name);
        if ($found) {
            $this->httpHeaders[$found] = $value;
        } else {
            $this->httpHeaders[$name] = $value;
        }
        return $this;
    }

    public function withAddedHeader($name, $value)
    {
        $found = $this->findHeader($name);
        if ($found) {
```





### 9. 然后，我们提供了一系列有用的请求头相关方法，用于确认请求头是否存在、获取单个请求头行以及以数组形式获取请求头，符合 PSR-7 标准：

```php
public function hasHeader($name)
{
    return boolval($this->findHeader($name));
}

public function getHeaderLine($name)
{
    $found = $this->findHeader($name);
    if ($found) {
        return $this->httpHeaders[$found];
    } else {
        return '';
    }
}

public function getHeader($name)
{
    $line = $this->getHeaderLine($name);
    if ($line) {
        return explode(',', $line);
    } else {
        return array();
    }
}
```

### 10. 最后，为了完善请求头的处理，我们介绍了 `getHeadersAsString` 方法，该方法生成一个单独的请求头字符串，其中各请求头之间使用 `\r\n` 分隔，以便直接用于 PHP 流上下文：

```php
public function getHeadersAsString()
{
    $output = '';
    $headers = $this->getHeaders();
    if ($headers && is_array($headers)) {
        foreach ($headers as $key => $value) {
            if ($output) {
                $output .= "\r\n" . $key . ': ' . $value;
            } else {
                $output  = $key . ': ' . $value;
            }
        }
    }
    return $output;
}
```

### 11. 仍在 Message 类中，我们现在将注意力转向版本处理。根据 PSR-7，协议版本（即 HTTP/1.1）的返回值应仅包含数字部分。出于此原因，我们还提供了 `onlyVersion()` 方法，该方法去除所有非数字字符，但允许保留句号：

```php
public function getProtocolVersion()
{
    if (!isset($this->version)) {
        $this->version = $this->onlyVersion(
            $_SERVER['SERVER_PROTOCOL']
        );
    }
    return $this->version;
}
```

```php
public function withProtocolVersion($version)
{
    $this->version = $this->onlyVersion($version);
    return $this;
}
```

```php
protected function onlyVersion($version)
{
    if (!empty($version)) {
        return preg_replace('/[^0-9\.]/', '', $version);
    } else {
        return NULL;
    }
}
```

### 12. 最后，几乎是顺理成章地，我们准备好定义我们的 Request 类。然而，必须指出的是，我们需要考虑出站请求和入站请求。也就是说，我们需要一个类来表示客户端将向服务器发出的传出请求，以及服务器从客户端接收到的请求。相应地，我们提供了 `Application\MiddleWare\Request`（客户端将向服务器发出的请求）和 `Application\MiddleWare\ServerRequest`（服务器从客户端接收到的请求）。好消息是，我们的大部分工作已经完成：请注意，我们的 Request 类继承了 Message。我们还提供了表示 URL 和 HTTP 方法的属性：

```php
namespace Application\Middleware;

use InvalidArgumentException;
use Psr\Http\Message\{ RequestInterface, StreamInterface, UriInterface };

class Request extends Message implements RequestInterface
{
    protected $uri;
    protected $method; // HTTP method
    protected $uriObj; // Psr\Http\Message\UriInterface instance
```

### 13. 构造函数中的所有属性默认为 NULL，但我们保留了立即定义相应参数的可能性。我们使用继承的 `onlyVersion()` 方法对版本进行清理。我们还定义了 `checkMethod()`，以确保提供的任何方法都在我们支持的 HTTP 方法列表中，该列表在 Constants 中定义为常量数组：

```php
public function __construct($uri = NULL,
                           $method = NULL,
                           StreamInterface $body = NULL,
                           $headers = NULL,
                           $version = NULL)
{
    $this->uri = $uri;
    $this->body = $body;
    $this->method = $this->checkMethod($method);
    $this->httpHeaders = $headers;
    $this->version = $this->onlyVersion($version);
}

protected function checkMethod($method)
{
    if ($method !== NULL) {
        if (!in_array(strtolower($method), Constants::HTTP_METHODS)) {
            throw new InvalidArgumentException(
                Constants::ERROR_HTTP_METHOD
            );
        }
    }
    return $method;
}
```

### 14. 我们将解释请求目标为原始请求的 URI，形式为字符串。请记住，我们的 `Uri` 类有方法可以将其解析为其组成部分，因此我们提供了 `$uriObj` 属性。在 `withRequestTarget()` 的情况下，请注意我们运行了 `getUri()`，它执行上述解析过程：

```php
public function getRequestTarget()
{
    return $this->uri ?? Constants::DEFAULT_REQUEST_TARGET;
}

public function withRequestTarget($requestTarget)
{
    $this->uri = $requestTarget;
    $this->getUri();
    return $this;
}
```

### 15. 我们的 `get` 和 `with` 方法，代表 HTTP 方法，没有让人意外的地方。我们使用在构造函数中同样使用的 `checkMethod()`，以确保该方法匹配我们计划支持的那些方法：

```php
public function getMethod()
{
    return $this->method;
}

public function withMethod($method)
{
    $this->method = $this->checkMethod($method);
    return $this;
}
```

## 附录

### 16. 最后，我们有一个针对 URI 的 `get` 和 `with` 方法。如步骤 14 中所述，我们在 `Uri` 属性中保留原始请求字符串，在 `UriObj` 中保留新解析的 `Uri` 实例。注意额外的标志用于保留任何现有的 Host 请求头：

```php
public function getUri()
{
    if (!$this->uriObj) {
        $this->uriObj = new Uri($this->uri);
    }
    return $this->uriObj;
}

public function withUri(UriInterface $uri, $preserveHost = false)
{
    if ($preserveHost) {
        $found = $this->findHeader(Constants::HEADER_HOST);
        if (!$found && $uri->getHost()) {
            $this->httpHeaders[Constants::HEADER_HOST] = $uri->getHost();
        } elseif ($uri->getHost()) {
            $this->httpHeaders[Constants::HEADER_HOST] = $uri->getHost();
        }
        $this->uri = $uri->__toString();
        return $this;
    }
}
```

### 17. ServerRequest 类继承自 Request，并提供了额外功能，以检索处理传入请求的服务器感兴趣的信息。我们通过定义将表示从各种 PHP `$_` 超全局变量（即 `$_SERVER`、`$_POST` 等）读取的传入数据的属性开始：

```php
namespace Application\Middleware;
use Psr\Http\Message\{ ServerRequestInterface,
UploadedFileInterface };

class ServerRequest extends Request implements
ServerRequestInterface
{
    protected $serverParams;
    protected $cookies;
    protected $queryParams;
    protected $contentType;
    protected $parsedBody;
    protected $attributes;
    protected $method;
    protected $uploadedFileInfo;
    protected $uploadedFileObjs;
}
```

### 18. 然后我们定义了一系列获取器来提取超全局变量信息。为了节省空间，我们没有展示所有内容：

```php
public function getServerParams()
{
    if (!$this->serverParams) {
        $this->serverParams = $_SERVER;
    }
    return $this->serverParams;
}
// getCookiesParams() reads $_COOKIE
// getQueryParams() reads $_GET
// getUploadedFileInfo() reads $_FILES

public function getRequestMethod()
{
    $method = $this->getServerParams()['REQUEST_METHOD'] ?? '';
    $this->method = strtolower($method);
    return $this->method;
}

public function getContentType()
{
    if (!$this->contentType) {
        $this->contentType =
            $this->getServerParams()['CONTENT_TYPE'] ?? '';
        $this->contentType = strtolower($this->contentType);
    }
    return $this->contentType;
}
```

### 19. 由于上传的文件应当被表示为独立的 UploadedFile 对象（在之前的配方中介绍），我们也定义了一个方法，该方法接收 `$uploadedFileInfo` 并创建 UploadedFile 对象：

```php
public function getUploadedFiles()
{
    if (!$this->uploadedFileObjs) {
```




## 附录

```php
foreach ($this->getUploadedFileInfo() as $field => $value) {
    $this->uploadedFileObjs[$field] =
        new UploadedFile($field, $value);
}
}
return $this->uploadedFileObjs;
}
```

20. 与之前定义的其他类类似，我们提供用于添加或覆盖属性并返回新实例的方法：

```php
public function withCookieParams(array $cookies)
{
    array_merge($this->getCookieParams(), $cookies);
    return $this;
}
public function withQueryParams(array $query)
{
    array_merge($this->getQueryParams(), $query);
    return $this;
}
public function withUploadedFiles(array $uploadedFiles)
{
    if (!count($uploadedFiles)) {
        throw new InvalidArgumentException(
            Constant::ERROR_NO_UPLOADED_FILES);
    }
    foreach ($uploadedFiles as $fileObj) {
        if (!$fileObj instanceof UploadedFileInterface) {
            throw new InvalidArgumentException(
                Constant::ERROR_INVALID_UPLOADED);
        }
    }
    $this->uploadedFileObjs = $uploadedFiles;
}
```

21. PSR-7 消息的一个重要方面是，主体（body）也应以解析后的形式可用，也就是说，是一种结构化的表示形式，而不仅仅是原始流。因此，我们定义了 `getParsedBody()` 及其配套的 `with` 方法。当涉及表单提交时，PSR-7 的建议非常具体。请注意一系列检查 `Content-Type` 头部以及方法的 if 语句：

```php
public function getParsedBody()
{
    if (!$this->parsedBody) {
        if (($this->getContentType() ==
            Constants::CONTENT_TYPE_FORM_ENCODED
            || $this->getContentType() ==
            Constants::CONTENT_TYPE_MULTI_FORM)
            && $this->getRequestMethod() ==
            Constants::METHOD_POST)
        {
            $this->parsedBody = $_POST;
        } elseif ($this->getContentType() ==
            Constants::CONTENT_TYPE_JSON
            || $this->getContentType() ==
            Constants::CONTENT_TYPE_HAL_JSON)
        {
            ini_set("allow_url_fopen", true);
            $this->parsedBody =
                json_decode(file_get_contents('php://input'));
        } elseif (!empty($_REQUEST)) {
            $this->parsedBody = $_REQUEST;
        } else {
            ini_set("allow_url_fopen", true);
            $this->parsedBody = file_get_contents('php://input');
        }
    }
    return $this->parsedBody;
}

public function withParsedBody($data)
{
    $this->parsedBody = $data;
    return $this;
}
```

22. 我们还允许使用未在 PSR-7 中精确定义的属性。相反，我们将此保持开放，以便开发人员可以根据应用程序需要提供任何适当的内容。请注意使用 `withoutAttributes()`，它允许你随时移除属性：

```php
public function getAttributes()
{
    return $this->attributes;
}

public function getAttribute($name, $default = NULL)
{
    return $this->attributes[$name] ?? $default;
}

public function withAttribute($name, $value)
{
    $this->attributes[$name] = $value;
    return $this;
}
public function withoutAttribute($name)
{
    if (isset($this->attributes[$name])) {
        unset($this->attributes[$name]);
    }
    return $this;
}
```

23. 最后，为了从入站请求中加载不同的属性，我们定义了 `initialize()`，虽然它不在 PSR-7 中，但极其方便：

```php
public function initialize()
{
    $this->getServerParams();
    $this->getCookieParams();
    $this->getQueryParams();
    $this->getUploadedFiles();
    $this->getRequestMethod();
    $this->getContentType();
    $this->getParsedBody();
    return $this;
}
```

## 工作原理...

首先，请确保完成前面的食谱，因为 `Message` 和 `Request` 类使用 `Uri`、`Stream` 和 `UploadedFile` 值对象。之后，请定义下表中总结的类：

| 类 | 讨论的步骤 |
| :----- | :--------------------- |
| `Application\MiddleWare\Message` | 步骤 2 至 9 |
| `Application\MiddleWare\Request` | 步骤 10 至 14 |
| `Application\MiddleWare\ServerRequest` | 步骤 15 至 20 |

之后，你可以定义一个服务器程序 `chap_09_middleware_server.php`，该程序设置自动加载并使用适当的类。此脚本将传入的请求拉入一个 `ServerRequest` 实例，初始化它，然后使用 `var_dump()` 显示接收到的信息：

```php
<?php
require __DIR__ . '/../Application/Autoload/Loader.php';
Application\Autoload\Loader::init(__DIR__ . '../');
use Application\MiddleWare\ServerRequest;

$request = new ServerRequest();
$request->initialize();
echo '<pre>', var_dump($request), '</pre>';
```

要运行服务器程序，首先切换到 `/path/to/source/for/this/chapter` 文件夹。然后可以运行以下命令：

```bash
php -S localhost:8080 chap_09_middleware_server.php
```

对于客户端，首先创建一个调用程序 `chap_09_middleware_request.php`，该程序设置自动加载，使用适当的类，并定义目标服务器和一个本地文本文件：

```php
<?php
define('READ_FILE', __DIR__ . '/getysburg.txt');
define('TEST_SERVER', 'http://localhost:8080/');
require __DIR__ . '/../Application/Autoload/Loader.php';
Application\Autoload\Loader::init(__DIR__ . '../');
use Application\MiddleWare{ Request, Stream, Constants };
```

接下来，你可以使用文本作为源创建一个 `Stream` 实例。这将成为一个新 `Request` 的主体，在这种情况下，它镜像了表单提交可能预期的内容：

```php
$body = new Stream(READ_FILE);
```

然后，你可以直接构建一个 `Request` 实例，并提供适当的参数：

```php
$request = new Request(
    TEST_SERVER,
    Constants::METHOD_POST,
    $body,
    [Constants::HEADER_CONTENT_TYPE =>
        Constants::CONTENT_TYPE_FORM_ENCODED,
        Constants::HEADER_CONTENT_LENGTH => $body->getSize()]
    );
```

或者，你可以使用流畅接口语法产生完全相同的结果：

```php
$uriObj = new Uri(TEST_SERVER); 
$request = new Request(); 
$request->withRequestTarget(TEST_SERVER) 
    ->withMethod(Constants::METHOD_POST) 
    ->withBody($body) 
    ->withHeader(Constants::HEADER_CONTENT_TYPE, Constants::CONTENT_TYPE_FORM_ENCODED) 
    ->withAddedHeader(Constants::HEADER_CONTENT_LENGTH, $body->getSize());
```

然后，你可以设置一个 cURL 资源来模拟表单提交，其中 `data` 参数是文本文件的内容。你可以跟随 `curl_init()`、`curl_exec()` 等，回显结果：

```php
$data = http_build_query(['data' => $request->getBody()->getContents()]); 
$defaults = array( 
    CURLOPT_URL => $request->getUri()->getUriString(), 
    CURLOPT_POST => true, 
    CURLOPT_POSTFIELDS => $data, 
); 
$ch = curl_init(); 
curl_setopt_array($ch, $defaults); 
$response = curl_exec($ch); 
curl_close($ch);
```

直接输出可能如下所示：

![](img/39390f6d56c5a83b28db083a8bd5185c_593_0.png)

## 另请参阅

- 由 PSR-7 编辑 Matthew Weir O’Phinney（也是 Zend Framework 1、2 和 3 的首席架构师）撰写的一篇展示示例用法的优秀文章可在 [这里](https://mmop.net/blog/2015-01-26-psr-7-by-example.html) 找到。

## 定义 PSR-7 Response 类

`Response` 类代表返回给发出原始请求的实体的出站信息。HTTP 头部在此上下文中起着重要作用，因为我们需要知道客户端请求的格式，通常位于传入的 `Accept` 头部中。然后，我们需要在 `Response` 类中设置适当的 `Content-Type` 头部以匹配该格式。否则，响应的实际主体将是已请求（并交付）的 HTML、JSON 或其他任何内容。

### 实现方法...

1. `Response` 类实际上比 `Request` 类更容易实现，因为我们只关心将响应从服务器返回给客户端。此外，它继承自我们的 `Application\MiddleWare\Message` 类，该类已完成大部分工作。因此，剩下要做的只是定义一个 `Application\MiddleWare\Response` 类。请注意，唯一的独特属性是 `$statusCode`：

```php
namespace Application\MiddleWare;
use Psr\Http\Message\{ Constants, ResponseInterface, StreamInterface };
class Response extends Message implements ResponseInterface
{
    protected $statusCode;
```

2. 构造函数未由 PSR-7 定义，但为了方便，我们提供了它，允许开发人员创建包含所有完整部分的 `Response` 实例。我们使用 `Message` 的方法和 `Constants` 类的常量来验证参数：

```php
public function __construct($statusCode = NULL,
    StreamInterface $body = NULL,
    $headers = NULL,
    $version = NULL)
{
    $this->body = $body;
    $this->status['code'] = $statusCode ?? Constants::DEFAULT_STATUS_CODE;
    $this->status['reason'] =
```




## 定义 PSR-7 类

```php
Constants::STATUS_CODES[$statusCode] ?? '';
$this->httpHeaders = $headers;
$this->version = $this->onlyVersion($version);
if ($statusCode) $this->setStatusCode();
}
```

- 我们提供了一种便捷的方式来设置 HTTP 状态码，而无需关心任何头部，使用 `http_response_code()` 函数，该函数从 PHP 5.4 开始可用。由于这项工作在 PHP 7 上进行，我们可以确信该方法是存在的：
  ```php
  public function setStatusCode()
  {
      http_response_code($this->getStatusCode());
  }
  ```

- 否则，使用以下方法获取状态码也是很有意义的：
  ```php
  public function getStatusCode()
  {
      return $this->status['code'];
  }
  ```

- 与前面食谱中讨论的其他基于 PSR-7 的类一样，我们还定义了一个 `with` 方法，用于设置状态码并返回当前实例。注意使用 STATUS_CODES 来确认其存在性：
  ```php
  public function withStatus($statusCode, $reasonPhrase = '')
  {
      if (!isset(Constants::STATUS_CODES[$statusCode])) {
          throw new InvalidArgumentException(
              Constants::ERROR_INVALID_STATUS);
      }
      $this->status['code'] = $statusCode;
      $this->status['reason'] = ($reasonPhrase
          ? Constants::STATUS_CODES[$statusCode] : NULL);
      $this->setStatusCode();
      return $this;
  }
  ```

- 最后，我们定义了一个方法，返回 HTTP 状态的原因，即一段简短的文本短语，在本例中基于 RFC 7231。注意使用了 PHP 7 的空合并运算符 `??`，它返回三个可能选项中的第一个非空项：
  ```php
  public function getReasonPhrase()
  {
      return $this->status['reason']
          ?? Constants::STATUS_CODES[$this->status['code']]
          ?? '';
  }
  ```

## 工作原理...

首先，务必定义前两个食谱中讨论的类。之后，你可以创建另一个简单的服务器程序，`chap_09_middleware_server_with_response.php`，该程序设置自动加载并使用相应的类：

```php
<?php
require __DIR__ . '/../Application/Autoload/Loader.php';
Application\Autoload\Loader::init(__DIR__ . '/../');
use Application\MiddleWare\{ Constants, ServerRequest, Response, Stream };
```

然后，你可以定义一个包含键/值对的数组，其中值指向当前目录中用作内容的文本文件：

```php
$data = [
    1 => 'churchill.txt',
    2 => 'gettysburg.txt',
    3 => 'star_trek.txt'
];
```

接下来，在 try...catch 块内，你可以初始化一些变量，初始化服务器请求，并设置一个临时文件名：

```php
try {
    $body['text'] = 'Initial State';
    $request = new ServerRequest();
    $request->initialize();
    $tempFile = bin2hex(random_bytes(8)) . '.txt';
    $code = 200;
```

之后，检查方法是 GET 还是 POST。如果是 GET，检查是否传入了 id 参数。如果是，返回匹配文本文件的正文。否则，返回文本文件列表：

```php
if ($request->getMethod() == Constants::METHOD_GET) {
    $id = $request->getQueryParams()['id'] ?? NULL;
    $id = (int) $id;
    if ($id && $id <= count($data)) {
        $body['text'] = file_get_contents(
            __DIR__ . '/' . $data[$id]);
    } else {
        $body['text'] = $data;
    }
```

否则，返回指示成功代码 204 和接收到的请求正文大小的响应：

```php
} elseif ($request->getMethod() == Constants::METHOD_POST) {
    $size = $request->getBody()->getSize();
    $body['text'] = $size . ' bytes of data received';
    if ($size) {
        $code = 201;
    } else {
        $code = 204;
    }
}
```

然后，你可以捕获任何异常并以状态代码 500 报告它们：

```php
} catch (Exception $e) {
    $code = 500;
    $body['text'] = 'ERROR: ' . $e->getMessage();
}
```

响应需要包装在一个流中，因此你可以将正文写入临时文件并将其创建为 Stream。你还可以将 Content-Type 头部设置为 application/json 并运行 `getHeaders()`，该方法输出当前的头部集合。之后，回显响应的正文。对于这个示例，你还可以转储响应实例以确认其是否正确构建：

```php
try {
    file_put_contents($tempFile, json_encode($body));
    $body = new Stream($tempFile);
    $header[Constants::HEADER_CONTENT_TYPE] = 'application/json';
    $response = new Response($code, $body, $header);
    $response->getHeaders();
    echo $response->getBody()->getContents() . PHP_EOL;
    var_dump($response);
```

最后，使用 Throwable 捕获任何错误或异常，并且不要忘记删除临时文件：

```php
} catch (Throwable $e) {
    echo $e->getMessage();
} finally {
    unlink($tempFile);
}
```

要测试，只需打开一个终端窗口，更改到 `/path/to/source/for/this/chapter` 目录，并运行以下命令：

```php
php -S localhost:8080
```

从浏览器中，你可以调用此程序，添加一个 id 参数。你可以考虑打开开发者工具来监控响应头部。以下是预期输出的示例。注意内容为 application/json 的内容类型：

![](img/39390f6d56c5a83b28db083a8bd5185c_598_0.png)

## 参见

- 有关 PSR 的更多信息，请访问 http://www.php-fig.org/psr/。
- 下表总结了撰写本文时 PSR-7 合规性的状态。未包含在此表中的框架要么完全不支持 PSR-7，要么缺少 PSR-7 的文档。

| 框架 | 网站 | 备注 |
| :--- | :--- | :--- |
| Slim | http://www.slimframework.com/docs/concepts/value-objects.html | 高度符合 PSR-7 |
| Laravel/Lumen | https://lumen.laravel.com/docs/5.2/requests | 高度符合 PSR-7 |
| Zend Framework 3/ Expressive | 分别参见 https://framework.zend.com/blog/2016-06-28-zend-framework-3.html 或 https://zendframework.github.io/zend-expressive/ | 高度符合 PSR-7 还使用 Diactoros 和 Straigility |
| Zend Framework 2 | https://github.com/zendframework/zend-psr7bridge | 提供 PSR-7 桥接 |
| Symfony | http://symfony.com/doc/current/cookbook/psr7.html | 提供 PSR-7 桥接 |
| Joomla | https://www.joomla.org | 有限 PSR-7 支持 |
| Cake PHP | http://mark-story.com/posts/view/psr7-bridge-for-cakephp | PSR-7 支持在路线图中，并将使用桥接方法 |

- 已经有许多可用的 PSR-7 中间件类。下表总结了一些较流行的中间件：

| 中间件 | 网站 | 备注 |
| :--- | :--- | :--- |
| Guzzle | https://github.com/guzzle/psr7 | HTTP 消息库 |
| Relay | http://relayphp.com/ | 调度器 |
| Radar | https://github.com/radarphp/Radar.Project | 动作/领域/响应器骨架 |
| NegotiationMiddleware | https://github.com/rszrama/negotiation-middleware | 内容协商 |
| psr7-csrf-middleware | https://packagist.org/packages/schnitzstabil/psr7-csrf-middleware | 跨站请求伪造防护 |
| oauth2-server | http://alexbib.ie.com/2016/04/league-oauth2-server-version-5-is-out | 支持 PSR-7 的 OAuth2 服务器 |
| zend-diactoros | https://zendframework.github.io/zend-diactoros/ | PSR-7 HTTP 消息实现 |

# 索引

## 符号

- `Saad` 参数 **480**
- `_POST` 数据
    - 过滤 **436-440**
    - 验证 **440-443**
- `_POST` 过滤器
    - 链接 **196-204**
    - 操作 **205-209**
- `_POST` 验证器
    - 链接 **210-215**
- `Stag_length` 参数 **480**
- `Stag` 参数 **480**
- `$this` 关键字
    - 参考链接 **88**
- `*AMP` 包
    - AMPPS，参考链接 **4**
    - EasyPHP，参考链接 **5**
    - MAMP，参考链接 **5**
    - WampServer，参考链接 **5**
    - XAMPP，参考链接 **4**
    - Zend Server，参考链接 **5**
- `__call()` 方法 **358**

## A

- 抽象方法 **90**
- 抽象语法树。 *参见* AST
- Accept-Language 头部
    - 参考链接 **266**
- 访问控制列表 (ACL) 机制
    - 使用中间件实现 **314-322**
- Adaptar **227**
- 高级加密标准 (AES)
    - 关于 **475**
    - 参考链接 **481**
- 备用 PHP 缓存 (APC) **336**
- Altrouter
    - 参考链接 **342**
- Amazon Mechanical Turk
    - 参考链接 **305**
- AMP **4**
- 匿名类
    - 关于 **81, 122**
    - 实现 **122-127**
- Apache、MySQL 和 PHP（还包括 Perl 和 Python）。 *参见* AMP
- API 密钥
    - 创建，参考链接 **235**
- Apple 开发者工具 **2**
- 应用程序编程接口 (API) **109, 130, 237**
- 数组
    - 创建，用于对象水合器 **392-394**
    - 数组水合器
        - 构建为对象 **395, 396**
- 断言
    - 关于 **497**
    - 参考链接 **515**
- AST
    - 关于 **26-28**
    - 参考链接 **30**
    - 操作 **28-30**
- 异步通信 **429**
- 异步 JavaScript 和 XML (AJAX)
    - 关于 **168**
    - 参考链接 **171**
- Aura.Router
    - 参考链接 **342**




## 带关联数据的认证加密 (AEAD)
480

## 权限
540

## 自动加载过程
101

## B

## 向后不兼容的变更
参考链接 23

## 二分查找
参考链接 377

### 二分查找类
构建 373-377

## 分组密码
参考链接 481

## BlowFish (BF)
475

## 浏览器数据
- 区域设置，获取 263-265

## 暴力破解攻击
- 概述 455
- 参考链接 460

## 冒泡排序
构建 368-370

## 内置 PHP Web 服务器
使用 6, 7

## C

## 缓存
用于提升性能 323-336

## Cake PHP 框架
参考链接 577

## 可调用对象
26

## CAMELLIA
475

## 图形验证码 (CAPTCHA)
- 概述 435, 461
- 参考链接 474
- 用于表单保护 461

## CAST5
475

## 密码分组链接 - 消息认证码 (CC-MAC)
477

## 类自动加载
实现 9-12

## 类
- 开发 82-88
- 扩展 88-95

## 逗号分隔值 (CSV)
44

## 完全自动化公众图灵测试以区分计算机和人
参见 图形验证码 (CAPTCHA)

## 复杂字符
转换 260-262

## Composer
参考链接 346

## composer.json 文件指令
参考链接 515

## 常量可见性
参考链接 109

## 上下文敏感分析器
- 概述 143
- 参考链接 146

## C 程序
编译，参考链接 5

## 跨站请求伪造 (CSRF)
- 概述 435, 449
- 参考链接 455

## 跨站脚本 (XSS)
444

## 密码学安全伪随机数生成器 (CSPRNG)
457

## CSPRNG
477

## 货币
- 格式化，按区域设置 271-275
- 处理，按区域设置 270

## 光标
132

## D

## 数据库
- 连接，PHP 数据对象 (PDO)
  - 使用 130-143
- 电子表格，上传到 44-47

## 数据库表
通过定义实体来表示 150-155

## 数据加密标准 (DES)
475

## 数据映射器
407

## 数据源名称 (DSN)
130

## 数据传输对象设计模式
392

## 数据类型
提示 59-62

## 日期格式
参考链接 280

## 日期/时间
格式化，按区域设置 276-279

## Debian
参考链接 3

## 解密
不使用 mcrypt 475-480

## 深度迭代
71

## 深度网页扫描器
构建 15-17

## 委托生成器
201

## 解引用过程
26

## DocBlock
82, 83

## Docker
参考链接 5

## Doctrine
参考链接 428

## 领域模型
- 概述 150
- 参考链接 155

## E

## 表情符号 (emoji)
- 编码，参考链接 260
- 使用，在视图脚本中 258-260

## 表情 (emoticons)
使用，在视图脚本中 258-260

## 加密
- 操作模式，参考链接 481
- 不使用 mcrypt 475-480

## 实体
定义以匹配数据库表 150-155

## 实体类
- 概述 150
- 与 RDBMS 查询链接 155-162

## 错误，配置阶段
- 概述 2, 3
- 参考链接 2, 3

## 可扩展标记语言 (XML)
223

## F

## FastRoute
参考链接 342

## Fedora / Red Hat
参考链接 4

## 获取模式
132

## fetchObject()
参考链接 163

## filter_input_array()
参考链接 209

## 过滤器
参考链接 209

## 流式接口
415

## 字体保护
参考链接 475

## foreach() 处理
差异 32-35

## 表单工厂
实现 190-195

## 表单
- 保护，使用 CAPTCHA 461
- 安全，使用令牌 449-455
- 验证，连接 215-221

### 表单保护
- CAPTCHA，使用 461
- 图像 CAPTCHA，生成 465-474
- 文本 CAPTCHA，生成 461-464

## 函数式编程
53

## 函数
- 概述 53
- 最佳实践 56
- 开发 54-58

## G

## 生成器
- 概述 75
- 用于编写自定义迭代器 75-78

## 通用表单元素生成器
- 创建 174-179
- 工作原理 179, 180

## 获取器 (getter)
- 概述 356
- 使用 356-361

## H

## gettext
- 避免在翻译中使用 297-305
- 参考链接 305

## glob() 函数
47

## GNU 编译器集合 (GCC)
2

## GNU 项目
2

## Google 翻译 API
- 参考链接 305

## 组使用特性
101, 104

## heredoc
259

## 主机
541

## HTML 国际化日历生成器
- 创建 280-283
- 细化国际化输出 284-288

## HTML 单选元素生成器
- 创建 181-185

## HTML 选择元素生成器
- 创建 185-190

## HTTP PUT
- 参考链接 237

## HTTP 状态码
- 参考链接 540

## 水合器
151

## 水合器模式
392

## 超文本传输协议 (HTTP)
227

## I

## 改进
- 死重，参考链接 41
- 快速参数解析，参考链接 40
- PHP NG，参考链接 40

## 初始化向量 (IV)
476

## 接口
- 使用 109-115, 484-488

## 跨框架系统调用
- 执行 342-350

## 国际组件 Unicode (ICU)
- 参考链接 270

## 国际化 (I18n)
263

## 国际标准化组织 (ISO)
- 参考链接 276

## 互联网工程任务组 (IETF)
307

## IntlCalendar 字段常量
- 参考链接 297

## 迭代器
67-74

## J

## JavaScript 对象表示法 (JSON)
498

## Joomla! 安装
- 修改 346

## jQuery
- 参考链接 171

## jQuery DataTables
- 概述 168
- 参考链接 171

## jQuery DataTables PHP 查询
- 实现 168-171

## L

## Laravel/Lumen 框架
- 参考链接 577

## 先进先出 (LIFO)
371

## 延迟静态绑定
- 概述 97
- 参考链接 100

## LimitIterator 类
- 参考链接 150

## 链表
- 概述 368
- 实现 362-367
- 参考链接 367

## 区域设置
- 概述 257
- 货币，按此处理 270-275
- 日期/时间，按此格式化 276-279
- 数字，按此格式化 266-270
- 获取，来自浏览器数据 263-265

## M

## 魔术方法
357

## 映射器
- 定义 407-417

## 大规模文件
- 遍历 41-44

## mcrypt
- 在解密中避免使用 475-479
- 在加密中避免使用 475-479
- 参考链接 481

## 方法
- 概述 82
- 使用 96-100

## 中间件
- 概述 307
- 用于认证 308-314
- 用于跨语言 350-353
- 用于实现访问控制列表 (ACL) 机制 314-322

## MinGW
- 概述 2
- 参考链接 5

## 模拟类
504

## 操作模式
476

## 模式
- 密码分组链接 (CBC) 476
- 密码反馈 (CFB) 476
- 计数器 (CTR) 477
- 带 CBC-MAC 的计数器 (CCM) 477
- 电子代码本 (ECB) 476
- 高斯/计数器模式 (GM) 477
- 输出反馈 (OFB) 477
- XTS 477

## msgid (消息 ID)
构建 298

## msgstr (消息字符串)
298

## 多维数组
显示 384-390

## MySQL 数据库
130

## N

## 命名占位符
139

## 命名空间
使用 100-104

## 命名冲突
112

## NGINX Web 服务器
参考链接 342

## 可空类型
- 概述 63
- 参考链接 67

## 空合并运算符 (??)
77

## 数字
格式化，按区域设置 266-270

## O

## 对象
构建为数组水合器 395, 396

## 对象水合器
数组，创建 392-394

## 面向对象编程 (OOP)
9, 391

## 对象关系映射
- 预加载所有子信息 418-422
- 实现 418
- 嵌入二级查找 423-428

## 观察者
434

## oclHashcat
参考链接 460

## OOP SQL 查询构建器
构建 143-146

## OpenSUSE
参考链接 4

## 操作系统平台
安全考虑，参考链接 5

## 自定义迭代器
使用生成器编写 75-78

## P

## 分页
- 概述 146
- 处理 146-150

## 参数
54

## 解析
差异 30-32

## 密码破解方法
参考链接 460

## 路径
542

## 性能
- 通过缓存改进 323-336
- 通过 PHP 7 增强功能改进 36-40

## 个人软件包存档 (PPA)
安全考虑，参考链接 5

## phar (PHP 存档) 文件
497

## PHP
转换为 XML 223-226

## PHP 5 到 PHP 7 代码转换器
创建 18-23

## PHP 7
- AMP 包，安装 4, 5
- 概述 257
- 获取，方式 1
- 安装考虑 2
- 安装，直接从源代码 2, 3
- 安装，从预编译二进制文件 3, 4

## php7cookbook.sql 文件
参考链接 8

## PHP 7 增强功能
用于改进性能 36-40

## PHP 存档
8

## PHP 数据对象 (PDO)
- 概述 129
- PDO 类 130
- PDODriver 类 130
- PDOException 类 130
- PDOStatement 类 130
- 预定义常量，参考链接 143
- 参考链接 143
- 用于连接数据库 130

## phpDocumentor
参考链接 255

## PHP 框架互操作性组 (PHP-FIG)
342

## php.ini 会话指令
参考链接 532

## PHP Locale 类
参考链接 266

## PHP NG (下一代)
40

## PHP RFC
参考链接 480

## PHP 会话
保护 443-449

## PHP 标准推荐第 7 号
参见 PSR-7

## PHP 流
参考链接 557

## PHPUnit
- 概述 497
- 安装 8
- 参考链接 8, 497

## PHPUnit 测试套件
参考链接 518

## 端口
541

## 位置占位符
139

## POST
参考链接 237

## PostgreSQL
131

## 预编译二进制文件
3

## 属性
82

## PSR
参考链接 557-576

## PSR-6
参考链接 336

## PSR-7
- 概述 307, 537
- 接口，参考链接 554
- 参考链接 538
- Request 类，开发 557-572
- Response 类，定义 572-576
- 值对象类，实现 537-557

## PSR-7 中间件类
- Guzzle，参考链接 577
- NegotiationMiddleware，参考链接 577
- oauth2-server，参考链接 577
- psr7-csrf-middleware，参考链接 577
- Radar，参考链接 577
- Relay，参考链接 577
- zend-diactoros，参考链接 577

## 发布/订阅设计模式
- 概述 429
- 实现 429-434
- 参考链接 434

## Q

## 查询结果
嵌入二级查找 164-167

## R

## 彩虹表
455

## RDBMS 查询
实体类，链接到 155-163

## 定期事件生成器
构建 289-296

## 递归
55

## 递归目录迭代器
47-51

## 递归迭代器
71





## R

- 关系型数据库管理系统 (RDBMS)
    - 相关内容 130
    - 参考链接 163
- 关系模型
    - 相关内容 156
    - 参考链接 163
- 存储库 (repository) 156
- 表述性状态转移 (REST) 223
- Request 类，PSR-7
    - 相关内容 557
    - 开发 557-572
- 解析运算符 (resolution operator) 98
- Response 类，PSR-7
    - 定义 572-576
    - 参考链接 572
- REST 客户端
    - 创建 227-230
    - 基于 cURL 的 REST 客户端，定义 233, 234
    - 基于流的 REST 客户端
        - 创建 231, 232
    - 使用 235
- REST 服务器
    - 创建 237-244
    - 使用 245, 246
- 返回类型声明
    - 参考链接 66
- 返回值数据类型
    - 参考链接 66
    - 使用 63-66
- RFC
    - 参考链接 36
- Rivest 密码算法 (RC) 475
- Ron 的代码 475
- 根区域代码 (root locale code) 264
- 路由
    - 相关内容 336
    - 实现 336-341

## S

- 标量 59
- 标量类型提示
    - 参考链接 63
- scheme 540
- 可滚动游标 135
- 搜索引擎
    - 实现 377-383
- 搜索引擎优化 (SEO) 336
- 二级查找 (secondary lookups)
    - 嵌入到查询结果中 164-167
- 安全密码生成器
    - 构建 455-460
- SEED 475
- 会话劫持
    - 参考链接 449
- 与 session 相关的 php.ini 指令
    - 参考链接 535
- 会话 (sessions)
    - 使用 session_start 自定义
        - 参数 531-535
- session_start 参数
    - 用于自定义会话 531-535
- set_exception_handler() 函数
    - 参考链接 493
- setlocale()
    - 参考链接 270
-  setter
    - 相关内容 356
    - 使用 356-360
- 浅层遍历 71
- 简单测试
    - 使用匿名类作为模拟
        - 对象 507, 508
    - 断言测试操作 514
    - 测试数据库模型类 502-512
    - 使用 Mock Builder 508, 509
    - 使用模拟类 504-513
    - 运行 499-511
    - 编写 497, 498
- 单例模式 (Singleton) 10
- Slim 框架
    - 参考链接 577
- SOAP 客户端
    - 创建 247, 248
    - 使用 249, 250
- SOAP 服务器
    - 创建 250-255
- SOAP 服务
    - 参考链接 226
- 软件设计模式 391
-  spaceship 运算符 375
- 电子表格
    - 上传到数据库 44-47
- SQL 注入 134
- SQLite 131
- 栈
    - 相关内容 371
    - 实现 371, 372
- 标准 PHP 库 (SPL) 11, 42, 429
- 静态属性
    - 相关内容 97-100
    - 使用 96
- 策略模式
    - 实现 397-406
- 流 (Streams)
    - 相关内容 231
    - 参考链接 237
- 结构化查询语言 (SQL) 129
- 子生成器 201
- Symfony 框架
    - 参考链接 577
- Synaptic 3

## T

- 测试 MySQL 数据库
    - 定义 7, 8
    - 参考链接 7
- 测试套件
    - 相关内容 515
    - 编写 515-518
- 线程安全
    - 与非线程安全对比 3
- 令牌
    - 用于保护表单 449-455
- 合计
    - 累加 384-390
- 特性 (traits)
    - 使用 115-121, 484-488
- 翻译
    - 不使用 gettext 处理 297-305
- 遍历 67
- TreeRoute
    - 参考链接 342
- Turbo C 编译器 2
- 类型提示 59, 186

## U

- Ubuntu
    - 参考链接 4
- Unicode 转义语法 257
- 统一资源标识符 (URI)
    - 参考链接 540
- 统一变量语法
    - 参考链接 32
- 单元测试
    - 相关内容 497
    - 参考链接 515
- 通用错误处理程序
    - 使用 493-496
- 通用异常处理程序
    - 使用 489-493
- URL 重写 336
- 用户信息 541
- UTF-8 12

## V

- Vagrant
    - 参考链接 5
- 验证
    - 与过滤的区别 197
    - 连接到表单 215-220
- PSR-7 值对象类
    - 实现 537-557
    - 参考链接 554
- 视图脚本
    - 使用 emoji 258-260
    - 使用 emoticons 258-260
- 可见性
    - 定义 105-109
- Visual Studio 2

## W

- Web 服务定义语言 (WSDL) 226, 247
- 网站
    - 悬停效果 12-14
- 网站漏洞
    - 参考链接 449
- Windows
    - 参考链接 3
- 万维网 (WWW) 16

## X

- Xcode IDE 2
- XLS 276
- XML
    - 相关内容 276
    - 转换为 PHP 223-226

## Y

- YaST 4

## Z

- Zend Expressive 345
- Zend Framework 3/Expressive 框架
    - 参考链接 577
- 零配置数据
    - 参考链接 171

