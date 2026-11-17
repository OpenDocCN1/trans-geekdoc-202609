

this.render();
}
```

render 是我们将要创建的下一个方法，它将根据节点的3D坐标正确定位和缩放我们的节点。现在让我们编写该函数，以便测试我们的电影。

将此方法直接放在 init 方法之后：

```
NodeClass.prototype.render = function() {
	var depthFactor = this.focalLength/
		(this.focalLength - this.z);
	this.x = this.x * depthFactor;
	this.y = this.y * depthFactor;
	this.xscale = this.yscale = this.z *
		depthFactor * scaleFactor + 100;
}
```

或许您会很高兴地知道，这就是本项目中涉及的3D计算的全部范围。我们没有时间深入探讨这里正在发生的事情，如果您在 Flash 中使用过任何3D，您可能已经遇到过类似的方法。只需说，这是一个将我们的3D坐标（x, y, z）转换为屏幕上2D坐标的方法。我们通过缩放电影剪辑并根据z 3D属性和 focalLength 调整 _x 和 _y 2D属性来模拟2D屏幕上的深度。使用这个我称为 depthFactor 的值，我们设置了剪辑的 _x、_y、_xscale 和 _yscale 属性，使z轴上更近的剪辑看起来更大，并且离3D消失点（0, 0, 0）更远。缩放本身由 z 值乘以 depthFactor 决定。添加 100 是为了将缩放提升到可工作的范围（因为我们处理的是负z深度）。scaleFactor 是我添加的，为了在如何显示节点方面多提供一点自由度（我们在代码顶部的代码图层上设置了这个变量）。

这是我们让 NodeClass 最初工作所需要的最后一行：

```
Object.registerClass("nodeSymbol",
	NodeClass);
```

registerClass 将库中的电影剪辑符号与代码中的类定义关联起来。如果您访问库中 nodeSymbol 的链接属性，您会看到我已经将其设置为导出为 nodeSymbol。有了上面的 registerClass 行，我们附加到舞台上的任何 nodeSymbol 都将自动成为我们 NodeClass 的实例。

好了！测试您的电影。您应该看到我们的第一个节点出现，一切就绪！虽然这可能看起来是为单个节点做了大量准备，但整棵树的基础工作已经完成。现在让树做一些非常酷的事情只需小步骤！

![](img/50202c17d5022233f3e3ec60560e35aa_96_0.png)

## 显示子节点

我们将要处理的下一部分是每当点击节点时显示其子节点。我们将创建几个新方法来处理这个功能。首先要考虑的是当点击节点时我们希望发生什么。除了仅显示节点的子节点之外，我们还需要让选定的节点移动到舞台中央。让我们先写那个方法。

将此方法直接放在 render 方法之后（确保它在 Object.registerClass 行之上，该行应始终保持为 NodeClass 代码中的最后一行）：

```javascript
NodeClass.prototype.center = function() {
    clearInterval(translateInt);
    this.showChildren();
    this._parent.tNodes = [];
    var x = -this.tX;
    var y = -this.tY;
    var z = -this.tZ;
    var i = 0;
    while (i < this._parent.nodes.length) {
        this._parent.nodes[i].setTranslate(x, y, z);
        i++;
    }
    translateInt = setInterval(this._parent,
        "translate", intervalTime);
}
```

此方法引入了一些我们稍后将要介绍的新项目。暂时跳过方法中的第一行代码，请注意我们正在调用一个名为 showChildren 的新方法，它将负责添加子节点所需的节点。然后我们在 _parent（树）时间轴上创建一个名为 tNodes 的新数组，用于存储我们需要转换的所有节点的引用。接下来的三行创建三个变量，用于存储此节点需要移动到（0, 0, 0）所需的距离。tX、tY 和 tZ 最终将保存转换后的坐标，即节点移动后的结束位置。如果节点位于（100, 100, -100），那么它需要在x轴上移动负100，在y轴上移动负100，并在z轴上移动正100才能到达（0, 0, 0）。这就是我们在 x、y 和 z 变量中存储的内容。现在，如果每个节点保持与其他每个节点的相同关系，那么每个节点将需要在每个轴上移动相同的距离。

在确定了这些值之后，我们为每个节点调用另一个名为 setTranslate 的新方法。使用while循环（比for循环稍快），我们遍历 _parent 的节点数组，该数组存储了所有节点的引用（我们在 init 方法中处理了此问题），并让每个节点设置其自身的转换。在接下来的一行中，我们使用 setInterval 在树时间轴上调用 translate 方法（我们尚未编写）。translate 是在每个间隔移动节点的方法。

让我们快速看一下 center 中刚刚调用的方法，以便您可以看到它们如何协同工作。

第一个要添加的方法是 NodeClass 的 setTranslate。在 center 方法之后添加这些行：

```javascript
NodeClass.prototype.setTranslate =
  function(x, y, z) {
      this.tX += x;
      this.tY += y;
      this.tZ += z;
      if (this.tZ > this.yon || this.tZ <
      this.hither) {
          this.x = this.tX;
          this.y = this.tY;
          this.z = this.tZ;
          this.render();
      } else {
          this._parent.tNodes.push(this)
      }
  }
```

setTranslate，就像我们在 center 方法中看到的那样，当树需要转换时会为每个节点调用。我们向此方法发送节点需要移动的 x、y 和 z 距离，并将其添加到节点当前的转换位置上。接下来的语句确保我们是否真的需要执行移动动画。基本上，我们测试该节点的结束 z 位置是否会超出我们指定的渲染范围（由 hither 和 yon 决定）。如果不在范围内，我们将 x、y 和 z 坐标设置为等于我们的转换坐标，并在最终位置渲染该节点（稍后，我们将添加一个可见性检查来关闭此节点，因为它不在范围内）。如果节点的 z 位置在渲染范围内，我们只需将节点引用推入 _parent 时间轴的 tNodes 数组，该数组将保存所有需要转换的节点。现在让我们处理那个方法。

对于这些行，您需要返回代码图层，因为它们不是 NodeClass 代码的一部分。在行 tree.depth = 15000; 之后放置此方法：

```
tree.translate = function() {
    var i = 0;
    while (i < this.tNodes.length) {
        this.tNodes[i].translate();
        this.tNodes[i].render();
        i++;
    }
    if (this.tNodes.length < 1) {
        clearInterval(translateInt);
    }
}
```

这部分非常不言自明。每次调用此函数时（由我们的 setInterval 决定），tree 会遍历其节点列表并告诉每个节点转换和渲染自身。节点一旦到达目的地，就会从 tNodes 数组中单独移除自身。一旦数组为空，我们就清除间隔，因为该函数不再需要被调用。

好了！要实现转换，还需要介绍一个方法。返回 NodeClass 图层，并在 setTranslate 方法之后放置这个新方法：

```
NodeClass.prototype.translate = function() {
    this.x -= (this.x - this.tX)/intervals;
    this.y -= (this.y - this.tY)/intervals;
    this.z -= (this.z - this.tZ)/intervals;
    if (Math.abs(this.x - this.tX) < 1 &&
        Math.abs(this.y - this.tY) < 1 &&
        Math.abs(this.z - this.tZ) < 1) {
        var i = 0;
        while (i < this._parent.tNodes.length) {
            if (this._parent.tNodes[i] == this) {
                this._parent.tNodes.splice(i, 1);
                break;
            }
            i++;
        }
    }
    this.x = this.tX;
    this.y = this.tY;
    this.z = this.tZ;
}
```

这里是我们的缓动动画代码。每次调用 translate 时，节点会在每个轴上移动一小段需要移动的距离。if 条件语句用于确定当前坐标是否足够接近结束坐标。当达到该点时，我们使用 while 循环查找节点在其 _parent.tNodes 数组中的位置。一旦找到，它就移除自身，并将当前坐标设置为等于结束转换坐标。如果您回头查看 tree 的 translate 方法，您会看到接下来发生的事情是渲染节点。之后，由于节点已从 tNodes 中移除，它就完成了转换。

这应该就处理了转换，但附加子节点呢？好吧，这就是本节中最后一个方法所做的。

