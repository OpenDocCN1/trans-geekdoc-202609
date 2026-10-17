
列表 37-7 是密码生成文件，`password_maker.inc`。

### 列表 37-7：随机密码函数

```php
<?php
/*********************************************************
 * 此函数生成一个随机字符串。
/********************************************************/
function random_string($charset, $length) {
    $string = "";
    for ($i = 0; $i < $length; $i++)
        $string .= $charset[rand(0, strlen($charset) - 1)];
    return $string;
}
$charset = "abcdefghijklmnopqrstuvwxyz0123456789";
// 示例调用：
// echo random_string($charset, 8);
?>
```

# 电子邮件陷阱

鉴于 PHP 中与邮件相关的函数较少，且这些函数非常直观，因此与邮件相关的问题很可能是由邮件服务器或协议本身的问题引起的。根据我们的经验，很少有 PHP 开发者能够修复在运行良好的 PHP 环境中突然出现的问题。

如果你在 PHP 中收到了邮件相关的错误消息，你想要做的第一件事就是调用你的 PHP 安装所指向的 `sendmail` 服务器——这仅仅是为了排除你的 SMTP 服务器完全坏掉的可能。

接下来，确保你在配置文件中正确设置了 `sendmail` 或 SMTP 路径。请记住，每当你更新 PHP 和/或 Web 服务器时，你都必须执行此操作。即使你已经过了，再次检查一下也没有坏。记住，可能存在多个配置，例如 `php.ini` 和 Apache 的 `http.conf` 都被用于设置 `sendmail` 路径。

如果你没有看到错误，但某些邮件没有送达，请尝试寻找失败的共同点。例如，管理良好的服务器通常会拒绝来自未执行反向 DNS 查询的服务器的邮件。如果你的 `sendmail` 配置不当，防火墙可能会将非公网机器的配置名或私网 IP 地址写入你的邮件头——这导致被 SMTP 服务器快速拒绝（通常企业较多，大学较少）。另一个常见问题发生于你忘记更改默认 PHP 邮件发送者时，或者将其设置为 `nobody` 或 `root` 用户时——许多管理良好的 SMTP 服务器会拒绝来自这些用户的邮件。

如果你的问题在于通过 PHP 客户端访问的 POP 或 IMAP 账户，请尝试等待看看服务器端是否会有影响。这些服务器以不稳定而闻名，不仅经常崩溃，而且需要异常高频率的计划性维护。这虽然令人沮丧，但完全超出了大多数 Web 开发者的责任范畴。

最后，如果你在 PHP 中处理附件时遇到问题，请检查你所使用的 MIME 邮件类随附的文档（包括代码注释）。换行符、时间戳和多个地址等细节问题可能会导致问题。

## 总结

电子邮件是互联网最有用且迷人的功能之一。PHP 提供了从 Web 页面发送和接收电子邮件的能力。然而，PHP 并不是专门的电子邮件程序，无法优雅地处理大量消息。

遗憾的是，电子邮件是我们领域中较为复杂的服务之一，具有许多活动部件，而且对于一个已经存在相当长的功能来说，缺乏稳定性。不要怪罪 PHP——这是电子邮件本身的固有属性。

PHP `mail` 函数最常用的用途之一是发送包含来自 Web 表单生成值的邮件（通常是发给自己的）。这比 `mailto` 链接更可靠且更能防止垃圾邮件，并允许你对数据施加更多结构。你还可以使用 PHP 从数据库发送小批量的邮件数据。然而，大批数据需要邮件管理器或其他解决方案。

# PHP 和 JavaScript

在本章中，我们尝试通过结合 PHP 和 JavaScript 来获取客户端和服务器端脚本的最优特性。我们将简要提一下关于何时使用脚本语言的问题，以及编写代码时可能有帮助的风格建议。然后，我们将转向在现实世界的 PHP 网站可能会看到的务实方面。

![](img/70f9bfaf3d714f908e4cb0592b8eb9a6_743_0.png)

如果你从未用过 JavaScript，仅通过阅读这一章是无法学会的。我们将触及对 PHP 有实质影响的 JavaScript 方面。如果你好奇什么是事件，我们推荐 Danny Goodman 的卓越著作《JavaScript圣经》第五版（Wiley, 2004）。

## 使用 PHP 输出 JavaScript

由于 PHP 是服务器端的，而 JavaScript 是客户端的，你可能预期在同一个页面上都会遇到问题。实际上，这种差异恰恰是它们如此匹配的原因。

尽管 PHP 为创建动态 Web 页面提供了强大的功能，但它是一种严格的服务器端语言。有一类常见的 Web 网站任务不需要所有处理并且可以快速完成——例如，在鼠标悬停时更改按钮的外观，JavaScript 是一种纯客户端语言（虽然也有服务器端版本，但我们已经在该端选择了 PHP），它可以被轻松地集成到 PHP 中，以填补许多空白。

另一方面，客户端 JavaScript（也称为 JavaScript、JS、ECMAScript）有许多局限性。例如，因为它无法与数据库通信，JavaScript 无法通过页面上的新数据来更新自己。更糟糕的是，依赖客户端技术是不可能的，因为这些技术可能在访问者的浏览器中不存在或被禁用。尽职尽的客户端 Web 开发者必须决定编写概率性兼容的代码（并接受多浏览器（用户）），或者同时维护网站的多个版本。（不负责任的开发者只需适应市场领先浏览器的完整功能并听天由命吧……但那是另一个故事了。）PHP 可以帮助缓解客户端不确定性的影响。

### 本章内容

- 使用 PHP 输出 JavaScript
- PHP 作为 JavaScript 的备份
- 静态与动态 JavaScript
- 动态表单生成

## 对决的对象

JavaScript 和 PHP 之间最大的差异可能在于对象模型领域。两者截然不同，并且使用不同的符号表示法。一些人认为这是一件好事，但至少没有混淆对象的机会（就像 ASP 和 JavaScript 之间那样）。可能也有人会将其视为一种痛苦、一种不兼容性、PHP 的缺陷或一个设计缺陷。在任何情况下，你都不可能用 PHP 访问同一个对象——所以放弃它吧。

JavaScript 从上到下始终是面向对象的。每条语句都需要指定一个对象和一个方法，并可能带有事件处理程序。JavaScript 使用所谓的点符号表示（`object.method`），这与我们使用的其他编程语言（如 Python 和微软的 VBScript）相似。

缺点是 JavaScript 的对象模型并没有高度标准化：尽管在理论上 ECMA 和 W3C 引导着国际标准，但在实践中，各种制造商会根据自己的意愿违反或增加这些核心内容。精通 JavaScript 的编写者花费大量精力来跟踪各种浏览器和平台的不兼容性及变通方法。

正如我们在书中讨论的（特别是第 20 章），PHP 的类更多是一个附加物、补丁，而不是语言的本质组成部分。其表示法是箭头或指针样式，在 C 代码中经常可见（`$->variable`）。目前没有机制允许使用点符号。诚实迫使我们承认 PHP 类（尽管这些类在 PHP 中有了很大改进）很可能并没有真正构成任何彻底的对象模型。并不是说我们曾经想要过一个——你在叫谁防御呢？

## PHP 不关心它输出什么

需要记住的主要点是 PHP 清楚知道它返回了什么。你（以及人们）使用 PHP 输出纯文本、HTML、XML、DHTML、JavaScript、XML-Math、各种图形格式、CSS，甚至（对于我们这些讽刺的人来说）ASP。PHP 输出 C 代码并没有真正的技术障碍，尽管这可能不是一种流行的用法。记住，PHP 并不总是输出 PHP——它的最终目标通常是供另一个应用程序（如浏览器）运行的代码。

有几种方法可以使用 PHP 输出 JavaScript。最简单的方法是在当你产生客户端代码冲动时从 PHP 中退出。这种实现方式与你从 HTML 中退出完全相同。

```
<?php
echo("想象在此块中带有复杂的 PHP 标签:");
?>
<script language="JavaScript">
<!-- 对禁用 JavaScript 的浏览器隐藏
document.write("严格版本的客户端和服务器端代码是一件好事。”\n// 结束标题 --
</script>
<?php
echo("在此块中是更多 PHP.");
?>
```

此示例并没有展示 PHP/JavaScript 分离的所有范围。许多 JavaScript 实际上是在 HTML 页面的 `<HEAD>` 元素中定义的，仅在 `<body>` 中调用，而 PHP 通常用于后者。

与 HTML 一样，某些情况下你可能不想跳出 PHP —— 或者这种风格可能是你的个人偏好。在这种情况下，你可以使用 PHP 的 `echo` 或 `print` 输出到 JavaScript。

```php
<?php
echo("This is some complex PHP code.");
echo("<script language=\"JavaScript\">\n");
echo("<!-- Hide from JavaScript described browsers\n");
echo(document.write("Strict separation of client-side and server-side code is a good thing,\n"));
echo("// end hiding --\n");
echo("</script>\n");
echo("More PHP in this block.");
?>
```

如果你使用脚本标签（例如使用 `<script language="PHP">` 来界定 PHP 解析器可能难以区分哪个 `</script>` 标签对应哪个 `<script>` 标签的块），可能会遇到麻烦。尽可能使用 `<?php ?>` 标签。

这种风格并不是完全错误，但可能很难保持条理清晰。除非你是一个经验丰富的程序员，否则可能希望将这种风格限制在 `onSubmit` 事件的场合。

如果你使用 `echo/print` 输出代码，请记住转义 JavaScript 部分中的双引号。参见前述代码段的第 3 行。

## 何时使用 JavaScript

客户端 JavaScript 不负责重型工作，但它在某些任务上速度更快，并允许实现你无法用 PHP 复制的效果。你应该考虑用 JavaScript 替换或增强 PHP 的地方包括：

- 表单和计算器中的简单算术（例如购物车实时总额、抵押计算器）
- 简单验证（例如确保电子邮件地址包含 `@` 符号）
- 站点导航（例如下拉导航菜单）
- 弹出窗口（警框、搜索框）
- 浏览器事件（`mouseover`, `onClick`）

## PHP 作为 JavaScript 的备份

我们使用 JavaScript 建议的反面观点是，PHP 可以帮助避免 JavaScript 的缺陷。有时你可以无缝地同时实现完成任务的客户端和服务器端方法。如果访问者的浏览器启用了 JavaScript，那很好——访问者将利用这种链式方法，通常甚至不会注意到自己有这种选择。如果没有，至少你不会遭受将他们完全锁在站点功能之外的耻辱。

一个完美的例子是用于站点导航的双栏下拉菜单。JavaScript 为你提供即时重定向，而对于那些没有启用 JavaScript 的浏览器，PHP 在经过较长等待后提供相同的结果。这种技巧利用了 JavaScript 具有事件处理器（例如 `onChange`）的事实，这些处理器独立于 HTML 表单结构工作，不需要实际的点击提交。因此，提交按钮可以留给 PHP 使用。列表 3-1 显示了一个使用 JavaScript `onChange` 重定向的 HTML 页面，如果不起作用，则使用 PHP 处理器。

### 列表 3-1：JavaScript 和 PHP 导航表单（`navigation.html`）

```html
<html>
<head>
  <title>导航下拉菜单</title>
  <script language="JavaScript">
<!--
  function Browse(form, i) {
    var site = form.elements[i].selectedIndex;
    if (site > 0) {
      top.location = form.elements[i].options[site].value
    }
  }
  // --
</script>
</head>
<body>
  <form method="post" action="redirect.php">
  <select name="category" onChange="Browse(this,form,0)">
  <option value=0">Choose a Category</option>
  <option value="desktop.php">Desktops</option>
  <option value="laptop.php">Laptops</option>
  <option value="monitor.php">Monitors</option>
  <option value="input.php">Input devices</option>
  <option value="storage.php">Storage devices</option>
  </select>
  <input type="submit">
</form>
</body>
</html>
```

PHP 处理器文件名为 `redirect.php` 只需要两行：

```php
<?php $category = $_POST['category'];
header("Location: $category"); ?>
```

你可以在表单验证中使用类似的分工。如果启用了 JavaScript，你可以用它来确保邮编为九位数字，电话号码为十位数字，电子邮件地址同时包含 `@` 和 `.`。如果没有启用 JavaScript，你可以编写一个小的 PHP 脚本，在表单提交时执行相同的操作并返回带有警告的表单。

![](img/70f9bfaf3d714f908e4cb0592b8eb9a6_747_0.png)

JavaScript 表单验证应该用于快速的便利提示和数据清洗。有关数据安全的更多信息，请参见第 29 章。

另一种类型的表单基本上是算术——带有实时总额的购物车或抵押贷款支付计算器。同样，你可以在算术表单中结合 JavaScript 和 PHP 以涵盖所有情况。

最后，有一种用途 PHP 的速度要快到你可能想完全替换 JavaScript：浏览器嗅探。这样做是为了根据浏览器向访问者发送不同版本的文件（例如样式表）。服务器端嗅探比客户端高效得多，因为不需要发送 JavaScript。

### 列表 3-2：服务器端嗅探（`browsnip.php`）

```php
<?php
if (strpos($_HTTP_USER_AGENT, 'IE') > 0) {
    header("Location:ie.html");
} elseif (strpos($_HTTP_USER_AGENT, 'Gecko') > 0) {
    header("Location:moz.html");
}
?>
```

## 静态与 JavaScript

虽然列表 3-1 中的静态表单对许多应用程序很有用，但它有一个大问题：你必须手动维护它。每当你决定向站点添加新页面时，都要手动将其添加到下拉列表中。通过 PHP 和数据库，你可以动态地更新它。列表 3-3 是你如何重写 3-1 以实现更好的客户端/服务器集成。

### 列表 3-3：动态 JavaScript 和 PHP 表单（`dyn_navigation.html`）

```html
<html>
<head>
<title>导航下拉菜单</title>
<script language="JavaScript">
<!--
function Browse(form,i) {
  var site = form.elements[i].selectedIndex;
  if (site > 0) {
    top.location = form.elements[i].options[site].value
  }
}
// -->
</script>
</head>
<body>
<form method="post" action="redirect.php">
<select name="Category" onChange="Browse(this.form,0)">
<option selected value="0">Choose a Category</option>
<?php
mysql_connect("localhost", "user", "password");
$mysql_db = "site_db";
$query = "SELECT filename, my_text
FROM categories\nWHERE display = '1'";
$result = mysql_query($query);
while($filename, $my_text = mysql_fetch_array($result)) {
  print("<option value=\"$filename\">$my_text</option>\n");
}
?>
</select>
<input type="submit">
</form>
```
