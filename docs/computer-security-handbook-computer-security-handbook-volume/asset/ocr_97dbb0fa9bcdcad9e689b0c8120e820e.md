Datagram Delivery Protocol (DDP). Apple dropped support for AppleTalk in 2009 and supports TCP/IP-based networking.

# Microsoft Networking.

Microsoft operating systems have come with LAN capabilities since Windows for Workgroups (WfW or Windows 3.11). Employing a nonroutable protocol called the Network Basic Input/Output System (NetBIOS) Extended User Interface (NetBEUI), Windows client systems (Windows 3.11 and later) can be easily used to build an inexpensive, simple peer-to-peer LAN for file and print sharing. NetBEUI is nonroutable because it does not provide an addressing mechanism to allow interconnected yet distinct NetBEUI subnetworks; if two NetBEUI networks are attached in any way, they will appear to be one large network. (This is why the hard drive of improperly configured Windows systems can be viewed from across the Internet.) Microsoft defined NetBIOS over TCP/IP (NBT) in the 1980s to support encapsulation of NetBIOS messages in TCP and UDP messages. Most Microsoft networking today relies more on TCP/IP than NetBEUI.

# Microsoft Windows Server (including Windows NT Server, Windows Server 2003, Windows Server 2008, and Windows Server 2012).

The NOS of choice for Windows network environments, Windows Server is Microsoft’s client/server operating system. Client systems can run nearly any Windows operating system, from Windows XP or NT Workstation to Windows VISTA, Windows 7, or Windows 8. Clients on a Windows Server network themselves can form a peer-to-peer network. Microsoft networking is reliant on Active Directory and TCP/IP.

# Novell NetWare.

Novell offered one of the first PC-class networks in the early 1980s using a proprietary star-based LAN. By the 1990s, NetWare was the best-known client/server NOS and accounted for more than 70 percent of the NOS market. The Network Layer protocol associated with classical NetWare is the Internetwork Packet Exchange (IPX) protocol. By the turn of the century, Microsoft was eating dramatically into NetWare’s popularity and TCP/IP was dominating as the protocol-of-choice. At around this time, Novell embraced Linux and TCP/IP, and NetWare has been replaced with the Open Enterprise Server.

# UNIX and Linux.

TCP/IP has been the network communications protocol for UNIX systems since 1984, allowing UNIX-based hosts to build client/server (and, ultimately, peer-to-peer) networks. TCP/IP has also been integral to Linux since its inception in 1991. With TCP/IP, any system can run server (daemon) software to provide services to other systems, so that any system can act as a client or server, depending on application.

# 6.8 SUMMARY.

Exhibit 6.17 shows a possible network design that includes many of the elements that have been described in this chapter (and a few that have not). This network’s router provides the interface to the Internet and is attached via some sort of dedicated connection, such as a point-to-point 56 Kbps or T1 (1.544 Mbps) leased line, frame relay, or digital subscriber line.

In this scenario, the router is physically located at the main site. From a security perspective, the organization may segment its network into an external and internal side, the internal being protected by a firewall.14 The external network includes the router, public Web server, and firewall. Those three systems are interconnected through