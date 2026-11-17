```
video.onEnterFrame = function() {
video.gotoAndStop
(video._currentframe-10);
};
unsetFocal();
};
controls.rewindBut.onRelease = function() {
video.onEnterFrame = null;
video.play();
playing = true;
unsetFocal();
};
//fastforward
controls.ffwdBut.onPress = function() {
video.onEnterFrame = function() {
video.gotoAndStop
(video._currentframe+10);
};
unsetFocal();
};
controls.ffwdBut.onRelease = function() {
video.onEnterFrame = null;
video.play();
playing = true;
unsetFocal();
};
```

All the buttons are now in place to be able to set up our ActionScript to get the movie doing what it was designed to do; record information. The code will follow our button code attached to frame 1 of our actions layer. There is quite a bit of it but that is mainly because of the different variables that need recording. The first bit of the code lays this out. The co-ordinates, rotations and frame numbers where these occur will be written into an array that will be used in the playback movie.

First we define the function that gathers all the information that we require in our array:

```
recordCurrent = function () {
```

We then record the frame position where the instruction occurs:

```
changeFrame[controls.i] = video._currentframe;
```

Then comes some code to record the position of the right foot:

```
rightPosX[controls.i] =
Math.round(rightFoot._x);
rightPosY[controls.i] =
Math.round(rightFoot._y);
```

and then the left foot:

```
leftPosX[controls.i] =
Math.round(leftFoot._x);
leftPosY[controls.i] =
Math.round(leftFoot._y);
```

We then record the rotation of each foot:

```
rightRot[controls.i] =
Math.round(rightFoot._rotation);
leftRot[controls.i] =
Math.round(leftFoot._rotation);
```

and the caption from our input text box:

```
caption[controls.i] = controls.caption.text;
```

The next section of code adds to the array number and resets the button to the default move option:

```
controls.i++;
resetButtons.call(controls.moveBut);
moveFoot.call(leftFoot);
moveFoot.call(rightFoot);
};
```

![](bbox=[0.03, 0.92, 0.94, 0.99])