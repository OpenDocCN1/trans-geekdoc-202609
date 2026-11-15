# Try It Out Display System Fonts

Try displaying each of the five system fonts. Save this script as `system_fonts.php` in your document root folder and open the script URL in your Web browser:

```
<?php
$textImage = imagecreate( 200, 100 );
$white = imagecolorallocate( $textImage, 255, 255, 255 );
$black = imagecolorallocate( $textImage, 0, 0, 0 );
$yOffset = 0;
for ( $i = 1; $i <= 5; $i++ ) {
    imagestring( $textImage, $i, 5, $yOffset, "This is system font $i", $black );
    $yOffset += imagefontheight( $i );
}
header( "Content-type: image/png" );
imagepng( $textImage );
imagedestroy( $textImage );
?>
```

Figure 17-23 shows the output of this script.

![](bbox=[0.23, 0.47, 0.68, 0.62])

Figure 17-23

# How It Works

First the script creates a blank palette-based image for the text, then it allocates the colors white and black in the image’s palette. Because the code allocates white first, it is set as the background color of the image:

```
<?php
$textImage = imagecreate( 200,100 );
$white = imagecolorallocate( $textImage, 255, 255, 255 );
$black = imagecolorallocate( $textImage, 0, 0, 0 );
```

Then, the script sets a variable to store the y position (how far down the image) to draw the string at. The first line of text will be at the top of the image, so this variable is set to 0.

```
$yOffset = 0;
```