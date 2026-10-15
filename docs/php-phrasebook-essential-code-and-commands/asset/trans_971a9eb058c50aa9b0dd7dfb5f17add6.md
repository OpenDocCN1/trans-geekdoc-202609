
## 去除 Cookie 中的“魔术引号”

如果启用了 magic_quotes，则 stripslashes() 会递归应用于 $_COOKIE 中的所有数据。

```php
<?php
function stripCookieSlashes($arr) {
    if (!is_array($arr)) {
        return stripslashes($arr);
    } else {
        return array_map('stripCookieSlashes', $arr);
    }
}

if (get_magic_quotes_gpc()) {
    $_COOKIE = stripCookieSlashes($_COOKIE);
}
?>
```

*从 Cookie 中移除“魔术引号”（stripCookieSlashes.inc.php）*

此文件随后应包含在读取 cookie 的所有 PHP 脚本中，使用以下语句：

```
require_once 'stripCookieSlashes.inc.php';
```

## 设置（合理的）过期日期

Cookie 的过期日期是 setcookie() 的第三个参数。它是一个整数值；因此必须使用时间戳的 epoch 值。第 3 章“日期和时间”包含有关如何处理此类信息的大量信息。

```php
<?php
    setcookie('version', phpversion(), time() +
        21*24*60*60);
?>
```
尝试发送 cookie。

*使用相对过期日期设置 Cookie（setcookie-expiry.php）*

通常，为 cookie 设置相对过期日期（“三周后”）是一个好主意，而不是绝对日期（“2006 年 5 月底”）。如果使用绝对日期，你可能需要定期更改脚本，因为绝对过期日期可能很快到来。将过期日期设置为遥远的未来，例如 2030 年，也被认为是非常不专业的。接收此 cookie 的客户端到那时很可能早已被淘汰。

因此，使用相对日期。PHP 函数 time() 获取当前 epoch 值；然后加上你希望 cookie 存活的秒数。本段开头的代码设置了一个将存在三周的 cookie。

## 设置客户端特定的过期日期

```
setcookie('version', phpversion(),
    $_GET['time'] + 21*24*60*60);
```

请记住，cookie 何时过期的决定是在客户端做出的，使用客户端的时间设置。因此，如果客户端的日期错误（这是服务器端无法控制的）。

你的 cookie 可能比你预期的更早过期。因此，不要尝试设置仅存活一小时左右的 cookie；像夏令时（DST）这样的小事就可能破坏你的计划。

```php
<?php
if (isset($_GET['time']) && is_int($_GET['time']))
{
    setcookie('version', phpversion(),
        $_GET['time'] + 21*24*60*60);
} else {
    setcookie('version', phpversion(),
        time() + 21*24*60*60);
}
?>
```
尝试发送 cookie。

*使用特定过期日期设置 Cookie（setcookie-specific.php）*

然而，通过一点 JavaScript，可以避免这个陷阱。以下列表中的代码是客户端 JavaScript 代码，它以 epoch 值确定当前时间（客户端！）并将其发送到服务器端脚本 setcookie-specific.php。PHP 的 time() 函数与 JavaScript 的 getTime() 方法之间的主要区别在于，后者返回自 1970 年 1 月 1 日以来的毫秒数，而前者仅使用秒数。因此，JavaScript 值首先必须除以 1,000 并向下取整。

本段开头的代码可以查看此文件：传输的值被用作计算相对 cookie 过期日期的基础。

```html
<script language="JavaScript"
    type="text/javascript"><!--
    var epoche = (new Date()).getTime();
    epoche = Math.floor(epoche / 1000);
    location.replace("setcookie-specific.php?time=" +
        epoche);
//--></script>
```

## 删除 Cookie

```
setcookie('version', '', time() - 10*365*24*60*60);
```

直观地删除 cookie 的方法是将其值设置为空字符串。然而，cookie 仍然存在，只是没有值。更好的方法是再次发送一个同名的 cookie，但提供一个在过去的过期日期。同样，必须考虑不正确的本地时间设置，因此使用一个非常小的过期日期，例如今天之前 10 年。此列表实现了这一点并删除了之前列表中发送的 version cookie。在这里，两种方法结合使用：cookie 值被设置为空字符串，并且过期日期在过去。图 5.4 显示了结果：浏览器尝试通过将过期日期设置为期望时间（该时间在过去，因此 cookie 已消失）来删除 cookie。

```php
<?php
    setcookie('version', '', time() -
        10*365*24*60*60);
?>
```
尝试删除 cookie。

删除 Cookie（deletecookie.php）

![](img/1e6d362f187af50011d2666ddaa68739_145_0.png)

图 5.4 cookie 将被删除（如果用户接受）。

警告
如果尝试将过期日期设置为 0，PHP 只是跳过此参数，因此不起作用。你必须提供一个正参数，即使是 1。

## 使 Cookie 可供多个域访问

```
setcookie('version', phpversion(), 0, '.example.com');
```

服务器发送的 Set-Cookie 头的一部分是有权访问此 cookie 的域。如果未明确发送，此值默认为发送 cookie 的域。将此域设置为完全不同的值，例如广告服务器的域（所谓的第三方 cookie；用于尝试生成用户画像），并不总是有效，因为许多浏览器允许专门禁用该功能。（参见图 5.5，了解旧版 Netscape 4.x 浏览器的示例，该浏览器已具备此功能。）

```php
<?php
    setcookie('version', phpversion(), 0,
        '.example.com');
?>
```
尝试发送 cookie。

*为 Cookie 设置域（setcookie-domain.php）*

![](img/1e6d362f187af50011d2666ddaa68739_146_0.png)

图 5.5  即使是 Netscape 4.x 也允许你阻止不使用源域的 cookie。

然而，在某些情况下，要求 cookie 在多个三级域或子域上工作，例如 www.example.com、store.example.com 和 ssl.example.com。这方面的例子是拥有许多子域的大型网站，如 Amazon 和 eBay。它们要求支持所有顶级域（TLD）。为此，必须设置 cookie 的域——setcookie() 的第四个参数。这里有一个技巧：

只要包含两个点，所有域名都是有效的。因此，如果将域设置为“.example.com”，example.com 的所有三级域都可以访问此 cookie。这里有一个“但是”：http://example.com/ 上的页面无法访问此 cookie。因此，你可能想尝试将域设置为“example.com”；然而，这不符合规范，并且可能不被所有浏览器支持。

## 检查客户端是否支持 Cookie

```php
$test_temp = isset($_COOKIE['test_temp']) ?
'supports' : 'does not support';
$test_persist = isset($_COOKIE['test_persist']) ?
'supports' : 'does not support';
```

请记住 cookie 的发送方式：首先，服务器作为 HTTP 响应的<|message|>一部分将 cookie 发送给客户端。在下一个请求中，如果接受，客户端会将 cookie 发送回。因此，调用 setcookie() 然后检查 $_COOKIE 的内容是无效的。你必须等待下一个 HTTP 请求。

```php
if (isset($_GET['step']) && $_GET['step'] == '2')
{
$test_temp = isset($_COOKIE['test_temp']) ?
'supports' : 'does not support';
$test_persist = isset($_COOKIE['test_persist']) ?
'supports' : 'does not support';
setcookie('test_temp', '', time() - 365*24*60*60);
setcookie('test_persist', '', time() - 365*24*60*60);
echo "Browser $test_temp temporary cookies.<br />";
echo "Browser $test_persist persistent cookies.";
} else {
setcookie('test_temp', 'ok');
setcookie('test_persist', 'ok', time() +
14*24*60*60);
header("Location: ".$_SERVER['PHP_SELF']."?step=2");
}
?>
```

*测试浏览器 Cookie 配置（cookietest.php）*

然而，你可以使用 header() 强制客户端创建第二个请求。在第一个请求中，你设置 cookie；在第二个请求中，你检查是否成功。

在之前的代码中，设置了两个 cookie，一个临时 cookie 和一个持久 cookie——因为可以配置某些浏览器以接受一种 cookie 而不接受另一种。然后，使用 header() 和 Location: HTTP 头进行重定向，并检查 cookie(s) 的存在。

当然，你应该配置浏览器在 cookie 到达时显示消息窗口；这使得调试变得容易得多。
