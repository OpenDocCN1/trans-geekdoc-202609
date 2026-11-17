

希望你现在能明白，将每个叶子的所有数据存储在数组中，并将相同信息传递给自定义类，这样我们就可以通过向leafMap数组添加更多信息，轻松创建每个具有独特属性的叶子新实例。为每个叶子添加新属性也只需修改类构造函数中几行代码。

要完成这部分代码，我们现在回过头来查看Leaf类构造函数的内部，看看它是如何工作的。这很简单。查看我们传入构造函数的第一个参数name，当我们创建Leaf对象实例时，我们通过类似以下方式为其赋予一个名为name的属性，并赋予唯一值：

```
this.name = name;
```

上述代码行的作用是：告诉Leaf对象实例为我（this——指当前实例）创建一个名为name的属性，并将其值设置为在创建实例时传入Leaf类构造函数的name参数。基于这一原理，Leaf类构造函数内部的其余代码应该非常容易理解和跟随。

请注意，我们还可以根据传入的各个参数通过数学计算来定义属性，例如：

```
this.stopX = stopX - plantSize;
```

稍后你会看到，我们将使用stopX属性来帮助确定每个叶子的大小。我们还会递增变量plantSize的值，这样当我们反复调用名为drawLeaf的函数时，植物就会增大，从而呈现出动画效果。

我要在Leaf类构造函数中讨论的最后一段代码是如下所示的代码：

```
this.ID = setInterval(drawLeaf, 10,
this.name, this.dir, this.levelNum,
this.originX, this.originY, this.stopX,
this.stopY, this.controlX,
this.controlY, this.thickness);
```

在setInterval函数的所有参数前都可以不指定this，但这样做可能会帮助你记住，这些属性现在实际上属于我们创建的Leaf对象实例，同时也表明setInterval函数内部的参数集在顺序和值上与我们最初传入Leaf类构造函数的参数略有不同。

上述代码行的作用是什么？它会创建一个setInterval动作，进而执行我们在setInterval参数中定义的函数，并且每隔x毫秒执行一次。

请记住，我们植物上的每个叶子实例都是调用Leaf类构造函数时创建的对象。我们可以看到，对于每个叶子实例，我们都会创建一个名为ID的属性，该属性的值是一个setInterval动作，它每隔10毫秒执行一次名为drawLeaf的函数，并向该函数传递一大堆参数。轻而易举！以这种方式使用setInterval的原因是，通过为其赋予名称或标识符，我们在不再需要它时可以将其销毁或停止。

我在这里使用setInterval而不是onEnterFrame，因为使用onEnterFrame方法时，你无法准确控制函数每次被调用的时间，并且在不再需要时也不总能轻松删除onEnterFrame动作。出于这些原因，使用setInterval可以节省处理器占用，确保代码尽可能流畅地运行。

接下来的大段代码就是实际在植物上绘制每个叶子的地方。我们知道我们现在有七个名为leaf0obj、leaf1obj，一直到leaf6obj的Leaf对象实例。这些实例中的每一个都具有一组属性（name、dir、levelNum等等），值在每个实例中都是唯一的。我们将在名为drawLeaf的函数中读取这些属性的值，以实际绘制每个叶子。

但我们不是直接深入drawLeaf函数，希望从相当复杂的代码中勉强看出些门道，我想我们先从植物电影中休息几分钟，制作另一个FLA文件，它将有两个用途：

- 演示我们使用绘图API制作叶子的简化版本。
- 制作一个小型应用程序，它将自动生成构成我们leafMap父数组中每个子数组的参数。

你难道真的认为我是一笔一划手动计算出所有这些数字的吗？

![](img/50202c17d5022233f3e3ec60560e35aa_174_0.png)

## 小型应用程序中的绘图API

我们现在将暂时离开植物，制作我们的小型应用程序来生成存储每个叶子数据的子数组，并了解绘图API的工作原理。从下载文件中打开名为leafmaker.fla的文件。在主时间轴的舞台上，你会看到三个颜色分别为红色、黄色和绿色的小电影剪辑——红色代表曲线的终止点，绿色代表起始点，黄色代表曲线的控制点。

函数内的第一行代码会在主时间轴的层级1上创建一个名为arc的空电影剪辑，这样我们就可以使用绘图API在其中绘制。要在Flash中使用ActionScript绘制任何东西，你都必须提供一个供Flash绘制的电影剪辑，而一个专门为此目的创建的空电影剪辑通常被认为是最佳实践。当你创建一个空电影剪辑时，其x和y会相对于其所在的时间轴设置为0,0。在我们的情况中，空电影剪辑所在的时间轴是_root，因此该电影剪辑也将位于主舞台的0,0处。

每个电影剪辑及其中按钮上的代码都相当基础，你应该很熟悉。简单来说，每个电影剪辑按钮内的代码就是：按下时拖动电影剪辑并通过setInterval动作运行drawCurve函数，释放时停止拖动动作。我们还确保每个电影剪辑在释放时位于整数像素上，只是为了让我们的数组输出看起来更整洁。leafmaker.fla内名为drawCurve的函数如下：

```
function drawCurve() {
_root.createEmptyMovieClip("arc", 1);
thickness = 10;
with (_root) {
beginFill(0x33CC00, 60);
lineStyle(1, 0x000000, 100);
moveTo(_root.startMov.x, _root.startMov.y);
curveTo(_root.ctrlMov.x,
_root.ctrlMov.y, _root.endMov.x,
_root.endMov.y);
curveTo( (_root.startMov.x-thickness),
(_root.startMov.y-(100+thickness)),
(_root.startMov.x), (_root.startMov.y));
endFill();
}
_root.myData = _root.leafName + "," +
_root.leafDir + "," + _root.leafNum + "," +
_root.startMov.x + "," + _root.startMov.y +
"," + _root.endMov.x + "," +
_root.endMov.y + "," + _root.ctrlMov.x +
"," + _root.ctrlMov.y + "," +
_root.thickness;
}
```

使用with动作（类似于旧的tellTarget动作），我们告诉_root.arc电影剪辑，我们将绘制一条宽度为1像素、颜色为黑色（0x000000是Flash表示#000000（黑色的十六进制值）的方式）的线条，且线条的alpha值为100%。然后我们告诉电影剪辑使用beginFill开始为叶子上色，指定填充的颜色和alpha值。

然后我们告诉绘图API从特定位置开始（相对于正在绘制的电影剪辑的0,0），方法是让它移动到舞台上绿色电影剪辑的x和y位置。

然后我们实际绘制第一条曲线。由于我们已经使用moveTo动作指定了绘制线条的起始位置，现在我们将使用curveTo动作中的前两个参数作为控制点，绘制一条曲线到最后两个参数指定的点。

