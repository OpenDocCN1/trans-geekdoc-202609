
# Node.JS 从零构建 Web 服务器指南

## James Smith

build-your-own.org

通过编写你自己的 `Web Server`，学习网络编程、HTTP 协议及其应用。

**James Smith**

build-your-own.org

## 7.4 讨论：缓冲区写入

# 引言

## 1.1 为什么需要引言

### 为什么需要引言

从零开始构建一个 Web 服务器是非常有感的，但这不应该是你的唯一目标。有很多博客文章向你展示一个“玩具级服务器”，但你如何超越玩具阶段呢？

### 网络编程

该项目在不使用任何依赖的情况下使用 Node.js，但许多概念是`语言无关`的，因此对任何语言的学习者来说都非常有价值。

### 协议与通信

第一步是 `socket` 编程。传输的数据必须符合 `HTTP` 标准。

### HTTP 详情

你已经了解 `HTTP`，例如 `GET` 和 `POST` 方法以及相关状态码。

## 1.2 构建你的底层

### 构建你的底层

大多数人每天使用 `HTTP`，但很少有人理解其内部原理。这本书 `Build Your Own` 深入探讨了 `socket` 的细节。

### 网络编程

该项目在不使用任何依赖的情况下使用 Node.js，但许多概念是`语言无关`的，因此对任何语言的学习者来说都非常有价值。

## 1.3 本书

### 本书

从零开始构建一个 Web 服务器是非常有感的，但这不应该是你的唯一目标。有很多博客文章向你展示一个“玩具级服务器”，但你如何超越玩具阶段呢？

### 以项目为中心

让你的 Web 服务器运行起来是非常有感的，但这不应该是你的唯一目标。有很多博客文章向你展示一个“玩具级服务器”，但你如何超越玩具阶段呢？

## 1.4 服务器

### 服务器

该项目在不使用任何依赖的情况下使用 Node.js，但许多概念是`语言无关`的，因此对任何语言的学习者来说都非常有价值。

正如你可能已经知到的，HTTP 协议位于 TCP 协议之上。TCP 本身是如何详细工作的并不是我们关注的；我们关于 TCP 需要了解的是，它是一个用于传输原始字节的双向通道——它是 HTTP 或 SSH 等其他应用协议的载体。

虽然 TCP 连接的每个方向都可以独立运行，但许多协议遵循“请求-响应”模型。客户端发送请求，然后服务器发送响应，接着客户端可能会使用同一个连接进行后续的请求和响应。

```
client
server
\------
\------
| req1 |
\==>
<==
| res1 |
| req2 |
\==>
<==
| res2 |
...
```

一个 HTTP 请求或响应由一个 `header`（头部）和一个可选的 `payload`（有效负载）组成。头部包含请求的 URL 或响应状态码，随后跟的是一系列 `header` `fields`（头部字段）列表。

## 2.2 通过示例理解 HTTP

为了掌握网络协议，让我们从从命令行发送一个 HTTP 请求开始。

运行 `netcat` 命令：

```
nc example.com 80
```

`nc` (netcat) 命令会与目标主机和端口建立一个 TCP 连接，然后将该连接到 `stdin` 和 `stdout`。我们现在可以在终端中开始输入，数据将会被传输：

```
GET / HTTP/1.0
Host: example.com
(empty line)
```

我们将得到以下响应：

```
HTTP/1.0 200 OK
Age: 525410
Cache-Control: max-age=604800
Content-Type: text/html; charset=UTF-8
Date: Thu, 20 Oct 2020 11:11:11 GMT
Etag: "1234567890+gzip+ident"
Last-Modified: Thu, 20 Oct 2019 11:11:11 GMT
Vary: Accept-Encoding
Content-Length: 1256
Connection: close
<!doctype html>
<!-- omitted -->
```

从命令行发送 HTTP 请求非常简单。让我们来看这些数据并尝试弄清楚它们的含义。

请求的第一行——`GET / HTTP/1.0`——包含了 HTTP 方法 `GET`、URI `/` 以及 HTTP 版本 `1.0`。这很容易辨认。

响应的第一行——`HTTP/1.0 200 OK`——包含了 HTTP 版本和响应状态码 `200`。

紧随第一行之后的是 `Key: value` 格式的头部字段列表。请求有一个头部字段——`Host`——它包含了域名。

响应包含许多字段，它们的功能并不像 `Host` 字段那样明显。许多 HTTP 头部字段是可选的，有些甚至是没用的。我们将在稍后的章节中学习更多相关内容。

响应头部之后是 `payload`，在我们的案例中，它是一个 HTML 文档。

Payload 和头部之间用一个空行隔开。`GET` 请求没有 payload，所以它以空行结束。

这只是一个简单的示例，你可以从命令行进行尝试。我们稍后将更详细地检查 HTTP 协议。

## 2.3 HTTP 的演进

### HTTP/1.0：原型

上面的示例使用了 `HTTP/1.0`，这是一个非常老的 HTTP 版本。`HTTP/1.0` 完全不支持在单个连接上进行多次请求，你必须为每个请求创建一个新连接。这是有问题的，因为典型的网页依赖于许多额外的资源，如图像、脚本或样式表；TCP 握手的延迟使得 `HTTP/1.0` 非常不优。

`HTTP/1.1` 解决了这个问题并成为了一个实用的协议。你可以通过简单地将 `HTTP/1.0` 更改为 `HTTP/1.1`，尝试使用 `nc` 命令在同一个连接上发送多个请求。

### HTTP/1.1：生产级且易懂

本书将关注 HTTP/1.1，因为它仍然非常流行且易理解。即使是与 Web 无关的软件系统也采用了 HTTP 作为其网络协议的基础。当后端开发者谈论“API”时，他们可能指的是基于 HTTP 的 API，即使对于内部软件服务也是如此。

为什么 HTTP 如此流行？一个可能的原因它可以作为一种通用的请求-响应协议；开发者可以依赖 HTTP 而不是发明自己的协议。这使得 HTTP 成为学习如何构建网络协议的好目标。

### HTTP/2：新特性

自 HTTP/1.1 之后还有进一步的发展。与 SPDY 相关的 `HTTP/2` 是 HTTP 的下一次迭代。除了压缩头部等增量式改进外，它还具有两个新能力：

- `Server push`（服务器推送），即在客户端请求之前就向其发送资源。

- 在单个 TCP 连接上进行多个请求的 `Multiplexing`（多路复用），这是解决*头部阻塞 (head-of-line blocking)* 的尝试。

有了这些新特性，`HTTP/2` 不再是一个简单的请求-响应协议。这就是为什么我们从 HTTP/1.1 开始，因为它足够简单且易理解。

### HTTP/3：更大的野心

`HTTP/3` 比 HTTP/2 大得多，它替换了 TCP 并使用 UDP。因此它需要复制 TCP 的大部分功能，这种替代方案被称为 `QUIC`。`QUIC` 背后的动机是用户态拥塞控制、多路复用。关于这些新技术可能会让你目不暇接，所以让我们从简单的开始：HTTP/1.1

## 2.4 命令行工具

向你介绍命令行工具是因为它可以进行快速测试和调试。你可能想将请求数据存储在文件中：`nc example.com 80 < request.txt`。在实践中，你可能会遇到 `nc` 的一些怪癖，例如发送 EOF 或多个版本的 `nc`。你可以使用现代的 `socat` 替代：

```
socat tcp:example.com:80
```

`telnet` 命令在教程中也很流行：

```
telnet example.com 80
```

你也可以使用现有的 HTTP 客户端而不是手动构建请求。尝试 `curl` 命令：

```
curl -vvv http://example.com/
```

大多数网站支持 HTTPS。HTTPS 在 HTTP 和 TCP 之间增加了一个额外的层 TLS。TLS 不是明文，所以你不能使用 `netcat` 测试 HTTPS 服务器。但 TLS 仍然像 TCP 一样提供字节流，你只需要将 `netcat` 替换为 TLS 客户端：

```
openssl s_client -verify_quiet -quiet -connect example.com:443
```

## 第三章

### 代码 TCP 服务器

我们的第一步是熟悉 socket API，因此我们在本章中编写一个简单的 TCP 服务器。

## 3.1 TCP 快速回顾

### 协议层

网络协议分为不同的层，高层依赖于低层，每一层都提供不同的能力。

```
top
/\
| App | 消息或其他
||
| TCP | 字节流
||
| IP | 数据包
||
| ... |
bottom
```

TCP 之下是 IP 层。每个 IP 数据包由三个部分组成：

- 发送者地址
- 接收者地址
- 消息数据

与基于包的方案进行通信并不容易。有很多应用程序需要解决的问题：

- 如果消息数据超过了单个数据包的容量怎么办？
- 如果数据包丢失了怎么办？
- 乱序包怎么办？

`UDP` 与 `TCP` 处于同一层，但仍然像底层一样基于数据包。`UDP` 只是在 `IP` 数据包上添加了端口号。

### TCP 字节流 vs UDP 数据包

关键区别：边界。

- `UDP`: 从套接字的每次 `read` 对应于对端的一次 `write`。
- `TCP`: 没有这种对应关系！数据是连续的字节流。

`TCP` 根本没有保留边界的机制。

1. `TCP` 发送缓冲区：这是传输前存储数据的地方。多次写入与单次写入无法区分的。
2. 数据被封装为一个或多个 `IP` 数据包，`IP` 边界与原始写入边界之间没有关系。
3. `TCP` 接收缓冲区：数据在到达时即可供应用程序使用。

套接字编程中的第一个新手陷阱是“合并与拆分 TCP 数据包”，因为不存在所谓的“TCP 数据包”。需要通过在字节流中强制设定边界来解释 `TCP` 数据。

### 字节流 vs. 数据包：以 DNS 为例

为了帮助你理解字节流的影响，让我们以 `DNS` 协议（域名到 IP 地址的查找）为例。

`DNS` 运行在 `UDP` 上，客户端发送单个请求消息，服务器响应单个响应消息。一个 `DNS` 消息被封装在一个 `UDP` 数据包中。

| IP 头部 | IP 负载 |
| :--- | :--- |
| ... | |
| UDP 头部 | UDP 负载 |
| DNS 消息 | |

由于基于包协议的缺点（例如无法使用大消息），`DNS` 也设计为运行在 `TCP` 上。但 `TCP` 对“消息”并不感知，因此在 `TCP` 上发送 `DNS` 消息时，会在每个 `DNS` 消息前添加一个 `2 字节长度字段`，以便服务器或客户端能够判断字节流的哪个部分是哪个消息。这个 2 字节长度字段是 `TCP` 之上 `应用协议` 最简单的示例。该协议允许在单个 `TCP` 字节流中存在多个 `应用消息`（`DNS`）。

| len1 | msg1 | len2 | msg2 | ... |

### TCP 从握手开始

要建立 `TCP` 连接，应该有一个和一个服务器（忽略同时发生的情况）。服务器在特定地址（IP + 端口）等待客户端，这一步被称为 `bind & listen`。然后客户端可以 `connect` 到该地址。`connect` 操作涉及三次握手（`SYN`、`SYN-ACK`、`ACK`），但这不是我们关注的，因为操作系统透明地完成了它。操作系统完成握手后，连接可以被服务器 `accepted`。

### TCP 是双向且全双工的

一旦建立，`TCP` 连接就可以用作双向字节流，每个方向有两个通道。许多协议如 `HTTP/1.1` 是这种请求-响应模式的，对端要么在发送请求/响应，要么在接收响应/请求。但 `TCP` 不限于此。

## 3.2 编写 TCP 服务器

### 第 1 步：创建服务器

Node.js 提供了 `net` 模块用于 TCP 编程。我们使用 `net.createServer()` 创建一个服务器。

```javascript
import * as net from "net";

let server = net.createServer();
```

### 第 2 步：监听连接

服务器需要绑定到地址并开始监听。

```javascript
server.listen(3000, () => {
  console.log('server listening on port 3000');
});
```

### 第 3 步：处理连接事件

`'connection'` 参数被称为一个 `event`（事件），你可以在其上注册回调函数。监听套接字（socket）上还有其他事件。例如，有一个 `'error'` 事件，当发生错误时，它会被触发。

```javascript
server.on('error', (err: Error) => { throw err; });
```

在这里，我们简单地抛出异常并终止程序。你可以通过在同一个地址和端口上运行 2 个服务器来测试这一点，第二个服务器将会失败。

由于这本书不是一份手册，我们不会在此处列出所有内容。请阅读 [Node.js 文档](https://nodejs.org/api/net.html#class-netserver) 来查找其他可能有用的事件。

### 第 4 步：读取与写入

从连接接收的数据也通过回调函数传递。从套接字读取数据的相关事件是 `'data'` 事件和 `'end'` 事件。每当数据从对方到达时，`'data'` 事件就会被触发；当对方结束传输时，`'end'` 事件就会被触发。

```javascript
socket.on('end', () => {
  // 收到 FIN。连接将自动关闭。
  console.log('EOF.');
});

socket.on('data', (data: Buffer) => {
  console.log('data:', data);
  socket.write(data); // 回显数据。
});
```

`socket.write()` 方法将数据发回对方。

### 第 5 步：关闭连接

`socket.end()` 方法结束传输并关闭套接字。在这里，当数据包含字母“q”时，我们调用 `socket.end()`，这样我们可以轻松地测试这种场景。

```javascript
socket.on('data', (data: Buffer) => {
  console.log('data:', data);
  socket.write(data); // 回显数据。
  // 如果数据包含 'q' 则主动关闭连接
  if (data.includes('q')) {
    console.log('closing.');
    socket.end();
    // 这将发送 FIN 并关闭连接。
  }
});
```

当传输从任何一方结束时，套接字会被运行时自动关闭。`net.Socket` 上还有一个 `'error'` 事件，用于报告 IO 错误。该事件也会导致运行时关闭套接字。

### 第 6 步：测试

这是我们回声服务器的完整代码。

```javascript
import * as net from "net";

function newConn(socket: net.Socket): void {
  console.log('new connection', socket.remoteAddress, socket.remotePort);
  socket.on('end', () => {
    // 收到 FIN。连接将自动关闭。
    console.log('EOF.');
  });
  socket.on('data', (data: Buffer) => {
    console.log('data:', data);
    socket.write(data); // 回显数据。
    // 如果数据包含 'q' 则主动关闭连接
    if (data.includes('q')) {
      console.log('closing.');
      socket.end();
      // 这将发送 FIN 并关闭连接。
    }
  });
}

let server = net.createServer();
server.on('error', (err: Error) => { throw err; });
server.on('connection', newConn);
server.listen(3000, () => {
  console.log('server listening on port 3000');
});
```

当传输从任何一方结束时，套接字会被运行时自动关闭。`net.Socket` 上还有一个 `'error'` 事件用于报告 IO 错误。该事件也会导致运行时关闭套接字。



```javascript
socket.on('end', () => {
  // 收到 FIN。连接将自动关闭。
  console.log('EOF.');
});

socket.on('data', (data: Buffer) => {
  console.log('data:', data);
  socket.write(data); // 回显数据。
});
```

`socket.write()` 方法将数据发回对方。

### 第 5 步：关闭连接

`socket.end()` 方法结束传输并关闭套接字。在这里，当数据包含字母“q”时，我们调用 `socket.end()`，这样我们可以轻松地测试这种场景。

[1](https://nodejs.org/api/net.html#class-netserver)

[报告错误 | 提问](https://forms.gle/UKo4bncUnuMGBrTM7) @ [build-your-own.org](https://build-your-own.org)

13

2024-02-02

## 03. 代码实现一个 TCP 服务器

```javascript
socket.on('data', (data: Buffer) => {
  console.log('data:', data);
  socket.write(data); // 回显数据。
  // 如果数据包含 'q' 则主动关闭连接
  if (data.includes('q')) {
    console.log('closing.');
    socket.end();
    // 这将发送 FIN 并关闭连接。
  }
});
```

当传输从任何一方结束时，套接字会被运行时自动关闭。`net.Socket` 上还有一个 `'error'` 事件，用于报告 IO 错误。该事件也会导致运行时关闭套接字。

### 第 6 步：测试

这是我们回声服务器的完整代码。

```javascript
import * as net from "net";

function newConn(socket: net.Socket): void {
  console.log('new connection', socket.remoteAddress, socket.remotePort);
  socket.on('end', () => {
    // 收到 FIN。连接将自动关闭。
    console.log('EOF.');
  });
  socket.on('data', (data: Buffer) => {
    console.log('data:', data);
    socket.write(data); // 回显数据。
    // 如果数据包含 'q' 则主动关闭连接
    if (data.includes('q')) {
      console.log('closing.');
      socket.end();
      // 这将发送 FIN 并关闭连接。
    }
  });
}

let server = net.createServer();
server.on('error', (err: Error) => { throw err; });
server.on('connection', newConn);
```

当传输从任何一方结束时，套接字会被运行时自动关闭。`net.Socket` 上还有一个 `'error'` 事件用于报告 IO 错误。该事件也会导致运行时关闭套接字。

*(注：由于原文中从 Step 6 之后出现了大量重复的描述和乱码片段，译文已按要求去除了重复部分。)*

Promise 可以被视为管理回调的另一种方式。它们也被描述为 `asynchronous`（异步），意味着结果是通过回调传递的。这些 API 不会阻塞事件循环，因为 JS 代码不会等待结果；相反，JS 代码会返回运行时，当结果就绪时，运行时会调用回调来继续你的程序。

与之相反的是 `synchronous`（同步）API，它会阻塞调用的操作系统线程以等待结果的产生。例如，让我们来看 `fs` 模块的文档，文件 API 在[所有 3 种](https://nodejs.org/api/fs.html)中可用。

```javascript
// promise
filehandle.read([options]);

// callback
fs.read(fd[, options], callback);

// synchronous, do not use!
fs.readSync(fd, buffer[, options]);
```

在网络应用中，你**不会**使用同步 API，因为它会阻塞事件循环。它们存在于某些简单的用例（如脚本），这些场景完全不依赖事件循环。

## 跨越网络的事件编程

IO 不仅仅是磁盘文件和网络。在 GUI 系统中，来自鼠标和键盘的用户输入也是 IO。而且事件循环并不是 Node.js 运行时特有的；Web 浏览器所有其他 GUI 应用程序底层也使用事件循环。你可以将 GUI 编程经验转移到网络编程，反之亦然。

[3](https://nodejs.org/api/fs.html)

[报告错误 | 提问](https://forms.gle/UKo4bncUnuMGBrTM7) @ [build-your-own.org](https://build-your-own.org)

17

2024-02-02

## 03. 代码一个 TCP 服务器

## 3.7 讨论：基于 Promise 的 IO

正如我们之前提到的，还有另一种编写 IO 代码的风格。另一种风格使用 Promise 代替回调。基于 Promise 的 API 的优势是你可以对它们进行 `await` 并获取结果，从而避免将你的程序拆散成散落在各处的微小回调。

一个假设的基于 Promise 的 `accept` 原语 API 如下：

```javascript
// 伪代码!
while (running) {
  let socket = await server.accept();
  newConn(socket);
  // 此处不要 await
}
```

而假设的 `read` 和 `write` 原语的 API 如下：

```javascript
// 伪代码!
async function newConn(socket) {
  while (true) {
    let data = await socket.read();
    if (!data) {
      break;
      // EOF
    }
    await socket.write(data);
  }
}
```

上面的伪代码看起来是同步的，但并没有阻塞事件循环。虽然在这一点上优势可能并不明显，因为我们的程序非常简单。

一些 Node.js API（但不是所有）同时可以在基于回调和基于 Promise 的风格中使用。然而，通过努力，基于回调的 API 可以转换为基于 Promise 的 API，正如我们将在下一节中看到的。

[报告错误 | 提问](https://forms.gle/UKo4bncUnuMGBrTM7) @ [build-your-own.org](https://build-your-own.org)

18

## 第 04 章

## Promise 与事件

在本章中，我们将再次实现回显服务器，但将使用基于 Promise 的风格，这是本书其余部分的基础。这一决定将在后文解释。

## 4.1 async 和 await 简介

让我们快速浏览 JS 中的 `async`/`await` 和 `Promise` 类型，以防你尚不熟悉它们。

### 使用回调

一个基于回调的 API 示例。应用逻辑在回调函数中继续。

```javascript
function my_app() {
  do_something_cb((err, result) => {
    if (err) {
      // 失败。
    } else {
      // 成功，使用结果。
    }
  });
}
```

### 使用 Promises 和 await

在 promise 上使用 `await` 的示例。应用逻辑在同一个 async 函数中继续。

```javascript
function do_something_prmoise(): Promise<T>;
async function my_app() {
  try {
    const result: T = await do_something_prmoise();
  } catch (err) {
    // 失败。
  }
}
```

优势：应用逻辑没有被拆分成多个函数。

### 创建 Promise

创建一个 promise 的示例：将基于回调的 API 转换为基于 Promise 的 API。

```javascript
function do_something_prmoise() {
  return new Promise<T>((resolve, reject) => {
    do_something_cb((err, result) => {
      if (err) {
        reject(err);
      } else {
        resolve(result);
      }
    });
  });
}
```

回调在 JS 中是不可避免的。在创建 promise 对象时，会将一个 `executor` 回调作为参数传递，以接收两个回调：

- `resolve()` 导致 `await` 语句返回一个值。
- `reject()` 导致 `await` 语句抛出一个异常。

当结果可用或操作失败时，你必须调用其中一个。这可能发生在执行器函数之外，因此你可能需要存储这些结果。

Promise 的术语：

- **Fulfilled**（已完成）：调用了 `resolve()`
- **Rejected**（已拒绝）：调用了 `reject()`
- **Settled**（已就决）：已完成或已拒绝。
- **Pending**（进行中）：未就决。

19

2024-02-02

## 04. Promise 与事件

## 4.2 理解 async 和 await

### 普通函数通过 return 返回

有两种 JS 函数：普通函数和 async 函数。普通函数从开始到返回（显式或隐式）。由于 JS 运行时是单线程的，你无法进行阻塞，相反你注册回调，运行时可以轮询事件。

### async 函数通过 await 返回

最初，`Promise` 类型只是管理回调的方式。它允许链式多个嵌套函数。然而，由于 async 函数的加入，我们不再需要这种 promise 使用。async 函数可以在执行中间返回运行时；这发生在对 promise 使用 `await` 语句时。

### 调用 async 函数启动新任务

调用 async 函数会导致一个在返回或抛出异常时决定的 promise。你可以像普通 promise 一样等待它，但它会被运行时调度。这类似于多线程编程中启动线程。但所有的 JS 代码共享单个线程，所以更好的词是 *任务*。

在不同环境中启动任务的方法：

- 在 JS 中，通过不等待 promise 启动任务。
- 在 Go 中，使用 `go` 语句。
- 在 Python 中，async/await 与 JS 类似，但你需要自己运行事件循环，因为它不是语言内置的。
- 在没有事件循环的环境中，你可以启动操作系统线程而不是用户级任务。

## 4.3 从事件到 Promise

`net` 模块未提供基于 Promise 的 API，因此我们需要实现上一节中的假设 API。

```typescript
function soRead(conn: TCPConn): Promise<Buffer>;
function soWrite(conn: TCPConn, data: Buffer): Promise<void>;
```

[报告错误 | 提问](https://forms.gle/UKo4bncUnuMGBrTM7) @ [build-your-own.org](https://build-your-own.org)

20

2024-02-02

### 步骤 1：分析解决方案

`soRead` 函数返回一个带有 socket 数据的 promise。它依赖 3 个事件。

1. `'data'` 事件完成 promise。
2. 在读取 socket 时，我们还需要知道是否发生了 EOF。因此，`'end'` 事件也会完成 promise。指示 EOF 的常用方法是返回零长度的数据。
3. 还有一个 `'error'` 事件，当此事件发生时，我们想要拒绝该 promise，否则 promise 将永远挂起。

为了通过这些事件解析或拒绝 promise，必须将 promise 存储在某个地方。

为此，我们将创建一个 `TCPConn` 包装对象。

```typescript
// 一个基于 promise 的 TCP 套接 API。

type TCPConn = {
  // JS socket 对象
  socket: net.Socket;
  // 当前读取操作 promise 的回调函数
  reader: null | {
    resolve: (value: Buffer) => void,
    reject: (reason: Error) => void,
  };
};
```

promise 的 `resolve` 和 `reject` 回调存储在 `TCPConn.reader` 字段中。

### 步骤 2：处理 'data' 事件

现在让我们尝试实现 `'data'` 事件。这里我们有一个问题：每当数据到达时都会触发 `'data'` 事件，但 promise 只有在程序从 socket 读取数据时才存在。因此，我们必须有一种方法来控制 `'data'` 事件何时准备触发。

```javascript
socket.pause(); // 暂停 'data' 事件
socket.resume(); // 恢复 'data' 事件
```

有了这些知识，我们现在可以实现 `soRead` 函数。

```typescript
// 从 net.Socket 创建包装器
function soInit(socket: net.Socket): TCPConn {
  const conn: TCPConn = {
    socket: socket, reader: null,
  };
  socket.on('data', (data: Buffer) => {
    console.assert(conn.reader);
    // 暂停 'data' 事件直到下次读取。
    conn.socket.pause();
    // 完成当前读取的 promise。
    conn.reader!.resolve(data);
    conn.reader = null;
  });
  return conn;
}

function soRead(conn: TCPConn): Promise<Buffer> {
  console.assert(!conn.reader);
  // 不并发调用
  return new Promise((resolve, reject) => {
    // 保存 promise 回调
    conn.reader = {resolve: resolve, reject: reject};
    // 恢复 'data' 事件以便稍后完成 promise。
    conn.socket.resume();
  });
}
```

由于 `'data'` 事件会在我们读取 socket 之前被暂停，因此 socket 在创建后默认应该是暂停状态。有一个标记可以实现这一点。

```javascript
const server = net.createServer({
  pauseOnConnect: true,
  // TCPConn 需要
});
```

### 步骤 3：处理 'end' 和 'error' 事件

与 `'data'` 事件不同，`'end'` 和 `'error'` 事件无法暂停，并且会在发生时立即触发。我们可以通过将它们存储在包装对象并在 `soRead` 中检查它们来处理。



```typescript
// 一个基于 promise 的 TCP 套接 API。
type TCPConn = {
  // JS socket 对象
  socket: net.Socket;
  // 来自 'error' 事件
  err: null | Error;
  // 来自 'end' 事件
  ended: boolean;
  // 当前读取操作 promise 的回调函数
  reader: null | {
    resolve: (value: Buffer) => void;
    reject: (reason: Error) => void;
  };
};

// 如果存在当前 reader，解析或拒绝它。
// 从 net.Socket 创建包装器
function soInit(socket: net.Socket): TCPConn {
  const conn: TCPConn = {
    socket: socket,
    err: null,
    ended: false,
    reader: null,
  };
  socket.on('data', (data: Buffer) => {
    // 省 ...
  });
  socket.on('end', () => {
    // 这也完成了当前的读取。
    conn.ended = true;
    if (conn.reader) {
      conn.reader.resolve(Buffer.from(''));
      conn.reader = null;
    }
  });
  socket.on('error', (err: Error) => {
    // 错误也会传递给当前读取。
    conn.err = err;
    if (conn.reader) {
      conn.reader.reject(err);
      conn.reader = null;
    }
  });
  return conn;
}

// 在 soRead 之前发生的事件会被存储并检查。
// 在 EOF 后返回一个空 Buffer。
function soRead(conn: TCPConn): Promise<Buffer> {
  console.assert(!conn.reader);
  return new Promise((resolve, reject) => {
    // 如果连接不可读，现在完成 promise。
    if (conn.err) {
      reject(conn.err);
      return;
    }
    if (conn.ended) {
      resolve(Buffer.from(''));
      return;
    }
    // 保存 promise 回调
    conn.reader = { resolve: resolve, reject: reject };
    // 恢复 'data' 事件以便稍后完成 promise。
    conn.socket.resume();
  });
}
```

### 步骤 4：写入 Socket

`socket.write` 方法接受一个回调函数来通知写入完成，因此转换为 promise 是轻而易举的。

```typescript
function soWrite(conn: TCPConn, data: Buffer): Promise<void> {
  console.assert(data.length > 0);
  return new Promise((resolve, reject) => {
    if (conn.err) {
      reject(conn.err);
      return;
    }
    conn.socket.write(data, (err?: Error) => {
      if (err) {
        reject(err);
      } else {
        resolve();
      }
    });
  });
}
```

Node.js 文档中还有一个 `'drain'` 事件可以用于此任务。Node.js 库通常会提供多种方法来实现相同的功能，你只需要选择其中一种并忽略其他的即可。

### 4.3 使用 async 和 await

让我们回到回声服务器的实现。为了在基于 promise 的 API 上使用 `await`，新连接的处理程序（`newConn`）变成了一个 `async` 函数。

```typescript
async function newConn(socket: net.Socket): Promise<void> {
  console.log('new connection', socket.remoteAddress, socket.remotePort);
  try {
    await serveClient(socket);
  } catch (exc) {
    console.error('exception:', exc);
  } finally {
    socket.destroy();
  }
}
```

我们还将代码封装在 `try-catch` 块中，因为当 promise 被拒绝时 `await` 语句会抛出异常。尽管在生产代码中你可能希望实际处理错误而不是使用通用的异常处理器。

```typescript
// 回声服务器
async function serveClient(socket: net.Socket): Promise<void> {
  const conn: TCPConn = soInit(socket);
  while (true) {
    const data = await soRead(conn);
    if (data.length === 0) {
      console.log('end connection');
      break;
    }
    console.log('data', data);
    await soWrite(conn, data);
  }
}
```

现在使用 socket 的代码变得直观了。没有回调来中断业务逻辑。

注意 `newConn` `async` 函数没有在任何地方被 `await`。它只是被作为监听 socket 回调调用的。这意味着多个连接是并发处理的。

读者的练习：将“接受”原语转换为基于 promise 的。

```typescript
type TCPListener = {
  socket: net.Socket;
  // ...
};

function soListen(...): TCPListener;

function soAccept(listener: TCPListener): Promise<TCPConn>;
```

## 4.5 讨论：背压

**等待 Socket 写入完成？**

我们新的回声服务器有一个很大的不同——我们现在等待 `socket.write()` 完成。

但“写入完成”意味着什么？为什么我们必须等待它完成？这个问题实际上比网络编程本身更深层。

**生产者受消费者限制**

只要有异步通信，就有连接生产者和消费者的队列或缓冲区。在物理世界中，队列和缓冲区的大小是有边界的，无法存储无限的数据。异步通信的一个问题是，**当生产者生产速度大于消费者速度时会发生什么**？必须有一种机制来防止队列或缓冲区溢出。这种机制在网络应用中通常被称为 `backpressure`（背压）。

## TCP 中的背压：流量控制

TCP 中的背压被称为 `flow control`（流量控制）。

- 消费者 TCP 栈将接收到的数据存储在接收缓冲区中，供应用程序消费。
- 生产者 TCP 栈可以发送的数据量受生产者 TCP 栈知的 `window`（窗口）限制，当 `window` 满时，它将 `pause` 发送数据。
- 消费者 TCP 栈管理 `window`；当应用程序从接收缓冲区中提取数据时，它会向前 `move` `window` 并通知生产者 TCP 栈 `resume`（恢复）发送。

流量控制的效果：`TCP` 可以暂停和恢复传输，从而使消费者的接收缓冲区保持边界。

```
flow ctrl

bounded!

|producer| ==> |send buf| ===========> |recv buf| ==> |consumer|

app

OS

TCP

OS

app
```

`TCP` 流量控制不应与 `TCP` 拥塞控制混淆，后者也控制 `window`。

## 应用与操作系统之间的背压

这种良好的机制不仅需要实现在 `TCP` 中，还需要在应用程序中。

让我们关注生产者。应用程序产生数据并提交给 `OS`，数据进入 `send buffer`（发送缓冲区），`TCP` 栈从 `send buffer` 消费数据并传输数据。

```
write()

may block!

|producer| ========> |send buf| =====> ...

app

OS

TCP
```

## 04. Promises 和事件

`OS` 如何防止 `send buffer` 溢出？简单，当 `buffer` 满时，应用程序无法写入更多数据。现在由应用程序负责自我节流以防止过度生产，因为数据必须去某个地方，但内存是有限的。

如果应用程序正在执行阻塞 IO，当 `send buffer` 满时调用将会阻塞，因此背压变得轻而易举。然而，在 `JS` 中使用事件循环进行编码时，情况并非如此。

### 无界队列是陷阱（Footguns）

我们现在可以回答这个问题了：为什么要等待写入完成？因为当应用程序等待时，它无法产生数据！即使运行时由于 `send buffer` 满而无法向 `OS` 提交更多数据，`socket.write()` 也会总是成功，但数据必须去往某个地方，它进入了运行时中的一个无界内部队列，这是一个导致可能导致无限内存占用的陷阱。

```
write()

unbounded!

event loop

|producer| ======> |internal queue| =========> |send buf| =====> ...

app

Node.js

OS

TCP
```

以我们旧的 echo 服务器为例，服务器既是生产者也是消费者，客户端也是如此。如果客户端产生数据的速度比它消费回显数据的速度快（或者客户端完全不消费任何数据），如果服务器不等待写入完成，服务器的内存将无限增长。

在任何连接生产者和消费者的系统中，都应该存在背压。一个经验法则是寻找软件系统中的无界队列，因为它们是缺乏背压的信号。

## 4.6 讨论：事件和有序执行

与旧版本的另一个不同点是使用了 `socket.pause()`。你现在可以理解为什么这至关重要，因为它被用于实现背压。

暂停 `'data'` 事件还有另一个原因。在基于回调的代码中，当事件处理程序返回时，如果没有暂停，运行时可以触发下一个 `'data'` 事件。问题在于，**事件回调的完成并不意味着事件处理的完成**——处理可以通过随后的回调继续。而且考虑到数据是字节的有序序列，交错处理（interleaved handling）可能会导致问题！

这种情况被称为 `race condition`（竞态条件），是一类与并发相关的问题。在这种情况下，引入了意外的并发。

## 4.7 结论：Promise vs 回调

遵循上述讨论，我们现在可以解释为什么我们切换到基于 promise 的 API，因为它们有优势。

- 如果你坚持使用 `promises` 和 `async/await`，很难创建上述的竞态条件，因为事情是按顺序发生的。
- 使用基于回调的代码，不仅更难理解代码执行的顺序，也更难控制顺序。简之，回调更难读，且编写时更容易出错。

使用基于 `promise` 的风格时，背压是自然存在的。这类似于使用阻塞 IO 编码（这在 `Node.js` 中无法实现）。

我们已经学习了 `socket` API 的基础。让我们进入下一个主题：协议。

## CHAPTER 05: 简单的网络协议

## 5.1 消息 Echo 服务器

解析 `HTTP` 是一项大量工作，所以让我们先迈出一小步。我们将实现一个更简单的协议来演示协议最重要的功能：将字节流拆分为消息。

我们的协议由 `'\n'`（换行符）分隔的消息组成。服务器读取消息并使用相同的协议发送回复。

- 如果客户端发送 `'quit'`，回复 `'Bye.'` 并关闭连接。
- 否则，带前缀 `'Echo: '` 回显消息。

```
client

server

\------

\------

msg1\n

==>

<==

Echo: msg1\n

msg2\n

==>

<==

Echo: msg2\n

quit\n

==>

<==

Bye.\n
```

## 5.2 动态缓冲区

### 动态缓冲区的必要

消息并不是直接来自 `socket` 本身，我们需要将接收到的数据存储在 `buffer` 中，然后我们可以尝试从中拆分消息。

`Node.JS` 中的 `Buffer` 对象是固定大小的二进制数据块。它不能通过追加数据来增长。我们可以做的是将两个 `buffers` 合并为一个 `buffer`。

```
buf = Buffer.concat([buf, data]);
```

然而，这是一种反模式，会导致 `O(n2)` 算法复杂度。

```
// 伪代码！坏的例子！

while (need_more_data()) {

  buf = Buffer.concat([buf, get_some_data()]);
}
```

每当通过合并追加新数据时，旧数据都会被复制。为了分摊拷贝成本，使用了*动态数组*：

- C++: `std::vector` 和 `std::string`。
- Python: `bytearray`。
- Go: `slice`。

### 编写动态缓冲区

`buffer` 必须比需要的数据大，以便利用额外容量分摊拷贝。`DynBuf` 类型存储实际的数据长度。

```typescript
// 一个动态大小的缓冲区
type DynBuf = {
  data: Buffer;
  length: number;
};
```

`copy()` 方法的语法是 `src.copy(dst, dst_offset, src_offset)`。这用于追加数据。

```typescript
// append data to DynBuf
function bufPush(buf: DynBuf, data: Buffer): void {
  const newLen = buf.length + data.length;
  if (buf.data.length < newLen) {
    // 增长容量 ...
  }
  data.copy(buf.data, buf.length, 0);
  buf.length = newLen;
}
```

`Buffer.alloc(cap)` 创建一个指定大小的新缓冲区。这用于调整缓冲区大小。新缓冲区必须*指数级*增长，以便分摊成本为 `O(1)`。我们将使用 2 的幂序列作为缓冲区容量。

```typescript
// append data to DynBuf
function bufPush(buf: DynBuf, data: Buffer): void {
  const newLen = buf.length + data.length;
  if (buf.data.length < newLen) {
    // 按 2 的幂增长容量
  }
}
```

[报告错误 | 提问](https://forms.gle/UKo4bncUnuMGBrTM7) @ [build-your-own.org](https://build-your-own.org)

32

2024-02-02

# 05. 简单的网络协议

```javascript
let cap = Math.max(buf.data.length, 32);

while (cap < newLen) {
  cap *= 2;
}

const grown = Buffer.alloc(cap);
buf.data.copy(grown, 0, 0);
buf.data = grown;

} 

data.copy(buf.data, buf.length, 0);
buf.length = newLen;

}
```

## 5.3 实现消息协议

### 步骤 1：服务器循环

从高层来说，服务器应该是一个循环。

1. 从传入的字节流中解析并移除一个完整的消息。
   - 向缓冲区中追加一些数据。
   - 如果消息不完整，则继续循环。
2. 处理消息。
3. 发送响应。



```javascript
async function serveClient(socket: net.Socket): Promise<void> {
  const conn: TCPConn = soInit(socket);
  const buf: DynBuf = {data: Buffer.alloc(0), length: 0};
  while (true) {
    // 尝试从缓冲区获取 1 条消息
    const msg: null|Buffer = cutMessage(buf);
    if (!msg) {
      // 需要更多数据
      const data: Buffer = await soRead(conn);
      bufPush(buf, data);
      // EOF?
      if (data.length === 0) {
        // 省略 ...
        return;
      }
      // 获取了部分数据，再次尝试。
      continue;
    }
    // 省略。处理消息并发送响应 ...
  } // 消息循环
}
```

Socket 读取与任何消息边界都无关。我们所做是将数据追加到缓冲区，直到它包含一条完整的消息。

`cutMessage()` 函数判断消息是否完整。

- 如果不完整，返回 `null`。
- 否则，它移除并返回该消息。

### 步骤 2：拆分消息

`cutMessage()` 函数使用分隔符 `\n` 测试消息是否完整。

```javascript
function cutMessage(buf: DynBuf): null|Buffer {
  // 消息通过 '\n' 分隔
  const idx = buf.data.subarray(0, buf.length).indexOf('\n');
  if (idx < 0) {
    return null;
    // 未完成
  }
  // 制作消息的副本并将剩余数据移动到头部
  const msg = Buffer.from(buf.data.subarray(0, idx + 1));
  bufPop(buf, idx + 1);
  return msg;
}
```

然后它会创建消息数据的副本，因为数据将从缓冲区中移除。

- `buf.subarray()` 返回子数组的引用，而不进行复制。
- `Buffer.from()` 通过从源复制数据创建一个新的缓冲区。

通过将剩余数据移动到头部来移除消息。

```javascript
// 从头部移除数据
function bufPop(buf: DynBuf, len: number): void {
  buf.data.copyWithin(0, len, buf.length);
  buf.length -= len;
}
```

`buf.copyWithin(dst, src_start, src_end)` 在缓冲区内复制数据，源和目的地可以重叠，类似于 C 语言中的 `memmove()`。这种处理缓冲区的方式并不理想，稍后会详细讨论。

### 步骤 3：处理请求

请求在服务器循环中被处理并发送响应。

```javascript
while (true) {
  // 尝试从缓冲区获取 1 条消息
  const msg = cutMessage(buf);
  if (!msg) {
    // 省略 ...
    continue;
  }
  // 处理消息并发送响应
  if (msg.equals(Buffer.from('quit\n'))) {
    await soWrite(conn, Buffer.from('Bye.\n'));
    socket.destroy();
    return;
  } else {
    const reply = Buffer.concat([Buffer.from('Echo: '), msg]);
    await soWrite(conn, reply);
  }
} // 消息循环
```

我们的消息回显服务器现在完成了。使用 `socat` 命令对其进行测试。

## 5.4 讨论：流水线请求

当从缓冲区中移除消息时，我们将剩余数据移动到了头部。

你可能会奇怪，为什么缓冲区中还会剩下数据，因为在请求-响应场景中，客户端会在发送更多请求之前等待响应的。这是为了支持一种优化。

### 通过流水线请求减少延迟

考虑一个典型的现代网页，……（文本根据提供的片段继续进行技术解构）。

## 5.6 结论：网络编程基础

到目前为止我们学到的总结：

- `socket` API：`listen`、`accept`、`read`、`write` 等。
- 事件循环及其影响。
- 回调（Callback）对比 `Promise`。使用 `async` 和 `await`。
- 背压（Backpressure）、队列和缓冲区。
- TCP 字节流、协议解析器、流水线消息。

[报告错误 | 提问](https://forms.gle/UKo4bncUnuMGBrTM7) @ [build-your-own.org](https://build-your-own.org)

# 第 06 章

## HTTP 语义与语法

HTTP 非常具有人类可读性，这意味着你可以通过查看示例而不是规范来构建服务器。然而，这种方法会导致产生 Bug 的“玩具代码”，而且你并学不到什么东西。因此，你需要查阅规范——一系列 `RFC` 文档。

## 6.1 高级结构

让我们回顾一下你在介绍性章节中已经掌握的内容：

- 一个 HTTP 请求消息包含：
    - 方法（Method），是一个如 `GET`、`POST` 的动词。
    - `URI`。
    - 头部字段（Header fields）列表，一组键值对。
    - 负载体（Payload body），紧跟请求头之后。特殊情况：`GET` 和 `HEAD` 没有负载。

- 一个 HTTP 响应包含：
    - 状态码（Status code），主要用于指示请求是否成功。
    - 头部字段列表。
    - 可选的负载体。

这些内容从 `HTTP/1.0` 到 `HTTP/3` 大多数是相同的。

```
HTTP/1.0 200 OK
Age: 525410
Cache-Control: max-age=604800
Content-Type: text/html; charset=UTF-8
Date: Thu, 20 Oct 2020 11:11:11 GMT
Etag: "1234567890+gzip+ident"
Last-Modified: Thu, 20 Oct 2019 11:11:11 GMT
Vary: Accept-Encoding
Content-Length: 1256
Connection: close

<!doctype html>
<!-- omitted -->
```

## 6.2 Content-Length

HTTP 语义大多关于头部字段的解释，这在 [RFC](https://www.rfc-editor.org/rfc/rfc9110.html) [9110](https://www.rfc-editor.org/rfc/rfc9110.html) 中描述。尝试自己读读它。

最重要的头部字段是 `Content-Length` 和 `Transfer-Encoding`，因为它们决定了 HTTP 消息的长度，这是协议最重要的功能。

### HTTP 头部长度

请求和响应都包含两个部分：头部（header） + 实体（body）。它们由一个空行分隔。行以 `\r\n` 结束。因此，头部包括空行结束于 `\r\n\r\n`。这就是我们确定头部长度的方法。

### HTTP 实体长度

体的长度很复杂，因为有 3 种方法确定它。第一种方法是使用 `Content-Length`，它包含了体的长度。

一些古旧的 `HTTP/1.0` 软件不使用 `Content-Length`，因此体就是连接剩余的数据，解析器读取 `socket` 直到 `EOF`，这就是体。这是确定体长度的第二种方法。这种方法有问题，因为你无法判断连接是否提前结束。

## 6.3 分块传输编码 (Chunked Transfer Encoding)

### 动态生成并发送数据

第三种方法是使用 `Transfer-Encoding: chunked` 代替 `Content-Length`。这被称为*分块传输编码*。它允许服务器在生成响应时发送负载，而无需提前知道大小。这种用例被称为 *流式传输（streaming）*。

### 协议的另一层

分块编码是如何工作的？作为接收方，我们不知道总负载长度，但我们知道负载的部分。特殊的块标记了结束。这里有一个具体的例子：

```
4\r\nHTTP\r\n
5\r\n0\r\n
```

它被解析为 3 块：

- `4\r\nHTTP\r\n`
- `5\r\n`
- `0\r\n`

## 6.4 歧义

### 理想情况

总结来说，`HTTP` 允许：

1. 存在 `Transfer-Encoding: chunked`。
2. `Content-Length: number`有效。
3. 如果两者都不存在，使用连接剩余部分。

### 糟糕情况

读者的练习：如果你正在设计一种新协议，如何避免这种情况？

## 6.5 HTTP 消息格式

[RFC 9112](https://www.rfc-editor.org/rfc/rfc9112.html) 描述了比特如何在网络上传输。

### 阅读 BNF 语言

HTTP 消息格式用名为 *BNF* 的语言描述。前往 RFC 9112 的“2. Message”章节，你会看到这样的内容：

```
HTTP-message
= start-line CRLF
*( field-line CRLF )
CRLF
[ message-body ]

start-line
= request-line / status-line
```

这表示：HTTP 消息可以是请求消息或响应消息。消息以请求行或状态行开始，随后是多个头部字段，然后是空行，最后是可选的负载体。行与 `CRLF` 分隔，`CRLF` 是 ASCII 字符串 `\r\n`。BNF 语言比英语更简洁且歧义更少。

### 头部字段

```
field-line
= field-name ":" OWS field-value OWS
```

头部字段名和值由冒号分隔，但字段名和值的规则定义在 RFC 9110 中。

```
field-name
= token

token
= 1*tchar

tchar
= "!" / "#" / "$" / "%" / "&" / "'" / "*"
/ "+" / "-" / "." / "^" / "_" / "`" / "|" / "~"
/ DIGIT / ALPHA
```

```
OWS
= *( SP / HTAB )
```

```
field-value
= *field-content

field-content
= field-vchar
[ 1*( SP / HTAB / field-vchar ) field-vchar ]
```

`field-vchar`
= `VCHAR` / `obs-text`

`obs-text`= `%x80-FF`

这是字段名和值的通用规则。`SP`、`HTAB` 和 `VCHAR` 分别指空格、制表符和打印 ASCII 字符。某些字符禁止在头部字段中使用，特别是 `CR` 和 `LF`。

[4](https://www.rfc-editor.org/rfc/rfc9112.html)

[报告错误 | 提问](https://forms.gle/UKo4bncUnuMGBrTM7) @ [build-your-own.org](https://build-your-own.org)

## 6.6 常见头部字段

许多头部字段要么被应用程序解释，要么被可选的 HTTP 特性使用，与我们的实现没有直接关系。你可以通过浏览器开发者工具中检查 HTTP 头部来熟悉它们。

表 1：常见头部字段。（C 代表客户端，S 代表服务器。）

| 头部字段 | 由谁提供 | 描述 |
| :--- | :--- | :--- |
| `Content-Length: 60` | C/S | 已讨论。 |
| `Transfer-Encoding: chunked` | C/S | 已讨论。 |
| `Accept: text/html` | C | 用于协商内容类型。 |
| `Content-Type: text/html` | S | 内容类型。 |
| `Accept-Encoding: gzip` | C | 用于协商内容压缩。 |
| `Content-Encoding: gzip` | S | 压缩后的响应。 |
| `Vary: content-encoding` | S | 通知代理服务器内容协商。 |
| `Authorization: Basic dTpw` | C | 通过用户名和密码进行认证。 |
| `Cache-Control: no-cache` | C/S | 影响缓存行为。 |
| `Age: 60` | S | 项目被代理缓存了多久？ |
| `Set-Cookie: k=v` | S | HTTP cookie。 |
| `Cookie: k=v` | C | HTTP cookie。 |
| `Date` | C/S | 不怎么有用。 |
| `Expect: 100-continue` | C | 一个冷门的特性。 |
| `Host: example.com` | C/S | URL 的主机名。 |
| `Last-Modified` | S | 用于缓存验证和 304 Not Modified。 |
| `If-Modified-Since` | C | 验证 `Last-Modified`。 |
| `ETag: abcd` | S | 用于缓存验证和 304 Not Modified。 |
| `If-None-Match: abcd` | C | 验证 `ETag`。 |
| `Range: 10-` | C | 范围请求。获取响应的一部分。 |
| `Content-Range: bytes 10-/60` | S | 范围响应。 |
| `Accept-Ranges: bytes` | S | 表示允许范围请求。 |
| `Referer: http://foo.com/` | C | 用户来自哪里？ |
| `Transfer-Encoding: gzip` | S | 实现压缩的另一种方式。 |
| `TE: gzip` | C | 用于协商 `Transfer-Encoding`。 |
| `Trailer: Foo` | C/S | 冷门特性：负载之后的头部字段。 |
| `User-Agent: Foo` | C | 客户端软件。 |
| `Server: Foo` | S | 服务器软件。 |
| `Upgrade: websocket` | C/S | 创建 WebSocket。 |
| `Access-Control-*` | S | 跨资源共享 (CORS)。 |
| `Origin` | C | CORS。 |
| `Location: http://bar.com/` | S | 用于 3xx 重定向。 |

## 6.7 HTTP 方法

### 只读方法

最重要的 HTTP 方法是 `GET` 和 `POST`。为什么我们需要不同的 HTTP 方法？除了 `POST` 可以携带负载而 `GET` 不能的事实外，将只读操作与写操作分开也是一个好主意。只读方法被称为“安全”方法：

- `GET`。
- `HEAD`，类似于 `GET` 但没有响应体。
- `OPTIONS`，很少使用，用于识别允许的方法和 CORS。

### 可缓存性

将只读操作与写操作分开的一个原因是只读操作通常是可以缓存的。另一方面，缓存写操作没有意义，因为它们会改变状态。然而，缓存性的规则比不同的 HTTP 方法更复杂：

- `GET` 和 `HEAD` 被认为是可缓存的。但 `OPTIONS` 不是，因为它有特殊用途。
- 状态码也会影响缓存性。
- `Cache-Control` 头部可以影响缓存性。
- `POST` 通常不可缓存，除非使用了冷门头部（`Content-Location`）且存在某些缓存指令。
- 不同实现有不同的缓存规则。[5](https://www.rfc-editor.org/rfc9110.html)

### CRUD 与资源

你可能奇怪为什么会有这么多 HTTP 方法。难道 `GET` 和 `POST` 不够吗？事实上，许多应用程序正是这样做的。HTTP 添加更多方法是因为人们将 HTTP 想象成管理“资源”的协议。例如，论坛用户可以像操作资源一样操作帖子：

- 通过 `PUT` 创建帖子。
- 通过 `GET` 读取帖子。



- 通过 `PATCH` 更新帖子。
- 通过 `DELETE` 删除帖子。

这 4 个动词通常被称为 **CRUD**。

### 等幂性

但为什么要将 CRUD 作为 HTTP 方法呢？论坛用户可能会将帖子移动到另一个论坛，HTTP 是否应该包含一个 `MOVE` 方法？镜像任意英语动词并不是定义 HTTP 方法的好理由。更好的理由之一是定义操作的等幂性。

等幂操作是可以重复产生相同效果的操作。这意味着你可以安全地重试操作直到它成功。例如，如果你通过 SSH `rm` 一个文件，在看到结果之前连接断开了，那么你不知道文件的状态，但你可以一直盲目地再次 `rm`（如果真的是同一个文件）：

- 如果你失败了，可能会再次失败。
- 如果之前的 `rm` 失败了但这次成功了，你的意图就实现了。
- 如果之前的 `rm` 成功了，再次执行也没有害。

HTTP 中的等幂操作可能导致不同的状态码，就像 `rm` 的返回码一样。

HTTP 中的等幂性：

- 只读方法（`GET` 和 `HEAD`）显然是等幂的。
- `PUT` 和 `DELETE` 是等幂的，删除文件。
- `POST` 和 `PATCH` 没有被定义为等幂。它们可能或不是。

浏览器中的等幂性：

- 如果你通过 `POST` 提交 `<form>` 然后刷新页面，浏览器会警告你不要提交可能非等幂的表单。
- HTML 表单限制于 `GET` 和 `POST`[6](https://softwareengineering.stackexchange.com/a/211790)。你需要 AJAX 来使用这些等幂方法。

[6](https://softwareengineering.stackexchange.com/a/211790)

[报告错误 | 提问](https://forms.gle/UKo4bncUnuMGBrTM7) @ [build-your-own.org](https://build-your-own.org)

---

# 06. HTTP 语义与语法

但这还没有回答为什么会有这么多动词之谜，因为 HTTP 只需要为等幂写入增加 1 个方法，而不是 3 个（`PATCH`、`PUT`、`DELETE`）。事实上，可能没有强力理由应用程序使用所有它们。

**HTTP 方法对比**

通用 HTTP 方法总结。

| 动词 | 安全 | 等幂 | 可缓存 | `<form>` | CRUD | 请求体 | 响应体 |
| :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- |
| GET | 是 | 是 | 是 | 是 | 读取 | | 是 |
| HEAD | 是 | 是 | 是 | 否 | 读取 | | 否 |
| POST | 否 | 否 | * | 是 | - | 是 | 是 |
| PATCH | 否 | 否 | * | 否 | 更新 | 是 | 是 |
| PUT | 否 | 是 | 否 | 否 | 创建 | 是 | 否 |
| DELETE | 否 | 是 | 否 | 否 | 删除 | 可能 | 可能 |

注：可缓存 `POST` 或 `PATCH` 是可能的，但很少支持。

HTTP 的设计允许从 `telnet` 发送请求，因此你可以通过尝试来学习它。然而，文本协议也有缺点。

**文本通常具有歧义**

一个缺点是，人类可读格式通常机器可读性较低，因为它们比所需的更灵活。考虑 HTTP 负载长度的确定方式：

- 常见的情况是 `Content-Length` 和 `Transfer-Encoding`。
- 某些 HTTP 方法和状态码有特殊情况。
- 存在会导致不同解释的情况，例如 `request smuggling`（请求走私）。

HTTP 是一个简单的协议，简单意味着它易于观察。为它编写代码并不简单，因为解释它的规则太多了，而且这些规则仍然会留下歧义。

[报告错误 | 提问](https://forms.gle/UKo4bncUnuMGBrTM7) @ [build-your-own.org](https://build-your-own.org)

---

## 文本更容易且容易出错

另一个缺点是处理文本的工作量大得多。为了正确处理文本字符串，你首先需要知道它们的长度，这通常是由分隔符决定的。寻找分隔符的额外工作是人类可读格式的代价。

它也很出错；在 C 语言编程中，空终止字符串（0 分隔符）已导致许多安全漏洞。

HTTP/2 是二进制的，并且比 HTTP/1.1 更复杂，但解析该协议仍然更容易，因为你不需要处理未知长度的元素。

## 6.9 讨论：分隔符

### 分隔数据中的序列化错误

分隔符在文本协议中无处不在。例如，在 HTTP 中……

- 头部行由 `CRLF` 分隔
- 头部和正文由空行分隔。

分隔符的一个问题是数据不能包含分隔符本身。未能强制执行此规则会导致某些注入攻击。

如果恶意客户端可以欺骗有错误的服务器输出包含 `CRLF` 的头部字段值，且该头部字段是最后一个字段，那么负载体将从攻击者控制的字段值部分开始。这被称为 [“HTTP 响应拆分”[7]](https://en.wikipedia.org/wiki/HTTP_response_splitting)。

适当的 HTTP 服务器/客户端必须禁止头部字段中的 `CRLF`，因为没有办法对其进行编码。然而，对于许多通用数据格式，情况并非如此。例如，JSON 使用 `{}[],: ` 来分隔元素，但 JSON 字符串可以包含任意字符，因此字符串被 `quoted` 以避免与分隔符产生歧义。但引号本身也是分隔符，因此需要 `escape sequences` 来编码引号。

这就是为什么你需要一个 JSON 库来生成 JSON，而不是将字符串拼接在一起。HTTP 的定义没有 JSON 那么完善且更复杂，所以请注意规范。

[[7]https://en.wikipedia.org/wiki/HTTP_response_splitting](https://en.wikipedia.org/wiki/HTTP_response_splitting)

[报告错误 | 提问](https://forms.gle/UKo4bncUnuMGBrTM7) @ [build-your-own.org](https://build-your-own.org)

---

## 二进制协议中的长度前缀数据

文本中的分隔符用于分离元素。在二进制协议和格式中，更好且更简单的替代方案是使用 `length-prefixed`（长度前缀）数据，即在元素之前指定元素的长度。一些示例包括：

- 分块编码（chunked encoding）。尽管长度仍然被分隔。
- HTTP/2 帧格式。没有任何分隔符。
- [MessagePack[8]](https://github.com/msgpack/blob/master.md) 格式。
- [JSON[8]](https://github.com/msgpack/blob/master.md) 序列化。

[报告错误 | 提问](https://forms.gle/UKo4bncUnuMGBrTM7) @ [build-your-own.org](https://build-your-own.org)

---

# 07. 代码 HTTP 服务器

**第 07 章：编码**

代码被分为较小的步骤。我们的第一步是定义 HTTP 消息的结构。

### 步骤 1：类型与结构

```typescript
type HTTPReq = {
  method: string;
  uri: string;
  version: string;
  headers: Buffer[];
};

type HTTPRes = {
  code: number;
  headers: Buffer[];
  body: BodyReader;
};
```

我们使用 `HTTPReq` 表示请求，使用 `HTTPRes` 表示响应。`BodyReader` 是用于读写数据的接口。

### 步骤 2：循环

我们的服务器遵循 `serveClient(conn)` 模式。

```typescript
async function serveClient(conn: TCPConn): Promise<void> {
  const buf: Buffer = Buffer.alloc(0);
  while (true) {
    // 尝试获取 HTTP 头部
    const msg: null | HTTPReq = cutMessage(buf);
    if (!msg) {
      // 需要更多数据
      const data = await soRead(conn);
      bufPush(buf, data);

      if (data.length === 0 && buf.length === 0) {
        return; // 无请求
      }
      if (data.length === 0) {
        throw new HTTPError(400, 'Unexpected EOF.');
      }
      // 获得了一些数据，再次尝试。
      continue;
    }

    // 处理消息并发送响应
    const reqBody: BodyReader = readerFrom(conn, msg);
    const res: HTTPRes = await handleReq(msg, reqBody);
    await writeHTTPResp(conn, res);

    // 对于 HTTP/1.0 关闭连接
    if (msg.version === '1.0') {
      return;
    }
    // 确保请求正文被消费
    while ((await reqBody.read()).length > 0) { /* 空 */ }
  }
}
```

`HTTPError` 是我们自定义异常类型。它用于生成错误响应并关闭连接。注意，这个东西仅仅是为了通过延迟处理错误情况来使我们的代码更简单。在生产代码中你可能不想这样抛出异常。

```typescript
async function newConn(socket: net.Socket): Promise<void> {
  const conn: TCPConn = soInit(socket);
  try {
    await serveClient(conn);
  } catch (exc) {
    console.error('exception:', exc);
    if (exc instanceof HTTPError) {
      // 意在发送错误响应
      const resp: HTTPRes = {
        code: exc.code,
        headers: [],
        body: readerFromMemory(Buffer.from(exc.message + '\n')),
      };
      try {
        await writeHTTPResp(conn, resp);
      } catch (exc) { /* 忽略 */ }
    }
  } finally {
    socket.destroy();
  }
}
```

### 步骤 3：分割头部

HTTP 头部以 `\r\n\r\n` 结束，这就是我们确定其长度的方式。

在理论上，header 的大小没有限制，但在实践中是有限制的。因为我们需要在内存中解析并存储 header，而内存是有限的。

```javascript
// 一个 HTTP header 的最大长度
const kMaxHeaderLen = 1024 * 8;

// 如果可能，从 buffer 头部解析并移除一个 header
function cutMessage(buf: DynBuf): null | HTTPReq {
  // header 的结束由 '\r\n\r\n' 标记
  const idx = buf.data.subarray(0, buf.length).indexOf('\r\n\r\n');
  if (idx < 0) {
    if (buf.length >= kMaxHeaderLen) {
      throw new HTTPError(413, 'header is too large');
    }
    return null;
    // 需要更多数据
  }
  // 解析并移除 header
  const msg = parseHTTPReq(buf.data.subarray(0, idx + 4));
  bufPop(buf, idx + 4);
  return msg;
}
```

当我们拥有完整的数据时，解析也会变得更容易。这就是为什么我们在解析任何内容之前要等待完整的 HTTP header 的另一个原因。

### 步骤 4：解析 Header

为了解析 HTTP header，由于我们在 buffer 中有了完整的 header，我们可以首先通过 CRLF 将数据分割若干行。然后我们可以逐个处理每一行。

```javascript
// 解析 HTTP 请求头
function parseHTTPReq(data: Buffer): HTTPReq {
  // 将数据拆分为行
  const lines: Buffer[] = splitLines(data);
  // 第一行是 `METHOD URI VERSION`
  const [method, uri, version] = parseRequestLine(lines[0]);
  // 随后是格式为 `Name: value` 的 header 字段
  const headers: Buffer[] = [];
  for (let i = 1; i < lines.length - 1; i++) {
    const h = Buffer.from(lines[i]);
    // 拷贝
    if (!validateHeader(h)) {
      throw new HTTPError(400, 'bad field');
    }
    headers.push(h);
  }
  // header 以空行结束
  console.assert(lines[lines.length - 1].length === 0);
  return {
    method: method,
    uri: uri,
    version: version,
    headers: headers,
  };
}
```

第一行简单来说是三个用空格分隔的片段。剩下的行是 header 字段。

虽然我们在这里没有尝试解析 header 字段，但对它们进行一些验证仍然是一个好主意。

`splitLines()`、`parseRequestLine()` 和 `validateHeader()` 函数并不有趣，所以我们在这里不会展示它们。你可以根据 RFC 轻松地编写它们。

### 步骤 5：读取 Body

在处理请求之前，我们必须首先构造 `BodyReader` 对象，并将将其传递给处理函数。正如我们之前提到的，读取负载 body 有 3 种方法。

```javascript
// 来自 HTTP 请求的 BodyReader
function readerFromReq(conn: TCPConn, buf: DynBuf, req: HTTPReq): BodyReader {
  let bodyLen = -1;
  const contentLen = fieldGet(req.headers, 'Content-Length');
  if (contentLen) {
    bodyLen = parseDec(contentLen.toString('latin1'));
    if (isNaN(bodyLen)) {
      throw new HTTPError(400, 'bad Content-Length.');
    }
  }
  const bodyAllowed = !(req.method === 'GET' || req.method === 'HEAD');
  const chunked = fieldGet(req.headers, 'Transfer-Encoding')?.equals(Buffer.from('chunked')) || false;
  if (!bodyAllowed && (bodyLen < 0 || chunked)) {
    throw new Error('body not allowed.');
  }
  if (!bodyAllowed) {
    bodyLen = 0;
  }
  if (bodyLen >= 0) {
    // Content-Length 存在
    return readerFromLength(conn, buf);
  } else if (chunked) {
    // chunked 编码
    throw new Error('TODO');
  } else {
    // 剩余部分
    throw new Error('TODO');
  }
}
```

*(注：由于提供的原文中代码块部分存在一些逻辑错乱或重复，翻译时已根据语意尽可能还原了注释，并保持了代码结构)*

### 步骤 6：请求处理

现在我们可以根据 URI 处理请求。这里我们将展示示例响应。



# 07. 代码实现一个基础的 HTTP 服务器

```javascript
// 一个请求处理器
async handleReq(req: HTTPReq, body: BodyReader): Promise<HTTPRes> {
  // 根据请求
  let resp: BodyReader;
  switch (req.uri.toString('latin1')) {
    case '/echo':
      // echo 服务
      resp = body;
      break;
    default:
      resp = readerFromMemory(Buffer.from('hello world\n'));
      break;
  }
  return {
    code: 200,
    headers: [Buffer.from('Server: my_server')],
    body: resp,
  };
}
```

如果 URI 是 `/echo`，我们只需将响应设置为请求负载。这本质上创建了一个 HTTP 服务器。你可以通过 `curl` 命令发送数据来测试它：

`curl -s --data-binary 'hello' http://127.0.0.1:1234/echo`

另一个示例响应是固定字符串 `hello world\n`。为了实现这一点，我们必须首先构造 `BodyReader` 对象。

```javascript
// 来自内存数据的 BodyReader
function readerFromMemory(data: Buffer): BodyReader {
  let done = false;
  return {
    length: data.length,
    read: async (): Promise<Buffer> => {
      if (done) {
        return Buffer.from(''); // 没有更多数据
      } else {
        done = true;
        return data;
      }
    },
  };
}
```

## 步骤 7：发送响应

处理请求后，我们可以发送响应头和响应体（如果有的话）。在本章中，我们将处理已知长度的负载体；分块编码留给后面的章节。我们只需要添加 `Content-Length` 字段。

```javascript
// 通过 socket 发送 HTTP 响应
async writeHTTPResp(conn: TCPConn, resp: HTTPRes): Promise<void> {
  if (resp.body.length < 0) {
    throw new Error('TODO: chunked encoding');
  }
  // 设置 "Content-Length" 字段
  console.assert(!fieldGet(resp.headers, 'Content-Length'));
  resp.headers.push(Buffer.from(`Content-Length: ${resp.body.length}`));
  // 写入头
}
```

```javascript
await soWrite(conn, encodeHTTPResp(resp));

// 写入正体 (body)

while (true) {
  const data = await resp.body.read();
  if (data.length === 0) {
    break;
  }
  await soWrite(conn, data);
}
}
```

`encodeHTTPResp()` 函数将响应头编码为字节缓冲区。其消息格式与请求消息几乎相同，除了第一行外。

`status-line = HTTP-version SP status-code SP [ reason-phrase ]`

编码比解析要容易得多，因此实现部分留给读者自行。

[报告错误 | 提问](https://forms.gle/UKo4bncUnuMGBrTM7) @ [build-your-own.org](https://build-your-own.org)

---

## 步骤 8：审查服务器循环

在发送响应后仍有一些工作需要完成。我们可以通过立即关闭连接为 HTTP/1.0 客户端提供一些兼容性，因为连接反正无法重用。

最重要的是，在继续循环处理下一个请求之前，我们必须确保请求体已完全完全消费，因为处理函数可能忽略了请求体，并让解析器留在了错误的位置。

```typescript
async function serveClient(conn: TCPConn): Promise<void> {
  const buf: DynBuf = {data: Buffer.alloc(0), length: 0};
  while (true) {
    // 尝试从缓冲区中获取 1 个请求头
    const msg: null|HTTPReq = cutMessage(buf);
    if (!msg) {
      // 省略 ...
      continue;
    }
    // 处理消息并发送响应
    const reqBody: BodyReader = readerFromReq(conn, buf, msg);
    const res: HTTPRes = await handleReq(msg, reqBody);
    await writeHTTPResp(conn, res);
    // 为 HTTP/1.0 关闭连接
    if (msg.version === '1.0') {
      return;
    }
    // 确保请求体被完全消费
    while ((await reqBody.read()).length > 0) { /* 空 */ }
  } // IO 循环
}
```

我们的第一个 HTTP 服务器现在已经完成了。

## 7.2 测试

简单的测试用例是使用 `curl` 发起请求。服务器应该用“hello world”问候你。你也可以向 `/echo` 路径 POST 数据，服务器会将数据回显给你。

[报告错误 | 提问](https://forms.gle/UKo4bncUnuMGBrTM7) @ [build-your-own.org](https://build-your-own.org)

---

```bash
curl -s --data-binary 'hello' http://127.0.0.1:1234/echo
```

### 大 HTTP 体

`curl` 命令也可以从文件发送数据。我们可以发送一个非常大的文件来验证我们的服务器是否只使用了常量内存而没有触发 OOM（内存溢出）。

```bash
curl -s --data-binary @a_big_file http://127.0.0.1:1234/echo | sha1sum
```

### 连接复用与管道化 (Pipelining)

另一个重要的测试点是处理单个连接多个请求的能力。你可以通过 `socat` 进行交互式测试，也可以通过 shell 脚本自动测试。

```bash
(cat req1.txt; sleep 1; cat req2.txt) | socat tcp:127.0.0.1:1234,crnl -
```

注意 `socat` 命令中的 `crnl` 选项，这是为了确保行以 CRLF 而非 LF 结尾。如果你删除了上述脚本中的 `sleep 1`，你也将是在测试管道请求。

## 7.3 讨论：纳格算法 (Nagle's Algorithm)

### 优化：合并小写入

在发送响应时，我们使用 `encodeHTTPResp()` 函数在将响应写入 socket 之前创建一个头的字节缓冲区。有些人可能会跳过这一步，逐行写入 socket。

```javascript
// 错误示例！
await soWrite(conn, Buffer.from(`HTTP/1.1 ${msg.code} ${status}\r\n`)); for (const h of msg.headers) {
  await soWrite(conn, h);
  await soWrite(conn, Buffer.from('\r\n'));
}
await soWrite(conn, Buffer.from('\r\n'));
```

这样做的问题在于它产生了许多小写入，导致 `TCP` 发送许多小包。不仅每个包都有相对较大的空间开销，处理更多数据包还需要更多的计算。人们看到了这个优化机会并在 TCP 栈中添加了名为“纳格算法”的特性——TCP 栈*延迟*传输以允许发送缓冲区累积数据，从而将多个连续的小写入合并起来。

### 过早优化

然而，这并不是一种好的优化。许多较新的网络协议设计（如 `TLS`）已经投入了大量精力减少 RTT（往返时间），因为许多性能问题都是延迟问题。现在在 `TCP` 中添加延迟来合并写入看起来更像是反向优化。

而且预期的优化可以在应用程序级别实现。编写良好的应用程序应该自己管理缓冲区。

### 人们在实践中是如何做的

在开发网络应用时：

1. 通过合并数据来避免小写入。

2. 禁用纳格算法。这通常是默认开启的。在 `Node.js` 中可以禁用：

```javascript
const server = net.createServer({
  noDelay: true
});
```

## 7.4 讨论：缓冲写入器 (Buffered Writer)

### 替代方案：让缓冲半透明

与其像处理响应那样显式地将数据序列化到缓冲区，我们也可以为 `TCPConn` 添加缓冲区并改变它的工作方式。

[报告错误 | 提问](https://forms.gle/UKo4bncUnuMGBrTM7) @ [build-your-own.org](https://build-your-own.org)

---

```typescript
// 将数据追加到内部缓冲区
function soWrite(conn: TCPConn, data: Buffer): Promise<void>;

// 将缓冲区刷新到运行时
function soFlush(conn: TCPConn): Promise<void>;
```

在新方案中，`soWrite()` 变为将数据追加到内部缓冲区，并使用新的 `soFlush()` 函数来实际写入数据。缓冲区大小是限制的，当缓冲区满时 `soWrite()` 也可以刷新缓冲区。

这种 IO 风格非常流行，你可能在其他编程语言中见过它。例如，`C` 语言中的 `stdio` 有一个默认开启的内置缓冲区，你必须在适当的情况下 `fflush()`。

### 替代方案：添加缓冲包装器

或者，你可以保持 `TCPConn` 不变，并添加一个独立的包装器：

```typescript
type BufferedWriter = {
  write: (data: Buffer) => Promise<void>,
  flush: () => Promise<void>,
  // ...
};

function createBufferedWriter(conn: TCPConn): BufferedWriter;
```

这类似于 Go 语言中的 `bufio.Writer`。这种方案比在 socket 代码中添加缓冲更灵活，因为缓冲包装器也适用于其他形式的 IO。Go 标准库的设计具有定义良好的接口 [`io.Writer`](https://pkg.go.dev/io#Writer)，使得缓冲写入器可以无缝替换非缓冲写入器。

从历史上看，万维网（WWW）主要由带有超链接的静态网页组成，`HTTP` 最初也是为此设计的。随后出现了提供动态内容的 Web 应用，这正是本章将考虑的内容。

# 08. 动态内容与流式传输

## 8.1 分块传输编码 (Chunked Transfer Encoding)

为了提供动态内容，我们需要实现上一章中缺失的分块编码。因为当我们即时生成网页时，无法预先知道输出的长度。

### 分块消息格式

让我们从规范 `RFC 9112` 开始看。

```
chunked-body
= *chunk
last-chunk
trailer-section
CRLF
chunk
= chunk-size [ chunk-ext ] CRLF
chunk-data CRLF
chunk-size
= 1*HEXDIG
last-chunk
= 1*("0") [ chunk-ext ] CRLF
chunk-data
= 1*OCTET ; a sequence of chunk-size octets
```

添加一个示例作为参考：

```
4\r\nHTTP\r\n5\r\nserver\r\n0\r\n\r\n
```

通过这个示例可以看出，格式非常直观。

- 每个分块以一个十六进制数字开头并以 `CRLF` 结束；这是分块数据的长度。
- 随后的分块数据也以 `CRLF` 结束；这个 `CRLF` 除了让协议具有人类可读性外没有作用。
- 零长度的分块标记着 `HTTP` 体的结束。我们经常看到这种约定！

### 冷门的 HTTP 特性

在 BNF 规范中仍有一些未触及的结构——`chunk-size` 行上可选的 `chunk-ext` 以及末尾的 `trailer-section`。这些是设计进规范的某些冷门特性，但在实践中并不常用。

`chunk-ext` 设计用于通过添加额外的键值对来扩展分块格式，但在实践中并没有这种扩展。

`trailer-section` 设计用于在 `HTTP` 体之后放置一些头部字段。你可能会奇怪为什么有人这样做，这是为了某些罕见的用例。有些人喜欢在 `HTTP` 头部字段中放置特定于应用程序的内容，例如数据的校验和。问题是，在流式传输数据时，校验和只有在数据传输完成后才能已知，因此设计了一种机制在最后一个分块之后附加一些头部字段。

许多 `HTTP` 服务器或客户端实现简单忽略了这些冷门特性，因为它们几乎没有用途或价值。另一方面，设计你的应用程序去使用任何冷门特性是不明智的，即使它们有 `RFC` 支持，因为你更有可能在客户端和中间件上遇到问题。我们在实现中也将忽略这些。

## 8.2 生成分块响应

第一步是在 `writeHTTPResp()` 函数中添加分块编码，该函数从 `BodyReader` 接口中提取响应体。

```typescript
// 一个用于从/向 HTTP 体读取/写入数据的接口。
type BodyReader = {
  // "Content-Length"，如果未知则为 -1。
  length: number,
  // 读取数据。EOF 后返回一个空缓冲区。
  read: () => Promise<Buffer>,
};
```

上一章的接口设计时已经考虑了分块编码。我们需要实现的是长度为 `-1`（未知）的情况。

```typescript
// 通过套接字发送 HTTP 响应
async function writeHTTPResp(conn: TCPConn, resp: HTTPRes): Promise<void> {
  // 设置 "Content-Length" 或 "Transfer-Encoding" 字段
  if (resp.body.length < 0) {
    resp.headers.push(Buffer.from('Transfer-Encoding: chunked'));
  } else {
    resp.headers.push(Buffer.from(`Content-Length: ${resp.body.length}`));
  }
  // 写入头部
  await soWrite(conn, encodeHTTPResp(resp));

  // 写入体
  const crlf = Buffer.from('\r\n');
  for (let last = false; !last; ) {
    let data = await resp.body.read();
    last = (data.length === 0); // 结束了？
    if (resp.body.length < 0) { // 分块编码
      data = Buffer.concat([
        Buffer.from(data.length.toString(16)), crlf,
        data, crlf,
      ]);
    }
    if (data.length) {
      await soWrite(conn, data);
    }
  }
}
```

注意，分块消息是在我们通过单个写入发送到套接字之前，使用 `Buffer.concat()` 创建的。这遵循了上一章关于缓冲 I/O 的建议。

## 8.3 JS 生成器

下一步是将生成响应体的应用程序代码（生产者）连接到 `BodyReader` 接口（队列），而 `writeHTTPResp()` 函数（消费者）从中从中提取数据。

```typescript
// 伪代码！
async function produce_response() {
  // ...
  await output(data1);
  // 从 BodyReader 读取
  // ...
  await output(data2);
  // 从 BodyReader 读取
  // ...
}
```

### 生产者、消费者与队列

使用队列并非易事，因为我们将会对此进行探讨。

### 作为生产者的 JS 生成器



# JavaScript 生成器非常适合生产者-消费者模型

下面是一个生成器示例。

```typescript
type BufferGenerator = AsyncGenerator<Buffer, void, void>;

// 函数后的星号是 JS 生成器的语法
async function *countSheep(): BufferGenerator {
  for (let i = 0; i < 100; i++) {
    // 等待 1s，然后输出计数器
    await new Promise((resolve) => setTimeout(resolve, 1000));
    yield Buffer.from(`${i}\n`);
  }
}
```

## 从 JS 生成器读取

为响应生成器添加一个新的 URI 处理器。`readerFromGenerator()` 函数将 JS 生成器转换为 `BodyReader`。

```typescript
function readerFromGenerator(gen: BufferGenerator): BodyReader {
  return {
    length: -1,
    read: async (): Promise<Buffer> => {
      const r = await gen.next();
      if (r.done) {
        return Buffer.from(''); // EOF
      } else {
        console.assert(r.value.length > 0);
        return r.value;
      }
    },
  };
}
```

要从生成器提取数据，使用 `next()` 方法。当生成器 yield 或 return 时，`next()` 方法返回，通过 `done` 标志进行区分，数据可以从 `value` 成员获取。

```typescript
case '/sheep':
  resp = readerFromGenerator(countSheep());
  break;
```

`next()` 方法可以接受一个可选参数，该参数将作为 `yield` 语句的结果传递给生产者，这意味着 JS 生成器是双向的。虽然我们现在不需要这种功能。

使用 `curl` 测试 `/sheep` URI，你应该能看到每 1s 输出一次计数器，这意味着分块编码正在正常工作。使用分块编码时，总体长度没有限制，你甚至可以生成无限字节流。

## 8.4 读取分块请求

分块编码主要用于响应而不是请求。网络浏览器总是知道上传的长度，除非客户端 JS 使用了实验性的 Streams API。

使用 `ReadableStream` 来发送请求。为了支持此类客户端，让我们添加代码来读取分块（chunked）请求。

[1](https://developer.mozilla.org/en-US/docs/Web/API/ReadableStream)

[2](https://developer.mozilla.org/en-US/docs/Web/API/fetch#body)

[报告错误 | 提问](https://forms.gle/UKo4bncUnuMGBrTM7) @ [build-your-own.org](https://build-your-own.org)

2024-02-02

## 08. 动态内容与流传输

### 分块解析器作为生产者

解码分块请求的代码必须连接到 `BodyReader` 接口。

与我们之前将响应生成器连接到 `BodyReader` 接口的任务是完全相同的。我们将再次使用 JS 生成器（generator）。

```javascript
// 解码分块编码并即时产生数据
async function* readChunks(conn: TCPConn, buf: DynBuf): BufferGenerator;
```

`readChunks()` 生成器的行为应该像我们之前编写的示例响应生成器。因此，我们可以直接使用 `readerFromGenerator()` 将其转换为 `BodyReader`。

```javascript
// 来自 HTTP 请求的 BodyReader
function readerFromReq(
  conn: TCPConn, buf: DynBuf, req: HTTPReq): BodyReader
{
  // 省略 ...
  if (bodyLen >= 0) {
    // 存在 "Content-Length"
    return readerFromConnLength(conn, buf, bodyLen);
  } else if (chunked) {
    // 分块编码
    return readerFromGenerator(readChunks(conn, buf));
  } else {
    // 读取连接的剩余部分
    return readerFromConnEOF(conn, buf);
  }
}
```

`readerFromConnEOF()` 函数用于兼容 HTTP/1.0 客户端。我们将跳过代码列表。

### 解码块格式

`readChunks()` 的实现：

```javascript
// 解码分块编码并即时产生数据
async function* readChunks(conn: TCPConn, buf: DynBuf): BufferGenerator {
  for (let last = false; !last; ) {
    // 读取分块大小行
    const idx = buf.data.subarray(0, buf.length).indexOf('\r\n');
    if (idx < 0) {
      // 需要更多数据，省略 ...
      continue;
    }
    // 解析分块大小并移除该行
    let remain = /\* omitted ... */;
    bufPop(buf, /\* omitted ... */);
    // 是最后一个吗？
    last = (remain === 0);
    // 读取并产生分块数据
    while (remain > 0) {
      if (buf.length === 0) {
        await bufExpectMore(conn, buf, 'chunk data');
      }
      const consume = Math.min(remain, buf.length);
      const data = Buffer.from(buf.data.subarray(0, consume));
      bufPop(buf, consume);
      remain -= consume;
      yield data;
    }
    // 分块数据后跟着 CRLF
    bufPop(buf, 2); // 每个分块
  }
}
```

这与 HTTP 本身的头部-体结构相似。你等待分块大小并确定主体的长度。头部是变长度的，因此在解析时我们需要限制其大小，就像我们处理 HTTP 头部时一样。

### 分块编码产生字节流

解码格式是简单的。你需要注意的是读取块数据的内部循环。代码并没有等待整个分块到达，而是只要数据到达就产生数据。如果我们等待整个分块，就必须将整个块存储在内存中并受到限制。

2024-02-02

08. 动态内容与流传输

分块请求可以使用 `curl http://127.0.0.1:1234` 进行测试。`curl` 将在不知道请求长度的情况下读取数据。

## 8.5 讨论：使用数据包捕获调试

一直在编写复杂的代码。了解如何调试代码是非常重要的。添加 `print` 语句是检查情况的一种快速方法，但对于网络应用程序，有更廉价的方法：数据包捕获工具如 `tcpdump`、`grep` 和 `wireshark`。

### 使用 `tcpdump` 捕获并检查数据

示例：`tcpdump -X -i lo port 1234`

- `-X` 标志让 `tcpdump` 进行十六进制转储。
- `-i lo` 标志限制网络接口。我们只关心到 `127.0.0.1:1234` 的连接。
- `port 1234` 是过滤无关数据包的布尔表达式。

`tcpdump` 的示例输出：

```
12:00:00.222444 IP 127.0.0.1.1234 > 127.0.0.1.59872:
0000: 4500 0079 c492 4000 4006 77ea 7f00 0001 E..y...@w.....
0010: 7f00 0001 04d2 e9e0 42d3 38e1 bb89 becb........B.8.....
0020: 8018 0200 fe6d 0000 0101 080a 8f86 a39c.....m..........
0030: 8f86 a395 4854 5450 2f31 2e31 2032 3030....HTTP/1.1.200
0040: 204f 4b0d 0a53 6572 7665 723a 206d 795f.OK..Server:.my_
0050: 6669 7273 745f 6874 7470 5f73 6572 7665first_http_serve
0060: 720d 0a43 6f6e 7465 6e74 2d4c 656e 6774r..Content-Lengt
0070: 683a 2031 330d 0a0d 0a h:.13....
12:00:00.222666 IP 127.0.0.1.59872 > 127.0.0.1.1234:
...
12:00:00.333444 IP 127.0.0.1.1234 > 127.0.0.1.59872:
0000: 4500 0041 c493 4000 4006 7821 7f00 0001 E..A..@.@.x.
```

2024-02-02

08. 动态内容与流传输

### 使用 `ngrep` 搜索数据包数据

对于 HTTP 这样的文本协议，十六进制转储可能大过其实。你可以使用 `ngrep` 将数据打印为文本。

`ngrep -qt -i lo '' port 1234`

- `-d lo` 用于网络接口。
- 空字符串 `''` 是过滤所有数据包的正则表达式。
- `port 1234` 类似于 `tcpdump` 使用的布尔表达式。

值得注意的是，所有这些工具都可以将数据包写入交换格式（pcap）的文件。你可以先捕获数据包，稍后分析。

[报告错误 | 提问](https://forms.gle/UKo4bncUnuMGBrTM7) @ [build-your-own.org](https://build-your-own.org)

### 使用 Wireshark 分析数据包

你也可以使用 `-w` 标志将捕获的数据包保存到文件中，而不是打印它们。文件格式可以被所有数据包分析软件（包括 `tcpdump` 本身）读取。

如果你更喜欢图形界面，可以使用 Wireshark 打开捕获的文件，它除了显示十六进制转储外，还可以解析协议，显示每个元素和结构。

- 使用布尔表达式过滤数据包。这会立即生效，因此你可以通过尝试错误来操作。
- 高亮单个连接。
- 使用真实数据学习新协议。
- 查看你自己的实现中哪些问题。

## 8.6 讨论：WebSocket

### 轮询更新

某些 Web 应用需要从服务器接收实时更新。实现此功能最原始的方法是通过轮询。客户端 JS 定期发起 AJAX 请求以检查更新。这浪费了资源，且无法用于低延迟场景。

轮询的实现可以不那么简单：服务器可以保持连接，仅在有新更新时才发送响应。如果我们进一步考虑，分块编码（chunked encoding）允许在单个响应中包含无限次更新。这被称为长轮询（long polling）。

例如，服务器可以生成由换行符分隔的 JSON 消息流，并通过分块编码交付。客户端只需发送单个请求，客户端就可以读取这些消息，而不会引入轮询带来的额外延迟。

```
client
server
------
------
|header| ==>
<== |header|
...
<== |JSON\n|
<== |JSON\n|
<== |JSON\n|
...
```

然而，这种用例已经被 `WebSocket` 淘汰了——这是一种 HTTP 协议的扩展。

### WebSocket 是基于消息的

`WebSocket` 的设计背后有多个动机。其中之一是面向消息（`message-oriented`）的设计，而不是字节流。`每行一个 JSON` 的例子听起来足够简单，但你仍然需要将字节流拆分成行。编写网络应用代码时的首大错误就是没有理解字节流。`WebSocket` 自带了内置帧格式，输出的是消息而不是字节，这让程序员避免了重复低级错误。

### WebSocket 不是请求-响应

`WebSocket` 的另一个贡献是双向和全双工（`full-duplex`）通信，这意味着客户端和服务器可以同时互相发送消息。技术上，你可以通过两个 HTTP 连接（一个用于推送，一个用于拉取）模拟双向消息而不使用 `WebSocket`。但 `WebSocket` 可以让客户端和服务器的操作都变得更简单。

### 08. 动态内容与流

```
client
server
------
------
|header| ==>
<== |header|
... ...
|message| ==>
|message| ==> <== |message|
|message| ==>
<== |message|
|message| ==>
... ...
```

我们将在稍后的章节中实现 `WebSocket`，在此之前，我们已经先探索 HTTP 的其他重要用途。

# 第 09 章：文件 IO 与资源管理

提供静态文件是 HTTP 设计的用途之一。还有几个主题需要探索：

1. `范围请求`（Ranged requests）。获取文件的部分内容。这允许传输被中断并在稍后恢复。
2. `缓存`（Caching）。减少不必要的传输。
3. `压缩`（Compression）。减少传输时间和开销。

我们将从实现一个基础文件服务器开始，这将使我们熟悉 `File API`。

## 9.1 Node.JS 中的文件 IO

如前所述，`Node.JS` 中的 `file API` 有 3 种类：

- 同步 API，我们无法使用。
- 基于回调的 API，我们不想使用。
- 基于 promise 的（`promise-based`）API，我们将使用它。

```typescript
import * as fs from "fs/promises";
```

我们将使用 4 种文件操作：

1. 打开文件。
2. `stat` 文件以获取如大小之类的元数据。
3. 读取文件数据。
4. 关闭文件。

像套字一样，磁盘文件由封装在 JS 对象中的不透明句柄（handles）表示。这里是我们使用的简化 TypeScript API 定义。

```typescript
function open(path: string, flags?: string): Promise<FileHandle>;
interface FileReadResult {
  bytesRead: number;
  buffer: Buffer;
}

interface FileReadOptions {
  buffer?: Buffer;
  offset?: number | null;
  length?: number | null;
  position?: number | null;
}

interface Stats {
  isFile(): boolean;
  isDirectory(): boolean;
  // ...
  size: number;
  // ...
}

interface FileHandle {
  read(options?: FileReadOptions): Promise<FileReadResult>;
  close(): Promise<void>;
  stat(): Promise<Stats>;
}
```

## 9.2 提供磁盘文件

### 步骤 0：为静态文件添加处理器

我们的第一步是编写提供磁盘文件的代码。我们将添加一个处理器来从当前工作目录提供文件。

```javascript
const uri = req.uri.toString('utf8');

if (uri.startsWith('/files/')) {
  // 从当前工作目录提供文件
  // FIXME: 防止通过 `..` 逃逸
  return await serveStaticFile(uri.substr('/files/'.length));
}
```

对于生产级 Web 服务器，还需要额外的工作来确保 URI 路径确实位于目标目录内（URI 规范化），并且文件是可访问的。我们将跳过这些工作。

### 步骤 1：打开并关闭文件

`r` 标志用于以只读模式打开文件。如果文件不存在或无法访问，`fs.open()` 将抛出异常。



# 09. 文件 IO 与 资源管理

```javascript
async function serveStaticFile(path: string): Promise<HTTPRes> {
  let fp: null | FileHandle = null;
  try {
    // 打开文件
    fp = await fs.open(path, 'r');
  } catch (exc) {
    // 无法打开文件
    console.info('error serving file:', exc);
    return resp404();
  } finally {
    // 确保文件被关闭
    await fp?.close();
  }
}
```

## 步骤 2：stat() 文件

`stat()` 方法用于从文件中检索元数据。它包含了文件类型（普通文件、目录）、大小和其他信息。

```javascript
// 打开文件
fp = await fs.open(path, 'r');
// 获取大小
const stat = await fp.stat();
if (!stat.isFile()) {
  return resp404();
}
const size = stat.size;
```

还有一个 `fs.stat(path)` 函数，它接受路径而不是句柄。它可以在不打开文件的情况下进行 stat。然而，在句柄上使用 `stat` 更好。因为路径可能会指向不同的文件，这属于`竞态条件`[^1]。先打开文件可以确保你操作的是同一个文件。

## 步骤 3：构建 BodyReader

`readerStaticFile()` 函数从文件句柄返回一个 `BodyReader`。在我们之前将 `fp` 设置为 `null` 是重要的，因为 `BodyReader` 稍后会读取文件，`finally` 块在此之后无法再关闭文件。

```javascript
async function serveStaticFile(path: string): Promise<HTTPRes> {
  let fp: null | FileHandle = null;
  try {
    // 打开文件
    fp = await fs.open(path, 'r');
    // ...
    // body 读取器
    const reader: BodyReader = readerStaticFile(fp, size);
    fp = null;
    // 现在由读取器负责关闭它
    return { code: 200, headers: [], body: reader };
  } catch (exc) {
    // ...
  } finally {
    // 确保文件被关闭
    await fp?.close();
  }
}
```

## 第 4 步：确保文件已关闭

如果处理函数成功返回了 `BodyReader`，文件仍然处于打开状态，后续必须关闭。我们将在 `BodyReader` 接口中添加一个 `close()` 函数来执行清理工作。

```typescript
// 用于从向 HTTP body 读写数据的接口
type BodyReader = {
  // "Content-Length"，未知则为 -1。
  length: number,
  // 读取数据。EOF 后返回一个空缓冲区。
  read: () => Promise<Buffer>,
  // 可选清理函数
  close?: () => Promise<void>,
};
```

`close()` 成员被设置为可选，因此我们只需要修改 `readerFromStaticFile()` 函数。

```typescript
function readerFromStaticFile(fp: fs.FileHandle, size: number): BodyReader {
  return {
    // ...
    close: async () => await fp.close(),
  };
}
```

处理函数调用之后的代码被封装在 `try-finally` 块中，以确保清理函数被调用。

```typescript
const res: HTTPRes = await handleReq(msg, reqBody);
try {
  await writeHTTPResp(conn, res);
} finally {
  await res.body.close?.();
  // 清理
}
```

这就是最基础的文件服务器。现在是时候停止并测试了。

## 9.3 讨论：手动资源管理

JS 是一种带垃圾回收（GC）的语言，它让你免于手动分配和释放内存这种低效且易出错的工作。然而，仍然有一些*非内存*资源必须手动管理，例如必须关闭的文件和套接字。如果你没有手动内存管理的经验，可能不知道通用如何管理非内存资源。

### 由某些实体拥有的资源

资源的“所有权”（ownership）是手动资源管理中最重要的概念。也就是说，谁负责终止和清理该资源。资源的所有者可以是：

- 函数：在退出前终止资源。
- 代码作用域：在退出前终止资源。
- 对象：在自身被终止时终止资源。

所有权可以是静态的或动态的。动态意味着所有者随时间变化。无论你做什么，资源始终只有一个所有者。

### 由函数或作用域拥有的资源

在 `serveStaticFile()` 函数中，打开的文件最初由函数拥有，因此函数必须关闭它。整个函数被封装在 `try-finally` 块中，清理代码放在函数的末尾。其他语言有类似的函数级清理构造结构：

- 在 Golang 中，你可以使用 `defer`。
- 在 C 中，通常做法是将清理代码放在函数末尾而不是直接返回。
- 在 C++ 中，你可以使用析构函数，特别是在使用异常时。
- 在 Python 中，除了 `try-finally` 块，你还有 `with` 语句。

除了 Go 之外，所有这些机制都提供了函数级清理。

### 所有权可以转移

在 `serveStaticFile()` 函数中，当 `BodyReader` 返回时，文件被置为 `null`。这确保了资源只有一个所有者。

### 所有者是链式的

当一个对象拥有资源时，它必须由另一个对象或代码作用域拥有。

这也会执行 `finally` 块。你甚至可以使用特殊类型的异常来通知生成器你打算在途中途终止它，这样生成器就可以处理这种特殊情况。

Python 生成器有[类似的方法[^3]](https://docs.python.org/3/reference/expressions.html#generator.close)。令人惊讶的是[^4]，Python 的垃圾回收器会自动为生成器执行 `finally` 块，尽管关于 GC 是否应该处理非内存业务尚存争议。

# 9.4 讨论：复用缓冲区

## 缓冲区分配是有成本的

`readerFromStaticFile()` 函数为每次读取分配并返回一个新缓冲区。这并不高效，因为缓冲区的分配是有成本的：

1. 内存分配器的成本。对于许多实现来说，这种成本在大多数情况下是 `constant` 的。在最好的情况下，分配器要么从空列表中返回对象，要么从大内存块中分配。
2. 零初始化的成本。随缓冲区大小 `linearly` 增长。

## 使用未初始化的缓冲区

由于减少了系统调用的次数，通常希望使用较大的缓冲区以获得更高的吞吐量。然而，分配过大的缓冲区具有线性的初始化成本，这可以通过在 Node.JS 中使用 `uninitialized` 缓冲区来避免。

```javascript
const buf = Buffer.allocUnsafe(65536);
```

此函数之所以为 `allocUnsafe` 是因为有错误的程序更有可能向用户泄露内部信息。未初始化数据的 bug 由于其不可预测性，也难以调试。

## 复用缓冲区

在某些语言（如 Go 或 Python）中，很难获取未初始化的缓冲区。你可以对同一个缓冲区进行多次 IO 操作。

```typescript
function readerFromStaticFile(fp: fs.FileHandle, size: number): BodyReader {
  const buf = Buffer.allocUnsafe(65536);
  // 每次读取复用
  return {
    length: size,
    read: async (): Promise<Buffer> => {
      const r = await fp.read({ buffer: buf });
      // ...
      return r.buffer.subarray(0, r.bytesRead);
    },
  };
}
```

这将分摊缓冲区分配的成本。

## 缓冲区池

与其在本地分配缓冲区，不如维护一个全局的 `used` 缓冲区池。每当你完成一个缓冲区时，就将其放入池中。当你需要缓冲区时，尝试从池中获取一个，只有当池为空时才创建一个新的。此处的优点是：

- 从池中获取内容的成本可能比内存分配器还要低。
- 不同的代码路径都能从中受益。真实的分配更少。

对象池的代码非常简单。Node.JS 的 `Buffer` 类型使用了内置池[^5]，但仅用于 `small` 缓冲区。Go 标准库也包含了对象池[^6]。

## 复用缓冲区时注意生存

缓冲区可以由生产者或消费者分配。在我们看到的所有情况下，生产者分配缓冲区并将其返回给任何使用数据的人。这可能会产生问题，因为在下次 `read()` 运行时，缓冲区可能仍被引用和使用。

```typescript
function readerFromStaticFile(fp: fs.FileHandle, size: number): BodyReader {
  const buf = Buffer.allocUnsafe(65536);
  // 每次读取复用
  return {
    length: size,
    read: async (): Promise<Buffer> => {
      const r = await fp.read({ buffer: buf });
      // 注意：缓冲区的生命周期不明确！
      return r.buffer.subarray(0, r.bytesRead);
    },
  };
}
```

让我们应用资源管理的教训：谁拥有缓冲区？对于本章的代码，我们知道生产者（`BodyReader`）返回的缓冲区被写入套接字，我们在调用下次 `read()` 之前会等待写入完成，因此生产者是引用缓冲区的唯一地方，我们可以推断消费者不需要拥有缓冲区，因此缓冲区复用是有效的。然而，对于更复杂的消费者，这可能不成立！

另一种是消费者分配缓冲区，只要数据是原地处理的，缓冲区的生命周期就是明确的，因此消费者是唯一的所有者。

```javascript
// 伪代码！
const buf = Buffer.allocUnsafe(65536);
// 每次读取复用
while (more_data()) {
  const nbytes = await read_data(buf);
  // 从生产者读取
  await process(buf.subarray(0, nbytes));
  // buf 不再使用，所以复用是安全的。
}
```

在 Golang 中，从 `io.Reader` 接口拉取数据时，缓冲区由消费者提供。这在设计上鼓励了缓冲区复用并抑制了不必要的分配。

# 第 10 章：范围请求

## 10.1 范围请求如何工作

### Range Header 字段语法

范围请求由客户端通过 `Range` 头部字段发起。例如，`Range: 0-9` 获取负载的前 10 个字节。该头部字段在 [RFC 9110](https://www.rfc-editor.org/rfc/9110) 中完整规范。

### 有效范围及示例

有效范围与实际文件范围的交集。假设我们有一个 50 字节的文件，这里是一些示例及其有效范围。

| Range: bytes=x | 有效范围 |
| :--- | :--- |
| 0-0 | [0, 1) |
| 0-1 | [0, 2) |
| 10- | [10, 50) |
| 10-60 | [10, 50) |
| -10 | [40, 50) |
| -60 | [0, 50) |
| 4-3 | invalid |
| 70-60 | invalid |
| -0 | invalid |
| --1 | invalid |
| foobar | invalid |
| 60- | out of range |
| 60-70 | out of range |

服务器还必须处理异常的情况：

- 如果交集为空，服务器返回状态码 416 (Range Not Satisfiable)。
- 如果任何一个范围无效，服务器将忽略该 Header 字段（并提供完整文件）。

## 范围请求是可选的

一旦你开始为 HTTP 服务器添加功能，你就会发现大多数 HTTP 特性都是可选的，而可选功能可能会让情况变得比看起来更复杂。

服务器可能完全不支持范围请求，即使支持，它们也不适用于所有请求。例如，对于动态生成的内容返回范围响应是没有意义的，因为内容的长度预先是不可知的，服务器无法判断请求是否超出了范围。

## 范围响应通过 206 状态码指示

客户端如何知道服务器是否支持范围请求？这就是 `206 (Partial Content)` 部分内容状态码的作用，它表示返回的是部分响应而不是完整响应（`200 OK`）。

## `Content-Range` 返回有效范围

如上例所示，有效范围可能与请求的范围不同，因此服务器需要告诉客户端返回的确切范围。这就是 `Content-Range` 头部字段的工作。它包含了响应的有效范围以及内容的总长度。

```text
Content-Range: bytes 12-34/1234
```

该头部字段也用于 `416 (Range Not Satisfiable)` 响应，告诉客户端内容的正确长度。

```text
Content-Range: bytes */1234
```

[^1]: https://en.wikipedia.org/wiki/Time-of-check_to_time-use
[^3]: https://docs.python.org/3/reference/expressions.html#generator.close
[^4]: https://docs.python.org/2.5/whatsnew/pep-342.html
[^5]: https://nodejs.org/api/buffer.html#static-method-bufferallocunsafesize
[^6]: https://pkg.go.dev/sync#Pool



## 宣告`范围支持（Range Support）`

有方法可以让客户端知道范围请求是否可用。服务器可以在非范围响应中包含 `Accept-Ranges: bytes` 头部字段，以指示该 URI 支持范围请求，这样客户端就知道如果下载被中断，可以使用范围请求恢复下载。

## 使用 `HEAD` 方法进行探测

还有一种方法可以在*不*获取响应的任何部分的情况下判断是否支持范围请求——即使用 `HEAD` HTTP 方法。

如果服务器支持 `HEAD` 方法，它的行为应该类似于 `GET`，但*不包含*响应体，只返回响应头部字段和状态码，就像请求被完整提供了一样。客户端随后可以检查 `Accept-Ranges` 或 `Content-Range`，而无需实际接收内容。

记住，HTTP 中确定有效负载长度的方法非常混乱。`HEAD` 方法为客户端增加了一个特殊情况：服务器可能会返回 `Content-Length`，但这次它不会告知有效负载长度；无论头部字段如何说明，`HEAD` 方法都没有响应体！

## 使用多部分消息（Multipart Message）多范围

虽然很少使用，但 `Range` 头部字段可以包含多个由逗号分隔的范围。

这里是一个示例。

```
GET / HTTP/1.1
Range: bytes=0-5,8-13
HTTP/1.1 206 Partial Content
Accept-Ranges: bytes
Content-Length: 227
Content-Type: multipart/byteranges; boundary=SEPARATOR1234567

--SEPARATOR1234567
Content-Type: text/html; charset=UTF-8
Content-Range: bytes 0-5/1234

<html>

--SEPARATOR1234567
Content-Type: text/html; charset=UTF-8
Content-Range: bytes 8-13/1234

<head>

--SEPARATOR1234567--
```

该响应与单范围响应完全不同：

- 没有使用 `Content-Range`。

相反，它使用了 `Content-Type: multipart/byteranges; boundary=x`。

- 响应采用新的消息格式编码：

  - 由 `Content-Type` 头部字段指示。

  - 多个部分由随机字符串分隔符分隔。

---

## 10. Range 请求 (Range Requests)

```javascript
await writeHTTPBody(conn, res.body);

} finally {

  await res.body.close?.();

  // cleanups
}
```

无论如何 `BodyReader` 都会被关闭，因为在我们的案例中 `BodyReader` 仍然拥有一个文件资源。你也可以在请求处理器中处理 `HEAD` 方法并尽早关闭文件（从根本上就不创建 `BodyReader`）。

---

# 第 11 章：HTTP 缓存

2024-02-02

在本章中，我们将探索 HTTP 缓存，它可以减少不必要的传输。

## 11.1 缓存验证器 (Cache Validator)

Web 浏览器默认会缓存响应，即使服务器没有投入太大精力。

问题是：客户端如何知道缓存项是否有效？有一种机制可以服务器查询这些信息。

### 通过时间戳验证 (Validate by Timestamp)

实现这种方法的方法是通过 `Last-Modified` 和 `If-Modified-Since` 头部字段。其步骤如下：

1. 服务器在 `Last-Modified` 头部字段中返回文件的文件系统修改时间。
2. 客户端缓存响应以及时间戳。
3. 客户端在复用缓存响应之前对其进行验证，发送将 `If-Modified-Since` 头部字段设置为缓存时间戳的请求：
   - 如果服务器上的文件已修改（由不同的时间戳指示），服务器将照常返回响应。
   - 如果服务器不支持此验证方法并忽略该字段，也照常返回。
   - 如果服务器上的时间戳相同，服务器返回状态码 `304`（未修改），此状态码没有负载，只需告诉客户端复用缓存。
4. 如果状态码为 `304`，客户端将复用缓存响应；或者使用正常响应并更新缓存。

### 通过 ETag 验证 (Validate by ETag)

时间戳的分率仅为一秒，对于某些用例是不够的，而且文件时间戳并不是识别内容的可靠方法。另一种识别内容的方法是通过 `ETag` 头部。它的工作方式与 `Last-Modified` 相同，但其值是任意的，你可以使用内容的哈希值或版本号。

`ETag` 通过 `If-None-Match` 进行验证，这类似于 `If-Modified-Since`。

### 范围请求验证 (Validate for Range Requests)

上述验证适用于客户端缓存了旧版本并期望服务器返回新版本场景。然而，范围请求的情况不同：如果内容与客户端拥有的相同，服务器只能返回部分响应。在这种情况下，客户端不能使用 `If-Modified-Since` 或 `If-None-Match`；而是使用 `If-Range` 头部，它包含 `ETag` 或时间戳。如果 `If-Range` 值*不匹配*（则导致完整响应）。

### 验证头部总结 (Summary of Validation Headers)

| 服务器到客户端 | 客户端到服务器 | 注释 |
| :--- | :--- | :--- |
| `Last-Modified` | `If-Modified-Since` | 时间戳。 |
| `ETag` | `If-None-Match` | 哈希、版本号等。 |
| `ETag/Last-Modified` | `If-Range` | 部分还是完整？ |

### 实现时间戳验证器 (Implementing the Timestamp Validator)

作为一个简单的服务器，添加 `Last-Modified` 和 `If-Modified-Since` 头部字段是轻而易举的。

```javascript
const ts = Math.floor(stat.mtime.getTime() / 1000); // 修改 ts

const headers: Buffer[] = [
  // 支持范围请求
  Buffer.from('Accept-Ranges: bytes'),
  // 用于缓存验证
  Buffer.from(`Last-Modified: ${stat.mtime.toUTCString()}`)
];

// 检查条件
const ifm = fieldGet(req.headers, 'If-Modified-Since');
if (ifm && parseHTTPDate(ifm.toString('latin1')) === ts) {
  const empty = readerFromMemory(Buffer.from(''));
  return {code: 304, headers: headers, body: empty};
}

let hrange = fieldGet(req.headers, 'Range');
const ifr = fieldGet(req.headers, 'If-Range');
if (ifr && parseHTTPDate(ifr.toString('latin1')) !== ts) {
  hrange = null;
  // 忽略 Range 字段
}
// 使用 hrange 检查请求范围 ...
```

`ETag` 可能需要一个独立的子系统来跟踪内容（无论是哈希值还是版本号），因此我们不会编写代码。

## 11.2 讨论：服务端缓存控制 (Discussion: Server-Side Cache Control)

我们已经讨论了客户端如何验证缓存，下一步是从服务器端控制缓存行为。即客户端应该保留缓存多久。

服务器使用 `Cache-Control` 头部字段建议客户端缓存。其值是逗号分隔的指令列表。例如：

`Cache-Control: no-store, no-cache, max-age=0, must-revalidate`

### 何时重新验证缓存 (When to Revalidate Cache)

`max-age=x` 指令指定缓存项存活多少秒（生存时间，或 TTL）。然而，缓存在过期时并简单地删除项。它非常复杂，复杂到有自己的文档：[RFC 9111](https://www.ietf.org/rfc/rfc9111)。

缓存项根据其是否超过了 `max-age` 被描述为*新鲜的 (fresh)* 或*过期的 (stale)*。新鲜或过期的状态决定了何时应该验证项。

| 服务器提供的 Cache-Control | 验证过期项 | TTL |
| :--- | :--- | :--- |
| `max-age=x` | 可能 (maybe) | x |
| `max-age=x, must-revalidate` | 必须 (must) | x |
| `max-age=x, immutable` | 应该 (should) | x |
| `max-age=0, must-revalidate` | (不新鲜) | 0 |
| `no-cache` | (不新鲜) | 0 |
| (不存在) | 启发式 (heuristic) | 启发式 (heuristic) |

**控制 TTL**

单凭 `max-age` 指令对缓存所示的寿命并没有提供足够的控制，因为表格使用了模糊的词汇“maybe”和“should”，它们之间有何区别？

浏览器通常会复用新鲜项，但即使缓存是新鲜的，它可能会重新验证项，这发生在用户点击刷新按钮时。

但为什么“验证过期项”是“应该”？如果设置 TTL 的效果无法保证，它的意义何在？事实上有两层保证：

1. 没有 `must-revalidate`，过期项可能仍被复用，这发生在服务器不可用时。
2. 有了 `must-revalidate`，缓存 TTL 实际上被遵守了。

不过实现实现并不区分“应该”和“必须”的情况。

**让客户端始终检查服务器 (Make the Client Always Check the Server)**

`no-cache` 指令具有误导性，它并不是“不要缓存”，它是 `max-age=0, must-revalidate` 的缩写，意味着“缓存但始终验证”。它用于需要最新数据的情况。

**防止缓存 (Prevent Caching)**

要完全防止缓存，使用 `no-store` 指令，它指示客户端不要碰缓存。（这也不会导致现有的缓存项被删除。）

**减少新鲜验证 (Reduce Fresh Validations)**

`immutable` 指令是一种优化；它告诉客户端即使在刷新时也不要重新验证新鲜项。这可以在 URL 是不可变的时使用，例如通过其哈希值检索资源时。不过并非所有浏览器都实现了这一点。

**启发式缓存 (Heuristic Caching)**

即使有了这些指令，客户端仍然拥有很大的自由度。如果没有实际用例，仅凭规范无法实现实用的软件。当服务器完全不使用 `Cache-Control` 时，客户端的自由度达到最高。这在网络浏览器中被称为[启发式](https://developer.mozilla.org/en-US/docs/Web/HTTP/Caching#heuristic_caching) [缓存[2]](https://developer.mozilla.org/en-US/docs/Web/HTTP/Caching#heuristic_caching)。

例如，浏览器可能会使用 `Last-Modified` 时间作为一种启发，使用从上次修改到现在的持续时间的一小部分作为缓存的 TTL（生存时间）。

## 非客户端缓存

到为止，我们假设缓存是由面向用户的客户端（如浏览器）完成的。在实践中，缓存也可以以下方式提供：

- 由服务器应用程序。这对于动态生成的内容特别有用。应用程序存储生成的内容以便自身复用。目标是节省延迟和/或生成内容的成本。由于应用程序控制内容，也可以轻松使用 `ETag` 方案来辅助客户端缓存。
- 由透明代理或中间件。代理充当源服务器的客户端，代表真实客户端处理请求。它可以像其他客户端一样缓存响应。这种形式的代理可以由服务开发者、CDN 或 ISP（在 HTTPS 流行之前）部署。

## 共享缓存与私有缓存

缓存代理的一个问题是，响应可能是个性化的，那么缓存代理如何知道哪些内容属于哪个用户？

这个问题在浏览器中并不存在，因为它代表单一用户。对于多个用户共享的缓存，有指令可以显式将响应标记为公共（public）或私有（private）。`private` 指令用于不应被代理缓存的个性化内容。

`Cache-Control: private`

对于决定是否缓存还有额外的规则。例如，`Authorization` 头部字段通常会防止代理缓存响应。但 `public` 指令可以覆盖此规则并使内容可缓存。

## 云端缓存

RFC 仅以非常松散的定义定义了预期的缓存行为。对于开发或理解真实世界的项目，你应该依赖软件/服务手册。

有许多云提供商提供 CDN 或缓存服务，有些甚至提供了额外的缓存控制。阅读它们的文档以了解它们在实践中是如何工作的。示例包括：

- [Cloudflare[3]](https://developers.cloudflare.com/cache/concepts/cache-control/)
- [AWS CloudFront[4]](https://docs.aws.amazon.com/AmazonCloudFront/latest/DeveloperGuide/Expiration.html)
- [Azure CDN[5]](https://learn.microsoft.com/en-us/azure/cdn/cdn-how-caching-works)
- [Google Cloud CDN[6]](https://cloud.google.com/cdn/docs/caching)

---

# 第 12 章：压缩与流 API

下一个主要功能是压缩。我们还将探索 Node.JS 中的流抽象（我们之前忽略了它）。

## 12.1 HTTP 压缩如何工作原理

### 与 `Accept-Encoding` 协商

HTTP 压缩与其他功能一样，是可选的，因此客户端必须显式请求服务器压缩响应。这是通过 `Accept-Encoding` 头部字段实现的，它包含一个用逗号分隔的压缩方法列表。常用的方法包括：

- `gzip`
- `deflate`
- `br`。[Brotli[1]](https://www.rfc-editor.org/rfc/rfc7932.html) 更新更新但支持范围较小。

该方法后面可以跟一个可选的权重以指示其优先级。具体语法请参见 RFC。

`Accept-Encoding: deflate, gzip;q=1.0`

### 使用 `Content-Encoding` 压缩

如果服务器选择了建议的压缩方法之一，它将通过 `Content-Encoding` 进行报告。

`Content-Encoding: gzip`

可以应用多个 `Content-Encoding`。但是，这没有实际用途。

某些内容类型已经是压缩过的，例如 PNG、JPG 或 ZIP。最好将它们排除在压缩之外，因为它们是不可压缩的。

### 压缩与 `Content-Length`

`Content-Length` 的目的不会随压缩而改变，即它是 HTTP 体的长度，而不是未压缩数据的长度。

当实时应用压缩时，压缩后的尺寸是无法预知的（除非缓冲整个输出，但这对于大内容无效），因此我们还需要使用分块传输（chunked encoding）。

### 压缩与缓存

压缩是 CPU 密集型的，它并不总是实时应用的；缓存代理可以缓存并提供压缩后的响应（如果 `Accept-Encoding` 允许）。

如果缓存代理不在乎压缩，它至少不能混合来自不同压缩方法的响应。这就是 `Vary` 头部字段的目的，告知代理如果使用了某些头部字段，响应将会发生变化。

例如，如果使用了 `Vary: content-encoding`，缓存项将使用 `Content-Encoding` 的值作为键，因此缓存查找将考虑这一点。

### 压缩上传

由于内容协商的性质，目前没有一种标准的方法来压缩请求体。如果客户端使用 `Content-Encoding` 这样做，可能是应用程序而非 HTTP 服务器来解压缩请求。

### 压缩与范围请求（Range Requests）

`Content-Encoding` 是内容的属性。因此，`Range` 头部字段作用于压缩后的数据，这并不是我们预期的行为。

通常做法是在提供范围响应时不进行压缩。

### 使用 `Transfer-Encoding` 压缩



还有另一种罕用/受支持的压缩方法。`Transfer-Encoding` 通常用于分块传输，它也可以压缩负载。

`Transfer-Encoding: gzip, chunked`

上述头部字段意味着负载先经过 gzip 压缩，然后进行分块传输。

它与 `Content-Encoding` 有什么区别？区别在于 `Transfer-Encoding` **不是**内容的属性，因此范围请求可以作用于 `Transfer-Encoding`，但不能作用于 `Content-Encoding`。

与其他晦涩的 HTTP 特性不同，使用 `Transfer-Encoding` 进行压缩实际上更实用，因此更为优，但遗憾的是实现上却走向了反面。

`TE` 头部字段用于协商 `Transfer-Encoding`，总结下所示。

表 1：HTTP 压缩协商。

| 请求头 | 响应头 | 广泛使用？ |
| :--- | :--- | :--- |
| `Range` | | 否 |
| `Accept-Encoding` | `Content-Encoding` | 是 |
| `TE` | `Transfer-Encoding` | 支持（否） |

## 12. 压缩与流 API

### 12.1 使用管道进行数据处理

#### 数据处理与 IO

我们将使用内置的 [`zlib`](https://nodejs.org/api/zlib.html) 模块来压缩响应体。压缩数据有 2 类 API，最简单的是输入作为单个 buffer 提供并将压缩后的数据作为单个 buffer 返回。如果输入很大，这种方法将不起作用，因为它可能无法放入内存。而且即使不考虑内存问题，延迟也会很糟糕。

```javascript
zlib.gzip(buffer, callback);
```

第二类是*实时*产生输出，你首先初始化有状态的压缩对象，然后向压缩器提供输入，压缩器会同时产生输出。

```javascript
const obj = zlib.createGzip();
// 从它读取并向它写入
```

压缩器具有背压（backpressure），因此如果使用得当，它不会撑爆内存。你必须同时排空输出以保持输入流动。

实时处理数据的方法是使用可以同时*读取*和*写入*的有状态处理器，这与我们处理 socket 的方式类似。

### 12.2 用于组合数据处理器的 Unix 管道

拥有多个数据处理步骤是常见的，而 Unix 管道是编程和组合这些步骤的一种*高层*方式。一个具体的例子是：

```bash
tar -c -f - ./directory | gzip | nc 1.2.3.4 1234
```

它通过 2 个管道连接 3 个步骤：

1. `tar`，归档生产者。
2. `gzip`，消耗归档并产生 gzip 数据。
3. `nc`，消耗 gzip 数据并通过网络发送。

管道自动将输出连接到输入，而无需用户编写代码在步骤之间移动数据。

#### 抽象管道

我们可以在 HTTP 服务器中使用一种类似管道的抽象：

`produce-response | gzip-compress | chunk-encode | write-to-socket`

这种模式有如下优点：

- 无需显式读取和写入数据；编写的代码更少！
- 背压是自动的（如果每个处理器都实现得当）。
- 正如我们所看到的，它不容易出错。

### 12.3 探索 Node.JS 中的流 API

#### 流接口列表

Node.JS 中确实存在管道，你可以通过 [Stream API](https://nodejs.org/api/stream.html) 管道化内容。

```javascript
import * as stream from "stream";
```

它定义了一组你可以实现的接口。

| 名称 | 说明 | 示例 |
| :--- | :--- | :--- |
| `Readable` | 从此消耗输出。 | `fs.createReadStream()` |
| `Writable` | 向此处提供输入。 | `fs.createWriteStream()` |
| `Duplex` | Readable + Writable。 | `net.Socket` |
| `Transform` | 扩展 Duplex。 | `zlib.createGzip()` |

`Readable` 和 `Writable` 是 2 个基础抽象。`Duplex` 和 `Transform` 都是 `Readable` 和 `Writable` 的组合，它们之间的区别对我们目前并不重要。

一些内置的 Node.JS 模块已经实现了它们，如表所示。

#### 在流接口上使用管道

我们探索这些抽象的目标是在它们上使用管道。

```javascript
import { pipeline } from "stream/promises";
```

`pipeline()` 函数将一个 `stream.Readable` 连接到 `stream.Writable`。在创建管道后，数据会自动从生产者流向消费者，并且存在背压，就像在 Unix 管道中一样。这个函数以 Unix 管道命名，不要将其与请求管道化（request pipelining）混淆。

```typescript
function pipeline(src: stream.Readable, dst: stream.Writable): Promise<void>;
```

你还可以在源和目的地之间放置一个或多个 `stream.Duplex`。

```typescript
function pipeline(
  src: stream.Readable,
  transform1: stream.Duplex,
  transform2: stream.Duplex,
  // 更多 ...
  dst: stream.Writable,
): Promise<void>;
```

### 12.4 实现 HTTP 压缩

`zlib` 模块为压缩对象实现了 `stream.Duplex`。这是一个学习如何 Node.JS Stream API 的绝佳机会。

#### 步骤 1：检查头部字段并启用压缩

根据头部字段操作。我们将在客户端请求时实现压缩。

```typescript
function enableCompression(req: HTTPReq, res: HTTPRes): void {
  const codecs: string[] = req.headers['accept-encoding'];
  if (!codecs.includes('gzip')) {
    return;
  }
  // 转换响应
  res.headers['content-encoding'] = 'gzip';
  res.body = gzipFilter(res);
}
```

#### 步骤 2：理解没有管道时的注意事项

如果不使用 `pipeline()` 函数，你可能会这样构思方案：

```typescript
function gzipFilter(reader: BodyReader): BodyReader {
  const gz: stream.Duplex = zlib.createGzip();
  return {
    length: -1,
    read: async (): Promise<Buffer> => {
      const data = await reader.read();
      await gz.write(data);
      // 背压导致死锁！
      return await gz.read();
    },
  };
}
```

遗憾的是，这种伪代码由于两个原因不起工作：

1. 压缩器实现了背压，这意味着如果你写入大量输入，代码将阻塞直到输入被处理并*排空*。但在上面的伪代码中，数据是在写入完成后才被排空的，这是一种死锁情况！（我们在“管道化请求”部分讨论过类似的死锁。）
2. 大多数数据压缩方法本质上需要缓存；1 次输入不会产生 1 个压缩输出。在没有足够数据的情况下，压缩器不会产生输出，因为它还没有决定如何压缩数据。从压缩器读取将阻塞在等待更多数据！

在 Unix 管道中，读取和写入发生在不同的进程中，管道是*同时*填充和排空的，因此不会出现上述方案中的死锁。这就是为什么我提到管道抽象的使用不容易出错。

#### 步骤 3：实现 `stream.Readable`

我们回到了正轨。在使用 `pipeline()` 函数之前，我们必须为数据源 `BodyReader` 实现 `stream.Readable` 接口。

以下是实现 `stream.Readable` 的方法：

1. `stream.Readable` 有一个内部队列，使用 `push()` 方法将数据添加到队列，然后数据即可消费。
2. 你应该何时向队列添加数据？你需要实现一个 `read()` 回调，该回调会在队列为空且有人在消费时被调用。这对于维护背压至关重要。
3. 使用 `destroy()` 方法将错误传递给消费者。

```javascript
function body2stream(reader: BodyReader): stream.Readable {
  let self: null | stream.Readable = null;
  // make TS happy
  self = new stream.Readable({
    read: async () => {
      try {
        const data: Buffer = await reader.read();
        self!.push(data.length > 0 ? data : null);
      } catch (err) {
        self!.destroy(err instanceof Error ? err : new Error('IO'));
      }
    },
  });
  return self;
}
```

> **注意**：`push()` 方法使用 `null` 来标记流的结束，这与我们正在使用的（0 长度缓冲区）不同。

#### 步骤 4：创建管道

让我们尝试在 `BodyReader` 和 `compressor` 之间建立一个管道。

```javascript
function gzipFilter(reader: BodyReader): BodyReader {
  const gz: stream.Duplex = zlib.createGzip();
  const input: stream.Readable = body2stream(reader);
  (async () => {
    try { await pipeline(input, gz); }
    catch (err) { gz.destroy(err); }
  })();
  // not awaiting it
  // return the wrapped `BodyReader` ...
}
```

`pipeline()` 函数将为我们移动数据，并返回一个 promise 供我们等待。

我们还必须在等待 promise 时捕获任何异常，并且捕获的错误必须传递给下一个流，否则它的消费者将永远挂起。

在 `gzipFilter()` 函数中，我们无法等待管道完成，因为我们必须向调用者返回一个封装过的 `BodyReader`，因此 `try-catch` 块被封装在一个没有 `await` 的匿名异步函数调用中。这可以通过向 promise 注册一个错误处理回调来简化。

`pipeline(input, gz).catch((err: Error) => gz.destroy(err));` // no await

#### 步骤 5：从 `stream.Readable` 读取

现在管道已经在运行了，我们可以从 `compressor` 读取输出。记得 `net.Socket` 也是一个 `stream.Readable`；`soRead()` 函数可以在不修改的情况下使用（除了类型注解），因为各种套接字事件（如 `'data'` 和 `'end'`）、`pause()` 和 `resume()` 方法实际上定义在 `stream.Readable` 上。

但 `stream.Readable` 接口已经有一个基于 promise 的读取方法。它的 `iterator()` 方法返回一个 `AsyncIterator`，你可以像使用生成器一样在 `for await...of` 循环中使用它。`AsyncIterator` 还有一个类似于生成器的 `next()` 方法。

```javascript
function gzipFilter(reader: BodyReader): BodyReader {
  // ...
  const iter: AsyncIterator<Buffer> = gz.iterator();
  return {
    length: -1, // 压缩后的 "Content-Length" 未知
    read: async (): Promise<Buffer> => {
      const r: IteratorResult<Buffer, void> = await iter.next();
      return r.done ? Buffer.from('') : r.value;
    },
    close: reader.close,
  };
}
```

返回的 `BodyReader` 包装器从 `compressor` 读取。如果为了学习，可以跳过 `soRead()` 函数。

#### 步骤 6：测试

我们快完成了，让我们为所有响应启用压缩并测试。

```javascript
const res: HTTPRes = await handleReq(msg, reqBody);
try {
  enableCompression(msg, res);
  await writeHTTPHeader(conn, res);
  if (msg.method !== 'HEAD') {
    // omit the body
    await writeHTTPBody(conn, res.body);
  }
} // ...
```

`curl` 可以请求压缩后的响应：

`curl -vvv http://127.0.0.1:1234/`

#### 步骤 7：刷新缓冲区

压缩可以工作。但有一个问题：当你测试 `/echo` 或 `/sheep` URI 时，响应没有立即出现。这是由于 `compressor` 的缓冲导致的。从“缓冲区写入”讨论中，我们知道必须有一种方法来 `flush` 缓冲区强制 `compressor` 输出。

`gz.flush(callback);`

但由于使用了 `pipeline()` 而不是显式的 `IO`，没有地方插入 `flush()` 调用。不过有一个选项可以让 `compressor` 自动刷新。

`const gz = zlib.createGzip({flush: zlib.constants.SYNC_FLUSH});`

频繁刷新 `compressor` 会降低压缩效率。因此，让应用程序控制是否刷新是一个好主意。例如，在提供静态文件时，不需要刷新 `compressor`，因为数据生成得尽可能快。

对于生成非常小数据块的应用程序，可能根本不压缩压缩，因为频繁刷新效果不好。

### 12.5 讨论：重构为 Stream

你可以尝试重构代码以使用更多的流和管道。首先，替换 `BodyReader` 接口中的 `read()` 函数。



```typescript
// 从/向 HTTP body 读取/写入数据的接口
type BodyReader = {
  // "Content-Length", 如果未知则为 -1。
  length: number,
  // 读取数据。
  reader: stream.Readable,
};
```

通过更多的流和管道可以节省大量代码：

1. 不需要 `soRead()` 函数的实现。
2. 读取磁盘代码可以用 `fp.createReadStream()` 替换。
3. `writeHTTPBody()` 函数只需在响应和套接字之间创建一个管道。
4. 由于我们不再处理显式的读写，分块编码器可以用实现 `stream.Transform` 来替换。
5. 生成器可以通过 `stream.Readable.from()` 转换为 `stream.Readable`。

[报告错误 | 提问](https://forms.gle/UKo4bncUnuMGBrTM7) @ [build-your-own.org](https://build-your-own.org)

106

2024-02-02

## 12. 压缩与 Stream API

响应请求的整个过程变成一系列管道：`produce-response | gzip-compress | chunk-encode | write-to-socket`

### 12.6 讨论：水位（High Water Mark）与背压

#### 单项队列

我们维护背压的方法是等待队列或缓冲区排空。从生产者和消费者的角度，队列有 2 个状态：

| 队列 | 可以产生 | 可以消费 |
| :--- | :---: | :---: |
| 空闲 | 是 | 否 |

这限制了队列最多只能有 1 个项目或 1 次待处理写入。

#### 高水位背压

然而，某些背压实现稍微复杂一些——队列限制字节数而不是仅仅 1 次写入。这个限制通常被称为水位。使用水位进行背压时，队列有 3 个状态：

| 队列 | 可以产生 | 可以消费 |
| :--- | :---: | :---: |
| 空 | 是 | 否 |
| 半 | 是 | 是 |
| 满 | 否 | 是 |

这更像 Unix 管道，Unix 管道是一个边界缓冲区，只要它未满就可以向其中添加更多字节；不需要等待它完全排空。

#### 使用队列批处理数据

使用水位而不是单项队列的原因是队列可以合并多次小写入。例如，当数据从队列移动到套接字时，有一些可能的优化：

- 队列可以是单个缓冲区；每当你向它写入时，数据都会追加到缓冲区。这会自动合并多次小写入，并将所有数据一次性发送到套接字。
- 队列存储单个缓冲区对象，在发送到套接字之前，可以将多个缓冲区合并为一个较大的缓冲区。
- 队列存储单个缓冲区对象，可以使用 `writev()` 系统调用一次性发送多个缓冲区，而无需手动合并。

所有优化都实现了之前讨论的半透明缓冲。另请参见：`stream.Writable._writev()`

## Node.js 中的高水位标记

`stream.Readable` 和 `stream.Writable` 都有一个内置的高水位标记，在实现它们时，可以通过 `highWaterMark` 选项进行更改。对于高吞吐量应用，通常使用较大的值是很有意义的。

```javascript
const r = new stream.Readable({
  highWaterMark: 4096,
  // 也适用于 `Writable`
  read: async () => { /* 生成数据并将其推送到 r.push() */ },
});
```

在使用高水位标记处理背压时，请检查 `Readable.push()` 和 `Writable.write()` 的返回值：

- 当队列满时，它们返回 `false`，因此你可以等待它排空。
- 否则，你可以向其中推入更多数据。

我们没有使用它们的返回值，是因为我们简单地将高水位标记视为 0，并在每次写入后排空队列。

表 5：流中的高水位标记。

| 接口 | 背压指示器 | 等待队列排空 |
| :--- | :--- | :--- |
| `Readable` | `.push(data)` | 通过 `read()` 回调 |
| `Writable` | `.write(data, cb)` | 通过 'drain' 事件。 |

流接口支持但不强制要求背压；即使队列满了，你仍然可以向它们推入数据，这对于初学者来说是一个性能陷阱。

[报告错误 | 提问](https://forms.gle/UKo4bncUnuMGBrTM7) @ [build-your-own.org](https://build-your-own.org)

108

# 第 13 章 WebSocket 与并发

让我们探索一些不同的东西 —— WebSocket (RFC6455) 我们还将仔细查看生产者-消费者问题，因为它们在网络应用中很常见。

## 13.1 建立 WebSocket

### 高层概述

我们已经在“动态内容”章节中讨论过 WebSocket。从用户的角度来看，WebSocket 是：

- 一个双向、全双工通道。
- 基于消息的，而不是字节流。
- 对现有 HTTP 服务器的扩展。

### 从 HTTP/1.1 升级

WebSocket 以 HTTP 头部开始，这是它与 HTTP 唯一的共同点。客户端使用 `Upgrade: websocket` 头部字段表示意图创建一个 WebSocket，服务器通过此头部和状态码 101 响应，表示 WebSocket 已建立。连接的其余部分将由 WebSocket 协议接管。

示例：

```
GET /chat HTTP/1.1
Upgrade: websocket
Connection: Upgrade
Sec-WebSocket-Key: dGhlIHNhbXBsZSBub25jZQ==

HTTP/1.1 101 Switching Protocols
Upgrade: websocket
Connection: Upgrade
Sec-WebSocket-Accept: s3pPLMBiTxa9kYGhZK+Oo=
```

如果服务器对 WebSocket 一无所知，它将像普通的 HTTP 请求一样响应。这是扩展的一种方式。

[报告错误 | 提问](https://forms.gle/UKo4bncUnuMGBrTM7) @ [build-your-own.org](https://build-your-own.org)

109

2024-02

### WebSocket 握手

WebSocket 握手包含一些额外的头部：

- 客户端发送 `Sec-WebSocket-Key`。
- 服务器通过 `Sec-WebSocket-Accept` 响应。

握手的一些原因如下：

1. 服务器理解 WebSocket。
2. `Sec-WebSocket-Key` 字段用于防止 WebSocket 缓存。
3. 代理服务器可能会缓存 101 状态码。

哈希值通过以下代码计算：

```javascript
function wsAccept(key) {
  return crypto.createHash('sha1')
    .update(key)
    .digest("base64");
}
```

### Connection 字段

`Connection` 头部用于从 HTTP/1.1 切换到 WebSocket。这是为了扩展协议。

110

2024-02

## 13.2 WebSocket 协议

### 帧格式

握手之后的连接部分由一系列帧组成。

| 字节 0 | 字节 1 | 字节 2 | 字节 3 |
| :--- | :--- | :--- | :--- |
| 0 1 2 3 4 5 6 7 | 0 1 2 3 4 5 6 7 | 0 1 2 3 4 5 6 7 | 0 1 2 3 4 5 6 7 |
| 标志 | 掩码 | 长度高 | 长度低 |
| FIN | | | |
| RSV1 | | | |
| Op | | | | |
| | | | | | | | | | | | | | 0 1 2 3 4 5 6 7 | 0 1 2 3 4 5 6 7 | 0 1 2 3 4 5 6 7 | 0 1 2 3 4 5 6 7 |
| 掩码位 | | | | | | | | | | | | | | |

注意：处理帧比处理 HTTP 要简单得多：

1. 第一字节包含 `FIN` 标志和 4 位 `opcode`。
2. 第二字节中的 `MASK` 位指示可选的 `mask-key`。
3. 接下来的字段是负载长度，以 7 位整数编码：
   - 0 到 125 的长度存储在该 7 位整数中。
   - 126 表示后续为 16 位大端整数。
   - 127 表示后续为 64 位大端整数。
4. 如果 `MASK` 位被设置，则后续有一个 4 字节随机掩码。该 4 字节掩码与负载数据进行异或。掩码必须用于客户端到服务器的帧，但反向则不然。掩码的目的是防止一种类型的缓存攻击。

### 帧类型

数据消息的 opcode：

- `0x01`：文本数据消息。用于应用程序。
- `0x02`：二进制数据消息。用于应用程序。
- `0x00`：消息分片。稍后讨论。

文本和二进制的区分取决于应用程序。

控制消息的 opcode：

- `0x08`：用于优雅终止的控制消息。可选负载包含状态码和字符串消息。
- `0x09` 和 `0x10`：Ping 和 pong，即心跳包。用于保持连接活跃和探测断开连接。对于应用程序可以是透明的。

### 分片消息

WebSocket 还支持在不预知消息长度的情况下发送消息，类似于 HTTP 中的分块传输编码。一个“逻辑”数据消息可以被分成多个帧，但应用程序看到的是合并后的消息。

- 第一帧的操作码为 `0x01` 或 `0x02`，其余帧使用 `0x00`。
- 最后一帧设置了 `FIN` 标志。
- 只有数据消息（opcode `0x01` 和 `0x02`）可以被分片。
- 不同消息的帧不能交替出现，控制消息除外。

一个包含 3 个分片的示例：

| opcode=0x01, FIN=0 | opcode=0x00, FIN=0 | opcode=0x00, FIN=1 |

未分片的消息被编码为单帧，操作码为 `0x01` 或 `0x02`，并设置了 `FIN` 标志。

类似于分块传输编码的设计，你可以将任意大小的数据作为单条消息流传输。但许多实现将消息数据表示为单个缓冲区，因此消息大小存在限制。

## 13.3 并发性编程简介

### 竞态条件



# WebSocket 与并发

在基于消息的设计中，由单个消费者消费多个消息源的情况很常见，例如多个并发任务通过单个 `WebSocket` 发送消息。

由于 `WebSocket` 消息被序列化为单个 `TCP` 字节流，对套接字的并发写入会破坏协议。

让我们用一个假设的示例来来说明这个问题。

```javascript
// 伪代码！
async function send(conn, msg) {
  await write_header(conn, msg);
  await write_body(conn, msg);
}
```

在这个示例中，写入 1 条消息涉及 2 次套接字写入，且代码在每个 `await` 语句处都会让给运行时。问题是，当返回运行时后，运行时可能会调度另一个也在发送消息的任务，导致套接字写入发生*交替*现象。

这在并发编程中被称为 `race condition`（竞态条件）。注意，这与单线程运行时或 CPU 核心数*完全无关*。

## 原子操作

你可能认为解决方案是每条消息只使用 1 次套接字写入。然而，这种解决方案是……

- 仅在套接字写入是原子的情况下正确，而这可能无法保证。
- 并不总是可行且不方便。考虑到 `WebSocket` 消息可以被分片并像流一样使用。

## 使用互斥锁实现互斥

一种解决方案是使用锁（`mutex`）来限制对套接字的并发写入。

在并发访问的情况下，一个任务持有 `lock`，其他任务在 `await` 语句处阻塞，释放锁将解除其中一个等待者的阻塞。`mutex` 是许多并发环境中 `synchronization primitives`（同步原语）之一。

## 使用队列多路用

防止并发访问的另一种解决方案是使用队列。队列接收来自并发生产者的 `WebSocket` 消息，由一个专用任务从队列中消费并写入套接字。

```javascript
// 伪代码
let queue = createQueue();
// 用于多个生产者
async function produce(msg) {
  await queue.pushBack(msg);
}

async function single_consumer() {
  while (running()) {
    const msg = await queue.popFront();
    // 写入套接字
  }
}
```

`mutex` 也是队列的一种形式，它不传递数据，而是传递控制权。

## 使用阻塞队列进行流量控制

`JS` 数组是一个可以 `push` 和 `pop` 的队列。但它对并发编程并不可好用。作为消费者，你如何知道队列何时不为空呢？这需要一种机制，允许消费者等待生产者。

这种机制可以在队列中实现！这就是为什么上面的伪代码使用 `await` 来从队列中消费数据。这被称为 `blocking queue`（阻塞队列），因为当队列为空时，消费者会被阻塞。

此外，反压（backpressure）要求队列的容量是有边界的。这通过让生产者在队列满时发生阻塞来实现。与 `Node.JS` 中的 `Stream` API 相比，这消除了不强制要求反压的“陷阱”。

```typescript
// 生产者和消费者都可以阻塞。
type Queue<T> = {
  pushBack(item: T): Promise<void>;
  popFront(): Promise<T>;
};
```

`blocking queue` 不仅在生产者和消费者之间传递数据，还传递 `control`，这类似于 `mutex`。事实上，虽然传递数据很方便，但在并发编程中传递控制权是更基础的。

## 使用可关闭队列进行取消

阻塞队列在阻塞行为上与 Unix 管道（pipe）相似。有一点不同：管道是可以被 `closed` 的！

- 如果由生产者关闭，消费者将获得 `EOF`。
- 如果由消费者关闭，生产者在写入时会收到错误。

在并发编程中，有时你需要任务退出工作。例如，如果 `WebSocket` 在应用程序任务阻塞它（读取或写入）时被关闭，任务应该被唤醒（获取 `EOF` 或错误），而不是永远挂起。

如果任务是队列的消费者，你可以在队列中放入特殊值来通知消费者退出。但对于等待队列的生产者来说，这并不容易。幸运的是，我们可以向 Unix 管道学习——添加一个 `close()` 方法来解除所有生产者和消费者的阻塞。

```typescript
type Queue<T> = {
  pushBack(item: T): Promise<void>;
  // 如果关闭则抛出异常
  popFront(): Promise<null|T>;
  // 如果关闭则返回 null
  close(): void;
};
```

我们可以向生产者抛出异常并向消费者返回 null，模拟关闭的管道。

## 阻塞队列作为同步原语

同步原语是用于阻塞和解除阻塞任务（传递控制权）的东西。

一些传统的同步原语包括：

- `Mutex`。
- `Semaphore`。
- `Condition variable`。
- `Event`。

除了传统的同步原语之外，`Golang` 还采用 `channel` 作为其主要的同步原语，它与我们讨论的阻塞队列非常相似。

`Node.JS` 并不包含这些同步原语，并发问题通常被掩盖在大量的回调中。幸运的是，随着 `async/await` 的加入，这些原语可以复制到 `JS` 中。但我们必须先使用 promises 和回调创建它们。

## 步骤 1：分析问题

考虑一个仅具有 `push` 和 `pop` 且没有缓冲能力的阻塞队列。该队列应该被多个生产者和多个消费者使用，这比生成器更通用。

```typescript
type Queue<T> = {
  pushBack(item: T): Promise<void>;
  popFront(): Promise<T>;
};
```

创建一个 promise 会产生一个 `resolve` 回调，用于稍后完成它的状态。生产者要么等待消费者，要么唤醒一个正在等待的消费者。

- 如果没有消费者在等待，它会将回调存储在某处。未来的消费者将调用该回调来获取数据并完成生产者。
- 如果有正在等待的消费者，则通过调用其回调来完成其中一个。

消费者的情况也类似：

- 它要么存储一个回调来等待生产者，
- 或者调用正在等待的生产者的回调。

## 步骤 2：Push 和 Pop

可能会有多个等待中的生产者或消费者，因此我们需要在列表中存储它们的回调。

对于消费者，只需存储它们自己的 `resolve` 回调以接收数据。

对于生产者，回调负责做两件事：

1. 获取消费者的回调并完成它（带上数据）。
2. 完成它自己的 promise。

```typescript
// 一个多生产者、多消费者且容量为 0 的队列。
function createQueue<T>(): Queue<T> {
  type Taker = (item: T) => void;
  // 完成消费者任务
  type Giver = (take: Taker) => void;
  // 唤醒生产者
  const producers: Giver[] = [];
  const consumers: Taker[] = [];

  return {
    pushBack: (item: T): Promise<void> => {
      return new Promise<void>((done: () => void) => {
        const give: Giver = (take: Taker) => {
          take(item);
          done();
        };

        if (consumers.length) { // 消费者正在等待
          give(consumers.shift()!);
        } else {
          // 等待生产者
          producers.push(give);
        }
      });
    },
    popFront: () => Promise<T> {
      return new Promise<T>((take: Taker) => {
        if (producers.length) { // 生产者正在等待
          producers.shift()!(take);
        } else {
          // 等待消费者
          consumers.push(take);
        }
      });
    },
  };
}
```

## 步骤 3：关闭队列

`close()` 方法稍后会非常有用。

```typescript
type Queue<T> = {
  pushBack(item: T): Promise<void>; // 如果关闭则抛出异常
  popFront(): Promise<T>;           // 如果关闭则返回 null
  close(): void;
};
```

由于我们可能在生产者处抛出异常，也存储了 `reject` 回调。

```typescript
type Rejector = (err: Error) => void;
const producers: { give: Giver, reject: Rejector }[] = [];
let closed = false;
```

我们还会记住 `closed` 状态。在推入或弹出之前应该检查此状态。关闭队列会解阻塞所有人。

```typescript
close: () => {
  // 解阻塞任何正在等待的生产者或消费者
  closed = true;
  while (producers.length) {
    producers.shift()!.reject(new Error('queue closed'));
  }
  while (consumers.length) {
    consumers.shift()!(null);
  }
}
```

## 步骤 4：添加缓冲区

该队列对于我们的目的已经足够。对于其他某些情况，队列可能需要缓冲固定数量的项而不阻塞生产者。这留给你们作为一个练习。

```typescript
function createQueue<T>(capacity: number): Queue<T>;
```

# WebSocket 服务器

## 步骤 1：设计消息接口

`WebSocket` 消息在应用中表示为 `WSMsg` 类型。负载数据使用 `read()` 函数进行，类似于 `BodyReader` 接口，支持任意大小的消息并实时接收数据。

```typescript
const WS_DATA_TEXT = 0x01;
const WS_DATA_BINARY = 0x02;

// WebSocket 消息类型
type WSMsg = {
  type: number;   // WS_DATA_TEXT, WS_DATA_BINARY
  length: number; // 字节
  read: () => Promise<Buffer>; // EOF 后为空
};
```

虽然 `read()` 函数不需要将整个消息都存储在内存中，但它确实有一个缺点：应用程序必须确保消息数据被消费，否则下一帧将无法解析。

## 步骤 2：设计应用接口

`WSServer` 是用于发送和接收数据消息的应用接口。

```typescript
type WSServer = {
  send(msg: WSMsg): Promise<void>; // 支持多个生产者
  recv(): Promise<null|WSMsg>;     // EOF 后返回 null
  close(): void;
};
```

这与我们对 socket 进行的操作类似——从它读取并向它写入。只不过并发读写有合法的用场景且必须被支持：

- 并发写入：多个应用任务独立生成消息。
- 并发读取：使用任务池进行并发消息处理。

你也可以使用回调来传递消息而不是主动读取它们。但这会让背压（backpressure）变得不明显，因为你还需要 `pause()` 和 `resume()` 方法。这就是为什么我们早期就放弃了基于回调的 IO。

## 步骤 3：设计服务器任务

与请求-响应模式不同，发送和接收是独立的。因此，我们需要：

- 一个解析入字节字节流的任务：`wsServerRecv()`。
- 一个向 socket 写入消息的任务：`wsServerSend()`。

这两个任务与应用任务并发运行。使用两个队列连接这两个任务与应用（发送和接收）。另一个队列用于连接 `wsServerSend()` 到 socket。

`App <= qrecv (Queue) <= wsServerRecv <= reqBody (BodyReader)`

`App => qsend (Queue) => wsServerSend => qsock (Queue) => resBody (BodyReader)`

可能会有多个应用任务通过单个 `WebSocket` 产生或消费数据，但读取和写入 socket 的任务必须是顺序的。这是一个通过传递数据解决并发问题的示例。

## 步骤 4：启动服务器任务

让我们为上一步步骤编写代码。

```typescript
function createWSServer(reqBody: BodyReader): [WSServer, BodyReader] {
  const qrecv: Queue<WSMsg> = createQueue<WSMsg>();
  const qsend: Queue<WSMsg> = createQueue<WSMsg>();

  const ws: WSServer = {
    send: qsend.pushBack,   // 如果关闭则抛出
    recv: qrecv.popFront,   // 如果关闭则返回 null
    close(): void => {
      qsend.close(); // 生成 WS_CTRL_CLOSE
      qrecv.close();
    },
  };

  // 任务 1：从 socket 读取
  wsServerRecv(reqBody, qrecv, ws)
    .finally(ws.close) // 关闭 WS API
    .catch(console.error); // 无等待

  // 任务 2：向 socket 写入
  const qsock: Queue<Buffer> = createQueue<Buffer>();
  wsServerSend(qsend, qsock)
    .finally(ws.close) // 关闭 WS API
    .finally(qsock.close) // 关闭 socket
    .catch(console.error); // 无等待

  const resBody: BodyReader = {
    length: -1,
    read: async () => await qsock.popFront() || Buffer.from(''),
  };

  return [ws, resBody];
}
```

注册在 promise 上的 `finally()` 回调行为类似于 `try-finally` 块。这用于关闭队列，以便任务不会永远挂在队列中。

注意：如果你没有 `await` 一个异步函数，那么使用 `catch()` 回调来捕获异常是关键的，否则你的程序将会崩溃。在这种情况下，我们简单地记录了并忽略了异常，但有时你需要传播错误。

## 第 5 步：向 Socket 消息

`wsServerSend()` 任务从队列中获取 `WSMsg` 输入，并将数据输出到 `qsock` 队列，该队列由 `BodyReader` 提取。帧代码已省略。

```javascript
// 格式化 WS 消息并将其发送到 socket
async function wsServerSend(
  qsend: Queue<WSMsg>, qsock: Queue<Buffer>): Promise<void>
{
  while (true) {
    const msg = await qsend.popFront();
    if (!msg) { // 关闭它
      // 省略。发送一个“close”帧 ...
      break;
    }
    // 省略。将帧数据写入 qsock ...
  }
}
```

注意这与使用 Unix 管道有多么相似：

- 输入和输出的统一接口。
- 可组合性。

## 第 6 步：从 Socket 解析帧

`wsServerRecv()` 为每个帧进行循环，并将 `WSMsgs` 馈送到输出队列。

```javascript
// 从客户端解析 WS 帧
async function wsServerRecv(
  reqBody: BodyReader, qrecv: Queue<WSMsg>, ws: WSServer): Promise<void>;
```

我们将使用另一个队列将帧数据发送到 `WSMsg` 的 `read()` 函数中。



```javascript
// 创建一个 WSMsg
const q = data = createQueue<Buffer>();
const msg: WSMsg = {
  // 省略 ...
  read: async () => await q.popFront() || Buffer.from(''),
};
await qrecv.pushBack(msg);
// 省略。将负载数据馈送到 q ...
```

[报告错误 | 提问](https://forms.gle/UKo4bncUnuMGBrTM7) @ [build-your-own.org](https://build-your-own.org)

122

2024-02-02

# 13. WebSocket 与并发

一个数据消息可以跨越多个帧，因此我们需要在循环之外存储队列，并在更多帧到达时馈送队列。请记住在设置 `FIN` 标志或退出循环时，确保队列已关闭。

```javascript
// 为当前消息提供数据
let data: null|Queue<Buffer> = null;
try {
  // 为每个帧进行循环
  while (true) {
    // 省略 ...
  }
} finally {
  // 如果应用阻塞在数据上，则关闭消息数据。
  data?.close();
}
```

## 第 7 步：与 HTTP 服务器集成

请求要么作为 WebSocket 处理，要么作为 HTTP 请求处理。这在 `getWSApp()` 中决定，它返回一个应用逻辑函数或 null。

```javascript
type WSApplication = (ws: WSServer) => Promise<void>;
// 将请求映射到 WS 应用。
function getWSApp(req: HTTPReq): null|WSApplication
```

WebSockets 的处理方式不同：

- 请求由 `handleWS()` 处理，它调用应用函数。
- socket 的其余部分数据将传递给协议，而不通过 `readerFromEOF()` 函数进行进一步处理。
- 响应直接写入 socket。因此，不要用响应压缩、额外的标头字段和分块编码来搞乱它。

```javascript
// 处理消息并发送响应
let reqBody: BodyReader;
let res: HTTPRes;
const wsapp: null|WSApplication = getWSApp(msg);
```

[报告错误 | 提问](https://forms.gle/UKo4bncUnuMGBrTM7) @ [build-your-own.org](https://build-your-own.org)

123

2024-02-02

# 13. WebSocket 与并发

```javascript
if (wsapp) {
  // 升级到 WebSocket
  reqBody = readerFromEOF(conn, buf);
  res = handleWS(msg, reqBody, wsapp);
} else {
  // 普通 HTTP 连接
  reqBody = readerReq(conn, buf, msg);
  res = handleReq(msg, reqBody);
}
try {
  if (!wsapp) {
    enableCompression(msg, res);
  }
  if (msg.method !== 'HEAD') {
    // 省略主体
    await writeHTTPBody(conn, res);
  }
} finally {
  // 清理
  await res.body?.close();
}
if (msg.version === '1.0' || wsapp) {
  // 关闭 HTTP/1.0 或 WebSocket 的连接
  return;
}
```

`handleWS()` 函数将这一切整合在一起：

- 启动任务处理协议。
- 启动应用任务。
- 返回 Upgrade 标头。

```javascript
async function handleWS(
  req: HTTPReq, reqBody: BodyReader, app: WSApplication): Promise<HTTPRes>
{
  // 处理 WS 协议
  const [ws, res]: [WSServer, BodyReader] = createWSServer(req);
  // 启动应用
  await app(ws).catch(console.error);
  // 切换协议
  return {
    code: 101,
    headers: [
      Buffer.from('Upgrade: websocket'),
      Buffer.from('Connection: Upgrade'),
      Buffer.from(`Sec-WebSocket-Accept: ${key}`),
    ],
    body: resBody,
  };
}
```

## 第 8 步：测试与调试

使用浏览器创建 WebSocket。记得使用数据抓包工具。Wireshark 可以拆解帧，所以你可以

- 学习帧的正确格式。
- 查看你生成的帧存在什么问题。

## 13.6 讨论：浏览器中的 WebSocket

WebSocket 在客户端和服务器的功能上是对称的。因此应用接口 适用于双方。让我们探讨浏览器中的 WebSocket。

### 浏览器中没有背压

最重要的区别是浏览器 API 是基于回调的。浏览器调用事件[6](https://developer.mozilla.org/en-US/docs/Web/API/message_event) 当消息到达。这与 Node.JS 的 `net.Socket` 相似，只是它有 `pause()` 和 `resume()` 方法，因此接收端是可以背压的。

对于发送消息，`send()` 方法[7](https://developer.mozilla.org/en-US/docs/Web/API/send) 只是缓存数据且不返回内容。有一个 `bufferedAmount` 属性告知缓冲区大小，因此应用程序仍然可以控制背压。

存在另一种 API 设计[8](https://developer.chrome.com/docs/capabilities/web-apis/websocketstream) 使用 `async/await` 进行读写，这是我们采取的方向。

[6] https://developer.mozilla.org/en-US/docs/Web/API/message_event

[7] https://developer.mozilla.org/en-US/docs/Web/API/send

[8] https://developer.chrome.com/docs/capabilities/web-apis/websocketstream

125

2024-02-02

# 13. WebSocket 与并发

### 应用层背压

缺少背压可能是网络编程中的第二大错误。但即使浏览器中无法实现背压，应用程序也可以在更高层实现：

- 消费者向生产者确认已处理的消息。
- 生产者根据确认信息来实现流量控制。

运行在 WebSocket 之上的消息协议可以实现背压，例如 [RSocket[9](https://rsocket.io/about/protocol#flow-control)].](#index_split_001.html#p131)

### 消息大小限制

虽然可以通过分帧将 WebSocket 消息视为无限流，但大多数软件（包括浏览器）将消息存储在单个缓冲区。因此消息大小和帧大小都有限制。（我们没有这些限制，因为我们使用 `read()` 函数即时消费数据）。

在 WebSocket 上发送大块数据的应用程序应该有一个分片机制，以保持较小的消息。

## 13.7 结论：我们学到了什么

自基础 HTTP 服务器以来重要的主题：

- HTTP 语义：
  - Content-Length 与分块传输编码。
  - 范围请求（Range requests）。
  - 缓存。
  - 压缩。
  - 基于所有权的手动资源管理。
  - Buffer 使用技巧。
  - 生产者-消费者问题和背压的抽象：
    - 生成器（Generators）。
    - 流（Streams）。
    - 阻塞队列（Blocking queues）。

[`rsocket.io/about/protocol#flow-control`](https://rsocket.io/about/protocol#flow-control)

[报告错误 | 提问](https://forms.gle/UKo4bncUnuMGBrTM7) @ [build-your-own.org](https://build-your-own.org)

126

2024-02-02

# 13. WebSocket 与并发

表 1：生产者-消费者问题的解决方案。

| | 阻塞队列 | Stream API | 异步生成器 |
| :--- | :--- | :--- | :--- |
| **生产者** | `await q.pushBack(x)` | `this.push(x)` | `yield x;` |
| **消费者** | `await q.popFront()` | `'data' event` | `await g.next()` |
| **多生产者** | 是 | 是 | 否 |
| **背压** | 自动 | 手动 | 自动 |

[报告错误 | 提问](https://forms.gle/UKo4bncUnuMGBrTM7) @ [build-your-own.org](https://build-your-own.org)

127

# 文档目录

- [封面]
- [目录]
- [01. 引言]
  - [1.1 为什么要编写 Web 服务器?]
    - 网络编程
    - 协议与通信
    - 深入理解 HTTP
  - [1.2 从零开始构建你的 X]
  - [1.3 本书]
    - 以项目为中心
    - 章节末尾
    - Node.js 和 TypeScript
    - 系列书籍
- [02. HTTP 概览]
  - [2.1 概述]
  - [2.2 示例说明 HTTP]
  - [2.3 HTTP 的演进]
    - HTTP/1.0：原型
    - HTTP/1.1：生产就绪且易于理解
    - HTTP/2：新功能
    - HTTP/3：更大的雄心
  - [2.4 命令行工具]
- [03. 编写一个 TCP 服务器]
  - [3.1 TCP 快速回顾]
    - 协议分层
    - TCP 字节流 vs 数据包
    - 字节流 vs 数据包：以 DNS 为例
    - TCP 通过握手开始
    - TCP 是双向全双工的
    - TCP 通过两次握手结束
  - [3.2 Socket 原始语]
    - 通过不透明句柄应用 Socket
    - 监听 Socket (Listening Socket) 与连接 Socket (Connection Socket)
    - 传输结束
    - Socket 原始语列表
  - [3.3 Node.js 中的 Socket API]
    - 步骤 1：创建一个监听 Socket
    - 步骤 2：接受新连接
    - 步骤 3：错误处理
    - 步骤 4：读与写
    - 步骤 5：关闭连接
    - 步骤 6：测试它
  - [3.4 讨论：半开连接]
  - [3.5 讨论：事件循环与并发]
    - JS 代码在事件循环中运行
    - JS 代码与运行时共享单个操作系统线程
    - Node.JS 中的并发是基于事件的
  - [3.6 讨论：异步 vs. 同步]
    - 阻塞与非阻塞 IO
    - Node.js 中的 IO 是异步的
    - 网络编程之外的事件驱动编程
  - [3.7 讨论：基于 Promise 的 IO]
- [04. Promise 与事件]
  - [4.1 async 和 await 简介]
    - 使用回调函数
    - 使用 Promise 和 await
    - 创建 Promise
  - [4.2 理解 async 和 await]
    - 普通函数通过 `return` 将控制权交给运行时
    - async 函数通过 `await` 将控制权交给运行时
    - 调用 async 函数启动新任务
  - [4.3 从事件到 Promise]
    - 步骤 1：分析解决方案
    - 步骤 2：处理 'data' 事件
    - 步骤 3：处理 'end' 和 'error' 事件
    - 步骤 4：写入 Socket
  - [4.4 使用 async 和 await]
  - [4.5 讨论：背压]
    - 等待 Socket 写入完成
    - 生产者被消费者限制颈
    - TCP 中的背压：流量控制
    - 应用之间的背压
    - 无界队列是陷阱 (Footguns)
  - [4.6 讨论：事件与有序执行]
  - [4.7 结论：Promise vs. 回调]
- [05. 一个简单的网络协议]
  - [5.1 消息回显服务器]
  - [5.2 动态 Buffer]
    - 动态缓冲区的需求
    - 编写动态 Buffer
  - [5.3 实现消息协议]
    - 步骤 1：服务器循环
    - 步骤 2：拆分消息
    - 步骤 3：处理请求
  - [5.4 讨论：流水线请求 (Pipelined Requests)]
    - 通过流水线请求减少延迟
    - 支持流水线请求
    - 流水线导致的死锁
  - [5.5 讨论：更智能的 Buffer]
    - 从头部移除数据
    - 使用固定大小 Buffer 而无需重新分配
  - [5.6 结论：网络编程基础]
- [06. HTTP 语义与语法]
  - [6.1 高层结构]
  - [6.2 Content-Length]
    - HTTP Header 的长度
    - HTTP Body 的长度
  - [6.3 分块传输编码]
    - 随地生成并发送数据
    - 协议的另一层
  - [6.4 HTTP 中的歧义]
    - 消息体长度的理想情况
    - 注意异常情况
  - [6.5 HTTP 消息格式]
    - 学习 BNF 语言
    - HTTP 头部字段
  - [6.6 常见头部字段]
  - [6.7 HTTP 方法]
    - 只读方法
    - 可缓存性
    - CRUD 与资源
    - 等幂性
    - HTTP 方法对比
  - [6.8 讨论：文本 vs. 二进制]
    - 文本通常具有歧义性
    - 文本处理更容易且容易出错
  - [6.9 讨论：分隔符]
    - 分隔符数据中的序列化错误
    - 二进制协议中的长度前缀数据
- [07. 代码：一个基础 HTTP 服务器]
  - [7.1 开始编码]
    - 步骤 1：类型与结构
    - 步骤 2：服务器循环
    - 步骤 3：拆分头部
    - 步骤 4：解析头部
    - 步骤 5：读取正体
    - 步骤 6：请求处理器
    - 步骤 7：发送响应
    - 步骤 8：回顾服务器循环
  - [7.2 测试]
    - 大尺寸 HTTP 消息
    - 连接复用与管道化
  - [7.3 讨论：Nagle 算法]
    - 优化：合并小规模写入
    - 过早优化
    - 人在实践中的实际做法
  - [7.4 讨论：缓冲写入器]
    - 替代方案：让缓冲变为半透明
    - 替代方案：添加缓冲封装
- [08. 动态内容与流式传输]
  - [8.1 分块传输编码]
    - 分块消息格式
    - 冷门的 HTTP 特性
  - [8.2 生成分块响应]
  - [8.3 JS 生成器]
    - 生产者、消费者与队列
    - 作为生产者的 JS 生成器
    - 从 JS 生成器消费数据
  - [8.4 读取分块请求]
    - 作为生产者的解析器
    - 解码格式
    - 分块编码产生字节流
  - [8.5 讨论：使用数据包捕获调试]
    - 使用 `tcpdump` 捕获并检查数据
    - 使用 `Wireshark` 分析数据包
    - 使用 `ngrep` 搜索数据包
  - [8.6 讨论：WebSocket]
    - 轮询更新
    - 实时推送
    - WebSocket 是基于消息的
    - WebSocket 不是请求-响应模式
- [09. 文件 IO 与资源管理]
  - [9.1 `Node.JS` 中的文件 IO]
  - [9.2 提供文件服务]
    - 步骤 0：为静态文件添加处理器
    - 步骤 1：打开与关闭文件
    - 步骤 2：`stat()` 文件



# 9.3 讨论：手动资源管理

## 资源由某些对象所有

## 资源由函数或作用域所有

## 所有权可以转移

## 所有者是链式结构

## 如何在生成器中进行清理

# 9.4 讨论：复用缓冲区

## 缓冲区分配存在成本

## 使用未初始化的缓冲区

## 复用大缓冲区

## 池化缓冲区

## 复用缓冲区时注意生命周期

# 10. 范围请求

## 10.1 范围请求的工作原理

### `Range` 头部字段语法

### 有效范围及示例

### 范围请求是可选的

### 206 表示范围响应

### `Content-Range` 返回有效范围

### 宣告支持 `Range`

### 使用 `HEAD` 方法进行探测

### 使用多部分消息处理多个范围

### 讨论：多部分消息在技术上有必要吗？

### 客户端可能的场景

## 10.2 实现范围请求

### 步骤 1：解析 `Range` 头部字段

### 步骤 2：读取文件部分

### 步骤 3：生成范围响应

### 步骤 4：添加 `HEAD` 方法

# 11. HTTP 缓存

## 11.1 缓存校验器

### 通过时间验证

### 通过 `ETag` 验证

### 针对范围请求验证

### 校验头部总结

### 实现时间验证器

## 11.2 讨论：服务端缓存控制

### 何时重新验证缓存

### 控制 TTL（生存时间）

### 让客户端始终检查服务器

### 防止缓存

### 减少有效验证

### 启发式缓存

### 非客户端缓存

## 共享与私有缓存

## 云端缓存

# 12. 压缩与 Stream API

## 12.1 HTTP 压缩的工作原理

- 通过 `Accept-Encoding` 进行协商
- 使用 `Content-Encoding` 压缩
- 压缩与 `Content-Length`
- 压缩与缓存
- 压缩上传
- 压缩与 Range 请求
- 使用 `Transfer-Encoding` 压缩

## 12.2 使用 Pipes 进行数据处理

- 数据处理与 IO
- Unix Pipes 用于组合的数据处理器
- 抽象 Pipes

## 12.3 在 Node.JS 中探索 Stream API

- Stream 接口列表
- 在 Stream 接口上使用 Pipes

## 12.4 实现 HTTP 压缩

- 第 1 步：检查头部字段并启用压缩
- 第 2 步：理解不使用 Pipes 的陷阱
- 第 3 步：实现 `stream.Readable`
- 第 4 步：创建一个 Pipe
- 第 5 步：从 `stream.Readable` 中读取数据
- 第 6 步：进行测试
- 第 7 步：刷新压缩器缓冲区

## 12.5 讨论：重构为 Stream

## 12.6 讨论：高水位

- 单队列
- 基于高水位的背压
- 使用队列进行批处理
- Node.JS 中的高水位

# 13. WebSocket 与并发

## 13.1 建立 WebSocket

### 概述

### 从 HTTP 升级

### 握手

### 头部字段

## 13.2 WebSocket 协议

### 帧格式

### 帧类型

### 分段消息

## 13.3 并发编程简介

### 竞态条件

### 原子操作

### 使用互斥锁互斥

### 使用队列多复用

### 使用队列流控

### 使用队列实现取消

### 阻塞队列作为同步原语

## 13.4 编写阻塞队列

### 第 1 步：分析问题

### 第 2 步：推送与弹出

### 第 3 步：关闭队列

### 第 4 步：添加缓冲区

## 13.5 WebSocket 服务器

### 第 1 步：设计消息接口

### 第 2 步：设计服务器应用接口

### 第 3 步：设计服务器任务

### 第 4 步：启动服务器任务

### 第 5 步：向 Socket 消息

### 第 6 步：从 Socket 解析帧

### 第 7 步：与 HTTP 服务器集成

### 第 8 步：测试与调试

## 13.6 讨论：浏览器中的 WebSocket

### 浏览器中的 WebSocket 没有背压

### 应用层背压

### 消息大小限制

## 13.7 结论：我们学到了什么
