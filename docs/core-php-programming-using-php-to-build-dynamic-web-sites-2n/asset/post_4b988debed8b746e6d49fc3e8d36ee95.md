
# Core PHP Programming

```
//make red circle
imagearc($image, 50, 50, 100, 0, 360, $colorRed);
imagefilltoborder($image, 50, 50, 100, $colorRed, $colorRed);

//make green circle
imagearc($image, 100, 50, 100, 0, 360, $colorGreen);
imagefilltoborder($image, 100, 50, 100, $colorGreen, $colorGreen);

//make blue circle
imagearc($image, 75, 75, 100, 0, 360, $colorBlue);
imagefilltoborder($image, 75, 75, $colorBlue, $colorBlue);

//send image
header("Content-type: image/jpeg");
jpeg($image);
```

# integer imagecolorat(integer image, integer x, integer y)

The imagecolor returns the index of the color at the specified pixel. All images have a palette of arbitrary colors referred to by integers.

```php
<?
/*
 ** Change a color
 */
//attempt to open image, suppress error messages
if!($image = @imagecreatefromjpeg("php_lang.jpg"))
{
    //error, so create an error image and exit
    $image = imagecreate(200,200);
    $colorWhite = imagecolorallocate($image, 255, 255, 255);
    $colorBlack = imagecolorallocate($image, 0, 0, 0);
    imagefill($image, 0, 0, $colorWhite);
    imagestring($image, 4, 10, 10, "Couldn't load image!", $colorBlack);
    header("Content-type: image/jpeg");
    jpeg($image);
    exit();
}
//get the color at (10,10)
$colorIndex = imagecolorat($image, 10, 10);

//change that color to red
imagecolorset($image, $colorIndex, 255, 0, 0);

//send image
header("Content-type: image/jpeg");
jpeg($image);
?>
```

# integer imageclosestest(integer image, integer red, integer green, integer blue)

The imageclosestest function returns the index of the color in the given image closest to the given color. Colors are treated as three-dimensional coordinates, and closeness is defined by the distance between two points.

```php
<?php
/*
 ** Compare closest color to real color
 */
//attempt to open image, suppress error messages
if(!($image = @imagecreatefromjpeg("php_lang.jpg")) {
    //error, so create an error image and exit
    $image = imagecolorallocate($image, 255, 255, 255);
    $colorBlack = imagecolorallocate($image, 0, 0, 0);
    imagefill($image, 0, 0, $colorWhite);
    imagestring($image, 4, 10, 10, "Couldn't load image!", $colorBlack);
}
header("Content-type: image/jpeg");
    imagejpeg($image);
}

//find index of color closest to pure magenta
$magentaIndex = imageclosestest($image, 255, 0, 255);

//get RGB values
$colorArray = imagecolorsforindex($image, $magentaIndex);

//allocate closest color
$colorMagenta = imagecolorallocate($image,
$colorArray[]="red",
$colorArray[]="green",
$colorArray[]="blue");

//draw a square
imagefilledrectangle($image, 10, 10, 100, 100, $colorMagenta);

//send image
header("Content-type: image/jpeg");
    imagejpeg($image);
?>
```

# Core PHP Programming

## integer imagecolorexact(integer image, integer red, integer green, integer blue)

Use the imagecolorexact function to find the index of the color in the given image that matches the given color exactly. If the color doesn't exist, negative one (-1) is returned.

```php
<?php
/**
** Check that an image contains black
** If so, change all back to cyan.
//attempt to open image, suppress error messages
if(!$image=@imagecreatefromjpeg("php_lang.jpg")) {
  //error, so create an error message and exit
  $image = imagecreate(200,200);
  $colorWhite = imagecolorexact($image, 255, 255, 255);
  $colorBlack = imagecolorexact($image, 0, 0, 0);
  imagefill($image, 0, 0, $colorWhite);
  imagestring($image, 4, 10, 10, "Couldn't load image!", $colorBlack);
  header("Content-type: image/jpeg");
  imagejpeg($image);
  exit();
}
```

```php
//find index of black
$blackIndex = imagecolorexact($image, 0, 0, 0);

if($blackIndex >= 0) {
  //make all black areas cyan
  imagecolorset($image, $blackIndex, 0, 255, 255);
}

//send image
header("Content-type: image/jpeg");
imagejpeg($image);
?>
```

# integer imagecolorresolve(integer image, integer red, integer green, integer blue)

The imagecolorresolve function returns a color identifier based on a specified color. If the color doesn't exist in the palette, it will be added. In the event that the color cannot be added, an identifier for the closest color will be returned.

```php
<?php
/*
# Core PHP Programming

** Attempt to draw a magenta square
*/
```

```php
//attempt to open image
```

```php
$colorMagenta = imagecolorresolve($image, 255, 0, 255);
```

```php
// draw a square
imagefilledrectangle($image, 10, 10, 50, 50, $colorMagenta);
```

```php
//send image
header("Content-type: image/jpeg");
imagejpeg($image);
?>
```

# boolean imagecolorset(integer image, integer index, integer red, integer green, integer blue)

The imagecolorset function sets the color at the index to the specified color. For an example of use, see the example for the imagecolorat function.

# array imagecolorsforindex(integer image, integer index)

The imagecolorsforindex function returns an associative array with the red, green, and blue elements of the color for the specified index.

```php
<?php
/*
 ** Show RGB values for a color
*/
//attempt to open image
```

```php
imagefill($image, 0, 0, $colorWhite);
imagestring($image, 4, 10, 10, "Couldn't load image!");
$colorBlack;
header("Content-type: image/jpeg");
imagejpeg($image);
exit();

// get the color at (100,100)
$colorIndex = imagecolorat($image, 100, 100);

// get RGB values
$colorParts = imagecolorsforindex($image, $colorIndex);

// display RGB values
$colorParts["red"],
```

# Core PHP Programming

## integer colorstotal(integer image)

The imagecolorstotal function returns the number of colors in the given image.

```php
/*
 ** Find number of colors
 */
// get the color at (100,100)
$colorIndex = imagecolorat($image, 100, 100);

// get RGB values
$colorParts = imagecolorsforindex($image, $colorIndex);

// display RGB values
$colorParts["red"],
```

# integer colortrans(integer image, integer color)

The colortrans function sets the given color transparent.

```php
<?php
/*
# Core PHP Programming

** Create a transparent field
** into it.
 */

// create red square
$image = imagecreate(200,200);
$colorRed = imageallocate($image, 255, 0, 0);
imagefill($image, 0, 0, $colorRed);

// draw a square
imagefilledrectangle($image, 10, 10, 70, 70, $colorBlue);

// send image
header("Content-type: image/jpeg");
imagejpeg($image);
?>
```

# Core PHP Programming

## imagecopyresized(integer destination, integer source, integer destination_x, integer destination_y, integer source_x, integer source_y, integer destination_width, integer destination_height)

imagecopyresized copies a portion of the source into the destination image. If the destination width and height are different than the source width and height, it will be stretched or shrunk.

```php
<?php
/*
# Core PHP Programming

** Put logo into field
** and resize it to 180x180
 */

// create red square
$image = imagecreate(200,200);
$colorRed = imageallocate($image, 255, 0, 0);
imagefill($image, 0, 0, $colorRed);

// attempt to open image, suppress error
if!($image2 = @imagecreatefromjpeg("php_lang.jpg")) {
    // error, so create an error image and exit
    $image = imagecreate(200,200);
$colorBlue = imageallocate($image, 0, 0, 255);
imagefill($image, 0, 0, $colorBlue);

// draw a square
imagefilledrectangle($image, 30, 30, 70, 70, $colorBlue);

// send image
header("Content-type: image/png");
imagepng($image);

// drop image2 into image, and stretch or squash
imagecopyresized($image, $image2, 10, 10, 0, 0, 180, 180, imagesx($image2), imagesy($image2));

// send image
header("Content-type: image/jpeg");
imagejpeg($image);
?>
```
