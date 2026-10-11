

# 查询的执行

在使用数据库时，首要步骤是建立连接。连接成功后，我们可以在 MySQLi 过程式函数中使用 SQL 命令。

执行查询有一种通用语法：

```
mysqli_query($database_connection, $query_string);
```

共有 2 个参数：

*   `$database_connection` 是资源变量 `$con`（即我们用于连接数据库的那个变量）
*   `$query_string` 是包含 SQL 语句的字符串

要在字符串中构建查询，我们应遵循以下规则：

*   SQL 查询在 PHP 中必须加引号
*   SQL 查询内部的字符串值必须加引号
*   数值不得加引号
*   单词 `NULL` 不得加引号

这意味着，如果我们使用双引号来括起 SQL 字符串，对于字符串值，我们将使用单引号。在实践环节编写代码时，我们将清楚地理解这一点。

在后续章节中，我们将学习操作数据——在应用程序专用表单中插入 / 查询 / 更新 / 删除数据。

---

## 7.2 插入数据 - I

有 3 种表单用于从用户处插入数据：

1.  注册（讲师 / 学习者）
2.  新课程
3.  上传内容

在注册中，我们将获取用户的输入。在新课程和上传内容中，讲师为字段提供值。这 3 个表单现在将被设计并用于学习插入数据语句。

首先，让我们从注册表单开始。我们将使用单个注册表单，并提供适当的字段来确定用户是讲师还是学习者。

### 实践

1.  如果你在文本编辑器中打开了 `index.php`，选择**另存为**选项，并将其另存为 `onlinecourse` 文件夹内的 `register.php`。
2.  保存后，你的 `onlinecourse` 文件夹应包含 2 个文件：`index.php` 和 `register.php`。

**替代方案：**

如果你对上述过程感到不适应，则：

*   在 `onlinecourse` 文件夹内创建一个名为 `register.php` 的新文件。
*   将 `index.php` 的内容复制到 `register.php` 并保存。

### 表单设计：register.php

1.  将 title 标签的内容更改为 **User Registration**（用户注册）。
2.  删除 `main` 标签之间的内容。
3.  替换为以下代码：

```html
<main>
  <section>
    <h3> User Registration </h3>
    <p>
      <form method="post" name="frmregister">
        <p><select name="txtusercategory">
            <option value="">Who are you?</option>
            <option value="learner">Learner</option>
            <option value="instructor">Instructor</option>
          </select></p>
        <p><input type="email" name="txtmail" size="40" placeholder="Enter your Email Address" required></p>
        <p><input type="password" name="txtpwd" size="40" placeholder="Enter your Password 8-15 characters" required></p>
        <p><input type="text" name="txtname" size="40" placeholder="Enter your Full Name" required></p>
        <p><textarea name="txtdetails" cols="40" placeholder="Enter your details" required></textarea></p>
        <p><input type="submit" name="register" value="Register" class="frmbtn"></p>
      </form>
    </p>
  </section>
</main>
```

4.  执行 `http://localhost/onlinecourse/register.php`

![7-2-1](Images/image00312.jpeg)

### 插入数据：register.php

在文件开头，HTML 声明行之前，我们将包含插入代码：

```php
<?php
require('connect.php');

if (isset($_POST['register'])) {
  $category = $_POST['txtusercategory'];
  $usermail = $_POST['txtmail'];
  $userpwd = $_POST['txtpwd'];
  $name = $_POST['txtname'];
  $details = $_POST['txtdetails'];

  if ((strlen($userpwd) > 7) && (strlen($userpwd) < 16)) {
    $userpwd = password_hash($userpwd, PASSWORD_DEFAULT);
    $insert1 = "INSERT INTO userlogin VALUES ('$usermail','$userpwd','$category')";
    if ($category == 'learner') {
      $insert2 = "INSERT INTO learners VALUES ('$usermail','$name','$details')";
    }
    if ($category == 'instructor') {
      $insert2 = "INSERT INTO instructors VALUES ('$usermail','$name','$details')";
    }
    $check_insert1 = mysqli_query($con, $insert1);
    $check_insert2 = mysqli_query($con, $insert2);
    if ($check_insert1 && $check_insert2) {
      echo "<script>alert('Registration successful!');</script>";
    } else {
      echo "<script>alert('Sorry! Try again!');</script>";
    }
  } else {
    echo "<script>alert('Password should be between 8-15 characters');</script>";
  }
}
?>
```

让我逐行解释：

```php
require('connect.php');
```

我们在 `connect.php` 文件中连接数据库。因此我们在此页面包含该连接文件。

```php
if (isset($_POST['register'])) { }
```

完整的 PHP 代码仅在按下注册按钮时才会执行。

```php
$category = $_POST['txtusercategory'];
$usermail = $_POST['txtmail'];
$userpwd = $_POST['txtpwd'];
$name = $_POST['txtname'];
$details = $_POST['txtdetails'];
```

我们将表单提交的值复制到变量中。

```php
if ((strlen($userpwd) > 7) && (strlen($userpwd) < 16)) {
}
else {
  echo "<script>alert('Password should be between 8-15 characters');</script>";
}
```

这里，我们通过施加两个条件来检查密码是否在 8 到 15 个字符之间：检查长度是否大于 7 且小于 16。如果长度不在 8 到 15 之间，它会打印一条消息并跳过注册。如果长度在 8-15 之间，则进入 `if` 代码块继续执行。

```php
$userpwd = password_hash($userpwd, PASSWORD_DEFAULT);
```

在数据库中明文存储密码是大忌。因此，我们使用 `password_hash()` 函数创建哈希值。

```php
$insert1 = "INSERT INTO userlogin VALUES ('$usermail','$userpwd','$category')";
if ($category == 'learner') {
  $insert2 = "INSERT INTO learners VALUES ('$usermail','$name','$details')";
}
if ($category == 'instructor') {
  $insert2 = "INSERT INTO instructors VALUES ('$usermail','$name','$details')";
}
```

注册期间，我们必须向 2 个表插入数据。一个表是 `instructor` 或 `learner`（根据上下文从 "login" 修正而来），另一个表是 `userlogin`，它存储登录详情和用户类别数据。

`$insert1` 语句包含 `userlogin` 表的查询字符串。

根据类别，将使用 `$insert2` 语句。希望你能看到双引号如何用于查询字符串，单引号如何用于字符串值。

```php
$check_insert1 = mysqli_query($con, $insert1);
$check_insert2 = mysqli_query($con, $insert2);
if ($check_insert1 && $check_insert2) {
  echo "<script>alert('Registration successful!');</script>";
}
else {
  echo "<script>alert('Sorry! Try again!');</script>";
}
```

这里，我们对 2 条插入语句执行 `mysqli_query()` 函数。希望你还记得上一节中执行查询的语法。

`$check_insert1` 和 `$check_insert2` 将分别保存 `true`（如果查询执行成功）或 `false`（如果查询执行失败）。如果两条语句都执行成功且值均为 `true`，我们将打印注册成功的消息。如果任一失败，我们将提示用户重试。

```html
<script>alert();</script>
```

`script` 标签包含在 `echo` 语句中。这意味着 `script` 标签内的内容是 JavaScript 代码。JS 中的 `alert()` 函数将显示一个带有消息的弹窗。我们尝试通过弹窗而不是在页面上打印消息来告知用户发生了什么操作。

还有一件事！这不是执行插入过程的唯一方法。不变的是 `mysqli_query()` 函数。实现方式可以有很多种差异，例如：

*   我们可以先向 `instructor` / `learner` 表插入数据；如果成功，再向 `userlogin` 表插入数据。
*   如果一个表的数据插入成功而另一个失败，我们可以发出删除命令来撤销已插入的数据。
*   不仅密码，所有其他字段在插入数据前也可以进行验证。

所有这些因素取决于开发应用程序的人，而条件取决于开发什么样的应用程序。

