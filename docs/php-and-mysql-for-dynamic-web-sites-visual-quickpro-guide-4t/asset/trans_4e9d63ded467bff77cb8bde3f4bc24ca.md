
如果你好奇，![Image](graphics/circle-e.jpg)展示了如果你不在`mysqli_connect()`前使用`@`且发生错误时会发生什么。

![Image](graphics/09_figure_06_e.jpg)

![Image](graphics/circle-e.jpg)如果你不使用错误抑制运算符（`@`），你将同时看到PHP错误和自定义的`OR die()`错误。

---

**Tip**

如果在建立MySQL连接时不需要选择数据库，请从`mysqli_connect()`函数中省略该参数：

```php
$dbc = mysqli_connect(hostname, username, password);
```

然后，在适当的时候，你可以使用以下方式选择数据库：

```php
mysqli_select_db($dbc, db_name);
```

---

### 执行简单查询

一旦你成功连接并选择了数据库，就可以开始执行查询。查询可以像插入、更新和删除一样基础，也可以像返回大量行的复杂连接一样复杂。无论SQL命令类型如何，执行查询的PHP函数都是`mysqli_query()`：

```php
result = mysqli_query(dbc, query);
```

该函数将数据库连接作为第一个参数，查询本身作为第二个参数。在完整的PHP脚本中，我通常将查询赋值给另一个变量，称为`$query`或仅为`$q`，因此运行查询可能如下所示：

```php
$r = mysqli_query($dbc, $q);
```

对于像`INSERT`、`UPDATE`、`DELETE`等简单查询（不返回记录），`$r`变量（result的简写）将是TRUE或FALSE，具体取决于查询是否成功执行。

请记住，“成功执行”意味着它无错误运行；并不意味着查询的执行一定产生了预期结果；你需要测试这一点。

对于返回记录的复杂查询（`SELECT`是其中最重要的），如果查询成功，`$r`将是指向查询结果的资源链接；如果不成功，则为FALSE。因此，你可以在条件语句中使用这行代码来测试查询是否成功运行：

```php
$r = mysqli_query($dbc, $q);

if ($r) { // Worked!
```

如果查询未成功运行，则必须发生了某种MySQL错误。要找出该错误是什么，请调用`mysqli_error()`函数：

```php
echo mysqli_error($dbc);
```

该函数的唯一参数是数据库连接。

脚本中最后一个（尽管是可选的）步骤是在完成操作后关闭现有的MySQL连接：

```php
mysqli_close($dbc);
```

此函数调用不是必需的，因为PHP会在脚本结束时自动关闭连接，但包含它是良好的编程习惯。

为了演示此过程，让我们创建一个注册脚本。它首次访问时显示表单![Image](graphics/circle-a.jpg)，处理表单提交，并在验证所有数据后，将注册信息插入`sitename`数据库的`users`表中。

![Image](graphics/09_figure_07_a.jpg)

![Image](graphics/circle-a.jpg)注册表单。

作为预警，此脚本已知存在一个安全漏洞（取决于所用PHP版本及其设置），将在本章后面修复。

#### 执行简单查询

**1.** 在文本编辑器或IDE中开始一个新的PHP脚本，命名为`register.php`（**[Script 9.3](#ch09.html#ch09ex03)**）：

```php
<?php # Script 9.3 - register.php

$page_title = 'Register';

include ('includes/header.html');
```

该脚本的基础——使用包含文件、让同一页面既显示又处理表单、创建粘性表单——来自[第3章](#ch03.html#ch03)。如果你对这些概念感到困惑，请参阅该章。

**2.** 创建提交条件并初始化`$errors`数组：

```php
if ($_SERVER['REQUEST_METHOD'] == 'POST') {

    $errors = array();
```

此脚本将同时显示和处理HTML表单。此第一个条件将检查脚本的请求方式，以便知道何时处理表单（同样来自[第3章](#ch03.html#ch03)）。`$errors`变量将用于存储每条错误消息（每个未正确填写的表单输入一条）。

**3.** 验证名：

```php
if (empty($_POST['first_name'])) {
    $errors[] = 'You forgot to enter your first name.';
} else {
    $fn = trim($_POST['first_name']);
}
```

正如[第3章](#ch03.html#ch03)所述，`empty()`函数提供了一种确保文本字段已填写的最小方法。如果名字段未填写，则向`$errors`数组添加一条错误消息。否则，`$fn`设置为提交的值，并去除多余空格。通过使用这个新变量——显然是`first_name`的简写——稍后编写查询在语法上会更容易。

**4.** 验证姓和电子邮件地址：

```php
if (empty($_POST['last_name'])) {
    $errors[] = 'You forgot to enter your last name.';
} else {
    $ln = trim($_POST['last_name']);
}
if (empty($_POST['email'])) {
    $errors[] = 'You forgot to enter your email address.';
} else {
    $e = trim($_POST['email']);
}
```

这些行本质上与验证名字段的行相同。在两种情况下，假设通过了最小验证，都将创建一个新变量。

**5.** 验证密码：

```php
if (!empty($_POST['pass1'])) {
    if ($_POST['pass1'] != $_POST['pass2']) {
        $errors[] = 'Your password did not match the confirmed password.';
    } else {
        $p = trim($_POST['pass1']);
    }
} else {
    $errors[] = 'You forgot to enter your password.';
}
```

**Script 9.3.** 注册脚本通过运行`INSERT`查询向数据库添加记录。

---

```php
1   <?php # Script 9.3 - register.php
2   // This script performs an INSERT query to add a record to the users table.
3
4   $page_title = 'Register';
5   include ('includes/header.html');
6
7   // Check for form submission:
8   if ($_SERVER['REQUEST_METHOD'] == 'POST') {
9
10      $errors = array(); // Initialize an error array.
11
12      // Check for a first name:
13      if (empty($_POST['first_name'])) {
14          $errors[] = 'You forgot to enter your first name.';
15      } else {
16          $fn = trim($_POST['first_name']);
17      }
18
19      // Check for a last name:
20      if (empty($_POST['last_name'])) {
21          $errors[] = 'You forgot to enter your last name.';
22      } else {
23          $ln = trim($_POST['last_name']);
24      }
25
26      // Check for an email address:
27      if (empty($_POST['email'])) {
28          $errors[] = 'You forgot to enter your email address.';
29      } else {
30          $e = trim($_POST['email']);
31      }
32
33      // Check for a password and match against the confirmed password:
34      if (!empty($_POST['pass1'])) {
35          if ($_POST['pass1'] != $_POST['pass2']) {
36              $errors[] = 'Your password did not match the confirmed password.';
37          } else {
38              $p = trim($_POST['pass1']);
39          }
40      } else {
41          $errors[] = 'You forgot to enter your password.';
42      }
43
44      if (empty($errors)) { // If everything's OK.
45
46          // Register the user in the database...
47
48          require ('../mysqli_connect.php'); // Connect to the db.
49
50          // Make the query:
51          $q = "INSERT INTO users (first_name, last_name, email, pass, registration_date) VALUES
            ('$fn', '$ln', '$e', SHA1('$p'), NOW() )";
52          $r = @mysqli_query($dbc, $q); // Run the query.
53          if ($r) { // If it ran OK.
54
55              // Print a message:
56              echo '<h1>Thank you!</h1>
```
