
![Image](graphics/circle-f.jpg)如果为打印图像选择了文件并成功上传，结果如下。

**6.** 完成图像处理部分：

```php
} else {
    $errors[] = 'The file could not be moved.';
    $temp = $_FILES['image']['tmp_name'];
}
} else {
    $errors[] = 'No file was uploaded.';
    $temp = NULL;
}
```

第一个 **`else`** 子句适用于文件无法移动到目标目录的情况。这只有在该目录的路径不正确或未在该目录上设置适当权限时才会发生 ![Image](graphics/circle-g.jpg)。无论哪种情况，**`$temp`** 变量都会被赋予原始上传文件的值，该文件仍驻留在其临时位置。这是必需的，因为未使用的文件稍后将在脚本中被移除。

![Image](graphics/19_figure_13_g.jpg)

![Image](graphics/circle-g.jpg)如果 `uploads` 目录不可由 PHP 写入，你将看到类似这样的错误。

第二个 **`else`** 子句适用于未上传文件的情况。由于本网站的目的是销售打印品，实际展示待售商品显得尤为重要。如果你愿意，可以向此错误消息添加更多详细信息或建议，说明应上传何种类型和大小的文件。

**7.** 验证尺寸、价格和描述输入：

```php
$s = (!empty($_POST['size'])) ? trim($_POST['size']) : NULL;

if (is_numeric($_POST['price']) && ($_POST['price'] > 0)) {
    $p = (float) $_POST['price'];
} else {
    $errors[] = 'Please enter the print\'s price!';
}

$d = (!empty($_POST['description'])) ? trim($_POST['description']) : NULL;
```

尺寸和描述值是可选的，但价格不是。作为基本的有效性测试，使用 **`is_numeric()`** 函数确保提交的价格是一个数字（应为小数），并且价格大于 0（以负价格销售产品可不是好事）。如果值合适，为了保险起见，将其类型转换为浮点数。如果未输入价格或输入了无效价格，将向数组添加一条错误消息。

**8.** 验证艺术家：

```php
if (isset($_POST['artist']) && filter_var($_POST['artist'], FILTER_VALIDATE_INT, array('min_range' => 1))) {
    $a = $_POST['artist'];
} else { // No artist selected.
    $errors[] = 'Please select the print\'s artist!';
}
```

要输入打印品的艺术家，管理员将使用一个下拉菜单 ![Image](graphics/circle-h.jpg)。结果将是一个作为正整数的 **`$_POST['artist']`** 值。请记住，如果你使用的是不支持 Filter 扩展的旧版 PHP，你将需要改用 **`is_numeric()`** 函数、类型转换以及检查值是否大于 0 的条件语句。详见 [第 13 章](#ch13.html#ch13)。

![Image](graphics/19_figure_14_h.jpg)

![Image](graphics/circle-h.jpg)管理员可以使用此下拉菜单选择一位现有艺术家。

**9.** 将记录插入数据库：

```php
if (empty($errors)) {
    $q = 'INSERT INTO prints (artist_id, print_name, price, size, description, image_name) VALUES (?, ?, ?, ?, ?, ?)';
    $stmt = mysqli_prepare($dbc, $q);
    mysqli_stmt_bind_param($stmt, 'isdsss', $a, $pn, $p, $s, $d, $i);
    mysqli_stmt_execute($stmt);
```

如果 **`$errors`** 数组仍为空，则表明所有验证测试均已通过，可以添加打印品。再次使用预处理语句，查询类似于 **`INSERT INTO prints (artist_id, print_name, price, size, description, image_name) VALUES (34, 'The Scream', 25.99, NULL, 'This classic...', 'scream.jpg')`**。

**`mysqli_stmt_bind_param()`** 函数指示查询需要六个输入（每个问号对应一个），类型分别为：整数、字符串、双精度（即浮点数）、字符串、字符串和字符串。如有任何疑问，请参阅 [第 13 章](#ch13.html#ch13)。

**10.** 确认查询结果：

```php
if (mysqli_stmt_affected_rows($stmt) == 1) {
    echo '<p>The print has been added.</p>';
    $id = mysqli_stmt_insert_id($stmt);
    rename($temp, "../../uploads/$id");
    $_POST = array();
} else {
    echo '<p style="font-weight: bold; color: #C00">Your submission could not be processed due to a system error.</p>';
}
```

如果查询影响了一行，则会在 Web 浏览器中打印一条成功消息 ![Image](graphics/graycircle-f.jpg)。接下来，必须检索打印品 ID，以便重命名关联的图像（它目前位于 **`uploads`** 文件夹中，但使用的是临时名称），使用 **`rename()`** 函数。该函数将文件的当前名称作为第一个参数，将文件的新名称作为第二个参数。第一个参数的值之前已赋给 **`$temp`**。第二个参数的值是 **`uploads`** 目录的路径，加上刚确定的打印品 ID 值。请注意，文件的新名称将不包含文件扩展名。在服务器上查看实际文件时这可能看起来很奇怪，但当文件（即图像）由网站的公共端提供服务时，这并不是问题，你很快就会看到。

最后，清空 **`$_POST`** 数组，以便其值显示在粘性表单中。

如果查询未影响一行，则可能发生了某些 MySQL 错误，你需要应用标准调试技术来弄清原因。

**11.** 完成条件语句：

```php
mysqli_stmt_close($stmt);
} // End of $errors IF.

if (isset($temp) && file_exists($temp) && is_file($temp)) {
    unlink($temp);
}
} // End of the submission IF.
```

第一个右大括号结束对 **`$errors`** 为空的检查。在这种情况下，应删除服务器上的文件，因为它尚未被永久移动和重命名。

**12.** 打印任何错误：

```php
if (!empty($errors) && is_array($errors)) {
    echo '<h1>Error!</h1>
    <p style="font-weight: bold; color: #C00">The following error(s) occurred:<br />';
    foreach ($errors as $msg) {
        echo " - $msg<br />\n";
    }
    echo 'Please reselect the print image and try again.</p>';
}
?>
```

发生的所有错误都将位于 **`$errors`** 数组中。可以使用 **`foreach`** 循环打印这些错误 ![Image](graphics/circle-i.jpg)。错误会在一些 CSS 样式中打印，使其变为粗体和红色。此外，由于粘性表单无法回调选定的文件，会提醒用户重新选择打印图像。（我的著作 *Effortless E-Commerce with PHP and MySQL* 中有一个示例脚本可以回调先前上传的文件，但代码有些棘手。）

![Image](graphics/19_figure_15_i.jpg)

![Image](graphics/circle-i.jpg)未完整填写的表单将生成多个错误。

**13.** 开始创建 HTML 表单：

```html
<h1>Add a Print</h1>
<form enctype="multipart/form-data" action="add_print.php" method="post">
    <input type="hidden" name="MAX_FILE_SIZE" value="524288" />
    <fieldset><legend>Fill out the form to add a print to the catalog:</legend>
    <p><b>Print Name:</b> <input type="text" name="print_name" size="30" maxlength="60" value="<?php if (isset($_POST['print_name'])) echo htmlspecialchars($_POST['print_name']); ?>" /></p>
    <p><b>Image:</b> <input type="file" name="image" /></p>
</fieldset>
</form>
```

因为此表单将允许用户上传文件，所以必须在 **`form`** 标签中包含 **`enctype`** 属性和 **`MAX_FILE_SIZE`** 隐藏输入。得益于其输入框 **`value`** 属性中的代码，该表单将具有粘性。请注意，你无法使 **`file`** 输入类型具有粘性。

以防打印品的名称、尺寸或描述使用了潜在的问题字符，每个值都通过 **`htmlspecialchars()`** 运行，以免弄乱值（例如，在 ![Image](graphics/graycircle-e.jpg) 中打印品的尺寸和描述中使用引号的情况）。
