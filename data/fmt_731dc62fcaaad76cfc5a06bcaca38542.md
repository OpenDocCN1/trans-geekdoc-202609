
测试了 1 个主机(s)

```
[root@websploit] [~]
--- #
```

**提示**

没有哪个工具是完美的。建议你熟悉不同工具的行为和输出。第 10 章涵盖了若干种可用于枚举的额外工具。

### 服务枚举

`服务枚举`(gloss.xhtml#gloss_167) 是识别运行在远程系统上的服务的过程，它是 Nmap 作为端口扫描器的主要关注点。本章早前的讨论强调了各种扫描类型以及如何使用它们来绕过过滤器。当你连接到位于直接连接网段的系统时，可以运行额外的脚本来进一步枚举。端口扫描从具有凭据的用户视角出发。`smb-enum-processes` 枚举 Windows 系统上的服务，并使用具有读取服务状态权限的用户凭据进行。这是一个远程查询 Windows 系统以确定确切服务列表的工具。命令的语法如下：

```
nmap --script smb-enum-processes --script-args smb-enum-processes.busername=<username>,smbpass=<password> -p445 <host>
```

### 通过数据包构造进行枚举

当涉及到通过数据包构造进行枚举时，Scapy 是我最喜欢的工具和框架之一。Scapy 是一个基于 Python 的全面数据包生成生态系统。本节介绍了使用该工具进行基础侦察的一些简单方法。

**提示**

Scapy 必须以 root 权限运行才能修改数据包。在终端中输入 `sudo scapy` 即可启动 Scapy 交互式 shell，如图 3-13 (ch03.xhtml#ch03fig13) 所示。示例 3-34 显示了开始构造有多简单。在这个示例中，构造了一个简单的 ICMP 数据包，并将 `malicious_payload` 作为有效负载发送到目标主机 `192.168.88.251`。

#### 示例 3-34 使用 Scapy 构造简单的 ICMP 数据包

点击此处查看代码图像

```
>>> send(IP(dst="192.168.88.251")/ICMP("malicious_payload"))
Sent 1 packets.
```

#### 图 13 从命令行启动 Scapy

示例 35 显示了目标系统 `192.168.88.225/vulnhost-1` 接收到的 ICMP 数据包。使用 `tshark` 数据包捕获工具捕捉构造的 ICMP 数据包。

#### 示例 35 使用 tshark 收集构造的数据包

点击此处查看代码图像

```
omar@vulnhost-1 % sudo tshark host 192.168.78.142
Capturing on 'eth0'
    1 0.00000000 192.168.78.142 ? 192.168.88.251 ICMP 60 Echo (ping)
  request  id=0x0000, seq=0/0, ttl=63
    2 0.000026929 192.168.88.251 ? 192.168.78.142 ICMP 59 Echo (ping)
    reply    id=0x0000, seq=0/0, ttl=64
```

Scapy 支持许多协议。你可以使用 `ls()` 函数列出所有格式和协议，如示例 3-36 所示。

### 示例 3-36 Scapy ls() 函数

点击此处查看代码图像

```
>>> ls()
AH          : AH
AKMSuite   : AKM
ARP         : ARP
ASN1P_INTEGER : None
ASN1P_OID  : None
ASN1P_PRIVSEQ : None
ASN1_Packet : None
ATT_Error_Response : Error Response
ATT_Exchange_MTU_Request : Exchange MTU Request
ATT_Exchange_MTU_Response : Exchange MTU Response
ATT_Execute_Write_Request : Execute Write Request
ATT_Execute_Write_Response : Execute Write Response
ATT_Find_By_Type_Value_Request : Find By Type Value Request
ATT_Find_By_Type_Value_Response : Find By Type Value Response
ATT_Find_Information_Request : Find Information Request
ATT_Find_Information_Response : Find Information Response
ATT_Handle : ATT Short
ATT_Handle_UUID128 : ATT Handle (UUID 128)
ATT_Handle_Value_Indication : Handle Value Indication
ATT_Handle_Value_Notification : Handle Value Notification
ATT_Handle_Variable : None
ATT_Hdr    : ATT header
ATT_Prepare_Write_Request : Prepare Write Request
<output omitted>
```

你可以使用 `ls()` 函数显示 Scapy 支持的特定协议或数据包的所有选项和字段，如示例 3-37 所示。此示例显示了 TCP 协议的可用字段。

#### 示例 3-37 在 Scapy 中列出 TCP 第四层字段

点击此处查看代码图像

```
>>> ls(TCP)
sport         : ShortEnumField                     = (20)
dport         : ShortEnumField                     = (80)
seq           : IntField                           = (0)
ack           : IntField                           = (0)
dataofs       : BitField  (4 bits)                 = (None)
reserved      : BitField  (3 bits)                 = (0)
flags         : FlagsField  (9 bits)               = (<Flag 2 (S)>)
window        : ShortField                         = (8192)
chksum        : XShortField                        = (None)
urgptr        : ShortField                         = (0)
options       : TCPOptionsField                    = (b'')
```

示例 3-38 显示了可以使用 Scapy 修改的 DNS 数据包字段。

```
>>> ls(DNS)
length      : ShortField (Cond)                 = (None)
id          : ShortField                        = (0)
qr          : BitField  (1 bit)                 = (0)
opcode      : BitEnumField  (4 bits)            = (0)
aa          : BitField  (1 bit)                 = (0)
tc          : BitField  (1 bit)                 = (0)
rd          : BitField  (1 bit)                 = (1)
ra          : BitField  (1 bit)                 = (0)
z           : BitField  (1 bit)                 = (0)
ad          : BitField  (1 bit)                 = (0)
cd          : BitField  (1 bit)                 = (0)
rcode       : BitEnumField  (4 bits)            = (0)
qdcount     : DNSRRCountField                   = (None)
ancount     : DNSRRCountField                   = (None)
nscount     : DNSRRCountField                   = (None)
arcount     : DNSRRCountField                   = (None)
qd          : DNSQRField                        = (None)
an          : DNSRRField                        = (None)
ns          : DNSRRField                        = (None)
ar          : DNSRRField                        = (None)
```

你可以使用 `explore()` 函数来遍历 Scapy 的层和协议。执行 `explore()` 函数后，屏幕将显示如图 3-14 所示。

![图 3-14 在 Scapy 中使用 explore() 函数](img/03fig14.jpg)

**图 3-14** 在 Scapy 中使用 `explore()` 函数

你可以对任何数据包格式或协议使用 `explore()` 函数。示例 3-39 展示了使用 `explore("dns")` 函数查看 `scapy.layers.dns` 中包含的数据包。

**示例 3-39** 使用 `explore("dns")` 函数显示 `scapy.layers.dns` 中的数据包类型

点击此处查看代码图像

```
>>> explore("dns")
Packets contained in scapy.layers.dns:
Class                      |Name
---------------------------|------------------------------
DNS                        |DNS
DNSQR                      |DNS Question Record
DNSRR                      |DNS Resource Record
DNSRRDLV                   |DNS DLV Resource Record
DNSRRDNSKEY                |DNS DNSKEY Resource Record
DNSRRDS                    |DNS DS Resource Record
DNSRRMX                    |DNS MX Resource Record
DNSRRNSEC                  |DNS NSEC Resource Record
DNSRRNSEC3                 |DNS NSEC3 Resource Record
DNSRRNSEC3PARAM            |DNS NSEC3PARAM Resource Record
DNSRROPT                   |DNS OPT Resource Record
DNSRRRSIG                  |DNS RRSIG Resource Record
DNSRRSOA                   |DNS SOA Resource Record
DNSRRSRV                   |DNS SRV Resource Record
DNSRRTSIG                  |DNS TSIG Resource Record
EDNS0TLV                   |DNS EDNS0 TLV
InheritOriginDNSStrPacket|
```

你可以通过许多不同的方式将 Scapy 作为扫描器使用。我的 GitHub 仓库中有几个使用 Scapy 执行网络和系统扫描的 Python 脚本示例；参见 [`github.com/The-Art-of-Hacking/h4cker/blob/master/python_ruby_and_bash`](https://github.com/The-Art-of-Hacking/h4cker/blob/master/python_ruby_and_bash)。不过，你可以对任何给定端口进行简单的 TCP SYN 扫描，如示例 3-40 所示。在此例中，向 IP 地址为 `192.168.88.251` 的主机发送了 TCP 445 端口 SYN 包。输出显示收到了一个答案，但没有指定具体的答案（响应）是什么。示例 3-41 显示了目标主机（192.168.88.251）上的数据包捕获。

**示例 3-40** 使用 Scapy 发送 TCP SYN 数据包

点击此处查看代码图像

```
>>> ans, unans = sr(IP(dst='192.168.88.251')/TCP(dport=445,
flags='S'))
Begin emission:
Finished sending 1 packets.
....*
Received 5 packets, got 1 answers, remaining 0 packets
>>>
```

**示例 3-41** 目标主机上的 TCP 数据包捕获

点击此处查看代码图像

```
omar@vulnhost-1 ~ % sudo tshark host 192.168.78.142
Running as user "root" and group "root". This could be dangerous.
Capturing on 'eth0'
    1 0.00000000 192.168.78.142
```
