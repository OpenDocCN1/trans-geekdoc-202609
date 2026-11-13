
如果你仍希望接收连接，只需移除 `$childSocket` 变量即可。

```
socket_close($childSocket);
socket_close($sock);
```

套接字可以按任何顺序关闭，但最好最后关闭主套接字，以防你需要先遍历多个客户端连接。

## 测试套接字服务器

可以使用简单的提示符或终端来测试套接字服务器，如图 8.2 所示。打开命令行后，启动 PHP 的命令行版本，使用 `-f` 选项传入示例文件。

```
$ /path/to/php -f /path/to/socket/sample/simpleSocket.php
```

## 图 8.2 在命令提示符中运行的简单套接字服务器

![](img/d9d48cd53eee0fbc1ebc363c322fac2c_179_0.png)

你会发现提示符指示符消失，且 PHP 文件没有任何输出。这可能不是非常理想的结果，因为没有任何东西在告诉你服务器正在运行。你可以在文件顶部添加一个非常简单的打印语句，例如：

```
<?php

$host = "127.0.0.1";
$port = "8888";

set_time_limit(0);

print "Starting Socket Server...\n";
...
```

如果你停止并启动套接字服务器，应该会看到打印的消息，类似于下面这样：

```
$ /usr/bin/php -f /path/to/simpleSocket.php
Starting Socket Server...
```

> 如果你经常重启套接字服务器，可能会看到提示端口已被占用的警告。你可以重试或选择另一个端口来继续测试。

当套接字服务器正常运行时，你可以打开一个新的提示符，并尝试将客户端与套接字服务器连接。

```
$ telnet 127.0.0.1 8888
```

成功连接后，应会出现类似下面的消息：

```
$ telnet 127.0.0.1 8888
Trying 127.0.0.1...
Connected to localhost.
Escape character is '^]'.
```

此应用程序在终止前仅接受发送的一条消息。如果你输入的内容不是 "are you hungry?"，则不会看到任何响应，除非你修改了套接字应用程序中提出的问题。

以下是此示例的完整代码：

```
<?php

$host = "127.0.0.1";
$port = "8888";

set_time_limit(0);

print "Starting Socket Server...\n";

$sock = socket_create(AF_INET, SOCK_STREAM, SOL_TCP);

socket_bind($sock, $host, $port);
socket_listen($sock, 4);

$childSocket = socket_accept($sock);
$incomingData = socket_read($childSocket, 2048);

if(substr($incomingData, 0, -2) == "are you hungry?")
{
    $response = "Server Response > I could eat!\n";
    socket_write($childSocket, $response, strlen($response)) ;
}
}
socket_close($childSocket);
socket_close($sock);
?>
```

返回消息后连接会自动终止，因为没有系统用于查找其他消息。更现实的应用程序会假设存在某种循环来查找多条消息。

## 创建持久套接字服务器

持久套接字服务器与前一个示例非常相似，区别在于它会循环检查新消息。

## 递归循环

PHP 不提供类似 ActionScript 中的异步系统（基于事件），但你可以创建一个循环来达到相同的效果。

例如，下面是一个非常简单的 `while` 循环，类似于将在持久连接示例中使用的循环：

```
x = 0;
while(x < 50)
{
x++;
}
```

## 管理多个通信

允许用户在一个连接中发送多条消息的关键，是将负责检查新消息的 `socket_read` 调用包装在一个循环中。

```
do
{
// // look for new messages

$incomingData = socket_read($childSocket, 2048);

if(trim($incomingData) == "are you hungry?")
{
$response = "Server Response > I could eat!\n";
socket_write($childSocket, $response, strlen($response));
}
else if(trim($incomingData) == "exit")
{
$response = "Goodbye!\n";
socket_write($childSocket, $response, strlen($response));
}
socket_close($childSocket);
break;
}
else
{
$response = strtoupper(trim($incomingData)) . "\n";
socket_write($childSocket, $response, strlen($response));
}
}
while(true);
```

如果你测试该示例，连接将保持活动状态，直到你关闭提示符，或在连接到应用程序时输入 "exit"（这会告知套接字服务器关闭你的连接）。你也可以输入除了 "exit" 或上述问题之外的任何内容，响应将是你以大写形式输入的内容。

此简单示例不支持多客户端，因此一旦客户端关闭，服务器也会随之结束。在本章的第二部分，你将构建一个基于套接字的完整多用户聊天应用程序，它本质上会允许同时存在多个连接。

到现在你应该已经了解 PHP 中套接字的工作原理，以及如何根据应用程序以不同方式实现它们。下一部分解释了套接字在 Flash 中的工作原理。然后在最后一章中，你将结合 Flash 和 PHP 来使用套接字发送/接收信息。

## 在 Flash 中使用套接字

Flash 被视为套接字连接的客户端。这意味着你无法直接从 Flash 部署套接字服务器，因为 Flash 是客户端应用程序。即使可以将 Flash 用作套接字服务器，也不会非常有益，因为 Flash 是图形应用程序。在命令行环境中使用 Flash 本质上是对资源的浪费。

话虽如此，Flash 是出色的套接字服务器客户端。前一部分使用了 Telnet，这是初始化与套接字服务器客户端连接的一种方式。Flash 允许 TCP 连接，但这需要更多代码和更多初始设置。

下一部分中大部分连接代码可以构建成公共类或库，以最大限度地减少创建套接字连接所需的代码量。

## 初始化套接字连接

初始化套接字连接的第一步是定义要连接的主机和端口。

```
var host:String = "127.0.0.1";
var port:uint = 8888;
```

这两个变量需要与你在上一部分编写的 PHP 代码相同。或者，如果你使用提供的代码，可以保留刚才显示的示例值。

定义变量后，创建 `Socket` 类的实例。该类的构造函数接受两个参数。第一个是主机，第二个是要连接的端口。

```
var socket:Socket = new Socket(host, port);
```

在继续使用动态数据源时，你会很快发现适当的事件处理程序能更容易地理解某事的工作原理。这意味着向套接字过程添加事件监听器是个好主意。先构建调用，稍后再创建事件处理程序。

```
socket.addEventListener(Event.CLOSE, closeHandler);
socket.addEventListener(Event.CONNECT, connectHandler);
socket.addEventListener(IOErrorEvent.IO_ERROR, ioErrorHandler);
socket.addEventListener(SecurityErrorEvent.SECURITY_ERROR,
securityErrorHandler);
socket.addEventListener(ProgressEvent.SOCKET_DATA,
socketDataHandler);
```

## 事件处理程序

此示例应用程序中使用的事件处理程序函数将错误追踪到输出窗口。更现实的应用程序需要一些逻辑来处理这些错误并相应地响应用户。

```
function closeHandler(event:Event):void
{
trace("Connection to [" + host + "] closed");
}
```

```
function ioErrorHandler(event:IOErrorEvent):void
{
trace(event.text);
}
```

```
function securityErrorHandler(event:SecurityErrorEvent):void
{
trace(event.toString());
}
```

## 特殊处理程序

此示例有两个特殊事件处理程序。第一个特殊事件处理程序在连接成功时被调用，通知你可以向套接字服务器发送消息。在建立正确连接之前发送的消息可能会导致错误或消息丢失。
