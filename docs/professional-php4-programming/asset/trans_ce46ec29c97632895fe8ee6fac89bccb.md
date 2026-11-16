

这将在源目录中创建一个名为 php 的文件。

然后，您可以安全地将该文件复制到 /usr/bin/ 目录或 /usr/sbin/ 或 /usr/local/bin/ 或您觉得最合适的任何位置。如果您希望与操作系统保持一致，请使用 whereis perl 来找到 perl 二进制文件的位置，并将 php 二进制文件放在同一目录中。

如果您完全不了解 perl 是什么，并且对目录的适当性感到非常困惑，请直接使用 /usr/bin/。

现在，您可以尝试类似下面的操作：

```
php /usr/local/apache/htdocs/phpinfo.php
```

您刚刚从命令行执行了 PHP 脚本 phpinfo.php，且未涉及任何 Web 服务器。这对于各种用途都非常方便。如果您暂时想不出任何用例，一旦开始创建脚本，就会想到它们。有关更多示例，请参见第 20 章。

您还可以创建可执行的 PHP 脚本，就像 Perl 一样。请尝试以下操作：切换到您的主目录（只需使用不带路径的 cd），并创建一个名为 hello 的文件（无需扩展名），内容如下：

```
#!/usr/bin/php -q
<?php
print ("Hello World\n");
?>
```

保存并退出编辑器，然后执行：

```
chmod 755 hello
./hello
```

通过使此文件可执行（chmod 755 hello），您创建了一个独立命令，就像 cd 和 ls 以及我们一直在使用的所有其他 UNIX 命令一样，但您的命令以 #!/usr/bin/php -q 开头，这指示它使用 PHP 二进制文件来执行指令。

-q 部分代表 quiet，它告诉 PHP 不要输出通常会发送到 Web 的某些默认标头。如果您愿意，可以尝试不带 -q 运行以查看差异。print() 将引号内的文本打印到控制台。\n 部分在末尾添加一个换行。如果没有它，您的 Shell 提示符将与 Hello World 输出显示在同一行。

## 在 Mac OS X 上安装

Mac OS X 是 Macintosh 操作系统的最新版本，基于修改版的 FreeBSD 内核，因此是 PHP 的一个非常可行的选择。Mac OS X 上的安装直接源自基于 UNIX 的安装，因此您可能希望回顾前面关于基于 UNIX 的安装的章节。

如果您遇到任何困难，原因和解决方案几乎肯定与基于 UNIX 的安装相同，因此在此不予重复。

Apache/MySQL/PHP 在 Mac OS X 之前的 Mac OS 版本上不原生运行，并且不太可能被移植回这些版本。

有一个低流量的邮件列表专门用于 Macintosh 上的 Apache/MySQL/PHP，网址为 http://forum.dynapolis.com/。

## 安装前准备

与从命令行执行 gunzip 和 tar 程序不同，Mac OS X 自带一个名为 StuffIt! 的易于使用的程序，只需单击鼠标即可完成相同的任务。在提取源分发版之前，建议将其移动到桌面。本 Mac OS X 教程基于所有源分发版均位于 /Users/root/Desktop/。移动后，只需单击每个分发版将其提取到常规文件夹中即可。

## 安装 MySQL

以 root 身份登录。从 http://mysql.com/ 下载基于 UNIX 的源分发版到桌面。使用 StuffIt! 按安装前准备部分所述将其提取到桌面。

## 为 MySQL 创建用户

如基于 UNIX 的安装所述，出于安全考虑，有必要创建一个唯一用户来运行 MySQL 数据库服务器。要创建新用户，请使用下图系统配置菜单中找到的“用户”小程序：

![](img/9cf7789dba9b16ef3f8576d5aea89186_74_0.png)

![](img/9cf7789dba9b16ef3f8576d5aea89186_75_0.png)

## 配置 MySQL 源代码

要配置 MySQL 以进行安装，请打开终端窗口并切换到源目录：

```
cd /Users/root/Desktop/mysql-3.xx.xx
```

接下来，使用 --prefix=/usr/local/mysql 和 --localstatedir=/usr/local/mysql/data 配置安装：

```
./configure --prefix=/usr/local/mysql \
--localstatedir=/usr/local/mysql/data
```

您可以省略 \\ 并将所有内容放在同一行上。

## 编译和初始化 MySQL

configure 脚本成功完成后，我们现在可以使用 make 命令实际编译 MySQL：

```
make
make install
```

除非出现问题，此时安装完成只剩下几个最后的步骤。为了使 MySQL 正常运行，根安装目录 /usr/local/mysql/ 和 MySQL 存储数据库的目录 /usr/local/mysql/data/ 必须使用 chown 命令更改权限。对于根目录，权限必须设置为使目录所有者为 root。对于数据库目录，所有者必须设置为我们创建的用户（mysql）：

```
chown -R root /usr/local/mysql
chown -R mysql /usr/local/mysql/data
chgrp -R mysql /usr/local/mysql/data
```

设置权限后，必须通过执行 MySQL 源分发版 ./scripts/ 目录中的 mysql_install_db 脚本来初始化 MySQL 服务器使用的授权表：

```
./scripts/mysql_install_db
```

权限设置正确且授权表初始化脚本完成后，现在可以安全地启动 MySQL 服务器。在我们的 MySQL 安装的 ./bin/ 目录中位于一个名为 safe_mysqld 的可执行文件，用于启动 MySQL 服务器。此命令必须作为后台进程运行（通过在命令末尾追加 & 符号），并且我们创建的用户名必须使用 --user 选项作为参数传递：

```
safe_mysqld --user=mysql &
```

MySQL 启动后，我们已成功完成 MySQL 的安装。可能希望每次重新启动机器时都启动 MySQL 服务器。可以通过将 mysql.server 文件（位于 ./support-files/ 目录中）复制到系统的相应启动位置来实现这一点。

### 测试 MySQL

您可以通过执行以下操作来验证 MySQL 服务器是否正在运行：

```
mysqladmin version
mysqlshow
```

这些命令应打印出版本和版权通知，以及 MySQL 中的数据库列表。最初，会有一个名为 mysql 的数据库，其中包含用户权限等 MySQL 内部内容，还可能有一个名为 test 的数据库，供您进行实验。

如果未包含 test，您应该能够执行：

```
mysqladmin CREATE test
```

然后，既然您有用于实验的 test 数据库，就可以执行：

```
mysql -u root test
```

这将启动 `mysql` 命令行客户端，允许您向 MySQL 服务器程序发送 SQL 命令。您将以 root 身份登录到 MySQL，并在名为 test 的数据库中工作。

您应该会看到欢迎通知和类似 mysql> 的提示符。然后，您可以执行 SQL 命令：

```
CREATE TABLE foo (foo_id INT(11) AUTO_INCREMENT, comment TEXT);
DESCRIBE foo;
INSERT INTO foo (comment) VALUES ('Hello World');
SELECT * FROM foo;
DELETE FROM foo;
DROP TABLE foo;
```

您可以使用 \q 命令退出 MySQL。

## 保护 MySQL

但是，此时，您的 MySQL 数据库只有一个名为 `root` 的 MySQL 用户，并且该用户的密码为空。MySQL 的 root 用户与操作系统的 root 用户完全无关，尽管两者背后的概念相同。MySQL 的 `root` 用户可以对 MySQL 中的任何数据库执行 **任何** 操作。最重要的是，已知恶意用户可以利用 MySQL `root` 访问权在计算机文件系统上安装程序以入侵您的计算机。

> 您 **必须** 设置 MySQL 的 `root` 密码。

不要在日常操作中使用 MySQL 的 `root` 用户名/密码。为每个数据库创建一个带有不同密码的新 MySQL 用户以提高安全性。

## 安装 Apache

本教程旨在覆盖 OS X 操作系统安装的当前 Apache Web 服务器。请在继续之前确保已备份所有重要数据（例如 `httpd` 二进制文件及其配置文件）。

## 配置 Apache 源代码

从先前解压并解档的 Apache 源代码树根目录（`/Users/root/Desktop/apache_1.x.xx/`）开始，我们将先准备源代码以使用 Apache 的 `configure` 脚本。`configure` 脚本用于确定某些安装参数，例如 Apache 的安装位置、Apache 将在 Internet 上查找要提供的文件的位置，以及 Apache 将存储其配置文件的位置。

在大多数配置下，OS X 已预装并配置了 Apple 版本的 Apache Web 服务器，因此在升级服务器时保留原始配置使用的目录结构和文件位置非常重要。出于此原因，在配置 Apache 时，我们无法依赖 `configure` 脚本为我们选择适当的路径，因此必须手动定义这些路径。此外，其他通常可以保留默认值的选项（例如某些模块是否为共享模块）也必须手动配置，以尽可能镜像原始 Apple Web 服务器：

