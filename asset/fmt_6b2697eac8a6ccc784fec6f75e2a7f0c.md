
函数首先绘制横跨矩形顶部的线条。它没有从 `$x1` 一直画到 `$x2`，因为它必须考虑角的弧线。为了做到这一点，它在 `$x1` 位置加上了 `$curveDepth` 值，并从 `$x2` 位置减去了该值：

```php
imageline($image, $x1 + $curveDepth, $y1, $x2 - $curveDepth, $y1, $color);
```

因为线条是水平的，两个点使用相同的 `$y` 位置。下一条线条以类似的方式沿矩形底部通过：

```php
imageline($image, $x1 + $curveDepth, $y2, $x2 - $curveDepth, $y2);
```

接下来两条是矩形左侧和右侧的垂直线条。函数对每条线条使用相同的 `$x` 值（左侧为 `$x1`，右侧为 `$x2`），并适当调整 `$y` 值，使线条与圆角匹配：

```php
imageline($image, $x1, $y1 + $curveDepth, $x1, $y2 - $curveDepth, $color);
imageline($image, $x2, $y1 + $curveDepth, x2, y2 - $curveDepth,);
```

接下来函数从左上角开始绘制圆角。为了计算弧的中心点（见图 17-15），函数在 `$x1` 和 `$y1` 值上都加上了 `$curveDepth`。为了获得弧的宽度和高度，函数需要将 `$curveDepth` 值翻倍，因为 `$curveDepth` 是弧的半径。![](img/ede05b7b77968b82cbd9a513122fb183_556_1.png) 因为这是左上角，弧从 180 度（9 点钟位置）开始，绕到 270 度（12 点钟位置）：

```php
imagearc($image, ($x1 + $curveDepth), ($y1 + $curveDepth), (2 * $curveDepth), 180, 270, $color);
```

其余角的创建完全相同，只是函数适当地增加或减少了 `$x1`, `$y1`, `$x2` 和 `$y2` 以获取每个弧的正确点。还要记住每个弧的起始和结束位置。

```php
imagearc($image, ($x2 - $curveDepth), ($y1 + $curveDepth), (2 * $curveDepth), 270, 360, $color);
imagearc($image, ($x2 - $curveDepth), ($y2 - $curveDepth), (2 * $curveDepth), 0, 90, $color);
imagearc($image, ($x1 + $curveDepth), ($y2 - $curveDepth), (2 * $curveDepth), 90, 180, $color);
```

圆角矩形函数结束了，现在我们可以绘制图像了。

第一个脚本创建图像并为图像分配两种颜色。第一种颜色（灰色）是图像的背景，第二种颜色（黑色）用于矩形：

```php
$myImage = imagecreate(200,100);
$myGray = imagecolorallocate($myImage, 204, 204, 204);
$myBlack = imagecolorallocate($myImage, 0, 0, 0);
roundedRectangle($myImage, 20, 10, 90, 20, $myBlack);
```

最后，通过调用 `header()` 将图像发送到浏览器。使用 `imagedestroy()` 函数清理内存：

```php
header("Content-type: image/png");
imagepng($myImage);
imagedestroy($myImage);
```

# 图像处理

到目前为止，你已经学习如何使用 GD 库的绘制函数创建图像，并创建了一些基本形状。但如果你想处理现有图像呢？PHP 并不限制你只能创建新图像——你可以轻松地根据现有图像生成新图像。

正如你所看到的，要从头创建一个新图像可以使用 `imagecreate()` 或 `imagecreatcolor()` 函数。要根据现有图像创建新图像，你使用 `imagecreatefrom` 系列函数。其中最常见的是 `imagecreatejpeg()`、`imagecreategif()` 和 `imagecreatepng()`。其他许多函数允许从内存中的现有图像创建新图像，但它们没有这三个使用广泛。

`imagecreatejpeg()` 函数的工作方式与 `imagecreate()` 函数相同，不同之处不是传递图像的宽度和高度，而是将现有图像的文件作为字符串传递。该函数返回一个你可以操作的图像资源。

例如，该行：

```php
$myImage = imagecreatejpeg("lucky.jpg");
```

打开与脚本在同一目录下的 JPEG 文件 `lucky.jpg`，将其内容存储在内存中。图像标识符 `$myImage` 指向内存中的图像数据。你可以通过将图像数据输出到浏览器来测试这一点。

## 尝试一下：显示 JPEG

在此示例中，你将现有 JPEG 文件读取到内存中，然后将其发送到浏览器显示。将以下脚本保存为 `show_jpeg.php` 到你的文档根文件夹中。确保传递给 `imagecreatejpeg()` 函数的文件名是相同文件夹中的 JPEG 文件。

```php
<?php
$myImage = imagecreatejpeg("lucky.jpg");
header("Content-type: image/jpeg");
jpeg($myImage);
imagedestroy($myImage);
?>
```

现在在 Web 浏览器中打开脚本的 URL。图 17-16 显示了一个示例输出——当然，你会有不同的图像。

# 第三部分：在实践中使用 PHP

![](img/ede05b7b77968b82cbd9a513122fb183_559_0.png)

图 17-16

## 工作原理

这段代码非常直观，不会出现任何问题。`imagecreatefromjpeg()` 函数会从现有图像创建一个新的图像资源：

```php
$myImage = imagecreatefromjpeg("lucky.jpg");
```

然后脚本向 Web 浏览器发送一个头部，告诉它将接收 JPEG 图像数据：

```php
header("Content-type: image/jpeg");
```

剩下的工作就是发送数据并清理内存中的图像：

```php
imagejpeg($myImage);
imagedestroy($myImage);
```

当然，这个脚本并没有做任何你无法使用纯 HTML 独立完成的事情，所以你可能会疑惑这有什么意义。事实上，在将其发送到浏览器之前打开现有图像并对其进行处理，在很多方面都是用的。使用 GD 图像函数对图像进行的一些操作包括：

- 缩放图像以创建用于缩略图
- 降低图像质量以提高加载速度

## 第17 章：使用 PHP 生成图像

- 在图像上添加一些描述性文本或说明
- 将另一张图像的一部分复制到图中，作为版权用途的水印

在接下来的章节中，你将查看如何为图像应用水印，以及如何创建图像的缩略图。

### 应用水印

如果你正在开发一个显示原创艺术品或照片的网站，你可能希望保护你或客户的知识产权不被盗用。一种常用方法是应用水印，以防止他人将其据为己有。操作方法。

首先，在 Photoshop 等图像编辑器中创建一个简单的版权图像（如图 17-17 所示）。为此，在白色背景上添加一些黑色文本，并将图像保存为具有八色色板的 PNG 文件。你可以在下文章节中看到这一操作：

> MATT DOYLE, 2008

图 17-17

#### 将水印复制到图像

以下是创建水印图像的脚本。将此文件保存为 `watermark.php`。图 17-18 显示了示例结果。

```php
<?php
$MyImage = imagecreatefromjpeg( "lucky.jpg" );
$MyCopyright = imagecreatefrompng( "copyright.png" );

$dstWidth = imagesx($MyImage);
$dstHeight = imagesy($MyImage);
$srcWidth = imagesx($MyCopyright);
$srcHeight = imagesy($MyCopyright);

$destX = ($dstWidth - $srcWidth) / 2;
$destY = ($dstHeight - $srcHeight) / 2;

imagecopy($MyImage, $MyCopyright, $destX, $destY, 0, 0, $srcWidth, $srcHeight);

header( "Content-type: image/jpeg" );
imagejpeg($MyImage);
imagedestroy($MyImage);
imagedestroy($MyCopyright);
?>
```

## 第三部分：PHP 实践

首先，你打开想要添加水印的原始图像：

```php
$MyImage = imagecreatefromjpeg("lucky.jpg" );
```

然后打开版权图像。因为它是 PNG 文件，所以使用 `imagecreatefrompng` 函数打开文件：

```php
$MyCopyright = imagecreatefrompng("copyright.png" );
```

为了将版权信息放置在图像中心，你必须知道每个图像的尺寸。`imagesx()` 函数返回图像的宽度，`imagesy()` 函数返回图像的高度。这两个函数都接受你想要获取宽度或高度的图像资源。脚本获取原始图像和版权信息的宽度及高度：

```php
$destWidth = imagesx($myImage);
$destHeight = imagesy($myImage);
$srcWidth = imagesx($myCopyright);
$srcHeight = imagesy($myCopyright);
```

现在你需要计算版权信息需要放置的左上角位置。要计算该角的 x 坐标，从图像宽度中减去版权信息的宽度，并将差值除以二。要获取 y 坐标，则对图像高度进行相同的计算：

```php
$destX = ($destWidth - $srcWidth) / 2;
$destY = ($destHeight - $srcHeight) / 2;
```

一旦知道了将版权信息放在哪里，就可以将其复制到要加水印的图像中。执行此操作的函数是 `imagecopy()`：

```php
imagecopy($myImage, $myCopyright, $destX, $destY, 0, 0, $srcWidth, $srcHeight);
```

`imagecopy()` 接受八个参数如下：

- 第一个参数是要复制数据的目标图像——即你想要加水印的图像
- 第二个参数是数据来源的图像——即版权图像
- 第三和第四个参数是目标图像中复制数据位置的 x 和 y 坐标。它们标记了正在复制的数据块的左上角
- 接下来两个参数是源图像中要复制数据块的左上角 x 和 y 坐标
- 最后两个参数表示要复制块的宽度和高度

在这种情况下，你希望复制整张图像，因此使用 0, 0 作为要复制块的左上角位置，并将版权图像的整个宽度和高度作为该块的宽度和高度。

数据复制完成后，像往常一样输出图像。记得清理两张图像都使用的内存：

```php
header( "Content-type: image/jpeg" );
imagejpeg($myImage);
imagedestroy($myImage);
imagedestroy($MyCopyright);
?>
```

![](img/ede05b7b77968b82cbd9a513122fb183_562_0.png)

图 17-18

这里有一个小问题。如你清楚看到的，图像被遮挡了。在下一节中，我们将完善脚本，让你看到更多的图像内容。

### 处理透明度

与其原样复制整个图像，不如只复制背景。为了这样做，你需要将白色设为透明。

## 第三部分：PHP 实践

首先，你需要获取白色的索引。你有两种方法可以做到。你可以使用 `imageat()` 函数获取精确像素颜色：

```php
$white = imageat($myCopyright, $x, $y);
```

或者，你可以使用 `imagecolat()` 并传入颜色的 RGB 值：

```php
$white = imagecolat($myCopyright, $red, $green, $blue);
```

后方法的缺点是图像中不存在该颜色。如果你将图像保存为 JPEG，可能会有细微差异。因此你可以使用 `imagecolortransparent()` 将颜色设为透明。在 `watermark.php` 的适当位置添加以下代码行：

```php
$destY = ($destHeight - $srcHeight) / 2;
$white = imagecolat($myCopyright, 255, 255, 255);
imagecolortparent($myCopyright, $white);
```

```php
imagecopy($myImage, $myCopyright, $destX, $destY, 0, 0, $srcWidth, $srcHeight);
```

现在脚本的输出（见图 17-19）看起来更有前景了。

## 第17 章：使用 PHP 生成图像

![](img/ede05b7b77968b82cbd9a513122fb183_564_0.png)

图 17-19

### 处理不透明度

图像的不透明度定义了图像像素的透明程度。图像范围从完全透明到不透明（完全无法穿透图像）。在上一节的 `imagecopy()` 函数中，版权信息的黑色文本是不透明的，而其白色背景是透明的。为了让水印不那么明显，你可以使用 `imagecopymerge()` 函数赋予图像透明度。该函数的工作方式与 `imagecopy()` 函数完全相同，只是你还额外提供了第九个参数，它控制被复制图像的透明度。值为0意味着复制的图像是完全透明的，你在最终图像中看不到它；而值为100意味着复制的图像是完全不透明的——函数运行方式类似于 `imagecopy()`。因此，你只需将 `watermark.php` 脚本中的这一行：

```php
imagecopy($myImage, $myCopyright, $destX, $destY, 0, 0, $srcWidth, $srcHeight);
```

改为：

```php
imagecopymerge($myImage, $myCopyright, $destX, $destY, 0, 0, $srcWidth, $srcHeight, 50);
```

# 第三部分：实战中的 PHP

在这里，你已经将 `imagecopy()` 函数替换为 `imagecopymerge()`，并提供了一个 50 的透明度值——这是透明和不透明之间的中间值。脚本的输出现在看起来更像一个水印，如图 17-20 所示。

![](img/ede05b7b77968b82cbd9a513122fb183_565_0.png)

如果你对处理图像中的透明效果感兴趣，请查看 PHP 手册（http://www.php.net/manual/en/ref.image.php）中的 `imagecolorallocate-alpha()` 和 `imagealphablending()` 函数。虽然你无法完全复制专业图形程序中可以获得的所有效果，但你仍然可以创建一些有趣的特效。

下一节也涉及处理现有的图像，但这次你将将其缩小为缩略图。

# 创建缩略图

创建图像缩略图的方法与应用水印类似，不同之处在于复制的方向相反——不是将小图像复制到大图中，而是将图像复制到一个新的较小的图像中，并在过程中进行缩放。这里有一个创建缩略图的示例脚本：

```php
<?php
$mainImage = imagecreatefromjpeg("lucky.jpg");
```

# 第 17 章：使用 PHP 生成图像

```php
$mainWidth = imagesx($mainImage);
$mainHeight = imagesy($mainImage);

$thumbWidth = intval($mainWidth / 4);
$thumbHeight = intval($mainHeight / 4);

$myThumbnail = imagecreatruecolor($thumbWidth, $thumbHeight);

imagecopyresampled($myThumbnail, $mainImage, 0, 0, 0, 0, $thumbWidth, $thumbHeight, $mainWidth, $mainHeight);

header("Content-type: image/jpeg");
imagejpeg($myThumbnail);
imagedestroy($myThumbnail);
imagedestroy($mainImage);
?>
```

将脚本保存为 `thumbnail.php` 并放在你的文档根目录下，将第二行的 `lucky.jpg` 替换为你选择的图像（保存在相同文件夹中）。在 Web 浏览器中打开其 URL 运行脚本。图 17-22 显示了运行示例。

以下是脚本的工作原理。首先，它打开图像以创建缩略图：

```php
$mainImage = imagecreatefromjpeg("lucky.jpg");
```

接下来，它使用 `imagesx()` 和 `imagesy()` 函数获取原始图像的宽高度。你需要计算新缩略图的尺寸：
