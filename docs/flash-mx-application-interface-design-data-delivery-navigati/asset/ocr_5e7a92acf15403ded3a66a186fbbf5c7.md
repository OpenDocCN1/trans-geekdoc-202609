Once a foot is pressed it can be dragged around the mat ~ the code after the startDrag action constrains the feet to the mat. The alpha of each foot is increased while it is pressed. Once released the foot returns to its faded state.

The feet need the ability to rotate too – that is what this code is for:

```
controls.rotateBut.onRelease = function() {
		resetButtons.call(this);
		rotateFoot.call(leftFoot);
		rotateFoot.call(rightFoot);
	};
```

The code is similar to that which gave the ability to move the feet, but this time gives the ability to rotate:

```
rotateFoot = function () {
	this.onPress = function() {
		this._alpha = 100;
		myX = this._x;
		this.onEnterFrame = function() {
			this._rotation +=
				Math.round(_xmouse-myX);
		};
	};
	this.onReleaseOutside =
		this.onRelease=function () {
			this._alpha = 50;this.onEnterFrame =
				undefined);
	};
};
```

Again the alpha is increased to 100 once a foot is pressed. The rotation function works through getting the position of the foot on the x axis, then rotating it depending on the mouse position from the foot. This can result in minus rotation if the mouse is moved to the left, and plus rotation if the mouse is to the right. As we will only see the static result of any rotation it does not matter if the foot rotates as a plus or minus.

![](bbox=[0.55, 0.1, 0.88, 0.38])

We then have the ActionScript that initializes the rest of the code through creating the empty arrays and setting the move and rotate controls to their default states:

```
video.stop();
playing = false;
unsetFocal();
changeFrame = new Array();
rightPosX = new Array();
leftPosX = new Array();
rightPosY = new Array();
leftPosY = new Array();
rightRot = new Array();
leftRot = new Array();
caption = new Array();
controls.i = 0;
```

```
leftFoot._alpha = rightFoot._alpha=50;
resetButtons.call(controls.moveBut);
moveFoot.call(leftFoot);
moveFoot.call(rightFoot);
gridvis = false;
grid._visible = false;
infovis = false;
info._visible = false;
```