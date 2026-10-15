
# **Tampering with a Client’s DNS Settings**

根据操作系统的不同，针对目标的 DNS 设置进行篡改的方法也有几种不同的实现方式。`Windows` 在现代 Windows 系统中，你可以通过将任意 DNS 条目添加到 `C:\Windows\System32\drivers\etc\hosts` 文件来插入自定义 DNS 记录。大多数情况下，需要管理员权限来更新该文件。条目格式为：`<IP 地址> <DNS 名称>`。例如，要让目标在尝试加载 Google 时被引导到你的服务器，只需在该文件中添加：

``` 
<你的 IP 地址> www.google.com
```

除了向本地 hosts 文件中插入任意记录外，还可以通过命令行更新特定网络接口的 Windows DNS 设置。你可以在受害机器上通过编写一个简单的批处理文件，或编译一个小程序来执行此操作。

``` 
netsh interface ip set dns name="Local Area Connection"\
 source=static addr=<你的恶意 DNS 服务器 IP>
```

可以将其简化为：

``` 
netsh interface ip set dns "Local Area Connection" static <IP>
```

`Linux/Unix/OS X` Linux、UNIX 和 OS X 系统将 hosts 文件存放在 `/etc/hosts`。该文件的格式与 Windows 类似，并且需要 root 权限即可更新。这些操作系统的 DNS 设置始终依赖于 `/etc/resolv.conf` 文件。拥有正确权限时，可以通过以下方式更新该文件：

``` 
echo "nameserver <你的恶意 DNS 服务器 IP>" > /etc/resolv.conf
```

* * *

# **从本地网络层面影响 DNS**

利用 ARP 中毒攻击，如上文所述，你可以在本地网络中将自己的机器伪装成 DNS 服务器。

Ettercap 提供一个名为 DNSSpoof 的模块，可自动执行此类攻击。首先，修改 `etter.dns` 文件以包含你的恶意 DNS 条目。在 Linux 系统上该文件通常位于 `/usr/share/ettercap/etter.dns`，而在 OSX 上则一般位于 `/opt/local/share/ettercap/etter.dns`。执行攻击时，你需要像之前一样运行 ettercap，但需指定插件：

``` 
ettercap -T -Q -P dns_spoof -M arp:remote \
 -i <网络接口> /<要中毒的目标 IP> //
```

在上述所有示例中，一旦你控制了目标机器或网络的 DNS，就可以冒充任何试图通过名称访问的计算机或服务器。为了利用这种中间人（MitM）技术注入你的初始代码，建议先监控正常的网页流量，看是否存在代理服务器。若存在，代理是理想的目标，因为本地浏览器的流量本身就会指向该服务器。

## **利用缓存**

Robert Hansen 发现浏览器在缓存非公共可路由 IP 地址（即 `10.0.0.0/8`、`172.16.0.0/12` 和 `192.168.0.0/16` 范围）时存在安全漏洞。Hansen 表明，在特定条件下，可以在源站中植入恶意逻辑。

随后，当目标在使用相同非可路由地址的网络中访问时，此攻击可让你在不破坏同源策略（SOP）的前提下访问内部服务器。

例如，目标可能在一家网络咖啡馆使用服务，而你同样拥有该网络的访问权限。利用 ARP 中继技术，你可以在网络中篡改所有 HTTP 请求（如前文所述）。你提前部署了一个 BeEF 服务器位于互联网上：

**Level1 1.** 中继攻击进行期间，等待目标发出任意 HTTP 请求。随后，在响应中插入多个 `<iframe>`，加载你控制的每个目标 IP 的内容。  
**2.** 返回你精心构造的数据，使其在浏览器中被缓存。每个 `<iframe>` 都包含指向你的 BeEF 服务器的初始化指令。  
**3.** 当目标离开公共网络并重新连接到办公室或家庭网络时，浏览器仍会继续向 BeEF 服务器轮询。  
**4.** 若目标随后访问私有 IP 地址（如其路由器的管理页面），之前缓存的内容将在该来源下执行。

/Level1

在特定的 VPN 条件下也可利用这些情况，但上述场景更为常见。之所以可能，是因为 JavaScript 在浏览器内部执行后，可能超出浏览器缓存，甚至在某些情况下影响 DNS 缓存。

本节展示了无需发现 Web 应用漏洞，即可在浏览器中执行恶意代码的可能性。有时，仅仅拥有网络访问权限就足以将初始指令注入目标浏览器。

# **总结**

本章重点介绍了在利用浏览器信任时所面临的第一道障碍。我们尽力涵盖了恶意代码进入浏览器的多种方式，但这些方法并非 exhaustive。随着浏览器技术的不断演进，攻击面也会随之起伏——快速扩张的互联网、推动所有事物上线的趋势等因素都会影响其规模。

你学习了各种方法，每一种都旨在展示实现目标的主要技术与技巧。一旦这些“闸门”打开，你可能会惊讶于浏览器愿意向你提供多少信息。

当然，执行初始指令只是两个主要障碍中的第一个。你的下一个挑战是建立持久的浏览器通信通道。这将是你接下来的浏览器黑客之旅的下一步，将在下一章中进一步探讨。

# **问题**

Level1 **1.** 攻击者若成功在浏览器中执行代码，可能会执行哪些操作？  
**2.** 请描述 XSS 攻击与常规 XSS 的主要区别。  
**3.** 哪种浏览器控制可阻止 XSS 执行？  
**4.** 请指出一个著名的 XSS “病毒”，并说明其传播方式。  
**5.** 请描述一种攻击者可以入侵网站并植入恶意代码的方法。  
**6.** 在什么情况下可以使用 sslstrip？  
**7.** 请描述 ARP 中毒（ARP spoofing）。  
**8.** 网络钓鱼（phishing）与垃圾邮件（SPAM）有何区别？  
**9.** 请用简要步骤说明如何进行社会工程攻击。  
**10.** 请描述一种物理“诱饵”技术。

/Level1

答案请参考书籍网站 [https://browserhacker.com/answers](https://browserhacker.com/answers) 或维基网站 [www.wiley.com/go/browserhackershandbook](http://www.wiley.com/go/browserhackershandbook)

**Notes**

1\. Netscape. (1995). Netscape and Sun announce JavaScript for enterprise networks and the Internet. Retrieved February 23, 2013 from [http://web.archive.org/web/20070916144913/http://wp.netscape.com/newsref/pr/newsrelease67.html](http://web.archive.org/web/20070916144913/http://wp.netscape.com/newsref/pr/newsrelease67.html)

2\. Carnegie Mellon University. (2000). CERT® Advisory CA-2000-02 Malicious HTML Tags Embedded in Client Web Requests. Retrieved February 23, 2013 from [http://www.cert.org/advisories/CA-2000-02.html](http://www.cert.org/advisories/CA-2000-02.html)

3\. Jeremiah Grossman. (2006). The origins of Cross-Site Scripting (XSS). Retrieved February 23, 2013 from [http://jeremiahgrossman.blogspot.com.au/2006/07/origins-of-cross-site-scripting-xss.html](http://jeremiahgrossman.blogspot.com.au/2006/07/origins-of-cross-site-scripting-xss.html)

