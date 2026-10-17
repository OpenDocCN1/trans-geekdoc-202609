
- 虽然数组元素的键通常应为数字或仅包含字母数字字符的字符串，但 `Zend_Db` 允许这种非常规语法，作为便利的快捷方式。

- 由于第三个参数可以是数组，你可以组合多个条件来定位要更新的记录，例如：

```php
$where['email = ?'] = $_POST['email'];
$where['username = ?'] = $_POST['username'];
$dbWrite->update('users', $data, $where);
```

- 这会更新 `users` 表中满足 `email` 列等于 `$_POST['email']` **且** `username` 列等于 `$_POST['username']` 的记录。

- ![Image](img/note.jpg) **NOTE:**  
  将多值数组作为 `update()` 方法的第三个参数等价于在 SQL `WHERE` 子句中使用 `AND` 运算符。若要使用 `OR` 运算符指定备选条件，则需将第三个参数构造为字符串。

- 如果在 `update()` 方法中省略第三个参数，则会更新表中**所有**记录，且更新方式相同。

- 为安全起见，`Zend_Db` 会将数据数组中的值转换为字符串并转义特殊字符。因此，你不能直接在数据数组中包含 SQL 函数（如 `CURDATE()` 用于当前日期）。相反，需要使用 `Zend_Db_Expr` 将 SQL 函数包装，例如：

```php
$data = array(
    'password' => $_POST['password'],
    'registered' => new Zend_Db_Expr('CURDATE()')
);
```

若要在 `update()` 方法的第三个参数中使用 SQL 函数，可这样操作：

```php
$today = new Zend_Db_Expr('CURDATE()');
$where = "start_date > $today";
```

- 在处理密码重置请求脚本之前，先了解其所需的决策链。下面的插图概述了整个流程。

![Image](img/fig08_23.jpg)

- 重置请求表单只包含一个用于输入用户邮箱地址的字段。处理脚本需要检查该邮箱是否已注册。若未注册，则显示错误信息并终止后续处理。

- 若邮箱已存在，脚本会从数据库获取用户信息并生成一个 32 字符的安全令牌（难以猜测）。同时，用户记录会被更新，将该令牌存入数据库。随后，会向用户发送包含重置密码页面链接的电子邮件。链接的查询字符串中会附带用户的主键和安全令牌，以供后续验证身份。将链接直接发送至用户注册的邮箱，可确保只有该用户能够进行密码重置。

- 本部分完成后，会在屏幕上显示一条消息，提示用户查收包含重置说明的邮件。

- 虽然流程看似复杂，但所需的 PHP 代码不超过 40 行：

**1.** 将 `request_reset.php` 从 `lesson08/start/scripts` 复制到 `lesson08/workfiles/scripts`。该文件已包含以下代码：

```php
$errors = FALSE;  
$result = FALSE;  
if ($_POST) {  
    require_once('library.php');  
    require_once('mail_connector.php');  
    try {  
    } catch (Exception $e) {  
        echo $e->getMessage();  
    }  
}
```

只需要一个错误信息，因此 `$errors` 设为 `FALSE`。若邮箱验证失败或未注册，则将其设为 `TRUE`。

另一个布尔变量 `$result` 用于决定是显示表单还是提示用户等待邮件。它最初为 `FALSE`，随后用于存储数据库查询的结果。若未在数据库中找到记录，则保持 `FALSE`；否则，它会是一个包含用户详细信息的数组（PHP 会将其视为 `TRUE`）。

**2.** 在 `try` 块内部，先对用户输入进行验证。添加以下代码：

```php
$val = new Zend_Validate_EmailAddress();  
if (!$val->isValid($_POST['email'])) {  
    $errors = TRUE;  
}
```

**3.** 若邮箱通过验证，则使用它查询数据库。添加以下代码来构建 SQL 语句并执行查询：

```php
if (!$errors) {  
    $sql = $dbRead->quoteInto('SELECT user_id, first_name, family_name, email FROM users WHERE email = ?', $_POST['email']);  
    $result = $dbRead->fetchRow($sql);  
}
```

这是一个 `SELECT` 查询，使用只读账户的 `quoteInto()` 方法安全地将用户输入嵌入 SQL。查询从 `users` 表中取出四列：`user_id`、`first_name`、`family_name`、`email`。

在 第 7 课 中，你使用过 `fetchAll()`，但本例使用 `fetchRow()`。请参阅“Choosing Between fetchAll() and fetchRow()”侧边栏，了解两者的区别。

**Choosing Between `fetchAll()` and `fetchRow()`**  
主要区别在于：`fetchAll()` 返回所有匹配行，而 `fetchRow()` 仅返回第一行。在 第 7 课 中，只需判断是否存在匹配即可，因此使用哪种方法均不影响结果。但当需要访问具体值时，选择就很重要。`fetchRow()` 只取一行，结果以列名为键的关联数组形式存储，例如 `$result['user_id']`。

当你使用 `fetchAll()` 时，结果始终以多维数组形式存储，每一行都有一个子数组——即使只有一行。你通常使用 `foreach` 循环来访问 `fetchAll()` 的结果，例如：

```php
foreach ($result as $row) {  
    // 处理每一行  
}
```

在循环内部，你通过 [oken 和 `$row` 数组通过列名（column name）来访问每个字段，例如：`$row['user_id']`。

如果不使用循环，你需要指定子数组的下标（从 0 开始）来访问，例如：`$result[0]['user_id']`。

**4.** 如果数据库中没有该电子邮件，`fetchRow()` 方法会返回 `FALSE`。因此，如果没有结果，需要将 `$errors` 设置为 `TRUE`。否则，可以继续处理重置请求。在你上一步创建的条件语句中，加入以下代码（已高亮）：

```php
$result = $dbRead->fetchRow($sql);  
if (!$result) {  
    $errors = TRUE;  
} else {  
    // 更新数据库并发送邮件  
}
```

**5.** 如果电子邮件在数据库中存在，需要创建安全令牌并更新用户记录以将其存储在数据库中。在 `else` 块中插入以下代码：

```php
$token = md5(uniqid(mt_rand(), TRUE));  
$data = array('token' => $token);  
$dbWrite->update('users', $data, "user_id = {$result['user_id']}");
```

第一行新代码使用了典型的 PHP 快捷写法，将函数作为参数传递给其他函数。`uniqid()` 函数基于当前时间生成唯一 ID，并可接受两个可选参数以随机化值。第一个参数是 `mt_rand()`，它生成随机数。最终，`uniqid()` 被 `md5()` 包装，这是一个加密函数，生成 32 个字符的十六进制字符串。如果发现细节令人困惑，请放心，只需接受 `$token` 的值应该是任何人都无法猜测的。

第二行创建一个关联数组，将 `$token` 分配给要存储的数据库列的 `name`。

第三行使用 `$dbWrite` 数据库对象（具有读写权限）来更新用户记录。第三个参数使用数据库结果中的 `user_id` 主键来标识要更新的记录。由于 `$result['user_id']` 是数组元素，需要用大括号将其包裹在双引号字符串中。`$result['user_id']` 的值是记录的主键，为自动递增的整数，直接用于第三个参数是安全的。由于它是数字，不需要加引号。

第二行创建的关联数组将 `$token` 分配给要存储的数据库列的 `name`。

第三行使用 `$dbWrite` 数据库对象（具有读写权限）来更新用户记录。第三个参数使用数据库结果中的 `user_id` 主键来标识要更新的记录。由于 `$result['user_id']` 是数组元素，需要用大括号将其包裹在双引号字符串中。`$result['user_id']` 的值是记录的主键，为自动递增的整数，直接用于第三个参数是安全的。由于它是数字，不需要加引号。

**6.** 现在，你需要向用户发送邮件，并附上重置密码页面的链接。在 `else` 块中插入以下脚本，使用你自己的电子邮件地址在 `setFrom()` 方法中：

```php
$mail = new Zend_Mail('UTF-8');  
$mail->addTo($result['email'], "{$result['first_name']} {$result['family_name']}");  
$mail->setSubject('Instructions for resetting your password');  
$mail->setFrom('webmaster@example.com', 'DW CS5 with PHP');  
$link = "http://phpcs5/lesson08/workfiles/reset.php?id={$result['user_id']}&token=$token";  
$message = "Use the following link to reset your password. This link can be used once only. $link";  
$mail->setBodyText($message, 'UTF-8');  
$mail->send();
```

创建并发送邮件在本课程早期已详细说明，因此这段代码应易于理解。

从数据库结果中提取的值用于通过 `addTo()` 的第一个参数设置收件人地址，并用双引号字符串将 `first_name` 和 `family_name` 的值包裹，以个性化收件人地址——无论是系统中登记的真实姓名，还是系统登记的姓名。

`$link` 变量包含重置密码页面的 URL，查询字符串包含用户的主键和安全令牌。`$link` 随后被包含在 `$message` 字符串中，并传递给 `setBodyText()`，发送纯文本消息。

**7.** 保存 `request_reset.php`，并将 `lesson08/start` 中的 `forgotten.php` 复制到 `lesson08/workfiles`。`forgotten.php` 中的代码包含两个条件语句，控制屏幕上显示的 HTML。

在 `DOCTYPE` 声明上方使用 `require_once()` 包含 `scripts/request_reset.php`，并加载 `forgotten.php` 到浏览器。你应该看到重置请求表单。

![Image](img/fig08_24.jpg)

**8.** 通过在文本框中输入错误的电子邮件地址并点击提交来测试页面。你应该在表单下方看到错误消息。

![Image](img/fig08_25.jpg)

**9.** 在字段中输入你自己的电子邮件地址，并提交表单。假设你的地址已注册在数据库中，表单应消失，并显示以下消息：

![Image](img/fig08_26.jpg)

不同的消息由 `forgotten.php` 中的条件语句控制。`if… else` 语句使用 `$result` 的值来决定显示表单还是前面截图中的消息。错误消息由 `$errors` 的值控制。

**10.** 如果网络神明眷顾你，你应该收到类似下面的电子邮件：

![image](img/fig08_27.jpg)

你已准备好继续到重置密码脚本。你可以将你的代码与 `lesson08/completed/scripts/request_reset.php` 进行比较。

如果在步骤 9 中看到成功消息但未收到邮件，最可能的原因是网络问题或邮件被邮件服务器拒绝。在 `setFrom()` 方法中使用假地址是常见原因，因为该邮件被视为垃圾邮件。

### 构建重置密码脚本

重置用户密码的脚本在更新数据库记录之前需要进行几项检查。首先，它需要验证 `user_id` 和安全令牌是否匹配。如果不匹配，则无需继续。如果匹配，下一步是验证新密码，使用与 Lesson 7 相同的技术。如果密码可接受，脚本最终可以更新用户记录。以下插图概述了决策链。

![Image](img/fig08_28.jpg)

尽管这里有很多内容，但最终脚本仅 45 行。

**1.** 复制 `lesson08/start/reset.php` 到 `lesson08/workfiles`，并在分屏视图中检查代码。在设计视图中，可以看到有三段 HTML：密码已重置的确认信息、错误消息以及包含两个密码字段的表单。`<span>` 标签上应用了 `Display Error Message` 服务器行为。与 `forgotten.php` 一样，一系列条件语句控制显示内容。

**2.** 复制 `lesson08/start/scripts/reset_password.php` 到 `lesson08/workfiles/scripts`。该文件包含以下基本代码：

```php
session_start();  
$_SESSION['nomatch'] = TRUE;  
$errors = array();  
$success = FALSE;  
require_once('library.php');  
try {  
} catch (Exception $e) {  
    echo $e->getMessage();  
}
```

脚本需要跟踪用户身份以更新正确的数据库记录。你可以将详细信息存储在隐藏表单字段中，但更安全的做法是使用服务器端会话变量。因此，脚本通过 `session_start()` 启动会话，并创建会话变量 `$_SESSION['nomatch']`，将其设置为 `TRUE`。`$_SESSION['nomatch']`、`$errors` 和 `$success` 控制 `reset.php` 中显示的内容。

脚本每次加载页面时都需要访问数据库，因此立即包含 `library.php`。

**3.** 回到 `reset.php`，并在 `DOCTYPE` 声明上方使用 `require_once()` 包含 `scripts/reset_password.php`。

**4.** 在打开的 `<form>` 标签（约第 21 行）中，它当前的样子是：

```html
<form id="form1" name="form1" method="post" action="">
```

`action` 属性告诉浏览器当表单提交时处理数据的脚本地址。如果没有地址，则假定表单是自处理的——换句话说，它将数据提交到同一页面。这个表单是自处理的，但有一个微妙的区别。

用户通过电子邮件链接访问此页面，该链接向 URL 附加了一个查询字符串。如果你将表单的 `action` 属性留空，则提交表单时查询字符串会保留在 URL 中，这会给处理脚本带来问题。必须删除查询字符串。

PHP 方便地将不带查询字符串的基本 URL 存储在一个名为 `$_SERVER['PHP_SELF']` 的超全局变量中。使用 `echo` 将页面 URL 插入 `action` 属性，如下所示：

```html
<form id="form1" name="form1" method="post" action=" <?php echo $_SERVER['PHP_SELF']; ?>">
```
