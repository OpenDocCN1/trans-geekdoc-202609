

数组的第一个元素是图像的宽度，第二个元素是图像的高度。第三个元素是一个标识图像类型的数字，其中 1 表示 GIF，2 表示 JPEG，3 表示 PNG（更多内容请参阅 PHP 手册[3]）。请注意，mime 元素仅在 PHP 4.3.0 及更高版本中可用。

[3] http://www.php.net/getimagesize

## 缩略图类

到目前为止，一切顺利……但我们创建的缩略图会将原始图像拉伸至空白缩略图的完整尺寸。这会导致图像变形，除非它碰巧与缩略图具有相同的宽高比。相反，我们想要一个按比例缩放的原始图像版本，尽可能整齐地适配空白缩略图。在本节中，我们将编写一个正好能实现此功能的类。

该类还将支持处理尺寸小于缩略图的图像，如果需要，可以保持其原始大小。该类设计为仅处理 PNG 和 JPEG 文件，但可以轻松修改以支持其他类型。

与往常一样，我将专注于构建类的 API——即你可能在自己的代码中使用的部分——然后展示如何使用该类。完整代码已提供在代码存档中。

与任何类一样，我们从构造函数开始：

```php
/**
 * Thumbnail constructor
 * @param int max width of thumbnail
 * @param int max height of thumbnail
 * @param boolean (optional) if true image scales
 * @param boolean (optional) if true inflate small images
 * @access public
*/
function Thumbnail($maxWidth, $maxHeight, $scale = true,
    $inflate = true)
{
    $this->maxWidth  = $maxWidth;
    $this->maxHeight = $maxHeight;
    $this->scale     = $scale;
    $this->inflate   = $inflate;
}
```

Thumbnail 类的构造函数接受四个参数。前两个参数分别是缩略图的最大宽度和高度（以像素为单位）。第三个参数告诉类是应该按比例缩放图像以适应缩略图，还是仅仅将其拉伸（如之前的示例所示）。第四个参数告诉类如何处理过小的图像，即是否将其放大以填充缩略图。

将这些参数安全地存储在实例变量后，以下是构造函数的其余部分：

```php
// Consider modifying these to handle other image types
$this->types = array('image/jpeg', 'image/png');
$this->imgLoaders = array(
    'image/jpeg' => 'imagecreatefromjpeg',
    'image/png'  => 'imagecreatefrompng'
);
$this->imgCreators = array(
    'image/jpeg' => 'imagejpeg',
    'image/png'  => 'imagepng'
);
```

`$this->types` 列出了该类可以处理的 MIME 类型。`$this->imgLoaders` 列出了用于加载这些 MIME 类型图像的函数，而 `$this->imgCreators` 列出了用于创建 *新* 图像的函数。

Thumbnail 类提供了两种加载要转换图像的方法。第一种是 loadFile，允许你指定要加载的本地文件：

```php
/**
 * Loads an image from a file
 * @param string filename (with path) of image
 * @return boolean
 * @access public
 */
function loadFile($image)
{
 // Code omitted
}
```

第二种是 loadData，允许你传递存储在 PHP 变量中的二进制图像数据，因此你可以从存储在（例如）MySQL 表中的文件创建缩略图：

```php
/**
 * Loads an image from a string (e.g. database)
 * @param string the image data
 * @param mime mime type of the image
 * @return boolean
 * @access public
 */
function loadData($image, $mime)
{
 // Code omitted
}
```

除了图像数据外，你还需要将 MIME 类型作为第二个参数提供。通常，当图像存储在数据库中时，它们的 MIME 类型会与它们一起存储，如第 9 章所见。

```php
/**
 * If a filename is provided, creates the thumbnail using that
 * name. If not, the image is output to the browser
 * @param string (optional) filename to create image with
 * @return boolean
 * @access public
 */
function buildThumb($file = null)
{
 $creator = $this->imgCreators[$this->sourceMime];
 if (isset($file)) {
 return $creator($this->thumb, $file);
 } else {
 return $creator($this->thumb);
 }
}
```

buildThumb 方法用于渲染完成的缩略图。如果向此方法传递一个文件名，缩略图将使用你指定的名称存储为文件。否则，图像会直接输出到浏览器，因此你需要确保已先发送正确的 HTTP 标头。请注意，这里我们使用的是在构造函数中存储的图像函数名。

最后的公共方法用于获取有关缩略图的信息。getMime 方法返回 MIME 类型，可用于为缩略图生成 Content-Type 标头：

```php
/**
 * Returns the mime type for the thumbnail
 * @return string
 * @access public
 */
function getMime()
{
    return $this->sourceMime;
}
```

getThumbWidth 和 getThumbHeight 方法用于返回缩略图的宽度和高度（以像素为单位），然后你可以使用它们来创建 HTML img 标记，例如：

```php
/**
 * Returns the width of the thumbnail
 * @return int
 * @access public
 */
function getThumbWidth()
{
    return $this->thumbWidth;
}

/**
 * Returns the height of the thumbnail
 * @return int
 * @access public
 */
function getThumbHeight()
{
    return $this->thumbHeight;
}
```

这就完成了！让我们试用一下我们崭新的类：

```php
<?php
// Include the Thumbnail class
require_once 'Images/Thumbnail.php';

// Instantiate the thumbnail
$tn = new Thumbnail(200, 200);

// Load the image from a file
$tn->loadFile('sample_images/sitepoint_logo.jpg');

// Send the HTTP Content-Type header
header('Content-Type: ' . $tn->getMime());

// Display the thumbnail
$tn->buildThumb();
?>
```

上述示例显示了将文件名传递给 Thumbnail 类以创建缩略图。我们使用 PHP 的 header 函数连同 getMime 方法来发送正确的 HTTP 标头；然后只需调用 buildThumb 方法即可显示图像。结果如图 7.2 所示。

## 图 7.2. 按比例缩放的缩略图

![](img/5b6cdf7cf4cf53e30b19e047895dc464_238_0.png)

以下是另一个示例，用于展示 loadData 方法，并说明如何存储文件而不是直接输出：

```php
<?php
// Include the Thumbnail class
require_once 'Images/Thumbnail.php';

// Instantiate the thumbnail
$tn = new Thumbnail(200, 200);

// Load an image into a string (this could be from a database)
$image = file_get_contents('sample_images/sitepoint_logo.jpg');

// Load the image data
$tn->loadData($image, 'image/jpeg');

// Build the thumbnail and store as a file
$tn->buildThumb('sample_images/thumb_sitepoint_logo.jpg');
?>
<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Transitional//EN"
    "http://www.w3.org/TR/xhtml1/DTD/xhtml1-transitional.dtd">
<html xmlns="http://www.w3.org/1999/xhtml">
<head>
<title> Thumbnail Example </title>
<meta http-equiv="Content-Type"
    content="text/html; charset=iso-8859-1" />
</head>
<body>
<h1>Before...</h1>
<img src="sample_images/sitepoint_logo.jpg" />
<h1>After...</h1>
<img src="sample_images/thumb_sitepoint_logo.jpg"
    width="<?php echo $tn->getThumbWidth(); ?>"
    height="<?php echo $tn->getThumbHeight(); ?>" />
</body>
</html>
```

请注意，在为缩略图生成 img 标记时，我们使用 getThumbWidth 和 getThumbHeight 方法来正确完成宽度和高度属性。图 7.3 显示了生成的页面。

## 图 7.3. 之前和之后

![](img/5b6cdf7cf4cf53e30b19e047895dc464_240_0.png)

### 之后...

![](img/5b6cdf7cf4cf53e30b19e047895dc464_240_1.png)

最后，以下是如何从包含 PNG 和 JPEG 文件的目录中构建一个简单的缩略图显示（有关本示例中使用的内置 dir 类的详细信息，请参见第 4 章）。此第一部分读取目录；它查找没有缩略图的图像并创建它们。这样我们就无需每次都创建缩略图，节省了开销：

```php
<?php
// Include the Thumbnail class
require_once 'Images/Thumbnail.php';

// Open the sample_images subdirectory
$dir = dir('sample_images');

// Read through the files looking for images to convert
while ($image = $dir->read()) {
    // Get the file extension
    $ext = explode('.', $image);
    $size = count($ext);
    // Check that it's a valid file
    if (($ext[$size-1] == 'png' || $ext[$size-1] == 'jpg') &&
        preg_match('/^thumb_/', $image ) == 0 &&
        $image != '.' && $image != '..') {
```

