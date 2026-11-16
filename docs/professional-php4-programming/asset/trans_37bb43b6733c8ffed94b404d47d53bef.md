

运行 make 来编译该库：

```
make
```

以超级用户身份登录并运行 make install，将该库安装到计算机上的正确位置：

```
make install
```

现在您需要重新配置 PHP 并启用 libedit 重新编译它。默认情况下 libedit 安装在 `/usr/local/lib`，如果您将其安装在其他位置，请相应更改路径。另外，请记住，您需要以超级用户身份登录才能运行下面的 make install：

```
cd ~/php4
./configure --with-libedit=/usr/local/lib [other configure options]
make
make install
```

您可以通过运行 php -m 来测试 libedit 扩展是否已安装，以列出编译到 PHP 中的模块。这应该会将 readline（libedit 扩展的原始名称）列为 [PHP 模块] 下的扩展之一。

## PHP-GTK 支持

UNIX 下 PHP-GTK 的安装使用与上面讨论的大致相同的命令。从 http://gtk.php.net/ 下载 PHP-GTK 模块的最新源代码以及 PHP 的当前 CVS 版本（或快照，或候选版本）。首先安装 PHP 的二进制版本。解压 PHP-GTK 发行版并切换到该目录；这类似于使用 tar 命令解压发行版。

在 PHP-GTK 目录中运行随 PHP 安装的 buildconf 脚本。这将创建 configure 脚本。接下来，运行 ./configure。它将检查您是否安装了正确的 GTK+ 版本（1.2.6 或更高版本，可从 http://www.gtk.org/ 获取）以及编译所需的其他文件，并创建所需的 makefiles。

请注意，PHP-GTK 目前仅适用于 GTK+ 的 1.2.x 系列，1.3.x 是不稳定的开发版本。./configure 命令有多种用于包含 PHP-GTK 模块的选项，请参阅 ./configure --help 了解您的安装支持的选项。最后，运行 make 来编译扩展。

编译成功后，以超级用户身份运行 make install，将扩展安装到默认的 PHP 扩展目录（通常是 /usr/local/lib/php/extensions）。

> PHP-GTK 目前仍被视为测试版。如果您在上述安装说明中遇到问题，请参阅发行版中包含的 README 文件，因为随着新功能的添加，这些说明可能会更改。如果您已这样做但仍无法编译 PHP-GTK，那么最好联系其中一个支持列表。

## Windows 设置

在本节中，我们将讨论如何在各种 Windows 版本上设置用于命令行应用程序的 PHP。

## 环境

为此，您需要从 http://www.php.net/ 下载 PHP 的 CGI 版本，或按照安装章节中详细说明的构建 php.exe。请注意，php.exe 也包含在 PHP-GTK 包中，因此如果您也打算安装 PHP-GTK，则无需遵循这些安装说明，可以直接跳转到下面的 PHP-GTK 说明。

在 Windows 95 或 98 下，将以下行添加到您的 C:\AUTOEXEC.BAT 中。这假设您的 php.exe 位于目录 c:\php 中：

```
SET PATH=%PATH%;c:\php;
```

AUTOEXEC.BAT 是 Windows 启动时自动执行的批处理文件。您需要重新启动 Windows 以确保环境更改已应用到您的系统。

在 Windows ME 下，流程略有不同，因为 Windows ME 没有 AUTOEXEC.BAT 文件。您需要运行 msconfig.exe（开始 | 运行 | msconfig）来设置这些环境变量，然后修改“环境”选项卡下的 PATH 条目。

在 Windows NT、Windows 2000 或 Windows XP 下，您需要设置一个环境变量以达到相同的结果。右键单击“我的计算机”图标。从菜单中选择“属性”，选择“高级”选项卡，然后单击“环境变量”按钮。如果您希望所有系统用户都能通过在命令行中输入 php 来使用 PHP，请设置系统变量，否则将其设置为用户变量。

如果尚未定义 PATH 环境变量，请单击“新建”按钮。将变量名文本框填写为 PATH，将变量值文本框填写为 c:\php，假设这是您的 php.exe 文件所在的目录。

如果 PATH 已作为环境变量定义，请单击列表框中的其条目，然后单击变量值框末尾的“编辑”按钮。输入分号后跟 c:\php，假设这是包含您的 php.exe 的目录。您可以在命令提示符下键入以下内容来检查路径是否已设置：

```
PATH
```

此命令将显示当前生效的 PATH 环境变量。然后，您可以使用以下内容来测试 php.exe 是否在您定义的 PATH 中：

```
"Hello GTK !!!" | php.exe
```

如果 PATH 设置未指向正确位置，MS-DOS 将响应一条 "Bad command or file name" 消息；如果您的 PATH 设置正确，PHP 将输出消息：

```
Hello GTK !!!.
```

libedit 在 Windows 下不可用，因此无法在 Windows 下使用 libedit 创建交互式命令行应用程序。

## PHP-GTK 支持

Windows 版 PHP-GTK 的二进制文件以 zip 文件形式提供，该文件包含 PHP 二进制可执行文件以及必要的 PHP-GTK 文件（可从 http://gtk.php.net/ 获取）。

解压文件后，将创建以下子目录：

- php4，此目录包含 PHP 和 PHP-GTK 二进制文件
- winnt\, 此目录包含默认的 php.ini 文件
- winnt\system32\, 此目录包含 GTK+ 二进制文件和 libglade dll
- samples\, 此目录包含一些示例以演示 PHP-GTK 用法

按照以下步骤完成安装：

- 将 php4 目录复制到您想要安装 PHP-GTK 的位置。通常，此目的最佳且默认位置是 c:\，以便您有一个名为 c:\php4 的目录。
- 将 winnt\ 目录的内容复制到系统根目录。在 Windows NT 和 Windows 2000 上，那是 c:\winnt\。在 Windows 95/98/ME/XP 上，它是 c:\windows\. 如果您已有 php.ini，则无需复制此文件。
- 将 winnt\system32\ 目录的内容复制到系统的 system32\ 目录。在 Windows NT 和 Windows 2000 上，它是 c:\winnt\system32\。在 Windows 95/98/ME/XP 上，它是 c:\windows\system32\。
- 将 samples\ 复制到您想要运行脚本的位置（例如 c:\php4\samples）。

要测试 PHP-GTK 应用程序，请打开 DOS 窗口并键入以下内容：

```
c:\php4\php -q c:\php4\samples\hello.php
```

这应该会启动发行版中包含的 "Hello World" 示例。为了方便起见，您可能希望像上面所述那样设置 PATH 环境变量。

如果 PHP 查找 php_gtk.dll 时出现问题，很可能是您 php.ini 中的 extension_dir 设置不正确。您应将其设置为 php_gtk.dll 所在的目录（通常是 c:\php4）。

## 自动化任务

从命令行使用时，PHP 可以帮助在 Windows 和 Linux 下自动执行任务。它可以执行的一个常见任务是解析当天的 Web 日志，这些日志存储在 NCSA Common Log Format（Apache 的默认日志类型）中。分析日志后，PHP 应将摘要电子邮件发送给网站管理员。为此，我们需要一个简单的脚本来执行以下操作：

- 打开当天的日志文件
- 将其读入内存
- 收集当天请求的统计信息
- 将它们电子邮件发送给管理员

然后我们需要设置脚本在每天午夜运行。

## NCSA 常见日志文件格式

在 NCSA 格式中，每行有一个条目，每个条目都是发送到服务器的请求。解释日志文件的最佳方法是查看示例：

```
10.0.0.1 - - [10/Apr/2001:14:22:57 +0100] "GET /icons/blank.gif HTTP/1.1" 404 287
10.0.0.1 - - [10/Apr/2001:14:24:37 +0100] "GET /error.php HTTP/1.1" 500 289
10.0.0.5 - - [10/Apr/2001:14:25:00 +0100] "GET /private/index.php HTTP/1.1" 401
291
10.0.0.5 - jm [10/Apr/2001:14:25:32 +0100] "GET /private/index.php HTTP/1.1" 200
770
10.0.0.2 - - [10/Apr/2001:14:26:58 +0100] "GET /links.php HTTP/1.1" 200 99
```

这里有一些来自我自己日志的针对本地 Web 服务器的各种请求。每行具有以下形式：

```
ClientIP - UserName [Date:Time TimeZone] "Method URI HTTPVersion" StatusCode BytesSent
```

如果查看日志摘要的第一行，它告诉我们 IP 地址为 10.0.0.1 的客户端于 2001 年 4 月 10 日 14:22:57 在 GMT+1 小时时区（英国夏令时）请求了我们 Web 服务器上的一个页面。他们请求通过 GET 方法使用 HTTP 协议版本 1.1 查看资源 /icons/blank.gif。服务器找不到此文件，并发送了 404 状态码，生成了 287 字节的出站流量。日志还显示，同一用户请求了页面 /error.php，导致服务器返回 500 状态码（内部服务器错误），该请求生成了 289 字节。

然后，另一位用户请求了一个受保护的页面，该请求生成了 401 状态码，要求用户进行身份验证，用户随即验证，以用户 jm 身份进行身份验证。这在日志文件的下一行中显示。最后一个请求只是 IP 为 10.0.0.2 的机器上的客户端请求页面 /links.php 的简单请求。服务器处理了该请求并返回了 OK 状态码 200。

