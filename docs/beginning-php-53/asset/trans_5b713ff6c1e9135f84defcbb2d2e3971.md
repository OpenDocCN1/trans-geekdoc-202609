

这个示例创建了一个名为 $myPoints 的多边形点数组。数组中有六个元素，即三组 x/y 坐标对。这意味着该多边形有三个角，分别位于 (20, 20)、(185, 55) 和 (70, 80)。

代码接着调用 `imagepolygon()` 函数，并传递以下参数：

- 1. 图像资源。
- 2. 点数组。
- 3. 多边形中的点数。
- 4. 用于绘制形状的颜色。

图 17-12 显示了示例多边形。

![](img/1ddec54918a4802eb9b4febec3d4e7f6_554_0.png)

顺便提一句，如果你想创建填充形状，可以使用 `imagefilledrectangle()`、`imagefilledellipse()`、`imagefilledarc()` 和 `imagefilledpolygon()` 等函数。了解更多信息，请访问 http://www.php.net/manual/en/ref.image.php。

## 尝试一下：绘制带圆角的矩形

既然你已经知道如何绘制直线和弧线，现在可以创建一个实用函数来绘制圆角矩形。将以下脚本保存为 `rounded_rectangle.php`，并在浏览器中打开其 URL：

```
<?php
function roundedRectangle( $image, $x1, $y1, $x2, $y2, $curveDepth, $color )
{
	// Draw the four sides
	imageline( $image, ($x1 + $curveDepth), $y1, ($x2 - $curveDepth), $y1,
	$color );
	imageline( $image, ($x1 + $curveDepth), $y2, ($x2 - $curveDepth), $y2,
	$color );
	imageline( $image, $x1, ($y1 + $curveDepth), $x1, ($y2 - $curveDepth),
	$color );
	imageline( $image, $x2, ($y1 + $curveDepth), $x2, ($y2 - $curveDepth),
	$color );

	// Draw the four corners
	imagearc( $image, ($x1 + $curveDepth), ($y1 + $curveDepth), (2 *
	$curveDepth), (2 * $curveDepth), 180, 270, $color );
	imagearc( $image, ($x2 - $curveDepth), ($y1 + $curveDepth), (2 *
	$curveDepth), (2 * $curveDepth), 270, 360, $color );
	imagearc( $image, ($x2 - $curveDepth), ($y2 - $curveDepth), (2 *
	$curveDepth), (2 * $curveDepth), 0, 90, $color );
	imagearc( $image, ($x1 + $curveDepth), ($y2 - $curveDepth), (2 *
	$curveDepth), (2 * $curveDepth), 90, 180, $color );
}
// An example rectangle
$myImage = imagecreate( 200,100 );
$myGray = imagecolorallocate( $myImage, 204, 204, 204 );
$myBlack = imagecolorallocate( $myImage, 0, 0, 0 );
roundedRectangle( $myImage, 20, 10, 180, 90, 20, $myBlack );
header( "Content-type: image/png" );
imagepng( $myImage );
imagedestroy( $myImage );
?>
```

图 17-13 显示了脚本的输出。

![](img/1ddec54918a4802eb9b4febec3d4e7f6_555_0.png)

图 17-13

## 工作原理

这里的内容你在过去几页中都已经见过；创建圆角矩形的唯一诀窍在于理解如何组合直线和弧线，以获得想要的效果。

脚本首先创建一个绘制圆角矩形的函数。通过将代码存储在函数中，如果你想绘制尺寸不同的其他圆角矩形，以后可以重复使用。该函数有七个参数：

```
function roundedRectangle( $image, $x1, $y1, $x2, $y2, $curveDepth, $color )
```

第一个参数是要在其中绘制矩形的图像资源。接下来的两个参数指定矩形的左上角，再接下来的两个参数用于矩形的右下角。（函数并不会实际在这些点上绘制任何内容，因为它绘制的是带有圆角的矩形，但这些点作为矩形角点的锚点。）第六个参数 $curveDepth 是曲线在每条矩形边结束前开始的像素数。最后一个参数当然是矩形的颜色。图 17-14 显示了传递给 roundedRectangle() 函数的参数如何使用。

![](img/1ddec54918a4802eb9b4febec3d4e7f6_556_0.png)

图 17-14

函数首先绘制矩形顶部的一条线。它不会从 $x1 绘制到 $x2 的整条线，因为必须考虑角点的圆曲线。为此，它将 $curveDepth 值加到 $x1 位置，并从 $x2 位置减去该值：

```
imageline( $image, ($x1 + $curveDepth), $y1, ($x2 - $curveDepth), $y1,
$color );
```

由于线条是水平的，两个点使用相同的 y 位置。下一条线以类似方式沿矩形底部延伸：

```
imageline( $image, ($x1 + $curveDepth), $y2, ($x2 - $curveDepth), $y2,
$color );
```

接下来的两条线是沿矩形左侧和右侧向下延伸的垂直线。这次，函数对每条线使用相同的 x 值（左侧线为 $x1，右侧为 $x2），并适当改变 y 值，使线条高度与圆角相匹配：

```
imageline( $image, $x1, ($y1 + $curveDepth), $x1, ($y2 - $curveDepth),
$color );
imageline( $image, $x2, ($y1 + $curveDepth), $x2, ($y2 - $curveDepth),
$color );
```

接下来，函数绘制圆角，从左上角开始。为了计算弧的中心点（参见图 17-15），函数将 $curveDepth 的值加到 $x1 和 $y1 上。为了得到弧的宽度和高度，函数需要将 $curveDepth 值加倍，因为 $curveDepth 实际上是弧的半径。

![](img/1ddec54918a4802eb9b4febec3d4e7f6_556_1.png)

图 17-15

由于这是左上角，弧从 180 度（9 点钟方向）开始，绕过到 270 度（12 点钟方向）：

```
imagearc( $image, ($x1 + $curveDepth), ($y1 + $curveDepth), (2 *
$curveDepth), (2 * $curveDepth), 180, 270, $color );
```

其余角点的创建方式完全相同，只不过函数根据需要从 $x1、$y1、$x2 和 $y2 中添加或减去 $curveDepth，以获得每个弧的正确中心点。还要记住，每个角点的弧的起始和结束位置都会变化。

```
imagearc( $image, ($x2 - $curveDepth), ($y1 + $curveDepth), (2 *
$curveDepth), (2 * $curveDepth), 270, 360, $color );
imagearc( $image, ($x2 - $curveDepth), ($y2 - $curveDepth), (2 *
$curveDepth), (2 * $curveDepth), 0, 90, $color );
imagearc( $image, ($x1 + $curveDepth), ($y2 - $curveDepth), (2 *
$curveDepth), (2 * $curveDepth), 90, 180, $color );
}
```

圆角矩形函数到此结束，现在脚本可以绘制图像了。

脚本首先创建空白图像，并为图像分配两种颜色。分配的第一种颜色（灰色）是图像的背景色，第二种颜色（黑色）用于矩形：

```
$myImage = imagecreate( 200, 100 );
$myGray = imagecolorallocate( $myImage, 204, 204, 204 );
$myBlack = imagecolorallocate( $myImage, 0, 0, 0 );
```

接下来，代码调用 roundedRectangle() 函数，并传递前面讨论过的参数：

```
roundedRectangle( $myImage, 20, 10, 180, 90, 20, $myBlack );
```

最后，通过调用 header() 然后是 imagepng() 将矩形图像发送到 Web 浏览器。为了收尾，调用 imagedestroy() 函数来清理内存：

```
header( "Content-type: image/png" );
imagepng( $myImage );
imagedestroy( $myImage );
?>
```

## 处理图像

在本章中，你已经了解了如何使用 GD 图像库的绘图函数创建图像，并创建了一些基本形状。但如果你想处理现有图像，会发生什么呢？好吧，PHP 并不限制你只能创建新图像——你可以同样轻松地生成基于现有 JPEG、PNG 或 GIF 图像的新图像。

## 打开现有图像

如你已经看到，要从头开始创建新图像，可以使用 `imagecreate()` 或 `imagecreatetruecolor()` 函数。要基于现有图像创建新图像，可以使用 `imagecreatefrom...` 系列函数。最常用的是 `imagecreatefromjpeg()`、`imagecreatefromgif()` 和 `imagecreatefrompng()`。还有一些其他函数可以让你从现有图像格式在内存中创建新图像，但它们不如这三个常用。

`imagecreatefromjpeg()` 函数的工作方式与 `imagecreate()` 函数相同，只不过不再将新图像的宽度和高度作为参数传递，而只需将现有图像的文件名作为字符串传递。该函数返回一个图像资源，你可以使用它。

例如，这一行

```
$myImage = imagecreatefromjpeg( "lucky.jpg" );
```

打开与脚本位于同一目录下的名为 `lucky.jpg` 的 JPEG 文件，并将其内容存储在内存中。图像资源标识符 `$myImage` 指向内存中的图像数据。你可以通过将图像数据输出到浏览器来进行测试。

## 尝试一下：显示 JPEG

在此示例中，你将现有的 JPEG 文件读入内存，然后将其发送到浏览器进行显示。将以下脚本保存为 `show_jpeg.php`，放在文档根目录下。确保传递给 `imagecreatefromjpeg()` 函数的文件名是同一文件夹中存在的 JPEG 文件。

```
<?php
$myImage = imagecreatefromjpeg( "lucky.jpg" );
header( "Content-type: image/jpeg" );
imagejpeg( $myImage );
imagedestroy( $myImage );
?>
```

现在在 Web 浏览器中打开脚本的 URL。图 17-16 显示了示例输出——当然，你会看到不同的图像。

