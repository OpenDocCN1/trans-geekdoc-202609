

| 什么 | 定义应用程序将执行的操作 |
| --- | --- |
| 谁 | 应用程序的目标受众 |
| 如何 | 开发应用程序所使用的技术 |

以下示例跳过“如何”步骤，因为这是一本关于 Flash 和 PHP 的书。一旦定义了“如何”，就可以思考“谁”了。当然，这就是你的目标受众。应用程序并不总是有严格定义的“谁”，尤其是当它是服务型网站时，但最好还是定义一个。确定目标受众的最佳方法是思考应用程序的类型。例如，它是电子商务应用程序还是视频播放器。知道谁将使用应用程序对其成功至关重要。

既然“如何”和“谁”都已定义，你就可以思考应用程序到底会做什么了。你绝不会去五金店，买下所有材料，然后再决定要建造什么。开发应用程序也是一样。当你开始遵循这些实践时，它们就会变得驾轻就熟。

## 了解应用程序设计

评估阶段完成后，你自然会进入设计阶段。但是，就像评估阶段一样，首先规划总是个好主意。这可以是用纸和铅笔绘制草图，或者使用 Flash 中的基本形状。例如，图 11.1 显示了一个示例草图。

## 使用伪代码

在开发好应用程序的整体布局后，你可以继续进行功能开发。这就是你开始编写伪代码的地方，例如函数、变量、事件以及应用程序中将使用的任何其他概念。以下是用户管理程序的伪代码示例。

```
// Pseudo-code

function loadUser(id:uint):void
{
  // make call to server passing
  // along the id as the user id
}
function handleServerResponse(e:Event):void
{
  // capture server response
  // make necessary calls to application
}

function drawInterface():void
{
// paint "draw" the interface that
// the user will interact with
}
function redraw():void
{
// redraw interface as info is loaded,
// to keep things up to date
}
// Assign event handlers
```

你会发现伪代码并不是完整的应用程序，而是整个应用程序的骨架。这使你能够快速开发应用程序的工作方式和功能。在开发大型应用程序时，编写伪代码变得更加重要，但无论项目规模如何，评估、草图和规划都是良好的实践。

图 11.1
使用 Flash 基本形状的示例应用程序草图

![](img/d9d48cd53eee0fbc1ebc363c322fac2c_262_0.png)

## 完成规划阶段

规划应用程序的最后一步并非最终确定，因为你既可以结束规划阶段，也可以开始开发过程。如果已指定客户或创意总监，有时这一选择由他们决定。

在规划过程的这个阶段，你已确定应用程序将做什么、谁将使用它以及如何构建它。你还设计了布局并开始了编程过程。下一步取决于你作为开发人员。你可以继续并完成设计过程，也可以开始开发应用程序将使用的代码。

通常，你会设计足够的应用程序内容以开始编程，因为随着开发的继续，事情多半会发生变化。但是，通过适当的规划，你可以最大限度地减少这些修订阶段。

## 开发聊天客户端

现在你已了解应用程序开发的最佳实践，可以开始开发第一个完整的应用程序。此应用程序将是一个使用 PHP 与 MySQL 数据库交互的 Flash 聊天客户端。开发完基本应用程序后，你将继续添加功能，并探讨构建可扩展应用程序的最佳方式。

可扩展应用程序的开发会牢记这一点：最初可能只有两个用户使用该应用程序，但随着时间的推移，数百万用户也可能轻松使用它。其理念是考虑到这一点，并以允许扩展的方式开发应用程序。

### Flash 部分

你开始这个项目是通过设计应用程序。对于此应用程序，设计已提供，但请随意修改。事实上，我们鼓励你扩展所有示例，这既是你熟悉新概念的方式，也是你作为开发人员成长的方式。图 11.2 显示了聊天应用程序的界面。

基本上，界面由一个 TextArea 组件组成，用于显示聊天消息；两个 TextInput 组件分别用于消息和用户名项目；以及一个 Button 实例用作提交按钮。

图 11.2
使用 Flash 预构建组件构建的聊天应用程序设计

![](img/d9d48cd53eee0fbc1ebc363c322fac2c_264_0.png)

表 11.2 显示每个组件的实例名称。

表 11.2
组件的实例名称

| 组件 | 实例名称 | 结果 |
|---|---|---|
| TextArea | messagesTxt | 显示聊天消息 |
| TextInput | newMsgTxt | 新消息 |
| TextInput | usernameTxt | 聊天人员姓名 |
| Button | sendBtn | 将新消息发送到服务器 |

在开发聊天应用程序的 ActionScript 期间，你将引用这些实例名称。

完成用户界面“设计”部分（或在此情况下加载）后，你可以开始代码开发。

聊天应用程序代码的第一部分是贯穿始终使用的一组变量。第一个变量是 PHP 文件的绝对路径。接下来的两个变量是负责从数据库发送和加载聊天消息的 PHP 文件。之后是两个布尔变量，用于确保无法进行多次消息调用。最后一组变量是对 Timer 对象和缓存突破器的引用。

```
var phpPath:String = "http://localhost/ch10/chatClient/";
var phpSendMessage:String = phpPath + "message.php";
var phpLoadMessages:String = phpPath + "getMessages.php";

var loadingMessages:Boolean = false;
var sendingMessage:Boolean = false;

var timer:Timer;
var cacheBuster:String = "?cb=1";
```

你将构建的第一个函数是 init() 或初始化函数。它只在应用程序启动时调用一次。它负责设置从服务器加载消息的计时器处理程序，并进行第一次缓存突破器调用（将在下一节中解释）。init() 函数的最后一个操作是调用 loadMessages 函数并填充消息列表。

```
function init():void
{
    // start timer for loading of messages
    timer = new Timer(5000, 0);
    timer.addEventListener(TimerEvent.TIMER, timerHandler);
    timer.start();

    cacheBuster = getCacheBuster();
    loadMessages(); // first time
}
```

Timer 类随 Flash 一起提供，有很多很好的用途。此示例利用 TIMER 事件，每次倒计时结束时都会调用该事件。倒计时时间和重复次数会传递给构造函数。将倒计时设置为 5000（即 5 秒），重复次数设置为 0，这实际上告诉 ActionScript 连续重复。创建新的 Timer 实例后，你会分配事件处理程序并立即启动计时器。计时器处理程序只是调用 loadMessages 函数。

这部分代码可以通过将 `loadMessages` 函数直接放在 `timerHandler` 的位置来精简，但以这种方式操作可以让我们日后添加更多功能。为事件创建适当的处理程序始终是良好的开发实践，这样代码就可以更新，并且整体可读性也高得多。

```actionscript
function timerHandler(e:TimerEvent):void
{
    loadMessages();
}
```

`loadMessages` 函数负责调用并处理来自服务器的响应。对服务器的调用与其他示例非常相似，只是有几个新元素。其中一个新元素是 `cacheBuster` 变量，用于确保我们不会收到缓存的结果。

### 使用动态数据停止缓存

你刚刚创建了一个用于停止缓存的变量，但这究竟是什么？服务器上的缓存是指存储动态数据以加快所有未来调用的加载速度。乍一看这似乎是个好主意，在大多数情况下也是如此。但是，在加载不断变化的聊天数据的示例中，可以说你希望这些数据是新鲜的。这是通过添加一个被称为“缓存突破器”的变量来实现的，它会欺骗浏览器，让其认为对同一文件的每次调用都是不同的。

以下是一个非常简单的缓存突破器示例以及发送到服务器的实际字符串：

```actionscript
function getRandom(length:uint):void
{
    return Math.round(Math.random() * (length - 1)) + 1;
}

var rand:String = "?cb=" + getRandom(8);
var php:String = "http://localhost/ch04/getMessages.php" + rand;

trace("URL: " + phpFile); // getMessages.php?cb=65378426
```

**注意** 缓存突破器会增加下载时间，并强制任何带有缓存突破器的文件在每次请求时都被下载。

URL 中 `?` 之后的所有内容都告诉浏览器和服务器，该调用是动态的，因此文件不会被缓存。

发送消息流程的下一部分是确保消息至少为三个字符长。如果消息不足三个字符，将显示错误消息。你可以用两种方式编写此条件检查。

