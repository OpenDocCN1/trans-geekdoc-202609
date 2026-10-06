# Part III: Using PHP in Practice

# Creating Images

Now that you understand the basic image concepts, you can start writing scripts to generate images. Creating an image in PHP requires four steps:

+   1. Create a blank image canvas for PHP to work with. This is an area of the Web server's memory that is set aside for drawing onto.
2. Work through the steps involved in drawing the image that you want. This includes setting up colors and drawing the shapes and text that you want within your image.
3. Send your finished image to the Web browser or save it to disk.
4. Remove your image from the server's memory.

# Creating a New Image

The first thing to do is to create a blank image canvas to store your new image. To do this you can use the `imagecreate()` function, which creates an 8-bit palette-based image with a maximum of 256 colors, or use the `imagecreatruecolor()` function, which creates a 24-bit true color image you would like to create. Both `imagecreate()` and `imagecreatruecolor()` functions take two parameters: the width and height of the image that you want to create. For example:

```
$myImage = imagecreate( 200, 150 );
```

The blank that this code creates is 200 pixels wide and 150 pixels high.

Both functions return an image resource (stored in `$myImage` in the example) that points to the image in memory. You then pass this image resource to other image functions so that they know which image to work with.

# Allocating Colors

Before you can start drawing on your blank image, you need to decide the color you want to draw with, then use the `imagecolorallocate()` function to create the color. This function takes four arguments: the image resource created by `imagecreate()` or `imagecreatruecolor()`, and the red, green, and blue components of the color you would like. Each component can have a value between 0 and 255.

For example, the following code creates a green color and stores it in a variable `$myGreen:`

```
$myGreen = imagecolorallocate(\$myImage, 51, 153, 51 );
```

The `imagecolorallocate()` function returns a color identifier that points to the newly created color. You can then use this identifier with various drawing functions, as you see in the moment.

If you've run out of space to allocate colors? This can happen if a palette-based image created with `imagecreate()` already contains 256 colors, and there's no space to allocate a new color. In this case, `imagecolorallocate()` returns `false`.

510