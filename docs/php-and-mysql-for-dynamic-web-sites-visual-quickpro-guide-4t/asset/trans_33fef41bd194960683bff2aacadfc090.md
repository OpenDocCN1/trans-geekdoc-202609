
• 扩展并更新了安装和配置说明

• 移除了过时内容（例如旧版 PHP 中使用的内容或不再适用的内容）

• 每章末尾增加了“复习与深入”部分，包含复习问题和提示，引导您如何根据刚学的知识进一步拓展知识面

对于拥有前几版书籍的读者（谢谢，谢谢，谢谢！），我相信这些新特性也将使本书成为您案头或书架上必备的参考书。

#### 本书与我的其他著作对比

这是我的第四本 PHP 和/或 MySQL 书籍，按顺序依次为：

• *《PHP for the World Wide Web: Visual QuickStart Guide》（PHP 万维网开发：可视化快速入门指南）*

• *《PHP 5 Advanced for the World Wide Web: Visual QuickPro Guide》（PHP 5 万维网高级开发：可视化快速专业指南）*

• *《MySQL: Visual QuickStart Guide》（MySQL：可视化快速入门指南）*

希望这份履历能暗示我具备撰写本书的资格，但作为站在书店里的读者，您该如何决定哪本书适合您？当然，您非常欢迎大方购买全套，这将让我感激不尽，但是……

*《PHP for the World Wide Web: Visual QuickStart Guide》* 是一本非常面向初学者的 PHP 指南。本书与它有部分重叠，主要集中在前三章，但使用了新示例以避免冗余。对于新手，本书可作为那本书的后续进阶读物。那本高级指南实际上是本书的续集，因为它假设读者已具备相当的知识基础，并建立在本书所教授的许多概念之上。MySQL 那本书几乎完全专注于 MySQL（只有两章涉及 PHP）。

考虑到这一点，请阅读“本书适合您吗？”部分，看看要求是否符合您的情况。如果您完全没有编程经验，并希望更循序渐进地学习 PHP，我的第一本书会更合适。如果您已经非常熟练掌握 PHP 并想学习其更多高级功能，请选择第二本。如果您主要对 MySQL 感兴趣，且不关心学习太多 PHP 知识，请看第三本。

也就是说，如果您想学习今天使用 PHP 和 MySQL 开发动态网站所需的一切知识，那么本书就是为您准备的！它参考了两项技术的最新版本，使用了其他书籍中未曾讨论的技巧，并包含独家示例。

无论您选择哪本书，请确保购买最新版本，或者至少选择与您将要使用的技术版本最匹配的版本。

### 配套网站

我专门为本书开发了一个配套网站，您可以访问 **[www.LarryUllman.com](http://www.LarryUllman.com)**。在那里，您将找到本书中的每一个脚本、一个包含冗长 SQL 命令的文本文件，以及出版过程中出现的勘误表。（如果您在命令或脚本上遇到问题，且完全按照书中操作，请查阅勘误表，确认不是印刷错误，以免让自己抓狂。）在该网站上，您还将找到有用的网络链接、一个读者可以互相提问和解答的热门论坛（我亲自解答许多问题），以及更多内容！

#### 问题、意见或建议？

如果您有任何关于 PHP 或 MySQL 的问题，可以求助于现有的众多网站、邮件列表、新闻组和 FAQ 资源库。快速在线搜索将获得几乎无限的资源。话虽如此，如果您需要即时答案，这些来源或快速网络搜索肯定能满足您的需求（极有可能其他人已经遇到并解决了您的同款问题）。

您也可以直接向我提出问题、意见和建议。使用本书对应的论坛能获得最快回复（我总是优先回答那些问题）。如果您更倾向于发邮件，我的联系方式在网站上提供。我会尽量回复收到的每一封邮件，但无法保证快速回复。

***

**出版商提示：查看作者 Larry Ullman 的配套视频培训！**

Visual QuickStart Guides 现在更加直观：基于畅销书 Visual QuickStart Guides 的成功，Peachpit 现推出 Video QuickStarts。作为本书的配套资料，Peachpit 提供了一小时以上的短小、任务导向的视频，帮助您掌握关键特性和技巧；您不必只是阅读如何编写 PHP 和 MySQL 脚本，而是可以亲眼看到它们的运行过程。这是学习所有基础知识以及一些较新或更复杂语言特性的绝佳方式。登录 Peachpit 网站 [www.peachpit.com/register](http://www.peachpit.com/register) 注册您的书籍，即可找到免费的流媒体试看样片；购买其余内容快速简便。

***

## 1. PHP 简介

本章内容

[基本语法](#ch01.html#ch01lev1sec1) [2](#ch01.html#ch01lev1sec1)

[向 Web 浏览器发送数据](#ch01.html#ch01lev1sec2) [6](#ch01.html#ch01lev1sec2)

[编写注释](#ch01.html#ch01lev1sec3) [10](#ch01.html#ch01lev1sec3)

[什么是变量？](#ch01.html#ch01lev1sec4) [14](#ch01.html#ch01lev1sec4)

[字符串简介](#ch01.html#ch01lev1sec5) [18](#ch01.html#ch01lev1sec5)

[字符串拼接](#ch01.html#ch01lev1sec6) [21](#ch01.html#ch01lev1sec6)

[数字简介](#ch01.html#ch01lev1sec7) [23](#ch01.html#ch01lev1sec7)

[常量简介](#ch01.html#ch01lev1sec8) [26](#ch01.html#ch01lev1sec8)

[单引号与双引号](#ch01.html#ch01lev1sec9) [29](#ch01.html#ch01lev1sec9)

[基本调试步骤](#ch01.html#ch01lev1sec10) [33](#ch01.html#ch01lev1sec10)

[复习与深入](#ch01.html#ch01lev1sec11) [34](#ch01.html#ch01lev1sec11)

虽然本书侧重于 MySQL 和 PHP 的结合使用，但您绝大部分的基础工作将仅使用 PHP 完成。在本章和下一章中，您将学习其基础知识，从语法到变量、运算符和语言结构（条件判断、循环等）。在掌握这些基础知识的同时，您也将开始编写可用的代码，稍后将在本书中将其集成到更大的应用程序中。

本介绍性章节将带您快速浏览 PHP 语言的大部分基础知识。您将学习 PHP 编码语法、如何向 Web 浏览器发送数据，以及如何使用两种变量（字符串和数字）加上常量。有些示例可能看似微不足道，但它们将演示您必须掌握的思想，以便日后编写更高级的脚本。本章最后提供了一些快速调试技巧……您懂的……以防万一！

### 基本语法

正如本书导言所述，PHP 是一种 *HTML-embedded*（HTML 嵌入式）脚本语言，这意味着您可以在同一个文件中混合编写 PHP 和 HTML 代码。因此，要开始 PHP 编程，请从一个简单的网页入手。**[脚本 1.1](#ch01.html#ch01ex01)** 是一个无花哨、无内容的 XHTML Transitional 文档示例，将作为本书中大多数网页的基础（本书不正式讨论 [X]HTML；更多信息请参阅专门资源）。请注意，该模板使用 UTF-8 编码，此主题将在侧边栏讨论。

要向页面添加 PHP 代码，请将其放在 PHP 标签内：

```
<?php  

?>
```

**脚本 1.1.** 一个基本的 XHTML 1.0 Transitional 网页。

***

```
1   <!DOCTYPE html PUBLIC "-//W3C//DTD XHTML  
      1.0 Transitional//EN" "http://www.w3.org/  
      TR/xhtml1/DTD/xhtml1-transitional.dtd">  
2   <html xmlns="http://www.w3.org/1999/  
      xhtml" xml:lang="en" lang="en">  
3   <head>  
4       <meta http-equiv="Content-Type"  
          content="text/html; charset=utf-8" />  
5       <title>Page Title</title>  
6   </head>  
7   <body>  
8       <!-- Script 1.1 - template.html -->  
9   </body>  
10  </html>
```

***

### 理解编码
