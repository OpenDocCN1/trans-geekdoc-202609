

isSessionAuthenticated() 函数用于检查会话是否为已验证的会话。验证后（参阅 login.php），值为 true 的变量 $isAuthenticated 会存储在会话中：

```
function isSessionAuthenticated()
{
    global $isAuthenticated;
    session_start();
    if (session_is_registered("isAuthenticated") &&
        $isAuthenticated) {
        return true;
    } else {
        return false;
    }
}
?>
```

## 新用户注册

以下 HTML 文件 createuser.html 显示了应用程序的新用户注册页面：

```
<html>
<head>
<title> Online Storage Application </title>
</head>
<body>
<h1> New User Registration </h1>
```

以下是用于注册新用户的 HTML 表单。表单的 action 是 createuser.php 脚本。请注意，使用了 POST 方法，因为我们不希望用户名和密码作为 URL 的一部分传递：

```
<form method="post" action="createuser.php">
<table>
<tr>
<td> firstname </td>
```

表单变量 firstname 存储用户的名字：

```
<td> <input type="text" name="firstname"/> </td>
</tr>
<tr>
<td> lastname </td>
```

表单变量 lastname 存储用户的姓氏：

```
<td> <input type="text" name="lastname"/> </td>
</tr>
<tr>
<td> email address </td>
```

表单变量 emailaddress 存储用户的电子邮件地址：

```
<td> <input type="text" name="emailaddress"/> </td>
</tr>
<tr>
<td> username </td>
```

表单变量 username 存储用户的用户名：

```
<td> <input type="text" name ="username"/> </td>
</tr>
<tr>
<td> password </td>
```

表单变量 password 和 confirmPassword 存储用户的密码：

```
<td> <input type="password" name ="password"/> </td>
</tr>
<tr>
<td> confirm password </td>
<td> <input type="password" name ="confirmPassword"/> </td>
</tr>
<tr>
<td> </td>
<td> <input type="submit" value="Submit"/> </td>
</tr>
</table>
</form>
</body>
</html>
```

以下文件 createuser.php 创建新用户：

```
<?php
include("common.php");
```

检查用户是否填写了所有表单变量。如果有任何表单变量为空，则发送错误页面：

```
// Check if the form variables are empty
$firstname = trim($firstname);
$lastname = trim($lastname);
$emailaddress = trim($emailaddress);
$username = trim($username);
$password = trim($password);
$confirmPassword = trim($confirmPassword);
if (($firstname == "") || ($lastname == "") || ($emailaddress == "") ||
($username == "") || ($password == "") || ($confirmPassword == "")) {
sendErrorPage("Error: Not all the form fields are filled ");
exit;
}
```

检查表单变量 $password 和 $confirmPassword 的值是否匹配：

```
if ($password != $confirmPassword) {
    sendErrorPage("Error: password and confirm password value don't match");
    exit;
}
```

检查用户名 $username 是否已存在。对于每个现有用户，在 $userProfileDir 目录中都会有一个配置文件：

```
// Check if the user name already exists
$userProfileFile = $userProfileDir . $fileSeparator . $username;
if (file_exists($userProfileFile)) {
    sendErrorPage("Error: User Name " . $username . " already exists");
    exit;
}
```

## 创建用户配置文件：

```
// Create user's profile file
if (($fp = fopen($userProfileFile, "w+")) < 0) {
    sendErrorPage("Internal Error: Could not create file " . $userProfileFile);
    exit;
}
```

将用户详细信息存储在配置文件中。配置文件包含由分号分隔的名称-值对：

```
fwrite($fp, "firstname:". $firstname . "\n");
fwrite($fp, "lastname:". $lastname . "\n");
fwrite($fp, "emailaddress:". $emailaddress . "\n");
fwrite($fp, "username:". $username . "\n");
```

存储密码哈希值。一般来说，以明文形式存储用户密码不是个好主意。可以改为存储密码的哈希值。可以将明文密码的哈希值与存储的哈希值进行比较，以进行身份验证。这里我们使用“带 2 字符 SALT 的标准 DES 加密”来创建哈希值。

请注意，crypt() 函数是单向函数 – 不存在 decrypt() 函数。因此，没有任何人可以从存储的哈希值中找出明文密码：

```
fwrite($fp, "password:". crypt($password, CRYPT_STD_DES) . "\n");
fclose($fp);
```

## 创建用户根目录：

```
// Create users home directory
if (createFolder("/", $username) <= 0) {
    sendErrorPage("Internal Error: Could not create directory " . $username);
    exit;
}
```

在用户根目录中创建 mimeTypes 文件。mimeTypes 文件用于存储上传文件的 MIME 类型：

```
// Create the mimeTypes file
$mimeTypeFile = $username . "/" . "mimeTypes";
if (!fopen(getAbsolutePath($mimeTypeFile), "w+")) {
    sendErrorPage("Internal Error: Could not create file " . $mimeTypeFile);
    exit;
}
?>
<html>
<head></head>
<body>
```

显示一条确认新用户注册的消息：

```
<h1> User <?php echo($username) ?> Created.
        Go to the <a href="login.html">Login page</a></h1>
</body>
</html>
```

配置文件示例：

```
firstname:Chacho
lastname:Agarwal
emailaddress:cagarwal@cagarwal.com
username:cagarwal
password:1$m8fRKpcZOX2
```

## 登录

以下 HTML 文件 login.html 显示了应用程序的登录页面：

```
<html>
<head>
<title> Online Storage Application </title>
</head>
<body>
<h1> Welcome to Online Storage Application </h1>
```

以下是用于登录的 HTML 表单。表单的 action 是 login.php 脚本。请注意，使用了 POST 方法，因为我们不希望用户名和密码作为 URL 的一部分传递：

```
<form name="LoginForm" action="login.php" method="post">
<table>
<tr>
<td>Username: </td>
```

表单变量 username 存储用户的姓名：

```
<td><input type="text" name="username"/></td>
</tr>
<tr>
<td> Password: </td>
```

表单变量 password 存储用户的密码：

```
<td><input type="password" name="password"/></td>
</tr>
<tr>
<td></td>
<td><input type="submit" value="Submit"/></td>
</tr>
</table>
</form>
</body>
</html>
```

以下文件 (login.php) 执行用户身份验证。如果身份验证成功，则显示主页；否则显示错误页面：

```
<?php
include_once("common.php");
```

确保用户输入的用户名和密码值不为空：

```
$username = trim($username);
$password = trim($password);
// Authenticate the User
if (($username == "") || ($password == "")) {
sendErrorPage("The username and password you have entered are invalid.
Please try again");
exit;
}
```

检查用户配置文件是否存在：

```
$UserProfileFile = $UserProfileDir . $fileSeparator . $username;
// Check if the user profile file exists
if (!file_exists($UserProfileFile)) {
sendErrorPage("The username and password you have entered are invalid.
Please try again");
exit;
}
```

从配置文件中获取用户名和密码哈希值：

```
// Read the profile file
$fileContent = file($UserProfileFile);
if ($fileContent == null) {
sendErrorPage("Internal Error: Could not read ".
$UserProfileFile . " file");
exit;
}
// Get the username and password
for($i=0; $i < sizeof($fileContent); $i++) {
$line = trim($fileContent[$i]);
list ($name, $value) = split(":", $line);
if ($name == "username") {
$uName = $value;
} else if ($name == "password") {
$uPassword = $value;
}
}
```

检查用户输入的密码是否与配置文件中的密码匹配。请注意，我们在配置文件中只存储了密码的哈希值，因此，为了进行匹配，需将用户输入密码的哈希值与用户配置文件中存储的哈希值进行比较：

```
if (($uName != $username) ||
($uPassword != crypt($password, CRYPT_STD_DES))) {
sendErrorPage("The username and password you have entered is invalid.
Please try again");
exit;
}
```

如果用户已通过身份验证，则创建 PHP 会话：

```
// User authenticated
// Create a session for the User and set authenticated flag
if (!session_start()) {
sendErrorPage("Internal Error: Could not create user session");
exit;
}
```

注册会话变量 isAuthenticated：

```
if (!session_register("isAuthenticated")) {
sendErrorPage("Internal Error: Could not add isAuthenticated variable
to the user session");
exit;
}
$isAuthenticated=true;
```

注册会话变量 username：

```
if (!session_register("username")) {
sendErrorPage("Internal Error: Could not add username variable
to the user session");
exit;
}
```

