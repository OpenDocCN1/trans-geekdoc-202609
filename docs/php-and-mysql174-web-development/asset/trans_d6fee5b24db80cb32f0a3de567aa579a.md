

# 第 27 章 构建用户认证与个性化

列表 27.14 logout.php—此脚本结束用户会话

```php
<?php

// 包含此应用的文件
require_once('bookmark_fns.php');
session_start();
$old_user = $_SESSION['valid_user'];

// 存储以测试是否*曾经*登录过
unset($_SESSION['valid_user']);
$result_dest = session_destroy();

// 开始输出 HTML
do_html_header('正在退出登录');

if (empty($old_user)) {
    if ($result_dest) {
        // 他们之前登录了，现在已退出登录
        echo 'Logged out.<br>';
        do_html_url('login.php', 'Login');
    } else {
        // 他们之前登录了但无法退出
        echo 'Could not log you out.<br>';
    }
} else {
    // 如果他们没有登录但由于某种原因进入此页面
    echo 'You were not logged in, and so have not been logged out.<br>';
    do_html_url('login.php', 'Login');
}

do_html_footer();

?>
```

再次，你可能会发现这段代码看起来很熟悉。那是因为它是基于你在第 22 章中编写的代码。

# 修改密码

如果用户遵循“修改密码”菜单选项，用户将看到图 27.7 所示的表单。

# 实现用户认证

![](img/654520c37415debd4290b9b4aa2c03f2_612_0.png)

图 27.7 change_passwd_form.php 脚本提供了一个允许用户更改密码的表单

此表单是由 `change_passwd_form.php` 脚本生成的。这个简单的脚本仅使用了输出库中的函数，因此我们没有包含它的源码。

当此表单被提交时，它会触发 `change_passwd.php` 脚本，该脚本见列表 27.15。

# 列表 27.15 change_passwd_form.php—此脚本更改用户密码

```php
<?php
require_once('bookmark_fns.php');
session_start();
do_html_header('修改密码');
check_valid_user();

display_password_form();

display_user_menu();
do_html_footer();
?>
```

此脚本检查用户是否已登录（使用 `check_valid_user()`）、用户是否已填写了密码表单（使用 `filled_out()`），以及新密码长度是否一致。目前这三个条件都不符合。如果一切顺利，脚本将如下所示调用 `change_password($password)` 函数：

```php
change_password($_SESSION['valid_user'], $old_passwd, $new_passwd);
echo 'Password changed';
```

此函数来自 `user_auth_fns.php` 库，其代码见列表 27.16。

- 列表 27.16 **来自 user_auth_fns.php 的 change_password() 函数—函数更新数据库中的密码**

此函数使用你已经看过的 `login()` 函数来检查提供的旧密码是否正确。如果正确，该函数将连接到数据库并将密码更新为新值。

# 重置忘记的密码

除了修改密码外，你还需要处理用户忘记密码的常见情况。在首页 `login.php` 上，你为这种这种情况的用户提供了一个标记为 `Forgotten your password?` 的链接。该链接将用户带到名为 `forgot_form.php` 的脚本，该脚本使用输出函数显示表单，如图 27.8 所示。

# 实现用户认证

![](img/654520c37415debd4290b9b4aa2c03f2_614_0.png)

重置密码

图 27.8 forgot_form.php 脚本提供了一个表单，用户可以在其中请求重置密码并发送给他们

`forgot_form.php` 脚本非常简单——仅使用输出函数——因此我们没有在这里包含它。当表单被提交时，它会调用 `forgot_passwd.php` 脚本，这个脚本更有趣。该脚本见列表 27.17。

- 列表 27.17 forgot_passwd.php—此脚本将用户的密码重置为随机值并为用户启用新密码

```php
<?php
require_once("bookmark_fns.php");
do_html_header("重置密码");

// 创建短变量名
$username = $_POST['username'];

try {
$password = reset_password($username);
notify_password($username, $password);
echo "Your new password has been emailed to you.<br>";
}
```

# 第 27 章 构建用户认证与个性化

```php
catch (Exception $e) {
echo 'Your password could not be reset - please try again later.';
}
do_html_url('login.php', 'Login');
do_html_footer();
?>
```

如你所见，此脚本使用了两个主要函数来完成工作：`reset_password()` 和 `notify_password()`。让我们逐查看这些函数。

`reset_password()` 函数为用户生成一个随机密码并放入数据库。该函数的代码见列表 27.18。

列表 27.18 来自 user_auth_fns.php 的 reset_password() 函数—此函数将用户的密码重置为随机值并通过电子邮件发送给用户

```php
function reset_password($username) {
// 为用户名设置随机值作为密码
// 返回新密码或失败时返回 false
// 获取 6 到 13 个字符之间的随机单词
$new_password = get_random_word(6, 13);

if($new_password == false) {
// 给出一个默认密码
$new_password = "changeMe!";
}

// 在其添加一个 0 到 999 之间的数字
// 让它成为稍微好一点的密码
$rand_number = rand(0, 999);
$new_password = $rand_number;

// 将用户的密码设置为此或返回 false
$conn = db_connect();
$result = $conn->query("update user
set password = sha1(''.$new_password.'\')
where username = ''.$username.''");

if (!$result) {
throw new Exception('Could not update'); // 失败
} else {
return $new_password; // 成功
}

```

# 实现用户认证 585

`reset_password()` 函数通过 `get_random_word()` 函数为用户生成一个随机密码并将其放入数据库。它使用 0 到 999 之间的随机数字来使其密码稍微好一点。该函数的代码见列表 27.19。

列表 27.19 来自 user_auth_fns.php 的 get_random_word() 函数—从字典获取随机单词

```php
if($new_password == false) {
// 给出一个默认密码
throw new Exception('Could not set password');
}
```

586 第 27 章 构建用户认证与个性化

为了工作，`get_random_word()` 函数需要一个字典。通常位于 `/usr/dict/`。如果你在这些地方没有找到，别担心！你可以在 `wordlist.sourceforge.net/` 找到列表。只需更改 `get_random_word()` 函数中的位置即可。

该网站提供许多语言的字典，所以如果你想要随机的挪威或或语单词，可以下载这些字典。这些文件的格式为每行一个单词，用换行符分隔。

为了从文件中获取随机单词，你在 0 到文件大小之间随机选择位置并读取文件。你可能会获取部分单词，因此你需要跳过该行并获取下一个单词作为你的密码。

该函数有两个清晰的优点。第一个是如果你在寻找单词时到达文件末尾，就回到开头：

```php
if (feof($fp)) { // 到达结尾
    fseek($fp, 0);
}
```

第二个是你可以搜索特定长度的单词：你从字典中提取每个单词，如果它不在 $min 长度和 $max 长度之间，你就继续搜索。同时，你还会提取带有单引号（'））的单词。你可以使用单词对其进行转义，但直接获取下一个单词更简单。

```php
while ((strlen($word) < $min_length) || (strlen($word) > $max_length) || strstr($word, "'"))) {
    if (feof($fp)) { // 到达结尾
        fseek($fp, 0);
    }
    $word = fgets($fp); // 获取单词
}

$word = trim($word); // 去除换行符
return $word;
```

