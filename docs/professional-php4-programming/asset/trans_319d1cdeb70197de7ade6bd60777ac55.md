

一旦打开了目录，就可以使用`readdir()`函数读取其内容。`readdir()`函数返回目录中下一个条目的名称。如果目录中没有更多条目，或者目录句柄无效，则该函数返回 false。

除了文件和子文件夹外，每个目录包含两个特殊条目"."和".."。"."条目引用当前目录，".."引用父目录。

当前目录可以通过打开"."来打开：

```
$dir = opendir(".")
```

读取完目录内容后，应关闭它并释放与其关联的所有资源：

```
void closedir($dir)
```

以下代码删除 temp/ 目录中最近十天未被访问的文件：

```
<html>
<head></head>
<body>
<?php
function cleanTemporaryFiles($directory)
{
    $dir = opendir($directory);
    while (($file = readdir($dir))) {
        if (is_file($directory . "/" . $file)) {
            $accessTime = fileatime($directory . "/" . $file);
            $time = time();
            if (($time - $accessTime) > 10*24*60*60) {
                if (unlink($directory . "/" . $file)) {
                    printf("File %s is removed from %s directory <br>\n",
                        $file, $directory);
                }
            }
        } else if (is_dir($directory . "/" . $file) &&
            ($file != ".") && ($file != "..")) {
            cleanTemporaryFiles($directory . "/" . $file);
        }
    }
    closedir($dir);
}
cleanTemporaryFiles("c:/temp");
?>
</body>
</html>
```

## 添加和删除目录

```
int mkdir(string directoryname, int mode)
```

mkdir() 函数可用于创建新目录。参数 directoryname 是要创建的目录的路径名。参数 mode 指定 UNIX 目录的访问权限。在 Windows 中，此参数被忽略。mode 条目作为八进制字符串指定，并且应始终以零字符开头。该函数在成功时返回 true，在失败时返回 false。

以下代码创建新目录 C:\temp\test：

```
<?php
if (mkdir("c:/temp/test", "0700")) {
    printf("New directory created");
} else {
    printf("Couldn't create directory");
}
?>
```

```
int rmdir(string dirname)
```

rmdir() 函数可用于删除目录。该函数在成功时返回 true，在失败时返回 false。请注意，如果目录非空，rmdir() 函数将失败。

以下函数删除非空目录：

```
<?php
function removeDirectory($directory)
{
    $dir = opendir($directory);
    while (($file = readdir($dir))) {
        if (is_file($directory . "/" . $file)) {
            unlink($directory . "/" . $file);
        } else if (is_dir($directory . "/" . $file) &&
            ($file != ".") && ($file != "..")) {
            removeDirectory($directory . "/" . $file);
        }
    }
    closedir($dir);
    rmdir($directory);
    printf("Directory %s removed", $directory);
}
?>
```

文件条目"."和".."分别指向当前目录和父目录。不应以这些作为参数调用 removeDirectory() 方法，也就是说，如果您不显式跳过"."和".."，可能会丢失所有数据！

## 从客户端上传文件

浏览器可用于将文件上传到服务器的两种机制：

- 基于 HTTP PUT 方法
- 基于 HTTP POST 方法

HTTP 协议提供三种基本方法 GET、PUT 和 POST 来从 Web 服务器访问信息。

GET 方法用于获取网页。当使用 GET 获取动态页面时，表单变量作为 URL 的一部分传递。浏览器使用 GET 方法随意获取页面是安全的——GET 方法不应在服务器上造成任何永久性更改。某些 Web 服务器对可处理的 URL 长度有限制（大多为 1024），因此不应使用 GET 传递大于此限制的表单数据。

PUT 方法用于更新服务器上的信息。它请求将封装的数据作为请求的 URL 存储在服务器上。PUT 方法主要用于发布页面。

如果请求 URL 会在服务器上造成永久性更改，则使用 POST 方法。例如，在基于 Web 的电子邮件应用程序中删除文件夹。在未获得用户确认的情况下，浏览器不应再次执行 POST 方法。POST 方法将所有表单变量作为请求体的一部分发送。当需要将大量表单数据传递到 URL 时，也会使用 POST 方法。

### 使用 PUT 上传文件

典型的 HTTP PUT 请求如下所示：

```
PUT /path/filename.html HTTP/1.1
```

在这种情况下，客户端希望 Web 服务器将请求内容作为指定 URL（/path/filename.html）存储在 Web 服务器的 URL 命名空间中。默认情况下，Web 服务器不会处理此类请求。相反，它会指定一个脚本来处理此类请求。文件上传的站点特定策略可以在指定的脚本中实现。

例如，在 Apache 中，可以使用 script 指令（存储在 httpd.conf 中）来实现此功能。以下 script 指令表示您希望 CGI 脚本 put.cgi 处理 HTTP PUT 请求：

```
Script PUT /cgi-bin/put.cgi
```

PHP 提供对编写 PUT 处理程序的支持。当 PHP 收到 PUT 请求时，它会将请求内容存储在临时文件中，该文件在请求处理后被删除。临时文件名存储在 $PHP_PUT_FILENAME 变量中，URL 名称存储在 $REQUEST_URI 中。

这个用于处理 PUT 请求的简单 PHP 脚本，将上传的文件复制到 Web 服务器 URL 命名空间中的指定 URL 位置：

```
<?php copy($PHP_PUT_FILENAME, $DOCUMENT_ROOT.$REQUEST_URI); ?>
```

在当前的 PHP 实现中，用于上传文件的 PUT 机制无法正常工作。您可以在 http://www.php.net/bugs.php?id=10383 上监控此错误的状态。

### 使用 POST 上传文件

HTML 表单元素允许用户输入将提交到 Web 服务器的文件名。此功能已在最新版本的 Netscape 和 Microsoft 浏览器中实现。用于提交文件的简单 HTML 表单 (uploadfile.html) 如下所示：

```
<html>
<head>
<title> A Simple Form for Uploading a File </title>
</head>
<body>
<h2> A simple form for uploading a file </h2>
```

表单元素的 enctype 属性设置为 multipart/form-data —— 这是文件上传正常工作所必需的。enctype 属性指定浏览器应使用的编码来对表单参数进行编码。enctype 属性的默认值是 application/x-www-form-urlencoded：

```
<form action="upload.php" method="post" enctype="multipart/form-data">
```

input 元素应为 file 类型：

```
Enter file name: <Input type="file" name="userfile"><br>
<input type="submit"><br>
</form>
</body>
</html>
```

该页面在浏览器中显示为：

![](img/9cf7789dba9b16ef3f8576d5aea89186_280_0.png)

在收到带有 file 类型 input 元素的 HTTP 请求时，PHP 会将上传文件的内容存储在临时文件中。除非在 php.ini 文件的 upload_tmp_dir 指令中指定了其他目录，否则临时文件将在服务器的默认临时目录中创建。可以通过设置环境变量 TMPDIR 更改服务器的默认临时目录。临时文件在请求结束时被删除，因此，如果要保留文件数据以供以后使用，处理请求的 PHP 脚本应复制该文件。

上传文件的详细信息可通过二维全局数组 HTTP_POST_FILES 供 PHP 脚本访问。假设 input 元素（file 类型）的名称为 userfile，则：

- 变量 $HTTP_POST_FILES['userfile']['name'] 包含客户端计算机上文件的原始名称
- 变量 $HTTP_POST_FILES['userfile']['type'] 包含文件的 MIME 类型
- 变量 $HTTP_POST_FILES['userfile']['size'] 包含上传文件的大小（以字节为单位）
- $HTTP_POST_FILES['userfile']['tmp_name'] 包含上传文件在服务器上存储的临时文件名

以下是 PHP 脚本 upload.php，它将上传的文件复制到 temp/ 目录：

```
<html>
<head>
<title>Upload File Example</title>
</head>
<body>
<?php

