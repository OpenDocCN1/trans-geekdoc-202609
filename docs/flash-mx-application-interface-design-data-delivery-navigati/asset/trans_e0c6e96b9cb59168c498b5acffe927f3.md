

现在我们已经建立了变量和颜色方案，是时候在舞台上放置一些电影剪辑来保存实际图形了。这段代码仍然位于变量图层上：

```
this.createEmptyMovieClip("sectionHolder", 1);
```

sectionHolder 是将保存所有按钮本身的剪辑。我经常喜欢将附加的图形放入容器中，而不是直接添加到舞台上，因为如果需要，这样可以给整个组的放置、旋转和缩放带来更多自由。

下一个电影剪辑将充当我们舞台的背景。由于我们将动态更改颜色，因此不能依赖舞台颜色本身。相反，我们使用绘图 API 在舞台周围绘制一个矩形框，并根据需要对其着色：

```
this.createEmptyMovieClip("bg", 0);
bg.beginFill(currentColorScheme.background
    , 100);
drawBox(bg, 0, 0, stageWidth,
    stageHeight);
bg.endFill();
```

好吧，如果你使用过绘图 API，那么 beginFill（我们向其中发送颜色和 Alpha 值）和 endFill 行可能对你来说很熟悉，但 drawBox 从何而来？嗯，由于我们将在这个电影中绘制大量矩形框，因此最好将其放在另一个我们可以轻松反复调用的函数中。我们发送到这个新函数的内容是要绘制的剪辑，以及矩形框的左、上、右和下边界。现在让我们处理这个函数，这样你就可以看到我们是如何完成的。

转到代码的函数图层（应该为空），然后键入以下内容：

```
drawBox = function(clip, l, t, r, b) {
    with(clip) {
        moveTo(l, b);
        lineTo(r, b);
        lineTo(r, t);
        lineTo(l, t);
        lineTo(l, b);
    }
}
```

尽管这个函数看起来很简单，但它将大有帮助。使用发送的四个边界，该函数在给定剪辑中绘制一个矩形框。请注意，我们将填充方法（以及 clear 和 lineStyle）保留在函数之外，以便我们可以针对不同的剪辑来处理这些内容。处理完这些后，跳回变量图层，以便我们可以在那里完成工作。

回到变量图层，我们需要添加格式化所有文本字段的行。将这些行添加到背景图形（bg）的创建之后：

```
headingTF = new TextFormat();
headingTF.align = "right";
headingTF.font = "scriptFont";
headingTF.size = 18;
headingTF.color = currentColorScheme.foreground;

infoTF = new TextFormat();
infoTF.align = "left";
infoTF.font = "scriptFont";
infoTF.size = 15;
infoTF.color = currentColorScheme.foreground;

buttonTF = new TextFormat();
buttonTF.align = "center";
buttonTF.font = "scriptFont";
buttonTF.size = 16;
buttonTF.color = currentColorScheme.foreground;
```

这里我们使用新的 TextFormat 对象为我们的文本字段提供格式。每个格式对象都有相同的字体，因为我们只从库中导出了一种，尽管每个对象的大小和对齐方式不同。请注意，每个对象还通过查看 currentColorScheme 的 foreground 属性来建立其颜色（每个对象的颜色相同）。由于我们将 currentColorScheme 设置为 blackboard，那么该颜色将是白色。

如果你使用的导出字体不是 QuillScript，那么你可能需要返回此区域来调整字体大小。如果我的值不适合你选择的字体，只需更改每个文本格式的 size 属性即可。

这就处理完了我们所有的变量。现在是时候添加将在舞台上实际绘制按钮的代码了。

## 绘制按钮

输入大量代码却看不到任何结果是很令人沮丧的，所以让我们编写一些代码，快速向我们展示结果，并奖励我们迄今为止的努力。这将在舞台上添加新的电影剪辑，以表示界面右侧的部分按钮。

转到设置舞台图层（此时应该为空），然后键入以下内容：

```
for (i = 0; i < sections.length; i++) {
    clip = sections[i].clip =
    sectionHolder.createEmptyMovieClip
    ("sectionButton" + i, i);
    sectionButtons.push(clip);
    clip._y = ((i*2) * buttonHeight) +
    buttonHeight*2;
    clip._x = sectionXPos;
}
```

我们以一个 for 循环开始，以遍历我们在部分设置图层中已经建立的部分数量。对于这些部分中的每一个，我们创建一个新的电影剪辑，并将对该电影剪辑的引用放在该部分的新 clip 属性中。我们还将引用放入一个变量中，以便在我们的其余代码中更易于使用。剪辑创建后的下一行将对剪辑的引用推入我们之前创建的 sectionButtons 数组中。最后两行将剪辑放置在舞台上。虽然每个剪辑的 _x 位置相同，但 _y 位置会根据循环的当前迭代而改变。我是如何得到这个值的并不十分重要，因为这只是剪辑将下落（且永远不会重新分配）的起始位置。

![](img/50202c17d5022233f3e3ec60560e35aa_63_0.png)

接下来的代码片段（应紧跟在上一部分之后）在 sectionButton 电影剪辑中添加并格式化一个文本字段：

```
clip.createTextField("label", 0,
    halfButtonWidth*.75, -buttonHeight/2,
    0, 0);
label = clip.label;
label.setNewTextFormat(headingTF);
label.embedFonts = 1;
label.autoSize = "right";
label.selectable = 0;
label.text = sections[i].name;
label._y -= label.textHeight/2;
```

要了解 label 的放置方式，我们首先需要了解 sectionButton 图形将如何绘制。基本上，边框将从 sectionButton 剪辑的中心向左和向右（正和负 _x）绘制 halfButtonWidth，并在 _y 轴上从 0 到 -buttonHeight。因此，将 label 文本字段放置在 halfButtonWidth*.75 和 -buttonHeight/2，会将其放在 x 轴的最右侧和 y 轴的中间。我们将其高度和宽度设为 0，因为在几行之后我们将其 autoSize 属性设置为 right，这意味着它将根据我们放入其中的文本从右侧自动调整大小。我们还应用了 headingTF 文本格式并嵌入导出的字体，以便可以看到它。在禁用文本字段的 selectable 属性（这将允许用户选择文本）之后，我们将相应部分的名称放入 text 属性中，并根据 textHeight 调整 y 位置，以使文本保持在剪辑的中间。

下一段代码在我们的 sectionButton 内部添加一个新的电影剪辑，以保存我们使用绘图 API 进行的任何绘图。将其放在前面的代码之后：

```
drawing = clip.createEmptyMovieClip
("drawing", 2);
drawing.leftSide = halfButtonWidth;
drawBorders(drawing);
```

创建名为 drawing 的新剪辑后，我们为它提供一个变量来保存绘图的当前左侧（目前，仅仅是 sectionButton 中心到 sectionButton 宽度的一半）。随着部分打开时我们将按钮的左侧向左扩展，这将发生变化。下一行是我添加的另一个函数，用于封装我们将在整个过程中使用的代码。drawBorders 将为电影剪辑添加随机边框。让我们跳回我们的函数代码图层，现在添加这个新函数。

在函数图层中，紧跟在我们的 drawBox 函数之后，编写以下内容：

```
drawBorders = function(clip) {
  clip.clear();
  clip.lineStyle(1,
  currentColorScheme.foreground, 100);
  drawRandomBox(clip, -clip.leftSide, -
  buttonHeight, halfButtonWidth, 0);
}
```

在这个函数中，我们接受一个电影剪辑作为参数，清除其中的任何先前绘图，根据当前颜色方案的前景颜色重置 lineStyle，并调用一个新函数 drawRandomBox，向它发送剪辑及其四个边界。这个函数与我们之前的 drawBox 函数类似，但它将绘制带有随机边框的矩形框。让我们现在编写必要的代码。

在 drawBox 函数下方，添加以下新函数：

```
drawRandomBox = function(clip, l, t, r, b) {
  with (clip) {
    for (var i = 0; i < 3; i++) {
      moveTo(getRandom(10) + l,
      getRandom(10) + b);
      lineTo(getRandom(10) + r,
      getRandom(10) + b);
      lineTo(getRandom(10) + r,
      getRandom(10) + t);
      lineTo(getRandom(10) + t,
      getRandom(10) + t);
      lineTo(getRandom(10) + l,
      getRandom(10) + b);
    }
  }
}
```

在这个函数中，我们运行三次 for 循环，并在矩形框的边界附近从随机位置绘制到随机位置。getRandom 是什么？哎呀，这是我们即将编写的另一个函数。

将此添加到 drawBox 函数上方，仍然在函数图层上：

```
getRandom = function(range) {
  return Math.random()*range - range/2
}
```

很简单。我们调用这个函数并发送一个范围，以在其中查找随机数。该函数使用 Math.random 找到 0 到 1 之间的数字，将其乘以我们的范围，使我们得到 0 到范围最大值之间的数字，然后我们减去一半的范围，因此返回的最终数字落在指定范围内，但在 0 的两侧（因此范围为 10 将返回 -5 到 5 之间的数字）。现在我们的 drawBorders 函数调用已完成，我们可以返回到设置舞台图层来完成那里的脚本。

返回到设置舞台图层后，添加这些行以完成 for 循环：

```
btn = clip.createEmptyMovieClip("btn", 1);
btn.beginFill(0, 0);
drawBox(btn, -halfButtonWidth,
-buttonHeight, halfButtonWidth, 0);
btn.endFill();
btn.onRollOver = sectionOver;
btn.onRollOut = btn.onReleaseOutside =
btn.onDragOut = sectionOut;
btn.onRelease = function() {
selectMe.apply(this._parent) };
}
delete clip;
delete btn;
delete drawing;
delete labelHolder;
delete label;
delete i;
```

