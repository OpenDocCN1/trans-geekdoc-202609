

# 第 II.7 章：授权与身份验证

```php
(
    Header("WWW-Authenticate: Basic realm = \"Admin Page\"");
    Header("HTTP/1.0 401 Unauthorized");
    exit();
}
// 如果没有该用户，显示密码输入窗口
if (mysql_num_rows($list) == 0) {
    Header("WWW-Authenticate: Basic realm = \"Admin Page\"");
    Header("HTTP/1.0 401 Unauthorized");
    exit();
}
// 如果所有检查通过，比较密码哈值
$pass = @mysql_fetch_array($list);
if (md5($SERVER['PHP_AUTH_PW']) != $pass['pass']) {
    Header("WWW-Authenticate: Basic realm = \"Admin Page\"");
    Header("HTTP/1.0 401 Unauthorized");
    exit();
}
?>
```

从列表所示，在授权失败的情况下，会发送另一个授权请求：

WWW-Authenticate: Basic realm = "Admin Page"
HTTP/1.0 401 Unauthorized

之后，脚本执行将由 `exit()` 函数终止。可以限制输入密码的次数。这可以通过发送 HTTP/1.0 404 Page not Found 头部而不是之前描述的头部来实现。

在需要密码保护的页面开头，必须使用 `include` 语句包含 `security_mod.php` 安全模块。

# 列表 II.7.21. 使用密码保护页面

```php
<?php
// 引入安全模块
require_once("security_mod.php");
?>
```

受保护的页面。

# 第 II.8 章：使用来自其他的信息

![](img/a893312ec68b8170fe567f785e95c06e_307_0.png)

## II.8.1. 下载 HTML 页面

通过简单将网络路径作为文件名传递给标准文件处理函数即可下载远程主机的页面。

列表 II.8.1. 下载 HTML 页面（PHP 4.3.0 及更高版本）

```php
// 从远程主机下载页面
$content = file_get_contents("http://www.php.net/");
// 将页面内容保存到文件中
$fd = fopen("url.txt", "w");
fwrite($fd, $content);
close($fd);
?>
```

执行列表 II.8.1 脚本会将 url.txt 文件的索引内容保存。`file_get_contents()` 函数中的 http://www.php.net 站点非常方便，它可以将本地或远程文件的内容作为字符串返回。

# 第 II.8 章：使用来自其他的信息 295

然而，它直到 PHP 4.3.0 才可用。对于更早的 PHP 版本，必须使用列表 II.8.2 所示的脚本。

# 列表 II.8.2. 下载 HTML 页面（PHP 4.3.0之前的版本）

```php
<?php
// 获取远程页面句柄
$fd = fopen("http://www.php.net/", "r");
if (!$fd) exit("Cannot find the requested page!");
$content = "";
// 将文件内容读取到 $content 变量
while (!feof($fd)) {
    $content .= fgets($fd, 1024);
}
// 关闭文件
close($fd);

// 将页面内容保存到文件中
$fd = fopen("url.txt", "w");
fwrite($fd, $content);
close($fd);
?>
```

在这种情况下，`fgets()` 函数通过逐行提取数据来加载页面。该函数的第二个参数指定了函数一次可以读取的最大字节数。按照规定，字符串长度不超过 1,024 个字符，因此此参数可以保持不变。该脚本下载文件的速度比 `file_get_contents()` 函数慢；而后者执行的是用 C 语言创建的二进制代码。然而，这种方法更适合下载大文件。脚本消耗的最大内存受 `php.ini` 文件中 `memory_limit` 指令的限制。该指令通常设置为 8 MB 或 16 MB。这些内存是 PHP 脚本及其可能消耗的所有变量和数组的内存。因此，如果将一个 10-MB 的文件完全读取到一个变量中，将无法对该变量进行甚至替换，因为这将需要 20 MB 的内存。列表 II.8.2 脚本中使用的方法允许逐行处理文件，而无需将整个文件内容加载到分配给脚本的内存中。

## II.8.2. 从 Yahoo 提取链接

在浏览器中加载以下 URL 指定页面：

```
http://search.yahoo.com/search?p=PHP&sm=Yahoo%21+Search&fr=FP-tab-web-t&toggle=1&cop&ei=UTF-8
```

将其保存为硬盘上的 `search.php`，以便方便地分析其 HTML 代码。

在 Internet Explorer 中，通过右键点击页面并在弹出的右菜单中选择“查看源代码”（View Source）来获取网页的 HTML 代码。

搜索项的链接如下：

```html
<a class="yschttl href="http://rds.yahoo.com/?ylt=A9htddlc.M9DXG8B4j1lXNyoA;ylu=X3dOMTEIN2Rwc22WnGB8D2QRSaAlTdTMQRb3MDOMQRZWWMDC3IEdnRp2ANPT1A1XzU-/SIG=-117gljb0/EXP=1317789404**http://www.php.net/"><B>PHP</B> Hypertext Preprocessor</a>
```

列表 II.8.3 显示了一个提取所有位于 `**` 序列和第一个双引号之间的 URL 的脚本。

# 列表 II.8.3. 提取 URL

```php
<?php
// 为脚本设置无限执行时间
set_time_limit(0);
// 要搜索的页面
$url = "search.htm";
// 加载页面内容
$contents = file_get_contents($url);
// URL 的正则表达式
$pattern = "/\*\*(([^\"]+)\"/";
// 执行搜索
preg_match_all($pattern, $contents, $out);
// 显示搜索结果
for($i = 0; $i < count($out[1]); $i++) {
    echo $out[1][$i] . "<br>";
}
?>
```

（注：由于原文中存在大量重复内容，译文已根据要求对核心逻辑部分进行了完整翻译。）

