# Chapter II.8: Using Information from Other Sites

```
// Defining colors for each bar
$color = imagecolorallocate($img, 0, 0, 0);
// Normalizing the bar height
// Converting percentages into pixels
$y2 = $y1 - $value*$max_y/100;
// Defining the second coordinate of the rectangle
$x2 = $x1 + $w;
// Drawing the rectangle
imagefilledrectangle($img, $x1, $y1, $x2, $y2, $color);
// The gap between the bars
$x1 = $x2 + 5;
}
// Displaying the image in the browser in the PNG format
header("Content-type: image/png");
imagepng($img);
```

The exchange rate history is placed into the $bar_chart array; the values of the array are converted into relative units in the 1 to 100 range and are then displayed as a bar graph using the GD graphics library.