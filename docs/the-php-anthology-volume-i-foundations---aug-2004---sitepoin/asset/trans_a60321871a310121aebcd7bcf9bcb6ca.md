

剩下的就是将柱状图添加到图表中，并将其发送到浏览器：

```
File: 8.php (excerpt)

// Finishing
$graph->Add($bplot);    // Add bar plot to graph
$graph->Stroke();       // Send to browser
?>
```

图7.7展示了结果。仅用七十一行PHP代码就能做到这一点，不错吧！

## 图7.7. 对钢笔的巨大需求

![](img/5b6cdf7cf4cf53e30b19e047895dc464_248_0.png)

## 饼图

JpGraph还可以轻松构建的另一种图表是饼图。让我们使用上一个示例中的示例数据来构建一个饼图。

在脚本开始处，必须包含饼图和3D饼图类：

```
File: 9.php (excerpt)

<?php
// JpGraph does not work with notices enabled
error_reporting(E_ALL ^ E_NOTICE);

// Include the necessary JpGraph libraries
require_once 'jpgraph.php';      // Core engine
require_once 'jpgraph_pie.php';  // Pie chart
require_once 'jpgraph_pie3d.php';// 3D Pie chart

// Sample sales data: could be a database query
$xdata = array('Mousemats', 'Pens', 'T-Shirts', 'Mugs'); // X Axis
$ydata = array(35, 43, 15, 10); // Y Axis
```

这次，我们不是使用Graph类，而是使用PieGraph类：

```
File: 9.php (excerpt)
// Set up the graph
$graph = new PieGraph(400, 200, 'auto'); // Width, height
$graph->SetMarginColor('yellow'); // Margin color yellow
$graph->SetShadow(); // Use a drop shadow
$graph->SetFrame(true, 'red'); // Red frame
```

标题的设置与之前相同：

```
File: 9.php (excerpt)
// Set up the graph title
$graph->title->Set('March Sales'); // Title text
$graph->title->SetColor('navy'); // Title color
$graph->title->SetFont(FF_VERDANA, FS_BOLD, 14); // Title font
```

我们还需要一个图例来标识饼图的每个部分代表什么：

```
File: 9.php (excerpt)
// Set up the pie segment legend
$graph->legend->SetColor('navy'); // Legend text color
$graph->legend->SetFillColor('orange'); // Legend background color
$graph->legend->Pos(0.05, 0.5); // Legend position
```

现在，我们创建3D饼图，使用Y数据实例化它，并使用X数据作为图例：

```
File: 9.php (excerpt)
// Set up 3D pie chart
$pie = new PiePlot3d($ydata); // Instantiate 3D pie with Y data
$pie->SetLegends($xdata); // Add X data to legends
$pie->SetTheme('water'); // Set color theme
$pie->SetCenter(0.39); // Center relative to X axis
$pie->SetSize(100); // Size of pie radius in pixels
$pie->SetAngle(30); // Set tilt angle of pie
$pie->ExplodeSlice(0); // Pop out a slice
$pie->ExplodeSlice(1); // Pop out another slice
```

在图表上的每个部分旁边，我们将显示一个标签，以标识该部分所代表的整体百分比：

```
// Set up values against each segment
$pie->value->SetFont(FF_VERDANA, FS_NORMAL, 10); // The font
$pie->value->SetColor('navy'); // Font color
```

最后，我们将3D饼图添加到图表中，并将其发送到浏览器：

```
// Finishing
$graph->Add($pie); // Add bar plot to graph
$graph->Stroke(); // Send to browser
?>
```

结果如图7.8所示。

## 图7.8. 谦卑之饼

![](img/5b6cdf7cf4cf53e30b19e047895dc464_250_0.png)

JpGraph是PHP的首选图表解决方案，因为它提供了比我们在此处看到的示例更多的功能。值得注意的是，它允许您将呈现的图表存储为PNG文件，因此您可以呈现一次，以后重复使用完成的图像。

## 如何防止图片“热链接”？

您可能遇到的一个问题（尤其是如果您的网站托管了独特的图片）是，其他网站从它们的页面“热链接”到您的图片，这使得您的酷图片看起来像是由它们托管或拥有。除了这里可能存在的版权问题外，外部网站“热链接”您的图片还可能占用您的带宽。

已经设计了不同的解决方案，例如使用Apache的mod_rewrite来检查浏览器提供的引荐信息（这并不总是可靠的），以确保来源是本地网页。例如：

```
SetEnvIfNoCase Referer "^http://www\.sitepoint\.com/" locally_linked=1
SetEnvIfNoCase Referer "^http://sitepoint\.com/" locally_linked=1
SetEnvIfNoCase Referer "^$" locally_linked=1
<FilesMatch "\.(gif|png|jpe?g)$">
    Order Allow,Deny
    Allow from env=locally_linked
</FilesMatch>
```

另一种选择是使用会话来确定查看图片的人是您网站的访客。诀窍是注册一个访客必须拥有才能查看图片的会话变量，然后使用第二个脚本来呈现图片。例如：

```
<?php
// Start a session
session_start();

// Register a variable in the session
$_SESSION['viewImages'] = TRUE;
?>
<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Strict//EN"
    "http://www.w3.org/TR/xhtml1/DTD/xhtml1-strict.dtd">
<html xmlns="http://www.w3.org/1999/xhtml">
<head>
<title> Preventing Hotlinking </title>
<meta http-equiv="Content-Type"
content="text/html; charset=iso-8859-1" />
</head>
<body>
<p> Here is the image:</p>
<img src="11.php?img=php-big.png" />
</body>
</html>
```

请注意，上述代码注册了一个名为viewImages的会话变量，然后使用img标签指向将获取图片的PHP脚本。以下是该脚本的代码：

```
File: 11.php

<?php
// Start a session
session_start();

// Check to see if $viewImages is registered
if (isset($_SESSION['viewImages']) &&
    $_SESSION['viewImages'] == TRUE) {

    // An array of available images
    $images = array(
        'sitepoint_logo.jpg',
        'php-big.png'
    );

    // If $_GET['img'] is set and in available...
    if (isset($_GET['img']) && in_array($_GET['img'], $images)) {

        // Get the image information
        $dims = getimagesize('sample_images/' . $_GET['img']);

        // Send the correct HTTP headers
        header('content-disposition: inline; filename=' .
            $_GET['img']);
        header('content-type: ' . $dims['mime']); # PHP 4.3.x +
        header('content-length: ' .
            filesize('sample_images/' . $_GET['img']));

        // Display the image
        readfile('sample_images/' . $_GET['img']);
    } else {
        die('Invalid or no image specified');
    }
} else {
    die('This image is protected from hotlinking');
}
?>
```

该脚本首先检查viewImages会话变量是否已设置为TRUE。如果是，并且通过$_GET['img']提供的图片名称已在数组$images中注册，则脚本使用您之前看到的getimagesize函数来获取图片的正确MIME类型，发送标头并显示它。

这应该能阻止所有执着的“热链接者”。

请注意，在第II卷第1章中，我开发了一个Session类，用于封装所有对PHP会话API的调用。修改后的上述示例以使用Session类，如下所示：

```
<?php
// Include the session class
require_once 'Session/Session.php';

// Instantiate the Session class
$session = new Session();

// Register a variable in the session
$session->set( 'viewImages', TRUE );
?>
<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Transitional//EN"
"http://www.w3.org/TR/xhtml1/DTD/xhtml1-transitional.dtd">
<html xmlns="http://www.w3.org/1999/xhtml">
<head>
<title> Preventing Hotlinking </title>
<meta http-equiv="Content-Type"
content="text/html; charset=iso-8859-1" />
</head>
<body>
<p>Here is the image:</p>
<img src="11.php?img=php-big.png" />
</body>
</html>
```

```
<?php
// Include the Session class
require_once 'Session/Session.php';

// Instantiate the Session class
$session = new Session();

// Check to see if $viewImages is registered
if ($session->get('viewImages')) {

    // An array of available images
    $images = array(
        'sitepoint_logo.jpg',
        'php-big.png'
    );

    // If $_GET['img'] is set and in available...
    if (isset($_GET['img']) && in_array($_GET['img'], $images)) {

        // Get the image information
        $dims = getimagesize('sample_images/' . $_GET['img']);

        // Send the HTTP headers
        header('content-disposition: inline; filename=' .
            $_GET['img']);
        header('content-type: ' . $dims['mime']);
        header('content-length: ' . filesize('sample_images/' .
            $_GET['img']));

        // Display the image
        readfile('sample_images/' . $_GET['img']);
    } else {
        die('Invalid image specified');
    }
} else {
    die('This image is protected from hotlinking');
}
?>
```

一个更实际的替代方案是将图片列表存储在数据库中。无论您如何操作，重要的是要验证请求的文件是您打算授予访问权限的文件；否则，您可能会允许访问超出预期的内容。

## 进一步阅读

- 首先阅读我！http://www.sketchpad.net/readme.htm

这篇文章很好地解释了计算机图形学的基础知识。如果您对GD库有宏伟计划，这是必读文章。

- 即时生成图像：http://hotwired.lycos.com/webmonkey/01/21/index4a.html

这是Webmonkey对PHP图像函数的介绍。

