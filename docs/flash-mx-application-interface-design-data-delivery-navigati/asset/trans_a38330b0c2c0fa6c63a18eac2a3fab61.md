

## 制作应用程序

该应用程序由右侧的一个相当基础的界面和左侧的一个大型绘图空间组成，绘图空间上有一件 T 恤衫图形。界面下方还有一个'帮助'区域，用于显示你当前使用的工具的信息，并在你将鼠标悬停在界面上的按钮时显示该工具的用途。让我们快速看一下屏幕布局，以及每个按钮的功能。

![](img/50202c17d5022233f3e3ec60560e35aa_189_0.png)

- Pencil tool – the-standard free-draw tool for pencil lines. This is also the default tool.
- Line tool – similar to the pencil, but for drawing straight lines.
- Curve tool – for drawing Bezier curves, click and drag three points to define the shape.
- Fill draw tool – for drawing filled shapes. Rather than a paint bucket, if you want to fill a shape then you have to draw that shape as you would with the pencil, and then release the mouse to fill the shape. If you don't want a line around the fill, then either set the line to be the same color as the background, or set its alpha to zero.
- Mask draw tool – this is similar to the fill draw tool, but it defines the shape for the mask that you will see the JPG through. You can draw more than one shape with this tool to create numerous windows into your image. The color and alpha settings of this tool make no difference to its effect.
- JPG mask toggle button – this button simply toggles the JPG mask on and off. When it's on, only the masked parts of the image are shown, and when it's off, the complete image and mask are shown.
- Mask move tool – this allows you to click on your JPG mask and drag it around to another position.
- JPG move tool – this is similar to the mask move tool, but you move the JPG rather than the mask.
- JPG scale tool – this tool allows you to click and drag on a JPG to resize it. You can also hold the SHIFT key down while you're dragging to constrain the proportions of the image.
- Load JPG button – this button will open up another box that allows you to enter the URL of a picture that you want to load into your image. You can only load one image per picture. When they are loaded in, the pictures are automatically resized to a square in the center of the t-shirt. Use the JPG scale tool to alter their size and proportions if needs be.

![](img/50202c17d5022233f3e3ec60560e35aa_190_0.png)

- The color palette – this is where you choose the colors to draw with. Make sure the right color chip is selected first, then choose a color and start drawing.
- Toggle t-shirt mask button – this toggles the main t-shirt mask on and off, hiding any extraneous elements that may have strayed over the edge of the shirt.

了解应用程序制作方式的最佳方法是将界面的每个单独工具和元素分解开来。我们将从整个应用程序的几个基础知识开始。

- Brush size – allows you to change the size of the stroke/brush lines. 1 is normal, 100+ is big... very big
- Brush and fill alpha – both of these boxes allow you to enter a percentage of opacity for strokes or fills respectively. Try layering large brush strokes with low alphas... mmmm...

![](img/50202c17d5022233f3e3ec60560e35aa_190_1.png)

- Brush, fill, and t-shirt color chips – click once on these to select them (the selected one has a yellow center), and then click on a color in the palette to change to it. Changing the t-shirt color will have an immediate effect, the brush and fill colors will only come in to effect the next time you use one of the appropriate tools.

![](img/50202c17d5022233f3e3ec60560e35aa_190_2.png)

## 初始化电影

在查看电影的其余部分之前，需要先初始化一些基本变量和电影剪辑。

此绘图边界在整个代码开始时定义，并由所有绘图工具使用。以下是全局声明：

```
_global.tableleft = _root.square._x-(_root.square._width/2);
_global.tableright = tableleft+_root.square._width;
_global.tabletop = _root.square._y-(_root.square._height/2);
_global.tablebottom = tabletop+_root.square._height;
```

平板或绘图边界被定义为主舞台上方形电影剪辑所占据的空间。这里的公式只是计算方形的边界，并将其存储在四个全局变量中。你将在整个代码中看到这些变量的使用。

全局变量 tempLayer 引用了用于预览某些绘图工具的电影剪辑。

```
_root.createEmptyMovieClip("temporaryDrawLayer", 8000);
_global.tempLayer = _root["temporaryDrawLayer"];
```

我们使用全局变量来保存对主要对象的引用，以便我们可以在代码中快速轻松地引用它们，而无需每次都输入完整路径，并且如果我们随时更改图层结构的设置或其名称，则只需在代码中的一个位置进行更改，而不是每次引用图层时都更改。

drawPad 存储使用界面创建的所有绘制元素：

```
_root.createEmptyMovieClip("drawingPad", 45000);
_global.drawPad = _root.drawingPad;
```

hitArea 告诉 drawPad 使用舞台上的方形电影剪辑作为命中区域：

```
drawPad.hitArea = _root.square;
```

![](img/50202c17d5022233f3e3ec60560e35aa_191_0.png)

![](img/50202c17d5022233f3e3ec60560e35aa_191_1.png)

![](img/50202c17d5022233f3e3ec60560e35aa_191_2.png)

![](img/50202c17d5022233f3e3ec60560e35aa_191_3.png)

jamJar 存储对一个保存蒙版和 JPG 电影剪辑的电影剪辑的引用：

```
_root.createEmptyMovieClip("JPGAndMaskHolder", 501);
_global.jamJar = _root.JPGAndMaskHolder;
```

你可能会问，为什么叫 jamJar？嗯，jam 代表 JPG And Mask，而 jar 是容器。这有点深奥，但它最初叫 jamHolder，而 jamJar 听起来好多了。

JPGContainer 是加载 JPG 图形的电影剪辑的父级：

```
jamJar.createEmptyMovieClip("JPGHolderHolder", 502);
_global.JPGContainer = jamJar.JPGHolderHolder;
```

JPGHolderHolder 看起来可能是个愚蠢的名字，但从逻辑上讲，这个电影剪辑是容纳 JPG 电影剪辑的容器，所以它有点说得通。幸运的是，这个名字只在这里提到，从现在开始，它就是更令人愉悦的 JPGContainer。JPG 图形嵌套在这个电影中用于缩放和 JPG 操作。稍后再详细介绍。

JPG 是我们加载 JPG 图像的电影：

```
JPGContainer.createEmptyMovieClip("JPGHolder", 500);
_global.JPG = JPGContainer.JPGHolder;
```

JPGM 存储绘制蒙版的电影剪辑的引用：

```
jamJar.createEmptyMovieClip("masker", 503);
_global.JPGM = jamJar.masker;
```

稍后再详细介绍。

![](img/50202c17d5022233f3e3ec60560e35aa_192_0.png)

![](img/50202c17d5022233f3e3ec60560e35aa_192_1.png)

![](img/50202c17d5022233f3e3ec60560e35aa_192_2.png)

![](img/50202c17d5022233f3e3ec60560e35aa_192_3.png)

## 界面元素

### 按钮

界面中所有主要按钮都基于相同的模型，并且使用相同的代码来工作。每个按钮非常简单地由两个帧组成，第一个帧上有一个停止动作以防止其自动播放。第一个帧是按钮的正常状态，带有白色背景，第二个帧是按钮的'按下'状态，带有黄色背景。

所有按钮都使用相同的代码，因此在初始设置函数中将相同的函数附加到它们上更有意义，而不是为每个按钮在单独的函数中重复相同的代码。在 Flash 中做到这一点的方法是使用 call 动作。以下是自由绘制工具函数调用的示例：

```
mainButCall.call(mainButDraw,
  funcFreeDraw, undefined, "Click and drag
  to draw pencil lines", "Pencil Tool");
```

mainButCall 是按钮初始化函数的名称，我们稍后将看看它是如何工作的。然后我们向此函数传递五个参数 – 让我们快速看看它们的含义：

- mainButDraw – 这是将要附加函数的舞台上电影剪辑的名称。
- funcFreeDraw – 这是我们希望按钮被单击时运行的函数的名称。
- undefined – 这是一个额外参数，我们可以将其传递给按钮调用的函数。在此 FLA 的大多数情况下，这都是 undefined，我们实际上只将其与 fillDraw 函数一起使用，以告知其绘制位置。
- "Click and drag to draw pencil lines" – 这是使用工具时将在屏幕底部显示的帮助文本。
- "Pencil Tool" – 这是用户将鼠标悬停在按钮上时将显示的帮助文本。

现在我们知道要传递给函数的内容了，让我们来看看这个函数，看看我们如何处理每个参数。（请记住上面调用的第一个参数是 call 动作用于附加函数的电影剪辑的名称，因此该参数不会传递给函数本身）。

```
mainButCall = function (funcName, pass,
  helpText, rollText) {
  this.onRelease = function() {
    allButsOff();
    this.gotoAndStop(2);
    funcName(pass);
    _root.help.text =
      _root.help.prev=helpText;
  };
  this.onRollOver = function() {
    _root.help.prev = _root.help.text;
    _root.help.text = rollText;
  };
  this.onRollOut = function() {
    _root.help.text = _root.help.prev;
  };
};
```

当你单击按钮时，首先发生的是调用一个函数来关闭所有按钮。这只是一种懒惰的方法，不必存储先前使用的工具，我稍后会解释它是如何工作的。接下来发生的是，当前按钮转到其第二个帧（带有黄色背景）以显示它已被单击。然后它调用与之关联的相关函数，最后设置在工具使用期间将在屏幕底部显示的帮助文本。帮助文本只是一个动态文本框，每当按钮被单击或鼠标悬停时都会设置它。

