# Part III: Using PHP in Practice

![](bbox=[0.147, 0.091, 0.755, 0.477])

Figure 17-16

# How It Works

The code is relatively straightforward and shouldn't pose any problems. The imagecreatefromjpeg() function creates a new image resource from the existing image:

```
$myImage = imagecreatefromjpeg("lucky.jpg");
```

Then the script sends a header to the Web browser, telling it to expect some JPEG image data:

```
header("Content-type: image/jpeg");
```

All that's left to do is send the data and clean up the image from memory:

```
imagejpeg($myImage);
imagedestroy($myImage);
```

Of course, the script doesn't do anything that you couldn't do yourself using plain HTML, so you may be wondering what the point is. Well, being able to open existing images and manipulate them before sending them to the browser is useful for a number of reasons. Some of the things that you can do to an image using the GD image functions include:

+   - Resizing the image to create a thumbnail for display

+   - Dropping the image quality for faster loading

522