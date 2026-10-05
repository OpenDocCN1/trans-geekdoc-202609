
示例 3-24 显示了针对目标 `192.168.88.251` 运行 `nmap smb-enum-users` 脚本的结果。如你所示，结果表明该脚本能够列出在该 Windows 目标上配置的用户。

**示例 3-24** 列举 SMB 用户

点击此处查看代码图像

```
|--[root@websploit]--[~]
|--- #nmap  script smb-enum-users.nse 192.168.88.251
Starting Nmap 7.91 ( https://nmap.org ) at 2021-06-22 11:14 EDT
Nmap scan report for 192.168.88.251
Host is up (0.012s latency).
Not shown: 992 closed ports
PORT     STATE SERVICE
22/tcp   open  ssh
80/tcp   open  http
139/tcp  open  netbios-ssn
445/tcp  open  microsoft-ds
3306/tcp open  mysql
8888/tcp open  sun-answerbook
9000/tcp open  cslistener
9090/tcp open  zeus-admin
Host script results:
| smb-enum-users:
|   VULNHOST-1\derek (RID: 1000)
|     Full name:
|     Description:
|_    Flags:       Normal user account
Nmap done: 1 IP address (1 host up) scanned in 0.81 seconds
```

示例 3-24 中的高亮行显示了被 Nmap 列出的的用户（`derek`）。

### 组列举

对于渗透测试人员来说，组列举有助于确定目标环境中使用的授权角色。用于列举 SMB 组的 Nmap NSE 脚本是 `smb-enum-groups`。该脚本尝试从远程 Windows 机器获取组列表。你还可以揭示作为这些组成员的用户列表。命令的语法如下：

点击此处查看代码图像

```
nmap --script smb-enum-groups.nse -p445 <host>
```

示例 3-25 显示了针对 `192.168.56.3` Windows 服务器运行该命令的示例输出。此示例使用了已知凭据来收集信息。

**示例 3-25** 列举 SMB 组

点击此处查看代码图像

```
|--[root@websploit]--[~]
|--- #nmap --script smb-enum-groups.nse --script-args smbusername=vagrant,smbpass=vagrant 192.168.56.3
Starting Nmap 7.91 ( https://nmap.org )
Nmap scan report for 192.168.56.3
Host is up (0.0062s latency).
Not shown: 979 closed ports
PORT      STATE SERVICE
22/tcp    open  ssh
135/tcp   open  msrpc
139/tcp   open  netbios-ssn
445/tcp   open  microsoft-ds
3306/tcp  open  mysql
3389/tcp  open  ms-wbt-server
MAC Address: 08:00:27:1B:A4:60 (Oracle VirtualBox virtual NIC)
Host script results:
| smb-enum-groups:
|   Builtin\Administrators (RID: 544): Administrator, vagrant, sshd_server
|   Builtin\Users (RID: 545): vagrant, sshd, sshd_server, leia_organa, luke_skywalker, han_solo, artoo_detoo, c_three_pio, ben_kenobi, darth_vader, anakin_skywalker, jarjar_binks, lando_calrissian, boba_fett, jabba_hutt, greedo, chewbacca, kylo_ren
|   Builtin\Guests (RID: 546): Guest, ben_kenobi
|   Builtin\Power Users (RID: 547): boba_fett
|   Builtin\Print Operators (RID: 550): jabba_hutt
|   Builtin\Backup Operators (RID: 551): leia_organa
|   Builtin\Replicator (RID: 552): chewbacca
|   Builtin\Remote Desktop Users (RID: 555): greedo
|   Builtin\Network Configuration Operators (RID: 556): anakin_skywalker
|   Builtin\Performance Monitor Users (RID: 558): lando_calrissian
|   Builtin\Performance Users (RID: 559): jarjar_binks
|   Builtin\Distributed COM Users (RID: 562): artoo_detoo
|   Builtin\IUS (RID: 568): darth_vader
|   Builtin\Cryptographic Operators (RID: 569): han_solo
|   Builtin\Event Readers (RID: 573): c_three_pio
|   Builtin\Certificate Service DCOM Access (RID: 574): luke_skywalker
|_  VAGANT-2008R2\WinMIUsers__(RID: 1003): <empty>
Nmap done: 1 IP address (1 host up) scanned in 0.81 seconds
|--[root@websploit]--[~]
|--- #
```

示例 3-25 中的高亮输出显示了列出的组和用户。在 Windows 中，相对标识（RID）是分配给对象的变长度数字，安全标识符（SID）唯一唯一标识账户或组。要了解更多关于 `RID` 数字的信息，请参见 `https://docs.microsoft.com/en-us/trouhoot/windows-server/identity/security-in-windows`。

### 网络共享列举

识别网络上共享文件、文件夹和打印机有助于构建内部网络的攻击面。Nmap `smb-enum-shares` 脚本使用远程过程调用（RPC）用于网络共享。`smb-enum-shares` 脚本的语法如下：

点击此处查看代码图像

```
nmap --script smb-enum-shares.nse -p445 <host>
```

示例 3-26 展示了 SMB 共享的列举。

**示例 3-26** 列举 SMB 共享

点击此处查看代码图像

```
|--[root@websploit]--[~]
|--- #nmap --script smb-enum-shares.nse -p445 192.168.88.251
Starting Nmap 7.91 ( https://nmap.org ) at 2021-06-22 11:27 EDT
Nmap scan report for 192.168.88.251
Host is up (0.0011s latency).
PORT    STATE SERVICE
445/tcp open  microsoft-ds
Host script results:
| smb-enum-shares:
|   account_used: guest
|   \\192.168.88.251\IPC$:
|     Type: STYPE_IPC_HIDDEN
|     Comment: IPC Service (Samba 4.9.5-Debian)
|     Users: 1
|     Max Users: <unlimited>
|     Path: C:\tmp
|     Anonymous access: READ/WRITE
|     Current user access: READ/WRITE
|   \\192.168.88.251\print$:
|     Type: STYPE_DISKTREE
|     Comment: Printer Drivers
|     Users: 0
|     Max Users: <unlimited>
|     Path: C:\var\lib\samba\printers
|     Anonymous access: <none>
|     Current user access: <none>
|   \\192.168.88.251\secret_folder:
|     Type: STYPE_DISKTREE
|     Comment: Extremely sensitive information
|     Users: 0
|     Max Users: <unlimited>
|     Path: C:\secret_folder
|     Anonymous access: <none>
|_    Current user access: <none>
Nmap done: 1 IP address (1 host up) scanned in 0.39 seconds
|--[root@websploit]--[~]
|--- #
```

### 额外的 SMB 列举示例

早期示例中系统（IP 地址为 `192.168.88.251`）运行 Linux 和 Samba。然而，从之前的扫描结果很难判断它是一个 Linux 系统。对主机上运行的应用程序和操作系统进行额外列举和指纹识别的简单方法是使用 `nmap -sC` 命令。`-sC` 根据目标系统上发现的开放端口运行最常见的 NSE 脚本。

**提示**

你可以仅使用 `locate *.nse` 命令在 Kali Linux 和 Parrot OS 中定位已安装的 NSE 脚本。`https://nmap.org/book/man-nse.html` 包含了对 NSE 的详细说明以及使用 Lua 编程语言创建新脚本的方法。

示例 3-27 显示针对运行 Samba 的 `192.168.88.251` Linux 系统启动的 `nmap -sC` 命令输出。

**示例 3-27** 运行 Nmap NSE 默认脚本

点击此处查看代码图像

```
|--[root@websploit]--[~]
|--- #nmap -sC 192.168.88.251
Starting Nmap 7.80 ( https://nmap.org ) at 2021-06-21 17:38 EDT
Nmap scan report for 192.168.88.251
Host is up (0.00011s latency).
Not shown: 992 closed ports
PORT     STATE SERVICE
22/tcp   open  ssh
| ssh-hostkey:
|   2048 d0:0c:83:4d:7f:84:2c:60:96:9f:df:26:da:d2:11:9a (RSA)
|   256 e2:aa:69:ab:a3:e6:0f:13:c5:5a:65:f2:d5:16:8c:3e (ECDSA)
|_  256 21:4b:27:7b:6e:a6:d4:33:86:60:cb:39:3b:48:9c:0b (ED25519)
80/tcp   open  http
|_http-title: WebSploit Mayhem
139/tcp  open  netbios-ssn
445/tcp  open  microsoft-ds
3306/tcp open  mysql
| mysql-info:
|   Protocol: 10
|   Version: 5.5.47-0ubuntu0.14.04.1
|   Thread ID: 3
|   Capabilities flags: 63487
|   Some Capabilities: InteractiveClient,
DontAllowDatabaseTableColumn, FoundRows, IgnoreSigpipes,
Support41Auth, ODBCClient, ConnectWithDatabase, LongPassword,
SupportsTransactions, IgnoreSpaceBeforeParenthesis,
Speaks41ProtocolOld, Speaks41ProtocolNew, SupportsCompression,
SupportsLoadDataLocal, LongColumnFlag, SupportsMultipleResults,
SupportsMultipleStatments, SupportsAuthPlugins
|   Status: Autocommit
|   Salt: b_60.4ZH=52:l5ajmhBP
|_  Auth Plugin Name: mysql_native_password
8888/tcp open  sun-answerbook
9000/tcp open  cslistener
9090/tcp open  zeus-admin
MAC Address: 1E:BD:4F:AA:C6:BA (Unknown)
Host script results:
|_clock-skew: mean: 17s, deviation: 0s, median: 17s
|_nbstat: NetBIOS name: VULNHOST-1, NetBIOS user: <unknown>, NetBIOS
MAC: <unknown> (unknown)
| smb-os-discovery:
|   OS: Windows 6.1 (Samba 4.9.5-Debian)
|   Computer name: vulnhost-1
|   NetBIOS computer name: VULNHOST-1\x00
|   Domain name: ohmr.org
|   FQDN: vulnhost-1.ohmr.org
|_  System time: 2022-06-21T21:38:40+00:00
| smb-security-mode:
|   account_used: guest
|   authentication_level: user
|   challenge_response: supported
|_  message_signing: disabled (dangerous, but default)
| smb2-security-mode:
|   2.02:
|_    Message signing enabled but not required
| smb2-time:
|   date: 2021-06-21T21:38:40
|_  start_date: N/A
Nmap done: 1 IP address (1 host up) scanned in 28.77 seconds
|--[root@websploit]--[~]
|--- #
```

高亮行在示例 3-27 中显示了系统上运行的 Samba 版本详情（Samba 版本 4.9.5）。你也可以看到，尽管操作系统被标记为 Windows 6.1，但正确的操作系统实际上是 Debian。示例 3-28 显示了目标系统（vulnhost-1）上执行 `samba -V` 命令的输出，这证实了扫描器能够确定出正确的 Samba 版本。

### 示例 3-28 在目标系统上确认扫描结果

点击此处查看代码图像

```
omar@vulnhost-1:~$ sudo samba -V
Version 4.9.5-Debian
omar@vulnhost-1:~$
```

你也可以使用 `enum4linux` 等工具来枚举 Samba 共享，包括用户账户、共享和其他配置。示例 3-29 显示了 `enum4linux` 工具在针对目标系统（192.168.88.251）启动后的输出。

### 示例 3-29 使用 enum4linux 举额外信息

点击此处查看代码图像

# 使用 `enum4linux` 进行 SMB 扫描

```bash
|-- [root@websploit]--[~]
|--- #enum4linux 192.168.88.251
Starting enum4linux v0.8.9 ( http://labs.portcullis.co.uk/application/
enum4linux/ )
 ==========================
|    目标信息    |
 ==========================
目标 ........... 192.168.88.251
RID 范围 ........ 500-550,1000-1050
用户名 ......... ''
```
