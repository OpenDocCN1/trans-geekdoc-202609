

# 第 8 章：留言板 2000，（半）防弹级留言板 201

从浏览器调用的页面命名非常直观：view.php、sign.php 和 edit.php。这些每个页面都调用了 start_page.php 和 end_page.php。这些文件包含了标准的页眉和页脚信息，并且易于阅读，因此我们在这里不会讨论它们。

你可能会发现 view.php、sign.php 和 edit.php 文件短得令人惊讶。每个文件只包含几十行代码。这是因为几乎所有的内容都是用可重用的函数编写的。

所以，再次强调，重要的是理解位于 `/book/functions/basic.php` 和 `/book/guestbook2k/header.php` 中的函数。

## 代码解析

如上一节所述，绝大部分工作都在函数中完成，而这些函数保存在会被浏览器调用的页面文件中。

## 可重用函数

我们将介绍 `function/basic.php` 和 `guestbook/header.php` 的内容。

### 来自 FUNCTIONS/BASIC.PHP

我们可以按任何顺序处理这些内容——字母顺序看起来也行。

AUTHENTICATE() 这个小函数发送一个 401 HTTP 响应码。此头部会强制你的浏览器打开图 8-9 所示的用户和密码框。

```php
function authenticate($realm="Secure Area")
{
    $errmsg="Please enter a username and password";
    Header("WWW-Authenticate: Basic realm=$realm");
    Header("HTTP/1.0 401 Unauthorized");
    die($errmsg);
}
```

输入这些文本字段的值会被赋值给 PHP 变量 $PHP_AUTH_USER 和 $PHP_AUTH_PW。随后 PHP 就可以查询 MySQL 来检查这些值是否存储在数据库中。注意，此函数仅发送头部。它没有对文本框中输入的值进行任何检查。这些检查是在 `guestbook2k/authenticate.php` 文件中进行的。如果未输入任何值或值与数据库中的任何内容都不匹配，就会调用此函数。

如果用户点击“取消”按钮，将打印存储在 $errmsg 中的字符串。

## 202 第三部分：简单应用程序

![](img/245156cc770929860a3ede93c01f9981_232_0.png)

图 8-9：401 未授权头部的结果

> 这种类型的认证仅在 PHP 作为 Apache 模块安装时可用。如果你将 PHP 作为 CGI 使用（这是在 Windows 下运行它的唯一方法），这将将不起作用。如果你在 Windows 上进行开发工作，请进入应用程序注释掉对 `authenticate()` 的调用，并为 `win_authenticate.php` 文件创建一个条目。

CLEANUP_TEXT() 此函数对于确保我们不会在数据库中插入恶意文本非常有帮助。

```php
function cleanup_text($value = "", $preserve="", $allowed_tags="")
{
  if (empty($preserve))
  {
    $value = strip_tags($value, $allowed_tags);
  }
  $value = htmlspecialchars($value);
  return $value;
}
```

## 第 8 章：留言板 2000，（半）防弹级留言板 203

这实现了两件事。首先，它删除了 HTML 标签。`strip_tags()` 函数负责这一点。这里不需要担心恶意脚本图片——除非你想要它们。你可以通过第二个参数（allowed_tags）指定你想要保留的标签。`strip_tags()` 的第二个参数可以是这样的字符串：`<b><i></i>`。

然后 `htmlspecialchars()` 将安培符号（&）和双引号转换为适当的实体（`&amp;` 和 `&quot;`）。在运行完这个小函数后，你的查询将在数据库中渲染。

SAFE_QUERY() 此函数将让你在尝试获取查询时不至于抓狂头发。

```php
function safe_query ($query = "") {
    if (empty($query)) { return FALSE; }
    $result = mysql_query($query)
    or die(".query failed: <error=".mysql_errno().".<error=".mysql_error().".<query=".$query);
    return $result;
}
```

在整个应用程序中，你将通过此函数运行查询。这样，如果你的查询由于某种原因失败，你就能很好地了解发生了什么。这是安全编码的另一个例子。在排除代码故障后，你不会经常遇到这些问题，但如果某处发生了更改（可能在你不知情的情况下），你将很清楚地知道发生了什么。

![](img/245156cc770929860a3ede93c01f9981_233_0.png)

> 对于公开访问的网站，通过此函数运行每个查询是有危险的。如果查询失败，黑客可能会看到比你希望的更多关于你的设置。为了防止这种情况发生，你可以定义一个常量（稍后将讨论），防止该函数打印描述性错误。类似这样的代码：
```php
function safe_query ($query = "") {
    if (empty($query)) { return FALSE; }

    if(QUERY_DEBUG == "Off") {
        $result = mysql_query($query) or
```

## 204 第三部分：简单应用程序

```php
die("Query failed: please contact the Webmaster");

else {
  $result = mysql_query($query)
  or die("<![query failed: <error=");
```

### 来自 /GUESTBOOK2K/HEADER.PHP
再次，此文件将被包含在此应用程序的每个页面中。它将保留所有特定此应用程序的函数。此外，还有几个细节是此应用程序的前几行将看到的。注意 `DOCUMENT_ROOT` 的使用。这是一个 Apache 变量，可以通过 PHP 访问，指示默认根文件夹。通过创建此变量，我们的整个应用程序变得可移植了。如果我们移动留言板文件夹及其所有的子文件夹，文件将被正确地找到并访问。请记住这是一个 Apache 变量；你的操作系统和 Web 服务器可能需要不同的变量。检查 `phpinfo()` 以确保。

```php
include($DOCUMENT_ROOT/book/functions/charset.php);
include($DOCUMENT_ROOT/book/functions/basic.php);
$conn = mysql_connect("localhost","username","password")
or die("could not connect to database");
mysql_select_db("guestbook2k",$conn);
die("could not select guestbook2k");
```

define("PAGE_LIMIT", 2);

第一行包含了我们的默认字符集。`charset.php` 文件包含一行。

```php
header("Content-Type: text/html; charset=ISO-8859-1");
```

## 第 8 章：留言板 2000，（半）防弹级留言板 205

此函数有助于防止人们发送不同字符集编码的值。如果他们发送了不同字符集的文本，`cleanup_text()` 函数将失效，你仍然容易跨站脚本攻击。这是一个困难的问题。如果你想了解更多细节，请查看这些文章：

```
http://www.cert.org/tech_tips/malicious_code_mitigation
http://www.apache.org/info/css-security/encoding_examples
```

在这里包含了一些有趣的东西：一个常量，名为 `PAGE_LIMIT`。常量类似于变量，因为它包含一个值（在本例中为 2）。然而，值不能通过简单的赋值或函数更改。常量不会遇到与变量相同的问题，因此可以在函数内部可以使用。运行 `define()` 函数后，常量 `PAGE_LIMIT` 将是每页显示的条目数。如果你想看到更大的数字，欢迎更改。

![](img/245156cc770929860a3ede93c01f9981_235_0.png)

如果你在组合查询时使用常量，你需要结束引号字符串以使用该常量。例如，
`query = "select * from db_name limit PAGE_LIMIT"`
将引起困惑，因为 PHP 没有将常量名替换为其值。然而，这样可行：
`query = "select * from db_name limit " PAGE_LIMIT`

![](img/245156cc770929860a3ede93c01f9981_235_1.png)

PHP 有许多可以在脚本中使用的内置常量。常量列表包含在 PHP 手书中：http://www.php.net/manual/language.constants.php

PRINT_ENTRY() 此函数在表格内打印查询结果。

```php
function print_entry($row,$preserve="") {
    $numargs = func_num_args();
    for ($i = 2; $i < $numargs; $i++) {
        $field = func_get_arg($i);
        $dbfield = str_replace("", "_", strtolower($field));
```

