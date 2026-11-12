```
-from 0 -to 300 \
-command "drawV" -tickinterval 50
grid .myVscale -row 0 -column 1
canvas .mycanvas -width 300 -height 300
grid .mycanvas -row 0 -column 0 -pady 5

.myHscale set 5
.myVscale set 5
```

The key to this program is in the two scale declarations. You can choose whether the slider control is a horizontal or vertical control; you can choose the size of the slider control (I chose 300 pixels); and you can choose the range. I'm using a range of 0 to 300, which matches the size of the scale.

You can also specify a -command option. However, this -command option is a bit different from the -command option in a button! For this command option, you specify a procedure that the slider will call when the user moves the slider. Further, the slider will pass a parameter to the procedure that's an integer representing the position of the slider. Thus, you'll notice that I only put the name of the procedure (drawH and drawV), but my procedures each take a parameter.

And what does this program do? If you move the sliders up and down, a little line moves. You can use this to draw like an Etch A Sketch drawing toy. Pretty cool, wouldn't you say? Check it out in Figure 7-5.

![](bbox=[0.15, 0.56, 0.48, 0.83])

Figure 7-5: The slider controls let the user select a number on a range.