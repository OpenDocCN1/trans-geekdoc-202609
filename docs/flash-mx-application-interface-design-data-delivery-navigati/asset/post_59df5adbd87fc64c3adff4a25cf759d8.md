
Once a user clicks on a laser with the mouse it becomes draggable. We remove any interval calls as well as its enterFrame handler (in case it is currently moving). Once the laser is released, we stop the dragging and call its setMoveWait method to determine when it moves next. This next line of code is what ties this Class definition with a symbol in our library. Place this after the releaseMe method:

```
Object.registerClass("laser", LaserClass);
for (i = 0; i < totalLasers; i++) {
this.attachMovie("laser", "l" + i, i);
}
```

If you right-click on the laser symbol in the library and select Linkage, you will notice that I have exported it as laser. By then registering this symbol with the Class definition LaserClass through the Object object's registerClass method, I have ensured that any instance of laser that I place on the stage will in fact be an instance of LaserClass. In the for loop that follows, I place all the lasers on the stage.

![](img/50202c17d5022233f3e3ec60560e35aa_22_0.png)

Go ahead and test your movie to see the lasers moving about the logo, each in its own random way, until the preloading is done and they scoot off the right hand side of the stage and disappear.

## Drawing the laser beams

Now it's time to complete the effect by drawing beams from the lasers onto the logo. This gets a little tougher, but creates a fantastic effect, so stick with me!

Our next method is called during our drawLogo function above and draws the actual laser beam on to the stage.

Place these lines after the init method:

```
LaserClass.prototype.drawLaser =
function(percent) {
this.recursiveCount = 0;
this.beamY = logo._y + this._y + percent;
this.beamX = this.getContactX();
}
```

(Really, you can place it anywhere within the LaserClass definition as long as it is after the LaserClass.prototype = new MovieClip() and before the Object.registerClass line. This goes for all subsequent methods of LaserClass as well.)

Remember that percent is the percentage of the kilobytes loaded multiplied by the height of the logo. We sent it to this function so that the lasers know at what y position to aim their beams. The first line initializes a variable called recursiveCount. We will use this as a safety check in a bit, and I will explain it more fully then. The next two lines find an x and y position for the end of the laser beam (the origin of the beam is always on the laser movie clip itself). beamY is found by taking the logo's _y position and subtracting the laser's _y position. This offset is necessary since we will be drawing the laser inside the laser movie clip. We then add in the current percentage of the logo's total height. Finding the x position of the laser is a bit more complicated, so I placed it inside another method called getContactX. We will address that method in a moment.

![](img/50202c17d5022233f3e3ec60560e35aa_22_1.png)

Continue with the drawLaser method by adding the following lines of code:

```
for (var i in logo) {
    if (typeof logo[i] == "movieclip") {
        if (logo[i].hitTest(this.contactPoint.x,
            this.contactPoint.y, 1)) {
            var logoColor = new Color(logo[i]);
            var laserColor = logoColor.getRGB();
            break;
        }
    }
}
```

To understand this code, you will need to understand how I have set up the logo. Enter symbol editing mode. You will find that the logo is separated into layers, and each layer contains an element of a different color. If you select any of the elements, you will find that each layer contains its own movie clip, and that the movie clip has been colored in the Properties panel. It is set up in this way so that we can use the Color object's built-in getRGB method to determine each clip's color when a laser is over it. For this reason we not only need to separate each color into its own movie clip, but we need to then tint that movie clip 100% of its base color (look down to the Properties panel again to see evidence of this). Currently, there is no way for Flash to determine a clip or pixel's color, so we must create this workaround to accomplish our task.

![](img/50202c17d5022233f3e3ec60560e35aa_23_0.png)

As to the code, the for in loop above runs through each property inside of logo. If a property (which can be an object) is a movie clip, then it tests to see if the point of contact for the laser (stored in this.contactPoint, which is set in the getContactX function that we will write next) hits that logo movie clip. If it does, then it creates a temporary Color object and uses it to find the color of that element using the getRGB method. It stores that color in the variable laserColor. Having found one color, we need no longer search and so we break out of the loop.

If you are wondering about the difference between the x and y values stored in this.contactPoint and the values stored in beamX and beamY, you will see when we set up the values for contactPoint that they are relative to the main timeline, whereas beamX and beamY are relative to the laser movie clip. We need the contactPoint values in order to call hitTest, but we will need the beamX and beamY values to draw the laser graphic correctly inside of the laser movie clip.

The last bit of this function is a piece of cake. Finish it off by adding these lines:

```
this.clear();
this.lineStyle(2, laserColor, 100);
this.lineTo(this.beamX, this.beamY);
}
```

Pretty easy. We clear the previously drawn beam graphic and reset the lineStyle (thickness, color and alpha for the laser), which is cleared every time the clear method is called. We then draw our line from the laser's origin (0,0) to whatever values we assigned to beamX and beamY.

The next, and final, method is a bit of a bear, and the most complicated of this project. Let's walk through it slowly.

![](img/50202c17d5022233f3e3ec60560e35aa_23_1.png)

Place it after the drawLaser method:

```
LaserClass.prototype.getContactX = function() {
    this.recursiveCount++;
    if (this.recursiveCount > 100) {
        return totalX/2
    }
    this.contactPointX +=
        this.laserPace*this.direction;
}
```

getContactX is called to determine the beam’s point of contact on the logo on the x axis. You will see in a moment that due to the odd shape of the logo, running a simple back and forth sweep isn’t possible, so we have to do a little searching for a place to shoot the beam. Because of this, getContactX is a recursive function, which means that it’s a function that can call itself. This is fine as long as you can ensure that the number of times the function is called isn’t infinite, which can sometimes happen in recursive loops. To take care of this, we set the laser’s recursiveCount property to 0 each time the laser is told to draw itself (in the drawLaser method). Each time we enter this method, we add one to recursiveCount. If it turns out that this method needs to call itself more than 100 times, we “give up” and simply set the x position to be dead center of the logo.

The final line of code in the above section increments our contactPointX property, which is in fact the beam’s x point of contact on the logo, by the rate of the laser multiplied by the direction (positive or negative).

Now we need to make some checks to make sure our beam is falling on to our logo. Type these lines after the previous code:

```
if (this.direction > 0) {
    if (this.contactPointX > totalX) {
        this.direction *= -1;
        this.contactPointX = totalX;
    }
} else {
    if (this.contactPointX < 0) {
        this.direction *= -1;
        this.contactPointX = 0;
    }
}
```

The first if statement simply checks to see if we are moving in a positive direction. If we are, we then check to see if we have moved off of the right side of the logo. If this occurs, we change direction. The else statement simply checks the left side of the logo.

And for the final bit of code for our getContactX method (and the final bit in this tutorial!):

```
var beamX = this.contactPointX - (this._x - logo._x);
this.contactPoint = {x:beamX, y:this.beamY};
this.localToGlobal (this.contactPoint);
while (!logo.hitTest (this.contactPoint.x,
    this.contactPoint.y, 1)) {
    beamX = this.getContactX();
}
return beamX;
}
```

Here we create a local variable named beamX and adjust it for the distance between our laser source and the logo. We need to do this since the value for contactPointX is simply a number between 0 and the width of the logo. If our laser’s _x position was equal to the logo’s _x position, then this value would be fine. Because the laser’s position is dynamic, however, we need to make this adjustment.

contactPoint is a new object in which we place the beamX and beamY variables. This object is necessary for the next line in which we call the localToGlobal method. localToGlobal is an extremely handy method, which converts coordinates from one coordinate space to another. In this instance, it is taking x and y coordinates values inside the laser and converting them to coordinates on the main stage. If we are to perform hitTests using coordinate points as we did in the above drawLaser function, and as we will in the next line inside this function, then we need to ensure the coordinates are all in the same coordinate space. Since a hitTest with the logo will need coordinate positions on the main timeline, we have to convert our laser contact point to suit.
