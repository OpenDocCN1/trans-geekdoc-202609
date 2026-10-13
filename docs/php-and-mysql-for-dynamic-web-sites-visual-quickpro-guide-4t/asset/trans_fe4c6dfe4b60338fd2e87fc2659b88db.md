
保存 **`php.ini`** 文件并重启 Web 服务器。如果重启过程提示找不到扩展的错误，请再次检查以确保扩展存在于 `extension_dir` 中，并且路径名正确。如果问题仍然存在，请在网上搜索或使用本书对应的论坛寻求帮助。

---

### 修改 PHP 的配置

**1.** 在 Web 浏览器中，执行一个调用 **`phpinfo()`** 函数的脚本。

**`phpinfo()`** 函数（在附录前一节中讨论过，参见 ![Image](graphics/graycircle-a.jpg)）会显示大量关于 PHP 安装的信息。

**2.** 在浏览器的输出中，搜索 `Loaded Configuration File` ![Image](graphics/circle-a.jpg)。

![Image](graphics/20_figure_21_a.jpg)

![Image](graphics/circle-a.jpg) 使用 `phpinfo()` 脚本来确认要编辑的活动 PHP 配置文件。

此文本旁边的值即为活动配置文件的位置。这将类似于 **`C:\xampp\php\php.ini`** 或 **`/Applications/MAMP/conf/php5.3/php.ini`**。您的服务器上可能有多个 **`php.ini`** 文件，但这个才是生效的那个。

如果 `Loaded Configuration File` 没有值，说明您的服务器没有活动的 **`php.ini`** 文件。在这种情况下，您需要从 **[www.php.net](http://www.php.net)** 下载 PHP 源代码，以找到一个示例配置文件。

**3.** 用任意文本编辑器打开 **`php.ini`** 文件。

如果您进入列出的目录却找不到 **`php.ini`** 文件，则需要从 PHP 网站下载该文件（它是 PHP 源代码的一部分）。

**4.** 进行您想要的任何更改，请记住以下几点：

- 注释以分号标记。分号之后的任何内容都会被忽略。
- 文件中包含了关于大多数设置含义的说明。
- 文件顶部列出了带有示例的一般信息。**请勿更改这些值！** 请在文件后面出现设置的地方进行更改。
- 为了安全起见，请勿更改任何原始设置。只需将它们注释掉（在行首加上分号），然后在之后添加新的修改后的行。
- 添加注释（使用分号）以标记您所做的更改及时间。例如：

```
; display_errors = Off
; Next line added by LEU
08/28/2011
display_errors = On
```

---

**启用邮件功能**

PHP **`mail()`** 函数仅在运行 PHP 的计算机可以访问 sendmail 或其他邮件服务器时才能工作。启用 **`mail()`** 函数的一种方法是在 **`php.ini`** 文件中设置 **`smtp`** 值（仅限 Windows）。例如，如果您的互联网服务提供商有一个可用的 SMTP 地址，这种方法就有效。遗憾的是，如果您 ISP 的 SMTP 服务器需要身份验证，则无法使用此值。

对于 Windows，也有许多免费的 SMTP 服务器，如 Mercury。它随 XAMPP 一起安装，如果您不使用 XAMPP，也可以自行安装。

Mac OS X 自带已安装的邮件服务器——postfix 和/或 sendmail——需要启用。请在 Google 上搜索关于在 Mac OS X 上手动启用邮件服务器的说明。

或者，您可以搜索一些 PHP 代码库，了解如何使用需要身份验证的 SMTP 服务器。

---

**5.** 保存 **`php.ini`** 文件。

**6.** 重启您的 Web 服务器。

您不必重启整台计算机，只需重启 Web 服务应用程序（Apache、IIS 等）。具体操作取决于所用的应用程序、操作系统和安装方法。Windows 用户可以使用 XAMPP 控制面板。Mac OS X 用户可以使用 MAMP 控制面板。Unix 用户通常只需在终端窗口中输入 **`apachectl graceful`** 即可。

**7.** 重新运行 **`phpinfo.php`** 脚本，以确保更改生效。

---

> **Tip**
>
> 如果您编辑了 **`php.ini`** 文件并重启了 Web 服务器，但更改未生效，请确保您编辑的是正确的 **`php.ini`** 文件（您的计算机上可能不止一个）。

---

> **Tip**
>
> Mac OS X 上的 MAMP PRO 使用 **`php.ini`** 文件的模板，必须在 MAMP PRO 本身中进行编辑。要在使用 MAMP PRO 时更改 PHP 设置，请选择“文件”>“编辑模板”>“PHP ***X***.***X***.***X*** php.ini”。

---

## 配置 Apache

本书的新版新增了本节，介绍如何配置 Apache Web 服务器。与 PHP 一样，Apache 是一项开源技术，已成为 Web 技术中的主导力量。如果您在计算机上安装了 XAMPP 或 MAMP，您现在就拥有一个功能齐全的 Apache 版本。如果您使用的是托管网站，极有可能那里也提供了 Apache。

一旦安装了支持 PHP 的 Apache，许多 PHP 程序员就再不会考虑 Web 服务器的事了。但随着您继续学习 Web 开发，掌握更多 Apache 知识是合乎逻辑的下一步。

您需要进一步了解 Apache 的最常见原因包括能够执行以下操作：

- 创建虚拟主机
- 添加安全套接字层 (SSL) 支持
- 保护目录
- 启用 URL 重写

这些以及其他对 Apache 行为的更改，可以通过两种方式实现：编辑主配置文件或创建特定目录的文件。主配置文件是 **`httpd.conf`**，位于 **`conf`** 目录中，它决定了整个 Apache Web 服务器如何运行。**`.htaccess`** 文件（读作 “H-T access”）放置在 Web 目录中，用于仅影响 Apache 在该文件夹及子文件夹中的行为。

一般来说，首选在 **`httpd.conf`** 文件中进行更改，因为该文件仅在服务器每次启动时需要被 Web 服务器读取一次。相反，**.htaccess** 文件必须针对每个可能适用 **`.htaccess`** 文件的请求，被 Web 服务器读取一次。例如，如果您有 **[www.example.com/somedir/.htaccess](http://www.example.com/somedir/.htaccess)**，对 **`www.example.com/somedir/`*`whatever`*** 的任何请求都需要读取 **`.htaccess`** 文件，以及读取可能存在于 **[www.example.com/](http://www.example.com/)** 中的 **`.htaccess`** 文件。另一方面，在共享托管环境中，不允许个人用户自定义整个 Apache 配置，但可能允许使用 **`.htaccess`** 进行仅影响其自身站点的更改。

在接下来的几页中，我将解释使用这两种文件类型的一些基础知识。在此过程中，您将学习如何执行一些标准的 Apache 自定义。

---

> **Tip**
>
> 为了安全起见，建议在进行后续任何编辑之前，先备份原始的 Apache 配置文件。

---

> **Tip**
>
> 在本书中，我无法充分解释如何启用 HTTPS（基于 SSL 的 HTTP），因为关键组件——获取和安装 SSL 证书——因人而异，因服务器而异，差异太大。请在网上查找具体细节，或在我的支持论坛（**[www.LarryUllman.com/forums/](http://www.LarryUllman.com/forums/)**）发帖求助。如果您有一个想要启用 SSL 的托管账户，请咨询您的托管公司。

---

### 创建虚拟主机

当您在计算机上安装 Apache 时，Apache 被设置为服务于一个网站，例如 **[www.example.com](http://www.example.com)**。对于所服务的网站，Apache 将主机名（和/或 IP 地址）与服务器上的一个目录关联起来，称为 *Web 文档根目录*。当用户访问 **[www.example.com](http://www.example.com)** 时，Apache 会从该站点的目录提供文件 ![Image](graphics/circle-a.jpg)。

![Image](graphics/20_figure_22_a.jpg)

![Image](graphics/circle-a.jpg) Web 服务器将 URL 或主机名与计算机上的目录或文件关联起来。
