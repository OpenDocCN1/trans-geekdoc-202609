
## OSI Model Layers

*   **Data Link Layer (Layer 2)** — Frame
*   **Physical Layer (Layer 1)** — Bits of data

The encapsulation process of adding headers (and a footer at the Data Link Layer) enables data exchange between layers on different systems. This is known as peer-to-peer communications. The content of a header includes information to be processed by the corresponding layer on the receiving end of a network link.

The content of the headers, mainly from Layers 2–4, are the greatest concern and focus of a firewall. Application proxy firewalls and stateful inspection firewalls can also examine the headers and the payload content of Layers 5–7.

### Sub-Protocols

TCP/IP is not a single protocol, but a collection of protocols. Often referred to as the TCP/IP suite, this collection includes several core protocols, such as **Internet Protocol (IP)**, **Transmission Control Protocol (TCP)**, and **User Datagram Protocol (UDP)**, as well as several commonly used protocols, such as Address Resolution Protocol (ARP), Internet Control Messaging Protocol (ICMP), Hypertext Transfer Protocol (HTTP), and Transport Layer Security (TLS). In addition to these, there are tens of thousands of proposed Request for Comments (RFCs) introducing potential protocols, but there are only a handful of protocols that typically operate within the network infrastructure created by TCP/IP.

A firm knowledge of the sub-protocols of TCP/IP is assumed but not essential to grasping the scope of this text.

### Headers and Payloads

Firewalls, specifically packet-filtering firewalls, inspect the contents of headers to allow or deny **frames**, packets, or segments. Depending on the type of filtering and the layer or protocol focus of the filtering, the item examined and the header it comes from can vary.

### Technical TIP

For a more complete list of the additional sub-protocols, along with the corresponding port assignments, view the document hosted by Internet Assigned Numbers Authority (IANA) at <https://www.iana.org/assignments/service-names-port-numbers/service-names-port-numbers.xhtml>. Nearly every one of the 65,536 ports has one or more protocols and applications associated with it.

For a list of ports used by malicious software, visit <https://attack.mitre.org/techniques/T1065/>.

Packet filtering often focuses on four main headers:

*   The Ethernet header of the frame from the Data Link Layer
*   The IP header of the packet from the Network Layer
*   The TCP header of the segment from the Transport Layer
*   The UDP header of the segment from the Transport Layer

Each of these four headers has numerous details that affect filtering action. These include MAC addresses, IP addresses, TCP header flags, port numbers, and more.

### Filtering on Addresses

With regard to the basic differences in IPv4 and IPv6 addressing, the issues to focus on are not subnet masks or the length of an address—both of which are important—but rather address length, available address capacity to meet the need for unique addresses, and subnet masking.

Many forms of filtering focus on the IP address and/or port number to make an allow or deny decision. Such decisions or rules can focus on either the source address or the destination address found in the header of a segment, packet, or frame. In other words, port number, IP address, or MAC address can support filtering as a source and/or destination concern.

Firewall filtering can focus on whether an address is public or private in both the source or destination position in the IP packet header. Generally, private addresses function on the private network and do not reach the outside. NAT will translate source-private addresses into a public address if the packet is heading toward an external destination. On the Internet, both routers and firewalls drop any IP packet that has an RFC 1918 address in the header. Firewalls can filter on whether an address is known or unknown. This function filters against addresses used for the source and/or the destination. Known addresses are usually trusted addresses. Only packets with trusted and known addresses are allowed to reach their destination. Unknown addresses are not likely to be trusted. Packets with unknown addresses can be stopped in every case or further inspected before an allow or deny decision is made.

Firewalls can filter on whether an address is known to be benign or commonly sends malicious content, a variation of known and unknown filtering. Instead of known addresses being trusted and unknowns not being trusted, this method twists the idea. A benign address is a known, trusted address and a malicious address is a known, not trusted address. In both cases, the addresses are known. Any unknown address encountered using this form of filtering will require additional subsequent filtering that looks at other aspects of the traffic.

Firewalls can also filter on whether an address is real or spoofed. This form of filtering is not as clear and distinct as the previous types. Whether a segment, packet, or frame’s address is the real correct address or a spoofed falsified address can be difficult to determine in every situation. When an address is a real address, in the sense that it’s within the subnet ranges of a network, the methods for determining whether it’s a spoofed address are few.

One method is to compare the address against a use table, such as that maintained by the Dynamic Host Configuration Protocol (DHCP) server, to see if the address is not currently assigned to any authorized system. Another method is to check the route, communication path, receipt vector, or receiving interface of the source address against what that aspect should be for a given address. For example, if a source address typically arrives on port 4 but it shows up on port 7, it is likely to be a spoofed source address.

Spoofed addresses can also be detected at border sentry points. When a source address comes from the opposite side of the firewall, then it is obviously a spoofed address. One clear example is when an internal LAN address appears as a source address in a packet on its way into a network from outside. This form of spoof filtering can be part of ingress filtering.

Likewise, the same process can be used for packets leaving a network. If a packet’s source address is from the outside, such as an Internet address, but the packet is received by a firewall from an interface in the private LAN, it must be from a spoofed address. This form of spoof filtering can be part of egress filtering.

## CHAPTER SUMMARY

Network security is complex, which is why we began with the fundamentals of network security. Once you have a firm grasp of these basic issues, you will be able to put security into practice on your own network. Network infrastructure design can have a significant impact on security.

A written security policy is the foundation of a successful security endeavor. Without a written policy, security will be chaotic and uncontrolled. A security policy defines and assigns roles and responsibilities to personnel within the organization. The seven domains of a typical IT infrastructure aid in identifying how users interact with each other and the resources on a network. These domains include the User Domain, Workstation Domain, LAN Domain, LAN-to-WAN Domain, Remote Access Domain, WAN Domain, and System/Application Domain. Administrators can employ numerous network components and devices to support a network security policy. These include firewalls, VPNs, and IDSs/IPSs.

## KEY CONCEPTS AND TERMS

*   **Access control**
*   **Application Layer (Layer 7)**
