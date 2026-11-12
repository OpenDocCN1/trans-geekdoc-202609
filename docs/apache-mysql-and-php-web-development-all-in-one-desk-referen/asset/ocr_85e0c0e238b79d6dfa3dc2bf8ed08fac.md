The following steps outline the basic way to use a canvas:

+   1. Create the canvas widget and give it a name like any other widget.
+   2. Position the canvas widget on your window.
+   3. Call your canvas widget's set of commands. The general format is the name of your canvas followed by the word create followed by a command such as rectangle or arc.

In the following sections, I show you how to do all this. For starters, however, I show how you can specify colors in your drawings.

# Colors

The Tk system supports a huge variety of colors, each with a unique name. Examples are azure2, blueviolet, DarkOrchid4, LemonChiffon, purple, wheat4, firebrick1, DarkSeaGreen1, and chocolate. I'm not making this up. If you want to see a list of all the colors, visit www.tcl.tk/man/tcl8.4/TkCmd/colors.htm. There you'll find hundreds of colors (and hundreds of unique names).

Here's an example that demonstrates several of these colors by drawing a colored bar of each. I won't bother with a screenshot, because this book is in black and white, but try out this example to see the color output. And feel free to try adding some more colors to the colorlist variable in this code:

```
canvas .mycanvas -width 300 -height 300
pack .mycanvas

set top 0
set colorlist {azure2 blueviolet DarkOrchid4 \\
LemonChiffon purple wheat4 \\
firebrick1 DarkSeaGreen1 chocolate}
foreach mycolor $colorlist {
set bottom [expr $stop + \\
[expr 300 / [llength $colorlist]]]
.mycanvas create rectangle 0 $top 300 $bottom \\
-fill $mycolor
set top $bottom
}
```

# Arcs

Creating arcs is easy in Tk. The key is in understanding that an arc is a portion of a circle, where you specify two angles: where on the circle to begin the arc, and a length of the arc in degrees. Additionally, you have three different arc styles to choose from: a filled-in pie slice, a single arc of a circle