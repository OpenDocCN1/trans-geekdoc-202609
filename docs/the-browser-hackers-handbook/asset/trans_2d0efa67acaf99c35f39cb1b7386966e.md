
-   [如图 10-18 所示]，结果是一张使用 Courier 字体打印的包含 “Demonstrating IPEC” 内容的页面，位于左下角坐标 72 和 500 处。请注意，PostScript 文件的默认坐标是以 1/72 英寸为单位的。

 start figure 

[**Figure 10-18:**](#c10.html#figureanchor10-18) IPEC 打印带格式的 PostScript 页面的结果

![c10f018.tif](image_fi/662090c10/c10f018.png)

 end figure 

#### IMAP 协议通信示例

IMAP 协议，特别是第 3 版和第 4 版，是一个可以实现 IPC（协议间通信）的协议的良好示例。虽然协议本身是一个很好的候选者，但其在现实中的适用性受到现代浏览器因端口禁用实施而限制直接访问 TCP 端口 143 的可能性。

在某些情况下，情况可能不同，例如 IMAP 版本 3 在 TCP 端口 220 上运行。此外，一些网络管理员会将服务移动到非标准端口，以隐藏其用途。这可能会通过非禁用的端口提供访问。

无论哪种情况，IMAP 都是一个很好的例子，用于说明浏览器中的攻击。由于其高度教育价值，你在本章中会在多个地方看到它的使用。

为了演示如何在 Firefox 中绕过端口禁用，最简单的方法是向 pref.js 扩展文件中添加以下行：

```
pref("network.security.ports.banned.override", "143");
```

完成后请勿忘记将其删除。正如你稍后将了解到，这个端口被禁用的原因是有充分理由的。

IMAP 实现之所以可以在浏览器中进行 IPC，是因为这些服务通常同时满足 IPC 条件。下面的示例代码尝试向 IMAP 服务器进行认证，然后退出：

```
var server = '172.16.37.151';
var port = '143';
var commands = 'a01 login root password\na002 logout';

var target = "http://" + server + ":" + port + "/abc.html";
var iframe = beef.dom.createInvisibleIframe();

var form = document.createElement('form');
form.setAttribute('name', 'data');
form.setAttribute('action', target);
form.setAttribute('method', 'post');
form.setAttribute('enctype', 'text/plain');

var input = document.createElement('input');
input.setAttribute('id', 'data1')
input.setAttribute('name', 'data1')
input.setAttribute('type', 'hidden');
input.setAttribute('value', commands);
form.appendChild(input);

iframe.contentWindow.document.body.appendChild(form);
form.submit();
```

本例中使用的 IMAP 服务器是 Eudora，后文将用于演示协议间利用。如图 10-19 所示，当 IMAP 服务器收到 POST 请求时，HTTP 头部会被解析为无效命令（“不 recognized 或在当前状态下不合法”）。POST 主体中的 IMAP 命令被正确解析。在此示例中，认证尝试失败是因为我们不知道正确的凭据。

 start figure 

[**Figure 10-19:**](#c10.html#figureanchor10-19) IPC 导致的 IMAP 服务器日志

![c10f019.eps](image_fi/662090c10/c10f019.png)

 end figure 

你可以在图 10-19 中看到，IMAP 服务器返回 “incorrect password”。在成功登录后，会返回不同的结果，需要加以区分。

一些 IMAP 服务器支持发送电子邮件，这可以用于创建侧信道。根据前文在非 HTTP 服务指纹识别部分的介绍， timing differences 也可以被利用，具体取决于实现。一旦登录，查看 Inbox 的内容通常比未认证的连接错误耗时更长。

前文列出的协议并非 IPC 兼容目标的完整列表。任何满足 IPC 条件（容错性和数据封装）的其他协议实现，都可能通过 IPC 进行交互。下次你在渗透测试中遇到新的潜在 IPC 目标时，请记住这些依赖关系。

### 实现协议间利用

前文讨论了协议间通信，但 Wade Alcorn 的研究并未在此停止。Alcorn 在 2007 年的研究论文中展示了 IPC 技术可以扩展到不仅实现通信，还能实现利用，从而得到协议间利用（Inter-protocol Exploitation，IPE）。这里讨论的某些主题涉及较低层的应用利用。如果你需要更多信息，请不要忘记查阅 The Shellcoder Hacker’s Handbook 2nd Edition。

如果你能够通过 HTTP 与非 HTTP 协议进行通信（如前一节所示），你发送的数据也可以包含 Shellcode。类似于 IPC，IPE 也依赖于容错性和数据封装。

让我们扩展之前用于讨论 IPC 的初始示例。假设一个服务寻找类似以下命令：

```
WRITE <content> <file_path>
```

假设处理 <file_path> 的代码因为未对 <content> 的长度进行检查，而使用 memcpy 将其复制到 1024 字节的缓冲区，导致缓冲区溢出。如果你在查找应用漏洞，可能会尝试对输入进行模糊测试，试图触发崩溃条件。当然，这个虚构的例子会崩溃。

当提交文件路径为 1500 字节的 WRITE 命令时，分析得到的段错误数据表明你可以控制 Extended Instruction Pointer（EIP），并且在内存中有 800 字节的空间用于放置 Shellcode。谁会想到？这个虚构的例子正好满足你对 IPE 的需求！

#### 计算 HTTP 头大小

当你发送包含 Shellcode 的 POST 请求时，往往需要非常精确。你需要指定返回地址应该指向的位置，以及需要多少个 NOP（以及其他垃圾字节）。即使 1 字节的误差也可能导致你试图攻击的监听服务崩溃。这可能导致 Shellcode 未能按预期执行，从而失败。

正如你所学到的，HTTP 头部在目标协议中会被丢弃。但这并不意味着它们不会被解析并加载到你正在向其发送数据的进程的内存中。在某些情况下，这意味着必须计入头部的大小。

验证 HTTP 头部是否存储在内存的最简便方法是向想要分析的进程附加调试器。正如下文在 IMAP 利用示例中讨论的，Eudora WorldMail 版本 6.1.21（及更早版本）在解析 POST 主体内容之前，会先将 HTTP 头部存储在内存中。

此外，你无法事先确定在发送跨源 POST 请求时使用的 HTTP 头部的精确大小。每个浏览器都不同，往往包含不同的 HTTP 头部。你的 exploit 必须可靠，否则 Shellcode 将无法执行，服务可能崩溃。

那么，如何解决这个问题？一种方法是提前确定浏览器提交的跨源请求的头部精确大小。BeEF 通过在独特端口上绑定套接字来模拟跨源情况，向该服务器发送相同的跨源请求。到达套接字的原始 HTTP 请求内容用于计算头部的精确大小。被钩住的浏览器可以随后获取跨源请求长度的 JSON 对象结果。负责计算头部大小并随后将结果返回给被钩住浏览器的代码如下：

