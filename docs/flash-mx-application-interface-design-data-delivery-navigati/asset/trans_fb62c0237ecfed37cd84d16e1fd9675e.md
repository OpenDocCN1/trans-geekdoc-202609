

我们还为每个按钮设置了 onRollOver 和 onRollOut 状态。当你将鼠标悬停在按钮上时，这些状态会在屏幕底部显示工具提示，以便你了解它的功能。原始帮助文本存储在临时变量中，当用户将鼠标从按钮上移开时会重置。

```
allButtonsOff = function () {
   mainButDraw.gotoAndStop(1);
   mainButLine.gotoAndStop(1);
   mainButCurve.gotoAndStop(1);
   mainButFill.gotoAndStop(1);
   mainButClear.gotoAndStop(1);
   maskDrawBut.gotoAndStop(1);
   mainButScale.gotoAndStop(1);
   applyMaskBut.gotoAndStop(1);
   moveMaskBut.gotoAndStop(1);
   moveJPGBut.gotoAndStop(1);
   mainMaskBut.gotoAndStop(1);
   loadJPGBut.gotoAndStop(1);
   tempLayer.clear();
   drawPad.onPress = drawPad.onRelease =
     drawPad.onReleaseOutside = undefined;
   _root.a1.removeMovieClip();
   _root.a2.removeMovieClip();
   _root.ctrl.removeMovieClip();
};
```

这基本上只是遍历每个按钮并将其设置为第 1 帧（即其关闭状态），然后清除临时绘图层，并确保 drawPad 上没有附加任何操作。它最后要做的就是从舞台中移除曲线工具将使用的三个点剪辑。

画笔、填充和 T 恤背景的颜色芯片的工作原理完全相同。点击它们时，它们会将自身打开，并将其他颜色芯片关闭。然后它们会在根上设置一个变量，以让颜色代码知道正在影响哪个芯片。

## 画笔尺寸

![](img/50202c17d5022233f3e3ec60560e35aa_194_0.png)

画笔尺寸、画笔透明度和填充透明度工具非常简单。每个工具基本上只是一个输入文本框的容器。每个文本框都附加了一个变量，因此每当在框中输入新值时，相应的变量就会更新。每当代码需要知道画笔尺寸或某个透明度值时，就会调用这个变量。

## 颜色调色板

这个绘图应用程序需要颜色用于三个方面——画笔颜色、填充颜色和 T 恤颜色。以最整洁且最直观的方式显示可用颜色的方法是绘制一个调色板。让我们来看看这里是如何实现的。

## 制作调色板

之前我以类似的方式处理颜色时，使用了位移运算，发现整个过程有点繁琐。所以，这次我决定“作弊”，使用一种我在使用 JavaScript 渲染的 HTML 表格时想出来的简单程序（灵感来自 graphic.com 2002 tableart 竞赛，www.graphic.com/tableart，我受邀担任评委）。

这种方法生成的完整颜色范围是标准的 216 色网页安全调色板。我不是说我一定始终遵循这个调色板，但这里的编码稍微简单一些，因为需要复现的颜色范围更小。

这是调色板（我总觉得这些挺好看的）：

![](img/50202c17d5022233f3e3ec60560e35aa_194_1.png)

让我们来看看生成这个调色板的代码。首先，在进入核心内容之前定义一个函数。

```
function setHex(hexColor) {
  this.col = new Color(this);
  this.col.setRGB(hexColor);
}
```

接下来我们设置一些变量：

```
rows = 0;
columns = 0;
count = 0;
columnCount = 24;
```

这个函数在整个代码中都用于设置上述工具的颜色。它非常简单，但几乎可以用于任何事情。这个函数与 call 命令一起使用，因此它适用于调用它的对象。我们将在下一部分代码中看到其实际用法。

该函数为请求它的对象设置一个新的 Color 对象，然后将其颜色设置为 hexColor。

那么 hexColor 从哪里来呢？嗯，这就是“作弊”所在，接下来的代码派上用场了。让我们逐段来看。

要理解这些变量，需要知道网格是如何生成的。它从左上角到右下角逐行绘制。columnCount 表示每行的列数或单元格数，稍后用于检查是否应该移到下一行。count 用作附加到每个附加方块实例名称的标准变量，而 columns 和 rows 用于绘制位置。

然后我们设置三个 for 循环：

```
for (redi=0; redi<colorLen; redi++) {
for (greeni=0; greeni<colorLen; greeni++) {
for (bluesi=0; bluesi<colorLen; bluesi++) {
```

好吧，我首先想做的是将颜色方案限制为网页安全调色板，将输入限制为某些十六进制值。对于不熟悉这些值的读者，这些值是 00、33、66、99、CC 和 FF，从中取任意三个组合，就能得到一个网页安全颜色。例如，纯红色的十六进制值为 #FF0000（由 FF 红、00 绿和 00 蓝组成）。

我们使用 colors 数组的长度，设置为 colorLen（在此例中每个为 6）作为最大数量。这三个循环将运行代码 6×6×6 次，从而得到神奇的数字 216。

考虑到这一点，我首先设置了一个包含所有网页安全十六进制值的数组：

```
colors = new Array("00", "33", "66", "99",
"CC", "FF");
colorLen = colors.length;
```

之后是在 for 循环中执行的代码：

```
attachMovie("sq", "sq"+count, count);
if (columns == columnCount) {
  columns = 0;
  rows++;
}
columns++;
```

这里的第二行代码只是获取数组中的元素数量。这与以下循环一起使用。

请记住，这段代码将运行 216 次——听起来很多，但它是瞬间完成的。

![](img/50202c17d5022233f3e3ec60560e35aa_195_0.png)

好吧，这里的第一行不需要太多解释——它只是从库中获取一个小方块。如果你想美化调色板的外观，或者只想要更大的图标，请务必更改这个形状。

下一行中的条件 if 语句执行检查，看当前的 columns 变量（即当前列位置）是否与 columnCount 相同。如果相同，则重置 columns，并递增 rows。这相当于打字机到达行尾，并在移到新行前听到那个令人愉快的“叮”声。最后，columns 会被递增。

然后我们有三行来执行当前方块的关键定位：

```
current = _root ["sq"+count] ;
current._x =columns* (current._width) +530 ;
current._y = rows* (current._height) +380 ;
```

x 和 y 位置根据 columns 和 rows 变量设置，乘以当前方块的宽度或高度。每个方程末尾添加的数字只是手动计算的量，用于将网格放置在舞台上的某个位置。

然后我们调用 getMeColor 函数将当前方块设置为按钮，并存储此方块的十六进制值：

```
getMeColor.call (current) ;
current.hexy = "0x"+colors [redi] +
colors [greeni] +colors [bluesi] ;
```

getMeColor 应用于调色板中的每个单元格，根据请求颜色的元素——无论是画笔、填充还是 T 恤——它只需更改该选项的芯片颜色，并将这些颜色存储在 _root 上。

![](img/50202c17d5022233f3e3ec60560e35aa_196_0.png)

![](img/50202c17d5022233f3e3ec60560e35aa_196_1.png)

下一行使用上述数组创建颜色，并将其存储在当前实例的名为 hexy 的变量中。一种颜色由红、绿、蓝值组成，每个值都从数组中提取，取决于嵌套 for 循环中的位置。颜色前面带有 0x 前缀，以将其定义为十六进制值。

稍后将重要地使用 hexy，从调色板中获取方块的颜色。

下一行使用 setHex 函数设置当前方块的颜色：

```
setHex.call (current , current .hexy ) ;
count++ ;
}
}
```

当所有 for 循环都运行完毕后，这段代码的整体就创建了我们的网页安全调色板。如你所见，这里的代码并不难，虽然调色板的创建非常简单，但也极其整洁高效。当然，这是“作弊”（因为更专业的方法是数值计算颜色，然后进行位移运算，而不是在数组中拼凑数字），但它省去了从一种格式到另一种格式的所有痛苦转换，以及那些讨厌的数学运算。

