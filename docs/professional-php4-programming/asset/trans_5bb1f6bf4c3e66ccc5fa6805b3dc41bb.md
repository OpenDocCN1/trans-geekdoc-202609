

截至 PHP 4.0.6，sockets API 仍被归类为“experimental”。本节讨论的大多数函数在未来版本中可能会更改，涉及参数的数量和类型、返回值，在某些情况下甚至函数名称本身。对应用程序程序员而言，这些大多可能是语法上的变化；然而，在该话题尘埃落定之前，不建议将这些接口用于生产质量的代码。

### socket()

```
int socket(int domain, int type, int protocol)
```

该函数创建一个套接字，即通信端点变量。domain 参数有两个可能的值，即 AF_INET 和 AF_UNIX。如果参数为 AF_INET，则表示协议族是 Internet 协议族或 TCP/IP 协议套件。该参数是必需的，因为套接字也可用于另一种进程间通信模式，例如 UNIX 域套接字，在这种情况下，值应为 AF_UNIX。

尽管在针对 Microsoft Windows 构建的 PHP 版本中现在支持 AF_UNIX 参数，但截至 PHP 4.0.6，其行为不正确，应尽可能避免以增强代码可移植性。type 参数表示协议交互的级别，例如，套接字是与 IP 层还是与传输层交互。它还指定数据包传输机制，即通信是基于流的还是无连接的。下表列出了可能的值：

| Socket Type | Description |
| :--- | :--- |
| SOCK_STREAM | 这表示基于流的可靠传递服务。 |
| SOCK_DGRAM | 这表示无连接传递服务。 |
| SOCK_SEQPACKET | 这表示数据包保证按顺序传递。 |
| SOCK_RAW | 这表示交互层是 IP 层或网络层。 |
| SOCK_RDM | 这表示可靠但无连接的数据报模型。数据报按发送顺序到达，发送方会收到未送达通知，但与其他可靠模型不同，无需建立连接。 |
| SOCK_PACKET | 这表示可以原样发送数据包的模型。例如，以太网地址可以按数据包发送。 |

domain 参数和 type 参数的并非所有组合都合理。例如，将第一个参数指定为 AF_UNIX 并指定 SOCK_RAW 是没有意义的，因为 UNIX 基于流的协议与 IP 层无关。因此，第三个参数存在是为了消除各种组合的歧义。由于 PHP 对第三个参数的实现似乎不完整，且值为 0 在大多数情况下都可用，因此最安全的做法是将值指定为 0。

socket 函数的返回值是一个整数，表示可对其执行读/写操作的套接字描述符。负返回值表示错误条件。该值可以传递给 strerror() 函数，后者返回描述错误条件的消息字符串。

### bind()

```
int bind(int socket, string address [, int port])
```

创建服务器套接字时，有必要将其绑定到 IP 地址和知名端口。`bind()` 函数将套接字描述符作为第一个参数，将本地地址（即 IP 地址，前提是套接字描述符是为 `AF_INET` 协议族创建的）作为第二个参数。如果套接字是为 `AF_UNIX` 族创建的，则第一个参数是指向实际 UNIX 域套接字的 UNIX 路径名。

`port` 参数仅在 `AF_INET` 情况下有效，表示服务器应绑定的端口。如果端口已被其他服务占用，`bind()` 函数将失败。如果返回值为负，则表示错误条件，其文本描述可通过将其作为参数传递给 `strerror()` 函数来获得。

### connect()

```
int connect(int socket, string address [, int port])
```

客户端程序创建套接字后，需要连接到服务器。`connect()` 函数提供此功能。第一个参数是 `socket()` 调用返回的套接字描述符。如果 `socket()` 调用将协议族指定为 `AF_INET`，则第二个参数是服务器的 IP 地址。如果在 `socket()` 调用时将协议族指定为 `AF_UNIX`，则它需要是 UNIX 路径名。

`port` 参数仅在 `AF_INET` 情况下有效，表示远程服务器正在监听的端口。如果 `connect()` 函数的返回值为负，则表示错误条件，其文本描述可通过将其作为参数传递给 `strerror()` 函数来获得。

### listen()

```
int listen(int socket, int backlog)
```

服务器应用程序创建套接字并执行 `bind()` 以将其与本地 IP 地址和知名端口关联后，需要监听来自客户端的传入请求。`listen()` 函数提供此功能。它将 `socket` 作为第一个参数（需监听传入连接），将 `backlog` 作为第二个参数（表示可为该套接字排队的最大请求数）。

负返回值表示错误条件，且可将返回值传递给 `strerror()` 函数以获取错误的文本描述。

### accept_connect()

```
int accept_connect(int socket)
```

作为创建服务器程序的一部分，我们需要使用 `socket()` 函数创建套接字，使用 `bind()` 函数将其绑定到地址和端口号，并使用 `listen()` 调用指定其应监听传入连接。之后，我们需要调用 `accept_connect()` 函数，将 `socket()` 函数返回的套接字描述符作为参数传递。该函数会阻塞，直到套接字上有新请求到达。当新请求到达时，它会创建一个新套接字描述符并将其返回给程序，程序可使用它从连接中读取和写入数据。如果套接字是非阻塞的（有关 socket_set_blocking() 函数，请参见下文），并且在调用 accept_connect() 后立即套接字上没有可用数据，则该函数会返回一个错误代码整数。

### fsockopen() and pfsockopen()

```
int fsockopen (string [udp://]hostname, int port [, int errno [, string errstr [, double timeout]]])
```

这是一个通用的便捷函数，客户端可用它连接到服务器。它封装了创建套接字、解析服务器 IP 地址以及连接到指定端口上的服务器地址的功能。它可用于连接 TCP、UDP 和 UNIX 域套接字：

- `$fp = fsockopen("myTCPServer.wrox.com", 4567);` 将连接到监听在服务器 myTCPServer.wrox.com 端口号 4567 上的 TCP 套接字。
- `$fp = fsockopen("udp://myUDPServer.wrox.com", 6789);` 将连接到监听在服务器 myUDPServer.wrox.com 端口号 6789 上的 UDP 套接字。
- `$fp = fsockopen("/tmp/unixsocket456", 0);` 将连接到由文件系统路径 /tmp/unixsocket456 寻址的 UNIX 域套接字。当要使用 UNIX 域套接字时，必须将 port 参数设置为 0。

在上述所有情况下，可提供可选参数 errno 和 errstr 以指示连接到套接字时可能出现的任何错误条件。errno 表示错误号，errstr 表示错误消息。如果 errno 返回值为 0 且函数返回 false，则表示初始化套接字时出现问题。

此外，还可以为 TCP 和 UDP 套接字指定可选的 timeout 参数，以指示函数在放弃建立连接前必须等待的秒数。返回值 false 表示失败。如果函数成功，它将返回一个文件指针，该文件指针可用于能够读写文件指针的函数，例如 fgets() 和 fputs()。

pfsockopen() 具有与 fsockopen() 相同的功能，并采用相同类型的参数。唯一的区别在于，fsockopen() 打开的连接在脚本退出后会被销毁，而 pfsockopen() 打开的连接在脚本退出后仍保持持久。

> pfsockopen() 与大多数其他持久函数有相同的警告，甚至更多。连接仅在最初创建连接的 Apache 进程中持久。如果后续请求由不同的 Apache 进程处理，我们需要再次调用此函数。此外，服务器上的应用程序逻辑可能无法容忍超过一定间隔的空闲连接，并可能关闭连接。这意味着假设连接始终可用是不安全的。

