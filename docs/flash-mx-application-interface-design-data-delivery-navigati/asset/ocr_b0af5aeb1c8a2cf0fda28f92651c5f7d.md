Once a user clicks on a laser with the mouse it becomes draggable. We remove any interval calls as well as its enterFrame handler (in case it is currently moving). Once the laser is released, we stop the dragging and call its setMoveWait method to determine when it moves next. This next line of code is what ties this Class definition with a symbol in our library. Place this after the releaseMe method:

```
Object.registerClass("laser", LaserClass);
for (i = 0; i < totalLasers; i++) {
this.attachMovie("laser", "l" + i, i);
}
```

If you right-click on the laser symbol in the library and select Linkage, you will notice that I have exported it as laser. By then registering this symbol with the Class definition LaserClass through the Object object's registerClass method, I have ensured that any instance of laser that I place on the stage will in fact be an instance of LaserClass. In the for loop that follows, I place all the lasers on the stage.

![](bbox=[0.04, 0.55, 0.46, 0.7])

Go ahead and test your movie to see the lasers moving about the logo, each in its own random way, until the preloading is done and they scoot off the right hand side of the stage and disappear.

# # Drawing the laser beams

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

![](bbox=[0.04, 0.84, 0.9, 0.99])