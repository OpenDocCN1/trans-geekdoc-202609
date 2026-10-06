# Part III: Using PHP in Practice

![](bbox=[0.178, 0.087, 0.691, 0.41])

The imagecopyresampled() function, although slightly slower, interpolates the pixels so that you do not get that blocky effect. Both the imagecopyresized() and the imagecopyresampled() functions take the same ten parameters:

+   - The destination image
- The source image
- The x and y coordinates in the destination image of the top-left corner of the copied block of pixels
- The x and y coordinates in the source image indicating the top-left corner of the block to copy
- The resized width and height of the copied block in the destination image
- The width and height of the block of image data to be copied out of the original image

The script uses the imagecopyresampled() function to copy the entire data to the thumbnail image, scaling it as it goes:

```
imagecopyresampled($myThumbnail, $mainImage, 0, 0, 0, 0, $thumbWidth,
$thumbHeight, $mainWidth, $mainHeight);
```

Finally the script sends the image data to the browser (see Figure 17-22) and cleans up the memory that the images used:

```
header( "Content-type: image/jpeg" );
jpeg($myThumbnail );
imagedestroy($myThumbnail );
imagedestroy($mainImage );
?>
```

530