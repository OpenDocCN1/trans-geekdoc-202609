
## 附录 B
### 如何为本书设置 Mac OS X

本附录展示了如何在 Mac OS X 上安装和配置我们推荐用于开发 PHP 应用的软件。该软件包括 XAMPP 包、NetBeans IDE、作为默认浏览器的 Google Chrome 以及作为文本编辑器的 TextWrangler。本附录还展示了如何为本书安装示例应用程序和练习。

在阅读本附录时，请记住大多数网站都在不断更新。因此，自本书出版以来，本附录中的某些操作步骤可能已发生变化。尽管如此，这些操作步骤仍可作为安装软件的良好指南。如果这些设置说明有重大更改，我们将在我们的网站（www.murach.com）上发布更新。

- **如何安装 Chrome 和 TextWrangler** ................................ 824
  - 如何安装 Chrome 浏览器 ....................................... 824
  - 如何安装 TextWrangler ............................................. 824
- **如何安装和配置 XAMPP** ................................. 826
  - 如何安装 XAMPP ..................................................... 826
  - 如何配置 phpMyAdmin ............................................. 828
- **如何安装 NetBeans 和 xDebug** ................................ 830
  - 如何安装 NetBeans .................................................. 830
  - 如何配置 xDebug .................................................. 830
- **如何安装本书应用程序和数据库** ................ 832
  - 如何安装本书的源代码 ............................ 832
  - 如何创建和恢复数据库 ................................ 834
- **如何修复时区可能出现的问题** ................... 836

## 如何安装 Chrome 和 TextWrangler

在做本书中的练习并使用应用程序时，我们建议您使用 Google Chrome 来测试您的应用程序。此外，我们建议您使用 TextWrangler 作为文本编辑器。这两个应用程序都是免费的，安装也不需要很长时间。

### 如何安装 Chrome 浏览器

图 B-1 显示了如何下载和安装 Chrome。在响应安装程序的对话框时，我们建议您将 Chrome 设为默认浏览器。

### 如何安装 TextWrangler

图 B-1 也显示了如何下载和安装 TextWrangler。

### 下载 Chrome 的网址

[www.google.com/chrome/](http://www.google.com/chrome/)

### 如何安装 Chrome

1. 转到上面的网站地址。
2. 点击“下载 Chrome”按钮。
3. 查看服务条款，保持“将 Google Chrome 设为我的默认浏览器”复选框已选中，然后点击“接受并安装”按钮。这将把磁盘映像（dmg）文件保存到您的硬盘上。
4. 如果 Chrome 磁盘窗口未出现，双击磁盘映像文件以打开磁盘窗口。
5. 在 Chrome 磁盘窗口中，将 Chrome 图标拖到“应用程序”文件夹图标上。然后关闭 Chrome 窗口。
6. 打开“应用程序”文件夹并双击 Chrome 图标以启动 Chrome。

### 下载 TextWrangler 的网站地址

[www.barebones.com/products/textwrangler](http://www.barebones.com/products/textwrangler)

### 如何安装 TextWrangler

1. 转到上面的网站地址。
2. 点击“立即下载”按钮。点击磁盘映像（dmg）的下载链接，并将磁盘映像文件保存到您的硬盘上。
3. 如果 TextWrangler 磁盘窗口未打开，双击 TextWrangler 磁盘映像文件以打开 TextWrangler 磁盘窗口。
4. 在 TextWrangler 磁盘窗口中，将 TextWrangler 图标拖到“应用程序”文件夹图标上。然后关闭 TextWrangler 窗口。
5. 打开“应用程序”文件夹并双击 TextWrangler 图标以启动 TextWrangler。

图 B-1 — 如何安装 Chrome 和 TextWrangler

## 如何安装和配置 XAMPP

在开发基于数据库的 PHP 应用程序之前，您需要安装和配置 Web 服务器、数据库服务器以及 PHP 语言的解释器。对于本书，我们推荐 Apache Web 服务器和 MySQL 数据库服务器。尽管您可以单独安装和配置这些组件，但这可能很繁琐且容易出错。因此，我们建议使用 XAMPP 包来简化 Apache、MySQL 和 PHP 的安装。

请注意，XAMPP 的安装默认情况下并不安全。因此，在正确加固之前，不应将其用作生产服务器。在阅读本书的过程中，您将了解更多关于保护 XAMPP 安装的信息。

### 如何安装 XAMPP

图 B-2 显示了安装 XAMPP 1.8.3 的流程，其中包含 PHP 5.5。当您使用此流程时，Apache Friends 网站会链接到 SourceForge 网站以提供 XAMPP 安装程序文件的下载。

在撰写本文时，Mac OS X 的最新 XAMPP 版本是 XAMPP 1.8.3（PHP 5.5）。如果您在安装 XAMPP 时发现更新的版本，我们建议您安装 XAMPP 1.8.3（PHP 5.5）而不是更新的版本。这样，您的计算机应按本书所述运行。当 XAMPP 的新版本可用时，您应该能在 SourceForge 网站上找到旧版本的 XAMPP。

完成基本安装后，您可以通过启动和停止 Apache 和 MySQL 服务器（如本图所示所述）来测试该安装。

启动 Apache 服务器后，您可以通过启动 Web 浏览器并导航到以下目录来测试它：

```
http://localhost/xampp
```

如果此 URL 显示网页，则表示您已成功安装并启动了 Apache 服务器。

### 下载适用于 Mac OS X 的 XAMPP 1.8.3 的网站地址

http://sourceforge.net/projects/xampp/files/

### 如何安装适用于 Mac OS X 的 XAMPP 1.8.3

1. 转到上面的网站地址。
2. 点击“下载”按钮。
3. 将磁盘映像（dmg）文件保存到您的硬盘上。
4. 使用 Finder 找到磁盘映像（dmg）文件并双击它以打开安装程序窗口。您需要输入系统密码。
5. 按照 XAMPP 设置向导中的说明操作。

### XAMPP 控制面板

![](img/b7dd5fec6684a99ab526c7fe8e21e7de_850_0.png)

### 如何启动和停止 Apache 和 MySQL 服务器

1. 打开“应用程序”文件夹并打开 XAMPP 文件夹。
2. 双击 manager-osx 应用程序。这将启动 XAMPP 控制面板。
3. 点击“管理服务器”按钮，通过点击其“启动”或“停止”按钮来启动或停止服务器。

### 可用于测试 Apache 服务器的 URL

http://localhost/xampp

### 描述

- XAMPP 包包括 Apache Web 服务器、MySQL 数据库服务器、PHP 解释器以及其他有助于开发 PHP 应用程序的软件。
- 在 Mac OS X 上启动 Apache 和 MySQL 后，它们在注销或重新启动计算机时可能会停止。在这种情况下，您可能需要在进行任何 PHP 开发之前重新启动 Apache 和 MySQL。

图 B-2 如何为 Mac OS X 安装 XAMPP

### 如何配置 phpMyAdmin

XAMPP 包含一个名为 phpMyAdmin 的基于 Web 的 MySQL 工具。默认情况下，phpMyAdmin 会将其配置文件（纯文本文件）中存储 MySQL root 用户的用户名和密码。由于这不安全，通常被认为是一个良好的做法来修改这些默认设置。

我们建议将 phpMyAdmin 的身份验证类型从‘config’更改为‘cookie’，如 图 B-3 所示。当您使用‘cookie’身份验证类型时，phpMyAdmin 不会在其配置文件中存储任何用户名或密码。相反，它在启动时会提示用户输入用户名和密码，并将用户名和密码存储在用户浏览器的 cookie 中。

修改 phpMyAdmin 的配置文件后，您可以使用本图中的第二个流程来确保 MySQL 服务器正常工作并确保 phpMyAdmin 配置正确。
