

# PHP 核心编程

与 `imagedashedline` 一，`imageline` 从起点到终点绘制一条线。在这种情况下，这条线是实线。

## 图 12-6. imageline.

![](img/58e6a0f5d6a8a41d4645d8c07b3bf1e3_344_0.png)

```php
<?php
** 绘制黑色实线
 */

// 创建青色矩形
$image = imagecreate(200,200);
$colorCyan = imagecolorallocate($image, 0, 255, 255);
$colorBlack = imagecolorallocate($image, 0, 0, 0);
imagefill($image, 0, 0, $colorCyan);

// 绘制黑色实线
imageline($image, 10, 10, 150, 130, $colorBlack);

// 发送图像
header("Content-type: image/jpeg");
imagejpeg($image);

integer imageloadfont(string filename)
```

`imageloadfont` 函数加载字体并返回一个可以与其他字体函数使用的标识符。字体以特殊格式的位图形式存储。PHP 3 分发包含一个 Perl 脚本，用于将 X11.bdf 文件转换为 PHP 格式。

加载字体的代码取决于架构。表 12.2 显示了使用 32 位整数的系统的字体文件结构。如果您想创建自己的字体文件。

| 表 12.2. PHP 字体文件格式 |

| 位置 | 长度 | 描述 |
| --- | --- | --- |
| 0 | 4 | 字体中的字符数 |
| 4 | 4 | 第一个字符的 ASCII 值 |
| 8 | 4 | 每个字符的像素宽度 |
| 12 | 4 | 每个像素使用 1 字节，此字段应为字符数、宽度和高度的乘积。 |
| 16 | variable | |

**imagepng** 函数将图像发送到浏览器或将其写入文件。如果提供了文件名，则创建一个 PNG 文件。否则，图像将直接发送到浏览器。本节中的许多示例都使用了后后一种方法。

## boolean imagepolygon(integer image, array points, integer number, integer color)

`imagepolygon` 函数的行为与 `imagefilledpolygon` 函数相同，区别是多边形不会被填充。`points` 参数是一个整数数组，每个多边形点对应两个整数。线将依次从每个点绘制，并从最后一个点连接到第一个点。

## 图 12-7. imagepolygon.

![](img/58e6a0f5d6a8a41d4645d8c07b3bf1e3_346_0.png)

```php
<?php
/**
 ** 绘制一个空心黑色三角形
 */

// 创建红色矩形
$image = imagecreate(200,200);
$colorRed = imagecolorallocate($image, 255, 0, 0);
$colorBlack = imagecolorallocate($image, 0, 0, 0);
imagefill($image, 0, 0, $colorRed);

// 设置三角形顶点
$points = array(100, 10, 50, 60, 150, 60);

// 绘制黑色三角形
imagepolygon($image,
	$points, count($points)/2,
	$colorBlack);

// 发送图像
header("Content-type: image/jpeg");
imagejpeg($image);
?>
```

array imagesbbox(string text, integer font_identifier, integer size, integer spacing, integer letting, double angle)

`imagesbbox` 函数返回一个包含坐标对的数组，用于指定一个围绕理论文本字符串的边界（bbox）。前两个数字是左下角的 x 和 y 值。第二对数字指定右上角。

`font_identifier` 是由 `imagespreadfont` 返回的整数。`size` 参数单位为像素。`spacing` 参数控制文本行之间的垂直间距。`letting` 参数控制字符之间的水平间距。两者都以 en-square 的 1/1000 为单位，并加到字体的默认行距上。它们可以是正值也可以是负值。`angle` 参数指定从正常的左到右方向旋转的角度数。

示例见下文的 `imageptext`。

integer imagescopopyfont(integer font_identifier)

`imagescopopyfont` 函数将通过 `imagespreadfont` 加载的字体复制到另一个字体标识符。这允许你在内存中保留一个字体的原始版本以及另一个拉伸或倾斜的副本。

```php
<?php
/*
 ** 使用 Postscript 字体绘制文本
 ** 绘制正常、拉伸和倾斜
 */
// 设置文本参数
$font_file = "ComputerModern-Roman";
$size = 20;
$angle = 0;
$text = "PHP";
$antialias_steps = 16;
$spacing = 0;
$letting = 0;

// 创建青色矩形
$image = imagecreate(300,200);
$colorCyan = imagecolorallocate($image, 0, 255, 255);
$colorBlack = imagecolorallocate($image, 0, 0, 0);
imagefill($image, 0, 0, $colorCyan);

// 绘制黑色实线
imageline($image, 10, 10, 150, 130, $colorBlack);

// 发送图像
header("Content-type: image/jpeg");
imagejpeg($image);
?>
```

