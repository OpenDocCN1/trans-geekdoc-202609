
# UDP

UDP is the User Datagram Protocol, a simpler and faster cousin to TCP. UDP has no handshake, session, or reliability: it is informally called “Send and Pray” for this reason. UDP has a simpler and shorter 8-byte header (shown in [Fig. 5.9](#Ch005_225-293_B9780443187346000039.xhtml#f0050)), compared to TCP’s default header size of 20 bytes. UDP header fields include source IP, destination IP, packet length (header and data), and a simple (and optional) checksum. If used, the checksum provides limited integrity to the UDP header and data. Unlike TCP, data usually is transferred immediately, in the first UDP packet. UDP operates at Layer 4.

![Fig. 5.9 UDP header [7].](images/B9780443187346000039/f05-09-9780443187346.jpg)

[Fig. 5.9](#Ch005_225-293_B9780443187346000039.xhtml#B-f0050) UDP header [\[7\]](#Ch005_225-293_B9780443187346000039.xhtml#bb0040).

UDP is commonly used for applications that are “lossy” (can handle some packet loss), such as streaming audio and video. It is also used for query-response applications, such as DNS queries.

## ICMP

ICMP is the Internet Control Message Protocol, a helper protocol that helps Layer 3 (IP, see note). ICMP is used to troubleshoot and report error conditions: Without ICMP to help, IP would fail when faced with routing loops, ports, hosts, or networks, etc., that are down. ICMP has no concept of ports, as TCP and UDP do, but instead uses types and codes. Commonly used ICMP types are echo request and echo reply (used for ping) and time to live exceeded in transit (used for traceroute).

> **Note**
>
> “Which protocol runs at which layer” is often a subject of fierce debate. We call this the “bucket game.” For example, which bucket does ICMP go into: Layer 3 or Layer 4? ICMP headers are at Layer 4, just like TCP and UDP, so many will answer “Layer 4.” Others argue ICMP is a Layer 3 protocol, since it assists IP (a Layer 3 protocol), and has no ports.
>
> This shows how arbitrary the bucket game is: a packet capture shows the ICMP header at Layer 4, so many network engineers will want to answer “Layer 4”: never argue with a packet. The same argument exists for many routing protocols: for example, BGP is used to route at Layer 3, but BGP itself is carried by TCP (and IP). This book will cite clear-cut bucket game protocol/layers in the text and self-tests, but avoid murkier examples (just as the exam should).

### Ping

*Ping* (named after sonar used to “ping” submarines) sends an ICMP Echo Request to a node and listens for an ICMP Echo Reply. Ping was designed to determine whether a node is up or down.

Ping was a reliable indicator of a node’s status on the ARPAnet or older Internet, when firewalls were uncommon (or did not exist). Today, an ICMP Echo Reply is a fairly reliable indicator that a node is up. Attackers use ICMP to map target networks, so many sites filter types of ICMP such as Echo Request and Echo Reply.

An unanswered ping (an ICMP Echo Request with no Echo Reply) does not mean a host is down. The node may be down, or the node may be up and the Echo Request or Echo Reply may have been filtered at some point.

### Traceroute

The *traceroute* command uses ICMP Time Exceeded messages to trace a network route. As discussed during IP, the Time to Live field is used to avoid routing loops: every time a packet passes through a router, the router decrements the TTL field. If the TTL reaches zero, the router drops the packet and sends an ICMP Time Exceeded message to the original sender.

Traceroute takes advantage of this TTL feature in a clever way. Assume a client is four hops away from a server: the client’s traceroute client sends a packet to the server with a TTL of 1. The router A decrements the TTL to 0, drops the packet, and sends an ICMP Time Exceeded message to the client. Router A is now identified.

The client then sends a packet with a TTL of 2 to the server. Router A decrements the TTL to 1 and passes the packet to router B. Router B decrements the TTL to 0, drops it, and sends an ICMP Time Exceeded message to the client. Router B is now identified. This process continues until the server is reached, as shown in [Fig. 5.10](#Ch005_225-293_B9780443187346000039.xhtml#f0055), identifying all routers along the route.

![Fig. 5.10 Traceroute.](images/B9780443187346000039/f05-10-9780443187346.jpg)

[Fig. 5.10](#Ch005_225-293_B9780443187346000039.xhtml#B-f0055) Traceroute.

Most traceroute clients (such as UNIX and Cisco) send UDP packets outbound. The outbound packets will be dropped, so the protocol does not matter. The Windows `tracert` client sends ICMP packets outbound; [Fig. 5.11](#Ch005_225-293_B9780443187346000039.xhtml#f0060) shows Windows `tracert` output for a route to [www.syngress.com](http://www.syngress.com). Both client types usually send three packets for each hop (the three “ms” columns in the [Fig. 5.11](#Ch005_225-293_B9780443187346000039.xhtml#f0060) output).

![Fig. 5.11 Windows tracert to www.syngress.com.](images/B9780443187346000039/f05-11-9780443187346.jpg)

[Fig. 5.11](#Ch005_225-293_B9780443187346000039.xhtml#B-f0060) Windows tracert to [www.syngress.com](http://www.syngress.com).

# Application Layer TCP/IP Protocols and Concepts

A multitude of protocols exist at TCP/IP’s Application Layer, which combines the Session, Presentation, and Application Layers of the OSI model.

## Telnet

Telnet provides terminal emulation over a network. “Terminal” means text-based VT100-style terminal access. Telnet servers listen on TCP port 23. Telnet was the standard way to access an interactive command shell over a network for over 20 years.

Telnet is weak because it provides no confidentiality; all data transmitted during a telnet session is plaintext, including the username and password used to authenticate to the system. Attackers who can sniff network traffic can steal authentication credentials this way.

Telnet also has limited integrity: attackers with write access to a network can alter data, or even seize control of Telnet sessions. Secure Shell (SSH) provides secure authentication, confidentiality, and integrity and is a recommended replacement for Telnet.

## FTP

FTP is the File Transfer Protocol, used to transfer files to and from servers. Like Telnet, FTP has no confidentiality or integrity and should not be used to transfer sensitive data over insecure channels.

> **Note**
>
> When discussing insecure protocols such as Telnet and FTP, statements like “no confidentiality” assume that they are used with default settings, with no additional hardening or encryption (such as using them via an IPsec VPN tunnel). You may mitigate the lack of confidentiality by using Telnet or FTP over an encrypted VPN tunnel or using SSH in their place, among other options. Also, “no integrity” means there is limited or no integrity at the application layer: some integrity may be provided at a lower layer, such as the transport layer.

FTP uses two ports: the control connection (where commands are sent) is TCP port 21; “Active FTP” uses a data connection (where data is transferred) that originates from TCP port 20. Here are the two socket pairs (the next two examples use arbitrary ephemeral ports):

*   Client:1025 → Server:21 (Control Connection)
*   Server:20 → Client:1026 (Data Connection)

Notice that the data connection originates from the server, in the opposite direction of the control channel. This breaks classic client-server data flow direction. Many firewalls will block the active FTP data connection for this reason, breaking Active FTP. Passive FTP addresses this issue by keeping all communication from client to server:

*   Client:1025 → Server:21 (Control Connection)
*   Client:1026 → Server:1025 (Data Connection)

The FTP server tells the client which listening data connection port to connect to; the client then makes a second connection. Passive FTP is more likely to pass through firewalls cleanly, since it flows in classic client-server direction.

## TFTP
