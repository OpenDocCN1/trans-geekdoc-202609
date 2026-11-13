

## 套接字安全

The use of sockets does require a more direct connection, which means security is a larger concern. Generally, whatever tool you are using to implement the socket client or server allows a level of security directly within its own library. For example, Flash requires a trust to be set up in a different domain that allows both parties to authorize the connection. In contrast, a simple connection made by the command line does not have any implied security beyond standard protocol limits.

使用套接字确实需要更直接的连接，这意味着安全是一个更大的问题。一般来说，无论你使用什么工具来实现套接字客户端或服务器，其自身库中都提供了一定级别的安全性。例如，Flash 需要在不同域之间设置信任，以允许双方授权连接。相比之下，命令行建立的简单连接除了标准协议限制之外，没有任何隐含的安全性。

**NOTE** Sockets can be a poor choice when implemented into certain systems or setups due to their direct connection nature.

**注意** 由于套接字具有直接连接的特性，在某些系统或设置中实现套接字可能不是一个好选择。

## Implementing a socket server

The socket server master can be implemented using many common programming languages.

套接字服务器主控端可以使用许多常见编程语言来实现。

For a persistent or production-level socket, you would most likely run it from a live server to ensure other users can connect to it and limit the risk of an open connection on your local system.

对于持久性或生产级套接字，你最好在实时服务器上运行它，以确保其他用户可以连接到它，并限制本地系统上开放连接的风险。

## Understanding the socket connection

The socket connection in the following example will be responsible for communicating with the user. The following sections explain that process.

以下示例中的套接字连接将负责与用户通信。以下部分将解释该过程。

## Parts of a socket

A socket connection is made of two pieces. The first part is the master connection or server, and the second part is the clients that connect to the master. The clients can talk directly to the master but cannot generally talk to other clients. If you want the clients to talk with each other you would implement a talkback system within the master.

套接字连接由两部分组成。第一部分是主控连接或服务器，第二部分是连接到主控的客户端。客户端可以直接与主控通信，但通常不能与其他客户端通信。如果你希望客户端之间相互通信，你需要在主控中实现一个回话系统。

## Binding

The master socket is bound to a specific IP address and port. This means the master connection is made to this specific point to ensure the connection is unique. Clients that want to communicate with that socket server must connect to the same IP address and port as the master.

主套接字绑定到特定的 IP 地址和端口。这意味着主控连接会连接到这个特定点，以确保连接的唯一性。想要与该套接字服务器通信的客户端必须连接到与主控相同的 IP 地址和端口。

## Listening

This is similar to the standard Web server. Once the socket server starts, it listens for active clients and new ones that want to connect. These clients are then added to the queue and begin to receive communications from the group.

这与标准 Web 服务器类似。套接字服务器启动后，它会监听活跃客户端以及想要连接的新客户端。这些客户端随后被添加到队列中，并开始接收来自组的通信。

## Working with Sockets in PHP

Building a socket server in PHP requires some prior configuration. A socket server within PHP cannot be run from the standard graphic version due to its persistent connection. A standard Web browser-based connection would timeout or possibly crash the host machine. A socket connection would be run using the nongraphic command-line version of PHP (CLI). The first step to working with sockets in PHP is to determine if you have this CLI version of PHP installed, as it is not normally included in a Web server package.

在 PHP 中构建套接字服务器需要一些预先配置。由于持久连接的原因，PHP 中的套接字服务器无法从标准图形版本运行。基于标准 Web 浏览器的连接会超时，甚至可能导致主机崩溃。套接字连接将使用 PHP 的非图形命令行版本（CLI）运行。在 PHP 中使用套接字的第一步是确定是否已安装此 CLI 版本的 PHP，因为它通常不包含在 Web 服务器软件包中。

## Looking for command-line version of PHP

The command-line version (CLI), if installed, is usually accessible directly from the Terminal on a Mac or the command prompt on a PC (see Figure 8.1).

如果已安装，命令行版本（CLI）通常可以直接从 Mac 的终端或 PC 的命令提示符访问（参见图 8.1）。

To determine if you have this version, simply open the command line. In Windows, click Start and then Run. Type cmd in the Run dialog box and click OK. If you're using a Mac, open the Finder, navigate to Applications/Utilities, and open the Terminal.

要确定是否安装了此版本，只需打开命令行即可。在 Windows 中，单击“开始”，然后单击“运行”。在“运行”对话框中键入 cmd，然后单击“确定”。如果你使用的是 Mac，打开 Finder，导航到 Applications/Utilities，然后打开终端。

## FIGURE 8.1

Example of a command prompt in Windows XP

Windows XP 中的命令提示符示例

![](img/d9d48cd53eee0fbc1ebc363c322fac2c_176_0.png)

With the command line open, type the following:

打开命令行后，输入以下内容：

```
$ php -v
```

That command tells PHP to report the version information and exit. The results should look something similar to the following:

该命令指示 PHP 报告版本信息并退出。结果应类似于以下内容：

```
PHP 5.2.5 (cli) (built: Dec 20 2007 02:55:52)
Copyright (c) 1997-2007 The PHP Group
Zend Engine v2.2.0, Copyright (c) 1998-2007 Zend Technologies
```

If you get a response similar to the following, it means the PHP version may be installed but not globally accessible from any command line and will require configuration.

如果收到类似以下的响应，则表示 PHP 版本可能已安装，但无法从任何命令行全局访问，并需要配置。

```
-bash: php: command not found
```

You will need to locate the command-line version or install it to continue with this chapter.

你需要查找命令行版本或安装它，以便继续本章的学习。

> See Chapter 1 for information on how to install the command-line version of PHP.

> 有关如何安装 PHP 命令行版本的信息，请参见第 1 章。

## Building a socket server

To build a simple socket server using PHP, start by creating a file and saving it to a commonly accessible location. This file does not need to be in your Web directory and will probably only be harder to work with if it is.

要使用 PHP 构建一个简单的套接字服务器，首先创建一个文件并将其保存到常用可访问的位置。此文件不需要放在 Web 目录中，而且如果放在其中，可能会更难处理。

> You want to ensure the socket file is not visible to the Web because it could cause your PHP to not work properly if a malicious user attempted to run the file.

> 你需要确保套接字文件对 Web 不可见，因为如果恶意用户尝试运行该文件，可能会导致 PHP 无法正常工作。

To better understand how sockets work, start with a very simple socket server example.

为了更好地理解套接字的工作原理，先从一个非常简单的套接字服务器示例开始。

## Simple PHP-based socket server

The first part of the socket server is to determine the server IP address and port number. If you are running the server locally you don't need to determine your physical IP address. Instead, you can use the local address.

套接字服务器的第一部分是确定服务器 IP 地址和端口号。如果你在本地运行服务器，则不需要确定物理 IP 地址。相反，你可以使用本地地址。

```
<?php

$host = "127.0.0.1";
$port = "8888";
```

The port number is not specific, but it needs to be unique on the same machine to ensure it won't collide with any other application on your system or network (if used remotely).

端口号没有特定要求，但在同一台机器上需要唯一，以确保它不会与系统或网络上的任何其他应用程序冲突（如果远程使用）。

This script will need to inform PHP to continue running because it needs to check for and manage connections indefinitely. This is achieved by passing the set_time_limit function a value of 0, meaning this script should never stop until properly exited.

此脚本需要通知 PHP 继续运行，因为它需要无限期地检查和管理连接。这是通过将 set_time_limit 函数的值设为 0 来实现的，这意味着该脚本应一直运行，直到正常退出。

```
set_time_limit(0);
```

With the configuration out of the way, you can create the master socket connection.

配置完成后，你可以创建主套接字连接。

```
$sock = socket_create(AF_INET, SOCK_STREAM, SOL_TCP);
```

The three arguments passed into the socket_create function define which type of connection it is and are PHP constants. For this example they are not important, but they will be explained later in the chapter.

传递给 socket_create 函数的三个参数定义了连接类型，且均为 PHP 常量。在本示例中它们不重要，但将在本章后面进行解释。

The $sock variable now contains an active socket resource id. The next step is to bind the socket to the port defined in the first part of the code.

$sock 变量现在包含一个活动套接字资源 ID。下一步是将套接字绑定到代码第一部分中定义的端口。

```
socket_bind($sock, $host, $port);
```

After the socket is bound to the port, you can start listening for connections. The first argument is the $socket variable, which holds the socket resource id. The second argument is a backlog variable that tells PHP how many messages to queue up before an error is passed to the client. This variable is a suggestion because some systems will define or override this value. For example, Windows sets this based on the underlying service provider and basically ignores any user-submitted value.

套接字绑定到端口后，你可以开始监听连接。第一个参数是 $socket 变量，它保存套接字资源 ID。第二个参数是 backlog 变量，它告诉 PHP 在向客户端传递错误之前要排队的消息数量。这个变量只是一个建议，因为有些系统会定义或覆盖此值。例如，Windows 基于底层服务提供程序设置此值，基本上会忽略用户提交的任何值。

```
socket_listen($sock, 4);
```

At this point, you have built a socket server that doesn't do anything. This basically means the server starts and waits for incoming connections but does not handle them in any way. The next step is to set up the portion of the socket server that handles the incoming connections.

此时，你已经构建了一个不执行任何操作的套接字服务器。这基本上意味着服务器启动并等待传入连接，但不以任何方式处理它们。下一步是设置处理传入连接的套接字服务器部分。

You need to create another socket that handles the incoming connections by making a call to socket_accept passing in the $socket resource id.

你需要通过调用 socket_accept 并传入 $socket 资源 ID 来创建另一个用于处理传入连接的套接字。

```
$childSocket = socket_accept($sock);
```

From this point the $childSocket variable is used to handle all client communications. The data sent from a connection is read using the socket_read function.

从这一点开始，$childSocket 变量用于处理所有客户端通信。来自连接的数据使用 socket_read 函数读取。

```
$incomingData = socket_read($childSocket, 2048);
```

This function takes two arguments. The first argument is the client socket handler, and the second argument is the number of bytes to read from the client. This can be useful when trying to run a more efficient socket server. It is also a good idea to limit the output on the client side (if possible).

该函数采用两个参数。第一个参数是客户端套接字句柄，第二个参数是要从客户端读取的字节数。在尝试运行更高效的套接字服务器时，这可能很有用。同时，最好限制客户端上的输出（如果可能）。

The socket_read function continues to load information into the $incomingData variable until the data limit is hit or one of the following characters is found: carriage return (\n), tab (\t), or \0. PHP treats those as end-of-input characters and moves to the next line in the script when one is found.

socket_read 函数会继续将信息加载到 $incomingData 变量中，直到达到数据限制或找到以下字符之一：回车符（\n）、制表符（\t）或 \0。PHP 将这些视为输入结束字符，并在找到其中一个时移动到脚本的下一行。

## Responding to the client connection

After the data is loaded, the next step is to act on that data and in most cases respond to the client. For example, the following is a simple question/answer demo that has PHP responding to one question:

加载数据后，下一步是根据数据采取行动，并在大多数情况下响应客户端。例如，以下是一个简单的问答演示，用于 PHP 对一个问题进行响应：

```
if(substr($incomingData, 0, -2) == "are you hungry?")
{
    $response = "Server Response > I could eat!\n";
    socket_write($childSocket, $response, strlen($response));
}
```

The socket_write function takes three arguments. The first is the child socket resource id; the second argument is the response being sent to the client. The third argument, which is optional, is the length of the $response. This example only sends a response back to the client when you ask PHP if it is hungry. As you can see, this is not a very practical application, but does clearly explain how sockets are set up and how to interact with them.

socket_write 函数采用三个参数。第一个是子套接字资源 ID；第二个参数是发送给客户端的响应。第三个参数是可选的，即 $response 的长度。此示例仅在你询问 PHP 是否饿了时才向客户端发送响应。如你所见，这不是一个非常实用的应用程序，但它确实清楚地解释了如何设置套接字以及如何与其交互。

The last step to the sample application, before testing it, is closing the two socket connections to free up the resources and allow new connections to be made.

在测试示例应用程序之前，最后一步是关闭两个套接字连接，以释放资源并允许建立新连接。

