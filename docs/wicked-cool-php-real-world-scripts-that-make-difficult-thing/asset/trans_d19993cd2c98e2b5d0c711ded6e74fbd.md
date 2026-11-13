

## 骇客脚本

许多脚本按行处理文件数据，而不是将其保存到一个巨大的变量中。这种情况相当常见，尤其是在查看其他程序生成的项目列表时。（“#55：读取逗号分隔文件”第 101 页展示了你可能需要逐行检查的示例。）要做到这一点，只需更改循环内部，如下例所示，该示例打印每个匹配 bob 的行。

```
while ( ! feof($fd) ) {
    $file_data = fgets($fd, 5000);
    if (strstr($file_data, 'bob') != FALSE) {
        print $file_data;
    }
}
```

注意，原脚本中的 .= 追加运算符在此处已更改为 = 赋值运算符。这很微妙，但非常重要。

根据服务器配置，你可能能够使用 fopen() 从 URL 读取数据，例如：

```
$fr = fopen('http://www.yahoo.com', 'r');
```

但是，如果你运行自己的服务器，应该非常小心地允许 fopen() 访问网站外部的文件；一些特定于 PHP 的蠕虫曾以非常恶劣的方式使用 fopen()。基本上，你必须非常小心文件名——确保用户对 fopen() 访问的文件名没有任何控制权！你可以通过将 allow_url_fopen 设置为 false 来关闭 fopen，如“配置设置和 php.ini 文件”第 20 页所示。作为更强大的替代方案，使用 cURL 访问网站，如第 11 章所示。

### 可能出错的情况？

最常见的错误发生在 PHP 没有权限读取文件时。有些文件 PHP 根本不应该查看（例如密码文件），如果你尝试打开其中一个，可能会收到错误消息。检查权限，如“文件权限”第 91 页所示。

这引出了一个更大的问题：永远，绝对不要允许用户在验证用户确实有打开该文件的必要之前打开文件。记住，你不能信任用户将要发送给你的内容。如果你过于依赖用户数据来决定文件名，那么用户完全可能访问你网站上的任何文件。基本上，你需要制定规则，绝对限制对网站文件的目录访问。

你还应验证用户尝试上传的文件中的数据。请参阅“#54：将图片上传到目录”第 97 页，了解如何验证文件类型、位置、大小等的示例。

### #51：创建并写入文件

以下是将字符串写入文件的方法：

```
<?
$file_data = "Hello, file.\nSecond line.";
$fd = fopen('file.txt', 'w');
if (!$fd) {
    echo "Error! Couldn't open/create the file.";
    die;
}
fwrite($fd, $file_data);
fclose($fd);
?>
```

注意，此脚本明确包含换行符。在 Unix 机器上查看时，文件如下所示：

```
Hello, file.
Second line.
```

两行之间的分隔符称为换行符。在 Unix 和 Mac 上，它是 PHP 中双引号内表示的单个字符 \n。但是，在 Windows 和 Mac 上，换行符是 \r\n 序列（“回车，然后换行”）。

因此，如果你确实关心跨平台文本文件可读性，就需要小心一点。Unix 文本文件在 Windows 上显示为一大行，而 Windows 文本文件在每行末尾前都有一个回车符。

如果你愿意，可以明确将换行符表示为 \r\n，但如果你真的担心可移植性，请在 fopen() 的模式末尾加上 t，使模式为 wt。这会在 Windows 上自动将 \n 转换为 \r\n。

### #52：检查文件是否存在

如果你尝试打开不存在的文件，fopen() 会生成错误消息，unlink() 等函数在尝试删除不存在的文件时也是如此。在执行文件操作之前检查文件是否存在，请在测试条件中使用 file_exists() 函数：

```
<?
if (file_exists('file.txt')) {
    print 'OK, file.txt exists.';
}
```

如你所见，如果文件存在，此函数返回 true；如果不存在，则返回 false。

### #53：删除文件

在 Unix 上删除文件，请使用 unlink() 函数：

```
<?
if (unlink("file.txt")) {
    echo "file.txt deleted.";
} else {
    echo "file.txt: delete failed.";
}
?>
```

当然，你需要有适当的权限才能删除文件。但是，这里最大的危险是你可能会删除不想删除的文件。在 Unix 上删除文件后，它就永远消失了；没有未删除或回收站。你可能找回东西的唯一方法是从系统管理员的备份中恢复。

如果你计划让用户操作删除文件，这里也要小心。出于迄今讨论的每个原因以及迄今讨论的每个其他文件操作，这都是危险的。

### #54：将图片上传到目录

每周定期上传 5 或 10 张照片到 Web 服务器是一件麻烦事。当我更新我的 Web 服务器时，我必须将照片保存到硬盘，启动 FTP 客户端，将它们放到网站上，然后将 URL 发送给任何感兴趣的人。有很多图片库程序可以做到这一点，但大多数都非常复杂；我想看看是否可以做一些更简单的事情。

像任何优秀的懒惰程序员一样，我决定自动化这个过程，构建一个相当防傻的系统，允许用户将图片（仅限图片）上传到目录。我想要包含的功能将阻止过大的图片，并生成带有高度和宽度属性的完整 HTML。系统的第一部分是一个名为 upload.html 的脚本，用于获取图片输入数据：

```
<table border="0" cellpadding="10">
<form action="image_process.php" enctype="multipart/form-data" method="post">
<tr>
<td valign=top><strong>Image file:</strong></td>
<td><input name="upfile" type="file"><br>
Image files must be in JPEG, GIF, or PNG format.
</td>
</tr>
<tr>
<td valign="top"><strong>Target directory:</strong></td>
<td>
<select name="location">
<option value="article" selected>Article Images</option>
<option value="banners">Banners/Advertisements</option>
</select>
</td>
</tr>
<tr>
<td valign="top"><strong>Filename (Optional):</strong></td>
<td><input name="newname" type="text" size="64" maxlength="64"></td>
</tr>
<tr>
<td colspan="2">
<div align="center"><input type="submit" value="Upload Image"></div>
</td>
</tr>
</form>
</table>
```

以下是处理此表单的 image_process.php 脚本。我们首先要做的是设置一些配置变量：

```
<?php
/* Configuration */

$root = "/home/www/wcphp/images"; /* Image directory root */
$urlroot = "http://www.example.com/images"; /* URL root */
$max_width = 420; /* Max width */
$max_height = 600; /* Max height */
$overwrite_images = false; /* Allow overwrite */

/* Permitted subdirectories */
$target_dirs = array("article", "banners");

/* End config */
```

将 $root 变量设置为要存储图片的位置，将 $urlroot 设置为从 Web 浏览器查看图片的位置。$target_dirs 中的项目是 $root 下的子目录。这些是允许用户存储图片的唯一位置。

配置完成后，让我们先检查脚本是否可用——这完全取决于 getimagesize() 函数是否可用：

```
if (!function_exists('getimagesize')) {
    die("getimagesize() required.");
}
```

从表单提取字段信息遵循标准流程：

```
/* Get upload information. */
$location = strval($_POST['location']);
$newname = strval($_POST['newname']);
$upfile = $_FILES['upfile']['tmp_name'];
$upfile_name = $_FILES['upfile']['name'];
```

我们需要确定在服务器上将文件命名为什么。在这样做时，我们要确保名称中没有奇怪的字符，并且不会通过添加一堆斜杠 (/) 离开目标目录。你可以使用正则表达式一次性删除任何你不认识的字符。完成后，$newname 包含上传文件的新名称：

```
/* Delete any unwanted characters in the target name. */
if ($newname) {
    $newname = preg_replace('/[^A-Za-z0-9_.-]/', '', $newname);
} else {
    $newname = preg_replace('/[^A-Za-z0-9_.-]/', '', $upfile_name);
}
```

是时候开始验证参数了。首先，我们检查目标子目录是否在有效列表中：

```
/* Validate parameters. */
if (!in_array($location, $target_dirs)) {
    /* Invalid location */
    die("invalid target directory.");
} else {
    $urlroot .= "/$location";
}
```

这里有一个合理性检查，用于确保 PHP 实际上上传了一个文件：

```
if (!$upfile) {
    /* No file */
    die("no file for upload.");
}
```

现在是时候验证数据本身了。我们初始化要接受的文件类型，然后使用 getimagesize() 获取上传图片的尺寸及其类型（$attr 在脚本后面出现）。

```
/* Verify file type. */
$file_types = array(
    "image/jpeg"  => "jpg",
    "image/pjpeg" => "jpg",
    "image/gif"   => "gif",
    "image/png"   => "png",
);
$width = null;
$height = null;

/* Extract MIME type and size for the image. */
$img_info = getimagesize($upfile);
$upfile_type = $img_info["mime"];
list($width, $height, $t, $attr) = $img_info;
```

