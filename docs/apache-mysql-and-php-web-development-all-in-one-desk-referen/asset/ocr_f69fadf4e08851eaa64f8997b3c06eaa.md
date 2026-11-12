Here's the buildmapimage.php file:

```
<?php
$pic = imagecreatefrompng("usmap.png");
$mycolor = imagecolorresolve($pic, 192, 0, 0);

// Calculate the location
$latitude = $_GET['latitude'];
$longitude = $_GET['longitude'];
$width = 557;
$height = 306;
$x = $width - (($longitude - 67) * ($width / 58));
$y = $height - ((($latitude - 25) * ($height / 24));

imagefilledrectangle($pic, $x-2, $y - 2, $x+2, $y+2,
        $mycolor);
header('Content-type:image/png');
imagepng($pic);
?>
```

This file first loads an existing image, usmap.png, with a function called imagecreatefrompng. Next, the program sets a color (red) that will be used later on for drawing a point on the map. Then the program extracts the latitude and longitude data and does a linear transformation (geek speak for adjusts the data) to fit the data points on the map. The map I make is 557 pixels wide by 306 pixels tall. The calculations that follow translate the latitude and longitude into pixels on the map.

Then the code draws a small box on the map at the calculated position in the color I defined earlier and, finally, sends the resulting graphic image to the browser.

The drawmap.php file shows up in the browser just like any other .html file; it contains text and images, like you would expect. What the users visiting the page don't realize is that the map was created dynamically.

If you want to see what this program will look like on-screen, hop over to www.jeffcogswell.com/dummies/usmaplookup.html. For the Latitude, enter any integer between 25 and 49. For the Longitude, enter any integer between 67 and 125.

# # Creating Thumbnail Images

Here's a handy little trick. Why take up space on your server with thumbnail images, when you can generate them dynamically? And why go through the headache of manually creating thumbnails for all the pictures from your trip to the Wisconsin Dells? Although thumbnail images don't have a huge impact on server space, you can have PHP generate them dynamically if you want.