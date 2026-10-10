
# 术语表

## Internet layer
**Internet layer** TCP/IP层，负责处理从一台计算机到另一台计算机的通信。它接受来自传输层的发送数据请求。Internet层由两个协议组成：Internet Protocol（IP）和Internet Control Message Protocol（ICMP）。

## Internet Message Access Protocol (IMAP)
**Internet Message Access Protocol (IMAP)** 类似于POP的协议，允许客户端从邮件服务器检索消息。（IMAP已迭代至第四版，即IMAP4。）IMAP允许为将邮件存储在邮件服务器以外的位置而检索电子邮件。IMAP可与Microsoft Outlook配合使用，以检索电子邮件并将其存储在本地PC的数据文件中。

## Internet Protocol (IP)
**Internet Protocol (IP)** 一种通用协议，建立跨网络传输数据的机制。为TCP/IP套件内的所有其他协议提供数据包传递服务。

## Internet Protocol (IP) address
**Internet Protocol (IP) address** 在网络上唯一标识一台计算机。IPv4地址长32位，采用点分十进制表示法。IPv6地址长128位，采用十六进制格式。

## Internet Protocol Security (IPSec)
**Internet Protocol Security (IPSec)** 一种安全协议，旨在加密IP流量并执行认证服务。

## internetwork
**internetwork** 网络的网络，如Internet。中继器、网桥和路由器是用于将各个LAN链接在一起以形成更大internetwork的设备。*另请参阅* [bridge](#ch23_glossary.xhtml#glos43) *和* [router](#ch23_glossary.xhtml#glos320)。

## intrusion detection system (IDS)
**intrusion detection system (IDS)** 检测可疑活动并通知管理员的设备或软件。

## intrusion prevention system (IPS)
**intrusion prevention system (IPS)** 检测可疑活动、采取纠正措施并通知管理员的设备或软件。

## IP
**IP** *参见* [Internet Protocol](#ch23_glossary.xhtml#glos197)。

## ipconfig
**ipconfig** 一种Windows命令行工具，用于查看和排查TCP/IP设置。

## kernel
**kernel** 也称为微内核，指操作系统中的核心代码。这是操作系统最重要的部分，负责系统上的所有功能，如创建、管理和调度线程。

## kernel mode
**kernel mode** 也称为特权模式，可直接访问硬件。过去作为用户模式组件运行的某些Windows组件现在作为内核模式组件运行。这些组件包括Windows Manager、Graphics Device Interface（GDI）和图形设备驱动程序。

## key distribution center (KDC)
**key distribution center (KDC)** Kerberos中的一项服务，负责提供会话票据。

## kilobits per second (Kbps)
**kilobits per second (Kbps)** 每秒1024位的数据传输速度。

## lag
**lag** 网络性能下降，通常由对可用带宽的需求增加引起。

## LAN
**LAN** *参见* [local area network](#ch23_glossary.xhtml#glos215)。

## lease duration
**lease duration** 指定DHCP客户端可以使用IP地址的时长，超过此时限必须向DHCP服务器续租。此期限可设置为无限期或预定期限。您可以选择将作用域配置为为DHCP客户端保留特定IP地址，甚至为网络上未启用DHCP的系统保留地址。

## least significant bit
**least significant bit** 组成字节的8位中最右边的位。注意，组成字节的8位中最左边的位称为*most significant bit*。

## lmhosts file
**lmhosts file** 位于客户端硬盘驱动器上的文本文件，有助于将NetBIOS名称映射到IP地址。

## load
**load** 网络上存在的数据量。也称为网络流量。

## local area network (LAN)
**local area network (LAN)** 由任意两台或更多计算机组成，它们连接在一起以在小范围内（通常不超过单栋建筑）进行通信。*另请参阅* [virtual local area network](#ch23_glossary.xhtml#glos397)。

## local groups
**local groups** 位于Windows系统本地SAM数据库中的组，用于分配对该系统资源的权限。

## log off (or log out)
**log off (or log out)** 按照终止与系统会话的过程操作。

## log on (or log in)
**log on (or log in)** 按照登录网络的过程操作，以便访问文件和其他网络信息。当您有权访问网络时，即称为已登录。

## loopback address
**loopback address** 任何以`127.x.x.x`开头的地址，用于验证TCP/IP软件栈已加载并在系统上正常运行。

## MAC
**MAC** *参见* [Media Access Control](#ch23_glossary.xhtml#glos226)。

## MAC address
**MAC address** 也称为硬件地址，是一个12位十六进制数（由数字0-9和字母A-F组成），分配给网卡。地址由两部分组成：第一部分标识供应商；第二部分是该网卡唯一的序列号。考试中无需了解这些数字如何细分，只需知道该地址是什么即可。

## mandatory access control (MAC)
**mandatory access control (MAC)** 基于员工的许可级别和分配给资源的数据分类标签来控制资源访问。

## mandatory logon
**mandatory logon** Windows用于强制用户在授予系统访问权限前登录的机制。

## mantrap
**mantrap** 两扇门之间的区域，第二扇门在第一扇门关闭前不会打开。Mantrap旨在防止有人在您开门后尾随潜入设施。

## media access card
**media access card** *参见* [network interface card](#ch23_glossary.xhtml#glos252)。

## Media Access Control (MAC)
**Media Access Control (MAC)** 数据链路层的一个子层，决定哪台计算机可以发言以及何时发言。

## megabits per second (Mbps)
**megabits per second (Mbps)** 每秒1,048,576位的通信速率，用于测量吞吐量或通信速度。

## member server
**member server** 属于域一部分但未安装Active Directory的Windows服务器。

## memory
**memory** 信息的临时存储空间。物理内存是RAM（随机存取存储器）；虚拟内存是充当额外RAM的硬盘空间。

## Microsoft Challenge Handshake Authentication Protocol (MS-CHAP)
**Microsoft Challenge Handshake Authentication Protocol (MS-CHAP)** 一种Challenge Handshake Authentication Protocol形式，使用与父协议相同的加密方法，但安全性略高。服务器向发起主机发送质询，后者必须返回用户名、质询字符串的MD4哈希、会话ID以及MD4哈希后的密码。

## Microsoft Message Analyzer
**Microsoft Message Analyzer** 微软提供的数据包嗅探工具。Microsoft Message Analyzer已取代Microsoft Network Monitor。

## MIME
**MIME** *参见* [Multipurpose Internet Mail Extensions](#ch23_glossary.xhtml#glos239)。

## mirroring
**mirroring** 将信息复制到另一块硬盘。如果一块硬盘故障，另一块硬盘可立即提供完全相同的信息。

## modem
**modem** *参见* [modulator/demodulator](#ch23_glossary.xhtml#glos235)。

## modulator/demodulator (modem)
**modulator/demodulator (modem)** 一种设备，用于将计算机的数字信号转换为可通过电话线传输的模拟信号。也称为数据电路终接设备。

## most significant bit
**most significant bit** 组成字节的8位中最左边的位。另请注意，8位值中最右边的位称为*least significant bit*。

## MS-CHAP
**MS-CHAP** *参见* [Microsoft Challenge Handshake Authentication Protocol](#ch23_glossary.xhtml#glos230)。

## multihomed system
**multihomed system** 配置了多个网络适配器的计算机。

## Multipurpose Internet Mail Extensions (MIME)
**Multipurpose Internet Mail Extensions (MIME)** 一种Internet协议，允许电子邮件消息包含文本、音频、视频和图像等不同形式的数据。

## NAT
**NAT** *参见* [Network Address Translation](#ch23_glossary.xhtml#glos249)。

## NBTSTAT
**NBTSTAT** 一种实用程序，用于排查NetBIOS名称与IP地址之间的名称解析问题。

## NetBIOS
**NetBIOS** *参见* [Network Basic Input/Output System](#ch23_glossary.xhtml#glos250)。
