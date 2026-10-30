
## TFTP

Trivial File Transfer Protocol (TFTP) is a file transfer protocol known for simplicity and lack of security mechanisms such as authentication. It uses UDP port 69, is designed only to read and write files, and typically is not used over the Internet.

## HTTP

The Hypertext Transfer Protocol (HTTP) is the application protocol that forms the basis of the Web. It uses TCP port 80 and operates on a client/server model involving hyperlinks and browser-rendered content from collections of referenced content.

## HTTPS

HTTPS is the use of SSL or TLS to encrypt a channel over which HTTP traffic is transmitted. This uses TCP port 443. HTTPS is the most widely used method to secure HTTP traffic.

## SCP

File transfers between systems can be accomplished via Secure Copy Protocol (SCP), which is an SSH-enabled file transfer mechanism. Because of its reliance on SSH, it uses TCP port 22.

## ICMP

Internet Control Message Protocol (ICMP) is the aspect of the Internet Protocol suite used for diagnostic, control, and error messaging. The most common ICMP traffic you are likely to encounter is ping, which is composed of an ICMP echo request and an ICMP echo reply. Optional in IPv4, ICMP is commonly blocked at the boundaries of a network because of a series of attack vectors that it enables, including ping floods and ping of death. In IPv6, ICMP is a must-carry component for the IP protocol to work end-to-end, meaning enterprises cannot block it at the network boundaries.

## IPv4

Internet Protocol version 4 (IPv4) is the most common version of the IP protocol in use today. It is characterized by a 32-bit address notation expressed in dotted quad notation in the form of X.X.X.X, where X can range from 0 to 255. IPv4 is used to route packets across the Internet and provides a wide range of services through a suite of associated protocols including ICMP, TCP, and UDP.

## IPv6

Internet Protocol version 6 (IPv6) is the replacement for IPv4. It uses a 128-bit address space, which represents approximately 3.4 × 10^38 addresses. IPv6 addresses can be expressed in eight groups of four hexadecimal digits, using colons as separators. IPv6 offers many features in addition to increased address space, including autoconfiguration, enhanced security, IPsec support, and enhanced multicast support. IPv6 is not interoperable with IPv4 and presents several challenges to network and security personnel. IPv6 is designed for host-to-host connections, making older systems such as NAT obsolete. It also presents challenges to security vendors, as the tools and techniques used to secure IPv4 do not work in the same fashion for IPv6.

## iSCSI

The Internet Small Computer System Interface (iSCSI) is a protocol for IP-based storage. iSCSI can be used to send data over existing network infrastructures, enabling storage area networks (SANs). Positioned as a low-cost alternative to Fibre Channel storage, the only real limitation is one of network bandwidth.

## Fibre Channel

Fibre Channel (FC) is a high-speed network technology (with throughput up to 16 Gbps) used to connect storage to computer systems. The FC protocol is a transport protocol similar to the TCP protocol in IP networks. Carried via special cables, one of the drawbacks of FC-based storage is cost.

## FCoE

The Fibre Channel over Ethernet (FCoE) protocol encapsulates the FC frames, enabling FC communication over 10-Gigabit Ethernet networks.

## Telnet

Telnet is a plaintext method of instantiating a command-line console to a remote machine. Telnet uses TCP port 23 and sends all transmissions in unencrypted form, making the traffic subject to eavesdropping. Telnet is an old protocol that has been used for decades, but it has been replaced by SSH due to security concerns.

## NetBIOS

NetBIOS is a separate naming scheme from DNS, used in older Windows systems. It uses TCP and UDP ports 137, 138, 139, and 445 over a local area network for things like file and printer sharing in Windows-based PCs. A frequent target for hackers, NetBIOS is largely obsolete and only found in older, smaller network environments.

## Ports

Services are referenced by ports under both TCP and UDP protocol stacks. Table 3-3 lists common port assignments relevant to the CompTIA Security+ exam requirements.

![](img/922567202a944c5e8d3ba0168d2ad3a5_98_0.png)

> EXAM TIP It is important to know the port numbers for common protocols.

**Table 3-3 Common TCP and UDP Port Assignments**

| Port | TCP Port Assignment | UDP Port Assignment |
|------|---------------------|---------------------|
| 21 | FTP |  |
| 22 | SSH |  |
| 25 | SMTP |  |
| 53 | DNS | DNS |
| 80 | HTTP |  |
| 110 | POP3 |  |
| 139 | NetBIOS |  |
| 143 | IMAP |  |
| 443 | HTTPS |  |
| 3389 | RDP | RDP |

## OSI Relevance

To organize the vast array of protocols into usable layers, the abstraction layers of the Open Systems Interconnection (OSI) model are useful. This enables one to quickly determine what protocols can be used with or encapsulated over other protocols. Table 3-4 illustrates the separation of the protocols by the OSI abstraction layers.

**Table 3-4 Protocols by OSI Layer**

| OSI Layer | Protocols |
|-----------|-----------|
| 7 – Application | DHCP, DNS, FTP, TFTP, SSH, LDAP, IMAP, POP3, Gopher, HTTP, NFS, NNTP, NTP, SIP, SSI, SMPP, SMTP, SNMP, Telnet |
| 6 – Presentation | MIME, XDR, EBCDIC, RDP |
| 5 – Session | Named Pipes, NetBIOS, PPTP, RTP, SAP, SOCKS, SPDY |
| 4 – Transport | DCCP, SCTP, SPX, TCP, UDP |
| 3 – Network | AppleTalk, IP (v4, v6), EGP, EIGRP, ICMP, IPsec, IGMP, IGRP, MPLS, IPX, X.25 |
| 2 – Data Link | ARP, ATM, Frame Relay, HDLC, IEEE 802.2, LLC, L2TP, PPP, PPTP, LLDP, STP, SDLC, SLIP, X.25 |
| 1 – Physical | Bluetooth, DSL, ADSL, ISDN, IEEE 1394, IEEE 802.3, IEEE 802.11, IEEE 802.15, IEEE 802.16, RS-232, RS-485, SONET/SDH, USB |

## Chapter Review

The chapter opened with an examination of how networks are segregated with design elements such as DMZs and subnets. The use of VLANs for traffic management and the security implications were examined, followed by Network Address Translation issues. The chapter continued through the concepts of remote access, network access control, telephony, and virtualization. Cloud computing was explored, both from the services provided, IaaS, SaaS, and PaaS, and from the cloud types, private, public, hybrid, and community. The chapter concluded with an examination of many of the common networking protocols and ports as well as the relevance of the OSI model.

## Questions

To help you prepare further for the CompTIA Security+ exam, and to test your level of preparedness, answer the following questions and then check your answers against the correct answers at the end of the chapter.

-   1. Which of the following servers would you be least likely to place in a DMZ?
-      A. Web server
-      B. DNS server
-      C. SMTP server
-      D. File server
-   2. Which network mask corresponds to a /31 prefix?
-      A. 255.255.255.0
-      B. 255.255.255.192
-      C. 255.255.255.248
-      D. 255.255.255.254
-   3. Match the items (one-to-one) from the column on the left with corresponding items on the right:
-      A. FTPS      1. Trunking
-      B. SSH       2. PBX
-      C. NAT       3. SSL/TLS
-      D. VLAN      4. SaaS
-                   5. TCP 22
-                   6. PAT

4. If you need multiple internal hosts to share a single external IP address, you might use:

-   - A. Destination Network Address Translation
-   - B. Port Address Translation
-   - C. Source Network Address Translation
-   - D. Dynamic Network Address Translation

5. Which of the following is not a remote-access method?

-   - A. Remote desktop software
-   - B. Terminal emulation
-   - C. SaaS
-   - D. Secure Shell

6. Network access control (NAC) is implemented:

-   - A. When devices initially attempt to access the network
-   - B. When devices change MAC addresses
-   - C. When devices change protocols
-   - D. When zero-day attacks are detected

7. When discussing virtualization, a snapshot is:

-   - A. The amount of resources used by a virtual machine at a given point in time
-   - B. The state of a virtual machine at an exact point in time
-   - C. The state of the virtual disks associated with a specific virtual machine
-   - D. The use of hardware emulation in a given virtual machine

8. Application delivery-only Platform as a Service (PaaS) offerings generally focus on:

-   - A. Security and scalability
-   - B. Development capabilities
-   - C. Allowing developers to use any programming language
-   - D. Subscription-based services

9. A company adopting an Infrastructure as a Service (IaaS) model would typically:

-   - A. Own the infrastructure equipment
-   - B. Be responsible for housing and maintaining equipment
-   - C. Only support networking infrastructure
-   - D. Pay on a per-use basis
