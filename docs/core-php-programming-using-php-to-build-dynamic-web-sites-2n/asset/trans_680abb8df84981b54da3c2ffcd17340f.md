

# PHP 核心编程

./configure -prefix=/www

该脚本将检查您的系统并为 Apache 准备一个 Makefile。`-prefix` 指令将在文件系统的根目录下创建一个目录。

接下来，配置并编译 PHP：

```
./configure -with-apache=/usr/local/src/apache_1.3.9-enable-track-vars
make
make install
```

这在 PHP 目录内完成。`-with-apache` 和 `-enable-track-vars` 选项是可选。如果您安装了 MySQL 数据库，可以添加 `-with-mysql`。PHP 通常可以独立使用 MySQL 库。附录 E“编译配置”列出了所有的 `configure` 指令。运行 `make` 将创建 PHP 库，运行 `make install` 将准备 Apache 以包含 PHP 模块。注意，`configure` 中包含了指向 Apache 源码目录的路径。这可以是相对路径，因为您可以将 Apache 源码与 PHP 源码并列放置。然而，不要在任何其他指令上误用相对路径。

接下来，您将需要重新配置 Apache 并运行 `make`。返回 Apache 源码目录并再次运行 `configure`，这次使用一个告诉 Apache 包含 PHP 模块的选项：

```
./configure -prefix=/www -activate-module=src/modules/php4/libphp4.a
make
make install
```

这将创建一个 Makefile 并运行它。新的 http 二进制文件将安装在 `/www/bin` 目录，或者您指定的任何文件安装位置。

为了提供额外的配置选项，PHP 使用了一个名为 `php.ini` 的文件。该文件应该位于 `/usr/local/lib`，因此请从 PHP 源码目录拷贝它：

```
cp php.ini-dist /usr/local/lib/php.ini
```

您可能不需要编辑此文件，但如果确实需要，里面有指导性的注释。文件中的注释解释了每个配置指令的作用。

# PHP 核心编程

最后一步是将文件扩展名与 PHP 相关。这是通过编辑 `httpd.conf` 文件实现的。它可以在 Apache 的 `conf` 目录下找到，例如 `/www/conf/httpd.conf`。添加以下行：

```
AddType application/x-httpd-php .php
```

这会导致所有扩展名为 `.php` 的文件作为 PHP 脚本执行。您可以选择另一个，例如 `phiml`。您可能还希望插入 `index.php` 作为默认文档。当 Apache 服务器启动时，它将处理 PHP 脚本。Apache 的文档提供了自动启动 Apache 的提示。如果您之前一直在运行 Apache，您将需要重启它，而不仅仅是使用 `kill -HUP` 命令。

# Windows NT 的 IIS 安装

第一步是安装 PHP。网站上提供了二进制发行版。下载 zip 包并将其解压到您希望的任何位置。将其放在 `c:\php4`。接下来，将 `php.ini-dist` 拷贝到您的系统根目录，即 `c:\windows`。将它重命名为 `php.ini`。当 PHP 被调用时，它会在该目录中查找 `php.ini`。虽然您可能不需要，但您可能想编辑它来更改配置参数，包括加载扩展。文件中的注释解释了每个配置指令的作用。

下一步是确保 DLL 文件在您的路径（path）中。一种方法是将所需文件拷贝到您的系统目录，例如 `c:\windows\system32`。或者，您可以点击控制面板中的系统图标，并将 PHP 添加到系统路径中。

您需要告诉 IIS 以特定扩展名（如 `.php`）结尾的文件应该用 PHP 处理。IIS 将此称为 ISAPI 过滤器。打开允许您配置 IIS 所有层面的管理控制台。编辑 Web 服务器的选项卡之一允许您添加 PHP 并指向 `php4isapi.dll` 文件，该文件应该与您通过 PHP 安装的其他文件放在一起。此文件很小，但它从另一个库 `php4ts.dll` 加载 PHP 核心。

现在您已经添加了该文件，需要将其与扩展名相关联。在属性对话框中查找主目录配置按钮。在应用程序映射（application mappings）列表中添加新条目。选择 `.php` 作为扩展名，再次找到您的 `php4isapi.dll` 文件。留标记为“方法排除”（method exclusions）的框，并勾选脚本引擎复选框。

最后一步是重启 Web 服务器。从管理控制台停止它是不够的。您必须通过命令行使用 `net stop w3svc` 或通过服务控制面板停止该服务。停止后，重启它。

# PHP 核心编程

# 编辑脚本

PHP 脚本只是文本文件，您可以像处理 HTML 文件一样编辑和创建它们。当然，您可以 telnet 到您的 Web 服务器并使用 vi 开始创建文件。或者，您可以使用记事本创建文件并通过 ftp 逐个上传。但这些并不是理想的体验。较新编辑器的一个特性是内置 FTP。这些编辑器可以打开远程服务器上的文件，就像它们在本地驱动器上一样。单击即可将其保存回远程服务器。另一个您可能喜欢的特性是语法高亮。这会让 PHP 关键字着色，以帮助您更快地阅读代码。

每个人都有喜爱的 PHP 脚本编辑器。我使用 UltraEdit <http://www.ultraedit.com/>。我知道许多 Windows 用户偏好使用 Macromedia 的 Dreamweaver <http://www.macromedia.com/software/dreamweaver/> 和 Allaire 的 HomeSite <http://www.allaire.com/products/homesite/> 来编辑 PHP 脚本。Systems 提供了一个名为 PhpWeave 的免费包，它允许自动编辑 PHP 脚本 <http://phpweave.quad-sys.com/>。我认识的 Macintosh 用户偏好使用 BbEdit <http://www.barebones.com/products/bbedit/>。在 Unix 系统上，您可能偏好使用 vi 或 nedit。

# PHP 脚本的样子

PHP 脚本只是文本文件，您可以像处理 HTML 文件一样编辑和创建它们。当然，您可以 telnet 到您的 Web 服务器并使用 vi 开始创建文件。或者，您可以使用记事本创建文件并通过 ftp 逐个上传。但这些并不是理想的体验。较新编辑器的一个特性是内置 FTP。这些编辑器可以打开远程服务器上的文件，就像它们在本地驱动器上一样。单击即可将其保存回远程服务器。另一个您可能喜欢的特性是语法高亮。这会让 PHP 关键字着色，以帮助您更快地阅读代码。

每个人都有喜爱的 PHP 脚本编辑器。我使用 UltraEdit <http://www.ultraedit.com/>。我知道许多 Windows 用户偏好使用 Macromedia 的 Dreamweaver <http://www.macromedia.com/software/dreamweaver/> 和 Allaire 的 HomeSite <http://www.allaire.com/products/homesite/> 来编辑 PHP 脚本。Systems 提供了一个名为 PhpWeave 的免费包，它允许自动编辑 PHP 脚本 <http://phpweave.quad-sys.com/>。我认识的 Macintosh 用户偏好使用 BbEdit <http://www.barebones.com/products/bbedit/>。在 Unix 系统上，您可能偏好使用 vi 或 nedit。

# PHP 脚本的样式

PHP 表现为 HTML 文件内部的标签。像所有 HTML 标签一样，它以小于符号（或左括号 <）开始，以大于符号（或右括号 >）结束。为了与其他标签区分，PHP 标签在左括号后、右括号前有一个问号 (?)。PHP 标签之外的所有文本将直接传递给浏览器。标签内的文本预期为 PHP 代码并会被解析。

为了适应 XML 和一些挑剔的编辑器（如微软的 Front Page），PHP 提供了其他三种标记代码的方法。在开启标签后放置 php 编写 JavaScript 一样。或者，您可以使用 script 标签就像使用 ASP 一样，使用 <% 开始代码块。附录 D 解释了这些替代方案如何工作。我在所有的示例中都使用简单的 < 和 ? 方法。

+   Listing 1.1 显示了一个普通的 HTML 页面，但有一个不同之处：位于 <?php ... ?> 之间的 PHP 代码。当此页面通过 PHP 模块时，它将把 PHP 代码替换为今天的日期。它读起来可能像：1999 年 5 月 1 日，星期五。

#  1.1 输出今天的日期

