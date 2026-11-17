
使其可拖动。我们将在本章后面的代码中通过扩展 MovieClip 对象创建另一个自定义类，因此我建议你届时回来查看这段代码并运用你的知识。它与我们即将开始的编码实际上并无不同（而且简单得多），除了存在作为代码首尾的 #initclip 和 #endinitclip 行之外。这些行所做的只是允许我们将这段代码放在电影剪辑内，而不是放在主时间轴上，并且代码仍会在电影开始前运行，初始化我们的对象。

## 结构

本项目最后准备好的项目是主时间轴上名为 structure 的图层中的代码。如果你选择该图层中的帧并打开 ActionScript 编辑器，你将看到我用来填充树的代码。由于你可能希望为自己的项目修改此代码，因此我们需要更仔细地查看它，以便你了解我是如何实现的。

首先，我们有三个对象，用于存储节点的颜色值：

```
chaosCol = {params:{ra:50, rb:32, ga:50,
gb:-10, ba:50, bb:0}, connector:0x471D27};
titansCol = {params:{ra:50, rb:17, ga:50,
gb:34, ba:50, bb:36}, connector:0x38494B};
olympiansCol = {params:{ra:50, rb:32, ga:50,
gb:13, ba:50, bb:37}, connector:0x47344C};
```

每个对象包含两个属性：params 和 connector。params 包含另一个自定义对象，其中包含要发送给 Color 对象的 setTransform 方法的值。我们将使用 params 对象为节点本身着色。另一方面，connector 包含一个十六进制值，当我们使用绘图 API 绘制连接器时，会将该值发送给 beginGradientFill 方法。

结构图层中脚本的其余部分用于填充我们的树。让我们来看看这段代码的前两行：

```
chaos = {name:"Chaos", col:chaosCol};
chaos.info = "This is where I would put information on Chaos."
```

我们树中的每个节点都将是一个至少包含三个属性的对象。第一个属性是节点的名称，第二个是上面创建的自定义着色对象的引用，第三个是我们希望在节点的展开界面中关联的任何信息。

如果你不熟悉创建自定义对象的多种方式，那么你需要知道，以下所有方法都会实现完全相同的结果：

```
chaos = new Object();
chaos.name = "Chaos";

chaos = new Object();
chaos["name"] = "Chaos";

chaos = {};
chaos.name = "Chaos";

chaos = {};
chaos["name"] = "Chaos";

chaos = {name:"Chaos"};
```

我选择的方式是在第一行给对象赋予名称和颜色属性，在第二行赋予 info 属性。我认为这种方法清晰且易于更新，同时能将行数控制在可管理的长度。

现在基于这个第一个对象（它将是整个树的始祖），我添加了以下几行：

```
gaea = {name:"Gaea", col:titansCol};
gaea.info = "This is where I would put information on Gaea."
tartarus = {name:"Tartarus",
col:chaosCol};
tartarus.info = "This is where I would put information on Tartarus."
eros = {name:"Eros", col:chaosCol};
eros.info = "This is where I would put information on Eros."
erebus = {name:"Erebus", col:chaosCol};
erebus.info = "This is where I would put information on Erebus."
chaos.children = [gaea, tartarus, eros,
erebus];
delete tartarus;
delete eros;
delete erebus;
```

每个子节点的设置方式与其父节点相同。一旦父节点的所有子节点都被创建，我们就将它们添加到父节点的 children 数组中，这是我们创建的一个新属性，用于保存引用。一旦子节点的引用被存储，我们就可以删除不再使用的那些变量。在这里，我们删除所有子节点，但 gaea 对象除外，因为它很快将需要存储子节点。如果你继续向下阅读代码，你会发现这种模式一直贯穿到底。重要的是你要明白，我们使用的所有变量（例如 gaea、tartarus 和 eros）仅仅是——保存内存中对象引用的变量，而不是对象本身。一旦一个对象被存储在其父节点的 children 数组中，并且（如果需要）拥有自己的包含对象引用的 children 属性，

我们就可以安全地删除该变量。对象本身并未被删除，仅删除引用它们的变量。当我们完成整个家族的存储后，只会剩下一个变量 chaos，它将在其多个维度中保存所有对象的引用。还需要注意的一点是，如果一个节点有配偶，我会添加另一个属性，就像我在这里对 cronus 节点所做的那样：

```
cronus.spouse = {name:"Rhea", col:titansCol};
```

spouse 属性包含一个持有名称和颜色的对象。

如果你希望构建自己的树，只需修改这些属性，因为显示树的系统与信息是独立运行的。你还可以考虑在 XML 中构建树，并将其导入 Flash 进行解析，但这对于本篇已经篇幅颇长的章节来说内容过多。请查看本章之后 Jamie Macdonald 的章节，了解 XML 结构。你不妨尝试融合这些技术！在下载文件中，你会找到 gods_tree_XML.fla，它使用 XML。SWF 允许你在两棵树之间切换，即希腊诸神树和北欧诸神树，它们在点击按钮时从 XML 文件加载。存储信息的两个文件，即 Greek_gods.XML 和 Norse_gods.XML，展示了构建和设置要加载到界面中的自有文件是多么容易。通过向树中添加更多元素，你可以创建额外的功能。例如，图像元素可能包含要加载到界面中的 JPG 文件名。

## 现在，代码

现在进入精彩部分！生成和导航此界面的代码分为两部分——节点本身和其他所有部分。“其他所有部分”实际上非常简单，因为大部分功能都包含在节点本身中，所以让我们敲几行代码，立即处理好它。

![](img/50202c17d5022233f3e3ec60560e35aa_91_0.png)

## 其他所有部分

这是我们要为电影设置一些全局变量的地方，包括用于控制界面文本格式的对象、尺寸、动画速率以及控制节点 3D 外观的几个因素。我们还将创建用于容纳和遮罩树的电影剪辑。

在主时间轴的代码图层中选择第一帧，打开 ActionScript 编辑器，键入以下内容：

```
windowWidth = 550;
windowHeight = 400;
intervalTime = 40;
intervals = 10;
```

windowWidth 和 windowHeight 保存我们查看窗口的尺寸（实际上小于舞台）。intervalTime 是电影中间隔调用之间的毫秒数。树的几乎所有动画都是使用 setInterval 而不是 enterFrame 事件来完成的，因此在这里有一个变量可以快速修改以更改动画速率是件好事。最后一个变量 intervals 用于所有缓动运动补间函数。此界面使用经典（且简单）的芝诺悖论补间方法，这意味着我们只需将剪辑将要移动的距离除以每帧的某个数字。此变量包含该数字。使用 10 意味着剪辑每帧将移动其剩余距离的十分之一。

接下来，这里还有四个变量，你可以直接在前四行之后添加：

```
childDistance = 2;
childDepth = 100;
scaleFactor = .4;
pi = Math.PI;
```

childDistance 是一个数字，我们将乘以父节点的直径，以获取放置子节点的距离。childDepth 是父节点和子节点之间在 z 轴上的距离（记住，我们正在进行 3D 处理，因此 z 轴垂直于你的计算机屏幕）。scaleFactor 是我添加的一个变量，用于更好地控制节点的外观。通过更改此数字，你可以使节点在屏幕上变大或变小，而无需深入所有 3D 渲染代码。最后，我将 pi 的值放入了一个变量中，因为我们会在代码中频繁使用它，这样就不必每次都去查找 Math 对象，因为这会稍微减慢我们的速度。

接下来是我们电影的字体格式。键入以下行以跟在前面的代码之后：

```
nameTF = new TextFormat();
nameTF.font = "sansFont";
nameTF.align = "center";
nameTF.size = 12;

underlineTF = new TextFormat();
underlineTF.underline = 1;

infoTF = new TextFormat();
infoTF.align = "left";

titleTF = new TextFormat();
titleTF.font = "titleFont";
titleTF.size = 32;
```

我非常喜欢 TextFormat 对象，真的。一个相当不错的特点是，你可以将它们组合在一起。因此，如果我将一个 TextFormat 对象添加到已经应用了一个 TextFormat 的文本字段，它只会应用额外的格式而不会擦除之前的格式（除非所有属性值都不同）。这是我在这里使用的概念。nameTF 是我电影的主要 TextFormat。它使用我从库中导出的 sansFont，将其居中并将大小设为 12 磅。接下来的两个 TextFormat 只是在此基础上添加格式，一个添加下划线，另一个将文本左对齐（我用它在节点界面的信息框中）。最后一个 TextFormat 用于节点界面中节点的标题。

![](img/50202c17d5022233f3e3ec60560e35aa_92_0.png)

![](img/50202c17d5022233f3e3ec60560e35aa_92_1.png)

![](img/50202c17d5022233f3e3ec60560e35aa_92_2.png)

![](img/50202c17d5022233f3e3ec60560e35aa_92_3.png)

![](img/50202c17d5022233f3e3ec60560e35aa_92_4.png)
