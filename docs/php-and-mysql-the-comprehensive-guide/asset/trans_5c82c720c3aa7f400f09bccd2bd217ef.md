

Cookie 还有一种可能性，即仅存储在内存中而非永久存储在硬盘上。因此，重新启动浏览器后，此数据将不再可用。在某些情况下，这种行为可能是可取的。

### 14.2.2 限制

为了发布 Cookie 规范，采取了某些预防措施。

可能最重要的限制是，Cookie 只能由设置它的服务器读取。因此，来自 `www.php.net` 的 Cookie 在网站 `www.asp.net` 上不可见——反之亦然。但是，可以将 Cookie 绑定到二级域名（SLD）。如果将 `.php.net` 指定为 Cookie 域（带有前导点），则此 Cookie 不仅可以从 `www.php.net` 读取，还可以从 `pecl.php.net` 和 `windows.php.net` 等读取。甚至可以将 Cookie 限制在域中的某个路径内。如果 Cookie 的路径设置为 `/government`，则无法从 `/opposition` 页面访问它，反之亦然。

数据量方面也有限制。Cookie 本身只能包含 4 KB（4,096 个字符）的数据。这适用于 Cookie 的名称和值。如果两者合计超过 4 KB，值可能会被截断，但名称保持完整（前提是名称小于 4 KB，这大概可以假设）。请注意，这是对浏览器的最低要求，浏览器也可以自行酌情处理更长的 Cookie。

网络浏览器还被指示最多只接受 300 个 Cookie。每个域只允许 20 个 Cookie。一旦超过其中任何一个限制（即总计到达第 301 个 Cookie 或域内到达第 21 个 Cookie），相应的最旧 Cookie 可能会被删除。这些限制可以追溯到硬盘空间几乎难以负担的年代。现代浏览器对这些限制更为宽松。

### 14.2.3 透明冲浪者？

因此，Cookie 只能由设置它们的服务器读取。那么，为什么 Cookie 的形象如此糟糕呢？Cookie 通常被称为*透明冲浪者*，这让人联想到一个可怕的景象：Web 用户在不知情的情况下向网站泄露了所有个人数据。

主要原因之一仍然是历史问题。在 1997 年 3 月刊的 *Byte* 杂志中，Jon Udell 撰写了一篇关于数字证书的文章。其中指出，这些数字 ID 明显优于 Cookie；更糟糕的是，Cookie 不能保证隐私，因为任何 Web 服务器都可以读取客户端计算机上的每个 Cookie。这一错误陈述——如前一节所示——迅速传播开来；甚至有传言称 Cookie 可被其他 Web 服务器用于读取用户的硬盘（嗯，Cookie 确实存储在用户的硬盘上）。

两个月后，即 1997 年 5 月，过期已久的更正出现在边栏的一个小方框中。作者承认他根本没有核实自己的主张，尽管从技术上讲这非常容易。他还声称自己有“窃取”Cookie 信息的想法，但未经核实就印刷了可能的结果（Cookie 不安全）。事实证明，这是不可能的。作者违反了至关重要的基本新闻准则，但损害已经造成。直到今天，许多人仍然不清楚 Cookie 是什么以及它们带来什么风险（另见第 14.5 节）——以及哪些风险仅仅是危言耸听。完全摒弃所有偏见和顾虑，我们现在将探讨如何在 PHP 中使用 Cookie。

## 14.3 在 PHP 中使用 Cookie

如前所述，Cookie 处理（读/写）完全通过 HTTP 头部进行。但 PHP 之所以是 PHP，正是因为用户不必亲自执行这项繁琐的过程。

### 14.3.1 设置 Cookie

setcookie() 函数有两种不同的语法选项。最常见的是以下语法（我们将稍后讨论替代方案）：

```
boolean setcookie ( string name [, string value [, int expires [, string path [, string domain [, bool secure[, bool httponly]]]]]])
```

表 14.1 解释了七个参数的含义。基于这种数量，您会欣赏 PHP 的命名函数参数特性，但这要等几页之后，因为首先需要考虑一个特殊功能。

| 参数 | 描述 | 数据类型 |
| :--- | :--- | :--- |
| name | Cookie 的名称；此参数是唯一的必填参数。其他所有参数均为可选。 | String |
| value | Cookie 的值。 | String |
| expires | Cookie 的过期日期，以自 1970 年 1 月 1 日以来的秒数表示。 | Integer |
| path | 可读取 Cookie 的目录。 | String |
| domain | 有权访问 Cookie 的域。 | String |
| secure | 指定 Cookie 是否只能通过 HTTPS 连接发送的值。 | Boolean |
| httponly | 指示 Cookie 对 JavaScript 是否“不可见”。 | Boolean |

表 14.1 "setcookie()" 的参数

各个参数（除 name 和 value 外）将在后面分别详细介绍。

#### 过期日期

Cookie 有两种类型，根据过期日期有所不同：
- 临时 Cookie 或会话 Cookie，仅在浏览器关闭前有效
- 持久 Cookie 或永久 Cookie，在指定的过期日期前有效

过期日期按表 14.1 所示设置，指定为整数值。使用的“计量单位”是 Unix 世界的纪元值：自 1970 年 1 月 1 日以来经过的秒数。有两种主要方法可以快速直观地计算这样的值：

- time() 以纪元值形式返回当前日期和时间。如果要使 Cookie 从当前时间起在某个时间段内有效，请将相应的秒数添加到 time() 的返回值中。例如，有效期为一天的 Cookie 的过期日期值如下：`time() + 60*60*24` 即，每分钟 60 秒，每小时 60 分钟，每天 24 小时。
- mktime() 将日期转换为纪元值。例如，有效期至 2025 年平安夜（12 月 24 日）中午 12 点的 Cookie 的过期日期值如下：`mktime(12, 0, 0, 12, 24, 2025)`

> 注意
> 有关这些及其他日期函数的更多信息，请参见第 9 章。

如果 Cookie 没有过期日期（即 setcookie() 没有第三个参数，或第三个参数为零），则它是临时 Cookie。浏览器关闭时系统会将其删除，因此下次启动浏览器时它不再存在。以下代码片段设置了一些 Cookie：

```
<?php
setcookie("ProgrammingLanguage", "PHP",
time() + 60*60*12); // valid for 12 hours
setcookie("LanguageVersion", "8",
mktime(0, 0, 0, 12, 24, 2025)); // Dec 24, 2025
setcookie("Session", "abc123"); // temporary
?>
```

#### 路径

Cookie 不仅可以绑定到域，还可以绑定到目录。在过去，当独立域名仍然非常昂贵时，这一点尤为重要，因此许多网站的 URL 形如 www.site.xyz/username。当然，如果在 www.site.xyz/username1 上设置了 Cookie，竞争对手 www.site.xyz/username2 可以读取它，这将是灾难性的。因此，PHP 中 Cookie 的标准行为如下：设置 Cookie 的目录也用作 Cookie 路径的值。在 www.your-company.xyz/products/index.php 上设置的 Cookie 无法从主页 www.your-company.xyz/index.php 读取！因此，最好将 Cookie 路径设置为主目录：

```
<?php
setcookie("ProgrammingLanguage", "PHP",
time() + 60*60*12, "/");
?>
```

如果您只需要在网站的特定区域（例如管理区域）中使用 Cookie，相应地设置路径也同样有用。最终，您将获得微小但显著的性能提升：Web 浏览器不再为所有页面在 HTTP 头部中发送 Cookie，而仅为指定路径内的 URL 发送 Cookie。

#### 域

setcookie() 的第五个参数是有权访问 Cookie 的域。默认情况下——即，如果您未指定域名——浏览器会直接从 URL 中获取相关域。因此，如果用户通过 IP 地址访问您的网站，则仅使用此 IP 地址；域名将不起作用。

在原始规范中，Netscape 开发者规定域名必须包含至少两个点。因此，如果要用一个 Cookie“服务”于 pecl.php.net、windows.php.net 和 www.php.net，则必须输入 ".php.net" 作为值，包括前导点。

较新的浏览器不一定需要两个点。但是，为了获得最大程度的浏览器兼容性，如果可能，应始终在域名中指定至少两个点。

现在有人想出了一个巧妙的技巧，可以跨多个域使用和收集 Cookie。整个过程在第 14.5 节中详细描述。该方法的核心组件是指定一个外部域。这意味着 Cookie 在 www.php.net 上设置，但 www.asp.net 被指定为域名。但是，此类“外部 Cookie”会被多个浏览器拒绝或可能被拒绝。以下是一个带有域值的 Cookie 代码片段：

