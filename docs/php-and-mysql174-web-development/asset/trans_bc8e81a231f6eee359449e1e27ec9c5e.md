

# 绘制图形与数据图表化

471

这是条形的最大长度——从基线到右页边距——除以 100，因为图表将显示百分比值。

第二个值是画布所需的总高度：

```php
$height = $num_candidates * ($bar_height + $bar_spacing) + 50;
```

这个值基本上是每个条形的高度乘以条形数量，再加上用于标题的额外额度。第 3 部分如列表 21.5.3 所示。

# 列表 21.5.3 show_poll.php—第 3 部分设置图表，准备添加数据

```
****************************************************
设置基础图像
****************************************************
// 创建空白画布
$im = imagecreatruecolor($width,$height);

// 分配颜色
$white = imagecolorallocate($im, 255, 255, 255);
$blue = imagecolorallocate($im, 0, 64, 128);
$black = imagecolorallocate($im, 0, 0, 0);
$pink = imagecolorallocate($im, 255, 78, 243);

$text_color = $black;
$percent_color = $black;
$bg_color = $white;
$line_color = $black;
$bar_color = $blue;
$number_color = $pink;

// 创建用于绘制的“画布”
imagefilledrectangle($im, 0, 0, $width, $height, $bg_color);

// 在画布周围绘制轮廓
imagerectangle($im, 0, 0, $width-1, $height-1, $line_color);

// 添加标题
$title = 'Poll Results';
$title_dimensions = imagegetttfbox($title_size, 0, $font_name, $title);
$title_length = $title_dimensions[2] - $title_dimensions[0];
$title_height = abs($title_dimensions[7] - $title_dimensions[1]);
$title_above_line = abs($title_dimensions[5]);
$title_x = ($width-$title_length)/2; // x轴居中
$title_y = ($y - $title_height)/2 + $title_above_line; // y轴间隙居中


# 第 21 章：生成图像

```php
imagettext($im, $title_size, 0, $title_x, $title_y,
$text_color, $font_name, $title);
```

```
// 从第一个条形稍微上方画一条线
// 到最后一个条形稍微下方
imageline($im, $x, $y-5, $x, $height-15, $line_color);
```

在脚本的第 3 部分中，你使用了基础图像，分配了颜色，然后开始绘制图表。

你使用以下语句填充图表的背景：

```php
imagefilledrectangle($im, 0, 0, $width, $height, $bg_color);
```

正如你可能想象到的那样，`imagefilledrectangle()` 函数绘制一个填充矩形。第一个参数是图像标识符。你必须向它传递该矩形起点和终点的 x 和 y 坐标。这些点分别对应左上角和右下角。在这种情况下，你用背景颜色（最后一个参数，它是白色）填充了整个画布。

然后你调用

```php
imageline($im, 0, 0, $width-1, $height-1, $line_color);
```

在画布边缘绘制一个黑色轮廓。这绘制的是带轮廓的矩形而不是填充矩形。参数是相同的。注意矩形绘制到 `$width-1` 和 `$height-1`，即从 (0,0) 到这些值的宽度为高度的画布。如果你将其绘制到 `$width` 和 `$height`，则矩形将位于画布区域之外。

对于条形，你使用了与前一个脚本相同的逻辑，以便在图表上居中并写入标题。

```php
imageline($im, $x, $y-5, $x, $height-15, $line_color);
```

`imageline()` 函数在你指定的图像 ($im) 上从一组坐标 ($x, $y-5) 绘制一条线到另一组坐标 ($x, $height-15)，使用 $line_color 指定颜色。

在这种情况下，你从想要绘制第一个条形的地方稍微上方开始绘制条形，到画布底部稍微上方。

现在你准备好在图表上填充数据了。第 4 部分如列表 21.5.4 所示。

# 列表 21.5.4 show_poll.php—第 4 部分将实际数据绘制到图表并完成

```
************************************
// 将数据绘制到图表
************************************
// 获取数据库中的每行数据并绘制对应的条形
```

```php
while ($r_stmt->fetch())
{
if ($total_votes > 0) {
    $percent = intval($num_votes/$total_votes)*100;
} else {
    $percent = 0;
}

// 显示此值的百分比
$percent_dimensions = imagetfbbbox(main_size, 0, $font_name, $percent.'%');

$percent_length = $percent_dimensions[2] - $percent_dimensions[0];
（注：此处原文内容似乎不完整或存在格式错乱，已根据要求翻译了可见部分）
