
登录过程包括将检索到的值存储在会话中（该会话已在 `header.html` 中启动），然后将用户重定向到主页。由于查询将返回一个包含三个元素的数组——一个索引为 `user_id`，一个为 `first_name`，第三个为 `user_level`，因此这三个值都可以直接获取到 `$_SESSION` 中，从而生成 `$_SESSION['user_id']`、`$_SESSION['first_name']` 和 `$_SESSION['user_level']`。如果 `$_SESSION` 中已有其他值，则不应使用此快捷方式，因为这会清除那些其他元素。

**6.** 重定向用户：

```php
$url = BASE_URL . 'index.php';
ob_end_clean();
header("Location: $url");
exit();
```

`ob_end_clean()` 函数将删除现有缓冲区（输出缓冲也是在 `header.html` 中开始的），因为该缓冲区将不再被使用。

**7.** 完成条件判断并关闭数据库连接：

```php
} else {
    echo '<p class="error">Either the email address and password entered do not match those on file or you have not yet activated your account.</p>';
}
} else {
    echo '<p class="error">Please try again.</p>';
}
mysqli_close($dbc);
} // End of SUBMIT conditional.
?>
```

错误消息 ![Image](graphics/circle-b.jpg) 指示登录过程可能因两个原因失败。一是提交的电子邮件地址和密码与存档的不匹配。另一个原因是用户尚未激活其账户。

![Image](graphics/18_figure_24_b.jpg)

![Image](graphics/circle-b.jpg) 如果登录查询未返回单个记录，则显示错误消息。

**8.** 显示 HTML 登录表单 ![Image](graphics/circle-c.jpg)：

```html
<h1>Login</h1>
<p>Your browser must allow cookies in order to log in.</p>
<form action="login.php" method="post">
  <fieldset>
  <p><b>Email Address:</b> <input type="text" name="email" size="20" maxlength="60" /></p>
  <p><b>Password:</b> <input type="password" name="pass" size="20" maxlength="20" /></p>
  <div align="center"><input type="submit" name="submit" value="Login" /></div>
  </fieldset>
</form>
```

![Image](graphics/18_figure_25_c.jpg)

![Image](graphics/circle-c.jpg) 登录表单。

登录表单与注册表单一样，会将数据提交回自身。不过，此表单不是粘性的，但您可以添加该功能。

请注意，页面包含一条消息，告知用户必须启用 Cookie 才能使用该网站（如果用户不允许 Cookie，则永远无法访问已登录用户页面）。

**9.** 包含 HTML 页脚：

```php
<?php include ('includes/footer.html'); ?>
```

**10.** 将文件保存为 `login.php`，将其放在您的 Web 目录中，并在 Web 浏览器中测试 ![Image](graphics/circle-d.jpg)。

![Image](graphics/18_figure_26_d.jpg)

![Image](graphics/circle-d.jpg) 成功登录后，用户将被重定向到主页，并会看到按姓名显示的欢迎语。

#### 编写 logout.php

**1.** 在文本编辑器或 IDE 中开始一个新的 PHP 文档，命名为 `logout.php`（**[Script 18.9](#ch18.html#ch18ex09)**）：

```php
<?php # Script 18.9 - logout.php
require ('includes/config.inc.php');
$page_title = 'Logout';
include ('includes/header.html');
```

**Script 18.9.** 注销页面会销毁所有会话信息，包括 Cookie。

***

```php
1  <?php # Script 18.9 - logout.php
2  // This is the logout page for the site.
3  require ('includes/config.inc.php');
4  $page_title = 'Logout';
5  include ('includes/header.html');
6
7  // If no first_name session variable exists, redirect the user:
8  if (!isset($_SESSION['first_name'])) {
9
10     $url = BASE_URL . 'index.php'; // Define the URL.
11     ob_end_clean(); // Delete the buffer.
12     header("Location: $url");
13     exit(); // Quit the script.
14
15  } else { // Log out the user.
16
17     $_SESSION = array(); // Destroy the variables.
18     session_destroy(); // Destroy the session itself.
19     setcookie(session_name(), '', time()-3600); // Destroy the cookie.
20
21  }
22
23  // Print a customized message:
24  echo '<h3>You are now logged out.</h3>';
25
26  include ('includes/footer.html');
27  ?>
```

***

**2.** 如果用户未登录，则重定向用户：

```php
if (!isset($_SESSION['first_name'])) {
    $url = BASE_URL . 'index.php';
    ob_end_clean();
    header("Location: $url");
    exit();
}
```

如果用户当前未登录（通过检查 `$_SESSION['first_name']` 变量确定），则将用户重定向到主页（因为尝试注销用户毫无意义）。

**3.** 如果用户当前已登录，则注销用户：

```php
} else { // Log out the user.
    $_SESSION = array();
    session_destroy();
    setcookie(session_name(), '', time()-3600);
}
```

要注销用户，需重置会话值，在服务器上销毁会话数据，并删除会话 Cookie。这些代码行首次在 [Chapter 12](#ch12.html#ch12) 中使用并描述。Cookie 名称将是 `session_name()` 函数返回的值。如果您稍后决定更改会话名称，此代码仍然准确。

**4.** 打印注销消息并完成 PHP 页面：

```php
echo '<h3>You are now logged out.</h3>';
include ('includes/footer.html');
?>
```

**5.** 将文件保存为 `logout.php`，将其放在您的 Web 目录中，并在 Web 浏览器中测试 ![Image](graphics/circle-e.jpg)（在上一页）。

![Image](graphics/18_figure_27_e.jpg)

![Image](graphics/circle-e.jpg) 成功注销的结果。

### 密码管理

该网站公共部分的最后一个方面是密码管理。需要考虑两个过程：重置遗忘的密码和更改现有密码。

#### 重置密码

用户不可避免地会忘记网站的登录密码，因此为这些情况制定应急计划很重要。一种选择是让用户在发生这种情况时给管理员发送电子邮件，但管理网站已经够难了，没必要增加额外的麻烦。相反，本网站将有一个脚本，其目的是重置遗忘的密码。

由于数据库中存储的密码使用 MySQL 的 `SHA1()` 函数进行加密，因此无法检索未加密的版本（数据库实际存储的是密码的*哈希*版本，而非*加密*版本）。替代方案是创建一个新的随机密码，并将现有密码更改为该值。与其直接在 Web 浏览器中显示新密码（那将极其不安全），不如将新密码发送到用户注册时使用的电子邮件地址。

#### 编写 forgot_password.php

**1.** 在文本编辑器或 IDE 中开始一个新的 PHP 文档，命名为 `forgot_password.php`（**[Script 18.10](#ch18.html#ch18ex10)**）：

```php
<?php # Script 18.10 - forgot_password.php
require ('includes/config.inc.php');
$page_title = 'Forgot Your Password';
include ('includes/header.html');
```

**2.** 检查表单是否已提交，包含数据库连接，并创建一个标志变量：

```php
if ($_SERVER['REQUEST_METHOD'] == 'POST') {
    require (MYSQL);
    $uid = FALSE;
}
```

此表单将接受电子邮件地址输入，并更改该记录的密码。为此，脚本首先需要检索与提交的电子邮件地址匹配的用户 ID 值。为了开始该过程，将一个标志变量赋值为 FALSE，假设不存在有效的用户 ID。

**3.** 验证提交的电子邮件地址：

```php
if (!empty($_POST['email'])) {
```
