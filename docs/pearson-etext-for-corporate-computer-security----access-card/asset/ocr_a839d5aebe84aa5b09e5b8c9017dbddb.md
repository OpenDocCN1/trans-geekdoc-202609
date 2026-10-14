# Masks

The Internet contains tens of thousands of **networks**. One of these networks is the University of Hawaii network. Another is the Microsoft network. Each ISP also is a network on the Internet.

Most organizations that have Internet networks subdivide these networks into **subnets**. For example, at the University of Hawaii, each college has its own subnet. One of these subnets is the Shidler College of Business subnet. A subnet may have many hosts.

Reflecting this hierarchical nature of the Internet’s organization (the Internet, networks, and subnets), Internet addresses are hierarchical. They have a network part that specifies a host’s network on the Internet, a subnet part that specifies the host’s subnet on that network, and a host part that specifies a particular host on that subnet. For instance, in the address 128.171.17.13, 128.171 is the network part for all hosts at the University of Hawaii. All IP addresses at the University of Hawaii begin with 128.171. Shidler is subnet 17, so all hosts in the Shidler College of Business begin with 128.171.17. Voyager is a host in the college. Its full IP address is 128.171.17.13.

At the University of Hawaii, the network part is 16 bits long, the subnet part is 8 bits long, and the host part is 8 bits long. However, network, subnet, and host parts vary in size. For a router to send an incoming packet back out, it needs to know either the packet’s network part or its combined network and subnet parts. Because part lengths vary, it must know an address’s mask, which gives the required information. For instance, the network mask for the University of Hawaii is 255.255.0.0. (A collection of 8 bits that is all 1s has the value 255.) Therefore, the network mask is sixteen 1s followed by sixteen 0s. For the Shidler College of Business, the subnet mask is 255.255.255.0. This means that the combined network and subnet parts are 24 bits long. Note in the IP header that there is no room for a mask. Routers exchange masks separately.

# IP Version 6

Although IP Version 4 is widely used, its 32-bit IP address size causes problems. This relatively "small" size limits the number of possible IP addresses. In addition, when IP addresses were distributed, most addresses were assigned to the United States because the Internet was invented there. In fact, some individual U.S. universities received more IP addresses than all of China.

To address the limitations of the 32-bit IP address size, a new version of the Internet Protocol was created. This was **IP Version 6 (IPv6)**. Figure A-13 shows the IPv6 packet organization.

One obvious change is that IPv6 addresses are much larger—128 bits. Each IPv6 address, then, must be written as four 32-bit rows. This large address size provides enough IP addresses to allow almost every device to be a host on the Internet—including toasters and coffee pots.

The version number field is four bits long, and its value is 6 (0110). There are also a traffic class field similar to the diff-serv field in Version 4 and a flow label field that together are 20 bits long. These two fields allow the packet to be assigned to a category based on the packet’s category (priority level, security level, etc.). All packets in a certain category would be assigned the same flow label and would be treated the same way by routers. However, this capability is not widely used.

On the next row, there is a 16-bit payload length field. "Payload" is another name for data field. Next comes the next header field, which we will see next. The second row ends with the hop limit field, which serves the same function as the TTL field in IPv4.

A major innovation in IPv6 is the next header field. IPv6 allows multiple headers. For instance, IPsec security is implemented with a security header. While options are unusual in IPv4, IPv6 uses additional headers extensively. The next header field tells what the next header is. Each subsequent header has a next header field that either identifies the next header or indicates that there is no next header.