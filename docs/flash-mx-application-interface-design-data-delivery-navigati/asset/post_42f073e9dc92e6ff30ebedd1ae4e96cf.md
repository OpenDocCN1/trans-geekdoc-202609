
If we pick the play/pause button to look more closely at we can see that the line videoside.play has been added after video.play(); and videoside.stop(); after video.stop();

```
controls.playBut.onRelease = function() {
  if (playing == false) {
    video.play();
    videoside.play();
    playing = true;
  } else {
    video.stop();
    videoside.stop();
    playing = false;
  }
};
```

This method has been repeated throughout the code. We can now test the movie and see that using the toggle button flips us between the front and side view videos.

![](img/50202c17d5022233f3e3ec60560e35aa_242_0.png)

![](img/50202c17d5022233f3e3ec60560e35aa_242_1.png)

Next we need to make use of the arrays we created earlier. The first line of the ActionScript for this movie should import our arrays. Importing these arrays will ensure that they are in place for the rest of our code to refer to. We have called it kata.as, so add this code to line 1 of our code. Remember to ensure that the .as file is in the same directory as the Flash movie.

```
#include "kata.as"
```

The captions we recorded are going to be written to a dynamic text box at the lower edge of the mat. Add a new layer above the grid mask layer and call it text. Create a large dynamic text box with a variable name of captionText across the bottom of the mat. Center align the text in it.

![](img/50202c17d5022233f3e3ec60560e35aa_243_0.png)

We can now add the code that will deliver the information recorded in our first movie and stored in kata.as. This will monitor the video movie clip and ensure that the feet graphics and captions are played back at the correct time. This code is added above the button code, and is similar to the recording code, in that it uses all the same variables for position and rotation, this time though it is setting these variables rather than recording them. Let’s take a look.

This function sets the position and rotation of the feet at any recorded point and places the caption dynamically:

```
setFeetGraphic = function (changeNum) {
	rightFoot._x = rightPosX[changeNum];
	rightFoot._y = rightPosY[changeNum];
	leftFoot._x = leftPosX[changeNum];
	leftFoot._y = leftPosY[changeNum];
	rightFoot._rotation = rightRot[changeNum];
	leftFoot._rotation = leftRot[changeNum];
	caption = caption[changeNum];
}
```

It uses the same variables as the record movie.

We then have this code to call positionLastFeet, a function created in the next piece of code:

```
positionLastFeet(changeNum);
```

We want to show the feet position immediately before the current one, which is known as change-1. This code creates these feet, with a low alpha so we know which are previous and which are current stances:

```
positionLastFeet = function (change) {
	if (change > 0) {
		lastrightFoot._visible = true;
		lastleftFoot._visible = true;
		lastrightFoot._alpha = 20;
		lastleftFoot._alpha = 20;
		lastrightFoot._x = rightPosX[change - 1];
		lastrightFoot._y = rightPosY[change - 1];
		lastleftFoot._x = leftPosX[change - 1];
		lastleftFoot._y = leftPosY[change - 1];
		lastrightFoot._rotation = rightRot[change - 1];
		lastleftFoot._rotation = leftRot[change - 1];
	} else {
		lastrightFoot._visible = false;
		lastleftFoot._visible = false;
	}
};
```

This will enable us to see where our feet are going to move from and to, in relation to each other, rather than just giving us a disembodied pair of feet with no reference to position. If there is no previous incarnation of the feet, it makes the instance lastrightFoot and lastleftFoot invisible. There is no need to know the last caption so this instruction is omitted from this function.

![](img/50202c17d5022233f3e3ec60560e35aa_244_0.png)

To save a little on processor usage this function stops the onEnterFrame script from running. It also lets Flash know that video has stopped playing:

```
stopPlayChecks = function () {
	_root.onEnterFrame = undefined;
	playing = false;
};
```

The following functions are those that our backBut and forwardBut buttons will call. previousInstruction checks to see that the current instruction is not the first, calls the stopPlayChecks function, then removes 1 from currentInstruction. It then positions the feet according to this instruction and moves both video clips to the correct frame.

```
previousInstruction = function () {
	if (currentInstruction > 0) {
		stopPlayChecks();
		currentInstruction--;
		setFeetGraphic(currentInstruction);
		video.gotoAndStop(changeFrame[currentInstruction]);
		videoside.gotoAndStop(changeFrame[currentInstruction]);
	}
};
```

Then come the functions singleCheck and playChecks, which work hand in hand monitoring the current frame number of the video movie clip and if necessary change the feet position using the setFeetGraphic function and then add one to currentInstruction.

```
singleCheck = function (added) {
	toCheck = currentInstruction + added;
	if (video._currentframe == changeFrame[_root.toCheck]) {
		setFeetGraphic(toCheck);
		_root.currentInstruction += added;
	}
};
```

```
playChecks = function () {
	_root.onEnterFrame = function() {
		singleCheck(1);
	};
};
```

We want playCheck to be functioning when the video is playing so we need to attach an extra line of code to PlayBut.

```
controls.playBut.onRelease = function() {
	if (playing == false) {
		video.play();
		videoside.play();
		playChecks();
		playing = true;
	} else {
		video.stop();
		videoside.stop();
		playing = false;
		stopPlayChecks();
	}
};
```

The second function, nextInstruction, will act as the previousInstruction function yet in reverse. We have to use a -1 with the currentInstruction if action, this is due to arrays starting at zero rather than one. The other difference is that the currentInstruction is added to rather than subtracted from.

```
nextInstruction = function () {
	if (currentInstruction < changeFrame.length - 1) {
		stopPlayChecks();
		currentInstruction++;
		setFeetGraphic(currentInstruction);
		video.gotoAndStop(changeFrame[currentInstruction]);
		videoside.gotoAndStop(changeFrame[currentInstruction]);
	}
};
```

Then we need the code that attaches our previously defined functions to the buttons that we added to the controller earlier.

```
controls.forwardBut.onRelease = function() {
	nextInstruction();
};
controls.backBut.onRelease = function() {
	previousInstruction();
};
```

We need to add some final code to initialize the movie.

We also need to initialize the movie to set one of the videos to visible and one to invisible, so this code needs to be the foot of the ActionScript.

First we set the initial video to be the front view:

```
fvvis = true;
video._visible = true;
videoside._visible = false;
```

currentInstruction is set at -1, to act as our counter:

```
currentInstruction = -1;
```

The movie starts to check each frame for instructions with the playChecks function:

```
playChecks();
```

We tell Flash that the video is playing:

```
playing = true;
```

Finally, four lines of code make sure that the previous stance is set to a lower depth than the current ones:

```
rightFoot.swapDepths(3);
leftFoot.swapDepths(4);
duplicateMovieClip("rightFoot", "lastrightFoot", 1);
duplicateMovieClip("leftFoot", "lastleftFoot", 2);
```

This gives some added prominence to the current feet. We don't want to trip ourselves up whilst trying to follow the steps.

We then need to add the singlecheck function to our single frame forward and back button code.

```
controls.backFrameBut.onRelease = function() {
	video.prevFrame();
	videoside.prevFrame();
	playing = false;
	singleCheck(-1);
};
controls.forwardFrameBut.onRelease = function() {
	video.nextFrame();
	videoside.nextFrame();
	playing = false;
	singleCheck(1);
};
```

The movie is now ready to be published and we are ready for our next lesson – learning our first kata, but that's another book altogether.

![](img/50202c17d5022233f3e3ec60560e35aa_246_0.png)

![](img/50202c17d5022233f3e3ec60560e35aa_246_1.png)

![](img/50202c17d5022233f3e3ec60560e35aa_246_2.png)

![](img/50202c17d5022233f3e3ec60560e35aa_246_3.png)

![](img/50202c17d5022233f3e3ec60560e35aa_246_4.png)

![](img/50202c17d5022233f3e3ec60560e35aa_246_5.png)

![](img/50202c17d5022233f3e3ec60560e35aa_246_6.png)

![](img/50202c17d5022233f3e3ec60560e35aa_246_7.png)
