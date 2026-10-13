

```php
5   include ('includes/header.html');

6

7   // Check for form submission:
8   if ($_SERVER['REQUEST_METHOD'] == 'POST') {

9

10      require ('../mysqli_connect.php'); // Connect to the db.

11

12      $errors = array(); // Initialize an error array.

13

14      // Check for a first name:
15      if (empty($_POST['first_name'])) {
16          $errors[] = 'You forgot to enter your first name.';
17      } else {
18          $fn = mysqli_real_escape_string($dbc, trim($_POST['first_name']));
19      }

20

21      // Check for a last name:
22      if (empty($_POST['last_name'])) {
23          $errors[] = 'You forgot to enter your last name.';
24      } else {
25          $ln = mysqli_real_escape_string($dbc, trim($_POST['last_name']));
26      }

27

28      // Check for an email address:
29      if (empty($_POST['email'])) {
30          $errors[] = 'You forgot to enter your email address.';
31      } else {
32          $e = mysqli_real_escape_string($dbc, trim($_POST['email']));
33      }

34

35      // Check for a password and match against the confirmed password:
36      if (!empty($_POST['pass1'])) {
37          if ($_POST['pass1'] != $_POST['pass2']) {
38              $errors[] = 'Your password did not match the confirmed password.';
39          } else {
40              $p = mysqli_real_escape_string($dbc, trim($_POST['pass1']));
41          }
42      } else {
43          $errors[] = 'You forgot to enter your password.';
44      }

45

46      if (empty($errors)) { // If everything's OK.

47

48          // Register the user in the database...

49

50          // Make the query:
51          $q = "INSERT INTO users (first_name, last_name, email, pass, registration_date) VALUES
              ('$fn', '$ln', '$e', SHA1('$p'), NOW() )";
52          $r = @mysqli_query ($dbc, $q); // Run the query.
53          if ($r) { // If it ran OK.

54

55              // Print a message:
56              echo '<h1>Thank you!</h1>
57              <p>You are now registered. In Chapter 12 you will actually be able to log in!</p><p>
              <br /></p>';

58

59          } else { // If it did not run OK.

60

61              // Public message:
62              echo '<h1>System Error</h1>
63              <p class="error">You could not be registered due to a system error. We apologize for
                  any inconvenience.</p>';

64

65              // Debugging message:
66              echo '<p>' . mysqli_error($dbc) . '<br /><br />Query: ' . $q . '</p>';

67

68          } // End of if ($r) IF.

69

70          mysqli_close($dbc); // Close the database connection.

71

72          // Include the footer and quit the script:
73          include ('includes/footer.html');
74          exit();

75

76      } else { // Report the errors.

77

78          echo '<h1>Error!</h1>
79          <p class="error">The following error(s) occurred:<br />';
80          foreach ($errors as $msg) { // Print each error.
81              echo " - $msg<br />\n";
82          }
83          echo '</p><p>Please try again.</p><p><br /></p>';

84

85      } // End of if (empty($errors)) IF.

86

87      mysqli_close($dbc); // Close the database connection.

88

89  } // End of the main Submit conditional.
90  ?>
91  <h1>Register</h1>
92  <form action="register.php" method="post">
93      <p>First Name: <input type="text" name="first_name" size="15" maxlength="20" value="<?php if
              (isset($_POST['first_name'])) echo $_POST['first_name']; ?>" /></p>
94      <p>Last Name: <input type="text" name="last_name" size="15" maxlength="40" value="<?php if
              (isset($_POST['last_name'])) echo $_POST['last_name']; ?>" /></p>
95      <p>Email Address: <input type="text" name="email" size="20" maxlength="60" value="<?php if
              (isset($_POST['email'])) echo $_POST['email']; ?>" /> </p>
96      <p>Password: <input type="password" name="pass1" size="10" maxlength="20" value="<?php if
              (isset($_POST['pass1'])) echo $_POST['pass1']; ?>" /></p>
97      <p>Confirm Password: <input type="password" name="pass2" size="10" maxlength="20"
              value="<?php if (isset($_POST['pass2'])) echo $_POST['pass2']; ?>" /></p>
98      <p><input type="submit" name="submit" value="Register" /></p>
99  </form>
100 <?php include ('includes/footer.html'); ?>
```

---

### 3. 修改验证流程以使用 `mysqli_real_escape_string()` 函数

将每处 **`$var = trim($_POST['var'])`** 替换为 **`$var = mysqli_real_escape_string($dbc, trim($_POST['var']))`**：

```php
$fn = mysqli_real_escape_string($dbc, trim($_POST['first_name']));
$ln = mysqli_real_escape_string($dbc, trim($_POST['last_name']));
$e = mysqli_real_escape_string($dbc, trim($_POST['email']));
$p = mysqli_real_escape_string($dbc, trim($_POST['pass1']));
```

不仅将提交的值直接赋给各个变量（**`$fn`**、**`$ln`** 等），还会先通过 **`mysqli_real_escape_string()`** 函数处理这些值。**`trim()`** 函数依然用于去除多余的空格。

---

### 4. 在主条件结构结束前增加第二次 `mysqli_close()` 调用

```php
mysqli_close($dbc);
```

为了保持一致性，既然数据库连接是在主条件结构的第一步打开的，那么也应该在该条件结构的最后一步关闭它。不过，在包含页脚并终止脚本之前（第 73 行和第 74 行），仍然需要关闭连接。

---

### 5. 将文件保存为 `register.php`，放入 Web 目录，并在浏览器中测试

![Image](graphics/circle-a.jpg)and ![Image](graphics/circle-b.jpg)

![Image](graphics/09_figure_14_a.jpg)

![Image](graphics/circle-a.jpg) 值中包含撇号的情况（如人名中的撇号）将不再导致 `INSERT` 查询出错，这要归功于 `mysqli_real_escape_string()` 函数。

![Image](graphics/09_figure_15_b.jpg)

![Image](graphics/circle-b.jpg) 现在注册流程能够处理有问题的字符，安全性更高。

---

> **Tip**
>
> **`mysqli_real_escape_string()`** 函数会根据所用语言（即排序规则）对字符串进行转义，这是该函数相对于其他替代方案的优势。

---

> **Tip**
>
> 如果出现类似 ![Image](graphics/circle-c.jpg) 的结果，说明 **`mysqli_real_escape_string()`** 函数无法访问数据库（因为没有连接，如 **`$dbc`**）。
>
> ![Image](graphics/09_figure_16_c.jpg)
>
> ![Image](graphics/circle-c.jpg) 由于 `mysqli_real_escape_string()` 需要数据库连接，在没有该连接的情况下使用它（例如在包含连接脚本之前）会导致其他错误。

---

> **Tip**
>
> 如果服务器启用了 Magic Quotes，则需要在使用 **`mysqli_real_escape_string()`** 函数之前，先移除 Magic Quotes 添加的斜杠。代码（尽管显得繁琐）如下所示：
>
> ```php
> $fn = mysqli_real_escape_string($dbc, trim(stripslashes($_POST['first_name'])));
> ```
>
> 如果不使用 **`stripslashes()`** 而 Magic Quotes 又处于启用状态，表单值将被双重转义。

---

> **Tip**
>
> 如果查看数据库中存储的值（使用 mysql 客户端、phpMyAdmin 或类似工具），你不会看到撇号和其他有问题的字符带有前导反斜杠。这是正确的。反斜杠防止有问题的字符破坏查询，但反斜杠本身不会被存储。

---

### 统计返回的记录数

