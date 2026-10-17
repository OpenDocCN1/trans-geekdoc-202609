
Getting the output here, just as with any tool, is helpful, but at some point you need to do something with the information, not least putting it into a report for your client or employer. One nice thing about `nbtscan` is the ability to generate output that can be manipulated programmatically. This may include taking the output and putting it into a database. While you can certainly read in values with white‑space separators, `nbtscan` lets you specify a separator that may make it easier to read in the output, but you can also specify a comma as a separator and then open the output in a spreadsheet program. Adding `‑s` followed by whatever character you want to use as a separator will get you the same output as shown earlier, just with your specified separator included between the different fields.

You may start to see a bit of a pattern when it comes to enumeration and SMB. While there are a lot of tools available, they all perform the same functions, and the easiest thing to do when it comes to enumeration is to identify systems that use SMB, including the name they advertise on the network. One note about that name: it may not resolve to an IP address. A name announced using NetBIOS is intended to be used and resolved on the local network. This means it won't resolve using DNS unless DNS is configured to use the same names and IP addresses. It's possible to have one name for your Windows sharing and another one for your DNS, assuming the system even has a DNS address. If your enterprise network uses WINS, they will resolve to be the same because of how the local systems register to WINS.

Another tool, and we'll see the same capabilities with this one, is `enum4linux`. The following example is being run from a Kali Linux system where it is installed by default, but it's easy enough to get a copy of it. It's just a Perl script, so to run it, you need a Perl interpreter. The following example enumerates the shares on a specific host, identified by IP address. The target system is a Linux system running Samba to provide Windows networking functionality over SMB. In the output, you will find a lot of information related to how Samba is configured. As an example, we can see that the workgroup WORKGROUP is configured, which is a way of organizing systems on a local network that are all using Windows.

### enum4linux Share Enumeration

```
root@quiche:~# enum4linux  -S 192.168.86.52

Starting enum4linux v0.8.9 ( http://labs.portcullis.co.uk/application/enum4linux/ ) on Sun Jan 3 12:18:25 2021

==========================

|    Target Information    |

==========================

Target …….. 192.168.86.52

RID Range …….. 500-550,1000-1050

Username ……… ''

Password ……… ''

Known Usernames .. administrator, guest, krbtgt, domain admins, root, bin, none

[+] Got domain/workgroup name: WORKGROUP

===================================================

|    Session Check on 192.168.86.52    |

=====================================

[+] Server 192.168.86.52 allows sessions using username '', password ''

========================================

|    Getting domain SID for 192.168.86.52    |

=========================================

Domain Name: WASHERE

Domain Sid: (NULL SID)

[+] Can't determine if host is part of domain or part of a workgroup

========================================

|    Share Enumeration on 192.168.86.52    |

========================================

WARNING: The "syslog" option is deprecated

     Sharename       Type      Comment

     ---------       ----      -------

     homes           Disk      Home Directories

     print$          Disk      Printer Drivers

     IPC$            IPC       Service (bobbie server (Samba, Ubuntu))

 Reconnecting with SMB1 for workgroup listing.

     Server               Comment

     ---------            -------

     Workgroup            Master

     ---------            -------

     WORKGROUP            STEVEDALLAS

[+] Attempting to map shares on 192.168.86.52

```

At the bottom, you can see the different share names. This includes the `IPC$`, which is used for interprocess communication between hosts. This allows for management of systems remotely. Using `enum4linux`, we can finally see the master browser on the network. The system named `STEVEDALLAS` holds the current authoritative list of all the systems on the network. This is a system that has been elected by other systems on the network, which essentially means it has volunteered, and based on its characteristics, no one else has challenged it. The reason for `STEVEDALLAS` to be the master browser is it is one of only a couple of Windows systems, and of the two or three that were actual Windows systems and not Linux or macOS running SMB services, `STEVEDALLAS` has the most recent operating system.

Using SMB‑related utilities, we can gather a lot of information from the target network. As noted earlier, it's generally necessary to be on the local network to be able to use any of these tools. One reason for this can be the broadcast domain orientation of Windows networking—announcements on the local network. Another is that Windows networking ports are commonly blocked by firewalls. Also, it's entirely possible that desktop networks, where the systems are most likely to be communicating with SMB, often use private addresses that may not be exposed to the outside world. To get to them, because they are nonroutable by convention, you'd have to be on a network where there would at least be routing rules to get to those target networks, meaning there is network reachability.

-   [禁用 SMBv1] SMBv1 是一个较旧的协议，除非在非常特殊的情况下不需要它。它易受多种攻击，可能导致信息泄露。这很容易禁用，事实上，较新的 Windows 版本默认已禁用它。

-   `Enable Host‑Based Firewall` 使用分区可以在不受信任网络上保护单个系统。主机防火墙还可以设置规则，限制谁可以通过 SMB 与单个系统通信。大多数情况下，你不需要允许从工作站发起的 SMB 通信，除非是特定的基础设施系统。

    `Host‑based firewalls` 可以让你设置规则，限制谁可以向工作站发起 SMB 通信。对 Windows 服务器也可能适用。你应知道哪些基础设施系统应允许入站请求，以及应从哪些系统允许。

-   `Network Firewalls` 主机防火墙保护单个系统，但你可以在网络段之间启用网络防火墙，仅允许从预期的基础设施系统发起的 SMB 流量，从而在源头拦截大量流量。

-   `Disable Sharing` 在企业网络中，通常不应允许工作站进行共享。更好的做法是将共享放在服务器上，集中管理，让用户从文件服务器共享文件。禁用共享会自动减少外部可获得的信息量。

-   `Disable NetBIOS over TCP/IP` 这不是大多数 Windows 网络功能所必需的协议。可以禁用它，从而防止通过 TCP/IP 堆栈进行 NetBIOS 探测。

### 简单网络管理协议

简单网络管理协议（SNMP）自 1980 年代末期以来一直存在，并经历了多次迭代。第一个版本（SNMPv1）于 1988 年推出，尽管随后出现了更替，它仍在使用。SNMPv1 存在多个安全缺陷。它是二进制协议，但不支持加密，这意味着任何能截获传输数据的人都能轻松解码。另一个问题是其认证非常弱：SNMPv1 使用“公共字符串”进行访问，要么提供只读权限，要么提供读写权限，且没有比这更细粒度的控制。此外，它缺乏用户概念，你只需提供相应字符串即可获得相应访问级别。更糟的是，常用的公共字符串非常出名：读取使用 “public”，读写使用 “private”。这些字符串并非硬编码，但使用非常普遍。

版本 2 引入了一些修复，解决了该协议的广为人知的问题。它首先增强了基于社区字符串的基本认证模型。然而，随之而来的 v2c 保留了社区字符串的实现，这意味着现有工具仍可仅使用社区字符串进行认证，而无需实现额外的认证机制。v2 与 v1 不兼容，其消息规范不同，即使工具仅使用社区字符串，也无法直接在使用 v1 的系统上运行。

版本 3 实现了进一步的修复，相较前几版是重大改进。首先，它支持加密而非明文传输。其次，它支持基于用户的认证，这提高了问责性，让你清楚谁在做什么。这是重要的，因为 SNMP 不仅用于监控设备，还可用于设置端点参数。

基本的 SNMP 架构在端点上安装代理，服务器系统定期轮询这些代理以获取监控数据。SNMP 代理可以提供存储在管理信息基（MIB）中的信息。MIB 定义了使用 Abstract Syntax Notation One（ASN.1）的数据结构。每个节点或数据元素都有一个对象标识符（OID），是由数字序列组成的点分隔字符串。获取或设置任何值都需要提供对应的 OID。

SNMP 可提供大量有用信息，前提是已在代理上正确安装并运行相应的 MIB。这包括系统名称、运行的内核版本等。下面的示例展示了使用 `snmpwalk` 程序“遍历” MIB 树以获取代理数据的过程。它从树的顶层开始，收集所有可得信息。`snmpwalk` 的输出中可以看到系统名称以及内核标识，还有一些在 SNMP 代理中配置的联系信息。输出中使用 `‑v 2c` 指定版本，使用 `‑c` 参数指定公共字符串，这里的字符串是 `‘public’`。

#### `snmpwalk` of Linux System

```
```
