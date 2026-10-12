
$delete2 = unlink($url);

if ($delete1 and $delete2) {
    echo "<script>alert('Content deleted!');</script>";
}

```

让我解释这部分：

我们首先使用 `content_id` 获取内容的路径

```
$delete1 = mysqli_query($con, "DELETE FROM contents WHERE content_id = $id");
```

我们从数据库中删除内容记录

```
$delete2 = unlink($url);
```

我们从服务器（`onlinecoourse/uploads` 文件夹）删除文件。`$url` 保存文件的路径。

当 `$delete1` 和 `$delete2` 都成功时，我们通过弹窗向用户显示一条消息。

执行：`http://localhost/onlinecourse/uploadcontent.php`

让我们上传一个名为 `file3.ppt` 的新文件

![7-7-2](img/image00334.jpeg)

![7-7-3](img/image00335.jpeg)

让我们也检查一下 uploads 文件夹：

![7-7-4](img/image00336.jpeg)

现在，我们将删除名为 Content 3 的内容，点击 Content 3 所在行的 Delete 链接。

![7-7-5](img/image00337.jpeg)

![7-7-7](img/image00338.jpeg)

让我们再次检查 uploads 文件夹：

![7-7-6](img/image00339.jpeg)

希望你喜欢这种通过应用程序操作数据的方法。

至此，本章结束！下一章将把所有这些部分整合成一个连贯且可工作的应用程序。

---

### 第 8 章：使用应用程序

---

*   8.1 注册和登录
*   8.2 用户仪表板
*   8.3 修改个人资料
*   8.4 管理课程和内容
*   8.5 报名和课程访问
*   8.6 主页
*   8.7 应用程序演示

---

#### 8.1 注册和登录

---

使用任何应用程序的第一步是注册。创建账户后，你将能够登录。每当你想要访问时，都需要登录。

本节将指导你完成注册和登录流程。

我们已经完成了用户详细信息的注册。我们尚未完成登录表单。让我为你描述一下流程：

注册 -> 登录 -> 用户仪表板

完成注册后，你将被带到登录页面。当你成功登录时，你将被带到相应的用户仪表板页面。仪表板是你可以从中访问用户相关页面的地方。我们显然会有 2 种类型的仪表板：一种供讲师使用，另一种供学习者使用。

我们需要 3 个页面：

*   `register.php`
*   `login.php`
*   `dashboard.php`

我们必须从注册页面重定向到登录页面，同样从登录页面重定向到仪表板页面。在登录页面，我们将创建一个指向注册页面的链接。我们将逐个完成。在此之前，先创建另外 2 个页面 `login.php` 和 `dashboard.php`。

让我再次提醒你，要么创建文件并复制内容，要么使用“另存为”选项来创建这 2 个文件。只有创建文件后，我们才能从 `register.php` 重定向到 `login.php`。如果没有名为 `login.php` 的页面，重定向时将会遇到 404 页面未找到错误。

##### 注册与登录流程

###### 注册 - 重定向到登录

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

###### 登录流程

我们将设计一个登录表单，然后像往常一样包含 PHP 代码。登录成功后，我们将重定向到 `dashboard.php`。让我们开始吧。

####### 设计表单：login.php

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

![8-1-1](img/image00340.jpeg)

####### 认证代码：login.php

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

####### $auth 何时变为 false？

*   当用户名不存在时
*   当输入的密码与表中已存储的哈希密码值不匹配时（通过 `password_verify()` 函数检查）

登录部分到此结束。我们将对 `dashboard.php` 进行一些更改，以便在此页面显示从登录页面传来的会话变量值。

##### 会话变量：dashboard.php

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

##### 执行

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

![1604664851-registration-login](img/image00341.gif)

希望你也拥有相同的应用流程，中间没有任何 Bug。

别忘了检查 phpMyAdmin - `learners` 和 `userlogin` 表！

![8-1-2](img/image00342.jpeg)

![8-1-3](img/image00343.jpeg)

##### 如果会话正在运行，如何重定向到仪表板？

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

#### 8.2 用户仪表板

仪表板是你可以从中访问所有必要链接的地方。

在讲师的仪表板中，我们可以放置创建课程、编辑课程、上传/删除内容、查看已注册学习者进度报告、更改个人资料和注销的链接。

在学习者的仪表板中，我们可以放置已注册课程、访问课程、更改个人资料和注销的链接。

无论我们创建哪个页面，我们有两个选择：

*   在每个页面中放置所有链接
*   在单个页面（仪表板）中放置所有链接，并在每个页面中放置仪表板链接

我们将采用第二种方案。我们将创建一个仪表盘页面，将所有链接放在此处，然后在需要的页面中链接该仪表盘。原因在于，当你想要扩展项目的功能/设施时，可以轻松地将它们添加到仪表盘中以供链接。

对于每个仪表盘链接，我们都必须进行几项检查！

*   检查用户是否已登录
*   检查用户类别 - 讲师或学习者

**页面 - 检查与登出：**

*   我们将创建一个名为 `check.php` 的新 PHP 页面，其中将包含上述所有检查。对于每个链接到仪表盘的页面，我们将引入 `check.php` 文件，并根据用户类别显示相应的仪表盘。
*   我们将创建一个名为 `logout.php` 的新 PHP 页面。如果学习者试图访问讲师的页面，反之亦然，我们将强制其登出。此外，我们还需要提供一个登出链接。

***

**登出会话：**

只需创建一个名为 `logout.php` 的空白文件，并放入以下代码：

```php
<?php
session_start();
if(isset($_SESSION['usersession'])){
 unset($_SESSION['usersession']);
}
header('Location: login.php');
?>
```

在取消设置会话变量后，我们重定向到 `login.php` 页面。`header()` 是一个用于重定向的 PHP 函数。到目前为止，我们使用 JavaScript 是因为我们需要向用户显示弹出消息。由于此处没有显示消息，我们使用了 PHP 函数来实现此目的。

执行 `http://localhost/onlinecourse/logout.php` 将带你进入 `login.php` 页面。

***

**检查会话与类别：**

我们将执行以下操作：

*   检查用户是否已登录
*   使用函数查找用户类别（讲师/学习者）
*   使用函数查找用户姓名

只需创建一个名为 `check.php` 的空白文件，并放入以下代码：

```php
<?php
session_start();
require('connect.php');
//functions
function get_category($con,$id){
 $get_cat = mysqli_query($con,"SELECT * FROM userlogin WHERE user_mail = '$id'");
 if($cat = mysqli_fetch_row($get_cat)){
 return $cat[2];
 } 
}
function get_name($con,$id,$cat){
 $str = '';
 if($cat == 'instructor'){
  $str = "SELECT * FROM instructors WHERE instruct_mail = '$id'";
 }
 if($cat == 'learner'){
```
