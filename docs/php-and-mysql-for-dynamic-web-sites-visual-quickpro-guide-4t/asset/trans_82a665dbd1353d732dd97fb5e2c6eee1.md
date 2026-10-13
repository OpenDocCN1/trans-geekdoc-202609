
这当然正是 `create_window()` JavaScript 函数中链接的 `show_image.php` 所做的事情。但是 `proxy.php` 或 `show_image.php` 是如何工作的呢？答案在于对 HTTP 头部的理解。

HTTP（超文本传输协议）是万维网的核心技术，定义了客户端和服务器通信的方式（用通俗的话说）。当浏览器请求一个网页时，它会收到一系列 HTTP 头部作为响应。这发生在后台；大多数用户完全意识不到这一点。

PHP 内置的 `header()` 函数可用于利用这一协议。最常见的例子将在下一章演示，那时将使用 `header()` 函数将 Web 浏览器从当前页面重定向到另一个页面。在这里，你将用它向 Web 浏览器发送文件。

理论上，`header()` 函数很容易使用。其语法是：

```
header(header string);
```

可能的头部字符串列表相当长，因为头部用于从重定向 Web 浏览器、发送文件、创建 Cookie，到控制页面缓存，以及更多更多功能。从简单的开始，要使用 `header()` 重定向 Web 浏览器，请输入：

```
header('Location: http://www.example.com/page.php');
```

该行将把 Web 浏览器从当前页面发送到另一个 URL。你将在下一章看到这方面的例子。

在下一个将图像文件发送到 Web 浏览器的示例中，使用了三个头部调用。第一个是 `Content-Type`。这是向 Web 浏览器指示即将发送什么类型的数据。`Content-Type` 值与数据的 MIME 类型匹配。此行让浏览器知道它即将接收一个 PDF 文件：

```
header("Content-Type:application/pdf\n");
```

接下来，你可以使用 `Content-Disposition`，它告诉浏览器如何处理数据：

```
header("Content-Disposition: attachment; filename=\"somefile.pdf\"\n");
```

`attachment` 值将提示浏览器下载该文件。另一种选择是使用 `inline`，它告诉浏览器显示数据，前提是浏览器支持。`filename` 属性顾名思义：它告诉浏览器与数据关联的名称。一些浏览器遵循此指令，另一些则不遵循。

![Image](graphics/11_figure_22_b.jpg)

由于 `attachment Content-Disposition` 值，Firefox 提示用户下载文件。

用于下载文件的第三个头部是 `Content-Length`。这是一个以字节为单位的值，对应于要发送的数据量。

```
header("Content-Length: 4096\n");
```

这就是关于使用 `header()` 函数的基础知识。在进入示例之前，请注意，如果脚本使用多个 `header()` 调用，每个调用都应以换行符（`\n`）结尾，如前面的代码片段所示。更重要的是，关于 `header()` 函数必须记住的绝对关键一点是，它必须在向 Web 浏览器发送*任何内容*之前调用。这包括 HTML，甚至是空白字符。如果你的代码有任何 `echo` 或 `print` 语句，PHP 标签外有空行，或包含在调用 `header()` 之前做这些事情的文件，你将看到如下图所示的错误消息。

![Image](graphics/11_figure_23_c.jpg)

*headers already sent*（头部已发送）错误意味着在使用 `header()` 函数之前，Web 浏览器已经接收到了某些内容——HTML、纯文本，甚至是一个空格。

### 使用 header() 函数

**1.** 在文本编辑器或 IDE 中开始一个新的 PHP 文档，命名为 `show_image.php`（**[脚本 11.5](#ch11.html#ch11ex05）**）：

```
<?php # Script 11.5 - show_image.php

$name = FALSE;
```

因为此脚本将使用 `header()` 函数，所以绝对不能向 Web 浏览器发送任何内容——绝对没有任何内容。没有 HTML，甚至没有开头 PHP 标签之前的空行、制表符或空格。

`$name` 变量将用作标志，指示所有验证例程是否已通过。

**2.** 检查图像名称：

```
if (isset($_GET['image'])) {
```

脚本需要在 URL 中接收一个有效的图像名称。这应该由调用此页面的 JavaScript 函数追加到 URL 中（参见 `function.js`，**[脚本 11.3](#ch11.html#ch11ex03)**）。

**3.** 验证图像的扩展名：

```
$ext = strtolower(substr($_GET['image'], -4));

if (($ext == '.jpg') OR ($ext == 'jpeg') OR ($ext == '.png')) {
```

下一个检查是要发送给 Web 浏览器的文件是否具有 `.jpeg`、`.jpg` 或 `.png` 扩展名。这样脚本就不会尝试向用户发送不良内容。例如，如果恶意用户将弹出窗口中的地址从 `http://www.example.com/show_image.php?image=image.png` 改为 `http://www.example.com/show_image.php?image=../../../path/to/something/important`，此条件将捕获并防止该攻击。

**脚本 11.5。** 此脚本从服务器检索图像并使用 HTTP 头部将其发送到浏览器。

```
<?php # Script 11.5 - show_image.php
// This page displays an image.

$name = FALSE; // Flag variable:

// Check for an image name in the URL:
if (isset($_GET['image'])) {

    // Make sure it has an image's
    extension:
    $ext = strtolower(substr($_GET
        ['image'], -4));

    if (($ext == '.jpg') OR ($ext ==
        'jpeg') OR ($ext == '.png')) {

        // Full image path:
        $image = "../uploads/{$_GET['image']}";

        // Check that the image exists and
        is a file:
        if (file_exists($image) &&
            (is_file($image))) {

            // Set the name as this image:
            $name = $_GET['image'];

        } // End of file_exists() IF.

    } // End of $ext IF.

} // End of isset($_GET['image']) IF.

// If there was a problem, use the
default image:
if (!$name) {
    $image = 'images/unavailable.png';
    $name = 'unavailable.png';
}

// Get the image information:
$info = getimagesize($image);
$fs = filesize($image);

// Send the content information:
header("Content-Type: {$info['mime']}\n");
header("Content-Disposition: inline;
    filename=\"$name\"\n");
header("Content-Length: $fs\n");

// Send the file:
readfile($image);
```

为了验证扩展名，`substr()` 函数返回图像名称的最后四个字符（`-4` 实现这一点）。扩展名还通过 `strtolower()` 函数处理，以便 `.PNG` 和 `.png` 被同等对待。然后条件语句检查 `$ext` 是否等于三个允许值中的任意一个。

**4.** 检查图像是否为服务器上的文件：

```
$image = "../uploads/{$_GET['image']}";

if (file_exists($image) && (is_file($image))) {
```

在尝试将图像发送到 Web 浏览器之前，请确保它存在且为文件（而不是目录）。作为安全措施，图像的完整路径被定义为 `../uploads` 和接收到的图像名称的组合。

**5.** 将标志变量的值设置为图像名称：

```
$name = $_GET['image'];
```

一旦图像通过了所有这些测试，`$name` 变量将被赋予图像的值。

**6.** 完成步骤 2、3 和 4 中开始的条件语句：

```
} // End of file_exists() IF.
} // End of $ext IF.
} // End of isset($_GET['image']) IF.
```
