
## 10 WORKING WITH IMAGES

![](img/19183d2b75bf6b509317c631c0e7b817_144_0.png)

This chapter shows you how to create and manipulate images such as GIFs and JPEGs. You won't be able to write scripts for heavy-duty image manipulation or processing such as online character recognition (your webserver limits the amount of computation that one script can do), but there are many small image operations that are very handy when developing a website.

### #66: Creating a CAPTCHA (Security) Image

Because many examples in this book use cURL to connect to and interact with websites, you know how easy it is to automate interactions with websites. You also know that if you have a site feature that you want no one but a real human to work with, you need to protect it. Otherwise, you may (at the very least) find your site completely overrun by spam comments. One way around this problem is to dynamically draw an image containing text that a user must type in order to post a comment (or perform some other human-only action, such as voting or rating). If you get the correct text from the user, the user is probably human.

This sort of test is named CAPTCHA, for *Completely Automated Public Turing Test to Tell Computers and Humans Apart*. It has two drawbacks. First, if you're blind, you can't read the text from the CAPTCHA image. Visually impaired people can use the Internet with the help of voice software to read the pages aloud, but this software can't interpret images without the descriptive alt attribute. A CAPTCHA locks out these users.

Furthermore, a CAPTCHA doesn't always work. Spammers are always looking for ways around your roadblocks. One of the more creative ways is linking the CAPTCHA image to a spammer-owned porn site with a label of INPUT THIS PHRASE AND SEE NAKED PEOPLE! Then some lonely guy inputs the password, which is then passed back to your site.

With these two shortcomings in mind, you should use CAPTCHAs sparingly and weigh them against alternatives such as the Akismet scanner. The CAPTCHA presented here is simple (see Figure 10-1 for a screenshot), but it is effective. To use it, your PHP must have the GD graphics library with Freetype support. To see if you have GD support, use phpinfo() as described in “#8: Revealing All of PHP’s Settings” on page 21. The output contains a section on GD with Freetype information if everything is okay. If the section is not there, rebuild PHP as described in “#18: Adding Extensions to PHP” on page 27.

![](img/19183d2b75bf6b509317c631c0e7b817_145_0.png)

### Figure 10-1: A CAPTCHA interface

You also need one or more fonts in the same directory as the script. It’s best to go with fonts that are at least halfway readable. There are two pieces to this system:

- 1. The main part is a script that creates CAPTCHA images. These images have irregular backgrounds, with strange swaths of color and lines running both horizontally and vertically. Then the script picks a passphrase, stores it in the `$_SESSION['tt_pass']` variable, and draws each letter in the passphrase differently. Finally, it sends the image output.
- 2. The second piece is a script to compare a CAPTCHA form’s input with the `$_SESSION['tt_pass']` variable. The script here is a simple demonstration, but because the image-generator script does most of the work, you won’t need to do much to make it fit your own needs.

Let's start with the image generator. The first step is to set several configuration variables for the image generator. The length of the passphrase, the image size, and the place to look for fonts:

```php
<?php
/* captcha_image.php */

/* Passphrase length */
$pass_length = 4;

/* Image dimensions */
$width = 200;
$height = 60;

/* TTF font path */
$font_path = dirname(__FILE__);
```

Now let's create the passphrase. Unlike most passwords, this doesn't need to be particularly challenging: There's no need to annoy your users more than you have to.

```php
session_start();

/* Create a passphrase. */
$passwd = "";
$i = 0;
while ($i < $pass_length) {
    $passwd .= chr(rand(97, 122));
    $i++;
}
```

We'll put the passphrase in a session variable. Therefore, it never appears in any pages in any form of encoding. This avoids the need to come up with an encoding that someone will just break.

```php
/** Store passphrase. */
$_SESSION["tt_pass"] = $passwd;
```

Before drawing anything, we want to make sure that we have some fonts to use for the image. This code creates a list of fonts in the current directory. If you'd like to make this part faster, you can set the $fonts array to a set of TrueType font filenames:

```php
/** Get a list of available fonts. */
$fonts = array();

if ($handle = opendir($font_path)) {
    while (false !== ($file = readdir($handle))) {
        /* Look for TTF fonts. */
        if (substr(strtolower($file), -4, 4) == '.ttf') {
            $fonts[] = $font_path . '/' . $file;
        }
    }
}
if (count($fonts) < 1) {
    die("No fonts found!");
}
```

The client has to know what kind of image you’re sending. This script creates a JPEG image, so it sends that MIME type. In addition, we don’t want the browser to cache the image, so we’ll send several cache-invalidating headers:

```php
/* Image header */
header("Content-Type: image/jpeg");
/* Invalidate cache. */
header("Expires: Mon, 01 Jul 1998 05:00:00 GMT");
header("Last-Modified: " . gmdate("D, d M Y H:i:s") . " GMT");
header("Cache-Control: no-store, no-cache, must-revalidate");
header("Cache-Control: post-check=0, pre-check=0", false);
header("Pragma: no-cache");
```

With all of the preparatory work complete, we can now start creating the image. GD functions begin with an image prefix. To initialize a color image canvas, use imagecreatetruecolor().

```php
/* Create image. */
$img = imagecreatetruecolor($width, $height);
```

The first thing we’ll draw is a rectangle to cover the entire background. To draw anything, you need to allocate a color in the image with imagecreatetruecolor(). The second, third, and fourth parameters to this function are the red, green, and blue values of the color, respectively. The value is an integer between 0 and 255, with 0 being the darkest and 255 being the lightest. The following statement creates a random pastel color:

```php
/* Fill background with a random shade of pastel. */
$bg = imagecolorallocate($img, rand(210,255), rand(210,255), rand(210,255));
```

Now let’s draw that rectangle with the imagefilledrectangle() function. The rectangle is parallel to the image axes, so you can define it by two points: (0, 0) and ($width, $height):

```php
imagefilledrectangle($img, 0, 0, $width, $height, $bg);
```

To convolute the background some more, we’ll draw several vertically oriented polygons across the canvas. The following loop creates the polygons with the imagefilledpolygon() function. This is different than drawing a rectangle because a polygon can have three or more sides in any orientation, so you need to provide an array of points as a parameter (here, $poly_points) instead of two sets of coordinates.

Try not to get sucked into the details of this loop. It is not a terribly important part of this script.

```php
/** Make the background jaggedly by creating different-colored
four-cornered polygons to cover the background area. */
/** Create swaths between 10 and 30 pixels wide across the image. */
$right = rand(10, 30);
$left = 0;
while ($left < $width) {
    $poly_points = array(
        $left, 0,               /* Upper left */
        $right, 0,              /* Upper right */
        rand($right-25, $right+25), $height,   /* Lower right */
        rand($left-15, $left+15), $height);    /* Lower left */
    /** Create the polygon, using four points from the array. */
    $c = imagecolorallocate($img, rand(210,255), rand(210,255), rand(210,255));
    imagefilledpolygon($img, $poly_points, 4, $c);
    /** Advance to the right edge. */
    $random_amount = rand(10, 30);
    $left += $random_amount;
    $right += $random_amount;
}
```

To further thwart those who might use OCR software to try to break this system, let's draw some random horizontal and vertical lines across the screen. To mix it up even more, we'll define a different color range for the lines for each image. By choosing random lower and upper bounds for the colors, the lines may or may not vary in intensity and will vary in consistency from image to image.

```php
/** Choose base value range for vertical and horizontal lines. */
$c_min = rand(120, 185);
$c_max = rand(195, 280);
```

To draw the vertical lines, start at the left side and pick a thickness and a slight offset to tilt the line. Then pick a color (using the preceding bounds), draw the line as a polygon, and advance to the right by yet another random amount:

```php
/** Draw random vertical lines across the width. */
$left = 0;
while ($left < $width) {
    $right = $left + rand(3, 7);
    $offset = rand(-3, 3);   /* Offset for angle */
    $line_points = array(
        $left, 0,       /* Upper left */
        $right, 0,      /* Upper right */
```
