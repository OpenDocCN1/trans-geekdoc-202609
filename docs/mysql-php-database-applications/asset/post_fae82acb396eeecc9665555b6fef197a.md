
## Session functions

These are explained in detail in Chapter 14. Sessions are means by which state is maintained between pages. Remember that HTTP, the language of the Web, does not allow servers to remember much of anything between requests for pages from a specific user. Sessions allow the server to keep track of activities by a single user.

## MySQL functions

These functions are explained in detail in Appendix J.

A total of 48 MySQL functions are available in the library. Only about a third of these are used in the applications in this book. You may find uses for some of the other MySQL functions in your applications, but you probably won’t use all of them.

## HTTP header functions

Three vital HTTP header functions exist, both of which you will need to get to know.

### header()

If you are going to be communicating with the browser or with other HTTP servers, this is the function to use.

```
int header (string string)
```

Essentially, you can send any header that would be expected under RFC 2616 (ftp://ftp.isi.edu/in-notes/rfc2616.txt), which defines HTTP. The RFC itself is a handful (and perhaps the sleepiest reading you’ll do all year). Here is a common header you are likely to send:

```
header("Location: http://www.php.net");
```

This is nothing more than a redirect: It sends the browser to a page you specify. If you have been working with straight HTML and JavaScript or the <META type=refresh> tag to do your redirects, you should switch to this type of header whenever possible. It will work for all browsers and the redirection will be totally transparent to the user.

![](img/47897cc2ae80cbce8ce42ba6e77e4d39_224_0.png)

IMPORTANT — no, make that VERY IMPORTANT — you cannot send a header after anything — ANYTHING — has been sent to the browser. If you send a header after even a hard return, you will get an error. If you send a hard return before your opening <?php tag, you will get an error. If there is a hard return in an included file that precedes your header() function, you will get an error. This should not be a problem you encounter frequently; your pages should be designed so that most of the logic is handled prior to the display. However, if you have a situation you just can’t work around, take a look at the output buffering functions.

### setcookie()

This is basically a specialized header function, because a cookie is set by nothing more than a specific HTTP header.

```
int setcookie (string name [, string value [, int expire [, string path [, string domain [, int secure]]]]])
```

The first argument will be the name of the cookie. The second will be the value. The expire value should be set with the time function. The following is a pretty typical use of setcookie():

```
setcookie("id", $id_val, time()+(24*60*60), "/", ".domain.com", 0);
```

This will set a cookie that will expire in 24 hours (24 × 60 × 60). The cookie will be available to every directory within domain.com. If you want to restrict it to a specific directory, you can change the / to a directory name.

- You can find more on cookies in Chapter 4 in the discussion on variables.
- In some versions of Internet Explorer, you must either give both time and path values or neither.

### headers_sent()

This function can keep you from sending headers after some text has been sent to the browser.

```
bool headers_sent(void)
```

If you are relying heavily on this function, you are probably not coding your pages properly.

## Image functions

PHP provides very powerful functions for generating and manipulating images.

### IMAGE FUNCTIONS USED IN THIS BOOK

Here is a rundown of the image functions used in this book.

### GETIMAGESIZE()

```
array getimagesize (string filename [, array imageinfo])
```

Given an image file as argument, this function returns an array containing the width of the image in pixels, the height of the image in pixels, a numeric flag containing the type of the image, and a text string containing the dimensions that can be used directly in an HTML IMG tag. Valid numeric flags include 1 for GIF, 2 for JPEG, and 6 for BMP.

So, given a JPEG of 468 × 60 pixels, getimagesize() would return the following:

```
Array
(
    [0] => 468
    [1] => 60
    [2] => 2
    [3] => height="60" width="468"
)
```

### IMAGECOPYRESIZED()

```
int imagecopyresized (resource dest_im, resource src_im, int destX, int destY, int srcX, int srcY, int destW, int destH, int srcW, int srcH)
```

This function is used to copy part of one image (referred to above as a resource), delineated by rectangular X and Y coordinates and offset, to another image. The arguments it takes are as follows:

- The destination image identifier
- The source image identifier
- The starting X coordinate on the destination image
- The starting Y coordinate on the destination image
- The starting X coordinate on the source image
- The starting Y coordinate on the source image
- The width in pixels of the destination image
- The height in pixels of the destination image
- The offset width to take from the source image
- The offset height to take from the source image

### IMAGECREATE()

```
resource imagecreate (int x_size, int y_size)
```

This function creates a new image with the given dimensions, and returns its identifier.

### IMAGECREATEFROMSTRING()

```
resource imagecreatefromstring (string image)
```

This function creates a new image from the image stream given in the argument string, and returns its identifier.

### IMAGEPNG()

```
int imagepng (resource image [, string filename])
```

Given an image identifier, imagepng() outputs an image stream, in PNG format, to either the user's browser or, if it is given a file name as a second argument, to the specified file.

### IMAGESX(), IMAGESY()

```
int imagesx (resource image)
```

```
int imagesy (resource image)
```

These two functions return the dimensions of the referenced image: imagesx() returns the width, and imagesy() returns the height.

### IMAGETYPES()

```
int imagetypes (void)
```

This function checks the configuration of the GD library that PHP is using to see which image types are supported. It returns a bitmask containing a value that corresponds to the AND sum of the constants that represent each image type. You can test for PNG support, therefore, with code like the following:

```
if (imagetypes() & IMG_PNG)
    echo "PNG support is enabled.";
```

### EXIF_IMAGETYPE()

```
int exif_imagetype (string filename)
```

exif_imagetype() examines an image file and determines the type of image it is, returning a numeric code, or FALSE if it is not a recognizable image type. PHP must be compiled with --enable-exif.

Refer to the online PHP manual (http://www.php.net/manual/en/ref.image.php) for a list of image types and their codes.

### EXIF_THUMBNAIL()

```
string exif_thumbnail (string filename [, int width [, int height [,
int imagetype]]])
```

If an image contains an embedded thumbnail, this function will retrieve the thumbnail as a data stream. For example:

```
<?php
$thumb= exif_thumbnail($imagefile, 40, 50);
echo $thumb;
?>
```

If the preceding code is stored as a file called thumbnail.php, a subsequent HTML call to this file as an image will display the thumbnail:

```
<img src="thumbnail.php" height="50" width="40">
```

## Mail function

If you have Sendmail or another suitable email program installed on your system, this function will take all the fuss out of sending email from your PHP pages.

> NOTE: Sendmail is the program most commonly used with PHP's mail function, but qmail with Sendmail wrappers will work, and Pegasus (http://pegasus.usa.com/) can apparently work on Windows (though we haven't tested it).

The mail() function sends an email from your PHP script.

```
bool mail ( string to, string subject, string message [, string additional_parameters] )
```

Your basic email will look like this:

```
mail("name@domain.com","Subject Text", "The complete message goes here");
```

And if you want to get a little fancier and include a From and a Cc, use the following:

```
mail("jay@trans-city.com","Test Message", "Here I am",
"From: Jay G \r\nCc: webmonkey@trans-city.com\r\nReply-to:
myname@mydomain.com");
```

Additional parameters have been added in the fourth argument, and the different parameters are separated by line feeds and newlines (\r\n).

> TIP: If you want to set up a large email system, don't use PHP. Better tools are out there. This function is intended for sending an occasional email from within PHP scripts.

> NOTE: If you'd like to send attachments in your PHP email, check out this excellent article at phpbuilder.com: http://phpbuilder.com/columns/kartic20000807.php3.

## URL functions

If you've ever looked at a query string, you may have noticed that the text you entered into your form fields has been changed. For example, spaces are turned into plus signs (+) and each ampersand (&) becomes %26. Many other characters are encoded. (All non-alphanumeric characters other than the hyphen (-), underscore (_), and dot (.) are replaced by a percent sign (%) and two characters).
