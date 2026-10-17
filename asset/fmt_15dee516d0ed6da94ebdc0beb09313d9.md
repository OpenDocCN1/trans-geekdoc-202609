
<section>

```php
<?php

if (($contents == 999) || ($contents == 0)) {
    echo "Please choose a content title!";
} else {
    $fetch_content = mysqli_query($con, "SELECT * FROM contents WHERE content_id = $contents");
    if ($fetch = mysqli_fetch_row($fetch_content)) {
        echo "<h4>" . $fetch[1] . "</h4>";
        $filestring = explode('.', $fetch[3]);
        $file_ext = strtolower(end($filestring));
        $exts = array('doc', 'docx', 'ppt', 'pptx');
        if (in_array($file_ext, $exts)) {
            echo "<p>The content will be downloaded!</p>";
        }
        echo "<p><iframe src='$fetch[3]' height='auto' width='80%' height='500px' frameborder='0'></iframe></p>";
    }
}
?>
</section>
```

此处，我们检查 `$contents` 值是否等于 0 或 999，然后显示“Please choose a content title!”消息。这意味着，每当未选择内容标题时，将显示此消息。

像往常一样，我们查找文件的扩展名，如果它是 doc、docx、ppt、pptx 之一，则无法在 HTML 文件中显示。因此，我们打印一条消息，提示文件将被下载，当 `iframe` 标签加载时下载将开始。如果文件扩展名是 pdf、mp4、txt、rtf 之一，则通过 `iframe` 标签显示。

尝试选择一个内容，查看相应文件是显示还是下载。

现在，还有一项待办任务！

### 记录学习者进度

此进度也将在同一页面中记录。

我们需要在 `iframe` 标签下方包含插入记录表的代码：

替换上面的 if 代码块：

```php
if ($fetch = mysqli_fetch_row($fetch_content)) {
    echo "<h4>" . $fetch[1] . "</h4>";
    $filestring = explode('.', $fetch[3]);
    $file_ext = strtolower(end($filestring));
    $exts = array('doc', 'docx', 'ppt', 'pptx');
    if (in_array($file_ext, $exts)) {
        echo "<p>The content will be downloaded!</p>";
    }
    echo "<p><iframe src='$fetch[3]' height='auto' width='80%' height='500px' frameborder='0'></iframe></p>";
    $get_enrolid = mysqli_query($con, "SELECT * FROM enroll WHERE learn_mail = '$usersession' AND course_code = $course");
    $enrolid = mysqli_fetch_array($get_enrolid);
    $eid = $enrolid['enroll_id'];
    $check_records = mysqli_query($con, "SELECT * FROM record WHERE enroll_id = $eid AND content_id = $contents");
    if (mysqli_num_rows($check_records) == 0) {
        mysqli_query($con, "INSERT INTO record VALUES ($eid, $contents)");
    }
    if (get_progress($con, $eid) == 100) {
        mysqli_query($con, "UPDATE enroll SET learn_end = NOW() WHERE enroll_id = $eid");
    }
}
```

*   我们使用 `$usersession` 变量和 `$course` 变量查找 `enroll_id`。
*   我们检查 `content_id` 和 `$enroll_id` 是否已插入 `record` 表中。
*   如果未插入，我们将数据插入 `record` 表。
*   当进度达到 100 时，我们将当前日期设为课程的完成日期。

让我展示访问课程名称 1 的内容。

*这是一张 GIF 图片。请确保您的设备支持 GIF 格式。*

![1604667223-access-contents](img/image00353.gif)

我们将查看 record 表的 phpmyadmin 截图。

![8-5-3](img/image00354.jpeg)

我们要从讲师仪表板查看学习者的进度吗？

退出学习者身份并以讲师身份登录：

您将看到“已注册学习者数量”旁边有一个链接：

![8-5-4](img/image00355.jpeg)

点击“View”查看学习者的进度：

![8-5-5](img/image00356.jpeg)

我想，应用程序的开发到此几乎结束了！我们涵盖了第 6.1 章项目大纲中指定的所有内容。

我们只剩下一个页面——应用程序的主页。我们将在下一节中完成它。

---

### 8.6 主页

---

我们要做的唯一事情就是完成主页任务：

*   显示课程及每门课程的注册学习者数量。
*   显示讲师的详细信息。

它们都是简单的检索过程！

打开 `index.php` 页面。

将 title 标签内容更改为 **Online Course Home**。

替换 article 标签内容为：

```php
<article class="artclass">
<div>
<h3>Courses with enrollments</h3>
<?php
require('connect.php');
$get_courses = mysqli_query($con, "SELECT * FROM courses");
while ($courses = mysqli_fetch_row($get_courses)) {
    $enrols = mysqli_query($con, "SELECT * FROM enroll WHERE course_code = $courses[0]");
    echo "<p>" . $courses[1] . " &emsp; - &emsp; " . mysqli_num_rows($enrols) . "</p>";
}
?>
</div>
<div style='vertical-align:top;'>
<h3>Instructors List</h3>
<?php
$get_instr = mysqli_query($con, "SELECT * FROM instructors");
while ($instr = mysqli_fetch_row($get_instr)) {
    echo "<p>" . $instr[1] . " - " . $instr[2] . "</p>";
}
?>
</div>
</article>
```

我们已完成简单的检索，以根据模板显示相关信息。

```php
$get_courses = mysqli_query($con, "SELECT * FROM courses");
while ($courses = mysqli_fetch_row($get_courses)) {
    $enrols = mysqli_query($con, "SELECT * FROM enroll WHERE course_code = $courses[0]");
    echo "<p>" . $courses[1] . " &emsp; - &emsp; " . mysqli_num_rows($enrols) . "</p>";
}
```

我们获取所有课程。在 while 循环中，针对每门课程，我们获取该特定课程的注册情况。`mysqli_num_rows($enrols)` 保存着该课程的注册人数。

```php
$get_instr = mysqli_query($con, "SELECT * FROM instructors");
while ($instr = mysqli_fetch_row($get_instr)) {
    echo "<p>" . $instr[1] . " - " . $instr[2] . "</p>";
}
```

我们获取所有讲师并显示他们的两项详细信息：讲师姓名和讲师详情。

让我给出截图：

![8-6](img/image00357.jpeg)

---

### 8.7 应用程序演示

---

让我展示一个工作应用程序的演示视频！

我将创建另一个学习者、另一个讲师、另一门课程，并为新课程上传内容。我们将把新学习者注册到新课程中，并查看每个阶段的进度。

这是演示！

*这是一张 GIF 图片。请确保您的设备支持 GIF 格式。*

![1604667613-Demo](img/image00358.gif)

**注意：**

出于调试原因和代码替换问题，让我逐页提供代码。

点击文件名查看代码。

**代码菜单：**

1.  数据库连接 - connect.php
2.  主页 - index.php
3.  登录页 - login.php
4.  登出页 - logout.php
5.  函数 - check.php
6.  注册 - register.php
7.  仪表板页 - dashboard.php
8.  个人资料页 - profile.php
9.  课程页 - courses.php
10. 课程详情页 - details.php
11. 学习者课程注册 - elist.php
12. 课程内容 - contents.php
13. 管理课程 - clist.php
14. 添加新课程 - newcourse.php
15. 编辑现有课程 - editcourse.php
16. 上传课程内容 - uploadcontent.php
17. 学习者报表 - reports.php

---

#### 数据库连接 - connect.php

```php
<?php
$host = "localhost";
$username = "ocuser";
$password = "Pass@OC20";
$database = "onlinecourse";
$con = mysqli_connect($host, $username, $password, $database);
if (!$con) {
    die("Connection failed: " . mysqli_connect_error());
}
?>
```

转到代码菜单

---

#### 主页 - index.php

### 在线课程系统 - 代码文件

#### 首页 - index.php

```html
<!DOCTYPE html>
<html>
<head>
<title> 在线课程首页 </title>
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
<h3>欢迎来到在线课程系统！</h3>
<p style='text-align:left;'>在本 Web 应用中，我们将开发一个用户友好的应用程序用于课程注册。我们主要有 2 类主要用户：</p>
<ul style='text-align:left;'>
<li>讲师 - 开发课程材料的人员 </li>
<li>学习者 - 学习这些开发好的课程材料的人员 </li>
</ul>
<p style='text-align:left;'>
讲师开发课程材料并上传至本网站。课程发布后，将出现在搜索列表中。学习者浏览课程列表并深入了解每个细节。一旦他们对某门课程满意，即可注册。注册后，他们可以查看课程材料。系统将提供进度跟踪以显示完成程度。当进度达到 100% 时，标记课程为已完成。
</p>
<p>
本应用中，所有课程均免费！
</p>
</section>
<article class="artclass">
<div>
<h3>有注册人数的课程</h3>
<?php
require('connect.php');
$get_courses = mysqli_query($con,"SELECT * FROM courses");
while($courses = mysqli_fetch_row($get_courses)){
    $enrols = mysqli_query($con,"SELECT * FROM enroll WHERE course_code = $courses[0]");
    echo "<p>".$courses[1]."  -  ".mysqli_num_rows($enrols)."</p>";
}
?>
</div>
<div style='vertical-align:top;'>
<h3>讲师列表</h3>
<?php
$get_instr= mysqli_query($con,"SELECT * FROM instructors");
while($instr = mysqli_fetch_row($get_instr)){
    echo "<p>".$instr[1]." - ".$instr[2]."</p>";
}
?>
</div>
</article>
</main>
<footer>
<h4>版权所有 &copy; 2020</h4>
</footer>
</body>
</html>
```

#### 登录页面 - login.php

```php
<?php
session_start();
if(isset($_SESSION['usersession'])){
    echo "<script>window.location.replace('dashboard.php')</script>";
}
require('connect.php');
$auth = true;
$hashedpwd = '';
if(isset($_POST['login'])){
    $username = $_POST['txtuser'];
    $password = $_POST['txtpwd'];
    $select_user = mysqli_query($con,"SELECT * FROM userlogin WHERE user_mail='$username'");
    if($user = mysqli_fetch_row($select_user)){
        $hashedpwd = $user[1];
    }
    else{
        $auth = false;
    }
    if(!(password_verify($password,$hashedpwd))){
        $auth = false;
    }
    if($auth){
        $_SESSION['usersession'] = $username;
        echo "<script>window.location.replace('dashboard.php')</script>";
    }
    else{
        echo "<script>alert('用户名或密码无效！')</script>";
    }  
}
?>
<!DOCTYPE html>
<html>
<head>
<title> 用户登录 </title>
```
