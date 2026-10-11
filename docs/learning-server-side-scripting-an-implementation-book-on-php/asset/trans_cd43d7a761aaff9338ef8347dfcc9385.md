

# 注册与登录流程

## 注册 - 重定向到登录

希望你已准备好文件。我们现在将包含代码。完成登录流程后我们将进行测试。

在顶部的 PHP 代码段中有一个 `if` 代码块：

```php
if($check_insert1 and $check_insert2){
  echo "<script>alert('Registration successful!');</script>";
}
```

我们将在此 `echo` 语句中通过 JavaScript 发出重定向命令。为什么要这样做？因为我们通过此 `alert()` 获取成功消息，所以必须在此消息之后触发重定向。如果我们在 PHP 中编写重定向代码，这条警报消息将会被错过。为了稳妥起见，我们将使用 JS 编写。

将代码更改为：

```php
if($check_insert1 and $check_insert2){
  echo "<script>alert('Registration successful!');
  window.location.replace('login.php');</script>";
}
```

这段代码表示当前页面必须替换为参数中的 URL。

## 登录流程

我们将设计一个登录表单，然后像往常一样包含 PHP 代码。登录成功后，我们将重定向到 `dashboard.php`。让我们开始吧。

### 设计表单：login.php

将 `title` 标签的内容更改为 "User Login"，并用以下代码替换 `main` 标签元素：

```html
<main>
  <section>
    <h3> User Login </h3>
    <p>
      <form method="post" name="frmlogin">
        <p><input type="email" name="txtuser" size="40" placeholder="Enter your email"></p>
        <p><input type="password" name="txtpwd" size="40" placeholder="Enter your password"></p>
        <p><input type="submit" name="login" value="Login" class="frmbtn"></p>
      </form>
    </p>
  </section>
</main>
```

不要输入任何详细信息！仅执行以查看页面： <http://localhost/onlinecourse/login.php>

![8-1-1](Images/image00340.jpeg)

### 认证代码：login.php

我们将像往常一样在页面顶部包含认证部分。

```php
<?php
session_start();
require('connect.php');
$auth = true;
$hashedpwd = '';
if(isset($_POST['login'])){
  $username = $_POST['txtmail'];
  $password = $_POST['txtpwd'];
  $select_user = mysqli_query($con,"SELECT * FROM userlogin WHERE user_mail='$username'");
  if($user = mysqli_fetch_row($select_user)){
    $hashedpwd = $user[1];
  }
  else{
    $auth = false;
  }
  if(!password_verify($password,$hashedpwd)){
    $auth = false;
  }
  if($auth){
    $_SESSION['usersession'] = $username;
    echo "<script>window.location.replace('dashboard.php')</script>";
  }
  else{
    echo "<script>alert('Invalid username or password!')</script>";
  } 
}
?>
```

我们来看看解释：

```php
session_start();
```

我们将为此认证使用 `session_start()`，因为我们必须将用户名存储为会话变量。这意味着，直到用户注销/关闭会话，会话变量将保持活跃。

```php
$auth = true;
$hashedpwd = '';
```

我们初始化两个变量。如果用户名和密码与数据库记录匹配，`$auth` 将保持 `true` 直到代码结束。如果 `$auth` 在某处变为 `false`，则意味着用户名或密码不匹配，即认证失败。`$hashedpwd` 稍后将保存用户名匹配时的密码字段。

```php
$select_user = mysqli_query($con,"SELECT * FROM userlogin WHERE user_mail='$username'");
if($user = mysqli_fetch_row($select_user)){
  $hashedpwd = $user[1];
}
else{
  $auth = false;
}
```

我们搜索 `userlogin` 表中与用户名匹配的记录。

*   如果存在该用户名的用户，则将密码字段赋值给 `$hashedpwd` 变量。
*   如果不存在该用户名的用户，则将 `$auth` 变量设置为 `false`。

```php
if(!password_verify($password,$hashedpwd)){
  $auth = false;
}
```

我们将表单中输入的密码与表中存储的哈希密码进行比较。我们使用专门为此目的设计的 `password_verify()` 函数。如果密码不匹配，`$auth` 将变为 `false`。

```php
if($auth){
  $_SESSION['usersession'] = $username;
  echo "<script>window.location.replace('dashboard.php')</script>";
}
else{
  echo "<script>alert('Invalid username or password!')</script>";
}
```

如果 `$auth` 在所有这些检查下都保持 `true`，我们将 `$username` 的值赋给会话变量 `$_SESSION['usersession']`。在此之后，我们重定向到仪表板页面。如果 `$auth` 在任何检查中变为 `false`，我们将打印无效登录消息。

### $auth 何时变为 false？

*   当用户名不存在时
*   当输入的密码与表中已存储的哈希密码值不匹配时（通过 `password_verify()` 函数检查）

登录部分到此结束。我们将对 `dashboard.php` 进行一些更改，以便在此页面显示从登录页面传来的会话变量值。

## 会话变量：dashboard.php

将 `title` 标签的内容更改为 "User Dashboard"。

将以下代码行放在页面顶部：

```php
<?php
session_start();
require('connect.php');
?>
```

建议将 `session_start()` 放在页面开头。

像往常一样，用以下代码替换 `main` 标签内容：

```php
<main>
  <section>
    <h3> User Dashboard </h3>
    <p>
      <?php 
      $usersession = '';
      if(isset($_SESSION['usersession'])){
        $usersession = $_SESSION['usersession'];
      }
      echo "<p>Hello ".$usersession."</p>";
      ?>
    </p>
  </section>
</main>
```

我们只是将会话变量的值赋给变量 `$usersession` 并将其打印出来。

## 执行

现在我们来检查一下完整流程吧？

这次，我们将：

*   注册一名学习者
*   登录该学习者
*   在仪表板页面查看学习者的用户名

我们必须将其作为一个应用程序来执行。所以我们将从主页跳转到注册页面。

*   访问 <http://localhost/onlinecourse/>
*   点击 Login
*   点击 Register here 链接。

让我以学习者身份注册/报名：

要输入的详细信息：

*   Who are you? Learner（你是谁？ 学习者）
*   Email - learner1@onlinecourse.com
*   Password - password
*   Full Name - Learner 1
*   Details - First learner of this platform

让我展示这个过程。

*这是一个 GIF 图片。请确保您的设备支持 GIF。*

![1604664851-registration-login](Images/image00341.gif)

希望你也拥有相同的应用流程，中间没有任何 Bug。

别忘了检查 phpMyAdmin - `learners` 和 `userlogin` 表！

![8-1-2](Images/image00342.jpeg)

![8-1-3](Images/image00343.jpeg)

## 如果会话正在运行，如何重定向到仪表板？

我们还有一项任务要做。万一你不知不觉关闭了浏览器标签页，但你的会话仍未过期，我们必须将登录页面重定向到仪表板，而无需再次询问登录详细信息。

因此，我们将在 **login.php** 文件开头添加此代码：

```php
session_start();
if(isset($_SESSION['usersession'])){
  echo "<script>window.location.replace('dashboard.php')</script>";
}
require('connect.php');
```

*   在浏览器的 2 个标签页中执行 <http://localhost/onlinecourse/>。
*   尝试在浏览器的一个标签页中登录。
*   在浏览器的另一个标签页中点击 Login。你将被重定向到 `dashboard.php`。

我们还必须对仪表板页面进行更多更改。我们将在下一节中进行。

# 8.2 用户仪表板

仪表板是你可以从中访问所有必要链接的地方。

在讲师的仪表板中，我们可以放置创建课程、编辑课程、上传/删除内容、查看已注册学习者进度报告、更改个人资料和注销的链接。

在学习者的仪表板中，我们可以放置已注册课程、访问课程、更改个人资料和注销的链接。

无论我们创建哪个页面，我们有两个选择：

*   在每个页面中放置所有链接
*   在单个页面（仪表板）中放置所有链接，并在每个页面中放置仪表板链接

