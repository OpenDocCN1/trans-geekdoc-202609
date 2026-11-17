

然后，我们使用原型函数绘制两组同心图形，这些图形用于容纳螺旋类型标签和我们的拨盘系统。

下一步涉及将我们在帧 1 中定义的空标签设置为与相应点击按钮相关的文本数据：

```
_root.size = " "+_root.link[ref][2];
_root.titletext.text = select;
titletext.setTextFormat (Tformat);
_root.spiraltype.text = _root.link[ref][1];
spiraltype.setTextFormat (Tformat);
_root.measurement.text = _root.link[ref][3];
measurement.setTextFormat (Tformat);
```

既然我们已有被点击按钮的引用编号 ref，就可以像之前一样，用它从维度链接数组中检索对应元素。例如，`_root.size = ""+_root.link[ref][2];` 将 _root.size 设置为维度链接数组中对应数组第三个元素的值，并在开头添加一个字符空格。然后，sizelabel 电影剪辑使用这个值，在舞台最左侧生成一个指示螺旋大小的浮动标签。titletext、spiraltype 和 measurement 文本字段也同样使用我们的 ref 变量引用链接数组来赋值。

接下来，我们创建一个名为 jpgframe 的新空电影剪辑，并在其中使用 drawShape 方法生成一个由同心图形组成的帧容器，用于容纳我们的 JPG 图片：

```
_root.createEmptyMovieClip('jpgframe', 300);
with (_root.jpgframe) {
drawShape(130, 193, 82, 1, 0xFFCACA, 0xFFCCCC, 40,
Math.random(1)*1.3, 0.7071);
drawShape(130, 193, 52, 1, 0xFFCACA, 0xEF9790, 100,
0.4086, 0.7071);
}
```

请注意，这次我们将 Math.random(1)*1.3 作为参数传递给 distorta 参数，其效果是生成一个带有浅色边框的随机但略带装饰性的粉色框架。在这个框架内，我们绘制了一个简单的圆形，用于容纳相关的 JPG。

![](img/50202c17d5022233f3e3ec60560e35aa_47_0.png)

![](img/50202c17d5022233f3e3ec60560e35aa_47_1.png)

![](img/50202c17d5022233f3e3ec60560e35aa_47_2.png)

![](img/50202c17d5022233f3e3ec60560e35aa_47_3.png)

接下来是将特定 JPG 加载到其框架中的代码块：

```
toload = select+".jpg";
_root.createEmptyMovieClip("jpgholder", 301);
with (_root.jpgholder) {
  _x = 91;
  _y = 163;
  loadMovie(toload);
}
}
```

首先，我们设置变量 toload，将 select 的值（将被设置为我们其中一个螺旋的字符串名称）与 .jpg 相加。然后，在舞台正确位置上新创建的名为 jpgholder 的电影剪辑内部，加载由 toload 表示的 JPG。

继续往下，我们来到 onEnterFrame 函数：

```
_root['mc'+i].onEnterFrame = function() {
  this._rotation -= 6*(2-(_root._xmouse/200));
}
}
```

这行简单的代码负责我们螺旋界面的方向旋转，该旋转取决于鼠标指针的 x 位置。由于我们按钮的特定空间分布，剪辑的旋转为界面带来了令人愉悦的三维深度效果。它让我们能够旋转螺旋并触达远侧的按钮——按钮半透明，因此当螺旋移动时，我们可以看到另一侧的内容。

最后的右花括号关闭了我们的 for 循环，在不到一秒的时间内，所有生成的按钮都通过刚才描述的回调函数附加获得了完整功能。

![](img/50202c17d5022233f3e3ec60560e35aa_48_0.png)

![](img/50202c17d5022233f3e3ec60560e35aa_48_1.png)

![](img/50202c17d5022233f3e3ec60560e35aa_48_2.png)

## 配置界面

我本来打算到此结束，但随后我想到在界面内添加一个界面——即利用构造变量（还记得 cshape、dshape、pha、kolor 和 rota 吗？）来影响按钮的形状和颜色，以及主界面的螺旋配置：

```
for (j=0; j<conf.length; j++) {
    _root.createEmptyMovieClip('nc'+j, 100+j);
    with (_root['nc'+j]) {
        drawShape(0, 0, 7, 1, 0xffffff, 0x666699*j/3.5, 40, 0.4086, 0.7071);
        drawShape(0, 0, 3, 1, 0xffffff, 0x999900*j/kolor, 30, 0.4086, 0.7071);
        _x = 30+j*15;
        _y = 375;
    }
}
_root['nc'+j].onRollOver = function() {
    ref = Number((this._name).substring(2));
    _root.select = ""+_root.conf[ref][2];
    _root.label._visible = true;
    this._xscale = this._yscale=110;
}
_root['nc'+j].onRollOut = function() {
    _root.label._visible = false;
    this._xscale = this._yscale=100;
}
_root['nc'+j].onRelease = function() {
    cshape = _root.conf[ref][0];
    dshape = _root.conf[ref][1];
    rota = _root.conf[ref][3];
    kolor = _root.conf[ref][4];
    pha = _root.conf[ref][5];
    _root.jpgholder.unloadMovie(toload);
    jpgframe.clear();
    _root.titletext.text = ""; _root.spiraltype.text = "";
    _root.measurement.text = ""; _root.dial.visible = true;
    gotoAndPlay(2);
}
}
```

配置界面在本质上与螺旋界面非常相似——它依赖一个名为 conf 的二维数组来存储传递给这些构造变量的数据，并使用相同的引用方法。这一次，按钮排列在舞台左下角的一行中——同样，按钮是使用 drawShape 原型生成的。每个按钮在鼠标悬停时会赋予一个新标签名称，而且这一次，每个按钮的缩放比例增加 10%，在鼠标移出时恢复到原始大小。当单击其中一个按钮时，这五个构造变量将被设置为我发现能在形状、颜色和形成方面产生有趣效果的值。尝试在 conf 数组中试验不同的值，以观察出现的各种几何精确且有趣的形状。

在我们的 onRelease 函数中，在设置完配置变量后，我们要求 Flash 使用 unloadMovie 方法卸载 JPG，并使用 clear 方法清除 jpgframe 电影剪辑。我们已将 _root.dial 的可见性设置为 true，以便为下一次重新绘制“指针”做好准备，并且还将标签内容设置为空字符串，从而从舞台上移除所有内容，为界面按新选定的配置重新构建做准备——我们只需指示 Flash 执行 gotoAndPlay(2) 即可实现。因此，帧 2 将再次生成界面，这次使用一组新的构造变量来影响螺旋的最终颜色、形状和配置。

## 帧 3

帧 3 包含一个简单的 stop，因此我们的故事到此结束。

![](img/50202c17d5022233f3e3ec60560e35aa_50_0.png)

## 向前与延伸

在本示例中，我使用 Flash 绘图 API 在运行时生成了屏幕上的所有界面元素。我展示了如何通过原型扩展基本 API 方法，从而为我们提供绘制更复杂形状的方法。然后，我将这些形状用作按钮，通过向其附加一系列事件回调函数来提供用户交互性。我们的数据引用自几个简单的二维数组——事实上，界面本身的生成结构也源自这些数组。从数组中提取的文本信息被动态创建和更新的文本字段所使用。总的来说，我们有一段相当精简的代码，大约 2.68 千字节，而且没有一个多余的符号。

从审美角度来看，我认为我们有一个有趣的界面，或许只差几步就能充当动画数据库前端。我希望在扭转和旋转界面的过程中能带来一定程度的乐趣，同时具备重新配置最终界面列的形状、颜色和结构的能力。在信息展示方面，我认为提供体验式导航对我们有利——即带有一丝趣味性的界面。我鼓励你向此系统添加更多构造变量，并调整现有变量的值，添加随机变量，甚至将其推向超越功能的程度——因为只有这种实验才是突破用户交互和导航新理念的唯一途径。

从技术角度来看，这个简单的系统也有很大优势，因为更新网站将变得轻松——我们只需用包含新螺旋名称及其所有相关数据的新数组元素来更新 link 数组。然后将新的 JPG 放入根文件夹，一切就绪——螺旋中的按钮数量始终与我们数组中的元素数量相同。

![](img/50202c17d5022233f3e3ec60560e35aa_51_0.png)

