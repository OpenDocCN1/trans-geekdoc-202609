
### 1. HTML 表单结构（片段）

```html
<p><b>Size:</b> <input type="text" name="size" size="20" maxlength="60" value="<?php if (isset($_POST['size'])) echo htmlspecialchars($_POST['size']); ?>" /> (可选)</p>
<p><b>描述：</b> <textarea name="description" cols="40" rows="5"><?php if (isset($_POST['description'])) echo $_POST['description']; ?></textarea> (可选)</p>
</fieldset>
<div align="center"><input type="submit" name="submit" value="提交" /></div>
</form>
</body>
</html>
```

---

### 2. 包含数据库连接脚本并检查表单是否已提交

```php
require ('../../mysqli_connect.php');

if ($_SERVER['REQUEST_METHOD'] == 'POST') {
    $errors = array();
}
```

任何表单验证问题都将被添加到 `$errors` 数组中，该数组在此处初始化。（因为此脚本可能会有多个错误，所以使用了数组；而在 `add_artist.php` 中，一次只能发生单个错误。）

### 3. 验证版画的名称

```php
if (!empty($_POST['print_name'])) {
    $pn = trim($_POST['print_name']);
} else {
    $errors[] = '请输入版画的名称！';
}
```

这是 `prints` 表中的必填字段之一，应检查其是否有值。同样，因为此脚本将使用预处理语句，用于查询的值不需要通过 `mysqli_real_escape_string()` 运行。

如果想要格外小心，可以在此处应用 `strip_tags()`（尽管如果恶意用户已进入管理区域，你将面临更大的问题）。

如果未输入值，则将错误消息添加到 `$errors` 数组中。

### 4. 如果选择了上传图像，则为其创建一个临时名称

```php
if (is_uploaded_file($_FILES['image']['tmp_name'])) {
    $temp = '../../uploads/' . md5($_FILES['image']['name']);
}
```

当介绍使用 PHP 处理文件上传的技术时（见第 11 章 “Web 应用程序开发”），曾提到 `is_uploaded_file()` 函数。如果文件已上传，它返回 `TRUE`，否则返回 `FALSE`。如果文件已上传，脚本将尝试将文件移动到 `uploads` 目录（在第 5 步中）。

这里还发生了一件事：图像不会使用其原始名称存储在服务器上（这可能是一个安全隐患）。相反，图像将使用其关联的版画 ID 进行存储。然而，由于该值尚未知晓（因为版画记录尚未添加到数据库），必须为此文件生成一个临时名称。为此，将 `md5()` 函数（返回 32 字符的哈希值）应用于图像的原始名称。该临时名称连同图像最终目的地的相对路径（相对于此脚本）被赋值给 `$temp`。

您可以在此方面做一些改进。您还可以验证图像是否为正确的大小和类型。为了保持这个已经很繁忙的脚本更易于管理，我在此省略了该部分，但请参阅第 11 章了解要应用的确切代码。

### 5. 将文件移动到其更永久的目标位置

```php
if (move_uploaded_file($_FILES['image']['tmp_name'], $temp)) {
    echo '<p>文件已上传！</p>';
    $i = $_FILES['image']['name'];
}
```

此时，版画图像已被移动到其永久位置（`uploads` 目录），但被赋予了一个临时名称（稍后将重命名）。打印一条消息指示移动成功。最后，`$i` 变量将被赋值为文件的原始名称（供脚本后面使用）。

### 6. 完成图像处理部分

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

第一个 `else` 子句适用于文件无法移动到目标目录的情况。这只有在该目录的路径不正确或未在该目录上设置适当权限时才会发生。无论哪种情况，`$temp` 变量都会被赋予原始上传文件的值，该文件仍驻留在其临时位置。这是必需的，因为未使用的文件稍后将在脚本中被移除。

第二个 `else` 子句适用于未上传文件的情况。由于本网站的目的是销售打印品，实际展示待售商品显得尤为重要。如果你愿意，可以向此错误消息添加更多详细信息或建议，说明应上传何种类型和大小的文件。

### 7. 验证尺寸、价格和描述输入

```php
$s = (!empty($_POST['size'])) ? trim($_POST['size']) : NULL;

if (is_numeric($_POST['price']) && ($_POST['price'] > 0)) {
    $p = (float) $_POST['price'];
} else {
    $errors[] = 'Please enter the print\'s price!';
}

$d = (!empty($_POST['description'])) ? trim($_POST['description']) : NULL;
```

尺寸和描述值是可选的，但价格不是。作为基本的有效性测试，使用 `is_numeric()` 函数确保提交的价格是一个数字（应为小数），并且价格大于 0（以负价格销售产品可不是好事）。如果值合适，为了保险起见，将其类型转换为浮点数。如果未输入价格或输入了无效价格，将向数组添加一条错误消息。

### 8. 验证艺术家

```php
if (isset($_POST['artist']) && filter_var($_POST['artist'], FILTER_VALIDATE_INT, array('min_range' => 1))) {
    $a = $_POST['artist'];
} else { // No artist selected.
    $errors[] = 'Please select the print\'s artist!';
}
```

要输入打印品的艺术家，管理员将使用一个下拉菜单。结果将是一个作为正整数的 `$_POST['artist']` 值。请记住，如果你使用的是不支持 Filter 扩展的旧版 PHP，你将需要改用 `is_numeric()` 函数、类型转换以及检查值是否大于 0 的条件语句。详见第 13 章。

### 9. 将记录插入数据库

```php
if (empty($errors)) {
    $q = 'INSERT INTO prints (artist_id, print_name, price, size, description, image_name) VALUES (?, ?, ?, ?, ?, ?)';
    $stmt = mysqli_prepare($dbc, $q);
    mysqli_stmt_bind_param($stmt, 'isdsss', $a, $pn, $p, $s, $d, $i);
    mysqli_stmt_execute($stmt);
}
```

如果 `$errors` 数组仍为空，则表明所有验证测试均已通过，可以添加打印品。再次使用预处理语句，查询类似于 `INSERT INTO prints (artist_id, print_name, price, size, description, image_name) VALUES (34, 'The Scream', 25.99, NULL, 'This classic...', 'scream.jpg')`。

`mysqli_stmt_bind_param()` 函数指示查询需要六个输入（每个问号对应一个），类型分别为：整数、字符串、双精度（即浮点数）、字符串、字符串和字符串。如有任何疑问，请参阅第 13 章。

### 10. 确认查询结果

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

如果查询影响了一行，则会在 Web 浏览器中打印一条成功消息。接下来，必须检索打印品 ID，以便重命名关联的图像（它目前位于 `uploads` 文件夹中，但使用的是临时名称），使用 `rename()` 函数。该函数将文件的当前名称作为第一个参数，将文件的新名称作为第二个参数。第一个参数的值之前已赋给 `$temp`。第二个参数的值是 `uploads` 目录的路径，加上刚确定的打印品 ID 值。请注意，文件的新名称将不包含文件扩展名。在服务器上查看实际文件时这可能看起来很奇怪，但当文件（即图像）由网站的公共端提供服务时，这并不是问题，你很快就会看到。

最后，清空 `$_POST` 数组，以便其值显示在粘性表单中。

如果查询未影响一行，则可能发生了某些 MySQL 错误，你需要应用标准调试技术来弄清原因。

### 11. 完成条件语句

```php
mysqli_stmt_close($stmt);
} // End of $errors IF.

if (isset($temp) && file_exists($temp) && is_file($temp)) {
    unlink($temp);
}

} // End of the submission IF.
```

第一个右大括号结束对 `$errors` 为空的检查。在这种情况下，应删除服务器上的文件，因为它尚未被永久移动和重命名。

### 12. 打印任何错误

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

发生的所有错误都将位于 `$errors` 数组中。可以使用 `foreach` 循环打印这些错误。错误会在一些 CSS 样式中打印，使其变为粗体和红色。此外，由于粘性表单无法回调选定的文件，会提醒用户重新选择打印图像。（我的著作 *Effortless E-Commerce with PHP and MySQL* 中有一个示例脚本可以回调先前上传的文件，但代码有些棘手。）

### 13. 开始创建 HTML 表单

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

因为此表单将允许用户上传文件，所以必须在 `form` 标签中包含 `enctype` 属性和 `MAX_FILE_SIZE` 隐藏输入。得益于其输入框 `value` 属性中的代码，该表单将具有粘性。请注意，你无法使 `file` 输入类型具有粘性。

以防打印品的名称、尺寸或描述使用了潜在的问题字符，每个值都通过 `htmlspecialchars()` 运行，以免弄乱值（例如，在打印品的尺寸和描述中使用引号的情况）。

### 14. 开始艺术家下拉菜单

**艺术家：**

```html
<select name="artist">
  <option>Select One</option>
```

艺术家下拉菜单将使用此 PHP 代码，根据存储在 `artists` 表中的记录动态生成。

### 15. 检索每一位艺术家

```php
<?php
$q = "SELECT artist_id, CONCAT_WS(' ', first_name, middle_name, last_name) FROM artists ORDER BY last_name, first_name ASC";
$r = mysqli_query($dbc, $q);
if (mysqli_num_rows($r) > 0) {
    while ($row = mysqli_fetch_array($r, MYSQLI_NUM)) {
        echo "<option value=\"$row[0]\"";
        // 检查粘性：
        if (isset($_POST['existing']) && ($_POST['existing'] == $row[0])) echo ' selected="selected"';
        echo ">$row[1]</option>\n";
    }
} else {
    echo '<option>Please add a new artist first.</option>';
}
mysqli_close($dbc); // 关闭数据库连接。
?>
</select>
```

此查询从数据库中检索每位艺术家的姓名和 ID（它未使用预处理语句，因为实际上并不需要）。MySQL `CONCAT_WS()` 函数——即 *concatenate with separator*（使用分隔符连接）的缩写——用于将艺术家的全名作为单个值检索。如果您对查询的语法感到困惑，请在 mysql 客户端或其他界面中运行它以查看结果。

如果数据库中没有现有的艺术家，则该下拉菜单将没有任何选项，因此会显示一条添加艺术家的提示。

由于希望使下拉菜单具有粘性，这段原本基础的代码变得复杂起来。要使任何 `select` 菜单具有粘性，必须向适当的选项添加 `selected="selected"`。因此，`while` 循环中的代码会检查 `$_POST['existing']` 是否已设置，如果已设置，则检查其值是否与正在添加到菜单中的当前艺术家 ID 相同。

### 16. 完成 HTML 表单

```html
```
