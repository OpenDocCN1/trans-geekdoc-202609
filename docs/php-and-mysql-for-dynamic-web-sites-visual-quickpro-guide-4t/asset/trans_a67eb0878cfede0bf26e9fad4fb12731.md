

![Image](graphics/circle-b.jpg)对对象使用 `print_r()`，或许将其包裹在预格式化标签中以使其输出更易读，可显示该对象的许多属性名称和值。

***

提示

由于如果未建立连接，`$mysqli` 对象会被销毁，因此任何需要它的脚本都可以通过以下方式测试连接是否成功：

```
if (isset($mysqli)) { // 执行相应操作。
```

为简洁起见，后续脚本中省略了此测试，但请知晓这是可行的。

***

提示

MySQLi 构造函数还接受两个参数：要使用的端口和套接字。运行 MAMP 或 XAMPP 时（参见[附录 A](#app01.html#app01)“[安装](#app01.html#app01)”，可从 peachpit.com 下载），可能需要提供端口号。

***

提示

`MySQLi::character_set_name()` 方法返回当前字符集。`MySQLi::get_charset()` 方法返回字符集、排序规则等信息。

***

提示

您可以通过 `select_db()` 方法更改当前连接使用的数据库：

```
$mysqli->select_db(dbname);
```

***

#### 执行简单查询

成功建立与 MySQL 服务器的连接后，即可开始使用 `MySQLi` 对象查询数据库。为此，调用名为 `query()` 的方法：

```
$mysqli->query(query);
```

其唯一参数是要执行的 SQL 命令，我通常会预先将其赋值给一个单独的变量：

```
$q = 'SELECT * FROM tablename';

$mysqli->query($q);
```

您可以将方法调用用作条件，以测试查询是否无错误执行：

```
if ($mysqli->query($q)) { // 成功！
```

或者，您可以检查 `error` 属性 ![Image](graphics/circle-c.jpg)：

```
if ($mysqli->error) { // 失败！

    echo $mysqli->error;

}
```

![Image](graphics/16_figure_03_c.jpg)

![Image](graphics/circle-c.jpg)查询出现问题会导致 MySQL 错误。

如果刚执行的查询是 `INSERT`，您可以通过 `insert_id` 属性检索自动生成的主键值：

```
$id = $mysqli->insert_id;
```

如果刚执行的查询是 `UPDATE`、`INSERT` 或 `DELETE`，您可以从 `affected_rows` 属性获取受影响的行数——即有多少行被更新、插入或删除：

```
echo "$mysqli->affected_rows rows were affected by the query.";
```

在执行任何查询之前，最后要了解的是如何*净化*查询中使用的数据。为此，请预先对字符串变量应用 `real_escape_string()`：

```
$var = $mysqli->real_escape_string($var);
```

这等同于调用 `mysqli_real_escape_string()`，可防止撇号和其他有问题的字符破坏 SQL 命令的语法。

利用所有这些信息，下一组步骤将使用 OOP 重写来自[第 9 章](#ch09.html#ch09)的 `register.php`（[脚本 9.5](#ch09.html#ch09ex05)）。

#### 执行简单查询

**1.** 在文本编辑器或 IDE 中打开 `register.php`（[脚本 9.5](#ch09.html#ch09ex05)）。

**2.** 将 MySQL 连接脚本的引入更改为（**[脚本 16.2](#ch16.html#ch16ex02)**）：

```
require ('../mysqli_oop_connect.php');
```

假设 `mysqli_oop_connect.php` 位于上一级目录中，此代码将正常工作。如果您的目录结构不同，请相应地更改对该文件的引用。

**3.** 将每处 `mysqli_real_escape_string()` 的用法更改为：

```
$mysqli->real_escape_string():
$fn = $mysqli->real_escape_string (trim($_POST['first_name']));
$ln = $mysqli->real_escape_string (trim($_POST['last_name']));
$e = $mysqli->real_escape_string (trim($_POST['email']));
$p = $mysqli->real_escape_string (trim($_POST['pass1']));
```

四个数据项——自然全是字符串——均经过转义以便在查询中获得额外保护。由于脚本现在采用面向对象方式使用 MySQL Improved 扩展，这四行代码应作相应更改。

**4.** 更新查询的执行方式（原脚本第 52 行）：

```
$mysqli->query($q);
```

要使用 OOP 在数据库上执行查询，请调用对象的 `query()` 方法，并将要运行的查询提供给它。

**脚本 16.2.** 此注册脚本的更新版本通过 OOP 使用 MySQL Improved 扩展。

***

```
1   <?php # 脚本 16.2 - register.php

2   // 此脚本执行 INSERT 查询
       以向 users 表添加一条记录。
3   // 这是来自第 9 章脚本的 OOP 版本。

4

5   $page_title = 'Register';
6   include ('includes/header.html');

7   // 检查表单提交：
8   if ($_SERVER['REQUEST_METHOD'] == 'POST')
{

9

10      require ('../mysqli_oop_connect.php');
      // 连接到数据库。

11

12      $errors = array(); // 初始化错误
         数组。

13

14      // 检查名：
15      if (empty($_POST['first_name'])) {
16          $errors[] = 'You forgot to enter
            your first name.';
17      } else {
18          $fn = $mysqli->real_escape_
            string(trim($_POST['first_name']));
19      }

20

21      // 检查姓：
22      if (empty($_POST['last_name'])) {
23          $errors[] = 'You forgot to enter
            your last name.';
24      } else {
25          $ln = $mysqli->real_escape_
            string(trim($_POST['last_name']));
26      }

27

28      // 检查电子邮件地址：
29      if (empty($_POST['email'])) {
30          $errors[] = 'You forgot to enter
            your email address.';
31      } else {
32          $e = $mysqli->real_escape_
            string(trim($_POST['email']));
33      }

34

35      // 检查密码并与确认密码匹配：
36      if (!empty($_POST['pass1'])) {
37      if ($_POST['pass1'] != $_POST
         ['pass2']) {
38          $errors[] = 'Your password
            did not match the confirmed
            password.';
39      } else {
40          $p = $mysqli->real_escape_
            string(trim($_POST['pass1']));
41      }
42  } else {
43      $errors[] = 'You forgot to enter
         your password.';
44  }

45

46  if (empty($errors)) { // 如果
         一切正常。

47

48      // 在数据库中注册用户...

49

50      // 创建查询：
51      $q = "INSERT INTO users
         (first_name, last_name, email,
         pass, registration_date) VALUES
         ('$fn', '$ln', '$e', SHA1('$p'),
         NOW() )";

52

53      // 执行查询：
54      $mysqli->query($q);

55

56      if ($mysqli->affected_rows ==
         1) { // 如果运行正常。

57

58          // 打印消息：
59          echo '<h1>Thank you!</h1>
         <p>You are now registered. In
         Chapter 12 you will actually be
         able to log in!</p><p><br /></p>';

60

61      } else { // 如果运行不正常。

62

63          // 公共消息：
64          echo '<h1>System Error</h1>
         <p class="error">You could not
            be registered due to a system
            error. We apologize for any
            inconvenience.</p>';

65

66          // 调试消息：
67          echo '<p>' . $mysqli->error .
            '<br /><br />Query: ' . $q .
            '</p>';

68

69          } // End of if ($r) IF.

70

71          $mysqli->close(); // 关闭数据库
            连接。
72          unset($mysqli);

73

74          // 引入页脚并退出脚本：
75          include ('includes/footer.html');
76          exit();

77

78      } else { // 报告错误。

79

80          echo '<h1>Error!</h1>
         <p class="error">The following
```

