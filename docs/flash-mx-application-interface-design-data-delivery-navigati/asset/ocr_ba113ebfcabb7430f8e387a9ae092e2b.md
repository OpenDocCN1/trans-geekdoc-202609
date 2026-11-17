After creating a new clip named drawing, we give it a variable to hold the current left side of the drawing (right now, simply half of the sectionButton's width from sectionButton center). This will change as we extend the left side of the button to the left as the section opens. The next line is another function I've added to encapsulate the code that we will use throughout. drawBorders will add randomized borders to a movie clip. Let's jump back to our functions code layer and add this new function now.

In the functions layer, immediately following our drawBox function, write the following:

```
```
drawBorders = function(clip) {
  clip.clear();
  clip.lineStyle(1,
  > currentColorScheme.foreground, 100);
  drawRandomBox(clip, -clip.leftSide, -
  > buttonHeight, halfButtonWidth, 0);
}
```
```

In this function, we accept a movie clip as a parameter and clear it of any previous drawings, reset the lineStyle based on the current color scheme's foreground color, and call a new function, drawRandomBox, sending it the clip and its four boundaries. This function is similar to our earlier drawBox function, but instead will draw a box with randomized borders. Let's write the necessary code now.

Below the drawBox function, add the following new function:

```
```
drawRandomBox = function(clip, l, t, r, b) {
  with (clip) {
    for (var i = 0; i < 3; i++) {
      moveTo(getRandom(10) + l,
      > getRandom(10) + b);
      lineTo(getRandom(10) + r,
      > getRandom(10) + b);
      lineTo(getRandom(10) + r,
      > getRandom(10) + t);
      lineTo(getRandom(10) + t,
      > getRandom(10) + t);
      lineTo(getRandom(10) + l,
      > getRandom(10) + b);
    }
  }
}
```
```

In this function, we run through a for loop three times and draw from and to randomized positions about the box's boundaries. What's getRandom? Why, another function we're just about to write.

Add this above the drawBox function, still on the functions layer:

```
```
getRandom = function(range) {
  return Math.random()*range - range/2
}
```
```

Pretty simple. We call this function and send a range in which to find a randomized number. The function uses Math.random to find a number between 0 and 1, multiplies this by our range so we have a number between 0 and our range maximum, then we subtract half of our range so the final number returned falls within the specified range but on either side of 0 (so a range of 10 will return a number between -5 and 5). Now we have our drawBorders function call complete and we can return to the set up stage layer to finish our script there.

After returning to the set up stage layer, add these lines to finish up the for loop:

```
```
btn = clip.createEmptyMovieClip("btn", 1);
btn.beginFill(0, 0);
drawBox(btn, -halfButtonWidth,
> -buttonHeight, halfButtonWidth, 0);
btn.endFill();
btn.onRollOver = sectionOver;
btn.onRollOut = btn.onReleaseOutside =
> btn.onDragOut = sectionOut;
btn.onRelease = function() {
> selectMe.apply(this._parent) };
}
delete clip;
delete btn;
delete drawing;
delete labelHolder;
delete label;
delete i;
```
```