IPv6, on the other hand, uses 16 bytes or 128 bits for its addresses. These addresses are typically displayed as eight groups of four bytes written in hexadecimal form, such as 2001:0db8:85a3:0000:0000:8a2e:0370:7334. Having 2^128 addresses equates to a capacity for a staggering 340,282,370,000,000,000,000,000,000,000,000,000 nodes.

# Public and private addresses

The key difference between public and private addresses is their visibility on the public internet. IP addresses that are used on the public internet must be globally unique. They are typically assigned to websites, external-facing servers and routers that connect to the internet. The allocation of these public internet addresses is managed by ICANN (the Internet Corporation for Assigned Names and Numbers).

Private IP addresses used within a private network are not directly routable on the global internet. They are commonly used in home and corporate networks for devices such as computers, tablets and internal servers. Traffic from these devices must be converted to a public address by the router to get on to the public internet.

ICANN has reserved certain ranges of addresses as private, non-routable addresses for organizations to use for their internal networks. These are:

+   - 10.0.0.0 to 10.255.255.255
+   - 172.16.0.0 to 172.31.255.255
+   - 192.168.0.0 to 192.168.255.255
+   - IPv6 has FC00::0000:0000:0000:0000:0000:0000:0000 to FDF:FFFF:FFFF:FFFF:FFFF:FFFF:FFFF:FFFF.

# Static and dynamic addresses

Static IP addresses are those that are permanently assigned to a device. The device uses the same IP address every time it connects to the network. Static IP addresses are essential for servers so that client devices know where to locate them on a network.

In contrast, a dynamic IP address is one that is assigned to a device when it connects to the network. This process is overseen by a DHCP server that allocates connecting devices an address from a predetermined pool of addresses that it has available to it. Dynamic addresses help reduce overheads by more efficiently utilizing a limited number of IP addresses in environments where devices frequently connect and disconnect.

# Network address translation (NAT)

![](bbox=[0.27, 0.66, 0.88, 0.78])

![](bbox=[0.11, 0.64, 0.26, 0.84])

Network address translation is a process whereby networks translate private IP addresses to public IP addresses, and vice versa. The process enables multiple devices on a network to share a single public IP address.