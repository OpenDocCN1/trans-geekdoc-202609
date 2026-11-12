
The following steps outline the basic way to use a canvas:

- 1. Create the canvas widget and give it a name like any other widget.
- 2. Position the canvas widget on your window.
- 3. Call your canvas widget's set of commands. The general format is the name of your canvas followed by the word create followed by a command such as rectangle or arc.

In the following sections, I show you how to do all this. For starters, however, I show how you can specify colors in your drawings.

## Colors

The Tk system supports a huge variety of colors, each with a unique name. Examples are azure2, blueviolet, DarkOrchid4, LemonChiffon, purple, wheat4, firebrick1, DarkSeaGreen1, and chocolate. I'm not making this up. If you want to see a list of all the colors, visit www.tcl.tk/man/tcl8.4/TkCmd/colors.htm. There you'll find hundreds of colors (and hundreds of unique names).

Here's an example that demonstrates several of these colors by drawing a colored bar of each. I won't bother with a screenshot, because this book is in black and white, but try out this example to see the color output. And feel free to try adding some more colors to the colorlist variable in this code:

```
canvas .mycanvas -width 300 -height 300
pack .mycanvas

set top 0
set colorlist {azure2 blueviolet DarkOrchid4 \
LemonChiffon purple wheat4 \
firebrick1 DarkSeaGreen1 chocolate}
foreach mycolor $colorlist {
set bottom [expr $stop + \
[expr 300 / [llength $colorlist]]]
.mycanvas create rectangle 0 $top 300 $bottom \
-fill $mycolor
set top $bottom
}
```

## Arcs

Creating arcs is easy in Tk. The key is in understanding that an arc is a portion of a circle, where you specify two angles: where on the circle to begin the arc, and a length of the arc in degrees. Additionally, you have three different arc styles to choose from: a filled-in pie slice, a single arc of a circle (just a curve, nothing filled in), and a filled-in chord, which is sort of a “pie crust” part. Here’s an example that demonstrates these styles:

```
canvas .mycanvas -width 600 -height 300
pack .mycanvas

.mycanvas create arc 10 10 290 290 -fill blue
.mycanvas create arc 10 10 290 290 -start 190 \
-extent 30 -fill green

.mycanvas create arc 310 10 590 290 -fill blue \
-style chord
.mycanvas create arc 310 10 590 290 -start 190 \
-extent 30 -fill green -style arc
```

This code creates the window shown in Figure 8-7.

![](img/3f967ab8a8fddc723173059f56621648_348_0.png)

Figure 8-7:
The arc command allows for three different styles.

To see how arcs are positioned, look carefully at the first two arc commands. Each occupies the same circle that fits inside the square 10, 10 through 290, 290. The difference, however, is in the angles. In the first arc example, I don’t specify any angles, so by default, I get an angle from 0 degrees to 90 degrees (which ranges from due East to due North on the circle). That’s in the upper-right quadrant. In the next arc command, I do specify an angle, from 190 degrees extending a distance of 30 degrees. That’s in the lower-left quadrant. (190 degrees is slightly more than 180; 180 would be due West.) Notice that the two arcs are aligned at their centers.

That can be confusing: Each of the two arc commands so far takes up a position 10,10 through 290,290, and yet the two commands don’t totally fill that rectangular area. Instead, they fill only the quadrant where they belong.

The default style is a pie shape, and you can specify the color of the pie using the -fill option. To show the other two styles, I draw two more arcs in the right side of the window. The first is a chord, which is like the pie crust of a pie shape: It's surrounded by the arc on the circle and a line connecting the two points (in this case, the two points are the default points: 0 degrees and 90 degrees). The second is an arc, which is just a curve along the perimeter of the imaginary circle.

## Lines and curves

Here's a cool thing: With the canvas widget, you can draw a sequence of lines and then, by setting a single option, you can generate a curve that fits the lines you drew. The line command is easy; you just specify a sequence of numbers representing points as I do in the following code:

```
canvas .mycanvas -width 300 -height 350
pack .mycanvas

.mycanvas create line \
10 10 75 100 125 50 250 200 40 200 \
-smooth off -width 1 -fill black -width 10 \
-joinstyle round

.mycanvas create line \
10 40 75 130 125 80 250 230 40 230 \
-smooth off -width 1 -fill black -width 10 \
-joinstyle miter -cap round

.mycanvas create line \
10 70 75 160 125 110 250 260 40 260 \
-smooth off -width 1 -fill black -width 10 \
-joinstyle bevel -arrow last
```

In the first line command, I have a bunch of line segments. The first starts at point 10,10 and goes to point 75,100. The next starts at that point — 75,100 — and goes to 125,50. The next starts there at 125,50 and goes to 250,200. And the final one starts there at 250,200 and goes to 40,200. Easy. The window for this code is shown in Figure 8-8.

With the line command, you also have several options. You can specify the width of the line; in the preceding code, all my lines are really fat, measuring in at 10 pixels. You can also specify a color (mine are all black, but you can use other colors like bisque3, whatever that is, or OliveDrab2).

You can also specify a cap style for the end of each line. Your choices are bevel, miter, and round. You can try out these different types and see what they look like.

![](img/3f967ab8a8fddc723173059f56621648_350_0.png)

You can also specify an arrow shape at the end of your line. I do this in the third line command, shown in Figure 8-8. In this case, I put an arrow at the end of the line sequence. You can also put one at the beginning by using -arrow first. Or if you want one on both ends, use -arrow both.

And you can specify a joint style connecting each line. This is subtle, but if you look at each of the three line sequences in the current example (and in Figure 8-8), you’ll see I used a slightly different join style for each. This style is the -joinstyle option, and the choices are bevel, miter, and round.

Notice also that I added the option -smooth off for each line. This is the default, so I was just being clear (although redundant) by using this option. In the next example, however, I turn on this option. Almost like magic, I get a curve that carefully fits the endpoints of the line sequence. Just to show how this curve fits, I also draw the same line sequence with the curve option off so you can compare the two. Here’s the example code:

```
canvas .mycanvas -width 600 -height 300
pack .mycanvas

.mycanvas create line \
 10 10 75 100 125 50 250 200 0 200 \
 -smooth off -width 1 -fill black

.mycanvas create line \
 10 10 75 100 125 50 250 200 0 200 \
 -smooth on -width 5 -fill red -capstyle round

.mycanvas create line \
310 10 375 100 425 50 550 200 300 200 \
-smooth off -width 1 -fill black
.mycanvas create line \
310 10 375 100 425 50 550 200 300 200 \
-smooth on -width 5 -fill red -capstyle round \
-splinesteps 3
```

The window for this code is shown in Figure 8-9. In this code and in the figure, I also had some fun with the -splinestep option. This option controls how smooth the line is. In my code, I used a value of 3. If you look closely at the right half of Figure 8-9, you can see that the line command used three smaller segments (shown in bold) in place of each original segment (shown as narrow). (The bottom line really does have three segments; two of the three are in the same direction, appearing as one long segment.) The higher the number you specify in the -splinesteps option, the more segments you'll get.

![](img/3f967ab8a8fddc723173059f56621648_351_0.png)

Figure 8-9:
Lines can
also be
curved.

## Polygons

A polygon is just like a line sequence, except the polygon adds a final line connecting the endpoint and the start point, closing up the polygon. The canvas widget then fills the polygon with your color of choice. Here's an example:

```
canvas .mycanvas -width 600 -height 300
pack .mycanvas

.mycanvas create polygon 10 10 210 50 130 290 -fill blue
.mycanvas create polygon 300 50 510 290 550 60 350 280 \
-fill red
```
