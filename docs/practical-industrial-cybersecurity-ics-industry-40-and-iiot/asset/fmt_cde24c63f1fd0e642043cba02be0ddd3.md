
This model includes controls for integrating cloud services and other WAN communication channels to accommodate larger or widely distributed sites. The division between the traditional Level 0-2 and Level 3 is enforced by boundary protection set up on each side of the Cloud/WAN system. Minor enforcement boundaries are established on the Level 0-2 side while major boundary enforcement solutions are applied on the Level 3 side. The organization's management servers, HMIs, engineering stations, testing and staging systems, remote access, and cybersecurity operations are segmented into sub-layers at the Level 3 layer.

![FIGURE 3.25a The SANS ICS410 Reference Architecture](images/c03f025b.png)

**FIGURE 3.25a** The SANS ICS410 Reference Architecture

As with more advanced versions of the Purdue model, DMZs are strategically placed throughout the ICS410 model to provide the A-to-B push and the B-to-C pull, but not A-to-C or C-to-A communications paths between all IT and OT layers. Firewalls are the control device of choice between Layers 3 and 4 of this model. These firewalls should be configured to block all traffic in and out of the OT network with explicit permit rules implemented for the minimum required traffic. Firewalls are also called for between Levels 3 and 4, as well as between Levels 4 and 5.

Additional authentication methods, including multifactor authentication, should be employed for all access paths to the OT network. Malware-checking should be performed on all files entering or leaving the OT network. Likewise, all traffic entering or leaving the OT network should be logged. Finally, no Internet access should be allowed below Level 4.

## Network Segmentation

*Network segmentation* is a subnetting technique employed to divide a network into layered segments based on the functional divisions of the organization. For example, there is generally no good reason for a department that is working on highly classified information to be directly networked with other departments that are not.

Typically, physical firewalls and routers are used to create network segmentation to control the movement of traffic between network tiers (segments). **FIGURE 3.25** depicts a generically segmented business network. In this example, the router is configured to interface with the Internet and pass all packets with an IP address in the range of 134.141.x.x to the designated subnet inside the local network. When the packet reaches the subnet, it is accepted by the host with the designated fourth octet in the address (0–254).

![FIGURE 3.25 A segmented network](images/c03f025a.png)

**FIGURE 3.25** A segmented network

For our purposes, the main advantage of network segmentation is the added security created by making the segment's internal structure invisible to the other network segments and the outside world. A segmented network will act to limit the depth of any intrusions into the enterprise and to minimize the propagation of any attacks.

However, heightened security is not the only advantage of network segmentation. There are also increased performance levels within the local segment due to limiting the traffic flow from other segments. Another advantage is that segmentation isolates local failures to the segment, making them easier to detect, troubleshoot, and repair. However, segmentation also impacts the overall performance of the network and requires additional management.

In the following sections we investigate two methods that can also be used to create network segmentation with NAT segmenting and network virtualization using layer 2/3 switches.

### Network Address Translation Segmenting

*Network address translation (NAT)* is a feature of most routers, servers, and firewalls. While the primary purpose of NAT is to shield the IP addresses of the internal network from those outside the network, it also provides a straightforward method of segmenting the internal physical structure of the organization's Intranet. **FIGURE 3.26** illustrates a NAT-segmented network.

![FIGURE 3.26 A NAT-segmented network](images/c03f026.png)

**FIGURE 3.26** A NAT-segmented network

For example, in a network that is segmented by function, a NAT firewall could be installed to provide segmentation for a department that requires both minimal security and Internet access, while not using other security protocols.

However, NAT is not a security cure-all. It requires careful configuration and offers limited security. In fact, NAT is a hindrance to many other security protocols that you may want to use on your LAN. Primarily, NAT does not work well with any protocol that encrypts IP information. This makes tunneling protocols such as *Point-to-Point Tunneling Protocol (PPTP)* incompatible with a NAT firewall.

One of the most popular protocols, *IPSec* employs *Authentication Header (AH)* protocol to prevent packet changes in transport. Because NAT is designed to change the source IP address, IPSec authentication will fail if used on the same network segment. In addition, IPSec employs *Encapsulating Security Payload (ESP)* to check IP addresses in *Transport mode*, which will also fail if NAT translates the source IP address.

Any protocol that binds the source IP address with an authentication key will fail to authenticate or negotiate a session because NAT changes the source IP address. This would be true for *Internet Key Exchange (IKE)* as well as *Certificate Authorities (CAs)*. Likewise, because *File Transfer Protocol (FTP)* changes the source IP address into ASCII text, it is also not compatible with NAT on the same network segment.

It is possible, however, to establish IPSec connections across NAT gateways using a UDP encapsulation technique referred to as *Network Address Translation traversal (NAT-T)*. As described, the NAT device alters the authenticity of the packet that caused it to be dropped. NAT-T adds an unencrypted UDP header to encapsulate the IPSec ESP header. This causes the packet to be treated like a normal UDP packet so that it passes through the gateway. NAT-T operations require three ports to be open: UDP port 4500 (NAT-T), UDP port 500 (IKE), and IP protocol 50 (ESP).

### Network Virtualization

Not all network structures are what they appear to be. A *virtual local area network (VLAN)* is a logical local area network that overlays one or more physical LANs. Virtualization software can be employed to partition a physical LAN into multiple logical LANs or to organize multiple physical LANs into a single logical LAN. In both cases, the organization and operation of the virtual LAN may bear little resemblance to the actual hardware the VLAN is operating on. Each virtual LAN is then identified by a *VLAN ID*, such as VLAN10.

VLANs (along with VPNs and VPLS) are *protocol-based virtual network structures*. As a security topology, VLANs restrict the visibility of network traffic by limiting the flow of traffic between designated ports and groupings. These structures are typically created using layer 2 managed switches to separate network segments along logical or functional chains of communication, regardless of their physical locations. The physical ports on the switches are assigned to specific user groups to create their own segments. This enables logical VLAN groups to span multiple physical network segments without requiring the use of a firewall.
