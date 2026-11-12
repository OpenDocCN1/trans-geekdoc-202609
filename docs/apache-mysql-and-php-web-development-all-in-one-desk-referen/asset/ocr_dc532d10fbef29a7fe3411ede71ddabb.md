```
.mycanvas create line \\
310 10 375 100 425 50 550 200 300 200 \\
-smooth off -width 1 -fill black
.mycanvas create line \\
310 10 375 100 425 50 550 200 300 200 \\
-smooth on -width 5 -fill red -capstyle round \\
-splinesteps 3
```

The window for this code is shown in Figure 8-9. In this code and in the figure, I also had some fun with the -splinestep option. This option controls how smooth the line is. In my code, I used a value of 3. If you look closely at the right half of Figure 8-9, you can see that the line command used three smaller segments (shown in bold) in place of each original segment (shown as narrow). (The bottom line really does have three segments; two of the three are in the same direction, appearing as one long segment.) The higher the number you specify in the -splinesteps option, the more segments you'll get.

![](bbox=[0.25, 0.43, 0.77, 0.65])

Figure 8-9:
Lines can
also be
curved.

# Polygons

A polygon is just like a line sequence, except the polygon adds a final line connecting the endpoint and the start point, closing up the polygon. The canvas widget then fills the polygon with your color of choice. Here's an example:

```
canvas .mycanvas -width 600 -height 300
pack .mycanvas

.mycanvas create polygon 10 10 210 50 130 290 -fill blue
.mycanvas create polygon 300 50 510 290 550 60 350 280 \\
-fill red
```