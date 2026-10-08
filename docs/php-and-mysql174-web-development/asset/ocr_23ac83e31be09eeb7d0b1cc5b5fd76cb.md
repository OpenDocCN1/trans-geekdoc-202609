This function takes the image identifier, the start coordinates of the area to paint (x and y), and the color to fill in as parameters.

Note
The coordinates of the image start from the top-left corner, which is x=0, y=0. The bottom-right corner of the image is x=$width, y=$height. This is normal for computer graphics, and the opposite of typical math graphing conventions, be beware!

Next, you draw a line from the top-left corner (0, 0) to the bottom-right corner ($width, $height) of the image:

```
imagestring($im, 0, 0, $width, $height, $width);
```

This function takes the image identifier, the start point x and y for the line, the end point, and then the color as parameters.

Finally, you add a label to the graph:

```
imagestring($im, 4, 50, 150, 'Sales', $width);
```

The imagestring() function takes some slightly different parameters. The prototype for this function is

```
int imagestring(resource img, int font, int x, int y, s, int color);
```

It takes the image identifier, the font, the x and y coordinates to start writing the text, the text to write, and the color.

The font is a number between 1 and 5. These numbers represent a set of built-in fonts in latin2 encoding, with higher numbers corresponding to larger fonts. As an alternative to these fonts, you can use TrueType fonts or PostScript Type 1 fonts. Each of these sets has a corresponding function set. We use the TrueType functions in the next example.

A good reason for using one of the alternative function sets is that the text written by imagestring() and associated functions, such as imagechar() (write a character to the image) is aliased. The TrueType and PostScript fonts produce antialiased text.

If you're not sure what the difference is, look at Figure 21.2. Where curves or angled lines appear in the letters, the aliased text appears jagged. The curve or angle is achieved by using a "staircase" effect. In the antialiased image, when curves or angle appear in the pixels, colors between the background and the text color are used to smooth the text's appearance.

# NormalnAnti-aliased

Figure 21.2 Normal text appears jagged, especially in a large font size. Antialiasing smooth the curves and corners of the letters