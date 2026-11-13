
第一个选项是：

```
if(newMsgTxt.text.length > 2)
{
}
```

第二个选项，更易于快速理解：

```
if (newMsgTxt.text.length >= 3)
{
}
```

两个选项都能达到相同的结果，但从逻辑角度来看，第二个选项要易读得多。

现在，假设您有一条长度正确的消息，可以继续将消息发送到服务器的过程。接下来的部分是构建对服务器的调用。

```
var variables:URLVariables = new URLVariables();
variables.user = usernameTxt.text;
variables.msg = newMsgTxt.text;
var urlRequest:URLRequest = new URLRequest(phpSendMessage +
getCacheBuster());
urlRequest.method = URLRequestMethod.POST;
urlRequest.data = variables;
var urlLoader:URLLoader = new URLLoader();
urlLoader.addEventListener(Event.COMPLETE, sendMessageHandler);
urlLoader.load(urlRequest);
```

调用服务器时，必须设置一个 URLVariables 对象以传递输入的用户名和消息。还会调用自定义缓存突破函数以确保数据始终是最新的。

发送函数的最后一步是立即添加用户的消息，而不是等待服务器更新消息列表。这使应用程序感觉更灵敏，并且消息不会显得被忽略。

```
addMessage(usernameTxt.text, newMsgTxt.text);
```

此函数接受两个参数：从各自组件中收集的用户名和消息。此信息随后构建为一个 HTML 字符串并分配给 messagesTxt 文本区域。用户名放在粗体标记中以强调名称。实际上，您可以在启用 HTML 的文本框中使用许多常见的 HTML 标记。

```
function addMessage(user:String, msg:String):void
{
 messagesTxt.htmlText += "<b>" + user + "</b>" + ": " + msg +
 "\n";
}
```

表 11.3 显示了可以使用的受支持 HTML 标记。

| Label | HTML Tag |
| :--- | :--- |
| 锚标记 | `<a>` |
| 粗体标记 | `<b>` |
| 换行标记 | `<br>` |
| 字体标记 | `<font>` |
| 图像标记 | `` |
| 斜体标记 | `<i>` |
| 列表项标记 | `<li>` |
| 段落标记 | `<p>` |
| 跨度标记 | `<span>` |
| 下划线标记 | `<u>` |

消息成功发送到服务器后会调用 sendMessageHandler 函数。此函数中唯一重要的部分是最后一行，它清除消息框并允许用户输入新消息。您可以在 send 函数中清除消息，但这样做可以确保消息保持完整，直到您确定它已被添加。

> 如果 SQL 失败，PHP 不会提醒您出错，除非页面未加载。您当然可以为此示例添加更高级的错误处理。

```
function sendMessageHandler(e:Event):void
{
  ...
  newMsgTxt.text = "";
}
```

现在您已完成发送和处理对服务器调用的代码，可以开始编写管理消息并在文本区域中显示它们的函数。

loadMessages() 函数从两个不同的点调用。第一个点是您之前查看过的 init() 函数；第二个是计时器处理程序。

该函数首先检查是否已经进行过另一次加载消息的调用。添加此检查可确保您不会向服务器发送过多请求并可能导致其无响应。如果另一次加载已开始，则只需退出函数并停止处理。

假设另一次加载尚未进行，您设置 loadingMessages 变量，这类似于进入房间后锁门。loadMessages 的大部分功能与发送过程类似。

基本上，您设置要加载的正确 PHP 文件，并为服务器返回消息数据时设置事件处理程序。

```
function loadMessages():void
{
    if(loadingMessages) return;
    loadingMessages = true;
    var urlRequest:URLRequest = new URLRequest(phpLoadMessages +
    getCacheBuster());
    var urlLoader:URLLoader = new URLLoader();
    urlLoader.addEventListener(Event.COMPLETE,
    loadMessagesHandler);
    urlLoader.load(urlRequest);
}
```

## 处理 XML 响应

加载响应函数负责处理 XML 数据并传递要显示的消息。

```
function loadMessagesHandler(e:Event):void
{
    var loader:URLLoader = URLLoader(e.target);
    var xml:XML = new XML(loader.data);
    messagesTxt.htmlText = "";
    for each(var item in xml..message)
    {
        addMessage(item.name, item.msg);
    }
    cacheBuster = getCacheBuster();
    loadingMessages = false;
}
```

> XML 响应中的项名区分大小写。标准是小写或驼峰命名（用于多个单词）。

XML 正确加载并准备就绪后，您设置一个 for...each 循环，就像在第 3 章中加载 XML 示例时使用的一样。该循环基于示例响应中找到的所有 "message" 节点。传回的响应示例如下：

```
<messages>
<message id='29'>
<name>guest1</name>
<msg>Flash is a lot of fun!</msg>
</message>
<message id='30'>
<name>Guest2</name>
<msg>PHP and Flash is better</msg>
</message>
<message id='32'>
<name>guest1</name>
<msg>You can do so many things with it</msg>
</message>
<message id='33'>
<name>guest2</name>
<msg>For sure, just look at this cool chat client</msg>
</message>
</messages>
```

loadMessagesHandler 函数的最后一步是创建一个新的缓存突破值，并将 loadingMessages 变量设置为 false，这允许将来的调用获取最新消息。

缓存突破之前在本节中已解释。但是，有多种方法可以创建唯一字符串。日期始终在变化，ActionScript 有一个 getTime 方法，它返回自 1970 年 1 月 1 日以来的毫秒数。使用此日期方法是因为它不断变化且永不重复，每次调用时都会留下一个唯一字符串。

至此，您已完成聊天应用程序的 ActionScript。以下是供参考的完整代码：

```
var phpPath:String = "http://localhost/ch10/chatClient/";
var phpSendMessage:String = phpPath + "message.php";
var phpLoadMessages:String = phpPath + "getMessages.php";

var loadingMessages:Boolean = false;
var sendingMessage:Boolean = false;
var chatMessages:Array = new Array();

var timer:Timer;
var cacheBuster:String = "?cb=1";

function init():void
{
  // start timer for loading of messages
  timer = new Timer(5000, 0);
  timer.addEventListener(TimerEvent.TIMER, timerHandler);
  timer.start();
  cacheBuster = getCacheBuster();
  loadMessages(); // first time
}

function sendMessage(e:MouseEvent):void
{
  if(usernameTxt.text == "")
  {
    trace("Username required");
    return;
  }

  if(newMsgTxt.text.length >= 3)
  {
    var variables:URLVariables = new URLVariables();
    variables.user = usernameTxt.text;
    variables.msg = newMsgTxt.text;

    var urlRequest:URLRequest = new URLRequest(phpSendMessage +
    getCacheBuster());
    urlRequest.method = URLRequestMethod.POST;
    urlRequest.data = variables;

    var urlLoader:URLLoader = new URLLoader();
    urlLoader.addEventListener(Event.COMPLETE,
    sendMessageHandler);
    urlLoader.load(urlRequest);

    // force message into display
    addMessage(usernameTxt.text, newMsgTxt.text);
  }
}

function sendMessageHandler(e:Event):void
{
  var loader:URLLoader = URLLoader(e.target);
  var variables:URLVariables = new URLVariables(loader.data);
  trace("Response: " + variables.resp);

  // clear message box
  newMsgTxt.text = "";
}

function loadMessages():void
{
  if(loadingMessages) return;
  loadingMessages = true;

  var urlRequest:URLRequest = new URLRequest(phpLoadMessages +
      getCacheBuster());
  var urlLoader:URLLoader = new URLLoader();

  urlLoader.addEventListener(Event.COMPLETE,
      loadMessagesHandler);
  urlLoader.load(urlRequest);
}

function loadMessagesHandler(e:Event):void
{
    var loader:URLLoader = URLLoader(e.target);
    var xml:XML = new XML(loader.data);

    loadingMessages = false;
    messagesTxt.htmlText = "";

    for each(var item in xml..message)
    {
        addMessage(item.name, item.msg);
    }

    cacheBuster = getCacheBuster();
}

function getCacheBuster():String
{
    var date:Date = new Date();
    cacheBuster = "?cb=" + date.getTime();
    return cacheBuster;
}

function addMessage(user:String, msg:String):void
{
    messagesTxt.htmlText += "<b>" + user + "</b>" + ": " + msg +
        "\n";
}

function timerHandler(e:TimerEvent):void
{
    trace("Timer hit");
    loadMessages();
}

sendBtn.addEventListener(MouseEvent.CLICK, sendMessage);

init();
```
