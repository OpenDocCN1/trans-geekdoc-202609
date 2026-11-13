

使用刚刚提取的参数，我们确保图像格式可接受，确定其后缀应该是什么，并确保它不太大：

```
/* Validate type. */
if (!file_types[$ufile_type]) {
    die("image must be in JPEG, GIF, or PNG format.");
} else {
    $file_suffix = $file_types[$ufile_type];
}
/* Validate size. */
if ($width > $max_width || $height > $max_height) {
    die("size $width x $height exceeds maximum $max_width x $max_height.");
}
```

不时，有人会上传带有错误后缀的文件。这通常不是什么大问题，但服务器发送时会搞错 MIME 类型。因为我们现在知道正确的后缀，所以通过切掉任何可能的错误后缀并添加自己的后缀来强制设定该后缀。某人也可能拼错后缀，此步骤也会通过简单追加正确后缀来纠正。例如，foo.jpg 可能变成 foo.jpg.jpg。虽然你也可以尝试纠正这种情况，但你会发现自己在怀疑那些真的应该学会如何打字的用户。在确定上传文件的最终名称后，我们将其完整路径名赋值给 $new_fullpath：

```
/* Force file suffix. */
$newname = preg_replace('/\.(jpe?g|gif|png)$/i', "");
$newname .= $file_suffix;
$new_fullpath = "$root/$location/$newname";
```

有了最终名称后，我们可以在设置为不覆盖模式时验证文件是否已存在：

```
if ((!$overwrite_images) && file_exists($new_fullpath)) {
    die("file exists; will not overwrite.");
}
```

现在是将文件复制到最终位置并确保复制成功的时候了：

```
/* Copy the file into final location. */
if (!copy($ufile, $new_fullpath)) {
    die("copy failed.");
}
```

如果我们走到这一步，说明上传成功了，我们只需打印一些 HTML 来给用户一个链接：

```
$image_url = "$urlroot/$sname";

/* Display status. */
print "HTML for image:</strong><br><textarea cols=\"80\" rows=\"4\">";
print "<img src=\"$image_url\" $attr alt=\"$upfile_name\" border=\"0\"/>;";
print "</textarea><br>";
print '<a href="upload.html">Upload another image?</a>';?>
```

## 使用脚本

此脚本要求 $target_dirs 中的所有目标目录都可由 PHP 写入。此外，你需要 GD 模块，这是一个 PHP 扩展，允许 PHP 分析和创建图像文件。大多数服务器默认已安装它，但如果你的服务器没有，请参阅第 27 页的“#18: 向 PHP 添加扩展”。就这些；你只需将浏览器指向 upload.html，PHP 就会完成其余工作。

## 可能出什么问题？

除了常见的权限问题外，最大的问题是安全性。目前，任何能访问此脚本 URL 的人都可以随意上传任意数量的图片，并可能覆盖你的图片。如果此脚本位于防火墙之外，你可能希望将此脚本与登录功能结合使用，以防止未经授权的访问，如第 116 页的“#63: 简单登录系统”中所示。

## 对脚本进行黑客改造

你可以通过查看 $_FILES['upfile']['size'] 变量来限制任何给定文件的大小。只需加入如下行：

```
if ($_FILES['upfile']['size'] > $max_size) {
	$_fatal_error = "This file is larger than $max_size bytes.";
}
```

注意：你可能还想查看第 25 页的“#13: 防止用户上传大文件”，它展示了如何设置全局上传文件大小限制。

## #55: 读取逗号分隔文件

一项常见的编程任务是将 Excel 电子表格中的数据转换为某种有用的形式，例如 HTML 或 MySQL 表中的行。如果我们都必须使用 Excel (XLS) 格式，那将是一个真正的问题。幸运的是，在 Excel 和 OpenOffice.org 中，你都可以将 Excel 文件导出为 CSV（逗号分隔值）格式。CSV 格式是一种花哨的说法，意思是它是一个文本文件，每行对应一个数据行，行中的字段之间用逗号分隔。它看起来像这样：

| 机场 | 城市 | 活动 |
| --- | --- | --- |
| LON | 伦敦 | 博物馆 |
| PAR | 巴黎 | 餐饮 |
| SLC | 盐湖城 | 滑雪 |

你可能会认为这只不过是抓取行并使用逗号作为分隔符来拆分它们的问题，但你还要担心引号、反斜杠以及格式的其他小细节。不过，大多数语言都有内置功能来处理这些东西，PHP 也不例外。使用内置的 fgetcsv() 函数处理 CSV 文件轻而易举。它的工作方式与 fgets() 类似，只不过它返回一个包含当前行行值的数组，而不是一个字符串。下面是一个非常简单的脚本，用于处理表单 csvfile 字段中上传的 CSV 文件：

```
<table>
<tr>
<th>Field 1</th>
<th>Field 2</th>
<th>Field 3</th>
</tr>
<?php

$fn = $_FILES["csvfile"]["tmp_name"];

$fd = fopen($fn, "r");

while (!feof($fd)) {
    $fields = fgetcsv($fd);
    print "<tr>";
    print "<td>$fields[0]</td><td>$fields[1]</td><td>$fields[2]</td>";
    print "</tr>";
}
fclose($fd);
?>
</table>
```

如你所见，此脚本以 HTML 表格格式打印 CSV 文件的前三列。

有时你会得到一个制表符分隔的文件，而不是 CSV 文件。要读取这样的文件，只需将包含 fgetcsv() 的行改为类似这样的内容：

```
$fields = fgetcsv($fd, 0, "\t");
```

第三个参数是分隔符；确保对 \t 使用双引号。第二个参数是 CSV 文件中行的最大长度。如果你不想要长度限制，请将其设置为 0。

## 8

## 用户和会话跟踪

![](img/19183d2b75bf6b509317c631c0e7b817_118_0.png)

万维网的初始设计只不过是一系列静态页面和媒体。该设计使发布和导航页面变得容易，但当网站开始提供动态内容时，Web 才真正变得有用。其中大部分内容特定于会话——例如，购物车就是会话数据；它通常特定于一个浏览器（或用户）。

跟踪 Web 会话的工具和技术是事后补救和权宜之计——它们碰巧能完成尚算合理的工作。有时事情会搞混乱，你必须小心安全（一如既往），但 PHP 可以为你去除一些复杂性。

## 使用 Cookie 和会话跟踪用户数据

要了解特定用户在你网站上在做什么，你需要存储关于该用户的信息，例如用户名、密码、访问间隔时间、偏好设置等。在 Web 编程中，为此目的的两种流行技术是 Cookie 和会话。

### Cookie

*Cookie* 是你存储在用户计算机上的小块数据。当用户访问你网站上的多个页面时，用户的浏览器会在这些访问中将任何有效的 Cookie 发送回你的服务器。因为在用户不知情的情况下在其计算机上存储任何类型的数据都是潜在的安全风险，你无法直接控制如何存储 Cookie。浏览器（和用户）设定了一些规则，如果你遵循这些规则，浏览器就会接受你的 Cookie，并在正确的情况下将它们发送回去。被接受的 Cookie 被称为已 *设置*。

### 优点

- Cookie 可以存储信息多年。
- Cookie 适合高流量网站所需的分布式、负载均衡 Web 服务器，因为所有数据都在用户的计算机上。

### 缺点

- 你需要小心遵循规则，否则许多浏览器不会接受你的 Cookie，而且它们也不会告诉你拒绝的情况。
- Cookie 的大小受到限制（通常最好不要超过 512Kb）。
- 如果用户愿意，可以轻松删除 Cookie。
- Cookie 通常特定于一台计算机上的一个用户。如果用户切换到另一台计算机，他通常不会使用任何旧的 Cookie。

### 会话

*会话* 由唯一会话 ID 和服务器上的某种存储机制组成。因为数据在你的服务器上，用户没有机会操纵它。

### 优点

- 尽管大多数会话通过在 Cookie 中设置会话 ID 来工作，但 PHP 和其他 Web 编程系统有无需 Cookie 即可使会话工作的方法。因此，此方法几乎总是有效。
- 你可以存储任意数量的会话数据。
- 用户通常无法查看或编辑会话数据，即使他们这样做，你也能控制该编辑过程。

