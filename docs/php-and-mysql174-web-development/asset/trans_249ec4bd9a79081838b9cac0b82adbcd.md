

# 实现书签存储与检索

```php
throw new Exception('Could not find email address.');
// 用户不在数据库
else {
$row = $result->fetch_object();
$email = $row->email;
$from = "From: support@phpbookmark \r\n";
$msg = "Your PHPBookmark password has been changed to .$password.\r\n" .
      "Please change next time you log in.\r\n";

if($email, 'PHPBookmark login information', $msg, $form) {
    return true;
} else {
    throw new Exception('Could not send email.');
}
}
```

在 `notify_password()` 函数中，给定用户名和新密码，你只需要查找该用户的邮箱地址并使用 PHP 的 `mail()` 函数将其发送给用户。

给用户提供一个真正随机的密码（由大小写字母、数字和标点符号的任意组合组成）会比随机单词和数字更安全。然而，像 `zigzag48` 这样的密码比真正随机的密码更容易让用户阅读和输入。对于用户来说，判断随机字符串中的某个字符是 0 还是 O（零或大写 O），或者 1 还是 l（一或小写 L）通常是很令人困惑的。

在我们的系统中，字典文件包含约 45,000 个单词。如果破解者知道我们正在创建密码并知道用户名，他平均需要尝试 22,500,000 次密码才能猜中一个。即使我们的用户忽略了我们修改密码的建议，这种安全级别对于这类应用程序似乎也足够，因为没有存储真实的个人数据。

然而，允许用户重置密码的更好方法是向用户发送一个重置密码页的链接，查询字符串中包含一个一次性令牌（token），该令牌在一段时间后过期（例如 24 小时或 72 小时）。这个一次性令牌将授权用户更改密码，而无需使用通过电子邮件发送的明密码。

# 实现书签存储与检索

处理完用户相关的功能后，让我们来看看书签是如何存储、检索和删除的。

# 添加书签

用户可以通过点击菜单中的“添加”链接来添加书签。此操作将他们带到图27.9 所示的表单。

![](img/654520c37415debd429b0aa19.png) 图27.9 add_bm_form.php 脚本提供了一个用户可以在其中添加书签的表单。

由于 `add_bm_form.php` 脚本简单且仅用于输出，我们没有包含它。当表单提交时，它会调用列表27.21 所示的 `bookmarks.php` 脚本。

列表27.21 bookmarks.php——向用户页面添加书签的脚本

```php
<?php

require_once('bookmark_fns.php');
session_start();

// 创建变量
$new_url = $_POST['new_url'];

do_html_header('Adding bookmarks');

try {
check_valid_user();
if (!$filled_out($_POST)) {
    throw new Exception('表单未填写完整');
}
// 检查 URL 格式
if (strpos($new_url, 'http://') === false) {
    $new_url = 'http://'.$new_url;
}

// 检查 URL 是否有效
if (!@open($new_url, 'r')) {
    throw new Exception('无效的 URL');
}

// 尝试添加签
add_bm($new_url);
echo '书签已添加';

// 获取此用户保存的书签
if ($url_array = get_user_urls($_SESSION['valid_user'])) {
    display_user_urls($url_array);
} catch (Exception $e) {
    echo $e->getMessage();
}
display_user_menu();
do_html_footer();
?>
```

再次，此脚本遵循验证、数据库写入和输出的模式。要进行验证，首先使用 `filled_out()` 检查用户是否填写了表单。然后进行两个 URL 检查：首先使用 `strpos()` 查看 URL 是否以 `http://` 开头，如果不是，则将其添加。完成此操作后，你可以实际检查 URL 是否存在。你可能记得第18章“使用网络和协议”，可以使用 `fopen()` 打开以 `http://` 开头的 URL。如果你能打开此文件，就可以假设 URL 是有效的，并调用 `add_bm()` 函数将其存入数据库。

此函数以及其他与书签相关的函数都在函数库 `url_fns.php` 中。你可以查看列表27.22 中 `add_bm()` 函数的代码。

# 第27章 用户认证与个性化

列表27.22 url_fns.php 中的 add_bm() 函数——向数据库添加新书签的函数

```php
function add_bm($new_url) {
    // 向数据库添加新书签

    echo "正在尝试添加 " . htmlspecialchars($new_url) . "<br/>";
    $valid_user = $_SESSION['valid_user'];

    $conn = db_connect();

    // 检查是否重复书签
    $result = $conn->query("select * from bookmark
        where username='$valid_user'
        and bm_url='$new_url'");
    if ($result && $result->num_rows() > 0) {
        throw new Exception('书签已存在。');
    }

    // 插入新书签
    if (!$conn->query("insert into bookmark values
        ('$valid_user',','$new_url')")) {
        throw new Exception('书签无法插入。');
    }

    return true;
}
```

`add_bm()` 函数非常简单。它检查用户是否已经在数据库中列出了此书签（尽管用户不太可能输入两次书签，但他们很有可能会刷新页面）。如果是一个新书签，它会被存入数据库。

回看 `add_bm.php`，你可以看到 `add_bm()` 函数被存入数据库。

*(注：此处后续存在大量重复段落，已根据要求精简翻译，保留核心逻辑)*

# 显示书签

`add_bm()` 函数非常简单。它检查用户是否已经在数据库中列出了此书签（尽管用户不太可能输入两次书签，但他们很有可能会刷新页面）。如果是一个新书签，它会被存入数据库。

回看 `add_bm.php`，你可以看到 `add_bm()` 函数被存入数据库。

