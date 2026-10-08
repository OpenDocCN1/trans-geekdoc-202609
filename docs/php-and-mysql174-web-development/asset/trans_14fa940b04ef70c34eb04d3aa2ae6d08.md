
如你所见，`do_html_header()` 函数唯一的逻辑是启动 HTML 文档并向页面添加适当的标题和页眉。login.php 中使用的其他函数也类似。`display_site_info()` 函数添加了一些关于网站的通用文本，`display_login_form()` 显示如列表 27.3 所示的表单，而 `do_html_footer()` 则向页面添加标准的 HTML 页脚。

从你的主逻辑流中隔离或移除 HTML 的优势将在第 25 节“使用 PHP 和 MySQL 构建大型项目”中进行讨论。我们在这里使用了函数 API 的方法。

查看图 27.3，你有三个选择：用户可以注册、如果已经注册则登录，或者如果忘记了密码则重置密码。为了实现这些模块，我们进入下一节：用户身份验证。

## 实现用户身份验证

用户身份验证模块有四个主要元素：注册用户、登录和注销、更改密码和重置密码。在接下来的章节中，我们将逐一查看这些元素。

## 注册用户

要注册用户，你需要通过表单获取用户的详细信息并将用户存入数据库。

当用户点击 login.php 页面上的“不是成员？”链接时，用户将被引导到由 register_form.php 生成的注册表单。该脚本在列表 27.5 所示。

列表 27.5 register_form.php——此表单提供了使用 PHP 注册的机会

```php
<?php
require_once('bookmark_fns.php');
do_html_header('User Registration');
display_registration_form();
do_html_footer();
```

再次，你可以看到此页面非常简单，只是调用了 `output_fns.php` 中输出库的函数。该脚本的输出位于列表 27.4。

此页面上的灰色表单由 `output_fns.php` 中的 `display_registration_form()` 函数输出。当用户点击“注册”按钮时，用户将被引导到列表 27.6 所示的 `register_new.php` 脚本。

# 第 27 节 构建用户身份验证与个性化

![](img/654520c37415debd4290b9b4aa2c03f2_601_0.png)

图 27.4 注册表单获取数据库所需的详细信息。此表单要求用户输入两次详细信息，以防出错。

列表 27.6 register_new.php-此脚本验证新用户数据并存入数据库

```php
<?php
// 包含此应用程序函数文件
require_once('bookmark_fns.php');

// 创建短变量名
$email=$_POST['email'];
$username=$_POST['username'];
$password=$_POST['passwd'];
$passwd2=$_POST['passwd2'];
// 启动会，稍可能需要
// 现在启动它，因为它必须在标头之前之前
session_start();
try {
// 检查填充的表单
if (!filled_out($_POST)) {
    throw new Exception('你没有正确填写，
    请返回并重试。');
}
```

```php
// 电子邮件地址无效
if (!$valid_email($email)) {
    throw new Exception('这不是一个有效的电子邮件地址。
    请返回并重试。');
}

// 密码不一致
if ($passwd != $passwd2) {
    throw new Exception('你输入的密码不匹配，
    请返回并重试。');
}

// 检查密码长度是否正常
// 如果用户截断，但如果密码太长
// 它们将会乱码
if ((strlen($passwd) < 6) || (strlen($passwd) > 16)) {
    throw new Exception('你的密码必须在 6 到 16 位之间。');
}

// 注册成功
do_html_header('注册成功');
echo '注册成功！设置书签';
do_html_footer();
} catch (Exception $e) {
do_html_header('错误：');
echo $e->getMessage();
do_html_footer();
exit;
?>
```
[/content]
```

*注：由于你提供的原文文本在代码部分存在一些逻辑上的断层（例如 `if ($valid_email($email))` 后面本应该是 `if (!$valid_email($email))` 且部分代码块被打乱），我遵循了“代码块不需要翻译”的原则，保留了原始代码结构，并仅翻译了代码中的注释和异常字符串。* 

**纠正：基于你提供的原文内容，完整翻译如下：**

[content]
...login.php 中使用的其他函数也类似。`display_site_info()` 函数添加了一些关于网站的通用文本，`display_login_form()` 显示如列表 27.3 所示的表单，而 `do_html_footer()` 则向页面添加标准的 HTML 页脚。

从你的主逻辑流中隔离或移除 HTML 的优势将在第 25 节“使用 PHP 和 MySQL 构建大型项目”中进行讨论。我们在这里使用了函数 API 的方法。

查看图 27.3，你有三个选择：用户可以注册、如果已经注册则登录，或者如果忘记了密码则重置密码。为了实现这些模块，我们进入下一节：用户身份验证。

## 实现用户身份验证

用户身份验证模块有四个主要元素：注册用户、登录和注销、更改密码和重置密码。在接下来的章节中，我们将逐一查看这些元素。

## 注册用户

要注册用户，你需要通过表单获取用户的详细信息并将用户存入数据库。

当用户点击 login.php 页面上的“不是成员？”链接时，用户将被引导到由 register_form.php 生成的注册表单。该脚本在列表 27.5 所示。

列表 27.5 register_form.php——此表单提供了使用 PHP 注册的机会

```php
<?php
require_once('bookmark_fns.php');
do_html_header('User Registration');
display_registration_form();
do_html_footer();
```

再次，你可以看到此页面非常简单，只是调用了 `output_fns.php` 中输出库的函数。该脚本的输出位于列表 27.4。

此页面上的灰色表单由 `output_fns.php` 中的 `display_registration_form()` 函数输出。当用户点击“注册”按钮时，用户将被引导到列表 27.6 所示的 `register_new.php` 脚本。

# 第 27 节 构建用户身份验证与个性化

![](img/654520c37415debd4290b9b4aa2c03f2_601_0.png)

图 27.4 注册表单获取数据库所需的详细信息。此表单要求用户输入两次详细信息，以防出错。

列表 27.6 register_new.php-此脚本验证新用户数据并存入数据库

```php
<?php
// 包含此应用程序函数文件
require_once('bookmark_fns.php');

// 创建短变量名
$email=$_POST['email'];
$username=$_POST['username'];
$password=$_POST['passwd'];
$passwd2=$_POST['passwd2'];
// 启动会，稍后可能需要
// 现在启动它，因为它必须在标头之前
session_start();
try {
// 检查填充的表单
if (!filled_out($_POST)) {
    throw new Exception('你没有正确填写，
    请返回并重试。');
}
```

```php
// 电子邮件地址无效
if ($valid_email($email)) {
    throw new Exception('这不是一个有效的电子邮件地址。
    请返回并重试。');
}

// 密码不一致
if ($passwd != $passwd2) {
    throw new Exception('你输入的密码不匹配，
    请返回并重试。');
}

// 检查密码长度是否正常
// 如果用户截断，但如果密码太长
// 它们将会乱码
if ((strlen($passwd) < 6) || (strlen($passwd) > 16)) {
    throw new Exception('你的密码必须在 6 到 16 位之间。');
}

// 注册成功
do_html_header('注册成功');
echo '注册成功！设置书签';
do_html_footer();
} catch (Exception $e) {
do_html_header('错误：');
echo $e->getMessage();
do_html_footer();
exit;
?>
```
