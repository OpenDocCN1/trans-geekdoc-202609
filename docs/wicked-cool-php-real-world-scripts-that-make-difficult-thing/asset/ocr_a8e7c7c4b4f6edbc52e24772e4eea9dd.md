```
}
}
}
if (count($fonts) < 1) {
    die("No fonts found!");
}
```

The client has to know what kind of image you’re sending. This script creates a JPEG image, so it sends that MIME type. In addition, we don’t want the browser to cache the image, so we’ll send several cache-invalidating headers:

```
/* Image header */
header("Content-Type: image/jpeg");
/* Invalidate cache. */
header("Expires: Mon, 01 Jul 1998 05:00:00 GMT");
header("Last-Modified: " . gmdate("D, d M Y H:i:s") . " GMT");
header("Cache-Control: no-store, no-cache, must-revalidate");
header("Cache-Control: post-check=0, pre-check=0", false);
header("Pragma: no-cache");
```

With all of the preparatory work complete, we can now start creating the image. GD functions begin with an image prefix. To initialize a color image canvas, use imagecreatetruecolor().

```
/* Create image. */
$img = imagecreatetruecolor($width, $height);
```

The first thing we’ll draw is a rectangle to cover the entire background. To draw anything, you need to allocate a color in the image with imagecreatetruecolor(). The second, third, and fourth parameters to this function are the red, green, and blue values of the color, respectively. The value is an integer between 0 and 255, with 0 being the darkest and 255 being the lightest. The following statement creates a random pastel color:

```
/* Fill background with a random shade of pastel. */
$bg = imagecolorallocate($img, rand(210,255), rand(210,255), rand(210,255));
```

Now let’s draw that rectangle with the imagefilledrectangle() function. The rectangle is parallel to the image axes, so you can define it by two points: (0, 0) and ($width, $height):

```
imagefilledrectangle($img, 0, 0, $width, $height, $bg);
```

To convolute the background some more, we’ll draw several vertically oriented polygons across the canvas. The following loop creates the polygons with the imagefilledpolygon() function. This is different than drawing a rectangle because a polygon can have three or more sides in any orientation, so you need to provide an array of points as a parameter (here, $poly_points) instead of two sets of coordinates.