
```
PS C:\Users\Ric Messier> ipconfig /displaydns
 
Windows IP Configuration
 
vortex.data.microsoft.com
----------------------------------------
Record Name . . . . . : vortex.data.microsoft.com
Record Type . . . . . : 5
Time To Live  . . . . : 24
Data Length . . . . . : 8
Section . . . . . . . : Answer
CNAME Record  . . . . : asimov.vortex.data.trafficmanager.net
 
 
Record Name . . . . . : asimov.vortex.data.trafficmanager.net
Record Type . . . . . : 1
Time To Live  . . . . : 24
Data Length . . . . . : 4
Section . . . . . . . : Answer
A (Host) Record . . . : 64.4.54.254
 
 
array511.prod.do.dsp.mp.microsoft.com
----------------------------------------
Record Name . . . . . : array511.prod.do.dsp.mp.microsoft.com
Record Type . . . . . : 1
Time To Live  . . . . : 1489
Data Length . . . . . : 4
Section . . . . . . . : Answer
A (Host) Record . . . : 52.184.213.21
 
1.0.0.127.in-addr.arpa
----------------------------------------
Record Name . . . . . : 1.0.0.127.in-addr.arpa.
Record Type . . . . . : 12
Time To Live  . . . . : 541542
Data Length . . . . . : 8
Section . . . . . . . : Answer
PTR Record  . . . . . : kubernetes.docker.internal
 
 
download.visualstudio.microsoft.com
----------------------------------------
Record Name . . . . . : download.visualstudio.microsoft.com
Record Type . . . . . : 5
Time To Live  . . . . : 33
Data Length . . . . . : 8
Section . . . . . . . : Answer
CNAME Record  . . . . : 2-01-5830-0005.cdx.cedexis.net
 
 
Record Name . . . . . : 2-01-5830-0005.cdx.cedexis.net
Record Type . . . . . : 5
Time To Live  . . . . : 33
Data Length . . . . . : 8
Section . . . . . . . : Answer
CNAME Record  . . . . : 4316b.wpc.azureedge.net
 
 
Record Name . . . . . : 4316b.wpc.azureedge.net
Record Type . . . . . : 5
Time To Live  . . . . : 33
Data Length . . . . . : 8
Section . . . . . . . : Answer
CNAME Record  . . . . : cs10.wpc.v0cdn.net
 
 
Record Name . . . . . : cs10.wpc.v0cdn.net
Record Type . . . . . : 28
Time To Live  . . . . : 33
Data Length . . . . . : 16
Section . . . . . . . : Answer
AAAA Record . . . . . : 2606:2800:11f:7de:d31:7db:168f:1225
 
array513.prod.do.dsp.mp.microsoft.com
----------------------------------------
Record Name . . . . . : array513.prod.do.dsp.mp.microsoft.com
Record Type . . . . . : 1
Time To Live  . . . . : 1202
Data Length . . . . . : 4
Section . . . . . . . : Answer
A (Host) Record . . . : 52.184.214.53
```

在实践中，侦察分为两个不同的阶段。虽然在发动攻击时会大量关注信息收集，但获取利用后也会进行大量侦察。你可以从外部以及内部进行侦察。一旦你进入内部网络，某些侦察工作会变得更容易，或者至少我们会打开其他侦察途径。利用本地系统中缓存的 DNS 条目的技术被称为 `passive` DNS 侦察。

每次在某些系统上执行 DNS 查找时，结果会被本地缓存。这种缓存可以避免下次访问相同主机时再发送网络请求。条目的存活时间（TTL）由 DNS 条目中的生存期（time‑to‑live）字段决定，该字段从权威记录（SOA）开始。SOA 记录指示域记录本身的过期时间，告诉任何查询该域的人何时需要再次检查权威域名服务器。每个域都有关联的 NS 记录，指明需要询问哪些服务器以获取该域的答案。除非记录已在本地缓存（无论是客户端本身还是客户端询问的本地缓存服务器），否则应始终向这些权威服务器查询。

除了 SOA 记录提供的域级超时长度外，DNS 中每条单独记录都可以拥有自己的生存期（TTL）值。该值表明系统可以缓存结果的时间，然后需要再次向权威 DNS 服务器查询以确认值未变。根据 DNS 规范，不必等到条目生命周期结束才刷新缓存，而是使用小于完整 TTL 的值。TTL 仍然指导本地缓存中保留值的时长。

Windows 系统会缓存这些值，并且可以导出缓存内容，如下面的片段所示。要在 Windows 系统上导出缓存，可使用命令行工具，例如传统的命令行或基于 PowerShell 的命令 `ipconfig /displaydns`。

```
PS C:\Users\Ric Messier> ipconfig /displaydns
 
Windows IP Configuration
 
vortex.data.microsoft.com
----------------------------------------
Record Name . . . . . : vortex.data.microsoft.com
Record Type . . . . . : 5
Time To Live  . . . . : 24
Data Length . . . . . : 8
Section . . . . . . . : Answer
CNAME Record  . . . . : asimov.vortex.data.trafficmanager.net
 
 
Record Name . . . . . : asimov.vortex.data.trafficmanager.net
Record Type . . . . . : 1
Time To Live  . . . . : 24
Data Length . . . . . : 4
Section . . . . . . . : Answer
A (Host) Record . . . : 64.4.54.254
 
 
array511.prod.do.dsp.mp.microsoft.com
----------------------------------------
Record Name . . . . . : array511.prod.do.dsp.mp.microsoft.com
Record Type . . . . . : 1
Time To Live  . . . . : 1489
Data Length . . . . . : 4
Section . . . . . . . : Answer
A (Host) Record . . . : 52.184.213.21
 
1.0.0.127.in-addr.arpa
----------------------------------------
Record Name . . . . . : 1.0.0.127.in-addr.arpa.
Record Type . . . . . : 12
Time To Live  . . . . : 541542
Data Length . . . . . : 8
Section . . . . . . . : Answer
PTR Record  . . . . . : kubernetes.docker.internal
 
 
download.visualstudio.microsoft.com
----------------------------------------
Record Name . . . . . : download.visualstudio.microsoft.com
Record Type . . . . . : 5
Time To Live  . . . . : 33
Data Length . . . . . : 8
Section . . . . . . . : Answer
CNAME Record  . . . . : 2-01-5830-0005.cdx.cedexis.net
 
 
Record Name . . . . . : 2-01-5830-0005.cdx.cedexis.net
Record Type . . . . . : 5
Time To Live  . . . . : 33
Data Length . . . . . : 8
Section . . . . . . . : Answer
CNAME Record  . . . . : 4316b.wpc.azureedge.net
 
 
Record Name . . . . . : 4316b.wpc.azureedge.net
Record Type . . . . . : 5
Time To Live  . . . . : 33
Data Length . . . . . : 8
Section . . . . . . . : Answer
CNAME Record  . . . . : cs10.wpc.v0cdn.net
 
 
Record Name . . . . . : cs10.wpc.v0cdn.net
Record Type . . . . . : 28
Time To Live  . . . . : 33
Data Length . . . . . : 16
Section . . . . . . . : Answer
AAAA Record . . . . . : 2606:2800:11f:7de:d31:7db:168f:1225
 
array513.prod.do.dsp.mp.microsoft.com
----------------------------------------
Record Name . . . . . : array513.prod.do.dsp.mp.microsoft.com
Record Type . . . . . : 1
Time To Live  . . . . : 1202
Data Length . . . . . : 4
Section . . . . . . . : Answer
A (Host) Record . . . : 52.184.214.53
```

在实践中，外部侦察这种技术可能用处不大。一旦你获得内部网络的访问权限，你就想了解所有系统和 IP 地址。从外部，你可以查询公开来源获取组织可能拥有的地址块信息。而在内部，它们通常使用私有地址，公开记录中很少有关于这些地址块的信息，除非你偶然获得网络管理系统的访问权限，该系统记录所有地址块。相反，你可以在你拥有访问权限的系统上导出 DNS 缓存。导出的内容不仅包含主机名，还包含这些主机名对应的 IP 地址。如果缓存中出现大量公司域名的条目，你很可能正在查看内部 DNS 记录。另一种表明你拥有内部地址的线索是看到以 `.local` 结尾的条目，这是一个不能在 Internet 上使用的顶级域，常被用作内部 DNS 实现的顶级域（即完全限定域名的最后部分，包含主机名和域名）。

公司常用的 `split DNS` 实现将外部 DNS 与内部 DNS 分开。外部 DNS 通常只包含向外部世界提供 essential 服务的系统的完整限定域名（FQDN）。在外部 DNS 之上，往往还有一个内部 DNS，所有内部系统在此登记，以便使用 FQDN 而非 IP 地址进行访问。你的企业网络中的系统可能会向 DNS 服务器注册，这样其他人只需使用你的 FQDN 即可解析到你的 IP 地址。

被动侦察能够收集大量信息。例如，监控网络头部（从层 3 到应用层）可以发现有趣的信息。虽然手动捕获数据包并逐一分析头部会很费时，但有一个程序能够自动完成大部分工作。该程序是 `p0f`，它会监听网络流量并随通信经过的接口进行观察。遗憾的是，`p0f` 的用途已经大幅下降。原因并非 `p0f` 本身，而是大多数 Web 服务器默认加密流量，导致 `p0f` 无法查看 HTTP 头部，也就无法识别服务器及其他有价值信息。下面展示了 `p0f` 的一些输出示例。

```
.-[ 192.168.86.45/46112 -> 8.43.72.22/443 (syn) ]-

 |

 | client   = `192.168.86.45/46112`

 | os       = `Linux 3.11 and newer`

 | dist     = `0`

 | params   = `none`

 | raw_sig  = `4:64+0:0:1460:mss*20,7:mss,sok,ts,nop,ws:df,id+:0`

 |

 `----

 .-[ 192.168.86.45/46112 -> 8.43.72.22/443 (mtu) ]-

 |

 | client   = `192.168.86.45/46112`

 | link     = `Ethernet or modem`

 | raw_mtu  = `1500`

 |

 `----

 .-[ 192.168.86.45/46112 -> 8.43.72.22/443 (uptime) ]-

 |

 | client   = `192.168.86.45/46112`

 | uptime   = `48 days 7 hrs 54 min (modulo 49 days)`

 | raw_freq = `1000.00 Hz`

 |

 `----

 .-[ 192.168.86.45/33498 -> 52.94.210.45/443 (syn) ]-

 |

 | client   = `192.168.86.45/33498`

 | os       = `Linux 3.11 and newer`

 | dist     = `0`

 | params   = `none`

 | raw_sig  = `4:64+0:0:1460:mss*20,7:mss,sok,ts,nop,ws:df,id+:0`

 |

 `----

 .-[ 192.168.86.45/33498 -> 52.94.210.45/443 (host change) ]-

 |

 | client   = `192.168.86.45/33498`

 | reason   = `tstamp port`

 | raw_hits = `0,1,1,1`

 |

 `----
```
