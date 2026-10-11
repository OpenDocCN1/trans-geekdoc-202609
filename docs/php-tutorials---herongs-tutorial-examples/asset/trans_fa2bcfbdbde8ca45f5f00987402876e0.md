

# PHP 7.3 简介与安装

## 在 Windows 上下载并安装 PHP 7.3

本节提供了一个教程示例，介绍如何在 Windows 系统上下载并安装 PHP 7.0 引擎。

1. 访问 [windows.php.net/download/](http://windows.php.net/download/) 并下载适用于 Windows 的 "VC15 x64 Thread Safe (2018-Dec-06 04:31:24)" 二进制版本。你将获得一个名为 `php-7.3.0-Win32-VC15-x64`、大小为 21,846,474 字节的文件。

2. 将 `php-7.3.0-Win32-VC15-x64` 解压到 `\php` 文件夹。

3. 打开一个命令窗口，并尝试运行以下命令：

```
herong> \php\php -v
```

4. 如果看到错误消息提示："The program can't start because VCRUNTIME150.dll is missing from your computer. Try reinstalling the program to fix this problem."（无法启动此程序，因为计算机中丢失 VCRUNTIME150.dll。尝试重新安装该程序以解决此问题。），则需要安装 "Visual Studio 2015 x86"。

* 访问 "Microsoft Visual C++ Redistributable for Visual Studio 2015" 页面：[microsoft.com/en-us/download/details.aspx?id=48145](https://www.microsoft.com/en-us/download/details.aspx?id=48145)。
* 点击 "Download"（下载）按钮。
* 将下载的文件 `vc_redist.x86.exe` 保存到桌面。
* 双击 `vc_redist.x86.exe` 运行它。
* 按照说明完成安装。

5. 再次打开一个命令窗口，并尝试运行以下命令：

```
herong> \php\php -v

PHP 7.3.0 (cli) (built: Dec  6 2018 01:54:19)
   (ZTS MSVC15 (Visual C++ 2017) x64)
Copyright (c) 1997-2018 The PHP Group
Zend Engine v3.3.0-dev, Copyright (c) 1998-2018 Zend Technologies
```

太棒了，PHP 的命令行界面（CLI）和通用网关接口（CGI）均已正常工作！

## "php -help" - 命令行选项

本节提供了一个教程示例，介绍如何查看 PHP 引擎支持的所有命令行选项：`php -help`。

如果你想了解 PHP 引擎支持哪些命令行选项，可以使用 `-help` 选项运行 PHP：

```
herong> \php\php -help

Usage: php [options] [-f] <file> [--] [args...]
   php [options] -r <code> [--] [args...]
   php [options] [-B <begin_code>] -R <code> [-E <end_code>] [--] [args...]
   php [options] [-B <begin_code>] -F <file> [-E <end_code>] [--] [args...]
   php [options] -- [args...]
   php [options] -a

  -a               交互式运行
  -c <path>|<file> 在此目录中查找 php.ini 文件
  -n               不使用 php.ini 文件
  -d foo[=bar]     定义值为 'bar' 的 INI 条目 foo
  -e               为调试器/分析器生成扩展信息
  -f <file>        解析并执行 <file>。
  -h               显示此帮助
  -i               PHP 信息
  -l               仅语法检查 (lint)
  -m               显示内编译的模块
  -r <code>        运行 PHP <code> 而无需使用脚本标记 <?..?>
  -B <begin_code>  在处理输入行之前运行 PHP <begin_code>
  -R <code>        对每个输入行运行 PHP <code>
  -F <file>        对每个输入行解析并执行 <file>
  -E <end_code>    在处理完所有输入行后运行 PHP <end_code>
  -H               从外部工具隐藏传递的任何参数。
  -S <addr>:<port> 使用内置 Web 服务器运行。
  -t <docroot>     为内置 Web 服务器指定文档根目录 <docroot>。
  -s               输出 HTML 语法高亮源代码。
  -v               版本号
  -w               输出去除注释和空白的源代码。
  -z <file>        加载 Zend 扩展 <file>。

  args...          传递给脚本的参数。当第一个参数以 - 开头或从 stdin 读取脚本时使用 -- args

  --ini            显示配置文件名

  --rf <name>      显示关于函数 <name> 的信息。
  --rc <name>      显示关于类 <name> 的信息。
  --re <name>      显示关于扩展 <name> 的信息。
  --rz <name>      显示关于 Zend 扩展 <name> 的信息。
  --ri <name>      显示关于扩展 <name> 的配置。
```

## "php -m" - 内置模块

本节提供了一个教程示例，介绍如何获取预编译进 PHP 引擎的所有模块列表：`php -m`。

PHP 7.3 引擎的 Windows 二进制版本预编译了许多模块。`-m` 选项可以列出所有内置模块：

```
herong> \php\php -m

[PHP Modules]
bcmath
calendar
Core
ctype
date
dom
filter
hash
iconv
json
libxml
mysqlnd
pcre
PDO
Phar
readline
Reflection
session
SimpleXML
SPL
standard
tokenizer
wddx
xml
xmlreader
xmlwriter
zip
zlib

[Zend Modules]
```

## "php -i" - PHP 引擎信息

本节提供了一个教程示例，介绍如何获取关于 PHP 引擎及其执行环境的更多信息：`php -i`。

如果你想了解更多关于 PHP 引擎及其执行环境的信息，可以使用 `-i` 选项运行 `php.exe` 程序：

```
herong> \php\php -i

phpinfo()
PHP Version => 7.3.0

System => Windows NT Local 6.1 build 7601 (Windows 7 Professional ...
Build Date => Dec  6 2018 01:48:44
Compiler => MSVC15 (Visual C++ 2017)
Architecture => x64
Configure Command => cscript /nologo configure.js  "--enable-snaps...
Server API => Command Line Interface
Virtual Directory Support => enabled
Configuration File (php.ini) Path => C:\windows
Loaded Configuration File => (none)
Scan this dir for additional .ini files => (none)
Additional .ini files parsed => (none)
PHP API => 20180731
PHP Extension => 20180731
Zend Extension => 320180731
Zend Extension Build => API320180731,TS,VC15
PHP Extension Build => API20180731,TS,VC15
Debug Build => no
Thread Safety => enabled
Zend Signal Handling => disabled
Zend Memory Manager => enabled
Zend Multibyte Support => disabled
IPv6 Support => enabled
DTrace Support => disabled

Registered PHP Streams => php, file, glob, data, http, ftp, zip, ...
Registered Stream Socket Transports => tcp, udp
Registered Stream Filters => convert.iconv.*, mcrypt.*, mdecrypt....

This program makes use of the Zend Scripting Language Engine:

...
```

## php.ini - PHP 运行时配置

本节描述 PHP 运行时配置文件 `php.ini`。

PHP 的运行时行为可通过 `\php` 文件夹中的名为 `php.ini` 的运行时配置文件进行控制。PHP 安装包提供了 2 个版本的 `php.ini`：

```
php.ini-development   - 更安全且性能更好
php.ini-production    - 错误消息更详细
```

既然我们是在本地机器上运行 PHP 以学习 PHP 语言，我们应该使用 `php.ini-development` 版本。因此，让我们将 `php.ini-development` 复制为 `php.ini`：

```
>copy \php\php.ini-development \php\php.ini
        1 file(s) copied.

>type \php\php.ini | more
[PHP]

;;;;;;;;;;;;;;;;;;;
; About php.ini   ;
;;;;;;;;;;;;;;;;;;;
; PHP's initialization file, generally called php.ini, is responsible
; for configuring many of the aspects of PHP's behavior.
; ...

; Name for user-defined php.ini files. Default is ".user.ini"
;user_ini.filename = ".user.ini"

; To disable this feature set this option to empty value
;user_ini.filename =

; TTL for user-defined php.ini files (time-to-live) in seconds.
; Default is 300 seconds (5 minutes)
;user_ini.cache_ttl = 300

; Enable the PHP scripting language engine under Apache.
engine = On

...
```

正如你所见，`php.ini` 文件非常易于使用。行首的 `;` 字符表示注释行。配置设置以 `name = value` 的格式提供。默认版本的 `php.ini` 包含大量注释，帮助你理解每项设置的含义。

