
## IPv6 Neighbor Discovery—Address Resolution (9.3.3)

Much as with ARP for IPv4, IPv6 devices use IPv6 ND to determine the MAC address of a device that has a known IPv6 address.

ICMPv6 Neighbor Solicitation and Neighbor Advertisement messages are used for MAC address resolution. This is similar to ARP requests and ARP replies used by ARP for IPv4. For example, say that PC1 wants to ping PC2 at IPv6 address 2001:db8:acad:1:1. To determine the MAC address for the known IPv6 address, PC1 sends an ICMPv6 Neighbor Solicitation message, as illustrated in Figure 9-13.

![](img/e71dc48d3ae3db3394e5857ab2acae75_347_0.png)

Figure 9-13 IPv6 Neighbor Discovery Process

ICMPv6 Neighbor Solicitation messages are sent using special Ethernet and IPv6 multicast addresses. This allows the Ethernet NIC of the receiving device to determine whether the Neighbor Solicitation message is for itself without having to send it to the operating system for processing.

PC2 replies to the request with an ICMPv6 Neighbor Advertisement message, which includes its MAC address.

![](img/e71dc48d3ae3db3394e5857ab2acae75_348_0.png)

## Packet Tracer—IPv6 Neighbor Discovery (9.3.4)

For a device to communicate with another device, the MAC address of the destination device must be known. With IPv6, a process called Neighbor Discovery is responsible for determining the destination MAC address. In this activity, you will gather PDU information in simulation mode to better understand the process. There is no Packet Tracer scoring for this activity.

Refer to the online course to complete this activity.

![](img/e71dc48d3ae3db3394e5857ab2acae75_348_1.png)

## Check Your Understanding—Neighbor Discovery (9.3.5)

Refer to the online course to complete this activity.

## Summary (9.4)

The following is a summary of the topics in the chapter and their corresponding online modules.

## MAC and IP

Layer 2 physical addresses (that is, Ethernet MAC addresses) are used to deliver the data link frame with the encapsulated IP packet from one NIC to another NIC on the same network. If the destination IP address is on the same network, the destination MAC address is the address of the destination device. When the destination IP address (IPv4 or IPv6) is on a remote network, the destination MAC address is the address of the host default gateway (that is, the router interface). Along each link in a path, an IP packet is encapsulated in a frame. The frame is specific to the data link technology associated with that link, such as Ethernet. If the next hop device is the final destination, the destination MAC address is the address of the device's Ethernet NIC. How are the IP addresses of the IP packets in a data flow associated with the MAC addresses on each link along the path to the destination? For IPv4 packets, this association is done through a process called ARP. For IPv6 packets, the process is ICMPv6 ND.

## ARP

Every IP device on an Ethernet network has a unique Ethernet MAC address. When a device sends an Ethernet Layer 2 frame, it contains two addresses: destination MAC address and source MAC address. A device uses ARP to determine the destination MAC address of a local device when it knows its IPv4 address. ARP provides two basic functions: resolving IPv4 addresses to MAC addresses and maintaining a table of IPv4-to-MAC address mappings. The ARP request is encapsulated in an Ethernet frame using header information about the source and destination MAC addresses and type. Only one device on a LAN has an IPv4 address that matches the target IPv4 address in the ARP request. All other devices do not reply. An ARP reply contains the same header fields as a request. Only the device that originally sent the ARP request receives the unicast ARP reply. After the ARP reply is received, the device adds the IPv4 address and the corresponding MAC address to its ARP table. When the destination IPv4 address is not on the same network as the source IPv4 address, the source device needs to send the frame to its default gateway. This is the interface of the local router. For each device, an ARP cache timer removes ARP entries that have not been used for a specified period of time. Commands may also be used to manually remove some or all of the entries in the ARP table. As a broadcast frame, an ARP request is received and processed by every device on the local network, which could cause the network to slow down. A threat actor can use ARP spoofing to perform an ARP poisoning attack.

## Neighbor Discovery

IPv6 does not use ARP; rather, it uses the ND protocol to resolve MAC addresses. ND provides address resolution, router discovery, and redirection services for IPv6 using ICMPv6. ICMPv6 ND uses five ICMPv6 messages to perform these services: Neighbor Solicitation, Neighbor Advertisement, Router Solicitation, Router Advertisement, and Redirect. Much as with ARP for IPv4, IPv6 devices use IPv6 ND to resolve the MAC address of a device to a known IPv6 address.

## Practice

The following activities provide practice with the topics introduced in this chapter. The lab is available in the companion *Introduction to Networks Labs & Study Guide (CCNAv7)* (ISBN 9780136634454). The Packet Tracer activity instructions are also provided in the *Labs & Study Guide*. The PKA files are available in the online course.

![](img/e71dc48d3ae3db3394e5857ab2acae75_350_0.png)

## Packet Tracer Activities

- Packet Tracer 9.1.3: Identify MAC and IP Addresses
- Packet Tracer 9.2.9: Examine the ARP Table
- Packet Tracer 9.3.4: IPv6 Neighbor Discovery

## Check Your Understanding Questions

Complete all the review questions listed here to test your understanding of the topics and concepts in this chapter. The appendix “Answers to ‘Check Your Understanding’ Questions” lists the answers.

1. When a host has an IPv4 packet sent to a host on a remote network, what address is requested in the ARP request?
   a. the IPv4 address of the destination host
   b. the IPv4 address of the default gateway
   c. the MAC address of the default gateway, the router interface closest to the sending host
   d. the MAC address of the switch port that connects to the sending host

2. How does the ARP process use an IPv4 address?
   a. to determine the MAC address of the remote destination host
   b. to determine the MAC address of a device on the same network
   c. to determine the amount of time a packet takes when traveling from source to destination
   d. to determine the network number based on the number of bits in the IP address

3. Which of the following does the ARP table in a switch map together?
   a. Layer 3 address to a Layer 2 address
   b. Layer 3 address to a Layer 4 address
   c. Layer 4 address to a Layer 2 address
   d. Layer 2 address to a Layer 4 address

4. What is one function of the ARP protocol?
   a. obtaining an IPv4 address automatically
   b. mapping a domain name to its IPv4 address
   c. resolving an IPv4 address to a MAC address
   d. maintaining a table of domain names with their resolved IPv4 addresses

5. Which router component holds the routing table, ARP cache, and running configuration file?
   a. RAM
   b. Flash
   c. NVRAM
   d. ROM

6. What type of information is contained in an ARP table?
   a. switch ports associated with destination MAC addresses
   b. domain name-to-IPv4 address mappings
   c. routes to reach destination networks
   d. IPv4 address-to-MAC address mappings

7. A cybersecurity analyst believes an attacker is spoofing the MAC address of the default gateway to perform a man-in-the-middle attack. Which command should the analyst use to view the MAC address a host is using to reach the default gateway?
   a. ipconfig /all
   b. route print
   c. netstat -r
   d. arp -a

8. What is a function of ARP?
   a. resolving known MAC addresses to unknown IPv4 addresses
   b. resolving known port addresses to unknown MAC addresses
   c. resolving known MAC addresses to unknown port addresses
   d. resolving known IPv4 addresses to unknown MAC addresses

9. What is the purpose of ARP in an IPv4 network?
   a. to forward data onward based on the destination IP address
   b. to obtain a specific MAC address when an IP address is known
   c. to forward data onward based on the destination MAC address
   d. to build the MAC address table in a switch from the information this gathered

10. Which action does a Layer 2 switch take when it receives a Layer 2 broadcast frame?
   a. It drops the frame.
   b. It forwards the frame out all ports except the port on which it received the frame.
   c. It forwards the frame out all ports that are registered to forward broadcasts.
   d. It forwards the frame out all ports.

11. Which destination MAC address is used in an ARP request?
   a. 0.0.0.0
   b. 255.255.255.255
   c. FFFF.FFFF.FFFF
   d. 1270.0.1
   e. 01-00-5E-00-AA-23
