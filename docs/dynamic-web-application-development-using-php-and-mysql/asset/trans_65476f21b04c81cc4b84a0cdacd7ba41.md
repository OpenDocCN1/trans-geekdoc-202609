
原始文件名：

```
if (move_uploaded_file($strFilename, "uploaded/$strRealname") )
```

如果由于某种原因文件无法移动，则会显示错误消息：

```
else
    echo "<p>Error: File not moved successfully!</p>";
```

好吧，那么我们在复制文件后如何访问它呢？好吧，我们可以浏览到其位置并查看文件，或者我们可以编写一个小型脚本来访问上传的文件。

> **NOTE** 如果您上传到 UNIX 计算机，则您的上传路径可能与上面显示的不同。

## 查看上传的文件

为了让我们能够查看已上传的文件，我们首先将修改之前的 PHP 脚本，以便除了将文件移动到“uploaded”子目录外，还在简单的文本文件中记录已上传的文件名。我们将在查看脚本中使用此信息。以下是修改后的脚本：

```
<?php
// File: example12-21.php

$strFilename = $_FILES['strFile']['tmp_name'];
$strRealname = $_FILES['strFile']['name'];

if (is_uploaded_file($strFilename) )
    if (move_uploaded_file($strFilename, "uploaded/$strRealname") ) {
    echo "<p>File uploaded successfully</p>";
    $fileTextFile = fopen ("uploadedfiles.txt",'a');
    fwrite($fileTextFile, "$strRealname\r\n");
    if (!fclose($fileTextFile) )
        echo "<p>Error closing file!</p>";
    }
else
    echo "<p>Error: File not moved successfully!</p>";
else
    echo "<p>Error: Not an uploaded file!</p>";
?>
```

您需要更改脚本“example12-19.htm”，以便表单调用此脚本（“example12-21.php”），以便正确工作。

脚本的修改全部在检查文件是否已成功移动的“if”结构内。打开一个文件进行追加，并在关闭文件之前写入上传的文件名：

```
$fileTextFile = fopen ("uploadedfiles.txt",'a');
fwrite($fileTextFile, "$strRealname\r\n");
if (!fclose($fileTextFile) )
    echo "<p>Error closing file!</p>";
```

该脚本现在为我们提供了已上传文件列表。我们现在可以编写一个简单的脚本来查看和浏览这些文件：

```
<?php
// File: example12-22.php

$fileTextFile = fopen ("uploadedfiles.txt",'r');

echo "<h1>The following files have been uploaded</h1>";
while (!feof($fileTextFile) ) {
    $strLine = fgets($fileTextFile);
    echo "<p><a href='uploaded/$strLine'>$strLine</a></p>";
}

if (!fclose($fileTextFile) )
    echo "<p>Error closing file!</p>";
?>
```

该脚本非常简单。它打开“uploadedfiles.txt”文件：

```
$fileTextFile = fopen ("uploadedfiles.txt",'r');
```

使用“while”结构，它显示所有已上传的文件：

```
while (!feof($fileTextFile) ) {
    $strLine = fgets($fileTextFile);
    echo "<p><a href='uploaded/$strLine'>$strLine</a></p>";
}
```

上述脚本的输出看起来与图 12.15 所示类似。尝试点击上传的文件链接，看看会发生什么。

## 图 12.15 文件上传查看器

![](img/b2471264f405d17994ef173e4b9cec92_384_0.png)

## 12.5 给用户发送电子邮件

电子邮件已成为电子通信的关键方式之一。PHP 包含电子邮件创建和交互的功能支持。在本节中，我们介绍 mail() 函数，该函数在 PHP 脚本中被广泛使用，以便同时向一个或多个收件人发送纯文本、HTML 和 mime 类型消息。电子邮件可以被视为数据流（如果您愿意，也可以是文件），这就是为什么我们将它们包含在本课中的原因。

除了演示如何以基本形式使用此函数外，我们还将研究 mail() 函数的一些更高级功能。

使用 PHP 发送电子邮件非常简单。为此，我们使用 mail() 函数。这使我们能够将消息从源邮件服务器传输到同一台或另一台邮件服务器上的目标电子邮件帐户。为了成功使用此函数，您必须能够访问邮件服务器。

要使用的邮件客户端在 php.ini 文件中定义。默认情况下，php.ini 文件中适用于邮件的部分如下：

```
[mail function]
; For Win32 only.
SMTP = localhost
```

您的 PHP 服务器是在 UNIX 还是 Windows 环境下运行，决定了您应如何配置此文件。对于 Windows 用户，您必须配置 SMTP 邮件服务器的位置和您的电子邮件地址。如果您拥有 Google 邮件帐户，则您的 SMTP 服务器地址为：

```
smtp.gmail.com
```

如果您拥有英国 Yahoo! 邮件帐户，则为：

```
smtp.mail.yahoo.co.uk
```

将 php.ini 文件更改为将 SMTP 从“localhost”更改为您的 SMTP 邮件服务器并保存文件。

UNIX 用户需要输入其 sendmail 应用程序的位置，通常为“/usr/bin/sendmail”。您应咨询您的服务提供商，以了解您需要为 SMTP 邮件服务器替换默认“localhost”的设置。

## 发送简单的邮件消息

mail() 函数可用于构建简单的邮件消息。mail() 函数的格式如下：

```
mail (to, subject, message, headers)
```

## 图 12.16 一封简单的电子邮件

![](img/b2471264f405d17994ef173e4b9cec92_387_0.png)

然而，仅在消息正文中包含 (X)HTML 元素并不是故事的结束。为了使其工作，我们还需要包含一些额外的头信息，如下所示：

```
$headers = "MIME-Version: 1.0\r\n";
$headers .= "Content-type: text/html; charset=iso-8859-1\r\n";
```

MIME 代表多用途互联网邮件扩展。MIME 扩展了互联网邮件的格式，以允许更复杂的非基于文本的电子邮件。电子邮件客户端需要知道我们使用的是哪个版本的 MIME，因此 MIME 头定义了 MIME 版本。Content-type 头是强制性头，指定消息正文的格式（在本例中为文本和 html）以及使用的字符集。以下脚本举例说明了创建 (X)HTML 电子邮件消息的脚本：

```
<?php
// File: example12-24.php

$strEmail = "simon.stobart@sunderland.ac.uk";
$strSubject = "Sales Figures";
$strMessage = "
<html>
<head>
<style type='text/css'>
body {background-color: white}
tr {color: white;
    background-color: blue}
h1 {color: black}
</style>
</head>

<body>
<div align="center">
<h1>Weekly Sales Figures</h1>
<table width=\"385\">
    <tr>
        <td>Mon</td><td>Tue</td><td>Wed</td><td>Thu</td><td>Fri</td>
    </tr>
    <tr>
<td>£100,000</td><td>£89,000</td><td>£67,000</td><td>£120,400</td><td>
£101,800</td>
    </tr>
</table>
</div>
</body>
</html>
";

$strHeaders = "MIME-Version: 1.0\r\n";
$strHeaders .= "Content-type: text/html; charset=iso-8859-1\r\n";
$strHeaders .= "From: simon.stobart@sunderland.ac.uk\r\n";
$strHeaders .= "Reply-To: simon.stobart@sunderland.ac.uk";
echo "<p>Message sent</p>";
mail($strEmail, $strSubject, $strMessage, $strHeaders);
?>
```

上述脚本首先通过定义电子邮件的收件人和电子邮件主题开始：

```
$strEmail = "simon.stobart@sunderland.ac.uk";
$strSubject = "Sales Figures";
```

消息使用 (X)HTML 元素创建：

```
$strMessage = "
<html>
<head>
<style type='text/css'>
body {background-color: white}
tr {color: white;
    background-color: blue}
h1 {color: black}
</style>
</head>

<body>
<div align="center">
<h1>Weekly Sales Figures</h1>
<table width=\"385\">
    <tr>
        <td>Mon</td><td>Tue</td><td>Wed</td><td>Thu</td><td>Fri</td>
    </tr>
    <tr>
<td>£100,000</td><td>£89,000</td><td>£67,000</td><td>£120,400</td><td>
£101,800</td>
    </tr>
</table>
</div>
</body>
</html>
";
```

接下来，包含特殊的 MIME 头：

```
$strHeaders = "MIME-Version: 1.0\r\n";
$strHeaders .= "Content-type: text/html; charset=iso-8859-1\r\n";
```

其后是 from 和 reply-to 头：

```
$strHeaders .= "From: simon.stobart@sunderland.ac.uk\r\n";
$strHeaders .= "Reply-To: simon.stobart@sunderland.ac.uk";
```

最后，发送消息：

```
mail($strEmail, $strSubject, $strMessage, $strHeaders);
```

上述脚本在网页上生成的输出为：

Message sent

然而，图 12.17 中说明了产生的电子邮件。

## 图 12.17 一封 (X)HTML 电子邮件

![](img/b2471264f405d17994ef173e4b9cec92_389_0.png)
