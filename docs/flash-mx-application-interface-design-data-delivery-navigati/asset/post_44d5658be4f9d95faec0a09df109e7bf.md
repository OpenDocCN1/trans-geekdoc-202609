
## The tools

### The pencil tool

![](img/50202c17d5022233f3e3ec60560e35aa_197_0.png)

The pencil tool is the standard scribble based-tool – no frills, no nothing. Put the pencil onto the paper, scribble, and if you can muster up the will power, take the pencil off the paper.

I like to think of this pencil tool as the equivalent of what most people do to post-it notes on the telephone – the creative action of drawing a continuous line, which creates random shapes and ever increasing complexity.

It will not come as a surprise that the pencil tool – aka the FreeDraw tool – is easily the most basic to code.

The general principle from a Flash and usability perspective is:

```
Press mouse button to begin drawing,
Draw a continuous line,
UNTIL...
The mouse button is released,
Stop drawing.
```

Not exactly rocket science, for sure.

Let's break it down into tasty chunks. Starting at the top:

```
funcFreeDraw = function () {
_root.freeDraw = function() {
if (_root.xmouse != oldX &&
_root.ymouse != oldY) {
```

After the function declarations is a conditional to check whether the last xmouse (oldX) and ymouse (oldY) readings are any different to the current ones. This check is performed just in case the user continues to hold down the mouse button without moving the cursor, and it saves Flash drawing on the same spot unnecessarily.

If the last and current readings are different then the code begins:

```
if (_root.penDown == 0) {
drawPad.moveTo(_root._xmouse,
_root._ymouse);
_root.penDown = 1;
} else {
```

This code checks firstly to see if the pencil is not already held down. This is performed because we need to know if the user is already drawing, or has their pencil off the paper. If the pencil is off the paper, then it will start drawing from where the user clicks the mouse. From then on, you can draw freeform.

The penDown state tells Flash if the pencil is currently touching the paper. Before you click to draw, it is set to 0, and after you've clicked it is set to 1. From now on, whilst the pencil is down, the following code will be run:

```
if (_root.xmouse>tabletleft &&
_root.xmouse<tableright) {
oldX = _root.xmouse;
}
if (_root.ymouse>tablettop &&
_root.ymouse<tabletbottom) {
oldY = _root.ymouse;
}
```

The if statements on lines 1 and 4 here check to see if the pencil is drawing within the given area. (Remember that the global variables for the drawing boundary were defined at the start of the code.)

If the pencil is within these constraints, then oldX and oldY are updated to reflect the current mouse position on both axes.

If the readings suggest that the positions are outside either axis, then oldX and/or oldY aren't changed.

We then need to draw the line itself:

```
drawPad.lineStyle(
_root.mainButBrushSize.bSize, _root.col,
_root.mainButBrushAlpha.bAlpha);
drawPad.lineTo(oldX, oldY);
}
};
```

The first line here simply sets the lineStyle for drawing, taking attributes written from the brushes input boxes.

The second line draws a line from the current mouse position to the end of the last line (oldX and oldY).

The last section of code sets the functions to run on mouse button activity:

```
drawPad.onPress = function() {
_root.penDown = 0;
freeDrawInterval = setInterval
(function() { freeDraw(); }), 10);
};
```

The onPress code here simply defines the code that is carried out when the mouse button is pressed. The first thing that happens is that the penDown flag is set to 1, and this, if you remember from the start of the function above, tells Flash to perform a moveTo to the current mouse position.

After this, a setInterval action is set, telling Flash to run the freeDraw function every 10 milliseconds. This is used as opposed to the onEnterFrame code because it runs a little more regularly. Sometimes onEnterFrame is affected by the frame rate and we want this to run regularly.

Here's the last of the code for the pencil tool:

```
drawPad.onRelease =
drawPad.onReleaseOutside=function () {
clearInterval(freeDrawInterval);
};
};
```

This batch of code is set to run in the event of an onRelease or onReleaseOutside.

A word of warning here. When you write code like this using double declarations...

```
me.onRelease = me.onReleaseOutside = function () {
doThis();
nowThis();
}
```

... make sure you don't reformat your code, as Flash tends to stick all the function code in one line and you end up with unreadable code like this:

```
me.onRelease = me.onReleaseOutside = function () {doThis();nowThis();}
```

It's super-annoying, believe me...

Anyway, back to the code. When the mouse is released, the setInterval method is cleared, and the drawing is stopped.

That concludes the pencil tool, as I said, it's not tricky to understand. It doesn't use the preview instance, like the line or curve tools, and just draws straight onto the pad. If anything the pencil tool is incredibly crude and unsophisticated, but it is one of the tools that I'm more likely to use.

It also rocks when you play with the brush thickness and alpha.

You might find yourself using a virtual pad when you run out of paper, or if you suddenly become worried about the decline of the rainforests. See post_it.fla for the pencil tool in a post-it style. Paul Davis eat your heart out.

![](img/50202c17d5022233f3e3ec60560e35aa_199_0.png)

### Line tool

![](img/50202c17d5022233f3e3ec60560e35aa_199_1.png)

There are two standard line drawing methods in drawing applications. The first is to click on a point to start the line, and then drag and release to fix the point where you want the line to end. The second method (sometimes called rubber-banding) is to click once to fix the first point, then click again to fix the second point, again to fix the third, and so on drawing out a continuous line. We chose to use the first method, but it would be a simple task to change the code to the second method if you preferred.

![](img/50202c17d5022233f3e3ec60560e35aa_199_2.png)

The line drawing tool is similar in execution to the freehand drawing tool, but with an important difference – instead of drawing directly onto the drawPad layer, we instead draw onto a preview layer first, and then fix the line onto the drawPad when the mouse is released.

The main line draw function is split into two parts, what happens when you press and drag the mouse on the drawPad, and what happens when you release it. Let's look at the onPress actions first.

The initial thing we do is record the x and y positions of the mouse, and store them as startX and startY:

```
funcLineDraw = function () {
    drawPad.onPress = function() {
        _root.startX = _root._xmouse;
        _root.startY = _root._ymouse;
    };
```

We then set up an onEnterFrame action on the root so that we can update the position of the preview line every frame. We place the event handlers on the root to ensure that they overwrite each other and there's no chance of two being run at the same time. We defined a global variable (tempLayer) for the position of the temporary layer earlier in the code, so we'll use that throughout this function. The first thing that we need to do every frame is to clear whatever was previously in the temporary layer so that there's only ever one line on it:

```
_root.onEnterFrame = function() {
    tempLayer.clear();
};
```

If you remove this line you can make some lovely patterns, but they're not really the effect we're after here:

After clearing the layer, we define the lineStyle according to the current settings, and move the drawing position to the original coordinates set when we clicked the mouse:

```
tempLayer.lineStyle(_root.mainButBrushSize.bSize,
    _root.col, _root.mainButBrushAlpha.bAlpha);
tempLayer.moveTo(_root.startX, _root.startY);
```

We now run through a bit of boundary checking code to make sure that we don't draw outside the drawPad. This code is the same as it was for the pencil drawing tool – it checks to see if we're over the boundaries, and if we're not then it sets a variable (_root.xM & _root.yM) to hold the new mouse position, but if we are then it keeps the old position. We then draw a line from the original coordinates to the new ones:

```
if (_root._xmouse>tabletleft && _root._xmouse<tabletright) {
    _root.xM = _root._xmouse;
}
if (_root._ymouse>tablettop && _root._ymouse<tabletbottom) {
    _root.yM = _root._ymouse;
}
tempLayer.lineTo(_root.xM, _root.yM);
});
```

![](img/50202c17d5022233f3e3ec60560e35aa_200_0.png)

![](img/50202c17d5022233f3e3ec60560e35aa_200_1.png)

![](img/50202c17d5022233f3e3ec60560e35aa_200_2.png)

![](img/50202c17d5022233f3e3ec60560e35aa_200_3.png)
