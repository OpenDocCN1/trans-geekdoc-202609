

出版时这是最新的非测试版本（我们后面将使用开发状态 2.2.1-dev）。在你阅读本章时，很有可能已经有更新的版本可用。只需查看 PHP SDK GitHub 页面上的 Releases 选项卡即可。特定选择某个版本（例如 `git checkout php-sdk-2.2.0`）的优势在于，你实际使用的是作为 "release" 发布的版本，而不是当前快照。

接下来，切换到 C:\php-sdk 文件夹并为编译准备文件系统（参见图 2.10）。接下来我们将使用 64 位版本；如果要将 PHP 作为 32 位应用程序使用，请将 x64 替换为 x86：

```
cd c:\php-sdk phpsdk-vs16-x64.bat
phpsdk_buildtree.bat phpmaster
```

不要惊讶：第二个批处理脚本位于 bin 子文件夹中，但可以从 C:\php-sdk 调用，因为第一个批处理脚本会相应地调整当前控制台窗口中的 PATH 环境变量。

![](img/ae7820c36e8f24c1623d26668b28e80e_56_0.png)

图 2.10 帮助脚本准备系统

接下来，我们需要 PHP 本身的源代码。你可以从项目的 Git 仓库克隆它（我们后面将这样做），也可以从 http://php.net/downloads.php 下载相应的归档文件，并将其解压到 C:\php-sdk\phpmaster\vs16\x64\php-src 文件夹：

```
git clone https://github.com/php/php-src.git
```

（如果需要，如果你需要 32 位版本，请再次将 x64 替换为 x86。）

我们还没有达到目标，因为仍然缺少所有必需的库。它们曾经可以作为 7z 归档文件在 PHP 网站上下载，但如今获取所需内容更加方便：`phpsdk_deps.bat` 脚本会自动获取所需的包。在存放源代码的文件夹中调用它。我们使用 PHP 的 `master` 分支，但你也可以指定任何其他 `branch`；6

```
cd php-src
phpsdk_deps.bat --update --branch master
```

这些下载和复制步骤相当多。但多亏了现成的批处理文件，一切应该都能无误运行。现在是时候开始真正的工作了！

首先运行 `buildconf` 脚本。这会创建一个配置脚本，PHP 将基于该脚本进行编译。在下一步中，调用 `configure` 并指定你想要创建哪些扩展。在 `http://s.php.co/v602262` 有完整列表，但以下调用对于初次测试已经足够：

```
configure --disable-all --enable-cli
```

最后，启动实际的编译过程：

```
nmake
```

这需要一些时间（参见图 2.11）。然而，最后你将获得 PHP 的二进制版本。如果你还使用了 `--enable-debug` 开关，结果将在 `Debug_TS` 文件夹中；否则，它将在 `Release_TS` 中。

> **注意**
>
> 你可以在图 2.12 所示的输出中看到，使用的 PHP 版本是 8.4.0-dev。这是怎么可能的，因为这本书是关于 PHP 8.3 的（并在其发布后不久定稿）？
>
> 答案很简单：PHP 8.3 发布后，PHP 团队名义上开始着手开发下一个主要版本 PHP 8.4。因为我们直接从 Git 获取了源代码，所以我们拥有最新版本，因此也是 8.4。由于 PHP 8.4 已经发布，你可能会看到 8.5.0-dev 版本。但不要过于兴奋：至少在出版时，这些版本几乎是一样的。
>
> 但是，如果你想编译特定的 PHP 版本，请在调用 `phpsdk_deps.bat` 时指定特定分支，如前面所述。

![](img/ae7820c36e8f24c1623d26668b28e80e_58_0.png)

图 2.11 PHP 正在编译 ...

![](img/ae7820c36e8f24c1623d26668b28e80e_58_1.png)

图 2.12 ... 并且它可以工作！

## 扩展

在 Windows 下，扩展安装在 `php.ini` 中。首先，扩展目录很重要。你使用 `extension_dir` 指令来设置它。在 PHP 中，你将在 `ext` 目录中找到扩展：

```
extension_dir = "ext"
```

许多扩展不包含在标准包中，而是在各自的 PECL 包中。PECL 是用 C 编写的扩展的官方目录（参见 [http://pecl.php.net](http://pecl.php.net)）。如果你已正确输入扩展目录，则只需注册扩展本身。自远古以来，这总是按照以下模式进行：

```
extension=php_name.dll
```

自 PHP 7.3 起，还有一种简写形式，免去了 `php` 和 `.dll`。其优势在于，配置的这部分因此与操作系统无关：

```
extension=name
```

随安装提供的大多数扩展已经写入 `php.ini`（参见图 2.13）。但是，它们仍然被分号注释掉：

```
;extension=exif
```

只需删除行前的分号即可启用扩展。如果你重启 Web 服务器（作为 CGI 模块使用时，重新调用一次即可），你将通过 `phpinfo()` 看到新扩展现已注册。

![](img/ae7820c36e8f24c1623d26668b28e80e_59_0.png)

图 2.13 “php.ini” 文件中的扩展

## 刷新

最终，剩下的就是保持系统安全。为此，最重要的是要定期使用 Windows Update（参见图 2.14）。

![](img/ae7820c36e8f24c1623d26668b28e80e_60_0.png)

图 2.14 Windows Update 更新操作系统和其他组件

然而，仅此还不够。即使你使用 Apache 或其他 Web 服务器，也应始终保持其最新状态。对于生产系统，php.ini 中的设置对安全性也至关重要。最后但同样重要的是，PHP 版本也应当保持相对最新。

## 2.1.3 macOS

macOS 用户（曾称 OS X）让 PHP 运行起来特别容易。例如，安装 Web 服务器这一最初有时繁琐的步骤已不再必要，因为 macOS 默认包含 Apache 服务器。但出于明显原因，它默认处于禁用状态。

没有用于设置和启动该 Web 服务器的内置 UI；你必须改用命令行。这取决于你使用的是现代 macOS 版本（至少 Monterey 或 macOS 10.12）还是旧版本。在后一种情况下，打开终端窗口并启动 Apache Web 服务器：

```
sudo apachectl start
```

Web 服务器有两个根目录。全局根目录位于 /Library/WebServer/Documents；那里的文件可通过 http://localhost/filename 访问。对于用户级别的 Web 文件夹，你必须先在用户目录中创建一个 sites 文件夹，然后配置服务器。在 http://s-prs.co/v602263，你可以找到 macOS Big Sur 的完整说明（也包含早期版本的链接），这里我们向你推荐该页面。

接下来，你需要 PHP。不幸的是，PHP 项目不为 Mac 提供官方二进制文件，但 PHP 已包含在 macOS 中（尽管通常是旧版本）。不过，你需要通过编辑 /private/etc/apache2/httpd.conf 文件来启用它——例如，使用以下命令（参见图 2.15）：

```
sudo nano /private/etc/apache2/httpd.conf
```

![](img/ae7820c36e8f24c1623d26668b28e80e_61_0.png)

图 2.15 编辑“httpd.conf”文件以激活 macOS 自带的 PHP

该文件包含以下行：

```
#LoadModule php7_module libexec/apache2/libphp7.so
```

是的，这实际上是 PHP 7 版本。你必须删除行首的井号（注释字符）。重启服务器后，PHP 即可使用：

```
sudo apachectl graceful
```

> **注意**
>
> 在旧版 macOS 中，httpd.conf 文件包含其他与 PHP 相关的内容。其中，你必须确保带有 .php 扩展名的文件也由 PHP 处理。请参阅 http://s-prs.co/v602264 中的步骤 2 和尤其是步骤 3。

