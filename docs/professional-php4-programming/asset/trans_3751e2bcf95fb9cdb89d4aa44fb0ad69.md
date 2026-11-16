

```
./configure --exec-prefix=/usr \
--localstatedir=/var \
--mandir=/usr/share/man \
--libexecdir=/System/Library/Apache/Modules \
--iconsdir=/System/Library/Apache/Icons \
--includedir=/System/Library/Frameworks/Apache.framework/Versions/1.3/Headers \
--enable-shared=max \
--enable-module=most \
--target=apache
```

确保 `--includedir=.../1.3/Headers \` 在同一行上。

## 编译 Apache

如果配置顺利，您现在可以编译 Apache：

```
make
```

如果成功，您可以安装 Apache：

```
make install
```

此时，您可能无法使用 Apache，因为您的旧 httpd.conf 文件可能未被覆盖，并且它可能仍在尝试加载旧版 PHP，而该旧版 PHP 可能已或未配置和编译为与您的新版 Apache 一起工作。

您可以编辑 httpd.conf，注释掉（不要删除）任何提及 php 的行，然后停止并启动 Apache 来测试 Apache：

```
apachectl stop
apachectl start
```

在发出这些命令之前，您可能需要切换到 Apache 的 bin 目录，或使用 bin/apachectl。

> 由于 Mac OS X GUI 存在问题，不建议通过“系统偏好设置 | 共享”小程序启动 Apache。虽然启用网页共享时 Apache 会启动，但 OS X 不会允许您在启动后关闭 Apache。出于此原因，建议仅通过终端窗口调用 apachectl 来启动和停止 Apache。

发出 apachectl start 命令后，您可以通过在进程列表中搜索服务器进程 httpd 来检查 Apache 是否真的已启动，方法是如示例所示组合使用 ps 和 grep 命令，或者在 Mac OS X 进程查看器中搜索 httpd：

```
ps -A | grep httpd
620 nobody      00:00:00 httpd
621 nobody      00:00:00 httpd
622 nobody      00:00:00 httpd
```

只要找到至少一个 `httpd` 进程，Apache Web 服务器即成功启动。

您应该能够在 http://localhost/ 上看到默认的 Apache 安装页面，或者查看您的 Web 服务器先前在 `httpd.conf` 的 `DocumentRoot` 设置中配置为主页的任何内容。

### 安装 PHP

一些第三方团队已开始为 OS X 提供预编译的 Apache/PHP 版本。虽然这些软件包不是必需的，但应注意到这些软件包的存在。有关为 OS X 下载 PHP 二进制版本的更多信息，请参阅 PHP 手册。本书将从源代码编译，但如果您遇到严重困难，可能会发现安装预编译二进制文件更容易。

将 PHP 源代码下载并解压到临时目录，就像您处理 MySQL 和 Apache 那样。如果需要除 MySQL 以外的任何 PHP 扩展，您应在安装 PHP 之前下载、安装并测试它们。

使用 Apache 服务器配置选项时，我们必须明确指定 PHP 使用的某些目录，以便它能与 OS X 顺利协作，如下所示：

```
./configure \
--with-mysql=/Users/root/Desktop/mysql-3.xx.xx \
--with-apache=/Users/root/Desktop/apache_1.x.xx \
--prefix=/usr \
--sysconfdir=/etc \
--localstatedir=/var \
--mandir=/usr/share/man
```

对于添加到此过程中的任何其他 PHP 扩展，您需要包含 `--with-XXX`。

### 编译 PHP

PHP 配置妥当后即可编译。与 Apache 和 MySQL 一样，PHP 是通过一对 `make` 命令编译的，如下所示：

```
make
make install
```

在某些情况下，上述命令可能会以错误结束。由于 UNIX/DOS/Mac 之间换行符的差异，先前的 configure 语句无法正确修改 PHP 源代码树中 `./main` 下的 `internal_functions.c` 文件。`configure` 脚本会插入多个 `#include` 语句，但插入的不是换行符，而只是一个 `n`，并且多个独立的 `#include` 行都在同一行上。要纠正此错误（如发生），请打开 `internal_functions.c` 文件并更正以下内容：

```
#include "ext/xml/php_xml.h"n#include "ext/standard/php_standard.h"ninclu...
```

应为：

```
#include "ext/xml/php_xml.h"
#include "ext/standard/php_standard.h"
#inclu...
```

简而言之，每个 #include 应独占一行，且直接位于其前的每个 n 都应被删除，无论有多少个。还请记住，我们只展示了受此问题影响的前几个 #include 语句。意味着应按上述方式更正所有 include 语句。一旦更正了该错误，PHP 即可无需进一步处理便可编译。

## 安装后

PHP 编译完成后，我们必须将 PHP 源代码树中的 php.ini-dist 文件复制到 PHP 配置为加载的位置，默认位置为 /usr/local/lib/php.ini：

```
cp php.ini-dist /usr/local/lib/php.ini
```

您应查看 php.ini 文件，并按“在类 UNIX 系统上安装”部分中所述进行编辑。

## 将 PHP 与 Apache 集成

现在 Apache 已正常工作，PHP 也已编译，是时候将两者集成了。切换回 Apache 源代码目录，并再次运行 configure 以在 Apache 中激活 PHP：

```
cd /Users/root/Desktop/apache_1.x.xx

./configure \
--exec-prefix=/usr \
--localstatedir=/var \
--mandir=/usr/share/man \
--libexecdir=/System/Library/Apache/Modules \
--iconsdir=/System/Library/Apache/Icons \
--includedir=/System/Library/Frameworks/Apache.framework/Versions/1.3/Headers \
--enable-shared=max \
--enable-module=most \
--target=apache \
--activate-module=src/modules/php4/libphp4.a
```

请确保 --includedir=.../1.3/Headers \` 在同一行上。

在某些情况下，尝试执行上述 configure 命令会导致错误，报告 libmodphp4.a 已过期。可以通过从 Apache 源代码树的 ./src/modules/php4 目录运行以下命令来解决此情况：

```
ranlib libmodphp4.a
```

使用 "--activate-module=...libphp4.a" 成功配置后，应适当修改 httpd.conf 文件，以便在重启 Apache 时激活 PHP。

停止并重启 Apache，以使修改后的 httpd.conf 文件生效：

```
apachectl stop
apachectl start
```

创建 phpinfo.php 并将其保存在您的 DocumentRoot Web 目录中。之后，您应该能够在 http://localhost/phpinfo.php 上查看来自 PHP 的状态页面。

如果不起作用，请检查 --activate-module=src/modules/php4/libphp4.a 在 httpd.conf 中造成的更改。

它可能未正确添加/更改基于 UNIX 的安装中讨论的 AddType 行。这是最可能的错误来源。另请检查基于 UNIX 的安装中的问题和解决方案。

### 独立编译 PHP

与基于 UNIX 的安装一样，应重复 PHP 的 configure 和 make 步骤，只是不要 --with-apache=... 行，然后将生成的 php 程序复制到 /usr/bin/ 或合适位置。

## 进一步资源

### Wrox.com

如果教程反复无法产生预期结果，还有许多其他来源可供查询以获取更多信息和帮助。对于所有三种软件包，Wrox 网站上均提供在线讨论论坛，网址为：http://p2p.wrox.com/。

### PHP.net

PHP 网站上的以下页面可能很有用：

- http://php.net/FAQ.php。PHP 常见问题解答。
- http://php.net/funcref。跟随正文中的每个链接并阅读概述。
- http://www.php.net/langref。在此书之前和之后阅读整个部分。

您还应了解 http://php.net/support.php 上的 PHP 邮件列表。这些列表已存档，大部分是新闻组的网关。

大部分也可在摘要模式下获得，频率低得多，每条大消息包含自上次摘要以来的所有消息。PHP-General 摘要每天两次，但仍是一封非常大的电子邮件。

PHP 邮件列表通常非常友好，对新手问题极其宽容，但请遵循以下规则：

- 阅读手册
- 在发送问题前重新阅读常见问题解答

