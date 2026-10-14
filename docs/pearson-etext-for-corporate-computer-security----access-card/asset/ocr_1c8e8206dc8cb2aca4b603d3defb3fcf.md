# A.2 A Sampling of Networks

This section looks briefly at a series of increasingly complex networks, giving the reader an overview of what networks are like in the real world.

# A Simple Home Network

Figure A-1 shows a simple home PC network. The home has two personal computers. The network allows the two PCs to share files and the family’s single laser printer. The network also connects the two computers to the Internet.

**THE ACCESS ROUTER** The heart of this network is its **access router**. This small device, which is about the size of a hardback book, has several functions:

+   - First, it is a switch. When one PC in the home sends messages (called frames) to the other PC, the switch transfers the frames between them.
+   - Second, the access router has a wireless access point that serves wireless computers. The upstairs computer is a wireless computer.
+   - Third, the access router is a true router. A router connects a network to another network; in this case, it connects the home network to the global Internet.
+   - Fourth, the access router has a Dynamic Host Configuration Protocol (DHCP) server. To use the Internet, each host needs an IP (Internet Protocol) address. The access router’s DHCP server gives each home PC an IP address.
+   - Fifth, the access router provides network address translation (NAT), which hides internal IP addresses from potential attackers. Some access routers also have a static packet inspection (SPI) firewall for added security.

> Wireless access points are dangerous because the radio signals they emit spread widely. If the user does not configure strong security on the access point and on all wireless stations, anyone will be able to read the traffic and do other mischief.
> 
> NAT provides a surprisingly large amount of protection automatically. Even people with one PC may find it attractive to use an access router to gain this protection.
> 
> It is important to configure computers for security. Although NAT by itself is strong and a growing number of access routers also provide stateful packet inspection firewalls, some attacks will inevitably get through to computers. The PCs in the home must have strong PC firewalls, antivirus programs, and antispyware programs. Such programs also must be updated whenever security patches are released by operating system vendors or application program vendors.

**PERSONAL COMPUTERS** Each of the two PCs in Figure A-1 needs circuitry to communicate over the network. Traditionally, this circuitry came in the form of a separate printed circuit board, so the circuitry was called the computer’s network interface card (NIC). In most computers today, the networking circuitry is built into the computer; there is no separate printed circuit board. However, the circuitry is still called the computer’s NIC.

**UTP WIRING** The downstairs PC connects to the access router via copper wiring. Specifically, it uses **4-pair unshielded twisted pair (UTP)** wiring. As Figure A-2 shows, a UTP cord contains eight copper wires organized as four pairs. The two wires of each pair are twisted around each other several times an inch to reduce interference.