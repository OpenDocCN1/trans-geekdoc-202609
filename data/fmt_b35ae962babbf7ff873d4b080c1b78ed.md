
## 数据包检查与窃听

作为一名渗透测试员，你可以使用`wireshark`、`tshark`和`tcpdump`等工具来捕获和分析流量。任何参与过网络或安全领域的人都曾在某个时候使用过这些工具进行侦察。如果你担心被发现，可能尝试被动侦察会更好，因为这不需要进入建筑内部。第 5 章“有线和无线网络攻击”深入探讨了这一主题。

## 理解漏洞扫描的艺术

一旦你确定了可用的目标主机以及在这些主机上监听的服务，你就可以开始探测这些服务以确定是否存在漏洞；这就是漏洞扫描器的工作。漏洞扫描器使用多种不同的方法来确定服务是否存在漏洞。主要方法是识别正在运行的软件版本，并尝试将其与已知的漏洞进行匹配。例如，如果漏洞扫描器确定某个 Linux 服务器运行着过时的 Apache Web 服务器，且该版本易受到远程攻击的影响，它会将该漏洞作为一个发现进行报告。

当然，自动化漏洞扫描器的主要问题是误报（false positives）；如果不对发现结果进行验证，漏洞扫描的输出可能将毫无用处。将一份充满误报的报告交给负责修复问题的开发人员或管理员，可能会引起冲突。

### 典型的自动化漏洞扫描器的工作原理

现在让我们来看看典型的自动化漏洞扫描器是如何工作的（参见图 3-15）。它们在某些方面各不相同，但大多数都遵循一个相似的过程：

**步骤 1**。在发现阶段，扫描器使用如`Nmap`的工具进行主机和端口枚举。

**步骤 2**。当扫描器获取了足够的开放端口信息以确定其运行的软件和版本时，它会将这些信息记录在数据库中以便进一步分析。

**步骤 3**。扫描器尝试确定监听目标系统上的软件是否易受到已知漏洞的影响。它是通过将已知漏洞数据库与数据库中记录的目标服务信息进行关联来实现的。

**步骤 4**。扫描器会对其怀疑可能存在漏洞的地方生成报告。请记住，这些结果往往是误报，需要进行验证。

至少，这种类型的工具可以让你对去哪里寻找可能被利用的漏洞有一个大致的概念。

![图 3-15 漏洞扫描器插图](img/03fig15.jpg)

**图 3-15** 漏洞扫描器插图

## 漏洞扫描类型

使用哪种漏洞扫描通常由自动化漏洞扫描工具中创建的扫描策略驱动。每个工具都有许多可用的扫描选项。你通常只需选择进行全扫描，这将运行所有扫描选项，尽管你可能无法使用每一个选项（例如，如果你正在扫描生产环境或一个在扫描发生时容易崩溃的设备）。在这种情况下，你必须小心只选择不太可能引起问题的扫描选项。接下来的章节将详细介绍典型的扫描类型。

![关键主题图标](img/key_topic_icon2.jpg)

### 未经过身份扫描

默认情况下，漏洞扫描器不使用凭据扫描目标。如果你只提供目标的 IP 地址并点击“扫描”，工具将从未经过身份远程攻击者的角度开始枚举主机。`未经过身份扫描`只显示暴露在网络上的网络服务。扫描器尝试枚举目标主机上开放的端口。如果服务没有在扫描器连接的网络段上监听，或者它被防火墙拦截，扫描器将报告该端口为关闭并继续。然而，这并不意味着没有漏洞。有时可以通过 SSH 端口转发和其他技巧访问未暴露在网络上的端口。在可能的情况下，运行凭据的（或身份验证的）扫描仍然是非常重要的。

**提示**

身份验证扫描的误报率可能比未经过身份扫描更低。

### 身份验证扫描

在某些情况下，最好对目标运行身份验证扫描以获取攻击面的全景。`身份验证扫描`要求你为扫描器提供一组具有系统 root 级权限的凭据。扫描器实际上通过 SSH 或其他机制登录到目标。然后它运行类似`netstat`的命令从主机内部收集信息。扫描器运行的许多命令都需要 root 级权限才能从系统中收集正确信息。

示例 3-42 显示了非权限用户（`omar`）运行的`netstat`命令；示例 3-43 显示了 root 用户运行的`netstat`命令。你可以看到不同用户级别权限的输出是不同的。具体来说，注意当以用户`omar`运行时，PID/程序名称不可用，而当以用户`root`运行时，就会显示该信息。

**示例 3-42** 无 root 级权限的 Netstat 示例

点击此处查看代码图像

```
omar@vulnhost-1 ~ % netstat -tunap

(Not all processes could be identified, non-owned process info
will not be shown, you would have to be root to see it all.)
Active Internet connections (servers and established)
Proto Recv-Q Send-Q Local Address         Foreign Address
State       PID/Program name
tcp        0       0 0.0.0.0:9000         0.0.0.0:*     LISTEN     -
tcp        0       0 0.0.0.0:9001         0.0.0.0:*     LISTEN     -
tcp        0       0 0.0.0.0:9002         0.0.0.0:*     LISTEN     -
tcp        0       0 0.0.0.0:3306         0.0.0.0:*     LISTEN     -
tcp        0       0 0.0.0.0:139          0.0.0.0:*     LISTEN     -
tcp        0       0 0.0.0.0:80           0.0.0.0:*     LISTEN     -
tcp        0       0 0.0.0.0:8881         0.0.0.0:*     LISTEN     -
tcp        0       0 0.0.0.0:8882         0.0.0.0:*     LISTEN     -
tcp        0       0 0.0.0.0:8883         0.0.0.0:*     LISTEN     -
tcp        0       0 0.0.0.0:8884         0.0.0.0:*     LISTEN
<output omitted for brevity>
```

示例 3-43 显示了与打开端口相关的进程和程序名称详情。

**示例 3-43** 具有 root 级权限的 Netstat 示例

点击此处查看代码图像

```
omar@vulnhost-1 ~ % sudo netstat -tunap
Active Internet connections (servers and established)
Proto Recv-Q Send-Q Local Address       Foreign Address  State
PID/Program name
tcp         0      0 0.0.0.0:9000       0.0.0.0:*       LISTEN
1076/docker-proxy
tcp         0      0 0.0.0.0:9001       0.0.0.0:*       LISTEN
762/docker-proxy
tcp         0      0 0.0.0.0:9002       0.0.0.0:*       LISTEN
1287/docker-proxy
tcp         0      0 0.0.0.0:3306       0.0.0.0:*       LISTEN
1095/docker-proxy
tcp         0      0 0.0.0.0:139        0.0.0.0:*       LISTEN
247/smbd
tcp         0      0 0.0.0.0:80         0.0.0.0:*       LISTEN
506/docker-proxy
```

如前所述，`全扫描`通常涉及启用扫描策略中的所有扫描选项。这些选项因扫描器而异，但大多数漏洞扫描器的选项分类方式都相似。例如，它们通常按照操作系统、设备制造商、设备类型、协议、合规性和攻击类型进行组织，其余选项可能归类为杂项。示例 3-44 展示了 Nessus 漏洞扫描器插件类别的示例列表。从此列表中可以看出，扫描器有许多可运行的插件。根据插件类别的名称也显而易见，绝不存在某个单一设备能同时适用于所有插件。例如，适用于 macOS 设备的插件将不适用于 Windows 设备。这就是为什么你通常需要自定义插件选择，以反映你正在扫描的环境。这样做可以减少不必要的流量并加快你的扫描过程。

### 示例 3-44 来自 Nessus 的插件类别示例

点击此处查看代码图像

```
Family                                        Count
AIX Local Security Checks                     11416
Amazon Linux Local Security Checks             1048
Backdoors                                       114
Brute force attack                               26
CGI abuses                                     3841
CGI abuses : XS                                 666
CISCO                                           918
CentOS Local Security Checks                   2585
DNS                                             172
Databases                                       577
Debian Local Security Checks                   5532
Default Unix Accounts                           168
Denial of Service                               109
F5 Networks Local Security Checks               607
FTP                                             255
Fedora Local Security Checks                  12634
Firewalls                                       240
FreeBSD Local Security Checks                  3957
Gain a shell remotely                           280
General                                         255
Gentoo Local Security Checks                   2650
HP-UX Local Security Checks                    1984
Huawei Local Security Checks                    563
Junos Local Security Checks                     212
macOS Local Security Checks                    1191
Mandriva Local Security Checks                 3139
Misc.                                          1661
Mobile Devices                                   76
Netware                                          14
Oracle Linux Local Security Checks             2806
OracleVM Local Security Checks                  459
Palo Alto Local Security Checks                  49
Peer-To-Peer File Sharing                        90
Policy Compliance                                49
Port scanners                                     7
RPC                                              38
Red Hat Local Security Checks                  4864
SCADA                                           300
SMTP problems                                   139
SNMP                                             33
Scientific Linux Local Security Checks         2493
Service detection                               431
Settings                                         85
Slackware Local Security Checks                1067
Solaris Local Security Checks                  4937
SuSE Local Security Checks                    11377
Ubuntu Local Security Checks                   4130
VMware ESX Local Security Checks                118
Virtuozzo Local Security Checks                 191
Web Servers                                    1092
Windows                                        4053
Windows : Bulletins                             1509
Windows : User                                   28
```
