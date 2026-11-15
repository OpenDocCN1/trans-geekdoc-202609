

```php
<?php
setcookie("ProgrammingLanguage", "PHP",
      time() + 60*60*12, "/", ".php.net");
?>
```

此 Cookie 可从 php.net 的所有子域中读取。

## 安全

最后，setcookie() 的第六个参数值得一提。如果将其设置为 true，则 Cookie 仅通过安全连接（即通过 HTTPS）发送。因此，如果在 Cookie 中存储敏感数据，则应设置此参数——但此时还需要一个支持 HTTPS 的 Web 服务器。

如果省略此参数（或将其设置为 false），则 Cookie 仅通过 HTTP 发送，而不通过 HTTPS。

> > **注释**
> > 但是，在 Cookie 中隐藏敏感数据（无论是否加密）不一定有好处；事实上，这是不宜的。最好将此数据专门存储在服务器上。在下一章中，您将了解如何实现这一点。

```php
<?php
setcookie("password", "top secret",
      time() + 60*60*12, "/", ".php.net",
      true);
?>
```

## httpOnly

跨站点脚本（XSS，一种针对 Web 应用程序的攻击，我们将在第 32 章中详细讨论）的一种可能表现形式是，被偷偷植入的 JavaScript 代码可以访问 Cookie。微软建议如何至少使这变得更加困难：如果将 httpOnly 指定为 Cookie 的附加参数，则 Cookie 与以前一样与完整的 HTTP 通信一起发送，但 JavaScript 不再能看到 Cookie。1 与此同时，其他浏览器开发商也纷纷效仿，也追加了该功能。

1 在某些配置下，JavaScript 仍然可以访问 Cookie，但需要付出一些努力。

```php
<?php
setcookie("password", "top secret",
    time() + 60*60*12, "/", ".php.net",
    true, true);
?>
```

## 替代语法和命名参数

大量可能的参数是使用命名参数的一个典型示例。但是，如果我们将前面的代码写成如下形式，会发生什么呢？

```php
<?php
setcookie(name: "password", value: "top secret",
    expires: time() + 60*60*12, path: "/", domain: ".php.net",
    secure: true, httponly: true);
?>
```

PHP 会以如下错误作出回应：

> PHP Fatal error: Uncaught Error: Unknown named parameter $expires in ..\set.php:3

要解决这个难题，我们需要稍作展开。为了使 setcookie() 函数尽可能灵活，如前所述，存在一种替代语法：

```
setcookie ( string $name [, string $value = "" [, array $options = [] ]] )
```

换句话说，除名称和值之外的所有参数都存储在数组中，因此上述调用可以重写如下：

```
setcookie("password", "top secret",
[
    expires: time() + 60*60*12,
    path: "/",
    domain: ".php.net",
    secure: true,
    httponly: true,
]
);
```

必须能够协调这两个不同的函数签名。`basic_functions.stub.php` 文件² 揭示了方法：

```
function setcookie(string $name, string $value = "", array|int $expires_or_options = 0, string $path = "", string $domain = "", bool $secure = false, bool $httponly = false): bool {}
```

2 参见 http://s-prs.co/v60222i。

因此，第三个参数称为 expires_or_options。如果值是数字，则将其用作过期日期；如果是数组，则期望一组选项。这不是一个很好的解决方案，但在技术上是必要的。因此，下面的调用是可能的：

```php
<?php
setcookie(name: "password", value: "top secret",
    expires_or_options: time() + 60*60*12, path: "/", domain: ".php.net",
    secure: true, httponly: true);
?>
```

## SameSite Cookie

SameSite Cookie 是一个热门话题。一方面，可以防止跨站请求伪造（CSRF）攻击，或者至少使其更加困难；另一方面，Google Chrome 决定为 Cookie 提供某些 SameSite 功能作为默认设置，这导致众多 Web 应用程序出现了未计划的额外工作。从本质上讲，每个 Cookie 都有三个 SameSite 级别之一（见表 14.2）。如果发生跨站请求——即，域 A 的页面在浏览器中加载，并向域 B 发送链接或表单——则域 B 的 Cookie 不会始终随请求一起发送。

| 参数 | 说明 |
|---|---|
| None | Cookie 处理与以前一样，没有特定限制 |
| Lax | Cookie 仅通过 HTTP GET 随跨站请求发送 |
| Strict | 跨站请求不转发 Cookie |

表 14.2 Cookie 的 SameSite 级别

由于 Chrome 已将 Lax 模式设为默认模式（Firefox 也宣布将在某个时间点效仿），因此可能需要采取行动。

这使我们可以建立与 PHP 的桥梁：setcookie() 和 setrawcookie() 没有针对 SameSite 模式的专用参数。但是，可以通过选项数组设置此值：

```
setcookie(name: "Password", value: "top secret",
options: [
expires: time() + 60*60*12,
path: "/",
domain: ".php.net",
secure: true,
httponly: true,
samesite: "None",
]);
```

## 时机

最后，一个重要提示：由于 Cookie 是作为 HTTP 标头的一部分发送的，因此所有对 setcookie() 的调用都必须在第一个 HTML 输出之前进行。3 这是因为一旦传递 HTML，HTTP 标头就已经发送了。如果之后仍设置 HTTP 标头，则在某些 PHP 版本和配置中会出现图 14.4 所示的错误消息。

![](img/ae7820c36e8f24c1623d26668b28e80e_465_0.png)

图 14.4 Cookie 必须在脚本开头设置

在以下脚本中，操作是正确的；也就是说，在输出 HTML 代码之前设置了几个 Cookie。

```php
<?php
setcookie("ProgrammingLanguage", "PHP",
    time() + 60*60*12, "/");
setcookie("LanguageVersion", "8",
    mktime(0, 0, 0, 12, 24, 2025), "/");
setcookie("Session", "abc123", 0, "/");
?>
<html>
<head>
<title>Cookies</title>
</head>
<body>
<p>Cookies have been set!</p>
</body>
</html>
```

## 清单 14.1 设置三个 Cookie ("set.php")

此脚本的输出相对寥寥无几，因为—如已提及—Cookie 仅在下次访问页面时才会发送到服务器。但是，如果查看浏览器开发者工具，至少会看到 Cookie HTTP 标头。图 14.5 显示了 Chrome 浏览器中的情况。

![](img/ae7820c36e8f24c1623d26668b28e80e_466_0.png)

图 14.5 浏览器开发者工具揭示了 Cookie 的到达。

> > **提示**
> > 如果仍想（甚至不得不）在 PHP 页面中间设置 Cookie 以方便操作，可以使用*输出缓冲*函数。有关此内容的更多信息，请参阅本章末尾。

> > **注释**
> > 如果要更改 Cookie 的值，必须输入与创建 Cookie 时完全相同的信息（过期日期和 Cookie 值本身除外，因为您可能希望更改这些信息）。如果不这样做，PHP 或 Web 浏览器会创建多个同名 Cookie。

关于时间顺序，最后简要说明：Cookie 按其在 PHP 脚本中出现的顺序发送到客户端。

## 特殊字符

Cookie 值会自动进行 URL 编码，因此在幕后会调用 `urlencode()`。但是，可能存在不希望这样做的情况，例如 Cookie 值已经过 URL 编码。在这种情况下，请使用 `setrawcookie()` 函数，它不会修改 Cookie 的值。除此之外，该函数与 setcookie() 相同。

### 14.3.2 读取 Cookie

PHP 读取客户端发送到 Web 服务器的所有 Cookie，并将其放入 $_COOKIE 全局数组中以供使用。以下简单脚本输出此数组的内容；它只需调用 print_r()。

```html
<html>
<head>
<title>Cookies</title>
</head>
<body>
<xmp>
<?php
print_r($_COOKIE);
?>
</xmp>
</body>
</html>
```

## 清单 14.2 输出 "$_COOKIE" 的内容 ("print_r.php")

图 14.6 显示了此脚本的输出（如果先前已执行 set.php，请参见清单 14.1）。

![](img/ae7820c36e8f24c1623d26668b28e80e_467_0.png)

图 14.6 "$_COOKIE" 的内容出现在浏览器中

要访问单个 Cookie，必须使用 Cookie 名称作为数组键。以下清单显示了先前设置的三个 Cookie。结果如图 14.7 所示。

