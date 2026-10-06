
# Part III: Using PHP in Practice

![](img/ede05b7b77968b82cbd9a513122fb183_559_0.png)

Figure 17-16

## How It Works

The code is relatively straightforward and shouldn't pose any problems. The `imagecreatefromjpeg()` function creates a new image resource from the existing image:

```php
$myImage = imagecreatefromjpeg("lucky.jpg");
```

Then the script sends a header to the Web browser, telling it to expect some JPEG image data:

```php
header("Content-type: image/jpeg");
```

All that's left to do is send the data and clean up the image from memory:

```php
imagejpeg($myImage);
imagedestroy($myImage);
```

Of course the script doesn't do anything that you couldn't do yourself using plain HTML, so you may be wondering what the point is. Well, being able to open existing images and manipulate them before sending them to the browser is useful for a number of reasons. Some of the things that you can do to an image using the GD image functions include:

- Resizing the image to create a thumbnail for display
- Dropping the image quality for faster loading

## Chapter 17: Generating Images with PHP

- Annotating the image with some descriptive text or a caption
- Copying a portion of another image into it to use as a watermark for copyright purposes

In the following sections you take a look at how to apply a watermark to an image, and also how to create thumbnails of your images.

## Applying a Watermark

If you are working on a Web site that displays original art or photographs, you may want to protect your or your clients' intellectual property from being stolen. A common way of doing this is to apply a watermark to discourage other people from using it as their own. Here's how to do it.

First, create a simple copyright image (such as Figure 17-17) in an image editor such as Photoshop. To do this, add some black text to a white background and save the image as a PNG file with eight-color palette. You may see this is done later in the section below:

> MATT DOYLE, 2008

Figure 17-17

## Copying the Watermark into the Image

Here's the script to create the watermark image. Save this file as watermark.php. Figure 17-18 shows an example result.

```php
<?php
$MyImage = imagecreatefromjpeg( "lucky.jpg" );
$MyCopyright = imagecreatefrompng( "copyright.png" );

$dstWidth = imagesx($MyImage);
$dstHeight = imagesy($MyImage);
$srcWidth = imagesx($MyCopyright);
$srcHeight = imagesy($MyCopyright);

$destX = ($dstWidth - $srcWidth) / 2;
$destY = ($dstHeight - $srcHeight) / 2;

imagecopy($MyImage, $MyCopyright, $destX, $destY, 0, 0, $srcWidth, $srcHeight);

header( "Content-type: image/jpeg" );
imagejpeg($MyImage);
imagedestroy($MyImage);
imagedestroy($MyCopyright);
?>
```

## Part III: Using PHP Practice

First, you open the original image that you want to watermark:

```php
$MyImage = imagecreatefromjpeg("lucky.jpg" );
```

Then you open your copyright image. Because it's a PNG file, use the imagecreatefrompng function to open the file:

```php
$MyCopyright = imagecreatefrompng("copyright.png" );
```

To position your copyright notice in the center of the image you have to know the dimensions of each of your images. The function `imagesx()` returns the width of an image, and the function `imagesy()` returns an image's height. Both functions take the image resource of the image that you would like to get the width or height. The script gets the width and height of the original image and the copyright notice:

```php
$destWidth = imagesx($myImage);
$destHeight = imagesy($myImage);
$srcWidth = imagesx($myCopyright);
$srcHeight = imagesy($myCopyright);
```

You now need to work out the top-left corner where the copyright notice needs to be placed. To work out the x position of the corner, subtract the width of the copyright notice from the width of the image and divide the difference by two. To get the y position, perform the same calculation using the image heights:

```php
$destX = ($destWidth - $srcWidth) / 2;
$destY = ($destHeight - $srcHeight) / 2;
```

Once you know where to put the copyright notice, you can go ahead and copy it into the image to be watermarked. The function to do this is `imagecopy()`:

```php
imagecopy($myImage, $myCopyright, $destX, $destY, 0, 0, $srcWidth, $srcHeight);
```

`imagecopy()` takes eight parameters, as follows:

- The first parameter is the image into which the data is copied — the image that you want to watermark
- The second parameter is the image from where the data is being copied — the copyright image
- The third and fourth parameters are the x and y coordinates of the position in the destination image where the image data is be copied. They mark the top-left corner of the block of data that is being copied across
- The next two parameters are x and y coordinates indicating the top-left corner of the block to copy in the source image
- The final two parameters indicate the width and height of the block to copy

In this case you want the entire image to be copied across, so you use 0, 0 as the top-left position of the block to copy, and the entire width and height of your copyright image as the width and height of the block.

After the data is copied across, you output the image as usual. Remember to clean up the memory that both images have used:

```php
header( "Content-type: image/jpeg" );
imagejpeg($myImage);
imagedestroy($myImage);
imagedestroy($MyCopyright);
?>
```

![](img/ede05b7b77968b82cbd9a513122fb183_562_0.png)

Figure 17-18

There's a slight problem here. As you can clearly see, the image is obscured. In the next section we refine the script so that you can see more of the image.

## Working with Transparency

Rather than copy the entire image as-is, you can copy just the white background. To do this, you need to make the white transparent.

## Part III: Using PHP Practice

First you need to get the color index of the white. You have two ways to do this. You can use the `imageat()` function to return the color at an exact pixel:

```php
$white = imageat($myCopyright, $x, $y);
```

Alternatively, you can use `imagecolxact()`, passing in the RGB values of the color:

```php
$white = imagecolxact($myCopyright, $red, $green, $blue);
```

The only drawback to the latter approach is if the color does not exist in your image. If you've saved the image as a JPEG you might have slight variations. So you can go ahead and use the `imagecolransparent()` function to make that color transparent. Add the following lines of code at the appropriate place in the watermark.php script:

```php
$destY = ($destHeight - $srcHeight) / 2;
$white = imagecolxact($myCopyright, 255, 255, 255);
imagecolortransparent($myCopyright, $white);
```

```php
imagecopy($myImage, $myCopyright, $destX, $destY, 0, 0, $srcWidth, $srcHeight);
```

Now the script's output (see Figure 17-19) looks more promising.

## Chapter 17: Generating Images with PHP

![](img/ede05b7b77968b82cbd9a513122fb183_564_0.png)

Figure 17-19

## Working with Opacity

The opacity of an image defines how transparent or opaque the image' pixels are. An image can range from completely see-through or transparent, to opaque, where you cannot see through the image at all. In the `imagecopy()` function in the previous section, the black text of the copyright message is opaque, and its white background was transparent. To make watermark less obvious, you can use the `imagecopymerge()` function to give the image a degree of transparency. The function works in the exact same way as the `imagecopy()` function, except that you also provide a ninth parameter, which controls how transparent or opaque the copied image is. A value of zero means that the copied image is completely transparent and you won't see it in the final image, whereas a value of 100 means that the copied image is completely opaque — in which the function operates like the `imagecopy()` function. So you can simply change this line in the `watermark.php` script:

```php
imagecopy($myImage, $myCopyright, $destX, $destY, 0, 0, $srcWidth, $srcHeight);
```

to read:

```php
imagecopymerge($myImage, $myCopyright, $destX, $destY, 0, 0, $srcWidth, $srcHeight, 50);
```
