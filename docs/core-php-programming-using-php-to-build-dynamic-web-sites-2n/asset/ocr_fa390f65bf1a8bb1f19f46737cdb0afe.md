```
//send image
header("Content-type: image/jpeg");
imagejpeg($image);
?
```

# boolean imagejpeg(integer image, string filename, integer
quality)

The imagejpeg function either sends an image to the browser or writes it to a file. If a filename is provided, a JPEG file is created. Otherwise, the image is sent directly to the browser. The optional quality argument determines the compression level used in the image, and should range from 0 (lowest quality) to 10 (highest quality).

```
?
/*
 ** create a blue square, save to disk
 */
// create image if it doesn't exist
// or its older than an hour
if(!file_exists("blue_square.jpg") OR
(filetime("blue_square.jpg") < (time() - 3600)))
{
    // send debugging info
print("<-creating image->\n");

// create a blue square
$image = imagecreate(200, 100);
$colorBlue = imagecolorallocate($image, 128, 128, 255);
$colorWhite = imagecolorallocate($image, 255, 255, 255);
imagefill($image, 0, 0, $colorBlue);

// add file creation time to image
imagestag($image, 4, 10, 10,
date("Y-m-d H:i:s"),
$colorWhite);

// write it to a file
imagejpeg($image, "blue_square.jpg");
}

// print image tag that show image
print("<IMG SRC="blue_square.jpg" " . 
"HEIGHT="100" WIDTH="200" BORDER="0">");
?
```

# boolean imageline(integer image, integer start_x, integer
start_y, integer end_x, integer end_y, integer color)