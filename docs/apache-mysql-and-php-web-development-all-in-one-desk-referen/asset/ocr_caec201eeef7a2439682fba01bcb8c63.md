```
wm title . "Pack demo 1"
pack propagate . off

button .bt1 -text "One"
button .bt2 -text "Two"
button .bt3 -text "Three"

pack .bt1 .bt2 .bt3 -side left

button .bt4 -text "Four"
pack .bt4 -side bottom

button .bt5 -text "Five"
pack .bt5 -side bottom

button .bt6 -text "Six"
pack .bt6 -side bottom
```

Figure 8-1 shows what this code looks like when it runs. The special line pack propagate . off turns off the squeezing effect for the window named dot (.), which is the main window. Notice in the figure that the three buttons labeled One, Two, and Three are all gathered up against the left side. And also notice that they move inward. First, the button called One was placed against the left side. Then the button called Two was placed as far left as it could, which was up against the existing button called One, and so on. Notice also that I called pack with all three of these buttons listed and an option -side set to left.

![](bbox=[0.16, 0.58, 0.38, 0.77])

Figure 8-1: With pack, the controls gather around the edges.

Next, the button called Four was pushed against the bottom side. Then, when I packed button Five, that button appeared as far towards the bottom as it could, which is just on top of button Four. Similarly, button Six appeared