
## Filled Shapes

Earlier you saw how to draw a square with the turtle. Suppose you want to draw not just the outline of a square, but a square filled with a given color. Turtle graphics allows you to do so by using the fillcolor, begin_fill, and end_fill functions.

You begin by setting the fill color of the shape. The fillcolor function does this using a color argument, as discussed in the previous section. The initial fill color is black. Note that when you set the fill color, this color also fills the shape of the turtle.

You then call the begin_fill function, followed by the commands that draw the square. Finally, you call the end_fill function, which tells turtle graphics to fill any fillable shapes drawn since the last call of begin_fill. The next session draws a filled square of length 70, with a black outline and a red interior. The result is shown in Figure 2.10 (color omitted, of course).

```
>>> reset()
>>> fillcolor("red")
>>> begin_fill()
>>> forward(70)
>>> left(90)
>>> forward(70)
>>> left(90)
>>> forward(70)
>>> left(90)
>>> forward(70)
>>> left(90)
>>> end_fill()
```

![](img/4dc3f6307b32ff815a6d58ec1c84708c_73_0.png)

Figure 2.10
Drawing a filled shape.
© 2014 Python Software Foundation.

The `color` function combines actions of the `pencolor` and `fillcolor` functions. Its first argument is the pen color, and its second argument is the fill color. When called with no arguments, `color` returns a tuple containing these two colors. Thus, the expression `color("blue", "red")` would set the pen color to blue and the fill color to red.

Table 2.6 summarizes the functions related to colors in turtle graphics.

Table 2.6 Functions Related to Colors

| Function | What It Does |
|---|---|
| `bgcolor(color)` | Sets the color of the canvas to `color` |
| `color(pColor, fColor)` | Sets the turtle’s pen color to `pColor` and its fill color to `fColor` |
| `fillcolor(color)` | Sets the turtle’s fill color to `color` |
| `pencolor(color)` | Sets the turtle’s pen color to `color` |
| `begin_fill()` | Begins a sequence of commands to draw filled shapes |
| `end_fill()` | Ends a sequence of commands to draw filled shapes |

## DRAWING CIRCLES

Turtle graphics provides just one built-in function that draws a shape. This function, named `circle`, expects the circle’s radius as an argument. Optional arguments include the `extent` (the portion of the circle to be drawn, in degrees) and the `steps` (the number of lines used to draw the circle’s circumference). You supply the `extent` argument when you want to draw an arc. Filling an arc requires you to connect the turtle’s starting and ending points.

To get a feel for how the circle function works, run the following code in the shell:

```
>>> from turtle import *
>>> home()
>>> circle(50)
```

Note that the turtle starts by facing east at the home position, draws the circle by repeatedly moving forward and turning left, and finally returns to its original position and heading.

Now consider how to draw a filled pie slice within this circle. The slice is a filled arc that occupies the lower-right quarter of the circle, as shown in Figure 2.11.

![](img/4dc3f6307b32ff815a6d58ec1c84708c_75_0.png)

Figure 2.11
Drawing a circle containing a filled arc.
© 2014 Python Software Foundation.

You start by running begin_fill to begin drawing a filled shape. To draw the arc, the turtle starts at the home position and draws a circle with a radius of 50 and an extent of 90 degrees. The turtle then draws two line segments to close the arc, create the pie slice, and allow it to be filled. To do this, you move the turtle to position (0, 50), which is the center point of the circle, and then return it to the home position. Finally, you run end_fill to fill the new shape. Here is the code:

```
>>> begin_fill()
>>> circle(50, 90)
>>> goto(0, 50)
>>> home()
>>> end_fill()
```

The key to working with circles and arcs is to set the initial position and the heading of the turtle to get the results that you want. For example, suppose you want a half-moon shape whose center point is the origin, whose radius is 50, and whose flat side lies along the x-axis, as shown in Figure 2.12.

![](img/4dc3f6307b32ff815a6d58ec1c84708c_76_0.png)

Figure 2.12
Drawing a half moon.
© 2014 Python Software Foundation.

The turtle starts drawing the circle from position (−50, 0), with the turtle’s heading at 270 degrees. Moving to that position from the home position draws half of the flat side of the arc. Then the turtle turns right 90 degrees. To draw the arc, the turtle draws the circle with an extent of 180 degrees. After drawing the arc, the turtle draws the other half of its flat side by returning home. Here is the code:

```
>>> reset()
>>> begin_fill()
>>> goto(-50, 0)
>>> right(90)
>>> circle(50, 180)
>>> home()
>>> end_fill()
>>> hideturtle()
```

## DRAWING TEXT

You draw text in the turtle’s window by calling the write function. The required argument is a string. Optional arguments direct the turtle to move during the drawing, align the text to the left, center, or right of the turtle’s initial position, and use a text font that you supply. The following code fragments show two ways to draw some text, with and without the optional arguments. The results are shown in Figure 2.13.

```
>>> from turtle import *
>>> reset()
>>> write("Python is way cool!")
>>> up()
>>> goto(0, 60)
>>> write("Python is way cool!", move = True, align = "Center",
    font = ("Arial", 14, "bold"))
```

![](img/4dc3f6307b32ff815a6d58ec1c84708c_77_0.png)

Figure 2.13
Drawing text.
© 2014 Python Software Foundation.

Note that the default alignment is left, the turtle does not move, and the text font is quite small. A font is expressed as a tuple, which contains the font name, point size, and style. Note also that if the turtle moves, it draws a line under the text. To avoid this effect, pick up the turtle before calling write.

## USING THE TURTLE'S WINDOW AND CANVAS

The turtle graphics window provides a partial view of a canvas or drawing area that lies beneath it. If the turtle moves beyond this visible area, you can either enlarge the window or scroll to the area of the canvas that you want to view.

The canvas is initially 400 pixels wide by 300 pixels high. The function screensize returns the current dimensions of the canvas. When you supply the first two optional arguments to this function, it resets the width and height of the canvas to these integers. An optional third argument is a color value for the background color.

The window’s initial width is 50% of your screen’s width and 75% of its height. The window is centered on your screen. The functions window_width and window_height return the window’s current width and height, respectively. (Recall that the user may alter these dimensions with the mouse at any time.)

To change the size and position of the window under program control, call the setup function. The first two arguments to set up are the window’s dimensions. If these arguments are integers, they represent the actual width and height. If these arguments are floating-point numbers, they represent fractions of the screen’s width and height. The third and fourth arguments represent the window’s position relative to the boundaries of the screen. If these arguments are positive, they indicate the distances of the window from the left boundary and the top boundary, respectively. If they are negative, the distances are relative to the right and bottom edges of the screen.

The next shell session places a turtle graphics window in the upper-right corner of the screen. The background color is black, and the pen and fill colors are white.

```
>>> setup(400, 300, -400, 50)
>>> screensize(1650, 1080, "black")
>>> color("white", "white")
```

Table 2.7 summarizes the functions related to the window and canvas in turtle graphics.

Table 2.7 Functions Related to the Window and Canvas

| Function | What It Does |
|---|---|
| screensize() | Returns the tuple (canvasWidth, canvasHeight). |
| screensize(canvwidth, canvheight, bg) | Sets the width, height, and background color of the canvas. (All arguments are optional.) |
| setup(width, height, startx, starty) | Sets the size and position of the turtle graphics window. width and height can be integers (the actual number of pixels) or floats (the percentages of the screen’s dimensions). startx and starty can be positive (the position in pixels from the left edge of the screen) or negative (the position in pixels from the right edge of the screen). |
| window_height() | Returns the height of the turtle graphics window. |
| window_width() | Returns the width of the turtle graphics window. |
