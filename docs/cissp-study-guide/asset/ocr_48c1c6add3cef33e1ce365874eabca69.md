# 240 CHAPTER 5 Domain 4: Communication and Network Security

# RFC 1918 Addressing

RFC 1918 addresses are private IPv4 addresses that may be used for internal traffic that does not route via the Internet. This allows for conservation of scarce IPv4 addresses: countless Intranets can use the same overlapping RFC 1918 addresses. Three blocks of IPv4 addresses are set aside for this purpose:

+   - 10.0.0.0–10.255.255.255 (10.0.0.0/8)
- 172.16.0.0–172.31.255.255 (172.16.0.0/12)
- 192.168.0.0–192.168.255.255 (192.168.0.0/16)

Any public Internet connection using un-translated RFC 1918 addresses as a destination will fail; there are no public routes for these networks. Internet traffic sent with an un-translated RFC 1918 source address will never return. Using the classical terminology, the 10.0.0.0/8 is a Class A network, the 172.16.0.0/12 is 16 continuous Class B networks, and 192.168.0.0/16 is 256 Class C networks.

RFC 1918 addresses are used to conserve public IPv4 addresses, which are in short supply. RFC stands for “Request for Comments,” a way to discuss and publish standards on the Internet. More information about RFC 1918 is available at: https://www.rfc-editor.org/rfc/rfc1918.txt.

> Note
Memorizing RFCs is not generally required for the exam: RFC 1918 addresses are exception to that rule. The exam is designed to test knowledge of the universal language of information security. The term “RFC 1918” is commonly used by network professionals and should be understood by information security professionals.

# Network Address Translation

Network Address Translation (NAT) is used to translate IP addresses. It is frequently used to translate RFC 1918 addresses as they pass from Intranets to the Internet. If you were wondering how you could surf the web using a PC configured with a private RFC 1918 address, NAT is one answer (proxying another).

Three types of NAT are static NAT, pool NAT (also known as dynamic NAT), and Port Address Translation (PAT, also known as NAT overloading). Static NAT makes a one-to-one translation between addresses, such as 192.168.1.47→192.0.2.2. Pool NAT reserves a number of public IP addresses in a pool, such as 192.0.2.10→192.0.2.19. Addresses can be assigned from the pool, and returned. Finally, PAT typically makes a many-to-one translation from multiple private addresses to one public IP address, as 192.168.1.*→192.0.2.20. PAT is a common solution for homes and small offices: multiple internal devices such as laptops, desktops, and mobile devices share one public IP address. Table 5.5 summarizes examples of the NAT types.

NAT hides the origin of a packet: the source address is the NAT gateway (usually a router or a firewall), not the host itself. This provides some limited security