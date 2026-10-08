# Drawing Figures and Graphing Data

471




This is the maximum length of the bars—from the baseline to the right margin—divided by
100 because the graph is going to show percentage values.

The second value is the total height that you need for the canvas:

```
$height = $num_candidates * ($bar_height + $bar_spacing) + 50;
```

This value is basically the height per bar times the number of bars, plus an extra amount for
title. Part 3 is shown in Listing 21.5.3.

# Listing 21.5.3 show_poll.php—Part 3 Sets Up the Graph, Ready for the Data to Be Added

```
****************************************************
Set up base image
****************************************************
// Create a blank canvas
$im = imagecreatruecolor($width,$height);

// Allocate colors
$white = imagecolorallocate($im, 255, 255, 255);
$blue = imagecolorallocate($im, 0, 64, 128);
$black = imagecolorallocate($im, 0, 0, 0);
$pink = imagecolorallocate($im, 255, 78, 243);

$text_color = $black;
$percent_color = $black;
$bg_color = $white;
$line_color = $black;
$bar_color = $blue;
$number_color = $pink;

// Create "canvas" to draw on
imagefilledrectangle($im, 0, 0, $width, $height, $bg_color);

// Draw outline around canvas
imagerectangle($im, 0, 0, $width-1, $height-1, $line_color);

// Add title
$title = 'Poll Results';
$title_dimensions = imagegetttfbox($title_size, 0, $font_name, $title);
$title_length = $title_dimensions[2] - $title_dimensions[0];
$title_height = abs($title_dimensions[7] - $title_dimensions[1]);
$title_above_line = abs($title_dimensions[5]);
$title_x = ($width-$title_length)/2; // center in x
$title_y = ($y - $title_height)/2 + $title_above_line; // center in y gap
```