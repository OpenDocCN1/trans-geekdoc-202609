
如果文件类型匹配我们允许的上传文件类型，则无需操作。否则，你应该停止脚本并提醒用户他们正尝试上传未许可的文件。

```php
{
  # true - 什么都不做
} else {
  $type = $_FILES['new_image']['type'];
  die ('Only gif, jpg, jpeg, and png files are allowed to be uploaded: ' . $type);
}
```

接下来，我们将通过检查文件大小是否大于 20 KB 来验证文件大小。我通常建议限制文件大小，以防止出现大量错误。$_FILES 超全局变量以字节（Bytes）测量文件大小，大约 1 MB = 1,000 KB。如果你希望是 1 KB = 1024 Bytes。

```php
if($_FILES['new_image']['size'] > 20000) {
  $size = round($_FILES['new_image']['size']/20480,1);
  die ('The file cannot be larger than 20 KB: ' . $size . ' KB');
}
```

在文件上传之前，我们可以进行最后一次检查，查看上传过程中是否有任何错误。如果有错误，我们将停止脚本并提醒用户。

```php
if($_FILES['new_image']['error'] > 0) {
  $error = $_FILES['file']['error'];
  die ('There is an error with your file: ' . $error);
}
```

现在我们可以为图像目录设置变量，并获取服务器上临时文件的名称。图像目录是我们希望放置上传文件夹的地方，相对于  。$_FILES 超全局变量将从服务器上的临时文件夹中检索文件。这是获取文件名的唯一方法，因为 PHP 会将临时文件重命名为唯一的随机字符串，例如 php4H6d3M。一旦脚本结束，临时文件将从服务器上删除。

```php
$image_directory = 'Images';
$temporary_file = $_FILES['new_image']['tmp_name'];
```

接下来：

```php
function findext($filename) {
  $filename = strtolower($filename);
  $ext = explode(".", $filename);
  $ext = end($ext);
  return $ext;
}
```

```php
// php function: 用户可以使用任何有效的 PHP 代码定义自己的函数。
http://us.php.net/manual/en/functions.user-defined.php
```

```php
// php strtolower: 将提供的字符串转为小写。
http://us.php.net/manual/en/function/strtolower.php
```

```php
// php explode: 使用分隔符将字符串拆分为数组。
http://us.php.net/manual/en/function/explode.php
```

```php
// php end: 获取数组的最后一个元素。
http://us.php.net/manual/en/function/end.php
```

```php
// php return: 结束当前函数的执行，并将参数作为函数的值返回。
http://us.php.net/manual/en/function/return.php
```

现在我们有一个可以获取扩展名的函数，我们可以定义一个变量来创建最终的目标路径和名称，该名称将插入到记录的 URL 字段中。将之前定义的 $image_directory 路径、来自 URL 的 id 值、用于扩展名的点，以及通过 findext 函数从上传的文件获取扩展名结合。

```php
$destination_file = $image_directory . $_REQUEST['id'] . "." . findext($_FILES['new_image']['name']);
```

现在我们拥有了移动临时文件、重命名文件和更新数据库所需的所有部分。使用 PHP move_uploaded_file 方法并插入上面定义的 $temporary_file 和 $destination_file 变量，如果 $move 变量成功，我们可以更新数据库并设置 URL 字段。否则，我们应该提醒用户发生了错误。

```php
$move = move_uploaded_file($temporary_file, $destination_file);
if ($move) {
  $url = $destination_file;
  $insert = $fm->newEdit('Demo php', $_REQUEST['id']);
  $insert->addField('URL', $url);
  $insert->execute();
} else {
  die('There was an error moving the file');
}
```

# move_uploaded_file: 将上传的文件移动到新位置。
http://us.php.net/manual/en/function.move-uploaded-file.php

接下来，我们要根据记录 ID 获取选定的记录。然后我们可以为表单中的显示定义几个变量。$id 用于表单中的隐藏值，将记录 ID 传递到数据库以查找并显示正确的记录。$url 用于通过 $path 变量从 URL 字段显示上传的图像，该变量将文本字段中的路径转换为显示图像源的正确 HTML 代码。

```php
$record = $fm->getRecord('Demo php', $_REQUEST['id']);
$id = $record->getRecordId();
$url = $record->getField('URL');
if ($url == "") {
  $path = "";
} else {
  $path = '<img src="' . $url . '/>';
}
```

最后，我们可以创建一个 HTML 表单让用户上传并查看上传的图像。此表单与我们目前为止处理过的其他表单的区别在于 enctype 是 "multipart/form-data"。这允许用户上传文件而不是文本。与之前一样，我们将记录 ID 作为隐藏值提供。一旦文件上传，我们可以为用户显示图像以及目标路径，以便他们知道文件去了哪里以及名称是什么。这部分仅用于您的开发目的。如果是用于公共生产网站，您绝不应该包含文件名和路径。最后，一旦用户对他们的上传满意，他们可以点击链接返回记录列表。

```html
<html>
<head>
  <title>Upload Image and Validate</title>
</head>
<body>
<form action="Upload.php" method="post" enctype="multipart/form-data">
  <input type="hidden" name="id" value="<?php echo $id; ?> />
  Upload image: <input name="new_image" type="file" />
  <input type="submit" name="upload" value="Upload" />
</form>
```

```php
<?php echo $path; ?>
<?php echo $destination_file; ?>
<a href="DisplayUpload.php">Click here to go back to the list view.</a>
</body>
</html>
```

# # 上传图像并验证

上传图像：[选择文件] 未选择文件 [上传]

![](5a2cfda68d42ed65f1850276e49ec_155_0.png)点击此处返回记录列表

图 7-32：Upload.php 页面。

# 第 12 节：显示外部存储的容器字段

**目标**：在本节中，你将学习如何使用 ContainerBridge.php 文件显示在外部存储图像或文件的容器字段内容。这是 FileMaker12 数据库的一个新功能。getContainerDataURL 方法是 FileMaker 12 API 中的唯一方法。此新方法提供了一些机会，无需将文件存储在服务器上即可减小数据库，同时也允许 FileMaker 用户将文件上传到容器字段，而无需使用专门的页面或 Web服务器。

在测试此新的 getContainerDataURL 方法时，我发现它对图像效果良好。然而，显示文件（如 PDF、mp3、电影等）表现出严重的跨浏览器问题。糟糕的是 Firefox 显示了 Web 页面的原始源代码！通常你会使用 embed 或 object 标签来显示文件。这些在此方法中完全不起作用。替代标签是 iframe，它适用于大多数浏览器。Firefox 用户需要安装 PDF 插件和 Adobe Acrobat Reader 10 或更高版本。由于你无法控制用户机器上安装了哪些浏览器和插件，显示文件的最佳方法仍然是将文件存储在服务器上，并使用带有文件路径的文本字段。

