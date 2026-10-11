
# Online Course Project - Code Files

## User Dashboard - `clist.php`

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
    <title> User Dashboard </title>
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
            <?php  
            echo "<h3>Hello ".$name."</h3>";
            echo "<p><a href='dashboard.php'>Dashboard</a>    <a href='logout.php'>Logout<a/></p>";
            echo "<h4><a href='newcourse.php'>Add New Course</a></h4>";
            $fetch_courses = mysqli_query($con,"SELECT * FROM courses WHERE course_instruct = '$usersession'");
            if(mysqli_num_rows($fetch_courses) == 0){
                echo "No courses created so far!";
            }
            else{
                echo "<table style='margin:0 10%;width:80%;;text-align:left;'>";
                echo "<tr>";
                echo "<th style='width:40%;'> Course Title </th>";
                echo "<th style='width:10%;'> Edit Details </th>";
                echo "<th style='width:10%;'> Manage Content </th>";
                echo "<th style='width:20%;'> Learners Count </th>";
                echo "</tr>";
            }	
            while($fetched = mysqli_fetch_row($fetch_courses)){
                echo "<tr>";
                echo "<td>".$fetched[1]."</td>";
                echo "<td><a href='editcourse.php?cid=$fetched[0]'>Edit</td>";
                echo "<td><a href='uploadcontent.php?cid=$fetched[0]'>Add</td>";
                $get_enrols = mysqli_query($con,"SELECT * FROM enroll WHERE course_code=$fetched[0]");
                echo "<td>";
                echo mysqli_num_rows($get_enrols);
                if (mysqli_num_rows($get_enrols) > 0){
                    echo "    <a href='reports.php?cid=$fetched[0]'>View";
                }
                echo "</td>";	
                echo "</tr>";
            }
            echo "</table>";
            ?> 
        </section>
    </main>
    <footer>
        <h4>Copyright &copy; 2020</h4>
    </footer>
</body>
</html>
```

---

## Add New Course - `newcourse.php`

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
        echo "<script>alert('New Course created!');window.location.replace('clist.php');</script>";
    }
    else {
        echo "<script>alert('Sorry, try again!');</script>";
    }
}
?>
<!DOCTYPE html>
<html>
<head>
    <title> New Course </title>
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
            <h3> New Course Details </h3>
            <p>
                <form method="post" name="frmnewcourse">
                    <p><input type="text" name="txtcourse" size="60" placeholder="Enter your Course Title" required></p>
                    <p><textarea name="txtdesc" cols="60" placeholder="Enter Course Description Details" required></textarea></p>
                    <p><textarea name="txtoutcome" cols="60" placeholder="Enter Course Outcomes separated by commas" required></textarea></p>
                    <p><textarea name="txteligible" cols="60" placeholder="Enter Eligibility Details separated by commas" required></textarea></p>
                    <p><input type="submit" name="newcourse" value="Create Course" class="frmbtn"></p>
                </form>
            </p>
        </section>
    </main>
    <footer>
        <h4>Copyright &copy; 2020</h4>
    </footer>
</body>
</html>
```

---

## Edit Existing Course - `editcourse.php`

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
        echo "<script>alert('Course Updated!');window.location.replace('clist.php');</script>";
    }
}
?>
<!DOCTYPE html>
<html>
<head>
    <title> Edit Course Details </title>
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
            <h3> Edit Course Details </h3>
            <p>
                <form method="post" name="frmeditcourse">
                    <input type="hidden" name="txtcourse" value="<?php echo $course; ?>"> 
                    <p><input type="text" name="txttitle" size="60" value="<?php echo $titleval; ?>"></p>
                    <p><textarea name="txtdesc" cols="60"><?php echo $describeval; ?></textarea></p>
                    <p><textarea name="txtoutcome" cols="60"><?php echo $outcomeval; ?></textarea></p>
                    <p><textarea name="txteligible" cols="60"><?php echo $eligibleval; ?></textarea></p>
                    <p><input type="submit" name="editcourse" value="Update Course" class="frmbtn"></p>
                </form>
            </p>
        </section>
    </main>
    <footer>
        <h4>Copyright &copy; 2020</h4>
    </footer>
</body>
</html>
```

---

## Upload Contents for Course - `uploadcontent.php`

[Go to Code menu](#part0056.xhtml#urllist)
