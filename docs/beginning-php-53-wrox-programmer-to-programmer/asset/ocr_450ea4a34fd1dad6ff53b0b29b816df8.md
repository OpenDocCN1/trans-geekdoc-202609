# Appendix A: Solutions to Exercises

# # Chapter 17

# ## Exercise 1 Solution

The only trick to successfully complete this exercise is to remember that the top-left corner of an image is (0,0). This means you must remember to subtract 1 from the width and height of the image to get the rightmost position and bottommost position of the image, respectively. Here's the code to draw the black border:

```
<?php
$myImage = imagecreatefromjpeg('hook.jpg');
$black = imagecolorallocate($myImage, 0, 0, 0);
$width = imagesx($myImage);
$height = imagesy($myImage);
imagereangle($myImage, 0, 0, $width-1, $height-1, $black);
header('Content-type: image/jpeg');
imagejpeg($myImage);
imagedestroy($myImage);
?>
```

If your script was to do this, your output should include a nice clean border around the image, like the one shown in Figure A-1.

![](bbox=[0.16, 0.474, 0.76, 0.816])

Figure A-1