

```php
$chtt = 'chtt=SalesByRegion' . ' ' . date('m/d/Y') . ' ' . '&';
$chs = 'chs=FF0000,12,c' . ' ' . '&';
```

你可以在图表的任何位置显示图例信息。我建议，如果 X 轴标签相互重叠，图例可能并不可用。你还可以在图表下方显示一个包含数据的表格。

```php
$chdl = 'chdl' . '.labels' . ' ' . '&';
$chldp = 'chldp=1' . ' ' . '&';
```

你可以定义线条的颜色。默认情况下，你将获得橙色。你可以为每个柱状图指定单一颜色或自定义颜色。我建议默认颜色是最好的，因为它们代码更少，而且不会浪费 2K 的字符限制。不过，考虑到我确信总会有三条线，所以我为每个数据系列定义了颜色。

```php
$chco = 'chco' . '0000FF,FF0000,FF0000' . ' ' . '&';
```

图表和图例边距类似于图表的单元格填充（padding）。这些值将强制标签和图表正确缩放以适应图表的大小。

```php
$chma = 'chma' . '20,20,20|50,50' . ' ' . '&';
```

最后，你可以用自定义颜色、渐变甚至透明度设置填充图表的背景。这将为图表提供自定义的视觉外观。

```php
$chf = 'chf' . 'bg,s=EFEFEF' . ' ' . '&';
```

还有其他可选元素和数据函数可用。我鼓励你至少查看一下，看看它们是否对你感兴趣。我倾向于让我的图表简单且直接，让数据脱颖而出，而不一定是设计。

现在你已经已经在 PHP 代码中定义了所有变量，可以组装 NVP（可选参数）。我们将使用最简单的 GET 方法来获取图像。我们将使用源指向 Google Chart URL 的 `img` 标签。如果由于某种原因你的字符串超过了 2K，你可以利用 POST 方法获取图像。Google 提供了实现此图表的完整说明。现在，我们将使用图像标签和 PHP 代码来显示图表：

```html
<img src="https://chart.googleapis.com/chart?<?php echo $chtt . $chs . $chds . $chd . $chcl . $chxr . $chm . $chco . $chid; ?>">
```

你能想象必须用所有原始字符串来组装源吗？我相信在 PHP 代码中设置变量可以为每种类型的图表创建模板变得更容易，更容易修改图表的设计和显示，并且显然让图像更更容易组装和解析。

![](img/5a2c5fda68d42e5d65f51850276e49ec_308_0.png)

图 7-104：Google 折线图

# 第39 节：Google Map API 商店定位器

**目标：** 在本节中你将学习如何集成 Google map API。如果你一直尝试将 Google maps 集成到你的 FileMaker PHP 站点，我知道你查看过他们的代码，要么放弃了，要么在忍受无数页文档和 JavaScript 中浪费了时间。截至 2011 年 5 月，Brad Welled 发布了一个卓越的 PHP 类，让 Google Maps 变得极其容易使用。尽管没有被 Google “官方支持”（因为它不是内部项目），但他们在会议上展示了它，并为 Brad 提供了一个使用他们域名的漂亮网站。这告诉我 Google 真的很喜欢它，我也一样。你可以在此处找到关于该类的更多信息：

```
http://code.google.com/p/php-google-map-api/
```

**难度：** 困难

**示例文件：** 
- PHPFiles/Advanced/Lesson39/GoogleMap.php
- PHPFiles/Advanced/Lesson39/JSMIn.php
- PHPFiles/Advanced/Lesson39/StoreLocator.php
- PHPFiles/Advanced/Lesson39/StoreLocator.f12

本节使用独立的数据库文件来演示。请将 StoreLocator.fmp2 数据库文件上传到你的服务器。

![](img/5a2c5fda68d42e5d65f51850276e49ec_309_0.png)

**页面导航：**

| 列表 |
|---|

**FileMaker API 方法：**
- `newPerformScriptCommand(`
- `getRecords(`
- `getField(`

**代码：**

Brad 的 V3 版本中有许多可用功能，我可能花费大量时间来介绍开发者一些最常见的请求以涵盖所有内容。相反，我将获取并将其插入你自己的数据库中。我的目标是将现有的文档（或缺失文档）和示例代码转换为 FileMaker 开发者社区有用的东西。第一个示例将创建一个商店定位器，利用 Google 的地理编码服务（Geocoding service）查找并显示具有用户定义距离数据库记录。

数据库具有名称、地址、城市和州的字段。这些应该是显而易见的。接下来是用于餐厅的纬度（Lat）和经度（Lon）字段。我已提供了记录的数据。在下一节中，我将向你展示如何获取并插入你自己的记录中。SearchLocation 和 Distance 字段用于商店定位器根据用户提供的信息查找记录。距离计算使用大圆导航公式（又称 Haversine 公式）来计算用户位置与每家商店之间的距离。关于该公式的更多信息，可以从我使用 FileMaker Pro 9 发表的《Map Distance》文章中找到：

```
http://www.formulations.com/pages/filemaker/detail.php?id=213
```

或者：

http://en.wikipedia.org/wiki/Haversine_formula

或者

距离计算的数学涉及相当复杂的三角学。由于数学课不是重点，我将让你自己理解这些数学，只要你可以直接使用该计算且它就能正常工作。关于距离计算，我唯一要说的是它是按英里计算距离。如果你在公里中使用它，可以更改计算中的常量。

StoreLocator.php

有两个主要过程来使此解决方案运行。首先是 PHP 页面。其次是商店定位器。分别描述它们更高效，所以我们将从 PHP 页面开始。始终从包含数据库的连接开始。

```php
<?php
require_once ('FileMaker.php');
$fm = new FileMaker();
$fm->setProperty('database', 'StoreLocator');
$fm->setProperty('hostname', 'http://127.0.0.1/');
$fm->setProperty('username', 'Admin');
$fm->setProperty('password', '1234');
?>
```

你还需要包含下载文件中要求你提供的两个类。GoogleMap.php 包含了连接到 Google Map API 的所有代码。从技术上说你不需要对其进行任何操作。但是，如果你浏览它，你会发现你可以通过将值从 `false` 改为 `true` 来配置通过 API 提供的任何功能。大多数功能在该文件中默认开启。对于控制 Google Map API 的简单性，我怎么说都不为过。你会怎么做——将值从 `false` 改为 `true`，还是处理 Google 的数百行代码？接下来是 JSMin.php，就这些了。再次，我向 Brad 致敬，因为他将所有代码移植到了 PHP。你不需要编写任何 JavaScript。它就能正常工作！

```php
<?php
include_once('GoogleMap.php');
include_once('JSMin.php');
?>
```

接下来，使用 PHP_SELF 动态快捷创建表单，将表单指向同一页面。之后，你可以根据你的解决方案设置任何合理值的距离弹出菜单。

