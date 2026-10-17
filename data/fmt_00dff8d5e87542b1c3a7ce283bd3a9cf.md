
PHP 中的某些图像函数是始终可用的，但大多数函数都需要 GD2 库，该库在 PHP 中已包含，但默认未启用。更详细的安装说明可以在附录 A“安装 Apache、PHP 和 MySQL”中找到，但以下是针对 Unix 和 Windows 用户的简要说明。

在 Windows 下，只要你注册了 `php_gd2.dll` 扩展，PNG 和 JPEG 就会被自动支持。你可以通过从安装目录将 `php_gd2.dll` 文件复制到系统中来实现。你还必须通过删除 `php.ini` 文件中以下行开头的 `;` 符号取消注释：

```
extension=php_gd2.dll
```

如果你想处理 PNG，需要下载并安装 `libpng` 和 `zlib`，并以下选项配置 PHP：

```
--with-png-dir=/path/to/libpng
--with-zlib-dir=/path/to/zlib
```

对于 JPEG，你需要下载 JPEG 库并使用以下内容配置 PHP：

```
--with-jpeg-dir=/path/to/jpeg
```

最后，你将使用 `--with-gd` 配置 PHP。

# 了解图像格式

GD 库支持 PNG、JPEG、GIF 以及许多其他格式。让我们在接下来的章节中查看这些图像格式。

## JPEG

JPEG（读作 "jay-peg"）代表联合摄影专家小组（Joint Photographic Experts Group），JFIF 名称正式对应于标准之一。如果你不熟悉它们，JPEG 通常用于存储具有多种颜色的照片或其他图像。这种格式使用低压缩率将照片压缩到较小的文件中；这会导致图像质量的损失。这种格式不适用于线条画、文本或纯色块。你可以在官方网站 http://www.jpeg.org 更多关于 JPEG/JFIF 的信息。

## PNG

PNG（读作 "ping"）代表便携网络图形（Portable Network Graphics）。由于稍后讨论的原因，这种文件格式成为了 GIF（图形交换格式）的替代品。PNG 将该格式描述为无损图像格式，适用于包含文本、直线、标题和网站按钮等色块的图像。由于它是无损的，因此同一图像的 PNG 压缩版本通常与 GIF 压缩版本的大小相似。PNG 还提供了可变透明度、伽马校正和二维交错。你可以在官方网站 http://www.libpng.org/pub/png/libpng.html 更多关于 PNG 的信息。

## GIF

GIF 代表图形交换格式（Graphics Interchange Format）。这是一种广泛用于网络的压缩格式，用于存储包含文本、直线和单色块的图像。GIF 格式使用来自 24 位 RGB 空间的多达 256 种不同颜调色板。它支持动画，允许每一帧使用独立的 256 色调色板。颜色限制使得 GIF 不适用于复制照片和其他具有连续颜色的图像，但它非常适合简单的图像，如具有纯色区域的图形或标志。GIF 使用 LZW 数据压缩技术进行压缩，这可以在不降低质量的情况下减小文件大小。

# 创建图像

在 PHP 中创建图像的基本步骤如下：

1. 创建一个用于工作的画布图像

2. 在该画布上绘制形状或打印文本

3. 输出最终图形

4. 清理资源

让我们查看列表 21.1 所示的图像创建脚本。

### 列表 21.1 simplegraph.php——输出带标签的简单折线图

```php
<?php
// 设置图像画布
$height = 200;
$width = 200;
$im = imagecreatruecolor($width, $height);
$white = imagecolorallocate($im, 255, 255, 255);
$blue = imagecolorallocate($im, 0, 0, 255);

// 在图像上绘制
imagefill($im, 0, 0, $blue);
imageline($im, 0, 0, $width, $height, $white);
imagestring($im, 4, 50, 150, 'Sales', $white);

// 输出图像
header('Content-type: image/png');
imagepng($im);

// 清理
imagedestroy($im);
?>
```

运行此脚本的输出如图 21.1 所示。

![](img/654520c37415debd4290b9b4aa2c03f2_483_0.png)

图 21.1 脚本绘制了一个蓝色背景，然后为图像添加了线条和文本标签

现在让我们逐个介绍创建此图像的步骤。

## 创建画布图像

要在 PHP 中开始构建或更改图像，你需要创建一个图像标识符。实现此操作有两种基本方法。一种是创建一个空白画布，你可以通过 `imagecreatetruecolor()` 函数来实现，并在此脚本中通过以下代码实现：

```
$im = imagecreatruecolor($width, $height);
```

该函数接受图像标识符、绘图区域的起始坐标（x 和 y）以及填充颜色作为参数。

注意

图像的坐标从左上角开始，即 x=0, y=0。图像的右下角为 x=`$width`, y=`$height`。这在计算机图形中是常的，与典型的数学绘图惯例相反，请务注意！

接下来，你从图像的左上角 (0, 0) 到右下角 (`$width`, `$height`) 画一条线：

```
imagestring($im, 0, 0, $width, $height, $width);
```

该函数接受图像标识符、线条的起始点 x 和 y、终点，以及颜色作为参数。

最后，你为图表添加一个标签：

```
imagestring($im, 4, 50, 150, 'Sales', $width);
```

`imagestring()` 函数接受的参数略有不同。该函数的原型为：

```
int imagestring(resource img, int font, int x, int y, string text, int color);
```

字体接受图像标识符、字体、开始写入文本的 x 和 y 坐标、要写入文本以及颜色。

字体是 1 到 5 之间的数字。这些数字代表 latin2 编码中的一组内置字体，数字越大字体越大。作为这些字体的替代，你可以使用 TrueType 字体或 PostScript Type 1 字体。这些字体组都有对应的函数集。我们在下一个示例中使用 TrueType 函数。

使用这些替代函数集的一个很好的原因是，通过 `imagestring()` 和相关函数（如 `imagechar()` 向图像写入字符）编写的文本是锯齿的（aliased）。TrueType 和 PostScript 字体产生抗锯齿文本。

如果你不确定差异在哪里，请查看图 21.2。当字母中出现曲线或斜线时，锯齿文本看起来是锯齿状。曲线或角度是通过使用“阶梯”效果实现的。在抗锯齿图像中，当像素中出现曲线或角度时，会使用背景色和文本颜色之间的颜色来平滑文本的外观。

### 普通 vs 抗锯齿

图 21.2 普通文本看起来是锯齿状，尤其是在大字体下。抗锯齿平滑了字母的曲线和转角。

## 输出最终图形

你可以将图像直接输出到浏览器，也可以输出到文件。

在这个示例中，你将图像输出到浏览器。这是一个阶段阶段。首先，你需要告诉 Web 浏览器你正在输出图像而不是文本或 HTML。你通过使用 `header()` 函数设置图像的 MIME 类型：

```
header('Content-type: image/png');
```

通常，当你在浏览器中检索文件时，MIME 类型是 Web 服务器发送的内容内容。对于 HTML 或 PHP 页面（执行后），第一个内容是：

```
Content-Type: text/html
```

这告诉浏览器如何解释随后的数据。在这种情况下，你告诉浏览器你发送的是图像而不是通常的 HTML 输出。你可以通过使用 `header()` 函数来实现，它会发送 HTTP 头部字符串。需要注意的一点是，如果 PHP 在向浏览器输出任何内容时自动发送了 HTTP 头部，则 `header()` 函数将无法执行。然而，如果你有任何 `echo` 语句或在打开 PHP 标签之前有任何空格，HTTP 头部将被发送，当你尝试调用 `header()` 时将收到来自 PHP 的警告消息。但是，你可以在同一个脚本中多次调用 `header()` 函数来发送多个 HTTP 头部，尽管它们必须在向浏览器发送任何输出之前出现。

在发送头部数据后，你通过调用以下函数输出图像数据：

```
imagepng($im);
```

此调用将输出以 PNG 格式发送到浏览器。如果你想以不同的格式发送它，可以调用 `imagejpeg($im)`——已启用 JPEG 支持。你还需要先发送相应的头部，如下所示：

```
header('Content-type: image/jpeg');
```

你可以使用的第二种选项（作为之前所有选项的替代方案）是将图像写入文件而不是浏览器。你可以通过向 `imagepng($im, $filename)` 添加以下第二个参数（或用于其他支持格式的类似函数）来实现：

```
imagepng($im, $filename);
```

记住，所有关于从 PHP 写入文件的常规规则都适用（例如正确设置权限）。

## 清理

当你完成图像后，应该通过销毁标识符将你使用的资源返回给服务器。你可以通过调用 `imagedestroy()` 来：

```
imagedestroy($im);
```

## 使用自动生成的图像

由于头部只能发送一次，而且这是告诉浏览器你正在发送图像数据的唯一方法，因此在普通页面中嵌入动态创建的任何图像有点棘手。你可以通过以下三种方法实现：

- 你可以让整个页面由图像输出组成，就像我们在上一个示例中所做的那。

- 你可以之前提到的将图像写入文件，然后使用普通的 `<img>` 标签引用它。

- 你可以将图像放在普通页面中。

我们已经涵盖了前两种方法。让我们简单看看第三种方法。要使用这种方法，请包含以下：

```html
<img src="simplegraph.php" height="200" width="200" alt="Sales" />
```

不是直接放入 PNG、JPEG 或 GIF，而是调用生成图像的 PHP 脚本。这允许你使用脚本生成图像，如图 21.3 所示。

## 使用文本和字体创建图像

让我们来看一个创建图像更复杂的示例。能够编程地创建按钮是有用的。你可以轻松地构建具有斜角边缘等功能的按钮，你可能会发现使用 Photoshop、GIMP 或其他某些图形工具创建这些按钮比在 PHP 中更容易。

在这个示例中，你也使用了 TrueType 字体，以便能够使用抗锯齿文本。TrueType 字体函数有它们自己的特性，我们将讨论它们。

基本过程是获取文本并用它生成按钮。文本将在按钮上水平和垂直方向都居中，并以适合放入按钮的最大字体大小进行渲染。

我们为测试给生成器构建了一个前端。该界面如图 21.4 所示，它只是一个向 PHP 脚本发送几个变量的简单表单。

图 21.4 前端允许用户选择按钮颜色并输入所需的文本

你可以使用这种接口让程序自动生成网站。你也可以以内联方式调用脚本，动态生成网站的所有按钮，但这需要缓存来防止变得费时费力。

脚本的典型输出如图 21.5 所示。

图 21.5 此按钮由 make_button.php 脚本生成

```php
// 使用正确的按钮颜色创建图像，并检查尺寸
$im = imagecreatefrompng($button_color.'-button.png');

$width_image = imagesx($im);
$height_image = imagesy($im);

// 我们的图像在距离边缘需要 1 像素的边距
$width_image_wo_margins = $width_image - (2 * 18);
$height_image_wo_margins = $height_image - (2 * 18);

// 告诉 GD2 你想要使用的字体位置

// 对于 Windows，使用：
putenv('FONTPATH=C:\WINDOWS\Fonts');

// 对于 UNIX，使用字体文件夹的完整路径。
// 在此示例中，我们使用 DejaVu 字体族：
putenv('FONTPATH:/usr/share/fonts/truetype/dejavu');

$font_name = 'DejaVuSans';

// 计算字体大小是否合适，如果不合适则不断减小，直到合适为止
// 从在我们的按钮上合理容纳的最大尺寸开始
$font_size = 33;

do {
  $font_size--;

  // 找出该字体大小下的文本尺寸
  $bbox = imagettbbox($font_size, 0, $font_name, $button_text);

  $right_text = $bbox[2]; // 右坐标
  $left_text = $bbox[0]; // 左坐标
  $width_text = $right_text - $left_text; // 它有多宽？
  $height_text = abs($bbox[1]); // 它有多高？
} while ($font_size > $width_image_wo_margins ||
  $height_text > $height_image_wo_margins);

if ($height_text > $height_image_wo_margins) {
  // 按钮上没有任何可读的字体大小合适
  echo '<p>提供的文本将无法适应按钮。</p>';
}
```

# 第 21 章.生成图像

```php
else {
  // 我们已经找到了一个合适的尺寸的字体大小。
  // 现在计算将其放在哪里。

  $text_x = $width_image / 2.0 - $width_text / 2.0;
  $text_y = $height_image / 2.0 - $height_text / 2.0;

  if ($left_text < 0) {
    $text_x += abs($left_text);
  }

  $above_line_text = abs($bbox[7]); // 在基线之距离；
  $text_y += $above_line_text; // 添加基线因子

  $text_y -= 2; // 针对模板形状的调整因子

  $white = imagecolorallocate($im, 255, 255, 255);

  imagettext($im, $font_size, 0, $text_x, $text_y, $white,
    $font_name, $button_text);

  header('Content-type: image/png');
  imagepng($im);

  // 清理资源
  imagedestroy($im);
}
```

这是我们迄为止见过的最长的脚本之一。让我们逐段分析它。

脚本开始于一些基础的错误检查，并设置了你要在其上面工作的画布。

## 设置基础画布

在列表 21.2 中，你不是从零开始，而是从一个现有的按钮图像开始基础工作。你在基础（basic red）中提供了三种颜色：红色 (`red-button.png`)、绿色 (`green-button.png`) 和蓝色 (`blue-button.png`)。

用户选择的颜色存储在表单的 `$button-color` 变量中。

你首先从全局变量 `$_POST` 中提取颜色，并根据相应的按钮设置一个新的图像标识符：

```php
$button-color = $_POST['button-color'];
```

然而，在继续创建该标识符之前，脚本会检查 `button-text` 和 `button-color` 是否都有值，如果没有，脚本将结束并在屏幕上产生一条消息。否则，脚本将移动到创建新的图像标识符：

`$im = imagecreatefrompng($color->'--button.png');`

函数 `imagecreatefrompng()` 将 PNG 的文件名作为参数，并返回一个包含该 PNG 副本的新型图像标识符。请注意，这不会以任何方式修改 PNG。如果支持，你可以以相同的方式使用 `imagecreatefromjpeg()` 和 `imagecreatefromgif()` 函数。

> 注意

> 调用 `imagecreatefrompng()` 仅在内存中创建图像。要将图像保存到文件或输出到浏览器，你必须使用 `imagepng()` 函数。你很快就会讨论这一点，但你首先需要对你生成的图像进行其他工作。

## 在按钮上拟合文本

用户通过表单输入的文本在从 `$_POST` 全局变量提取后被存储在 `$button_text` 变量中。接下来你需要做的是以能够容纳的最大字体大小在按钮上打印文本。你通过迭代，或者严格地说，通过试错法来实现这一点。

你首先设置了一些相关的变量。前两个是按钮图像的高度和宽度：

```php
$width_image = imagesx($im);
$height_image = imagesy($im);
```

第二个代表距离按钮边缘的边距。按钮图像是倒角的，因此你需要在边缘周围留出空间。如果你使用不同的图像，这个数字将会不同。在这种情况下，每边的边距为 18 像素：

```php
$width_image_wo_margins = $width_image - (2 * 18);
$height_image_wo_margins = $height_image - (2 * 18);
```

你还需要设置初始字体大小。从 32 开始（实际上是 33，但你稍后会减小它），因为这是在按钮上能容纳的最大字体：

`$font_size = 33;`

使用 GD2，你需要通过设置环境变量来告诉它你的字体在哪里：
