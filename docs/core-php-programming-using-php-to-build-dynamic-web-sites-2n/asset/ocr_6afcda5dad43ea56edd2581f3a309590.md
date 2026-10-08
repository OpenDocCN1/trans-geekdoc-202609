# Core PHP Programming

```
<?php
/*
 // Show image with a dashed line
 */

//create yellow square
$image = imagecreate(200,200);
$colorBlue = imagecolorallocate($image, 0, 0, 255);
$colorYellow = imagecolorallocate($image, 255, 255, 0);
imagefill($image, 0, 0, $colorYellow);

//draw dashed line in blue
imagesashedhedline($image, 10, 10, 150, 130, $colorBlue);

//send image
header("Content-type: image/jpeg");
imagejpeg($image);
?>
```

# boolean imagedestroy(integer image)

Use the imagedestroy function to clear memory associated with the specified image. Most of the time you will not need this function. PHP will clean up when your script ends.

```
<?php
/*
 // Create an image, then free its memory
 */

//create blue square
$image = imagecreate(200,200);
$colorBlue = imagecolorallocate($image, 128, 128, 255);
imagefill($image, 0, 0, $colorBlue);
```

IT-SC book 337