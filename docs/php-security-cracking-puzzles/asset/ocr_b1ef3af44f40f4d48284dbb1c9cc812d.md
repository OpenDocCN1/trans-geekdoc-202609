```
}
//////////////////////////////////////////////////////////////////////
// The scaling block
//////////////////////////////////////////////////////////////////////
// Calculating the maximum value
$max = max($bar_chart);
// Calculating the minimum value
$min = min($bar_chart);
for($i = 0; $i < count($bar_chart); $i++)
{
  $bar_chart[$i] = (int)($bar_chart[$i] - $min) / ($max - $min)*100;
}
//////////////////////////////////////////////////////////////////////
// The block for creating the bar graph
//////////////////////////////////////////////////////////////////////
// Creating a blank 200 x 200 pixel image
$img = imagecreatetruecolor(200, 200);
// If the image is not created,
// the script execution is terminated.
if (!$img) exit();
// Defining white on the image
$white = imagecolorallocate($img, 255, 255, 255);
// Filling the image with white
imagefill($img, 1, 1, $white);
// Defining the bar graph's background color
$color = imagecolorallocate($img, 240, 240, 240);
// The $cx and $Scy variables define the center
$cx = 50;
// The bar width
$w = 5;
// The lower coordinate of the graph's bars is in the upper left origin.
$yl = 200;
// The maximum vertical image size
$max_y = 200;
// The bar graph's starting X coordinate
$x1 = 0;
foreach ($bar_chart as $value)
{
```