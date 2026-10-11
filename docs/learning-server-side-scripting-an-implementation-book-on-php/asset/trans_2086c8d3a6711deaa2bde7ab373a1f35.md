

# 用户仪表盘页面

```php
<?php
include ('check.php');
if (isset($_POST['changepwd'])) {
    $oldpassword = $_POST['txtoldpwd'];
    $newpassword = $_POST['txtnewpwd'];
    $get_password = mysqli_query($con, "SELECT * FROM userlogin WHERE user_mail = '$usersession'");
    $pwd = mysqli_fetch_array($get_password);
    if (password_verify($oldpassword, $pwd['user_pwd'])) {
        if ((strlen($newpassword) > 7) and (strlen($newpassword) < 21)) {
            $hashed = password_hash($newpassword, PASSWORD_DEFAULT);
            $updatepwd = "UPDATE userlogin SET user_pwd = '$hashed' WHERE user_mail = '$usersession'";
            if (mysqli_query($con, $updatepwd)) {
                echo "<script>alert('密码已更改！请使用新密码登录！');window.location.replace('logout.php');</script>";
            }
        } else {
            echo "<script>alert('密码长度必须在 8-15 个字符之间！');</script>";
        }
    } else {
        echo "<script>alert('旧密码错误！');</script>";
    }
}
if (isset($_POST['changeprofile'])) {
    $newname = $_POST['txtname'];
    $newdetails = $_POST['txtdetails'];
    if ($category == 'instructor') {
        $updateprofile1 = "UPDATE instructors SET instruct_name = '$newname' WHERE instruct_mail = '$usersession'";
        $updateprofile2 = "UPDATE instructors SET instruct_details = '$newdetails' WHERE instruct_mail = '$usersession'";
    }
    if ($category == 'learner') {
        $updateprofile1 = "UPDATE learners SET learn_name = '$newname' WHERE learn_mail = '$usersession'";
        $updateprofile2 = "UPDATE learners SET learn_details = '$newdetails' WHERE learn_mail = '$usersession'";
    }
    if (mysqli_query($con, $updateprofile1) and mysqli_query($con, $updateprofile2)) {
        echo "<script>alert('个人资料已更新！');</script>";
    }
}
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
            if ($(window).width() > 600)
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
            <li><a href="index.php" title="首页">首页</a></li>
            <li><a href="courses.php" title="关于">课程</a></li>
            <li><a href="login.php" title="联系">登录</a></li>
        </ul>
    </nav>
    <main>
        <section>
            <?php  
            echo "<h3>你好 " . $name . "</h3>";
            echo "<p><a href='dashboard.php'>仪表盘</a>    <a href='logout.php'>登出</a></p>";
            $str = '';
            $details = '';
            if ($category == 'instructor') {
                $str = "SELECT * FROM instructors WHERE instruct_mail = '$usersession'";
            }
            if ($category == 'learner') {
                $str = "SELECT * FROM learners WHERE learn_mail = '$usersession'";
            }
            $fetch_details = mysqli_query($con, $str);
            if ($fetch = mysqli_fetch_row($fetch_details)) {
                $details = $fetch[2];
            } 
            ?>
            <form method="post" name="frmpwd">
                <p><input type="password" name="txtoldpwd" size="40" placeholder="请输入旧密码" required></p>
                <p><input type="password" name="txtnewpwd" size="40" placeholder="请输入新密码 8-15 个字符" required></p>
                <p><input type="submit" name="changepwd" value="修改密码" class="frmbtn"></p>
            </form>
            <p><hr></p>
            <form method="post" name="frmprofile">
                <p><input type="text" name="txtname" size="40" value="<?php echo $name; ?>" required></p>
                <p><textarea name="txtdetails" cols="40" required><?php echo $details; ?></textarea></p>
                <p><input type="submit" name="changeprofile" value="更新个人资料" class="frmbtn"></p>
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

# 课程页面 - courses.php

```php
<?php
session_start();
require('connect.php');
if (isset($_POST['enroll'])) {
    if (isset($_SESSION['usersession'])) {
        $usersession = $_SESSION['usersession'];
        $course = $_POST['txtcourse'];
        $get_enrol = mysqli_query($con, "SELECT * FROM enroll WHERE learn_mail = '$usersession' AND course_code = $course");
        if (mysqli_num_rows($get_enrol) == 0) {
            $enrol = "INSERT INTO enroll VALUES (NULL, '$usersession', $course, DEFAULT, NULL)";
            if (mysqli_query($con, $enrol)) {
                echo "<script>alert('您已成功报名！');window.location.replace('elist.php');</script>";
            }
        } else {
            echo "<script>alert('您已经报名过了！');window.location.replace('elist.php');</script>";
        }
    } else {
        echo "<script>alert('请先登录再报名！');</script>";
    }
}
?>
```

```html
<!DOCTYPE html>
<html>
<head>
    <title> 课程 </title>
    <link rel="stylesheet" href="css/style.css">
    <meta name="viewport" content="width=device-width, initial-scale=1.0"> 
    <style>
        .cl {
            margin: 5px;
            display: inline-block;
            vertical-align: top;
            width: 300px;
            height: 200px;
            border: 1px solid #ccc;
        }
    </style>
    <script src="https://ajax.googleapis.com/ajax/libs/jquery/3.4.1/jquery.min.js"></script>
    <script>
        $(document).ready(function(){
            if ($(window).width() > 600)
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
            <li><a href="index.php" title="首页">首页</a></li>
            <li><a href="courses.php" title="关于">课程</a></li>
            <li><a href="login.php" title="联系">登录</a></li>
        </ul>
    </nav>
    <main>
        <?php
        $pattern = '';
        $patternexist = false;
        if (isset($_POST['searchcourse'])) {
            $pattern = $_POST['txtsearch'];
            $patternexist = true;
        }
        ?>
        <section>
            <h3>课程</h3>
            <div>
                <form method="post" name="frmsearch">
                    <p><input type="search" name="txtsearch" size="60" value="<?php if ($patternexist) { echo $pattern; } ?>"></p>
                    <p><input type="submit" name="searchcourse" class="frmbtn" value="搜索课程"></p>
                </form>
            </div>
            <?php
            require('connect.php');
            $query = "SELECT * FROM courses";
            if ($patternexist) {
                $query = "SELECT * FROM courses WHERE course_title LIKE '%$pattern%' OR course_description LIKE '%$pattern%'";
            }
            $select_courses = mysqli_query($con, $query);
            while ($selected = mysqli_fetch_row($select_courses)) {
                echo "<div class='cl'>";
                echo "<h4><a href='details.php?search=$selected[0]'>" . $selected[1] . "</a></h4>";
                echo "<p style='height:70px';>" . $selected[3] . "</p>";
                echo "<form method='post'>";
                echo "<input type='hidden' name='txtcourse' value='$selected[0]'>";
                echo "<input type='submit' name='enroll' value = '报名' class='frmbtn'>";
                echo "</form>";
                echo "</div>";   
            }
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

# 课程详情页面 - details.php

