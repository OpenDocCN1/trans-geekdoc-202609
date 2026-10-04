
```
|--[root@websploit]--[~]
|--- #nmap -sV --script=http-enum -p 80 192.168.88.251
Starting Nmap 7.91 ( https://nmap.org ) at 2021-06-22 11:53 EDT
Nmap scan report for 192.168.88.251
Host is up (0.0011s latency).

PORT   STATE SERVICE VERSION
80/tcp open  http    nginx 1.17.2
| http-enum:
|   /admin/: Possible admin folder
|   /admin/index.html: Possible admin folder
|_  /s/: Potentially interesting folder
|_http-server-header: nginx/1.17.2
Service detection performed. 请向 https://nmap.org/submit/ 报告任何错误结果。
Nmap done: 1 IP address (1 host up) scanned in 8.54 seconds
|--[root@websploit]--[~]
|--- #
```

示例 32 中高亮的输出显示了多个枚举的目录/文件夹以及所使用的 Web 服务器版本（Nginx 1.17.2）。这是攻击 Web 应用程序的良好起点。

我们应该讨论的另一个 Web 服务器枚举工具是 `Nikto`。`Nikto` 是一个存在多年的开源 Web 漏洞扫描器。它不像商业 Web 漏洞扫描器那样强大；但在运行快速脚本来枚举 Web 服务器及其托管的应用程序信息方面非常有用。由于 `Nikto` 扫描 Web 服务器的速度非常快，它的噪声非常大。它提供了许多扫描选项，包括对需要用户名和密码的 Web 进行身份验证的能力。示例 3-33 显示了针对示例 3-32 中相同的主机（192.168.88.251）运行 `Nikto` 扫描的输出。示例 3-33 中的输出结果与示例 3-32 中使用的 Nmap 脚本相似。

### 示例 3-33 Nikto 扫描示例

点击此处查看代码图像

```
|--[root@websploit]--[~]
|--- #nikto -h 192.168.88.251
- Nikto v2.1.6
-----------------------------------------------------------------------
+ Target IP:           192.168.88.251
+ Target Hostname:    192.168.88.251
+ Target Port:         80
-----------------------------------------------------------------------
+ Server: nginx/1.17.2
+ The anti-clickjacking X-Frame-Options header is not present.
+ The anti-clickjacking X-Frame-Options header is not present.
+ The X-XSS-Protection header is not defined. This header can hint to
the user agent to protect against some forms of XSS
+ The X-Content-Type-Options header is not set. This could allow the
user agent to render the content of the site in a different fashion
to the MIME type
+ No CGI Directories found (use '-C all' to force check all possible
dirs)
+ OSVDB-3092: /admin/: This might be interesting...
+ /admin/index.html: Admin login page/section found.
+ /wp-admin/: Admin login page/section found.
+ /wp-login/: Admin login page/section found.
+ 7916 requests: 0 error(s) and 7 item(s) reported on remote host
+ End Time:            2021-06-22 11:57:59 (GMT-4) (15 seconds)
---------------------------------------------------------------------------
+ 1 host(s) tested
|--[root@websploit]--[~]
|--- #
```

**提示**

没有任何工具是完美的。建议你熟悉不同工具的行为和输出。第 10 章涵盖了若干可以用于枚举和侦察的额外工具。

#### 服务枚举

*服务枚举* (#gloss.xhtml#gloss_167) 是识别在远程系统上运行的服务的过程，它是 Nmap 作为端口扫描器的主要关注点。本章早些讨论强调了各种扫描类型以及如何使用它们来绕过过滤器。当你连接到直接连接网段上的系统时，可以运行一些额外的脚本进行进一步枚举。端口扫描从具有凭据的远程用户的视角出发。Nmap 的 `smb-enum-processes` NSE 脚本枚举 Windows 系统上的服务。

```
>>> ls(DNS)
length      : ShortField (Cond)
id          : ShortField        = (0)
qr          : BitField                 = (0)
opcode      : BitField  = bits (0)
aa          : BitField                 = (0)
tc          : BitField                 = (0)
rd          : BitField                 = (1)
ra          : BitField                 = (0)

          : BitField                 = (0)
ad          : BitField                 = (0)
rcode       : BitField  = (0)
qd:::SRRCount                   = (None)
ancount     : DNSRRCount                   = (None)
nscount     : DNSRRCount                   = (None)
arcount     : DNSRRCount                   = (None)
qd          : DNSQR                        = (None)
an          : DNSSRRField= (None)
ns          ::SRRField== (
)
```

你可以使用 `explore()` 函数来遍历 Scapy 层和协议。在执行 `explore()` 函数后，将显示图 3-14。

![图 3-14 在 Scapy 中使用 explore() 函数](img/03fig14)

**图 3-14** 在 Scapy 中使用 explore() 函数

你可以使用 `explore()` 处理任何数据包格式或协议。示例 3-39 显示了使用 `explore("dns")` 函数时 `scapy.layers.dns` 中的数据包。

**示例 3-39** 使用 `explore("dns")` 函数显示 `scapy.layers.dns` 中的数据包类型

点击查看代码

```
>>> explore("dns")

scapy.layers.dns 中的数据包：

Class                      |Name

---------------------------|------------------------------

DNS                        |DNS

DNSQR                      |DNS Question Record

DNSRR                      |DNS Resource Record

DNSRRDLV                   |DNS DLV Resource Record

DNSRRDNSKEY                |DNS DNSKEY Resource Record

DNSRRDS                    |DNS DS Record

DNSRRMX                    |DNS MX Record

DNSRRNSEC                  |DNS NSEC Record

DNSRRNSEC3                 |DNS NSEC3 Resource Record

DNSRRNSEC3PARAM            |DNS NSEC3PARAM Resource Record

DNSRROPT                   |DNS OPT Resource Record

DNSRRRSIG                  |DNS RRSIG Resource Record

DNSRRSOA                   |DNS SOA Resource Record

DNSRRSRV                   |DNS SRV Resource Record

DNSRRTSIG                  |DNS TSIG Resource Record

EDNS0TLV                   |DNS EDNS0 TLV
```

你可以通过多种方式将 Scapy 作为扫描器。我在 GitHub 仓库中提供了几个 Python 脚本示例，可以使用 Scapy 进行网络和系统扫描；请访问 [`github.com/The-Art-of-Hacking/h4cker/blob/master/python_ruby_and_bash`](https://github.com/The-Art-of-Hacking/h4cker/blob/master/python_ruby_and_bash)。不过，如示例 3-40 所示，你可以对任何给定的端口进行简单的 TCP SYN 扫描。在这个示例中，向 IP 地址为 `192.168.88.251` 的主机发送了 TCP 445 SYN 包。输出显示收到了一个答案，但没有说明具体的答案（响应）是什么。示例 3-41 显示了目标主机（192.168.88.251）上的数据包捕获。

**示例 3-40** 使用 Scapy 发送 TCP SYN

点击查看代码

```
>>> ans = sr(IP(dst="192.168.88.251")/TCP(dport=445,flags="S"))
```

**示例 3-41** 目标主机上的数据包捕获

点击查看代码

```
>>> ans = sr(IP(dst="192.168.88.251")/TCP(dport=445,flags="S"))
```

#### 封包检查与窃听

作为渗透测试员，你可以使用 `wireshark`、`tshark` 和 `tcpdump` 等工具来捕捉流量。

### 理解漏洞扫描的艺术

一旦你确定了可用的主机以及在上面运行的服务，就可以开始探测这些服务以确定是否存在漏洞。漏洞扫描器的作用。漏洞扫描器使用多种方法来确定服务是否存在漏洞。主要方法是识别运行的软件版本，并将其与已知的漏洞进行匹配。例如，如果漏洞扫描器确定 Linux 服务器运行着过版本的 Apache Web 服务器，该版本容易受到远程攻击，它就会报告该漏洞为。

# 第 4 步。

扫描器会针对它怀疑可能存在漏洞的部分生成报告。请记住，这些结果通常是误报，需要进行验证。

至少，这种工具可以让你大致了解应该去哪里寻找可能被利用的漏洞。

![图 3-15 漏洞扫描器插图](img/03fig15.jpg)

**图 3-15** 漏洞扫描器插图

## 漏洞扫描类型

使用哪种类型的漏洞扫描通常由自动化漏洞扫描工具中创建的扫描策略驱动。每个工具都有许多可用的扫描选项。你通常只需选择进行全扫描，它将运行所有扫描选项，尽管你可能无法使用每一个选项（例如，如果你正在扫描生产环境或一个在扫描发生时极易崩溃的设备）。在这种情况下，你必须小心，只选择不太可能引起问题的扫描选项。接下来的章节将更详细地查看典型的扫描类型。

![](img/key_topic_icon2.jpg)

### 未身份验证扫描

默认情况下，漏洞扫描器不使用凭据扫描目标。如果你只提供目标的 IP 地址并点击扫描，工具将开始从未身份验证远程攻击者的角度枚举该主机。`未身份验证扫描` 只显示暴露在网络上的服务。扫描器尝试枚举目标主机上开放的端口。如果服务没有在扫描器连接的网络网段上监听，或者它被防火墙拦截，扫描器将报告该端口为关闭并继续。然而，这并不意味着没有漏洞。有时通过 SSH 端口转发和其他技巧，可以访问未暴露在网络上的端口。在可能的情况下，运行凭据扫描（或已身份验证扫描）仍然非常重要。

**提示**

已身份验证扫描提供的误报率可能比未身份验证扫描更低。

### 身份验证扫描

在某些情况下，对目标运行身份验证扫描以获取攻击面的全景是最好的。`身份验证扫描` 要求你向扫描器提供一组具有系统 root 级访问权限的凭据。扫描器实际上通过 SSH 或其他机制登录目标。然后它运行如 `netstat` 等命令来从主机内部收集信息。扫描器运行的许多命令都需要 root 级访问权限才能从系统中收集正确信息。

`示例 3-42` 显示了非特权用户 (`omar`) 运行的 `netstat` 命令；`示例 3-43` 显示了 root 用户运行的 `netstat` 命令。你可以看到不同用户权限的输出是不同的。具体来说，注意当以用户 `omar` 运行时，无法获取 PID/程序名称，而当以用户 `root` 运行时，该信息将会显示。

**示例 3-42** 无 root 级权限的 Netstat 示例

点击此处查看代码图像

```
omar@vulnhost-1 ~ % netstat -tunap

(无法识别所有进程，非所有者的进程信息

将不会显示，你必须是 root 才能查看所有信息。)

Active Internet connections (servers and established)

Proto Recv-Q Send-Q Local Address         Foreign Address

State       PID/Program name

tcp        0       0 0.0.0.0:9000         0.0.0.0:*     LISTEN     -

tcp        0       0 0.0.0.0:9001         0.0.0.0:*     LISTEN     -
```

### 发现扫描

`发现扫描` 主要是为了识别目标的攻击面。端口扫描是发现扫描执行的一个主要部分。扫描器实际上可能会使用像 `Nmap` 的工具来执行端口扫描。然后它将端口扫描的结果拉入其数据库，以便使用这些信息进行更深入的发现。例如，端口扫描的结果可能显示端口 80、22 和 443 是开放并监听的。

### 全扫描

**示例 3-42** 无 root 级权限的 Netstat 示例

点击此处查看代码图像

```
omar@vulnhost-1 ~ % netstat -tunap
(无法识别所有进程，非所有者的进程信息
将不会显示，你必须是 root 才能查看所有信息。)
Active Internet connections (servers and established)
Proto Recv-Q Send-Q Local Address         Foreign Address
State       PID/Program name
tcp        0       0 0.0.0.0:9000         0.0.0.0:*     LISTEN     -
tcp        0       0 0.0.0.0:9001         0.0.0.0:*     LISTEN     -
```
