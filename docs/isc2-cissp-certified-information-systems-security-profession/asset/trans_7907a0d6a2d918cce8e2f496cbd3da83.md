
地址和命名是网络通信的重要组成部分。没有地址方案，网络计算机将无法区分一个计算机与另一个计算机，也无法指定通信的目的地。同样，没有命名方案，人类就必须记住并依赖数字编号系统来识别计算机。因此，记住 `Google.com` 要比记住 `64.233.187.99` 容易得多。因此，大多数命名方案是为人类使用而设计的，而非为计算机使用。

合理理解在 TCP/IP 网络中使用的地址和编号的基本概念是很重要的。需要关注三个不同的层次。这里按逆序列出，因为第三层是最基础的：

*   第三层，也就是底层，是 MAC 地址。MAC 地址，或称硬件地址，是一个“永久”的物理地址。

*   第二层，也就是中间层，是 IP 地址。IP 地址是一种“临时”的逻辑地址，它在 MAC 地址之上或之中被分配。

*   顶层是域名。域名或计算机名是一种“临时”的、面向人类的友好约定，它在 IP 地址之上被分配。

这种命名和地址体系为每个网络组件提供所需的信息，并尽可能简化其使用。人类获得友好的域名，网络协议获得路由友好的 IP 地址，网络接口获得物理地址。然而，这三种方案必须相互链接，以实现互操作性。因此，开发了 `Domain Name System (DNS)` 和 ARP 系统，分别在域名与 IP 地址之间，以及 IP 地址与 MAC 地址之间进行交换或解析。DNS 将人类友好的域名解析为其对应的 IP 地址。然后，ARP 将 IP 地址解析为对应的 MAC 地址。如果在 DNS 中配置了 PTR 记录（见本章后续关于“Domain Name System”的说明），也可以通过 DNS 反向查找将 IP 地址解析为域名。

DNS 是一种层次化的命名方案，适用于公共网络和私有网络。DNS 将 IP 地址与人类友好的 `fully qualified domain names (FQDNs)` 关联在一起。一个 FQDN 由三个主要部分组成：

*   `Top-level domain (TLD)`——例如 `com` 在 `www.google.com` 中。

*   `Registered domain name`——例如 `google` 在 `www.google.com` 中。

*   `Subdomain(s)` 或 `hostname`——例如 `www` 在 `www.google.com` 中。

TLD 可以是官方选项的任意数量，包括六个原始 TLD——`com`、`org`、`edu`、`mil`、`gov`、`net`——以及许多新的 TLD，如 `info`、`museum`、`telephone`、`mobi`、`biz` 等。还有被称为 `country codes` 的国家变体（详见 `www.iana.org/domains/root/db/` 以获取当前 TLD 和国家代码的详细信息）。注意，原始的第七个 TLD `int`（国际）已被两位字母的国家代码取代。

注册的域名必须向任何一个获准的域名注册商（如 Network Solutions 或 `1and1.com`）进行官方登记。

FQDN 的最左侧部分可以是单个主机名（如 `www`、`ftp` 等），也可以是多层次子域名（如 `server1.group3.bldg5.mycompany.com`）。

FQDN 的总长度不能超过 253 个字符（包括点号），每个单独部分不能超过 63 个字符。FQDN 只能包含字母、数字和连字符。

每个注册域名都有一个授权的权威名称服务器。`primary authoritative name server`（主权威名称服务器）保存该域的原始区域文件。`Secondary authoritative name servers`（次要权威名称服务器）可用于保存区域文件的只读副本。`zone file`（区域文件）是 `resource records`（资源记录）的集合，描述特定域的详细信息。虽然有数十种可能的资源记录（见 `List of DNS record types`），但最常见的列在 `Table 11.6` 中。

[**TABLE 11.6**](#c11.xhtml#tableanchor11-6) **Common resource records**

| Record || Type || Description |
| --- | --- | --- |
| A || Address record || Links an FQDN to an IPv4 address |
| --- | --- | --- |
| AAAA || Address record || Links an FQDN to an IPv6 address |
| PTR || Pointer record || Links an IP address to a FQDN (for reverse lookups) |
| CNAME || Canonical name || Links an FQDN alias to another FQDN |
| MX || Mail exchange || Links a mail- and messaging-related FQDN to an IP address |
| NS || Name server record || Designates the FQDN and IP address of an authorized name server |
| SOA || Start of authority record || Specifies authoritative information about the zone file, such as primary name server, serial number, time-outs, and refresh intervals |

最初，DNS 通过静态本地文件 `HOSTS file` 处理。该文件仍然存在，但动态 DNS 查询系统已取代了它，尤其是在大型私有网络以及互联网中。当客户端软件指向 FQDN 时，协议栈会发起 DNS 查询，以将名称解析为可用于构建 IP 头的 IP 地址。解析过程首先检查本地 DNS 缓存，看是否已经知道答案。本地 DNS 缓存包含从本地 HOSTS 文件预加载的内容以及在当前启动会话期间（未过期）执行的任何 DNS 查询。如果缓存中没有所需答案，就会将查询发送到本地 IP 配置中指定的 DNS 服务器。虽然解析过程有趣且复杂，但大部分内容与 (ISC)² CISSP 考试无关。

DNS 通过 TCP 和 UDP 端口 53 运行。TCP 端口 53 用于区域传输，即 DNS 服务器之间的区域文件交换，用于特殊手动查询或当响应超过 512 字节时。UDP 端口 53 用于大多数常规 DNS 查询。

`Domain Name System Security Extensions (DNSSEC)` 是对现有 DNS 基础设施的安全增强。DNSSEC 的主要功能是为 DNS 操作提供设备间可靠的认证。DNSSEC 已在 DNS 系统的大部分区域得到实现。每个 DNS 服务器都会获得一个数字证书，用于进行双向证书认证。DNSSEC 的目标是防止在解析过程中注入错误数据的各种滥用行为。一旦完全实施，DNSSEC 将显著降低服务器导向的 DNS 滥用。

#### DNS Poisoning

`DNS poisoning` 是篡改客户端用于定位目标系统的 DNS 信息的行为。它可以通过多种方式发生。每当客户端需要将 DNS 名称解析为 IP 地址时，它可能会经历以下过程：

1.  检查本地缓存（其中包含 HOSTS 文件的内容）。

2.  向已知的 DNS 服务器发送 DNS 查询。

3.  向可能存在的本地子网 DNS 服务器发送广播查询。（此步骤不常被支持。）

如果客户端未能从上述任何步骤获得 DNS 到 IP 的解析，则解析失败，通信无法发送。DNS 中毒可以在上述任何步骤发生，但最容易的方式是篡改 HOSTS 文件或 DNS 服务器查询。

攻击或利用 DNS 的方式有很多。攻击者可能会使用以下技术之一：

