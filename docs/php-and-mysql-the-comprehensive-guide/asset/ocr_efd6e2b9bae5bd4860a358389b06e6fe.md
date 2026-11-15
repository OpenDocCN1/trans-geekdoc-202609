In many installations with hosts and in standard packages, the line is already commented out and GD 2 is onboard. You can then use phpinfo() to test whether the installation has worked. JPEG and TrueType font support is already included.

# ## 30.2 GD 2 in Action

GD 2 by Thomas Boutell is not written exclusively for PHP, but it has reached many developers with PHP. It offers options for drawing shapes and text, but also allows existing images to be modified.

# ### 30.2.1 Basic Framework

If you create a graphic with GD 2, the graphic is a PHP file. The basic structure is always the same. First, you must output the data type via the HTTP header:

```
header("Content-type: image/png");
```

Content-type is the file type of the image. You have the following options:

```
header("Content-type: image/gif");
```

for GIF or

```
header("Content-type: image/jpeg");
```

for JPEG.

> **Note**
> 
> GIF only supports 256 colors, all of which are collected in a color palette. Due to its area-oriented compression algorithm, GIF is mainly suitable for flat graphics such as buttons and offers transparency and the option of GIF animations as special functions. JPEG uses 16.78 million colors and is preferred for photos. However, JPEG compresses with lossy compression, which ultimately leads to unsightly pixelated effects, called JPEG artifacts, if the compression is too strong.
> 
> PNG was created as an alternative to both formats: PNG-8 (and lower) stores 256 colors, while PNG-24 supports 16.78 million colors. PNG-8 supports simple transparency. With PNG-24, the files are usually somewhat larger than with JPEGs, but they compress without loss, and in contrast to PNG-8 and JPEG, the alpha transparency helps to create pretty effects. Alpha transparency means that pixels can also be semitransparent, which enables smooth transitions with the background.

Now you need to create an image. To do this, use the imagecreatetruecolor(width, height) function: