

onEnterFrame 回调函数使用描述圆上点的公式在舞台上绘制大小标签的位置。公式是：

```
X position = Xposition of center point + Math.cos(degrees / 180 * Math.PI) * radius;
Y position = Yposition of center point + Math.sin(degrees / 180 * Math.PI) * radius;
```

接下来的条件语句检查名为 count 的变量是否已达到 _root.size 值的 10 倍。如果是，则围绕圆形路径的大小标签动画停止 – 因此它最终移动的距离取决于 _root.size 的值。每过一帧，标签就会沿圆形路径移动 7 度，并且变量 count 加 1。

此代码块中的接下来几行代码负责渲染指向大小标签的表盘“指针”。在名为 indial 的新建电影剪辑内，从中心点向外绘制一条 1 像素粗的线，指向与大小标签相对应的位置 – 最终结果是一个指向大小标签的动画指针。

行 `_root.sizelabel.insidesize.text = _root.size;` 使用 _root.size 的值填充文本字段 – 该值来自我们的维度数组，稍后将会看到。此代码块中的最后一行代码将文本字段设置为我们先前定义的 Tformat 文本格式。

## 第 2 帧

如果第 1 帧主要用于为生成界面做准备，那么第 2 帧则是实际生成完成的部分。在第 2 帧中的命令执行之前，屏幕上看不到任何内容。

第一个代码块指示 Flash 绘制一个舞台大小的矩形，并用深红色渐变填充它 – 这将为我们的界面提供背景。我们再次充分利用了绘图 API：

```
_root.createEmptyMovieClip("background", -2000);
with (_root.background) {
colors = [0xD83D3D, 0x990000];
alphas = [100, 100];
ratios = [0, 0xFF];
matrix = {matrixType:"box", x:100, y:100, w:200, h:200, r:(90/180)*Math.PI};
beginGradientFill("linear", colors, alphas, ratios, matrix);
moveTo(0, 0);
lineTo(660, 0);
lineTo(660, 400);
lineTo(0, 400);
lineTo(0, 0);
endFill();
}
```

首先我们在深度 -2000 处创建一个名为 background 的空电影剪辑，以确保稍后生成的任何内容都不会出现在其下方，然后我们定义四个数组，它们是应用于背景电影剪辑的 beginGradientFill 方法的默认参数。按顺序，这些数组为：

- 颜色数组 – 渐变经过的两种颜色
- 透明度数组 – 定义两种颜色的 alpha 值
- 比率数组 – 包含颜色分布
- 矩阵数组 – 包含字符串标识符、x 和 y 位置、宽度和高度以及渐变的相对旋转。

请注意，矩阵数组的最后一个元素（即旋转）是以弧度为单位的，因此我们必须除以 180 并乘以 PI，以便从更广泛理解的角度单位转换过来。

beginGradientFill 方法指示 Flash 开始填充该方法调用后出现的任何形状所围成的区域。该方法总共使用 5 个参数：一个表示渐变类型（线性或径向）的字符串，以及我们刚刚讨论的其他四个数组。然后使用 moveTo 和 lineTo 方法及舞台大小绘制一个矩形。渐变填充使用 endFill 终止。

好吧，这个深红色渐变本可以使用创作环境中的绘图工具制作，并转换为符号放置在舞台上。也许更简单、更快，没错，但使用 API 版本的好处在于，当用户与界面交互时，我们可以以多种方式动态更改渐变。也许我们希望用户做出新选择时更改渐变颜色？我们只需向颜色数组引入一个动态变量，这总比生成，比如说，十个渐变符号（每个选择一个）要好。事实上，这是使用 API 动态生成整个界面的重要原因之一。它使添加由几个变量控制的动态元素变得非常容易，而这些变量又受用户选择的影响。没有任何理由认为整个界面不能以这种方式构建，其中所有元素的属性都受用户交互影响。这样一来，我们就拥有一种变色龙界面，它在导航过程中会变形，希望能够吸引用户，因为他正直接参与界面的结构与重构。

第 2 帧中的以下代码行创建了一个名为 dial 的空电影剪辑，准备承载表盘系统：

```
_root.createEmptyMovieClip('dial', -88);
_root.dial._visible = false;
_root.size = "";
```

![](img/50202c17d5022233f3e3ec60560e35aa_44_0.png)

新创建剪辑的可见性设置为 false。代码块中的最后一行将变量 _root.size 设置为空字符串。

序列中的下一个代码块开始实际以螺旋形状生成按钮：

```
for (i=0; i<link.length; i++) {
	_root.createEmptyMovieClip('mc'+i, i);
	with (_root['mc'+i]) {
	drawShape(i*1.4, 0, 5+i/1.5, 1,
	0xffffff, 0x666699*i/kolor, pha,
	cshape, dshape);
	drawShape(i*1.4, 0, 2+i/4.5, 1,
	0xffffff, 0x999900*i/5, pha,
	cshape, dshape);
	_x = 375;
	_y = 20+i*13;
	_rotation = i*rota;
	_alpha = 80;
	}
}
```

首先，我们设置了一个 for 循环，循环次数等于 link 数组中第一级数组的数量。length 是数组的一个属性，返回数组中的元素数量，在此例中为 26。因此，我们将有 26 个按钮，每个按钮对应一个第二级数组，包含我们所有的螺旋数据。

下一行代码创建一个空电影剪辑作为生成按钮的容器。使用 with 语句，避免为每个应用的方法重写对象的完整路径，我们指示 Flash 调用两次 drawShape 方法，在新建的空“电影剪辑”中绘制两个同心图形（在此例中结果呈花形）。传递给原型函数的参数之前已讨论过 – 在这里，圆圈的大小、填充颜色和相对位置取决于 mc 生成序列的位置，即变量 i 的一个因子。按钮的 alpha 值取决于 pha 的值。这些按钮的最终形状也取决于变量 cshape 和 dshape。要绘制完美圆形，这两个变量的值应分别为 0.4086 和 0.7071。还值得指出的是，除了取决于 i 的因子外，第一个图形或圆圈的填充颜色还取决于变量 kolor。四个变量 cshape、dshape、pha 和 kolor 是左下角一排按钮用于重新配置界面外观的变量 – 但我们稍后会详细说明。

此代码块中的最后四行代码沿 x 和 y 轴定位 mc，并按 i*rota 的因子对其进行旋转。如我们将看到，变量 rota 也用于使用左下角一排按钮重新配置界面。最后，我们将 mc+i 的 alpha 设置为 80。

仍在 for 循环内，接下来要做的是定义我们的鼠标悬停回调函数：

```
_root['mc'+i].onRollOver = function() {
	this._alpha = 100;
	ref = Number((this.name).substring(2));
	_root.select = _root.link[ref][0];
	_root.label._visible = true;
}
```

首先，我们将鼠标悬停时的 mc alpha 设置为 100。此前，在生成按钮 mc 的代码块中我们将 alpha 设置为 80，这样做会让按钮在鼠标悬停时产生微妙高亮的效果。如稍后所见，当我们从特定按钮 mc 移开鼠标时，alpha 将恢复为 80。

接下来 – 随后的 onRollOut 函数简单地将按钮电影剪辑的 alpha 设回 80，并将标签的可见性设回 false。

```
_root['mc'+i].onRollOut = function() {
    this._alpha = 80;
    _root.label._visible = false;
};
```

接下来，我们将一个新变量 ref 的值设置为 Number((this._name).substring(2)) 的值。这相当于将该特定实例名称的字符串标识符中的第三个字符转换为数字数据类型。因此，这给我们提供了一个变量，表示按钮序列中哪个按钮被鼠标悬停，基本上是 0 到 25 之间的一个数字，这确实非常方便。

下一个代码块中的 onRelease 函数指示 Flash 做许多事情 – 首先它绘制形状：

```
_root['mc'+i].onRelease = function() {
    count = 0;
    degrees = -90;
    _root.dial._visible = true;
    _root.createEmptyMovieClip('shapes', -1000);
    with (_root.shapes) {
        drawShape(486, 191, 57, 1, 0xFFCCCC,
        0xFFCCCC, 40, cshape, dshape);
        drawShape(286, 191, 57, 1, 0xFFCCCC,
        0xFFCCCC, 40, cshape, dshape);
        drawShape(486, 191, 134, 1, 0xFFCCCC,
        0xFFCCCC, 40, cshape, dshape);
        drawShape(286, 191, 100, 1, 0xFFCCCC,
        0xFFCCCC, 40, cshape, dshape);
    }
}
```

接下来的一行，我们可以看到变量 _root.select 已被设置为 _root.link[ref][0] 的值。因此，我们使用 ref 来引用嵌套的 link 数组，在此例中引用第一个元素。例如，如果我们在序列中鼠标悬停于第 9 个按钮，我们将引用 link 数组中第九个嵌套数组的第一个元素，在此例中返回字符串 shell。

这种方法在本示例中被广泛使用，作为引用我们数组中与正在交互的按钮对应的数据的一种方式。

下一行将标签设置为可见，因此我们的按钮标签出现在屏幕上，并在指针所在处跟随它浮动，只要它位于按钮上方。在第 1 帧中为标签定义的 onEnterFrame 回调函数会在每一帧都使用 _root.select 的值更新其包含的文本，从而始终显示正确的标签。

变量 count 和 degrees 分别设置为 0 和 -90，这基本上在点击按钮时将表盘指针和大小标签的位置重置回 12 点方向。通过将表盘的可见性属性设置为 true 来使表盘可见。

![](img/50202c17d5022233f3e3ec60560e35aa_46_0.png)

