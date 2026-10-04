

# 第 11 章

3. 接下来，创建一个告知用户已登录的页面；然后你可以显示通往用户个人区域（我们稍后会创建）的链接，允许其更新个人信息或完全删除你的账户。使用以下代码将此文件命名为 logged_user.php：

```php
<html>
<head>
  <title>初级 PHP, Apache, MySQL Web 开发</title>
</head>
<body>
<h1>欢迎来到首页</h1><br>
感谢您登录我们的系统。<br>
您现在可以<a href="user_personal.php">点击此处</a>进入您的个人信息区域，
并根据您的需要更新或删除您的信息。
</body>
</html>
```

4. 创建一个名为 `conn.inc.php` 的页面，将其包含在你的其他页面中，用于存储 MySQL 连接信息：

```php
<?php
$conn = mysql_connect("localhost", "wrox_user", "wrox_pass") or
die(mysql_error());
$db = mysql_select_db("registration") or die(mysql_error());
?>
```

5. 创建注册页面，确保包含所有可选字段，并确保注册用户使用的用户名不与现有用户名重复。将其命名为 `register.php`（由于代码较多，我们稍后在整合整个系统时会进行解释）。

如果用户没有填写某些必填字段，或使用了已注册的用户名，我们将通知他们并保留他们之前在相应字段中输入的内容，以免他们重新输入一遍。

```php
<?php
session_start();
include "conn.inc.php";
?>
<html>
<head>
  <title>初级 PHP, Apache, MySQL Web 开发</title>
</head>
<body>
<?php
if ($_POST['submit'] == "Register")
{
  if ($_POST['username'] != "" && $_POST['password'] != "" &&
  $_POST['first_name'] != "" && $_POST['last_name'] != "" &&
  $_POST['email'] != "")
{
    $check_user = $_POST['username'];

    $query = "SELECT username FROM user_info WHERE username = '$check_user'";
    $result = mysql_query($query) or die(mysql_error());

    if (mysql_num_rows($result) != 0) {
        <font color="#ff0000"><b>用户名 <?php echo $_POST['username'];?>, 请选择另一个！</b></font><br>
        &nbsp;&nbsp; 已被占用
        <form action="register.php" method="post">
        用户名: <input type="text" name="username" value="<?php echo $_POST['username'];?>"><br>
        密码: <input type="password" name="password" value="<?php echo $_POST['password'];?>"><br>
        邮箱: <input type="text" name="email" value="<?php echo $_POST['email'];?>"><br>
        名字: <input type="text" name="first_name" value="<?php echo $_POST['first_name'];?>"><br>
        姓: <input type="text" name="last_name" value="<?php echo $_POST['last_name'];?>"><br>
        城市: <input type="text" name="city" value="<?php echo $_POST['city'];?>"><br>
        州: <input type="text" name="state" value="<?php echo $_POST['state'];?>"><br>
        爱好: 
        <select name="hobbies" size="10" multiple>
        <option value=""></option>
        <option value="Golfing" <?php if (in_array('Golfing', $_POST['hobbies'])) echo "selected";?>高尔夫</option>
        <option value="Hunting" <?php if (in_array('Hunting', $_POST['hobbies'])) echo "selected";?>狩猎</option>
        <option value="Reading" <?php if (in_array('Reading', $_POST['hobbies'])) echo "selected";?>阅读</option>
        <option value="Dancing" <?php if (in_array('Dancing', $_POST['hobbies'])) echo "selected";?>舞蹈</option>
        <option value="Internet" <?php if (in_array('Internet', $_POST['hobbies'])) echo "selected";?>上网</option>
        <option value="Flying" <?php if (in_array('Flying', $_POST['hobbies'])) echo "selected";?>飞行</option>
        <option value="Traveling" <?php if (in_array('Traveling', $_POST['hobbies'])) echo "selected";?>旅游</option>
        <option value="Exercising" <?php if (in_array('Exercising', $_POST['hobbies'])) echo "selected";?>运动</option>
        <option value="Computers" <?php if (in_array('Computers', $_POST['hobbies'])) echo "selected";?>电脑</option>
        <option value="Other Than Listed" <?php if (in_array('Other Than Listed', $_POST['hobbies'])) echo "selected";?>列表之外其他</option>
        </select><br>
        <input type="submit" name="submit" value="注册">&nbsp;<input type="reset" value="清除">
        </form>
    }
    else {
        $query = "INSERT INTO user_info(username, password, email, first_name, last_name, city, state, hobbies) VALUES ('" .
        mysql_real_escape_string($_POST['username']) . "', "',
        mysql_real_escape_string($_POST['password']) . "', "',
        mysql_real_escape_string($_POST['email']) . "', "',
        mysql_real_escape_string($_POST['first_name']) . "', "',
        mysql_real_escape_string($_POST['last_name']) . "', "',
        mysql_real_escape_string($_POST['city']) . "', "',
        mysql_real_escape_string($_POST['state']) . "', "',
        implode("','", (array)$_POST['hobbies']) . "')";
        $result = mysqli_query($conn,$query) or die(mysqli_error($conn));
        $_SESSION['user_logged'] = $_POST['username'];
        $_SESSION['password'] = $_POST['password'];
    ?>
    感谢 <?php echo $_POST['first_name']; ?> 注册！<br>
    <a href="index.php">点击此处</a>继续。
<?php
} else {
    <font color="#ff0000">所有必填字段均已填写*</font>
    <br>
    <form action="register.php" method="post">
    <!-- 此处省略重复的表单字段代码 -->
    </form>
}
?>
</body>
</html>
```

