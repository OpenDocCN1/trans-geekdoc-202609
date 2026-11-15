

## 第三部分：在实际中使用 PHP

在这里，你已将 imagecopy() 函数改为 imagecopymerge()，并提供了不透明度值 50 —— 介于透明和不透明之间。脚本的输出现在看起来更像一个水印，如图 17-20 所示。

![](img/1ddec54918a4802eb9b4febec3d4e7f6_565_0.png)

图 17-20

如果你对在图像中尝试透明效果感兴趣，请查看 PHP 手册中的 imagecolorallocatealpha() 和 imagealphablending() 函数，网址为 http://www.php.net/manual/en/ref.image.php。尽管你无法复制使用专业图形程序所能获得的所有效果，但仍然可以创建一些有趣的效果。

下一节也涉及操作现有图像，但这次你将把它缩小为缩略图。

## 创建缩略图

创建图像的缩略图使用了与应用水印类似的方法，只是复制方向相反 —— 不是将较小的图像复制到较大的图像中，而是将较大的图像复制到一个新的较小图像中，并在过程中将其缩小。以下是创建缩略图的示例脚本：

```php
<?php
$mainImage = imagecreatefromjpeg( "lucky.jpg" );
$mainWidth = imagesx( $mainImage );
$mainHeight = imagesy( $mainImage );

$thumbWidth = intval( $mainWidth / 4 );
$thumbHeight = intval( $mainHeight / 4 );

$myThumbnail = imagecreatetruecolor( $thumbWidth, $thumbHeight );

imagecopyresampled( $myThumbnail, $mainImage, 0, 0, 0, 0, $thumbWidth,
$thumbHeight, $mainWidth, $mainHeight );

header( "Content-type: image/jpeg" );
imagejpeg( $myThumbnail );
imagedestroy( $myThumbnail );
imagedestroy( $mainImage );
?>
```

将脚本保存为文档根目录文件夹中的 thumbnail.php，将第二行中的 lucky.jpg 替换为你自己的图像（保存在同一文件夹中）。在 Web 浏览器中打开其 URL 来运行脚本。图 17-22 显示了一个示例运行。

以下是脚本的工作原理。首先它打开要为其创建缩略图的图像：

```php
$mainImage = imagecreatefromjpeg( "lucky.jpg" );
```

接下来，它使用 imagesx() 和 imagesy() 函数获取原始图像的宽度和高度。你需要这些值来计算新缩略图的大小：

```php
$mainWidth = imagesx( $mainImage );
$mainHeight = imagesy( $mainImage );
```

在此示例中，缩略图将是原始图像大小的四分之一，因此脚本将原始宽度和高度除以四来计算缩略图尺寸。然后使用 intval() 函数将得到的值四舍五入为整数（因为你无法使用半个像素）：

```php
$thumbWidth = intval( $mainWidth / 4 );
$thumbHeight = intval( $mainHeight / 4 );
```

现在脚本创建一个新的空白图像来存储缩略图。通常你会制作照片的缩略图，因此你需要一个颜色数量较多的图像。因此，脚本使用 imagecreatetruecolor() 函数来创建空白缩略图：

```php
$myThumbnail = imagecreatetruecolor( $thumbWidth, $thumbHeight );
```

接下来，脚本需要将原始图像缩小并将其复制到新的缩略图中。有两个函数可以做到这一点：imagecopyresized() 和 imagecopyresampled()。两者的区别在于，imagecopyresized() 稍微快一些，但完全不进行图像平滑处理。如果你使用 imagecopyresized() 创建缩略图然后放大，你会看到类似图 17-21 所示的块状效果。

![](img/1ddec54918a4802eb9b4febec3d4e7f6_567_0.png)

图 17-21

imagecopyresampled() 函数虽然稍慢一些，但会对像素进行插值，因此你不会得到那种块状效果。imagecopyresized() 和 imagecopyresampled() 函数都采用相同的十个参数：

- 目标图像
- 源图像
- 目标图像中复制的像素块左上角的 x 和 y 坐标
- 源图像中指示要复制的块左上角的 x 和 y 坐标
- 目标图像中复制块的调整大小后的宽度和高度
- 要从原始图像中复制出的图像数据块的宽度和高度

脚本使用 imagecopyresampled() 函数将整个图像数据复制到缩略图中，并在过程中将其缩小：

```php
imagecopyresampled( $myThumbnail, $mainImage, 0, 0, 0, 0, $thumbWidth,
$thumbHeight, $mainWidth, $mainHeight );
```

最后，脚本将图像数据发送到浏览器（参见图 17-22），并清理图像使用的内存：

```php
header( "Content-type: image/jpeg" );
imagejpeg( $myThumbnail );
imagedestroy( $myThumbnail );
imagedestroy( $mainImage );
?>
```

![](img/1ddec54918a4802eb9b4febec3d4e7f6_568_0.png)

图 17-22

## 在图像中使用文本

使用 PHP 向图像添加文本使你能够为图像添加注释或绘制动态图表和图形。向图像添加文本最快、最简单的方法是使用 imagestring() 函数，它允许你在指定位置在图像上绘制一行文本。

### 添加标准文本

使用 imagestring() 在图像上绘制很容易，因为该函数可以使用系统内置字体来绘制文本。这意味着你不必担心在服务器上加载特定字体。

imagestring() 接受六个参数：

- 图像资源
- 用于文本的字体。这是一个整数值，范围从 1 开始。1 到 5 之间的值为内置系统字体；随后加载的任何字体都由从 6 开始的数字表示
- 文本位置的 x 和 y 值。这些值表示文本将出现的矩形的左上角
- 要绘制的文本字符串
- 文本的颜色

要为 imagestring() 函数加载字体，请使用 imageloadfont() 函数。它加载一种与架构相关的位图字体；这意味着字体需要在你想要使用它的同一类型系统上生成。一个更简单的解决方案是使用 TrueType 字体 —— 你马上就会了解到这一点。

如果 imagestring() 成功将文本添加到图像中，则返回 true；如果出错，则返回 false。

## 尝试：显示系统字体

尝试显示每个五种系统字体。将此脚本保存为文档根目录文件夹中的 `system_fonts.php`，并在 Web 浏览器中打开脚本 URL：

```php
<?php
$textImage = imagecreate( 200, 100 );
$white = imagecolorallocate( $textImage, 255, 255, 255 );
$black = imagecolorallocate( $textImage, 0, 0, 0 );
$yOffset = 0;
for ( $i = 1; $i <= 5; $i++ ) {
    imagestring( $textImage, $i, 5, $yOffset, "This is system font $i", $black );
    $yOffset += imagefontheight( $i );
}
header( "Content-type: image/png" );
imagepng( $textImage );
imagedestroy( $textImage );
?>
```

图 17-23 显示了此脚本的输出。

![](img/1ddec54918a4802eb9b4febec3d4e7f6_569_0.png)

图 17-23

## 工作原理

首先，脚本创建一个基于调色板的空白图像用于文本，然后在图像的调色板中分配白色和黑色。因为代码先分配白色，所以它被设置为图像的背景色：

```php
<?php
$textImage = imagecreate( 200,100 );
$white = imagecolorallocate( $textImage, 255, 255, 255 );
$black = imagecolorallocate( $textImage, 0, 0, 0 );
```

然后，脚本设置一个变量来存储绘制字符串的 y 位置（向下的距离）。第一行文本将位于图像顶部，因此此变量设置为 0。

```php
$yOffset = 0;
```

接下来，脚本设置一个 `for` 循环来遍历每个五个内置系统字体：

```php
for ( $i = 1; $i <= 5; $i++ ) {
    imagestring( $textImage, $i, 5, $yOffset, "This is system font $i", $black );
    $yOffset += imagefontheight( $i );
}
```

循环结束后，脚本输出图像并清理：

```php
header( "Content-type: image/png" );
imagepng( $textImage );
imagedestroy( $textImage );
?>
```

### 使用 TrueType 字体

绘制基本图表和图形时，你可能更喜欢使用内置系统字体，因为它们是非比例字体 —— 所有字符宽度相同 —— 因此布局和定位更容易。但是，如果你希望文本看起来更优雅，那么你可能想使用 TrueType 字体。这些字体提供了更多的灵活性 —— 不仅可以通过从广泛可用的字体中选择来控制文本的外观，还可以指定文本大小和绘制文本的角度。

绘制 TrueType 文本的首选函数是 `imagefttext()`，它使用 FreeType 2 库。该函数按顺序接受以下参数：

- 包含要在其上写入文本的图像的图像资源
- 以点为单位的字体大小
- 要旋转文本的角度，以度为单位。零度为三点钟方向，90 度为十二点钟方向，依此类推。值为零会生成标准的从左到右文本。（请注意，与相应的 `imagearc()` 参数不同，此角度按逆时针方向而不是顺时针方向工作）
- 你希望文本开始的 `x` 和 `y` 位置。这是文本周围边界框的左下角。这与 `imagestring()` 函数不同，后者的坐标表示边界框的左上角

