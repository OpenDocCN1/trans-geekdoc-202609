
现在，我们已使用函数从共享对象中检索了信息，是时候根据收到的数字进行一些计算了。

首先，我们需要检查共享对象文件是否存在，以确认用户之前是否访问过我们的网站。我们使用 if 语句来完成此操作：

```
if(!firstVisit) {
  plantSize = 0;
  daysSinceLastVisit = 0;
  firstVisit = 1;
}
```

它检查名为 firstVisit 的变量是否有任何值，而不是 undefined。在函数 getLastVisit 中，我们让 firstVisit 等于 retrievedObj.data.firstVisit。如果用户从未访问过该网站，则共享对象文件 timeHolder 不会存在于用户的计算机上，因此当我们尝试检索 retrievedObj.firstVisit 的值时，它将是 undefined。如果这是用户的首次访问，我们将变量 plantSize 设置为 0，将变量 daysSinceLastVisit 设置为 0，并将变量 firstVisit 设置为 1。

Date Actions 层中代码的第二个 if 语句检查距离用户上次访问已过去多长时间（如果他们之前访问过该网站）：

```
if((daysSinceLastVisit == 0) &&
  (plantSize < 50)) {
  plantSize ++;
} else if ((daysSinceLastVisit > 0) &&
  (plantSize > 0)) {
  plantSize -= daysSinceLastVisit;
}
```

这样我们就可以根据用户上次访问的时间，让植物生长或萎缩。如果自上次访问以来的天数为 0（意味着用户在过去 24 小时内访问过），我们会通过 plantSize++ 让植物体积以 1 的因子增长，最大体积为 50。否则，如果自上次访问以来的天数大于 0（意味着距离上次访问已超过一天或 24 小时周期），我们将因用户访问不够频繁而惩罚用户，使其植物在体积和颜色上萎缩，具体做法是将变量 plantSize 设置为自上次访问以来每过一天减少 1。

现在，我们已利用用户上次访问的所有信息相应地设置了植物大小，是时候将当前时间和一些其他变量保存到用户的 sharedObject 文件中，以便他们下次访问我们的网站时可以读取。我们通过编写一个名为 saveTime 的非常简短整洁的函数来完成所有这些操作：

```
function saveTime() {
  savedObj = sharedObject.getLocal
  ("timeHolder");
  savedObj.data.lastVisit = currentTime;
  savedObj.data.plantSize = plantSize;
  savedObj.data.firstVisit = firstVisit;
  savedObj.flush();
}
```

再次，就像我们在函数 getLastVisit 中所做的那样，我们创建了另一个 sharedObject 对象的实例。为了避免与在 getLastVisit 中创建的第一个实例混淆，我们将此实例命名为 savedObj。我们将为 savedObj 实例设置三个自定义属性：

- savedObj.data.lastVisit – 毫秒级的当前 UTC（协调世界时）时间。
- savedObj.data.plantSize – 表示植物新大小的数字。
- savedObj.data.firstVisit – 告诉我们用户之前访问过该网站。

函数内的最后一行：

```
savedObj.flush();
```

该行将数据保存到用户计算机上的 `sharedObject` 文件中，以供下次用户返回时检索。我们接着在下一行执行 `saveTime` 函数：

```
saveTime();
```

## 浇灌树叶（或：将 RGB 颜色转换为十六进制值）

此层上的最后一个函数 `convertColors` 是一段精巧的小代码，你可能在许多其他项目中也会发现它很有用。让我们先看看代码，然后再讨论它的作用：

```
function convertColors(varName, varR,
   varG, varB) {
   newR = varR.toString(16);
   if (newR == 0) { newR="00" };
   newG = varG.toString(16);
   if (newG == 0) { newG="00" };
   newB = varB.toString(16);
   if (newB == 0) { newB="00" };
   this[varName] = ("0x" + newR + newG + newB);
}
```

该函数允许我们动态创建值等效于十六进制值的变量——十六进制值是网页中引用颜色时使用的字母/数字组合。例如，#000000 是黑色，#FFCC00 是橙色，#FFFFFF 是白色。通过将要转换的颜色的 RGB 值传递给该函数，我们可以输出相同 RGB 数字的等效十六进制值，并在绘图 API 中使用它们。这样，我们就可以动态地将植物颜色从棕色改为绿色。真翠绿！

我们将向函数 `convertColors` 传递要创建的变量名，以及三个表示红色、绿色和蓝色值的数值（范围在 0 到 255 之间，构成我们想要的颜色）。在函数内部，我们为红色、绿色和蓝色值创建临时变量，并使用 `toString(16)` 方法将其转换为 16 进制。这样做会将数字转换为字符串。

例如，如果我们将数字 200 传递给变量 `newR` 的 `toString(16)` 方法，将返回字符串 `c8`；如果对 `newG` 也做同样的操作并传入数字 150，则返回字符串 `96`；最后，我们当然还需要蓝色的十六进制字符串值，因此我们将值 `0` 传递给 `newB`，并返回 `0`。现在，由于十六进制颜色需要一个六个字符的字符串，我们会对每个新变量进行一次小检查，看返回的字符串是否等于 0，如果等于，则将其设置为 `00`。

最后，我们动态创建变量来存储最终颜色。

我们希望植物开始时呈现相当不健康的棕色，而幸运的是，棕色的 RGB 值和明亮健康的绿色的 RGB 值可以轻松转换成一个巧妙的小公式，该公式允许我们根据用户访问的频率动态更改植物颜色。

我们将使用的棕色的 RGB 值为：

- 红色：200
- 绿色：150
- 蓝色：0

而健康明亮绿色的 RGB 值为：

- 红色：150
- 绿色：200
- 蓝色：0

正如你所见，随着用户访问网站，通过变量 `plantSize` 减少植物的红色值并增加绿色值，将方便地将植物从棕色变为绿色！

要执行该函数并创建一个值为代表颜色的十六进制字符串的变量（我们将使用该颜色为植物上色），我们编写：

```
convertColors("fillColor", (200-plantSize),
    (150+plantSize), 0);
```

最终得到一个名为 `fillColor` 的变量，其字符串值为 `0xC39B00`。接着我们再次执行相同操作，以存储植物轮廓的颜色：

```
convertColors("outlineColor", (150-plantSize), (100+plantSize), 0);
```

这给我们提供了一个名为 `outlineColor` 的变量，其字符串值为 `0x906A00`。

现在，我们已创建一些变量来存储植物轮廓和填充颜色的值，既然已经创建了这个巧妙的小函数，我们不妨使用它为植物所在的花盆创建颜色，具体方法是动态创建变量 `potFill` 和 `potColor`：

```
convertColors("potOutline", 0, 102, 255);
convertColors("potFill", 0, 153, 255);
```

![](img/50202c17d5022233f3e3ec60560e35aa_168_0.png)

## 为植物制作动画

现在我们已完成所有设置，可以开始为植物制作动画了。Date Actions 层上的最后一行代码告诉 Flash 使用名为 makeThePlant（名字还挺有趣的……）的函数来创建植物。代码如下：

```
makeThePlant();
```

这将调用 Plant Actions 层上的一个函数，该函数使用绘图 API 来绘制并为我们的植物制作动画。

现在，我们转到植物电影剪辑中 Plant Actions 层上的代码。这段代码看起来可能很复杂，而且……确实如此。有点复杂。部分代码看起来冗长的原因是，植物电影剪辑设计为可以简单地拖放到你正在制作的任何电影的主时间轴上，并且可以正常工作。不仅如此，你可以在极短的时间内添加或删除植物上的单个树叶，因此可以说该代码具有可扩展性和动态性——这些都是我们喜欢的高效代码的特点。这并不是说 Plant Actions 层上的 ActionScript 无法进一步优化（我相当确定可以），但我这样编写是为了使其能够以逻辑方式理解，并让你了解 MX ActionScript 中的一些很棒的新功能。

首先，在 Plant Actions 层内部，我们创建一个二维数组——一个由一系列其他数组组成的数组。如果你愿意，可以把它看作嵌套数组。我们的数组映射，即二维数组，如下所示：

```
leafMap = new Array( ["leaf0", "left", 1,
130, 300, 75, 200, 130, 230, 10], ["leaf1",
"right", 2, 130, 300, 180, 225, 130,
200,20], ["leaf2", "right", 3, 130, 300,
140, 170, 130, 200, 20], ["leaf3", "left",
4, 130, 300, 115, 180, 130, 200, 10],
["leaf4", "left", 5, 130, 300, 80, 200,
135, 155, 20], ["leaf5", "left", 6, 130,
300, 70, 230, 130, 200, 10],
["leaf6", "right", 7, 130, 300, 170,
200, 130, 200, 20] );
```

让我们拆解它，看看它是如何运作的。看一下数组的第一个元素。如果我们对第一个元素进行 trace，它看起来会是这样：

```
trace( leafMap[0] );
```

它将输出：

```
"leaf0", "left", 1, 130, 300, 75, 200,
130, 230, 10
```

由此可见，数组中第一个元素的值是……另一个数组！就是这样。如果我们想要获取构成数组第一个元素的子数组中的第一个元素，我们可以这样做：

```
trace(leafMap[0][0]);
```

它将输出：

```
leaf0
```

要获取第一个子数组中的下一个元素，我们输入：

```
trace(leafMap[0][1]);
```

它将输出：

```
left
```

实际上，我们在这里所做的是使用一个数组来存储许多其他子数组，这些子数组包含关于每个树叶的独特信息。这样一来，我们就拥有了植物外观的一个“地图”。主数组中的元素数量告诉我们将制作多少片树叶，每个元素都包含一个子数组，用于存储我们将要生成的每个树叶电影剪辑的名称，以及该树叶的起始位置、每条曲线的终点等等。
