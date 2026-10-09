

源主机的 IP 地址和源套接字的端口号——也会附加到数据包中。然而，将源地址附加到数据包通常*不*是由 UDP 应用程序代码完成的；相反，这是由底层操作系统自动完成的。

我们将使用以下简单的客户端-服务器应用程序来演示 UDP 和 TCP 的套接字编程：

- 1. 客户端从键盘读取一行字符（数据）并将其发送到服务器。
- 2. 服务器接收数据并将字符转换为大写。
- 3. 服务器将修改后的数据发送回客户端。
- 4. 客户端接收修改后的数据并将其显示在屏幕上。

图 2.27 强调了通过 UDP 传输服务进行通信的客户端和服务器之间主要的套接字相关活动。

![](img/059c6683459cb0a4f802be65ff31bb03_179_0.png)

# 图 2.27 ♦ 使用 UDP 的客户端-服务器应用程序

现在让我们动手实践，查看这个简单应用程序的 UDP 实现的客户端-服务器程序对。我们在每个程序之后都提供了详细的逐行分析。我们将从 UDP 客户端开始，该客户端将向服务器发送一个简单的应用层消息。为了让服务器能够接收并回复客户端的消息，它必须处于就绪和运行状态——也就是说，在客户端发送消息之前，它必须作为一个进程在运行。

客户端程序名为 `UDPClient.py`，服务器程序名为 `UDPServer.py`。为了强调关键问题，我们故意提供了最简化的代码。“良好的代码”肯定会有几行辅助代码，特别是用于处理错误情况的。对于此应用程序，我们任意选择 12000 作为服务器端口号。

## UDPClient.py

以下是该应用程序客户端的代码：

```python
from socket import *
servName = 'hostname'
serverPort = 12000
clientSocket = socket(AF_INET, SOCK_DGRAM)
message = input('Input lowercase sentence:')
clientSocket.sendto(message.encode(), (servName, serverPort))
modifiedMessage, serverAddress = clientSocket.recvfrom(2048)
print(modifiedMessage.decode())
clientSocket.close()
```

现在让我们来看看 `UDPClient.py` 中的各种代码行。

```python
from socket import *
```

套接字模块是 Python 中所有网络通信的基础。通过包含这一行，我们将能够在程序中创建套接字。

```python
servName = 'hostname'
serverPort = 12000
```

第一行将变量 `servName` 设置为字符串 'hostname'。这里，我们提供一个包含服务器 IP 地址（例如，“128.138.32.126”）或服务器主机名（例如，“cis.poly.edu”）的字符串。如果我们使用主机名，则会自动执行 DNS 查找以获取 IP 地址。第二行将整数变量 `serverPort` 设置为 12000。

```python
clientSocket = socket(AF_INET, SOCK_DGRAM)
```

这一行创建了客户端的套接字，名为 `clientSocket`。第一个参数指示地址族；具体而言，`AF_INET` 指示底层网络使用 IPv4。（现在不要担心这一点——我们将在第 4 章讨论 IPv4。）第二个参数指示套接字的类型是 `SOCK_DGRAM`，这意味着它是一个 UDP 套接字（而不是 TCP 套接字）。请注意，在创建套接字时，我们没有指定客户端套接字的端口号；相反，我们让操作系统为我们完成这一点。既然客户端进程的门已经创建，我们将希望创建一个消息以通过这扇门发送。

```python
message = input('Input lowercase sentence:')
```

`input()` 是 Python 中的一个内置函数。当执行此命令时，客户端的用户会被提示输入“Input lowercase sentence:”。然后用户使用键盘输入一行，该行被放入变量 `message` 中。现在我们已经有了套接字和消息，我们将希望将消息通过套接字发送到目标主机。

```python
clientSocket.sendto(message.encode(), (servName, serverPort))
```

在上一行中，我们首先将消息从字符串类型转换为字节类型，因为我们需要向套接字发送字节；这是通过 `encode()` 方法完成的。方法 `sendto()` 将目标地址（`servName`、`serverPort`）附加到消息上，并将生成的数据包发送到进程的套接字 `clientSocket` 中。（如前所述，源地址也附加到了数据包中，尽管这是自动完成的，而不是由代码显式完成的。）通过 UDP 套接字发送从客户端到服务器的消息就是这么简单！发送数据包后，客户端等待接收来自服务器的数据。

*注：在原始 OCR 文本中，sendto 调用中的变量被识别为 `serverName`，但在上面的代码块中它被定义为 `servName`。根据代码块的上下文，`servName` 是该脚本中使用的正确变量名。*

```python
modifiedMessage, serverAddress = clientSocket.recvfrom(2048)
```

通过上一行代码，当数据包从互联网到达客户端的套接字时，数据包的数据被放入变量 `modifiedMessage` 中，数据包的源地址被放入变量 `serverAddress` 中。变量 `serverAddress` 包含服务器的 IP 地址和端口号。程序 `UDPClient` 实际上并不需要这个服务器地址信息，因为它从一开始就知道服务器地址；但这行 Python 代码仍然提供了服务器地址。方法 `recvfrom` 还接受缓冲区大小 `2048` 作为输入。（此缓冲区大小适用于大多数用途。）

```python
print(modifiedMessage.decode())
```

在将消息从字节转换为字符串后，这一行在用户显示器上打印出 modifiedMessage。它应该是用户键入的原始行，但现在是大写的。

```python
clientSocket.close()
```

这一行关闭套接字。然后进程终止。

## UDPServer.py

现在让我们来看看该应用程序的服务器端：

```python
from socket import *
serverPort = 12000
serverSocket = socket(AF_INET, SOCK_DGRAM)
serverSocket.bind(('', serverPort))
print("The server is ready to receive")
while True:
    message, clientAddress = serverSocket.recvfrom(2048)
    modifiedMessage = message.decode().upper()
    serverSocket.sendto(modifiedMessage.encode(), clientAddress)
```

请注意，`UDPServer` 的开头与 `UDPClient` 相似。它也导入了套接字模块，也将整数变量 `serverPort` 设置为 12000，并且也创建了类型为 `SOCK_DGRAM`（即 UDP 套接字）的套接字。与 `UDPClient` 显著不同的第一行代码是：

```python
serverSocket.bind(('', serverPort))
```

上一行将端口号 12000 绑定（即分配）到服务器的套接字上。因此，在 `UDPServer` 中，代码（由应用程序开发者编写）显式地将端口号分配给套接字。以这种方式，当任何人向服务器的 IP 地址的端口 12000 发送数据包时，该数据包将被引导至此套接字。`UDPServer` 然后进入一个 while 循环；该 while 循环允许 `UDPServer` 无限期地接收和处理来自客户端的数据包。在 while 循环中，`UDPServer` 等待数据包到达。

```python
message, clientAddress = serverSocket.recvfrom(2048)
```

这行代码与我们在 `UDPClient` 中看到类似。当数据包到达服务器套接字时，数据包的数据被放入变量 `message`，数据包的源地址被放入变量 `clientAddress`。变量 `clientAddress` 包含客户端的 IP 地址和端口号。这里，`UDPServer` *将*利用此地址信息，因为它提供了返回地址，类似于普通邮件中的退回地址。有了这个源地址信息，服务器现在知道应该将回复定向到哪里。

```python
modifiedMessage = message.decode().upper()
```

这一行是我们简单应用程序的核心。它接收客户端发送的行，在将消息转换为字符串后，使用 `upper()` 方法将其转换为大写。

```python
serverSocket.sendto(modifiedMessage.encode(), clientAddress)
```

最后一行将客户端地址（IP 地址和端口号）附加到大写消息上（在将字符串转换为字节之后），并将生成的数据包发送到服务器套接字中。（如前所述，服务器地址也附加到了数据包中，尽管这是自动完成的，而不是由代码显式完成的。）然后互联网会将数据包递交到此客户端地址。在服务器发送数据包后，它保持在 while 循环中，等待另一个 UDP 数据包到达（来自任何主机上运行的任何客户端）。

要测试这两个程序，你在一个主机上运行 `UDPClient.py`，在另一个主机上运行 `UDPServer.py`。务必在 `UDPClient.py` 中包含服务器的正确主机名或 IP 地址。接下来，你在服务器主机上执行 `UDPServer.py`（已编译的服务器程序）。这在服务器中创建了一个进程，该进程空闲运行，直到被某个客户端联系。然后你在客户端上执行 `UDPClient.py`（已编译的客户端程序）。这在客户端中创建了一个进程。最后，要在客户端使用该应用程序，你键入一个句子并按下回车键。

要开发你自己的 UDP 客户端-服务器应用程序，你可以从稍微修改客户端或服务器程序开始。例如，服务器不必将所有字母转换为大写，而是可以统计字母 *s* 出现的次数并返回这个数字。或者你可以修改客户端，使得在接收到大写句子后，用户可以向服务器发送更多句子。

## 2.7.2 使用 TCP 进行套接字编程

与 UDP 不同，TCP 是一种面向连接的协议。这意味着在客户端和服务器开始相互发送数据之前，它们首先需要握手并建立 TCP 连接。TCP 连接的一端连接到客户端套接字，另一端连接到服务器套接字。在创建 TCP 连接时，我们将客户端套接字地址（IP 地址和端口号）和服务器套接字地址（IP 地址和端口号）与之关联。在建立 TCP 连接后，当一方想要向另一方发送数据时，它只需丢弃该数据
