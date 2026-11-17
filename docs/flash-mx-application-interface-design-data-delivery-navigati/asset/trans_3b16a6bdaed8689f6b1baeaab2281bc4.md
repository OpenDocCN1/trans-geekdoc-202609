

转到我们编写 tree.translate 方法的代码图层，并将此方法放置在其下方：

```
tree.startRotate = function(amount) {
    this.rot = this._rotation;
    this.degrees = amount*180/Math.PI;
    while (this.degrees < -180) {
        this.degrees += 360 };
    while (this.degrees > 180) {
        this.degrees -= 360 };
    if (Math.abs(this.degrees - this.rot) > 180) {
        if (this.rot > 0) {
            this.degrees += 360
        } else {
            this.degrees -= 360
        }
    }
    rotateInt = setInterval(this, "rotate",
        intervalTime);
}
```

这段代码看起来比实际更令人困惑。基本上，我将树的当前旋转存储在 rot 中，因为我们会在动画过程中调整这个数字，并且它需要与实际属性保持分离。这是因为该值可能需要超过 180 或 -180，而 _rotation 永远不允许这样做（例如，-190 会自动转换为 170）。我将要旋转到的角度存储在变量 degrees 中（我将其从弧度转换而来）。如果 degrees 值超出 -180 到 180 的范围，我会对其进行调整。一旦 degrees 和 rot 都在同一范围内，我就会找出两者之间的最小旋转量，并在必要时再次调整 degrees。此调整是为了确保向正确方向旋转。例如，如果 degrees 是 170 而 rot 是 -170，那么旋转 20 度就是到达正确角度的最短距离，而不是 340 度。在这种情况下，将从 degrees 中减去 360，剩余量为 -190，这样就能让我们从 -170 旋转 20 度到 -190。将 rot 和 degrees 设置为我们需要的形式后，我设置一个间隔来调用 tree 的 rotate 方法，我们将立即编写该方法。

在前面的代码之后立即放置此方法：

```
tree.rotate = function(amount) {
    this.rot -= (this.rot -
        this.degrees)/intervals;
    this._rotation = this.rot;
    if (Math.abs(this.rot - this.degrees) < 1) {
        clearInterval(rotateInt);
    }
}
```

另一个带有缓动和运动补间的动画。我们只是在每次间隔调用时稍微调整一下树的旋转。一旦足够接近，我们就清除间隔。现在测试你的电影以查看结果。

![](img/50202c17d5022233f3e3ec60560e35aa_107_0.png)

看出问题了吗？通过旋转树，我们也在旋转每个节点，这反过来会导致文本旋转到无法阅读的位置。我们需要做的是将节点图形与树向相反方向旋转。我们将在 NodeClass 内创建一个最后的方法来处理此问题。

在 NodeClass 图层的 NodeClass drawConnector 方法之后添加此方法：

```
NodeClass.prototype.rotateGraphics = \
    function(degrees) {
        this.nodeGraphic._rotation = degrees;
    }
```

在这里，我们只是旋转节点的图形。很简单。现在要调用此方法，我们可以简单地在 tree 的 rotate 方法中放置一个循环来遍历其节点。这是最简单的做法。然而，我想向你展示一种处理此类情况的新方法，这在当前系统中可能不必要，但你以后可能会觉得非常有价值。我们将创建一个自定义事件。

Flash MX 中有一个未记录的功能，它允许我们在电影中创建自己的自定义事件（例如 onEnterFrame 或 onMouseMove），然后注册对象以接收这些自定义事件。例如，你知道每个电影剪辑实例在进入每一帧时都会自动接收通知，你可以编写一个处理程序来在该事件发生时运行函数：

```
mcInstance.onEnterFrame = function() {};
```

在这种情况下，事件已经定义，电影剪辑也已经设置为接收事件通知。现在想象一下，如果你可以定义自己的事件，并决定哪些对象应该在触发这些事件时接收通知。这现在是可能的，并且只需要几行代码。所以让我们试一下！

在代码图层中，将此新行添加到创建我们的 tree 电影剪辑后面：

```
this.createEmptyMovieClip("tree", 0);
tree._x = windowWidth*.5;
tree._y = windowHeight*.5;
tree.depth = 15000;
tree.setMask(mask);

ASBroadcaster.initialize(tree);
```

ASBroadcaster 是一个未记录的对象，它允许我们使新对象能够广播事件，这正是我们希望 tree 能够做到的。initialize 方法将此能力赋予 tree。现在 tree 可以定义新事件以向 Flash 电影广播。

现在我们需要实际广播我们的自定义事件，每次旋转树时都会执行此操作。将这些新行放入我们的 tree.rotate 方法中：

```
tree.rotate = function(amount) {
    this.rot -= (this.rot -
        this.degrees)/intervals;
    this._rotation = this.rot;
    if (Math.abs(this.rot - this.degrees) < 1) {
        clearInterval(rotateInt);
    }
    this.broadcastMessage("onRotate", -this._rotation);
}
```

由于我们已使用 ASBroadcaster 初始化了该对象，我们可以使用 broadcastMessage 来触发自定义事件。现在，每次调用 tree.rotate 函数时，它都会向任何已注册以接收该事件的对象发送自定义事件 onRotate。此外，我们还发送一个额外参数 this._rotation，可供接收事件的对象使用。

只需两行代码就能让我们的新事件正常工作。首先，我们需要有接收这个新事件并希望据此采取行动的对象。

转到 NodeClass 图层，并将以下行添加到 NodeClass 的 init 方法中：

```
this._parent.addListener(this);
this.onRotate = this.rotateGraphics;

if (this._name == "rootNode") {
    this.render();
    return;
}
```

addListener 将此对象（此节点）添加为 tree（this._parent）将广播的任何事件的侦听器。在下一行中，我们为这个自定义事件分配一个函数，即我们刚才编写的 rotateGraphics 方法。现在，除了接收所有标准电影剪辑事件（enterFrame、mouseMove、load 等）的通知外，我们的 NodeClass 实例在树旋转时也会接收通知，并且在发生此事件时将使用 onRotate 处理程序。

现在测试你的电影，看看节点如何知道何时旋转其图形。这种分配自定义事件的能力非常有用——而且玩起来也相当有趣！

![](img/50202c17d5022233f3e3ec60560e35aa_109_0.png)

## 进一步探索

在本章中，我向你展示了如何构建、操作和动画化分支结构。如果你想完整查看代码，本教程中展示的完成文件可以在下载文件中找到，名为 gods_tree_book.fla。正如你在初始 gods_tree.swf 中看到的那样，我通过允许用户单击节点以访问其他信息（此外，我还向系统添加了配偶节点）来为该系统构建了另一层功能。所有代码都有注释，我鼓励你打开它并了解某些事情是如何完成的。

此外，想象一下你可以将这个概念和文件带向何方。虽然它非常适合显示分支信息，而且确实是为此构建的，但我忍不住想到一些可以从此系统构建的精彩游戏，从更复杂的“打地鼠”到“选择你自己的冒险”类型的交互式故事。与其加载一个满载信息的单个界面，你或许可以将系统设置为一个画廊，在节点上选择低分辨率图片来加载高分辨率的全屏版本。画廊系统是否可以根据用户之前选择的图片类型进行响应，在下一代中加载类似或互补的图片？也许你可以完全移除用户，使用一些随机生成和古怪的数学来动画化节点和系统的颜色，创作一些超现实的 Web 艺术。或者，也许我应该停止透露我的想法，抢在你之前行动！

