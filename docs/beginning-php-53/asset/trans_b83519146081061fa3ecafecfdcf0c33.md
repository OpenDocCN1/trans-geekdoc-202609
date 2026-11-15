

![](img/1ddec54918a4802eb9b4febec3d4e7f6_559_0.png)

图 17-16

## 工作原理

代码相对简单，不应该出现任何问题。imagecreatefromjpeg() 函数从现有图像创建一个新的图像资源：

```
$myImage = imagecreatefromjpeg( "lucky.jpg" );
```

然后，脚本向 Web 浏览器发送一个标头，告知其预期接收一些 JPEG 图像数据：

```
header( "Content-type: image/jpeg" );
```

剩下要做的就是发送数据，并从内存中清理图像：

```
imagejpeg( $myImage );
imagedestroy( $myImage );
```

当然，脚本所做的事，你用纯 HTML 也可以自己完成，因此你可能想知道这样做有什么意义。嗯，能够打开现有图像并在将其发送到浏览器之前对其进行处理，这在许多方面都很有用。使用 GD 图像函数可以对图像执行的一些操作包括：

- 调整图像大小以创建用于显示的缩略图
- 降低图像质量以加快加载速度
- [ ] 用描述性文本或标题对图像进行注释
- [ ] 将另一图像的一部分复制到其中，以便用作版权水印

在以下各节中，你将学习如何将水印应用到图像，以及如何创建图像的缩略图。

## 应用水印

如果你正在开发一个展示原创艺术或照片的网站，你可能希望保护你或你客户的知识产权不被窃取。一种常见的方法是在图像上应用水印，以阻止他人将其据为己有。具体做法如下。

首先，在 Photoshop 等图像编辑器中创建一个简单的版权图像（如图 17-17 所示）。具体来说，在白色背景上添加一些黑色文本，并将图像另存为带有八色调色板的 PNG 文件。（这样做的原因将在本节稍后说明。）

© MATT DOYLE, 2008

图 17-17

## 将水印复制到图像中

下面是创建带水印图像的脚本。将此文件另存为 watermark.php。图 17-18 显示了一个示例结果。

```php
<?php
$myImage = imagecreatefromjpeg ( "lucky.jpg" );
$myCopyright = imagecreatefrompng ( "copyright.png" );

$destWidth = imagesx( $myImage );
$destHeight = imagesy( $myImage );
$srcWidth = imagesx( $myCopyright );
$srcHeight = imagesy( $myCopyright );

$destX = ($destWidth - $srcWidth) / 2;
$destY = ($destHeight - $srcHeight) / 2;

imagecopy( $myImage, $myCopyright, $destX, $destY, 0, 0, $srcWidth,
$srcHeight );

header ( "Content-type: image/jpeg" );
imagejpeg( $myImage );
imagedestroy( $myImage );
imagedestroy( $myCopyright );
?>
```

## 第三部分：在实际中使用 PHP

首先，打开你想要加水印的原始图像：

```
<?php
$myImage = imagecreatefromjpeg( "lucky.jpg" );
```

然后打开你的版权图像。因为它是 PNG 文件，所以使用 imagecreatefrompng() 函数来打开该文件：

```
$myCopyright = imagecreatefrompng( "copyright.png" );
```

要将版权声明定位在图像中心，你需要知道每幅图像的尺寸。imagesx() 函数返回图像的宽度，imagesy() 函数返回图像的高度。这两个函数都接受你想要获取宽度或高度的图像资源。脚本获取原始图像和版权通知的宽度和高度：

```
$destWidth = imagesx( $myImage );
$destHeight = imagesy( $myImage );
$srcWidth = imagesx( $myCopyright );
$srcHeight = imagesy( $myCopyright );
```

现在你需要计算版权通知需要放置的左上角位置。要计算角的 x 位置，用待加水印图像的宽度减去版权通知的宽度，然后将差值除以二。要获取 y 位置，使用图像高度执行相同的计算：

```
$destX = ($destWidth - $srcWidth) / 2;
$destY = ($destHeight - $srcHeight) / 2;
```

一旦知道版权通知应放置的位置，你就可以将其复制到待加水印的图像中。执行此操作的函数是 imagecopy()：

```
imagecopy( $myImage, $myCopyright, $destX, $destY, 0, 0, $srcWidth,
$srcHeight );
```

imagecopy() 接受八个参数，如下所示：

- 第一个参数是要复制数据的目标图像——即你想要加水印的图像
- 第二个参数是数据被复制的来源图像——即版权图像
- 第三个和第四个参数是目标图像中要复制图像数据的位置的 x 和 y 坐标。它们标记正在复制的数据块的左上角
- 接下来的两个参数是指示源图像中要复制的数据块左上角的 x 和 y 坐标
- 最后两个参数指示要复制的数据块的宽度和高度

在此示例中，你希望整个图像被复制过去，因此你使用 `0, 0` 作为要复制的数据块的左上角位置，并将版权图像的整个宽度和高度作为数据块的宽度和高度。

数据复制完成后，像往常一样输出图像。请记住清理两个图像所使用的内存：

```
header ( "Content-type: image/jpeg" ) ;
imagejpeg ( $myImage ) ;
imagedestroy ( $myImage ) ;
imagedestroy ( $myCopyright ) ;
?>
```

![](img/1ddec54918a4802eb9b4febec3d4e7f6_562_0.png)

图 17-18

这里有一个小问题。如图所示，图像的大部分现在被遮挡了。在下一节中，你将改进脚本，以便能看到更多图像内容。

## 使用透明度

与其原封不动地复制整个版权图像，不如只复制黑色文本。为此，你需要使版权图像的白色区域变为透明。

首先，你需要获取图像中白色的颜色索引。有多种方法可以做到这一点。你可以使用 imagecolorat() 函数来获取精确像素位置处颜色的调色板索引：

```
$white = imagecolorat( $myCopyright, $x, $y );
```

或者，你可以使用 imagecolorexact()，传入要从调色板中获取的颜色的 RGB 值：

```
$white = imagecolorexact( $myCopyright, $red, $green, $blue );
```

后一种方法的唯一缺点是，如果颜色不存在于图像的颜色调色板中，函数不会返回有效的颜色索引。

之前，你将版权图像另存为 8 位颜色的 PNG。这确保了你有一个小的调色板可供使用，并且图像的白色背景在整个图像中保持一致。如果你将图像另存为带有数百万种颜色的 JPEG，可能会在白色背景中产生细微的差异，使你很难准确定位想要变为透明的白色。通过将图像另存为颜色数量较少的 PNG，你可以避免这个问题。

因此，你可以继续使用 imagecolorexact() 函数来获取白色的颜色索引。获取颜色索引后，你可以使用 imagecolortransparent() 函数使该颜色在图像中变为透明。该函数接受两个参数：图像资源和要设为透明的颜色索引。

在你先前创建的 watermark.php 脚本中，适当位置添加以下两行代码：

```
$destY = ($destHeight - $srcHeight) / 2;
```

```
$white = imagecolorexact( $myCopyright, 255, 255, 255 );
imagecolortransparent( $myCopyright, $white );
```

```
imagecopy( $myImage, $myCopyright, $destX, $destY, 0, 0, $srcWidth,
$srcHeight );
```

现在脚本的输出（参见图 17-19）看起来更有希望了。

![](img/1ddec54918a4802eb9b4febec3d4e7f6_564_0.png)

图 17-19

## 使用不透明度

图像的不透明度定义了图像像素是透明还是不透明。图像可以从完全透明（看得见透过）到完全不透明（完全看不见透过）。在上一节的 imagecopy() 函数中，版权消息的黑色文本是不透明的，而其白色背景是透明的。

要使水印不那么明显，你可以使用 imagecopymerge() 函数为复制的图像赋予一定程度的透明度。该函数的工作方式与 imagecopy() 函数完全相同，只不过你还需要提供一个第九个参数，用于控制复制图像的透明度或不透明度。值为零表示复制的图像完全透明，在最终图像中不会看到它；而值为 100 表示复制的图像完全不透明，在这种情况下，函数的操作方式类似于 imagecopy() 函数。因此，你可以简单地更改 watermark.php 脚本中的这一行：

```
imagecopy( $myImage, $myCopyright, $destX, $destY, 0, 0, $srcWidth,
$srcHeight );
```

改为：

```
imagecopymerge( $myImage, $myCopyright, $destX, $destY, 0, 0, $srcWidth,
$srcHeight, 50 );
```

