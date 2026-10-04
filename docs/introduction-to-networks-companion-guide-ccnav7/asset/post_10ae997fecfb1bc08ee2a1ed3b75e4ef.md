
automatically creates an IPv6 LLA whenever a GUA is assigned to the interface. By default, Cisco IOS routers use EUI-64 to generate the interface IDs for all LLAs on IPv6 interfaces. For serial interfaces, a router uses the MAC address of an Ethernet interface. To make it easier to recognize and remember these addresses on routers, it is common to statically configure IPv6 LLAs on routers. To verify IPv6 address configuration, use the following three commands: show ipv6 interface brief, show ipv6 route, and ping.

## IPv6 Multicast Addresses

There are two types of IPv6 multicast addresses: well-known multicast addresses and solicited-node multicast addresses. Assigned multicast addresses are reserved multicast addresses for predefined groups of devices. Well-known multicast addresses are assigned. Two common IPv6 assigned multicast groups are the ff02::1 all-nodes multicast group and the ff02::2 all-routers multicast group. A solicited-node multicast address is similar to the all-nodes multicast address. The advantage of a solicited-node multicast address is that it is mapped to a special Ethernet multicast address.

## Subnet an IPv6 Network

IPv6 was designed with subnetting in mind. A separate subnet ID field in the IPv6 GUA is used to create subnets. The subnet ID field is the area between the global routing prefix and the interface ID. The benefit of a 128-bit address is that it can support more than enough subnets and hosts per subnet for each network. Address conservation is not an issue. For example, if the global routing prefix is /48, and you use the typical 64 bits for the interface ID, you end up with a 16-bit subnet ID:

- 16-bit subnet ID: Creates up to 65,536 subnets
- 64-bit interface ID: Supports up to 18 quintillion host IPv6 addresses per subnet (that is, 18,000,000,000,000,000,000)

Because there are more than 65,536 subnets to choose from, the task of a network administrator is to design a logical scheme to address the network. Address conservation is not a concern when using IPv6. Much as when configuring IPv4, with IPv6, each router interface can be configured to be on a different IPv6 subnet.

![](img/e71dc48d3ae3db3394e5857ab2acae75_474_0.png)

## Packet Tracer—Implement a Subnetted IPv6 Addressing Scheme (12.9.1)

Your network administrator wants you to assign five /64 IPv6 subnets to the network shown in the topology. Your job is to determine the IPv6 subnets, assign IPv6 addresses to the routers, and set the PCs to automatically receive IPv6 addressing. Your final step is to verify connectivity between IPv6 hosts.

## Lab—Configure IPv6 Addresses on Network Devices (12.9.2)

In this lab, you will complete the following objectives:

- Part 1: Set Up Topology and Configure Basic Router and Switch Settings
- Part 2: Configure IPv6 Addresses Manually
- Part 3: Verify End-to-End Connectivity

## Practice

The following activities provide practice with the topics introduced in this chapter. The lab is available in the companion Introduction to Networks Labs & Study Guide (CCNAv7) (ISBN 9780136634454). The Packet Tracer activity instructions are also provided in the Labs & Study Guide. The PKA files are available in the online course.

## Labs

Lab 12.7.4: Identify IPv6 Addresses

Lab 12.9.2: Configure IPv6 Addresses on Network Devices

## Packet Tracer Activities

Packet Tracer 12.6.6: Configure IPv6 Addressing

Packet Tracer 12.9.1: Implement a Subnetted IPv6 Addressing Scheme

## Check Your Understanding Questions

Complete all the review questions listed here to test your understanding of the topics and concepts in this chapter. The appendix “Answers to ‘Check Your Understanding’ Questions” lists the answers.

1. What is indicated by a successful ping to the ::1 IPv6 address?
   a. The host is cabled correctly.
   b. The default gateway address is configured correctly.
   c. All hosts on the local link are available.
   d. The link-local address is correctly configured.
   e. IP is properly installed on the host.

2. What is the most compressed representation of the IPv6 address 2001:0db8:0000:abcd:0000:0000:0000:0001?
   a. 2001:0db8:abcd::1
   b. 2001:db8:0:abcd::1
   c. 2001:0db8:abcd::1
   d. 2001:0db8:0000:abcd::1
   e. 2001:db8::abcd:0:1

3. What is the purpose of the command ping ::1?
   a. It tests the internal configuration of an IPv6 host.
   b. It tests the broadcast capability of all hosts on the subnet.
   c. It tests the multicast connectivity to all hosts on the subnet.
   d. It tests the reachability of the default gateway for the network.

4. At a minimum, which address is required on IPv6-enabled interfaces?
   a. link-local
   b. unique local
   c. site local
   d. global unicast

5. What is the interface ID of the IPv6 address 2001:db8::1000:a9cd:47ff:fe57:fe94/64?
   a. fe94
   b. fe57:fe94
   c. 47ff:fe57:fe94
   d. a9cd:47ff:fe57:fe94
   e. 1000:a9cd:47ff:fe57:fe94

6. What are the three parts of an IPv6 global unicast address? (Choose three.)
   a. an interface ID that is used to identify the local network for a particular host
   b. a global routing prefix that is used to identify the network portion of the address that has been provided by the ISP
   c. a subnet ID that is used to identify networks inside the local enterprise site
   d. a global routing prefix that is used to identify the portion of the network address provided by a local administrator
   e. an interface ID that is used to identify the local host on the network

7. What is the most compressed format possible for the IPv6 address 2001:0db8:0000:ab00:0000:0000:0000:1234?
   a. 2001:db8:0:ab00::1234
   b. 2001:db8:0:ab::1234
   c. 2001:db8:0000:ab::1234
   d. 2001:db8:0:ab:0::1234

8. What is the prefix associated with the IPv6 address 2001:db8:d15:ea:cc44::1/64?
   a. 2001::/64
   b. 2001:db8::/64
   c. 2001:db8:d15:ea::/64
   d. 2001:db8:d15:ea:cc44::/64

9. What type of address is automatically assigned to an interface when IPv6 is enabled on that interface?
   a. global unicast
   b. link-local
   c. loopback
   d. unique local

10. Which IPv6 network prefix is only intended for local links and cannot be routed?
    a. 2001::/3
    b. fc00::/7
    c. fe80::/10
    d. ff00::/12

11. Your organization is issued the IPv6 prefix 2001:0:130f::/48 by your service provider. With this prefix, how many bits are available for your organization to create /64 subnetworks if interface ID bits are not borrowed?
    a. 8
    b. 16
    c. 80
    d. 128

12. What is the network address for the IPv6 address 2001:db8:aa04:b5:1/64?
    a. 2001::/64
    b. 2001:db8::/64
    c. 2001:db8:aa04::/64
    d. 2001:db8:aa04:b5::/64

13. Which type of IPv6 address is not routable and is used only for communication on a single subnet?
    a. global unicast address
    b. link-local address
    c. loopback address
    d. unique local address
    e. unspecified address

14. Which address type is not supported in IPv6?
    a. private
    b. multicast
    c. unicast
    d. broadcast

15. What is the minimum configuration for a router interface that is enabled for IPv6?
    a. to have a link-local IPv6 address
    b. to have both IPv4 and IPv6 addresses
    c. to have a self-generated loopback address
    d. to have both a link-local address and a global unicast address
    e. to have only an automatically generated multicast address

## Objectives

Upon completion of this chapter, you will be able to answer the following questions:

- How is ICMP used to test network connectivity?
- How do you use the **ping** and **traceroute** utilities to test network connectivity?

## Introduction (13.0)

Imagine that you have an intricate model train set. Your tracks and trains are all connected and powered up and ready to go. You throw the switch. The train goes halfway around the track and stops. You know right away that the problem is most likely located where the train has stopped, so you look there first. It is not as easy to visualize problems with a network. Fortunately, there are tools to help you locate problem areas in a network—and they work with both IPv4 and IPv6 networks! You will be happy to know that this chapter has a couple Packet Tracer activities to help you practice using these tools, so let’s get testing!

## ICMP Messages (13.1)

In this section, you will learn about the different types of Internet Control Message Protocol (ICMP) messages and the tools that are used to send them.

### ICMPv4 and ICMPv6 Messages (13.1.1)

Although IP is only a best-effort protocol, the TCP/IP suite does provide for error messages and informational messages when communicating with another IP device. These messages are sent using the services of ICMP. The purpose of these messages is to provide feedback about issues related to the processing of IP packets under certain conditions—not to make IP reliable. ICMP messages are not required and are often not allowed in a network for security reasons.

ICMP is available for both IPv4 and IPv6. ICMPv4 is the messaging protocol for IPv4. ICMPv6 provides the same services for IPv6 but includes additional functionality. In this book, the term ICMP is used to refer to both ICMPv4 and ICMPv6.

The types of ICMP messages and the reasons they are sent are extensive. The ICMP messages common to both ICMPv4 and ICMPv6 and discussed in this chapter include

- Host reachability (Echo Request and Echo Reply) messages
- Destination Unreachable or Service Unreachable messages
- Time Exceeded messages

### Host Reachability (13.1.2)

ICMP Echo Request and Echo Reply messages can be used to test the reachability of a host on an IP network. The local host sends an ICMP Echo Request to a host. If
