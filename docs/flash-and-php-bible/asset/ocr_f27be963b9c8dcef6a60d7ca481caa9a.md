**CAUTION** The process of building an image pixel by pixel is processor intensive and can take a long time, depending on the size of the image.

Here is the completed PHP code:

```
<?php

$width = $_POST['width'];
$height = $_POST['height'];

$points = simplexml_load_string($_POST['pointData']);

$img = imagecreatetruecolor($width, $height);

$limit = count($points->point);

for($j=0; $j < $limit; $j++)
{
	$x = $points->point[$j]->x;
	$y = $points->point[$j]->y;

	$color = $points->point[$j]->c;
	$color = hexdec($color);

	imagesetpixel($img, $x, $y, $color);
}

header('Content-Type: image/png');
imagepng($img, 'render_' . time() . '.png');
?>
```

# Gathering the pixel data in Flash

There are only a few updates necessary to the Flash code from the previous section, but for now focus on gathering the image data using the BitmapData class.

The first step in this function is to determine the dimensions of the image.

```
var width:uint = penMC.width;
var height:uint = penMC.height;
```

The next variable to define is the PHP file reference.

```
var phpFile:String =
	"http://localhost/ch12/DrawingGD/ImageGenerator.php";
```

The next step is to build a new bitmap using the draw() method of the BitmapData class. The draw method takes one argument, which is the target. This method takes the argument and copies the pixel data to the new bitmap.