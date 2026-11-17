

我们使用 num 值（即传递给该方法的 kidCount 值）来指定 kidsArray 中哪个条目包含新节点的正确信息，并用于计算其目标弧度值 radianTarg。附加新的 clusterNode 电影剪辑后，我们将 newKid 的引用放入当前节点的 kidMCs 数组中。稍后我们会用到这个。moveToPosition 方法非常简单：

```
clusterNode.prototype.moveToPosition = function(radius) {
    this.radiusTarg = radius
    this.onEnterFrame = this.rotateMe;
}
```

这里我们所做的就是将传递给它的 radius 值存储为 radiusTarg，然后将 onEnterFrame 处理程序设置为 rotateMe。乍一看，存储 radius 似乎没有什么意义，因为这个值始终是一样的，但稍后当我们希望节点射出并形成其自身集群的中心时，我们会用到这个。我们可以重用已经编写的方法，只需提供不同的 radius 值即可。

现在，新节点将每帧调用 rotateMe。这是另一个简单的函数：

```
clusterNode.prototype.rotateMe = function() {
    if (this.moveToTarget(1)) {
        delete this.onEnterFrame;
    }
}
```

它基本上会调用 moveToTarget，直到节点达到目标弧度和半径值。该方法调用位于 if 语句中。这意味着，如果方法返回 true，则会执行 if 语句中的操作；否则不会执行。因此，当 moveToTarget 返回 true 时，onEnterFrame 处理程序将被删除，电影剪辑将停止移动。

你可能已经注意到，值 1 被传递给了 moveToTarget 方法。这个值用于容差。它表示电影剪辑在对齐到目标之前必须与目标的距离，达到该距离后方法才会返回 true。同样，这也是我们稍后会用到的东西，因为当集群关闭时所需的精度不如打开时高。

现在来看实际执行运动的方法：

```
clusterNode.prototype.moveToTarget = function(tolerance) {
    this.radian += (this.radianTarg - this.radian) / 3
    this.radius += (this.radiusTarg - this.radius) / 6

    this.xt = Math.cos(this.radian) * this.radius
    this.yt = Math.sin(this.radian) * this.radius

    this.x += (this.xt - this.x) / 6
    this.y += (this.yt - this.y) / 6
    this._x = Math.round(this.x)
    this._y = Math.round(this.y)

    if (Math.abs(this.xt - this.x) < tolerance && Math.abs(this.yt - this.y) < tolerance) {
        this.radian = this.radianTarg
        this.radius = this.radiusTarg
        this.x = Math.cos(this.radian) * this.radius
        this.y = Math.sin(this.radian) * this.radius
        this._x = Math.round(this.x)
        this._y = Math.round(this.y)
        return true
    }
}
```

你可以大致将此方法视为包含四个部分。首先，我们通过在节点的 `radian` 和半径值之间添加间隙的一小部分，将它们带向目标值。然后，我们基于这些值计算剪辑的 x 和 y 目标值。接下来，在同一部分中，我们将节点的 x 和 y 属性移向这些值。方法的最后一部分检查 x 和 y 值是否在 `xt` 和 `yt` 的容差范围内 – 如果是，则方法返回 `true`。

请注意，我们并不是直接使用 `_x` 和 `_y` 电影剪辑属性，而是使用 x 和 y，然后将 `_x` 和 `_y` 设置为这些属性的舍入值。这基本上是为了处理 Flash 在处理像素字体时的问题。如果包含文本字段的电影剪辑未放置在绝对像素上，字体会变得模糊，因此我们必须确保设置的 `_x` 和 `_y` 值是整数。你可以这样说，x 和 y 是每个节点的 **真实** 位置，而 `_x` 和 `_y` 是每个节点的 **呈现** 位置。

![](img/50202c17d5022233f3e3ec60560e35aa_129_0.png)

我们使用 Math.abs 将距离（可能是正数或负数）转换为正数（绝对值），以便进行正确的比较。还应该指出，通过修改此方法，我们也可以实现不同类型的运动。可以修改它，使节点以弹性方式移动到目标，或者使用从弧度和半径确定的值作为绘图点，而不是作为移动目标。此外，还可以让此方法接受额外参数，以在特定情况下更改运动速度。

如果你现在进行测试（它包含在下载文件中，文件名为 spinner002.fla），你应该会看到第一个节点的五个子节点从中心向外螺旋移动到位置，彼此之间有轻微的间隔。

![](img/50202c17d5022233f3e3ec60560e35aa_129_1.png)

![](img/50202c17d5022233f3e3ec60560e35aa_129_2.png)

下一阶段将是整理每个节点的图形，然后再进行交互元素的开发。

![](img/50202c17d5022233f3e3ec60560e35aa_129_3.png)

![](img/50202c17d5022233f3e3ec60560e35aa_129_4.png)

## 绘制节点图形

对于节点图形，我们将创建一个名为 bg 的新电影剪辑。我们可以使用绘图 API 来创建此图形，但我认为在创作环境中对图形进行更改并尝试各种效果通常更快。在 bg 中，我们将有三个独立的电影剪辑：left、right 和 mid。通过拉伸 mid 电影剪辑并将 right 电影剪辑定位在其右侧边缘，我们可以在不失真的情况下调整图形大小。

因此，我们有三个包含以下图形的新电影剪辑：

- left
  - 黑色矩形，1x19 px，左上角位于 0,0。
  - 黑色正方形，1x1 px，位于 1,0。
  - 浅绿色矩形 (#F1F4F0)，1x17 px，位于 1,1。
  - 黑色正方形，1x1 px，位于 1,18。

- right
  - 黑色矩形，1x19 px，左上角位于 1,0。
  - 黑色正方形，1x1 px，位于 0,0。
  - 中绿色矩形 (#CFDADC)，1x17 px，位于 0,1。
  - 黑色正方形，1x1 px，位于 0,18。

- mid
  - 黑色矩形，50x1 px，位于 0,0。
  - 浅绿色矩形 (#F1F4F0)，50x1 px，位于 0,1。
  - 白色矩形，50x15 px，位于 0,2。
  - 中绿色矩形 (#CFDADC)，50x1 px，位于 0,17。
  - 黑色矩形，50x1 px，位于 0,18。

![](img/50202c17d5022233f3e3ec60560e35aa_130_0.png)

将这三个电影剪辑放入 bg 中，并为它们指定实例名称 left、mid 和 right。如果你愿意，可以将它们紧密排列在 0,0 处，但因为我们将动态定位它们，所以这并不重要。

接下来，在 bg 内部添加另一个图层并创建一个文本字段，将其放置在 (0,0)。我使用了来自 minilm.com 的像素字体，设置为 8pt。如果你想使用设备字体，则应确保未嵌入字体轮廓（单击“字符”按钮，选择“仅为不存在的字符嵌入字体轮廓”），并将其设置为 9pt。嵌入的像素字体可能是最佳选择，因为使用设备字体时运动往往会稍微受影响。将字体设置为动态文本，并为其指定实例名称 tf。最后，将 bg 电影剪辑的实例放入 nodeSymbol 中，并将实例命名为 bg。

我们将创建一个新的 draw 方法，它将把类别名称放入文本字段，然后计算文本宽度以确定背景元素的大小和位置。draw 方法将从 init 方法中调用：

```
clusterNode.prototype.init = function() {
    this.catName = this.myObject.catName
    this.kidsArray = this.myObject.kidsArray
    this.segment = (2 * Math.PI) / this.kidsArray.length
    this.kidMCs = []
    this.draw()
}
```

这是 draw 方法，我稍后会逐节介绍：

```
clusterNode.prototype.draw = function() {
    this.bg.tf.autoSize = true
    this.bg.tf.text = this.catName
    var wid = this.bg.tf.textWidth + 10
    this.bg.tf._x = this.bg.left._width + 2
    this.bg.left._x = 0
    this.bg.left._y = 0
    this.bg.mid._x = this.bg.left._width
    this.bg.mid._y = 0
    this.bg.mid._width = wid - (this.bg.left._width + this.bg.right._width)
    this.bg.right._x = wid - this.bg.right._width
    this.bg.right._y = 0
    this.bg._x = Math.round(wid / 2) * -1
    this.bg._y = Math.round(this.bg.mid._height / 2) * -1
    this.bg.swapDepths(1000)
}
```

