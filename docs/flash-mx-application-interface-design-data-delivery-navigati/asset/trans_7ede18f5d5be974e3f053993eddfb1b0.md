

界面可以根据需要进行扩展，并可能与舞台上的其他元素集成。要查看实际效果，请访问我的网站 www.glenrhodes.com。虽然引擎与这里展示的相同，但我最近对其进行了更新以改变美学效果，如所示。

与其制作让人联想到文件和计算机系统的图形，不如我们可以使用饼干罐或任何其他物品的图像来表示“文件夹”。在其中，与其使用文件图标，不如将图标更改为饼干，这样我们的文件浏览器就由饼干罐中的饼干组成。变化是无止境的——这是我构思的另一个版本。

![](img/50202c17d5022233f3e3ec60560e35aa_161_0.png)

![](img/50202c17d5022233f3e3ec60560e35aa_161_1.png)

![](img/50202c17d5022233f3e3ec60560e35aa_161_2.png)

![](img/50202c17d5022233f3e3ec60560e35aa_161_3.png)

## 规划网站粘性

我们已经了解了创建富有启发性的网站和界面的几种方法，但“启发性”在保持访客兴趣方面只能起到有限的作用。我们如何超越这一点？网页设计中最理想的技巧之一，就是如何让人们定期回访网站。在本章中，我们将探讨如何创建一个能响应每个单独用户的功能。

当然，在我们的Flash电影中，有很多很多种方式可以选择来表现这一点，例如显示一个写着“自您上次访问已过去X天”的文本字段这种简单而又有些枯燥的方法。但是，我决定在这里更有创意一些，使用一个有机概念，一种会根据环境条件生长和缩小的事物，来展示用户回访您的网站的频率。

我们将使用室内植物的想法，它一开始会有小棕色的叶子。如果用户每天访问网站，他们的植物就会生长并变成漂亮的健康绿色。在创建过程中，我们将了解Flash MX的一些令人兴奋的新功能，这些功能让我们的编程工作变得轻松得多，其中一些功能文档并不完善（哎呀，其中一些功能在最初的MX帮助文件中甚至根本没有提到！）。

![](img/50202c17d5022233f3e3ec60560e35aa_162_0.png)

### 用户信息和共享对象功能

那么，问题在于：我们需要追踪用户回访我们网站的频率。然后，我们可以使用绘图API来制作一个植物，根据网站被访问的频率，使其大小发生变化并改变颜色。

那么，我们如何追踪和存储这些信息呢？嗯，我可以向你提供一大堆可行的解决方案：PHP、ASP、ColdFusion MX、PERL或MySQL。虽然这些方案可以为眼前的问题提供非常稳固和强大的解决办法，但在大多数情况下，这需要大量的学习，并且可能需要安装和配置一些令人生畏的服务器软件，才能使这个想法实现。

既然有更简单的路可走，为什么要让事情变得复杂和困难呢？现在就跟随我，无畏的读者，进入那个被称为**共享对象**的神秘世界……

Flash MX这个很棒的新功能几乎无人知晓，更不用说有实用的文章介绍了。你在MX早期版本随附的文档中找不到它，正因如此，你也很难在网上找到关于如何使用它的示例。

共享对象允许您以多种不同的形式在用户计算机上的特定位置存储数据，以便日后轻松检索该信息。它与cookie相同，只不过强大得多，强大得多。

现在，有一点您应该注意：当用户首次访问您的网站时，Flash Player会提醒用户SWF希望通过共享对象将数据保存到其机器上，并提示用户允许或禁止此操作。如果用户禁止，您将无法在Flash电影中存储和检索任何信息。不建议让您的电影严重依赖共享对象——请确保，如果用户在其机器上禁止使用共享对象，您的电影仍能正常工作。

我们将要制作的电影在未获得使用共享对象的权限下也能正常运行，但植物不会变大或变小——用户始终只会在电影的舞台上拥有一株小小的棕色植物。而且，坦白说，经过我辛勤的工作后，这也是他们应得的。

![](img/50202c17d5022233f3e3ec60560e35aa_163_0.png)

![](img/50202c17d5022233f3e3ec60560e35aa_163_1.png)

![](img/50202c17d5022233f3e3ec60560e35aa_163_2.png)

### 使用共享对象保存信息

通过使用ActionScript创建共享对象，Flash Player会在用户计算机上保存一个带有`.sol`扩展名的小文件。该文件可用于以变量字符串和数字、数组甚至XML对象的形式存储各种信息。

乍一看，从共享对象保存和检索数据看起来非常相似。要将数据保存到共享对象文件中，我们编写如下所示的ActionScript：

```actionscript
savedObj = sharedObject.getLocal("myFirstFlashCookie");
savedObj.data.storedVariable = "hello world!";
savedObj.data.storedNumber = 123456;
savedObj.data.storedArray = myArray;
savedObj.flush();
```

您可以将`sharedObject`实例的名称替换为任何您喜欢的名称。在本例中，它是`savedObj`，您也可以替换`sharedObject`的每个属性名称，在本例中是`storedVariable`、`storedNumber`和`storedArray`。您无法更改的是`sharedObject`数据，它出现在每行的中间部分。如果您更改了这个，您的`sharedObject`将根本无法工作。

如上面所示的最后一行代码 – `savedObj.flush();` 告诉Flash Player将我们指定的属性及其值写入名为`myFirstFlashCookie`的`sharedObject`文件中。如您所见，您可以在共享对象中存储字符串、数字、数组，几乎任何您喜欢的东西。酷吧？

要使用前一段代码检索我们存储的信息，我们编写如下内容：

```actionscript
retrievedObj = sharedObject.getLocal("myFirstFlashCookie");
_root.myVar = retrievedObj.data.storedVariable;
_root.myNumber = retrievedObj.data.storedNumber;
_root.myArray = retrievedObj.data.storedArray;
```

很简单！首先，我们将名为`storedVariable`的共享对象属性保存到计算机上的`sharedObject`文件中，然后在从文件中检索信息时，我们创建一个名为`_root.myVar`的新变量，并将其值设为`retrievedObj.data.storedVariable`。

![](img/50202c17d5022233f3e3ec60560e35aa_164_0.png)

### 开始编写代码

作为一个很好的入门示例，我们将使用这个想法来存储用户上次访问网站的时间和日期，并根据用户访问我们网站的频率显示我们的植物图形变大或变小。

从下载文件中打开stickiness.fla文件，并选择舞台左上角名为**植物**的空白电影剪辑。进入就地编辑模式。这个电影剪辑（实例名称为plant或_root.plant）包含三个图层，其中两个实际上包含代码。让我们通过查看名为Date Actions的图层上的ActionScript来了解共享对象。这个图层是我们将用来存储所有发送和检索访客频率信息所需代码的图层。

我们从Date Actions图层上的以下代码片段开始：

```actionscript
myDate = new Date();
currentTime = myDate.getTime();
```

使用内置的Date对象，我们创建一个Date对象的新实例并将其命名为myDate。然后，我们创建一个名为currentTime的变量，并将其值设为Date对象的getTime方法。getTime方法获取当前UTC（协调世界时，或格林尼治标准时间）时间——即自1970年1月1日以来经过的毫秒数。我们将使用这个数字来比较任何两次连续访问之间的毫秒时间，从而得知用户两次访问之间经过了多长时间。

通常，您会先将数据保存到sharedObject文件，然后再检索它，但在我们的特殊情况下，我们希望在写入之前先从共享对象中检索信息，否则我们将在有机会比较两者之前，不断用新日期数据覆盖旧日期数据。首先，我们创建一个名为getLastVisit的函数，并执行它以查看用户上次是什么时候访问我们的网站：

```actionscript
function getLastVisit() {
 retrievedObj = sharedObject.getLocal("timeHolder");
 lastVisited = retrievedObj.data.lastVisit;
 plantSize = retrievedObj.data.plantSize;
 firstVisit = retrievedObj.data.firstVisit;
 timeDifference = Math.round((currentTime-lastVisited)/3600000);
 daysSinceLastVisit = Math.ceil(timeDifference/24);
}
```

该函数首先创建一个共享对象的新实例。该实例名为retrievedObj。因此，我们创建一个sharedObject对象的新实例，并从名为timeHolder的sharedObject文件中获取信息。

然后，我们创建一些变量来临时存储从检索到的sharedObject中获取的信息。这些变量是：

- `lastVisited` – 用于以毫秒为单位告诉我们上次访问的时间。
- `plantSize` – 一个数字，用于表示植物的大小。
- `firstVisit` – 一个布尔值，用于告诉我们是否是第一次访问。
- `timeDifference` – 给出自上次访问以来的总小时数。
- `daysSinceLastVisit` – 向上取整自上次访问以来的天数。

之后，我们调用函数getLastVisit：

```actionscript
getLastVisit();
```

