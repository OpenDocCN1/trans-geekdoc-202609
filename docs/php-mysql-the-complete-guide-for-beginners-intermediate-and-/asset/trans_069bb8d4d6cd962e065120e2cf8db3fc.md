

对 PHP 手册的修改需要由拥有 Doc Karma 的 PHP 文档组成员批准。Doc Karma 有点像声望，但更难获得。这种同行评审流程确保只有事实正确的信息才能进入 PHP 手册。

PHP 手册是用 DocBook 编写的，这是一种易于学习的、用于撰写书籍的标记语言。乍一看可能有点复杂，但有模板可以帮你入门。你肯定不需要成为 DocBook 专家就能做出贡献。

## 第 104.2 节：为手册做贡献的技巧

以下是为那些希望为 PHP 手册做贡献的人提供的技巧列表：

遵循手册的风格指南。确保始终遵循[手册的风格指南](http://doc.php.net/tutorial/style.php)，以保持一致性。

执行拼写和语法检查。确保使用正确的拼写和语法——否则所呈现的信息可能更难以吸收，且内容看起来会不够专业。

解释要简练。避免啰嗦，以便清晰简洁地向希望快速查阅的开发者呈现信息。

将代码与其输出分开。这能为开发者提供更整洁、不那么繁杂的代码示例以供理解。

检查页面章节顺序。确保被编辑的手册页面的所有章节都按正确的顺序排列。手册的统一性使其更易于快速阅读和查找信息。

移除 PHP 4 相关内容。考虑到 PHP 4 现在已经非常古老，具体提及 PHP 4 的内容已不再相关。应从手册中移除对它的提及，以防止用不必要的信息使手册变得繁杂。

正确设置文件版本。在文档中创建新文件时，确保文件的修订 ID 设置为空，如下所示：

```
<!-- $Revision$ -->
```

将有用的评论合并到手册中。一些评论贡献了手册可受益的有用信息。这些应被合并到主页面的内容中。

不要破坏文档构建。在提交更改前，始终确保 PHP 手册能正确构建。

# 第 105 章：为 PHP 核心做贡献

## 第 105.1 节：设置基本开发环境

PHP 的源代码托管在 [GitHub](https://github.com/php/php-src) 上。要从源代码构建，你首先需要检出一份工作副本。

如果你想添加功能，最好创建你自己的分支。

最后，配置并构建 PHP。

如果因缺少依赖项而导致配置失败，你将需要使用操作系统的包管理系统来安装它们（例如 `yum`、`apt` 等），或者下载并从源代码编译它们。

# 附录 A：在 Windows 上安装 PHP 环境

## 第 A.1 节：下载、安装和使用 WAMP

WampServer 是一个 Windows Web 开发环境。它允许你使用 Apache2、PHP 和 MySQL 数据库创建 Web 应用程序。此外，PhpMyAdmin 允许你轻松管理数据库。

WampServer 有两个不同的版本可免费获得（基于 GPML 许可证）：32 位和 64 位。WampServer 2.5 与 Windows XP 不兼容，无论是否带 SP3，也不兼容 Windows Server 2003。旧版本的 WampServer 可在 [SourceForge](https://sourceforge.net/projects/wampserver/files/) 上找到。

WampServer 版本：

*   [WampServer (64 位) 3](https://sourceforge.net/projects/wampserver/files/WampServer%203/WampServer%203.0.0/wampserver3.0.4_x64_apache2.4.18_mysql5.7.11_php5.6.19-7.0.4.exe/download)
*   [WampServer (32 位) 3](https://sourceforge.net/projects/wampserver/files/WampServer%203/WampServer%203.0.0/wampserver3.0.4_x86_apache2.4.18_mysql5.7.11_php5.6.19-7.0.4.exe/download)

当前提供：

*   Apache: 2.4.18
*   MySQL: 5.7.11
*   PHP: 5.6.19 & 7.0.4

安装很简单，只需运行安装程序，选择位置并完成即可。

完成后，你可以启动 WampServer。然后它会在系统托盘（任务栏）中启动，最初为红色，服务器启动后变为绿色。

你可以打开浏览器并输入 `localhost` 或 `127.0.0.1` 以获取 WAMP 的索引页面。从现在起，你可以通过将文件存储在 `PATH_TO_WAMP/www/<php_or_html_file>` 中，并在 `http://localhost/<php_or_html_file_name>` 上查看结果，在本地处理 PHP 文件。

## 第 A.2 节：安装 PHP 并配合 IIS 使用

首先，你需要在机器上安装并运行 IIS（Internet Information Services）；IIS 默认不可用，你必须从控制面板 -> 程序 -> Windows 功能 中添加该特性。

1.  从 [http://windows.php.net/download/](http://windows.php.net/download/) 下载你喜欢的 PHP 版本，并确保下载 PHP 的非线程安全（NTS）版本。
2.  将文件解压到 `C:\PHP\`。
3.  打开 Internet Information Services (IIS) 管理器。
4.  在左侧面板中选择根项目。
5.  双击“处理程序映射”。
6.  在右侧面板点击“添加模块映射”。
7.  按如下方式设置值：
    *   安装 `vcredist_x64.exe` 或 `vcredist_x86.exe`（Visual C++ 2012 可再发行组件），从 [https://www.microsoft.com/en-US/download/details.aspx?id=30679](https://www.microsoft.com/en-US/download/details.aspx?id=30679)
8.  设置你的 `C:\PHP\php.ini`，特别是设置 `extension_dir = "C:\PHP\ext"`。
9.  重置 IIS：在 DOS 命令控制台中输入 `IISRESET`。

你也可以选择安装 [PHP Manager for IIS](https://phpmanager.codeplex.com/)，它对设置 ini 文件和跟踪错误日志很有帮助（在 Windows 10 上不工作）。

记得将 `index.php` 设置为 IIS 的默认文档之一。

如果你遵循了安装指南，现在你已经准备好测试 PHP 了。

就像 Linux 一样，IIS 在服务器上有一个目录结构，这棵树的根目录是 `C:\inetpub\wwwroot\`，这是所有公共文件和 PHP 脚本的入口点。

现在使用你喜欢的编辑器，或者只是 Windows 记事本，输入以下内容：

```
<?php phpinfo(); ?>
```

将文件以 UTF-8 格式（无 BOM）保存到 `C:\inetpub\wwwroot\index.php`。

然后在浏览器中使用此地址打开你全新的网站：[http://localhost/index.php](http://localhost/index.php)

## 第 A.3 节：下载并安装 XAMPP

什么是 XAMPP？

XAMPP 是最流行的 PHP 开发环境。XAMPP 是一个完全免费、开源且易于安装的 Apache 发行版，包含 MariaDB、PHP 和 Perl。

我应该从哪里下载？

从[他们的下载页面](http://www.apachefriends.org/download.html)下载合适的稳定 XAMPP 版本。根据操作系统类型（32 位或 64 位及操作系统版本）以及它必须支持的 PHP 版本选择下载。

当前最新版本为 [XAMPP for Windows 7.0.8 / PHP 7.0.8](http://www.apachefriends.org/xampp-files/7.0.8/xampp-win32-7.0.8-0-VC14-installer.exe)。

或者你可以遵循以下方式：

XAMPP for Windows 有三种不同的形式：

*   exe 格式
*   zip 格式
*   7zip 格式

*   [安装程序](https://sourceforge.net/projects/xampp/files/XAMPP%20Windows/7.0.8/xampp-portable-win32-7.0.8-0-VC14-installer.exe/download)（可能是安装 XAMPP 最简单的方法）
*   [ZIP](https://sourceforge.net/projects/xampp/files/XAMPP%20Windows/7.0.8/xampp-portable-win32-7.0.8-0-VC14.zip/download)（给纯粹主义者：作为普通 ZIP 归档的 XAMPP）

