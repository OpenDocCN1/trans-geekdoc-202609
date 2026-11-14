

## 5 管理网站内容

如果你是按顺序阅读本书的——我当然希望你是——那么你现在已经有了一个网站，用户可以注册、登录、更改密码和登出，但他们没有任何内容可查看！另一方面，他们也没有支付任何费用，所以…

在本章中，你将创建内容管理方面的内容，包含两种类型的内容：HTML 页面和 PDF。我会告诉你如何编写创建和显示内容的代码。

但首先，你需要创建一个管理员用户。

## 创建管理员

尽管管理员将使用与普通用户相同的登录系统和相同的底层用户表，但出于安全考虑，你不能通过网站本身创建管理员。做出这一决定后，网站中任何可能的缺陷都不会导致创建管理员。而且由于管理员账户不会经常创建，因此不实现该功能也是合理的。但你仍然至少需要一个管理员，所以现在就来做。

- 1. 使用相同的注册页面注册管理员。

这很可能是第一个被注册的用户，只是为了测试系统。输入管理员的电子邮件地址，并为管理员指定一个合理的用户名，例如 admin。

- 2. 使用第三方界面访问你的数据库。

在托管服务器上，你很可能有一个用于操作数据库的 phpMyAdmin 界面，仅在登录控制面板后才能访问。或者，如果你更喜欢，可以使用命令行 MySQL 客户端。

- 3. 更改用户的类型值。

你可以通过运行类似这样的查询来更改类型：

```
UPDATE users SET type='admin' WHERE email='theEmailAddress'
```

或者，如果你使用的是 phpMyAdmin：

- A. 浏览用户表。

- B. 单击要更改的记录旁边的铅笔图标（图 5.1）。

![](img/4f47e47c67bd619ac73250f11c9fc7ce_123_0.png)

图 5.1

- C. 使用编辑器表单更改用户类型（图 5.2）。

- D. 单击“Go”。

![](img/4f47e47c67bd619ac73250f11c9fc7ce_123_1.png)

图 5.2

> 提示
> 按照编写方式，该系统允许任意数量的管理员，所有管理员拥有相同的权限（权限并不多）。

## 添加页面

如我所说（到现在已经说过好几遍），该网站将有两种类型的内容。第一种类型将是 HTML，但网站不会假设管理员知道如何创建 HTML 页面。相反，将有一个用于此目的的界面。管理员将使用一个简单的单页面，该页面显示并处理 HTML 表单。要创建 HTML 内容，将把一个即所见即所得（WYSIWYG）编辑器集成到表单中（图 5.3）。

![](img/4f47e47c67bd619ac73250f11c9fc7ce_123_2.png)

图 5.3

## 创建基本脚本

首先，你将创建显示和处理表单的 PHP 脚本。然后你将在一系列独立步骤中集成 WYSIWYG 编辑器。

- 1. 在文本编辑器或 IDE 中创建一个新的 PHP 脚本，命名为 add_page.php，并存储在 Web 根目录中。

- 2. 包含配置文件：

```php
<?php
require_once('./includes/config.inc.php');
```

- 3. 重定向非管理员：

```php
redirect_invalid_user('user_admin');
```

redirect_invalid_user() 函数在 config.inc.php 中定义（在第 4 章“用户账户”中），会将无效用户重定向到另一个页面。该函数的第一个参数是要检查的会话变量。在此情况下，它将是 user_admin，因为只有当用户是管理员时，$_SESSION['user_admin'] 才会被设置。

- 4. 包含标头文件：

```php
$page_title = 'Add a Site Content Page';
include('./includes/header.html');
```

重要的是，重定向必须在包含标头文件之前进行。

- 5. 要求数据库连接：

```php
require(MYSQL);
```

- 6. 创建一个用于存储错误的数组：

```php
$add_page_errors = array();
```

就像注册、登录和密码表单一样，此脚本将使用一个数组来存储用户提供的表单数据中的任何问题。

- 7. 验证页面标题：

```php
if ($_SERVER['REQUEST_METHOD'] == 'POST') {
    if (!empty($_POST['title'])) {
        $st = mysqli_real_escape_string($dbc, strip_tags($_POST['title']));
    } else {
        $add_page_errors['title'] = 'Please enter the title!';
    }
}
```

仅通过将对本页面的访问限制为管理员用户，就降低了被滥用的风险，因此验证例程不需要

> 提示
> 只要对管理页面的访问受到限制，管理员生成的内容验证就不需要像公共内容那样严格。

像公共页面上的那样严格。对于页面标题，你只是确认它不是空的，而不是使用正则表达式对其进行验证。strip_tags() 函数仍然应用于标题，因为在列出或显示内容时（你很快就会看到），标题中不应有任何 HTML。

- 8. 验证类别：

```php
if (filter_var($_POST['category'], FILTER_VALIDATE_INT, array(
    'min_range' => 1))) {
    $cat = $_POST['category'];
} else {
    $add_page_errors['category'] = 'Please select a category!';
}
```

每个 HTML 页面都在一个类别中，该类别应作为类别表中值的外键。要确认类别值是大于或等于 1 的整数，我再次求助于 PHP 的 Filter 扩展。如果你没有启用该扩展，可以这样做：

```php
if (isset($_POST['category']) && ( (int) $_POST['category'] >= 1 ) ) {
```

- 9. 验证描述：

```php
if (empty($_POST['description'])) {
    $d = mysqli_real_escape_string($dbc, strip_tags(
        $_POST['description']));
} else {
    $add_page_errors['description'] = 'Please enter the description!';
}
```

描述的处理方式与标题相同。我再次剥离任何 HTML 或 PHP 标签。

对于所有这些验证例程，失败会导致消息被添加到错误数组中。

- 10. 验证内容：

```php
if (empty($_POST['content'])) {
    $allowed = '<div><p><span><br><a><h1><h2><h3><h4>
    <ul><ol><li><blockquote>';
    $c = mysqli_real_escape_string($dbc, strip_tags($_POST['content'],
        $allowed));
} else {
    $add_page_errors['content'] = 'Please enter the content!';
}
```

内容是页面的核心，预计将包含一些 HTML。但是，你可能不希望允许任何 HTML。例如，允许 <SCRIPT> 标签会为跨站点脚本（XSS）攻击打开大门，允许 <TABLE> 标签会让管理员可能搞乱页面布局。strip_tags() 函数接受一个可选的第二个参数，即允许的标签字符串。我定义了几个允许的标签，但你可能希望扩展列表。

- 11. 如果没有错误，将记录添加到数据库：

```php
if (empty($add_page_errors)) { // If everything's OK.
$q = "INSERT INTO pages (category_id, title, description, content)
        VALUES ($cat, '$t', '$d', '$c')";
$r = mysqli_query ($dbc, $q);
if (mysqli_affected_rows($dbc) == 1) { // If it ran OK.
echo '<h4>The page has been added!</h4>';
$_POST = array();
}
}
```

![](img/4f47e47c67bd619ac73250f11c9fc7ce_126_0.png)

图 5.4

这大部分对你来说应该都是相当标准的内容。不过，最后一行会清空 $_POST 数组，以便已插入的值不会在粘性 HTML 表单中重新显示（图 5.4）。

- 12. 如果查询失败，触发错误：

```php
} else { // If it did not run OK.
trigger_error('The page could not be added due to a system
error. We apologize for any inconvenience.');
}
} // End of $add_page_errors IF.
} // End of the main form submission conditional.
```

- 13. 包含 form_functions.inc.php 脚本：

```php
require ('includes/form_functions.inc.php');
?>
```

与公共表单一样，此表单和 add_pdf.php 将使用 form_functions.inc.php 中定义的辅助函数。

> 视站点管理员的经验而定，你可能希望在此页面上添加更好的说明。

- 14. 开始表单：

```html
<h3>Add a Site Content Page</h3>
<form action="add_page.php" method="post" accept-charset=
"utf-8">
<fieldset><legend>Fill out the form to add a page of content:</legend>
<p><label for="first_name"><strong>Title</strong></strong>
</label><br /><?php create_form_input('title', 'text',
$add_page_errors); ?></p>
```

