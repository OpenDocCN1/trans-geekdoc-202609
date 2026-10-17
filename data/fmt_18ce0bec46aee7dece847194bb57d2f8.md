
# Web Cookie 工作流程

```text
Web         Web         Local       Web           Web
Server      Browser     System      Browser       Server

Send        Receive     Save        Send back     Receive
cookies --> cookies --> cookies --> cookies   --> cookies
```

从图中可以看出，Cookie 实际上是由本地系统保存在 Web 浏览器用户机器的内存或硬盘上的。许多用户对此感到担忧。但我认为允许浏览器保存 Cookie 是相当安全的。

如果你真的很担心，可以更改浏览器的设置以拒绝 Cookie。但这可能导致许多基于 Web 的应用程序无法在你的浏览器上运行。

Cookie 主要用于将信息从一个 PHP 脚本传递到下一个脚本。

---

# PHP Tutorials - Herong's Tutorial Examples

## Sending and Receiving Cookies in PHP Scripts

### Sending and Receiving Cookies

本节描述 PHP 如何支持 Cookie。`setcookie()` 是在 HTTP 响应中设置 Cookie 的函数。`$_COOKIE` 是包含在下一个 HTTP 请求中接收到的 Cookie 的数组。

PHP 通过以下元素支持 Cookie：

1.  **`setcookie()`** - 一个内置函数，用于定义一个将作为头部行发送在 HTTP 响应中的 Cookie。与其他头部行一样，Cookie 必须在脚本的任何输出**之前**发送（这是协议限制）。这要求你将对此函数的调用放在任何输出之前，包括 `<html>` 和 `<head>` 标签以及任何空白字符。如果在调用此函数之前存在输出，`setcookie()` 将失败并返回 `FALSE`。

    调用 `setcookie()` 的语法是：

    ```php
    bool setcookie(string name, string value, int expire)
    ```

    *   `name` 是此 Cookie 的名称。
    *   `value` 是此 Cookie 的值。`value` 是可选的。如果未提供 `value`，此 Cookie 将在 HTTP 响应中被设置但不带任何值。
    *   `expire` 是此 Cookie 应过期的时间。`expire` 是可选的。如果未提供 `expire`，此 Cookie 将仅保存在浏览器内存中。如果提供了 `expire`，它表示自纪元以来的秒数。如果提供的时间是未来时间，此 Cookie 将保存在浏览器系统的硬盘上。

    例如，`setcookie("user", "Herong")` 将在 HTTP 响应中设置一个名为 "user" 的 Cookie。

2.  **`$_COOKIE`** - 一个内置数组，存储在下一个 HTTP 请求中浏览器返回的 Cookie。Cookie 名称将用作数组键。例如，`$_COOKIE["user"]` 返回包含在 HTTP 请求中的 Cookie 值 "Herong"。

---

## Sending and Receiving Cookies - Example

本节提供了一个教程示例，说明如何使用 `setcookie()` 函数设置和发送 Cookie，以及如何使用 `$_COOKIE` 数组接收 Cookie。

为了帮助我们理解如何发送和接收 Cookie，我编写了以下 PHP 教程示例脚本页面 `CookieTest.php`：

```php
<?php
#### CookieTest.php
#- Copyright 2003 (c) HerongYang.com. All Rights Reserved.
#
   $numCookies = count( array_keys($_COOKIE) );
   $numCookies++;
   $cookieName = "Cookie_$numCookies";
   $cookieValue = "My cookie value";
   setcookie($cookieName, $cookieValue);

   print("<pre>\n");
   print("Cookies added by the server:\n");
   print("   $cookieName: $cookieValue\n");

   print("\nCookies received by the server:\n");
   foreach ($_COOKIE as $k => $v) {
      print "   $k = $v\n";
   }

   print "</pre>\n";
?>
```

当我用浏览器运行此脚本时，我得到了：

```text
Cookies added by the server:
   Cookie_1: My cookie value

Cookies received by the server:
```

### 当我点击浏览器的刷新按钮时，页面发生了如下变化：

```text
服务器添加的 Cookie：
   Cookie_2: My cookie value

服务器接收到的 Cookie：
   Cookie_1 = My cookie value
```

这里发生的情况是：当我第一次打开页面时，服务器从浏览器的 HTTP 请求中未收到任何 Cookie。因此我的页面在 HTTP 响应中添加了第一个名为 "Cookie_1" 的 Cookie。

当我点击刷新按钮时，浏览器在 HTTP 请求中将我的第一个 Cookie 发回给服务器。然后我的页面在响应中添加了第二个名为 "Cookie_2" 的 Cookie。

如果我持续点击刷新按钮，请求和响应中会添加越来越多的 Cookie。但这是有限制的。浏览器只会接受来自同一 Web 服务器的最多 20 个 Cookie。

---

### `ob_start()` - 输出缓冲函数

本节介绍如何使用 `ob_start()` 函数开启输出缓冲，这允许在响应主体已添加后继续添加 HTTP 响应头行。

正如你从 `setcookie()` 的定义中所见，PHP 引擎不对 HTTP 响应主体提供缓冲。这意味着一旦 PHP 脚本开始向 HTTP 响应主体发送输出，HTTP 头部块将被最终确定，不再允许任何更改。

但可以通过调用输出控制函数来改变这种默认行为：

*   `setcookie()` 必须在向 HTTP 响应输出任何内容之前调用。主要原因是 PHP 不缓冲 HTTP 响应。但你可以通过使用 `ob_*()` 函数来改变此行为。
*   **`ob_start()`** - 一个开启输出缓冲的内置函数。
*   **`flush()`** - 一个将输出缓冲区的内容刷新到 HTTP 响应主体的内置函数。

当然，默认行为也可以通过配置文件 `php.ini` 来改变。打开 `php.ini` 并设置以下行：

```ini
output_buffering = 4096
```

上述配置行指示 PHP 引擎开启输出缓冲，并将缓冲区大小设置为 4096 字节。一旦开启 `output_buffering`，你就不必在脚本中调用 `ob_start()` 了。

为了测试 PHP 引擎的默认行为，我将 `CookieTest.php` 修改为 `CookieOutputBuffer.php`：

```php
<?php
#### CookieOutputBuffer.php
#- Copyright 2003 (c) HerongYang.com. All Rights Reserved.
#
   print("<pre>\n");
   print("Adding cookies by the server:\n");

   $numCookies = count( array_keys($_COOKIE) );
   $numCookies++;
   $cookieName = "Cookie_$numCookies";
   $cookieValue = "My cookie value";
   print("   $cookieName: $cookieValue\n");

   setcookie($cookieName, $cookieValue);

   print("\nCookies received by the server:\n");
   foreach ($_COOKIE as $k => $v) {
      print "   $k = $v\n";
   }

   print "</pre>\n";
?>
```

然后我打开 `php.ini` 并设置以下行：

```ini
output_buffering = 0
```

在 IE 中运行 `CookieOutputBuffer.php` 得到如下结果：

```text
Adding cookies by the server:
   Cookie_2: My cookie value

Cookies received by the server:
   User = Herong Yang

PHP Warning: Cannot modify header information - headers already
sent by (output started at ...\CookieOutputBuffer.php:4) ...
```

现在我真正相信 PHP 引擎的默认行为是无输出缓冲。请务必在继续下一个测试前将 `output_buffering` 改回 4096。

---

## 保存在硬盘上的持久 Cookie

本节介绍什么是持久 Cookie —— 一个具有未来过期时间并保存在浏览器计算机硬盘 Cookie 文件中的 Cookie。

Cookie 分为两种：持久 Cookie 和临时 Cookie。

*   **持久 Cookie** 存储在你计算机硬盘上的一个文件中。关闭 Web 浏览器后它仍然保留在那里。当浏览器向该 Cookie 来源的 Web 服务器发起 HTTP 请求时，会拾取该持久 Cookie 并将其包含在请求中。
*   **临时 Cookie** 或**会话 Cookie** 仅在当前浏览会话期间存储在内存中。关闭浏览器时临时 Cookie 会被删除。

`setcookie(name,value)` 的默认行为是设置一个临时 Cookie。要设置持久 Cookie，我们需要使用以下语法向 `setcookie()` 函数调用添加另一个参数：

```php
bool setcookie(string name, string value, int expire)
```

其中 `expire` 指定该 Cookie 何时过期。如果过期时间是未来的时间（如从今天起 30 天后），该 Cookie 将被设置为持久 Cookie。注意 `expire` 应以自纪元以来的秒数表示。设置 `expire` 的最佳方式是使用 `time()` 函数，它以自纪元以来的秒数表示当前时间。例如，从今天起 30 天后可表示为 `time()+60*60*24*30`。

如果未给出 `expire`，将创建一个临时 Cookie。

为了向你展示如何设置持久 Cookie 以及 Cookie 如何存储在文件中，我编写了以下 PHP 脚本页面 `CookiePersisted.php`：

```php
<?php
#### CookiePersisted.php
#- Copyright 2003 (c) HerongYang.com. All Rights Reserved.
#
   $cookieName = "User";
   $cookieValue = "Herong Yang";
   $expiration = time()+60*60*24*30;
   setcookie($cookieName, $cookieValue, $expiration);

   print("<pre>\n");
   print("Cookies added by the server:\n");
   print("   $cookieName: $cookieValue\n");
   print("   Expires at: $expiration\n");
   print "</pre>\n";
?>
```

我用 IE (Internet Explorer) 打开此页面，得到：

```text
Cookies added by the server:
   User: Herong Yang
   Expires at: 1134531525
```

要找出此 Cookie 存储在我电脑的哪个文件中，我点击 IE 的“工具”菜单，选择“Internet 选项...”，并在“常规”选项卡的“临时 Internet 文件”部分点击“设置...”按钮。我看到了我的“临时 Internet 文件夹”位置。于是我进入该文件夹，看到了一个名为类似 "Cookie:user@localhost/" 的 Cookie 文件。我双击该文件，并在记事本中成功打开它：

```text
User
Herong+Yang
localhost/
1024
3801469056
29753439
3934260416
29747404
*
```

实际上，我还看到了许多由我过去访问过的其他网站创建的 Cookie 文件。我把它们全都删除了。

---

## 其他 Cookie 属性 - Domain 和 Path

本节介绍 Cookie 的其他属性。

Cookie 还有两个其他属性：

1.  **domain** - 一个定义该 Cookie 应提供给哪些 Web 服务器域的属性。当 Web 服务器与其定义的域匹配时，Web 浏览器会将 Cookie 发回给该服务器。Web 浏览器绝不会将 Cookie 发回给其定义域以外的域。

    例如，如果一个 Cookie 的域是 `www.google.com`，浏览器仅在访问 `www.google.com` 时才会将此 Cookie 发回给服务器。浏览器绝不会将此 Cookie 发回给 `www.yahoo.com`。

    要使 Cookie 对顶级域的所有子域可用，请将 domain 属性设置为顶级域名。例如，如果 Cookie 的域设置为 `.google.com`，此 Cookie 将对所有 Google 子域可用，如 `groups.google.com` 和 `gmail.google.com`。

2.  **path** - 一个定义该 Cookie 应提供给哪个 Web 服务器路径的属性。当 Web 服务器与其定义的域匹配，且请求的页面与其定义的路径匹配时，Web 浏览器会将 Cookie 发回给该服务器。Web 浏览器绝不会将 Cookie 发回给其定义路径以外的请求路径。

    请注意，定义的路径也包含其所有子路径。例如，如果 Cookie 的域为 `www.amazon.com`，路径为 `/order/`，那么浏览器会针对 `http://www.amazon.com/order/checkout.html` 和 `http://www.amazon.com/order/report/invoice.html` 等请求发回此 Cookie。但对于 `http://www.amazon.com/catelog/book.html` 等请求，浏览器不应发回此 Cookie。

`setcookie()` 函数提供了两个额外参数，允许您按以下语法设置 Cookie 的 "domain"（域）和 "path"（路径）属性：

```php
bool setcookie(string name, string value, int expire, string path, string domain)
```

其中 "path" 指定 Cookie 的路径属性，"domain" 指定 Cookie 的域属性。如果未给出 "path"，Cookie 将默认使用 `/` 作为路径。如果未给出 "domain"，Cookie 将默认使用当前域作为域。

好的，让我们通过以下脚本 `CookieProperties.php` 来实验这些属性：
