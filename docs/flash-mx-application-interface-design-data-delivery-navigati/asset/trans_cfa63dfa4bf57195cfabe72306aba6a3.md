

但是，如果图片已经在缓存中——比如说另一个浏览器窗口已经打开了它——那么图片就会加载进来。考虑到这一点，JavaScript 弹出式窗口方案可以正常工作，也就是说，如果你喜欢窗口到处弹出的话...

你可以猜到，这全部造成了一种相当糟糕的局面。如果你在浏览器中测试 SWF，别指望还能看到第二张图片。

绕过这种缓存的已知方法是，向服务器端脚本发送带随机数的查询字符串，从而阻止 IE 显式地对其进行缓存。

## 工作原理

经历了所有那些“邪恶”之后，让我们来评估一下该工具的功能。加载 JPG 工具通过打开一个对话框来工作，该对话框请求 JPG 图像文件的 URL 或位置。该位置可以相对于 SWF 的位置，也可以是带 Web 前缀的绝对路径。

![](img/50202c17d5022233f3e3ec60560e35aa_209_0.png)

如果你离线测试 SWF，只需将一张 JPG 放在与 SWF 相同的文件夹中并调用它。这样可以节省一些输入和下载。

单击 GO 按钮后，图片会被获取（如果存在），并且已加载百分比会显示并更新。

当图片完全加载后，对话框消失，图片被调整为 200 x 200 像素，并位于 T 恤中央，与原始大小无关。JPG 缩放工具被加入是为了允许用户调整图片大小。

代码由两个主要函数组成——funcLoadJPG 和 loadImage。前者执行所有图形和进度职责，而 loadImage 函数负责加载和完成任务。

这里代码量不少，但没有我们搞不定的。

首先，我们声明函数并调用对话框：

```
funcLoadJPG = function () {
  _root.attachMovie("loadJPGBox",
    "loadJPGBox", 111111);
  _root.loadJPGBox._x = (Stage.width/2);
  _root.loadJPGBox._y = (Stage.height/2);
  Selection.setFocus
  ("_root.loadJPGBox.urlText");
}
```

loadJPGBox 从库中调入，并在舞台上被赋予相同的名称。然后它在屏幕上定位。

下一行使用 Selection 对象，将对话框的 urlText 输入字段设置为文本光标焦点。该对象对于任何输入情况都非常有用，通常用户必须先选择文本框才能继续。这提供了一定程度的自动化，并允许用户立即输入。

接下来这段代码为对话框的 GO 按钮设置初始代码：

```
_root.loadJPGBox.goBut.onRelease = function() {
  JPG.unloadMovie();
  _root.loadImage(_root.loadJPGBox.urlText.text);
  _root.loadJPGBox.loadJPGBoxText.text = "Please
  wait... loading JPG\rIf nothing
  happens for a long time,\rplease
  hit Cancel and try another image";
  _root.loadJPGBox.goBut._visible =
  false;
}
```

首先发生的是 JPG 被清除。JPG 稍后定义，但基本上是我们 loadMovie 调用的容器。下一行调用 loadImage 函数——稍后定义——并发送对话框文本框的输入。

之后，我们设置对话框的文本，向用户告知当前状态。顺便说一句，如果你曾经好奇这里的 \r 是什么，它基本上是一个换行符，相当于 HTML 中的 <br> 或众多其他脚本语言中的 \n。

最后一行隐藏 GO 按钮——因为我们不再需要它了。它已经实现了自己的目的和存在理由。

接下来这段代码会每帧检查图片是否已加载，然后再重置按钮、启用铅笔工具并移除对话框：

```
_root.loadJPGBox.onEnterFrame =
    function () {
    if (JPG.getBytesLoaded() ==
        JPG.getBytesTotal() &&
        JPG.getBytesTotal() != 0) {
        _root.allButsOff();
        _root.mainButDraw.gotoAndStop(2);
        _root.funcFreeDraw();
        _root.help.text = "Click and drag
        to draw pencil lines";
        removeMovieClip(_root.loadJPGBox);
    }
}
```

我们重置到铅笔工具仅仅因为它是默认工具，你可以轻松地将其更改为默认其他工具（例如 JPG 移动工具），如果你更喜欢的话。

条件语句之所以是这样，是因为：

```
if (JPG.getBytesLoaded() ==
    JPG.getBytesTotal() &&
    JPG.getBytesTotal() != 0) {
```

...其目的是检查图片是否已加载，以及 getBytesTotal 是否不等于零。Flash 通常对传入文件的响应会稍慢一些，可能会在一段时间内将此值保持为零，直到它意识到文件正在传输中。

我们还需要在对话框中设置 CANCEL 按钮：

```
_root.loadJPGBox.cancelBut.onRelease
    = function() {
    _root.allButsOff();
    _root.mainButDraw.gotoAndStop(2);
    _root.funcFreeDraw();
    _root.freeDraw("");
    _root.help.text = "Click and drag to
    draw pencil lines";
    removeMovieClip(_root.loadJPGBox);
    JPG.unloadMovie();
}
```

如果被点击，工具会被重置，铅笔工具被激活，对话框被移除，JPG 的内容被卸载。这里没有太复杂的内容，但对于用户来说是一个必要的功能。

现在我们进入最重要的函数——即实际加载 JPG 的那个函数：

```
loadImage = function (imageFileName) {
    JPG.loadMovie(imageFileName);
```

声明此处后，JPG 全局变量被告知使用参数 imageFileName 加载图片。将 JPG 加载到 Flash 时，使用 loadMovie 命令。

接下来是每帧运行的代码：

```
_root.onEnterFrame = function() {
if (JPG.getBytesLoaded() > 0) {
_root.loadBoxPerc.text =
(Math.floor((JPG.getBytesLoaded() /
JPG.getBytesTotal()) * 100)) + "%";
}
if (JPG.getBytesLoaded() ==
JPG.getBytesTotal() &&
JPG.getBytesTotal() != 0) {
```

它设置对话框中显示的已加载百分比文本，并检查图片是否已完全加载。这里执行相同的条件判断，以抵消 Flash 对文件的慢速读取。

当图片完全加载后，我们还需要一些代码将其放置在屏幕上：

```
JPG._width = 200;
JPG._height = 200;
JPG._x = -JPG.width/2;
JPG._y = -JPG._height/2;
JPG._visible = true;
JPGContainer._x = _root.square._x;
JPGContainer._y = _root.square._y;
JPGContainer._xscale = 100;
JPGContainer._yscale = 100;

_root.onEnterFrame = undefined;
duplicateMovieClip(_root.tshirt,
"newtee", 600);
JPGContainer.setMask(_root.newtee);
```

JPG 电影剪辑被调整为强制的 200 x 200 像素，图片被重新定位，使其居中于注册点（加载图片时，默认位于绝对位置 0,0）。这样重新定位是为了让 JPG 缩放工具能够从中心向外缩放它。

![](img/50202c17d5022233f3e3ec60560e35aa_211_0.png)

接下来的两行代码将 JPGContainer 定位到与 square 相同的位置。square 具有中心注册点，因此此操作将 JPG 图像居中于 T 恤中间。

然后 JPGContainer 被重置为 100% 的缩放比例，以重置之前的任何操作。

这里最后几行代码为 JPGContainer 设置了一个遮罩，以便图像在移动时不会覆盖界面。

![](img/50202c17d5022233f3e3ec60560e35aa_211_1.png)

JPG 加载部分就到这里。

本章后续将通过 JPG 缩放工具和动态遮罩扩展 JPG 元素...

## JPG 遮罩

本应用中 JPG 遮罩的吸引力超出了标准方形或形状遮罩。在此应用中，用户可以绘制自己的遮罩形状，然后将其应用于加载的 JPG。

此部分将分为两个部分——第一部分涵盖遮罩的绘制，第二部分将遮罩应用到 JPG 图像上。

### 绘制遮罩

![](img/50202c17d5022233f3e3ec60560e35aa_212_0.png)

你会很高兴地知道，我们已经介绍了绘制遮罩所需的工具。遮罩绘制使用填充绘制工具代码，但绘制到其自己的图层上。此工具的绘制电影剪辑在整个电影的初始化中设置：

```
jamJar.createEmptyMovieClip("masker", 503);
```

该电影剪辑在那里也被设为全局：

```
_global.JPGM = jamJar.masker;
```

将用户限制使用类似填充绘制的工具的原因是，描线不能用作遮罩，因此线条工具或铅笔工具几乎没用，所以我在开发期间决定将工具限制为此。

这不仅为我省了一些编码工作（制作新工具），还能让用户同时熟悉此工具和填充绘制工具。一举两得。

一旦你绘制了遮罩形状，你就需要一个让它去遮罩的东西...

### 将遮罩应用到 JPG

![](img/50202c17d5022233f3e3ec60560e35aa_212_1.png)
![](img/50202c17d5022233f3e3ec60560e35aa_212_2.png)
![](img/50202c17d5022233f3e3ec60560e35aa_212_3.png)

将遮罩应用到图像的开关是通过一个简单的函数来实现的。

这里的一般策略是使用 setMask 方法，并根据上一状态切换遮罩的开启或关闭。以下是第一段代码：

```
funcApplyMask = function () {
  _root.allButsOff();
  _root.mainButDraw.gotoAndStop(2);
  _root.funcFreeDraw();
  _root.help.text = "Click and drag to
  draw pencil lines";
}
