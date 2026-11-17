
距离是勾股定理在起作用，并根据我们节点的当前比例进行了调整。老实说，减去四分之一的半径是我偶然发现的一个值，结果完美奏效。我花了大量时间绞尽脑汁想弄明白原因，以便能向你解释，但有时你该庆幸自己的运气，用“因为它就是有效”来回答“为什么这有效？”这个问题。

不过，接下来的两行代码可以解释。我们清除连接器之前的绘图，并将“笔”移动到起始的x和y位置。

这两行代码有助于确定我们绘图的高度，我们将在渐变参数中用到它。请将这些行直接放在前面的代码之后：

```
y = -(distance + this.connY1);
var gradientHeight = y - this.connY1;
```

我们第二个y位置是通过将距离加到初始y位置来确定的。我们也将此值设为负，因为连接器的第二个角在第一个角的上方。

gradientHeight然后很容易通过计算第一个和第二个y值的差来得到。这将是渐变的总高度。

现在让我们使用以下代码创建渐变，该代码应紧跟在前面的行之后：

```
var colors = [this.node.col.connector,
this.parent.node.col.connector];
var alphas = [100, 100];
var ratios = [70, 220];
var matrix = {matrixType:"box",
x:this.connX1, y:this.connY1, w:50,
h:gradientHeight, r:pi/2};
```

```
this.connector.beginGradientFill("linear",
colors, alphas, ratios, matrix);
```

beginGradientFill接受若干参数。首先，我们发送渐变类型，在本例中为"linear"（你也可以使用"radial"）。接下来，我们发送三个值数组。colors数组保存我们节点和父节点的颜色，alphas数组保存每种颜色的不透明度。ratios数组是渐变中每个指定颜色达到100%的位置。这些值将在0到255之间（十六进制百分比）。我将节点颜色的值设置为在70处为100%，父节点颜色在220处为100%。这意味着渐变实际上只会在这两个值之间发生，这接近连接器的中间位置。

最后，matrix是一个包含我们需要传递给beginGradientFill方法的若干属性的对象。对于这种渐变方法，matrixType将始终是box（创建渐变的替代方法将是另一回事了），x和y是相对于电影剪辑注册点的渐变起点（我们将其设置为连接器的第一个角），w和h是我们渐变的宽度和高度（宽度对我们要创建的线性渐变影响不大），而r是我们希望旋转渐变的弧度，我将其设置为90度以将渐变转向侧面。

哇！这真是个方法！但等一切结束后，我们会得到一个绝佳的效果。说到结束，让我们完成这个drawConnector方法，这样我们就能看到它了！

最后几行绘制连接器的两侧：

```
this.connector.curveTo(-10, -distance*.5,
this.connX1, y);
this.connector.lineTo(this.connX2, y);
this.connector.curveTo(10, -distance*.5, this.connX2, this.connY2);
this.connector.endFill();
}
```

curveTo命令接受四个参数。最后两个参数是我们正在绘制到的实际坐标，你可以看到我们已经用connX1、connX2、connY2和y变量确定了它们。前两个参数是线条弯曲方向的坐标。在本例中，我们选择连接器中间位置的y坐标和与曲线相反中心一侧的x坐标，从而获得一个很好的凹形。

![](img/50202c17d5022233f3e3ec60560e35aa_104_0.png)

测试你的电影以查看我们制作的内容。有趣！

你可能会注意到从我们的rootNode Chaos伸出一个不需要的连接器。问题是，它没有可以连接的节点（可怜的Chaos！），所以我们需要确保它不会尝试。我们可以在init方法中非常快速地修复它。

将以下行添加到我们NodeClass的init方法中：

```
if (this._name == "rootNode") {
    this.render();
    return;
}

this.createEmptyMovieClip("connector", 1);
this.connX1 = connectorCos1 * this.radius;
this.connY1 = connectorSin1 * this.radius;
this.connX2 = connectorCos2 * this.radius;
this.connY2 = connectorSin2 * this.radius;
```

在这里，我们在添加连接器电影剪辑之前只是进行了一个快速检查。如果节点是rootNode，它会自行渲染并退出方法。

不过，即使rootNode没有连接器电影剪辑，它仍然会不必要地运行drawConnector代码，所以让我们在drawConnector方法中再添加一行：

```
NodeClass.prototype.drawConnector =
    function() {
    if (this._name == "rootNode") { return
    false };
    var x = this._x - this.parent._x;
    var y = this._y - this.parent._y;
```

现在rootNode会立即离开此函数而不运行代码。测试你的电影以查看所有效果。

![](img/50202c17d5022233f3e3ec60560e35aa_104_1.png)

## 一次一条分支

如果你稍微玩过一下，可能会注意到在舞台上放置的节点越多，系统运行就越慢。除此之外，当分支开始变得茂密时，有些节点可能会遮挡其他节点。为了解决这个问题，我决定删除被点击节点的任何“侄女”和“侄子”。这样，你就能看到直接血统，但看不到兄弟节点的子节点。我还觉得这可能会加快运行速度（Flash不喜欢舞台上同时移动太多电影剪辑）。

![](img/50202c17d5022233f3e3ec60560e35aa_105_0.png)

我们将向NodeClass添加另一个方法，以协助实现此额外功能。让我们将此新方法的调用放在center方法内。由于额外节点是在那里作为子节点添加的，因此在那里删除不必要的节点是有道理的：

```javascript
NodeClass.prototype.center = function() {
    clearInterval(translateInt);
    this.parent.removeSiblings(this);
    this.showChildren();
};
```

因此，一个节点实际上会告诉其父节点删除其兄弟节点的子节点，这很合理，因为一个节点实际上对其兄弟节点没有直接了解。让我们编写`removeSiblings`方法，看看我们如何实现这一点。

在`NodeClass`的`showChildren`方法之后，添加以下新代码行：

```javascript
NodeClass.prototype.removeSiblings =
function(skip) {
    var i = 0;
    while (i < this.children.length) {
    if (this.children[i] != skip) {
    this.children[i].collapseChildren()
    }
    i++;
    }
}
```

`removeSiblings`让父节点遍历其子节点数组（跳过调用该方法的子节点）。如果一个子节点拥有自己的`children`数组，这意味着子节点当前位于舞台上。它通过调用子节点的`collapseChildren`方法来告诉子节点删除这些子节点，我们现在就来编写该方法。

将此新方法放在我们的`removeSiblings`方法之前：

```javascript
NodeClass.prototype.collapseChildren =
function() {
    var i = 0;
    while (i < this.children.length) {
    if (this.children[i].children != undefined) {
    this.children[i].collapseChildren()
    }
    this.children[i].removeNode();
    i++;
    }
    delete this.children;
}
```

这是我们在前一个方法中调用的函数，用于删除节点的子节点。你可以看到，它遍历其子节点数组并调用removeNode方法（如果子节点本身有子节点，则也会删除那些子节点）。一旦所有子节点都被删除，子节点数组就会被删除，从而为如果节点被点击时重新附加子节点腾出空间。

剩下要编写的唯一东西是我们刚才调用的removeNode方法。将它放在removeSiblings方法之后：

```
NodeClass.prototype.removeNode = function() {
    var i = 0;
    while (i < this._parent.nodes.length) {
    if (this._parent.nodes[i] == this) {
    this._parent.nodes.splice(i, 1);
    break;
    }
    i++
    }
    this.removeMovieClip();
}
```

这个方法所做的只是遍历树的节点数组以查找自身引用。一旦找到，它就删除该引用，并使用removeMovieClip将自身从舞台上删除。就这些。

现在测试你的电影，看看删除兄弟节点的子节点有什么帮助。

![](img/50202c17d5022233f3e3ec60560e35aa_106_0.png)

## 旋转树

我们现在已经有一个相当不错的系统了。不过，不知足的我想给我们的树添加旋转功能。幸运的是，由于我们设置的方式，这相当容易。不需要使用任何3D旋转数学或变换矩阵——每个节点都包含在一个电影剪辑内，这意味着我们只需旋转树剪辑（谢天谢地！）。由于其注册点位于视图窗口中心（即点击节点正在前往的位置），树看起来将围绕节点旋转。

首先，我们需要决定在哪里调用旋转代码。将它添加到NodeClass内的center方法中是有道理的，因为当节点被点击时，旋转就需要从这里开始。下面是修改后的方法：

```
NodeClass.prototype.center = function() {
    clearInterval(translateInt);
    clearInterval(rotateInt);
    this.parent.removeSiblings(this);
    this.showChildren();
    this._parent.tNodes = [];
    var x = -this.tx;
    var y = -this.ty;
    var z = -this.tZ;
    var i = 0;
    while (i < this._parent.nodes.length) {
    this._parent.nodes[i].setTranslate(x, y, z);
    i++;
    }
    translateInt = setInterval(this.parent, "translate", intervalTime);
    this.parent.startRotate(-this.angle);
}
```

开始时很简单，对吧？在顶部，如果正在发生旋转，我们会清除任何间隔（请记住它将被命名为rotateInt）。在底部，我们告诉_parent（树）进行旋转，并发送此节点angle属性的负值，这基本上是树需要逆向旋转的角度。
