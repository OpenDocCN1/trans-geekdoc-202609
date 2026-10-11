

# 表单设计：profile.php

我们将从表单设计开始！像往常一样，使用“另存为”选项或创建一个新文件并粘贴内容。文件名为 `profile.php`。

在文件开头，不要忘记包含下面这行代码：

```php
<?php
include ('check.php');
?>
```

这次在设计中，我们将包含一些 PHP 代码，目的是显示来自数据库的详细信息。

按如下方式替换 `<main>` 标签的内容：

```php
<main>
<section>
<?php 
echo "<h3>Hello ".$name."</h3>";
echo "<p><a href='dashboard.php'>Dashboard</a>&emsp;<a href='logout.php'>Logout</a></p>";
$str = '';
$details = '';
if($category == 'instructor'){
 $str = "SELECT * FROM instructors WHERE instruct_mail = '$usersession'";
}
if($category == 'learner'){
 $str = "SELECT * FROM learners WHERE learn_mail = '$usersession'";
}
$fetch_details = mysqli_query($con,$str);
if($fetch = mysqli_fetch_row($fetch_details)){
  $details = $fetch[2];
}
?>
<form method="post" name="frmpwd">
<p><input type="password" name="txtoldpwd" size="40" placeholder="Enter your old Password" required></p>
<p><input type="password" name="txtnewpwd" size="40" placeholder="Enter your new Password 8-15 characters" required></p>
<p><input type="submit" name="changepwd" value="Change Password" class="frmbtn"></p>
</form>
<p><hr></p>
<form method="post" name="frmprofile">
<p><input type="text" name="txtname" size="40" value="<?php echo $name; ?>" required></p>
<p><textarea name="txtdetails" cols="40" required><?php echo $details; ?></textarea></p>
<p><input type="submit" name="changeprofile" value="Update Profile" class="frmbtn"></p>
</form>
</section>
</main>
```

我们根据用户类别选择表。根据选择，从相应的表中检索详细信息。由于 `instructors` 和 `learners` 表中具有相同的字段集，我们使用 `$details[2]` 元素来获取详细信息。

您可以执行个人资料页面并查看设计效果：

![8-3-1](Images/image00346.jpeg)

根据设计代码，我们执行两次更新：一次用于更改密码，另一次用于更改个人资料详情。我们必须为这两次提交分别包含两个 `if(isset())` 代码块。

## 更新个人资料：profile.php

### 1. 将此代码片段添加到 PHP 文件开头（用于更改密码）

```php
<?php
include ('check.php');
if(isset($_POST['changepwd'])){
  $oldpassword = $_POST['txtoldpwd'];
  $newpassword = $_POST['txtnewpwd'];
  $get_password = mysqli_query($con,"SELECT * FROM userlogin WHERE user_mail = '$usersession'");
  $pwd = mysqli_fetch_array($get_password);
  //verifying if old password = new password
  if(password_verify($oldpassword,$pwd['user_pwd'])){ 
    if((strlen($newpassword) > 7) and (strlen($newpassword) < 21)){
      $hashed = password_hash($newpassword,PASSWORD_DEFAULT);
      $updatepwd = "UPDATE userlogin SET user_pwd = '$hashed' WHERE user_mail = '$usersession'";     
      if(mysqli_query($con,$updatepwd)){
         echo "<script>alert('Password changed! Login with new password!');
         window.location.replace('logout.php');</script>";
      }
    }
    else{
      echo "<script>alert('Password length must be between 8-15 characters!');</script>";
    } 
  }
  else{
    echo "<script>alert('Old password is wrong!');</script>";
  }
}
?>
```

具体工作从使用 `password_verify()` 函数检查旧密码开始。

*   我们从表中检索了哈希密码，并通过 `$pwd['user_pwd']` 访问它。
*   我们使用 `password_verify()` 来比较 `$pwd['user_pwd']` 和表单中输入的 `$oldpassword`。
*   如果密码不匹配，我们打印“Old password is wrong.”
*   如果密码匹配，我们再对新密码的长度进行一次检查。
    *   如果新密码长度在 8 到 15 个字符之间，则更新新密码的哈希值并向用户显示消息。
    *   如果长度不匹配，我们打印一条消息，要求用户提供长度在 8 到 15 个字符之间的密码。

### 2. 将以下个人资料更改提交代码追加到前面的 PHP 片段之后

```php
if(isset($_POST['changeprofile'])){
 $newname = $_POST['txtname'];
 $newdetails = $_POST['txtdetails'];
 if($category == 'instructor'){
   $updateprofile1 = "UPDATE instructors SET instruct_name = '$newname' WHERE instruct_mail = '$usersession'";
   $updateprofile2 = "UPDATE instructors SET instruct_details = '$newdetails' WHERE instruct_mail = '$usersession'";
 }
 if($category == 'learner'){
   $updateprofile1 = "UPDATE learners SET learn_name = '$newname' WHERE learn_mail = '$usersession'";
   $updateprofile2 = "UPDATE learners SET learn_details = '$newdetails' WHERE learn_mail = '$usersession'";
 }
 if(mysqli_query($con,$updateprofile1) and mysqli_query($con,$updateprofile2)){
   echo "<script>alert('Profile Updated!');</script>";
 }
}
```

这一次，无论在何处进行更改，我们都更新了这两个字段。这只是为了向您展示两种方式都是正确的。这完全取决于开发人员。

希望更新过程已清楚。

执行 [http://localhost/onlinecourse](#part0052.xhtml)

以讲师/学习者身份登录并更新个人资料。

*这是一个 GIF 图像。请确保您的设备支持 GIF。*

![1604664382-change-profile](Images/image00347.gif)

在下一节中，我们将着手讲师的仪表板。

---

### 8.4 管理课程和内容

---

现在，我们进入讲师类别的核心部分！

讲师应该能够：

*   创建新课程
*   查看现有课程
*   编辑课程详情
*   向课程上传内容
*   查看已注册学习者及其进度

我们有新建课程、编辑课程和上传内容的页面。对于我们在仪表板部分设计的这个页面，文件名是 `clist.php`。

可以对 `dashboard.php` 页面使用“另存为”，或者创建一个新文件 `clist.php` 并从 `dashboard.php` 复制内容。

**此页面包含什么内容？**

*   一个创建新课程的链接
*   已创建的课程将以表格形式显示
*   编辑课程的链接
*   上传内容的链接
*   查看学习者进度的链接

我们将为讲师准备好所有页面。关于进度页面，我们将设计并使其就绪。一旦完成下一节的内容，我们将从那里执行此进度页面的工作。

我们开始吧？

## 显示现有课程

我们将显示由讲师创建的课程：讲师 1。

希望页面 `clist.php` 已经在页面开头包含了 `check.php` 文件。如果没有，请按如下方式包含它，并添加一行：

```php
<?php include('check.php');
if($category == 'learner'){
  header('logout.php');
}
?>
```

我们在这里还将添加一个条件：万一学习者已登录并以某种方式检索到此页面，我们可以自动将他们重定向到注销。

要测试这一点，以学习者身份登录并在 URL 中访问 `clist.php`；您将被注销并转到 `login.php`。

## clist.php

