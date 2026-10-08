# Core PHP Programming

```
c
 C
  C
   C
```

```
/*
 ** Draw 'C' in each of the built-in fonts
 */

//create white square
$image = imagecreate(200,200);
$colorBlack = imagecolorallocate($image, 0, 0, 0);
$colorWhite = imagecolorallocate($image, 255,255,255);
imagefill($image, 0, 0, $colorWhite);

//draw a C in each built-in font
imagechar($image, 1, 0, 0, "C", $colorBlack);
imagechar($image, 2, 20, 20, "C", $colorBlack);
imagechar($image, 3, 40, 40, "C", $colorBlack);
imagechar($image, 4, 60, 60, "C", $colorBlack);
imagechar($image, 5, 80, 80, "C", $colorBlack);

//send image
header("Content-type: image/jpeg");
jpeg($image);
```

boolean imagecharup(integer image, integer font, integer x, integer y, string character, integer color)

The imagecharup function operates identically to imagechar, except that the character is oriented vertically, bottom to top.

Figure 12-2. imagecharup.

IT-SC book 327