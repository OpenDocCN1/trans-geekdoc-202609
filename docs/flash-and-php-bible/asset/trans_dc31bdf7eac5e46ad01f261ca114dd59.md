
当按下 Enter 键时，会调用 dispatchEvent，强制点击提交按钮。

```
function keyDownHandler(e:KeyboardEvent):void
{
    if(e.keyCode == Keyboard.ENTER)
    {
        sendBtn.dispatchEvent(new MouseEvent(MouseEvent.CLICK));
    }
}
```

## 提交消息处理程序

键盘处理程序会调用提交按钮的单击事件，该事件分配给以下函数。该函数检查 msgTxt 文本输入框的长度，如果长度大于零，则准备并发送消息。

该函数的最后一步是清空消息框，以确保不会重复发送相同的消息。你可以将此清除代码添加到状态处理程序中。这样在确认消息已发送后会清空该字段。这使你能够保留消息，并避免因网络故障导致消息丢失。

```
function sendButtonHandler(e:MouseEvent):void
{
    if(msgTxt.text.length > 0)
    {
        writeLine(msgTxt.text);
        clearBtn.dispatchEvent(new MouseEvent(MouseEvent.CLICK));
    }
}
```

## 清除消息输入

每当需要清除文本输入字段并禁用提交按钮（直到输入新消息）时，都会调用 clearButtonHandler 函数。在下一节分发 CHANGE 事件时，按钮将被禁用。

```
function clearButtonHandler(e:MouseEvent):void
{
    msgTxt.text = "";
    msgTxt.dispatchEvent(new Event(Event.CHANGE));
}
```

## 检查文本输入长度

当输入新消息或清空输入框时，会对 msgTxt 框调用 CHANGE 事件。该事件负责检查输入框中文本的长度，并根据长度检查结果启用或禁用提交按钮和清除按钮，如图 8.5 所示。

```
function inputHandler(e:Event):void
{
    if(e.target.text.length > 0)
    {
        clearBtn.enabled = true;
        sendBtn.enabled = true;
    }
    else
    {
        clearBtn.enabled = false;
        sendBtn.enabled = false;
    }
}
```

## 图 8.5

显示应用处于禁用状态

![](img/d9d48cd53eee0fbc1ebc363c322fac2c_202_0.png)

## 保持界面稳定

要创建稳定的应用程序，在没有连接时应禁用界面和按钮。

```
function enableInterface():void
{
    msgTxt.enabled = true;
    bodyTxt.enabled = true;
}

function disableInterface():void
{
    bodyTxt.editable = false;
    msgTxt.enabled = false;
    clearBtn.enabled = false;
    sendBtn.enabled = false;
}
```

这些启用和禁用函数会根据活动连接的结果，从代码的其他部分调用。例如，disableInterface 函数由 closeHandler 调用，该处理程序在活动连接终止时分发。

```
function closeHandler(event:Event):void
{
...
 disableInterface();
}
```

## 发送初始请求

建立连接时会调用 sendRequest 函数。该函数向状态函数发送数据，并清除套接字连接中任何现有的排队信息。

```
function sendRequest() :void
{
 statusMessage("Send initial request to [" + host + "]",
 "#006600");
 socket.flush();
 enableInterface();
}
```

## 向套接字服务器发送消息

将消息实际发送到套接字服务器的过程由 writeLine 函数处理。此 writeLine 函数由前一部分代码中定义的输入和提交处理程序调用。

```
function writeLine(str:String):void
{
 ...
}
```

函数的第一部分是在消息末尾追加一个新行，你可能记得这是 PHP 中的消息结束标志。

```
str += "\n";
```

该函数还采用 try-catch 编程风格，以确保发送过程中的错误被正确捕获并对用户隐藏。为简单起见，错误会在输出窗口中显示。在更真实的应用程序中，你可能希望在消息未发送时通知用户，并存储消息以便稍后尝试重新发送。

```
try
{
	socket.writeUTFBytes(str);
}
catch(e:IOError)
{
	trace(e);
}
```

## 处理状态更新

此应用程序有一个状态框，用于通知用户可能的连接或消息问题。所有这些状态更新都发送到 statusMessage 函数，该函数将其输入状态框并相应地上色。

```
function statusMessage(str:String, color:String="#000000"):void
{
	statusTxt.htmlText += "<font color=\""
	+ color + "\">"
	+ str + "</font>";
}
```

如果调用者忘记定义颜色，将应用默认颜色。未包含默认颜色可能导致文本未被添加。

此基于套接字的聊天应用程序中的最后一个函数，在从套接字服务器接收到新消息时调用。

```
function readResponse():void
{
}
```

该函数的第一部分从 socket 类检索新消息并将其分配给 str 变量，该变量在函数的其余部分中使用。

```
var str:String = socket.readUTFBytes(socket.bytesAvailable);
```

在显示消息之前，必须删除可能影响文本显示方式的任何额外换行符。这是使用非常基本的 substring 函数来完成的，该函数返回不包括最后两个字符的消息，在此情况下即 "\r\n"。

```
// strip off line feeds
if(str.substring((str.length-2), str.length) == "\r\n")
{
	trace("found \\n\\r");
	str = str.substring(0, (str.length-2));
}
```

删除换行符后，下一步是确定该消息是否来自管理员。此示例允许任何 *用户* 成为管理员。在更完整的应用程序中，你可能希望在使用管理员账户之前要求登录。如果消息来自管理员，则消息内容会显示为红色，以便管理员消息更加突出。

```
if(str.substring(0, 12) == "ADMIN NOTICE")
{
    bodyTxt.htmlText += "<font color=\"#FF0000\">" + str +
        "</font>";
}
```

如果消息是标准消息，则将其简单地添加到文本区域中，函数结束，等待检索下一条消息。

```
else
{
    bodyTxt.htmlText += "<font color=\"#000000\">" + str +
        "</font>";
}
```

这就是基于 PHP 套接字服务器的 Flash 聊天客户端的全部内容。此时，你可以启动套接字服务器（除非它已经在运行）并测试聊天客户端，如图 8.6 所示。由于该系统旨在支持多个连接，你可以叫上几个朋友来测试。

或者，你可以修改代码以允许远程连接，并通过发送 Flash 应用程序的链接让许多用户连接。

以下是聊天客户端示例的完整代码：

```
var host:String = "127.0.0.1";
var port:uint = 8888;

var socket:Socket = new Socket(host, port);

socket.addEventListener(Event.CLOSE, closeHandler);
socket.addEventListener(Event.CONNECT, connectHandler);
socket.addEventListener(IOErrorEvent.IO_ERROR, ioErrorHandler);
socket.addEventListener(SecurityErrorEvent.SECURITY_ERROR,
    securityErrorHandler);
socket.addEventListener(ProgressEvent.SOCKET_DATA, sockHandler);
msgTxt.addEventListener(Event.CHANGE, inputHandler);
addEventListener(KeyboardEvent.KEY_DOWN, keyDownHandler);

clearBtn.addEventListener(MouseEvent.CLICK, clearButtonHandler);
sendBtn.addEventListener(MouseEvent.CLICK, sendButtonHandler);

this.align = StageAlign.TOP_LEFT;
this.scaleMode = StageScaleMode.NO_SCALE;

function writeLine(str:String):void
{
    str += "\n";
    try
    {
        socket.writeUTFBytes(str);
    }
    catch(e:IOError)
    {
        trace(e);
    }
}

function sendRequest():void
{
    statusMessage("Send initial request to [" + host + "]",
        "#006600");
    socket.flush();
    enableInterface();
}

function readResponse():void
{
    var str:String = socket.readUTFBytes(socket.bytesAvailable);

    // strip off line feeds
    if(str.substring((str.length-2), str.length) == "\r\n")
    {
        trace("found \\n\\r");
        str = str.substring(0, (str.length-2));
    }

    if(str.substring(0, 12) == "ADMIN NOTICE")
    {
        bodyTxt.htmlText += "<font color=\"#FF0000\">" + str +
            "</font>";
    }
    else
```
