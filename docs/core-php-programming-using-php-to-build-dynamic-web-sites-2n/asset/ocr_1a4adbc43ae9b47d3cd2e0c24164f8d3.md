# Core PHP Programming

```
$ButtonLabelHeight = imagefontheight($ButtonFont);
$ButtonLabelWidth = imagefontwidth($ButtonFont) *
strlen($ButtonLabel);

//determine label upper left corner
$ButtonLabelX = ($ButtonWidth-
$ButtonLabelWidth)/2;
$ButtonLabelY = ($ButtonHeight-
$LabelHeight)/2;

//draw label shadow
imagestring($image,
$ButtonFont,
$ButtonLabelX+1,
$ButtonLabelY+1,
$ButtonLabel,
$colorShadow);

//draw label
imagestring($image,
$ButtonFont,
$ButtonLabelX,
$ButtonLabelY,
$ButtonLabel,
$colorHighlight);
\n//output image
header("Content-type: image/jpeg");
imagejpeg($image);
?>
```

The first step takes is to make sure it has valid information for all the parameters. These include the size of the button and the text with which to label the button. I've chosen the built-in fonts, which are numbered one through five. Chapter 12 has descriptions of functions for loading different fonts, and I encourage you to modify your script to incorporate them.

The next step is to create an image. There are two ways to do this. You can create an image of a specific size which is blank, or you can load an existing JPEG. I've chosen the former because it allows the script to make buttons of any size. You can make more stylish buttons using the latter method. This is another good example.

The button will be drawn with three colors: a body color, a highlight, and a shadow. I've chosen to go with three shades of gray. These colors must be allocated with the imagecolorallocate function. Using the body color, the script makes a rectangle that is one pixel smaller than the entire image. The border around this rectangle is created with four lines. The lines on the bottom and right sides are drawn in the shadow color,