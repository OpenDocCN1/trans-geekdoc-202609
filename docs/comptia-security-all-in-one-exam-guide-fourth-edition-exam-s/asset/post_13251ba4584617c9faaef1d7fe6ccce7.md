
Many types of servers belong in this area, including web servers that are serving content to Internet users, as well as remote-access servers and external e-mail servers. In general, any server directly accessed from the outside, untrusted Internet zone needs to be in the DMZ. Other servers should not be placed in the DMZ. Domain name servers for your inner, trusted network and database servers that house corporate databases should not be accessible from the outside. Application servers, file servers, print servers—all of the standard servers used in the trusted network—should be behind both firewalls, plus routers and switches used to connect these machines.

The idea behind the use of the DMZ topology is to force an outside user to make at least one hop in the DMZ before he can access information inside the trusted network. If the outside user makes a request for a resource from the trusted network, such as a data element from a database via a web page, then this request needs to follow this scenario:

1. A user from the untrusted network (the Internet) requests data via a web page from a web server in the DMZ.
2. The web server in the DMZ requests the data from the application server, which can be in the DMZ or in the inner, trusted network.
3. The application server requests the data from the database server in the trusted network.
4. The database server returns the data to the requesting application server.
5. The application server returns the data to the requesting web server.
6. The web server returns the data to the requesting user from the untrusted network.

This separation accomplishes two specific, independent tasks. First, the user is separated from the request for data on a secure network. By having intermediaries do the requesting, this layered approach allows significant security levels to be enforced. Users do not have direct access or control over their requests, and this filtering process can put controls in place. Second, scalability is more easily realized. The multiple-server solution can be made to be very scalable, literally to millions of users, without slowing down any particular layer.

![](img/922567202a944c5e8d3ba0168d2ad3a5_80_0.png)

EXAM TIP DMZs act as a buffer zone between unprotected areas of a network (the Internet) and protected areas (sensitive company data stores), allowing for the monitoring and regulation of traffic between these two zones.

## Subnetting

An IP address (IPv4) consists of two parts, a network address and a host address, combined in a 32-bit number. The higher-order bits represent the network address, and the lower, or remaining bits, represent the host address. The point of separation is defined as a subnet mask. Initially, the IPv4 address space was divided into a series of address ranges, based on some standard separations, as detailed in Table 3-1. Over time, this was deemed too restrictive and a new scheme called Classless Inter-Domain Routing (CIDR) was developed. CIDR allows the partitioning of the IPv4 address space into user-definable chunks, allowing greater flexibility.

| Class | Addresses per Network | Number of Networks | Subnet Mask |
|---|---:|---:|---|
| Class A | 16,777,214 | 128 | 255.0.0.0 |
| Class B | 65,534 | 16,384 | 255.255.0.0 |
| Class C | 254 | 2,097,152 | 255.255.255.0 |

**Table 3-1** IPv4 Network Classes and Subnet Masks

CIDR allows address blocks to be broken into smaller networks referred to as subnets. Beginning with a Class C address, such as 192.168.x.x, CIDR can break it into a series of networks. If it is desired to break it into two networks, then the highest-order bit of the host space becomes a network address bit; this makes the new subnet mask 255.255.128.0. The effect is to use 17 bits for network addressing and 15 bits for hosts. CIDR uses a notation where the network address bits are marked with a "/" sign, so this example would be 192.168.x.x/17. This is the same as saying the subnet mask is 255.255.128.0. The resulting set of host addresses would be 192.168.0.1 through 192.168.127.254 on one network and 192.168.128.1 through 192.168.255.254 on the other. If you need three subnets, you will need to use 2 bits for four subnets, as the number of subnets will increase by powers of two. This may result in unused subnets, but it is unavoidable.

CIDR can either create a subnet, which is part of a class network, or a supernet, which is larger than a class network. Table 3-2 illustrates the relationships between a class network, a subnet, and a supernet. It might be confusing, but as the CIDR mask number increases, the number of networks goes down and the number of hosts goes up.

In Table 3-2 note that the number of usable hosts is two less than the mathematical number of hosts. This is because the addresses that end in all zeros or all ones are broadcast addresses—that is, addresses that target all hosts. So the .0 and .255 addresses in this example are not individual machines.

| CIDR Notation | Mask | Number of Usable Hosts | Size |
|---|---:|---:|---|
| X.X.X.X/25 | 255.255.255.128 | 126 | Half of a Class C subnet |
| X.X.X.X/24 | 255.255.255.0 | 254 | Class C subnet |
| X.X.X.X/23 | 255.255.254.0 | 510 | Two Class C subnets |

**Table 3-2** CIDR Subnets and Supernets

## VLAN

A local area network (LAN) is a set of devices with similar functionality and similar communication needs, typically co-located and operated off a single switch. This is the lowest level of a network hierarchy and defines the domain for certain protocols at the data link layer for communication. Virtual LANs (VLANs) use a single switch and divide it into multiple broadcast domains and/or multiple network segments, known as trunking. This very powerful technique allows significant network flexibility, scalability, and performance.

## Trunking

Trunking is the process of spanning a single VLAN across multiple switches. A trunk-based connection between switches allows packets from a single VLAN to travel between switches, as shown in Figure 3-2. Two trunks are shown in the figure: VLAN 10 is implemented with one trunk, and VLAN 20 is implemented by the other. Hosts on different VLANs cannot communicate using trunks and are switched across the switch network. Trunks enable network administrators to set up VLANs across multiple switches with minimal effort. With a combination of trunks and VLANs, network administrators can subnet a network by user functionality without regard to host location on the network or the need to re-cable machines.

![](img/922567202a944c5e8d3ba0168d2ad3a5_82_0.png)

Figure 3-2 VLANs and trunks

## Security Implications

VLANs are used to divide a single network into multiple subnets based on functionality. This permits engineering and accounting, for example, to share a switch because of proximity and yet have separate traffic domains. The physical placement of equipment and cables is logically and programmatically separated so adjacent ports on a switch can reference separate subnets. This prevents unauthorized use of physically close devices through separate subnets but the same equipment. VLANs also allow a network administrator to define a VLAN that has no users and map all of the unused ports to this VLAN. Then if an unauthorized user should gain access to the equipment, he will be unable to use unused ports, as those ports will be securely defined to nothing. Both a purpose and a security strength of VLANs is that systems on separate VLANs cannot directly communicate with each other.

![](img/922567202a944c5e8d3ba0168d2ad3a5_83_0.png)

> **CAUTION** Trunks and VLANs have security implications that need to be heeded so that firewalls and other segmentation devices are not breached through their use. They also require understanding of their use to prevent an unauthorized user from reconfiguring them to gain undetected access to secure portions of a network.

## NAT

Network Address Translation (NAT) uses two sets of IP addresses for resources—one for internal use and another for external (Internet) use. NAT was developed as a solution to the rapid depletion of IP addresses in the IPv4 address space; it has since become an Internet standard (see RFC 1631 for details). NAT is used to translate between the two addressing schemes and is typically performed at a firewall or router. This permits enterprises to use the nonroutable private IP address space internally and reduces the number of external IP addresses used across the Internet.

Three sets of private IP addresses are defined as nonroutable, which means that addresses will not be routed across the Internet. These addresses are routable internally, and routers can be set to route them, but the routers across the Internet are set to discard packets sent to these addresses. This approach enables a separation of internal and external traffic and allows these addresses to be reused by anyone and everyone who wishes to do so. The three private address spaces are

- **Class A**   10.0.0.0–10.255.255.255
- **Class B**   172.16.0.0–172.31.255.255
- **Class C**   192.168.0.0–192.168.255.255

The use of these addresses inside a network is unrestricted, and they function like any other IP addresses. When outside—that is, Internet-provided—resources are needed for one of these addresses, NAT is required to produce a valid external IP address for the resource. NAT operates by translating the address when traffic passes the NAT device.
