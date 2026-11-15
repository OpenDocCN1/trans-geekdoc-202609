

<?php
setcookie("ProgrammingLanguage", "PHP",
        time() + 60*60*12, "/");
setcookie("LanguageVersion", "8",
        mktime(0, 0, 0, 12, 24, 2025), "/");
setcookie("Session", "abc123", 0, "/");
?>
<?php echo "Cookies have been set!"; ?>
</body>
</html>
<?php
ob_end_flush();
?>

## 列表 14.5 使用缓冲区设置三个 Cookie（"set-buffering.php"）

输出缓冲区提供了许多其他选项，此处仅简要介绍其中一种：大多数 Web 浏览器都支持使用 Gzip 压缩的数据。这样可以节省大量带宽，因为 Web 服务器发送的不是 HTML 文档，而是其压缩版本。

以下调用（必须位于页面头部）可为页面启用 Gzip 压缩：

```
ob_start("ob_gzhandler");
```

由于只能对完整页面使用 Gzip（或其他算法）进行压缩，因此此处需要输出缓冲区。顺便提一下，PHP 机制会自动检查浏览器是否支持 Gzip。如果不支持，数据将以常规方式（即未压缩）发送。不过应当注意，如果需要，某些 Web 服务器也可以自动使用 Gzip 压缩所有传出数据。

## 14.4 Cookie 测试

让我们通过一个应用示例来演示所学内容。由于用户可以禁用 Cookie，因此判断用户是否接受 Cookie 非常重要。此类测试可以相对快速地创建。

首先，必须向 Web 浏览器发送 Cookie。由于大多数浏览器现在分别处理临时 Cookie 和持久 Cookie，因此应测试两种类型的 Cookie：

```
setcookie("CookieTemp", "ok");
setcookie("CookiePerm", "ok", time() + 60*60*24);
```

这些 Cookie 只有在 Web 服务器请求下一份文档时才会在 $_COOKIE 中可用。由于 IIS 的 bug，使用 header() 进行转发被排除在外（当然，除非你知道你的应用程序绝不需要安装在 IIS Web 服务器上）。相反，会再次使用一个 <meta> HTML 标签：

```
echo "<meta http-equiv=\"refresh\" " .
"content=\"0;url=" .
htmlspecialchars($_SERVER["PHP_SELF"]) .
"?test=ok\">";
```

会再次调用相同的脚本，但这次 URL 中会附加 ?test=ok。脚本会识别该参数，然后检查 Cookie 是否存在：

```
if (isset($_GET["test"])) {
$temp = array_key_exists("CookieTemp",
$_COOKIE);
$perm = array_key_exists("CookiePerm",
$_COOKIE);
}
```

下面的列表显示了完整的脚本。

```
<?php
if (isset($_GET["test"])) {
$temp = array_key_exists("CookieTemp",
$_COOKIE);
$perm = array_key_exists("CookiePerm",
$_COOKIE);
setcookie("CookieTemp", "", 0);
setcookie("CookiePerm", "", 0);
} else {
setcookie("CookieTemp", "ok");
setcookie("CookiePerm", "ok", time() + 60*60*24);
}
?>
```

```
<html>
<head>
<title>Cookies</title>
```

```
<?php
if (!isset($_GET["test"])) {
echo "<meta http-equiv=\"refresh\" " .
"content=\"0;url=" .
htmlspecialchars($_SERVER["PHP_SELF"]) .
"?test=ok\">";
}
?>
```

</head>
<body>

<?php
if (isset($_GET["test"])) {
    echo "Temporary cookies are " .
    ($temp ? "" : "not " .
    "supported.<br />");
    echo "Permanent cookies are " .
    ($perm ? "" : "not " .
    "supported.");
} else {
    echo "Cookies are being set ...";
}
?>

</body>
</html>

## 列表 14.6 检查 Cookie 支持（"cookietest.php"）

![](img/ae7820c36e8f24c1623d26668b28e80e_476_0.png)

## 图 14.10 浏览器仅支持临时 Cookie

> **注意**
> 代码使用 ? 运算符输出已确定的浏览器配置：
> echo("Permanent cookies are " .
> ($perm ? "" : "not " .
> "supported."));
> 如果 $perm 的值为 false，则插入 "not "；否则，只插入一个空格。
> 此外，测试后会再次删除已设置的 Cookie，以免留下不必要的残留。

## 14.5 最后考虑

Cookie 当然很有用，但许多用户拒绝这项技术。因此，你必须遵循两条指导原则：

- 确保即使没有 Cookie，你的网站也能完美无限制地运行。
- 不要欺负那些启用了 Cookie 的用户。

关于最后一点：可能的“限制”例如包括设置许多单独的 Cookie，比如每张图片都发送一个——或者当这些信息也可以存储在单个 Cookie 中时，却设置多个单独的 Cookie。这样做的原因之一是（理论上）300 个 Cookie 的限制。

另一个烦人之处是 Cookie 的过期日期。普通 PC 的使用寿命可能为两到五年——因此让 Cookie 一直有效到 2037 年实在有点尴尬。通常一年就足够了。由于 300 个 Cookie 的限制，大多数 Cookie 根本等不到它们的第一个生日。

关于 Cookie 危险的谣言真相如何？如果 Cookie 只发送给设置过该 Cookie 的域，那么透明的冲浪者是不可能的。

这基本上是正确的，但有几种方法可以绕过这一限制。假设你访问包含来自 www.ad-company.zzz 的广告横幅的网站 www.xy.zzz。这意味着广告商可以设置一个可发回至 ad-company.zzz 的 Cookie。到目前为止，一切都好。

不过现在，你访问了另一个碰巧为横幅显示使用相同广告商的网站。因此，如果在这个网站上显示图形并由 ad-company.zzz 请求，广告商就会收到 Cookie 并识别出你——尽管你在一个完全不同的网站上。

这个场景中的“损害”当然是有限的。广告商可以确定你访问哪些网站，根据此创建用户档案，并向你提供有针对性的广告。但是，电子邮件地址或你在网站上输入的其他个人信息对广告商来说是不可见的。实践也表明，面向特定群体的广告横幅似乎并不真的有效，这点两位作者的自行测试已经证明。相反，我们经常看到已经购买过的产品的广告。此外，这些第三方 Cookie 会在当前浏览器版本按需被过滤掉。

一种较老的方法是在数据收集服务器上手动设置 Cookie 中的域值。无论你在哪个页面上，Cookie 看起来都来自收集站点，并且也会发回给该站点。但是，此方法已不再有效；浏览器可以自动拒绝第三方 Cookie。因此，即使这个“技巧”曾经偶尔被使用过，如今也已成为过去式。

## 第 15 章

## 会话

*会话依赖于 Cookie，但使用更方便。虽然也可以在不使用 Cookie 的情况下使用会话，但不推荐这样做。*

HTTP 是一种无状态协议；上一章已经多次指出这一点。Cookie 只是绕过此限制的一种方式。从最终用户的角度来看，Cookie 的主要问题是，在一定范围内可以用来创建用户档案。从网站开发者的角度来看，Cookie 的主要问题是它们可以在浏览器中被禁用。或者更确切地说，它们*可能*被禁用——但这一点稍后再讨论。

一种可能的解决方案可以用一个词来表达：会话。¹ 当冲浪者访问网站时，就会发生一次会话。因此，如果你打开网上商店的首页，点击几个页面，10 分钟后又冲浪到另一个网站，那么你与该商店进行了一次 10 分钟的会话。如果一小时后你返回商店，这通常会被视为新会话。

PHP 提供了在会话中存储数据的选项。这意味着你可以保存会话数据——使用稍后解释的机制——并且只要会话处于活动状态，就可以再次访问这些数据。PHP 会自动处理所有技术细节（数据存储在哪里，如何实现访问等）。

### 15.1 准备工作

PHP 的会话支持也是 PHP 的一部分，不需要任何额外的 DLL 或配置开关。² 不过，在本章中，你有时会想要修改 *php.ini* PHP 配置文件。那里有一个 [Session] 部分，汇总了所有相关设置。首先，重要的是设置 *session.save_path* 的值。PHP 随附的 *php.ini* 模板包含以下内容：

```
session.save_path = "/tmp"
```

为什么这只是注释？在 Unix/Linux 系统中，目录 */tmp* 通常存在，并且对 Web 服务器或 PHP 进程也是可写的，但在 Windows 上，此

¹ 不过，如你稍后将看到，会话和 Cookie 可以完美互补。

² 但是，作为交换，你可以使用 --disable-session 配置选项完全禁用会话支持。

