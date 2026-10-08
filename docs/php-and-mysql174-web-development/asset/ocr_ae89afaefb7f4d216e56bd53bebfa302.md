# Chapter 21. Generating Images

After you have this information, you test the loop condition:

```
while ($font_size > 8 &&
  ($height_text > $height_image_wo_margins ||
  $width_text > $width_image_wo_margins)
 {
```

You test two of conditions here. The first is that the font is still readable; there's no point in making it smaller than 8-point type because the button becomes too difficult to read. The second set of conditions tests will ensure the text fit inside the drawing space you have available for it.

Next, you check to whether the iterative calculations found an acceptable font size and report an error if:

```
if ($height_text > $height_image_wo_margins ||
  $width_text > $width_image_wo_margins)
{
  // no readable font size will fit on button
  echo '<p>Text will not fit on button.</p>';
}
```

# Positioning the Text

If all is well, you work out a base position for the start of the text. This is the midpoint of the available space.

```
$text_x = $width_image/2.0 - $width_text/2.0;
$text_y = $height_image/2.0 - $height_text/2.0;
```

Because of the calculations with the baseline relative coordinate system, you need to add some corrections:

```
if ($left_text < 0)
{
  $text_x += abs($text_text); // add factor for left overhang
}
```

```
$above_line_text = abs($bbox[7]); // how far above the baseline;
$text_y += $above_line_text; // add baseline factor
```

```
$text_y = -2; // adjustment factor for shape of your template
```

These correction allow for the baseline and a little adjustment because the image is bit "top heavy.",

# Writing the Text onto the Button

After that, it's smooth sailing. You set up the text color, which will be white:

```
$white = imagecolorallocate($im, 255, 255, 255);
```