

var urlRequest:URLRequest = new URLRequest(serverFile);
navigateToURL(urlRequest, "_blank");

window 参数可以接受以下字符串之一，如表 3.1 所示。

| 链接的窗口目标 | |
|---|---|
| "_self" | 当前窗口中的当前帧 |
| "_blank" | 新窗口 |
| "_parent" | 当前帧的父帧 |
| "_top" | 当前窗口中的顶级帧 |

window 参数还可以接受自定义名称，例如帧或特定窗口的名称。例如，假设您要将链接发送到名为 "childWindowBox" 的窗口，代码如下所示：

```
var serverFile:String = "http://localhost/callLink.php";
var urlRequest:URLRequest = new URLRequest(serverFile);
navigateToURL(urlRequest, "_childWindowBox");
```

您替换预构建的窗口名称并添加自定义名称。虽然这是一项小更改，但它提供了一些很棒的附加功能。

打开新窗口或现有窗口只是与其他数据连接的可能性之一。

Flash 中另一种单向通信类型可以通过使用 sendToURL() 执行。

sendToURL() 用于与脚本进行静默通信。静默通信是一种单向通信形式，不会加载单独的网页。这种通信形式可以在不干扰用户浏览体验的情况下向服务器发送数据。

以下是之前的示例，添加了新函数，并包含一些基本错误处理来管理无效和不可用的请求。

```
var serverFile:String = "http://localhost/callLink.php";
var urlRequest:URLRequest = new URLRequest(serverFile);
try
{
    sendToURL(urlRequest);
}
catch (e:Error)
{
 // handle error here
}
```

## 向服务器发送数据

有时，您可能不仅希望静默请求 URL，还希望随请求一起发送数据。这是通过使用 URLVariables 类来完成的，该类允许您创建名称/值对对象。这些名称/值对与标准 HTML 请求中的相同。

```
var serverFile:String = "http://localhost/callLink.php";

var variables:URLVariables = new URLVariables();
variables.id = 1004;
variables.user = "James";

var urlRequest:URLRequest = new URLRequest(serverFile);
urlRequest.data = variables;

try
{
 sendToURL(urlRequest);
}
catch (e:Error)
{
 // handle error here
}
```

单向通信的另一个示例是向服务器盲发 POST 数据。这通过从 URL 中删除参数，为您的应用程序增加了一点更多的安全性，方法是将参数包含在请求中。

POST 数据请求的代码只是将值赋给 URLRequest 实例的 method 属性。ActionScript 在 URLRequestMethod 类上有一个静态变量，该变量将被赋给 method 变量。

```
var serverFile:String = "http://localhost/callLink.php";

var variables:URLVariables = new URLVariables();
variables.id = 1004;
variables.user = "James";

var urlRequest:URLRequest = new URLRequest(serverFile);
urlRequest.method = URLRequestMethod.POST;
urlRequest.data = variables;

try
{
 sendToURL(urlRequest);
}
catch (e:Error)
{
    // handle error here
}
```

以下是将发送到服务器的示例请求。如您所见，Content 和 POST 元素包含所发送的信息。请求的其余部分是标准数据属性，不特定于本示例。

```
POST /callLink.php HTTP/1.1
Accept-Language: en
Accept-Encoding: gzip, deflate
Cookie: login=usernames;session-id=1206701
Referer: http://www.example.org/
User-Agent: Mozilla/5.0 (Macintosh; U; Intel Mac OS X; en)
AppleWebKit/522.11.1 (KHTML, like Gecko) Version/3.0.3
Safari/522.12.1
Content: id=1004&user=James
Content-Type: application/x-www-form-urlencoded
Accept: text/xml, text/html;q=0.9, text/plain;q=0.8, image/png
Pragma: no-cache
Content-Length: 327
Connection: keep-alive
Host: www.example.org
```

## 双向通信

在某些情况下，您在发送数据时希望收到响应。例如，尝试从数据库加载特定用户的数据时。您会传递用户 ID，并期望收到包含该用户信息的某种数据类型。

双向通信的响应通过分配事件侦听器并附加处理程序函数来处理。

```
var serverFile:String = "http://localhost/callLink.php";
var variables:URLVariables = new URLVariables();
variables.id = 1004;
variables.user = "James";
var urlRequest:URLRequest = new URLRequest(serverFile);
urlRequest.method = URLRequestMethod.POST;
urlRequest.data = variables;
var urlLoader:URLLoader = new URLLoader();
urlLoader.addEventListener(Event.COMPLETE, userResponseHandler);
try {
    urlLoader.load(urlRequest);
} catch (e:Error) {
    //handle error here
}
}

// handler function
function userResponseHandler(e:Event):void
{
    var urlLoader:URLLoader = URLLoader(e.target);
    var args:URLVariables = new URLVariables(urlLoader.data);

    trace("User Data: " + args.response);
}
```

响应函数接收对 Event 的引用。URLLoader 和 URLVariables 实例处理拆分响应并仅返回发回数据的过程。响应会随其他值和参数一起返回，但大多数时候，您只会关注 URLLoader 实例的 data 属性。

更完整的应用程序通常返回 XML 格式，这在第 3 章的其他各种数据加载示例中有所介绍。

既然您了解了如何使用单向通信和双向通信，下一节将通过连接到 PHP 来扩展这些做法。

## 将 Flash 连接到 PHP

将 Flash 连接到 PHP 的过程是使用前一节中介绍的预构建类完成的。如果您此时尚未安装 PHP，请参考第 1 章以充分了解并安装 PHP。

要开始本示例，请打开包含在书籍源文件中的起始文件。源文件可以在书籍的网站上找到。本示例的起始文件已添加设计和组件，如图 3.2 所示，让您可以专注于使其正常工作的代码。

本示例的第一部分是定义 PHP 文件在本地或远程服务器上的位置变量。

```
var phpFile:String =
    "http://localhost/connecting/exampleConn.php";
```

定义 PHP 脚本位置后，下一步是创建单击按钮时调用的函数。

```
function callServer(e:MouseEvent):void
{
    var urlRequest:URLRequest = new URLRequest(phpFile);

    var loader:URLLoader = new URLLoader();
    loader.addEventListener(Event.COMPLETE, serverResponse);
    loader.load(urlRequest);
}
```

## 图 3.2

以下是您将使用的示例应用程序的完成设计。

![](img/d9d48cd53eee0fbc1ebc363c322fac2c_91_0.png)

此函数创建 URLLoader 和 URLRequest 实例。将 phpFile 传递给 URLRequest 以创建对象。最后，将事件侦听器附加到 loader 变量，引用 serverResponse，即在数据加载时调用的函数。

```
function serverResponse(e:Event):void
{
   var loader:URLLoader = URLLoader(e.target);
   var variables:URLVariables = new URLVariables(loader.data);
   timeTxt.text = variables.returnValue;
}
```

服务器处理函数 serverResponse() 负责捕获从 PHP 文件传回的数据。在数据正确加载后，它将传递到 URLVariables 类以生成动态对象。

此动态对象包含从服务器传回的响应数据，因此只需简单的对象调用即可加载示例数据。在本示例中，该示例数据将是 PHP 捕获并返回的 UNIX 时间戳。

最后一部分是一个简单的按钮处理程序，在用户单击按钮时调用 callServer 函数。

