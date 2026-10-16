
你想要做三件事：

- 1. 连接数据库
- 2. 查询数据库
- 3. 关闭数据库连接

在执行这三件事之前，让我们为名字和姓氏创建两个变量：

```
$first_name = $_POST['first_name'];
$last_name = $_POST['last_name'];
```

### 打开数据库连接

在 else { 语句之后（但在闭合 ?> 之前）我们使用 mysqli_connect()⁶ 函数连接到数据库。该函数默认接受四个字符串参数：host、username、password 和 database_name。我们的 mysqli_connect() 语句应如下所示：

```
$dbc = mysqli_connect('localhost', 'testuser', 'testuser', 'FullName')
    or trigger_error('Error connecting to MySQL server.', E_USER_ERROR);
```

> 在源代码中以明文形式输入密码并不是一个好主意（尤其是如果我们不小心将其发布到某个 git 仓库）。更好的管理方式是使用配置文件或环境变量。

如果 mysqli_connect() 调用成功，$dbc 将包含指向我们数据库的资源连接。使用 or trigger_error() 语句是个好主意，这样你就可以确定在连接数据库时是否遇到问题。如果失败，你将在网页上看到错误信息，并且 PHP 脚本的执行将停止。

> 为什么不用 or die()？你很可能会遇到使用 die() 语句来停止并显示消息的旧代码或在线旧教程。由于它会停止 PHP 解释器的执行，你的错误信息不会记录到 PHP 的错误日志中，也不会传递给任何自定义错误处理器。此外，通知用户遇到错误的唯一方式就是等待有人报告故障。带有 E_USER_ERROR 级别的 trigger_error() 在没有这些缺点的情况下具有相同的效果。

[6] mysqli_connect(): http://php.net/function.mysqli-connect

## 12. 向 MySQL 数据库插入数据

### 向数据库插入全名

接下来我们想要构建一个 SQL SELECT 查询并使用 mysqli_query() 函数[7]将其发送到数据库。该函数接受两个参数：数据库连接资源和查询字符串。我们的查询字符串和 mysqli_query() 语句应如下所示：

```
$query = "INSERT INTO fullName (first_name, last_name)"
  . " VALUES ('$first_name', '$last_name')";

$result = mysqli_query($dbc, $query);
```

如果 mysqli_query() 调用成功，$result 包含 TRUE。否则，如果查询失败，则返回 FALSE。你也可以同样使用 or trigger_error() 语句。

### 关闭数据库连接

最后，使用 mysqli_close() 函数关闭数据库连接。该函数接受一个参数：数据库连接。我们的 mysqli_close() 语句应如下所示：

```
mysqli_close($dbc);
```

> 每当我们想要查询数据库时，一种方法是连接到数据库、执行查询，然后关闭数据库连接。不要让数据库连接保持打开状态不是一个好主意。它会占用线程资源，如果你有一个大型应用程序同时存在多个打开的连接，则可能成为潜在问题。假设你正在编写一个大型应用程序，该应用程序可能在同一时间有许多打开的数据库连接。在这种情况下，你应该考虑在完成与数据库的交互后关闭连接，而不是等待脚本结束。

> 另一方面，PHP 会在脚本终止时自动关闭任何打开的数据库连接。对于小型到中型的应用程序，或者如果你的查询分布在许多函数中，你可以跳过显式调用 mysqli_close()。

综合起来，我们的脚本现在看起来像列表 12.2。

[7] mysqli_query() function: http://php.net/mysqli_query

### 列表 12.2.

```
```php
<html>
<head>
<title>Form for Entering Full Name</title>
</head>
<body>
<?php if (!isset($_POST['submit'])) { ?>
<h2>Enter Full Name</h2>
<form action="<?=$_SERVER['PHP_SELF']?>" method="POST">
First name:<br/>
<input type="text" name="first_name"/><br/>
Last name:<br/>
<input type="text" name="last_name"/><br/>
<p>
<input type="submit" name="submit" value="Submit Name" />
</form>
<?php } else { ?>
<h2>Greetings!</h2>
<?php
// Grab full name from form
$first_name = $_POST['first_name'];
$last_name = $_POST['last_name'];

// Insert full name into database
$dbc = mysqli_connect('localhost', 'testuser', 'testuser', 'FullName')
or trigger_error('Error connecting to MySQL server.', E_USER_ERROR);

$query = "INSERT INTO fullName (first_name, last_name)"
. " VALUES ('$first_name', '$last_name')";

$result = mysqli_query($dbc, $query);
or trigger_error('Error querying database.', E_USER_WARNING);

if (!$result)
{
trigger_error("Query Error description: "
. mysqli_error($dbc), E_USER_WARNING);
}

mysqli_close($dbc);
?>
<br/><br/>Hello <?= $first_name . " " . $last_name; ?>
Thanks for submitting the form!
<?php } ?>
</body>
</html>
```
```

## 12. 向 MySQL 数据库插入数据

### 测试和验证

### 预期结果

让我们运行我们的应用程序并验证我们是否正确地将项目插入数据库。

如果一切顺利，我们应该得到图 12.25 所示的预期输出。

现在让我们检查一下我们的全名是否确实插入到了 fullName 表中。在 MySQL CLI 工具中，选择 fullName 表中的所有字段和行：

```
SELECT * FROM FullName;
```

根据你的输入，你应该会看到像图 12.26 中那样的一行新记录。

### 成功！

### 可能出现的问题

现在可能会出现一些常见错误，这将阻止你的应用程序成功运行。最常见的问题往往与数据库通信有关。由于 PHP 编码错误导致的错误可以使用标准调试器以及像 Xdebug[8] 这样的工具和像 JetBrains’ PhpStorm 这样的 PHP 集成开发环境（IDE）来找到。

关于数据库通信错误，使用像 Adminer 这样的数据库管理工具或（对于我们的示例）MySQL CLI 工具来验证你的连接参数是否有效是有帮助的。数据库通信错误通常涉及无法连接到数据库或 SQL 查询格式错误。让我们看看这两者。

[8] Xdebug: http://xdebug.org

![](img/83a2e1d9463a10cf8d6f7fe54ee4b1c7_132_0.png)

![](img/83a2e1d9463a10cf8d6f7fe54ee4b1c7_132_1.png)

![](img/83a2e1d9463a10cf8d6f7fe54ee4b1c7_132_2.png)

## 创建 PHP 应用程序以插入数据

### 数据库连接失败

无法连接到数据库通常涉及 mysqli_connect() 函数的一个或多个参数不正确，这可能是凭据错误或数据库名称不存在。

例如，你可能会看到像图 12.27 那样的输出。

错误输出可能相当难以解读。然而，我们确实知道我们的 mysqli_connect() 调用失败了。我们还可以看到给出的原因是：

```
php_network_getaddresses: getaddrinfo failed: Name or service not known in
```

我们看到网络地址存在问题这一事实是线索，说明出了什么问题。在 PHP 手册中查找 mysqli_connect()[9] 函数定义，我们看到期望的第一个参数是 SQL 服务器的主机名或 IP 地址。查看我们代码的第 24 行，我们看到图 12.28。

我们很快发现我们输入的是 localhosed 而不是 localhost，这可以快速修复。

![](img/83a2e1d9463a10cf8d6f7fe54ee4b1c7_133_0.png)

![](img/83a2e1d9463a10cf8d6f7fe54ee4b1c7_133_1.png)

假设我们看到图 12.29 中的输出。

给出的原因是：

```
Access denied for user 'testusers'@'localhost'...
```

![](img/83a2e1d9463a10cf8d6f7fe54ee4b1c7_133_2.png)

因为我们看到访问被拒绝，这告诉我们 mysqli_connect() 的用户名或密码参数不正确。查看我们代码的第 24 行，我们看到图 12.30。

![](img/83a2e1d9463a10cf8d6f7fe54ee4b1c7_133_3.png)

查看用户名参数，我们可以看到它拼写错误并且末尾多了一个 s。

[9] mysqli_connect(): https://php.net/mysqli_connect

