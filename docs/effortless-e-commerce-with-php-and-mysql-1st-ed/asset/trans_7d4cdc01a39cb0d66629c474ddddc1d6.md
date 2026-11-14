
使用预处理语句进行数据库查询会改变查询值的处理方式，如你将在第12步中看到的。

产品的类别值应来自选择菜单。它需要是一个至少为1的整数。如果不满足这些条件，将向错误数组添加一个错误。与书中其他地方看到的验证例程不同，此时不会对验证后的值进行其他操作。

- 6. 验证价格和库存数量:

```
if (empty($_POST['price']) || !filter_var($_POST['price'], FILTER_VALIDATE_FLOAT) || ($_POST['price'] <= 0)) {
    $add_product_errors['price'] = 'Please enter a valid price!';
}

if (empty($_POST['stock']) || !filter_var($_POST['stock'], FILTER_VALIDATE_INT, array('min_range' => 1))) {
    $add_product_errors['stock'] = 'Please enter the quantity in stock!';
}
```

价格不能为空，且必须是一个不小于或等于零的浮点数（小数）。库存数量必须是一个大于或等于1的整数。如果你想允许管理员添加稍后库存会增加的产品，可以将min_range改为零。

- 7. 验证名称和描述:

```
if (empty($_POST['name'])) {
    $add_product_errors['name'] = 'Please enter the name!';
}
if (empty($_POST['description'])) {
    $add_product_errors['description'] = 'Please enter the description!';
}
```

这两个值不能为空。

由于网站上的图片相对较小，最大尺寸可以合理地限制在100 KB以下。

- 8. 开始验证图像:

```
if (is_uploaded_file($_FILES['image']['tmp_name']) && ($_FILES['image']['error'] == UPLOAD_ERR_OK)) {
    $file = $_FILES['image'];
    $size = ROUND($file['size']/1024);
    if ($size > 512) {
        $add_product_errors['image'] = 'The uploaded file was too large.';
    }
}
```

此代码与第5章中用于验证上传PDF文件的代码类似。图像的最大尺寸为512 KB。

- 9. 验证文件的类型:

```
$allowed_mime = array('image/gif', 'image/pjpeg', 'image/jpeg',
    'image/JPG', 'image/X-PNG', 'image/PNG', 'image/png',
    'image/x-png');
$allowed_extensions = array ('.jpg', '.gif', '.png', 'jpeg');
$image_info = getimagesize($file['tmp_name']); $ext = substr($file['name'], -4);
if ( (!in_array($file['type'], $allowed_mime))
  || (!in_array($image_info['mime'], $allowed_mime) )
  || (!in_array($ext, $allowed_extensions) )
) {
    $add_product_errors['image'] = 'The uploaded file was not of the
    proper type.';
}
```

同样，这与上传PDF的过程类似。首先，定义允许的MIME类型数组。然后，定义允许的扩展名数组。第三，调用getimagesize()函数，它可以作为图像属性的良好服务器端确认。第四，获取上传文件名的最后四个字符，以便与允许的扩展名进行比较。

然后，如果三个条件中有任何一个为假，代码会创建一个错误。第一个条件是浏览器提供的MIME类型适当。第二个条件是服务器提供的MIME类型（来自getimagesize()函数调用）可接受。第三个条件是文件的扩展名在批准列表中。

- 10. 将文件移动到其最终位置:

```
if (array_key_exists('image', $add_product_errors)) {
    $new_name = (string) sha1($file['name'] . uniqid('', true));
    $new_name .= ((substr($ext, 0, 1) != '.' ? '.' : '') . $ext);
    $dest = "./../products/$new_name";
    if (move_uploaded_file($file['tmp_name'], $dest)) {
        $_SESSION['image']['new_name'] = $new_name;
        $_SESSION['image']['file_name'] = $file['name'];
        echo '<h4>The file has been uploaded!</h4>';
    } else {
        trigger_error('The file could not be moved.');
        unlink($file['tmp_name']);
    }
} // End of array_key_exists() IF.
```

如果不存在与图像相关的错误，将为图像创建一个新名称，首先对文件当前名称与唯一ID的组合应用`SHA1()`。这将生成一个40个字符长的随机名称。然后附加现有扩展名。最后，将文件移动到其最终位置，即 **Web根目录**`/products` 文件夹。

图像的新名称和原始文件名都存储在会话中以供以后使用。

- 11. 如果发生文件上传错误，确定错误是什么:

```
} elseif (isset($_SESSION['image'])) {
switch ($_FILES['image']['error']) {
case 1:
case 2:
$add_product_errors['image'] = 'The uploaded file was too
large.';
break;
case 3:
$add_product_errors['image'] = 'The file was only partially
uploaded.';
break;
case 6:
case 7:
case 8:
$add_product_errors['image'] = 'The file could not be
uploaded due to a system error.';
break;
case 4:
default:
$add_product_errors['image'] = 'No file was uploaded.';
break;
} // End of SWITCH.
} // End of $_FILES IF-ELSEIF-ELSE.
```

再次，这与PDF上传脚本中的内容相似。首先，只有当会话中没有已表示的文件时，才会检查`switch`。这是必要的，因为管理员第一次可能正确上传了图像，但在表单中存在另一个错误。在这种情况下，当管理员重新提交表单时，应使用现有的图像上传。

- 12. 如果没有错误，将记录添加到数据库:

```
if (empty($add_product_errors)) {
    $q = 'INSERT INTO non_coffee_products (non_coffee_category_id,
        name, description, image, price, stock) VALUES (?, ?, ?, ?, ?, ?)';
    $stmt = mysqli_prepare($dbc, $q);
    mysqli_stmt_bind_param($stmt, 'isssdi', $_POST['category'],
        $name, $desc, $_SESSION['image']['new_name'], $_POST['price'],
        $_POST['stock']);
    $name = strip_tags($_POST['name']);
    $desc = strip_tags($_POST['description']);
    mysqli_stmt_execute($stmt);
}
```

如第7章所述，要使用预处理语句，第一步是定义查询，使用占位符（问号）代替实际值。然后准备语句。接下来，按类型将占位符绑定到PHP变量。mysqli_stmt_bind_param()函数的第二个参数表示第一个占位符是整数，接下来三个是字符串，第五个是小数，最后一个是另一个整数。

用于查询的四个值直接来自$_POST和$_SESSION。其他两个值将来自局部变量，在应用strip_tags()函数之后。

如果在执行此脚本时遇到问题，可以在准备语句后使用以下行来查看问题是什么：

```
if (!$stmt) echo mysqli_stmt_error($stmt);
```

- 13. 如果查询创建了新记录，打印消息并执行一些清理:

```
if (mysqli_stmt_affected_rows($stmt) == 1) {
    echo '<h4>The product has been added!</h4>';
    $_POST = array();
    $_FILES = array();
    unset($file, $_SESSION['image']);
}
```

如果影响了一行，将打印一条消息，并重置变量（因为表单将再次显示，不应显示先前的值）。

- 14. 如果出现问题，触发错误:

```
} else {
	trigger_error('The product could not be added due to a system error.
	We apologize for any inconvenience.');
	unlink ($dest);
}
```

当由于数据库或查询错误发生问题时，将向管理员显示一条消息并删除上传的文件（以防止死文件杂乱产品目录）。

- 15. 完成错误数组和请求方法条件语句:

```
} // End of $errors IF.
} else { // Clear out the session on a GET request:
unset($_SESSION['image']);
} // End of the submission IF.
```

如果管理员上传了文件但未完整填写表单，然后出于某种原因点击了标题中的链接返回此页面，从而重新开始该过程，则最终取消设置会话变量将适用。

- 16. 包含表单函数脚本:

```
require ('../includes/form_functions.inc.php');
```

create_form_input()函数在此脚本（位于公共includes文件夹）中定义，因此必须在此处包含它。

- 17. 开始表单:

```
?><h3>Add a Non-Coffee Product (a "Goodie")</h3>
<form enctype="multipart/form-data" action=
	"add_other_products.php" method="post" accept-charset="utf-8">
	<input type="hidden" name="MAX_FILE_SIZE" value="524288" />
	<fieldset><legend>Fill out the form to add a non-coffee product to
the catalog. All fields are required.</legend>
```

为了处理文件上传，表单必须使用enctype属性，并且应包含MAX_FILE_SIZE隐藏输入（它向浏览器推荐最大上传文件大小）。该值以字节为单位。

- 18. 创建类别菜单:

```
<div class="field"><label for="category"><strong>Category
	</strong></label><br /><select name="category"<?php
	if (array_key_exists('category', $add_product_errors)) echo '
	class="error"; ?>
```
