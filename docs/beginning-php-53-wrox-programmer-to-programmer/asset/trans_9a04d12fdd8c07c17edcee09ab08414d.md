

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

## 应用水印

如果你正在开发一个显示原创艺术品或照片的网站，你可能希望保护你或客户的知识产权不被盗用。一种常用方法是应用水印，以防止他人将其据为己有。操作方法。

首先，在 Photoshop 等图像编辑器中创建一个简单的版权图像（如图 17-17 所示）。为此，在白色背景上添加一些黑色文本，并将图像保存为具有八色色板的 PNG 文件。你可以在下文章节中看到这一操作：

> MATT DOYLE, 2008

图 17-17

## 将水印复制到图像

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

## 处理透明度

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

## 处理不透明度

图像的不透明度定义了图像像素的透明程度。图像范围从完全透明到不透明（完全无法穿透图像）。在上一节的 `imagecopy()` 函数中，版权信息的黑色文本是不透明的，而其白色背景是透明的。为了让水印不那么明显，你可以使用 `imagecopymerge()` 函数赋予图像透明度。该函数的工作方式与 `imagecopy()` 函数完全相同，只是你还额外提供了第九个参数，它控制被复制图像的透明度。值为0意味着复制的图像是完全透明的，你在最终图像中看不到它；而值为100意味着复制的图像是完全不透明的——函数运行方式类似于 `imagecopy()`。因此，你只需将 `watermark.php` 脚本中的这一行：

```php
imagecopy($myImage, $myCopyright, $destX, $destY, 0, 0, $srcWidth, $srcHeight);
```

改为：

```php
imagecopymerge($myImage, $myCopyright, $destX, $destY, 0, 0, $srcWidth, $srcHeight, 50);
```

