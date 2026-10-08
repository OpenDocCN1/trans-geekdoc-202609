# PHP 网络爬虫实用指南

- **作者**: Matthew Turland
- **出版方**: Marco Tabini & Associates, Inc.
  28 Bombay Ave.
  Toronto, ON M3H 1B7
  加拿大

  (416) 630-6202 / (877) 630-6202
  info@phparch.com / www.phparch.com
- **出版人**: Marco Tabini
- **技术审稿人**: Luke Giuliani
- **排版与设计**: Arbi Arzoumani
- **编辑**: Beth Tucker Long
- **财务与资源管理**: Emanuela Corso
- **封面图片**: Vladimir Fofanov



# 致谢

我知道这部分可能不是你们购买本书的主要原因，但我还是鼓励你们继续读下去。我在大学期间学到的一件事是，即使我无法记住所有教给我的知识，但对这些知识拥有哪怕模糊的意识，也能拓宽并改善我的视角。我认为，在阅读某位作者写的书时，更多地了解这位作者也是同理，尤其是那些在其生活和完成作品过程中给予支持的人。这里提到的人都是好人，他们值得被铭记。

## 惠特尼

我花了无数个夜晚和周末来写这本书。那几个月简直是个时间黑洞。这也是我自我提升、展示能力以及分享我所拥有之物的个人追求的一部分。我无法想象对于配偶来说，理解并支持我坚持这么久直到完稿是一件多么不容易的事，而我的妻子做到了。对此，我找不到足够的言语来描述，更别提回报，所以我不会尝试。我只想说，希望你们喜欢这本书，因为如果没有她，这本书将不会存在。

## MTA

在我真正开始着手写书之前，我曾尝试向几家大型技术出版商推介这个书稿概要，但没有成功。不过，最终结果反而是更好的，因为 PHP 社区正是我的目标读者。事后看来，为了达到这一目的，我不认为我能找到比 php|architect 更好的出版商了。当时，我在 php|architect 杂志上仅有一篇关于该主题的文章出自我的手笔。Liz 审阅了提案并将其推介给 Marco，最终由 Marco 做出了接受的决定，而 Beth 则在初稿完成后进行了审阅。每个人都在确保本书成为一部打磨精良的出版作品方面发挥了作用，即使书已经付梓很久之后，我依然会感激他们的付出。

## 卢克

我没能找到比卢克·朱利亚尼（Luke Giuliani）更好的技术编辑了。他有一种细致入微和超凡的注重细节的习惯，有时甚至超越了我自己，但大多数时候，这是我们共同拥有的令人愉快的特质。即使我陷入困境，他也总能提供动力和鼓励。他的建议不仅包括与书籍内容相关的更正和建议，还包括关于组织和呈现方式的指导，以最大化清晰度。如果没有卢克的参与，我严重怀疑我的书不会像你们眼前看到的这个版本如此精良。我欠他很多。

## 本

本是一个令我极度尊敬的人。他愿意表达他的观点，包括开发和遵守 Web 标准的重要性。我们从 HTTP 协议到罗伊·菲尔丁（Roy Fielding）关于 REST 的论文解读的讨论，都令我着迷并深受启发。当这本书完稿的曙光在隧道尽头显现时，我开始考虑如果由一位拥有他这般专业知识的人为本书撰写前言，将会为它带来多大的价值。当我就此事联系他并询问他是否愿意担此重任时，他愉快地接受了。尽管完成项目本身感觉美好，但他对其价值的评价让这场胜利变得更加甜蜜。

## 朋友们

“朋友”一词并非我轻率使用的。长久以来，我一直认为家人不是由血缘决定的，而是由人们如何对待彼此决定的，我对朋友也持同样的看法。在 PHP 社区中，有一群特殊的人，我将这个称号赋予他们。他们人数众多，无法一一列举，但其中每一位都在我需要的时刻提供过批评、建议或精神支持。我想他们都清楚自己是谁。无论他们如何看待自己付出的大小，我希望他们知道其重要性以及我对它的感激之情。

## 你们

虽然写一本书可能需要更长的时间，但花时间读书也是个人投资。这本书经历了一段漫长的发展旅程才到达你们手中。你们是它的读者。我感激你们花费时间阅读这本书，并希望它能证明这段时间是值得的。无论你们读完后的看法如何，我都鼓励你们写一篇书评，在你喜欢的社交网站上讨论它，或者发送电子邮件至 me@matthewturland.com 告诉我你们的想法。

# 前言

网络爬虫是 Web 的未来。当马修第一次找到我，邀请我为这本书写前言时，我并不相信这一点。事实上，我当时持有截然相反的观点。网络爬虫？那不是一个老话题吗——我们曾经在 Web 开发早期做过的事情？我为什么要读关于网络爬虫的内容？这难道不道德吗？

你们可能也在问自己同样的问题。

于是，我开始思考——思考网络爬虫究竟是什么——我考虑得越多，它就越让我想起蒂姆·伯纳斯·李（Tim Berners-Lee）关于链接数据之 Web 的愿景，关于语义数据，它们相互连接并向所有人开放以共享和使用。网络爬虫难道不就是一种从一个来源获取数据并解析以用于自己应用程序的行为吗？这难道不是语义 Web 的目标吗？

当 Web 刚刚起步时，它的目的是共享数据。教育和研究社区利用 Web 来展示数据，并通过超链接将这些数据与其他数据联系起来。由于在早期，XML、网络服务和数据馈送（data feeds）（甚至更少）尚不存在，编写脚本从其他网站获取数据、解析接收到的 HTML、以某种方式处理数据，然后将其显示在自己的网站上，已成为一种常见做法。

我最早接触网络爬虫的经历是在 1998 年，当时我想在一个网站上显示最新的新闻标题。当时，某个特定的新闻网站（名字不便透露）为其客户提供新闻标题的 HTML 代码片段，以便嵌入他们的网站。然而，我并非客户，但我找到了一种方法来抓取原始 HTML，解析它，并将其显示在我的网站上。无论这种行为多么不道德——我绝不提倡这种行为——我参与的行为后来被发现被称为“网络爬虫”。





如今，市面上有许多服务提供新闻源，也有大量的代码库可以解析这些数据。那么，随着网络服务和公共 API 的普及，为什么网络抓取对 Web 的未来仍然如此重要？这很重要，原因在于微格式、语义网技术、W3C 链接开放数据社区项目以及开放数据运动的兴起。就在今年，蒂姆·伯纳斯-李在 TED 大会上谈到了链接数据，他说：“我们要数据。我们要未加修饰的数据。我们现在必须索取原始数据。”

Web 的未来在于提供和访问原始数据。我们如何访问这些原始数据？通过网络抓取。

是的，在决定网络抓取是否是你想要采用的技术时，需要考虑法律层面的问题，但本书描述的技术对于访问和解析 Web 上任何类型的原始数据都非常有用，无论这些数据来自 Web 服务 API、XML 源、嵌入在网页中的 RDF 数据、HTML 中的微格式，还是普通的 HTML 本身。

没有办法回避这一点。要成为一名成功的 Web 程序员，你必须掌握这些技术。让它们成为你工具箱的一部分。让它们指导你的软件设计决策。我鼓励你带我们进入 Web 的未来。在法律范围内抓取 Web，发布你的原始数据供公众使用，并立即索取原始数据！

Ben Ramsey

美国佐治亚州亚特兰大

2009 年 6 月 28 日

## 第 1 章

### 简介

如果你想知道这本书是关于什么的，或者你是否属于其目标读者群体，那么这一章就是为你准备的。它将提供关于后续章节内容的背景信息，并解决一些相关的常见顾虑，这些问题可能对你很切题。如果你对网络抓取已经有了一个很好的高层概念，并希望直接跳入本书更技术性的内容，你可以安全地跳到下一章。

### 目标读者

本书面向中级或高级开发人员，要求读者已经对使用 PHP 5 进行编程有相当程度的熟悉感。你应该熟悉面向对象编程原则，如继承、抽象和封装，以及这些原则如何与 PHP 5 对象模型相关联。本书将详细介绍一般概念，并使用 PHP 作为（一种非常有限的）手段，通过实际示例来说明这些概念。对 HTTP 协议、XML 概念和相关 PHP 扩展库或 JavaScript 的了解也将特别有帮助。

### 如何阅读本书

如果你遇到一个不熟悉的 PHP 函数，请尝试将你的首选 Web 浏览器指向 `http://php.net/functionname`，其中 `functionname` 是相关函数的名称。这通常会将你引导至该函数在手册中的条目，或包含该函数条目的手册部分的着陆页。

除此之外，各章节可以独立阅读，但它们之间存在相互关联，因此从头到尾阅读全书有助于形成更完整的理解。

### 网络抓取的定义

网络抓取是一个过程，涉及从互联网检索半结构化文档（通常是 HTML 或 XHTML 等标记语言的网页），并分析该文档以提取特定数据，以便在其他上下文中使用。它通常（尽管不完全准确）也被称为屏幕抓取。网络抓取在技术上不属于数据挖掘领域，因为后者暗示尝试从已获得的大型数据集中识别语义模式或趋势。网络抓取应用程序（也称为智能、自动或自主代理）仅关注通过检索和提取获取数据本身，涉及的数据集大小可以差异很大。

你可能会对自己说，网络抓取听起来很像充当 Web 服务的客户端。区别在于文档的目标受众，进而由之决定的文档格式和结构。Web 服务由于其既定目的，本质上受限于生成有效标记的要求，以保持其有用性。它们必须保持一致的标准格式，以便机器能够解析其输出。

另一方面，Web 浏览器在处理文档的视觉渲染时，即使其标记无效，通常也更具宽容性。此外，Web 浏览器旨在供人类使用，它们消费信息的方式并不总是与机器在使用等效 Web 服务时消费信息的方式平行。这在某些情况下会使网络抓取应用程序的开发变得困难。就像 Web 服务生成有效标记的义务一样，Web 浏览器也有某些责任。这些包括尊重服务器请求以不索引某些页面，以及将发送给服务器的请求数量保持在合理范围内。

简而言之，网络抓取是 Web 浏览器功能的一个子集，用于以一种适合数据使用方式获取和渲染数据。

### 网络抓取的应用

虽然网站使用 Web 服务公开其数据变得越来越普遍，但缺乏针对机器定制的数据源（该数据源提供对应网站的所有数据）仍然是一种常见情况。在这种情况下，网站本身必须有效地成为你的数据源，而网络抓取可以被用来自动化消费其提供的数据。此外，Web 服务还用于将信息传输到外部数据系统。在没有它们的情况下，网络抓取也可以用于与那些不提供 Web 服务但为其用户提供基于 Web 接口的系统集成。

网络抓取的另一个应用可能更为知名，即开发名为爬取器（crawlers）的自动代理，它们寻找用于存储和分析的资源，这些资源最终将构成提供给你的搜索结果。在互联网的最初日子里，这种类型的数据是由人类手动寻找的，这是一个缓慢且繁琐的过程，限制了搜索引擎扩展其服务的速度。网络抓取提供了一种替代方案，让计算机来完成查找新页面和提取其内容的繁重工作。

最后，网络抓取是实现 Web 应用程序集成测试的一种方式——不是唯一的方式，也不一定是推荐的方式，但确实是其中一种方式。利用其作为客户端提取和传输数据的能力，网络抓取应用程序可以模拟普通用户的浏览器活动。这有助于确保 Web 应用程序的输出符合其预期的响应，以应对应用程序的需求。

### 网络抓取的适当使用

一些数据提供者可能只提供网站，而另一些可能提供不提供等效数据（以 conducive 格式或根本不提供）的 API。一些 Web 服务可能涉及广泛的身份验证流程，或不可用于公共消费。与网站相比，Web 服务端点的不可靠性也可能使其不可行。正是在这些情况下，网络抓取成为一种理想的替代方案。

通常的做法是避免进行破坏现有使用 Web 服务 API 的应用程序向后兼容性的更改，或者对它们进行版本管理，以允许应用程序供应商有时间过渡到新版本。因此，与网站页面的标记结构相比，Web 服务被修改的可能性要小得多，尤其是没有事先警告的情况下。对于经常更改的网站，这一点尤其成立，这可能会严重影响使用网络抓取的应用程序的稳定性。

简而言之，当没有其他可行的选项来获取所需数据时，网络抓取应作为最后手段使用。

### 网络抓取的合法性

这个问题的答案相当详细，并偏离到了“法律领域”。因此，它被收录在附录 A 中，以免分散本书的主要目的。

### 涵盖的主题

你显然正在阅读第 1 章，本章提供了网络抓取的简要介绍，回答了常见问题，并引出本书的主要内容。

- 第 2 章讨论 HTTP 协议的相关细节，因为在文档检索过程中使用了 HTTP 客户端。这包括请求和响应的结构，以及在实现 Cookie、HTTP 身份验证、重定向等功能时使用的各种头部信息。




- 第 3 章至第 7 章介绍了特定的 PHP HTTP 客户端库及其功能、用法以及各自的优缺点。
- 第 8 章深入探讨了自定义客户端库的开发，以及使用任何库时的常见关注点，包括防止限流、访问随机化、代理调度以及客户端脚本的副作用。
- 第 9 章详细说明了如何使用 tidy 扩展来修正获取的标记中的问题，以便在使用其他扩展进行分析之前先进行处理。
- 第 10 章至第 12 章回顾了 PHP 的各种 XML 扩展，比较了两大类 XML 解析器，并简要介绍了 XPath。
- 第 13 章研究了 CSS 选择器，比较了它们与 XPath 表达式的异同，并提供了关于用于查询标记文档的可用库的信息。
- 第 14 章探讨了使用 PCRE 扩展的正则表达式，这在验证抓取数据时非常有用，可以确保网页抓取应用程序的稳定性。
- 第 15 章概述了设计和开发网页抓取应用程序时的几种通用高层策略和最佳实践。

## 第 2 章

### HTTP

网页抓取应用程序必须能够执行的首要任务是检索包含待提取信息的文档。如果你使用过网页浏览器，却没有意识到它在“底层”为渲染页面供你浏览所做的所有工作，这听起来可能很微不足道。然而，网页抓取应用程序的复杂度通常与其目标应用程序（用于检索和提取数据）的复杂度成正比。

对于由多个页面组成或需要保留会话或身份验证信息的目标，开发相应的网页抓取应用程序通常需要进行一定程度的逆向工程。就像一道复杂的数学题可能有一个非常简单的答案一样，开发网页抓取应用程序有时涉及对目标应用的更多分析，而用于实现检索和提取数据脚本的工作量反而较少。

这种侦察工作需要具备**超文本传输协议**（即 **HTTP**，驱动互联网运行的协议）的良好工作知识。本章的大部分内容将侧重于熟悉该协议。最终目标是让你能够进行必要的研究，了解目标应用程序如何工作，从而能够编写应用程序来提取你想要的数据。

### 请求

HTTP 协议旨在为两方提供一种通用的通信方式：**Web 客户端**和 **Web 服务器**。客户端是向服务器发送请求的程序或脚本。客户端的例子包括网页浏览器（如 Internet Explorer 和 Mozilla Firefox）以及爬虫（如 Yahoo! 和 Google 用于扩展其搜索引擎服务的爬虫）。服务器是无限期运行且只接收并发送响应给客户端请求的程序。流行的例子包括 Microsoft IIS 和 Apache HTTP 服务器。

你必须足够熟悉 HTTP 请求和响应的结构及细微差别，以便做到以下两点。首先，你能够配置并使用你首选的客户端来查看在你访问目标应用时，该客户端与托管目标应用程序的服务器之间传递的请求和响应。这对于在不耗费过多时间和精力开发网页抓取应用程序方面至关重要。

其次，你能够使用 PHP HTTP 客户端库提供的大部分功能。理想情况下，你应该足够精通 HTTP 和 PHP，以便在必要时构建自己的客户端库或修复现有库的问题。然而，原则上，你应该首先寻找并使用现有的充分库，将构建可重用库作为最后的手段。我们将在接下来的几章中检查其中一些库。

### 补充参考

本书将以足够的深度介绍与网页抓取相关的 HTTP 内容，但在任何方面都不应被视为该主题的综合指南。以下是一些推荐的参考文献，用于补充本书涵盖的内容。

- RFC 2616 超文本传输协议 – HTTP/1.1 (http://www.ietf.org/rfc/rfc2616.txt)
- RFC 3986 通用资源标识符 (URI): 通用语法 (http://www.ietf.org/rfc/rfc3986.txt)
- "HTTP: The Definitive Guide"（ISBN 1565925092）
- “HTTP Pocket Reference: HyperText Transfer Protocol”（ISBN 1565928628）
- “HTTP Developer's Handbook”（ISBN 0672324547）
- Ben Ramsey 关于 HTTP 的博客系列文章 (http://benramsey.com/http-status-codes)

### GET 请求

让我们从一个非常简单的 HTTP 请求开始，即检索维基百科英文网站的主登录页面。

```
GET /wiki/Main_Page HTTP/1.1
Host: en.wikipedia.org
```

此请求的各个组成部分如下。

- **GET** 是 **方法或操作**。把它想象成句子中的动词，即你想对某物执行的动作。其他方法的例子包括 POST 和 HEAD。这些将在本章后面详细讲解。
- **/wiki/Main_Page** 是 **统一资源标识符** 或 **URI**。它为 **资源**（即操作的对象或目标）提供唯一的参考点。
- **HTTP/1.1** 指定客户端使用的 **HTTP 协议版本**，这将在本章稍后详细解释。
- 方法、URL 和 HTTP 版本共同构成了 **请求行**，其以 <CR><LF>（回车换行）序列结束，分别对应 ASCII 字符 13 和 10，或 Unicode 字符 U+000D 和 U+000A。（更多信息请参阅 RFC 2616 第 2.2 节。）
- 请求行之后跟随一个单个 **头部** Host 及其关联值 en.wikipedia.org。可能还会跟随更多的头部-值对。
- 基于资源、Host 头的值以及使用的协议（HTTP，而非 HTTPS 或基于 SSL 的 HTTP），http://en.wikipedia.org/wiki/Main_Page 是所请求资源的完整 URL。

### URI 与 URL

URI 有时与 URL 互换使用，这经常导致对二者确切性质的混淆。URI 用于唯一标识资源、指示如何定位资源，或两者兼有。URL 是 URI 的子集，它同时执行这两种功能（而非仅其中之一），这使得它们能被人类使用。毕竟，如果你无法访问资源，能够标识资源又有什么用呢！更多信息请参阅 RFC 3986 的第 1.1.3 节和第 1.2.2 节。

GET 是 HTTP 协议中使用最普遍的操作。根据 HTTP 规范，GET 的意图是请求资源的表示，基本上就是像读取文件系统中的文件一样“读取”它。此类表示的常见格式示例包括 HTML 和基于 XML 的格式（如 XHTML、RSS 和 Atom）。

原则上，GET 不应修改应用程序暴露的任何现有数据。因此，它被认为是一种被称为 **安全操作** 的操作。值得注意的是，在检查目标应用程序时，你可能会遇到 GET 操作被错误地用于修改数据而非简单返回数据的情况。这表明应用程序设计不佳，在开发自己的应用程序时应避免这种情况。

### URL 的结构

如果你还不熟悉 URL 的所有组件，这在后面的章节中可能会很有用。

```
http://user:pass@www.domain.com:8080/path/to/file.ext?query=$var=value#anchor
```

- http 是用于与资源交互的协议。另一个例子是 https，它等同于使用 SSL 证书加密连接的 http。
- user:pass@ 是一个可选组件，用于指示客户端需要基本 HTTP 身份验证才能访问资源，且 user 和 pass



在认证时，应分别用于用户名和密码。HTTP 认证将在本章末尾进行更详细的介绍。

-   `:8080` 是另一个可选段，用于指示客户端 `8080` 是 Web 服务器监听传入请求的端口。如果缺少此段，大多数客户端将使用标准的 HTTP 端口 80。
-   `/path/to/file.ext` 指定要访问的资源。
-   `query=&var=value` 是查询字符串，将在下一节中更详细地介绍。
-   `#anchor` 是片段，指向当前资源内的特定位置或状态。

## 查询字符串

URL 的另一个机制称为**查询字符串**，用于向 Web 应用程序传递**请求参数**。以下是一个包含查询字符串的 GET 请求，用于请求编辑维基百科页面的表单。

```
GET /w/index.php?title=Query_string&action=edit
Host: en.wikipedia.org
```

此 URL 有几种显著的特征。

-   问号表示资源路径的结束和查询字符串的开始。
-   查询字符串由键值对组成，每对之间用 & 分隔。
-   键和值之间用等号分隔。

查询字符串并非仅适用于 GET 操作，也可以用于其他操作。说到这点，让我们继续往下读。

## 查询字符串限制

大多数主流浏览器对查询字符串的最大字符长度施加了限制。这一点没有标准化的数值，但截至撰写本文时，Internet Explorer 7 似乎保持着 2,047 字节的最低公分母。查询搜索引擎可以得出你偏好浏览器的限制。这种情况在开发过程中很少会成为问题，但这是一个值得了解的情形。

## POST 请求

继 GET 之后最常见的 HTTP 操作是 POST，它用于向指定资源提交数据。当使用 Web 浏览器作为客户端时，这通常通过 HTML 表单完成。POST 旨在添加或修改应用程序公开的数据，潜在的结果是创建新资源或更改现有资源。GET 请求和 POST 请求之间的一个主要区别是，后者在请求头之后包含一个**主体**，用于容纳要提交的数据。

```
POST /w/index.php?title=Wikipedia:Sandbox&action=submit HTTP/1.1
Host: en.wikipedia.org

wpAntispam=&wpSection=&wpStarttime=20080719022313&wpEdittime=200807190221006&wpScrolltop=&wpTextbox1=~7%B7Please+leave+this+line+alone+%28sandbox%21+heading%29%7D%7D+%3C%21---Hello%21+Feel+free+to+try+your+formatting+and+editing+skills+below!this+line._As+this+page+is+for+editing+experiments%2C+this+page+will+automatically+be+cleaned+every+12+hours.+---%3E&wpSummary=&wpAutoSummary=d41d8cd98f00b204e9800998ecf8427e&wpSave=Save+page&wpPreview=Show+preview&wpDiff=Show+changes&wpEditToken=%5C%2B
```

一个空行将头部与主体分开。主体应该看起来很熟悉，因为它的格式与查询字符串完全相同，除了它前面没有问号。

![](img/1e839861f06c77df9ecabc0aed9127b5_32_0.png)

## URL 编码

查询字符串的一个特性是，参数值使用百分号编码进行编码，或者更常见的名称是**URL 编码**。PHP 函数 `urlencode` 和 `urldecode` 是处理这种编码的字符串值的一种便捷方式。大多数 HTTP 客户端库都会为你处理请求参数的编码。虽然它被称为 URL 编码，但其技术细节实际上与 RFC 3986 中第 2.1 节所示的 URI 关系更为密切。

## HEAD 请求

尽管在访问目标 Web 应用程序时并不常见，但 HEAD 请求在几种情况下对网络抓取应用程序很有用。它们的功能与 GET 请求相同，只有一个例外：当服务器提供其响应时，它不会提供通常构成响应主体的资源表示。之所以这样做有用，是因为它允许客户端获取响应头中存在的数据，而无需下载可能大得多的整个响应。此类数据可以包括资源是否仍可访问，如果是，它最后一次被修改的时间。

```
HEAD /wiki/Main_Page HTTP/1.1
Host: en.wikipedia.org
```

说到响应，现在是深入研究它们的好时机。

### 响应

除了第一行响应行（称为**状态行**）外，响应的格式与请求非常相似。虽然请求和响应使用不同的头部，但它们的格式相同。在请求和响应中，一个空行都用于分隔头部和主体。根据请求操作的不同，主体在请求或响应中可能都不存在。以下是一个示例响应。

```
HTTP/1.0 200 OK
Date: Mon, 21 Jul 2008 02:32:52 GMT
Server: Apache
X-Powered-By: PHP/5.2.5
Cache-Control: private, s-maxage=0, max-age=0, must-revalidate
Content-Language: en
Last-Modified: Mon, 21 Jul 2008 02:06:27 GMT
Content-Length: 53631
Content-Type: text/html; charset=utf-8
Connection: close

[body...]
```

除了头部，请求和响应之间的主要区别在于请求行与状态行内容的差异。

-   1.0 是客户端可以正确解释响应的最低 HTTP 协议版本。
-   200 是响应**状态码**，OK 是其对应的人类可读描述。它表明服务器尝试处理请求的结果，在本例中请求成功。

状态码分为五类，由代码的第一个数字区分。以下是每一类的简要总结。关于特定状态码可能收到的情况的进一步描述，请参阅 RFC 2616 第 10 节。

-   1xx 信息性：请求已接收，继续处理。
-   2xx 成功：请求已接收、理解并接受。
-   3xx 重定向：客户端必须采取额外操作来完成请求。
-   4xx 客户端错误：由于客户端问题，请求无法完成。
-   5xx 服务器错误：请求有效，但服务器处理失败。

让我们继续深入探讨头部。

## 头部

头部是一种通用的方法，用于传达与请求和响应相关的各种信息。客户端和服务器使用头部来完成许多事情，包括使用 cookies 保留状态和使用 HTTP 认证进行身份验证。本节将讨论那些特别适用于网络抓取应用程序的头部。欲知更多信息，请参阅 RFC 2616 第 14 节。

## Cookies

HTTP 被设计为一个无状态协议。也就是说，一旦服务器返回了请求的响应，它就实际上“忘记”了这个请求。它可能会记录关于请求及其提供的响应的信息，但它不会在同一个客户端的请求之间保留任何状态感。Cookies 是一种使用头部绕过这一限制的方法。以下是其工作原理。

-   客户端发出请求。
-   在其响应中，服务器包含一个 Set-Cookie 头。头的值由名称-值对组成，每个对都有可选的相关属性-值对。
-   在后续的请求中，客户端将包含一个 Cookie 头，其中包含它在 Set-Cookie 响应头中接收到的数据。

Cookies 经常用于限制对某些内容的访问，通常是通过要求某种形式的身份验证，之后目标应用程序才会指示应设置 cookie。大多数客户端库都有能力适当地处理解析和重新发送 cookie 数据，尽管有些需要在这样做之前进行明确指示。欲知关于 cookies 的更多信息，请参阅 RFC 2109 或其较晚（但普及度较低）的版本 RFC 2965。

上述属性之一，“expires”，用于指示客户端何时应丢弃 cookie 并在后续请求中不持久化其数据。此属性是可选的，其存在与否是决定 cookie 是否被称为**会话 cookie** 的决定因素。如果一个 cookie 没有过期值



设置后，它将在客户端会话期间持续有效。对于常规 Web 浏览器而言，这通常是指浏览器应用程序的所有实例都已关闭时。

### 重定向

Location 头由服务器使用，用于将客户端重定向到某个 URL。在此场景中，响应很可能包含 3xx 类状态码（例如 302 Found），但也可能包含 201 代码以指示新资源的创建。有关更多信息，请参阅 RFC 2616 的子章节 14.30。

从理论上讲，功能失调的应用程序可能会导致服务器在自身和客户端之间发起一系列无限的重定向。为此，客户端库通常会实现一个限制，规定在处理连续重定向的次数之前，假设被访问的应用程序行为不当并终止处理。库通常实现一个默认限制，但允许你用自己的限制覆盖它。

## 来源 URL

被请求的资源可能以某种方式引用其他资源。当这种情况发生时，客户端传统上会在 Referer 头中包含来源资源的 URL。是的，该头的名称拼写错误，且是故意为之。该特定拼写错误的普遍性导致其进入了官方 HTTP 规范，从而成为引用该特定头时使用的标准行业拼写。

规范来源的情况有多种。用户可能在浏览器中点击超链接，在这种情况下，包含该超链接的资源的完整 URL 将是来源。当请求包含嵌入图像的标记资源时，随后对这些图像的请求将包含包含这些图像的页面的完整 URL 作为来源。如前一节所述，发生重定向时也会指定来源。

这一点之所以相关，是因为某些应用程序在设计上依赖于 Referer 头的值，而从简单事实来看，头值可以被伪造，因此这不是理想的情况。无论如何，重要的是要知道，如果提供的头值与应用程序在浏览器中使用时发送的值不一致，某些应用程序可能无法按预期运行。有关更多信息，请参阅 RFC 2616 的子章节 14.36。

## 持久连接

HTTP 请求的标准操作程序如下。

- 客户端连接到服务器。
- 客户端通过已建立的连接发送请求。
- 服务器返回响应。
- 连接终止。

然而，在向同一服务器发送多个连续请求时，该过程中的第一步和第四步会产生大量的开销。HTTP 1.0 没有为此建立解决方案；每个请求一个连接是正常行为。在 HTTP 1.0 和 1.1 标准的发布之间，非正式地建立了一种约定，涉及客户端在请求中包含一个值为 Keep-Alive 的 Connection 头，以指示服务器期望持久连接。

后来，1.1 发布并将默认行为从每个请求一个连接更改为持久连接。对于非持久连接，客户端可以包含一个值为 close 的 Connection 头，以指示服务器在发送响应后终止连接。1.0 和 1.1 之间的区别是一个重要的区别，在评估客户端库和托管目标应用程序的服务器时，应将其作为一个检查点，以便你了解它们相对于持久连接的行为。有关更多信息，请参阅 RFC 2616 的子章节 8.1。

存在一种替代实现，在客户端和服务器中获得的显著支持较少，涉及使用 Keep-Alive 头。此技术问题的讨论见 RFC 2068 的子章节 19.7.1，但应避免明确使用此头。这里提到它只是为了让你意识到它的存在，并且它与持久连接有关。

## 内容缓存

存在两种方法允许客户端查询服务器，以确定自客户端上次访问以来资源是否已更新。RFC 2616 第 14 节的子章节详述了相关的头。

第一种方法是基于时间的，服务器在响应中返回 `Last-Modified` 头（子章节 29），客户端可以在对同一资源的后续请求中通过 `If-Modified-Since` 头（子章节 25）发送该值。

另一种方法是基于哈希的，服务器通过 `Etag` 头（子章节 19）在响应中发送哈希值，客户端可以在对同一资源的后续请求中通过 `If-None-Match` 头（子章节 26）发送该值。

如果资源在任一情况下均未更改，服务器只需返回 304 Not Modified 响应。除了检查资源是否仍然可用（如果不可用将导致 404 响应）外，这是使用 HEAD 请求的适当情况。

或者，可以通过使用 `If-Unmodified-Since` 头（子章节 28）反转第一种方法的逻辑，在这种情况下，如果资源自提供的访问时间以来确实已被修改，服务器将返回 412 Precondition Failed 响应。

### 用户代理

客户端有时被称为用户代理。这指的是 Web 浏览器作为代理，代表用户行动，以最小化用户干预的事实。`User-Agent` 头使客户端能够提供关于自身的信息，例如名称和版本号。爬虫通常使用它来提供获取有关爬虫或爬虫操作员电子邮件地址的更多信息的 URL。简单的搜索引擎查询应该会揭示主流浏览器的用户代理字符串列表。有关更多信息，请参阅 RFC 2616 的子章节 14.43。

不幸的是，一些应用程序会参与一种被称为**用户代理嗅探**或**浏览器嗅探**的做法，它们根据客户端提供的用户代理字符串调整它们交付的显示内容。这可能完全禁用主要站点功能，例如使用 ActiveX（一种特定于 Windows 和 Internet Explorer 的技术）的电子商务结账页面。

此技术的一个著名应用是机器人排除标准，用于明确指示爬虫避免访问单个资源或整个网站。有关此标准的更多信息可在 http://www.robotstxt.org 获取。在开发网络爬虫应用程序时，务必考虑那里详述的指导原则，以防止其表现出与正常用户不一致的行为。

在某些情况下，一种称为**用户代理伪造**的客户端实践，涉及指定虚假的用户代理字符串，足以规避用户代理嗅探，但并非总是如此。应用程序可能有平台特定的要求，正当理由使其拒绝访问某些用户代理。无论如何，伪造用户代理是一种应尽可能避免的做法。

## 范围

Range 请求头允许客户端指定服务器响应正文应限制为其正常正文的一个或多个特定字节范围。最初旨在允许失败的检索尝试从其停止点恢复，此功能允许你最小化应用程序与服务器之间的数据传输，以减少带宽消耗和网络爬虫应用程序的运行时间。

这适用于你对目标数据在文档中的位置有大致了解的情况，尤其是当文档相当大且你只需要其包含数据的一个小子集时。然而，使用它确实为你的应用程序增加了一个变量，如果目标站点发生变化，这可能会破坏你的应用程序，你在选择这样做时应牢记这一点。

虽然头值的格式保持开放以允许其他范围单位，但 HTTP/1.1 支持的唯一单位是字节。客户端和服务器都可以使用 Accept-Ranges 头来指示它们支持哪些单位。服务器将使用 Content-Range 头包含部分响应正文所在的完整响应正文的范围（格式略有不同）。

对于字节，文档的起始位置由 0 表示。范围使用包含边界。例如，文档的前 500 个字节将指定为


为 0-499。若要指定从某点到文档末尾的范围，只需省略上界。从字节 500 开始到文档末尾的部分表示为 500-。

如果指定的范围对于请求的资源是有效的，服务器应返回 206 Partial Content 响应。否则，它应返回 416 Requested Range Not Satisfiable 响应。关于 Range 和 Content-Range 头的更多信息，请参见 RFC 2616 的第 14.35 节和第 14.16 节。

## 基本 HTTP 认证

另一种不太常用的在请求之间保持身份持久化的方法是 HTTP 认证。大多数第三方客户端都提供某种形式的原生支持。虽然如今这并不常见，但在必须自行实现的情况下，了解如何推导适当的头值是很好的。有关 HTTP 认证的更多信息，请参见 RFC 2617。

HTTP 认证有几种不同的“风味”，其中较流行的两种是 Basic（未加密）和 Digest（加密）。Basic 是两者中更常见的，但两者的流程如下：

- 客户端发送一个不包含任何认证信息的请求。
- 服务器发送一个带有 401 状态码和 `WWW-Authenticate` 头的响应。
- 客户端重新发送原始请求，但这次包含了带有认证凭据的 `Authorization` 头。
- 服务器要么发送表示成功的响应，要么发送带有 403 状态码的响应，表示认证失败。

在 Basic 认证的情况下，`Authorization` 头的值将是单词 `Basic`，后跟一个空格，然后是派生自由冒号分隔的用户名-密码对的 Base64 编码序列。例如，如果用户名是 `bigbadwolf` 且密码是 `letmein`，则该头的值为 `Basic YmlnYmFkd29sZnM6RtZWlru`，其中字符串 `bigbadwolf:letmein` 的 Base64 编码版本位于 `Basic` 之后。

## 摘要 HTTP 认证

Digest 认证稍微复杂一些。服务器返回的 WWW-Authenticate 头将包含单词“Digest”，后跟一个空格，然后是逗号分隔的多个键值对，格式为 key="value"。以下是此头的示例。

```
WWW-Authenticate: Digest realm="testrealm@host.com", 
qop="auth,auth-int",
nonce="dcd98b7102dd2f0e8b11d0f600bfb0c093",
opaque="5cc069c403ebaf9f0l71e9517f40e41"
```

客户端必须使用服务器在允许客户端继续之前将验证的特定响应值进行响应。推导该值需要使用 MD5 哈希算法，这在 PHP 中可以使用 md5 或 hash 函数访问。流程如下。

- 将适当用户名、服务器提供的 realm 键值以及适当密码通过冒号连接起来，然后对该字符串进行 MD5 哈希。我们称之为 HA1。在会话的剩余时间内它不应改变。

```php
$ha1 = md5($username . ':testrealm@host.com:' . $password);
```

- 将原始请求的方法和 URI 通过冒号连接起来，然后对该字符串进行 MD5 哈希。我们称之为 HA2。显然，这将随方法或 URI 而变化。

```php
$ha2 = md5('GET:/wiki/Main_Page');
```

- 初始化一个请求计数器，我们称之为 nc，其值为 1。此计数器的值需要随着每个后续请求进行递增并重新传输，以唯一地标识该请求。重新传输在前一次请求中使用的请求计数器值将导致服务器拒绝它。注意，此计数器的值需要以十六进制数的形式传达给服务器。dechex PHP 函数对此很有用。

```php
$nc = 1;
```

- 使用上述哈希函数生成一个随机哈希，我们称之为客户端 nonce 或 cnonce。time 和 rand 函数可能在这里有用。这可以在（并且通常应该）每次请求时重新生成和重置。

```php
$cnonce = md5($_SERVER['REMOTE_ADDR'] . microtime(true));
```

- 注意服务器提供的 nonce 键的值，也称为服务器 nonce。我们将其简称为 nonce。这是由服务器随机生成的，并在一定时间后过期，此时服务器将返回 401 状态码。它将以两种显著方式修改返回的 WWW-Authenticate 头：1) 添加键值对 stale=TRUE；2) 更改 nonce 值。当发生这种情况时，只需使用新的 nonce 值如所示重新推导响应码并重新提交原始请求（不要忘记递增请求计数器）。

- 将 HA1、服务器 nonce（nonce）、当前请求计数器（nc）值、生成的客户端 nonce（cnonce）、服务器提供的 qop（保护质量）键中包含的逗号分隔列表中的适当值（最可能是 "auth"）以及 HA2 通过冒号连接起来，然后对该字符串进行 MD5 哈希。这就是最终的响应码。

```php
$response = implode(':', array(
    $ha1,
    $nonce,
    dechex($nc),
    $cnonce,
    'auth',
    $ha2
));
```

- 最后，将服务器最初在 WWW-Authenticate 头中发送的所有内容，加上响应值及其组成部分（显然不包括密码），通过普通的 Authorization 头发回给服务器。

```
Authorization: Digest username="USERNAME",
                realm="testrealm@host.com",
                nonce="dcd98b7102dd2f0e8b11d0f600bfb6c093",
                uri="/wiki/Main_Page",
                qop="auth",
                nc=00000001,
                cnonce="0a4f113b",
                response="6629fae49393a05397450978507c4ef1",
                opaque="5cc069c403e8af9f0171e9517f40e41"
```

一些第三方客户端实现了这一点，一些则没有。同样，它并不常用，但在必须自行实现的情况下，了解如何推导适当的头值是很好的。有关 HTTP 认证的更多信息，请参见 RFC 2617。

#### 总结

此时，你应该能够自如地查看 HTTP 请求和响应，并通过分析其各个组件来推断相关信息。接下来的几章将通过回顾几种常用的 PHP HTTP 客户端实现来阐述这些信息。

# 第 3 章

## HTTP 流封装器

此时，你应该已经相当熟悉使用 HTTP 客户端所涉及的一些通用概念。接下来的几章将回顾一些更主流的客户库，特别是常见的用例以及各自的优缺点。本章中介绍的客户端将是 HTTP 流封装器。

PHP 4.3 在核心中增加了 Streams 扩展。根据 PHP 手册的相关章节，其目的是提供“一种概括文件、网络、数据压缩以及其他共享一组通用函数和用途的操作的方法”。Streams 引入了几个概念，其中之一是 **wrapper**（封装器）。封装器的任务是定义流如何处理特定协议或使用特定编码的通信。HTTP 就是提供封装器协议之一。

HTTP 流封装器的优势在于 API 方面几乎没有需要学习的内容。很容易快速让简单的功能运行起来。缺点是就提供的功能集而言，它非常精简。它允许你发送 HTTP 请求，而无需完全自行构建（通过指定主体以及可选地添加任何你想要添加的头），并访问响应中的数据。仅此而已。请求调试能力就是一个当时未包含在内的功能示例。

封装器是用 C 编写的这一事实是一把双刃剑。一方面，C 代码和 PHP 之间存在显著的性能差异



代码（尽管在高负载环境中更为明显）。从负面来看，你必须要么了解 C 语言，要么依赖社区及时提供补丁来解决可能出现的问题。这也适用于后续章节中介绍的用 C 编写的扩展。

流包装器是 PHP 核心的一部分，因此除了 PHP 本身的安装要求外，没有其他安装要求。

## 简单的请求和响应处理

下面是一个使用 HTTP 流包装器的简单示例。

```php
<?php
$response = file_get_contents('http://localhost.example');
print_r($http_response_header);
?>
```

有几点需要注意。

- 此功能要求启用 `allow_url_fopen` PHP 配置项，这在大多数环境中是默认开启的。
- 在此示例中，调用 `file_get_contents` 函数相当于对指定 URL 'http://localhost.example' 发起 GET 请求。
- `$response` 将在调用 `file_get_contents` 函数完成后包含响应体。
- `$http_response_header` 会在调用 `file_get_contents` 后隐式填充 HTTP 响应状态行和头部，因为它在*当前作用域内*使用了 HTTP 流包装器。

虽然这个示例可以正常工作，但它违反了好代码实践的一个核心原则：没有意外的副作用。`$http_response_header` 的来源并不完全明显，因为 PHP 是隐式填充它的。此外，它更具限制性，因为该变量仅在包含对 `file_get_contents` 调用的作用域内被填充。以下是获取响应头中相同数据的更好方法。

```php
<?php
$handle = fopen('http://localhost.example', 'r');
$response = stream_get_contents($handle);
$meta = stream_get_meta_data($handle);
print_r($meta['wrapper_data']);
?>
```

让我们逐步分析。

- 资源 `$handle` 被创建用于读取 URL http://localhost.example。
- 调用 `stream_get_contents` 函数将 `$handle` 资源指向的流上剩余的数据读取到 `$response` 中。
- 调用 `stream_get_meta_data` 函数将 `$handle` 资源指向的流的元数据读取到 `$meta` 中。
- `$meta` 数组的 `wrapper_data` 索引输出与当前作用域内的 `$http_response_header` 相同的数组。只要 `$handle` 在当前作用域内可访问，就可以在其上调用 `stream_get_meta_data()`。这使其比 `$http_response_header` 更灵活。

### 流上下文和 POST 请求

流引入的另一个概念是上下文（context），基本上它是一组用于流操作的配置选项。上下文是通过将上下文选项及其对应值的关联数组传递给 `stream_context_create` 函数来创建的。关于 HTTP 流包装器，上下文的一个用途是发起 POST 请求，因为包装器默认使用 GET 方法。

```php
<?php
$context = stream_context_create(array(
  'http' => array(
    'method' => 'POST',
    'header' => implode("\r\n", array(
      'Content-Type: application/x-www-form-urlencoded',
      'Referer: http://localhost.example'
    )),
    'content' => http_build_query(array(
       'param1' => 'value1',
       'param2' => 'value2'
     ))
  )
));

$response = file_get_contents(
   'http://localhost.example/process',
   false,
   $context
);
?>
```

以下是此示例的详细解析。

- `'http'` 是正在使用的流包装器。
- `'POST'` 是请求的 HTTP 方法。
- `'header'` 流上下文配置项被填充为一个包含 HTTP 头部键值对的字符串，在本例中用于 Content-Type 和 Referer HTTP 头部。Content-Type 头部用于指示请求体数据是 URL 编码的。当需要多个自定义头部时，它们必须用回车换行符分隔（`"\r\n"` 也称为 CRLF 序列）。如果头部键值对存储在枚举数组中，`implode` 函数对此很有用。
- 使用 `http_build_query` 函数来构建请求体。此函数也可用于为 GET 请求构建 URL 的查询字符串。
- `http://localhost.example/process` 是被请求资源的 URL。
- 调用 `file_get_contents` 来执行请求，其选项通过使用 `stream_context_create` 创建的上下文 `$context` 传递。
- 响应体被返回并存储在变量 `$response` 中。

## 错误处理

在 PHP 5.3.0 之前，导致 HTTP 错误响应（即 4xx 或 5xx 状态码）的 HTTP 流包装器操作会触发 PHP 级别的警告。此警告仅包含 HTTP 版本、状态码和状态码描述。此类操作的函数调用通常返回 false，导致你无法获得流资源来检查更多信息。以下是获取尽可能多数据的方法示例。

```php
<?php
function error_handler($errno, $errstr, $errfile, $errline,
          array $errcontext) {

    // $errstr 将包含类似以下内容：
    // fopen(http://localhost.example/404): failed to open stream: 
    // HTTP request failed! HTTP/1.0 404 Not Found

    if ($httperr = strstr($errstr, 'HTTP/')) {

        // 在上述示例中，$httperr 将包含 HTTP/1.0 404 Not Found，
        // 在这里对该信息做一些有用的处理
    }
}

set_error_handler('error_handler', E_WARNING);

// 如果以下语句失败，$stream 将被赋值为 false
// 并且会自动调用 error_handler
$stream = fopen('http://localhost.example/404', 'r');

// 如果 error_handler() 未终止脚本，控制将在此处返回，
// 在其执行完成后
restore_error_handler();
?>
```

在 PHP 5.3 中，由于添加了 `ignore_errors` 上下文配置项，这种情况有所改善。当此配置项设置为 true 时，导致错误的操作与成功操作的处理方式相同。以下是其可能呈现的样子示例。

```php
<?php
$context = stream_context_create(
    array(
        'http' => array(
            'ignore_errors' => true
        )
    )
);

$stream = fopen('http://localhost.example/404', 'r', false, $context);

// 无论操作结果如何，此时 $stream 将是一个流资源
$body = stream_get_contents($stream);
$meta = stream_get_meta_data($stream);

// 此时 $meta['wrapper_data'][0] 将类似于 HTTP/1.0 404 Not Found，
// 随后的数组元素为其他头部
$response = explode(' ', $meta['wrapper_data'][0], 3);
list($version, $status, $description) = $response;
switch (substr($status, 0, 1)) {
    case '4':
    case '5':
        $result = false;
    default:
        $result = true;
}
?>
```

### HTTP 身份验证

HTTP 流包装器没有用于 HTTP 身份验证凭据的上下文选项。但是，可以将凭据作为正在访问的 URL 的一部分包含在内。参见下方示例。请注意，凭据不会预先编码；这是在发起请求时透明处理的。另外，请注意，此功能仅在使用基本（Basic）HTTP 身份验证时有效；摘要（Digest）身份验证必须手动处理。

```php
<?php
$response = file_get_contents(
    'http://username:password@localhost.example'
);
?>
```

### 更多其他选项

以下是 HTTP 流包装器中可能很有用的其他几个流上下文选项。

- `user_agent` 允许你设置用于该操作的用户代理字符串。也可以通过在 `header` 上下文选项值中指定 User-Agent 头部的值来手动设置。
- `max_redirects` 用于设置在假定应用程序行为异常并终止请求之前，该操作将处理的最大重定向次数。此选项仅在 PHP 5.1.0 及更高版本中可用，默认值为 20。
- `timeout` 用于设置读操作允许执行的最大时间限制（以秒为单位），超过该时间将被终止。它默认为 default_socket_timeout PHP 配置项的值。

所有其他利用头部的功能都必须通过手动实现，即在 `header` 上下文选项中指定请求头部，并检查 `$http_response_header` 或 `stream_get_meta_data` 函数返回数组的 `wrapper_data` 索引中的响应头部。

#### 总结

有关 HTTP 流包装器本身的更多信息，请参见 [http://www.php.net/manual/en/wrappers.http.php](http://www.php.net/manual/en/wrappers.http.php)。

有关特定于该包装器的上下文选项的详细信息，请参见 [http://www.php.net/manual/en/context.http.php](http://www.php.net/manual/en/context.http.php)。




### 第 4 章

### cURL 扩展

自 PHP 4.0.2 起可用的 cURL PHP 扩展封装了名为 libcurl 的库，该库实现了各种互联网协议的客户端逻辑，包括 HTTP 和 HTTPS。其 API 相当小巧，应用程序的使用主要由设置配置选项及其相应值的调用组成。

与 HTTP 流包装器相比，cURL 假设的默认配置值更少，例如是否处理重定向以及处理多少重定向。这带来的缺点在于，结合该扩展丰富的功能集，使用 cURL 的 PHP 代码通常比使用其他客户端库的等效代码更冗长。

与流包装器类似，cURL 扩展是用 C 编写的，在这方面具有相同优缺点。cURL 使用 **会话句柄**（一种 PHP 资源数据类型），可以以此将配置设置以类似于流包装器上下文关联方式联系起来。同样，像流上下文一样，cURL 会话句柄可以多次使用以重复相同的操作，直到将其传递给 `curl_close` 函数。

cURL 扩展包含在 PHP 核心中，但必须将其编译到 PHP 中或作为单独的扩展安装。根据运行环境的操作系统，这可能涉及安装除 OS PHP 软件包之外的其他软件包。

### 简单的请求和响应处理

```php
<?php
$ch = curl_init('http://localhost.example/');
curl_setopt($ch, CURLOPT_RETURNTRANSFER, true);
$response = curl_exec($ch);
curl_close($ch);
?>
```

让我们逐行查看这段代码。

- 调用 `curl_init` 并传入 'http://localhost.example/path/to/form' 作为请求的 URL。请注意，此参数是可选的，也可以通过调用 `curl_setopt` 来指定，参数为 cURL 会话句柄（在此为 $ch）、`CURLOPT_URL` 常量和 URL 字符串。
- 调用 `curl_setopt` 将 `CURLOPT_RETURNTRANSFER` 参数所表示的配置设置值设为 true。此设置将导致 `curl_exec` 以字符串形式返回 HTTP 响应体，而不是直接输出它，后者是默认行为。
- 调用 `curl_exec` 以执行请求并返回响应体。
- 调用 `curl_close` 以显式关闭 cURL 会话句柄，之后该句柄将不再可重用。

值得及早提到的一个有用设置是 `CURLOPT_VERBOSE`，当设置为 true 时会输出调试信息。该输出被发送到 stderr（默认值）或 `CURLOPT_STDERR` 值所引用的文件。

### 对比 GET 和 POST

显然，cURL 扩展还有其他函数，但总体而言，使用 cURL 扩展发出的大多数 HTTP 请求都将遵循上述示例所示的操作序列。让我们将其与 POST 请求进行比较。

```php
<?php
$data = array(
        'param1' => 'value1',
        'param2' => 'value2',
        'file1' => '@/path/to/file',
        'file2' => '@/path/to/other/file'
);

$ch = curl_init();
curl_setopt($ch, CURLOPT_URL, 'http://localhost.example/process');
curl_setopt($ch, CURLOPT_POST, true);
curl_setopt($ch, CURLOPT_POSTFIELDS, $data);
curl_setopt($ch, CURLOPT_RETURNTRANSFER, true);
$response = curl_exec($ch);
curl_close($ch);
?>
```

以下是此示例与前一个示例之间的差异。

- 这次 URL 是使用 curl_setopt 函数传入的，只是为了展示如何在不将其传递给 curl_init 函数的情况下完成操作。这在以不同 URL 重用 cURL 会话句柄时非常重要。
- 将 CURLOPT_POST 设置为 true 以将请求方法更改为 POST。
- CURLOPT_POSTFIELDS 是用作请求体数据的关联数组或预格式化的查询字符串。可以通过指定第一个字符为 @ 且其余部分为文件系统路径的值来上传文件，该路径指向要上传的文件。

以下是其他一些与请求方法相关的 cURL 配置设置常量。

- CURLOPT_HTTPGET：布尔值，当设置为 true 时，如果请求方法已从默认值更改，则明确将其重置为 GET。
- CURLOPT_NOBODY：布尔值，当设置为 true 时，通过将请求方法更改为 HEAD 来从响应中排除请求体。

### 设置多个选项

如果你使用的是 PHP 5.1.3 或更高版本，你可以访问 `curl_setopt_array` 函数，该函数允许你传入由设置-值对组成的关联数组，通过单次函数调用进行设置。如果你使用的是旧版本的 PHP，编写该函数相对容易。

使用此函数不仅使代码更少且更整洁，而且对于原生 C 函数而言，还减少了函数调用次数，从而间接提高了性能。

```php
<?php
if (!function_exists('curl_setopt_array')) {
    function curl_setopt_array($ch, $options) {
        foreach ($options as $setting => $value) {
            curl_setopt($ch, $setting, $value);
        }
    }
}

$ch = curl_init();
$opts = array(
    CURLOPT_URL => 'http://localhost.example',
    CURLOPT_RETURNTRANSFER => true
);
curl_setopt_array($ch, $opts);
$response = curl_exec($ch);
curl_close($ch);
?>
```

### 处理请求头

`CURLOPT_HEADER` 持有一个布尔标志，当设置为 `true` 时，将使请求头包含在 `curl_exec` 返回的响应字符串中。

获取包含在响应头中的某些数据（例如 HTTP 响应码）的另一种方法是使用 `curl_getinfo` 函数，如下例所示。有关此函数提供的其他信息，请参阅 PHP 手册中的条目。

```php
<?php
$ch = curl_init();
// ... 
$response = curl_exec($ch);
$info = curl_getinfo($ch);
$responsecode = curl_getinfo($ch, CURLINFO_HTTP_CODE);
?>
```

CURLOPT_HTTPHEADER 持有一个枚举数组，包含自定义请求头名称-值对，格式如下。

```php
<?php
$ch = curl_init();
curl_setopt($ch, CURLOPT_HTTPHEADER, array(
    'Accept-Language: en-us,en;q=0.5',
    'Accept-Charset: ISO-8859-1,utf-8;q=0.7,*;q=0.7',
    'Keep-Alive: 300',
    'Connection: keep-alive'
));
?>
```

### 调试

在前一节关于处理请求头的讨论中已经提到，curl_getinfo 函数还允许你查看由 cURL 发送的请求。这在调试时非常有用。下面是此功能的一个示例。

```php
<?php
$ch = curl_init();
curl_setopt_array(array(
    CURLINFO_RETURNTTRANSFER => true,
    CURLINFO_HEADER_OUT => true
));
curl_exec($ch);
$request = curl_getinfo($ch, CURLINFO_HEADER_OUT);
?>
```

- 在 `curl_setopt_array` 调用中，即使没有捕获 `curl_exec` 的返回值，CURLOPT_RETURNTRANSFER 也被设置为 `true`。这只是为了防止不需要的输出。
- 在 `curl_setopt_array` 调用中，CURLINFO_HEADER_OUT 被设置为 `true`，以指示应保留请求，因为它将在发出请求后被提取。
- 在 `curl_getinfo` 调用中指定 CURLINFO_HEADER_OUT，以将其返回值限制为包含所发出请求的字符串。

### Cookie

```php
<?php
$cookiejar = '/path/to/file';

$ch = curl_init();

$url = 'http://localhost.example';
curl_setopt($ch, CURLOPT_URL, $url);
curl_setopt($ch, CURLOPT_COOKIEJAR, $cookiejar);
curl_exec($ch);

$url = 'http://localhost.example/path/to/form';
curl_setopt($ch, CURLOPT_URL, $url);
curl_setopt($ch, CURLOPT_COOKIEFILE, $cookiejar);
curl_exec($ch);

curl_close($ch);
?>
```

以下是相关要点列表。

- 在第一次 `curl_exec` 调用之后，cURL 会将服务器返回的 Set-Cookie 响应头的值存储在与本地文件系统中 '/path/to/file' 路径引用的文件中，依据 CURLOPT_COOKIEJAR 设置。此设置值将持续存在，直至第二次 `curl_exec` 调用。
- 当第二次 `curl_exec` 调用发生时，CURLOPT_COOKIEFILE 设置也将指向 '/path/to/file'。这将导致 cURL 读取文件内容



该文件，并在构造请求时将其用作 Cookie 请求头的值。

- 如果 `$cookiejar` 设置为空字符串，Cookie 数据将持久保存在内存中，而不是本地文件中。这能提升性能（内存访问比磁盘快）并增强安全性（取决于服务器环境，文件存储可能比内存更容易被其他用户和进程访问）。

在某些情况下，希望 `CURLOPT_COOKIEJAR` 的值在每次请求中有所不同，例如用于调试。不过，在大多数情况下，`CURLOPT_COOKIEJAR` 会在接收初始 Cookie 数据的第一次请求时设置，并且其值会在后续请求中持续有效。在大多数情况下，在第一次请求之后，`CURLOPT_COOKIEFILE` 会被赋予与 `CURLOPT_COOKIEJAR` 相同的值。这将导致 Cookie 数据被读取以包含在请求中，随后响应中的 Cookie 数据会被写回（并覆盖该位置已有的数据），以供后续请求使用。相关地，如果你希望 cURL 开始一个新会话，从而丢弃会话 Cookie 的数据（即没有过期日期的 Cookie），你可以将 `CURLOPT_COOKIESESSION` 设置为 `true`。

如果你因某种原因需要手动处理 Cookie 数据，可以通过 `CURLOPT_COOKIE` 设置来指定 Cookie 请求头的值。为了访问响应头，将 `CURLOPT_HEADER` 和 `CURLOPT_RETURNTRANSFER` 设置为 `true`。这将使 `curl_exec` 调用返回包含头和主体的完整响应。请回想一下，头和主体之间有一行空行，冒号将每个头名称与其对应的值分隔开。将此信息与 PHP 中的基本字符串处理函数结合使用，通常就足够了。此外，你需要将 `CURLOPT_FOLLOWLOCATION` 设置为 `false`，以防止 cURL 自动处理重定向。如果不这样做，由导致重定向的请求所设置的任何 Cookie 都将丢失。

## HTTP 认证

cURL 支持 Basic 和 Digest 等多种 HTTP 认证方法。`CURLOPT_HTTPAUTH` 设置用于控制使用的方法，并通过 `CURLAUTH_BASIC` 或 `CURLAUTH_DIGEST` 等常量进行设置。`CURLOPT_USERPWD` 设置是一个包含认证凭据的字符串，格式为 `username:password`。请注意，这必须为每个需要认证的请求单独设置。

### 重定向

将 `CURLOPT_FOLLOWLOCATION` 设置为 `true`，可以让 cURL 自动处理重定向。也就是说，它会检测服务器响应中的 `Location` 头，并隐式发起请求，直到服务器响应中不再包含 `Location` 头为止。若要设置在终止前让 cURL 自动处理的最大 `Location` 头数量，请使用 `CURLOPT_MAXREDIRS` 设置。若要让认证凭据在由重定向产生的请求中持续有效，请将 `CURLOPT_UNRESTRICTED_AUTH` 设置为 `true`。

## 引用页

`CURLOPT_REFERER` 允许你显式设置 `Referer` 头的值。将 `CURLOPT_AUTOREFERER` 设置为 `true` 将导致 cURL 在处理 `Location` 头时自动设置 `Referer` 头的值。

## 内容缓存

`CURLOPT_TIMECONDITION` 必须设置为 `CURL_TIMECOND_IFMODSINCE` 或 `CURL_TIMECOND_IFUNMODSINCE`，分别选择使用 `If-Modified-Since` 或 `If-Unmodified-Since` 头。

`CURLOPT_TIMEVALUE` 必须设置为一个 UNIX 时间戳（使用 UNIX 纪元与目标日期之间的秒数来表示的日期），以指示资源的最后一次客户端访问时间。可以使用 time 函数来推导此值。

### 用户代理

`CURLOPT_USERAGENT` 可用于设置要使用的 User Agent 字符串。

## 字节范围

`CURL_OPT_RESUME_FROM` 可用于设置文档中的一个点，从该点开始响应主体。这将使 `Range` 头被设置为 `$X -$` 的值，其中 `$X$` 是指定的起始点。

若要指定多个范围，`CURL_OPT_RANGE` 接受一个字符串，其格式与 `Range` 头相同（例如：`X-Y, Z-`）。

# DNS 缓存

你可能会注意到，使用 cURL 扩展的代码比使用流的代码运行得更快。原因是 cURL 实现了自己的 DNS 缓存，如果你的操作系统或互联网服务提供商不提供 DNS 缓存，这种优势可能会更明显。

DNS，即域名系统，是一种以类似使用姓名查找电话号码的方式来为域名推导 IP 地址的系统。为域名获取 IP 地址的过程称为 DNS 查询，就所需时间而言可能是一个代价高昂的操作。

由于 DNS 查询的结果并不经常变化，通常使用 DNS 缓存来在查询执行后的特定时间段内保留结果。这可以在多个层级完成，包括源代码层级（如 cURL）、操作系统原生层级，或通过本地或远程服务器（如互联网服务提供商使用的服务器）上的软件（如 nscd 或 dnsmasq）来实现。

cURL 的 DNS 缓存默认是启用的。在某些情况下（如调试）可能需要禁用它，这可以通过将 `CURL_OPT_DNS_USE_GLOBAL_CACHE` 设置为 `false` 来实现。cURL 默认还会在内存中保留 DNS 查询结果两分钟。要更改此行为，请将 `CURL_OPT_DNS_CACHE_TIMEOUT` 设置为结果在缓存中保留的秒数，超时后结果将失效。

值得注意的是，cURL 的 DNS 缓存不是线程安全的。线程是一种特定的并行处理风格。最常见的线程实现由包含在单个操作系统进程中的多个执行线程组成，这些线程共享内存等资源。因此，在如 Windows Server 或运行线程化 Apache MPM（如 worker）的 \*NIX 等线程环境中，其行为可能会不可预测。

如果你正在使用 HTTP 流包装器或本章介绍的任何基于 PHP 的 HTTP 客户端库，并且你有权限在服务器上安装软件，你可能希望安装一个本地 DNS 缓存守护进程来提高性能。在 \*NIX 上尝试 nscd 或 dnsmasq。关于在后续编写自己的 HTTP 客户端章节中，我们将涵盖如何在你自己的客户端中编写 DNS 缓存。

## 超时

`CURLOPT_CONNECTTIMEOUT` 是 cURL 操作连接尝试将被限制的最大时间（以秒为单位）。可以将其设置为 0 以禁用此限制，但在生产环境中不建议这样做。请注意，此时间包括 DNS 查询。对于使用的 DNS 服务器或托管目标应用的 Web 服务器响应较慢的环境，可能需要增加此设置的值。

`CURLOPT_TIMEOUT` 是限制单个 cURL 扩展函数调用执行时间的最大秒数。请注意，此设置的值应包含 `CURLOPT_CONNECTTIMEOUT` 的值。换句话说，`CURLOPT_CONNECTTIMEOUT` 是 `CURLOPT_TIMEOUT` 所表示时间的一部分，因此后者的值应大于前者的值。

## 请求池化

由于是用 C 语言编写的，cURL 扩展拥有一项无法由 PHP 编写的库完全复制的功能：并行执行多个请求。这意味着可以一次性向 cURL 提供多个请求，并且，而不是等待第一个请求收到响应后再发送第二个请求，所有请求都会被发送并在响应返回时进行处理。这可以显著缩短完成所有请求所需的总时间。但是，在使用此功能时，应小心不要使单一主机因请求过载而崩溃。

```php
<?php
```





## 5. cURL 扩展（续）

```php
$ch1 = curl_init('http://localhost.example/resource1');
curl_setopt($ch1, CURLOPT_RETURNTRANSFER, true);
/* other curl_setopt calls */

$ch2 = curl_init('http://localhost.example/resource2');
curl_setopt($ch2, CURLOPT_RETURNTRANSFER, true);
/* other curl_setopt calls */

$mh = curl_multi_init();
curl_multi_add_handle($mh, $ch1);
curl_multi_add_handle($mh, $ch2);

$running = null;
do {
    curl_multi_exec($mh, $running);
} while ($running > 0);

$ch1_response = curl_multi_getcontent($ch1);
$ch2_response = curl_multi_getcontent($ch2);

curl_multi_remove_handle($mh, $ch1);
curl_close($ch1);

curl_multi_remove_handle($mh, $ch2);
curl_close($ch2);

curl_multi_close($mh);
```

-   两个 cURL 会话句柄 `$ch1` 和 `$ch2` 被正常初始化和配置。请注意，此类操作中可以使用超过两个句柄；这里仅为了满足示例目的而使用两个。
-   一个 cURL multi 句柄 `$mh` 被初始化，并且两个会话句柄被添加到其中。
-   使用循环配合标志 `$running` 来反复检查（即轮询）multi 句柄，直到所有包含的操作完成。
-   `curl_multi_getcontent` 用于两个会话句柄以获取各自的响应主体。
-   会话句柄分别通过 `curl_multi_remove_handle` 从 multi 句柄中移除，并使用 `curl_close` 关闭。
-   multi 句柄使用 `curl_multi_close` 关闭。

请注意，这是一个相当简单的示例，它等待所有请求完成后再尝试处理它们。如果你想在一返回就处理请求，请参阅 `http://code.google.com/p/rolling-curl/source/browse/#svn/trunk` 处的源代码，了解如何执行此操作。

#### 总结

有关 cURL 扩展的更多信息，请参阅 `http://php.net/manual/en/book.curl.php`。

有关安装 cURL 扩展的信息，请参阅 `http://php.net/manual/en/curl.installation.php`。

有关 cURL 扩展配置常量的信息，请参阅 `http://php.net/manual/en/function.curl-setopt.php`。

### 第 5 章

## pecl_http PECL 扩展

pecl_http 扩展在 PHP 5 中可用，并在 PHP 5.1 中增加了 HTTP 响应类。与 cURL 扩展类似，它也封装了 libcurl 库，因此具有类似的优点，例如其内部 DNS 缓存。虽然 cURL 扩展使用资源和配置选项来更密切地模拟 libcurl 自身的 API，但 pecl_http 扩展以过程式和面向对象 API 的形式提供相同的功能。结果是，使用 pecl_http 的代码通常比使用 cURL 扩展的等效代码更短。

另一个主要区别是，cURL 扩展被视为 PHP 核心的一部分，这意味着它更有可能出现在大多数支持 PHP 的环境中。相比之下，pecl_http 必须通过 pecl 安装程序安装或从源代码手动编译。无论哪种方式，该扩展都需要存在 PHP 和 libcurl 开发标头才能正确编译。由于在技术上不属于 PHP 核心，因此在共享主机环境中，取决于主机提供商，它不太可能存在或可用。这可能是针对打算在多种环境中分发的代码的一个关注点。

要通过 pecl 安装程序安装 pecl_http，必须已安装 PEAR（请参阅 `http://pear.php.net/manual/en/installation.php`）。PEAR 的包也可能通过你的 OS 包管理器可用。一旦安装完成，只需发出命令 `pecl install pecl_http`。要从源代码安装，请从 `http://pecl.php.net/get/pecl_http` 下载最新版本。请注意，这需要你正在使用的 PHP 版本的头文件，这些头文件包含在 PHP 源码 tarballs 中，可从 `http://www.php.net/downloads.php` 下载，或者可能也可以通过你的 OS 包管理器获取。

### GET 请求

```php
<?php
// Procedural
$response = http_get('http://localhost.example', null, $info);

// Object-oriented
$request = new HttpRequest('http://localhost.example');
$response = $request->send();
?>
```

-   `http_get` 调用后，`$response` 将是包含响应主体的字符串，`$info` 将包含一个关联数组，其中包含关于请求和响应的信息。`null` 用于代替稍后将详细介绍的请求选项数组。
-   `HttpRequest` 块是 `http_get` 过程式调用的面向对象等价物，并提供了一个更明确（尽管稍微不太简洁）的 API 来设置和获取有关请求和响应的数据。
-   `HttpRequest` 类的构造器有两个此处未显示的额外可选参数：一个表示请求方法的常量（GET 请求的默认值是 `HTTP_METH_GET`）以及 `http_get` 调用中使用的请求选项关联数组。

### POST 请求

```php
<?php
$data = array(
    'param1' => 'value1',
    'param2' => 'value2'
);

$files = array(
    array(
        'name' => 'file1',
        'type' => 'image/jpeg',
        'file' => '/path/to/file1.jpg'
    ),
    array(
        'name' => 'file2',
        'type' => 'image/gif',
        'file' => '/path/to/file2.gif'
    )
);

$options = array(
    'referer' => 'http://localhost.example/'
);

// Procedural
$response = http_post_fields(
    'http://localhost.example/process',
    $data,
    $files,
    $options,
    $info
);

// Object-oriented
$request = new HttpRequest;
$request->setUrl('http://localhost.example/process');
$request->setMethod(HTTP_METH_POST);
$request->setPostFields($data);
$request->setPostFiles($files);
$request->setOptions($options);
$response = $request->send();
```

-   `http_post_fields`、`setPostFields` 和 `setPostFiles` 用于将请求方法设置为 `POST`，并指定扩展应处理使用提供的数据构造和编码 POST 主体。如果你自己处理请求的这一方面，请改用 `http_post_data` 或 `setRawPostData`。
-   `setUrl` 用于设置 `HttpRequest` 实例的 URL，而不是在构造器中设置，仅作为一个示例。
-   实例化 `HttpRequest` 后，使用常量 `HTTP_METH_POST` 显式设置其请求方法。
-   此时传入了请求选项，具体来说是 Referer 头的值。它们通过 `http_post_fields` 的第四个参数和 `setOptions` 指定。
-   与 GET 请求一样，`http_post_fields` 和 `send` 的返回值的类型（字符串和 `HttpResponseMessage`）与前面 GET 示例中的对应项相同。
-   因为 `http_post_fields` 没有对象用于保留状态，所以它允许通过传入第五个参数 `$info` 来存储有关请求和响应的信息。请参阅 `http://php.net/http_get` 了解存储在 `$info` 中的信息示例。

> **替代方法和更多选项**
> 有关过程式 API 使用的除 GET 和 POST 之外的请求方法常量，请参阅 `http://php.net/manual/en/http.constants.php`。有关两种 API 可用请求选项的更多信息，请参阅 `http://php.net/manual/en/http.request.options.php`。

### 处理头

在使用过程式 API 时，通过发出请求的函数的 `$info` 参数可以获得有限的请求头信息。响应头包含在这些函数调用返回的字符串中。当该字符串传递给 `http_parse_message` 时，它返回一个对象，该对象有一个 `headers` 属性，这是以头部名称为索引的头值关联数组。

自定义请求头可以通过 `'headers'` 请求选项设置，其格式为关联数组，以头部名称为键，指向对应的头部值（与 cURL 不同，cURL 使用枚举数组，每个数组项包含一个头部名称-值对）。下面是一个请求选项数组中自定义头的示例。




### 调试

使用 pecl_http 调试传输的请求和响应其实非常简单。配置并发送请求，然后在请求实例上调用 `getRawRequestMessage` 和 `getRawResponseMessage` 方法，如下所示。

```php
<?php
$request = new HttpRequest('http://localhost.example/index.php');
// 配置 $request
$request->send();

// 返回包含完整请求的字符串
echo $request->getRawRequestMessage();

// 返回包含完整响应的字符串
echo $request->getRawResponseMessage();
?>
```

## 超时

与 cURL 类似，pecl_http 提供处理超时的选项。

'timeout' 请求选项对应 `CURLOPT_TIMEOUT`，它定义了整个请求在超时前允许的最大秒数。

同样，'connecttimeout' 请求选项是 `CURLOPT_CONNECTTIMEOUT` 的对应项，它定义了连接尝试（包括 DNS 解析）允许的最大秒数。

最后，'dns_cache_timeout' 请求选项等同于 `CURLOPT_DNS_CACHE_TIMEOUT`，它定义了 DNS 缓存条目保留的最大秒数，默认值为 120 秒（两分钟）。

#### 内容编码

如果您对内容编码不熟悉，请参阅第 8 章中的“Content Encoding”以获取更多信息。在使用 pecl_http 时，若要启用此功能，必须将 'compress' 请求选项设置为 true。

请注意，这需要启用 libz 支持。您可以通过在 PHP 脚本中执行 phpinfo 函数或在命令行中运行 php -ri http 来检查。如果未启用 libz 支持，可以使用第 8 章中详述处理编码内容的技术，应用于请求对象的 getResponseBody 方法的返回值。

## Cookies

```php
<?php
$requestcookies = array(
    'foo' => 'foovalue',
    'bar' => 'barvalue'
);

$cookiejar = '/path/to/cookiejar';

// 过程式
$options = array(
    'cookie' => $requestcookies,
    // - 或者 -
    'cookiestore' => $cookiejar
);

$response = http_get('http://localhost.example', $options);
$parsedresponse = http_parse_message($response);
$responsecookies = array_map(
    'http_parse_cookie',
    $parsedresponse->headers['Set-Cookie']
);

// 面向对象
$request = new HttpRequest('http://localhost.example');
$request->enableCookies();
$request->setCookies($cookies);
$request->addCookies(array('baz' => 'bazvalue'));
$request->send();
$responsecookies = $request->getResponseCookies();
?>
```

- 就像 cURL 一样，pecl_http 允许手动指定 cookie 数据。与 cURL 不同的是，pecl_http 为您处理了大部分格式化工作。只需为 `cookie' 请求选项指定一个关联数组，其中包含 cookie 名称-值对即可。如果您的 cookie 值已经编码，请将 `encodecookies' 请求选项设置为 false。
- 同样，就像 cURL 一样，pecl_http 包含一个使用文件存储 cookie 数据的选项。与 cURL 不同的是，pecl_http 始终为读和写操作使用相同的数据源。也就是说，它将 `CURLOPT_COOKIEFILE` 和 `CURLOPT_COOKIEJAR` 选项合并为 `cookiestore' 请求选项。
- 由于过程式 API 缺乏面向对象 API 所特有的持久作用域，提取 cookie 值以用于存储和持久化之外的用途稍显复杂。`http_parse_message` 用于解析包含 HTTP 响应消息的字符串中的头部和正文到一个对象中，以便更轻松地访问。然后，将 `http_parse_cookie` 应用于 `Set-Cookie` 头部值，从中解析出 cookie 数据。
- 在 `HttpRequest` 中，`enableCookies` 方法显式地将 `CURLOPT_COOKIEFILE` 设置为空字符串，以便 cookie 数据在内存中持久化。`setCookies` 接受一个包含 cookie 名称-值对的关联数组，就像 `cookie' 请求选项一样。`addCookies` 做同样的事情，但它是将数组内容合并到现有的 cookie 数据中，而不是像 `setCookies` 那样删除后者。
- 一旦在 `$request` 上调用 `send` 方法，就可以通过调用 `getResponseCookies` 方法从响应中检索 cookie 数据。

## HTTP 认证

`httppauth' 请求选项用于设置格式为 `username:password' 的凭证。要使用的 HTTP 认证类型通过 `httppauthtype' 请求选项指定，使用 pecl_http 的 `HTTP_AUTH_\*` 常量之一，这些常量与 cURL 扩展中用于相同目的的常量类似。

最后，如果认证凭证应包含在指向与当前主机不同的主机的重定向所导致的请求中，可以将 `unrestrictedauth' 请求选项设置为 `true`。

## 重定向和引用页

直观地看，`redirect` 请求选项用于设置在处理自动终止前允许的最大重定向次数。不那么直观的是，它的默认值为 0，这意味着禁用重定向处理，并且必须显式将此请求选项设置为大于 0 的值才能启用它。

`referer` 请求选项可用于设置 Referer 请求头的值。或者，在使用过程式 API 时，可以通过 `headers` 请求选项设置；在使用面向对象 API 时，可以通过 `HttpRequest` 类的 `setHeaders` 和 `addHeaders` 方法设置（稍后会有更多说明）。

## 内容缓存

`lastmodified` 请求选项接受一个 UNIX 时间戳，用作 If-Modified-Since 或 If-Unmodified-Since 请求头的值。

同样，`etag` 请求选项接受一个字符串，用作 If-Match 或 If-None-Match 请求头的值。

## User Agents

`useragent` 请求选项可用于为请求设置自定义 user agent 字符串。

## 字节范围

与 cURL 类似，pecl_http 包含用于单个恢复点和多个字节范围的请求选项。前者是 `resume`，接受一个整数作为起始点。后者是 `range`，格式化为一个枚举数组，其中每个元素包含一对整数，代表单个字节范围。下面是在请求选项数组中设置字节范围的示例。

```php
<?php
$opts = array(
    'range' => array(
        array(0, 1023), // 前 1024 字节 (KB)
        array(3072, 4095) // 第四部分 1024 字节 (KB)
    )
);
?>
```

或者，可以通过 `headers` 请求选项使用自定义头进行设置。

```php
<?php
$opts = array(
    'headers' => array(
        'User-Agent' => 'Mozilla/5.0 (X11; U; ...',
        'Connection' => 'keep-alive'
    )
);
?>
```

## 请求池

pecl_http 还继承了 cURL 对请求池（即并行发送和处理多个请求）的支持。与其他特性一样，pecl_http 以更简洁的方式实现了它。奇怪的是，它是 pecl_http 面向对象 API 中特有的一个功能，在过程式 API 中没有等价物。它通过 `HttpRequestPool` 类实现。

```php
<?php
$request1 = new HttpRequest;
// 配置 $request1

$request2 = new HttpRequest;
// 配置 $request2

$request3 = new HttpRequest;
// 配置 $request3

$pool = new HttpRequestPool($request1, $request2);
$pool->attach($request3);
$pool->send();
?>
```




- `HttpRequestPool` 构造函数接受可变数量的参数，所有参数都应是预配置好的 `HttpRequest` 实例。
- 也可以通过 `HttpRequestPool` 类的 `attach` 方法添加请求实例。
- 在池实例上调用 `send` 会发送所有请求，并阻塞直到接收到所有响应。完成后，所有请求实例都包含各自的响应数据，就好像它们被单独发送一样。

## 小结

有关 `pecl_http` 扩展的更多信息，请参阅 http://php.net/http。
有关其请求选项的更多信息，请参阅 http://php.net/manual/en/http.request.options.php。

## 第 6 章

## PEAR::HTTP_Client

PHP 扩展和应用程序库 (PEAR) 项目包含一个由 PHP 编写的可重用组件库以及用于分发它们的系统，其中 **HTTP_Client** 包将在本节中介绍。PEAR 推动了 PECL 项目的创建，这是一个 C 扩展库，上一节中讨论的 `pecl_http` 扩展就源自于此。

PEAR 中许多组件的一个特点是与旧版本的 PHP 保持向后兼容性。 **HTTP_Client** 包本身仅要求 4.3.0，而 PHP 4 分支的最新且最终版本是 4.4.9。因此，当功能需求超出 HTTP 流封装器原生支持的范围，且预期的运行环境限制在旧版本的 PHP 时，此客户端可能是一个不错的解决方案。否则，如果您仍然希望使用用 PHP 编写的 HTTP 客户端，可以查看下一节中描述的 `Zend_Http_Client`。不言而喻，对 PHP 4.x 的支持已经停止，在生产环境中强烈建议运行更新的稳定版本 PHP。

PHP 源代码包包含一个配置选项，用于在编译时包含 PEAR。某些操作系统可能提供了独立于 PHP 本身的 PEAR 软件包。一旦安装了 PEAR，`pear install HTTP_Client` 通常就足以安装 PEAR::HTTP_Client。也可以选择手动下载必要的 PEAR 包（HTTP_Client、HTTP_Request、Net_URL 和 Net_Socket）的 tarball，尽管随着更新的发布，这在长期维护上会稍微困难一些。

**PEAR 的发展**
在撰写本书时，正在进行 PEAR 2 的开发工作，它是当前 PEAR 项目版本的继任者。这将包括新的软件包分发系统，以及对许多现有软件包的移植或重新开发，使其与 PHP 5 中可用的功能保持同步。然而，由于目前 PEAR 2 缺乏稳定的移植代码，本书的范围将仅限于 PEAR 1。

## 请求与响应

使用相关的 PEAR 组件执行 HTTP 请求有两种方法：HTTP_Request 和 HTTP_Client。后者组合前者，以增加处理重定向以及在多个请求间持久化头部、cookie 数据和请求参数等功能。以下是直接使用 HTTP_Request 执行简单请求并提取响应信息的方法。

```php
<?php
require_once 'HTTP/Request.php';

$request =& HTTP_Request('http://localhost.example');
$request->setMethod(HTTP_REQUEST_METHOD_GET);
$request->setURL('http://localhost.example');
$response = $request->sendRequest();
?>
```

- HTTP_Request 构造函数有两个参数，均为可选。第一个是包含请求 URL 的字符串；注意，`setURL` 方法是指定此值的另一种方式。第二个是参数数组，将在后文中讨论。
- 默认情况下，使用 GET 方法。使用常量通过 `setMethod` 更改此设置，常量的命名方式是在所需请求方法前加上 `HTTP_REQUEST_METHOD_` 前缀，例如 `HTTP_REQUEST_METHOD_GET`。

`sendRequest` 直观地分发请求并获取响应。它返回 `true` 表示该请求成功，或者如果出现问题则返回一个错误对象（默认为 PEAR_Error 类）。

导致错误的问题包括组件的环境要求未得到满足或请求目标超出了重定向限制。`PEAR::isError` 用于确定 `sendRequest` 调用是否导致了错误。如果请求成功发送，可以使用请求对象的几种方法来提取响应信息。

```php
<?php
if (!PEAR::isError($response)) {
  $code = $request->getResponseCode();
  $reason = $request->getResponseReason();
  $body = $request->getResponseBody();
  $cookies = $request->getResponseCookies();
  $headers = $request->getResponseHeader();
  $contentType = $request->getResponseHeader('Content-Type');
}
?>
```

以下是关于响应信息方法的几个具体细节。

- `getResponseCode` 返回包含 HTTP 状态码的整数。
- `getResponseReason` 返回包含与 HTTP 状态码对应的描述字符串。
- 如果没有设置 cookie，`getResponseCookies` 返回 `false`；否则，它返回一个关联数组的枚举数组，其中每个数组包含单个 cookie 的信息，如其名称、值和过期时间。
- 如果未向 `getResponseHeader` 传递参数，它将返回一个包含所有头部的关联数组，索引为头部名称（全部小写）；否则，它接受一个包含特定头部名称的字符串参数，并返回其值。

`sendRequest` 不会修改你设置的特定于请求的参数（相对于响应而言）。也就是说，请求实例可以重用，仅根据需要修改个别参数，以改变连续请求之间的差异。要使用现有的请求实例“重新开始”，只需显式调用其构造函数方法。

```php
<?php
$request =& new HTTP_Request;
// ...
$request->HTTP_Request();
// 所有之前设置的参数都将被清除
?>
```

### 数据处理

HTTP_Request 使数据管理变得非常简单直接，因此本节涵盖了所有内容。

```php
<?php
$request =& new HTTP_Request('http://localhost.example');

// GET
$request->addQueryString('variable', 'value');
$request->addRawQueryString('foo=bar');

// POST
$request->addPostData('variable', 'value');
$request->clearPostData();

// COOKIE
$request->addCookie('variable', 'value');
$request->clearCookies();

// FILES
$request->addFile('fieldname', '/path/to/file', 'text/plain');
?>
```

- `addRawQueryString` 的命名不太直观，因为它实际上会覆盖你之前设置的任何查询字符串。
- 默认情况下，`addQueryString` 和 `addPostData` 会对变量值进行 URL 编码。如果数据已经预先编码，想要防止此行为，请在任一方法中传递值 `true` 作为第三个参数。
- `clearPostData` 和 `clearCookies` 分别重置用于存储由 `addQueryString` 和 `addPostData` 传入数据的内部变量。
- `setURL` 和 `addQueryString` 或 `addRawQueryString` 可以一起使用，以控制请求 URL 内部变量的内容。在开发期间可以使用 `getURL` 来查看这些操作的效果。
- `addFile` 旨在模拟通过 HTML 表单中的文件输入字段上传文件。对于具有多个同名文件上传的表单，第二个参数传递文件路径数组，（可选地）第三个参数传递相应的文件 MIME 类型数组。
- 要将文件内容作为请求的整个正文发送，请使用 `file_get_contents` 获取文件内容到一个字符串，并将其传递给请求实例的 `setBody` 方法。

### 处理头部

处理头部也相对简单。包含的唯一特定于头部的便捷方法用于处理基本的 HTTP 身份验证，如下所示。

```php
<?php
$request =& new HTTP_Request;
$request->addHeader('name', 'value');
$request->removeHeader('name');
$request->setBasicAuth('username', 'password');
?>
```




### 使用客户端

HTTP_Client 在多个请求中持久化显式设置的标头和请求参数集合，这些集合分别通过 `setDefaultHeader` 和 `setRequestParameter` 方法设置。客户端构造函数也接受这些集合的数组形式。通过调用客户端实例上的 `reset` 方法可以清除默认标头和请求参数。

内部地，客户端类实际上为每个请求创建一个 HTTP_Request 的新实例。请求操作根据调用的客户端实例方法而设置；支持 `get`、`head` 和 `post`。

此处描述的客户端功能都可以通过重用同一个请求实例进行多次请求来实现。然而，客户端还处理了请求类未涉及的两项功能：Cookie 和重定向。

默认情况下，Cookie 会在没有额外配置的情况下自动跨请求持久化。内部使用 HTTP_Client_CookieManager 来实现此功能。对于自定义的 Cookie 处理，可以扩展此类并将其实例作为第三个参数传递给客户端构造函数。如果这样做，将使用该实例，而不是默认创建的 native cookie manager 类实例。

可以使用客户端类的 `setMaxRedirects` 方法设置处理的最大重定向前数。内部，将根据需要创建并发送请求以处理重定向，直到接收到非重定向响应或达到最大重定向限制为止。在前一种情况下，被调用的客户端方法将返回包含响应代码的整数，而不是像请求类那样返回 `true`。在后一种情况下，客户端方法将返回一个错误实例。请注意，除了 HTTP 层执行的重定向外，客户端类还将处理 HTML 文档中 meta 标签包含的重定向。

要检索最后接收到的响应信息，请使用客户端实例的 `currentResponse` 方法。它将返回一个关联数组，包含键 '`code`'、'`headers`' 和 '`body`'，其值分别对应请求方法 `getResponseCode`、`getResponseHeader` 和 `getResponseBody` 的返回值。

默认情况下，所有响应都会被存储，并且可以像下面那样单独访问。要禁用除最后一个响应以外的所有响应存储，请在客户端实例上调用 `enableHistory` 并传入 `false`。

```php
<?php
for ($client->rewind(); $client->valid(); $client->next()) {
    $url = $client->key();
    $response = $client->current();
}
?>
```

### 观察请求

HTTP_Request 和 HTTP_Client 都有 `attach` 和 `detach` 方法，用于添加和移除 HTTP_Request_Listener 实例。此类实现了观察者设计模式，用于拦截在发送请求和接收响应过程中发生的事件。要创建一个观察者，首先创建一个扩展 HTTP_Request_Listener 的类，如下所示。

```php
<?php
class Custom_Request_Listener extends HTTP_Request_Listener
{
    function Custom_Request_Listener()
    {
        $this->HTTP_Request_Listener();
    }

    function update(&$subject, $event, $data = null)
    {
        switch ($event) {
            // Request events
            case 'connect':      // handle the 'connect' event
            case 'sentRequest':  // ...
            case 'disconnect':   // ...

            // Response events
            case 'gotHeaders':   // ...
            case 'tick':         // ...
            case 'gztick':       // ...
            case 'gotBody':      // ...

            // Client events
            case 'request':      // ...
            case 'httpSuccess':  // ...
            case 'httpRedirect': // ...
            case 'httpError':    // ...

            default:
                PEAR::raiseError('Unhandled error: ' . $event);
        }
    }
}
?>
```

- 声明一个构造函数，该构造函数调用父类构造函数并执行所需的自定义逻辑。
- 声明具有所示签名的 `update` 方法。`$subject` 是监听器所附加的请求或客户端实例。`$event` 是一个包含 switch 语句中所示事件之一的字符串。
- `$data` 是与接收服务器响应相关的事件特定数据。
- 请求和响应事件发生在 HTTP_Request 实例中。客户端事件发生在 HTTP_Client 实例中。
- 请注意，并非所有事件都需要处理，只需处理您关注的那些事件即可。

HTTP_Request 中的 `attach` 方法接受单个参数，即一个监听器实例。HTTP_Client 中的等效方法接受两个参数，一个必需的监听器实例和一个可选的布尔标志。当后者为 `false`（默认情况）时，附加的监听器不会传播到客户端实例内部创建的请求中。也就是说，添加的监听器不会收到请求和响应事件的通知，只接收客户端事件。要使添加的监听器接收所有事件，在调用 `attach` 时显式指定 `$propagate` 参数为 `true`。

#### 总结

有关此处介绍的 PEAR 包更多信息，请参见下面列出的资源。

- http://pear.php.net/manual/en/package.http.http-request.php
- http://pear.php.net/manual/en/package.http.http-client.php
- http://pear.php.net/manual/en/package.http.http-request.listeners.php

## 第 7 章

### Zend_Http_Client

Zend Framework（通常缩写为 ZF）构想于 2005 年初。与 PEAR 不同，ZF 倾向于保持其要求的 PHP 版本相对较新，并且经常利用新版本中可用的功能。截至 ZF 1.10.1，要求使用 PHP 5.2.4。

ZF 旨在充分利用 PHP 5 引入的新对象系统，具有完全面向对象的 API。项目团队努力保持 E_STRICT 级别的合规性以及通过单元测试实现良好的代码覆盖率。

ZF 中包含的组件之一是 Zend_Http_Client，这是一个 HTTP 客户端库，其功能集与前面章节中已介绍的其他库相当可观。既然如此，让我们来看看它的工作原理。

### 基本请求

让我们从一个基本请求开始。

```php
<?php
$client = new Zend_Http_Client;
$client->setUri('http://localhost.example');
$response = $client->request();

// This does the same thing
$client = new Zend_Http_Client('http://localhost.example');
$response = $client->request('GET');

// Another way to set the request method
$client->setMethod(Zend_Http_Client::GET);
?>
```

- 请求的 URL 可以作为 `Zend_Http_Client` 构造函数的第一个参数传入，或者在创建客户端实例后通过 `setUri` 方法传入。这两种方法都接受 URI 作为字符串或 `Zend_Uri_Http` 实例。
- 客户端的 `request` 方法用于发送请求，接受一个可选参数，即包含要使用的 HTTP 请求方法的字符串。默认使用 `GET`。也可以通过使用命名为该 HTTP 请求方法的客户端类常量，利用客户端的 `setMethod` 方法来设置 HTTP 请求方法。

### 响应

客户端 `request` 方法返回的响应具有许多有用的访问器方法。

```php
<?php
// Returns an integer containing the status code
var_dump($response->getStatus());

// Returns a string containing a description for the status code
var_dump($response->getMessage());

// Returns a string containing the fully decoded response body
var_dump($response->getBody());

// Returns a string containing the unaltered response body
var_dump($response->getRawBody());

// Returns an associative array of headers
var_dump($response->getHeaders());

// Returns a string or array of values for a single header
var_dump($response->getHeader('Content-Type'));

// Returns TRUE for 100- and 200-level status codes
var_dump($response->isSuccessul());

// Returns TRUE for 400- and 500-level status codes
var_dump($response->isError());
?>
```

### URL 处理

默认情况下，Zend_Http_Client 使用 Zend_Uri_Http 来验证传入客户端的任何 URI。使用非常规 URL，特别是那些使用 RFC 2396（RFC 3986 的前身）第 2.4.3 节中描述为不允许的字符的 URL，可能会导致验证失败。请参阅下面的代码示例了解如何处理这种情况。

```php
<?php
// $valid will be false because the URL contains a |
$valid = Zend_Uri::check('http://localhost.example/?q=this|that');

// Force URLs with disallowed characters to be considered valid
Zend_Uri::setConfig(array('allow_unwise' => true));

// $valid will be true because of allow_unwise being enabled
$valid = Zend_Uri::check('http://localhost.example/?q=this|that');

// URLs with disallowed characters will be considered invalid again
Zend_Uri::setConfig(array('allow_unwise' => false));
?>
```

### 自定义标头

`setHeaders` 方法是 Zend_Http_Client 标头管理的瑞士军刀。请参阅下面的示例，了解设置标头的多种方法。



<?php
// 单个请求头，请求头名称和值分开
$client->setHeaders('Host', 'localhost.example');

// 单个请求头，请求头名称和值合在一起
$client->setHeaders('Host: localhost.example');

// 具有多个值的单个请求头，主要用于 Cookie
$client->setHeaders('Cookie', array(
    'lang=en-US',
    'PHPSESSID=1a0b82148815944c548caef5ccb884c9'
));

// 多个请求头，请求头名称和值分开
$client->setHeaders(array(
    'Host' => 'localhost.example',
    'User-Agent' => 'Zend_Http_Client 1.7.2'
));

// 多个请求头，请求头名称和值合在一起
$client->setHeaders(array(
    'Host: localhost.example',
    'User-Agent: Zend_Http_Client 1.7.2'
));
?>

### 配置

Zend_Http_Client 拥有类似于 HTTP 流包装器上下文选项、cURL 扩展配置项以及 pecl_http 扩展请求选项的配置设置。如下面的示例所示，配置项以设置名称-值对的关联数组形式声明，可以作为 Zend_Http_Client 构造函数的第二个参数传入，或者稍后通过其 setConfig 方法传入。

```php
<?php
$config = array('timeout' => 30);

// 一种方式
$client = new Zend_Http_Client('http://localhost.example', $config);

// 另一种方式
$client->setConfig($config);
?>
```

### 连接

`timeout` 配置项是一个整数值，指定客户端尝试连接服务器前等待的秒数，超过该时间即视为超时。发生超时时，将抛出异常实例 `Zend_Http_Client_Adapter_Exception`。

默认情况下，客户端假设在其建立的连接上只执行一次请求。也就是说，它将自动包含一个值为 `close` 的 `Connection` 请求头。当向同一主机发送多个请求时，可以将 `keepalive` 配置项设置为 `true`，以便所有请求都在同一连接上发送，从而提高性能。

### 调试

可以通过客户端的 `getLastRequest` 方法以字符串形式获取最后发送的请求。对于最后接收到的响应，可以调用对应的方法 `getLastResponse`。该方法返回 `Zend_Http_Response` 的实例，而不是字符串。要将此对象转换为字符串，请调用其 `asString` 方法。以下示例展示了这两种用法。

```php
<?php
$requestString = $client->getLastRequest();
$responseObject = $client->getLastResponse();
$responseString = $responseObject->asString();
?>
```

请注意，`storeresponse` 配置项会影响 `getLastResponse` 的行为。当设置为 `true`（默认值）时，客户端接收到的最后一个响应会被存储起来，以便后续检索。当设置为 `false` 时，响应不会被存储，仅作为客户端 `request` 方法的返回值存在。在这种情况下，getLastResponse 将返回 null。如果您不需要额外获取响应数据，关闭此选项可以减少资源使用。

### Cookie

Zend_Http_Client 通过其 setCookie 方法接受手动指定的 Cookie 名称-值对，但默认情况下不会自动保存响应中的 Cookie 并在后续请求中重新发送。要启用此行为，只需调用不带参数的 setCookieJar 方法即可。这将隐式实例化默认的 Cookie 处理类 Zend_Http_CookieJar 的一个实例。

如果您需要访问 Cookie 数据用于除传播到后续请求之外的其他用途，有几种方法可以做到。可以通过 Cookie 容器的 getCookie 方法单独访问 Cookie，该方法所需的参数是一个 URI 和一个 Cookie 名称。

```php
<?php
$cookie = $client->getCookieJar()->getCookie(
        'http://localhost.example/',
        'cookieName'
    );
?>
```

请注意，URI 包含协议（http://）、域名（localhost.example）和路径（/）。单个 Cookie 容器实例可以存储同一域名下多个域名和多个路径的 Cookie 数据。在后一种功能未使用的情况下，可以指定路径 /，以便该指定域名下所有路径均可访问在该域名上设置的所有 Cookie。Zend_Http_CookieJar 的 getMatchingCookies 方法允许基于这些条件集体访问 Cookie，并默认返回一个 Zend_Http_Cookie 对象的数组。以下示例说明了其用法。

```php
<?php
// 域名 localhost.example 的所有 Cookie
$cookies = $cookieJar->getMatchingCookies(
        'http://localhost.example/'
    );

// 域名 localhost.example 中路径或子路径为 /some/path 的所有 Cookie
$cookies = $cookieJar->getMatchingCookies(
    'http://localhost.example/some/path'
);

// 域名 localhost.example 的所有非会话 Cookie
$cookies = $cookieJar->getMatchingCookies(
    'http://localhost.example/',
    false
);
?>
```

或者，可以使用 getAllCookies 来访问 Cookie 容器实例中包含的所有 Cookie。当 Cookie 容器仅用于存储单个域名的 Cookie 时，getAllCookies 提供了比 getMatchingCookies 更简洁的方式来检索该域名的所有 Cookie。与 getMatchingCookies 一样，getAllCookies 也默认返回一个 Zend_Http_Cookie 对象的数组。

### 重定向

maxredirects 配置项是一个整数，指示终止前执行的最大重定向次数。终止时，客户端将简单地返回其接收到的最后一个响应。Zend_Http_Response 的 isRedirect 方法对于具有 3xx 级别状态码的响应返回 true。

RFC 2616 的第 10.3.2 节和第 10.3.3 节指出，当发生重定向时，应保留请求方法和参数。在实践中，大多数客户端并非如此行为。相反，参数会被清除，方法会恢复为 GET。为了与其他客户端保持一致，Zend_Http_Client 默认采用这种非合规行为。要强制使其符合 RFC 标准，可以将 strictredirects 配置项设置为 true。

### 用户代理

useragent 配置项包含要使用的用户代理字符串，默认为 'Zend_Http_Client'。

### HTTP 身份验证

截至本文撰写时，Zend_Http_Client 仅支持基本 HTTP 身份验证。根据 Zend Framework 参考指南，对摘要认证的支持已在计划中。要设置 HTTP 身份验证凭据，请调用客户端的 setAuth 方法并传入用户名和密码。

#### 总结

有关 Zend_Http_Client 的参考指南章节，请参阅 http://framework.zend.com/manual/en/zend.http.html。

有关 Zend_Http 包中所有类的 API 文档，请参阅 http://framework.zend.com/apidoc/core/classstrees_Zend_Http.html。

## 第 8 章

### 自行开发

首先，不言而喻，使用并基于现有库进行开发通常优于从头开始自行开发。一方面，这样可以“免费”获得许多功能，无需您做任何工作。另一方面，团队和项目之外的开发人员也在维护这些库，正如 Eric S. Raymond 所言：“只要眼睛足够多，所有 Bug 都会暴露无遗。”

然而，即使您不打算自己开发客户端，熟悉这些信息也无济于事。这样做可以增强您排查现有库问题的能力，并能够向其项目团队贡献补丁。

无论您的动机是什么，让我们开始吧。

### 发送请求

除了针对特定协议的包装器外，流扩展还提供了套接字传输层，用于在更低的层面处理数据。其中一种套接字传输层用于 TCP（传输控制协议），这是一种核心的互联网协议，用于确保有序字节序列的可靠传输。该套接字传输层便于向服务器发送原始数据流，在此情况下为手动构建的 HTTP 请求。

```php





```php
$stream = stream_socket_client('tcp://localhost.example:80');
$request = "GET / HTTP/1.1\r\nHost: localhost.example\r\n\r\n";
fwrite($stream, $request);
echo stream_get_contents($stream);

/*
Example output:
HTTP/1.1 200 OK
Date: Wed, 21 Jan 2009 03:16:43 GMT
Server: Apache/2.2.9 (Ubuntu) PHP/5.2.6-2ubuntu4 with Suhosin-Patch
X-Powered-By: PHP/5.2.6-2ubuntu4
Vary: Accept-Encoding
Content-Length: 12
Connection: close
Content-Type: text/html

Hello world!
*/
```

- `stream_socket_client` 函数用于与服务器建立连接，并返回分配给 $stream 的连接句柄资源。 
- `tcp://` 指定要使用的传输协议。 
- `localhost.example` 是服务器的主机名。 
- `:80` 指定连接服务器的端口，这里使用 80，因为它是 HTTP 的标准端口。使用的端口取决于 Web 服务器的配置。 
- `$request` 包含要发送到服务器的请求，其中各行之间以 CRLF 序列分隔（参见第 2 章“GET 请求”），并且请求以双 CRLF 序列结束（实际上是一个空行），以指示服务器请求已结束。请注意，请求*必须*包含结束序列，否则 Web 服务器将一直挂起等待请求的其余部分。 
- `fwrite` 函数用于通过由 $stream 表示的已建立连接传输请求。
- `stream_get_contents` 函数用于从连接中读取所有可用数据，在本例中即是对请求的响应。
- `fclose` 函数用于显式终止连接。

根据项目的性质和需求，可能无法一次性知晓请求的所有方面。在这种情况下，理想的做法是将请求元数据封装在关联数组或对象等数据结构中。然后，可以使用一个中心逻辑单元来读取这些元数据，并基于此以字符串形式构建请求。

如上文示例所示，手动在字符串内构建请求在可读性方面也不是理想的。如果已知确切的请求且请求不会变化，另一种方法是将它们存储在某种类型的数据源中，然后在运行时重新检索它们，并按原样通过连接发送。是否可能采取这种方法取决于 Web 抓取应用程序与目标应用程序之间请求的变异程度。

如果需要手动构建查询字符串或 URL 编码的 POST 请求体，可以使用 `http_build_query` 函数通过关联数组来实现。

### 解析响应

一旦收到响应，下一步就是从其中获取所需的数据。以上一个示例中的响应为例，让我们看看这可能是什么样子。

```php
<?php
// Split the headers and body into separate variables
list($headers, $body) = explode("\r\n\r\n", $response, 2);

// Remove the status line from the headers
list($status, $headers) = explode("\r\n", $headers, 2);

// Parse the headers segment into individual headers
preg_match_all(
    "/(?P<name>[^:]+): (?P<value>[^\r\n]+)(?:$|\r\n[\t ]*)/U",
    $headers,
    $headers,
    PREG_SET_ORDER
);
?>
```

分离单个标题的逻辑必须考虑标题值跨越多行的可能性，这符合 RFC 2616 第 2.2 节的规定。因此，这里使用 `preg_match_all` 来分离单个标题。有关正则表达式的更多信息，请参阅后面关于 PCRE 的章节。如果情况需要解析包含在 URL 和查询字符串中的数据，请查看 `parse_url` 和 `parse_str` 函数。与请求一样，通常希望将响应数据解析为数据结构，以便于引用。

#### 传输编码

在解析正文之前，应检查标题的几项内容。如果存在 Transfer-Encoding 标题且其值为 chunked，则表示服务器是分块而不是一次性发送响应的。这样做的优点是服务器不必等到整个响应组合完毕后才开始返回它（以便确定并在 Content-Length 标题中包含其长度），这可以增加整体的服务器吞吐量。

当发送每个块时，前面会有一个十六进制数来表示块的大小，后跟一个 CRLF 序列。每个块的结尾也由一个 CRLF 序列表示。正文的结尾由大小为 0 的块表示，在使用持久连接时这一点尤为重要，因为客户端必须知道一个响应在哪里结束，下一个响应从哪里开始。

可以使用 `strstr` 函数获取字符串中换行符之前的字符。要将包含十六进制数的字符串转换为对应的十进制值，请参见 `hexdec` 函数。下方包含了一个这两个函数实际运行的示例。该示例假设请求正文已被写入字符串中。

```php
<?php
$chunked = '';
do {
    if ($length = hexdec(strstr($body, "\r\n", true))) {
        $body = ltrim(strstr($body, "\r\n"));
        $chunked .= substr($body, 0, $length);
        $body = substr($body, $length + 2);
    }
} while ($length > 0);
```

有关分块传输编码的更多信息，请参见 RFC 2616 第 3.6.1 节和附录 19.4.6。

#### 内容编码

如果加载了 zlib 扩展（可以通过 extension_loaded 函数或从命令行执行 `php -m` 进行检查），客户端可以选择在请求中包含一个值为 `gzip, deflate` 的 `Accept-Encoding` 标题。如果服务器支持内容压缩，它将在响应中包含一个 `Content-Encoding` 标题，其值指示它在发送之前对响应正文使用了这两种压缩方案中的哪一种。

这样做的目的是减少发送的数据量，从而降低带宽消耗并提高吞吐量（假设压缩和解压缩花费的时间少于数据传输，这通常是实际情况）。收到响应后，客户端必须使用服务器用于压缩响应的原始方案对响应进行解压缩。

```php
<?php
// If Content-Encoding is gzip...
$decoded = gzinflate(substr($body, 10));

// If Content-Encoding is deflate...
$decoded = gzuncompress($body);
?>
```

- 是的，函数名称是正确的。人们可能会认为使用 `deflate` 编码方案编码的正文应该使用 `gzinflate` 来解码。显然，这只是 zlib 库使用的命名方案中的一个怪癖。
- 当编码方案为 `gzip` 时，响应中会包含一个 GZIP 头部。`gzinflate` 对此响应不佳。因此，在将正文传递给 `gzinflate` 之前，会先去除该头部（包含在正文的前 10 个字节中）。

有关内容编码的更多信息，请参见 RFC 2616 第 3.5 节。RFC 1951 介绍了 `deflate` 编码方案所基于的 DEFLATE 算法的具体细节，而 RFC 1952 则详细说明了 `gzip` 编码方案所基于的 `gzip` 文件格式。

#### 时间控制

每当 Web 服务器接收到一个请求时，都会创建或复用一个以进程或线程形式的独立执行流来处理该请求。如果不加控制，这可能会消耗服务器上的所有资源以应对大量的请求负载。因此，Web 服务器通常会限制其可以并发处理的请求数量。超过此限制请求将被阻塞，直到服务器完成已分配资源现有的请求为止。长时间未得到服务的请求最终会超时。

“节流”是一个术语，用于描述客户端向服务器发送过多请求，导致其消耗可用资源池，从而延迟或阻止请求处理（包括客户端自己最后发送的请求）的情况。显然，出于两个原因，避免这种行为是理想的：1) 这可以被视为滥用行为，并可能导致你的 IP 被禁止访问服务器；2) 这阻碍了客户端保持持续的功能正常。

大多数 Web 浏览器在加载特定资源及其依赖项时，每个域名最多建立四个并发连接。因此，这是测试托管目标应用程序的服务器负载的良好起点。在可能的情况下，测量单个请求的响应时间，并将其与并发发送的请求数量进行比较，以确定服务器能承受多大的负载。

根据应用程序的情况，与目标应用程序进行实时交互可能不是必需的。如果与目标应用程序及其处理数据的交互仅限于你的 Web 抓取应用程序的用户群，则可能可以在需要时检索数据，将其本地缓存，在本地存储修改，并在非高峰时段以批量方式将它们推送到目标应用程序。要确定这些时段是哪些，请观察请求发出时间与响应时间的关系，以找到响应时间 consistently 较高的时段。




## 第 9 章

### Tidy 扩展

至此，你应该已经完成了网络爬虫流程中的检索阶段，原始的响应体已准备就绪，等待进一步分析。恭喜你在整个过程中达到了半程里程碑。

虽然其他响应格式也是可能的，但你极有可能正在处理基于标记的语言，例如 **HTML** 或 **XHTML**。因此，本章及后续章节将专门讨论这些格式。通常情况下，所使用的语言是 HTML。

有许多可用的专注于 XML 的 PHP 扩展可以处理标记语言，这些将在后续章节中审查。虽然这些扩展确实提供了一些对 HTML 的支持，并且在处理格式错误的标记时也有一定的宽容度，但格式良好的 XHTML 才是它们的理想输入。鉴于此，分析过程的第一步是对响应体进行必要的清理，以最大程度地减少在后续分析过程中可能遇到的问题数量。

### 验证

万维网联盟（W3C）提供了一个标记验证服务，旨在促进对 Web 标准的遵守。你可以通过访问 `http://validator.w3.org` 来访问此服务。它接受通过 URL、文件上传或直接输入方式提交的标记进行测试。这将让你了解你的文档是否存在标记格式问题，如果存在的话，具体是什么问题。

### Tidy

清理标记格式错误有两种方式。一种是手动方式，涉及使用基本的字符串操作函数或正则表达式函数，但这种方式很快就会变得杂乱且难以管理。另一种方式更为自动化，涉及使用 tidy 扩展来定位和修正标记问题。虽然这个过程是可配置的，但显然它缺乏手动处理时的那种细粒度控制。

本章的大部分内容将侧重于使用 tidy 来修正标记问题。对于那些 tidy 无法令你满意地处理的问题，前面提到的涉及字符串和正则表达式函数的方法是你的替代方案。正则表达式将在后续章节中更详细地介绍。

tidy 扩展提供两种 API 风格：过程式和面向对象的。两者提供的功能大多等效（相关差异将在后文说明），选择使用哪一种纯属个人偏好。尽管两种 API 风格都使用 tidy 类的对象，但为了语法的一致性，建议在可行范围内尽量只使用一种风格。本章中的代码示例将同时使用这两种风格。

### 输入

在修正一组标记数据中的标记问题之前，必须将数据解析到一个 tidy 对象中。通常情况下，当标记数据准备被解析时，它已经包含在一个字符串中，但也可能存储在一个外部文件中。请参阅下文，了解如何处理这两种情况的示例。

```php
<?php
// 过程式
$tidy = tidy_parse_string($string, $config);
$tidy = tidy_parse_file($filename, $config);

// 面向对象
$tidy = new tidy;
$tidy->parseString($string, $config);
$tidy->parseFile($filename, $config);
?>
```

### 配置

与 cURL 扩展类似，tidy 扩展在很大程度上依赖于配置概念；因此，上述示例中的所有调用都包含 $config 参数。与大多数其他扩展不同，此参数实际上可以是两种形式之一：一个由设置-值对组成的关联数组，或者指向外部配置文件的路径。

配置文件格式与 CSS 样式表中的单独样式设置有些相似。一个示例如下所示。非开发人员不太可能需要访问这些配置设置，也不会像使用 tidy 访问 PHP 源代码那样访问它们。因此，将配置分离到外部配置文件中，其唯一的作用实际上是为了避免使源代码被设置项弄乱。此外，由于配置文件是从磁盘读取的，在高使用率下可能会带来性能方面的顾虑。

```
// 单行注释
/* 多行注释 */
indent: false /* 设置: 值 */
wrap: 78
```

当使用面向对象的 API 时，使用配置文件的替代方案是子类化 tidy 类，并覆盖其 parseString 和 parseFile 方法，以自动包含特定的配置设置值。这种方法允许轻松复用 tidy 配置。

```php
<?php
class mytidy extends tidy {
    private $._default = array(
        'indent' => false,
        'wrap' => 78
    );
```

```php
public function parseFile($filename, $config, $encoding, $use_include_path=false) {
    return parent::parseFile(
        $filename,
        array_merge($this->_default, $config),
        $encoding,
        $use_include_path
    );
}

public function parseString($filename, $config, $encoding, $use_include_path=false) {
    return parent::parseString(
        $filename,
        array_merge($this->_default, $config),
        $encoding,
        $use_include_path
    );
}
?>
```

- `array_merge` 用于将 `$_default` 属性中的默认参数值合并到指定的 `$config` 数组中。在原始 `$config` 数组中指定的任何参数都将优先于在 `$_default` 中指定的对应参数。
- `parseFile` 和 `parseString` 将修改后的 `$config` 参数以及其他提供的参数传递到 tidy 类中各自的方法，并返回相应的返回值。

### 选项

Tidy 包含大量配置选项，其中只有少数几个与本书的上下文相关。

两个选项涉及适用于网络爬虫的输出格式：`output.html` 和 `output.xhtml`。两者都指定为布尔值。这些选项是互斥的，意味着在任何给定时间只能将其中一个设置为 `true`。通常 `output.xhtml` 更可取，但可能并不总是可行。重要的是将 tidy 的输出与原始文档进行比较，以确认修正文档格式错误没有导致数据丢失。

根据使用时的配置，文档编码可能是后来会出现问题的领域之一。例如，XMLReader 扩展内部使用 UTF-8 编码，如果你的输入文档的编码与此冲突，可能会产生问题。`input-encoding` 和 `output-encoding` 可用于控制各自的假设编码。

其他选项主要用于调试目的，在生产环境中通常应将其关闭。这是一个子类化 `tidy` 类以控制默认选项值的好理由，以便可以轻松访问两组不同的配置，用于不同的开发环境。

这三个选项是 `indent`、`indent-spaces` 和 `indent-attributes`。其中的第一个，`indent`，是一个布尔值，指示 tidy 是否应应用缩进，以使元素之间的层级关系在视觉上更突出。`indent-spaces` 是一个整数，表示用于表示单级缩进的空格字符数量，默认为 2。最后，`indent-attributes` 是一个布尔值，指示元素内的每个单独属性是否应在新行开始。

说到属性，`sort-attributes` 可以设置为 `alpha`，以便按字母顺序对元素属性进行排序。默认设置为 `none`，这将禁用排序。

如果文档中的行往往很长且难以阅读，`wrap` 选项可能很有用。它是一个整数，表示 tidy 在强制换行前每行应允许的最大字符数。默认设置为 68，可以将其设置为 0 来完全禁用。

没有空行来分隔代码块也可能使标记难以阅读。`vertical-space` 是一个布尔值，旨在通过添加空行来提高可读性。默认情况下它是禁用的。

### 调试

尽管 tidy 做得很好，但它并不总能清理文档。当使用 tidy 修复文档时，检查其遇到的问题是通常是个好主意。




### 警告和错误

在使用 tidy 进行网络抓取分析时，需要检查两类问题：警告和错误。与它们的 PHP 对应物类似，警告是非致命的，并且通常有某种自动化响应，tidy 会执行以处理它们。错误不一定是致命的，但表明 tidy 可能无法处理某个特定问题。

所有问题都会根据其类型存储在一个错误缓冲区中。访问该缓冲区内的信息及其相关信息，是 tidy 扩展的过程式和面向对象 API 之间存在差异的一个领域。

```php
<?php
// 过程式
$issues = tidy_get_error_buffer($tidy);

// 面向对象
$issues = $tidy->errorBuffer;
?>
```

请注意，`errorBuffer` 是 `$tidy` 对象的一个属性，而不是方法。还要注意，过程式函数和对象属性之间的命名约定略有不同，这与 API 其他大多数区域保持一致的做法形成了对比。

字符串中包含的错误缓冲区本身几乎没什么用。下面是一个代码示例，它源自 PHP 手册页面上关于 `tidy_get_error_buffer` 函数的用户贡献评论。这会将每个问题的各个组件解析到数组中，以便于访问。

```php
<?php
preg_match_all(
        '/^(?:line (?:P<line>\d+) column (?:P<column>\d+) - ?)' .
        '(?:P<type>\S+): (?:(?:(?:\d+\.?){4}):)?(?:P<message>.*)?$/m',
        $tidy->errorBuffer, // 或 tidy_get_error_buffer($tidy)
        $issues,
        PREG_SET_ORDER
);

print_r($issues);
/*
示例输出：
Array
(
    [0] => Array
        (
            [0] => line 12 column 1 - Warning: <meta> element not
                empty or not closed
            [line] => 12
            [1] => 12
            [column] => 1
            [2] => 1
            [type] => Warning
            [3] => Warning
            [message] => <meta> element not empty or not closed
            [4] => <meta> element not empty or not closed
        )
)
*/
?>
```

tidy 扩展还提供了一种方法来获取遇到的警告和错误数量，而不需要手动解析错误缓冲区。不幸的是，而且有些奇怪的是，这只在过程式 API 中受到支持。然而，通过子类化 tidy 类将其添加到面向对象 API 中是相当简单的。两者的示例如下所示。

```php
<?php
// 过程式
$warnings = tidy_warning_count($tidy);
$errors = tidy_error_count($tidy);

// 面向对象
class mytidy extends tidy {
    public function warningCount() {
        return tidy_warning_count($this);
    }
    public function errorCount() {
        return tidy_error_count($this);
    }
}
?>
```

#### 输出

获取 tidy 修复文档后的结果输出相当简单。

```php
<?php
// 过程式
$output = tidy_get_output($tidy);

// 面向对象
$output = (string) $tidy;
?>
```

虽然面向对象 API 没有公开声明魔术方法 `__toString`，但它也可以强制转换为字符串，也可以使用 `echo` 语句直接输出。

#### 总结

本章到此结束。此时，你应该已经将获得的文档转换为适合输入到 XML 扩展的格式。接下来的几章将专门介绍如何使用特定的扩展从修复后的文档中搜索和提取数据。

有关 tidy 扩展的 PHP 手册部分，请访问 http://php.net/tidy。

有关 tidy 库本身的文档，请访问 http://tidy.sourceforge.net/#docs。

有关 tidy 配置设置参考，请访问 http://tidy.sourceforge.net/docs/quickref.html。

### 第 10 章

### DOM 扩展

一旦检索到的标记文档被清理并通过验证，下一步就是从中提取有用的数据。为此，理想的方法是利用文档是有效标记这一事实，并应用一个 XML 扩展。PHP 有几种这样的扩展，接下来的几章将专门介绍它们。

本章的同名主题是文档对象模型（DOM）扩展。该扩展的名称来源于一种标准化的、语言无关的 API，用于导航和操作有效的、格式良好的 XML 和 HTML 文档。该标准由致力于新兴互联网相关标准的万维网联盟（W3C）维护并推荐。本章不会全面覆盖 DOM 扩展，仅涉及与网络抓取相关且必不可少的部分。

> **注意：DOM XML**
> DOM 扩展仅在 PHP 5 中可用。其 PHP 4 兼容的前身 DOM XML 扩展具有略微不同的 API，但共享许多相同的概念。本章的示例将仅限于 DOM 扩展。有关 DOM XML 扩展的等效细节，可以参考 PHP 手册的相关章节，请访问 http://php.net/manual/en/book.domxml.php。

在继续深入之前，你应该知道有两种类型的 XML 解析器：**树解析器**和**拉取解析器**。树解析器将整个文档加载到内存中，允许你在任何时候访问其任何部分并进行操作。拉取解析器逐块读取文档，并限制你只能处理当前正在读取的部分。

这两种类型的解析器共享类似 `file_get_contents` 和 `fgets` 函数之间的关系：前者允许你一次处理整个文档，并使用存储它所需的任何内存，而后者允许你一次处理文档的一部分，并在过程中使用更少的内存。

在处理相当大的文档时，较低的内存使用率通常是更可取的选择。试图一次性将巨大的文档加载到内存中，对本地系统的影响与限制客户端对 Web 服务器的影响相同：在这两种情况下，资源都被消耗，系统性能都会因压力而减弱，直到系统最终锁死或崩溃。

DOM 扩展是一个树解析器。一般来说，网络抓取并不要求能够同时访问文档的所有部分。然而，使用拉取解析器实现网络抓取所涉及的数据提取类型可能相当复杂。选择哪种扩展取决于文档的大小和复杂度。

### 加载文档

DOMDocument 类是开始使用 DOM 扩展的地方。首先要做的是实例化它，然后输入已验证的标记数据。请注意，如果加载的文档无效或格式良好，DOM 扩展在加载文档时会产生警告。为了避免这种情况，请参见上一章中关于使用 tidy 扩展的内容。如果 tidy 未能消除问题，错误可以按照下面的示例进行控制。请注意，错误会被缓冲直到手动清除，因此如果不再需要它们，请在每次加载操作后清除它们，以避免浪费内存。

```php
<?php
// 缓冲 DOM 错误，而不是将其作为警告发出
$oldSetting = libxml_use_internal_errors(true);

// 实例化一个文档容器
$doc = new DOMDocument;

// 加载已包含在字符串中的标记
$doc->loadHTML($htmlString);

// 加载保存到外部文件的标记
$doc->loadHTMLFile($htmlFilePath);

// 获取所有错误（如果需要）
$errors = libxml_get_errors();

// 只获取最后一个错误
$error = libxml_get_last_error();

// 清除来自先前操作的任何现有错误
libxml_clear_errors();

// 将错误缓冲恢复到其先前的设置
libxml_use_internal_errors($oldSetting);
?>
```

### 树术语

一旦文档被加载，下一个自然的步骤就是从中提取所需的数据。然而，这样做需要对 DOM 的结构有更深入的了解。回想之前提到的树解析器。如果你有任何计算机科学背景，你会很高兴地知道，在树解析器的语境中，“树”一词确实指的是同名数据结构。如果没有，以下是相关概念的简要说明。

**树**是一种分层结构（想想家谱），由**节点**组成，这些节点在 DOM 扩展中作为 `DOMNode` 类存在。节点之于树，就像元素之于数组：只是存在于数据结构中的项目。

每个单独的节点可以有零个或多个**子节点**，这些子节点在 `DOMNode` 类中由 `childNodes` 属性集体表示。`childNodes` 是类 `DOMNodeList` 的一个实例，这听起来正是它的样子。其他相关的 proper-


这些属性包括 `firstChild` 和 `lastChild`。**叶子节点**是指没有子节点的节点，可以使用 `DOMNode` 的 `hasChildNodes` 方法进行检查。

树中的所有节点都有一个单一的**父节点**，唯一的例外是**根节点**，树中的所有其他节点都源于该根节点。如果两个节点共享同一个父节点，它们就被恰当地称为**兄弟节点**。这种关系体现在 `DOMNode` 的 `previousSibling` 和 `nextSibling` 属性中。

最后，某节点的子节点、这些子节点的子节点，依此类推，统称为**后代节点**。同样地，某节点的父节点、该父节点的父节点，依此类推，统称为**祖先节点**。

一个示例可能有助于展示这些术语。

```html
<html>
<body>
<ul id="thelist">
<li>Foo</li>
<li>Bar</li>
</ul>
</body>
</html>
```

- `html` 是根节点。
- `body` 是 `html` 的第一个（也是唯一的）子节点。
- `ul` 是 `body` 的第一个（也是唯一的）子节点。
- 包含**Foo**和**Bar**的 `li` 节点分别是 `ul` 的第一个和最后一个子节点。
- 包含**Bar**的 `li` 节点是包含**Foo**的 `li` 节点的下一个兄弟节点。
- 同样，包含**Foo**的 `li` 节点是包含**Bar**的 `li` 节点的上一个兄弟节点。
- `ul` 和 `li` 节点是 `body` 节点的后代。

### 元素和属性

至此，DOM 超越了树的类比。存在多种类型的节点，或者用 DOM 扩展的语境来表达，即 `DOMNode` 拥有多个子类。您主要将要处理的是用于**元素**的 `DOMElement` 和用于**属性**的 `DOMAttr`。以下是这些概念在上节示例中的具体应用。

- `ul` 是一个元素的名称。
- `id` 是 `ul` 元素的一个属性的名称。
- `thelist` 是 `id` 属性的值。
- `Foo` 和 `Bar` 是 `li` 元素的值。

#### 定位节点

`DOMDocument` 类的两种方法允许您相对快速地减少需要遍历的节点数量，以找到您想要的数据。

`getElementById` 试图定位满足两个条件的单个元素：1) 它是文档根元素的后代；2) 它具有给定的 `id` 属性值。如果找到这样的元素，则作为 `DOMElement` 实例返回；否则，返回 `null`。

`getElementsByTagName` 试图定位满足两个条件的所有元素：1) 它是文档根元素的后代；2) 它具有给定的元素名称（例如 `ul`）。此方法始终返回找到的任意元素的 `DOMNodeList`。`DOMNodeList` 类有一个 `length` 属性，如果未找到任何元素，该属性将等于 0。它也是可迭代的，因此可以作为 `foreach` 循环的主题使用。

`DOMElement` 类也有一个 `getElementsByTagName` 方法，其功能相同，只是定位到的元素将是该元素的后代，而不是文档根元素的后代。

```php
<?php
// 获取上一示例中列表项的一种方法
$listItems = $doc->getElementsByTagName('li');

// 一种更具体的方法（如果有多个列表时更好）
if ($list = $doc->getElementById('thelist')) {
	$listItems = $list->getElementsByTagname('li');
}

// 另一种方法，如果列表没有 id
$lists = $doc->getElementsByTagname('ul');
if ($lists->length) {
	$list = $lists->item(0);
	$listItems = $list->getElementsByTagname('li');
}

// 输出 "thelist"（不带引号）
echo $list->getAttribute('id');

// 第一行输出 "Foo"，第二行输出 "Bar"
foreach ($listItems as $listItem) {
	echo $listItem->nodeValue, PHP_EOL;
}

// 输出 <ul id="thelist"> 和 </ul> 内的文本内容
echo $list->nodeValue;
?>
```

### XPath 和 DOMXPath

类似于正则表达式允许在字符串中找到字符模式的实例，XPath 允许在 XML 兼容的文档中找到节点模式的实例。这两种技术都是通过提供由**元字符**组成的语法来实现其目的的，从而以简洁明了的方式表达这些模式。在 DOM 扩展中，XPath 标准的 1.0 版本支持是作为**DOMXPath** 类实现的。

**DOMXPath** 构造函数有一个必需的参数：现有的**DOMDocument** 实例，查询将在该实例上执行。**DOMXPath** 还有两个相关的方法：evaluate 和 query。这两个方法的第一参数都是包含 XPath 表达式的字符串，用于查询文档。

可选地，可以与文档相关联的 **DOMNode** 实例可以作为第二个参数（$contextNode）传递给任一方法。当指定时，该节点将成为**上下文节点**，查询结果将被限制在该节点及其后代中。否则，假设文档的根元素为上下文节点。

*evaluate* 和 *query* 之间的区别在于，后者始终返回 *DOMNodeList* 的实例，而前者在仅找到一个结果时会尝试返回适当类型的结果。

#### 绝对寻址

使用 XPath 表达式获取该表达式应用的一组节点的过程被称为**寻址**。本章的其余部分将介绍寻址的各个方面以及相关表达式语法。

XPath 表达式与 UNIX 文件系统路径有几个相似之处，两者都用于遍历概念上的树结构。请参阅下面的具体实例。此处重新使用了上文中用于说明标记语言各种概念的 HTML 示例，以展示 XPath 寻址。

```php
<?php
// 加载一个标记文档
$doc = new DOMDocument;
$doc->loadHTML('
<html>
<body>
<ul id="thelist">
<li>Foo</li>
<li>Bar</li>
</ul>
</body>
</html>
');

// 配置用于查询文档的对象
$xpath = new DOMXPath($doc);

// 返回仅包含 html 节点的 DOMNodeList
$list = $xpath->query('/html');

// 返回仅包含 body 节点的 DOMNodeList
$list = $xpath->query('/html/body');

// 同样返回仅包含 body 节点的 DOMNodeList
$list = $xpath->query('//body');
?>
```

- 在前两个示例中请注意，即使在查询调用中未指定其他节点作为第二个参数（这意味着假设根节点（html）为上下文节点），根元素（html）也在表达式中被引用。
- 一个**单斜杠** / 表示父子关系。`/html/body` 寻址文档根 html 元素的所有作为子节点的 body 节点（在此情况下仅产生单个结果）。
- 一个**双斜杠** // 表示祖先后代关系。`//body` 寻址上下文节点的所有后代 body 节点（同样仅产生单个结果）。

单斜杠和双斜杠运算符可以多次使用，并如以下所示相互组合。

```php
<?php
// 返回所有作为 body 节点后代的 ul 节点
$list = $xpath->query('//body/ul');

// 返回所有作为 ul 节点子节点的 li 节点
$list = $xpath->query('//body/ul/li');
?>
```

### 命名空间

如果您尝试通过元素名称寻址节点，但本应得到结果时却未收到，有可能文档正在对节点进行命名空间处理。解决此问题的最简单方法是用条件替换元素名称。
例如，如果您使用的表达式是 `ul`，则忽略命名空间的等效表达式将是 `*[name()="ul"]`，其中 `*` 是所有节点的通配符，`name` 函数将节点名称与给定值进行比较。

#### 相对寻址

上述示例使用所谓的**绝对寻址**，其概念类似于绝对文件系统路径。下一个示例涵盖使用*相对寻址*。

```php
<?php
// 返回所有具有 li 子节点的 ul 节点
$list = $xpath->query('/body//ul/li/..');
?>
```

其中 `/body//ul/li` 选择 `li` 节点，而 `/body//ul/li/..` 通过使用相对寻址（具体来说是 `..`）选择 `ul` 节点，这表明应返回寻址节点（`li`）的父节点，而不是寻址节点本身。请将其与在 UNIX 文件系统中使用相同序列引用当前目录的父目录进行比较。

#### 寻址属性

迄今为止的示例主要处理的是元素节点。XPath 也支持属性节点的选择。

```php
<?php
// 返回所有 ul 节点的 id 属性节点
$list = $xpath->query('//ul/@id');

// 返回所有具有 id 属性节点的 ul 节点
$list = $xpath->query('//ul/@id/..');

// 返回所有 id 属性节点
$list = $xpath->query('//@id');
?>
```

- `/ul/@id` 寻址与作为上下文节点后代的 `ul` 元素节点相关联的所有 `id` 属性节点。
- 请注意第二个示例中相对寻址的使用如何同样适用于属性节点，就像它适用于子元素节点一样。



-   `/@id` 寻址上下文节点的所有 `id` 属性节点，无论它们关联于哪个元素。

#### 并集

在寻址节点时，可以使用多个表达式执行单个查询。这被称为寻址这些表达式的**并集**。

```php
<?php
// 返回所有 ul 和 ol 节点的 li 子节点
$list = $xpath->query('//ol/li|//ul/li');
// 返回所有 tr 节点的 th 和 td 节点
$list = $xpath->query('//tr/th|//tr/td');
?>
```

-   第一个示例返回无序（**ul**）列表和有序（**ol**）列表中所有的列表项（**li**）。
-   第二个示例返回表格行（**tr**）中所有的表头（**th**）和数据（**td**）单元格。

#### 条件

除了其周围的层级结构外，还可以基于**条件**来寻址节点。

```php
<?php
// 返回具有 id 属性节点的所有 ul 节点
$list = $xpath->query('//ul[@id]');

// 返回 id 为 "thelist" 的 ul 节点的所有 li 子节点
$list = $xpath->query('//ul[@id = "thelist"]/li');

// 返回上下文节点的第一个 ul 后代节点
$list = $xpath->query('//ul[1]');

// 返回每个 ul 节点的第一个 li 子节点
$list = $xpath->query('//ul/li[1]');

// 返回包含值为 "foo"bar" 的 li 节点的所有 ul 节点
$list = $xpath->query('//ul[li = "foo"bar]');
?>
```

-   方括号用于界定条件表达式。
-   在条件内部，元素和属性节点的表示方式与在条件外部相同。也就是说，元素仅通过元素名称引用，而属性名称前缀为 @。
-   = 运算符用于相等性比较。反之，!= 运算符用于检查不等性。还支持其他一些标准的比较运算符，包括 <、<=、> 和 >=。
-   仅由单个数字组成的条件实际上是 position() = # 的简写形式，其中 # 是使用的数字。position 是一个函数，返回当前上下文中每个单独节点的位置。

# 资源

这里只涵盖了 XPath 提供功能的一小部分，主要是基本概念以及在使用 XPath 从检索到的标记文档中提取数据时最可能适用的领域。其他函数、运算符以及更高级的概念在本章末尾引用的资源中有更详细的说明。为了进行更广泛和更复杂的数据提取应用程序，强烈建议查阅这些资源。

-   PHP 手册中的 DOM 文档：http://php.net/dom
-   XML 和 XPath 的优秀概述：http://schlitt.info/opensource/blog/0704_xpath.html
-   XML 的更多信息：http://en.wikibooks.org/wiki/XML:_Managing_Data_Exchange
-   DOM 第三级核心标准：`http://www.w3.org/TR/DOM-Level-3-Core`
-   DOM 第三级 XPath 标准：`http://www.w3.org/TR/DOM-Level-3-XPath`

## 第 11 章

### SimpleXML 扩展

与 DOM 扩展一样，SimpleXML 扩展也提供了一个树解析器。然而，DOM 扩展保持其 API 与其基于的标准非常一致。与 DOM 扩展的 API 相比，SimpleXML 提供的 API 对大多数 PHP 开发者来说更少、更直观且更易于使用。

SimpleXML 通过使用 PHP 数组来访问具有相同元素名的集合中的单个元素以及元素属性，利用了 PHP 数组的灵活性和多功能性。它还使标记文档具有可迭代性，使其遍历变得简单。

然而，这些优势并非没有代价。与其他树解析器一样，SimpleXML 必须解析整个文档后才能使用。因此，在解析比 XMLReader（稍后将介绍）这样的拉取解析器更大的文档时，它往往速度较慢。但对于处理较小文档的脚本而言，SimpleXML 在紧急情况下工作得很好。

### 加载文档

在 DOM 扩展中，DOMDocument 是核心类，而 SimpleXMLElement 是 SimpleXML 扩展中的对应类。加载标记文档只需通过类构造函数指定即可。

```php
<?php
// 加载已包含在字符串中的标记
$exe = new SimpleXMLElement($markupString);

// 加载包含在外部文件中的标记
$exe = new SimpleXMLElement($filePath, null, true);
?>
```

构造函数的第二个参数（在上述第二个示例中指定为 null）允许对该实例进行进一步配置。对于标记不太有效的文档，将此参数的值设置为 LIBXML_NOERROR | LIBXML_NOWARNING 可能很有用，因为它会抑制错误和警告报告。

最后，第二个构造函数调用中使用的第三个参数设置为 true，以指示 $filePath 实际上是包含标记的文件路径，而不是标记本身。

#### 访问元素

使用 SimpleXML 看起来有点像是 XPath 表达式，除了通过 API 以编程方式实现相同的效果，而不是通过存储在字符串中的格式化表达式。与 XPath 表达式不同，SimpleXML 自动假设元素访问是相对于根节点的。

```php
<?php
$markupString = '
<html>
<body>
<ul id="thelist">
<li>Foo</li>
<li>Bar</li>
</ul>
</body>
</html>
',

// 输出 "Foo" -- 注意未引用 "html" 元素
$exe = new SimpleXMLElement($markupString);
echo $exe->body->ul->li[0];

// 也有效，如果存在多个 "li" 元素，则假设第一个 "li" 元素
echo $sxe->body->ul->li;

// 也输出 "Foo" -- 注意这次引用了 "html"
$doc = new DOMDocument();
$doc->loadHTML($markupString);
$xpath = new DOMXPath($doc);
echo $xpath->evaluate('/html/body/ul/li[0]');

// 输出 "ul"
echo $sxe->body->ul->getName(), PHP_EOL;

// 输出 "Foo" 然后 "Bar"
foreach ($sxe->body->ul->li as $li) {
    echo $li, PHP_EOL;
}

// 做同样的事
foreach ($sxe->body->ul->children() as $li) {
    echo $li, PHP_EOL;
}
?>
```

当引用当前元素的子元素时（例如通过上述 $sxe 的 body 属性），请注意正在访问的子元素也是 SimpleXMLElement 的一个实例。这意味着不仅可以链接元素访问，还可以使用变量引用此类链接中的最后一个元素。参见上述第一个 foreach 循环作为这两点的示例。

#### 访问属性

在访问元素时，对于访问同一层级上具有相同名称的多个元素使用枚举数组，而在访问属性时使用关联数组。以下示例使用与上一个示例相同的 $markupString 样本数据。

```php
<?php
// 输出 "thelist"
echo $sxe->body->ul['id'];

// 输出 "id=thelist"
foreach ($sxse->body->ul->attributes() as $name => $value) {
    echo $name, '=', $value, PHP_EOL;
}

// 另一种输出 "thelist" 的方法
$attrs = $sxse->body->ul->attributes();
echo $attrs->id;
?>
```

attributes() 方法实际返回的是一个 SimpleXMLElement 实例，该实例以 SimpleXMLElement 通常使子元素及其值可用的方式提供对属性名称和值的访问。因此，返回的实例可以作为 foreach 循环的主题，以迭代它公开的属性。

```
<!-- 实际标记 -->
<ul id="thelist"></ul>

<!-- attributes() 如何将其作为 SimpleXMLElement 实例公开 -->
<ul>
    <id>thelist</id>
</ul>
```

![](img/1e839861f06c77df9ecabc0aed9127b5_135_0.png)

### 一个调试缺陷

影响 SimpleXML 扩展的缺陷 #44973 报告称存在于 PHP 5.2.6 中，并且可能存在于其他版本中。当尝试使用 echo、print_r()、var_dump() 和其他类似函数通过 SimpleXMLElement 实例访问并输出节点时，会暴露此缺陷。如果节点同时具有属性和文本值，这些函数的输出中不会显示属性。这并不意味着在这种情况下属性值无法访问；只是它们无法以这种方式输出，除非直接引用。有关此问题的更多信息，请访问 http://bugs.php.net/bug.php?id=44973。





#### 比较节点

要将元素或属性与字符串值进行比较，必须首先将其显式转换为字符串。否则，它们将被视为对象，这可能导致类型问题，包括引发错误。

```php
<?php
if ((string) $sxe->body->ul['id'] = 'thelist') {
    echo htmlspecialchars((string) $sxe->body->ul['id']);
}
?>
```

#### DOM 互操作性

由于 DOM 和 SimpleXML 扩展都是树解析器，因此两者之间具有一定的互操作性。在重构旧代码时，如果您偏好使用其中一种扩展，这可能会很有用；或者，如果您在单个应用程序中同时有使用这两种扩展的用例。

```php
<?php
// 将 SimpleXMLElement 转换为 DOMElement
$domElement = dom_import_simplexml($simpleXmlElement);

// 将 DOMNode 转换为 SimpleXMLElement
$simpleXmlElement = simplexml_import_dom($domNode);
?>
```

#### XPath

与 DOM 扩展一样，SimpleXML 也支持 XPath。与 DOM 使用单独的类不同，SimpleXMLElement 类本身包含了一个用于此目的的方法。DOMXPath 类的 query() 和 evaluate() 方法返回 DOMNodeList 实例，而 SimpleXMLElement 的 xpath 方法则返回一个枚举数组，其中包含与给定 XPath 表达式匹配的 SimpleXMLElement 实例。

```php
<?php
// 返回前一个示例中所有列表项
$elements = $sxe->xpath('//ul[@id="thelist"]/li');

// 输出 "Foo" 然后输出 "Bar"
foreach ($elements as $li) {
    echo $li, PHP_EOL;
}
?>
```

#### 总结

本章到此结束。希望本章能让您对 SimpleXML 扩展的功能及其易用性有一个很好的了解。需要注意的是，本章并没有展示太多的实际使用示例。通过实验真实世界的数据来学习这一点是最有效的。最终，您将了解何时可以使用 SimpleXML，何时应该优先选择 DOM 作为解决方案。

有关 PHP 手册中的 SimpleXML 文档，请参阅 [http://php.net/manual/en/book.simplexml.php](http://php.net/manual/en/book.simplexml.php)。

### 第 12 章

### XMLReader 扩展

前面两章介绍了两个可用的实现树解析器的 XML 扩展。本章将重点介绍 XMLReader 扩展，它实现了一个拉取解析器。

正如在 DOM 扩展章节中提到的，拉取解析器与树解析器的不同之处在于，它们分段读取文档，而不是将文档一次性加载到内存中。其结果是，拉取解析器通常只会沿一个方向遍历文档一次，需要您自行收集沿途相关的任何数据。

在开始之前，有一点值得注意：XMLReader 的底层库 libxml 内部使用 UTF-8 编码。因此，如果您导入的任何文档（特别是那些使用 tidy 扩展清理过的文档）都经过适当编码，则编码问题将会得到缓解，从而避免编码冲突带来的问题。

> **XML 解析器**
> 正如 PHP 手册中所称，XML Parser 扩展是 XMLReader 的前身，也是 PHP 4 环境的替代方案。与其 XMLReader 扩展的迭代取向不同，其 API 更倾向于事件驱动风格的编程。有关 XML Parser 扩展的更多信息，请参阅 [http://php.net/manual/en/book.xml.php](http://php.net/manual/en/book.xml.php)。

### 加载文档

XMLReader 扩展的核心类是名为 XMLReader 的类。它没有声明构造函数，而是提供两种方法将 XML 数据引入其中。

```php
<?php
// 加载包含在字符串中的文档
$doc = XMLReader::xml($xmlString);

// 从外部文件加载文档
$doc = XMLReader::open($filePath);
?>
```

这两个方法都有两个额外的参数。

第二个参数是一个指定输入文档编码方案的字符串。它是可选的，如果未指定或指定为 null，则默认为 'UTF-8'。此参数的有效值未包含在 PHP 手册中，但可以在底层 libxml2 库的参考文档 [http://www.xmlsoft.org/encoding.html#Default](http://www.xmlsoft.org/encoding.html#Default) 中找到。

第三个参数是一个整数值，可以使用来自 libxml 扩展的常量以位掩码方式设置。这是配置解析器的首选方法，而不是使用已弃用的 setParserProperty() 方法。可以使用位或运算符 | 形成位掩码的具体常量如下所示。它们的描述可以在 [http://php.net/manual/en/libxml.constants.php](http://php.net/manual/en/libxml.constants.php) 中找到。

- LIBXML_COMPACT
- LIBXML_DTDATTR
- LIBXML_DTDLOAD
- LIBXML_DTDVALID
- LIBXML_NOBLANKS
- LIBXML_NOCDATA
- LIBXML_NOENT
- LIBXML_NOERROR
- LIBXML_NONET
- LIBXML_NOWARNING
- LIBXML_NSCLEAN
- LIBXML_XINCLUDE

例如，配置解析器以抑制错误和警告的调用可能如下所示。

```php
<?php
$doc = XMLReader::xml(
    $xmlString,
    null,
    LIBXML_NOERROR | LIBXML_NOWARNING
);
?>
```

### 迭代

XMLReader 实例既充当整个文档的迭代器，也充当当前节点的数据对象，该节点由该迭代器指向。它包含一组只读属性（描述于 [http://php.net/manual/en/class.xmlreader.php#xmlreader.props](http://php.net/manual/en/class.xmlreader.php#xmlreader.props)），这些属性表示当前节点的特性，并随着迭代器位置的变化而更新。

```php
<?php
while ($doc->read()) {
    // ...
}
?>
```

read() 方法试图将迭代器位置移动到下一个节点，并返回一个布尔值以指示是否成功。也就是说，一旦到达文档末尾，它就返回 false。因此，它非常适合用于如上所示的 while 循环中。

### 节点

与其他扩展一样，每个节点都有一个类型，存储在读取器的 nodeType 属性中。您通常感兴趣的类型仍然是元素 (XMLReader::ELEMENT) 和属性 (XMLReader::ATTRIBUTE)，可能还包括文本 (XMLReader::TEXT) 和 CDATA (XMLReader::CDATA) 元素。此外，XMLReader 扩展还有一个用于结束元素（即闭合标签）的节点类型，XMLReader::END_ELEMENT。其重要性将在下一节中变得更加明显。

下面的示例展示了如何将节点类型与适当的常量进行检查。这些常量的列表请参见 [http://php.net/manual/en/class.xmlreader.php#xmlreader.constants](http://php.net/manual/en/class.xmlreader.php#xmlreader.constants)。

```php
<?php
while ($doc->read()) {
    if ($doc->nodeType == XMLReader::ELEMENT) {
        var_dump($doc->localName);
        var_dump($doc->value);
        var_dump($doc->hasValue);
    }
}
?>
```

与其他扩展一样，节点也有名称。有两个属性用于此目的：name 和 localName。前者代表完全限定名称，包括命名空间说明；而后者仅代表节点名称本身，通常这是您想要使用的那个。

### 元素和属性

属性节点可以具有值。当迭代器指向属性节点时，value 属性将填充该节点的值，并且可以使用 hasValue 属性来检查其是否存在。

元素节点可以具有属性。当迭代器指向元素节点时，**hasAttributes** 属性指示是否存在属性，并且可以使用 **getAttribute()** 方法以字符串形式获取属性值。

下面的示例将这两者结合起来，用于解析 HTML 表格中的数据。

```php
<?php
$inTable = false;
$tableData = array();

while ($doc->read()) {
  switch ($doc->nodeType) {
    case XMLREADER::ELEMENT:
      if ($doc->localName == 'table'
          && $doc->getAttribute('id') == 'thetable') {
          $inTable = true;
      } elseif ($doc->localName == 'tr' && $inTable) {
        $row = count($tableData);
        $tableData[$row] = array();
      } elseif ($doc->localName == 'td' && $inTable) {
        $tableData[$row][] = $doc->readString();
      }
      break;
    case XMLREADER::END_ELEMENT:
      if ($doc->localName == 'table' && $inTable) {
        $inTable = false;
      }
      break;
  }
}
?>
```

这展示了拉取解析器和树解析器的主要区别：前者没有层级上下文的概念，只有迭代器当前指向的节点的概念。因此，您必须在需要时创建自己的上下文指示器。

在这个例子中，读取节点时会检查节点类型，任何不是开始元素或结束元素的节点都会被忽略。如果遇到开始元素，则评估其名称 ($doc->localName) 以确认它是表格，并检查其 **id** 属性值 ($doc->getAttribute('id')) 以确认其值为 'thetable'。如果是这样，标志变量 **$inTable** 被设置为 **true**。这用于指代 -



...类到后续 if 分支案例中，指示迭代器指向的节点位于目标表格内部。

当遇到表格行元素时，进入下一个 if 分支。通过检查节点名称和先前设置的 `$inTable` 标志来促进这一过程。当进入该分支时，`$tableData` 数组中的新元素被初始化为空数组。该数组稍后将存储该行中单元格的数据。与 `$tableData` 中该行关联的键存储在 `$row` 变量中。

最后，当遇到表格单元格元素时执行最后一个 if 分支。与行分支类似，此分支检查节点名称和 `$inTable` 标志。如果检查通过，则会将当前节点的值存储在关联于当前表格行的数组中。

这就是 XMLREADER::END_ELEMENT 节点类型发挥作用的地方。一旦到达表格末尾，就不应将更多数据读入数组。因此，如果结束元素名为 'table'，且 `$inTable` 标志当前指示迭代器指向目标表格内的节点，则将该标志设置为 false。由于理论上没有其他表格应拥有相同的 id 属性，因此在后续 while 循环迭代中不会执行任何 if 分支。

如果该表格是文档中唯一感兴趣的表格，将 `$inTable = false;` 语句替换为 `break 2;` 语句是明智的。这将在遇到表格末尾时终止用于从文档读取节点的 while 循环，防止任何进一步的无谓读取操作。

### readString() 可用性

正如 PHP 手册条目中所述，上述示例中使用的 `readString()` 方法仅在 XMLReader 扩展针对特定版本的底层 libxml 库编译时才存在。

如果你的环境中此方法不可用，示例中的替代方案是使用开/关表格单元格检查来切换它们自己的标志（例如 `$inCell`），并为 TEXT 和 CDATA 节点类型添加情况，这些情况会检查该标志，并且当标志设置为 true 时，将 XMLReader 实例的 `value` 属性的内容添加到 `$tableData` 数组中。

#### DOM 互操作

XMLReader 扩展的一个良好特性是 `expand()` 方法，它返回迭代器当前指向的节点对应的 DOM 扩展类对象。例如，元素节点导致此方法返回 DOMElement 实例。

下面的示例说明了前一个示例的修改，并利用这种 DOM 互操作性提供了获取表格单元格内容的 `readString()` 方法的另一种替代方案。

```php
<?php
if ($doc->localName == 'td' && $inTable) {
    $node = $doc->expand();
    $tableData[$row][] = $node->nodeValue;
}
?>
```

#### 关闭文档

在对文档执行所有必要的读取操作后，应调用 XMLReader 实例的 `close()` 方法，以干净地终止文件访问，或者以其他方式表明不再需要访问原始数据源。

#### 总结

希望本章能让你了解拉式解析器（pull parsers）通常是如何工作的，以及在何时使用 XMLReader 这样的解析器比使用树解析器更好。要获取更多关于 XMLReader 的信息，请查看 PHP 手册中位于 <http://www.php.net/manual/en/book.xmlreader.php> 的相应章节。

### 第 13 章

#### CSS 选择器库

本章将回顾几个建立在前面章节描述的 XML 扩展之上的库。这些库提供了使用 CSS 选择器表达式来查询标记文档的接口，而不是使用编程 API 或 XPath 表达式。如果你对 CSS 选择器不熟悉，请不要担心，因为本章的一部分将展示基本表达式及其 XPath 等价物。

![](img/1e839861f06c77df9ecabc0aed9127b5_148_0.png)

**CSS 版本**

CSS 标准有多个版本，支持的随版本变化的选择器各不相同。本章将涵盖 CSS3 中可用选择器的一个子集。特定库支持的 CSS 标准版本会在可用的情况下注明。可以在 <http://www.w3.org/TR/css3-selectors/#changesFromCSS2> 找到两个常见版本 CSS2 和 CSS3 之间差异的列表。

#### 使用它们的理由

在深入探讨使用 CSS 选择器库的“如何”之前，最好先弄清“为什么”（以及“为什么不”）。不用说，这些库为使用它们的应用程序增加了一层复杂性，引入了另一个潜在的故障点。为了实现将 CSS 选择器表达式作为输入并将其转换为等效的 userland 操作，它们实现了表达式解析器，这可能会影响性能。

除上述观点外，它们确实提供了一些被认为更直观的语法。如今大多数开发人员至少了解一些 CSS，并且很可能对使用 CSS 选择器在客户端进行节点选择的 JavaScript 库（例如 jQuery）有一点经验。因此，当使用基于此的库时，该特定领域的知识可以转移到服务器端。

总而言之，如果你特别关注性能或应用程序的简洁性（相对于其依赖组件的数量），最好坚持使用像 XPath 这样的工具。否则，CSS 选择器库值得考虑，以便利用现有的通用技能集。

即使你的决定是坚持使用 XPath，请继续阅读。本章还将展示每组已解释 CSS 选择器的 XPath 等价物，这可能有助于进一步加深你对 XPath 的理解。请注意，这些比较并不一定是全面的，并且在任何给定情况下，可能有多种方式来表达相同的内容。

![](img/1e839861f06c77df9ecabc0aed9127b5_149_0.png)

#### jQuery 示例

jQuery 库本身的文档实际上拥有出色的选择器可视化客户端示例。如果你不确定是否理解下面任何 CSS 选择器的描述，jQuery 演示和源代码很可能会证明是有益的补充。你可以在 <http://api.jquery.com/category/selectors/> 找到它们。

#### 基础

让我们查看一些基本选择器及其应用于标记示例时的结果。

```html
<html>
<body>
  <div id="nav">
    <ul class="horizontal">
      <li><a href="/home">Home</a></li>
      <li><a href="/about-us">About Us</a></li>
      <li><a href="/contact-us">Contact Us</a></li>
    </ul>
    <img src="/img/ad1.jpg" alt="Advertisement #1">
    <img src="/img/ad2.jpg" alt="Advertisement #2">
  </div>
</body>
</html>
```

- `#nav` 将选择 div 元素，因为它的 id 属性值为 nav。
- `li` 将根据节点名称选择所有 li 元素。
- `.horizontal` 将选择 ul 元素，因为它具有 horizontal 类。（注意元素可以具有多个类。）
- `*` 将选择文档中的所有元素。
- `li, a` 通过将两个选择器 li 和 a 组合成逗号分隔列表来选择文档中所有的 li 和 a 元素。

以下是各自的 CSS 对应项旁边的 XPath 等价项。除了 .class 选择器外，XPath 表达式并没有显著变长或变得复杂。

| 选择器 | CSS | XPath |
| :--- | :--- | :--- |
| id | `#nav` | `//*[@id="nav"]` |
| 元素 | `li` | `//li` |
| 类 | `.horizontal` | `//*[@class="horizontal"] or starts-with(@class, "horizontal ") or contains(@class, " horizontal ") or ends-with(@class, " horizontal ")` |
| 通配符 | `*` | `//*` |
| 多重 | `li, a` | `//li | //a` |

#### 层级选择器

现在让我们继续讨论层级选择器，它们使用文档结构作为选择元素的方式，使用之前的标记示例。

- `body ul` 将选择所有 body 元素的 descendants（后代）中的 ul 元素。
- `ul > li` 将选择所有 ul 元素的 children（子级）中的 li 元素。
- `ul + img` 将选择所有紧随 ul 兄弟元素之后的 img 元素（即它们的下一个兄弟）。
- `ul ~ img` 将选择所有跟随 ul 兄弟元素的 img 元素（即它们之后且拥有相同父节点）。

此列表中的第三项和第四项可能看起来非常相似。区别在于“immediately”（紧接）这个词。在此示例中，列表中的第三项只会选择 Advertisement#1 图像，因为它紧接在文档中其 ul 兄弟元素之后。另一方面，列表中的第四项将选择两个图像，因为两个都跟随其 ul 兄弟元素。

| **选择器** | **CSS** | **XPath** |
| --- | --- | --- |
| 祖先 后代 | `body ul` | `body//ul` |
| 父级 > 子级 | `ul > li` | `//ul/li` |
| 前 + 后 | `ul + img` | `//ul/following-sibling::img[1]` |
| 前 ~ 兄弟 | `ul ~ img` | `//ul/following-sibling::img` |

#### 基本过滤器

本章到目前为止回顾的选择器始终改变所选择节点的 *类型*。相反，当在表达式后附加过滤器时，它仅仅是将返回的节点集限制为匹配原始表达式的子集。

请注意，可用的过滤器因库而异。jQuery 对过滤器的支持相当全面，因此在本章中，它被用作与过滤器相关部分的主要参考。





*   `li:first` 仅选择文档中找到的第一个 li 节点。
*   `li:last` 同样选择文档中找到的最后一个 li 节点。
*   `li:even` 选择文档中所有位于偶数位置的节点，从 0 开始计数。
*   `li:odd` 同样选择文档中所有位于奇数位置的节点，也从 0 开始计数。
*   `li:eq(0)` 选择 li 节点集合中位置为 0 的 li 节点（即第一个节点）。
*   `li:gt(0)` 选择 li 节点集合中位置大于 0 的所有 li 节点（即除第一个节点外的所有节点）。
*   `li:lt(1)` 选择 li 节点集合中位置小于 1 的所有 li 节点（即第一个节点）。
*   `:header` 匹配所有标题节点。（即 h1、h2 等）
*   `:not(:first)` 否定 `:first` 选择器，因此选择文档中除第一个 li 节点外的所有 li 节点。

| 选择器 | CSS | XPath |
| --- | --- | --- |
| 第一个节点 | `li:first` | `//li[1]` |
| 最后一个节点 | `li:last` | `//li[last()]` |
| 偶数节点 | `li:even` | `//li[position() mod 2 = 0]` |
| 奇数节点 | `li:odd` | `//li[position() mod 2 = 1]` |
| 特定节点 | `li:eq(0)` | `//li[1]` |
| 之后的所有节点 | `li:gt(0)` | `//li[position() > 1]` |
| 之前的所有节点 | `li:lt(1)` | `//li[position() < 2]` |
| 标题节点 | `:header` | `//h1//h2//h3//h4//h5//h6` |
| 不匹配表达式的节点 | `:not(:first)` | `/*[not(position() = 1)]` |

阅读此表时请注意，CSS 选择器的集合索引从 0 开始，而 XPath 的索引从 1 开始。

### 内容过滤器

基本过滤器主要基于节点类型或其在结果集中的位置，而内容过滤器则基于节点值或周围的层次结构。

*   `a:contains("About Us");` 选择所有节点值包含子字符串 “About Us” 的 a 节点。
*   `img:empty` 选择所有不包含子节点（包括文本节点）的 img 节点。
*   `li:has(a:contains("About Us"))` 选择所有包含节点值中包含子字符串 “About Us” 的 a 节点的 li 节点。
*   `li:parent` 选择所有包含子节点（包括文本节点）的 li 节点。

| **选择器** | **CSS** | **XPath** |
|---|---|---|
| 包含文本的节点 | `a:contains("About Us")` | `//a[contains(text(), "About Us")]` |
| 没有子节点的节点 | `img:empty` | `//img[not(node())]` |
| 包含选择器匹配项的节点 | `li:has(a:contains("About Us"))` | `//li[//a[contains(text(), "About Us")]]` |
| 包含子节点的节点 | `li:parent` | `//li[node()]` |

### 属性过滤器

到目前为止提到的过滤器特定于元素节点，但属性节点也存在相应的过滤器。在 CSS 和 XPath 中，属性过滤器都由方括号包围，但区别在于 CSS 主要使用运算符作为条件，而 XPath 主要使用函数。与本章节中描述的其他过滤器不同，不同库对属性过滤器的支持相当普遍。

*   `[href]` 匹配所有具有名为 `href` 的属性节点的节点。
*   `[href="/home"]` 匹配所有具有名为 `href` 且值为 "/home" 的属性节点的节点。
*   `[href!="/home"]` 匹配所有具有名为 `href` 且值不为 "/home" 的属性节点的节点。
*   `[href^="/"]` 匹配所有具有名为 `href` 且值以 "/" 开头的属性节点的节点。
*   `[href$="-us"]` 匹配所有具有名为 `href` 且值以 "-us" 结尾的属性节点的节点。
*   `[href*="-us"]` 匹配所有具有名为 `href` 且值中包含 "-us"（位于值内任意位置）的属性节点的节点。
*   `[src*="ad"][alt^="Advertisement"]` 匹配所有同时具有值为包含 "ad" 的 `src` 属性节点和值以 "Advertisement" 开头的 `alt` 属性节点的节点。

| 选择器 | CSS | XPath |
| :--- | :--- | :--- |
| 具有属性 | `[href]` | `//*[@href]` |
| 具有属性值 | `[href="/home"]` | `//*[@href="/home"]` |

### 子节点过滤器

子节点过滤器与之前复习的基本过滤器非常相似，只是应用于子节点。

*   `ul:nth-child(2)` 选择每个 ul 节点内的第二个子元素。传递给过滤器的参数也可以是 even 或 odd（这相对于父元素中的子节点位置计算），或者可以使用包含变量 *n* 的表达式（如 3n 表示每隔第三个子节点）。
*   `li:first-child` 选择所有作为其父节点第一个子节点的 li 节点。
*   `li:last-child` 同样选择所有作为其父节点最后一个子节点的 li 节点。
*   `li:only-child` 选择所有作为其父节点唯一子节点的 li 节点。

| 选择器 | CSS | XPath |
| :--- | :--- | :--- |
| 第 N 个子节点 | `ul:nth-child(2)` | `//ul/*[position() = 2]` |
| 第一个子节点 | `li:first-child` | `//***/[name() = "li" and position() = 1]` |
| 最后一个子节点 | `li:last-child` | `//***/[name() = "li" and position() = last()]` |
| 唯一子节点 | `li:only-child` | `//***/[name() = "li" and count() = 1]` |

### 表单过滤器

表单过滤器只是其他表达式的更便捷的简写形式。

*   `:input` 匹配所有 input、textarea、select 和 button 元素。
*   `:text`、`:hidden`、`:password`、`:radio`、`:checkbox`、`:submit`、`:image`、`:reset` 和 `:file` 均匹配具有相应类型的 input 元素。
*   `:button` 匹配所有 button 元素和类型为 button 的 input 元素。
*   `:enabled` 匹配所有未禁用的表单元素，`:disabled` 匹配已禁用的元素。
*   `:checked` 匹配所有已选中的单选按钮和复选框元素。
*   `:selected` 匹配所有已选中的 option 元素。

| 选择器 | CSS | CSS 替代写法 | XPath |
| :--- | :--- | :--- | :--- |
| 所有表单元素 | `:input` | `input, textarea, select, button` | `//input \|//textarea \|//select \|//button` |
| 特定类型的表单元素 | `:text` | `input[type="text"]` | `//input[type="text"]` |
| 按钮元素 | `:button` | `button, input[type="button"]` | `//button \|//input[type="button"]` |
| 启用状态的元素 | `:enabled` | `:not([disabled="disabled"])` | `//*[contains("input textarea select button", name()) and not(@disabled) or @disabled!="disabled"]` |
| 禁用状态的元素 | `:disabled` | `[disabled="disabled"]` | `//*[contains("input textarea select button", name()) and @disabled="disabled"]` |
| 已选中的元素 | `:checked` | `:input[checked="checked"]` | `//input[contains("checkbox radio", @type) and @checked="checked"]` |
| 已选中的选项 | `:selected` | `option[selected="selected"]` | `//option[@selected="selected"]` |

### 库

至此，CSS 选择器已被充分覆盖，解释了任何特定库支持的所有或部分选择器。本节将回顾一些可用的库实现，在哪里找到它们，它们支持的功能集，以及使用它们的优缺点。

#### PHP Simple HTML DOM Parser

该库的主要特征是它的依赖要求：PHP 5 和 PCRE 扩展（这在大多数 PHP 发行版中相当标准）。它不依赖或关联其他库或扩展，甚至不依赖 PHP 的标准 XML 扩展。

这意味着所有解析都在 PHP 本身中处理，因此性能可能不如基于 PHP 扩展构建的库。然而，在 XML 扩展（特别是 DOM 扩展）可能不可用的环境中（这种情况很少见），该库可能是一个不错的选择。它提供基本的检索支持，使用 PHP 的文件系统函数（要访问远程文档，需要启用配置设置 `allow_url_fopen`）。

该库的文档相当完善，可以在 `http://simplehtmldom.sourceforge.net/manual.htm` 找到。其主要网站包含下载库的链接，可在 `http://simplehtmldom.sourceforge.net` 获取。它采用 MIT 许可证。

#### Zend_Dom_Query

作为 Zend Framework 的组件之一，该库最初创建是为了提供基于该框架的应用程序的集成测试手段。然而，它可以独立于框架运行，并提供网络抓取分析阶段所需的功能。在撰写本文时，Zend Framework 1.10.1 要求 PHP 5.2.4 或更高版本。

Zend_Dom_Query 大量使用 DOM 扩展。它通过使用 DOM 扩展的 DOMXPath 类支持 XPath，并通过将 CSS 表达式转换为等效的 XPath 表达式来处理 CSS。请注意，仅支持 CSS 2，这排除了非属性过滤器。





值得注意的是，Zend_Dom_Query 不提供获取功能。所有将文档引入其中方法都要求这些文档事先以字符串形式存在。如果你已经在使用 Zend 框架，一个现成的获取选项是 Zend_Http_Client，本书中也对此进行了讨论。

可以在 [http://framework.zend.com/manual/en/zend.dom.query.html](http://framework.zend.com/manual/en/zend.dom.query.html) 找到 Zend_Dom_Query 的文档。目前，没有官方支持的方法来仅下载 Zend_Dom 包。可以从 [http://framework.zend.com/download/current/](http://framework.zend.com/download/current/) 下载整个框架，并从中提取 Zend_Dom 包所在的目录。在 [http://epic.codeutopia.net/pack/](http://epic.codeutopia.net/pack/) 可以找到下载单个非官方包的方法。Zend 框架组件基于新 BSD 许可证发布。

#### phpQuery

phpQuery 深受 jQuery 的影响，并在服务器端运行时环境（相对于客户端）允许的范围内保持与 jQuery 的相似性。它需要 PHP 5.2 和 DOM 扩展，以及 Zend 框架中的 Zend_Http_Client 和 Zend_Json 组件。这些组件是捆绑提供的，但可以用本地 Zend 框架安装中的相同组件进行替换。

CSS 支持仅限于 CSS3 的一个子集。大多数 jQuery 功能都得到支持，包括插件支持，并且计划移植多个 jQuery 插件。其他组件包括一个 CLI 工具，可从命令行调用 phpQuery 库的功能，以及一个用于通过客户端调用与 jQuery 集成的服务器组件。获取支持以与 Zend_Http_Client 集成的形式包含在内。

文档和下载链接可从 [http://code.google.com/p/phpquery/](http://code.google.com/p/phpquery/) 获取。它基于 MIT 许可证发布。

#### DOMQuery

这个库实际上是我自己的项目。虽然撰写本文时仍处于 Alpha 阶段，但它功能相当完整，并包含完整的单元测试套件。与本章提到的其他一些库一样，它需要 PHP 5，并大量使用 DOM 扩展。

然而，与其他库不同，它不实现 CSS 选择器解析器来提供相关功能。相反，它是通过其 API 以编程方式实现的。例如，不是将元素名称（比如 div）传递给中央查询方法，而是 `element()` 方法接受要查询的元素名称。虽然这使得它比其他库略显冗长，但也使其更具表达力，操作它只需要具备基本的 DOM 概念知识即可。

可以在 [http://github.com/elazar/domquery/tree/master](http://github.com/elazar/domquery/tree/master) 下载它。中央类 `DOMQuery` 使用 phpDoc 兼容的 API docblock 进行文档化，并且单元测试套件为每个可用方法提供了使用案例。

#### 总结

本章到此结束。阅读完本章后，你应该了解使用基于 CSS 选择器的库的优缺点以及适用场景、特定的 CSS 选择器及其在 XPath 中的可能等价形式，以及值得考虑的特定库实现。

## 第 14 章

### PCRE 扩展

有些情况下，标记文档可能格式错误得如此严重，以至于无法被 XML 扩展使用。在其他时候，你可能希望有一种方法来检查已提取的数据，以确保其符合预期。标记文档结构的重大变更可能导致你的 CSS 或 XPath 查询返回没有结果。变更也可能微小而微妙，导致虽然你能获得查询结果，但它们包含比预期更少或不同的数据。

虽然这两项任务都可以使用基本的字符串处理函数和比较运算符完成，但在大多数情况下，其实现会显得杂乱且不可靠。**正则表达式**提供了一套由**元字符**组成的语法，从而能够灵活且简洁地表达字符串内的模式。本章将专门讨论与 Perl 兼容正则表达式 (PCRE) PHP 扩展相关的正则表达式。

一种常见的错误做法是仅使用正则表达式从标记文档中提取数据。虽然这对于旨在短时间内容仅使用一次或很少几次的简单脚本可能有效，但长期来看更难维护且可靠性较低。正则表达式并非为此目的设计，而前面章节讨论的其他标记专用扩展更适合这项任务。这是关于为工作选择最佳工具的问题，因此应避免这种做法。

#### POSIX 扩展正则表达式

许多 PHP 开发者是从使用 POSIX 正则表达式扩展（也称为 ereg 扩展）开始学习正则表达式的。在 PHP 5.3 中，该扩展的函数正被弃用，转而采用 PCRE 扩展中的函数，后者速度更快且提供更强大的功能集。除了某些特殊字符范围在语法上的差异外，大多数 ereg 表达式只需添加表达式定界符即可配合 preg 函数使用。

#### 模式基础

让我们从简单的开始：检测字符串中任意位置子串的存在。

```php
<?php
// 使用基本字符串函数检测子串
$present = (strpos($string, 'foo') !== false);

// 使用 PCRE 函数实现相同功能
$present = (preg_match('/foo/', $string) === 1);
?>
```

注意，在 `preg_match()` 调用中的模式与 `strpos()` 调用中使用的字符串非常相似。在前者中，模式两侧使用 `/` 来表示其开始和结束。模式字符串中的第一个字符被视为模式定界符，可以是您指定的任意字符。在选择用于此字符时（`/` 是最常见的选择），请记住，如果在模式内部使用它，你将不得不对其进行转义（后面转义章节会有介绍）。这在本章稍后会更清晰。

这个例子中使用的两个函数之间的区别在于，`strpos()` 返回子串在字符串中的位置（从 `0` 开始），如果字符串中不包含该子串则返回 `false`。这需要使用 `!==` 运算符来区分子串是在字符串开头匹配还是根本没有匹配。相比之下，`preg_match()` 返回它找到的匹配次数。由于 `preg_match()` 在找到匹配后立即停止搜索，所以结果将是 `0` 或 `1`。

#### 锚点

你可能希望检查模式是否存在于字符串的开头或结尾，而不仅仅是检查模式是否包含在字符串的任意位置。这些功能的元字符统称为**锚点**。

```php
<?php
// 使用基本字符串函数检查字符串开头
$start = (strpos($string, 'foo') === 0);

// 使用 PCRE 函数实现相同功能
$start = (preg_match('/^foo/', $string) == 1);

// 使用基本字符串函数检查字符串结尾
$end = (substr($string, - strlen('foo')) == 'foo');

// 使用 PCRE 函数实现相同功能
$end = (preg_match('/foo$/', $string) == 1);

// 相当于字符串的精确匹配
$equal = (preg_match('/^foo$/', $string) == 1);
?>
```

- `^`（也称为尖音符字符）用于模式内表达式的开头，表示匹配应从字符串的开头开始。
- 类似地，`$` 用于指示模式内表达式的匹配应在字符串的结尾停止。
- 当 `^` 和 `$` 一起使用时，它们可以指示 `$string` 的全部内容精确匹配该模式。

> **字符串或行的开头**
> 重要的是要注意，这两个运算符的行为可能会有所不同。默认情况下，它们匹配 `$string` 的开头和结尾。如果使用多行修饰符，它们匹配的是 `$string` 中每一行的开头和结尾。本章后面的修饰符部分将更详细地介绍这一点。




可以在单个模式中同时检查多个表达式，这也被称为**交替匹配**（alternation），使用管道元字符 `|` 即可实现。

```php
<?php
// 匹配 'foo' 或 'bar' 或 'baz'，位置不限
$matches = (preg_match('/foo|bar|baz/', $string) == 1);
?>
```

请注意，`^` 和 `$` 不会隐式地应用于交替匹配中的所有表达式；必须为每个表达式显式使用它们。

```php
<?php
// $result == 1
$result = preg_match('/^foo|bar/', 'abar');

// $result == 0
$result = preg_match('/^foo|^bar/', 'abar');
?>
```

第一个示例返回 1，因为 `abar` 包含 `bar`，而在该模式中，`^` 并未应用于该表达式。第二个示例则对 `bar` 应用了 `^`，由于 `abar` 既不以 `foo` 也不以 `bar` 开头，因此返回 0。

模式中的某部分可能存在也可能不存在，或者可能被重复多次。这被称为**重复**（repetition），涉及使用一组统称**量化符**（quantifiers）的元字符。

```php
<?php
// 如果存在，则匹配 'a' 0 次或 1 次
$matches = (preg_match('/a?/', $string) == 1);

// 匹配 'a' 0 次或多次，数量不限
$matches = (preg_match('/a*/', $string) == 1);

// 匹配 'a' 1 次或多次，数量不限
$matches = (preg_match('/a+/', $string) == 1);

// 如果存在，则匹配 'a' 0 次或 1 次，等同于 ?
$matches = (preg_match('/a{0,1}/', $string) == 1);

// 匹配 'a' 0 次或多次，等同于 *
$matches = (preg_match('/a{0,}/', $string) == 1);

// 匹配 'a' 1 次或多次，等同于 +
$matches = (preg_match('/a{1,}/', $string) == 1);

// 匹配恰好 2 次 'a'
$matches = (preg_match('/a{2}/', $string) == 1);
?>
```

请注意，任何非 {X}、{X,} 或 {X,Y} 形式的大括号使用，都将被视为模式中的字面字符串。

### 子模式

你会注意到上一节示例中只使用了单个字符。这是因为**子模式**（subpatterns）的概念尚未引入。为了理解这些，最好查看一个不使用它们的示例，以了解它们对模式匹配方式的影响。

```php
<?php
// 匹配 'a' 后跟一个或多个 'b'
$matches = (preg_match('/ab+/', $string) == 1);
?>
```

如果没有子模式，就无法匹配例如字符串 'ab' 的一个或多个实例。子模式通过允许使用括号将模式的各个部分分组来解决这个问题。

```php
<?php
// 匹配 'ab' 一次或多次
$matches = (preg_match('/(ab)+/', $string) == 1);

// 匹配 'foo' 或 'foobar'
$matches = (preg_match('/foo(bar)?/', $string) == 1);

// 匹配 'ab' 或 'ac'
$matches = (preg_match('/a(b|c)/', $string) == 1);

// 匹配 'ab'、'ac'、'abb'、'abc'、'acb'、'acc' 等
$matches = (preg_match('/a(b|c)+/', $string) == 1);
```

### 匹配

子模式的作用不仅仅是允许你定义应用交替匹配或重复的部分。当找到匹配项时，不仅可以获取原字符串中与整个模式匹配的 substrings，还可以获取由子模式匹配的 substrings。

```php
<?php
if (preg_match('/foo(bar)?(baz)?/', $string, $match) == 1) {
    print_r($match);
}
?>
```

`preg_match()` 的第三个参数 `$match`，如果在找到匹配项时，将被设置为一个包含匹配数据的数组。该数组将至少包含一个元素：与模式匹配的整个 substrings。随后的任何元素将是子模式匹配项，其索引与该子模式在模式中的位置相匹配。也就是说，第一个子模式的索引为 1，第二个子模式的索引为 2，依此类推。

如果模式是条件性的（即使用了 `?`）且不存在，则数组中要么有一个空元素值，要么根本没有数组元素。

```php
<?php
if (preg_match('/foo(bar)?/', 'foo', $match) == 1) {
    // $match == array('foo');
}
```

- 在第一个示例中，`(bar)?` 子模式结束了整个模式，并且未匹配。因此，它在 `$match` 中没有条目。
- 在第二个示例中，`(bar)?` 子模式未结束整个模式，并且未匹配。因此，它在 `$match` 中有一个空条目。

```php
<?php
if (preg_match('/foo(bar)?(baz)?/', 'foobaz', $match) == 1) {
    // $match == array('foo', '', 'baz');
}
?>
```

子模式还可以包含其他子模式。

```php
<?php
if (preg_match('/foo(ba(r|z))?/', 'foobar', $match) == 1) {
    // $match == array('foobar', 'bar', 'r');
}
?>
```

除了将 `$match` 传递给 `print_r()` 或类似函数外，确定子模式在 `$match` 中位置的一种简便方法是，从模式左侧开始计数，直到到达目标子模式，计算模式中的左括号数量。

使用上述所示的语法，任何子模式都会被捕获（即在匹配数组中拥有自己的元素）。捕获的子模式限制为 99 个，而总子模式数量（无论是否捕获）限制为 200 个。虽然这在现实中不太可能成为问题，但最好使用 `(?:` 而不是 `(` 来开始不需要捕获的子模式，以明确表示。

此外，从 PHP 4.3.3 开始，可以为子模式分配有意义的名称，当它们被捕获时，用作匹配数组中的索引。要为子模式分配名称，请以 `(?P<name>` 语法开头，而不是 `(`，其中 `name` 是你想分配给该子模式的名称。这样做的好处是使代码更具表达性，从而更易于维护。

#### 转义

在某些情况下，你可能希望在模式中包括那些通常被解释为元字符的字面字符。可以通过 `\` 元字符实现这一点。

```php
<?php
// 匹配字面量 [
$matches = (preg_match('/\\[/', $string) == 1);

// 匹配字面量 \
$matches = (preg_match('/\\\\/', $string) == 1);

// 匹配表达式分隔符 /
$matches = (preg_match('/\\//', $string) == 1);

// 匹配标准转义序列 \r、\n 或 \t 中的任意一个
$matches = (preg_match('/\\r|\\n|\\t/', $string) == 1);
?>
```

请注意，第二个示例中必须双重转义 `\\`，因为无论是否用于正则表达式，PHP 都将字符串 `'\\'` 解释为单个反斜杠。在其他情况下，无需转义 `\` 即可正确解释转义序列。

> **双重转义**
>
> 有关本节中双重转义示例背后原因更多信息，请参阅 `http://php.net/manual/en/language.types.string.php#language.types.string` 以及 `http://php.net/manual/en/regexp.reference.php` 中的反斜杠部分。

#### 转义序列

匹配单个字符（该字符可能是几个字符之一）有三种方法。

第一种方法涉及使用 `.` 元字符，它将匹配除换行符（`"\n"`）之外的任何单个字符，前提是不使用修饰符（稍后会有介绍）。它可以像其他字符一样用于重复。

第二种方法需要使用代表字符范围的特殊转义序列。除了上一节示例中提到的转义序列外，以下是一些常用项。

- `\d`：数字，0 到 9。
- `\h`：水平空白字符，如空格或制表符。
- `\v`：垂直空白字符，如回车符或换行符。
- `\s`：任何空白字符，等同于由 `\h` 和 `\v` 表示的所有字符。
- `\w`：任何字母、数字或下划线。

每个这些转义序列都有一个补集。

- `\D`：非数字字符。
- `\H`：非水平空白字符。
- `\V`：非垂直空白字符。
- `\S`：非空白字符。
- `\W`：非字母、非数字且非下划线的字符。

第三种且最后的方法涉及使用**字符范围**，即方括号（`[` 和 `]`）内的字符。字符范围表示单个字符，但就像普通单个字符一样，它们可以应用重复。

```php
<?php
// 匹配与 \d 相同
$matches = (preg_match('/[0-9]/', $string) == 1);

// 匹配与 \w 相同
$matches = (preg_match('/[a-zA-Z0-9_]/', $string) == 1);
?>
```




范围是相对于 ASCII（美国信息交换标准代码）而言的。换句话说，起始字符的 ASCII 值必须位于结束字符的 ASCII 值之前。否则，将发出警告“Warning: preg_match(): Compilation failed: range out of order in character class at offset $n$”，其中 $n$ 是正则表达式中的字符偏移量。

在方括号内，单个字符和特殊范围是并排列出的，中间没有分隔符，如上面的第二个示例所示。此外，前面提到的转义序列（如 \w）可以在方括号内部和外部使用。

![](img/1e839861f06c77df9ecabc0aed9127b5_171_0.png)

#### ASCII 范围

如需查看优秀的 ASCII 查找表，请参阅 http://www.asciitable.com。

关于字符范围，还有另外两个值得注意的点，如下面的示例所示。

```php
<?php
// 在字符范围中使用字面量 ] 的方法如下
$matches = (preg_match('/[\]]/', $string) == 1);

// 匹配任何不是 'a' 的字符
$matches = (preg_match('/[^a]/', $string) == 1);

// 在字符范围中使用字面量 ^ 的方法如下
$matches = (preg_match('/[\^]/', $string) == 1);
$matches = (preg_match('/[a^]/', $string) == 1);
?>
```

- 要在字符范围中使用字面量 `]` 字符，需按照转义其他元字符的方式对其进行转义。
- 要否定一个字符范围，请使用 `^` 作为该字符范围中的第一个字符。（是的，这可能会令人困惑，因为当 `^` 不用于字符范围内部时，它也用于表示行或整个字符串的开头。）请注意，否定适用于范围内的所有字符。换句话说，被否定的字符范围意味着“不是这些字符中任何一个的任何字符。”
- 要在字符范围中使用字面量 `^` 字符，要么按照转义其他元字符的方式对其进行转义，要么不要将其用作范围中的第一个或唯一字符。

### ctype 扩展

一些简单的模式在 ctype 库中有等效函数。这些函数通常性能更好，在合适时应优先于 PCRE 使用。有关 ctype 扩展及其提供函数的更多信息，请参阅 http://php.net/ctype。

### 修饰符

使用模式定界符来标记模式开始和结束的原因在于，模式之前有**修饰符**，它们会影响元字符的匹配行为。以下是几个在网页抓取应用中可能证明有用的修饰符。

- i: 模式中的任何字母都将匹配大写字母和小写字母，而与模式中使用的字母的大小写无关。
- m: `^` 和 `$` 将匹配字符串中行的开始和结束位置（由换行符分隔），而不是整个字符串的开始和结束位置。
- s (小写): `.` 元字符将匹配换行符，默认情况下它不匹配。
- S (大写): 将花费额外的时间来分析模式，以加速后续使用该模式的匹配。适用于多次使用的模式。
- U: 默认情况下，量词 `*` 和 `+` 表现为所谓的“贪婪”模式。也就是说，它们尽可能匹配尽可能多的字符，而不是尽可能少的字符。此修饰符强制使用后一种行为。
- u: 强制将模式字符串视为 UTF-8 编码字符串。

下面的示例匹配成功，因为使用了 *i* 修饰符，这意味着模式匹配 '`a`' 和 '`A`'。

```php
<?php
$matches = (preg_match('/a/i', 'A') == 1);
?>
```

#### 总结

本章涵盖了适用于验证抓取数据的核心正则表达式方面。正则表达式还有更高级的方面，可能在其他领域有用。鼓励进一步复习 PHP 手册中的 PCRE 部分。

- 有关模式修饰符，请参阅 [http://php.net/manual/en/reference.pcre.pattern.modifiers.php](http://php.net/manual/en/reference.pcre.pattern.modifiers.php)。
- 有关模式语法，请参阅 [http://php.net/manual/en/reference.pcre.pattern.syntax.php](http://php.net/manual/en/reference.pcre.pattern.syntax.php)。
- 有关正则表达式的优秀书籍，请参阅《精通正则表达式》，ISBN 0596528124。

## 第 15 章

### 技巧与窍门

本章之前的章节旨在提供有关构建网页抓取应用所需技能的有用信息。本章更多地聚焦于该材料的一系列实际应用和方法论。其目的是将之前涵盖的所有材料联系在一起，并使整本书更加完整。这里涉及的一些主题将特定于某类网页抓取应用，一些将具有普遍适用性，而大多数将假设该应用旨在长期使用。希望它们都能说明设计应用时需要考虑的重要因素。

### 批处理任务

旨在长期使用的网页抓取应用通常以两种方式使用：实时或批处理。

采用实时方法实现的网页抓取应用将接收请求，并向被抓取的目标应用发送请求，以履行原始请求。这有两个优点。首先，从目标应用拉取的任何数据都是最新的。其次，推送到目标应用的任何数据，其在该网站上的反映时间与直接将数据推送到目标应用所需的时间几乎相同。这种方法的不在于增加了网页抓取应用的响应时间，因为客户实际上必须等待每个原本发送给目标应用的请求对应的两个请求完成。

批处理方法基于同步。对于读操作，数据按固定间隔更新。对于写操作，更改在本地存储，然后批量推送到目标应用（因此得名），也按固定间隔进行。这种方法的优缺点是实时方法优缺点的互补：更新将是实时的，但网页抓取应用的响应时间不会增加。当然，可以使用相对低间隔的批处理方法来近似实时，同时获得批处理方法的好处。

方法的选择取决于网页抓取应用的需求。通常，如果网页抓取应用或目标应用不要求实时更新，则优先选择批处理方法以维持高性能水平。

### 可用性

无论网页抓取应用采用实时还是批处理方法，它都应将对远程服务视为潜在故障点，并考虑其未返回响应的情况。一旦经过测试的网页抓取应用投入生产，常见原因要么是服务停机，要么是服务变更。这些症状包括连接超时以及状态码高于 2xx 范围的响应。

在这种情况下，批处理方法的一个优势是网页抓取应用的面向用户的界面可以不受影响。可以使用缓存数据，或者将更新存储在本地，并在服务再次可用或网页抓取应用已修复以应对远程服务变更时启动同步。

#### 并行处理

前面介绍的两个 HTTP 客户端库，cURL 和 pecl_http，支持使用单个连接并行运行请求。虽然无法使用其他库完全复制此功能，但可以使用在并行执行的过程中在单独的连接上运行多个请求。

即使你使用的是支持连接池的库，当抓取多个主机时，这种技术也很有用，因为每个主机无论如何都需要一个单独的。相比之下，在单个过程中这样做意味着，发送给响应率较低的主机的早期请求可能会阻塞发送给另一个响应较快主机的后续请求。

有关此技术的更详细示例，请参阅附录 B。

#### 爬虫

一些网页抓取应用旨在作为爬虫来索引网站内容。与其他所有网页抓取应用一样，它们执行的工作可以分为两类：检索和分析。并行处理方法在此适用，因为每类工作都为另一类工作填充工作队列。

检索过程被给予一个或多个初始文档进行检索。每次检索到一个文档时，它就成为分析过程的一个任务，该过程抓取标记并搜索指向其他文档的链接（a 元素），这些链接可能受一个或多个相关性因素限制。一旦文档分析完成，任何当前未检索的文档的地址则反馈给检索过程。

这种相互供应的情况理论上将持续到没有发现未索引或被认为相关的文档为止。届时，可以使用适当的请求标头检查文档更新，并将文档提供给分析过程以查找更新，从而重新启动流程。

#### 表单

一些网页抓取应用必须将数据推送到目标应用。这通常使用模拟 HTML 表单提交的 HTTP POST 请求来实现。然而，在发送此类请求之前，有几个事件



通常需要在这些情况下发生。首先，如果网络抓取应用程序旨在向用户展示，则必须向该用户呈现一个至少在一定程度上相似的表单。其次，应验证用户通过该表单提交的数据，以确保其很可能被目标应用程序接受。

根据项目的需求和表单结构的不同，此技术的适用性会有所不同。它涉及抓取目标应用程序中表单的标记，并使用抓取的数据生成类似元数据文件或 PHP 源代码文件，可直接放入网络抓取应用程序项目中。这对于加速具有多个表单或复杂表单且必须模拟 POST 请求的目标应用程序的开发工作非常有用。

为了构建 POST 请求，你需要查询具有 name 属性的 input、select、textarea 或可能是 button 元素。除此之外，还需考虑以下几个与特定元素相关的注意事项。

- 当网络抓取应用程序侧的表单提交时，那些 type 属性值为 checkbox 或 radio 且未被选中的 input 元素，其在最终向目标应用程序发起 POST 请求时，不应包含其 value 属性值。一种常见的做法是，在文档中将该 checkbox 元素之前放置另一个 type 属性值为 hidden 且具有相同 name 的元素，以便在 checkbox 未被选中时假定使用 hidden 元素的值。

- select 元素是否支持多个值取决于是否设置了 multiple 属性。这在 POST 请求中的表达方式可能取决于目标应用程序运行的平台。确定此点的最佳方法是使用能够显示底层 POST 请求的客户端在目标应用程序上提交表单。

- 具有 maxLength 属性的 input 元素被限制为长度小于或等于该值。同样，select 元素也被限制为其包含的 option 子元素的 value 属性值。在验证用户提交的数据时，这两者都应予以考虑。

#### Web 服务

构建网络抓取应用程序的原因通常是目标应用程序没有提供 Web 服务或格式化为可自动消费的数据。然而，有些网站在已经构建好网络抓取应用程序之后，最终会提供 Web 服务。因此，在设计阶段保持对这种潜在可能性的警惕非常重要。

Web 服务的引入并不会消除之前提到的关于检索的问题。对于试图实时访问目标应用程序或相应 Web 服务的应用程序来说，延迟仍然可能成为一个问题。理想情况下，从网络抓取应用程序切换到 API 时，分析过程中的复杂性将降低，性能将提高。

然而，如果 API 服务确实推出，这两个区域的代码可能都需要被替换。因此，重要的是设计一个尽可能接近假想 Web 服务提供的 API，并集中那些在该情况下需要替换的逻辑。通过这样做，使用现有 API 的现有本地应用程序逻辑将只需要很少或无需更改。

撇开法律问题不谈（关于法律问题的更多信息见附录 A），与新的 Web 服务提供相比，考虑维护现有的网络抓取应用程序有其原因。这些原因可能包括与 Web 服务提供的数据相比，前者受到限制或不完整，或者 Web 服务的正常运行时间低于可接受的容差。在前一种情况下，网络抓取逻辑可以替换为 Web 服务调用，以在两种数据提供重叠的地方提高数据可靠性。在后一种情况下，当服务可用时，网络抓取逻辑可以执行 Web 服务调用，并在服务再次可用之前使用缓存数据或在本地存储数据更新。

#### 测试

单元测试对于应用程序的质量保证有多么重要，它对网络抓取应用程序就更重要，因为它依赖于其目标保持不变。必须检查标记文档的查询，以断言它们产生可预测的结果，并且必须验证从这些标记文档中提取的数据，以确保其符合预期。对于实时应用程序，还必须检查 HTTP 响应，以确保目标应用程序可访问，并且没有发生巨大变化导致资源不再位于其原始位置。

在开发过程中，建议下载要抓取的文档的本地副本，并将其作为单元测试套件的一部分包含在内，随着套件的开发而不断完善。此外，测试套件应包括两种工作模式：本地和远程。前一种情况会对上述本地文档副本执行测试，而后者则会实时从目标站点下载文档。如果网络抓取应用程序的任何部分停止按预期工作，对比这两种工作模式的结果对于确定问题的原因非常有帮助。

PHPUnit 是现有的 PHP 单元测试框架中最受欢迎的之一。更多信息请访问 http://phpunit.de。其众多功能之一是将测试结果以 XML 格式输出到文件的选项。此功能以及 PHPUnit 和其他单元测试框架中类似的其它功能，对于生成可移植到另一数据介质并对网络抓取应用程序本身可访问的结果非常有用。这促进了在相关功能测试失败时，暂时限制或禁用该应用程序中功能的能力。

归根结底是这样的：调试 Web 应用程序就像试图用豌豆射手去杀一只飞行的苍蝇。重要的是让定位问题原因尽可能容易，以最小化更新网络抓取应用程序以适应变化所需的周转时间。测试失败应警告开发人员并锁定任何敏感的应用程序区域，以防止数据的错误传输、损坏或删除。

### 结束了，大家

感谢阅读本书。希望你喜欢并在此过程中学到了新东西，或者至少获得了一些思考的素材。理想情况下，阅读本书将对你未来如何构建网络抓取应用程序产生深远影响，并且它将成为你不断参考的书之一。除了这本书之外，剩下的学习要靠实践。所以，出发去抓取吧！

## 附录 A

### 网络抓取的法律性

网络抓取的法律性是一个相当复杂的问题，主要由于版权法和知识产权法。不幸的是，没有一个简单且完全明确的回答，特别是因为这些法律在不同国家之间可能存在差异。然而，在审查潜在的网络抓取目标时，有少数几个常见的考察点。

首先，网站通常有一些被称为服务条款（TOS）、使用条款或用户协议的文件（为了引用方便，以下简称为 TOS 文档）。这些文件通常位于一个不起眼的地方，如网站页脚中的链接或在法律文档或帮助部分。这些类型的文档在较大且较知名的网站上更为常见。以下是几个明确禁止抓取其内容的网站中的此类文档片段。

- “您特别同意不通过任何自动化手段（包括使用脚本或网络爬虫）访问（或试图访问）任何服务……” – Google 服务条款，截至 2010 年 2 月 14 日的第 5.3 节

- “未经许可，您不得以自动化方式（如收割机器人、机器人、蜘蛛或爬虫）收集用户的内容或信息，或以其他方式访问 Facebook。” – Facebook 权利与责任声明，安全部分，截至 2010 年 2 月 14 日





- “Amazon grants you a limited license to access and make personal use of this site ... This license does not include ... any use of data mining, robots, or similar data gathering and extraction tools.” – Amazon Conditions of Use, LICENSE AND SITE ACCESS section as of 2/14/10

  亚马逊授予您访问和使用本网站的有限个人使用权……此许可不包括……使用数据挖掘、机器人或类似的数据采集和提取工具。——《亚马逊使用条款》，许可证和网站访问章节，截至2010年2月14日

- “You agree that you will not use any robot, spider, scraper or other automated means to access the Sites for any purpose without our express written permission.” – eBay User Agreement, Access and Interference section as of 2/14/10

  您同意，未经我们明确的书面许可，不得使用任何机器人、爬虫、抓取器或其他自动化手段出于任何目的访问本网站。——《eBay 用户协议》，访问与干扰章节，截至2010年2月14日

- “... you agree not to: ... access, monitor or copy any content or information of this Website using any robot, spider, scraper or other automated means or any manual process for any purpose without our express written permission; ...” – Expedia, Inc. Web Site Terms, Conditions, and Notices, PROHIBITED ACTIVITIES section as of 2/14/10

  ……您同意不进行以下行为：……未经我们明确的书面许可，使用任何机器人、爬虫、抓取器或其他自动化手段或任何手动流程出于任何目的访问、监控或复制本网站的任何内容或信息；……——Expedia, Inc. 网站条款、条件和声明，禁止活动章节，截至2010年2月14日

- “The foregoing licenses do not include any rights to: ... use any robot, spider, data miner, scraper or other automated means to access the Barnes & Noble.com Site or its systems, the Content or any portion or derivative thereof for any purpose; ...” – Barnes & Noble Terms of Use, Section I LICENSES AND RESTRICTIONS as of 2/14/10

  上述许可不包括以下权利：……使用任何机器人、爬虫、数据挖掘器、抓取器或其他自动化手段出于任何目的访问巴诺网站或其系统、内容或其任何部分或衍生作品；……——《巴诺使用条款》，第一章节 许可与限制，截至2010年2月14日

确定目标网站是否有 TOS 文档将是第一步。如果您找到文档，请查找使用与上述示例类似语言的条款。同时，也要查找任何广泛的“全面禁止”条款，网络抓取可能会归属于此类被禁止的活动之下。

如果您找到了一份 TOS 文档，且其中未明确禁止网络抓取，下一步是联系有权代表拥有该网站的组织发言的代表。某些组织可能允许网络抓取，前提是您事先已获得适当权限的许可。在获得此许可时，最好获取一份书面文件，并使用官方信头，以明确表明该文件来源于相关组织。这能最大程度地降低可能出现的任何法律问题。

如果因使用自动代理或由代理获取的信息而对个人提起与知识产权相关的指控，假设该个人未违反其所有者施加的任何 TOS 协议或相关计算机使用法律，法院判决最终可能归结于该信息的使用是否被解释为在指控发生地的地理区域内符合版权法中的“合理使用”。

请注意，这些陈述非常通用，并非旨在替代律师咨询。如果 TOS 协议或缺乏协议以及与网站所有者的沟通未能得出明确结论，强烈建议在尝试在网站上启动自动代理之前寻求法律建议。这也是网络抓取是解决数据获取问题的不理想方案的原因，只有在没有其他替代方案时才应考虑使用它。

一些网站实际上使用许可协议来授予其内容开放或轻度限制的使用权。用于此目的的常见许可包括 GNU 自由文档许可和 Creative Commons 许可。在特定的数据源用于获取数据不相关的情况下，应优先选择使用此类许可的来源，而不是没有使用许可的来源，因为法律问题的发生几率显著降低。

第二个检查点是作为待采集数据原始来源的网站合法性。即使是拥有大量法律资源的大型公司，如 Google，也曾因自动代理从非法联合分发其他网站内容的站点获取内容而遇到问题。在某些情况下，网站会注明其来源，但在许多情况下它们不会。

对于文本内容，将可能来自该站点的直接引语（具有唯一性的可能性较大）输入主要搜索引擎，是确定相关网站是否为数据原始来源的一种方法。这也可以提供一些指示，表明联合分发该数据是否合法。

对于非文本数据，请根据主题推测相应的关键词，并尝试使用特定于该数据格式的搜索引擎进行搜索。此类搜索的目的不是进行全面或决定性的指示，而仅仅是排除对原始数据源明显联合分发的一种快速方法。

## 附录 B

### 多进程

当使用 CLI SAPI（即从命令行）执行 PHP 脚本时，该执行实例作为本地操作系统中的一个进程存在。进程控制（pcntl）扩展使得 PHP 脚本能够执行所谓的进程 **fork**。这包括原始 PHP 进程（随后称为 **父进程**）创建自身的副本（恰当地称为 **子进程**），其中包含从与该进程关联的数据到 fork 指令后的当前执行点的所有内容。

一旦 fork 完成，两个进程都存在并独立执行。父进程可以连续多次 fork 自身，并对其子进程保持有限的感知。特别是，当任何给定的子进程终止时，它会收到通知。

由于每个子进程都是其父进程的副本，可以 fork 的子进程数量受本地系统硬件资源的限制。CPU 仅限制所有子进程完成的速度。然而，如果本地系统的 RAM 被超过并不得不使用交换空间进行存储，内存可能会成为瓶颈。

这种限制促使我们希望 fork 尽可能多的进程，以便并行完成一项工作而不触及任何资源限制。这通常通过使用对要 fork 的进程数量的预定上限来实现。然而，一旦任何给定的子进程完成，可能希望在其位置创建一个新的子进程以完成另一个工作单元。下面示例中展示了这种实现方式。

```php
<?php
// Maximum number of child processes to fork
$children_max = 10;

// Counter for current number of child processes
$children_count = 0;

// Temporary variable for the status of a terminated child process
$child_status = null;

// Process identifier, initialized so the parent branch executes
$pid = 1;

while (true) {
    if ($pid == -1) {
        trigger_error('Unable to fork process', E_USER_ERROR);
    } elseif ($pid) {
        // Parent process

        // Check for more work

        // Break out of the loop if the job is finished

        // Fork another child
        $children_count++;
        $pid = pcntl_fork();

        // Wait to fork more children if the max is reached
        if ($children_count == $children_max) {
            pcntl_wait($child_status);
            $children_count--;
        }
    } else {
        // Child process

        // Perform a unit of work

        exit;
    }
}
?>
```

### 进程控制资源

有关进程控制扩展的更多信息，请参阅 http://php.net/manual/en/book.pcntl.php。

