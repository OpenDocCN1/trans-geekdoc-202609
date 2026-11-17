

选择代码图层第一帧中的空白关键帧，并打开 ActionScript 编辑器。在代码中我们要做的第一件事是为影片设置几个变量。请输入：

```
stageWidth = 550;
stageHeight = 400;

moveWidth = stageWidth*.5;
moveHeight = stageHeight*.5;

totalY = logo._height;
totalX = logo._width;

totalLasers = 5;
```

stageWidth 和 stageHeight 是我们影片的尺寸。不直接硬编码这些值，你可能想使用新 Stage 对象的 width 和 height 属性。不过，我在测试过程中发现，有时这些值是错误的。如果你使用 _root_.width 和 _root_.height，你会得到舞台上所有对象周围边界框的宽度，而不是你在影片属性中设置的值（尽管当嵌入 HTML 页面时它可以正常工作），因此我倾向于在代码的前几行硬编码这些尺寸。

moveWidth 和 moveHeight 是我们的激光（发射光束的球体）在舞台上移动时所走的最大距离。我们实际上会让激光的运动围绕标志居中，因此这两个变量会让激光保持在屏幕中心附近。

totalX 和 totalY 将用于我们要在标志上绘制的遮罩。它将是一个矩形遮罩，这两个变量保存该矩形的最终尺寸。如果你在舞台上选择标志电影剪辑，你会发现我已经给它指定了实例名称 logo。

最后，totalLasers 是一个保存我们要添加到舞台上的激光数量的变量。我发现五是一个对我而言处理器友好的不错数字，但你可以在测试时随意调整这个数字。

下一步是创建我们将用于绘制标志遮罩的空电影剪辑。在前面的代码行之后输入以下代码：

```
this.createEmptyMovieClip("mask", 100);
mask._x = logo._x;
mask._y = logo._y;
logo.setMask(mask);
```

在这些行中，我们创建一个名为 mask 的电影剪辑并将其放置在标志的注册点（你会注意到它设置在符号的左上角）。然后我们使用新的 setMask 方法将其启用为标志电影剪辑的遮罩。

设置好这些基本变量和遮罩后，让我们编写一个函数，在每一帧调用它来监控加载状态：

```
assessLoad = function(clip) {
// var kbLoaded = Math.floor(clip.getBytesLoaded()/1024);
// var kbTotal = Math.floor(clip.getBytesTotal()/1024);

// delete these two lines and uncomment
// the above lines upon publishing
var kbLoaded = Math.floor(getTimer()/200) + 2;
var kbTotal = 150;}
```

这是预加载器的核心。我们创建了一个名为 assessLoad 的函数，并向它发送一个电影剪辑的引用（参数中的 clip）。这就是我们要检查加载状态的剪辑。它可以是主影片、电影剪辑或某个层级，这取决于我们向函数传递什么。被注释掉的前两行是在在线使用此文件时会使用的内容。为了测试目的，我在接下来的几行中伪造了一些变量，你在发布此文件的最终版本时会删除它们。让我们来看看被注释掉的行实际上为我们做了什么。

函数声明后的第一行创建了一个名为 kbLoaded 的局部变量，并在该变量中保存剪辑中当前已加载的千字节数（getBytesLoaded 返回字节，因此除以 1024 将其转换为千字节）。下一行将剪辑中千字节的总数存储在名为 kbTotal 的变量中。当此影片在线时，这些就是函数需要查看的数字。

为了在测试期间正常工作，我在接下来的两行中为这些变量创建了伪值。kbLoaded 从影片的当前毫秒数获取其值。kbTotal 只是一个硬编码数字。你在最终发布时会删除这些行。

通过输入以下行来完成此函数：

```
var percentOfLogo =
    Math.floor(kbLoaded/kbTotal * totalY);
loaded.text = kbLoaded + "KB";
total.text = kbTotal + "KB";
drawLogo(percentOfLogo);
if ((kbLoaded >= kbTotal) && kbTotal > 1) {
    endPreload(clip);
}
```

在这里，我们通过将已加载字节数除以总字节数来计算当前已加载字节的百分比。由于此数字在 0 到 1 之间，我们将其乘以 totalY 变量（标志的高度），以确定我们应该在标志上向下绘制遮罩多远（标志 totalY 的一个百分比）。调用 Math.floor 舍入方法将数字舍去到最接近的整数。

接下来的两行将我们的两个千字节值放入舞台上各自的文本字段中，并在数字后添加字符串 "KB"。然后我们调用一个名为 drawLogo 的函数，并向它传送要绘制的标志当前百分比。这个函数实际上会绘制遮罩并激活我们的激光。最后几行是在加载完成时结束预加载动作。if 语句检查已加载的千字节数是否大于或等于总千字节数，这意味着所有内容都已加载。if 语句的第二个条件只是我使用的一种保障措施，用于在进行此检查前确保已加载一些内容（偶尔，第一个条件可能是 undefined == undefined，这将求值为 true）。如果所有内容都已加载，我们会调用 endPreload 函数，我们稍后会编写它。

我们接下来要讨论的函数是上一段代码中调用的 drawLogo 函数。将这些行紧接在 assessLoad 函数之后放置：

```
drawLogo = function(percent) {
    mask.clear();
    mask.beginFill(0, 100);
    mask.lineTo(totalX, 0);
    mask.lineTo(totalX, percent);
    mask.lineTo(0, percent);
    mask.endFill();
    for (var i in lasers) {
        lasers[i].drawLaser(percent)
    }
}
```

如果你尚未使用过新的绘图 API（应用程序编程接口），它非常容易上手。在上述代码中，我们首先清除遮罩电影剪辑中之前绘制的任何内容。每次我们打算绘制新内容时都需要这样做。使用 beginFill 方法，我们设置遮罩的颜色和 Alpha 值。由于遮罩不会可见（就像你在创作环境中创建的遮罩一样），这两个值都不重要，所以我只是将颜色设置为黑色（值为 0x000000，即 0），Alpha 设置为 100。

此函数中的接下来三行使用 lineTo 方法绘制遮罩矩形的三条边。需要注意的是，每次对剪辑调用 clear 方法时，剪辑的“笔”都会移动到注册点 (0, 0)。第一个 lineTo 然后绘制一条线到标志的右侧，由 totalX 表示。第二个 lineTo 垂直向下绘制到当前加载百分比确定的 totalY 数量。第三个 lineTo 接着绘制一条线回到标志的左侧。调用 endFill 方法会自动通过绘制最后一条线返回注册点来关闭我们的矩形。

![](img/50202c17d5022233f3e3ec60560e35aa_18_0.png)

最后的 for in 循环遍历我们将在舞台上放置的每个激光。lasers 数组实际上将保存每个激光电影剪辑的引用。这些剪辑中的每一个都将保存一个名为 drawLaser 的方法。我们稍后会查看这个方法。

我们的最后一个通用函数在加载完成时被调用。将这些行放在 drawLogo 函数之后：

```
endPreload = function(clip) {
   clearInterval(preload);
   mask.removeMovieClip();
   for (var i in lasers) {
      lasers[i].leaveStage();
   }
   loaded.text = "";
   total.text = "";
}
```

请记住，在我们的 assessLoad 函数中，clip 是我们正在评估的电影剪辑。加载完成后，将调用此函数。我们会在这里添加在跳转到主内容、主页或其他我们要加载的内容之前需要清理的任何内容。

preload 将是不断调用我们上面 assessLoad 函数的间隔的标识符。我们将在代码稍后使用新的 setInterval 函数来创建它。在这里，我们通过调用 clearInterval 函数来删除该间隔。接下来，我们删除我们在代码顶部动态添加到舞台上的遮罩电影剪辑。接下来的 for in 循环遍历我们的 lasers 数组并调用每个激光的 leaveStage 方法，这会将激光赶出舞台右侧。最后，我们通过将两个文本字段的文本值设置为空字符串来清除它们的文本。如果你实际上想要将播放头发送到另一帧，这就是你会执行的地方（或者你可能会等待所有激光退出舞台）。

接下来的这段代码启动所有内容：

```
preload = setInterval(assessLoad, 40, this);
```

新的 setInterval 命令非常出色。在这种形式下（还有其他形式——我们将在本教程稍后使用另一种），它至少需要两个参数，但可以接受更多。第一个是要调用的函数的名称，在我们的情况中是 assessLoad。第二个参数是每次调用函数之间的毫秒数。我们每 40 毫秒调用一次 assessLoad 函数。我们发送的最后一个参数是传给 assessLoad 的参数，你会记得那是要观看的剪辑。我们发送 this，即 _root 主影片。如果你要加载到另一个层级或电影剪辑中，你可以简单地用 _level1 或 myMC 或你正在处理的任何层级或实例名称来替换它，代码就会正常工作。

