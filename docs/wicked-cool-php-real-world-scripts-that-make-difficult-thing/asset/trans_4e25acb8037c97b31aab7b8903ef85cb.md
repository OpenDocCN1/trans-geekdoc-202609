
## 10 使用图像

![](img/19183d2b75bf6b509317c631c0e7b817_144_0.png)

本章将向你展示如何创建和操作 GIF 和 JPEG 等图像。你无法编写用于繁重图像操作或处理的脚本，例如在线字符识别（你的 Web 服务器限制了单个脚本可以执行的计算量），但在开发网站时，有许多小的图像操作非常实用。

### #66：创建 CAPTCHA（安全）图像

由于本书中的许多示例使用 cURL 连接网站并与其交互，你知道自动化网站交互有多容易。你也知道，如果你有一个希望只有真人才能使用的网站功能，就需要对其进行保护。否则，你至少可能会发现你的网站被垃圾评论完全淹没。解决这个问题的一种方法是动态绘制一张包含文本的图像，用户必须输入该文本才能发布评论（或执行其他仅限人类的操作，例如投票或评分）。如果你从用户那里得到了正确的文本，那么该用户很可能是人类。

这种测试被称为 CAPTCHA，即 *Completely Automated Public Turing Test to Tell Computers and Humans Apart*。它有两个缺点。首先，如果你是盲人，你无法读取 CAPTCHA 图像中的文本。视障人士可以借助语音软件朗读网页来使用互联网，但如果没有描述性的 alt 属性，该软件无法解读图像。CAPTCHA 会将这些用户锁定在外。

此外，CAPTCHA 并不总是有效。发垃圾邮件者一直在寻找绕过你障碍的方法。更有创意的方法之一是将 CAPTCHA 图像链接到垃圾邮件者拥有的色情网站，并贴上“输入此短语即可看到裸体！”的标签。然后某个孤独的家伙输入密码，该密码随后被传回你的网站。

牢记这两个缺点，你应该谨慎使用 CAPTCHA，并将其与替代方案（例如 Akismet 扫描器）进行权衡。此处介绍的 CAPTCHA 很简单（请参阅图 10-1 的屏幕截图），但它是有效的。要使用它，你的 PHP 必须安装带有 Freetype 支持的 GD 图形库。要查看是否有 GD 支持，请使用 phpinfo()，如第 21 页“#8: Revealing All of PHP’s Settings”中所述。如果一切正常，输出中将包含带有 Freetype 信息的 GD 部分。如果该部分不存在，请按照第 27 页“#18: Adding Extensions to PHP”中所述重新构建 PHP。

![](img/19183d2b75bf6b509317c631c0e7b817_145_0.png)

### 图 10-1: CAPTCHA 界面

你还需要将一种或多种字体与脚本放在同一目录中。最好选择至少半可读的字体。这个系统包含两个部分：

- 1. 主要部分是一个创建 CAPTCHA 图像的脚本。这些图像具有不规则的背景，带有奇怪的色彩区域和水平及垂直方向的线条。然后脚本选择一段通行短语，将其存储在 `$_SESSION['tt_pass']` 变量中，并以不同的方式绘制短语中的每个字母。最后，它发送图像输出。
- 2. 第二部分是一个脚本，用于将 CAPTCHA 表单的输入与 `$_SESSION['tt_pass']` 变量进行比较。此处的脚本是一个简单的演示，但由于图像生成脚本完成了大部分工作，你不需要做太多工作就可以使其适应自己的需求。

让我们从图像生成器开始。第一步是为图像生成器设置几个配置变量：通行短语的长度、图像大小以及查找字体的位置：

```php
<?php
/* captcha_image.php */

/* Passphrase length */
$pass_length = 4;

/* Image dimensions */
$width = 200;
$height = 60;

/* TTF font path */
$font_path = dirname(__FILE__);
```

现在让我们创建通行短语。与大多数密码不同，这不需要特别具有挑战性：没必要比必须的更让用户感到烦躁。

```php
session_start();

/* Create a passphrase. */
$passwd = "";
$i = 0;
while ($i < $pass_length) {
    $passwd .= chr(rand(97, 122));
    $i++;
}
```

我们将把通行短语放入会话变量中。因此，它绝不会以任何编码形式出现在任何页面中。这样可以避免需要想出一种别人会破解的编码。

```php
/** Store passphrase. */
$_SESSION["tt_pass"] = $passwd;
```

在绘制任何内容之前，我们要确保有可用于图像的字体。这段代码会在当前目录中创建一个字体列表。如果你希望加快这部分速度，可以将 $fonts 数组设置为一组 TrueType 字体文件名：

```php
/** Get a list of available fonts. */
$fonts = array();

if ($handle = opendir($font_path)) {
    while (false !== ($file = readdir($handle))) {
        /* Look for TTF fonts. */
        if (substr(strtolower($file), -4, 4) == '.ttf') {
            $fonts[] = $font_path . '/' . $file;
        }
    }
}
if (count($fonts) < 1) {
    die("No fonts found!");
}
```

客户端需要知道你发送的是什么类型的图像。此脚本创建 JPEG 图像，因此会发送相应的 MIME 类型。此外，我们不希望浏览器缓存图像，因此会发送多个用于使缓存失效的标头：

```php
/* Image header */
header("Content-Type: image/jpeg");
/* Invalidate cache. */
header("Expires: Mon, 01 Jul 1998 05:00:00 GMT");
header("Last-Modified: " . gmdate("D, d M Y H:i:s") . " GMT");
header("Cache-Control: no-store, no-cache, must-revalidate");
header("Cache-Control: post-check=0, pre-check=0", false);
header("Pragma: no-cache");
```

完成所有准备工作后，我们现在可以开始创建图像了。GD 函数以 image 前缀开头。要初始化彩色图像画布，请使用 imagecreatetruecolor()。

```php
/* Create image. */
$img = imagecreatetruecolor($width, $height);
```

我们要绘制的第一件事是一个用于覆盖整个背景的矩形。要绘制任何内容，你需要使用 imagecreatetruecolor() 在图像中分配一种颜色。此函数的第二、第三和第四个参数分别是颜色的红色、绿色和蓝色值。该值为 0 到 255 之间的整数，0 表示最暗，255 表示最亮。以下语句会创建一种随机的淡色：

```php
/* Fill background with a random shade of pastel. */
$bg = imagecolorallocate($img, rand(210,255), rand(210,255), rand(210,255));
```

现在让我们使用 imagefilledrectangle() 函数绘制该矩形。矩形与图像坐标轴平行，因此可以通过两个点来定义它：(0, 0) 和 ($width, $height)：

```php
imagefilledrectangle($img, 0, 0, $width, $height, $bg);
```

为了进一步复杂化背景，我们会在画布上绘制多个垂直方向的多边形。以下循环使用 imagefilledpolygon() 函数创建多边形。这与绘制矩形不同，因为多边形可以有三条或更多边且方向任意，因此你需要提供一个点数组作为参数（这里是 $poly_points），而不是两组坐标。

不要被这个循环的细节所困扰。它不是脚本中非常重要的部分。

```php
/** Make the background jaggedly by creating different-colored
four-cornered polygons to cover the background area. */
/** Create swaths between 10 and 30 pixels wide across the image. */
$right = rand(10, 30);
$left = 0;
while ($left < $width) {
    $poly_points = array(
        $left, 0,               /* Upper left */
        $right, 0,              /* Upper right */
        rand($right-25, $right+25), $height,   /* Lower right */
        rand($left-15, $left+15), $height);    /* Lower left */
    /** Create the polygon, using four points from the array. */
    $c = imagecolorallocate($img, rand(210,255), rand(210,255), rand(210,255));
    imagefilledpolygon($img, $poly_points, 4, $c);
    /** Advance to the right edge. */
    $random_amount = rand(10, 30);
    $left += $random_amount;
    $right += $random_amount;
}
```

为了进一步阻止可能使用 OCR 软件试图破解该系统的人，让我们在屏幕上绘制一些随机的水平线和垂直线。为了进一步增加变化，我们将为每张图像定义不同的线条颜色范围。通过为颜色选择随机的上下限，线条的强度可能会变化也可能不会变化，并且在每张图像之间的一致性也会有所不同。

```php
/** Choose base value range for vertical and horizontal lines. */
$c_min = rand(120, 185);
$c_max = rand(195, 280);
```

要绘制垂直线，请从左侧开始，选择一种粗细和一个轻微偏移来倾斜线条。然后选择一种颜色（使用上述界限），将线条作为多边形绘制，并再次向右移动一个随机距离：

```php
/** Draw random vertical lines across the width. */
$left = 0;
while ($left < $width) {
    $right = $left + rand(3, 7);
    $offset = rand(-3, 3);   /* Offset for angle */
    $line_points = array(
        $left, 0,       /* Upper left */
        $right, 0,      /* Upper right */
```
