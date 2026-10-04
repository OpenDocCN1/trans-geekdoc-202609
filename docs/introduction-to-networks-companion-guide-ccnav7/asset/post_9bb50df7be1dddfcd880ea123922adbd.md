
2. Configure addressing on network devices and hosts.
3. Verify IP connectivity.
4. Troubleshoot connectivity issues, as required.

## Lab—Design and Implement a VLSM Addressing Scheme (11.10.2)

In this lab, use the 192.168.33.128/25 network address to develop an addressing scheme for the network displayed in the topology diagram. Use VLSM to meet the IPv4 addressing requirements. After you have designed the VLSM address scheme, you will configure the interfaces on the routers with the appropriate IP address information. The future LANs at BR2 need to have addresses allocated, but no interfaces will be configured at this time.

## Practice

The following activities provide practice with the topics introduced in this chapter. The lab is available in the companion *Introduction to Networks Labs & Study Guide (CCNAv7)* (ISBN 9780136634454). The Packet Tracer activity instructions are also provided in the *Labs & Study Guide*. The PKA files are available in the online course.

## Labs

- Lab 11.6.6: Calculate IPv4 Subnets
- Lab 11.10.2: Design and Implement a VLSM Addressing Scheme

## Packet Tracer Activities

- Packet Tracer 11.5.5: Subnet an IPv4 Network
- Packet Tracer 11.7.5: Subnetting Scenario
- Packet Tracer 11.9.3: VLSM Design and Implementation Practice
- Packet Tracer 11.10.1: Design and Implement a VLSM Addressing Scheme

## Check Your Understanding Questions

Complete all the review questions listed here to test your understanding of the topics and concepts in this chapter. The appendix “Answers to ‘Check Your Understanding’ Questions” lists the answers.

1. What is the prefix length notation for the subnet mask 255.255.255.224?
   a. /25
   b. /26
   c. /27
   d. /28

2. How many valid host addresses are available on an IPv4 subnet that is configured with a /26 mask?
   a. 254
   b. 190
   c. 192
   d. 62
   e. 64

3. Which subnet mask would be used if 5 host bits are available?
   a. 255.255.255.0
   b. 255.255.255.128
   c. 255.255.255.224
   d. 255.255.255.240

4. A network administrator subnets the 192.168.10.0/24 network into subnets with /26 masks. How many equal-sized subnets are created?
   a. 1
   b. 2
   c. 4
   d. 8
   e. 16
   f. 64

5. What subnet mask is represented by the slash notation /20?
   a. 255.255.255.248
   b. 255.255.224.0
   c. 255.255.240.0
   d. 255.255.255.0
   e. 255.255.255.192

6. Which statement is true about variable-length subnet masking?
a. All the subnets are equally sized.
b. The sizes of subnets may be different, depending on requirements.
c. Subnets may only be subnetted one additional time.
d. Bits are returned, rather than borrowed, to create additional subnets.

7. Why does a Layer 3 device perform the ANDing process on a destination IPv4 address and subnet mask?
a. to identify the broadcast address of the destination network
b. to identify the host address of the destination host
c. to identify faulty frames
d. to identify the network address of the destination network

8. How many usable IPv4 addresses are available on the 192.168.1.0/27 network?
a. 256
b. 254
c. 62
d. 30
e. 16
f. 32

9. Which subnet mask would be used if exactly 4 host bits are available?
a. 255.255.255.224
b. 255.255.255.128
c. 255.255.255.240
d. 255.255.255.248

10. Which of the following are components of an IPv4 address? (Choose two.)
a. subnet portion
b. network portion
c. logical portion
d. host portion
e. physical portion
f. broadcast portion

11. If a network device has a mask of /30, how many IPv4 addresses are available for hosts on this network?
- a. 64
- b. 8
- c. 2
- d. 32
- e. 16
- f. 4

12. What does the IPv4 address 172.17.4.250/24 represent?
- a. network address
- b. multicast address
- c. host address
- d. broadcast address

13. If a network device has a mask of /28, how many IP addresses are available for hosts on this network?
- a. 256
- b. 254
- c. 62
- d. 32
- e. 16
- f. 14

14. What is the purpose of the subnet mask in conjunction with an IPv4 address?
- a. to uniquely identify a host on a network
- b. to identify whether the address is public or private
- c. to determine the subnet to which the host belongs
- d. to mask the IP address to outsiders

15. A network administrator is variably subnetting a network. The smallest subnet has a mask of 255.255.255.224. How many usable host addresses will this subnet provide?
- a. 2
- b. 6
- c. 14
- d. 30
- e. 62

## Objectives

Upon completion of this chapter, you will be able to answer the following questions:
- Why is IPv6 addressing needed?
- How are IPv6 addresses represented?
- What are the types of IPv6 network addresses?
- How do you configure static global unicast and link-local IPv6 network addresses?
- How do you configure global unicast addresses dynamically?
- How do you configure link-local addresses dynamically?
- How do you identify IPv6 addresses?
- How do you implement a subnetted IPv6 addressing scheme?

## Key Terms

This chapter uses the following key terms. You can find the definitions in the glossary at the end of the book.
- dual stack page 399
- tunneling page 400
- Network Address Translation 64 (NAT64) page 401
- preferred format page 402
- global unicast address (GUA) page 408
- link-local address (LLA) page 408
- global routing prefix page 410
- subnet ID page 410
- interface ID page 410
- Router Advertisement (RA) message page 417
- Router Solicitation (RS) message page 417
- stateless address autoconfiguration (SLAAC) page 418
- stateless DHCPv6 page 419
- stateful DHCPv6 page 420
- Extended Unique Identifier (EUI) page 422
- well-known IPv6 multicast address page 430
- solicited-node multicast address page 432

## Introduction (12.0)

It is a great time to be (or become) a network administrator! Why? In many networks, you will find both IPv4 and IPv6 working together. After the hard work of learning to subnet an IPv4 network, you may find that subnetting an IPv6 network is much easier. You probably didn’t expect that, did you? A Packet Tracer at the end of this chapter will give you the opportunity to subnet an IPv6 network. Go ahead, jump in!

### IPv4 Issues (12.1)

This section examines the reasons for the migration to IPv6.

### Need for IPv6 (12.1.1)

You already know about the shortage of IPv4 addresses. That is why you need to learn about IPv6.

IPv6 is designed to be the successor to IPv4. IPv6 has a larger 128-bit address space, providing 340 undecillion (that is, 340 followed by 36 zeros) possible addresses. However, IPv6 is more than just larger and more addresses.

When the IETF began its development of a successor to IPv4, it took the opportunity to fix the limitations of IPv4 and include enhancements. One example is Internet Control Message Protocol version 6 (ICMPv6), which includes address resolution and address autoconfiguration not found in ICMP for IPv4 (ICMPv4).

The depletion of IPv4 address space has been the motivating factor for moving to IPv6. Africa, Asia, and other areas of the world have become more connected to the internet, and there are not enough IPv4 addresses to accommodate this growth. As shown in Figure 12-1, four out of the five RIRs have run out of IPv4 addresses.

IPv4 has a theoretical maximum of 4.3 billion addresses. Private addresses in combination with Network Address Translation (NAT) have been instrumental in slowing the depletion of IPv4 address space. However, NAT is problematic for many applications, creates latency, and has limitations that severely impede peer-to-peer communications.

With the ever-increasing number of mobile devices, mobile providers have been leading the way with the transition to IPv6. The top two mobile providers in the United States report that over 90% of their traffic now occurs over IPv6.

Most top ISPs and content providers such as YouTube, Facebook, and Netflix have also made the transition. Many companies, including Microsoft, Facebook, and LinkedIn, are transitioning to IPv6-only networks internally. In 2018, broadband ISP Comcast reported IPv6 deployment of over 65%, and British Sky Broadcasting reported deployment of over 86%.
