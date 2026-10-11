

# 用户注册页面 - register.php

```php
<?php
require('connect.php');
if (isset($_POST['register'])) {
    $category = $_POST['txtusercategory'];
    $usermail = $_POST['txtmail'];
    $userpwd = $_POST['txtpwd'];
    $name = $_POST['txtname'];
    $details = $_POST['txtdetails'];

    if ((strlen($userpwd) > 7) && strlen($userpwd < 21)) {
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
        if ($check_insert1 and $check_insert2) {
            echo "<script>alert('Registration successful!');window.location.replace('login.php');</script>";
        } else {
            echo "<script>alert('Sorry! Try again!');</script>";
        }
    } else {
        echo "<script>alert('Password should be between 8-15 characters');</script>";
    }
}
?>
```

```html
<!DOCTYPE html>
<html>
<head>
    <title> 用户注册 </title>
    <link rel="stylesheet" href="css/style.css">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <script src="https://ajax.googleapis.com/ajax/libs/jquery/3.4.1/jquery.min.js"></script>
    <script>
    $(document).ready(function(){
        if($(window).width() > 600)
            $("ul").show();
        else
            $("ul").hide();
        $("button").click(function(){
            $("ul").slideToggle();
        });
    });
    </script>
</head>
<body>
<header>
    <h1> 在线课程项目 </h1>
</header>
<nav>
    <button> 点击查看菜单 </button>
    <ul>
        <li><a href="index.php" title="Home">首页</a></li>
        <li><a href="courses.php" title="About">课程</a></li>
        <li><a href="login.php" title="Contact">登录</a></li>
    </ul>
</nav>
<main>
    <section>
        <h3> 用户注册 </h3>
        <form method="post" name="frmregister">
            <p><select name="txtusercategory">
                <option value="">您是谁？</option>
                <option value="learner">学习者</option>
                <option value="instructor">讲师</option>
            </select></p>
            <p><input type="email" name="txtmail" size="40" placeholder="请输入您的邮箱地址" required></p>
            <p><input type="password" name="txtpwd" size="40" placeholder="请输入您的密码 8-15 位字符" required></p>
            <p><input type="text" name="txtname" size="40" placeholder="请输入您的全名" required></p>
            <p><textarea name="txtdetails" cols="40" placeholder="请输入您的详细信息" required></textarea></p>
            <p><input type="submit" name="register" value="注册" class="frmbtn"></p>
        </form>
    </section>
</main>
<footer>
    <h4>版权所有 &copy; 2020</h4>
</footer>
</body>
</html>
```

[前往代码菜单](#part0056.xhtml#urllist)

---

# 仪表盘页面 - dashboard.php

```php
<?php
include ('check.php');
?>
```

```html
<!DOCTYPE html>
<html>
<head>
    <title> 用户仪表盘 </title>
    <link rel="stylesheet" href="css/style.css">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <style>
    .cl {
        margin: 5px;
        display: inline-block;
        vertical-align: top;
        width: 300px;
        height: 100px;
        border: 1px solid #ccc;
    }
    </style>
    <script src="https://ajax.googleapis.com/ajax/libs/jquery/3.4.1/jquery.min.js"></script>
    <script>
    $(document).ready(function(){
        if($(window).width() > 600)
            $("ul").show();
        else
            $("ul").hide();
        $("button").click(function(){
            $("ul").slideToggle();
        });
    });
    </script>
</head>
<body>
<header>
    <h1> 在线课程项目 </h1>
</header>
<nav>
    <button> 点击查看菜单 </button>
    <ul>
        <li><a href="index.php" title="Home">首页</a></li>
        <li><a href="courses.php" title="About">课程</a></li>
        <li><a href="login.php" title="Contact">登录</a></li>
    </ul>
</nav>
<main>
    <section>
        <?php
        echo "<h3>你好 " . $name . "</h3>";
        echo "<p><a href='logout.php'>退出登录<a/></p>";
        echo "<div class='cl'>";
        if ($category == 'instructor') {
            echo "<h3><a href='clist.php'>课程<a/></h3>";
            echo "<p>管理课程、内容和报告</p>";
        }
        if ($category == 'learner') {
            echo "<h3><a href='elist.php'>报名记录<a/></h3>";
            echo "<p>已报名课程和内容访问</p>";
        }
        echo "</div>";
        echo "<div class='cl'>";
        echo "<h3><a href='profile.php'>个人资料<a/></h3>";
        echo "<p>修改密码和个人资料</p>";
        echo "</div>";
        ?>
    </section>
</main>
<footer>
    <h4>版权所有 &copy; 2020</h4>
</footer>
</body>
</html>
```

[前往代码菜单](#part0056.xhtml#urllist)

---

# 个人资料页面 - profile.php

