

# 列表 18.1 需要身份认证

```php
<?
/*
** 定义两个函数，用于
** 开始和结束一个 HTML 文档
*/
function startGame() {
    print("<HTML\n");
    print("<HEAD>\n");
    print("<TITLE>Listing 18.1</TITLE>\n");
    print("</HEAD>\n");
    print("<body>\n");
}

function endPage() {
    print("</BODY>\n");
    print("</HTML>\n");
}
/*
** 用于用户名/密码的测试服务器
*/
if(($PHP_AUTH_USER == "leon") AND ($PHP_AUTH_PW == "secret")) {
    startPage();
    print("You have logged in successfully!<BR>\n");
    endPage();
} else {
    //发送头信息导致浏览器向用户
    //请求用户名和密码
    header("WWW-Authenticate: Basic realm=\"Leon's Protected Area\");
    header("HTTP/1.0 401 Unauthorized");

    //显示失败文本
    print("This page is protected by HTTP Authentication.<br>\n");
    print("Use <B>leon</B> for the username, and <B>secret</B> ");
    print("for the password.<br>\n");
}
?>

# PHP 核心编程

现在你已经知道如何保护页面，但反向操作——即请求一个受保护的页面——可能会很有启发性。正如我之前提到的，`fopen` 函数允许你将用户名和密码作为 URL 的一部分，但可能会遇到更复杂的情况，此时需要使用 `fsockopen`。认证请求头是必要的。该头的值是由冒号分隔的用户名和密码：这是 base64 编码的，符合 HTTP 规范。

列表 18.2 请求了列表 18.1 中的脚本。你可能需要修改 URI 以便在你的 Web 服务器上运行。该脚本假设你已经在 Web 服务器的 `/corephp/listings` 下安装了所有示例。如果你对每行末尾的 `\r\n` 感到好奇，请记住发送到 HTTP 服务器的所有行都必须以回车符和换行符结束。

# 列表 18.2 请求受保护的文档

```php
<?php
//打开套接
if(!$fp = fsockopen("localhost", 80))
{
    print("Couldn't open socket!<BR\n");
    exit;
}

//请求文档
fputs($fp, "HEAD /corephp/listings/18-1.php\nHTTP/1.0\r\n");

//发送用户名和密码
fputs($fp, "Authorization: Basic " 
base64_encode("leon:secret") 
."\r\n");

//结束请求
fputs($fp, "\r\n");

//转储服务器的响应
passthru($fp);
?>
```

# 控制浏览器缓存

编写动态 Web 页面的一个麻烦点是缓存的行为。浏览器维护自己的缓存，默认情况下，它们每个会话只检查一次新版本的页面。某些 ISP 也会提供自己的缓存。其意图是避免页面的浪费重新传输。然而，如果你的页面内容每次请求都可能发生变化，那么出现旧版本就会非常困扰。如果你正在开发电子商务网站，确保每个页面都重新处理是关重要的。

另一方面，你的页面可能会动态构建一个包含不经常变化信息的页面。我的经验是，缓存足以存储看起来像普通 HTML 文件的 URL，但不能存储带有问号后变量的 URL。不过，你的 PHP 可能会在 URL 中使用变量。如果这些页面上的信息频繁变化，你想让缓存知道这一点。

RFC 2616 描述了 HTTP 1.1 协议，它提供了几个控制缓存的头信息。列表 18.3 显示了防止页面被缓存的头信息。`Last-Modified` 头报告文档最后修改的时间，将其设置为当前时间会告诉浏览器此版本的页面是新鲜的。`Expires` 头告诉浏览器此版本的文档何时会再次被请求。我们再次使用当前时间，希望让浏览器将该文档排除在缓存之外。也许最重要的头信息 `Cache-Control` 告诉浏览器缓存该页面。在这种情况下，请求页面是为了那些只理解 HTTP 1.0 的旧浏览器。尝试重新加载列表 18.3 中的脚本。你应该会看到日期每次更新一次。

# 列表 18.3 发送头信息以防止缓存

```php
<?php
  header("Last-Modified: " . gmmdate("D, d M Y H:i:s"));
?>
```

列表 18.4 导致页面被缓存 24 小时。与列表 18.3 类似，`Last-Modified`、`Expires` 和 `Cache-Control` 头用于控制缓存行为。最后修改时间作为文件的实际修改时间发送。过期时间被设定为现在 24 小时。缓存被指示让文档老化 86400 秒（一天的秒数）。为了向自己证明文件是从缓存返回的，请快速重新加载页面。页面上的日期应该保持不变。

注意，这两个示例中的所有日期都使用 GMT（格林尼治标准时间）。这是 HTTP 协议规定的。忘记从你的本地时区转换为 GMT 可能会成为一个恼人的 Bug 来源。

# 列表 18.4 发送头信息以鼓励缓存

```php
<?php
//报告脚本的实际修改时间
$LastModified = filetime(__FILE__) + date("Z");
header("Last-Modified: " . gmdate("D, d M Y H:i:s", $LastModified) . " GMT");

//设置过期时间为现在 24 小时（86400 秒）
$Expires = time() + 86400;
header("Expires: " . gmdate("D, d M Y H:i:s", $Expires) . " GMT");

//告诉缓存页面最后 24 小时（86400 秒）
header("Cache-Control: max-age=86400");
?>
<html>
<HEAD>
<TITLE>Listing 18.4</TITLE>
</HEAD>
<BODY>
The time is <?php print(gmdate("D, d M Y H:i:s")); ?> GMT<BR>
<BR>
This document was last modified
<?php print(gmdate("D, d M Y H:i:s", $LastModified)); ?> GMT<BR>
It expires
<?php print(gmdate("D, d M Y H:i:s", $Expires)); ?> GMT<BR>
</BODY>
</</html>
```

# 设置文档类型

默认情况下，PHP 发送的 HTTP 头指定文档为 HTML。`Content-Type` 头指定 MIME 类型 `text/html`，浏览器会将代码解释为 HTML。有时你希望用 PHP 创建其他类型的文档。你将在第 19 章“生成图形”中学习创建图像，这可能需要 `image/png` MIME 类型。MIME 类型由 IANA 管理。你可以在这里找到官方媒体类型列表：http://www.isi.edu/in-notes/assignments/media-types/。

有时，你可能会利用浏览器对不同内容的反应。例如，`text/plain` 会以等宽字体显示且不解释 HTML。如果你对内容使用 `text/plain`，浏览器会显示保存文件的对话框。也许最有趣的用法是启动辅助应用程序。

列表 18.5 创建了一个可能会启动 Microsoft Excel 的制表符文件。

