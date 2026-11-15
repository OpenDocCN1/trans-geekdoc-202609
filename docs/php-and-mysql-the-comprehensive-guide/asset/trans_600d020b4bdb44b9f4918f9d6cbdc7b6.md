

```html
<html>
<head>
<title>Cookies</title>
</head>
<body>
<table>
<tr><th>Name</th><th>Value</th></tr>
<tr><td>Programming language</td><td>
<?php
echo htmlspecialchars(
$_COOKIE["Programming language"]);
?>
</td></tr>
<tr><td>Language version</td><td>
<?php
echo htmlspecialchars(
$_COOKIE["Language version"]);
?>
</td></tr>
<tr><td>Session</td><td>
<?php
echo htmlspecialchars(
$_COOKIE["Session"]);
?>
</td></tr>
</table>
</body>
</html>
```

清单 14.3 输出三个 Cookie（"read.php"）

![](img/ae7820c36e8f24c1623d26668b28e80e_468_0.png)

图 14.7 Cookie 值在浏览器中显示

但请注意：如果不存在指定名称的 Cookie，将根据相应的 PHP 配置显示一条警告消息。要测试此问题，请关闭所有浏览器窗口，重新启动浏览器，然后再次调用 read.php 脚本（或者，如果您的 Web 浏览器允许，也可以手动删除 session Cookie）。您可以在图 14.8 中看到结果：Cookie session 不再存在（因为它没有过期日期）。因此，`$_COOKIE["Session"]` 无法指向任何位置。

![](img/ae7820c36e8f24c1623d26668b28e80e_469_0.png)

图 14.8 不存在的 Cookie 的错误消息

因此，您必须显式检查 Cookie 是否存在。可以使用 array_key_exists() 数组函数（参见第 8 章）：

```
if (array_key_exists("Session", $_COOKIE)) {
    // ...
}
```

不过，更常见的是使用 empty() 或 isset() 进行检查，如表单处理中所示：

```
if (isset($_COOKIE["Session"])) {
    // ...
}
```

> **注**
>
> 清单 14.3 的相应改进版本可在本书的在线资料（参见前言）中找到，文件名为 read-improved.php。警告消息在那里也会消失。

这样您可以读取每个 Cookie，但不能读取其属性（如路径和过期日期）。此类数据仅存储在客户端；只有 Cookie 名称和 Cookie 值会发送到服务器。

## 14.3.3 删除 Cookies

最后，还有一个如何删除 Cookie 的问题。例如，如果 Cookie 存储了用户已登录受保护系统的事实，那么删除它可能很有用。

这里的诀窍是将过期日期设置为过去的日期。浏览器随后将从 Cookie 内存中删除该 Cookie。

例如，值 0 很适合此目的——即将日期转换为 1970 年 1 月 1 日——因为它显然在过去。以下代码将对会话 Cookie 执行此操作；对于永久 Cookie，其工作方式相同：

```
setcookie("Session", "abc123", 0, "/" );
```

> **注**
>
> 再次注意，请务必使用与设置 Cookie 时相同的其余参数。如果省略用于路径的第四个参数，浏览器将把该 Cookie 视为一个新的碎屑 Cookie（随后会因过期日期而立即将其删除）。

让我们创建一个小应用程序，使用户能够删除 Cookie。为此，所有 Cookie 都将在 foreach 循环中输出：

```
foreach ($_COOKIE as $name) {
// ...
}
```

输出每个 Cookie 后，会输出一个链接，该链接带有 URL 参数 ?kill-cookiename 再次调用脚本。如果识别到此参数，脚本将再次删除该 Cookie——当然，是在第一个 HTML 输出之前：

```
if (isset($_GET["kill"])) {
setcookie($_GET["kill"], "", 0, "/" );
}
```

为了让 Web 服务器看到这些更改，必须重新加载页面；否则，$_COOKIE 数组起初仍将包含已删除的 Cookie：

```
echo("<meta http-equiv=\"refresh\" " .
"content=\"0;url=\" " .
htmlspecialchars($_SERVER["PHP_SELF"]) .
"\">");
```

> **提示**
>
> 您可能会问：为什么这么复杂？为什么不直接使用 HTTP 重定向？您需要输出 HTTP 标头 Location。在 PHP 中，这是通过 header() 函数完成的。通过 $_SERVER["PHP_SELF"]，您可以访问当前脚本的 URL，从而确保重定向或重新加载（nl2br() 会删除任何现有的换行符）：
> header("Location: " . nl2br($_SERVER["PHP_SELF"]));

之所以这样做，是因为 Microsoft IIS Web 服务器的旧版本存在一个 bug。如果调用一个设置（或删除，从技术上讲是同一件事）Cookie 的 CGI 脚本，然后立即执行服务器端重定向，则该 Cookie 不会从 Web 服务器发送到 Web 浏览器。
出于此原因，您需要使用显示的 <meta> 标签进行 HTML 重定向。

完整的脚本在下一个清单中显示；图 14.9 展示了其应用。

```
<?php
if (isset($_GET["kill"])) {
setcookie($_GET["kill"], "", 0, "/");
}
?>

<html>
<head>
<title>Cookies</title>

<?php
if (isset($_GET["kill"])) {
echo("<meta http-equiv=\"refresh\" " .
"content=\"0;url=\" " .
htmlspecialchars($_SERVER["PHP_SELF"]) .
"\">");
}
?>

</head>
<body>
<table>
<tr><th>Name</th><th>Value</th>
<th>Delete?</th></tr>

<?php
foreach (array_keys($_COOKIE) as $name) {
echo("<tr><td>" . htmlspecialchars($name) .
"</td>");
echo("<td>" .
htmlspecialchars($_COOKIE[$name]) .
"</td>");
echo("<td><a href=\"" .
htmlspecialchars($_SERVER["PHP_SELF"]) .
"?kill=" . urlencode($name) .
"\">Yes</a></td></tr>");
}
?>

</table>
</body>
</html>
```

清单 14.4 可以删除 Cookies（"delete.php"）

![](img/ae7820c36e8f24c1623d26668b28e80e_472_0.png)

图 14.9 基于 Web 的 "Cookie 擦除器" 实际运行

该应用程序有一些微妙之处。例如，在使用 htmlspecialchars() 输出之前，会将 Cookie 名称和值转换为 HTML 格式。这样可以避免显示中出现潜在的"灾难"（例如，如果 Cookie 值包含尖括号）。此外，在输出链接或重新加载页面之前，脚本名称始终通过 $_SERVER["PHP_SELF"] 读取。这意味着即使重命名脚本，它仍然可以工作。

但是，有一个限制：如前所述，路径值必须与删除 Cookie 时实际设置的 Cookie 路径匹配。这无法通过 PHP 读取。出于此原因，值 "/" 被"猜测"为路径。如果 Cookie 具有不同的路径，删除将不起作用。

## 14.3.4 "新" Cookies

如前所述，www.ietf.org/rfc/rfc2965.txt 上提供了一种新的 Cookie 规范。该规范在设置 Cookie 时使用 Set-Cookie2 而非 Set-Cookie 作为 HTTP 标头。Cookie 数据的传输方式也不同；例如，Cookie 值带引号传输：

```
Set-Cookie2: Session="abc123"; Path="/"
```

这会设置一个名为 Session、值为 "abc123" 的 Cookie，可在整个网站（路径 /）上读取。客户端随后按以下方式将 Cookie 发送回 Web 服务器：

```
Cookie: $Session="abc123"; $Path="/"
```

当前浏览器尚不支持此规范。但是，已经可以在 PHP 中使用此技术。您必须使用 header() 函数设置 Cookie，该函数允许您指定 HTTP 标头：

```
header("Set-Cookie2: Session=\"abc123\"; Path=\"/\"");
```

一旦出现可以处理这些"新" Cookie 的客户端，您将通过 $_SERVER["HTTP_COOKIE"] 访问这些数据。

> **提示**
>
> $_SERVER["HTTP_COOKIE"] 已经包含 Cookie 名称和值的列表；$_COOKIE 的数据也是从此确定的。

由此可见，使用 PHP 您已经为下一代 Cookie 做好了准备；但是，由于浏览器需要向后兼容，这可能需要一段时间才能普及。但这似乎是值得的，因为新规范包括将 Cookie 绑定到端口的选项。

## 输出缓冲

我们之前已经提示过：由于 Cookie 作为 HTTP 标头的一部分发送，因此必须在第一个 HTML 输出之前设置它们，因为 PHP 会将您输出的所有数据（例如，使用 echo 或 print，甚至是 HTML 片段）直接发送到客户端。但是，您可以通过使用输出缓冲来防止这种情况。

按照以下步骤操作：

1. 使用 ob_start() 启用输出缓冲。
2. 输入您希望输出的数据（包括 Cookie）。
3. 使用 ob_end_flush() 将所有缓冲的数据发送到 Web 浏览器（如果省略该函数，缓冲区将在页面结束时自动发送到客户端）。

因此，我们可以如下在清单 14.5 中修订清单 14.1——在页面中间调用 setcookie()。

```
<?php
ob_start();
?>
<html>
<head>
<title>Cookies</title>
</head>
<body>
```

