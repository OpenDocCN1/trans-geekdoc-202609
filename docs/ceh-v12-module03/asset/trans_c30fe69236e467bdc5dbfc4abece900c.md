
In addition, this scanning technique is slow because it limits the ICMP error message rate as a form of compensation to machines that apply RFC 1812 section 4.3.2.8. A remote host will require access to the raw ICMP socket to distinguish closed ports from unreachable ports.

此外，这种扫描技术很慢，因为它限制了 ICMP 错误消息速率，作为对应用 RFC 1812 第 4.3.2.8 节的机器的补偿形式。远程主机需要访问原始 ICMP 套接字来区分关闭的端口和不可达的端口。

## UDP RECVFROM () and WRITE () Scanning
## UDP RECVFROM() 和 WRITE() 扫描

Although non-root users cannot read unreachable port errors directly, Linux informs you indirectly when it receives messages.

虽然非 root 用户无法直接读取不可达端口错误，但 Linux 在接收到消息时会间接通知你。

### Example:
### 示例：
For example, a second write() call to a closed port will usually fail. Various scanners, such as Netcat and Pluvial pscan.c, perform recvfrom() on non-blocking UDP sockets, and they usually return EAGAIN ("Try Again," errno 11) if the ICMP error has not been received or ECONNREFUSED ("Connection refused," errno 111) otherwise. This technique is used for determining open ports when non-root users use -u (UDP). Root users can also use the -1 (lame UDP scan) option to force this process.

例如，对关闭端口的第二次 write() 调用通常会失败。各种扫描器，例如 Netcat 和 Pluvial pscan.c，在非阻塞 UDP 套接字上执行 recvfrom()，如果未收到 ICMP 错误，它们通常返回 EAGAIN（“Try Again”，errno 11），否则返回 ECONNREFUSED（“Connection refused”，errno 111）。当非 root 用户使用 -u（UDP）时，使用此技术来确定开放端口。root 用户还可以使用 -1（lame UDP scan）选项来强制此过程。

### Advantage:
### 优点：
The UDP scan is less intrusive with regard to an open port because there is no overhead of a TCP handshake. However, if ICMP is responding to each unavailable port, the total number of frames can exceed that from a TCP scan. Microsoft-based OSs do not usually implement any ICMP rate limiting; hence, this scan operates very efficiently on Windows-based devices.

UDP 扫描对开放端口的侵入性较小，因为没有 TCP 握手的开销。然而，如果 ICMP 对每个不可用的端口都作出响应，总帧数可能超过 TCP 扫描。基于 Microsoft 的操作系统通常不实现任何 ICMP 速率限制；因此，此扫描在基于 Windows 的设备上运行效率非常高。

### Disadvantage:
### 缺点：
The UDP scan provides port information only. If additional information of the version is needed, the scan must be supplemented with a version detection scan (-sV) or the OS fingerprinting option (-o).

UDP 扫描仅提供端口信息。如果需要版本等额外信息，则扫描必须辅以版本检测扫描（-sV）或操作系统指纹识别选项（-o）。

The UDP scan requires privileged access; hence, this scan option is only available on systems with the appropriate user permissions.

UDP 扫描需要特权访问；因此，此扫描选项仅在具有适当用户权限的系统上可用。

Most networks have massive amounts of TCP traffic; as a result, the efficiency of the UDP scan is low. The UDP scan will locate open ports and provide the security manager with valuable information for identifying successful attacker invasions on open UDP ports owing to spyware applications, Trojan horses, and other malicious software.

大多数网络都有大量的 TCP 流量；因此，UDP 扫描的效率较低。UDP 扫描将定位开放端口，并为安全管理员提供有价值的信息，以识别由于间谍软件应用程序、特洛伊木马和其他恶意软件对开放 UDP 端口的成功攻击者入侵。

## SCTP INIT Scan
## SCTP INIT 扫描

Stream Control Transport Protocol (SCTP) is a reliable message-oriented transport layer protocol. It is used as an alternative to the TCP and UDP protocols, as its characteristics are similar to those of TCP and UDP. SCTP is specifically used to perform multi-homing and multi-streaming activities. Some SCTP applications include discovering VoIP, IP telephony, and Signaling System 7/Signaling Transport (SS7/SIGTRAN)-related services. SCTP association comprises a four-way handshake method, as shown in the screenshot below.

流控制传输协议（SCTP）是一种可靠的消息导向传输层协议。它用作 TCP 和 UDP 协议的替代方案，因为其特性与 TCP 和 UDP 相似。SCTP 专门用于执行多宿主和多流活动。一些 SCTP 应用包括发现 VoIP、IP 电话和信令系统 7/信令传输（SS7/SIGTRAN）相关服务。SCTP 关联包括四次握手方法，如下图所示。

![](img/198108450322f24970ade227cbf24f47_63_0.png)

Figure 3.65: SCTP Association four-way handshake
图 3.65：SCTP 关联四次握手

In SCTP, the INIT scan is performed quickly by scanning thousands of ports per second on a fast network not obstructed by a firewall offering a stronger sense of security. The SCTP INIT scan is very similar to the TCP SYN scan; comparatively, it is also stealthy and unobtrusive, as it cannot complete SCTP associations, hence making the connection half-open.

在 SCTP 中，INIT 扫描通过在未受防火墙阻碍的快速网络上每秒扫描数千个端口来快速执行，提供更强的安全感。SCTP INIT 扫描与 TCP SYN 扫描非常相似；相比之下，它也具有隐蔽性和不显眼性，因为它无法完成 SCTP 关联，因此使连接处于半开状态。

Attackers send INIT chunk to the target host. If the port is listening or open, it sends an acknowledgement as an INIT+ACK chunk.

攻击者向目标主机发送 INIT 分块。如果端口正在监听或开放，则会作为 INIT+ACK 分块发送确认。

![](img/198108450322f24970ade227cbf24f47_63_1.png)

Figure 3.66: SCTP INIT scan result when a port is listening (Open)
图 3.66：端口正在监听（开放）时 SCTP INIT 扫描结果

If the target is inactive and it is not listening, then it sends an acknowledgement as an ABORT chunk.

如果目标处于非活动状态且未监听，则会作为 ABORT 分块发送确认。

![](img/198108450322f24970ade227cbf24f47_63_2.png)

Figure 3.67: SCTP INIT scan result when a port is not listening (Closed)
图 3.67：端口未监听（关闭）时 SCTP INIT 扫描结果

After several retransmissions, if there is no response, then the port is indicated as a filtered port. The port is also indicated as a filtered port if the target server responds with an ICMP unreachable exception (type 3, code 0, 1, 2, 3, 9, 10, or 13). In Zenmap, the -sY option is used to perform the SCTP INIT scan.

经过多次重传后，如果没有响应，则端口被指示为已过滤端口。如果目标服务器以 ICMP 不可达异常（类型 3，代码 0、1、2、3、9、10 或 13）响应，则端口也将被指示为已过滤端口。在 Zenmap 中，使用 -sY 选项执行 SCTP INIT 扫描。

### Advantages:
### 优点：
- INIT scan can clearly differentiate between various ports such as open, closed, and filtered states
- INIT 扫描可以清楚地区分各种端口，例如开放、关闭和过滤状态

![](img/198108450322f24970ade227cbf24f47_64_0.png)

Figure 3.68: SCTP INIT scan in Zenmap
图 3.68：Zenmap 中的 SCTP INIT 扫描

## SCTP COOKIE ECHO Scan
## SCTP COOKIE ECHO 扫描

SCTP COOKIE ECHO scan is a more advanced type of scan. In this type of scan, attackers send the COOKIE ECHO chunk to the target, and if the target port is open, it will silently drop the packets onto the port and you will not receive any response from the target. If the target sends back the ABORT chunk response, then the port is considered as a closed port. The COOKIE ECHO chunk is not blocked by non-stateful firewall rule sets as in the INIT scan. Only an advanced IDS can detect the SCTP COOKIE ECHO scan. In Zenmap, the -sZ option is used to perform the SCTP COOKIE ECHO scan.

SCTP COOKIE ECHO 扫描是一种更高级的扫描类型。在这种扫描中，攻击者向目标发送 COOKIE ECHO 分块，如果目标端口开放，它会静默丢弃发送到该端口的数据包，你将不会收到目标的任何响应。如果目标返回 ABORT 分块响应，则端口被视为关闭端口。与 INIT 扫描不同，COOKIE ECHO 分块不会被非状态防火墙规则集阻止。只有高级 IDS 才能检测到 SCTP COOKIE ECHO 扫描。在 Zenmap 中，使用 -sZ 选项执行 SCTP COOKIE ECHO 扫描。

![](img/198108450322f24970ade227cbf24f47_64_1.png)

Figure 3.69: SCTP COOKIE ECHO scan result when port is open
图 3.69：端口开放时 SCTP COOKIE ECHO 扫描结果

![](img/198108450322f24970ade227cbf24f47_65_0.png)

Figure 3.70: SCTP COOKIE ECHO scan result when port is closed
图 3.70：端口关闭时 SCTP COOKIE ECHO 扫描结果

### Advantages:
### 优点：
- The port scan is not as conspicuous as the INIT scan.
- 端口扫描不如 INIT 扫描那么显眼。

### Disadvantages:
### 缺点：
- SCTP COOKIE ECHO scan cannot differentiate clearly between open and filtered ports, and it shows the output as open|filtered in both cases.
- SCTP COOKIE ECHO 扫描无法清楚地区分开放和过滤端口，在两种情况下都显示输出为 open|filtered。

![](img/198108450322f24970ade227cbf24f47_65_1.png)

Figure 3.71: SCTP COOKIE-ECHO scan in Zenmap
图 3.71：Zenmap 中的 SCTP COOKIE-ECHO 扫描

## SSDP and List Scan
## SSDP 和列表扫描

### SSDP Scan
### SSDP 扫描
- The Simple Service Discovery Protocol (SSDP) is a network protocol that works in conjunction with the UPnP to detect plug and play devices
- Simple Service Discovery Protocol (SSDP) 是一种网络协议，与 UPnP 协同工作以检测即插即用设备
- Vulnerabilities in UPnP may allow attackers to launch Buffer overflow or DoS attacks
- UPnP 中的漏洞可能允许攻击者发起缓冲区溢出或 DoS 攻击
- Attacker may use the UPnP SSDP M-SEARCH information discovery tool to check if the machine is vulnerable to UPnP exploits or not
- 攻击者可能会使用 UPnP SSDP M-SEARCH 信息发现工具来检查机器是否容易受到 UPnP 利用

### List Scan
### 列表扫描
- This type of scan simply generates and prints a list of IPs/Names without actually pinging them
- 这种扫描类型只是生成并打印 IP/名称列表，而不实际 ping 它们
- A reverse DNS resolution is performed to identify the host names
- 会执行反向 DNS 解析以识别主机名

![](img/198108450322f24970ade227cbf24f47_66_0.png)

![](img/198108450322f24970ade227cbf24f47_66_1.png)

## SSDP and List Scan
## SSDP 和列表扫描

### SSDP Scan
### SSDP 扫描
Simple Service Discovery Protocol (SSDP) is a network protocol that generally communicates with machines when querying them with routable IPv4 or IPv6 multicast addresses. The SSDP service controls communication for the Universal Plug and Play (UPnP) feature. It generally works when the machine is not firewalled; however, it can sometimes work through a firewall. The SSDP service will respond to a query sent over IPv4 or IPv6 broadcast addresses. This response includes information about the UPnP feature associated with it. The attacker uses SSDP scanning to detect UPnP vulnerabilities that may allow him/her to launch buffer overflow or DoS attacks.

Simple Service Discovery Protocol (SSDP) 是一种网络协议，通常在用可路由的 IPv4 或 IPv6 组播地址查询机器时与机器通信。SSDP 服务控制通用即插即用（UPnP）功能的通信。它通常在机器未被防火墙保护时工作；然而，有时它也可以通过防火墙工作。SSDP 服务会响应通过 IPv4 或 IPv6 广播地址发送的查询。此响应包括与其关联的 UPnP 功能的信息。攻击者使用 SSDP 扫描来检测 UPnP 漏洞，这些漏洞可能允许他/她发起缓冲区溢出或 DoS 攻击。

![](img/198108450322f24970ade227cbf24f47_67_0.png)

Figure 3.72: UPnP SSDP M-SEARCH in Parrot Security
图 3.72：Parrot Security 中的 UPnP SSDP M-SEARCH

The attacker may use the UPnP SSDP M-SEARCH information discovery tool to check whether the machine is vulnerable to UPnP exploits. The UPnP SSDP M-SEARCH information discovery tool gleans information from UPnP-enabled systems, as shown in the figure.

攻击者可能会使用 UPnP SSDP M-SEARCH 信息发现工具来检查机器是否容易受到 UPnP 利用。UPnP SSDP M-SEARCH 信息发现工具从启用 UPnP 的系统收集信息，如图所示。

### List Scan
### 列表扫描
In a list scan, the discovery of the active network host is indirect. A list scan simply generates and prints a list of IPs/Names without actually pinging or scanning the hosts. As a result, the list scan shows all IP addresses as “not scanned” (0 hosts up). By default, a reverse DNS resolution is still carried out on each host by Nmap to learn their names. In Zenmap, the -sL option is used to perform a list scan.

在列表扫描中，活动网络主机的发现是间接的。列表扫描只是生成并打印 IP/名称列表，而不实际 ping 或扫描主机。因此，列表扫描将所有 IP 地址显示为“未扫描”（0 个主机启动）。默认情况下，Nmap 仍会对每个主机执行反向 DNS 解析以了解其名称。在 Zenmap 中，使用 -sL 选项执行列表扫描。

![](img/198108450322f24970ade227cbf24f47_68_0.png)

Figure 3.73: List scan using Zenmap
图 3.73：使用 Zenmap 进行列表扫描

### Advantages:
### 优点：
- A list scan can perform a good sanity check.
- 列表扫描可以进行良好的合理性检查。
- The list scan detects incorrectly defined IP addresses in the command line or in an option file. It primarily repairs the detected errors to run any “active” scan.
- 列表扫描检测命令行或选项文件中定义不正确的 IP 地址。它主要修复检测到的错误以运行任何“主动”扫描。

## IPv6 Scan
## IPv6 扫描
- IPv6 increases the IP address size from 32 bits to 128 bits to support more levels of address hierarchy
- IPv6 将 IP 地址大小从 32 位增加到 128 位，以支持更多级别的地址层次结构
- Attackers need to harvest IPv6 addresses from network traffic, recorded logs, or Received from: header lines in archived emails
- 攻击者需要从网络流量、记录日志或归档电子邮件中的 Received from: 标头行中收集 IPv6 地址
- Attackers can use the -6 option in Zenmap to perform IPv6 scanning
- 攻击者可以在 Zenmap 中使用 -6 选项执行 IPv6 扫描

![](img/198108450322f24970ade227cbf24f47_69_0.png)

```
root@ :~# nmap -6 scanme.nmap.org
Starting Nmap ( http://nmap.org ) at 04:25 UTC
Nmap scan report for scanme.nmap.org (2600:3c01::f03c:91ff:fe18:bb2f)
Host is up (0.062s latency).
Not shown: 997 closed ports
PORT      STATE SERVICE
22/tcp    open  ssh
80/tcp    open  http
31337/tcp open  Elite

Nmap done: 1 IP address (1 host up) scanned in 3.94 seconds
```

![](img/198108450322f24970ade227cbf24f47_69_1.png)

![](img/198108450322f24970ade227cbf24f47_69_2.png)

## IPv6 Scan
## IPv6 扫描

IPv6 increases the size of the IP address space from 32 bits to 128 bits to support higher levels of the addressing hierarchy. Traditional network scanning techniques are computationally less feasible because of the larger search space (64 bits of host address space, or 2^64 addresses) provided by IPv6 in a subnet. Scanning the IPv6 network is more difficult and complex compared to IPv4. Additionally, a number of scanning tools do not support ping sweeps on IPv6 networks. Attackers need to harvest IPv6 addresses from network traffic, recorded logs, or "Received from" and other header lines in archived email or Usenet news messages to identify IPv6 addresses for subsequent port scanning. However, scanning an IPv6 network provides a large number of hosts in a subnet; if an attacker can compromise one subnet host, he/she can probe the "all hosts" link local multicast address if the hosts numbers are sequential or use any regular scheme. An attacker needs to analyze 2^64 addresses to verify if a particular open service is running on a host in that subnet. At a conservative rate of one probe per second, such a scan would take about 5 billion years to complete. Attackers can use Nmap to perform IPv6 scanning. In Zenmap, the -6 option is used to perform the IPv6 scan.

IPv6 将 IP 地址空间的大小从 32 位增加到 128 位，以支持更高级别的寻址层次结构。由于 IPv6 在子网中提供的更大搜索空间（64 位主机地址空间，或 2^64 个地址），传统网络扫描技术在计算上不太可行。与 IPv4 相比，扫描 IPv6 网络更困难、更复杂。此外，许多扫描工具不支持 IPv6 网络上的 ping 扫描。攻击者需要从网络流量、记录日志或归档电子邮件或 Usenet 新闻消息中的“Received from”和其他标头行中收集 IPv6 地址，以便进行后续端口扫描。然而，扫描 IPv6 网络会在子网中提供大量主机；如果攻击者能够入侵一个子网主机，他/她可以探测“所有主机”链路本地组播地址，如果主机号是顺序的或使用任何常规方案。攻击者需要分析 2^64 个地址来验证子网中主机上是否运行特定开放服务。以每秒一次探测的保守速率计算，此类扫描大约需要 50 亿年才能完成。攻击者可以使用 Nmap 执行 IPv6 扫描。在 Zenmap 中，使用 -6 选项执行 IPv6 扫描。

```
root@ :~# nmap -6 scanme.nmap.org
Starting Nmap ( http://nmap.org ) at 04:25 UTC
Nmap scan report for scanme.nmap.org (2600:3c01::f03c:91ff:fe18:bb2f)
Host is up (0.062s latency).
Not shown: 997 closed ports
PORT      STATE SERVICE
22/tcp    open  ssh
80/tcp    open  http
31337/tcp open  Elite

Nmap done: 1 IP address (1 host up) scanned in 3.94 seconds
```

Figure 3.74: IPv6 Scan using nmap
图 3.74：使用 nmap 进行 IPv6 扫描
