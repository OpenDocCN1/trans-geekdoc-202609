

```
timer = new Timer(1, 0);
timer.addEventListener(TimerEvent.TIMER, tickHandler);
timer.start();
timerMC.alpha = 1.0;
}
```

上一节中的事件处理程序为每次计时器调用分配一个函数。该函数就是该处理程序。传入的参数是对计时器对象的引用。你也可以引用全局 Event；不过，如果你将来再次查看此代码，这样会更容易理解。

```
function tickHandler(e:TimerEvent):void
{
    var time:Timer = e.target as Timer;
    var milli:uint = (startingTime - getTimer());
    var sec:uint = Math.round(milli / 1000);
    timerMC.timerTxt.text = String(sec)
    + ((sec == 1) ? " second" : " seconds");
    if(sec == 0)
    {
        timer.stop();
        stage.removeChildAt(0);
    }
}
```

事件对象的目标被转换为 Timer。同样，此步骤不是必需的，但有助于更轻松地使用代码。

其理念是显示剩余秒数，该秒数使用剩余毫秒数确定。剩余毫秒数通过 getTimer() 函数获取，该函数返回当前电影运行的毫秒数。用 startingTime 减去该值，结果即为总毫秒数。

```
var milli:uint = (startingTime - getTimer());
```

> 注意 getTimer() 函数始终返回当前电影运行的总时间。这意味着如果在播放过程中稍后执行此测试，该值将不会正确显示。

然后使用一些基本数学将剩余毫秒转换为秒。milli 变量的当前值除以 1000 即等于剩余秒数。

```
var sec:uint = Math.round(milli / 1000);
```

确定秒数后，该值会发送到舞台上的 timerTxt 文本字段。为了正确的语法显示，使用 sec 变量来确定应显示 "second" 还是 "seconds"。在每次运行此函数时都会测试该 sec 变量，以确定何时停止计时器并卸载整个应用程序。

```
if(sec == 0)
{
	timer.stop();
	stage.removeChildAt(0);
}
```

## 卸载应用程序

卸载整个应用程序的操作是通过在 Stage 实例上调用 removeChildAt 来完成的。在这种情况下，应移除整个电影，因此传入 0 表示从索引 0 开始向下移除。

```
if(sec == 0)
{
	timer.stop();
	stage.removeChildAt(0);
}
```

代码的最后一步是调用 init，它会启动整个过程。

```
init();
```

这是完整的应用程序，当当前沙箱为本地时它将运行。你可以调整此应用程序中的整体逻辑并将其添加到你自己的应用中，以确保你的电影不会被不当运行。

以下是完成后的代码：

```
var timer:Timer;
var sandbox:String;
var startingTime:uint = 5;
function init():void
{
	timerMC.alpha = 0;
	sandbox = Security.sandboxType;
	if(sandbox.indexOf('local') == -1)
	{
		startTimer();
	}
}
function startTimer():void
{
startingTime *= 1000;
timer = new Timer(1, 0);
timer.addEventListener(TimerEvent.TIMER, tickHandler);
timer.start();
timerMC.alpha = 1.0;
}
```

```
function tickHandler(e:TimerEvent):void
{
var time:Timer = e.target as Timer;

var milli:uint = (startingTime - getTimer());
var sec:uint = Math.round(milli / 1000);

timerMC.timerTxt.text = String(sec)
+ ((sec == 1) ? " second" : " seconds");

if(sec == 0)
{
timer.stop();
stage.removeChildAt(0);
}
}
```

```
init();
```

到此，你应该很好地了解 Flash 安全沙箱的工作原理及其含义。如你所见，沙箱在某些情况下可能会带来问题，但总体而言，其目的是保护用户。在上一个示例中，代码已被扩展，现在沙箱既能保护内容所有者，也能保护用户。

你可以将本节学到的实践和技术应用到你自己的应用程序中。

## 确保应用程序无法共享

作为本节的补充内容，最后一个示例将创建类似的沙箱风格检查，但这次的目标是：电影只能在其构建所在的网站上观看，不能在任何其他网站上观看。

这是通过使用 loaderInfo 对象上的 url 属性来实现的。该属性可在任何加载的对象上访问。在此示例中，加载的对象将是舞台，因为它是根显示对象。用于确定电影当前运行位置的代码是：

```
stage.loaderInfo.url
```

此代码返回一个字符串，显示电影运行的位置。本地运行的电影示例响应将是：

```
file:///MacPro%20HD/Library/Server/Documents/DomainCheck.swf
```

使用此属性，你可以像在沙箱测试中那样显示警告消息。为演示目的，提供了一个无效域以导致电影立即移除。

```
if (String(stage.loaderInfo.url).indexOf('example.org') != -1)
{
stage.removeChildAt(0);
}
```

假设上述代码在不位于 example.org 域上的电影中运行，电影将移除自身，应用程序将不再可访问。为了构建更完整的应用程序，你将检查网站的 www 和非 www 版本。你也可以扩展此代码并检查有效站点列表，这可以通过简单的 for 循环和允许域的数组来实现。

> 注意 由于访问 url 的限制，此检查并非 100% 安全。

现在你应该了解如何保护你的应用程序，并添加一层保护以防止其他站点和位置未经许可从你的内容中获益。

## 摘要

在本章中，你学会了如何正确清理用户数据，同时意识到它可能如何影响应用程序功能。接着，你学习了如何正确加载和清理用户数据，以确保存储过程不会受损。随后介绍了存储安全数据，并举例说明了简单的 SQL 调用如何在你的应用程序中引起麻烦。

引入的下一步是将数据返回到 Flash 并分析这些数据，以确保它们被正确处理。

最后一节介绍并概述了 Flash 沙箱及其可能对你的应用程序产生的影响。作为补充内容，你学习了如何创建一个应用程序，如果它不在正确的域上运行，它将移除自身。

## 第 8 章
### 使用套接字

- 本章内容
- 了解套接字
- 在 PHP 中使用套接字
- 在 Flash 中使用套接字
- 使用 Flash 和 PHP 构建基于套接字的聊天客户端

在使用多用户应用程序时，有多种发送和接收数据的方式。你可以使用基于 XML 的传递方法。标准传递的另一种替代方案是构建一个“拉取”应用程序，使用计时器检查更新。

套接字允许“推送”方法，去除了计时器，仅在发送新数据时更新。套接字的使用不仅限于简单数据；你实际上可以构建一个多用户绘图应用程序，它会将坐标传递给各个已登录的客户端。

本章分为两部分。第一部分解释套接字。第二部分是一个基于 Flash 的聊天应用程序，使用套接字作为消息的传递方式。

### 了解套接字

套接字是通信端点，或网络中连接到同一协议上另一台计算机的计算机部分。传统连接（Internet）与套接字之间的区别在于能够区分你正在与哪些机器通信。

当你从 Internet 请求网站时，你会收到请求的页面，但 Internet 不能在你再次请求之前直接将新数据推送到你（客户端）。

套接字通过允许主连接向你（客户端）发送新数据来提供这种直接通信。这最常用于直接连接的应用程序，例如即时通讯器、视频应用程序和团队协作环境。

