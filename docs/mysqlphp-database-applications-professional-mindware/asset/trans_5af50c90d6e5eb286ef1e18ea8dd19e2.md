
此时你的 MySQL 安装已完成。 要测试它，请进入 DOS 提示符并移动到你为 MySQL 安装指定的目录。 然后移动到名为 \bin 的子目录。 如果你随后输入 mysqld，mysql 守护进程应该会启动。 要测试守护进程是否正常工作，请通过输入 mysql 启动 mysql 命令行客户端。 如果监视器启动并看起来像图 B-1，则 MySQL 正常工作。

![](img/de0823012275cf4ceebdb822a56e6b71_440_0.png)

图 B-1：MySQL 监视器在 Windows 上运行

接下来，你应该安装 Apache。

这只需要双击你从 CD 或 apache.org 网站复制的可执行文件即可。 安装非常简单：你真正需要做的就是选择一个希望安装 Apache 的目录。 完成后，开始菜单中会添加一个 Apache 组项。

> 暂时不要启动 Apache。 稍后还会有一些配置信息。

现在开始 PHP。 你应该有一个文件夹，里面解压了所有 PHP 文件。 在该文件夹中，将 MSVCRT.DLL 和 PHP4TS.DLL 复制到 c:\windows\system。 然后将 php.ini-dist 重命名为 php.ini，并将其保留在 php.exe 文件所在的同一目录中。

这一步你需要做的就是确保 Apache 知道 PHP，并且 PHP 知道 MySQL。

首先进入你安装 Apache 的目录，在 \conf 目录中找到 httpd.conf 文件，并在文本编辑器中打开它。 在文件中添加以下三行：

```
ScriptAlias /php4/ "d:/php4/"
AddType application/x-httpd-php4 .php
Action application/x-httpd-php4 "/php4/php.exe"
```

请注意，我们指定了 d: 盘，因为我们自己的系统就是这样设置的。 c: 盘同样可以使用。

第一行指示 PHP 所在的路径。 第二行告诉 Apache 哪些文件扩展名必须作为 PHP 解析，第三行给出 php 可执行文件的路径。 请注意，使用这种类型的安装，PHP 将作为可执行文件运行，而不是 Apache 服务器模块。

如果你希望其他文件扩展名也被 PHP 解析，只需在 conf 文件中再添加一行 AddType；例如：

```
AddType application/x-httpd-php4 .phtml
```

你可能需要在 httpd.conf 文件中做一些其他修改。 如果服务器拒绝启动，你可能需要在 Server Name 指令中添加一些内容。 如果你在局域网中使用 TCP/IP，你可能需要添加你机器的 IP 地址，例如：

```
ServerName 192.168.1.2
```

或者如果你的机器没有联网，你可能想使用以下 ServerName

```
ServerName 127.0.0.1
```

如果你的机器上也运行着 Personal Web Server，你可能希望更改 Apache 运行的端口。 默认情况下，Web 服务器监听 80 端口，但你可以通过修改 httpd.conf 中的 Port 行来更改它——也许是 8080。

这样应该就完成了。 通过开始菜单启动 Apache。 在你的 \htdocs 文件夹中添加一个包含 phpinfo() 函数的文件。 当你调用该函数时，你应该会看到一切正常，并且有一个 MySQL 条目。 图 B-2 显示了 phpinfo() 的结果。

![](img/de0823012275cf4ceebdb822a56e6b71_442_0.png)

图 B-2：Windows 上的 phpinfo()

请注意，你不需要对 php.ini 文件做任何修改就能让 PHP 与 MySQL 协同工作。 事实上，MySQL 支持已内置于 Windows 版 PHP 中。

![](img/de0823012275cf4ceebdb822a56e6b71_442_1.png)

> 如果你取消注释指令 extension=php_mysql.dll，你在加载 PHP 页面时会遇到各种各样的问题。

这些就是在 Windows 上使用 PHP 和 MySQL 所需的基础知识。 请注意，你也可以将 PHP 作为 Internet Information Server (IIS) 和 PWS 的 ISAPI 过滤器安装。 相关说明包含在 PHP zip 文件中包含的 readme.txt 文件中。 截至本文撰写时，在生产环境中以 IIS 过滤器运行 PHP 并不是推荐的做法。

## Unix 安装

在 Unix 上，你可以使用更多选项。 你可能希望通过自行编译源代码或（在 Linux 上）使用 rpm 文件来安装。 本附录仅涵盖从源代码编译。 我们强烈建议

不要使用 rpm 文件。 rpm 有时提供的便利性并不适用于这种类型的配置。 有各种库和可选函数可以编译到 PHP 中，并且库和函数一直在不断添加。 在本快速指南中，我们只会涵盖一些重点。 如果你有其他优先事项，需要 rpm，或希望包含此处未涵盖的选项，请查阅在线手册中的文档。 这真的不是一个非常困难的安装过程，你应该能够以最小的努力按需自定义。 首先是 MySQL。

### MySQL 安装

有关 MySQL 安装的完整信息可在 MySQL 在线手册的第 4 章中找到：http://www.mysql.com/documentation/mysql/bychapter/manual_Installing.html。 如果你遇到问题，请查看。

你需要从随附的 CD-ROM 或 http://www.mysql.com/downloads/ 获取 .tar.gz 文件。 将其复制到你想要工作的目录，然后使用以下命令解包此文件：

```
gunzip mysql-3.23.22.tar.gz
tar xf mysql-3.23.22.tar
```

这将创建一个以 mysql 发行版名称命名的目录（例如 mysql-3.23.22）。 使用 cd 进入该目录。 请注意，具体版本可能不同，具体取决于你下载软件的时间。

第一步是运行 configure。 你可以使用 configure 标志设置许多选项。 要获取完整列表，请运行 `./configure --help`。

在我运行的安装中，我发现指定 --prefix 很方便。 如果你不指定前缀，将使用 /usr/local，这几乎总是完全可以的。 此外，mysql 允许你指定任何子目录的位置（数据目录、bin 目录等）。 通常这不是必要的。 通常你可以运行

```
./configure --prefix=/path/to/installation
```

如果你需要在应用程序中使用数据库事务，你需要使用 Berkeley Database (BDB) 表。 截至本文撰写时，此功能仍处于 beta 版本。 你可以从 http://www.mysql.com/downloads 获取 BDB 表。

如果你想使用 BDB 表，你应运行以下 configure 行，而不是前面显示的那一行。

```
./configure --prefix=/path/to/installation --with-berkeley-db=/path/to/files
```

接下来，运行以下两个命令：

```
make
make install
```

就这样。 你现在应该有一个包含所有文件和子文件夹的目录。

你接下来要做的是 cd 进入 bin 目录并运行以下命令：

```
./mysql_install_db
```

这会创建你的默认数据库和权限表。 你现在应该能够使用 /bin 目录中的 safe_mysql 命令启动 mysql 守护进程。

默认情况下，mysql 使用 3306 端口并将重要的套接字文件保存在 /tmp/mysql.sock。 这通常是可以的。 PHP 将在此位置查找套接字文件。 然而，如果你有多个 MySQL 安装，你需要更改端口和套接字位置，这可能会很麻烦。 你需要修改你的 my.cnf 文件。 有关更多信息，请参阅 MySQL 手册第 4 章。

### PHP/Apache

在 Unix 上，PHP 将作为 Apache 模块加载。 因此，两者的安装需要协同进行。 再次强调，有很多很多安装选项。 你可以将 PHP 创建为用于 CGI 或命令行处理的可执行文件，作为共享 Apache 模块（apxs），或用于 DSO。 在这里我们只介绍作为 Apache 模块的安装。

首先解包 Apache 和 PHP。

```
gunzip apache-1.3.x.tar.gz
tar xf apache-1.3.x.tar
gunzip php-4.02.tar.gz
tar xf php-4.02
```

这里的“x”是 apache 的版本号。

使用 cd 进入 Apache 目录并运行 configure，指定你希望安装 Apache 的路径。

```
./configure --prefix=/path/to/apache
```

这会“准备”Apache 设置 PHP 编译所需的特定于机器的信息。 你稍后会回来完成 Apache 安装。
