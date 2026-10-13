
从该声明的末尾开始说，PHP `可以嵌入 HTML` 意味着你可以获取一个标准的 HTML 页面，在需要的地方插入一些 PHP，最终得到一个动态结果。这一特性使得 PHP 对任何做过哪怕一点点 HTML 工作的人都非常容易上手。

此外，PHP 是一种 `脚本` 语言，相对于 `编译型` 语言：PHP 旨在编写 Web 脚本，而非独立应用程序（尽管现在付出一些额外努力，你也可以用 PHP 创建应用程序）。PHP 脚本仅在事件发生后运行——例如，当用户提交表单或访问一个 URL（统一资源定位符，Web 地址的技术术语）时。

我应该补充说明，PHP 是一种服务端的、跨平台的技术，这两个描述都很重要。`服务端` 指的是 PHP 所做的一切都发生在服务器上。需要一个 Web 服务器应用程序，如 Apache 或微软的 IIS（Internet Information Services，互联网信息服务），并且所有 PHP 脚本都必须通过 URL（`http://`*某物*）来访问。其跨平台的本质意味着 PHP 可在大多数操作系统上运行，包括 Windows、Unix（及其众多变体）和 Macintosh。更重要的是，在一台服务器上编写的 PHP 脚本通常无需修改或仅需少量修改即可在另一台服务器上运行。

***

### PHP 6 发生了什么？

当我撰写本书的上一版 *PHP 6 and MySQL 5 for Dynamic Web Sites: Visual QuickPro Guide* 时，PHP 的下一个主要版本——PHP 6——大约完成了 50%。考虑到 PHP 6 会在书出版后某个时候发布，我在该版的部分内容中依赖了一个 PHP 6 的测试版。然后……PHP 6 夭折了。

PHP 6 计划的关键特性之一是支持 Unicode，这意味着 PHP 6 能够原生地处理任何语言。这将是对一个已广受欢迎的编程工具的极佳补充。不幸的是，实现 Unicode 支持从复杂变得非常困难，语言背后的开发者们搁置了 PHP 6 的开发。然而，并非一无所获：PHP 6 计划中的其他一些特性，例如对 `命名空间`（一种面向对象编程概念）的支持，被加入到了 PHP 5.3 中。

在撰写本书时，尚不清楚 Unicode 支持何时能完成，也不清楚 PHP 6 会如何发展。我的直觉是，PHP 将在版本 5 的主干上进行一段时间的增量开发。

***

在本书撰写时，PHP 处于 5.3.6 版本，本书假设你使用的是至少 5.0 版本。书中涵盖的一些函数和特性将需要更具体或更新的版本，如 PHP 5.2 或更高版本。在这些情况下，我会明确说明该功能是在哪个 PHP 版本中添加的，并为使用稍旧版本语言的读者提供替代方案。

如果你仍在使用 PHP 4 版本，你真的应该升级。如果这不在你的计划中，请改阅读本书的第二版。

关于 PHP 的更多信息，始终可以在 PHP.net 或 Zend（[www.zend.com](http://www.zend.com)）——PHP 核心背后的智囊团——找到。

### 为什么使用 PHP？

简单来说，在开发动态 Web 网站方面，PHP 比其他替代方案更好、更快、更容易学习。使用 PHP 你将获得卓越的性能、与几乎所有可用数据库的紧密集成、稳定性、可移植性，以及因其可扩展性而带来的近乎无限的功能集。所有这些都无需成本（PHP 是开源的），且拥有非常平缓的学习曲线。PHP 是我见过的最完美的结合之一，它既让初学者能轻松上手，又能让高级程序员做他们需要的一切。

最后，事实胜于雄辩：自诞生以来，PHP 的使用量呈指数级增长，是超过 76% 所有网站的首选服务端技术 ![Image](graphics/circle-b.jpg)。就所有编程语言而言，PHP 是第五大最流行的语言 ![Image](graphics/circle-c.jpg)。

![Image](graphics/00_figure_02_b.jpg)

![Image](graphics/circle-b.jpg)Web Technology Surveys 网站提供了这张关于服务端技术的图表（[www.w3techs.com/technologies/overview/programming_language/all](http://www.w3techs.com/technologies/overview/programming_language/all)）。

![Image](graphics/00_figure_03_c.jpg)

![Image](graphics/circle-c.jpg)Tiobe 指数（[http://www.tiobe.com/index.php/content/paperinfo/tpci/index.html](http://www.tiobe.com/index.php/content/paperinfo/tpci/index.html)）使用多种因素组合对编程语言的流行度进行排名。

当然，你可能会认为，作为一本 PHP 书的作者（实际上是好几本），我的观点有偏见。虽然程度远不如 PHP 深，但我也曾使用 Java Server Pages (JSP)、Ruby on Rails (RoR) 和 ASP.NET 开发过网站。各有优劣，但 PHP 是我始终会回归的技术。你可能会听说它的性能或扩展性不如其他技术，但 Yahoo!、Wikipedia 和 Facebook 都在使用 PHP，你找不到比这些访问量更大、要求更高的网站了。

你可能也会想知道 PHP 有多安全。但 `安全性不在于语言本身`；而在于如何使用该语言。请放心，本书提供了关于所有相关安全问题的完整且最新的讨论。

### PHP 如何工作

如前所述，PHP 是一种服务端语言。这意味着你编写的 PHP 代码位于一台称为 `服务器` 的主机计算机上。服务器将网页发送给请求的访问者（即你，客户端，使用你的 Web 浏览器）。

当访问者访问一个用 PHP 编写的网站时，服务器读取 PHP 代码，然后根据其脚本指令进行处理。在 ![Image](graphics/circle-d.jpg) 所示的示例中，PHP 代码指示服务器将适当的数据——HTML 代码——发送给 Web 浏览器，浏览器将接收到的代码视为标准的 HTML 页面处理。

![Image](graphics/00_figure_04_d.jpg)

![Image](graphics/circle-d.jpg)当用户请求网页时，PHP 如何融入客户端/服务器模型。

这与静态 HTML 网站不同，后者在发出请求时，服务器仅将 HTML 数据发送给 Web 浏览器，不会发生任何服务端解释 ![Image](graphics/circle-e.jpg)。因为不需要服务端动作，你可以在不使用服务器的情况下在 Web 浏览器中运行 HTML 页面。

![Image](graphics/00_figure_05_e.jpg)

![Image](graphics/circle-e.jpg)请求静态 HTML 页面时的客户端/服务器流程。

对于最终用户和 Web 浏览器而言，`home.html` 和 `home.php` 看起来可能没有可感知的差别，但该页面内容的创建方式将截然不同。

### 什么是 MySQL？

MySQL（[www.mysql.com](http://www.mysql.com)） ![Image](graphics/circle-f.jpg) 是世界上最流行的开源数据库。事实上，如今 MySQL 是昂贵的巨头如 Oracle 和微软 SQL Server 的有力竞争者（具有讽刺意味的是，MySQL 归 Oracle 所有）。像 PHP 一样，MySQL 提供卓越的性能、可移植性和可靠性，拥有适度的学习曲线，且几乎零成本。

![Image](graphics/00_figure_06_f.jpg)

![Image](graphics/circle-f.jpg)MySQL 数据库应用程序的主页。

MySQL 是关系型数据库的数据库管理系统（DBMS）（因此，MySQL 是一个 RDBMS）。用最简单的术语来说，数据库是数据的集合，无论是文本、数字还是二进制文件，由 DBMS 存储并保持有序。
