

# 在线课程项目 - 代码文件

## 用户仪表板 - `clist.php`

```php
<?php
include ('check.php');
if($category == 'learner'){
    header('logout.php');
}
?>
<!DOCTYPE html>
<html>
<head>
    <title> 用户仪表板 </title>
    <link rel="stylesheet" href="css/style.css">
    <meta name="viewport" content="width=device-width, initial-scale=1.0"> 
    <style>
        .cl{
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
            <li><a href="index.php" title="主页">主页</a></li>
            <li><a href="courses.php" title="关于">课程</a></li>
            <li><a href="login.php" title="联系">登录</a></li>
        </ul>
    </nav>
    <main>
        <section>
            <?php  
            echo "<h3>你好 ".$name."</h3>";
            echo "<p><a href='dashboard.php'>仪表板</a>    <a href='logout.php'>退出登录<a/></p>";
            echo "<h4><a href='newcourse.php'>添加新课程</a></h4>";
            $fetch_courses = mysqli_query($con,"SELECT * FROM courses WHERE course_instruct = '$usersession'");
            if(mysqli_num_rows($fetch_courses) == 0){
                echo "暂无已创建的课程！";
            }
            else{
                echo "<table style='margin:0 10%;width:80%;;text-align:left;'>";
                echo "<tr>";
                echo "<th style='width:40%;'> 课程标题 </th>";
                echo "<th style='width:10%;'> 编辑详情 </th>";
                echo "<th style='width:10%;'> 管理内容 </th>";
                echo "<th style='width:20%;'> 学习者数量 </th>";
                echo "</tr>";
            }	
            while($fetched = mysqli_fetch_row($fetch_courses)){
                echo "<tr>";
                echo "<td>".$fetched[1]."</td>";
                echo "<td><a href='editcourse.php?cid=$fetched[0]'>编辑</td>";
                echo "<td><a href='uploadcontent.php?cid=$fetched[0]'>添加</td>";
                $get_enrols = mysqli_query($con,"SELECT * FROM enroll WHERE course_code=$fetched[0]");
                echo "<td>";
                echo mysqli_num_rows($get_enrols);
                if (mysqli_num_rows($get_enrols) > 0){
                    echo "    <a href='reports.php?cid=$fetched[0]'>查看";
                }
                echo "</td>";	
                echo "</tr>";
            }
            echo "</table>";
            ?> 
        </section>
    </main>
    <footer>
        <h4>版权所有 &copy; 2020</h4>
    </footer>
</body>
</html>
```

---

## 添加新课程 - `newcourse.php`

```php
<?php
include('check.php');
if(isset($_POST['newcourse'])){
    $title = $_POST['txtcourse'];
    $describe = $_POST['txtdesc'];
    $instruct = $usersession;
    $outcome = $_POST['txtoutcome'];
    $eligible = $_POST['txteligible'];
    $insert = mysqli_query($con,"INSERT INTO courses VALUES (NULL,'$title','$instruct','$describe','$outcome','$eligible')");
    if($insert){
        echo "<script>alert('新课程创建成功！');window.location.replace('clist.php');</script>";
    }
    else {
        echo "<script>alert('抱歉，请重试！');</script>";
    }
}
?>
<!DOCTYPE html>
<html>
<head>
    <title> 新课程 </title>
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
            <li><a href="index.php" title="主页">主页</a></li>
            <li><a href="courses.php" title="关于">课程</a></li>
            <li><a href="login.php" title="联系">登录</a></li>
        </ul>
    </nav>
    <main>
        <section>
            <h3> 新课程详情 </h3>
            <p>
                <form method="post" name="frmnewcourse">
                    <p><input type="text" name="txtcourse" size="60" placeholder="请输入课程标题" required></p>
                    <p><textarea name="txtdesc" cols="60" placeholder="请输入课程描述详情" required></textarea></p>
                    <p><textarea name="txtoutcome" cols="60" placeholder="请输入课程目标，用逗号分隔" required></textarea></p>
                    <p><textarea name="txteligible" cols="60" placeholder="请输入资格要求详情，用逗号分隔" required></textarea></p>
                    <p><input type="submit" name="newcourse" value="创建课程" class="frmbtn"></p>
                </form>
            </p>
        </section>
    </main>
    <footer>
        <h4>版权所有 &copy; 2020</h4>
    </footer>
</body>
</html>
```

---

## 编辑现有课程 - `editcourse.php`

```php
<?php
include('check.php');
$course = '';
$instructor = $usersession;
if(isset($_REQUEST['cid'])){
    $course = $_REQUEST['cid'];
} 

$get_details = mysqli_query($con,"SELECT * FROM courses WHERE course_code = $course");
if($details = mysqli_fetch_row($get_details)){
    $titleval = $details[1];
    $describeval = $details[3];   
    $outcomeval = $details[4];
    $eligibleval = $details[5];  
}
if(isset($_POST['editcourse'])){
    $course = $_POST['txtcourse'];
    $title = $_POST['txttitle'];
    $describe = $_POST['txtdesc'];
    $outcome = $_POST['txtoutcome'];
    $eligible = $_POST['txteligible'];
    $update = false;
    if($title != $titleval){
        $update1 = mysqli_query($con,"UPDATE courses SET course_title = '$title' WHERE course_code = $course");
        $titleval = $title;
        $update = true;
    }
    if($describe != $describeval){
        $update2 = mysqli_query($con,"UPDATE courses SET course_description = '$describe' WHERE course_code = $course");
        $describeval = $describe;
        $update = true;
    }
    if($outcome != $outcomeval){
        $update3 = mysqli_query($con,"UPDATE courses SET course_outcome = '$outcome' WHERE course_code = $course");
        $outcomeval = $outcome;
        $update = true;
    }
    if($eligible != $eligibleval){
        $update4 = mysqli_query($con,"UPDATE courses SET course_eligibility = '$eligible' WHERE course_code = $course");
        $eligibleval = $eligible;
        $update = true;
    }
    if($update){
        echo "<script>alert('课程已更新！');window.location.replace('clist.php');</script>";
    }
}
?>
<!DOCTYPE html>
<html>
<head>
    <title> 编辑课程详情 </title>
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
            <li><a href="index.php" title="主页">主页</a></li>
            <li><a href="courses.php" title="关于">课程</a></li>
            <li><a href="login.php" title="联系">登录</a></li>
        </ul>
    </nav>
    <main>
        <section>
            <h3> 编辑课程详情 </h3>
            <p>
                <form method="post" name="frmeditcourse">
                    <input type="hidden" name="txtcourse" value="<?php echo $course; ?>"> 
                    <p><input type="text" name="txttitle" size="60" value="<?php echo $titleval; ?>"></p>
                    <p><textarea name="txtdesc" cols="60"><?php echo $describeval; ?></textarea></p>
                    <p><textarea name="txtoutcome" cols="60"><?php echo $outcomeval; ?></textarea></p>
                    <p><textarea name="txteligible" cols="60"><?php echo $eligibleval; ?></textarea></p>
                    <p><input type="submit" name="editcourse" value="更新课程" class="frmbtn"></p>
                </form>
            </p>
        </section>
    </main>
    <footer>
        <h4>版权所有 &copy; 2020</h4>
    </footer>
</body>
</html>
```

---

## 为课程上传内容 - `uploadcontent.php`

[前往代码菜单](#part0056.xhtml#urllist)

