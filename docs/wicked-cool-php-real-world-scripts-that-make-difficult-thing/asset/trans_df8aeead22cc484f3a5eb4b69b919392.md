
## 缺点

- 会话通常特定于一个浏览器窗口或一个浏览器进程。当你关闭该窗口时，除非将会话 ID 存储为持久 Cookie，否则用户将无法找回旧数据。但是，借助登录系统，你可以将会话 ID 与用户名关联。
- 默认情况下，PHP 的会话是服务器特定的。如果你有一个销售服务器和一个内容服务器，销售服务器将无法看到来自内容服务器的任何会话数据。你可以自定义会话存储系统来解决这个问题。
- 因为会话 ID 是用户读取和发送的数据，除非你采取预防措施，否则窃听者可能会访问会话。

从抽象的角度来看，你可以将会话视为增强型 Cookie。用户的计算机仍然会以某种方式获取某些数据（例如会话 ID），但真实数据始终存储在你的服务器上。会话技术有多种不同的实现方式，但基本理念始终相同。不过请记住，如果有一些你不希望用户读取或修改的数据，你应该将其放在会话中，而不是 Cookie 中。你需要对 Cookie 执行与对待任何表单数据相同的验证过程，因为它来自客户端，因此很容易被伪造。

## #56: 使用 Cookie 创建“欢迎回来，用户名！”消息

许多网站采用的一种廉价小把戏是向回访用户显示“欢迎回来”。如果你告诉网站你的名字，它可以称呼你的名字问候你。

为了演示一种实现方法，这里有一个脚本可以将用户信息存储在 Cookie 中，并在可用时显示该 Cookie：

```php
<?php
if (isset($_REQUEST["user_name"])) {
    setcookie("stored_user_name", $_REQUEST["user_name"], time() + 604800, "/");
    $_COOKIE["stored_user_name"] = $_REQUEST["user_name"];
}
if (isset($_COOKIE["stored_user_name"])) {
    $user = $_COOKIE["stored_user_name"];
    print "Welcome back, <b><?=$user?></b>";
} else {
?>
<form method="post">
User name: <input type="text" name="user_name" />
</form>
<?php
}
```

在 PHP 中，访问和存储 Cookie 涉及两种不同的机制。你可以通过 $_COOKIE 数组读取客户端发送给你的 Cookie。这就像 $_POST 和 $_GET 数组一样工作。

要设置 Cookie，请使用 setcookie() 函数，它有三个必需参数：

- Cookie 名称。本脚本使用 stored_user_name。
- Cookie 值。
- Cookie 在用户计算机上应过期的时间，以 Unix 时间戳形式表示。本脚本使用 time()+604800——即从当前时间起七天后（有关时间戳的更多详细信息，请参见第 6 章）。

还有三个可选参数：

- 一条路径，用于限制本站点中 Cookie 有效的位置。它的工作方式类似于目录；例如，如果你希望 Cookie 仅对站点下 /content/ 路径下的所有内容有效，请将 /content/ 用作此参数。如果你希望 Cookie 在站点的所有位置都有效，请使用 /。
- Cookie 有效的域。假设你有 www.example.com 和 sales.example.com 主机，并且希望 Cookie 对两者都有效。为此，请将 .example.com 用作域参数。如果你的域中只有一个 Web 服务器主机，则无需关心此项。
- 安全连接的设置。将此参数设置为 1 表示浏览器应仅在连接安全时发送 Cookie。

### 可能出什么问题？

在设置和检索 Cookie 时，经常会出现许多问题：

- 你在调用 setcookie() 之前向用户的浏览器发送了数据。Cookie 请求信息位于 Web 服务器响应的 HTTP 标头中。因此，在调用 setcookie() 之前，你不能向客户端发送任何真实文档数据，也就是说，不能打印或执行其他会导致输出的操作。启用警告后，PHP 会在你犯此错误时提示你。

  导致此问题的常见原因是对 PHP 文件中的空白字符处理不当。如果在开始 PHP 代码部分的 `<?` 之前有任何空行或空格，就会发生此问题。此情况也适用于在调用 setcookie() 之前包含的任何文件；此外，包含的文件在关闭 `?>` 标记之后不能有任何空白字符。

- 用户的浏览器拒绝接受 Cookie。如果浏览器不接受 Cookie，你将不会收到任何反馈。要检查 Cookie，请使用 isset() 查看 $_COOKIE[] 数组槽中是否有任何内容。浏览器拒绝 Cookie 的最常见原因是域不正确（浏览器通常不接受与请求的服务器主机不匹配的域的 Cookie）。

- **有人传入了错误的参数。** Cookie 像客户端发送的其他任何内容一样，很容易被伪造。不要信任它们的值；就像对待任何表单数据一样验证它们。

- **你试图将数组存储在 Cookie 变量中。** 你无法这样做。但是，你可以使用序列化数组（请参见第 12 页的“#5: 将数组转换为以后可恢复的非数组变量”）。

## #57: 使用会话临时存储数据

一个相当常见的用户界面设计是让用户在多个表单中输入大量数据。你可能还希望在用户浏览器打开期间存储一组数据（例如，用于购物车）。虽然从技术上讲可以使用隐藏表单字段实现这一点，但在大多数情况下这并不可取，因为其复杂性和浏览器状态问题。

PHP 有一个内置的 *会话管理* 系统，你可以使用它来按浏览器存储和访问数据。它完成了设置 Cookie（或设置会话 ID 参数）以及将数据存储在服务器某处的大部分脏活累活。在你的 PHP 脚本中，你只需要使用 *session_start()* 函数启动会话管理器，然后使用 $_SESSION 数组访问会话数据即可。

这是一个使用会话管理来捕获、汇总和编辑数据的表单。让我们从一个简单的表单脚本开始。第一部分启动会话并提取现有会话数据：

```php
<?
session_start();

$name = $_SESSION["name"];
$color = $_SESSION["color"];
?>
```

新用户不会设置这些变量，但如果他们随时返回此表单，脚本的这部分将捕获他们的旧值。在打印表单时，我们将这些旧值用作默认值：

```php
print '<form action="sessionview.php" method="post">';
print 'What is your name? ';
print '<input name="name" type="text" value="" . $name . " " /><br/>';
print 'What is your favorite color? ';
print '<input name="color" type="text" value="" . $color . " " /><br/>';
print '<input type="submit" />';
print '<input type="submit" name="clear" value="Clear Details" />';
?>
```

请注意，有一个额外的提交按钮用于清除会话值（你很快就会看到它是如何工作的）。以下是 sessionview.php 脚本，它存储表单数据并给用户机会返回并编辑值。首先，我们启动会话并检查名称和/或颜色是否已作为表单数据发送。如果已发送，我们将这些值设置为会话变量：

```php
<?
session_start();

if ($_REQUEST["name"]) {
    $_SESSION["name"] = $_REQUEST["name"];
}

if ($_REQUEST["color"]) {
    $_SESSION["color"] = $_REQUEST["color"];
}
?>
```

下一部分检查用户是否在表单上按了 Clear Details 按钮。如果是这样，我们使用 unset() 清除会话值：

```php
if ($_REQUEST["clear"]) {
    unset($_SESSION["name"]);
    unset($_SESSION["color"]);
}
```

现在我们知道 $_SESSION 数组包含所有正确的值，因此我们可以根据这些值打印用户的信息：

```php
$name = $_SESSION["name"];
$color = $_SESSION["color"];

if ($name) {
    print "Your name is <b>$name</b>.<br />";
}
if ($color) {
    print "Your favorite color is <b>$color</b>.<br />";
}
```

最后，我们给用户机会返回并编辑详细信息或清除值。我们已经在脚本中完成了所有工作，因此只需提供指向正确位置的超链接即可：

```php
print ' <a href="sessionform.php">Edit details</a>';
print ' | <a href="sessionview.php?clear=1">Clear values</a>';
?>
```
