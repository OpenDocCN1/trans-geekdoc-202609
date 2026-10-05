

```php
if(isset($_POST['submit'])) {
    if (empty($_POST["name"])) {
        $nameError = "Name is required";
    } else {
        $name = test_input($_POST["name"]);
        // check name only contains letters and whitespace
        if (!preg_match('/^[a-zA-Z ]*$/, $name)) {
            $nameError = "Only letters and white space allowed";
        }
    }
    if (empty($_POST["email"])) {
        $emailError = "Email is required";
    } else {
        $email = test_input($_POST["email"]);
        // check e-mail address syntax is valid or not
        if (!preg_match('/\w-]+@[\w-]+\.[\w-]+/', $email)) {
            $emailError = "Invalid email format";
        }
    }
    if (empty($_POST["website"])) {
        $website = "";
    } else {
        $website = test_input($_POST["website"]);
        // check address syntax is valid or not(this regular expression allows dashes in the URL)
        if (! preg_match('/\b(?:https?|ftp):://\\www\.)[-a-z0-9+&@#%$/*~!.;;]*[-a-z0-9+&@#%$%/~_|]/i", $website)) {
            $websiteError = "Invalid URL";
        }
    }
    if (empty($_POST["comment"])) {
        $comment = "";
    } else {
        $comment = test_input($_POST["comment"]);
    }
    if (empty($_POST["gender"])) {
        $genderError = "Gender is required";
    } else {
        $gender = test_input($_POST["gender"]);
    }
}
function test_input($data) {
    $data = trim($data);
    $data = stripslashes($data);
    $data = htmlspecialchars($data);
    return $data;
}
//php code ends here
?>
```

![](img/f8aa82c4ef45031ca4eadc2bb946c87a_203_0.png)

```php
<?php
$username = check_input($_POST['username']);
$email = check_input($_POST['email']);
$likite = check_input($_POST['likite']);
$comments = check_input($_POST['comments']);
?>
```

```html
<html>
<body>
  Your name is: <?php echo $username; ?><br />
  Your e-mail: <?php echo $email; ?><br />
  <br />
```

# Web 技术

你喜欢这个网站吗？<?php echo $likeit; ?><br />

<br />

评论：<br />

<?php echo $comments; ?>

</body>
</html>
```

```php
<?php
function check_input($data)
{
  $data = trim($data);
  $data = stripslashes($data);
  $data = htmlspecialchars($data);
  return $data;
}
?>
```

# 来自“validation.php”的 HTML 代码段

```html
<!DOCTYPE html>
<html>
<head>
  <title>PHP 表单验证 - 演示</title>
  <meta content="noindex, nofollow" name="robots">
  <link href="style.css" rel="stylesheet">
</head>
<body>
  <div class="maindiv">
    <div class="form_div">
      <div class="title">
```

# 基础计算机编程：PHP

```html
<h2>使用 PHP 进行表单验证</h2>
</div>
<form action="validation.php" method="post">
<h2>表单</h2>
<span class="error">* 必填字段。</span>
姓名：
<input class="input" name="name" type="text" value="">
<span class="error">* <?php echo $nameError;?></p>
邮箱：
<input class="input" name="email" type="text" value="">
<span class="error">* <?php echo $emailError;?></p>
性别：
<input class="radio" name="gender" type="radio" value="female">
<input class="radio" name="gender" type="radio" value="male">男
<span class="error">*<?php echo $genderError;?></p>
网站：
<input class="input" name="website" type="text" value="">
<span class="error">?<?php echo $websiteError;?></p>
评论：
<textarea cols="40" name="comment" rows="5"></textarea>
<input class="submit" name="submit" type="submit" value="提交">
</form>
</div>
</body>
</html>
```

# CSS 文件：style.css

```css
@import "http://fonts.googleapis.com/css?family=Droid+Serif";
/* 上行代码用于导入 Google 字体样式 */
.maindiv{
margin:0 auto;
width:980px;
height:500px;
background:#fff;
padding-top:20px;
font-size:14px;
}
.title{
width:500px;
height:70px;
text-shadow:2px 2px 2px #cfcfcf;
font-size:16px;
text-align:center;
font-family:' Serif',serif
}
.form_div{
width:70%;
float:left
}
form{
width:440px;
border:1px dashed #ccc;
padding:10px 30px 40px;
background-color:#f0fff;
font-family:' Serif',serif
}
h2{
text-align:center;
text-shadow:2px 2px 2px #cfcfcf;
}
textarea{
width:250px;
height:60px;
border-radius:1px;
box-shadow:0 0 1px 2px #123456;
margin-top:10px;
padding:5px;
border:none;
}
.input{
width:250px;
height:15px;
border-radius:0px;
box-shadow:0 0 1px 2px #123456;
margin-top:10px;
padding:5px;
border:none;
}
```

