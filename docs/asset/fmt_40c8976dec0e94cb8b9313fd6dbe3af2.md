
注意，`htpassword` 可能不在你的路径中：如果是的话，你可能会在 `/usr/local/apache/bin` 目录下找到它。

这种认证很容易设置，但使用 `.htaccess` 文件存在一些问题。

用户名和密码存储在文本文件中。每当浏览器请求受 `.htaccess` 文件保护的文件时，服务器都必须解析 `.htaccess` 文件，然后解析密码文件，尝试匹配用户名和密码。与其使用 `.htaccess` 文件，

你可以在 `httpd.conf` 文件中指定相同的内容——这是 Web 服务器的主配置文件。`.htaccess` 文件在每次请求文件时都会被解析。而 `httpd.conf` 文件仅在服务器初始启动时才解析一次。这种方法速度更快，但意味着如果你想进行更改，就需要停止并重启服务器。

无论你将服务器指令存储在何处，每个请求仍然需要对密码文件进行搜索。这意味着，就像我们看过的扁平文件技术一样，这并不适用于成百上千个用户。

对于许多简单的网站来说，针对文件使用 `mod_auth_basic` 基础身份验证是理想的。它速度快，实现起来相对简单，并允许你使用任何方便的机制为新用户添加数据库条目。你也可以将其与数据库配合使用，但为了获得更大的灵活性以及对页面部分进行细粒度控制的能力，你可以使用 PHP 和 MySQL 实现你自己的身份验证。

## 创建你自己的自定义身份验证

在本章中，你查看了创建自己的身份验证方法，包括一些缺点和折中，而且它们的灵活性不如编写自己的代码。在书的后面，在你学习了会话控制之后，你将能够编写出比本章中折中更少的自定义身份验证。

在第 22 章中，我们将开发一个简单的用户身份验证系统，该系统通过使用会话跟踪页面之间的变量，避免了我们在这里面临的一些问题。

在第 27 章中，我们将这种方法应用于一个真实项目，并查看如何使用它来实现细粒度的身份验证系统。

## 进阶阅读

HTTP 身份验证的细节由 RFC 2617 规定，可以通过 http://www.rfc-editor.org/rfc/rfc2617.txt 获取。

`mod_auth_basic` 的文档（用于控制 Apache 中的基础身份验证）可以在 https://httpd.apache.org/docs/2.4/mod/mod_auth_basic.html 找到。

## 下节

本书的下一节将涵盖一些高级 PHP 技术，包括与文件系统交互、使用会话控制、实现本地化以及其他有用功能。

本页特意留空

## 与文件系统和服务器交互

在第 2 章“存储和检索数据”中，你了解了如何从 Web 服务器上的文件读取数据以及向文件写入数据。本章涵盖了其他允许你与 Web 服务器文件系统交互的 PHP 函数。

本章涵盖的关键主题包括：

- 使用 PHP 上传文件
- 使用目录函数
- 与服务器上的文件进行交互
- 在服务器上执行程序
- 使用服务器环境变量

为了讨论这些函数的用途，我们来看一个示例。考虑一种情况：你希望能够上传图像并包含网站内容中（或者你可能想给自己提供一个比 FTP 或 SCP 更友好的界面）。一种方法是直接通过你网站上的表单上传文件，也许该表单仅限管理员访问。一旦文件被上传，你就可以根据需要使用它们。

在我们深入研究文件系统函数之前，让我们简要查看文件上传是如何工作的。

### 上传文件

PHP 的一个非常有用的功能是支持上传文件。文件不是通过 HTTP 从服务器传到浏览器，而是相反的方向——即从浏览器传到服务器。通常，你通过 HTML 表单接口来实现此配置。示例中使用的见图 17.1。

第 17 章 与文件系统和服务器交互

![](img/654520c37415debd4290b9b4aa2c03f2_411_0.png)

**图 17.1** 用于此文件上传的 HTML 表单其字段和字段类型与普通 HTML 表单不同

如你所见，表单有一个框，用户可以在其中输入文件名，或点击“浏览”（Browse）按钮来浏览本地可用的文件。我们很快就会查看如何实现这一点。

输入文件名后，用户可以点击“发送文件”（Send File），文件将被上传到服务器，那里有一个 PHP 脚本在等待它。

在我们深入研究文件上传示例之前，重要的是，`php.ini` 文件有五个控制 PHP 如何处理文件上传的指令。这些指令的默认值和描述如表 17.1 所示。

**表 17.1** `php.ini` 中的文件上传配置设置

| 指令 | 描述 | 默认值 |
|---|---|---|
| `file_uploads` | 控制是否允许 HTTP 上传。值为 On 或 Off。 | On |
| `upload_tmp_dir` | 指示上传的文件在等待处理时临时存储的目录。如果未设置此值，将使用系统默认值（如 `/tmp`） | NULL |

`upload_max_filesize` 控制允许上传的文件的最大大小。如果文件大于此值，PHP 将改为写入一个 0 字节的占位文件。你可以对大小使用简写符号：K 表示千字节，M 表示兆字节，G 表示吉字节。

`2M`

`post_max_size` 控制 PHP Accept 的 POST 数据的最大大小。此值必须大于 `upload_max_filesize` 指令的值，因为它是所有 POST 数据的大小，包括任何要上传的文件。你也可以对此配置设置像 `upload_max_filesize` 一样使用简写符号。

`8M`

### 文件上传的 HTML

要实现文件上传，你需要一些语法。HTML 所示于列表 17.1。

列表 17.1 上传的 HTML

```html
<!DOCTYPE html>
<html>
<head>
<title>Upload File</title>
</head>
<body>
<h1>Upload File</h1>
<form action="upload.php" method="post" enctype="multipart/form-data">
<label for="file">Select file:</label>
<input type="file" name="file" id="file">
<input type="submit" value="Upload">
</form>
</body>
</html>
```

注意，表单使用了 `enctype="multipart/form-data"` 让服务器知道有一个文件传来。输入元素必须是 `file` 类型。`php.ini` 中的 `upload_max_filesize` 和 `post_max_size` 指令控制可以上传的最大大小。在这里，我们将其设置为 1,000,000 字节（约 1 兆字节）。

在你知道文件在哪里以及它叫什么名字时，你现在可以将其复制到需要的地方。在你的脚本执行之前，临时文件将被删除。因此，你必须移动或重命名该文件如果你想保留它。

在本示例中，你将 PNG 图像文件上传到名为 `/uploads/` 的新目录。
注意，你需要在 Web 服务器的文档根目录下创建一个名为 `uploads` 的文件夹。如果该目录不存在，文件上传将失败。

执行此任务的脚本显示在列表 17.2 中。

# 列表 17.2 `upload.php`—用于从 HTML 表单获取文件的 PHP

```php
<!DOCTYPE html>
<html>
<head>
<title>上传中...</title>
</head>
<body>
<h1>正在上传文件...</h1>
</body>
<?php
if ($_FILES['the_file']['error'] > 0) 
{
    echo 'Problem: ';
    switch ($_FILES['the_file']['error']) 
    {
        case 1:
            echo 'File exceeded upload_max_filesize.';
            break;
        case 2:
            echo 'File exceeded max_file_size.';
            break;
        case 3:
            echo 'File only partially uploaded.';
            break;
        case 4:
            echo 'No file uploaded.\n';
            break;
        case 6:
            echo 'Cannot upload file: No temp directory specified.';
            break;
        case 7:
            echo 'Upload failed: Cannot write to disk.';
            break;
        case 8:
            echo 'A PHP extension blocked the file upload.';
            break;
    }
}
exit;
// 文件是否具有正确的 MIME 类型？
```
