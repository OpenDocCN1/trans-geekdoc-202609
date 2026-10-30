# Filled Shapes

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

![](bbox=[0.07, 0.62, 0.43, 0.82])

Figure 2.10
Drawing a filled shape.
© 2014 Python Software Foundation.