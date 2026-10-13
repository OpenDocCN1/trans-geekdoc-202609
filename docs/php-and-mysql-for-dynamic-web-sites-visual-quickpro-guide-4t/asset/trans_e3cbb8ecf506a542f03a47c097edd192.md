
# 用户注册处理脚本分析

## 代码实现

```php
57          <p>You are now registered. In Chapter 12 you will actually be able to log in!</p><p>  
              <br /></p>';  
58  
59          } else { // If it did not run OK.  
60  
61             // Public message:  
62             echo '<h1>System Error</h1>  
63             <p class="error">You could not be registered due to a system error. We apologize for  
                any inconvenience.</p>';  
64  
65             // Debugging message:  
66             echo '<p>' . mysqli_error($dbc) . '<br /><br />Query: ' . $q . '</p>';  
67  
68          } // End of if ($r) IF.  
69  
70          mysqli_close($dbc); // Close the database connection.  
71  
72          // Include the footer and quit the script:  
73          include ('includes/footer.html');  
74          exit( );  
75  
76      } else { // Report the errors.  
77  
78          echo '<h1>Error!</h1>  
79          <p class="error">The following error(s) occurred:<br />';  
80          foreach ($errors as $msg) { // Print each error.  
81              echo " - $msg<br />\n";  
82          }  
          echo '</p><p>Please try again.</p><p><br /></p>';  
84  
85      } // End of if (empty($errors)) IF.  
86  
87  } // End of the main Submit conditional.  
88  ?>  
89  <h1>Register</h1>  
90  <form action="register.php" method="post">  
91      <p>First Name: <input type="text" name="first_name" size="15" maxlength="20" value="<?php if  
             (isset($_POST['first_name'])) echo $_POST['first_name']; ?>" /></p>  
92      <p>Last Name: <input type="text" name="last_name" size="15" maxlength="40" value="<?php if  
             (isset($_POST['last_name'])) echo $_POST['last_name']; ?>" /></p>  
93      <p>Email Address: <input type="text" name="email" size="20" maxlength="60" value="<?php if  
             (isset($_POST['email'])) echo $_POST['email']; ?>" /> </p>  
94      <p>Password: <input type="password" name="pass1" size="10" maxlength="20" value="<?php if  
             (isset($_POST['pass1'])) echo $_POST['pass1']; ?>" /></p>  
95      <p>Confirm Password: <input type="password" name="pass2" size="10" maxlength="20"  
             value="<?php if (isset($_POST['pass2'])) echo $_POST['pass2']; ?>" /></p>  
96      <p><input type="submit" name="submit" value="Register" /></p>  
97  </form>  
98  <?php include ('includes/footer.html'); ?>
```

## 密码验证逻辑

为了验证密码，脚本需要检查 `pass1` 输入是否有值，然后确认 `pass1` 的值与 `pass2` 的值匹配（即密码和确认密码相同）。

## 步骤详解

### 6. 检查是否可以注册用户

```php
if (empty($errors)) {
```

如果提交的数据通过了所有条件，`$errors` 数组将没有值（为空），因此此条件为真，可以安全地将记录添加到数据库。如果 `$errors` 数组不为空，则应打印相应的错误消息（见步骤 11），并给用户另一次注册机会。

### 7. 包含数据库连接

```php
require ('../mysqli_connect.php');
```

这行代码将 `mysqli_connect.php` 文件的内容插入到此脚本中，从而创建与 MySQL 的连接并选择数据库。您可能需要根据服务器上的文件位置更改文件引用（按原样编写，此行假设 `mysqli_connect.php` 位于当前文件夹的父文件夹中）。

### 8. 将用户添加到数据库

```php
$q = "INSERT INTO users (first_name, last_name, email, pass, registration_date) VALUES ('$fn', '$ln', '$e', SHA1('$p'), NOW() );  
$r = @mysqli_query ($dbc, $q);
```

查询本身类似于[第 5 章](#ch05.html#ch05)中演示的查询。`SHA1()` 函数用于加密密码，`NOW()` 用于将注册日期设置为当前时刻。

将查询赋值给变量后，通过 `mysqli_query()` 函数运行，该函数将 SQL 命令发送到 MySQL 数据库。与 `mysqli_connect.php` 脚本一样，`mysqli_query()` 调用前面有 `@` 以抑制任何难看的错误。如果出现问题，将在下一步中更直接地处理错误。

### 9. 报告注册成功与否

```php
if ($r) {  
    echo '<h1>Thank you!</h1>  
    <p>You are now registered. In Chapter 12 you will actually be able to log in!</p><p><br /></p>';  
} else {  
    echo '<h1>System Error</h1>  
    <p class="error">You could not be registered due to a system error. We apologize for any inconvenience.</p>';  
    echo '<p>' . mysqli_error($dbc) . '<br /><br />Query: ' . $q . '</p>';  
} // End of if ($r) IF.
```

`$r` 变量被赋予 `mysqli_query()` 返回的值，可用于条件判断以测试查询是否成功执行。

如果 `$r` 为 TRUE，则显示 *Thank you!* 消息。如果 `$r` 为 FALSE，则打印错误消息。出于调试目的，错误消息将包括 MySQL 抛出的错误（得益于 `mysqli_error()` 函数）以及正在运行的查询。此信息对于调试问题至关重要。但是，您不希望在实时站点上显示此类信息。

> **图示说明**
> - 如果用户能够在数据库中注册，将显示此消息。
> - 由查询引起的任何 MySQL 错误都将被打印，正在运行的查询也将被打印。

### 10. 关闭数据库连接并完成 HTML 模板

```php
mysqli_close($dbc);  
include ('includes/footer.html');  
exit( );
```

关闭连接不是必需的，但这是一个好的策略。然后包含页脚并终止脚本（得益于 `exit()` 函数）。如果没有这两行，注册表单将再次显示（成功注册后这是不必要的）。

### 11. 打印任何错误消息并关闭提交条件

```php
} else { // Report the errors.  
    echo '<h1>Error!</h1>  
    <p class="error">The following error(s) occurred:<br />';  
    foreach ($errors as $msg) { // Print each error.  
        echo " - $msg<br />\n";  
    }  
    echo '</p><p>Please try again.</p><p><br /></p>';  
} // End of if (empty($errors)) IF.  
} // End of the main Submit conditional.
```

如果存在任何错误，将调用 `else` 子句。在这种情况下，使用 `foreach` 循环显示所有错误。

> **图示说明**
> 每个表单验证错误都会报告给用户，以便他们可以尝试再次注册。

最后的右大括号关闭主提交条件。主条件是一个简单的 `if`，而不是 `if-else`，以便使表单具有粘性（同样，请参阅[第 3 章](#ch03.html#ch03)）。

### 12. 关闭 PHP 部分并开始 HTML 表单

```php
?>  
<h1>Register</h1>  
<form action="register.php" method="post">  
    <p>First Name: <input type="text" name="first_name" size="15" maxlength="20" value="<?php if (isset($_POST['first_name'])) echo $_POST['first_name']; ?>" /></p>  
    <p>Last Name: <input type="text" name="last_name" size="15" maxlength="40" value="<?php if (isset($_POST['last_name'])) echo $_POST['last_name'];?>" /></p>
```

表单非常简单，针对 `users` 表中的每个字段（`user_id` 和 `registration_date` 列除外，它们将自动填充）都有一个文本输入框。每个输入都使用如下代码使其具有粘性：

```php
value="<?php if (isset($_POST['var'])) echo $_POST['var']; ?>"
```
