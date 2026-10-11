

```
import_request_variables("GPC",$prefix);
```

其中 "GPC" 表示从 `$_GET`、`$_POST` 和 `$_COOKIE` 复制的键值对将被注册为局部变量。`$prefix` 定义一个要添加到变量名前面的前缀字符串。

为了测试这一点，我在 `php.ini` 中开启了 `register_globals` 设置，并编写了这个示例脚本 `RequestVariables.php`：

```
<?php
#  RequestVariables.php
#- Copyright 2003 (c) HerongYang.com. All Rights Reserved.
#
   print "<pre>\n";
   print "\nContents of \$_REQUEST:\n";
   foreach ($_REQUEST as $k => $v) {
      print "   $k = $v\n";
   }
#
   print "\nLocal imported variables from the request:\n";
   import_request_variables("GPC","r_");
   print "   \$r_lang = $r_lang\n";
   print "   \$r_search = $r_search\n";
#
   print "\nGlobally imported variables from the request:\n";
   print "   \$lang = $lang\n";
   print "   \$search = $search\n";
   print "</pre>\n";
?>
```

使用 `http://localhost/RequestVariables.php?lang=PHP&search` 打开此脚本，你将得到：

```
Contents of $_REQUEST:
   lang = PHP
   search =

Local imported variables from the request:
   $r_lang = PHP
   $r_search =

Globally imported variables from the request:
   $lang = PHP
   $search =
```

# PHP 教程 - Herong 的教程示例

## 在 PHP 脚本中创建和管理会话

本章提供关于会话的教程示例和说明。主题包括理解会话概念；编写脚本以创建和使用会话；在当前会话中存储数据；将会话 ID 作为 Cookie 和 URL 透明参数进行管理。

> [什么是会话](#part0108.xhtml)
>
> [PHP 如何支持会话](#part0109.xhtml)
>
> [SessionPage*.php - 会话测试脚本页面](#part0110.xhtml)
>
> [运行会话测试脚本页面](#part0111.xhtml)
>
> [不使用 Cookie 管理会话 ID](#part0112.xhtml)
>
> [会话数据存储在哪里](#part0113.xhtml)

### 要点：

*   会话 ID 必须在 HTTP 请求和响应之间传递，以将它们链接成一个单一序列。
*   将会话 ID 作为 Cookie 值传递更安全。
*   将会话 ID 作为透明 URL 变量传递安全性较低，因为会话 ID 将显示在网页地址栏中。
*   你必须在 PHP 脚本开头调用内置函数 `session_start()` 来启动一个新会话，或继续一个现有会话。
*   内置数组 `$_SESSION` 可用于将信息从一个脚本传递到另一个与第一个脚本共享同一会话的脚本。
*   会话数据在服务器端永久持久化到硬盘。

# PHP 教程 - Herong 的教程示例

## 在 PHP 脚本中创建和管理会话

### 什么是会话

本节描述 Web 服务器端应用程序使用的会话概念。Web 会话表示浏览器和 Web 服务器之间交换的一系列 HTTP 请求和响应。通常，使用 Cookie 来携带 Web 会话的 ID。

#### 什么是会话？

会话是一个抽象概念，用于表示特定 Web 浏览器和特定 Web 服务器之间交换的一系列 HTTP 请求和响应。会话概念对于基于 Web 的应用程序非常有用，可用于将信息从一个网页（请求）传递并共享到另一个网页（请求）。

由于 HTTP 协议的当前设计不支持会话概念，所有 Web 服务器端脚本技术（包括 PHP）都设计了自己的方式来支持会话概念。会话支持的关键设计要素在于如何用 ID（标识）来标识会话以及如何维护会话 ID。维护会话 ID 的一种常用方法是使用 Cookie 技术。下图展示了如何做到这一点：

```
           Server                Browser
ID created  | <-- Request #1  --- |
            | --- Response #1 --> | ID kept as cookie
            | <-- Request #2  --- | ID send back to server
            | --- Response #2 --> |
            | <-- Request #3  --- | ID send back to server
            | --- Response #3 --> |
            |     ......          |
```

会话概念应由服务器管理。当来自客户机上浏览器的第一个请求到达时，服务器应创建一个新会话，并分配一个新的会话 ID。然后会话 ID 将作为 Cookie 发送回同一个浏览器。浏览器将记住此 ID，并在后续请求中将 ID 发送回服务器。当服务器收到包含相同会话 ID 的请求时，它知道该请求是现有会话的延续。

当服务器收到来自新客户机上浏览器的请求（不带会话 ID 的请求）时，服务器不仅应创建一个新的会话 ID，还应创建一个与新会话 ID 关联的新会话对象。此会话对象应成为同一会话的不同请求存储和共享信息的存储位置，这些请求包含相同的会话 ID。

如果很长一段时间内没有后续请求针对特定的会话 ID 返回，该会话应超时。会话超时后，如果浏览器再次带着相同的会话 ID 返回，服务器应给出无效会话错误。

# PHP 教程 - Herong 的教程示例

## 在 PHP 脚本中创建和管理会话

### PHP 如何支持会话

本节描述 PHP 如何支持会话。会话 ID 作为 Cookie 或 GET/POST 变量传递。`session_start()` 是启动会话的内置函数。`$_SESSION` 是管理会话数据的内置数组。

PHP 在配置文件 `php.ini` 中通过以下主要元素支持 Web 会话：

1.  `session.use_cookies = 1/0` - 一个设置，用于确定会话 ID 是否应作为 Cookie 存储和管理。
    *   `session.use_cookies = 1`（默认设置） - 作为 Cookie 管理会话 ID。会话 ID 存储在一个默认名为 "PHPSESSID" 的 Cookie 中。此 "PHPSESSID" Cookie 将由 PHP 引擎自动插入 HTTP 响应并从 HTTP 请求中检索。
    *   `session.use_cookies = 0` - 停止将会话 ID 作为 Cookie 存储。

2.  `session.use_trans_sid = 1/0` - 配置文件 `php.ini` 中的一个设置，用于控制会话 ID 是否应作为 URL 中的透明参数存储和管理。
    *   `session.use_trans_sid = 1` - 作为 URL 中的额外透明参数管理会话 ID。额外的 URL 参数包含默认名为 "PHPSESSID" 的会话 ID 值。此 "PHPSESSID" 参数将由 PHP 引擎自动插入 HTTP 响应中的所有链接，并从 HTTP 请求中检索。
    *   `session.use_trans_sid = 0`（默认设置） - 停止将会话 ID 作为 URL 透明参数存储。

3.  `session.save_handler = files/mm/user` - 配置文件 `php.ini` 中的一个设置，用于控制会话数据应如何存储。
    *   `session.save_handler = files`（默认设置） - 将会话数据作为文件存储在 `session.save_path = "/tmp"` 设置定义的目录中。
    *   `session.save_handler = mm` - 将会话数据存储在共享内存中。
    *   `session.save_handler = user` - 通过用户定义的函数存储会话数据。

4.  `session_start()` - 一个用于创建新会话或恢复现有会话的内置函数。调用 `session_start()` 时，PHP 引擎将检查当前 HTTP 请求，以查看是否包含现有会话 ID。
    *   如果未找到会话 ID，PHP 引擎将创建一个带有新会话 ID 的新会话。
    *   如果找到会话 ID，PHP 引擎将恢复由此会话 ID 标识的会话。如果恢复的会话已超时，将发出错误。

