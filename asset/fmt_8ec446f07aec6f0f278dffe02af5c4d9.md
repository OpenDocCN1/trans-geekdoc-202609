
| 132 | 在 `xml_parse()` 函数完成 XML 解析后，使用 `xml_parser_free()` 函数释放与解析器关联的内存。 |

| 133–135 | 停止作为 PHP 解析该页面，并关闭该页面的 HTML 标签。 |

### 将数据库内容导出到 XML 文件

虽然这不需要 PHP XML 函数，但使用 PHP 将数据从数据库导出到 XML 文件是获取结构化 XML 的极佳方法，你可以将其用于其他支持 XML 的应用程序。

数据库数据的性质非常适合在 XML 应用程序中使用。你已经创建了一个数据库结构。接下来的脚本提取地址录的内容，并将其存储在 XML 中。使用 PHP，你可以轻松地将这些数据导出到 XML 文件，或者在浏览器中显示。如果你在浏览器中检查是否遇到了某个特定元素，只需要检查该元素名称的大写版本即可。

| 33 | 生成一个 SQL 语句来选择表中的所有内容，并按姓氏、再名字对结果进行排序。 |

| 34 | 执行 SQL 查询并将结果存放在 `$result` 变量中。 |

| 35–52 | 使用 `while` 循环遍历结果集。 |

| 36–51 | 停止作为 PHP 继续页面的处理。由于我们正在输出大量数据，让服务器发送纯 XML 会比将每行都作为打印语句进行处理要简单。将当前行返回的每个结果作为 "contact" 元素的部分打印出来。在 "contact" 内部找到子元素包含了通讯录条目的详细信息。 |

| 52 | 关闭 `while` 循环。 |

| 53 | 通过打印根元素 `<addressbook>` 的闭合标签来结束 XML 的输出。 |

| 54 | 关闭在第 30 行开始的 `if` 语句。 |

| 55 | 结束脚本。 |

## 第 11 章：使用 PHP 生成动态图形

### 本章内容

* 概述

* GD 库

* 启用 GD 支持

* 使用 GD 生成图形

### 概述

PHP 能够动态生成和修改图像。若要在 PHP 中使用这些高级功能，你需要包含一些安装 PHP 时默认未包含的额外库。

### GD 库

PHP 提供了通过 GD 库来创建和操作图像的能力。GD 主页位于 [www.boutell.com/gd/](http://www.boutell.com/gd/)，其列出的 GD 定义为：

> “一个用于动态创建图像的 ANSI C 库。GD 可以创建 PNG 和 JPEG 图像等其他格式。GD 不创建 GIF 图像。”

此前，GD 被广泛用于创建 GIF 图像，但拥有 GIF 图像使用的 LZW 压缩算法专利的 Unisys 公司最近开始行使他们的专利权，GIF 创建功能随后从 GD 的功能列表中删除。

然而，GD 仍然可以用于创建 JPEG 和 PNG 图形，这两种格式都被大多数流行的 Web 浏览器支持。此外，GD 还支持创建 WBMP 图像，这种图像用于小型移动无线设备。

基本上，GD 可以很好地满足你脚本化图形创建的需求。请注意，GD 不是一个绘画程序。它可以通过向图像添加文本来操作现有图像，或者通过两个或多个现有图像创建新图像。

GD 在创建按钮图像以及在现有图像中嵌入说明时最为有用。

### 启用 GD 支持

GD 支持默认未启用。如果你使用的是 Windows，则必须启用扩展；如果你使用的是 Linux，则需要编译编译或链接该扩展。

#### 在 Windows 上启用 GD

在 Windows 上启用 GD 支持非常简单，因为 GD 的 DLL 文件已经过编译并包含在基础的 PHP Windows 安装包中。用文本编辑器打开你的 `php.ini` 文件，并搜索如下行：

```
extension_dir =  ./ 
```

此行应该指向 PHP 扩展文件所在的位置。如果你将扩展复制到了与 `php.ini` 文件相同的目录下，则不需要修改该行。如果你没有将 PHP 扩展移动到与 `php.ini` 相同的目录下，则需要编辑该行以指向正确的目录，例如：

```
extension_dir = C:\Apache\php\extensions 
```

接下来，在 `php.ini` 文件中找到如下部分：

```
;Windows Extensions 
```

该行后面会跟着几行。要启用 GD，取消包含 GD 的行开头的分号注释：

```
extension=gd.dll
```

取消该行的注释后，保存文件并重启 Apache 服务器。你可以使用图 11-1 所示的 `phpinfo()` 来验证 GD 是否正确安装。

##### 图 11-1 启用 GD 的 phpinfo() 结果

#### 在 Linux 上启用 GD

如果你使用 Apache 的 APXS 编译了 PHP，那么为 PHP 添加功能非常简单。在重新编译 PHP 之前，我建议你先删除 `config.cache` 并清理上次编译留下的文件。可以这样操作：

```
cd /path/to/php/source
rm config.cache
make clean
```

执行命令后，你会发现有很多文件被删除。不用担心，`make` 程序只是在清理重新编译时不需要的文件。如果不运行 `make clean` 命令，即使你没有更改任何内容，也可能会遇到一些问题，问题。

一旦你清理了上次编译的混乱，就可以开始新的编译。要编译带有 GD 支持的 PHP：

```
./configure --with-apxs=/usr/local/apache/apxs \
--with-gd \
--with-ttf
```

运行 `configure` 后，执行命令：

```
make
```

假设没有发生错误，你就可以执行命令：

```
make install
```

最后的命令将 `libphp4.so` 库复制到 `/path/to/apache/libexec/`。重启 Apache 以加载新库：

```
/path/to/apache/bin/apachectl restart
```

你可以通过 `phpinfo()` 函数验证 GD 是否正确安装。

### 使用 GD 生成图形

一旦你配置了 PHP 使用 GD 库，你就可以开始创建图形了。

#### 线和文本

使用 GD 库创建图像时使用的基础函数是 `ImageCreate()` 函数。

```
$length = 300; 
$width = 100;
$image = ImageCreate($length, $width);
```

```
$blue = ImageColorAllocate($image, 0, 0, 255); 
```

现在你已经创建了一个框并为它指定了颜色。现在剩下的工作是在浏览器中显示图像。要做到这一点，你还需要另外两行代码：

```
Header("Content-type: image/png"); 
ImagePNG($image);
```

第一行告诉浏览器期望一个 PNG 图像，第二行是将你创建的图像输出到浏览器的函数。不过，在你输入这些代码之前，让我们先添加一些文本。

既然你已经创建了基础图像，可以在其上添加一些形状。你可以为图像添加的最基础的“形状”是线。线段通过连接图像上的两个端点创建的。使用 `ImageLine()` 函数创建线条：

```
ImageLine($image, $x1, $y1, $x2, $y2, $color); 
```

你在 `ImageLine()` 函数中指定的点是 x,y 顶点，几乎就像数学中绘制点时使用的点，不同的是这里使用的网格略有不同。GD 中用于放置形状的网格从左上角的 x,y 点 0,0 开始。x 坐标向右移动，就像普通的数学图形一样。然而，y 坐标向下移动，而不是像数学图形那样向上移动，因此点 (10,20) 位于图像左上角右侧 10 像素、下方 20 像素处。

GD 还支持一些基本的字符串函数，允许你在图像上打印文本。你只能使用一种基本字体，并且只有五种大小，列在 表 11-1 中，但它对于不需要花哨字体的图形和图表效果良好。要向图像中添加文本：

```
IMageString($image, $fontSize, $x1, $y1, $string, 
$color);
```

##### 表 11-1. GD 字符串函数可字体大小

| 字体大小 || 字体 || 大小 |

| --- | --- | --- |

| 1 || gdFontTiny || 8 x 5 像素 |

| 2 || gdFontSmall || 13 x 6 像素 |

| 3 || gdFontMediumBold || 13 x 7 像素 |

| 4 || gdFontLarge || 15 x 8 像素 |

| 5 || gdFontGiant || 15 x 9 像素 |

下一个脚本创建了一个简单的图形，如图 11-2 所示，使用 `ImageLine()` 和 `ImageString()` 函数来说明图表的工作原理以及文本大小的外：

##### 脚本 11–1 gd\_grid.php

```
1.  <?
 2.  $height = 301;
 3.  $width = 301;
 4.  $image = ImageCreate($width, $height);
 5.  $white = ImageColorAllocate($image, 255, 255, 255);
 6.  $blue = ImageColorAllocate($image, 0, 0, 255);
 7.  $red = ImageColorAllocate($image, 255, 0, 0);
 8.  for($i = 0; $i < $height; $i = $i + 20) {
 9.    ImageLine($image, $i, 0, $i, $height, $blue);
 10.    ImageLine($image, 0, $i, $width, $blue);
 11.    ImageString ($image, 1, $i, 0, $i, $red);
 12.    ImageString ($image, 1, $2, $i, $red);
 13.  }
 14.  ImageString ($image, 1, 82, 22, "Size 1 Font", $red);
 15.  ImageString ($image, 2, 82, 62, "Size 2 Font", $red);
 16.  ImageString ($image, 3, 82, 102, "Size 3 Font", $red);
 17.  ImageString ($image, 4, 82, 142, "Size 4 Font", $red);
 18.  ImageString ($image, 5, 82, 182, "Size 5 Font", $red);
 19.  header ("Content-type: image/png");
 20.  ImagePng($image);
 21.  ImageDestroy($image);
 22.  ?>
```

##### 图 11-2. gd\_grid.php

![graphics/11fig02.jpg](img/11fig02.jpg)

##### 脚本 11-1. gd\_grid.php 逐行解释

| 行 || 说明 |

| --- | --- |

| 2 || 为图像定义 301 像素的高度（以便网格的最后线可见）。 |

| 3 || 为图像定义 301 像素的宽度。 |

| 4 || 使用 `ImageCreate()` 函数创建基础图像，指定之前定义的高宽。 |

| 5 || 使用 `ImageColorAllocate()` 定义变量 `$white`。参数允许白色（RGB 值 255,255,255）被 `$image` 使用。它也被用作 `$image` 的背景颜色，因为它是分配给 `$image` 的第一个颜色。 |

| 6 || 定义蓝色并允许被 `$image` 使用。 |

| 7 || 定义红色并允许被 `$image` 使用。 |

| 8–13 || 创建一个 `for` 循环，从坐标 0,0（图像左上角）开始每 20 像素绘制一条线。 |

| 9 || 在 `for` 循环中，在 `$image` 内部创建从点 `$i, 0` (0,0 20,40...) 到点 `$i, $height` (0,301 20,301...) 的线。循环的每次迭代从图像顶部到底部绘制一条垂直线，左右间距为 20 像素。 |

| 10 || 在 `for` 循环中，在 `$image` 内部创建从点 0, `$i` (0,0 20,40...) 到点 `$width, $i` (301,0 301,20 301,40...) 的线。循环的每次迭代从图像左侧到右侧绘制一条水平线，上下间距为 20 像素。 |

| 11 || 在 `for` 循环中，使用 `ImageString()` 函数创建一个小标签来显示当前垂直线的当前像素。记住 `ImageString($image, $fontsize, $x, $y, $text, $color);`。 |

| 12 || 在 `for` 循环中，创建一个小标签来显示当前水平线的当前像素 `ImageString()` 函数。 |

| 13 || 结束 `for` 循环。 |

| 14–18 || 在屏幕上不同位置创建文本以显示不同的字体。 |

| 19 || 将图像头发送到用户的浏览器。 |

| 20 || 显示你创建的图像 `$image`。 |

| 21 || 从服务器内存中销图像，因为它已经发送到了浏览器。 |

#### 为你的图像添加 TrueType 字体

你可以使用 TrueType 字体在图像上添加更好看的文本。实现此点的函数是 `ImageTTFText()`。

```
ImageTTFText($image, $size, $angle, $xcoord, $ycoord, $color, $font, $text);
```

`ImageTTFText()` 的参数为：

* `$image`— 你放置此字体的图像的句柄。

* `$size`— 文本的大小，以磅为单位。

* `$angle`— 文本倾斜的度数。注意这并不是字符本身的倾斜（例如使用斜体字体时），而是写入文本的“线”的倾斜。

* `$xcoord`— 图像中 `$text` 第一个字符左方的 x 坐标。

* `$ycoord`— 图像中 `$text` 第一个字符下方的 y 坐标。

* `$color`— 文本的颜色。

* `$font`— TrueType 字体文件的位置。

* `$text`— 你想要打印的文本。

下一个脚本创建了一个简单的图形，如图 11-2 所示，使用 `ImageLine()` 和 `ImageString()` 函数来说明图表的工作原理以及文本大小的外：

##### 脚本 11–1 gd\_grid.php

```
1.  <?
 2.  $height = 301;
 3.  $width = 301;
 4.  $image = ImageCreate($width, $height);
 5.  $white = ImageColorAllocate($image, 255, 255, 255);
 6.  $blue = ImageColorAllocate($image, 0, 0, 255);
 7.  $red = ImageColorAllocate($image, 255, 0, 0);
 8.  for($i = 0; $i < $height; $i = $i + 20) {
 9.    ImageLine($image, $i, 0, $i, $height, $blue);
 10.    ImageLine($image, 0, $i, $width, $blue);
 11.    ImageString ($image, 1, $i, 0, $i, $red);
 12.    ImageString ($image, 1, $2, $i, $red);
 13.  }
 14.  ImageString ($image, 1, 82, 22, "Size 1 Font", $red);
 15.  ImageString ($image, 2, 82, 62, "Size 2 Font", $red);
 16.  ImageString ($image, 3, 82, 102, "Size 3 Font", $red);
 17.  ImageString ($image, 4, 82, 142, "Size 4 Font", $red);
 18.  ImageString ($image, 5, 82, 182, "Size 5 Font", $red);
 19.  header ("Content-type: image/png");
 20.  ImagePng($image);
 21.  ImageDestroy($image);
 22.  ?>
```

##### 图 11-2. gd\_grid.php

![graphics/11fig02.jpg](img/11fig02.jpg)

##### 脚本 11-1. gd\_grid.php 逐行解释

| 行 || 说明 |

| --- | --- |

| 2 || 为图像定义 301 像素的高度（以便网格的最后线可见）。 |

| 3 || 为图像定义 301 像素的宽度。 |

| 4 || 使用 `ImageCreate()` 函数创建基础图像，指定之前定义的高宽。 |

| 5 || 使用 `ImageColorAllocate()` 定义变量 `$white`。参数允许白色（RGB 值 255,255,255）被 `$image` 使用。它也被用作 `$image` 的背景颜色，因为它是分配给 `$image` 的第一个颜色。 |

| 6 || 定义蓝色并允许被 `$image` 使用。 |

| 7 || 定义红色并允许被 `$image` 使用。 |

| 8–13 || 创建一个 `for` 循环，从坐标 0,0（图像左上角）开始每 20 像素绘制一条线。 |
