# 238 CHAPTER 5 Domain 4: Communication and Network Security

192.168.2.122. Hosts may access IPv6 networks via IPv4; this is tunneled. Another IPv6 address worth noting is the loopback address: ::1. This is equivalent to the IPv4 address of 127.0.0.1.

# IPv6 Security Challenges

IPv6 solves many problems, including adding sufficient address space and autoconfiguration, making routing much simpler. Some of these solutions, such as autoconfiguration, can introduce security problems.

An IPv6-enabled system will automatically configure a link-local address (beginning with fe80::...) without the need for any other IPv6-enabled infrastructure. That can communicate with other link-local addresses on the same LAN. This is true if the administrators are unaware that IPv6 is flowing on their network.

ISPs are also enabling IPv6 service, sometimes without the customer's knowledge. Modern network tools, such as network intrusion detection systems, can “see” IPv6, but are often not configured to do so. And many network professionals have limited experience or understanding of IPv6. From an attacker's perspective, this can offer a golden opportunity to launch attacks or exfiltrate data via IPv6.

All services that are not required be disabled is a fundamental part of system hardening. If IPv6 is not required, it should be disabled. To disable IPv6 on a Windows host, open the network adapter, and choose properties. Then uncheck the “Internet Protocol Version 6” box, as shown in Fig. 5.4.

# Classful Networks

The original IPv4 networks (before 1993) were “classful,” classified into classes A through E. Classes A through C were used for normal network use. Class D was multicast, and Class E was reserved. Table 5.4 shows the IPv6 address range of each.

Classful networks are inflexible: used for normal hosts in three sizes: 16,777,216 addresses (Class A), 65,536 addresses (Class B), and 256 addresses (Class C). The smallest routable network is a Class C network with 256 addresses; a suitable point-to-point link using classful networks requires a network between the two points, wasting over 250 IP addresses.

# Classless Inter-Domain Routing

Classless Inter-Domain Routing (CIDR) allows far more flexible network sizes than those allowed by classful addresses. CIDR allows for many network sizes beyond the arbitrary classful boundaries.

The Class A network 10.0.0.0 contains addresses that begin with: 10.1.2.3, 10.187.24.8, 10.396.223, etc. In other words, 10.* is a Class A address. The first 8 bits of the dotted-quad IPv4 address is the network (10); the remaining 24 bits are the host address: 3.962.223, the last IP address in the previous example. The CIDR notation for a Class A network is /8 for 10.0.0.0. The “/8” is the netmask, which means the network portion is 8 bits long, leaving 24 bits for the host.