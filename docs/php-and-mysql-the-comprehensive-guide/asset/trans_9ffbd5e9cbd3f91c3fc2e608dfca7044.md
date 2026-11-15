

注
*php.ini* 中的设置可以在 www.php.net/manual/ini.php 找到。然而，在本书中，有一个单独章节专门介绍 *php.ini*（第 34 章）。

## 2.1.2 Windows

现成的 Windows 版 PHP 的存在是 PHP 早期成功的关键因素之一。当然，主机主要使用 Linux 和 Apache³ 作为其 Web 服务器，但大多数业余和专业开发人员仍在家用电脑上使用 Windows。与此同时，使用 XAMPP 等现成软件包进行安装是一种可靠且流行的替代方案。本章还包含手动安装说明。

3 因此有著名的 LAMP 缩写，代表 Linux、Apache、MySQL 和 PHP。

注
本书原版基于 PHP 8.3.0 最终版本。PHP 8.4.0 在制作英文版本书后期发布。我们添加了若干对 PHP 8.4.0 的引用，但重点仍放在 PHP 8.3 上。

### Web 服务器

Windows 上可以使用各种 Web 服务器。最重要的是：

- *互联网信息服务* (IIS; 参见图 2.2) 是微软提供的“专业”Web 服务器。它随大多数 Windows 版本提供。

![](img/ae7820c36e8f24c1623d26668b28e80e_46_0.png)

图 2.2 已安装 IIS

您可以在 Windows 10/11 的“打开或关闭 Windows 功能”中检查是否已安装。

如果缺少 IIS，请单击它。双击以打开更多选项。重要的是，ISAPI 和 CGI 也应在“应用程序开发功能”下安装。

- Apache for Windows 是市场领先 Web 服务器的 Windows 移植版。最新版本属于 2.x 分支。两个版本的二进制文件可在 https://httpd.apache.org 上找到，PHP 项目还正式推荐在 https://www.apachelounge.com/download 上下载。

如果已安装 Web 服务器，通常可以通过 http://localhost/ 或 http://127.0.0.1/ 在本地访问它。本书中所有 PHP 示例都位于 php 子文件夹中。其 URL 如下：

```
http://localhost/php/
```

如果为 Web 服务器使用非默认端口 80 以外的端口，还必须指定端口：

```
http://localhost:8080/php/
```

### 安装包

由于 Apache、PHP 和 MySQL（或 MariaDB）通常一起使用，一些项目提供自动安装程序。一大优点是您可以再次卸载整个安装包。但是，有些包在较新的 PHP 版本方面略有滞后，尤其是 PHP 8.3（尽管从写下这些行到您阅读它们之间可能发生了很多事情）。以下是我们认为目前最好的三个安装包：

- XAMPP 无疑是最著名的项目（https://www.apachefriends.org/index.html）。它的巨大优势在于适用于 Linux、Windows 和 macOS。安装不仅包含所有扩展，还包含可直接使用的 PEAR。4 它也会非常定期地更新。您还可以在 http://sourceforge.net/projects/xampp/files 上找到旧版本。XAMPP 的配置对生产环境并非最佳，因此主要用作本地开发平台。不过，该项目尚未针对 PHP 8.3 进行更新（参见图 2.3）。顺便说一句，XAMPP 安装的是 MariaDB 而不是 MySQL，这最初没有显著的功能影响。

- EasyPHP Devserver（www.easyphp.org）既可用于开发也可用于生产环境。使用此包，PHP 版本非常容易配置，还可以安装附加包。（出版时，当前版本 17.0 中仅包含 PHP 7；不过，PHP 8.3 可作为附加组件进行安装。）

- 最初源自法国的 WampServer 项目（https://www.wampserver.com/en）也颇为知名。（出版时，已支持 PHP 8.3。）

4 有关详细信息，请参阅第  节。

![](img/ae7820c36e8f24c1623d26668b28e80e_48_0.png)

图 2.3 XAMPP 尚未支持 PHP 8.3（写作时）

> **注**
> 
> 例如，如果 IIS（或其他 Web 服务器）已经在端口 80 上运行，并且您使用的自动安装程序也将 Apache 设置为端口 80，则可能会出现问题。在这种情况下，必须停止其他 Web 服务器或将 Apache 设置为不同的端口。对于 Apache，这是在 `httpd.conf` 配置文件中完成的，该文件位于 `conf` 文件夹中。

### 手动安装

现在我们来讨论手动安装。但是，本节解释的基本原理和程序也适用于您希望使用包对安装进行更改的情况。此处按 Web 服务器进行细分。

对于生产系统——即连接到互联网并在此执行工作的 Web 服务器——在 90% 的情况下，手动安装是唯一合适的方法。处理 `php.ini` 中的配置设置时需要格外小心。大多数安装程序或安装包以 `php.ini` 中过于宽松的设置开始，这些设置不适合生产系统。

以下安装说明基于尚未安装 PHP 的系统。此处展示的变体基于 PHP 在线文档中的新说明，因为这提供了最佳且最快的可更新性。PHP 仅集中保存在一个文件夹中，而在之前的安装中，php.ini 文件总是最终位于 Windows 目录中，其他扩展必须也复制到那里，或者（不推荐）复制到 System32。

> **注**
> 对于 IIS，CGI 变体推荐使用 PHP 的非线程安全 (NTS) 版本。通常，出于性能原因，几乎专用于 FastCGI 版本。

要安装 PHP，请执行以下步骤：

- 1. 下载包含 PHP 8.3 Windows 二进制文件的 ZIP 文件。Windows 下载页面位于 [Windows 下载页面](http://windows.php.net/download)。必须使用非线程安全版本，并决定其应在 x86 还是 x64 系统上运行。您还需要 Visual C++ Redistributable for Visual Studio 2019 包（针对 PHP 8.4 则为 Visual C++ Redistributable for Visual Studio 2022）才能运行 PHP——这一点在下载页面有一个小而易被忽略的注释中注明。您可以在 [Visual C++ Redistributable](http://s-prs.co/v602204) 上找到它，在此处必须选择也要安装 PHP 的处理器架构（32 位或 64 位）。
- 2. 为 PHP 创建一个新文件夹。此处假设的默认路径为 C:\\php。
- 3. 将 ZIP 文件的内容解压到此文件夹中。注意：ZIP 不再自动包含 php 文件夹！这就是我们在上一步中创建它的原因。
- 4. 下面是简要清单：PHP 的 CGI 版本称为 php-cgi.exe，而非 php.exe。后者 php.exe 是控制台版本，默认已位于 PHP 主文件夹中。SAPI 文件是 php8.dll。不过，如前所述，它不再推荐用于 IIS。如前所述，php.ini 文件仅在标准包中以两个模板形式提供：php.ini-development 和 php.ini-production。前者更多用于测试系统，后者用于生产系统。不过，您通常需要自行修改。
- 5. 将提供的两个 php.ini 模板文件之一重命名为 php.ini。
- 6. 在下一步中，应让 Windows 明确 php-cgi.exe PHP 模块和 php.ini 位于主 PHP 目录中（此处：C:\\php）。虽然这并非绝对必要，但通常能简化控制，尤其是在与扩展配合使用时。此步骤需要设置一个新环境变量：
  - 通过“控制面板” • “系统” • “系统和安全” • “高级系统设置”切换到环境变量。
  - 在“环境变量” • “系统变量”下编辑 Path 条目。

