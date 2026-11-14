

在字符串中，这需要所谓的 _零宽正向先行断言_，由 ?= 表示。正向先行断言根据字符后面的内容进行匹配。与其读一页关于此模式如何超出该简单定义工作的解释，不如你亲自测试一下以确认其有效性，如果你真的好奇，可以在线研究零宽正向先行断言。

- 8. 如果没有错误，则检查电子邮件地址和用户名的可用性：

```
if (empty($reg_errors)) {
    $q = "SELECT email, username FROM users WHERE email='$e' OR 
    \tusername='$u'";
    $r = mysqli_query ($dbc, $q);
    $rows = mysqli_num_rows($r);
    if ($rows == 0) { // No problems!
}
```

如果 $reg_errors 数组仍为空，则未发生任何错误（因为即使只有一个错误也会向此数组添加一个元素，使其不再为空）。接下来，一个查询会查找任何具有提交的电子邮件地址或用户名的现有记录。理论上，此查询最多可能返回 2 条记录（一条用于电子邮件地址，一条用于用户名）；如果它未返回任何记录，则可以安全地继续。

> **note**
> 
> 事实上，我只是添加了用户名字段来演示如何保证电子邮件地址和用户名的唯一性。

- 9. 将用户添加到数据库中：

```
$q = "INSERT INTO users (username, email, pass, first_name,
    \tlast_name, date_expires) VALUES ('$u', '$e', ''
    . create_password_hash($p) . '', '$fn', '$ln', ADDDATE(NOW(),
    \tINTERVAL 1 MONTH))";
$r = mysqli_query ($dbc, $q);
```

该查询使用提交的值在数据库中创建新记录。请注意，对于密码值，会调用 get_password_hash() 函数。无需设置用户的类型，因为如果未为 ENUM 列提供值，将使用第一个枚举值——这里是 _member_。

在第 6 章“使用 PayPal”中集成 PayPal 之前，我将帐户到期日期设置为一个月后。一旦集成了 PayPal，到期日期将设置为昨天。在这种情况下，当 PayPal 返回成功付款的指示时，用户的帐户将设置为一年后到期。

> **note**
> 
> 作为安全措施，用户的类型在注册流程之后只能是 _member_。您必须进入数据库并手动更改用户的类型，才能创建管理员。

- 10. 如果查询创建了一行，则感谢新客户并发送电子邮件：

```
if (mysqli_affected_rows($dbc) == 1) {
echo '<h3>Thanks!</h3><p>Thank you for registering! You may now
\ log in and access the site's content.</p>';
$body = "Thank you for registering at <whatever site>. Blah. Blah.
\ Blah.\n\n";
mail($_POST['email'], 'Registration Confirmation', $body, 'From:
\ admin@example.com');
include ('./includes/footer.html');
exit();
}
```

> **tip**
> 
> 您可以在配置文件中定义一个电子邮件地址，用于向客户发送消息中的“发件人”地址。

首先，会显示一个 Thanks! 页面（图 4.9）。下一步是将他们发送到 PayPal，我们将在第 6 章中添加此功能。此外，可以向用户发送一封您想要的任何内容的电子邮件，但不要在该电子邮件中包含用户的密码。最后，会包含页脚，并调用 exit() 停止页面。这是必要的，以防止注册表单再次显示，从而使用户困惑。

![](img/4f47e47c67bd619ac73250f11c9fc7ce_104_0.png)

图 4.9

- 11. 如果查询失败，则创建错误：

```
} else {
 trigger_error('You could not be registered due to a system error. We
\ apologize for any inconvenience.');
}
```

此时，如果查询未创建新行，则存在数据库或查询错误。在这种情况下，会使用 trigger_error() 函数生成错误，该错误将由配置文件中的错误处理程序管理。在已经过测试的实际运行站点上，这可能仅在数据库服务器宕机或过载时发生。

- 12. 如果电子邮件地址或用户名不可用，则创建错误：

```
} else {
if ($rows == 2) { // Both are taken.
$reg_errors['email'] = 'This email address has already been
registered. If you have forgotten your password, use the link at
right to have your password sent to you.';
$reg_errors['username'] = 'This username has already been
registered. Please try another.';
}
```

如果 SELECT 查询返回任何记录，则适用 else 子句。这意味着电子邮件地址和/或用户名已被注册。现在我们需要确定哪个值是罪魁祸首。如果返回了两行，则两者都已被注册。假设是同一客户已注册（因为其电子邮件地址在系统中），而另一客户已拥有该用户名（因为它与不同的电子邮件地址关联）。错误消息会添加到 $reg_errors 数组中，分别以 email 和 username 为索引，以便在重新显示表单时，它们会出现在相应的表单输入旁边。

- 13. 确认已注册的项目：

```
} else { // One or both may be taken.
$row = mysqli_fetch_array($r, MYSQLI_NUM);
if (($row[0] == $_POST['email']) && ($row[1] == $_POST['username'])) { // Both match.
$reg_errors['email'] = 'This email address has already been
registered. If you have forgotten your password, use the link at
right to have your password sent to you.';
$reg_errors['username'] = 'This username has already been
registered with this email address. If you have forgotten your
password, use the link at right to have your password sent to
you.';
} elseif ($row[0] == $_POST['email']) { // Email match.
$reg_errors['email'] = 'This email address has already been
registered. If you have forgotten your password, use the link at
right to have your password sent to you.';
} elseif ($row[1] == $_POST['username']) { // Username match.
$reg_errors['username'] = 'This username has already been
registered. Please try another.';
}
} // End of $rows == 2 ELSE.
```

如果只返回了一行，则代码需要确定是用户名匹配、电子邮件地址匹配，还是两者在同一条记录中都匹配。三个条件语句分别测试每种可能性，并分配相应的错误消息（图 4.10 和 4.11）。

![](img/4f47e47c67bd619ac73250f11c9fc7ce_106_0.png)

![](img/4f47e47c67bd619ac73250f11c9fc7ce_106_1.png)

> **note**
> $rows == 后面的字符是零。

- 14. 完成条件语句：
- } // $rows == 0 IF 结束。
- } // empty($reg_errors) IF 结束。
- } // 主表单提交条件语句结束。
- 15. 保存并测试注册脚本。

# 激活帐户

对于不需要付费的站点，我通常会包含激活流程：

- 1. 当用户注册时，随机代码会存储在 users 表中。
- 2. 电子邮件会发送到注册的电子邮件地址，其中包含站点激活页面的链接。链接会将用户的电子邮件地址和特定代码传递到 PHP 页面：https://www.example.com/activate.php?x=email@example.com&y=CODE
- 3. PHP 页面会确认表中存在具有该电子邮件地址和代码组合的记录，然后激活该帐户（通常是通过将 code 列设置为 NULL）。
- 4. 当用户登录时，查询必须确认电子邮件和密码组合正确，并且表中的 code 列具有 NULL 值。

这被称为“闭环”确认流程，可防止虚假注册。在“知识就是力”站点中，使用 PayPal 将防止虚假注册，因为黑客通常不会在黑客攻击尝试中花钱。

# 登录

登录站点是一个两步过程：完成表单，并根据数据库验证提交的值。登录表单不是独立页面——它显示在所有未登录用户的侧边栏中，因此不能使用与 register.php 中相同的单脚本方法。那么问题在于，用户在成功登录和未成功登录时应该被导向哪里。在两种情况下，我都决定他们应返回主页；出于此原因，登录表单会提交到 index.php。因此，需要使用处理表单的代码更新 index 页面。与其将代码直接写入主页，不如将其作为单独的文件包含，位于数据库连接之后、包含头文件之前：

```
if ($_SERVER['REQUEST_METHOD'] == 'POST') {
    include('./includes/login.php');
}
```

之所以可行，是因为通常 index.php 将通过 GET 请求。如果是 POST 请求，则表示已提交登录表单，因此此脚本将包含用于测试登录凭据的文件。

### 处理表单

我认为，如果最后再谈表单，实际上更容易跟踪登录流程，因此让我们先查看处理登录表单的代码。该过程需要：

- 1. 验证提交的电子邮件地址和密码。
- 2. 将提交的值与数据库中的值进行比较。
- 3. 如果值不正确，则创建错误。
- 4. 如果值正确，则将数据存储在会话中。

以下是实际代码的工作原理：

- 1. 在文本编辑器或 IDE 中创建一个名为 login.inc.php 的新 PHP 脚本。
- 它将存储在 **includes** 目录中。

- 2. 创建一个空数组用于记录错误：

```
<?php
$login_errors = array();
```

此错误数组将像注册脚本中的 $reg_errors 一样使用。

> 通过包含登录处理代码，而不是将其写入 index.php 文件，我保持了更好的代码分离。

> 最好为包含文件中的变量命名唯一名称，以免它们覆盖父脚本中创建的任何变量。

