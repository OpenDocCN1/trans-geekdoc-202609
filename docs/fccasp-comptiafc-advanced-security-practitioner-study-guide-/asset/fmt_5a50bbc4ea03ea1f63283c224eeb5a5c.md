
### IPv4 类别地址范围

| 类别 | 网络地址范围 | 网络数量 | 每网络主机数 |
| :--- | :--- | :--- | :--- |
| A | 1–126 | 126 | 16,777,214 |
| B | 128–191 | 16,384 | 65,534 |
| C | 192–223 | 2,097,152 | 254 |
| D | 224–239 | NA | NA |
| E | 240–255 | NA | NA |

![FIGURE 2.11 IPv6 header](images/c02f011.jpg)

**FIGURE 2.11** IPv6 header

**TABLE 2.2** IPv4 and IPv6 differences

| IPv4 | IPv6 |
| :--- | :--- |
| IPSec is an optional feature. | IPSec is built in. |
| IPv4 supports a header checksum. | Common routing protocols used are RIP-2 and OSPF. |
| IPv4 supports an Options field. | IPv6 does not support an Options field. |
| ARP is supported. | IPv6 uses neighbor discovery. |
| 32-bit addresses are used. | 128-bit addresses are used. |
| A broadcast is used. | An anycast is used. |
| IPv4 supports fragmentation. | IPv6 does not support fragmentation. |

**TABLE 2.3** Common ICMPv4 types and codes

| Type | Code | Function |
| :--- | :--- | :--- |
| 0/8 | 0 | Echo response/request (ping) |
| 3 | 0–15 | Destination unreachable |
| 4 | 0 | Source quench |
| 5 | 0–3 | Redirect |
| 11 | 0–1 | Time exceeded |
| 12 | 0 | Parameter fault |
| 13/14 | 0 | Time stamp request/response |
| 17/18 | 0 | Subnet mask request/response |

**TABLE 2.4** Common ICMPv6 functions and types

| Function | Code |
| :--- | :--- |
| Destination unreachable | 1 |
| Packet too large | 2 |
| TTL exceeded | 3 |
| ICMP echo request | 128 |
| ICMP echo reply | 129 |
| Multicast listener query | 130 |
| Multicast listener report | 131 |
| Multicast listener done | 132 |
| Router solicitation | 133 |
| Router advertisement | 134 |
| Neighbor solicitation | 135 |
| Neighbor advertisement | 136 |
| Redirect message | 137 |

## Transport Layer

The transport layer provides end-to-end delivery. Two primary protocols are located at the host-to-host layer: `TCP` and `UDP`.

### 1. TCP

`TCP` is designed for reliable communications. Its purpose is to allow hosts to establish a connection and exchange data reliably. `TCP` has built-in reliability: It performs a three-step handshake, it uses sequence and acknowledgment numbers, and it completes a four-step shutdown that gracefully concludes the session. `TCP` can also make use of a reset to kill communication should something go wrong. The startup sequence is shown in **FIGURE 2.12**.

At the heart of `TCP`'s reliable communication is a one-byte flag field. Flags help control the `TCP` process. Common flags include synchronize (`SYN`), acknowledge (`ACK`), push (`PSH`), and finish (`FIN`). `TCP` security issues include `TCP` sequence number attacks, session hijacking, and `SYN` flood attacks. Scanning programs tweak the `TCP` flags to attempt to identify active hosts or distinguish one operating system from another. **Exercise 2.5** shows you how to capture a `TCP` header with Wireshark.

### 2. UDP

**UDP** is built for speed. It has no startup or shutdown process like `TCP`. Although this makes **UDP** considerably less reliable than `TCP`, **UDP** is ideally suited for data that requires fast delivery and is not sensitive to packet loss. **UDP** is used by services like VoIP, streaming video, and DNS. **UDP** is easier for attackers to spoof than `TCP`, since it does not use sequence and acknowledgment numbers. **FIGURE 2.13** shows the packet structure of **UDP**.

![FIGURE 2.12 TCP startup](images/c02f012.jpg)

**FIGURE 2.12** TCP startup

![FIGURE 2.13 UDP header](images/c02f013.jpg)

**FIGURE 2.13** UDP header

## Application Layer

The application layer sits at the top of the protocol stack. The application layer is responsible for application support. Applications are typically mapped not by name but by their corresponding port. Ports are placed into `TCP` and `UDP` packets so the correct application can be passed to the required protocols.

Although a particular service may have an assigned port, nothing specifies that services cannot listen on another port. The primary reason services have assigned ports is so that a client can easily find that service on a remote host. For example, HTTP servers generally listen at `TCP` port 80 and sometimes `TCP` port 8080. Just as benevolent applications use specific ports, malicious applications often use predetermined ports as well. One infamous example is the use of `TCP` port 31337 by the Back Orifice Remote Access Tool (RAT). These Trojan ports were, of course, easily identified, but the Back Orifice RAT was a very powerful technology for its time, as was its successor, BO2K. New malware often attempts to obfuscate its traffic by using ports that are commonly used by legitimate applications. A prime example of this is the initial use of HTTP port 80 or SSL port 443 by the Mebroot rootkit. Client applications like FTP listen on port 21 and perform data transfer on port 20. There are 65,536 ports; they are divided into well-known ports (0–1023), registered ports (1024–49151), and dynamic ports (49152–65535).

There are hundreds of ports and corresponding applications, but in practice fewer than a hundred are in common use. The most common of these are shown in **TABLE 2.5**. These are some of the ports that a CASP should know.

**TABLE 2.5** Common ports and applications

| Port | Service | Protocol |
| :--- | :--- | :--- |
| 21 | FTP | TCP |
| 22 | SSH | TCP |
| 23 | Telnet | TCP |
| 25 | SMTP | TCP |
| 53 | DNS | TCP/UDP |
| 67/68 | DHCP | UDP |
| 69 | TFTP | UDP |
| 79 | Finger | TCP |
| 80 | HTTP | TCP |
| 88 | Kerberos | UDP |
| 110 | POP3 | TCP |
| 111 | SUNRPC | TCP/UDP |
| 135 | MS RPC | TCP/UDP |
| 139 | NB Session | TCP/UDP |
| 161 | SNMP | UDP |
| 162 | SNMP trap | UDP |
| 389 | LDAP | TCP |
| 443 | SSL | TCP |
| 445 | SMB over IP | TCP/UDP |
| 1433 | MS-SQL | TCP |

Practicing a “deny all” approach and blocking all ports that are not explicitly needed is one good approach to port security. If a port is not being used, it should be closed. Security is a never-ending process. Just because the port is closed today doesn't mean it will be closed tomorrow. You will want to test for open ports periodically. Not all applications are created equal. Although some, like SSH, are relatively secure, others, like Telnet, are not. The following list discusses the operation and security issues of some common applications:

### 1. File Transfer Protocol (FTP)

`FTP` is a `TCP` service and operates on port 20 and 21. `FTP` is a basic file transfer protocol. Port 20 is used for the data stream and transfers the data between the client and the server. Port 21 is the control stream and is used to pass commands between the client and the `FTP` server. Attacks on `FTP` target misconfigured directory permissions and compromised or sniffed clear-text passwords. `FTP` is widely targeted by hackers, and using a more secure variant such as FTPS, SFTP, or `FTP` over SSH is highly recommended.

### 2. Telnet

`Telnet` is a `TCP` service that operates on port 23. `Telnet` enables a client at one site to establish a session with a host at another site. The program passes the information typed at the client's keyboard to the host computer system. Although `Telnet` can be configured to allow anonymous connections, it should be configured to require usernames and passwords. Unfortunately, even then, `Telnet` sends the usernames and passwords in clear text. When users are logged in, they can perform any allowed task. Consider applications such as Secure Shell (`SSHv2`) as a replacement.
