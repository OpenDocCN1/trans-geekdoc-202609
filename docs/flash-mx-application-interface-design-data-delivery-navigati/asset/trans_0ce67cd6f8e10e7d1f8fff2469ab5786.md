
这条线每一帧都会被重新绘制，我们从起始点到鼠标移动到的任何位置都能得到一条漂亮平滑的线。

当我们释放鼠标时，会执行一组类似的操作，但我们是绘制到 drawPad 而不是 tempLayer。首先，我们清空 tempLayer 以删除之前使用的临时线：

```
drawPad.onRelease = drawPad.onReleaseOutside = function () {
    tempLayer.clear();
};
```

然后我们设置 drawPad 的 lineStyle，并从原始起始点绘制一条线到最后的鼠标位置。我们还将 _root.onEnterFrame 处理程序设置为 undefined，因为在下次单击鼠标之前我们已经用不着它了。

```
drawPad.lineStyle(_root.mainButBrushSize.bSize, _root.col, _root.mainButBrushAlpha.bAlpha);
drawPad.moveTo(_root.startX, _root.startY);
drawPad.lineTo(_root.xM, _root.yM);
_root.onEnterFrame = undefined;
```

线条工具就这么多。它很简单，但你可以用它创造出一些很棒的效果：

![](img/50202c17d5022233f3e3ec60560e35aa_201_0.png)

![](img/50202c17d5022233f3e3ec60560e35aa_201_1.png)

![](img/50202c17d5022233f3e3ec60560e35aa_201_2.png)

![](img/50202c17d5022233f3e3ec60560e35aa_201_3.png)

![](img/50202c17d5022233f3e3ec60560e35aa_201_4.png)

![](img/50202c17d5022233f3e3ec60560e35aa_201_5.png)

## 曲线工具

![](img/50202c17d5022233f3e3ec60560e35aa_202_0.png)

曲线工具比其他绘图工具稍微复杂一些，但仍然相当直观。实际的绘图方法与线条工具类似，即我们先在同一个临时图层上绘制，完成后再将其固定到 drawPad。主要区别在于 Flash 中绘制曲线的方式。对于直线，我们只有两个点，即起点和终点；但对于曲线，我们有三个点，即起始锚点、结束锚点和控制点。Flash 使用 Bezier 绘图系统，但为了便于理解，我们可以将其替换为轨迹比喻。

那么，这只鸟就是我们的控制点。每当它移动并再次开始叫唤时，你就再扔一个球，磁铁把它吸引过去，曲线的形状也随之改变。如我所说，这并不完全是 Flash 中发生的情况，但这应该能让你更好地理解曲线为何呈现这样的形状。真正理解它的最好方法就是运行程序并亲自尝试一下。

好了，理论部分讲完了，现在进入代码部分。我们要做的第一件事是定义几个函数，但我将按照事情发生的顺序来解释，而不是按照代码顺序，请见谅。当你单击曲线工具按钮时，首先发生的事情是系统要求你单击三个点，以设置锚点和控制点的初始位置。

想象一下，你站在一个大田野里，身边堆着无限多的金属球。大约在你 20 英尺远的地方有一个大而强大的磁铁，每当你扔出一个球，它就会被吸到磁铁上。你和磁铁代表曲线的锚点，而你扔出球时的轨迹描述了曲线的形状。现在，为了让这个例子更加离奇，想象空中有一只烦人的鸟在盘旋并对你叫唤。你以完美的力度和精度扔出一个球想击中鸟，但球还没到那里，磁铁就把球拉回了地面：

库中有三个电影剪辑，其链接名称分别为 a1、a2 和 ctrl——这些简单的圆圈将代表我们的锚点和控制点。我们首先将 clickedPoints 变量初始化为 0，然后在 drawPad 上设置一个 onRelease 处理程序。接着，我们通过一系列简单的 if 语句来检查我们是第一次、第二次还是第三次单击。针对每次单击采取的操作都非常相似，因此我只讲解第一次：

```
if (clickedPoints == 0) {
  _root.attachMovie("a1", "a1", 22220);
  _root.a1._x = _xmouse;
  _root.a1._y = _ymouse;
  clickedPoints++;
}
```

在这里，我们从库中附加相应的剪辑并设置其深度级别。然后我们根据鼠标位置对其定位，并递增 clickedPoints 变量以进入下一个。

接下来，我们在 tempLayer 上绘制初始调用，并更改帮助文本以说明下一步该做什么：

```
drawCurve.call(tempLayer, a1, ctrl, a2);
_root.help.text = "Drag green anchor
points to position curve, then drag and
release control point to fix curve and
color";
```

最后，我们再次递增 clickedPoints，这样我们在单击时就不会再创建任何圆圈了，并将 previewCurve 函数附加到每个电影剪辑上：

```
clickedPoints++;
previewCurve.call(_root.a1);
previewCurve.call(_root.a2);
previewCurve.call(_root.ctrl);
};
```

好了，所有的初始化工作都完成了——现在我们进入每帧更新预览曲线的阶段。这段代码大部分与线条工具代码相似，因此我将跳过其中一些部分，专注于发生变化的部分。我们将锚点设置为可拖动，但限制在方形绘图板内：

```
previewCurve = function () {
    this.onPress = function() {
        tempLayer.clear();
        if (this != ctrl) {
            this.startDrag(true, tabletleft,
            tablettop, tabletright,
            tablebottom);
        }
    }
}
```

不过控制点略有不同：

```
else {
    this.startDrag(true);
}
```

如果我们将其限制在方形内，你就无法绘制非常大的曲线了。为了解决这个问题，我们将允许控制点在舞台上的任何位置拖动。曲线本身仍将在方形内遮罩，以免其散落在界面各处，但现在你可以对曲线的形状有更多控制。稍后我们将说明释放时会发生什么。

不过首先，我们将在根上设置一个 onEnterFrame 处理程序来每帧重绘曲线：

```
_root.onEnterFrame = function() {
    tempLayer.clear();
    tempLayer.lineStyle(_root.mainButBrushSize.bSize, 0x000000, 100);
    _root.point1x = _root.a1._x;
    _root.point1y = _root.a1._y;
    tempLayer.moveTo(_root.point1x,
    _root.point1y);
    tempLayer.curveTo(_root.ctrl._x,
    _root.ctrl._y, _root.a2._x, _root.a2._y);
};
```

这段代码与我们用于线条工具的代码相同，唯一的区别是我们使用 curveTo 而不是 lineTo，并向其提供额外的一组坐标。我们将预览曲线始终设置为黑色且 100% 透明度，以便你能清楚地看到你正在绘制的曲线形状。

当我们释放鼠标时，我们还希望对各个点采取不同的操作。锚点将仅停止拖动，因为它们已经被限制在方形内，但控制点有一些额外的代码：

```
this.onRelease = this.onReleaseOutside = function () {
    this.stopDrag();
    if (this == ctrl) {
        drawCurve.call(drawPad, a1, ctrl, a2);
        tempLayer.clear();
        if (_root.ctrl._x > tabletright) {
            _root.ctrl._x = tabletright;
        }
        if (_root.ctrl._x < tabletleft) {
            _root.ctrl._x = tabletleft;
        }
        if (_root.ctrl._y < tablettop) {
            _root.ctrl._y = tablettop;
        }
        if (_root.ctrl._y > tabletbottom) {
            _root.ctrl._y = tabletbottom;
        }
    }
    _root.onEnterFrame = undefined;
};
```

```
drawCurve = function (clip1, control, clip2) {
    this.lineStyle(
    _root.mainButBrushSize.bSize,
    _root.col,
    _root.mainButBrushAlpha.bAlpha);
    this.moveTo(clip1._x, clip1._y);
    this.curveTo(control._x, control._y,
    clip2._x, clip2._y);
};
```

Flash 曲线绘图引擎中存在一个故障，你可能不时会遇到。如果锚点和控制点都在一条直线上，且两个锚点都在同一侧，那么绘制的线条通常会变得有点奇怪，如下图所示：

![](img/50202c17d5022233f3e3ec60560e35aa_204_0.png)

当我们释放控制点时，我们首先将曲线固定到 drawPad 并清空 tempLayer，但接着我们将电影剪辑的位置吸附回方形内部。我们做到这一点的方法是，简单地检查控制点在每个轴上是否超出方形范围，如果是，则将其设回方形边缘。最后，我们取消定义根的 onEnterFrame 处理程序。

不过，这通常不应该是什么大问题，因为你通常会使用线条工具绘制直线，而不是曲线工具。

曲线工具最后要解释的函数是实际的 drawCurve 函数。这个函数非常简单，只需获取三个点的位置，并在它们之间绘制曲线，并在绘制过程中将其设置为正确的 lineStyle：
