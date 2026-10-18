
# 4.2.3. NAT

Network address translation (NAT) is primarily used to allow local IP address to share a public IPv4 address. Given the lack of IPv4 address space many devices have to share a single address. As mentioned when discussing IPv6, NAT routers often also include security features such as a stateful firewall as the complexity of the hardware required to perform NAT is equivalent to what would be needed for a firewall.

# 4.2.4. IPsec

Internet Protocol Security (IPsec) is used to set up a point-to-point encryption tunnel to secure data in transit across IP networks. IPsec is used primarily in dedicated VPN links and makes use of three main parts: SA, ESP, and AH:

SA stands for security association and is a channel used to set up encryption parameters and exchange keys. This happens via UDP on port 500.ESP stands for encapsulating security protocol and is used to encrypt IP headers and payloads. It is sent using standard IP packets with the protocol field set to 50.AH stands for authentication header and they can optionally be used in standard IP packets with the protocol field set to 51. AH simply ensures that a packet hasn’t been tampered with.

# 4.3. Transport Layer Protocols

## 4.3.1. TCP

Transmission Control Protocol (TCP) is at the heart of most networks. It provides for reliable communication via a three way hand shake, breaks large data segments into packets, ensures data integrity, and provides flow control for those packets. This all comes at a cost of course, and this connection-oriented protocol typically has higher latency than its counterparts. Given the complex nature of TCP is has often been targeted for attacks. TCP stacks are constantly adapting and changing (within the parameters of the protocol) to avoid DoS and MitM attacks.

## 4.3.2. UDP

User Datagram Protocol (UDP) is a connectionless protocol designed for instances where TCP may have too much latency. UDP achieves this performance boost by not having handshaking or flow control. The result is a speedy protocol that sometimes drops datagrams. UDP is often used as the basis for gaming or streaming protocols where the timing of the packets is more important that whether or not they all arrive. UDP does still employ checksums so you can be sure of the integrity of any UDP packets that you do receive.

## 4.3.3. Common Ports and Services

Port numbers are used in a transport layer connection to specify which service to connect to. This allows a single host to have multiple services running on it. Ports 0 to 1023 are well-known ports and typically support a commonly used service. In most operating systems it takes administrative privileges to bind to a Well-known port and listen for connections. Registered ports range from 1024 to 49151 and do not require administrative privileges to run a service on. You may find many things listening on these ports as any user can have a service on them. Lastly ports 49152 to 65535 are used dynamically by applications as needed.

It is important to know some commonly used ports as the services running on these ports may be subject to an attack. When scanning a machine, only necessary ports should be open.

| Port Number | L4 Protocol | Usage |
|-------------|-------------|-------|
| 20 | TCP | File Transfer Protocol (FTP) Data Transfer |
| 21 | TCP | FTP Command Control |
| 22 | TCP | Secure Shell (SSH) |
| 23 | TCP | Telnet Remote Login Service |
| 25 | TCP | Simple Mail Transfer Protocol (SMTP) E-Mail |
| 53 | TCP, UDP | Domain Name System (DNS) |
| 67, 68 | UDP | Dynamic Host Configuration Protocol (DHCP) |
| 69 | UDP | Trivial File Transfer Protocol (TFTP) |
| 80 | TCP | Hypertext Transfer Protocol (HTTP) |
| 110 | TCP | Post Office Protocol (POP3) E-Mail |
| 119 | TCP, UDP | Network News Transfer Protocol (NNTP) |
| 123 | UDP | Network Time Protocol (NTP) |
| 137-139 | TCP, UDP | NetBIOS |
| 143 | TCP | Internet Message Access Protocol (IMAP) E-Mail |
| 161, 162 | TCP, UDP | Simple Network Management Protocol (SNMP) |
| 194 | TCP, UDP | Internet Relay Chat (IRC) |
| 389 | TCP, UDP | Lightweight Directory Access Protocol (LDAP) |
| 443 | TCP | HTTP Secure (HTTPS) HTTP over TLS/SSL |
| 3389 | TCP, UDP | Microsoft Terminal Server (RDP) |

# 4.4. Application Layer Protocols

## 4.4.1. DHCP

Dynamic Host Configuration Protocol (DHCP) is used to allow new clients on a network to obtain an IP address and information about services provided. IPv4 addresses can be thought of as being in two groups: static addresses and dynamic addresses. Dynamic addresses are distributed by a DHCP server for a particular lease time. When the time is up, the DHCP server may distribute the address to another client. DHCP servers can also give information about proxies, Domain Name Servers (DNS), gateways and even where to get a where to get a kernel to boot an OS over the network!

Given the dynamic nature of modern networks, with clients coming and going, DHCP is the standard. From a security standpoint someone impersonating a DHCP server can wreak havoc on a network. These rogue DHCP servers can cause traffic to be redirected to initiate MitM attacks or cause DoS attacks. DHCP relies on broadcast Address Resolution Protocol (ARP) messages and does not make use of authentication, meaning that once an attacker is on the same Ethernet segment as the victim machines all bets are off.

## 4.4.2. HTTP

Hypertext Transfer Protocol (HTTP) is a text based protocol that governs how web traffic moves. It is built on the concept of a request and a response. A typical request has an method and a path, such as GET /index.html which would retrieve the landing page of a website. Responses have a code, message, and optionally data. Some standard responses are shown below:

| Code | Message |
|------|---------|
| 200 | OK |
| 202 | Accepted |
| 400 | Bad Request |
| 401 | Unauthorized |
| 403 | Forbidden |
| 404 | Not Found |
| 500 | Internal Server Error |
| 502 | Bad Gateway |
| 503 | Service Unavailable |

Both requests and responses can take advantage of headers, arbitrary lines of text following the initial request or response. Since headers were designed to be open-ended, many new headers have been added over time. A modern web request/response usually has far more information in the headers than just the basics defined in HTTP 1.1. Unencrypted HTTP traffic is sent over port 80 and is vulnerable to attack as all information is sent in cleartext.

## 4.4.3. SSL/TLS

Secure Sockets Layer (SSL) or the more modern nomenclature Transport Layer Security (TLS) is a protocol that allows cleartext protocols used on the web to be encrypted. It is a general purpose protocol, designed as a layer through which other protocols communicate. Some protocols typically wrapped in TLS include HTTP, SMTP, IMAP, VoIP, and many VPN protocols. TLS uses a handshake to exchange certificate information as shown in the diagram. It should be noted that at the time of writing TLS 1.3 is the most current version, but only half of websites support it. TLS 1.2, the most common version, is still considered safe if best practices are followed and TLS 1.1 or lower is considered depreciated.

## 4.4.4. HTTPS

HTTPS “icon” by Sean MacEntee used under CC-BY 2.0.

Hypertext Transfer Protocol Secure (HTTPS) solves the problem of unencrypted traffic by wrapping HTTP requests in TLS. HTTPS traffic uses port 443 and is typically signified in a browser with a lock icon in the upper left-hand corner. By clicking on the icon users can learn more about the certificates being used for communication. Utilizing a robust PKI HTTPS allows for safe HTTP communication between client and server.

## 4.4.5. RDP

Remote Desktop Protocol (RDP) is build into Windows and is typically used to control a machine remotely. It works over port 3389 via TCP or UDP. While RDP can be quite useful for performing remote administration on a remote machine, it can also be a large security hole if a bad actor gains access. RDP use in ransomware attacks is on the rise as ransomware programs may use RDP to find other machines to attack.

## 4.4.6. Telnet

Telnet is an antiquated remote administration tool that gives access to a shell via a cleartext channel. Telnet runs on port 23 and while still occasionally in use it should largely be phased out. You will still find telnet in embedded applications and legacy systems. You may also see the client being used to inspect other types of traffic. For example, you can use a telnet client to submit HTTP requests or send email via SMTP.

## 4.4.7. SSH

Secure Shell (SSH) is the most widely deployed remote administration tool. SSH provides access to a shell via an encrypted connection. SSH supports many options including SOCKS5 proxies, port forwarding, and the usage of multiple authentication schemes: password, key, hardware device, etc. SSH uses TCP on port 22.

## 4.4.8. LDAP

Lightweight directory access protocol (LDAP) is used for accessing and maintaining directory information services. It’s primary use is with Windows Active Directory (AD) where it can be used to obtain information regarding users and resources from an AD server. Clients can authenticate through the server and obtain privileges to read or read/write certain entries. LDAP did not originally support encryption, so LDAP over SSL (LDAPS) was developed. LDAP uses TCP and UPD over port 389 and LDAPS uses TCP over port 636.

## 4.4.9. DNS

Domain Name System (DNS) is used to resolve domain names to IP addresses. Domain names are the simple names people are accustomed to for websites, such as njit.edu as opposed to 54.83.189.142. Names are significantly easier for people to remember than IP addresses. In order for a computer to resolve a name, it first queries a local cache, then its primary DNS server. Assuming the DNS server cannot find the name it will query a Root server for a Top Level Domain (TLD) server, which maintains a listing of Authoritative Nameservers for that particular domain (edu, com, net, org, gov, etc.). Finally once an authoritative nameserver is found it will respond with the IP address for that particular hostname which will be cached and sent back through the user’s primary DNS server to the user.

DNS is designed to be resilient and decentralized but unfortunately the traffic is not authenticated or encrypted. This has made it a target for MitM attacks. Likewise cache hits and misses can yield information as to what names have been recently resolved (as was the case in discovering the extent of the Sony Rootkit). The recursive nature has of DNS has also allowed for DoS attacks in the past, but much of that has been solved by limiting recursive queries to the user-facing DNS servers (ie. the one given to you by your DHCP request). DNS operates via UDP (and occasionally TCP) on port 53.

## 4.4.10. DNSSEC

Domain Name System Security Extensions (DNSSEC) is a suite of extension specifications designed to authenticate responses to domain name lookups. This can help prevent MitM attacks by checking the digital signature of the responding server. While this is certainly helpful, it is important to note that DNSSEC does not provide confidentiality. DNS resolutions can still be monitored by anyone who has access to the traffic.

## 4.4.11. IMAP/POP3

Internet Message Access Protocol (IMAP) and Post Office Protocol 3 (POP3) are two protocols used to retrieve email from a server. IMAP is the more recent protocol which supports saving mail on the sever and folders. POP3 is more primitive, supporting only the retrieval (and subsequent deletion from the server) of emails. Both protocols use cleartext and are now commonly run over TLS. POP3 defaults to TCP port 110 or 995 if using TLS. IMAP defaults to TCP port 143 or 993 if using TLS. In the age of webmail it is easy to forget about these protocols, but a security specialist must keep them in mind as they may still be used in support of corporate devices.

## 4.4.12. SMTP

Simple Mail Transfer Protocol is used for sending/forwarding email. As it states, it is a simple protocol consisting of lines of text. Basic SMTP used TCP on port 25. SMTP was later expanded to support authentication and finally wrapped in TLS still using TCP on port 587. SMTP servers accept outgoing mail from (hopefully) authenticated clients, route mail to other SMTP servers based on the Mail Exchange (MX) information in DNS records, and accept mail for their domain from other SMTP servers. Various checks have been implemented in SMTP servers to ensure that messages from domains actually come from those domains. This is largely used to combat spam, which continues to be a problem.

## 4.4.13. NTP

Network Time Protocol uses UDP over port 123 to sync the system time with a time server. NTP servers are layered in stratums, with the lowest stratums being closest to the most accurate sources of time, atomic clocks, GPS, etc. NTP is important as many protocols, including several key exchanges, require system clocks to be in sync. System clocks are also used to check when certificates expire and used in logs to indicate when something happened. Without an accurate, synchronized system clock many things will fail in surprising ways.

## 4.4.14. FTP

File Transfer Protocol is a relatively simple, text-based protocol for sending files between machines. FTP uses TCP on port 21 and traditionally establishes two channels: one for protocol messages, and one binary channel for data. The interesting thing about this setup is that the FTP server would initiate the connection of the data channel from server to client, meaning that in many NAT situations where the client couldn’t be easily reached behind a firewall it would fail. The solution to this problem was passive FTP which uses one channel established by the client.

Despite this initial shortcoming, FTP has proven to be incredibly popular and is still used in many corporate environments. You may see FTP being used to transmit bulk data for import to systems or used to update firmware in embedded systems. You can use FTP with a commandline client, ftp, a graphical client such as Filezilla or SecureFX, or even in most web browsers with the ftp:// URL scheme.

Unfortunately FTP does not support authentication systems other than passwords and the passwords are sent in plaintext. As such Secure FTP (SFTP) is recommended. SFTP uses an SSH connection to send and receive files over an encrypted channel. SFTP also supports all SSH authentication methods.

## 4.4.15. SNMP

SNMP by Deegii121314 used under CC-BY-SA 4.0

Simple Network Management Protocol is used for gathering information about the workings of a network. It is broken into two groups: clients using UDP port 161 (TLS 10161) and a manager using UDP port 162 (TLS 10162). The manager collects messages from the clients regarding the operations of the network and uses this information to take actions as necessary. SNMP can be used to pass information about the temperature of a machine, how many connections it currently has, the channel capacity currently being utilized, etc. SNMP is currently up to version 3 which is encrypted and requires authentication. This is particularly important because SNMP is a very powerful protocol which exchanges information that could potentially be very valuable to an attacker. Access to SNMP should be limited and its usage on a network should be monitored.

# 4.5. Lab: Scanning with nmap

For this lab we will start by downloading and extracting the files required. Download nmap.zip and extract it to a directory you can access from the shell. Open a shell in that directory (it should have a docker-compose.yml in it and a victim and scanner directory). Since we will be simulating multiple machines in this lab, we will make use of Docker Compose which was already installed with Docker. Docker Compose reads a docker-compose.yml file which should already be in your nmap directory. Run docker-compose up --build --detach to build and run the images in the background:

```
PS C:\Users\rxt1077\temp\nmap> docker-compose up --build --detach
```
