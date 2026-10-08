

# 创建一个简单的会话示例

这些讨论可能看起来很抽象，所以让我们来看一个示例。在这里，你将实现一组包含三个页面的程序。

在第一个页面，启动会话并创建变量 $_SESSION['session_var']。实现此操作的代码位于列表 22.1。

列表 22.1 page1.php—启动会话并创建会话变量

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

# 列表 22.2 page2.php—访问会话变量并取消销它

```php
<?php
session_start();

echo 'The content of '.$_SESSION['session_var'].' is ' \
    .$_SESSION['session_var'].'<br />';

unset($_SESSION['session_var']);
?>
<p><a href="page3.php">Next page</a></p>
```

调用 `session_start()` 之后，变量 $_SESSION['session_var'] 将以其之前存储的值可用，如图 22.2 所示。

![](img/654520c37415debd4290b9b4aa2c03f2_512_0.png)

图 22.2 通过会话 ID 传递到 page2.php 的会话变量值

在列表中使用该变量后，你将其取消设置（unset）。会话仍然存在，但变量 $_SESSION['session_var'] 不再存在。

最后，你跳转到示例中的最后一个脚本 page3.php。该脚本的代码位于列表 22.3。

# 列表 22.3 page3.php—结束会话

```php
<?php
session_start();

echo 'The content of '.$SESSION['session_var'].' is ' \
    .$_SESSION['session_var'].'<br />';

session_destroy();
?>
```

# 第 22 章在 PHP 中使用会话控制

如图 22.3 所示，你不再可以访问 $_SESSION['session_var'] 的持久值。

![](img/654520c37415debd4290b9b4aa2c03f2_513_0.png)

图 22.3 会话变量不再可用

你通过调用 `session_destroy()` 结束脚本以销毁会话 ID。

# 配置会话控制

有一组会话的配置选项，你可以在 php.ini 文件中设置它们。表 22.1 显示了一些更有用的选项及其描述。此外，在第 17 章“与文件系统和服务器交互”中，你还学习了更多与会话上传进度相关的配置选项。

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

# 使用会话控制实现身份验证

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

# 列表 22.4 authmain.php—身份验证的主体部分

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
    echo 'Connection to database failed:'.mysqli_connect_error();
    exit();
  }

$query = "select * from authorized_users where
name='$userid' and
password=sha1('$password.')";
```

```php
$result = $db_conn->query($query);
if ($result->num_rows)
{
    // 如果他们在数据库中，则注册用户
    $_SESSION['valid_user'] = $userid;
}
$db_conn->close();
?>
<!DOCTYPE html>
<html>
<head>
  <title>Home Page</title>
  <style type="text/css*>
  fieldset {
    width: 50%;
    border: 2px solid #ff0000;
  }
  legend {
    font-weight: bold;
    font-size: 125%;
  }
  label {
    width: 125px;
    float: left;
    text-align: left;
    font-weight: bold;
  }
  input {
    border: 1px solid #000;
    padding: 3px;
  }
  button {
    margin-top: 12px;
  }
  </style>
</head>
<body>
  <h1>Home Page</h1>
<?php
if (isset($_SESSION['valid_user']))
{
    echo '<p>You are logged in as: '.$SESSION['valid_user'].'<br />';
    echo '<a href="logout.php">Log out</a></p>';
}
?>
</body>
</html>
```

