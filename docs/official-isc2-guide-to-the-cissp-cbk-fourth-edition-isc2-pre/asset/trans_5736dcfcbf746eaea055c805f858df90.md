
- RFC 4034：DNS 安全扩展的资源记录
- RFC 4035：DNS 安全扩展的协议修改
- RFC 4470：最小覆盖 NSEC 记录与 DNSSEC 在线签名
- RFC 4592：通配符在域名系统中的作用
- RFC 5155：DNS 安全（DNSSEC）哈希认证的拒绝存在
- RFC 5452：提高 DNS 抵御伪造应答能力的措施
- RFC 6014：DNSSEC 加密算法标识符分配
- RFC 6604：xNAME RCODE 与状态位澄清
- RFC 6672：DNS 中的 DNAME 重定向
- RFC 6840：DNS 安全（DNSSEC）的澄清与实现说明
- RFC 6944：适用性声明：DNS 安全（DNSSEC）DNSKEY 算法实现状态

19 关于 LDAPv3 信息，请参阅以下 RFC：

详细说明轻量级目录访问协议（LDAP）第 3 版（一种互联网协议）的技术规范由本文档及以下文档组成：

- LDAP：轻量级目录访问协议（LDAP）：技术规范路线图 [RFC4510]
- LDAP：协议 [RFC4511]
- LDAP：目录信息模型 [RFC4512]
- LDAP：认证方法与安全机制 [RFC4513]
- LDAP：可分辨名称的字符串表示 [RFC4514]
- LDAP：搜索过滤器的字符串表示 [RFC4515]
- LDAP：统一资源定位符 [RFC4516]
- LDAP：语法与匹配规则 [RFC4517]
- LDAP：国际化字符串准备 [RFC4518]
- LDAP：用户应用模式 [RFC4519]

20 由于 NIS+ 提供的服务是安全关键的，NIS+ 被设计为安全运行。该设计的一个方面是“安全级别”的概念，它决定了对传入的 RPC NIS 请求进行审查的程度。共有三个安全级别，编号为 0 到 2。在级别 0，NIS+ 服务器（rpc.nisd）不执行任何身份验证来确定传入请求的合法性。此选项仅用于调试目的。在级别 1，使用 RPC AUTH_UNIX（客户端提供的 UID 和 GID）对请求进行身份验证。在级别 2（最安全的级别），使用 AUTH_DES 对传入请求进行加密身份验证。不幸的是，即使系统以安全级别 2 运行（该级别应要求对所有请求进行加密身份验证），rpc.nisd 守护进程仍提供多个未经身份验证的 RPC 调用。这些调用允许远程客户端从 NIS+ 服务器获取敏感的系统状态信息。远程攻击者可获取的信息包括 NIS+ 配置信息（包括服务器的安全级别及其提供的目录对象列表），以及确定 NIS+ 服务器上有效进程 ID 的能力。此外，远程客户端可用的 RPC 调用之一可能允许攻击者禁用 NIS+ 服务器上的日志记录，并操纵 NIS+ 缓存。这可能会使攻击者降低或拒绝 NIS+ 服务器的服务。能够使用 NIS+ 远程确定有效进程 ID 是严重的，因为它使攻击者能够预测 Unix 应用程序生成的某些随机数。通常，Unix 应用程序使用进程 ID 和当前时间（直接或作为随机数生成器的种子）生成随机数。

21 请参阅以下内容：http://jap.inf.tu-dresden.de/index_en.html  
22 http://www.inl.gov/technicalpublications/Documents/3375141.pdf （第 8 页）  
23 http://csrc.nist.gov/publications/nistir/ir7442/NIST-IR-7442_2007CSDAnnualReport.pdf  
24 有关横河安全咨询报告的全文，请参阅以下内容：  
http://www.yokogawa.com/dcs/security/ysar/YSAR-14-0001E.pdf  
25 http://ics-cert.us-cert.gov/sites/default/files/Monitors/ICS-CERT_Monitor_%20Jan-April2014.pdf  
26 请参阅以下内容：http://www.ietf.org/rfc/rfc3720.txt

以下是与 iSCSI 相关的其他 RFC 列表：

- RFC 3721 - 互联网小型计算机系统接口（iSCSI）命名与发现
- RFC 3722 - 互联网小型计算机系统接口（iSCSI）名称的字符串配置文件
- RFC 3723 - 通过 IP 保护块存储协议（范围：使用 IPsec 和 IKE 保护 iSCSI、iFCP、FCIP、iSNS 和 SLP v2。）
- RFC 3347 - 互联网上的小型计算机系统接口协议（iSCSI）要求与设计考虑
- RFC 3783 - 使用 iSCSI 时的小型计算机系统接口（SCSI）命令排序考虑
- RFC 3980 - iSCSI 节点名称的 T11 网络地址机构（NAA）命名格式
- RFC 4018 - 使用服务定位协议版本 2（SLPv2）发现互联网小型计算机系统接口（iSCSI）目标和名称服务器
- RFC 4173 - 使用互联网小型计算机系统接口（iSCSI）协议引导客户端
- RFC 4544 - 互联网小型计算机系统接口（iSCSI）托管对象定义
- RFC 4850 - 互联网小型计算机系统接口（iSCSI）节点架构的声明性公共扩展密钥
- RFC 4939 - iSNS（互联网存储名称服务）托管对象定义
- RFC 5048 - 互联网小型计算机系统接口（iSCSI）更正与澄清
- RFC 5047 - DA：互联网小型计算机系统接口（iSCSI）的数据移动器架构
- RFC 5046 - 用于远程直接内存访问（RDMA）的互联网小型计算机系统接口（iSCSI）扩展

27 转发信息库（FIB），也称为转发表，最常用于网络桥接、路由及类似功能中，以找到正确的接口，输入接口应将数据包发送到该接口以便路由器进行传输。

与路由信息库（RIB）（也称为路由表）相比，FIB 针对目标地址的快速查找进行了优化。早期的实现只缓存实际转发中最常使用的路由子集，这在拥有有意义的常用子集的企业中效果相当不错。

然而，用于访问整个互联网的路由器在刷新小型缓存时经历了严重的性能下降，因此各种实现改为让 FIB 与 RIB 一一对应。

RIB 针对路由协议和其他控制平面方法的高效更新进行了优化，并包含路由器学习到的全部路由。

FIB 也可以使用快速的硬件查找机制实现，例如三态内容寻址存储器（TCAM）。然而，TCAM 相当昂贵，而且它往往更多地用于路由数量相对较少的边缘路由器，而不是用于必须携带完整互联网路由表及补充内部路由的路由器。

RIB 至少包含三个信息字段：

1. 网络 ID：即目标网络 ID
2. 成本：即数据包发送所经路径的成本或度量值
3. 下一跳：下一跳或网关是数据包在到达最终目的地过程中要发送到的下一站的地址

28 请参阅以下内容：http://www.ietf.org/rfc/rfc2543.txt  
29 请参阅以下内容：http://www.ietf.org/rfc/rfc3361.txt  
30 请参阅以下内容：http://www.ietf.org/rfc/rfc3325.txt  
31 请参阅以下内容：http://community.arubanetworks.com/t5/Community-Tribal-Knowledge-Base/Analysis-of-quot-Hole-196-quot-WPA2-Attack/ta-p/25382  
32 http://tools.ietf.org/html/rfc6960  
33 “什么是堡垒主机？”，作者 Cory Janssen，访问于 2015 年 1 月 15 日，  
http://www.techopedia.com/definition/6157/bastion-host

34 TIA/EIA-568 是美国电信工业协会（TIA）制定的一套电信标准，TIA 是电子工业联盟（EIA）的一个分支。这些标准涉及电信产品和服务的商业建筑布线。截至 2014 年，该标准为 C 修订版，取代了现已过时的 2001 年 B 修订版、1995 年 A 修订版及 1991 年初始版本。TIA/EIA-568 最有名的特点也许是八导体 100 欧姆平衡双绞线布线的引脚/线对分配。这些分配分别命名为 T568A 和 T568B。IEC 标准 ISO/IEC 11801 为网络电缆提供了类似的标准。

35 请参阅以下内容：http://tools.ietf.org/html/rfc1918  
36 请参阅以下内容：  
http://tools.ietf.org/html/rfc3920  
http://www.ietf.org/rfc/rfc3921  
37 有关 Jabber 开发 SDK 和 API 的概述，请参阅以下内容：  
https://developer.cisco.com/site/collaboration/jabber/overview.gsp  
38 http://www.ietf.org/rfc/rfc1439  
39 http://tools.ietf.org/html/rfc3948  
40 http://tools.ietf.org/html/rfc2661  
41 有关 RADIUS 的完整 RFC 集，请参阅以下内容：  
http://tools.ietf.org/html/rfc2865  
http://tools.ietf.org/html/rfc3575  
http://tools.ietf.org/html/rfc5080  
http://tools.ietf.org/html/rfc6929  
42 有关 SNMP 的 RFC，请参阅以下内容：  
http://tools.ietf.org/html/rfc1157  
http://www.ietf.org/rfc/rfc3410  
http://www.ietf.org/rfc/rfc3411  
http://www.ietf.org/rfc/rfc3412  
http://www.ietf.org/rfc/rfc3413  
http://www.ietf.org/rfc/rfc3414  
http://www.ietf.org/rfc/rfc3415  
http://www.ietf.org/rfc/rfc3416  
http://www.ietf.org/rfc/rfc3417
