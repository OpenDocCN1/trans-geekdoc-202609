

## PHP 核心编程

```php
$colorWhite = imagecolorallocate($image, 255, 255, 255);
$colorBlack = imagecolorallocate($image, 0, 0, 0);
imagefill($image, 0, 0, $colorWhite);
imagestring($image, 4, 10, 0, "Couldn't load image!");
$colorBlack;
header("Content-type: image/jpeg");
jpeg($image);
exit();


// 发送图像
header("Content-type: image/jpeg");
jpeg($image);
?>
```

## integer imagecreatefrompng(string filename)

使用 `imagecreatefrompng` 从文件加载 PNG 图像。

```php
<?php
// 加载并显示图像
$image = imagecreatefrompng("php.png");
header("Content-type: image/png");
imagepng($image);
?>
```

## boolean imagedashedline(integer image, integer start_x, integer start_y, integer end_x, integer end_y, integer color)

`imagedashedline` 从起点到终点绘制一条虚线。
`color` 参数是由 `imagecolorallocate` 返回的颜色标识符。使用 `imageline` 绘制实线。

图 12-3. imagedashedline。

```php
<?php
/*
 // 显示带有虚线的图像
 */

// 创建黄色正方形
$image = imagecreate(200,200);
$colorBlue = imagecolorallocate($image, 0, 0, 255);
$colorYellow = imagecolorallocate($image, 255, 255, 0);
imagefill($image, 0, 0, $colorYellow);

// 绘制蓝色虚线
imagesashedhedline($image, 10, 10, 150, 130, $colorBlue);

// 发送图像
header("Content-type: image/jpeg");
jpeg($image);
?>
```

## boolean imagedestroy(integer image)

使用 `imagedestroy` 函数释放与指定图像关联的内存。大多数情况下，你不需要这个函数，PHP 会在脚本结束时自动清理。

```php
<?php
/*
 // 创建图像，然后释放其内存 */
// 创建蓝色正方形
$image = imagecreate(200,200);
$colorBlue = imagecolorallocate($image, 128, 128, 255);
imagefill($image, 0, 0, $colorBlue);

// 发送图像
header("Content-type: image/jpeg");
jpeg($image);

// 使用 image 释放内存
imagedestroy($image);
?>
```

## boolean imagefill(integer image, integer x, integer y, integer color)

`imagefill` 函数在指定点使用指定的颜色进行洪刷填充。`color` 参数必须由 `imagecolorallocate` 返回。从指定点开始，像素被更改为指定的颜色，颜色向外扩散，直到遇到与指定点不同的颜色为止。请参见 `imagearc` 的描述示例。请参见 `imagefill` 以获取替代方案。

## boolean imagefilledpolygon(integer image, array points, integer number, integer color)

`imagefilledpolygon` 函数创建一个多边形，并内部填充指定的颜色。`points` 参数是一个包含每个点 x 和 y 值的数组。`number` 参数报告从数组中使用多少个点。

图 12-4. imagefilledpolygon。

```php
<?php
/*
 绘制一个黑色三角形
 绘制一个红色正方形 */
$image = imagecreate(200,200);
$colorRed = imagecolorallocate($image, 255, 0, 0);
$colorBlack = imagecolorallocate($image, 0, 0, 0);
imagefill($image, 0, 0, $colorRed);

// 设置三角形的三个点
$points = array(100, 10, 50, 60, 150, 60);

// 绘制三角形
imagefilledpolygon($image,
    $points, count($points),
    $colorBlack);

// 发送图像
header("Content-type: image/jpeg");
jpeg($image);
?>
```

图 12-5. imagefilledrectangle。

```php
<?php
/*
 ** 绘制一个黑色正方形 */
// 创建绿色正方形
$image = imagecreate(200,200);
$colorGreen = imagecolorallocate($image, 128, 255, 128);
$colorBlack = imagecolorallocate($image, 0, 0, 0);
imagefill($image, 0, 0, $colorRed);

// 绘制一个黑色矩形
imagefilledrectangle($image, 
10, 10, 90, 90,
$colorBlack);

// 发送图像
header("Content-type: image/jpeg");
jpeg($image);
?>
```

## boolean imagefilledrectangle(integer image, integer top_left_x, integer top_left_y, integer bottom_right_x, integer bottom_right_y, integer color)

`imagefilledrectangle` 函数根据左上角和右下角绘制一个填充的矩形。

## boolean imagefillborder(integer image, integer x, integer y, integer border_color, integer color)

`imagefillborder` 函数将对由 `border_color` 参数定义的区域进行洪刷填充。洪刷填充将从指定的坐标开始。关于高度的示例请参见 `imagecolorallocate`。

## integer imagefontheight(integer font)

`imagefontheight` 返回指定字体的像素高度，字体可能是内置字体（1–5）或通过 `imagefontload` 加载的字体。

```php
<?php
/** ** 创建大小正合适的文本图像 */

$Text = "Core PHP Programming";
$Font = 5;
$Width = imagefontwidth($Font) * strlen($Text);
$Height = imagefontheight($Font);

// 创建绿色正方形
$image = imagecreate($Width, $Height);
$colorGreen = imagecolorallocate($image, 128, 255, 128);
$colorBlack = imagecolorallocate($image, 0, 0, 0);
imagefill($image, 0, 0, $colorRed);

// 添加黑色文本
imagestring($image, $Font, 0, 0, $Text, $colorBlack);

// 发送图像
header("Content-type: image/jpeg");
jpeg($image);
?>
```

## integer imagefontwidth(integer font)

`imagefontwidth` 返回指定字体的像素宽度，字体可能是内置字体（1–5）或通过 `imagefontload` 加载的字体。请参见 `imagefontheight` 示例。

## boolean imagejpeg(integer image, string filename, integer quality)

`imagejpeg` 函数将图像发送到浏览器或写入文件。如果提供了 `filename`，则创建 JPEG 文件。否则，将图像直接发送到浏览器。可选的 `quality` 参数决定压缩级别，范围从 0（最低质量）到 10（最高质量）。

```php
<?php
/* ** 创建蓝色正方形，保存到磁盘 */
// 如果不存在或早于一小时，则创建图像
if(!file_exists("blue_square.jpg") OR
(filetime("blue_square.jpg") < (time() - 3600)))
{
    // 发送调试信息
    print("<-creating image->\n");

    // 创建蓝色正方形
    $image = imagecreate(200,100);
    $colorBlue = imagecolorallocate($image, 128, 128, 255);
    $colorWhite = imagecolorallocate($image, 255, 255, 255);
    imagefill($image, 0, 0, $colorBlue);

    // 为图像添加创建时间
    imagestag($image, 4, 10, 10,
    date("Y-m-d H:i:s"),
    $colorWhite);

    // 写入文件
    imagejpeg($image, "blue_square.jpg");
}

// 打印显示图像的标签
print("<IMG SRC="blue_square.jpg" " . 
"HEIGHT="100" WIDTH="200" BORDER="0">");
?>
```

## boolean imageinterlace(integer image, boolean on)

使用 `imageinterlace` 设置图像是否交错。如果更改成功，则返回 TRUE。交错图像的存储方式使其能够渐进显示而不是一次性显示。事实上，JPEG 可能不支持交错。

```php
<?php
/* ** 创建交错图像 */
// 创建红色正方形
$image = imagecreate(200,200);
$colorRed = imagecolorallocate($image, 255, 0, 0);
imagefill($image, 0, 0, $colorRed);

// 设置为交错
imageinterlace($image, TRUE);

// 发送图像
header("Content-type: image/jpeg");
jpeg($image);
?>
```

