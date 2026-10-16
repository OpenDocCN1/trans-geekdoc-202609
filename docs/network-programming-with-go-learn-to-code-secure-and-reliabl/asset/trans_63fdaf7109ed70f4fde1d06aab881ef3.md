
在这段示例中，你允许来自 `users` 或 `staff` 组的任何同行建立连接。服务会拒绝访问未在至少一个这些组中的同行。如果这些组在你的 Linux 发行版中不存在，请在 `/etc/groups` 文件中选择任意组。服务正在监听 `/tmp/creds.sock` 套接字文件，这是你提供给 Netcat 的地址。

接下来，你需要一种更改组 ID 的方法，以便测试服务是否拒绝访问你未授权的客户端。当前，服务以你的用户和组 ID 运行，因为你启动了服务。因此，它会接受所有你的连接，因为服务通过 Unix Domain Sockets 159 允许其自身组（即我们的组）进行身份验证，依据 Listing 7-15 中的组映射。要在启动套接字连接时更改你的组，可以使用 sudo 命令行实用程序。

由于使用 sudo 需要提升权限，你通常在首次尝试时会被提示输入密码。下面的示例已省略密码提示，但你在 sudo 的第一次调用时会被要求输入密码：

$ `sudo -g staff -- nc -U /tmp/creds.sock`

Welcome

`^C`

$

使用 sudo，你通过向 `-g` 标志传递组名来更改你的组。在此示例中，你将组设置为 staff。然后执行 nc 命令。`-U` 标志指示 Netcat 通过 Unix domain socket 连接到 `/tmp/creds.sock` 文件。

由于 staff 组是受允许的组之一，你在连接时会收到 Welcome 消息。你通过按下 ctrl-C 终止连接的一方。

如果你使用不受允许的组重复测试，应该得到相反的结果：

$ `sudo -g nogroup -- nc -U /tmp/creds.sock`

Access denied

$

此时，你使用不受服务允许的 nogroup 组。如预期，你立即收到 Access denied 消息，服务器端的套接字会终止连接。

**What You’ve Learned**

本章开头介绍了 Unix domain sockets。Unix domain socket 是一种基于文件的进程间通信方式，适用于同一节点上运行的进程。本地数据库服务器和客户端等两个或多个进程可以通过 Unix domain socket 发送和接收数据。由于 Unix domain socket 依赖文件系统进行定位，你可以利用文件系统的所有权和权限来控制通过 Unix domain socket 进行通信的进程的访问权限。

随后，你学习了 Go 支持的 Unix domain socket 类型：`unix`、`unixgram` 和 `unixpacket`。Go 使得通过 Unix domain socket 进行通信变得相对简单，并为你处理了许多细节，尤其是当你使用 net 包的接口时。例如，用于流式 TCP 网络的代码在稍作修改后也可以在流式 Unix domain socket 上使用，尽管它仅适用于本地进程通信。同样，用于 UDP 网络的代码可以通过 unixgram 套接字类型利用。你还了解到混合 Unix domain socket 类型 `unixpacket`，并发现其缺点（第 160 页）并未超过其益处，特别是在跨平台支持方面。其他两种 Unix domain socket 类型对于大多数使用场景来说是更佳的选择。

本章介绍了进程凭证，并展示了如何使用它们来验证客户端连接。你可以超越基于文件的访问控制，在 Unix domain socket 上请求关于套接字另一端客户端的详细信息。

现在，你应该能够确定 Unix domain socket 在你的网络栈中最适合的位置。

Unix Domain Sockets 161

 **PART III**

**A P P L I C A T I O N - L E V E L**

**P R O G R A M M I N G**

 **8**

**W R I T I N G H T T P C L I E N T S**

*The HyperText Transfer Protocol* *(HTTP)* 是应用层协议，由万维网使用。在 HTTP 通信中，Web 客户端向 Web 服务器发送 *uniform resource locator* *(URL)*，服务器则返回相应的媒体资源。此上下文中，*resource* 可以是图片、样式表、HTML 文档、JavaScript 文件等。例如，如果你的浏览器向 Google 的服务器发送 `www.google.com` URL，服务器会返回 Google 的主页。

我们几乎每天都会进行这样的 Web 交易，无论是从手机、电脑，还是物联网设备（是的，甚至包括门铃、恒温器或烤箱）。

本章将介绍 Go 的 HTTP 客户端。首先，你将学习 HTTP 的基础知识，包括请求方法和响应代码。接着，你将探索 Go 的 HTTP 客户端用于向 Web 服务器请求资源，同时注意可能遇到的陷阱。然后，你将深入标准库代码，了解实现促进客户端与服务器之间的请求-响应通信的实现细节。

最后，你将看到在使用 Go 的 HTTP 客户端与 Web 服务器交互时常见的陷阱。

本章将为你提供与服务通过 HTTP 交互的基础，这将为你在下一章处理服务器端请求提供必要的基础。

**Understanding the Basics of HTTP**

HTTP 是一种无连接的客户端-服务器协议，客户端发起请求，服务器响应。HTTP 是应用层协议，是万维网通信的基础。它使用 TCP 作为底层传输层协议。

本章假设你使用的是 HTTP 版本 1.1（HTTP/1.1）。

我们也会覆盖 HTTP 版本 2.0（HTTP/2）引入的功能。

幸运的是，Go 抽象了这些协议之间的差异，因此我们可以使用相同的代码轻松支持任一协议。

***Uniform Resource Locators***

一个 *URL* 是用于客户端定位 Web 服务器并识别请求资源的地址。它由五个部分组成：必需的 *scheme*（指示使用的连接协议）、可选的 *authority*（资源的授权）、*path*（资源路径）、可选的 *query*（查询）和可选的 *fragment*（片段）。冒号（:）后跟两个正斜杠（//）分隔 scheme 与 authority。authority 包含可选的用户名和密码（以 @ 结尾）、主机名，以及可选的端口号（以 : 前缀）。path 是以正斜杠分隔的段序列。问号（?）标记查询的开始，通常由键值对用 & 连接组成。hash（#）标记片段，是资源子部分的标识符。整体来看，URL 遵循如下模式：

*scheme*:// *user*: *password*@ *host*: *port*/ *path*? *key1*\= *value1*& *key2*\= *value2*\# *table\_of\_contents* 典型的互联网 URL 至少包含 scheme 和 hostname。例如，如果你想查找关于 gophers 的图片，你可以在浏览器地址栏中输入以下 URL 并搜索 *gophers*：

1https://2images.google.com3/

**166** Chapter 8

scheme 1 告诉你的浏览器使用 HTTPS 连接到 *images.google.com* 2，并且希望访问默认资源 3。如果你在没有指定具体资源的情况下访问服务器地址，服务器会返回默认资源。正如大型公司在你未提供分机号时会将你的来电转给接线员一样，当你未指定想要的资源时，Web 服务器会提供默认资源。Google 会收到你的

