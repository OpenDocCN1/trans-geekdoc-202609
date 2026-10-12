
## Chapter 12: Network Security

1.  **A.** The original implementation of SSL stripping attacks relied heavily on unencrypted HTTP connections, and the updated version of SSLStrip+ continues to leverage HTTP connections, and then adds the ability to rewrite HTTPS links to HTTP links, allowing it even greater access to unencrypted links. DNSSEC and ARP are not involved in this technique.

2.  **C.** A honeynet is a group of systems that intentionally exposes vulnerabilities so that defenders can observe attacker behaviors, techniques, and tools to help them design better defenses.

3.  **B.** Telnet provides remote command-line access but is not secure. SSH is the most common alternative to telnet, and it operates on port 22.

4.  **A.** Broadcast storms occur when broadcast packets are received and retransmitted by switches in a network, amplifying the traffic and causing heavy traffic loads. Spanning Tree Protocol, loop prevention features, and limited VLAN sizes can all reduce the potential for a broadcast storm. Disabling ARP on a network is not a recommended solution for a TCP/IP network.

5.  **D.** Unfortunately, BGP does not have native security methods, and BGP hijacks continue to appear in the news. Two solutions, SIDR and RPLS, have not been broadly adopted.

6.  **D.** The Windows `pathping` tool is specifically designed to show the network latency and loss at each step along a route. The `tracert` tool identifies the path to a remote system, and the `route` command can be used to view, add, and delete routes. `traceroute` is used in Linux, not Windows.

7.  **A.** The `arp` command will show the system's ARP cache using the `/a` flag on Windows systems. Other flags are `/d` to delete the cache or a single address if one is supplied, and `/s`, which will allow you to add an entry. In most cases, security professionals will use the `/a` flag most frequently to see what exists in an ARP cache on a system.

8.  **C.** `tcpdump` is a command-line tool that will allow Bart to capture and analyze the traffic coming from the Windows workstation. If he does not see a three-way handshake, he will need to determine what is occurring with the traffic. Wireshark is a GUI (graphical) program, `tcpreplay` is used to replay traffic, and `dd` is used to clone drives.

9.  **D.** Transport Layer Security (TLS) is commonly used to wrap (protect) otherwise insecure protocols. In fact, many of the secure protocols simply add TLS to protect them. ISAKMP and IKE are both used for IPSec and can be used to wrap insecure protocols, but they aren't used alone. SSL is no longer used; TLS has almost entirely replaced it, although SSL is still often casually referred to as TLS.

10.  **A.** The secure version of LDAP runs on TCP port 636. IMAPS runs on 993, SRTP runs on UDP 5004, and SNMPv3 runs on the standard UDP 161 and 162 ports used for all versions of the protocol.

11.  **D.** None of the protocols listed will accomplish Randy's task. In fact, there is no secure DHCP or ARP version, and secure LDAP does not impact DHCP services.

12.  **C.** End users may use secure POP (POPS), secure IMAP (IMAPS), and secure HTTP (HTTPS) to retrieve email. SPF, DKIM, and DMARC are used to identify and validate email servers, not to access email by end users.

13.  **C.** IPv6 does not include network address translation (NAT) because there are so many IP addresses available. That means that there is not a NAT implementation, and thus, IPv6 can't have an insecure version. Rules based on static IPv6 addresses may not work since dynamic addresses are heavily used in IPv6 networks, reputation services remain relatively rare and less useful for IPv6 traffic, and IPv6 traffic may bypass many existing IPv4 security tools.

14.  **B.** Active/active designs spread traffic among active nodes, helping to ensure that a single node will not be overwhelmed. Active/passive designs are useful for disaster recovery and business continuity, but they do not directly address heavy load on a single node. There are many load-balancing schemes, but daisy chains and duck, duck, goose are not among them.

15.  **A.** Agent-based, pre-admission NAC will provide Isaac with the greatest amount of information about a machine and the most control about what connects to the network and what can impact other systems. Since systems will not be connected to the network, even to a quarantine or pre-admission zone, until they have been verified, Isaac will have greater control.

16.  **C.** Although `tcpdump` can be used to view packets sent as part of a VoIP connection, Wireshark has built-in VoIP analysis and protocol-specific tools. Danielle will have greater success using those built-in tools. A network SIPper is a made-up tool, and `netcat` is not a packet sniffer.

17.  **B.** Man-in-the-browser attacks take advantage of malicious browser plug-ins or proxies to modify traffic at the browser level. They do not involve compromised routers or servers, and a modified hosts file is more likely to be involved in a man-in-the-middle attack.

18.  **A.** The Secure Real-Time Transfer Protocol is used for media streaming in many VoIP implementations. UDP/S is not an actual protocol, S/MIME is used for email, and SFTP is a replacement for FTP and is not typically associated with VoIP systems.

19.  **A.** DNSSEC does not encrypt data but does rely on digital signatures to ensure that DNS information has not been modified and that it is coming from a server that the domain owner trusts. DNSSEC does not protect confidentiality, which is a key thing to remember when discussing it as a security option. TLS, an IPSec VPN, or encryption via AES are all potential solutions to protect the confidentiality of network data.

20.  **C.** Out-of-band management places the administrative interface of a switch, router, or other device on a separate network or requires direct connectivity to the device to access and manage it. This ensures that an attacker who has access to the network cannot make changes to the network devices. NAC and port security help protect the network itself, whereas trunking is used to combine multiple interfaces, VLANs, or ports together.

## Chapter 13: Wireless and Mobile Security

1.  **B.** A hardware security module (HSM) in a microSD form factor allows a mobile device like an Android phone to securely store and manage certificates. Alyssa will also need an application to access and use the HSM, but she will have a complete, portable, and secure solution for her PKI needs. SEAndroid allows mandatory access control to be enforced on an Android device. TPMs are connected to systems and are often integrated into the motherboard or added as plug-in module, not a wireless component. MDM is not a secure hardware solution, but it is a software solution for managing mobile devices.

2.  **D.** Using a containerization system can allow Fred's users to run corporate applications and to use corporate data in a secure environment that cannot be accessed by other applications outside of the container on the device. Containerization schemes for mobile devices typically use encryption and other isolation techniques to ensure that data and applications do not cross over. Biometrics and context-aware authentication are useful for ensuring that the right user is using a device but don't provide this separation. Full-device encryption helps reduce the risk of theft or loss of a device resulting in a data breach.
