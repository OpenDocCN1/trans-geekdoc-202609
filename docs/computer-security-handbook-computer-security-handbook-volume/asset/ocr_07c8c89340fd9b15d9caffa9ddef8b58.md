# 25.4 PHYSICAL LAYER ISSUES.

The LAN itself has a number of additional vulnerabilities because the systems and media are so widely dispersed. This section discusses securing the LAN infrastructure.

# 25.4.1 Sniffers and Broadcast LANs.

Traditional LAN media access control (MAC) schemes operate assuming a logical, if not physical, broadcast topology. In a broadcast network, every station hears every transmission. When operating in promiscuous mode, a LAN station will read every frame that goes by regardless of whether the frame is addressed to the station or not.

When protocol analysis, or sniffer, software became available in the 1980s, every station on the LAN became a potential network analysis and management tool—or a surreptitious eavesdropper. Since so many of the network’s applications—particularly Transmission Control Protocol/Internet Protocol (TCP/IP)-based applications—transmit passwords and files in plaintext, this type of software is potentially very dangerous.

A number of sources offer very powerful and very flexible commercial packet-sniffing software, such as Network Associates’ SnifferPro and Novell’s LANalyzer. These packages usually have additional capabilities, such as network monitoring, performance monitoring, and traffic analysis. Prior to 1990, network protocol analysis required a special piece of hardware with a connection to the network. Today, a large number of software packages that do TCP/IP packet sniffing can help an intruder because they can be installed directly on an individual’s laptop or desktop computer. Some of these packages include:

+   - WireShark (Windows, MacOS, and UNIX)
+   - BUTTsniffer (Windows NT)
+   - Network Monitor (free with, and for, Windows NT)
+   - Sniffit (Linux, SunOS, Solaris, FreeBSD, Irix)
+   - snort (UNIX and Windows)
+   - Solsniff (Solaris)
+   - tcpdump (MacOS and UNIX)
+   - WinDump (DOS)

Relatively few countermeasures can be taken against these kinds of tools. Fortunately, they are effective only on a broadcast network, such as a hubbed LAN. If an Ethernet hub, for example, is replaced with a switch, the only traffic broadcast to all hosts on the network are those frames actually addressed to the LAN’s broadcast address. In this case, a station can sniff only that traffic that is going to or coming from the station with the sniffer software. Replacing all hubs with switches may be unreasonable in many environments, but placing all servers on a switch instead of a hub will improve both performance and security.

Other network-based tools that can detect a host with a network interface card (NIC) in promiscuous mode, such as AntiSniff (Windows) and sentinel (UNIX). These tools work by performing a number of tests to detect the promiscuous host; they then check the network host’s operating systems, domain name system (DNS) activity, and network and machine latency.

Sniffers can be defeated using cryptography. Use of secure IP (IPsec) and Secure Shell (SSH) for TCP/IP applications can provide privacy and integrity to all