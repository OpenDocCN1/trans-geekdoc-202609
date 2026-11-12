# PHP 宝典 第 I 卷：基础






## 关于作者

Harry 是一名技术作家、程序员和系统工程师。他于 1994 年开始在企业 IT 部门工作，拥有物理学学士学位。他最初在 1999 年构建一个小型内联网时接触到 PHP。如今，他是一家企业外联网的首席开发人员，PHP 在提供众多后台系统的统一平台方面发挥着重要作用。

在业余时间，他为 SitePoint 撰写技术文章并运营 phpPatterns (http://www.phppatterns.com/)，该网站探索 PHP 应用程序设计。

Harry 最初来自英国，如今居住在瑞士。5 月，Harry 成为了一名美丽女婴的骄傲父亲，这让他白天黑夜都忙个不停！

## 关于 SitePoint

SitePoint 专注于为 Web 专业人士出版有趣、实用且易于理解的内容。访问 http://www.sitepoint.com/ 以获取我们的书籍、简报、文章和社区论坛。

献给 Natalie 和 Masha

## 前言

PHP 最大的优点之一是其充满活力且活跃的社区。开发者享有许多线上交流场所，包括 SitePoint Forums[1]，开发者聚集于此，共同解决日常工作中遇到的问题，从 PHP 的基础工作原理，到解决诸如“我该如何验证表单？”之类的设计问题。作为获取帮助的方式，这些社区非常出色——它们充斥着让你的项目成功所需的各种关键片段。但将所有这些知识整合成适用于你特定情况的解决方案可能是个问题。通常，社区成员假设其他发帖者具备一定程度的知识；你常常需要花费大量时间，从各种帖子、线程和用户（每个人的编程风格都不同）中汇总代码片段，才能获得完整的画面。

_《PHP 精选集》_首先，是一本汇编集，收录了 SitePoint Forums 上经常出现的常见 PHP 问题的最佳解决方案，并结合了我过去四年来每天使用 PHP 工作所获得的经验和见解。

这本书与其他 PHP 书籍略有不同之处在于，它摒弃了教程风格，而是致力于以最小的努力实现实际目标。因此，你应该能够以多少带点“即插即用”的方式使用这里提供的许多解决方案，而不必从头到尾阅读此书。

话虽如此，这些讨论中贯穿着一个“隐藏议程”。除了提供解决方案外，本书还旨在向你介绍可以节省精力的技术，并帮助你缩短完成并以后维护基于 Web 的 PHP 应用程序所需的时间。

尽管 PHP 最初被构想为一种过程式编程语言，但近年来，它作为面向对象解决方案开发的语言，已被证明越来越成功。这一趋势因 2003 年 1 月 PHP 应用程序和扩展程序库[2]（PEAR）的公开发布而进一步加强，PEAR 提供了越来越多可重用且维护良好的解决方案，用于解决全球 PHP 开发人员经常遇到的架构问题（例如 Web 表单生成和验证）。

面向对象范式似乎让许多 PHP 开发人员望而生畏，并且通常被认为只有 PHP 大师才能触及。本书将向你展示，你不需要计算机科学学位也能充分利用 PHP 当今可用的丰富类库。在开发本书提供的解决方案时，只要有可能，我都使用了我个人觉得非常实用的免费可用库，这些库为我节省了许多开发时间。使用他人开发的类通常与使用 PHP 提供的任何内置函数一样容易。

本书强调利用可重用组件构建 PHP Web 应用程序，这代表了与许多当前 PHP 相关图书关注点的又一次背离。尽管你不会找到关于面向对象应用程序设计的大量讨论，但从头到尾阅读_《PHP 精选集，第 I 卷：基础》_和_《第 II 卷：应用》_，会通过一种潜移默化的过程，帮助你将 PHP 编码技能提升到一个新水平，为你构建经得起时间考验的应用程序奠定良好基础。

_《PHP 精选集，第 I 卷：基础》_将为你提供在使用 PHP 引擎时所需的信心必备知识，包括一份 PHP 面向对象编程的快速入门（参见第 2 章）。做好这些准备后，本书将探讨可应用于几乎所有基于 PHP 的 Web 应用程序的解决方案，这些基础知识你可能已经了解，但尚未完全掌握。

## 谁应该阅读此书？

如果你已经初涉 PHP，也许读过 Kevin Yank 的 _《使用 PHP 和 MySQL 构建自己的数据库驱动网站》_（SitePoint 出版，ISBN 0-9579218-1-0），并使用 PHP 完成了你的一个或两个项目，那么这本书就是为你准备的。

拥有更多 PHP 经验的读者可能希望跳到_《PHP 精选集，第 II 卷：应用》_学习如何使用 PHP 的一些更高级功能，并在需要解释更基础概念时回到_《第 I 卷：基础》_查阅。

## 本书涵盖什么内容？

以下是你将在本卷各章节中找到的内容：

# 第 1 章：PHP 基础知识

本章概述了你在 PHP 中快速上手所需的所有基本知识，从如何使用手册，到理解 PHP 错误消息，再到包含文件的工作原理。本章还包含一些编写可移植代码的技巧，我们还将了解一些主要的 PHP 配置陷阱。

# 第 2 章：面向对象 PHP

第二章概述了 PHP 的类语法，并附有一份入门指南，解释面向对象范式的所有关键元素如何应用于 PHP。这是本文选中后续章节的必读预备材料。

# 第 3 章：PHP 与 MySQL

本章为你提供了 MySQL（PHP 最喜爱的数据库）的所有基本知识。我们从基础知识开始，涵盖如何避免 SQL 注入攻击等重要主题。接着，我们将深入探讨许多不太为人知的主题，例如 MySQL FULLTEXT 搜索功能、如何修复损坏的表并备份数据库，以及如何使用 PEAR::DB_DataObject 避免编写 SQL。本章还作为设计一个处理连接到 MySQL 数据库和查询数据库的类的“案例研究”。

# 第 4 章：文件

第四章是使用 PHP 操作文件的生存指南。在这里，我们将涵盖从访问本地文件系统，到使用 PHP 的 FTP 客户端通过网络获取文件的所有内容。接着，我们将学习如何使用 PEAR::Archive_Tar 创建自己的压缩存档。

# 第 5 章：文本操作

本章介绍了处理站点内容的基本知识。我们将讨论你不可或缺的字符串函数，以及验证和过滤用户提交内容的过程。我们将探讨如何实现 BBCode 系统，并了解防止跨站点脚本漏洞的实际操作。

# 第 6 章：日期与时间

在这里，你将学习如何在数据库中存储日期，以及如何使用 PHP 的日期函数。我们将探讨处理不同时区的细微差别，并实现一个在线日历。我们将了解在没有命令行访问权限的情况下在你的网站上运行批处理任务是多么容易，并学习如何执行简单的脚本性能测量。

# 第 7 章：图像

本章探讨缩略图的创建，以及如何在你的站点上为图像添加“水印”。我们还将讨论如何防止其他网站的热链接，以及如何使用 JpGraph 制作一些专业的图表。

# 第 8 章：电子邮件

在本章中，我们将专门探讨电子邮件相关的解决方案，向你展示如何充分利用 PHP 进行电子邮件操作。我们将学习如何借助 PHP Mailer 成功发送 HTML 电子邮件和附件，以及如何使用 PHP 轻松处理发送到 Web 服务器的来信。

# 第 9 章：Web 页面元素

本章介绍了 Web 页面和导航的基本知识，例如使用 PEAR::HTML_Table 的表格，以及实现分页结果集的过程。我们将讨论使用 PEAR::HTML_QuickForm 开发表单，深入探讨文件上传处理和导航菜单的构建。我们还将探讨一些可以与 Apache 配合使用的技巧，以生成对搜索引擎友好的 URL。

# 第 10 章：错误处理

了解 PHP 的错误报告机制，如何利用 PHP 的自定义错误处理功能，以及如何在这一内容丰富的章节中优雅地处理错误。

## 本书的网站

本书支持网站位于 http://www.sitepoint.com/books/phpant1/，将为你提供以下设施：

## 代码存档

随着你阅读本书的进展，你会注意到多次提到代码存档。这是一个可下载的 ZIP 存档，包含本书中所有示例的完整代码。

除了 PHP 脚本本身，该存档还包含若干共享库，这些库打包在 SPLIB 目录中。为了依赖这些库的脚本能按预期工作，你需要将此目录添加到 PHP 的 include_path 中（有关 include_path 的完整详细信息，请参见第 1 章中的“我如何在一个 PHP 脚本中引入另一个 PHP 脚本？”）。这样做还可以更轻松地在你自己的项目中使用这些库。





要完整了解如何安装和使用代码存档，请参阅存档中的 readme.txt 文件。

## 更新和勘误

没有一本书是完美的，我们期望细心的读者能在读完本书之前发现至少一两个错误。本书网站上的勘误页面将始终提供有关已知印刷和代码错误以及 PHP 和各种 Web 标准新版本所需更新的最新信息。

## SitePoint 论坛

如果您希望就本书与我或 SitePoint 出版团队的其他成员交流，应该加入 SitePoint 的在线社区[4]。如我上面所述，特别是 PHP 论坛[5]，可以提供本书解决方案之外的大量信息。

事实上，即使您不想与我们交谈，也应该加入那个社区，因为那里有许多有趣且经验丰富的 Web 设计师和开发人员。这是学习新事物、快速获得问题解答以及单纯娱乐的好方法。

## SitePoint 新闻通讯

除了像本书这样的图书之外，SitePoint 还发布免费电子邮件新闻通讯，包括《SitePoint Tribune》和《SitePoint Tech Times》。在其中，您将阅读有关 Web 开发各个方面的最新新闻、产品发布、趋势、提示和技术。无论如何，您都会得到有用的 PHP 文章和提示，但如果您有兴趣学习其他技术，您会发现它们特别有价值。请立即订阅一份或多份 SitePoint 新闻通讯，网址为 http://www.sitepoint.com/newsletter/——我等您！

[4] http://www.sitepointforums.com/
[5] http://www.sitepointforums.com/forumdisplay.php?forumid=34

## 您的反馈

如果您无法通过论坛找到答案，或因任何其他原因希望与我们联系，最佳写信地址是 <books@sitepoint.com>。我们设有一个配备充足人员的电子邮件支持系统来跟踪您的询问，如果我们的支持人员无法回答您的问题，他们会直接转交给我。欢迎提出改进建议，并报告您可能发现的任何错误。

## 致谢

首先，我想感谢 SitePoint 团队为使本书得以出版所做出的出色工作，感谢他们在截止日期不可避免地延后时表现出的体谅，以及他们亲切的工作作风，这使得与他们合作成为一种享受。

特别感谢 Kevin Yank，他在整个过程中提供宝贵的技术见解和紧密合作，解决了许多悬而未决的问题，并帮助使《PHP 文集》既易读又易懂。还要感谢 Julian Szemere，他频繁的反馈帮助塑造了本文集的内容，以及 Georgina Laidlaw，她设法使我一些“深夜”的时刻更加连贯。

特别感谢为 SitePoint 论坛[7]做出贡献的许多人。有一长串值得表扬的人，他们无私地分享自己在 PHP 方面的实践经验。在过去三年里，看着 PHP 论坛的发展非常有趣，从讨论 PHP 语法的基础知识，到最近探讨企业应用架构的更细微之处。总体而言，我相信 SitePoint 的 PHP 社区对使 PHP 成为一门流行且成功的技术做出了非常重大的贡献。

[7] http://www.sitepointforums.com/

最后，回到家里，我想感谢 Natalie，她一贯的耐心、爱和理解始终让我惊叹。在写本书的中途，我们的第一个孩子 Masha 出生了；同时写一本书并不总是容易的。

## PHP 基础知识

PHP 是一种专门为构建网站而设计的编程语言，它既因异常易于学习和使用而蒙福，也因此而受诅咒。入门极其简单。不久之后，典型的初学者就可以搭建一个简单的网站，并通过 HotScripts[1] 等资源尝试大量开源项目。

不幸的是，开发基于 PHP 的网站之所以容易，也意味着您可能很快就会陷入麻烦。随着网站流量的增加，以及对更多功能和更高复杂性的需求，深入了解 PHP 并研究在大型网站上已被证明成功的应用设计和技术非常重要。当然，您不能一跃成为程序员就指望立刻懂得一切。即使您能，那又有什么乐趣呢？

在本章中，我将假设您已经掌握了 PHP 的基础知识，例如 Kevin Yank 的《使用 PHP 和 MySQL 构建自己的数据库驱动网站》前几章中提供的内容（ISBN 0-9579218-1-0），并将重点放在 PHP 的“导航”要点上。

在本章中，您将了解在哪里可以获得帮助——这是对那些对您吼着“读手册！”的人的一种防御——以及如何处理代码中的错误。我们还将讨论一些保持代码可移植性的一般技巧，并为您的 PHP 谋生提供其他必需的“膳食纤维”。这里的并非所有内容都属于“基础”范畴——对于更有经验的 PHP 开发人员，也许还有一些惊喜在等着您，所以请睁大眼睛！

不过，请注意，讨论 PHP 语法并不是最令人振奋的主题——尽管它为后续章节做准备是必不可少的。如果您开始感到吃力，请记住《空前绝后》中的一句台词：在您能完成飞踢之前，必须先学会“上蜡，擦蜡”。

[1] http://www.hotscripts.com/

## 在哪里获得帮助？

PHP 是使用最广泛的 Web 脚本语言，在全球超过一千万个域名上运行[2]。作为一种完全没有企业资助的开源技术，其受欢迎程度可能看似无法解释。然而，PHP 的成功并非谜团；它拥有任何技术中最活跃、最乐于助人的在线社区之一。最近的估计表明，全球 PHP 开发人员数量约为 500,000 人，鑑于该媒介的性质，可以合理地假设其中很大一部分人在线活跃。也就是说，对于基于 PHP 的网站开发人员来说，帮助只需点击几下即可获得。

## 阅读手册

有一个广为人知的四字母缩写 RTFM（我想这里无需解释），它往往被用来骚扰计算机各个领域的初学者。虽然我能理解老手们可能不愿意一遍又一遍地重复那些文档齐全的说明，但我认为基本假设应该是我们都一开始就知道如何阅读手册。

PHP 的文档非常出色，由志愿者维护，他们将保持文档及时、易懂和相关作为唯一目标。在线版本[3]导航极其简便，并包含来自全球开发人员的注释形式的更多诀窍。手册是 PHP 真正卓越的领域之一；Sun 和 Microsoft 等软件公司在为其平台上的开发人员提供这种高质量材料方面仍有很长的路要走。

[2] http://www.php.net/usage.php
[3] http://www.php.net/manual/en/

手册也提供二十四种不同的语言版本[4]，但既然您在读本书，我假设您对手册的英文版感到满意。它分为五个主要部分，外加附录。了解可以找到什么样的信息以及在哪里找到（至少在前四个部分中，这些部分对典型的 PHP 开发人员最相关）是有价值的。

## 第一部分：入门

http://www.php.net/getting-started

本部分提供 PHP 的简短介绍，附带一些基本示例。然后解释如何安装 PHP（描述各种操作系统-Web 服务器组合），以及如何通过修改 php.ini 文件来配置它。

不容忽视的是安全性部分，它涵盖 PHP 开发人员经常犯错、使其应用程序面临滥用风险的领域。再次强调，PHP 易于使用的“代价”在于它并不总能保护您免受最严重错误的影响，因此在您的 PHP 生涯早期尽早开始学习安全性是有价值的。您将在附录 C 以及本书中相关讨论中找到关键安全问题的摘要。

## 第二部分：语言参考

http://www.php.net/langref

本部分涵盖 PHP 作为编程语言的基础知识。其中一些对于您使用 PHP 取得任何成就至关重要，而另一些在您寻找改进技巧的方法时会变得有用。一次性通读全部内容可能就像读词典一样。幸运的是，可以通过阅读网上大量的教程并研究开源 PHP 应用程序中使用的代码，来吸收语言参考中包含的大部分信息。当然，在阅读本书的过程中，我希望您能学到一些充分利用 PHP 的技巧。但是，熟悉本部分手册中包含的主题，并将其牢记在心以备将来参考，也是值得的。





## 第 III 节：功能

http://www.php.net/features

此处介绍了 PHP 的核心要素，这些要素通常专注于解决特定的 Web 相关问题。功能部分大部分内容读起来像“执行摘要”，从开发者的角度来看，当你亲眼看到这些信息在实际中运行时（例如，在本书后面将看到的示例中），可能会更好地理解其中包含的信息。

## 第 IV 节：函数参考

http://www.php.net/manual/en/funcref.php

本部分构成了手册的主体，涵盖了 PHP 中可用的所有功能方面。随着你对 PHP 的深入学习，大部分时间都将花在这里，因此你会很高兴地听说 PHP 小组已经下决心使本部分易于导航。即使是无聊时随意翻阅手册，也会对 PHP 能做的所有事情感到惊叹，这甚至很有趣。是的，我刚才把阅读手册描述为“有趣”！

函数参考被分解为多个子部分，涵盖了各种类别的函数，每个类别对应一个 PHP 扩展。

## PHP 扩展

扩展的概念一开始可能有点令人困惑，因为许多扩展都随标准 PHP 安装一起分发。字符串函数（我们几乎离不开它们）就是一个例子。一般而言，PHP 小组作为默认 PHP 安装的一部分，分发了他们认为对开发者至关重要的所有扩展。

被视为“非关键”功能（即某些开发者需要，但并非所有开发者都需要）的扩展必须单独添加。每个扩展的主页面上，重要信息出现在“安装”标题下。核心扩展通过以下句子描述：“使用这些函数无需安装；它们是 PHP 核心的一部分。”非标准扩展在附录 B 中进行了考察。

可通过搜索字段（右上角）和在“函数列表”中搜索来访问函数参考中的信息。请注意，在函数列表中搜索仅检查手册的函数参考部分。要搜索整个手册，需要在“在线文档”中搜索。

另一种便捷的导航方式是通过 URL 传递你感兴趣的主题名称来“快捷方式”到函数。例如，尝试在浏览器地址栏输入以下内容：http://www.php.net/strings。这将带你到 http://www.php.net/manual/en/ref.strings.php，即字符串扩展的主页面。查看此页面，你将看到扩展提供的所有函数列表；同一列表也可在左侧菜单中找到。

以 strpos 函数为例，输入 URL http://www.php.net/strpos（这将带你到 http://www.php.net/manual/en/function.strpos.php）。你将看到关于 strpos 函数的以下信息：

```
strpos
(PHP 3, PHP 4)
strpos -- Find position of first occurrence of a string
Description
int strpos (string haystack, string needle [, int offset])
Returns the numeric position of the first occurrence of needle in the haystack string. Unlike the strrpos(), this function can take a full string as the needle parameter and the entire string will be used.
If needle is not found, returns FALSE.
```

第一行包含函数名称，第二行列出了函数可用的 PHP 版本。第三行告诉你函数实际的作用。在此情况下，这是一个相当简略的解释，但 strpos 确实不是让人感到兴奋的主题。

在 Description 标题下，也许是所有内容中最重要的一行——函数签名。它描述了该函数接受的参数以及它返回的值。从左到右阅读，首先是 int，它告诉你函数返回的值是整数（在此情况下，是一段文本中另一段文本的位置）。接下来是函数名称本身，然后在括号中是该函数接受的参数，用逗号分隔。

让我们来看看参数 string haystack。这说明第一个参数应该是一个字符串值，而 haystack 只是为该参数命名，以便在详细描述中引用。请注意，第三个参数放在方括号内，这意味着它是可选的（即你不需要提供此参数）。

以下是使用 strpos 的示例：

```
<?php
$haystack = 'Hello World!';
$needle = 'orld';
// Use the strpos() function
$position = strpos($haystack, $needle);
echo 'The substring "' . $needle . '" in "' . $haystack . '" begins at character ' . $position;
?>
```

请注意，我使用 strpos 的方式与手册中出现的方式类似。我使用变量名 $haystack 和 $needle 来清楚地说明每个变量与手册中解释的关系，但你可以使用任何你喜欢的变量名。

函数签名约定在整个手册中始终如一地使用，因此一旦你习惯了它，就能快速掌握如何使用你未曾尝试过的函数。

## 遇到问题时获取帮助

> 如果你在 PHP 4.3.0 中使用内置函数时出错，PHP 的默认错误报告机制将显示一条错误消息，其中包含一个可直接带你进入手册的链接。

如果你有任何疑问，请务必阅读其他 PHP 开发者提交的评论，这些评论出现在手册每个页面的底部。通常，你至少会看到函数用法示例，这可能会解决你遇到的特定难题。在许多情况下，你还会找到函数的替代解释和用法，这有助于扩展你的理解。

### 进一步帮助

在手册之外，有成千上万的在线资源可供你获取进一步的帮助。我敢说，你在 PHP 中遇到的 99% 以上的常见问题都已经在某个地方得到解答，并且在线上可用。这意味着最明显（但有时被遗忘）的起点是 Google，在那里快速搜索“PHP strpos problem”会让你了解我的意思。

还有某些出色的网站，你可以直接从其他 PHP 开发者那里获得答案（当然是免费的——这是 PHP 的精神）。也许英语中最大的三个是：

- SitePoint Forums: http://www.sitepointforums.com/
- Dev Shed Forums: http://forums.devshed.com/
- phpBuilder: http://www.phpbuilder.com/board/

这些网站都使用 vBulletin [16] 来托管在线讨论，因此拥有非常友好且易于使用的界面。所有网站都有非常活跃的会员，你应该能在二十四小时内找到大多数问题的解答。

请注意，在论坛上寻求帮助时，“帮助他人帮助你”的原则很重要。不要发一条说“此脚本有问题”然后粘贴整个 PHP 脚本的消息。将问题缩小范围——确定你遇到问题的区域，并将此代码片段连同其他相关信息（如错误消息、代码目的、操作系统等）一起发布。提供帮助的人通常不想在你的问题上花费超过几分钟（毕竟他们是在免费提供帮助），所以节省他们的时间会提高你获得有用答案的机会。

不太方便，但也许是最终最有效的手段是 PHP 邮件列表 [17]，鼓励初学者使用 PHP 通用列表。这些列表可供有限浏览 [18]，不过可以使用 PHP 网站 [19] 的搜索字段搜索其中一些列表并选择你想要的列表。

[16] http://www.vbulletin.com/
[17] http://www.php.net/mailing-lists.php
[18] http://news.php.net/
[19] http://www.php.net/

Zend（开发 PHP 引擎核心的公司）也为一般 PHP 问题托管了一个相当活跃的论坛 [20]。

如果你想保证得到答案，值得调查一下 PHP Helpdesk [21]，这是由 Tap Internet [22] 运营的一项服务，该公司已与 Zend 合作提供 PHP 培训。

## 如何修复 PHP 在我的脚本中发现的错误？

你正在进行最新、最棒的脚本，一半的时候，突然一次测试执行输出了以下错误：

```
Parse error: parse error, unexpected T_ECHO, expecting ',' or ';' in c:\htdocs\sitepoint\phpbasics\2.php on line 5
```

有问题的代码如下：

```
<?php
echo 'This is some code<br />';
echo 'Somewhere in here I\'ve got a ';
echo 'parse error!<br />'
echo 'But where is it?<br />';
?>
```

你面对的被称为语法错误，作为 PHP 新手，你可能会花很多时间来追查此类问题。随着你对 PHP 变得更有经验，追踪语法错误会变得更容易。你甚至会了解自己的不良习惯，并且很可能在开始追查之前就能猜到自己犯的错误（我自己的典型缺点是在 PHP 字符串中构建 SQL 语句时忘记最后一个引号，以及在构建数组时省略逗号）。不过，熟悉 PHP 的错误消息是个好主意。

一般而言，你在 PHP 应用程序中会遇到四种基本类型的错误：

[20] http://www.zend.com/phorum/list.php?num=3
[21] http://www.phphelpdesk.com/
[22] http://www.tapinternet.com/




## 语法错误

与前面的示例一样，**语法错误**发生在您违反 PHP 语法规则时。语法错误通常会导致 PHP 输出解析错误消息。

在前面的示例中，问题本身出在第 4 行：

```
echo 'parse error!<br />'
```

我忘记在行末添加分号 (;)，而每条语句都需要分号来标记结束。PHP 解析器直到在第五行遇到另一个 echo 语句时才注意到问题，因为指令合法地可以跨越多行。这一点值得注意，因为它有时会让错误难以查找——错误可能实际上发生在 PHP 注意到问题的那一行之前。

在处理大型 if-else 或 while 语句时，语法错误尤其容易令人困惑；例如，您可能忘记添加右圆括号。也许您有一段很长的代码，中间插有 HTML 块；找到那个缺失的花括号可能极其困难。但是，随着您编码技巧的提高，并开始利用类，将代码分割为代码简短、易于阅读的独立块，您会发现定位语法错误要容易得多。

还需要注意的一点是 PHP 对 **标记（tokens）** 的使用。在上面的错误消息中，PHP 抱怨遇到了“意外的 T_ECHO”。T_ECHO 是代表 PHP 脚本中 echo 语句的标记。PHP 解析器将代码拆分为标记，以便分析和处理脚本。您在解析错误中看到的一些标记比其他标记不那么明显，因此如果您不确定，值得查看有关标记的手册[23]。

如果您使用的是 PHP 4.3.0，您会发现它包含所谓的 tokenizer 扩展[24]，它允许您以 PHP 解析器的视角查看脚本。出于兴趣，以下是查看 tokenizer 输出的方法：

```php
<?php
/* Note: This script will only work with PHP 4.3.0 or later */
// Read a PHP script as a string
$script = file_get_contents('2.php');

// Fetch the tokens into an array
$tokens = token_get_all($script);

// Display
echo '<pre>';
print_r($tokens);
echo '</pre>';
?>
```

- [23] http://www.php.net/tokens
- [24] http://www.php.net/tokenizer

## 语义错误

当您编写符合 PHP 语法规则的代码，但在执行时却违反了 PHP 的“运行时规则”时，就会发生语义错误。例如，foreach 语句期望您传入一个数组：

```php
<?php
$variable = 'This is not an array';

foreach ($variable as $key => $value) {
    echo $key . ' : ' . $value;
}
?>
```

因为 $variable 不是数组，该脚本会生成以下错误消息：

```
Warning: Invalid argument supplied for foreach() in
c:\htdocs\sitepoint\phpbasics\3.php on line 4
```

语义错误通常会生成像这样的一条 Warning 错误消息。

## 环境错误

当外部于 PHP 脚本的系统导致问题时，就会发生环境错误。例如，在您的 PHP 脚本尝试连接 MySQL 服务器时，该服务器可能已宕机。也许您指定了要打开的文件的错误路径，因此 PHP 无法找到该文件。

当将在一个系统上编写的 PHP 脚本在另一个环境不同的系统上执行时，也会出现这些错误。问题可能仅仅是 Web 服务器的底层目录结构或域名不同。处理这类问题的常见做法是创建一个中央配置脚本来存储所有这些环境变量。

php.ini 中还有许多设置，可能导致脚本在设置不同的其他系统上失败。我将在“如何编写可移植的 PHP 代码？”中介绍这些设置；附录 A 中也有汇总信息。

## 逻辑错误

**逻辑错误**是指应用程序在 PHP 引擎层面运行完全正常，但代码执行的操作与您原本意图不符的情况。例如，假设您有一个邮件脚本，想用它向在线论坛的几名成员发送同一条消息。令您惊恐的是，执行脚本后您发现已向整个论坛成员发送了邮件……整整二十次！

这类问题是最难找到的；Windows XP 用户对 Windows 更新再熟悉不过了——甚至大公司也会为逻辑错误所困。

查找逻辑错误的关键在于，您能够在与“生产”Web 服务器分离的安全环境中严格测试代码。幸运的是，PHP 及相关技术（如 Apache 和 MySQL，如果您使用它们）是跨平台的，即使底层操作系统不同，也能轻松搭建有效的开发环境。

您还应研究 **单元测试**，它是 **极限编程（XP）** 的一个方面，相关介绍可在第 II 卷第 6 章中找到。我还在本章末尾推荐了进一步阅读材料。

在第 10 章中，我将探讨处理错误本身的策略，特别是环境错误。具体而言，我们将讨论如何记录（或捕获）错误以供您分析，而不必向您的应用程序显示难看的消息。

## 如何在一个 PHP 脚本中包含另一个 PHP 脚本？

发现编写数千行的脚本可能不是保持条理的最佳方式后，您可能正在寻找将代码拆分到单独文件中的方法。也许在使用他人开源应用程序时，您发现自己正努力消除如下所示的错误消息：

> 致命错误：无法打开所需的 'script.php'

### 相互包含

PHP 提供了四个命令，允许您将一个 PHP 脚本的内容添加到另一个脚本中，即 include、require、include_once 和 require_once。在每种情况下，PHP 都会获取命令中指定的文件，然后执行其内容。include 与 require 之间的区别在于，当它们无法找到被指示获取的脚本时的行为方式不同。

include 会生成如下所示的 PHP 警告消息：

> 警告：无法打开 'script.php' 以进行包含

这将允许调用 include 命令的脚本继续执行。

相比之下，require 会导致像上面所示的致命错误，这意味着调用脚本将终止，一切都将停止。如果所需文件对您的应用程序至关重要，脚本终止是一件非常好的事情。

include_once 和 require_once 命令与它们各自的“表亲”表现相似，但如果脚本在其他任何地方（通过这四个命令之一）已被包含或 require，则该语句将被忽略。乍一看，可能不明显这些命令如何使用；您肯定知道自己使用过多少次 include 命令，对吧？ _once 命令极其有用的地方在于更复杂的应用程序，其中有一些 PHP 脚本包含其他 PHP 脚本，而这些脚本又包含更多 PHP 脚本。当您使用类库（我们将在第 2 章中探讨），并且这些类被许多脚本反复重用时，这一点尤为重要。一个类可能依赖于另一个类的可用性；使用 require_once 来包含所需的类可确保其始终可用，但如果该类恰巧已在其他地方使用，则不会造成问题。

为了直观展示这一切，让我们创建一个名为 include_me.php 的脚本：

```php
<?php
// include_me.php

echo 'I\'ve been included!<br />';
?>
```

每次包含此脚本时，它都会显示消息“I’ve been included!”，以便我们知道它已成功工作。

现在，让我们测试在另一个脚本中包含此文件的各种方式：

```php
<?php
// This works fine
echo '<br />Requiring Once: ';
require_once 'include_me.php';

// This works fine as well
echo '<br />Including: ';
include 'include_me.php';

// Nothing happens as file is already included
echo '<br />Including Once: ';
include_once 'include_me.php';

// This is fine
echo '<br />Requiring: ';
require 'include_me.php';

// Again nothing happens - the file is included
echo '<br />Requiring Once again: ';
require_once 'include_me.php';

// Produces a warning message as the file doesn't exist
echo '<br />Include the wrong file: ';
include 'include_wrong.php';

// Produces a fatal error and script execution halts
echo '<br />Requiring the wrong file: ';
```

require 'include_wrong.php';
// This will never be executed as we have a fatal error
echo '<br />Including again: ';
include 'include_me.php';
?>

这里是生成的输出（注意，我简化了末尾的错误消息）：

```
Requiring Once: I've been included!
Including: I've been included!
Including Once:
Requiring: I've been included!
Requiring Once again:
Include the wrong file:
Warning: Failed opening 'include_wrong.php' for inclusion
Requiring the wrong file: Fatal error: Failed opening required
'include_wrong.php'
```

请注意，这里第一次使用 include_once 没有任何效果（文件已经被包含了），稍后使用 require_once 也是如此。后来，当我尝试包含错误的文件（在本例中，是一个不存在的文件）时，会收到一条警告消息。但是，执行会继续到下一行，在那里我尝试 require 一个不存在的文件。这次，PHP 会产生一个致命错误，脚本执行停止，这意味着最后一次尝试包含文件永远不会发生。

请注意，您包含的文件不必只包含 PHP。包含的文件可以简单地只包含 HTML，而不包含任何 PHP。

## 应该使用哪个命令？

> 作为一般做法，除非存在需要其他行为的特殊情况，否则请始终使用 require_once 命令将一个文件包含到另一个文件中。当您将 PHP 类放在单独的文件中，并且一个类可能依赖于另一个类时，这一点尤其重要。有关类的完整内容，请参见第 2 章。

PHP 的四个包含命令不应与各种文件相关函数（在第 4 章中讨论）混淆；这些函数用于获取文件而不立即将其解析为 PHP 脚本，从而允许您处理其内容。

请注意，在本书中，即使使用 require 命令之一，我也会谈论“包含”文件。这是谈论 PHP 的一种常见惯例，源于早期 PHP 开拓者使用的旧编程语言。

## 路径查找

到目前为止，我只研究了包含与包含命令所在脚本位于同一目录中的文件。在实际中，您通常希望根据文件的作用将其组织到子目录中。这可能会带来很多困惑，特别是在使用第三方代码时，因为处理其他目录中的包含有多种替代方法。

首先要注意的是，所有包含都是相对于主脚本（开始执行的脚本）所在的目录计算的。例如，假设我们有三个文件位于以下位置：

/home/username/www/index.php
/home/username/www/includes/script.php
/home/username/www/another.php

首先，让我们考虑 index.php。命令 include 'includes/script.php'; 会正确包含 script.php，假设 index.php 是实际请求的文件。

但是，如果我们在 script.php 中使用以下命令会怎样：

```
include '../another.php'; // ???
```

如果 script.php 是我们正在查看的页面，此命令将正确包含 another.php。但是，如果 index.php 是我们正在查看的页面，并且它包含 script.php，则此命令会失败，因为 another.php 的位置是相对于 index.php 的位置计算的，而不是相对于 script.php。

我们有两种选择。我们可以修改 script.php，使其按如下方式包含 another.php：

```
include 'another.php';
```

或者，我们可以输入 another.php 的完整路径，如下所示：

```
include '/home/username/www/another.php';
```

这消除了关于 another.php 位置的任何疑问。

PHP 配置文件 php.ini 还包含 include_path 指令。这允许您指定可以包含文件的目录，而无需在使用包含命令之一时指定其位置。

这种方法需要谨慎使用，因为如果多个目录中存在同名的包含文件，可能会导致奇怪的结果，但它可以是解决包含相关问题的有效手段。例如，PHP 的 PEAR[25] 类库依赖于您将包含 PEAR 包含文件的目录添加到包含路径中。另请注意，在包含路径中指定太多位置并不是一个好主意，因为这会在 PHP 尝试查找代码中包含的脚本时减慢其速度。

如果您在共享托管环境中使用 Apache，可能能够使用 .htaccess 文件覆盖 include_path 的值。将文件放在要应用的目录中（它也适用于所有子目录），文件应包含类似这样的内容：

```
php_value include_path ".:/usr/local/lib/php:/home/user/phplib/"
```

也可以使用 PHP 函数 ini_set 完成相同的操作，例如：

```
ini_set('include_path', 'C:/phplib');
```

这允许在 PHP 脚本内部运行时进行更改。

有关 php.ini 值的参考，请参见附录 A。

## 如何编写可移植的 PHP 代码？

并非所有 PHP 安装都相同。取决于版本和 php.ini 中的配置设置，您的脚本可能会或可能无法在安装了 PHP 的另一台服务器上正确运行。但是，您可以采用一些一般的最佳实践，使生活更轻松，并最大限度地减少为其他服务器重写代码的需要。

## 将所有配置集中管理

对于大多数 PHP 应用程序，有必要提供描述脚本将运行的环境的信息，包括数据库用户名和密码、目录位置等。作为一般规则，请尝试将此信息的大部分保存在一个地方——甚至是一个文件中，以便在需要修改信息时，可以在一个地方完成所有修改。也就是说，在构建模块化应用程序时，您可能希望将特定“模块”本地的配置元素与模块本身一起存储，而不是集中存储。

您选择存储此信息的具体方式是个人偏好的问题。在某些情况下，值得考虑使用 XML 文件或将部分信息存储在数据库中。还值得了解 `parse_ini_file` 函数，我将在第 4 章中探讨它。

一种简单但有效的机制是将所有设置作为 PHP 常量放在单个文件中，这使得它们在应用程序中的任何函数或类中都可用。例如：

```
<?php
// Configuration settings
define('DOMAIN', 'sitepoint.com');

// In another script
echo 'The domain is ' . DOMAIN;
?>
```

不过，常量需要谨慎使用。为了使您的函数和类在其他应用程序中可重用，它们不应依赖于固定名称的常量；相反，它们应该将配置信息作为参数接受。在这种情况下，最好在集中配置文件中使用 PHP 变量，然后根据需要将其传递给函数和类。如果您查看第 3 章，在连接到 MySQL 时，我们可以识别出需要在中心位置拥有的若干变量：服务器主机名、用户名、密码和所选数据库名称。

使用我们在前一个解决方案中研究过的 require_once 命令，我们可以创建一个名为 config.php 的文件，并将其放在公共 Web 目录之外。这有助于确保没有人意外浏览到包含此关键信息的文件，从而使网站的安全性面临风险。

## 使用完整的 <?php ?> 标签

PHP 支持多种标签样式来标记 PHP 代码部分，包括短标签（< ? >）和 ASP 风格标签（< % >）。这些标签通过 php.ini 中的 short_open_tag 和 asp_tags 设置控制。虽然您可能将这些设置设为 On，但其他人可能不会。例如，短标签样式在 PHP 与 XML 文档混合时会引起问题，XML 文档使用类似这样的处理指令：

```
<?xml version="1.0"?>
```

如果我们有一个包含 PHP 和 XML 的文档，并且启用了 short_open_tag，PHP 会将 XML 处理指令 <?xml 误认为是 PHP 开始标签。

您的代码可能需要在 short_open_tags 和 asp_tags 均关闭的环境中运行。确保这一点的最佳方法是养成始终使用 <?php ?> 标签样式的习惯，否则在某个黑暗的未来，可能需要进行大量代码重写。

## register_globals 关闭

PHP 能够将传入的数据转换为原生 PHP 变量。此功能由 php.ini 中的 register_globals 设置控制。启用 register_globals 后，如果我在浏览器中访问 http://www.mysite.com/index.php?logged_in=1 这样的地址，PHP 会自动创建一个变量 $logged_in 并将其值设为 1。PHP 团队现在建议禁用此设置，因为如前示例所示，它会带来安全风险。

因此，请确保 php.ini 中包含以下代码：

```
register_globals = Off
```

这将迫使您通过特殊的预定义超全局变量（例如 $_GET['username']）来访问传入的数据，这意味着它们不会与您在脚本中创建的变量冲突。

使用 Apache 的 .htaccess 文件，可以使用以下代码实现相同的结果：

```
php_flag register_globals off
```



可以在 PHP 手册[26] 和 Kevin Yank 在 SitePoint 上的文章《使用 PHP 4.2 编写安全脚本！》[27] 中找到更多信息。

## 魔术引号

魔术引号是一项旨在帮助防止 PHP 初学者开发的网站出现安全漏洞的功能。

它会在你的脚本能够访问这些值之前，自动为传入的 URL 查询字符串、表单提交和 Cookie 数据添加转义字符（有关更多信息，请参见第 5 章）。

如果你直接将数据插入数据库，只要启用了魔术引号功能，就没有人能篡改数据库的风险。

对初学者来说，这无疑是预防灾难的有用方法。但是，一旦你了解什么是 SQL 注入攻击，并在代码中养成处理它们的习惯，魔术引号功能可能会弊大于利。

魔术引号功能由 PHP 配置设置 magic_quotes_gpc 控制，该设置可以是 on 或 off。

我个人始终倾向于关闭魔术引号，并亲自处理 SQL 语句的数据转义。不幸的是，这意味着我编写的代码在魔术引号已启用的 PHP 安装中移植性较差（我的内容中会出现反斜杠）。幸运的是，为了解决这个问题，PHP 提供了 get_magic_quotes_gpc 函数，可用于检查魔术引号是否已启用。为了保持本书中代码的可移植性，我们将使用一个简单的文件，在启用该功能时剥离魔术引号：

```
<?php
/**
 * Checks for magic_quotes_gpc = On and strips them from incoming
 * requests if necessary
 */
if (get_magic_quotes_gpc()) {
    $_GET    = array_map('stripslashes', $_GET);
    $_POST   = array_map('stripslashes', $_POST);
    $_COOKIE = array_map('stripslashes', $_COOKIE);
}
?>
```

[26] http://www.php.net/registerglobals
[27] http://www.sitepoint.com/article/758

如果在接受查询字符串、表单提交或 Cookie 数据的任何文件开头包含此代码，则会在启用魔术引号功能时删除其添加的任何斜杠。这实际上让我们得到了最初的内容。

第 3 章中详细讨论了 SQL 注入攻击的主题：“如何解决由引号/撇号引起的数据库错误？”。如果你还不确定自己能否防范 SQL 注入攻击，请使用魔术引号。一旦你完全掌握所有问题，请关闭魔术引号功能，这能让你免去许多麻烦。请注意，魔术引号只能通过 php.ini 文件或 Apache 的 .htaccess 文件之一进行开启或关闭。有关更多信息，请参见附录 A。

## 调用时按引用传递（Call-Time Pass-By-Reference）已关闭

引用类似于变量值的“快捷方式”。当我们使用 PHP 函数和类时，经常需要用到引用，我们将在第 2 章进一步讨论这一主题。在调用函数或类方法时使用对变量的引用，被称为调用时按引用传递。请看此示例：

```
$result = myFunction(&$myVariable);
```

在这里，& 运算符告诉 PHP 将变量 $myVariable 的引用用作参数，而不是创建其值的副本。这现在通常被视为不良做法，因为它会让理解他人代码的工作变得极其困难。

使用以下命令在 php.ini 中将其关闭：

```
allow_call_time_pass_reference = Off
```

或者，按以下方式在 .htaccess 文件中将其关闭：

```
php_flag allow_call_time_pass_reference off
```

## 编写可复用代码

我说起来容易，但如果你发现自己编写的 PHP 脚本超过一个，就需要开始思考如何让代码可复用，以免过早脱发。从技术角度看，这不完全算是可移植性问题，但如果你最终要在其他网站或应用程序上工作，你会很欣慰拥有可以直接插入新项目的现成代码。另外，如果你编写的代码会被其他人集成到他们网站上的现有应用程序中，那么你需要以一种不会对他们已有代码提出要求的形式来封装它。

例如，如果你的应用程序有某种用户身份验证系统，它能与他们已经使用的系统集成吗——一个已经拥有大量关联用户数据库的系统？

最好的方法是以创建可复用“组件”为目标编写 **面向对象** 代码（第 2 章的重点）。有些人认为在 PHP 中编写面向对象代码会降低应用程序性能，因此应不惜一切代价避免。他们忘记提及的是，面向对象编程能带来 **_你_** 性能的显著提升。毕竟，高效程序员的成本高于高效微处理器！

在评估代码复用潜力时，需要考虑以下几点：

- [ ] 当需求发生变化时会发生什么？
- [ ] 向代码添加新功能是否容易？
- [ ] 长时间后你还能理解代码吗？
- [ ] 你的代码能否轻松与其他应用程序集成？
- [ ] 代码中做出的假设是否适用于你在其他网站上的工作？

贯穿本书，你会发现许多提示和建议，鼓励你编写可复用代码，尽管对 PHP 应用程序设计整体的深入分析超出了本书的范围。阅读本书时，你应该对一些关键因素有所了解，以供进一步研究。作为一名经验丰富的 PHP 开发人员，你对自己的一项主要责任是：不断扩大对软件开发更深奥方面的一般知识，例如 **设计模式** 和 **企业应用架构**，以此来改进你的开发技术，更重要的是，节省自己的时间。你的知识越广泛，承接大项目时失败的风险就越低。

## 进一步阅读

- [ ] 使用 PHP 4.2 编写安全脚本！: http://www.sitepoint.com/article/758
  一篇解释在关闭 register_globals 的情况下编写脚本的重要性的教程。

- [ ] 使用 PHP 断言进行轻松（或更好！）的错误检测：http://www.sitepoint.com/article/1008

- [ ] 使用字符串：http://www.zend.com/zend/tut/using-strings.php
  Zend 对可用于处理字符串的主要函数进行了演示。

- [ ] 字符串理论：http://www.devshed.com/Server_Side/PHP/StringTheory/
  DevShed 对字符串进行了深入探讨，涉及 Posix 扩展正则表达式。

## 面向对象 PHP

面向对象范式是一种编程方法，旨在鼓励开发可维护且结构良好的应用程序。许多 PHP 程序员将面向对象编程（OOP）视为一种神秘艺术，因为 PHP 示例通常仅关注解决问题的过程式¹方法。这很遗憾，因为采用面向对象方法开发 PHP 应用程序有很多好处，也许最重要的是代码复用。一段编写良好的面向对象代码可以轻松用于解决其他项目中的相同问题；我们只需在需要时将其插入即可。越来越多的面向对象代码仓库，例如 PEAR[1] 和 PHP Classes[2]，可以让你免于花费数小时解决已被充分探索的问题，并使你能够专注于应用程序的具体细节。

¹过程式编程是非面向对象编程的名称。本书迄今所见的所有代码本质上都是过程式的。
[1] http://pear.php.net/
[2] http://www.phpclasses.org/





PHP Anthology，我会在合适的地方使用 OOP，这应该能为你提供更多可供研究的示例。特别是第二卷第七章，应该能让你了解为什么 OOP 是构建应用程序的有效方式。

实际上，学习使用 PHP 提供的对象模型要求我们实现两个目标，这两个目标通常需要同时进行：

- 你需要学习 PHP 类语法和面向对象术语。
- 你必须从过程式代码向面向对象代码完成“心智飞跃”。

第一步很简单。它是下一个解决方案的主题，后续解决方案中还会出现更多关于高级主题的示例。

第二步，“心智飞跃”，既简单又有挑战性。一旦你完成了它，你就不再会去思考单个脚本应该完成的长任务列表；相反，你会将编程视为将一组工具组合在一起，由你的脚本委派工作给这些工具。

稍微超前一点——为了让你一睹后面的内容——这里是一个任何使用 PHP 超过一周的人都应该熟悉的简单示例：连接到 MySQL 并获取一些数据。常见的过程式方法如下：

```
<?php
// Procedural Example

// Connect to MySQL
$connection = mysql_connect('localhost', 'harryf', 'secret');

// Select desired database
mysql_select_db('sitepoint', $connection);

// Perform a query selecting five articles
$sql = 'SELECT * FROM articles LIMIT 0,5';
$result = mysql_query($sql, $connection);

// Display the results
while ($row = mysql_fetch_array($result)) {
    // Display results here
}
?>
```

在上面的脚本中，我们直接调用了 PHP 的 MySQL 函数，这些函数作用于我们传递给它们的变量。这通常会使我们得到一个新变量，然后可以使用该变量进行进一步的工作。

解决相同问题的面向对象方法可能如下所示：

```
<?php
// OOP Example

// Include MySQL class
require_once 'Database/MySQL.php';

// Instantiate MySQL class, connect to MySQL and select database
$db = new MySQL('localhost', 'harryf', 'secret', 'sitepoint');

// Perform a query selecting five articles
$sql = 'SELECT * FROM articles LIMIT 0,5';
$result = $db->query($sql); // Creates a MySQLResult object

// Display the results
while ($row = $result->fetch()) {
  // Display results here
}
?>
```

使用 PHP 的 MySQL 函数处理 MySQL 的细节现已委派给一个由 **MySQL 类**创建的 **对象**（我们将在本书中频繁使用该类，它在第 3 章中构建）。虽然这个示例可能并不完全清楚地展示 OOP 的优势，考虑到代码量方面它与第一个示例非常相似，但它*确实*表明，原始脚本的某些复杂性现在由 MySQL 类来处理。

例如，我们现在不再需要执行两个步骤来连接 MySQL 服务器，然后选择数据库；相反，我们可以在创建 MySQL 对象时一次性处理这两个步骤。此外，如果我们后来希望脚本从不同的数据库（例如 PostgreSQL）获取结果，可以使用提供与 MySQL 类相同 **应用程序编程接口（API）** 的相关类——要做到这一点，我们只需更改上述示例中的一行代码。我们将在第二卷第七章中这样做。

面向对象方法在对象相互交互的情况下真正体现出其价值。我将把对此的进一步讨论留给本章中的解决方案，但这是一个重要概念。当你熟练掌握面向对象编程后，你会发现编写复杂的应用程序就像拼接乐高积木一样容易。

在本讨论中，我将偶尔介绍 **统一建模语言（UML）** 类图。UML 是一种使用图像描述面向对象程序的标准。如果你以前没有接触过 UML，请不要担心；图表与代码之间的关系不言自明。

## 面向对象 PHP 的基础是什么？

假设你对 OOP 一无所知，开始学习的最佳起点是类的基本 PHP 语法。你可以简单地将 **类** 视为函数和变量的集合。

## 阅读精妙手册

PHP 手册包含关于 OOP 的大量信息：
http://www.php.net/oop

在这里，我们将开发一个可以帮助生成 HTML 的简单示例，以演示 PHP 中类和对象的基础知识。这并非旨在成为优秀设计的示例；它只是 PHP 语法的入门。让我们先从构建网页的过程式脚本开始，然后逐渐将其转换为 PHP 类：

```
<?php
// Generates the top of the page
function addHeader($page, $title)
{
    $page .= <<<EOD
    <html>
    <head>
    <title>$title</title>
    </head>
    <body>
    <h1 align="center">$title</h1>
    EOD;
    return $page;
}
// Generates the bottom of the page
function addFooter($page, $year, $copyright)
{
    $page .= <<<EOD
<div align="center">&copy; $year $copyright</div>
</body>
</html>
EOD;
    return $page;
}

// Initialize the page variable
$page = '';

// Add the header to the page
$page = addHeader($page, 'A Procedural Script');

// Add something to the body of the page
$page .= <<<EOD
<p align="center">This page was generated with a procedural
script</p>
EOD;

// Add the footer to the page
$page = addFooter($page, date('Y'), 'Procedural Designs Inc.');

// Display the page
echo $page;
?>
```

这个示例值得注意的地方是我们第一次看到 **heredoc 语法**，这是编写 PHP 字符串的一种替代方法。不再使用引号将文本括起来，而是以 <<<EOD 和一行新行开始，以一行新行然后 EOD 结束。如果你好奇，PHP 手册[4] 可以提供更多详细信息。

这个过程式示例使用两个函数 addHeader 和 addFooter，以及一个全局变量 $page。这或许与你自己编写的过程式脚本并无太大不同；也许你在每个页面中都引入了一个包含 addHeader 和 addFooter 等函数的文件。

[4] http://www.php.net/types.string#language.types.string.syntax.heredoc

但是，我们如何将上述代码重构² 为面向对象形式呢？首先，我们需要一个类来放置 addHeader 和 addFooter 这两个函数：

```
File: 2.php (excerpt)
<?php
// Page class
class Page {
    // Generates the top of the page
    function addHeader($page, $title)
    {
        $page .= <<<EOD
<html>
<head>
<title>$title</title>
</head>
<body>
<h1 align="center">$title</h1>
EOD;
        return $page;
    }

    // Generates the bottom of the page
    function addFooter($page, $year, $copyright)
    {
        $page .= <<<EOD
<div align="center">&copy; $year $copyright</div>
</body>
</html>
EOD;
        return $page;
    }
}
```

使用 PHP 关键字 class，我们可以将 addHeader 和 addFooter 这两个函数分组到类中。放置在类中的函数称为 **成员函数**，或者更常见的是 **方法**。与普通函数不同，方法必须作为类的一部分来调用：

²重构是指在不更改代码实际功能的情况下重新组织代码的过程。这通常是为了便于未来对代码进行维护和扩展，而当前的结构可能会阻碍这些工作。

```
<?php
// Initialize the page variable
$page = '';

// Add the header to the page
$page = Page::addHeader($page, 'A Script Using Static Methods');

// Add something to the body of the page
$page .= <<<EOD
<p align="center">This page was generated with static class methods</p>
EOD;

// Add the footer to the page
$page = Page::addFooter($page, date('Y'), 'Static Designs Inc.');

// Display the page
echo $page;
?>
```

这里，我们使用 `::` 运算符调用了类方法 `addHeader` 和 `addFooter`。脚本几乎与之前相同；但是，我们不再直接调用函数，而是如下所示调用它们：

```
$page = Page::addHeader($page, 'A Script Using Static Methods');
```

虽然这并不是很大的改进，但它确实让我们可以按功能将函数收集在一起。这样我们就可以使用相同的名称调用不同的函数，每个函数分别嵌套在不同的类中。

> **静态方法**
> 
> 到目前为止，我们只是将类用作相关函数的容器。在面向对象术语中，以这种方式设计的函数称为 **静态方法**。
> 
> 实际上，与大多数方法相比，静态方法听起来有多无聊就有多无聊。在下面的章节中，我们将看到如何使用一些完整的方法来*真正*发挥你的面向对象编程能力。

## 类和对象

**类** 是对象的“蓝图”。也就是说，与你声明和使用的函数不同，类仅仅描述了一种对象的*类型*。在使用它完成有用工作之前，你需要使用一个过程创建一个 **对象**——即类的一个*实例*。




称为**实例化**。一旦你有了一个对象，就可以调用类中定义的方法。

类不仅包含函数，还可以包含变量。为了让我们上面开发的 Page 类更加有用，我们可能希望将一些变量与方法分组，然后将类实例化为对象。以下是重新设计的 Page 类代码；请继续向下阅读以了解说明：

```
<?php
// Page class
class Page {
    // Declare a class member variable
    var $page;

    // The constructor function
    function Page()
    {
        $this->page = '';
    }

    // Generates the top of the page
    function addHeader($title)
    {
        $this->page .= <<<EOD
<html>
<head>
<title>$title</title>
</head>
<body>
<h1 align="center">$title</h1>
EOD;
    }

    // Adds some more text to the page
    function addContent($content)
    {
        $this->page .= $content;
    }

    // Generates the bottom of the page
    function addFooter($year, $copyright)
    {
        $this->page .= <<<EOD
<div align="center">&copy; $year $copyright</div>
</body>
</html>
EOD;
}

// Gets the contents of the page
function get()
{
    return $this->page;
}
}
```

在本示例的这个版本中，Page 类变得更加有用。首先，我们添加了一个**成员变量**（也称为**字段**）用于存储 HTML：

```
// Declare a class member variable
var $page;
```

PHP 关键字 var 用于在类中声明变量。我们也可以在声明变量时为其赋值，但不能在声明中放置函数调用。例如：

```
// This is allowed
var $page = '';
```

```
// This is NOT allowed
var $page = strtolower('HELLO WORLD');
```

在变量声明之后，我们有一个名为**构造函数**的特殊方法。当类被实例化时，此方法会自动执行。构造函数必须始终与类同名。

## 构造函数没有返回值

构造函数不能返回任何值。它纯粹用于在类实例化时以某种方式设置对象。如果这有所帮助，可以将构造函数视为一个在设置完成后自动返回对象的函数，因此你不需要自己提供返回值。

话虽如此，如果需要，你仍然可以使用不带指定值的**return**命令立即终止构造函数。

在构造函数中，我们使用了一个特殊变量 $this：

```
    // The constructor function
    function Page()
    {
        $this->page = '';
    }
```

在任何方法（包括构造函数）中，$this 都指向方法正在运行的对象。它允许该方法访问属于该特定对象的其他方法和变量。$this 后面跟随的 ->（箭头）运算符用于指向对象中命名的属性或方法。

在上面的示例中，构造函数将一个空字符串值赋给我们在开头声明的 $page 成员变量。$this 变量的概念一开始可能会让人觉得别扭和困惑，但这是其他编程语言（如 Java[5]）采用的常见策略，用于让类成员相互交互。一旦你开始编写面向对象的 PHP 代码，你很快就会习惯它，因为类中的几乎每个方法都可能需要它。

在其他类方法中，addHeader 和 addFooter 与之前几乎相同；不过请注意，它们不再返回值。相反，它们更新对象的 $page 成员变量，正如你将看到的，这有助于简化使用该类的代码。我们还在此处使用了 addContent 方法；通过它，我们可以向页面添加更多内容（例如，我们在对象之外格式化的 HTML）。最后，我们有 get 方法，它是唯一返回值的方法。一旦我们完成页面构建，将使用它来创建 HTML。

所有这些方法都访问 $page 成员变量，这并非巧合。将 PHP 代码（方法）与其操作的数据（变量）绑定在一起的能力是面向对象编程最基本的特征。

以下是类的实际运行情况：

```
$webPage = new Page();

// Add the header to the page
$webPage->addHeader('A Page Built with an Object');

// Add something to the body of the page
$webPage->addContent("<p align=\"center\">This page was " .
"generated using an object</p>\n");

// Add the footer to the page
$webPage->addFooter(date('Y'), 'Object Designs Inc.');

// Display the page
echo $webPage->get();
?>
```

[5] http://java.sun.com/

要使用该类，我们使用 new 关键字对其进行了实例化。从类创建的对象放置在 `$webPage` 变量中。通过该变量，我们可以访问对象的所有成员，就像上面使用 `$this` 变量一样。

对 `addHeader` 方法的首次调用说明了这一点：

```
$webPage->addHeader('A Page Built with an Object');
```

只有在最后调用 `get` 方法时，我们才真正从类中得到任何返回值。我们不再需要担心传递包含页面内容的变量——类会处理所有这些。

## 避免在类中输出

![](img/5b6cdf7cf4cf53e30b19e047895dc464_53_0.png)

与使用 `get` 不同，我们本可以为 `Page` 类添加一个名为 `write` 的方法，以立即将页面代码发送到浏览器。这会使上述代码稍微简单一些，因为主脚本不需要从对象中 `get` 代码并自行 `echo` 它。我们之所以避免这样做是有原因的。

通常直接在类中输出（使用 `echo` 和 `printf` 等语句和函数）是个糟糕的主意；这样做会降低类的灵活性。允许从类中检索值，可以让你在将其发送到浏览器之前对其进行额外的转换，或者将其用于完全不同的目的（例如，将其放入电子邮件中！）。

还要注意的是，使用该类所需编写的代码行数比先前的示例更少。虽然无法通过计算代码行数来判断良好的应用程序设计，但很明显，该类使得使用它的过程式代码变得简单得多。从阅读代码的人的角度来看，即使不查看 `Page` 类的代码，目前发生的事情也已经相当清楚了。

## 理解作用域

编写几百行以上的过程式 PHP 代码，你无疑会遇到解析错误，或者更糟的是，由你意外多次使用同一个函数名或变量名而引起的神秘错误。当你包含大量文件且代码变得越来越复杂时，你可能会发现自己对这个问题变得越来越多疑。如何防止此类命名冲突发生？一种有助于解决此问题的方法是利用**作用域**来隐藏不需要的代码中的变量和函数。

作用域是你在其中定义的变量或函数与其他作用域隔离的上下文。PHP 有三种可用的作用域：**全局作用域**、**函数作用域**和**类作用域**。在任何这些作用域中定义的函数和变量都对任何其他作用域隐藏。函数作用域和类作用域是*局部*作用域，这意味着函数 X 的作用域对函数 Y 的作用域隐藏，反之亦然。

类的一大优势在于，它们让你能够在一个地方定义变量以及使用这些变量的函数，同时将函数对不相关的代码隐藏。这凸显了面向对象范式的一个关键理论要点。过程式范式主要强调函数，变量被视为几乎只是在函数调用之间存储数据的地方。面向对象范式将重点转移到变量上；函数“支撑”变量，并用于访问或修改它们。

让我们通过一个示例来探讨这一点：

```
<?php
// A global variable
$myVariable = 'Going global';

// A function declared in the global scope
function myFunction()
{
    // A variable in function scope
    $myVariable = 'Very functional';
}

// A class declared in the global scope
class MyClass {
    // A variable declared in the class scope
    var $myVariable = 'A class act';
}
```


```
// A function declared in the class scope
function myFunction()
{
    // A variable in the function (method) scope
    $myVariable = 'Methodical';
}
}
?>
```

在上述示例中，`$myVariable` 的每个声明实际上都是一个独立的变量。它们可以和谐共存而互不干扰，因为每个变量都位于独立的作用域中。同样，两个 `myFunction` 声明是两个独立的函数，它们也存在于独立的作用域中。因此，PHP 会为你保持它们所有值的独立。

当你开始在 PHP 应用程序中大量使用面向对象编程时，作用域变得很重要。由于许多类可以具有同名的方法，你可以设计独立的类来提供相同的应用程序编程接口（API）。使用这些类的脚本随后可以使用相同的方法调用，而不管用于实例化它们正在处理的对象的类是哪个。这是编写可维护代码的一种非常强大的技术。我们将在本章后面讨论多态性时更详细地探讨这一点。

## 三行代码

以下是我们可以让类更易于使用的方法：

```php
<?php
// Page class
class Page {
    // Declare a class member variable
    var $page;
    var $title;
    var $year;
    var $copyright;

    // The constructor function
    function Page($title, $year, $copyright)
    {
        // Assign values to member variables
        $this->page = '';
        $this->title = $title;
        $this->year = $year;
        $this->copyright = $copyright;

        // Call the addHeader() method
        $this->addHeader();
    }

    // Generates the top of the page
    function addHeader()
    {
    $this->page .= <<<EOD
<html>
<head>
<title>$this->title</title>
</head>
<body>
<h1 align="center">$this->title</h1>
EOD
    }

    // Adds some more text to the page
    function addContent($content)
    {
    $this->page .= $content;
    }

    // Generates the bottom of the page
    function addFooter()
    {
    $this->page .= <<<EOD
<div align="center">&copy; $this->year $this->copyright</div>
</body>
</html>
EOD;
    }

    // Gets the contents of the page
    function get()
    {
    // Keep a copy of $page with no footer
    $temp = $this->page;

    // Call the addFooter() method
    $this->addFooter();
    // Restore $page for the next call to get
    $page = $this->page;
    $this->page = $temp;
    return $page;
    }
}
```

这一次，我们修改了构造函数，使其接受页面页眉和页脚所需的所有变量。一旦将值分配给对象的成员变量，构造函数就会调用 addHeader 方法，该方法会自动构建页面的页眉：

```php
// The constructor function
function Page($title, $year, $copyright)
{
    // Assign values to member variables
    $this->page = '';
    $this->title = $title;
    $this->year = $year;
    $this->copyright = $copyright;

    // Call the addHeader() method
    $this->addHeader();
}
```

正如你所见，与成员变量一样，方法可以使用 `$this` 变量来调用。

addHeader 方法本身现在从成员变量中获取所需的数据。例如：

```php
<title>$this->title</title>
```

我们还更新了 get 方法，使其在返回 `$page` 成员变量的内容之前调用 addFooter 方法。这意味着在获取完成的页面时，页脚会自动添加。

```php
// Gets the contents of the page
function get()
{
    // Keep a copy of $page with no footer
    $temp = $this->page;

    // Call the addFooter() method
    $this->addFooter();
    // Restore $page for the next call to get
    $page = $this->page;
    $this->page = $temp;
    return $page;
}
```

为了确保可以多次调用 get 而不会向页面添加额外的页脚，花了一些工夫，但这种复杂性被整齐地隐藏在类中。

在外部使用类现在更加容易：

```php
// Instantiate the page class
$WebPage = new Page('As Easy as it Gets', date('Y'),
    'Easy Systems Inc.');

// Add something to the body of the page
$WebPage->addContent(
    "<p align=\"center\">It's so easy to use!</p>\n");

// Display the page
echo $WebPage->get();
?>
```

基本上，页面现在只需三行代码即可构建；我还可以重用此类来生成其他页面。作为 UML 图表示，Page 类如图 2.1 所示。

## 图 2.1. 作为 UML 的 Page 类

| Page |
| :--- |
| -page : 字符串 |
| -title : 字符串 |
| -year : 整数 |
| -copyright : 字符串 |
| +addHeader() : 无 |
| +addContent(in content : 字符串) : 无 |
| +addFooter() : 无 |
| +get() : 字符串 |

成员变量出现在中间区域，而方法出现在底部框中。此外，加号和减号用于向其他开发者指示类中的哪些元素是公开（+）的，哪些是私有（-）的。与 Java 等语言不同，PHP 不会对对象强制执行隐私性；³ 在上述示例中，我们本可以在主脚本中直接访问 `$page` 成员变量。因为我们希望对象在没有外部干扰的情况下处理自己的数据，因此我们在 UML 图中指示，只有带有 + 的成员才可供公开使用。带有 - 的成员纯粹用于类内部。

这就涵盖了 PHP 类语法的基础，并应该让你了解类与过程式代码的比较。凭借你所学的语法，你应该能够编写包含常用变量和函数的独立类——这项任务可以真正帮助整理代码并使其更易于维护。这是一个很好的开始，但面向对象编程的*真正*威力来自于多个对象和类共同使用。本章剩余部分将探讨 PHP 对象模型的一些更高级方面，包括引用、继承、聚合和组合。

## PHP 中的引用是如何工作的？

关于 PHP 中引用的大多数讨论都以“引用令人困惑”这样的开场白开始，这可能会增加围绕它们的神秘感。事实上，引用是一个非常容易掌握的概念，但自学 PHP 的开发者只有在开始编写面向对象应用程序时才真的需要考虑它。在此之前，你可能对 PHP 在幕后处理变量的方式一无所知。围绕引用存在的许多混淆，更多地与那些精通 C++ 或 Java 等其他语言并尝试使用 PHP 的开发者有关：特别是 Java，处理对象引用的方式几乎与 PHP 4 所采用的方法*正好相反*。

### 引用与指针

![](img/5b6cdf7cf4cf53e30b19e047895dc464_59_0.png)

熟悉 C++ 或 Java 等编译型语言的开发者应当注意，PHP 中的引用与其他语言中的指针并不类似。

*指针*包含内存中指向变量的地址，必须进行*解引用*才能检索变量的内容。

³类成员上的强制隐私约束将在 PHP 5.0 中添加。

在 PHP 中，所有变量名都会自动与内存中的值关联。使用引用允许我们将两个变量名链接到内存中的同一值，就好像变量名相同一样。然后你可以互相替换它们。

### 什么是引用？

要理解引用，我们必须先了解 PHP 在正常情况下（即不使用引用时）如何处理变量。

默认情况下，当变量被传递给其他任何东西时，PHP 会创建该变量的副本。当我说“传递”时，我指的是以下任何一种情况：

- 将变量传递给另一个变量：

```php
<?php
$color = 'blue';
$settings['color'] = $color;
?>
```

$settings['color'] 现在包含 $color 的副本。

- 将变量作为参数传递给函数：

```php
<?php
function isPrimaryColor($color)
{
    // $color is a copy
    switch ($color) {
    case 'red':
    case 'blue':
    case 'green':
    return true;
    break;
    default:
    return false;
    }
}

$color = 'blue';
if (isPrimaryColor($color)) {
    echo $Color . ' is a primary color';
} else {
    echo $Color . ' is not a primary color';
}
```



```
}
?>
```

当将 $color 传递给函数 isPrimaryColor 时，PHP 在函数内部使用原始 $color 变量的副本。

- 将变量传递给类方法时也适用同样的规则：

```php
<?php
class ColorFilter {
var $color;
function ColorFilter($color)
{
// $color is a copy
$this->color = $color;
// $this->color is a copy of a copy
}
function isPrimaryColor()
{
switch ($this->color) {
case 'red':
case 'blue':
case 'green':
return true;
break;
default:
return false;
}
}
}
$color = 'blue';
$filter = new ColorFilter($color);
if ($filter->isPrimaryColor() ) {
echo ($color.'. is a primary color');
} else {
echo ($color.'. is not a primary color');
}
?>
```

类外部的原始 $color 被传递给 ColorFilter 的构造函数。
构造函数内部的 $color 变量是传递给它的那个版本的副本。随后将其赋值给 $this->color，从而使该版本成为副本的副本。

所有这些传递变量的方式都会创建该变量值的副本；这称为 **按值传递**。

## 使用引用

要使用引用传递，需要使用引用运算符 &（and 符号）。例如：

```php
<?php
$color = 'blue';
$settings['color'] = &$color;
?>
```

$settings['color'] 现在包含对原始 $color 变量的 *引用*。

对比以下示例，第一个使用 PHP 的默认复制行为：

```php
<?php
$color = 'blue';
$settings['color'] = $color; // Makes a copy
$color = 'red'; // $color changes
echo $settings['color']; // Displays "blue"
?>
```

第二个涉及 **按引用传递**：

```php
<?php
$color = 'blue';
$settings['color'] = &$color; // Makes a reference
$color = 'red'; // $color changes
echo $settings['color']; // Displays "red"
?>
```

按引用传递使我们能够将新变量与原始源变量“关联”保留。对新变量或旧变量的任何更改都会体现在两者的值中。

目前为止，一切都好。你可能会想，“这里有什么大不易的？只要得到预期结果，PHP 是复制变量还是创建引用有什么区别？” 对于在过程式程序中传递的变量，你几乎永远不需要担心引用。然而，当涉及对象之间的交互时，如果不按引用传递对象，你可能会得到意想不到的结果。

## 引用的重要性

想象你的网站上有一个机制，允许访问者更改网站的外观和风格——一个用户“控制面板”。要实现这种功能，你很可能会编写针对一组包含“外观和风格”数据的变量的代码，以便独立于应用程序其余逻辑对其进行修改。

用类简单地表示这一点，首先，让我们看看将存储与外观和风格相关数据的类：

```php
<?php
// Look and feel contains $color and $size
class LookAndFeel {
    var $color;
    var $size;
    function LookAndFeel()
    {
        $this->color = 'white';
        $this->size = 'medium';
    }
    function getColor()
    {
        return $this->color;
    }
    function getSize()
    {
        return $this->size;
    }
    function setColor($color)
    {
        $this->color = $color;
    }
    function setSize($size)
    {
        $this->size = $size;
    }
}
```

接下来，我们有一个处理呈现输出的类：

```php
// Output deals with building content for display
class Output {
var $lookandfeel;
var $output;

// Constructor takes LookAndFeel as its argument
function Output($lookandfeel)
{
$this->lookandfeel = $lookandfeel;
}
function buildOutput()
{
$this->output = 'Color is ' . $this->lookandfeel->getColor() .
' and size is ' . $this->lookandfeel->getSize();
}
function display()
{
$this->buildOutput();
return $this->output;
}
}
```

注意 Output 类的构造函数。它将 LookAndFeel 的实例作为参数，以便稍后可以使用它来帮助构建页面的输出。我们将在本章后面讨论类之间交互的更多方式。

以下是使用这些类的方法：

```php
// Create an instance of LookAndFeel
$lookandfeel = new LookAndFeel();

// Pass it to an instance of Output
$output = new Output($lookandfeel);

// Display the output
echo $output->display();
?>
```

这将显示以下消息：

> 颜色是白色，尺寸是中等

现在，假设作为对用户控制面板中某个选项的响应，你想要对网站的外观和风格做一些更改。让我们将其付诸实施：

```php
File: 6.php (excerpt)

$lookandfeel = new LookAndFeel(); // Create a LookAndFeel
$output = new Output($lookandfeel); // Pass it to an Output

// Modify some settings
$lookandfeel->setColor('red');
$lookandfeel->setSize('large');

// Display the output
echo $output->display();
```

使用 setColor 和 setSize 方法，我们将颜色改为“red”，将大小改为“large”，对吧？其实不然。输出显示仍然显示：

> 颜色是白色，尺寸是中等

为什么？问题在于我们只将 LookAndFeel 对象的副本传递给了 $output。因此，我们对 $lookandfeel 所做的更改对 $output 用于生成显示的副本没有影响。

要解决这个问题，我们必须修改 Output 类，使其使用所给 LookAndFeel 对象的引用。我们通过更改构造函数来实现这一点：

```php
File: 7.php (excerpt)

function Output(&$lookandfeel)
{
    $this->lookandfeel = &$lookandfeel;
}
```

请注意，这里必须两次使用引用操作。这是因为变量被传递了两次——第一次传递给构造函数，第二次放入成员变量中。

做出这些更改后，显示如下：

> 颜色是红色，尺寸是大号

总而言之，按引用传递使目标变量与源变量“关联”保留，因此当一个变化时，另一个也会变化。

## 好的做法和不好的做法

使用类和对象时，每当涉及对象时，最好都使用引用。偶尔，你可能需要对数组做同样的事情，例如，当你想要在代码的不同部分对数组进行排序时。但是，在大多数情况下，普通变量不需要这种处理，仅仅是因为，当你的代码达到需要这样做的复杂程度时，（我希望！）你会将变量存储在对象中，并按引用传递完整的对象。

让我们看看你可能需要使用引用的其他情况...

```php
// Make sure $myObject is a reference to
// the variable created by the new keyword
$myObject = &new MyClass();
```

乍一看这很奇怪，但请记住，这里传递的是由 new 关键字创建的变量——即使你看不到它。引用运算符避免了 PHP 需要为将新创建的对象副本存储在 $myObject 中。

```php
class Bar {
}

class Foo {
    // Return by reference
    function &getBar()
    {
        return new Bar();
    }
}

// Instantiate Foo
$foo = &new Foo();

// Get an instance of Bar from Foo
$bar = &$foo->getBar();
```

在上面的示例中，你会注意到 Foo 类中的 getBar 方法。通过在函数名前加上引用运算符，函数返回的值将按引用传递。请注意，我们在将 getBar 的返回值赋给 $bar 时也必须使用引用运算符。当类方法将返回对象时，通常会使用这种技术。

不好的做法如下：

```php
function display($message) {
    echo $message;
}

$myMessage = 'Hello World!';

// Call time pass by reference - bad practice!
display(&$message);
```

这被称为调用时按引用传递，PHP 通过 php.ini 中的以下设置进行控制：

```ini
allow_call_time_pass_reference = Off
```

默认情况下，在较新的 PHP 版本中，上述设置应切换为 Off；PHP 的创建者不鼓励将其打开。关闭后，每次函数调用指定参数应按引用传递时，PHP 都会生成警告错误。因此，最好让该设置保持关闭。

调用时按引用传递之所以是“糟糕的做法”，是因为调用时按引用传递会使代码极难跟踪。我偶尔见过使用调用时按引用传递编写的 PHP XML 解析器——几乎不可能弄清楚发生了什么。

关于变量是按引用传递还是按值传递的“决定”，属于被调用函数，而不是调用它的代码。上述代码正确的写法如下：

```php
// Accept by reference - good practice
function display(&$message)
{
    echo $message;
}

$myMessage = 'Hello World!';

display($message);
```

## 性能问题

取决于你的应用程序规模，在使用引用时可能需要考虑一些性能问题。




在简单情况下，将一个变量复制到另一个变量时，PHP 内置的 **引用计数** 特性可防止不必要的内存使用。例如：

```php
$a = 'the quick brown fox';
$b = $a;
```

在上面的例子中，`$b` 的值不会占用额外内存，因为 PHP 内置的引用计数会隐式地将 `$b` 和 `$a` 指向内存中的同一位置，直到它们的值变得不同。这是 PHP 的内部特性，影响性能但不影响行为。我们不必太担心它。

不过，在某些情况下，使用引用 *更* 快，尤其是处理大型数组和对象时，因为无法使用 PHP 内置的引用计数，因此必须复制内容。

因此，为获得最佳性能，您应执行以下操作：

- 对于整数和字符串等简单值，应尽可能避免使用引用。
- 对于数组和对象等复杂值，应尽可能使用引用。

## 引用与 PHP 5

在 PHP 5 中，引用将不再是问题，因为 PHP 在传递对象时的默认行为将是按引用传递。如果您需要对象的副本，可以使用特殊的 `__clone` 方法来创建副本。

从本质上讲，这一变化使 PHP 与大多数面向对象编程语言（如 Java）保持一致，并肯定能大大减少围绕该主题的混淆。不过，在 PHP 5 获得广泛采用之前，了解引用的工作原理仍然很重要。

## 如何利用继承？

**继承** 是面向对象范式的基本组成部分，也是其强大功能的重要组成部分。继承是不同类之间的一种关系，其中一个类被定义为另一个类的子类或派生类。子类继承父类中定义的方法和成员变量，从而可以对父类进行“增加价值”。

查看 PHP 中继承工作原理的最简单方法是通过示例。假设我们有这个简单的类：

```php
<?php
class Hello {
    function sayHello()
    {
        return 'Hello World!';
    }
}
```

使用 extends 关键字，我们可以创建一个 Hello 的子类：

```php
class Goodbye extends Hello {
    function sayGoodbye()
    {
        return 'Goodbye World!';
    }
}
```

Goodbye 现在是 Hello 的子类。反过来说，Hello 是 Goodbye 的 **父类** 或 **超类**。现在，我们可以简单地实例化子类，并使用单个对象访问 sayHello 和 sayGoodbye 方法：

```php
$msg = &new Goodbye();
echo $msg->sayHello() . '<br />';
echo $msg->sayGoodbye() . '<br />';
?>
```

该示例展示了继承的基本工作原理，但并未体现其实际威力……这需要通过重写来实现。

## 重写

当我们在子类中定义与父类同名的函数时会发生什么？示例：

```php
<?php
class Hello {
function getMessage()
{
return 'Hello World!';
}
}

class Goodbye extends Hello {
function getMessage()
{
return 'Goodbye World!';
}
}
```

两个类都有相同的方法名 getMessage。PHP 完全接受这一点——它不会对方法被声明两次提出异议。

使用这些类时会发生以下情况：

```php
$hello = &new Hello();
echo $hello->getMessage() . '<br />';

$goodbye = &new Goodbye();
echo $goodbye->getMessage() . '<br />';
?>
```

输出如下：

```
Hello World!
Goodbye World!
```

通过 $goodbye 对象调用 getMessage 会显示 “Goodbye World！” 子类中的方法 **重写** 了父类中的方法。

您也可以让子类在内部使用父类的方法，同时对其进行重写。示例：

```php
<?php
class Hello {
function getMessage()
{
return 'Hello World!';
}
}
class Goodbye extends Hello {
function getMessage()
{
$parentMsg = parent::getMessage();
return $parentMsg . '<br />Goodbye World!';
}
}

$goodbye = &new Goodbye();
echo $goodbye->getMessage() .'<br />';
?>
```

使用 parent 关键字，我们可以调用父类的方法。

请注意，我们也可以按名称调用父类以实现完全相同的结果：

```php
class Goodbye extends Hello {
function getMessage() {
$parentMsg = Hello::getMessage();
return $parentMsg . '<br />Goodbye World!';
}
}
```

请注意，我们已将 parent 关键字替换为 Hello 类的名称。输出完全相同。但是，使用 parent 可以免去在子类中工作时记住父类名称的麻烦，并且是推荐的语法。

从非静态方法调用 parent::getMessage() 或 Hello::getMessage() 与调用静态函数不同。这是涉及继承的一种特殊情况。父类中被调用的函数仍保留对实例数据的访问权限，因此不是静态的。这可以如下演示：

```php
<?php
class A {
var $a = 1;
function printA()
{
             echo $this->a;
         }
     }
class B extends A {
    var $a = 2;
    function printA()
    {
        parent::printA();
        echo "\nWasn't that great?";
    }
}

$b = new B();
$b->printA();
?>
```

以上代码生成的输出如下：

```
2
Wasn't that great?
```

## PHP 不会级联构造函数

大多数面向对象语言（如 Java）会在运行子类中覆盖的构造函数之前，自动运行父类的构造函数。这称为级联构造函数——而 PHP 不具备此功能。

如果在子类中创建构造函数，请注意您完全覆盖了父类的构造函数，并且如果您仍希望父类处理其部分对象初始化，则必须从新构造函数中显式调用它。

覆盖声明的成员变量的方式与方法完全相同，尽管您不太可能频繁使用此功能。

## 继承实战

现在您大致了解了 PHP 中继承的用法，是时候查看一个示例，以便更好地了解如何应用继承。

以下示例为 Web 页面实现了一个简单的导航系统，生成页面顶部出现的 HTML。通过让一个类继承另一个类，在需要时可以向页面添加“面包屑”导航。

首先，StandardHeader 类负责生成页面顶部的 HTML，并提供 setHeader 和 getHeader 方法来访问存储 HTML 的变量。

```php
<?php
/**
 * A standard header for a Web page
 */
class StandardHeader {
 /**
  * The header HTML is stored here
  */
 var $Header = '';

 /**
  * The constructor, taking the name of the page
  */
 function StandardHeader($title)
 {
  $html = <<<EOD
 <html>
 <head>
  <title>$title</title>
 </head>
 <body>
  <h1>$title</h1>
 EOD;
  $this->setHeader($html);
 }

 /**
  * General method for adding to the header
  */
 function setHeader($string)
 {
  if (!empty($this->header)) {
   $this->header .= $string;
  } else {
   $this->header = $string;
  }
 }

 /**
  * Fetch the header
  */
 function getHeader()
 {
     return $this->header;
 }
}
```

现在，子类 CategoryHeader 为其父类增加了额外功能，向生成的 HTML 添加了“面包屑”链接。我们不需要重新创建 setHeader 和 getHeader 方法，因为在实例化 CategoryHeader 时，这些方法会从 StandardHeader 继承。

文件：12.php（摘录）

```php
/**
 * Subclass for dealing with Categories, building a breadcrumb
 * menu
 */
class CategoryHeader extends StandardHeader {
    /**
     * Constructor, taking the category name and the pages base URL
     */
    function CategoryHeader($category, $baseUrl)
    {
        // Call the parent constructor
        parent::StandardHeader($category);

        // Build the breadcrumbs
        $html = <<<EOD
<p><a href="{$baseUrl}">Home</a> >
        <a href="{$baseUrl}?category=$category">{$category}</a></p>
EOD;
        // Call the parent setHeader() method
        $this->setHeader($html);
    }
}
```

现在让我们使用这两个类：

文件：12.php（摘录）

```php
// Set the base URL
$baseUrl = '12.php';

// An array of valid categories
```


```php
$categories = array('PHP', 'MySQL', 'CSS');

// Check to see if we're viewing a valid category
if (isset($_GET['category']) &&
    in_array($_GET['category'], $categories)) {

    // Instantiate the subclass
    $header = new CategoryHeader($_GET['category'], $baseUrl);
} else {

    // Otherwise it's the home page. Instantiate the Parent class
    $header = new StandardHeader('Home');
}

// Display the header
echo $header->getHeader();
?>

<h2>Categories</h2>
<p><a href="?<?php echo $baseUrl; ?>?category=PHP">PHP</a></p>
<p><a href="?<?php echo $baseUrl; ?>?category=MySQL">MySQL</a></p>
<p><a href="?<?php echo $baseUrl; ?>?category=CSS">CSS</a></p>
</body>
</html>
```

如上所述，控制逻辑会查找 `$_GET['category']` 变量。如果存在，则会创建 `CategoryHeader` 的实例，显示导航以便用户能够找到返回主页的路径。但如果不存在，则会改为创建父类 `StandardHeader` 的实例，这适用于用户查看主页的情况（因此不需要面包屑导航来找到返回路径）。

换而言之，继承使我们能够添加所需的额外功能，而无需复制已存在于父类中的逻辑；现有的方法和逻辑可以通过子类复用。

继承提供了一种强大的机制，用于创建模块化的类来解决特定问题，同时仍可提供共享的方法和变量，无论我们处理的是哪个具体对象，都可以使用这些方法和变量。

## 避免深层继承结构

通常来说，使用继承构建类层次结构时，应避免超过两代。这样做通常是糟糕设计的表现，表明错过了让类以不同方式交互的机会（参见下一解决方案）。在实践中，超过两代的类往往会导致各种调试问题，并使代码难以维护。例如，很难跟踪层次结构中更高层使用的变量名。

## 对象如何交互？

除了继承之外，对象还有其他交互方式；例如，一个对象使用另一个对象。从许多方面来看，这种交互比继承更重要，面向对象范式正是在此处展现其真正威力。

一个对象使用另一个对象有两种方式：**聚合**和**组合**。

## 聚合

聚合是指一个对象将另一个对象以“临时借用”的方式交给自身。第二个对象通常会通过第一个对象的某个成员函数传递给第一个对象。随后，第一个对象可以调用第二个对象中的方法，从而为自己的目的使用第二个对象中存储的功能。

聚合的常见示例涉及数据库连接类。假设你将数据库连接类传递给另一个类，然后该类使用数据库连接类来执行查询。执行查询的类**聚合**了数据库连接类。

下面是使用 MySQL 类的简单示例（我们将在第 3 章中创建该类）：

```php
<?php
// Include the MySQL database connection class
require_once 'Database/MySQL.php';

// A class which aggregates the MySQL class
class Articles {
    var $db;
    var $result;

    // Accept an instance of the MySQL class
    function Articles(&$db)
    {
        // Assign the object to a local member variable
        $this->db = &$db;
        $this->readArticles();
    }

    function readArticles()
    {
        // Perform a query using the MySQL class
        $sql = "SELECT * FROM articles LIMIT 0,5";
        $this->result = &$this->db->query($sql);
    }

    function fetch()
    {
        return $this->result->fetch();
    }
}

// Create an instance of the MySQL class
$db = &new MySQL('localhost', 'harryf', 'secret', 'sitepoint');

// Create an instance of the Article class, passing it the MySQL
// object
$articles = &new Articles($db);
while ($row = $articles->fetch()) {
    echo '<pre>';
    print_r($row);
    echo '</pre>';
}
?>
```

在上述示例中，我们在 `Articles` 类之外实例化 `MySQL` 类，然后在实例化 `Articles` 时将其传递给 `Articles` 构造函数。随后，`Articles` 可以使用 `MySQL` 对象来执行特定查询。在此例中，`Articles` 聚合了 `MySQL` 对象。图 2.2 使用 UML 说明了这种关系。

### 图 2.2. 聚合

![](img/5b6cdf7cf4cf53e30b19e047895dc464_78_0.png)

## 组合

组合是指一个对象“完全拥有”另一个对象。也就是说，第一个对象负责创建（实例化）第二个对象。这种情况在许多场景下都很有用，但通常，当第一个对象可能是唯一需要使用第二个对象的对象时，会使用组合。

第 II 卷第 1 章中的一个示例是 `Auth` 类，它**组合**了 `Session` 类的一个实例，并在构造函数中创建它：

```php
class Auth {
    ...
    /**
     * Instance of Session class
     * @var Session
     */
    var $session;
    ...

    function Auth (&$dbConn, $redirect, $md5 = true)
    {
        $this->dbConn = &$dbConn;
        $this->redirect = $redirect;
        $this->md5 = $md5;
        $this->session = &new Session();
        $this->checkAddress();
        $this->login();
    }
}
```

由于 `Auth` 类需要读写会话变量，且应用程序中不太可能有很多其他不相关的类也需要使用 `Session`，因此由它创建自己的 `Session` 对象是合理的。

图 2.3 使用 UML 说明了本示例中的组合关系。

### 图 2.3. 组合

![](img/5b6cdf7cf4cf53e30b19e047895dc464_79_0.png)

## 分辨差异

判断对象 A 是聚合还是组合对象 B 的一般“思想实验”是问：“如果对象 A 消失，对象 B 还会存活吗？”如果对象 B 在对象 A 消失后仍然存活，则称对象 A 聚合对象 B。但如果对象 A 消失时对象 B 也随之消失，则称对象 A 组合对象 B。

从实际开发的角度来看，了解何时应用聚合或组合非常重要。

聚合的优势在于开销较低，因为单个对象会被许多其他对象共享。当然，聚合你的数据库连接类是个好主意；但如果将其与每个想要执行查询的对象组合，可能需要多个数据库连接，当你的网站吸引高流量时，这会迅速使应用程序停止响应。

组合的优势在于使类从外部使用时更加便捷。使用该类的代码无需担心向其传递所需的其他对象，在复杂应用程序中，这往往会变得棘手并导致设计上的“权宜之计”。组合还能让你确切知道哪个类可以访问被组合的对象。而在聚合中，共享被聚合对象的另一个对象可能会更改其状态，从而“破坏”该对象，使其他使用它的类无法正常工作。

## 多态

面向对象编程的另一个强大特性是多态——即不同类能够共享**接口**的能力。

接口是一个或多个方法，可让你为特定目的使用类。例如，你可以拥有两个数据库连接类——一个用于 MySQL，另一个用于 PostgreSQL。只要它们都提供查询方法，你就可以互换使用它们来在不同数据库上运行查询。查询方法是两个类共享的简单接口。

共享相同接口的类通常继承自提供常用方法的父类。再次强调，这最好通过示例来理解。

首先，我们定义一个**抽象**基类 `Message`，它提供常用方法 `getMessage`。在 `Message` 类之下，我们定义**具体**类，每个类创建特定消息。

“抽象”和“具体”这两个术语涉及类的用法，特别是类是否旨在被直接使用。抽象类是指某些功能或结构将由所有子类共享，但本身不打算直接使用的类；通常，它具有一个或多个空方法，这些方法没有任何实际用途。换句话说，你不应该从抽象类创建对象。具体类是抽象类的子类，你*可以*从中创建对象。某些语言（如 Java）在语法层面提供对抽象类的支持——这是 PHP 4 所不具备的。不过，在设计应用程序时，你仍然可以使用抽象类的*概念*，尽管你可以考虑添加文档，告知与代码协作的其他开发者该类是抽象类。

```php
<?php
class Message {
    var $message;

    function setMessage($message)
    {
        $this->message = $message;
    }

    function getMessage()
    {
        return $this->message;
    }
}
```





```
class PoliteMessage extends Message {
function PoliteMessage()
{
	$this->setMessage('How are you today?');
}
}

class TerseMessage extends Message {
function TerseMessage()
{
	$this->setMessage('Howzit?');
}
}

class RudeMessage extends Message {
function RudeMessage()
{
	$this->setMessage('You look like *&* today!');
}
}
```

Now, we define the MessageReader class, which takes an array of Message objects through its constructor.

```
class MessageReader {
var $messages;
function MessageReader(&$messages) {
	$this->messages = &$messages;
	$this->readMessages();
}
function readMessages() {
	foreach ($this->messages as $message) {
		echo $message->getMessage() . '<br />';
	}
}
}
```

这里需要注意的是，就 MessageReader 而言，“Message 对象”是指从 Message 类或其任何子类实例化的任何对象。你注意到吗，在 readMessages 方法中，我们调用了 getMessage 方法？这段代码适用于任何具有 getMessage 方法的对象——包括 Message 的任何子类。

Now, to prove the point, let’s create some `Message` objects using our three sub-classes at random:

```
$classNames =
    array('PoliteMessage', 'TerseMessage', 'RudeMessage');
$messages = array();
srand((float)microtime() * 1000000); // Prepares random shuffle
for ($i = 0; $i < 10; $i++) {
    shuffle($classNames);
    $messages[] = new $classNames[0]();
}
$messageReader = new MessageReader($messages);
?>
```

通过创建 `$classNames` 数组并反复将其打乱，我们可以获取数组的第一个元素，并使用它来创建一个新对象：

```
$messages[] = new $classNames[0]();
```

这是**可变函数**的一个示例。表达式 `$classNames[0]` 将被求值，以确定要调用的构造函数（`PoliteMessage`、`TerseMessage` 或 `RudeMessage`）的名称。

Finally, the `$messages` array contains ten messages, randomly selected, and is passed to the constructor of `MessageReader` on instantiation.

Here’s a sample result:

```
You look like *%&* today!
Howzit?
How are you today?
How are you today?
How are you today?
You look like *%&* today!
How are you today?
How are you today?
Howzit?
How are you today?
```

Each time we execute the script, the list is different.

Because all the concrete message classes share the same `getMessage` function (i.e. they implement the same interface), the `MessageReader` class is able to extract the data without knowing which particular type of message it’s dealing with. The ability for a group of related classes to work interchangeably is called polymorphism, and is illustrated in the UML diagram in Figure 2.4.

### 图 2.4. 多态性

![](img/5b6cdf7cf4cf53e30b19e047895dc464_83_0.png)

一旦你意识到面向对象编程的这一方面的价值，它就非常强大。例如，你可能拥有一组表示 HTML 标签的对象，每个都是父类 HTMLTag 的子类，从该父类继承 render 方法。另一个处理页面渲染的类可以接收一组 HTMLTag 对象，并通过调用每个对象的 render 方法来创建页面。

### 进一步阅读

- 面向对象 PHP：分页结果集：http://www.sitepoint.com/article/662
- PHP 引用详解：http://www.zez.org/article/articleview/77/
- PHP 引用
  - 第 1 部分：http://www.onlamp.com/pub/a/php/2002/08/15/php_foundations.html
  - 第 2 部分：http://www.onlamp.com/pub/a/php/2002/09/12/php_foundations.html
- PHP 引用计数和别名：
  - http://www.zend.com/zend/art/ref-count.php

# 3 PHP 与 MySQL

> “今天的网络上，内容为王。”
> ——凯文·扬克

在互联网的“旧日”里，大多数网页只不过是包含 HTML 的文本文件。当人们浏览你的网站时，你的 Web 服务器会简单地将文件提供给他们的浏览器，浏览器解析内容并渲染出人类可读的东西。这种方法起初没问题，但随着网站规模扩大，设计和导航等问题变得越来越重要，开发人员意识到维护成百上千个 HTML 文件将是一场大麻烦。为了解决这个问题，将可变内容（文章、新闻条目等）与网站的静态元素（即其设计和布局）分开变得流行起来。

使用数据库作为存储可变内容的存储库，PHP 等服务器端语言负责获取数据并将其放置在统一的“框架”内，设计和布局元素被重复使用。这意味着修改网站的整体外观和感觉可以作为与添加或维护内容分开的任务来处理。突然间，运营网站不再是一项占据开发者每一分清醒时间的任务。

PHP 支持所有值得提及的关系数据库，包括大公司中常用的 Oracle、IBM 的 DB2 和 Microsoft 的 SQL Server。两个最值得注意的开源替代方案是 PostgreSQL 和 MySQL。尽管 PostgreSQL 可以说是更好的数据库，因为它支持更多关系数据库常见的功能，但 MySQL 在 Windows 上获得更好的支持，并且是提供 PHP 支持的 Web 主机中流行的选择。这些因素结合起来，使 PHP 和 MySQL 成为非常流行的组合。本书侧重于将 MySQL 与 PHP 一起使用，但重要的是要记住，有替代方案完全支持存储过程、触发器和约束等功能，其中许多在具有复杂数据结构的应用程序中变得重要。

本章涵盖 PHP 开发人员在使用 MySQL 时需要执行的所有常见操作，从检索和修改数据到搜索和备份数据库。示例专注于使用单个表，因此此处不讨论表关系。如需完整讨论表关系，请参阅 Kevin Yank 的《使用 PHP 和 MySQL 构建自己的数据库驱动网站》（ISBN 0-9579218-1-0），或在我们处理第二卷第 1 章的用户组时查看其实践示例。

此处使用的示例使用名为 sitepoint 的示例数据库，其中包含以下单个表：

```
File: articles.sql

CREATE TABLE articles (
    article_id INT(11) NOT NULL AUTO_INCREMENT,
    title VARCHAR(255) NOT NULL DEFAULT '',
    intro TEXT NOT NULL,
    body TEXT NOT NULL,
    author VARCHAR(255) NOT NULL DEFAULT '',
    published VARCHAR(11) DEFAULT NULL,
    public ENUM('0','1') NOT NULL DEFAULT '0',
    PRIMARY KEY (article_id),
    FULLTEXT KEY art_search (title, body, author)
)
```

构建此表以及一些示例数据的查询可在代码存档中找到，包含在文件 sql/articles.sql 中。该表将在本书后续章节的示例中使用。

## 如何访问 MySQL 数据库？

使用 PHP 连接 MySQL 再简单不过了。这本质上是一个两步过程；首先连接到 MySQL 数据库服务器本身，然后告知 MySQL 要连接的数据库。

## 基本连接

以下是 MySQL 数据库连接的最简单形式：

```
File: 1.php

<?php
$host = 'localhost'; // Hostname of MySQL server
$dbUser = 'harryf'; // Username for MySQL
$dbPass = 'secret'; // Password for user
$dbName = 'sitepoint'; // Database name

// Make connection to MySQL server
if (!$dbConn = mysql_connect($host, $dbUser, $dbPass)) {
    die('Could not connect to server');
}

// Select the database
if (!mysql_select_db($dbName, $dbConn)) {
    die('Could not select database');
}

echo 'Connection successful!';
// ... some code here using MySQL

// Close the connection when finished
mysql_close($dbConn);
?>
```

重要的是要记住，MySQL 是一个独立的服务器程序，类似于 Apache。两台服务器可能运行在同一台物理计算机上（因此在上述示例中使用了 $host = 'localhost';），但也可以连接到远程计算机上的 MySQL，例如 $host = 'anothercomputer.com';。为了使事情更有趣一点，MySQL 还有自己的端口号，默认是 3306。PHP 假设 3306 是端口号，但如果你需要使用不同的端口，只需 $host = 'anothercomputer.com:4321';。

另一个概念难点在于理解单个 MySQL 服务器可以提供对许多数据库的访问，这就是为什么你需要在连接到服务器后在 PHP 中选择数据库。

回到上面的代码，有几点需要注意。首先，我将连接 MySQL 所需的值放入了变量中。这只会让我们的生活更轻松；通常将此类信息存储在单独的文件中


包含在每个 PHP 脚本中，从而可以一次更改许多脚本。稍后我们将看看可以使用哪些进一步的技巧来让生活更轻松。

mysql_connect 函数负责连接到 MySQL 服务器。它返回的值要么是 **链接标识符**（PHP 提供的用于标识连接的值），要么是 FALSE，表示连接失败。

```
if (!$dbConn = mysql_connect($host, $dbUser, $dbPass)) {
    die('Could not connect to server');
}
```

这个 if 语句会问自己：“我是否成功连接到 MySQL 服务器？” 如果没有，它使用 die 来终止脚本。

接下来，我们使用 mysql_select_db 选择了想要的数据库，采用同样的 if 语句技术：

```
if (!mysql_select_db($dbName, $dbConn)) {
```

请注意，我们将包含链接标识符的变量作为第二个参数提供给 mysql_select_db。我们通常不需要这样做（该参数是可选的），但当复杂的脚本要处理多个数据库连接时，这种方法可以帮助确保 PHP 知道你指的是哪个。

最后，我们使用 mysql_close 再次断开与服务器的连接：

```
mysql_close($dbConn);
```

这发生在脚本底部，在运行一些使用该连接的虚构 PHP 代码之后。通常关闭连接是可选的——PHP 会在脚本结束后自动关闭任何连接¹。

¹使用 mysql_pconnect 建立的连接有所不同。该函数建立与数据库的持久连接，以便多个 PHP 脚本重复使用。使用持久连接可以让脚本略快一些，因为 PHP 不再需要每次都重新连接，但速度是有代价的：如果你的网站运行在共享服务器上，持久连接可能会独占该服务器，导致其他网站有时无法连接。在这类环境中，通常要么避免使用 mysql_pconnect，要么配置 MySQL，使连接一旦不再执行任何操作就立即终止，方法是使用短连接超时值。

## 可重用代码

你刚刚看到了连接到 MySQL 最简单的方法。不过，将上述代码“打包”到函数或类中通常更有用，这样它就可以被重复使用。

作为函数，我们可以如下：

```
<?php
function &connectToDb($host, $dbUser, $dbPass, $dbName)
{
    // Make connection to MySQL server
    if (!$dbConn = @mysql_connect($host, $dbUser, $dbPass)) {
        return false;
    }

    // Select the database
    if (!@mysql_select_db($dbName)) {
        return false;
    }

    return $dbConn;
}

$host = 'localhost'; // Hostname of MySQL server
$dbUser = 'harryf'; // Username for MySQL
$dbPass = 'secret'; // Password for user
$dbName = 'sitepoint'; // Database name

$dbConn = &connectToDb($host, $dbUser, $dbPass, $dbName);
?>
```

这将连接到 MySQL 并选择数据库的过程减少为一行（如果算上 include 语句，则为两行，该语句会指向包含 connectToDb 函数的单独文件）：

```
$dbConn = &connectToDb($host, $dbUser, $dbPass, $dbName);
```

请注意，我们使用了引用运算符 &。这个运算符及其作用在第 2 章中已详细介绍。

## 做个懒人：写好代码

科学家现在已经确凿证明，PHP 知识与空闲时间成反比，但与脱发成正比。防止这些影响的唯一方法是尽早学习如何编写可扩展、可维护且可重用的代码。充分利用 PHP 中的类和面向对象是正确道路上的一大步。作为 PHP 开发者，懒惰是一种美德。

更进一步，我们可以将这段代码封装到一个类中：

文件：Database/MySQL.php（在 SPLIB 中）（节选）

```
<?php
/**
 * MySQL Database Connection Class
 * @access public
 * @package SPLIB
 */
class MySQL {
/**
 * MySQL server hostname
 * @access private
 * @var string
 */
var $host;

/**
 * MySQL username
 * @access private
 * @var string
 */
var $dbUser;

/**
 * MySQL user's password
 * @access private
 * @var string
 */
var $dbPass;

/**
 * Name of database to use
 * @access private
 * @var string
 */
var $dbName;

/**
 * MySQL Resource link identifier stored here
 * @access private
 * @var string
 */
var $dbConn;

/**
 * Stores error messages for connection errors
 * @access private
 * @var string
 */
var $ConnectError;

/**
 * MySQL constructor
 * @param string host (MySQL server hostname)
 * @param string dbUser (MySQL User Name)
 * @param string dbPass (MySQL User Password)
 * @param string dbName (Database to select)
 * @access public
 */
function MySQL($host, $dbUser, $dbPass, $dbName)
{
    $this->host = $host;
    $this->dbUser = $dbUser;
    $this->dbPass = $dbPass;
    $this->dbName = $dbName;
    $this->connectToDb();
}

/**
 * Establishes connection to MySQL and selects a database
 * @return void
 * @access private
 */
function connectToDb()
{
    // Make connection to MySQL server
    if (! $this->dbConn = @mysql_connect($this->host,
        $this->dbUser, $this->dbPass)) {
        trigger_error('Could not connect to server');
        $this->connectError = true;
    } else if (!@mysql_select_db($this->dbName, $this->dbConn)) {
        trigger_error('Could not select database');
        $this->connectError = true;
    }
}

/**
 * Checks for MySQL errors
 * @return boolean
 * @access public
 */
function isError()
{
    if ($this->connectError) {
        return true;
    }
    $error = mysql_error($this->dbConn);
    if (empty($error)) {
        return false;
    } else {
        return true;
    }
}
?>
```

这看起来可能有点令人望而生畏，但最重要的是，不是类本身是如何编写的²，而是你如何使用它。

最重要的是，连接到 MySQL 的任务现在已减少到如下：

```
<?php
 // Include the MySQL class
 require_once 'Database/MySQL.php';

 $host = 'localhost'; // Hostname of MySQL server
 $dbUser = 'harryf'; // Username for MySQL
 $dbPass = 'secret'; // Password for user
 $dbName = 'sitepoint'; // Database name

 // Connect to MySQL
 $db = new MySQL($host, $dbUser, $dbPass, $dbName);
 ?>
```

²特别是，trigger_error 函数将在本章后面讨论“如何解决 SQL 查询中的错误？”。

在这里使用类的目的是为了练习使用 PHP 的对象模型来处理常见任务。如果你刚接触 PHP 的面向对象编程，在这个阶段最重要的是记住，你不需要理解类中所有代码，就能在自己的代码中使用它。

我们将在整本书中使用这个类和其他类，来说明面向对象编程如何帮助代码重用，并在开发应用程序时节省时间。

## 如何从表中获取数据？

当然，能够连接到数据库很好。但是，如果我们无法从中获取任何东西，那又有什么用呢？

从 MySQL 获取数据有多种方法，但最广泛使用的可能是将 mysql_fetch_array 与 mysql_query 配合使用。

我们只需在我们在“如何访问 MySQL 数据库？”中看到的 connectToDb 函数基础上稍加补充，即可从该表中获取数据：

```
// Connect to MySQL
$dbConn = &connectToDb($host, $dbUser, $dbPass, $dbName);

// A query to select all articles
$sql = "SELECT * FROM articles ORDER BY title";

// Run the query, identifying the connection
$QueryResource = mysql_query($sql, $dbConn);

// Fetch rows from MySQL one at a time
while ($row = mysql_fetch_array($QueryResource, MYSQL_ASSOC)) {
	echo 'Title: ' . $row['title'] . '<br />';
	echo 'Author: ' . $row['author'] . '<br />';
	echo 'Body: ' . $row['body'] . '<br />';
}
```

总之，获取数据有三个步骤：

- 1. 首先，将必要的 SQL 查询³放入字符串中：

³如果你对结构化查询语言（SQL）不熟悉，我将在本章中介绍基础知识。不过，为了获得更完整的内容，请参阅《使用 PHP 和 MySQL 构建自己的数据库驱动网站，第 2 版》（ISBN 0-9579218-1-0）。




```php
$sql = "SELECT * FROM articles ORDER BY title";
```

将其保存在单独的变量中很方便，因为当我们开始编写更复杂的查询并出错时，可以用这一行代码来双重检查查询：

```php
echo $sql;
```

- 2. 接下来，告诉 MySQL 执行查询：

```php
$queryResource = mysql_query($sql, $dbConn);
```

起初这可能会让人感到困惑。当你告诉 MySQL 执行查询时，它不会立即返回结果。相反，它会将结果保存在内存中，直到你告诉它下一步该做什么。PHP 使用 **资源标识符** 来跟踪结果，这就是你从 `mysql_query` 函数中获取的内容。在上面的代码中，我们已将标识符存储在 `$queryResource` 中。

- 3. 最后，使用 `mysql_fetch_array` 逐行从结果集中获取一行：

```php
while ($row = mysql_fetch_array($queryResource, MYSQL_ASSOC))
```

这会将结果中的每一行依次放入变量 `$row` 中。这些行中的每一行都将由一个数组表示。通过在 `mysql_fetch_array` 中使用额外参数 `MYSQL_ASSOC`，我们告诉函数返回一个数组，其中的键对应表中的列名。如果省略 `MYSQL_ASSOC` 参数，每个列都会在数组中出现两次：一次使用数字索引（即 `$row[0]`、`$row[1]` 等），一次使用字符串索引（即 `$row['title']`、`$row['author']` 等）。虽然这通常不会造成问题，但指定想要的数组值类型会稍微提升速度。

如上所示，使用 while 循环是依次处理结果集中每一行的常见方法。循环实际上是在说：“不断从 MySQL 中获取行，直到获取不到为止”，循环体在获取行的同时对其进行处理。

## 对大型查询放弃缓冲

![](img/5b6cdf7cf4cf53e30b19e047895dc464_94_0.png)

对于大型查询（即产生大型结果集的查询），你可以通过告诉 PHP 不要**缓冲**查询结果来大幅提升性能。当查询_被_缓冲时，整个结果集会先从 MySQL 检索并存储在内存中，然后脚本才能继续执行。另一方面，**未缓冲查询**允许 MySQL 保留结果，直到你逐行请求它们（例如，使用 mysqli_fetch_array）。这不仅允许你的脚本在 MySQL 执行查询时继续运行，还避免了 PHP 需要一次性将所有行存储在内存中。

PHP 允许你使用 mysqli_unbuffered_query 执行未缓冲查询：

```php
$queryResource = mysqli_unbuffered_query($sql, $dbConn);
```

当然，好事总有代价——使用未缓冲查询后，你将无法再使用 mysqli_num_rows 函数来计算行数。显然，由于 PHP 没有保留完整结果集的副本，它无法计算其中包含的行数！你还必须从 MySQL 中获取结果集的所有行，然后才能执行另一条查询。

虽然还有其他函数可用于从查询结果中获取行和单元格，例如 mysqli_fetch_object 和 mysqli_result，但仅使用 mysqli_fetch_array 就能实现大致相同的功能，并且保持一致性有助于使代码保持简单。

## 使用类获取数据

既然你已经对从 MySQL 获取数据的基础知识感到满意，是时候在上一个方案的 MySQL 类基础上进行进一步构建了。

首先，让我们向类中添加一个运行查询的方法：

```php
File: Database/MySQL.php (in SPLIB) (excerpt)

/**
 * Returns an instance of MySQLResult to fetch rows with
 * @param $sql string the database query to run
 * @return MySQLResult
 * @access public
 */
function &query($sql)
{
    if (!($queryResource = mysqli_query($sql, $this->dbConn)) {
        trigger_error('Query failed: ' . mysqli_error($this->dbConn)
            . ' SQL: ' . $sql);
    }

    return new MySQLResult($this, $queryResource);
}
```

这个新方法的作用是接受一个包含 SQL 语句的变量，运行它，然后从另一个类 MySQLResult（如下所述）构建一个新对象。接着，它将该对象返回到调用 query 的位置。

以下是该新类 MySQLResult 的代码：

```php
File: Database/MySQL.php (in SPLIB) (excerpt)

/**
 * MySQLResult Data Fetching Class
 * @access public
 * @package SPLIB
 */
class MySQLResult {
/**
 * Instance of MySQL providing database connection
 * @access private
 * @var MySQL
 */
var $mysql;

/**
 * Query resource
 * @access private
 * @var resource
 */
var $query;

/**
 * MySQLResult constructor
 * @param object mysql (instance of MySQL class)
 * @param resource query (MySQL query resource)
 * @access public
 */
function MySQLResult(&$mysql, $query)
{
    $this->mysql = &$mysql;
    $this->query = $query;
}

/**
 * Fetches a row from the result
 * @return array
 * @access public
 */
function fetch()
{
    if ($row = mysql_fetch_array($this->query, MYSQL_ASSOC)) {
        return $row;
    } else if ( $this->size() > 0 ) {
        mysql_data_seek($this->query, 0);
        return false;
    } else {
        return false;
    }
}

/**
 * Checks for MySQL errors
 * @return boolean
 * @access public
 *
*/
function isError()
{
    return $this->mysql->isError();
}
```

现在，请再稍微屏住呼吸，直到你看到使用这些类是什么样子：

```php
<?php
// Include the MySQL class
require_once 'Database/MySQL.php';

$host = 'localhost'; // Hostname of MySQL server
$dbUser = 'harry'; // Username for MySQL
$dbPass = 'secret'; // Password for user
$dbName = 'sitepoint'; // Database name

// Connect to MySQL
$db = &new MySQL($host, $dbUser, $dbPass, $dbName);

$sql = "SELECT * FROM articles ORDER BY title";

// Perform a query getting back a MySQLResult object
$result = $db->query($sql);

// Iterate through the results
while ($row = $result->fetch()) {
    echo 'Title: ' . $row['title'] . '<br />';
    echo 'Author: ' . $row['author'] . '<br />';
    echo 'Body: ' . $row['body'] . '<br />';
}
?>
```

如果你不习惯面向对象编程，这可能看起来非常令人困惑，但最重要的是要专注于如何使用这些类，而不是关注类内部隐藏的细节。一旦你习惯了，这就是面向对象编程的乐趣之一。代码在幕后可能会变得非常复杂，但你只需要关注代码用来使用类的简单“接口”（API）。

### 关于 API

在类周围经常会听到 API 这个术语。API 代表 *应用程序编程接口*。它指的是作为类中功能“入口”的一组方法。设计良好的 API 将允许类的开发人员在幕后进行根本性更改，而不会破坏使用该类的任何代码。

将使用 MySQL 类与之前的过程式代码进行比较，很容易看出两者的相似之处。既然它们如此相似，你可能会问：“为什么不坚持使用纯粹的过程式 PHP？”嗯，在这种情况下，它隐藏了与执行查询相关的许多细节。管理连接、捕获错误以及决定以何种格式获取查询结果等任务，都由类在幕后处理。类还使全局修改（例如从 MySQL 切换到 PostgreSQL）变得相对轻松（即，你可以简单地切换到提供相同 API 的 *PostgreSQL* 类）。

## 如何解决 SQL 查询中的错误？

当尝试将 PHP 和 SQL 一起使用时出错，往往很难找到原因。诀窍是让 PHP 告诉你问题出在哪里，但请记住，当网站上线时，你必须能够向访问者隐藏这些信息。

PHP 提供了 `mysqli_error` 函数，用于返回最近一次 MySQL 操作的详细错误消息。

最好将其与 trigger_error 函数（将在第 10 章中更详细地讨论）配合使用，该函数允许你控制错误消息的输出。让我们修改一下之前看到的基本连接代码：

```php
// Make connection to MySQL server
if (!$dbConn = mysql_connect($host, $dbUser, $dbPass)) {
    trigger_error('Could not connect to server: ' . mysql_error());
    die();
}

// Select the database
if (!mysql_select_db($dbName)) {
    trigger_error('Could not select database: ' . mysql_error());
    die();
}
```

查询也可以采用同样的方法：

```php
// A query to select all articles
$sql = "SELECT * FROM articles ORDER BY title";

// Run the query, identifying the connection
if (!$queryResource = mysql_query($sql, $dbConn)) {
    trigger_error('Query error ' . mysql_error() . ' SQL: ' . $sql);
}
```

返回完整的查询本身通常是个好主意，就像我们在上面的示例中所做的那样，尤其是当你使用 PHP 变量构建查询时。这样你可以清楚地看到执行了哪个查询，并在必要时直接针对 MySQL 执行它，以准确找出出错的地方。

上面讨论的 MySQL 类在遇到问题时会自动使用 mysql_error 和 trigger_error。

## 如何向数据库中添加或修改数据？

能够从数据库中获取数据是一个好的开始，但你最初如何将数据放入其中呢？





再说一次，使用 PHP 时答案很简单：使用 mysql_query 函数配合 SQL 命令 INSERT 和 UPDATE。INSERT 用于在表中创建新行，而 UPDATE 用于修改现有行。

## 插入一行

使用本章开头定义的 articles 表，一个简单的 INSERT 如下所示：

```
// A query to INSERT data
$sql = "INSERT INTO
articles
SET
title = '$title',
body = '$body',
author = '$author'";

// Run the query, identifying the connection
if (! $queryResource = mysql_query($sql, $dbConn)) {
trigger_error('Query error ' . mysql_error() . ' SQL: ' . $sql);
}
```

## 更新一行

在使用 UPDATE 查询之前，你需要能够识别要更新表中的哪一行（或哪些行）。在本示例中，我使用了一个 SELECT 查询来获取标题为“How to insert data”的文章的唯一 article_id 值：

```
// A query to select an article
$sql = "SELECT article_id FROM articles
WHERE title='How to insert data'";

if (! $queryResource = mysql_query($sql, $dbConn)) {
trigger_error('Query error ' . mysql_error() . ' SQL: ' . $sql);
}

// Fetch a single row from the result
$row = mysql_fetch_array($queryResource, MYSQL_ASSOC);

// A new title
$title = 'How to update data';

$sql = "UPDATE
 articles
 SET
 title='Title'
 WHERE
 article_id='' . $row['article_id'] . ''";

 if (!$queryResource = mysql_query($sql, $dbConn)) {
  trigger_error('Query error ' . mysql_error() . ' SQL: ' . $sql);
 }
```

在上述示例中，我们使用 SELECT 查询来查找要更新的行的 ID。

在实际的 Web 应用程序中，UPDATE 可能发生在依赖 Web 浏览器输入的页面上，例如，用户使用 HTML 表单输入了值之后。这些数据中的字符串可能包含撇号，这会破坏 SQL 并影响安全。因此，请务必阅读“如何解决由引号/撇号引起的数据库错误？”，该部分涵盖 SQL 注入攻击。

![](img/5b6cdf7cf4cf53e30b19e047895dc464_101_0.png)

## 警惕全局更新

使用 UPDATE 时要小心，并记住使用 WHERE 子句来指示要更改哪些行。

例如，考虑以下查询：

```
UPDATE articles SET title = 'How NOT to update data'
```

这将更新表中*每一行*！

## 另一个类操作

使用上次在“如何从表中获取数据？”中出现的 MySQL 类，我们可以执行 INSERT 和 UPDATE 查询，无需任何进一步修改。使用该类重复上述示例，我们可以先这样 INSERT：

```
// Connect to MySQL
$db =& new MySQL($host, $dbUser, $dbPass, $dbName);

$title = 'How to insert data';
$body = 'This is the body of the article';
$author = 'HarryF';

// A query to INSERT data
$sql = "INSERT INTO
        articles
        SET
        title = '$title',
        body = '$body',
        author = '$author'";

$db->query($sql);

if (!$db->isError()) {
    echo 'INSERT successful';
} else {
    echo 'INSERT failed';
}
```

我们可以这样 UPDATE：

```
$db = &new MySQL($host, $dbUser, $dbPass, $dbName);

// A query to select an article
$sql = "SELECT article_id FROM articles
        WHERE title='How to insert data'";

$result = $db->query($sql);

$row = $result->fetch();

// A new title
$title = 'How to update data';

$sql = "UPDATE
        articles
        SET
        title='' . $title . ''
        WHERE
        article_id='' . $row['article_id'] . ''";

$db->query($sql);

if (!$db->isError()) {
    echo 'UPDATE successful';
} else {
    echo 'UPDATE failed';
}
```

## 如何解决由引号/撇号引起的数据库错误？

考虑以下 SQL 语句：

```
INSERT INTO articles SET title='The PHP Anthology';
```

也许生成此查询的 PHP 脚本包含类似这样的内容：

```
<?php
$title = "The PHP Anthology";

$sql = "INSERT INTO articles SET title='$title'; ";

$result = mysql_query($sql, $dbConn);
?>
```

目前为止没问题，但如果更改标题，看看会发生什么：

```
$title = "PHP's Greatest Hits";
```

注意标题中的撇号了吗？当我们将其放入 SQL 语句时，MySQL 接收到的查询将如下所示：

```
INSERT INTO articles SET title='PHP's Greatest Hits';
```

看出问题了吗？当 MySQL 读取该语句时，它只会读到这里：

```
INSERT INTO articles SET title='PHP'
```

语句的其余部分会导致语法错误，查询将失败。当你自己编写标题时，避免这个问题很容易，但如果你的脚本从用户输入中获取值，会发生什么呢？

## 伟大的转义

解决方案是在撇号之前添加反斜杠来**转义**撇号字符。例如，以下查询将正常工作：

```
INSERT INTO articles SET title='PHP\'s Greatest Hits';
```

## 反斜杠与 ANSI SQL 标准

请注意，使用反斜杠作为转义字符不是标准 ANSI SQL。如果 MySQL 是你将要使用的唯一数据库，反斜杠可能可以接受，但相同的 SQL 语句在其他数据库上运行可能会失败。根据 ANSI SQL，我们应该使用另一个单引号来转义撇号：

```
INSERT INTO articles SET title='PHP ''s Greatest Hits';
```

问题是，当我们在 PHP 中即时构建查询时，如何确保所有撇号都已转义？由于存在多种替代方案，处理这种情况变得相当令人困惑：

- 首先是 php.ini 设置 magic_quotes_gpc。魔术引号是 PHP 的一项功能，开启后，它会通过在字符串中添加反斜杠，自动转义传入的 GET、POST 和 Cookie 变量中发现的单引号、双引号、反斜杠和空字符。这听起来很棒，但在实践中，它很快就会引起麻烦，通常是在涉及表单的情况下。

假设你有一个用于编辑文章的表单。你的脚本获取用户输入的文本并将其插入 MySQL。现在，如果用户未能完成某个重要字段，你可能希望重新显示表单中迄今输入的详细信息。开启魔术引号后，你将不得不剔除它添加到值中的所有斜杠（使用 PHP 的 stripslashes 函数）！

那么，如果你想在 magic_quotes_gpc 被禁用的服务器上运行代码，该怎么办呢？你的代码则需要检查魔术引号是否开启，并跳过使用 stripslashes。头痛是不可避免的，如果你出错并最终在数据库⁴中存储了多余的反斜杠，你可能面临痛苦的清理过程。

魔术引号在第 1 章中有详细讨论。如果你像我建议的那样关闭 magic_quotes_gpc，则应了解潜在的安全风险。请参见下面的“SQL 注入攻击”部分和附录 C。

⁴ 我始终惊讶于有那么多专业设计的网站无法正确处理字符转义！在你自己的 Web 浏览中，要留意意外的反斜杠。有关如何在自己的网站上最好地避免这种情况的建议，请参见第 1 章。

- 接下来，我们有 PHP 函数 addslashes。应用于任何字符串时，addslashes 将使用反斜杠转义单引号、双引号、反斜杠和空字符。这使其成为用于查询的字符串转义的有效手段。

当然，如果魔术引号已开启，则不得使用 addslashes，否则字符将被转义两次！为解决此冲突，你可以使用函数 get_magic_quotes_gpc 检查魔术引号是否启用，如果启用则返回 TRUE，否则返回 FALSE。你可以将此测试封装到一个函数中，如下所示：

```
<?php
function safeAddSlashes($string)
{
if (get_magic_quotes_gpc()) {
return $string;
} else {
return addslashes($string);
}
}
?>
```

- 第三种方法与 addslashes 非常相似，它使用函数 mysql_escape_string 或 mysql_real_escape_string（后者添加于 PHP 4.3.0）。这些函数使用底层 MySQL C++ API（由 MySQL 开发者而非 PHP 开发者提供）来转义特殊字符。

这些函数转义空字符、换行符、回车符、反斜杠、单引号、双引号和文件结束字符。自 PHP 4.3.0 以来，这两个函数都使用 PHP 和 MySQL 之间连接的当前字符集。因此，在最新的 PHP 版本中，这两个函数没有区别，所以如果你的服务器是最新的，请随意使用较短的那个，即 mysql_escape_string。

由于这种方法实际上是 MySQL 提供的转义字符串的内置机制，我推荐使用它，而不是 addslashes 或 magic_quotes_gpc。当然，如果你希望 SQL 能够良好地移植到其他数据库，你可能希望将函数调用“隐藏”在类方法中，这样在迁移到不同数据库时，你可以更换类——包括转义机制。





同样，如果你没有以其他方式处理魔术引号问题，你将不得不检查 magic_quotes_gpc 是否开启：

```php
function safeEscapeString($string)
{
    if (get_magic_quotes_gpc()) {
        return $string;
    } else {
        return mysql_real_escape_string($string);
    }
}
```

本书中的脚本使用了在第 1 章中介绍并包含在代码归档中的 MagicQuotes/strip_quotes.php 引入文件，以在启用魔术引号的服务器上有效地将其关闭，因此接下来的解决方案将自由地使用 mysql_real_escape_string。如果你对自己转义引号和其他特殊字符有信心，我建议你在自己的脚本中也这样做。

## SQL 注入攻击

SQL 注入攻击是指攻击者利用你网站上的合法用户输入机制，发送 SQL 代码，而你毫无戒心的脚本会将其传递给数据库执行。金科玉律：在让外部数据接近你的数据库之前，先转义所有来自外部来源的数据。这条规则不仅适用于 INSERT 和 UPDATE 查询，也适用于 SELECT 查询。

毫无疑问，许多 PHP 开发人员之所以免受最严重的 SQL 注入攻击，多亏了 MySQL 的局限性——MySQL 每次调用 mysql_query 只允许执行一条 SQL 语句。在其他数据库上，SQL 注入的影响可能是灾难性的，因为攻击者可以发送第二条查询，例如删除整个表的内容。然而，使用 MySQL 时问题仍然可能发生，如下面的代码所示：

```php
$sql = "SELECT * FROM users
       WHERE username='" . $_POST['username'] . "'
       AND password='" . $_POST['password'] . "'";

echo 'Query: ' . $sql . '<br />';

$result = mysql_query($sql);
$rows = mysql_num_rows($result);

if ($rows > 0) {
    echo 'You are logged in!<br />';
} else {
    echo 'You are not allowed here!<br />';
}
?>
<form method="post" action="?<?php echo $_SERVER['PHP_SELF']; ?>">
<input type="text" name="username" /><br />
<input type="text" name="password" /><br />
<input type="submit" />
</form>
```

精明的攻击者可以简单地在表单的密码字段中输入以下内容：

```
' OR username LIKE '%'
```

假设你的服务器上禁用了魔术引号，并且没有采取其他预防措施，这个巧妙的攻击会改变查询的含义：

```
SELECT * FROM users
WHERE username='' AND password='' OR username LIKE '%'
```

修改后的查询将选取用户表中*所有*记录！当脚本检查是否有任何用户与提供的用户名和密码组合匹配时，它将看到这个庞大的结果集并授予访问网站的权限！

如果我们转义传入的变量，就可以防止这种情况：

```php
$sql = "SELECT * FROM users
WHERE username='" . safeEscapeString($_POST['username']) . "'
AND password='" . safeEscapeString($_POST['password']) . "'";
```

在某些情况下，视具体情况而定，这可能不是必须的。但如果你珍惜自己的安宁，请记住那条金科玉律：转义所有来自外部来源的数据。

## 如何创建灵活的 SQL 语句？

SQL 是一种用于操作数据的强大语言。使用 PHP，我们可以从变量构建 SQL 语句，这对于按单个列对表进行排序或将大型结果集分页显示非常有用。

下面是一个简单示例，允许我们按表列对查询结果进行排序：

```php
// A query to select all articles
$sql = "SELECT * FROM articles";

// Initialize $_GET['order'] if it doesn't exist
if (!isset($_GET['order']))
    $_GET['order'] = FALSE;

// Use a conditional switch to determine the order
switch ($_GET['order']) {
    case $author:
        // Add to the $sql string
        $sql .= " ORDER BY author";
        break;
    default:
        // Default sort by title
        $sql .= " ORDER BY title";
        break;
}

// Run the query, identifying the connection
if (!$queryResource = mysql_query($sql, $dbConn)) {
    trigger_error('Query error ' . mysql_error() . ' SQL: ' . $sql);
}
?>
<table>
<tr>
<th><a href="<?php echo $_SERVER['PHP_SELF']; ?>?order=title">Title</a></th>
<th><a href="<?php echo $_SERVER['PHP_SELF']; ?>?order=author">Author</a></th>
</tr>
<?php
while ($row = mysql_fetch_array($queryResource, MYSQL_ASSOC)) {
    echo "<tr>\n";
    echo "<td>" . $row['title'] . "</td>";
    echo "<td>" . $row['author'] . "</td>";
    echo "</tr>\n";
}
?>
</table>
```

在 switch 语句中，我根据脚本从浏览器接收到的 GET 变量“即时”生成了部分 SQL 语句。

这种通用方法可以扩展到 WHERE 子句、LIMIT 子句以及你愿意在 SQL 中考虑的任何其他内容。我们将在第 9 章构建分页结果集时更详细地探讨这一点。

## 持久层：无需 SQL 的数据库交互

持久层正变得流行，并且在当今的 PHP 中得到了良好支持。持久层是一组代表数据库中表的类，为你提供了一个 API，数据库与 PHP 应用程序之间交换的所有数据都通过该 API 传递。这通常使你无需手动编写 SQL 语句，因为查询由代表数据的 PHP 类自动生成和执行。

由于 SQL 是一个定义良好的标准，因此也有可能自动生成持久层。程序可以检查你的数据库架构，并生成将自动读取和更新它的类。这可以大大节省时间；只需设计数据库，运行代码生成工具，其余的“只是”格式化少量 (X)HTML 的问题。

持久层的一个主要示例是 PEAR::DB_DataObject[1]，它基于 PEAR::DB 数据库抽象库，并自动生成一组用于访问表的类。

[1] http://pear.php.net/package-info.php?package=DB_DataObject

持久层（尤其是 PEAR::DB_DataObject）在“我真的需要编写 SQL 吗？”中进行了讨论。

## 如何查明我选取了多少行？

在对查询返回的行数做任何处理之前，能够先行统计行数通常很有用，例如在按页拆分结果或生成统计信息时。在选取结果时，你可以使用 PHP 或 MySQL 来统计行数。

### 使用 PHP 统计行数

使用 PHP 时，函数 mysql_num_rows 返回选取的行数，但在使用非缓冲查询时其应用可能受到限制（参见“如何从表中获取数据？”）。下面的代码说明了 mysql_num_rows 的用法：

```php
// A query to select all articles
$sql = "SELECT * FROM articles ORDER BY title";

// Run the query, identifying the connection
$queryResource = mysql_query($sql, $dbConn);

// Fetch the number of rows selected
$numRows = mysql_num_rows($queryResource);

echo $numRows . ' rows selected<br />';

// Fetch rows from MySQL one at a time
while ($row = mysql_fetch_array($queryResource, MYSQL_ASSOC)) {
    echo 'Title: ' . $row['title'] . '<br />';
    echo 'Author: ' . $row['author'] . '<br />';
    echo 'Body: ' . $row['body'] . '<br />';
}
```

上面示例中演示的 mysql_num_rows 函数，接受一个结果集资源标识符并返回该结果集中的行数。

请注意，相关函数 mysql_num_fields 可用于查明选取了多少列。在使用类似 SELECT * FROM table 的查询但不知道选取了多少列时，这非常方便。

### 使用 MySQL 统计行数

另一种方法是在查询中使用 MySQL 的 COUNT 函数。这需要执行两个查询——一个用于计数结果，一个用于实际*获取*结果——这在性能上会稍有损耗。

下面是如何使用 MySQL COUNT 函数的示例：

```php
// A query to select all articles
$sql = "SELECT COUNT(*) AS numrows FROM articles";

// Query to count the rows returned
$queryResource = mysql_query($sql, $dbConn);
```



```php
$row = mysql_fetch_array($queryResource, MYSQL_ASSOC);
echo $row['numrows'] . " rows selected<br />";
// A query to select all articles
$sql = "SELECT * FROM articles ORDER BY title";
// Run the query, identifying the connection
$queryResource = mysql_query($sql, $dbConn);
// Fetch rows from MySQL one at a time
while ($row = mysql_fetch_array($queryResource, MYSQL_ASSOC)) {
    echo 'Title: ' . $row['title'] . '<br />';
    echo 'Author: ' . $row['author'] . '<br />';
    echo 'Body: ' . $row['body'] . '<br />';
}
```

注意我们使用了一个 **别名** 来放置 COUNT 函数的结果吗？

```sql
SELECT COUNT(*) AS numrows FROM articles
```

我们这么做是为了以后可以使用 $row['numrows'] 来识别行数。另一种做法是省略别名：

```sql
SELECT COUNT(*) FROM articles
```

这将需要我们以 $row['COUNT(*) '] 的方式访问信息，这会使代码阅读起来令人困惑。

当我们使用 COUNT 函数时，像我们在“如何创建灵活的 SQL 语句？”中看到的那样，即时构建查询变得很重要。你需要确保你的 COUNT 查询包含与在“真实”查询中使用的相同的 WHERE 或 LIMIT 子句。例如，如果我们实际用于获取数据的查询是：

```sql
SELECT * FROM articles WHERE author='HarryF'
```

在 PHP 中，我们可能会想要这样的代码：

```php
// Define reusable "chunks" of SQL
$table = " FROM articles";
$where = " WHERE author='HarryF'";
$order = " ORDER BY title";
// Query to count the rows returned
$sql = "SELECT COUNT(*) as numrows" . $table . $where;

// Run the query, identifying the connection
$queryResource = mysql_query($sql, $dbConn);

$row = mysql_fetch_array($queryResource, MYSQL_ASSOC);

echo $row['numrows'] . " rows selected<br />";

// A query to fetch the rows
$sql = "SELECT * " . $table . $where . $order;

// Run the query, identifying the connection
$queryResource = mysql_query($sql, $dbConn);

// Fetch rows from MySQL one at a time
while ($row = mysql_fetch_array($queryResource, MYSQL_ASSOC)) {
    echo 'Title: ' . $row['title'] . '<br />';
    echo 'Author: ' . $row['author'] . '<br />';
    echo 'Body: ' . $row['body'] . '<br />';
}
```

## 使用类统计行数

让我们再看看本节中一直在开发的类。我们可以通过向 MySQLResult 类引入以下方法来添加查找所选行数的功能：

文件：Database/MySQL.php（在 SPLIB 中）（摘录）

```php
/**
 * Returns the number of rows selected
 * @return int
 * @access public
 */
function size()
{
    return mysql_num_rows($this->query);
}
```

以下是使用方法：

文件：15.php（摘录）

```php
// Connect to MySQL
$db =& new MySQL($host, $dbUser, $dbPass, $dbName);
// Select all results for a particular author
$sql = "SELECT * FROM articles WHERE author='HarryF'";
$result = $db->query($sql);
echo "Found " . $result->size() . " rows";
```

### 统计受影响的行数

也可以使用 PHP 函数 `mysql_affected_rows` 找出 UPDATE、INSERT 或 DELETE 查询影响了多少行。在典型的 PHP 应用程序中，使用 `mysql_affected_rows` 并不常见，但它可以是告知用户“你刚刚从 Customers 表中删除了 1854 条记录。祝你愉快！”的好方法。

与将结果集资源标识符作为参数的 `mysql_num_rows` 不同，`mysql_affected_rows` 接受数据库连接标识符。它返回指定连接上最后一次修改数据库的查询所影响的行数。

以下是 `mysql_affected_rows` 的使用方法：

```php
// Connect to MySQL
$dbConn = &connectToDb($host, $dbUser, $dbPass, $dbName);
// A query which updates the database
$sql = "UPDATE
articles
SET
author='The Artist Formerly Known as...'
WHERE
author='HarryF'";
// Run the query, identifying the connection
$queryResource = mysql_query($sql, $dbConn);
// Fetch the number of rows affected
$changedRows = mysql_affected_rows($dbConn);
echo $changedRows . ' rows changed<br />';
```

由于需要 `mysql_affected_rows` 的情况不常见，出于保持简单的目的，我将在 MySQLResult 类中省略此功能。

## 插入一行后，如何找到其行号？

在处理数据库表中的 AUTO_INCREMENT 列时，通常很有用能够找到刚插入的行的 ID，以便其他表可以使用此信息进行更新。毕竟，表之间的关系就是这么构建的。PHP 提供了 mysql_insert_id 函数，当给定一个链接标识符时，它返回使用该连接执行的最后一次 INSERT 生成的 ID。以下是 mysql_insert_id 的使用方法：

```php
// A query to insert a row
$sql = "INSERT INTO articles
        SET
        title='How to use mysql_insert_id()',
        body='This is an example',
        author='HarryF';";

// Run the query, identifying the connection
$QueryResource = mysql_query($sql, $dbConn);

// Fetch the inserted ID
$insertID = mysql_insert_id($dbConn);

echo 'The new row has ID: ' . $insertID;
```

### 类 Insert ID

要在我们的 MySQLResult 类中使用此功能，请添加以下方法：

```php
/**
 * Returns the ID of the last row inserted
 * @return int
 * @access public
 */
function insertID()
{
    return mysql_insert_id($this->mysql->dbConn);
}
```

如你所料，使用此方法非常简单：

文件：18.php（摘录）

```php
// Include the MySQL class
require_once 'Database/MySQL.php';

$host = 'localhost'; // Hostname of MySQL server
$dbUser = 'harry'; // Username for MySQL
$dbPass = 'secret'; // Password for user
$dbName = 'sitepoint'; // Database name

$db = &new MySQL($host, $dbUser, $dbPass, $dbName);

// A query to insert a row
$sql="INSERT INTO
articles
SET
title='How to use mysql_insert_id()',
body='This is an example',
author='HarryF'";

$result = $db->query($sql);

echo 'The new row has ID: ' . $result->insertID();
```

## 如何搜索我的表？

有些人就是不耐烦；他们不愿使用你提供的友好导航系统在你的网站上搜索，而是要求立即获得信息！因此，像你我这样的 PHP 开发者需要实现搜索功能，为访问者提供一个“快捷方式”来找到他们想要的信息。在将所有内容以 HTML 文件形式存储的日子里，这可能是一个大问题，但现在你使用数据库存储内容，搜索变得容易多了。

### 使用 LIKE 选择

最基本的搜索形式是针对单个列，使用 LIKE 运算符：

```sql
SELECT * FROM articles WHERE title LIKE 'How %'
```

% 是通配符字符。上述语句将选择标题以单词“How”开头的所有文章。MySQL 还支持 POSIX 正则表达式（与 PHP 的 ereg 函数相同）。使用 `RLIKE` 运算符，我们可以使用正则表达式比较列：

```sql
SELECT * FROM articles WHERE title RLIKE '^How '
```

上述语句还会选择每篇标题以“How”开头并后跟空格的文章。

经过一些工作，这些运算符提供了探索数据所需的一切。上述方法成为负担的地方是在多个列上执行搜索时。例如，

```sql
SELECT * FROM articles
WHERE title LIKE '%show%' OR body LIKE '%show%'
```

对于较大的表，这可能需要你编写非常复杂且令人不快的查询。

### FULLTEXT 搜索

MySQL 提供了一个替代方案，可以为你完成大部分工作——FULLTEXT 索引。数据库中的索引很像书籍的索引；它们提供了一种从有组织的列表中快速定位数据库内信息的方法。FULLTEXT 索引允许你搜索表中的特定单词。

FULLTEXT 索引是在 MySQL 3.23 版本中引入的。当时的实现相当有限，但对于基本搜索仍然有用，这也是我将在此演示的内容。在 MySQL 4.0.1 版本中，此功能被扩展以提供完整的布尔搜索机制，使你能够构建类似 Google™ 高级搜索功能的东西。FULLTEXT 索引还允许每个结果带有一个“相关性”值返回，因此，例如，多个单词搜索的结果可以根据每个结果与用户特定搜索的匹配程度来显示。

要利用 FULLTEXT 索引，你首先需要指示 MySQL 开始构建要搜索的列的索引：

```sql
ALTER TABLE articles ADD FULLTEXT art_search (title, body, author)
```

一旦你做了这一点，你需要插入一条新记录（或修改现有记录）来让 MySQL 构建索引。你还需要数据库中至少有三条记录，FULLTEXT 搜索才能工作，因为非布尔搜索只有在搜索字符串出现在小于 50% 的行中时才会返回结果



表中（如果表中只有两行，且你的搜索匹配其中一行，那将占 50%）。最后需要注意的一点是，FULLTEXT 搜索只匹配超过三个字母的搜索词；索引机制会忽略三个字符或更少的单词，以避免构建庞大的索引。这很像书籍的索引；你会非常惊讶地发现，在书籍的索引中，单词“the”出现在哪些页面！

## 以下是基本的 FULLTEXT 搜索：

```
SELECT * FROM articles
WHERE MATCH (title,body,author) AGAINST ( 'MySQL' );
```

此搜索将返回标题、正文或作者中包含单词“MySQL”的所有行。

FULLTEXT 索引的另一个用途是在搜索中为每个结果返回相关性。例如：

```
// Select all rows but display relevance
$sql = "SELECT
  *, MATCH (title, body, author)
  AGAINST
  ('The PHP Anthology Released Long Word Matching')
  AS
  score
  FROM
  articles
  ORDER BY score DESC";
// Run the query, identifying the connection
$queryResource = mysql_query($sql, $dbConn);
// Fetch rows from MySQL one at a time
while ($row = mysql_fetch_array($queryResource, MYSQL_ASSOC)) {
  echo 'Title: ' . $row['title'] . '<br />';
  echo 'Author: ' . $row['author'] . '<br />';
  echo 'Body: ' . $row['body'] . '<br />';
  echo 'Score: ' . $row['score'] . '<br />';
}
```

别名 score 现在包含一个值，用于标识该行与搜索的相关程度。该值不是百分比，而仅是一种度量；0 表示完全没有匹配。匹配一个单词将产生大约 1 的值。匹配的单词越多，数值就越大，因此五个单词匹配的排名将产生大约 13 的相关性评分。MySQL 的相关性算法专为大型表设计，因此你拥有的数据越多，相关性值就越有用。

总的来说，MySQL 的 FULLTEXT 搜索功能提供了一种易于实现且能够提供有用结果的机制。

## 如何备份我的数据库？

数据库越大，如果没有包含其中数据的备份，就越令人不安。如果服务器崩溃，一切都丢失了怎么办？幸运的是，MySQL 提供了两种替代方案：一个名为 mysqldump 的命令行实用程序，以及用于备份表的查询语法。

以下是如何使用 mysqldump 从命令行导出数据库内容：

```
mysqldump -uharryf -psecret sitepoint > sitepoint.sql
```

该命令将以用户“harry”（-uharryf）和密码“secret”（-psecret）登录到 MySQL，并将 sitepoint 数据库的内容输出到名为 sitepoint.sql 的文件。sitepoint.sql 的内容将是一系列可以针对 MySQL 运行的查询，也许可以使用 mysql 实用程序从命令行执行反向操作：

```
mysql -uharryf -psecret sitepoint < sitepoint.sql
```

使用 PHP 的 system 函数，你可以在 PHP 脚本中执行上述命令（这要求你已登录并能够从命令行执行 PHP 脚本）。以下类将所有这些整合成一个方便的 PHP 形式，你可以使用它来定期备份你的网站。

```
File: Database/MySQLDump.php (in SPLIB)

/**
 * MySQLDump Class<br />
 * Backs up a database, creating a file for each day of the week,
 * using the mysqldump utility.<br />
 * Can compress backup file with gzip or bzip2<br />
 * Intended for command line execution in conjunction with
 * cron<br />
 * Requires the user executing the script has permission to execute
 * mysqldump.
 * <code>
* $mysqliDump = new MySQLDump('harryf', 'secret', 'sitepoint',
    '/backups');
*
* $mysqliDump->backup();
* </code>
* @access public
* @package SPLIB
*/
class MySQLDump {
/**
* The backup command to execute
* @private
* @var string
*/
var $cmd;

/**
* MySQLDump constructor
* @param string dbUser (MySQL User Name)
* @param string dbPass (MySQL User Password)
* @param string dbName (Database to select)
* @param string dest (Full dest. directory for backup file)
* @param string zip (Zip type; gz - gzip [default], bz2 - bzip)
* @access public
*/
function MySQLDump($dbUser, $dbPass, $dbName, $dest,
    $zip = 'gz')
{
    $zip_util = array('gz'=>'>gzip', 'bz2'=>'>bzip2');
    if (array_key_exists($zip, $zip_util)) {
        $fname = $dbName . '.' . date("w") . '.sql.' . $zip;
        $this->cmd = 'mysqldump -u ' . $dbUser . ' -p' . $dbPass .
            ' ' . $dbName . '|' . $zip_util[$zip] . '> ' .
            $dest . '/' . $fname;
    } else {
        $fname = $dbName . '.' . date("w") . '.sql';
        $this->cmd = 'mysqldump -u ' . $dbUser . ' -p' . $dbPass .
            ' ' . $dbName . '> ' . $dest . '/' . $fname;
    }
}

/**
* Runs the constructed command
* @access public
* @return void
*/
function backup()
{
	system($this->cmd, $error);
	if ($error) {
		trigger_error('Backup failed: ' . $error);
	}
}
```

MySQLDump 类对操作系统配置做了一些假设。它假设 mysqldump 实用程序可在执行此脚本的用户的路径中使用。如果使用 gzip 或 bzip2 实用程序，它们也需要存在于执行此脚本的用户的路径中。
bzip2 提供比 gzip 更好的压缩，有助于节省磁盘空间。

以下代码演示了如何使用此类：

```
<?php
// Include the MySQLDump class
require_once 'Database/MySQLDump.php';

$dbUser = 'harryf';        // db User
$dbPass = 'secret';        // db User Password
$dbName = 'sitepoint';     // db name
$dest   = '/home/harryf/backups'; // Path to directory
$zip    = 'bz2';           // ZIP utility to compress with

// Instantiate MySQLDump
$mysqlDump = new MySQLDump($dbUser, $dbPass, $dbName, $dest,
		$zip);

// Perform the backup
$mysqlDump->backup();
?>
```

$dest 变量指定应放置备份文件的目录路径。创建的文件名将采用以下格式：

databaseName.dayOfWeek.sql.zipExtension

例如：

sitepoint.1.sql.bz2

dayOfWeek 元素可以是 0 到 6 之间的任何数字（0 代表星期日，6 代表星期六）。这提供了每周“滚动”备份，下周的文件将覆盖上周的文件。这应该提供足够的备份，给你一周的时间来发现任何严重问题，而无需过多磁盘空间来存储文件。

使用 ZIP 实用程序是可选的。如果 `$zip` 变量的值不是 `gz` 或 `bz2` 之一，则不会进行压缩，尽管对于大型数据库，显然使用压缩工具来最大限度地减少所需磁盘空间是个好主意。

此类旨在与 `crontab` 实用程序一起使用，这是一个 Unix 功能，允许你定期（例如每天）执行脚本。

MySQL 还提供 SQL 语句 `BACKUP TABLE` 和 `RESTORE TABLE`，允许你将表的内容复制到文件系统上的另一个位置。与 `mysqldump` 实用程序不同，以这种方式备份的表保留其原始格式（不可读），但此机制不需要访问命令行实用程序，因此可以通过网页执行。

这些语句的一般语法如下：

```
BACKUP TABLE tbl_name[, tbl_name ...]
TO '/path/to/backup/directory'
```

```
RESTORE TABLE tbl_name[, tbl_name ...]
FROM '/path/to/backup/directory'
```

请注意，在 Windows 系统上，最好使用正斜杠指定路径（例如 `C:/backups`）。

通过将这些与 MySQL 提供的某些“内省”语句相结合，我们可以使用本章构建的 MySQL 类来备份数据库。首先，我们需要获取数据库中的表列表，可以使用 `SHOW TABLES` 查询语法快速实现：

```
<?php
// Include the MySQL class
require_once 'Database/MySQL.php';

$host = 'localhost'; // Hostname of MySQL server
$dbUser = 'harryf'; // Username for MySQL
$dbPass = 'secret'; // Password for user
$dbName = 'sitepoint'; // Database name
```



```php
$db = &new MySQL($host, $dbUser, $dbPass, $dbName);

// A query to show the tables in the database
$sql = "SHOW TABLES FROM sitepoint";

// Execute query
$result = $db->query($sql);
```

我们还存储此查询返回的行数，以帮助我们格式化用于构建 BACKUP 查询的字符串：

```php
// Get the number of tables found
$numTables = $result->size();
```

接下来，我们遍历结果，构建一个要备份的逗号分隔的表列表：

```php
// Build a string of table names
$tables = '';
$i = 1;
while ($table = $result->fetch()) {
    $tables .= $table['Tables_in_sitepoint'];
    if ($i < $numTables) {
        $tables .= ', ';
    }
    $i++;
}
```

最后，我们使用 BACKUP TABLE 查询语法将表复制到我们选择的目录（当然，执行此查询的脚本需要有写入权限）：

```php
// Build the backup query
$sql = "BACKUP TABLE $tables TO '/home/harryf/backup'";

// Perform the query
$db->query($sql);

if (!$db->isError()) {
    echo 'Backup succeeded';
} else {
    echo 'Backup failed';
}
}
?>
```

## 如何修复损坏的表？

虽然这不应该发生，但存储在 MySQL 中的数据偶尔会损坏。这种情况可能发生在许多（罕见）的情况下；Windows 特别容易受到影响，因为它没有 Unix 系统那样强大的文件锁定机制。负载较大的服务器上，`INSERT` 和 `UPDATE` 查询与 `SELECT` 查询一起使用很常见，也可能会偶尔发生损坏。假设你使用的是 MyISAM 表类型（除非你另有指定，否则将使用此类型），好消息是；一般来说，你应该能够恢复损坏表中的所有数据。

请注意，此处提供的信息旨在为你需要快速求助时提供快速参考。阅读 MySQL 手册中关于灾难预防与恢复[2] 的内容非常有价值，这样你就知道自己在做什么。

MySQL 提供了两个重要的实用程序来处理损坏的表，以及适合能够访问 MySQL 命令行的人们使用的实用 SQL 语法。

首先，可以从命令行运行 `perror` 实用程序来大致了解 MySQL 错误代码的含义。该实用程序应可在 MySQL 安装的 `bin` 子目录中找到。例如，输入 `perror 145` 将告诉你：

```
145 = Table was marked as crashed and should be repaired
```

然后，你可以从命令行使用 `myisamchk` 实用程序来检查数据库文件本身：

```
myisamchk /path/to/mysql/data/table_name
```

使用 `myisamchk` 修复损坏的表，语法如下：

```
myisamchk -r /path/to/mysql/data/table_name
```

使用 SQL，你也可以使用类似这样的查询来检查和修复表：

```
CHECK TABLE articles
```

还有这个：

[2] http://www.mysql.com/doc/en/Disaster_Prevention.html

```
REPAIR TABLE articles
```

幸运的是，你可能只需要一两次使用这些命令，但提前做好准备是有价值的，这样你就能有效地应对（行动中甚至不会丝毫慌乱）。

## 我真的需要写 SQL 吗？

作为程序员，一种值得拥有的好品质是懒惰——即以最小的努力完成尽可能多的工作的愿望。虽然你可能不想在面试中将其列为自己的优点之一，但有动力让自己生活更轻松在开发设计良好的应用程序时是一项巨大的优势。

既然你已经读完了关于 PHP 和 MySQL 的这一章，我认为现在是时候透露我讨厌 SQL 了，这并不是因为 SQL 本身有什么问题，而是因为它总是让我很苦恼。例如，如果我的 PHP 代码中有语法错误，PHP 会为我找到它。但 PHP 不会发现 SQL 语句中的错误，MySQL 错误信息往往不够明确。如果我在应用程序中手动编写 SQL，我会花不少时间调试它——这些时间本可以用来轻松放松！

如果你能完全避免编写 SQL 语句会怎样？如果你回想一下“如何创建灵活的 SQL 语句？”，我们在那里根据传入的变量“即时”构建 SQL 字符串，你可能已经隐约感觉到会有一种通用解决方案来让生成 SQL 更加容易。确实有！它被称为 PEAR::DB_DataObject[3]。

DB_DataObject 是一个类，它通过简单的 API 封装了编写 SQL 语句的过程。它利用 SQL 的原生“语法”，为你提供了一种机制，几乎消除了自己编写任何 SQL 的需要。作为处理数据库的一种方法，它通常被描述为数据库持久层，或者，也可以说是使用数据访问对象（DAO）设计模式。你将在本章末尾找到关于 DB_DataObject 使用的通用技术的进一步讨论。

在此，我将简要介绍 DB_DataObject 以帮助你入门，因为这是一个如果深入探讨很容易占据整整一章的主题。PEAR 网站上的 DB_DataObject 文档[4]应该能为你提供大量进一步的帮助。我们在这里使用的版本是 1.1；请注意，它要求你安装了 PEAR::DB 数据库抽象库（有关安装 PEAR 库的更多信息，请参见附录 D）。

[3] http://pear.php.net/DB_DataObject
[4] http://pear.php.net/manual/en/package.database.db-dataobject.php

开始使用 DB_DataObject 的第一步是将其指向你的数据库，并告诉它生成将作为你与表之间接口的 DataObject 类。DB_DataObject 会自动检查你的数据库，使用 MySQL 的内省功能，为数据库中的每个表生成一个类，以及一个包含表定义的列详细信息的配置文件。为了让 DB_DataObject 知道数据库位于何处，你需要为其提供一个类似这样的配置文件：

```
[DB_DataObject]
; PEAR::DB DSN
database = mysql://harryf:secret@localhost/sitepoint
; Location where sitepoint.ini schema file should be created
schema_location = /htdocs/phpanth/SPLIB/ExampleApps/DataObject
; Location where DataObjects classes should be created
class_location = /htdocs/phpanth/SPLIB/ExampleApps/DataObject
; Prefix for including files from your code
require_prefix = ExampleApps/DataObject
; Classes should be prefixed with this string e.g. DataObject_User
class_prefix = DataObject_
; Debugging information: 0=off, 1=display sql, 2=display results, 3=everything
debug = 0
; Prevent SQL INSERT, UPDATE or DELETE from being performed
debug_ignore_updates = false
; Whether to die of error with a PEAR_ERROR_DIE or not
dont_die = false
```

上述 ini 文件遵循与 php.ini 相同的格式规则。最重要的是第一行，它是一个 PEAR::DB DSN 字符串，定义了连接数据库所需的变量。此文件既用于生成 DataObject 类，也用于执行查询时使用这些类。

准备好后，我们可以使用此脚本（必须从命令行运行）来生成类：

```php
<?php
// Builds the DataObjects classes
$_SERVER['argv'][1] = 'db_dataobject.ini';
require_once 'DB/DataObject/createTables.php';
?>
```

此脚本会自动创建我们访问数据库所需的类文件。以下是为 articles 表开发的示例：

```
File: ExampleApps/DataObject/Articles.php (in SPLIB)

<?php
/**
 * Table Definition for articles
 */
require_once 'DB/DataObject.php';

class DataObject_Articles extends DB_DataObject
{

    ###START_AUTOCODE
    /* the code below is auto generated do not remove the above tag
     */

    var $__table = 'articles';    // table name
    var $Article_id;   // int(11)  not_null primary_key auto_increment
    var $Title;    // string(255)  not_null multiple_key
    var $Intro; // blob(65535)  not_null blob
    var $Body; // blob(65535)  not_null blob
    var $Author;   // string(255)  not_null
    var $Published;   // string(11)
    var $Public; // string(1)  not_null enum

    /* ZE2 compatibility trick*/
    function __clone() { return $this;}

    /* Static get */
    function staticGet($k,$v=NULL) {
        return DB_DataObject::staticGet('DataObject_Articles',$k,$v); }
    /* the code above is auto generated do not remove the tag below */
    ###END_AUTOCODE
}
?>
```

现在让我们使用这个类来访问 articles 表：

```php
File: 23.php

<?php
// Include the DataObjects_Articles class
```





```php
require_once 'ExampleApps/DataObject/Articles.php';

// Parse the database ini file
$dbconfig = parse_ini_file('db_dataobject.ini', true);

// Load Database Settings
// (note main PEAR class is loaded by Articles.php)
foreach ($dbconfig as $class => $values) {
    $Options = &PEAR::getStaticProperty($class, 'options');
    $Options = $values;
}

// Instantiate the DataObject_Articles class
$articles = new DataObject_Articles();

// Assign a value to use to search the 'Author' column
$articles->author = 'Kevin Yank';

// Perform the query
$articles->find();

echo 'Kevin has written the following articles:<br />';

// Loop through the articles
while ($articles->fetch()) {
    echo ' - ' . $articles->title . ', published: ' .
        date('jS M Y', $articles->published) . '<br />';
}
?>
```

首先，SQL 在哪里？没有 SQL ——太棒了！parse_ini_file 函数由 PHP 提供（详情见第 4 章），用于从我们的 db_dataobject.ini 配置文件中获取变量。foreach 循环会在我们实例化其自动生成的子类 DataObject_Articles 时，将所需变量提供给 DB_DataObject。通过为 $articles 对象的 author 属性赋值，我们为 DataObject_Articles 在查询数据库时应使用的 WHERE 条件做好了准备。查询实际上是通过调用 find 方法执行的（有关详细信息，请参阅 DB_DataObject 文档），该方法反过来执行以下查询：

```sql
SELECT * FROM articles WHERE articles.author = 'Kevin Yank'
```

要遍历结果，我们使用 fetch 方法。调用它时，fetch 会用当前行的结果填充 $articles 对象的属性。这样我们就可以通过属性名再次访问它们，例如 `$articles->title`。

还提供了其他方法来使查询更复杂，例如 `whereAdd` 方法：

```php
// Instantiate the DataObject_Articles class
$articles = new DataObject_Articles();

// Assign a value to use to search the 'Author' column
$articles->author = 'Kevin Yank';

// Add a where clause
$articles->whereAdd('published > ' . mktime(0, 0, 0, 5, 1, 2002));

// Perform the query
$articles->find();
```

这样我们就可以向 WHERE 子句添加进一步条件：

```sql
SELECT * FROM articles
WHERE published > 1020204000 AND articles.author = 'Kevin Yank'
```

还有其他类似的方法，因此如果这些方法无法提供您需要的内容，您可以使用 `query` 方法来执行手动编写的查询。请注意，如果您发现自己需要使用 `query` 方法，最好为生成的 `DataObject` 类创建一个子类，并将查询封装在一个准确描述它的有用方法名称中。

`DB_DataObject` 还能有效处理表连接，虽然与上面的示例相比稍微详细一些，但与手动编写复杂的连接查询相比，它肯定是一个省时的方法。

我们对 `DB_DataObject` 的简短介绍到此结束，但本节应该让您对它能为您做什么有了一些了解。最大的优势是，它使使用 SQL 查询数据库变得不那么令人疲惫且不易出错。此外，通过将对特定表的访问集中在单个类中，它有助于简化对表结构更改的处理。

## 进一步阅读

- MySQL 入门: http://www.devshed.com/Server_Side/MySQL/Intro/
  本文提供了将 SQL 与 MySQL 配合使用的扎实总结。

- 把我的 MySQL 命令行还给我!: http://www.sitepoint.com/article/627
  凯文·扬克展示了如何组合一个 PHP 脚本，该脚本可用于通过网页模拟 MySQL 命令行。

- 优化您的 MySQL 应用程序: http://www.sitepoint.com/article/402
  这份实用教程讨论了 MySQL 中索引的使用以及如何利用它们来提高性能。

- 生成 PHP 数据库访问层: http://freshmeat.net/articles/view/843/
  这篇文章概述了持久层及相关代码生成，并指向一些有用的工具。

- Zend 全文搜索教程: http://www.zend.com/zend/tut/tutorial-Ferrara.php
  该教程详细介绍了 FULLTEXT 搜索。

- 开始使用 MySQL 全文搜索: http://www.devarticles.com/art/1/195
  这份优秀的教程再次详细介绍了 FULLTEXT 搜索。

- 使用 MySQLDump 进行备份: http://www.sitepoint.com/article/678
  本教程探讨了 mysqldump 实用程序的方方面面。

- 生成 PHP 数据访问层: http://freshmeat.net/articles/view/843/
  该教程从相当广泛的角度探讨了 PHP 中的数据库持久层，并推荐了提供此功能的一个或两个开源项目。

# 4 文件

数据库是存储信息的绝佳工具，因为它们速度快，且借助 SQL 易于导航。不过，有时您需要访问存储在文件中的数据，无论是图像、配置信息，甚至是远程服务器上的网页。PHP 通过其强大的文件函数集合使此类工作变得轻松。唯一困难的部分是为工作选择合适的工具。

## 关于安全的一句话

在滥用 PHP 的文件函数之前，请仔细考虑您正在做什么：您将把操作系统中的文件公开到网页上，而该网页将暴露在互联网上。反复检查访问文件的代码——寻找逻辑中的“漏洞”，这些漏洞可能会允许对文件进行不必要的访问。

特别是在允许通过 URL 标识文件和目录，或从网站上传或下载文件时，请格外小心。此警告也适用于 PHP 的 include 命令，这些命令可用于执行从远程 Web 服务器包含的脚本，例如 include 'http://www.hack-er.com/bad_script.txt';。

我将在每个解决方案中指出潜在的危险，以便您小心谨慎地学习编写安全代码。

为了演示，我保存了凯文·扬克的文章《使用 PHP 4.2 编写安全脚本》([1]) 的可打印版本副本，我们将使用 PHP 的文件函数对其进行操作。该文件保存为 writeSecureScripts.html。

## 如何读取本地文件？

首先是 PHP 的 file 函数，它使用换行符将文件读入数组，以指示新数组元素应从何处开始。这是一个示例：

```php
<?php
// Read file into an array
$file = file('demo/writeSecureScripts.html');

// Count the number of lines
$lines = count($file);

// Initialise $alt
$alt = '';

// Loop through the lines in the file
for ($i=0; $i<$lines; $i++) {
    // Creates alternating background color
    if ($alt == '#f5f6f6') {
        $alt = '#ffffff';
    } else {
        $alt = '#f5f6f6';
    }

    // Display the line inside a div tag
    echo '<div style="font-family: verdana;
    font-size: 12px;
    background-color: ' . $alt . ';">';
    // Use htmlspecialchars to see the raw HTML
    echo $i . ': ' . htmlspecialchars($file[$i]);
    echo "</div>\n";
}
?>
```

噢，瞧！文件出现在一个格式良好的页面上，您可以逐行检查，如图 4.1 所示。

### 图 4.1. 原始 HTML

![](img/5b6cdf7cf4cf53e30b19e047895dc464_133_0.png)

自 PHP 4.3 起，一个名为 file_get_contents 的新函数可以将文件直接读入字符串，而无需将其拆分。例如：

```php
<?php
// Read file into a string
$file = file_get_contents('demo/writeSecureScripts.html');

// Strip the HTML tags from the file
$file = strip_tags($file);
?>
<form>
<textarea
 style="font-family: verdana;
 font-size: 12px;
 width: 400px;
 height: 300px;">
<?php
 // Display the file
 echo htmlspecialchars($file);
 ?>
</textarea>
</form>
```

文件内容现在显示在 HTML 文本区域中，已剥离所有 HTML 标签，如图 4.2 所示。

### 图 4.2. 原始文本

![](img/5b6cdf7cf4cf53e30b19e047895dc464_134_0.png)




另一个选项是 readfile 函数，它会获取文件内容并直接在屏幕上显示：

```php
<?php
// Read file and display it directly
readfile( 'demo/writeSecureScripts.html' );
?>
```

一行代码按原样显示文件，如图 4.3 所示。

### 图 4.3. 使用 readfile 进行直接输出

![](img/5b6cdf7cf4cf53e30b19e047895dc464_135_0.png)

当然，因为我只下载了 HTML，而没有下载关联的图片和 CSS 文件，所以外观与原件不太一样。

## 文件句柄

上述文件函数只需指向要读取的文件即可，使用相对于执行该函数的 PHP 脚本的路径。PHP 中的大多数文件函数使用略有不同的机制来“连接”到文件，这与连接数据库非常相似；该过程使用 fopen 函数来“连接”，使用 fclose 来“断开连接”。使用 fopen 时，返回的值是一个 PHP 文件指针，即文件的句柄。当使用 fopen 连接到文件时，必须指定文件路径以及访问文件的模式，例如 r 表示只读。

```php
// Open a file for reading
$fp = fopen($filename, 'r');
```

可用的各种模式在手册[2]中说明。

## 二进制文件修饰符

与 Linux 不同，Windows 区分二进制文件和 ASCII 文件。可以使用额外的修饰符 b 向 PHP 标识二进制文件，以便在 Windows 上正确处理它们。

```php
// Open a binary file for reading
$fp = fopen($filename, 'rb');
```

即使你编写的代码当前用于基于 Unix 的系统，为二进制文件实现 b 修饰符也是值得的，以确保可移植性。

在旧版本中，fread 函数可以作为 file_get_contents 的替代品：

```php
<?php
// Variable to store the location of the file
$location = 'demo/writeSecureScripts.html';

// Open the file handle for reading
$fp = fopen($location, 'r');

// Read the complete file into a string
$file = fread($fp, filesize($location));

// Close the file handle
fclose($fp);

echo $file;
?>
```

[2] http://www.php.net/fopen

这与使用 `readfile` 时一样显示整个文件，并生成图 4.3 中所示的显示效果。本示例主要用于简单演示文件句柄的用法。请注意，使用 `fread` 时，第二个参数是从文件开头开始应读取的字节大小。对于此参数，我使用了 `filesize` 函数，它会告诉我文件的总大小。通常，`fread` 仅适用于读取文件的有限部分；要获取完整文件，通常使用 `file_get_contents` 或 `file` 会更高效，具体取决于您的需求。

## 节省内存

迄今所见内容对于小文件来说足够了。然而，类似于对 `SELECT * FROM table` 之类查询的论点也适用于读取文件；如果使用 `file` 或 `file_get_contents` 读取大文件，PHP 将不得不用其内容填充大量内存。

要解决这个问题，可以采用不同的方法来读取文件内容：分阶段读取文件，并在读取过程中对内容进行操作。此方法使用类似 `fgets` 的函数：

```php
<?php
// Open the file handle for reading
$fp = fopen('demo/writeSecureScripts.html', 'r');

// Loop until the end of the file
while (!feof($fp)) {
    // Get a chunk to the next linefeed
    $chunk = fgets($fp);
    echo $chunk;
}

// Close the file handle!
fclose($fp);
?>
```

连接照常打开。接下来，我们使用一个 while 循环，只要 `feof` 函数返回 FALSE，循环就会继续。如果到达文件末尾，或文件句柄出错（例如连接丢失，这在远程文件中可能发生），`feof` 将返回 TRUE。

接下来，我们使用 `fgets` 获取文件的一个“块”，从当前位置开始，一直读取到下一个换行符。我们会得到返回的字符串，而 `fgets` 会相应地将文件句柄的内部 PHP 文件指针向前移动。

使用文件句柄读取文件还有更多函数。其中一个是 `fgetss`（注意双写的 s），它几乎与 `fgets` 完全相同，但会剥离找到的任何 HTML 标签，方式与 `strip_tags` 函数相同。另一个是 `fscanf`，它以与 `printf` 相同的方式格式化文件的输出。闲暇时浏览文件系统函数[3]以寻找“宝贝”非常值得。

PHP 提供了相当简单的文件处理函数，但更好的选择是使用 PEAR::File。它提供了更简单的 API 来读取文件，并允许您利用其他 PEAR 类来执行诸如在文件系统中查找文件和修改 .htaccess 文件等任务。PEAR::File 可在 PEAR 网站[4] 上找到；此处使用的版本是 1.0.3（有关如何安装 PEAR 模块的说明，请参见附录 D）。

PEAR::File 特别有用的一个功能是，它允许在读取文件时对其加锁，这意味着您不会遇到两个人同时处理同一文件时发生冲突的问题。PEAR::File 还能很好地处理错误。

![](img/5b6cdf7cf4cf53e30b19e047895dc464_138_0.png)

## 将数据库交给专家

虽然可以以与在数据库中存储数据大致相同的方式在文件中存储数据（尤其是考虑到 PHP 提供的锁定机制），但通常最好将此类工作交给 MySQL。在 PHP 中编写自己的数据库是一个非常复杂的问题，除非万不得已，否则没有必要“重复造轮子”。

让我们看看如何使用 PEAR::File 读取文件的完整内容：

```php
<?php
// Include PEAR::File
require_once 'File.php';

// Read the entire file and display, using a shared read lock
echo File::readAll('demo/writeSecureScripts.html',
    FILE_LOCK_SHARED);
?>
```

[3] http://www.php.net/filesystem
[4] http://pear.php.net/package-info.php?pacid=43

目前，PEAR::File 对基于换行符逐行处理文件的过程处理得不是很好。我希望未来版本能改进这一点；请查看下一个关于写入文件的解决方案中它的表现。

## 如何修改本地文件？

现在您已经了解了如何读取文件内容并熟悉了文件句柄，那么如何更新文件呢？使用 PHP 同样很简单。让我们制作该 HTML 文件的文本版本：

```php
<?php
// Fetch a file into an array
$lines = file('demo/writeSecureScripts.html');

// Open file for writing (create if doesn't exist)
$fp = fopen('demo/writeSecureScripts.txt', 'w');

// Loop through lines of original
foreach ($lines as $line) {
    // Strip out HTML
    $line = strip_tags($line);
    // Write the line
    fwrite($fp, $line);
}

// Display the new file
echo '<pre>';
echo file_get_contents('demo/writeSecureScripts.txt');
echo '</pre>';
?>
```

请注意我们使用 fopen 打开新文件时所用的模式。模式 w 意味着写入文件的内容将从开头开始，覆盖已存在的任何内容。如果我们改用 a，则新内容将追加到文件中，保留原有内容。无论哪种情况，如果文件不存在，则会创建该文件。

以下是使用 PEAR::File 实现相同效果的方法，它还提供在写入文件时锁定文件的额外好处：

```php
<?php
// Include PEAR::File
require_once 'File.php';

// Fetch a file into an array
$htmlVersion = File::readAll('demo/writeSecureScripts.html');

// Strip out HTML
$txtVersion = strip_tags($htmlVersion);

// Write to file and lock while writing
File::write('demo/writeSecureScripts2.txt', $txtVersion,
    FILE_MODE_WRITE, LOCK_EX);

// Now unlock the file
File::unlock('demo/writeSecureScripts2.txt', FILE_MODE_WRITE);

// Display the new file
echo '<pre>';
echo File::readAll('demo/writeSecureScripts2.txt');
echo '</pre>';
?>
```

请注意，在基于 Unix 的 Web 服务器上，PHP 通常以 www 或 nobody 等用户身份运行，该帐户权限非常有限，且不特定属于您。PHP 创建的文件需要放置在该用户具有写入权限的目录中。

要使文件或目录可读可写，请使用此命令：

```
chmod o=rw <directory | file>
```

如果还需要执行该文件（例如它是 PHP 脚本），请使用以下命令：

```
chmod o=rwx <directory | file>
```

## 保护敏感文件

如果您使用共享服务器，以这种方式使目录可读可写，意味着服务器上有帐户的其他人将能够读取和修改这些目录中的内容。请注意您放入其中的信息类型！

您的 Web 主机应该能够帮助您解决任何安全问题。




## 如何获取本地文件的信息？

PHP 自带一系列函数，可帮助你获取文件信息。例如，我们可以检查文件是否存在，并获取其大小：

```
<?php
// Function to convert a size to bytes to large units
function fileSizeUnit($size)
{
    if ($size >= 1073741824) {
        $size = number_format(($size / 1073741824), 2);
        $unit = 'GB';
    } else if ($size >= 1048576) {
        $size = number_format(($size / 1048576), 2);
        $unit = 'MB';
    } else if ($size >= 1024) {
        $size = number_format(($size / 1024), 2);
        $unit = 'KB';
    } else if ($size >= 0) {
        $unit = 'B';
    } else {
        $size = '0';
        $unit = 'B';
    }

    return array('size' => $size, 'unit' => $unit);
}

$file = 'demo/writeSecureScripts.html';
// Does the file exist
if (file_exists($file)) {
    echo 'Yep: ' . $file . ' exists.<br />';
} else {
    die('Where has: ' . $file . ' gone!<br />');
}

// Use a more convenient file size
$size = fileSizeUnit(filesize($file));

// Display the result
echo 'It\'s ' . $size['size'] . '' . $size['unit'] .
' in size.<br />';
?>
```

我们开头使用的 fileSizeUnit 函数有助于让 PHP 的 filesize 函数返回的结果更易读。

这里是输出：

```
Yep: demo/writeSecureScripts.html exists.
It's 16.28 KB in size.
```

PHP 还能提供许多其他文件信息片段：

```
<?php
$file = 'demo/writeSecureScripts.html';

// Is it a file? Could be is_dir() for directory
if (is_file($file)) {
    echo 'Yep: ' . $file . ' is a file<br />';
}

// Is it readable
if (is_readable($file)) {
    echo $file . ' can be read<br />';
}

// Is it writable
if (is_writable($file)) {
    echo $file . ' can be written to<br />';
}

// When was it last modified?
$Modified = date("D d M g:i:s", filemtime($file));
echo $file . ' last modified at ' . $Modified . '<br />';

// When was it last accessed?
$Accessed = date("D d M g:i:s", fileatime($file));
echo $file . ' last accessed at ' . $Accessed . '<br />';
?>
```

这里是输出：

```
Yep: demo/writeSecureScripts.html is a file
demo/writeSecureScripts.html can be read
demo/writeSecureScripts.html can be written to
demo/writeSecureScripts.html last modified at Sun 09 Mar 12:08:02
demo/writeSecureScripts.html last accessed at Sun 09 Mar 2:35:47
```

## 清除文件统计缓存

PHP 会缓存文件信息函数的结果以提高性能。不过，有时有必要清除该缓存；这可以通过 clearstatcache 函数来实现。

## 如何使用 PHP 读取目录？

特别是对于基于 Web 的文件管理器，使用 PHP 浏览目录内容非常方便。这有两种基本方法；涉及的 PHP 函数在 PHP 手册[5]中有说明。

```
<?php
// Open the current directory
$location = './';
// Open current directory
$dp = opendir($location);
// Loop through the directory
while ($entry = readdir($dp)) {
    // If $entry is a directory....
    if (is_dir($location . $entry)) {
        echo '[Dir] ' . $entry . '<br />';
    } else if (is_file($location . $entry)) {
        echo '[File] ' . $entry . '<br />';
    }
}
// Close it again!
closedir($dp);
?>
```

[5] http://www.php.net/dir

这里是输出：

```
[Dir] .
[Dir] ..
[File] 1.php
[File] 10.php
[File] 11.php
[File] 12.php
[File] 13.php
[File] 14.php
[File] 15.php
[File] 16.php
[File] 17.php
[File] 18.php
[File] 19.php
[File] 2.php
[File] 3.php
[File] 4.php
[File] 5.php
[File] 6.php
[File] 7.php
[File] 8.php
[File] 9.php
[Dir] demo
[File] extensions.ini
[Dir] ftploads
[File] sample.zip
```

另一种方法是使用内置于 PHP 的“伪”类 dir 函数。在用法上，它几乎完全相同：

```
File: 12.php
<?php
// Specify current directory
$location = './';
// Open current directory
$dir = dir($location);
// Loop through the directory
while ($entry = $dir->read()) {
// If $entry is a directory...
if (is_dir($location . $entry)) {
echo '|Dir| ' . $entry . '<br />';
}
// If $entry is a file...
} else if (is_file($location . $entry)) {
echo '[File] ' . $entry . '<br />';
}
}
// Close it again!
$dir->close();
?>
```

选择哪种纯粹是个人偏好问题。

## 如何在线显示 PHP 源代码？

有时你可能想显示某个文件的源代码，例如在为他人发布代码时。不过，以这种方式操作时必须极其谨慎——你可能会不经意间泄露比预期更多的信息，例如数据库用户名和密码。

需要指出，我这里并不主张出于安全考虑而隐藏代码。代码应该从一开始就编写得安全。为了防止他人发现其中的漏洞而隐藏代码，是走向灾难的配方；最终，有人会发现你隐藏了什么，而且更糟糕的是，你很可能会对他们正在利用你的安全漏洞一无所知。

PHP 提供了一个名为 highlight_string 的非常方便的函数来显示代码，它使用 php.ini 中定义的格式以美观的方式显示 PHP 代码。与此函数配套的 highlight_file 让事情变得更加简单，只需传递一个文件名即可显示。

下面是一个显示目录中所选文件源代码的脚本：

```
<?php
// Define an array of allowed files - VERY IMPORTANT!
$allowed = array('3.php', '4.php', '6.php', '10.php');

// If it's an allowed file, display it.
if (isset($_GET['view']) && in_array($_GET['view'], $allowed)) {
    highlight_file($_GET['view']);
} else {
    // Specify current directory
    $location = './';
// Open current directory
$dir = dir($location);

// Loop through the directory
while ($entry = $dir->read()) {
    // Show allowed files only
    if (in_array($entry, $allowed)) {
        echo '<a href="' . $_SERVER['PHP_SELF'] .
        '?view=' . $entry . '">' . $entry . "</a><br />\n";
    }
}

// Close it again!
$dir->close();
}
?>
```

请注意，无论在显示目录内容还是单个文件源代码时，我都非常小心地只允许访问指定文件。上面的示例应该能让你了解在 PHP 中构建文件管理系统是多么容易。

精美呈现的脚本如图 4.4 所示。亲自试一下，看看各种 PHP 语法片段的彩色高亮效果！

## 图 4.4. 返回源代码

```
<?php
$file = 'demo/writeSecureScripts.html';

// Is it a file? Could be is_dir() for directory
if ( is_file ( $file ) )
   echo ( 'Yep: '.$file.' is a file<br />' );

// Is it readable
if ( is_readable ( $file ) )
   echo ( $file.' can be read<br />' );

// Is it writeable
if ( is_writeable ( $file ) )
   echo ( $file.' can be written to<br />' );

// When was it last modified?
$modified = date ( "D d M g:i:s",filemtime($file) );
echo ( $file.' last modified at '.$modified.'<br />' );

// When was it last accessed?
$accessed = date ( "D d M g:i:s",fileatime($file) );
echo ( $file.' last accessed at '.$accessed.'<br />' );
?>
```

在 PHP 4.2.0 或更高版本中，如果向 highlight_string 或 highlight_file 传递第二个参数 TRUE，则它将把结果作为字符串返回，而不是直接显示文件。

## 如何将配置信息存储在文件中？

某些在整个网站中反复使用的信息，例如数据库连接设置，最好存储在单个文件中。如果需要将代码迁移到另一个网站，你只需修改一次设置，而不是成百上千次。实现这一点的最简单方法是在包含文件中创建变量，然后在代码中包含该文件。但有时编辑 PHP



files 会让你的代码用户感到不安，出于安全考虑，通常有必要能够使用不同的扩展名来识别配置文件，例如，可以使用 .htaccess 对其进行保护。方便的替代方案是 PHP 的 parse_ini_file 函数，它解析使用与 php.ini 相同格式的文件。

请参考以下文件：

```
File: demo/example.ini

; Settings to connect to MySQL
[Database_Settings]
host=localhost
user=harryf
pass=secret
dbname=sitepoint

; Default look of the site
[Preferences]
color=blue
size=medium
font=verdana
```

使用 parse_ini_file，PHP 将读取内容并使用它们构建一个二维数组：

```
File: 14.php

<?php
$iniVars = parse_ini_file('demo/example.ini', TRUE);

echo '<pre>';
print_r($iniVars);
echo '</pre>';
?>
```

请注意，我们用于 parse_ini_file 的第二个布尔参数告诉它文件包含子节（[Database_Settings] 和 [Preferences]），因此应使用这些子节来构建多维数组。

以下是输出：

```
Array
(
    [Database_Settings] => Array
    (
        [host] => localhost
        [user] => harryf
        [pass] => secret
        [dbname] => sitepoint
    )
    [Preferences] => Array
    (
        [color] => blue
        [size] => medium
        [font] => verdana
    )
)
```

使用我们在第 3 章中创建的 MySQL 类连接到 MySQL 现在可以这样实现：

```
$iniVars = parse_ini_file('demo/example.ini', TRUE);

$mysql = &new MySQL(
    $iniVars['Database_Settings']['host'],
    $iniVars['Database_Settings']['user'],
    $iniVars['Database_Settings']['pass'],
    $iniVars['Database_Settings']['dbname']
);
```

## 如何从远程服务器访问文件？

迄今为止我还没告诉你的是，在大多数情况下，PHP 可以通过 Internet 以几乎与访问本地文件完全相同的方式访问远程服务器上的文件。这里的主要限制是，你不能使用 `filesize` 函数，或其他用于获取文件信息的函数。

重用“如何读取本地文件？”中的 5.php，我们可以这样直接从 SitePoint 获取一直在使用的原始文件：

```
<?php
// Open the file handle for reading
$fp = fopen('http://www.sitepoint.com/print/758', 'r');
// Loop while the connection is good and not at end of file
while (!feof($fp)) {
    // Get a chunk to the next linefeed
    $chunk = fgets($fp);
    echo $chunk;
}

// Close the file handle!
fclose($fp);
?>
```

我们所要做的就是将 fopen 函数指向的位置改为一个 URL！

这种方法的问题是，我们采用了一个针对本地文件系统设计的函数，并用它来访问远程 Web 服务器。fopen 不太擅长处理你在 Internet 上通常会遇到的问题，例如超时，并且无法提供远程连接可能需要的详细错误报告。它还会删除远程 Web 服务器发送的 HTTP 响应头，这些头有时是必需的——例如，在 Web 服务中——并且会自动处理请求头，而你可能需要自己控制请求头。

让我们看看替代方案 fsockopen：

```
<?php
$host = 'www.sitepoint.com'; // Remote host
$port = '80'; // Port number
$timeout = '10'; // Timeout in seconds
$uri = '/print/758'; // Page to fetch

// Open remote socket
if (!$fp = fsockopen($host, $port, $errNo, $errMsg, $timeout)) {
    die('Error connecting: ' . $errNo . ' - ' . $errMsg);
}

// Build an HTTP request header
$requestHeader = "GET " . $uri . " HTTP/1.1\r\n";
$requestHeader .= "Host: " . $host . "\r\n\r\n";

// Send the request header
fputs($fp, $requestHeader);

// Loop while the connection is good and not at end of file
while (!feof($fp)) {
    // Get a chunk to the next linefeed
    $chunk = fgets($fp);
    echo $chunk;
}

// Close the file handle!
fclose($fp);
?>
```

查看上述脚本的原始输出，我们看到页面顶部有以下 HTTP 头：

```
HTTP/1.1 200 OK
Date: Sun, 09 Mar 2003 18:06:59 GMT
Server: Apache/1.3.27 (Unix) PHP/4.3.1
X-Powered-By: PHP/4.3.1
Connection: close
Content-Type: text/html
```

对 HTTP 协议的详细分析超出了本书的范围；不过，本章末尾建议了一些参考资料。

## 如何在 PHP 中使用 FTP？

PHP 的一大优点是其内置或仅需扩展即可使用的功能数量庞大；文件传输协议 (FTP) 也不例外。使用 PHP 的 FTP 功能，可以让 PHP 脚本充当 FTP 服务器的客户端。这对于从为 FTP 文件存储库构建 Web 接口，到开发从 PHP 开发环境更新站点的工具等，都非常有用。要使用 FTP 函数，需要确保主机已启用 PHP 的 FTP 功能（参见附录 B）。

![](img/5b6cdf7cf4cf53e30b19e047895dc464_151_0.png)

### FTP 不安全

无论通过何种方式连接到普通 FTP 服务器，你提供的用户名和密码都会以明文形式发送到服务器。这些信息可能会被任何在你与连接服务器之间“插入”的数据包嗅探器读取。请务必定期更改密码，并且一般来说，在有更好的替代方案时，尽量避免使用 FTP。

如果你有 SSH 权限访问站点并且使用 Windows，WinSCP[6] 是通过安全连接传输文件的一个好工具。

让我们从一个简单的示例开始：

```
<?php
// Set time limit to infinite
set_time_limit(0);

// Define server and target directory
$ftpServer = 'ftp.uselinux.org';
$targetDir = '/pub/redhat/updates/8.0/en/os/i386';

// Connect server
if (! $ftp = ftp_connect($ftpServer, 21, 30)) {
    die('Connection failed');
}

// Login anonymously
if (! ftp_login($ftp, 'anonymous', 'you@yourdomain.com')) {
    die('Login failed');
}
```

首先，我们使用 set_time_limit 函数删除脚本执行时间限制。在这个特定示例中，默认的 30 秒 PHP 脚本执行时间应该足够长，但对于涉及文件传输的脚本，可能确实需要更长的执行时间。

我们使用 ftp_connect 函数打开到 FTP 服务器的连接，指定服务器的端口号（可选：默认为 21）以及 PHP 放弃连接尝试前的秒数（默认为 90）。

之后，ftp_login 函数允许我们登录到 FTP 服务器。由于它是公共服务器，你可以以匿名用户身份登录（将电子邮件地址作为密码提供）。不过，这也可能是你 Web 服务器上的 FTP 帐户，在这种情况下，你需要提供有效的用户名和密码。

以下是示例的其余部分：

```
// Change directory
if (! ftp_chdir($ftp, $targetDir)) {
    die ('Unable to change directory to: ' . $targetDir);
}

// Display the remote directory location
echo '<b>Current Directory:</b> <code>' . ftp_pwd($ftp) .
     '</code><br />';

echo '<b>Files Available:</b><br />';

// Get a list of files on the server
$files = ftp_nlist($ftp, '.');

// Display the files
foreach ($files as $file) {
    echo $file . '<br />';
}
?>
```

接下来，我们使用 ftp_chdir 更改目录。使用 FTP 时，重要的是要记住，FTP 相关操作的根目录将是你登录服务器时所在的目录，而不是服务器的真正根目录。因此，在适当的时候请务必指定绝对路径。

为了表明我们在正确的位置，我们使用 ftp_pwd 显示当前工作目录。ftp_nlist 函数返回当前目录的文件数组，我们可以显示该数组。

列表应该如下所示：

```
Current Directory: /pub/redhat/updates/8.0/en/os/i386
Files Available:
lynx-2.8.5-7.1.i386.rpm
galeon-1.2.6-0.8.0.i386.rpm
ggv-1.99.9-5.i386.rpm
gv-3.5.8-19.i386.rpm
xinetd-2.3.7-5.i386.rpm
pam-0.75-46.8.0.i386.rpm
kamera-3.0.3-5.i386.rpm
pam-devel-0.75-46.8.0.i386.rpm
vnc-3.3.3r2-39.2.i386.rpm
```

这是 PHP FTP 函数实际运行的一个简单示例。完整的函数列表可在 PHP 手册[7]中找到。

在 PEAR::NET_FTP 中，我们有一个方便的类，可确保数据以正确的模式（ASCII 或二进制）传输，并解决与递归上传相关的问题。




以及在需要将目录及其子目录从一个系统传输到另一个系统时的下载。

例如，以下代码连接到 FTP 服务器上的远程目录，并将包括子目录在内的内容复制到本地计算机上的某个目录¹：

```php
<?php
// Set time limit to infinite
set_time_limit(0);

// Include PEAR::Net_FTP
require_once 'Net/FTP.php';

// Define server, username and password
$ftpServer = 'ftp.uselinux.org';
$ftpUser = 'anonymous';
$ftpPass = 'user@domain.com';

// Local Directory to place files
$localDir = 'ftpdownloads/';

// Remote Directory to fetch files from
$remoteDir = '/pub/software/web/html-utils/';

// Instantiate Net_FTP
$ftp = new Net_FTP();

// Set host and login details
$ftp->setHostname($ftpServer);
$ftp->setUsername($ftpUser);
$ftp->setPassword($ftpPass);

// Connect and login
$ftp->connect();
$ftp->login();

// Specify the extensions file
$ftp->getExtensionsFile('extensions.ini');

// Get the remote directory contents
if ($ftp->getRecursive($remoteDir, $localDir)) {
    echo 'Files transferred successfully';
} else {
    echo 'Transfer failed';
}
?>
```

¹显然，如果没有安全保护，你可不想把这个放在你的网站上。

请注意，Net_FTP 的 getExtensionsFile 方法允许你指定一个文件，用于定义特定的文件扩展名（例如 .gif 和 .jpg）为二进制或 ASCII 格式，以确保它们以正确的方式传输。getRecursive 方法会获取指定远程目录的内容，包括其子目录。

假设你有权在服务器上放置文件，可以使用 putRecursive 方法轻松将相同操作反向应用。这在本地开发系统与网站之间传输项目时非常有用，尤其是在从命令行使用 PHP 时。

凭借根据扩展名正确传输文件的能力，Net_FTP 也非常适合单个的“put”和“get”文件操作，因为它消除了你需要自己设置正确传输模式的必要。

## 如何使用 PHP 管理文件下载？

开发者在构建发布供下载文件的网站时，经常会遇到如何管理这些文件的问题。也许有些文件不应公开提供。你可能还希望在访客通过 Web 表单提供其详细信息后再交付文件。处理下载可能不仅仅是将文件存储在公开目录中并从站点链接到它。

处理下载的诀窍是使用几个特殊的 HTTP 头部，让 PHP 为你“提供”文件：

```php
<?php
// Specify a file to download
$fileName = 'sample.zip';
$mimeType = 'application/zip';
if (strpos($_SERVER['HTTP_USER_AGENT'], 'MSIE 5') or
    strpos($_SERVER['HTTP_USER_AGENT'], 'Opera 7'])) {
    $mimeType = 'application/x-download';
}
// Tell the browser it's a file for downloading
header('content-disposition: attachment; filename=' . $fileName);
header('content-type: ' . $mimeType);
header('content-length: ' . filesize($fileName));

// Display the file
readfile($fileName);
?>
```

content-disposition 头部告诉浏览器将文件视为下载（即不在浏览器窗口中显示），并为其指定文件名。content-type 头部也告诉浏览器正在发送的文件类型。在大多数情况下，应选择与所发送文件类型相匹配的值；但是，Internet Explorer 5 和 Opera 浏览器有一个不良习惯，即无论 content-disposition 头部如何，都会在浏览器中显示已识别类型的文件，因此我们对这些浏览器将 MIME 类型设置为虚构的值 application/x-download。最后，content-length 头部告诉浏览器文件的大小，以便它能够显示下载进度条。

## 首先发送 HTTP 头部

请记住，头部必须在发送任何其他内容到浏览器之前传送。

请注意，PHP 的输出控制函数在此处很有帮助，因为它们允许你按正确的顺序将内容发送到浏览器：你可以“保留”PHP 已经发送到输出的内容，同时让头部通过。有关输出控制的更多详细信息，请参见第 II 卷第 5 章。

既然文件传输已受你控制，你可以将此功能集成到身份验证系统中，例如控制谁可以下载文件。

## 文件分发策略

互联网中无法解决的问题之一是如何最好地从网站分发文件。例如，如果你以 JPEG 格式出售艺术品，你将如何处理从客户处接受付款，然后仅允许他们下载已付款的图片这一过程？你如何确保他们不会重新分发购买的图片？客户可以下载已付款的图片多少次？

没有完美的解决方案。如果有人决定复制他们从你这里购买的图片并在你不知情的情况下重新分发这些副本，该怎么办？除非你提供专门为分发目的修改过的文件（例如受水印保护的图像文件），否则几乎不可能阻止他们这样做。

分发的几种不同策略如下：

- [ ] 通过电子邮件发送文件。这对于小文件很有用，因为它几乎可以保证送达，但许多电子邮件系统会限制用户可接收的文件大小（通常为一两兆字节）。

- [ ] 为客户提供唯一链接，他们可以在有限的时间内（例如一周）使用该链接下载文件。如果下载尝试失败（例如，客户在下载过程中失去 Internet 连接），此策略允许他们重试。可以生成一个唯一的随机数，并将其用于下载 URL 中。该数字与数据库中的条目对应，并在指定的时间段后过期。这至少可以限制文件被下载的次数，并应有助于防止通过相同 URL 重新分发文件。PayPal Antifraud[8] 等服务采用此方法。

- [ ] 为客户提供用户名和密码组合，供其登录网站并下载自己的文件。这种方法对 PHP Architect[9] 网站尤其有效，该网站使用它以 Adobe Acrobat 格式分发 PHP Architect 杂志。Acrobat 文件“即时生成”，并使用客户登录网站时使用的相同密码进行保护。这显然会阻止客户重新分发杂志，因为他们将不得不泄露自己的密码。

如我所说，这个问题没有完美的解决方案。但是，如果在正在下载的文件中内置某种形式的安全性（例如软件的许可证密钥），可以实现更强的保护。

## 如何使用 PHP 创建压缩的 ZIP/TAR 文件？

也许你有一个包含许多文件、不同类型的文件以及子目录的目录。可能存在需要创建整个目录下载并保留其原始结构的情况。在基于 Unix 的系统上，实现此目的的典型命令行方法是首先创建一个“归档”文件（例如 .tar 文件（.tar 文件是“磁带归档”，最初设计用于帮助将文件系统备份到磁带上）），然后使用 gzip 或 bzip2 压缩该文件。如果你有一个名为 mywork 的目录想要将其存储为单个压缩文件，可能会在命令行中输入以下内容：

```
tar cvf mywork.tar ./mywork
gzip mywork.tar
```

这会生成一个名为 mywork.tar.gz 的文件。要解压缩并提取文件，可以输入：

```
gunzip mywork.tar.gz
tar xvf mywork.tar
```

这会在当前工作目录下重新创建 mywork 目录。请注意，在典型的 Linux 发行版中，如果使用 ’z’ 标志，可以将上述示例合并在一行中：压缩 tar zcvf mywork.tar.gz ./mywork，提取 tar zxvf mywork.tar.gz。

使用 PHP 的 system 函数，你可以从 PHP 脚本中执行这些命令，前提是你的 Web 服务器有权限使用 tar 和 gzip/bzip2 可执行文件（但可能没有）。那么，如何从存储在数据库中的数据，或者 XML 文档中的节点创建归档文件呢？

多亏了 PEAR::Archive_Tar[10]，这一切都成为可能。基本功能允许你构建 .tar 文件；前提是已安装 zlib 或 bz2 扩展，你也可以压缩文件。

让我们使用本章前面处理过的一些文件创建一个归档文件：

[10] http://pear.php.net/Archive_Tar




# 5 文本操作

尽管我们生活在多媒体时代，但大多数 Web 内容都以最乏味却最有效的格式呈现：文本。作为 PHP 开发人员，您的大部分工作都会以某种形式操作文本——无论是 HTML、XML 还是其他格式——用于在您的网站上显示。

## 如何解决 HTML 文档中文本内容的问题？

学习 (X)HTML 通常相当容易，至少与面向对象编程语言等相比。不过，HTML 看起来几乎是欺骗性简单。它看起来比实际更复杂，特别是在即时生成 HTML 时。

在本解决方案中，我将探讨使用 PHP 构建 HTML 时可能遇到的一些常见问题，以及可用于帮助您解决这些问题的资源。

## 动态链接 URL

当它们被用作网页链接的一部分时，某些字符会导致尝试单击该链接的用户出现问题。以空格为例；URL 中包含的空格的准确数量可能会丢失，因为浏览器正在识别页面地址。但是，可以使用代码 %20 在 URL 中发送空格字符的表示形式。将特殊字符替换为适当代码的过程称为 **URL 编码**。

存在两种类型的问题字符：

- **保留字符**，它们在 URL 中已经具有特定用途，例如 ? 和 &
- **不安全字符**，根据 Web 浏览器和 Web 服务器，可能会以不可预测的方式处理

例如，假设您的数据库中有一个登录名为“Ben&Jerry”的用户。您构建了一个页面来查看该用户的个人资料。为了访问它，您决定使用数据库中的登录名构建一个链接。您最终可能会得到这样的链接：

```html
<a href="/index.php?view=profile&amp;user=Ben&Jerry">
View Ben&Jerry </a>
```

接收请求的 index.php 脚本将把 GET 变量 ($_GET['user']) 仅接收为“Ben”，而忽略“Jerry”（他可能不会高兴）。当脚本尝试在数据库中查找该名称时，显然会出现问题。

幸运的是，PHP 提供了 urlencode 函数来处理此情况。如果在渲染链接时将链接中包含的用户名通过 urlencode 传递，结果将如下：

```html
<a href="/index.php?view=profile&amp;user=Ben%26Jerry">
View Ben&Jerry </a>
```

请注意，链接中的用户名变为 Ben%26Jerry。脚本现在将把“Ben&Jerry”作为 $_GET['user'] 的值，并能够在数据库中找到该用户。

### 其他 URL 编码/解码函数

PHP 还提供了 urldecode 函数，在需要使用 PHP 解析 HTML 时非常有用。它还提供了 rawurlencode 和 rawurldecode 函数，这两个函数使用 + 字符而不是 %20 来标记空格。这是对 URL 编码的替代规范的结果。

在本章末尾，我推荐了一份进一步阅读的资料来源，详细介绍了 URL 编码的一般主题。

urlencode 和类似函数仅应在文本用于创建 HTML 文档时应用。不要被迷惑，在将文本存储到数据库之前对其进行修改！在上述示例中，我不得不以两种不同的格式呈现用户名。如果我改为在将用户名插入数据库之前应用 urlencode，那么每当我想以普通文本显示用户名时，我都需要应用 urldecode。在执行搜索数据库等操作时，我也会遇到问题；我需要更多代码来在两个版本之间进行转换。如果我们只是将文本“原样”插入数据库，并且仅在需要时对其进行编码，就可以避免所有这些问题。

### 表单字段和 HTML 内容

在处理带有预填充值（可能来自数据库）的 HTML 表单元素时，我们面临另一个难题。

想象一下，您有一个表单允许用户编辑其在您网站上的帐户详细信息，例如在线论坛中常见的“个人资料”页面。表单中有一个文本字段允许用户修改其“昵称”。该字段可能如下所示：

```html
<input type="text" name="nickname"
value="<?php echo $nickname; ?>" />
```

$nickname 变量的值将来自您的数据库。如果用户的昵称是“Joe Bloggs”，则没有问题。发送到浏览器的最终 HTML 将是：

```html
<input type="text" name="nickname"
value="Joe Bloggs" />
```

但如果有人使用类似“Joe “The Hacker” Bloggs”的昵称会怎样？表单元素最终将如下所示：

```html
<input type="text" name="nickname"
value="Joe "The Hacker" Bloggs" />
```

这对 Web 浏览器来说是个坏消息。最好，它们会显示一个仅包含名称“Joe”的表单字段；最坏，它们会完全打乱页面。

幸运的是，PHP 又来救场了！htmlspecialchars 函数将识别可能引起问题的字符，并将它们转换为特殊代码，以便浏览器将它们识别为内容的一部分。其中的字符


问题都涉及单引号 (')、双引号 (")、与号 (&) 以及大于号和小于号 (< 和 >)。

如果在输出之前先将 Joe 的昵称通过 htmlspecialchars 处理，输入字段将变为：

```html
<input type="text" name="nickname"
value="Joe &quot;The Hacker&quot; Bloggs" />
```

请注意，&quot; 现在替代了双引号作为昵称字段的值。浏览器会将这些显示为预期的双引号。

再次保存！

## HTML 中的换行

您可能知道，如果您有如下所示的一段 HTML：

```html
<p>Dear Sir or Madam,
This is my nicely formatted letter. I hope that
it really impresses you.
Look! I've started a new paragraph.
Yours faithfully,
Mike Format</p>
```

在 Web 浏览器中显示时，它看起来可能不太理想。在这种情况下，它看起来会像这样：

亲爱的先生或女士，这是我精心格式化的信件。我希望这能给您留下深刻印象。看！我开始新的一段了。您忠实的，Mike Format

在基于 PHP 的网站上，如果您希望用户无需了解太多 HTML 即可执行基本文本格式化，这可能会带来麻烦。

幸运的是，这次有 PHP 的 nl2br 函数可以提供帮助。下面是将 Mike 的信件通过 nl2br 处理后生成的 HTML：

```html
<p>Dear Sir or Madam,<br />
<br />
This is my nicely formatted letter. I hope that<br />
it really impresses you.<br />
<br />
Look! I've started a new paragraph.<br />
<br />
Yours faithfully,<br />
<br />
Mike Format</p>
```

Mike 可以继续用他的格式给人留下深刻印象！

![](img/5b6cdf7cf4cf53e30b19e047895dc464_167_0.png)

## 在 SELECT 时修改文本，而非在 INSERT 时

初学者常见的错误是，在将文本插入数据库时使用上述类型的函数。在应用程序的初始设计阶段，这可能看起来是个好主意。然而，这种方法以后可能会引起问题——例如，如果您决定以不同的格式显示文本。

以 nl2br 函数为例。这对于简单的 HTML 显示没问题，但如果您想允许用户在 textarea 表单字段中编辑文本呢？他们将面对换行符被移除并替换为 br 标签的文本。如果用户不希望编辑 HTML，他们可能会非常困惑。将 br 元素转换回换行符是一种可能，但会给您的代码增加复杂性和混乱。

通过仅在将内容从数据库获取后、在向最终用户显示时应用 nl2br，您可以避免许多麻烦。

在某些情况下，在将字符串插入数据库时移除部分内容可能是可以接受的，就像 strip_tags 函数（见下文）的情况一样，但通常最好在需要为浏览器渲染字符串之前，避免实际重新格式化字符串。

## 标签剥离

如果您允许普通公众更新您的网站，那么能够禁止使用 HTML 就很重要，可以防止访客发布干扰网站布局的标记。

PHP 函数 strip_tags 几乎完美地处理了这项工作的大部分。给定一些文本，strip_tags 将消除任何看起来像 HTML 标签的内容。更准确地说，strip_tags 所做的是移除任何以 < 开头并以 > 结尾的文本块。除标签之外的所有内容都保持原样。以下是一个简单示例：

```php
<?php
$text = 'This is <b>bold</b> text';

// Strip that tag
echo strip_tags($text);
?>
```

输出为：

```
This is bold text
```

您还可以提供一个允许 strip_tags 忽略的标签列表。例如，

```php
<?php
$text = 'This is <b>bold</b> and this is <i>italic</i>.
    What about this <a href="http://www.php.net/">link</a>?';

// Strip those tags
echo strip_tags($text, '<b><i>');
?>
```

它返回的 HTML 如下：

```
This is <b>bold</b> and this is <i>italic</i>.
What about this link?
```

如您所见，strip_tags 保留开始标签和结束标签之间的文本。如果它找到 < 字符但未找到匹配的 > 字符，它将移除直到字符串末尾的所有文本。

不过，使用 strip_tags 移除 HTML 有一个缺点，即在属性处理方面。如果您允许某些标签，网站成员可能能够在这些标签中使用属性，例如 style，这可能导致非常奇怪的布局。更糟糕的是，链接中包含的 JavaScript 可能导致跨站脚本（XSS）安全漏洞（参见附录 C）。

在下一个解决方案中，我将向您展示如何实现一个“自定义代码”系统，该系统提供了一种更可靠的机制来允许某些标签。稍后，我们将探讨如何检查属性本身的内容，以验证它们是否有效。

## 总结

值得了解的最后一个函数是 wordwrap。如果您有一段不包含特定格式的长文本字符串，可以使用 wordwrap 在给定间隔处插入一个字符，例如换行字符（\n）。wordwrap 会注意不要拆分单词，除非您明确指示它这样做。这对于构建排版良好的电子邮件消息特别有用，如第 8 章所示。

## 如何更改字符串的内容？

PHP 自带一组功能强大的字符串函数。乍一看手册[1]，它们可能看起来很简单，但只要稍加技巧，您就能用它们完成很多事情。例如，PEAR::XML_HTMLSax[2] 是一个用于解析格式不良的 XML（如 HTML）的完整 SAX 解析器。它几乎完全不使用正则表达式，而是依赖 strpos 和 substr 等函数来完成工作。

- [1] http://www.php.net/strings
- [2] http://pear.php.net/package-info.php?package=XML_HTMLSax

## 搜索和替换

先从一个简单示例开始，让我们考虑以下代码：

```php
<?php
// Places part of a string inside an HTML tag
function addTag($text, $word, $tag)
{
    $length = strlen($word);
    $start = strpos($text, $word);
    $word = '<' . $tag . '>' . $word . '</' . $tag . '>';
    return substr_replace($text, $word, $start, $length);
}

$text = <<<EOD
PHP (recursive acronym for "PHP: Hypertext Preprocessor") is a
widely-used Open Source general-purpose scripting language that
is especially suited for Web development and can be embedded
into HTML.
EOD;

$word = 'general-purpose';

echo addTag($text, $word, 'b');
?>
```

此处定义的 addTag 函数是一个非常简单的“搜索和替换”函数，可帮助我们为文本添加 HTML 标记。在此示例中，文本中的字符串“general-purpose”被包裹在 b 标签中，生成以下输出：

PHP (“PHP：超文本预处理器”的递归首字母缩写词）是一种广泛使用的开源通用脚本语言，尤其适用于 Web 开发，可以嵌入 HTML。
widely-used Open Source <b>general-purpose</b> scripting
language that is especially suited for Web development and can
be embedded into HTML.

其他函数，例如 str_replace，也可用于执行类似任务。在上述示例中，使用以下方法可能更简单：

```php
File: 4.php
<?php
$text = <<<EOD
PHP (recursive acronym for "PHP: Hypertext Preprocessor") is a
widely-used Open Source general-purpose scripting language that
is especially suited for Web development and can be embedded
into HTML.
EOD;

$word = 'general-purpose';

echo str_replace($word, '<b>' . $word . '</b>', $text);
?>
```

这与第一个示例实现的效果完全相同。

## 拆除

假设我们一直在使用的文本包含换行符，我们可以使用 explode 函数将其拆分为一行行的数组：

```php
File: 5.php
<?php
$text = <<<EOD
PHP (recursive acronym for "PHP: Hypertext Preprocessor") is a
widely-used Open Source general-purpose scripting language that
is especially suited for Web development and can be embedded
into HTML.
EOD;

$lines = explode("\n", $text);

echo "<table border=\"1\">\n";
foreach ($lines as $line) {
    echo "<tr>\n<td>$line</td>\n</tr>\n";
}
echo "</table>\n";
?>
```

这会在换行符处拆分文本，并将其放入 HTML 表中，如图 5.1 所示。

## 图 5.1. 拆分表格

| PHP（“PHP：超文本预处理器”的递归首字母缩写词）是一种广泛使用的 |
| 开源通用脚本语言，尤其适用于 Web 开发，可以 |
| 嵌入 HTML。 |

> implode 函数可用于逆转 explode 的效果，从数组值列表构建字符串。

## 请修剪两端

trim 函数是另一个实用工具；它移除字符串开头和结尾的空白字符。例如，在处理表单提交时，它可能很有用。它的工作原理如下：

```php
<?php
$string = ' This has whitespace at both ends ';

// Remove that whitespace!
$string = trim($string);
?>
```


## 格式化

另外两个强大的函数是 printf 和 sprintf 函数，前者将输出显示到屏幕，后者将其输出到另一个字符串。示例如下：

```php
<?php
$fruit = array('banana', 'mango', 'pear');
$price = array('30', '50', '35');

// A string with formatting
$format = "A %1\$s costs %2\$d cents.<br />\n";
for ($i = 0; $i < 3; $i++) {
    printf($format, $fruit[$i], $price[$i]);
}
?>
```

这会产生以下输出：

```
A banana costs 30 cents.
A mango costs 50 cents.
A pear costs 35 cents.
```

在此示例中，$format 包含 printf 和 sprintf 识别并替换为我们提供的值的特殊字符。有关更多详细信息，请参阅 PHP 手册[3]。

[3] http://www.php.net/sprintf

PHP 还能够将字符串视为数组，至少从简单语法的角度来看是这样。例如：

```php
<?php
$string = 'Hello World!';

$length = strlen($string);

for ($i = 0; $i < $length; $i++) {
    echo $string[$i] . '<br />';
}
?>
```

[3] http://www.php.net/sprintf

不过，这种能力也仅限于此。例如，你不能将字符串传递给 PHP 的某个数组函数。

现在你应该对使用 PHP 的常规字符串函数能实现什么有所了解。一般来说，如果能用它们解决问题，就使用它们。它们速度快、易于使用，且比正则表达式¹出错的可能性小得多。

## 如何实现自定义格式化代码？

如果你运营一个允许用户添加文本的网站，你很快就会意识到，允许他们直接使用 HTML 是灾难的根源。没过多久，就会有人（无论是意外还是恶意地）发布一条消息，打乱你网站整洁的布局。

如果你曾使用过 vBulletin 或 phpBB 之类的论坛，那么你肯定接触过 BBCode（公告板代码），这是一组非 HTML 标签，论坛成员可以使用这些标签提供简单的文本格式化，而不会损坏你网站的布局。如今，BBCode 几乎已成为标准，因为大多数论坛都实现了这种标签约定。

以下是 BBCode 的简单示例：

```
This is an example of a BBCode link to
[url=http://www.sitepointforums.com/]sitepointforums[/url]
```

当上述文本在论坛上显示时，论坛软件生成的代码如下：

```
This is an example of a BBCode link to
<a href="http://www.sitepointforums.com/">sitepointforums</a>
```

与你在“如何解决 HTML 文档中文本内容的问题？”中看到的 PHP 内置 strip_tags 函数相比，BBCode 的优势在于它能让你完全控制显示内容。BBCode 允许你赋予网站成员一定的格式化其添加到网站内容的能力，而不会影响整体网站布局。

¹正则表达式允许你定义复杂模式，以便在 PHP 字符串中搜索。正则表达式是一个复杂的主题，足以（并且已经）成为一整本书的主题。如果你有兴趣深入了解，下文“进一步阅读”部分中提供了一个参考。

如果你阅读过本书前面的一些解决方案，就会知道我主张在 PHP 中使用类。这个解决方案让我有机会充分阐明这一点，因为我们将选择一个开源类，使实现 BBCode 系统变得轻松。

这个名为 **BBCode** 的类由 Leif K-Brooks 开发，可从 PHP Classes[4] 获取。该类几乎满足你所有的 BBCode 需求，并随本书代码一起提供。其采用 PHP 许可证[5] 授权。

这个类中最重要的方法是 `add_tag` 方法。它以关联数组作为参数，该数组最多可包含六个键来描述相关标签。让我们来看看 `add_tag` 方法的实际应用示例。

以下示例注册了 BBTag [b]：

```php
$this->bbcode->add_tag(
    array(
        'Name'     => 'b',
        'HtmlBegin' => '<span style="font-weight: bold;">',
        'HtmlEnd'   => '</span>'
    )
);
```

该标签的 Name 为 b。数组中的 `HtmlBegin` 和 `HtmlEnd` 键定义了 BBTags 转换后将使用的 HTML 开始标签和结束标签。

以下示例设置了另一个 BBTag [link]：

```php
$this->bbcode->add_tag(
    array(
        'Name'     => 'link',
        'HasParam' => TRUE,
        'HtmlBegin' => '<a href="%%P%%">',
        'HtmlEnd'   => '</a>'
    )
);
```

这段代码注册了另一个键 `HasParam`，它告诉该类，这个 BBTag 具有一个应在转换后的文本中显示的单个属性。还要注意 `HtmlBegin` 的值。这里我们使用字符串 `%%P%%` 来标识参数应放置的位置。

[4] http://www.phpclasses.org/browse.html/package/951.html
[5] http://www.php.net/license/2_02.txt

在下一个示例中，它创建了一个 `size` 标签，我们看到了一个新键。`ParamRegex` 定义了参数必须符合的正则表达式；在此例中，它是一个对应字体大小的数字。代码如下：

```php
$this->bbcode->add_tag(
    array(
        'Name'        => 'size',
        'HasParam'    => TRUE,
        'HtmlBegin'   => '<span style="font-size: %%P%%;pt;">',
        'HtmlEnd'     => '</span>',
        'ParamRegex'  => '[0-9]+'
    )
);
```

此最终示例展示了数组中所有键的实际应用，并引入了键 `ParamRegexReplace`，可用于修改参数。在此例中，它允许 BBTag `[color=c5c6c7]` 变为 `<span style="color: #c5c6c7;">`：

```php
$this->bbcode->add_tag(
    array(
        'Name'             => 'color',
        'HasParam'         => TRUE,
        'ParamRegex'       => '[A-Za-z0-9#]+',
        'HtmlBegin'        => '<span style="color: %s%;">',
        'HtmlEnd'          => '</span>',
        'ParamRegexReplace'=> array('/^[A-Fa-f0-9]{6}$/'=>'#$0')
    )
);
```

我将所有这些内容整齐地封装在一个名为 `SitepointBBCode`（`SPLIB` 中的 `TextManipulation/SitepointBBCode.php`）的类中，该类在其构造函数中创建自定义标签。这样我们就可以通过实例化该类来简单地定义 BBTag。让我们来看看这段代码的实际应用：

```php
<?php
// Include the BBCode class
require_once 'ThirdParty/bbcode/bbcode.inc.php';

// Include the SitepointBBCode class which defines custom tags
require_once 'TextManipulation/SitepointBBCode.php';

$text=<<<EOD
Here is some <b>bold HTML which is unparsed</b>.
[i]This[/i] text [bg=yellow]illustrates[/bg]
the [b]bbcode[/b] class in action[/u].

You can visit [url=http://www.sitepointforums.com/]SitePoint forums[/url] with it [color=c5c6c7]just[/color] like the [size=15]real thing[/size].

You can even [s]email[/s] the
[align=center][email=editor@sitepoint.com]editor[/email][/align].
EOD;

// Replace any real HTML with entities
$text = htmlspecialchars($text);

$bbCode=new SitepointBBCode();
echo nl2br($bbCode->parse($text));
?>
```

$text 变量模拟你从数据库中获取的文本，该文本包含 BBCode（请记住，你希望在 SELECT 之后而非在 INSERT 或 UPDATE 之前应用这种文本操作）。

我们需要做的第一件事是将文本传递给 htmlspecialchars，我们在“如何解决 HTML 文档中文本内容的问题？”中见过它。这将允许 HTML 代码以纯文本形式出现，而无需被浏览器解析。在 The SitePoint Forums[6] 之类的论坛上，用户经常讨论 HTML，允许 HTML 代码作为普通文本出现是至关重要的。不过，一个不那么技术导向的网站可能会选择使用 strip_tags，彻底消除 HTML 标签。

以上代码生成的原始 HTML 如下：

```
Here is some &lt;b&gt;bold HTML which
is unparsed&lt;/b&gt;.<br />
<span style="font-style: italic;">This</span> text
<span style="background: yellow;">illustrates</span><br />
the <span style="font-weight: bold;">bbcode</span> class
in action.</span><br />
<br />
You can visit <a href="http://www.sitepointforums.com/"> SitePoint forums</a> with it
```

[6] http://www.sitepointforums.com/





就像真正的东西一样。

你甚至可以给编辑发邮件。

所有真实的 HTML 已被替换为 HTML 实体；BBCode 已被替换为我所想要的精确标记。能够将代码包装在一个漂亮、易于使用的类中，难道不是件很棒的事吗？而且还是免费的！

## 我如何实现一个敏感词过滤器？

如果你运营的网站面向未成年人，或者你不希望成员在激烈讨论中“充分”地表达自己，那么能够将特定单词替换为更悦目的内容将是一个非常实用的工具。

针对这个特定问题，你可以考虑在将文本插入数据库之前实现一个过滤器。这个解决方案的优势在于减少了 PHP 在内容显示之前需要完成的工作量。

这是一个你可以重复用于所有审查需求的类：

```
/**
 * WordFilter
 * Class for censoring words in text
 * @access public
 * @package SPLIB
 *
 */
class WordFilter {
 /**
  * An array of words to censor
  * @access private
  * @var array
  */
 var $badWords;
 /**
  * WordFilter constructor
  * Randomly generates strings to censor words with
  * @param array an array of words to filter
 * @access public
 */
function WordFilter($badWords)
{
    $this->badWords = array();
    srand((float)microtime() * 1000000);
    $censors = array('$', '@', '#', '*', '£');
    foreach ($badWords as $badWord) {
        $badWord = preg_quote($badWord);
        $replaceStr = '';
        $size = strlen($badWord);
        for ($i = 0; $i < $size; $i++) {
            shuffle($censors);
            $replaceStr .= $censors[0];
        }
        $this->badWords[$badWord] = $replaceStr;
    }
}

/**
 * Searches for bad words in text and censors them
 * @param string text to filter
 * @return string the filtered text
 * @access public
 */
function filter($text)
{
    foreach ($this->badWords as $badWord => $replaceStr) {
        $text = preg_replace('/' . $badWord . '/i', $replaceStr,
            $text);
    }
    return $text;
}
}
```

如果你在思考构造函数，其思路是创建一个随机字符串来替换每个单词——仅仅为了好玩。请注意，我使用了 preg_quote 来确保敏感词不会被解释为正则表达式语法。

现在，我厌恶天线宝宝™。事实上，只要提到“Tubby”这个词，我就会勃然大怒。将这个类付诸实践，我可以从我的网站上根除所有关于“Tubby”的讨论：

```
<?php
// Include the word filter
require_once 'TextManipulation/WordFilter.php';

// An array of words to replace
$badWords = array('tele', 'tubby', 'tubbies', 'byebye');

// Include the word file with the list of bad words
$WordFilter = new WordFilter($badWords);

// $text simulates some data from the database
$text = 'Time for teletubbies! I like tubbies so much. ByeBye!';

// Filter the words
$text = $WordFilter->filter($text);

echo $text;
?>
```

我得到了什么？

> 到了 £#£*#££*$@@！我非常喜欢 ££*$@@。@$$#*$！

世界现在更安全了。

## 我如何验证提交的数据？

验证字符串通常很重要。你如何确保用户通过表单提交的数据是它应该的样子——例如，一个 URL 或电子邮件地址？确保用户提供的值是它应该的值是一个常见问题。幸运的是，PEAR::Validate 可用，让你免于重复造轮子。此处使用的版本为 0.2.0。

PEAR::Validate 提供了一个主类，用于验证 Web 应用程序中常见的字符串和值，还提供了越来越多相关的国际化类，用于处理诸如英国邮政编码和美国社会安全号码等事物。每个类中包含一组静态方法（无需从类构造对象即可调用的方法），用于验证特定值。目前，了解可用内容的最佳方法是查看源代码，因为这仍然是一个相当年轻的包，文档很少。使用 PHPDocumentor 解析文件以生成 API 文档（有关 PHPDocumentor 的更多信息，请参见第 II 卷，第 6 章）。

以下是如何使用主 Validate 类中可用的三个方法（即 string、email 和 url）来验证表单数据：

```
<?php
// Include PEAR::Validate
require_once 'Validate.php';

// Include file to strip quotes if needed
require_once 'MagicQuotes/strip_quotes.php';

// Initialize errors array
$errors = array('name' => '', 'email' => '', 'url' => '');

// If the form is submitted...
if (isset($_POST['submit'])) {
	// Define the options for formatting the name field
	$name_options = array(
		'format' => VALIDATE_ALPHA . VALIDATE_SPACE,
		'min_length' => 5
	);

	// Validate name
	if (!Validate::string($_POST['name'], $name_options)) {
		$errors['name'] = ' class="error"';
	}

	// Validate email
	if (!Validate::email($_POST['email'])) {
		$errors['email'] = ' class="error"';
	}

	// Validate url
	if (!Validate::url($_POST['url'])) {
		$errors['url'] = ' class="error"';
	}
}
?>
```

首先，我们包含 PEAR::Validate 和我处理魔术引号的自定义代码。然后，在测试表单是否已提交后，我们静态地调用验证方法来检查字段。第一个检查是查看 name 字段是否只包含字母表中的字母或空格字符，并且长度至少为五个字符（这是由 $name_options 数组定义的）。

接下来，我们只需调用 Validate::email 和 Validate::url 来检查通过表单提交的 email 和 url 字段。请注意，如果将 TRUE 作为第二个参数传递，PEAR::Validate 将使用 PHP 的 checkdnsrr 函数检查指定主机名是否存在于 DNS 中。这种验证确实要付出与最近 DNS 服务器通信所涉及的延迟的代价。

这是表单本身的代码：

```
<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Transitional//EN"
"http://www.w3.org/TR/xhtml1/DTD/xhtml1-transitional.dtd">
<html xmlns="http://www.w3.org/1999/xhtml">
<head>
<title>PEAR::Validator</title>
<meta http-equiv="Content-Type"
content="text/html; charset=iso-8859-1" />
<style type="text/css">
form.userinfo {
font-family: verdana;
font-size: 12px;
width: 30em;
}
form.userinfo legend {
font-weight: bold;
}
form.userinfo div {
clear: both;
margin: 5px 10px;
}
form.userinfo label {
float: left;
}
form.userinfo span {
float: right;
}
.error {
color: red;
font-weight: bold;
}
</style>
</head>
<body>
<form class="userinfo" action="<?php echo $_SERVER['PHP_SELF'];
?>" method="POST">
<legend>Enter your details</legend>
<div>
<label><?php echo $errors['name']; ?>>Name:</label>
<span>
<input type="text" name="name"
value="<?php echo @$_POST['name']; ?>"> /
</span>
</div>
<div>
<label><?php echo $errors['email']; ?>>Email:</label>
<span>
<input type="text" name="email"
value="<?php echo @$_POST['email']; ?>"> /
</span>
</div>
<div>
<label><?php echo $errors['url']; ?>>Website:</label>
<span>
<input type="text" name="url"
value="<?php echo @$_POST['url']; ?>"> /
</span>
</div>
<div>
<span>
<input type="submit" name="submit" value="send" />
</span>
</div>
</form>
</body>
</html>
```

在构建表单本身时，我们使用 $errors 数组和一些 CSS 将表单标签标记为红色。这样可以让用户知道他们的输入中哪一部分无效，如图 5.2 所示。

## 图 5.2. PEAR::Validator 在行动...

![](img/5b6cdf7cf4cf53e30b19e047895dc464_182_0.png)

此示例中还值得注意的一点是在使用 echo 输出变量时使用 @ 运算符：

```
<?php echo @$_POST['url']; ?>
```

通过在变量名前面加上 @，我们指示 PHP 如果相关变量不存在时不要报错。

## 我如何过滤掉不需要的 HTML 代码？

如你在“如何解决 HTML 文档中的文本内容问题”中所见，strip_tags 函数可用于从包含 HTML 的字符串中删除标签；但是，它不处理标签中的属性。这是一个严重的限制——它可能使你面临跨站点脚本（XSS）攻击等风险（参见附录 C），并允许用户实现 style 标签，该标签可用于重新排列你的页面。

我们将应用于过滤的策略基于“拒绝我们不明确允许的一切”的原则。为帮助我们，我们仍将使用 strip_tags 函数来消除除小部分 HTML 以外的所有内容。然后，我们将使用本机 XML SAX 扩展来解析剩余内容，从而使我们能够检查这些内容。请注意，SAX 扩展的完整说明在第 II 卷第 2 章。此处我将假设你知道它的工作原理，并专注于构建一个允许少数标签的简单类。我们还将使用 PEAR::Validate，这次用于检查链接中 href 属性的内容。

再次，将此功能转换为可重用组件的最佳方法是使用一个类：

```
File: TextManipulation/FormFilter.php (in SPLIB) (excerpt)

/**
 * FormFilter<br />
 * Class for examining HTML tags.<br />
 * Note: requires PEAR::Validate
 * @access public
 * @package SPLIB
 */
class FormFilter {
 /**
  * String of allowed tags
  * @access private
```





* @var string
 */
var $AllowedTags = '<a><b><strong><i><em><u>';

/**
 * Instance of native XML parser
 * @access private
 * @var resource
 */
var $parser;

/**
 * String of allowed tags
 * @access private
 * @var string
 */
var $post = '';

/**
 * Used to store any XML error string
 * @access private
 * @var string
 */
var $error = '';

/**
 * Constructs FormFilter
 * @access public
 */
function FormFilter()
{
    $this->parser = xml_parser_create();
    xml_set_object($this->parser, $this);
    xml_set_element_handler($this->parser, 'open', 'close');
    xml_set_character_data_handler($this->parser, 'data');
}

/**
 * Constructs FormFilter
 * @param string data to filter
 * @return string filter data
 * @access public
 */
function filter($post)
{
    $this->post = '';
$post = strip_tags($post, $this->allowedTags);
$post = '<?xml version="1.0"?><post>' . $post . '</post>';
if (!xml_parse($this->parser, $post, true)) {
    $this->error = 'Post data is not well formed: ' .
    xml_error_string(xml_get_error_code($this->parser)) .
    ' on line ' . xml_get_current_line_number($this->parser);
    return false;
}
return $this->post;
}

/**
 * Returns any XML errors
 * @return string XML error
 * @access public
 */
function getError()
{
    return $this->error;
}

在FormFilter类的构造函数中，我们首先要做的是创建原生Expat解析器的实例，并告诉它要使用哪些回调函数（有关此内容将在第2卷第2章中详细介绍）。完成这些后，我们提供filter方法来“筛选”包含HTML的字符串。首先，我们移除除$allowedTags成员变量中定义的标签之外的所有内容。然后，我们需要将XML处理指令预置到字符串开头，并确保整个内容被包装在根XML节点中；这样做是为了防止解析器对字符串格式不正确提出警告。

如果在解析过程中遇到问题，错误消息将被本地存储，并通过getError方法提供。一旦解析完成，我们将帖子返回给调用filter方法的代码。

真正的工作发生在XML处理程序中：

文件：TextManipulation/FormFilter.php（在SPLIB中）（节选）

```
/**
 * Sax Open TagHandler
 * @param XML_HTMLSax
 * @param string tag name
 * @param array attributes
 * @return void
 * @access private
 */
function open(&$parser, $tag, $attrs)
{
    switch ($tag) {
    case 'A':
    if (isset($attrs['HREF']) &&
    Validate::url($attrs['HREF'])) {
    $this->post .= '<a href="' . $attrs['HREF'] .
    '" target="_blank">';
    } else {
    $this->post =
    '<a href="javascript;" target="_blank">';
    }
    break;
    case 'B':
    case 'STRONG':
    $this->post .= '<strong>';
    break;
    case 'I':
    case 'EM':
    $this->post .= '<em>';
    break;
    }
}

/**
 * Sax Close TagHandler
 * @param XML_HTMLSax
 * @param string tag name
 * @param array attributes
 * @return void
 * @access private
 */
function close(&$parser, $tag)
{
    switch ($tag) {
    case 'A':
    $this->post .= '</a>';
    break;
    case 'B':
    case 'STRONG':
    $this->post .= '</strong>';
    break;
    case 'I':
    case 'EM':
    $this->post .= '</em>';
    break;
    }
}

/**
 * Sax Data Handler
 * @param XML_HTMLSax
 * @param string data inside tag
 * @return void
 * @access private
 */
function data(&$parser, $data)
{
	$this->post .= $data;
}
}
```

解析器在读取XML文档时会调用这些处理程序方法。查看open方法，你可以看到我们如何处理不同的标签名称。特别是，当我们收到a标签时，我们使用PEAR::Validate来检查URL是否有效。还要注意，我们将b和i转换为strong和em。这里遇到的任何其他未明确标识的属性都会被简单地丢弃。

请注意，在这个示例中，使用strip_tags实际上是多余的，因为处理程序方法也会忽略任何未明确标识的标签。当然，我们在这里将自己限制在只有少数几个HTML标签。处理其他标签（例如列表）通常需要更复杂的代码，增加了我们可能允许意外HTML标签的风险。strip_tags函数充当我们的保险单。

使用XML扩展的一个好处是，我们要求用户提交格式正确的XML。这样做的好处是，例如未关闭的a标签不会被接受。但这也意味着，某些标签（例如br，如果允许的话）如果不按照XML标准编写，就会出现问题。

以下是该类在实际中的示例：

```
File: 12.php

<?php
// Include PEAR::Validate
require_once 'Validate.php';

// Include PEAR::XML_HTMLSax
require_once 'TextManipulation/FormFilter.php';

// Include file to strip quotes if needed
require_once 'MagicQuotes/strip_quotes.php';

// If the form is submitted...
if (isset($_POST['submit'])) {
    // Instantiate the form filter
    $FormFilter = &new FormFilter();

    // Filter the message
    if (FALSE === ($filtered_message =
        $FormFilter->filter($_POST['message']))) {
        $filtered_message = $FormFilter->getError();
    }
}
?>
<!DOCTYPE html "-//W3C//DTD XHTML 1.0 Transitional//EN"
"http://www.w3.org/TR/xhtml1/DTD/xhtml1-transitional.dtd">
<html xmlns="http://www.w3.org/1999/xhtml">
<head>
<title>Form HTML Filter</title>
<meta http-equiv="Content-Type"
    content="text/html; charset=iso-8859-1" />
</head>
<body>
<p><b>Add your comment:</b></br />
<form action="<?php echo $_SERVER['PHP_SELF']; ?>" method="POST">
<textarea cols="40" rows="5" name="message"></textarea><br />
<input type="submit" name="submit" value=" Post " />
</form></p>
<p>Allowed tags: <code>&lt;code&gt;&lt;a&gt; &lt;b&gt; &lt;strong&gt; &lt;i&gt; &lt;em&gt;</code></p>
<?php
    if (isset ( $filtered_message )) {
        echo ( "<p>Your post:</b><br />\n<code>\n".
            htmlspecialchars($filtered_message)."</code>\n" );
    }
?>
</body>
</html>
```

通过测试，你会发现这段代码只允许我们在类中标识的那些元素。

## 延伸阅读

- URL 编码: http://www.blooberry.com/indexdot/html/topics/urlencoding.htm

这对于URL编码是一个有用的参考。

- HTML实体参考: http://www.htmlhelp.com/reference/html40/entities/

收藏这个方便的参考，用于查找在HTML中具有特殊含义的字符。

- PCRE教程: http://codewalkers.com/tutorials/30/2.html

在本教程中，你将找到一些关于Perl兼容正则表达式的有用且实用的帮助。

# 6 日期和时间

如果一周有十天，那该多好？一小时有100分钟呢？一年有十个月？

日期和时间可能是你习以为常的东西。你每天都在处理它们，可能并不知道大脑用来计算还要等多久才到周五的巧妙数学算法。只有当你开始编程时，你才会意识到，这些年来你一直习以为常的东西在代码中处理起来并不像你预期的那么简单。怪罗马人吧！

在日常生活中，我们习惯于使用十进制（基数为十）的数字，这些数字针对处理十的倍数进行了优化（十个一组成十，十个十成一百，十个一百成一千，等等）。不谈数学课，日期和时间的问题在于它们不能分解为十的整组：

- 一秒中有1000毫秒。没问题。
- 一分钟中有60秒。
- 一小时中有60分钟。
- 一天中有24小时。

那么，给定一个以毫秒为单位的值，你如何计算天数呢？这需要一连串的长除法！而这仅仅是时间——那日期呢？

- 一周中有七天（你的周是从周日还是周一开始？）
- 一个月中你有……嗯……你不知道确切的天数或周数；它取决于月份（别让我提闰年！）
- 一年中有12个月。

当然，这太简单了。那要不要更难一点？你通常需要能够以多种格式表示日期，例如“Tuesday 18th March, 2003”、“03/18/03”（美国格式）、“18/03/03”（欧洲格式）、“18th Mar 2003”和“20030318”（MySQL风格的时间戳），更不用说“1047942000”（Unix时间戳）了！

你计划如何显示从数据库获取并按日期排序的文章列表？如果你想呈现更复杂的内容，例如在线日历，又该如何？在应用程序中处理日期和时间时，需要考虑很多问题。

PHP确实让处理时间和日期尽可能轻松，这要归功于date等强大的函数。但在PHP程序员职业生涯早期，制定处理日期和时间的正确策略非常重要。从第一天就采取正确的方法，就可以避免以后不得不编写极其复杂的代码来修复新手时犯下的错误。在本章中，我们将探讨可以采用的策略，并解决在日期和时间方面可能遇到的一些常见问题。

## 如何在MySQL中存储日期？

乍一看，在MySQL中存储日期的最简单方法似乎是直接将它们按网页上显示的样子存入，例如“18th March 2003”。警告——这是走向严重脱发之路的第一步。在针对MySQL运行的SQL语句中，WHERE子句不会允许你执行这样的操作：

```
SELECT * FROM table WHERE date > '14th February 2003'
```

存储日期信息的更好方法是使用时间戳。时间戳是以可用于求解的格式标识日期和时间的数字。




你在应用程序中通常会遇到的问题类型；例如，它们使对列表进行排序或比较两个日期等操作变得更加容易。作为PHP开发人员，你基本上会遇到两种时间戳——Unix时间戳和MySQL时间戳。

## Unix 时间戳

Unix时间戳通常是处理日期最有效的方法——它们是棘手问题的简单解决方案。Unix时间戳反映了自1970年1月1日00:00:00 GMT以来经过的秒数。将日期转换为其Unix时间戳，使日期和时间相关的计算变得容易。

Unix时间戳的缺点是，除非你是神童，否则它们不具备可读性；如果我告诉你1047994036是自1970年1月1日以来经过的秒数，你能告诉我那是哪一天吗？

Unix时间戳的另一个问题是，它们只能在有限的日期范围内使用，具体取决于你的操作系统。在基于Linux的系统上，你应该能够回溯到大约1902年，向前延伸至2037年。在基于Windows的操作系统上，下限可能最近到1970年1月1日。问题在于数字的大小。任何操作系统都可以轻松处理一定大小（2^32，即当前32位操作系统的4,294,967,296）以内的整数数字，之后它就必须更加费力地处理超大数字。因此，为了效率，操作系统通常会对日期和时间等重要值施加这种“最大”大小限制。Linux至少允许日期具有负整数值，因此你可以处理1970年1月1日之前的日期，而PHP在Windows上可能会对这些日期报错。我在这里想说的是，潜在的另一个类似Y2K的问题可能在2038年1月19日左右出现，这将影响所有仍在使用的32位操作系统。尝试在Google上搜索那个日期，你就明白我的意思了...

虽然2038年还很遥远，时间戳问题最多只会影响你选择起搏器，但如果你计划开发一个需要处理遥远过去或未来日期的应用程序（也许是在历史网站上），这点值得牢记。PHP提供了time和mktime等函数来帮助处理Unix时间戳。要查看问题的实际表现，请尽可能在多种不同的操作系统上运行以下脚本：

```
<?php
echo '1st Jan 1899: ' . mktime(0, 0, 0, 1, 1, 1899) . '<br />';
echo '1st Jan 1902: ' . mktime(0, 0, 0, 1, 1, 1902) . '<br />';
echo '31st Dec 1969: ' . mktime(0, 0, 0, 12, 31, 1969) . '<br />';
echo '1st Jan 1970: ' . mktime(0, 0, 0, 1, 1, 1970) . '<br />';
echo '1st Jan 2037: ' . mktime(0, 0, 0, 1, 1, 2037) . '<br />';
echo '1st Jan 2038: ' . mktime(0, 0, 0, 1, 1, 2038) . '<br />';
echo '19th Jan 2038: ' . mktime(0, 0, 0, 1, 19, 2038) . '<br />';
echo '20th Jan 2038: ' . mktime(0, 0, 0, 1, 20, 2038) . '<br />';
echo '1st Jan 2039: ' . mktime(0, 0, 0, 1, 19, 2039) . '<br />';
?>
```

取决于你的操作系统，特别是在Windows上，这可能会生成一系列不同的PHP警告错误。

关于Unix时间戳，还需要注意的一点是，它们的长度各不相同；1970年1月2日的时间戳显然会比当代时间戳短。一般来说，当你将Unix时间戳放入数据库时，列大小为10（INT(10））应该足以让你的应用程序在未来270多年里运行（当然，假设它没有运行在32位操作系统上）。

## MySQL 时间戳

MySQL时间戳比Unix时间戳更简单。其通用形式为YYYY-MM-DD HH:MM:SS，通常存储在类型为DATETIME的列中（另请注意列类型DATE和TIME，它们分别仅存储YYYY-MM-DD和HH:MM:SS）。

对于简单的排序和比较操作，这种形式的时间戳非常完美，*并且*它们具有可读性的优势。它们还具有可预测的长度（直到公元9999年），这使得它们更容易验证。

缺点是，在处理更复杂的日期相关操作时，你仍然会遇到问题。例如，你要如何按周分组数据？你最终可能需要将MySQL时间戳转换为Unix时间戳才能实现这一点，这种转换会显著减慢处理大量数据的应用程序的速度。

就我个人而言，在两种时间戳中，我更倾向于使用Unix时间戳在MySQL中存储日期信息。当然，我计划在2038年到来时已经退休去钓鱼，但我会在这里提供两种示例，并将选择权留给你。

## 时间戳实战

要查看Unix时间戳的实际效果，假设该列不存在，我们首先需要使用以下命令修改第3章中使用的articles表：

```
ALTER TABLE articles ADD
published INT(10) UNSIGNED DEFAULT '0' NOT NULL;
```

请注意，我们将新的published列设置为UNSIGNED，因为我们不打算插入1970年1月1日之前的任何日期（这需要负值）；这增加了可以存储的正时间戳值的范围。默认值0表示1970年1月1日。

我们现在可以按如下方式插入新行：

```
<?php
// Include MySQL class
require_once 'Database/MySQL.php';

$host = 'localhost'; // Hostname of MySQL server
$dbUser = 'harryf'; // Username for MySQL
$dbPass = 'secret'; // Password for user
$dbName = 'sitepoint'; // Database name

// Instantiate MySQL connection
$db = &new MySQL($host, $dbUser, $dbPass, $dbName);

// Get the UNIX timestamp for right now
$now = time();

// A query to create an article
$sql = "INSERT INTO articles
SET
title='Test Article',
body='This is a test...',
author='HarryF',
published='$now'";

// Perform the query
$result = $db->query($sql);

if ($result->isError()) {
echo 'Problem: ' . $result->isError();
} else {
    echo 'Article inserted';
}
?>
```

请注意，我们使用time函数获取当前时间的Unix时间戳，然后将其插入数据库。现在可以对记录进行排序等操作了；我们只需使用类似这样的查询：

```
SELECT * FROM articles ORDER BY published DESC LIMIT 0, 10
```

这将获取数据库中最新的十篇文章列表，从最近的开始。

要处理复杂的查询，例如获取上周发布的所有文章，我们可以使用mktime函数生成所需的时间戳，并借助date函数获得少许帮助。在这种情况下，解决方案如下：

```
// Instantiate MySQL connection
$db = &new MySQL($host, $dbUser, $dbPass, $dbName);

// Timestamp for last week
$lastWeek = mktime(0, 0, 0, date('m'), date('d') - 7, date('Y'));

$sql="SELECT * FROM articles
WHERE published > '$lastWeek'
ORDER BY published DESC";

// Perform the query
$result = $db->query($sql);

while ($row = $result->fetch()) {
    echo $row['title'] . ': ' .
    date('F j, Y', $row['published']) . '<br />';
}
```

mktime函数需要一些时间来熟悉（值得学习手册[1]以获取更多详细信息），但非常强大。它根据日期和时间的秒、分、时、月、日、年组件（按此顺序）构建Unix时间戳。在此情况下，我们想要确定正好一周前的日期。因此，我们对日组件使用了以下表达式：

[1] http://www.php.net/mktime

```
date('d') - 7
```

date('d')返回今天日期的日组件（同样，该函数的手册页面[2]值得你关注），减去七会让我们从今天倒退一周。你可能已经注意到，如果今天是本月的1日，减去七会得到日期“-6”。幸运的是，mktime能够理解这种意图；它会正确调整月份，并从上个月的总天数开始倒计数。

如果你追求最大性能，并且不介意自己进行数学计算，可以使用以下方法实现大致相同的效果：

```
$lastWeek = time() - 7 * 24 * 3600;
```

或者更简单地：

```
$lastWeek = time() - 604800;
```

稍后，我们将使用date函数，结合数据库中的Unix时间戳，为该时间戳创建可读的日期：

```
date('F j, Y', $row['published'])
```

date函数可以接受一个Unix时间戳，并根据第一个参数（在此情况下为'F j, Y'）将其格式化：

```
March 18, 2003
```

如你所见，date函数将Unix时间戳转换为可读的内容。

要使用MySQL时间戳，你需要使用以下命令修改articles表：

```
ALTER TABLE articles CHANGE published published DATETIME NOT NULL
```

请注意，这样做会搞乱articles中存储的日期；显然，你不应该用真实数据尝试此操作。

用于识别上周文章的查询现在将如下所示：

[2] http://www.php.net/date
1. 区别在于，使用mktime可以指定午夜一周后发布的文章，而替代方法查找的是一周后当前时间之后发布的文章。在大多数应用程序中，这种差异可能无关紧要。




文件：4.php

```php
<?php
// Include MySQL class
require_once 'Database/MySQL.php';

$host = 'localhost'; // Hostname of MySQL server
$dbUser = 'harryf'; // Username for MySQL
$dbPass = 'secret'; // Password for user
$dbName = 'sitepoint'; // Database name

// Instantiate MySQL connection
$db =& new MySQL($host, $dbUser, $dbPass, $dbName);

// Select articles
$sql = "SELECT
            *,
            DATE_FORMAT(published, '%M %e, %Y') as published
            FROM articles
            WHERE published > UTC_TIMESTAMP() - INTERVAL 7 DAY
            ORDER BY published DESC";

// Perform the query
$result = $db->query($sql);

while ($row = $result->fetch()) {
    echo $row['title'] . ': ' .
        $row['published'] . '<br />';
}
?>

```

请注意，我们使用了 MySQL 的 DATE_FORMAT 函数[3] 来格式化页面上显示的日期，而在之前的示例中，格式化是由 PHP 脚本处理的。我们还使用了 MySQL 的 UTC_TIMESTAMP 函数和一个 INTERVAL 来选择我们要查找的日期。

这个示例展示了我偏好将日期/时间值存储为 Unix 时间戳的几个原因：

- 我希望 SQL 语句尽可能简单。
- 在 PHP 中调试错误通常比在 SQL 语句中更容易。
- MySQL 日期/时间功能的许多细节都是数据库特定的，如果需要，它们移植到其他数据库时效果不佳。
- 您的数据库应该负责跟踪您的数据，而不是将其格式化为显示用的格式。²

当您使用 MySQL 时间戳时，通常需要依赖 MySQL 的内置函数来帮您完成一些工作。让我再展示一个饱受“复杂查询综合征”之苦的示例。

假设您想显示一个统计数据，告诉您网站上上一篇文章是多少天前发布的。为此，您需要计算今天日期与上一篇文章发布日期之间的“天数距离”（而非差值）。MySQL 可以这样做：

```
SELECT TO_DAYS(NOW()) - TO_DAYS(published)
FROM articles
ORDER BY published DESC
LIMIT 1
```

这看起来还可以，但 SQL 语句正在变得越来越复杂。如果我改为将数据存储为 Unix 时间戳，查询将如下所示：

```
SELECT published
FROM articles
ORDER BY published DESC
LIMIT 1
```

然后，要在 PHP 中显示结果，我将使用以下代码：

```
$daysAgo = floor((time() - $row['published']) / 86400);
```

86400 是一天中的秒数；floor 函数用于将小数向下舍入为整数值。

当然，您可能不同意在 PHP 中处理事情更简单，这种情况下，我完全鼓励您探索 MySQL 的日期处理功能。最终，Unix 时间戳和 MySQL 时间戳都可以达到相同的目的；您偏爱哪种是个人喜好的问题。

²顺便说一句，MySQL 的开发者倾向于同意我的这一观点。

[3] http://www.mysql.com/doc/en/Date_and_time_functions.html

## 如何解决常见的日期问题？

请考虑我们每次面对日历时大脑所进行的计算类型：

> “我希望它在3月3日前完成……那只有五天的时间了！”

很明显，处理日期不仅仅是按重要性组织数据或显示单个数据点。在本方案中，我们将探讨处理日期和时间时可能遇到的一些常见问题。具体来说，我们将看到如何处理

- [ ] 一周中的天数
- [ ] 一年中的周数
- [ ] 一年中的天数
- [ ] 一个月的天数
- [ ] 闰年

在此过程中，我们将构建一个可以在您自己的应用程序中轻松重用的类。

以下代码为该类奠定了基础：

```php
<?php
/**
 * DateMath class for solving common date problems
 * @package SPLIB
 */
class DateMath {
/**
 * Unix timestamp
 * @access private
 * @var int
 */
var $timeStamp;
/**
 * DateMath constructor
 * If parameters not provided, DateMath uses current time
 * <code>
 * $dateMath = new DateMath(2003,8,22); // Uses 22nd August 2003
 * $dateMath = new DateMath(); // Uses current date and time
 * </code>
 * @param int year ( e.g. 2003 )
 * @param int month ( e.g. 8 for August )
 * @param int day of month ( e.g. 22 )
 * @param int hours ( e.g. 15 )
 * @param int minutes ( e.g. 5 )
 * @param int seconds ( e.g. 7 )
*/
function DateMath($y = NULL, $m = NULL, $d = NULL, $h = NULL,
$i = NULL, $s = NULL)
{
$time = time();

$y = is_numeric($y) ? $y : date('Y', $time);
$m = is_numeric($m) ? $m : date('m', $time);
$d = is_numeric($d) ? $d : date('d', $time);
$h = is_numeric($h) ? $h : date('H', $time);
$i = is_numeric($i) ? $i : date('i', $time);
$s = is_numeric($s) ? $s : date('s', $time);
$this->timeStamp = mktime($h, $i, $s, $m, $d, $y);
}

/**
* For setting a Unix timestamp
* @param int a Unix timestamp
* @return void
* @access public
*/
function setTimeStamp($timeStamp)
{
$this->timeStamp = $timeStamp;
}
```

构造函数会检查您是否为日期传递了任何值，参数按年、月、日、时、分、最后是秒的顺序出现。对于您未提供数值的任何参数，都将使用当前日期或时间。然后，构造函数将其转换为时间戳，以便后续计算更加容易。

如果我要从时间戳开始，可以使用 setTimeStamp 方法提供自己的值。

## 一周中的天数

如果给定日期“2003年3月22日”，我们如何知道那是星期几？最简单的解决方案是将其转换为时间戳，然后使用 PHP 的 date 函数来告诉我们22日是星期几。要将其添加到类中，我们只需插入另一个方法：

```php
/**
 * Returns the day of the week
 * @param boolean if true returned value will be numeric day of week
 * @return mixed e.g. Saturday or 6
 * @access public
 */
function dayOfWeek($Numeric = false)
{
    if ($Numeric) {
        return date('w', $this->timeStamp);
    } else {
        return date('l', $this->timeStamp);
    }
}
```

现在，使用 dayOfWeek 方法，我们将找出2003年3月22日是星期几：

```php
<?php
// Include DateMath class
require_once 'DateTime/DateMath.php';

// Instantiate DateMath class 22nd March 2003
$dateMath = new DateMath(2003, 03, 22);

echo '22nd March 2003 is a ' . $dateMath->dayOfWeek();
?>
```

请注意，如果向 dayOfWeek 方法传递 TRUE，它将返回一周中天数的数字表示，从0表示星期日开始：

echo '22nd March 2003 is day ' . $dateMath->dayOfWeek(TRUE) .
 ' of the week.';

## 一年中的周数

要确定一年中的周数，我们向 DateMath 类添加另一个方法：

文件：DateTime/DateMath.php（在 SPLIB 中）（节选）

```php
/**
 * Returns the ISO 8601 week of the year
 * @return int numeric week of year e.g. 12
 * @access public
 */
function weekOfYear()
{
   return date('W', $this->timeStamp);
}
```

将其付诸实践：

文件：6.php

```php
<?php
// Include DateMath class
require_once 'DateTime/DateMath.php';

// Instantiate DateMath class 22nd March 2003
$dateMath = new DateMath(2003, 3, 22, 0, 0, 0);

echo '22nd March 2003 is in week ' . $dateMath->weekOfYear() .
     ' of the year';
?>
```

请注意，weekOfYear 方法依赖于 PHP 的 date 函数，该函数对周使用 ISO 8601 标记[4]。根据该标准，一年的第一周是包含当年的第一个星期四的周（从星期一开始）。因此，例如，如果12月的最后两天分别是星期一和星期二，根据此标记，它们实际上属于下一年。

## 一个月的天数

我的记忆力很差，我从来都记不住某个月应该有多少天。幸运的是，使用 PHP 找出这一点并不太难，我们可以简单地向 DateMath 类添加一个 daysInMonth 方法：

[4] http://www.cl.cam.ac.uk/~mgk25/iso-time.html





/**
 * Provides the number of days in the month
 * @return int number of days in the month
 * @access public
 *
 function daysInMonth()
 {
     return date('t', $this->timeStamp);
 }
```

Here, we simply rely again on the PHP date function to do the hard work, but it's good to have this method available from our class—this makes it a complete solution for common date-related problems.

译文：
这里，我们再次依赖 PHP 的 date 函数来完成繁重的工作，但从我们的类中提供这个方法是件好事——这使得它成为解决常见日期相关问题的完整方案。

Let's put it to the test:

译文：
让我们来测试一下：

```
<?php
// Include DateMath class
require_once 'DateTime/DateMath.php';

$months = array(
    'January' => 01,
    'February' => 02,
    'March' => 03,
    'April' => 04,
    'May' => 05,
    'June' => 06,
    'July' => 07,
    'August' => 08,
    'September' => 09,
    'October' => 10,
    'November' => 11,
    'December' => 12);

foreach ($months as $sname => $num) {
    $dateMath = new DateMath(2003, $num, 1, 0, 0, 0);
    echo $sname . ' has ' . $dateMath->daysInMonth() . ' days<br/>';
}
?>
```

This helps me remember that:

译文：
这帮我记住：

```
January has 31 days
February has 28 days
March has 31 days
April has 30 days
May has 31 days
June has 30 days
July has 31 days
August has 31 days
September has 30 days
October has 31 days
November has 30 days
December has 31 days
```

Note that this method will correctly report twenty-nine days in February when the date stored in DateMath occurs in a leap year. And *speaking of leap years*...

译文：
请注意，当 DateMath 中存储的日期发生在闰年时，此方法将正确报告二月有二十九天。而且，*说到闰年*...

## 闰年

译文：
## 闰年

Not all years are the same, which, if you had the misfortune to be born on February 29, you'll know only too well; every four years there's an extra day, with occasional exceptions.³ To identify leap years, I can take advantage of the daysInMonth method to create a new method; this will examine February and use it to find out whether it occurs in a leap year:

译文：
并非所有年份都相同，如果你不幸出生于2月29日，你就会深有体会；每四年会多出一天，偶尔有例外。³ 要识别闰年，我可以利用 daysInMonth 方法创建一个新方法；它将检查二月，并用它来确定是否发生在闰年：

```
File: DateTime/DateMath.php (in SPLIB) (excerpt)

/**
 * Determines whether current year is a leap year
 * @return boolean true if a leap year
 * @access public
 */
function isLeapYear()
{
	return date('L', $this->timeStamp);
}
```

Once again, we're wrapping a convenient package around an obscure feature of PHP's date function.

译文：
又一次，我们为 PHP date 函数的一个冷门特性包装了一个方便的封装。

Let's see how it works:

译文：
让我们看看它是如何工作的：

³Years evenly divisible by 4 are leap years, with the exception of years evenly divisible by 100 that are *not* evenly divisible by 400. Therefore, the years 1700, 1800, 1900 and 2100 are not leap years, but 1600, 2000, and 2400 are leap years.

译文：
³能被4整除的年份是闰年，但能被100整除且*不能*被400整除的年份除外。因此，1700年、1800年、1900年和2100年不是闰年，但1600年、2000年和2400年是闰年。

```
<?php
// Include DateMath class
require_once 'DateTime/DateMath.php';

// Build an array for the next ten years
$thisyear = date('Y');
$years = range($thisyear, $thisyear + 10);

// Find the leap years
foreach ($years as $year) {
    $dateMath = new DateMath($year, 1, 1, 0, 0, 0);
    if (!$dateMath->isLeapYear()) {
        echo $year . ' is not a leap year<br/>';
    } else {
        echo $year . ' is a leap year!<br/>';
    }
}
?>
```

This identifies which of the next ten years are and are not leap years:

译文：
这识别出接下来十年中哪些是闰年，哪些不是：

```
2003 is not a leap year
2004 is a leap year!
2005 is not a leap year
2006 is not a leap year
2007 is not a leap year
2008 is a leap year!
2009 is not a leap year
2010 is not a leap year
2011 is not a leap year
2012 is a leap year!
2013 is not a leap year
```

## 一年中的第几天

译文：
## 一年中的第几天

Another feature of date tells us what day of the year it is:

译文：
date 的另一个功能告诉我们现在是一年中的第几天：

```
/**
 * Returns the day of the year
 * @return int numeric day of year e.g. 81
 * @access public
 */
function dayOfYear()
{
    return date('z', $this->timeStamp) + 1;
}
```

This is then simply applied to find out that March 22 will be the eighty-first day of the year 2005:

译文：
然后只需应用它，即可得知3月22日是2005年的第81天：

```
<?php
// Include DateMath class
require_once 'DateTime/DateMath.php';

// Instantiate DateMath class 22nd March 2003
$dateMath = new DateMath(2003, 3, 22, 0, 0, 0);

echo '22nd March 2003 is day ' . $dateMath->dayOfYear() .
    ' of the year';
?>
```

## 月份的第一天

译文：
## 月份的第一天

A useful piece of information, particularly when building calendars, is to be able to determine what day of the week the first of a month falls on:

译文：
一条有用的信息，特别是在构建日历时，是能够确定一个月的第一天是星期几：

```
/**
 * Returns the day of the week for the first of the month
 * @param boolean if true returned value will be numeric day of
 * week
 * @return mixed e.g. 1 or Monday
 * @access public
 */
function firstDayInMonth($numeric = false)
{
    $firstDay = mktime(0, 0, 0, date('m', $this->timeStamp), 1,
        date('Y', $this->timeStamp));
    if ($numeric) {
        return date('w', $firstDay);
    } else {
        return date('l', $firstDay);
    }
}
```

Just to double check, March 2003 should begin on a Saturday:

译文：
为了再确认一下，2003年3月应该是星期六开始：

```
<?php
// Include DateMath class
require_once 'DateTime/DateMath.php';

// Instantiate DateMath class 22nd March 2003
$dateMath = new DateMath(2003, 3, 22, 0, 0, 0);

echo 'The first day of March is a ' .
     $dateMath->firstDayInMonth() . '.';
?>
```

You’ll see more of this method in the next solution.

译文：
你将在下一个解决方案中看到更多关于此方法的内容。

## 语法小贴士

译文：
## 语法小贴士

Let’s say you want to print out the day of the month in an English format, with a suffix (e.g. “January 1st, 2003”). How could we decide on the suffix for the number? In this case, the built-in date function provides the answer with its S formatting character:

译文：
假设你想以英语格式打印月份的一天，并带有后缀（例如“January 1st, 2003”）。我们如何确定数字的后缀？在这种情况下，内置的 date 函数通过其 S 格式字符提供了答案：

```
// Retrieve the day of the month, with suffix
$dayOfMonth = date('jS');
```

On February 3, this would result in $dayOfMonth being ‘3rd’.

译文：
在2月3日，这将导致 $dayOfMonth 为‘3rd’。

However, what if we want to apply a suffix for a number that *isn’t* a day of the month? You may have noticed in the section called “Day of the Year” that what we got back was a message like this:

译文：
然而，如果我们想为一个*不是*月份日期的数字应用后缀怎么办？你可能注意到在名为“一年中的第几天”的章节中，我们得到的消息是这样的：

> 22nd March 2003 is day 81 of the year

译文：
> 2003年3月22日是一年的第81天

Of course, “the 81st day of the year” would have been more natural. What we need is a little code which, when given a positive integer, provides the correct suffix. Let’s add this code to the DateMath class:

译文：
当然，“一年的第81天”会更自然。我们需要一小段代码，给定一个正整数，提供正确的后缀。让我们将此代码添加到 DateMath 类中：

```
/**
 * Provide the suffix for a number e.g. 22 is the 22nd
 * @static
 * @param int some number
 * @return string e.g. 'nd' for 22nd
 * @access public
 */
function suffix($num)
{
    if ($num < 11 || $num > 13) {
        $desc = array(0 => 'st', 1 => 'nd', 2 => 'rd',
                      4 => 'th', 5 => 'th', 6 => 'th', 7 => 'th',
                      8 => 'th', 9 => 'th');
        return $desc[$num % 10];
    } else {
        return 'th';
    }
}
```

Note that the numbers 11, 12, and 13 are special cases in the English language, and are treated as such by the code above.

译文：
请注意，数字11、12和13在英语中是特殊情况，上述代码也将它们视为特殊情况。

Here's the suffix method in action:

译文：
以下是 suffix 方法的实际应用：

```
<?php
// Include DateMath class
require_once 'DateTime/DateMath.php';

// Instantiate DateMath class for 22nd March 2003
$dateMath = new DateMath(2003, 3, 22, 0, 0, 0);

echo '22nd March 2003 is the: <br />';
echo $dateMath->dayOfWeek(TRUE) + 1 .
     $dateMath->suffix($dateMath->dayOfWeek(TRUE) + 1) .
     ' day of the week<br />';
echo $dateMath->weekOfYear() .
     $dateMath->suffix($dateMath->weekOfYear()) .
     ' week of the year<br />';
echo $dateMath->dayOfYear() .
     $dateMath->suffix($dateMath->dayOfYear()) .
     ' day of the year<br />';
?>
```

```
22nd March 2003 is the:
7th day of the week
12th week of the year
81st day of the year
```

The methods provided here should solve the majority of the more unusual date-related problems. The DateMath class is simple, as you can see, but it's easily made more complex, so you should have no problems adding further methods to it.

译文：
这里提供的方法应该能解决大多数不寻常的日期相关问题。正如你所见，DateMath 类很简单，但它很容易变得更加复杂，因此你应该不会在向其中添加更多方法时遇到问题。

## 如何构建在线日历？

译文：
## 如何构建在线日历？

Now that the DateMath class is ready, I have a couple of methods that will help us build a calendar. Aside from the specific date-related issues that DateMath solves, the hard part is to build an online calendar that suits everybody. If one site needs a calendar as HTML, but another needs WML (wireless markup language), we have a problem. The trick to solving this problem is to separate the building of the calendar’s “data structures” from the rendering of output.

译文：
既然 DateMath 类已经准备就绪，我有几种方法将帮助我们构建日历。除了 DateMath 解决的特定日期相关问题之外，难点在于构建一个适合所有人的在线日历。如果一个网站需要 HTML 日历，而另一个需要 WML（无线标记语言）日历，我们就有麻烦了。解决这个问题的诀窍是将日历“数据结构”的构建与输出的呈现分开。

To cut a long story short, in top cooking program style it’s time to say that magic phrase, “Here’s one I prepared earlier!” as I introduce a collection of classes that can help build calendar data structures. Once we’ve got a grasp on these, we’ll use them to build our calendar.

译文：
长话短说，就像顶级烹饪节目中的风格，是时候说出那句神奇的台词了：“这里有一个我早就准备好了！”当我介绍一套可以帮助构建日历数据结构的类时。一旦我们掌握了这些，我们将使用它们来构建我们的日历。

As shown in the UML diagram in Figure 6.1, all the classes in this example inherit a great deal of functionality from the Calendar base class.

译文：
如图6.1的UML图所示，本示例中的所有类都从 Calendar 基类继承了大量功能。





## 图 6.1. 日历类的 UML

![](img/5b6cdf7cf4cf53e30b19e047895dc464_211_0.png)

这些类采用的基本策略如下：例如，给定一个 Month，你可以构建其中出现的 Days。同样，给定一个 Day，你可以构建该天内出现的 Hours。此外，你可能遇到的任何 Calendar 子类都了解其前后内容；所以，如果你正在处理表示 2003 年 1 月 1 日的 Day 对象，它将“知道”表示 2003 年 12 月 31 日的 Day 对象在它之前。日期组件本身可以以数值形式获取，例如分别代表 2003 年 8 月 9 日的 Year、Month 和 Day 组件的 2003、8 和 9，或者作为 Unix 时间戳，具体取决于你需要达成的目标。

了解其工作原理最简单的方式是通过示例。

以下代码片段展示了如何使用 Year 类为仅显示月份的简单日历创建 Month 对象。

首先，我们需要包含必要的类：

```
<?php
// Include Calendar Year
require_once 'DateTime/Year.php';
require_once 'DateTime/Month.php';
```

由于这是我们第一次使用一个庞大的继承层次结构，我应该指出，这里包含的两个类——Year 和 Month——各自也会执行一些包含操作。例如，它们都会包含其父类 Calendar。还包含一个名为 TimeUnitValidator 的类，负责检查这些类创建的日期是否有效。虽然上述两个包含操作应该会透明地包含所有这些类，但你 _确实_ 需要确保相关的类文件可用（如果不可用，PHP 会提醒你！）。此处和代码存档中呈现的代码假设所有日期/时间类都可以在你的 PHP 包含路径中名为 DateTime 的目录下找到。

接下来，我需要为控制显示日历哪一部分的 $_GET 变量设置默认值。如果 URL 中未提供日期，我将这些变量设置为当前年份和月份。没有要求使用此处出现的变量名；你可以随意命名。

```
// Initialize $_GET variables to this year and month if not set
if (!isset($_GET['y'])) $_GET['y'] = date('Y');
if (!isset($_GET['m'])) $_GET['m'] = date('m');
```

完成这些后，我们创建一个 Year 对象，并传递它所代表的年份的数值（例如 2003）。之后，我们创建一个数组，并在其中放置一个 Month 对象。此数组用于标识特定的日历元素已被“选中”，我们稍后将看到其实际效果。

```
// Create a new Year object
$year = new Year($_GET['y']);

$selectedMonths = array(
new Month($_GET['y'], $_GET['m'])
);
```

最后，我们调用 Year 的 build 方法，并传入所选月份的数组：

```
// Instruct the Year to build Month objects
$year->build($selectedMonths);
```

实际指示 Calendar 子类（Second 除外）构建其子项的是 build 方法。再次说明，这稍后会变得清晰。

接下来，我们创建两个变量，用于制作“下一页”和“上一页”链接，以便用户在年份之间导航：

```
$prev = $_SERVER['PHP_SELF'] . "?y=" . $year->lastYear();
$next = $_SERVER['PHP_SELF'] . "?y=" . $year->nextYear();
```

请注意，我们使用 Year 方法 lastYear 获取前一年的数值，并使用 nextYear 返回来年的值。然后，在开始构建日历输出 HTML 时，我们使用 thisYear 获取当前年份的值：

```
// Start building HTML
$calendar = "<table>\n";
$calendar .=
    "<caption><a href=\"$prev\" class=\"nav\">&lt;&lt;</a> " .
    $year->thisYear() .
    " <a href=\"$next\" class=\"nav\">&gt;&gt;</a></caption>\n";
```

请注意，将值 TRUE 传递给任何以“this”开头的方法（例如 thisYear）将返回时间戳，而不是数值型、人类可读的值。我们稍后将使用此功能。

在日历顶部构建完成后，我们可以开始在 while 循环中使用迭代器方法 fetch 构建主体。fetch 方法返回你正在使用的类的“子项”；例如，Day 返回 Hours，而 Minute 返回 Seconds。

```
while ($month = $year->fetch()) {
    $calendar .= "<tr>\n";
    $link = $_SERVER['PHP_SELF'] . "?y=" . $month->thisYear() .
        "&m=" . $month->thisMonth();
    if (!$month->isSelected()) {
        $calendar .= "<td><a href=\"$link\">" .
            date('F', $month->thisMonth(TRUE)) .
            "</a></td>\n";
    } else {
        $calendar .= "<td class=\"selected\"><a href=\"$link\">" .
            date('F', $month->thisMonth(TRUE)) .
            "</a></td>\n";
    }
    $calendar .= "</tr>\n";
}
$calendar .= "</table>\n";
?>
```

> 在使用 fetch 方法之前必须调用 build 方法，否则 fetch 将返回 FALSE。

在循环内部，你会注意到 isSelected 方法。它用于标识传递给 build 方法的月份。它允许我们修改“选中”月份的 HTML 格式，以便以某种方式高亮显示。

另外，请注意此处我们将布尔值 TRUE 传递给了 thisMonth。这告诉该方法返回一天的 Unix 时间戳，而不是数值；然后我们可以使用 PHP 的 date 函数将该时间戳重新格式化为相应月份的英文名称。

现在我们已经构建了日历并将其放入一个字符串中，可以简单地将其“丢入”我们的 HTML 页面……瞧——我们看到一个显示年份月份的简单日历！输出结果如图 6.2 所示。

## 图 6.2. 一年中的月份

![](img/5b6cdf7cf4cf53e30b19e047895dc464_215_0.png)

## 罗马日历

现在你大致了解了可用的方法，何不来一个更实用的示例？以下代码以日历中常见的格式显示给定的月份——一个表格，其中每行代表一周。首先，我们将实例化一个 Month，并使用它来获取上一个月和下一个月的时间戳：

```
<?php
// Include Calendar Month and Day
require_once 'DateTime/Month.php';
require_once 'DateTime/Day.php';

// Set up initial variables
if (!isset($_GET['y'])) $_GET['y'] = date('Y');
if (!isset($_GET['m'])) $_GET['m'] = date('m');
if (!isset($_GET['d'])) $_GET['d'] = date('d');

// Instantiate the Month class
$month = new Month($_GET['y'], $_GET['m']);

// Get the details of the months as timestamps
$last = $month->lastMonth(true);
$next = $month->nextMonth(true);
$thisMonth = $month->thisMonth(true);
```

接下来，我们将构建表格的顶行，以便用户在月份之间导航：

```
// Start building the calendar
$calendar = "<table class="cal" width="420">\n<tr>\n";
$calendar .= "<td colspan="2">" .
    "<a class="cal_nav" href="" .
    $_SERVER['PHP_SELF'] .
    "?y=". date('Y', $last) .
    "&m=". date('m', $last) . "&d=1">" .
    date('F', $last) . "</a></td>";
$calendar .= "<td class="cal_now" colspan="3">" .
    "align="center">". date('F', $thisMonth) .
    "</td>";
$calendar .= "" .
    "<td colspan="2" align="right">" .
    "<a class="cal_nav" href="" .
    $_SERVER['PHP_SELF'] .
    "?y=". date('Y', $next) .
    "&m=". date('m', $next) . "&d=1">" .
    date('F', $next) . "</a>" .
    "</td></tr>";
```

我们还将构建一个所选天的数组，并在 Month 对象上调用 buildWeekDays 方法：

```
// Array for selected days
$sDays = array(new Day($_GET['y'], $_GET['m'], $_GET['d']));

// Build the days of the month
$month->buildWeekDays($sDays);
```

在其构建方法方面，Month 是一个特殊情况。默认的 build 方法为任何给定月份构建一个正常的天序列。另一方面，buildWeekDays 构建一个包含“空”天的序列，这些天在构建日历时用作占位符。正如你无疑知道的，典型月历的列通常按星期几对齐，最左边也许是星期一。当然，并非每个月都从星期一开始，因此需要“空”天来保持对齐。

请注意，Month 类还带有一个 buildWeeks 方法，以防你希望将 Week 作为对象来处理。为了避免冗长的讨论，我将留给你自行探索，但最终效果与使用 buildWeekDays 方法类似，即生成的 Week 中存在“空”天。




再次使用获取迭代器方法，我们可以循环遍历天数，一次处理一天，并在构建日历主体的过程中逐步完成：

```php
File: 13.php (excerpt)

// Define the days of the week for column headings
$daysOfWeek = array('Monday', 'Tuesday', 'Wednesday',
'Thursday', 'Friday', 'Saturday', 'Sunday');

// Build the column headings
$calendar .= "<tr class=\"cal_top\">\n";
// Display the days of the week
foreach ($daysOfWeek as $DayOfWeek) {
    $calendar .= "<th class=\"cal_week\">" . $DayOfWeek . "</th>";
}
$calendar .= "\n</tr>\n";

$salt = '';

// Loop through the day entries
while ($day = $month->fetch()) {

    // For displaying alternate row styles
    $salt = $salt == "cal_row" ? "cal_row_alt" : "cal_row";

    // If it's the start of a week, start a new row
    if ($day->isFirst()) {
        $calendar .= "<tr class=\"" . $salt . "\">\n";
    }

    // Check to see if day is an "empty" day
    if (!$day->isEmpty()) {

        // If it's the current day, highlight it
        if (!$day->isSelected()) {
            $calendar .= "<td>";
        } else {
            $calendar .= "<td class=\"cal_current\">";
        }

        // Display the day inside a link
        $calendar .= "<a class=\"cal_entry\" href=\"" .
            $_SERVER['PHP_SELF'] . "?y=" .
            $day->thisYear() .
            "&m=" . $day->thisMonth() .
            "&d=" . $day->thisDay() . "\">" .
            $day->thisDay() . "</a></td>";
    } else {
        // Display an empty cell for empty days
        $calendar .= "<td class=\"cal_entry\">\&nbsp;</td>";
    }

    // If it's the end of a week, close the row
    if ($day->isLast()) {
        $calendar .= "\n</tr>\n";
    }
}
$calendar .= "</table>\n";
?>
```

Day 类提供了 isFirst 和 isLast 方法，用于识别由 buildWeekDays 构建的、分别位于一周开头或结尾的天数。

isEmpty 方法允许我们识别“空”天数，如上文所述。如果找到这种天数，我们只需显示一个空表格单元格。如果天数不为空，则必须检查它是否为“选定”天数，为此我们使用了 isSelected 方法。

表格构建完成后，只需将其放入带有正确 CSS 定义的网页中，即可显示如图 6.3 所示的格式精美的表格。

## 图 6.3. 熟悉的月历

| 八月 | 2004 年九月 | 十月 |
| --- | --- | --- |
| 星期一 | 星期二 | 星期三 | 星期四 | 星期五 | 星期六 | 星期日 |
| | | 01 | 02 | 03 | 04 | 05 |
| 06 | 07 | 08 | 09 | 10 | 11 | 12 |
| 13 | 14 | 15 | 16 | 17 | 18 | 19 |
| 20 | 21 | 22 | 23 | 24 | 25 | 26 |
| 27 | 28 | 29 | 30 | | | |

## PHP 日程簿

到目前为止，我只使用了 Year、Month 和 Day 类。这对许多情况来说已经足够，但如果我们想构建一个内联网网站，例如，让人们可以查看自己的日程安排，该怎么办呢？登场：Hour 类。在接下来的解决方案中，我们将制作前面示例的新版本，但这次，在月份表格下方，我们将显示另一个包含小时的日表格。我们将在生成月历所用的代码下方添加以下代码。

首先，使用 $_GET 变量中的当前值创建一个新的 Day 对象。我们还需要初始化小时的 $_GET 变量（如果尚未设置），因为我们希望当前小时，或用户选择的小时，在日程表中显示为高亮。

```php
// Create a new day
$day = new Day($_GET['y'], $_GET['m'], $_GET['d']);

// Initialize the current hour
if (!isset($_GET['h'])) $_GET['h'] = date('H');

$sHours = array(new Hour($_GET['y'], $_GET['m'], $_GET['d'],
    $_GET['h']));

// Build the hour list for that day
$day->build($sHours);

$calendar .= "<br />\n";
$calendar .= "<table class=\"cal\" width=\"450\">\n";
$calendar .= "<caption>Your schedule for "
    . date('l', $day->thisDay(true)) .
    "</caption>\n";
```

由于这是一款办公应用程序，我们将显示的小时限制在办公时间内。此处的其余方法您之前实际上已经见过。

```php
$alt = '';

// Loop through the hours
while ($hour = $day->fetch()) {
    // Set a range for the hours; only between 8am and 6pm
    if ($hour->thisHour() < 8 || $hour->thisHour() > 18) {
        continue;
    }

    // For alternating row colors
    $alt = $alt == "cal_row" ? "cal_row_alt" : "cal_row";

    // If it's the current day, highlight it
    if (!$hour->isSelected()) {
        $calendar .= "<tr class=\"" . $alt . "\">\n";
    } else {
        $calendar .= "<tr class=\"cal_current\">\n";
    }

    $calendar .= "<td align=\"right\">";

    // Display the hour inside a link
    $calendar .= "<a class=\"cal_entry\" href=\"" .
        $_SERVER['PHP_SELF'] . "?y=" .
        $hour->thisYear() .
        "&m=" . $hour->thisMonth() .
        "&d=" . $hour->thisDay() .
        "&h=" . $hour->thisHour() . "\">".
        date('g A', $hour->thisHour(true)) . "</a></td>";

    $calendar .= "<td align=\"right\"> " .
        "Timestamp is " . $hour->getTimeStamp() . "</td>";

    $calendar .= "</tr>\n";
}
$calendar .= "</table>\n";
?>
```

为在每个条目上显示一些信息，我在此处添加了时间戳值。在实际应用中，您可以使用此值构建一个 SQL 查询，从用户的日记中选择特定日期的所有条目，然后在构建表格的每一行时，通过比较时间戳值来检查哪些数据库结果应显示。这需要多次遍历结果集<sup>4</sup>，但优于为日程表中的每个小时执行一次新查询。第 3 章中 MySQLResult 类的 fetch 方法每次到达末尾时都会自动重置查询结果集，允许您多次传递这些值。以下是如何操作的简化示例：

```php
$sql = "SELECT * FROM diary
WHERE
	date >= " . $day->thisDay(true) . " AND
	date < " . ($day->thisDay(true) + 86400) . "
ORDER BY date DESC";
```

4 如果您足够聪明，让每次迭代只处理结果集的一部分，实际上可以避免这种情况。如果您预计每天会有许多条目，值得探索这一点。

```php
$result = &$db->query($sql);
// Loop through the hours
while ($hour = $day->fetch()) {
    // Loop through the query result
    while ($row = $result->fetch()) {
        if ($row['date'] >= $hour->thisHour(true) &&
            $row['date'] < $hour->nextHour(true)) {
            // Display the entry here
        }
    }
}
```

图 6.4 演示了“日程簿”应该有的样子。

## 图 6.4. 使用 PHP 实现高度有序

| 七月 | 2003 年八月 | 九月 |
| :--- | :--- | :--- |
| 星期一 | 星期二 | 星期三 | 星期四 | 星期五 | 星期六 | 星期日 |
| 04 | 05 | 06 | 07 | 01 | 02 | 03 |
| 11 | 12 | 13 | 14 | 15 | 16 | 17 |
| 18 | 19 | 20 | 21 | 22 | 23 | 24 |
| 25 | 26 | 27 | 28 | 29 | 30 | 31 |

您的周四日程表

| 上午 8 点 | 时间戳为 1060840800 |
| 上午 9 点 | 时间戳为 1060844400 |
| 上午 10 点 | 时间戳为 1060848000 |
| 上午 11 点 | 时间戳为 1060851600 |
| 中午 12 点 | 时间戳为 1060855200 |
| 下午 1 点 | 时间戳为 1060858800 |
| 下午 2 点 | 时间戳为 1060862400 |
| 下午 3 点 | 时间戳为 1060866000 |
| 下午 4 点 | 时间戳为 1060869600 |
| 下午 5 点 | 时间戳为 1060873200 |
| 下午 6 点 | 时间戳为 1060876800 |

请注意，尽管我使用纯过程式代码渲染了日历的 HTML（这样做是为了让 Calendar 引擎的使用更易于理解），但在实际应用中，将代码封装到一个构建 HTML 并简化显示的类中可能更容易——甚至可以利用您将在第 9 章中看到的 PEAR::HTML_Table。您可能还想研究第二卷第 5 章中的缓存技术。渲染日历输出在 PHP 资源方面是一项昂贵的操作，因此如果您可以存储编译后的 HTML（假设日历不会频繁更改），将显著提高性能。

值得注意的是，分离开发日历数据结构的过程（由 `Calendar` 及其子类处理）与构建 HTML 的工作，其影响很大；这使得重用 `Calendar` 作为工具来构建对最终用户而言外观和行为不同的其他日历变得容易。

### 如何处理时区？

自不列颠主宰海洋以来，世界一直面临着一个问题：所有时间都集中在伦敦的一个名为格林威治的区域。格林威治如今是国家海事博物馆的所在地，也是许多光线昏暗的酒吧的所在地，在那里最好不要提到你是外地人。

用土包子的话说，时区在全球东西向运行，测量太阳每天达到最高点时，比格林威治早或晚多少个小时。似乎没有人在格林威治见过太阳，但这从未阻止早期的水手们，他们使用设定为格林威治标准时间 (GMT) 的时钟来计算自己绕地球旅行了多少东西方向。如今，GMT 也称为协调世界时 (UTC)、祖鲁时间、世界时，或者简单地说是世界时间。

对于当今的 Web 开发者来说，处理时区几乎和对早期探险者一样棘手，需要付出一些努力来确保正确。也许托管您网站的国家所在的时区与您所在的时区不同。您可能还需要允许访客设置自己的时区，以便您的网站可以相应地调整时间敏感内容。

您的主机应提供一台配置正确的服务器，该服务器提供的时间值可通过 PHP 的 `date` 和 `time` 函数使用。服务器还应准确配置其所在时区。您可以使用 PHP 的 `date` 函数检查这些值，如下所示：

```php
<?php
echo date('H:i:s T O');
?>
```

这将返回类似以下的内容：




## 我的时区是什么？

要确定要为全球主要城市设置的值，请访问 http://www.bsdi.com/xdate/。

但是，如何更改环境，使日期和时间函数显示你希望反映的特定时区的值呢？在 Linux 系统上，这可以通过使用 PHP 的 putenv 函数为当前脚本执行设置系统的 TZ 变量，以全局方式轻松实现：

```
<?php
echo 'Current time: ' . date('H:i:s T O') . '<br />';
putenv('TZ=Europe/London');
echo 'New time: ' . date('H:i:s T O');
?>
```

## putenv 和 Internet Information Services (IIS)

请注意，在某些 Windows 服务器（尤其是 Microsoft IIS）上，putenv 函数不仅影响当前脚本执行，还会影响整个服务器进程。

在上述示例中，首次调用脚本时，你会看到时区发生变化，但此后，两条 echo 语句都会显示相同的时区。要将服务器恢复到系统默认时区，你必须重启服务器，或再次使用 putenv 将 TZ 变量设置回其原始值。

在我的 Linux 服务器上，这会显示以下内容：

```
Current time: 09:31:10 EST -0500
New time: 14:31:10 GMT +0000

```

通过使用 php.ini 设置 auto_prepend_file，你可以将此更改应用到站点上执行的每个 PHP 脚本，确保所有日期或时间实例都使用正确的时区。如果你无法更改 php.ini，或需要将更改限制在服务器上的特定站点或目录，请使用包含类似以下命令的 .htaccess 文件：

```
php_value auto_prepend_file '/path/to/set_timezone.php'

```

在 Windows 系统上，则没这么幸运；如果你无法自行更改服务器的时区设置，就只能使用 PHP 来转换时区，这意味着你将无法直接调用日期和时间。

## 如何为 PHP 脚本计时？

随着你使用 PHP 构建越来越大、越来越复杂的应用程序，了解代码对整体性能的影响往往是个好主意；互联网本身已经很慢，尤其是对使用拨号上网的人来说，让访客等待不会鼓励他们再次光顾。发现脚本执行需要多长时间，可以通过 PHP 的 microtime 函数轻松实现：

```
<?php
function getMicroTime()
{
    list($usec, $sec) = explode(" ", microtime());
    return (float)$usec + (float)$sec;
}

$start = getMicroTime();

for ($i = 0; $i < 5; $i++) {
    sleep(1);
}

echo 'Script took: ' . (getMicroTime() - $start);
?>
```

上述代码告诉我的结果是“Script took: 4.9990350008011”，这是一个以秒为单位的时间。microtime 返回的字符串值格式为 decimal_part integer_part。拆分此结果并将它们相加，即可得到以秒为单位的浮点时间。这种脚本计时方法简单地涉及在脚本开始前记录时间，并在所有执行完成后再次记录时间。microtime 函数用于提供足够精确以供使用的时间。

如果你想了解站点内部的整体情况，可以使用 php.ini 设置 auto_prepend_file 和 auto_append_file 来计时所有脚本，或者使用类似下面的 .htaccess 文件：

```
php_value auto_prepend_file '/path/to/script_start.php'
php_value auto_append_file '/path/to/script_end.php'
```

结合我们在第 10 章中将讨论的日志机制，这将使你能够在整个站点上建立脚本性能统计信息。

## 如何使用 PHP 安排批处理作业？

能够使用 cron 作业^5 是按固定间隔执行脚本的理想方式，无论站点上发生什么。但是，如果你无法访问 cron，或者在缺乏有效“批处理执行”工具的系统上运行 PHP，则另一种替代方案以伪 cron[6] 的形式存在。如果你想寻找 PHP 开发者创造力的示例，无需再找，这就是一个！

伪 cron 的工作原理是利用站点上的正常访问在后台执行 PHP 脚本。特别巧妙的是，它使用表现为图像的脚本来执行其他 PHP 脚本，而不会影响访客正在查看的页面性能。你只需使用 HTML img 标签将图像脚本插入到经常查看的页面即可。

### 安装伪 cron

我使用的伪 cron 版本为 1.22。如果你的 php.ini 设置 short_open_tag 为 off，请确保编辑随伪 cron 提供的文件，以提供完整的 <?php 开始标记。

第一步是将 ZIP 文件的内容放置在站点上的某个位置——理想情况下放在 Web 目录之外的目录中，以防止任何潜在的安全风险。

接下来，按喜好编辑文件 pseudo-cron.inc.php 中的以下部分：

```
$cronTab = '/home/username/pseudocron/cronjobs/crontab.txt';
$writeDir = '/home/username/pseudocron/cronjobs/';
$useLog = 1;
```

$cronTab 变量指向包含 crontab 计划⁶ 的文件。其格式与传统 cron 非常相似（请参阅“进一步阅读”部分）。$writeDir 变量指定将用于写入 cron 执行日志文件的位置。在发行版中，这是一个相对目录位置；如果你已将代码放在安全目录中，则需要指定完整路径。你还需要为此目录提供公共读写权限，以便 Web 服务器用户有权写入它；这伴随着共享 Web 服务器用户通常会看到的安全警告：其他用户也将能够访问此目录。当然，这假设你希望写入日志文件；你可以通过将 $useLog 设置为 0 来关闭它们。

接下来，编辑 imagecron.php 中的以下行，以便它包含正确的文件：

```
include ("/home/username/pseudocron/pseudo-cron.inc.php");
```

文件 crontab.txt 用于指定将由伪 cron 执行的 PHP 脚本。例如：

```
#mi h d m dow job
0 1 * * * /home/user/pseudocron/cronjobs/dbbakup.php
*/30 9-17 * * 1-5 /home/user/pseudocron/cronjobs/rssupdate.php
0 2 * * * /home/user/pseudocron/cronjobs/webstats.php
0 9 1 * * /home/user/pseudocron/cronjobs/report.php
```

cron 计划格式需要一些时间来适应，但在网上有很好的描述（有关推荐，请参阅“进一步阅读”部分）。

在此示例中，第一个脚本 dbbakup.php（代表数据库备份）每天 01:00 运行。rssupdate.php 脚本（可能正在更新新闻源）在周一至周五 9:00 到 17:00 之间每 30 分钟运行一次（注意你也可以使用 Mon-Fri 代替 1-5）。每天第 2 小时运行 webstats.php，这是一个处理前一天捕获的访客数据的任务。最后，每月的第一天 09:00 运行 report.php 脚本，它会将关于站点的各种关键信息报告邮件发送给管理员。

crontab.txt 中指定的文件由 pseudo-cron.inc.php 包含。请注意，由你负责确保脚本不包含任何关键错误（这可能导致 pseudo-cron.inc.php 无法执行其他脚本）。

此外，如果脚本需要超过默认的 30 秒才能完成执行，你也必须使用 set_time_limit 或其他方式来处理，以确保每个任务都有足够的时间完成。

设置完成后，使用伪 cron 所需的一切就是显示带有指向 imagecron.php 的“假图像”的一些 HTML。例如：

```
<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Transitional//EN"
"http://www.w3.org/TR/xhtml1/DTD/xhtml1-transitional.dtd">
<html xmlns="http://www.w3.org/1999/xhtml">
<head>
<title>Pseudo-cron Example </title>
<meta http-equiv="Content-Type"
content="text/html; charset=iso-8859-1" />
</head>
<body>
<p>This is an example of pseudo-cron.
<img src="/pseudo_cron/imagecron.php" /></p>
</body>
</html>
```

不要忘记，伪 cron 实际执行的文件不应放置在访客可以直接访问的位置，否则你可能会在意料之外的时候发生 cron 作业！

## 进一步阅读

- ADODb 日期和时间库：http://php.weblogs.com/adodb_date_time_library
  本文侧重于延长 Unix 时间戳的生命周期。

- 使用 PHP 进行日期/时间处理：http://www.devshed.com/Server_Side/PHP/DateTime/
  一篇提供 PHP 日期和时间函数深入介绍的优秀文章。

- 使用 PHP 和 MySQL 的实际日期/时间示例：http://www.devarticles.com/art1/331/

^5Cron 是一种在大多数基于 Unix 的系统上运行的程序。它允许将任务（通常称为“cron 作业”）安排在固定间隔执行。
[6] http://www.bitfolge.de/?l=en&s=pseudocron

⁶要在 Unix 系统上设置由 cron 执行的任务，用户传统上必须使用名为 crontab 的单独程序。这个名称已扩展为用于指系统上配置的一组 cron 任务。




Red Hat Linux 定制指南第 28 章：自动化任务：https://www.redhat.com/docs/manuals/linux/RHL-9-Manual/custom-guide/ch-autotasks.html

Red Hat 对 cron 的基本介绍。另请参阅 crontab[11] 的 man 页面，以获取伪 cron 期望的调度文件格式的完整描述。

# 7 图像

构建网站不仅仅是显示 (X)HTML 格式的文本。“多媒体”这一统称描述了向桌面交付多种形式内容的过程，包括声音、文本和图像——甚至动画和电影。就图像而言，PHP 具有强大的功能。你可以做的远不止在 HTML 中添加静态图像。

何不自动添加水印以标识您的文件，或者上传图像并将其显示为适合您页面的正确大小的缩略图？更棒的是，如何从数据库中存储的数据实时渲染图表？我们将在后续页面中介绍所有这些内容及更多内容。

在*PHP 文选*的其他章节中，您会发现更多示例，例如将图像存储在 MySQL 中并显示它们（第 9 章）、使用文本渲染图像（第 II 卷，第 1 章），以及使用图像来“在后台”运行 PHP 脚本（第 II 卷，第 4 章）。本章专注于使用 PHP 显示图像时您可能希望解决的一些常见问题。

要使用此处的示例，您需要 PHP 的 **GD 图像库**。使用 GD 库的 PHP 函数在 PHP 手册[1]中有文档说明。完整的安装说明也在该处提供。

[1] http://www.php.net/image

由于 GIF 图像的专利问题[2]，GD 库对该格式的支持在 1.6 版本中停止。您可以在网上找到 GD 库的旧版本，但使用它可能会招致 Unisys 或 IBM 的法律风险。更令人兴奋的是，GD 库直到 1.6 版本才开始支持 PNG 格式（一种由较新浏览器支持的 GIF 免费替代品）。在此示例中，我假设您已安装内置了 Freetype、JPEG 和 PNG 支持的 GD 2.0 版本（该版本随最新版 PHP 捆绑提供）。

好消息是 GIF 格式的专利将于 2004 年到期，因此我们希望 GD 库很快能重新支持 GIF。在此之前，值得将 PNG 格式视为首选替代方案。PNG 能够支持完整的 32 位图像，而 GIF 仅支持 8 位。此外，PNG 使用更高效的压缩算法，与 8 位 GIF 相比，8 位 PNG 所使用的带宽更少。

## MIME 类型

MIME 代表 **多用途互联网邮件扩展**，这是一项最初设计用于帮助识别不同电子邮件内容类型的标准。MIME 此后已成为 _事实上的_ 标准，用于描述 Internet 上的内容类型。在 PHP 中处理图像时，掌握不同的内容类型非常重要，否则您可能会为一个简单的问题苦苦挣扎数小时。

通常，在将请求的内容发送到浏览器之前，Web 服务器必须使用特殊的 **内容类型** 标头来宣布内容类型，以便浏览器知道如何处理内容。例如，以下是服务器可能发送以宣布采用便携式网络图形 (PNG) 格式的图像的标头：

```
HTTP/1.1 200 OK
Date: Fri, 28 Mar 2003 21:42:44 GMT
Server: Apache/1.3.27 (Unix) PHP/4.3.1
Last-Modified: Wed, 26 Feb 2003 01:27:19 GMT
Content-Length: 1164
Connection: close
**Content-Type: image/png**
```

[2] http://www.gnu.org/philosophy/gif.html

Content-Type 标头用于指定当前 URL 上内容的 **MIME 类型**。在此示例中，MIME 类型是 `image/png`，表示 PNG 图像。

在 PHP 中，当我们从 PHP 脚本生成图像时，这一点变得很重要。默认情况下，PHP 脚本发送的 MIME 类型是 `text/html`（HTML 文档）。因此，在您的脚本发送图像而非 HTML 的情况下，您需要使用 PHP 的 `header` 函数来指定 MIME 类型。例如：

```php
<?php
header('Content-Type: image/png');
?>
```

您需要的图像 MIME 类型如表 7.1 所示。

### 表 7.1. 图像的 MIME 类型

| 图像格式 | MIME 类型 |
|---|---|
| JPEG 文件交换格式 (.jpeg/.jpg) | image/jpeg¹ |
| 便携式网络图形 (.png) | image/png |
| 图形交换格式 (.gif) | image/gif |
| Windows 位图 (.bmp) | image/bmp |
| 可缩放矢量图形 (.svg) | image/xml+svg |

¹Internet Explorer 理解 `image/jpeg` 类型，但在上传 JPEG 图像时，它会发送 `image/pjpeg` 类型。

## 如何创建缩略图？

如果您的网站允许上传图像（也许用于显示提交的内容），如何确保显示的图像大小合适？如果用户上传特别大的图像，在显示时可能会破坏页面布局。一个解决方案是创建 **缩略图**，它保证显示的图像永远不会超过特定的高度和宽度。

构建基本缩略图是一个五个阶段的过程：

- 1. 将源图像加载到 PHP 变量中。
- 2. 确定原始图像的高度和宽度。
- 3. 创建正确大小的空白缩略图图像。
- 4. 将原始图像复制到空白缩略图中。
- 5. 使用正确的内容类型显示缩略图。

让我们从 SitePoint 徽标的 JPEG 大尺寸版本创建一个缩略图：

```php
<?php
// Specify source image
$sourceImage = 'sample_images/sitepoint_logo.jpg';

// Specify thumbnail height and width
$thumbWidth = 200;
$thumbHeight = 90;

// Load the source image
$original = imagecreatefromjpeg($sourceImage);

// Get the size of the original
$dims = getimagesize($sourceImage);

// Create a blank thumbnail (note slightly reduced height)
$thumb = imagecreatetruecolor($thumbWidth, $thumbHeight);

// Copy a resized version of the original onto the thumbnail
imagecopyresampled($thumb, $original, 0, 0, 0, 0,
    $thumbWidth, $thumbHeight, $dims[0], $dims[1]);

// Send the content header
header("Content-type: image/jpeg");

// Display the image
imagejpeg($thumb);
?>
```

在上述示例中，我们使用 imagecreatefromjpeg 将图像从文件系统加载到 PHP 变量中。getimagesize 函数告诉我们图像的宽度和高度（稍后将详细介绍 getimagesize）。

imagecreatetruecolor 函数用于创建一个空白图像（在内存中，作为 PHP 变量），缩略图将被放置其中。请注意，正如函数名所示，这将创建一个 **真彩色**（24 位）图像，而不是您使用 `imagecreate` 所得到的 **基于调色板**（8 位）图像（有关图像信息的建议来源，请参阅“进一步阅读”部分）。`imagecreatefromjpeg` 函数从源文件创建真彩色图像，因此我们还需要缩略图是真彩色的。

`imagecopyresampled` 函数是从原始图像实际创建缩略图的关键点。它将图像的调整大小版本放置到空白缩略图图像中，并在过程中进行 **重采样**，以确保图像平滑调整大小。此函数的旧版本 `imagecopyresized` 以更粗糙的方式更改图像大小。如果需要，请参阅 PHP 手册以获取此函数参数的完整描述。

最后，在发送正确的内容类型标头后，我们使用 `imagejpeg` 输出完成的缩略图。图 7.1 显示了最终结果。虽然还有改进空间，但这是一个起点。

### 图 7.1. 我们的第一个缩略图

![](img/5b6cdf7cf4cf53e30b19e047895dc464_233_0.png)

让我们回到 `getimagesize` 函数——值得注意的就是它提供的信息：

```php
<?php
// Specify source image
$sourceImage = 'sample_images/sitepoint_logo.jpg';

// Get the size of the original
$dims = getimagesize($sourceImage);

echo '<pre>';
print_r($dims);
echo '</pre>';
?>
```

这将显示：


数组的第一个元素是图像的宽度，第二个元素是图像的高度。第三个元素是一个标识图像类型的数字，其中 1 表示 GIF，2 表示 JPEG，3 表示 PNG（更多内容请参阅 PHP 手册[3]）。请注意，mime 元素仅在 PHP 4.3.0 及更高版本中可用。

[3] http://www.php.net/getimagesize

## 缩略图类

到目前为止，一切顺利……但我们创建的缩略图会将原始图像拉伸至空白缩略图的完整尺寸。这会导致图像变形，除非它碰巧与缩略图具有相同的宽高比。相反，我们想要一个按比例缩放的原始图像版本，尽可能整齐地适配空白缩略图。在本节中，我们将编写一个正好能实现此功能的类。

该类还将支持处理尺寸小于缩略图的图像，如果需要，可以保持其原始大小。该类设计为仅处理 PNG 和 JPEG 文件，但可以轻松修改以支持其他类型。

与往常一样，我将专注于构建类的 API——即你可能在自己的代码中使用的部分——然后展示如何使用该类。完整代码已提供在代码存档中。

与任何类一样，我们从构造函数开始：

```php
/**
 * Thumbnail constructor
 * @param int max width of thumbnail
 * @param int max height of thumbnail
 * @param boolean (optional) if true image scales
 * @param boolean (optional) if true inflate small images
 * @access public
*/
function Thumbnail($maxWidth, $maxHeight, $scale = true,
    $inflate = true)
{
    $this->maxWidth  = $maxWidth;
    $this->maxHeight = $maxHeight;
    $this->scale     = $scale;
    $this->inflate   = $inflate;
}
```

Thumbnail 类的构造函数接受四个参数。前两个参数分别是缩略图的最大宽度和高度（以像素为单位）。第三个参数告诉类是应该按比例缩放图像以适应缩略图，还是仅仅将其拉伸（如之前的示例所示）。第四个参数告诉类如何处理过小的图像，即是否将其放大以填充缩略图。

将这些参数安全地存储在实例变量后，以下是构造函数的其余部分：

```php
// Consider modifying these to handle other image types
$this->types = array('image/jpeg', 'image/png');
$this->imgLoaders = array(
    'image/jpeg' => 'imagecreatefromjpeg',
    'image/png'  => 'imagecreatefrompng'
);
$this->imgCreators = array(
    'image/jpeg' => 'imagejpeg',
    'image/png'  => 'imagepng'
);
```

`$this->types` 列出了该类可以处理的 MIME 类型。`$this->imgLoaders` 列出了用于加载这些 MIME 类型图像的函数，而 `$this->imgCreators` 列出了用于创建 *新* 图像的函数。

Thumbnail 类提供了两种加载要转换图像的方法。第一种是 loadFile，允许你指定要加载的本地文件：

```php
/**
 * Loads an image from a file
 * @param string filename (with path) of image
 * @return boolean
 * @access public
 */
function loadFile($image)
{
 // Code omitted
}
```

第二种是 loadData，允许你传递存储在 PHP 变量中的二进制图像数据，因此你可以从存储在（例如）MySQL 表中的文件创建缩略图：

```php
/**
 * Loads an image from a string (e.g. database)
 * @param string the image data
 * @param mime mime type of the image
 * @return boolean
 * @access public
 */
function loadData($image, $mime)
{
 // Code omitted
}
```

除了图像数据外，你还需要将 MIME 类型作为第二个参数提供。通常，当图像存储在数据库中时，它们的 MIME 类型会与它们一起存储，如第 9 章所见。

```php
/**
 * If a filename is provided, creates the thumbnail using that
 * name. If not, the image is output to the browser
 * @param string (optional) filename to create image with
 * @return boolean
 * @access public
 */
function buildThumb($file = null)
{
 $creator = $this->imgCreators[$this->sourceMime];
 if (isset($file)) {
 return $creator($this->thumb, $file);
 } else {
 return $creator($this->thumb);
 }
}
```

buildThumb 方法用于渲染完成的缩略图。如果向此方法传递一个文件名，缩略图将使用你指定的名称存储为文件。否则，图像会直接输出到浏览器，因此你需要确保已先发送正确的 HTTP 标头。请注意，这里我们使用的是在构造函数中存储的图像函数名。

最后的公共方法用于获取有关缩略图的信息。getMime 方法返回 MIME 类型，可用于为缩略图生成 Content-Type 标头：

```php
/**
 * Returns the mime type for the thumbnail
 * @return string
 * @access public
 */
function getMime()
{
    return $this->sourceMime;
}
```

getThumbWidth 和 getThumbHeight 方法用于返回缩略图的宽度和高度（以像素为单位），然后你可以使用它们来创建 HTML img 标记，例如：

```php
/**
 * Returns the width of the thumbnail
 * @return int
 * @access public
 */
function getThumbWidth()
{
    return $this->thumbWidth;
}

/**
 * Returns the height of the thumbnail
 * @return int
 * @access public
 */
function getThumbHeight()
{
    return $this->thumbHeight;
}
```

这就完成了！让我们试用一下我们崭新的类：

```php
<?php
// Include the Thumbnail class
require_once 'Images/Thumbnail.php';

// Instantiate the thumbnail
$tn = new Thumbnail(200, 200);

// Load the image from a file
$tn->loadFile('sample_images/sitepoint_logo.jpg');

// Send the HTTP Content-Type header
header('Content-Type: ' . $tn->getMime());

// Display the thumbnail
$tn->buildThumb();
?>
```

上述示例显示了将文件名传递给 Thumbnail 类以创建缩略图。我们使用 PHP 的 header 函数连同 getMime 方法来发送正确的 HTTP 标头；然后只需调用 buildThumb 方法即可显示图像。结果如图 7.2 所示。

## 图 7.2. 按比例缩放的缩略图

![](img/5b6cdf7cf4cf53e30b19e047895dc464_238_0.png)

以下是另一个示例，用于展示 loadData 方法，并说明如何存储文件而不是直接输出：

```php
<?php
// Include the Thumbnail class
require_once 'Images/Thumbnail.php';

// Instantiate the thumbnail
$tn = new Thumbnail(200, 200);

// Load an image into a string (this could be from a database)
$image = file_get_contents('sample_images/sitepoint_logo.jpg');

// Load the image data
$tn->loadData($image, 'image/jpeg');

// Build the thumbnail and store as a file
$tn->buildThumb('sample_images/thumb_sitepoint_logo.jpg');
?>
<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Transitional//EN"
    "http://www.w3.org/TR/xhtml1/DTD/xhtml1-transitional.dtd">
<html xmlns="http://www.w3.org/1999/xhtml">
<head>
<title> Thumbnail Example </title>
<meta http-equiv="Content-Type"
    content="text/html; charset=iso-8859-1" />
</head>
<body>
<h1>Before...</h1>
<img src="sample_images/sitepoint_logo.jpg" />
<h1>After...</h1>
<img src="sample_images/thumb_sitepoint_logo.jpg"
    width="<?php echo $tn->getThumbWidth(); ?>"
    height="<?php echo $tn->getThumbHeight(); ?>" />
</body>
</html>
```

请注意，在为缩略图生成 img 标记时，我们使用 getThumbWidth 和 getThumbHeight 方法来正确完成宽度和高度属性。图 7.3 显示了生成的页面。

## 图 7.3. 之前和之后

![](img/5b6cdf7cf4cf53e30b19e047895dc464_240_0.png)

### 之后...

![](img/5b6cdf7cf4cf53e30b19e047895dc464_240_1.png)

最后，以下是如何从包含 PNG 和 JPEG 文件的目录中构建一个简单的缩略图显示（有关本示例中使用的内置 dir 类的详细信息，请参见第 4 章）。此第一部分读取目录；它查找没有缩略图的图像并创建它们。这样我们就无需每次都创建缩略图，节省了开销：

```php
<?php
// Include the Thumbnail class
require_once 'Images/Thumbnail.php';

// Open the sample_images subdirectory
$dir = dir('sample_images');

// Read through the files looking for images to convert
while ($image = $dir->read()) {
    // Get the file extension
    $ext = explode('.', $image);
    $size = count($ext);
    // Check that it's a valid file
    if (($ext[$size-1] == 'png' || $ext[$size-1] == 'jpg') &&
        preg_match('/^thumb_/', $image ) == 0 &&
        $image != '.' && $image != '..') {
```



// Check no thumbnail exists for this image
if (file_exists('sample_images/thumb_' . $image)) {
    continue;
} else {
    // Instantiate the thumbnail without scaling small images
    $tn = new Thumbnail(200, 200, TRUE, FALSE);

    // Create the thumbnail
    $tn->loadFile('sample_images/' . $image);
    $tn->buildThumb('sample_images/thumb_' . $image);
}
}
}

脚本随后遍历目录查找缩略图（以 thumb_ 开头的文件），并将找到的文件名添加到在页面正文中显示的表格中：

### 文件：5.php（摘录）

```php
// Rewind the directory listing
$dir->rewind();

// Start building an HTML table
$table = "<table border=\"1\" cellpadding=\"5\">\n";

// Read through the directory and add thumbnails to the table
while ($image = $dir->read()) {
    if (preg_match('/^thumb_/', $image) == 1 &&
        $image != '.' && $image != '..' ) {
        $table .= "<tr><td align=\"center\">";
        $table .= "<img src=\"sample_images/\" . $image . "\">";
        $table .= "</td></tr>\n";
    }
}

$table .= "</table>\n";

?>
<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Transitional//EN"
    "http://www.w3.org/TR/xhtml1/DTD/xhtml1-transitional.dtd">
<html xmlns="http://www.w3.org/1999/xhtml">
<head>
<title> Thumbnail Example </title>
<meta http-equiv="Content-Type"
    content="text/html; charset=iso-8859-1" />
</head>
<body>
<h1>Thumbnails...</h1>
<?php echo $table; ?>
</body>
</html>
```

该脚本输出示例见图 7.4。请注意，由于我们将 Thumbnail 类的 inflate（第四个）参数设置为 FALSE，因此小型徽标保持原始大小。

### 图 7.4. 缩略图列表

![](img/5b6cdf7cf4cf53e30b19e047895dc464_242_0.png)

## 如何向图像添加水印？

另一个你可能需要解决的常见问题是如何 **添加水印** 到图像，也就是说，如何放置某些标识图像或文本以表明你拥有版权。使用 GD 库和 PHP，这轻而易举！

如果你有一个带有透明背景的徽标或其他可识别的图形，可以轻松地将其放置在另一张图像上：

```php
<?php
// Load the original image
$image = imagecreatefrompng('sample_images/mysql_logo.png');

// Get image width
$iWidth = imagesx($image);

// Allow transparent images...
imagealphablending($image, true);

// Get the watermark image
$watermark = imagecreatefrompng(
    'sample_images/sitepoint_watermark.png');

// Get the height and width
$wmWidth = imagesx($watermark);
$wmHeight = imagesy($watermark);

// Find the far right position
$xPos = $iWidth - $wmWidth;

// Copy the watermark to the top right of original image
imagecopy($image, $watermark, $xPos, 0, 0, 0, $wmWidth,
    $wmHeight);

// Send the HTTP content header
header('Content-Type: image/png');

// Display the final image
imagejpeg($image);
?>
```

这个过程简单来说就是加载原始图像并启用 **Alpha 混合**（绘制透明度），以便可以将带有透明背景的图像放置在其上。加载“水印”图像，然后在获取其高度和宽度后，使用 imagecopy 将水印放置在原始图像上。

### 图 7.5. 海豚品牌

![](img/5b6cdf7cf4cf53e30b19e047895dc464_244_0.png)

在图像上显示文本更加简单。例如：

```php
<?php
// Load the original image
$image = imagecreatefrompng('sample_images/mysql_logo.png');

// Get a color and allocate to the image pallet
$color = imagecolorallocate($image, 153, 153, 153);

// Add the text to the image
imagestring($image, 3, 0, 0, 'Skippy 2003', $color);

// Send the HTTP content header
header('Content-Type: image/png');

// Display the final image
imagejpeg($image);
?>
```

imagecolorallocate 函数允许你通过指定红、绿、蓝分量来创建用于在图像上绘制的新颜色。该函数返回一个数字，用于在图像中标识该颜色。

一旦拿到颜色，你就可以使用 imagestring 函数将文本放置在图像上。该函数的第二个参数是字体编号，数字 1 到 5 指内置字体。你可以使用 imagefontload 使自定义字体可用。第三个和第四个参数表示文本应在图像上绘制的水平和垂直坐标。其余参数不言自明。

脚本的输出如图 7.6 所示。

### 图 7.6. 难道那应该是 Flipper 吗？

![](img/5b6cdf7cf4cf53e30b19e047895dc464_245_0.png)

## 如何使用 PHP 显示图表和图形？

以图形形式显示数据是与网站访问者沟通的强大方式，并帮助自己确切了解网站的使用情况。图表可以显示从每月网站流量统计（如第 II 卷第 4 章所示）到网站上的销售报告等任何内容。

许多项目扩展了 PHP 渲染图像的基本功能，允许将数据显示为某种形式的图表或图形。其中首屈一指的是出色的 JpGraph 库[4]，这是一个用 PHP 编写的项目，充分利用了 GD 库和 PHP 的图像函数。使用 JpGraph 可以做很多事情，详细探讨超出了本书范围。文档超过 1MB，非常出色，并提供了许多有用的示例。我还在本章末尾推荐了一些进一步阅读的材料。不过，这里我将向你展示如何从同一简单数据集中显示条形图和饼图。

请注意，JpGraph 仅免费用于非商业用途（请确保阅读网站上的许可信息）。此处使用的版本是 1.11。此处的代码还假设你已将 jpgraph/src/ 目录添加到 PHP 包含路径中，以便可以加载 JpGraph 类文件。

[4] http://www.aditus.nu/jpgraph/index.php

## JpGraph 与 PHP 通知

取决于你使用的 JpGraph 版本，如果在 `php.ini` 中打开了 PHP 的错误通知，可能会遇到问题。生成的错误消息可能导致图表图像无法显示。本章中的示例明确禁用了通知以避免此问题。有关如何控制错误报告的更多信息，请参见第 10 章。

## 条形图

首先，让我们看看如何使用 JpGraph 生成条形图。

假设它在某个包含路径中可用，在此示例中我们将包含核心“引擎”以及条形图类。接下来，我们设置两个示例数据数组，将用于图表的 X 轴和 Y 轴。在实际应用中，这些可能是从 MySQL 中获取的结果。

```php
<?php
// JpGraph does not work with notices enabled
error_reporting(E_ALL ^ E_NOTICE);

// Include the necessary JpGraph libraries
require_once 'jpgraph.php'; // Core engine
require_once 'jpgraph_bar.php'; // Bar graph

// Sample sales data: could be a database query
$xdata = array('Mousemats', 'Pens', 'T-Shirts', 'Mugs'); // X Axis
$ydata = array(35, 43, 15, 10); // Y Axis
```

在大多数情况下，JpGraph API 不言自明，并附带完整（且有用）的 API 文档。从我们的数据数组生成图表的第一步是设置图表本身的“基础”，例如大小和背景颜色：

```php
// Set up the graph
$graph = new Graph(400, 200, 'auto'); // Width, height
$graph->img->SetMargin(40, 20, 20, 40); // Margin widths
$graph->SetScale('textlin'); // X text, Y linear scale
$graph->SetColor('green'); // Plot background green
$graph->SetMarginColor('navy'); // Margin color navy
$graph->SetShadow(); // Use a drop shadow
$graph->SetFrame(true, 'blue'); // Blue frame
```

为图表添加标题不是问题。JpGraph 内置了你可能需要的大多数有用字体，例如 Verdana 和 Courier。

```php
// Set up the graph title
$graph->title->Set('Sales Figures for March'); // Title text
$graph->title->SetColor('white'); // Title color
$graph->title->SetFont(FF_VERDANA, FS_BOLD, 14); // Title font
```

现在，让我们设置 X 轴。这里，标签是使用 SetTickLabels 方法分配的，刻度是 X 轴上每个间隔的标记。

```php
// Set up the X Axis
$graph->xaxis->title->Set('Product Type'); // Text
$graph->xaxis->title->SetColor('yellow'); // Color
$graph->xaxis->title->SetFont(FF_VERDANA, FS_BOLD, 10); // Font
$graph->xaxis->SetTickLabels($xdata); // Labels
$graph->xaxis->SetColor('silver', 'orange'); // Colors
$graph->xaxis->SetFont(FF_VERDANA, FS_NORMAL, 8); // Font
$graph->xaxis->HideTicks(); // Ticks
```

添加 Y 数据后，Y 轴将自动生成数值。

```php
// Set up the Y Axis
$graph->yaxis->title->Set('Units Sold'); // Text
$graph->yaxis->title->SetColor('yellow'); // Color
$graph->yaxis->title->SetFont(FF_VERDANA, FS_BOLD, 10); // Font
$graph->yaxis->SetColor('silver', 'orange'); // Colors
$graph->yaxis->SetFont(FF_VERDANA, FS_NORMAL, 8); // Font
$graph->yaxis->HideTicks(); // Ticks
```

以下代码实际在图表上绘制条形：

```php
// Create the Bar graph plot
$bplot = new BarPlot($ydata); // Y data
$bplot->SetWidth(0.75); // Width of bars
$scol = array(255, 51, 204); // Gradient start
$ecol = array(204, 0, 102); // Gradient end
$bplot->SetFillGradient($scol, $ecol, GRAD_VER); // Add gradient
```





剩下的就是将柱状图添加到图表中，并将其发送到浏览器：

```
File: 8.php (excerpt)

// Finishing
$graph->Add($bplot);    // Add bar plot to graph
$graph->Stroke();       // Send to browser
?>
```

图7.7展示了结果。仅用七十一行PHP代码就能做到这一点，不错吧！

## 图7.7. 对钢笔的巨大需求

![](img/5b6cdf7cf4cf53e30b19e047895dc464_248_0.png)

## 饼图

JpGraph还可以轻松构建的另一种图表是饼图。让我们使用上一个示例中的示例数据来构建一个饼图。

在脚本开始处，必须包含饼图和3D饼图类：

```
File: 9.php (excerpt)

<?php
// JpGraph does not work with notices enabled
error_reporting(E_ALL ^ E_NOTICE);

// Include the necessary JpGraph libraries
require_once 'jpgraph.php';      // Core engine
require_once 'jpgraph_pie.php';  // Pie chart
require_once 'jpgraph_pie3d.php';// 3D Pie chart

// Sample sales data: could be a database query
$xdata = array('Mousemats', 'Pens', 'T-Shirts', 'Mugs'); // X Axis
$ydata = array(35, 43, 15, 10); // Y Axis
```

这次，我们不是使用Graph类，而是使用PieGraph类：

```
File: 9.php (excerpt)
// Set up the graph
$graph = new PieGraph(400, 200, 'auto'); // Width, height
$graph->SetMarginColor('yellow'); // Margin color yellow
$graph->SetShadow(); // Use a drop shadow
$graph->SetFrame(true, 'red'); // Red frame
```

标题的设置与之前相同：

```
File: 9.php (excerpt)
// Set up the graph title
$graph->title->Set('March Sales'); // Title text
$graph->title->SetColor('navy'); // Title color
$graph->title->SetFont(FF_VERDANA, FS_BOLD, 14); // Title font
```

我们还需要一个图例来标识饼图的每个部分代表什么：

```
File: 9.php (excerpt)
// Set up the pie segment legend
$graph->legend->SetColor('navy'); // Legend text color
$graph->legend->SetFillColor('orange'); // Legend background color
$graph->legend->Pos(0.05, 0.5); // Legend position
```

现在，我们创建3D饼图，使用Y数据实例化它，并使用X数据作为图例：

```
File: 9.php (excerpt)
// Set up 3D pie chart
$pie = new PiePlot3d($ydata); // Instantiate 3D pie with Y data
$pie->SetLegends($xdata); // Add X data to legends
$pie->SetTheme('water'); // Set color theme
$pie->SetCenter(0.39); // Center relative to X axis
$pie->SetSize(100); // Size of pie radius in pixels
$pie->SetAngle(30); // Set tilt angle of pie
$pie->ExplodeSlice(0); // Pop out a slice
$pie->ExplodeSlice(1); // Pop out another slice
```

在图表上的每个部分旁边，我们将显示一个标签，以标识该部分所代表的整体百分比：

```
// Set up values against each segment
$pie->value->SetFont(FF_VERDANA, FS_NORMAL, 10); // The font
$pie->value->SetColor('navy'); // Font color
```

最后，我们将3D饼图添加到图表中，并将其发送到浏览器：

```
// Finishing
$graph->Add($pie); // Add bar plot to graph
$graph->Stroke(); // Send to browser
?>
```

结果如图7.8所示。

## 图7.8. 谦卑之饼

![](img/5b6cdf7cf4cf53e30b19e047895dc464_250_0.png)

JpGraph是PHP的首选图表解决方案，因为它提供了比我们在此处看到的示例更多的功能。值得注意的是，它允许您将呈现的图表存储为PNG文件，因此您可以呈现一次，以后重复使用完成的图像。

## 如何防止图片“热链接”？

您可能遇到的一个问题（尤其是如果您的网站托管了独特的图片）是，其他网站从它们的页面“热链接”到您的图片，这使得您的酷图片看起来像是由它们托管或拥有。除了这里可能存在的版权问题外，外部网站“热链接”您的图片还可能占用您的带宽。

已经设计了不同的解决方案，例如使用Apache的mod_rewrite来检查浏览器提供的引荐信息（这并不总是可靠的），以确保来源是本地网页。例如：

```
SetEnvIfNoCase Referer "^http://www\.sitepoint\.com/" locally_linked=1
SetEnvIfNoCase Referer "^http://sitepoint\.com/" locally_linked=1
SetEnvIfNoCase Referer "^$" locally_linked=1
<FilesMatch "\.(gif|png|jpe?g)$">
    Order Allow,Deny
    Allow from env=locally_linked
</FilesMatch>
```

另一种选择是使用会话来确定查看图片的人是您网站的访客。诀窍是注册一个访客必须拥有才能查看图片的会话变量，然后使用第二个脚本来呈现图片。例如：

```
<?php
// Start a session
session_start();

// Register a variable in the session
$_SESSION['viewImages'] = TRUE;
?>
<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Strict//EN"
    "http://www.w3.org/TR/xhtml1/DTD/xhtml1-strict.dtd">
<html xmlns="http://www.w3.org/1999/xhtml">
<head>
<title> Preventing Hotlinking </title>
<meta http-equiv="Content-Type"
content="text/html; charset=iso-8859-1" />
</head>
<body>
<p> Here is the image:</p>
<img src="11.php?img=php-big.png" />
</body>
</html>
```

请注意，上述代码注册了一个名为viewImages的会话变量，然后使用img标签指向将获取图片的PHP脚本。以下是该脚本的代码：

```
File: 11.php

<?php
// Start a session
session_start();

// Check to see if $viewImages is registered
if (isset($_SESSION['viewImages']) &&
    $_SESSION['viewImages'] == TRUE) {

    // An array of available images
    $images = array(
        'sitepoint_logo.jpg',
        'php-big.png'
    );

    // If $_GET['img'] is set and in available...
    if (isset($_GET['img']) && in_array($_GET['img'], $images)) {

        // Get the image information
        $dims = getimagesize('sample_images/' . $_GET['img']);

        // Send the correct HTTP headers
        header('content-disposition: inline; filename=' .
            $_GET['img']);
        header('content-type: ' . $dims['mime']); # PHP 4.3.x +
        header('content-length: ' .
            filesize('sample_images/' . $_GET['img']));

        // Display the image
        readfile('sample_images/' . $_GET['img']);
    } else {
        die('Invalid or no image specified');
    }
} else {
    die('This image is protected from hotlinking');
}
?>
```

该脚本首先检查viewImages会话变量是否已设置为TRUE。如果是，并且通过$_GET['img']提供的图片名称已在数组$images中注册，则脚本使用您之前看到的getimagesize函数来获取图片的正确MIME类型，发送标头并显示它。

这应该能阻止所有执着的“热链接者”。

请注意，在第II卷第1章中，我开发了一个Session类，用于封装所有对PHP会话API的调用。修改后的上述示例以使用Session类，如下所示：

```
<?php
// Include the session class
require_once 'Session/Session.php';

// Instantiate the Session class
$session = new Session();

// Register a variable in the session
$session->set( 'viewImages', TRUE );
?>
<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Transitional//EN"
"http://www.w3.org/TR/xhtml1/DTD/xhtml1-transitional.dtd">
<html xmlns="http://www.w3.org/1999/xhtml">
<head>
<title> Preventing Hotlinking </title>
<meta http-equiv="Content-Type"
content="text/html; charset=iso-8859-1" />
</head>
<body>
<p>Here is the image:</p>
<img src="11.php?img=php-big.png" />
</body>
</html>
```

```
<?php
// Include the Session class
require_once 'Session/Session.php';

// Instantiate the Session class
$session = new Session();

// Check to see if $viewImages is registered
if ($session->get('viewImages')) {

    // An array of available images
    $images = array(
        'sitepoint_logo.jpg',
        'php-big.png'
    );

    // If $_GET['img'] is set and in available...
    if (isset($_GET['img']) && in_array($_GET['img'], $images)) {

        // Get the image information
        $dims = getimagesize('sample_images/' . $_GET['img']);

        // Send the HTTP headers
        header('content-disposition: inline; filename=' .
            $_GET['img']);
        header('content-type: ' . $dims['mime']);
        header('content-length: ' . filesize('sample_images/' .
            $_GET['img']));

        // Display the image
        readfile('sample_images/' . $_GET['img']);
    } else {
        die('Invalid image specified');
    }
} else {
    die('This image is protected from hotlinking');
}
?>
```

一个更实际的替代方案是将图片列表存储在数据库中。无论您如何操作，重要的是要验证请求的文件是您打算授予访问权限的文件；否则，您可能会允许访问超出预期的内容。

## 进一步阅读

- 首先阅读我！http://www.sketchpad.net/readme.htm

这篇文章很好地解释了计算机图形学的基础知识。如果您对GD库有宏伟计划，这是必读文章。

- 即时生成图像：http://hotwired.lycos.com/webmonkey/01/21/index4a.html

这是Webmonkey对PHP图像函数的介绍。





- 使用 PHP 开发专业质量图表：
  http://www.zend.com/zend/tut/tutsweat3.php

  这是一份关于使用 JpGraph 的实用教程。

# 8 电子邮件

构建在线应用程序不仅仅是将页面交付给 Web 浏览器。对于大多数网站，电子邮件是保持与访问者联系、构建用户注册系统等各种用途的必备工具。

使用 PHP 的 mail 函数发送简单电子邮件非常简单；只需一行代码即可发送一条消息——还有什么比这更简单呢？

mail 函数可以与本地 sendmail 客户端（一种在基于 Unix 的系统上广泛使用的电子邮件应用程序）集成，也可以与远程 SMTP（简单邮件传输协议）服务器集成，前提是你没有 sendmail 兼容的客户端。你的 Web 主机商应该为你设置好这些，但如果你在 Windows 开发环境下开发，你需要告诉 PHP 用于发送邮件的 SMTP 服务器。在绝大多数情况下，这将是你 ISP 提供的 SMTP 服务器。

要进行此设置，你需要修改 php.ini 中的以下设置：

```
[mail function]
; For Win32 only.
SMTP = smtp.yourdomain.com

; Default value
smtp_port = 25

; For Win32 only.
sendmail_from = you@yourdomain.com
```

在本章中，我们将重点介绍一个类，它能让构建更复杂的电子邮件变得轻松：PHPMailer[1]。PHPMailer 根据较小 GNU 公共许可证授权，为你可能希望从网站发送的任何内容提供了稳健的 API。它可能不像一行代码那样简单，但它肯定让发送复杂电子邮件更加方便！本章中使用的版本是 1.65。

### 如何简化复杂电子邮件的生成？

使用 mail 函数对于简单消息没问题，但有许多功能你需要自己实现。当你决定希望自己的电子邮件地址出现在消息的“From”字段中时，这起初会变得明显，当你尝试在收件人地址旁添加姓名、尝试抄送电子邮件等时，情况会变得更加复杂。

Kevin Yank 在《PHP 中的高级电子邮件》中详细讨论了这些问题（见本章末尾的“进一步阅读”部分），因此你确切地知道涉及哪些内容。

PHPMailer 为 mail 函数添加了大量功能，包括附件、HTML 电子邮件和混合格式电子邮件；它还能够完全绕过 mail 函数并直接连接到 SMTP 服务器。其 API 使构建更复杂的电子邮件变得非常容易。

你首先需要做的是下载 PHPMailer 并将其放在包含路径中的某个位置。本书随附的类库中提供了版本 1.65。

PHPMailer 的最基本用法如下：

```
<?php
// Include the phpmailer class
require 'ThirdParty/phpmailer/class.phpmailer.php';

// Instantiate it
$mail = new phpmailer();

// Define who the message is from
$mail->From = 'you@yourdomain.com';
$mail->FromName = 'Your Name';

// Set the subject of the message
$mail->Subject = 'Test Message';

// Add the body of the message
$body = 'This is a test';
$mail->Body = $body;

// Add a recipient address
$mail->AddAddress('you@yourdomain.com', 'Your Name');

// Send the message
if (!$mail->Send()) {
    echo 'Mail sending failed';
} else {
    echo 'Mail sent successfully';
}
?>
```

[1] http://phpmailer.sourceforge.net/

如你所见，PHPMailer 暴露给公共使用的方法和类成员变量相当自解释。虽然与使用 mail 函数所需的代码行数明显多得多，但它易于读取，并隐藏了正确格式化 SMTP 标头所涉及的复杂性。

### 如何将附件添加到消息中？

使用 PHPMailer，你实际上可以使用三种方法将附件添加到消息中——两种用于一般文件，一种专门用于图片：

### AddAttachment(path, name [, encoding[, type]])

此方法用于已位于服务器上的文件。你需要提供文件的路径和名称。请注意，encoding 通常最好保留默认值 "base64"，而你可能希望通过 type 参数提供更具体的 MIME 类型¹。

> 1. 常见 MIME 类型列表可在 http://www.hivemail.com/mime.types.php 上找到。MIME 类型在第 7 章中有更详细的讨论。

### AddStringAttachment(string, filename[, encoding[, type]])

使用 AddStringAttachment，你可以向 PHPMailer 提供已存储在 PHP 变量中的文件，例如刚刚上传的文件或存储在 MySQL 中的文件。

### AddEmbeddedImage(path, cid, name[, encoding[, type]])

使用 AddEmbeddedImage，你可以附加一张图片并为其提供 ID（通过 cid），从而允许你将其嵌入 HTML 电子邮件正文中。

下面是使用 AddAttachment 方法的示例：

```
<?php
// Include the phpmailer class
require 'ThirdParty/phpmailer/class.phpmailer.php';

// Instantiate it
$mail = new phpmailer();

// Modify this
$YourEmail   = 'your@yourdomain.com';
$YourName    = 'Your Name';

// Modify this
$RecipientEmail = 'your@yourdomain.com';
$RecipientName = 'Your Name';

// Define who the message is from
$mail->From     = $YourEmail;
$mail->FromName = $YourName;

// Set the subject of the message
$mail->Subject = 'Test Attachment';

// Add the body of the message
$body        = 'This message has an attachment';
$mail->Body  = $body;

// Add an attachment,
if (!$mail->AddAttachment('./files/php_logo.gif',
                          'php_logo.gif',
                          'base64', 'image/gif')) {
    echo 'Failed to attach file!<br />';
}

// Add a recipient address
$mail->AddAddress($recipientEmail, $recipientName);

// Send the message
if (!$mail->Send()) {
    echo 'Mail sending failed';
} else {
    echo 'Mail sent successfully';
}
?>
```

为了演示 AddStringAttachment 方法，让我们使用 PEAR::HTML_QuickForm 库（在第 9 章中有详细介绍）来构建一个简单的文件上传表单：

```
<?php
// Include the QuickForm class
require_once 'HTML/QuickForm.php';

// Include the phpmailer class
require 'ThirdParty/phpmailer/class.phpmailer.php';

// Modify this
$yourEmail = 'you@example.com';
$yourName = 'Your name';

// Instantiate QuickForm
$form = new HTML_QuickForm('imageUpload', 'POST');

// Add the recipient name field
$form->addElement('text', 'name', 'Recipient Name: ');
$form->addRule('name', 'Enter a name', 'required', NULL, 'client');

// Add the recipient address field
$form->addElement('text', 'mailTo', 'Recipient Email: ');
$form->addRule('mailTo', 'Enter an email address', 'required', NULL, 'client');
$form->addRule('mailTo', 'Enter a valid email address', 'email', NULL, 'client');

// Add the subject field
$form->addElement('text', 'subject', 'Subject: ');
$form->addRule('subject', 'Enter a subject', 'required', NULL,
    'client');

// Add the message body
$form->addElement('textarea', 'body', 'Message: ');
$form->addRule('body', 'Add a body to the message', 'required',
    NULL, 'client');

// The file upload field
$form->addElement('file', 'image', 'Select Image: ');
$form->addRule('image', 'The maximum file size is 56k',
    'maxfilesize', 57344);
$form->addRule('image', 'The file must be an image', 'mimetype',
    array('image/gif', 'image/jpeg', 'image/png'));
$form->addRule('image', 'No file selected.', 'uploadedfile', NULL,
    'client');

// The submit button
$form->addElement('submit', 'submit', 'Send');
```

获取表单提交数据后，我们现在可以使用 PHPMailer 从 PHP 生成的表单发送带附件的电子邮件：

```
if ($form->validate()) {
    // Fetch the details of the file
    $name = $form->_submitFiles['image']['name'];
    $type = $form->_submitFiles['image']['type'];

    // Fetch file
    $filename = $form->_submitFiles['image']['tmp_name'];
    $fp = fopen($filename, 'r');
    $contents = fread($fp, filesize($filename));
    fclose($fp);

    // Instantiate it
    $mail = new phpmailer();

    // Define who the message is from
    $mail->From = $yourEmail;
    $mail->FromName = $yourName;

    // Set the subject of the message
    $mail->Subject = $form->getSubmitValue('subject');

    // Add the body of the message
    $mail->Body = $form->getSubmitValue('body');
```





```php
// Add the contents of the form upload
$mail->AddStringAttachment($contents, $name, 'base64', $type);

// Add a recipient address
$mail->AddAddress($form->getSubmitValue('mailTo'),
    $form->getSubmitValue('name'));

// Send the message
if (!$mail->Send()) {
    echo 'Mail sending failed';
} else {
    echo 'Mail sent successfully';
}
} else {
$form->display();
}
?>
```

生成的表单如图 8.1 所示。

## 图 8.1. 发送带附件的电子邮件

![](img/5b6cdf7cf4cf53e30b19e047895dc464_263_0.png)

- * 表示必填字段

我们将在下一个解决方案中查看 AddEmbeddedImage 方法。

## 如何发送 HTML 电子邮件？

一些电子邮件客户端，例如 Outlook Express 和许多基于 Web 的客户端，能够理解放置在电子邮件正文中的 HTML。使用 PHPMailer，向电子邮件添加 HTML 甚至将附加图片嵌入文档中非常简单。该类会自动确定您是否在消息正文中放置了 HTML，并相应地设置正确的 MIME 头。您还可以添加替代文本消息，并且使用 AddEmbeddedImage，您可以将附加图片放置在 HTML 消息的正文中。

将所有这些整合到一个示例中，结果如下：

```php
<?php
// Include the phpmailer class
require 'ThirdParty/phpmailer/class.phpmailer.php';
// Instantiate it
$mail = new phpmailer();
// Modify this
$yourEmail = 'you@example.com';
$yourName = 'Your Name';
// Modify this
$recipientEmail = 'you@example.com';
$recipientName = 'Your Name';
// Define who the message is from
$mail->From = $yourEmail;
$mail->FromName = $yourName;
// Set the subject of the message
$mail->Subject = 'Test HTML Email';
// Add the HTML body of the message
$html = '<b>Hi ' . $recipientName . '</b><br />';
// Embed an image using cid:12345
$html .= 'This page was generated by <img src="cid:12345" />';
// Add message to body
$mail->Body = $html;
// Add the plain text alternative
$txt = "Hi " . $recipientName . "!\n";
$txt .= "This page was generated by PHP";
// Add message as alternative
$mail->AltBody = $txt;
// Add an embedded attachment identify the cid
if (!$mail->AddEmbeddedImage('./files/php_logo.gif',
    '12345',
    'php_logo.gif',
    'base64', 'image/gif')) {
    echo 'Failed to attach file!<br />';
}
// Add a recipient address
$mail->AddAddress($recipientEmail, $recipientName);
// Send the message
if (!$mail->Send()) {
    echo 'Mail sending failed';
} else {
    echo 'Mail sent successfully';
}
?>
```

这会发送一条多部分消息，一部分是 HTML，另一部分是纯文本，此外还有一个通过 img 标签嵌入 HTML 中的图片。

请注意，支持 HTML 中嵌入图片的邮件客户端更少，不过大多数主要邮件客户端（包括 Outlook、Outlook Express、Eudora、Netscape、Mozilla Mail 和 Evolution）都支持。

## 如何给一群人发邮件？

有时，一次性给多个人发邮件非常有用。而有时，给一群人发邮件被称为垃圾邮件——我相信您使用 PHP 时肯定不会这么做！

使用 PHPMailer，您可选用 addCC 和 addBCC 方法，它们允许您向这些字段添加多个地址，操作方式与 addAddress 方法相同。不过，这种方法可能不符合您的需求，因为如果将所有地址都列在单封电子邮件的头中，超大的分发列表很快就会让您的电子邮件服务器不堪重负。

更好的方法是逐封发送邮件，同时复用同一个 PHPMailer 类实例：

```php
File: 5.php

<?php
// Include the phpmailer class
require 'ThirdParty/phpmailer/class.phpmailer.php';

// Instantiate it
$mail = new phpmailer();

// Modify this
$yourEmail = 'you@example.com';
$yourName = 'Your Name';

// An array of recipients: Modify these
$recipients = array(
    'Your Name1' => 'recipient@example.com',
    'Your Name2' => 'recipient@example.com',
    'Your Name3' => 'recipient@example.com'
);

// Define who the message is from
$mail->From = $yourEmail;
$mail->FromName = $yourName;

// Set the subject of the message
$mail->Subject = 'Test Group Mail';

// Add the body of the message
$body = 'This message is being sent to a group';
$mail->Body = $body;

// Look through the recipients
foreach ($recipients as $name => $address) {
    // Add a recipient address
    $mail->AddAddress($address, $name);

    // Send the message
    if (!$mail->Send()) {
        echo 'Mail sending failed to ' . $address . '<br />';
    } else {
        echo 'Mail sent successfully to ' . $address . '<br />';
    }

    // Reset the address
    $mail->clearAddresses();
}
}

echo 'Finished sending emails<br />';
?>
```

在上面的示例中，我们复用了同一个 PHPMailer 实例，为其设置了消息及其发件人。对于 $recipients 数组中的每个元素（该数组旨在模拟数据库查询的结果），我们可以向 PHPMailer 实例添加一个地址，发送消息，然后再使用 clearAddresses 方法将其移除。请注意，PHPMailer 还有一个 clearAllRecipients 方法，可移除任何 CC 或 BCC 条目，以及一个 clearAttachments 方法，可移除任何附加文件。要替换消息的正文或主题，您只需像以前一样为其赋予新值：

`$mail->Body = $body;`

对于非常大的分发列表，简单的 foreach 循环远远不够——您可能会用消息淹没邮件服务器！相反，您需要想出一种以服务器能够处理的速度发送消息的方法。实现此目的的最简单方式是使用 PHP sleep 函数，每发送大约十条消息就暂停脚本一次。您还需要使用 set_time_limit 函数，允许脚本运行时间超过默认的三十秒限制。

## 如何使用 PHP 处理来邮？

您已经看到，使用 PHP 发送邮件毫无问题。但使用 PHP 处理来邮呢？如果您的网站托管在 Linux 系统上，您会很高兴地听到，经过少量调整后，您应该能够让 PHP 检查来邮。此外，PHP 有许多用于读取电子邮件和提取所需信息的机制，例如 IMAP 扩展[3]、Mailparse 扩展[4]，以及一个用 PHP 编写的功能较为有限的 PEAR 包 PEAR::Mail_Mime[5]。由于本章侧重于 PHP 内置功能而非深奥的扩展，我们将在此简要了解 PEAR::Mail_Mime 有何提供。

- [3] http://www.php.net/imap
- [4] http://www.php.net/mailparse
- [5] http://pear.php.net/package-info.php?pacid=21

在此解决方案中，我假设您的网站托管在基于 Linux 的系统上，能够通过命令提示符访问服务器，能够从命令提示符运行 PHP，并且服务器上使用 sendmail 处理电子邮件。我知道这是一长串要求，但这种相当常见的配置大大简化了问题。

首先，您需要在主目录中放置一个名为 .forward 的文件。使用文本编辑器将以下内容写入文件（全部写在一行上）：

```
you@yoursite.com
"|/home/yourUserName/phpmailer/mailhandler.php"
```

这告诉服务器上的邮件系统，任何发往 you@yoursite.com 的电子邮件不仅需要发送到该地址，还必须发送到 /home/yourUserName/phpmailer/mailhandler.php 处的 PHP 脚本。

现在，在 PHP 脚本 mailhandler.php 中，您可以随意处理来邮。由于此 PHP 脚本旨在由邮件系统（而非 Web 服务器）自动运行，文件的第一行必须指向服务器上独立 PHP 程序的位置（通常是 /usr/bin/php）。以下是一个可能的脚本，用于检测来自特定地址的来邮，并作为回复发送第二封通知邮件：

```php
#!/usr/bin/php
<?php
// Read the email from the stdin file
$fp = fopen('php://stdin', 'r');
$email = fread ($fp, filesize('php://stdin'));
fclose($fp);

// Break the email up by linefeeds
$email = explode("\n", $email);

// Initialize vars
$numLines = count($email);
for ($i = 0; $i < $numLines; $i++) {
    // Watch out for the From header
    if (preg_match("/^From: (.*)/", $email[$i], $matches)) {
        $from = $matches[1];
        break;
    }
}

// Forward the message to the hotline email
if (strstr($from, 'vip@example.com')) {
    mail('you@yourdomain.com', 'Urgent Message!',
```



'Check your mail!');
}
?>
```

该代码从标准输入获取电子邮件。有关独立 PHP 脚本的此及其他问题的详细信息，请参阅 PHP 手册[6]。

PEAR::Mail_Mime 的邮件读取功能正在开发中（“work in progress”），但你可以通过使用其 Mail_mimeDecode 类来读取电子邮件，从而简化生活。

此示例与前一个脚本实现相同的目标，但代码更简单：

```
#!/usr/bin/php
<?php
// Include the PEAR mimeDecode class
require_once 'Mail/mimeDecode.php';

// Read the email from the stdin file
$fp = fopen('php://stdin', 'r');
$email = fread($fp, filesize('php://stdin'));
fclose($fp);

$decode = new Mail_mimeDecode($email, "\r\n");
$structure = $decode->decode();

// Forward the message to the hotline email
if (strstr($structure->headers['from'], 'vip@example.com')) {
    mail('you@yourdomain.com', 'Urgent Message!',
        'Check your mail!');
}
?>
```

变量 $structure 包含一个数据结构，其中电子邮件的所有关键元素都以命名形式提供。例如，$structure->headers['from'] 包含消息的“From”地址。

如果将原始电子邮件保存为文本文件，并使用 Mail_mimeDecode 将其解码，你就可以亲自查看这些值。以下是 $structure 的一个示例，它通过 print_r 函数传递，使用了另一个 PEAR 包—PEAR::mailparse[7] 中的一些测试数据：

- [6] http://www.php.net/features.commandline
- [7] http://pear.php.net/package-info.php?pacid=143

stdClass Object
(
    [headers] => Array
    (
        [return-path] =>
        [received] => Array
        (
            [0] => from secure.thebrainroom.com (raq338.uk
            [1] => from pb1.pair.com (pb1.pair.com [216.92
            [2] => (qmail 63230 invoked by uid 1010); 28 0
            [3] => (qmail 63215 invoked from network); 28
        )
        [x-authentication-warning] => zaneeb.brainnet.i: Host
        [mailing-list] => contact php-cvs-help@lists.php.net;
        [precedence] => bulk
        [list-help] =>
        [list-unsubscribe] =>
        [list-post] =>
        [delivered-to] => mailing list php-cvs@lists.php.net
        [reply-to] => marcus.boerger@post.rwth-aachen.de
        [message-id] => <5.1.0.14.2.20021028193555.01d47c20@ma
        [x-mailer] => QUALCOMM Windows Eudora Version 5.1
        [date] => Mon, 28 Oct 2002 19:36:10 +0100
        [to] => Melvyn Sopacua
        [from] => marcus.boerger@t-online.de (Marcus =?iso-885
        [cc] => php-cvs@lists.php.net
        [in-reply-to] => <5.1.0.14.2.20021028192151.039729e0@y
        [references] => <5.1.0.14.2.20021028190015.01d4d650@ma
        [mime-version] => 1.0
        [content-type] => multipart/alternative; boundary="=====
        [x-sender] => 520072483730-0001@t-dialin.net
        [x-spam-status] => No, tests=bogofilter, spamicity=0.0
        [subject] => Re: [PHP-CVS] cvs: php4 /ext/iconv/tests
        [x-trb-destbox] => user.wez.php.cvs (auth as wez) (wez
    )
    [ctype_primary] => multipart
    [ctype_secondary] => alternative
    [ctype_parameters] => Array
    (
        [boundary] => ===============_71195359==_.ALT
    )
    [parts] => Array
    (
        [0] => stdClass Object
        (
            [headers] => Array
            (
                [content-type] => text/plain; charset=
                [content-transfer-encoding] => quoted-
            )
            [ctype_primary] => text
            [ctype_secondary] => plain
            [ctype_parameters] => Array
            (
                [charset] => iso-8859-1
                [format] => flowed
            )
        )
    )
)
```

## 寻找问题的解决方案？

使用 PHP 处理传入电子邮件的价值可能并不明显。如果你曾经读过 SitePoint Tech Times[8]，你就会知道答案——无论你是否意识到！邮件列表的订阅和取消订阅是由 PHP 处理的。你也可以使用 PHP 构建垃圾邮件过滤器，允许通过浏览器和电子邮件更新论坛应用程序，并创建许多其他应用程序。

## 进一步阅读

- PHP 中的高级电子邮件：http://www.sitepoint.com/article/679
  本教程深入介绍了 PHP 的 mail 函数以及如何将其与 SMTP 标头配合使用。

- PHP 中的传入邮件：http://gvtulder.f2o.org/4_Incoming_Mail_and_PHP
  本文介绍了使用 sendmail、exim 和 qmail 的服务器使用 PHP 处理传入邮件的基本知识。

- 使用 PEAR 的 mimeDecode 模块：http://www.devarticles.com/art/1/618

- 使用 PHP3 读取 IMAP 邮件：http://www.phpbuilder.com/columns/musone19990207.php3

本文介绍了使用 PHP 的 IMAP 扩展读取电子邮件。

# 网页元素

尽管互联网作为信息传递手段还很年轻，但关于“设计是否已死”的问题已经引发激烈讨论。无论你在这场辩论中持何种立场，当我们使用 PHP 渲染 Web 内容时，就会清楚地发现相同的“元素”不断重现。

当你着手开发第一个 PHP 网站时，编写生成 HTML 表的脚本可能看起来不是问题。给它些时间！当你构建了几个网站，不得不回头修改过去的作品后，表格就不会那么美好了。最终，一提到维护，你很可能会倒吸一口凉气说“不要再来一个表格了！”，然后默默地对着键盘流泪。

别担心——帮助就在手边。并非所有 HTML 都相同，但 HTML 元素之间存在明显的共同点。这些共同点是 PHP 类的完美目标，PHP 类让你能够消除重复工作，专注于你喜欢的创意方面。

在本章中，我们将广泛使用 PEAR 的一些 HTML 包。相较于手动编写自己的 HTML 表格和表单，PEAR 具有出色的价值。

附录 D 解释了如何在服务器上安装 PEAR 并添加包。你需要参考该信息才能使用本章所需的 PEAR 类。

此处讨论的示例将使用以下数据库表格：

- 用户表：

```
CREATE TABLE user (
  user_id   INT(11)     NOT NULL AUTO_INCREMENT,
  login     VARCHAR(50) NOT NULL DEFAULT '',
  password  VARCHAR(50) NOT NULL DEFAULT '',
  email     VARCHAR(50) DEFAULT NULL,
  firstName VARCHAR(50) DEFAULT NULL,
  lastName  VARCHAR(50) DEFAULT NULL,
  signature TEXT        NOT NULL,
  PRIMARY KEY (user_id),
  UNIQUE KEY user_login (login)
)
```

- 存储图像的表：

```
CREATE TABLE image (
  image_id  INT(11)      NOT NULL AUTO_INCREMENT,
  name      VARCHAR(100) NOT NULL DEFAULT '',
  size      INT(11)      NOT NULL DEFAULT '0',
  type      VARCHAR(50)  NOT NULL DEFAULT '',
  contents  BLOB         NOT NULL,
  PRIMARY KEY (image_id)
)
```

- 最后，存储站点菜单的表：

```
CREATE TABLE menu (
  menu_id     INT(11)      NOT NULL auto_increment,
  parent_id   INT(11)      NOT NULL default '0',
  name        VARCHAR(255) NOT NULL default '',
  description TEXT         NOT NULL,
  location    VARCHAR(255) NOT NULL default '',
  PRIMARY KEY (menu_id),
  UNIQUE KEY location (location)
)
```

你会发现创建这些表格并包含示例数据的 MySQL 查询包含在代码存档的 sql/ 目录中。

## 如何在表格中显示数据？

HTML 表格是 PHP 与 MySQL 数据库中存储的数据交互的自然结果。在构建 PHP 应用程序时，拥有快速生成表格的工具是节省时间的必备手段。

使用我在第 3 章中构建的 MySQL 类生成表格的最简单方法可能如下所示：

```
$db = &new MySQL($host, $dbUser, $dbPass, $dbName);

$sql = "SELECT * FROM user ORDER BY lastName, firstName";

$result = $db->query($sql);

echo "<table align=\"center\">\n";
echo "<tr>\n<th>Login</th><th>Name</th><th>Email</th>\n</tr>";

while ($row = $result->fetch()) {
    echo "<tr>
    <td>" . $row['login'] . "</td>
    <td>" . $row['firstname'] . " ". $row['lastname'] . "</td>
    <td>" . $row['email'] . "</td>
    </tr>\n";
}
echo "</table>";
```

这种方法对于简单的东西来说还可以，但随着表格变得更加复杂，它可能会成为负担。

## PEAR 风格的表格

构建更复杂表格的任务由 PEAR::HTML_Table[1] 变得更容易。HTML_Table 由 Bertrand Mansion 和 Adam Daniel 开发，它为表格构建提供了一个便捷的 API，不需要你输入任何 HTML 标签。对于复杂表格，这可以节省大量时间，并减少在 HTML 本身中出错的机会。此处使用的版本是 1.5。

[1] http://pear.php.net/HTML_Table





让我们看看如何通过一个简单示例来实现。我们将重复上面的用户列表，并添加一些吸引人的视觉效果。首先，在引入 HTML_Table 类后，我们将构建一个 switch 语句，以便可以按特定列对结果进行排序：

```
File: 2.php (excerpt)

// Include the PEAR::HTML_Table class
require_once "HTML/Table.php";

$db = &new MySQL($dbHost, $dbUser, $dbPass, $dbName);

// Basic SQL statement
$sql = "SELECT * FROM user";

// A switch to allow sorting by column
switch (@$_GET['sort']) {
case 'login':
$sql .= " ORDER BY login ASC";
break;
case 'email':
$sql .= " ORDER BY email ASC";
break;
default:
$sql .= " ORDER BY lastName, firstName";
break;
}
```

到目前为止，一切顺利。

要使用 HTML_Table，您需要熟悉 PHP 的数组；HTML_Table 接受的许多参数都是以数组形式传递的。HTML 属性通常作为关联（命名）数组传递，而行数据本身则作为索引（编号）数组传递：

```
File: 2.php (excerpt)

// Overall style for the table
$tableStyle = array(
'width' => '650',
'style' => 'border: 1.75px dotted #800080;'
);

// Create the table, passing the style
$table = new HTML_Table($tableStyle);

// Define a style for the caption of the table
$captionStyle = array(
'style' => 'font-family: Verdana; font-weight: bold;
           font-size: 14.75px; color: navy;'
);

// Add the caption, passing the text to display and the style
$table->setCaption('User List', $captionStyle);

// Define an array of column header data
$columnHeaders = array(
    '<a href="' . $_SERVER['PHP_SELF'] . '?sort=login">Login</a>',
    '<a href="' . $_SERVER['PHP_SELF'] . '?sort=name">Name</a>',
    '<a href="' . $_SERVER['PHP_SELF'] . '?sort=email">Email</a>'
);

// Add the header row, passing header text and using a TH tag
$table->addRow($columnHeaders, '', 'TH');
```

在以下 while 循环中，我们获取每一行，并从从数据库中检索到的关联数组构建一个索引数组。然后，我们使用 addRow 方法将索引数组添加到表中：

```
$result = $db->query($sql);

// A loop for each row of the result set
while ($row = $result->fetch()) {
    // Place row data in indexed array
    $rowData = array(
        $row['login'],
        $row['firstName'] . ' ' . $row['lastName'],
        $row['email']
    );

    // Add the row, passing the data
    $table->addRow($rowData);
}
```

让我们通过应用一些 HTML 属性来完善表格，使其更具吸引力。首先，我们将使用 setAllAttributes 为每个单元格应用样式。然后，我们将使用 setRowAttributes 为第一行（编号为 0）覆盖此样式，使该文本稍大一些。最后，我们将使用 altRowAttributes 为每一行应用交替样式，从表格中的第一行实际数据开始：

```
// Set the style for each cell of the row
$cellStyle = 'style="font-family: verdana; font-size: 11;"';

// Apply the style
$table->setAllAttributes($cellStyle);

// Define the style for the column headings
$headerStyle = 'style="background-color: #ffffff;
font-family: verdana;
font-weight: bold;
font-size: 12;"';

// Set the row attributes for the header row
$table->setRowAttributes(0, $headerStyle);

// Set alternating row colors
$table->altRowAttributes(
    1,
    'style="background-color: #d3d3d3"',
    'style="background-color: #ffffff"',
    TRUE
);

// Display the table
echo $table->toHTML();
```

最终结果是一个整洁的表格，我们可以按列对其进行排序，如图 9.1 所示。

## 图 9.1. 由 PEAR::HTML_Table 生成的表格

| 登录名 | 姓名 | 电子邮件 |
|---|---|---|
| hfuecks | Harry Fuecks | hfuecks@phppatterns.com |
| Testing | Harry Fuecks | hfuecks@hotmail.com |
| bjones | Bruce Jones | bjones@hotmail.com |
| hjones | Hale Jones | hjones@php.net |
| dmoore | Demi Moore | dmoore@hotmail.com |
| hmoore | Hale Moore | hmoore@php.net |
| mmoore | Madeline Moore | mmoore@php.net |
| dschwarzenegger | Demi Schwarzenegger | dschwarzenegger@hotmail.com |
| jschwarzenegger | John Schwarzenegger | jschwarzenegger@hotmail.com |
| mschwarzenegger | Madeline Schwarzenegger | mschwarzenegger@yahoo.co.uk |
| cstowe | Catherine Stowe | cstowe@yahoo.co.uk |
| hstowe | Hale Stowe | hstowe@yahoo.co.uk |
| btravolta | Bruce Travolta | btravolta@mysql.com |
| mtravolta | Madeline Travolta | mtravolta@mysql.com |
| rtravolta | Robin Travolta | rtravolta@hotmail.com |
| dwilliams | Demi Williams | dwilliams@hotmail.com |
| hwilliams | Hale Williams | hwilliams@mysql.com |
| awillis | Arnold Willis | awillis@hotmail.com |
| jwillis | John Willis | jwillis@mysql.com |
| rwillis | Robin Willis | rwillis@mysql.com |

你可能会对生成这个表格所需的代码量感到有点失望。不过请记住，使用 HTML_Table 构建的表格比我们一开始使用的简单示例包含了更多格式。在实际应用中，将网站的 CSS 属性定义在专用样式表中，然后使用 HTML_Table API 仅设置 class 属性，也是更合理的做法。

## 如何构建结果分页器？

结果分页器是一个导航元素，允许网站访问者以“页”为单位浏览从数据库中提取的数据。其目的是避免使用全表扫描（SELECT * FROM table），如果处理大量数据，这会严重拖慢服务器，并以用户友好的“块”而非单个巨型列表的形式提供结果。如果你曾使用过像 Google™ 这样的搜索器（可以安全地假设你使用过），那么你已经使用过结果分页器来浏览搜索结果。

MySQL 使实现结果分页器变得非常简单；我们只需在查询中使用 LIMIT 子句。以下是一个简单示例：

```
SELECT * FROM user LIMIT 5, 10
```

上述查询将从第 5 行开始，总共选取 10 行。现在你只需要一些 PHP 代码来动态构建此子句，传递查询将开始的行号以及它将选取的行数。

![](img/5b6cdf7cf4cf53e30b19e047895dc464_280_0.png)

## 何时实现结果分页器

作为一般规则，如果你有类似 SELECT * FROM user 的全表扫描查询，应该考虑实现结果分页器。

在开发应用程序时，你可能不会注意到问题，但一旦表中包含成千上万条记录且网站流量很高，MySQL 将难以应对所有这些查询。此外，取决于你如何编写 PHP，随着表中行数的增加，脚本执行时间可能会越来越长。

诀窍是编写生成 LIMIT 子句中那两个神奇数字的 PHP 代码。通常，第一步是让 MySQL 告诉你“未分页”结果集中有多少行。这通常需要一个 COUNT 查询：

```
SELECT COUNT(*) AS num_rows FROM user
```

要确定总页数，只需将结果集中的行数除以每页显示的行数即可。然后，通过将页码乘以每页显示的行数，即可确定每页将从哪一行开始。

用一些代码来看会更容易。首先，让我们组装一个简单的分页类来封装这些计算：

```
File: Database/SimplePager.php (in SPLIB) (excerpt)

/**
 * SimplePager class
 * Used to help calculate the number of pages in a database result
 * set
 * @access public
 * @package SPLIB
*/
class SimplePager {
/**
 * Total number of pages
 * @access private
 * @var int
*/
var $totalPages;

/**
 * The row MySQL should start its select with
 * @access private
 * @var int
 */
var $startRow;

/**
 * SimplePager Constructor
 * @param int number of rows per page
 * @param int total number of rows available
 * @param int current page being viewed
 * @access public
 */
function SimplePager($rowsPerPage, $numRows, $currentPage = 1)
{
    // Calculate the total number of pages
    $this->totalPages = ceil($numRows / $rowsPerPage);

    // Check that a valid page has been provided
    if ($currentPage < 1) {
        $currentPage = 1;
    } else if ($currentPage > $this->totalPages) {
        $currentPage = $this->totalPages;
    }

    // Calculate the row to start the select with
    $this->startRow = (($currentPage - 1) * $rowsPerPage);
}

/**
 * Returns the total number of pages available
 * @return int
 * @access public
 */
function getTotalPages()
{
    return $this->totalPages;
}

/**
 * Returns the row to start the select with
 * @return int
 * @access public
```





/*
function getStartRow()
{
    return $this->startRow;
}
}
*/

我们只需在实例化此类时，将相关行信息以及当前正在查看的页码传递给它。它随后会告诉我们总页数以及应从哪个行号开始执行select查询。

下面是它的实际应用：

```
File: 3.php (excerpt)
// Instantiate MySQL connection
$db = &new MySQL($host, $dbUser, $dbPass, $dbName);

// Find out how many rows are available
$sql = "SELECT COUNT(*) AS num_rows FROM user";
$result = $db->query($sql);
$row = $result->fetch();

// Define the number of rows per page
$rowsPerPage = 10;

// Set a default page number
if (!isset($_GET['page'])) {
    $_GET['page'] = 1;
}

// Instantiate the pager
$pager = new SimplePager($rowsPerPage, $row['num_rows'],
    $_GET['page']);

// Build a table for the pager
echo "<table align=\"center\"/>\n<tr>\n";

// Build the HTML for the pager
for ($i = 1; $i <= $pager->getTotalPages(); $i++) {
    echo "<td><a href=\"" . $_SERVER['PHP_SELF'] . "?page=$i\">";
    if ($i == $_GET['page']) {
        echo "<strong>$i</strong>";
    } else {
        echo $i;
    }
    echo "</a></td>\n";
}
echo "</tr>\n</table>\n";
```

请注意，我们在用于构建页间导航链接的for循环中使用了getTotalPages方法。

在页面准备就绪且HTML构建完成后，我们现在可以利用getStartRow方法来创建结果表格：

```
File: 3.php (excerpt)

// Now construct the "real" SQL statement
$sql = "SELECT * FROM user
LIMIT " . $Pager->getStartRow() . ", " . $rowsPerPage;

// Fetch and display the results
$result = $db->query($sql);

echo "<table align=\"center\">\n";
echo "<tr>\n<th>Login</th><th>Name</th><th>Email</th>\n</tr>";

while ($row = $result->fetch()) {
    echo "<tr>\n";
    echo "<td>" . $row['login'] . "</td>";
    echo "<td>" . $row['firstName'] . " " . $row['lastName'] . "</td>";
    echo "<td>" . $row['email'] . "</td>\n";
    echo "</tr>\n";
}
echo "</table>";
```

我们现在可以每次显示十行来分页浏览用户表格。这是一个不错的开端，但代码有些凌乱。它还缺少一些功能，例如仅需点击“下一页”或“上一页”即可前进或后退一页的能力。并且一次显示的页数没有限制（对于大型表格，可能会有数百页，这会导致网页显得不美观）。

## 滑动页码

PEAR提供了另一个名为PEAR::Pager_Sliding[2]的实用包。由Lorenzo Alberton编写，Pager_Sliding将计算和链接构建结合在一个易于使用的类中。此处使用的版本为1.4。

- [2] http://pear.php.net/Pager_Sliding

该类并未提供我们想要的一切，因此我们首先需要一个扩展Pager_Sliding类以提供额外信息的类。顺便提一下，这使用了**继承**（有关更多信息，请参见第2章）。

```
/**
 * DB_Pager_Sliding - extends PEAR::Pager_Sliding
 * Provides an API to help build query result pagers
 * @access public
 * @package SPLIB
 */
class DB_Pager_Sliding extends Pager_Sliding {
    /**
     * DB_Pager_Sliding constructor
     * @param array params for parent
     * @access public
     */
    function DB_Pager_Sliding($params)
    {
        parent::Pager_Sliding($params);
    }

    /**
     * Returns the number of rows per page
     * @access public
     * @return int
     */
    function getRowsPerPage()
    {
        return $this->_perPage;
    }

    /**
     * The row number to start a SELECT from
     * @access public
     * @return int
     */
    function getStartRow()
    {
        if ($this->_currentPage == 0) {
            return $this->_perPage;
        } else {
            return ($this->_currentPage - 1) * $this->_perPage;
        }
    }
}
```

这个扩展类提供了构建查询所需的信息。现在，让我们将分页器添加到在“如何在表格中显示数据？”中构建的用户表格：

```
// Include the PEAR::HTML_Pager_Sliding class
require_once 'HTML/Sliding.php';

// Include the extended class
require_once 'DB_Pager_Sliding.php';

// Instantiate MySQL
$db = &new MySQL($host, $dbUser, $dbPass, $dbName);

$sql = "SELECT COUNT(*) AS num_rows FROM user";
$result = $db->query($sql);
$row = $result->fetch();

// Define pager settings
$pager_params = array(
  // The total number of rows
  'totalItems' => $row['num_rows'],
  // Rows per page
  'perPage' => 10,
  // The size of the sliding Window +/-.
  'delta' => 2,
  // Separator and spacing between links
  'separator' => ' . . ',
  'spacesBeforeSeparator' => 2,
  'spacesAfterSeparator' => 2,
  // The $_GET variable name
  'urlVar' => 'page',
  // Browser status bar text
  'altPrev' => 'Previous Page',
  'altNext' => 'Next Page',
  'altPage' => 'Page: ',
  // CSS Class names
  'curPageLinkClassName' => 'currentPage',
  'linkClass' => 'pageLink',
);

// Instantiate the pager
$pager = &new DB_Pager_Sliding($pager_params);

// Fetch the HTML links
$links = $pager->getLinks();
```

现在我们可以修改查询，以使用分页器生成的LIMIT子句：

```
// Basic SQL statement
$sql = "SELECT * FROM user";

// A switch to allow sorting by column
switch (@$_GET['sort']) {
    case 'login':
    $sql .= " ORDER BY login ASC";
    break;
    case 'email':
    $sql .= " ORDER BY email ASC";
    break;
    default:
    $sql .= " ORDER BY lastName, firstName ASC";
    break;
}

// Add the LIMIT clause
$sql .= " LIMIT " . $pager->getStartRow() . ", " .
    $pager->getRowsPerPage();
```

现在剩下的就是定义在分页器设置中指定的CSS类currentPage和pageLink，并在表格下方显示链接：

```
<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Transitional//EN"
"http://www.w3.org/TR/xhtml1/DTD/xhtml1-transitional.dtd">
<html xmlns="http://www.w3.org/1999/xhtml">
<head>
<title> Users </title>
<meta http-equiv="Content-Type"
content="text/html; charset=iso-8859-1" />
<style type="text/css">
.currentPage
{
 font-family: verdana;
 font-size: 10px;
 font-weight: bold;
 color: red;
}
.pageLink
{
 font-family: verdana;
 font-size: 10px;
 color: red;
}
</style>
</head>
<body>
<?php
// Display the table
echo $table->toHTML();
?>
<div align="center">
<?php
// Display the paging links
echo $links['all'];
?>
</div>
</body>
</html>
```

请注意，此处未复现构建表格的代码，但请放心，您将在与此解决方案关联的代码存档中找到它。

Pager_Sliding类在数组中提供已构建的链接。我们可以单独访问每个链接（如果想更精确地控制分页器在页面上的位置，这很有用），也可以像这里所示使用$links['all']显示完整的分页器。

完成的表格及其后的分页链接如图9.2所示。

## 图9.2. 分页显示所有用户...

| 登录名 | 姓名 | 电子邮件 |
|---|---|---|
| hwilliams | Hale Williams | hwilliams@mysql.com |
| jschwarzenegger | John Schwarzenegger | jschwarzenegger@hotmail.com |
| jwillis | John Willis | jwillis@mysql.com |
| mmoore | Madeline Moore | mmoore@php.net |
| mschwarzenegger | Madeline Schwarzenegger | mschwarzenegger@yahoo.co.uk |
| mtravolta | Madeline Travolta | mtravolta@mysql.com |
| rtravolta | Robin Travolta | rtravolta@hotmail.com |
| rwillis | Robin Willis | rwillis@mysql.com |

Pager_Sliding类的妙处在于，它显示的页码范围会随访客当前所在页面而变化。随着表格的增长，导航依然简便。在处理大型结果集时这一点至关重要；例如，如果查询返回超过十页的结果，没有“滑动分页器”，你的网页上将不得不显示一长串页码，这既难看又难以导航。Pager_Sliding类可帮助你实现类似于Google[3]使用的分页器，搜索通常会返回数百页的结果。

## 如何在PHP中处理HTML表单？

> “能力越大，责任越大。”
> —蜘蛛侠的本叔

与链接和URL相比，HTML表单提供了一种功能强大得多的机制，用于接收网站访客的信息。表单允许你开发复杂的界面，例如，使用户能够从动态生成的列表中选择值、输入大段文本，甚至上传文件。表单使从简单的留言本到复杂的用户注册和身份验证系统等一切成为可能。但功能增强也带来了更广泛的问题。你如何验证表单？如果表单填写不正确，应当如何处理？如何使用数据库中的数据填充表单？在处理表单时，你将面临这些挑战中的几个；还有更多。

### HTTP请求方法

因特网使用的HTTP协议（通常用于获取网页）定义了许多“方法”，浏览器可使用这些方法向Web服务器发送请求和数据。在可用方法中，最重要的是GET方法和POST方法。

- GET是因特网的“默认”方法，每当你使用浏览器请求页面时都会使用。请求中的所有数据必须编码到URL中。
- POST最常用于提交表单。它允许随请求一起发送额外的表单数据。

HTML允许你为每个表单标签指定要使用的方法。虽然GET是默认方法，但最常用的是POST，因为它避免了将提交的数据添加到URL中，从而避免URL过于杂乱。

- [3] http://www.google.com/





## 处理表单的准则

- [ ] 在 HTML 中声明表单时使用 POST 方法。这样可以防止表单值出现在 URL 中，并允许通过表单提交更多数据。

- [ ] 在用 PHP 值填充表单字段时，使用 PHP 的 htmlspecialchars 函数，以避免生成格式错误的 HTML，如第 5 章所述。

- [ ] 不要完全依赖 JavaScript 验证。它可以改善用户体验，但单独使用 JavaScript 验证很容易被用户绕过。

- [ ] 如果使用普通 HTTP，表单数据将以“明文”形式从浏览器通过 Internet 发送到服务器。这意味着有人可能使用数据包嗅探器拦截它。当发送诸如财务细节等机密信息时，请使用诸如 SSL 之类的加密技术。

## 与 QuickForm 一起使用表单

我暂且假设你愿意使用最基本的表单。在这里，我们将专注于另一个 PEAR 包——PEAR::HTML_QuickForm[4]。QuickForm 由 Bertrand Mansion 和 Adam Daniel 开发，它使从 PHP 渲染简单的 HTML 表单变得容易……但这还不是全部！QuickForm 还提供了更多功能，帮助解决一系列其他问题，例如生成日历表单元素，以及使用 PHP 和 JavaScript 进行验证。它还会自动处理与魔术引号相关的问题，因此如果你使用 QuickForm，就不需要担心魔术引号是开启还是关闭。这些示例中使用的版本是 3.1。

首先，一个简单的例子：

```php
<?php
// Include the QuickForm class
require_once 'HTML/QuickForm.php';

// Instantiate the QuickForm class
$form = new HTML_QuickForm('quickForm1', 'POST');

// Add a text input field called firstName,
```

[4] http://pear.php.net/HTML_QuickForm

```php
// labelled "Enter your name"
$form->addElement('text', 'firstName', 'Enter your name');

// Add a submit button called submit with "Send" as the text
// for the button
$form->addElement('submit', 'submit', 'Send');

// If the form is submitted...
if (isset($_POST['submit'])) {
    // Display the submitted value "firstName"
    echo 'Hello ' . $form->getSubmitValue('firstName');
} else { // If not submitted, display the form
    $form->display();
}
?>
```

这将显示一个简单的表单，用户可以在其中输入他们的姓名。

以下是它生成的格式良好的 HTML：

```html
<table border="0">
    <form action="/sitepoint/WebPageElements/3.php" method="POST"
    name="quickForm1" target="_self">
    <tr>
        <td align="right" valign="top"><b>Enter your name</b></td>
        <td nowrap="nowrap" valign="top" align="left"><input
        name="firstName" type="text" /></td>
    </tr>
    <tr>
        <td align="right" valign="top"><b></b></td>
        <td nowrap="nowrap" valign="top" align="left"><input
        name="submit" value="Send" type="submit" /></td>
    </tr>
    </form>
</table>
```

在此示例中，我们使用了原生的 $_POST 变量来确定表单是否已提交。但我们不必这样做。如果我们应用 QuickForm 的验证功能，可以使用其 validate 方法来检查表单是否已提交，并一次性确保其已正确验证。

以下是相同的表单；这次，它使用 PHP 中的 JavaScript 来检查是否输入了姓名，如果 JavaScript 被禁用，则回退到 PHP 验证：

```php
<?php
// Include the QuickForm class
require_once 'HTML/QuickForm.php';

// Instantiate the QuickForm class
$form = new HTML_QuickForm('quickForm2', 'POST');

// Add a text input field called firstName, labelled
// "Enter your name"
$form->addElement('text', 'firstName', 'Enter your name');

// Rule to validate with JavaScript and PHP
$form->addRule('firstName', 'Please enter your name', 'required',
FALSE, 'client');

// Add a submit button called submit with "Send" as the text
// for the button
$form->addElement('submit', 'submit', 'Send');

// If the form is submitted...
if ($form->validate()) {
  // Display the submitted value "firstName"
  echo 'Hello ' . $form->getSubmitValue('firstName');
} else {
  // If not submitted, display the form
  $form->display();
}
?>
```

addRule 方法提供了向表单添加验证规则的手段。包含 client 参数告诉 QuickForm 在客户端使用 JavaScript 进行表单验证。请注意，当你使用客户端验证时，QuickForm 将继续为禁用了 JavaScript 的浏览器在服务器端验证表单。

我们可以使用 validate 方法来检查表单是否已提交。请注意，如果表单在 PHP 中验证失败，它将再次显示给用户，并伴随一条告诉他们哪里出错的消息（参见图 9.3）。

## 图 9.3. 刚才，我叫什么名字来着？

![](img/5b6cdf7cf4cf53e30b19e047895dc464_292_0.png)

## QuickForm 验证规则类型

在上面的示例中，我们使用了 required 规则。QuickForm 附带了一些针对特定情况的内置规则，以及一些更通用的规则。支持的规则如下：

| 规则 | 描述 |
| :--- | :--- |
| required | 表单字段必须提供一个值 |
| maxlength | 字段值的字符长度受到最大长度限制 |
| minlength | 字段值必须包含最少数量的字符 |
| rangelength | 字段值必须正好是指定的长度 |
| email | 字段值必须是一个有效的电子邮件地址 |
| emailorblank | 字段值必须是一个有效的电子邮件地址，或者必须为空 |
| lettersonly | 字段值只能包含字母 ’a’ 到 ’z’（不区分大小写） |
| alphanumeric | 字段只能包含字母 ’a’ 到 ’z’（不区分大小写）或数字 |

- **数值型**：字段值只能包含数字
- **无标点**：字段中不得包含任何标点字符
- **非零**：字段值必须是 0 以外的数字
- **已上传文件**：字段必须包含一个上传的文件，由 PHP 的 is_uploaded_file 函数[5]验证
- **最大文件大小**：字段中包含的上传文件的大小受到最大大小限制
- **MIME 类型**：字段中包含的上传文件必须是特定的 MIME 类型¹
- **文件名**：字段中包含的上传文件的文件名必须匹配一个正则表达式
- **函数**：当将字段的值传递给指定函数时，该函数必须返回 TRUE
- **正则表达式**：字段的值必须与指定的正则表达式匹配

你可以使用 addRule 方法将上述一条或多条规则应用于任何 QuickForm 字段：

```
addRule(element, message, type[, format[, validation[, reset[, force]]]])
```

对于上述参数，

- **元素**：是你使用 addElement 方法为元素分配的名称
- **消息**：如果用户违反此验证规则，则向用户显示的文本
- **类型**：验证规则类型（如上所列）

[5] http://www.php.net/is-uploaded-file
参见 http://www.hiveemail.com/mime.types.php 获取 MIME 类型列表。

- **格式**：规则的参数，例如最小长度或与 regex 规则类型一起使用的正则表达式
- **验证**：可以是 `server` 或 `client`；如果使用 `client`，将同时执行 JavaScript 和 PHP 验证
- **重置**：如果为 `TRUE`，则在用户出错重新显示表单时清空关联的表单字段
- **强制**：即使表单名称不存在，也会使 QuickForm 应用验证规则，这在你“即时”生成表单时很有用

如果你查看 QuickForm 的代码，会发现该类的每个方法都有文档。撰写本文时，文档尚未在 PEAR 网站上发布，但很快应该可用。

## 立即注册

现在你更了解 QuickForm 了，是时候用它做一些更有趣的事情了。让我们构建一个注册表单，向 users 表中添加新帐户。这将意味着再次启用第 3 章中的 MySQL 类。开始吧...

```php
<?php
// Include the MySQL class
require_once 'MySQL.php';

// Include the QuickForm class
require_once 'HTML/QuickForm.php';

$host = 'localhost'; // Hostname of MySQL server
$dbUser = 'harryf'; // Username for MySQL
$dbPass = 'secret'; // Password for user
$dbName = 'sitepoint'; // Database name
```

一开始，我们已包含所需的类，并设置了数据库的变量。接下来，我们将定义 QuickForm 用于对其从表单接收的值执行操作的三个函数：



```
// A function for comparing password
function cmpPass($element, $confirmPass)
{
    global $form;
    $password = $form->getElementValue('password');
    return $password == $confirmPass;
}

// A function to apply mysqli_real_escape_string
function escapeValue($value)
{
    return mysqli_real_escape_string($value);
}

// A function to encrypt the password
function encryptValue($value)
{
    return md5($value);
}
```

cmpPass 函数将用于验证表单的“确认密码”字段，该字段必须与“密码”字段匹配。请注意，该函数将 $form 声明为全局变量，以便在函数内部访问。一般来说，使用 global 关键字不是个好主意；在复杂的应用程序中，这可能会导致与同名变量发生冲突。尽管在当前版本的 QuickForm 中我们别无选择，但希望未来会有所改变。

escapeValue 和 encryptValue 函数用于在提交后对值进行“过滤”。如您在第 3 章中研究 SQL 注入攻击时所了解的，在将数据插入数据库之前对所有传入数据进行转义至关重要，因此有了 escapeValue 函数。而 encryptValue 函数呢？我们将以加密形式在数据库中存储密码，此函数将执行必要的加密操作。有关更多信息，请参见第 II 卷，第 1 章，其中我们构建了一个包含此功能的用户身份验证系统。

接下来，我们实例化该类，创建所有表单字段，并为它们应用规则：

```
// Instantiate the QuickForm class
$form = new HTML_QuickForm('regForm', 'POST');
```

```
// Register the compare function
$form->registerRule('compare', 'function', 'cmpPass');

// The login field
$form->addElement('text', 'login', 'Desired Username');
$form->addRule('login', 'Please provide a username', 'required',
    FALSE, 'client');
$form->addRule('login', 'Username must be at least 6 characters',
    'minlength', 6, 'client');
$form->addRule('login',
    'Username cannot be more than 50 characters', 'maxlength', 50,
    'client');
$form->addRule('login',
    'Username can only contain letters and numbers',
    'alphanumeric', NULL, 'client');

// The password field
$form->addElement('password', 'password', 'Password');
$form->addRule('password', 'Please provide a password',
    'required', FALSE, 'client');
$form->addRule('password',
    'Password must be at least 6 characters', 'minlength', 6,
    'client');
$form->addRule('password',
    'Password cannot be more than 12 characters', 'maxlength', 50,
    'client');
$form->addRule('password',
    'Password can only contain letters and numbers',
    'alphanumeric', NULL, 'client');

// The field for confirming the password
$form->addElement('password', 'confirmPass', 'Confirm Password');
$form->addRule('confirmPass', 'Please confirm password',
    'required', FALSE, 'client');
$form->addRule('confirmPass', 'Passwords must match',
    'compare', 'function');

// The email field
$form->addElement('text', 'email', 'Email Address');
$form->addRule('email', 'Please enter an email address',
    'required', FALSE, 'client');
$form->addRule('email', 'Please enter a valid email address',
    'email', FALSE, 'client');
$form->addRule('email', 'Email cannot be more than 50 characters',
    'maxlength', 50, 'client');
```

```
// The first name field
$form->addElement('text', 'firstName', 'First Name');
$form->addRule('firstName', 'Please enter your first name',
'required', FALSE, 'client');
$form->addRule('firstName',
'First name cannot be more than 50 characters', 'maxlength',
50, 'client');

// The last name field
$form->addElement('text', 'lastName', 'Last Name');
$form->addRule('lastName', 'Please enter your last name',
'required', FALSE, 'client');
$form->addRule('lastName',
'Last name cannot be more than 50 characters', 'maxlength',
50, 'client');

// The signature field
$form->addElement('textarea', 'signature', 'Signature');

// Add a submit button called submit and "Send" as the text for
// the button
$form->addElement('submit', 'submit', 'Register');
```

请注意，为字段添加多个规则完全没问题，因为可能需要满足多个要求。

现在，我们使用 if-else 条件来检查表单是否已通过验证：

```
// If the form is submitted...
if ($form->validate()) {
```

如果表单已通过验证，我们使用 applyFilter 方法告诉 QuickForm 将上面定义的 escapeValue 过滤函数应用于表单的每个字段：

```
// Apply the escape filter to all fields
$form->applyFilter('__ALL__', 'escapeValue');
```

我们还应用加密密码的过滤器：

```
// Apply the encryption filter to the password
$form->applyFilter('password', 'encryptValue');
```

现在剩下的就是执行查询，用户即可注册：

```
// Instantiate the MySQL class
$db = &new MySQL($host, $dbUser, $dbPass, $dbName);

// Construct a query using the submitted values
$sql = "INSERT INTO user SET
	login='' . $form->getSubmitValue('login') . '',
	password='' . $form->getSubmitValue('password') . '',
	email='' . $form->getSubmitValue('email') . '',
	firstName='' . $form->getSubmitValue('firstName') . '',
	lastName='' . $form->getSubmitValue('lastName') . '',
	signature='' . $form->getSubmitValue('signature') . ''";

// Perform the query
$Result = $db->query($sql);

// If all went well, say thanks
if (!$result->isError()) {
	echo 'Thank you. Registration completed';
}
} else {
	// If not submitted, display the form
	$form->display();
}
?>
```

如您从图 9.4 的结果中所见，QuickForm 构建功能强大的表单变得非常简单。上次您用 100 多行代码构建这样一个注册表单（编写 HTML、定义完整验证（甚至在 JavaScript 中）、并在用户出错时处理数据重新显示）是什么时候？

## 图 9.4. 使用 QuickForm 注册

![](img/5b6cdf7cf4cf53e30b19e047895dc464_299_0.png)

使用 QuickForm 还可以做更多事情，包括配置用于显示表单的 HTML 格式、处理其他类型的表单字段（下拉菜单、复选框等），甚至对字段进行分组（例如电话号码，号码的每个部分都是一个单独的文本字段）。我们将在下一个解决方案中介绍文件上传的处理。有关修改 QuickForm 外观的示例，请参见第 II 卷，第 1 章中开发的“注册”表单。

## 如何使用 PHP 上传文件？

允许网站成员向网站上传文件（以便其他成员下载，例如）通常非常方便。使用 PHP 时，解决方案和往常一样非常简单。请注意，完整文档可在 PHP 手册[7]中查看。

### 设置最大上传大小

![](img/5b6cdf7cf4cf53e30b19e047895dc464_300_0.png)

PHP 在 php.ini 中有两个设置用于限制文件上传的最大大小。第一个是 post_max_size，它控制可以通过 POST 方法发送到脚本的数据最大量。默认情况下，此设置为八兆字节。第二个设置是 upload_max_filesize，它专门限制上传文件的大小，默认情况下设置为两兆字节。如果您预计会有大文件上传，可能需要增加这两个设置。

有关更多详细信息，请参见附录 A。

如果您熟悉 HTML 表单，您就会知道在表单中添加文件上传字段是一件简单的事情。您只需向表单标签添加 enctype="multipart/form-data" 属性，并向表单添加必要的 input 标签：

```
<input type="file" name="fieldname" />
```

当文件上传提交到 PHP 脚本时，文件会被安全地存储在网站的临时目录中（Linux 系统上通常是 /tmp），并获得一个唯一的临时文件名，以便 PHP 脚本可以使用它。关于文件的信息包含在 $_FILES 数组中，并与对应表单字段名的键一起存储（即 $_FILES['fieldname']。该信息作为另一个数组存储，包含五个值：

```
$_FILES['fieldname']['name']
```

文件的原始名称





- `$_FILES['fieldname']['type']`: 文件的 MIME 类型[8]
- `$_FILES['fieldname']['tmp_name']`: 文件上传时 PHP 创建的临时名称和位置
- `$_FILES['fieldname']['error']`: 如果一切正常则为 0（错误代码请参见 PHP 手册[9]）
- `$_FILES['fieldname']['size']`: 文件的大小（字节）

下面是 PHP 的 print_r 函数生成的文件上传信息数组示例：

```
Array
(
    [name] => php_logo.gif
    [type] => image/gif
    [tmp_name] => /tmp/php1B1B.tmp
    [error] => 0
    [size] => 3872
)
```

掌握这些知识后，让我们来看一个简单的脚本，它接受 GIF 文件上传并将其复制到当前目录的 files 子目录中：

```
<?php
// Include Magic Quotes filter
require_once 'MagicQuotes/strip_quotes.php';

// If the form has been submitted...
if (isset($_POST['submit'])) {

    // If the file is a GIF image...
    if ($_FILES['image']['type'] == 'image/gif') {

        // Copy the file from temporary storage to final destination
        copy($_FILES['image']['tmp_name'], "./files/" . $_FILES['image']['name'])
or die("Could not copy");

// Display some information about the file
echo "File Upload Complete<br />\n";
echo "Name: " . $_FILES['image']['name'] . "<br />\n";
echo "Size: " . $_FILES['image']['size'] . "<br />\n";
echo "Type: " . $_FILES['image']['type'] . "<br />\n";
echo "<img src=\"\\files/" . $_FILES['image']['name'] . "\\" />";
}

// ... otherwise display the form
} else {
?>
<form method="POST"
    action="?<?php echo $_SERVER['PHP_SELF']; ?>"
    enctype="multipart/form-data">
Upload a GIF image: <input type="file" name="image" />
<input type="submit" name="submit" value="Submit" />
</form>
<?php
}
?>
```

搞定，即时文件上传！请参见图 9.5 查看结果。

### 图 9.5. PHP 徽标上传成功

![](img/5b6cdf7cf4cf53e30b19e047895dc464_303_0.png)

### 确保是上传的文件

也许你有一个更复杂的脚本，在其中你将临时文件名传递给了另一个 PHP 变量，进行了各种操作，然后忘了代码里留了个漏洞——这个漏洞允许用户用另一个文件名修改 PHP 变量的内容！在对上传的文件做任何操作（例如将其复制到其他人可以看到的公共目录）之前，值得使用 PHP 函数 `is_uploaded_file` 双重检查上传的文件确实是正确的文件。过去，有人诱使 PHP 脚本将包含密码的文件（而不是实际上传的图像）复制到公共目录。与其后悔，不如谨慎。

### 使用 QuickForm 进行文件上传

让我们再次启用我们的老朋友 QuickForm，并学习如何将文件存储在 MySQL 中。

表单的构建与“如何在 PHP 中处理 HTML 表单？”中的示例非常相似：

```
<?php
// Include the MySQL class
require_once 'Database/MySQL.php';

// Include the QuickForm class
require_once 'HTML/QuickForm.php';

$host = 'localhost'; // Hostname of MySQL server
$dbUser = 'harryf'; // Username for MySQL
$dbPass = 'secret'; // Password for user
$dbName = 'sitepoint'; // Database name

// A function to apply mysql_real_escape_string
function escapeValue($value)
{
    return mysql_real_escape_string($value);
}

// Instantiate QuickForm
$form = new HTML_QuickForm('imageUpload', 'POST');

// The file upload field
$form->addElement('file', 'image', 'Select Image:');
$form->addRule('image', 'The maximum file size is 56KB',
    'maxfilesize', 57344);
$form->addRule('image', 'The file must be an image', 'mimetype',
    array('image/gif', 'image/jpeg', 'image/pjpeg',
    'image/png'));
$form->addRule('image', 'No file selected.', 'uploadedfile', NULL,
    'client');

// The submit button
$form->addElement('submit', 'submit', 'Upload');
```

请注意，我们已应用 mimetype 规则，这允许我们传递一个用户可以上传的允许 MIME 类型数组³。

³请注意，JPEG 文件可能会根据浏览器被报告为 image/jpeg 或 image/pjpeg；因此，两者都包含在可接受类型列表中。

虽然调用 applyFilter 方法会转义提交到表单的所有文本值，但它不会转义与文件上传关联的值。因此，我们必须在从 $form 对象检索这些值时（包括二进制文件数据）对每个值应用 escapeValue 函数：

```
if ($form->validate())
{
    // Apply the escape filter to all fields
    $form->applyFilter('__ALL__', 'escapeValue');

    // Instantiate the MySQL class
    $db = &new MySQL($host, $dbUser, $dbPass, $dbName);

    // Fetch the details of the file
    $name = escapeValue($form->_submitFiles['image']['name']);
    $size = escapeValue($form->_submitFiles['image']['size']);
    $type = escapeValue($form->_submitFiles['image']['type']);

    // Fetch file data
    $contents = file_get_contents(
        $form->_submitFiles['image']['tmp_name']);

    // Escape binary data
    $contents = escapeValue($contents);

    $sql = "INSERT INTO image SET
        name='$name',
        size='$size',
        type='$type',
        contents='$contents'";

    // Perform the query
    $result = $db->query($sql);

    // If all went well, say thanks
    if (!$result->isError()) {
        echo 'File Uploaded Successfully';
    } else {
        $form->display();
    }
} ?>
```

请注意，在获取文件详细信息时，我们直接访问了 QuickForm 的一个属性（_submitFiles），在使用对象时这在技术上属于不良做法（如果在将来的 QuickForm 版本中变量名发生更改，这将导致我的脚本出错）。不幸的是，QuickForm 目前没有提供访问此信息的机制，因此我们不得不采用这个变通方法。

既然我们已经上传了一些文件并将它们存储在数据库中，那么显示它们呢？

```
File: 10.php
<?php
// Include the MySQL class
require_once 'Database/MySQL.php';

$Host = 'localhost'; // Hostname of MySQL server
$dbUser = 'harryf'; // Username for MySQL
$dbPass = 'secret'; // Password for user
$dbName = 'sitepoint'; // Database name

$db =& new MySQL($Host, $dbUser, $dbPass, $dbName);

// Define SQL statement to fetch image information
// but NOT CONTENTS!!!
$sql = "SELECT image_id, name, size, type FROM image
    ORDER BY name";

// Fetch the result object
$result = $db->query($sql);

// A loop for each row of the result set
while ($row = $result->fetch()) {
    echo '<img src="11.php?id=' . $row['image_id'] . '" /> <br />';
    echo $row['name'] . ': ' . $row['size'] . ' : ' .
        $row['type'] . '<br />';
}
?>
```

上述代码列出了数据库中的图像。然后它生成一些 HTML，使用 img 标签指定另一个 PHP 脚本，正是该脚本实际显示图像。请注意，我们谨慎地没有选择图像的内容——只选择每个图像所需的信息。否则，这将非常迅速地耗尽 PHP 的内存。

它生成的 HTML 如下：

```
<img src="11.php?id=2" /><br />
mysql.png : 1107 : image/png<br />
<img src="11.php?id=1" /><br />
php_logo.gif : 3872 : image/gif<br />
<img src="11.php?id=3" /><br />
sitepoint_arrow.gif : 508 : image/gif<br />
```

现在，查看 11.php，它显示了用于生成图像的代码：

```
<?php
// Include the MySQL class
require_once 'Database/MySQL.php';

$host = 'localhost'; // Hostname of MySQL server
$dbUser = 'harryf'; // Username for MySQL
$dbPass = 'secret'; // Password for user
$dbName = 'sitepoint'; // Database name

// Instantiate the MySQL class
$db =& new MySQL($host, $dbUser, $dbPass, $dbName);

// If there's not image, die
if (!isset($_GET['id'])) {
	die('No image selected');
}

// Escape the string, for good practice
$_GET['id'] = mysql_real_escape_string($_GET['id']);

// An SQL statement to get the contents and MIME type of the image
$sql = "SELECT * FROM image WHERE image_id='" . $_GET['id'] . "'";

// Fetch the data
$result = $db->query($sql);
$row = $result->fetch();

// Use a header to tell the browser what MIME type the image is
header('content-disposition: inline; filename=' . $row['name']);
header('content-type: ' . $row['type']);
header('content-length: ' . $row['size']);

// Display the contents
echo $row['contents'];
?>
```





我们使用 header 函数向 Web 浏览器发送指令（HTTP 头），指明我们即将发送的图像文件的名称、类型和大小。有关此处使用的头的更多信息，请参见第 4 章。

## 如何使用 PHP 和 MySQL 构建有效的导航？

一个坚实的导航系统是网站最关键的元素之一。做对了，访客会在网站上流连数小时；做错了，你可能会在 http://www.webpagethatsuck.com/ 上“客串亮相”。好消息是，这是一条被反复验证的路径；构建成功导航系统的要素已被清晰定义。

在这里，我们将学习如何为层次结构类别构建两种最稳固且广泛使用的导航类型：面包屑导航和树形菜单。

请注意，我在此处使用的数据库结构方法被称为邻接列表模型。这种方法也许是最容易理解的，并且被广泛使用。然而，它通常不是在数据库中存储层次结构信息的最佳方式，因为需要进行大量处理来分析数据并重建树（使用递归 PHP 函数或多个数据库查询）。如果你需要存储大量层次结构数据，更好的模型是修改后的前序树遍历模型（也称为嵌套集），如文章《在数据库中存储层次结构数据》[11] 中所述。

PEAR::Tree[12] 提供了一个用于处理嵌套集的有用类。有关更多信息，请参见本章末尾的“进一步阅读”部分。

[11] http://www.sitepoint.com/article/1105
[12] http://pear.php.net/Tree

### 汉塞尔与格蕾特

面包屑导航旨在帮助用户了解自己在网站中的位置，并帮助他们返回来时的地方。你可能在互联网上的某个地方见过面包屑导航；例如，如果你访问 SitePoint 的高级 PHP 论坛[13]，你将在顶部看到面包屑导航，如图 9.6 所示。

### 图 9.6. SitePoint 的面包屑

![](img/5b6cdf7cf4cf53e30b19e047895dc464_309_0.png)

每个正斜杠之间的文本是一个“面包屑”，点击后会将用户带到网站中的特定位置。

顺便说一句，它们被称为面包屑，是对格林童话《汉塞尔与格蕾特》的引用——故事中的两个孩子，你可能记得，用面包屑在森林中标记路径，以便能找到回家的路。

### 迷失在树中

树形菜单在软件应用中无处不在，已被应用于从文本驱动的 DOS 应用程序界面到 Windows 及 Linux 等效系统中的“开始”按钮等各种场景。在 Web 上，树形菜单的应用效果参差不齐，主要使用 JavaScript，而 JavaScript 的支持程度各不相同。然而，没有什么能阻止你构建纯基于 HTML 的树形菜单，在该菜单中，点击菜单项会更新菜单。

处理树形菜单有多种方法。为了让你更轻松，我整理了一组类，以各种形式提供树形数据结构。我将留给你来决定如何使用它们来构建你的 HTML（或 JavaScript）菜单。

### 递归表结构

设计菜单本身有多种方法，而存储最初构建菜单所需信息的策略也多种多样。有人可能会认为文本文件最好，有人更喜欢复杂的 PHP 数组，有人主张使用 XML 文档，还有人则倾向于使用数据库。每种方法都有其优缺点，尽管未来可能会看到 XML 成为存储此类信息的主流机制，因为它正在变得更易于开发人员使用。

[13] http://www.sitepointforums.com/forumdisplay.php?forumid=147

在这里，我们将采用最后一种方法：将数据存储在 MySQL 中。这种方法使构建和获取菜单变得容易——只需将新行插入表中，稍后再选择它们即可。它还使以不同“样式”构建最终菜单变得容易；其他方法（例如文本文件）可能会将我们绑定到特定的菜单设计，并在开发期间需要进行大量的文本编辑。

MySQL 的缺点是，如果没有方便的存储过程来帮助我们，我们将不得不一次性获取菜单表的全部内容，并使用 PHP 来操作它们以反映我们想要的结构。执行多个查询来构建菜单会给我们的应用程序带来拖累，并且随着每个新菜单项的添加而加剧。MySQL 的另一个问题是编辑和删除菜单项的问题，这将影响菜单中“分支”之间的关系。我们将在此处解决前一个问题，并留给你自行研究如何解决后一个问题。

让我们再看看我们将使用的表结构：

```
CREATE TABLE menu (
  menu_id   INT(11)     NOT NULL AUTO_INCREMENT,
  parent_id INT(11)     NOT NULL DEFAULT '0',
  name      VARCHAR(255) NOT NULL DEFAULT '',
  description TEXT      NOT NULL,
  location  VARCHAR(255) NOT NULL DEFAULT '',
  PRIMARY KEY (menu_id),
  UNIQUE KEY location (location)
)
```

在这个表中，我们在行之间使用递归关系；每个行都有自己的唯一 menu_id（表的主键），以及一个名为 parent_id 的字段，该字段将行与同一表中的“父”行相关联。这样一来，我们可以定义显示在其他菜单项“下方”的菜单项，从而创建树形结构。默认的 parent_id 为 0，用于定义没有父级的“根”节点（换句话说，就是顶级菜单项）。

在其他字段中，name 是菜单项本身的名称，即它在菜单中出现的样子。description 允许我们向访问者提供关于每个菜单项的更多信息。更重要的是 location 字段，我们将其定义为 UNIQUE（即，没有两个行可以具有相同的 `location` 值）。使用此字段，我们可以定义 URL（或 URL 片段），用户点击菜单项时将被引导到该地址。图 9.7 显示了带有某些示例值的表。

### 图 9.7. menu 表

| 菜单ID | 父ID | 名称 | 描述 | 位置 |
|---|---|---|---|---|
| 1 | 0 | 主页 | 主页 | / |
| 2 | 1 | 新闻 | 站点新闻 | /news/ |
| 3 | 1 | 关于我们 | 关于我们 | /about/ |
| 4 | 1 | 联系我们 | 联系我们 | /contact/ |
| 5 | 0 | 产品 | 产品目录 | /products/ |
| 6 | 5 | 宠物 | 宠物店 | /products/pets/ |
| 7 | 6 | 鸟类 | 鸟舍 | /products/pets/birds/ |
| 8 | 6 | 猫类 | 狮子巢穴 | /products/pets/cats/ |
| 9 | 5 | 书籍 | 书店 | /products/books/ |
| 10 | 9 | 小说 | 小说 | /products/books/fiction/ |
| 11 | 9 | 传记 | 传记 | /products/books/biography/ |
| 12 | 8 | 作品集 | 网站 | /about/folio/ |

在准备好表本身之后，我们需要一些代码来读取内容并构建菜单项列表，然后可以将其“包装”在 HTML 中。因为你可能希望在网站上使用几种不同的“导航样式”，我们将使用类来构建所需的列表，与格式无关。

为了避免用琐事让你厌烦，我们不会详细探讨每个类的全部内容。相反，我们将看看如何使用每个类的 API，这非常简单。毕竟，使用类的乐趣就在于此——你不必关心幕后发生了什么，只需专注于自己的代码即可。

所有菜单类都包含在一个名为 `Menu.php` 的单一文件中，你可以在本章的代码中找到它。它包含以下类：

- Menu 这是一个基类，用于从数据库获取菜单项并提供一些可重用的方法（例如 getMenu），这些方法旨在供 Menu 的子类使用。你不应该直接实例化 Menu；相反，请使用其子类之一。我们稍后会更详细地探讨这一点，因为如果你使用的表结构与我们在此处使用的不同，可能需要对其进行修改。
- **面包屑** (扩展 Menu) 如果使用此类，你将获得一个“面包屑”列表，从“根”面包屑开始。
- **子节点** (扩展 Menu) 此类创建一个列表，包含位于给定菜单项下方一级的所有菜单项。例如，它可以用于为面包屑导航元素提供“下拉”菜单。
- **上下文菜单** (扩展 Menu) 此类显示与当前菜单项处于同一级别的所有菜单项，以及当前菜单项下方一级存在的子项。这可以与面包屑配合使用，以允许你的网站访问者以“水平”和“垂直”两种方式遍历你的菜单系统。
- **折叠树** (扩展 Menu) 此类将始终显示所有根菜单项以及所有“打开”的子菜单，很像 Windows 中的“开始”菜单。
- FullTree 此类只是将整个菜单结构作为树返回，如果你要构建一个基于 JavaScript 的菜单并且需要一次性了解整个菜单结构，这可能很有用。
- **菜单项** 这是一个独立的类，用于从 Menu 类创建 MenuItem 对象。你将从 Menu 类中得到大量这样的对象，存储在数组中。它们将包含表中行的数据，例如重要的“name”和“location”字段。我们稍后会更仔细地查看这一点；如果你在自己的应用程序中使用不同的表结构，你需要知道这里发生了什么。
- **标记** (扩展 菜单项) 这是一种特殊的 MenuItem 形式，因为它用于标记开头


和占据树结构中同一层级的一组菜单项的结束。

关于 Menu 类需要注意的一点是，它们会对菜单表执行全表扫描并一次性获取所有内容。此前我曾建议不要执行全表扫描，但在这种情况下，这是在两害中取其轻的选择，替代方法是使用许多递归查询，这会大幅降低应用程序的性能。

不过，你需要注意，表中行数越多，PHP 处理这些类所需的内存就越多。由于菜单不经常变化，你可以通过使用某种形式的缓存来绕过这个问题——这个话题我们将在第 II 卷第 5 章中讨论。

现在我已经向你介绍了这些类，首先要做的就是不要慌！让我们通过一个例子来逐一查看，它会向你展示这些类有多容易使用。

## 给小鸟喂食

首先，让我们来看看 BreadCrumb 类。这是我们获取菜单的方式：

```php
// Instantiate MySQL connection
$db = &new MySQL($dbHost, $dbUser, $dbPass, $dbName);

// Set the base location for this page relative to Web root
// MODIFY THIS!!!
$baseUrl = '/sitepoint/WebPageElements/12.php';

// Fetch the location fragment to match against menu table
$location = str_replace($baseUrl, '', $_SERVER['PHP_SELF']);

// Instantiate new BreadCrumb menu passing the MySQL connection
// and location
$crumbs = &new BreadCrumb($db, $location);
?>
```

让我们来回顾一下代码。首先，我们像往常一样建立了数据库连接。接下来的两条命令获取 URL 的片段，允许我们将请求与我们的菜单表进行匹配。

注意，如果你自己尝试这段代码，需要修改 $baseUrl 变量以适应你的环境。在定义 $baseUrl 后，我们可以使用 $_SERVER['PHP_SELF'] 获取相对于 Web 根目录的完整 URL，然后去除 $baseUrl。这留下了一个我们可以与菜单表中的 location 字段匹配的字符串。我采用这种方法是为了举例说明，因为它允许我使用单个脚本演示菜单，同时利用 Apache 的“回溯”功能（我们将在本章后面详细讨论）。利用此功能，我们可以获取 URL 中脚本名称右侧出现的路径片段，并将其插入到我们的 PHP 脚本中。例如，请考虑以下 URL：

http://localhost/sitepoint/WebPageElements/12.php/products/

实际脚本名称是 12.php；我可以检查额外的 /products/ 片段来决定显示正确的菜单。不过，你不需要这样做。例如，你可能有多个 PHP 脚本使用相同的代码——或许是一个包含文件——来显示正确的菜单：

http://www.example.com/products/index.php
http://www.example.com/news/index.php

采用这种方法，你可能会使用 PHP 变量 $_SERVER['PATH_INFO'] 来获取脚本位置，并基于此选择菜单。

不过，让我们继续我们的单脚本示例，它使用 URL 后缀作为菜单位置。接下来是所有动作发生的那一行：

```php
$crumbs = &new BreadCrumb($mysql, $location);
```

这将实例化 BreadCrumb 类并将其传递 MySQL 对象，它使用该对象从菜单表中获取数据，利用 $location 变量找到用户在菜单中的当前位置。BreadCrumb 类已准备好完成所有工作并自动构建菜单。

那么菜单在哪里呢？嗯，我不能把它做得太简单，对吧？以 HTML、JavaScript 或其他方式生成菜单，由你决定。BreadCrumb 类所做的全部工作就是返回一个菜单项列表，然后你需要对其进行格式化。以下是一种实现方式：

```html
<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Transitional//EN"
"http://www.w3.org/TR/xhtml1/DTD/xhtml1-transitional.dtd">
```

```html
<html xmlns="http://www.w3.org/1999/xhtml">
<head>
<title> BreadCrumb Menu Example </title>
<meta http-equiv="Content-Type"
content="text/html; charset=iso-8859-1" />
<style type="text/css">
body, a, li
{
font-family: verdana;
font-size: 11px;
}
h1
{
font-family: verdana;
font-size: 15px;
color: navy
}
.breadCrumbs
{
margin-bottom: 10px;
border-style: dashed;
border-width: 2px;
padding: 4px;
width: 400px;
}
</style>
</head>
<body>
<h1>Bread Crumbs Menu</h1>
<div class="breadCrumbs">
<?php
// Display the breadcrumbs
while ($item = $crumbs->fetch()) {
if ($item->isRoot()) {
echo "<a href=\"" . $baseUrl . $item->location() . "\">" .
$item->name() . "</a>";
} else {
echo " <a href=\"" . $baseUrl . $item->location() . "\">" .
$item->name() . "</a>";
}
}
?>
</div>
<b>Sample Urls:</b><br />
<a href="<?php echo $baseUrl; ?>/contact/">Contact</a><br />
<a href="<?php echo $baseUrl; ?>/about/folio/">Folio</a><br />
```

```html
<a href="<?php echo $baseUrl; ?>/products/">Products</a><br />
<a href="<?php echo $baseUrl; ?>/products/books/fiction/">Fiction</a><br />
</body>
</html>
```

稍微简化一下，菜单构建的实际工作发生在这里：

```php
while ($item = $crumbs->fetch()) {
    if ($item->isRoot()) {
        echo "<a href=\"" . $baseUrl . $item->location() . "\">" .
            $item->name() . "</a>";
    } else {
        echo " > <a href=\"" . $baseUrl . $item->location() . "\">" .
            $item->name() . "</a>";
    }
}
```

迭代器方法 fetch 用于遍历菜单项列表，到达末尾时返回 FALSE（有关迭代器的更多信息，请参见第 II 卷第 7 章）。返回的每个 $item 都是 MenuItem 类的实例，我们将在稍后介绍。简而言之，这些是上面用于构建菜单链接的方法：

- isRoot 如果这是菜单树的根，返回 TRUE。
- location 返回菜单表中的 location 字段。
- name 返回菜单表中的 name 字段。

还有一个 description 方法，我们可以用它来显示弹出描述（例如，使用链接的 title 属性）。

图 9.8 显示了生成的链接在浏览器中的外观。

## 图 9.8. 面包屑导航

![](img/5b6cdf7cf4cf53e30b19e047895dc464_317_0.png)

注意，我添加了一些示例 URL 来演示导航，因为面包屑的设计目的是让你找回原路，而不是开辟新路。

## 保持上下文

如你所见，使用 BreadCrumb 类为访问者提供了一种简单的方式，让他们可以访问导航层次结构中高于当前位置的层级。然而，除非我们给访问者提供深入该层次结构的能力，否则此功能用处不大。接下来，我们将把 ContextMenu 类投入使用。此处包含的代码集中在重要部分：

```php
File: 13.php (excerpt)

// Set the base location for this page relative to Web root
// MODIFY THIS!!!
$baseUrl = '/sitepoint/WebPageElements/13.php';

// Fetch the location fragment to match against menu table
$location = str_replace($baseUrl, '', $_SERVER['PHP_SELF']);

// Instantiate new BreadCrumb menu passing the MySQL connection
// and location
```

```php
$crumbs = &new BreadCrumb($db, $location);
// Instantiate the ContextMenu class
$menu = &new ContextMenu($db, $location);
```

这一次，我们构建了 BreadCrumb 类和 ContextMenu 类。这实际上使查询数量翻了一番，可以通过创建更多类来避免，但为了简单起见，我们在此不这么做。

我们可以用来构建面包屑的循环与之前相同。不过，ContextMenu 略有不同：

```php
File: 13.php (excerpt)

<?php
// Display the context menu
while ($item = $menu->fetch()) {
    if ($item->isStart()) {
        echo "<ul>";
    } else if ($item->isEnd()) {
        echo "</ul>";
    } else {
        echo "<li><a href=\"" . $baseUrl . $item->location() . "\">" .
            $item->name() . "</a></li>";
    }
}
?>
```

在这里，我们使用了两个新方法：isStart 和 isEnd。只有 Marker 类会对其中任何一个方法返回 TRUE。Marker 是一个“假”的菜单项，用于宣布同一层级的一组菜单项的开始或结束。这使我们可以构建带有开始和结束标签的 HTML，例如上面示例中的无序列表。

如图 9.9 所示，上下文敏感菜单显示用户在树当前分支中同一层级的所有项目，以及他们当前查看项目的子项目。结合面包屑导航，这允许用户访问菜单表中注册的任何位置。



图 9.9. 带面包屑导航的上下文敏感菜单

![](img/5b6cdf7cf4cf53e30b19e047895dc464_319_0.png)

## 下拉菜单

使用 ChildNodes 类，我们可以将下拉菜单附加到面包屑导航的末尾。

```
File: 14.php (excerpt)

// Set the base location for this page relative to Web root
// MODIFY THIS!!!
$baseUrl = '/sitepoint/WebPageElements/14.php';

// Fetch the location fragment to match against menu table
$location = str_replace($baseUrl, '', $_SERVER['PHP_SELF']);

// Instantiate new BreadCrumb menu passing the MySQL connection
// and location
$crumbs = &new BreadCrumb($db, $location);

// Get the number of breadcrumbs
$size = $crumbs->size();

// Instantiate the ChildNodes class
$menu = &new ChildNodes($db, $location);
```

请注意，size 方法可用于任何菜单类，以获取菜单中的项目数量。在此示例中，我们需要知道面包屑的数量，以便可以在正确的位置附加下拉菜单：

```
<?php
// Display the breadcrumbs
$i = 1;
while ($crumb = $crumbs->fetch()) {
echo "<td class=\"menu\">";
echo "<a class=\"root\" href=\"" . $baseUrl .
$crumb->location() . "\">" . $crumb->name() .
"</a><br />";
// Check if this is now current place to attach the drop down
if ($i == $size) {
// Display the child nodes
while ($item = $menu->fetch()) {
echo "<a href=\"" . $baseUrl . $item->location() . "\">" .
$item->name() . "</a><br />";
}
}
$i++;
echo "</td>";
}
?>
```

图 9.10 展示了运行中的下拉菜单。

图 9.10. 带下拉菜单的面包屑导航

![](img/5b6cdf7cf4cf53e30b19e047895dc464_321_0.png)

请注意，我们是从当前位置构建 ChildNodes 的：

```
$menu = &new ChildNodes($db, $location);
```

但情况不一定非得如此。例如，我们可以这样做：

```
while ($crumb = $crumbs->fetch()) {
    $menu = &new ChildNodes($db, $crumb->location());
}
```

这会为每个面包屑构建一个子菜单，而不是使用 $location 的当前值。这样做的好处是，我们可以使用 JavaScript 显示下拉菜单，例如，当访问者将鼠标悬停在每个面包屑上时展开它们。

## 折叠树菜单

接下来是 CollapsingTree 类。折叠树将始终显示菜单的根元素，以及当前位置的子项和当前位置与根之间的所有条目。这类似于 Windows 和 Linux 中的 "开始"-类型菜单；当你继续向下导航菜单树时，之前用于导航的菜单将保持打开状态。请注意，这个类要完成的工作最多，因此比其他类更慢，尽管它提供了可能最有用的导航功能。

获取菜单的方式与前面的示例相同：

```
// Set the base location for this page relative to Web root
// MODIFY THIS!!!
$baseUrl = '/sitepoint/WebPageElements/15.php';

// Fetch the location fragment to match against menu table
$location = str_replace($baseUrl, '', $_SERVER['PHP_SELF']);

// Instantiate new BreadCrumb menu passing the MySQL connection
// and location
$crumbs = &new BreadCrumb($db, $location);

// Instantiate the CollapsingTree class
$menu = &new CollapsingTree($db, $location);
```

将菜单作为对象存储后，我们可以像以前一样构建页面。这次，为了呈现菜单项本身，我们将使用一些其他“技巧”来给导航带来略有不同的外观：

```
// Define some bullet for menu items, in this case just spaces
$bullet = '&nbsp;&nbsp;';

// Set the current depth of the menu
$depth = 0;

// Display the collapsing tree menu
while ($item = $menu->fetch()) {
    // If this is the start of a new menu branch, increase the depth
    if ($item->isStart()) {
        $depth++;
    // If this is the end of a menu branch, decrease the depth
    } else if ($item->isEnd()) {
        $depth--;
    // Display a menu item
    } else {
        // Reset the bullets
        $bullets = '';

        // Build the bullets based on the current depth
        for ($i = 0; $i <= $depth; $i++) {
            $bullets .= $bullet;
        }

        // Build onMouseOver description
        $mouseOver = " onMouseOver=\"window.status='\" .
            addslashes($item->description()) .
            "';return true\\\" \".
            \"onMouseOut=\"window.status='';return true\\\" \"";

        // Display the menu item with bullets
        echo $bullets . "<a href=\"" . $baseUrl . $item->location() .
            "\" . $mouseOver . \">" . $item->name() . "</a><br />";
    }
}
```

在这里，我们通过监视开始和结束标记来跟踪层次结构中当前菜单项的深度。根据菜单项的深度，我们可以修改每个项目的“项目符号”；在此示例中，我使用了 HTML 空格实体 (&nbsp;) 来营造缩进效果⁴。结果如图 9.11 所示。

图 9.11. 折叠菜单

## 折叠菜单 + 面包屑

![](img/5b6cdf7cf4cf53e30b19e047895dc464_323_0.png)

折叠菜单旨在用于完全用 PHP 呈现的菜单。对于 JavaScript 解决方案，你可能会想要下一个类。

## 完整树菜单

FullTree 类仅将整个菜单作为结构获取，该结构可用于构建 JavaScript（或其他）菜单——它适用于任何需要完整了解菜单的系统。鉴于浏览器兼容性问题，我并不是 JavaScript 的大粉丝，因此我将使用简单（但可靠）的 HTML 来演示 FullTree 类。话虽如此，使用此类生成用于 JavaScript 的菜单是非常可行的，例如 http://www.treemenu.com/ 或 PEAR::HTML_TreeMenu[15] 中的菜单。

启动 FullTree 类与以前一样（这次我将省略面包屑导航）：

```
File: 16.php (excerpt)

// Instantiate MySQL connection
$db =& new MySQL($host, $dbUser, $dbPass, $dbName);

// Set the base location for this page relative to Web root
// MODIFY THIS!!!
$baseUrl = '/test/WebPageElements/16.php';

// Fetch the location fragment to match against menu table location
$location = str_replace($baseUrl, '', $_SERVER['PHP_SELF']);

// Instantiate the Collapsing Tree class
$menu =& new FullTree($db, $location);
```

构建菜单引入了 MenuItem 类中你尚未见过的另一个方法：

```
File: 16.php (excerpt)

// Display the collapsing tree menu
while ($item = $menu->fetch()) {
  // If this is the start of a new menu branch, increase the depth
  if ($item->isStart()) {
    echo '<ul>';
  // If this is the end of a menu branch, decrease the depth
  } else if ($item->isEnd()) {
    echo '</ul>';
  // Display a menu item
  } else {
    // Display the menu item with bullets
    echo "<li><a href=\"" . $baseUrl . $item->location() . "\">";
    if ($item->isCurrent()) {
      echo ">> " . $item->name() . " <<";
    } else {
      echo $item->name();
    }
    echo "</a></li>";
  }
}
```

在这里，我们使用了 isCurrent 方法，以便可以在菜单中标记用户的当前位置。稍后我将总结 MenuItem 类中所有可用的方法。

图 9.12 展示了完整树菜单的全部风采。

图 9.12. 完整树菜单

![](img/5b6cdf7cf4cf53e30b19e047895dc464_323_0.png)

- 完整树菜单
  - 主页
    - 关于
      - 作品集
    - 联系
    - >> 新闻 <<
  - 产品
    - 图书
      - 传记
      - 小说
    - 宠物
      - 鸟类
      - 猫类

URL 是 /phprecipes/WebPageElements/16.php/news/
BaseUrl 是 /phprecipes/WebPageElements/16.php
位置片段是 /news/

## 处理不同的表结构

如果你使用与我相同的表结构，那么一切都很好，但如果你的列名称不同怎么办？在 Menu 类的类文件中，列名称被指定为常量：

```
@define( 'MENU_TABLE', 'menu' ); # Name of menu table
@define( 'MENU_ID', 'menu_id' ); # ID of menu item
@define( 'MENU_PARENT_ID', 'parent_id' ); # Parent ID column
@define( 'MENU_NAME', 'name' ); # Name of menu item
@define( 'MENU_DESCRIPTION', 'description' ); # Description of item
@define( 'MENU_LOCATION', 'location' ); # URI of menu
```

4 在实际实现中，最好使用 CSS 边距来缩进菜单。

[15] http://pear.php.net/HTML_TreeMenu




这使你可以在代码中覆盖其中的任何常量，并允许你使用与这里所示不同名称的表和列。

## Summary

以下是一个“模拟”脚本，演示了所有 Menu 类及其方法的用法。每个方法都用注释进行了描述。

```
<?php
// Instantiate MySQL connection
$db = &new MySQL($host, $dbUser, $dbPass, $dbName);

// Build the correct $location variable e.g.
//$baseUrl = '/index.php';
$location = str_replace($baseUrl, '', $_SERVER['PHP_SELF']);

// Instantiate the menu, one of the following
$menu = &new BreadCrumb($mysql, $location);
$menu = &new ChildNodes($mysql, $location);
$menu = &new ContextMenu($mysql, $location);
$menu = &new CollapsingTree($mysql, $location);
$menu = &new FullTree($mysql, $location);

// If you need it, find out how many items in the menu
$size = $menu->size();

// Loop through the items
while ($item = $menu->fetch()) {
    if ($item->isStart()) {
        // This is a Marker to show the START of a submenu
    } else if ($item->isEnd()) {
        // This is a Marker to show the END of a submenu
    } else {
        if ($item->isCurrent()) {
            // This is a menu item corresponding to the current location
        }
        $item->id(); // The menu_id from table menu
        $item->parent_id(); // The parent_id from table menu
        $item->name(); // The name field from table menu
        $item->description(); // The description field from table menu
        $item->location(); // The location field from table menu
    }
}
}
?>
```

## How do I make “search engine friendly” URLs in PHP?

在典型的 PHP 应用程序中，你可能会看到这样的 URL：

```
http://www.example.com/article.php?id=123&page=4
```

URL 中的 id GET 变量用于从数据库中识别文章，而 page 变量告诉脚本显示文章的哪一页。不过，这里有一个小问题：许多搜索引擎会忽略 GET 变量，跳过 URL 中 ? 后面的所有内容。Google 和 AllTheWeb 是这一规则的两个例外，但即使它们也会对索引的内容持“谨慎”态度。

为了解决这个问题，并同时开发出对人类更友好的 URL 结构，最好使用类似这样的 URL：

```
http://www.example.com/article/123/4
```

实现这种改进的 URL 格式有两个步骤：

- [ ] 将查询字符串变量（?id=123&page=4）转换为路径样式格式（/123/4）
- [ ] 隐藏 PHP 脚本的名称（/article.php），使其看起来像一个标准目录（/article）

在接下来的章节中，我将介绍并演示在 Apache 服务器上实现此目标的技术。

关于构建搜索引擎友好 URL 和 Apache mod_rewrite 的进一步阅读资料，请参阅名为“进一步阅读”的章节。

### Doing Without the Query String

对于像你我这样的 Web 开发人员，像 ?id=123&page=4 这样的查询字符串很容易阅读。但典型的 Web 用户——以及许多搜索引擎——会被这种符号和信息的混合体弄糊涂。流行的 Apache 服务器的一个特别好的特性是，当遇到像 http://www.example.com/article.php/123/4 这样的 URL 时，它足够智能，能够识别 article.php 是文件名，而其后的所有内容（/123/4，我们将其称为 **URL 后缀**）可以被忽略。当然，诀窍在于让 PHP 看到该 URL 后缀并读取其中包含的值。

幸运的是，虽然 Apache 对 URL 后缀视而不见，但 PHP 不是。PHP 提供了一些可用于收集此信息的变量，即 `$_SERVER['PATH_INFO']`、`$_SERVER['PHP_SELF']`、`$_SERVER['REQUEST_URI']` 和 `$_SERVER['SCRIPT_NAME']`。以下脚本演示了它们的实际效果：

```
<?php
// Examine some pre-defined variables
echo '$_SERVER[\'PATH_INFO\']: ' . @$_SERVER['PATH_INFO'] .
'<br />';
echo '$_SERVER[\'PHP_SELF\']: ' . @$_SERVER['PHP_SELF'] .
'<br />';
echo '$_SERVER[\'REQUEST_URI\']: ' . @$_SERVER['REQUEST_URI'] .
'<br />';
echo '$_SERVER[\'SCRIPT_NAME\']: ' . @$_SERVER['SCRIPT_NAME'] .
'<br />';
?>
```

如果将此文件放在服务器上并加载，例如 http://www.example.com/phpanth/WebPageElements/18.php，则其输出如下：

```
$_SERVER['PATH_INFO']:
$_SERVER['PHP_SELF']: /phpanth/WebPageElements/18.php
$_SERVER['REQUEST_URI']: /phpanth/WebPageElements/18.php
$_SERVER['SCRIPT_NAME']: /phpanth/WebPageElements/18.php
```

乍一看，这些变量并不特别引人注目。但请看当我们向 URL 添加 URL 后缀和查询字符串（例如 http://www.example.com/phpanth/WebPageElements/18.php/this/is?a=test）时会发生什么：

```
$_SERVER['PATH_INFO']: /this/is
$_SERVER['PHP_SELF']: /phpanth/WebPageElements/18.php/this/is
$_SERVER['REQUEST_URI']:
/phpanth/WebPageElements/18.php/this/is?a=test
$_SERVER['SCRIPT_NAME']: /phpanth/WebPageElements/18.php
```

这就有意思了！特别是，$_SERVER['PATH_INFO'] 似乎是从 URL 后缀中获取隐藏值的最佳位置。不幸的是，当我们实现 URL 简化的第二部分（隐藏 PHP 脚本名称）时，PHP 将不再为我们创建此变量，因此在这个阶段我们不能依赖它。

为了帮助从 URL 后缀中获取变量，我为你创建了 PathVars 类。该类会自动分析浏览器请求的 URL 并获取 URL 后缀中的所有值。该类使用 `$_SERVER['REQUEST_URI']` 变量来查看 URL 后缀，虽然这可能不是显而易见的选择，但在我们稍后隐藏 PHP 脚本名称时，它是上述四个变量中唯一保持可靠的一个。

为了省去你阅读 PathVars 类代码的麻烦（如果你想看，可以在代码存档中找到它），我将直接向你展示它的实际效果。首先，我们实例化 PathVars 类，并向其传递 `$_SERVER['SCRIPT_NAME']` 的值，即脚本的 _实际_ 路径：

```
<?php
// Include the PathVars class
require_once 'Url/PathVars.php';

echo '$_SERVER['REQUEST_URI'] is ' . $_SERVER['REQUEST_URI'] .
    '<br />';
echo '$_SERVER['SCRIPT_NAME'] is ' . $_SERVER['SCRIPT_NAME'] .
    '<br />';

// Instantiate PathVars
$pathVars =& new PathVars($_SERVER['SCRIPT_NAME']);
```

PathVars 将给定的脚本路径与 `$_SERVER['REQUEST_URI']` 的值进行比较，并生成一个值列表，你可以随后访问这些值：

```
echo "<b>Iterate over Extracted Variables</b><br />\n";
while ($var = $pathVars->fetch()) {
    echo $var . "<br />\n";
}

echo "<b>Fetch Variable 3 by Index</b><br />\n";
echo $pathVars->fetchByIndex(3);
?>
```

你可以使用 `fetch` 遍历提取的路径变量，也可以使用 `fetchByIndex`，它将返回你提供索引的变量。还可以使用 `size` 来查找对象找到了多少个变量。最后，`fetchAll` 可用于返回完整的路径变量数组。如果给定的 URL 如 http://www.example.com/phpanth/WebPageElements/19.php/this/is/?a=test/of/the/class/，Figure 9.13 显示的输出如下：

图 9.13. 提取的路径变量

```
$_SERVER['REQUEST_URI'] is
/phpanth/WebPageElements/19.php/this/is/?a=test/of/the/class/
$_SERVER['SCRIPT_NAME'] is /phpanth/WebPageElements/19.php
Iterate over Extracted Variables
this
is
of
the
class
Fetch Variable 3 by Index
the
```

特别要注意的是，PathVars 类检测并忽略了 URL 中查询字符串样式的段（?a=test）。这是出于设计目的，这样查询字符串（例如 PHP 自动生成的会话标识符）的存在就不会干扰 URL 后缀中的变量。

## Hiding PHP Scripts with ForceType

在成功将查询字符串变量移动到 URL 后缀后，要实现搜索引擎友好 URL，我们只需隐藏 PHP 脚本的文件名。也就是说，我们希望从 http://www.example.com/article.php/123/4 过渡到 http://www.example.com/article/123/4。实际上有两种不同的方法可以做到这一点；在本节中，我将解释其中最简单的一种，并在下一节中介绍第二种方法。与读取 URL 后缀的方法一样，这两种技术都依赖于 Apache Web 服务器的有用功能。





改变 URL 中出现的文件名最明显的方法是重命名文件；也就是说，我们可以简单地将脚本 article.php 重命名为 article。当然，没有 .php 扩展名，Apache 无法知道该文件是 PHP 脚本。因此，默认情况下，它会直接将未解析的 PHP 代码发送到浏览器——这绝对是*我们不想要的*！

要纠正这一点，我们需要明确告诉 Apache 将该文件视为 PHP 脚本。这可以通过 .htaccess 文件轻松实现，但你首先需要确保 Apache 已配置为允许此操作。如果你在自己的服务器上工作，只需确保在 Apache 的 httpd.conf 文件中将 AllowOverride 设置为 All 即可。如果你使用的是 Web 主机，则需要请求他们来处理。完成后，将以下代码放入名为 .htaccess 的文件中，并将其保存在要重命名的脚本所在的同一目录：

```
File: forcetype/.htaccess

<Files article>
 ForceType application/x-httpd-php
</Files>
```

此指令告诉 Apache 将名为 article 的文件视为 PHP 脚本。简单，对吧？

要亲自尝试，请查看本章代码存档中的 forcetype 目录。我已经使用一个名为 article 的脚本和一个将其标识为 PHP 脚本的 .htaccess 文件进行了设置。以下是 article 的代码：

```
File: forcetype/article

<?php
 // Include the PathVars class
 require_once 'Url/PathVars.php';

 // Create instance of PathVars
 $pathVars = new PathVars($_SERVER['SCRIPT_NAME']);

 echo 'This is the article script<br />';

 if ($pathVars->fetchByIndex(0)) {
  echo 'The article ID is ' . $pathVars->fetchByIndex(0);
 }
 ?>
```

尝试在 URL 后缀中加载带有文章 ID 的页面（例如 http://www.example.com/phpanth/WebPageElements/forcetype/article/123）。如果 Apache 已正确配置以允许 `.htaccess` 文件中的 ForceType 指令，则应正确显示 ID。

## 通过重写 URL 隐藏 PHP 脚本

虽然 `ForceType` 是一个巧妙的解决方案，但有一个替代方案提供了更多功能，并完全消除了 URL 中出现任何 PHP 脚本文件名部分的需要。该替代方案是 **mod_rewrite**。这是一个可选的 Apache 模块，需要在你的服务器上安装，并且与 `ForceType` 类似，你需要在 `httpd.conf` 中为你的网站设置 `AllowOverride All`。

一般来说，`mod_rewrite` 允许你检测浏览器对特定 URL 的请求，并指示 Apache 将其视为对完全不同的 URL 的请求。在最简单的情况下，你可以告诉 Apache 检测对 `/article` 等路径的请求，并将其视为对 `/article.php` 的请求。当然，这与我们通过 `ForceType` 实现的没有区别，所以让我们再进一步，看看 `mod_rewrite` 到底有多灵活！

与检测特定 URL 不同，我们可以使用 `mod_rewrite` 来检测*任何* URL 并将请求指向单个 PHP 文件。让我们来看一个这样做的示例 `.htaccess` 文件：

```
RewriteEngine On
RewriteRule !(\.gif|\.jpe?g|\.css|\.php|^images/.*|^files/.*)$ index.php [nocase,last]
```

`RewriteEngine` 行只是告诉 Apache 为此目录启用 `mod_rewrite` 处理；`RewriteRule` 是*真正*起作用的地方。上面的 `RewriteRule` 告诉 Apache 将*所有*请求发送到 `index.php`，*除了*对 `.gif`、`.jpg`、`.jpeg`、`.css`、`.php` 文件的请求，或者来自子目录 `images` 和 `files` 中的任何内容，它应该允许这些正常进行。

显然，`index.php` 变成了一个非常重要的脚本！它可能如下所示：

```
<?php
// Include the PathVars class
require_once 'Url/PathVars.php';

// MODIFY THIS FOR YOUR CONFIGURATION!!!
$baseUrl = '/phpanth/WebPageElements/rewrite/';

// Create instance of PathVars
$pathVars = new PathVars($baseUrl);

// What's the first path variable?
switch ($pathVars->fetchByIndex(0)) {
case 'download':
  // Examine the second path variable
  if ($pathVars->fetchByIndex(1)) {
    echo 'Downloading file ' . $pathVars->fetchByIndex(1);
  } else {
    echo 'Download <a href="' . $baseUrl .
      'download/myStuff.zip">myStuff.zip</a><br />';
  }
  break;
case 'article':
  // Examine the second path variable
  if ($pathVars->fetchByIndex(1)) {
    echo 'Viewing article ' . $pathVars->fetchByIndex(1);
  } else {
    echo 'View <a href="' . $baseUrl .
      'article/123">Article 123</a><br />';
  }
  break;
default:
  echo 'This is the home page<br />';
  echo '<a href="' . $baseUrl .
    'download/">Downloads</a><br />';
  echo '<a href="' . $baseUrl . 'article/">Articles</a><br />';
  break;
}
?>
```

在此代码中，我使用了 PathVars 类来允许 index.php 处理站点上的大多数请求。以下是它可能需要处理的一些 URL：

- **http://www.example.com/phpanth/WebPageElements/rewrite/**
  PathVars 在 URL 后缀中找不到任何参数。该脚本将显示站点的主页。

- **http://www.example.com/phpanth/WebPageElements/rewrite/download/myStuff.zip**
  PathVars 在 URL 后缀中检测到参数 download 和 myStuff.zip。该脚本将把指定的文件作为下载发送到浏览器。

- **http://www.example.com/phpanth/WebPageElements/rewrite/article/123**
  PathVars 在 URL 后缀中检测到参数 article 和 123。该脚本将显示 ID 为 123 的文章以供查看。

## URL 重写和 PathVars

请特别注意本示例中 PathVars 的实例化方式：

```
// MODIFY THIS FOR YOUR CONFIGURATION!!!
$baseUrl = '/phpanth/WebPageElements/rewrite/';

// Create instance of PathVars
$pathVars = new PathVars($baseUrl);
```

URL 重写的一个副作用是，$_SERVER['SCRIPT_NAME'] 和 $_SERVER['REQUEST_URI'] 不再能通过比较来找到 URL 后缀。前者包含 PHP 脚本的实际名称，而后者包含浏览器实际请求的 URL。

因此，在像这样使用 URL 重写设置时使用 PathVars 时，你需要将包含 .htaccess 的目录路径提供给构造函数，而不像以前那样简单地将其传递给 $_SERVER['SCRIPT_NAME']。

简单地说，使用 URL 重写时，给 PathVars 提供你希望它忽略的 URL 部分。

还要注意的是，在构建链接时我们使用了 $baseUrl 变量，而不是 $_SERVER['PHP_SELF']。后者会在链接中再次包含 index.php，这是我们不希望看到的。

## 设计 URLs

基于 PHP 的网站通常是一组执行不同任务的应用程序，每个应用程序都有其自身可识别的 URL。例如：

- http://www.example.com/forums/
  一个论坛

- http://www.example.com/blog/
  一个 Web 日志（或“博客”）

- http://www.example.com/downloads/
  一个下载管理器

这些 URL 中的每一个都是应用程序的根。如果站点构建良好，这些应用程序将被集成，例如，如果下载文件需要用户名和密码，则论坛使用相同的用户名和密码。

在每个应用程序中，都有*视图*对应站点访问者将看到的不同页面类型。例如：

- `http://www.example.com/forums/discussion/php`
  PHP 讨论论坛的一个视图

- `http://www.example.com/forums/discussion/php/34`
  PHP 论坛中一条消息的一个视图

每个视图都有默认外观，但可能能够接受额外的*参数*。例如：

- `http://www.site.com/forums/discussion/php/?sort=popularity`
  按受欢迎程度对帖子进行排序

- `http://www.site.com/forums/discussion/php/?sort=date&numposts=10`
  显示论坛上的最新十篇帖子

明白我的意思了吗？应用程序和视图由 URL 后缀标识，而该视图使用的参数由标准查询字符串变量标识。

在视图和参数之间做这种划分，可以真正帮助构建驱动站点的 PHP。确定站点访问者请求了哪个应用程序和视图，需要固定数量的变量，这些变量可以通过它们在 URL 中的相对位置来识别。相比之下，特定视图通常会使用许多参数，但并非所有参数都会同时存在。因此，参数最好用名称/值对来标识，查询字符串使这成为可能。

在代码中使用 URL 后缀值需要一些规划。再考虑一下这个 URL：

`http://www.site.com/forums/discussion/php/`

你只能按索引（即变量在 URL 中出现的位置）来访问变量。使用上面的 URL，你可能会使用 **PathVars** 来检索包含变量的数组：



```
Array
(
    [0] => forums
    [1] => discussion
    [2] => php
)
```

就您的代码而言，您需要有一种决策逻辑，将每个变量的处理传递给知道如何处理它的代码。在此示例中，

- 1. 从您网站的“根”PHP 脚本（例如 index.php）开始，检查路径变量 0，以确定将此任务传递给哪个代码。在此示例中，是论坛代码。
- 2. 从论坛代码开始，检查路径变量 1，以确定论坛应用程序中的哪个代码应处理此事。在此示例中，是讨论代码。
- 3. 在讨论代码中，检查路径变量 2，以确定应显示哪个讨论。

在每种情况下，代码都会将工作委托给其他代码，直到到达需要执行实际工作的点（例如，讨论代码会执行数据库查询以选择所请求讨论中的所有主题，并将其作为 HTML 表显示）。

您实际处理工作委托的方式取决于偏好和经验。您可能只需使用 include 语句，在每次做出决策时加载正确的 PHP 脚本。更复杂但通常更灵活的方法使用面向对象编程，其中决策过程基于为每个步骤选择正确的类来处理。

无论如何，这都会使您的网站朝着成为框架的方向发展——一种结构化的环境，您向其中添加应用程序的代码，框架按需执行这些代码。在考虑如何实现这一点时，值得研究一些可用的其他 PHP 框架，例如 eZ publish[16]、Phrame[17] 和 Ambivalence[18]，以便进一步了解您需要考虑的设计问题。

- [16] http://developer.ez.no/
- [17] http://phrame.sourceforge.net/
- [18] http://amb.sourceforge.net/

## 进一步阅读

- 面向对象 PHP：分页结果集：http://www.sitepoint.com/article/662

本文介绍了面向对象编程的基础知识，并在其最后一个示例中使用了一个与本章类似的分页结果集。

- 构建可扩展菜单类：http://www.devshed.com/Server_Side/PHP/ExtensibleMenuClass/

本文介绍了构建菜单类的另一种观点，该类使用 MySQL 完成大部分工作，而不是 PHP。

- 在数据库中存储层次数据：http://www.sitepoint.com/article/1105

本文详细探讨了邻接模型和嵌套集方法。

- PEAR::Tree 教程：http://www.phpkitchen.com/article.php?story=20030427152620585

有关 PEAR::Tree 用法的说明，请参阅本文，它提供了用于处理嵌套集数据结构的 API。

- 搜索引擎友好 URL：http://www.sitepoint.com/article/485

本文解释了搜索引擎友好 URL 的方方面面。

- Apache 的 ForceType 指令：http://www.devarticles.com/art/1/143/2

本教程详细介绍了如何使用 ForceType 指令。

- mod_rewrite：URL 重写初学者指南：http://www.sitepoint.com/article/910

此处考察了 Apache 的 mod_rewrite。

- eZ Publish：PHP 的杀手级应用：http://www.sitepoint.com/article/917

这个三部分系列从头开始考察了 eZ publish 框架。

# 10 错误处理

在第 1 章中，我介绍了 PHP 的内置错误处理机制，我们讨论了错误通常分为四种基本类型：

- **语法错误**：脚本不遵守 PHP 的基本语言规则，无法执行。
- **语义错误**：在执行代码时，PHP 遇到了在 PHP“语法”方面不合法的情况，例如将字符串传递给期望数组的函数。
- **环境错误**：PHP 脚本在执行过程中使用的环境中遇到了问题，例如 MySQL 服务器不可用。
- **逻辑错误**：就 PHP 引擎而言，脚本执行正确，但并未按设计者预期的方式运行。

在本章中，我们将探讨 PHP 提供的扩展本机错误报告机制并让您更好地控制错误处理方式的机制。这些机制的好处通常体现在处理环境错误方面；这些机制为您的代码提供了优雅退出执行的机会，并允许您向网站访问者隐藏错误，同时私下接收错误通知。

## PHP 5 中的错误处理

即将发布的 PHP 5 将包含一种新的错误处理机制，该机制应从根本上改进 PHP 4 中处理错误的方式。PHP 5 将提供一种与 Java 等语言常见的 try-catch 控制结构。值得牢记这一点，即这一变化即将到来，以便您在时机成熟时轻松修改代码。这些修改可能只是对所有使用 trigger_error 的位置进行查找和替换操作。或者，它们可能更复杂，即将所有对 trigger_error 的调用都通过您自己定义的单个函数传递，这样您只需修改该函数即可切换到生成错误的新机制。

## 如何使用 PHP 实现自定义错误处理程序？

到这时，您可能已经非常熟悉 PHP 的本机错误报告；或许您熟悉它的程度超出了您的意愿，这要归咎于那些不可避免的语法错误。PHP 4 提供了生成和处理错误的额外机制，您可以控制这些机制；这些机制在 PHP 手册[1] 中有所描述。能够生成自己的错误消息可以让您为应用程序添加额外的错误报告，帮助您在问题和错误发生后进行追踪。同时，创建自己的错误处理程序的功能允许您记录错误消息并控制传递给网站访问者的输出。

## 错误级别

PHP 脚本在解析以排除语法错误后，在运行脚本时可以生成三类错误：

- 错误：导致 PHP 停止脚本进一步执行的致命错误
- 警告：PHP 可以从中恢复的一般环境错误
- **通知**：PHP 并不真正在意的潜在问题，但可能反映您代码中的错误

了解此分类在生成您自己的错误时将很有用。

**错误报告级别**确定上述哪一类错误会导致 PHP 显示错误消息。PHP 安装的默认错误报告级别由 `php.ini` 中的 `error_reporting` 选项设置。例如，将其设置为 `E_ALL` 告诉 PHP 报告所有错误类型：

```
error_reporting = E_ALL
```

除这种特殊情况外，指示 PHP 使用特定错误级别会导致 PHP 仅报告该级别的错误；如果您希望 PHP 报告多种错误类型，则必须使用**按位运算符**将级别**组合**起来。例如，要报告除*通知*之外的所有错误类型，通常会按以下方式配置：

```
error_reporting = E_ALL & ~E_NOTICE
```

您可以在 PHP 脚本中使用 `error_reporting` 函数来确定当前的错误报告级别：

```
<?php
echo error_reporting();
?>
```

这将以整数显示当前级别（例如 `E_ALL` 为 2047）。您也可以使用 `error_reporting` 函数设置错误级别。例如：

```
<?php
error_reporting(E_ALL ^ E_NOTICE); // Report all except notices
echo error_reporting(); // Displays 2039?>
```

在上面的示例中，我们指示 PHP 报告除通知之外的所有错误，使用按位 XOR 运算符 `^`，从 `E_ALL` 错误级别中减去 `E_NOTICE` 错误级别。

以下是一些其他说明性示例：

`File: 3.php`

```php
<?php
error_reporting(E_ALL); // Report all errors
error_reporting(2047); // Report all errors
error_reporting(0); // Turn off error reporting
?>
```

通常，您不需要修改上述示例之外的错误级别。

> **应该使用哪个错误报告级别？**
> 
> 开发代码时，始终将错误级别设置为最高值 E_ALL（或 2047）。这将告知您所有错误。特别是，它将显示有助于您发现未初始化变量的通知——未初始化变量是许多逻辑错误的根源。此错误级别还将确保其他使用您代码的人的最大可移植性，他们可能希望以此级别运行 PHP 且不查看您的工作生成的任何错误消息。
> 
> 设置此错误级别的最佳方法是在 php.ini 中使用 error_reporting 设置。如果不可能，次佳方案是使用带有以下命令的 .htaccess 文件：
> 
> ```
> php_value error_reporting 2047
> ```
> 
> 无论如何，都要将该设置全局应用于所有代码。
> 
> 请记住，仅仅告诉 PHP 不要报告某些错误并不意味着这些错误没有发生！开发代码时要小心，并使用完整的错误报告。

需要注意的是，错误报告级别适用于内置的 PHP 错误处理程序，而不适用于您自己定义的错误处理程序（我们稍后将介绍）。换句话说，就默认 PHP 错误报告机制而言，您可以关闭错误报告，同时仍然可以使用您自己定义的错误处理程序来捕获错误。

控制错误行为的另一种机制是错误抑制运算符 @，可用于抑制 PHP 函数和表达式生成的错误消息。例如：

`File: 4.php`

```php
<?php
// Use error reporting operator
if (!@mysql_connect('localhost', 'wronguser', 'wrongpassword')) {
    echo 'Error connecting to MySQL Server: ' . mysql_error();
}
```



}
?>

假设此处显示的用户名和密码不正确，如果不使用错误抑制运算符，mysql_connect 将显示一条错误消息。在本示例中，我已抑制 PHP 生成的错误，以便显示我自己的错误。

错误抑制运算符不仅适用于函数：

```
<?php
if (@$_GET['name'] == 'Bill') {
    echo 'This page is not available to you';
} else {
    echo 'Welcome';
}
?>
```

如果不是因为这里存在错误抑制运算符，PHP 在发现 $_GET['name'] 变量未定义时将显示一个错误，前提是错误报告级别设置为显示通知。在本示例中，我们使用错误抑制运算符来告诉 PHP，我们理解该变量在某些情况下可能未定义，因此不需要被提醒此事实。

我建议您谨慎使用错误抑制运算符，仅在您希望自行控制错误报告的情况下使用。为举例说明，对于前一个示例，我建议您明确检查 $_GET['name'] 是否已定义后再使用它：

```
<?php
if (isset($_GET['name']) && $_GET['name'] == 'Bill') {
    echo 'This page is not available to you';
} else {
    echo 'Welcome';
}
?>
```

采用这种方法编写代码（并通常对所有传入的数据进行检查）将产生更可靠、更安全的应用程序。过度使用错误抑制运算符会导致代码非常难以调试。

## 生成错误

如上文所示，有三种错误级别可用于报告代码中的错误消息：错误、警告和通知。生成错误消息的介质是函数 trigger_error[2]，它可以放置在代码中的任何位置，并在执行时导致 PHP 报告您指定级别的错误。您的选择是 E_USER_ERROR、E_USER_WARNING 和 E_USER_NOTICE，这里的“用户”是指您——PHP 开发者。

下面是一个简单示例：

```
<?php
if (!@mysql_connect('localhost', 'wronguser', 'wrongpassword')) {
    trigger_error('Error connecting to MySQL Server: ' .
        mysql_error(), E_USER_ERROR);
}

echo 'Hello World!';
?>
```

在这里，我们使用了错误抑制运算符来抑制正常的错误消息，以便我们可以使用 trigger_error 显示一条更有用的消息。我们提供给 trigger_error 的第二个参数（可选）是我们希望报告错误的级别；默认级别为 E_USER_NOTICE。

从理论角度来看，值得考虑我们在这里究竟做了什么。如果 mysql_connect 失败，PHP 通常会使用的错误级别将是警告，因为它将其视为不阻止脚本运行的环境错误。然而，我们抑制了正常的警告消息，并将严重程度提升为错误。由于错误被认为对 PHP 脚本是致命的，这会停止 PHP 对脚本的执行。在这种情况下，输出“Hello World!”的指令不会被执行，而 PHP 通常会产生的警告原本会允许它执行。

我们为什么要这样做？嗯，如果跟随数据库连接尝试的脚本依赖于该数据库连接来产生有用的输出，那么如果数据库连接失败，让脚本继续运行就没有多大意义了。虽然某些应用程序可能能够在没有数据库连接的情况下凑合，但我们可以使用 trigger_error 立即阻止那些不能的应用程序。

[2] http://www.php.net/trigger_error

## 生成错误的策略

您在代码中如何使用 `trigger_error` 完全由您决定，但为了充分发挥其作用，最好心中有一种策略，使您能够正确处理代码生成的错误。在选择要触发的错误类型时，请考虑从应用程序 _用户_ 的角度来看错误意味着什么，而不是对 PHP 引擎意味着什么。以下旨在代表使用不同错误级别的最佳实践：

**E_USER_ERROR**

这是您可用的最严重的错误级别，是一个会停止 PHP 执行其余代码的致命错误。从使用您的应用程序的人的角度来看，致命错误是导致应用程序在根本层面上无法履行其职责的错误。例如，脚本无法连接到存储应用程序想要呈现的内容的 MySQL 服务器。

**E_USER_WARNING**

在此级别，您的应用程序可以继续执行，尽管用户请求的操作出了问题。使用此错误级别的好方法是，当用户做出超出应用程序限制的操作时应用它。例如，他们可能请求了不存在内容的 URL，或者向脚本传递了错误类型的数据（例如，他们通过 `$_GET` 变量传递了一个字符串，而该变量预期包含整数值）。显然，这应在合理范围内应用；一般来说，触发的错误无法像代码中的返回值那样有效处理（参见下文“触发的错误与条件执行”部分）。

**E_USER_NOTICE**

此级别适用于向网站的用户和管理员提供信息。如果有人在尝试登录网站安全区域时，连续三次输错用户名/密码组合，则可能是触发 `E_USER_NOTICE` 错误的好时机。此错误将导致向网站管理员发送一封电子邮件，警告他们可能存在试图破解用户身份验证系统的行为。您也可以使用 E_USER_NOTICE 在网站所有页面上显示一条消息，声明：“今天下午1点，网站将因例行维护而停机十分钟。”

请注意，在这些级别触发的错误可能不是应用程序执行时生成的唯一错误。PHP 生成的错误类型，E_PARSE、E_ERROR、E_WARNING 和 E_NOTICE 也将“生效”，除非您专门禁用它们，或使用错误抑制运算符将其抑制。这意味着您可以区分“PHP 级别”错误和“应用程序级别”错误，这有助于使错误处理更加灵活。

## 自定义错误处理程序

现在您已了解 PHP 的错误级别并看到 trigger_error 函数的实际运行情况，是时候了解如何实现自定义错误处理程序了。

PHP 为您提供了指定自己的错误处理程序的功能，您可以使用它来捕获错误并按您选择的方式响应，例如向网站访问者显示友好的消息，同时使用详细消息更新面向网站管理员的错误日志。使此功能成为可能的机制是一个将用作回调的 PHP 函数——即 PHP 将自动调用的函数。定义函数后，我们指示 PHP 使用 set_error_handler[3] 函数来使用错误处理程序，该函数将自定义错误处理函数的名称作为其参数。请注意，可以将类方法用作自定义错误处理程序，但实现此功能所需的代码相当丑陋，因此我们在此情况下将避免使用类。

请注意，您无法处理导致 PHP 立即停止执行的错误，即 E_PARSE 和 E_ERROR 级别。E_ERROR 级别用于 PHP 可用内存耗尽（例如，使用 DOM 扩展解析巨大的 XML 文档）并被迫立即停止的情况。至于 E_PARSE——嗯，你不是在实时 Web 服务器上编辑文件，对吧？

[3] http://www.php.net/set_error_handler

```
<?php
/**
 * Custom Error handler
 *
 * @param int error level number
 * @param string error message
 * @param string php script where error occurred
 * @param int line number in script where error was triggered
 * @param array current state of all global variables
 */
function myErrorHandler($errLvl, $errMsg, $errFile, $errLine,
        $errContext)
{
    // Switch statement watching for specific error levels
    switch ($errLvl) {
        case E_USER_ERROR:
            $error = "<h2>Custom Error Message</h2>
            <b>E_USER_ERROR</b> in $errFile on line $errLine<br />
            $errMsg";
            break;
    }
    echo $error;
}

// Set the custom error handler
set_error_handler('myErrorHandler');

// Trigger an error
if (!@mysql_connect('localhost', 'wronguser', 'wrongpassword')) {
    trigger_error('Error connecting to MySQL Server: ' .
            mysql_error(), E_USER_ERROR);
}
?>
```

在本示例中，我们首先创建自定义错误处理函数。函数中定义的参数是触发错误时将作为参数传递的所有参数。您不必全部使用（甚至不必定义它们），但它们出现的顺序必须与这里所示一致。第一个参数 $errLvl 是表示此错误级别的数字。我们将其用作 switch 语句的基础，在本示例中，该语句仅用于捕获 E_USER_ERROR 报告。第二个参数 $errMsg 是错误消息，在此例中，我们将其作为 trigger_error 函数的第一个参数提供。参数 $errFile 包含发生错误的 PHP 脚本的名称；$errLine 是该文件中发生错误的行号。





occurred. 最后，$errContext（在本示例中我们尚未使用它）包含一个数组，其中包含错误发生点的所有全局变量的名称和值。在某些情况下，这些信息可能对调试有用，例如，它包含 $_SERVER 变量，其中可以找到访客浏览器的详细信息。

定义自定义错误处理函数后，我们需要做的就是使用 set_error_handler 告诉 PHP 新的处理程序。

执行此脚本将生成以下 HTML：

```
<h2>Custom Error Message</h2>
<b>E_USER_ERROR</b> in /home/username/www/errorhandling/6.php on
line 31<br />
Error connecting to MySQL Server: Access denied for user:
'wronguser@localhost' (Using password: YES)
```

需要注意的是，该示例生成了两条错误消息：一条是由 mysql_connect 函数产生的 E_WARNING，我们已通过错误抑制运算符将其抑制；另一条是我们通过 trigger_error 生成的 E_USER_ERROR。如前所述，错误抑制运算符和 error_reporting 函数仅适用于 PHP 的内置错误处理程序，而不适用于您定义的自定义处理程序。这意味着自定义处理程序实际上会捕获这两个错误，如以下脚本所示：

```
<?php
/**
 * Custom Error handler
 *
 * @param int error level number
 * @param string error message
 * @param string php script where error occurred
 * @param int line number in script where error was triggered
 * @param array current state of all global variables
 */
function myErrorHandler($errLvl, $errMsg, $errFile, $errLine,
 $errContext)
{
 // Switch statement watching for specific error levels
 switch ($errLvl) {
 case E_USER_ERROR:
 $error = "<h2>Custom Error Message</h2>
 <b>E_USER_ERROR</b> in $errFile on line $errLine<br />
 $errMsg";
 break;
 // Catch all other errors
 default:
 $error = "<h2>Default Error Message</h2>
 <b>Level: $errLvl</b> in $errFile on line $errLine<br />
 $errMsg";
 break;
 }
 echo $error;
 }

// Set the custom error handler
set_error_handler('myErrorHandler');

// Attempt to disable E_WARNING messages (applies to built-in
// handler only)
error_reporting(E_ALL ^ E_WARNING);

// Trigger an error
if (!@mysql_connect('localhost','wronguser','wrongpassword')) {
    trigger_error('Error connecting to MySQL Server: ' .
    mysql_error(), E_USER_ERROR);
}
?>
```

尽管我们试图通过 error_reporting 函数和错误抑制运算符禁用 E_WARNING 消息，但上述示例仍会报告这两个错误。

## 触发的错误与条件执行

PHP 的自定义错误处理机制实际上为您的应用程序引入了另一层错误处理，这一次是在全局级别。在使用此机制之前，理解这种方法的后果非常重要。

到目前为止，您可能已在调用时将错误处理构建到代码中。以下是一个典型示例：

```
<?php
// Some function which updates the database
function updateUserDetails($name, $password, $email)
{
    // If update succeeds...
    return TRUE;
}

// If update failed
return FALSE;
}

// If a form was submitted
if (isset($_GET['submitUserDetailsForm'])) {
    // Perform "call time" error checking
    if (updateUserDetails($_GET['name'], $_GET['password'],
        $_GET['email'])) {
        echo 'Update succeeded';
    } else {
        echo 'Update failed. Please try again';
    }
}
?>
```

这段代码（旨在说明一种常见模式，而非可运行示例）展示了错误处理通常如何构建到应用程序中。调用 updateUserDetails 函数的代码会检查从函数中获取的值（TRUE 或 FALSE），并作出相应响应。

PHP 的自定义错误处理机制不允许这种模式。让我们看看上述示例的等效写法：

```
<?php
// Some function which updates the database
function updateUserDetails($name, $password, $email)
{
    // If update failed
    trigger_error('Update failed', E_USER_WARNING);
}

// If a form was submitted
if (isset($_GET['submitUserDetailsForm'])) {
    updateUserDetails($_GET['name'], $_GET['password'],
        $_GET['email']);
}
?>
```

调用 updateUserDetails 函数的代码现在无法检查函数是否成功。相反，您的自定义错误处理程序必须对函数做出响应，由于它与 updateUserDetails 或调用它的代码完全独立地定义，因此要使其正确响应会很困难。有方法可以将自定义错误处理与您的应用程序更紧密地集成，但通常涉及复杂的变通方法和 hack，最终导致难以维护且易于损坏的代码。

在 PHP 4 中，开发者在处理错误时会面临一个问题，即条件错误检查仅在发生错误的点起作用，而自定义错误处理在全局级别运行，并且与代码的逻辑流程断开连接。如前所述，PHP 5 引入了一种新的错误处理机制，称为 **异常处理**，它将允许您在错误发生的点 *和* 全局级别处理错误。目前，最好不要过度使用 PHP 的自定义错误处理；而是将其简单视为网站的“看门狗”，确保记录发生的错误，以便下次有时间时可以更正它们。PHP 4 的一个良好过渡解决方案是 PEAR::Error 类，它是核心 PEAR 安装的一部分。使用 PEAR::Error，当您准备利用 PHP 5 中将包含的新错误处理时，您的代码应该相当容易修改。有关 PEAR::Error 的建议阅读材料可在本章末尾找到。

## 如何记录和报告错误？

自定义错误处理程序变得有用的地方在于创建您稍后可以访问的错误日志，并在调整应用程序时参考它们。为了方便起见，PHP 自带 error_log 函数，可用于写入日志文件或发送包含错误报告的电子邮件等操作。此函数可在自定义错误处理程序内部用于存储错误数据。例如：

```
<?php
/**
 * Custom Error handler
 *
 * @param int error level number
 * @param string error message
 * @param string php script where error occurred
 * @param int line number in script where error was triggered
 * @param array current state of all global variables
 */
function myErrorHandler($errLvl, $errMsg, $errFile, $errLine,
                        $errContext)
{
    $time = date('YmdHis');
    $errMsg = htmlspecialchars($errMsg);
    $error = <<<EOD
####START ERROR####
Level: $errLvl
File: $errFile
Line: $errLine
Time: $time

$errMsg
####END ERROR####

EOD;
error_log($error, 3, 'log/errors.log');
switch ($errLvl) {
  case E_USER_ERROR:
    echo 'System is temporarily unavailable. ' .
      'Please try again later';
    break;
  }
}

// Set the custom error handler
set_error_handler('myErrorHandler');

// Trigger an error
if (!@mysql_connect('localhost', 'wronguser', 'wrongpassword')) {
  trigger_error('Error connecting to MySQL Server: ' .
    mysql_error(), E_USER_ERROR);
}
?>
```

自定义错误处理程序现在以易于使用 PHP 字符串函数解析的格式记录错误。它将这些错误记录到 errors.log 文件中，该文件如下所示：

```
####START ERROR####
Level: 256
File: c:\htdocs\phpanth\errorhandling\8.php
Line: 39
Time: 20031012233727

Error connecting to MySQL Server: Access denied for user:
'wronguser@127.0.0.1' (Using password: YES)
####END ERROR####
```

## 电子邮件过载

尽管 error_log 能够发送包含错误消息的电子邮件，但请小心！您的收件箱中可能会出现比您预期的更多内容。您可以通过 php.ini 值 ignore_repeated_errors 和 ignore_repeated_source 控制错误报告的频率——有关详细信息，请参见附录 A。

当然，您并不局限于仅使用 error_log 函数来创建日志文件。您可以决定编写自己的类来记录错误，或者考虑使用 PEAR::Log[4]，它提供了更多选项来捕获应用程序中的数据。

## 如何优雅地显示错误？

既然您已经了解了如何定义自己的自定义错误处理程序，我可以向您展示如何使用 PHP 的输出缓冲（我将在第二卷第 5 章中详细讨论，并在 PHP Manual[5] 中描述），以便您的生产网站能优雅地告知用户“暂时遇到困难”，而无需在部分呈现的 HTML 页面上贴上丑陋的错误消息。以下示例演示了这种方法，并提供了一个更全面的自定义错误处理程序，它能够处理多个错误级别：

```
<?php
/**
 * Custom Error handler
 *
 * @param int error level number
 * @param string error message
 * @param string php script where error occurred
 * @param int line number in script where error was triggered
 * @param array current state of all global variables
 */
function myErrorHandler($errLvl, $errMsg, $errFile, $errLine,
$errContext)
{
    switch ($errLvl) {
        // Handle ERRORs
        case E_USER_ERROR:
            // Stop and clean the second buffer
```

[4] http://pear.php.net/package/Log
[5] http://www.php.net/manual/en/ref.outcontrol.php




ob_end_clean();
// Clean out the main buffer
ob_clean();
// Display an error message
echo '
<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Strict//EN"
"http://www.w3.org/TR/xhtml1/DTD/xhtml1-strict.dtd">
<html xmlns="http://www.w3.org/1999/xhtml">
<head>
<title> Temporary Interruption </title>
<meta http-equiv="Content-Type"
content="text/html; charset=iso-8859-1" />
</head>
<body>
<h2>Temporary Interruption</h2>
The site is currently down for non-scheduled maintenance.<br />
Please try again shortly
</body>
</html>';
// End and flush the main buffer
ob_end_flush();
// Stop execution
exit();
break;
// Handle WARNINGs
case E_USER_WARNING:
// Clean out the main buffer
ob_clean();
// Display an error message
echo '<b>Warning:</b> ' . $errMsg;
break;
// Handle NOTICEs
case E_USER_NOTICE:
// Display an error message
echo '<b>Notice:</b> ' . $errMsg;
break;
}
}
```

这个自定义错误处理程序能够处理三种错误级别：E_USER_ERROR、E_USER_WARNING 和 E_USER_NOTICE。你会注意到，它在每个级别处理输出缓冲区的方式略有不同。E_USER_ERROR 消息（如前所述，这是一个致命错误）会导致处理程序清除两个输出缓冲区（共有两个，其原因稍后会变得显而易见），并显示关于网站宕机的消息；这会完全移除可能已发送到缓冲区的任何 HTML。E_USER_WARNING 错误会导致第二个缓冲区被擦除并替换为错误消息；结果，HTML 页面的正文被错误消息替换。E_USER_NOTICE 行为将通知错误添加到第二个缓冲区中——它只是附加到现有 HTML 之后。

看看页面主体现在的样子：

```
// Set the custom error handler
set_error_handler('myErrorHandler');
// Start an output buffer for ERRORs
ob_start()
?>
<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Strict//EN"
    "http://www.w3.org/TR/xhtml1/DTD/xhtml1-strict.dtd">
<html xmlns="http://www.w3.org/1999/xhtml">
<head>
<title> Custom Error Handling with Buffering </title>
<meta http-equiv="Content-Type"
    content="text/html; charset=iso-8859-1" />
</head>
<body>
<h2>Example Errors</h2>
<?php
// Start a second output buffer for NOTICES and WARNINGs
ob_start();
?>
```

如上所示，在指示 PHP 使用我们的自定义错误处理程序后，我们将一个输出缓冲区嵌套在另一个缓冲区内，以便页面的页头和页脚位于与正文分开的缓冲区中。

```
<a href="?<?php echo $_SERVER['PHP_SELF']; ?>?triggerError=error">
Trigger a Fatal Error</a><br />
<a href="?<?php echo $_SERVER['PHP_SELF']; ?>?triggerError=warning">
Trigger a Warning</a><br />
<a href="?<?php echo $_SERVER['PHP_SELF']; ?>?triggerError=notice">
Trigger a Notice</a><br />

<?php
// Generate sample errors
if (isset($_GET['triggerError'])) {
switch ($_GET['triggerError']) {
```

```
case 'error':
    trigger_error('A fatal error', E_USER_ERROR);
    break;
case 'warning':
    trigger_error('You have been warned!', E_USER_WARNING);
    break;
case 'notice':
    trigger_error('Please take note!', E_USER_NOTICE);
    break;
}
}
// Finish and display the second buffer
ob_end_flush();
?>
</body>
</html>
<?php
// Finish the main buffer
ob_end_flush();
?>
```

在页面正文中，在第二个缓冲区内，我们使用了 trigger_error 来演示处理程序，并使用 $_GET 变量 triggerError。

执行脚本时，你会发现致命错误会导致呈现完全不同的页面（如 E_USER_ERROR 的自定义错误处理程序中定义）；警告错误会用警告消息替换三个链接，而错误通知会添加到三个链接下方。

只要小心处理，就可以将自定义处理程序与输出控制相结合，以优雅的方式（从网站访问者的角度）处理错误。不过请注意，最好保持这类代码简洁务实，而不是构建过于复杂的东西，原因将在 "如何在 PHP 中实现自定义错误处理程序？" 中讨论，位于 "触发的错误与条件执行" 节。

## 进一步阅读

- [PHP 中的错误处理](http://www.devshed.com/Server_Side/PHP/ErrorHandling)

这个两部分系列深入探讨了 PHP 的自定义错误处理功能以及如何将其与输出缓冲相结合。

- [错误处理](http://www.derickrethans.nl/errorhandling/talk.html)

Derick Rethans，PHP 的领先开发者之一，在这个很棒的教程中对从 HTTP 状态页面到调试和分析 PHP 代码的错误处理技术进行了简洁的分析。

- [PEAR-Error 详解](http://www.php-mag.net/itr/online_artikel/psecom,id,330,nodeid,114.html)

Alexander Merz 在 PHP 杂志上发表的这篇免费文章中详细考察了 PEAR::Error。

# 附录 A：PHP 配置

这是一个关于配置 PHP 的快速参考，涵盖了你需要了解的最重要的一般设置，无论是在实时环境中运行应用程序，还是因为它们影响安全性或编码方式。

## 配置机制

配置 PHP 的主要机制是 php.ini 文件。作为主文件，它让你可以控制所有配置设置。条目通常采用以下格式：

```
setting = value
```

不过，在做出更改之前，请务必阅读文件中提供的注释。有一些小技巧，例如在 Unix 上 include_path 使用冒号 (:) 作为分隔符，而在 Windows 上使用分号 (;)。

大多数 Web 主机不会让你访问 php.ini 文件，除非你对系统拥有根访问权限（如果你使用的是廉价虚拟托管服务，通常不是这种情况）。你的下一个选择是使用 .htaccess 文件来配置 PHP（假设 Web 服务器是 Apache）。

.htaccess 文件是一个纯文本文件，你将其放在公共 Web 目录中，以确定 Apache 在从该目录提供页面时的行为；例如，你可以标识允许公众访问的页面。请注意，.htaccess 文件的效果是递归的——它也适用于子目录。

要使用 .htaccess 文件配置 PHP，你的托管提供商必须在 Apache 主 httpd.conf 配置文件中为你的 Web 目录应用 AllowOverride Options 或 AllowOverride All 设置。假设已完成此操作，有两个 Apache 指令可用于修改 PHP 的配置：

**php_flag**
用于具有布尔值的设置（即 on/off 或 1/0），例如 register_globals

**php_value** 用于为设置指定字符串值，例如你可能使用的 include_path 设置

以下是示例 .htaccess 文件：

```
## Switch off register globals
php_flag register_globals off

## Set the include path
php_value include_path ".:/home/username/pear"
```

控制 PHP 配置的最后一种机制是 ini_set 和 ini_alter 函数组，它们允许你修改配置设置，以及 ini_get，它允许你检查配置设置，还有 ini_restore，它将 PHP 的配置重置为由 php.ini 和任何 .htaccess 文件定义的默认值。使用 ini_set，这里有一个示例，允许我们在连接到 MySQL 时避免定义主机、用户名和密码：

```
ini_set('mysql.default_host', 'localhost');
ini_set('mysql.default_user', 'harryf');
ini_set('mysql.default_password', 'secret');

if (!mysql_connect()) {
 echo mysql_error();
} else {
 echo 'Success';
}
```

请注意，PHP 为某些设置（例如 error_reporting）提供了替代函数，这些函数与 ini_set 的作用基本相同。使用哪个是个人偏好的问题。

请注意，某些设置（例如 register_globals）只能通过 php.ini 或 .htaccess 才能有用地修改，因为这些设置会在 PHP 开始执行脚本之前影响其行为。

此外，某些配置设置只能在 php.ini 中更改，例如 extension_dir，它告诉 PHP 查找 PHP 扩展的目录。要完整参考控制设置，请参阅 PHP 手册[1]。





## 关键安全性和可移植性设置

表 A.1 列出了与 PHP 脚本安全性和可移植性相关的最重要 PHP 设置。

### 表 A.1. 关键安全性和可移植性设置

| 设置 | 说明 |
|---|---|
| register_globals (default: off) | 从传入的 HTTP 请求变量（例如 GET 和 POST）自动创建全局变量。出于安全性和可移植性考虑，强烈建议将此功能关闭。有关更多详细信息，请参阅 http://www.php.net/register_globals。 |
| magic_quotes_gpc (default: off) | 使用反斜杠自动转义传入 HTTP 请求变量中的引号，有助于防止 SQL 注入攻击。如果你知道自己在做什么，通常最好关闭此功能，并在将数据插入数据库时自行处理转义，因为此功能可能会在表单方面给你带来问题，并且会引入性能开销。有关使脚本与此功能兼容的信息，请参见第 1 章。 |
| call_time_pass_reference (default: off) | 允许在调用时使用变量引用（例如 htmlentities(&$string)）。为了保持代码整洁易懂，并确保可移植性，请保持此功能关闭。 |
| short_open_tag (default: on) | 允许使用 `<?` 而不是较长的 `<?php` 来启动 PHP 代码块。还允许使用 `<?=` 输出 PHP 表达式，这与 `<?php echo` 相同。虽然方便，但这些快捷方式不符合 XML 规范，并且在遇到 `<?xml version="1.0"?>` 之类的 XML 处理指令时，可能会导致 PHP 处理器混淆。许多人已关闭 short_open_tag，因此为获得最大可移植性，请避免使用快捷方式，并在开发期间关闭此功能。 |
| asp_tags (default: off) | 允许使用 ASP 风格的标签（`<% ... %>`）作为 PHP 开始和结束标签（`<?php ... ?>`）的替代方案。很少有人使用这些标签，因此为获得最大可移植性，最好避免使用它们，并在开发期间关闭此功能。 |
| error_reporting (default: E_ALL & ~E_NOTICE) | 开发时，为获得最大可移植性，最好将此项设置为 E_ALL，以便 PHP 在例如你的代码依赖的 `$_GET` 变量未初始化等情况下通知你。这迫使你编写更安全、逻辑错误更少的代码，以避免警告。这还可确保你的代码在以这种方式配置的其他服务器上运行正常。 |
| display_errors (default: on) | 决定 PHP 是否将错误消息发送到 Web 浏览器。在实时环境中运行应用程序时，通常最好关闭此选项，而是使用 PHP 的日志机制将错误捕获到文件中，例如。 |
| open_basedir (default: not set) | 允许将所有 PHP 文件操作限制在给定目录或其子目录中。这是个好主意，可防止用于显示文件内容的脚本等，被用来访问服务器上其他位置的敏感文件。 |
| allow_url_fopen (default: on) | 允许为 `fopen` 等函数指定远程文件位置（例如 `fopen( 'http://www.sitepoint.com/', 'r' );`）。这是一个方便的工具，但对于编写不良的脚本，也可能是安全风险。如果确定不需要，请将其关闭。 |

## 包含和执行设置

表 A.2 列出了与包含（includes）以及 PHP 脚本运行情况相关的最重要 PHP 设置。

### 表 A.2. 包含和执行设置

| 设置 | 说明 |
|---|---|
| `include_path` (default: '.') | 允许你在使用 `include` 相关命令时，指定 PHP 应搜索的相对路径和绝对路径。请确保至少指定了当前目录 (.)，否则大多数第三方脚本将无法正常工作。在 Unix 系统中，目录列表由冒号 (`:`) 分隔，而在 Windows 中，分隔符是分号 (`;`)。 |
| `auto_prepend_file` (default: not set) | PHP 会在执行任何请求的脚本 *之前* 执行指定的文件。对于执行站点范围的操作（如安全性、日志记录、定义错误处理程序、删除由魔术引号功能添加的反斜杠等）非常有用。适用于确定仅自己使用的应用程序，但不适用于打算分发的代码。无法使用 `.htaccess` 文件修改 `php.ini` 设置的人将无法使用此类代码。列表分隔符与 `include_path` 设置所用的相同。 |
| `auto_append_file` (default: not set) | `auto_prepend_file` 的对应项，在请求的脚本执行 *之后* 执行。 |
| `max_execution_time` (default: 30) | 指定通过 Web 服务器运行的 PHP 脚本允许执行的最长时间（秒）。通常，最好保持默认设置，并使用 `set_time_limit` 函数按脚本基础扩展限制。任何一个值为 0 都会删除脚本执行时间的任何限制。 |
| `memory_limit` (default: 8M) | PHP 在运行时可用的内存量。通常，默认值足够，但例如在处理非常大的 XML 文档或处理图像时，可能需要增加它。此值越大，脚本实际使用的内存越多，则可用于服务器上运行的其他应用程序的内存就越少。 |
| post_max_size (default: 8M) | PHP 将通过 HTTP POST 接受的最大数据量（例如上传图像的表单）。如果应用程序允许用户上传较大文件，可能需要增加此值。 |

## 错误相关设置

表 A.3 列出了与 PHP 处理错误的方式相关的最重要 PHP 设置，此外还有在表 A.1 中描述的 display_errors 和 error_reporting。

### 表 A.3. 错误相关设置

| 设置 | 说明 |
|---|---|
| log_errors (default: off) | 允许将错误记录到文本文件中，并与 error_log（下文）配合使用。对于已关闭访客错误显示的实时站点非常有用。 |
| error_log (default: not set) | 启用 log_errors 时，错误将被记录到的文件名。 |
| ignore_repeated_errors (default: off) | 使用此项，如果同一 PHP 脚本的同一行出现相同错误，则每次脚本执行只报告一次。有助于防止在记录到文本文件时，因循环中出现的错误而导致日志文件过大。 |
| ignore_repeated_source (default: 30) | 与 ignore_repeated_errors 类似，但在这种情况下，它会抑制 PHP 脚本中同一类型的重复错误。 |
| report_memleaks (default: on) | 请确保此项已开启，尤其是在使用 PHP 的实验版本或非稳定版本时，否则泄漏内存可能会耗尽所有可用空间并导致服务器崩溃。error_reporting 必须设置为报告警告，此设置才生效。 |

## 其他设置

表 A.4 列出了 PHP 配置中你应了解的其他重要设置。

### 表 A.4. 其他设置

| 设置 | 说明 |
|---|---|
| session.save_path (default: /tmp) | 如果在基于 Windows 的系统上将会话存储在文件中，则需要将此设置修改为 PHP 可写入会话文件的可用目录。 |
| session.use_cookies (default: 1) | 使用 Cookie 在客户端存储会话 ID，而不是将会话 ID 放在 URL 中（这可能会带来更大的安全风险）。 |
| extension_dir (default: './') | 可找到已编译 PHP 扩展的路径。在基于 Windows 的系统上，可能类似于：`extension_dir = C:\php-4.3.2\extensions\` |
| extension | 仅在基于 Windows 的系统上使用，用于识别应加载的所有扩展。指定的扩展应位于 `extension_dir` 路径（上文）中。例如：`extension = php_xslt.dll` |





# 附录 B：托管提供商检查表

PHP，以及更广泛的 LAMP 组合（Linux、Apache、MySQL 和 PHP/Perl/Python），可通过成千上万的 Web 主机获得，价格非常实惠。您可以轻松获得高质量的 Web 托管，每站点每月低于 10 美元即可满足 90% 的需求。话虽如此，所有 PHP 安装并不都相同，很大程度上取决于 php.ini 中定义的配置设置以及主机为您安装的扩展。还有许多与您对自己环境所拥有的控制程度相关的一般问题，如果您不想以后遇到大麻烦，这些问题很重要。

这是在为托管服务付款前应调查的关键问题的摘要。联系潜在的提供商，并让他们针对每个问题作出回复。之后，向了解/使用过该服务的其他人寻求意见。有许多在线论坛，您可以在那里找到能提供建议的人。不过请注意，“知识渊博”与“无知”的比例严重偏向无知；请掌握技术细节，以便您能够核实所给出的答案是否确实可靠。

我在此提供的某些观点可能显得有些极端，但经历过几次之后，您可能会想要花钱买到真正的价值，而不是花周六的早晨去修复主机周五晚上为您制造的问题。

### 一般问题

- [ ] 要求 Linux 和 Apache (1.3)

从性能和可靠性的角度来看，这是最佳组合。避免使用 Apache 2.x 的任何主机（它与 PHP 尚未完全稳定）。询问 Linux 发行版的详细信息。虽然 Red Hat 和 Suse 很受欢迎，但您可能会发现使用 Debian（或者更好，是 Rock Linux）的主机更了解自己在做什么。

- [ ] 主机是否为您提供服务器的 SSH 访问权限？

SSH 为您提供到服务器的安全连接，以便从 Linux 命令行执行任务或使用 SCP（安全复制）传输文件。避免任何允许您使用 telnet（一种在 Internet 上连接到服务器的根本不安全方式）的主机。对于 Windows 用户，Putty[1] 是通过 SSH 使用的绝佳命令行工具，而 WinSCP[2] 提供了使用 SSH 连接的安全文件传输机制。哦，不要使用 ftp 传输文件——它和 telnet 一样不安全。

[1] http://www.chiark.greenend.org.uk/~sgtatham/putty/download.html
[2] http://winscp.sourceforge.net/eng/

### 主机是转售商还是自己维护服务器？

如果您需要基础技术层面的帮助（例如，您自称是新手），转售商可以提供显著价值，但他们通常对服务器的控制程度与您相同。“直扑来源”意味着在出现系统问题时，您不必处理延迟，因为您很可能会直接与维护服务器的人打交道。缺点是，他们往往不太“容忍新手”，因此您可能会得到答案——但不一定是您能理解的答案。

### 主机在多大程度上“超载”服务器？

许多 Web 托管公司在服务器上创建的账户数量远超系统规定的最大值。最佳指标是 uptime 命令（您需要有权限使用）；它会告诉您服务器在 1、5 和 15 分钟内的平均负载。理想情况下，服务器的平均负载绝不应超过 1。显然，问题不像这样简单，但一旦您看到服务器负载超过 5，您的 PHP 应用程序就会开始出现明显的延迟。

### 托管提供商关于从命令行运行脚本和程序的政策是什么？

MySQLDump 是备份数据库的非常方便的工具，但如果您无法运行它，那就毫无用处。一些主机会自动终止任何执行时间超过指定时间的命令行应用程序。

### 主机是否为您提供对 cron（允许您安排批处理作业的 Unix 实用程序）的访问权限？

如果是，请确保主机允许执行命令行脚本。一些主机已实施 cron，使其通过 Web URL 执行脚本。如果相关脚本使用 MySQLDump 应用程序来备份数据库，这就没用了——通过 Apache 执行的 PHP 脚本通常以用户身份运行，该用户不会拥有完成该工作所需的正确权限。

### 与 PHP 相关的问题

- 您可以在实际分配到的服务器上查看 phpinfo 的输出吗？

一些主机可能会声称这是安全风险，但专业主机知道，隐藏即安全并不能替代 _真正的_ 安全。phpinfo 提供的信息对那些知道自己在做什么、并且已正确设置 Linux、Apache 和防火墙的托管提供商来说，_并非_ 安全风险。phpinfo 告诉您的内容是确认事实的最佳方式。

- PHP 是作为 Apache 模块安装的（而不是 CGI 变体）？

这能提供更好的性能。

- Apache 设置 AllowOverride 是设置为 Options 还是 All？

这将允许您使用 .htaccess 文件修改 php.ini 设置。

- PHP 安全模式是否禁用？

php.ini 中的 safe_mode 选项在理论上是一种使 PHP 安全、防止用户执行某些任务或使用某些安全敏感函数的方法。如果您在进行任何严肃的 PHP 工作，安全模式只会带来巨大的麻烦。

- 检查主机的升级政策。

询问主机在升级执行前会给予多少通知。检查他们是否会为您提供将用于升级的 php.ini 文件副本（在升级发生前）。一夜之间将 register_globals = on 切换为 register_globals = off 的主机数量相当可观。确保在主机执行升级之前，先在您的开发系统上针对新版本测试您的应用程序。

- 请求提供已安装 PHP 扩展的列表。

确认这些扩展与您的应用程序的要求相匹配。例如，很少有主机费心提供 XSLT 扩展。同时确认主机保证所有扩展在 PHP 升级之间仍可用。

- [ ] PHP 是否可用于从命令行使用？

如果不能，您可能需要访问 Perl 或 Python，或者能够运行 shell 脚本（如果您满意于这些语言的话）。通常，运行严肃的网站需要您能够运行常规批处理作业（使用 cron），用于备份、向您发送 PHP 错误日志等任务。

- [ ] 最后但同样重要的是，提出一两个问题来测试您的托管提供商对 PHP 的了解。虽然编写 PHP 代码可能不是他们的工作，但当您发现自己对 PHP 的了解远多于主机时，结果令人沮丧。拥有了解您需求的主机很重要。

# 附录 C：安全检查表

考虑到在线 PHP 应用程序本质上暴露给任何人和所有人，在开发应用程序时，安全应该是顶级关注点之一，如果不是 _首要_ 关注点的话。在某种程度上，PHP 应用程序开发的简便性也是其最大的弱点之一，因为对于不了解可能危险的初学者来说，部署一个安全防线如筛子般漏洞百出的应用程序非常容易。

请确保您了解情况，如有任何疑问，请询问。开放 Web 应用安全项目（OWASP）[1] 是一个企业赞助的社区，致力于提高 Web 安全意识，是了解潜在危险的绝佳信息来源。他们最近发布了一份 Web 应用程序中常见安全缺陷的“前 10 名”列表，我在此概述了其中的相关要点。

### 主要安全漏洞

- 未经验证的数据

永远不要信任从 Web 浏览器获得的任何内容。浏览器完全不在您的控制之中，伪造 HTTP 来源等值很容易。伪造表单中的隐藏字段也很容易。

更重要的是，例如在处理表单时，请仔细验证数据。使用“全部拒绝，仅允许少量”的政策。例如，如果注册表单有一个用户名字段，请仅允许字母字符和可能的数字 0–9，而不仅仅是拒绝特定的特殊字符。使用正则表达式将数据限制在您需要的内容。第 9 章中您看到的 PEAR::QuickForm 等包提供了验证表单的内置机制，并能很大程度上帮助您弥补可能忽略的弱点。

另外，涉及 include 文件等内容时，请注意以下逻辑：

```
include($_GET['page']);
```

请确保将 `$_GET['page']` 的值与您的代码设计为包含的文件列表进行核对：

[1] http://www.owasp.org/





```php
$pages = array(
    'news.php', 'downloads.php', 'links.php'
);

if (in_array($_GET['page'], $pages)) {
    include $_GET['page'];
} else {
    include 'not_found.php';
}
```

如果没有这样的检查，攻击者很容易使用类似的代码来执行其他 PHP 脚本——甚至是你没有编写的脚本。

## 访问控制缺陷

如果你不清楚自己在做什么，这种形式的基本逻辑很容易出错。例如，开发人员通常使用类似这样的逻辑来检查数据库中的用户名/密码组合：

```php
if ($numRows != 0) {
    // allow access ...
}
```

这意味着即使在数据库中找到多个匹配项，他们也会允许用户登录，而如果你的网站还有命令注入等安全漏洞（见下文），这可能会让攻击者获得比你预期的多得多的访问权限。在你认为安全的情况下，很容易犯错误，但实际上逻辑很容易被绕过。一般来说，尽可能使用可信的第三方库，例如 PEAR::Auth[2] 和 PEAR::LiveUser[3]。此外，研究 Web 测试框架，例如 SimpleTest[4]，它们能够从 Web 浏览器的角度测试你的网站。

- [2] http://pear.php.net/package/Auth
- [3] http://pear.php.net/package/LiveUser
- [4] http://www.lastcraft.com/simple_test.php

## 会话和 Cookie 漏洞

注意防范会话劫持的可能性。在确实需要安全身份验证的网站上（例如电子商务网站），使用 SSL 向浏览器提供网站，以确保通信加密且没有人窃听。如果你通过 URL 传递会话 ID（就像 WML 基础的网站所做的那样），请确保不要将会话 ID 放在指向远程站点的 URL 中。此外，当将访问者转发到远程站点时，请通过一个中间脚本转发，该脚本会去除任何包含会话 ID 的可能 HTTP 来源页信息。一般来说，使用 Cookie 处理会话更好。

如果你使用基于 Cookie 的自有身份验证，只在 Cookie 中存储标识性会话 ID，而不是用户名和密码。

## 跨站脚本 (XSS)

攻击者可以利用你网站提供的合法机制在你的网站上发布内容，例如 JavaScript，导致其他用户泄露他们的会话 ID，从而让攻击者劫持他们的会话。较不严重但同样尴尬的是，仅仅是发布会“打乱”你页面布局的 HTML，例如过早关闭 `table` 标签。

采用“全部拒绝，少量允许”的方法，或者更好的做是，使用单独的标记语言，例如 BBCode（参见第 5 章），同时使用 PHP 函数（如 `strip_tags` 和 `htmlentities`）消除 HTML。如果你确实想允许发布 HTML，请考虑构建基于 PEAR::XML_HTMLSax[5] 的过滤器（参见卷 II，第 2 章）。

- [5] http://pear.php.net/package/XML_HTMLSax

## 命令注入

当攻击者能够影响 PHP 与外部系统（例如文件系统或数据库）交互的方式时，就会发生命令注入。SQL 注入是一个典型的例子，当攻击者使用表单或 URL 来修改数据库查询时，就会发生 SQL 注入。此事在第 3 章中有详细讨论。简而言之，在将用户提供的数据用于查询之前，对其进行转义。

## 错误处理

经验丰富的攻击者能够从你的错误消息中获取关于你系统的大量重要信息。虽然这属于“通过隐瞒实现安全”（它无法替代*真正*安全的应用程序），但对于正式运行的网站，最好指示 PHP 将错误消息记录到文件中，而不是将其显示在浏览器上。详情请参见附录 A。

## 不安全的加密使用

首先，谈到密码学时，不要自己实现。其次，请记住，如果某种算法旨在被解码，那么除你之外的其他人也能够解码它。请记住，严格来说，MD5 不是加密算法（即你无法解密 MD5 字符串以获取原始数据）；它是消息摘要算法。但是，如果你不需要解密某个值，则可以使用 MD5，它可以通过 PHP 的 md5 函数使用。这样可以让你比较两段数据的加密版本（例如存储的密码和用户输入的密码），从而避免处理可能被攻击者解密的加密值所带来的风险。

## 管理缺陷

允许攻击者获得与你相同的网站访问权限，显然是不好的消息。分别使用 SCP/SFTP 和 SSH 来代替 FTP 和 telnet。Linux 发行版通常预安装所需的客户端工具。对于 Windows，请查看用于 SSH 访问的 putty[6] 和用于 SCP/SFTP 的 WinSCP[7]。FTP 和 telnet 会将你的密码暴露给网络嗅探器。确保你的主机提供的任何 Web 管理工具仅通过 SSL 连接使用。如果你使用第三方软件（例如 phpBB），请立即更改默认管理员密码，并及时了解潜在安全缺陷。

## 配置与补丁

安装 PHP 时，配置文件 php.ini-recommended 是确保正确配置软件包的最佳起点。

如果你使用托管公司，它们应该为你处理大部分问题，例如在宣布漏洞时对软件进行打补丁。不过，最好还是自行保持更新，使用 Security Focus[8] 和 DMOZ[9] 上列出的其他网站等。

PHP Advisory[10] 上有更多信息，尽管遗憾的是，该网站已不再维护。

- [6] http://www.chiark.greenend.org.uk/~sgtatham/putty/
- [7] http://winscp.sourceforge.net/eng/
- [8] http://www.securityfocus.com/incidents/
- [9] http://dmoz.org/Computers/Security/Mailing_Lists/
- [10] http://www.phpadvisory.com/

# 附录 D：使用 PEAR

PEAR[1]（PHP 扩展与应用程序仓库）是 Stig Bakken 的心血，并受到 Perl 的 CPAN[2] 的启发。

作为一个项目，它最初构思于 1999 年，并于 2003 年 1 月发布了首个稳定版。它有两个目的。首先，它提供了一组用于解决常见“架构”问题的 PHP 类库，你在本书中已经见过其中的一些。其次，在“PECL”（PHP 扩展代码库）标题下，PEAR 为 PHP 扩展提供了一个仓库。PECL 最初旨在存储“非标准”扩展，这些扩展更多处于 PHP 的边缘，但此后它已发展为所有未包含在核心 PHP 发行版中的扩展的默认仓库。在这里，我将专注于 PEAR 提供的 PHP 类。

提交工作并维护 PEAR 仓库的人都是志愿者。最初是一个小型开发者社区，PEAR 首个稳定版的发布使其人数显著增长，并获得了整个 PHP 社区的更多关注。仍有大量工作要做，以将标准提升到 PHP 本身的水平。文档是一个关键领域，还有很大的改进空间。如果你遇到困难，一个不错的起点是 PHPKitchen 的 PEAR 教程列表[3]。话虽如此，PEAR 在减少开发 PHP 应用程序所需的工作量方面确实提供了显著价值。

但是，PEAR 对你实际上意味着什么？考虑到 PEAR::SOAP 的功能（已在卷 II，第 2 章中介绍），先尝试编写自己的 SOAP 实现，然后再编写使用它的“应用”代码，显然是浪费时间。浏览包列表[4]，你会发现 PEAR 提供了更多类，按包和主题分类，以帮助你避免重复造轮子。重要的是要理解，PEAR 类的重点是架构问题，而不是应用程序级类。换句话说，PEAR 不是 Hotscripts；你不会在那里找到完整的应用程序；相反，你会发现可以在多种不同应用程序中重用的代码。同样重要的是，与例如通过 SourceForge[5] 提供的项目（通常是个人项目）相比，PEAR 开发者社区会尽力维护和支持该库。

- [1] http://pear.php.net/
- [2] http://www.cpan.org/
- [3] http://www.phpkitchen.com/staticpages/index.php?page=2003041204203962
- [4] http://pear.php.net/packages.php
- [5] http://www.sourceforge.net/





一旦相关人员停止贡献时间，这些努力就会戛然而止。否则，该库在一定程度上强调保持标准化。例如，所有错误处理都应使用 PEAR::Error 进行，并且代码应使用 PHPDoc 标准进行文档编写，这意味着如果你无法在 PEAR 网站上找到文档，则应该能够使用 PHPDocumentor[6]（参见第 II 卷，第 6 章）提取 API 文档。

警告：与 Java 类库相比，PEAR 内各包之间的集成程度目前仍然较低。这意味着在某些情况下，你会面临是使用 PEAR::HTML_QuickForm 的验证功能，还是 PEAR::Validate，亦或两者都使用的抉择。投入一些时间提前研究哪个更符合你的开发风格是个好主意，而不是直接开始使用某个 PEAR 类作为应用程序的关键部分，后来才发现它并不是该问题的最佳选择。

需要明确的一个重要点是，提到“PEAR”实际上可能指两件事之一：整个仓库，或者 PEAR 前端（又称包管理器），它提供用于安装和升级你所使用的 PEAR 包的工具。

请注意，使用 PEAR 包管理器安装 PEAR 包并非强制要求。如果需要，你可以直接从 PEAR 网站下载它们，并手动解压到你的 PHP include 路径中。请务必检查网站上列出的依赖项（即其他所需的包），并且注意大多数包隐式需要 PEAR “base” 包[7] 来处理错误之类的任务。

## 安装 PEAR

如今，PEAR 的基础组件已随 PHP 发行版本身提供，但 Web 主机通常无法为客户提供默认的 PEAR 安装，因此了解如何从零开始进行此操作是值得的。该过程在基于 Unix 和 Windows 的系统之间可能略有不同。

第一步是确保你可以通过命令行运行 PHP 脚本。如果你输入 PHP 二进制文件的完整路径，这总是可行的。对于基于 Unix 的系统，你可以使用以下命令：

[6] http://www.phpdoc.org/
[7] http://pear.php.net/package/PEAR

```
/usr/local/bin/php /home/username/scripts/my_script.php
```

对于 Windows，你可以使用类似这样的命令：

```
c:\php\cli\php.exe c:\scripts\my_script.php
```

请注意，在上面的 Windows 路径中，我们使用了 PHP 安装目录下 c:\cli（命令行接口）子目录中的可执行文件，该可执行文件与 Apache 用于处理 Web 页面的可执行文件略有不同。自 4.3.0 以来，Windows 版 PHP 二进制发行版将 c:\cli 版本的 PHP 可执行文件放置在此目录中。

不过，通过对系统环境变量进行一些更改，可以使 PHP 从命令行使用变得更加容易。有关深入讨论，请参阅 PHPBuilder[9] 上的 Replacing Perl Scripts with PHP Scripts[8]。

接下来，在浏览器中访问 http://pear.php.net/go-pear，你会看到一个 PHP 脚本。此脚本用于安装 PEAR 包管理器——这是安装其他 PEAR 包所需的基础。将此文件下载到你的计算机上（文件，另存为）为 go-pear.php。至此，你有多种选择。

将 go-pear.php 存储在 Web 服务器文档根目录下的某个位置，将允许你将脚本作为 Web 页面运行。不过，此行为仍处于实验阶段，因此无法保证其能正确运行。如果你确实使用此方法，请确保脚本不对公众开放！

更好的做是通过命令行执行 go-pear.php 脚本，例如：

```
/usr/local/bin/php /home/username/pear/go-pear.php
```

或者，在 Windows 上：

```
c:\php\cli\php c:\pear\go-pear.php
```

这将启动一个交互式命令行界面，它会询问你希望如何安装 PEAR。请注意，“安装前缀”是 PEAR（以及你稍后安装的任何包）将被安装的目录，称为 $prefix，而 $php_dir 是 PHP 安装的路径（go-pear.php 将默认将 PEAR 相关文档放置在此路径中，除非你另有指定）。Windows 用户应注意，更改安装前缀会弹出一个 Windows“浏览”对话框，你可以通过该对话框指定所需目录。

[8] http://www.phpbuilder.com/columns/jayesh20021111.php3 [9] http://www.phpbuilder.com/

在将安装选项设置为符合你的要求后，go-pear.php 脚本将连接到 PEAR 网站，并下载设置包管理器所需的所有包（它还会询问你是否需要其他额外的包，这些包非常值得拥有）。包将安装在你指定为安装前缀的目录的 pear 子目录中（因此，在上面的示例中，你最终会得到 c:\pear\pear 或 /home/username/pear/pear）。

最后，如果你允许，go-pear.php 安装程序将尝试修改 php.ini 中的 include_path。如果要手动执行此操作，假设你使用了上面的目录，则需指定以下内容：

```
include_path = " .:/home/username/pear/pear"
```

对于 Windows 用户，路径如下：

```
include_path = ". ; c:\\pear\\pear"
```

最后，要从命令行使用 PEAR 包管理器，你需要设置一些环境变量。对于 Windows 用户，可以通过右键单击文件 PEAR_ENV.reg 并选择运行，将其自动添加到 Windows 注册表中。也可以通过 Windows 控制面板手动将其配置为环境变量。Unix 系统用户可以通过编辑主目录（/home/username）中的 .profile 文件，将其配置为每次登录时设置：

```
## Environment variables
export PHP_PEAR_SYSCONF_DIR=/home/username/pear
export PHP_PEAR_INSTALL_DIR=/home/username/pear/pear
export PHP_PEAR_DOC_DIR=/home/username/pear/pear/docs
export PHP_PEAR_BIN_DIR=/home/username/pear
export PHP_PEAR_DATA_DIR=/home/username/pear/pear/data
export PHP_PEAR_TEST_DIR=/home/username/pear/pear/tests
export PHP_PEAR_PHP_BIN=/usr/local/bin/php
```

最后，你需要将 PEAR 命令行脚本添加到系统路径中。在 Windows 上，可以通过系统控制面板应用程序（在高级选项卡上，单击环境变量），将 ;c:\pear 追加到 PATH 变量来实现。

在基于 Unix 的系统上，将以下内容添加到你的 .profile 脚本中：

```
export PATH=$PATH;/home/username/pear
```

完成所有这些后，你就可以继续使用包管理器的多种形态之一了。

## PEAR 包管理器

假设你已正确设置 PEAR，现在可以使用 PEAR 包管理器的命令行界面来安装包。例如，从命令行输入：

```
pear install HTML_Common
```

这将从 PEAR 网站安装 HTML_Common 包。命令行使用的包名称与网站上的相同。

PEAR 包管理器使用 XML_RPC 与 PEAR 网站通信。如果你处于代理服务器或防火墙后面，则需要使用以下命令告知 PEAR 代理服务器的域名：

```
pear config-set http_proxy proxy.your-isp.com
```

如果要在以后取消设置该变量，只需使用：

```
pear config-set http_proxy " "
```

现在要将 QuickForm 添加到已安装的 PEAR 包中，只需输入：

```
pear install HTML_QuickForm
```

如果安装 QuickForm 之后又发布了新版本，可以使用以下命令升级：

```
pear upgrade HTML_QuickForm
```

如果出于某种原因，你后来决定不再需要 QuickForm，可以使用以下命令将其删除：

```
pear uninstall HTML_QuickForm
```

要查看所有 PEAR 命令列表，只需输入 pear。

现在，如果你不喜欢命令行，还有一个（实验性的）基于 Web 的 PEAR 前端（以及一个 PHP-GTK 前端，但这超出了本讨论范围）。要使用它，你首先需要从命令行安装它



(请注意，如果您是通过 Web 服务器执行 go-pear.php 的，则也会为您安装 Web 前端)。键入以下命令：

```
pear install Net_UserAgent_Detect
pear install Pager
pear install HTML_Template_IT
pear install PEAR_Frontend_Web
```

请注意，前三个包是 PEAR_Frontend_Web 所必需的。完成后，您可以使用以下简单脚本从 Web 服务器启动前端：

```
<?php
// Optional if include path not set
### ini_set('include_path', 'c:\htdocs\PEAR');

require_once 'PEAR.php';

// For Windows users
### $pear_user_config = 'c:\windows\pear.ini';
// For Unix users
$pear_user_config = '/home/username/pear/PEAR/PEAR/pear.conf';

$useDHTML = TRUE; // Switch off for older browsers

require_once 'PEAR/WebInstaller.php';
?>
```

## 手动安装包

可以手动安装包（尽管这会增加工作量），但在操作时务必仔细检查包含路径。首先，创建一个目录，作为您安装的所有 PEAR 类的基础。此目录 *必须*位于您的包含路径中。接下来，安装主 PEAR 包[11]——下载最新的 *稳定* 版本并直接解压到您创建的目录，使 PEAR.php 位于该目录的根目录中。

安装更多包的方式大致相同，但您需要注意解压到哪个目录。例如，以 PEAR::DB 为例，主 DB.php 文件与 PEAR 类目录根目录中的 PEAR.php 文件并置，而其他 PEAR::DB 相关文件则位于子目录 DB 中。最佳检查方法是查看每个 PEAR 包随附的 package.xml 文件。该文件包含一个名为 `filelist` 的元素，列出了包中包含的所有文件及其应安装的位置。对于每个 `file`，请检查 `baseinstalldir` 属性（如果已指定），它会告诉您文件应放置的位置，该位置相对于根 PEAR 类目录。`name` 属性指定每个文件应放置的路径和文件名，该路径和文件名相对于 `baseinstalldir`（如果没有 `baseinstalldir` 属性，则仅相对于根 PEAR 类目录）。

- [11] http://pear.php.net/package/PEAR

## 索引

本索引涵盖 *PHP 选集* 的两个卷。另一卷中的页码引用前面带有卷号，并以斜体表示（例如 II-123 指第 II 卷第 123 页）。

### 符号

- $_FILES 数组，280
- $GLOBALS 数组，II-91
- $this 变量，31, 37, II-97
- %（通配符），95
- &（引用）运算符，42, 69, II-124
  - （另请参阅 引用）
- ->（箭头）运算符，32
- .=（字符串追加）运算符，II-309
- .forward 文件，248
- .htaccess 文件，16, 18, 20, 118, 128, 204, 311, 322, II-72, II-81, II-229
- :: 运算符，29
- =（赋值）运算符，II-309
- @（错误抑制）运算符，163, 322, 324
- @ 文档标记，II-285, II-293
- __clone 方法，48

### A

- 抽象类，60, II-84
- 验收测试，II-298
- 访问控制，II-1, II-13, II-21
  - （另请参阅 方法，访问控制）
  - （另请参阅 权限）
  - 安全问题，II-1, II-24
- 邻接表模型，288
- 聚合，56, 59
- 别名（另请参阅 SELECT 查询，别名）
- allow_call_time_pass_reference 指令，20, 47
- Alpha 混合，223
- 替代内容类型，II-169
- Apache，308, 310
- API 文档，II-xiii, II-283
  - 生成，II-291
  - 阅读，II-287
- 撇号
  - 转义（另请参阅 魔术引号）
  - 在 SQL 语句中（另请参阅 SQL 语句中的引号）
- 应用程序编程接口 (API)，25, 35, 78
- 应用程序编程接口 (APIs)
  - （另请参阅 API 文档）
- 应用程序，314
- 归档文件（另请参阅 压缩文件）
- 参数，5
- 数组指针，II-324
- 数组，256
  - 转换为字符串，151
  - 从字符串创建，150
  - 字符串作为，152
- ASP 标签 (<% %>)，18
- asp_tags 指令，18
- 身份验证（另请参阅 访问控制）
- 身份验证标头（另请参阅 HTTP 身份验证）
- 自动登录，II-232
- 自动注册
  - 防御，II-37
- auto_append_file 指令，204
- AUTO_INCREMENT 列，94
- auto_prepend_file 指令，203, 204, II-72, II-260
- 自动化测试（另请参阅 单元测试）
- AWSStats，II-225

### B

- 备份 MySQL 数据库，98
- BACKUP TABLE 查询，101, 102
- 不良语汇过滤器（另请参阅 屏蔽不良语汇）
- 条形图（另请参阅 图表，条形图）
- Base64 编码，II-6
- BBCode，153
- 二进制文件
  - 在 Windows 中读取，116
- 位运算符，321
- 黑盒测试，II-299
- 面包屑（另请参阅 面包屑导航）
- 缓冲查询（另请参阅 非缓冲查询）
- 缓冲（另请参阅 输出缓冲）
- bzip2，100

### C

- 缓存，202, 293, II-156, II-175, II-241
  - （另请参阅 模板缓存）
  - 分块，II-248, II-255
  - 客户端，II-242, II-262
  - 下载，II-244
  - 函数调用，II-260
  - 防止，II-243
  - 安全问题，II-256
  - 服务器端，II-242, II-247, II-254
  - Web 服务，II-260
- 日历，190
  - 每日日程，198
  - 月份天数，195
  - 一年中的月份，194
- 调用时按引用传递，20, 47
- 回调函数，326, II-87, II-90, II-93
- 级联构造函数，52
- 屏蔽不良语汇，157
- 图表（另请参阅 图表）
- CHECK TABLE 查询，103
- 子类，48
- 分块缓冲（另请参阅 输出缓冲，分块）
- 类声明，28
- 类作用域（另请参阅 作用域）
- 类，25, 26, 29, 154
  - （另请参阅 类中的输出）
- 点击路径分析，II-223, II-225, II-238
- 代码存档，xii, II-iv
- 代码优化
  - 惰性包含，II-275
  - 引号，II-276
  - 引用，II-276
  - SQL 查询，II-275
- 集合，II-323
- 组合，58, 59, II-158
- 压缩文件
  - （另请参阅 PEAR，PEAR::Archive_Tar）
  - 创建，138
  - 解压，139
- 具体类，60
- 条件 GET，II-264
- 配置信息
  - 存储方法，17
  - 存储在文件中，127
- 常量，II-13, II-228
- 构造函数，31
  - 在 PHP 中不级联，52
- 上下文菜单，292, 297
- Cookie，II-8, II-214, II-232
  - 与会话对比，II-232
- 损坏的数据库（另请参阅 修复损坏的 MySQL 数据库）
- COUNT（另请参阅 MySQL 函数，COUNT）
- cron，205, 206
  - （另请参阅 crontab）
  - （另请参阅 伪 cron）
- crontab，101
- 跨站脚本 (XSS) 攻击，148, 163, II-10
- 面包屑导航，53, 288, 293
- 自定义错误处理程序（另请参阅 错误，处理）
- 自定义错误页面，333
- 自定义会话处理程序，II-10
- 自定义标签（另请参阅 BBCode）
- 文档标记（另请参阅 @ 文档标记）
- DocBlocks，II-294
- 文档对象模型 (DOM)，II-80, II-102, II-110, II-112, II-114
  - （另请参阅 XPath）
- DOM（另请参阅 文档对象模型 (DOM)）
- DOM 检查器，II-79
- 下载（另请参阅 文件，下载）
- 下拉菜单，299

## D

- 数据访问对象 (DAO)，104
- 数据库索引，96
- 数据库持久层（另请参阅 持久层）
- 数据库，65, 216
  - （另请参阅 MySQL）
  - 备份（另请参阅 备份 MySQL 数据库）
  - 存储日期，172
  - 日期
    - 星期，182
    - 一年中的天数，186
    - 月份天数，183
    - 月份第一天，187
    - 闰年，185
    - 数字后缀，188
    - 在 MySQL 中存储，172
    - 一年中的周数，183
  - 日期和时间
    - 在 HTTP 中，II-264
- DELETE 查询
  - 计算受影响的行数，93
- 派生数据，II-226
- 设计模式，21, II-xiii, II-311
  - 适配器模式，II-190, II-342
  - 工厂方法，II-313
  - 迭代器模式，II-323, II-333
    - （另请参阅 迭代器）
  - 观察者模式，II-25, II-347
  - 策略模式，II-334
- 开发技术，II-xiii
- 目录
  - 读取，123
- 调度映射，II-160

## E

- echo 语句，II-201, II-245, II-246
- Eclipse PHP 库，II-290, II-334
- ECMAScript（另请参阅 JavaScript）
- 电子邮件，237, II-29
  - 附件，239
  - 复杂消息，238
  - 嵌入图像，240, 243
  - HTML，243
  - 邮件列表，251
  - 多部分，245
  - 多个收件人，245
  - PHP 设置，237
  - 接收，247
- 电子邮件地址
  - 临时，II-25
- 封装，II-286
- 加密，275, II-46, II-51
  - （另请参阅 MD5 摘要）
- enctype 属性，280
- 企业应用架构，21
- 实体引用（另请参阅 XML 实体引用）
- 环境错误，10, 319
- 错误报告级别，321, 322
  - （另请参阅 错误，级别）
- error_reporting 指令，321, 322
  - （另请参阅 错误报告级别）
- 错误，320, 324, 325
  - （另请参阅 环境错误）





(参见 逻辑错误)
(参见 语义错误)
(参见 语法错误)
显示, 333
生成, 324, 325
处理, 11, 320, 326, 329, 331, II-31, II-139
在 PHP 5 中, 320
级别, 320, 324
(参见 通知)
(参见 警告)
日志记录, 331
抑制, 322
(参见 @ (错误抑制运算符))
类型, 8, 319
转义字符, 19, 84
(参见 魔术引号)
事件处理程序, II-80, II-87
异常处理, 331
(参见 try-catch 语句)
执行时间限制, 132, II-195
(参见 PHP 函数, set_time_limit)
exit 语句, II-20
extends 关键字, 49
可扩展标记语言 (参见 XML)
扩展 (参见 PHP 扩展)
极限编程, 11, II-298
eXtremePHP, II-334

## F

- 致命错误 (参见 错误)
- 字段 (参见 成员变量)
- 文件句柄, 116
- 文件指针 (参见 文件句柄)
- 文件传输协议 (FTP), 131
  - (参见 PEAR, PEAR::NET_FTP)
  - 安全问题, 131
- 文件, 111
  - (参见 压缩文件)
  - (参见 目录)
  - 远程访问, 129, 130
  - 追加, 119
  - 作为数据库替代, 118
  - 下载, 135
  - 缓存问题, II-244
  - 安全问题, 136
  - 获取信息, 121
  - 权限, 120, II-10
  - 安全问题, 120
  - 读取, 112, 116, 117
  - 安全问题, 111
  - 传输 (参见 文件传输协议 (FTP))
  - 上传, 280
    - (参见 最大上传大小)
    - 显示, 286
    - 安全问题, 283
    - 与 QuickForm, 283
  - 写入, 119
- 文件夹 (参见 目录)
- 字体
  - .afm, II-175
  - 在 PDF 文档中, II-175
  - 在动态图像中使用, 224, II-41
- for 语句, 263, II-274
- ForceType 指令, 310
- foreach 语句, 10, 107, 247, II-88, II-125, II-129, II-324
- 忘记的密码 (参见 密码，检索)
- 表单字段值, 145
  - 转义 (参见 特殊字符)
- 格式化输出值, 152
- 表单, 268
  - 使用 QuickForm 生成, 269
  - 指南, 269
  - 安全问题, 269
  - 验证 (参见 验证提交的数据)

- FPDF, II-170, II-190
- FTP (参见 文件传输协议 (FTP))
- FULLTEXT 搜索, 96, II-280
- 函数参考, 4
- 函数作用域 (参见 作用域)
- 函数
  - (参见 参数)
  - (参见 PHP 函数)
  - (参见 返回值)
  - 签名, 5, II-286

## G

- GD 图像库, 209, 225
- GET (参见 HTTP 请求方法)
- GIF 文件
  - 专利问题, 210
- global 关键字, 275
- 全局作用域 (参见 作用域)
- 全局变量 (参见 超全局变量)
- 图表, 225
  - 柱状图, 226
  - 饼图, 228
- 灰盒测试, II-299
- 组 (参见 用户组)
- gzip, 100
- GZIP 文件 (参见 压缩文件)

## H

- HAWHAW, II-208, II-289
- HDML, II-208
- heredoc 语法, 27
- 层次数据, 288, 289
- 层次菜单 (参见 树形菜单)
- HTML
  - 转换为 PDF, II-177
  - 在电子邮件中 (参见 电子邮件, HTML)
  - 解析, II-81, II-177
- HTML 标签
  - 用 BBCode 替换, 153
  - 从文本中剔除, 147, 163
- HTML2FO, II-200
- HTTP 身份验证, II-3, II-5, II-6
- HTTP 头, 135, 288, II-175, II-215, II-242, II-243, II-262
  - 与输出缓冲, II-246
  - 授权, II-6
  - 缓存控制, II-243, II-263
  - 内容处置, 136, II-244
  - 内容长度, 136
  - 内容类型, 136, 210, 217, II-120, II-201
  - ETag, II-263
  - 过期, II-243, II-263, II-264
  - 如果自从修改以来, II-263, II-264, II-266
  - 最后修改, II-175, II-244, II-263, II-264, II-266
  - 位置, II-20, II-234
  - Pragma, II-243
  - 来源页面, II-10
  - 何时发送, II-7
  - WWW-Authenticate, II-5
- HTTP 请求头, II-4
- HTTP 请求方法, 268, II-163
- HTTP 响应头, II-4, II-9
- httpd.conf, 312
- 超链接 URL
  - URL 编码, 143

## I

- if-else 语句, 9, 68, 277, II-132, II-148, II-195, II-271, II-282, II-334
- ignore_repeated_errors 指令, 333, 333
- 图像
  - 获取尺寸, 212
  - 获取类型, 214
  - 叠加文本, 224, II-40
  - 基于调色板的, 213
  - 防止“热链接”, 230
  - 重采样, 213
  - 调整大小, 213
  - 按比例缩放, 214
  - 真彩色, 213
  - 水印, 223
- include, 12, 15, 69
  - (参见 require)
- 包含文件 (参见 包含)
- include_once, 12, 14
  - (参见 require_once)
- include_path 指令, 16, II-171
- 包含, 12, 15, 127
  - (参见 代码优化, 懒加载包含)
  - (参见 include_path 指令)
  - 跨目录, 15
- 入站邮件 (参见 电子邮件, 接收)
- 索引 (参见 数据库索引)
- 继承, 48, 52, 190, 264, II-84
  - 深层结构, 55
- ini 文件 (参见 配置信息, 存储在文件中)
- INSERT 查询, 80, 81, 96
  - 计算受影响的行数, 93
  - 检索新行 ID, 94
- 实例 (参见 实例化)
- 实例化, 30
- 接口, 60, II-353
  - (参见 应用程序编程接口 (API))
- IP 地址, II-24, II-224, II-232
- 迭代器, 296, II-98, II-108, II-183, II-323, II-338

## J

- JavaScript, II-10
  - 使用 JavaScript 进行表单验证, 269, 270, 271
  - 与 SVG 的交互, II-203
- JpGraph 库, 225

## L

- 语言过滤器 (参见 屏蔽脏话)
- 分层应用设计 (参见 N 层设计)
- 懒加载, II-69
- LIKE 运算符, 95
- LIMIT 子句, 89, 91, 259, II-280
- 换行符
  - 在 HTML 中保留, 146
- 链接标识符, 68
- 链接 URL (参见 URL 编码)
- LiveHttpHeaders, II-262
- 错误日志记录 (参见 错误, 日志记录)
- 逻辑错误, 11, 319
- 查找表, II-61

## M

- 魔术引号, 19, 84, 269, II-17, II-31
  - (参见 SQL 语句中的引号)
- magic_quotes_gpc 指令, 19, 84, 85, II-17
  - (参见 魔术引号)
- 邮件列表 (参见 电子邮件, 邮件列表)
- 最大上传大小, 280
- MD5 摘要, II-16
- 成员函数 (参见 方法)
- 成员变量, 31
  - 访问控制, II-286
- meta 标签, II-242, II-243
  - 过期, II-243
  - Pragma, II-243
  - 问题, II-243
- 方法, 28
  - (参见 静态方法)
  - 访问控制, II-286
  - 访问成员变量, 32
  - 调用其他方法, 37
  - 签名, II-286
- MIME (参见 多用途互联网邮件扩展 (MIME))
- MML, II-208
- 模拟对象, II-306
- mod_rewrite, 231, 312, 314
- Mozilla, II-79, II-215
- 多用途互联网邮件扩展 (MIME), 210
- MIME 类型, 211, 215, 216, 239, 284 (参见 application/vnd.mozilla.xul+xml)
  - image/bmp, 211
  - image/gif, 211
  - image/jpeg, 211
  - image/png, 211
  - image/xml+svg, 211
  - text/html, 211
- myisamchk, 103
- MySQL, 17, 24, 66, 66, 78, 290, II-2, II-254, II-279, II-343
  - (参见 非缓冲查询)
  - 备份 (参见 备份 MySQL 数据库)
  - 连接到, 67, 69
  - 显示数据, 255
  - 获取数据, 73, 75
  - 插入数据行, 80
  - 存储天, 172
  - 更新数据行, 80
- MySQL 列类型
  - DATE, 174
  - DATETIME, 174
  - TIME, 174
- MySQL 函数
  - COUNT, 90, 260
  - DATE_FORMAT, 178
  - UTC_TIMESTAMP, 178
- MySQL 手册, 103
- MySQL 时间戳, 174, 177
- mysqldump, 98, 100, 101
- 嵌套集, 288
- new 关键字, 33
- 新行 (参见 换行符)
- 通知, 321, 323, 324, 325
- 数字后缀, 188
- NuSOAP, II-157

## N

- N 层设计, II-xiii, II-200, II-277
- 命名空间 (参见 XML 命名空间)
- 导航系统, 288
- 嵌套缓冲 (参见 输出缓冲, 嵌套)

## O

- 面向对象编程, x, 21, 23, II-311
  - 基础, 26
- 面向对象编程
  - 性能问题, II-271
- 对象, 25, 29
  - 交互, 56
  - 优化代码, II-269
  - for 循环, II-274
  - 最可能者优先, II-271
- ORDER BY 子句, 256
- 输出缓冲, 333, II-245, II-247
  - 分块, II-248
  - (参见 缓存, 分块)
  - 嵌套, II-254
- 类中的输出, 33
- 重写, 50
  - 调用被重写的方法, 51

## P

- 抓包器, II-1
- 分页结果, 259
- 参数 (参见 参数)
- 父类, 49
  - 调用其方法, 51
- parent 关键字, 51
- 解析错误, 9
- 按引用传递, 42
  - (参见 引用)
- 按值传递, 42
- 密码
  - 更改, II-55
  - 生成, II-51

## Index

- 检索, II-46
- 暂停脚本执行, 247, II-24
- PDF (参见 可移植文档格式 (PDF))
- PEAR, ix, 16, 23, 253
  - (参见 phpOpenTracker)
  - Auth_HTTP, II-8
  - PEAR::Archive_Tar, 138
  - PEAR::Cache, II-261
  - PEAR::Cache_Lite, II-156, II-254, II-257, II-259, II-260, II-264
  - PEAR::DB, 89, 105, II-262, II-280, II-343
  - PEAR::DB_DataObject, 89, 104
  - PEAR::Error, 331
  - PEAR::File, 118, 119
  - PEAR::HTML_QuickForm, 241, 269, II-22, II-26, II-31, II-37, II-48, II-55, II-218
  - PEAR::HTML_Table, 201, 255
  - PEAR::HTML_TreeMenu, 304
  - PEAR::Image_GraphViz, II-238
  - PEAR::Log, 333
  - PEAR::Mail_Mime, 247, 249
  - PEAR::mailparse, 249
  - PEAR::NET_FTP, 133
  - PEAR::Pager_Sliding, 263
  - PEAR::PHPUnit, II-301
  - PEAR::SOAP, II-152, II-157, II-160
  - PEAR::Tree, 288
  - PEAR::Validate, 159, 163, 167
  - PEAR::XML_fo2pdf, II-200
  - PEAR::XML_HTMLSax, 149, II-81, II-177, II-187, II-191
  - PEAR::XML_SaxFilters, II-102
  - PEAR::XML_Tree, II-238
  - PEAR::DB, II-319
- 性能
  - 测量, 204
- 权限, II-61
  - (参见 文件, 权限)
- perror, 103
- 持久层, 89, 104, 104
- PHP
  - 语言特性, 4
  - 语言基础, 3
  - 邮件列表, 7
  - 相关网站, 7
  - 使用统计, 2
- PHP 类, 23, 154, II-342
- PHP 扩展, 4
  - ClibPDF, II-170
  - DOMXML, II-82, II-83, II-102, II-112
  - IMAP, 247
  - Java, II-200
  - Mailparse, 247
  - Msession, II-262, II-280
  - PDFLib, II-170
  - Xdebug, II-270, II-277
  - XML, II-82, II-87
  - XML-RPC, II-142
  - XSLT, II-82, II-135
- PHP 函数
  - mysql_num_fields, 90
- PHP 函数
  - addslashes, 85, 85, II-144
  - apache_request_headers, II-262
  - apache_response_headers, II-262
  - array_map, 19
  - base64_encode, II-235
  - checkdnsrr, 161
  - clearstatcache, 123
  - closedir, 123
  - count, II-274
  - date, 122, 176, 182, 185, 186, 188, 194, 202, 203, II-250, II-264
  - define, II-13
  - die 函数, 68
  - dir, 124, 220, II-83, II-331
  - domxml_new_doc, II-102
  - domxml_open_file, II-102
  - domxml_open_mem, II-102
  - each, II-273, II-325




- error_log, 331
- error_reporting, 321, II-102, II-171
- eval, II-153
- explode, 150
- fclose, 123
- feof, 117
- fgets, 117
- fgetss, 118
- file, 112, 117, II-87
- file_exists, 121
- file_get_contents, 113, 116, 117, 284
- fileatime, 122
- filemtime, 122
- filesize, 117, 121, 129
- flush, II-227
- fopen, 116, 119, 123, 130
- fread, 116, 117, 123
- fscanf, 118
- fsockopen, 130, II-87
- ftp_chdir, 133
- ftp_connect, 132
- ftp_login, 132
- ftp_nlist, 133
- ftp_pwd, 133
- get_magic_quotes_gpc, 19, 85
- getallheaders, II-262, II-266
- gethostbyaddr, II-223
- getimagesize, 212, 213, 233
- gmdate, II-264
- header, 211, 288, II-7, II-243, II-246
- highlight_file, 125
- highlight_string, 125
- htmlspecialchars, 145, 156, 269
- imagecolorallocate, 224
- imagecopy, 224
- imagecopyresampled, 213
- imagecopyresized, 213
- imagecreatefromjpeg, 212
- imagecreatetruecolor, 212, 213
- imagefontload, 224
- imagejpeg, 213, II-43
- imageloadfont, II-41
- imagestring, 224, II-41
- implode, 151
- ini_set, 16, II-72
- is_dir, 122
- is_file, 122
- is_readable, 122
- is_string, II-304
- is_uploaded_file, 283
- is_writable, 122
- mail, 237, 238, II-287
- md5, II-16, II-51, II-258
- microtime, 204
- mktime, 176, 176
- mysql_affected_rows, 93
- mysql_close, 68
- mysql_connect, 24, 68, 323
- mysql_error, 78
- mysql_escape_string, 85, II-17
- mysql_fetch_array, 24, 73, 74, 75
- mysql_fetch_object, 75
- mysql_insert_id, 94
- mysql_num_rows, 89, 93
- 与未缓冲查询一起, 75
- mysql_query, 24, 73, 74, 80, 86
- mysql_real_escape_string, 85
- mysql_result, 75
- mysql_select_db, 24, 68
- mysql_unbuffered_query, 75
- nl2br, 146
- ob_clean, II-250
- ob_end_clean, II-246, II-254
- ob_end_flush, II-246, II-248, II-254
- ob_get_contents, II-246, II-250
- ob_start, II-246, II-254
- opendir, 123
- parse_ini_file, 17, 107, 128
- preg_quote, 158
- print_r, 249, 281
- printf, 118, 152
- pspell_suggest, II-54
- putenv, 203
- 与 IIS 一起, 203
- rawurldecode, 144
- rawurlencode, 144
- readfile, 123
- readfile, 115, 117, II-227
- session_register, II-11
- session_start, II-7, II-9, II-11, II-246
- session_unregister, II-11
- setcookie, II-246
- set_error_handler, 326, 328
- set_time_limit, 132, 207, 247
- sleep, 247, II-24
- sprintf, 152
- str_replace, 150
- strip_tags, 118, 147, 153, 156, 163, 167, II-210
- stripslashes, 19, 84
- strpos, 5, 149
- strtotime, II-266
- substr, 149
- system, 98, 138
- time, 176, 202, 203
- trigger_error, 79, 320, 324, 325, II-97
- trim, 151
- urldecode, 144
- urlencode, 144
- 警告, 324
- wordwrap, 149
- xml_parse_into_struct, II-87, II-88
- xml_parser_create, II-87
- xml_parser_free, II-88
- xml_parser_set_option, II-87
- xml_set_character_data_handler, II-93
- xml_set_element_handler, II-93
- xml_set_object, II-97, II-101
- xslt_create, II-137
- xslt_errno, II-137
- xslt_error, II-137
- xslt_process, II-137
- PHP 许可证, 154
- PHP 手册, 2
- 搜索, 4
- 捷径, 5
- PHP 源代码
- 在线显示, 125
- 安全问题, 125
- php.ini, 3, 11, 16, 18, 20, 47, 84, 105, 125,128,203,204,205,226,237,280,321,322, II-72, II-81, II-82, II-260, II-270
- PHPDoc, II-284
- PHPDocumentor, 159
- phpDocumentor, II-293
- PHPMailer, 238, 243, 245, II-26, II-48, II-287
- phpOpenTracker, II-221, II-227, II-234, II-238
- API, II-231
- 安装, II-228
- 搜索引擎插件, II-236
- PHPSESSID 变量, II-214
- phpSniff, II-222
- PhpUnit, II-300
- 饼图 (参见 graphs, pie charts)
- PNG (参见 Portable Network Graphics (PNG))
- 点, II-172
- 多态, 35, 60, 63
- 可移植文档格式 (PDF), II-169
- 来自 HTML, II-177
- 生成, II-176, II-196
- 页面原点, II-173
- 渲染, II-169
- 可移植网络图形 (PNG), 210
- 可移植 PHP 代码, 16
- POST (参见 HTTP 请求方法)
- post_max_size 指令, 280
- PostgreSQL, 66, 78, II-343
- 打印语句, II-245
- 私有方法, 39
- 过程式编程, 23
- 处理指令 (参见 XML 处理指令)
- 代理服务器, II-224
- 伪 cron, 205
- (另见 cron)
- 公有方法, 39

## Q

- QuickForm (参见 PEAR, PEAR::HTML_QuickForm)
- 引号 (参见 代码优化, 引号)
- SQL 语句中的引号, 83, 84

## R

- R&OS PDF, II-170
- 原始数据, II-226
- RDF (参见 RSS)
- 领域, II-6
- 重定向, II-20
- (另见 HTTP 标头, location)
- 重构, 28
- 引用计数, 48
- 引用, 20, 39, 45, II-276
- (另见 调用时按引用传递)
- (另见 按引用传递)
- 使用它提高性能, 47
- 在 PHP 5 中, 48
- 从函数/方法返回, 46
- 到新对象, 46
- register_globals 指令, 18, II-11, II-18
- 注册用户 (参见 用户注册系统)
- 正则表达式, 153, 158, II-44, II-340
- REPAIR TABLE 查询, 103
- 修复损坏的 MySQL 数据库, 103
- require, 12
- (另见 include)
- require_once, 12, 14, 17, II-276, II-283
- (另见 include_once)
- 保留字符, 144
- 资源标识符, 74
- RESTORE TABLE 查询, 101
- 结果分页器 (参见 分页结果)
- 返回命令
- 在构造函数中, 31
- 返回值, 5
- 对于构造函数, 31
- 重用代码, 20, 23
- 富客户端, II-215
- RLIKE 运算符, 96
- 机器人 (参见 访问者统计, 排除搜索引擎)
- RSS, II-79, II-85, II-102
- 聚合, II-122
- 生成, II-114
- 验证, II-122
- RTFM, 2
- (另见 PHP 手册)

## S

- SAX (参见 简单 XML API (SAX))
- 可缩放矢量图形 (SVG), II-169, II-200
- 使用 PHP 渲染, II-205
- 作用域, 34
- 脚本执行时间 (参见 计时 PHP 脚本)
- 搜索引擎友好的 URL, 307
- 搜索引擎查询, II-236
- 在字符串中查找和替换文本, 149
- 搜索 MySQL 数据库, 95
- (另见 全文搜索)
- 安全套接层 (SSL), II-1
- 安全, 3
- SELECT 查询, 80
- 别名, 91, II-62
- 计算返回的行数, 89, 92
- 与 MySQL 一起, 90
- 与 PHP 一起, 89
- 优化, II-275
- 使用它搜索, 95
- 排序结果, 256
- 语义错误, 10, 319
- sendmail, 237
- 会话变量, II-45
- session.save_path 指令, II-10, II-72
- 会话, 231, II-8, II-11, II-12, II-55, II-154, II-214
- (另见 自定义会话处理程序)
- (另见 跟踪在线用户)
- 在多台服务器上, II-280
- 安全问题, II-9, II-57
- 存储在 MySQL 中, II-71, II-73
- 与 cookies 相比, II-232
- 短标签 (<? ?>)
- short_open_tag 指令, 18, 205, II-81
- SHOW TABLES 查询, 101
- 简单 XML API (SAX), 163, II-80, II-82, II-87, II-88, II-110, II-177
- 简单邮件传输协议 (SMTP), 237
- 简单对象访问协议 (参见 SOAP)
- SimpleTest, II-301
- 滑动页码, 263
- SMTP (参见 简单邮件传输协议 (SMTP))
- SOAP, II-iii, II-141, II-150, II-226
- (另见 WSDL)
- (另见 XML-RPC)
- 构建客户端, II-152, II-164
- 构建服务器, II-157
- 与 XML-RPC 相比, II-142
- 源代码 (参见 PHP 源代码)
- 特殊字符, 145, 145, 156
- (另见 保留字符)
- (另见 不安全字符)
- 爬虫 (参见 访问者统计, 排除搜索引擎)
- SQL 注入攻击, 275
- SQL 注入攻击, 19, 20, 81, 86, II-144
- 独立 PHP 脚本, 249
- 标准输入, 249
- 静态方法, 29, 159
- 统计 (参见 访问者统计)
- stdClass, II-100
- 字符串函数, 149
- (另见 PHP 函数)
- 字符串
- 转换为数组, 150
- 从数组创建, 151
- 视为数组, 152
- 修剪空白, 151
- 将格式化值写入, 152
- 结构化查询语言 (SQL), 73, II-134
- (另见 DELETE 查询)
- (另见 INSERT 查询)
- (另见 SQL 语句中的引号)
- (另见 SELECT 查询)
- (另见 UPDATE 查询)
- (另见 变量, 在 SQL 查询中)
- 自动生成, 104
- 从 XML 生成, II-138
- 使用它解决问题, 78
- 子类 (参见 子类)
- 父类 (参见 父类)
- 超全局变量, 18
- SVG (参见 可缩放矢量图形 (SVG))
- switch 语句, 88, 256, 327, II-58, II-60, II-89, II-130, II-322, II-334
- 语法错误, 9, 319
- 语法高亮 (参见 PHP 源代码, 在线显示)
- 系统集成测试, II-298




## T

- 表关系，66，94
- 表格
  - 交替行颜色，257
  - 使用 PHP 生成，255
- TAR 文件（参见压缩文件）
- 模板缓存，II-245
- 文本内容
  - 在 HTML 文档中，143
- 缩略图
  - 创建，211，214
- 时间限制（参见执行时间限制）
- 时区，202
- 时间戳，172
  - （另请参见 MySQL 时间戳）
  - （另请参见 Unix 时间戳）
- 计时 PHP 脚本，204
- 分词器扩展，9
- 标记，9
- 跟踪在线用户，II-73
- 树形菜单，289，301，303
- try-catch 语句，320

## U

- 非缓冲查询，74，89
- 统一建模语言 (UML)，26，38，57，59，63，190，II-84，II-318，II-322，II-340，II-351
  - 从其生成代码，II-293
- 单元测试，11，II-xiii，II-298，II-300
- Unix 时间戳，173，175，II-186
  - 生成，176
  - 在 MySQL 中存储，174
- 不安全字符，144
- UPDATE 查询，80，81
  - 计算受影响的行数，93
  - WHERE 子句的重要性，81
- upload_max_filesize 指令，280
- URL 编码，144
- URL 重写（参见 mod_rewrite）
- URLs（参见搜索引擎友好型 URL）
  - 设计，314
- 用户代理字符串，II-223
- 用户组，II-61
- 用户注册系统，II-25，II-37

## V

- 验证提交的数据，159，II-335
  - 使用 QuickForm，270，272，274
- var 命令，31
- 变量函数，62
- 变量，40
  - （另请参见按值传递）
  - （另请参见按引用传递）
  - 用于输出的格式化，152
  - 在 SQL 查询中，87
  - 不存在的，163
  - 会话变量，231
- 视图，315
- 访客统计
  - 排除搜索引擎，II-237
  - 退出链接，II-234
  - 收集，II-225
  - 记录，II-226
  - 报告，II-238
  - 回访访客，II-232
  - 搜索引擎查询，II-236

## W

- WAP（参见无线应用协议 (WAP)）
- 警告，320，324，325
- 水印，223
- Web bug，II-230
- Web 服务，II-xiii，II-79，II-141，II-150，II-202
  - 缓存，II-260
  - 使用，II-150
  - 部署，II-150
  - 安全问题，II-165
- Web 服务描述语言（参见 WSDL）
- Webalizer，II-238
- WHERE 子句，89，91，II-275
- while 语句，9，74，117，193，257，II-212，II-248，II-326，II-328
- 白盒测试，II-299
- 空白字符
  - 修剪，151
- 无线应用协议 (WAP)，II-205
- 无线标记语言 (WML)，II-135，II-169，II-205，II-279，II-289
  - （另请参见 HAWHAW）
  - 卡片，II-206
  - 生成，II-208
  - 使用 Opera 查看，II-205
- WML（参见无线标记语言 (WML)）
- 单词换行（参见文本换行）
- 文本换行，149
- WSDL，II-142，II-150，II-157，II-160
  - 编辑器，II-151

## X

- Xdebug（参见 PHP 扩展, Xdebug）
- XML，17，18，290，II-79，II-205，II-238
  - （另请参见 XPath）
  - （另请参见 XSLT）
  - 转换为 SQL，II-138
  - 生成，II-80，II-111，II-112
- XML 实体引用，II-93
- XML 命名空间，II-81，II-127
  - 默认命名空间，II-127
- XML 处理指令，18，II-81，II-93，II-201
- XML Schema，II-81，II-142
- XML 用户界面语言 (XUL)，II-169，II-215
- XML-RPC，II-xiii，II-141
  - （另请参见 SOAP）
  - 构建客户端，II-146
  - 构建服务器，II-142
  - 故障代码，II-144
  - 与 SOAP 的对比，II-142
- XP（参见极限编程）
- XPath，II-81，II-123，II-128，II-134，II-139
  - 谓词，II-136
- XQuery，II-134
- XSL 格式化对象 (XSL-FO)，II-200
- XSLT，II-79，II-135，II-138
  - 错误处理，II-139
- XSS（参见跨站点脚本 (XSS) 攻击）
- XUL（参见 XML 用户界面语言 (XUL)）

## Z

- ZIP 文件（参见压缩文件）

## 使用 PHP 高效办公...

'The PHP Anthology, Volume I: Foundations' 是常见 Web 开发问题的最佳实践解决方案汇编。它通过应用结构良好、面向对象的软件设计原则，致力于以最小的努力实现实际目标。

## 关于 Harry Fuecks

![](img/5b6cdf7cf4cf53e30b19e047895dc464_397_0.png)

Harry Fuecks 自 1994 年起一直在企业 IT 领域工作，并获得物理学学士学位。他于 1999 年在搭建一个小型内联网时首次接触 PHP。如今，他是企业外联网的首席开发人员，SitePoint 丰富 PHP 社区的活跃参与者，也是 phpPatterns.com 的推动者。

## 关于 SitePoint

![](img/5b6cdf7cf4cf53e30b19e047895dc464_397_1.png)

SitePoint 专注于为 Web 专业人士出版有趣、实用且易于理解的内容。访问 sitepoint.com 以获取我们的书籍、通讯、文章和社区论坛。

