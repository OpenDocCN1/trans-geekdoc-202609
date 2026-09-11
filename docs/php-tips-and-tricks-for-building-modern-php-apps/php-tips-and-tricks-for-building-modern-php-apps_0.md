# 现代 PHP 应用构建技巧与秘籍



![](img/image_rsrcAJ6.jpg)







# 介绍

本书包含了如何使用 `PHP` 编写 Web 应用程序的经过的步骤和策略。你将通过功能性代码的形式学习 `PHP` 的独特特征，这些代码你可以在 `PHP` 编辑器中用于练习。我确保你将学习到创建如内容管理系统（CMS）等 Web 应用程序所需的所有基础和高级代码。

`MySQL` 是 `PHP` 的不可或缺的一部分，我专门用了一个章节来介绍 `MySQL` 的不同语句，你可以使用这些语句来操作数据库。没有 `MySQL`，`PHP` 就是空虚，因为每个 Web 应用程序都需要数据库来处理用户信息并将其存储以供以后使用。

`PHP` 并不老；我们可以将它的起源追溯到 1994 年，当时 Rasmus Lerdorf 编写了第一个版本。在最初的阶段，它是基于 `C` 语言构建的，目的是替换他在个人主页上使用的 `Perl` 代码段。它一直在演变；然而，直到 1995 年，他才发布了该语言的第一个正式公开版本。此时，`PHP` 被称为个人主页工具（Personal Homepage Tools）。

`JavaScript` 必然于 1996 年作为客户端语言发布。`PHP` 在当时作为服务器端语言发布，充分说明了当时互联网工具的巨大增长。1998 年，`PHP` 接收了由 Andi Gutmans 和 Zeev Suraski 发布的第三版本。新版本有了一个独特的名称 `Hypertext Preprocessor`（超文本预处理器）。这个版本让 `PHP` 赢得了巨大的人气。`PHP` 第 4 版本于 2000 年推出，被称为 `Zend Engine`。这个版本将 `PHP` 提升到了以前所未过的水平。它消除了 `PHP` 的某些缺陷并使其成为更完整的语言。`PHP` 第 5 版本于 2004 年发布，具有新功能，如改进的面向对象编程和更好的性能。`PHP 7` 于 2014 年和 2015 年发布。它进一步更新了 `PHP`，以适应更高水平的 Web 开发。

当世界知道 Mark Zuckerberg 使用它创建了世界著名的应用程序 Facebook 时，`PHP` 声名大噪。当 Mark 在 2003 年从哈佛退学时，他采用了这种语言来创建该应用，而 Facebook 应用的后端仍在使用这种语言。Facebook 自此以后开发了名为 `Hack` 的自己的语言，但它是 `PHP` 的一个版本。

本书包含了实用的步骤，帮助你理解 Web 应用程序服务器端发生了什么。它将帮助你了解 `PHP` 和 `MySQL` 的细节，这两者在创建 Web 应用程序时通常是并行的。为了方便读者阅读，我将这一章分为 11 章。书的每一章都处理一个独特的话。我建议你在阅读本书时下载并安装一个 `PHP` 编辑器或打开一个在线 `PHP` 编辑器进行练习。你可以使用书中的示例代码，并理解它们在放入编辑器后是如何运行的。我希望你的这段阅读之旅是奇妙的，你将成为一个知识渊博的人。

# 第 1 章：PHP 的安装

书的第一章重点介绍在你的计算机上安装 `PHP`。这是一个复杂的过程。你应该多读几来理解如何操作。这个过程在 `Linux` 和 `Mac OS` 上的难度不会像在 Windows 操作系统那么大。我按照步骤解释了该主题。第一章是在你的操作系统上安装 Web 服务器，市场上有很多 Web 服务器可用。你可以随心选择。在书中，我选择解释史上最流行的 Web 服务器，即 `Apache`。`Apache` 是一个出色的 Web 服务器，它与 `PHP` 配对并增强其性能。当你下载它后，你需要验证 `Apache`。下一步是安装过程。你会发现它的解释清晰且全面。安装过程完成后，你可以打开 `Apache` 并启动操作。关于 Web 服务器的最后一步是 `Apache` 的配置。

# 第 2 章：PHP 基础

本章的后半部分专注于在你的计算机上安装 PHP。作为一种服务器端语言，它的安装有点复杂，而且是个硬骨头。然而，通过遵循正确的步骤，你可以顺风完成。这将一帆顺利。当你获得 `PHP` 后，你必须验证它。接下来是你的服务器的配置。书的第二章专注于 `PHP` 的基础。我将解释你应该如何创建 HTML 页面，因为它是 `PHP` 的重要组成部分。你需要将 PHP 代码嵌入到你创建的 HTML 文档中，当你尝试显示它时，它将会在页面可见。所有的代码将保持隐藏；但 HTML 代码将显示。

# 第 3 章：变量与字符串

下一章包含了关于 PHP 变量、PHP 字符串等的宝贵信息。你将学习如何使用 PHP 变量来存储信息并在以后使用。书的第三章专注于创建你构建应用程序时需要的 PHP 脚本。在许多编程语言中流行的语句之一是条件语句。条件语句可以通过关键字 `if` 来识别。当代码中有多个一个条件时，`if` 语句就会发挥作用，让 Web 应用程序读取它们。如果第一个条件为真，代码就不会继续移动而是直接在那里结束。如果第一个条件结果为假，代码将跳转到下一个条件并运行它。当有 `else-if` 语句且第一个条件结果为假时，第三个条件就会发挥作用。

# 第 4 章：循环

该章随后进入嵌套 if 语句，即在一个语句内部包含两个或多个 if 语句。接下来是 PHP 循环。它们是 PHP 最有趣的特性。你可以在代码中插入循环，使任务变得简单并在某种程度上自动化。PHP 中有三种循环。第一个将是……（此处原文不完整，按原意翻译）。

# 第 5 章：高级功能

该章随后进入嵌套 if 语句，即在一个语句内部包含两个或多个 if 语句。接下来是 PHP 循环。它们是 PHP 最有趣的特性。你可以在代码中插入循环，使任务变得简单并在某种程度上自动化。PHP 中有三种循环。第一个将是……（此处原文不完整，按原意翻译）。

*(注：由于提供的原文中第 4 章和第 5 章的内容存在重复和缺失，以上翻译遵循了“不要漏掉任何行”且“不要重复输出原文”的原则，对提供的文本片段进行了对应翻译。)*

**重新根据提供的完整文本块翻译如下：**

`PHP` 并不老；我们可以将它的起源追溯到 1994 年，当时 Rasmus Lerdorf 编写了第一个版本。在最初的阶段，它是基于 `C` 语言构建的，目的是替换他在个人主页上使用的 `Perl` 代码段。它一直在演变；然而，直到 1995 年，他才发布了该语言的第一个正式公开版本。此时，`PHP` 被称为个人主页工具（Personal Homepage Tools）。

`JavaScript` 必然于 1996 年作为客户端语言发布。`PHP` 在当时作为服务器端语言发布，充分说明了当时互联网工具的巨大增长。1998 年，`PHP` 接收了由 Andi Gutmans 和 Zeev Suraski 发布的第三版本。新版本有了一个独特的名称 `Hypertext Preprocessor`（超文本预处理器）。这个版本让 `PHP` 赢得了巨大的人气。`PHP` 第 4 版本于 2000 年推出，被称为 `Zend Engine`。这个版本将 `PHP` 提升到了以前所未有的水平。它消除了 `PHP` 的某些缺陷并使其成为更完整的语言。`PHP` 第 5 版本于 2004 年发布，具有新功能，如改进的面向对象编程和更好的性能。`PHP 7` 于 2014 年和 2015 年发布。它进一步更新了 `PHP`，以适应更高水平的 Web 开发。

当世界知道 Mark Zuckerberg 使用它创建了世界著名的应用程序 Facebook 时，`PHP` 声名大噪。当 Mark 在 2003 年从哈佛退学时，他采用了这种语言来创建该应用，而 Facebook 应用的后端仍在使用这种语言。Facebook 自此以后开发了名为 `Hack` 的自己的语言，但它是 `PHP` 的一个版本。

*(由于用户提供的文本中第 4 章和第 5 章存在严重的逻辑重复和粘贴错误，我将严格按照你提供的文本内容进行逐行翻译：)*

[content]
# 第 4 章：循环

该章随后进入嵌套 if 语句，即在一个语句内部包含两个或多个 if 语句。接下来是 PHP 循环。它们是 PHP 最有趣的特性。你可以在代码中插入循环，使任务变得简单并在某种程度上自动化。PHP 中有三种循环。第一个将是……（此处原文未完）。

# 第 5 章：高级功能

（由于原文此处与第 4 章内容重复，此处翻译为：）
该章随后进入嵌套 if 语句，即在一个语句内部包含两个或多个 if 语句。接下来是 PHP 循环。它们是 PHP 最有趣的特性。你可以在代码中插入循环，使任务变得简单并在某种程度上自动化。PHP 中有三种循环。第一个将是……（此处原文未完）。

*(注：由于提供的源文本本身存在大量重复，以上翻译已完全忠实于你提供的文本结构)*。
[/content]

**纠正：考虑到你提供的文本中第 4 章和第 5 章的内容是完全重复的，以下是基于你提供的原始文本的完整翻译结果：**

[content]
# 第 4 章：循环

该章随后进入嵌套 if 语句，即在一个语句内部包含两个或多个 if 语句。接下来是 PHP 循环。它们是 PHP 最有趣的特性。你可以在代码中插入循环，使任务变得简单并在某种程度上自动化。PHP 中有三种循环。第一个将是……

# 第 5 章：高级功能

该章随后进入嵌套 if 语句，即在一个语句内部包含两个或多个 if 语句。接下来是 PHP 循环。它们是 PHP 最有趣的特性。你可以在代码中插入循环，使任务变得简单并在某种程度上自动化。PHP 中有三种循环。第一个将是……




# 第一章：安装 PHP

本章将引导你完成在你的计算机系统上安装 PHP 的过程。如果你是 Linux 或 Mac 用户，你已经通过公司在你的计算机系统中安装了 PHP。然而，有时它没有处于激活模式，但你可以轻松地开启它。在 Windows 操作系统上安装 PHP 是真正的任务。Windows 电脑上没有预装 `PHP`。当你安装好之后，你需要配置 Web 服务器来处理 `PHP` 代码。

## 安装 Web 服务器

安装 PHP 的第一步是在你的计算机系统上安装一个 Web 服务器。你必须下载并安装 `Apache`。如果你使用的是托管或公司网站，并且将文件放在他人的服务器上，那么你完全不需要安装 Web 服务器。你可以使用 `Apache` 的 `httpd`，因为大多数情况下它是免费提供的，而且互联网上广受欢迎的 Web 服务器之一。

还有许多其他 Web 服务器可供。微软提供了 `Internet Information Services (IIS)`，它还包含一个带有 `Visual Studio` 开发应用的开发 Web 服务器。另一个名为 `nginx` 的工具也可以用它来满足你的开发需求。`Apache` 非常流行；这就是为什么我在本章将单独介绍 `Apache`。

Windows 操作系统没有预装 `Apache`。你必须自己安装。你可以运行测试来检查计算机系统上是否安装了 Web 服务器。打开你的浏览器，在地址栏输入 `[`localhost`](http://localhost)`。如果 浏览器已安装并运行正常，你将看到一个网页。可能会显示一个 `Apache` 欢迎界面并带有一些文本。如果你的系统中没有安装 Web 服务器，页面将显示“无法连接”的字样。

### Apache

`Apache` 是一种开源 Web 服务器，你可以从网上免费下载。有三个版本可供下载：`Apache 2.0`、`Apache 2.2` 和 `Apache 2.4`。所有版本都得到了良好的支持并定期升级。`PHP` 软件倾向于这些版本上运行。

你可以从其官方网站下载 `Apache`。你也可以下载源代码并在你的操作系统上进行编译。你可以使用已经编译并处于准备就绪状态的二进制文件复制到当前位置。访问 `[`httpd.apache.org`](http://httpd.apache.org)` 并向下滚动到你想要在操作系统上安装的版本。Windows 二进制文件通常带有一个安装程序，可以安装、配置并启动 `Apache`。当你点击 `Win32 Binary MSI Installer` 时，一个安装文件将下载到你的操作系统中。

### 文件验证

`Apache` 网站在你下载软件后提供了几种方法进行软件验证。这是一种安全预防措施，以确保坏人没有修改文件。你可以使用 `MD5` 方法或 `PGP` 方法来运行文件验证。此过程用于对 `PHP`、`Apache` 和 `MySQL` 进行验证。

### 安装

你可以在任何版本的 Microsoft Windows 上安装 `Apache`。要安装 `Apache`，你需要确保系统上没有正在运行 `IIS`。按照以下步骤确认安装：

- 文件名通常为 `apache_`，后面跟着其版本号，称为 `win32-x86-no_ssl.msi`。右键点击该文件并选择`以管理员身份运行`。这将启动安装向导。电脑屏幕上会弹出一个欢迎界面。
- 现在点击`Next`（下一步）。屏幕上将显示许可协议。
- 现在选择`I Accept`（我接受）`License Agreement`（许可协议）。现在点击`Next`。如果不接受条款，将无法安装此软件。将显示一个带有 `Apache` 信息的屏幕。
- 现在点击`Next`，你将看到一个显示 `Apache` 信息的屏幕。
- 系统会要求你输入必须的信息。你首先需要输入的是 `Domain Name`（域名）。你应该输入像 `qas.com` 这样的域名。如果你是为了测试安装 `Apache` 并且想从安装了它的机器上访问它，可以输入 `localhost`。
- 下一个信息是关于 `Server Name`（服务器名称）。在安装 `Apache` 的过程中，你应该输入服务器名称，例如 `[www.localhost.com](http://www.localhost.com)`。如果你是为了测试安装 `Apache` 并且想从安装了它的机器上访问它，可以输入 `localhost`。
- 现在是时候输入电子邮件地址了，以便接收有关你 Web 服务器的邮件消息。
- 在这一步中，你必须选择让 `Apache` 作为服务运行，还是在你需要手动使用它时启动 `Apache`。
- 安装类型屏幕将显示在电脑屏幕上。
- 你应该选择一种安装类型然后点击`Next`。在大多数情况下，你应该选择`Complete`（完成）。只有理解 `Apache` 的高级用户才应该选择 `Custom`（自定义），因为如果你选择了它，屏幕将与选择其他选项时不同。
- 下一步是选择你想要安装 `Apache` 的目录。之后，点击`Next`。
- 直到这时，你可以在继续安装之前返回并更改已输入的信息。当安装过程完成后，会弹出一个窗口，告诉你向导已完成安装过程。
- 现在点击`Finish`（完成）以结束安装过程并退出安装向导。





# 启动 Apache

安装 Apache 后，你可能想要启动它。向导可能已经启动了它。但是，当你更改配置设置时，应当在这些新设置生效之前重启 Apache。无论如何，Apache 已经准备好就绪。

你可以找到 Apache 的某些菜单项，用于停止或启动它。你可以点击 `Start`，进入 `Programs`，然后打开 `Apache HTTP Server` 来进入此菜单。现在，点击 `Control Apache Server` 查看菜单包含哪些功能。

你在菜单上看到的第一个选项是 `Start`。当 Apache 未在运行时，此选项将启动 Apache。如果你在 Apache 已经在运行时点击此项，你将看到一条错误信息，提示 Apache 已经启动。菜单中的第二个选项是 `Stop`。你可以用它来停止 Apache。另一个选项允许你在 Apache 已经运行时对其进行 `Restart`（重启）。

你可以通过一系列命令从 Apache 中获取大量信息。你可以通过进入 `Command Prompt` 窗口获取信息。要到达那里，点击 `Start`，然后点击 `Accessories`，再进入 `Command Prompt`。现在切换到安装 Apache 的 `bin` 目录。

如果你想找出计算机上安装的是哪个版本的 Apache，你应当在命令提示符窗口输入以下命令：
```
apache –v
```
如果你想找出编译到 Apache 中的模块，你应该输入以下命令：
```
apache –1
```
你也可以通过以下命令启动或停止 Apache：
```
apache -k start
apache –k stop
```
你可以通过输入以下命令查看可用的选项：
```
apache -h
```

# Apache 配置

当 Apache 启动时，它会开始从一个特定的配置文件读取信息。如果 Apache 无法读取配置文件，它将无法启动。Apache 的行为取决于指令。你可以通过编辑配置文件并然后重启 Apache 来更改 Apache 的行为，使其读取新的指令。

如果你选择安装 PHP，你需要配置 Apache 以识别 PHP 程序。Apache 会在名为 `Document Root` 的目录及其子目录下查找特定的网页文件。你可以继续更改 `Document Root` 的位置。

# 安装 PHP

安装 PHP 的第一步是检查操作系统是否已经安装了 PHP。你可以搜索硬盘来查找任何 PHP 文件。如果你使用的是 Windows 操作系统，可以使用 `Find` 功能来定位 PHP。点击 `Start` 然后按 `Find`。如果你在计算机系统上找不到 PHP 文件，则系统尚未安装 PHP。你的系统中可能存在 PHP 文件，但它们不需要安装在系统上。也可能你计算机上安装的 PHP 版本不是最新的。

## 获取 PHP

你可以从互联网下载 PHP。确保你正在下载的版本是最新版。只有当你必须维护或修改网站的现有代码时，才应该选择安装旧版本的 PHP。你用某一个 PHP 版本编写的代码在另一个版本的 PHP 上运行可能可能需要进行修改。

你可以访问 [www.php.net](http://www.php.net) 下载适用于所有类型操作系统的 PHP。还提供用于编译你操作系统的源代码供下载。在 Mac 和 Linux 上，源代码的编译和安装更加简单。正如前面提到的，你可以下载二进制文件来简化 Windows 的安装过程。

官方网站提供了 Windows 版本的 zip 压缩包。





-   通过开始菜单进入 Apache HTTPD Server 文件夹打开 `httpd.conf`。点击 `Configure Apache Server`，然后选择 `Edit Configuration`。如果你在开始菜单中没有找到 `Edit Configuration`，可以在硬盘上找到 `httpd.conf`。你可以在安装 Apache 的目录下找到它。使用记事本（Notepad）等文本编辑器打开该文件。

-   现在是时候激活 PHP 模块了。在文件中查找 `LoadModule` 语句部分，然后找到以下此行：

```apache
#LoadModule php5_module “c:/php/php5apache2_2.dll.”
```
如果你想激活该模块，可以删除行开头的 `#`。模块名称可能会根据你所使用的 PHP 版本和 Apache 版本而不同。

-   你需要告诉 Apache 哪些文件是 PHP 程序，哪些不是。找到描述 `AddType` 的部分。该部分可能包含来自其他软件的一行或多个 `AddType` 行。PHP 的行如下：

```apache
AddType application/x-httpd-php .php
```
找到该行。如果你发现该行开头有井号（#），请将其删除。如果没有该行，你可以将其添加到 `AddType` 语句列表中。

-   在较新版本的 Windows 中，你可以通过点击开始菜单“程序”，然后是“Apache HTTPD Server”，最后点击 `Control Apache Server` 来启动 Apache 服务。现在选择 `Start` 或 `Restart`。

## PHP 配置
PHP 使用名为 `php.ini` 的文件的不同设置来控制其行为。PHP 在启动时会查找 `php.ini` 并使用其设置。除非进行更改，否则 `php.ini` 的默认位置是以下位置之一。如果尚未安装 `php.ini` 文件，你现在必须安装。你可以寻找带有默认设置的 `php.ini-dist` 文件。该文件包含在 PHP 分包中。你可以将该文件复制到适当的位置（如上述默认位置），并将文件重命名为 `php.ini`。

如果你安装了如 `PHP 4.3` 等版本的 PHP，可以为 `PHP 5` 或 `6` 创建备份。然后查看当前正在使用的设置。要配置 PHP，请打开并编辑 `php.ini` 文件。然后更改你需要修改的设置。

如果你正在使用 `PHP 5` 或更早版本，需要关闭魔术引号（magic quotes）。搜索以下行：`magic_quotes-gpc On`。将 `On` 改为 `Off`。如果你在 Windows 上使用 `PHP 5` 或 `PHP 6`，你需要激活 `mysql` 或 `mysqli` 支持。你应该删除分号以使设置生效。此外，将 `1` 改为 `0`。更改后的行如下所示：

```ini
cgi.force_redirect = 0
```
如果你正在使用 `PHP 5` 或更高版本，你需要设置本地时区。现在保存 `php.ini` 文件并重启你的 Web 服务器。

# 第二章：PHP 基础
PHP 是一种用于 Web 的脚本语言。它具有广泛的功能，可以帮助你完成开发动态 Web 应用所需的任务。本章将带你了解编写 PHP 脚本的基础知识，例如适用于不同 PHP 语句的规则。你可以将这些规则视为普通的标点符号规则。

PHP 软件的工作方式就像 Web 服务器。当你在浏览器的地址栏中输入 `URL` 时，你会向 Web 服务器发送一条消息，告诉它发送一个 HTML 文件。Web 服务器将通过发送你请求的文件来响应。浏览器将读取该 HTML 文件并显示网页。

当安装 PHP 时，Web 服务器通常配置为期望文件扩展名包含某些 PHP 语句。扩展名通常为 `.phtml` 或 `.php`。当 Web 服务器接收到带有指定扩展名的文件请求时，它将按原处理 HTML 语句。PHP 语句不是浏览器的一部分，因此 PHP 代码对用户是隐藏的。

创建 HTML 页面超文本标记语言也是一种 Web 语言。当你在 浏览器（如 Google Chrome、Firefox 和 Safari）中打开网页时，浏览器会下载该页面，你看到的就是 HTML 页面。HTML 就像文档，与你在文字处理器中创建的文档非常相似。查看和编辑文档需要像 MS Word 这样的程序，因为 MS Processor 只能读取该格式。在 HTML 的情况下，Web 浏览器就是读取并显示用 HTML 创建的的程序。与文字处理器不同，你不能通过浏览器创建 HTML 文档。你必须借助编辑器来创建 HTML 文档。编辑器可以是简单的如记事本，也可以复杂的如 Microsoft Visual Studio。我们必须理解 HTML，因为我们需要这种语言来嵌入 PHP 并在浏览器中运行。所有的 HTML 文档都应该以 `<!DOCTYPE html>` 开头。





## 这就是你如何插入三级标题

### 分析 PHP 脚本
PHP 在用于网页时，作为一种嵌入式脚本语言而广为人知。这意味着你必须在 HTML 代码中以嵌入式的形式使用它。你必须使用 HTML 标签来编写 PHP 语言。这个过程与其他 HTML 文档相同。你可以像创建和编辑其他 HTML 页面一样，创建并编辑包含 PHP 的不同网页。

PHP 语言语句通常包含在特定的 PHP 标签中。PHP 脚本可以放置在文档的任何位置。脚本以 `<?php` 开始，以 `?>` 结束。

```html
<html>
<head>
<title>这是一个 PHP 脚本外观所示的示例</title>
</head>
<body>
<?php echo "<h1>我们正在通过 PHP 进入应用开发的世界！</h1>\n"; ?>
</body>
</html>
```

```php
main.php
```

```html
<html>
<head>
<title>这是一个 PHP 脚本外观所示的示例</title>
</head>
<body>
<h1>我们正在通过 PHP 进入应用开发的世界！</h1>
</body>
</html>
```

浏览器不会在代码中显示 PHP 脚本。你也可以通过仅使用 `<?` 和 `?>` 使用更短版本的 PHP 标签。如果你启用了短标签，就可以节省一些时间。问题是，如果你将脚本移动到另一个未激活 PHP 短标签的 Web 主机，你的脚本将无法有效运行。

所有的 PHP 语句都在这些 PHP 标签之间处理。在浏览器处理 PHP 部分之后，它会将其丢弃。如果有输出，PHP 部分将被替换为输出，正如你在上面示例中所示。一个 PHP 脚本可以有多个部分。这里是示例。

```html
<html>
<head>
<title>这是一个 PHP 脚本外观所示的示例</title>
</head>
<body>
<?php echo "<h1>我们正在通过 PHP 进入应用开发的世界！</h1>\n"; ?>
<?php echo "<h2>我正在通过 PHP 学习应用开发！</h1>\n"; ?>
</body>
</html>
```

上述脚本的结果如下：

```php
main.php
```

```html
<html>
<head>
<title>这是一个 PHP 脚本外观所示的示例</title>
</head>
<body>
<h1>我们正在通过 PHP 进入应用开发的世界！</h1>
<h2>我正在通过 PHP 学习应用开发！</h2>
</body>
</html>
```

如果你熟悉 Python，你可能知道 Python 是区分大小大小的。这意味着在 Python 中，`class` 和 `CLASS` 两个单词是大小敏感的。让我们看看 PHP 如何处理各种大小写情况。

```html
<html>
<head>
<title>这是一个 PHP 脚本外观所示的示例</title>
</head>
<body>
<?php echo "<h1>我们正在通过 PHP 进入应用开发的世界！</h1>\n"; ?>
<?php Echo "<h2>我正在通过 PHP 学习应用开发！</h1>\n"; ?>
<?php ECHO "<h2>我正在通过 PHP 学习应用开发！</h1>\n"; ?>
</body>
</html>
```

我用三种不同的大小写写了相同的脚本。现在来看看结果。

```php
main.php
```

```html
<html>
<head>
<title>这是一个 PHP 脚本外观所示的示例</title>
</head>
<body>
<h1>我们正在通过 PHP 进入应用开发的世界！</h1>
<h2>我正在通过 PHP 学习应用开发！</h2>
<h2>我正在通过 PHP 学习应用开发！</h2>
</body>
</html>
```

所有的 PHP 关键字如 `if`、`class` 和 `echo` 都不区分大小写，但 PHP 变量是区分大小写的。

```html
<html>
<head>
<title>这是一个 PHP 脚本外观所示的示例</title>
</head>
<body>
<?php
$color = "blue";
echo "My car is " . $color . "<br>";
echo "My shoes is " . $COLOR . "<br>";
echo "My coat is " . $coLOR . "<br>";
?>
</body>
</html>
```

当大小写改变时，浏览器无法理解。如果你使用编辑器编写脚本，你将在页面底部看到错误消息。

```php
main.php
```

```html
<html>
<head>
<title>这是一个 PHP 脚本外观所示的示例</title>
</head>
<body>
My car is blue<br>
My shoes is <br>
My coat is <br>
</body>
</html>
```

PHP Notice: Undefined variable: COLOR in `/home/cg/root/3268398/main.php` on line 9
PHP Notice: Undefined variable: coLOR in `/home/cg/root/3268398/main.php` on line 10

### PHP 代码
PHP 代码应当对人类和 PHP 软件可读。当你为 Web 应用程序编写脚本时，你编写的脚本应该是易于维护的。你可以创建并以一种易于理解的方式编写。PHP 语句应该以单行编写并以分号结束。

### PHP 变量
通常，PHP 变量以 `$` 符号开头，后面跟着变量名。`echo` 用于显示输出。查看以下示例以了解如何在屏幕上显示。

```html
<html>
<head>
<title>这是一个 PHP 脚本外观所示的示例</title>
</head>
<body>
<?php
$txt = "amazing";
echo "PHP is " . $txt . ".";
?>
</body>
</html>
```

### 字符串
PHP 字符串是字符的形式。这些是数字、字母和标点。当字符串作为变量时，你告诉 PHP 它何时开始以及何时结束。使用双引号或单引号都有相同的结果。

```html
<html>
<head>
<title>这是一个 PHP 脚本外观所示的示例</title>
</head>
<body>
<?php
$string = "I am invited to Sally's house.";
echo $string;
?>
</body>
</html>
```

### 字符串连接
你可以通过被称为连接的连接来连接字符串。

```html
<html>
<head>
<title>这是一个 PHP 脚本外观所示的示例</title>
</head>
<body>
<?php
$string1 = "I am invited to Sally's house.";
$string2 = " Please join us and fun.";
$stringall = $string1.$string2;
echo $stringall;
?>
</body>
</html>
```

### Heredoc
PHP 提供了一种名为 heredoc 的功能，你可以用它来创建跨行的长字符串。Heredoc 允许你告诉 PHP 应该从哪里开始结束。`ENDSTRING` 可以包含你需要的任何内容。通过将 `ENDSTRING` 放在开头和结尾，你会封装想要存储在变量 `$varname` 中的文本。当 PHP 处理 heredoc 时，它会读取 `ENDSTRING` 并知道开始测试。

```html
<html>
<head>
<title>这是一个 PHP 脚本外观所示的示例</title>
</head>
<body>
<?php
$distance = 50;
$herevariable = <<<ENDOFTEXT
你可能会发现乌干和 Kira 镇之间的距离是 $distance 公里。
ENDOFTEXT;
echo $herevariable;
?>
</body>
</html>
```

### 数组
数组被认为是复杂的变量。特定的数组倾向于在一个变量名中存储一组值。这对于存储相关值非常有用。你可以存储关于某种花卉的颜色、品种和成本的信息。你可以处理、修改并访问这些信息。





# 第三章：创建 PHP 脚本

PHP 脚本通常指的是具有特定扩展名的文件中的系列指令，这些指令指示 Web 服务器在文件中查找 PHP 部分。该扩展名通常为 `.phtml` 和 `.php`。PHP 中的指令被标记为语句（statements），这些语句可以是简单的，也可以是复杂的。复杂语句往往执行一个或多个语句块。

## 条件

PHP 中的条件是 PHP 测试或评估的表达式，用以验证条件是否为真或假。PHP 条件通常以复杂语句的形式使用，用于检查填充有简单语句的块是否可以执行。你必须比较不同的值来设置条件。

### if 语句

当其中一个条件为真时，`if` 语句将执行代码。`if` 语句的第一部分（你将在示例中看到的）是 `if` 部分。如果条件为真，则执行该语句块。当它们被执行时，脚本将通过遵循条件语句跳转到下一条指令。如果条件语句拥有 `else-if` 或 `else` 部分，脚本将跳过它们。如果条件为假，则不执行该语句块。脚本将跳到下一条指令，该指令将是 `else-if`、`else`，或者 `if` 条件语句之后的任何其他后续指令。

`if` 语句中的另一个关键字是 `else`。这部分被认为是可选的。一个 `else` 可以集成到 `if` 语句中。它不是为了测试任何条件。然而，它的目的是执行一个语句块。当 `if` 部分和 `else-if` 部分不为真时，脚本往往进入 `else` 部分。

让我们尝试一个 `if else` 语句。

```html
<html>
<head>
<title>这是 PHP</title>
</head>
<body>
<?php
$t = date("H");
if ($t < "15") {
    echo "Welcome! I wish you a good day!";
} else {
    echo "Good night! I have to go now!";
}
?>
</body>
</html>
```

`$php main.php`

```html
<html>
<head>
<title>这是 PHP</title>
</head>
<body>
Welcome! I wish you a good day!
</body>
</html>
```

这是一个包含完整 `if-else` 语句的代码块。

```html
<html>
<head>
<title>这是 PHP</title>
</head>
<body>
<?php
$thescore = 100;
if ($thescore > 95 ) {
    $thegrade = "A";
    $themessage = "This is Excellent!";
} else-if ($thescore <= 95 and $thescore > 85 ) {
    $thegrade = "B";
    $themessage = "This is Very Good!";
} else-if ($thescore <= 85 and $thescore > 75 ) {
    $thegrade = "C";
    $themessage = "This is Okay. Not as much good as it should have";
} else-if ($thescore <= 75 and $thescore > 65 ) {
    $thegrade = "D";
    $themessage = "Not good. In fact really bad!";
} else {
    $thegrade = "F";
    $themessage = "You are doomed!";
}
echo $themessage."\n";
echo "Your grade is $thegrade\n";
?>
</body>
</html>
```

`$php main.php`

```html
<html>
<head>
<title>这是 PHP</title>
</head>
<body>
This is Excellent! Your grade is A
</body>
</html>
```

现在我将更改分数让第二个代码块工作。这是示例：

```html
<html>
<head>
<title>这是 PHP</title>
</head>
<body>
<?php
$thescore = 90;
if ($thescore > 95 ) {
    $thegrade = "n";
    $themessage = "This is Excellent!";
} else-if ($thescore <= 95 and $thescore > 85 ) {
    $thegrade = "B";
    $themessage = "This is Very Good!";
} else-if ($thescore <= 85 and $thescore > 75 ) {
    $thegrade = "C";
    $themessage = "This is Okay. Not as much good as it should have";
} else-if ($thescore <= 75 and $thescore > 65 ) {
    $thegrade = "D";
    $themessage = "Not good. In fact really bad!";
} else {
    $thegrade = "F";
    $themessage = "You are doomed!";
}
echo $themessage."\n";
echo "Your grade is $thegrade\n";
?>
</body>
</html>
```

`$php main.php`

```html
<html>
<head>
<title>这是 PHP</title>
</head>
<body>
This is Very Good! Your grade is B
</body>
</html>
```

在下面的示例中，我将输入小于 85 的值，以便第三个 `else-if` 语句生效。浏览器将忽略 `if 语句`和第一个 `else-if` 语句。

```html
<html>
<head>
<title>这是 PHP</title>
</head>
<body>
<?php
$thescore = 80;
if ($thescore > 95 ) {
    $thegrade = "n";
    $themessage = "This is Excellent!";
} else-if ($thescore <= 95 and $thescore > 85 ) {
    $thegrade = "B";
    $themessage = "This is Very Good!";
} else-if ($thescore <= 85 and $thescore > 75 ) {
    $thegrade = "C";
    $themessage = "This is Okay. Not as much good as it should have";
} else-if ($thescore <= 75 and $thescore > 65 ) {
    $thegrade = "D";
    $themessage = "Not good. In fact really bad!";
} else {
    $thegrade = "F";
    $themessage = "You are doomed!";
}
echo $themessage."\n";
echo "Your grade is $thegrade\n";
?>
</body>
</html>
```

`$php main.php`

```html
<html>
<head>
<title>这是 PHP</title>
</head>
<body>
This is Okay. Not as much good as it should have grade is C
</body>
</html>
```

让我们查看最后一个选项。

```html
<html>
<head>
<title>这是 PHP</title>
</head>
<body>
<?php
$thescore = 60;
if ($thescore > 95 ) {
    $thegrade = "n";
    $themessage = "This is Excellent!";
} else-if ($thescore <= 95 and $thescore > 85 ) {
    $thegrade = "B";
    $themessage = "This is Very Good!";
} else-if ($thescore <= 85 and $thescore > 75 ) {
    $thegrade = "C";
    $themessage = "This is Okay. Not as much good as it should have";
} else-if ($thescore <= 75 and $thescore > 65 ) {
    $thegrade = "D";
    $themessage = "Not good. In fact really bad!";
} else {
    $thegrade = "F";
    $themessage = "You are doomed!";
}
echo $themessage."\n";
echo "Your grade is $thegrade\n";
?>
</body>
</html>
```

`$php main.php`

```html
<html>
<head>
<title>这是 PHP</title>
</head>
<body>
You are doomed! Your grade is F
</body>
</html>
```

### 嵌套 if

你可以将一个 `if` 条件语句放在另一个 `if` 语句内部。这个过程被称为嵌套。假设你必须联系住在明尼苏达州的客户。你计划向他们的 ID 发送电子邮件，然后向那些没有地址的人发送信。你可以通过以下方法识别客户群。

```php
if ($thecustState == "ID") {
    if ($theEmailAdd = "") {
        $thecontactMethod = "letter";
    } else {
        $thecontactMethod = "contact through email";
    }
} else {
    $thecontactMethod = "there is none needed";
}
```

### Switch 语句

`switch` 语句旨在测试 `$variablename` 的值。脚本移动到 `case` 部分并执行语句，直到遇到 `break` 语句或 `switch` 结束。你可以使用 `switch` 语句来执行特定的代码。

```php
<?php
$thescore = 5;
switch ($thescore) {
    case "green":
        echo "This is green!";
        break;
    case "yellow":
        echo "This is yellow!";
        break;
    case "red":
        echo "This is red!";
        break;
    default:
        echo "This is something else!";
}
?>
```

## 循环

循环通常用于脚本中，当你需要设置一个重复执行的语句块时。PHP 循环可以无限重复。你可以创建一个包含世界国家名称的循环。循环将输出名称，直到满足它会停止的条件。循环可以给你目录中的某些文件名，直到目录为空。

### 循环类型

第一类型是 `for` 循环。它设置一个计数器来重复填充的语句块，直到计数器达到特定的数字。第二类型是 `while` 循环。它设置一个条件，检查该条件是否为真并重复某些语句直到条件为假。第三类型是 `do…while` 循环，它也设置一个条件。在之后执行语句块直到条件为假。有一个 `init` 计数器初始化循环的计数器值。然后有一个 `test` 计数器在循环的每次迭代中进行评估。如果评估为真，循环继续。否则，它结束。`increment` 计数器增加循环的计数器值。

```php
<?php
for ($y = 0; $y <= 20; $y++) {
    echo "The requisite number is $y";
}
?>
```

### 嵌套循环

你可以将一个 `for` 循环放在另一个 `for` 循环内部。我们可以使用两个 `for` 循环共同工作创建 1 到 12 的乘法表。

```php
<?php
for($a=1;$a<=12;$a++) {
    echo "\nMultiply by $a \n";
    for($b=1;$b<=12;$b++) {
        $result = $a * $b;
        echo "$a x $b = $result\n";
    }
}
?>
```





* 在开始时，你可以设置一个条件。
* 然后在每个单独循环的顶部测试该条件。
* 如果条件为真，循环将重复执行。如果条件为假，循环将停止。

### While 循环

这是一个 while 循环，它将整齐地显示蔬菜的名称。

```html
<html> <head> <title>This is PHP</title> </head> <body> <?php 
$vegetables = array ( "pumpkin", "carrot", "radish", "beet", "tomato", "potato"); 
$testvariable = "no"; 
$k = 0; 
while ( $testvariable != "yes" ) { 
    if ($vegetables[$k] == "tomato" ) { 
        $testvariable = "yes"; 
        echo "Now we have a tomato.\\n"; 
    } else { 
        echo "$vegetables[$k] is not a tomato\\n"; 
    } 
    $k++; 
} 
?> </body>
</html>
```

`$php main.php`

```html
<html> <head> <title>This is PHP</title> </head> <body> pumpkin is not a tomato carrot is not a tomato radish is not a tomato beet is not a tomato Now we have a tomato. </body> </html>
```

在接下来的示例中，我将改变蔬菜并观察循环是如何工作的。

```html
<html> <head> <title>This is PHP</title> </head> <body> <?php 
$vegetables = array ( "pumpkin", "carrot", "radish", "beet", "tomato", "potato"); 
$testvariable = "no"; 
$k = 0; 
while ( $testvariable != "yes" ) { 
    if ($vegetables[$k] == "potato" ) { 
        $testvariable = "yes"; 
        echo "Now we have a potato.\\n"; 
    } else { 
        echo "$vegetables[$k] is not a potato\\n"; 
    } 
    $k++; 
} 
?> </body>
</html>
```

`$php main.php`

```html
<html> <head> <title>This is PHP</title> </head> <body> pumpkin is not a potato carrot is not a potato radish is not a potato beet is not a potato tomato is not a potato Now we have a potato. </body> </html>
```

### Do...while 循环

do…while 循环倾向于在开始时循环一次特定的代码块，只要条件为真，它就会持续重复。它会执行一次代码，检查条件，然后只要条件为真就会重复循环。许多程序员将 `do...while` 循环和 `while` 循环放在同一个地方，然而，`do...while` 循环在循环底部测试一组条件。如果条件为真，循环就开始重复执行。如果条件为假，`do...while` 循环就会停止工作。

```html
<html> <head> <title>This is PHP</title> </head> <body> <?php 
$vegetables = array ( "pumpkin", "carrot", "radish", "beet", "tomato", "potato"); 
$testvariable = "no"; 
$k = 0; 
do { 
    if ($vegetables[$k] == "beet" ) { 
        $testvariable = "yes"; 
        echo "Now we have a beet.\\n"; 
    } else { 
        echo "$vegetables[$k] is not a potato\\n"; 
    } 
    $k++; 
} while ($testvariable != "yes"); 
?> </body>
</html>
```

`$php main.php`

```html
<html> <head> <title>This is PHP</title> </head> <body> pumpkin is not a potato carrot is not a potato radish is not a potato Now we have a beet. </body> </html>
```

在下段代码中，我将 beet 改为 potato。让我们看看代码的结果。

```html
<html> <head> <title>This is PHP</title> </head> <body> <?php 
$vegetables = array ( "pumpkin", "carrot", "radish", "beet", "tomato", "potato"); 
$testvariable = "no"; 
$k = 0; 
do { 
    if ($vegetables[$k] == "potato" ) { 
        $testvariable = "yes"; 
        echo "Now we have a potato.\\n"; 
    } else { 
        echo "$vegetables[$k] is not a potato\\n"; 
    } 
    $k++; 
} while ($testvariable != "yes"); 
?> </body>
</html>
```

`$php main.php`

```html
<html> <head> <title>This is PHP</title> </head> <body> pumpkin is not a potato carrot is not a potato radish is not a potato tomato is not a potato we have a potato. </body> </html>
```

如果你仔细观察上面的代码，你会发现 `while` 循环和 `do...while` 循环的输出是相同的。它们的区别在于，在 `while` 循环中条件在代码顶部检查，而在 `do...while` 循环中通常在代码底部检查。如果我们从一开始就将 `testvariable` 的值设置为 ‘yes’，那么代码块永远不会运行。

```html
<html> <head> <title>This is PHP</title> </head> <body> <?php 
$vegetables = array ( "pumpkin", "carrot", "radish", "beet", "tomato", "potato"); 
$testvariable = "yes"; 
$k = 0; 
do { 
    if ($vegetables[$k] == "potato" ) { 
        $testvariable = "yes"; 
        echo "Now we have a potato.\\n"; 
    } else { 
        echo "$vegetables[$k] is not a potato\\n"; 
    } 
    $k++; 
} while ($testvariable != "yes"); 
?> </body>
</html>
```

`$php main.php`

```html
<html> <head> <title>This is PHP</title> </head> <body> pumpkin is not a potato </body> </html>
```

### 无限循环

你可以设置无限循环。它们会永远运行。无限循环是无意创建的。无限循环会持续下去。无限循环被用于……无限循环的名称是……在代码顶部的循环。

```html
<html> <head> <title>This is PHP</title> </head> <body> <?php 
$vegetables = array ( "pumpkin", "carrot", "radish", "beet", "tomato", "potato"); 
$testvariable = "no"; 
$k = 0; 
while ( $testvariable != "yes" ) { 
    if ($vegetables[$k] == "tomato" ) { 
        $testvariable = "yes"; 
        echo "Now we have a tomato.\\n"; 
    } else { 
        echo "$vegetables[$k] is not a tomato\\n"; 
    } 
    $k++; 
} 
?> </body>
</html>
```

### Break 语句

Break 语句可以帮助你跳出循环。Break 语句更多用于 switch 语句。Break 语句在某一点停止了。

```html
<html> <head> <title>This is PHP</title> </head> <body> <?php 
$thecounter = 0; 
while ( $thecounter < 15 ) { 
    $thecounter++; 
    if ($thecounter == 13 ) { 
        echo "break\\n"; 
        break; 
    } 
    echo "This is the last line in the loop:$thecounter\\n"; 
} 
?> </body>
</html>
```

`$php main.php`

```html
<html> <head> <title>This is PHP</title> </head> <body> This is the last line in the loop: counter=1 This is the last line in the loop: counter=2 This is the last line in the loop: counter=3 This is the last line in the loop: counter=4 This is the last line in the loop: counter=5 This is the last line in the loop: counter=6 This is the last line in the loop: counter=7 This is the last line in the loop: counter=8 This is the last line in the loop: counter=9 This is the last line in the loop: counter=10 This is the last line in the loop: counter=11 This is the last line in the loop: counter=12 This is the last line in the loop: counter=13 break This is the last line in the loop: counter=14 </body>
</</html>
```

### Continue 语句

Continue 语句可以跳过。Continue 语句将继续循环。

```html
<html> <head> <title>This is PHP</title> </head> <body> <?php 
$thecounter = 0; 
while ( $thecounter < 12 ) { 
    $thecounter++; 
    if ($thecounter == 10 ) { 
        echo "this will continue the loop\\n"; 
        continue; 
    } 
    echo "This is the last line in the loop:counter=$thecounter\\n"; 
} 
?> </body>
</html>
```

`$php main.php`

```html
<html> <head> <title>This is PHP</title> </head> <body> This is the last line in the loop: counter=1 This is the last line in the loop: counter=2 This is the last line in the loop: counter=3 This is the last line in the loop: counter=4 This is the last line in the loop: counter=5 This is the last line in the loop: counter=6 This is the last line in the loop: counter=7 This is the last line in the loop: counter=8 This is the last line in the loop: counter=9 this will continue the loop This is the last line in the loop: counter=11 This is the last line in the loop: counter=12 break </body>
</</html>
```

如果你担心无限循环，可以在代码中插入 `break` 语句。





# 第四章：高级 PHP

应用程序通常需要在脚本的多个位点执行多个任务。PHP 函数允许你根据需要在多个位置复用相同的代码。函数通常来说是 PHP 中的一组语句，设计用于执行特定的任务。

## PHP 函数

在接下来的示例中，我将创建一个 PHP 函数示例。函数中的大括号标记了函数的开始和结束。当你需要调用函数时，只需简单编写它的名称即可。

```html
<<html>
<head>
    <title>This is PHP function</title>
</head>
<body>
<?php
function greetings() { 
    echo "Good morning! Hope you are fine!"; 
}
greetings(); // 这就是调用函数的方式
?>
</body>
</html>
```

```bash
$php main.php
```

```html
<html
<head>
    <title>This is PHP function</title>
</head>
<body>
    Good morning! Hope you are fine!
</body>
</html>
```

看另一个示例。

```html
<html
<head>
    <title>This is PHP function</title>
</head>
<body>
<?php
function format_your_name() { 
    global $formatted_name; 
    $your_first_name = "Chris"; 
    $your_last_name = "Angel"; 
    $formatted_name = $your_last_name. "," .$your_first_name; 
}
format_your_name();
echo "$formatted_name";
?>
</body>
</html>
```

```bash
$php main.php
```

```html
<html
<head>
    <title>This is PHP function</title>
</head>
<body>
    Angel,Chris
</body>
</html>
```

如果你必须在函数外部创建变量，除非在代码中插入全局变量，否则你无法这样做。请参见变量放置在脚本外部的示例。

## 参数

你可以通过参数向函数传递信息。参数的作用就像变量一样。它们指定在函数名称后面的括号内。你可以向函数中添加任意数量的变量。

```html
<html
<head>
    <title>This is PHP function</title>
</head>
<body>
<?php
function greetings($name) { 
    echo "$name, welcome to the bachelor's club.<br>"; 
}
greetings("John");
greetings("Sylvia");
greetings("Sim");
greetings("Kai Jim");
greetings("Ben");
?>
</body>
</html>
```

```bash
$php main.php
```

```html
<html
<head>
    <title>This is PHP function</title>
</head>
<body>
    John, welcome to the bachelor's club.<br>
    Sylvia, welcome to the bachelor's club.<br>
    Sim, welcome to the bachelor's club.<br>
    Kai Jim, welcome to the bachelor's club.<br>
    Ben, welcome to the bachelor's club.<br>
</body>
</html>
```

你还可以通过添加更多参数来扩展脚本。在下一个示例中，我将在脚本中添加两个参数。

```html
<html
<head>
    <title>This is PHP function</title>
</head>
<body>
<?php
function greetings($name, $year) { 
    echo "$name, welcome to the adult's club. I suppose you are born in $year <br>"; 
}
greetings("John" , "1999");
greetings("Sylvia" , "1988");
greetings("Sim" , "1995");
greetings("Kai Jim" , "2001");
greetings("Ben" , "2002");
?>
</body>
</html>
```

```bash
$php main.php
```

```html
<html
<head>
    <title>This is PHP function</title>
</head>
<body>
    John, welcome to the adult's club. I suppose you are born in 1999 <br>
    Sylvia, welcome to the adult's club. I suppose you are born in 1988 <br>
    Sim, welcome to the adult's club. I suppose you are born in 1995 <br>
    Kai Jim, welcome to the adult's club. I suppose you are born in 2001 <br>
    Ben, welcome to the adult's club. I suppose you are born in 2002 <br>
</body>
</html>
```

## 默认值

你可以为参数使用默认值，这样如果你留空参数部分仍然可以调用函数。

```html
<html
<head>
    <title>This is PHP function</title>
</head>
<body>
<?php
function greetings($name = "Tom", $year = 1996) { 
    echo "$name, welcome to the adult's club. I suppose you are born in $year <br>";
}
greetings("John" , "1999");
greetings("Sylvia" , "1988");
greetings();
greetings("Kai Jim" , "2001");
greetings();
?>
</body>
</html>
```

```bash
$php main.php
```

```html
<html
<head>
    <title>This is PHP function</title>
</head>
<body>
    John, welcome to the adult's club. I suppose you are born in 1999 <br>
    Sylvia, welcome to the adult's club. I suppose you are born in 1988 <br>
    Tom, welcome to the adult's club. I suppose you are born in 1996 <br>
    Kai Jim, welcome to the adult's club. I suppose you are born in 2001 <br>
    Tom, welcome to the adult's club. I suppose you are born in 1996 <br>
</body>
</html>
```

## 返回值

如果你想让函数返回值，必须在代码中插入 `return` 语句。

```html
<html
<head>
    <title>This is PHP function</title>
</head>
<body>
<?php
function sumup(int $a, int $b) { 
    $c = $a + $b; 
    return $c;
}
echo "45 + 10 = " . sumup(45, 10) . "<br>";
echo "57 + 13 = " . sumup(57, 13) . "<br>";
echo "29 + 41 = " . sumup(29, 41);
?>
</body>
</html>
```

```bash
$php main.php
```

```html
<html
<head>
    <title>This is PHP function</title>
</head>
<body>
    45 + 10 = 55<br>
    57 + 13 = 70<br>
    29 + 41 = 70
</body>
</html>
```

## 插入正确的参数

函数对你需要传递的值非常敏感。如果你发送的值不够，函数将检测到缺失的值。当你执行代码时会看到警告消息。

```html
<html
<head>
    <title>This is PHP function</title>
</head>
<body>
<?php
function greetings($name , $year) { 
    echo "$name, welcome to the adult's club. I suppose you are born in $year <br>"; 
}
greetings("John" , 1999);
greetings( "Sim", 1988);
greetings("Drake" , 2000);
greetings("Kai Jim" , 2001);
greetings( 2002);
?>
</body>
</html>
```

```bash
$php main.php
```

```html
<html
<head>
    <title>This is PHP function</title>
</head>
<body>
    John, welcome to the adult's club. I suppose you are born in 1999 <br>
    Sim, welcome to the adult's club. I suppose you are born in 1988 <br>
    Drake, welcome to the adult's club. I suppose you are born in 2000 <br>
    Kai Jim, welcome to the adult's club. I suppose you are born in 2001 <br>
     PHP Fatal error: Uncaught ArgumentCountError: Too few arguments to function greetings(), 1 passed in /home/cg/root/1842013/main.php on line 15 and exactly 2 expected in /home/cg/root/1842013/main.php:7 Stack trace: #0 /home/cg/root/1842013/main.php(15): greetings(2002) #1 {main} thrown in /home/cg/root/1842013/main.php on line 7
</body>
</html>
```

你可以看到缺失参数触发的错误。





# 第五章：面向对象编程

面向对象编程（OOP）是一种围绕类和对象的特殊编程方法。它是目前 PHP 最流行的用法之一。PHP5 的发布是作为面向对象编程的改进版本。它具有更快的速度和更改进的功能。面向对象编程，缩写为 OOP，并不是关于使用不同的语法，而是关于为你提供一种不同的分析问题并刻画其解决方案的方法。在 OOP 中，脚本被视为一组不同的对象，这些对象代表了脚本必须解决的问题元素。如果脚本是关于一个二手车交易场的，那么对象可以是客户和汽车。OOP 带来了新的概念和术语。

## 类 (Classes)

面向对象编程的基本元素之一是对象。你可以将它们看作代码形式的物理对象。一个 PHP 对象可以是一辆汽车、一只猫或一只狗。你可以给它们赋予某些属性，在编程世界中被称为属性（attributes）。例如，猫可以有坐下、在地上滚等属性。汽车可以有颜色、型号和公司名称等属性。

PHP 代码中的类充当用于创建对象的模板。类通常定义了特定对象的属性。它还会定义对象所执行的一系列操作，例如它的职责。你写了一个类来定义一个带有引擎和四个轮子的汽车。该类列出了汽车可以做的事情，比如它可以向前移动也可以停车。

你也可以写像下面这样的语句：

```html
<html
<head>
<title>这是一个 PHP 函数示例</title>
</head>
<body>
<?php
class Vegetables {
    // 这些是属性 (Properties)
    public $vname;
    public $vcolor;
    // 这些是方法 (Methods)
    function set_name($vname) {
        $this->vname = $vname;
    }
    function get_name() {
        return $this->vname;
    }
}
?>
</body>
</html>
```

在类中，变量被标记为属性（properties），而函数被称为方法（methods）。没有对象，类一无是处。你可以自由地从一个类中创建大量的对象。每个对象都包含该类中定义的某些属性和方法，但是它们的属性值是不同的。`new` 关键字用于创建类的对象。然后是 `Vegetables` 类的实例。

```html
<<html>
<head>
<title>这是一个 PHP 函数示例</title>
</head>
<body>
<?php
class Vegetables {
    // 这些是属性 (Properties)
    public $vname;
    public $vcolor;
    // 这些是方法 (Methods)
    function set_name($vname) {
        $this->vname = $vname;
    }
    function get_name() {
        return $this->vname;
    }
}
$potato = new Vegetables();
$beet = new Vegetables();
$potato->set_name('Potato');
$beet->set_name('Beet');
echo $potato->get_name();
echo "<br>";
echo $beet->get_name();
?>
</body>
</html>
```
`$php main.php`

```html
<html>
<head>
<title>这是一个 PHP 函数示例</title>
</head>
<body>
Potato<br>Beet
</body>
</html>
```

在下一个代码段中，我将向同一个蔬菜类再添加两个方法。我添加了用于给对象添加颜色的方法。

```html
<html>
<head>
<title>这是一个 PHP 函数示例</title>
</head>
<body>
<?php
class Vegetables {
    // 这些是属性 (Properties)
    public $vname;
    public $vcolor;
    // 这些是方法 (Methods)
    function set_name($vname) {
        $this->vname = $vname;
    }
    function get_name() {
        return $this->vname;
    }
    function set_color($vcolor) {
        $this->vcolor = $vcolor;
    }
    function get_color() {
        return $this->vcolor;
    }
}
$potato = new Vegetables();
$beet = new Vegetables();
$potato->set_name('Potato');
$potato->set_color('Red');
$beet->set_name('Beet');
$beet->set_color('Blue');
echo $potato->get_name();
echo "Color: " . $potato->get_color();
echo "<br>";
echo $beet->get_name();
echo "<br>";
echo "Color: " . $beet->get_color();
?>
</body>
</html>
```
`$php main.php`

```html
<html>
<head>
<title>这是一个 PHP 函数示例</title>
</head>
<body>
PotatoColor: Red<br>Beet<br>Color: Blue
</body>
</html>
```

## 蔬菜类 (Vegetable Class)

当你必须定义一个类时，你应该在最顶部声明属性。不需要声明变量。你可以根据自己的需要直接使用它们，而无需先声明。然而，在创建类时声明属性会更好。这使得类变得更容易理解。如果你遗漏了，会被认为是一种糟糕的编程习惯。

你为每个属性需要一个关键字，以决定如何访问它们：

- `public` 关键字：可以在类外部的另一个类或脚本中访问。
- `private` 关键字：无法从类的外部访问属性。
- `protected` 关键字：可以在类内部或其子类中访问。

## 构造函数 (Constructor Function)

PHP 构造允许你在创建对象时初始化对象的属性。当你从类中创建一个对象时，PHP 会调用该函数。

```html
<html>
<head>
<title>这是一个 PHP 函数示例</title>
</head>
<body>
<?php
class Vegetables {
    // 这些是属性 (Properties)
    public $vname;
    public $vcolor;
    // 这些是方法 (Methods)
    function __construct($vname) {
        $this->vname = $vname;
    }
    function get_name() {
        return $this->vname;
    }
}
$potato = new Vegetables("Potato");
echo $potato->get_name();
?>
</body>
</html>
```
`$php main.php`

```html
<html>
<head>
<title>这是一个 PHP 函数示例</title>
</head>
<body>
Potato
</body>
</html>
```

我将向现有代码中添加另一个颜色功能。查看 `__construct` 中的更改。

```html
<html>
<head>
<title>这是一个 PHP 函数示例</title>
</head>
<body>
<?php
class Vegetables {
    // 这些是属性 (Properties)
    public $vname;
    public $vcolor;
    public $weight;
    public $shape;
    // 这些是方法 (Methods)
    function __construct($vname, $vcolor, $weight, $shape) {
        $this->vname = $vname;
        $this->vcolor = $vcolor;
        $this->weight = $weight;
        $this->shape = $shape;
    }
    function get_name() {
        return $this->vname;
    }
    function get_color() {
        return $this->vcolor;
    }
    function get_weight() {
        return $this->weight;
    }
    function get_shape() {
        return $this->shape;
    }
}
$potato = new Vegetables("Potato", "Red", 50, "round");
echo $potato->get_name();
echo "<br>";
echo $potato->get_color();
echo "<br>";
echo $potato->get_weight();
echo "<br>";
echo $potato->get_shape();

$beet = new Vegetables("Beet", "Blue", 50, "round");
echo $beet->get_name();
echo "<br>";
echo $beet->get_color();
echo "<br>";
echo $beet->get_weight();
echo "<br>";
echo $beet->get_shape();

$tomato = new Vegetables("Tomato", "Red", 100, "round");
echo $tomato->get_name();
echo "<br>";
echo $tomato->get_color();
echo "<br>";
echo $tomato->get_weight();
echo "<br>";
echo $tomato->get_shape();

$turnip = new Vegetables("Turnip", "White", 150, "round");
echo $turnip->get_name();
echo "<br>";
echo $turnip->get_color();
echo "<br>";
echo $turnip->get_weight();
echo "<br>";
echo $turnip->get_shape();
?>
</body>
</html>
```
`$php main.php`

```html
<html>
<head>
<title>这是一个 PHP 函数示例</title>
</head>
<body>
Potato
Red
50
round
Beet
Blue
50
round
Tomato
Red
100
round
Turnip
White
150
round
</body>
</html>
```

## 析构函数 (Destructor)

当对象被销毁或脚本停止或退出时，你需要调用 `__destruct()`。如果你有机会创建一个 `__destruct()` 函数，PHP 在脚本结束时调用它。和构造函数一样，析构函数也以两个下划线开头。

```html
<html>
<head>
<title>这是一个 PHP 函数示例</title>
</head>
<body>
<?php
class Vegetables {
    // 这些是属性 (Properties)
    public $vname;
    public $vcolor;
    // 这些是方法 (Methods)
    function __construct($vname, $vcolor) {
        $this->vname = $vname;
        $this->vcolor = $vcolor;
    }
    function __destruct() {
        echo "The vegetable is {$this->vname} and the color is {$this->vcolor}.";
    }
}
$potato = new Vegetables("Potato", "Brown");
$beet = new Vegetables("Beet", "Red");
?>
</body>
</html>
```
`$php main.php`

```html
<html>
<head>
<title>这是一个 PHP 函数示例</title>
</head>
<body>
</body>
</html>
```
The vegetable is Beet and the color is Red. The vegetable is Potato and the color is Brown.

## PHP 访问修饰符 (PHP Access Modifiers)

PHP 属性和方法通常有访问修饰符来控制它们如何被访问。通常有三种修饰符：`public`、`protected` 和 `private`。

- `public` 修饰符：可以在任何地方访问。
- `protected` 修饰符：可以在类内部以及派生自类中访问。
- `private` 修饰符：只能在类内部访问。

在这个例子中，我为上述属性添加了三种不同的访问修饰符。如果你设置 name 属性将会成功。但是如果你设置 weight 或 color 属性将会报错。

```html
<html>
<head>
<title>这是一个 PHP 函数示例</title>
</head>
<body>
<?php
class Vegetable {
    public $vname;
    protected $vcolor;
    private $weight;
}
$beet = new Vegetable();
$beet->vname = 'Beet'; // OK
$beet->vcolor = 'Purplish Red'; // 将触发 ERROR
$beet->weight = '50'; // 将触发 ERROR
?>
</body>
</html>
```
PHP Fatal error: Uncaught Error: Cannot access protected property Vegetable::$vcolor in /home/cg/root/27113/main.php:15
Stack trace: #0 {main} thrown in /home/cg/root/27113/main.php on 15

## 继承 (Inheritance)

OOP 中的继承意味着一个类派自另一个类。子类倾向于继承父类几乎所有的保护和公共方法及属性。它也可以拥有自己的方法和属性。你可以使用 `extends` 关键字来定义它。

```html
<html>
<head>
<title>这是一个 PHP 函数示例</title>
</head>
<body>
<?php
class Vegetable {
    public $vname;
    public $vcolor;
    function __construct($vname, $vcolor) {
        $this->vname = $vname;
        $this->vcolor = $vcolor;
    }
    public function intro() {
        echo "The vegetable is {$this->vname} and its color is {$this->vcolor}.";
    }
}
// The beet is inherited from Vegetable
class Beet extends Vegetable {
    public function message() {
        echo "Does beet taste like fruit or vegetable?";
    }
}
$beet = new Beet("Beet", "purplish red");
$beet->message();
$beet->intro();
?>
</body>
</html>
```
`$php main.php`

```html
<html>
<head>
<title>这是一个 PHP 函数示例</title>
</head>
<body>
The vegetable is Beet and its color is purplish red.
</body>
</html>
```

由于 `Beet` 派自 `Vegetable` 类，它可以使用主类中的 `vname` 和 `vcolor` 属性以及其他方法。它也有自己的名为 `message` 的方法。在下一个例子中，我将主类的函数从 `public` 为 `protected`。你将在编辑器屏幕上看到一个致命错误。

```html
<html>
<head>
<title>这是一个 PHP 函数示例</title>
</head>
<body>
<?php
class Vegetable {
    public $vname;
    public $vcolor;
    function __construct($vname, $vcolor) {
        $this->vname = $vname;
        $this->vcolor = $vcolor;
    }
    protected function intro() {
        echo "The vegetable is {$this->vname} and its color is {$this->vcolor}.";
    }
}
// The beet is inherited from Vegetable
class Beet extends Vegetable {
    public function message() {
        echo "Does beet taste like fruit or vegetable?";
    }
}
$beet = new Beet("Beet", "purplish red");
$beet->message();
$beet->intro();
?>
</body>
</html>
```
`$php main.php`

```html
<html>
<head>
<title>这是一个 PHP 函数示例</title>
</head>
<body>
PHP Fatal error: Uncaught Error: Call to protected method Vegetable::intro() in /home/cg/root/27113/main.php:27
Stack trace: #0 {main} thrown in /home/cg/root/27113/main.php on 27
```

有一个解决这个问题的方法。我们可以在派生类内部调用保护的 `intro()` 方法。

```html
<html>
<head>
<title>这是一个 PHP 函数示例</title>
</head>
<body>
<?php
class Vegetable {
    public $vname;
    public $vcolor;
    function __construct($vname, $vcolor) {
        $this->vname = $vname;
        $this->vcolor = $vcolor;
    }
    protected function intro() {
        echo "The vegetable is {$this->vname} and its color is {$this->vcolor}.";
    }
}
// The beet is inherited from Vegetable
class Beet extends Vegetable {
    public function message() {
        echo "Does beet taste like fruit or vegetable?";
    }
    public function intro() {
        // 现在在派生类内部调用该方法
        $this->intro();
    }
}
$beet = new Beet("Beet", "purplish red");
$beet->message();
$beet->intro();
?>
</body>
</html>
```

## 重写继承 (Overriding Inheritance)

如果在子类中重新定义继承的方法，就可以进行重写。在下面的例子中，我将重写它们。

```html
<html>
<head>
<title>这是一个 PHP 函数示例</title>
</head>
<body>
<?php
class Vegetable {
    public $vname;
    public $vcolor;
    function __construct($vname, $vcolor) {
        $this->vname = $vname;
        $this->vcolor = $vcolor;
    }
    public function intro() {
        echo "The vegetable is {$this->vname} and its color is {$this->vcolor}.";
    }
}
// The beet is inherited from Vegetable
class Beet extends Vegetable {
    public $vweight;
    function __construct($vname, $vcolor, $vweight) {
        $this->vname = $vname;
        $this->vcolor = $vcolor;
        $this->weight = $vweight;
    }
    public function intro() {
        echo "The vegetable is {$this->vname} and its color is {$this->vcolor}, and its size is {$vweight}";
    }
}
$beet = new Beet("Beet", "purplish red", 500);
$beet->intro();
?>
</body>
</html>
```
`$php main.php`

```html
<html>
<head>
<title>这是一个 PHP 函数示例</title>
</head>
<body>
The vegetable is Beet and its color is purplish red, and its size is 500
</body>
</html>
```

你可以通过在脚本中插入 `final` 关键字来防止重写。

```html
<html>
<head>
<title>这是一个 PHP 函数示例</title>
</head>
<body>
<?php
final class Vegetable {
    public $vname;
    public $vcolor;
    function __construct($vname, $vcolor) {
        $this->vname = $vname;
        $this->vcolor = $vcolor;
    }
    public function intro() {
        echo "The vegetable is {$this->vname} and its color is {$this->vcolor}.";
    }
}
// The beet is inherited from Vegetable
class Beet extends Vegetable {
    public $vweight;
    function __construct($vname, $vcolor, $vweight) {
        $this->vname = $vname;
        $this->vcolor = $vcolor;
        $this->weight = $vweight;
    }
    public function intro() {
        echo "The vegetable is {$this->vname} and its color is {$this->vcolor}.";
    }
}
$beet = new Beet("Beet", "purplish red", 500);
$beet->intro();
?>
</body>
</html>
```
`$php main.php` PHP Fatal error: Class Beet may not inherit from final class (Vegetable) in /home/cg/root/271113/main.php on line 30

## 抽象类 (Abstract Class)

当你继承抽象类时，子类方法应当以相同的名称和限制较少的修饰符定义。如果抽象方法定义为 `protected`，则子类方法需要定义为 `public` 或 `protected`。所需参数的数量和类型应当相同。

```html
<html>
<head>
<title>这是一个 PHP 函数示例</title>
</head>
<body>
<?php
abstract class Vegetable {
    public $vname;
    public $vcolor;
    function __construct($vname, $vcolor) {
        $this->vname = $vname;
        $this->vcolor = $vcolor;
    }
    abstract protected function intro();
}
class Beet extends Vegetable {
    public function intro() {
        echo "The vegetable is {$this->vname} and its color is {$this->vcolor}.";
    }
}
class Onion extends Vegetable {
    protected function intro() {
        echo "The vegetable is {$this->vname} and its color is {$this->vcolor}.";
    }
}
class Pumpkin extends Vegetable {
    public function intro() {
        echo "The vegetable is {$this->vname} and its color is {$this->vcolor}.";
    }
}
class Radish extends Vegetable {
    protected function intro() {
        echo "The vegetable is {$this->vname} and its color is {$this->vcolor}.";
    }
}
class Tomato extends Vegetable {
    public function intro() {
        echo "The vegetable is {$this->vname} and its color is {$this->vcolor}.";
    }
}
$beet = new Beet("Beet", "purplish red");
$beet->intro();
$onion = new Onion("Onion", "white");
$onion->intro();
$pumpkin = new Pumpkin("Pumpkin", "green");
$pumpkin->intro();
$radish = new Radish("Radish", "red");
$radish->intro();
$tomato = new Tomato("Tomato", "red");
$tomato->intro();
?>
</body>
</html>
```

## 抽象类示例 (Abstract Class Examples)

```html
<html>
<head>
<title>这是一个 PHP 函数示例</title>
</head>
<body>
<?php
abstract class ParentClass {
    // This is an Abstract method with an argument
    abstract protected function prefixName($name);
}
class ChildClass extends ParentClass {
    public function prefixName($vname) {
        if ($vname == "John Snow") {
            $theprefix = "Mister.";
        } else-if ($vname == "Jane Snow") {
            $theprefix = "Mrs.";
        } else {
            $theprefix = "";
        }
        return "{$theprefix} {$vname}";
    }
}
$class = new ChildClass();
echo $class->prefixName("John Snow");
echo "<br>";
echo $class->prefixName("Jane Snow");
?>
</body>
</html>
```
`$php main.php`

Mister. John Snow
Mrs. Jane Snow

```

The vegetable is Beet and its color is purplish red
The vegetable is Onion and white
The vegetable is Pumpkin and green
The vegetable is Radish and red
The vegetable is Tomato and red





# 第六章：PHP 表单与文件处理

PHP 超全局变量如 `$_POST` 和 `$_GET` 通常用于收集表单数据。本章将带你逐步了解如何创建和处理 PHP 表单。

我将从一个带有两个输入字段的简单 HTML 表单开始。它还将包含一个提交按钮，用户填写信息并点击提交按钮即可完成操作。你可以构建一个 Web 应用并将表单集成其中，以便从用户那里获取所需的某些信息。

```html
<html>
<body>
<form action="Wewelcomeyou.php" method="post">
  Name: <input type="text" name="Please enter your name"><br>
  E-mail: <input type="text" name="Please enter your email"><br>
  <input type="submit">
</form>
</body>
</html>
```




当用户填写表单并点击提交按钮时，数据将传递到一个名为 `Wewelcomeyou.php` 的 PHP 文件进行处理。表单通过 `HTTP POST` 方法发送。如果你想显示提交的数据，可以简单地 `echo` 这些变量。如果你使用 `$GET` 方法发送表单，它对所有人可见。所有的名称和值都将显示在 URL 中。它还对你想要发送的信息大小有限制。变量将显示在 URL 中，因此无法在该页面上创建书签。你也可以使用 `POST` 方法创建表单，但问题是在此方法中，信息将对其他人可见。

在下一个代码示例中，你将看到新的变量，它们将帮助你为所有必填字段添加错误消息。对于每个 `$_POST` 变量都会有一个 `if-else` 语句。它将检查 `$_POST` 变量是否为空，如果不为空，你会看到封装在不同错误变量中的错误消息。它通过 `test_input()` 函数发送用户输入。

```html
<html>
<head>
    <title>这是 PHP</title>
</head>
<body>
<?php
    // 你应该定义变量并将它们置为空
    $pnameErr = $pemailErr = $pgenderErr = $pwebsiteErr = "";
    $pname = $pemail = $pgender = $pcomment = "";
    if ($_SERVER["REQUEST_METHOD"] == "POST") {
        if (empty($_POST["name"])) {
            $pnameErr = "你需要姓名";
        } else {
            $pname = test_input($_POST["name"]);
        }
        if (empty($_POST["email"])) {
            $pemailErr = "你需要邮箱";
        } else {
            $pemail = test_input($_POST["email"]);
        }
        if (empty($_POST["website"])) {
            $pwebsiteErr = "";
        } else {
            $pwebsite = test_input($_POST["website"]);
        }
        if (empty($_POST["comment"])) {
            $pcomment = "";
        } else {
            $pcomment = test_input($_POST["comment"]);
        }
        if (empty($_POST["gender"])) {
            $pgenderErr = "你需要性别";
        }
 else {
            $pgender = test_input($_POST["gender"]);
        }
    }
?>
</body>
</html>
```

## PHP 文件处理
异常处理是程序员认为软件开发中最困难的部分。程序错误、网络故障和数据库故障为程序员带来了许多严重问题。开发者应该在编写阶段检测故障，添加检查，并调用相应的函数来管理它们。异常帮助你在无需编写 `if` 语句的情况下编写强大的程序。

PHP 日期有很多类型。添加到 Web 应用程序中最基本的方法是 PHP `date()` 函数。该函数的格式参数指定了如何格式化日期和时间。查看用于日期的字符：
- `d` 字符代表每月 01 到 31。
- `m` 字符代表每年 01 到 12。
- `Y` 参数代表四位数的年份。
- `l` 代表星期。

```html
<html>
<head>
    <title>这是 PHP</title>
</head>
<body>
<?php
    echo "日期是 " . date("Y/m/d") . "<br>";
    echo "日期是 " . date("Y.m.d") . "<br>";
    echo "日期是 " . date("Y-m-d") . "<br>";
    echo "星期是 " . date("l");
?>
</body>
</html>
```

```php
main.php
```
```html
<html>
<head>
    <title>这是 PHP</title>
</head>
<body>
    日期是 2020/06/23<br>
    日期是 2020.06.23<br>
    日期是 2020-06-23<br>
    今天是星期二
</body>
</html>
```

当新年开始时，你可以通过以下方法更新 Web 应用程序的版权年份：
`&copy; 2020-<?php echo date("Y");?>`

这是一个让 PHP 估计四个月后准确日期的示例：

```html
<html>
<head>
    <title>这是 PHP</title>
</head>
<body>
<?php
    $d=strtotime(" tomorrow ");
    echo date("m-d-y h:i:sa", $d) . "<br>";
    $d=strtotime(" next Friday ");
    echo date(" m-d-y h:i:sa ", $d) . "<br>";
    $d=strtotime(" +4 Months ");
    echo date(" m-d-y h:i:sa ", $d) . "<br>";
    $d=strtotime(" +8 Months ");
    echo date(" m-d-y h:i:sa ", $d) . "<br>";
    $d=strtotime("+1 Month ");
    echo date(" m-d-y h:i:sa ", $d) . "<br>";
    $d=strtotime(" next Wednesday ");
    echo date(" m-d-y h:i:sa ", $d) . "<br>";
?>
</body>
</html>
```

```php
main.php
```
```html
<html
<head>
    <title>这是 PHP</title>
</head>
<body>
    06-24-20 12:00:00am<br>
    06-26-20 12:00:00am <br>
    10-23-20 05:13:14am<br>
    02-23-21 05:13:14am<br>
    07-23-20 05:13:14am<br>
    06-24-20 12:00:00am<br>
</body>
</html>
```

### 更多示例
```html
<html
<head>
    <title>这是 PHP</title>
</head>
<body>
<?php
    $thestartdate = strtotime("Friday");
    $theenddate = strtotime("+36 weeks", $thestartdate);
    while ($thestartdate < $theenddate) {
        echo date("M d Y", $thestartdate) . "<br>";
        $thestartdate = strtotime("+1 day", $thestartdate);
    }
?>
</body>
</html>
```

```php
main.php
```
```html
<html
<head>
    <title>这是 PHP</title>
</head>
<body>
    <!-- 为了简洁，省略日期循环的输出 -->
</body>
</html>
```

### 包含因素
为了在页面中包含底部文件，你应该使用 `include` 语句。

```html
<html
<head>
    <title>这是 PHP</title>
</head>
<body>
<?php include 'footer.php'; ?>
</body>
</html>
```




# 第七章：MySQL 基础

许多网站都需要一个后端数据库，用于存储网页显示给用户的信息，或存储用户在网站上填写的信息。MySQL 是一种非常流行的数据库，可用于网站。它被开发为一种为网站提供的轻量且快速的系统。MySQL 在使用 PHP 编写的网站中特别受欢迎。简而言之，MySQL 和 PHP 通常配合得很好。

MySQL 包含一个 MySQL 服务器、一组辅助管理 MySQL 数据库的实用程序，以及 MySQL 服务器需要的一些辅助软件。MySQL 服务器被认为是数据库系统的管理器。它可以处理所有的数据库指令。MySQL 被称为关系型数据库系统 (RDBMS)。MySQL 服务器倾向于同时管理多个数据库。许多人可能共同控制由一个 MySQL 服务器管理的不同数据库。

每个数据库都有一个存储数据的结构。通常情况下，数据库在没有数据的情况下存在。你可以以表的形式将数据存储在数据库中。向数据库添加数据之前，必须先创建表。开始时创建一个空数据库，稍后再填充数据。表中的每一行都代表一个实体，例如书籍或项目。每一列承载关于实体的一个信息，例如书名或客户名。一个数据库包含一个或多个表，每个表都可以通过特定的名称来识别。就像普通表一样，MySQL 表包含列和行。我将在这些脚本中使用一个数据库。

## MySQL 查询

它大部分是英语。由英语短语和句子组成。你不需要看透并学习一种晦涩的技术语言来编写查询。语句的第一个单词是它的名称。它是一个动词，告诉 MySQL 你想让它做什么。本章将讨论这些语句。你无法在系统上安装或卸载 MySQL，因为它运行在网络托管计算机上。你可以通过账户访问 MySQL 中的数据。

### SQL SELECT

第一行是 `SQL select` 语句。我有一个目前存在于数据库中的演示数据库。你数据库中的表如下所示。

| CustomerID | CustomerName | ContactNumber | SecretCode | Country |
| --- | --- | --- | --- | --- |
| 1 | Emily Jack | 55779034 | 45 | United States |
| 2 | Jason Austin | 34568988 | 2 | United Kingdom |
| 3 | Amanda McMahon | 34578899 | 1 | Ireland |
| 4 | Victoria Ann | 23768800 | 67 | Germany |
| 5 | Simon Wiz | 45327899 | 9 | United States |
| 6 | Tracy Drupal | 23897609 | 8 | France |
| 7 | Emilia Tim | 45890093 | 3 | Italy |
| 8 | Tyson Jackson | 34980900 | 2 | Sweden |

这就是我们拥有的内容，我们可以通过 SQL 语句访问它。如果你想显示整个表，可以使用以下语句。

```sql
SELECT * FROM Members;
```

在该语句中，`Members` 是上述表的名字。其余部分属于 `SQL`。如果使用得当，`Select` 语句非常有趣。你可以用它来显示表中不同的列。例如，假设你在一家拥有上述数据库的机构工作。你的老板要求你打印成员列表及其原籍国，而忽略数据库的其他部分。你可以使用以下语句在几秒钟内完成。

```sql
SELECT CustomerName, Country FROM Members;
```

| CustomerName | Country |
| --- | --- |
| Emily Jack | United States |
| Jason Austin | United Kingdom |
| Amanda McMahon | Ireland |
| Victoria Ann | Germany |
| Simon Wiz | United States |
| Tracy Drupal | France |
| Emilia Tim | Italy |
| Tyson Jackson | Sweden |

### DISTINCT 语句

`SELECT DISTINCT` 语句通常用于仅返回唯一值。有时，某一列包含重复值，而你只想列出唯一的值。在这种情况下，你可以选择 `SELECT DISTINCT` 语句。当我们使用简单的 `SELECT` 语句显示表时，它会显示列中的所有值，而不区分重复条。`DISTINCT` 语句仅显示列中的唯一值。演示表如下。

```sql
SELECT DISTINCT Country FROM Members;
```

| Country |
| --- |
| United States |
| United Kingdom |
| Ireland |
| Germany |
| France |
| Italy |
| Sweden |

United States 重复了，但这里只显示了一个条目。

### WHERE 子

这个特定的语句从你提到的特定位置选择成员。在对数据库应用 `SQL` 语句之前，让我们复习数据库中的表。

| CustomerID | CustomerName | ContactNumber | SecretCode | Country |
| --- | --- | --- | --- | --- |
| 1 | Emily Jack | 55779034 | 45 | United States |
| 2 | Jason Austin | 34568988 | 2 | United Kingdom |
| 3 | Amanda McMahon | 34578899 | 1 | Ireland |
| 4 | Victoria Ann | 23768800 | 67 | Germany |
| 5 | Simon Wiz | 45327899 | 9 | United States |
| 6 | Tracy Drupal | 23897609 | 8 | France |
| 7 | Emilia Tim | 45890093 | 3 | Italy |
| 8 | Tyson Jackson | 34980900 | 2 | Sweden |
| 9 | Tom Dick | 45980999 | 4 | United States |
| 10 | Dane harry | 47889933 | 0 | United States |

这是数据库中的表。

```sql
SELECT * FROM Members WHERE Country='United States';
```

| CustomerID | CustomerName | ContactNumber | SecretCode | Country |
| --- | --- | --- | --- | --- |
| 1 | Emily Jack | 55779034 | 45 | United States |
| 5 | Simon Wiz | 45327899 | 9 | United States |
| 9 | Tom Dick | 45980999 | 4 | United States |
| 10 | Dane harry | 47889933 | 0 | United States |

看另一个 `WHERE` 语句的示例。

```sql
SELECT * FROM Members WHERE CustomerID=1; WHERE CustomerID=2; WHERE CustomerID=3; WHERE CustomerID=4; WHERE CustomerID=5; WHERE CustomerID=6; WHERE CustomerID=7;
```

| CustomerID | CustomerName | ContactNumber | SecretCode | Country |
| --- | --- | --- | --- | --- |
| 1 | Emily Jack | 55779034 | 45 | United States |
| 2 | Jason Austin | 34568988 | 2 | United Kingdom |
| 3 | Amanda McMahon | 34578899 | 1 | Ireland |
| 4 | Victoria Ann | 23768800 | 67 | Germany |
| 5 | Simon Wiz | 45327899 | 9 | United States |
| 6 | Tracy Drupal | 23897609 | 8 | France |
| 7 | Emilia Tim | 45890093 | 3 | Italy |





### AND 语句

以下语句将选择 `Members` 表中国家为美国或 `SecretCode` 为 7 的所有字段。在执行语句之前，我会对数据库表进行一些更改并将其显示。

| CustomerID | CustomerName | ContactNumber | SecretCode | Country |
| :--- | :--- | :--- | :--- | :--- |
| 1. | Emily Jack | 55779034 | 45 | United States |
| 2. | Jason Austin | 34568988 | 7 | United Kingdom |
| 3. | Amanda McMahon | 34578899 | 7 | Ireland |
| 4. | Victoria Ann | 23768800 | 67 | Germany |
| 5. | Simon Wiz | 45327899 | 7 | United States |
| 6. | Tracy Drupal | 23897609 | 7 | France |
| 7. | Emilia Tim | 45890093 | 3 | Italy |
| 8. | Tyson Jackson | 34980900 | 7 | Sweden |
| 9. | Tom Dick | 45980999 | 4 | United States |
| 10. | Dane harry | 47889933 | 0 | United States |

以下是该语句：
```
SELECT * FROM Members WHERE Members= ‘United States’ AND SecretCode=7;
```

| CustomerID | CustomerName | ContactNumber | SecretCode | Country |
| :--- | :--- | :--- | :--- | :--- |
| 1. | Emily Jack | 55779034 | 45 | United States |
| 2. | Jason Austin | 34568988 | 7 | United Kingdom |
| 3. | Amanda McMahon | 34578899 | 7 | Ireland |
| 5. | Simon Wiz | 45327899 | 7 | United States |
| 6. | Tracy Drupal | 23897609 | 7 | France |
| 8. | Tyson Jackson | 34980900 | 7 | Sweden |
| 9. | Tom Dick | 45980999 | 4 | United States |
| 10. | Dane harry | 47889933 | 0 | United States |

还有另一个神奇的语句被称为 `OR` 语句。它允许你在从数据库中检索数据时进行选择。
```
SELECT * FROM Members WHERE Country= ‘United States’ OR SecretCode= 7;
```

| CustomerID | CustomerName | ContactNumber | SecretCode | Country |
| :--- | :--- | :--- | :--- | :--- |
| 1. | Emily Jack | 55779034 | 45 | United States |
| 2. | Jason Austin | 34568988 | 7 | United Kingdom |
| 3. | Amanda McMahon | 34578899 | 7 | Ireland |
| 5. | Simon Wiz | 45327899 | 7 | United States |
| 6. | Tracy Drupal | 23897609 | 7 | France |
| 8. | Tyson Jackson | 34980900 | 7 | Sweden |
| 9. | Tom Dick | 45980999 | 4 | United States |
| 10. | Dane harry | 47889933 | 0 | United States |

再看另一个例子：
```
SELECT * FROM Members WHERE Members= ‘United States’ OR CustomerID = 2;
```

| CustomerID | CustomerName | ContactNumber | SecretCode | Country |
| :--- | :--- | :--- | :--- | :--- |
| 1. | Emily Jack | 55779034 | 45 | United States |
| 2. | Jason Austin | 34568988 | 7 | United Kingdom |
| 5. | Simon Wiz | 45327899 | 7 | United States |
| 9. | Tom Dick | 45980999 | 4 | United States |
| 10. | Dane harry | 47889933 | 0 | United States |

如果你想留下一个条目并检索所有其他条目，可以在脚本中使用 `NOT` 语句。
```
SELECT * FROM Members WHERE NOT Country= ‘Sweden’;
```

| CustomerID | CustomerName | ContactNumber | SecretCode | Country |
| :--- | :--- | :--- | :--- | :--- |
| 1. | Emily Jack | 55779034 | 45 | United States |
| 2. | Jason Austin | 34568988 | 7 | United Kingdom |
| 3. | Amanda McMahon | 34578899 | 7 | Ireland |
| 4. | Victoria Ann | 23768800 | 67 | Germany |
| 5. | Simon Wiz | 45327899 | 7 | United States |
| 6. | Tracy Drupal | 23897609 | 7 | France |
| 7. | Emilia Tim | 45890093 | 3 | Italy |
| 9. | Tom Dick | 45980999 | 4 | United States |
| 10. | Dane harry | 47889933 | 0 | United States |

## 结合 `AND`, `OR` 和 `NOT`

你可以组合这三个语句使工作更加精确。以下语句将选择 `Members` 表中国家为美国且名为 `Emilia` 的不同字段。表如下：

| CustomerID | CustomerName | ContactNumber | SecretCode | Country |
| :--- | :--- | :--- | :--- | :--- |
| 1. | Emilia Jackson | 55779034 | 45 | United States |
| 2. | Jason Austin | 34568988 | 7 | United Kingdom |
| 3. | Amanda McMahon | 34578899 | 7 | Ireland |
| 4. | Victoria Ann | 23768800 | 67 | Germany |
| 5. | Harry Styles | 45327899 | 7 | United States |
| 6. | Tracy Drupal | 23897609 | 7 | France |
| 7. | Emilia Tim | 45890093 | 3 | Italy |
| 8. | Tyson Jackson | 34980900 | 7 | Sweden |
| 9. | Emilia Jackson | 45980999 | 4 | United States |
| 10. | Harry Styles | 47889933 | 0 | United States |

让我们写这个 SQL 语句：
```
SELECT * FROM Members WHERE Members= ‘United States’ AND (CustomerName=‘Emilia Jackson’ OR CustomerName=‘Harry Styles’);
```

| CustomerID | CustomerName | ContactNumber | SecretCode | Country |
| :--- | :--- | :--- | :--- | :--- |
| 1. | Emilia Jackson | 55779034 | 45 | United States |
| 5. | Harry Styles | 45327899 | 7 | United States |
| 9. | Emilia Jackson | 45980999 | 4 | United States |
| 10. | Harry Styles | 47889933 | 0 | United States |

## `AND NOT` 语句

你可以使用 `AND NOT` 语句从表中排除两个条目，然后在屏幕上显示或打印它们。整个表如下：

| CustomerID | CustomerName | ContactNumber | SecretCode | Country |
| :--- | :--- | :--- | :--- | :--- |
| 1. | Emilia Jackson | 55779034 | 45 | United States |
| 2. | Jason Austin | 34568988 | 7 | United Kingdom |
| 3. | Amanda McMahon | 34578899 | 7 | Ireland |
| 4. | Victoria Ann | 23768800 | 67 | Germany |
| 5. | Harry Styles | 45327899 | 7 | United States |
| 6. | Tracy Drupal | 23897609 | 7 | France |
| 7. | Emilia Tim | 45890093 | 3 | Italy |
| 8. | Tyson Jackson | 34980900 | 7 | Sweden |
| 9. | Emilia Jackson | 45980999 | 4 | United States |
| 10. | Harry Styles | 47889933 | 0 | United States |

```
SELECT * FROM Members WHERE NOT Country= ‘Sweden’ AND NOT Country= ‘United Kingdom’
```

| CustomerID | CustomerName | ContactNumber | SecretCode | Country |
| :--- | :--- | :--- | :--- | :--- |
| 1. | Emilia Jackson | 55779034 | 45 | United States |
| 3. | Amanda McMahon | 34578899 | 7 | Ireland |
| 4. | Victoria Ann | 23768800 | 67 | Germany |
| 5. | Harry Styles | 45327899 | 7 | United States |
| 6. | Tracy Drupal | 23897609 | 7 | France |
| 7. | Emilia Tim | 45890093 | 3 | Italy |
| 9. | Emilia Jackson | 45980999 | 4 | United States |
| 10. | Harry Styles | 47889933 | 0 | United States |

## `ORDER BY` 关键字

你可以使用 `ORDER BY` 关键字按升序或降序排序结果。`ORDER BY` 关键字默认按升序排序记录。要按降序排序，你可以使用 `DESC` 关键字。这里是当前形式的表：

| CustomerID | CustomerName | ContactNumber | SecretCode | Country |
| :--- | :--- | :--- | :--- | :--- |
| 1. | Emilia Jackson | 55779034 | 45 | United States |
| 2. | Jason Austin | 34568988 | 7 | United Kingdom |
| 3. | Amanda McMahon | 34578899 | 7 | Ireland |
| 4. | Victoria Ann | 23768800 | 67 | Germany |
| 5. | Harry Styles | 45327899 | 7 | United States |
| 6. | Tracy Drupal | 23897609 | 7 | France |
| 7. | Emilia Tim | 45890093 | 3 | Italy |
| 8. | Tyson Jackson | 34980900 | 7 | Sweden |
| 9. | Emilia Jackson | 45980999 | 4 | United States |
| 10. | Harry Styles | 47889933 | 0 | United States |




这是你必须输入的语句。

```sql
SELECT * FROM Members ORDER BY Members;
```

| CustomerID | CustomerName | ContactNumber | SecretCode | Country |
| :--- | :--- | :--- | :--- | :--- |
| 6. | Tracy Drupal | 23897609 | 7 | France |
| 4. | Victoria Ann | 23768800 | 67 | Germany |
| 3. | Amanda McMahon | 34578899 | 7 | Ireland |
| 7. | Emilia Tim | 45890093 | 3 | Italy |
| 8. | Tyson Jackson | 34980900 | 7 | Sweden |
| 2. | Jason Austin | 34568988 | 7 | United Kingdom |
| 1. | Emilia Jackson | 55779034 | 45 | United States |
| 5. | Harry Styles | 45327899 | 7 | United States |
| 9. | Emilia Jackson | 45980999 | 4 | United States |
| 10. | Harry Styles | 47889933 | 0 | United States |

这是完全升序排列的结果。不过，你可以通过在 SQL 语句中使用 `DESC` 关键字来反转顺序。它将选取所有条目并根据 `Country` 列将其重乱为降序排列。这是表格当前的形式。

| CustomerID | CustomerName | ContactNumber | SecretCode | Country |
| :--- | :--- | :--- | :--- | :--- |
| 1. | Emilia Jackson | 55779034 | 45 | United States |
| 2. | Jason Austin | 34568988 | 7 | United Kingdom |
| 3. | Amanda McMahon | 34578899 | 7 | Ireland |
| 4. | Victoria Ann | 23768800 | 67 | Germany |
| 5. | Harry Styles | 45327899 | 7 | United States |
| 6. | Tracy Drupal | 23897609 | 7 | France |
| 7. | Emilia Tim | 45890093 | 3 | Italy |
| 8. | Tyson Jackson | 34980900 | 7 | Sweden |
| 9. | Emilia Jackson | 45980999 | 4 | United States |
| 10. | Harry Styles | 47889933 | 0 | United States |

```sql
SELECT * FROM Members ORDER BY Members DESC;
```

| CustomerID | CustomerName | ContactNumber | SecretCode | Country |
| :--- | :--- | :--- | :--- | :--- |
| 1. | Emilia Jackson | 55779034 | 45 | United States |
| 9. | Emilia Jackson | 45980999 | 4 | United States |
| 10. | Harry Styles | 47889933 | 0 | United States |
| 5. | Harry Styles | 45327899 | 7 | United States |
| 2. | Jason Austin | 34568988 | 7 | United Kingdom |
| 8. | Tyson Jackson | 34980900 | 7 | Sweden |
| 3. | Amanda McMahon | 34578899 | 7 | Ireland |
| 7. | Emilia Tim | 45890093 | 3 | Italy |
| 4. | Victoria Ann | 23768800 | 67 | Germany |
| 6. | Tracy Drupal | 23897609 | 7 | France |

你也可以在升序和降序中设置两个不同的列，或者将两个都设置为升序。

```sql
SELECT * FROM Members ORDER BY CustomerName, Country;
```

### 插入语句 (Insert Into Statements)
通过此语句，你可以随地更新数据库。我们在数据库中有一个表格，我们将对其进行相应的更新。让我们来看看表格。

| CustomerID | CustomerName | ContactNumber | SecretCode | Country |
| :--- | :--- | :--- | :--- | :--- |
| 1. | Emilia Jackson | 55779034 | 45 | United States |
| 2. | Jason Austin | 34568988 | 7 | United Kingdom |
| 3. | Amanda McMahon | 34578899 | 7 | Ireland |
| 4. | Victoria Ann | 23768800 | 67 | Germany |
| 5. | Harry Styles | 45327899 | 7 | United States |
| 6. | Tracy Drupal | 23897609 | 7 | France |
| 7. | Emilia Tim | 45890093 | 3 | Italy |
| 8. | Tyson Jackson | 34980900 | 7 | Sweden |
| 9. | Emilia Jackson | 45980999 | 4 | United States |
| 10. | Harry Styles | 47889933 | 0 | United States |

```sql
INSERT INTO Members (CustomerName, SecretCode) VALUES ('Haddy','45');
```

| CustomerID | CustomerName | ContactNumber | SecretCode | Country |
| :--- | :--- | :--- | :--- | :--- |
| 1. | Emilia Jackson | 55779034 | 45 | United States |
| 2. | Jason Austin | 34568988 | 7 | United Kingdom |
| 3. | Amanda McMahon | 34578899 | 7 | Ireland |
| 4. | Victoria Ann | 23768800 | 67 | Germany |
| 5. | Harry Styles | 45327899 | 7 | United States |
| 6. | Tracy Drupal | 23897609 | 7 | France |
| 7. | Emilia Tim | 45890093 | 3 | Italy |
| 8. | Tyson Jackson | 34980900 | 7 | Sweden |
| 9. | Emilia Jackson | 45980999 | 4 | United States |
| 10. | Harry Styles | 47889933 | 0 | United States |

```sql
INSERT INTO Members (CustomerName, SecretCode) VALUES ('Sylvia','9');
```

| CustomerID | CustomerName | ContactNumber | SecretCode | Country |
| :--- | :--- | :--- | :--- | :--- |
| 1. | Emilia Jackson | 55779034 | 45 | United States |
| 2. | Jason Austin | 34568988 | 7 | United Kingdom |
| 3. | Amanda McMahon | 34578899 | 7 | Ireland |
| 4. | Victoria Ann | 23768800 | 67 | Germany |
| 5. | Harry Styles | 45327899 | 7 | United States |
| 6. | Tracy Drupal | 23897609 | 7 | France |
| 7. | Emilia Tim | 45890093 | 3 | Italy |
| 8. | Tyson Jackson | 34980900 | 7 | Sweden |
| 9. | Emilia Jackson | 45980999 | 4 | United States |
| 10. | Harry Styles | 47889933 | 0 | United States |

你可以选择性地向表格的特定列添加数据。

```sql
INSERT INTO Members (CustomerName, SecretCode) VALUES ('Tane','5');
```




| CustomerID | CustomerName | ContactNumber | SecretCode | Country |
| :--- | :--- | :--- | :--- | :--- |
| 3 | Amanda McMahon | 34578899 | 7 | 爱尔兰 |
| 4 | Victoria Ann | 23768800 | 67 | 德国 |
| 5 | Harry Styles | 45327899 | 7 | 美国 |
| 6 | Tracy Drupal | 23897609 | 7 | 法国 |
| 7 | Emilia Tim | 45890093 | 3 | 意大利 |
| 8 | Tyson Jackson | 34980900 | 7 | 瑞典 |
| 9 | Emilia Jackson | 45980999 | 4 | 美国 |
| 10 | Harry Styles | 47889933 | 0 | 美国 |
| 11 | Haddy | 45789809 | 7 | 美国 |
| 12 | Sylvia | 15769091 | 9 | 美国 |

这是另一个例子，我更改了列。

```sql
UPDATE Members SET CustomerName = ‘Milton’, Country = ‘Bolivia’ WHERE CustomerID = 5;
```

| CustomerID | CustomerName | ContactNumber | SecretCode | Country |
| :--- | :--- | :--- | :--- | :--- |
| 1 | Fanny | 55779034 | 007 | 美国 |
| 2 | Jason Austin | 34568988 | 7 | 英国 |
| 3 | Amanda McMahon | 34578899 | 7 | 爱尔兰 |
| 4 | Victoria Ann | 23768800 | 67 | 德国 |
| 5 | Milton | 45327899 | 7 | 波利维亚 |
| 6 | Tracy Drupal | 23897609 | 7 | 法国 |
| 7 | Emilia Tim | 45890093 | 3 | 意大利 |
| 8 | Tyson Jackson | 34980900 | 7 | 瑞典 |
| 9 | Emilia Jackson | 45980999 | 4 | 美国 |
| 10 | Harry Styles | 47889933 | 0 | 美国 |
| 11 | Haddy | 45789809 | 7 | 美国 |
| 12 | Sylvia | 15769091 | 9 | 美国 |

`WHERE` 语句非常神奇。它允许你同时更改多条记录。例如，你可以用它来更新不同的集合。看下面的示例。

```sql
UPDATE Members SET CustomerName= ‘Marlow’ WHERE SecretCode= ‘7’
```

| CustomerID | CustomerName | ContactNumber | SecretCode | Country |
| :--- | :--- | :--- | :--- | :--- |
| 1 | Fanny | 55779034 | 007 | 美国 |
| 2 | Marlow | 34568988 | 7 | 英国 |
| 3 | Marlow | 34578899 | 7 | 爱尔兰 |
| 4 | Victoria Ann | 23768800 | 67 | 德国 |
| 5 | Marlow | 45327899 | 7 | 美国 |
| 6 | Marlow | 23897609 | 7 | 法国 |
| 7 | Emilia Tim | 45890093 | 3 | 意大利 |
| 8 | Marlow | 34980900 | 7 | 瑞典 |
| 9 | Emilia Jackson | 45980999 | 4 | 美国 |
| 10 | Harry Styles | 47889933 | 0 | 美国 |
| 11 | Marlow | 45789809 | 7 | 美国 |
| 12 | Sylvia | 15769091 | 9 | 美国 |

你可以通过使用 `country` 列来进行此更改。

```sql
UPDATE Members SET CustomerName= ‘Dom Carry’ WHERE Country= ‘United States’;
```

| CustomerID | CustomerName | ContactNumber | SecretCode | Country |
| :--- | :--- | :--- | :--- | :--- |
| 1 | Dom Carry | 55779034 | 007 | 美国 |
| 2 | Marlow | 34568988 | 7 | 英国 |
| 3 | Marlow | 34578899 | 7 | 爱尔兰 |
| 4 | Victoria Ann | 23768800 | 67 | 德国 |
| 5 | Dom Carry | 45327899 | 7 | 美国 |
| 6 | Marlow | 23897609 | 7 | 法国 |
| 7 | Emilia Tim | 45890093 | 3 | 意大利 |
| 8 | Marlow | 34980900 | 7 | 瑞典 |
| 9 | Emilia Jackson | 45980999 | 4 | 美国 |
| 10 | Harry Styles | 47889933 | 0 | 美国 |
| 11 | Dom Carry | 45789809 | 7 | 美国 |
| 12 | Dom Carry | 15769091 | 9 | 美国 |

在使用 `WHERE` 子句时应该格外小心，因为如果你漏掉了它，你将更新数据库中的所有记录。这将会是一场灾难。看看你是如何破坏数据库的。如下：

| CustomerID | CustomerName | ContactNumber | SecretCode | Country |
| :--- | :--- | :--- | :--- | :--- |
| 1 | Fanny | 55779034 | 007 | 美国 |
| 2 | Marlow | 34568988 | 7 | 英国 |
| 3 | Marlow | 34578899 | 7 | 爱尔兰 |
| 4 | Victoria Ann | 23768800 | 67 | 德国 |
| 5 | Marlow | 45327899 | 7 | 美国 |
| 6 | Marlow | 23897609 | 7 | 法国 |
| 7 | Emilia Tim | 45890093 | 3 | 意大利 |
| 8 | Marlow | 34980900 | 7 | 瑞典 |
| 9 | Emilia Jackson | 45980999 | 4 | 美国 |
| 10 | Harry Styles | 47889933 | 0 | 美国 |
| 11 | Marlow | 45789809 | 7 | 美国 |
| 12 | Sylvia | 15769091 | 9 | 美国 |

```sql
UPDATE Members SET CustomerName= ‘Dom Carry’
```

| CustomerID | CustomerName | ContactNumber | SecretCode | Country |
| :--- | :--- | :--- | :--- | :--- |
| 1 | Dom Carry | 55779034 | 007 | 美国 |
| 2 | Dom Carry | 34568988 | 7 | 英国 |
| 3 | Dom Carry | 34578899 | 7 | 爱尔兰 |
| 4 | Dom Carry | 23768800 | 67 | 德国 |
| 5 | Dom Carry | 45327899 | 7 | 美国 |
| 6 | Dom Carry | 23897609 | 7 | 法国 |
| 7 | Dom Carry | 45890093 | 3 | 意大利 |
| 8 | Dom Carry | 34980900 | 7 | 瑞典 |
| 9 | Dom Carry | 45980999 | 4 | 美国 |
| 10 | Dom Carry | 47889933 | 0 | 美国 |
| 11 | Dom Carry | 45789809 | 7 | 美国 |
| 12 | Dom Carry | 15769091 | 9 | 美国 |

就像处理任何文档一样，你可以从数据库中删除记录。我将使用的数据库如下：

| CustomerID | CustomerName | ContactNumber | SecretCode | Country |
| :--- | :--- | :--- | :--- | :--- |
| 1 | Fanny | 55779034 | 007 | 美国 |
| 2 | Marlow | 34568988 | 7 | 英国 |
| 3 | Marlow | 34578899 | 7 | 爱尔兰 |
| 4 | Victoria Ann | 23768800 | 67 | 德国 |
| 5 | Marlow | 45327899 | 7 | 美国 |
| 6 | Marlow | 23897609 | 7 | 法国 |
| 7 | Emilia Tim | 45890093 | 3 | 意大利 |
| 8 | Marlow | 34980900 | 7 | 瑞典 |
| 9 | Emilia Jackson | 45980999 | 4 | 美国 |
| 10 | Harry Styles | 47889933 | 0 | 美国 |
| 11 | Marlow | 45789809 | 7 | 美国 |
| 12 | Sylvia | 15769091 | 9 | 美国 |

从表中删除特定条目的语句如下：

```sql
DELETE FROM Members WHERE CustomerName = ‘Sylvia’;
```

再尝试另一条记录。

```sql
DELETE FROM Members WHERE Country = ‘United Kingdom.’
```

| CustomerID | CustomerName | ContactNumber | SecretCode | Country |
| :--- | :--- | :--- | :--- | :--- |
| 1 | Fanny | 55779034 | 007 | 美国 |
| 3 | Marlow | 34578899 | 7 | 爱尔兰 |
| 4 | Victoria Ann | 23768800 | 67 | 德国 |
| 5 | Marlow | 45327899 | 7 | 美国 |
| 6 | Marlow | 23897609 | 7 | 法国 |
| 7 | Emilia Tim | 45890093 | 3 | 意大利 |
| 8 | Marlow | 34980900 | 7 | 瑞典 |
| 9 | Emilia Jackson | 45980999 | 4 | 美国 |





| CustomerID | CustomerName | ContactNumber | SecretCode | Country |
| :--- | :--- | :--- | :--- | :--- |
| 10. | Harry Styles | 47889933 | 0 | 美国本土 |
| 11. | Marlow | 45789809 | 7 | 美国本土 |
| 12 | Sylvia | 15769091 | 9 | 美国本土 |

### SELECT TOP 语句

`SELECT TOP` 语句用于检索你需要返回的顶部记录，并隐藏表的其余部分。你可以对具有数千条记录的大型表使用它。这非常有用，因为如果你返回大量的记录，将影响你的性能。

| CustomerID | CustomerName | ContactNumber | SecretCode | Country |
| :--- | :--- | :--- | :--- | :--- |
| 1. | Fanny | 55779034 | 007 | 美国本土 |
| 2. | Marlow | 34568988 | 7 | 英国 |
| 3. | Marlow | 34578899 | 7 | 爱尔兰 |
| 4. | Victoria Ann | 23768800 | 67 | 德国 |
| 5. | Marlow | 45327899 | 7 | 美国本土 |
| 6. | Marlow | 23897609 | 7 | 法国 |
| 7. | Emilia Tim | 45890093 | 3 | 意大利 |
| 8. | Marlow | 34980900 | 7 | 瑞典 |
| 9. | Emilia Jackson | 45980999 | 4 | 美国本土 |
| 10. | Harry Styles | 47889933 | 0 | 美国本土 |
| 11. | Marlow | 45789809 | 7 | 美国本土 |
| 12 | Sylvia | 15769091 | 9 | 美国本土 |

```sql
SELECT TOP 6 * FROM Members;
```

| CustomerID | CustomerName | ContactNumber | SecretCode | Country |
| :--- | :--- | :--- | :--- | :--- |
| 1. | Fanny | 55779034 | 007 | 美国本土 |
| 2. | Marlow | 34568988 | 7 | 英国 |
| 3. | Marlow | 34578899 | 7 | 爱尔兰 |
| 4. | Victoria Ann | 23768800 | 67 | 德国 |
| 5. | Marlow | 45327899 | 7 | 美国本土 |
| 6. | Marlow | 23897609 | 7 | 法国 |

你也可以使用 `LIMIT` 子句来指定你想查看的记录数量。请以下示例。

```sql
SELECT * FROM Members LIMIT 8;
```

| CustomerID | CustomerName | ContactNumber | SecretCode | Country |
| :--- | :--- | :--- | :--- | :--- |
| 1. | Fanny | 55779034 | 007 | 美国本土 |
| 2. | Marlow | 34568988 | 7 | 英国 |
| 3. | Marlow | 34578899 | 7 | 爱尔兰 |
| 4. | Victoria Ann | 23768800 | 67 | 德国 |
| 5. | Marlow | 45327899 | 7 | 美国本土 |
| 6. | Marlow | 23897609 | 7 | 法国 |
| 7. | Emilia Tim | 45890093 | 3 | 意大利 |
| 8. | Marlow | 34980900 | 7 | 瑞典 |
| 9. | Emilia Jackson | 45980999 | 4 | 美国本土 |
| 10. | Harry Styles | 47889933 | 0 | 美国本土 |
| 11. | Marlow | 45789809 | 7 | 美国本土 |
| 12 | Sylvia | 15769091 | 9 | 美国本土 |

### PERCENT 语句

`PERCENT` 语句可以用于指定你想要查看的百分比记录。这里有一个有趣的 `PERCENT` 语句。

| CustomerID | CustomerName | ContactNumber | SecretCode | Country |
| :--- | :--- | :--- | :--- | :--- |
| 1. | Fanny | 55779034 | 007 | 美国本土 |
| 2. | Marlow | 34568988 | 7 | 英国 |
| 3. | Marlow | 34578899 | 7 | 爱尔兰 |
| 4. | Victoria Ann | 23768800 | 67 | 德国 |
| 5. | Marlow | 45327899 | 7 | 美国本土 |
| 6. | Marlow | 23897609 | 7 | 法国 |
| 7. | Emilia Tim | 45890093 | 3 | 意大利 |
| 8. | Marlow | 34980900 | 7 | 瑞典 |
| 9. | Emilia Jackson | 45980999 | 4 | 美国本土 |
| 10. | Harry Styles | 47889933 | 0 | 美国本土 |
| 11. | Marlow | 45789809 | 7 | 美国本土 |
| 12 | Sylvia | 15769091 | 9 | 美国本土 |

这里是 `TOP PERCENT` 语句。

```sql
SELECT TOP 50 PERCENT FROM Members;
```

| CustomerID | CustomerName | ContactNumber | SecretCode | Country |
| :--- | :--- | :--- | :--- | :--- |
| 1. | Fanny | 55779034 | 007 | 美国本土 |
| 2. | Marlow | 34568988 | 7 | 英国 |
| 3. | Marlow | 34578899 | 7 | 爱尔兰 |
| 4. | Victoria Ann | 23768800 | 67 | 德国 |
| 5. | Marlow | 45327899 | 7 | 美国本土 |
| 6. | Marlow | 23897609 | 7 | 法国 |
| 7. | Emilia Tim | 45890093 | 3 | 意大利 |
| 8. | Marlow | 34980900 | 7 | 瑞典 |
| 9. | Emilia Jackson | 45980999 | 4 | 美国本土 |
| 10. | Harry Styles | 47889933 | 0 | 美国本土 |
| 11. | Marlow | 45789809 | 7 | 美国本土 |
| 12 | Sylvia | 15769091 | 9 | 美国本土 |

## 通配符用法

现在我表格上应用 `%` 通配符。

```sql
SELECT * FROM Members WHERE Country LIKE '%es%';
```

在接下来的示例中，我将尝试检索以 'om' 结尾的记录。查看示例表。

```sql
SELECT * FROM Members WHERE Country LIKE '%om%';
```





## 字符列表通配符

在以下语句中，你可以列出特定国家的第一个字母来显示记录。以下是操作方法。

| CustomerID | CustomerName | ContactNumber | SecretCode | Country |
| :--- | :--- | :--- | :--- | :--- |
| 1. | Fanny | 55779034 | 007 | United States |
| 2. | Marlow | 34568988 | 7 | United Kingdom |
| 3. | Marlow | 34578899 | 7 | Ireland |
| 4. | Victoria Ann | 23768800 | 67 | Germany |
| 5. | Marlow | 45327899 | 7 | United States |
| 6. | Marlow | 23897609 | 7 | France |
| 7. | Emilia Tim | 45890093 | 3 | Italy |
| 8. | Marlow | 34980900 | 7 | Sweden |
| 9. | Emilia Jackson | 45980999 | 4 | United States |
| 10. | Harry Styles | 47889933 | 0 | United States |
| 11. | Marlow | 45789809 | 7 | United States |
| 12 | Sylvia | 15769091 | 9 | United States |

现在让我们来编写语句。

```sql
SELECT * FROM Members WHERE Country LIKE '[isu]%';
```

| CustomerID | CustomerName | ContactNumber | SecretCode | Country |
| :--- | :--- | :--- | :--- | :--- |
| 1. | Fanny | 55779034 | 007 | United States |
| 2. | Marlow | 34568988 | 7 | United Kingdom |
| 3. | Marlow | 34578899 | 7 | Ireland |
| 5. | Marlow | 45327899 | 7 | United States |
| 7. | Emilia Tim | 45890093 | 3 | Italy |
| 8. | Marlow | 34980900 | 7 | Sweden |
| 9. | Emilia Jackson | 45980999 | 4 | United States |
| 10. | Harry Styles | 47889933 | 0 | United States |
| 11. | Marlow | 45789809 | 7 | United States |
| 12 | Sylvia | 15769091 | 9 | United States |

让我们将表格恢复到原始状态，然后尝试只显示以 ‘u’ 开头的国家。以下是该表格。

| CustomerID | CustomerName | ContactNumber | SecretCode | Country |
| :--- | :--- | :--- | :--- | :--- |
| 1. | Fanny | 55779034 | 007 | United States |
| 2. | Marlow | 34568988 | 7 | United Kingdom |
| 3. | Marlow | 34578899 | 7 | Ireland |
| 4. | Victoria Ann | 23768800 | 67 | Germany |
| 5. | Marlow | 45327899 | 7 | United States |
| 6. | Marlow | 23897609 | 7 | France |
| 7. | Emilia Tim | 45890093 | 3 | Italy |
| 8. | Marlow | 34980900 | 7 | Sweden |
| 9. | Emilia Jackson | 45980999 | 4 | United States |
| 10. | Harry Styles | 47889933 | 0 | United States |
| 11. | Marlow | 45789809 | 7 | United States |
| 12 | Sylvia | 15769091 | 9 | United States |

```sql
SELECT * FROM Members WHERE Country LIKE '[u]%';
```

| CustomerID | CustomerName | ContactNumber | SecretCode | Country |
| :--- | :--- | :--- | :--- | :--- |
| 1. | Fanny | 55779034 | 007 | United States |
| 2. | Marlow | 34568988 | 7 | United Kingdom |
| 5. | Marlow | 45327899 | 7 | United States |
| 9. | Emilia Jackson | 45980999 | 4 | United States |
| 10. | Harry Styles | 47889933 | 0 | United States |
| 11. | Marlow | 45789809 | 7 | United States |
| 12 | Sylvia | 15769091 | 9 | United States |

`IN` 运算符会让你的工作变得简单得多。它会选择所有住在特定国家的客户。你只需要输入国家名称即可显示相同的记录。

| CustomerID | CustomerName | ContactNumber | SecretCode | Country |
| :--- | :--- | :--- | :--- | :--- |
| 1. | Fanny | 55779034 | 007 | United States |
| 2. | Marlow | 34568988 | 7 | United Kingdom |
| 3. | Marlow | 34578899 | 7 | Ireland |
| 4. | Victoria Ann | 23768800 | 67 | Germany |
| 5. | Marlow | 45327899 | 7 | United States |
| 6. | Marlow | 23897609 | 7 | France |
| 7. | Emilia Tim | 45890093 | 3 | Italy |
| 8. | Marlow | 34980900 | 7 | Sweden |
| 9. | Emilia Jackson | 45980999 | 4 | United States |
| 10. | Harry Styles | 47889933 | 0 | United States |
| 11. | Marlow | 45789809 | 7 | United States |
| 12 | Sylvia | 15769091 | 9 | United States |

```sql
SELECT * FROM Members WHERE Country IN ('United States', 'United Kingdom', 'Italy');
```

| CustomerID | CustomerName | ContactNumber | SecretCode | Country |
| :--- | :--- | :--- | :--- | :--- |
| 1. | Fanny | 55779034 | 007 | United States |
| 2. | Marlow | 34568988 | 7 | United Kingdom |
| 5. | Marlow | 45327899 | 7 | United States |
| 7. | Emilia Tim | 45890093 | 3 | Italy |
| 9. | Emilia Jackson | 45980999 | 4 | United States |
| 10. | Harry Styles | 47889933 | 0 | United States |
| 11. | Marlow | 45789809 | 7 | United States |
| 12 | Sylvia | 15769091 | 9 | United States |

还有另一个 SQL 语句可以帮助你过滤特定国家的记录。以下语句将过滤掉所有不在德国、瑞典和法国的客户。查看当前的表格。

| CustomerID | CustomerName | ContactNumber | SecretCode | Country |
| :--- | :--- | :--- | :--- | :--- |
| 1. | Fanny | 55779034 | 007 | United States |
| 2. | Marlow | 34568988 | 7 | United Kingdom |
| 3. | Marlow | 34578899 | 7 | Ireland |
| 4. | Victoria Ann | 23768800 | 67 | Germany |
| 5. | Marlow | 45327899 | 7 | United States |
| 6. | Marlow | 23897609 | 7 | France |
| 7. | Emilia Tim | 45890093 | 3 | Italy |
| 8. | Marlow | 34980900 | 7 | Sweden |
| 9. | Emilia Jackson | 45980999 | 4 | United States |
| 10. | Harry Styles | 47889933 | 0 | United States |
| 11. | Marlow | 45789809 | 7 | United States |
| 12 | Sylvia | 15769091 | 9 | United States |

```sql
SELECT * FROM Members WHERE Country NOT IN ('Germany', 'Sweden', 'France');
```

在数据量巨大且始终存在数据丢失风险的大型组织中，你必须创建多个副本存储在数据库中。手动操作，在数据库中手动填写每条记录以创建一个完美的副本将花费大量时间。此外，某些情况下数据是特定用户的，这意味着你无法轻松地检索它。MySQL 允许你创建任意数量的数据副本。请查看以下示例。

| CustomerID | CustomerName | ContactNumber | SecretCode | Country |
| :--- | :--- | :--- | :--- | :--- |
| 1. | Fanny | 55779034 | 007 | United States |
| 2. | Marlow | 34568988 | 7 | United Kingdom |
| 3. | Marlow | 34578899 | 7 | Ireland |
| 4. | Victoria Ann | 23768800 | 67 | Germany |
| 5. | Marlow | 45327899 | 7 | United States |
| 6. | Marlow | 23897609 | 7 | France |
| 7. | Emilia Tim | 45890093 | 3 | Italy |
| 8. | Marlow | 34980900 | 7 | Sweden |
| 9. | Emilia Jackson | 45980999 | 4 | United States |

| 10. | Harry Styles | 47889933 | 0 | United States |

```sql
SELECT INTO
```





| 10. | Harry Styles | 47889933 | 0 | 美国 | |
| 11. | Marlow | 45789809 | 7 | 美国 | |
| 12 | Sylvia | 15769091 | 9 | 美国 | |

以下是语句：
```sql
SELECT * INTO MembersBackup2020 FROM Members;
```

| 客户 ID | 客户名称 | 联系电话 | 密钥代码 | 国家 |
| :--- | :--- | :--- | :--- | :--- |
| 1. | Fanny | 55779034 | 007 | 美国 | |
| 2. | Marlow | 34568988 | 7 | 英国 |
| 3. | Marlow | 34578899 | 7 | 爱尔兰 |
| 4. | Victoria Ann | 23768800 | 66 | 德国 |
| 5. | Marlow | 45327899 | 7 | 美国 | |
| 6. | Marlow | 23897609 | 7 | 法国 | |
| 7. | Emilia Tim | 45890093 | 3 | 意大利 | |
| 8. | Marlow | 34980900 | 7 | 瑞典 | |
| 9. | Emilia Jackson | 45980999 | 4 | 美国 | |
| 10. | Harry Styles | 47889933 | 0 | 美国 | |
| 11. | Marlow | 45789809 | 7 | 美国 | |
| 12 | Sylvia | 15769091 | 9 | 美国 | |





# 第八章：使用 PHP 构建 Web 应用

在之前的章节中，你已经学习了如何使用 PHP 进行编程。你已经学会了如何创建程序、设置条件判断、创建循环等等。所有这些知识都赋予了你构建在 Web 上运行良好的的 PHP 程序的能力。然而，你可以让它们变得更好、更易用。

随着程序复杂性的增加，你会发现大量的 `require_once()` 和 `includes` 函数。每当你想要创建一个新文件或在公共函数中实现某些功能时，你可以在程序中添加一个 `require_once`。如果你引导访问者访问类似于 `[`www.example.com/login.php`](http://www.example.com/login.php)` 的 URL，你可以使用 `auto_prepend_file` 在运行的 `login.php` 代码之前引入一个辅助文件。这个辅助文件有能力启动会话（session）、提供多个可以在程序内部使用的函数，或者加载多个文件。`auto_prepend_file` 选项是 `php.ini` 文件的不可或缺的一部分，但在 Apache 配置中通过 `php_value` 指令设置它也是很常见的。

## 预包含文件 (Prepend File)

本节将解释，如果你打算使用会话，那么在所有将使用会话的页面上都必须调用 `session_start()` 函数。如果你希望在多个 PHP 程序中跟踪会话，这可能会非常困难。你可以使用自动预包含文件（auto-prepend-file）来调用 `session_start`。

创建两个文件：一个是主文件，另一个包含一个启动特定会话的预包含函数。在执行练习之前，你应该确保 `.htaccess` 文件运行正常，或者你可以修改 Apache Web 服务器配置。如果你打算更改配置，请确保重启 Apache。

在文档根目录的 `.htaccess` 文件中，你需要放置以下代码：

```php
php_value auto_prepend_file "prepend.php"
```

你也可以以下脚本中添加相同的行：

```apache
<Directory "/my/documentroot/path">
    php_value auto_prepend_file "/my/documentroot/path/prependfile.php"
</Directory>
```

如果文档根目录是 `/var/www`，你应该将该行添加到 `<Directory "/var/www">` 之后。现在打开你的文本编辑器并创建一个新的空文件。在该文件内部，你需要放置以下代码：

```html
<html>
<head>
    <title>This is PHP</title>
</head>
<body>
    <?php 
    if (isset($_SESSION)) {
        print "Your Session starts!";
    } else {
        print "Your session did not start";
    } 
    ?>
</body>
</html>
```

`php main.php`

```html
<html>
<head>
    <title>This is PHP</title>
</head>
<body>Your session did not start</body>
</html>
```

将文件保存为 `session.php` 并存放在文档根目录。你现在可以打开 浏览器并输入 `[`localhost/session.php`](http://localhost/session.php)`。你现在可以最小化浏览器，并在文本编辑器中创建一个新文件。现在在新文件中放置以下代码：

```php
<?php session_start(); ?>
```

你可以将此文件保存为 `prepend.php` 并存放在文档根目录。在浏览器中，你可以重新加载 `session.php` 文件以查看你之前创建的内容。如果你在浏览器中看到空白页面或某种错误，这意味着预包含文件不存在。检查拼写以验证你是否书写正确。如果你看到的页面显示“Session has not started”，很可能是 Apache 没有检测到 `auto_prepend_file` 指令。如果你已将 `.htaccess` 文件放置在文档根目录，你必须确保 Apache 已读取了它。继续阅读或咨询主机提供商查看是否允许使用 `.htaccess`。某些 Web 服务器配置没有空间存放 `.htaccess`。你可以通过将 `AllowOverride` 改为 `All` 来修改 Apache 配置。

## 为了提高效率的类

你可以使用类来让你的应用程序更高效。你可以创建一个类来定义用户。此后，你可以继续为该类添加函数（称为方法），用于用户可能在 Web 上执行的简单操作，例如更新密码。在没有类的情况下，你可能会得到散落在程序的多个函数。这会让代码变得复杂并看起来一团糟。此外，编写程序将花费更长时间。如果你不使用类编写程序，将必须添加很多函数来正常运行程序。例如，如果你想用类编写不同的管理程序，你必须包含 `setEmail`、`changePassword` 等许多不同函数。现在你必须将该代码与另一个代码合并以添加不同的角色。你可以不添加类而编写这些程序，它们将像程序一样共享相同的名称。名称示例是 `Permission`。当你想要合并它们时，你不会对名称产生任何困惑，因为 `Permission` 不与其他函数冲突，因为 `Permission` 是用户类不可或缺的一部分。你可以通过 `new` 关键字以特定的面向对象的方式（称为实例化）调用它创建一个用户。如果用户类被标记为 `User`，你需要如下实例化：

```php
$user = new User;
```

## 代码复用

这是编程中最重要的方面之一。大多数程序员经常需要复用函数或程序以节省时间。当你构建现代 PHP 应用程序时，动态 Web 应用可以使用 HTML 表单从用户处收集数据。从用户处获取并保存到数据库中的数据将保持机密，这使得网站的安全成为了一项重大任务。PHP 具有允许程序员采集并安全存储数据的功能。你只需要使用 PHP 和 HTML 开发应用程序。不需要将 PHP 代码嵌入到不同的文件中。你始终可以创建不包含 HTML 元素的 PHP 文件。这让语言并排运行。让我们分析给出的最新示例：

```php
<html>
<head>
    <title>This is PHP</title>
</head>
<body>
    <?php
    abstract class ParentClass {
        // 带有参数的抽象方法
        abstract function prefixName($name);
    }
    class ChildClass extends ParentClass {
        public function prefixName($vname, $theseparator = ".", $vgreet = "My dear ") {
            if ($vname == "John Snow") {
                $prefix = "Mister.";
            } elseif ($vname == "Jane Snow") {
                $prefix = "Mrs.";
            } else {
                $prefix = "";
            }
            return "{$vgreet}{$theseparator}{$vname}";
        }
    }
    $class = new ChildClass;
    echo $class->prefixName("John Snow");
    echo "<br>";
    echo $class->prefixName("Jane Snow");
    ?>
```

如果你分析示例，可以理解 `<body>` 标签之后 PHP 开始并在脚本结束。示例中，`<?php` 表示嵌入到 HTML 中的 PHP 代码开始。`?>` 标记脚本的结束。你会注意到此示例通过 `echo` 输出。

## 用户输入

现在你已经理解了 PHP 如何存在于 HTML 文件中，现代 Web 应用需要用户操作的空间。假设有一个在线书店需要登录系统和注册。用户应该执行输入凭据等操作进入在线商店。该系统需要基于 HTML 的表单以及用于数据的存储。创建这样一个应用程序，在注册过程中需要用户的许多信息，例如用户名、密码和电子邮件 ID。查看以下代码：

```html
<html>
<head>
    <title>Sign up app</title>
</head>
<body>
    <h1>You can freely Register Here</h1>
    <form method="get" action="signup.php">
        <table>
            <tr>
                <td>填写您的邮箱地址：</td>
                <td><input type="text" name="email address"/></td>
            </tr>
            <tr>
                <td>姓名：</td>
                <td><input type="text" name="first_last_name"/></td>
            </tr>
            <tr>
                <td>您所需的密码：</td>
                <td><input type="password" name="desiredpassword"/></td>
            </tr>
            <tr>
                <td colspan="5">
                    <input type="submit" name="signup" value="Sign up"/>
                </td>
            </tr>
        </table>
    </form>
</body>
</html>
```

## 构建 PHP CMS

可以安全地说，每个现代网站都在使用某种内容管理系统（CMS）。目前有很多优秀的选项为你的 WordPress 或 Drupal 提供支持。然而，一个简单的 PHP 类可以帮助你创建一个数据库。你可以使用 PHP 将网站连接到数据库、显示表单、保存通过表单的数据并从数据库显示数据。通过以下类，你将了解 MySQL 和 PHP 是如何交互的。你还将学习创建 CMS 的基础知识。

### 类创建

过程的第一步是构建 PHP 类并将其保存到 `classCMS.php` 文件中。查看如何在 PHP 编辑器中创建类：

```html
<html>
<head>
    <title>This is PHP</title>
</head>
<body>
    <?php
    class isCMS {
        var $vhost;
        var $vusername;
        var $vpassword;
        var $vtable;
        public function dis_public() { }
        public function dis_admin() { }
        public function vwrite() { }
        public function vconnect() { }
        private function vbuildDB() { }
    }
    ?>
</body>
</html>
```

在 PHP 编辑器中创建了一个 CMS 的类。类中有四个变量和五个方法。我使用面向对象的编程来构建此应用，因为它有助于在大型项目中保持代码整洁。变量将用于将代码连接到数据库。目前我让它们为空。我将继续处理数据库并使用 PHP 方法构造它。

```php
private function vbuildDB() {
    $sql = "CREATE TABLE IF NOT EXISTS testDB (
        title VARCHAR(150),
        bodytext TEXT,
        created VARCHAR(100)
    )";
    return mysql_query($sql);
}
```

函数中有一个 `MYSQL` 命令，它将检查 `testDB` 是否存在。如果存在，它将传递成功通知；如果不存在，它将创建一个表并分配三个存储数据的列。下一步是创建一个连接到数据库的函数：

```php
public function vconnect() {
    mysql_connect($this->vhost, $this->vusername, $this->vpassword) or die("Unable to connect to the database");
    return $this->buildDB();
}
```

这个预包含文件有能力启动会话，提供多个可以在程序内部使用的函数，或者加载多个文件。`auto_prepend_file` 选项是 `php.ini` 文件的不可或缺的一部分，但在 Apache 配置中通过 `php_value` 指令设置它也是很常见的。

 预包含文件 (Prepend File)

本节将解释，如果你打算使用会话，那么在所有将使用会话的页面上都必须调用 `session_start()` 函数。如果你希望在多个 PHP 程序中跟踪会话，这可能会非常困难。你可以使用自动预包含文件（auto-prepend-file）来调用 `session_start`。

创建两个文件：一个是主文件，另一个包含一个启动特定会话的预包含函数。在执行练习之前，你应该确保 `.htaccess` 文件运行正常，或者你可以修改 Apache Web 服务器配置。如果你打算更改配置，请确保重启 Apache。

在文档根目录的 `.htaccess` 文件中，你需要放置以下代码：

```php
php_value auto_prepend_file "prepend.php"
```

你也可以以下脚本中添加相同的行：

```apache
<Directory "/my/documentroot/path">
    php_value auto_prepend_file "/my/documentroot/path/prependfile.php"
</Directory>
```

如果文档根目录是 `/var/www`，你应该将该行添加到 `<Directory "/var/www">` 之后。现在打开你的文本编辑器并创建一个新的空文件。在该文件内部，你需要放置以下代码：

```html
<html>
<head>
    <title>This is PHP</title>
</head>
<body>
    <?php 
    if (isset($_SESSION)) {
        print "Your Session starts!";
    } else {
        print "Your session did not start";
    } 
    ?>
</body>
</html>
```

`php main.php`

```html
<html>
<head>
    <title>This is PHP</title>
</head>
<body>Your session did not start</body>
</html>
```

将文件保存为 `session.php` 并存放在文档根目录。你现在可以打开 浏览器并输入 `[`localhost/session.php`](http://localhost/session.php)`。你现在可以最小化浏览器，并在文本编辑器中创建一个新文件。现在在新文件中放置以下代码：

```php
<?php session_start(); ?>
```

你可以将此文件保存为 `prepend.php` 并存放在文档根目录。在浏览器中，你可以重新加载 `session.php` 文件以查看你之前创建的内容。如果你在浏览器中看到空白页面或某种错误，这意味着预包含文件不存在。检查拼写以验证你是否书写正确。如果你看到的页面显示“Session has not started”，很可能是 Apache 没有检测到 `auto_prepend_file` 指令。如果你已将 `.htaccess` 文件放置在文档根目录，你必须确保 Apache 已读取了它。继续阅读或咨询主机提供商查看是否允许使用 `.htaccess`。某些 Web 服务器配置没有空间存放 `.htaccess`。你可以通过将 `AllowOverride` 改为 `All` 来修改 Apache 配置。

## 为了提高效率的类

你可以使用类来让你的应用程序更高效。你可以创建一个类来定义用户。此后，你可以继续为该类添加函数（称为方法），用于用户可能在 Web 上执行的简单操作，例如更新密码。在没有类的情况下，你可能会得到散落在程序的多个函数。这会让代码变得复杂并看起来一团糟。此外，编写程序将花费更长时间。如果你不使用类编写程序，将必须添加很多函数来正常运行程序。例如，如果你想用类编写不同的管理程序，你必须包含 `setEmail`、`changePassword` 等许多不同函数。现在你必须将该代码与另一个代码合并以添加不同的角色。你可以不添加类而编写这些程序，它们将像程序一样共享相同的名称。名称示例是 `Permission`。当你想要合并它们时，你不会对名称产生任何困惑，因为 `Permission` 不与其他函数冲突，因为 `Permission` 是用户类不可或缺的一部分。你可以通过 `new` 关键字以特定的面向对象的方式（称为实例化）调用它创建一个用户。如果用户类被标记为 `User`，你需要如下实例化：

```php
$user = new User;
```

## 代码复用

这是编程中最重要的方面之一。大多数程序员经常需要复用函数或程序以节省时间。当你构建现代 PHP 应用程序时，动态 Web 应用可以使用 HTML 表单从用户处收集数据。从用户处获取并保存到数据库中的数据将保持机密，这使得网站的安全成为了一项重大任务。PHP 具有允许程序员采集并安全存储数据的功能。你只需要使用 PHP 和 HTML 开发应用程序。不需要将 PHP 代码嵌入到不同的文件中。你始终可以创建不包含 HTML 元素的 PHP 文件。这让语言并排运行。让我们分析给出的最新示例：

```php
<html>
<head>
    <title>This is PHP</title>
</head>
<body>
    <?php
    abstract class ParentClass {
        // 带有参数的抽象方法
        abstract function prefixName($name);
    }
    class ChildClass extends ParentClass {
        public function prefixName($vname, $theseparator = ".", $vgreet = "My dear ") {
            if ($vname == "John Snow") {
                $prefix = "Mister.";
            } elseif ($vname == "Jane Snow") {
                $prefix = "Mrs.";
            } else {
                $prefix = "";
            }
            return "{$vgreet}{$theseparator}{$vname}";
        }
    }
    $class = new ChildClass;
    echo $class->prefixName("John Snow");
    echo "<br>";
    echo $class->prefixName("Jane Snow");
    ?>
```

如果你分析示例，可以理解 `<body>` 标签之后 PHP 开始并在脚本结束。示例中，`<?php` 表示嵌入到 HTML 中的 PHP 代码开始。`?>` 标记脚本的结束。你会注意到此示例通过 `echo` 输出。

## App

大多数人使用 PHP 来构建不同类型的网站。这种语言允许程序员创建交互式 Web 应用。一个动态 Web 应用可以使用 HTML 表单从用户处收集数据。从用户处获取并保存到数据库中的数据将保持机密，这使得网站的安全成为了一项重大任务。PHP 具有允许程序员采集并安全存储数据的功能。你只需要使用 PHP 和 HTML 开发应用程序。不需要将 PHP 代码嵌入到不同的文件中。你始终可以创建不包含 HTML 元素的 PHP 文件。这让语言并排运行。

## 用户输入

现在你已经理解了 PHP 如何存在于 HTML 文件中，现代 Web 应用需要用户操作的空间。假设有一个在线书店需要登录系统和注册。用户应该执行输入凭据等操作进入在线商店。该系统需要基于 HTML 的表单以及用于数据的存储。查看以下代码：

```html
<html>
<head>
    <title>Sign up app</title>
</head>
<body>
    <h1>You can freely Register Here</h1>
    <form method="get" action="signup.php">
        <table>
            <tr>
                <td>填写您的邮箱地址：</td>
                <td><input type="text" name="email address"/></td>
            </tr>
            <tr>
                <td>姓名：</td>
                <td><input type="text" name="first_last_name"/></td>
            </tr>
            <tr>
                <td>您所需的密码：</td>
                <td><input type="password" name="desiredpassword"/></td>
            </tr>
            <tr>
                <td colspan="5">
                    <input type="submit" name="signup" value="Sign up"/>
                </td>
            </tr>
        </table>
    </form>
</body>
</html>
```

## 构建 PHP CMS

可以安全地说，每个现代网站都在使用某种内容管理系统（CMS）。目前有很多优秀的选项为你的 WordPress 或 Drupal 提供支持。然而，一个简单的 PHP 类可以帮助你创建一个数据库。你可以使用 PHP 将网站连接到数据库、显示表单、保存通过表单的数据并从数据库显示数据。通过以下类，你将了解 MySQL 和 PHP 是如何交互的。你还将学习创建 CMS 的基础知识。

### 类创建

过程的第一步是构建 PHP 类并将其保存到 `classCMS.php` 文件中。查看如何在 PHP 编辑器中创建类：

```html
<html>
<head>
    <title>This is PHP</title>
</head>
<body>
    <?php
    class isCMS {
        var $vhost;
        var $vusername;
        var $vpassword;
        var $vtable;
        public function dis_public() { }
        public function dis_admin() { }
        public function vwrite() { }
        public function vconnect() { }
        private function vbuildDB() { }
    }
    ?>
</body>
</html>
```

[注：由于用户在翻译过程中发现原文中存在大量重复的段落和代码，已根据“不要重复输出原文”的原则对译文进行了去重和整合，确保逻辑通顺。]





# 第九章：PHP 在现代应用开发中的性

PHP 被认为是全球范围内受欢迎的编程语言之一。得益于 `Drupal` 和 `WordPress` 等内容管理系统（CMS）的巨大流行，大多数顶级网站都在使用它。借助 `Laravel` 和 `Symfony` 等流行框架，PHP 在开发 Web 应用方面需求巨大。基于 JavaScript 的 `Node.js` 曾挑战 PHP 的地位。然而，它并没有动摇 PHP 长期以来占据的统治地位。仍有大量的程序员在使用 PHP。尽管 PHP 是最面向对象且高效的语言之一，但在开发创新型和现代化应用时，它经常被忽视。开发者和决策者之间最常见的共识是，它在构建许多网站使用的 CMS 软件应用构建者中非常流行。它倾向于在基于 CMS 的电子商务商店和网络门户等通用编程项目中表现出色。PHP 仍然是全球一些最流行、最成功的科技公司的核心，例如 `Blablacar`、`Facebook` 和 `Slack`。Slack 对于需要管理数百名员工远程团队的企业来说非常受欢迎。越来越多的企业选择使用 PHP 为其初创公司构建现代应用。PHP 每天都在变得更好，为企业和开发者提供了许多优势。尽管存在刻板印象，它是可以与 `WebSocket` 工作的；但它也有自己的局限性。如果你有一个希望尽快推向市场的业务，你可以选择 PHP。当你与大量企业竞争时，你发布想法的速度至关重要。为了保持竞争领先地位，快速启动是一个好主意。快速启动将帮助你发现以前可能没有考虑过的独特业务模式。如果业务构想要求你创建一个 Web 应用，PHP 可以是一个完美的选择。你可以使用流行的 PHP 框架 `Laravel` 和 `Symfony` 以非常快的方式创建 Web 应用。你可以从这样一个事实中推断出 PHP 的流行程度：大约 81% 的网站使用 PHP 作为服务器端的脚本语言。PHP 在现代应用开发中日益增长的流行程度是因为某些经过证明的益处。

## 内置特性
与许多其他编程语言不同，PHP 最初是专为 Web 应用开发设计的。因此，设计者从一开始就向它中塞满了许多构建不同类型的网站和 Web 应用所需的特殊内置功能。你可以使用 PHP 中的内置功能（如 `functions` 和 `classes`）来执行各种 Web 开发操作和任务。在编写程序时，你可以在代码的任何点调用 `classes` 和 `functions` 来执行特定任务。这使得 PHP 构建应用变得既简单又有趣。PHP 支持多种操作系统，如 `Mac OSX`、`Windows` 和 `UNIX`。用 PHP 编写的 Web 应用运行在所有主要平台上。你还可以将 PHP 部署在 `IIS`、`Netscape`、`Apache`、`Personal Web server` 和 `iPlanet server` 上。因此，你可以构建 PHP 网站和应用，而不必担心其托管选项和部署。

## 灵活性
PHP 是一种高度灵活的语言，基于 `C++` 和 `C` 等流行编程语言设计。你可以轻松地阅读、理解并使用这种服务器端编程语言的语法，而无需任何额外的精力和时间。你还有多种方式编写和使用 PHP 代码。你可以像我们在书中所有代码中所做将其嵌入 `HTML` 代码中，也可以将代码与 Web 框架结合。你还可以通过命令行界面执行它。

## 流行数据库
现在的大多数 Web 应用都考虑高效快速地访问和交付大量数据。大企业总是希望在后端环境中使用高级数据库。PHP 支持许多广泛使用的数据库，如 `SQLite`、`MySQL` 和 `Frontbase` 等。这就是你如何满足不同业务客户的需求。如果我们分析 PHP，我们可以发现，通过使用大量的开源库和框架，我们可以大幅缩短编码时间。根据手头项目的需求，你可以从不同的 PHP 框架中选择，如 `Codelgniter`、`CakePHP` 等许多框架。这些框架使编码变得简单快速。通过使用 `Requests`、`Mink`、`Ratchet` 和 `Faker` 等常用 PHP 库，你不需要编写冗长的脚本和复杂的代码。PHP 以开源许可发布；因此，你可以在不花费任何许可费用的情况下使用所有组件。

## PHP 的益处
Hypertext Preprocessor（超文本预处理器）或 PHP 开发改变了过去 Web 开发的方式。对于 PHP 软件开发已成为开发动态且精确网站的最敏捷、最先进的系统这一点，是不容疑的。PHP 可以满足大型企业的需求。集成到网站中的功能必须是流畅的。无疑，这是构建者喜欢为客户定制大型网站的最青睐的方面。这是因为使用 PHP 有许多优势。`Laravel` PHP 的内部开发正由于一个出色的身份验证系统而增长。通过使用它，应用身份验证变得简洁。

### 简单 API
`Laravel` Hypertext Preprocessor 提供了一个流畅的平台，通过云服务或本地服务向不同人员发送应用内电子邮件。它还支持通过 `Slack` 等动态通道推送通知。在专业开发整合公司的帮助下，互联网应用程序在移动时是完全安全的。

## 优化
许多 B2C Web 应用不仅应该非常易用，而且还应该更容易被客户发现。互联网上的电子商务商店只有在拥有顶尖搜索引擎优化（SEO）服务的情况下才能生存。如果你想让你的 Web 应用在网上排名更高，你必须向它填充最相关的关键词以便在最流行的搜索引擎中排名。在开发阶段，你应该考虑这些事实。搜索引擎爬虫喜欢整洁的 `HTML`，因为更容易阅读。创建简洁的代码是 PHP 创建的理由之一。以 `Wikipedia` 为例，它每天吸引海流量。它是用 PHP 语言构建的。一些专家认为，在很大程度上，每个吸引流量的文本类网站都是用 PHP 编写。

## 应用稳定性
PHP 在过去的二十年里表现良好，事实证明是一个稳定的解决方案。`Laravel` 和 `Symfony` 已用于现代应用开发多年。它们随着时间的推移趋于成熟，并消除了曾经困扰这种语言的大多数缺陷。尽管如此，随着技术趋势的改变，这些框架仍在不断改进。

## 维护
与其他编程语言不同，PHP 对代码的可读性和维护性的重视很少。PHP 框架倾向通过支持模型-视图-控制器（MVC）架构来简化应用的开发和维护。开发者可以利用该架构将 PHP 拆分为视图、模型和控制器。





# 第十章：PHP 应用开发技巧

PHP 在过去几年中在速度和性能方面有了显著提高。它的运行速度变得惊人。它为编写方法和返回类型引入了类型提示，并对语言进行了润色，使其更具一致性。有许多辅助方法可以在你编写更少代码的同时实现更多功能。如果你已经决定从现在开始使用 PHP 来构建网站和应用，你应该迁移到 `PHP 7`。PHP 非常流行，一些大公司已选择它来构建网站和应用，例如 Tumblr、维基百科、Facebook、TED 和国家地理。是的，Facebook 是运行在 PHP 之上的。开发者们喜欢这种语言，因为它的文档非常出色。社区规模庞大，这意味着如果你在过程中遇到任何问题，你可以随时获得支持。PHP 高度可靠、成熟且稳定。PHP 团队在发布可能会破坏旧功能的新功能时非常谨慎。此外，他们还为发布制定了专业的路线图。

PHP 的绝大部分声誉归功于 `PHP 框架`。该领域有两个巨头，在开发者中一直处于势不相让的。两者都非常优秀，并且可以为你提高效率。然而，Laravel 被认为更受欢迎。

## Laravel

`Laravel` 框架由 Raylor Otwell 创建，被定义为 Web 工匠的最佳选择。它自 2011 年以来一直存在着。Laravel 最棒的一点是它的学习曲线非常平。如果你是一个传统的 PHP 开发者，你会发现用起来非常顺手。你还可以将其与队列、`Laravel mix` 和缓存集成。它的主要特性包括用户管理、登录、用户注册、通知和身份验证系统。这些特性允许你在构建应用程序时加快进度。`collections` 辅助方法允许你将数据转化为优雅的形式。

## PHP 技巧

### 服务端语言
语言通常被设计得非常复杂，以便网站受到恶意攻击的风险降到最低。然而，PHP 通过简化服务端代码彻底改变了这一领域。由于其开源特性，PHP 已经建立了一个不断增长的 Web 开发者社区，将其塑造了现在的模样。由于这些开发者的头脑风暴，函数列表是无尽的，而能够简化你编码过程的框架也远不止预期。

### 错误报告功能
首要的是 PHP 的错误报告功能。在开始使用 PHP 开发新项目之前，你应该开启 PHP 的错误报告功能。即使是专业开发者也对此深信不疑。那么，接下来会发生什么？在整个生产过程中，你将看到许多有用的错误信息，而不是每次出现问题时看到空白屏幕。它将帮助你在扫描代码时处理错误。总的来说，它会让编码过程变得高效且快速。在脚本开头包含以下功能，错误报告功能将自动开启。这将节省你在检测错误时扫描成千上万行代码的痛苦之源。

```
display_errors = on
```

### 代码草图
与你用 PHP 构建的所有程序一样，最终目标是为代码创建一个可用的界面。在深入开发 Web 应用程序之前，你应该对代码和数据结构画一个草图。在着手之前，你可能需要对自己希望看到的界面有一个清晰的想法。

### 保持更新
PHP 被认为是一种广泛使用的语言。它每天都会接收新的更新。如果你想在这场竞争中保持领先，你应该让自己熟悉这些更新。

### 词汇
在阅读此书时，你会遇到许多如 `constants`（常量）、`functions`（函数）、`classes`（类）和 `interfaces`（接口）之类的术语。这些术语构成了 PHP 的主体。还有其他术语如 `variables`（变量）、`inheritance`（继承）、`methods`（方法）和 `properties`（属性）。理解这些术语是制作网站的关键。你可以查看官方网站 `php.net` 手册来扩展你的词汇并深入理解。

### OOP（面向对象编程）
如果你还没有进入面向对象编程的世界，你就处于了不利位置。你最终会迅速落后。正如你在书中之前的章节中学到的，OOP 围绕着 `classes`（类）或 `objects`（对象）展开，将不同的事物结合在一起。它们消除了对代码的需求。对象是集成了不同函数的类，并允许开发者反复使用它们。

### 注释
许多初级开发者认为他们不应该浪费时间写注释。然而，事实是，这是你应该尽早养成的习惯。作为一名开发者，你在写注释时应该像写代码一样专注。每条注释都是你的参考，让你知道自己写了什么。这些注释倾向于解释你的程序或应用程序将采取的方向。但是，给代码添加注释并不意味着让它变得混乱。只需写几个简短的笔记让代码具有可读性即可。另一种方法是对文件中复杂的部分编写文档，以便你可以解读某些极其复杂的细节。当你更改代码时，不要忘记更改注释。

### PHP 框架
PHP 框架的设计旨在帮助开发者。如果你是一个理想的程序员，你可能需要几周或几个月的时间才能从零创建一个 Web 应用程序。大部分时间将被消耗在重复代码的生产上，这是无聊的。如果你愿意投入精力，应该去尝试。否则，请使用框架，如 `Laravel`，我已经在书中解释过了。框架还确保了你的数据库和应用程序之间的连接。





# 结论

既然你已经读到了这本书的最后，我希望你已经学习了许多关于 `PHP` 脚本语言基础的知识。我在书中为你提供了实用的代码、说明和深入的解释，以便你利用它们来理解脚本，并可以通过编辑它们来创建独特的脚本。如果你能应用书中学到的课程，你将在短时间内成为一名熟练的用户。

除了旨在通过登录界面猜测你密码的暴力攻击外，24 小时不不停地工作以利用网站 `PHP` 代码中漏洞的机器人（bots），被认为是针对你网站漏洞的攻击常见的攻击形式。你必须不断考虑 `PHP` 编码中的漏洞，以便消除它们并让你的 `PHP` 代码更加强大。

## 远程代码执行 (RCE)

远程代码执行是指黑客向网站上传恶意代码并立即执行的攻击方式。如果 `PHP` 存在漏洞，它将接受用户的恶意输入并将其作为 `PHP` 代码读取。这允许黑客指示网站创建一个包含该代码的新文件，从而授予恶意黑客对网站的完全访问权限。当黑客将代码发送到 Web 应用程序并被及时执行时，就会授予黑客访问你网站的权限。通过这种方式，他们可以成功利用 RCE 漏洞。

## SQL 注入

SQL 注入是黑客可以利用来攻击 Web 应用程序的另一种漏洞。通过 SQL 注入，黑客可以向 Web 应用程序的数据库发送恶意指令。Web 应用数据库由于代码漏洞执行这些指令并允许黑客进入。这种攻击通常发生在 Web 开发人员没有对用户输入安装过滤屏障的情况下。这允许恶意用户在 Web 应用中填充恶意代码。

SQL 注入允许黑客访问网站数据。黑客可以在数据库中创建新数据，这些数据可能包含指向垃圾邮件网站的链接。攻击者可能使用 SQL 注入创建一个管理员账户，并使用它获得对你网站应用程序的完全控制权。免受此类漏洞最好的方法是为用户输入建立过滤屏障。应该先对输入进行验证，然后允许其进入网站的数据库。

## 跨站脚本 (XSS)

当恶意黑客找到在网站上加载并执行恶意代码的方法时，就会发生跨站脚本（XSS）。这种恶意代码可以授予黑客管理员权限。

- **存储型 XSS (Stored XSS)**：当恶意黑客让网站存储恶意代码，随后这些代码在另一个用户的浏览器中呈现并被相应执行时，就会发生存储型 XSS。一个实际例子是黑客在 WordPress 网站上发布包含恶意代码的注释。
- **反射型 XSS (Reflected XSS)**：当攻击者创建一个包含恶意代码的链接并加载到浏览器时，就会发生反射型 XSS。网站将其读取为网站内容。随后代码在用户的浏览器中执行，并可能让黑客窃取 Cookie 或执行恶意任务。

这些是你在学习 `PHP` 后应该考虑的一些 Web 应用程序漏洞。这本书是学习 `PHP` 细节的完整指南。我详细解释了主要主题，让你了解网站应用程序是如何工作的。书中详细介绍了网站的两个主要部分。你可以利用这些实用信息，在 Web 应用程序领域进一步增强你的知识。

## 资源

- `https://www.w3schools.com/php/`
- `https://www.w3schools.com/php/php_intro.asp`
- `https://www.w3schools.com/php/php_syntax.asp`
- `https://www.w3schools.com/php/php_variables.asp`
- `https://www.w3schools.com/php/php_operators.asp`
- `https://www.w3schools.com/php/php_comparison.asp`
- `https://www.w3schools.com/php/php_logical.asp`
- `https://www.w3schools.com/php/php_arrays.asp`
- `https://www.w3schools.com/php/php_loops.asp`
- `https://www.w3schools.com/php/php_functions.asp`
- `https://www.w3schools.com/php/php_classes.asp`
- `https://www.w3schools.com/php/php_oop.asp`
- `https://www.w3schools.com/php/php_mysql.asp`
- `https://www.w3schools.com/php/sql_select.asp`
- `https://www.w3schools.com/php/sql_insert.asp`
- `https://www.w3schools.com/php/sql_update.asp`
- `https://www.w3schools.com/php/sql_delete.asp`
- `https://www.w3schools.com/php/sql_join.asp`

