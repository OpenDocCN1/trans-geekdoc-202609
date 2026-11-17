When we first execute the function makeThePlant, the next line of code in that function executes the function makePot. And the function does exactly that – it makes the pot that our plant sits in. We start by creating an empty movie clip, give it an instance name of pot and put it on level 10, so that it sits well in front of the seven leaves we made, which sit on levels 1-7. We then begin to fill the pot based on the color potFill we created with the convertColors function on the Date Actions layer. After this we draw a combination of curved and straight lines to form our pot, and end the fill at the end of the function.

Then we use the drawing API to draw the flower (note that the colors are hard-coded in this function – you can just as easily go back to the Date Actions layer and create some variables to color the flowers just as we did for the leaves and the pot). We then scale the flower down to 1 percent, so that we can make it grow when the movie clip loads, and randomly rotate, the flower movie clip just to give the finished plant a bit of randomness.

The very last function in our code is used to draw the flowers that go on the end of each leaf once the variable plantSize reaches a value greater than 25.

After this we create an onLoad method for the flower movie clip that we just made:

Even though this function is quite long, if you break it down into its subcomponents, there's not much in it that we haven't already talked about. We start by creating an empty movie clip to draw the flower in, and set the x and y position of the flower to be the same as the end point for the leaf that called this function:

```
function makeFlower
(name, levelNum, xPos, yPos) {
this.createEmptyMovieClip(name,
20+levelNum);
this[name].xscale = this[name].yscale = 1;
this[name]._x = xPos;
this[name] ._Y = yPos;
this[name].rotation =
Math.round(Math.random()*360);
with(this[name]) {
beginFill(0xFFFFFF00, 100);
lineStyle(1, 0xFFCC00, 100);
moveTo(-2, -9);
curveTo(-20, -17, -10, 1);
curveTo(-19, 24, 0, 9);
curveto(22, 18, 8, -2);
curveTo(18, -26, -2, -9);
endfill;
}
```

```
this[name].onLoad = function() {
this.startX = this._x;
this.num = 0;
this.clicked = false;
}
```

This is effectively telling the movie clip that when it loads, it makes a variable named startX to remember where the movie clip's x position is when the flower first loads, and another variable named clicked that is set to false to denote that the flower hasn't been clicked on yet (we're going to make the flower do something when you click on it).

In Flash MX you can assign an onRelease action or an onRollver action to a movie clip, just as you would with a button, so this is what we do next:

```
this[name].onRelease = function() {
this.clicked = true;
}
```

In a nutshell, this tells the movie clip to do something when the movie clip is clicked on with the mouse – in this case change the variable named clicked from false (which we set when the movie clip first loaded using the onLoad method) to true.

![](bbox=[0.605, 0.925, 0.965, 0.995])