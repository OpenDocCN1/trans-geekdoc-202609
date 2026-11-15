
- 添加 PHP 目录——例如，C:\php。
- 为 php.ini 创建一个新的系统变量。该变量必须适用于带有用户管理的 Windows 操作系统，而不仅仅是当前用户。
- 环境变量名为 PHPRC，目录为 php.ini 所在的目录——例如，C:\php（见图 2.4）。
- 最后，保存或确认更改并重启操作系统。

![](img/ae7820c36e8f24c1623d26668b28e80e_50_0.png)

图 2.4 添加其他路径以确保找到 PHP 模块

现在通过 inetmgr.exe 启动 IIS 管理控制台。

- 7. 单击“处理程序映射”。
- 8. 然后在右侧选择“添加模块映射”。
- 9. 在图 2.5 所示的对话框中，将“*.php”——或要与 PHP 关联的其他文件扩展名——作为请求路径输入。

![](img/ae7820c36e8f24c1623d26668b28e80e_50_1.png)

图 2.5 作为 CGI 的 PHP 设置

- 10. 将 **FastCgiModule** 选为 **模块**。

- 11. 可执行文件是 *php-cgi.exe* CGI 文件。

- 12. 将以下配置设置添加到 *php.ini*（并替换任何现有且不同的设置）。最后一项设置尤其重要，否则默认值 1 会阻止直接调用 PHP CGI 模块，导致 IIS 出现错误：

```
fastcgi.impersonate = 1
fastcgi.logging = 0
cgi.fix_pathinfo = 1
cgi.force_redirect = 0
```

错误的常见原因是尚未设置 CGI。您必须通过 **“启用或关闭 Windows 功能”** 下的安装来检查此项。

为此，请转到 **“应用程序开发功能”**（见图 2.6），如有疑问，请在此处安装 **CGI**。可能还需要为 CGI 角色授予应用程序开发的相应权限。

![](img/ae7820c36e8f24c1623d26668b28e80e_51_0.png)

图 2.6 安装 CGI 支持

在 <https://www.php.net/install.windows>，您可以在在线手册中找到 Windows 上 PHP 的进一步设置选项，以及有关 PHP 与 IIS 组合的信息。

## 在版本之间切换

一些开发者希望或需要在系统中同时使用不同的 PHP 版本。使用 XAMPP 等安装包可以非常轻松地快速切换。不过，手动安装时也有一些小技巧能让生活更轻松：

- 1. 为 C:\php 文件夹创建环境变量。
- 2. php.ini 也位于该文件夹中。两个 PHP 版本中的一个位于此文件夹，为另一个起个略有不同的名称，例如 C:\php8.4。
- 3. 现在更改非常简单：重命名这两个文件夹。例如，C:\php 变为 C:\php8.3。
- 4. 然后将 C:\php8.4 重命名为 C:\php。

就这么简单。相应版本的 .ini 文件始终用作 php.ini。扩展也会自动复制。这样可以轻松管理两个或更多版本。

## Apache 2.x

使用 Apache 2.x 时安装非常简单。此处可找到 PHP 8.x 和 Apache 2.4 的说明，不支持旧版 Apache。PHP 作为 SAPI 模块（也称为处理程序）安装。

- 1. 对于 Windows 二进制文件，请选择线程安全版本以及与已安装 Web 服务器匹配的 x86 或 x64 版本。不要忘记来自 [http://s-prs.co/v602260](http://s-prs.co/v602260) 的 Visual Studio 2019 的 Visual C++ Redistributable。

**注意**
如果版本不匹配，安装将在此处失败。

- 2. 将二进制文件解压到 C:\php 目录中。

- 3. 重命名提供的两个 php.ini 版本中的一个为 php.ini。

- 4. 然后在 Apache 配置文件 httpd.conf 中进行配置。在标准安装中，它位于 C:\Apache24\conf\httpd.conf。对于 SAPI 模块，内容如下：

```
LoadModule php_module "C:/php/php8apache2_4.dll"
AddType application/x-httpd-php .php
PHPIniDir "C:/php"
```

**注意**
对于其他版本，您当然应该相应调整 dll 的版本号。如果不存在名为 php8apache2_4.dll 的文件，您可能下载了面向 IIS 的非线程安全 PHP 发行版。请改为选择线程安全版本。

- 5. 然后启动 Apache，例如通过命令提示符：

```
httpd.exe -k start
```

## 测试安装

要测试安装，请切换到文本编辑器并创建一个新的 PHP 文件。将此 PHP 文件保存为 phpinfo.php 或任何其他名称，放在 Web 服务器的根目录中（对于 IIS 默认在 C:\inetpub\wwwroot 下，对于 Apache 在程序目录的 htdocs 下，例如 C:\Apache24\htdocs）。

在该文件中仅编写三行代码：

```
<?php
phpinfo();
?>
```

第一行和最后一行是 PHP 代码的分隔符，用于告诉 PHP 解释器在哪里执行操作。phpinfo() 函数实际上是关键函数。它会生成关于 PHP 安装及所有已安装扩展的自报告（见图 2.7）。

![](img/ae7820c36e8f24c1623d26668b28e80e_53_0.png)

图 2.7 PHP 8 安装的 "phpinfo()" 输出（此处为 IIS 中的 FastCGI）

要立即测试，请在 Web 服务器上调用刚刚创建的 PHP 文件。在本例中，需要地址 `http://localhost/phpinfo.php`。这样可以同时检查 PHP 的基本功能及其与 Web 服务器的集成。如果有什么无法正常工作，php.exe 的控制台输出可能会提供更多信息（见图 2.8）。以下命令显示版本号：

```
php -v
```

![](img/ae7820c36e8f24c1623d26668b28e80e_54_0.png)

图 2.8 控制台上的 PHP

**注意**
在生产系统中，带有 phpinfo() 的文件不应从外部访问，因为它包含入侵者可能利用的系统信息。

## 自行编译

要在 Windows 上自行运行 PHP，需要来自 Microsoft 的 Visual Studio。此处将介绍 PHP 8.3 的过程，它需要 Visual Studio 2019 版本。PHP 8.4 使用 Visual Studio 2022。

Microsoft 在 http://s-prs.co/v602261 提供所谓的开发环境社区版。这对大多数用户是免费的，5 编译也可以使用它。安装过程中，只需确保安装了 PHP 所需的编译器（默认情况下未安装）。选择自定义设置，并在“编程语言” • “Visual C++” • “Visual C++ 2019 的常规工具”下激活复选框。在较新版本的 Visual Studio 2019 中，您会在单独组件列表中找到所需的相应生成工具（见图 2.9）。

**注意**
早期版本的 PHP 依赖于旧版本的 Visual Studio。仅 PHP 8.0 到 8.3 需要 Visual Studio 2019。但是，过程是相似的。PHP wiki 在 http://s-prs.co/v602205 提供有关旧版本（直到包括 7.1）的更多信息。页面 http://s-prs.co/v602206 涵盖 PHP 7.2 及更高版本。

5 详细信息可在 http://s-prs.co/v602207 上找到。注意：您绝对需要适用于 Windows 的 Visual Studio，而不是 macOS 版本，也不是同名但完全不同的 Visual Studio Code。

![](img/ae7820c36e8f24c1623d26668b28e80e_55_0.png)

图 2.9 安装适用于 VC++ 的最新工具集至关重要（“单独组件”选项卡）

开发环境包含您所需的几乎所有内容。过去，您还需要安装 Windows 软件开发工具包。现在不再需要。相反，有一个特殊的 PHP SDK，它在 GitHub 上托管 PHP 项目。项目 URL 是 https://github.com/php/php-sdk-binary-tools。

PHP 的大致编译步骤如下：

- 安装 PHP SDK
- 准备目录结构
- 导入当前 PHP 源代码
- 编译

那么，让我们开始吧。如果可能，您还需要 Git 来轻松获取 PHP SDK 和 PHP 本身的源代码。如果您不想使用 Git，也可以从各自的项目页面将这些包作为 ZIP 存档获取并解压。但是，我们将在后面使用 Git 版本，并假设您的系统已相应配置。

在 Visual Studio 2019 的开始菜单文件夹中，您会找到 **“VS 2019 的开发者命令提示符”**。这将打开一个命令提示符，其中大多数所需工具的路径已正确设置。

以下命令检索 PHP SDK 的当前源代码，将其解压到 C:\php-sdk 目录，然后检索至少版本 2.2.0：

```
git clone https://github.com/php/php-sdk-binary-tools.git c:\php-sdk
```
