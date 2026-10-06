The transition to IPv6 began in 1998 while Microsoft was developing Windows 2000, and our first glimpse of the next-generation TCP/IP (an integrated IPv4/IPv6 layer architecture) was in Windows Vista. Since then, all of Microsoft's new client and server operating systems have the next-generation TCP stack at the core of their networking, including, of course, Windows Server 2012.

# The Benefits of IPv6

The transition to IPv6 networking brings with it a number of benefits when compared to IPv4, such as these:

**Large Address Scaling.** With the growing usage of consumer Internet-connected mobile devices, IPv4 was becoming saturated with the demand for more addresses. The solution was to create a protocol that could handle thousands of IP addresses, and that's where IPv6 comes into ours. IPv6 addresses are 128 bits in length in comparison to IPv4 addresses, which are only 32-bit. With IPv6, obtaining a public address space is very easy, and on your local network a prefix that uses Unique Address (ULA) can apply to each size of your organization. The combination of public address space and ULA prefixes allows you to scale your internet to an extent.

**Efficient Internet Connectivity** IPv6 in Windows Server 2012 detects potential routing-path issues between IPv4 and IPv6 Networks and can prevent the initial connection attempt. This feature, along with other benefits such as fixed-length IP packet headers and aggregated allocation, from the outset delivers a much more Internet connectivity experience.

**Enhanced Security** In IPv6, IPSec support is a protocol requirement; this was optional in IPv4. This requirement provides a standards-based solution for your network security needs, promotes interoperability between different IPv6 implementations, and is applicable for devices, applications, and services.

**Integrated Quality of Service** QoS enables you to measure and throttle the levels of bandwidth over your network interface cards (NICs). It's available in Microsoft's operating systems for a number of years but not widely used by administrators and IT pros because of more favorable hardware-based solutions on the market. QoS is fully integrated into Windows Server 2012, and it works by using a 20-bit Flow Label field and an 8-bit Traffic Class in IPv6 to determine how traffic is dealt with.

# IPv6 Transition Technologies

The journey from IPv4 to IPv6 will not necessarily happen in a short time, and it became apparent to the original designers of IPv6 that both protocols must coexist and work together on the same infrastructure. The caveat, though, is that IPv4 and IPv6 cannot natively talk to each other, and a solution had to be developed to address the barriers between these protocols for the duration of this transitional period. A set of transitional technologies and addresses were created so that IPv6 nodes can communicate with each other in a mixed-protocol environment, even if they are separated by an IPv4-only infrastructure.

The original IPv6 designers requested Request for Comment (RFC) 2893, "Transition Mechanisms for IPv6 Hosts and Routers." This RFC defined the different IPv4 and IPv6 node types on the Internet, and Table 4.1 explains what they are.