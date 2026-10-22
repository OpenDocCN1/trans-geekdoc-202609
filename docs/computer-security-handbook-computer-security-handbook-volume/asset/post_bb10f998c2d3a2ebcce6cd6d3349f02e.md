
- Are tapes and disks refinished or replaced before performance is degraded?
- Are air conditioners adequate for peak thermal loads? Are air conditioners backed up?
- Is there a schedule for frequent filter changes?
- Have all static electricity generators been disabled?
- Have all sources of water damage been eliminated?
- Is good housekeeping enforced throughout the facility?
- Is access to data terminals restricted?
- Are terminals and surrounding areas examined frequently to detect passwords carelessly left about?
- Is a log maintained of unsuccessful attempts to enter the computer from terminals?
- Is the log used to prevent further attempts?
- Is a log maintained of all successful entries to sensitive data?
- Is the log used to verify authorizations?
- Are terminals equipped with automatic identification generators?
- Are test procedures adequate to assure high-quality data transmissions?
- Is cryptography or scrambling used to protect sensitive data?
- Has a complete backup plan been formulated? Is it updated frequently?
- Does the backup plan include training, retraining, and cross-training of personnel?
- Is onsite backup available for the central processing unit? For peripherals?
- Does your backup site advise you of all changes to its hardware configuration and operating system?
- Does your backup site have enough free time available to accommodate your emergency needs?
- Do you monitor power-line voltage and frequency?
- Are the effects of brownouts, dim-outs, and blackouts known?
- Is advance warning available, and if so, is there a checklist of actions to be taken?
- Are power correctors in use? Voltage regulators? Line conditioners? Lightning spark gaps?
- Is backup power available? Dual substation supply? Motor generators? Uninterruptible power supplies?
- Does your equipment provide automatic restart and recovery after a power failure?
- Are backup plans tested realistically? At frequent intervals?

## Microcomputers

In addition to the appropriate items just listed:

- Are removable disks always kept in a closed container when not actually mounted in a disk drive?
- Is it forbidden to put food or drink on or near computer equipment?
- Are personal computers securely fastened to prevent dropping or theft?
- Are air vents kept free?
- Are accurate inventories maintained?
- Is electrical power properly wired?
- Are uninterruptible power supplies in place?
- Has static electricity been eliminated?
- Are data communications secure?
- Is there an effective maintenance plan?

## 4.16 FURTHER READING

Ayers, J. E. *Digital Integrated Circuits: Analysis and Design.* Boca Raton, FL: CRC Press, 2003. (Second edition scheduled for publication in 2009.)
Clements, A. *Principles of Computer Hardware*, 4th ed. New York: Oxford University Press, 2006.
Horak, R. *Telecommunications and Data Communications Handbook.* Hoboken, NJ: Wiley-Interscience, 2007.
Kerns, D. V. *Essentials of Electrical and Computer Engineering*, 2nd ed. Upper Saddle River, NJ: Prentice-Hall, 2004.
Patterson, D. A., and J. L. Hennessy. *Computer Organization and Design: The Hardware Software Interface*, 3rd ed. Los Angeles: Morgan Kaufmann, 2007.
Stallings, W. *Computer Organization and Architecture: Designing for Performance*, 7th ed. Upper Saddle River, NJ: Prentice-Hall, 2005.

## CHAPTER 5

## DATA COMMUNICATIONS AND INFORMATION SECURITY

Raymond Panko and Eric Fisher

- 5.1 INTRODUCTION 5.2
- 5.2 SAMPLING OF NETWORKS 5.2
- 5.2.1 Simple Home Network 5.2
- 5.2.2 Building LAN 5.4
- 5.2.3 Firms' Wide Area Networks (WANs) 5.5
- 5.2.4 Internet 5.7
- 5.2.5 Applications 5.9
- 5.3 NETWORK PROTOCOLS AND VULNERABILITIES 5.9
- 5.4 STANDARDS 5.9
- 5.4.1 Core Layers 5.10
- 5.4.2 Layered Standards Architectures 5.10
- 5.4.3 Single-Network Standards 5.11
- 5.4.4 Internetworking Standards 5.13
- 5.5 INTERNET PROTOCOL (IP) 5.14
- 5.5.1 IP Version 4 Packet 5.14
- 5.5.2 IP Version 6 5.16
- 5.5.3 IPsec 5.17
- 5.6 TRANSMISSION CONTROL PROTOCOL (TCP) 5.18
- 5.6.1 Connection-Oriented and Reliable Protocol 5.18
- 5.6.2 Reliability 5.20
- 5.6.3 Flag Fields 5.20
- 5.6.4 Octets and Sequence Number 5.21
- 5.6.5 Acknowledgment Numbers 5.21
- 5.6.6 Window Field 5.21
- 5.6.7 Options 5.21
- 5.6.8 Port Numbers 5.22
- 5.6.9 TCP Security 5.23
- 5.7 USER DATAGRAM PROTOCOL 5.23
- 5.8 TCP/IP SUPERVISORY STANDARDS 5.24
- 5.8.1 Internet Control Message Protocol (ICMP) 5.24
- 5.8.2 Domain Name System (DNS) 5.25
- 5.8.3 Dynamic Host Configuration Protocol (DHCP) 5.26
- 5.8.4 Dynamic Routing Protocols 5.27
- 5.8.5 Simple Network Management Protocol (SNMP) 5.27
- 5.9 APPLICATION STANDARDS 5.28
- 5.9.1 HTTP and HTML 5.28
- 5.9.2 E-Mail 5.28
- 5.9.3 Telnet, FTP, and SSH 5.28
- 5.9.4 Other Application Standards 5.29
- 5.10 CONCLUDING REMARKS 5.29
- 5.11 FURTHER READING 5.29
- 5.12 NOTES 5.29

## 5.2 DATA COMMUNICATIONS AND INFORMATION SECURITY

### 5.1 INTRODUCTION.

Sometimes, an attacker can simply walk up to a target computer. In most cases, however, attackers must use networks to reach their targets. Some attacks even aim at networks, trying to bring down local area networks, wide area networks, and even the global Internet. This chapter provides an overview of networking to help readers of this Handbook when they come across networking concepts in other chapters or in other contexts. This chapter covers a limited number of networking concepts. Specifically, it focuses on aspects of networking that are most relevant to security.

Before beginning, readers should note three important pieces of terminology that pervade the chapter.

- 1. This chapter often uses the term octet, which is a byte—a collection of eight bits. Networking grew out of electrical engineering, where octet is the preferred term; it is also widely used in the international technical community.
- 2. The second term is host. Any device attached to the global Internet is called a host. This includes everything from large server hosts to client PCs, personal digital assistants, mobile telephones, and even Internet-accessible coffeepots.
- 3. We will distinguish between the terms internet and Internet: the latter refers to the global Internet. However, internet spelled in lower case is either the Internet layer in the TCP architecture (see Section 5.6) or a collection of networks that is not the global Internet.

### 5.2 SAMPLING OF NETWORKS.

This section looks briefly at a series of increasingly complex networks, giving the reader a high-level overview of what networks look like in the real world.

### 5.2.1 Simple Home Network.

Exhibit 5.1 shows a simple home PC network. The home has two personal computers. The network allows the two PCs to share files and the family’s single laser printer. The network also connects the two computers to the Internet.

![](img/a2e2eee3c32fb4bb08c64c1d6efd2e39_161_0.png)

EXHIBIT 5.1 Simple Home Network

### 5.2.1.1 Access Router.

The heart of this network is its access router. This small device performs a variety of functions, most importantly these five:

- 1. It performs as a switch. When one PC in the home sends messages (called packets) to the other hosts, the switch transfers the packets between them.
- 2. The access router is a wireless access point (WAP), which permits wireless computers to connect to it. Host A connects to the access router wirelessly.
- 3. A router connects a network to another network—in this case, it connects the internal network to the global Internet.
- 4. To use the Internet, each computer needs an Internet Protocol (IP) address. We will see later that IP is the main protocol that governs communication over the Internet. The access router has a built-in Dynamic Host Configuration Protocol (DHCP) server that gives each home PC an IP address.
- 5. The router provides network address translation (NAT), which hides internal IP addresses from potential attackers. Most routers also have a firewall for added security. WAPs are easily exploited if not configured with proper authentication security. Wireless signals can be transferred up to 800 feet away or more with special equipment. Without constant monitoring to defeat intrusions, an attacker can connect to an access point without the user’s knowledge and intercept all passing traffic. Using NAT is essential to keeping a home network secure. Users should always enable this feature in order to prevent their hosts from being directly accessible to the public Internet, where direct scans and attacks are prevalent.

### 5.2.1.2 Personal Computers.

Each of the two PCs needs circuitry to communicate over the network. Traditionally, this circuitry came in the form of a printed circuit board, so the circuitry was called the computer’s network interface card (NIC). In most computers today, the circuitry is built into the computer; there is no separate printed circuit board. However, the circuitry is still called the computer’s NIC.

In this small network, the two computers share their files. Given the wireless access capability of the network, drive-by hackers could potentially read shared files as well. File sharing without strong wireless security is dangerous. It is important to set up Wi-Fi Protected Access (WPA or WPA2) or 802.11i security in pre-shared key (PSK) mode on both the access router/access point and each of the client PCs.

It is important to configure the PCs for security. Although NAT by itself is strong, and most routers also provide stateful-inspection firewalls (see Chapter 26 in this Handbook), some attacks will inevitably get through to the internal network. Hosts must have strong firewalls, antivirus programs, and antispyware programs (see Chapter 41); and they must be updated automatically when security patches are released by the operating system vendor and by application program vendors (see Chapter 40).

### 5.2.1.3 UTP Wiring.

In Exhibit 5.1, Host B connects to the access router via copper wiring called a UTP cable, Ethernet (IEEE 802.3) cable, or commonly Cat5 (Cat5 stands for Category 5 cabling, defined in standard ANSI/TIA/EIA-568-A). It uses four-pair unshielded twisted pair (UTP) wiring inside the cord jacket. As Exhibit 5.2 shows, a UTP cord contains eight copper wires organized as four pairs. The two wires of each pair are twisted around each other. The RJ-45 connectors at the ends of a UTP cord look like RJ-11 home telephone connectors but are a little wider. (RJ means
