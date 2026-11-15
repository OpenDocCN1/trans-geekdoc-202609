*HTTP headers and the header() function were covered in the previous chapter.*

These three functions return true if the image was outputted successfully, or false if there was a problem.

imagejpeg() takes an optional third argument that specifies the compression level, or quality, of the final image. This is an integer between zero (maximum compression) and 100 (maximum quality). The default is around 75, which is usually a good compromise between file size and image quality. Here's how you might send a lower-quality JPEG image to the browser if you wanted to conserve bandwidth:

```
header( "Content-type: image/jpeg" );
imagejpeg( $myImage, null, 50 );
```

Similarly, you can pass a compression level to imagepng() as an optional third argument. PNG compression levels range from zero (no compression) to 9 (maximum compression). PNG is a lossless format so an image looks the same regardless of its compression level; however, higher compression levels usually result in smaller file sizes (though the image will take longer to create). The default compression level is 6, which is fine for most scenarios.

When you've finished with an image, you should remove it from memory in order to free up the memory for other purposes. To do this, call the imagedestroy() function, passing in the resource of the image to delete:

```
imagedestroy( $myImage );
```

imagedestroy() returns true if the image was successfully deleted, or false if there was a problem.

# # Drawing in an Image

Once you have allocated the colors that you want to draw with, you can start drawing on your blank canvas. PHP provides functions for drawing points, lines, rectangles, ellipses, arcs, and polygons.

All of the drawing functions in PHP have a similar pattern to the arguments that you need to pass them. The first argument is always the image resource of the image that you want to draw on. The next arguments vary in number, but are always the x and y pixel positions that you need to supply in order to draw the shape that you want. For example, if you are drawing only a single pixel, you have to provide only one x and one y coordinate, but if you are drawing a line you need to provide x and y coordinates for both the start and end positions of the line. The last parameter is always the color with which you want to draw.

# # Drawing Individual Pixels

To color a single pixel on your canvas, use the imagesetpixel() function:

```
imagesetpixel( $myImage, 120, 60, $myBlack );
```

This colors the pixel that is 120 pixels across and 60 pixels down from the top-left corner of the image $myImage. It sets the pixel to the color identified by $myBlack. Figure 17-4 shows the layout of this single pixel in the image.