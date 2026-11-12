

```
<?php
print date("l, F dS, Y \\a\\t h:i:s A T");
?>
</body></html>
```

此文件使用 date 函数来格式化当前日期。字符串中的每个字母都代表不同的日期格式；您可以在 www.php.net/date 查看这些字母及其格式的列表。

关于这个日期字符串，我只想补充一点，涉及奇怪的 \a\t。如果你有一个字母是格式说明符，但希望该字母原样出现，则在其前面加上反斜杠。因为 a 是格式说明符，而我希望字母 a 出现，所以我使用 \a。字母 t 也是格式说明符，但 \t 是一个制表符。要仅打印一个 t，我使用两个反斜杠。因此 \a\\t 会打印出这个令人愉快的小词 at。

前面的代码生成服务器端代码（这就是我加入 T 的原因，它用于打印时区），如果客户端位于不同的时区，而您希望页面显示本地时间，这可能会成为一个问题。解决此问题的方法是使用客户端语言（例如 JavaScript），完全不使用 PHP。下面是一个使用 JavaScript 打印本地时间的 .html 文件：

```
<html><head><title>Welcome</title></head>
<body>
Welcome to my Web page!
It is
<SCRIPT LANGUAGE="JavaScript" TYPE="text/javascript">
document.write(Date())
</SCRIPT>
</body></html>
```

## 动态生成样式表

样式表很有趣，可以为网页添加比普通旧式 HTML 更花哨的格式。样式表使您可以指定文本大小、颜色、字体、边框、阴影以及各种其他内容。大多数人喜欢将样式表放在单独的文件中，然后让每个网页连接到该样式表。这样，每当添加新网页时，您就不需要重新输入所有样式信息。如果要更改某个样式，只需在一处进行修改即可。

将 PHP 添加到网站的妙处在于，您可以拥有多个样式表，然后动态选择要使用的样式表。您可以让用户通过指定用户名登录，然后在 MySQL 数据库中查找用户偏好的样式表。或者，您可以根据季节更改样式表（例如，秋季使用黄色和棕色）。

下面是一个基于时间演示两个不同样式表的单个 .php 文件：

```
<html><head><title>Changing Styles</title>
<style type="text/css">
<!--
<?php
if (time() % 2 == 0) {
    print 'body { font-family: Georgia, '.
        '"Times New Roman", Times, serif; '.
        'font-size: 14px; font-weight: bold; '.
        'color: #000009)';
}
else {
    print 'body { font-family: '.
        'Arial, Helvetica, sans-serif; '.
        'font-size: 16px; font-weight: bold; '.
        'color: #006666}';
}
?>
-->
</style>
<body bgcolor="#FFFFFF" text="#000000">
This is some basic text!
</body></html>
```

此文件根据当前 Unix 时间为正文文本选择样式。（不过，我建议让用户对样式有一定的决定权。）我将样式放在同一个 .php 文件中；如果您希望这些样式在整个站点中都可用，只需将它们放在自己的 .php 文件中，然后 include 或 require 该文件。

如果您亲自尝试此示例，请记住，程序将根据当前时间（以秒计）是偶数还是奇数来选择样式表。因此，在看到更改之前，您可能需要刷新页面几次。

## 允许文件上传

某些网站允许用户上传文件。一个很好的示例是 Web 电子邮件服务，它允许用户将文件附加到发出的电子邮件中。

要处理上传，您需要在 HTML 中创建一个表单，并创建一个单独的 .php 文件来接收上传的文件。下面是一个示例 .html 文件：

```
<html><head><title>File Upload Form</title></head>
<body>
<form enctype="multipart/form-data"
action="upload2.php" method="post">
<input type="hidden" name="MAX_FILE_SIZE" value="30000">
Filename: <input name="filename1" type="file"><br>
<input type="submit" value="Submit">
</form>
</body></html>
```

两个关键部分是 form 标签中的 enctype 参数和文件输入框。enctype 参数及其值 "multipart/form-data" 用于告诉浏览器发送文件。type 为 file 的输入框会在浏览器中显示一个文本框和一个浏览按钮。浏览按钮会打开一个“打开文件”对话框，当用户选择文件时，文件名会出现在文本框中。

您可以通过拥有多个文件类型表单对象来支持多文件上传；只需确保为每个对象赋予不同的 name 值。请注意，我在前面示例中提供的 name 值是 filename1；您可以将其他对象命名为 filename2、filename3 等等。

![](img/3f967ab8a8fddc723173059f56621648_508_0.png)

名为 MAX_FILE_SIZE 的隐藏表单对象告诉浏览器不要上传大于指定字节数的文件（本例为 30,000 字节）。（不过，有人报告过浏览器忽略此设置的情况，因此在 PHP 代码中，您可能需要再次检查接收到的文件大小。）

在接收端，您的 .php 文件会获取一个名为 $_FILES 的数组，其中包含有关上传文件的信息（但不包含文件本身）。$_FILES 数组中每个上传的文件都有一个条目，键是 HTML 表单中文件类型输入框使用的名称。（因此，如果文件来自前面的 .html 文件示例，$_FILES 数组将有一个键，即包含 filename1 的字符串。）数组中每个元素的值本身也是一个数组。下面是处理上传的 .php 文件：

```
<?php
$uploads_dir = '/home/me/uploads';
foreach ($_FILES as $myfile) {
$filename = $myfile['name'];
switch ($myfile['error']) {
case UPLOAD_ERR_NO_FILE:
    continue 2; // continue for loop
case UPLOAD_ERR_INI_SIZE:
case UPLOAD_ERR_FORM_SIZE:
    print "Sorry, $filename ".
    "is too big.<p>";
    continue 2;
case UPLOAD_ERR_PARTIAL:
    print "The upload of file ".
    "$filename was broken. ".
    "Please try again!<p>";
    continue 2;
}
print "Thank you for the file $filename.";
print "This file is of type ".
$myfile['type']."<br>";
move_uploaded_file(
    $myfile['tmp_name'],
    $uploads_dir.$myfile['name']);
}
?>
```

下面是对这段代码的简要介绍：

- foreach 循环针对每个上传的文件运行。
- $myfile 变量（在循环头中指定）包含每个文件的信息。
- $myfile['name'] 是文件名。
- 如果出现问题，$myfile['error'] 将设置为 switch 语句中列出的四个值之一。
- $myfile['type'] 是文件的 MIME 类型。（例如，JPEG 图像的此值将为 "image/pjpeg"。）
- $myfile['tmp_name'] 是 PHP 存储上传文件的完整路径和文件名。通常，文件将存储在临时目录中；因此，您会希望像我在前面示例中使用 move_uploaded_file 函数那样移动文件。

![](img/3f967ab8a8fddc723173059f56621648_509_0.png)

在前面的代码中，我使用了 UPLOAD_ERR_NO_FILE、UPLOAD_ERR_INI_SIZE、UPLOAD_ERR_FORM_SIZE 和 UPLOAD_ERR_PARTIAL 常量，它们是 PHP 语言内置的。但是，它们仅从 PHP 版本 4.2 开始出现。如果您使用的是更早的版本，则需要改用数字。将 UPLOAD_ERR_INI_SIZE 替换为数字 1；UPLOAD_ERR_FORM_SIZE 替换为数字 2；UPLOAD_ERR_PARTIAL 替换为数字 3；UPLOAD_ERR_NO_FILE 替换为数字 4。（要小心——我在前面的示例中并没有按数字顺序排列这些常量；顺序将是 4、1、2、3。）

在此示例中，我使用了一种奇怪的结构，即 `continue 2` 结构。这会告诉 PHP 跳出当前循环，然后继续执行下一个外层循环。

此代码中我未演示的 `$myfile` 数组中唯一的值是 `$myfile['size']`。它包含上传文件的大小。

使用这段代码获取上传文件后，我会使用 `move_uploaded_file` 函数将文件从临时目录移动到我的上传目录。请务必使用此函数，而不是标准的 `copy` 函数，因为此函数内置了各种入侵保护。

如果您使用的是早于 4.1.0 的 PHP 版本，则无法使用 `$_FILES` 变量。请改用 `$HTTP_POST_FILES`。但是，在使用之前，您需要像这样将其作为全局变量访问：

```
global $HTTP_POST_FILES;
```

## 在适当时使用 POST

使用 `GET` 方法将数据发送回 Web 服务器的 HTML 表单会将数据添加到 URL 中。这可能不是发送以下类型信息的最佳方法：

- **密码或其他敏感数据：** 如果用户输入密码，密码会通过 URL 发送，因此站在旁边的任何人都能看到。任何人都可以查看地址框的历史记录或下拉列表，从而看到 URL 中的数据并获取密码。
- **大量数据：** 您可能有太大而无法放入 URL 的数据。如果表单中有一个允许输入大量文本的编辑框（例如典型 Web 邮件系统中看到的那种），则不能使用 `GET` 方式发送数据。

在这些情况下，`POST` 方法效果更好。切换到 `POST` 方式发送数据很容易；您只需在 HTML `form` 标签中指定 `POST` 方法，如下所示：

```
<form name="form1" method="post" action="welcome.php">
```

在 PHP 端，接收文件（本例中为 `welcome.php`）可以使用 `$_POST` 数组而不是 `$_GET` 数组来提取数据，如下所示：

```
$password = $_POST['password'];
```

