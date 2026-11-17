

如果我们仔细查看播放/暂停按钮，可以看到 videoside.play 已添加至 video.play(); 之后，videoside.stop(); 则添加至 video.stop(); 之后：

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

此方法在代码中反复使用。现在我们可以测试电影，并看到使用切换按钮在正面视图和侧面视图视频之间切换。

![](img/50202c17d5022233f3e3ec60560e35aa_242_0.png)

![](img/50202c17d5022233f3e3ec60560e35aa_242_1.png)

接下来，我们需要使用先前创建的数组。此电影 ActionScript 的第一行应导入我们的数组。导入这些数组可确保它们可供其余代码引用。我们将其命名为 kata.as，因此请将此代码添加到代码的第 1 行。请确保 .as 文件与 Flash 电影位于同一目录中。

```
#include "kata.as"
```

我们录制的字幕将写入垫子底边的动态文本框中。在网格遮罩图层上方添加新图层并将其命名为 text。在垫子底部创建一个大的动态文本框，变量名为 captionText，并使其中的文本居中对齐。

![](img/50202c17d5022233f3e3ec60560e35aa_243_0.png)

现在我们可以添加代码，以传递在我们的第一部电影中录制并存储在 kata.as 中的信息。这将监视视频电影剪辑，并确保脚部图形和字幕在正确的时间播放。此代码添加在按钮代码上方，与录制代码类似，因为它使用了所有相同的位置和旋转变量，但这次是设置这些变量而不是录制它们。让我们来看看。

此函数在任何录制点设置脚部的位置和旋转，并动态放置字幕：

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

它使用与录制电影相同的变量。

然后我们有以下代码来调用 positionLastFeet，这是在下一段代码中创建的函数：

```
positionLastFeet(changeNum);
```

我们想要显示当前位置之前的脚部位置，即 change-1。此代码会创建这些脚部，并使用低透明度，以便我们了解哪些是之前的姿态，哪些是当前姿态：

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

这样我们就可以看到脚部相对于彼此的移动方向和目的，而不是仅仅给出一对没有位置参考的脱离身体的脚。如果没有脚的前一个实例，则会使 lastrightFoot 和 lastleftFoot 实例不可见。无需知道上一个字幕，因此此指令从此函数中省略。

![](img/50202c17d5022233f3e3ec60560e35aa_244_0.png)

为了节省一点处理器使用量，此函数会停止 onEnterFrame 脚本的运行。它还会让 Flash 知道视频已停止播放：

```
stopPlayChecks = function () {
	_root.onEnterFrame = undefined;
	playing = false;
};
```

以下函数是我们的 backBut 和 forwardBut 按钮将调用的函数。previousInstruction 检查当前指令是否不是第一个，调用 stopPlayChecks 函数，然后从 currentInstruction 中减去 1。然后它根据此指令定位脚部，并将两个视频剪辑移动到正确的帧。

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

接下来是 singleCheck 和 playChecks 函数，它们协同工作，监视视频电影剪辑的当前帧号，如果需要，则使用 setFeetGraphic 函数更改脚部位置，然后向 currentInstruction 添加 1。

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

我们希望 playCheck 在视频播放时正常工作，因此需要将额外代码行附加到 PlayBut。

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

第二个函数 nextInstruction 的作用与 previousInstruction 相反。在执行操作时，我们必须将 -1 与 currentInstruction 一起使用，这是因为数组从 0 开始而不是从 1 开始。另一个区别是，currentInstruction 是相加而不是相减。

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

然后我们需要代码，将先前定义的函数附加到先前添加到控制器的按钮上。

```
controls.forwardBut.onRelease = function() {
	nextInstruction();
};
controls.backBut.onRelease = function() {
	previousInstruction();
};
```

我们需要添加一些最终代码来初始化电影。

我们还需要初始化电影，将其中一个视频设置为可见，另一个设置为不可见，因此此代码需要放在 ActionScript 的末尾。

首先，我们将初始视频设置为正面视图：

```
fvvis = true;
video._visible = true;
videoside._visible = false;
```

currentInstruction 设置为 -1，作为我们的计数器：

```
currentInstruction = -1;
```

电影开始使用 playChecks 函数检查每一帧的指令：

```
playChecks();
```

我们告诉 Flash 视频正在播放：

```
playing = true;
```

最后，四行代码确保之前的姿态深度低于当前姿态：

```
rightFoot.swapDepths(3);
leftFoot.swapDepths(4);
duplicateMovieClip("rightFoot", "lastrightFoot", 1);
duplicateMovieClip("leftFoot", "lastleftFoot", 2);
```

这使当前脚部更加突出。在尝试跟随步骤时，我们不希望自己绊倒。

然后我们需要将 singlecheck 函数添加到单帧前进和后退按钮代码中。

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

电影现已准备好发布，我们也准备好进行下一课——学习我们的第一个 kata，但那又是另一本书的内容了。

![](img/50202c17d5022233f3e3ec60560e35aa_246_0.png)

![](img/50202c17d5022233f3e3ec60560e35aa_246_1.png)

![](img/50202c17d5022233f3e3ec60560e35aa_246_2.png)

![](img/50202c17d5022233f3e3ec60560e35aa_246_3.png)

![](img/50202c17d5022233f3e3ec60560e35aa_246_4.png)

![](img/50202c17d5022233f3e3ec60560e35aa_246_5.png)

![](img/50202c17d5022233f3e3ec60560e35aa_246_6.png)

![](img/50202c17d5022233f3e3ec60560e35aa_246_7.png)

