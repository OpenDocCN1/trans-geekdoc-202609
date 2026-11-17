
现在来看实际的遮罩。

首先，遮罩主 T 恤比 JPG 遮罩要复杂一些，仅仅是因为它需要遮罩的东西更多。主遮罩必须隐藏 drawPad、square 和 jamJar 的内容。

这可能看起来有些过度设计，但这里实际上有三个遮罩在工作。这样做的原因是 Flash 遮罩每次只能遮罩一个项目。当然，你可以通过嵌套来遮罩更多项目，但并不总是可行，而且你会失去少量控制。

虽然有三个遮罩，但你会很高兴地知道其中一个是复用的。当我们第一次加载 JPG 时（参见加载 JPG 代码），为它创建了一个名为 newtee 的遮罩，以防止它超出 T 恤区域并覆盖整个界面。应用主遮罩时，newtee 遮罩被指示遮罩整个 jamJar 电影剪辑——即 JPG 遮罩 (_global.JPGM) 和 JPG (_global.JPGContainer)。

另外两个遮罩隐藏在主舞台上，名为 tshirt 和 tshirt2。这两个都是 tshirt_mask 的实例：

![](img/50202c17d5022233f3e3ec60560e35aa_217_0.png)

## 主遮罩的代码如下：

```
funcMainMask = function () {
	if (_root.maskOn == false) {
		_root.square.setMask(_root.tshirt2);
		drawPad.setMask(_root.tshirt);
		jamJar.setMask(_root.newtee);
		_root.maskOn = true;
	} else if (_root.maskOn == true) {
		drawPad.setMask(drawPadMask);
		JPGContainer.setMask(_root.newtee);
		_root.square.setMask(null);
		_root.maskOn = false;
	}
};
```

其中大部分都很简单，与 JPG 遮罩脚本非常相似，使用一个切换开关来打开或关闭遮罩，并检查其当前状态。唯一的区别是，某些遮罩会根据状态发生变化。下面是发生的操作：

- 当遮罩打开时，drawPad 的遮罩会从 drawPadMask（一个与绘图区域大小相同的正方形）更改为 tshirt。
- square 由 tshirt2 遮罩，当遮罩关闭时取消遮罩（null）。
- 当遮罩打开时，newtee 用作 jamJar 父级的遮罩；当遮罩关闭时，它遮罩 JPGContainer。

遮罩代码就这些。其中没有什么我们之前没见过的。

### 清除工具

![](img/50202c17d5022233f3e3ec60560e35aa_218_0.png)

当一切出错时，你会用到清除工具。它会删除你目前所做的一切，并让你重新从空白画布和铅笔开始。这听起来有点极端，确实如此，因此与所有极端操作一样，你会获得第二次机会来确认是否真的是你想要的。这是通过一个警告框来完成的，该警告框会跳转到舞台中央，并提供以下选项：

![](img/50202c17d5022233f3e3ec60560e35aa_218_1.png)

按下按钮后发生的第一件事是，我们从库中附加 clearCheck 警告框并将其定位在舞台中央：

```actionscript
funcClearTool = function () {
    _root.attachMovie("clearCheck",
        "clearCheck", 111111);
    _root.clearCheck._x = (Stage.width/2);
    _root.clearCheck._y = (Stage.height/2);
}
```

然后我们为每个按钮设置操作。“yes”按钮会清除 drawPad，擦除所有绘图，还会擦除 JPG 遮罩层并卸载 JPG 图像。完成这次彻底的“吸尘”后，它会打开自由绘图工具，修正帮助文本，然后从舞台上删除警告框：

```actionscript
_root.clearCheck.yesBut.onRelease =
    function() {
    drawPad.clear();
    JPG.clear();
    JPG.unloadMovie();
    _root.allButsOff();
    _root.mainButDraw.gotoAndStop(2);
    _root.funcFreeDraw();
    _root.help.text = "Click and drag to
    draw pencil lines";
    removeMovieClip(_root.clearCheck);
};
```

“no”按钮会跳过前三行擦除代码，但之后与“yes”按钮完全相同。它只是将绘图工具重置为自由绘图模式，并从舞台上删除警告框：

```actionscript
_root.clearCheck.noBut.onRelease =
    function() {
    _root.allButsOff();
    _root.mainButDraw.gotoAndStop(2);
    _root.funcFreeDraw();
    _root.help.text = "Click and drag to
    draw pencil lines";
    removeMovieClip(_root.clearCheck);
};
```

如果你愿意，可以将之前的工具存储在临时变量中，这样如果你选择取消清除命令，就会回到按下清除按钮之前的确切状态。

### 结语

尽管这个应用程序已经完成，但仍有很大的改进空间。当我向各种人展示它时，他们都请求添加一些不存在的工具，从无处不在的撤销选项到文本工具，再到形状工具。现实是，这个应用程序的开发永无止境...

我的版本侧重于创建基本设计和构图。工具的限制鼓励人们更具创造力和足智多谋。

该应用程序的任何新闻和更新都将在线发布于 www.pinderkaas.com/foed_tshirt。如果你在自己的网站上使用它，或进行任何修改或改进，请通过网站上的联系方式告知我——我很乐意看到其他人对它的诠释！

享用吧...

![](img/50202c17d5022233f3e3ec60560e35aa_219_0.png)

### 互动视频：空手道！

掌握 Flash 的实用知识让我们处于有利地位。在那种深夜讨论你想做但一直没去做的事情的时候，一位朋友提到他希望通过某种教学影片向他人展示自己空手道的娴熟技艺。这让我开始思考。能否使用 Flash 帮助他实现这个目标？Flash MX 的新视频功能打开了无限的可能性，我的脑海中立即开始转动，思考如何将这个愿望变为现实。然而，我知道挑战不仅仅是把视频放到网上。该网站必须是教学性质的，而且，它还需要易于更新。毕竟，他想要最终的控制权。能否创建一个可扩展的界面，让他能够准备和添加额外内容，一旦基础工作完成，只需付出最小的努力？我不是退缩于挑战的人，于是开始工作。

小小的足位图固然不错，但我们当然希望通过加入一些硬核空手道视频动作来为这项技术增添额外的维度。利用 Flash MX 嵌入视频到 Flash 电影中的新功能，结合基于矢量动态图形的传统 Flash 技术，我们可以分析视频内容，并将 Flash 用作教育内容制作者，在这里用于演示型（kata）的表演。我通过创建两部 Flash 电影来着手这项工作。第一部可以让我记录型（kata）的动作，第二部则旨在将这些捕获的信息作为空手道教学电影进行播放。我们的第一部电影名为 *kata_record.fla*，第二部是 *kata_play.fla*。

空手道的基本技术包括站姿以及格挡、踢击、出拳和打击的方法。这些技术在练习中会被组合成称为 katas（发音为 KAH tahs）的编排动作。我们都见过使用大量足部符号和箭头来描绘舞蹈动作的图示。虽然 Flash 足以胜任制作一支“如何跳舞”的电影，但除了 *Strictly Ballroom* 或 *Billy Elliot* 这些炒作驱动的潮流之外，谁又想跳舞呢？不过，这种图示表现的想法似乎非常适合我的挑战，即找到一种有效的方式来演示空手道。

事情就是这样，一个周五晚上，当世界上其他上班族都在为周末收尾时，我和一个穿着白色睡衣的人发现自己身处一个废弃的踢拳健身房，只带着一台 DV 摄像机和一个三脚架。

我们多次录制了型（kata）的表演，既有正面也有侧面。我们认为这两个角度能为观众提供最多的信息。我们希望观众在观看完整电影时能选择视角，因此提前考虑并确保任何可能需要的画面都在这个时候拍摄下来很重要。

在我们的 kata side 电影中，敬礼（rei）发生在 2.2 秒处。

![](img/50202c17d5022233f3e3ec60560e35aa_221_0.png)

理想情况下，这两个角度本应使用两台 DV 摄像机同时录制——但我们不生活在理想世界里，而作为一个真正的专业人士，我习惯于在技术和财务限制下工作。我们将型（kata）的表演既对着镜头拍摄，又横跨视野拍摄。（顺便说一下，出于这个项目的目的，所表演的练习是 Pinan Yondan 型（kata），但我想你自己也看出来了。）

在 kata front 中，它发生在 1.15 秒处。

![](img/50202c17d5022233f3e3ec60560e35aa_221_1.png)

使用 iMovie 来捕获素材。它的优点是简单易用，而且当然，它对我们来说是免费的，因为它随所有当前 Mac 标配。（它是仅限 Mac 的软件，但如果你打算进行类似项目并需要使用 PC，Windows XP 的 Movie Maker 也能完成同样的工作。）

将每个角度的型（kata）表演素材导入 iMovie 后，（两个剪辑被富有想象力地命名为 katafront 和 kataside）需要进行一些编辑，因为我们需要检查两个剪辑在时间轴上的开始和结束点是否一致。

由于型（kata）是一套精心编排的动作，每次表演所需的时间几乎完全相同。我们需要将 kataside 与 katafront 同步。每个型（kata）的第一步是鞠躬，也就是 rei（这挺有教育意义的，不是吗？）。我们需要在两个电影中让 rei 在时间轴上的完全相同位置发生。

一点简单的数学告诉我，我需要从 kataside 中移除 2.2 减去 1.15 秒，即 1.05 秒。为此，我们将播放头定位在 1.05 秒处，然后拆分视频剪辑。编辑 > 在播放头处拆分视频剪辑，或使用 Cmd / Ctrl-T。
