

## 用于处理图像的函数

| 名称 | 描述 |
|---|---|
| `imagecreatefromxxx($path)` | 根据指定的文件路径创建 xxx 类型的图像。 |
| `imagesx($image)` | 返回指定图像的宽度。 |
| `imagesy($image)` | 返回指定图像的高度。 |
| `imagexxx($image, $path)` | 将指定的 xxx 类型图像写入指定的文件路径。 |
| `imagedestroy($image)` | 释放用于指定图像的内存。 |

## 读取和写入图像的代码

```php
// Set the paths for the images
$image_path = getcwd() . DIRECTORY_SEPARATOR . 'gibson_sg.png';
$image_path_2 = getcwd() . DIRECTORY_SEPARATOR . 'gibson_sg_2.png';

// Get the image width, height, and type
$image_info = getimagesize($image_path);
$image_type = $image_info[2];

// Set up the function names for the image type
switch($image_type) {
    case IMAGETYPE_JPEG:
        $image_from_file = 'imagecreatefromjpeg';
        $image_to_file = 'imagejpeg';
        break;
    case IMAGETYPE_GIF:
        $image_from_file = 'imagecreatefromgif';
        $image_to_file = 'imagegif';
        break;
    case IMAGETYPE_PNG:
        $image_from_file = 'imagecreatefrompng';
        $image_to_file = 'imagepng';
        break;
    default:
        echo 'File must be a JPEG, GIF, or PNG image.';
        exit;
}

// Create a new image from the file
$image = $image_from_file($image_path);

// Check the image's width and height
$image_width = imagesx($image);
$image_height = imagesy($image);

// Write the image to a file
$image_to_file($image, $image_path_2);

// Free any memory associated with the image
imagedestroy($image);
```

**图23-8** — 如何读取和写入图像

## 如何调整图像大小

图23-9展示了如何调整图像大小。具体来说，它展示了如何将大图像调整为较小的尺寸。这会减小图像的显示尺寸和文件大小，有助于加快图像加载速度，而且不会降低图像的视觉质量。虽然你可以使用类似的技术来创建更大的图像，但这会增加文件大小并降低图像的视觉质量。因此，很少有必要增大图像尺寸。

要调整图像大小，可以使用 `imagecreatetruecolor` 函数创建一个较小尺寸的新真彩色图像。真彩色图像使用 RGB 值，这些值由红色、绿色和蓝色的 256 种色调组成。

创建较小尺寸的新图像后，可以使用 `imagecopyresampled` 函数将大图像复制到较小的图像中。该函数会对图像进行重采样和调整大小，使其适合较小的图像。

调整图像大小时，通常需要按相同比例调整高度和宽度。否则，图像会被拉伸，从而扭曲原始图像。为了避免这种情况，你需要执行如本例所示的计算，以便获得正确的宽高比。

该示例首先为图像设置两个路径。然后，它获取旧图像（源图像）的高度和宽度。接下来，它计算该图像高度和宽度相对于 100 像素值的比率。例如，如果图像高度为 300，则高度比率为 3；如果图像宽度为 400，则宽度比率为 4。

在计算高度和宽度比率后，此代码检查任一比率是否大于 1。如果大于 1，则执行代码创建一个最大为 100 像素 × 100 像素的图像。首先，此代码使用 `max` 函数获取两个比率中较大的一个。然后，使用该比率计算新图像（目标图像）的高度和宽度。接下来，创建新图像并将旧图像复制到新图像。为此，此代码将旧图像和新图像的 x 和 y 值设为 0，以表示两个图像都从左上角开始。此外，它还指定了旧图像和新图像正确的宽高值。

调整图像大小后，此代码将新图像写入新文件。这里的文件名（`gibson_sg_100.png`）表示图像最大为 100 × 100 像素。然后，此代码释放与新图像和旧图像关联的所有内存。

## 可用于调整图像大小的函数

| 名称 | 描述 |
|---|---|
| `imagecreatetruecolor($w, $h)` | 返回指定大小的全黑色真彩色图像。 |
| `imagecopyresampled($di, $si, $dx, $dy, $sx, $sy, $dw, $dh, $sw, $sh)` | 将源图像 (s) 的矩形部分复制到目标图像 (d)，必要时调整图像大小。 |

## 将图像缩放至最大 100 × 100 像素的代码

```php
// Set some variables
$old_path = getcwd() . DIRECTORY_SEPARATOR . 'gibson_sg.png';
$new_path = getcwd() . DIRECTORY_SEPARATOR . 'gibson_sg_100.png';
$image_type = IMAGETYPE_PNG;

// Get the old image and its height and width
$old_image = imagecreatefrompng($old_path);
$old_width = imagesx($old_image);
$old_height = imagesy($old_image);

// Calculate height and width ratios for a 100x100 pixel maximum
$width_ratio = $old_width / 100;
$height_ratio = $old_height / 100;

// If image is larger than specified ratio, create the new image
if ($width_ratio > 1 || $height_ratio > 1) {

    // Calculate height and width for the new image
    $ratio = max($width_ratio, $height_ratio);
    $new_height = round($old_height / $ratio);
    $new_width = round($old_width / $ratio);

    // Create the new image
    $new_image = imagecreatetruecolor($new_width, $new_height);

    // Copy old image to new image to resize the file
    $new_x = 0;        // Start new image in upper left corner
    $new_y = 0;
    $old_x = 0;        // Copy old image from upper left corner
    $old_y = 0;
    imagecopyresampled($new_image, $old_image,
                       $new_x, $new_y, $old_x, $old_y,
                       $new_width, $new_height, $old_width, $old_height);

    // Write the new image to a file
    imagepng($new_image, $new_path);

    // Free any memory associated with the new image
    imagedestroy($new_image);
}

// Free any memory associated with the old image
imagedestroy($old_image);
```

**图23-9** — 如何调整图像大小

## 如何处理透明度

透明度指的是图像中透明的部分。例如，如果包含星星的图像被放置在绿色背景上，绿色背景会透过星星周围图像的透明部分显示出来。虽然 JPEG 图像不允许图像的一部分透明，但 GIF 和 PNG 图像确实支持透明度。

透明图像不仅存储颜色的 RGB 值，还存储一个 *alpha 通道*，该通道提供有关透明度的附加信息。然后，浏览器可以将图像的透明部分与背景组合，从而产生透明效果。这个过程称为 *alpha 混合*。

当你按前一张图所述创建新的真彩色图像时，图像默认带有黑色背景。因此，如果将使用透明度的图像复制到此黑色背景上，图像背景将变为黑色，且透明度会丢失。为避免这种情况，你可以使用图23-10中的函数和技术来控制图像的透明度。

在此图的示例中，第一个 if 语句检查图像是否为 GIF 图像。如果是，则此代码执行一些对于 GIF 图像需要处理、而对于 PNG 图像不需要处理的操作。具体来说，第一条语句调用 `imagecolorallocatealpha` 函数来分配 alpha 颜色。在本例中，该函数通过指定 RGB 值为 0、0、0 将 alpha 颜色设置为黑色。此外，它指定 alpha 值为 127，表示 alpha 颜色应完全透明。然后，下一条语句使用 `imagecolortransparent` 函数将 alpha 颜色设置为图像中的透明色。

第二个 if 语句检查图像是 GIF 图像还是 PNG 图像。如果是，则此代码执行 GIF 图像所需的其他处理，以及 PNG 图像所需的唯一处理。这里，第一条语句关闭 alpha 混合。如果要保存完整的 alpha 通道信息，这是必需的。然后，第二条语句尝试保存完整的 alpha 通道信息。如果成功，此代码将创建具有完全透明部分的图像。

处理完图像后，你可能需要查看它的效果。为此，你可以使用 Windows 资源管理器或 Mac 访达查看图像。或者，也可以在图形编辑程序（如 Photoshop）中打开图像。这些程序通常使用背景色或棋盘格图案来表示图像中的透明部分。

