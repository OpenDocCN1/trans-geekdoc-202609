

Titanium 在概念上类似于 Adobe Air，本质上两者的优点、缺点和用途都相同。然而情况本可以完全不同，因为 Titanium 的早期版本曾将 PHP 作为一等语言提供集成支持。这意味着你可以像使用 JavaScript 一样在 HTML 中使用 PHP *within* 你的 HTML。无需服务器。这意味着你可以在页面上运行 PHP 代码，直接访问页面 DOM 并执行 PHP 能做的一切。然而，从 v2 版本开始，Appcelerator 撤回了该功能，专注于 JavaScript。尽管开源核心产品的旧版本仍可用并保留 PHP 功能，但本条目更多是对本可能成为现实之事的历史性备注。

| ![](Images/image00249.gif) || `Appcelerator Titanium` |

| --- | --- |

|   ||   |

|   || 支持 HTML & JavaScript 应用的运行时，可替代浏览器 |

|   ||   |

|   || `Main website` : [http://www.appcelerator.com/](http://www.appcelerator.com/) |

|   ||   |

|   || `Main documentation & Installation info` : [http://docs.appcelerator.com/](http://docs.appcelerator.com/) |

|   ||   |

|   || `Now removed PHP functionality` : [http://matthewturland.com/slides/titanium/](http://matthewturland.com/slides/titanium/) |

|   ||   |

|   || `Appcelerator Licensing Controversy` : [http://arstechnica.com/information-technology/2012/09/when-free-isnt-developer-accuses-tool-vendor-of-extorting-customer/](http://arstechnica.com/information-technology/2012/09/when-free-isnt-developer-accuses-tool-vendor-of-extorting-customer/) |

### 5.21 PHP-Qt

PHP-Qt 是一个扩展，用于为流行的跨平台 QT 小部件工具包提供 PHP 绑定。然而，该项目似乎最后一次发布代码是在 2007 年，并于 2009 年被弃用。此处仅为完整性而提及，代码仍可供下载，可能对试图开发类似解决方案的人有所帮助。

| ![](Images/image00249.gif) || `PHP-Qt` |

| --- | --- |

|   ||   |

|   || 已废弃的项目，用于为 QT 工具包提供绑定。 |

|   ||   |

|   || `Information` : [http://en.wikipedia.org/wiki/PHP-Qt](http://en.wikipedia.org/wiki/PHP-Qt) |

### 5.22 PHP/TK

PHP 是一个最后更新于 2004 年的项目，为 TCL/TK X-windows 接口工具包提供绑定。与上述 PHP-Qt 类似，此处仅为完整性而提及。

| ![](Images/image00249.gif) || `wxPHP` |

| --- | --- |

|   ||   |

|   || 为 TCL/TK 工具包提供绑定。 |

|   ||   |

|   || `Main website` : [http://php-tk.sourceforge.net/](http://php-tk.sourceforge.net/) |

|   ||   |

|   || `Using PHP/TK with Delphi/Lazarus` : [http://web.fastermac.net/~MacPgmr/PhpTk/PhpTkStatus.html](http://web.fastermac.net/~MacPgmr/PhpTk/PhpTkStatus.html) |

## 6\. System software

在上一章中，我们探讨了面向用户的软件，即人类用户直接交互的软件。在本章中，我们将探讨我将称之为“系统软件”的内容，即（通常）无需人工驱动即可执行任务的软件。

要编写系统软件，我们通常需要创建一个“守护进程”，即持续运行的进程。创建守护进程后，我们需要确定其主要功能。有些守护进程持续工作（测量、监控、通信等），而另一些则等待并响应事件（网络连接、系统变化、用户操作）来工作。我们将探讨如何在 PHP 中创建守护进程并使其持续运行。然后，我们将探讨如何将该基本守护进程改为不持续工作，而是在系统中发生某些事件时立即响应。

在上一章中我们探讨的面向用户的软件，通常一次只由一个人或一个进程使用。另一方面，系统软件通常同时为许多不同的“客户端”服务。在此语境下，“客户端”可以是网络客户端（例如，Web 服务器的 Web 浏览器）、用户进程（访问您 API 服务器的 GUI 客户端）、文件（日志服务器的日志文件）或类似内容。在这样做的同时，它需要保持“响应性”，即一个客户端不应在另一个客户端的请求完成之前等待。想想如果 Apache 一次只能提供一个网页，网络会变得多么拥堵！为了在 PHP 中管理并发任务并保持守护进程的响应性，我们可以使用任务调度和管理系统，我们将在本章的最后部分探讨这一点。

### 6.1 Daemons in PHP

守护进程是一个通常作为后台进程持续运行的程序。它通常不直接与用户交互，而是执行后台任务或响应系统事件、来自其他软件的调用、网络请求或其他机器对机器事件。作为守护进程运行的程序示例包括 Cron（在后台等待并根据当前时间执行任务）和 Apache（等待来自远程机器的 Web 资源请求）。守护进程通常：

*   永久运行（或运行很长时间，或直到预定事件发生），

*   在引导时启动

*   执行有用的任务

*   由 root 或（非人类）系统用户拥有。

然而，这些标准并不普遍适用于所有守护进程，事实上，守护进程唯一共有的具体特征是它们没有控制终端（tty），因此被视为在“后台”运行。没有 tty，软件无法从键盘获取用户输入，也无法通过终端将输出显示给用户（尽管有其他方式可以直接和间接地与用户交互）。虽然消耗最少资源传统上是后台进程的关键特征，但现在已不再常见。数据库管理系统和 Web 服务器等软件“服务器”作为后台守护进程运行，但通常会消耗大量（甚至全部）系统资源，并且通常有专门用于运行它们的机器。因此，最好将守护进程视为任何通常不直接与用户交互的持续运行软件。

### 6.2 Creating a daemon

要在 PHP 中创建守护进程，我们使用 PHP 进程控制扩展，即 PCNTL，它仅在 Unix/Linux 类型系统上可用。在 Windows 上，您可以使用 win32service pecl 扩展来控制 Windows“服务”（即守护进程），包括将您自己的 PHP 脚本转换为服务。该扩展目前处于 Beta 阶段，文档较为稀疏，因此我们不会在此介绍。

| ![](Images/image00249.gif) || `win32service extension` |

| --- | --- |

|   ||   |

|   || Beta 扩展，允许您创建和控制 Windows 服务。 |

|   ||   |

|   || `Main website` : [http://pecl.php.net/package/win32service](http://pecl.php.net/package/win32service) |

|   ||   |

|   || `Main documentation & Installation info` : [http://php.net/manual/en/book.win32service.php](http://php.net/manual/en/book.win32service.php) |

|   ||   |

|   || `Example of a PHP script as a service` : [http://php.net/manual/en/win32service.examples.php](http://php.net/manual/en/win32service.examples.php) |

大多数预编译版本的 PHP 包含 PCNTL 扩展，但如果没有，您将需要使用 `--enable-pcntl` 选项重新编译 PHP，或使用包管理器安装该扩展。有关详细信息，请参见附录 A。

创建守护进程的大致过程如下：

*   我们运行一个进程（PHP 脚本）。我们将此称为父进程。

*   从父进程，我们 fork（复制）一个子进程。

*   父进程随后退出。子进程现在没有父进程。

*   `init` 收养没有父进程的子进程。`init` 是内核在引导时启动的原始进程，是所有进程的祖先。

*   然后我们将子进程与启动父进程的终端分离（分离子进程）。这是为了

    *   我们的任何输出都不会出现在终端中

