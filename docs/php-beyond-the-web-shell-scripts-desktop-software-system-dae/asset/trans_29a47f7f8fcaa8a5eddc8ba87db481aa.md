

will simply execute your `myprogram.php` file (which you write mostly like any other PHP script) and return any output back to the terminal (unless you tell it otherwise) instead of being sent to the web server (which doesn’t exist!).

In general, PHP scripts called directly using PHP CLI will behave in the same way as when called through a web server, although there are some differences. For instance, you won’t find any `$_GET` or `$_POST` arrays, and PHP won’t send any HTTP headers by default, as these concepts don’t mean much beyond the web. Default settings like `max_execution_time` are set to sensible values for local use (in this case to 0 so your scripts won’t time out), output buffering is turned off, and error messages are displayed in plain text rather than HTML.

The PHP CLI SAPI is what we will be using for most of the examples in this book as it is designed with exactly the same motivations as this book: taking PHP beyond the web. Full details of how to install and use the CLI SAPI are given in the next chapter.

### 2.2 PHP 版本 - 你用的是哪个？

PHP 从 4.3.0 版本开始就支持 CLI SAPI，因此本书中的许多示例都可以在该版本及之后的任何 PHP 版本上运行。撰写本书时，PHP 的当前版本是 5.6.5，本书中的代码已针对该版本进行了测试。如果你发现某个特定函数似乎不存在或无法按预期工作，请查看该函数的在线 PHP 手册。这会显示哪些版本支持哪些函数，并描述较新版本引入的任何破坏性更改。

如果你使用的是旧版本，升级有非常充分的理由。

*   最近的版本性能显著提升（相应地，资源使用量减少）

*   虽然对于非 Web 应用程序来说安全性并不总是那么关键（有关注意事项请参见本章后面的安全性讨论），但如果你要处理来自外部来源的数据，或者如果你同时使用同一版本进行 Web 开发，那么最近版本中的安全增强和安全相关的错误修复是必不可少的

*   现代语言特性可用，这有助于提高你的编码生产力，也能让其他人更认真地对待你的代码

与 Web 版本的 PHP 一样，如果你有需要，可以编译自己的 CLI SAPI 版本。如果你想包含操作系统软件仓库中未预打包的扩展，出于性能原因移除非必要代码，或使用 PHP 支持的任何其他编译时选项，那么学习“自行构建”版本可能是值得的。关于编译和安装 PHP 及相关扩展的入门指南可在附录 A 中找到。

### 2.3 不要在 PHP 中这样做的几个好理由

本书专注于在 PHP 中完成所有事情，对于 90% 的任务，PHP 都能满足要求。但在你决定用 PHP 重构你的世界之前，有一些相关问题你可能需要仔细考虑，然后再行动。

*   **高性能要求**

如果你需要非常高的性能，特别是在硬件有限的情况下，PHP 可能不适合你。最近的 PHP 版本性能大幅提升，在基准测试中经常超越 Python 等语言和 Ruby-on-Rails 等框架。然而，PHP 的核心是一种抽象脚本语言，对于某些任务，它永远无法达到像 C 这样更接近底层的低级语言的性能。不过，不要因为高性能任务就完全否定 PHP，如果你在考虑性能的同时也关注成本，你可能会发现，PHP 开发速度带来的开发人员时间成本节省，超过了为获得性能而投入的额外硬件成本。请参阅第 9 章，了解如何提高性能，并了解如何从 PHP 与 C 等语言交互，以便你仍然可以在 PHP 中获得 RAD（快速应用开发）的一些好处。

*   **不要（不一定）重复造轮子**

你 *可以* 用 PHP 编写 Web 服务器（示例请参见附录 D），但 *现有* 的服务器（如 Apache）是否能满足你的需求？对于许多或大多数基础设施“痒处”，已经存在软件（由多种不同语言编写）可以为你提供所需的“抓痒”。除非你真的需要其他功能，否则编写自己的软件所花费的时间通常会超过学习和实现现有软件所花费的时间。当然，对于某些人来说，情况正好相反。“因为我能”可以是一个有效的理由，编写软件总是一次宝贵的学习经历。

*   **保持源代码闭源**

PHP 是一种脚本语言，这意味着如果你编写软件用于销售或部署到其他地方，你将向接收者泄露你的源代码。许多人（包括你的作者）会认为，即使是商业上的“开源”也是一件好事。但如果这不符合你的口味，那么你需要下更大功夫来保护你的代码。网上有源代码混淆器可用，它们使用各种技巧使你的代码难以（但并非不可能）阅读，并且现在有许多 PHP 编译器可用于生成二进制程序（尽管在语法和扩展覆盖方面存在限制）。但是，主 PHP 项目并未表达支持代码隐藏或编译的任何意图，因此此类方法的长期可行性尚不确定。闭源软件的商业论据在中长期内也并非铁板钉钉。

### 2.4 考虑安全性

每个称职的程序员至少都意识到构建网站和在线应用程序的安全影响。你故意将你的代码暴露给公众，暴露给世界，暴露给任何会来的人（好人和坏人）。PHP 的早期失败之一是将易用性置于代码安全性之上（关于 `register_globals` 等遗留物的恐怖故事，快速谷歌一下就能找到）。随着更新、更安全的默认设置和 `register_globals` 等函数被弃用，PHP 在线上比以往任何时候都更安全。而且，虽然大多数安全问题是由程序员而非语言引起的，但如今即使是最新的 Web 编码者似乎也从一开始就对安全问题有所认识。

然而，踏入离线软件的世界，情况就截然不同了。通常我们看到的软件仅面向受信任的用户，部署在受信任的机器上，并完全由仁慈的用户控制。用户不会故意攻击软件或机器，他们处理的是自己的数据，功能绝对不能被妥协。在开发桌面应用程序等软件时，很少会考虑安全性，更不用说在设计时将其指定为功能了，因为它不是“必要的”。

然而，世界并非如此运作。查看任何软件漏洞邮件列表，如 BugTraq，你会发现 Adobe Reader、Microsoft Word 甚至 GIMP 等开源老牌软件中存在大量漏洞。事实是，即使在本地应用程序中，安全性也很重要，主要有两个原因。第一个是“典型用户”行为的老生常谈问题。这对于从不犯错的聪明精通技术的用户（比如你，亲爱的读者）来说不是问题，但对于我们其余的人使用的任何软件来说，灾难只在一次意外点击可疑电子邮件之间。安全性之所以重要，第二个原因是，对于大多数机器来说，许多非 Web 应用程序并不真正“离线”。即使桌面应用程序或系统守护进程本身不与 Web、本地网络或其他外部服务交互，它所连接的机器也几乎总是插着以太网线或激活了 WiFi/3G/4G 连接。你的软件不会在自己舒适的小领域里运行，与外部世界隔绝。当然，完全沙箱化的虚拟机除外。

