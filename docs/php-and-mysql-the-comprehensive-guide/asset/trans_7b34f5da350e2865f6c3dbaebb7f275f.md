

```php
$id_POST = $_POST["id"] ?? "";

if ($id_GET != "" && $id_POST == "") {
?>
<form method="post">
<input type="hidden" name="id"
value="<?php echo htmlspecialchars($id_GET); ?>" />
<input type="submit" value="Confirm deletion" />
</form>
<?php
}

if ($id_GET != "" && $id_POST != "") {
    delete_entry($id_POST); //yet to be implemented ;-)
    echo "<b>Entry deleted!</b>";
}
?>
</body>
</html>
```

### 列表 32.5 删除数据的（糟糕）方法（“delete.php”）

![](img/ae7820c36e8f24c1623d26668b28e80e_875_0.png)

### 图 32.5 首先用户确认删除 …

![](img/ae7820c36e8f24c1623d26668b28e80e_875_1.png)

### 图 32.6 … 然后 Web 服务器才执行它

这种方法不仅糟糕，而且致命，因为这里也使用了未经检查的用户数据。仅仅因为 POST 数据无法如此轻松方便地在 URL 中传输，并不意味着无法伪造 HTTP 请求。在此情况下，甚至有一种非常简单的方法可以欺骗 delete.php 脚本：

- 1. 在 Web 浏览器中调用脚本。
- 2. 将 HTML 代码保存到本地硬盘。
- 3. 将代码中 `<form>` 标记的 `action` 属性设置为原始脚本的 URL。
- 4. 将隐藏字段的值更改为不同的 ID。
- 5. 在 Web 浏览器中打开（本地）表单并提交。Web 服务器上的脚本被调用，伪造的 ID 通过 POST 传输。

图 32.7 显示了新代码；更改或添加的区域已高亮显示。

> **注意**
>
> 大多数浏览器都内置了工具，使得更改表单数据特别容易（通常可以通过 `[F12]` 访问）。因此，隐藏的表单字段并不不可见！

不要认为这种攻击过于简单而（已）过时。就在几年前，一个相对知名的在线商店中发现了一个基于这种攻击方法的安全漏洞。

```html
<html>
<head>
<title>Delete</title>
</head>
<body>
<form method="post" action="http://server.xy/delete.php">
<input type="hidden" name="id"
value="99" />
<input type="submit" value="Confirm deletion" />
</form>
</body>
</html>
```

### 图 32.7 HTML 代码可以在编辑器中本地修改

## 32.5 输入过滤

PHP 拥有一个内置扩展，用于处理输入过滤。该包的最初开发者是 Derick Rethans 和 PHP 发明者 Rasmus Lerdorf。

该扩展无需进一步安装步骤即可使用。它不在 SAPI 级别运行，因此不会在 PHP 看到输入之前拦截任何输入。相反，该过滤器实现了几个函数，这些函数以这种方式过滤数据，使得最终（按计划）不包含任何有害内容。

该扩展的主要函数之一是 `filter_input()`，用于确定 GET、POST 和 Cookie 数据。你指定数据类型（`INPUT_GET`、`INPUT_POST`、`INPUT_COOKIE`），然后是名称，最后是所需的数据类型。如果不满足此条件，则 filter_input() 返回值 0；否则返回输入值。以下示例大致基于第 13 章中的虚构订单表单。

```html
<html>
<head>
<title>Order Form</title>
</head>
<body>
<?php
$ok = false;
if (isset($_POST["Submit"])) {
$ok = true;
if (filter_input(INPUT_GET, "Email", FILTER_VALIDATE_EMAIL) == null) {
$ok = false;
}
if (filter_input(INPUT_POST, "Number", FILTER_VALIDATE_INT) == null) {
$ok = false;
}
if ($ok) {
?>
<h1>Form data</h1>
<?php
$Email = htmlspecialchars(filter_input(INPUT_POST, "Email",
FILTER_SANITIZE_EMAIL));
$Number = filter_input(INPUT_POST, "Number", FILTER_SANITIZE_NUMBER_INT);
echo "<p><b>$Number of tickets for $Email</b></p>";
?>
<?php
} else {
echo "<p><b>Form incomplete</b></p>";
}
}

if (!$ok) {
?>
<h1>World Cup Ticket Service</h1>
<form method="post" action="">
Email address <input type="text" name="Email" /><br />
Number of tickets
<select name="Number">
<option value="0">Please select</option>
<option value="1">1</option>
<option value="2">2</option>
<option value="3">3</option>
<option value="4">4</option>
</select><br />
<input type="submit" name="Submit" value="Place order" />
</form>
<?php
}
?>
</body>
</html>
```

### 列表 32.6 表单数据已过滤（“filter.php”）

filter_input() 第三个参数的可能值包括以下内容：

- **FILTER_SANITIZE_EMAIL**  
  删除不属于电子邮件地址的所有内容。

- **FILTER_SANITIZE_ENCODED**  
  对数据进行 URL 编码。

- **FILTER_SANITIZE_ADD_SLASHES**  
  在特殊字符前添加反斜杠（内部调用 addslashes()）。

- **FILTER_SANITIZE_NUMBER_FLOAT**  
  删除不属于浮点数的所有内容。

- **FILTER_SANITIZE_NUMBER_INT**  
  删除不属于整数的所有内容。

- **FILTER_SANITIZE_SPECIAL_CHARS**  
  将所有特殊字符编码为 HTML 实体。

- **FILTER_SANITIZE_STRING 和 FILTER_SANITIZE_STRIPPED**  
  删除 HTML 特殊字符。请注意，自 PHP 8.1.0 起，这些过滤器已被弃用；建议改用 htmlspecialchars()。

- **FILTER_SANITIZE_UNSAFE_RAW**  
  不删除 HTML 特殊字符。

- **FILTER_SANITIZE_URL**  
  删除不属于 URL 的所有内容。

> **验证和清理**
>
> 列出的所有过滤器的名称中都包含 SANITIZE。这表明过滤器会更改输入数据，并且 filter_input() 返回新值。但是，如果将 SANITIZE 替换为 VALIDATE，则 filter_input() 仅检查（不更改）并返回 true 或 false（或 null），具体取决于数据是否被认为有效。

也可以为 filter_input() 提供第四个参数，用于指定其他信息。例如，存在 FILTER_VALIDATE_REGEXP 过滤器类型，它期望一个用于检查的正则表达式——但开头和结尾没有定界符：

```php
$Number = filter_input(INPUT_POST,
    "Number",
    FILTER_VALIDATE_REGEXP,
    ["regexp" => "^[1-9]\d*$"]);
```

PHP 输入过滤器的第二个主要函数是 filter_var()。你将其传递数据（例如字符串），然后选择过滤器类型。这些与我们之前讨论的类型相同。一如既往，完整列表可在 PHP 手册中找到，网址为 http://php.net/manual/filters.php。

以下列表显示了基于第 26 章中类似应用程序的示例。

```html
<form method="post" action="">
URL: <input type="text" name="url" value="<?php
echo (isset($_POST["url"]) && is_string($_POST["url"])) ? htmlspecialchars($_POST["url"]) : "";
?>"/>
</form>
<hr />
<?php
if (filter_input(INPUT_POST, "url", FILTER_VALIDATE_URL) == null) {
    $url = filter_input(INPUT_POST, "url", FILTER_SANITIZE_URL);
    $data = filter_var($url, FILTER_SANITIZE_STRING);
    echo "<pre>$data</pre>";
}
?>
```

### 列表 32.7 读取 URL 并移除 HTML 标记（“textversion.php”）

该扩展还有几个其他功能，但这些示例对于初步了解应该足够了。相应文档可在 http://s-prs.co/v602247 找到。

> **注意**
>
> 另一类有趣的功能包含在 ctype 扩展中，该扩展也会自动激活。有关此内容的信息可在 http://php.net/ctype 找到。

## 32.6 跨站请求伪造

跨站请求伪造（CSRF）在某种程度上被 XSS 和 SQL 注入等“大”竞争对手攻击所掩盖，甚至在 2017 年被从 OWASP Top 10 中移除——但它在 2021 年作为顶级条目（访问控制受损）的子项回归。CSRF 不仅非常危险，而且在 Web 上变得越来越普遍。在安全审计中，我们越来越发现，许多 XSS 和 SQL 注入漏洞已得到修复，但其他攻击却被完全忽视了。这是怎么回事？用户向网站发送数据；这些数据可以是简单的 GET 请求或 POST 请求。诀窍在于，用户通常是非自愿且无意地发送数据。让我们看一个非常简化的示例。假设你访问了一个内置了以下 HTML 的任意网站：

```html
<img src="http://victim.xy/order.php?articleId=123&quantity=1"
width="1" height="1" />
```

因此，你的浏览器将向服务器 victim.xy 发送 HTTP 请求，同时——如 URL 中示意所示——发送订单信息。再做一个简化的假设：你是 victim.xy 的客户，已经登录，并且会基于此类 GET 请求自动下单。因此，你在并不真正想要的情况下订购了一份文章 123。图 32.8 再次以图形方式显示了流程。

![](img/ae7820c36e8f24c1623d26668b28e80e_880_0.png)

### 图 32.8 CSRF 的工作原理

在这种情况下，CSRF 之所以有效，是因为用户已登录受攻击的网站（通常通过会话 Cookie），并且浏览器在向同一服务器发出请求时会自动发送此 Cookie。因此，有些人也将 CSRF 称为会话劫持，尽管“跨站请求伪造”一词现在已成为通用说法（严格来说，会话劫持只涉及 CSRF 的一个方面）。

当然，在实际中，情况并不总是如此简单，因为 POST 用于订单等重要操作。但这也可以通过 CSRF 进行攻击。请查看以下列表中的表单。

```html
<html>
<head>
<title>Order Form</title>
```

