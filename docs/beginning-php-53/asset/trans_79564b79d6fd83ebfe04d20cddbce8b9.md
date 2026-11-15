

## 在 Windows 上安装

PHP 在 Windows 上可以与 Apache 或 IIS 配合使用。为求简单，本章将介绍一种非常简便的安装 Apache 和 PHP 的方法：WampServer。这个方便的软件将 Apache、MySQL 和 PHP 集成在一个易于安装的包中。

WampServer 源自缩写 WAMP —— Windows、Apache、MySQL 和 PHP —— 用于描述任何使用这三种开源技术的基于 Windows 的 Web 服务器配置。

要安装 WampServer，请执行以下步骤：

- 1. 从 http://www.wampserver.com/en/ 下载 WampServer 的最新版本。撰写本文时，最新版本是 PHP 5.2.6；但是，当您阅读本文时，很可能已经有 PHP 5.3 版本可用。

- 2. 打开下载的 WampServer .exe 文件，并按照屏幕上的说明安装应用程序。

- 3. 取消对 Apache 的阻止。运行安装程序时，系统可能会询问您是否要允许 Apache 通过 Windows 防火墙，如图 2-4 所示。如果要允许网络上的其他计算机访问 Web 服务器，请单击 Unblock。如果您只打算从同一台计算机上的浏览器访问 Web 服务器，可以单击 Keep Blocking 以提高安全性。

![](img/1ddec54918a4802eb9b4febec3d4e7f6_52_0.png)

图 2-4

- 4. 输入默认邮件设置。在配置过程中，系统还会要求您输入 PHP 要使用的默认邮件服务器和电子邮件地址（图 2-5）；目前您可以接受默认设置。

![](img/1ddec54918a4802eb9b4febec3d4e7f6_53_0.png)

图 2-5

- 5. 安装向导完成后，您应该在任务栏中看到 WampServer 图标；单击此图标以显示 WampServer 菜单（图 2-6）。选择 Start All Services 选项以启动 Apache 和 MySQL 服务器。

![](img/1ddec54918a4802eb9b4febec3d4e7f6_53_1.png)

图 2-6

- 6. 要测试 Web 服务器是否正在正常运行，请从 WampServer 菜单中选择 Localhost 选项。如果一切按计划进行，您应该会看到图 2-7 所示的页面；这意味着 WampServer 已成功安装。恭喜！转到本章的“测试您的安装”部分，以确保一切正常。

![](img/1ddec54918a4802eb9b4febec3d4e7f6_54_0.png)

图 2-7

## 在 Mac OS X 上安装

Mac OS X 已预安装了 Apache 和 PHP 的一个版本。但是，已安装的版本可能有些过时。此外，Mac OS X 默认未预安装 MySQL 软件包，虽然完全可以自行安装。（您需要 MySQL 或类似的数据库系统来构建数据库驱动的 Web 网站，如本书后面所述。）

幸运的是，正如 Windows 有 WAMP，Mac OS X 有 MAMP —— 一个集成的、易于安装的包，可为您的 Mac 提供 Apache、MySQL 和 PHP 设置。MAMP（及其 Windows 版 WAMP 等同物）的妙处在于它是独立的。这意味着它不会弄乱已安装的任何现有服务器软件；其所有文件都存储在单个文件夹下；如果您想要，以后还可以非常轻松地卸载它。

要在 Mac 上安装 MAMP，请执行以下步骤：

- 1. 从 www.mamp.info/en/ 下载最新的 MAMP 版本。（撰写本文时，有两个版本可用：MAMP 和 MAMP PRO。常规 MAMP 用于在 Mac 上开发 PHP 应用程序已经足够。）

- 2. 打开下载的 MAMP .dmg 文件。

- 3. 在弹出的窗口中，将 MAMP 文件夹拖到 Applications 文件夹上方以安装它。

- 4. 在 Finder 中打开 Applications 文件夹内的 MAMP 文件夹，然后双击 MAMP 图标以启动应用程序。

## 第一部分：使用 PHP 入门

- 5. 如果需要，单击 Start Servers 按钮启动 Apache 和 MySQL 服务器。它们运行后，您应该会在对话框中看到它们旁边的绿灯亮起，如图 2-8 所示。

![](img/1ddec54918a4802eb9b4febec3d4e7f6_55_0.png)

图 2-8

- 6. 要测试 Web 服务器是否正在正常运行，请单击 Open Start Page 按钮。如果看到类似图 2-9 所示的页面出现，恭喜——您的 Mac 上现在有一个可正常工作的 Apache、PHP 和 MySQL 安装！

![](img/1ddec54918a4802eb9b4febec3d4e7f6_55_1.png)

图 2-9

默认情况下，MAMP 的 Apache 服务器运行在端口 8888 上，其 MySQL 服务器运行在端口 8889 上。这是为了避免与 Mac 上可能运行的任何其他 Apache 或 MySQL 服务器发生冲突，但这也意味着您需要在浏览器地址栏的 URL 中指定 Apache 端口（8888），如图 2-9 所示。如果您愿意，可以单击 MAMP 应用程序中的 Preferences 按钮来更改 MAMP Apache 和 MySQL 服务器使用的端口。例如，只要您已停止 Mac 上可能使用标准 HTTP 端口 80 的任何其他 Web 服务器，就可以将 MAMP Apache 端口设置为 80，以免必须在浏览器地址栏中输入端口号。

与先前讨论的 Linux 和 Windows 安装选项一样，撰写本文时 MAMP 安装的是 PHP 5.2，而非 PHP 5.3。但是，当您阅读本书时，很可能 MAMP 会提供 PHP 5.3 版本。

## 测试您的安装

现在您已在计算机上安装了 Apache、PHP 和 MySQL，可以测试安装以确保一切正常。在此过程中，您将创建您的第一个 PHP 脚本（虽然是一个极其简单的脚本！）。

### 测试 Web 服务器

首先要做的是创建一个简单的 HTML 网页用于测试。在诸如 Windows 上的 Notepad、Mac 上的 TextEdit 或 Linux 上的 `vi`/`emacs`/`pico` 等文本编辑器中，创建以下简单网页：

```
<html>
<head>
<title>Testing</title>
</head>
<body>
<h1>Testing, testing, 1-2-3</h1>
</body>
</html>
```

将网页命名为 `testing.html`，并将其保存在硬盘上 Web 服务器的文档根目录文件夹中。什么是文档根目录文件夹，您可能会问？安装 Apache 时，它会附带一个默认网站。这个网站有一个文档根目录文件夹，即您存放网站文件的顶级文件夹。您希望将 `testing.html` 网页保存在此文件夹中，以便可以通过 Web 浏览器访问它。

那么，文档根目录文件夹在哪里？这取决于您的设置，如下所示：

- - 如果您在 Ubuntu Linux 上安装了 Apache，文档根目录文件夹可能是 `/var/www`。
- - 在 Windows 上使用 WampServer 时，文档根目录文件夹通常位于 `C:\wamp\www`。
- - 如果您将 MAMP 安装到 Mac 的 `/Applications` 文件夹中，文档根目录文件夹可能是 `/Applications/MAMP/htdocs`。（请注意，您可以打开 MAMP 应用程序并单击 Preferences，然后单击 Apache 选项卡来检查甚至更改此设置。）

因此，将 `testing.html` 文件保存到相应的文件夹，然后打开 Web 浏览器，在地址栏中输入以下内容：

```
http://localhost/testing.html
```

现在按 Enter 键。如果一切按计划进行，您应该会看到类似图 2-10 的内容。

![](img/1ddec54918a4802eb9b4febec3d4e7f6_57_0.png)

图 2-10

如果您的 Apache 服务器未运行在标准 HTTP 端口（80）上——例如，如果您安装了 MAMP 并使用其默认端口 8888——请相应地修改 URL；例如：http://localhost:8888/testing.html 。

这意味着 Apache 已经启动并正在运行，并且您已成功找到 Web 服务器的文档根目录。如果您看不到此页面，很可能发生以下两种情况之一：

- - [ ] 如果您收到 404 Not Found 错误，这意味着 testing.html 文件不在 Web 服务器的文档根目录中。再次检查文档根目录文件夹的位置——如有必要，请查看文档——并确保 testing.html 文件位于该文件夹内。
- - [ ] 如果您收到 Connection Refused 错误，Apache Web 服务器未运行（或者它正在不同的端口上运行）。检查您是否已启动 Web 服务器，以及是否已正确配置它（同样，随软件包提供的文档应该能提供帮助）。

### 测试 PHP

现在您知道 Apache 正在正常工作，是时候确保 PHP 已安装并正常工作了。这时您就可以编写您的第一个 PHP 脚本了！

再次打开文本编辑器，创建一个包含以下内容的新文件：

```
<?php
phpinfo();
?>
```

将此文件另存为 testing.php，保存在与 testing.html 相同的文件夹中——也就是说，文档根目录文件夹。现在在地址栏中输入以下内容（如有必要调整 HTTP 端口号）：

http://localhost/testing.php

按 Enter 键，您应该会看到类似图 2-11 的页面出现。（如果您安装了 PHP 5.3，您当然会在页面中看到对 5.3 版本的引用，而不是 5.2 版本。）这是运行 phpinfo() 函数的结果，这是一个内置的 PHP 函数，用于显示已安装的 PHP 版本的信息。这意味着您已成功安装 Apache 和 PHP。恭喜！

