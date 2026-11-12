```
wm title . "Pack demo 2"
button .bt1 -text "One"
button .bt2 -text "Two"
button .bt3 -text "Three"

pack .bt1 .bt2 .bt3
```

Figure 8-3 shows what this window looks like.

![](bbox=[0.05, 0.27, 0.29, 0.36])

# Creating a horizontal toolbar

If you know the way pack works, you can make some sophisticated layouts by adding a frame and then putting controls inside the frame. For example, a common look is to have a row of buttons across the top of a window, and a main widget taking up the rest of the window.

To do this kind of look, create a frame and put the frame at the top. Then add buttons to the frame, packing the buttons inside the frame from the frame's left. Finally, add the main control at the bottom. In the following example, I have commented out some lines — I will discuss these shortly. Also, the control I add at the bottom is a canvas control, which you can draw images on.

```
wm title . "Pack demo 3"
pack propagate . off

frame .buttonbar
pack .buttonbar -side top

button .buttonbar.bt1 -text "One"
button .buttonbar.bt2 -text "Two"
button .buttonbar.bt3 -text "Three"

pack .buttonbar.bt1 .buttonbar.bt2 .buttonbar.bt3 \
   -side left -padx 5 -pady 5

#try each of these two instead of the above
#pack .buttonbar.bt1 .buttonbar.bt2 .buttonbar.bt3 \
```