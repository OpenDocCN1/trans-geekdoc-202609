

PHP 组使用次要版本号用于包含安全增强或错误修复的更新。次要版本发布没有固定的发布计划；当增强功能或修复程序添加到代码中并经过彻底测试后，PHP 组会发布带有新次要版本号的新版本。

在您购买本书时，次要版本号可能已发生变化，达到 5.2.6 或更高。如果是这样，您应阅读 http://www.php.net/ChangeLog-5.php 中的更改列表，了解有关安装或配置过程（即本章主要内容）的任何变更。

尽管次要版本更新之间不太可能更改任何安装说明，但您应养成始终检查所安装和维护的软件的变更日志的习惯。如果在阅读本书时发生了次要版本变更，但变更日志未注明安装变更，只需在脑海中记住，并在安装说明及配套图中出现的位置替换为新版本号即可。

## 在 Mac OS X 上安装 PHP

在 Mac OS X 上将 PHP 与 Apache 一起安装有多种不同选项，包括如前一节所述从源代码构建。但最简单的方法是从预编译二进制包安装 PHP，例如此处列出的（参考 PHP 手册）：

- Entropy—http://www.entropy.ch/software/macosx/php/
- Fink—http://www.finkproject.org/
- MacPorts—http://www.macports.org/

> **注意**：如果您希望从源代码构建 PHP，并且熟悉 Mac OS X 操作系统和终端使用，可随时参考 PHP 手册中的说明，网址为 http://www.php.net/manual/en/install.macosx.php。

Entropy 和开发者 Marc Liyanage 的软件包功能完整、维护良好且文档齐全。

要获取 PHP 安装包，请访问 http://www.entropy.ch/software/macosx/php/ 并查找标题为“安装说明”的部分。到达该页面后，按照链接下载适用于您 Mac OS X 版本的 PHP 5。此 PHP 版本可能会比当前的 Linux/UNIX 构建文件或 Windows 安装程序落后几个版本。

下载完成后，挂载磁盘映像并双击 `*.pkg` 文件。执行以下安装步骤以完成过程：

- 1. PHP 安装程序会自动启动，如图 4.1 所示。单击“继续”进入下一步。

![](img/be3c5789b9e58d6dc55dc804718f15b4_66_0.png)

图 4.1 Mac PHP 安装程序已启动。

- 2. 下一屏幕要求您选择目标位置。选择驱动器，如图 4.2 所示，然后单击“继续”。

![](img/be3c5789b9e58d6dc55dc804718f15b4_67_0.png)

图 4.2 选择安装位置。

- 3. 系统将提示您输入管理用户名和密码，除非您以 root 身份进行安装。如果是，请输入这些值并单击“继续”按钮。

- 4. 安装过程将继续，安装 PHP 并优化系统。过程完成后，安装程序将显示完成消息，如图 4.3 所示。

![](img/be3c5789b9e58d6dc55dc804718f15b4_67_1.png)

图 4.3 PHP 安装已完成！

PHP 安装程序已对您的 Apache 配置进行了所有必要更改，因此您无需做其他事情，只需跳至“测试您的安装”部分即可。

## 在 Windows 上安装 PHP

在 Windows 上安装 PHP 只需下载发行版文件即可。要下载 PHP 发行版文件，请访问 PHP 主页 http://www.php.net/，并按照链接进入下载部分。从 Windows 二进制文件部分获取 zip 包的最新版本（不是安装程序）— 在此示例中，我们使用 5.2.5。您的发行版名称将类似于 php-VERSION.zip，其中 VERSION 是最新的发布版本号。

> **注意**：您可能会问，“为什么不用安装程序？”答案很简单：在自动设置各种文件、扩展和配置时存在相当多的限制。这些限制会导致您花费更多精力去“修复”安装，而不是最初就手动安装。这种情况，加上作者认为如果您打算使用某项技术，就应该了解其工作原理，以及 PHP 组自身建议“使用安装程序不是安装 PHP 的首选方法”，共同促成了本章中您将看到的说明。

文件下载到您的系统后，双击它以启动解压缩软件。该发行版已使用相对路径打包，因此请将文件解压缩到名为 `C:\php\` 的新目录中，所有文件和子目录都将放置在该新目录下。

从此点开始，只需执行两个基本步骤：

- 1. 将您的 PHP 目录添加到 Windows PATH。如果您不知道如何操作，请参阅 PHP 手册中 http://www.php.net/manual/en/faq.installation.php#faq.installation.addtopath 的相应常见问题解答。
- 2. 在 PHP 安装目录中，将 php.ini-recommended 文件复制为 php.ini。要使 PHP 的基本版本与 Apache 配合工作，您需要对 Apache 配置文件进行一些小修改。

### 将 PHP 与 Windows 上的 Apache 集成

要确保 PHP 和 Apache 能够协同工作，您需要向 httpd.conf 配置文件添加一些项目。首先，找到如下所示的部分：

```
# Example:
# LoadModule foo_module modules/mod_foo.so
#
LoadModule access_module modules/mod_access.so
...
#LoadModule ssl_module modules/mod_ssl.so
```

在本节末尾，添加以下内容：

```
LoadModule php5_module C:/php/php5apache2_2.dll
```

此外，添加以下内容以确保 Apache 知道 php.ini 的位置：

```
PHPIniDir "C:/php/"
```

接下来，查找以下部分：

```
#
# AddType allows you to add to or override the MIME
# configuration
# file mime.types for specific file types.
#
```

> **注意：** 如果您在让 Apache 读取正确的 php.ini 文件时遇到困难，请查看 PHP 手册中的“运行时配置”条目，该条目提供了搜索 php.ini 的位置列表，网址为 http://www.php.net/manual/en/configuration.php。

添加以下行：

```
AddType application/x-httpd-php .php .html
```

此语句可确保 PHP 引擎解析以 .php 和 .html 扩展名结尾的文件。您的文件名选择可能不同。

保存 httpd.conf 文件，然后重启 Apache。服务器应无警告地启动；PHP 现在已成为 Apache Web 服务器的一部分。

## php.ini 基础知识

在编译或安装 PHP 后，您仍可通过 php.ini 文件更改其行为。在 Linux/UNIX 系统上，此文件的默认位置是 /usr/local/php/lib，或是配置时使用的 PHP 安装位置的 lib 子目录。在 Windows 系统上，此文件应位于 PHP 目录中，或 Apache httpd.conf 文件中 PHPIniDir 值所指定的其他目录中。

php.ini 文件中的指令有两种形式：值和标志。值指令采用指令名称和用等号分隔的值的形式。可能的值因指令而异。标志指令采用指令名称和用等号分隔的正面或负面术语的形式。正面术语包括 1、On、Yes 和 True。负面术语包括 0、Off、No 和 False。空格会被忽略。

您可以随时更改 php.ini 设置，但更改后，需要重启服务器才能使更改生效。找个时间自行通读 php.ini 文件，了解可以配置的内容类型。

## 测试您的安装

测试 PHP 安装的最简单方法是创建一个使用 phpinfo() 函数的小型测试脚本。该函数将生成一长串配置信息。打开文本编辑器，键入以下行：

```
<?php phpinfo(); ?>
```

将此文件另存为 phpinfo.php，并将其放置在 Web 服务器的文档根目录中—即您 Apache 安装的 htdocs 子目录或 Mac OS X 上的 /Library/WebServer/Documents 目录。使用 Web 浏览器访问此文件，您应该会看到类似图 4.4 所示的内容。

