

首先，将 MySQL 二进制文件从 http://mysql.com/downloads 站点复制到本地驱动器。对 Apache 和 PHP 也做同样的操作（这里相应的下载站点是 http://httpd.apache.org/download.cgi 和 http://www.php.net/download）。文件名大致如下（可能会根据你使用的版本略有不同）：

- mysql-4.0.14b-win.zip
- apache_1_3_22_win32_no_src.exe
- php-4.2.2-Win32.zip

首先，使用你喜欢的解压工具解压 MySQL 文件和 PHP 文件。（如果你没有，我们推荐 http://www.winzip.com/ 上的 WinZip。）将它们解压到你觉得方便的目录中。我们偏好为每个文件使用单独的目录。

从 MySQL 开始。

1. 在解压文件的目录中，你会有一个名为 setup.exe 的文件。执行该文件。

2. 选择一个你想安装到的目录（例如 c:\mysql），然后在下一屏幕中，选择“典型安装”。（你可能想查看自定义选项，但在 Windows 安装中几乎没有真正的选项。）

此时，你的 MySQL 安装已完成。要测试它，请进入 DOS 提示符，切换到你为 MySQL 安装指定的目录。然后进入 \bin 子目录。如果随后输入 mysqld，MySQL 守护进程应该启动。要测试守护进程是否正常工作，请输入 mysql 启动 MySQL 命令行客户端。

接下来，你应该安装 Apache。

此安装只需双击从 apache.org 站点复制的可执行文件即可。安装过程很简单：你真正需要做的只是选择一个域名（如果你不打算将其实际发布到互联网上，只需使用 localhost）以及要安装 Apache 的目录。安装完成后，启动菜单中会添加一个 Apache HTTP Server 组项目。记住你安装 Apache 的目录很重要。你将把构成应用程序的所有 PHP 文件都放在那里。如果你使用了默认设置，则默认服务目录将是 c:\Program Files\Apache Group\Apache\htdocs。

> 现在不要启动 Apache。接下来还有更多配置信息。

接下来是 PHP。你应该有一个解压了所有 PHP 文件的文件夹。（在以下说明中，我们假设该文件夹是 c:\php。）另外，PHP 4 及更高版本有一个相当不错的 Windows Apache 模块。在本书的上一版中，我们推荐使用 CGI 二进制文件。Apache 模块在功能上稍多一些，因此你可能应该使用它。

1. 将 php4ts.dll 和 php4apache.dll 从 c:\php 复制到 c:\windows\system 或 c:\winnt\system32 目录，具体取决于你的 Windows 版本中可用的目录。

2. 接下来，将 php.ini-dist 文件从 c:\php 目录复制到 Windows 95/98 上的 c:\windows，或 NT/2000/XP 上的 c:\winnt。将文件重命名为 php.ini。现在打开 php.ini 文件，修改 extension_dir 条目，使其与存放 .dll 文件的文件夹名称匹配。例如：

```
extension_dir = c:/windows/system32
```

3. 现在你需要修改 Apache 配置文件。最简单的方法是进入“开始”菜单，选择 Apache HTTP Server → 配置 Apache 服务器 → 编辑配置文件。

4. 将以下三行添加到文件中。注意，第一行必须与你系统上的目录名称匹配：

```
LoadModule php4_module c:/windows/system
AddModule mod_php4.c
AddType application/x-httpd-php .php
```

最后一行确保所有带有 .php 扩展名的文件都作为 PHP 应用程序处理。如果你希望其他文件扩展名由 PHP 解析，只需在 conf 文件中添加另一行 AddType，如下所示：

```
AddType application/x-httpd-php4 .phtml
```

你可能还需要对 httpd.conf 文件进行一些其他修改，例如：

- 如果服务器拒绝启动，你可能需要向 ServerName 指令添加一些内容。如果你在局域网中使用 TCP/IP，可能需要添加你机器的 IP 地址，如下所示：

```
ServerName 192.168.1.2
```

或者，如果你的机器未联网，你可能希望使用以下 ServerName：

```
ServerName 127.0.0.1
```

- 如果你的机器上也运行着 Microsoft Personal Web Server，你可能想要更改 Apache 运行的端口。默认情况下，Web 服务器监听端口 80，但你可以通过修改 httpd.conf 中的 port 行将其改为其他值 – 也许是 8080。

就这样应该就搞定了。通过“开始”菜单启动 Apache。向你的 \htdocs 文件夹添加一个包含 phpinfo() 函数的文件。当你调用该函数时，应该能看到一切正常工作，并且其中有一个 MySQL 条目。

请注意，你不需要对 php.ini 文件做任何修改即可让 PHP 与 MySQL 配合使用。事实上，MySQL 支持已内置于 Windows 版 PHP 中。

如果你取消注释指令 extension=php_mysql.dll，加载 PHP 页面时会出现各种问题。

这些是在 Windows 上使用 PHP 和 MySQL 所需的基础知识。请注意，你也可以将 PHP 作为 ISAPI 过滤器安装到 Internet Information Server (IIS) 和 PWS 中。相关说明包含在 PHP Zip 文件附带的 readme.txt 文件中。

截至撰写本文时，将 PHP 作为 IIS 过滤器运行既棘手又不可靠，不建议在生产环境中使用。更好的做是在 Internet Services Management 控制台中将 .php 扩展名与 PHP 解释器关联。这样做要可靠得多。

## 在 Unix/Mac OS X 上安装

在 Unix 上，你可选择的选项多得多。你可以选择自己编译源代码来安装，或者（在 Linux 上）使用 .rpm 文件。本附录仅介绍从源代码编译。我们强烈建议不要使用 .rpm 文件。.rpm 有时提供的便利性并不适用于这种配置，主要是因为配置可能比较棘手，而手动操作是做对它的唯一方法。

你可以将各种库和可选函数编译到 PHP 中，并且还在不断添加新的库和函数。在这本快速指南中，我们仅介绍一些亮点。

如果你有其他优先事项，需要 .rpms，或者想要包含此处未涵盖的选项，请查阅在线手册中的文档。这其实不是一项很难的安装，你应该能以最小的努力随心所欲地进行自定义。第一站，MySQL。

### MySQL 安装

一个我们尚未讨论的选项——可能也是 Unix 上最好的一个选项——是获取由 MySQL AB 分发的一组二进制文件。如果你访问 www.mysql.com/downloads，可以查看几乎所有主要 Unix 发行版的二进制文件，包括 Solaris、Irix、HP-UX、FreeBSD 和 Mac OS X。将所有这些安装文件都包含在 CD 中是不切实际的（而且你还是从网站上获取它们更好），并且安装说明可能因平台而异。但是，从二进制文件安装非常容易——而且比从源代码编译快得多。如果你下载适用于你平台的二进制文件，你会看到随包附带的一组说明。只需运行几个命令，你就可以在 10 分钟内完成 MySQL 安装。

有关 MySQL 安装的完整信息可在 MySQL 在线手册的第 2 章中找到：http://www.mysql.com/documentation/mysql/bychapter/manual_Installing.html。如果你遇到问题，请查看。

如果你决定确实要从源代码安装，则需要从 http://www.mysql.com/downloads/ 获取源代码的压缩 tarball（.tar.gz 或 .tgz 文件）。将其复制到你想要工作的目录，然后使用类似以下的命令解包：

```
gunzip mysql-4.0.12.tar.gz
tar xf mysql-4.0.12.tar
```

此命令会创建一个以 MySQL 发行版命名的目录（例如，mysql-4.0.12）。使用 cd 进入该目录。请注意，确切版本可能会有所不同，这取决于你下载软件的时间。

第一步是运行 configure。你可以使用 configure 标志设置许多选项；要获取完整列表，请运行 ./configure --help。

在我们运行的安装中，发现指定 --prefix 很方便。如果不指定前缀，则使用 /usr/local，这几乎总是完全没问题。此外，MySQL 允许你指定任何子目录的位置（数据目录、bin 目录等）。通常没有必要。通常你可以运行以下命令：

```
./configure --prefix=/path/to/installation
```

现在你只需执行两个命令：

```
make
make install
```

