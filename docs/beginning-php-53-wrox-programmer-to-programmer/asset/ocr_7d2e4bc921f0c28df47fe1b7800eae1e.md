# Chapter 17: Generating Images with PHP

of the rectangle that the curve should begin. The last parameter is, of course, the color of the rectangle. Figure 17-14 shows how the parameters passed to the roundedRectangle() function are used.

![](bbox=[0.348, 0.143, 0.725, 0.283])

The function first draws the line across the top of the rectangle. It doesn't draw the line all the way from $x1 to $x2 because it has to take the curves of the corners into account. To do this it adds the $curveDepth value to the $x1 position, and subtracts it from the $x2 position:

```
imageline($ image, ($x1 + $curveDepth), $y1, ($x2 - $curveDepth), $y1,
color);
```

Because the line is horizontal, both points use the same $y position. The next line goes along the bottom of the rectangle in a similar fashion:

```
imageline($ image, ($x1 + $curveDepth), $y2, ($x2 - $curveDepth), $y2,
color);
```

The next two uses the vertical lines that go down the left- and right-hand sides of the rectangle. The function uses the same x values for each of the lines ($x1 for the left-hand line and $x2 for the right-hand side), and alters the $y values appropriately so that the height of the lines fits with the curved corners:

```
imageline($ image, $x1, ($y1 + $curveDepth), $x1, ($y2 - $curveDepth),
color);
imageline($ image, $x2, ($y1 + $curveDepth), $x2, ($y2 - $curveDepth),
color);
```

Next function draws the curved corners, starting with the top-left corner. In order to calculate the center point of the arc (see Figure 17-15), the function adds the value of $curveDepth to both the $x1 and the $y1 values. To get the arc's width and height, the function needs to double the $curveDepth value, because $curveDepth is the radius of the arc.

![](bbox=[0.398, 0.788, 0.603, 0.906])

519