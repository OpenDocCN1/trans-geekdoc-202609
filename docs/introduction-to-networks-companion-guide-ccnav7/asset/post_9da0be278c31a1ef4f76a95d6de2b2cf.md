
## Figure 11-15 Large Broadcast Domain

![](img/e71dc48d3ae3db3394e5857ab2acae75_397_0.png)

The solution is to reduce the size of the network to create smaller broadcast domains in a process called subnetting. These smaller network spaces are called subnets.

In Figure 11-16, the 400 users in LAN 1 with network address 172.16.0.0/16 have been divided into two subnets of 200 users each: 172.16.0.0/24 and 172.16.1.0/24. Now broadcasts are propagated only within the smaller broadcast domains. Therefore, a broadcast in LAN 1 would not propagate to LAN 2.

![](img/e71dc48d3ae3db3394e5857ab2acae75_397_1.png)

## Figure 11-16 Segmenting a Large Broadcast Domain

Notice that the prefix length has changed from a single /16 network to two /24 networks. This is the basis of subnetting: using host bits to create additional subnets.

## Note

The terms subnet and network are often used interchangeably. In most cases, a network is a subnet of some larger address block.

## Reasons for Segmenting Networks (11.4.3)

Subnetting reduces overall network traffic and improves network performance. It also enables an administrator to implement security policies such as which subnets are allowed or not allowed to communicate together. In addition, subnetting reduces the number of devices affected by abnormal broadcast traffic due to misconfigurations, hardware/software problems, or malicious intent.

There are various ways of using subnets to help manage network devices, as shown in Figures 11-17 through 11-19.

![](img/e71dc48d3ae3db3394e5857ab2acae75_398_0.png)

Figure 11-17 Subnetting by Location

Network administrators can create subnets using any other division that makes sense for the network. Notice in Figures 11-17 through 11-19 that the subnets use longer prefix lengths to identify networks.

Understanding how to subnet networks is a fundamental skill that all network administrators must develop. Various methods have been created to help understand this process. Although it may be a little overwhelming at first, pay close attention to the detail and, with practice, subnetting will become easier.

Interactive Graphic

## Check Your Understanding—Network Segmentation (11.4.4)

Refer to the online course to complete this activity.

![](img/e71dc48d3ae3db3394e5857ab2acae75_399_0.png)

## Figure 11-18 Subnetting by Group or Function

![](img/e71dc48d3ae3db3394e5857ab2acae75_399_1.png)

## Figure 11-19 Subnetting by Device Type

## Subnet an IPv4 Network (11.5)

Without subnetting, the performance of an IPv4-based network would quickly decrease as the number of hosts increased. Proper subnetting allows better control of network traffic and greatly improves network efficiency.

## Subnet on an Octet Boundary (11.5.1)

In the previous section, you learned several good reasons for segmenting a network. You also learned that segmenting a network is called subnetting. Subnetting is a critical skill to have when administering an IPv4 network. It is a bit daunting at first, but it gets much easier with practice.

IPv4 subnets are created by using one or more of the host bits as network bits. This process involves extending the subnet mask to borrow some of the bits from the host portion of the address to create additional network bits. The more host bits that are borrowed, the more subnets that can be defined. The more bits that are borrowed to increase the number of subnets, the lower the number of hosts per subnet.

Networks are most easily subnetted at an octet boundary: /8, /16, or /24. Table 11-4 identifies these prefix lengths. Notice that using longer prefixes decreases the number of hosts per subnet.

Table 11-4 Subnet Masks on Octet Boundaries

| Prefix Length | Subnet Mask | Subnet Mask in Binary (n = network, h = host) | Number of Hosts |
|---|---|---|---|
| /8 | 255.0.0.0 | nnnnnnnn.hhhhhhhh.hhhhhhhh.hhhhhhhh<br>11111111.00000000.00000000.00000000 | 16,777,214 |
| /16 | 255.255.0.0 | nnnnnnnn.nnnnnnnn.hhhhhhhh.hhhhhhhh<br>11111111.11111111.00000000.00000000 | 65,534 |
| /24 | 255.255.255.0 | nnnnnnnn.nnnnnnnn.nnnnnnnn.hhhhhhhh<br>11111111.11111111.11111111.00000000 | 254 |

To understand how subnetting on the octet boundary can be useful, consider the following example: Say that an enterprise has chosen the private address 10.0.0.0/8 as its internal network address. That network address can connect 16,777,214 hosts in one broadcast domain. Obviously, having more than 16 million hosts on a single subnet is not ideal.

The enterprise could further subnet the 10.0.0.0/8 address at the octet boundary /16, as shown in Table 11-5. This would enable the enterprise to define up to 256 subnets

(that is, 10.0.0.0/16 to 10.255.0.0/16), and each subnet would be capable of connecting 65,534 hosts. Notice that the first two octets identify the network portion of the address, whereas the last two octets are for host IP addresses.

## Table 11-5 Subnetting Network 10.0.0.0/8 Using a /16 Prefix

| Subnet Address (256 Possible Subnets) | Host Range (65,534 Possible Hosts per Subnet) | Broadcast |
|---|---|---|
| 10.0.0.0/16 | 10.0.0.1–10.0.255.254 | 10.0.255.255 |
| 10.1.0.0/16 | 10.1.0.1–10.1.255.254 | 10.1.255.255 |
| 10.2.0.0/16 | 10.2.0.1–10.2.255.254 | 10.2.255.255 |
| 10.3.0.0/16 | 10.3.0.1–10.3.255.254 | 10.3.255.255 |
| 10.4.0.0/16 | 10.4.0.1–10.4.255.254 | 10.4.255.255 |
| 10.5.0.0/16 | 10.5.0.1–10.5.255.254 | 10.5.255.255 |
| 10.6.0.0/16 | 10.6.0.1–10.6.255.254 | 10.6.255.255 |
| 10.7.0.0/16 | 10.7.0.1–10.7.255.254 | 10.7.255.255 |
| ... | ... | ... |
| 10.255.0.0/16 | 10.255.0.1–10.255.255.254 | 10.255.255.255 |

Alternatively, the enterprise could choose to subnet the 10.0.0.0/8 network at the /24 octet boundary, as shown in Table 11-6. This would enable the enterprise to define 65,536 subnets, each capable of connecting 254 hosts. The /24 boundary is very popular in subnetting because it accommodates a reasonable number of hosts and conveniently subnets at the octet boundary.

## Table 11-6 Subnetting Network 10.0.0.0/8 Using a /24 Prefix

| Subnet Address (65,536 Possible Subnets) | Host Range (254 Possible Hosts per Subnet) | Broadcast |
|---|---|---|
| 10.0.0.0/24 | 10.0.0.1–10.0.0.254 | 10.0.0.255 |
| 10.0.1.0/24 | 10.0.1.1–10.0.1.254 | 10.0.1.255 |
| 10.0.2.0/24 | 10.0.2.1–10.0.2.254 | 10.0.2.255 |
| ... | ... | ... |
| 10.0.255.0/24 | 10.0.255.1–10.0.255.254 | 10.0.255.255 |
| 10.1.0.0/24 | 10.1.0.1–10.1.0.254 | 10.1.0.255 |
| 10.1.1.0/24 | 10.1.1.1–10.1.1.254 | 10.1.1.255 |
| 10.1.2.0/24 | 10.1.2.1–10.1.2.254 | 10.1.2.255 |
| ... | ... | ... |
| 10.100.0.0/24 | 10.100.0.1–10.100.0.254 | 10.100.0.255 |
| ... | ... | ... |
| 10.255.255.0/24 | 10.255.255.1–10.255.255.254 | 10.255.255.255 |

## Subnet Within an Octet Boundary (11.5.2)

The examples shown thus far have borrowed host bits from the common /8, /16, and /24 network prefixes. However, subnets can borrow bits from any host bit position to create other masks.

For instance, a /24 network address is commonly subnetted using longer prefixes by borrowing bits from the fourth octet. This provides an administrator with additional flexibility when assigning network addresses to a smaller number of end devices.

Table 11-7 shows six ways to subnet a /24 network.

Table 11-7 Subnetting a /24 Network

| Prefix Length | Subnet Mask | Subnet Mask in Binary (n = Network, h = Host) | Number of Subnets | Number of Hosts |
|---|---|---|---|---|
| /25 | 255.255.255.128 | nnnnnnnn.nnnnnnnn.nnnnnnnn.nhhhhhhh<br>11111111.11111111.11111111.10000000 | 2 | 126 |
| /26 | 255.255.255.192 | nnnnnnnn.nnnnnnnn.nnnnnnnn.nnhhhhhh<br>11111111.11111111.11111111.11000000 | 4 | 62 |
| /27 | 255.255.255.224 | nnnnnnnn.nnnnnnnn.nnnnnnnn.nnnnhhhh<br>11111111.11111111.11111111.11100000 | 8 | 30 |
| /28 | 255.255.255.240 | nnnnnnnn.nnnnnnnn.nnnnnnnn.nnnnhhhh<br>11111111.11111111.11111111.11110000 | 16 | 14 |
| /29 | 255.255.255.248 | nnnnnnnn.nnnnnnnn.nnnnnnnn.nnnnnhhh<br>11111111.11111111.11111111.11111000 | 32 | 6 |
| /30 | 255.255.255.252 | nnnnnnnn.nnnnnnnn.nnnnnnnn.nnnnnnhh<br>11111111.11111111.11111111.11111100 | 64 | 2 |
