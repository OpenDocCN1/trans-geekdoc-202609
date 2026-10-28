

在第 4 部分中，如果高度比或宽度比大于 1，则说明原始图像大于最大高度或最大宽度。因此，代码会调整原始图像的大小，使其符合指定的最大高度或最大宽度。为此，代码首先获取两个比值中较大的一个。然后，它使用该比值计算新图像的新高度和新宽度，并创建一个该高度和宽度的新的真彩色图像。

创建新图像后，这段代码会为 GIF 或 PNG 图像设置透明性。因此，如果用户上传的 GIF 或 PNG 图像使用了透明效果，所创建的新图像也会使用透明效果。然后，这段代码将原始图像复制到新路径，从而创建并调整新图像的大小。接下来，这段代码将新图像写入指定的文件路径。最后，`if` 子句中的最后一行释放新图像所占用的内存。

如果高度比和宽度比都小于 1，则执行 `if` 子句后面的 `else` 子句，这意味着原始图像小于最大高度或最大宽度。此时，代码不会调整原始图像的大小，而是将原始图像的副本写入新路径。最后，在 `if` 语句结束后，使用 `imagedestroy` 函数释放原始图像占用的内存。

## image_util.php 文件（续）

```php
// If image is larger than specified ratio, create the new image
if ($width_ratio > 1 || $height_ratio > 1) {

    // Calculate height and width for the new image
    $ratio = max($width_ratio, $height_ratio);
    $new_height = round($old_height / $ratio);
    $new_width = round($old_width / $ratio);

    // Create the new image
    $new_image = imagecreatetruecolor($new_width, $new_height);

    // Set transparency according to image type
    if ($image_type == IMAGETYPE_GIF) {
        $alpha = imagecolorallocatealpha($new_image, 0, 0, 0, 127);
        imagecolortransparent($new_image, $alpha);
    }
    if ($image_type == IMAGETYPE_PNG || $image_type == IMAGETYPE_GIF) {
        imagealphablending($new_image, false);
        imagesavealpha($new_image, true);
    }

    // Copy old image to new image - this resizes the image
    $new_x = 0;
    $new_y = 0;
    $old_x = 0;
    $old_y = 0;
    imagecopyresampled($new_image, $old_image,
                        $new_x, $new_y, $old_x, $old_y,
                        $new_width, $new_height,
                        $old_width, $old_height);

    // Write the new image to a new file
    $image_to_file($new_image, $new_image_path);

    // Free any memory associated with the new image
    imagedestroy($new_image);
} else {
    // Write the old image to a new file
    $image_to_file($old_image, $new_image_path);
}
// Free any memory associated with the old image
imagedestroy($old_image);
}

?>
```

## 控制器

第 5 部分展示了 Upload Image 应用的控制器。首先，控制器导入了你刚才查看的两个工具文件。接下来，它创建了两个变量，用于处理存储图像的目录。然后，它获取当前操作。

该操作的默认值是一个空字符串。因此，控制器第一次运行时，会跳过 `switch` 语句，获取已上传文件的列表，并显示视图。但是，如果操作被设置为 “upload” 或 “delete”，控制器就会执行相应的代码。

对于 “upload” 操作，控制器会检查是否已在超全局数组 `$_FILES` 中设置了该文件。如果是，就获取文件的原始名称。但是，如果文件名为空字符串，此代码会使用 `break` 语句退出 `switch` 语句。

如果文件名不是空字符串，控制器会获取该文件的临时名称。然后，它将临时文件移动到 images 目录中的新永久位置。最后，它调用 `process_image` 函数来创建上传文件的较小版本。

对于 “delete” 操作，控制器会获取用户想要删除的文件的名称。然后，它检查该图像是否存在。如果存在，就使用 `unlink` 函数删除该图像。

`switch` 语句之后，代码继续获取已上传文件的列表并显示视图。这会显示应用的第一页，以便用户上传另一张图像。

### 控制器（index.php）

```php
<?php
require_once 'file_util.php';       // the get_file_list function
require_once 'image_util.php';      // the process_image function

$image_dir = 'images';
$image_dir_path = getcwd() . DIRECTORY_SEPARATOR . $image_dir;

$action = filter_input(INPUT_POST, 'action');
if ($action == NULL) {
    $action = filter_input(INPUT_GET, 'action');
    if ($action == NULL) {
        $action = '';
    }
}

switch ($action) {
    case 'upload':
        if (isset($_FILES['file1'])) {
            $filename = $_FILES['file1']['name'];
            if (empty($filename)) {
                break;
            }
            $source = $_FILES['file1']['tmp_name'];
            $target = $image_dir_path . DIRECTORY_SEPARATOR . $filename;
            move_uploaded_file($source, $target);

            // create the '400' and '100' versions of the image
            process_image($image_dir_path, $filename);
        }
        break;
    case 'delete':
        $filename = filter_input(INPUT_GET, 'filename',
            FILTER_SANITIZE_STRING);
        $target = $image_dir_path . DIRECTORY_SEPARATOR . $filename;
        if (file_exists($target)) {
            unlink($target);
        }
        break;
}
$files = get_file_list($image_dir_path);
include('uploadform.php');
?>
```

图 23-11  Upload Image 应用（第 5 部分，共 6 部分）

## 视图

第 6 部分展示了视图的代码。这些代码大部分是 HTML，理解起来应该没有困难。不过，请仔细查看上传表单的代码。在这里，第二个 `<input>` 标签显示“选择文件”按钮。该标签将上传的文件命名为 “file1”。然后，第三个 input 标签显示表单的提交按钮，即 Upload 按钮。

这个表单之后的 PHP 代码使用 `if` 语句检查 images 目录中是否包含任何文件。如果不包含，这段代码会显示一条消息，提示尚未上传任何图像。

否则，这段代码会使用循环处理目录中的每个文件。对于每个文件，该循环都会创建两个 URL，供后面的链接使用。第一个 URL 用于在浏览器窗口中显示图像；第二个 URL 用于删除文件。为此，该 URL 会以 “action” 参数设为 “delete” 以及一个包含文件名的 filename 参数来调用当前页面。

创建 URL 后，循环会显示无序列表的项，其中每个项对应 images 目录中的一个文件。每个列表项都提供两个链接，使用循环前面创建的 URL。第一个链接显示当前目录中名为 delete.png 的图像。当用户单击该图像时，控制权会连同删除文件的相应参数一起传递给控制器。第二个链接显示图像的文件名。当用户单击该名称时，应用会显示该图像。

### 视图（uploadform.php）

```html
<!DOCTYPE html>
<html>
<head>
    <title>Upload Image</title>
    <link rel="stylesheet" type="text/css" href="main.css"/>
</head>
<body>
    <header>
        <h1>Upload Image</h1>
    </header>
    <main>
        <h2>Image to be uploaded</h2>
        <form id="upload_form"
              action="" method="POST"
              enctype="multipart/form-data">
            <input type="hidden" name="action" value="upload">
            <input type="file" name="file1"><br>
            <input id="upload_button" type="submit" value="Upload">
        </form>
        <h2>Images in the directory</h2>
        <?php if (count($files) == 0) : ?>
            <p>No images uploaded.</p>
        <?php else: ?>
            <ul>
                <?php foreach($files as $filename) :
                    $file_url = $image_dir . '/' .
                                $filename;
                    $delete_url = '?action=delete&amp;filename=' .
                                  urlencode($filename);
                ?>
                <li>
                    <a href="<?php echo $delete_url;?>">
                        <img src="delete.png" alt="Delete"></a>
                    <a href="<?php echo $file_url; ?>">
                        <?php echo $filename; ?></a>
                </li>
                <?php endforeach; ?>
            </ul>
        <?php endif; ?>
    </main>
</body>
</html>
```

