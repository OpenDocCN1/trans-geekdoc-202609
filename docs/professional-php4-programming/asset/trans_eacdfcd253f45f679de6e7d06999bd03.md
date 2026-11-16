

## 查看文件

将上传的文件条目添加到 mimeTypes 文件中。上传文件的 MIME 类型存储在 $HTTP_POST_FILES["userfile"]["type"] 变量中。请注意，mimeTypes 文件以追加模式打开：

```
// Add the mime-type of the file in the mimeTypes file
$fp = fopen(getAbsolutePath($currentFolder . "/" . "mimeTypes"), "a");
fwrite($fp, basename($HTTP_POST_FILES["userfile"]["name"]) . ":" .
$HTTP_POST_FILES["userfile"]["type"] . "\n");
```

关闭文件：

```
fclose($fp);
```

包含 main.php 以显示主页面：

```
include_once("main.php");
?>
```

mimeTypes 文件示例：

```
MyPic.jpg:image/jpeg
Welcome.html:text/html
file_chap.doc:application/msword
```

以下 PHP 脚本 viewfile.php 将所选文件的内容返回到浏览器：

```
<?php
include("common.php");
```

检查用户是否已通过身份验证：

```
if (!isSessionAuthenticated()) {
    sendErrorPage("User session has expired. Please login again");
    exit;
}
```

查找文件的 MIME 类型：

```
// Find the mime type of the file
$mimeTypeFile = getAbsolutePath($currentFolder . "/" . "mimeTypes");
if (($fileContent = file($mimeTypeFile)) == null) {
    sendErrorPage("Internal Error: Could not read file " . $mimeTypeFile);
    exit;
}
for($i=0; $i < sizeof($fileContent); $i++) {
    $line = trim($fileContent[$i]);
    list ($fileName, $mimeType) = split(":", $line);
    if ($fileName == $file) {
        $contentType= $mimeType;
        break;
       }
}
```

在响应中发送 Content-Type HTTP 标头。Content-Type HTTP 标头的值是所发送文件的 MIME 类型：

```
if (isset($contentType)) {
    header("Content-Type: ".$contentType);
}
```

获取 $file 的绝对路径。变量 $file 从主页面传递：

```
$fileAbsPath = getAbsolutePath($currentFolder . "/." . $file);
```

打开文件。这里假设，如果文件的 MIME 类型包含 text，则文件包含文本数据，否则包含二进制数据：

```
if (isset($contentType) && strstr($contentType, "text/")) {
    $fp = fopen($fileAbsPath, "r");
} else {
    $fp = fopen($fileAbsPath, "rb");
}
```

将文件内容发送到客户端：

```
fpassthru($fp);
?>
```

## 查看文件夹

以下脚本 viewFolder.php 显示当前文件夹的内容：

```
<?php
include("common.php");
```

检查用户是否已通过身份验证：

```
if (!isSessionAuthenticated()) {
    sendErrorPage("User session has expired!!. Please login again");
    exit;
}
```

设置会话 currentFolder 文件夹；PHP 脚本 main.php 显示会话变量 $currentFolder 指定的文件夹内容：

```
session_register("currentFolder");
// Set the current Folder
if ($fold == ".") {
  // Do nothing
} else if ($fold == "..") {
  $pos = strrpos($currentFolder, "/");
  $currentFolder = substr($currentFolder, 0, $pos);
} else {
  $currentFolder = $currentFolder . "/" . $fold;
}
```

确保 $currentFolder 包含 $username。这样做是为了防止用户访问其他用户的文件夹：

```
// Current folder should always contain $username
if (!strstr(strtoupper($currentFolder), strtoupper($username)) ) {
  sendErrorPage("Error: Cannot access " . $currentFolder);
  exit;
}
```

包含 main.php：

```
include_once("main.php");
?>
```

## 退出登录

以下 PHP 脚本实现退出登录功能：

```
<?php
include("common.php");
```

检查用户是否已通过身份验证：

```
if (!isSessionAuthenticated()) {
  sendErrorPage("User session has expired. Please login again");
  exit;
}
```

销毁会话：

```
session_destroy();
?>
<html>
<head>
<title> Online Storage Application </title>
</head>
<body>
<h1> Thanks <?php echo($username) ?> for using Online Storage Application </h1>
</body>
</html>
```

## 摘要

在本章的第一部分中，我们介绍了 PHP 用于在服务器文件系统中操作文件和目录的内置函数。我们还介绍了 PHP 的另一个有用功能，即从 Web 浏览器上传文件的功能。

在本章的第二部分中，我们继续使用 PHP 中可用的文件和目录函数实现了一个简单的实际示例。我们可以继续开发大量比上面看到的更复杂的应用程序，但基本函数保持不变。使用 PHP 的文件和目录 API 的其他可能应用程序包括：

- **基于 Web 的文件资源管理器**
  为访问服务器本地文件系统提供基于 Web 的界面

- **基于 Web 的电子邮件服务器**
  实现基于 Web 的电子邮件服务器，该服务器使用服务器的文件系统存储电子邮件

- 增强在线存储应用程序以支持用户之间共享文件夹

## 编写 FTP 客户端

FTP 是最古老、最广为人知的 Internet 协议之一。大多数 Web 开发者都熟悉它，作为一种在不同系统之间传输文件的标准方式。本章通过关注 FTP 扩展的实际使用方面，全面介绍了 PHP 的 FTP 支持。

PHP 的 FTP 扩展专注于 FTP 的非交互式使用，并不能替代完整的 FTP 客户端。它非常适合自动化文件传输或构建基于 Web 的 FTP 客户端（有关此类脚本的示例，请参见下文）。

本章分为三个主要部分：

- 第一部分演示了 PHP 的 FTP 扩展的工作原理。旨在让读者快速熟悉该扩展。
- 第二部分侧重于基于 PHP 的 FTP 扩展开发两种不同的应用程序：
  - 一个方便的封装器，用于使用 FTP 函数在服务器之间移动文件
  - 一个简单的基于 Web 的 FTP 客户端
- 第三部分包含三种不同的互补函数参考：
  - 第一个函数参考按用途对 FTP 函数进行分组。组中每个函数列表包含函数原型和简要描述。
  - 第二个参考是按字母顺序排列的命令列表。每个命令都有函数原型、其功能的技术描述和使用示例。
  - 第三个参考将常见 FTP 客户端命令与相应的 PHP FTP 函数对应起来。

### 为 PHP 添加 FTP 支持

自版本 3.0.13 起，PHP 内置了对 FTP 的支持。

在 *nix 操作系统中，默认未启用 FTP 支持。要启用它，必须使用 --enable-ftp 配置标志构建 PHP。PHP 的 Windows 二进制版本中已启用 FTP 支持。

有关 FTP 协议的详细技术信息可在 ftp://ftp.isi.edu/in-notes/rfc959.txt 上查阅。要了解 FTP 的一般概述，请参阅 FTP 客户端和服务器应用程序随附的文档。*nix 操作系统的用户可以尝试以下命令：

- man ftp
- man ftpd

### PHP 的 FTP 扩展

让我们看看 PHP 如何实现 FTP 支持。此脚本匿名连接到 ftp.wrox.com，检索单个文件并关闭连接：

```
<?php
// Connect to FTP server
$ftp_link = ftp_connect('ftp.wrox.com');

// Log in with username and password
ftp_login($ftp_link, 'anonymous', 'foo@bar.com');

// Fetch a file in ASCII mode
ftp_get($ftp_link, 'noscan', 'noscan', FTP_ASCII);

// Close the FTP connection
ftp_quit($ftp_link);
?>
```

此脚本非常简单直接。它不处理错误或意外情况，但确实展示了该扩展的基本用法。

这是一个更完整的脚本，展示了如何使用 FTP 扩展。它侧重于错误处理和调试：

```
<?php
// Put the host and port name into variables as a debugging aid
$host = 'ftp.wrox.com';
$port = 21;
$user = 'anonymous';
$pass = 'zak@fooassociates.com';

// FTP servers may not respond very quickly.
set_time_limit(120);
```

