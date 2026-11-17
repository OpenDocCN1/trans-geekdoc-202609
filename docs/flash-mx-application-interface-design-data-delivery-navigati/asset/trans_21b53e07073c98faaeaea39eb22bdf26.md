

现在，当按下新部分时，之前选定的部分将收回其左侧。测试你的电影以查看其工作原理。

![](img/50202c17d5022233f3e3ec60560e35aa_72_0.png)

在 retractLeftSide 函数之后，开始我们之前调用的 addContent 函数：

```
addContent = function() {
    this.drawing.bottom = 0;
    this.onEnterFrame = extendBottomSide;
}
```

显然，这目前还没有添加任何内容，但我们稍后会处理这个问题。与此同时，让我们专注于我们刚刚设置为在 onEnterFrame 处理程序上调用的 extendBottomSide 函数。一旦部分按钮向界面左侧展开，这就是将负责将窗口向下扩展的函数。请注意，首先我们将表示底部边当前位置的 bottom 属性设置为 0。让我们来处理 extendBottomSide 以了解其工作原理。

将此代码紧跟在 addContent 函数上方放置：

```
extendBottomSide = function() {
    var mc = this.drawing;
    mc.bottom += ((windowBottom._y - topSectionY()) - mc.bottom)/1.2;
}
```

它开始时足够简单，使用与我们之前函数中相同的缓动代码，每次调用稍微调整一下底部边。接下来的代码将处理绘制本身。

将此代码放在前面几行之后：

```
with (mc) {
clear();
lineStyle(1, currentColorScheme.foreground, 100);
for (var j = 0; j < 3; j++) {
moveTo(getRandom(10) - leftSide, getRandom(10) - buttonHeight);
lineTo(getRandom(10) + halfButtonWidth, getRandom(10) - buttonHeight);
lineTo(getRandom(10) + halfButtonWidth, getRandom(10));
lineTo(getRandom(10) - branchDown, getRandom(10));
lineTo(getRandom(10) - branchDown, getRandom(10) + bottom);
lineTo(getRandom(10) - leftSide, getRandom(10) + bottom);
lineTo(getRandom(10) - leftSide, getRandom(10) - buttonHeight);
}
}
```

在这种情况下，我们不能调用 drawBorders 函数，因为现在我们处理的是六边形而不是四边形。然而，尽管有额外的边，概念仍然相同。我们循环三次，为窗口底部边向下扩展时的每一边绘制随机线条。现在，当然，我们需要检查何时到达底部。

键入以下行以完成 extendBottomSide 函数：

```
if ((windowBottom._y - topSectionY) - mc.bottom < 1) {
delete this.onEnterFrame
}
```

与之前一样，我们检查每次函数调用，以查看何时足够接近目的地以停止，此时将删除 onEnterFrame 处理程序。现在测试你的电影以查看结果。

![](img/50202c17d5022233f3e3ec60560e35aa_73_0.png)

好了，现在我们可以看到需要添加内容的位置了，因此让我们按照所示在 addContent 函数中添加以下行来处理它：

```
addContent = function() {
  this.drawing.bottom = 0;
  this.onEnterFrame = extendBottomSide;
  var content = this._parent.createEmptyMovieClip("content", 50);
  var margin = sectionXPoss - extendedButton;
  content.createTextField("info", 0, margin*1.6, windowHeight*.25, windowWidth*.45, windowHeight*.45);
  var info = content.info;
  info.setNewTextFormat(infoTF);
  info.embedFonts = 1;
  info.selectable = 0;
  info.wordWrap = 1;
  info.text = sections[currentSection].info;
  info._y -= info.textHeight/2;
}
```

content 是我们添加到主时间轴（this._parent）的一个电影剪辑，用于保存所有内容。margin 持存放在打开的窗口左侧的空间量，当我们开始放置项目时会有所帮助。我们添加的文本字段位于窗口左上角，下方四分之一处，宽度和高度大约为窗口本身的一半。我们为它提供了所有必要的格式，包括换行功能，并放置我们随部分包含的任何信息文本。

接下来，我们将为部分附加并上色合适的图像。将此代码紧跟在上面最后一行之后，但在 addContent 的闭合括号之前放置（此代码全部属于 addContent）：

```
var image = content.attachMovie(sections[currentSection].image, "image", 500);
imageColor = new Color(image);
imageColor.setRGB(currentColorScheme.foreground);
image.onRollOver = function() { info.text = sections[currentSection].info };
image.useHandCursor = 0;
image._x = windowWidth*.65;
image._y = windowHeight*.1;
```

这段代码都相当简单。我们附加一张图像，根据前景颜色为其上色，赋予其按钮动作以便在 rollOver 时将部分信息放回 info 文本字段，禁用手形光标，最后将图像放置在窗口右上角。

![](img/50202c17d5022233f3e3ec60560e35aa_74_0.png)

![](img/50202c17d5022233f3e3ec60560e35aa_74_1.png)

![](img/50202c17d5022233f3e3ec60560e35aa_74_2.png)

![](img/50202c17d5022233f3e3ec60560e35aa_74_3.png)

![](img/50202c17d5022233f3e3ec60560e35aa_74_4.png)

![](img/50202c17d5022233f3e3ec60560e35aa_74_5.png)

继续编写 addContent，将此代码放在前面的图像代码之后（同样在 addContent 的闭合括号之前）：

```
var midLine = content.createEmptyMovieClip("midLine", 250);
midLine.lineStyle(1, currentColorScheme.foreground, 100);
for (var i = 0; i < 4; i++) {
midLine.moveTo(getRandom(10) + margin, getRandom(10) + windowHeight/2);
midLine.lineTo(getRandom(10) + windowWidth + margin, getRandom(10) + windowHeight/2);
}
```

midLine 是绘制在窗口两半之间的线条。在这里，我们只是创建一个新的电影剪辑，并以与之前代码中绘制边框相似的方式，在窗口中间附近随机绘制线条总共四次。

这最后一段代码应紧跟在上面的 midLine 代码之后，并立即置于 addContent 的闭合括号之前：

```
content.createTextField("textBlock", 777, margin*1.4, windowHeight*.53, windowWidth*.95, windowHeight*.4);
var tb = content.textBlock;
tb.setNewTextFormat(infoTF);
tb.embedFonts = 1;
tb.wordWrap = 1;
tb.selectable = 0;
tb.text = sections[currentSection].textBlock;
```

为了结束 addContent，我们添加并格式化另一个文本字段来保存界面底部的文本。这是存储在部分的 textBlock 属性中的文本将显示的位置。现在就去测试你的电影以查看结果。

![](img/50202c17d5022233f3e3ec60560e35aa_75_0.png)

我们几乎完成了，但你可以看到出现了一些问题。首先，在窗口完全打开之前就能看到内容；其次，选择新部分时内容不会立即被移除。让我们通过添加遮罩来处理第一个问题，以揭示内容。我们将在 addContent 代码中执行此操作。

将这些行放在 addContent 函数的末尾，紧跟在 tb 的格式化之后：

```
this.createEmptyMovieClip("contentMask", 50);
content.setMask(this.contentMask);
```

这很简单，但我们实际上只有一个空剪辑。我们需要在其中绘制一些东西来作为遮罩区域。我们将在 extendBottomSide 函数中处理这个问题，这很合适，因为这是我们希望遮罩逐渐揭示内容的地方。

将这些行放在 extendBottomSide 函数中的最终 if 语句之前：

```
this.contentMask.clear();
this.contentMask.beginFill(0, 0);
drawBox(this.contentMask, -mc.leftSide, -buttonHeight, -branchDown, mc.bottom);
this.contentMask.endFill();
```

现在我们有东西了！contentMask 内部的框可以使用 drawBox 函数绘制，因为我们希望为内容创建一个矩形遮罩。随着 mc.bottom 每次函数调用稍微调整一点，遮罩将随绘制的边框一起扩展，以揭示更多内容。

最后一件需要处理的事情是移除之前的内容。这可以通过在 selectMe 函数中添加几行额外代码来完成，这是需要移除旧内容的位置。

将以下行添加到 selectMe 的开头（仍在部分代码图层上）。它可以添加在第一个 for 循环之前的任何位置。

```
this._parent.content.removeMovieClip();
```

这样就移除了内容。同时也要处理遮罩，请将以下新行添加到第二个 for 循环中：

```
for (var i in sectionButtons) {
    if (sectionButtons[i].selected) {
    sectionButtons[i].onEnterFrame = retractLeftSide;
    sectionButtons[i].contentMask.removeMovieClip();
    sectionButtons[i].btn.enabled = 1;
    delete sectionButtons[i].selected;
    }
}
```

有了这些添加，现在测试你的电影并看看我们取得了什么成就！

![](img/50202c17d5022233f3e3ec60560e35aa_76_0.png)

![](img/50202c17d5022233f3e3ec60560e35aa_76_1.png)

![](img/50202c17d5022233f3e3ec60560e35aa_76_2.png)

![](img/50202c17d5022233f3e3ec60560e35aa_76_3.png)

![](img/50202c17d5022233f3e3ec60560e35aa_76_4.png)

![](img/50202c17d5022233f3e3ec60560e35aa_76_5.png)

![](img/50202c17d5022233f3e3ec60560e35aa_76_6.png)

