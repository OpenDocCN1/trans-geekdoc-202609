
```php
<?php
//Connect to database
$con = mysqli_connect("localhost", "root", "", "mydb");
//execute simple query
$result = mysqli_query("SELECT * FROM employee",$con);
echo "<select style='width:150px'>";
while ($row = mysqli_fetch_array($result))
{

echo "<option>".$row[0]."</option>";
}

mysqli_free_result($result);
?>
```

### 示例4：在HTML表格中显示MySQL记录

```php
<?php
//Connecting to the database

$con = mysqli_connect("localhost", "root", "", "mydb");

//execute simple query

$result = mysqli_query("SELECT * FROM employee",$con);
?>
```

<table border="1" width="400" cellpadding="5">
<?php
while ($row = mysqli_fetch_assoc($result))
{
?>
<tr>
<td><?php echo $row['name']; ?></td>
<td><?php echo $row['email']; ?></td>
<td><?php echo $row['phone']; ?></td>
</tr>
<?php
}
?>
</table>

### 示例4：使用MySQL where子句的基本搜索操作

### HTML 表单

```html
<html>
<head>
<title>Simple Search</title>
</head>
<body>
<form action="search-records.php" method="get">
Name : <input type="text" name="txtName" placeholder="Enter few letters">
<input type="submit" value="Search">
</form>
</body>
</html>
```

![](img/9ab4a56a650535285811bb802190e58f_90_0.png)

### Search.php

```php
<?php
$name=$_REQUEST['txtname'];
// Connecting to the database
$con = mysqli_connect("localhost", "root", "", "mydb");
//execute simple query
$result = mysqli_query("select * from employee where name like '%$name%' ",$con);

?>
```

<table border="1" width="400" cellpadding="5">

<?php

while ($row = mysqli_fetch_assoc($result))

{

?>

<tr>

<td><?php echo $row['name']; ?></td>

<td><?php echo $row['email']; ?></td>

<td><?php echo $row['phone']; ?></td>

</tr>

<?php

}

?>

</table>

### 说明

### 示例

```php
<?php
if(!file_exists("/docs/resume.txt"))
{
    die("File not found");
}
else
{
    $file = fopen("/docs/resume.txt","r");
}
?>
```

## 示例：

```php
<?php
$a = 0;
$b = 200;
$result = $b/$a;
echo "RESULT: ". $result;
?>
```

输出：Warning: Division by zero in ... on line 4

## 示例：

```php
<?php
echo "Hi lets learn PHP"
echo "<br/>This is another line";
?>
```

输出：Parse error: syntax error, unexpected 'echo' (T_ECHO), expecting ',' or ';' in ... on line 3

## **PHP 中的一些可能错误**

- `E_ERROR`——致命的运行时错误。脚本的执行被中止。

- `E_WARNING`——非致命错误。执行不会中止。

- `E_PARSE`——编译时的解析错误。

- `E_NOTICE`——运行时的通知。

- `E_ALL`——除`E_STRICT`级别之外的所有错误和警告。

- `E_CORE_WARNING`——PHP初始启动期间发生的非致命运行时错误。

我们可以在以下几个不同的位置控制错误：

- 在 `php.ini` 文件中

- 在 Web 服务器上的 `.htaccess` 文件中

- 从你自己的 PHP 代码中。

我们也可以在运行时通过从自己的PHP代码中调用 `error_reporting()` 函数来做到这一点，如下所示：

```
error_reporting(E_ALL);
```

要打开错误日志并将错误记录到我们指定的日志文件中（而不是默认的错误日志文件，默认通常是 Web 服务器的错误日志文件）：

```
log_errors = on
error_log = "/tmp/error.log"
```

## **创建自定义错误处理器：**

我们只需创建一个特殊函数，当 PHP 中发生错误时可以调用该函数。在示例中，如果发生特定错误，我们将发送一封包含错误信息的电子邮件：

```php
<?php
//error handler function
function customError($errno, $errstr)
{
    echo "<b>Error:</b> [$errno] $errstr<br>";
    echo "Error Occurred";
    error_log("Error: [$errno] $errstr",1,
    "info@websjyoti.com","From: webmaster@websjyoti.com");
}

//set error handler
set_error_handler("customError",E_USER_WARNING);

//trigger error
$test=2;
if ($test>=1)
{
    trigger_error("Value must be 1 or below",E_USER_WARNING);
}
?>
```

## 解释：

`set_error_handler()`：PHP 的默认错误处理器是内置的错误处理器。我们在脚本运行期间将上面的函数设为默认错误处理器。由于我们希望自定义函数处理所有错误，`set_error_handler()` 只需要一个参数，也可以添加第二个参数来指定错误级别。

### 示例

`set_error_handler("customError",E_USER_WARNING);` 当非法输入发生时，`trigger_error()` 函数会引发错误。

## 使用 include() 函数：

假设你想在每个页面上打印相同的信息，比如公司的详细信息和地址，或者今天的日期。如果你在网站的每个页面中都放置相同的代码，那效率并不高，因为——

- 你一遍又一遍地输入相同的信息，这不是一个好方法。

- 如果需要更新或更改，你必须对网站的每个页面进行修改，这是一个非常耗时的过程。

解决这个问题的方法是使用 `include()` 方法。你可以将常用信息放到一个单独的文件中。例如，如果有一组变量需要在网站的每个页面中使用，你可以在一个 PHP 文件中一次性定义它们。然后，在每个页面中，你可以通过引用该文件来 `include()` 它。

## include 和 require 之间的区别：

PHP 中 `include` 和 `require` 语句的主要区别在于：如果发生任何错误，`include` 将产生一条错误消息，然后继续执行页面中的其余代码；而 `require` 将产生一个致命错误并终止执行。

`require()` 函数会抛出一个错误（`E_COMPILE_ERROR`）并停止脚本。

`include()` 函数会抛出一个警告（`E_WARNING`），但脚本将继续执行。

## **require_once()**

当代码的结果是必需的，但后续的包含会抛出错误时，`require_once()` 函数非常有用。这适用于带有函数的脚本。如果这样的脚本被多次包含，就会抛出错误，因为函数不能被重新声明。

## **include_once()**

`include_once()` 函数在包含远程文件并且不希望因 HTTP 开销而多次包含它们的情况下非常有用。这在支付网关以及电子商务网站的处理过程中也很有用。

### 示例

```html
<html>

<head>

<title>My Web page</title>

</head>

<body>

<div class="header">

<?php
include_once "menu.php";
?>
</div>
<div class="footer">
<?php
include_once "menu.php";
?>
</div>
</body>
</html>
```

在此示例中，当你尝试重新调用文件“menu.php”时，会看到一个警告。

## PHP 错误——故障排查

Fatal error: Call to undefined function xyz() in localhost/test.php on line 2

解决方案：这意味着当前页面需要的 PHP 函数找不到。请仔细检查所有包含的文件是否已上传或替换，以及是否遵循了安装说明。

PHP Warning: include(abc.php): failed to open stream: No such file or directory in localhost/test.php on line 2

解决方案：此警告告诉你，一个包含文件（使用 PHP 的 `include` 语法包含的文件）未找到。如果你收到有关无法打开文件的警告或错误消息，请检查错误消息中提到的文件是否存在，以及你的路径是否正确。

Warning: move_uploaded_file(upload/logo.jpg) [function.move-uploaded-file]: failed to open stream: Permission denied in localhost/upload.php on line 32

**解决方案：** 此警告是一个权限错误的示例。脚本试图将文件上传到一个目录，但该目录没有足够的权限让文件移动进去。

## 备注

## 处理图像和其他上传文件

处理上传文档是任何服务端编程语言的主要部分。上传 PDF 文档、图像、视频和其他文件是通过 HTML 中的 `enctype="multipart/form-data"` 属性来处理的。我们需要创建一个 HTML 表单，允许你选择要上传的文件。

注意：请确保你的表单 method 类型为 `post`，并且 `enctype="multipart/form-data"`，这样才能成功处理文件上传过程。

### HTML 代码

```html
<form enctype="multipart/form-data" action="process.php" method="POST">
Choose File : <input name="myfile" type="file" />
<input type="submit" value="Upload" />
</form>
```

现在创建一个 PHP 文件 `process.php` 来处理文件信息。请注意，你不能在此页面上直接查看上传的文件。我们将使用 `$_FILES` 超全局变量来获取上传文件的信息。

示例：`$_FILES['myfile']['name'];`

`$_FILES[][]` 是一个关联二维数组，保存与上传文件相关的所有信息。第一个 `[]` 包含文件字段的名称（`myfile`），第二个 `[]` 包含预定义属性（`name`）。

下面还有一些其他预定义属性：

- `$_FILES['file']['tmp_name']` – 上传文件在 Web 服务器临时目录中的位置。

- `$_FILES['file']['name']` – 上传文件的实际名称。

- `$_FILES['file']['size']` – 上传文件的大小（以字节为单位）。

- `$_FILES['file']['type']` – 上传文件的 MIME 类型。

- `$_FILES['file']['error']` – 与文件相关的错误代码。

那么让我们来看一个例子：

```php
<?php
// get the uploaded file name
$filename = $_FILES['myfile']['name'];

// get the file type
$filetype = $_FILES['myfile']['type'];

// get the file size (in bytes)
$filesize = $_FILES['myfile']['size'];
echo "<h2>Uploaded file information</h2>";
echo "File Name : ".$filename;
echo "<br> File Size : ".$filesize;
echo "<br>File Type : ".$filetype;
?>
```

文件成功上传后，你可以根据需要添加一些验证，使其更有用：

```php
<?php
// get the uploaded file name
$filename = $_FILES['myfile']['name'];
// get the file type
$filetype = $_FILES['myfile']['type'];
// get the file size (in bytes)
$filesize = $_FILES['myfile']['size'];
// You may put your validations here i.e restrict file size
if($filesize >= 1000000)
{
    echo "File is too Large, Maximum file size should be 1 MB";
    exit;
}
// Validation to check if uploaded file is an Image
if($filetype != "image/jpeg" && $filetype != "image/png" &&
   $filetype != "image/JPEG")
{
    echo "Only Images allowed, Kindly upload valid Image.";
    exit;
}
else
{
    // create a folder – upload (in the same location where you have this PHP file) to move uploaded image from your local computer to server
    $target = "upload/";
    $target = $target . basename( $_FILES['myfile']['name'] );
    move_uploaded_file($_FILES['myfile']['tmp_name'], $target);
    echo "Image Uploaded Successfully";
}
?>
```

你需要将上传的图像保存到 Web 服务器上的文件夹中，这意味着你需要一个 Web 服务器可写的目录。要使文件夹对 Web 服务器可写，你可以使用 FTP 客户端来完成。

要将上传的图像写入目标文件夹，可以使用 `move_uploaded_file` 函数。这个 PHP 函数会获取图像并将其移动到指定位置。

**错误消息：** PHP 通过 HTML 表单上传文件时会返回一个错误代码。我们可以通过 PHP 获取文件上传过程中的错误代码。下面解释一些错误消息：

- `UPLOAD_ERR_OK` – 没有错误，文件上传成功。

- `UPLOAD_ERR_INI_SIZE` – 上传的文件超过了 `php.ini` 文件中 `upload_max_filesize` 指定的值。

- `UPLOAD_ERR_FORM_SIZE` – 上传的文件超过了 HTML 表单中指定的 `MAX_FILE_SIZE` 指令。

- `UPLOAD_ERR_PARTIAL` – 文件仅被部分上传，或者上传过程被中断。

- `UPLOAD_ERR_NO_FILE` – 用户没有上传任何文件。当用户尝试上传文件但 PHP 没有收到任何内容时会发生。

- `UPLOAD_ERR_NO_TMP_DIR` – 缺少临时文件夹。

- `UPLOAD_ERR_CANT_WRITE` – 无法将文件写入磁盘。

- `UPLOAD_ERR_EXTENSION` – 某个 PHP 扩展停止了文件上传过程。

### 示例
