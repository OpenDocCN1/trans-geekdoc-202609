
你可以安装单个实例，也可以在物理宿主机有足够内存的情况下，在虚拟机中安装多个实例。要构建一个运行的 Windows 网络，你应该至少运行一个桌面版本和一个服务器版本（并将服务器配置为 AD）。可以通过图形用户界面（GUI）添加域控制器和其他角色，而 Windows 擅长通过这一过程手动处理这些工作。

安装最新版本的 Windows Server 会让你看到一个界面，类似于图 13.4 所示。这实际上是一个用于设置服务器和安装不同角色（或服务）的向导。构建设置过程将让你学习到大量关于 Windows 网络的知识，并让你对安全角度可能犯的错误有所了解。尝试向你的域添加用户并赋予他们不同的权限，你就能理解域管理员是如何犯错的。

![](img/46e491ee87887ca9f9393b757b453bb7_488_0.png)

图 13.4：Windows Server 2019

> 注意：在第 9 章“文件与文件共享”中，你接触到了 Samba，它可以用于在网络上共享更多文件。Samba 实现了一系列 Windows 服务器技术，可以用于设置 AD DC（域控制器），这意味着你不需要设置 Windows 机器即可练习某些 Windows 攻击技术。请见下一页有关如何使用 Samba 设置 AD DC 的详情：wiki.samba.org/index.php/Setting_up_Samba_as_an_Active_Directory_Domain_Controller

# Windows 攻击工具包

你到为止遇到的同样的通用型黑客工具——Nmap、Searchscript、Metasploit、Netcat 等——都可以像通常一样用于 Windows 主机，并从你的 Kali 虚拟机中运行。你在第 9 章看到的工具在探测 NetBIOS、服务器消息块 (SMB) 和远程调用 (RPC) 时也将特别有用。请记住，Windows 使用它自己的 RPC 协议 Microsoft RPC (MS-RPC)，它是分布式计算环境 (DCE) RPC 系统的修改版本。尽管如此，这种形式的 RPC 有不同的引导，如基于 TCP 的 DCE/RPC 和基于 HTTP 的 DCE/RPC。正如你可以想象的，有很多定制的 Windows 攻击工具，例如：

- 穷举工具 (`enumlinux`、`enum.exe` 和 `RIDenum`)
- 域映射工具 (`BloodHound`)
- Windows 外壳工具 (`PowerShell`、`PowerTools`、`PwnShell` 和 `Empire`)
- .NET 应用 (`Mimikatz`)
- 密码哈希转储工具 (`Mimikatz`、`Samdump`、`Cain and Abel`)
- 哈希值传递工具 (`impacket`)
- 渗透后工具 (`Metasploit` 和 `Empire`)

记住，黑客与系统管理员非常相似，只是没有授权。如果你打算攻击 Windows，就需要熟悉可用的工具。Hacker House 汇集了一些常用工具二进制包。与所有二进制文件一样，从网上下载时要谨慎。

www.hackerbook.com/files/Windows_Tradecraft.zip

# Windows 与 NSA

当几个国家安全局 (NSA) 的工具泄露时，人们发现他们一直在使用自己的 Windows 攻击框架进行操作。许多此类利用工具已进入他人手中。以下是泄露工具的部分选择：

- `FUZZBUNCH`：基于 Python 和动态链接库 (DLL) 的利用框架
- `DANDERSPRITZ`：一种用于间谍活动的远程访问工具，具有清理日志隐藏攻击轨迹的功能
- `DOUBLEPULSAR`：用于 DLL 注入的内核负载
- `ETERNALBLUE`
- `ETERNALROMANCE`
- `ETERNALCHAMPION`
- `ETERNSYNERGY`

> 警告：在使用泄露工具时需要极其谨慎。由 NSA 这样拥有大量资源的组织开发的工具可能会在其软件中内置追踪功能。在使用时，工具可能会向其真实所有者报告，或引入未知的恶意软件。使用此类工具可能会无意中使自己的系统或系统受到攻击，并可能带来进一步的法律后果。在没有网络访问的虚拟环境中使用工具，并使用像 `Wireshark` 这样的数据包分析工具，是减少工具可能造成的损害的方法之一，并为你提供分析的机会。

# 扫描 Windows Server

Nmap 也可以像你目前所看到的那样用于扫描 Windows 主机。以下代码是对一个运行 Windows Server 2008 的虚拟机的基础端口扫描。这将让你对域控制器上运行的服务有一个大致了解。虽然这现在看起来可能过时了，但你将获得类似的结果，这适用于配置了组策略或安装了 IIS 服务后的较后版本的 Windows Server。

```
Nmap scan report for 192.168.56.104
Host is up (0.00049s latency).
Not shown: 65535 closed ports
PORT      STATE SERVICE       VERSION
53/tcp    open  domain        Microsoft DNS 6.1.7601
| dns-nsid|
|_bind.version: Microsoft DNS 6.1.7601 (IDB1446A)
80/tcp    open  http          Microsoft IIS httpd 7.5
88/tcp    open  kerberos-sec  Microsoft Windows Kerberos
135/tcp   open  msrpc         Microsoft Windows RPC
139/tcp   open  netbios-ssn   Windows netbios-ssn
389/tcp   open  ldap          Microsoft Active Directory LDAP
443/tcp   open  ssl/?
445/tcp   open  microsoft-ds  Windows Server 2008 R2 Standard 7601
464/tcp   open  kpasswd5
593/tcp   open  nacmn_http    Microsoft Windows RPC over HTTP 1.0
636/tcp   open  tcpwrapped
3268/tcp  open  ldap          Microsoft Active Directory LDAP
3269/tcp  open  tcpwrapped
3389/tcp  open  ssl/ms-bt-server?
5900/tcp  open  vnc           VNC (protocol 3.8)
9389/tcp  open  mc-mnf        .NET Message Framing
4701/tcp  open  http          Microsoft HTTPAPI httpd 2.0 (SSDP/UHP)
49152/tcp open  msrpc         Microsoft Windows RPC
49153/tcp open  msrpc         Microsoft Windows RPC
49154/tcp open  msrpc         Microsoft Windows RPC
49155/tcp open  msrpc         Microsoft Windows RPC
49156/tcp open  msrpc         Microsoft Windows RPC
49158/tcp open  nacmn_http    Microsoft Windows RPC over HTTP 1.0
49161/tcp open  msrpc         Microsoft Windows RPC
49163/tcp open  msrpc         Microsoft Windows RPC
49168/tcp open  msrpc         Microsoft Windows RPC
49186/tcp open  msrpc         Microsoft Windows RPC
49187/tcp open  msrpc         Microsoft Windows RPC
```

在本章中，我们将使用一些旧软件来解释漏洞，但如果这些技术与不安全的系统相关联，许多技术也适用于新的系统。Windows 的“阿喀琉斯之踵”在于它对同一网域内的其他系统非常信任。Windows 主机的安全性完全取决于它所连接的受信外部网络资源，无论该资源是 ICS 环境中运行 Windows XP 的旧式桌面电脑，还是其他过时的主机。一旦网络上的某一个系统被破解，通常就可以从系统到系统进行扩散，这导致了许多灾难性攻击在 Microsoft 平台上变得频发。

Nmap 结果表明，Windows Server 托管在许多关键端口和服务上，你可以看到这些：这些是 Kerberos 服务（`kerberos-sec` 和 `kpasswd`）；Microsoft RPC（`msrpc`），它与你已经探索过的开放网络计算 (ON) RPC 类似（TCP 端口 595 正在监听 RPC over HTTP，这与 XML RPC 相当）；NetBIOS 服务（`netbios-ssn`）；Microsoft Directory 服务/SMB（`microsoft-ds`）以及 `ms-wbt-server` 服务，后者是远程桌面协议（RDP，也称为终端服务）。上一个屏幕中显示的其他服务并非 Microsoft 特有。还要记住，某些服务（如 SMB 和 NetBIOS 服务）可以使用 Samba 运行在类 Unix 服务器上。你将在扫描结果的末尾看到许多被 MRPC 使用的端口。

上一个图中还显示了其他服务，它们适用于任何主机——DNS、HTTP、HTTPS 和 LDAP 服务。如果你设置了 Windows Server 2019 实验室并分配了域控制器、DNS 服务器（DC 需要）和 Web 服务器角色，那么你将看到类似下面的默认安装的端口扫描：

```
Nmap report for 192.168.56.109
Host is up (0.00071 latency).
Not shown: 994 filtered ports
PORT     STATE SERVICE
53/tcp   open  domain
80/tcp   open  http
135/tcp  open  msrpc
139/tcp  open  netbios-ssn
445/tcp  open  microsoft-ds
3389/tcp open  ms-wbt-server
```

# Microsoft DNS

上一个扫描结果中显示的第一个开放端口是 53 端口，你现在应该知道它是用于 DNS 的。你应该尝试在这里使用 Dig，就像对任何其他 DNS 主机或服务做的那样。针对提供 DNS 服务的 Windows Server 上使用 `dig @TargetIP version.bind txt` 命令，可能会返回一些有用信息，如下：

```
;;>>HEADER<< opcode: QUERY, status: NOERROR, id: 33661
;; flags: aa rd rd; QUERY: 1, ANSWER: 1, AUTHORITY: 0, ADDITIONAL: 1
;; WARNING: recursion requested but not available

;; QUESTION SECTION:
;;version.bind. CH TXT

;; ANSWER SECTION:
;;version.bind. 14765 IN TXT "Microsoft 6.1.7601 (IDB1446A)"
```
