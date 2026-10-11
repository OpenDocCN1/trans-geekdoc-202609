
# Online Course System - Code Files

## Home Page - index.php

```html
<!DOCTYPE html>
<html>
<head>
<title> Online Course Home </title>
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
<h1> Online Course Project </h1>
</header>
<nav>
<button> Click for Menu </button>
<ul>
  <li><a href="index.php" title="Home">Home</a></li>
  <li><a href="courses.php" title="About">Courses</a></li>
  <li><a href="login.php" title="Contact">Login</a></li>
</ul>
</nav>
<main>
<section>
<h3>Welcome to Online Course System!</h3>
<p style='text-align:left;'>In this web application, we will develop user-friendly application to enroll to courses. We primarily have 2 major users for this application: </p>
<ul style='text-align:left;'>
<li>Instructor - the one who develops course materials </li>
<li>Learner - the one who studies those developed course materials </li>
</ul>
<p style='text-align:left;'>
The instructors develop course materials and upload the same in this website. Once the course is published, they appear in the search list. The learners browse through the course list and sneek into every detail. Once they are 
comfortable with a course, they enroll into it. Once they enroll, they can view the course materials. A progress track will be there to specify how far they have completed the course. When progress reaches 100%, it marks the course to be completed.
</p>
<p>
For this application, we keep all courses free of cost!
</p>
</section>
<article class="artclass">
<div>
<h3>Courses with enrollments</h3>
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
<h3>Instructors List</h3>
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
<h4>Copyright &copy; 2020</h4>
</footer>
</body>
</html>
```

## Login Page - login.php

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
        echo "<script>alert('Invalid username or password!')</script>";
    }  
}
?>

<!DOCTYPE html>
<html>
<head>
<title> User Login </title>
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
<h1> Online Course Project </h1>
</header>
<nav>
<button> Click for Menu </button>
<ul>
  <li><a href="index.php" title="Home">Home</a></li>
  <li><a href="courses.php" title="About">Courses</a></li>
  <li><a href="login.php" title="Contact">Login</a></li>
</ul>
</nav>
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
<p>New learner or instructor? <a href="register.php">Register here</a> </p>
</section>
</main>
<footer>
<h4>Copyright &copy; 2020</h4>
</footer>
</body>
</html>
```

## Logout Page - logout.php

```php
<?php
session_start();
if(isset($_SESSION['usersession'])){
    unset($_SESSION['usersession']);
}
header('Location: login.php');
?>
```

## Functions - check.php

```php
<?php
session_start();
require('connect.php');

//functions
function get_category($con, $id){
    $get_cat = mysqli_query($con,"SELECT * FROM userlogin WHERE user_mail = '$id'");
    if($cat = mysqli_fetch_row($get_cat)){
        return $cat[2]; 
    }	
}

function get_name($con, $id, $cat){
    $str = '';
    if($cat == 'instructor'){
        $str = "SELECT * FROM instructors WHERE instruct_mail = '$id'";
    }
    if($cat == 'learner'){
        $str = "SELECT * FROM learners WHERE learn_mail = '$id'";
    }
    $get_fname = mysqli_query($con, $str);
    if($name = mysqli_fetch_row($get_fname)){
        return $name[1];
    }	  
}

function get_progress($con, $id){
    $get_enrols = mysqli_query($con,"SELECT * FROM enroll WHERE enroll_id = $id");
    $progress = 0;
    if($enrol = mysqli_fetch_row($get_enrols)){
        $enrolid = $enrol[0];
        $course = $enrol[2];
        $completed = 0;
        $contents = mysqli_query($con,"SELECT * FROM contents WHERE course_code = $course");
        $total = mysqli_num_rows($contents);
        while($content = mysqli_fetch_row($contents)){
            $contentid = $content[0];
            $records = mysqli_query($con,"SELECT * FROM record WHERE enroll_id = $enrolid AND content_id = $contentid");
            if(mysqli_num_rows($records) == 1){
                $completed = $completed + 1;
            }
        }
        $progress = round(($completed / $total) * 100);
    }
    return $progress;
}

//checking session
$usersession = '';
$category = '';
$name = '';
if(isset($_SESSION['usersession'])){
    $usersession = $_SESSION['usersession'];
    $category = get_category($con, $usersession);
    $name = get_name($con, $usersession, $category);
}
else{
    echo "<script>window.location.replace('login.php');</script>";
}  
?>
```

## Registration - register.php

[Go to Code menu](#part0056.xhtml#urllist)
