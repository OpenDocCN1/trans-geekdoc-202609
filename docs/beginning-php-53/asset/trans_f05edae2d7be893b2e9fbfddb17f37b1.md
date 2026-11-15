

- 文本颜色，作为颜色索引（例如由 imagecolorallocate() 返回）
- 服务器硬盘上字体（.ttf）文件的完整路径
- 要绘制的文本字符串

imagefttext() 绘制文本，然后返回一个由八个元素组成的数组，表示围绕绘制文本的边界框的四个角点：

| 元素索引 | 说明 |
|---|---|
| 0 | 左下角的 x 坐标 |
| 1 | 左下角的 y 坐标 |
| 2 | 右下角的 x 坐标 |
| 3 | 右下角的 y 坐标 |
| 4 | 右上角的 x 坐标 |
| 5 | 右上角的 y 坐标 |
| 6 | 左上角的 x 坐标 |
| 7 | 左上角的 y 坐标 |

这意味着你可以确切地了解绘制的文本在图像中占用了多少空间。如果你想绘制与刚刚绘制的文本相对定位的更多文本或形状，这将非常有用。

## 尝试一下：使用 TrueType 字体绘制文本

下面是一个使用 TrueType 字体显示文本的示例脚本。将代码保存为文档根目录中的 truetype.php，并在 Web 浏览器中运行该脚本。（如果你没有在 /usr/share/fonts/truetype/ttf-bitstream-vera/Vera.ttf 处安装 Vera 字体，请将脚本更改为指向你已安装的 TrueType 字体。）

```php
<?php
$textImage = imagecreate( 200, 120 );
$white = imagecolorallocate( $textImage, 255, 255, 255 );
$black = imagecolorallocate( $textImage, 0, 0, 0 );
imagefttext( $textImage, 16, 0, 10, 50, $black, "/usr/share/fonts/truetype/ttf-bitstream-vera/Vera.ttf", "Vera, 16 pixels" );
header( "Content-type: image/png" );
imagepng( $textImage );
imagedestroy( $textImage );
?>
```

图 17-24 显示了生成的文本。

![](img/1ddec54918a4802eb9b4febec3d4e7f6_572_0.png)

图 17-24

## 工作原理

首先，脚本创建一个空白图像并分配两种颜色：

```php
<?php
$textImage = imagecreate( 200, 120 );
$white = imagecolorallocate( $textImage, 255, 255, 255 );
$black = imagecolorallocate( $textImage, 0, 0, 0 );
?>
```

然后，通过调用 imagefttext() 将字符串绘制到图像上：

```php
imagefttext( $textImage, 16, 0, 10, 50, $black, "/usr/share/fonts/truetype/ttf-bitstream-vera/Vera.ttf", "Vera, 16 pixels" );
```

最后，脚本输出生成的图像：

```php
header( "Content-type: image/png" );
imagepng( $textImage );
imagedestroy( $textImage );
?>
```

要演示如何绘制旋转文本，请更改以下行：

```php
imagefttext( $textImage, 16, 0, 10, 50, $black, "/usr/share/fonts/truetype/ttf-bitstream-vera/Vera.ttf", "Vera, 16 pixels" );
```

改为：

```php
imagefttext( $textImage, 16, -30, 10, 30, $black, "/usr/share/fonts/truetype/ttf-bitstream-vera/Vera.ttf", "Vera, 16 pixels" );
```

唯一的变化是，你现在以 –30 度方向而不是零度绘制文本。旋转方向为逆时针，因此负数会使文本以顺时针方向倾斜。如果零度是钟面的三点钟方向，那么顺时针 30 度就是钟面的四点钟方向。你可以在图 17-25 中看到结果。

![](img/1ddec54918a4802eb9b4febec3d4e7f6_573_0.png)

图 17-25

## 总结

本章讨论了如何使用 PHP 创建、操作和输出图像。在本章中，你学习了：

- 了解计算机图像的基础知识，包括颜色、坐标系统和图像类型
- 了解如何使用 `imagecreate()` 及相关函数创建位图图像，以及在图像中分配颜色
- 了解如何使用 `imagejpeg()`、`imagegif()` 和 `imagepng()` 将图像输出到 Web 浏览器或文件
- 了解了一些 PHP 的绘图函数，包括 `imagesetpixel()`、`imageline()`、`imagerectangle()`、`imageellipse()`、`imagearc()` 和 `imagepolygon()`
- 了解如何使用 `imagecreatefromjpeg()`、`imagecreatefromgif()` 和 `imagecreatefrompng()` 打开现有图像以便对其进行操作。例如，你将水印图像应用到现有照片上，并基于现有图像创建了缩略图。在此过程中，你探索了透明度和不透明度的概念
- 使用 `imagestring()` 和 `imagefttext()` 将文本添加到图像中

生成和输出图像的能力进一步扩展了 PHP 脚本的功能。例如，你可以创建仅用 HTML 很难实现的内容，例如饼图和其他图表。此外，由于你可以使用 PHP 代码操作现有图像，因此执行创建图库缩略图和批量处理图像等任务变得轻而易举。

下一章将探讨一个完全不同的主题：正则表达式。这些强大的工具可以让你以各种有用的方式搜索和操作文本字符串。不过，在阅读之前，请先看看下面两个图像操作练习。

## 练习

下面是一些练习，帮助你练习本章学习的一些技术。你也可以扩展这些练习以应用于现实世界示例。练习的解答在附录 A 中。

1. 创建一个 PHP 脚本，打开图像文件，在图像上添加一个一像素的黑色边框，并将生成的图像输出到浏览器。
2. 使用 disk_total_space() 和 disk_free_space() 函数，以图形方式显示 Web 服务器硬盘上已使用的磁盘空间大小。

## 使用正则表达式进行字符串匹配

在第 5 章中，你探索了 PHP 许多强大的字符串操作函数，例如用于在字符串中查找文本的 `strstr()` 和用于搜索和替换字符串中文本的 `str_replace()`。

在本章中，你将学习 PHP 更强大的正则表达式函数。这些函数比常规字符串匹配函数灵活得多，因为它们让你将字符串与一组字符的 *模式* 进行比较，而不是与固定字符串进行比较。例如，你可以搜索一个字符串，查找由恰好三个数字组成的字符模式，后面跟一个逗号或句点，再后面跟一到四个字母。

在正则表达式中，你使用 `?` 和 `^` 等特殊符号来指定模式。由于模式可能变得非常复杂，初学者可能难以理解正则表达式。但是，通过一些练习以及本章中的一些提示，你会发现你可以更快速、更轻松地读取正则表达式。

虽然正则表达式对 PHP 编程并非必不可少——你通常可以使用字符串匹配函数和一两个循环来完成类似的工作——但当你需要匹配模式时，它们是你的最佳选择。一方面，单个正则表达式通常比一整套字符串匹配和循环要紧凑直观得多。该表达式通常运行速度也快得多。

读完本章后，你将了解：

- **将字符串与正则表达式匹配：** 你将探索 PHP 的 `preg_match()` 和 `preg_match_all()` 函数，这些函数允许你将正则表达式应用于字符串以查找匹配项
- **正则表达式语法的方方面面：** 你将了解正则表达式中使用的所有特殊字符，以及如何匹配字符类型、一次匹配多个字符、字符的替代组等等
- **搜索整个字符串数组：** 你可以使用 PHP 的 preg_grep() 函数遍历字符串数组，查找与正则表达式匹配的文本
- **替换文本：** 你将学习 PHP 的 preg_replace() 和 preg_replace_callback() 函数，用于将字符串中匹配的文本替换为不同的文本
- **模式修饰符：** 你可以通过向表达式添加某些模式修饰符来使正则表达式更加灵活
- **分割字符串：** 就像你可以使用 explode() 使用固定分隔符分割字符串一样，你可以使用 preg_split() 基于正则表达式分割字符串

你还将学习如何使用正则表达式匹配来搜索网页中的链接 URL，并验证用户输入（正则表达式的非常常见用途）以及操作字符串。

本章专门使用一种称为 PCRE（Perl 兼容正则表达式）的 PHP 正则表达式类型。PHP 的旧版本支持另一种称为 POSIX Extended 的正则表达式类型。其中包括 ereg()、ereg_replace() 和 split() 等函数。从 PHP 5.3 版本开始，POSIX Extended 正则表达式已被弃用，并将在 PHP 6 中删除。如果你有使用 POSIX Extended 函数的现有代码，现在是将它们替换为 PCRE 等价函数的好时机。

## 什么是正则表达式？

正则表达式为你提供了一种特殊的语法，用于在字符串中搜索文本模式。在最简单的形式下，正则表达式只是一个搜索文本字符串，就像你传递给 strstr() 的那样（参见第 5 章）。正则表达式被封装在分隔符中（通常是斜杠）。例如，这个简单的正则表达式搜索目标字符串中任意位置的单词“world”：

```
/world/
```

不过，这是一个简单的示例（事实上，在这种情况下，使用更快的 strstr() 会更好）。一旦你插入具有特殊含义的其他字符，正则表达式就开始变得有用。例如，表达式开头的插入符（^）字符意味着“后面的字符必须出现在目标字符串的开头”：

```
/^world/
```

此示例将匹配字符串“world”，但不匹配字符串“hello, world”（因为“world”不在字符串开头）。

下面是你可以使用正则表达式执行的一些简单搜索示例：

- 单词“train”，但不包括单词“training”
- 至少一个数字，后跟单个字母 A、B 或 C
- 单词“hello”后跟五到十个其他字符，再后跟“world”
- 一到两个数字，后跟字母“st”、“nd”、“rd”或“th”，再后跟一个空格，再后跟三个字母（适用于识别字符串中嵌入的日期）

