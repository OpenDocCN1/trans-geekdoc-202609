
# sleep(integer seconds)

The sleep function causes execution to pause for the given number of seconds.

```php
<?php
print(microtime());
sleep(3);
print("<BR\n");
print(microtime());
?>
```

# usleep(integer microseconds)

The usleep function causes execution to pause for the given number of microseconds. There are a million microseconds in a second.

```php
<?php
print(microtime());
usleep(30);
print("<BR\n");
print(microtime());
?>
```

## Chapter 12. IMAGE FUNCTIONS

Analyzing Images

Creating JPEG, PNG, and WBMP Images

The majority of the image functions draw their functionality from the GD library, free software for manipulating images. These require the GD extension to be loaded, via php3.ini or the di extension. The functions in the first section of this chapter are not part of the GD extension and should always be available to you.

The GD library was created at Boutell.com, a company that has contributed several Open Source tools to the Web community. The library historically supported GIF image creation, but in 1999 this functionality was pulled in favor of PNG format files. The compression algorithm used in GIF creation is patented, which means permission must be granted to software authors who use PNG, on the other hand, is an open specification. It also happens to be superior to GIF. Support for PNG added to the fourth generations of the two most popular browsers, Netscape Navigator and Microsoft Internet Explorer, using PNG is feasible. In 2000, support for JPEG and WBMP images was added to GD.

The GD library's home on the Web is <http://www.boutell.com/gd/>. The URL for PNG's page home is <http://www.cdrom.com/pub/png>.

Two of the functions in this section require a special library to deal with TrueType fonts: imageffbox and imagettext. Likewise, the functions that work with PostScript fonts require their own library. Consequently, these functions may not be available to you, depending on how PHP was compiled.

Chapter 19, "Generating Graphics," makes use of the functions in this chapter to explore some practical uses.

## Analyzing Images

These functions are part of PHP's core and do not require loading an extension.

### string gamma_correct_tag(string color, double original, double new)

The gamma_correct_tag adjusts an HTML color from one gamma to another. Video display hardware is given a gamma rating that describes relatively how bright images appear. Identical images appear lighter on Macintosh than on the typical Windows clone. The W3C has a discussion about color spaces that includes information about gamma values: <http://www.w3.org/Graphics/Color/sRGB.html>.

## Core PHP Programming

```php
<?php
//go from Windows gamma to Macintosh gamma
$color = gamma_correct_tag("#CC000", 2.2, 1.571);

print("FONTCOLOR=$color");
print("Sample Text");
print("/FONT");
?>
```

### string getimagesize(string filename, array image_info)

The getimagesize function returns a four-element array that tells you the image size of the filename. The contents of this array are listed in Table 12.1. The file must be a graphic file in one of three formats: GIF, JPEG, or PNG.

The optional image_info argument will be set with additional information from the file. At the time of writing, this array is with APP markers 0-15 from JPEG files. One of the most common is APP13, which is an International Press Telecommunications Council (IPTC) block. These blocks are used to communicate information about electronic media to news agencies. They are stored in binary, so decode them you use the iptparse function. You can find out more about the IPTC at their Web site: http://www.iptc.org/iptc/.

| Table 12.1. Array Elements for getimagesize |
| Element | Description |
| :--- | :--- |
| 0 | Width in pixels |
| 1 | Height in pixels |
| 2 | Image Type (GIF = 1, JPG = 2, PNG = 3) |
| 3 | String like "height=150 width=200", usable in IMG tag |
| bits | Bits per pixel for jpgs |
| channels | Samples per pixel for jpegs |

Note that the image_info argument must be passed by reference, which means it must be preceded by an ampersand.

```php
<?php
$image_file = "php.jpg";
$image_size = getimagesize($image_file, &$image_info);
print("IMG SRC=$image_file $image_size[3]>BR\n");

//show information if it exists
while (list($key, $value) = each($image_info)) {
    print($key . "BR\n");
}
?>
```

### string iptcbed(string iptc, string file, integer spool)

The iptcbed function adds IPT blocks to JPEG files. By default the blocks are added to the file, and the modified file is returned. The spool argument allows you to change this behavior. If the spool flag is 1 or 2, the modified JPEG will be sent directly to the browser. If the spool is 2, the JPEG will not be returned as a string.

### array iptcparse(string iptc_)

The iptcparse takes an IPTC block and returns an array. See getimagesize to see how to use.

## Creating JPEG, PNG, and WBMP Images

All the functions in this section require the GD library. To get started, you must ensure PHP is compiled with the support. If it is not, you may need to recompile PHP.

### boolean imagearc(integer image, integer x, integer y, integer width, integer height, integer start, integer end, integer color)

The imagearc function draws an ellipse in image. The start and end are given in degrees. The center is specified by x and y. The width and height are the dimensions of the ellipse. The color is the color of the ellipse.

### integer imagecolorallocate(integer image, integer red, integer green, integer blue)

The imagecolorallocate function allocates a color in the given image. The color is specified by the amount of red, green, and blue. An identifier is returned for referring to this color in other functions.

### boolean imagecup(integer image, integer font, integer x, integer y, string character)

The imagecup function operates identically to imagechar, except that the character is oriented vertically, bottom to top.
