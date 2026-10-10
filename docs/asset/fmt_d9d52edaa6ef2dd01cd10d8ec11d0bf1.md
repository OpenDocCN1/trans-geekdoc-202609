
`imagerectangle($im, 0, 0, $width-1, $height-1, $line_color);`

// 添加标题

`$title = 'Poll Results';`

`$title_dimensions = imagegetttfbox($title_size, 0, $font_name, $title);`

`$title_length = $title_dimensions[2] - $title_dimensions[0];`

`$title_height = abs($title_dimensions[7] - $title_dimensions[1]);`

`$title_above_line = abs($title_dimensions[5]);`

`$title_x = ($width-$title_length)/2;` // x轴居中

`$title_y = ($y - $title_height)/2 + $title_above_line;` // y轴间隙居中

# 第 21 章：生成图像

```php
imagettext($im, $title_size, 0, $title_x, $title_y,
$text_color, $font_name, $title);
```

```
// 从第一个条形稍微上方画一条线
// 到最后一个条形稍微下方
imageline($im, $x, $y-5, $x, $height-15, $line_color);
```

在脚本的第 3 部分中，你使用了基础图像，分配了颜色，然后开始绘制图表。

你使用以下语句填充图表的背景：

```php
imagefilledrectangle($im, 0, 0, $width, $height, $bg_color);
```

正如你可能想象到的那样，`imagefilledrectangle()` 函数绘制一个填充矩形。第一个参数是图像标识符。你必须向它传递该矩形起点和终点的 x 和 y 坐标。这些点分别对应左上角和右下角。在这种情况下，你用背景颜色（最后一个参数，它是白色）填充了整个画布。

然后你调用

```php
imageline($im, 0, 0, $width-1, $height-1, $line_color);
```

在画布边缘绘制一个黑色轮廓。这绘制的是带轮廓的矩形而不是填充矩形。参数是相同的。注意矩形绘制到 `$width-1` 和 `$height-1`，即从 (0,0) 到这些值的宽度为高度的画布。如果你将其绘制到 `$width` 和 `$height`，则矩形将位于画布区域之外。

对于条形，你使用了与前一个脚本相同的逻辑，以便在图表上居中并写入标题。

```php
imageline($im, $x, $y-5, $x, $height-15, $line_color);
```

`imageline()` 函数在你指定的图像 (`$im`) 上从一组坐标 (`$x`, `$y-5`) 绘制一条线到另一组坐标 (`$x`, `$height-15`)，使用 `$line_color` 指定颜色。

在这种情况下，你从想要绘制第一个条形的地方稍微上方开始绘制条形，到画布底部稍微上方。

现在你准备好在图表上填充数据了。第 4 部分如列表 21.5.4 所示。

## 列表 21.5.4 show_poll.php—第 4 部分将实际数据绘制到图表并完成

```
************************************
// 将数据绘制到图表
************************************
// 获取数据库中的每行数据并绘制对应的条形
```

```php
while ($r_stmt->fetch())
{
if ($total_votes > 0) {
    $percent = intval($num_votes/$total_votes)*100;
} else {
    $percent = 0;
}

// 显示此值的百分比
$percent_dimensions = imagetfbbbox(main_size, 0, $font_name, $percent.'%');

$percent_length = $percent_dimensions[2] - $percent_dimensions[0];
```

（注：此处原文内容似乎不完整或存在格式错乱，已根据要求翻译了可见部分）

## 理解基础会话功能

PHP 中的会话由唯一的会话 ID 驱动，这是一个加密随机数。该会话 ID 由 PHP 生成并存储在客户端，其生命周期贯穿整个会话期间。它可以存储在用户的计算机 Cookie 中（最常用的方法），也可以通过 URL 传递。

会话 ID 充密钥，允许你将特定的变量注册为所谓的会话变量。这些变量的内容存储在服务器上。会话 ID 是客户端可见的唯一信息。如果在连接你网站的特定时刻，会话 ID 通过 Cookie 或 URL 可见，你就可以访问存储在该会话服务器上的变量。你可能用过某些在 URL 中存储会话 ID 的网站。如果你的 URL 包含一段看起来随机的数据字符串，它很可能是某种形式的会话控制。

默认情况下，会话变量存储在服务器的平铺文件中。（如果你愿意编写自己的函数，可以将此行为更改为数据库；你将在“配置会话控制”部分学习更多关于该主题的内容。）

## 什么是 Cookie？

Cookie 是解决在多次事务中保持状态同时保持 URL 洁洁的问题的另一种方案。Cookie 是脚本可以存储在客户端机器上的小段信息。你可以通过发送包含以下格式的 HTTP Header在用户机器上设置 Cookie：

```
Set-Cookie: name=value;expires=date;[path=path];[domain=domain.name];[secure; HttpOnly]
```

这会创建一个名为 name、值为 value 的 Cookie。其他参数是可选可选的。如果没有设置过期日期，该 Cookie 实际上是永久的，除非该 Cookie 不再相关；除非用户手动删除它。path 和 domain 共同用于指定 Cookie 相关的 URL 或多个 URL。secure HttpOnly 关键字意味着 Cookie不会通过明文 HTTP 连接发送，并且只能通过 HTTP 访问，而不能通过任何客户端脚本语言（如 JavaScript）访问。

当浏览器连接到 URL 时，它会首先搜索本地存储的 Cookie。如果存储的任何 Cookie 与连接的域名和路径相关，存储在 Cookie 或多个 Cookie 中的信息将传输到服务器。

## 使用 PHP 设置 Cookie

你可以使用 `setcookie()` 函数在 PHP 中手动设置 Cookie。其原型如下：

```
bool setcookie (string name, string value, int expire = 0, string path = "", string domain = "", int secure = false, [, httponly = false])
```

参数与之前提到的 Set-Cookie Header 中的完全对应。

如果你使用以下代码在 PHP 中设置 Cookie：

```php
setcookie('mycookie', 'value');
```

那么当用户访问你网站的下一个页面（或刷新当前页面）时，你将通过 `$_COOKIE['mycookie']` 访问存储在 Cookie 中的数据。

你可以通过再次调用 `setcookie()` 并使用相同的 Cookie 名称和过去的过去的过期时间来删除 Cookie。你也可以通过 PHP header 函数和之前提供的语法手动设置 Cookie。一个提示是，Cookie Header 必须在任何其他 Header 之前发送；否则它们将无法工作；这是 Cookie 标准使用的要求，而不是 PHP 的限制。

## 在会话中使用 Cookie

Cookie 存在一些相关问题：某些浏览器不接受 Cookie，某些用户可能在浏览器中禁用了 Cookie。（这是 PHP 会话使用 Cookie/URL 双重方法的原因之一，我们将会讨论。）

当你使用会话时，不需要手动设置任何 Cookie。会话函数会通过创建与正在创建会话匹配所需的 Cookie 来为你完成这项任务。

你可以使用 `session_get_cookie_params()` 函数来查看 Cookie 参数。它返回一个包含有效期、路径、域名、secure 和 httponly 的数组。

```php
session_set_cookie_params($lifetime, $path, $domain, $secure, $httponly);
```

## 存储会话

默认情况下，PHP 将会话数据存储在服务器的文件上。会话 ID 用于链接客户端到特定文件。要启动会话，必须调用 `session_start()`：

```php
session_start();
```

一旦会话启动，你可以在 `$_SESSION` 超全局数组中存储数据：

```php
$_SESSION["username"] = "JohnDoe";
$_SESSION["role"] = "admin";
```

会话 ID 是客户端可见的唯一信息。如果会话 ID 通过 Cookie 或 URL 可见，你就可以访问存储在该会话服务器上的变量。

要删除特定的会话变量，可以使用 `unset()`：

```php
unset($_SESSION["username"]);
```

要销毁整个会话并删除所有关联数据，可以使用 `session_destroy()`：

```php
session_destroy();
```

## 创建一个简单的会话示例

这些讨论可能看起来很抽象，所以让我们来看一个示例。在这里，你将实现一组包含三个页面的程序。

在第一个页面，启动会话并创建变量 `$_SESSION['session_var']`。实现此操作的代码位于列表 22.1。

### 列表 22.1 page1.php—启动会话并创建会话变量

```php
<?php
session_start();
$_SESSION['session_var'] = "Hello world!";
echo 'The content of ' .$_SESSION['session_var'].' is ' . .$_SESSION['session_var'].'<br>';
?>
<a href="page2.php">Next page</a>
```

此脚本创建了变量并设置了值。该脚本的输出如图 22.1。

![](img/654520c37415debd4290b9b4aa2c03f2_511_0.png)

图 22.1 页面显示的会话变量初始值将在后续中可用

页面上变量的最终值将在后续页面可用。在脚本结束时，会话变量被序列化（或冻结），直到下一次调用 `session_start()` 时重新加载。

因此，你可以通过调用 `session_start()` 开始下一个脚本。该脚本位于列表 22.2。

### 列表 22.2 page2.php—访问会话变量并取消销它

```php
<?php
session_start();
echo 'The content of '.$_SESSION['session_var'].' is ' \
    .$_SESSION['session_var'].'<br />';
unset($_SESSION['session_var']);
?>
<p><a href="page3.php">Next page</a></p>
```

调用 `session_start()` 之后，变量 `$_SESSION['session_var']` 将以其之前存储的值可用，如图 22.2 所示。

![](img/654520c37415debd4290b9b4aa2c03f2_512_0.png)

图 22.2 通过会话 ID 传递到 page2.php 的会话变量值

在列表中使用该变量后，你将其取消设置（unset）。会话仍然存在，但变量 `$_SESSION['session_var']` 不再存在。

最后，你跳转到示例中的最后一个脚本 page3.php。该脚本的代码位于列表 22.3。

### 列表 22.3 page3.php—结束会话

```php
<?php
session_start();
echo 'The content of '.$SESSION['session_var'].' is ' \
    .$_SESSION['session_var'].'<br />';
session_destroy();
?>
```

## 第 22 章在 PHP 中使用会话控制

如图 22.3 所示，你不再可以访问 `$_SESSION['session_var']` 的持久值。

![](img/654520c37415debd4290b9b4aa2c03f2_513_0.png)

图 22.3 会话变量不再可用

你通过调用 `session_destroy()` 结束脚本以销毁会话 ID。

## 配置会话控制

有一组会话的配置选项，你可以在 `php.ini` 文件中设置它们。表 22.1 显示了一些更有用的选项及其描述。此外，在第 17 章“与文件系统和服务器交互”中，你还学习了更多与会话上传进度相关的配置选项。

会话配置的完整列表，请参阅 PHP 手册 http://php.net/manual/en/session.configuration.php。

| 表 22.1 会话配置选项 | | |
| 选项名称 | 默认值 | 效果 |
| :--- | :--- | \--- |
| session.auto_start | 0 (disabled) | 自动启动会话。 |
| session.cache_expire | 180 | 设置缓存会话页面的有效期，单位为分钟。 |
| session.cookie_domain | None | 指定会话 cookie 中设置的域。 |
| session.cookie_path | None | 指定会话 cookie 中设置的路径。 |
| session.cookie_secure | None | 指定会话 cookie 是否通过明文 HTTP 连接发送或是否需要 HTTPS。 |
| session.cookie_httponly | None | 指定会话 cookie 是否仅可通过 HTTP 访问，因此对客户端脚本不可用。 |
| session.cookie_lifetime | 0 | 设置会话 ID cookie 在用户机器上的持续时间。默认值 0 将持续到浏览器关闭。 |
| session.cookie_path | / | 指定会话 cookie 中设置的路径。 |
| session.name | PHPSESSID | 设置在用户系统中用作 cookie 名称的会话名称。 |
| session.save_handler | Files | 定义会话数据存储存储位置。你可以将此选项指向数据库，但你必须编写自己的函数来访问数据。 |
| session.save_path | " " | 设置存储会话数据的路径。更通俗地说，它获取传递给 session.save_handler 的参数。 |
| session.use_cookies | 1 (enabled) | 配置会话在客户端使用 cookie。 |
| session.hash_function | 0 (MD5) | 允许你指定用于生成会话 ID 的哈希算法。"0" 表示 MD5 (128 位)，"1" 表示 SHA-1 (160 位)。 |

## 使用会话控制实现身份验证

会话控制最用途是在用户通过登录机制身份验证后对其进行跟踪。在这个示例中，你演示了如何从 MySQL 数据库身份验证并使用会话提供此功能。此功能是第 27 章“构建用户身份验证和个性化”的基础，并在其他项目中复用。

该示例由三个简单的脚本组成。第一个 `authmain.php` 为网站成员提供登录表单和身份验证。第二个 `members_only.php` 仅向成功登录的成员显示信息。第三个 `logout.php` 允许成员注销。

要理解此示例如何工作，请看图 22.4，它显示了 `authmain.php` 显示的初始页面。

![](img/654520c37415debd4290b9b4aa2c03f2_515_0.png)

图 22.4 因为用户尚未登录，向其显示登录页面

此页面为用户提供了登录的地方。如果用户尝试在未登录的情况下访问“仅限（Members Only）”部分，他们将看到图 22.5 所示的消息。

![](img/654520c37415debd4290b9b4aa2c03f2_515_1.png)

图 22.5 未登录的用户无法查看网站内容；他们将看到此消息。

然而，如果用户先登录（用户名：testuser，密码：password），然后尝试访问 Members 页面，他们将得到图 22.6 所示的输出。

首先，让我们来看应用程序的代码。大部分代码在 `authmain.php` 中，如列表 22.4 所示。我们将逐行分析。

![](img/654520c37415debd4290b9b4aa2c03f2_516_0.png)

图 22.6 用户登录后，可以访问成员区域

### 列表 22.4 authmain.php—身份验证的主体部分

```php
<?php
session_start();
if (isset($_POST['userid']) && isset($_POST['password']))
{
  // 如果用户刚刚尝试登录
  $userid = $_POST['userid'];
  $password = $_POST['password'];
  $db_conn = new mysqli('localhost','webauth', 'auth');
  if (mysqli_connect_errno()) {
```
