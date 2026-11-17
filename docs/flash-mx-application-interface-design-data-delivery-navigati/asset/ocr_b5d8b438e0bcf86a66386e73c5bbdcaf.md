Now we have established our variables and color schemes, it’s time to place a few movie clips on our stage to hold the actual graphics. This code is still located on the variables layer:

```
this.createEmptyMovieClip("sectionHolder", 1);
```

sectionHolder is the clip that will hold all of the section buttons themselves. I often like to place attached graphics into holders, rather than adding them directly to the stage, because it gives more freedom for placing, rotating and scaling the entire group if need arises.

The next movie clip will serve as the background of our stage. Since we will be changing colors dynamically, we can’t rely on the stage color itself. Instead we draw a box around the stage, using the drawing API, and color it as needed:

```
this.createEmptyMovieClip("bg", 0);
bg.beginFill(currentColorScheme.background
    , 100);
drawBox(bg, 0, 0, stageWidth,
    stageHeight);
bg.endFill();
```

OK, the beginFill (where we send a color and alpha value) and endFill lines might be familiar to you if you have used the drawing API at all, but where does drawBox come from? Well, since we will be drawing plenty of boxes in this movie, it’s best that we place this in another function that we can easily call up over and over. What we are sending to this new function are the clip in which to draw, and the left, top, right and bottom boundaries for the box. Let’s take care of this function now so you can see how we accomplish this.

Go to the functions layer of code (which should be empty) and type the following:

```
drawBox = function(clip, l, t, r, b) {
    with(clip) {
        moveTo(l, b);
        lineTo(r, b);
        lineTo(r, t);
        lineTo(l, t);
        lineTo(l, b);
    }
}
```

As simple as this function might seem, it will help us out tremendously. Using the four boundaries sent, the function draws a box in the given clip. Notice how we have kept the fill methods (as well as clear and lineStyle) outside of the function so that we can handle these for differing clips. With that taken care of, jump back to the variables layer so we can finish up there.

Back on the variables layer, we need to add the lines that will format all of our text fields. Add these lines to follow the creation of the background graphic (bg):

```
headingTF = new TextFormat();
headingTF.align = "right";
headingTF.font = "scriptFont";
headingTF.size = 18;
headingTF.color = currentColorScheme.foreground;

infoTF = new TextFormat();
infoTF.align = "left";
infoTF.font = "scriptFont";
infoTF.size = 15;
infoTF.color = currentColorScheme.foreground;

buttonTF = new TextFormat();
buttonTF.align = "center";
buttonTF.font = "scriptFont";
buttonTF.size = 16;
buttonTF.color = currentColorScheme.foreground;
```

Here we are using the new TextFormat object to provide formatting for our text fields. Each formatting object has the same font, since we only exported one from our library, though each has a different size and alignment. Notice too how each establishes its color (which is the same for each) by looking in the foreground property of the currentColorScheme. Since we set the currentColorScheme to be blackboard, then that color will be white.

If you are using a font other than QuillScript as your exported font, this is the area where you might need to come back to adjust the font size. Simply alter each text format’s size property if my values are not working for your choice of font.

That takes care of all of our variables. Now it’s time to add the code that will actually draw our buttons on our stage.