The default style is a pie shape, and you can specify the color of the pie using the -fill option. To show the other two styles, I draw two more arcs in the right side of the window. The first is a chord, which is like the pie crust of a pie shape: It's surrounded by the arc on the circle and a line connecting the two points (in this case, the two points are the default points: 0 degrees and 90 degrees). The second is an arc, which is just a curve along the perimeter of the imaginary circle.

# ## Lines and curves

Here's a cool thing: With the canvas widget, you can draw a sequence of lines and then, by setting a single option, you can generate a curve that fits the lines you drew. The line command is easy; you just specify a sequence of numbers representing points as I do in the following code:

```
```
canvas .mycanvas -width 300 -height 350
pack .mycanvas
```
```

```
```
.mycanvas create line \
10 10 75 100 125 50 250 200 40 200 \
-smooth off -width 1 -fill black -width 10 \
-joinstyle round
```
```

```
```
.mycanvas create line \
10 40 75 130 125 80 250 230 40 230 \
-smooth off -width 1 -fill black -width 10 \
-joinstyle miter -cap round
```
```

```
```
.mycanvas create line \
10 70 75 160 125 110 250 260 40 260 \
-smooth off -width 1 -fill black -width 10 \
-joinstyle bevel -arrow last
```
```

In the first line command, I have a bunch of line segments. The first starts at point 10,10 and goes to point 75,100. The next starts at that point — 75,100 — and goes to 125,50. The next starts there at 125,50 and goes to 250,200. And the final one starts there at 250,200 and goes to 40,200. Easy. The window for this code is shown in Figure 8-8.

With the line command, you also have several options. You can specify the width of the line; in the preceding code, all my lines are really fat, measuring in at 10 pixels. You can also specify a color (mine are all black, but you can use other colors like bisque3, whatever that is, or OliveDrab2).

You can also specify a cap style for the end of each line. Your choices are bevel, miter, and round. You can try out these different types and see what they look like.