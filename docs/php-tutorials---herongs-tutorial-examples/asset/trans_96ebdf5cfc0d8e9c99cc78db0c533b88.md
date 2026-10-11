

# PHP 引擎和 `$_SERVER` 数组

PHP 引擎还会从 Web 服务器收集额外信息，并将其作为键和值存储在 `$_SERVER` 数组中。例如，以下键和值代表从 Web 服务器接收到的信息：

```
SERVER_SIGNATURE =
SERVER_SOFTWARE = Apache/2.4.37 (Win64)
SERVER_NAME = localhost
SERVER_ADDR = ::1
SERVER_PORT = 80
REMOTE_ADDR = ::1
DOCUMENT_ROOT = C:/apache/htdocs
REQUEST_SCHEME = http
CONTEXT_PREFIX = /cgi-bin-php/
CONTEXT_DOCUMENT_ROOT = /local/php/
......
```

PHP 引擎还会从运行 PHP 引擎的操作系统收集额外信息，并将其作为键和值存储在 `$_SERVER` 数组中。例如，以下键和值代表从操作系统接收到的信息：

```
SystemRoot = C:\windows
COMSPEC = C:\windows\system32\cmd.exe
PATHEXT = .COM;.EXE;.BAT;.CMD;.VBS;.VBE;.JS;.JSE;.WSF;.WSH;.MSC
WINDIR = C:\windows
...
```

---

# `$_SERVER` 中的操作系统信息

本节提供了一个教程示例，演示如何转储存储在 `$_SERVER` 数组中的操作系统信息。

为了帮助我们理解预定义变量 `$_GET`、`$_POST`、`$_COOKIE`、`$_REQUEST` 和 `$_SERVER` 的工作原理，我编写了以下教程示例脚本：

```php
<?php
#  HttpRequestDetails.php
#- Copyright 2003 (c) HerongYang.com. All Rights Reserved.
#
   print "<pre>\n";
   print "\nContents of \$_GET:\n";
   foreach ($_GET as $k => $v) {
      print "   $k = $v\n";
   }
#
   print "\nContents of \$_POST:\n";
   foreach ($_POST as $k => $v) {
      print "   $k = $v\n";
   }
#
   print "\nContents of \$_COOKIE:\n";
   foreach ($_COOKIE as $k => $v) {
      print "   $k = $v\n";
   }
#
   print "\nContents of \$_REQUEST:\n";
   foreach ($_REQUEST as $k => $v) {
      print "   $k = $v\n";
   }
#
   print "\nContents of \$_SERVER:\n";
   foreach ($_SERVER as $k => $v) {
      print "   $k = $v\n";
   }
   print "</pre>\n";
?>
```

如果你在不使用任何 Web 服务器的情况下独立运行此示例脚本，你应该会得到：

```
<pre>

Contents of $_GET:

Contents of $_POST:

Contents of $_COOKIE:

Contents of $_REQUEST:

Contents of $_SERVER:
   ALLUSERSPROFILE = C:\ProgramData
   CommonProgramFiles = C:\Program Files\Common Files
   CommonProgramFiles(x86) = C:\Program Files (x86)\Common Files
   CommonProgramW6432 = C:\Program Files\Common Files
   ComSpec = C:\windows\system32\cmd.exe
   configsetroot = C:\windows\ConfigSetRoot
   FP_NO_HOST_CHECK = NO
   ProgramData = C:\ProgramData
   ProgramFiles = C:\Program Files
   ProgramFiles(x86) = C:\Program Files (x86)
   ProgramW6432 = C:\Program Files
   PROMPT = $P$G
   ......
</pre>
```

请注意，`$_GET`、`$_POST`、`$_COOKIE` 和 `$_REQUEST` 都是空的，因为我们在没有任何 HTTP 请求的情况下执行了脚本。`$_SERVER` 仅包含从操作系统收集的信息。

---

# `$_SERVER` 中的 Web 服务器信息

本节提供了一个教程示例，演示如何转储存储在 `$_SERVER` 数组中的 Web 服务器信息。

现在，让我们在本地 Apache Web 服务器上运行 `HttpRequestDetails.php`。首先将 `HttpRequestDetails.php` 复制到 `\apache\htdocs`，然后使用 `http://localhost/HttpRequestDetails.php` 在 Internet Explorer (IE) 中运行。你应该会得到：

```
Contents of $_GET:

Contents of $_POST:

Contents of $_COOKIE:

Contents of $_REQUEST:

Contents of $_SERVER:
   REDIRECT_HANDLER = application/x-httpd-php
   REDIRECT_STATUS = 200
   HTTP_HOST = localhost
   HTTP_CONNECTION = keep-alive
   HTTP_UPGRADE_INSECURE_REQUESTS = 1
   HTTP_REFERER = http://localhost/
   HTTP_ACCEPT_ENCODING = gzip, deflate, br
   HTTP_ACCEPT_LANGUAGE = en-US,en;q=0.9
   SystemRoot = C:\windows
   COMSPEC = C:\windows\system32\cmd.exe
   PATHEXT = .COM;.EXE;.BAT;.CMD;.VBS;.VBE;.JS;.JSE;.WSF;.WSH;.MSC
   WINDIR = C:\windows
   SERVER_SIGNATURE =
   SERVER_SOFTWARE = Apache/2.4.37 (Win64)
   SERVER_NAME = localhost
   SERVER_ADDR = ::1
   SERVER_PORT = 80
   REMOTE_ADDR = ::1
   DOCUMENT_ROOT = C:/apache/htdocs
   ......
```

请注意，`$_GET`、`$_POST`、`$_COOKIE` 和 `$_REQUEST` 仍然全为空，因为 HTTP 请求不包含使用 GET 或 POST 方法提交的信息。并且 HTTP 请求中没有 Cookie。

然而，HTTP 请求中包含的其他信息以及从 Web 服务器收集的信息现在存储在 `$_SERVER` 数组中。例如，`DOCUMENT_ROOT = c:/apache/htdocs` 是来自 Web 服务器的一条信息，告诉我们 Web 服务器从 `c:/apache/htdocs` 目录获取 HTTP 文档和脚本。

---

# `$_GET` 和 `$_REQUEST` 中的信息

本节提供了一个教程示例，演示如何转储存储在 `$_GET` 数组和 `$_REQUEST` 数组中的信息。

现在尝试此 URL：`http://localhost/HttpRequestDetails.php?lang=PHP&search`。你应该会得到：

```
Contents of $_GET:
   lang = PHP
   search =

Contents of $_POST:

Contents of $_COOKIE:

Contents of $_REQUEST:
   lang = PHP
   search =

Contents of $_SERVER:
   ......
   QUERY_STRING = lang=PHP&search
   ......
```

请注意：

*   附加在 URL 末尾的 `?lang=PHP&search` 代表使用 GET 方法提交的信息。
*   `?lang=PHP&search` 被 PHP 引擎解析为 2 对名称和值，并存储在 `$_GET` 数组中。
*   PHP 引擎将相同的信息从 `$_GET` 复制到了 `$_REQUEST`。

请注意，如果你正在迁移早于 PHP 5.4.0 的脚本，你可能会发现 `$_POST`、`$_COOKIE` 和 `$_REQUEST` 中引号传递方式的突然变化。

在 PHP 5.4.0 之前，PHP 引擎有一个名为 `magic_quotes_gpc` 的默认选项，它为 GPC（Get/Post/Cookie）操作开启了 `magic_quotes` 状态。当 `magic_quotes` 状态开启时，所有 `'`（单引号）、`"`（双引号）、`\`（反斜杠）都会自动用反斜杠转义。

因此，早于 PHP 5.4.0 的脚本正在使用 `stripslashes()` 函数调用来清理在 `$_POST`、`$_COOKIE` 和 `$_REQUEST` 中接收到的值。

现在你必须从旧脚本中移除那些 `stripslashes()` 函数调用。如果不移除，从客户端接收的值可能会被破坏。例如，`\\` 将被接收为 `\`。

**练习：** 尝试找到一种方法来测试如何使用 POST 方法提供信息以及如何提供 Cookie。

---

# 将 `$_REQUEST` 键注册为全局变量

本节提供了一个教程示例，演示如何将 `$_REQUEST` 数组中的键和值提升（或注册）为全局变量，这样你就不必使用数组符号来访问它们的值。

要访问存储在 `$_REQUEST` 数组中的信息，可以使用正常的数组元素符号 `$_REQUEST[$key]`。例如，在上一节使用的示例脚本中，`$_REQUEST["lang"]` 将返回 "PHP"。

但 `$_REQUEST` 中的键值对也可以通过以下两种方式之一提升（或注册）为独立的全局变量：

1.  要在整个服务器上将 `$_REQUEST` 键值对注册为全局变量，请编辑 `\php\php.ini` 并设置：

```
register_globals = on
```

使用此设置，PHP 引擎将自动为 `$_REQUEST` 中的每个键创建一个全局变量，并将键名作为变量名。当然，与键关联的值将同时被复制到变量中。例如，如果 `$_REQUEST["lang"]` 包含 "PHP"，则将创建 `$lang` 并赋值为 "PHP"。

2.  要仅为当前脚本执行将 `$_REQUEST` 键值对注册为局部变量，请使用以下函数：

