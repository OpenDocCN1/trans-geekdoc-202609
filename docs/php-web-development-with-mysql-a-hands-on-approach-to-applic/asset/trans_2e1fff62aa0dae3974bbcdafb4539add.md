
## 会话变量

会话变量也允许持久保存少量数据。然而，与将其存储在客户端浏览器中不同，它们存储在服务器上，从而在防止用户篡改数据方面提供了额外的安全优势。它们也不限于存储字符串数据。您可以持久保存数组、变量和可序列化对象，PHP 解释器会在脚本之间自动转换它们。然而，会话变量仅在当前网页浏览会话期间存在。换句话说，会话在用户关闭浏览器时结束。当会话结束时，$_SESSION 变量会被销毁。

使用会话变量时，您必须通过使用函数 session_start()[3] 来指示会话何时开始：

```
session_start();
```

首次调用 session_start() 时，没有数据被保存。它仅表示 PHP 解释器可以开始存储和访问会话变量，并且在内部为此会话设置一个唯一标识符。Web 浏览器和我们的应用程序使用此唯一标识符将一个会话与多个网页关联起来。

会话标识符在会话关闭之前不会被销毁。这发生在 Web 浏览器关闭时或调用 session_destroy() 函数时：

```
session_destroy();
```

如果您使用 session_destroy()[4] 函数自行关闭会话，它不会删除会话变量。相反，它仅结束会话。

创建会话变量时，您使用 $_SESSION[] 超全局变量：

```
$_SESSION['user_name'] = 'kenmarks';
```

您通过使用分配的索引访问 $_SESSION 超全局变量[5] 来使用会话变量以检索其值：

```
<p class="login">You are logged in as <?= $_SESSION['user_name'] ?>.</p>; 
```

[3] session_start(): https://php.net/session_start
[4] session_destroy(): https://php.net/session_destroy
[5] $_SESSION superglobal: https://php.net/reserved.variables.session

使用会话变量有几点有趣之处。首先，您必须在创建和访问会话变量之前调用 session_start()。其次，在从一个页面链接到另一个页面（或同一页面）时，您必须记住 Web 是无状态的。要访问您创建的任何会话变量，您必须再次调用 session_start() 函数。

> session_start() 的命名是不幸的。当开发人员首次学习如何在 PHP 中使用会话变量时，他们通常假设一旦调用 session_start()，就不需要再次调用它——即使 Web 是无状态的。他们会疑惑为什么在后续请求中无法访问其会话变量。这个函数的更准确名称可能是：session_start_or_resume()。

第三，如上所述，调用 session_destroy() 仅结束会话，但不会删除会话变量。在用户关闭浏览器并且 PHP 的会话垃圾回收器删除过期会话数据之前，您不能依赖任何数据被删除。为了确保会话变量被删除，请在销毁会话后立即将 $_SESSION[] 超全局变量设置为空数组：

```
session_destroy();
$_SESSION = []; // Destroy all session variables in the current session
```

## 会话示例

为了展示如何使用会话，让我们重写我们最喜欢的 cookie 应用程序，使其使用会话变量而不是 cookie。

复制 cookies.php 并将其命名为 sessionvariables.php。将 <head> 元素部分内的 <title> 元素中的内容以及 <body> 元素部分内的 <h1> 内容从 Using Cookies 改为 Using Session Variables：

在脚本顶部添加对 session_start() 的调用。您应该尽早调用此函数，并在发送任何 HTML 输出之前调用，以防止 Web 服务器警告。

```
<?php
    session_start(); // Start or resume the current session so we can access session variables
?>

<title>Using Session Variables</title>

    <h1>Using Session Variables</h1>
```

## 21. 持久性

在第一个 if 子句正上方，将注释更改为引用 $_SESSION 变量而不是 $_COOKIE：

```
<?php
// User entered name, save name to Session variable and display form asking for favorite cookie
if (isset($_POST['name_submission']) && isset($_POST['entered_name']))
{
```

一旦您调用了 session_start，设置会话变量不需要调用特殊函数。接下来，用会话变量的创建替换对 setcookie() 的调用。

```
// User entered name, save name to Session variable and display form asking for favorite cookie
if (isset($_POST['name_submission']) && isset($_POST['entered_name']))
{
    $_SESSION['name'] = $_POST['entered_name'];
```

在第一个 elseif 子句之前，将注释更改为引用会话变量而不是 cookie。在此 elseif 子句中，用会话变量的创建替换对 setcookie() 的调用：

```
// User entered favorite cookie, save favorite cookie to Session variable and route to this page
elseif (isset($_POST['cookie_submission']) && isset($_POST['entered_cookie']))
{
    $_SESSION['favorite_cookie'] = $_POST['entered_cookie'];
```

在最后一个 elseif 子句之前，添加以下注释以替换引用 cookie 的注释：

```
// Output message displaying saved Session variables
// then end the current session and delete the Session variables
elseif (isset($_SESSION['name']) && isset($_SESSION['favorite_cookie']))
{
```

并将 isset() 调用中的 $_COOKIE[] 引用替换为使用 $_SESSION[]。

在此 elseif 子句中，将对 $_COOKIE 的引用替换为使用 $_SESSION 变量，以便输出的短语：

```
    elseif (isset($_SESSION['name']) && isset($_SESSION['favorite_cookie']))
    {
?>
<h4>
Hey <?= $_SESSION['name'] ?>, you like
<?= $_SESSION['favorite_cookie'] ?> cookies. Very nice!
</h4>
```

最后，为了清除响应，用对 session_destroy() 的调用替换删除 cookie 的 setcookie() 调用。然后，删除 $_SESSION[] 超全局变量的内容。参见列表 21.6。

### 列表 21.6.

```php
elseif (isset($_SESSION['name']) && isset($_SESSION['favorite_cookie']))
{
?>
<h4>
Hey <?= $_SESSION['name'] ?>, you like
<?= $_SESSION['favorite_cookie'] ?> cookies. Very nice!
</h4>
<?php
session_destroy(); // End the current session
$_SESSION = []; // Destroy all session variables in the current session
}
```

## 完整的 sessionvariables.php 代码列表

### 列表 21.7.

```php
<?php
session_start(); // Start or resume the current session so we can access session variables
?>
<html>
<head>
<title>Using Session Variables</title>
<link rel="stylesheet"
href="https://stackpath.bootstrapcdn.com/bootstrap/4.2.1/css/bootstrap.min.css"
integrity="sha384-GJzZqFGwbIQTTN6wy59ff1BuGJpLSa9DkKmp0Dg1MDm4iYMj70gZKylYbI706tWS"
crossorigin="anonymous">
</head>
<body>
<div class="card">
<div class="card-body">
<h1>Using Session Variables</h1>
<?php
// User entered name, save name and display form asking for favorite cookie
if (isset($_POST['name_submission']) && isset($_POST['entered_name'])) {
$_SESSION['name'] = $_POST['entered_name'];
?>
<form class="needs-validation" novalidate method="POST"
action="<?= $_SERVER['PHP_SELF'] ?>;">
<div class="form-group">
<label for="name"><h4>what is your favorite
cookie?</h4></label>
<input type="text" class="form-control"
id="entered_cookie" name="entered_cookie"
placeholder="Enter a cookie you like to eat"
required>
</div>
<button type="submit" class="btn btn-primary"
name="cookie_submission">Submit
</button>
</form>
<?php
} // User entered favorite cookie, save session variable and redirect to this page
elseif (isset($_POST['cookie_submission']) && isset($_POST['entered_cookie'])) {
$_SESSION['favorite_cookie'] = $_POST['entered_cookie'];

header("Location: {$_SERVER['PHP_SELF']}");
exit;
}
// Output message displaying saved Session variables
// then end the current session and delete the Session variables
elseif (isset($_SESSION['name']) && isset($_SESSION['favorite_cookie'])) {
?>
<h4>
Hey <?= $_SESSION['name'] ?>, you like
<?= $_SESSION['favorite_cookie'] ?> cookies. Very nice!
</h4>
<?php
session_destroy(); // End the current session
$_SESSION =
[]; // Destroy all session variables in the current session
} // Initial navigation to this page, display form asking for name
else {
?>
<form class="needs-validation" novalidate method="POST"
action="<?= $_SERVER['PHP_SELF'] ?>">
<div class="form-group">
<label for="name"><h4>What is your name?</h4>
</label>
<input type="text" class="form-control"
id="entered_name" name="entered_name"
placeholder="Enter your name" required>
</div>
<button type="submit" class="btn btn-primary"
name="name_submission">Submit
</button>
</form>

<?php
}
?>
</div>
</div>
<script>
// JavaScript for disabling form submissions if there are invalid fields
```
