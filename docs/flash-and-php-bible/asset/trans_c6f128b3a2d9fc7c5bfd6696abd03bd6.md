

你可能还记得，在这个示例的 PHP 部分中，数据是以名称/值对形式返回的。这些数据存储在新创建的加载器实例的 data 属性中。

这些数据被传递到 URLVariables 类的一个实例中，该类会创建一个 ActionScript 对象，以便脚本的其他部分可以处理数据。

```
var dataObj:URLVariables = new URLVariables(loader.data);
```

数据加载完成后，你可以使用简单的 trace 语句进行测试，该语句应显示返回的总条目数。

```
trace("Total Albums: " + dataObj.total);
```

该 trace 调用应在输出面板中显示以下内容：

```
//Output: **Total Albums: 5**
```

这意味着 PHP 文件正在被调用，数据正在使用 PHP 作为中间数据处理器，从数据库中正确加载。

你可以在这里结束脚本，因为一切都正常工作，但继续使用 for.. 循环，通过一系列 trace 调用来简单地显示每张专辑的信息。

for.. 循环是使用 dataObj 的 total 属性来设置的，以确定循环应运行多少次。

```
for(var i:uint = 0; i < dataObj.total; i++)
{
...
}
```

for.. 循环中的第一条 trace 语句显示当前正在显示的专辑。当前专辑编号是使用循环的 i 变量并加 1 创建的。这样做是因为 i 变量从零开始，而为了显示目的，第一张专辑应该是 1。

```
trace("Album " + (i + 1));
```

下一条 trace 语句设置为显示当前艺术家。该值是使用动态对象引用从 dataObj 对象实例中捕获的。"artist" 名称附加到 i 变量，从而创建一个实例名称。

```
trace(" Artist: " + dataObj['artist' + i]);
```

剩余的 trace 语句是前一条语句的副本，仅对实例名称和描述做了轻微修改。

```
trace(" Album: " + dataObj['album' + i]);
trace(" Genre: " + dataObj['genre' + i]);
```

此时，循环已完成，整个示例应用程序也已完成。你现在可以测试示例，并应该在输出面板中看到显示的 trace 语句，如图 3.4 所示。

## 图 3.4

以下是在输出面板中显示的专辑数据示例。

![](img/d9d48cd53eee0fbc1ebc363c322fac2c_104_0.png)

此应用程序的完整 ActionScript 部分如下：

```
var phpFile:String = "http://localhost/getAlbums.php";

function loadHandler():void
{
   var urlRequest:URLRequest = new URLRequest(phpFile);

   var urlLoader:URLLoader = new URLLoader();
   urlLoader.addEventListener(Event.COMPLETE, callServerHandler);
   urlLoader.load(urlRequest);
}

function callServerHandler(e:Event):void
{

   var loader:URLLoader = URLLoader(e.target);

   var dataObj:URLVariables = new URLVariables(loader.data);

   // Simple trace for example
}
```

```
actionscript
for(var i:uint = 0; i < dataObj.total; i++)
{
    trace("Album " + (i + 1));

    trace(" Artist: " + dataObj['artist' + i]);
    trace(" Album: " + dataObj['album' + i]);
    trace(" Genre: " + dataObj['genre' + i]);
}
}
loadHandler();
loadHandler();
```

## 摘要

前一个示例应该已经让你很好地理解了如何在 Flash 中使用 PHP 作为中间脚本来操作 MySQL 数据库。你可以在此示例的基础上扩展，创建更强大的应用程序，因为此示例应用程序是用来说明概念的，并未侧重于显示或应用程序本身。

MySQL 数据只是可以在 Flash 中显示的数据的一个示例。

下一章将在此示例基础上扩展，并介绍更高级的数据对象，例如 XML，以及图像和文本文件等其他形式的数据。

## 第 4 章

### 使用数据

使用数据是发送和加载信息供 ActionScript 解释的过程。ActionScript 中可使用的数据有两种类型：静态和动态。

在大多数常见情况下，首选动态过程而非静态过程。这主要是因为动态数据通常包含数据库组件。

本章介绍如何在 Flash 和 PHP 中使用动态数据。你将从加载简单文本文件开始，然后转到 XML 和更高级的加载。本章以一个完整的演示应用程序结束，该应用程序加载图像数据以显示缩略图和常规尺寸图像。

- 如何加载数据
- 发送数据
- 加载 XML
- 使用 PHP 加载图像

### 在 Flash 中加载数据

在 Flash 中加载数据是一种非常普遍的做法。在几乎每个项目中，你都希望有动态（可更新）的部分。动态数据的目的是限制所需的更新量。例如，如果你查看新闻网站，你会发现大部分外部内容不会更改（徽标、导航等）。Flash 应用程序也是如此，你很可能只有一部分需要实际更新。本节将引导你完成从 XML 到图像和声音加载数据的过程。

在 Flash 中加载数据的过程很快就会变得熟悉，因为你要加载的大多数数据类型都有类似的要求。

首先来看一个加载文本文件的简单示例。此示例将根据应用程序的运行位置，在几个不同的位置查找文本文件。如果在 Flash IDE 中执行此代码，它将查找 FLA 保存的同一位置，或者如果文件未保存，则在用户的临时目录中查找。如果代码位于编译的 SWF 中，文本文件将从 SWF 存储的同一目录加载。

```
var txtFile:String = "sample.txt";
var urlRequest:URLRequest = new URLRequest(txtFile);
var loader:URLLoader = new URLLoader();
loader.addEventListener(Event.COMPLETE, loadHandler);
loader.load(urlRequest);

function loadHandler(e:Event):void
{
    var loader:URLLoader = URLLoader(e.target);
    trace("Loaded Data: " + loader.data);
}
```

前一个示例加载 "sample.txt" 文件，并将其所有内容跟踪到 Flash 输出面板，该面板会自动打开。打开或关闭输出面板的另一种方法是选择 Window➤Output。

### 了解用于加载数据的类

Flash 中的 ActionScript 具有一系列用于加载数据的预构建类。以下部分将解释每个类的功能。

### URLRequest

此类用于设置要加载的文件。你可以将其直接赋值给变量，或者为了保持代码更紧凑，将其直接赋值给 URLLoader 的 load() 中。事实上，你可以将此过程应用于许多类。这不会影响类的功能，也不是必需的步骤。

```
...
    loader.load(new URLRequest(txtFile));
```

### URLLoader

正如 Adobe Live Docs 所述，“URLLoader 类以文本、二进制数据或 URL 编码变量的形式从 URL 下载数据。它有助于下载文本文件、XML 或其他信息，用于动态的数据驱动应用程序。”

在 ActionScript 中发送和加载数据时，URLLoader 服务于两个目的。URLLoader 的第一个目的是设置完成处理程序。另一个目的是在完成处理程序中捕获加载的数据。第二个目的的一个显著区别是，URLLoader 前面没有 new 关键字。

### 设置回调

设置数据加载器的最后一步是回调。回调是数据完全加载时调用的“处理程序”函数的另一个名称。此函数分配给 URLLoader 类上的 Event.COMPLETE 事件。

```
var loader:URLLoader = new URLLoader();
loader.addEventListener(Event.COMPLETE, loadHandler);
```

此回调函数需要一个 Event 类型的参数，当调用 ActionScript 时会自动传入该参数。此参数是存储加载数据内容的位置。

如果忘记在事件处理程序中包含该参数，你会收到参数数量不匹配错误。

```
ArgumentError: Error #1063: Argument count mismatch on
sendtophp_fla::MainTimeline/serverResponse(). Expected 0,
got 1.
at flash.events::EventDispatcher/dispatchEventFunction()
at flash.events::EventDispatcher/dispatchEvent()
at flash.net::URLLoader/onComplete()
```

### 综合起来

既然你了解了使用 ActionScript 加载数据的代码如何工作，现在可以继续了解更具体的发送和加载示例。在此示例中，你可以基于 URLLoader 类进行实验和构建，因为它拥有的事件远比你使用的简单 COMPLETE 事件多。例如，当加载或发送失败时会调用 IOError 事件。各种事件的代码基本相同；对于你的 IOError 示例，它看起来像这样：

```
var loader:URLLoader = new URLLoader();
loader.addEventListener(Event.COMPLETE, ioHandler);
function ioHandler(e:Event):void
{
trace("File loading was terminated");
}
```

你会很快注意到，唯一改变的是事件字符串和处理程序函数。还可以分配多个事件，保持高度兼容性通常也是个好主意。如果设置了适当的事件，你还可以快速调试代码。

### 分配多个事件

假设你想处理加载器实例的 IOError 和 Complete 事件。你可以输入每个事件处理程序；但是，在处理多个加载器时，这可能会变成一个漫长的过程。实现预期结果的一种方法是使用函数来分配处理程序。你基本上将目标作为参数传入，并动态分配事件处理程序。

```
var txtFile:String = "sample.txt";
var urlRequest:URLRequest = new URLRequest(txtFile);
```

